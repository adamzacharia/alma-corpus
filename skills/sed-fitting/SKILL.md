---
name: alma-sed-fitting
description: "Fit (sub)mm and far-IR photometry that includes ALMA fluxes to get dust temperature, emissivity index beta, L_IR / L_FIR, dust mass and IR-based SFR, with a single or general-opacity modified blackbody, IR templates, or panchromatic energy-balance codes (MAGPHYS, CIGALE). Use when an agent must turn ALMA continuum fluxes (plus Herschel, SCUBA-2, Spitzer, radio) into dust or star-formation quantities, pick fixed T_dust/beta for a single-band source, decide between MBB, templates and MAGPHYS/CIGALE, or check someone else's SED fit. Built from 989 ALMA papers (2012-2026)."
---

# Dust SED fitting (modified blackbody, templates, panchromatic codes)

Fits the thermal dust SED to get T_dust, beta, L_IR (or L_FIR), dust mass and SFR. When the far-IR data are sparse
(for example the quasar-host papers that fix T=47 K and beta=1.6, see the table), the answer is set by
**assumptions** (T_dust, beta, opacity regime, IMF, which wavelength range "L_IR" means) rather than by the data.
The two mistakes that matter most: (1) quoting a T_dust or L_IR that the wavelength coverage cannot constrain as if
it were measured, and (2) mixing conventions (8-1000 um L_IR vs 42.5-122.5 um L_FIR, Chabrier vs Salpeter SFR
constants, SFR averaging timescale, optically thin vs general opacity, opacity per dust mass vs per gas+dust mass,
fitted T_dust vs peak temperature) when comparing to the literature.

Counts come from the evidence pack (`skills/packs/sed-fitting.md`, 989 papers, 558 of them high-z galaxies): its
aggregates or my count of distinct bibcodes in its parameter/assumption lines, as stated. Those lines cover only part
of the 989 papers, so counts are lower bounds. Many tagged papers fit non-dust SEDs (afterglows, jets, YSO grids,
disks). Some examples are papers that the current pack lists only bibliographically; they were checked against the
earlier pack and are kept as examples, not counted.

## When to use

- Turning ALMA continuum fluxes (alone or with Herschel/SCUBA-2/Spitzer) into T_dust, beta, L_IR, SFR_IR or
  M_dust for galaxies, quasar hosts, nearby nuclei or Galactic clumps; choosing fixed T_dust and beta for one band.
- Deciding between a modified blackbody (MBB), IR templates, or an energy-balance code (MAGPHYS, CIGALE).
- Removing AGN, synchrotron or free-free contributions before fitting the dust.
- Reviewing a published or colleague's SED fit for convention mismatches and over-claimed precision.

## When not to use

| Situation | Use instead |
|---|---|
| Protoplanetary or debris disk SED with geometry (RADMC-3D, MCFOST, DIAD, DALI, e.g. 2019ApJ...878..103R) | `radiative-transfer-modelling` skill |
| Single-band dust or gas mass via a Rayleigh-Jeans calibration (2017ApJ...844..123F) | `dust-continuum-mass`, `gas-mass-co-conversion` |
| Spectral index between two ALMA bands, beta from alpha (2015ApJ...798..124R) | `spectral-index` |
| Synchrotron / afterglow / jet SEDs (2019ApJ...871...73H, 2023NatAs...7...80U) | `free-free-synchrotron`, `variability-time-domain` |
| YSO classification with Robitaille-type grids or Tbol/Lbol (2015ApJ...808...97Y, 2021A&A...648A..41V) | general YSO SED practice; this skill covers only the dust MBB part |
| Stacked fluxes of undetected populations | `stacking`, then come back here for L_IR |

## Steps

