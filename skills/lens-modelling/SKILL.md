---
name: alma-lens-modelling
description: "Model strongly lensed ALMA sources: fit a lens mass model (SIE plus shear and its variants, cluster models) to visibilities, images or image positions, reconstruct the source plane (parametric or pixelated), derive magnifications per component, tracer and velocity channel, and propagate them into intrinsic sizes, luminosities, masses and kinematics. Use when an ALMA source is (or might be) gravitationally lensed, when you need a magnification or a source-plane map or cube, when deciding whether a multiple-component source is lensed at all, or when reviewing someone's lens model. Built from 61 ALMA papers (2013-2026)."
---

# Strong-lens modelling of ALMA sources

Fits a model of the foreground mass and of the background source so that the lensed model reproduces the
ALMA data, then reads the magnification and the intrinsic (source-plane) structure off that model. Almost all
ALMA work here is on lensed dusty star-forming galaxies (60 of 61 pack papers are tagged high-z galaxies) plus
a few lensed quasars and lens-galaxy mass-profile studies. The mistakes that matter most: (1) quoting a
magnification error that is only the statistical width of one parametric model, when the authors themselves
say systematics from the source parameterisation or the mass model dominate (2016ApJ...826..112S,
2020ApJ...905..152D, 2025ApJ...995..219F); (2) dividing every tracer by one magnification when differential
lensing between dust, CO lines and velocity channels reaches tens of per cent (2019ApJ...873...50D,
2026A&A...705A..81K, 2021A&A...645A..45C).

Counts below are from the evidence pack (`skills/packs/lens-modelling.md`). The regex tagger pulled in a few
papers where lensing is incidental (redshift-distribution, cluster-environment, survey and stacking papers:
2013ApJ...767...88W, 2016ApJ...822...80S, 2018ApJ...862...64S, 2018ApJ...864...60M, 2020A&A...633A.160C,
2025ApJS..278...45F); my own counts of pack lines exclude them, leaving 55 on-topic papers. Many fit their own
lens model; others apply a published model (2020ApJ...905..152D uses an earlier parametric model) or a single
or median magnification (2020ApJ...902...78R). I did not census own-model vs inherited-model papers.
Every "my count" below is a census of pack lines (aggregates, settings, assumptions, excerpts) with the
bibcodes listed so it can be re-checked; "(card)" marks a detail verified in that paper's card, not the pack.

## When to use

- A submm/mm-bright source shows arcs, an Einstein ring, or multiple compact components around a foreground
  galaxy or cluster (SPT, Herschel, Planck-selected DSFGs: 2013ApJ...767..132H, 2016ApJ...826..112S,
  2021A&A...645A..45C).
- You need intrinsic L_IR, SFR, dust/gas mass, size or surface density of a lensed source (fluxes divide by
  mu; see step 9 for sizes and surface densities, which do not take a blanket 1/mu).
- You need source-plane maps or cubes for morphology, clumps or kinematics (2019A&A...624A.138Y,
  2018ApJ...866L..12G, 2025NatAs...9.1553F, 2024A&A...685A..80Z).
- You want the lens galaxy itself: inner mass profile, central image, SMBH limit, subhalo or line-of-sight
  perturbers (2015ApJ...811..115W, 2015PASJ...67...72T, 2016MNRAS.457.2936I, 2020A&A...641L...2M,
  2017ApJ...843L..35W).
- You need to test whether a multi-component source is lensed at all (2020ApJ...891...64F,
  2026ApJ..1002L..28Y).

## When not to use

- Unlensed compact source, or you only need a flux/size from a generic Gaussian or disk fit to visibilities:
  use the `uv-plane-fitting` skill. That skill also covers visibility weights, likelihoods and samplers in
  general; this one adds the lens.
- Weakly magnified field sources behind cluster lenses where you only need a magnification at a position:
  take it from the published cluster model (median and 16-84th percentiles over models, 2017A&A...597A..41G)
  rather than building a new model.
- Statistical lensing arguments (image-separation distributions, magnification bias) are a different
  calculation (2018MNRAS.475.4939A uses halo mass functions and cross sections, not individual models).
- SED fitting, dust masses, gas conversion factors and kinematic fitting of the reconstructed source are
  downstream; use the matching skills once you have mu and source-plane products.

## Steps

