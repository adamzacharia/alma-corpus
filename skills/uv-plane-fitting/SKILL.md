---
name: alma-uv-plane-fitting
description: "Fit parametric or non-parametric source models directly to ALMA visibilities (point sources, Gaussians, uniform or exponential disks, rings, radiative-transfer or lensed model images, line-emission models) to get fluxes, sizes, positions, geometry and radial profiles with honest uncertainties. Use when a source is compact or near the resolution limit, when image-plane deconvolution would bias sizes or profiles, when fitting disk or debris-belt structure, extracting spectra of unresolved components, measuring stellar or planetary fluxes, or checking someone else's visibility fit. Built from 638 ALMA papers (2012-2026)."
---

# Fitting models directly to visibilities

Compares a model with the measured complex visibilities at the observed (u,v) points instead of with a
deconvolved image, so the fit itself involves no CLEAN deconvolution, beam deconvolution or non-linear masking
(it still inherits the self-calibration model and any sources subtracted beforehand, 2020ApJ...902..141S, and
any image-derived template carries the reconstruction and noise biases of that image, 2026A&A...707A.255C). It
gives fluxes, sizes, positions, inclination/PA and radial profiles, often below the beam size. The mistakes
that matter most: (1) not checking the visibility weights and treating formal errors as total errors (papers
multiplied pipeline weights by factors of 0.1 to 0.6: matched to image RMS in 2020ApJ...902..141S, from the
data scatter in 2024PASJ...76..437Y, stated without a derivation in 2026ApJ..1005...94N; formal errors miss
calibration, astrometric and model-choice systematics, 2024A&A...687A.308S), and (2) reading structure
the uv coverage cannot constrain: total flux extrapolated to zero spacing, sizes near the largest recoverable
scale, and degenerate profile shapes (2020ApJ...898..146M, 2014ApJ...791L...6W, 2015ApJ...798..124R).

> Always report: model family and its assumptions (axisymmetric? optically thin?), which data entered the fit
> (uv range, channels, averaging), how weights were set, the fitter/sampler with priors and chain settings,
> and the validation (residual image at identical uv coverage, deprojected visibility profile).

## When to use

- Compact or barely resolved continuum sources needing size and flux: submm galaxy FIR sizes (uvmultifit
  exponential disk, 2017ApJ...850...83F, 2020ApJ...901...74T), [C II] sizes and a stacked-visibility halo search
  (2025A&A...693A.237I), protostellar disks (2024ApJ...963..164R), cores (2014ApJ...797...27F).
- Stars, planets, moons and comets with physically simple models: point fluxes (2020ApJ...894...76W,
  2018ApJ...855L...2M), uniform or limb-darkened disks (2023PSJ.....4..142C, 2015ApJ...808...36M,
  2018AJ....156..164B, 2024Natur.633..323V), Haser comae (2014ApJ...792L...2C, 2025ApJ...986L..22R).
- Disk and debris-belt structure: ring/gap profiles (2018ApJ...865...37M, 2018ApJ...869...17L,
  2020ApJ...891...48H), belt radius/width/height (2025A&A...693A.151M, 2017MNRAS.465.2595M, 2019ApJ...875...87D,
  2026A&A...705A.197Z), RT model images (2020ApJ...902..141S, 2019ApJ...871..100H), multi-epoch fits with one
  intensity model and a centre per epoch (2024A&A...692A.155K).
- Line emission: Keplerian disk models (2017ApJ...846L..26W, 2018ApJ...856..117F, 2025ApJ...986L..11S; pdspy +
  RADMC-3D + galario + dynesty with velocity and uv cuts per protostar, 2024A&A...687A.308S), abundance models and
  matched-filter detection (2017A&A...605A..21C; this assumes co-spatial lines and template mismatch makes fluxes
  lower limits, so use it for detection significance only). Fitted temperature and turbulence depend on the
  assumed structure: mock tests in 2018ApJ...856..117F recovered temperature only to 20-50% (card) far from the
  tau=1 surface, so test how turbulence shifts with the temperature and abundance assumptions before quoting it.
- Per-channel spectra of components blended in the image: lensed quasar images (2014A&A...566A.112M,
  2020A&A...637A...7M), galaxies as PSF responses (2019MNRAS.485.2092C, 2025A&A...700A.165B), clumps as PSFs
  with a free centre per channel (2024A&A...685A..80Z; fixed positions only for continuum upper limits).
