---
name: alma-dust-continuum-mass
description: "Turn ALMA (sub)mm continuum flux into dust mass, gas mass, column density or an upper limit, with an opacity law, dust temperature, gas-to-dust ratio and distance chosen the way published ALMA papers choose them. Use when converting a continuum flux or brightness to a disk, core, clump, envelope, debris belt, circumstellar shell or galaxy dust/gas mass, when checking someone else's mass, or when stating mass upper limits for non-detections. Built from 385 ALMA papers (2012-2026)."
---

# Dust and gas masses from (sub)mm continuum

Measures the mass of emitting dust from a continuum flux density under the optically thin, isothermal
assumption, then (optionally) a gas mass through a gas-to-dust ratio. The answer is only as good as three
assumed numbers: opacity kappa_nu, dust temperature T_d, and gas-to-dust ratio. The two mistakes that matter
most: (1) mixing an opacity quoted **per gram of gas** with one quoted **per gram of dust** (a factor 100
error), and (2) applying the thin formula to emission that is partly optically thick, which only gives a
**lower limit** (2018A&A...619A.161C, 2015A&A...573L...1O, 2014ApJ...783L..13P).

> Always report kappa_nu (with its reference frequency, beta and whether it is per dust or per gas mass),
> T_d, distance, gas-to-dust ratio, and the flux you used. A mass without these is not reproducible.

## When to use

- A detected continuum source (disk, core, clump, envelope, belt, shell, galaxy) and you need M_dust, M_gas,
  N(H2) or n(H2) from its flux or surface brightness.
- A non-detection: convert an n-sigma flux limit to a mass limit (3 sigma is the usual choice:
  2015A&A...583A..66H, 2019ApJ...875L...9W, 2017ApJ...842....8M; 2 sigma in 2024ApJ...963....1O).
  Such a limit is an optically thin, assumed-size limit only (see step 8).
- Population work: dust-mass distributions and M_dust vs M_star relations for disk surveys
  (2016ApJ...828...46A, 2020A&A...633A.114S, 2014ApJ...787...42C).
- Core and clump fragmentation studies needing core masses, densities and virial parameters
  (2020ApJ...894L..14L, 2020ApJ...890...76N, 2019ApJ...871..185L).
- Sanity-checking a mass quoted in a paper or produced by another tool.

## When not to use

| Situation | Use instead |
|---|---|
| Emission likely optically thick (bright compact disks, hot cores, inner envelopes, T_b close to T_d) | Radiative transfer model (RADMC-3D, MCFOST, DALI) or state the result as a lower limit (2015A&A...573L...1O, 2017A&A...604A...6S) |
| Disk structure, settling, gaps, gas and dust together | Full disk modelling: DALI (13 papers in pack aggregates), RADMC-3D (13), MCFOST/mcfost (10) |
| High-z galaxy with good FIR photometry | SED fit (MAGPHYS 6 summed over two labels, CIGALE 5 in the aggregates; STARDUST in 2024A&A...690A..55S) and use its dust mass, after reconciling its dust composition and opacity with yours (2025A&A...694A..82S divides CIGALE masses by 2 for this), with the single-band mass as a cross-check |
| Gas mass where CO is detected and alpha_CO is defensible | CO-based mass, then compare with the dust route (2021A&A...652A..98G, 2018Sci...362.1034D) |
| Continuum dominated by free-free, synchrotron or stellar photosphere | Decompose first (SED with radio data); the dust formula on raw flux overestimates mass (2016A&A...591A..73G, 2017MNRAS.468L..87C) |
| Extended emission resolved out by the interferometer | Combine with ACA/TP or single-dish, or quote the mass as a lower limit (2014ApJ...787...48X, 2024ApJ...968L..19F) |

## Steps

1. **Define the emitting object and regime.** Decide the aperture or component (whole disk, ring, crescent,
   core, clump, belt, galaxy). Note whether you need dust mass, gas mass, column density or volume density;
   each needs extra inputs (gas-to-dust, mu, a size or thickness). Examples of core extraction in clusters:
   astrodendro (2020ApJ...894L..14L), Clumpfind (2020ApJ...890...76N), both (2019ApJ...871..185L); the pack
   does not show which is more common.