1. **Establish that it is lensed and gather lens priors.**
   - Goal: lens/source redshifts, lens-light position and shape, image configuration.
   - Method: optical/NIR imaging (HST, JWST, IRAC) to locate deflectors and guide the model
     (2016ApJ...826..112S); lens redshift from spectroscopy, otherwise assumed (2019ApJ...870...80L fixes
     z=0.9).
   - Redshifts: record every lens and source redshift assumption and test its effect on mu and the geometry.
     Documented cases: source z unknown, assumed z=2 with z=1-3 propagated as the error (2017A&A...597A..41G);
     lens redshifts uncertain, all deflectors and the halo put at the same z~1 (2025ApJ...991...53C); two
     deflectors at distinct redshifts z=0.626 and 1.002 (2019A&A...624A.138Y); a second absorber at z=0.19
     neglected (2020A&A...641L...2M); a z=0.357 perturber given its own NFW (2025ApJ...995..219F). State
     whether extra deflectors are put on one plane or treated as separate planes.
   - For ambiguous cases fit a lens model and test it: 2020ApJ...891...64F fits SIE+shear to four
     ALMA peaks with glafic and checks positions and fluxes; 2026ApJ..1002L..28Y rejects lensing because
     continuum and [C II] fits need different deflector positions and Einstein radii.
   - Lens light: subtract with GALFIT or fit it inside the lens code. 2024ApJ...967...11C lists doing it
     separately as a limitation.
2. **Prepare the data.**
   - Visibility fits: calibrated, continuum-subtracted (uvcontsub) visibilities for lines
     (2026A&A...705A..81K). Time-average to cut volume but only while the binned visibility stays compact in
     uv: up to 3 min within 10 m (2018Sci...361.1016S), up to 10 min within 15 m (2019ApJ...873...50D),
     or any length unless it spans >10 m (2020ApJ...905...85S).
   - Noise per visibility: from differencing adjacent visibilities (2013ApJ...767..132H), from the rms within
     an observing block per baseline (2015MNRAS.451L..40R), or via CASA statwt (2026A&A...705A..81K).
   - Image-plane fits use CLEAN images or moment-0 maps (2019A&A...624A.138Y, 2014A&A...568A..92M,
     2018ApJ...866L..12G); position fits use peak or knot positions with assigned errors.
3. **Choose the constraint type.**
   - Extended arcs or rings in interferometer data: fit visibilities. My count, 12 papers: 11 with pack
     evidence of a visibility-plane lens fit (2013ApJ...767..132H, 2015MNRAS.451L..40R, 2015ApJ...811..124S,
     2018A&A...613A..34P, 2018Natur.553...51M, 2018Sci...361.1016S, 2019ApJ...870...80L,
     2019ApJ...873...50D, 2020ApJ...905...85S, 2024A&A...684A..56K, 2026A&A...705A..81K) plus
     2016ApJ...826..112S (visilens in the aggregate; method from its card). That paper (card, section 3)
     prefers the uv plane because "the noise and measurement are well understood" there.
   - Compact knots, quasar images, clusters: fit image positions (and sometimes flux ratios or time delays)
     with a positional error per image (2015PASJ...67...72T, 2016MNRAS.457.2936I, 2020A&A...641L...2M,
     2025ApJ...995..219F, 2016MNRAS.461..164I).
   - Combined: 2025ApJ...991...53C fits point images first, then a pixelated reconstruction with pixsrc;
     2017ApJ...843L..35W takes structural priors from an HST arc fit before fitting ALMA conjugate points.