- Lensed sources (2015ApJ...811..124S, 2018Natur.553...51M), SZ pressure profiles (2016ApJ...829L..23B,
  2019A&A...628A.100D), and time-resolved flux from short chunks (2 s in 2018ApJ...855L...2M; each scan in
  2020ApJ...894...76W; `uvmodelfit` per 6 s or 10 s integration with > 3 sigma flare candidates in
  2022ApJ...939L...6B).

## When not to use

| Situation | Use instead |
|---|---|
| Complex, clumpy, non-axisymmetric emission with no simple parametrization | Image-plane analysis or a full imaging/RT model; the pack shows high chi2 and model failures for asymmetric envelopes (2025A&A...700A.188C) and large chi2 for axisymmetric torus models (2019A&A...632A..61G) |
| Source extended toward the largest recoverable scale, no ACA/TP | Add short spacings first; fits near the LRS are unreliable (2014ApJ...791L...6W, 2016ApJ...829L..23B, 2017MNRAS.465.2595M). Resolved-out flux made ACA-only Gaussian envelope fits spiky and only first approximations (2021A&A...653A..53A); a 12-m-only Band 1 mosaic recovered ~30% of the flux (2026A&A...707A.255C) |
| Weak lines at low S/N | Stacking or matched filtering; "S/N for all weak lines is too low" for uv fitting in 2018A&A...617A..23B |
| Only uv-plane continuum subtraction is needed | That is the `continuum-subtraction` technique (several pack papers matched only for `uvcontsub`) |
| VLBI/EHT component modelling (Difmap modelfit, closure quantities) | VLBI-specific tools; pack papers 2020A&A...636A..62K, 2025A&A...695A.233R are outside ALMA uv fitting |
| Lens modelling with a free lens | The `lens-modelling` technique. One pack example of a fixed lens: 2015ApJ...811..124S took the best-fit lens from its ALMA continuum and held it fixed while fitting the source to ATCA CO visibilities |

## Steps

1. **Prepare the visibilities.** Calibrated, self-calibrated MS; line-free channels for continuum, or
   continuum-subtracted channels for lines (carry contsub systematics, 2019ApJ...882..118X). Subtract separable
   (distant) field sources (`uvmodelfit`, `ft`, `uvsub`) but fit close or blended ones jointly
   (2025A&A...700A.188C; uvsub before galario in 2025ApJ...986L..11S); subtraction adds uncertainty to the
   neighbour (2020ApJ...902..141S). Bright off-axis sources need an accurate primary beam: an Airy-disk beam left
   ~5% residuals, fixed by a joint 4-field fit per execution block (2026A&A...707A.255C). For axisymmetric fits,
   recentre on a first Gaussian (`uvmodelfit` then `fixvis`) and check the centre by minimising the RMS of the
   imaginary-part image (2021ApJ...909..212K).
2. **Average to a manageable size, without smearing.** Papers used 10-30 s up to 3-10 min with small uv shift
   (examples in `references/parameters.md`). General practice: keep time/bandwidth smearing at the longest
   baseline below the scales you fit.
3. **Check the weights against the noise.** Know the convention first (general practice from the CASA
   documentation, not the pack): in a CASA MS since 4.2.2, WEIGHT = 1/sigma^2 where sigma is the noise of the
   real part and, separately, of the imaginary part (not of the complex amplitude), so
   chi2 = sum w [(Re_d - Re_m)^2 + (Im_d - Im_m)^2] over 2N real numbers for N visibilities. Weights in archival
   and combined data are often mis-scaled (older CASA versions, averaging, concat), so re-estimate them from the
   data scatter before any chi2 or MCMC fit: recompute with CASA `statwt` (2018MNRAS.475.4924K,
   2024A&A...686A.206Y; 2017MNRAS.465.2595M, card), or compare the per-baseline scatter of Re and Im in
   line-free channels or short time chunks with 1/sqrt(w). Papers also rescaled to the image RMS
   (2020ApJ...902..141S, x0.25), from the scatter (f = stddev^-2 / mean weight, 0.1-0.3, 2024PASJ...76..437Y),
   by a stated factor per execution block (`visweightscale` 0.6 and 0.2, 2026ApJ..1005...94N, derivation not
   given), or fitted the scaling as a free parameter (2020ApJ...898..146M, 2024ApJ...962..166W,
   2021MNRAS.502.5390P; 2025A&A...693A.151M, card). These corrections were dataset-specific; set yours from an
   independent noise estimate, not by forcing the model's reduced chi2 to 1. 11 papers state a
   visibility-weight treatment (9 from my count of current pack lines naming statwt, a rescaling factor,
   visweightscale or free weight scaling, plus 2 confirmed in their cards); separately, 2019MNRAS.485.2092C
   scaled spectral errors so Var(S/sigma)=1 in line-free channels. General practice (not stated in the pack): if the
   weight scale s is free, the log-likelihood must keep the normalisation term, ln L = -chi2/(2 s) - (N/2) ln s
   for N real data values with variances scaled by s (or the full log-determinant for a covariance), and s
   needs a proper prior (for example uniform in log s over a bounded range); dropping that term lets the
   sampler inflate s without limit.
