---
name: alma-uv-plane-fitting
description: "Fit parametric or non-parametric source models directly to ALMA visibilities (point sources, Gaussians, uniform or exponential disks, rings, radiative-transfer or lensed model images, line-emission models) to get fluxes, sizes, positions, geometry and radial profiles with honest uncertainties. Use when a source is compact or near the resolution limit, when image-plane deconvolution would bias sizes or profiles, when fitting disk or debris-belt structure, extracting spectra of unresolved components, measuring stellar or planetary fluxes, or checking someone else's visibility fit. Built from 278 ALMA papers (2012-2026)."
---

# Fitting models directly to visibilities

Compares a model with the measured complex visibilities at the observed (u,v) points instead of with a
deconvolved image, so the fit itself involves no CLEAN deconvolution, beam deconvolution or non-linear masking
(it still inherits the self-calibration model and any sources subtracted beforehand, 2020ApJ...902..141S). It
gives fluxes, sizes, positions, inclination/PA and radial profiles, often below the beam size. The mistakes
that matter most: (1) not checking the visibility weights and treating formal errors as total errors (several
papers scaled pipeline weights down by factors of 2.5 to 4 after checking them against the noise, and formal
errors miss calibration and model systematics), and (2) reading structure
the uv coverage cannot constrain: total flux extrapolated to zero spacing, sizes near the largest recoverable
scale, and degenerate profile shapes (2020ApJ...898..146M, 2014ApJ...791L...6W, 2015ApJ...798..124R).

> Always report: model family and its assumptions (axisymmetric? optically thin?), which data entered the fit
> (uv range, channels, averaging), how weights were set, the fitter/sampler with priors and chain settings,
> and the validation (residual image at identical uv coverage, deprojected visibility profile).

## When to use

- Compact or barely resolved continuum sources where you need size and flux: submm galaxy FIR sizes
  (uvmultifit exponential disk, 2017ApJ...850...83F; 2020ApJ...901...74T), protostellar disks
  (2024ApJ...963..164R), cores (2014ApJ...797...27F).
- Stars, planets, moons and comets where the model is physically simple: point source fluxes
  (2020ApJ...894...76W, 2018ApJ...855L...2M), uniform or limb-darkened disks (2023PSJ.....4..142C,
  2015ApJ...808...36M, 2018AJ....156..164B, 2024Natur.633..323V), Haser coma models (2014ApJ...792L...2C,
  2025ApJ...986L..22R).
- Protoplanetary disk and debris belt structure: axisymmetric ring/gap profiles (2018ApJ...865...37M,
  2018ApJ...869...17L, 2020ApJ...891...48H), belt radius/width/height (2025A&A...693A.151M,
  2017MNRAS.465.2595M, 2019ApJ...875...87D), radiative-transfer model images compared in the uv plane
  (2020ApJ...902..141S, 2019ApJ...871..100H).
- Line emission: Keplerian disk models for dynamical masses, turbulence and temperature
  (2017ApJ...846L..26W, 2018ApJ...856..117F, 2025ApJ...986L..11S), parameterized abundance models
  (2017A&A...605A..21C), matched-filter detection of weak lines (2017A&A...605A..21C; this assumes the weak
  and template lines are co-spatial, and template mismatch makes the derived fluxes lower limits, so use it for
  detection significance, not for reliable integrated fluxes). Line fits return temperature and turbulence
  that depend on the assumed parametric structure: mock tests in 2018ApJ...856..117F recovered temperature
  poorly (20-50%) far from the tau=1 surface, so test how fitted turbulence shifts with the temperature and
  abundance assumptions before quoting it.
- Per-channel spectra of unresolved components that overlap in the image: lensed quasar images
  (2014A&A...566A.112M, 2020A&A...637A...7M), galaxies treated as unresolved PSF responses
  (2019MNRAS.485.2092C, 2025A&A...700A.165B), clumps fitted as PSFs with a free centre per channel
  (2024A&A...685A..80Z, which used fixed-position uv fits only for continuum upper limits).
- Lensed sources (visibility-plane lens models: 2015ApJ...811..124S, 2018Natur.553...51M) and SZ pressure
  profiles (2016ApJ...829L..23B, 2019A&A...628A.100D).
- Time-resolved flux (flares, variability) from short visibility chunks (2018ApJ...855L...2M fit 2 s
  intervals; 2020ApJ...894...76W fit each 6-8 min scan).

