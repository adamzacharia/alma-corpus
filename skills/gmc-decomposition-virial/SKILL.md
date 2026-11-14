---
name: alma-gmc-decomposition-virial
description: "Decompose ALMA molecular-line cubes into clouds or clumps (CPROPS, astrodendro, CLUMPFIND, fixed-scale), measure size, linewidth, luminosity and mass, and derive virial parameters, Larson scaling relations, mass spectra, surface density, pressure and free-fall times. Use when asked whether GMCs or clumps are bound, to build a cloud catalog from a CO / 13CO / dense-gas cube, to fit size-linewidth or mass-size relations, or to compare cloud properties across galaxies or environments. Built from 127 ALMA papers (2012-2025) in the evidence pack, of which roughly 57 are on-topic."
---

# Molecular cloud decomposition and virial analysis

Find discrete clouds (or clumps) in a line cube, measure R, sigma_v, L and M for each, then compare kinetic and
gravitational terms through alpha_vir = 5 sigma_v^2 R / (G M) and the Larson relations. The two mistakes that
matter most: (1) cloud properties are set by the segmentation and the beam, so sizes near the resolution and
fluxes without short spacings are biased; (2) alpha_vir carries every assumption of the mass (alpha_CO, R21,
abundance, Tex, dust temperature) and of the geometry (density profile, 1D vs 3D dispersion), so absolute values
are uncertain by factors of 2 or more and must be reported with the conventions used.

Counts below are from the pack (`C:\Users\adama\alma-corpus\skills\packs\gmc-decomposition-virial.md`). The pack
was tagged by regex, so about 70 of its 127 papers only mention "free-fall" infall, a "virial" dynamical mass of a
galaxy, or LVG K_vir; those are excluded from the guidance here. Of the roughly 57 on-topic papers, about half work
at GMC scale in CO in nearby galaxies, the LMC/SMC and dwarfs, and the rest at clump and core scale in Galactic
clouds (my reading of the pack titles and lines).

## When to use

- A CO, 13CO, C18O or dense-gas (HCN, CS, H13CO+, N2H+) cube where the question is about cloud populations,
  binding, or cloud scaling relations (2018ApJ...857...19F, 2018PASJ...70...73H, 2024ApJ...964..166K).
- Testing whether clumps or cores are gravitationally bound with a virial parameter, including Galactic-centre and
  massive-protocluster clumps (2014ApJ...795L..25R, 2015MNRAS.449..715W, 2019ApJ...872..121U, 2020ApJ...894...87C).
- Size-linewidth, virial (M_lum vs M_vir), mass-size and C_RdV (sigma/R^0.5) vs Sigma relations
  (2018ApJ...857...19F, 2024ApJ...966...51G).
- GMC mass spectra (2018PASJ...70...73H) and star formation efficiency per free-fall time
  (2018PASJ...70...73H, 2018ApJ...861L..18U, 2018ApJ...855L..25K).
- Calibrating alpha_CO or X_CO from virial masses of resolved clouds (2015Natur.525..218R, 2020MNRAS.499.2534K).

## When not to use

- **Dense cores in dust continuum maps, core mass functions:** use the `alma-core-extraction-cmf` skill
  (core-extraction-cmf). This skill covers line-cube segmentation and the virial step; core finding in continuum
  images (getsf, dendrograms on continuum, CMF fitting) belongs there.
- **Galaxy dynamical masses** from a rotation curve or a single "virial" sigma^2 R of an unresolved galaxy: use a
  galaxy kinematics skill. Several pack papers do this (2024ApJ...972..111L, 2024ApJ...961..120C) and they are not
  cloud analysis.
- **Infall onto protostars, free-fall streamers, Keplerian disks** (2014ApJ...786..114L, 2025SciA...11.4512O):
  use the envelope or disk kinematics skills.
- **LVG excitation with a K_vir prior** (2014ApJ...785..149S, 2020A&A...643A..89P): use the non-LTE excitation skill.
- **Clouds below about one beam in every dimension:** do not report sizes or alpha_vir as measured; give limits.
  A fixed-scale (beam-sized) analysis (2018ApJ...860..172S, see Step 2) is a different measurement: it gives the
  properties of an assumed beam volume, not the radius or binding state of the compact object inside it.

## Steps