4. **Choose the model family** (simplest that the data need; see the table below). Start with a point or
   Gaussian fit to get centre, flux and rough geometry, then use those as fixed values or priors for the
   detailed model (imfit initial guesses for uvmultifit, 2017ApJ...850...83F; axis ratio and PA fixed from
   the Gaussian fit, 2020ApJ...901...74T; galario geometry passed to frank, 2025ApJ...986L..11S). If geometry
   is fixed for a later fit, propagate its uncertainty: 2025ApJ...986L..11S (card) ran frank 500 times with i and PA
   drawn with 1 deg scatter and offsets with one third of the beam major axis, rather than using one fixed
   geometry (those values are that paper's choice; take the scatter from your own geometry posterior). Fixed
   morphology also sets the flux: in 2018MNRAS.481.1976Z fluxes "depend critically" on the optical size used for
   the exponential model, and a PSF model would underestimate them. Report such fluxes as conditional on the
   adopted shape and refit with plausible size and profile alternatives, especially for low-S/N spectra.
   Image-derived templates need the same care: injecting simulated data through both template construction and
   fitting showed a template normalisation biased to 0.96 +- 0.005 and a regularised template biasing a
   spectral index to -0.26 +- 0.09 (2026A&A...707A.255C).
5. **Compute model visibilities at the observed (u,v).** Analytic models: CASA `uvmodelfit` (one component),
   uvmultifit (several components, per channel), GILDAS `uv_fit`, MIRIAD `uvfit`, AIPS OMFIT. Image models:
   make a model image (analytic or RADMC-3D/LIME), multiply by the primary beam for extended sources
   (Gaussian PB of 24.3'' in 2015ApJ...798..124R; PB multiply in 2020ApJ...898..146M; a PB per pointing for a
   mosaic in 2026A&A...705A.197Z; frank profiles carry no PB correction, 2020MNRAS.498.1319M), then sample its
   Fourier transform with galario or vis_sample (2025A&A...693A.151M, 2020ApJ...891...48H,
   2017A&A...605A..21C). Axisymmetric profiles: Hankel transform of the profile against deprojected
   baselines (2018ApJ...865...37M).
6. **Fit.** Least squares for quick, well-behaved models (Levenberg-Marquardt or SIMPLEX in uvmultifit,
   2014A&A...563A.136M; lmfit in 2025ApJ...986L..22R). For anything with correlated parameters use MCMC
   (emcee, 136 mentions in the pack software aggregates) with likelihood proportional to exp(-chi2/2) and
   uniform priors (2017MNRAS.465.2595M, 2020ApJ...898..146M, 2025A&A...693A.151M; with fixed weights; see
   step 3 for a free weight scale), or nested sampling when you also want Bayes factors (dynesty,
   2020ApJ...902..141S, 2024A&A...687A.308S; MultiNest with 75 live points, 2020RSOS....700063K). Least squares
   with iminuit and Hessian errors served for point-source fits (2026A&A...707A.255C). Expensive RT models are
   fitted by grid search (2018ApJ...865...37M, 2019ApJ...871..100H, 2017A&A...605A..21C).
7. **Get uncertainties.** From the posterior (median or mode with 68% interval, 2015ApJ...798..124R; 95% in
   2020ApJ...902..141S), the covariance at minimum (2018A&A...617A..23B), or a delta-chi2 curve (Delta chi2 = 1
   and 6.63 for 68% and 99% on one parameter, Lp, in 2025ApJ...986L..22R; general practice: 2.30 and 9.21 for
   joint two-parameter regions). Add the dataset's flux-scale uncertainty to fluxes (10% in 2016A&A...596A..75S;
   5% in 2023PSJ.....4..142C), as a correlated term for spectral indices or ratios of jointly calibrated data
   (general practice). Add the astrometric systematic to positions (5% of the beam, 2025Natur.642..905L).