2. **Build a clean continuum flux.**
   - Image line-free continuum (CASA `tclean`, or GILDAS MAPPING; 2024A&A...691A.180F,
     2021A&A...652A..98G). The cards rarely state which channels were line-free (the pack counts dozens of
     cards flagging "line-free channels" as not stated), so record yours. Line contamination of continuum is
     a real limitation (2013ApJ...774L...7M).
   - Apply primary-beam correction before measuring flux (8 cards flag PB-correction details as unstated).
   - Measure the flux: aperture inside a contour (5 sigma contour and 50% PB response in
     2019ApJ...874...89C), 2D Gaussian with `imfit` (CASA imfit in 3 aggregate papers), or a uv-plane fit
     (`lmfit` on visibilities in 2025ApJ...986L..22R; emcee on visibilities in the fitting aggregates).
   - Use the integrated flux density (Jy) for a mass. A peak in Jy/beam is a mass per beam; for surface
     brightness divide by the beam solid angle, Omega_beam = pi theta_maj theta_min / (4 ln 2) (general
     practice). Take the noise locally from the PB-corrected map, not one global rms: noise rises toward the
     PB edge and can be enhanced locally (gap rms in 2024ApJ...974..102S).
   - Remove non-dust flux: stellar photosphere (F_dust = F_cen - F_star in 2013ApJ...762L..21M),
     free-free or synchrotron (2017MNRAS.468L..87C, 2016ApJ...821L..16C, 2016A&A...591A..73G), compact
     companions or central sources by Gaussian subtraction (2014ApJ...796....1T).
3. **Choose the dust temperature** (Parameter table). The pack shows examples of each approach, not a
   ranking. My guidance (not a literature census): prefer a temperature measured for the same emitting
   component (SED fit, NH3 or line rotational temperature), then a luminosity or radiative-equilibrium
   scaling, then a fixed fiducial, and check the temperature applies to the dust you are weighing. Examples: SED fit with SciPy least squares (2020ApJ...890...76N), MCMC SED fit
   (2018MNRAS.475..448T), T_d from gas temperature (2014ApJ...797...27F, 2016ApJ...828..100F), luminosity
   scaling for disks (2016ApJ...819..102V, 2021A&A...653A..46V), radiative equilibrium at the belt radius
   for debris disks (2017ApJ...842....8M, 2025A&A...693A.151M).
4. **Choose the opacity law** kappa_nu = kappa_0 (nu/nu_0)^beta. Pick the convention of the subfield you
   will be compared with (Parameter table, `references/parameters.md`), and check whether kappa_0 is per gram
   of dust or per gram of gas.