1. **Prepare the cube (goal: known noise, beam and flux recovery).**
   - Use one circular or fixed elliptical beam per cube and a noise map; report rms per channel.
   - Check flux recovery against single dish before decomposing: papers recover 63% of APEX
     (2018ApJ...857...19F), 58% of NANTEN (2020MNRAS.499.2534K), and lose about half without short spacings
     (2012A&A...538L...9H). Combine with 7m/TP when available (2020ApJ...894...87C used TP C18O for the clump
     dispersion).
   - For cross-galaxy or resolution tests, smooth to a common resolution with CASA `imsmooth`, `specsmooth`,
     `imrebin` and confirm flux is preserved (2018ApJ...857...19F, 40 pc and 2 km/s).
2. **Choose a segmentation (goal: a reproducible cloud catalog).**
   - CPROPS is the most common choice: named 17 times in the pack software aggregate (one of those is the
     off-topic SN 1987A ejecta paper 2017ApJ...842L..24A), plus `cpropstoo` once. Others: CLUMPFIND 4,
     astrodendro 3 (pack aggregate). SCIMES appears once (2024ApJ...966...51G).
   - CPROPS with ECLUMP: THRESH = 3 sigma, EDGE = 1.5 sigma, MINAREA = 0.5 beams, MINPEAK = 3 sigma, MINVCHAN = 3,
     BOOTSTRAP = 1000, /NONUNIFORM (2025A&A...699A.369V); mask above 4 sigma with edge 2.0-1.5 sigma
     (2020MNRAS.499.2534K); 4 sigma seeds in adjacent voxels, 2 sigma edge, local maxima in a 15 pc x 15 pc x
     2 km/s box, SIGDISCONT = 5, candidates larger than one beam and peak > 1 K above the merge level
     (2018ApJ...857...19F).
   - astrodendro: leaves with peak S/N > 3, 3 sigma above the merge level, min pixels = 3 beam areas
     (2018PASJ...70...73H); min_value = 3 sigma, min_delta = 1 sigma, min_npix = 60 (2017MNRAS.464L..31H).
   - CLUMPFIND: threshold 8 sigma, increment 4 sigma, then drop clumps smaller than the beam (265 to 187 clumps)
     (2017PASJ...69...18T).
   - Fixed-scale alternative: treat each beam as the cloud, R = r_beam, line-of-sight depth about 2 r_beam, an
     assumed rho ~ r^-1 profile (f = 10/9) (2018ApJ...860..172S); for SFE_ff a fixed H = 100 pc with hydrostatic
     and virial-cloud alternatives (2018ApJ...861L..18U). This yields beam-averaged Sigma, sigma_v and alpha_vir of
     an assumed volume at that scale, with mass and linewidth taken from the same beam; it does not recover the
     size or alpha_vir of an unresolved cloud. Report it as a fixed-scale quantity and state the assumed depth.
   - Single isolated clump: CASA `imfit` 2D Gaussian on the moment-0 map (2020ApJ...892..147S).
   - Inspect the catalog: flag sidelobe artifacts by hand (2025A&A...699A.369V), dispersed leaves
     (3 flagged, 2018PASJ...70...73H), and duplicates across mosaic fields (2018ApJ...857...19F).
3. **Measure R, sigma_v and L (goal: beam- and sensitivity-corrected moments).**
   - Separate velocity components first. Inspect the spectrum of each object before assigning a linewidth;
     papers fit two Gaussian components where one fails (2020ApJ...894...87C, strips 1 and 3), used DCO+ to pick
     the component associated with the dust mass (2020ApJ...894...87C), and fit Gaussians to blended clumps
     (2025A&A...699A.369V). Recommendation: the linewidth must come from the component that matches the mass
     aperture; flag blended or multi-component objects and keep them out of relation fits or report them apart.
   - Moment method with extrapolation to 0 K and beam deconvolution, R = 1.91 sigma_r (Solomon convention)
     (2018ApJ...857...19F; 2018PASJ...70...73H writes it as 3.4/sqrt(pi) sqrt(sigma_x sigma_y)); bootstrap
     uncertainties with 1000 draws (2018ApJ...857...19F).
   - Alternatives: geometric mean of CLUMPFIND semi-axes (2020ApJ...890...76N), imfit Gaussian sigma
     (2020ApJ...892..147S), dendrogram vs deconvolved radius compared side by side (2020ApJ...894...87C).
   - Use a thermal-corrected dispersion when testing total support (2020ApJ...894...87C); an effective sound
     speed of 0.247 km/s from a 0.4 km/s N2D+ linewidth was used at core scale (2021ApJ...907L..15S).
     General practice for the correction: sigma_tot^2 = sigma_obs^2 - kT/(m_tracer) + kT/(mu_p m_H), that is,
     subtract the tracer molecule's thermal variance and add the bulk gas thermal variance, with mu_p the mass per
     free particle (2.33, see Step 4).
   - Drop or flag unresolved objects: R < 5 pc, about half the resolution (2018ApJ...857...19F); area below
     1.5 beam areas, 34 of 76 cores (2020ApJ...894...87C); diameter < 1.4 arcsec (2017PASJ...69...18T).