## When not to use

| Situation | Use instead |
|---|---|
| Complex, clumpy, non-axisymmetric emission with no simple parametrization | Image-plane analysis or a full imaging/RT model; the pack shows high chi2 and model failures for asymmetric envelopes (2025A&A...700A.188C) and large chi2 for axisymmetric torus models (2019A&A...632A..61G) |
| Source extended toward the largest recoverable scale, no ACA/TP | Add short spacings first; fits near the LRS are unreliable (2014ApJ...791L...6W, 2016ApJ...829L..23B, 2017MNRAS.465.2595M) |
| Weak lines at low S/N | Stacking or matched filtering; "S/N for all weak lines is too low" for uv fitting in 2018A&A...617A..23B |
| Only uv-plane continuum subtraction is needed | That is the `continuum-subtraction` technique (several pack papers matched only for `uvcontsub`) |
| VLBI/EHT component modelling (Difmap modelfit, closure quantities) | VLBI-specific tools; pack papers 2020A&A...636A..62K, 2025A&A...695A.233R are outside ALMA uv fitting |
| Lens modelling with a free lens | The `lens-modelling` technique. One pack example of a fixed lens: 2015ApJ...811..124S took the best-fit lens from its ALMA continuum and held it fixed while fitting the source to ATCA CO visibilities |

## Steps

1. **Prepare the visibilities.** Calibrated, self-calibrated MS; line-free channels for continuum, or
   continuum-subtracted channels for lines. Shift phase centre if needed (fixvis in 2017MNRAS.465.2595M).
   Deal with other field sources: subtract separable (distant) ones by modelling them with `uvmodelfit`,
   predicting with `ft` and removing with `uvsub`, but fit close or blended secondaries jointly with the target
   (2025A&A...700A.188C does both; uvsub of an external source before the galario fit in 2025ApJ...986L..11S).
   Subtraction adds uncertainty: the envelope mass of a source next to a subtracted one was flagged as more
   uncertain than its nominal errors (2020ApJ...902..141S). If continuum subtraction feeds a line fit, carry its
   systematics; 2019ApJ...882..118X notes its uncertainties may be underestimated for leaving them out.
2. **Average to a manageable size, without smearing.** Time averaging: 3 min and 2 GHz bins
   (2017MNRAS.465.2595M), up to 3 min with uv separation < 10 m (2018Sci...361.1016S), up to 10 min with
   uv separation < 15 m (2019ApJ...873...50D), 10 s and four channels per SPW (2018MNRAS.475.4924K). General
   practice: check that time/bandwidth smearing at the longest baseline stays below the scales you fit.
3. **Check the weights against the noise.** Recompute with CASA `statwt` (2018MNRAS.475.4924K,
   2017MNRAS.465.2595M) or rescale to match the image RMS or the scatter (x0.25 in 2020ApJ...902..141S;
   /2.667 in 2020ApJ...891...48H; 1/2.5 in 2018MNRAS.475.4924K), or fit the scaling as a free parameter
   (2020ApJ...898..146M, 2025A&A...693A.151M). These corrections were dataset-specific; set yours from an
   independent noise estimate (line-free channels, image RMS, visibility scatter), not by forcing the model's
   reduced chi2 to 1. My count of pack lines naming statwt, weights or reweighting: 6 papers state an explicit
   visibility-weight treatment (2019MNRAS.485.2092C also scaled spectral errors so Var(S/sigma)=1 in
   line-free channels); most cards do not. General practice (not stated in the pack): if the weight scale s
   is a free parameter, the log-likelihood must keep the normalisation term, ln L = -chi2/(2 s) - (N/2) ln s
   for N real data values with variances scaled by s (or the full log-determinant for a covariance), and s
   needs a proper prior (for example uniform in log s over a bounded range); dropping that term lets the
   sampler inflate s without limit.