5. **Compute the mass** with the full Planck function (general practice; the Rayleigh-Jeans limit is
   poor at 20 K and 230 GHz, where h nu / k is about 11 K):

   ```
   M_dust = F_nu d^2 / (kappa_nu B_nu(T_d))                       # optically thin, isothermal
   M_gas  = (gas-to-dust) x M_dust                                # or use kappa per gram of gas directly
   N(H2)  = I_nu / (mu_H2 m_H kappa_nu,gas B_nu(T_d))             # I_nu in surface brightness per sr
   n(H2)  = M_gas / ((4/3) pi r^3 mu_H2 m_H)                      # spherical mean, as in 2020ApJ...894L..14L
   ```

   mu_H2 is the mean mass per H2 molecule (2.8; 2019A&A...628A..27B, 2020ApJ...890...76N); do not
   substitute a mean mass per free particle (about 2.33 to 2.37, general practice) here. The n(H2) line
   assumes a sphere of radius r (2020ApJ...894L..14L uses r = (A/pi)^0.5 from the astrodendro area). Say
   so, and propagate the geometry: 2019ApJ...871..185L uses a flattened structure with an assumed thickness
   profile, and 2014ApJ...795L..25R quotes density as a lower limit because the core is unresolved. For an
   unresolved source, r is only an upper bound, so n(H2) is a lower bound.

   Sanity number: with kappa = 2.3 cm2/g at 1.3 mm and T_d = 20 K, 1 mJy at 140 pc is about 0.57 Earth
   masses of dust; 2015A&A...583A..66H uses exactly M_dust = 0.566 [F_1300/mJy (d/140 pc)^2] M_earth.
   For high-z sources (general practice; check the convention of the paper you compare with):

   ```
   nu_rest = (1+z) nu_obs ;  T_CMB(z) = 2.725 K (1+z)
   M_dust  = F_nu,obs D_L^2 / [ (1+z) kappa(nu_rest) ( B_nu_rest(T_d(z)) - B_nu_rest(T_CMB(z)) ) ]
   ```

   The B(T_CMB) term is the contrast correction (dust is seen against the CMB). CMB heating is a separate
   correction that raises T_d(z) for cold dust; apply it only if your T_d is a z = 0 value. Papers that
   correct for the CMB: 2016ApJ...822...80S, 2017Natur.545..457D, 2017ApJ...851..145M, 2015MNRAS.452...54M;
   2020ApJ...892...66M uses the Kovacs-style thin equation with CMB correction. For lensed sources, use the
   intrinsic flux (divide by the magnification mu_L) and say which magnification applies to the dust;
   2016ApJ...822...80S notes that a single magnification is a simplification, since differential
   magnification between dust and other tracers adds uncertainty.
6. **Check optical depth.** Compare the peak intensity with what the dust at T_d would emit if thick.
   For an absorption-only isothermal slab with beam filling factor f and background T_bg (general practice,
   no scattering):

   ```
   tau = -ln[ 1 - Delta I_nu / ( f (B_nu(T_d) - B_nu(T_bg)) ) ]     # Delta I_nu = background-subtracted intensity
   ```

   Use the Planck intensity, not the Rayleigh-Jeans T_b ratio (RJ is poor at these T and nu). 2018A&A...619A.161C
   did a brightness-based check and found the crescent only marginally thin (tau about 0.4 even with T_d
   raised by 1.5), so called its masses lower limits. A low beam-averaged brightness does **not** prove the
   emission is thin: beam dilution (f << 1) or scattering can suppress the observed intensity of thick dust.
   Check the source is resolved before trusting f = 1 (2016Sci...353.1519P flags beam dilution), and
   exclude or model scattering (2020A&A...644A..11L drops pixels with scattering or thick emission;
   2019MNRAS.488.1005P includes anisotropic scattering in RT). If tau is not small, report a lower limit or
   move to RT modelling.
7. **Convert to gas, if needed.** Gas-to-dust 100 is the default (Parameter table); scale with
   metallicity for galaxies and the Magellanic Clouds (2020ApJ...892...66M, 2020ApJ...891..164S,
   2017MNRAS.469.4683C). Cross-check with CO where possible (2021A&A...652A..98G).
8. **Handle limits and samples.** Convert n-sigma limits with the same kappa and T. State the source
   size assumed: a point-source limit (2017ApJ...842....8M) uses the local rms per beam, while an extended
   source needs an aperture or model-dependent limit that grows with the area. A thin mass limit is
   conditional: compact optically thick material can hide more mass. 2017ApJ...842....8M converts its
   Fomalhaut b flux limit to a thin dust-mass limit or, if thick, to a clump-size limit, and
   2019MNRAS.488.1005P uses size-dependent RT models. Do not call a thin limit an upper bound on total mass
   without an optical-depth and size assumption. For samples with non-detections use survival analysis
   (Kaplan-Meier in ASURV: 2016ApJ...828...46A) or Bayesian regression with censored data
   (linmix: 2020A&A...633A.114S).
9. **Write the error budget** (Verification checks). Example: 30% kappa, 15% flux calibration and about 10%
   temperature (2014ApJ...787...48X). Term ordering depends on the case; do not assume it.

## Parameter defaults and ranges