8. **Validate** (see Verification checks): residual image at identical uv coverage, deprojected visibility
   profile with model overlaid, imaginary part for asymmetry, model comparison, injection tests.

### Model families seen in the pack

| Model | Typical use | Tool and examples |
|---|---|---|
| Point source | stars, flares, unresolved galaxies, per-channel spectra | `uvmodelfit` (2020ApJ...894...76W, 2018ApJ...855L...2M, 2024PASJ...76..340K, 2022ApJ...939L...6B per integration and per sideband); GILDAS PSF fit (2019MNRAS.485.2092C, 2025A&A...700A.165B); emcee on > 50 klambda (2020ApJ...898..146M) |
| Circular / elliptical Gaussian | sizes of cores, galaxies, molecular emission | `uvmodelfit` (2014ApJ...797...27F); uvmultifit (2018A&A...617A..23B, 2020ApJ...901...74T); GILDAS `uv_fit` (2024A&A...685A..80Z) |
| Exponential disk (Sersic n=1) | galaxy FIR / [C II] sizes | uvmultifit (2017ApJ...850...83F, 2017ApJ...834..135T, 2020ApJ...900....1F, 2025A&A...693A.237I, which fixed the axis ratio to 1 below peak S/N 8). The size conversion is written inconsistently in the pack: 2017ApJ...850...83F states R_e = 0.826 FWHM, while 2017ApJ...834..135T and 2020ApJ...900....1F state FWHM = 0.826 R_e, and 2025A&A...693A.237I uses R_e,major = 1.21 FWHM (the same relation). Check which size parameter your tool returns and state the relation you used; general practice: for an exponential profile FWHM = 2 ln2 h = 1.386 h and R_e = 1.678 h, so FWHM = 0.826 R_e |
| Uniform / limb-darkened disk | stars, planets, moons, KBOs | uvmodelfit (2023PSJ.....4..142C); AIPS OMFIT (2015ApJ...808...36M); uvmultifit top-hat (2024Natur.633..323V); 2018AJ....156..164B |
| Gaussian rings, power laws, cavities | disk and debris substructure | emcee + Hankel (2018ApJ...865...37M); vis_sample + emcee (2020ApJ...891...48H); galario + emcee (2025A&A...693A.151M, 2025ApJ...986L..11S) |
| Non-parametric radial profile | substructure without an assumed shape | frank, with geometry perturbed over 500 runs (2025ApJ...986L..11S), frank hyperparameter grid (2024A&A...689A.104D, 2024ApJ...974..306S), frank repeated over a grid of assumed scale heights to get a height likelihood (2026A&A...705A.197Z); Fourier-Bessel series up to n=4 terms (2018A&A...616A..88V) |
| RT model image | physical disk/envelope/belt models | RADMC-3D + galario (2020ApJ...902..141S, 2025A&A...693A.151M); RADMC-3D + uvsim + emcee (2017MNRAS.465.2595M); RADMC-3D grid + vis_sample, chi2 beyond 200 klambda (2019ApJ...871..100H); DIAD grid (2018ApJ...865...37M) |
| Line-emission cube | Keplerian disks, abundances, comae | LIME + vis_sample (2017A&A...605A..21C); parametric disk (2015ApJ...813...99F, 2017ApJ...846L..26W, 2018ApJ...856..117F); pdspy Keplerian disks (2024A&A...687A.308S); SUBLIMED + vis_sample (2025ApJ...986L..22R) |
| Lensed source | lensed DSFGs | visilens with an SIE lens (2018Natur.553...51M); SIE lens fixed from the ALMA continuum fit (2015ApJ...811..124S); SIE lens (2018Sci...361.1016S) |

General practice (not from the pack), with theta in radians and baseline q in wavelengths: a Gaussian of FWHM
theta has V(q) = F exp(-(pi theta q)^2 / (4 ln 2)); a uniform disk of diameter theta has
V(q) = 2F J1(pi theta q)/(pi theta q), first null at q = 1.22/theta; a thin ring of radius r has
V(q) = F J0(2 pi r q), first null at q = 0.383/r. Null positions depend on the radial profile and ring width,
so infer sizes from the fitted profile, not from an observed null (2014ApJ...791L...6W fitted ring models to
binned deprojected visibilities around its 290 klambda null).