4. **Fit a parametric lens plus source model.**
   - Mass: SIE (often with external shear) is the profile most often named. My count, 18 papers whose pack
     lines name an SIE: 2013ApJ...767..132H, 2015ApJ...811..124S, 2016MNRAS.457.2936I, 2016MNRAS.461..164I,
     2018A&A...610A..53M, 2018Natur.553...51M, 2018Sci...361.1016S, 2019A&A...624A.138Y,
     2019ApJ...870...80L, 2019ApJ...873...50D, 2020ApJ...891...64F, 2020ApJ...892L..18I,
     2020ApJ...905...85S, 2023Natur.621..483G (simulation only), 2024ApJ...967...11C, 2025ApJ...991...53C,
     2026A&A...705A..81K, 2026ApJ..1002L..28Y. This is a frequency, not evidence that SIE is adequate. Variants:
     elliptical power law (2014A&A...568A..92M, 2015MNRAS.451L..40R, 2018A&A...613A..34P,
     2018ApJ...866L..12G), cored power law plus SMBH point mass (2015ApJ...811..115W, 2017ApJ...843L..35W),
     cored isothermal plus multipoles (2015PASJ...67...72T), softened isothermal (2020A&A...641L...2M),
     extra halo or companions (2025ApJ...991...53C, 2018ApJ...866L..12G), cluster PIEMD/NFW/pseudo-Jaffe
     models (2024A&A...692A.215C, 2025ApJ...995..219F, 2017A&A...600L...3C).
   - Source: Sérsic (2016ApJ...826..112S, 2019ApJ...873...50D, 2026A&A...705A..81K, 2024A&A...684A..56K),
     Gaussian (2013ApJ...767..132H, 2015ApJ...811..124S) or exponential (2019A&A...624A.138Y). Sérsic by my
     count in 7 papers: 2018Natur.553...51M, 2019ApJ...873...50D, 2024A&A...684A..56K, 2024ApJ...967...11C,
     2026A&A...705A..81K, 2026ApJ..1002L..28Y (pack) and 2016ApJ...826..112S (card, section 3). Add
     components as needed (four Sérsics for SPT0311-58, 2018Natur.553...51M) and select with DIC
     (2019ApJ...873...50D, 2020ApJ...905...85S).
   - Fitting: documented choices include MCMC (the phrasing most often seen in the pack's fitting-methods
     aggregate), emcee (named in 7 pack papers, not all for the lens fit), Metropolis-Hastings
     (2013ApJ...767..132H, 2019A&A...624A.138Y), PSO start then emcee (2024ApJ...967...11C), MultiNest
     (aggregate, 1 paper), chi^2 minimisation (2016MNRAS.457.2936I, 2020A&A...641L...2M), maximum a
     posteriori (2015MNRAS.451L..40R) and importance sampling (aggregate, 1 paper). Many cards do not state
     the sampler at all (2026A&A...705A..81K, 2015ApJ...811..115W).
   - Calibration nuisance terms in visibility fits: solve antenna phases at each chain step
     (2013ApJ...767..132H; amplitude rescaling between observations, 2016ApJ...826..112S, card section 2),
     or marginalise over residual calibration errors (2018Natur.553...51M).
5. **Optional pixelated source reconstruction.**
   - Method: source on a pixel, Delaunay or Voronoi grid with regularisation, lens parameters from the
     parametric fit or iterated (2015MNRAS.451L..40R, 2019ApJ...870...80L, 2020ApJ...905...85S,
     2026A&A...705A..81K, 2018ApJ...866L..12G).
   - Regularisation: documented forms are gradient (2015MNRAS.451L..40R, 2018Natur.553...51M,
     2020ApJ...905...85S; chosen "to prevent the source from being overly smoothed", 2015MNRAS.451L..40R)
     and constant, with one coefficient, in PyAutoLens (2026A&A...705A..81K). Many cards do not state the
     form or strength (2018A&A...613A..34P, 2014A&A...568A..92M). Strength set by maximising Bayesian
     evidence at fixed lens parameters, alternating with the lens MCMC until both converge
     (2020ApJ...905...85S, 2019ApJ...870...80L; also 2018Sci...361.1016S, card "Lens Modeling Methodology").
   - Randomised Voronoi grids: 2020ApJ...905..152D reconstructs each slice with 50 realisations and takes the
     mean "weighted by the log of the likelihood of each realisation". That is the paper's wording; the
     exact weighting is not spelled out, so ask or check the cited method before copying it.
6. **Line cubes and differential lensing.**
   - Three documented workflows; say which one you use:
     (a) Lens fixed from one dataset, then each channel or bin reconstructed: from the dust continuum
     (2019A&A...624A.138Y, 2020ApJ...905...85S, 2019ApJ...870...80L), from the 160 um deflections
     (2018Natur.553...51M), from the ALMA best fit applied to ATCA CO (2015ApJ...811..124S), or from all CO
     channels combined (2018A&A...613A..34P).
     (b) Joint fit: continuum and line channels fitted simultaneously with one shared set of lens parameters
     (2019ApJ...873...50D, which also runs single-channel models).
     (c) Independent diagnostic fits: 2026A&A...705A..81K models the line channels only (no continuum lens),
     then splits each line into red and blue bins and fits a parametric lens model to each bin to test
     differential lensing. Different lens parameters per bin are a diagnostic, not a physical lens.
   - Bin widths reported: 40 km/s (2018Natur.553...51M), 50 km/s (2019ApJ...870...80L), 75-250 km/s
     (2019ApJ...873...50D), 105 km/s (2019A&A...624A.138Y), red/blue halves at low S/N
     (2026A&A...705A..81K). Test alternative channelisations (100-400 km/s, 2015ApJ...811..124S). Record
     the exact channel ranges and velocity zero point; cards flag both as missing (2026A&A...705A..81K).
   - For weak lines, transfer the per-channel magnification of a bright line by nearest velocity, which
     assumes the weak line follows the bright line's kinematics (2024A&A...684A..56K).
