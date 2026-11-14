---
name: alma-sz-effect
description: "Measure the thermal (and, where possible, kinetic) Sunyaev-Zeldovich decrement with ALMA and the ACA: subtract compact sources, forward-model a gNFW or shock pressure model at the measured uv points, report detection significance, Compton y, pressure profiles, M500, Mach numbers and SZ-plus-X-ray temperatures. Use when detecting or confirming galaxy clusters and protoclusters in Band 3/4, reconstructing ICM pressure or merger shocks, combining ALMA/ACA with ACT, SPT, Bolocam, Planck or MUSTANG-2 SZ data, searching for SZ halos around quasars, or checking someone else's SZ mass or significance. Built from 14 ALMA papers (2016-2024)."
---

# Sunyaev-Zeldovich effect measurements with ALMA/ACA

The SZ effect is a small negative signal in Band 3/4 (tens to hundreds of microJy) set by the line-of-sight
integral of electron pressure. ALMA and the ACA sample it only on scales below their largest recoverable scale,
so almost every paper fits a pressure model directly to the visibilities instead of reading numbers off an
image. The mistakes that matter most: (1) treating the filtered interferometric signal as the full SZ signal,
which biases amplitudes, masses and integrated Y low and makes pressure-model slopes degenerate
(2016ApJ...829L..23B, 2024A&A...689A..41V, 2024A&A...682A.186L, 2021A&A...650A.153D); and (2) leaving compact
radio or dusty sources in the data, which fill in or mimic the decrement (2020A&A...638A..70D,
2019A&A...629A.104G, 2019MNRAS.490.5134B).

> Always report: which arrays and bands entered the fit, how compact sources were modelled (spectral form, uv
> cuts), the pressure model and which of its parameters were fixed, priors and sampler, relativistic and kSZ
> treatment, cosmology, how significance was computed, and at least one external check (X-ray, another SZ
> instrument, or mock observations).

## When to use

- Confirming cluster candidates with short ACA Band 3 integrations and getting rough M500
  (2020A&A...638A..70D: SZ detected in 7 of 10 MaDCoWS clusters).
- Resolved ICM pressure and morphology in high-z clusters and protoclusters, z of about 1 to 2.2
  (2024A&A...689A..41V at z = 1.98, 2019A&A...629A.104G at z = 1.99, 2021A&A...650A.153D at z of about 1.13,
  2024A&A...682A.186L for the Spiderweb at z = 2.16).
- Merger shocks: pressure jump across a shock front gives a Mach number (2016ApJ...829L..23B El Gordo,
  2019A&A...628A.100D Bullet Cluster).
- Cool cores and inner pressure profiles at arcsec resolution (2020PASJ...72...33K Phoenix).
- Joint fits with lower-resolution SZ data that see the large scales ALMA misses: ACT (2024A&A...689A..41V,
  2021A&A...650A.153D compares with AdvACT), Bolocam plus Planck (2019MNRAS.487.4037D), MUSTANG-2 at 90 GHz
  (2020ApJ...891...90R, a multi-facility paper where ALMA is minor).
- Thermodynamics without X-ray spectroscopy: SZ pressure divided by X-ray density gives temperature
  (2024A&A...682A.186L, 2020PASJ...72...33K, proposed in 2020EPJWC.22800009E).
- Searching for hot circumgalactic gas around AGN and quasars (2019MNRAS.490.5134B single field,
  2024ApJ...969...56M stack of ten fields). Expect low significance.

## When not to use

- "Sz 65", "Sz 71", "Sz 98" are Lupus star names, and "Shakura-Sunyaev" is a disk model; papers on those are
  tagged by the regex but have nothing to do with SZ. For disks use the disk-substructure or uv-plane-fitting
  skills.
- Total cluster Y or masses out to r500 and beyond from ALMA alone: the arrays cannot constrain these scales
  (2020EPJWC.22800009E notes missing SZ data at 30 to 100 arcsec; 2020PASJ...72...33K cannot constrain
  temperature beyond 250 kpc). Add ACT, SPT, Planck, Bolocam or MUSTANG-2 data, or quote a model-dependent
  extrapolation clearly.