Counts below are my own count of distinct bibcodes in the pack's "Key parameters" and "Assumptions" lines,
which list 308 of the 385 papers (the lists are truncated), so they are lower bounds. The mu counts were
made by matching "mu = 2.8" / "mu_H2 = 2.8" and "mu = 2.3x" in those lines and counting distinct bibcodes.

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| Gas-to-dust (mass) | 100 | 40 to about 370 typical; 4594 in a metal-poor dwarf | about 95 use 100 | 100: 2016ApJ...828...46A, 2020ApJ...894L..14L; 141: 2013ApJ...779...96T, 2018ApJ...853..160C; 150: 2019A&A...621A.122B; 90 +/- 25: 2014MNRAS.438.1267S; 300 (C-rich AGB): 2024A&A...686A.274V; LMC continuum N(H2) with dust-to-gas 0.0027 (gas-to-dust about 370), while the same paper's chemical model uses 300: 2020ApJ...891..164S; 40: 2017A&A...597A..99W; 4594: 2020ApJ...892..147S |
| T_d, disks and cores (fixed) | 20 K | 6 to 30 K for cold gas | 38 use 20 K | 2016ApJ...828...46A, 2019A&A...623A.150V, 2020ApJ...894L..14L; 15 K: 2018A&A...619A.161C, 2017ApJ...838..114K; 6 K: 2024ApJ...968L..19F; 10 K: 2016ApJ...823..160D |
| T_d, disks (scaled) | 25 K (L*/Lsun)^0.25 | exponent 0.17 to 0.25; 20 K fallback or minimum (2021A&A...653A..46V, 2018ApJ...868L...3M) | 7 use an L scaling | 2016ApJ...819..102V, 2021A&A...653A..46V, 2017ApJ...846...70P; RT-calibrated: 2020ApJ...892..111F, 2024A&A...684A.134R |
| T_d, protostellar / hot cores | by evolutionary class | 20 / 50 / 100 K; up to 150 to 300 K | (see examples) | 2020A&A...635A...2S, 2018A&A...615A...9P, 2024A&A...690A.185W, 2019A&A...628A..27B, 2020ApJ...892..152H |
| T_d, high-z galaxies | 35 to 47 K with beta 1.5 to 1.8 | 25 K to 100 K (hot DOG) | (see examples) | 47 K/1.6: 2016ApJ...816...37V, 2017Natur.545..457D; 25 K mass-weighted: 2020ApJ...892...66M; 25 K assumed: 2024ApJ...963....1O; 50-100 K: 2018Sci...362.1034D |
| T_d, debris belts | radiative equilibrium | 25 to 51 K | (see examples) | 2017ApJ...842....8M, 2025A&A...693A.151M, 2013ApJ...762L..21M |
| kappa, disks / debris (per dust) | 10 cm2/g at 1000 GHz, beta 1 (2.3 cm2/g at 230 GHz) | 2 to 3.5 cm2/g at 0.9 to 1.3 mm | 16 use the 1000 GHz form; 18 quote 2.3 cm2/g | 2016ApJ...828...46A, 2019A&A...623A.150V, 2017ApJ...842....8M, 2025A&A...693A.151M |
| kappa, disks, shallow beta | 2.3 cm2/g (nu/230 GHz)^0.4 | beta 0.4 | (see examples) | 2014ApJ...787...42C, 2017ApJ...846...70P, 2018ApJ...869...17L, 2017A&A...597A..32V |
| kappa, cores (OH94, per dust) | 0.899 cm2/g at 1.3 mm | 0.86 to 1.11 cm2/g at 1.3 mm | 12 | 2020ApJ...894L..14L, 2018ApJ...853..160C, 2017ApJ...849...68S, 2019A&A...621A.122B |
| kappa, per gas (includes 100) | 0.01 cm2/g at 230 GHz; 0.1 (nu/1000 GHz)^beta | 0.008 to 0.02 cm2/g near 1.3 mm | (see examples) | 2019ApJ...884...48C, 2018MNRAS.475..448T, 2017A&A...600A.141K, 2014ApJ...791...20R, 2018ApJ...855...24P |
| kappa, galaxies | 0.04 to 0.15 m2/kg near 850 um, beta 1.8 | 0.0431 m2/kg at 352.6 GHz; 0.0865 at 351 GHz | (see examples) | 2020ApJ...892...66M, 2018Sci...362.1034D, 2014MNRAS.438.1267S, 2021A&A...652A..98G |
| beta | 1 (disks, kappa normalised at 1000 GHz); 1.5 to 1.8 (cores, galaxies) | 0.4 to 2.2 | 21 use 1; 29 use 1.5 to 1.9 | 2016ApJ...828...46A; 2020ApJ...892...66M; 2016ApJ...833..209O |
| mu_H2 (mass per H2 molecule) | 2.8 for N(H2), n(H2) | 2.8 only | 13 quote 2.8 (6 label it mu_H2) | mu_H2 = 2.8: 2014ApJ...791..108F, 2019A&A...628A..27B, 2020ApJ...890...76N; mu = 2.8: 2024ApJ...962...48J, 2017ApJ...849...68S |
| mu (other definitions) | not interchangeable with mu_H2 | 2.3 to 2.37 | 8 | 2.3: 2017A&A...604A...6S, 2020A&A...635A...2S; 2.33: 2019ApJ...884...48C, 2020A&A...644A..84M; 2.37: 2016ApJ...823..160D. The cards rarely say whether this is per free particle; check the paper before reusing it |
| Upper-limit significance | 3 sigma | 2 to 3 sigma | (see examples) | 2015A&A...583A..66H, 2019ApJ...875L...9W, 2024ApJ...963....1O |