4. **Convert to mass (goal: M_lum or M_LTE or M_dust with stated conversions).**
   - CO, general form: M_lum = alpha_CO,10 L'_J / R_J1, where L'_J is the CO(J to J-1) luminosity in
     K km/s pc^2, alpha_CO,10 is the CO(1-0) conversion, and R_J1 = L'_J / L'_10 is the brightness-temperature
     luminosity ratio (R21 for CO(2-1), R31 for CO(3-2)); for CO(1-0) R_J1 = 1. Helium convention (general
     practice): X = 2.0e20 cm^-2 (K km/s)^-1 is about 3.2 Msun pc^-2 (K km/s)^-1 in H2 alone and about 4.35-4.4
     with the 1.36 helium factor; say which one you use.
   - Adopted conversions seen: alpha_CO,MW = 4.35 with R21 = 0.7 for CO(2-1) (2018ApJ...857...19F);
     alpha_CO = 4.35 with R21 = 1 (2017ApJ...835..278S); X = 2.0e20 with helium 1.36, giving M = 4.4 L_CO for
     CO(1-0) (2018PASJ...70...73H); X = 3.0e20 without helium and I(2-1)/I(1-0) = 1 (2012ApJ...760L..25E);
     alpha_CO = 8.4 with M = alpha_CO L_CO(1-0) and R32/10 about 2 in 30 Dor (2025A&A...699A.369V); CPROPS
     X_CO 4.35e20 with brightness temperature ratio 0.82 (2018ApJ...867..165B).
   - X(1-0) = 2.4, X(2-1) = 3 with R21 = 0.8 in the LMC (2024ApJ...966...51G): the pack and card give these
     without a unit scale or power of ten. Do not use them until the scale is checked in the paper.
   - Conversions derived from virial masses are results, not choices: X_CO = 5.5e20 +/- 4.6e20
     (2020MNRAS.499.2534K), alpha_CO about 28 +/- 28 Msun pc^-2 (K km/s)^-1 in WLM (2015Natur.525..218R).
   - 13CO LTE: same Tex for 12CO and 13CO from the 12CO peak, N(H2)/N(13CO) = 3e6 (2024ApJ...966...51G);
     [H2]/[13CO] = 5.0e5 with Tex = 8.5 K (2017PASJ...69...18T).
   - Dense tracers: Tex per core from RADEX on two CS lines, X(H13CO+) = 6e-11, X(C34S) = 4.87e-10
     (2019ApJ...872..121U).
   - Dust: T = 20 K (2020ApJ...894...87C, 2014ApJ...795L..25R), 70 K gas in the CMZ (2015MNRAS.449..715W).
   - Two different mean masses, not interchangeable choices: mu_p = 2.33, the mass per free particle, sets the
     sound speed and thermal pressure (2020ApJ...894...87C, 2025ApJ...995..193Y; 2.37 in 2021ApJ...907L..15S);
     mu_H2 = 2.8, the mass per H2 molecule, converts N(H2) to gas mass (2020ApJ...890...76N; mu = 2.8 mH also in
     2015MNRAS.449..715W). Using 2.33 in a column-to-mass conversion underestimates mass by about 17%.
