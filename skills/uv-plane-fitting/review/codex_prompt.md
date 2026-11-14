# Review task: an ALMA agent skill against its evidence pack

You are reviewing a skill file (SKILL.md, plus an optional parameters table) that another model wrote from the
EVIDENCE PACK below. The pack is built from methods cards of published ALMA papers; every quote in it was
mechanically verified against the paper text. The skill will be given to research agents that analyse ALMA data,
so wrong defaults or misattributed practice cause real errors. You have no file access: everything you need is in
this message.

Check, in this order:

1. **Attribution.** Every number, range, default, software attribution and "papers do X" claim that cites
   bibcodes: does the pack support it for those bibcodes? Flag claims the pack contradicts, claims cited to a paper
   whose pack entry says something else, and counts that do not match the pack aggregates.
2. **Unsupported practice.** Statements presented as literature practice with no support in the pack. (General
   background marked as general practice is fine if it is correct.)
3. **Scientific correctness.** Wrong formulas, wrong units, wrong CASA task/parameter names or semantics, unsafe
   advice, or a recommendation that contradicts the evidence.
4. **Omissions.** Important pitfalls, assumptions or validation checks that are clearly present in the pack (for
   example in "Limitations the authors admit" or "Settings cards flag as needed but not stated") but missing from
   the skill.
5. **Usability.** Anything an agent would misread or could not act on.

Output format (Markdown, nothing else):

```
# Codex review: <slug>
VERDICT: CLEAN | FIX
## Findings
- SR-01 | high|medium|low | <attribution|unsupported|science|omission|usability> | <the claim, quoted briefly> | <problem, citing the pack line or bibcode> | <concrete fix>
- SR-02 | ...
## Notes
<at most 5 lines: overall quality, anything the writer should know>
```

Use `VERDICT: CLEAN` only when there are no high or medium findings. Be specific and terse; do not restate the
skill. Do not invent pack content: when you say the pack contradicts a claim, cite the pack line.

=== SKILL.md (uv-plane-fitting) ===
---
name: alma-uv-plane-fitting
description: "Fit parametric or non-parametric source models directly to ALMA visibilities (point sources, Gaussians, uniform or exponential disks, rings, radiative-transfer or lensed model images, line-emission models) to get fluxes, sizes, positions, geometry and radial profiles with honest uncertainties. Use when a source is compact or near the resolution limit, when image-plane deconvolution would bias sizes or profiles, when fitting disk or debris-belt structure, extracting spectra of unresolved components, measuring stellar or planetary fluxes, or checking someone else's visibility fit. Built from 278 ALMA papers (2012-2026)."
---

# Fitting models directly to visibilities

Compares a model with the measured complex visibilities at the observed (u,v) points instead of with a
deconvolved image, so the result is free of CLEAN artefacts, beam deconvolution and non-linear masking. It
gives fluxes, sizes, positions, inclination/PA and radial profiles, often below the beam size. The mistakes
that matter most: (1) trusting pipeline visibility weights and formal errors (several papers rescale weights
by factors of 2.5 to 4, and formal errors miss calibration and model systematics), and (2) reading structure
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
  (2017A&A...605A..21C), matched-filter detection of weak lines (2017A&A...605A..21C).
- Per-channel spectra of unresolved components that overlap in the image: lensed quasar images
  (2014A&A...566A.112M, 2020A&A...637A...7M), clumps or galaxies at fixed positions (2024A&A...685A..80Z,
  2019MNRAS.485.2092C, 2025A&A...700A.165B).
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
| Lens modelling with a free lens | The `lens-modelling` technique; here lens parameters are usually held fixed (2015ApJ...811..124S) |

## Steps

1. **Prepare the visibilities.** Calibrated, self-calibrated MS; line-free channels for continuum, or
   continuum-subtracted channels for lines. Shift phase centre if needed (fixvis in 2017MNRAS.465.2595M).
   Remove unrelated field sources first: model them with `uvmodelfit`, predict with `ft`, subtract with
   `uvsub` (2025A&A...700A.188C; uvsub of an external source before the galario fit in 2025ApJ...986L..11S).
2. **Average to a manageable size, without smearing.** Time averaging: 3 min and 2 GHz bins
   (2017MNRAS.465.2595M), up to 3 min with uv separation < 10 m (2018Sci...361.1016S), up to 10 min with
   uv separation < 15 m (2019ApJ...873...50D), 10 s and four channels per SPW (2018MNRAS.475.4924K). General
   practice: check that time/bandwidth smearing at the longest baseline stays below the scales you fit.
3. **Fix the weights.** Recompute with CASA `statwt` (2018MNRAS.475.4924K, 2017MNRAS.465.2595M) or rescale
   to match the image RMS or the scatter (x0.25 in 2020ApJ...902..141S; /2.667 in 2020ApJ...891...48H;
   1/2.5 in 2018MNRAS.475.4924K), or fit the scaling as a free parameter (2020ApJ...898..146M,
   2025A&A...693A.151M). My count of the pack: 7 papers state an explicit weight treatment; most cards do not.
4. **Choose the model family** (simplest that the data need; see the table below). Start with a point or
   Gaussian fit to get centre, flux and rough geometry, then use those as fixed values or priors for the
   detailed model (imfit initial guesses for uvmultifit, 2017ApJ...850...83F; axis ratio and PA fixed from
   the Gaussian fit, 2020ApJ...901...74T; galario geometry passed to frank, 2025ApJ...986L..11S).
5. **Compute model visibilities at the observed (u,v).** Analytic models: CASA `uvmodelfit` (one component),
   uvmultifit (several components, per channel), GILDAS `uv_fit`, MIRIAD `uvfit`, AIPS OMFIT. Image models:
   make a model image (analytic or RADMC-3D/LIME), multiply by the primary beam for extended sources
   (Gaussian PB of 24.3'' in 2015ApJ...798..124R; PB multiply in 2020ApJ...898..146M), then sample its
   Fourier transform with galario or vis_sample (2025A&A...693A.151M, 2020ApJ...891...48H,
   2017A&A...605A..21C). Axisymmetric profiles: Hankel transform of the profile against deprojected
   baselines (2018ApJ...865...37M).
6. **Fit.** Least squares for quick, well-behaved models (Levenberg-Marquardt or SIMPLEX in uvmultifit,
   2014A&A...563A.136M; lmfit in 2025ApJ...986L..22R). For anything with correlated parameters use MCMC
   (emcee, 73 mentions in the pack software aggregates) with likelihood proportional to exp(-chi2/2) and
   uniform priors (2017MNRAS.465.2595M, 2020ApJ...898..146M, 2025A&A...693A.151M), or nested sampling
   (dynesty, 2020ApJ...902..141S) when you also want Bayes factors. Expensive RT models are fitted by grid
   search (2018ApJ...865...37M, 2019ApJ...871..100H, 2017A&A...605A..21C).
7. **Get uncertainties.** From the posterior (median or mode with 68% interval, 2015ApJ...798..124R; 95%
   in 2020ApJ...902..141S), from the covariance at minimum (2018A&A...617A..23B, 2025ApJ...986L..22R), or
   from delta-chi2 contours (Delta chi2 = 1 and 6.63 in 2025ApJ...986L..22R). Add absolute flux calibration
   error (10%) in quadrature to fluxes (2016A&A...596A..75S, 2021A&A...653A.117B).
8. **Validate** (see Verification checks): residual image at identical uv coverage, deprojected visibility
   profile with model overlaid, imaginary part for asymmetry, model comparison, injection tests.

### Model families seen in the pack

| Model | Typical use | Tool and examples |
|---|---|---|
| Point source | stars, flares, unresolved galaxies, per-channel spectra | `uvmodelfit` (2020ApJ...894...76W, 2018ApJ...855L...2M, 2024PASJ...76..340K); GILDAS PSF fit (2019MNRAS.485.2092C, 2025A&A...700A.165B); emcee on > 50 klambda (2020ApJ...898..146M) |
| Circular / elliptical Gaussian | sizes of cores, galaxies, molecular emission | `uvmodelfit` (2014ApJ...797...27F); uvmultifit (2018A&A...617A..23B, 2020ApJ...901...74T); GILDAS `uv_fit` (2024A&A...685A..80Z) |
| Exponential disk (Sersic n=1) | galaxy FIR / [C II] sizes | uvmultifit, R_e = 0.826 FWHM (2017ApJ...850...83F, 2017ApJ...834..135T, 2020ApJ...900....1F) |
| Uniform / limb-darkened disk | stars, planets, moons, KBOs | uvmodelfit (2023PSJ.....4..142C); AIPS OMFIT (2015ApJ...808...36M); uvmultifit top-hat (2024Natur.633..323V); 2018AJ....156..164B |
| Gaussian rings, power laws, cavities | disk and debris substructure | emcee + Hankel (2018ApJ...865...37M); vis_sample + emcee (2020ApJ...891...48H); galario + emcee (2025A&A...693A.151M, 2025ApJ...986L..11S) |
| Non-parametric radial profile | substructure without an assumed shape | frank (2025ApJ...986L..11S, 2024A&A...689A.104D); Fourier-Bessel series up to n=4 terms (2018A&A...616A..88V) |
| RT model image | physical disk/envelope/belt models | RADMC-3D + galario/vis_sample (2017MNRAS.465.2595M, 2020ApJ...902..141S, 2019ApJ...871..100H); DIAD grid (2018ApJ...865...37M) |
| Line-emission cube | Keplerian disks, abundances, comae | LIME + vis_sample (2017A&A...605A..21C); parametric disk (2015ApJ...813...99F, 2017ApJ...846L..26W, 2018ApJ...856..117F); SUBLIMED + vis_sample (2025ApJ...986L..22R) |
| Lensed source | lensed DSFGs | visilens (2018Natur.553...51M); fixed SIE lens (2015ApJ...811..124S, 2018Sci...361.1016S) |

General practice (not from the pack): the Gaussian visibility amplitude is
V(q) = F exp(-(pi theta q)^2 / (4 ln 2)) for FWHM theta and baseline q in wavelengths; a uniform disk of
diameter theta gives V(q) = 2F J1(pi theta q)/(pi theta q), whose first null (as seen at 290 klambda in
2014ApJ...791L...6W for a ring) pins the size.

## Parameter defaults and ranges

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| Sampler | emcee affine-invariant | emcee, dynesty, Metropolis chains, grid | emcee 73 mentions, dynesty 3 (pack aggregates) | 2025A&A...693A.151M, 2020ApJ...902..141S |
| Walkers | 100 | 32-1024 | 8 papers use 100 (my count of pack parameter lines) | 2018ApJ...869...17L, 2019ApJ...882...49L, 2019ApJ...881...84S (1024), 2025ApJ...993...90S (32) |
| Walkers per free parameter | 8-10 x N_free | 8-10 | 3 | 2020ApJ...898..146M, 2025A&A...693A.151M, 2025ApJ...986L..11S |
| Steps / burn-in | 5000-20000 steps, discard first 20-50% | 1000 to 1e5 steps | about 35 papers state chain settings (my count) | 2020ApJ...891...48H (20000, 10000 burn), 2018ApJ...869...17L (5000, last 1000 used) |
| Priors | uniform | uniform; sin i on inclination; Gaussian on geometry/centre | many state "uniform"; few give bounds | 2018ApJ...869...17L (+-20 deg i/PA, +-0.5'' offsets), 2024ApJ...966...59S (sin i), 2020ApJ...891...48H (Gaussian on PA, i, offsets) |
| Weights | statwt or rescale to image RMS | x0.25 to x1/2.667; free scale factor | 7 (my count) | 2020ApJ...902..141S, 2020ApJ...891...48H, 2018MNRAS.475.4924K |
| Time averaging | <= 3 min with small uv shift | 10 s to 10 min | 4 | 2017MNRAS.465.2595M, 2018Sci...361.1016S, 2019ApJ...873...50D |
| uv range | full, or cut to isolate a component | > 50 klambda (star), < 200 m (planet disk), > 200 or > 400 klambda (compact disk) | 6 | 2020ApJ...898..146M, 2023PSJ.....4..142C, 2019ApJ...871..100H, 2024ApJ...963..164R |
| uv binning for profiles | 10-50 klambda bins | 5-75 klambda | 4 | 2014ApJ...791L...6W (10), 2019ApJ...876..112R (5-50 tested), 2019ApJ...887...40W (50, 75) |
| Model image | >= 1024 px, pixel well below beam | 256-2048 px; 3 mas to 0.02'' | 5 | 2015ApJ...798..124R (2048 x 0.015''), 2019NatAs...3..278K (2048 x 4.6 mas), 2025MNRAS.543.2723P (256 x 0.02'') |
| frank hyperparameters | alpha 1.05-1.3, w_smooth 1e-4 to 1e-1 | N 300-400, Rmax 4 R_out to 5'' | 2 | 2025ApJ...986L..11S, 2024A&A...689A.104D |
| Belt vertical aspect ratio | fixed h = 0.03 unless resolved | fitted 0.01-0.3 | 2 | 2025A&A...693A.151M, 2020ApJ...898..146M |
| S/N cut | S/N >= 10 (sizes discussed only above it in 2020ApJ...901...74T) | S/N >= 10 | 2 | 2020ApJ...901...74T, 2015ApJ...810..133I |
| Minimum resolvable size | theta_min = 0.88 theta_beam / sqrt(S/N) | | 1 | 2020A&A...643A..53F |
| Flux systematic | 10% added in quadrature | 5-10% | 4 | 2016A&A...596A..75S, 2021A&A...653A.117B, 2020ApJ...894...76W, 2023PSJ.....4..142C (5%) |

More chain settings, geometry constraints and per-paper fixed values: `references/parameters.md`.

## Software

Counts are mentions in the pack's "software named in the matched steps" aggregate; I summed case variants
(uvmultifit + UVMULTIFIT, galario + GALARIO + Galario), so one paper may be counted twice.

| Software | Used for | Mentions |
|---|---|---|
| CASA | calibration, `statwt`, `uvsub`, `ft`, `uvmodelfit`, residual imaging | 105 |
| emcee | MCMC over model parameters | 73 |
| CASA `uvmodelfit` | single-component point/Gaussian/disk fits; quick sizes and fluxes | 39 (32 + 7) |
| uvmultifit | multi-component and per-channel fits, fixed-position spectra | 38 (24 + 14) |
| galario | fast FT of model images at observed (u,v) | 33 (14 + 12 + 7) |
| GILDAS (`uv_fit`) | point/Gaussian fits per channel, IRAM-style workflows | 24 (+4 `uv_fit`) |
| RADMC-3D | RT model images then sampled in uv | 26 (24 + 2) |
| vis_sample | sample model images/cubes at observed (u,v), matched filter | 21 (19 + 2) |
| MIRIAD (`uvfit`, `uvmodel`) | older fits, CARMA/SMA data | 11 |
| LIME | non-LTE line cubes for visibility fitting | 7 |
| lmfit, MPFIT | least squares | 4, 1 |
| dynesty | nested sampling with evidence | 3 |
| visilens, uvmcmcfit | lensed source fitting | 2, 2 |
| frank | non-parametric radial profiles | not in the aggregate; 2025ApJ...986L..11S, 2024A&A...689A.104D |

Recommendation from the evidence: `uvmodelfit` for single-component sanity checks (note 10 cards flag its
starting parameters as not stated, so record yours), uvmultifit for several components or per-channel
fluxes, galario or vis_sample + emcee for anything with an image-based or multi-parameter model.

## Pitfalls

- **Weights are wrong by default.** Pipeline weights needed x0.25 (2020ApJ...902..141S) or /2.667
  (2020ApJ...891...48H) to match the noise. Without this, chi2 and posteriors are too narrow.
- **Formal errors are not total errors.** Errors "are formal only" (2016A&A...586A..99H); Mira sizes and PAs
  are "dominated by systematic uncertainties" (2015ApJ...808...36M); uncertainties often assume reduced
  chi2 of 1 (2018A&A...617A..23B, 2017AJ....153..240A).
- **Zero-spacing extrapolation.** Total belt flux depends on the model because it is extrapolated to zero
  uv distance (2020ApJ...898..146M). Missing short baselines anti-correlate Mach number and pressure
  normalization in SZ fits (2016ApJ...829L..23B) and hide extended comet sources (2014ApJ...792L...2C).
- **Degenerate shapes.** Gap vs double power law cannot be told apart (2015ApJ...798..124R); r0 and alpha_out
  degenerate when barely resolved (2017A&A...601A...7F); gap width vs depth (2017ApJ...851L..23C); dust
  opacity vs surface density (2015ApJ...798..124R, 2016A&A...586A..99H).
- **Axisymmetry hides asymmetry.** Fitting only the real part discards asymmetry information
  (2017ApJ...839...99P); azimuthal uv averaging loses 2D morphology (2025A&A...700A.188C); imaginary scatter
  at long baselines hints at asymmetry (2014ApJ...791L...6W).
- **Model selection criteria can disagree.** AIC favoured a ring (Delta AIC = -24.4) while BIC favoured the
  simpler Gaussian (Delta BIC = +11.8) in 2025ApJ...986L..11S. Report both and call such substructure tentative.
- **Image plane and uv plane give different sizes.** Gas-to-dust size ratios 6-8 in the visibilities vs 2-2.7
  in the image plane (2025ApJ...986L..11S).
- **Low S/N biases sizes.** Faint or compact sources in low-resolution data do not give reliable sizes
  (2017ApJ...850...83F); correct with injection tests (step 8).
- **Mosaics.** uvmultifit mosaic fits require components small relative to the primary beam
  (2014A&A...563A.136M).
- **Settings papers leave out** (pack "not stated" counts): CASA version (30 cards), self-cal intervals (12),
  `uvmodelfit` starting parameters (10), image and cell size (10), MCMC walkers/steps/priors (2). The cards
  rarely state prior bounds, convergence diagnostics or the exact chi2 definition. Write all of these down.

## Verification checks

What papers did:
- **Residual image at identical uv coverage**: subtract model visibilities, image the residuals, check they
  are noise-like (2014ApJ...791L...6W, 2014ApJ...797...27F, 2020ApJ...898..146M). 65 of 74 belts passed
  this test in 2025A&A...693A.151M; residuals up to 8.4 sigma remained in 2020ApJ...891...48H and were
  reported.
- **Deprojected visibility profile** with the model overlaid, real and imaginary parts
  (2025A&A...693A.151M, 2020ApJ...902..141S); a missing second null drove a third ring in
  2018ApJ...865...37M.
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
- Reduced chi2 near 1 after weight rescaling; if not, say why (2025A&A...700A.188C reports chi2 well above 1).
- Autocorrelation time and acceptance fraction for emcee; chains many autocorrelation times long.
- Fits per execution block or per epoch agree before combining (per-EB stellar fits in 2020ApJ...898..146M).
- Sizes only quoted above the resolution threshold (2020A&A...643A..53F) and upper limits otherwise
  (0.1'' unresolved limit in 2025MNRAS.543.2723P).
- Absolute flux error included in quoted fluxes and spectral indices.

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

=== references/parameters.md ===
# uv-plane fitting: longer parameter tables

All values from the `uv-plane-fitting` evidence pack ("Key parameters and settings" and excerpts). Counts are
my own count of pack lines.

## MCMC chain settings stated in the pack

| Paper | Walkers | Steps | Burn-in / kept | Notes |
|---|---|---|---|---|
| 2016A&A...591A.108O | 200 | 2000 | 500 burn-in | alpha_in fixed 5 |
| 2017ApJ...839...99P | 1000 | 4000 | ~1000 burn-in | radial grid 1-500 au, 0.1 au steps |
| 2017ApJ...843..150F | 80 | 1000 | first 500 | |
| 2017MNRAS.465.2595M | 50-180 | 300-1000 | | 3 min / 2 GHz averaging |
| 2018A&A...610A..24F | 80 | 45000 | after 5000 | |
| 2018ApJ...859..111H | 500 | 1000 | | uniform priors on Md, gamma, Rc, H100 |
| 2018ApJ...866L...6C | 120 | 50e3 | after 30e3 | |
| 2018ApJ...868L...5K | 100 | 500 + 500 | 500 burn-in | 11 free parameters, flat priors |
| 2018ApJ...869...17L | 100 | 5000 (+5000) | last 1000 | uniform +-20 deg i/PA, +-0.5'' offsets |
| 2018ApJ...869...75M | 100 | 10000 | | |
| 2018MNRAS.474.4347C | ~100 | 1000 | | uniform priors with listed bounds |
| 2018MNRAS.475.4924K | 40 | 1000 | ~100 | statwt, reweighting 1/2.5 |
| 2019A&A...626L...2F | 90 | 18000 | after 2000 | uniform priors |
| 2019A&A...628A..95M | 150-400 | 20000-31000 | | 1 or 2 disks |
| 2019ApJ...873...50D | 1000 chains | 1000 extra | 1000 burn-in | |
| 2019ApJ...875...87D | 50 | 1e5 samples | | 0.15 au per pixel |
| 2019ApJ...877L..32M | 100 | 10000 | | |
| 2019ApJ...878...16P | 200 | 2000 | | uniform priors with bounds |
| 2019ApJ...881...84S | 1024 | 1.25e4 | 2.5e3 | |
| 2019ApJ...882...49L | 100 | 5000 | <1000; last 1000 | |
| 2019NatAs...3..278K | 64 | 1000 | after 1000 | 2048 px of 4.6 mas |
| 2020A&A...633A.114S | 200 | 20000 | | |
| 2020ApJ...889...59P | 240 | 2000 | | |
| 2020ApJ...891...48H | 96 | 20000 | 10000 | weights /2.667 |
| 2020ApJ...895..126H | 70 | 100000 | 100 x 1000 | uniform priors |
| 2020ApJ...895L..18B | 144 chains | 15000 | 10000 incl. | |
| 2020ApJ...898...36L | 100 | 5000 | last 1000 | |
| 2020ApJ...898..146M | 10 x N_free (40) | 2000 | | free weight scaling |
| 2024A&A...689A.104D | 80 | 10000 | after 2000 | |
| 2024ApJ...966...59S | 50 | 10000 | | Nuker priors; sin i |
| 2025A&A...693A.151M | 10 x N_free | >= 1000 | | weight rescaling free |
| 2025A&A...700A.188C | 120 | 25000 | | uniform priors |
| 2025ApJ...986L..11S | 192 (8 x N_free); 100 | ~1e4 + 1e4; 10000 | | flat priors |
| 2025ApJ...993...90S | 32 | 1000 | | initialised from SpM cos i and PA |
| 2025MNRAS.543.2723P | 8 per parameter | 30000 | final 10000 | 7 free parameters |

Non-MCMC samplers and optimisers: dynesty nested sampling (2020ApJ...902..141S); Adam optimiser, learning
rate 0.02, 15,000 iterations, 2000 posterior samples (2024ApJ...976..132H); Levenberg-Marquardt or SIMPLEX
(2014A&A...563A.136M); lmfit least squares (2025ApJ...986L..22R); `uvmodelfit` up to 20 iterations
(2020ApJ...899...55A).

## Geometry handling

| Choice | Examples |
|---|---|
| i and PA fixed from continuum or an earlier fit | 2019ApJ...882..160Q, 2018ApJ...868L...5K, 2018ApJ...865...37M (from step 3), 2024NatAs...8..587F |
| i and PA free with offsets | 2018ApJ...865...37M, 2016MNRAS.460.2933M, 2025MNRAS.543.2723P |
| Inclination from Gaussian axis ratio, i = arccos(minor/major) | 2024ApJ...963..164R, 2019ApJ...871..100H, 2016ApJ...828...46A |
| Centre fixed from imfit | 2020ApJ...900....1F |
| Positions fixed, only fluxes free (linear fit) | 2016A&A...593A..61M, 2019ApJ...873L..19B, 2014A&A...563A.136M (step 2) |
| Relative positions bounded by VLBI astrometry (10 mas) | 2014A&A...563A.136M |
| Point-source model if size/uncertainty < 5 | 2016ApJ...828...46A |

## Fixed physical inputs in image-based models

| Paper | Fixed values |
|---|---|
| 2017MNRAS.465.2595M | kappa_abs = 3.8 cm2/g at 0.88 mm; T(r) = 42 (r/150 AU)^-0.5 K |
| 2016MNRAS.460.2933M | kappa_abs = 1.1 cm2/g at 1.3 mm; h lower limit 0.03 |
| 2020ApJ...898..146M | h = 0.03; T proportional to r^-0.5; optically thin |
| 2025A&A...693A.151M | h = 0.03 unless constrained; blackbody grains |
| 2015ApJ...798..124R | flux scaled as nu^(2+beta), beta = 0.4; optically thin, axisymmetric |
| 2020ApJ...891...48H | p = 3.5, a_max = 1 mm; 512 x 1024 x 64 RADMC-3D cells, 10^8 photons |
| 2017ApJ...846L..26W | X_CO = 1e-4, mu = 2.37, r_in = 0.1 au, distance 140 pc with 20 pc added in quadrature |
| 2018ApJ...856..117F | T_mid0, M*, distance, CO abundance, PA, v_sys fixed; T_atm0, q, R_c, i, dv_turb free |
| 2017A&A...605A..21C | i = 44 deg, PA = 133 deg, d = 122 pc; Tc grid 12-36 K in 2 K steps |

=== EVIDENCE PACK (uv-plane-fitting) ===
# Evidence pack: Fitting models directly to visibilities (`uv-plane-fitting`)

Scope: parametric or non-parametric models fitted in the uv plane

Built from 278 non-held-out ALMA papers whose methods cards passed mechanical evidence verification (every quote below is verbatim from the paper). Years 2012-2026.
Matcher (regex over analysis steps): `uvmultifit|galario|vis_sample|uvmodelfit|visibilit\w* (?:fit|model)|(?:fit|model)\w* (?:\w+ ){0,3}visibilit|uv[- ]plane|uv[- ]?fit|in the uv`
Tagging is by regex, so a few papers may be off-topic: ignore those.

## Aggregates over all papers

### Science fields
- protoplanetary_disks: 119
- high_z_galaxies: 62
- star_formation: 58
- astrochemistry: 43
- agn_and_quasars: 33
- debris_disks: 32
- nearby_galaxies: 26
- stellar_physics: 17
- evolved_stars: 11
- exoplanets: 11
- milky_way_ism: 10
- solar_system: 10
- galaxy_clusters_and_sz: 6
- instrumentation: 4
- other: 1

### Software named in the matched steps
- CASA: 105
- emcee: 73
- CASA uvmodelfit: 32
- GILDAS: 24
- uvmultifit: 24
- RADMC-3D: 24
- vis_sample: 19
- UVMULTIFIT: 14
- GALARIO: 14
- galario: 12
- MIRIAD: 11
- LIME: 7
- uvmodelfit: 7
- Galario: 7
- CASA imfit: 6
- lmfit: 4
- AIPS: 3
- imfit: 3
- Python: 3
- galfit: 3
- dynesty: 3
- RATRAN: 2
- MIRIAD uvfit: 2
- MIRIAD uvmodel: 2
- VIS_SAMPLE: 2
- uvsim: 2
- uvmcmcfit: 2
- CASA uvsub: 2
- Hyperion: 2
- DiskFit: 2
- GILDAS UV_FIT: 2
- GALFIT: 2
- DIAD: 2
- radmc-3d: 2
- visilens: 2
- tclean: 2
- pdspy: 2
- GILDAS uv_fit: 2
- SUBLIME: 2
- MPFIT: 1

### Fitting methods (most common phrasings)
- MCMC: 2
- MCMC with emcee, uniform priors: 2
- MPFIT chi2 on visibilities, then manual tweaks; priors not stated: 1
- ln L = -chi^2/2; uniform priors with bounds F_belt, F_cen, sigma^2_cen >= 0 and 0 <= r_i < r_o: 1
- chi2 grid minimization; 1 sigma ranges from chi2 surfaces: 1
- Hand-tuned, not an optimized fit; chi2 of complex visibilities and inspection of CLEANed maps: 1
- Marginal likelihood estimator from chi2 of grid models: 1
- Levenberg-Marquardt or SIMPLEX chi-square minimization: 1
- uv fitting: 1
- Affine-invariant MCMC (emcee), minimizing chi^2: 1
- uncertainties scaled to reduced chi-squared of unity: 1
- chi2 minimization with MCMC; 1 sigma confidence intervals: 1
- chi2 grid search: 1
- Chi-square-like minimisation, Q and Lp free: 1
- Scaling tuned to minimize difference on eastern lobe without over-subtraction: 1
- least-squares minimization in amplitude and phase: 1
- Reduced chi2 grid in M_star and inclination; cavity radius by visual inspection: 1
- emcee affine-invariant MCMC, several hundred walkers and iterations; best values are the mode of marginalized posterior…: 1
- Gaussian model of the visibilities: 1
- Least-squares fits; errors per Condon (1997): 1
- chi-square comparison: 1
- chi^2 grid minimization; errors from rescaling reduced chi^2 to 1: 1
- MCMC with chi^2 metric: 1
- Chi-square fitting; reduced chi2 0.61 vs 5.76 (NB2315-02): 1
- Point source or circular Gaussian model returning centroid, deconvolved size and integrated flux: 1
- MCMC with emcee affine-invariant ensemble sampler, minimizing chi2 over 41 bins; sigma_i from dispersion in bins: 1
- emcee, uniform priors, chi2 with CASA weights: 1
- least squares, linear in visibility space: 1
- Ensemble MCMC; uniform priors except sin(i)/2 on inclination and Gaussian distance prior 145+/-20 pc; i>90 deg enforced: 1
- Levenberg-Marquardt chi2 minimization; initial rho_i at visibility peak centers: 1
- MCMC; AIC for model comparison: 1
- uvmodelfit least squares; aperture uncertainty from random apertures: 1
- uvmodelfit chi^2 minimization, single uniform disk: 1
- emcee affine-invariant sampler, uniform priors, likelihood ∝ exp(-chi2/2): 1
- Weighted least-square image model fit in visibility domain: 1
- Point source model with free flux and position fitted to 12-m EB12-1 to 4 simultaneously: 1
- emcee sampling of likelihood in visibilities; 1 sigma range of posterior: 1
- chi2 grid search, degeneracy between r0 and alpha_out: 1
- Least-squares visibility fitting with UVMULTIFIT; sampler/priors not stated: 1
- Gaussian disk, 6 free parameters for CN: 1