Longer lists by subfield (opacity normalisations, temperature prescriptions, gas-to-dust variants) are in
`references/parameters.md`.

## Software

From the pack aggregates (software named in the matched steps of all 385 papers). Where two labels are
merged (RADMC-3D 11 + RADMC3D 2, MCFOST 5 + mcfost 5, MAGPHYS 5 + magphys 1, linmix 2 + linmix_err 1) the
number is a sum of label counts; overlap between labels was not checked, so it may overcount papers.

| Tool | Papers | What it is used for |
|---|---|---|
| CASA | 15 (+3 imfit, +1 simobserve) | continuum imaging, `imfit` Gaussian fluxes, simulated observations of models |
| DALI | 13 | thermochemical disk models giving gas and dust masses together |
| RADMC-3D / RADMC3D | 13 | dust RT; e.g. turning a flux limit into a disk mass limit (2019MNRAS.488.1005P) |
| MCFOST / mcfost | 10 | disk RT and SED fitting |
| emcee | 7 | MCMC for SED and visibility fits |
| MAGPHYS / magphys | 6 | galaxy SED fits giving dust mass (2020ApJ...892...66M uses its stellar masses) |
| CIGALE | 5 | galaxy SED fits incl. dust mass (2025ApJ...995L..63L) |
| LIME | 4 | non-LTE line RT for envelopes and disks |
| MIRIAD, GILDAS MAPPING | 3, 2 | imaging outside CASA |
| SciPy | 3 | modified blackbody least squares (2020ApJ...890...76N) |
| ASURV, linmix / linmix_err | 2, 3 | censored statistics on dust-mass samples |

The pack does not establish a dominant implementation of the thin formula; the cards rarely name the code
used for it.

## Pitfalls

- **Per gas vs per dust opacity.** Many cards quote kappa that already includes gas-to-dust 100
  (2018MNRAS.475..448T says so explicitly; 2019ApJ...884...48C, 2018ApJ...853..171G). Multiplying again by 100
  inflates gas mass 100x; using it as a dust opacity inflates dust mass 100x.
- **Units.** 1 m2/kg = 10 cm2/g (general). Galaxy papers quote m2/kg, disk papers cm2/g.
- **Optical depth.** Thin masses of bright compact sources are lower limits (2018A&A...619A.161C,
  2015A&A...573L...1O, 2017A&A...604A...6S, 2016ApJ...832..178V, 2014ApJ...783L..13P). A lower spectral index
  can come from optical depth, not grain growth (2018A&A...619A.161C).