**1. Decide what you are fitting and what the data can support.**
- Rules seen: fix beta=1.8 always, the mid-IR slope alpha=2.5 with fewer than 4 far-IR points and T_dust=35 K
  with fewer than 2 (2017ApJ...840..101C); at least 4 detected bands for a photo-z survey (2014ApJ...788..125S);
  only convex SEDs over at least 4 adjacent Herschel bands for Galactic clumps (2025A&A...696A.149M); drop the
  stellar component where optical-NIR data are missing "to prevent overfitting" (2024ApJ...964...95S).
- One continuum point does not constrain T_dust (2015ApJ...807..180W); L and SFR can then be uncertain by orders
  of magnitude (2015ApJ...813...45L).
- With two or more points, identifiability depends on where they sit relative to the rest-frame peak, which
  parameters are free, and the T-beta degeneracy (general practice: T and beta anti-correlate, so a higher beta
  fits the same photometry with a lower T; rest-frame points near 200 um are not yet Rayleigh-Jeans at 30-50 K and
  still depend on T). Without points near the peak, T, tau and beta
  cannot be constrained together (2016ApJ...832..187B).

**2. Build the photometry table.**
- ALMA flux: total flux from a Gaussian or uv-plane fit (CASA `imfit`, 7 mentions in the pack aggregate), not peak
  flux, for resolved sources. Interferometers can lose extended flux: one paper propagates the missing-flux range
  as the error (2014A&A...567A.125G), another drops the ALMA point from the MBB fit (2018MNRAS.475..448T).
- Same emission in every band: a common solid angle (2017ApJ...840...72L), high-resolution ALMA fluxes left out of
  a fit to low-resolution FIR points (2021A&A...648A..41V), or an admission that sizes were not matched
  (2015ApJ...801...82H). List every excluded point.
- ALMA continuum hygiene: record line-free channels and the continuum method, check line contamination
  (2024ApJ...962....1S had almost no line-free USB channels), confirm primary-beam correction and use local noise
  off-centre. In the pack's "not stated" aggregate, line-free channel variants add up to 79 and primary-beam
  correction variants to 21 (my sum of the listed labels; mentions, not unique papers).
- Bandpass and colour corrections: model fluxes must be on the same convention as the catalogue fluxes. Either
  synthesize photometry through each filter or apply documented colour corrections, and say whether the inputs were
  already corrected. Seen: Herschel colour corrections assuming an MBB with beta=2 (2024A&A...687A.217D); SPIRE
  colour/aperture corrections iterated with a power-law SED from the 250 and 350 um fluxes (2023MNRAS.519.5807D);
  a photometry table given "before color corrections" (2024AJ....168..142L).
- Low-resolution Herschel/SCUBA-2: deblend with ALMA positions as priors (iterative lens subtraction,
  2016A&A...596A..75S; super-deblending, 2024A&A...690A..55S; fits with and without SPIRE, 2018ApJ...859...35G; a
  fixed 25% of the SCUBA flux given to the quasar of a pair, 2020MNRAS.493.3744F, source allocation, not AGN heating
  removal). Prior-based deblending can bias against sources faint in the prior band (general caution).
- Keep three kinds of extra uncertainty apart (table in `references/parameters.md`):
  - Calibration floors on input fluxes: ALMA 10% (2024MNRAS.530.4887W, 2021ApJ...918...76C), or band-dependent
    5% (Bands 3-4), 10% (6-7), 20% (8-9) (2024ApJ...974..306S); other instruments 5-20%. ALMA band dependence is a
    different thing from differences between instruments.
  - Deblending or model uncertainty: 35% on the lens-model flux used in deblending (2016A&A...596A..75S).
  - Systematics on outputs: 0.1 dex added in quadrature to MAGPHYS outputs (2020ApJ...901...79A).
- Upper limits: keep >3 sigma points and treat the rest as 3 sigma limits (2024A&A...690A..55S) or follow the
  code's convention (BayeSED takes a negative flux error as a limit, 2024ApJ...964...95S). The model must never
  exceed a limit (2021A&A...649A.152K); limits treated as detections make the fit an upper limit
  (2017MNRAS.468.4205K). State which you used.