- Separating thermal from kinetic SZ with a single band: not possible without more frequencies
  (2024ApJ...969...56M, 2021A&A...650A.153D). Use a prior on the integrated flux at best.
- Pure dust or synchrotron continuum work on cluster members: use the continuum, spectral-index or
  source-extraction skills; here those sources are contaminants to remove.

## Steps

1. **Pick data and check uv coverage.** Goal: enough short spacings to see the decrement.
   - Papers use Band 3 (about 92 GHz) and add Band 4 to separate SZ from compact sources
     (2024A&A...689A..41V, 2021A&A...650A.153D). Band 3 near 92 GHz was chosen as a compromise between
     integration time and dust contamination, in a compact configuration (2019A&A...629A.104G, methods card).
   - ACA plus ALMA 12-m together is the norm (2019A&A...628A.100D, 2024A&A...689A..41V, 2020PASJ...72...33K);
     ACA alone suffices for detection but limits mass inference (2020A&A...638A..70D).
   - For weak signals check that the shortest-baseline bin is populated by many independent uv tracks and
     antenna pairs, not one (2019MNRAS.490.5134B checked more than 50 uv tracks and 20 antenna pairs).
2. **Model and remove compact sources.** Goal: a source-free uv dataset or a joint source model.
   - Point (Dirac delta) models fitted in the uv plane. Spectral forms seen: power law
     (2021A&A...650A.153D), modified power law with curvature for a central radio source (2021A&A...650A.153D),
     first-order polynomial (2024A&A...689A..41V), flat spectrum (2020A&A...638A..70D).
   - Isolate compact emission with uv cuts: lower uv cut of 11 klambda when fitting sources
     (2024A&A...689A..41V); CASA `uvmodelfit` on 12-m baselines longer than 30 klambda, then subtraction in the
     uv plane (2020PASJ...72...33K, methods card); subtraction of nine known sources in groups, brightest
     first (2019A&A...629A.104G, methods card).
   - For an extended radio galaxy, an upper uv threshold of 65 klambda made it unresolved across the jet so a
     point-component set could describe it (2024A&A...682A.186L).
   - Preferred practice in the newer papers: fit sources jointly with the SZ model and marginalize, rather
     than subtract and forget (2021A&A...650A.153D, 2020A&A...638A..70D, 2024A&A...682A.186L).
3. **Build the pressure model.** Goal: a model sky in SZ brightness for each band.
   - Spherical gNFW pressure (Nagai2007 form) integrated along the line of sight to Compton y, converted to
     brightness per band, multiplied by the primary beam, Fourier transformed and sampled at the data uv
     points (2021A&A...650A.153D, 2024A&A...689A..41V, 2019A&A...628A.100D).
   - Shape choices: universal profile of Arnaud2010 with free centroid, mass and inner slope
     (2021A&A...650A.153D); fixed shape with free M500 and z (2020A&A...638A..70D); eight literature templates
     (A10 UP/MD, M14 UP/NCC, L15 REF/8.0/8.5, G17 EXT) each with only M500 free (2024A&A...682A.186L); LeB15,
     A10, S16, McD14 templates with free mass (2019A&A...629A.104G).
   - Shocks: gNFW upstream plus a pressure boost at the shock radius from Rankine-Hugoniot,
     p_down/p_up = (5M^2 - 1)/4 (2016ApJ...829L..23B); power-law downstream with gNFW upstream and
     gamma = 5/3 (2019A&A...628A.100D).
   - Multiple subclusters: one gNFW component each, with an ordering condition on declination so the modes
     stay identifiable (2021A&A...650A.153D).
4. **Fit in the uv plane.** Goal: posteriors and a model evidence.
   - Nested sampling with `dynesty` is the most common sampler among on-topic papers (static:
     2024A&A...689A..41V; dynamic: 2019A&A...628A.100D; 2024A&A...682A.186L). Gaussian likelihood on unbinned
     visibilities (2024A&A...689A..41V). MCMC inside CASA was used in 2016ApJ...829L..23B; `emcee` with a
     full-covariance likelihood for MUSTANG-2 profiles (2020ApJ...891...90R).
   - Fast forward modelling: `galario` for the FFT and uv sampling (2019A&A...628A.100D). An FFT approximation
     agreed with CASA `simalma` to within about 4% (2019A&A...629A.104G).
   - Marginalize flux-calibration and redshift uncertainty with Gaussian priors (2024A&A...689A..41V;
     2019A&A...628A.100D used a normal(1, 0.05) scaling).