- **Temperature dominates.** Factor 2 in T gives about factor 2 in mass (pack validation list);
  2017ApJ...838..114K finds 10 K gives 2x higher and 25 K about 2x lower masses than 15 K;
  2020ApJ...894L..14L finds 50 K lowers core masses 3x vs 20 K. 2020ApJ...894L..14L admits T_d at
  2000 au is unknown. The isothermal assumption can bias masses either way, and papers state this
  differently: 2016MNRAS.457.4536W calls its masses upper limits because of the isothermal assumption;
  2016ApJ...833L...6C says its dust mass may be underestimated because warm dust dominates the SED peak;
  see also 2017MNRAS.468L..87C.
- **Opacity uncertainty is a factor 2 to 3 in the papers that quote it.** Factor 2 (2018ApJ...855...24P,
  2015ApJ...808..102K), factor 2-3 (2016A&A...593L..14F), factor 3 between Hildebrand and OH94
  (2014ApJ...796....1T). Large grains can hide mass, so masses are lower limits (2015ApJ...808...69B,
  2016MNRAS.458L..29C). Total mass uncertainty can be larger: 2013ApJ...764L..14Z quotes its disk mass as a
  lower limit with a factor-five uncertainty.
- **Gas-to-dust is not universal.** It rises at low metallicity (2020ApJ...892...66M, 2020ApJ...892..147S),
  differs for AGB envelopes (2024A&A...686A.274V), and disk gas masses from dust conflict with CO by about
  10x (2016ApJ...828...46A). Dust-based gas misses the atomic phase (2020ApJ...892...66M).
- **Resolved-out flux.** Interferometers miss extended emission: continuum interferometer-to-single-dish
  ratio 0.53 in 2014ApJ...787...48X, N(H2) 4x low in 2024ApJ...968L..19F. Line emission suffers the same way
  (CO example: only 43% of single-dish flux recovered in 2016ApJ...832..148V).
- **Point-source limits and local noise.** A limit quoted for a point source (2017ApJ...842....8M) does not
  apply to extended emission, and noise can be locally enhanced (gap rms in 2024ApJ...974..102S).
- **Lensing.** Apparent masses of lensed galaxies must be divided by the magnification; a single
  magnification is a simplification (2016ApJ...822...80S).
- **SED masses on other conventions.** SED codes carry their own dust composition and opacity; reconcile
  before comparing (2025A&A...694A..82S divides CIGALE masses by 2).
- **Contaminating emission.** Free-free, synchrotron, the stellar photosphere and line emission all add to
  the continuum (2016A&A...591A..73G, 2013ApJ...762L..21M, 2013ApJ...774L...7M).
- **Distance.** Mass scales as d^2; distance can dominate limit uncertainties (2015A&A...583A..66H) and
  disputed distances change masses (2014ApJ...791..108F, 2017A&A...603A..10B).
- **Core definition.** Core boundaries and thresholds change masses by 10-40% (2015MNRAS.449..715W) and are
  subjective (2013ApJ...779...96T, 2019ApJ...871..185L).
- **Unstated settings.** Cards most often flag as missing: CASA version (36), self-calibration intervals
  (18 + 13), line-free channels (12 + 12 + 10 under different wordings), flux-scale uncertainty (9), PB
  correction (8). State all of these.

## Verification checks

What the papers did:

- **Vary T_d and beta** and report the spread: T 15-35 K gives 25-50% systematic (2020ApJ...892...66M);
  20-30 K (2018ApJ...854L...4R, 2016ApJ...833...12R); 1.5x T test of tau (2018A&A...619A.161C); 50 K and
  random-T appendix (2020ApJ...894L..14L); other T prescriptions repeated (2020A&A...633A.114S).
- **Vary the opacity** (Hildebrand vs OH94: 2014ApJ...796....1T) or bracket with grain size
  (100 um vs 1 mm grains: 2024ApJ...974..102S).
- **Explicit error budget**: 30% kappa, 15% flux calibration, about 10% temperature (2014ApJ...787...48X);
  mass about 40% and column density about 35% (2020ApJ...890...76N).