## Parameter defaults and ranges

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| Sampler | emcee affine-invariant | emcee, dynesty, MultiNest, Metropolis chains, grid | emcee 136, dynesty 9, multinest 5 (pack aggregates) | 2025A&A...693A.151M, 2020ApJ...902..141S, 2020RSOS....700063K |
| Walkers | 100 | 24-1024 | 68 papers give walker counts; 100 in 17, 200 in 12, 120 in 7 (my count of pack parameter lines) | 2018ApJ...869...17L (100), 2019ApJ...878...16P (200), 2025ApJ...988..106H (24), 2019ApJ...881...84S (1024) |
| Walkers per free parameter | 8-10 x N_free | 2-10 | 7 (my count of pack lines), plus "more than double" in 2026A&A...705A.197Z | 2020ApJ...898..146M (10), 2021MNRAS.506.1978L (10), 2025ApJ...986L..11S (8), 2024A&A...688A.149D (8), 2026MNRAS.552g1700S (8) |
| Chain length / burn-in | No default: run until converged (autocorrelation time, stable posteriors) and report what you ran. Historical examples only, not stopping rules | emcee steps per walker 300 (2017MNRAS.465.2595M) to 1e5 (2020ApJ...895..126H, 2025A&A...701A.203S); "more than 250000 steps after convergence" with walkers not stated, so per walker or total is unclear (2021A&A...649A.122P); Metropolis-type chains 1e4-2.4e5 iterations (2017A&A...597A..41G); 1e5 total samples (2019ApJ...875...87D) | about 90 papers mention walkers, steps, burn-in, chains or iterations (my count of pack parameter lines; a few are grid steps) | 2019ApJ...874..136S (~5000 steps after burn-in with autocorrelation time ~1000), 2026A&A...705A.197Z (>= 1e5 samples after convergence), 2018ApJ...865...37M (30000, last 5000 used) |
| Priors | uniform | uniform; sin i or uniform cos i on inclination; Gaussian on geometry/centre | 29 papers mention priors (my count); few give bounds | 2018ApJ...869...17L (+-20 deg i/PA, +-0.5'' offsets), 2024ApJ...966...59S (sin i), 2025ApJ...988..106H (cos i in [0,1]), 2025MNRAS.536.3757A (Gaussian centre, sigma 1'') |
| Weights | statwt, or rescale from an independent noise estimate (image RMS, visibility scatter); CASA WEIGHT = 1/sigma^2 per real and per imaginary part | multiplicative factors 0.1-0.6; free scale factor | 11 (9 from pack lines, 2 from cards; same set as step 3) | 2020ApJ...902..141S (x0.25), 2020ApJ...891...48H (/2.667 = x0.375), 2018MNRAS.475.4924K (x0.4), 2024PASJ...76..437Y (0.1-0.3), 2026ApJ..1005...94N (0.2, 0.6) |
| uv range | full, or cut to isolate a component or drop noise-dominated baselines | > 15 klambda to < 3000 klambda; > 50 klambda (star), < 200 m (planet or moon disk), > 100-400 klambda (compact disks, protostars) | about 19 (my count of pack lines stating a uv cut) | 2020ApJ...898..146M, 2025PSJ.....6..183C (< 200 m; same cut in 2023PSJ.....4..142C, card), 2024ApJ...963..164R, 2024A&A...687A.308S, 2021ApJ...909..212K (< 2000 klambda where amplitude reaches the noise), 2019A&A...626A..81V (> 2-3 Mlambda for SPWs with short-baseline excess) |
| Belt vertical aspect ratio h = H/R | study-specific: fixed when unconstrained, fitted otherwise; state whether H is a Gaussian sigma or a HWHM (HWHM = 1.177 sigma, general practice) | fixed 0.015 (HWHM), 0.03, 0.05; uniform prior [0.005, 0.2] | 8 debris-belt papers (my count of pack lines giving h fixed or fitted) | fixed 0.03: 2020ApJ...898..146M, 2021MNRAS.502.5390P, 2025A&A...693A.151M (fitted where constrained, which "does not necessarily mean" resolved); fixed 0.05: 2026A&A...706A...4R, 2022MNRAS.517.2546L; h_HWHM 0.015 default: 2026A&A...705A.196H; fitted: 2024ApJ...962..166W, 2026A&A...705A.197Z (H_sigma proportional to r) |
| S/N cut | S/N >= 8-10 for sizes | S/N >= 8 to >= 10 | 4 | 2020ApJ...901...74T (10), 2015ApJ...810..133I (10), 2021A&A...654A..90L (8), 2025A&A...693A.237I (axis ratio fixed below 8) |
| Resolved or point | resolved model only if it clearly wins; rules are study-specific | Delta BIC >= 2 for a Gaussian, else beam as upper limit (sign not given in the pack; define Delta BIC = BIC_point - BIC_Gaussian so positive favours the Gaussian); size > 3 sigma from zero; a/sigma_a > 5; P_unres <= 10% | 6 (my count of pack lines) | 2020MNRAS.492.3194S, 2021A&A...645A..33B, 2020AJ....160..248A, 2016ApJ...828...46A, 2019ApJ...877L..23P, 2021NatAs...5..319P |
| Flux systematic | the dataset's own flux-scale uncertainty, in quadrature for single fluxes, as a correlated term for ratios of jointly calibrated data | 5-10% (band-dependent: 5% B3-B6, 10% B7 in 2023A&A...676A...4C) | 11 ALMA papers (my count of pack lines naming a paper and a flux-scale percentage; VLBI papers excluded) | 2016A&A...596A..75S (10%), 2021A&A...653A.117B (10%), 2025A&A...703A..15M (10%), 2020ApJ...894...76W (~10%), 2023PSJ.....4..142C (5%), 2025PSJ.....6..183C (5%); full list in references/parameters.md |