**3. Remove what is not star-formation-heated dust.**
- Synchrotron and free-free: extrapolate from radio with fixed indices (alpha_synch=-0.8, alpha_ff=-0.1,
  2017A&A...597A...5M) or fit grey-body + free-free + synchrotron together (2021A&A...656A..46M). In radio galaxies
  the mm continuum can be synchrotron, so SFRs become upper limits (2016A&A...591A..73G).
- AGN: subtract a QSO template from SDSS+WISE (2017ApJ...844..123F), assume a fixed share (20% of L_IR,
  2024ApJS..275...36F; 50% for luminous QSOs, 2021A&A...645A..33B, 2024A&A...689A.220T), or fit an AGN component
  (CIGALE Fritz/SKIRTOR, 2024ApJ...962....1S, 2024ApJ...965..108U; CLUMPY in BayeSED, 2024ApJ...964...95S).
  Thresholds: AGN significant if >=20% of L_IR (2018MNRAS.478.3721S); keep the AGN component only if Delta BIC > 10,
  BIC = chi2 + k ln(n) (2024ApJ...965..108U). Quote the cut.
- AGN heat can leak into a free cold component: one Hot DOG paper limited T_dust to 30-50 K instead of 10-100 K
  and based its results on that fit (2024ApJ...964...95S). If the AGN share is unknown, call SFR_IR an upper limit
  (2021ApJ...908..235I). Old-star (cirrus) heating also inflates SFR_IR (2019MNRAS.486..560S calls its SFRs
  conservative upper values). The subtraction carries at least 0.13 dex (2017ApJ...844..123F) and extreme obscuration
  can hide an AGN (2018ApJ...859...35G); propagate it and test a buried-AGN alternative.
- Rest-frame cut: drop points shortward of rest 50 um for a single cold MBB (2016ApJ...822...80S). This protects
  the cold fit but does not recover warm-dust luminosity (step 6).
- Lensing: correct with the magnification; papers assume differential magnification negligible
  (2025ApJ...989..115T) or leave lens-model uncertainty out of the errors (2024ApJ...965..108U). Say which.

**4. Choose the model.**
- Optically thin MBB (general practice):
  S_nu,obs = (1+z) M_d kappa_nu0 (nu_rest/nu0)^beta [B_nu(T_d(z)) - B_nu(T_CMB(z))] / D_L^2, with
  T_CMB(z) = 2.73 (1+z) K. M_d is a dust mass only if kappa is per gram of dust.
- General opacity (galaxies): (1 - exp(-tau_nu)) B_nu(T), tau_nu = (nu/nu_0)^beta, i.e. tau=1 at lambda_0. Values
  fixed: 100 um (2014ApJ...785..149S, 2024A&A...691A.133V), 125 um (2024ApJ...964...95S), 150 um
  (2017ApJ...844..123F), 200 um (2014A&A...562A..67G, 2015Natur.519..327W). It gives warmer T: 58.5 K vs about
  33 K for one source (2014A&A...562A..67G). One z ~ 5.5 paper kept both 100 and 200 um where data could not decide
  (2020MNRAS.498.4192F). Normalization and mass in this model: step 6.
- Debris-disk "break wavelength" laws are a different thing: a blackbody multiplied by (lambda0/lambda)^beta beyond
  lambda0 (lambda0 = 380 um, beta 2.3 cold; 160 um, beta ~0 warm; 2024A&A...686A.206Y), lambda0 = 100 um with beta
  0.65 when far-IR data are absent (2025A&A...703A..15M), lambda0 = 70 um (2015A&A...583A..66H). Do not treat these
  lambda0 values as tau=1 wavelengths.