4. **Choose the model family** (simplest that the data need; see the table below). Start with a point or
   Gaussian fit to get centre, flux and rough geometry, then use those as fixed values or priors for the
   detailed model (imfit initial guesses for uvmultifit, 2017ApJ...850...83F; axis ratio and PA fixed from
   the Gaussian fit, 2020ApJ...901...74T; galario geometry passed to frank, 2025ApJ...986L..11S). If geometry
   is fixed for a later fit, propagate its uncertainty: 2025ApJ...986L..11S ran frank 500 times with i and PA
   drawn with 1 deg scatter and offsets with one third of the beam major axis, rather than using one fixed
   geometry (those values are that paper's choice; take the scatter from your own geometry posterior).
5. **Compute model visibilities at the observed (u,v).** Analytic models: CASA `uvmodelfit` (one component),
   uvmultifit (several components, per channel), GILDAS `uv_fit`, MIRIAD `uvfit`, AIPS OMFIT. Image models:
   make a model image (analytic or RADMC-3D/LIME), multiply by the primary beam for extended sources
   (Gaussian PB of 24.3'' in 2015ApJ...798..124R; PB multiply in 2020ApJ...898..146M), then sample its
   Fourier transform with galario or vis_sample (2025A&A...693A.151M, 2020ApJ...891...48H,
   2017A&A...605A..21C). Axisymmetric profiles: Hankel transform of the profile against deprojected
   baselines (2018ApJ...865...37M).
6. **Fit.** Least squares for quick, well-behaved models (Levenberg-Marquardt or SIMPLEX in uvmultifit,
   2014A&A...563A.136M; lmfit in 2025ApJ...986L..22R). For anything with correlated parameters use MCMC
   (emcee, 74 mentions in the pack software aggregates) with likelihood proportional to exp(-chi2/2) and
   uniform priors (2017MNRAS.465.2595M, 2020ApJ...898..146M, 2025A&A...693A.151M; with fixed weights; see
   step 3 for a free weight scale), or nested sampling
   (dynesty, 2020ApJ...902..141S) when you also want Bayes factors. Expensive RT models are fitted by grid
   search (2018ApJ...865...37M, 2019ApJ...871..100H, 2017A&A...605A..21C).
7. **Get uncertainties.** From the posterior (median or mode with 68% interval, 2015ApJ...798..124R; 95%
   in 2020ApJ...902..141S), from the covariance at minimum (2018A&A...617A..23B, 2025ApJ...986L..22R), or
   from a delta-chi2 curve (2025ApJ...986L..22R used Delta chi2 = 1 and 6.63 for 68% and 99% confidence on a
   single parameter, Lp; general practice: for joint regions in two parameters the 68% and 99% thresholds are
   2.30 and 9.21, so pick the threshold for the number of parameters of interest). Add the dataset's absolute
   flux calibration uncertainty in quadrature to fluxes (10% in 2016A&A...596A..75S, 2021A&A...653A.117B; 5%
   in 2023PSJ.....4..142C). General practice: the calibration error is shared by measurements calibrated
   together, so do not add it independently to each point of a spectral index or ratio from the same data;
   propagate it as a correlated term.
8. **Validate** (see Verification checks): residual image at identical uv coverage, deprojected visibility
   profile with model overlaid, imaginary part for asymmetry, model comparison, injection tests.

### Model families seen in the pack

| Model | Typical use | Tool and examples |
|---|---|---|
| Point source | stars, flares, unresolved galaxies, per-channel spectra | `uvmodelfit` (2020ApJ...894...76W, 2018ApJ...855L...2M, 2024PASJ...76..340K); GILDAS PSF fit (2019MNRAS.485.2092C, 2025A&A...700A.165B); emcee on > 50 klambda (2020ApJ...898..146M) |
| Circular / elliptical Gaussian | sizes of cores, galaxies, molecular emission | `uvmodelfit` (2014ApJ...797...27F); uvmultifit (2018A&A...617A..23B, 2020ApJ...901...74T); GILDAS `uv_fit` (2024A&A...685A..80Z) |
| Exponential disk (Sersic n=1) | galaxy FIR / [C II] sizes | uvmultifit (2017ApJ...850...83F, 2017ApJ...834..135T, 2020ApJ...900....1F). The size conversion is written inconsistently in the pack: 2017ApJ...850...83F states R_e = 0.826 FWHM, while 2017ApJ...834..135T and 2020ApJ...900....1F state FWHM = 0.826 R_e. Check which size parameter your tool returns and state the relation you used; general practice: for an exponential profile FWHM = 2 ln2 h = 1.386 h and R_e = 1.678 h, so FWHM = 0.826 R_e |
| Uniform / limb-darkened disk | stars, planets, moons, KBOs | uvmodelfit (2023PSJ.....4..142C); AIPS OMFIT (2015ApJ...808...36M); uvmultifit top-hat (2024Natur.633..323V); 2018AJ....156..164B |
| Gaussian rings, power laws, cavities | disk and debris substructure | emcee + Hankel (2018ApJ...865...37M); vis_sample + emcee (2020ApJ...891...48H); galario + emcee (2025A&A...693A.151M, 2025ApJ...986L..11S) |
| Non-parametric radial profile | substructure without an assumed shape | frank, with geometry perturbed over 500 runs (2025ApJ...986L..11S), frank hyperparameter grid (2024A&A...689A.104D); Fourier-Bessel series up to n=4 terms (2018A&A...616A..88V) |
| RT model image | physical disk/envelope/belt models | RADMC-3D + galario (2020ApJ...902..141S, 2025A&A...693A.151M); RADMC-3D + uvsim + emcee (2017MNRAS.465.2595M); RADMC-3D grid + vis_sample, chi2 beyond 200 klambda (2019ApJ...871..100H); DIAD grid (2018ApJ...865...37M) |
| Line-emission cube | Keplerian disks, abundances, comae | LIME + vis_sample (2017A&A...605A..21C); parametric disk (2015ApJ...813...99F, 2017ApJ...846L..26W, 2018ApJ...856..117F); SUBLIMED + vis_sample (2025ApJ...986L..22R) |
| Lensed source | lensed DSFGs | visilens with an SIE lens (2018Natur.553...51M); SIE lens fixed from the ALMA continuum fit (2015ApJ...811..124S); SIE lens (2018Sci...361.1016S) |

General practice (not from the pack), with theta in radians and baseline q in wavelengths: a Gaussian of FWHM
theta has V(q) = F exp(-(pi theta q)^2 / (4 ln 2)); a uniform disk of diameter theta has
V(q) = 2F J1(pi theta q)/(pi theta q), first null at q = 1.22/theta; a thin ring of radius r has
V(q) = F J0(2 pi r q), first null at q = 0.383/r. Null positions depend on the radial profile and ring width,
so infer sizes from the fitted profile, not by applying one of these formulas to an observed null. The
pack's example: 2014ApJ...791L...6W saw a null at 290 klambda and fitted Gaussian and flat ring models to
the binned deprojected visibilities to get ring radii and widths.

## Parameter defaults and ranges

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| Sampler | emcee affine-invariant | emcee, dynesty, Metropolis chains, grid | emcee 74 mentions, dynesty 3 (pack aggregates) | 2025A&A...693A.151M, 2020ApJ...902..141S |
| Walkers | 100 | 32-1024 | 8 papers use 100 (my count of pack parameter lines) | 2018ApJ...869...17L, 2019ApJ...882...49L, 2019ApJ...881...84S (1024), 2025ApJ...993...90S (32) |
| Walkers per free parameter | 8-10 x N_free | 8-10 | 4 (my count of pack lines) | 2020ApJ...898..146M (10), 2025A&A...693A.151M (10), 2025ApJ...986L..11S (8), 2025MNRAS.543.2723P (8) |
| Chain length / burn-in | No default: run until converged (autocorrelation time, stable posteriors) and report what you ran. Historical examples only, not stopping rules | emcee steps per walker 300 (2017MNRAS.465.2595M) to 1e5 (2020ApJ...895..126H); Metropolis-type chains 1e4-2.4e5 iterations (2017A&A...597A..41G); 1e5 total samples (2019ApJ...875...87D) | about 40 papers state chain settings (my count of pack parameter lines naming walkers, chains, burn-in, links or iterations, optimisers excluded) | 2020ApJ...891...48H (20000 steps, first 10000 discarded), 2018ApJ...869...17L (5000 + 5000, last 1000 used), 2018ApJ...865...37M (30000, last 5000 used) |
| Priors | uniform | uniform; sin i on inclination; Gaussian on geometry/centre | many state "uniform"; few give bounds | 2018ApJ...869...17L (+-20 deg i/PA, +-0.5'' offsets), 2024ApJ...966...59S (sin i), 2020ApJ...891...48H (Gaussian on PA, i, offsets) |
| Weights | statwt, or rescale from an independent noise estimate (image RMS) | multiplicative factors 0.25-0.4; free scale factor | 6 (my count of pack lines naming statwt, weights or reweighting) | 2020ApJ...902..141S (x0.25), 2020ApJ...891...48H (/2.667 = x0.375), 2018MNRAS.475.4924K (x1/2.5 = x0.4) |
| Time averaging | <= 3 min with small uv shift | 10 s to 10 min | 4 | 2017MNRAS.465.2595M, 2018Sci...361.1016S, 2019ApJ...873...50D |
| uv range | full, or cut to isolate a component | > 50 klambda (star), < 200 m (planet disk), > 200 or > 400 klambda (compact disk) | 6 | 2020ApJ...898..146M, 2023PSJ.....4..142C, 2019ApJ...871..100H, 2024ApJ...963..164R |
| uv binning for profiles | 10-50 klambda bins | 5-75 klambda | 4 | 2014ApJ...791L...6W (10), 2019ApJ...876..112R (5-50 tested), 2019ApJ...887...40W (50, 75) |
| Model image | >= 1024 px, pixel well below beam | 256-2048 px; 3 mas to 0.02'' | 5 | 2015ApJ...798..124R (2048 x 0.015''), 2019NatAs...3..278K (2048 x 4.6 mas), 2025MNRAS.543.2723P (256 x 0.02'') |
| frank hyperparameters | alpha 1.05-1.3, w_smooth 1e-4 to 1e-1 | N 300-400, Rmax 4 R_out to 5'' | 2 | 2025ApJ...986L..11S, 2024A&A...689A.104D |
| frank geometry uncertainty | perturb i, PA, offsets over repeated fits | 500 runs; 1 deg on i and PA, 1/3 beam major axis on offsets | 1 | 2025ApJ...986L..11S |
| Belt vertical aspect ratio | study-specific assumption: h fixed to 0.03 unless vertically constrained | fitted 0.01-0.3 | 2 | 2025A&A...693A.151M (h fitted where constrained, which "does not necessarily mean" resolved), 2020ApJ...898..146M (h = 0.03 for all models) |
| S/N cut | S/N >= 10 (sizes discussed only above it in 2020ApJ...901...74T) | S/N >= 10 | 2 | 2020ApJ...901...74T, 2015ApJ...810..133I |
| Minimum resolvable size | theta_min = 0.88 theta_beam / sqrt(S/N) | | 1 | 2020A&A...643A..53F |
| Flux systematic | the dataset's own flux-scale uncertainty, in quadrature for single fluxes, as a correlated term for ratios of jointly calibrated data | 5-10% | 4 | 2016A&A...596A..75S (10%), 2021A&A...653A.117B (10%), 2020ApJ...894...76W (~10%), 2023PSJ.....4..142C (5%) |

More chain settings, geometry constraints and per-paper fixed values: `references/parameters.md`.

## Software

Counts are mentions in the pack's "software named in the matched steps" aggregate (names are already
lower-cased and merged there). Where I add two aggregate rows (for example "casa uvmodelfit" and "uvmodelfit")
I say so; one paper may then be counted twice.