More chain settings, geometry constraints and per-paper fixed values: `references/parameters.md`.

## Software

Counts are mentions in the pack's "software named in the matched steps" aggregate; where two rows are added
(e.g. "casa uvmodelfit" + "uvmodelfit") a paper may be counted twice.

| Software | Used for | Mentions |
|---|---|---|
| CASA | calibration, `statwt`, `uvsub`, `ft`, `uvmodelfit`, residual imaging | 283 (plus tclean 41, uvcontsub 20) |
| emcee | MCMC over model parameters | 136 |
| CASA `uvmodelfit` | single-component point/Gaussian/disk fits; quick sizes and fluxes; light curves | 94 (casa uvmodelfit 56 + uvmodelfit 38) |
| uvmultifit | multi-component and per-channel fits | 86 |
| galario | fast FT of model images at observed (u,v) | 81 |
| GILDAS (`uv_fit`) | point/Gaussian/PSF fits per channel, IRAM-style workflows | 77 (plus gildas uv_fit 6) |
| RADMC-3D | RT model images then sampled in uv | 49 |
| vis_sample | sample model images/cubes at observed (u,v), matched filter | 37 |
| imfit, GALFIT | image-plane cross-checks of uv sizes | 31 (imfit 18 + casa imfit 13), 13 |
| MIRIAD (`uvfit`) | older fits, CARMA/SMA data | 21 (plus miriad uvfit 4) |
| frank (frankenstein) | non-parametric radial profiles, vertical heights | 14 (frank 7 + frankenstein 7) |
| LIME | non-LTE line cubes for visibility fitting | 13 |
| dynesty, MultiNest | nested sampling with evidence | 9, 5 |
| visilens, uvmcmcfit, PyAutoLens | lensed source fitting | 9, 8, 8 |
| pdspy | RADMC-3D disk models fitted in uv (2020ApJ...902..141S, 2024A&A...687A.308S) | 7 |
| pyralysis | uv-plane point-source fits and subtraction on ungridded visibilities (2026A&A...707A.255C) | 4 |

Also in the aggregate: AIPS 9, diskfit 7, lmfit 6, MPFIT 4, uvplot 4 (binned profile plots).

Recommendation from the evidence: `uvmodelfit` for single-component sanity checks (note 11 cards flag its
starting parameters as not stated, so record yours), uvmultifit for several components or per-channel
fluxes, galario or vis_sample + emcee for anything with an image-based or multi-parameter model.

## Pitfalls

- **Unchecked weights.** Pipeline weights needed x0.25 (2020ApJ...902..141S) or /2.667 (2020ApJ...891...48H);
  too-large weights inflate chi2 and narrow posteriors. Do not rescale merely to reach reduced chi2 = 1: high chi2
  can be model inadequacy (2025A&A...700A.188C), which error inflation would hide.