7. **Magnification and its uncertainty.**
   - Definition (general practice): total flux magnification mu = F_image / F_source, the lensed
     (image-plane) flux over the intrinsic (source-plane) flux, so mu > 1 for a magnified source; the
     pack's explicit form is mu = F_LP/F_SP over S/N >= 3 pixels (2018A&A...610A..53M). Do not copy the
     ordering in the 2015MNRAS.451L..40R wording ("ratio of the reconstructed emission in the source-plane
     and image-plane"); its reported mu = 17.6 is a magnification > 1. Signed per-image magnifications
     (negative for parity-flipped images, e.g. mu_B = -2.9 in 2020A&A...641L...2M) are a different quantity;
     use |mu| when converting fluxes.
   - Averaging choices: flux-weighted over the source (2018Natur.553...51M), luminosity-weighted from
     amplification maps and the line image (2021A&A...645A..45C), restricted to pixels with S/N >= 3
     (2018A&A...610A..53M), or mean in an aperture (2024A&A...692A.215C). State which.
   - Uncertainty: recompute mu over posterior draws, 100 (2024ApJ...967...11C, 2024A&A...692A.215C, which
     quotes the median and (p84-p16)/2) or 1000 (2025ApJ...995..219F). Report mu per component and per
     tracer.
8. **Source-plane resolution and products.**
   - Lens a mock point source through the best model and reconstruct it to get the effective resolution
     (0.13x0.15 arcsec, 0.12x0.12 near the caustic, 2019ApJ...870...80L; also mock-data resolution tests in
     2018Sci...361.1016S, card "Lens Model Tests"); or reconstruct the beam on a grid of image-plane
     positions to get the source-plane PSF (2015ApJ...806L..17S, card "Analysis & Discussion").
   - Make source-plane S/N maps (2026A&A...705A..81K), then morphology (IMFIT, 2019A&A...624A.138Y) and
     kinematics on source-plane cubes (3DBarolo: 2019A&A...624A.138Y, 2025NatAs...9.1553F; galpak3d with
     PSF homogenisation: 2018ApJ...866L..12G).
9. **Intrinsic properties.**
   - Extensive quantities (flux, luminosity, SFR, dust and gas mass) divide by the mu of the matching
     tracer (2013ApJ...767..132H), and only apply the dust-derived mu to the far-IR part of the SED
     (2015MNRAS.451L..40R).
   - Sizes: 2017A&A...597A..41G corrects the effective radius from a uv-plane Gaussian fit of sources behind
     Frontier Fields clusters as r_s/sqrt(mu), with mu from published cluster models. Treat that as an
     approximation for an effective radius only; it assumes isotropic stretching. In strong lensing the tangential and radial stretch differ, especially
     near caustics, so axes, separations and resolved structure must come from the source-plane
     reconstruction, not from a sqrt(mu) scaling.
   - Surface densities (SFR, gas, dust per area) do not take a blanket 1/mu: under lensing both flux and
     area are magnified, so form them from the intrinsic quantity and the intrinsic (source-plane) area,
     measured consistently in the reconstruction (general practice).
   - If no model exists, a sample median mu (5.5, 2020ApJ...902...78R) makes the result an estimate, as those
     authors say.

## Parameter defaults and ranges

Every row below is a setting one or a few papers reported for their own data. None is a validated
transferable default: justify each choice for your data and show convergence or a sensitivity test.

| Parameter | Reported example (not a validated default) | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| Lens mass profile | SIE + external shear | power law, cored PL + SMBH, softened/cored isothermal, multipoles, NFW, PIEMD | SIE in 18 (my census, step 4) | 2013ApJ...767..132H, 2015PASJ...67...72T, 2018A&A...613A..34P |
| Lens-model free parameters (as stated; components differ, so not comparable) | SIE 5 lens + Gaussian source 4 (2013ApJ...767..132H) | softened isothermal, 8 incl. 2 source-position (2020A&A...641L...2M); power-law primary + isothermal satellite + shear, 8 (2018A&A...613A..34P); cored isothermal + shear + multipoles, 12 (2015PASJ...67...72T) | 4 | 2013ApJ...767..132H, 2020A&A...641L...2M, 2018A&A...613A..34P, 2015PASJ...67...72T |
| External shear prior | Gaussian, width 0.05 | mean 0.05 or 0.00 | 2 | 2020ApJ...891...64F, 2025ApJ...991...53C |
| Einstein radius prior | uniform U[0.1, 1.1 arcsec] | lognormal 0.1 dex; upper limit set from a previous model | 3 | 2019A&A...624A.138Y, 2025ApJ...991...53C, 2026A&A...705A..81K |
| Lens centre | within 0.2 arcsec of HST centroid (2018ApJ...867..140L); no prior on SIE centroid (2020ApJ...891...64F) | 2026A&A...705A..81K says centres were "fixed" at the Einstein-ring centres "using uniform priors" with no bounds given; the pack cannot tell whether they were fixed or sampled. State either exact fixed coordinates or sampled bounds. | 3 | 2026A&A...705A..81K, 2018ApJ...867..140L, 2020ApJ...891...64F |
| Lens axis ratio prior | Normal(0.5, 0.2) | shape priors 0.05-0.20 | 2 | 2019A&A...624A.138Y, 2025ApJ...991...53C |
| Source profile | Sérsic | Gaussian, exponential, point | Sérsic in 7 (my census, step 4) | 2016ApJ...826..112S, 2019ApJ...873...50D, 2013ApJ...767..132H |
| Source size prior | Normal(0.1, 0.03 arcsec) in [0, 0.2] | | 1 | 2019A&A...624A.138Y |
| Image-position error, compact clumps/knots | 20-30 mas | 20 mas, but 100-200 mas for 10 blended knots (2015PASJ...67...72T); 0.03 arcsec (2020ApJ...891...64F, 2025ApJ...991...53C); beam/4 = 6x8 mas for clump peaks (2016MNRAS.457.2936I); 0.02 arcsec radial / 0.05 arcsec tangential for conjugate points (2017ApJ...843L..35W, card section 3) | 5 | 2020ApJ...891...64F, 2025ApJ...991...53C, 2015PASJ...67...72T, 2016MNRAS.457.2936I, 2017ApJ...843L..35W |
| Image-position error, other data | | HST images 130-200 mas (2015PASJ...67...72T); lens-galaxy centroid 0.02 arcsec (2016MNRAS.457.2936I) | 2 | 2015PASJ...67...72T, 2016MNRAS.457.2936I |
| Image flux error (position fits) | 10% | | 1 | 2020ApJ...891...64F |
| Visibility time averaging | until binned uv spread ~10 m | 3-10 min, 10-15 m | 3 | 2018Sci...361.1016S, 2019ApJ...873...50D, 2020ApJ...905...85S |
| Line velocity binning | 40-105 km/s | 40-400 km/s; 2 bins at low S/N | 6 | 2018Natur.553...51M, 2019ApJ...873...50D, 2026A&A...705A..81K |
| Regularisation | gradient, evidence-optimised | constant | 5 | 2015MNRAS.451L..40R, 2020ApJ...905...85S, 2026A&A...705A..81K |
| emcee run (visilens) | 1000 chains, 1000 burn-in + 1000 steps | | 1 | 2019ApJ...873...50D |
| Glee MCMC chain (sampler not named; card flags sampler details missing) | chain length 5x10^5 | | 1 | 2015ApJ...811..115W |
| Posterior draws for mu | 100 | 100-1000 | 3 | 2024ApJ...967...11C, 2024A&A...692A.215C, 2025ApJ...995..219F |
| pixsrc noise level | raised to 80 uJy/beam for that dataset's fit/regularisation balance | | 1 | 2025ApJ...991...53C |
| Cosmology | flat LCDM, H0 ~70, Om ~0.3 | H0 67.4-73.3, Om 0.26-0.308 | 10 (my count) | 2014A&A...568A..92M, 2019ApJ...873...50D, 2020A&A...641L...2M |

Cosmology count (my census of the pack's assumptions lines): 2013ApJ...767..132H, 2014A&A...568A..92M,
2015PASJ...67...72T, 2015ApJ...812...88M, 2016ApJ...826..112S, 2018A&A...620A.115B, 2018MNRAS.475.4939A,
2019ApJ...873...50D, 2020A&A...641L...2M, 2020ApJ...902...78R.

Selected ALMA central magnification estimates in the pack run from about 1.3 (2018Natur.553...51M,
component E) to ~58 (2020ApJ...891...64F, whose stated 2 sigma range is 18-117 and whose model is poorly
constrained); typical galaxy-scale DSFG values are 5-30 (2013ApJ...767..132H, 2019ApJ...873...50D,
2024ApJ...967...11C). Optical values can be much larger: the same 2020ApJ...891...64F model predicts ~450
for the HST quadruple images, uncertain by a factor of a few. Demagnified central images go well below 1
(mu_C = 0.022, 2020A&A...641L...2M).

## Software

Counts are the pack's software aggregate over all 61 papers (lens codes only; SED and imaging tools omitted).

| Code | Pack count | Used for | Examples |
|---|---|---|---|
| visilens (+ emcee) | 7 | parametric SIE + Sérsic fits to visibilities | 2016ApJ...826..112S, 2019ApJ...873...50D, 2024A&A...684A..56K |
| emcee | 7 | sampler for visilens, lenstronomy, glafic; also SED and uv fits | 2024ApJ...967...11C, 2025ApJ...995..219F |
| Lenstool | 6 | cluster and group models, amplification maps | 2024A&A...692A.215C, 2021A&A...645A..45C, 2017A&A...600L...3C |
| PyAutoLens / AutoLens | 4 + 1 | capabilities shown per paper: uv-plane parametric SIE + Sérsic fit, then adaptive Voronoi source with constant regularisation (2026A&A...705A..81K); SIE + shear with Sérsic sources on continuum and [C II] to test lensing (2026ApJ..1002L..28Y); a pixelised reconstruction used only to cross-check an image-plane sl_fit model, setup not given (2019A&A...624A.138Y) | 2026A&A...705A..81K, 2026ApJ..1002L..28Y, 2019A&A...624A.138Y |
| glafic | 4 | position-based galaxy and cluster models | 2015PASJ...67...72T, 2020ApJ...891...64F, 2025ApJ...995..219F |
| RIPPLES | 3 | pixelated visibility reconstruction | 2019ApJ...870...80L, 2020ApJ...905...85S |
| gravlens / lensmodel | 3 + 1 | position, flux-ratio and time-delay fits | 2016MNRAS.461..164I, 2020A&A...641L...2M, 2025ApJ...991...53C |
| Glee | 3 | power-law + SMBH models, conjugate points | 2015ApJ...811..115W, 2017ApJ...843L..35W |
| sl_fit | 2 | image-plane parametric lens + source | 2019A&A...624A.138Y |
| lenstronomy | 2 | multi-band JWST models, simulated lensed polarisation | 2024ApJ...967...11C, 2023Natur.621..483G |
| Pixelated code of Hezaveh et al. 2016 (not public) | 3 | pixelated visibility reconstruction (gradient regularisation stated in 2018Natur.553...51M) | 2018Natur.553...51M, 2018Sci...361.1016S |
| SLI code | 1 (others unnamed) | semi-linear inversion, Voronoi grids | 2014A&A...568A..92M, 2018ApJ...866L..12G, 2020ApJ...905..152D |
| pixsrc | 1 | pixelated reconstruction after point-image model | 2025ApJ...991...53C |
| GALFIT | 3 | lens/foreground light subtraction | 2014A&A...568A..92M, 2025ApJ...995..219F |
| 3DBarolo / galpak3d | 2 / 1 | kinematics of source-plane cubes | 2025NatAs...9.1553F, 2018ApJ...866L..12G |
| CASA statwt / simobserve | 1 / 1 | visibility weights; mock observations through a lens | 2026A&A...705A..81K, 2023Natur.621..483G |

Several codes are in-house or unreleased (2013ApJ...767..132H, 2016MNRAS.457.2936I, 2018Sci...361.1016S),
so exact reproduction is often impossible; prefer a public code and say which.

## Pitfalls

- **Statistical-only magnification errors.** mu = 10.7 ± 0.002 (2026A&A...705A..81K) is a formal sampler
  error. Authors admit errors exclude lens-model systematics (2020ApJ...905..152D, 2025ApJ...995..219F) and
  that source-parameterisation systematics dominate (2016ApJ...826..112S). Systematic estimates in the pack:
  up to ~25% (2025NatAs...9.1553F), a factor of a few for a poorly constrained model (2020ApJ...891...64F).
- **Mass-sheet degeneracy** not explored or possibly unbroken (2019A&A...624A.138Y, 2025ApJ...995..219F).
- **Bimodal posteriors**: SPT0529-54 with compact-configuration data only (2013ApJ...767..132H, which
  expects extended-array data to break it) and a bimodal lens solution in 2018Sci...361.1016S. Run several
  chains and look.
- **Model too simple.** No external shear (2018ApJ...867..140L), SIE without multipoles or non-isothermal
  slopes (2016MNRAS.461..164I, 2016MNRAS.457.2936I); core radius, velocity dispersion and BH mass are
  degenerate (2015PASJ...67...72T).
- **Parametric sources hide structure.** Sérsic models cannot independently constrain faint extended emission
  (2019ApJ...873...50D); a Gaussian source was rejected as a poor fit (2024A&A...684A..56K).
- **Differential magnification.** CO(2-1) ~60% more magnified than CO(6-5) (2019ApJ...873...50D); blue vs red
  halves mu ~14 vs ~9 and ~14 vs ~4.4 (2026A&A...705A..81K); HNC 16.3 vs CO 22.0 (2021A&A...645A..45C);
  continuum 37 vs CO(11-10) 28 (2020ApJ...892L..18I). Papers that neglect it say so (2018A&A...620A.115B,
  2017MNRAS.466.2825B, 2016A&A...586L...7B), and image fluxes were dropped as constraints because of it
  (2015ApJ...811..115W).
- **Single mu across the SED.** Assumed constant across the far-IR (2019A&A...624A.138Y); applying the ALMA mu
  to stellar emission is an untested assumption (2015ApJ...812...88M), and SED fits are limited by the
  precision of differential magnification (2018A&A...613A..34P).
- **Low per-channel S/N** prevents full delensed cubes and clump-scale resolution (2026A&A...705A..81K).
- **Lens light** subtracted outside the lens fit (2024ApJ...967...11C); IRAC blending with the lens makes
  stellar masses unreliable (2018Natur.553...51M).
- **Interferometric flux loss.** ALMA may resolve out extended flux (2018ApJ...867..140L); check against
  single-dish totals.
- **Spectral truncation.** Check that the line sits wholly inside the band before reading recovered flux,
  line asymmetry or maximum velocity from the reconstruction: ~10% of the line flux fell outside the
  coverage in 2020ApJ...905..152D, and limited bandwidth hid redshifted P Cygni emission and capped vmax in
  2020ApJ...905...85S. Missing channels are not a lensing effect; separate the two before invoking
  differential magnification.
- **Size bias.** Strongly lensed samples favour compact sources (2015MNRAS.451L..40R); conjugate-point fits
  carry their own degeneracies (2017ApJ...843L..35W).
- **Unreported settings.** For the lens model, cards flag missing priors, MCMC settings, regularisation
  values, source grid sizes and lens code release (2013ApJ...767..132H, 2018Natur.553...51M,
  2026A&A...705A..81K, 2020ApJ...905...85S). The pack's "not stated" aggregate is led by data-provenance
  items, which feed the lens fit too. Report, alongside the lens configuration:
  - CASA and pipeline version (flagged in 6 papers; aggregate) and calibration scripts;
  - flux calibrator and flux-scale uncertainty (6 papers across two phrasings; aggregate);
  - line-free channels and the continuum-subtraction method (uvcontsub) per source (about 9 papers across
    several phrasings; aggregate);
  - imaging settings: cell and image size, weighting, clean threshold and masks (aggregate);
  - exact channel ranges of each velocity bin and the systemic-velocity zero point (2026A&A...705A..81K,
    and the aggregate's "systemic redshift velocity zero points" item);
  - self-calibration intervals and rounds (2019A&A...624A.138Y, 2020ApJ...905...85S).

## Verification checks

What papers did:
- Residual images or visibilities consistent with noise: no residuals >3 sigma (2026A&A...705A..81K), <2.5
  sigma (2019A&A...624A.138Y), fraction of >2 sigma residuals 0.2-0.5% (2014A&A...568A..92M), 4.7% and 0.3%
  of visibilities beyond 2 and 3 sigma (2015MNRAS.451L..40R).
- Image-position rms: ~0.015 arcsec (2015ApJ...811..115W), <0.02 arcsec (2025ApJ...991...53C), 0.14 arcsec for
  a cluster model (2025ApJ...995..219F); reduced chi2 < 1 (2017ApJ...843L..35W).
- Second code or method: PyAutoLens pixelated run converges to the sl_fit model (2019A&A...624A.138Y);
  pixelated vs visilens sources agree to <15% (2018Natur.553...51M); glafic vs Glee with "similar results" (2017ApJ...843L..35W, card section 3);
  in-house vs GRAVLENS chi2 within a few per cent (2016MNRAS.457.2936I).
- Lens parameters consistent across wavelengths (<10%, 2018Natur.553...51M) and with HST/Keck models
  (within 2 sigma, 2018A&A...613A..34P; 2015PASJ...67...72T).
- Flux recovery: mu x L'_intrinsic vs apparent L' (2019ApJ...873...50D); modelled ALMA flux vs LABOCA
  870 um within ~10% (2013ApJ...767..132H).
- Mock tests: point sources across the source plane recovered to ~25% plus a negative-bowl check at >=10% of
  peak (2020ApJ...905...85S); simulated data recover input antenna phases (2013ApJ...767..132H). For
  polarisation, 2023Natur.621..483G simulated a source with constant B-field orientation and constant
  polarisation fraction, lensed it with SIE + shear and found the lens and convolution do not rotate it or
  change P. That holds for that uniform test source only; a spatially varying field can be mixed by
  differential magnification, so simulate your own source structure before claiming invariance.
- Source vs image plane moment maps agree (2019A&A...624A.138Y); model selection by DIC
  (2019ApJ...873...50D) or Bayesian evidence (2018ApJ...866L..12G).

What a careful referee adds:
- Refit with a second mass profile (power-law slope free, shear on/off) and a second source model; quote the
  spread in mu as a systematic next to the posterior width.
- Report mu per tracer and per velocity bin before forming any line ratio or SLED.
- Run independent chains or a sampler with multimodal support and show the posterior is not bimodal.
- Confirm the lens centre against the optical deflector and the lens redshift against spectroscopy.
- Publish priors, chain settings, regularisation strength, grid size and the code version.

## Source cards

Full list: `references/sources.md`. Most informative for method detail:

- 2013ApJ...767..132H: visibility MCMC with antenna-phase self-calibration in the fit
- 2016ApJ...826..112S: 47 SPT sources with visilens (count from card); systematics discussion
- 2019ApJ...873...50D: per-channel CO lens models, DIC, differential magnification
- 2019A&A...624A.138Y: priors stated in full, two deflectors, cross-check with PyAutoLens
- 2015MNRAS.451L..40R: pixelated visibility reconstruction, gradient regularisation, per-baseline noise
- 2020ApJ...905...85S: RIPPLES, evidence-tuned regularisation, mock tests
- 2019ApJ...870...80L: per-channel [C II] reconstruction and source-plane resolution test
- 2018Natur.553...51M: visilens then pixelated, cross-wavelength and cross-code checks
- 2018Sci...361.1016S: pixelated reconstruction of absorption, bimodal lens solution
- 2026A&A...705A..81K: PyAutoLens uv fit, Voronoi sources, red/blue differential lensing
- 2018A&A...613A..34P: power-law lens on CO visibilities, compared with HST/Keck models
- 2018ApJ...866L..12G: semi-linear inversion, source-plane kinematics with galpak3d
- 2015PASJ...67...72T: 46-knot position fit with multipoles in GLAFIC
- 2015ApJ...811..115W: Glee cored power law, central image and SMBH limit
- 2016MNRAS.457.2936I: flux-ratio anomalies, aperture flux ratios in the source plane
- 2017ApJ...843L..35W: conjugate-point fit with HST priors, Glee vs glafic
- 2025ApJ...991...53C: point-image then pixsrc, halo models, explicit priors
- 2025ApJ...995..219F: GLAFIC cluster model, posterior resampling for mu
- 2024A&A...692A.215C: Lenstool MCMC magnification for cluster arcs
- 2024ApJ...967...11C: lenstronomy PSO + emcee, lens light issue
- 2024A&A...684A..56K: per-channel visilens mu transferred to weak lines
- 2020ApJ...891...64F: testing the lensing hypothesis for a quasar
- 2026ApJ..1002L..28Y: rejecting lensing via inconsistent lens models
- 2021A&A...645A..45C: luminosity-weighted differential magnification