| Software | Used for | Mentions |
|---|---|---|
| CASA | calibration, `statwt`, `uvsub`, `ft`, `uvmodelfit`, residual imaging | 105 |
| emcee | MCMC over model parameters | 74 |
| CASA `uvmodelfit` | single-component point/Gaussian/disk fits; quick sizes and fluxes | 39 (casa uvmodelfit 32 + uvmodelfit 7) |
| uvmultifit | multi-component and per-channel fits | 39 |
| galario | fast FT of model images at observed (u,v) | 33 |
| GILDAS (`uv_fit`) | point/Gaussian/PSF fits per channel, IRAM-style workflows | 24 (plus gildas uv_fit 4, gildas/mapping uv_fit 2) |
| RADMC-3D | RT model images then sampled in uv | 26 |
| vis_sample | sample model images/cubes at observed (u,v), matched filter | 21 |
| MIRIAD (`uvfit`, `uvmodel`, `uvamp`) | older fits, CARMA/SMA data | 12 (plus 2 each for uvamp, uvmodel, uvfit) |
| LIME | non-LTE line cubes for visibility fitting | 7 |
| lmfit | least squares | 4 |
| dynesty | nested sampling with evidence | 3 |
| uvsim | simulated visibilities from model images (2017MNRAS.465.2595M) | 2 |
| visilens, uvmcmcfit | lensed source fitting | 2, 2 |
| frank (frankenstein) | non-parametric radial profiles | 2 (2025ApJ...986L..11S, 2024A&A...689A.104D) |