- MBB + mid-IR power law (alpha 1.5-2.5; fixed 2.0 in 2024A&A...691A.133V, 2020MNRAS.498.4192F).
- Two-temperature MBB: T_cold fixed 35 K, beta=1.5, free warm component (2014ApJ...790..160S).
- Empirical templates, two kinds. Freely rescaled to the ALMA flux: Bethermin 2017 (2020A&A...643A...2B;
  main-sequence vs starburst templates by offset from the main sequence, 2024A&A...681A.110W), Magdis 2012 via
  STARDUST (2024A&A...690A..55S). Luminosity-dependent templates picked by luminosity and used without rescaling:
  Chary & Elbaz 2001 (2021ApJ...915...46C). Say which; rescaling a luminosity-dependent template breaks its tie between shape and luminosity (general
  practice). More template examples: `references/parameters.md`.
- Panchromatic energy balance: MAGPHYS (photo-z extension, 2024ApJ...965..108U), CIGALE (2018ApJ...859...35G,
  2024ApJ...965..108U with polar dust) and BayeSED (2024ApJ...964...95S), when you need M_star and SFR with dust.
- Resolved Galactic maps: PPMAP with 8 MBB temperature components, beta=1.8, kappa_300 = 0.1 cm2/g per gas+dust,
  optically thin (2024A&A...687A.217D).

**5. Fit.**
- chi2 grid or Levenberg-Marquardt for MBBs with several points (2014A&A...562A..67G; mpfit with lambda_0 = 100 um,
  2020AJ....159..288M).
- MCMC (emcee is the most-named sampler, 73 mentions, many non-dust) or other samplers (PyMC3 NUTS,
  2020MNRAS.498.4192F; MultiNest in BayeSED, 2024ApJ...964...95S) with explicit priors. Priors seen: flat T 20-50 K,
  beta 0.5-4 (2024MNRAS.530.4887W); flat T, Gaussian beta 1.8 +/- 0.5 (2020MNRAS.498.4192F); flat A, T_d, M_d,
  beta with A capped by the beam area (2025A&A...695L..15F); T < 100 K **observed-frame** (2014A&A...568A..92M).
  More priors and sampler settings: `references/parameters.md`.
- Fixed walker and step counts do not prove convergence: check autocorrelation time or effective sample size and
  look for posteriors piled against a prior bound (general practice).
- CIGALE/MAGPHYS: report the likelihood-weighted PDF mean, log-uniform priors for SFR, M_star, L_dust, M_dust and
  uniform for T_dust (2024ApJ...965..108U).

**6. Derive quantities.**
- L_IR: integrate over rest 8-1000 um. 19 listed papers integrate over 8-1000 um whatever they call it (some label
  it FIR or TIR, e.g. 2022ApJ...941...47S, 2021ApJ...909..204F, 2017ApJ...836....8T); 42.5-122.5 um L_FIR in 4
  papers (2017ApJ...836....8T, 2021ApJ...908..235I in the lists; 2020MNRAS.498.4192F, 2014ApJ...796...84R in the
  excerpts); 3-1100 um in 2020MNRAS.498.4192F. How counted and the bibcode list: `references/parameters.md`. Name
  each integral by its limits, not by the paper's label.
- An MBB alone misses warm dust (about 20% of L_FIR, 2017ApJ...844L..10S). For an 8-1000 um L_IR from a cold MBB,
  add a mid-IR power law or warm component, use a template, or quote the extrapolation uncertainty.
- Temperature: say which one. T_SED is the fitted MBB parameter. T_peak is a convention, not a physical
  temperature (Wien's 2898 um K holds exactly only for a pure blackbody's B_lambda peak). T_peak = 2898 um K / lambda_peak with the peak of
  the rest-frame S_nu taken in wavelength convention (2020MNRAS.498.4192F). 2024ApJ...965..108U uses 5099 /
  lambda_peak with the peak taken "in the dimension of Jy" and calls it "not the intrinsic temperature"; its
  1.7 x T_dust is that survey's own conversion, not a general rule. Compute each model's peak yourself from the
  fitted SED and state whether it is the peak of S_nu or of nu S_nu. For one z ~ 5.5 galaxy T_SED vs T_peak is
  40.8 vs 33.9 K (lambda_0 = 100 um) and 48.4 vs 30.8 K (200 um) (2020MNRAS.498.4192F).