- **Formal errors are not total errors.** Mira sizes and PAs are dominated by systematics (2015ApJ...808...36M);
  errors are sometimes computed assuming reduced chi2 = 1 (2018A&A...617A..23B) or scaled by its square root
  (2017AJ....153..240A); model choice and strict velocity/uv cuts left disk parameters poorly constrained
  (2024A&A...687A.308S); models with different components cannot be compared by fit statistics alone
  (2019MNRAS.487.4037D).
- **Zero-spacing extrapolation.** Total belt flux depends on the model because it is extrapolated to zero
  uv distance (2020ApJ...898..146M). Missing short baselines anti-correlate Mach number and pressure
  normalization in SZ fits (2016ApJ...829L..23B) and hide extended comet sources (2014ApJ...792L...2C).
- **Degenerate shapes.** Gap vs double power law cannot be told apart, and dust opacity is degenerate with
  surface density (2015ApJ...798..124R); belt width and eccentricity parameters degenerate at ~10 au
  resolution (2017ApJ...842....8M); Mdot and alpha degenerate in the physical disk model
  (2018ApJ...865...37M).
- **Axisymmetry hides asymmetry.** Fits to the real part of deprojected visibilities assume axisymmetry
  (2018ApJ...865...37M); azimuthal uv averaging loses 2D morphology (2025A&A...700A.188C); imaginary scatter
  at long baselines hints at asymmetry (2014ApJ...791L...6W). The imaginary-part asymmetry itself depends on
  the chosen phase centre and is noisy at short baselines (2021ApJ...909..212K). Axisymmetric, midplane-peaked
  vertical models can inflate heights in warped belts, and a poor radial profile biases the height
  (2026A&A...705A.197Z).
- **Model selection criteria can disagree.** AIC favoured a ring (Delta AIC = -24.4) while BIC favoured the
  simpler Gaussian (Delta BIC = +11.8) in 2025ApJ...986L..11S (card). Report both and call such substructure tentative.
- **Sizes depend on method and S/N.** Gas-to-dust size ratios 6-8 from visibilities vs 2-2.7 in the image
  plane (2025ApJ...986L..11S, card); faint or compact sources in low-resolution data give unreliable sizes
  (2017ApJ...850...83F); correct with injection tests.
- **Mosaics and primary beams.** uvmultifit mosaic fits require components small relative to the PB
  (2014A&A...563A.136M); an Airy-disk PB left ~5% residuals on a bright off-axis source (2026A&A...707A.255C,
  step 1); frank profiles are not PB corrected (2020MNRAS.498.1319M).
- **Settings papers leave out** (pack "not stated" aggregate, rows summed across phrasings, so a paper can
  count twice): CASA/pipeline version (79 over 7 phrasings), line-free channels (78 over 11), self-cal
  intervals or status (55 over 7), image and cell size (34 over 6), flux calibrator and flux-scale uncertainty
  (27 over 5), reference antenna (12), continuum-subtraction method (11), `uvmodelfit` starting parameters
  (11), source coordinates (7), PB correction (5); excerpts rarely give prior bounds, convergence diagnostics
  or the chi2 definition. Record all of these; propagate continuum-subtraction uncertainty (2019ApJ...882..118X).

## Verification checks

What papers did:
- **Residual image at identical uv coverage**: subtract model visibilities, image the residuals, check they
  are noise-like (2014ApJ...791L...6W, 2014ApJ...797...27F, 2020ApJ...898..146M). 65 of 74 belts passed
  this test in 2025A&A...693A.151M; residuals up to 8.4 sigma remained in 2020ApJ...891...48H and were
  reported.
- **Deprojected visibility profile** with the model overlaid, real and imaginary parts
  (2025A&A...693A.151M, 2020ApJ...902..141S); in 2018ApJ...865...37M a two-ring model failed to reproduce
  the second minimum in the negative visibilities near 600 klambda (card), which led to a third Gaussian.
- **Model comparison**: BIC (lower by about 40 for the belt model, 2017MNRAS.465.2595M), AIC/BIC
  (2020ApJ...898..146M; 2025ApJ...986L..11S, card), Bayes factors (2020ApJ...902..141S).