Recommendation from the evidence: `uvmodelfit` for single-component sanity checks (note 10 cards flag its
starting parameters as not stated, so record yours), uvmultifit for several components or per-channel
fluxes, galario or vis_sample + emcee for anything with an image-based or multi-parameter model.

## Pitfalls

- **Unchecked weights.** In two datasets the pipeline weights needed x0.25 (2020ApJ...902..141S) or /2.667
  (2020ApJ...891...48H) to match the noise; if weights are too large, chi2 is inflated and posteriors too
  narrow. Check them against an independent noise estimate for your data; do not rescale merely to bring
  reduced chi2 to 1, because a high chi2 can also come from model inadequacy (asymmetric envelopes and
  unsubtracted field sources in 2025A&A...700A.188C), which error inflation would hide.
- **Formal errors are not total errors.** Mira sizes and PAs are dominated by systematics
  (2015ApJ...808...36M); uncertainties are sometimes computed assuming reduced chi2 of 1
  (2018A&A...617A..23B) or scaled by the square root of reduced chi2 (2017AJ....153..240A).
- **Zero-spacing extrapolation.** Total belt flux depends on the model because it is extrapolated to zero
  uv distance (2020ApJ...898..146M). Missing short baselines anti-correlate Mach number and pressure
  normalization in SZ fits (2016ApJ...829L..23B) and hide extended comet sources (2014ApJ...792L...2C).