- SFR: apply the constant to L_IR,SF (AGN and other non-SF heating removed), Lsun in, Msun/yr out. Seen: 1.40e-10
  L'_IR (Chabrier, AGN removed: 1.40e-10 x 0.41 x 1.34e13 = 770 Msun/yr, 2024ApJ...962....1S, my arithmetic),
  1.0e-10 (Kennicutt98 with Chabrier, 2017ApJ...844..123F), 1.496e-10 (Kroupa, 2024A&A...689A.220T), 1.7e-10
  (Kennicutt98, 2021ApJ...915...46C). Full list in `references/parameters.md`. Convert IMFs explicitly.
- SFR averaging timescale: state it next to every SFR and before comparing codes. Seen: 10 Myr average
  (2024ApJ...965..108U), 100 Myr SFH average (2024ApJ...964...95S, 2025ApJ...989..115T), instantaneous GalaPy SFRs
  (2025A&A...699A.183H), constant SF over 100 Myr behind an L_FIR calibration (2021A&A...652A.128J). An IR
  calibration and a 10 Myr code SFR are not the same quantity; give the SFH assumption too.
- M_dust, optically thin: invert the thin formula above with a stated kappa (see table). Check kappa's mass basis:
  per gram of gas+dust (0.1 cm2/g (nu/1 THz)^beta "includes a gas-to-dust ratio of 100", 2018MNRAS.475..448T) gives
  total gas mass, so do not multiply by a gas-to-dust ratio again.
- M_dust, general opacity: the model needs a geometry. With emitting area A and solid angle Omega = A / D_A^2,
  S_nu,obs = Omega [1 - exp(-tau_nu)] [B_nu(T_d) - B_nu(T_CMB(z))] / (1+z)^3, tau_nu = kappa_nu M_d / A
  (general practice; it reduces to the thin formula when tau << 1). Fit A and M_d together (flat priors on A, T_d,
  M_d, beta, A capped by the beam area, 2025A&A...695L..15F) or take the solid angle from resolved sizes
  (2024A&A...689A.220T). Do not reuse the thin conversion on a general-opacity fit without justifying it.
- CMB (general practice, da Cunha et al. 2013): heating gives
  T_d(z)^(4+beta) = T_d0^(4+beta) + T_CMB0^(4+beta) [(1+z)^(4+beta) - 1]; the contrast term subtracts
  B_nu(T_CMB(z)). Papers use contrast only (2018MNRAS.481.1631B) or both (2020MNRAS.493.4294B); 12 listed papers
  mention the CMB (my count). If your T_d is already the heated temperature, apply only the contrast term. T_d must
  exceed T_CMB(z) = 2.73 (1+z) K: 14.7 K at z=4.43 (2024A&A...684A..56K), 23.4 K at z=7.5 (2017MNRAS.466..138K).
  An assumed 25 K falls below T_CMB at z > 8.16 (my arithmetic, 25/2.73 - 1).

**7. Validate** (see Verification checks).

## Parameter defaults and ranges