5. **Virial mass and virial parameter (goal: alpha_vir with its convention written down).**
   - alpha_vir = 5 sigma_v^2 R / (G M) is the usual form (2024ApJ...964..166K, 2020ApJ...894...87C,
     2024ApJ...966...51G). Call it alpha_5.
   - Two normalizations exist for a density profile rho ~ r^-k_rho; keep them apart (general practice):
     a = (1 - k_rho/3) / (1 - 2 k_rho/5) and alpha_5 = 2a E_K/|E_G|. The energy ratio alpha_E = 2E_K/|E_G| =
     alpha_5 / a. For alpha_E, equilibrium is 1 and the bound limit is 2. For alpha_5, equilibrium is a and the
     bound limit is 2a. Never apply a profile-corrected coefficient and then also use the 2a threshold.
   - What papers did: 2020ApJ...894...87C keeps alpha_5 = 5 sigma^2 R/(G M) = 2a E_K/|E_G| with k_rho = 1.5,
     a = 5/4, and calls a core unbound above alpha_cr = 2a. 2014ApJ...795L..25R uses alpha_vir = 3k sigma^2 R/(G M)
     with k = 1.16 for rho ~ r^-1.8 (3k = 3.48, close to 5/a = 3.5 for that profile, so this is an alpha_E-type
     form; the comparison is my arithmetic). 2018ApJ...860..172S uses alpha_vir = 5 sigma^2 R/(f G M) with
     f = 10/9 for rho ~ r^-1 (f equals a for that profile, again alpha_E-type).
   - M_vir coefficients in the pack (R in pc, velocities in km/s): 1040 R sigma^2 (2020ApJ...892..147S),
     1044 R sigma^2 (2015Natur.525..218R), 189 R dV^2 with FWHM dV for a beta = 1 truncated power law
     (2018ApJ...857...19F), 190 R dV^2 for r^-1 (2025A&A...699A.369V), 210 R dV^2 for uniform density
     (2018ApJ...856..147O, 2019ApJ...872..121U). See references/parameters.md for how these relate.
   - Omitted terms, as each paper states them: surface term and magnetic energy ignored (2020ApJ...894...87C);
     no external pressure and no magnetic field (2019ApJ...872..121U); magnetic fields and external pressure
     ignored, isothermal cylinder (2014ApJ...791..108F); magnetic fields neglected, uniform sphere
     (2016ApJ...833..209O).
   - Interpretation thresholds seen: equilibrium for 0.71 < alpha < 1.4 (2020ApJ...890...76N); virial vs
     equipartition bins (2024ApJ...966...51G); alpha_5 > 2a unbound (2020ApJ...894...87C). Check which
     normalization a threshold refers to before comparing.
6. **Derived quantities (goal: environment comparison).**
   - Sigma = M / (pi R^2); P_e/k = 3 Pi M sigma^2 / (4 pi R^3 k) with Pi = 0.5 (2024ApJ...964..166K).
   - t_ff (general practice): t_ff = sqrt(3 pi / (32 G rho)) with rho = M / ((4/3) pi R^3) for a sphere of
     radius R; state the volume geometry (sphere of R, or a fixed depth for fixed-scale work). 2018PASJ...70...73H
     derives tau_ff from rho with a factor 1.26; the pack does not show where that factor enters, so check the
     paper before reproducing its numbers. SFE_ff = SFR t_ff / M (2018PASJ...70...73H).
   - Associating star formation (2018PASJ...70...73H): an HII region belongs to a GMC if its centre lies within
     the GMC boundary; when several GMCs are associated, the SFR is split among them by mass; the association
     radius is varied by +/-20%. The same paper considers stochastic IMF sampling, stellar-age uncertainty in the
     SFR calibration and mass consumption by feedback, and says the SFR could be underestimated by about a
     factor of 2. Recommendation: carry an SFR uncertainty budget with these terms into SFE_ff.
   - Outlier search for extreme clumps with a GESD test, upper bound 20 outliers (2024ApJ...964..166K, `papanda`).
7. **Fit scaling relations and mass spectra (goal: slopes with honest errors).**
   - Orthogonal distance regression in log space with errors on both axes (2018ApJ...857...19F; ODR also in
     2024ApJ...966...51G).
   - Mass spectrum: truncated power law (Williams & McKee form) fitted to the cumulative mass function over
     1e6 to 3e7 Msun in M83, 100 bootstrap draws, median and MAD, two-sided KS test (2018PASJ...70...73H).
     Recommendation: fit only above your completeness mass; the cards rarely state how the range was chosen.