### Validation checks used
- agreement with previous observations: 2
- Compare model and data channel maps: 1
- Reduced chi^2 = 1.37; no significant residuals; fits to each SB individually consistent: 1
- Residual channel maps show no significant emission; reduced chi2 = 1.07: 1
- Residual channel maps and integrated line profiles; admits models are degenerate: 1
- Model SEDs compared with observations; smin=4 um excluded: 1
- continuum fluxes agree with SMA and ALMA SV data: 1
- Cross-check with Gildas mapping: 1
- Fitted positions differ by at most about 15 mas from the true ones in simulations: 1
- Fitting errors show no line features; typical error ~0.5 mJy: 1
- Epochs' spectra averaged after checking profiles unaffected by variations: 1
- Compared with predicted orbit position: 1
- Compared reduced chi^2 and residual maps of ring vs ring+vortex: 1
- offsets of centroids compared with stellar positions: 1
- Best-fit model visibilities compared with binned data; T_ext variations give consistent results: 1
- Residual images with identical uv coverage: 1
- Residuals compared with noise levels: 1
- Residual images after subtracting best-fit model: 1
- Residual image after subtracting disc; Band 3 25 Oct epoch excluded due to resolved calibrator: 1
- Atmospheric O3 lines identified as appearing at same frequency in SW and NE spectra: 1
- Visual comparison of best model with 13CO and C18O maps; SED consistency check with MCFOST: 1
- Different walker starting positions tested; residual maps and visibility profiles inspected: 1
- Monte Carlo and artificial source injection tests for systematic errors: 1
- Residual image from visibility subtraction compared to image-plane differencing: 1
- Monte-Carlo with 82000 mock sources: 1
- Residuals inspected; 85% of structure recovered: 1
- Continuum peak coincides with VLA 8.4 GHz peak: 1
- Residuals consistent with noise; alternative channelizations tested: 1
- Phase calibrator shows constant amplitude (point source): 1
- Compared with CASA imfit in the image plane: 1
- chi2 1437 (single) vs 283 (broken); likelihood-ratio test; 399.S confirms: 1
- Images resolved in CLEAN maps (1'' separation vs 0.75''x0.55'' beam): 1
- Jackknife test splitting time in half for H2O: 1
- mean acceptance fraction 0.48, max autocorrelation time 60; best model imaged with CASA ft/clean and residuals inspected: 1
- Compared with CH3CHO size from same dataset; lines similar peak intensity so S/N bias unlikely: 1
- Similar results from image-plane Gaussian fit: 1
- Compared with jet inclination 82.3 deg from knot proper motions: 1
- Offsets consistent with stellar position given proper motion: 1
- Flux compared with Rayleigh-Jeans photosphere and solar-analog calibration via alpha Cen A: 1
- Model compared with data in channel maps: 1

### Key parameters and settings (bibcode: value)
- 2012ApJ...757..129R: PA fixed 151 deg; M*=0.8 Msun; inclination free; T10,q free per line
- 2013ApJ...762L..21M: ~10^6 MCMC trials; 12 free parameters
- 2013ApJ...765L..14Q: Vertical boundaries fixed: sigma_s = 0.32, sigma_m = 3.2
- 2013ApJ...774...16R: Mgas=0.09 Msun, gamma=0.8, rc=150 AU, Tfrz=19 K, sigma_s=9e20 cm^-2, Tm=19K (r/155AU)^-0.3
- 2013ApJ...774...16R: xi=0.01 km/s, i=224 deg, PA=312 deg
- 2013ApJ...777L..25M: smax fixed 3000 um; smin 4, 6, 8, 16 um
- 2014A&A...563A.136M: PKS 1830-211: relative position bounded within 10 mas of VLBI astrometry
- 2014ApJ...783L..13P: SR 21 ring+vortex inclination fixed to 15 deg
- 2014ApJ...791...20R: R_in = 0.05 AU; free parameters M_disk (Sigma_10AU), p, R_out
- 2014ApJ...791...20R: Grain size distribution n(a) ∝ a^3, amin 0.1 micron; T_ext = 10 K (5, 15 K tested); T ∝ R^-3/4 beyond R_thin
- 2014ApJ...791L...6W: fluxes fixed at 0.962 and 0.024 Jy (302 GHz), 1.190 and 0.048 Jy (346 GHz)
- 2014ApJ...792L...2C: v = 1.0 km/s (ISON), 0.7 km/s (Lemmon) from HCN HWHM
- 2015ApJ...798...85P: h=0.1 r, gamma=1, R_c=200 au, T=50 K (r/50au)^-0.3, b=50 m/s, inner truncation 0.3 au
- 2015ApJ...798..124R: model image 2048x2048 pixels of 0.015''; flux scaled as nu^(2+beta), beta=0.4
- 2015ApJ...808..102K: 25 models per target: b_t = {0.6,0.8,1.0,1.2,1.4}, h = {0.95,1.10,1.25,1.40,1.55}
- 2015ApJ...808..102K: pixel 9 AU, 1024x1024 image
- 2015ApJ...810..133I: S/N>=10 threshold
- 2015ApJ...810L...7V: Grid steps 1 degree and 1 AU
- 2015ApJ...811...39I: gain 0.1, threshold 1.0 mJy
- 2015ApJ...811..124S: Each Gaussian has up to four free parameters: centroid, flux, size
- 2015ApJ...813...99F: Fixed: d=122 pc, M*=2.3 Msun, PA=312 deg, Mgas=0.09 Msun, CO/H2=1e-4 (unless varied)
- 2016A&A...586A..45S: primary beam factor x3.73
- 2016A&A...586A..99H: 4 or 6 free parameters; fixed Sigma_10au=0.39, kappa=3.4, q0=2.6, q1=0.26, R0=7 au
- 2016A&A...591A.108O: 200 walkers, 500 burn-in, 2000 iterations; alpha_in = 5 fixed
- 2016A&A...596A..75S: 10% calibration error added in quadrature
- 2016ApJ...818..156C: p fixed to 1; 12-dimensional posterior
- 2016ApJ...823L..18H: Sigma_c=5e-5 g/cm2, gamma=1, r_c=100 AU, B=3, r_ring=150 AU, sigma_ring=20 AU
- 2016ApJ...823L..18H: turbulent broadening xi = 0.01 km/s
- 2016ApJ...828...25L: beta = 0.8; rho = 2.7 g cm^-3; grain sizes 0.1-3000 um
- 2016ApJ...828...46A: point-source model if a/uncertainty < 5
- 2016ApJ...829....6W: natural weighting; threshold 1/2 sigma_RMS
- 2016ApJ...829L..23B: Free: pressure amplitude, shock radius, Mach number; slopes consistent with X-ray; outer slope marginalized within 30%
- 2016ApJ...833L...6C: 1.5 sigma cutoff CO(1-0); 2.5 sigma cutoff CO(3-2)
- 2016MNRAS.460.2933M: Free parameters: r0, h, Δr, Mdust, PA, i, RA and Dec offsets; h lower limit 0.03
- 2016Natur.535..258C: alpha = ln(F232.6/F218.0)/ln(218.0/232.6)
- 2017A&A...597A..41G: 10,000-240,000 iterations, 5,000 burn-in
- 2017A&A...603L...6H: cutoff uv radius 60 m for the reported results
- 2017A&A...605A..21C: template 1'' beam via uv taper, 0.084 km/s channels
- 2017A&A...605A..21C: R_in = 50 AU for H2CO; Tc 12–36 K in 2 K steps; Rc 210–410 AU (H2CO), 70–350 AU (C18O) in 20 AU steps; X1/X2 0.001–10 (0.1–1000 for C18O)
- 2017A&A...605A..21C: Reference abundances 1e-12 (H2CO), 1e-7 (C18O)
- 2017A&A...605A..21C: H2CO X1 grid [1,2,3,4,5]e-12 with Rc = 270 AU
- 2017A&A...607A..55V: Two disks sharing center, inclination and PA, plus offset Gaussian
- 2017AJ....153..240A: uncertainties scaled by sqrt of reduced chi2; detection >3 sigma
- 2017ApJ...834..135T: FWHM = 0.826 R1/2
- 2017ApJ...836..223W: 200 walkers; star 4300 K, 1 Lsun
- 2017ApJ...839...43O: (z/r)up=0.3, rout=100 AU fixed; vary inner radius, lower boundary, power law
- 2017ApJ...839...99P: short baselines <~200 kλ or full uv
- 2017ApJ...839...99P: radial grid 1-500 au in 0.1 au steps; 4000 steps, 1000 walkers, burn-in ~1000 steps
- 2017ApJ...840...23L: inner disk PA fixed 93 deg, inclination fixed 75 deg
- 2017ApJ...840L..12S: Free: L*, Mdisk, alpha, beta, h0, Rgap, delta, Rdisk, inclination, PA, amax, A_K
- 2017ApJ...842....8M: Free: R_belt, Δa, F_belt, F_star, i, PA, e_f, e_p, ω_f, Δα, Δδ
- 2017ApJ...843..150F: 80 walkers, 1000 steps, first 500 burn-in
- 2017ApJ...844..158S: R_in = 0.1 au; scale height fixed
- 2017ApJ...845..138S: 62.5 MHz channels, robust = 0.5
- 2017ApJ...846..108C: 36000 injected models, peak SNR 1-10, radius up to 2''
- 2017ApJ...846L..14S: Averaged 24 (J2202) or 6 (J0912) channels, ~200 and 50 km/s
- 2017ApJ...846L..26W: Free: Mdisk, Rdisk, gamma, T0, q, xi, M*, vsys, inclination, PA, small centering offset
- 2017ApJ...849...56A: Free: Mdisk, Rout, p, Sdamp, H1, h; fixed: i=85 deg, Rin=0.1 AU, T1=403.5 K, q=0.5, kappa=0.031, g/d=100; outer radius 1000 AU
- 2017ApJ...850...54C: MOM0 cut ±1σ, MOM1 cut ±5σ
- 2017ApJ...850...83F: sizes 0.04''-3.0''; random positions within 10'' radius; SNR bins 5-10, 10-20, 20-30
- 2017ApJ...851...85B: Free: Sigma0, R_dust, h0, p, inclination, position angle; R_in fixed; minimum temperature 10 K
- 2017ApJ...851L..23C: lambda = 0.1, G = 30, eta = 1.0
- 2017MNRAS.465.2595M: Visibilities averaged to 3 min and 2 GHz bins; 300-1000 steps, 50-180 walkers
- 2017MNRAS.466.4201W: 10 chains, 100000 links, acceptance ~26%
- 2017MNRAS.469.4683C: Delta v ~ 1680 km/s
- 2017MNRAS.469.4683C: Assumed clump line FWHM 100 km/s; mean clump FWHM 0.18 arcsec for stack
- 2017NatAs...1E.130Z: v_turb fixed at 0.01 km/s; outer-disk T = 21 K; fixed stellar mass 0.6 Msun, i=7 deg, PA=155 deg
- 2018A&A...610A..24F: 80 chains, 45000 steps after 5000 burn-in
- 2018A&A...613A..34P: eight free parameters
- 2018A&A...616A..88V: up to n=4 terms, 13 free parameters; rho ranges at least 100 klambda wide
- 2018A&A...617A..23B: Gaussian position, flux density, FWHM; delta component at same position
- 2018A&A...619A..39F: line visibilities averaged over -500 to 500 km/s
- 2018A&A...619A.161C: 9 model parameters + center (x_c,y_c) + inclination; PA fixed at 62 deg
- 2018A&A...619A.161C: 120 walkers, 24000 likelihoods
- 2018AJ....156..164B: Eris visibility fit: slightly limb-darkened disk, radius 1163 km; others point sources
- 2018ApJ...852..122H: Fiducial: N_CO=3e19 cm-2, R1=15 AU, R2=70 AU, A=3, f=0.025, Tmid10=40 K, Tatm10=125 K, q=0.47, Tfrz=27 K, Rin=0.05, Rout=215 AU
- 2018ApJ...853..147M: moment 0 integrated within ±7 km/s of stellar velocity
- 2018ApJ...854..130W: Free: M_disk, r_c, gamma, T0, q, xi, v_sys, inclination, PA
- 2018ApJ...856..117F: Free: T_atm0, T_mid0, q_atm, R_c, inclination, δv_turb; fixed: stellar mass, distance, CO abundance, PA, systemic velocity, offset
- 2018ApJ...859...21A: robust +0.5 or -1.0
- 2018ApJ...859...32P: radial grid 0-500 au in 0.5 au steps; last 700 steps used
- 2018ApJ...859...35G: 5"x5" extraction region at peak pixel
- 2018ApJ...859..111H: 500 walkers, 1000 iterations; uniform priors on Md, gamma, Rc, H100
- 2018ApJ...861....7F: sky fixed at 0; center fixed at image center
- 2018ApJ...863..129S: velocity resolution 20, 30 or 50 km/s
- 2018ApJ...865...37M: Free: i, PA, dRA, dDEC, and a_i, sigma_i, x_i per ring
- 2018ApJ...865...37M: Mdot fixed at 7.8e-9 Msun/yr; alpha varied 0.0001-0.01; Rwall 25-40 au; mid amax 1 mm-2.5 cm; eps_atm 0.001-0.8; Rdisk 150-300 au
- 2018ApJ...866L...6C: 120 walkers, 50e3 steps after 30e3 burn-in
- 2018ApJ...867..140L: moment-0 maps collapsed over 300 km/s centered at +/-155 km/s
- 2018ApJ...868L...5K: 11 free parameters, flat priors, 100 walkers, 500 burn-in + 500 steps
- 2018ApJ...869...17L: 100 walkers, 5000 steps, burn-in ~2000; second run 5000 more steps; posterior from last 1000 steps; radial grid 0.0001''-4'' step 0.001''
- 2018ApJ...869...17L: Uniform priors: ±20 deg for i and PA, ±0.5 arcsec for offsets
- 2018ApJ...869...75M: 100 walkers, 10,000 steps
- 2018ApJ...869L..48G: uv-points 10 to 10000 kλ in 10 kλ steps; 27 free parameters (23 ring, 4 geometry)
- 2018MNRAS.474.4347C: Priors uniform: Mdisc 0.001-1 Msun, gamma 0-2, Rc 10-100 au, hc 1-10 au, psi 0-2, Rstar 1-8 Rsun, i 10-80 deg
- 2018MNRAS.474.4347C: ~100 walkers, 1000 iterations
- 2018MNRAS.475.4924K: 40 walkers, 1000 steps, ~100 burn-in; data averaged to 10 s and four channels per SPW; weights recomputed with statwt; reweighting 1/2.5
- 2018Natur.553...51M: Four Sersic components (1 E, 3 W) for visilens
- 2018Sci...361.1016S: time averaging up to 3 min with uv separation <10 m
- 2019A&A...623A.150V: baselines up to 800 klambda (Sz 71) and 500 klambda (Sz 98)
- 2019A&A...625A.118K: robust = 0.5
- 2019A&A...626L...2F: 90 walkers, 18000 steps after 2000 burn-in; uniform priors
- 2019A&A...628A..95M: 150 walkers, ~20000 steps (1 disk); 200 walkers, >25000 steps (2 disks); 400 walkers, 31000 steps (UZ Tau)
- 2019A&A...628A.100D: Priors in Table 1: P_e,us and T_e,us split-normal from X-ray; shock nose and angle split-normal; M uniform 1-10; alpha uniform -10 to 0; kappa normal(1,0.05)
- 2019A&A...628A.118B: natural weighting, 0.04 arcsec pixel, 30 km/s channels
- 2019A&A...630A..59B: Niter 500-1000, threshold 3 sigma
- 2019A&A...632A..61G: 20 km/s channels
- 2019AJ....158..162F: 23 free parameters (7 ring incl. centre offset, plus Gaussian sources)
- 2019ApJ...870...80L: lambda fitted for fixed lens model, alternating with MCMC until convergence
- 2019ApJ...871..100H: Model A free parameters: Lstar, Mdisk, Rdisk, theta_flared, a_pow, a_max; r0 = 25 au
- 2019ApJ...871..112X: robust 0.5, cell 0.3 arcsec
- 2019ApJ...873...50D: time averaging up to 10 min with uv separation <15 m; velocity bins 75-250 km/s
- 2019ApJ...873...50D: 1000 chains, 1000 burn-in, 1000 extra steps
- 2019ApJ...873L..19B: position fixed; only flux density free
- 2019ApJ...875...87D: 50 walkers, 10^5 samples; 0.15 au per pixel
- 2019ApJ...876..112R: uv-bin size varied 5 to 50 klambda
- 2019ApJ...877L..32M: ~10^6 iterations (100 walkers, 10,000 steps each)
- 2019ApJ...878...16P: PA 26.8±1.3 deg, inclination 47.6±2.4 deg
- 2019ApJ...878...16P: 200 walkers, 2000 steps, uniform priors (r_peak 10-80 au, sigma 1-50 au, A 0-1, sigma_inner 0.1-10 au, F_total 0-3 Jy)
- 2019ApJ...878L...8T: Single Gaussian component
- 2019ApJ...881...84S: 1024 walkers, 1.25e4 steps, burn-in 2.5e3
- 2019ApJ...882...49L: 100 walkers, 5000 steps, burn-in <1000, posterior from last 1000 steps
- 2019ApJ...882..118X: Briggs robust 0.5 (B4, B6), 0.0 (B7)
- 2019ApJ...882..160Q: R1 and R2 grid interval of 5 au; vertical boundaries Σ21 = 3.2 and 100; i and PA fixed from continuum
- 2019ApJ...883...22C: robust=0.5
- 2019ApJ...883...71C: Ka and Q combined into 8.0 mm image; K band excluded
- 2019ApJ...887...40W: uv bins 50 klambda (J0129), 75 klambda (J1044)
- 2019ApJ...887..144J: 16 MHz per channel
- 2019MNRAS.482..698C: Free parameters: flux, major/minor FWHM, PA, offsets <1''
- 2019MNRAS.484.1257M: stellar template Teff 5250 K, radius 0.77 Rsun; h>0.02 imposed
- 2019MNRAS.484.1257M: 11 free parameters
- 2019MNRAS.485.2092C: Stack velocity width 753±22 km/s; errors scaled so Var(S/sigma)=1 in line-free channels
- 2019MNRAS.485.2092C: <U>=22; L_IR/Md factor 125; 0.15 dex systematic
- 2019MNRAS.490.4956G: compact Reff fixed to 0.10''; extended Reff ~0.5''
- 2019NatAs...3..278K: 64 walkers, 1000 steps after 1000 step burn-in; scale height 0.05r; 2048 pixels of 4.6 mas
- 2020A&A...633A.114S: 200 walkers, 20000 steps
- 2020A&A...633A.126B: kappa 345GHz = 0.02 cm2/g gas; Tdust ~30 K
- 2020A&A...636A..62K: 10% flux accuracy; position error ~1/10 beam; polarization threshold 9 sigma
- 2020A&A...643A..53F: theta_min = 0.88 theta_beam/sqrt(S/N), theta_beam=0.60''
- 2020AJ....159..288M: Briggs robust 0.5
- 2020ApJ...889...59P: Free: Mdisk, gamma, Rc, H100, Psi plus centroid shift; 240 walkers, 2000 iterations
- 2020ApJ...889...59P: Grid 256x64, 1200 K sublimation inner edge, outer radius 100 au
- 2020ApJ...891...48H: 96 walkers, 20,000 steps, 10,000 burn-in; weights scaled down by 2.667
- 2020ApJ...891...48H: 512 radial cells, 1024 poloidal cells, 64 azimuthal cells, 10^8 photon packages; parameters in Table 4
- 2020ApJ...895..109F: Free: T_atm0, q, R_c, i, δv_turb, R_in, v_sys; fixed PA, γ=1, T_mid0, Z_q0, masses
- 2020ApJ...895..126H: 70 walkers, 100,000 steps, burn-in 100 walkers x 1000 steps; uniform priors
- 2020ApJ...895L..18B: 144 chains, 15000 iterations including 10000 burn-in
- 2020ApJ...897...91G: channel weights w=1/sigma_i^2
- 2020ApJ...898...36L: 100 walkers, 5000 steps, last 1000 used; grid 0.0001-4" step 0.0005"
- 2020ApJ...898...75I: robust 0.0 (Bands 6-8); robust 0.5 with outertaper 0.2'' (Band 3); dV = 10 km/s (20 for 13CO)
- 2020ApJ...898..146M: 2000 steps, 40 walkers, uniform priors, likelihood exp(-chi2/2), free weight scaling
- 2020ApJ...898..146M: aspect ratio h fixed to 0.03; walkers = 10 x free parameters; 2000 steps
- 2020ApJ...899...55A: uvmodelfit up to 20 iterations; 20 (Lambda_l, Lambda_t) sets; 10-fold CV; MFISTA up to 1000 iterations; keep images with MSE < MSE_best+sigma
- 2020ApJ...900....1F: FWHM_major = 0.826 r_e,major; r_e = r_e,major sqrt(q); source center fixed from imfit
- 2020ApJ...901...74T: Only S/N>10 sources (62) used for size discussion
- 2020ApJ...902..132B: position, intensity, sizes and orientation free
- 2020ApJ...902..141S: Visibility weights multiplied by ~0.25 to match image RMS
- 2020ApJ...902..141S: Protostar T=4000 K, luminosity free; inner disk radius 0.1 au; cavity or gap added
- 2020MNRAS.493L.108B: 0.2'' uv-taper; first moment with 2.5 sigma clip
- 2021A&A...653A..46V: 3 sigma detection threshold
- 2021A&A...653A.117B: theta_obs = sqrt(theta_beam^2 + theta_source^2); 10% calibration error in flux
- 2021AJ....161...38O: Sigma(20au)=35 g cm-2, gamma=-1.3, H(20au)=2 au, p=0.3, mean molecular weight 2.37, T_atm=125 K at 10 au
- 2021AJ....161..271F: 22 free parameters (Model 1), 24 (Models 2, 3)
- 2021AJ....161..271F: Surface density zero inside 70 au and beyond 600 au for Models 2 and 3
- 2024A&A...689A..85G: Gaussian ring I(r)=f exp(-0.5((r-r_k)/sigma_k)^2); gamma_SB2=1
- 2024A&A...689A.104D: alpha={1.05,1.2,1.3}, wsmooth={1e-1,1e-4}, Rmax=5.0", p0=1e-35, 300 radial points
- 2024A&A...689A.104D: 80 walkers, 10,000 steps after 2000 burn-in
- 2024A&A...689A.299M: 10 s averaging; spectral window 227.1 GHz
- 2024ApJ...963..164R: uv-distance > 400 kλ; phase center within 0.5" of published positions
- 2024ApJ...966...59S: 50 walkers, 10000 steps; model pixel 3 mas
- 2024ApJ...966...59S: Nuker priors: log10 alpha U(0,2), beta U(0,10), gamma approx uniform (-3,2); point flux U(0,1) mJy
- 2024ApJ...976..132H: Adam optimizer, learning rate 0.02, 15,000 iterations; 2000 posterior samples
- 2024NatAs...8..587F: Free: J0, sigma_G, delta RA, delta Dec; inclination 46.7 deg and PA 138.0 deg fixed
- 2024PASJ...76..340K: detection threshold 3x line image rms; J axis PA=68.35 deg
- 2025A&A...693A.151M: h fixed to 0.03 unless vertically constrained; temperature r^-0.5
- 2025A&A...695A.233R: acceptable reduced chi-square < 2
- 2025A&A...698A.183D: scale height H/r < 0.05; stellar flux not included
- 2025A&A...700A.165B: Low-res: +-30 km/s (three channels each side); high-res: 10 km/s width
- 2025A&A...700A.188C: Uniform priors: sigma 0-0.7'', Ri 0-2.0'', Rout 2.0-15.0'', p+q in [1,3], inc/PA full range, offsets within few tenths of arcsec
- 2025A&A...700A.188C: 120 walkers, 25000 steps
- 2025ApJ...986L..11S: 192 walkers, flat priors, converged after ~10^4 steps, then 10^4 more
- 2025ApJ...986L..11S: 100 walkers, 10000 steps
- 2025ApJ...986L..11S: alpha=1.20, w_smooth=1e-3, N=400, Rmax=4 Rout
- 2025ApJ...986L..22R: Lp=0 assumed for geometry; free Q1,Q2,v1,v2,gamma,phi,psi
- 2025ApJ...986L..22R: Tss=95±9 K (NEATM) or 60 K (CO)
- 2025ApJ...990L..31B: channels |v|>1000 km/s for fit; hogbom; natural weighting
- 2025ApJ...993...90S: 1000 iterations, 32 walkers, init from SpM cos i and PA
- 2025MNRAS.536.3757A: Gaussian prior on centre (sigma 1 arcsec); uniform Vmax 0-600 km/s, sigma 0-200 km/s, r_e 0-2", r_t 0-1"
- 2025MNRAS.543.2723P: 7 free parameters (f0, sigma_r, R_peak, inc, PA, dRA, dDec); 8 walkers per parameter; 30,000 steps then final 10,000; uniform priors; 256x256 pixels of 0.02 ar…
- 2025NatAs...9.1476C: 4 T(r) segments for Apr 18–25; 3 for May 4
- 2026A&A...705A..81K: lens centers fixed at Einstein ring centers with uniform priors; Einstein radius upper limit slightly above Spilker16