Counts: my count of distinct bibcodes in the pack's parameter/assumption lines (regex, stated per row in
`references/parameters.md`), all fields unless the row says otherwise.

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| Fixed (T_d, beta), quasar hosts (mostly z > 5.7) and some z ~ 2-2.5 quasar systems | 47 K, 1.6 | 35-60 K | 9 pair 47 K with 1.6 | 2019ApJ...879..117K, 2021ApJ...908..235I, 2024ApJ...977..190X; 35 K alternative (2024ApJ...972..116I); 60 K without Herschel (2021A&A...645A..33B) |
| Fixed T_d, SMGs / DSFGs (z ~ 2-3) | 35 K | 25-45 K | 15 mention 35 K (includes local LIRGs and Galactic clumps) | 2014ApJ...795....5O, 2015A&A...584A..78C, 2024ApJS..275...36F, 2025A&A...699A.324H |
| Fixed T_d, z > 4 star-forming galaxies, one band | 45-47 K | 30-55 K | 3 | 2021A&A...646A..26B (45 K; 35/55 K tested), 2026MNRAS.546ag049F (46 K), 2025A&A...700A.277C (47 K) |
| beta (fixed), galaxies and Galactic dust | 2.0 (27), 1.6 (16), 1.5 (16), 1.8 (15) | 1.2-2.5 (1.2 in 2014ApJ...795L..25R) | counts all fields | 2018Sci...362.1034D (1.8), 2024ApJ...972..116I (1.6) |
| beta, debris disks and stellar shells | n/a | 0-1 | examples | 0.65 (2025A&A...703A..15M), ~0 warm (2024A&A...686A.206Y), 0 grey body (2021A&A...655A..98A) |
| beta measured (free), galaxies | about 2 | 1.6-2.4 at z ~ 5.5 | examples | 2020MNRAS.498.4192F, 2023MNRAS.523.4654T (2.14 +/- 0.17) |
| Opacity regime, galaxies | optically thin | general opacity, lambda_0 = 100-200 um | examples (step 4) | 2014A&A...562A..67G, 2020MNRAS.498.4192F; disk break wavelengths 70-380 um are a separate law |
| kappa per dust mass | 0.077 m2/kg at 850 um / 353 GHz | galaxies 0.0383-0.15; with stellar and debris-disk papers up to 0.17 m2/kg | 5 use 0.077 | 2021A&A...645A..33B, 2024MNRAS.530.4887W, 2017ApJ...851...98T (0.0383), 2020MNRAS.493.4294B (0.15), 2019A&A...626A.126A (0.17) |
| Gas-to-dust | 100 | adopted 60-200; 300 as a sensitivity test | 30 mention 100 (most are disk or Galactic models) | 2014A&A...567A.125G (60), 2025A&A...695L..15F (200, Hot DOG), 2021ApJ...918...76C (1:300 tested) |
| IMF for SFR | Chabrier | Salpeter, Kroupa | 61 / 20 / 14 | 2024A&A...689A.220T (Kroupa) |
| Integration range | 8-1000 um | 42.5-122.5 um, 3-1100 um | 19 / 4 / 1 | 2018MNRAS.478.3721S, 2017ApJ...836....8T, 2020MNRAS.498.4192F |
| Calibration floor | 10% (ALMA) | 5-20% by instrument or ALMA band | table in references | 2024MNRAS.530.4887W, 2024ApJ...974..306S, 2024A&A...686A.122A |
| Fixed z for unknown-z sources | 2.5 | 2-3 | 4 | 2017ApJ...844..123F, 2015ApJ...807..128S, 2025A&A...699A.324H |

Longer tables (opacity laws, SFR constants, calibration floors, samplers, code settings, integration-range bibcodes,
single-band sensitivity ranges) are in `references/parameters.md`.

## Software

Mentions from the pack's "Software named in the matched steps" aggregate; mentions in any matched step, not counts
of dust-SED fits.

| Software | Mentions | Used for | Examples |
|---|---|---|---|
| CIGALE | 98 | energy balance with AGN (Fritz, SKIRTOR), polar dust, radio | 2018ApJ...859...35G, 2024ApJ...965..108U |
| MAGPHYS | 87 | energy balance, M_star + SFR + M_dust; no AGN component | 2020ApJ...901...79A, 2024ApJ...965..108U |
| emcee | 73 | MCMC for MBB and template normalization; many non-dust uses | 2018ApJ...853..195W |
| MultiNest, PyMC3 | 10, example | BayeSED nested sampling; NUTS for an MBB + power law | 2024ApJ...964...95S, 2020MNRAS.498.4192F |
| Bagpipes, Prospector, dynesty | 31, 18, 8 | Bayesian stellar SED (M_star, SFH) | 2025ApJ...989..160I |
| EAZY, LePhare, hyperz | 24, 17, 13 | photometric redshift | 2024ApJ...968...34W |
| STARDUST | 8 | template FIR fit after super-deblending | 2024A&A...690A..55S |
| RADMC-3D, MCFOST, DALI | 20, 16, 15 | disk radiative transfer (out of scope) | 2019ApJ...878..103R |