## Parameter defaults and ranges

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| Segmentation code | CPROPS (ECLUMP or modified) | CPROPS, astrodendro, CLUMPFIND, SCIMES, imfit, fixed beam | cprops 17, clumpfind 4, astrodendro 3 (aggregate, all papers) | 2025A&A...699A.369V, 2018PASJ...70...73H, 2017PASJ...69...18T |
| Detection threshold | 3-4 sigma | 3 sigma to 8 sigma | 6 | 2025A&A...699A.369V, 2020MNRAS.499.2534K, 2017PASJ...69...18T |
| Edge / mask extension | 1.5-2 sigma | 1.5-2 sigma | 3 | 2025A&A...699A.369V, 2018ApJ...857...19F, 2020MNRAS.499.2534K |
| Merge / contrast | 1 sigma (dendro) or 3 sigma | 1 sigma to 4 sigma increment | 3 | 2017MNRAS.464L..31H, 2018PASJ...70...73H, 2017PASJ...69...18T |
| Minimum size | about 1 beam | 0.5 beam to 3 beam areas; R > half resolution | 5 | 2025A&A...699A.369V, 2018PASJ...70...73H, 2018ApJ...857...19F, 2020ApJ...894...87C |
| Radius definition | 1.91 sigma_r, deconvolved, extrapolated | geometric-mean semi-axes; imfit; R = r_beam | 6 | 2018ApJ...857...19F, 2020ApJ...890...76N, 2018ApJ...860..172S |
| Bootstrap draws | 1000 | 100-1000 | 3 | 2018ApJ...857...19F, 2025A&A...699A.369V, 2018PASJ...70...73H |
| alpha_CO adopted (Msun pc^-2 (K km/s)^-1) | 4.35 (Galactic) | alpha_CO 4.35-8.4 (3 papers); X 2.0e20-4.35e20 cm^-2 (K km/s)^-1 (3 papers); derived from virial masses, not adopted: X 5.5e20, alpha_CO about 28 | 6 adopted | 2018ApJ...857...19F, 2017ApJ...835..278S, 2025A&A...699A.369V, 2018PASJ...70...73H, 2012ApJ...760L..25E, 2018ApJ...867..165B |
| R21 | 0.7-0.8 | 0.7-1.0 | 4 | 2018ApJ...857...19F, 2024ApJ...966...51G, 2012ApJ...760L..25E, 2017ApJ...835..278S |
| Density profile in M_vir | rho ~ r^-1 | uniform, r^-1, r^-1.5, r^-1.8 | 13 | 2025A&A...699A.369V, 2018ApJ...856..147O, 2020ApJ...894...87C, 2014ApJ...795L..25R |
| Mean mass per free particle (sound speed) | mu_p = 2.33 | 2.33-2.37 | 4 | 2020ApJ...894...87C, 2025ApJ...995..193Y, 2018ApJ...855L..25K, 2021ApJ...907L..15S |
| Mean mass per H2 molecule (column to mass) | mu_H2 = 2.8 | 2.8 | 2 | 2020ApJ...890...76N, 2015MNRAS.449..715W |
| Pi in pressure | 0.5 | - | 1 | 2024ApJ...964..166K |
| Bound criterion | alpha_5 < 2 (uniform) or alpha_5 < 2a; alpha_E < 2 | 0.71-1.4 equilibrium band; alpha_cr = 2a | 3 | 2020ApJ...890...76N, 2020ApJ...894...87C, 2024ApJ...966...51G |

Counts in the table are my counts of distinct papers whose pack lines (aggregate sections and excerpts) state the
setting; the segmentation-code row is the pack software aggregate (mentions, not unique papers). For alpha_CO,
"adopted" counts 2018ApJ...857...19F, 2017ApJ...835..278S, 2025A&A...699A.369V (alpha_CO) and 2018PASJ...70...73H,
2012ApJ...760L..25E, 2018ApJ...867..165B (X); 2024ApJ...966...51G is left out because its unit scale is missing.

Reported values that bracket a sanity check: median alpha_vir about 1.4 for 179 M83 GMCs with median mass
1.6e6 Msun (2018PASJ...70...73H); median 1.22 (std 0.88) for G286 cores (2020ApJ...894...87C); mean 13.77 in the
Antennae overlap, classed supervirial (2024ApJ...964..166K); 1.4, 0.7, 0.9 for CMZ clouds (2015MNRAS.449..715W);
size-linewidth slope 0.48 +/- 0.05, virial slope 1.00 +/- 0.05, mass-size slope 2.00 +/- 0.12 in NGC 300
(2018ApJ...857...19F); median C_RdV 0.46 km/s pc^-1/2 (2018ApJ...857...19F); mass-spectrum slope -1.6 +/- 0.1
(2018PASJ...70...73H). A per-paper settings table is in `references/parameters.md`.