5. **Compute significance.** Goal: a detection claim that survives a referee.
   - Bayes factor between models with and without SZ, converted with sigma_eff = sqrt(2 Delta log Z);
     sigma_eff of about 3 or more is called robust (2020A&A...638A..70D). Delta log Z = 120.72 was quoted as
     15.6 sigma (2021A&A...650A.153D). That conversion assumes a Gaussian posterior and ignores prior volume
     changes (2021A&A...650A.153D).
   - Image-plane or uv-profile alternatives: total signal and S/N after source subtraction
     (2019A&A...629A.104G reports -190 +/- 36 microJy, 5.3 sigma, methods card); dirty-image significance as a
     cross-check (2020A&A...638A..70D).
6. **Derive physical quantities.**
   - M500 from the Arnaud2010 parametrization, which assumes self-similarity and hydrostatic equilibrium
     (2021A&A...650A.153D); Y500 to M500 with Arnaud2010 local scaling relations (2024A&A...689A..41V).
   - Average across pressure models: evidence-weighted mean (2024A&A...689A..41V) or Bayesian model averaging
     with model variance propagated (2024A&A...682A.186L).
   - Integrated SZ flux in a cylinder matched to an external catalog's r500, here 1.69 arcmin to compare with
     AdvACT (2021A&A...650A.153D).
   - Temperature: kT_e = P_e / n_e per X-ray annulus, assuming the ideal gas law (2024A&A...682A.186L); or a
     pseudo-temperature map from SZ divided by the square root of X-ray surface brightness, assuming constant
     temperature along the line of sight (2024A&A...689A..41V).
   - Mach number from the pressure jump, optionally with an X-ray prior on upstream pressure
     (2016ApJ...829L..23B, 2019A&A...628A.100D).
   - Image route, if needed: CASA `tclean` multi-scale joint 12-m plus 7-m mosaic with natural weighting,
     noise from half-split difference maps, image divided by a missing-flux factor of 0.94 calibrated on
     `simobserve` mocks, mean signal at 42 arcsec subtracted (2020PASJ...72...33K, partly from the methods card).
7. **Optional kinetic SZ.** Add a kSZ term per component and break the thermal/kinetic degeneracy with a prior
   on integrated SZ flux from a survey (2021A&A...650A.153D). Expect velocity errors of thousands of km/s.

## Parameter defaults and ranges

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| Band | Band 3 near 92 GHz | Band 3 alone to Band 3 + 4 | 6 (my count) | 2019A&A...629A.104G, 2024A&A...689A..41V |
| Pressure model | gNFW, Arnaud2010 shape | 1 template to 8 templates; free inner slope | 8 (my count) | 2021A&A...650A.153D, 2024A&A...682A.186L, 2019A&A...629A.104G |
| Free SZ parameters | M500 (+ centroid) | M500 only (centroid fixed to X-ray) to M500, centroid, inner slope, z | 4 (my count) | 2024A&A...682A.186L, 2020A&A...638A..70D |
| Centroid prior | uniform over ACA field | normal with sigma 14.3 to 15 arcsec; fixed to X-ray | 3 | 2021A&A...650A.153D, 2020A&A...638A..70D |
| Redshift | split-normal or Gaussian, marginalized | fixed | 2 | 2020A&A...638A..70D, 2024A&A...689A..41V |
| Flux-scale nuisance | normal(1, 0.05) | Gaussian priors | 2 | 2019A&A...628A.100D, 2024A&A...689A..41V |
| Point-source spectrum | varies | power law; flat; first-order polynomial; modified power law | 3 | 2020A&A...638A..70D, 2024A&A...689A..41V |
| uv cut for sources | lower cut 11 to 30 klambda | upper cut 65 klambda for extended radio galaxy | 3 | 2024A&A...689A..41V, 2024A&A...682A.186L |
| Relativistic correction | none (small at low T) | Itoh2004 / Nozawa2006; kT_e = 7 keV; X-ray projected T | 6 (my count) | 2020A&A...638A..70D, 2021A&A...650A.153D, 2020ApJ...891...90R |
| kSZ | neglected | fitted with integrated-flux prior | 4 | 2019A&A...628A.100D, 2024ApJ...969...56M |
| Cosmology | flat LCDM, Om 0.30, H0 70 | Planck H0 67.7, Om 0.307 | 4 | 2021A&A...650A.153D, 2024A&A...689A..41V |
| Mach prior (shock) | uniform 1 to 10 | free | 2 | 2019A&A...628A.100D, 2016ApJ...829L..23B |
| Detection threshold | sigma_eff of 3 or more | Bayes factor vs null | 2 | 2020A&A...638A..70D, 2024A&A...689A..41V |
| dynesty stop | Delta ln B = 0.01 | not stated elsewhere | 1 | 2024A&A...689A..41V |
| Line-of-sight integration | +/- 5 R500 | not stated in ALMA papers | 1 | 2020ApJ...891...90R |
| Compton-y background | 1.6e-6 | rarely stated | 1 | 2019A&A...629A.104G |