- **Injection and Monte Carlo tests**: 26,600 artificial sources to correct flux/size bias in S/N bins
  (2017ApJ...850...83F, card); size errors vs S/N from mock sources (2020ApJ...901...74T); simobserve size
  recovery that set the usable resolution range (2020ApJ...888...44C); simulated template visibilities for a
  spectral index (2026A&A...707A.255C). More in `references/parameters.md`.
- **Other checks**: stacked residuals for a faint extended component (2025A&A...693A.237I); halving the model
  pixel (2024A&A...692A.155K); sideband or half-band agreement (2022ApJ...939L...6B, 2021ApJ...909..212K); ACA
  data left out of the fit (2020ApJ...902..141S); image-plane cross-checks (2024A&A...685A..80Z,
  2020ApJ...888...44C); earlier measurements (2018ApJ...855L...2M, 2023PSJ.....4..142C).
- **Chain behaviour**: different walker starting positions (2015ApJ...798..124R); autocorrelation time ~1000
  steps reported (2019ApJ...874..136S); acceptance fraction 0.2-0.5 (2020MNRAS.492..572A); geometry consistent
  between line and continuum fits (2025ApJ...986L..11S). Some papers also redistributed "lost" walkers
  (2020ApJ...902..141S) or dropped walkers 5 sigma below the maximum log-likelihood (2026A&A...705A.197Z) or
  with chi2 - chi2_min > 44 (2019ApJ...874..136S). These are interventions, not convergence tests: pruning by
  likelihood can cut real posterior tails or modes, so after any such step keep sampling the intended
  posterior and recheck convergence on the samples you report.

What a careful referee adds:
- Weights set from an independent noise estimate (step 3), reduced chi2 reported as found, and structured
  residuals explained rather than absorbed (2025A&A...700A.188C).
- Autocorrelation time and acceptance fraction; convergence, not a copied step count, sets the run length.
- Uncertainty from fixed inputs propagated: geometry (2025ApJ...986L..11S), adopted morphology
  (2018MNRAS.481.1976Z), subtracted neighbours (2020ApJ...902..141S), continuum subtraction (2019ApJ...882..118X).
- Per-EB or per-epoch fits agree before combining (2020ApJ...898..146M), or the differences are modelled
  (per-epoch flux scale and centre, 2024A&A...692A.155K; per-observation stellar flux, 2026A&A...705A.197Z).
- Sizes quoted only above the resolution threshold, theta_min = 0.88 theta_beam / sqrt(S/N)
  (2020A&A...643A..53F), upper limits otherwise; flux-scale error included and treated as correlated in ratios.

## Source cards

All 638 papers: `references/sources.md`. Most informative for this technique:

- 2014A&A...563A.136M (uvmultifit method paper, continuum then per-channel fits)
- 2017ApJ...850...83F (uvmultifit sizes for 1034 sources, injection bias correction)
- 2020ApJ...901...74T (Gaussian then exponential disk, size errors vs S/N)
- 2025A&A...693A.237I (uvmultifit [C II] exponential disks, stacked-visibility halo test)
- 2020ApJ...888...44C (uvmodelfit size-recovery simulations, uv vs image-plane sizes)
- 2014ApJ...791L...6W (binned deprojected visibilities, chi2 grid, nulls)
- 2021ApJ...909..212K (recentring, binned real visibilities, imaginary-part asymmetry test)
- 2018ApJ...865...37M (Hankel Gaussian rings, MCMC then RT grid)
- 2020ApJ...891...48H (vis_sample + emcee, 21 parameters, weight rescaling)
- 2025A&A...693A.151M (RADMC-3D + galario + emcee for 74 belts)
- 2026A&A...705A.197Z (belt vertical structure: galario + emcee, frank height grid, limitations)
- 2020ApJ...898..146M (star then belt, free weight scaling, AIC/BIC)
- 2015ApJ...798..124R (PB-multiplied model image, walker tests, degeneracy)
- 2020ApJ...902..141S (galario + dynesty, Bayes factors, ACA check)
- 2025ApJ...986L..11S (two-layer CO fit, galario, frank, AIC vs BIC)
- 2017A&A...605A..21C (LIME + vis_sample, matched filter)
- 2024A&A...687A.308S (pdspy + dynesty Keplerian line fits, uv and velocity cuts, model-choice caveat)
- 2025ApJ...986L..22R (comet coma, lmfit, delta-chi2 errors)
- 2026A&A...707A.255C (pyralysis point-source subtraction, primary-beam residuals, flux loss)