## Software

| Tool | Used for | Pack count |
|---|---|---|
| CPROPS / cpropstoo (IDL) | segmentation and moment measurements with extrapolation, deconvolution, bootstrap | 17 + 1 (aggregate) |
| CLUMPFIND | segmentation (also the ECLUMP assignment inside CPROPS) | 4 |
| astrodendro | dendrogram leaves as clouds or cores | 3 |
| CASA (`imsmooth`, `specsmooth`, `imrebin`, `imfit`, `immoments`) | resolution matching, single-clump Gaussian fits, moments | casa 6, casa imfit 2, casa immoments 1 |
| RADEX / myradex | Tex for LTE masses of dense tracers | 3 / 1 (several are off-topic LVG uses) |
| ODR | scaling-relation fits with errors on both axes (the pack does not name the implementation; scipy.odr is one option) | 1 |
| papanda | GESD outlier test | 1 |
| SCIMES | spectral clustering of dendrogram structures | named once in a card note (2024ApJ...966...51G) |

Counts are the pack's software aggregate over all 127 papers, so tools like radex, emcee and xspec mostly come
from off-topic papers. The cards rarely name pycprops or the CPROPS version.

## Pitfalls

- **Missing short spacings.** ALMA-only cubes lose 37-42% of single-dish flux in the examples above
  (2018ApJ...857...19F, 2020MNRAS.499.2534K); about half in 2012A&A...538L...9H. Without TP, extended emission and
  low-surface-brightness clouds are missed (2025A&A...699A.369V).
- **Unresolved clouds.** Most clumps were unresolved in 30 Dor (2025A&A...699A.369V) and NGC 4039
  (2012ApJ...760L..25E); only 4 of 13 clumps could be deconvolved in 2014ApJ...793...37A; many G286 cores are not
  well resolved (2020ApJ...894...87C). Deconvolved sizes near the beam are biased; drop or flag them.
- **Mass conversion dominates alpha_vir.** X_CO varies by a factor of 4 in starbursts (2024ApJ...964..166K);
  alpha_CO may be a factor of a few lower in bars (2020MNRAS.495.3840M); abundances up to a factor 2
  (2019ApJ...872..121U); adopted abundance and Tex may vary cloud to cloud (2017PASJ...69...18T); optically thin
  12CO affects LTE masses (2024ApJ...966...51G).
- **Dust temperature for dust-based masses.** T = 15 or 30 K changes alpha by 0.6 or 1.9 (2020ApJ...894...87C,
  absolute alpha uncertain by a factor of 2.5); higher core temperatures lower mass and raise alpha
  (2019ApJ...884...48C); 0.4-0.5 dex mass uncertainty from Tdust, kappa and DGR (2018ApJ...869..126L).
- **Boundary definition.** Cloud area is ambiguous, giving about a factor 2 systematics (2015MNRAS.449..715W).
  Segmentation settings change the catalog; test them (Verification).
- **Dispersion conventions.** One paper omits the factor 3 by using the 1D dispersion (2024A&A...690A.375S); only
  line-of-sight sigma is measured. Do not mix FWHM coefficients (189-210) with sigma coefficients (1040-1044).
- **Extrapolated dispersions.** Velocity dispersion extrapolated by an assumed Kolmogorov law
  (2019ApJ...884...48C) adds a model assumption to alpha.
- **Ignored terms.** Surface or external pressure is dropped in 2020ApJ...894...87C, 2019ApJ...872..121U and
  2014ApJ...791..108F; magnetic terms in those three and in 2016ApJ...833..209O. A high alpha_vir can mean
  pressure confinement, not dispersal.
- **Mixed alpha normalizations.** A profile-corrected alpha_E compared with an alpha_5 threshold (or the reverse)
  shifts the bound/unbound line by the factor a (1.11-1.43 for the profiles in the pack). See Step 5.
- **Comparisons across resolution.** Cross-galaxy comparisons depend on resolution and on X_CO and R21
  (2024ApJ...964..166K); smooth to a common resolution first (2018ApJ...857...19F).