- **Brightness-based optical depth check** (2018A&A...619A.161C), with scattering or thick pixels
  excluded in 2020A&A...644A..11L.
- **Independent mass**: CO-based gas mass (2021A&A...652A..98G median offset 0.23 dex;
  2018Sci...362.1034D), H13CO+ or other tracers, earlier ALMA or single-dish fluxes
  (2017ApJ...842....8M, 2024ApJ...968L..19F), full SED fit as a sanity check (CIGALE in the aggregates).
- **Physical plausibility**: 2020ApJ...890L..14T rejected uncoated-grain opacities because they gave a shell
  mass above the star's possible initial mass.
- **Detection completeness**: injection-recovery for faint compact sources (2024ApJ...974..102S); 5 sigma
  mass sensitivity per beam (2020ApJ...894L..14L).

What a careful referee adds:

- Recompute one mass from the quoted F_nu, d, kappa, T (the 0.57 Earth-mass sanity number above).
- Confirm the opacity is per dust or per gas and that gas-to-dust is applied once.
- Confirm the flux is PB-corrected, line-free, and free of free-free and stellar flux.
- Compare the peak intensity with f B_nu(T_d) before accepting "optically thin", and check resolution
  (filling factor) and scattering: a low beam-averaged brightness alone is inconclusive.
- Check that mass limits state the assumed size and optical depth, and use the local PB-corrected noise.
- Check that limits use the same kappa and T as detections and that censored data are handled with
  survival analysis.

## Source cards

The full list with titles is in `references/sources.md` (generated). The most informative cards for this
technique:

- 2016ApJ...828...46A: Lupus disk survey; T 20 K, 10 cm2/g at 1000 GHz, beta 1; ASURV.
- 2020A&A...633A.114S: brown-dwarf disks; kappa_890 = 2 cm2/g; repeats with other T laws; linmix.
- 2015A&A...583A..66H: closed-form M_dust = 0.566 F (d/140)^2 M_earth; distance-dominated limits.
- 2018A&A...619A.161C: crescent mass, tau from T_b, lower limits.
- 2014ApJ...796....1T: component subtraction; Hildebrand vs OH94 factor 3.
- 2017ApJ...842....8M: Fomalhaut belt; radiative-equilibrium T; mass limit for a point source.
- 2025A&A...693A.151M: 74 debris belts; kappa 0.23 m2/kg at 1.33 mm; T(R) law.
- 2020ApJ...894L..14L: CMZ cores; OH94 0.899 cm2/g; T sensitivity appendix.
- 2020ApJ...890...76N: clump SED for T and beta; core masses with 40% error.
- 2020A&A...635A...2S: T_d by evolutionary class (20/50/100 K).
- 2019A&A...628A..27B: hot-core column densities at 150 K, mu 2.8.
- 2020ApJ...892...66M: ASPECS stacking; Kovacs thin formula, CMB, metallicity-dependent gas-to-dust.
- 2018Sci...362.1034D: hot DOG; 50-100 K bracket; dust vs CO gas.
- 2021A&A...652A..98G: GATOS tori; dust vs CO masses agree to 0.23 dex.
- 2014ApJ...787...48X: error budget; interferometer/single-dish ratio.
- 2014MNRAS.438.1267S: SMG dust masses with kappa_870 = 0.15 m2/kg and gas-to-dust 90 +/- 25.
- 2020ApJ...891..164S: LMC hot core; dust-to-gas 0.0027 scaled by metallicity; three T values.
- 2020ApJ...890L..14T: AGB shell mass; plausibility rejects an opacity.
- 2015A&A...573L...1O: red supergiant dust; thin-limit lower limits; resolved-out flux.
- 2019MNRAS.488.1005P: RT conversion of flux limits to circumplanetary disk mass limits.
- 2024ApJ...974..102S: spectral index, grain-size-dependent kappa, injection-recovery.
- 2016ApJ...819..102V: T = 25 (L/Lsun)^0.25 for low-mass disks.
- 2017ApJ...838..114K: explicit T sensitivity (10 / 15 / 25 K).