### Assumptions (bibcode: value)
- 2012ApJ...757..129R: vertically isothermal, mu=2.37, Keplerian, vr=vz=0
- 2013ApJ...762L..21M: Inclination 89.5 deg
- 2013ApJ...765L..14Q: Keplerian rotation; Qi11 disk structure; constant abundance in a layer; power-law column density
- 2013ApJ...774...16R: 80% of gas is H2; constant CO:H2 abundance; CO depleted by 1e8 below freezeout; ISM isotopologue ratios
- 2013ApJ...777L..25M: Silicate (olivine) + amorphous carbon, Mie theory, size exponent -3.5
- 2014ApJ...783L..13P: Ring emission axisymmetric; PA fixed to 62 deg (SAO 206462) and 16 deg (SR 21)
- 2014ApJ...791...20R: Distance 140 pc; gas-to-dust ratio 100; kappa 0.02 cm2/g_gas at 0.89 mm
- 2014ApJ...791L...6W: Circular symmetry
- 2014ApJ...792L...2C: T=90 K (ISON), 55 K (Lemmon); excitation by H2O and electron collisions and solar IR pumping
- 2015A&A...577L...4V: Distance 92 pc
- 2015ApJ...798...85P: Keplerian rotation, ISM CO abundance, vertically isothermal, axisymmetric
- 2015ApJ...798..124R: axisymmetric, geometrically and optically thin disk; constant dust opacity across disk
- 2015ApJ...808...36M: distance 110 pc; Tb=2Sc^2/(k nu^2 pi theta_maj theta_min)
- 2015ApJ...808..102K: distance 140 pc; constant beta; accretion disk cut at 5 Rc
- 2015ApJ...810..133I: Symmetric Gaussian profile
- 2015ApJ...811..124S: Lens parameters fixed to ALMA best fit
- 2015ApJ...813...99F: CO frozen out below 19 K and photodissociated above column threshold (abundance reduced by 8 orders of magnitude); LTE; mu=2.37
- 2016A&A...586A..99H: Constant dust opacity 3.4 cm2/g; geometrically thin, vertically isothermal; cos i ~ 1
- 2016A&A...591A.108O: circular disk
- 2016A&A...595L...4L: Elliptical Gaussian spatial distribution
- 2016A&A...595L...4L: Vsys = +1.7 km/s
- 2016A&A...596A..88L: Flat disk inclination from axis ratio; CO may underestimate true inclination because emission arises above the disk plane
- 2016ApJ...818..156C: Vertically isothermal, radial power-law temperature, hydrostatic equilibrium, Keplerian rotation, LTE
- 2016ApJ...818L..16Z: flat intensity inside the cavity
- 2016ApJ...823L..18H: LTE; Keplerian velocities; ISM isotopologue ratios 69 and 557; T_atm,10=150 K, q_atm=0.5; C18O traces CO column
- 2016ApJ...828...25L: Compact astrosilicates (Draine 2003), Mie theory temperatures; Kurucz-Lejeune photosphere
- 2016ApJ...828...46A: inclination derived from axis ratio assuming circular disk
- 2016ApJ...829....6W: Flux uncertainty dominated by 10% absolute flux scale
- 2016ApJ...829L..23B: p_down/p_up = (5M^2-1)/4
- 2016MNRAS.460.2933M: Astrosilicate, 3.5 g/cm3, Dohnanyi q=-3.5, amin 1.3 um, amax 1 cm, kappa_abs=1.1 cm2/g at 1.3 mm
- 2016MNRAS.462L.101A: circular disk structure, Keplerian rotation for moment-map check
- 2016MNRAS.462L.101A: circular disk, Gaussian representation
- 2017A&A...601A...7F: Central star not included; inclination and PA from SPHERE fit
- 2017A&A...603L...6H: CN and C15N co-spatial
- 2017A&A...605A..21C: All three H2CO lines are co-spatial; fluxes are lower limits
- 2017A&A...605A..21C: i = 44 deg, PA = 133 deg, d = 122 pc; OPR = 3 at T>=200 K and exponentially lower below; H2 collision partner; dust continuum optically thin
- 2017A&A...605A..21C: 12CO/C18O = 550 for converting to the CO abundance
- 2017ApJ...834..135T: dust emission traces star formation if dust temperature is constant
- 2017ApJ...836..223W: 70% silicate/30% graphite, grain size 5 nm to 3 mm, power-law -3.5, giving 2.25 cm2/g at 1.3 mm
- 2017ApJ...839...43O: LTE justified by densities above 1e6 cm-3
- 2017ApJ...840...23L: distance 145 pc
- 2017ApJ...840L..12S: M3 central star; distance 137 pc; McClure 2009 extinction law
- 2017ApJ...842....8M: Negligible vertical thickness (opening angle ~1 deg); temperature T ∝ r^-0.5; ω_p random 0 to 2π
- 2017ApJ...843..150F: d=122 pc, PA=312 deg, Mgas=0.09 Msun, XCO=1e-4 for CO, LTE, ring sigma=0.1 R, v_turb proportional to sound speed
- 2017ApJ...844..158S: Distances 131 pc (L1495), 119 pc (L1688), 140 pc Taurus average
- 2017ApJ...846L..26W: T = 20 K, kappa = 2.3 cm^2/g, distance 140 pc, optically thin
- 2017ApJ...846L..26W: Flared LTE vertically isothermal Keplerian disk; X_CO=1e-4; mu=2.37; inner radius 0.1 au; distance 140 pc with 20 pc uncertainty added in quadrature
- 2017ApJ...849...56A: LTE, vertically isothermal, same density power-law index for disk and envelope
- 2017ApJ...850...83F: Sersic n=1 exponential disk
- 2017ApJ...851...85B: Uniform opacity, a^-3.5 size distribution, max grain size 1 cm; Gaussian vertical structure
- 2017MNRAS.465.2595M: Astrosilicate/amorphous carbon/water ice 70/15/15%, Dohnanyi size distribution q=-3.5, 1 um-1 cm, kappa_abs=3.8 cm2/g at 0.88 mm
- 2017MNRAS.465.2595M: T(r)=42(r/150 AU)^-0.5 K
- 2017NatAs...1E.130Z: Emission arises from mid-plane or adjacent regions characterized by one temperature; C18O/13C18O constant
- 2018A&A...610A..24F: axisymmetry; flat priors
- 2018A&A...613A..34P: Gaussian uncorrelated noise
- 2018A&A...617A..23B: Gaussian intensity distribution; uncertainties assume reduced chi2 of 1
- 2018A&A...620A.152F: sources point-like in 0.60 arcsec mosaic
- 2018ApJ...852..122H: LTE; thin Keplerian disk; inclination 5 deg, PA 152 deg; mu=2.37; CO freezeout step function p=1e-6 below Tfrz
- 2018ApJ...854..130W: M*=1.7 Msun, d=103 pc, X_CO=1e-4, mu=2.37, inner radius 0.1 AU, Keplerian, vertically isothermal, single plane
- 2018ApJ...856..117F: Mdisk=0.05 Msun, CO/H2=1e-6, M*=0.7 Msun, d=54 pc, CO freeze-out at 19 K
- 2018ApJ...857...18S: Lynden-Bell & Pringle surface density, Ulrich envelope, 10% uncertainty on literature photometry and IRS points
- 2018ApJ...859..111H: Grain sizes 0.1 um to 3 mm, n(a)∝a^-3.5; 30% amorphous carbon/70% astrosilicate; kappa_1.3mm=2.2 cm2/g; Tstar=3859 K, R=0.8 Rsun; Rin 0.05 au; gas-to-dust 100
- 2018ApJ...859..131L: Distance 59.5 pc, PA 155 deg, inclination 8 deg, M*=0.8 Msun
- 2018ApJ...865...37M: Axisymmetric emission
- 2018ApJ...865...37M: Dust-to-gas ratio 0.01; distance 160 pc; inclination and PA fixed from step 3
- 2018ApJ...867..140L: Lens within 0.2 arcsec of HST optical centroid; no external shear
- 2018ApJ...868L...5K: Inclination and P.A. fixed to ellipse-fit values
- 2018ApJ...869...17L: Axisymmetry
- 2018ApJ...869...59W: kappa=0.899 cm2/g, Tdust=15 K, d=140 pc
- 2018ApJ...869...75M: Continuous surface density at R_halo; no vertical structure
- 2018ApJ...869L..48G: Axisymmetric emission; number of rings chosen by visual inspection
- 2018ApJ...869L..50P: Arc follows steady-state vortex prescription (Lyra & Lin 2013)
- 2018MNRAS.474.4347C: 10,000 K blackbody central source with L=Lbol; amax 3 mm, n(a)∝a^-3.5; kappa_abs(1.3mm)=2.2 cm2/g; viscous heating ignored
- 2018MNRAS.475.4924K: Dust size 10 um to 1 cm, q=11/6; 880 um opacity 0.17 m2/kg
- 2018MNRAS.481L..40S: Compact emission approximated by delta functions; Gaussians gave unstable results
- 2018Natur.553...51M: Lens is a singular isothermal ellipsoid
- 2018Sci...361.1016S: Singular isothermal ellipsoid lens
- 2019A&A...623A.124C: CH3OH and H2CO co-spatial
- 2019A&A...628A..95M: axisymmetric brightness profile, independent geometry per disk
- 2019A&A...628A.100D: gamma=5/3; flat LCDM Om=0.30, H0=70; kSZ neglected
- 2019A&A...628A.118B: intrinsic QSO continuum variation across spw0/spw1 less than 1%
- 2019A&A...632A..61G: Dust spectral index alpha ~3-4 in dust-dominated CND regions to estimate dust fraction at S1
- 2019AJ....158..162F: Blackbody grains, opacity 2.3 cm^2/g, constant surface density
- 2019ApJ...870...80L: Lens at z=0.9
- 2019ApJ...871....5T: Gaussian ring emission for beam deconvolution
- 2019ApJ...871..100H: Inclination 65 deg from Gaussian aspect ratio; center, PA fixed from 1.38 mm fit; grain size distribution n(a) ∝ a^-a_pow
- 2019ApJ...873...50D: Flat Planck LCDM: h=0.677, Om=0.308, OL=0.691
- 2019ApJ...873L..19B: Source unresolved since Re=0.23" << 2" beam
- 2019ApJ...875...55W: Sirius A is a point source (0.00602")
- 2019ApJ...875...87D: opacity 2.3 cm^2/g; dust in blackbody equilibrium; L*=0.09 Lsun; d=9.725 pc; vertically isothermal
- 2019ApJ...876..112R: circularly symmetric Gaussian profile
- 2019ApJ...877L..32M: Axisymmetric surface brightness I∝r^α with T∝r^-0.5
- 2019ApJ...881...84S: Dust blackbody temperature T ∝ r^-1/2
- 2019ApJ...882..160Q: Hyperfine levels in LTE; HCO+ collisional rates used for N2H+
- 2019ApJ...884...97L: constant component sizes with wavelength; concentric in most trials
- 2019MNRAS.484.1257M: Gaussian vertical profile; all particles share the same eccentricity and pericentre
- 2019MNRAS.485.2092C: Galaxies unresolved (PSF response)
- 2019MNRAS.485.2092C: Dust temperature as in z=2 MS template
- 2019NatAs...3..278K: CO orbits a point mass of 1.28 Msun
- 2020A&A...633A.114S: Azimuthally symmetric disk
- 2020A&A...633A.126B: Optically thin continuum; distance 192 pc
- 2020AJ....159..288M: Gaussian radial profile, FWHM = 0.2R
- 2020ApJ...889...59P: Star Teff 1e4 K, R*=5 Rsun; dust n(a)~a^-3.5 from 0.1 um to 3 mm; kappa_abs=2.2 cm2/g at 1.3 mm
- 2020ApJ...891...48H: Axisymmetric, geometrically thin
- 2020ApJ...891...48H: p = 3.5, a_max = 1 mm; vertically isothermal
- 2020ApJ...891...80M: Distance 9.725 pc
- 2020ApJ...894...76W: Stars are point sources; absolute flux uncertainty ~10%
- 2020ApJ...894...76W: Rayleigh-Jeans regime, S_nu ∝ nu^(2+beta)
- 2020ApJ...894...76W: Background source has constant flux
- 2020ApJ...895..109F: T_mid0 fixed from literature (DM Tau 19 K freeze-out at 70 au; MWC 480 18.8 K; V4046 Sgr 12 K); distances from Gaia DR2
- 2020ApJ...895..126H: Axisymmetric disks
- 2020ApJ...898...36L: axisymmetric profiles; Gaussian inner disk for DS Tau, tapered power law for GO/DL Tau, Gaussian rings
- 2020ApJ...898..146M: Optically thin; r^-0.5 temperature profile; constant dust opacity
- 2020ApJ...900....1F: Sersic index n=1
- 2020ApJ...901...74T: Disk model: axis ratio and PA fixed to Gaussian values
- 2020ApJ...902..141S: Distance 400 pc; axisymmetric models; Ulrich envelope
- 2021A&A...653A..46V: Disks azimuthally symmetric for inclination
- 2021AJ....161..271F: Dust: 70% astrosilicate, 15% amorphous carbon, 15% water ice; size power law -3.5, 1 um to 1 cm; Band 7 opacity 1.9 cm2/g
- 2021AJ....161..271F: Band 6 emission scaled from Band 7 via free alpha_mm
- 2021ApJ...908...54W: point-like source approximation valid
- 2023PSJ.....4..142C: T_cmb = 2.7 K; 5% flux scale error
- 2024A&A...685A..80Z: Clumps unresolved
- 2024A&A...686A.201N: geometrically thin disk for inclination lower limit
- 2024A&A...689A..85G: Dust mass: T_dust 20 K, wavelength 1.33 mm, kappa 2.254 cm2/g, distance 140±10 pc
- 2024A&A...689A.104D: azimuthally symmetric, geometrically thin, optically thick disk
- 2024A&A...689A.104D: axisymmetric; i=5.8 deg, PA=151.6 deg fixed
- 2024A&A...689A.299M: Negligible circular polarization
- 2024A&A...689A.317G: Continuum constant within each spectral window (spectral index 2, <1% variation)
- 2024ApJ...963..164R: Disks axisymmetric and geometrically thin; i = arccos(sigma_minor/sigma_major); distance 300 pc
- 2024ApJ...966...59S: Uniform priors; inclination prior ∝ sin i
- 2024ApJ...976..132H: Geometrically thin disk (flared surface for SO 897); posterior approximated as multivariate normal
- 2024NatAs...8..587F: Distance 140 pc
- 2024Natur.633..323V: top-hat disc profile
- 2025A&A...693A.151M: Gaussian radial profile; large grains behave as blackbodies
- 2025A&A...700A.165B: Galaxy unresolved at ACA resolution; GMCs co-spatial with star clusters and unresolved
- 2025ApJ...986L..11S: Back layer not farther from midplane than front layer
- 2025ApJ...986L..22R: Gas kinetic temperature 4 K
- 2025ApJ...986L..22R: H2CO-CO collision cross-section 5e-14 cm-2 (thermalization approximation)
- 2025ApJ...986L..22R: Opacities 0.17-0.467 m2/kg; dust at equilibrium temperature
- 2025ApJ...991..176W: Azimuthally symmetric Gaussian ring
- 2025MNRAS.543.2723P: Structured if R_peak > 0.05 arcsec, smooth otherwise; unresolved size upper limit 0.1 arcsec (14.5 au)
- 2025NatAs...9.1476C: Steady-state coma; electron density scaling x_ne=0.2; collisional cross-section with H2O 5e-14 cm^-2; T1=T2
- 2025NatAs...9.1476C: CH3OH/H2O constant over ALMA period, 20% added uncertainty
- 2026ApJ..1001..124M: Dust and gas thermally coupled; constant temperature in azimuth; albedo up to 0.8 (0.7 representative)


### Limitations the authors admit
- 2012ApJ...757..129R: Model parameters are not unique nor optimized; limited resolution
- 2013ApJ...762L..21M: Spectral index of central peak poorly constrained; inner belt interpretation needs higher resolution
- 2013ApJ...765L..14Q: Low S/N prevents constraining the vertical distribution; weak lines unresolved
- 2013ApJ...765L..14Q: 3-2 and 5-4 lines lie at the edge of the spectral window
- 2013ApJ...774...16R: Models are degenerate, not unique or optimal; systematic residuals at large radii
- 2013ApJ...774...16R: Band 7 sky frequency in SV measurement set incorrect
- 2013ApJ...777L..25M: Details of grain migration cannot be constrained by the data
- 2013Sci...341..630Q: Vertical disk structure is uncertain; vertical N2H+ boundaries fixed
- 2014A&A...562A..67G: Size measurement needs confirmation at higher resolution; sparse uv sampling
- 2014A&A...563A.136M: Mosaic fits require components small relative to the primary beam; no line-profile kinematics in the models
- 2014A&A...566A.112M: CO and C I column densities highly uncertain in SW wings and NE
- 2014A&A...566L...6M: NE covering factor poorly known (0.3<fc<1.0); NE H2(37)Cl+ not detected, only a lower limit on the ratio.
- 2014A&A...570L..14R: Only ~50% of extended flux recovered even with ACA; dynamic range limited to ~50
- 2014ApJ...783L..13P: Emission may be partly optically thick so asymmetries may not trace mass; masses are lower limits.
- 2014ApJ...787...42C: Dust mass errors exclude opacity uncertainty; upper limits treated inconsistently between samples; multiplicity unknown for most stars
- 2014ApJ...791...20R: Sample biased toward brightest disks; dust opacity absolute values unconstrained
- 2014ApJ...791L...6W: Disk size near largest recoverable scale; imaginary scatter at long baselines may indicate asymmetry needing higher resolution
- 2014ApJ...792L...2C: Lack of short baselines prevents ruling out additional H2CO sources with sizes >= 5 arcsec
- 2014ApJ...796...82Z: Equipartition estimates may be inaccurate for flat spectra; double-subtracted images unusable due to errors
- 2014ApJ...797...27F: Masses uncertain to factors of a few
- 2015A&A...577L...4V: Band 3 resolution too poor to confirm the hotspot there; 25 Oct Band 3 epoch affected by resolved calibrator
- 2015A&A...582L...4M: Metallicity of the foreground galaxy cannot be determined precisely; nucleosynthesis models have uncertain assumptions
- 2015A&A...583A..66H: Dust mass method has significant uncertainties; ages uncertain; binarity unconfirmed
- 2015ApJ...798...85P: Gas mass is a crude estimate, dominated by assumed isotopic ratios and temperature
- 2015ApJ...798..124R: Data cannot distinguish between gap and double power-law forms; dust opacity degenerate with surface density
- 2015ApJ...798L..23K: Veiling prevents accurate spectral type/mass determination of the companion
- 2015ApJ...808...36M: Mira A size and PA uncertainties dominated by systematics; disagreements with Vlemmings et al. 2015 in Band 3
- 2015ApJ...808..102K: Inner radii unreliable due to resolution and decoherence; constant beta assumed; kappa0 uncertain by factor two
- 2015ApJ...810..133I: Large Sigma_SFR uncertainties for ~0.1" sources; only 13 sources; redshifts mostly lower limits
- 2015ApJ...810L...7V: Optical depth at 680 GHz cannot be measured independently of temperature.
- 2015ApJ...811...39I: 150 pc resolution mixes AGN and SB contributions; CO(3-2) only partially covered
- 2015ApJ...811..124S: Systematic uncertainties in alpha_CO ~100% per method
- 2015ApJ...811L...3T: Gas masses depend on dust opacity, dust-to-gas ratio and temperature assumptions
- 2015ApJ...812L..23S: alpha_CO uncertain; metallicity of ionised gas may not represent molecular gas; AGN cannot be excluded
- 2015ApJ...813...99F: Parametric temperature structure cannot capture asymmetries; turbulence may be inflated; degeneracies between Tatm0 and Zq0, q and Rc
- 2015MNRAS.453L..83M: Log-normal is not a literal description of the true AGN distribution
- 2016A&A...586A..45S: Clumps are unresolved and the metallicity at the ALMA position is unknown
- 2016A&A...586A..99H: Cannot infer both surface density and opacity from single wavelength; errors are formal only
- 2016A&A...586L...1G: Missing short spacings and cloud structure on 7-10'' scales may bias temperatures; inner <40 au may be biased
- 2016A&A...586L...1G: Spectral index could not be constrained, degeneracy between temperature and surface density
- 2016A&A...589L...5M: Only one CF+ transition; k_f unmeasured so coefficient uncertain by factor 2-3
- 2016A&A...591A..73G: Continuum from HzRG and companion #10 contaminated by synchrotron, so SFRs are upper limits; single greybody is crude.
- 2016A&A...591A.108O: Large ALMA beam leaves outer slope poorly constrained; uncertainties should be treated carefully
- 2016A&A...593A..61M: Differential RM imaging with polarized fiducial element can be biased by up to ~30%.
- 2016A&A...595L...4L: Source size from three low-energy lines; higher-energy lines likely more compact, affecting column density; higher resolution needed
- 2016A&A...596A..75S: Herschel fluxes of the SMG derived through indirect procedure with unverified assumptions; Y-band scatters ~2 sigma from best fit
- 2016A&A...596A..88L: Detailed radiative transfer disk modelling and SED fitting beyond scope; mass estimates are simple
- 2016A&A...596A..88L: Dust mass highly sensitive to assumptions
- 2016ApJ...816...27S: Code is not entirely internally self-consistent; geometry of HD 377/8907 highly uncertain
- 2016ApJ...818...45S: Putative 13-AU belt needs deeper data; SED models degenerate due to lack of Rayleigh-Jeans constraints
- 2016ApJ...818..156C: Mass precision limited by face-on geometry and cloud contamination
- 2016ApJ...818L..16Z: Deconvolution solution is not unique
- 2016ApJ...819..102V: Sample biased toward far-IR bright, larger-mass disks; SED fitting insensitive to geometry; opacity uncertainties affect masses
- 2016ApJ...823L..18H: Thermal vs non-thermal desorption contributions not constrained; narrow optically thick dust rings need higher resolution
- 2016ApJ...828...25L: Low resolution prevents breaking R_Out/p degeneracy and resolving widths
- 2016ApJ...828...46A: Gas masses depend inversely on assumed [CO]/[H2] and isotopologue ratios; CO depletion would raise gas masses
- 2016ApJ...829....6W: CO mass assumes optically thin LTE and could be larger by a factor of a few or more
- 2016ApJ...829....6W: Debris mass depends strongly on assumed size distribution, density, albedo
- 2016ApJ...829L..23B: Short-spacing problem makes Mach number anti-correlated with pressure normalization
- 2016ApJ...829L..23B: Pre-shock temperature unconstrained in Chandra data
- 2016ApJ...833L...6C: Large structures (>~12") undersampled in Band 7; could matter for dust
- 2016ApJ...833L...6C: Dust mass may be underestimated since warm dust dominates SED peak; LMC X_CO may overestimate gas
- 2016MNRAS.458L..29C: Dust mass relies on ISM grain size distribution assumption that may not hold for large-grain-dominated disc; detailed modelling deferred
- 2016MNRAS.458L..29C: Red-shifted CO side affected by cloud filtering
- 2016MNRAS.459.4518H: Single SED point, grain size and surface density unconstrained; dust mass relies on grain assumptions
- 2016MNRAS.460.2933M: Dust mass depends strongly on assumed composition and amax; h not fully constrained
- 2016MNRAS.462L.101A: Inclinations reflect bulk geometry; uncertainties exclude systematics; small sample
- 2016Natur.535..258C: Temperature is an extrapolation from the optically thick surface and may underestimate midplane snow-line temperature; tau0 and Ts degenerate when optically thin
- 2016PASJ...68...88K: Missing flux on large scales due to no Total Power Array
- 2017A&A...597A..32V: Limited resolution cannot distinguish gap from ring
- 2017A&A...597A..41G: Possible unaccounted systematics at 5-10% level; non-uniform sensitivity in two mosaics
- 2017A&A...599A.134S: Sample likely biased against heavily obscured H-dropout galaxies
- 2017A&A...601A...7F: The disk is barely resolved by ALMA, giving a degenerate r0 and alpha_out.
- 2017A&A...602L..10O: Limited resolution smears fine structures and reduces contrast; spectral index errors may be underestimated
- 2017A&A...603L...6H: CN and C15N co-spatiality assumption hard to assess; C15N map not used
- 2017A&A...603L...6H: Robust CN column density needs self-consistent modelling; 2D radiative transfer needed
- 2017A&A...605A..21C: Inner 50 AU cannot be modeled due to low resolution and dust optical depth
- 2017A&A...605A..21C: Matched-filter fluxes are only lower limits
- 2017A&A...605A..21C: Parameterized models include no chemistry; formation route cannot be distinguished
- 2017A&A...605A..28D: Weak bimodal high-velocity emission not reproduced; 12CO 9-8 peak ~20% low; LVG may not apply to torus
- 2017A&A...606A.109M: Covering factor unresolved; apparent opacities give lower limits for column densities
- 2017A&A...607A..55V: Dust temperature is likely overestimated so dust mass is a lower limit
- 2017A&A...608A..96L: A more efficient thermalization route may be missed.
- 2017AJ....153..233F: HCN LTE model significantly fainter than LIME model; vertical structure unresolved
- 2017AJ....153..233F: CO heavily contaminated by cloud, blue side excluded
- 2017AJ....153..240A: Many upper limits, uncertain stellar properties; gas masses could be underestimated by carbon depletion
- 2017AJ....154...11H: Radio noise value is approximate; ALMA compact-configuration uncertainty may be underestimated
- 2017AJ....154..225S: Disk width only resolved by ~1.7 beams so density distribution and star-disk offset cannot be determined
- 2017AJ....154..225S: Bright source cannot be cleanly separated from the disk
- 2017ApJ...834..135T: High-resolution maps might miss extended, diffuse components
- 2017ApJ...834..178Y: Only three protostars with M*<0.1 Msun; larger low-mass sample required
- 2017ApJ...834..178Y: Masses and disk radii of IRAS 15398 and IRAS 16253 are lower and upper limits
- 2017ApJ...836..223W: Orbit and geometry results are preliminary because many orbital solutions share similar chi^2
- 2017ApJ...836..223W: Accretion rate for B is a lower limit due to unknown extinction
- 2017ApJ...839...43O: Disk vertical temperature structure highly uncertain; abundances not accurate; toy models leave >5 sigma residuals
- 2017ApJ...839...99P: Gas masses not estimated due to foreground absorption
- 2017ApJ...839...99P: Only real visibilities fit, so significance of asymmetry residuals unclear
- 2017ApJ...840...23L: Band 6 flux uncertain, precluding spectral index analysis
- 2017ApJ...840L..12S: Envelope mass and radius are degenerate; data cannot distinguish compact low-mass from large massive envelopes
- 2017ApJ...841L..25T: Not clear that starburst alpha_CO holds for entire galaxies
- 2017ApJ...842....8M: Resolution (~10 AU) prevents constraints on edge sharpness; Δa and e_p degenerate; large uncertainty on ω from inclination degeneracy
- 2017ApJ...842....8M: 2D model ignores vertical structure, which could loosen width constraints
- 2017ApJ...843...18V: Modest angular resolution is a major limitation
- 2017ApJ...843..150F: Parametric temperature/density structure, degeneracies with abundance, dust-to-gas ratio and 18O abundance; turbulence is a disk-averaged intensity-weighted value
- 2017ApJ...844..158S: Cloud contamination limits CO and CN usability; Teff uncertainties limit comparison
- 2017ApJ...845..138S: Inclination derived from only two successful rings; real uncertainty may be much larger
- 2017ApJ...845..170B: Gas masses subject to large systematic uncertainty from unknown alpha_CO in ETGs
- 2017ApJ...845..170B: Beam smearing contributes to observed line widths
- 2017ApJ...846..108C: CO detection is only ~3 sigma peak SNR so 2D CO kinematics and central detail are limited
- 2017ApJ...846..108C: ALESS67.2 nature inconclusive
- 2017ApJ...846L..14S: Factor of two systematic uncertainty from CO excitation and alpha_CO; very small sample
- 2017ApJ...846L..26W: Single optically thick CO line likely underestimates gas mass
- 2017ApJ...849...56A: Resolution not high enough to resolve vertical structures; temperature profile fixed and vertically isothermal; abundance constraints weak
- 2017ApJ...850...54C: Missing short spacings; about half of expected flux recovered
- 2017ApJ...850...83F: Sample not complete at fixed stellar mass
- 2017ApJ...850...83F: Size measurement unreliable for compact/faint sources in low-resolution maps
- 2017ApJ...851...85B: Single-wavelength data cannot constrain dust opacity; CO likely optically thick so gas mass unconstrained
- 2017ApJ...851L..23C: Gaps only partially resolved, degeneracy between width and depth
- 2017ApJ...851L..23C: Other explanations (MHD, instabilities) remain possible
- 2017MNRAS.465.2595M: Missing short baselines; no ACA; CO detection tentative and morphology inconsistent with simple Keplerian ring

### Settings cards flag as needed but not stated
- casa version: 30
- self-calibration solution intervals: 12
- casa version and pipeline version: 12
- uvmodelfit starting parameters: 10
- image size and cell size: 10
- flux calibrator and flux scale uncertainty: 8
- line-free channels for uvcontsub: 8
- line-free channels for continuum subtraction: 7
- self-calibration solution intervals and number of iterations: 7
- line-free channels used for continuum subtraction: 6
- self-calibration solution intervals and reference antenna: 6
- line-free channels used for uvcontsub: 6
- casa/pipeline version: 5
- source coordinates: 5
- line-free channels and continuum subtraction method: 5
- line-free channels used for continuum: 4
- line-free channel selection for continuum: 4
- briggs robust value: 4
- line-free channel ranges: 4
- clean mask, threshold, cell and image size: 4
- self-calibration solution intervals and number of rounds: 3
- cell size and image size: 3
- self-calibration solution interval: 3
- self-calibration solution interval and reference antenna: 3
- primary beam correction details: 3
- flux calibrators and flux scale uncertainty: 3
- line-free channels and uvcontsub fit order: 3
- pipeline version: 3
- flux scale uncertainty: 2
- continuum channel selection / line-free channels: 2
- line-free channels for continuum: 2
- image size, cell size, clean masks and thresholds: 2
- casa version and calibration pipeline/manual details: 2
- distance adopted: 2
- line-free channels and continuum subtraction details: 2
- image size, cell size, and clean parameters: 2
- clean threshold, mask, image size and cell size: 2
- mcmc walkers, steps, burn-in and priors: 2
- primary-beam correction and flux-scale uncertainty: 2
- rest frequencies of lines: 2

## Paper excerpts (40 of 278, chosen for detail and spread over fields/years)

### 2017A&A...605A..21C: Increased H<SUB>2</SUB>CO production in the outer disk around HD 163296 (2017; protoplanetary_disks, astrochemistry; observational_alma_primary)
- question: What is the distribution of H2CO in the HD 163296 disk, and what does it say about gas-phase versus solid-phase (grain-surface) formation routes?
- step 4: Detect weak lines by matched filter
  - method: uv-plane cross-correlation of weak-line visibilities with a template from the tapered 3_03-2_02 cube sampled with vis_sample; flux ratio of peak responses gives weak-line fluxes [3.1.1 Matched filter detections: "Image channels showing H$_2$CO emission (1.6–10 km s$^{-1}$) were sampled in the $uv$ plane using the PYTHON `vis_sample` routine"]
  - software: vis_sample, Python
  - parameter: template 1'' beam via uv taper, 0.084 km/s channels [3.1.1 Matched filter detections: "using a $uv$ taper to achieve a 1$\ensuremath{''}$ synthesized beam"]
  - assumption: All three H2CO lines are co-spatial; fluxes are lower limits [3.1.1 Matched filter detections: "Under the assumption that all three observed H$_2$CO lines are co-spatial, the $\sigma$-ratio can be used to estimate the weaker line fluxes"]
  - validation: Detections at 4.5 and 5 sigma, with sigma from emission-free channels [3.1.1 Matched filter detections: "The inset reveals the 4.5$\sigma$ and 5$\sigma$ detections of H$_2$CO 3$_{22}$–2$_{21}$ and H$_2$CO 3$_{21}$–2$_{20}$, respectively"]
- step 5: Model line emission with parameterized abundances
  - method: LIME non-LTE radiative transfer on Mathews2013 disk model; four abundance parameterizations (low-temperature, power-law, temperature step, radial step); synthetic visibilities via vis_sample; chi2 minimization on normalized visibilities [3.2 Modeling H2CO and C18O emission: "Goodness of fit for each model was determined by $\chi^2$ minimization between the normalized visibilities of the model and the visibilities of the data."]
  - software: LIME, vis_sample
  - parameter: R_in = 50 AU for H2CO; Tc 12–36 K in 2 K steps; Rc 210–410 AU (H2CO), 70–350 AU (C18O) in 20 AU steps; X1/X2 0.001–10 (0.1–1000 for C18O) [3.2.3 Temperature step-abundance model: "The change-over temperature $T_{\rm c}$ was tested in the range 12 – 36 K in steps of 2 K."]
  - parameter: Reference abundances 1e-12 (H2CO), 1e-7 (C18O) [3.2 Modeling H2CO and C18O emission: "The H$_2$CO reference abundance was set to $X = 1.0 \ \times \ 10^{-12}$."]
  - assumption: i = 44 deg, PA = 133 deg, d = 122 pc; OPR = 3 at T>=200 K and exponentially lower below; H2 collision partner; dust continuum optically thin [3.2 Modeling H2CO and C18O emission: "The disk inclination, position angle, and distance are set to $i$ = 44.0$^{\circ}$, P.A. = 133.0$^{\circ}$, and $d$ = 122 pc."]
  - fitting: Grid search with chi2 minimization on visibilities; reduced chi2 [Table 2: "$\chi^2$ values are reduced by the number of points and free parameters in each model."]
  - validation: Compare model and data radial profiles, spectra, integrated intensity maps and residuals [3.2.5 H2CO and C18O abundance: "Integrated intensity maps of the best-fit models were compared to integrated intensity maps of observed H$_2$CO 3$_{03}$–2$_{02}$ and C$^{18}$O 2–1 data."]
- step 6: Fit absolute abundances
  - method: Scale normalized best-fit model to total flux (vector-averaged visibilities at baselines <30 m), then vary X1 in LIME with fixed X1/X2 and Rc, chi2 minimization; 3 sigma radial-profile error bars give ranges [3.2 Modeling H2CO and C18O emission: "To determine the total flux, we took a vector average of visibilities with baselines $<$30 m and integrated over all channels containing emission."]
  - software: LIME, vis_sample
  - parameter: H2CO X1 grid [1,2,3,4,5]e-12 with Rc = 270 AU [3.2.5 H2CO and C18O abundance: "H$_2$CO models had $R_{c}$ = 270 AU and $X_1$ = \[1.0, 2.0, 3.0, 4.0, 5.0\] $\times \ 10^{-12}$."]
  - assumption: 12CO/C18O = 550 for converting to the CO abundance [3.2.5 H2CO and C18O abundance: "assuming $^{12}$CO/C$^{18}$O = 550"]
  - fitting: chi2 minimization on visibilities [3.2 Modeling H2CO and C18O emission: "using $\chi^2$ minimization on the visibilities."]
  - validation: Residual maps; C18O residual above 3 sigma in the central region [3.2.5 H2CO and C18O abundance: "though the best-fit C$^{18}$O has residual emission above the 3$\sigma$ in the central part of the disk."]
- result: Matched-filter detection significance of 3_22 and 3_21 = 4.5 and 5 ± not stated sigma [3.1.1 Matched filter detections: "The inset reveals the 4.5$\sigma$ and 5$\sigma$ detections of H$_2$CO 3$_{22}$–2$_{21}$ and H$_2$CO 3$_{21}$–2$_{20}$, respectively"]
- result: Best-fit H2CO radial step change-over radius Rc = 270 ± 20 AU [3.2.4 Radial step-abundance model: "Best-fit parameters are a change-over radius $R_{\rm c}$ = 270$\pm$20 AU and an abundance ratio $X_1/X_2 = 0.5$."]
- result: H2CO X1/X2 = 0.5 ± not stated dimensionless [3.2.4 Radial step-abundance model: "Best-fit parameters are a change-over radius $R_{\rm c}$ = 270$\pm$20 AU and an abundance ratio $X_1/X_2 = 0.5$."]
- result: H2CO inner abundance X1 = 2-5e-12 (best fit 4.0e-12) ± range from 3 sigma error bars relative to H2 [3.2.5 H2CO and C18O abundance: "The best-fit fractional abundances were $X_1 = 4.0 \times 10^{-12}$ and $X_2 = 8.0 \times 10^{-12}$."]
- result: C18O radial step Rc and depletion factor = 290 AU; factor 10 ± 20 AU AU [3.2.4 Radial step-abundance model: "Best-fit C$^{18}$O models have $R_{\rm c}$ = 290$\pm$20 AU and $X_1/X_2 =$10"]
- result: C18O inner abundance X1 = 4-12e-8 (best fit 5.0e-8) ± range from 3 sigma error bars relative to H2 [3.2.5 H2CO and C18O abundance: "$X_1 = 4\!-\!12 \times 10^{-8}$ and $X_2 = 4\!-\!12 \times 10^{-9}$ for C$^{18}$O"]
- result: H2CO low-temperature model threshold T = 24 ± 2 K [3.2.1 Low-temperature abundance model: "The best fit for the normalized low-temperature model for H$_2$CO has a threshold temperature of 24$\pm$2 K"]
- result: H2CO temperature step Tc = 16 ± 2 K [3.2.3 Temperature step-abundance model: "The best-fit H$_2$CO model has a change-over temperature $T_{\rm c} = 16 \pm 2$ K"]
- result: C18O temperature step Tc = 32 ± 2 K [3.2.3 Temperature step-abundance model: "C$^{18}$O is best fit by a change-over temperature $T_{\rm c} = 32 \pm 2$ K"]
- limitation (authors): Inner 50 AU cannot be modeled due to low resolution and dust optical depth [3.2 Modeling H2CO and C18O emission: "The inner region ($<$50 AU) cannot be properly modeled here due to the low resolution of the observations"]
- limitation (authors): Matched-filter fluxes are only lower limits [3.1.1 Matched filter detections: "The response of the template is limited by how well it spatially matches the emission, thus making the derived line fluxes lower limits."]
- limitation (authors): Parameterized models include no chemistry; formation route cannot be distinguished [4 Discussion: "It is difficult to distinguish which formation route is responsible for this modest increase in abundance."]
- not stated (card): Line-free channel ranges used for continuum subtraction and self-calibration; How the matched-filter response was normalized and the exact uv taper; Exact LIME settings (number of grid points, photons, resolution); Gas-to-dust ratio and dust opacity details inherited from the Mathews2013 model; Whether CASA version was specified (not given); Exact chi2 definition and uv binning for the model-data…

### 2017ApJ...850...83F: Demonstrating a New Census of Infrared Galaxies with ALMA (DANCING-ALMA). I. FIR Size and Luminosity Relation at z = 0-6 Revealed with 1034 ALMA Sources (2017; high_z_galaxies; archival_reuse)
- question: What is the relation between rest-frame FIR effective radius and FIR luminosity of ALMA-detected dusty galaxies at z=0-6, and how does it evolve with redshift and compare with UV/optical sizes?
- step 3: Measure flux and size in uv plane
  - method: uvmultifit with symmetric exponential disk (n=1), positions fixed, imfit values as initial guesses; Re=0.826 FWHM; visual flagging [3.2 Flux and Size Measurement: "The fitting result of the FWHM values are converted to the $R_{\rm e}$ values via the relation of $R_{\rm e}=0.826\,{\rm FWHM}$ in the case of $n=1$"]
  - software: uvmultifit
  - assumption: Sersic n=1 exponential disk [3.2 Flux and Size Measurement: "Here we adopt a symmetric exponential disk model."]
  - fitting: uv-visibility fitting; flag=0 reliable results only [3.2 Flux and Size Measurement: "We use only the results with flag = 0 in the following analyses in this paper."]
  - validation: Compared with previous ALMA flux/size measurements [3.4: "Our size measurements are also consistent with the majority of the previous ALMA results within the $\sim$ 1$-$2 $\sigma$ errors"]
- step 4: Correct biases with Monte-Carlo simulations
  - method: Inject 26,600 artificial sources into uv data of 10 representative maps; fit linear input-output relations in 3 SNR bins [3.3 Simulation and Correction: "we create $26,600$ artificial sources with the uniform distribution of the total fluxes in the $5\sigma_{\rm f}-45\sigma_{\rm f}$ levels"]
  - software: uvmultifit
  - parameter: sizes 0.04''-3.0''; random positions within 10'' radius; SNR bins 5-10, 10-20, 20-30 [3.3 Simulation and Correction: "we divide our simulation results into three bins with the output peak signal to noise ratio (SNR) of 5$-$10, 10$-$20, and 20$-$30."]
  - fitting: S_in = A0 S_out + A1; Re_in = B0 Re_out + B1 [3.3 Simulation and Correction: "$A_{0}, A_{1}, B_{0},$ and $B_{1}$ are the free parameters."]
  - validation: Selection completeness and measurement completeness maps; completeness thresholds [3.5: "we define the completeness threshold in each sub-dataset."]
- limitation (authors): Sample not complete at fixed stellar mass [3.7: "our ALMA sources are not the complete sample at a fixed $M_{\rm star}$."]
- limitation (authors): Size measurement unreliable for compact/faint sources in low-resolution maps [3.5: "We cannot obtain the reliable size measurements for the compact and/or faint sources in the low-resolution observations."]
- not stated (card): Which exact archival projects/maps entered the sample (full 1627-map table is only online); Cell size and image size for CLEAN; Line-free channel ranges and how line channels were identified in the three line projects; uvmultifit initial-value and fit settings details; Perturbation-method and power-law fit algorithm details (fit method, priors); Completeness threshold values per sub-dataset; Phot…

### 2017MNRAS.465.2595M: ALMA observations of the η Corvi debris disc: inward scattering of CO-rich exocomets by a chain of 3-30 M<SUB>⊕</SUB> planets? (2017; debris_disks; observational_alma_primary)
- question: What is the structure of the eta Corvi outer belt, and does it favour an LHB-like instability or a stable planetary configuration feeding the hot dust? Is CO gas present, and what planets could sculpt the belt?
- step 4: Fit parametric disc models to visibilities
  - method: Four models (Gaussian belt, self-stirred, LHB/double power law, eccentric belt) with RADMC-3D images, simulated visibilities, MCMC [3 Disc modelling: "A Bayesian approach is used to constrain the different parameters of the disc models (details below), sampling the parameter space to recover the posterior distribution"]
  - software: RADMC-3D, emcee, CASA, uvsim
  - parameter: Visibilities averaged to 3 min and 2 GHz bins; 300-1000 steps, 50-180 walkers [3 Disc modelling: "We run emcee for 300-1000 steps using 50-180 *walkers*, depending on the model"]
  - assumption: Astrosilicate/amorphous carbon/water ice 70/15/15%, Dohnanyi size distribution q=-3.5, 1 um-1 cm, kappa_abs=3.8 cm2/g at 0.88 mm [3 Disc modelling: "This leads to a mass-weighted absorption opacity $\kappa_{\mathrm{abs}}=3.8$ cm$^{2}$ g$^{-1}$ at 0.88 mm"]
  - fitting: emcee; likelihood proportional to exp(-chi2/2); uniform priors; weights from statwt [3 Disc modelling: "The likelihood function is defined proportional to $\exp(-\chi^2/2)$"]
  - validation: Model comparison with BIC; residual dirty maps [3.5 Model comparison: "We find that the belt model’s BIC is lower by $\sim40$ compared to the self-stirred best model’s BIC, and lower by 20 compared to the double power law model."]
- step 5: Constrain hidden cavity emission
  - method: Analytic 3-sigma limit plus added power-law second component fit to visibilities [3.6: "we added a second component to the simple belt model described in Sec. 3.1 and we fit this to the observed visibilities"]
  - software: RADMC-3D, emcee
  - assumption: T(r)=42(r/150 AU)^-0.5 K [3.6: "We also assumed $T(r)=42 (r/150 \ \mathrm{AU})^{-0.5}$ K"]
  - fitting: alpha free between -5 and 5 [3.6: "where we leave $\alpha$ as a free parameter that can vary between -5 and 5"]
- result: Belt mean radius = 152 ± 3 AU [Table 1: "$r_{0}$ \[AU\] | $152\pm3$"]
- result: Belt radial FWHM = 46 ± 5 AU [Table 1: "$\Delta r$ \[AU\] | $46\pm5$"]
- result: Inclination = 35 ± 2 deg [Table 1: "$i$ \[$^{\circ}$\] | $35\pm2$"]
- result: Position angle = 117 ± 4 deg [Table 1: "PA \[$^{\circ}$\] | $117\pm4$"]
- result: Belt model total flux = 13.3 ± 1.0 mJy [3.1: "The total flux of the best fit model is $13.3\pm1.0$ mJy"]
- result: Belt dust mass = 0.014 ± 0.001 Mearth [Table 1: "$M_{d}$ \[M$_{\oplus}$\] | $0.014\pm0.001$"]
- result: Double power law inner slope = 6.2 ± +2.0/-1.3 dimensionless [3.3: "We find $\alpha_\mathrm{in}=6.2^{+2.0}_{-1.3}$, with a $3\sigma$ lower limit of 3.3."]
- result: Belt eccentricity 99.7% upper limit = 0.05 ± not stated dimensionless [3.4 Eccentric belt: "we derive a 99.7% upper limit of 0.05"]
- result: Hidden cavity dust mass limit (3 sigma) = 2.7e-3 ± not stated Mearth [3.6: "We find an $3\sigma$ upper limit of $2.7\times10^{-3}$ M$_\oplus$ for $M_{d2}$ and 3.2 mJy"]
- limitation (authors): Missing short baselines; no ACA; CO detection tentative and morphology inconsistent with simple Keplerian ring [2.1 Continuum emission: "This shows the importance of having a complete uv-coverage that includes baselines that can capture the angular size of the observed source"]
- not stated (card): Number of CLEAN iterations, threshold and mask definitions; Exact line-free channels and velocity ranges for uvcontsub; Whether pipeline or manual calibration was used and CASA calibration version; Flux calibrator models used per execution; Exact fixvis phase-centre offsets per execution; Grid size and resolution of the RADMC-3D model; Prior ranges for each parameter; uvsim tool configuration for…

### 2014ApJ...791L...6W: ALMA Hints at the Presence of two Companions in the Disk around HD 100546 (2014; protoplanetary_disks; observational_alma_primary)
- question: What are the gas and dust structures of the HD 100546 disk at (sub)mm wavelengths, and do they indicate companions or a protoplanet?
- step 2: Fit disk geometry
  - method: uvmodelfit elliptical disk to continuum visibilities [RESULTS: "the CASA task `uvmodelfit` was used to fit the continuum visibilities assuming the emission arises from a elliptical disk."]
  - software: CASA uvmodelfit
  - validation: agreement with previous observations [RESULTS: "in excellent agreement with previous observations"]
- step 3: Fit radial structure in visibility domain
  - method: Bin deprojected visibilities (10 kλ); grid fit of power-law ring, then Gaussian compact ring plus flat extended ring; chi2 grid with Bayesian errors [RESULTS: "A small step size of 0.5 AU was chosen to allow quantification of the errors via Bayesian inference."]
  - parameter: fluxes fixed at 0.962 and 0.024 Jy (302 GHz), 1.190 and 0.048 Jy (346 GHz) [RESULTS: "the total flux contribution from the compact and extended components were fixed at 0.962 and 0.024 Jy at 302 GHz"]
  - assumption: Circular symmetry [RESULTS: "Without any further knowledge on the structure we assume a circular-symmetric surface-brightness distribution."]
  - fitting: chi2 grid search [RESULTS: "A low-resolution grid was run (5 AU) to determine the location of the global minimum in the $\chi^2$ value."]
  - validation: Residual images with identical uv coverage [RESULTS: "The model residuals were imaged using an identical $uv$ coverage as the observations"]
- result: Inclination = 44 ± 3 deg [RESULTS: "inclination of 44$\pm$3°and a position angle"]
- result: Position angle = 146 ± 4 deg [RESULTS: "position angle (measured East from North) of 146$\pm$4°"]
- result: Visibility null = 290 ± not stated kλ [RESULTS: "there is a zero crossing (null) at 290 k$\lambda$"]
- result: Outer ring centre = 190 ± 3 AU [RESULTS: "an outer ring with a width of 75$\pm$3 AU centered at 190$\pm$3 AU"]
- result: Inner ring peak / FWHM = 26 / 21 ± not stated AU [RESULTS: "a compact ring with a peak brightness at 26 AU and a FWHM of 21 AU"]
- limitation (authors): Disk size near largest recoverable scale; imaginary scatter at long baselines may indicate asymmetry needing higher resolution [RESULTS: "Higher spatial resolution observations are needed to confirm any asymmetry at small spatial scales."]
- not stated (card): CLEAN masks, number of iterations and thresholds, cell and image size; Line-free channels used for uvcontsub; Self-calibration solution intervals and number of rounds; Exact visibility-fitting chi2 and Bayesian error procedure; Dust evolution code and numerical set-up (grid, gas surface density profile); Which execution calibrators apply to which spectral windows

### 2019A&A...632A..61G: ALMA images the many faces of the <ASTROBJ>NGC 1068</ASTROBJ> torus and its surroundings (2019; nearby_galaxies, agn_and_quasars; observational_alma_primary)
- question: How is the torus of NGC 1068 structured and connected to the host disk, and how does AGN feedback affect the molecular gas kinematics from torus to CND scales?
- step 1: Image cubes and continuum
  - method: CASA calibration, uv-tables exported to GILDAS; UV-MAP imaging with robust 1 (MSR) and 0.1 (HSR); uv-plane continuum subtraction [2.2 Band 7 data: "We obtain two sets of angular resolutions by changing in the `GILDAS` task `UV-MAP` the robust parameter ($b$) from 1"]
  - software: CASA, GILDAS
  - parameter: 20 km/s channels [2.2 Band 7 data: "The line data cubes were binned to a common frequency resolution of 23.1 MHz (equivalent to $\sim$20 km s$^{-1}$ in Band 7)."]
  - validation: Compared CND fluxes with GB14 CO(3-2) and Krips CO(2-1) maps to check missing flux [2.3 Band 6 data: "530 Jy km s$^{-1}$ (cite: Kri11) $\simeq$ 580 Jy km s$^{-1}$ (this work)"]
- step 2: Continuum position and spectral index
  - method: UV-FIT for AGN position; spectral index maps from 229.7, 344.5, 694 GHz at common 0.11'' aperture [3 Continuum maps: "derived for a common aperture size of $0.11\ensuremath{''}\times0.11\ensuremath{''}$ ($8$ pc$~\times$ 8 pc)"]
  - software: GILDAS
  - assumption: Dust spectral index alpha ~3-4 in dust-dominated CND regions to estimate dust fraction at S1 [3 Continuum maps: "We used the spectral index values measured in the CND regions dominated by dust emission ($\alpha\simeq$ 3–4) to derive the fraction of emission at 871 $\mu$m"]
- limitation (authors): Models are axisymmetric and chi2 values are large [7.2: "the goodness-of-fit parameters are admittedly large in either case ($\geq$4)"]
- not stated (card): CLEAN parameters in GILDAS (niter, threshold, masks, cell and image size); Line-free channel selection for continuum; Calibrator names and CASA version; Details of 3DBarolo configuration (ring widths, masks, normalization, thresholds, fixed vs free parameters per step); Exact kinemetry settings (harmonic order choice, ring spacing, errors); Torus model code and parameter grid, pixel counts for ch…

### 2025ApJ...986L..11S: Hints of Disk Substructure in the First Brown Dwarf with a Dynamical Mass Constraint (2025; protoplanetary_disks, star_formation; observational_alma_primary)
- question: Does the disk of the brown dwarf 2M0444 show Keplerian rotation (giving a dynamical mass), radial drift, and dust substructure at high resolution?
- step 3: Dynamical mass from 12CO visibility fitting
  - method: Channel-by-channel visibilities, 30 channels, two emitting layers (front and back), MCMC [3.2 Fitting of the visibilities for the…: "The brightness model cube considered two emitting layers to recreate the $^{12}$CO emission: A front and back emitting layer, each one with its own independent height and temperature profile."]
  - parameter: 192 walkers, flat priors, converged after ~10^4 steps, then 10^4 more [3.2 Fitting of the visibilities for the…: "with 192 walkers (equal to eight times the number of free parameters), and a flat prior for all the parameters"]
  - assumption: Back layer not farther from midplane than front layer [3.2 Fitting of the visibilities for the…: "The only additional condition imposed on the model was that the back layer could not be at a larger distance from the midplane than the front layer."]
  - fitting: MCMC, flat priors; uncertainties from walker dispersion (3σ for mass) [3.2 Fitting of the visibilities for the…: "The uncertainty for each parameter is measured from the dispersion of the walkers."]
  - validation: Residual image after model subtraction; geometry consistent with continuum [3.2 Fitting of the visibilities for the…: "we find consistent solutions of inclination and position angle to those from the continuum"]
- step 4: Parametric continuum fit for geometry
  - method: After uvsub of external source, galario fit of central Gaussian plus Gaussian ring, MCMC [3.3 Fitting of the visibilities for the…: "we applied the code `galario`(cite: Tazzari2018) to perform a parametric fit which was solely aimed at retrieving the disk’s geometrical parameters"]
  - software: galario, emcee, CASA
  - parameter: 100 walkers, 10000 steps [galario fit: "results of the `galario` fit run using 100 walkers and 10000 steps"]
  - fitting: chi2 minimisation, emcee MCMC, uniform priors, f0 and f1 sampled logarithmically [3.3 Fitting of the visibilities for the…: "Uniform priors were employed, with the intensity normalization factors $f0$ and $f1$ sampled logarithmically."]
- step 5: Non-parametric radial profile
  - method: frank Fourier-Bessel fit of deprojected visibilities with galario geometry; 500-run bootstrap for uncertainties [3.3 Fitting of the visibilities for the…: "We ran the `frank` fit 500 times, randomly varying the geometrical parameters ($i$, PA, $\Delta$RA, and $\Delta$Dec)"]
  - software: frankenstein
  - parameter: alpha=1.20, w_smooth=1e-3, N=400, Rmax=4 Rout [3.3 Fitting of the visibilities for the…: "we selected conservative values of $\alpha=1.20$ and $w_\mathrm{smooth}=10^{-3}$, along with $N = 400$ and $R_\mathrm{max} = 4\,R_\mathrm{out}$"]
  - fitting: Gaussian-process regularised Fourier-Bessel series; 1 deg sigma on i and PA, 1/3 beam major axis on offsets [3.3 Fitting of the visibilities for the…: "We used a standard deviation of 1 deg for $i$ and PA, and 1/3 of the synthesized beam’s major axis for the positional offsets"]
  - validation: Model comparison: Gaussian vs Gaussian+ring with AIC and BIC; frank log-likelihood difference [Statistical comparison of dust substruc…: "The Gaussian+Ring model is strongly favored by the AIC ($\Delta\text{AIC}=-24.4$)"]
- step 6: Measure gas and dust disk sizes
  - method: Cumulative flux radii R68, R90, R95 from image plane and visibility fits [3.4 Size of disk: gas vs dust: "We defined the radii $R_{68}$, $R_{90}$, and $R_{95}$ as the distances within which 68%, 90%, and 95% of the total flux is enclosed, respectively."]
  - validation: Compared image plane vs visibility plane [Size of disk: gas vs dust: "with gas-to-dust size ratios ranging from 6 to 8 in the visibilities, compared to 2 to 2.7 in the image plane"]
- result: Dynamical mass (12CO visibility fit) = 0.092 ± +0.019/-0.007 (3σ) Msun [3.2 Fitting of the visibilities for the…: "we obtain $M_\star=0.092_{-0.007}^{+0.019}$ M$_{\odot}$"]
- result: Disk inclination (galario) = 49.9 ± ±0.5 deg [Table 1: "| Inclination | $49.9_{-0.5}^{+0.5}$ deg |"]
- result: Gap radius = 98.1 ± +4.2/-8.4 mas [abstract: "our best fit shows a gap and a ring at 98.1$^{+4.2}_{-8.4}$ mas ($\sim$14 au) and 116.0$^{+4.2}_{-4.8}$ mas ($\sim$16 au), respectively"]
- result: Ring radius = 116.0 ± +4.2/-4.8 mas [abstract: "116.0$^{+4.2}_{-4.8}$ mas ($\sim$16 au), respectively"]
- result: Gap-to-dust R68 ratio of gas/dust (visibility plane) = 7.7 (R68), 7.8 (R90), 6.3 (R95) ± not stated dimensionless [Table 2: "| | Ratio | 7.7 | 7.8 | 6.3 |"]
- result: Dust R68 image plane = 0.121 ± ±0.001 arcsec [Table 2: "| plane | Dust | 0.121 $\pm$ 0.001 | 0.144 $\pm$ 0.002 | 0.149 $\pm$ 0.002 |"]
- result: Delta AIC (ring vs Gaussian) = -24.4 ± not stated dimensionless [Statistical comparison of dust substruc…: "The Gaussian+Ring model is strongly favored by the AIC ($\Delta\text{AIC}=-24.4$)"]
- result: Delta BIC (ring vs Gaussian) = +11.8 ± not stated dimensionless [Statistical comparison of dust substruc…: "The BIC favors the simpler Gaussian model ($\Delta\text{BIC}=+11.8$)"]
- limitation (authors): Low S/N; EDDY ignores beam convolution; visibility mass inconsistent with Teff [4.1 Substellar Mass of 2M0444: "EDDY` does not take the beam convolution into account, which may result in smaller stellar mass"]
- limitation (authors): Substructure tentative; BIC prefers no ring [Statistical comparison of dust substruc…: "the evidence for the additional substructure is less compelling under BIC"]
- not stated (card): Self-calibration solution intervals for each iteration; Line-free channels and continuum-subtraction method/order; Cell size and image size; Flagged channel ranges and reference antenna; Priors ranges and parameter list for 12CO two-layer visibility model and code used; galario prior bounds and initial positions; Keplerian mask parameters and EDDY settings (radial range, fitting method); Which 12…

### 2020ApJ...891...48H: A Multifrequency ALMA Characterization of Substructures in the GM Aur Protoplanetary Disk (2020; protoplanetary_disks; observational_alma_primary)
- question: What are the dust substructures, spectral index variations, optical depths and gas cavity of the GM Aur disk at high resolution in Bands 4 and 6?
- step 3: Fit axisymmetric surface brightness models in uv plane
  - method: Delta function + Gaussian rings parametrization, vis_sample synthetic visibilities, MCMC, 21 free parameters [4.1. Surface brightness models: "for a total of 21 free parameters."]
  - software: vis_sample, emcee, CASA
  - parameter: 96 walkers, 20,000 steps, 10,000 burn-in; weights scaled down by 2.667 [4.1. Surface brightness models: "Each ensemble employs 96 walkers for 20,000 steps, with the first 10,000 steps discarded as burn-in."]
  - assumption: Axisymmetric, geometrically thin [4.1. Surface brightness models: "An axisymmetric model is adopted, given that the azimuthal variations described in Section 3 are modest."]
  - fitting: emcee affine-invariant sampler; uniform priors on profile parameters, Gaussian priors on PA, i, offsets (Table 3); Gaussian likelihood in visibilities [4.1. Surface brightness models: "Uniform priors are adopted for the parameters defining I ν ."]
  - validation: Compared model and residual images/profiles; residuals up to 8.4 sigma at 1.1 mm and 6.8 sigma at 2.1 mm [4.1. Surface brightness models: "Some significant residuals remain, as large as 8.4 σ at 1.1 mm and 6.8 σ at 2.1 mm."]
- step 5: Test B84 geometry with radiative transfer
  - method: RADMC-3D models: flat, thick, warped rings, imaged with CASA and plotted in polar deprojection [4.3. The geometry of B84: "we use RADMC-3D (Dullemond 2012) to perform 3D Monte Carlo radiative transfer calculations"]
  - software: RADMC-3D, vis_sample, CASA
  - parameter: 512 radial cells, 1024 poloidal cells, 64 azimuthal cells, 10^8 photon packages; parameters in Table 4 [4.3. The geometry of B84: "64 azimuthal cells spaced evenly between 0 and 2 π, and 10 8 photon packages."]
  - assumption: p = 3.5, a_max = 1 mm; vertically isothermal [4.3. The geometry of B84: "We use a dust population with p = 3 . 5 and a max = 1 mm"]
  - fitting: Parameters adjusted manually until ring width and height match [4.3. The geometry of B84: "The parameters to generate the disk surface density are adjusted manually"]
  - validation: Models illustrative, not best fit [4.3. The geometry of B84: "Thus the models we present should be taken as illustrative, not as a “best fit” to GM Aur."]
- result: Inclination from 1.1 mm fit = 53.20 ± ±0.01 degree [Table 3: "53 . 20 ± 0 . 01"]
- limitation (authors): Temperature, flux calibration and degeneracies prevent precise grain size measurements [4.2.2. Constraints on dust grain sizes: "the aim of this section is to comment on which regions of parameter space are consistent with the observations rather than to provide precise measurements."]
- not stated (card): Line-free channels flagged for Band 6 continuum; Self-calibration solution intervals and number of iterations; Gaussian taper parameters for the HCO+ cube; CLEAN thresholds and image size/cell size; Exact visibility binning and weight handling code for the MCMC fits; Which data reduction scripts were used (not released)

### 2019ApJ...871..100H: ALMA Observations of the Protostellar Disk around the VeLLO IRAS 16253-2429 (2019; star_formation, protoplanetary_disks; observational_alma_primary)
- question: Is there a disk around the VeLLO IRAS 16253, and what are its dust, kinematic and chemical (CO freeze-out) properties?
- step 1: Fit continuum visibilities with double Gaussian
  - method: Double Gaussian fit to visibility amplitudes at 0.87 and 1.38 mm, finding a break at ~200 kλ between extended and compact components [continuum emission at 0.87 mm and 1.38 …: "We employ a double Gaussian fit to the observed amplitude but not phase, and we find a break point at a $uv$-distance of $\approx$200 k$\lambda$"]
  - validation: Check sources compared to reference positions (within 10 mas at 1.3 mm, 5 mas at 0.87 mm) [continuum emission at 0.87 mm and 1.38 …: "find that they are consistent with the referenced positions within 10 mas and 5 mas, respectively"]
- step 2: Model continuum offset with radiative transfer
  - method: RADMC-3D flared disk (A) and torus-like thick disk (B1/B2) grids, chi2 fit to visibilities beyond 200 kλ using vis_sample [Models of the continuum images: "We construct model grids (Sections [4.1.1](#sec:modA) and [4.1.2](#sec:modB)) to perform a $\chi^2$ fitting to the visibilities at uv-distances beyond 200 k$\lambda$."]
  - software: RADMC-3D, DIANA Opacity Tool, vis_sample
  - parameter: Model A free parameters: Lstar, Mdisk, Rdisk, theta_flared, a_pow, a_max; r0 = 25 au [Model A - flared-disk model: "We take six free parameters including the protostellar luminosity ($L_{\rm star}$), $M_{\rm disk}$ (total mass of the disk scaled by $\Sigma_0$), $R_{\rm disk}$, $\theta_{\rm flared}$, $a_{\rm pow}$, and $a_{\rm max}$."]
  - assumption: Inclination 65 deg from Gaussian aspect ratio; center, PA fixed from 1.38 mm fit; grain size distribution n(a) ∝ a^-a_pow [Model A - flared-disk model: "an inclination angle of $65\ensuremath{^\circ}$ is estimated from the Gaussian aspect ratio"]
  - fitting: chi-squared grid fit; errors from chi2 distribution at 99.9% confidence [Table 2: "The error of the fitted parameters are calculated with the $\chi^2$ distribution in a confidence level of 99.9%."]
  - validation: Compare model peak offset with observed 46 mas [Model A - flared-disk model: "the offset (7 mas) in this model is still much smaller than the observed one (46 mas)"]
- step 4: CO channel-map model with CO depletion
  - method: Compare best-fit dynamic model with channel maps via vis_sample, per-channel intensity scaling, add f_snow zeroing gas below f_snow×H [CO channel map and CO-depletion model: "the gas density at $z<f_{\rm snow}\times H(R)$ is set to zero, with $f_{\rm snow}$ between 0 (no CO depletion) and 1 (complete CO depletion)"]
  - software: vis_sample
  - fitting: best f_snow = 0.55, chi2_r 1.78 vs 1.92 for f_snow=0 [CO channel map and CO-depletion model: "we find the best-fit CO-depletion model for $f_{\rm snow}=0.55$ with $\chi^2_{\rm r}=1.78$ while $\chi^2_{\rm r}=1.92$ for $f_{\rm snow}=0$"]
  - validation: Qualitative reproduction of quadruple pattern; chi2 difference small [CO channel map and CO-depletion model: "The model with CO depletion reproduces the quadruple pattern qualitatively well, though the CO peak positions are not perfectly matched and the difference between the $\chi^2_{\rm r}$ is small."]
- result: 1.3 mm deconvolved Gaussian size = 0.16" x 0.07" (20 au x 8.8 au) ± not stated arcsec [abstract: "The 1.3 mm dust continuum emission has a deconvolved Gaussian size of $0.16\ensuremath{''}\times0.07\ensuremath{''}$ (20 au $\times$ 8.8 au)"]
- result: Offset between 0.87 and 1.38 mm peaks = 46 ± not stated mas [continuum emission at 0.87 mm and 1.38 …: "the central positions are offset by 46 milliarcsecs (mas)"]
- result: Disk component flux 1.38 mm = 10.1 ± 0.4 mJy [Table 1: "10.1$\pm$0.4"]
- result: Best-fit CO depletion parameter f_snow = 0.55 ± not stated dimensionless [CO channel map and CO-depletion model: "we find the best-fit CO-depletion model for $f_{\rm snow}=0.55$"]
- result: Central mass from Keplerian rotation = 0.12 ± not stated Msun [dynamics of the disk-envelope system: "We then estimate a mass of the central star of 0.12 $M_\odot$"]
- result: Model A disk mass = 1.6e-3 ± 0.1e-3 Msun [Table 2: "1.6$\pm$0.1"]
- limitation (authors): Offset smaller than beam; calibration issue or proper motion not excluded [grain growth at the Class 0 stage: "the offset of $0.046\ensuremath{''}$ is smaller than the beam sizes, $0.15\ensuremath{''}$ at 0.87 mm and $0.1\ensuremath{''}$ at 1.38 mm"]
- not stated (card): CASA version and whether the pipeline or manual calibration was used; Imaging task, deconvolver, cleaning masks, cell/image size, continuum-subtraction channels; Flux scale uncertainty; Model grid ranges and step sizes for continuum and PV fits; Dust composition/opacity inputs to the DIANA tool; Distance adopted; Details of the Cycle 2 C18O data processing and project-code association (2013.1.008…

### 2020ApJ...901...74T: Structural Evolution in Massive Galaxies at z ∼ 2 (2020; high_z_galaxies; observational_alma_primary)
- question: Where does star formation occur in massive (M*>1e11) star-forming galaxies at z~2 (FIR vs optical/mass size), and how will these galaxies change their size and central mass?
- step 3: Measure FIR sizes via visibility fitting
  - method: Fit elliptical/circular Gaussian and exponential disk (n=1) models to visibilities [4.1: "we fit elliptical or circular Gaussian models to the observed data by using the `UVMULTIFIT`"]
  - software: UVMULTIFIT
  - parameter: Only S/N>10 sources (62) used for size discussion [4.1: "We use only 62 massive SFGs with S/N$>$10 for discussion of the size measurements at 870 $\mu$m."]
  - assumption: Disk model: axis ratio and PA fixed to Gaussian values [4.1: "We fit the visibility data to exponential disk models by fixing the axis ratio and the position angle to the values derived from Gaussian fitting."]
  - fitting: Multi-component models for fields with several sources; circular Gaussians for extra components [Appendix B: "When more than one source is detected in the observed field, we use two- or three-component models for the fitting."]
  - validation: Mock sources injected into visibilities of non-detected objects; recovery tested in S/N bins [Appendix B: "The uncertainties in the size measurements are typically $\Delta$FWHM=$\pm$0.2$''$ at S/N=5, $\Delta$FWHM=$\pm$0.1$''$ at S/N=10, and $\Delta$FWHM=$\pm$0.05$''$ at S/N=15."]
- limitation (authors): Half-mass radius may be overestimated due to dust extinction; JWST 3-4 um needed. [Summary: "One caveat of our study is that we may overestimate the half-mass radius of massive SFGs due to strong dust extinction in the galaxy centers"]
- limitation (authors): Sample is rest-optically selected; optically dark galaxies may be missed. [2.1 Sample selection: "it is possible that some unknown number of massive galaxies could be optically dark and missed"]
- not stated (card): CASA version and calibration/flagging details; whether pipeline or manual; Calibrator and flux scale uncertainties; Spectral window setup and continuum bandwidth; Cell size and image size for tclean; Treatment of archival data from different projects (frequency/resolution differences); UVMULTIFIT starting values, bounds and fit procedure details; Number of mock simulations processing details; SED…

### 2024A&A...685A..80Z: Unveiling [C II] clumps in a lensed star-forming galaxy at z ∼ 3.4 (2024; high_z_galaxies; observational_alma_primary)
- question: Are there [C II]-emitting clumps (parent molecular clouds) in a lensed z~3.4 galaxy that hosts UV clumps, and what are their gas masses and depletion times?
- step 2: Extract [C II] line and integrated map
  - method: Iterative uv-plane 2D Gaussian fit (uv_fit) channel by channel, extract 1D spectrum, average best channels, refit position until convergence [3.3 [C II] emission line map: "We modeled our target’s emission in the *uv* plane with the GILDAS task `uv_fit`, adopting a two-dimensional (2D) Gaussian profile in all four sidebands and channel per channel."]
  - software: GILDAS
  - fitting: Gaussian fit of 1D spectrum for redshift [3.3 [C II] emission line map: "we adopt the redshift obtained from the 1D Gaussian fit"]
  - validation: Redshift agrees with SINFONI within 1 sigma; M2 gives consistent results [3.3 [C II] emission line map: "found that they agree within $1 \sigma$, increasing the reliability of the detection"]
- step 3: Continuum upper limits
  - method: Averaged line-free channels; 5σ upper limit from uv-plane Gaussian or PSF fit with fixed position [3.2 Continuum emission map: "we report the total flux density upper limit that we estimated as the 5$\sigma$ uncertainty obtained when fitting, in the *uv* plane, the Fourier Transform of a 2D Gaussian model"]
  - software: GILDAS
- step 5: Measure clump [C II] fluxes
  - method: uv-plane fit of 2D PSF per channel with free centre (method 3), summed over adjacent channels; compared to image-plane and Gaussian fits; corrected by average magnification [3.6 Measuring clumps [C II] flux: "We decided to adopt the flux measurements obtained by fitting clumps with PSF models"]
  - software: GILDAS
  - assumption: Clumps unresolved [3.6 Measuring clumps [C II] flux: "as they are expect to be unresolved at the resolution of our observations"]
  - validation: Five flux methods compared; conclusions unchanged [3.6 Measuring clumps [C II] flux: "Even when adopting fluxes obtained with the other reported methods, the conclusions of our work do not change substantially."]
- result: Integrated [C II] flux (M1) = 7.5 ± 0.7 mJy (over 122 km/s) [3.3 [C II] emission line map: "The total observed flux is $\mathrm{F_{[C\,{\footnotesize II}]} = 7.5 \pm 0.7\, mJy}$ (over $\mathrm{\Delta v = 122\, km\, s^{-1}}$)."]
- result: [C II] redshift = 3.39548 ± 0.00007 dimensionless [3.3 [C II] emission line map: "$z_\mathrm{[C\,{\footnotesize II}]} = 3.39548 \pm 0.00007$"]
- result: Continuum 5σ upper limit (PSF model, intrinsic) = < 34 ± not stated μJy [5.2 The lack of dust continuum: "$\mathrm{F_{cont} < 34\, \mu Jy}$ when considering a PSF model"]
- limitation (authors): Clump C is tentative and needs confirmation; dynamical modelling is beyond scope [3.5 Identifying clumps: "More observations with higher S/N are needed to confirm it."]
- not stated (card): Line-free channel ranges used for the continuum map; Exact uv_fit/imaging settings (cell size, image size, uv taper) in GILDAS; Absolute flux calibration uncertainty and phase calibrators; Full details of the lens model and magnification maps (from Iani2021); Kennicutt UV-SFR conversion constants after IMF scaling; Area definition used for the surface densities of clumps; Number of ALMA antennas …

### 2019A&A...628A.118B: The gentle monster PDS 456. Kiloparsec-scale molecular outflow and its implications for QSO feedback (2019; agn_and_quasars, nearby_galaxies; observational_alma_primary)
- question: Does the hyper-luminous radio-quiet QSO PDS 456, which hosts a powerful UFO, have a kpc-scale molecular outflow, and what are its energetics relative to energy-conserving expansion?
- step 1: Continuum subtraction and imaging
  - method: UV-plane zero-order continuum fit to spw0+spw1, subtraction, Hogbom cleaning with interactive masks [ALMA observation and data reduction: "We subtracted this fit from the global visibilities and created continuum-subtracted CO(3$-$2) visibilities."]
  - software: CASA
  - parameter: natural weighting, 0.04 arcsec pixel, 30 km/s channels [ALMA observation and data reduction: "a pixel size of 0.04 arcsec and a spectral resolution of $\sim30$ km s$^{-1}$"]
  - assumption: intrinsic QSO continuum variation across spw0/spw1 less than 1% [ALMA observation and data reduction: "the intrinsic QSO continuum variation across spw0 and spw1 is expected to be less than 1%"]
  - validation: first-order polynomial did not significantly change results [ALMA observation and data reduction: "A first order polynomial fit to the continuum emission did not significantly change our results."]
- result: 340 GHz continuum flux density = 0.69 ± 0.02 mJy [Results: "a flux density of $0.69\pm0.02$ mJy"]
- limitation (authors): Gas masses depend strongly on alpha_CO; large uncertainties on tau_dep and tau_SF [Discussion: "We note that the estimate of the molecular gas masses strongly depends on the assumption on $\alpha_{\rm CO}$."]
- not stated (card): Clean mask definitions and iteration counts; Pipeline version and exact flagging; Priors, optimiser and initial guesses for the Gaussian pixel-by-pixel decomposition; 3DBarolo parameter settings (ring widths, fit options); Method for deriving v98 and clump selection details; Fitting method for the parabolic scaling relations; SFR from SED fit (Vignali in prep.) is not reproducible; Exact L'CO1-0 …

### 2020ApJ...902..141S: The VLA/ALMA Nascent Disk and Multiplicity (VANDAM) Survey of Orion Protostars. III. Substructures in Protostellar Disks (2020; star_formation, protoplanetary_disks; observational_alma_primary)
- question: How early do substructures (rings, gaps, cavities, asymmetries) form in protostellar disks, and how young/embedded are the disks that show them?
- step 3: fit analytic ring/asymmetry/point/Gaussian models in uv plane
  - method: Image-plane model Fourier-transformed with GALARIO at observed baselines; up to 18 parameters [3.1 Analytic Models: "we generate an image-plane model image, and use the `GALARIO` package (cite: Tazzari2018) to compute the Fourier transform of that image sampled at the same baselines as our observations."]
  - software: GALARIO, dynesty
  - parameter: Visibility weights multiplied by ~0.25 to match image RMS [2 Sample Selection & Data Reduction: "the weights provided by the ALMA pipeline need to be multiplied by a factor of $\sim0.25$ to match the RMS of the images"]
  - fitting: Bayesian nested sampling with dynesty, uniform priors; best fit = maximum posterior sample; uncertainties 95% inclusion interval [3.1 Analytic Models: "Samples are drawn from uniform priors on all parameters, with limits listed in Table [\[table:analytic_priors\]]"]
  - validation: Bayes factors between model complexities; residual images and visibility profiles [3.2 Analytic Modeling Results: "we provide a calculation of Bayes Factor in Table [\[table:analytic_best_fits\]] for each model considered, compared with the most complete model"]
- step 5: fit protostar+disk+envelope RT models
  - method: RADMC-3D models of SED and 345 GHz image, GALARIO to visibilities, emcee MCMC; visibilities centered using analytic best-fit centroids [3.3 Radiative Transfer Modeling: "we instead use the `emcee` code to run a Markov Chain Monte Carlo (MCMC) fit of the synthetic observations to our dataset"]
  - software: RADMC-3D, GALARIO, emcee, pdspy
  - parameter: Protostar T=4000 K, luminosity free; inner disk radius 0.1 au; cavity or gap added [3.3 Radiative Transfer Modeling: "we fix the inner radius of the disk at 0.1 au, and include a central cavity or a gap with some amount of depletion"]
  - assumption: Distance 400 pc; axisymmetric models; Ulrich envelope [3.3 Radiative Transfer Modeling: "we assume they are all at 400 pc, a typical distance for Orion"]
  - fitting: emcee; best fit = max posterior, 95% range uncertainties; lost walkers redistributed [3.4 Radiative Transfer Modeling Results: "Walkers that got “lost" (cite: Sheehan2019), were redistributed around the median of the post-burn-in samples"]
  - validation: Compared models to ACA data not included in fit [3.4 Radiative Transfer Modeling Results: "Despite not being included in the fits, our best fit models show good consistency with the short-baseline ACA data"]
- result: Ring center radii range = ~0.1"-0.6" (40-240 au) ± not stated arcsec [3.2 Analytic Modeling Results: "The radii of the centers of the rings range from $\sim0.1"-0.6"$ ($40-240$ au at the distance of Orion)"]
- result: Ring radius HOPS-124 (analytic) = 146.9 ± +0.7/-0.6 mas [Table 3: "$r_{c,r}$ (mas) | $105.0^{+ 1.7}_{- 2.0}$ | $331.0^{+ 10.0}_{- 10.6}$ | $595.9^{+ 16.7}_{- 20.7}$ | $146.9^{+ 0.7}_{- 0.6}$"]
- limitation (authors): HOPS-56B envelope mass is more uncertain due to nearby source subtraction [3.4 Radiative Transfer Modeling Results: "the results for HOPS-56B should be considered more uncertain than the nominal errors show"]
- limitation (authors): HOPS-124 and HOPS-157 envelope masses may be lower limits [3.4 Radiative Transfer Modeling Results: "the envelope masses measured here, and consequently their $M_{env}/M_{disk}$ ratios, might reasonably be considered lower limits"]
- not stated (card): CASA version used; Exact clean parameters and masks for the sources imaged here, and uvsub masks for HOPS-56B and HOPS-140; dynesty settings (live points, stopping criteria); emcee walker number, steps, burn-in and priors for the RT models; Full RT parameter list, priors and dust model details (deferred to Sheehan2017b); Which analytic model components are used for each source beyond the Bayes fa…

### 2018A&A...617A..23B: Molecular line study of the S-type AGB star W Aquilae. ALMA observations of CS, SiS, SiO and HCN (2018; evolved_stars, astrochemistry; observational_alma_primary)
- question: What are the spatial distribution, abundances and radial extent of CS, SiS, 29SiO and H13CN in the circumstellar envelope of the S-type AGB star W Aql, resolved with ALMA?
- step 2: Fit emission size in uv plane
  - method: Fit circular Gaussian, then Gaussian plus delta function, to visibilities per channel (main array + ACA only) [4.3 uv fitting: "we use the CASA tool *uvmultifit* (cite: Marti-Vidal2014), to fit geometric flux models to the bright emission regions of all spectral lines."]
  - software: uvmultifit, CASA
  - parameter: Gaussian position, flux density, FWHM; delta component at same position [4.3 uv fitting: "described by its position (relative to the current stellar position of RA 19:15:23.379 and DEC –07:02:50.38 J2000.0 (cite: Ramstedt2017)), flux density, and FWHM size"]
  - assumption: Gaussian intensity distribution; uncertainties assume reduced chi2 of 1 [Appendix uv-fitting: "meaning that the reduced $\chi^2$ can be assumed to be similar to its expected value of unity"]
  - fitting: chi2 minimisation; uncertainties from post-fit covariance matrix [Appendix uv-fitting: "estimates the uncertainties of the fitted parameters from the curvature of the $\chi^2$ distribution at its minimum via the diagonal elements of the post-fit covariance matrix"]
  - validation: Residual images imaged and checked as Gaussian noise; Monte Carlo exploration of chi2 PDFs [Appendix uv-fitting: "we have performed a Monte Carlo analysis of our Gaussian source model plus additional delta component across the full parameter space"]
- limitation (authors): Spherical symmetry assumed despite asymmetric emission [6.2 Limitations of radiative transfer m…: "The most obvious limitation of the radiative transfer models is that they assume spherical symmetry"]
- limitation (authors): Weak lines too low S/N for uv fitting [4.3 uv fitting: "the signal-to-noise ratio (S/N) for all weak lines is too low for confident fitting"]
- not stated (card): CASA version used for calibration and imaging; CLEAN threshold, mask criteria, cell size and image size; Line-free channels and continuum subtraction method; Flux calibration uncertainty and whether archive products were used as is; uvmultifit settings (initial guesses, channel handling); Exact ALI model grid, fitting criterion and how best fit was judged beyond by-eye; Wind velocity profile para…

### 2015ApJ...811..124S: Sub-kiloparsec Imaging of Cool Molecular Gas in Two Strongly Lensed Dusty, Star-forming Galaxies (2015; high_z_galaxies; multi_facility_alma_minor)
- question: What are the sizes, structure and kinematics of the cool molecular gas (low-J CO) versus dust in two lensed SPT DSFGs, and what do they imply for alpha_CO and the star formation relation?
- step 2: Visibility-plane lens modeling of CO and continuum
  - method: Gaussian source-plane components per velocity channel lensed with fixed ALMA-derived SIE lens, fit to visibilities [3 Lens Modeling: "we fit lensing models directly to the measured visibilities. As in (cite: hezaveh13), we use a Bayesian Markov Chain Monte Carlo (MCMC) fitting procedure."]
  - parameter: Each Gaussian has up to four free parameters: centroid, flux, size [3 Lens Modeling: "Each profile has up to four free parameters, namely, the two-dimensional centroid of the source and its intrinsic flux and size."]
  - assumption: Lens parameters fixed to ALMA best fit [3 Lens Modeling: "so we use the best-fit lens properties derived from the ALMA continuum data to model the source-plane in the ATCA CO data."]
  - fitting: MCMC with chi^2 metric [3 Lens Modeling: "using the $\chi^2$ metric to determine the quality of the fit."]
  - validation: Residuals consistent with noise; alternative channelizations tested [4.1 SPT0346-52: "We have modeled alternative channelizations of the data, with velocity bins ranging from 100–400 $\rm{km\,s}^{-1}$"]
- result: SPT0538-50 CO(3-2)/CO(1-0) brightness temperature ratio = ~0.6 ± not stated dimensionless [4.2.3 CO(1–0) Emission: "implies a CO brightness temperature ratio of $r_{31} \sim 0.6$"]
- limitation (authors): Systematic uncertainties in alpha_CO ~100% per method [5.2.4 Summary of CO–H$_2$ Conversion Fa…: "The uncertainty in these estimates is dominated by systematic, rather than statistical, errors of $\sim$100% for each method."]
- not stated (card): MCMC sampler, priors, chain length and convergence criteria; Calibration software and versions (ATCA/ALMA reduction packages); Best-fit lens parameters fixed from ALMA models; Line-free channels and continuum subtraction details; MAGPHYS fit configuration; Stellar mass upper limit for SPT0346-52 (Ma et al. in prep.)

### 2025A&A...700A.188C: FAUST: XXVI. The dust opacity spectral indices of protostellar envelopes bridge the gap between interstellar medium and disks (2025; star_formation, protoplanetary_disks; large_program_or_survey)
- question: What are the dust opacity spectral indices (beta) of protostellar envelopes, after removing the optically thick disk contribution, and do they bridge ISM-like and disk-like values?
- step 3: Remove secondary sources in field
  - method: Model distant secondaries as Gaussians and subtract from visibilities; close secondaries fit jointly [Removal of secondaries: "We modeled the secondary sources as gaussians using `uvmodelfit` CASA routine"]
  - software: CASA uvmodelfit, CASA ft, CASA uvsub
- step 4: Fit visibilities with compact (Gaussian) plus Plummer envelope models
  - method: Sum of 2D Gaussians and Plummer envelope visibilities fit per band [3: "we consider the total model to be the sum of the visibilities of the individual components"]
  - software: emcee, galario, CARTA
  - parameter: Uniform priors: sigma 0-0.7'', Ri 0-2.0'', Rout 2.0-15.0'', p+q in [1,3], inc/PA full range, offsets within few tenths of arcsec [3: "Finally, the envelope power law exponent p+q was set free in the range \[1,3\]."]
  - parameter: 120 walkers, 25000 steps [3: "We ran 120 walkers for 25000 steps to reach convergence"]
  - fitting: MCMC with emcee, galario chi2 on visibilities, uniform priors [3: "The parameters were all set to vary within uniform prior distributions."]
  - validation: Reduced chi2 reported; compact flux saturation at 150-200 klambda consistent with Galametz2019 [3: "We thus confirm that their approach is robust"]
- result: alpha of compact component, IRAS15398-3359 = 2.2 ± 0.2 dimensionless [Table 1: "| IRAS15398-3359 | 1.28 | 8.09 | 9 | 2.2 $\pm$ 0.2 |"]
- limitation (authors): Azimuthal averaging in the uv-plane loses 2D morphology information [3: "the main one being the loss of information about the 2D source morphology"]
- limitation (authors): High chi2 for asymmetric envelopes and unsubtracted FOV sources [3: "in some cases, the $\chi^2$ results significantly higher than unity"]
- not stated (card): Exact ALMA configurations, execution blocks and on-source times per source; Spectral window frequencies and continuum bandwidths; Cell size, image size, masking, deconvolver and clean threshold; Self-calibration solution intervals; Burn-in and convergence diagnostics for emcee; Which uv-bins and uncertainties were used for alpha and beta profiles; How beta at 500 au was extrapolated and gradient …

### 2015ApJ...811...39I: ALMA Observations of the Submillimeter Dense Molecular Gas Tracers in the Luminous Type-1 Active Nucleus of NGC 7469 (2015; nearby_galaxies, agn_and_quasars, astrochemistry; observational_alma_primary)
- question: How are submillimeter dense gas tracers (HCN, HCO+, CS 4-3/7-6) distributed in NGC 7469, and do the line ratios at the AGN support the submm-HCN enhancement and constrain AGN heating effects?
- step 1: Image continuum and lines
  - method: CASA CLEAN with natural weighting; uv-plane continuum subtraction; primary beam correction [2.1: "All images of the line and continuum emissions were reconstructed with the CASA task `CLEAN` (gain = 0.1, threshold = 1.0 mJy, weighting = natural)."]
  - software: CASA
  - parameter: gain 0.1, threshold 1.0 mJy [2.1: "gain = 0.1, threshold = 1.0 mJy, weighting = natural"]
  - validation: Continuum peak coincides with VLA 8.4 GHz peak [3: "This precise match supports the accuracy of the astrometry of ALMA."]
- result: 860 um continuum peak at AGN = 5.19 ± 0.09 mJy/beam [3: "is 5.19$\pm$0.09 mJy beam$^{-1}$"]
- limitation (authors): 150 pc resolution mixes AGN and SB contributions; CO(3-2) only partially covered [1: "the spatial resolution of this study ($\sim$ 150 pc) would still be insufficient to exclusively probe the region where gas heating due to an AGN"]
- not stated (card): CLEAN mask, iteration count and cleaning region; line-free channel selection for continuum; spectral window to channel mapping and CASA clean spw/width settings; flux density of J2232+117 adopted; Exact apertures/regions for CND integration of luminosities; Which MIRIAD and CASA commands for Gaussian fitting of spectra

### 2018ApJ...855L...2M: Detection of a Millimeter Flare from Proxima Centauri (2018; stellar_physics, debris_disks, exoplanets; archival_reuse)
- question: Does the 1.3 mm emission from Proxima Cen require dust belts, or is it explained by stellar flaring and coronal emission?
- step 1: Image and fit 12-m continuum
  - method: Natural-weight clean image and uvmodelfit point source fit to visibilities, combined and per SB/scan [3.1 ALMA 12-m Observations: "Fitting a point source model to the visibilities using the `CASA` task `uvmodelfit` yields a total flux density of $101\pm9$ $\mu$Jy"]
  - software: CASA
  - validation: Compared with Anglada et al. 106±12 uJy [3.1 ALMA 12-m Observations: "consistent with the result of $106\pm12$ $\mu$Jy reported by (cite: ang17)"]
- step 3: Find and characterize ACA flare
  - method: Image the 13 ACA observations individually, then fit visibilities in 2 s intervals in the flare scan; alpha and |Q/I| in 5 s bins [3.2 ACA Observations: "we fit models to the visibilities in this scan in 2 second intervals using `uvmodelfit` in `CASA`"]
  - software: CASA
- result: 12-m flux density = 101 ± 9 uJy [3.1 ALMA 12-m Observations: "yields a total flux density of $101\pm9$ $\mu$Jy"]
- result: Flare peak flux density = 100 ± 4 mJy [3.2 ACA Observations: "At peak brightness, the flux density reaches $100\pm4$ mJy"]
- result: Flare peak luminosity = 2.04e14 ± 0.15e14 erg/s/Hz [3.2 ACA Observations: "a luminosity of $2.04\pm0.15\times10^{14}$ erg s$^{-1}$ Hz$^{-1}$ at 1.3 pc"]
- result: Flare minimum spectral index = -1.77 ± 0.45 dimensionless [3.2 ACA Observations: "a minimum value of $\alpha = -1.77\pm0.45$"]
- result: Flare |Q/I| at peak = 0.19 ± 0.02 dimensionless [3.2 ACA Observations: "$|Q/I| = 0.19\pm0.02$"]
- not stated (card): CASA version; clean cell size, image size, niter, and threshold; uvmodelfit starting parameters; how the spectral index and uncertainties were derived; how flux density in the 2 s and 5 s bins was extracted; how the number of background sources was computed from the counts

### 2019ApJ...882..118X: ALMA Detection of Vibrationally Excited (v <SUB>t</SUB> = 1, 2) Acetic Acid toward NGC 6334I (2019; astrochemistry, star_formation; observational_alma_primary)
- question: Are vibrationally excited (vt = 1, 2) acetic acid lines present toward NGC 6334I, and what are their excitation temperature, column density and spatial distribution?
- step 1: Image and continuum-subtract
  - method: UV-plane continuum subtraction, tclean imaging, smoothing to 0.26'' beam [2 Observations: "used to subtract the continuum emission in the UV-plane."]
  - software: CASA
  - parameter: Briggs robust 0.5 (B4, B6), 0.0 (B7) [2 Observations: "a Robust parameter of 0.5 for the Band 4 and 6 data and 0.0 for the Band 7 data"]
- limitation (authors): Uncertainties may be underestimated since continuum subtraction systematics not included [3.1 Line Identification: "the uncertainties listed here might be underestimated as we have not incorporated the systematic uncertainties introduced by continuum subtraction."]
- not stated (card): Actual line-free channel ranges; CASA version; Calibration/pipeline details and flux uncertainty; tclean cell size, image size, niter, threshold, masks; Details of Gaussian fits and chi2 fit implementation; How T_bg values were measured; Band 4 and Band 7 observing parameters (arrays, dates) in this paper

### 2025ApJ...986L..22R: The First Detection of Molecular Activity in the Largest Known Oort Cloud Comet: ALMA Imaging of C/2014 UN271 (Bernardinelli─Bernstein) at 16.6 au from the Sun (2025; solar_system; observational_alma_primary)
- question: What are the molecular activity drivers, CO outgassing kinematics and continuum (nucleus/dust) properties of the distant active Oort cloud comet C/2014 UN271 at 16.6 au?
- step 3: Fit CO line with 3D radiative transfer and derive production rates and scale lengths
  - method: SUBLIMED non-LTE model, two regions (jet and ambient), Haser distribution, vis_sample Fourier transform, least-squares fit to visibilities [Fourier Domain Modeling: "We then performed least-squares fits of our radiative transfer models against the measured interferometric visibilities."]
  - software: SUBLIMED, vis_sample, lmfit
  - parameter: Lp=0 assumed for geometry; free Q1,Q2,v1,v2,gamma,phi,psi [Fourier Domain Modeling: "allowing the molecular production rate, expansion speed, and jet geometry ($Q_1, Q_2, v_1, v_2, \gamma, \phi, \psi$) to vary as free parameters"]
  - assumption: Gas kinetic temperature 4 K [Fourier Domain Modeling: "We assumed a gas kinetic temperature $T_{\mathrm{kin}}$ = 4 K"]
  - assumption: H2CO-CO collision cross-section 5e-14 cm-2 (thermalization approximation) [4.1: "using an average collisional cross-section with CO of $5\times10^{-14}$ cm$^{-2}$"]
  - fitting: Levenberg-Marquardt least squares; uncertainties from covariance diagonal; Lp from delta chi2 curve (1 and 2.6 sigma at 1 and 6.63) [Fourier Domain Modeling: "We obtained the 1$\sigma$ and 2.6$\sigma$ uncertainties from the values for $\Delta\chi^2$ = 1 (68% confidence) and 6.63 (99% confidence) thresholds."]
  - validation: Checked for background CO sources with Planck maps and SIMBAD [4.1: "confirmed there were no known background sources within 100$\ensuremath{''}$"]
- step 5: Continuum visibility fits: nucleus size and dust coma mass
  - method: lmfit fits to 233 GHz visibilities with point source, point+1/rho coma, and fixed max coma; NEATM diameters; coma dust mass from flux with opacities [Continuum Modeling: "We used the `lmfit` package to perform least squares fits to the 233 GHz continuum visibilities"]
  - software: lmfit
  - parameter: Tss=95±9 K (NEATM) or 60 K (CO) [Continuum Modeling: "The resulting $T_{ss}$ is 95 $\pm$ 9 K on both dates."]
  - assumption: Opacities 0.17-0.467 m2/kg; dust at equilibrium temperature [Coma Dust Mass: "the derived opacities are in the range $1.70-4.67\times10^{-1}$ m$^2$ kg$^{-1}$"]
  - fitting: Least squares, chi2 comparison [5: "Based on $\chi^2$ analysis, our March 8 data are best fit by a 101–129 km nucleus"]
  - validation: Compared with Lellouch et al. nucleus size [5: "Overall, our values are in formal agreement with (cite: Lellouch2022) within 2$\sigma$."]
- result: Q(CO) March 8 (Lp<2500 km model) = 3.44 ± 0.55 1e27 s-1 [Table 1: "3.44 $\pm$ 0.55"]
- result: Q(CO) March 17 = 5.33 ± 0.88 1e27 s-1 [Table 1: "5.33 $\pm$ 0.88"]
- result: v1 sunward jet speed March 8 = 0.386 ± 0.006 km/s [Table 1: "0.386 $\pm$ 0.006"]
- result: Jet half-opening angle March 8 = 27 ± 5 deg [Table 1: "27 $\pm$ 5"]
- result: Lp 1 sigma upper limit March 8 = <2500 ± not stated km [4.1: "our 1$\sigma$ upper limit on $L_p$ ($<$2,500 km for March 8)"]
- result: Nucleus diameter range = 101-151 ± not stated km [5: "with nominal diameters ranging from 101 km – 151 km"]
- result: Dust coma mass March 8 = 0.44-1.2 ± 0.08-0.2 1e11 kg [Table 5: "$(0.44\pm0.08$)–$(1.2\pm0.2)$"]
- result: Surface temperature from CO speed = 60 ± 2 (Mar 8), 3 (Mar 17) K [4.1.1: "give $T$ = $(60\pm2)$ K and $(60\pm3)$ K on March 8 and 17"]
- limitation (authors): Two-component model is a simplification of the dual-jet geometry; March 17 S/N lower [4.1.1: "Our two-component radiative transfer model is a simplification of this geometry"]
- not stated (card): Line-free channels and continuum subtraction method; Image pixel/cell size and image size; Exact spectral window frequencies and CO rest frequency; Initial guesses and bounds for lmfit fits; Choice of aperture/extraction for interferometric spectra fitted; Pipeline version; Calibrator catalog data used for polynomial fit details; Phase center coordinates

### 2020ApJ...898..146M: Dust Populations in the Iconic Vega Planetary System Resolved by ALMA (2020; debris_disks, exoplanets; observational_alma_primary)
- question: What is the mm-wavelength structure of Vega's outer dust belt, is there warm inner dust emission, and what planetary architecture explains it?
- step 2: Fit stellar flux and offsets
  - method: Point-source fit to 12m visibilities beyond 50 klambda per execution; mean flux adopted for rescaling [3.2 Modelling the star: "We first model the star as a point source and fit the long baseline ($>50 k\lambda$) visibilities of each of the 12-m datasets independently."]
  - software: emcee
  - parameter: 2000 steps, 40 walkers, uniform priors, likelihood exp(-chi2/2), free weight scaling [3.2 Modelling the star: "We ran the MCMC for 2000 steps using 40 walkers, ensuring convergence."]
  - fitting: emcee affine-invariant sampler [3.2 Modelling the star: "using the affine-invariant sampler from (cite: GoodmanWeare2010), starting from uniform priors on all parameters"]
  - validation: Residual maps noise-like at stellar location [3.2 Modelling the star: "produced noise-like maps, free of significant residual emission at the stellar location"]
- step 3: Fit outer belt models to visibilities
  - method: Gaussian, single power-law, double power-law radial models; RADMC-3D ray-trace, primary-beam multiply, GALARIO Fourier transform, star added, MCMC; ACA fit first for ACA stellar parameters, then joint ACA+12m [3.3.1 Modelling framework: "we first ray-trace the belt’s emission at 1.34 mm using RADMC-3D"]
  - software: RADMC-3D, GALARIO, emcee
  - parameter: aspect ratio h fixed to 0.03; walkers = 10 x free parameters; 2000 steps [3.3.1 Modelling framework: "For all models, we fixed the aspect ratio $h$ to 0.03"]
  - assumption: Optically thin; r^-0.5 temperature profile; constant dust opacity [3.3.1 Modelling framework: "we assume the dust to follow a $r^{-0.5}$ radial temperature profile"]
  - fitting: MCMC as for stellar fits [3.3.1 Modelling framework: "We fit this star+belt model to the observed visibilities with MCMC as done for the star-only fits"]
  - validation: Residual images and AIC/BIC model comparison [3.3.2 Modelling results: "Statistical tests such as the Akaike Information Criterion (AIC) and the Bayesian Information Criterion (BIC) confirm"]
- result: Mean stellar flux density at 1.34 mm (12m) = 2495 ± not stated uJy [3.2 Modelling the star: "mean of the best-fit values obtained from the separate 12m datasets (2495 $\mu$Jy)"]
- result: Gaussian belt radius r_c = 118 ± +4/-3 au [Table 2: "$118^{+4}_{-3}$ ($15.3^{+0.5}_{-0.4}$)"]
- result: Gaussian belt FWHM = 67 ± +9/-7 au [Table 2: "$67^{+9}_{-7}$ ($8.7^{+1.2}_{-0.9}$)"]
- result: Power-law inner edge r_in = 74 ± +3/-3 au [Table 2: "$74^{+3}_{-3}$ ($9.6^{+0.4}_{-0.4}$)"]
- result: Double power-law inner slope gamma = 10 ± +5/-3 dimensionless [Table 2: "$10^{+5}_{-3}$"]
- result: Belt flux density (Gaussian) = 8.5 ± +1.3/-1.1 mJy [Table 2: "$8.5^{+1.3}_{-1.1}$"]
- result: Total 1.34 mm flux density of Vega system = 9.9-16.9 ± 1 sigma range mJy [3.3.2 Modelling results: "ranging between $9.9-16.9$ mJy (1$\sigma$ range, including the star)"]
- limitation (authors): Total belt flux is model-dependent due to extrapolation to zero uv distance; position angle and inclination unconstrained [3.3.2 Modelling results: "The best-fit total belt flux at 1.34 mm varies depending on the model employed"]
- limitation (authors): Low target elevation and antenna shadowing [2 Observations: "The high source declination means that the elevations of the Vega scans were low - in the range 21-28$^{\circ}$."]
- not stated (card): CLEAN thresholds, masks, cell and image sizes; Priors ranges and starting positions of belt MCMC; Exact line-free channel selection beyond +-50 km/s and CO imaging details; Pipeline version and ALMA flagging details; Temperature grid details for RADMC-3D; Phase-center coordinates of Vega

### 2015ApJ...808...36M: New Measurements of the Radio Photosphere of Mira Based on Data from the JVLA and ALMA (2015; evolved_stars; observational_alma_primary)
- question: Do JVLA and ALMA continuum data at 46, 96 and 229 GHz match the radio photosphere model of Mira A (size, shape, flux, brightness structure), and what are the properties of Mira B?
- step 4: Fit size, shape, flux of Mira A and B
  - method: Uniform elliptical disk fits to visibilities and elliptical Gaussian fits to images [4.1.1 Mira A: "The first was to fit a uniform elliptical disk model to the visibility data at each observed frequency"]
  - software: AIPS (OMFIT, JMFIT)
  - assumption: distance 110 pc; Tb=2Sc^2/(k nu^2 pi theta_maj theta_min) [Table 2: "The brightness temperature was computed as $T_{b}=2S_{\nu}c^2/(k\nu^{2}\pi\theta_{\rm maj}\theta_{\rm min})$"]
  - fitting: Least-squares fits; errors per Condon (1997) [Appendix: "compute uncertainties according to the formalism outlined by Condon (1997)"]
  - validation: Monte Carlo and artificial source injection tests for systematic errors [Appendix: "we introduced into our actual visibility data at each frequency a series of artificial elliptical Gaussians and uniform elliptical disks"]
- step 5: Test brightness non-uniformity
  - method: Compare multi-component visibility models (ring, point, Gaussian) and residual images for 229 GHz [4.2: "for the 229 GHz data, two-component models produced a clear improvement in $\chi^{2}$, with the elliptical disk+Gaussian fit providing the best match to the data"]
  - software: AIPS
  - fitting: chi-square comparison [Results, Evidence for Non-uniformities …: "none of these three simple models produced a significant improvement in the fit (as assessed by visual inspection of the residuals and the improvement in the $\chi^{2}$ statistic)"]
  - validation: Residual image from visibility subtraction compared to image-plane differencing [4.2: "the result is virtually indistinguishable, suggesting that the image residuals are not solely artifacts of the deconvolution process"]
- result: Mira A 229 GHz flux density (uniform disk) = 150 ± ±30 mJy [Table 2: "| 6 (229 GHz) | 0.51 | 46.2$\pm$2.3 (0.03) | 41.5$\pm$2.3 (0.02) | 144$\pm$11 (0.1) | 0.90$\pm$0.07 | 150$\pm$30 (0.04) | 2620$\pm$560 |"]
- result: Mira A 46 GHz flux density = 7.4 ± ±1.5 mJy [Table 2: "| Q (46 GHz) | 0.76 | 60.0$\pm$2.0 (0.7) | 49.3$\pm$1.6 (0.5) | $156\pm$4 (1) | 0.82$\pm$0.04 | 7.4$\pm$1.5 (0.04) | 2110$\pm$440 |"]
- result: Mira A photospheric radius at 46/96/229 GHz = 3.0 / 2.6 / 2.4 AU ± not stated AU [4.1.1 Mira A: "4.5$\times10^{13}$ cm (3.0 AU) at 46 GHz, 3.9$\times10^{13}$ cm (2.6 AU) at 96 GHz, and 3.6$\times10^{13}$ cm (2.4 AU) at 229 GHz"]
- result: Mira B radius from 229 GHz = ≈2.0e13 ± not stated cm [4.1.2 Mira B: "we derive a radius for Mira B of $\approx2.0\times10^{13}$ cm"]
- result: Mira B 229 GHz flux density = 11.5 ± ±2.3 mJy [Table 3: "| 6 (229 GHz) | 25.4$\pm$0.6 (0.4) | 23.4$\pm$0.6 (0.4) | 69$\pm$7 (7) | 11.5$\pm$2.3 (0.09) |"]
- result: Disk+Gaussian model hot spot fraction at 229 GHz = 39% of 151 mJy in Gaussian FWHM 26 mas ± not stated mixed [4.2: "The total flux density in this model was 151 mJy, with 39% in a Gaussian component with FWHM 26 mas"]
- limitation (authors): Mira A size and PA uncertainties dominated by systematics; disagreements with Vlemmings et al. 2015 in Band 3 [Appendix: "the uncertainties on the source size and position angle reported in this work are dominated by systematic uncertainties"]
- not stated (card): Number of clean iterations, clean masks/thresholds in AIPS; Exact AIPS/CASA versions; Which flagged channels containing line emission in JVLA data; Data selection and weighting for uv fits (OMFIT settings); Exact target coordinates; Whether ALMA self-cal reference antenna and models were specified

### 2024PASJ...76..340K: Sub-parsec-scale jet-driven water maser with possible gravitational acceleration in the radio galaxy NGC 1052 (2024; agn_and_quasars, nearby_galaxies; observational_alma_primary)
- question: Is the 321-GHz H2O emission in NGC 1052 a maser (brightness temperature, size, variability), and what do its velocity structure, drift and spatial distribution say about the jet-torus region?
- step 3: Measure emission sizes and brightness temperature
  - method: Gaussian fit to visibility amplitude vs uv distance for continuum and blue (1360-1500 km/s) and red (1500-1625 km/s) line components [3.2 Size of emission regions: "We measured sizes of the continuum and line-emitting components by fitting a Gaussian function to visibilities as a function of spatial frequency"]
  - fitting: Most-likelihood best fit with 99% confidence band [3.2 Size of emission regions: "Best and max sizes are derived by the most likelihood and 99% confidence band shown in figure [4](#fig:uvplot)."]
- step 5: Position line components and velocity gradient
  - method: uvmodelfit point-source fits on continuum-subtracted visibilities binned by 5 channels (4.57 km/s); linear regression V_LSR ~ jJ + dD [3.4 Positioning line emitting components: "We performed `uvmodelfit` task in CASA to estimate the positions of line emission source using continuum-subtracted visibilities binned by 5 spectral channels (4.57 km s$^{-1}$)."]
  - software: CASA
  - parameter: detection threshold 3x line image rms; J axis PA=68.35 deg [3.4 Positioning line emitting components: "Threshold for the maser flux density was set to $3\times$ the line image rms"]
  - fitting: linear regression [Results, Positioning line emitting comp…: "We applied linear regression of $V_{\rm LSR} \sim j J + d D$, where $J$ and $D$ are offset along PA=$68^{\circ}.35$ and $-21^{\circ}.65$, respectively, to estimate the velocity gradients"]
- result: Continuum flux density (07-10, 07-24) = 0.624 and 0.704 ± 0.019 and 0.021 Jy [3.3 Continuum images: "increased from $0.624 \pm 0.019$ Jy to $0.704 \pm 0.021$ Jy by $12.8 \pm 4.2$%"]
- result: Maser emitter size = <0.6 ± not stated mas [3.2 Size of emission regions: "allowed us to constrain the size of emission region in $<0.6$ milliarcsec (mas) and the brightness temperature of $T_{\rm B} > 10^6$ K."]
- result: Velocity gradient along jet = -174 ± 19 km/s/mas [5 Summary: "We identified velocity gradient of $-174 \pm 19$ km s$^{-1}$ mas$^{-1}$ along the jet."]
- limitation (authors): Red component decomposition not unique; drift versus growth ambiguous; first epoch had poorer uv coverage [3.1 Line profiles: "The decompositions are not unique, especially in the red component consisting of complex sub-components."]
- not stated (card): Line-free channels / continuum definition for BB4 continuum subtraction; tclean cell size, image size, niter, threshold, mask; Self-calibration solution intervals; Initial values and ranges for Gaussian/Lorentzian nls decomposition; Table of observation log contents (rms values) not in text; Details of the uv-distance Gaussian fitting method and 99% confidence band; 2022-05-12 spectrum from earli…

### 2016ApJ...829L..23B: ALMA-SZ Detection of a Galaxy Cluster Merger Shock at Half the Age of the Universe (2016; galaxy_clusters_and_sz; observational_alma_primary)
- question: Can ALMA SZ measurements detect the pressure discontinuity of a merger shock at the NW radio relic of El Gordo, and what Mach number and relic magnetic field result when combined with Chandra and ATCA data?
- step 3: Fit SZ shock model to ALMA uv-data
  - method: GNFW pressure plus R-H pressure boost at shock radius, fit directly to visibilities by MCMC within CASA [2.3 ALMA-SZ data: "This is done using an MCMC method within CASA and is computationally expensive, due to the large data volume."]
  - software: CASA
  - parameter: Free: pressure amplitude, shock radius, Mach number; slopes consistent with X-ray; outer slope marginalized within 30% [2.3 ALMA-SZ data: "leaving the pressure amplitude, shock radius and the Mach number as free parameters"]
  - assumption: p_down/p_up = (5M^2-1)/4 [2.3 ALMA-SZ data: "$p_{\mathrm{down}}/p_{\mathrm{up (GNFW)}} = (5{\cal M}^2 -1)/4$"]
  - fitting: MCMC [2.3 ALMA-SZ data: "This is done using an MCMC method within CASA"]
  - validation: Mock ALMA observations with M=1, 2, 4 shocks [2.3 ALMA-SZ data: "We make extensive simulations for mock ALMA observations"]
- result: SZ shock radius = 870 ± +14/-13 kpc [3.1 SZ shock modeling: "$r_{\mathrm{sh}}=870^{+14}_{-13}$ kpc"]
- result: Mach number from SZ alone = 1.4 ± +1.2/-0.2 dimensionless [3.1 SZ shock modeling: "${\cal M}= 1.4^{+1.2}_{-0.2}$, supporting ${\cal M}> 1$ at more than $98\%$ confidence"]
- result: Mach number SZ with weak-lensing mass prior = 1.5 ± +0.5/-0.2 dimensionless [3.1 SZ shock modeling: "reduces the errors to ${\cal M}= 1.5^{+0.5}_{-0.2}$"]
- limitation (authors): Short-spacing problem makes Mach number anti-correlated with pressure normalization [2.3 ALMA-SZ data: "its amplitude is anti-correlated with the pressure normalization. This is an inherent limitation of the current ALMA observation"]
- limitation (authors): Pre-shock temperature unconstrained in Chandra data [3 Results and Discussion: "the pre-shock temperature in this high-$z$ object remains unconstrained due to the high background-to-cluster photon ratio"]
- not stated (card): Additional flagging details for the ALMA data; Specifics of the MCMC-in-CASA uv-fitting code, sampler and priors; CASA and CIAO versions (only CALDB 4.7.1 given); CLEAN parameters (cell, size, masking, threshold); GNFW parameter values and priors on amplitude, shock radius, Mach number; Binning of Chandra profile and X-ray temperature fitting details; Priors for the radio/B-field calculation and …

### 2015ApJ...798..124R: ALMA Observations of the Debris Disk around the Young Solar Analog HD 107146 (2015; debris_disks; observational_alma_primary)
- question: What is the radial distribution of mm-sized dust in the HD 107146 debris disk, and is there a gap or dip in the dust surface density?
- step 4: fit disk models to visibilities
  - method: Model image multiplied by Gaussian primary beam (24.3''), Fourier transformed and sampled at observed uv points; chi2 minimised for single power-law, power-law with gap, double power-law [4.2 Models - data comparison: "The model visibilities were obtained through a Fourier transform of the image and sampling the model using the same $(u,v)$ data points in the ALMA observations."]
  - software: emcee
  - parameter: model image 2048x2048 pixels of 0.015''; flux scaled as nu^(2+beta), beta=0.4 [4.2 Models - data comparison: "The model image has a size of 2048x2048 pixel with 0.015$''$ pixels."]
  - assumption: axisymmetric, geometrically and optically thin disk; constant dust opacity across disk [4.1 Debris Disk Model: "Our models consider a debris disk as an axisymmetric, geometrically thin and optically thin layer of solids."]
  - fitting: emcee affine-invariant MCMC, several hundred walkers and iterations; best values are the mode of marginalized posteriors with 68.3% intervals [4.2 Models - data comparison: "For each surface density parameterization, `emcee` was run with several hundreds walkers (see (cite: Foreman:2013)) for several hundreds iterations."]
  - validation: Different walker starting positions tested; residual maps and visibility profiles inspected [4.2 Models - data comparison: "We also ran several trials by either varying or not varying the starting positions of the walkers"]
- result: Gap radius (single power-law with gap) = 80.9 ± +1.8/-2.6 AU [Table 2: "$R_{\rm{gap}}$ \[AU\] | ... | $80.9^{+1.8}_{-2.6}$"]
- result: Gap width = 9.0 ± +1.0/-1.5 AU [5.2 Single power-law with gap: "radial width $\Delta R_{\rm{gap}} = 9.0^{+1.0}_{-1.5}$ AU"]
- result: Single power-law slope p = 0.74 ± +0.06/-0.05 dimensionless [5.1 Single power-law models: "The $p$ value of $0.74^{+0.06}_{-0.05}$ indicates a surface density which is increasing with radius"]
- result: Double power-law R_break = 68.5 ± +6.2/-2.6 AU [5.3 Double power-law: "$R_{\rm{break}} = 68.5^{+6.2}_{-2.6}$ AU"]
- result: Inclination (single power-law) = 20.6 ± 1.9 deg [Table 2: "$i$ \[deg\] | $20.6 \pm 1.9$"]
- result: Dust mass of best-fit models = ≈0.2 ± not stated Earth masses [7 The non-detection of CO: "have a dust mass of $\approx 0.2~M_{\oplus}$"]
- limitation (authors): Data cannot distinguish between gap and double power-law forms; dust opacity degenerate with surface density [5.3 Double power-law: "The ALMA data presented in this paper do not allow us to distinguish between these possible different functional forms"]
- not stated (card): Number of emcee walkers and iterations (only 'several hundreds') and burn-in; Priors and bounds on model parameters; Clean threshold, mask, cell and image size of the CLEAN images; Whether CASA clean or other tools were used for the visibility extraction and weight rescaling in detail; Which spectral windows/channels were used for continuum (line-free channels excluded CO); Exact dust opacity tab…

### 2020ApJ...894...76W: The MESAS Project: ALMA Observations of the F-type Stars γ Lep, γ Vir A, and γ Vir B (2020; stellar_physics, debris_disks; observational_alma_primary)
- question: What are the submm/mm fluxes and chromospheric structure of debris-poor F-type stars, and is there short-term variability or bias for debris disk studies?
- step 2: Measure stellar fluxes
  - method: Point-source uvmodelfit to visibilities per EB [3.1 Visibility model fitting: "obtain the flux using the CASA task *uvmodelfit* and a point source model for all targets"]
  - software: CASA uvmodelfit
  - assumption: Stars are point sources; absolute flux uncertainty ~10% [3.1 Visibility model fitting: "All of the stars observed are effectively point sources given the achieved synthesized beams."]
  - fitting: Iterative chi^2 minimization [3.1 Visibility model fitting: "This approach converges on a minimum $\chi^{2}$ through an iterative procedure."]
- step 3: Characterize background source near gamma Vir
  - method: Point and Gaussian uvmodelfit; Gaussian preferred; spectral index and beta from two bands [3.2 Additional source: "we fit both a point source and Gaussian model to the object with *uvmodelfit* and find it to be more consistent with a Gaussian."]
  - software: CASA uvmodelfit
  - assumption: Rayleigh-Jeans regime, S_nu ∝ nu^(2+beta) [3.2 Additional source: "assuming the object is in the Rayleigh-Jeans regime with $S_\nu \propto \nu^{2+\beta}$"]
  - validation: Compared expected high-z galaxy counts (~0.5 in field) [3.2 Additional source: "meaning the expected number of objects within our ALMA Band 6 field-of-view is about 0.5"]
- step 5: Assess short-term variability
  - method: uvmodelfit applied to each on-source scan (6-8 min between phase calibrations); compare stars with background source [4.2 Potential millimeter wavelength var…: "We can therefore further divide up the observations into increments of $6-8$ minutes between individual phase calibrations"]
  - software: CASA uvmodelfit
  - assumption: Background source has constant flux [3.2 Additional source: "the assumption that it has a relatively constant flux during each EB"]
  - validation: Qualitative comparison of time series [Potential millimeter wavelength variabi…: "While the curves are indeed not flat, they are roughly consistent with the full integrated flux and there is likely no variability at the level of the flux calibrations over the course of the observations."]
- result: gamma Lep flux 0.87 mm = 707 ± 17 (model); 30 obs uJy [Table 1: "| $\gamma$ Lep | 0.87 | 2018 Sep 22 | J0522-3627 | 707 | 17 | 30 | 2.83 |"]
- result: gamma Lep flux 1.29 mm = 345 ± 6 (model); 10 obs uJy [Table 1: "| $\gamma$ Lep | 1.29 | 2018 Sep 28 | J0522-3627 | 345 | 6 | 10 | 2.82 |"]
- result: gamma Vir B flux 1.29 mm (2019 Mar 18) = 356 ± 8 (model) uJy [Table 1: "| $\gamma$ Vir B | 1.29 | 2019 Mar 18 | J1256-0547 | 356 | 8 | 14 | 3.48 |"]
- result: Background source Band 7 flux = 430 ± 25 uJy [3.2 Additional source: "The Band 7 total flux is $430\pm25~\mu \rm Jy$ and the Band 6 total flux is $160\pm16~\mu \rm Jy$."]
- result: Background source Band 6 flux = 160 ± 16 uJy [3.2 Additional source: "The Band 7 total flux is $430\pm25~\mu \rm Jy$ and the Band 6 total flux is $160\pm16~\mu \rm Jy$."]
- result: Background source spectral index = ≈2.5 ± not stated dimensionless [3.2 Additional source: "This corresponds to a spectral index $\alpha\approx 2.5$ and a dust emissivity $\beta\approx 0.5$"]
- limitation (authors): gamma Vir models lack constraints at other wavelengths; temperature minimum cannot be analyzed [4.1 Semi-empirical chromospheric model: "Therefore, it is not possible to perform an analysis of the temperature minimum in these two stars."]
- limitation (authors): Variability at longer timescales cannot be ruled out for gamma Lep [4.2 Potential millimeter wavelength var…: "we cannot rule out the possibility of variability at time periods longer than the length of the EBs."]
- not stated (card): CLEAN mask, niter, cell and image size; Whether pipeline products were used or manually re-imaged; spectral line flagging; uvmodelfit starting parameters; KINICH-PAKAL settings, convergence criteria and weighting of data points; Source of stellar parameters (footnotes a-e); How per-scan time series were binned and uncertainties assigned; Gamma Vir EB combination procedure

### 2025A&A...693A.151M: REsolved ALMA and SMA Observations of Nearby Stars (REASONS): A population of 74 resolved planetesimal belts at millimetre wavelengths (2025; debris_disks, exoplanets; large_program_or_survey)
- question: What are the spatial properties (radius, width, vertical aspect ratio) and evolution of mm-resolved planetesimal belts across a uniformly modelled population of 74 systems?
- step 2: Fit visibilities with belt model
  - method: Radially and vertically Gaussian ring model from RADMC-3D images, Fourier transformed with GALARIO, fit with MCMC [4.2.3 The fitting process: "We then use the GALARIO software package (cite: Tazzari2018) to obtain a Fourier transform of the model image, and sample it at the same u-v locations as the data."]
  - software: MIAO, RADMC-3D, GALARIO, emcee, CASA
  - parameter: h fixed to 0.03 unless vertically constrained; temperature r^-0.5 [4.2.2 The physical model: "In other cases, we fix this value to $h=0.03$, motivated by the aspect ratio of the AU Mic disc (cite: Daley2019)."]
  - assumption: Gaussian radial profile; large grains behave as blackbodies [4.2.2 The physical model: "on the assumption that the large grains probed by millimetre observations are well approximated by blackbodies"]
  - fitting: Affine-invariant emcee v3, uniform priors, likelihood proportional to exp(-chi2/2), walkers = 10x free parameters, >=1000 steps, weight rescaling free [4.2.3 The fitting process: "We ran the MCMC to sample the posterior probability distribution of the parameters using a number of walkers equal to 10 times the number of free parameters"]
  - validation: Residual images and deprojected visibility profiles; 65/74 fit well [4.2.4 Modelling results: "Based on the compatibility of residual images with pure noise, we find that 65/74 belts are fit well by our radially and vertically Gaussian model."]
- result: Radius-luminosity slope alpha = 0.14 ± +0.03/-0.03 dimensionless [5.1: "leads to a slope $\alpha=0.14^{+0.03}_{-0.03}$"]
- result: Intrinsic scatter in R-L relation = 0.44 ± +0.05/-0.04 fraction of radius [5.1: "an intrinsic scatter $f=0.44^{+0.05}_{-0.04}$"]
- result: Median fractional width of belts = 0.71 ± not stated dimensionless [5.2: "with a median fractional width of 0.71"]
- result: Belt aspect ratio range (24 belts) = 0.01-0.3 ± not stated dimensionless [5.4: "We find well-constrained aspect ratios in the range between $\sim$0.01 and 0.3"]
- limitation (authors): Sample biased by flux-density limits; heights may be extracted from azimuthal profile rather than resolved [5.4: "this does not necessarily mean that these belts were all vertically resolved"]
- not stated (card): Per-target weighting, robust and u-v taper values (only on Zenodo); MCMC prior ranges and exact step counts per system; Line-free channels for continuum subtraction/ CO; Details of bias map selection thresholds per wavelength; Exact photometry compilations used in SED fits

### 2024Natur.633..323V: One month convection timescale on the surface of a giant evolved star (2024; evolved_stars, stellar_physics; observational_alma_primary)
- question: What are the size and timescale of convective surface structures on the AGB star R Doradus, as imaged with ALMA at submillimeter wavelengths?
- step 2: Fit stellar disc in visibilities
  - method: uv-fit of a nearly circular disc to the last three epochs combined [Methods: Source properties: "Using a combination of the last three epochs, we fit a nearly circular stellar disc"]
  - software: uvmultifit
  - assumption: top-hat disc profile [Methods: Stellar disc profile: "how well a top-hat shaped stellar disc profile fits the observations"]
  - validation: Radial profile compared with a beam-convolved top-hat model; residuals ~2% of peak [Methods: Stellar disc profile: "with residuals at a level of $\sim 2\%$ of the peak emission"]
- step 3: Spatial PSD of surface structure
  - method: Subtract disc from visibilities, compute |V|^2 in annular uv-distance bins; compare on-source with an off-source PSD at 7 arcsec offset [Methods: Spatial Power Spectral Density…: "We chose an offset of $7$ arcseconds to avoid a contribution to the off-source PSD from the source signal."]
  - software: uvmultifit
  - validation: Off-source PSD identifies correlated noise [Methods: Spatial Power Spectral Density…: "By comparing the on- and off-source PSD we can determine which structures are significant and which are possibly due to correlated noise in the visibilities."]
- result: Dominant structure size = 0.72 ± 0.05 au [abstract: "$0.72\pm0.05$ astronomical units (au)"]
- result: Dominant structure angular size = 13.1 ± 0.6 mas [main text: "$x=13.1\pm0.6$ mas"]
- result: 338 GHz disc radius = 1.64 ± 0.09 au [Methods: Source properties: "$R_{\rm 338GHz} = 1.64\pm0.09$ au"]
- result: Brightness temperature at 338 GHz = 2270 ± 130 K [Methods: Source properties: "$T_b=2270\pm130$ K"]
- result: 338 GHz disc flux density = 521 ± 18 mJy [Methods: Source properties: "$F_{\rm 338GHz}=521\pm18$ mJy"]
- limitation (authors): Observed motions depend on density, temperature, ionisation and velocity changes; velocities are lower limits [main text: "They thus represent a lower limit to the actual gas velocities."]
- not stated (card): tclean parameters (cell, image size, niter, threshold, masking); superuniform weighting parameters (e.g. npixels); which channels/lines were flagged; self-calibration solution intervals; uvmultifit model setup and uv bin widths in PSD; method for deriving half-power radius vs position angle and velocity uncertainty; stellar mass/Teff details for the escape velocity; PSD peak-fitting method

### 2023PSJ.....4..142C: Thermal Properties of the Leading Hemisphere of Callisto Inferred from ALMA Observations (2023; solar_system; observational_alma_primary)
- question: What are the global thermal properties (thermal inertia, emissivity) and local thermal anomalies of Callisto's leading hemisphere at 0.87 mm?
- step 2: disk-integrated flux and Tb
  - method: fit uniform disk to visibilities with uvmodelfit excluding baselines >200 m; invert Planck equation with CMB subtraction [2.2 Data Analysis: "fit with Bessel functions using the CASA task `uvmodelfit` assuming a uniform disk model, fitting to all spectral windows, and by excluding baselines $>$200 m"]
  - software: CASA uvmodelfit
  - assumption: T_cmb = 2.7 K; 5% flux scale error [2.2 Data Analysis: "$T_{cmb}$ is the cosmic microwave background (2.7 K)"]
  - fitting: uniform-disk visibility fit [Methods, Data Analysis: "The visibilities were fit with Bessel functions using the CASA task `uvmodelfit` assuming a uniform disk model, fitting to all spectral windows"]
  - validation: compared with prior disk-integrated measurements [4.1 Disk-Integrated Brightness Temperat…: "Overall, our result agrees well with past work"]
- result: disk-integrated flux density = 8.03 ± 0.40 Jy [4.1 Disk-Integrated Brightness Temperat…: "is 8.03 $\pm$ 0.40 Jy at 343.5 GHz (0.87 mm), which is equivalent to a brightness temperature of 116 $\pm$ 5 K"]
- result: disk-integrated brightness temperature = 116 ± 5 K [4.1 Disk-Integrated Brightness Temperat…: "brightness temperature of 116 $\pm$ 5 K"]
- limitation (authors): cost function formally limited to independent data points [3.1 Two-Component Mixtures: "we note that the cost function is formally limited to data sets with independent data points."]
- limitation (authors): single observation of leading hemisphere only [5 Conclusion: "However, such a hypothesis is difficult to confirm in the context of a single thermal observation."]
- not stated (card): tclean image size, cell size, niter, threshold and masks; startmodel Lambertian disk parameters; intermediate self-cal solints and number of iterations; CASA version; emissivity/thermal model input parameters (density, heat capacity, dielectrics, roughness); exact cost function and chi-squared cutoff implementation; thermophysical model code availability; quasar J1232-0224 role details

### 2025A&A...700A.165B: GAMA 526784: The progenitor of a globular cluster-rich ultra-diffuse galaxy?: II. Molecular gas, neutral gas, and environment (2025; nearby_galaxies, star_formation; observational_alma_primary)
- question: How much molecular (CO) and neutral (HI) gas does the ultra-diffuse galaxy GAMA 526784 contain, and could a nearby companion have shaped its star formation and star clusters?
- step 1: uv-plane CO spectrum and averaged map
  - method: Fit a point-source (PSF) model in the uv-plane at fixed optical centre per channel; average channels around the expected CO frequency [CO(1-0) Emission: "we extracted the CO spectrum by applying the Fourier Transform of a PSF model and looked for a detection around the expected frequency"]
  - software: GILDAS, CASA
  - parameter: Low-res: +-30 km/s (three channels each side); high-res: 10 km/s width [CO(1-0) Emission: "allowing for a velocity width of 30 km s$^{-1}$ up and down, i.e. three channels at each side"]
  - assumption: Galaxy unresolved at ACA resolution; GMCs co-spatial with star clusters and unresolved [CO(1-0) Emission: "GMCs are unresolved at the resolution of our observations and fitting them as point sources"]
  - validation: Image-plane inspection gave the same non-detection [CO(1-0) Emission: "we also inspected the imaging and arrived at the same conclusions, i.e. no CO detection"]
- result: CO(1-0) 5 sigma flux upper limit, galaxy = <=5.80 ± not stated uJy [Table 3: "| GAMA 526784 | $\leq$5.80 |"]
- limitation (authors): Current data cannot distinguish between scenarios [Environment: "Current data cannot definitively distinguish between these scenarios."]
- not stated (card): Star cluster positions (from Paper I) and the optical centre used for the PSF fit; Which spectral windows or channels define the continuum; Conversion details from flux upper limit to L'CO and gas mass (line width, brightness-temperature ratio); GBT baseline order, smoothing width and flux scale; Calibration and flagging details of the pipeline

### 2020ApJ...898...75I: ALMA Observations of Multiple CO and C Lines toward the Active Galactic Nucleus of NGC 7469: An X-Ray-dominated Region Caught in the Act (2020; nearby_galaxies, agn_and_quasars, astrochemistry; observational_alma_primary)
- question: Does the [C I](1-0) to CO/13CO line ratio at ~100 pc scale distinguish the AGN (XDR) from the starburst ring in NGC 7469, and what are the gas conditions and CO/CI-to-H2 conversion factors?
- step 1: Calibrate and image cubes
  - method: CASA pipeline calibration, uv-plane continuum subtraction, concat, clean with Briggs weighting [2 Observations and data reduction: "The continuum emission was identified and subtracted in the $uv$-plane for each visibility set of different array configuration"]
  - software: CASA
  - parameter: robust 0.0 (Bands 6-8); robust 0.5 with outertaper 0.2'' (Band 3); dV = 10 km/s (20 for 13CO) [2 Observations and data reduction: "we created cubes of $^{12}$CO and \[C I\](1–0) lines with a common velocity resolution of $dV = 10$ km s$^{-1}$"]
  - validation: Band 8 position offset (~0.08'') corrected using calibrator [2 Observations and data reduction: "This is due to a phase error in the Band 8 dataset, as confirmed by inspecting the position of a dedicated calibration source (quasar)."]
- limitation (authors): Dominance of H2 in the CND is assumed; HI/HII may contribute [4.2 Impact on H2 mass measurements: "One big assumption is about the dominant phase of the circumnuclear gas in terms of mass."]
- limitation (authors): RADEX assumes single homogeneous medium though real structure is complex; single transition limits Tex [4.1.2 Non-LTE perspective: "we need to assume that all lines observed are emitted from the same volume, although as we revealed in § 3 the real structures are quite complex"]
- not stated (card): Line-free channels used for continuum subtraction and rms; clean threshold, masking, niter and image size; Whether Band 7 compact-configuration data exclusion detail and flagging beyond pipeline; Exact aperture/spectrum extraction procedure and Gaussian-fit initial guesses; 3DBarolo settings (mask, normalization, weighting) beyond ring geometry; MGE fitting details and HST stellar mass profile (d…

### 2014ApJ...797...27F: Revealing H<SUB>2</SUB>D<SUP>+</SUP> Depletion and Compact Structure in Starless and Protostellar Cores with ALMA (2014; star_formation, astrochemistry; observational_alma_primary)
- question: What small-scale structure and H2D+ distribution exist in the Oph A SM1 and SM1N cores, and are they starless or protostellar?
- step 2: Fit Gaussian models to visibilities
  - method: Single 2D Gaussian fit with uvmodelfit to 359 GHz windows [3.1: "we fit both the SM1 and SM1N condensations with single 2D Gaussians in the $uv$-plane using the CASA task *uvmodelfit*."]
  - software: CASA uvmodelfit, Miriad uvamp
  - fitting: least-squares minimization in amplitude and phase [3.1: "This task performs a least-squares minimization of a model to the observed visibilities in amplitude and phase."]
  - validation: Residual images after subtracting best-fit model [3.1: "We then subtracted the best-fit model visibilities from the observed visibilities, and imaged the residuals to determine the quality of the fit."]
- result: SM1 total flux (uv model) = 0.317 ± 0.001 Jy [Table 2: "| SM1 | 16:26:27.86 | -24:23:59.5 | 0.317(1) | 0.314(1) | 0.908(7) | -6(2) |"]
- result: SM1 Gaussian major axis = 0.314 ± 0.001 arcsec [Table 2: "| SM1 | 16:26:27.86 | -24:23:59.5 | 0.317(1) | 0.314(1) | 0.908(7) | -6(2) |"]
- result: SM1N total flux (uv model) = 0.15 ± 0.01 Jy [Table 2: "| SM1N | 16:26:27.20 | -24:23:22.4 | 0.15(1) | 4.2(2) | 0.61(3) | -24(3) |"]
- result: SM1N major axis = 4.2 ± 0.2 arcsec [Table 2: "| SM1N | 16:26:27.20 | -24:23:22.4 | 0.15(1) | 4.2(2) | 0.61(3) | -24(3) |"]
- limitation (authors): Masses uncertain to factors of a few [3.2: "While the uncertainty in the derived masses is thus uncertain to factors of a few"]
- not stated (card): Self-calibration solint and number of iterations for SM1; Cell size, image size, clean masks and thresholds; Multiscale scales for SM1N; Taper parameters for the H2D+ cube; Line-free channels used for continuum subtraction; uvmodelfit starting parameters; Phase centre / reference positions used for uv-averaging bins; ATCA NH3 data and SMA data are unpublished (in preparation)

### 2018AJ....156..164B: Medium-sized Satellites of Large Kuiper Belt Objects (2018; solar_system; observational_alma_primary)
- question: What are the sizes and albedos of Dysnomia (Eris) and Vanth (Orcus), and do they fit the small icy collisional-satellite paradigm?
- step 1: Reduce visibilities and measure flux densities
  - method: Pipeline calibration in CASA, then AIPS; natural-weight imaging; flux by image, CLEAN components, gaussian fit and visibility fit; decorrelation correction from check source [2 Observations: "flux density in the image; flux density in the CLEAN components; fitting a gaussian in the image; and fitting the visibilities directly."]
  - software: CASA, AIPS
  - parameter: Eris visibility fit: slightly limb-darkened disk, radius 1163 km; others point sources [2 Observations: "For Eris, we used a fit of a slightly limb-darkened disk, with radius of 1163 km (cite: 2011_Sicardy)."]
  - validation: Compared the four flux methods; relatively good agreement [2 Observations: "We found relatively good agreement for all of these techniques."]
- limitation (authors): Dysnomia detection is weak and needs robust detection at multiple locations [Discussion: "robust detection at multiple locations are desired"]
- not stated (card): Phase calibrators, flux calibrator, and antenna numbers/baselines; AIPS imaging parameters (cell, image size, clean depth); Decorrelation correction factors per observation; MCMC sampler details, priors, chain lengths; Beaming parameter priors; Distances/heliocentric geometry for thermal model

### 2014A&A...563A.136M: UVMULTIFIT: A versatile tool for fitting astronomical radio interferometric data (2014; instrumentation, other; technical_calibration_or_instrument)
- question: Can a flexible visibility-domain model-fitting library outperform image-plane analysis for sources near or below the resolution limit?
- step 1: Locate sources from continuum channels
  - method: Fit two delta components to line-free channels in one fit (OneFitPerChannel=False), with relative position bounded [3.1.4 Visibility model-fitting. Locatin…: "we select a subset of frequency channels corresponding to continuum emission and fit the data with `OneFitPerChannel`=False"]
  - software: uvmultifit, CASA
  - parameter: PKS 1830-211: relative position bounded within 10 mas of VLBI astrometry [3.2.1 ALMA observations of PKS 1830-211: "we bounded the fit of the relative positions to be within only 10 mas with respect to the VLBI-astrometry results."]
  - fitting: Levenberg-Marquardt or SIMPLEX chi-square minimization [2.2 Model-fitting algorithm: "is performed using either the Levenberg-Marquardt approach (cite: Levenberg) or the SIMPLEX algorithm (cite: Nesa)"]
  - validation: Fitted positions differ by at most about 15 mas from the true ones in simulations [3.1.5 Visibility model-fitting. Recover…: "the positions fitted in continuum mode only differ by about 15 mas (at most) from the true positions of the sources."]
- step 2: Recover per-channel spectra
  - method: Fix positions, fit flux density of each component per channel (OneFitPerChannel=True) [3.1.5 Visibility model-fitting. Recover…: "we only solve for the fluxes of the two delta components at each spectral channel (i.e., we now set `OneFitPerChannel`=True)."]
  - software: uvmultifit
  - validation: Fitting errors show no line features; typical error ~0.5 mJy [3.1.5 Visibility model-fitting. Recover…: "The typical fitting error is around 0.5 mJy for both components."]
- limitation (authors): Mosaic fits require components small relative to the primary beam; no line-profile kinematics in the models [2.2 Model-fitting algorithm: "the size of each individual component must be small compared with the telescope’s primary beam"]
- not stated (card): Calibration and CASA version for the PKS 1830-211 ALMA data; Line-free channel ranges for the PKS 1830-211 continuum fit; Initial guesses and fitted flux values for PKS 1830-211; uvmultifit version and exact code for reproduction; Random seed for the synthetic spectra

### 2014ApJ...792L...2C: Mapping the Release of Volatiles in the Inner Comae of Comets C/2012 F6 (Lemmon) and C/2012 S1 (ISON) Using the Atacama Large Millimeter/Submillimeter Array (2014; solar_system; observational_alma_primary)
- question: Where are HCN, HNC and H2CO released in the inner comae of comets Lemmon and ISON (nucleus vs distributed source)?
- step 3: Fit visibility amplitudes with Haser model
  - method: Model visibility amplitudes with Q and Lp free; least squares on real parts [Locations of molecular production/relea…: "Goodness of fit was determined by minimizing the sum of the squares of the differences between the real parts of the observed and modeled visibility amplitudes."]
  - parameter: v = 1.0 km/s (ISON), 0.7 km/s (Lemmon) from HCN HWHM [Locations of molecular production/relea…: "Respective outflow velocities of $1.0$ km $\rm{s}^{-1}$ and $0.7$ km $\rm{s}^{-1}$ for ISON and Lemmon were obtained from the HWHM of the HCN lines."]
  - assumption: T=90 K (ISON), 55 K (Lemmon); excitation by H2O and electron collisions and solar IR pumping [Locations of molecular production/relea…: "The molecular excitation calculation considers collisions with H$_2$O and electrons, and pumping by Solar infrared radiation."]
  - fitting: Chi-square-like minimisation, Q and Lp free [Locations of molecular production/relea…: "with $Q$ and $L_p$ as free parameters"]
- result: HCN Q, Lemmon = 2.3e26 ± ~10% s^-1 [Table 1: "HCN | $4-3$ | 354.505 | 42.5 | 8.55(9) | 2.3"]
- result: HCN Q, ISON = 3.5e26 ± ~10% s^-1 [Locations of molecular production/relea…: "For ISON, our value of $3.5\times10^{26}$ s$^{-1}$ on 2013 November 17"]
- result: H2CO Lp, ISON = 280 (+50/-50) ± 1 sigma km [Table 1: "$280^{+50}_{-50}$"]
- result: H2CO Lp, Lemmon = 1200 (+1200/-400) ± 1 sigma km [Table 1: "$1200^{+1200}_{-400}$"]
- result: HNC Lp, ISON = 700 (+1100/-400) ± 1 sigma km [Table 1: "$700^{+1100}_{-400}$"]
- result: Q(HNC)/Q(HCN) ISON = 34% ± not stated percent [HCN and HNC: "Our $Q({\rm HNC})/Q({\rm HCN})$ ratio of 34% is somewhat larger than the value of 18%"]
- result: Q(HNC)/Q(HCN) Lemmon = about 0.4% ± not stated percent [HCN and HNC: "The $Q({\rm HNC})/Q({\rm HCN})$ ratio in comet Lemmon was only about 0.4%"]
- limitation (authors): Lack of short baselines prevents ruling out additional H2CO sources with sizes >= 5 arcsec [H2CO: "Due to the lack of short baselines, our ALMA data cannot rule out the presence of additional H$_2$CO sources with angular sizes $\gtrsim5''$."]
- not stated (card): Cell size and image size; Cube/channel velocity ranges for line integration; Continuum channel selection and continuum subtraction; Quasar calibrator names; Visibility binning and uv-range and phase centre handling in the model; Excitation model code, collision rates, and electron density; Photodissociation rates adopted for HNC and H2CO daughters; Noise treatment/fitting of real visibility ampli…

### 2020A&A...637A...7M: Detection of deuterated molecules, but not of lithium hydride, in the z = 0.89 absorber toward PKS 1830-211 (2020; astrochemistry, high_z_galaxies; observational_alma_primary)
- question: Are deuterated molecules (ND, NH2D, HDO) and lithium hydride detectable in the z=0.89 absorber toward PKS 1830-211, and what are their abundance ratios?
- step 1: Extract normalized spectra
  - method: Fit two point sources to visibilities with UVMULTIFIT; normalize Stokes I spectra to continuum and average the two executions [2 Observations: "The spectra, extracted from Stokes I data, were then normalized to the continuum level and averaged."]
  - software: CASA, UVMULTIFIT
  - validation: NE image spectra used as monitor to discard Galactic, atmospheric lines or bandpass ripples [2 Observations: "the spectra extracted from the NE image serve as a monitor to control the quality of the spectral bandpass"]
- limitation (authors): Non-simultaneous XD and XH observations and time variability; high uncertainties [Summary and conclusions: "Measurements of deuterium fractionation toward PKS 1830$-$211 could be improved by simultaneous observations of the XD and XH isotopologues"]
- limitation (authors): Assumed covering factor of 1 [3.1: "We further assume that the absorbing gas completely and uniformly covers the background continuum emission from the quasar"]
- not stated (card): Line-free channels and continuum normalization procedure; Gaussian fitting code and fitting/error method; Exact CASA version and bandpass/flux calibrator flux scale; Velocity-resolution/Hanning details per project; Details of the time-variation correction applied to final ratios; Phase center/coordinates of target; Exact RADEX input parameters beyond range

### 2014A&A...566A.112M: An ALMA Early Science survey of molecular absorption lines toward PKS 1830-211. Analysis of the absorption profiles (2014; milky_way_ism, astrochemistry, nearby_galaxies; observational_alma_primary)
- question: What is the structure, velocity-component content, chemical inventory and time variability of molecular absorption along the NE and SW lines of sight of the z=0.89 absorber toward PKS 1830-211?
- step 1: Extract NE and SW spectra
  - method: Fit two point-like sources to visibilities with uvmultifit per channel; solve NE flux and SW/NE ratio ('self-bandpass'); apply cvel Doppler correction [2 Observations and data reduction: "solved, on a spectral channel basis, for the flux density of the NE image and for the flux ratio SW/NE."]
  - software: CASA, uvmultifit
  - validation: Epochs' spectra averaged after checking profiles unaffected by variations [2 Observations and data reduction: "we averaged the extracted spectra instead, after checking that the absorption profiles were not significantly affected by time variations"]
- limitation (authors): CO and C I column densities highly uncertain in SW wings and NE [4.4: "The derived column densities and abundances of CO and C I are highly uncertain in the wings of the SW absorption and toward the NE image"]
- not stated (card): Exact VLBI relative positions of NE and SW components; RADEX input parameters used to derive alpha for CO and C I; Self-bandpass channel selection (line-free channels); CASA version; Hanning smoothing details and time-averaging weights for combined spectra; Method for Gaussian fit and hfs deconvolution of CH

### 2020A&A...636A..62K: Investigating the connection between γ-ray activity and the relativistic jet in 3C 273 during 2015-2019 (2020; agn_and_quasars; multi_facility_alma_minor)
- question: What is the origin of the 2015-2019 gamma-ray outbursts of 3C 273 and how do they connect to the parsec-scale jet?
- step 3: Analyze 43 GHz VLBA jet structure
  - method: Circular Gaussian components fitted in visibility domain; polarization maps; proper motions of the peak [3.4 Parsec-scale jet: "the structure of the jet was represented by a number of two-dimensional circular Gaussians fitted to the visibility domain."]
  - software: Difmap
  - parameter: 10% flux accuracy; position error ~1/10 beam; polarization threshold 9 sigma [2.3 VLBA 43 GHz: "We consider a conservative accuracy of flux densities of 10%."]
- result: Apparent speed after 2016 outburst = ~6.0 c ± not stated c [3.4 Parsec-scale jet: "The proper motion of this displacement is about 0.59 mas/year which corresponds to an apparent speed of $\sim$6.0 $c$"]
- result: S1 brightness temperature peak = 2.3e12 ± not stated K [4.2: "$S1$ reaches $2.3\times10^{12}$ K"]
- limitation (authors): Photon index uncertainties too large for quantitative analysis [3.2: "Overall, the uncertainties of the photon indices are too large for a meaningful quantitative analysis."]
- not stated (card): ALMA flux calibration and which calibrators/frequencies per epoch; Exact ALMA light-curve data table; Fermi-LAT spectral-fit details beyond the standard recipe; Gaussian model-fit parameters (in an appendix not in the text)

### 2016A&A...593A..61M: Dual differential polarimetry. A technique to recover polarimetric information from dual-polarization observations (2016; instrumentation, agn_and_quasars; technical_calibration_or_instrument)
- question: Can polarimetric information of resolved sources be recovered from dual-polarization (XX, YY only) interferometric data using Earth-rotation synthesis of the parallactic angle?
- step 2: Fit component fluxes per scan in XX and YY
  - method: Visibility fitting of fixed-position CLEAN components, only flux densities free, per parallactic angle scan [Extended polarized emission: "The positions of all the components were fixed, and we only fit the flux densities."]
  - software: uvmultifit
  - fitting: least squares, linear in visibility space [Implementation of differential polarime…: "only the flux densities of the source components are fitted at each snapshot (so that the fitted source model is fully linear in visibility space)"]
- limitation (authors): Differential RM imaging with polarized fiducial element can be biased by up to ~30%. [Bias in the $RM$ differential imaging: "the bias can be as large as $\sim30$%, even with wide fractional bandwidths"]
- not stated (card): CLEAN parameters (niter, threshold, masks) for simulations and 3C 286; Scan/time binning used to define constant parallactic angle; Noise levels in simulations; In-house modified simobserve not available; Details of the fit initial values and uncertainties for the PKS 1830-211 reanalysis; Corrected feed angles and spectral windows/epochs used in reanalysis

### 2018ApJ...865...37M: Multiple Rings in the Transitional Disk of GM Aurigae Revealed by VLA and ALMA (2018; protoplanetary_disks; observational_alma_primary)
- question: What is the radial distribution of large dust grains in the transitional disk of GM Aur at 0.9 mm and 7 mm, and does it contain multiple rings?
- step 3: Fit Gaussian-ring surface brightness model to deprojected visibilities
  - method: Hankel transform of sum of Gaussian rings fitted to real part of deprojected visibilities; 3 Gaussians for ALMA, 2 for VLA [4.1 Surface Brightness Profile Model: "directly fitting an analytical model of the surface brightness profile of the disk to the real part of deprojected visibilities"]
  - software: emcee
  - parameter: Free: i, PA, dRA, dDEC, and a_i, sigma_i, x_i per ring [4.1 Surface Brightness Profile Model: "the free parameters of our model are the inclination, PA, offsets in RA and DEC, and $a_i$, $\sigma_i$, and $x_i$ for each Gaussian ring"]
  - assumption: Axisymmetric emission [4.1 Surface Brightness Profile Model: "If we assume that the emission is axisymmetric"]
  - fitting: emcee affine-invariant ensemble MCMC; chains initialized around Levenberg-Marquardt best fit; flat priors for ALMA; Gaussian priors from ALMA posteriors for VLA; 30000 iterations, last 5000 used [Markov Chain Monte Carlo runs: "We ran the MCMC for 30000 iterations to assure that the chains had converged. The last 5000 iterations were used to obtain the posteriors"]
  - validation: Third Gaussian added when two failed to reproduce second visibility minimum at ~600 kλ [4.1 Surface Brightness Profile Model: "it failed to reproduce the second minimum in the negative visibilities at $\sim600$ k$\lambda$"]
- step 4: Physical DIAD disk model fit to SED, VLA and ALMA
  - method: Grids of DIAD models; best fit chosen by min chi2, visual inspection and iterative refinement; epsilon_mid modulated by factor delta in radial ranges; model visibilities with observed uv coverage, residuals imaged [4.2.1 Modeling Procedure: "we ran a number of grids of models and found the best-fit parameters by a combination of model selection based on minimum $\chi^2$, visual inspection, and successive refinement of the parameters of the grids"]
  - software: DIAD, CASA
  - parameter: Mdot fixed at 7.8e-9 Msun/yr; alpha varied 0.0001-0.01; Rwall 25-40 au; mid amax 1 mm-2.5 cm; eps_atm 0.001-0.8; Rdisk 150-300 au [4.2.1 Modeling Procedure: "we decided to fix $\dot{M}$ to an average value of $7.8\times10^{-9}$ $M_{\odot}$ yr$^{-1}$, and we varied $\alpha$ between 0.0001 and 0.01"]
  - assumption: Dust-to-gas ratio 0.01; distance 160 pc; inclination and PA fixed from step 3 [4.2 Physical Disk Model: "We assume a fixed “standard" dust-to-gas mass ratio of 0.01."]
  - fitting: Grid search, not MCMC or Levenberg-Marquardt, due to computational cost [4.2.1 Modeling Procedure: "This prevents us from using common algorithms or statistical methods, such as Levenberg-Marquardt $\chi^2$ minimization or MCMC"]
  - validation: Iterated until SED fit good and VLA/ALMA image residuals below ~3 sigma [4.2.1 Modeling Procedure: "ensuring that the residuals in the VLA and ALMA images were below $\sim3\sigma$"]
- result: Disk inclination = 52.77 ± +0.05/-0.04 deg [4.1 Surface Brightness Profile Model: "we find an inclination of $52.77^{\circ} ~^{+0.05}_{-0.04}$"]
- result: Disk position angle = 56.45 ± +0.06/-0.05 deg [4.1 Surface Brightness Profile Model: "a PA of $56.45^{\circ}~^{+0.06}_{-0.05}$"]
- result: Inner ring radius x1 at 0.9 mm = 42.5 ± ±0.2 au [4.1 Surface Brightness Profile Model: "than at 0.9 mm ($x_1=42.5\pm0.2$ au)"]
- result: Inner ring radius x1 at 7 mm = 39 ± ±1 au [4.1 Surface Brightness Profile Model: "smaller at 7 mm ($x_1=39\pm1$ au)"]
- result: Second ring radius x2 at 0.9 mm = 83.4 ± ±0.6 au [Table 1: "$x_{2}$ | $0\rlap.''521^{+0\rlap.''004}_{-0\rlap.''004}$ ($83.4^{+0.6}_{-0.6}$ au)"]
- result: Third component x3 at 0.9 mm = 149 ± ±1 au [Table 1: "$x_{3}$ | $0\rlap.''934^{+0\rlap.''006}_{-0\rlap.''006}$ ($149^{+1}_{-1}$ au)"]
- result: Dust mass in DIAD model = 2.0 ± not stated M_Jup [4.2.2 Model Results: "The dust mass ($M^{\rm{dust}}_{\rm{disk}}$) in our disk model is $2.0~M_{J}$."]
- result: Total disk mass (assuming gas-to-dust 100) = 200 ± not stated M_Jup [4.2.2 Model Results: "this implies a total disk mass of $200~M_{J}$"]
- result: Best-fit alpha = 0.0012 ± not stated dimensionless [Table 2: "$\alpha$ | 0.0012"]
- limitation (authors): Mdot and alpha degenerate; other combinations may fit; no MCMC uncertainties on the physical model [4.2.1 Modeling Procedure: "other models with similar disk masses but different values of $\alpha$ and $\dot{M}$ may also result in satisfactory fits"]
- limitation (authors): VLA data sensitivity limited; asymmetry and cavity difference low significance [3 Results: "both the C configuration and B configuration images of the 7 mm emission are probably sensitivity limited"]
- not stated (card): Self-calibration solution intervals, number of rounds and reference; Line-free channel selection for the line SPWs; CLEAN masks, image size, cell size and number of iterations/threshold; Prior ranges of the flat priors and MCMC walker count and initial scatter; Uvrange/binning of visibilities used in the fit; DIAD code availability and grid ranges/steps; exact chi2 definition; Dust opacity detail…

### 2019MNRAS.485.2092C: Suppressed CO emission and high G/D ratios in z = 2 galaxies with sub-solar gas-phase metallicity (2019; high_z_galaxies, galaxy_clusters_and_sz; observational_alma_primary)
- question: How do molecular gas, dust and star formation relate in sub-solar metallicity galaxies at z~2, and how do alpha_CO and G/D depend on metallicity?
- step 2: Measure CO line fluxes and stack
  - method: Point-source fits in uv plane at optical positions, visibilities collapsed over Halpha-derived 90% flux width; weighted mean stack [2.2 CO spectroscopy and dust continuum …: "Line fluxes were measured directly in the uv-visibility plane with the GILDAS task `uv_fit`."]
  - software: GILDAS
  - parameter: Stack velocity width 753±22 km/s; errors scaled so Var(S/sigma)=1 in line-free channels [3.2: "calculate the stacked line fluxes over the mean FWZP linewidth of the individual galaxies, $\Delta$v=753$\pm$22kms$^{-1}$"]
  - assumption: Galaxies unresolved (PSF response) [2.2 CO spectroscopy and dust continuum …: "all spectra were extracted assuming a point spread function (PSF) response"]
  - validation: MCMC redshift displacement and linewidth resampling show negligible effect [3.2: "The effect of this on the output stacked line fluxes is negligible."]
- step 3: Measure continuum, dust masses and stack
  - method: 870um fluxes with GALFIT on dirty images; 2mm in uv plane; flux converted to Md with Magdis template; weighted combination; image-plane stack of dust mass maps [3.3 Dust continuum emission: "All of these individual dust maps were then stacked in the image plane, by performing a weighted co-add of the images at each pixel position."]
  - software: GALFIT, GILDAS
  - parameter: <U>=22; L_IR/Md factor 125; 0.15 dex systematic [3.3 Dust continuum emission: "our assumed value of $\langle$U$\rangle$=22"]
  - assumption: Dust temperature as in z=2 MS template [3.3 Dust continuum emission: "As we cannot constrain the temperature of the dust with these data"]
  - validation: CASA, GILDAS and GALFIT fluxes previously verified consistent [2.2 CO spectroscopy and dust continuum …: "continuum fluxes measured with Common Astronomy Software Applications"]
- result: Stacked CO[4-3] flux = <47 ± 3 sigma limit mJy km/s [3.2: "We therefore place a 3$\sigma$ upper limit on the stacked CO[4-3] line flux of $<$47mJy kms$^{-1}$"]
- result: Stacked CO[1-0] flux = <20 ± 3 sigma limit mJy km/s [3.2: "In the stacked CO[1-0] spectrum, we find a 3$\sigma$ upper limit of $<$20mJy kms$^{-1}$."]
- result: Stacked dust mass = <7.4e7 ± 3 sigma limit Msun [3.3 Dust continuum emission: "M$_{d}<$7.4$\times$10$^{7}$ M$_{\odot}$"]
- limitation (authors): Gas masses rely on assumed MS SFE; effect of MS offset cannot be dissected with five galaxies [4.2.2: "the effect of main-sequence offset on ISM scaling relations cannot be dissected with the number of galaxies studied in this paper"]
- not stated (card): Calibration details, CASA version, imaging parameters (weighting, cleaning) for ALMA/VLA data (deferred to Coogan 2018); Spectral channel widths and line-free channel selection; Exact SFE prescription parameters and Sargent 2014 equation 5 values; GILDAS uv_fit settings and neighbour source models; GALFIT setup for 870um mosaic

## All papers in this technique

- 2012ApJ...757..129R (2012): Kinematics of the CO Gas in the Inner Regions of the TW Hya Disk
- 2013ApJ...762L..21M (2013): Millimeter Emission Structure in the First ALMA Image of the AU Mic Debris Disk
- 2013ApJ...765L..14Q (2013): First Detection of c-C<SUB>3</SUB>H<SUB>2</SUB> in a Circumstellar Disk
- 2013ApJ...774...16R (2013): A Spatially Resolved Vertical Temperature Gradient in the HD 163296 Disk
- 2013ApJ...777L..25M (2013): ALMA Continuum Observations of a 30 Myr Old Gaseous Debris Disk around HD 21997
- 2013Sci...341..630Q (2013): Imaging of the CO Snow Line in a Solar Nebula Analog
- 2014A&A...562A..67G (2014): ALMA reveals a warm and compact starburst around a heavily obscured supermassive black hole at z = 4.75
- 2014A&A...563A.136M (2014): UVMULTIFIT: A versatile tool for fitting astronomical radio interferometric data
- 2014A&A...566A.112M (2014): An ALMA Early Science survey of molecular absorption lines toward PKS 1830-211. Analysis of the absorption profiles
- 2014A&A...566L...6M (2014): Detection of chloronium and measurement of the <SUP>35</SUP>Cl/<SUP>37</SUP>Cl isotopic ratio at z = 0.89 toward PKS 1830-211
- 2014A&A...570L..14R (2014): The wonderful complexity of the Mira AB system
- 2014ApJ...783L..13P (2014): Large-scale Asymmetries in the Transitional Disks of SAO 206462 and SR 21
- 2014ApJ...787...42C (2014): An ALMA Continuum Survey of Circumstellar Disks in the Upper Scorpius OB Association
- 2014ApJ...791...20R (2014): Brown Dwarf Disks with ALMA
- 2014ApJ...791L...6W (2014): ALMA Hints at the Presence of two Companions in the Disk around HD 100546
- 2014ApJ...792L...2C (2014): Mapping the Release of Volatiles in the Inner Comae of Comets C/2012 F6 (Lemmon) and C/2012 S1 (ISON) Using the Atacama Large Millimeter/Su…
- 2014ApJ...796...82Z (2014): Spectral and Morphological Analysis of the Remnant of Supernova 1987A with ALMA and ATCA
- 2014ApJ...797...27F (2014): Revealing H<SUB>2</SUB>D<SUP>+</SUP> Depletion and Compact Structure in Starless and Protostellar Cores with ALMA
- 2015A&A...577L...4V (2015): Resolving the stellar activity of the Mira AB binary with ALMA
- 2015A&A...582L...4M (2015): Detection of extragalactic argonium, ArH<SUP>+</SUP>, toward PKS 1830-211
- 2015A&A...583A..66H (2015): Probing the final stages of protoplanetary disk evolution with ALMA
- 2015ApJ...798...85P (2015): CO Gas Inside the Protoplanetary Disk Cavity in HD 142527: Disk Structure from ALMA
- 2015ApJ...798..124R (2015): ALMA Observations of the Debris Disk around the Young Solar Analog HD 107146
- 2015ApJ...798L..23K (2015): An ALMA Disk Mass for the Candidate Protoplanetary Companion to FW Tau
- 2015ApJ...808...36M (2015): New Measurements of the Radio Photosphere of Mira Based on Data from the JVLA and ALMA
- 2015ApJ...808..102K (2015): Resolving Protoplanetary Disks at Millimeter Wavelengths with CARMA
- 2015ApJ...810..133I (2015): Compact Starbursts in z ∼ 3-6 Submillimeter Galaxies Revealed by ALMA
- 2015ApJ...810L...7V (2015): A Concentration of Centimeter-sized Grains in the Ophiuchus IRS 48 Dust Trap
- 2015ApJ...811...39I (2015): ALMA Observations of the Submillimeter Dense Molecular Gas Tracers in the Luminous Type-1 Active Nucleus of NGC 7469
- 2015ApJ...811..124S (2015): Sub-kiloparsec Imaging of Cool Molecular Gas in Two Strongly Lensed Dusty, Star-forming Galaxies
- 2015ApJ...811L...3T (2015): SXDF-ALMA 1.5 arcmin<SUP>2</SUP> Deep Survey: A Compact Dusty Star-forming Galaxy at z = 2.5
- 2015ApJ...812L..23S (2015): A Higher Efficiency of Converting Gas to Stars Pushes Galaxies at z ∼ 1.6 Well Above the Star-forming Main Sequence
- 2015ApJ...813...99F (2015): Weak Turbulence in the HD 163296 Protoplanetary Disk Revealed by ALMA CO Observations
- 2015MNRAS.453L..83M (2015): ALMA and Herschel reveal that X-ray-selected AGN and main-sequence galaxies have different star formation rate distributions
- 2016A&A...586A..45S (2016): Star formation efficiency along the radio jet in Centaurus A
- 2016A&A...586A..99H (2016): Steepening of the 820 μm continuum surface brightness profile signals dust evolution in TW Hydrae's disk
- 2016A&A...586L...1G (2016): The shadow of the Flying Saucer: A very low temperature for large dust grains
- 2016A&A...589L...5M (2016): Detection of extragalactic CF<SUP>+</SUP> toward PKS 1830-211. Chemical differentiation in the absorbing gas
- 2016A&A...591A..73G (2016): ALMA finds dew drops in the dusty spider's web
- 2016A&A...591A.108O (2016): Azimuthal asymmetries in the debris disk around HD 61005. A massive collision of planetesimals?
- 2016A&A...593A..61M (2016): Dual differential polarimetry. A technique to recover polarimetric information from dual-polarization observations
- 2016A&A...595L...4L (2016): Hot methanol from the inner region of the HH 212 protostellar system
- 2016A&A...596A..75S (2016): Characterizing elusive, faint dusty star-forming galaxies: a lensed, optically undetected ALMA galaxy at z 3.3
- 2016A&A...596A..88L (2016): ALMA observations of the <ASTROBJ>Th 28</ASTROBJ> protostellar disk. A new example of counter-rotation between disk and optical jet
- 2016ApJ...816...27S (2016): Resolved Millimeter-wavelength Observations of Debris Disks around Solar-type Stars
- 2016ApJ...818...45S (2016): The Inner Debris Structure in the Fomalhaut Planetary System
- 2016ApJ...818..156C (2016): A Disk-based Dynamical Constraint on the Mass of the Young Binary DQ Tau
- 2016ApJ...818L..16Z (2016): On the Commonality of 10-30 AU Sized Axisymmetric Dust Structures in Protoplanetary Disks
- 2016ApJ...819..102V (2016): Dust Masses of Disks around 8 Brown Dwarfs and Very Low-mass Stars in Upper Sco OB1 and Ophiuchus
- 2016ApJ...823L..18H (2016): Evidence for a CO Desorption Front in the Outer AS 209 Disk
- 2016ApJ...828...25L (2016): Debris Disks in the Scorpius-Centaurus OB Association Resolved by ALMA
- 2016ApJ...828...46A (2016): ALMA Survey of Lupus Protoplanetary Disks. I. Dust and Gas Masses
- 2016ApJ...829....6W (2016): ALMA Observations of HD 141569’s Circumstellar Disk
- 2016ApJ...829L..23B (2016): ALMA-SZ Detection of a Galaxy Cluster Merger Shock at Half the Age of the Universe
- 2016ApJ...833L...6C (2016): ALMA Reveals Potential Localized Dust Enrichment from Massive Star Clusters in II Zw 40
- 2016MNRAS.458L..29C (2016): A ring-like concentration of mm-sized particles in Sz 91
- 2016MNRAS.459.4518H (2016): The detection of dust around NN Ser
- 2016MNRAS.460.2933M (2016): Exocometary gas in the HD 181327 debris ring
- 2016MNRAS.462L.101A (2016): Dipper discs not inclined towards edge-on orbits
- 2016Natur.535..258C (2016): Imaging the water snow-line during a protostellar outburst
- 2016PASJ...68...88K (2016): The Sunyaev-Zel'dovich effect at 5″: RX J1347.5-1145 imaged by ALMA
- 2017A&A...597A..32V (2017): Cavity and other radial substructures in the disk around HD 97048
- 2017A&A...597A..41G (2017): The ALMA Frontier Fields Survey. I. 1.1 mm continuum detections in Abell 2744, MACS J0416.1-2403 and MACS J1149.5+2223
- 2017A&A...599A.134S (2017): The ALMA Redshift 4 Survey (AR4S). I. The massive end of the z = 4 main sequence of galaxies
- 2017A&A...601A...7F (2017): SPHERE/SHINE reveals concentric rings in the debris disk of HIP 73145
- 2017A&A...602L..10O (2017): The inhomogeneous submillimeter atmosphere of Betelgeuse
- 2017A&A...603L...6H (2017): Direct evidence of multiple reservoirs of volatile nitrogen in a protosolar nebula analogue
- 2017A&A...605A..21C (2017): Increased H<SUB>2</SUB>CO production in the outer disk around HD 163296
- 2017A&A...605A..28D (2017): The extended molecular envelope of the asymptotic giant branch star π<SUP>1</SUP> Gruis as seen by ALMA. I. Large-scale kinematic structure…
- 2017A&A...606A.109M (2017): Detection of CH<SUP>+</SUP>, SH<SUP>+</SUP>, and their <SUP>13</SUP>C- and <SUP>34</SUP>S-isotopologues toward PKS 1830-211
- 2017A&A...607A..55V (2017): An 80 au cavity in the disk around HD 34282
- 2017A&A...608A..96L (2017): The ortho-to-para ratio of H<SUB>2</SUB>Cl<SUP>+</SUP>: Quasi-classical trajectory calculations and new simulations in light of new observa…
- 2017AJ....153..233F (2017): ALMA Observations of Asymmetric Molecular Gas Emission from a Protoplanetary Disk in the Orion Nebula
- 2017AJ....153..240A (2017): An ALMA Survey of Protoplanetary Disks in the σ Orionis Cluster
- 2017AJ....154...11H (2017): An Updated 2017 Astrometric Solution for Betelgeuse
- 2017AJ....154..225S (2017): ALMA 1.3 mm Map of the HD 95086 System
- 2017ApJ...834..135T (2017): Bulge-forming Galaxies with an Extended Rotating Disk at z ~ 2
- 2017ApJ...834..178Y (2017): Signs of Early-stage Disk Growth Revealed with ALMA
- 2017ApJ...836..223W (2017): An ALMA and MagAO Study of the Substellar Companion GQ Lup B*
- 2017ApJ...839...43O (2017): H<SUB>2</SUB>CO Distribution and Formation in the TW HYA Disk
- 2017ApJ...839...99P (2017): A Multi-wavelength Analysis of Dust and Gas in the SR 24S Transition Disk
- 2017ApJ...840...23L (2017): A Multi-ringed, Modestly Inclined Protoplanetary Disk around AA Tau
- 2017ApJ...840L..12S (2017): WL 17: A Young Embedded Transition Disk
- 2017ApJ...841L..25T (2017): Rotating Starburst Cores in Massive Galaxies at z = 2.5
- 2017ApJ...842....8M (2017): A Complete ALMA Map of the Fomalhaut Debris Disk
- 2017ApJ...843...18V (2017): Quasar Feedback in the Ultraluminous Infrared Galaxy F11119+3257: Connecting the Accretion Disk Wind with the Large-scale Molecular Outflow
- 2017ApJ...843..150F (2017): A Three-dimensional View of Turbulence: Constraints on Turbulent Motions in the HD 163296 Protoplanetary Disk Using DCO<SUP>+</SUP>
- 2017ApJ...844..158S (2017): Dynamical Masses of Low-mass Stars in the Taurus and Ophiuchus Star-forming Regions
- 2017ApJ...845..138S (2017): Gas Dynamics of a Luminous z = 6.13 Quasar ULAS J1319+0950 Revealed by ALMA High-resolution Observations
- 2017ApJ...845..170B (2017): ALMA Observations of Circumnuclear Disks in Early-type Galaxies: <SUP>12</SUP>CO(2-1) and Continuum Properties
- 2017ApJ...846..108C (2017): A Spatially Resolved Study of Cold Dust, Molecular Gas, H II Regions, and Stars in the z = 2.12 Submillimeter Galaxy ALESS67.1
- 2017ApJ...846L..14S (2017): Massive Quenched Galaxies at z ∼ 0.7 Retain Large Molecular Gas Reservoirs
- 2017ApJ...846L..26W (2017): An ALMA Dynamical Mass Estimate of the Proposed Planetary-mass Companion FW Tau C
- 2017ApJ...849...56A (2017): ALMA Observations of the Protostar L1527 IRS: Probing Details of the Disk and the Envelope Structures
- 2017ApJ...850...54C (2017): ALMA CO(3-2) Observations of Star-forming Filaments in a Gas-poor Dwarf Spheroidal Galaxy
- 2017ApJ...850...83F (2017): Demonstrating a New Census of Infrared Galaxies with ALMA (DANCING-ALMA). I. FIR Size and Luminosity Relation at z = 0-6 Revealed with 1034…
- 2017ApJ...851...85B (2017): Measurement of Circumstellar Disk Sizes in the Upper Scorpius OB Association with ALMA
- 2017ApJ...851L..23C (2017): ALMA Observations of Elias 2-24: A Protoplanetary Disk with Multiple Gaps in the Ophiuchus Molecular Cloud
- 2017MNRAS.465.2595M (2017): ALMA observations of the η Corvi debris disc: inward scattering of CO-rich exocomets by a chain of 3-30 M<SUB>⊕</SUB> planets?
- 2017MNRAS.465.4390B (2017): The discovery of gas-rich, dusty starbursts in luminous reddened quasars at z ∼ 2.5 with ALMA
- 2017MNRAS.466..138K (2017): A merger in the dusty, z = 7.5 galaxy A1689-zD1?
- 2017MNRAS.466.4201W (2017): 1.3-mm ALMA observations of the Fomalhaut debris system
- 2017MNRAS.469.4683C (2017): ALMA constraints on star-forming gas in a prototypical z = 1.5 clumpy galaxy: the dearth of CO(5-4) emission from UV-bright clumps
- 2017NatAs...1E.130Z (2017): Mass inventory of the giant-planet formation zone in a solar nebula analogue
- 2018A&A...610A..24F (2018): ALMA continuum observations of the protoplanetary disk AS 209. Evidence of multiple gaps opened by a single planet
- 2018A&A...613A..34P (2018): ALMA view of RX J1131-1231: Sub-kpc CO (2-1) mapping of a molecular disk in a lensed star-forming quasar host galaxy
- 2018A&A...614A.106C (2018): Probing midplane CO abundance and gas temperature with DCO<SUP>+</SUP> in the protoplanetary disk around HD 169142
- 2018A&A...616A..23D (2018): The evolving jet spectrum of the neutron star X-ray binary Aql X-1 in transitional states during its 2016 outburst
- 2018A&A...616A..88V (2018): V1094 Scorpii: A rare giant multi-ringed disk around a T Tauri star
- 2018A&A...616A.110E (2018): Starbursts in and out of the star-formation main sequence
- 2018A&A...616L...3B (2018): High-resolution observations of the symbiotic system R Aqr. Direct imaging of the gravitational effects of the secondary on the stellar wind
- 2018A&A...617A..23B (2018): Molecular line study of the S-type AGB star W Aquilae. ALMA observations of CS, SiS, SiO and HCN
- 2018A&A...617A..28S (2018): Chemistry in disks. XI. Sulfur-bearing species as tracers of protoplanetary disk physics and chemistry: the DM Tau case
- 2018A&A...618A..85S (2018): Near infrared spectroscopy and star-formation histories of 3 ≤ z ≤ 4 quiescent galaxies
- 2018A&A...619A..39F (2018): The dense molecular gas in the z ∼ 6 QSO SDSS J231038.88+185519.7 resolved by ALMA
- 2018A&A...619A.161C (2018): Evidence for a massive dust-trapping vortex connected to spirals. Multi-wavelength analysis of the HD 135344B protoplanetary disk
- 2018A&A...620A..75K (2018): High-resolution observations of gas and dust around Mira using ALMA and SPHERE/ZIMPOL
- 2018A&A...620A.152F (2018): GOODS-ALMA: 1.1 mm galaxy survey. I. Source catalog and optically dark galaxies
- 2018AJ....156..164B (2018): Medium-sized Satellites of Large Kuiper Belt Objects
- 2018ApJ...852..122H (2018): CO and Dust Properties in the TW Hya Disk from High-resolution ALMA Observations
- 2018ApJ...853..147M (2018): Molecular Reconnaissance of the β Pictoris Gas Disk with the SMA: A Low HCN/(CO+CO<SUB>2</SUB>) Outgassing Ratio and Predictions for Future…
- 2018ApJ...854..130W (2018): The Orbit of the Companion to HD 100453A: Binary-driven Spiral Arms in a Protoplanetary Disk
- 2018ApJ...855L...2M (2018): Detection of a Millimeter Flare from Proxima Centauri
- 2018ApJ...856..117F (2018): Turbulence in the TW Hya Disk
- 2018ApJ...857...18S (2018): Multiple Gaps in the Disk of the Class I Protostar GY 91
- 2018ApJ...859...21A (2018): ALMA Survey of Lupus Protoplanetary Disks. II. Gas Disk Radii
- 2018ApJ...859...32P (2018): Homogeneous Analysis of the Dust Morphology of Transition Disks Observed with ALMA: Investigating Dust Trapping and the Origin of the Cavit…
- 2018ApJ...859...35G (2018): The Dual Role of Starbursts and Active Galactic Nuclei in Driving Extreme Molecular Outflows
- 2018ApJ...859..111H (2018): The Circumstellar Disk and Asymmetric Outflow of the EX Lup Outburst System
- 2018ApJ...859..131L (2018): The Distribution and Excitation of CH<SUB>3</SUB>CN in a Solar Nebula Analog
- 2018ApJ...860....7R (2018): A Cavity of Large Grains in the Disk around the Group II Herbig Ae/Be Star HD 142666
- 2018ApJ...860..103S (2018): Molecular Gas Contents and Scaling Relations for Massive, Passive Galaxies at Intermediate Redshifts from the LEGA-C Survey
- 2018ApJ...861....7F (2018): ALMA 26 Arcmin<SUP>2</SUP> Survey of GOODS-S at One Millimeter (ASAGAO): Average Morphology of High-z Dusty Star-forming Galaxies in an Exp…
- 2018ApJ...861...43P (2018): Hidden in Plain Sight: A Massive, Dusty Starburst in a Galaxy Protocluster at z = 5.7 in the COSMOS Field
- 2018ApJ...861...91H (2018): ALMA Observations of Polarized 872 μm Dust Emission from the Protostellar Systems VLA 1623 and L1527
- 2018ApJ...863...19A (2018): The Distinct Evolutionary Nature of Two Class 0 Protostars in Serpens Main SMM4
- 2018ApJ...863..129S (2018): Spatially Resolved Dense Molecular Gas Excitation in the Nearby LIRG VV 114
- 2018ApJ...865...37M (2018): Multiple Rings in the Transitional Disk of GM Aurigae Revealed by VLA and ALMA
- 2018ApJ...866L...6C (2018): High-resolution Millimeter Imaging of the CI Tau Protoplanetary Disk: A Massive Ensemble of Protoplanets from 0.1 to 100 au
- 2018ApJ...867...48I (2018): Circumnuclear Multiphase Gas in the Circinus Galaxy. II. The Molecular and Atomic Obscuring Structures Revealed with ALMA
- 2018ApJ...867..140L (2018): Resolving Star Formation on Subkiloparsec Scales in the High-redshift Galaxy SDP.11 Using Gravitational Lensing
- 2018ApJ...868L...5K (2018): A Spatially Resolved au-scale Inner Disk around DM Tau
- 2018ApJ...869...17L (2018): Gaps and Rings in an ALMA Survey of Disks in the Taurus Star-forming Region
- 2018ApJ...869...59W (2018): Physical and Chemical Conditions of the Protostellar Envelope and the Protoplanetary Disk in HL Tau
- 2018ApJ...869...75M (2018): ALMA Detection of Extended Millimeter Halos in the HD 32297 and HD 61005 Debris Disks
- 2018ApJ...869..158F (2018): ALMA Detections of the Youngest Protostars in Ophiuchus
- 2018ApJ...869L..48G (2018): The Disk Substructures at High Angular Resolution Program (DSHARP). VIII. The Rich Ringed Substructures in the AS 209 Disk
- 2018ApJ...869L..50P (2018): The Disk Substructures at High Angular Resolution Project (DSHARP). X. Multiple Rings, a Misaligned Inner Disk, and a Bright Arc in the Dis…
- 2018MNRAS.474.4347C (2018): The ALMA early science view of FUor/EXor objects - V. Continuum disc masses and sizes
- 2018MNRAS.475.4924K (2018): ALMA observations of the narrow HR 4796A debris ring
- 2018MNRAS.476.3956T (2018): ALMA view of a massive spheroid progenitor: a compact rotating core of molecular gas in an AGN host at z = 2.226
- 2018MNRAS.481L..40S (2018): A flux-ratio anomaly in the CO spectral line emission from gravitationally lensed quasar MG J0414+0534
- 2018Natur.553...51M (2018): Galaxy growth in a massive halo in the first billion years of cosmic history
- 2018Sci...361.1016S (2018): Fast molecular outflow from a dusty star-forming galaxy in the early Universe
- 2019A&A...621A..18M (2019): Submillimeter polarization and variability of quasar PKS 1830-211
- 2019A&A...623A.124C (2019): Upper limits on CH<SUB>3</SUB>OH in the HD 163296 protoplanetary disk. Evidence for a low gas-phase CH<SUB>3</SUB>OH-to-H<SUB>2</SUB>CO rat…
- 2019A&A...623A.150V (2019): The ALMA Lupus protoplanetary disk survey: evidence for compact gas disks and molecular rings from CN
- 2019A&A...624A..33V (2019): ALMA study of the HD 100453 AB system and the tidal interaction of the companion with the disk
- 2019A&A...625A.118K (2019): Highly structured disk around the planet host PDS 70 revealed by high-angular resolution observations with ALMA
- 2019A&A...626L...2F (2019): High gas-to-dust size ratio indicating efficient radial drift in the mm-faint CX Tauri disk
- 2019A&A...628A..65A (2019): Nuclear molecular outflow in the Seyfert galaxy NGC 3227
- 2019A&A...628A..95M (2019): Observational constraints on dust disk sizes in tidally truncated protoplanetary disks in multiple systems in the Taurus region
- 2019A&A...628A.100D (2019): An ALMA+ACA measurement of the shock in the Bullet Cluster
- 2019A&A...628A.118B (2019): The gentle monster PDS 456. Kiloparsec-scale molecular outflow and its implications for QSO feedback
- 2019A&A...629A.128W (2019): Chlorine-bearing molecules in molecular absorbers at intermediate redshifts
- 2019A&A...630A..59B (2019): Widespread QSO-driven outflows in the early Universe
- 2019A&A...632A..33A (2019): ALMA captures feeding and feedback from the active galactic nucleus in NGC 613
- 2019A&A...632A..61G (2019): ALMA images the many faces of the <ASTROBJ>NGC 1068</ASTROBJ> torus and its surroundings
- 2019AJ....157..237R (2019): Constraints on a Putative Planet Sculpting the V4046 Sagittarii Circumbinary Disk
- 2019AJ....158...47M (2019): Thermal Emission from the Uranian Ring System
- 2019AJ....158..162F (2019): From Scattered-light to Millimeter Emission: A Comprehensive View of the Gigayear-old System of HD 202628 and its Eccentric Debris Ring
- 2019ApJ...870...80L (2019): Spatially Resolved [C II] Emission in SPT0346-52: A Hyper-starburst Galaxy Merger at z ∼ 5.7
- 2019ApJ...871....5T (2019): The Flared Gas Structure of the Transitional Disk around Sz 91
- 2019ApJ...871...48P (2019): High-resolution ALMA Observations of HD 100546: Asymmetric Circumstellar Ring and Circumplanetary Disk Upper Limits
- 2019ApJ...871..100H (2019): ALMA Observations of the Protostellar Disk around the VeLLO IRAS 16253-2429
- 2019ApJ...871..112X (2019): ALMA Observations of the Spatial Distribution of Three C<SUB>2</SUB>H<SUB>4</SUB>O<SUB>2</SUB> Isomers toward Sgr B2(N)
- 2019ApJ...872...92F (2019): The Planet Formation Potential around a 45 Myr Old Accreting M Dwarf
- 2019ApJ...873...50D (2019): Source Structure and Molecular Gas Properties from High-resolution CO Imaging of SPT-selected Dusty Star-forming Galaxies
- 2019ApJ...873L..19B (2019): Extremely Low Molecular Gas Content in a Compact, Quiescent Galaxy at z = 1.522
- 2019ApJ...875...55W (2019): The MESAS Project: Long-wavelength Follow-up Observations of Sirius A
- 2019ApJ...875...87D (2019): The Mass of Stirring Bodies in the AU Mic Debris Disk Inferred from Resolved Vertical Structure
- 2019ApJ...875L...9W (2019): The Ophiuchus DIsk Survey Employing ALMA (ODISEA): Disk Dust Mass Distributions across Protostellar Evolutionary Classes
- 2019ApJ...876..112R (2019): Strong Far-ultraviolet Fields Drive the [C II]/Far-infrared Deficit in z ∼ 3 Dusty, Star-forming Galaxies
- 2019ApJ...877L..32M (2019): Multiple Rings of Millimeter Dust Emission in the HD 15115 Debris Disk
- 2019ApJ...878...16P (2019): An Inner Disk in the Large Gap of the Transition Disk SR 24S
- 2019ApJ...878L...8T (2019): Discovery of An au-scale Excess in Millimeter Emission from the Protoplanetary Disk around TW Hya
- 2019ApJ...880..130M (2019): A New, Rotating Hot Corino in Serpens
- 2019ApJ...881...84S (2019): The REASONS Survey: Resolved Millimeter Observations of a Large Debris Disk around the Nearby F Star HD 170773
- 2019ApJ...881L...2B (2019): ALMA Observations of the Terahertz Spectrum of Sagittarius A*
- 2019ApJ...882...49L (2019): Compact Disks in a High-resolution ALMA Survey of Dust Structures in the Taurus Molecular Cloud
- 2019ApJ...882..118X (2019): ALMA Detection of Vibrationally Excited (v <SUB>t</SUB> = 1, 2) Acetic Acid toward NGC 6334I
- 2019ApJ...882..160Q (2019): Probing CO and N<SUB>2</SUB> Snow Surfaces in Protoplanetary Disks with N<SUB>2</SUB>H<SUP>+</SUP> Emission
- 2019ApJ...883...22C (2019): The Degree of Alignment between Circumbinary Disks and Their Binary Hosts
- 2019ApJ...883...71C (2019): The Radial Distribution of Dust Particles in the HL Tau Disk from ALMA and VLA Observations
- 2019ApJ...884...97L (2019): Diagnosing 0.1-10 au Scale Morphology of the FU Ori Disk Using ALMA and VLTI/GRAVITY
- 2019ApJ...885...82L (2019): Sulfur-bearing Molecules in Orion KL
- 2019ApJ...887...40W (2019): Resolving the Interstellar Medium in the Nuclear Region of Two z = 5.78 Quasar Host Galaxies with ALMA
- 2019ApJ...887..107F (2019): First Identification of 10 kpc [C II] 158 μm Halos around Star-forming Galaxies at z = 5-7
- 2019ApJ...887..144J (2019): Discovery of Four Apparently Cold Dusty Galaxies at z = 3.62-5.85 in the COSMOS Field: Direct Evidence of Cosmic Microwave Background Impac…
- 2019MNRAS.482..698C (2019): The Ophiuchus DIsc Survey Employing ALMA (ODISEA) - I: project description and continuum images at 28 au resolution
- 2019MNRAS.484.1257M (2019): A gap in HD 92945's broad planetesimal disc revealed by ALMA
- 2019MNRAS.485..739M (2019): Asymmetric mid-plane gas in ALMA images of HD 100546
- 2019MNRAS.485.2092C (2019): Suppressed CO emission and high G/D ratios in z = 2 galaxies with sub-solar gas-phase metallicity
- 2019MNRAS.490.4956G (2019): An ALMA survey of the SCUBA-2 Cosmology Legacy Survey UKIDSS/UDS field: high-resolution dust continuum morphologies and the link between su…
- 2019NatAs...3..278K (2019): Publisher Correction: A circumbinary protoplanetary disk in a polar configuration
- 2020A&A...633A.114S (2020): Demographics of disks around young very low-mass stars and brown dwarfs in Lupus
- 2020A&A...633A.126B (2020): The dynamically young outflow of the Class 0 protostar Cha-MMS1
- 2020A&A...635A.119C (2020): Extended Hα over compact far-infrared continuum in dusty submillimeter galaxies. Insights into dust distributions and star-formation rates …
- 2020A&A...636A..37D (2020): Dust and gas content of high-redshift galaxies hosting obscured AGN in the Chandra Deep Field-South
- 2020A&A...636A..62K (2020): Investigating the connection between γ-ray activity and the relativistic jet in 3C 273 during 2015-2019
- 2020A&A...637A...7M (2020): Detection of deuterated molecules, but not of lithium hydride, in the z = 0.89 absorber toward PKS 1830-211
- 2020A&A...641A.155V (2020): CO emission in distant galaxies on and above the main sequence
- 2020A&A...642A.155Z (2020): GOODS-ALMA: Optically dark ALMA galaxies shed light on a cluster in formation at z = 3.5
- 2020A&A...643A..53F (2020): GOODS-ALMA: Using IRAC and VLA to probe fainter millimeter galaxies
- 2020AJ....159..288M (2020): The Big Sibling of AU Mic: A Cold Dust-rich Debris Disk around CP-72 2713 in the β Pic Moving Group
- 2020ApJ...889...59P (2020): Resolving the FU Orionis System with ALMA: Interacting Twin Disks?
- 2020ApJ...891...48H (2020): A Multifrequency ALMA Characterization of Substructures in the GM Aur Protoplanetary Disk
- 2020ApJ...891...80M (2020): Properties of M Dwarf Flares at Millimeter Wavelengths
- 2020ApJ...894...76W (2020): The MESAS Project: ALMA Observations of the F-type Stars γ Lep, γ Vir A, and γ Vir B
- 2020ApJ...895..109F (2020): Measuring Turbulent Motion in Planet-forming Disks with ALMA: A Detection around DM Tau and Nondetections around MWC 480 and V4046 Sgr
- 2020ApJ...895..126H (2020): The Evolution of Dust Disk Sizes from a Homogeneous Analysis of 1-10 Myr old Stars
- 2020ApJ...895L..18B (2020): GW Ori: Interactions between a Triple-star System and Its Circumtriple Disk in Action
- 2020ApJ...897...91G (2020): The ALMA Spectroscopic Survey in the HUDF: Deep 1.2 mm Continuum Number Counts
- 2020ApJ...898...36L (2020): Dual-wavelength ALMA Observations of Dust Rings in Protoplanetary Disks
- 2020ApJ...898...75I (2020): ALMA Observations of Multiple CO and C Lines toward the Active Galactic Nucleus of NGC 7469: An X-Ray-dominated Region Caught in the Act
- 2020ApJ...898..146M (2020): Dust Populations in the Iconic Vega Planetary System Resolved by ALMA
- 2020ApJ...899...55A (2020): Search for Alignment of Disk Orientations in Nearby Star-forming Regions: Lupus, Taurus, Upper Scorpius, ρ Ophiuchi, and Orion
- 2020ApJ...900....1F (2020): The ALPINE-ALMA [C II] Survey: Size of Individual Star-forming Galaxies at z = 4-6 and Their Extended Halo Structure
- 2020ApJ...901...74T (2020): Structural Evolution in Massive Galaxies at z ∼ 2
- 2020ApJ...901...79A (2020): The ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: The Nature of the Faintest Dusty Star-forming Galaxies
- 2020ApJ...902..132B (2020): On the Nature of the T Tauri Triple System
- 2020ApJ...902..141S (2020): The VLA/ALMA Nascent Disk and Multiplicity (VANDAM) Survey of Orion Protostars. III. Substructures in Protostellar Disks
- 2020ApJ...903...29M (2020): Reconstructing the EUV Spectrum of Star-forming Regions from Millimeter Recombination Lines of H I, He I, and He II
- 2020MNRAS.493L.108B (2020): <SUP>13</SUP>C<SUP>17</SUP>O suggests gravitational instability in the HL Tau disc
- 2021A&A...653A..46V (2021): Probing protoplanetary disk evolution in the Chamaeleon II region
- 2021A&A...653A.117B (2021): ORion Alma New GEneration Survey (ORANGES). I. Dust continuum and free-free emission of OMC-2/3 filament protostars
- 2021AJ....161...38O (2021): The TW Hya Rosetta Stone Project. I. Radial and Vertical Distributions of DCN and DCO<SUP>+</SUP>
- 2021AJ....161..271F (2021): A Detailed Characterization of HR 8799's Debris Disk with ALMA in Band 7
- 2021ApJ...908...54W (2021): ALMA Measures Rapidly Depleted Molecular Gas Reservoirs in Massive Quiescent Galaxies at z ∼ 1.5
- 2023PASJ...75..424O (2023): ALMA Band 6 high-resolution observations of the transitional disk around SY Chamaeleontis
- 2023PSJ.....4..142C (2023): Thermal Properties of the Leading Hemisphere of Callisto Inferred from ALMA Observations
- 2023PSJ.....4..193B (2023): Masses and Densities of Dwarf Planet Satellites Measured with ALMA
- 2024A&A...684A..23T (2024): Fitting pseudo-Sérsic (Spergel) light profiles to galaxies in interferometric data: The excellence of the uυ-plane
- 2024A&A...685A..80Z (2024): Unveiling [C II] clumps in a lensed star-forming galaxy at z ∼ 3.4
- 2024A&A...686A.201N (2024): ALMA view of the L1448-mm protostellar system on disk scales: CH<SUB>3</SUB>OH and H<SUP>13</SUP>CN as new disk wind tracers
- 2024A&A...689A..85G (2024): MINDS: A multi-instrument investigation into the molecule-rich JWST-MIRI spectrum of the DF Tau binary system
- 2024A&A...689A.104D (2024): From traffic jams to roadblocks: The outer regions of TW Hya with ALMA Band 8
- 2024A&A...689A.299M (2024): Prospects of directly using closure traces for imaging in very long baseline interferometry
- 2024A&A...689A.317G (2024): Continuum and molecular emission from the inner regions of the symbiotic system R Aquarii
- 2024A&A...690A..55S (2024): NOEMA formIng Cluster survEy (NICE): Characterizing eight massive galaxy groups at 1.5 &lt; z &lt; 4 in the COSMOS field
- 2024ApJ...963..164R (2024): The Disk Orientations of Perseus Protostellar Multiples at ∼8 au Resolution
- 2024ApJ...966...59S (2024): Small and Large Dust Cavities in Disks around Mid-M Stars in Taurus
- 2024ApJ...972..163L (2024): First JVLA Radio Observation on PDS 70
- 2024ApJ...974..102S (2024): Hints of Planet Formation Signatures in a Large-cavity Disk Studied in the AGE-PRO ALMA Large Program
- 2024ApJ...976..132H (2024): High-resolution ALMA Observations of Richly Structured Protoplanetary Disks in σ Orionis
- 2024MNRAS.529.3601R (2024): Observations of spiral and streamer on a candidate proto-brown dwarf
- 2024NatAs...8..587F (2024): Resolved ALMA observations of water in the inner astronomical units of the HL Tau disk
- 2024Natur.633..323V (2024): One month convection timescale on the surface of a giant evolved star
- 2024PASJ...76..340K (2024): Sub-parsec-scale jet-driven water maser with possible gravitational acceleration in the radio galaxy NGC 1052
- 2024PSJ.....5..230D (2024): Surface Properties of the Kalliope─Linus System from ALMA and VLA Data
- 2025A&A...693A.151M (2025): REsolved ALMA and SMA Observations of Nearby Stars (REASONS): A population of 74 resolved planetesimal belts at millimetre wavelengths
- 2025A&A...695A.233R (2025): A multifrequency study of sub-parsec jets with the Event Horizon Telescope
- 2025A&A...698A.183D (2025): Dust populations from 30 to 1000 au in the debris disk of HD 120326: Panchromatic view with VLT/SPHERE, ALMA, and HST/STIS
- 2025A&A...699A.256P (2025): The ALMA-CRISTAL survey: Extended [CII] emission in an interacting galaxy system at z ∼ 5.5
- 2025A&A...700A.165B (2025): GAMA 526784: The progenitor of a globular cluster-rich ultra-diffuse galaxy?: II. Molecular gas, neutral gas, and environment
- 2025A&A...700A.188C (2025): FAUST: XXVI. The dust opacity spectral indices of protostellar envelopes bridge the gap between interstellar medium and disks
- 2025A&A...700A.278R (2025): CO(1─0) imaging reveals 10-kiloparsec molecular gas reservoirs around star-forming galaxies at high redshift
- 2025ApJ...986L..11S (2025): Hints of Disk Substructure in the First Brown Dwarf with a Dynamical Mass Constraint
- 2025ApJ...986L..22R (2025): The First Detection of Molecular Activity in the Largest Known Oort Cloud Comet: ALMA Imaging of C/2014 UN271 (Bernardinelli─Bernstein) at …
- 2025ApJ...990L..31B (2025): ALMA Reveals Bright Circumgalactic Emission and a Biconical Outflow in z ∼ 6.4 Quasar PSOJ183+05
- 2025ApJ...991..176W (2025): Radiative Transfer Modeling of a Shadowed Protoplanetary Disk Assisted by a Neural Network
- 2025ApJ...993...90S (2025): ALMA High-resolution Observation for the Transitional Disk Around IRAS 04125+2902
- 2025MNRAS.536.3757A (2025): The kinematics of massive high-redshift dusty star-forming galaxies
- 2025MNRAS.543.2723P (2025): Observational constraints on evolution of dust disc properties in Upper Scorpius
- 2025NatAs...9.1476C (2025): A D/H ratio consistent with Earth's water in Halley-type comet 12P from ALMA HDO mapping
- 2026A&A...705A..81K (2026): Resolving the molecular gas emission of the z ∼ 2.5─2.8 starburst galaxies SPT 0125-47 and SPT 2134-50
- 2026ApJ..1001..124M (2026): Multiwavelength ALMA Imaging of HD 34282: Dust-trapping Signatures of a Vortex Candidate
- 2026ApJ..1004..126K (2026): An Active Galactic Nucleus in the Antennae Galaxies?