- **Not stated in cards.** From the pack "not stated" aggregate (counts are entries per exact wording, so related
  wordings are listed separately there): continuum subtraction and line-free channels 11 (plus several other
  wordings of the same gap), CASA version 9 (plus CASA/pipeline version 4 and 3 in other wordings), flux scale
  uncertainty 7 (plus flux calibrator and flux scale uncertainty 6), self-calibration solution intervals 5,
  primary-beam correction details 4 (+2), image and cell size 3, CPROPS parameters 2, and single entries for
  absolute astrodendro min_delta/min_value and pixel size, bootstrap details and line-free channels for rms.
  Recommendation: record continuum treatment, primary-beam correction and noise map, flux-scale uncertainty,
  CASA and pipeline versions, cell size, channel width and any spectral smoothing, and every segmentation
  parameter in absolute units.

## Verification checks

What papers did:
- Segmentation sensitivity: SIGDISCONT 0, 1, 2, 5, 999, added-noise runs and duplicate-cloud comparison
  (2018ApJ...857...19F); minimum area changed to 2 beam areas gave 6% more leaves (2018PASJ...70...73H).
- Extrapolation factors compared with the Gaussian expectation (2018PASJ...70...73H).
- Bootstrap property errors (2018ApJ...857...19F, 2025A&A...699A.369V).
- Covariance test: a Monte Carlo of 1e4 random clouds gives slope 0.27 and r = 0.37 for the C_RdV-Sigma relation,
  showing how much of a correlation comes from shared variables (2018ApJ...857...19F).
- Resolution test: smooth and rerun CPROPS, check flux preserved (2018ApJ...857...19F).
- Flux recovery against single dish (2018ApJ...857...19F, 2020MNRAS.499.2534K).
- Mass cross-checks: 1.3 mm vs Herschel masses differ by a factor 2 (2020ApJ...894...87C); three density estimates
  agree near 1e3 cm^-3 (2015Natur.525..218R); variable R21 had no significant effect (2024ApJ...966...51G).
- Comparison with the Solomon et al. 1987 relation (2025A&A...699A.369V) and other galaxies' scaling relations
  (2015Natur.525..218R).
- Manual inspection for sidelobe false detections (2025A&A...699A.369V).
- Mass spectrum goodness of fit with a two-sided KS test (2018PASJ...70...73H).

What a careful referee adds (recommendation, following the checks above):
- Report alpha_vir with the formula, density-profile factor, alpha_CO, R21 and distance on one line, and show how
  the median moves under the stated range of each.
- Show the catalog is stable under at least two threshold settings and one alternative segmentation.
- Mark or exclude clouds with R or sigma_v near the beam or channel width before fitting relations.
- State the completeness limit in mass and fit mass spectra only above it.

## Source cards

Full list: `references/sources.md` (generated). Most informative for this technique:

- 2018ApJ...857...19F: CPROPS settings, SIGDISCONT tests, ODR Larson fits, resolution test (NGC 300).
- 2018PASJ...70...73H: astrodendro GMCs, mass spectrum, SFE_ff (M83).
- 2025A&A...699A.369V: full CPROPS ECLUMP parameter set, 190 dV^2 R (30 Dor).
- 2024ApJ...964..166K: alpha_vir, pressure, GESD outliers (Antennae).
- 2024ApJ...966...51G: size-linewidth and feedback, 13CO LTE masses (LMC).
- 2020ApJ...894...87C: thermal-corrected core alpha, profile factor a, uncertainty budget.
- 2017PASJ...69...18T: CLUMPFIND at 8 sigma, 13CO LTE masses (NGC 1068).
- 2018ApJ...860..172S: fixed-scale beam approach, f = 10/9.
- 2018ApJ...861L..18U: SFE per free-fall time with fixed and virial scale heights.
- 2020MNRAS.499.2534K: CPROPS ECLUMP, X_CO from virial fit (Magellanic Bridge).
- 2015Natur.525..218R: 1044 R sigma^2, virial alpha_CO in WLM.
- 2020ApJ...892..147S: imfit single clump, 1040 R sigma^2 (DDO 70).
- 2019ApJ...872..121U: RADEX Tex, abundance-based LTE masses (Galactic centre).
- 2015MNRAS.449..715W: dust virial ratios of CMZ clouds.
- 2014ApJ...795L..25R: k = 1.16 for rho ~ r^-1.8.
- 2017ApJ...835..278S: clouds at 2 pc in NGC 6822, alpha_CO 4.35 with R21 = 1.
- 2017MNRAS.464L..31H: astrodendro thresholds.
- 2018ApJ...867..165B: CPROPS X_CO setting (Henize 2-10).
- 2012ApJ...760L..25E: X factor without helium, unresolved clumps (NGC 4039).