## Pitfalls

- **Single-band "measurements".** A fixed-SED L_IR carries about 0.2-0.3 dex systematics (2015MNRAS.453L..83M,
  2020MNRAS.491.4724F), 0.3 dex without Herschel vs 0.1 dex with it (2021A&A...645A..33B), 0.5 dex for template
  choice (2020MNRAS.496..875R). Quote the assumed T and beta next to every number.
- **Cold priors at high z.** For four infrared-bright z ~ 5.5 main-sequence galaxies, peak temperatures are
  38 +/- 8 K, and colder earlier assumptions would underestimate single-band L_IR by 0.3-0.6 dex
  (2020MNRAS.498.4192F). The authors say the sample, chosen among the IR-brightest, likely misses more metal-poor
  systems, so treat this as a warning about priors, not a population-wide correction. 35 K instead of 47 K makes
  luminosities about 2x smaller (2021ApJ...908..235I).
- **Different "dust temperatures".** T_SED and T_peak differ by 7-18 K for the same galaxy (2020MNRAS.498.4192F);
  the 1.7 factor of 2024ApJ...965..108U is that survey's calibration. Compare like with like (step 6).
- **T-beta degeneracy.** Papers fit beta fixed and free (2019ApJ...879..117K) or average two pairs
  (2017MNRAS.465.4390B: 47 K/1.6 and 41 K/1.95). Do not compare T_d across papers with different beta.
- **Optically thin vs general opacity.** 58.5 K vs about 33 K for the same data (2014A&A...562A..67G); optically
  thin maps can bias T and mass at high column (2024A&A...687A.217D); an optical-depth correction raised a field's
  maximum T from 39 to 44 K (2024A&A...686A.122A). The thin mass formula does not apply to a thick fit (step 6).
- **Single-temperature dust masses.** A warm (~45 K) greybody can miss the colder diffuse ISM that holds most of the
  mass (2024ApJ...964...95S).
- **Code and model systematics.** For the same sources CIGALE and MAGPHYS scatter by 0.17 dex in L_dust, 0.33 dex in
  M_dust, 0.59 dex in SFR and 7.8 K in T_dust; photo-z vs fixed z adds 0.47 dex in L_dust (2024ApJ...965..108U).
  Check the SFR timescales match before blaming the codes.
- **CMB at high z.** Ignoring it biases T and M_d (corrected in 2023MNRAS.523.4654T; skipped in
  2015ApJ...807..180W). Direction (general practice): the observed flux is measured against the CMB, so at fixed
  T_d leaving out the contrast term B_nu(T_CMB(z)) underestimates M_d. Never correct heating twice; keep
  T_d > T_CMB(z).
- **Uncertainty budgets that leave things out.** Fit errors excluding absolute calibration (2021A&A...656A..46M);
  kappa uncertainty left out of dust-mass errors (2024ApJ...964...95S; about 25% not propagated,
  2021A&A...655A..98A).
- **Opacity and mass factors of 2.** 0.077 vs 0.15 m2/kg at 850 um; Dunne et al. 2000 instead of Hildebrand doubles
  M_d (2019PASJ...71...71H); CIGALE dust masses divided by 2 to match Draine07 (2025A&A...694A..82S). A kappa per
  gram of gas+dust (2018MNRAS.475..448T) gives gas mass, about 100x a dust mass.
- **Blending, apertures, redshift.** Deblending assumptions often cannot be verified (2016A&A...596A..75S); high
  fitted T can reflect residual blending (2024ApJ...965..108U); assuming z=2.5 makes results "less reliable"
  (2017ApJ...844..123F).