Counts marked "my count" are from reading the pack excerpts; the others count the bibcodes listed. Per-paper
setups are in `references/parameters.md`.

## Software

Pack aggregates count software over all 21 tagged papers (casa 6, dynesty 4, emcee 3, galario 1, simobserve 1,
casa simalma 1, tclean 1, colossus 1, ciao 1), but several casa and emcee hits come from off-topic disk
papers. Among the 14 on-topic papers (my count):

| Tool | Used for | Papers |
|---|---|---|
| CASA (`tclean`, `uvmodelfit`, `simobserve`, `simalma`) | imaging, compact-source fits, mock observations to calibrate filtering, MCMC in CASA | 2016ApJ...829L..23B, 2019MNRAS.490.5134B, 2019A&A...629A.104G, 2020PASJ...72...33K |
| dynesty | nested sampling of SZ + source models, Bayesian evidence | 2024A&A...689A..41V, 2019A&A...628A.100D, 2024A&A...682A.186L |
| galario | fast FFT and uv sampling of model images | 2019A&A...628A.100D (also GALARIO fits in 2019MNRAS.490.5134B) |
| emcee | MCMC pressure-profile fit with full covariance | 2020ApJ...891...90R |
| colossus | mass conversions for dynamical M500 | 2024A&A...689A..41V |
| CIAO | Chandra pressure profile for comparison | 2019MNRAS.487.4037D |

Several papers use an in-house uv forward-modelling code not named or versioned in the card
(2019MNRAS.487.4037D; the sampler in 2020A&A...638A..70D is not named).

## Pitfalls

- **Filtering bias.** Missing short spacings make the pressure normalization degenerate with shape and Mach
  number (2016ApJ...829L..23B, 2024A&A...689A..41V), push fits toward compact low-mass models
  (2021A&A...650A.153D), and can underestimate the SZ normalization (2024A&A...682A.186L). ALMA+ACA integrated
  SZ flux came out at 2.17e-4 arcmin^2 against 4.7e-4 from AdvACT (2021A&A...650A.153D). The outermost pressure
  bin can be biased low (2020ApJ...891...90R). A simulation-based correction factor of 2.5 was needed in one
  quasar field (2019MNRAS.490.5134B).
- **Template dependence of mass.** Eight pressure templates gave M500 from 2.01e13 to 6.54e13 Msun for one
  object (2024A&A...682A.186L). Free versus fixed slopes changed component masses from 2.60e14 and 1.34e14 to
  3.10e14 and 3.26e14 Msun (2021A&A...650A.153D). Report the model spread, not one template.
- **Hydrostatic and self-similar assumptions.** M500 inherits them; mergers and non-hydrostatic gas bias masses
  (2021A&A...650A.153D).
- **SZ temperatures can disagree with X-ray.** In the Spiderweb the SZ-based temperature was about 3 times
  lower than the X-ray spectral value, possibly from filtering, metallicity or non-thermal contamination
  (2024A&A...682A.186L).
- **tSZ/kSZ degeneracy** with one band (2024ApJ...969...56M, 2021A&A...650A.153D); stacks are blind to
  non-spherical kSZ (2024ApJ...969...56M).