- **Degenerate shapes.** Gap vs double power law cannot be told apart, and dust opacity is degenerate with
  surface density (2015ApJ...798..124R); belt width and eccentricity parameters degenerate at ~10 au
  resolution (2017ApJ...842....8M); Mdot and alpha degenerate in the physical disk model
  (2018ApJ...865...37M).
- **Axisymmetry hides asymmetry.** Fits to the real part of deprojected visibilities assume axisymmetry
  (2018ApJ...865...37M); azimuthal uv averaging loses 2D morphology (2025A&A...700A.188C); imaginary scatter
  at long baselines hints at asymmetry (2014ApJ...791L...6W).
- **Model selection criteria can disagree.** AIC favoured a ring (Delta AIC = -24.4) while BIC favoured the
  simpler Gaussian (Delta BIC = +11.8) in 2025ApJ...986L..11S. Report both and call such substructure tentative.
- **Image plane and uv plane give different sizes.** Gas-to-dust size ratios 6-8 in the visibilities vs 2-2.7
  in the image plane (2025ApJ...986L..11S).
- **Low S/N biases sizes.** Faint or compact sources in low-resolution data do not give reliable sizes
  (2017ApJ...850...83F); correct with injection tests (step 8).
- **Mosaics.** uvmultifit mosaic fits require components small relative to the primary beam
  (2014A&A...563A.136M).
- **Settings papers leave out** (pack "not stated" aggregate; where a category appears under several
  phrasings I summed the rows): exact line-free channels (53 across 12 phrasings), self-calibration solution
  intervals (36 across 7), CASA and/or pipeline version (54 across 6), flux calibrator and flux-scale
  uncertainty (15 across 4), reference antenna (11 across 3), continuum-subtraction method or fit order
  (10 across 3), `uvmodelfit` starting parameters (10), image and cell size (10). The excerpts also rarely
  state prior bounds, convergence diagnostics or the exact chi2 definition. Write all of these down, and when
  continuum subtraction feeds the fit, propagate its uncertainty where it matters (2019ApJ...882..118X).

## Verification checks

What papers did:
- **Residual image at identical uv coverage**: subtract model visibilities, image the residuals, check they
  are noise-like (2014ApJ...791L...6W, 2014ApJ...797...27F, 2020ApJ...898..146M). 65 of 74 belts passed
  this test in 2025A&A...693A.151M; residuals up to 8.4 sigma remained in 2020ApJ...891...48H and were
  reported.
- **Deprojected visibility profile** with the model overlaid, real and imaginary parts
  (2025A&A...693A.151M, 2020ApJ...902..141S); in 2018ApJ...865...37M a two-ring model failed to reproduce
  the second minimum in the negative visibilities near 600 klambda, which led to a third Gaussian.
- **Model comparison**: BIC (lower by about 40 for the belt model, 2017MNRAS.465.2595M), AIC/BIC
  (2020ApJ...898..146M, 2025ApJ...986L..11S), Bayes factors (2020ApJ...902..141S).