- **Unstated settings.** In the pack's "not stated" list (label variants, mentions not papers), the five
  flux-calibrator / flux-scale-uncertainty variants add up to 51 (17+13+9+7+5, my sum). Cards often note that SED
  code priors and grids are not given (2017ApJ...844..123F; "other priors and likelihood not stated" for
  2024ApJ...964...95S). State yours.

## Verification checks

What papers did:
- Refit with the fixed parameter freed and confirm it comes back: T_cold free recovered 35 K (2014ApJ...790..160S).
- Compare optically thin vs general opacity (2014A&A...562A..67G; about 0.1 dex in L_IR, 2017ApJ...844..123F), and
  lambda_0 = 100 vs 200 um: T_peak and L_IR did not move, T_SED did (2020MNRAS.498.4192F).
- Refit with a narrower and a wider T prior (30-50 vs 10-100 K, 2024ApJ...964...95S).
- Cross-check codes (CIGALE vs MAGPHYS, 2024ApJ...965..108U; L_IR vs a stacked SED within 0.2 dex,
  2020MNRAS.498.4192F), after matching SFR timescale and SFH.
- Drop bands and refit: with and without SPIRE (2018ApJ...859...35G), unchanged without Herschel
  (2016A&A...596A..75S).
- Goodness of fit: median reduced chi2 0.52 (2024ApJ...962....1S); chi2/dof < 5 with residuals inspected and a grid
  extended when a fit fails (2024ApJ...965..108U); 86% of pixel data points within 1 sigma (2024A&A...687A.217D).
- Compare dust-based gas mass with CO-based and dynamical mass (within a factor 2 in 2020MNRAS.498.4192F).

What a careful referee adds:
- A table of every input flux with error, calibration floor (by instrument and ALMA band), colour-correction status,
  which points are limits or excluded and why, and the aperture or component model each comes from.
- ALMA line-free channels, a line-contamination check, primary-beam correction with local noise.
- The full prior list and sampler settings; T-beta contours; a convergence check; no posterior piled at a bound.
- Integrals named by rest-frame limits; the temperature named (T_SED, T_peak and its S_nu or nu S_nu convention);
  SFR with IMF, constant, averaging timescale and which luminosity (L_IR,SF) it used.
- For general-opacity fits, the area or solid angle and tau at the ALMA frequency.
- For AGN hosts, the subtraction uncertainty propagated and a buried-AGN alternative tested.
- For single-band sources, the spread in L_IR over a T_d and beta range chosen for the population and redshift
  (ranges in `references/parameters.md`), kept above T_CMB(z). These are conditional tests, not full bounds.

## Source cards

Full list: `references/sources.md` (all 989 papers). Most informative for this technique:

- 2020MNRAS.498.4192F: z ~ 5.5 MBB fits, lambda_0 test, T_SED vs T_peak, cold-prior L_IR bias and its limits.
- 2024ApJ...965..108U: CIGALE with AGN by Delta BIC, CIGALE vs MAGPHYS scatter, 10 Myr SFR, Jy-peak temperature.
- 2024ApJ...964...95S: BayeSED for Hot DOGs, T prior vs AGN leakage, 100 Myr SFH, SED-calibrated SFR.
- 2021A&A...645A..33B: QSO + MBB templates, 50% AGN share, L_IR sensitivity to T_dust.
- 2014A&A...562A..67G: optically thick vs thin MBB, L_IR and SFR.
- 2017ApJ...844..123F: QSO subtraction, general-opacity MBB, Monte Carlo errors.
- 2025A&A...695L..15F: general-opacity fit with emitting area and dust mass fitted together.
- 2024A&A...687A.217D: PPMAP maps, Herschel colour corrections.
- 2018ApJ...859...35G: CIGALE with AGN torus, with/without SPIRE test.
- 2024ApJ...962....1S: CIGALE for a z=6 quasar, f_AGN, SFR constant.
- 2024MNRAS.530.4887W: MBB priors, per-instrument calibration errors.