- **Too few degrees of freedom.** A 17-parameter positive-source model left dof = 1 on short baselines
  (2019MNRAS.490.5134B). A best-fit model with chi-square similar to zero signal is not a detection
  (2024ApJ...969...56M).
- **Comparing non-nested models.** Statistical comparison between models with different components can mislead
  and overfitting can hide an overpressure (2019MNRAS.487.4037D).
- **Geometry.** Shock and post-shock geometry dominate systematics (2019A&A...628A.100D).
- **Undetected sources** leave positive residuals, so significance is conservative (2019A&A...629A.104G); radio
  flux boosting can be up to about 40% for faint sources (2021MNRAS.503.1174K).
- **Settings cards flag as not stated** (pack aggregates): CASA version (2 cards), dynesty live points and
  stopping, exact likelihood and visibility weights, uv selection and binning, map grid and line-of-sight
  limits, primary-beam model, numerical gNFW parameters and the Y-to-M500 implementation. State all of these.

## Verification checks

What papers did:
- Prior-only or data-free runs to show priors do not drive the result (2019A&A...628A.100D,
  2020A&A...638A..70D).
- Re-fit with alternate gNFW and source priors and with observation subsets (2021A&A...650A.153D); vary gNFW
  slopes and centroid (2019A&A...628A.100D).
- Residual maps: subtract the model in the visibility plane and image the residuals (2024A&A...689A..41V,
  2019MNRAS.490.5134B, 2019A&A...628A.100D). Images are for display; fit in the uv plane
  (2021A&A...650A.153D).
- Mock observations with known input: shocks with M = 1, 2, 4 (2016ApJ...829L..23B); FABLE simulation through
  `simobserve` (2019MNRAS.490.5134B); Monte Carlo test of SZ-X-ray peak offsets (2019A&A...629A.104G).
- External agreement: X-ray pressure profiles (2019MNRAS.487.4037D, 2020ApJ...891...90R), X-ray luminosity
  predicted from SZ mass (2021A&A...650A.153D), survey integrated SZ flux (2021A&A...650A.153D), masses from
  X-ray, CARMA and ACT (2024A&A...689A..41V), y-map morphology against X-ray (2020PASJ...72...33K).

What a careful referee adds:
- Inject a model decrement into the real visibilities (or noise realizations from the weights) and recover it
  with the full pipeline, including source fitting.
- Show the azimuthally averaged or binned real visibility amplitude versus uv distance with the model curve.
- Quote masses for every reasonable pressure template plus the averaged value, and state the uv range that
  actually constrains the fit.
- Confirm sources were modelled with a spectral form allowing both signs of spectral index across bands.

## Source cards

Full list with titles: `references/sources.md`. Most informative for this technique:

- 2021A&A...650A.153D (two-component gNFW, evidence, kSZ attempt, AdvACT comparison)
- 2024A&A...689A..41V (dynesty uv forward model, ALMA+ACA+ACT joint, template averaging)
- 2020A&A...638A..70D (ACA cluster confirmation, priors, sigma_eff)
- 2019A&A...628A.100D (Bullet shock, galario + dynamic nested sampling, prior table)
- 2016ApJ...829L..23B (El Gordo shock, Rankine-Hugoniot model, mock tests)
- 2024A&A...682A.186L (eight templates, BMA, SZ + X-ray temperature)
- 2019A&A...629A.104G (uv-profile, simalma, source subtraction)
- 2020PASJ...72...33K (image route, missing-flux factor, y map)
- 2019MNRAS.487.4037D (ALMA + Bolocam + Planck)
- 2020ApJ...891...90R (MUSTANG-2 pressure bins, full covariance)
- 2019MNRAS.490.5134B (quasar halo, residual visibilities, simulation correction)
- 2024ApJ...969...56M (stacked quasar fields, Compton y limit)
- 2020EPJWC.22800009E (SZ + X-ray + lensing shapes; preliminary ALMA data)
- 2021MNRAS.503.1174K (radio jets against an SZ residual map)

An earlier pack also tagged seven off-topic papers (Lupus "Sz" star names and Shakura-Sunyaev accretion disks).
The matcher now excludes them, so this skill rests on the 14 papers in references/sources.md.