- **Injection and Monte Carlo tests**: 26,600 artificial sources to correct flux/size bias in S/N bins
  (2017ApJ...850...83F); mock sources giving Delta FWHM = +-0.2'' at S/N 5, +-0.1'' at 10, +-0.05'' at 15
  (2020ApJ...901...74T); injected elliptical Gaussians and disks (2015ApJ...808...36M); mock SZ shocks
  (2016ApJ...829L..23B).
- **Independent data or methods**: ACA data left out of the fit still matched (2020ApJ...902..141S);
  image-plane imfit or Gaussian fit cross-checks (2024A&A...685A..80Z compared five flux methods);
  agreement with earlier measurements (2018ApJ...855L...2M, 2023PSJ.....4..142C, 2017ApJ...850...83F).
- **Chain behaviour**: different walker starting positions (2015ApJ...798..124R); "lost" walkers
  redistributed (2020ApJ...902..141S); geometry consistent between line and continuum fits
  (2025ApJ...986L..11S).

What a careful referee adds:
- Weights calibrated from an independent noise estimate, with reduced chi2 reported as found; where it is
  well above 1, residual structure explained rather than absorbed by inflating errors (2025A&A...700A.188C
  reports chi2 well above 1 and attributes it to asymmetric envelopes and unsubtracted sources).
- Autocorrelation time and acceptance fraction for emcee; chains many autocorrelation times long, so that
  convergence, not a copied step count, sets the run length.
- Uncertainty from fixed inputs propagated: geometry passed to a profile fit (500 perturbed frank runs in
  2025ApJ...986L..11S), subtracted neighbours (2020ApJ...902..141S), continuum subtraction
  (2019ApJ...882..118X).
- Fits per execution block or per epoch agree before combining (per-EB stellar fits in 2020ApJ...898..146M).
- Sizes only quoted above the resolution threshold (2020A&A...643A..53F) and upper limits otherwise
  (0.1'' unresolved limit in 2025MNRAS.543.2723P).
- Absolute flux error included in quoted fluxes, and treated as correlated (not added independently per
  point) in spectral indices or ratios of jointly calibrated data.

## Source cards

All 278 papers: `references/sources.md`. Most informative for this technique:

- 2014A&A...563A.136M (uvmultifit method paper, continuum then per-channel fits)
- 2017ApJ...850...83F (uvmultifit sizes for 1034 sources, injection bias correction)
- 2020ApJ...901...74T (Gaussian then exponential disk, size errors vs S/N)
- 2018A&A...617A..23B (uvmultifit per channel, covariance errors, Monte Carlo chi2)
- 2014ApJ...797...27F (uvmodelfit Gaussian, residual imaging)
- 2020ApJ...894...76W (uvmodelfit point source per EB and per scan)
- 2023PSJ.....4..142C (uniform disk with baseline cut)
- 2015ApJ...808...36M (uniform disk, injection tests, systematics)
- 2014ApJ...791L...6W (binned deprojected visibilities, chi2 grid, nulls)
- 2018ApJ...865...37M (Hankel Gaussian rings, MCMC then RT grid)
- 2020ApJ...891...48H (vis_sample + emcee, 21 parameters, weight rescaling)
- 2025A&A...693A.151M (RADMC-3D + galario + emcee for 74 belts)
- 2020ApJ...898..146M (star then belt, free weight scaling, AIC/BIC)
- 2017MNRAS.465.2595M (four belt models, BIC)
- 2015ApJ...798..124R (PB-multiplied model image, walker tests, degeneracy)
- 2020ApJ...902..141S (galario + dynesty, Bayes factors, ACA check)
- 2025ApJ...986L..11S (two-layer CO fit, galario, frank, AIC vs BIC)
- 2024A&A...689A.104D (frank hyperparameters)
- 2017A&A...605A..21C (LIME + vis_sample, matched filter)
- 2025ApJ...986L..22R (comet coma, lmfit, delta-chi2 errors)
- 2014ApJ...792L...2C (Haser model on visibility amplitudes)
- 2015ApJ...811..124S (lensed source fit per channel)
- 2016ApJ...829L..23B (SZ shock fit, short-spacing degeneracy)
- 2024A&A...685A..80Z (GILDAS uv_fit per channel, flux-method comparison)
