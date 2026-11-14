# Review task: a REFRESHED ALMA agent skill against its rebuilt evidence pack

The skill below was first written from a ~1,600-paper corpus, reviewed, and fixed (the fix record is the
RECONCILIATION section). The corpus then grew to ~3,500 papers, the evidence pack was rebuilt, and a writer began
updating the skill to the new pack. The writer may have been cut off before finishing, so expect a mix: some
counts and ranges updated to the new pack, others still at the old values, and possibly a half-edited section.

Apply every check from the standard review (attribution, unsupported practice, scientific correctness, omissions,
usability: see below), and also these refresh checks:

A. **Stale or mixed numbers.** Paper counts, "used in N papers", common choices and ranges that do not match the
   NEW pack aggregates (the old corpus was about half the size, so old counts are usually roughly half). The
   description line's "Built from N ALMA papers" must match the pack.
B. **Lost fixes.** Any item the RECONCILIATION marks FIXED that the current skill has undone or reintroduced.
C. **Broken edits.** Duplicated sections, contradictory statements left from an unfinished rewrite, tables whose
   rows disagree with the text, dangling references.
D. **Length.** Over ~300 lines is a low-severity usability finding; say what could move to references/parameters.md.

Standard checks, in this order:
1. Attribution: every number, range, default, software attribution and "papers do X" claim that cites bibcodes is
   supported by the pack for those bibcodes; counts match the pack aggregates.
2. Unsupported practice presented as literature practice.
3. Scientific correctness: formulas, units, CASA task/parameter names and semantics, unsafe advice.
4. Omissions: important pitfalls, assumptions or validation checks clearly present in the pack but missing.
5. Usability: anything an agent would misread or could not act on.

You have no file access: everything you need is in this message.

Output format (Markdown, nothing else):

```
# Codex refresh review: <slug>
VERDICT: CLEAN | FIX
REFRESH: COMPLETE | PARTIAL   (PARTIAL if any section still carries old-pack numbers or an unfinished edit)
## Findings
- RR-01 | high|medium|low | <stale|lost-fix|broken-edit|length|attribution|unsupported|science|omission|usability> | <the claim, quoted briefly> | <problem, citing the pack line or bibcode> | <concrete fix>
- RR-02 | ...
## Notes
<at most 5 lines>
```

Use `VERDICT: CLEAN` only when there are no high or medium findings. Be specific and terse; do not restate the
skill. Do not invent pack content: when you say the pack contradicts a claim, cite the pack line.

=== SKILL.md (uv-plane-fitting) ===
---
name: alma-uv-plane-fitting
description: "Fit parametric or non-parametric source models directly to ALMA visibilities (point sources, Gaussians, uniform or exponential disks, rings, radiative-transfer or lensed model images, line-emission models) to get fluxes, sizes, positions, geometry and radial profiles with honest uncertainties. Use when a source is compact or near the resolution limit, when image-plane deconvolution would bias sizes or profiles, when fitting disk or debris-belt structure, extracting spectra of unresolved components, measuring stellar or planetary fluxes, or checking someone else's visibility fit. Built from 638 ALMA papers (2012-2026)."
---

# Fitting models directly to visibilities

Compares a model with the measured complex visibilities at the observed (u,v) points instead of with a
deconvolved image, so the fit itself involves no CLEAN deconvolution, beam deconvolution or non-linear masking
(it still inherits the self-calibration model and any sources subtracted beforehand, 2020ApJ...902..141S). It
gives fluxes, sizes, positions, inclination/PA and radial profiles, often below the beam size. The mistakes
that matter most: (1) not checking the visibility weights and treating formal errors as total errors (several
papers multiplied pipeline weights by factors of 0.1 to 0.6 after checking them against the noise,
2020ApJ...902..141S, 2024PASJ...76..437Y, 2026ApJ..1005...94N, and formal errors miss calibration, astrometric
and model-choice systematics, 2024A&A...687A.308S), and (2) reading structure
the uv coverage cannot constrain: total flux extrapolated to zero spacing, sizes near the largest recoverable
scale, and degenerate profile shapes (2020ApJ...898..146M, 2014ApJ...791L...6W, 2015ApJ...798..124R).

> Always report: model family and its assumptions (axisymmetric? optically thin?), which data entered the fit
> (uv range, channels, averaging), how weights were set, the fitter/sampler with priors and chain settings,
> and the validation (residual image at identical uv coverage, deprojected visibility profile).

## When to use

- Compact or barely resolved continuum sources where you need size and flux: submm galaxy FIR sizes
  (uvmultifit exponential disk, 2017ApJ...850...83F; 2020ApJ...901...74T), [C II] sizes and a stacked-visibility
  search for an extended halo (2025A&A...693A.237I), protostellar disks (2024ApJ...963..164R), cores
  (2014ApJ...797...27F).
- Stars, planets, moons and comets where the model is physically simple: point source fluxes
  (2020ApJ...894...76W, 2018ApJ...855L...2M), uniform or limb-darkened disks (2023PSJ.....4..142C,
  2015ApJ...808...36M, 2018AJ....156..164B, 2024Natur.633..323V), Haser coma models (2014ApJ...792L...2C,
  2025ApJ...986L..22R).
- Protoplanetary disk and debris belt structure: axisymmetric ring/gap profiles (2018ApJ...865...37M,
  2018ApJ...869...17L, 2020ApJ...891...48H), belt radius/width/height (2025A&A...693A.151M,
  2017MNRAS.465.2595M, 2019ApJ...875...87D; vertical aspect ratios for a whole survey, 2026A&A...705A.197Z),
  radiative-transfer model images compared in the uv plane (2020ApJ...902..141S, 2019ApJ...871..100H),
  multi-epoch fits with one intensity model and a separate centre per epoch (2024A&A...692A.155K).
- Line emission: Keplerian disk models for dynamical masses, turbulence and temperature
  (2017ApJ...846L..26W, 2018ApJ...856..117F, 2025ApJ...986L..11S; pdspy + RADMC-3D + galario + dynesty with
  velocity and uv cuts to isolate each protostar, 2024A&A...687A.308S), parameterized abundance models
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
  intervals; 2020ApJ...894...76W fit each 6-8 min scan; 2022ApJ...939L...6B ran `uvmodelfit` point fits on
  every 6 s (12-m) or 10 s (ACA) integration and flagged > 3 sigma points as flare candidates).

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
   continuum-subtracted channels for lines. Shift phase centre if needed (fixvis in 2017MNRAS.465.2595M).
   Deal with other field sources: subtract separable (distant) ones by modelling them with `uvmodelfit`,
   predicting with `ft` and removing with `uvsub`, but fit close or blended secondaries jointly with the target
   (2025A&A...700A.188C does both; uvsub of an external source before the galario fit in 2025ApJ...986L..11S).
   Subtraction adds uncertainty: the envelope mass of a source next to a subtracted one was flagged as more
   uncertain than its nominal errors (2020ApJ...902..141S). Bright off-axis sources need an accurate primary
   beam: an Airy-disk beam left ~5% residuals in single-field point-source fits, fixed by fitting the 4 nearest
   mosaic fields jointly, per execution block (2026A&A...707A.255C). If continuum subtraction feeds a line fit,
   carry its systematics; 2019ApJ...882..118X notes its uncertainties may be underestimated for leaving them out.
   For axisymmetric fits, recentre on a first Gaussian fit (`uvmodelfit` then `fixvis`) and check the centre by
   shifting it and minimising the RMS of the image made from the imaginary part (2021ApJ...909..212K).
2. **Average to a manageable size, without smearing.** Time averaging: 3 min and 2 GHz bins
   (2017MNRAS.465.2595M), up to 3 min with uv separation < 10 m (2018Sci...361.1016S), up to 10 min with
   uv separation < 15 m (2019ApJ...873...50D), 10 s and four channels per SPW (2018MNRAS.475.4924K,
   2024A&A...686A.206Y), 24 s and one channel per SPW (2024A&A...692A.155K), 30 s (2021A&A...645A..33B). General
   practice: check that time/bandwidth smearing at the longest baseline stays below the scales you fit.
3. **Check the weights against the noise.** Recompute with CASA `statwt` (2018MNRAS.475.4924K,
   2024A&A...686A.206Y, 2017MNRAS.465.2595M), rescale to match the image RMS or the scatter (factors 0.1-0.6,
   see the parameter table; f = stddev^-2 / mean weight in 2024PASJ...76..437Y; `visweightscale` 0.6 for one
   project and 0.2 for each track of another in 2026ApJ..1005...94N, so check each execution block), or fit
   the scaling as a free parameter (2020ApJ...898..146M, 2025A&A...693A.151M, 2024ApJ...962..166W,
   2021MNRAS.502.5390P). These corrections were dataset-specific; set yours from an independent noise estimate
   (line-free channels, image RMS, visibility scatter), not by forcing the model's reduced chi2 to 1. Only 10
   papers state a visibility-weight treatment (my count of current pack lines); 2019MNRAS.485.2092C scaled
   spectral errors so Var(S/sigma)=1 in line-free channels. General practice (not stated in the pack): if the
   weight scale s is free, the log-likelihood must keep the normalisation term, ln L = -chi2/(2 s) - (N/2) ln s
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
7. **Get uncertainties.** From the posterior (median or mode with 68% interval, 2015ApJ...798..124R; 95%
   in 2020ApJ...902..141S), from the covariance at minimum (2018A&A...617A..23B, 2025ApJ...986L..22R), or
   from a delta-chi2 curve (2025ApJ...986L..22R used Delta chi2 = 1 and 6.63 for 68% and 99% confidence on a
   single parameter, Lp; general practice: for joint regions in two parameters the 68% and 99% thresholds are
   2.30 and 9.21, so pick the threshold for the number of parameters of interest). Add the dataset's absolute
   flux calibration uncertainty in quadrature to fluxes (10% in 2016A&A...596A..75S, 2021A&A...653A.117B; 5%
   in 2023PSJ.....4..142C). General practice: the calibration error is shared by measurements calibrated
   together, so do not add it independently to each point of a spectral index or ratio from the same data;
   propagate it as a correlated term. For positions, add the ALMA astrometric systematic in quadrature (5% of
   the beam in 2025Natur.642..905L).
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
so infer sizes from the fitted profile, not by applying one of these formulas to an observed null. The
pack's example: 2014ApJ...791L...6W saw a null at 290 klambda and fitted Gaussian and flat ring models to
the binned deprojected visibilities to get ring radii and widths.

## Parameter defaults and ranges

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| Sampler | emcee affine-invariant | emcee, dynesty, MultiNest, Metropolis chains, grid | emcee 136, dynesty 9, multinest 5 (pack aggregates) | 2025A&A...693A.151M, 2020ApJ...902..141S, 2020RSOS....700063K |
| Walkers | 100 | 24-1024 | 68 papers give walker counts; 100 in 17, 200 in 12, 120 in 7 (my count of pack parameter lines) | 2018ApJ...869...17L (100), 2019ApJ...878...16P (200), 2025ApJ...988..106H (24), 2019ApJ...881...84S (1024) |
| Walkers per free parameter | 8-10 x N_free | 2-10 | 7 (my count of pack lines), plus "more than double" in 2026A&A...705A.197Z | 2020ApJ...898..146M (10), 2021MNRAS.506.1978L (10), 2025ApJ...986L..11S (8), 2024A&A...688A.149D (8), 2026MNRAS.552g1700S (8) |
| Chain length / burn-in | No default: run until converged (autocorrelation time, stable posteriors) and report what you ran. Historical examples only, not stopping rules | emcee steps per walker 300 (2017MNRAS.465.2595M) to 1e5 (2020ApJ...895..126H, 2025A&A...701A.203S); Metropolis-type chains 1e4-2.4e5 iterations (2017A&A...597A..41G); 1e5 total samples (2019ApJ...875...87D) | about 90 papers mention walkers, steps, burn-in, chains or iterations (my count of pack parameter lines; a few are grid steps) | 2019ApJ...874..136S (~5000 steps after burn-in with autocorrelation time ~1000), 2026A&A...705A.197Z (>= 1e5 samples after convergence), 2018ApJ...865...37M (30000, last 5000 used) |
| Priors | uniform | uniform; sin i or uniform cos i on inclination; Gaussian on geometry/centre | 29 papers mention priors (my count); few give bounds | 2018ApJ...869...17L (+-20 deg i/PA, +-0.5'' offsets), 2024ApJ...966...59S (sin i), 2025ApJ...988..106H (cos i in [0,1]), 2025MNRAS.536.3757A (Gaussian centre, sigma 1'') |
| Weights | statwt, or rescale from an independent noise estimate (image RMS, visibility scatter) | multiplicative factors 0.1-0.6; free scale factor | 10 (my count of current pack lines naming statwt, visweightscale, reweighting or free weight scaling) | 2020ApJ...902..141S (x0.25), 2020ApJ...891...48H (/2.667 = x0.375), 2018MNRAS.475.4924K (x0.4), 2024PASJ...76..437Y (0.1-0.3), 2026ApJ..1005...94N (0.2, 0.6) |
| Time averaging | <= 3 min with small uv shift, or 10-30 s | 10 s to 10 min | 8 | 2017MNRAS.465.2595M, 2018Sci...361.1016S, 2019ApJ...873...50D, 2024A&A...692A.155K (24 s), 2021A&A...645A..33B (30 s) |
| uv range | full, or cut to isolate a component or drop noise-dominated baselines | > 15 klambda to < 3000 klambda; > 50 klambda (star), < 200 m (planet disk), > 100-400 klambda (compact disks, protostars) | about 19 (my count of pack lines stating a uv cut) | 2020ApJ...898..146M, 2023PSJ.....4..142C, 2024ApJ...963..164R, 2024A&A...687A.308S, 2021ApJ...909..212K (< 2000 klambda where amplitude reaches the noise), 2019A&A...626A..81V (> 2-3 Mlambda for SPWs with short-baseline excess) |
| uv binning for profiles | 10-50 klambda bins | 5-150 klambda | about 12 | 2014ApJ...791L...6W (10), 2019ApJ...876..112R (5-50 tested), 2020MNRAS.492.3194S (50), 2016ApJ...828L..21K (150); bin errors as azimuthal std / sqrt(N) (2021ApJ...909..212K) |
| Model image | >= 1024 px, pixel well below beam | 256-4096 px; 0.2 mas to 0.02'' | about 10 | 2015ApJ...798..124R (2048 x 0.015''), 2024MNRAS.532.1752R (2048-4096 px), 2025MNRAS.543.2723P (256 x 0.02''); 4 mas checked against 2 mas (2024A&A...692A.155K) |
| frank hyperparameters | alpha 1.05-1.3, w_smooth 1e-4 to 1e-1 | alpha 1.05-1.4; N 300-400; Rmax 2'', 5'' or 4 R_out | 7 (my count of pack lines giving frank settings) | 2025ApJ...986L..11S, 2024A&A...689A.104D, 2024ApJ...974..306S, 2024A&A...682A..55M, 2025ApJ...990L..70L (alpha 1.4) |
| frank geometry uncertainty | perturb i, PA, offsets over repeated fits | 500 runs; 1 deg on i and PA, 1/3 beam major axis on offsets | 1 | 2025ApJ...986L..11S |
| Belt vertical aspect ratio | study-specific assumption: h fixed to 0.03 unless vertically constrained | fitted 0.01-0.3 | 2 | 2025A&A...693A.151M (h fitted where constrained, which "does not necessarily mean" resolved), 2020ApJ...898..146M (h = 0.03 for all models) |
| S/N cut | S/N >= 8-10 for sizes | S/N >= 8 to >= 10 | 4 | 2020ApJ...901...74T (10), 2015ApJ...810..133I (10), 2021A&A...654A..90L (8), 2025A&A...693A.237I (axis ratio fixed below 8) |
| Resolved or point | resolved model only if it clearly wins | Delta BIC >= 2 for a Gaussian, else beam as upper limit; point if size/uncertainty < 5 | 2 | 2020MNRAS.492.3194S, 2016ApJ...828...46A |
| Minimum resolvable size | theta_min = 0.88 theta_beam / sqrt(S/N) | | 1 | 2020A&A...643A..53F |
| Astrometric systematic | added in quadrature to MCMC position errors | 5% of the beam | 1 | 2025Natur.642..905L |
| Flux systematic | the dataset's own flux-scale uncertainty, in quadrature for single fluxes, as a correlated term for ratios of jointly calibrated data | 5-10% | 4 | 2016A&A...596A..75S (10%), 2021A&A...653A.117B (10%), 2020ApJ...894...76W (~10%), 2023PSJ.....4..142C (5%) |

More chain settings, geometry constraints and per-paper fixed values: `references/parameters.md`.

## Software

Counts are mentions in the pack's "software named in the matched steps" aggregate (names are already
lower-cased and merged there). Where I add two aggregate rows (for example "casa uvmodelfit" and "uvmodelfit")
I say so; one paper may then be counted twice.

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

Also in the aggregate: AIPS 9, diskfit 7, lmfit 6, MPFIT 4, uvplot 4 (binned profile plots). uvsim
(2017MNRAS.465.2595M) is no longer in the top-40 list.

Recommendation from the evidence: `uvmodelfit` for single-component sanity checks (note 11 cards flag its
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
  (2018A&A...617A..23B) or scaled by the square root of reduced chi2 (2017AJ....153..240A). Model choice can
  give larger errors than those quoted, and strict velocity and uv cuts left all disk parameters except
  stellar mass poorly constrained (2024A&A...687A.308S). Models with different components cannot be compared
  by fit statistics alone (2019MNRAS.487.4037D).
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
  simpler Gaussian (Delta BIC = +11.8) in 2025ApJ...986L..11S. Report both and call such substructure tentative.
- **Image plane and uv plane give different sizes.** Gas-to-dust size ratios 6-8 in the visibilities vs 2-2.7
  in the image plane (2025ApJ...986L..11S).
- **Low S/N biases sizes.** Faint or compact sources in low-resolution data do not give reliable sizes
  (2017ApJ...850...83F); correct with injection tests (step 8).
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
  the second minimum in the negative visibilities near 600 klambda, which led to a third Gaussian.
- **Model comparison**: BIC (lower by about 40 for the belt model, 2017MNRAS.465.2595M), AIC/BIC
  (2020ApJ...898..146M, 2025ApJ...986L..11S), Bayes factors (2020ApJ...902..141S).
- **Injection and Monte Carlo tests**: 26,600 artificial sources to correct flux/size bias in S/N bins
  (2017ApJ...850...83F); mock sources giving Delta FWHM = +-0.2'' at S/N 5, +-0.1'' at 10, +-0.05'' at 15
  (2020ApJ...901...74T); injected elliptical Gaussians and disks (2015ApJ...808...36M); mock SZ shocks
  (2016ApJ...829L..23B); simobserve Gaussians fitted with `uvmodelfit` recovered sizes within 20% only for
  0.1-0.4'' resolution, which set the archival sample (2020ApJ...888...44C); simulated visibilities from a
  template recovered the input spectral index (2026A&A...707A.255C).
- **Stacked residuals and numerics**: stack visibilities and test the shortest uv bin of the residuals for a
  faint extended component (1.2 sigma at 20 klambda, not a detection, 2025A&A...693A.237I); halve the model
  pixel and check the result holds (2024A&A...692A.155K).
- **Sub-band consistency**: flare candidates kept only if lower and upper sideband fluxes agreed within 20%
  (2022ApJ...939L...6B); separate fits to the upper and lower halves of Band 6 gave similar residual patterns
  (2021ApJ...909..212K).
- **Independent data or methods**: ACA data left out of the fit still matched (2020ApJ...902..141S);
  image-plane imfit or Gaussian fit cross-checks (2024A&A...685A..80Z compared five flux methods;
  `uvmodelfit` sizes ~2% below imfit and GALFIT ~10% above in 2020ApJ...888...44C);
  agreement with earlier measurements (2018ApJ...855L...2M, 2023PSJ.....4..142C, 2017ApJ...850...83F).
- **Chain behaviour**: different walker starting positions (2015ApJ...798..124R); "lost" walkers
  redistributed (2020ApJ...902..141S) or discarded when 5 sigma below the maximum log-likelihood
  (2026A&A...705A.197Z) or with chi2 - chi2_min > 44 (2019ApJ...874..136S); autocorrelation time ~1000 steps
  reported (2019ApJ...874..136S); acceptance fraction 0.2-0.5 (2020MNRAS.492..572A); geometry consistent
  between line and continuum fits (2025ApJ...986L..11S).

What a careful referee adds:
- Weights calibrated from an independent noise estimate, with reduced chi2 reported as found; where it is
  well above 1, residual structure explained rather than absorbed by inflating errors (2025A&A...700A.188C
  reports chi2 well above 1 and attributes it to asymmetric envelopes and unsubtracted sources).
- Autocorrelation time and acceptance fraction for emcee; chains many autocorrelation times long, so that
  convergence, not a copied step count, sets the run length.
- Uncertainty from fixed inputs propagated: geometry passed to a profile fit (500 perturbed frank runs in
  2025ApJ...986L..11S), subtracted neighbours (2020ApJ...902..141S), continuum subtraction
  (2019ApJ...882..118X).
- Fits per execution block or per epoch agree before combining (per-EB stellar fits in 2020ApJ...898..146M),
  or the differences are modelled: a free flux scale and centre per epoch (2024A&A...692A.155K), a separate
  stellar flux per observation for a variable star (2026A&A...705A.197Z).
- Sizes only quoted above the resolution threshold (2020A&A...643A..53F) and upper limits otherwise
  (0.1'' unresolved limit in 2025MNRAS.543.2723P).
- Absolute flux error included in quoted fluxes, and treated as correlated (not added independently per
  point) in spectral indices or ratios of jointly calibrated data.

## Source cards

All 638 papers: `references/sources.md`. Most informative for this technique:

- 2014A&A...563A.136M (uvmultifit method paper, continuum then per-channel fits)
- 2017ApJ...850...83F (uvmultifit sizes for 1034 sources, injection bias correction)
- 2020ApJ...901...74T (Gaussian then exponential disk, size errors vs S/N)
- 2025A&A...693A.237I (uvmultifit [C II] exponential disks, stacked-visibility halo test)
- 2020ApJ...888...44C (uvmodelfit size-recovery simulations, uv vs image-plane sizes)
- 2022ApJ...939L...6B (uvmodelfit per integration, flare light curves, sideband check)
- 2015ApJ...808...36M (uniform disk, injection tests, systematics)
- 2014ApJ...791L...6W (binned deprojected visibilities, chi2 grid, nulls)
- 2021ApJ...909..212K (recentring, binned real visibilities, imaginary-part asymmetry test)
- 2018ApJ...865...37M (Hankel Gaussian rings, MCMC then RT grid)
- 2020ApJ...891...48H (vis_sample + emcee, 21 parameters, weight rescaling)
- 2025A&A...693A.151M (RADMC-3D + galario + emcee for 74 belts)
- 2026A&A...705A.197Z (belt vertical structure: galario + emcee, frank height grid, limitations)
- 2020ApJ...898..146M (star then belt, free weight scaling, AIC/BIC)
- 2017MNRAS.465.2595M (four belt models, BIC)
- 2015ApJ...798..124R (PB-multiplied model image, walker tests, degeneracy)
- 2020ApJ...902..141S (galario + dynesty, Bayes factors, ACA check)
- 2025ApJ...986L..11S (two-layer CO fit, galario, frank, AIC vs BIC)
- 2017A&A...605A..21C (LIME + vis_sample, matched filter)
- 2024A&A...687A.308S (pdspy + dynesty Keplerian line fits, uv and velocity cuts, model-choice caveat)
- 2025ApJ...986L..22R (comet coma, lmfit, delta-chi2 errors)
- 2026A&A...707A.255C (pyralysis point-source subtraction, primary-beam residuals, flux loss)
- 2024A&A...685A..80Z (GILDAS uv_fit per channel, flux-method comparison)

=== references/parameters.md ===
# uv-plane fitting: longer parameter tables

All values from the `uv-plane-fitting` evidence pack ("Key parameters and settings" and excerpts). Counts are
my own count of pack lines. The pack was rebuilt from 638 papers (2026-10-30 refresh); rows added then are
marked (new). Some older rows come from the earlier 278-paper pack and are still in that paper's card even
where the rebuilt pack shows fewer lines per paper.

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
| 2019ApJ...875...87D | 50 | 1e5 samples in total (not steps per walker) | | 0.15 au per pixel |
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
| 2020ApJ...898..146M | 40 (star fits); 10 x N_free (belt fits) | 2000 | | free weight scaling |
| 2024A&A...689A.104D | 80 | 10000 | after 2000 | |
| 2024ApJ...966...59S | 50 | 10000 | | Nuker priors; sin i |
| 2025A&A...693A.151M | 10 x N_free | >= 1000 | | weight rescaling free |
| 2025A&A...700A.188C | 120 | 25000 | | uniform priors |
| 2025ApJ...986L..11S | 192 (8 x N_free); 100 | ~1e4 + 1e4; 10000 | | flat priors |
| 2025ApJ...993...90S | 32 | 1000 | | initialised from SpM cos i and PA |
| 2025MNRAS.543.2723P | 8 per parameter | 30000 | final 10000 | 7 free parameters |
| 2018ApJ...865...37M | not stated | 30000 iterations | last 5000 used | chains started around a Levenberg-Marquardt fit |
| 2019ApJ...874..136S (new) | 200 | ~5000 after burn-in | | autocorrelation time ~1000 steps; walkers with chi2 - chi2_min > 44 dropped |
| 2020MNRAS.492..572A (new) | 120 | 5000 | | acceptance fraction 0.2-0.5 |
| 2021ApJ...909..212K (new) | 100 | 1000 | 1000 burn-in | 16-parameter profile fit to binned real visibilities, < 2000 klambda |
| 2021MNRAS.506.1978L (new) | 120-180 (10 x N_free) | 600-1600 | 250-1000 | three belt models, 12-18 parameters |
| 2021A&A...649A.122P (new) | | > 250000 after convergence | | galario pixel 0.2 mas; 16th/84th percentiles |
| 2024A&A...688A.149D (new) | 136 (8 x N_free) | 6000 | 5000 | 2048 px of 4 mas |
| 2025A&A...701A.203S (new) | 32, then 64 | 1e4, then 1e5 | 30% | two-stage run |
| 2025A&A...699A.373F (new) | 100, then 250 | ~1e3, then 1e4 | 25% | preliminary then fiducial run; same scheme in 2026A&A...709A.174F (120 walkers, 2e4) |
| 2025ApJ...988..106H (new) | 24 | 15000 | 1000 | flat priors, cos i in [0,1] |
| 2026A&A...705A.197Z (new) | 64 (more than 2 x N_free) | ~1500 | visual convergence | >= 1e5 samples after convergence; walkers 5 sigma below max log-likelihood dropped |
| 2026MNRAS.552g1700S (new) | 104 (8 x 13) | 8000 | | geometry fixed from Band 6; 1024 px of 10 mas |

Other chain types: 10,000-240,000 iterations with 5,000 burn-in (2017A&A...597A..41G); 10 chains of 100,000
links, acceptance ~26% (2017MNRAS.466.4201W); ~10^6 MCMC trials (2013ApJ...762L..21M). These lengths are
historical examples; let convergence diagnostics set your run length.

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
| Recentre on a uvmodelfit Gaussian with fixvis, then test the centre by shifting it +-2 mas and minimising the imaginary-image RMS (new) | 2021ApJ...909..212K |
| Phase centre from the high-resolution image peak with fixvis (new) | 2020MNRAS.492.3194S |
| One intensity model for five epochs, separate centre and free flux scale per epoch, one epoch fixed to 1 (new) | 2024A&A...692A.155K |
| Strict position priors so each source in a multiple is fitted separately (new) | 2024A&A...687A.308S |
| Radius, inclination and PA priors normal with sd 3% of Herschel values (new) | 2025MNRAS.541...71M |
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
| 2018ApJ...856..117F | free: T_atm0, T_mid0, q_atm, R_c, i, dv_turb; fixed: M*, distance, CO abundance, PA, v_sys, offset |
| 2020ApJ...895..109F | T_mid0 fixed from the literature, with PA, gamma = 1, Z_q0 and masses; T_atm0, q, R_c, i, dv_turb, R_in, v_sys free |
| 2017A&A...605A..21C | i = 44 deg, PA = 133 deg, d = 122 pc; Tc grid 12-36 K in 2 K steps |

=== RECONCILIATION (first review, fixes to keep) ===
# Reconciliation: uv-plane-fitting
- SR-01 | FIXED | Exponential-disk row now states the pack's conflict (850..83F says R_e = 0.826 FWHM; 834..135T and 900....1F say FWHM = 0.826 R_e), tells the agent to state its own relation, and adds the general-practice derivation (FWHM = 0.826 R_e for n=1).
- SR-02 | FIXED | parameters.md: 2018ApJ...856..117F now lists T_atm0, T_mid0, q_atm, R_c, i, dv_turb as free (pack line 219); added 2020ApJ...895..109F as the paper that fixed T_mid0 (lines 248, 429).
- SR-03 | FIXED | RT row now gives 2017MNRAS.465.2595M as RADMC-3D + uvsim + emcee (pack line 720); galario attributed to 2020ApJ...902..141S and 2025A&A...693A.151M, vis_sample grid to 2019ApJ...871..100H; uvsim added to the Software table (aggregate count 2).
- SR-04 | FIXED | When-to-use now says 2024A&A...685A..80Z fitted clumps as PSFs with a free centre per channel and used fixed-position uv fits only for continuum upper limits (pack lines 876-881).
- SR-05 | FIXED | Lensed-source row: "fixed" kept only for 2015ApJ...811..124S; 2018Sci...361.1016S listed as an SIE lens without "fixed".
- SR-06 | FIXED | Walkers-per-parameter count changed to 4 (my count of pack lines 104/182/275/780), adding 2025MNRAS.543.2723P (8 per parameter).
- SR-07 | FIXED | Range now separates emcee steps per walker 300 (465.2595M) to 1e5 (895..126H), Metropolis iterations 1e4-2.4e5 (597A..41G) and 1e5 total samples (875...87D); parameters.md marks 875...87D as total samples and adds the other chain types. Chain-setting count recounted to about 40 (method stated).
- SR-08 | FIXED | Weights row now gives multiplicative factors 0.25-0.4 with each paper's value (x0.25, /2.667 = x0.375, x1/2.5 = x0.4). Paper count recounted to 6 visibility-weight treatments (method stated).
- SR-09 | FIXED | Verification text now says the two-ring model failed to reproduce the second minimum in the negative visibilities near 600 klambda (pack line 1329).
- SR-10 | FIXED | "usually held fixed" removed; the row now gives 2015ApJ...811..124S as one example where the ALMA continuum lens was held fixed while fitting ATCA CO visibilities (pack line 366).
- SR-11 | FIXED | Belt aspect ratio row relabelled a study-specific assumption, "unless vertically constrained", with 693A.151M's caveat that constrained heights need not be resolved (pack line 531).
- SR-12 | FIXED | "Weights are wrong by default" replaced by "Unchecked weights": calibrate weights from an independent noise estimate, do not rescale to force reduced chi2 = 1, high chi2 can be model inadequacy (700A.188C); referee check and step 3 rewritten the same way.
- SR-13 | FIXED | Step 3 adds a general-practice note: with a free weight scale s the log-likelihood keeps the -(N/2) ln s term (or log-determinant) and s needs a proper bounded prior; step 6 notes exp(-chi2/2) applies with fixed weights.
- SR-14 | FIXED | Formula paragraph now has theta in radians, separate uniform-disk and thin-ring formulas with their first nulls, warns that null positions depend on the profile, and describes 2014ApJ...791L...6W as fitting ring models to the binned visibilities.
- SR-15 | FIXED | Step 7 and the flux-systematic row use the dataset's own flux-scale uncertainty (10% in 596A..75S, 653A.117B; 5% in 2023PSJ.....4..142C) and add a general-practice note to treat it as correlated for spectral indices and ratios.
- SR-16 | FIXED | Step 7 now says Delta chi2 = 1 and 6.63 are 68% and 99% for one parameter (Lp) in 2025ApJ...986L..22R and gives 2.30 / 9.21 for two parameters as general practice.
- SR-17 | FIXED | Summary now says the fit involves no CLEAN or beam deconvolution but still inherits the self-cal model and subtracted sources (2020ApJ...902..141S).
- SR-18 | FIXED | Step 4, model table, a new parameter row and a referee check now describe the 500-run geometry perturbation (1 deg on i/PA, 1/3 beam on offsets) from 2025ApJ...986L..11S, framed as that paper's example of propagating geometry uncertainty.
- SR-19 | FIXED | Matched-filter bullet now states the co-spatial assumption and that template mismatch makes fluxes lower limits (pack lines 349, 497); use it for detection significance only.
- SR-20 | PARTLY | Added a requirement to test fitted turbulence against temperature and abundance assumptions, citing 2018ApJ...856..117F (mock tests recover temperature poorly, 20-50%, pack line 587). Not added: the cited claims about 2015ApJ...813...99F (temperature structure inflating turbulence) and 2017ApJ...843..150F (disk-averaged, intensity-weighted turbulence), because the rebuilt pack has no line supporting either (it lists only their fixed parameters and assumptions, lines 288, 328, 454, 481).
- SR-21 | FIXED | Not-stated checklist rebuilt from the current aggregate with summed counts: line-free channels (53), self-cal intervals (36), CASA/pipeline version (54), flux calibrator and flux-scale uncertainty (15), reference antenna (11), continuum-subtraction method/order (10); propagate continuum-subtraction uncertainty (2019ApJ...882..118X).
- SR-22 | FIXED | Step 1 now subtracts separable distant secondaries and fits close or blended ones jointly (700A.188C, pack line 951), and notes subtraction uncertainty (902..141S).
- SR-23 | FIXED | Chain-length row now has no default: convergence sets the run length, and the listed settings (including 865...37M keeping the last 5000 of 30000) are labelled historical examples.

## Other changes from the pack rebuild (not Codex findings)
- Software table recounted from the current aggregate (names now lower-cased and merged): emcee 74, uvmultifit 39, galario 33, RADMC-3D 26, MIRIAD 12, frank 2 (now in the aggregate); MPFIT dropped (no longer in the aggregate).
- Removed claims whose pack lines vanished in the rebuild: "formal only" (2016A&A...586A..99H), r0/alpha_out degeneracy (2017A&A...601A...7F), gap width vs depth (2017ApJ...851L..23C), real-part-only asymmetry loss (2017ApJ...839...99P). Replaced with supported degeneracies (2017ApJ...842....8M line 591, 2018ApJ...865...37M line 547) and the real-part axisymmetric fit of 2018ApJ...865...37M.

=== WRITER'S REFRESH NOTES ===
# Refresh notes: uv-plane-fitting (3,500-paper corpus, 2026-10-30)

Pack 278 -> 638 papers. Bibcodes cited: SKILL.md 68 -> 100 (with parameters.md 96 -> 133). SKILL.md 296 -> 334
lines (over the ~300 target). All SR-01..SR-23 fixes kept. Claims whose support the rebuilt pack no longer shows line-for-line (26,600
injections in 2017ApJ...850...83F, 600 klambda minimum in 2018ApJ...865...37M, 500 frank runs and AIC/BIC in
2025ApJ...986L..11S, 290 klambda null in 2014ApJ...791L...6W, Delta chi2 6.63 in 2025ApJ...986L..22R, joint
fit of close secondaries in 2025A&A...700A.188C, per-scan fits in 2020ApJ...894...76W) were checked against
their cards and kept; all cited bibcodes are in the new pack.

## Counts recomputed (pack aggregates unless noted)
- Software: CASA 105 -> 283, emcee 74 -> 136, uvmodelfit 39 -> 94 (56 + 38), uvmultifit 39 -> 86, galario
  33 -> 81, GILDAS 24 -> 77, RADMC-3D 26 -> 49, vis_sample 21 -> 37, MIRIAD 12 -> 21, LIME 7 -> 13, dynesty
  3 -> 9, frank 2 -> 14 (frank 7 + frankenstein 7). New rows: MultiNest 5, PyAutoLens 8, pdspy 7, pyralysis 4,
  imfit/GALFIT as cross-checks; AIPS, diskfit, lmfit, MPFIT, uvplot in one line. uvsim fell out of the top 40.
- Walkers (my count): 68 papers; 100 in 17, 200 in 12, 120 in 7; range 32-1024 -> 24-1024. Walkers per
  parameter 4 -> 7 papers (range 2-10). Chain settings ~40 -> ~90 papers. Priors: 29 papers.
- Weights: 6 -> 10 papers; factor range 0.25-0.4 -> 0.1-0.6 (2024PASJ...76..437Y 0.1-0.3, 2026ApJ..1005...94N
  0.2/0.6 per track). The summary now says "multiplied by 0.1 to 0.6" instead of "down by 2.5 to 4".
- uv cuts 6 -> ~19; uv bins 4 -> ~12 (range 5-150 klambda); time averaging 4 -> 8; model image 5 -> ~10
  (256-4096 px); frank settings 2 -> 7 (alpha up to 1.4, 2025ApJ...990L..70L); S/N cut 2 -> 4 (S/N >= 8-10).
- Not-stated settings re-summed: CASA/pipeline version 79, line-free channels 78, self-cal 55, image/cell 34,
  flux calibrator/scale 27, refant 12, contsub method 11, uvmodelfit start 11, coordinates 7, PB 5.

## New practice added
- Recentre via uvmodelfit + fixvis, check by imaginary-image RMS (2021ApJ...909..212K); Airy PB left ~5%
  residuals, fixed by a joint 4-field fit (2026A&A...707A.255C); per-pointing PB (2026A&A...705A.197Z).
- Astrometric systematic 5% of beam (2025Natur.642..905L); resolved-vs-point rule (2020MNRAS.492.3194S).
- Convergence checks from the pack: autocorrelation ~1000 steps (2019ApJ...874..136S), >= 1e5 post-convergence
  samples and dropping walkers 5 sigma low (2026A&A...705A.197Z), acceptance 0.2-0.5 (2020MNRAS.492..572A).
- Verification: size-recovery simulations and uvmodelfit vs imfit/GALFIT offsets (2020ApJ...888...44C),
  stacked-residual halo test (2025A&A...693A.237I), pixel-halving test (2024A&A...692A.155K), sideband
  agreement for flares (2022ApJ...939L...6B), multi-epoch fits with per-epoch centre and flux scale.
- Pitfalls: model choice and strict uv/velocity cuts (2024A&A...687A.308S); mixed-component models
  (2019MNRAS.487.4037D); warped belts (2026A&A...705A.197Z); missing flux in ACA sizes (2021A&A...653A..53A).
- Exponential disk: 2025A&A...693A.237I's R_e,major = 1.21 FWHM matches the general FWHM = 0.826 R_e.

## Source cards: out 2014ApJ...797...27F, 2023PSJ.....4..142C, 2014ApJ...792L...2C, 2015ApJ...811..124S,
2016ApJ...829L..23B, 2018A&A...617A..23B, 2020ApJ...894...76W, 2024A&A...689A.104D; in 693A.237I, 888...44C,
939L...6B, 909..212K, 705A.197Z, 687A.308S, 707A.255C (23 listed). No recommendation reversed.

=== EVIDENCE PACK (uv-plane-fitting, rebuilt) ===
# Evidence pack: Fitting models directly to visibilities (`uv-plane-fitting`)

Scope: parametric or non-parametric models fitted in the uv plane

Built from 638 non-held-out ALMA papers whose methods cards passed mechanical evidence verification (every quote below is verbatim from the paper). Years 2012-2026.
Matcher (regex over analysis steps): `uvmultifit|galario|vis_sample|uvmodelfit|visibilit\w* (?:fit|model)|(?:fit|model)\w* (?:\w+ ){0,3}visibilit|uv[- ]plane|uv[- ]?fit|in the uv`
Tagging is by regex, so a few papers may be off-topic: ignore those.

## Aggregates over all papers

### Science fields
- protoplanetary_disks: 226
- high_z_galaxies: 179
- star_formation: 135
- agn_and_quasars: 117
- astrochemistry: 105
- nearby_galaxies: 64
- debris_disks: 56
- stellar_physics: 39
- evolved_stars: 30
- exoplanets: 28
- solar_system: 22
- galaxy_clusters_and_sz: 21
- milky_way_ism: 21
- instrumentation: 11
- cosmology: 9

### Software named in the matched steps
- casa: 283
- emcee: 136
- uvmultifit: 86
- galario: 81
- gildas: 77
- casa uvmodelfit: 56
- radmc-3d: 49
- tclean: 41
- uvmodelfit: 38
- vis_sample: 37
- miriad: 21
- uvcontsub: 20
- imfit: 18
- lime: 13
- galfit: 13
- casa imfit: 13
- visilens: 9
- dynesty: 9
- aips: 9
- uvmcmcfit: 8
- pyautolens: 8
- pdspy: 7
- frank: 7
- frankenstein: 7
- diskfit: 7
- concat: 6
- lmfit: 6
- gildas uv_fit: 6
- python: 5
- ratran: 5
- scipy: 5
- difmap: 5
- eht-imaging: 5
- multinest: 5
- sextractor: 4
- pyralysis: 4
- miriad uvfit: 4
- mpfit: 4
- uvplot: 4
- fixvis: 3

### Fitting methods (most common phrasings)
- Gaussian in uv-plane: 2
- MCMC: 2
- MCMC with emcee, uniform priors: 2
- Grid search with chi2 minimization on visibilities; reduced chi2: 1
- chi2 minimization on visibilities: 1
- Polynomial fit to the noise ratio versus FWHM ratio: 1
- uv-plane model fit with GILDAS; uncertainties from the fit: 1
- Uncertainties on L_IR and M_dust by Monte Carlo simulations; points weighted by their uncertainties: 1
- Manual iteration of parameters to improve visual match; no sampler or priors: 1
- Iterative scaling of the input S abundance by the ratio of observed to model CS radial profiles, linearly interpolated …: 1
- uvcontsub polynomial fit of order 1: 1
- MCMC sampling (emcee) in the visibility plane; Deviance Information Criterion (DIC) used to select number of sources: 1
- Gaussian visibility fit with uvmodelfit.: 1
- emcee MCMC with χ² = sum of squared differences between binned observed and model real visibilities, divided by σobs,k²…: 1
- Vary stellar luminosity and Σ0 for observational agreement, then dust size; no full parameter-uncertainty modeling.: 1
- Compare model brightness-temperature profiles and SEDs; quantitative fitting statistic not stated.: 1
- 1D Gaussian fit using scipy curve_fit: 1
- Visibility fitting in UVMULTIFIT with uncertainties from the post-fit covariance matrix and error propagation: 1
- Kolmogorov-Smirnov test to compare size distributions across multiplicity classes: 1
- Single and double exponential disk fitting in UVMULTIFIT evaluated with reduced chi^2: 1
- uniform priors, likelihood ∝ exp(-chi2/2): 1
- same MCMC procedure as continuum: 1
- chi2 grid search: 1
- chi-squared grid fit; errors from chi2 distribution at 99.9% confidence: 1
- best f_snow = 0.55, chi2_r 1.78 vs 1.92 for f_snow=0: 1
- Gaussian fit in uv plane: 1
- Single Gaussian line fit, FWHM~500 km/s, reduced chi2 2.27: 1
- Point-source or Gaussian source models fitted to visibilities; image-plane 2D Gaussian: 1
- chi2 minimisation; uncertainties from post-fit covariance matrix: 1
- Linear (fitorder = 1) continuum fit per visibility: 1
- Image-plane imfit with a nuclear point source and an offset elliptical Gaussian: 1
- Bayesian nested sampling with dynesty, uniform priors; best fit = maximum posterior sample; uncertainties 95% inclusion…: 1
- emcee; best fit = max posterior, 95% range uncertainties; lost walkers redistributed: 1
- Log-likelihood proportional to -0.5 chi²; weighted squared real and imaginary visibility residuals. Priors not stated.: 1
- Median and 16th/84th percentiles for peaked PDFs; 99.7th-percentile upper limit when probability remains nonzero at zer…: 1
- 2D Gaussian fit to the continuum source using CASA imfit; linear power-law continuum fit in uvcontsub: 1
- MCMC in visibility space; sampler, priors and likelihood not stated: 1
- emcee affine-invariant ensemble MCMC with Gaussian likelihood in visibility plane: 1
- Visibility fitting of continuum spectral windows in AIPS: 1
- Per-channel visibility fitting in AIPS and GILDAS: 1

### Validation checks used
- agreement with previous observations: 2
- Detections at 4.5 and 5 sigma, with sigma from emission-free channels: 1
- Compare model and data radial profiles, spectra, integrated intensity maps and residuals: 1
- Residual maps; C18O residual above 3 sigma in the central region: 1
- Fluxes and sizes well recovered for large galaxies given enough S/N; similar results with GILDAS simulations: 1
- Detections robust against the model used for the 1D spectrum extraction; positions consistent with HST peaks: 1
- CASA uvmodelfit gives consistent fluxes; Gaussian model also consistent; channel-to-channel scatter consistent with err…: 1
- Expected false detections < 0.1 among the six sources for the 2.3 sigma tentative signals; average ratio from stacking …: 1
- Conclusions unchanged if upper limits are used in the fits; median L_IR and M_dust agree with literature MS values: 1
- C18O model radial profile matched to within ~10% interior to 200 au: 1
- Iteration stopped when CS profiles matched within 10% inside 200 au; test with all sulfur initially in SO and test with…: 1
- 140 GHz lens parameters compared and found to agree with Marrone et al. (2018) pixellated lens model: 1
- Compare C43-8 and C43-4 geometry fits; test the adopted center using imaginary-image RMS in step 6.: 1
- Compare observed and model visibilities; reduced χ² = 1.58 (upper) and 1.28 (lower); inspect posterior plots.: 1
- Compare major-axis profiles and residual maps; check agreement of residual patterns between upper and lower bands.: 1
- Central and upper-left features agree with model-subtracted images; fiducial Gaussian center has minimum RMS among test…: 1
- Temperature converges after 2–3 iterations; changing s from 0 to 0.5 affects midplane temperature by only a few Kelvin.: 1
- Compare SEDs beyond band 6 and test consistency of predicted instability with the absence of fragments.: 1
- Visual inspection confirming the +-2 sigma velocity range includes almost all [C II] line emission.: 1
- Checked residual maps for absence of >2 sigma peaks in the central 2" region and compared with ALPINE-only visibility f…: 1
- Checked positional offsets between [C II], UV, and FIR emission peaks.: 1
- Checked residual visibility flux excess at the shortest uv-distance bin (20 klambda) against standard deviation.: 1
- Best-fit model subtracted in image plane; residuals within noise: 1
- Compared model and data moment-0 visibilities; some residuals remain: 1
- Residual images with identical uv coverage: 1
- Check sources compared to reference positions (within 10 mas at 1.3 mm, 5 mas at 0.87 mm): 1
- Compare model peak offset with observed 46 mas: 1
- Qualitative reproduction of quadruple pattern; chi2 difference small: 1
- Compared CND fluxes with GB14 CO(3-2) and Krips CO(2-1) maps to check missing flux: 1
- Subtracted models give uniform residual noise maps; image and uv fits consistent: 1
- Residual images imaged and checked as Gaussian noise; Monte Carlo exploration of chi2 PDFs: 1
- Cases 2 and 3 tested; they produce faint, likely spurious spectral deficits or excesses near redshifted CO: 1
- imfit residuals show no additional sources within the inner 50 mas: 1
- Bayes factors between model complexities; residual images and visibility profiles: 1
- Compared models to ACA data not included in fit: 1
- Visual walker and likelihood inspection; discard burn-in and walkers at least 5 sigma below maximum log-likelihood.: 1
- Inspect height PDFs and compare with parametric and rave estimates.: 1
- Continuum flux density checked against the ~10% ALMA flux calibration uncertainty: 1
- Residual maps show no residuals above 3 sigma within 200 au; model without a gap fails to reproduce visibility wiggles …: 1
- Bolton ray tracing tested against Gravlens; residual maps inspected: 1

### Key parameters and settings (bibcode: value)
- 2017A&A...605A..21C: template 1'' beam via uv taper, 0.084 km/s channels
- 2017A&A...605A..21C: R_in = 50 AU for H2CO; Tc 12–36 K in 2 K steps; Rc 210–410 AU (H2CO), 70–350 AU (C18O) in 20 AU steps; X1/X2 0.001–10 (0.1–1000 for C18O)
- 2017A&A...605A..21C: Reference abundances 1e-12 (H2CO), 1e-7 (C18O)
- 2017A&A...605A..21C: H2CO X1 grid [1,2,3,4,5]e-12 with Rc = 270 AU
- 2018MNRAS.481.1976Z: Polynomial relation y = 1.00 + 0.79x + 0.14x^2 + 0.01x^3 between noise ratio y and FWHM ratio x
- 2018MNRAS.481.1976Z: Secure detection: emission line significance > 5 sigma in the optimal channel range
- 2018MNRAS.481.1976Z: Exponential model size = effective radius from HST stellar mass map (R_e in Table 2)
- 2018MNRAS.481.1976Z: Line map averaged over 719 km/s (3 x MAD redshift accuracy summed in quadrature with average detected line FWHM)
- 2018MNRAS.481.1976Z: Rest-frame 158 um continuum removed from the stack by reducing the flux by 10%
- 2018MNRAS.481.1976Z: L_IR integrated over 8-1000 um from SED fitting
- 2018MNRAS.481.1976Z: <U> = L_IR/(125 M_dust)
- 2024ApJ...973..135H: f_lg = 0.99 (model A) and 0.90 (model B)
- 2024ApJ...973..135H: Grain size distribution slope p = 3.5 (MRN)
- 2024ApJ...973..135H: Network of 131 species and 1721 reactions
- 2024ApJ...973..135H: Radial intensity profiles binned at 10 au
- 2021ApJ...921...97J: Briggs weighting, robust = 0.5
- 2021ApJ...921...97J: Spectral cube velocity averaging = 100 km s^-1; Moment 0 single channel width = 1000 km s^-1 (W) and 500 km s^-1 (E)
- 2021ApJ...921...97J: Spectral extraction apertures: 2.5'' (W) and 1.2'' (E)
- 2021ApJ...921...97J: 1000 MCMC chains; lens parameters constrained within best-fit values of 140 GHz single-lens model
- 2021ApJ...909..212K: i = 37.2° ± 0.026°; position angle = 32.4° ± 0.04°.
- 2021ApJ...909..212K: Adopt the geometry fitted to C43-8.
- 2021ApJ...909..212K: C43-8 only; fit 233.0 and 216.7 GHz separately.
- 2021ApJ...909..212K: Use ρ < 2000 kλ.
- 2021ApJ...909..212K: Fitting section: bins 10 kλ for ρ > 1200 kλ and 20 kλ for ρ < 1200 kλ; observations section gives the reverse.
- 2021ApJ...909..212K: Visibility errors: azimuthal standard deviation divided by square root of bin population.
- 2021ApJ...909..212K: 100 walkers; 1000 burn-in steps followed by 1000 steps.
- 2021ApJ...909..212K: Parameter minima and maxima listed in Table 2; Rcav range 0.0–1.9 au in both bands.
- 2021ApJ...909..212K: Use the observed-image procedure and Table 1 imaging parameters for mock and residual images.
- 2021ApJ...909..212K: Use C43-4 and C43-8, both upper and lower bands.
- 2021ApJ...909..212K: Shift the phase center by ±2 mas (±0.38 au) horizontally and vertically; compare RMS within 0.6 arcsec (114 au).
- 2021ApJ...909..212K: Fix structural parameters to Table 2 C43-8 values; use surface-density slope s = 0.
- 2021ApJ...909..212K: Radial grid: 0.1–1000 au, 256 logarithmic cells; angular grids: 256 each over 0 < θ < 2π and 0 < φ < π.
- 2021ApJ...909..212K: 3 × 10^8 photons for thermal Monte Carlo and imaging; 10^7 photons for SED.
- 2021ApJ...909..212K: L* = 11 L⊙ with Σ0 = 3 g/cm²; L* = 22 L⊙ with Σ0 = 1.5 g/cm².
- 2025A&A...693A.237I: 1-arcsec aperture; 20 km/s channel width; +-2 sigma velocity range (95% flux); nchan = 1
- 2025A&A...693A.237I: Sérsic index n = 1 (exponential disk); 6 free parameters (R.A., Decl., total flux density, major-axis FWHM, minor-to-major axis ratio q, position angle); q fix…
- 2025A&A...693A.237I: Excluded CRISTAL-21 from FIR size comparison due to unreliable FIR size measurement
- 2025A&A...693A.237I: 16 single galaxies; 20 klambda and 100 klambda uv-distance bins; average redshift z = 5.22
- 2019MNRAS.489.3670K: 100 walkers, 1200 steps after burn-in
- 2019MNRAS.489.3670K: 10 free parameters for double power law
- 2014ApJ...791L...6W: fluxes fixed at 0.962 and 0.024 Jy (302 GHz), 1.190 and 0.048 Jy (346 GHz)
- 2019ApJ...871..100H: Model A free parameters: Lstar, Mdisk, Rdisk, theta_flared, a_pow, a_max; r0 = 25 au
- 2018A&A...612A..29B: Visibility noise 7.5 uJy; flux 142 uJy
- 2018A&A...612A..29B: velocity range -800 to 800 km/s; 20 km/s binning for spectrum
- 2019A&A...632A..61G: 20 km/s channels
- 2021A&A...645A..33B: 40 km/s channels, natural weighting (except J1639+2824)
- 2021A&A...645A..33B: J1639+2824 taper beyond 900 klambda
- 2021A&A...645A..33B: Continuum-subtraction fit to |v|>500 km/s, first-order polynomial
- 2021A&A...645A..33B: uv channels averaged spectrally and temporally to 30 s
- 2021A&A...645A..33B: Gaussian preferred if size differs from zero at >3 sigma and detection significance increases
- 2018A&A...617A..23B: Gaussian position, flux density, FWHM; delta component at same position
- 2025ApJ...989...83B: Case 1: exclude |v_LOS - v_sys| < 500 km/s (used for the main emission and absorption results)
- 2025ApJ...989...83B: Case 3 (CO(1-0) only): exclude 100 < |v_LOS - v_sys| < 2200 km/s
- 2025ApJ...989...83B: 1-sigma flux limit delta S_ext = 0.75 mJy
- 2020ApJ...902..141S: Visibility weights multiplied by ~0.25 to match image RMS
- 2020ApJ...902..141S: Protostar T=4000 K, luminosity free; inner disk radius 0.1 au; cavity or gap added
- 2026A&A...705A.197Z: Gaussian primary beam approximation; mosaic treatment for HD 39060.
- 2026A&A...705A.197Z: Stellar flux added in visibility domain at disk center; dRA and dDec free.
- 2026A&A...705A.197Z: 64 walkers; at least 10^5 post-convergence samples, approximately 1500 steps per walker.
- 2026A&A...705A.197Z: Fit inclination, PA, surface density normalization, stellar flux, dRA, dDec and radial/vertical form parameters.
- 2026A&A...705A.197Z: AU Mic: three separate stellar flux values.
- 2026A&A...705A.197Z: Fix PA, inclination and offsets to Marino_2026.
- 2026A&A...705A.197Z: Narrow height grid around probability mass; quadratic interpolation.
- 2026ApJ..1005...94N: visweightscale = 0.6 (2019.1.00036.S) and 0.2 for each of the two 2018.1.00397.S tracks
- 2026ApJ..1005...94N: Briggs robust = 0.5, pixel scale = 0.04'', image size = 512 x 512 pixels^2, channel width = 10 km s^-1, clean threshold = 1.5 sigma_RMS
- 2020MNRAS.498.1319M: Gap depth fixed to 1
- 2020MNRAS.498.1319M: Vertical extent fixed to 5% of radius, uniform vertical mass distribution
- 2020MNRAS.498.1319M: r_min lower limit of 14 au; outer edge fixed at 250 au
- 2020MNRAS.498.1319M: Free parameters include disc inclination and PA, phase centre offsets, and position, size (2D Gaussian) and flux of a background SMG ~11.5'' to the SW; spectra…
- 2020MNRAS.498.1319M: Reported values are posterior medians with 16th and 84th percentile uncertainties
- 2015ApJ...812...43B: 512 walkers; burn-in 500-1000 iterations; final 10 iterations
- 2015ApJ...812...43B: uniform priors; theta_E 0.1-6 arcsec; q_lens>0.3; q_s>0.2; r_s 0.01-1.5 arcsec
- 2022Icar..37214722L: Continuum flux density set to 17.5 mJy at CO(3-2), 18.3 mJy at HCN(4-3), and 11.1 mJy at HNC(3-2)
- 2022Icar..37214722L: Maximum u-v range = 1000 klambda; Pluto continuum disk = 0.1009" with limb darkening exponent 0.1
- 2022Icar..37214722L: Prescribed CO emission size = 1.01, 1.05, 1.40 x Pluto diameter at 5, 1, 0 MHz from line center; HCN emission size = 1.00, 1.40, 1.78 x Pluto diameter at 0.6, …
- 2022Icar..37214722L: Pixel size = 0.01" (CO/HCN cube), 0.1" (HNC cube); spectral binning factor = 4 (HNC setup)
- 2024A&A...687A.308S: Free parameters include M*, M_disk, R_disk, gamma, T0, q, a_turb, i, p.a., v_sys, x0, y0 (R_in free for A, fixed at 0.1 au for B and W)
- 2024A&A...687A.308S: Strict priors on source position so each source is fit separately
- 2024A&A...687A.308S: Channel cuts: exclude 3.25-5.5 km/s for A and -2.5 to 6.75 km/s for B
- 2024A&A...687A.308S: uv cuts: exclude uv < 100 klambda for B and < 200 klambda for W
- 2020ApJ...888...44C: Briggs robust 0.5; natural weighting for stack
- 2020ApJ...888...44C: sizes 0.10-0.40 arcsec, fluxes 0.25-2.00 mJy, 300 s
- 2020ApJ...888...44C: UVMODELFIT starts from IMFIT values, five iterations
- 2022ApJ...939L...6B: natural weighting
- 2022ApJ...939L...6B: ten source-free regions for rms calculation
- 2022ApJ...939L...6B: integration time = 6 sec (ALMA 12-m) and 10 sec (ACA)
- 2022ApJ...939L...6B: detection threshold > 3 sigma
- 2022ApJ...939L...6B: sideband flux agreement within 20%
- 2022ApJ...939L...6B: upper (230 + 232 GHz) and lower (219 + 217 GHz) sidebands
- 2022ApJ...939L...6B: ALMA XX and YY polarizations at flare peak
- 2022ApJ...939L...6B: Exclude flaring intervals E1, E2, and E3
- 2015A&A...582A..91C: 20 km/s common resolution
- 2019ApJ...882..118X: Briggs robust 0.5 (B4, B6), 0.0 (B7)
- 2025ApJ...986L..22R: Lp=0 assumed for geometry; free Q1,Q2,v1,v2,gamma,phi,psi
- 2025ApJ...986L..22R: Tss=95±9 K (NEATM) or 60 K (CO)
- 2019MNRAS.487.4037D: Free: Pei, rs (uniform priors), point-source position, flux, spectral index; kappa Gaussian, eta exponential hyperparameters
- 2014A&A...566A..74L: PA -65 deg, centre LSR velocity 6.2 km/s
- 2014A&A...566A..74L: free parameters: central mass and disc radius
- 2021A&A...653A..53A: Position, flux, major axis, minor-to-major axis ratio, and position angle.
- 2021A&A...653A..53A: Central-channel Gaussian major axes and axis ratios.
- 2021A&A...653A..53A: Error: average error from the two channels on each side of the central velocity channel.
- 2018AJ....156..164B: Eris visibility fit: slightly limb-darkened disk, radius 1163 km; others point sources
- 2021A&A...650A.153D: ASKAP: two Taylor terms; convolve 36 single-beam images to 18″ FWHM; linear mosaic; spectral index T1/T0
- 2021A&A...650A.153D: ATCA: eight spectral windows for calibration; primary calibrator 1934-638; interleaved calibrator amplitude/phase solutions
- 2021A&A...650A.153D: ATCA 2.1 GHz: natural weighting and three phase self-calibration rounds; whole-band multifrequency synthesis
- 2025A&A...704A..18O: Uniform elliptical disk model
- 2015ApJ...798..124R: model image 2048x2048 pixels of 0.015''; flux scaled as nu^(2+beta), beta=0.4
- 2021A&A...647A..87L: SMM1-a extraction position: α_J2000 = 18:29:49.793, δ_J2000 = +1.15.20.200
- 2021A&A...647A..87L: Line-free bandwidth fraction: ≥20% (10% in two spectral windows)
- 2026ApJ..1000..141K: two-point-source model with separation ~0.3 arcsec
- 2015MNRAS.452...88K: moment 0 over 337.3-338.2 GHz; moment 1 pixels with S/N ≥4 of ~2 mJy rms
- 2026A&A...707A.255C: reference frequency nu_0 = 40.15 GHz; 60-channel bins; 4 nearest fields used for DoAr 21, closest field for SR 4 and ISO-Oph-17
- 2026A&A...707A.255C: 120-channel average (16 channels); reference frequency nu_0 = 36.63 GHz; pure-chi2 template (lambda = 0)
- 2024A&A...682A.186L: uv upper threshold 65 klambda
- 2024A&A...682A.186L: SZ centroid fixed to X-ray centroid so that only the mass term (M500) is free per pressure model
- 2024A&A...683A..62M: Source positions fixed at continuum locations; amplitude per spectral channel free
- 2024A&A...683A..62M: Continuum levels used for normalization: 1.3 Jy (NE) and 1.0 Jy (SW) at 250 GHz
- 2022A&A...666A..39M: 4 s cadence
- 2022A&A...666A..39M: 4 fitted parameters per integration time: F_ext, F_SgrA*, delta_ra, delta_dec
- 2022A&A...666A..39M: Detection threshold: peak excursion of 7 times the instantaneous rms between consecutive images; at least 3 standard deviations in maxima between two consecuti…
- 2022A&A...666A..39M: Minimum duration: 12 s (three 4 s integration times)
- 2025MNRAS.543..862V: Clean region twice the primary beam FWHM, down to 2x expected RMS (2.5x with A configuration)
- 2025MNRAS.543..862V: UV-plane point-source fit is the formal detection criterion; 3 sigma upper limits for non-detections
- 2025MNRAS.543..862V: Light curves in 1-minute bins assessed with reduced chi-square of a constant fit
- 2014A&A...563A.136M: PKS 1830-211: relative position bounded within 10 mas of VLBI astrometry
- 2014ApJ...792L...2C: v = 1.0 km/s (ISON), 0.7 km/s (Lemmon) from HCN HWHM
- 2023MNRAS.520.1613M: Binned pixel scale = 0.01'', synthesised beam = 0.0308'' x 0.0235'' at PA = 15 deg, rotation PA = 11.9 deg, calibration error = 10%
- 2018ApJ...865...37M: Free: i, PA, dRA, dDEC, and a_i, sigma_i, x_i per ring
- 2018ApJ...865...37M: Mdot fixed at 7.8e-9 Msun/yr; alpha varied 0.0001-0.01; Rwall 25-40 au; mid amax 1 mm-2.5 cm; eps_atm 0.001-0.8; Rdisk 150-300 au
- 2019ApJ...882..107R: all parameters free; fluxes corrected with tclean primary beam
- 2026A&A...705A..49Z: 250 burn-in steps; 90 walkers; 1000 steps before first convergence check
- 2026A&A...705A..49Z: Stop when relative change in the median of each parameter is below 5% over the last 500 steps; otherwise continue
- 2026A&A...705A..49Z: Priors chosen per disk for inc, PA, v_sys, M*, r_tau and r_z from the channel maps; Gaussian and uniform priors (example in Table 3)
- 2026A&A...705A..49Z: Best fit = median, uncertainties = 68% interval of posterior
- 2026A&A...705A..49Z: image size 1500 pix, cell 0.01 arcsec, scales (0, 10, 30, 60), robust=1, threshold 20 mJy per beam, Keplerian mask
- 2020ApJ...904..131N: Corrected flux F = C + eps R = eps D, eps = C/(D-R) in the aperture
- 2020ApJ...904..131N: Aperture error approximated by rms x sqrt(N beams)
- 2021ApJ...908..250H: 8 free parameters (F_total, r_cav1, r_cav2, delta, gamma1, gamma2, i, PA); phase center fixed
- 2021ApJ...908..250H: 2000 burn-in steps plus 2000 steps, 4000 total, 200 walkers
- 2021ApJ...908..250H: Outer radius of model 300 au; delta left free after delta=0 failed
- 2021ApJ...908..250H: Band 3 1.70 +/- 0.06 mJy, Band 6 13.43 +/- 0.13 mJy, Band 7 33 +/- 0.4 mJy
- 2021ApJ...908..250H: PA 165.71 deg and i 75.13 deg taken from the visibility fit
- 2021ApJ...908..250H: Free parameters r_cav1_large, r_cav2_small, h_small(100 au), M_disk
- 2021ApJ...908..250H: r_cav2_large fixed to 26 au from the visibility fit
- 2021ApJ...908..250H: q1 = -1.0, q2 = 4.5 (fiducial)
- 2021ApJ...908..250H: Scale height of large grains fixed at 1 au at 100 au; small grains varied to match 60-70 um flux
- 2021ApJ...908..250H: Large-grain mass fraction 0.9; accretion rate 1.3e-9 Msun/yr; inclination 75 deg
- 2025PASP..137l4501T: uvmultifit with OneFitPerChannel = True, write = residuals; Gaussian or delta model
- 2025PASP..137l4501T: Natural weighting, Hogbom, cell = 1/5 of the beam major axis
- 2025PASP..137l4501T: Unresolved case: flux taken as peak value in the image; resolved case: flux in circular aperture of radius 3 sigma of the Gaussian
- 2018MNRAS.479.5423M: 19 free parameters; h>0.03 prior
- 2013ApJ...774...16R: Mgas=0.09 Msun, gamma=0.8, rc=150 AU, Tfrz=19 K, sigma_s=9e20 cm^-2, Tm=19K (r/155AU)^-0.3
- 2013ApJ...774...16R: xi=0.01 km/s, i=224 deg, PA=312 deg
- 2016A&A...590A..33P: q=0.5, T0=1500 K at 0.1 AU, Tmin=10 K, inner radius 0.1 AU, Tavg=30 K for Gaussian mass
- 2018ApJ...856L...5F: Single vs double Gaussian compared with reduced chi2
- 2018ApJ...869...27V: line width and centre fixed from high-SN CO lines
- 2021A&A...654L...8C: robust = 0.5; uv taper 4 arcsec; maximum spectral resolution 22 km/s
- 2021A&A...654L...8C: Gaussian FWHM = 300+-80 kpc
- 2017NatAs...1..848V: Strongest hotspot SNR=59; 5 sigma size limit <2x3 mas
- 2025A&A...699A.279D: One Bayesian model: 64×64 raster over 200 μas; extended Gaussian size fixed at 1000 μas.
- 2025A&A...699A.279D: Gains vary every scan; ALMA phase fixed to zero, otherwise the next station alphabetically is the reference.
- 2020A&A...636A..26H: q = 0.35, 0.4, 0.5; Sigma ~ R^-1
- 2026A&A...705A.196H: alpha sets the minimum S/N down to which visibilities are fit
- 2026A&A...705A.196H: w_smooth sets smoothing of the reconstructed power spectrum
- 2026A&A...705A.196H: Number of radial points N and outer radius R_out chosen per source; final per-target values (alpha, w_smooth, N, r_out) tabulated
- 2026A&A...705A.196H: Stellar flux subtracted from real visibilities as a constant offset (none subtracted for HD 109573; SED flux for HD 32297)
- 2026A&A...705A.196H: PA, inclination and centring offset fixed to ARKS paper I values
- 2026A&A...705A.196H: Functional forms: double/triple power law, power law + error function, Gaussian, asymmetric Gaussian, double/triple Gaussian, Gaussian + double power law, opti…
- 2026A&A...705A.196H: Vertical aspect ratio h_HWHM fixed at 0.015 by default, with exceptions for some discs
- 2026A&A...705A.196H: Certain shape parameters fixed to reduce degeneracies
- 2025MNRAS.537..520Z: Briggs robust = 0.5 (and robust = 2.0 for warp/non-circular motion analysis); channel width 20 km s^-1; rest frequency 230.538 GHz; clean threshold 1.5 sigma_R…
- 2020ApJ...898..146M: 2000 steps, 40 walkers, uniform priors, likelihood exp(-chi2/2), free weight scaling
- 2020ApJ...898..146M: aspect ratio h fixed to 0.03; walkers = 10 x free parameters; 2000 steps
- 2015ApJ...811..124S: Each Gaussian has up to four free parameters: centroid, flux, size
- 2022A&A...659L...1L: Rescaling factors: 0.99 (SB1) and 0.995 (SB2)
- 2022A&A...659L...1L: Assumed flux calibrator fluxes: 1.22 Jy for J2258-2758 and 1.26 Jy for J0519-4546
- 2022A&A...659L...1L: uv-radius bin width: 400 m
- 2026A&A...708A.251X: 36.3'' coarse resolution with 14.0'' pixel size; 18'' medium resolution; 6.2'' high resolution
- 2026A&A...708A.251X: uv overlap between 18.2'' and 28.0''
- 2020A&A...633A.134L: upper limit S_CO,wings < 10 x RMS_200 x 200 for non-detections
- 2013PASJ...65..100I: pixel 0.3 arcsec; 20 channel binning to ~8.5 km/s
- 2019ApJ...871..112X: robust 0.5, cell 0.3 arcsec
- 2025NatAs...9.1476C: 4 T(r) segments for Apr 18–25; 3 for May 4
- 2016ApJ...829L..23B: Free: pressure amplitude, shock radius, Mach number; slopes consistent with X-ray; outer slope marginalized within 30%
- 2020A&A...640A.133R: Error = average error of fits in the two channels adjacent to center velocity; colon marks uncertain values
- 2020A&A...640A.133R: 32×32 pixels of 0.8″ (CO 2-1) and 0.7″ (CO 3-2)
- 2020PASJ...72...33K: Four compact sources detected above 5 sigma
- 2020PASJ...72...33K: C2 modelled as elliptical Gaussian with major-to-minor axis ratio fixed at 0.05
- 2013ApJ...777L..25M: smax fixed 3000 um; smin 4, 6, 8, 16 um
- 2021A&A...652A...5M: v_Helio = v_LSRK - 12.4 km/s
- 2021A&A...652A...5M: Phase-only gain corrections every 6 s
- 2026A&A...706A.365M: Relative positions of the two point sources fixed at the known locations of the lensed images
- 2026A&A...706A.365M: Visibilities self-calibrated before extraction
- 2013A&A...558A.123M: Line-free channels remaining typically >2000
- 2024ApJ...967..164X: VLA cell size = 0.27'', natural weighting, auto-masking
- 2024ApJ...967..164X: ALMA synthesized beam = 2.23'' x 1.67'' (84 GHz) and 1.94'' x 1.49'' (95 GHz), median RMS = 4 mJy beam^-1
- 2018A&A...615A..95P: PA=12.0±0.9 deg, i=37.3±0.6 deg
- 2018A&A...615A..95P: 200 walkers, 1000 steps; r_peak in [1,150] au, sigma in [1,50] au, F in [0,0.1] Jy; radial grid 0-500 au step 0.25 au
- 2017ApJ...850...83F: sizes 0.04''-3.0''; random positions within 10'' radius; SNR bins 5-10, 10-20, 20-30
- 2025ApJ...986L..11S: 192 walkers, flat priors, converged after ~10^4 steps, then 10^4 more
- 2025ApJ...986L..11S: 100 walkers, 10000 steps
- 2025ApJ...986L..11S: alpha=1.20, w_smooth=1e-3, N=400, Rmax=4 Rout
- 2021ApJ...917...99Y: Lens redshift = [0.67], Source redshift = [6.5187], Lens Mass = [2.06x10^10 M_sun], Lens e = [0.65], Lens PA = [94.58 deg] (in default model)
- 2021ApJ...917...99Y: source-plane pixel size = 0.04''
- 2021ApJ...917...99Y: integrated flux SNR > 10 threshold for moment 1 and 2
- 2023A&A...676A...4C: 10 free parameters: I_0 (f_0), r, sigma, inc, PA, R_in, R_out, p, dRA, dDec
- 2023A&A...676A...4C: Flux calibration uncertainty: 10% for B7, 5% for B3, B4, B6
- 2023A&A...676A...4C: Angle sectors: envelope (-20 deg < PA < 20 deg), outflow (70 deg < PA < 110 deg), cavity walls (remaining zones)
- 2026A&A...709A..14Z: 3x velocity binning from native 6.5 - 13.5 km s^-1 resolution
- 2026A&A...709A..14Z: 3 sigma detection threshold; 3 sigma upper limits using CO(2-1) channel range for non-detections
- 2017MNRAS.465.2595M: Visibilities averaged to 3 min and 2 GHz bins; 300-1000 steps, 50-180 walkers
- 2014ApJ...791...20R: R_in = 0.05 AU; free parameters M_disk (Sigma_10AU), p, R_out
- 2014ApJ...791...20R: Grain size distribution n(a) ∝ a^3, amin 0.1 micron; T_ext = 10 K (5, 15 K tested); T ∝ R^-3/4 beyond R_thin
- 2017ApJ...849...56A: Free: Mdisk, Rout, p, Sdamp, H1, h; fixed: i=85 deg, Rin=0.1 AU, T1=403.5 K, q=0.5, kappa=0.031, g/d=100; outer radius 1000 AU
- 2019A&A...628A.118B: natural weighting, 0.04 arcsec pixel, 30 km/s channels
- 2018ApJ...859...35G: 5"x5" extraction region at peak pixel
- 2021A&A...654A..37D: Extraction diameter 1″; W0410–0913: 2.5″; centered on emission peak
- 2021A&A...654A..37D: Direct line integration within ±2.5 σ of the fitted peak
- 2026MNRAS.546ag167S: CO velocity integration ranges (FWHM): 455 km s^-1 (J1236+0500), 220 km s^-1 (J2317-1033), 480 km s^-1 (J2345-1104)
- 2026MNRAS.546ag167S: Continuum Spergel index tested for 3 cases: fixed to CO fit value, fixed to -0.3, and free
- 2020A&A...633A.126B: kappa 345GHz = 0.02 cm2/g gas; Tdust ~30 K
- 2026A&A...706A...4R: Minimum u-v distance 600 klambda (lower setup) and 700 klambda (higher setup), chosen visually
- 2026A&A...706A...4R: 110 walkers, 10000 steps, burn-in of 400 steps discarded
- 2026A&A...706A...4R: Vertical aspect ratio fixed at 0.05; free parameters include i, PA, R and Delta R (Gaussian) or R_in, R_out, p (power law), disk and star fluxes per setup, RA/…
- 2026A&A...707A.144S: robust = 0.5
- 2026A&A...707A.144S: Continuum subtracted in uv plane with order 0 baseline
- 2026A&A...707A.144S: Channels of 7.8 MHz (~10 km/s)
- 2021AJ....161..271F: 22 free parameters (Model 1), 24 (Models 2, 3)
- 2021AJ....161..271F: Surface density zero inside 70 au and beyond 600 au for Models 2 and 3
- 2015ApJ...810..133I: S/N>=10 threshold
- 2021PSJ.....2....3M: Self-calibration solution intervals of 20, 10, 5, and 1 minutes
- 2024A&A...682A..61C: Inner Gaussian extends 1.4 arcsec (2 sigma, 574 au)
- 2024A&A...682A..61C: uv-plane check: uvmodelfit point source, 16.1 mJy in B6 and 2.6 mJy in B3
- 2022MNRAS.516.4066L: Högbom deconvolver, Briggs robust = 0.5, cleaned down to ~3 sigma, 15 km/s channel binning, GIPSY Boolean mask smoothed to 0.4'' clipped at 3 sigma_s
- 2021A&A...647A.173K: Flagged first 10 channels in spw 2 (both epochs); flagged DA63 (Epoch 1) and DA41 (Epoch 2) all spws; flagged DA42 and DA48 spw 1 (Epoch 2)
- 2021A&A...647A.173K: Scan length ~10 min for intra-epoch timing
- 2015ApJ...811...39I: gain 0.1, threshold 1.0 mJy
- 2026ApJ...999L..32R: CH3OH-H2O average collisional cross-section = 5 x 10^-14 cm^-2
- 2026ApJ...999L..32R: Q(OH) = (5.7 +/- 0.6) x 10^28 s^-1 at r_H = 1.43 au; branching ratio = 85.5%
- 2026ApJ...999L..32R: 3D cone geometry: phi = phi_STO, psi = psi_sun, gamma = 90 deg
- 2019A&A...628A.100D: Priors in Table 1: P_e,us and T_e,us split-normal from X-ray; shock nose and angle split-normal; M uniform 1-10; alpha uniform -10 to 0; kappa normal(1,0.05)
- 2020CPhy...30...85D: |Vz| > 8 km s^-1; aperture radii R < 1.5 arcsec and R < 0.3 arcsec
- 2023PASJ...75..311K: baselines > 15 klambda
- 2023PASJ...75..311K: detection threshold 5 sigma
- 2013ApJ...762L..21M: ~10^6 MCMC trials; 12 free parameters
- 2018ApJ...856..117F: Free: T_atm0, T_mid0, q_atm, R_c, inclination, δv_turb; fixed: stellar mass, distance, CO abundance, PA, systemic velocity, offset
- 2019MNRAS.485.2092C: Stack velocity width 753±22 km/s; errors scaled so Var(S/sigma)=1 in line-free channels
- 2019MNRAS.485.2092C: <U>=22; L_IR/Md factor 125; 0.15 dex systematic
- 2024A&A...692A.155K: Visibilities averaged to one channel per spw and 24 s; epochs not combined
- 2024A&A...692A.155K: All five epochs fit simultaneously with common intensity model but separate disk centers per epoch
- 2024A&A...692A.155K: Free per-epoch flux scale i_obs, SB4 fixed to 1
- 2024A&A...692A.155K: Model pixel size 4 mas (2 mas test gave consistent results)
- 2024A&A...692A.155K: Same procedure as the main visibility fit
- 2021ApJ...914...36I: 20 klambda uv bins; FIR range 42.5-122.5 um; TIR range 8-1000 um
- 2021ApJ...914...36I: Core frequency range 235.270-235.455 GHz; Wing uv fit frequency ranges 234.970-235.166 GHz and 235.559-235.756 GHz (+/- 250-500 km s^-1), 50 klambda bins, <300…
- 2020ApJ...891...48H: 96 walkers, 20,000 steps, 10,000 burn-in; weights scaled down by 2.667
- 2020ApJ...891...48H: 512 radial cells, 1024 poloidal cells, 64 azimuthal cells, 10^8 photon packages; parameters in Table 4
- 2024MNRAS.528.5019H: pixel 0.2 arcsec (deep tapered), primary beam cutoff 0.2; wide map pixel 0.12 arcsec, cutoff 0.4
- 2024MNRAS.528.5019H: clean threshold 20 uJy/beam (deep), 100 uJy/beam (wide)
- 2024MNRAS.528.5019H: common beam from the largest beam; 0.2 arcsec grid spanning 5 arcmin; Gaussian apodization with sigma equal to beamsize out to 3 x beamsize
- 2019MNRAS.484.1257M: stellar template Teff 5250 K, radius 0.77 Rsun; h>0.02 imposed
- 2019MNRAS.484.1257M: 11 free parameters
- 2012ApJ...757..129R: PA fixed 151 deg; M*=0.8 Msun; inclination free; T10,q free per line
- 2017AJ....154...24R: gamma = 1; q between 0 and 3/4; gamma_e <= 2
- 2017MNRAS.468.4205K: aperture radius ~1.5" (C1591, C92), ~1" (#226)
- 2020MNRAS.496..598C: Extended CO(3–2): 137.714–137.980 GHz; extraction radius 0.7″
- 2020MNRAS.496..598C: Compact CO(3–2): 137.7–138.0 GHz; CO(2–1): 91.8–92.0 GHz; extraction radii 3″
- 2018A&A...610A...4G: SD 0-20 m added, scaled by 1.7 (SMA)
- 2024ApJ...977..190X: Bin spectra to 64–77 km/s.
- 2024ApJ...977..190X: Integrate intensity maps over 1.5 × FWHM_line.
- 2024ApJ...977..190X: J0129-0035 CO (10-9) 3σ upper limit: channel width 74 km s−1 and line range 275 km s−1.
- 2020ApJ...902..132B: position, intensity, sizes and orientation free
- 2024A&A...686A.206Y: data averaged to 10 s and four channels per spectral window, weights recomputed with statwt
- 2024A&A...686A.206Y: 100 walkers, 1000 steps, first 900 discarded as burn-in
- 2024A&A...686A.206Y: modified blackbody: lambda0 = 380 um, beta = 2.3 (cold); lambda0 = 160 um, beta ~ 0 (warm)
- 2024A&A...687A.193W: integration area ~ 50 x 50 mas, channel width 3.8 km s−1
- 2020RSOS....700063K: MultiNest with 75 live points; only MultiNest results reported
- 2020RSOS....700063K: Four model variants per target: Gaussian or Uniform semi-major axis distribution, each full or simple
- 2025A&A...700A.188C: Uniform priors: sigma 0-0.7'', Ri 0-2.0'', Rout 2.0-15.0'', p+q in [1,3], inc/PA full range, offsets within few tenths of arcsec
- 2025A&A...700A.188C: 120 walkers, 25000 steps
- 2022ApJ...926..159I: Briggs weighting, robust = 0.5, gain = 0.1; 20-channel binning (~35 km/s) for ULIRGs, 10-channel binning (~20 km/s) for NGC 1614; pixel scale 0.025''-0.1'' pix…
- 2021MNRAS.502..521D: 5-min time intervals for ATCA; 30-sec time intervals for ALMA
- 2025PSJ.....6..183C: baselines longer than 200 m excluded
- 2025PSJ.....6..183C: 5% flux scale error included in Tb uncertainty
- 2019A&A...629A.104G: initial free-position fit in uv=6-25 m
- 2021A&A...651A...4B: Velocity channels resampled to 0.8 km/s; continuum subtracted in the uv plane except for J=6-5
- 2020A&A...638A..70D: free: M500, z, centroid, point source positions and fluxes, flux normalization
- 2017ApJ...846L..26W: Free: Mdisk, Rdisk, gamma, T0, q, xi, M*, vsys, inclination, PA, small centering offset
- 2017ApJ...846..108C: 36000 injected models, peak SNR 1-10, radius up to 2''
- 2024MNRAS.532.1752R: galario grid: CIDA 9 0.012'' (2 au) pixels, 2048 pixels; RY Tau 0.0031'' (0.4 au) pixels, 4096 pixels; fine wall grid 0.05 au
- 2024MNRAS.532.1752R: 10 free parameters: r_wall, H_wall, F_wall, F_ring, sigma_ring, i, PA, dRA, dDec, flux scale A
- 2024MNRAS.532.1752R: robust = 0.5 for residual images
- 2023MNRAS.524..923Z: 2D PSF (point-source) model in uv plane
- 2023MNRAS.524..923Z: 5 sigma upper limit at fixed CO position
- 2020A&A...635A..12P: inner radius 169 au; scale height 24 au at 200 au; V0=3.37 km/s; dV=0.3 km/s
- 2017ApJ...842....8M: Free: R_belt, Δa, F_belt, F_star, i, PA, e_f, e_p, ω_f, Δα, Δδ
- 2015ApJ...806..154C: 12 free parameters: T10, q, Mco, rc, xi, M*, i_d, phi, offsets, vsys, d; gamma fixed to 1
- 2017ApJ...849...14S: r2G: baselines <0.2 Mlambda flagged
- 2020MNRAS.492.3194S: phase centre taken from the peak of the High Resolution images, using fixvis
- 2020MNRAS.492.3194S: uv-distance bins of 50 klambda
- 2020MNRAS.492.3194S: Gaussian model accepted only if Delta BIC >= 2; unresolved sources get the beam size as an upper limit
- 2024A&A...682L...3P: 3g model adds six degrees of freedom over the 2g compact model
- 2024A&A...682L...3P: Fit data: 86 visibility amplitudes, 14 non-trivial closure phases, 80 absolute fractional polarisations
- 2024A&A...682L...3P: Net polarisation: image-domain Stokes sum over the whole field of view
- 2020ApJ...903...50E: Briggs robust = 0.5
- 2020ApJ...903...50E: line cubes smoothed to 2.93 MHz channels (8.9 and 10.3 km/s)
- 2026A&A...705A.202M: Axisymmetric component: double power law fitted to the azimuthally averaged radial profile
- 2026A&A...705A.202M: Arc component: 2D Gaussian in r and azimuth, with separate azimuthal widths on the leading and trailing sides
- 2026A&A...705A.202M: Free parameters also include inclination, position angle, and RA/Dec offsets
- 2026A&A...705A.202M: Dust opacity 1.9 cm2/g at 0.89 mm
- 2024MNRAS.532.4645H: L_bol,AGN = 5.5e42 erg/s from bolometric correction to L(2-10 keV)
- 2024MNRAS.532.4645H: Shock v_s = 250 km/s, n = 4350 cm^-3, G0 = 653 F_T
- 2021MNRAS.506.1978L: SYM: 12 parameters, 120 walkers, 600 steps, 250 burn-in; CL: 18 parameters, 180 walkers, 1600 steps, 1000 burn-in; ECC: 14 parameters, 140 walkers, 1000 steps,…
- 2015ApJ...799...81S: free parameters: position, peak flux, major/minor axis, PA
- 2024ApJ...963..164R: uv-distance > 400 kλ; phase center within 0.5" of published positions
- 2021A&A...654A..24B: robust = 2.0, hogbom deconvolver, limiting flux threshold optimised per case
- 2021A&A...654A..24B: Line cubes with channel width ~10 and ~30 km/s and pixel size about 1/5 to 1/4 of the synthesised beam
- 2021A&A...654A..24B: Continuum image built from all continuum channels of the four spectral windows, discarding CO(2-1) channels
- 2020PASJ...72...36T: robust = 0.5; beam 0.41 x 0.30 arcsec, PA=-77 deg; 0.2 mJy/beam in a line-free channel; phase calibrator J1744-3116
- 2020MNRAS.494.1323D: Higher weighting to shorter baselines in the second stack
- 2019ApJ...878...16P: PA 26.8±1.3 deg, inclination 47.6±2.4 deg
- 2019ApJ...878...16P: 200 walkers, 2000 steps, uniform priors (r_peak 10-80 au, sigma 1-50 au, A 0-1, sigma_inner 0.1-10 au, F_total 0-3 Jy)
- 2017MNRAS.469.4683C: Delta v ~ 1680 km/s
- 2017MNRAS.469.4683C: Assumed clump line FWHM 100 km/s; mean clump FWHM 0.18 arcsec for stack
- 2025A&A...696A.232G: 48 to 120 walkers, 2,000 to 30,000 steps; first 1,000 steps discarded as burn-in; binaries needed more walkers and iterations
- 2025A&A...696A.232G: Initial parameters from UVMODELFIT for single disks
- 2025A&A...696A.232G: Final values are posterior medians with 16th and 84th percentile uncertainties
- 2025A&A...696A.232G: Inclination and PA fixed to face-on / P.A. fixed to 0 for unresolved or poorly constrained disks
- 2025A&A...696A.232G: R68 definition (68% of total flux)
- 2020Natur.584..201R: conjugate gradient tolerance 1e-12 (typical source-inversion accuracy 1e-6)
- 2020Natur.584..201R: 163190 visibilities per channel
- 2020Natur.584..201R: rotation curve function V_t, R_t, beta, xi; exponential velocity dispersion profile; no radial variation of inclination and position angle; gas surface density…
- 2020Natur.584..201R: four-step optimisation scheme for lens mass model and source kinematics
- 2023NatAs...7..684K: cell size = 0.5", image region = 20"x20", velocity integration range = -14.5 to 25.5 km s-1, elliptical aperture radius = 5.0"
- 2023NatAs...7..684K: uvmodelfit channels = ±10 km s-1 from source velocity, 20 iterations (converging after ∼8)
- 2025MNRAS.537.1163A: Pixels shown only where SNR_G > 5 (SNR_G^2 = chi2_G - chi2_line)
- 2018MNRAS.474.4500W: Uncertainties: sigma_rms plus 5% (VLA) or 10% (ALMA) calibration, in quadrature
- 2013ApJ...765L..14Q: Vertical boundaries fixed: sigma_s = 0.32, sigma_m = 3.2
- 2017A&A...606A.121L: Td = 50-200 K
- 2020A&A...638L..13M: feed rotation beta = 45 deg in Band 6
- 2019A&A...626A..81V: uv range restricted to >2 Mlambda (Band 4) or >3 Mlambda (Bands 6,7) for spws with short-baseline excess
- 2024ApJ...960....1L: Search ranges: 10-25 mJy for S_tot, 1e-6 to 2 mas for theta_core, -1 to 1 mas for x and y
- 2024ApJ...960....1L: 200 walkers, 1e4 iterations, first half of samples discarded
- 2020MNRAS.493.3412F: Nominal MRS ~25'' (Band 3) and ~19'' (Band 4)
- 2024ApJ...962..166W: 90 walkers; 4000 steps; reported 50(+34/-34)th posterior percentiles
- 2024ApJ...962..166W: Uniform priors: R [45,110] au; ΔR [8,100] au; F_belt [0.1,5.0] mJy
- 2024ApJ...962..166W: Uniform priors: inclination [70,90] degrees; PA [0,180] degrees; h [0.005,0.2]
- 2024ApJ...962..166W: σ_visibility=1/√w; free weight scaling
- 2025PASJ...77..834O: Continuum subtraction: first-degree polynomial in the uv-plane (CASA uvcontsub)
- 2025PASJ...77..834O: Integration range +-300 km/s about 1116 km/s
- 2025PASJ...77..834O: Final resolution and grid 150 pc, hexagonal
- 2022MNRAS.517.2546L: Free parameters: M_dust, r_1, i, PA, F_*_B6, x_off, y_off, plus (p_SPL, r_2) for SPL or (sigma_SGR) for SGR; N_Dat = 12,104,328
- 2015ApJ...806..260F: Cloverleaf natural weighting; SMMJ02399 UV-taper ~0.5" beam
- 2021ApJ...907L..27A: Phase-only self-calibration with 30 s solution interval
- 2021ApJ...907L..27A: First-order continuum subtracted from one copy
- 2026A&A...706A.292S: Envelope flux, p+q, R_in, R_out, disk flux and disk radius per model; reduced chi2 used to pick best model
- 2022A&A...661A.125W: Restored beam 2" x 2" for SED flux measurements and 1.4/3/9 GHz alpha-map; 1" beam for 3/9 GHz alpha-map; spectral index threshold alpha = 1.1
- 2017ApJ...839...99P: short baselines <~200 kλ or full uv
- 2017ApJ...839...99P: radial grid 1-500 au in 0.1 au steps; 4000 steps, 1000 walkers, burn-in ~1000 steps
- 2019ApJ...882..168P: 18 free parameters HZ10, 12 for HZ9
- 2025ApJ...984L..16G: Gaussian ring profile I(r)=Ix exp[−(r−rx)^2/(2wx^2)]
- 2025ApJ...984L..16G: Deconvolve Gaussian amplitudes using measured σ/deconvolved σ
- 2025ApJ...984L..16G: Continuum-compatible radii 29, 51, 80 au; masses 3–5, 0.4, 0.25 MJ
- 2025ApJ...984L..16G: Reference continuum model Mp1=3.8 MJ
- 2021NatAs...5..319P: R_eff = FWHM / 2; resolved threshold P_unres <= 10%
- 2021NatAs...5..319P: Subtraction performed within R_eff,ALMA = 1.54 kpc over full frequency range of the spectral window
- 2021A&A...649A.122P: Deprojection uses inclination and PA from the visibility fits; profiles normalized to the ring peak and restored with a common 0.05'' x 0.034'' beam
- 2021A&A...649A.122P: galario pixel size 0.2 mas
- 2021A&A...649A.122P: More than 250000 steps after convergence; 16th and 84th percentiles as error bars
- 2026A&A...706A.174A: B6: only spectral windows 0 and 1 used because of emission lines in the others
- 2026A&A...706A.174A: Lens centre free with Gaussian prior between the two images and standard deviation 1″
- 2016ApJ...828..113M: Free: Rin, Rout, Fbelt, Fcen, gamma; Rout <= 55 AU; gamma in -4 to 4; uniform priors
- 2016ApJ...828..113M: Gaussian prior 0.6 mJy <= Fbelt <= 1.6 mJy
- 2015ApJ...798...85P: h=0.1 r, gamma=1, R_c=200 au, T=50 K (r/50au)^-0.3, b=50 m/s, inner truncation 0.3 au
- 2018A&A...617A..10C: 0.42 km/s channels for centroids
- 2019A&A...630A..59B: Niter 500-1000, threshold 3 sigma
- 2023ApJ...948..134P: Plot threshold: geometric mean positional uncertainty sqrt(sigma_x * sigma_y) < 20 mas; reference maser spot at v = 561.6 km s^-1
- 2017A&A...605A.116K: Briggs robust = 0.5; 1 km/s velocity binning
- 2026A&A...712A.244H: 1000 Monte Carlo realizations; noise std devs: X-Y Phase = 2 deg, X-Y Bandpass amp = 0.1% (B4, B6) / 0.2% (B7), X-Y Bandpass phase = 0.5 deg, D-terms = 0.5% (B…
- 2021A&A...653A.117B: theta_obs = sqrt(theta_beam^2 + theta_source^2); 10% calibration error in flux
- 2025A&A...703A..15M: multiscale scales = [0, 5, 15, 25] pixels; Briggs robust = 0.5 (natural for HD 144277, HD 176497; 1 arcsec taper for non-detections)
- 2025A&A...703A..15M: W_disk = 0.7 R_disk fixed for HD 176497, HD 112532, HD 141960, HD 145101
- 2026MNRAS.548ag546D: High-res cube: robust = 0.8, channel width = 10 km s^-1, clean threshold = 1.5 x RMS, 1000x1000 pix at 0.03 arcsec/pix, velocity range 1100-1400 km s^-1, momen…
- 2026MNRAS.548ag546D: Low-res cube: robust = 2.0, uvtaper = 600 kilolambda (~780 m), channel width = 10 km s^-1, 300x300 pix at 0.1 arcsec/pix, moment mask clip = 5 x RMS after 1x b…
- 2021MNRAS.502.5390P: F_nu_star, F_nu_belt, R (r_c), Delta R (FWHM of Gaussian), h=H/R (fixed to 0.03 when unconstrained), i, PA, Delta RA, Delta Dec, weight rescaling factor
- 2022MNRAS.514.5035L: channel width = 2 km s^-1 (and 15 km s^-1 for kinematics)
- 2022MNRAS.514.5035L: Briggs robust = 2.0, uv-taper = 0.7'', final circular beam FWHM = 1.1''
- 2016A&A...593A.111T: Upper limits = 3 x rms above measured flux (null if negative)
- 2016A&A...593A.111T: Inner radius 0.1 AU; Sigma0 at R0=10 AU; grain a 10 nm-1 um (q=3.5) surface, 10 nm-1.4 cm (q=3) midplane
- 2018ApJ...861....7F: sky fixed at 0; center fixed at image center
- 2025A&A...700L...5G: Older 2013.1.00387.S and 2013.2.00163.S fluxes too bright by about 5 and 7%, respectively; rescaled before merging.
- 2025A&A...700L...5G: Filter spectral lines with UV_FILTER; rotate final images 3.1° clockwise.
- 2025A&A...700L...5G: Fit orientation, inclination, systemic velocity, stellar mass and local line width.
- 2022A&A...668L...4G: Free astrometric offset (< 0.15 arcsec for detections)
- 2022A&A...668L...4G: 1000 random off-center extractions for r.m.s. error estimation; 3 sigma upper limits for non-detections
- 2021A&A...649A..19S: 200 independent walkers for thousands of steps; baselines > 1000 klambda excluded
- 2025A&A...694A.218B: continuum from all line-free channels with point-source models in uv space
- 2025A&A...694A.218B: average 1 sigma line sensitivity 0.05 Jy km/s/beam over 500 km/s in Band 3
- 2016ApJ...828...25L: beta = 0.8; rho = 2.7 g cm^-3; grain sizes 0.1-3000 um
- 2015Natur.520..198O: x_100AU 1e-14 to 1e-10; alpha ranges 0-1 (H13CN), 1-2 (HC3N), 0-2 (CH3CN); Rout 100 AU
- 2021A&A...654A..90L: uv-distance bin width = 50 klambda; uvmodelfit iterations = 20; S/N >= 8 threshold for reliable sizes
- 2024A&A...692A.205B: Circular Gaussian model
- 2025MNRAS.541...71M: 90 walkers, 1,000 steps (90,000 realisations); posterior from last 10,000 realisations
- 2025MNRAS.541...71M: Priors for radius, inclination, position angle normal with sd 3% of initial value, from Herschel
- 2024ApJ...970...75Z: deconvolver = hogbom, threshold = 3 rms, Briggs robust b = 0.5 (continuum), natural weighting (CO(2-1) cube), channel width = 5 km s^-1
- 2020AJ....159..288M: Briggs robust 0.5
- 2020ApJ...898...75I: robust 0.0 (Bands 6-8); robust 0.5 with outertaper 0.2'' (Band 3); dV = 10 km/s (20 for 13CO)
- 2018ApJ...869...17L: 100 walkers, 5000 steps, burn-in ~2000; second run 5000 more steps; posterior from last 1000 steps; radial grid 0.0001''-4'' step 0.001''
- 2018ApJ...869...17L: Uniform priors: ±20 deg for i and PA, ±0.5 arcsec for offsets
- 2019ApJ...873...50D: time averaging up to 10 min with uv separation <15 m; velocity bins 75-250 km/s
- 2019ApJ...873...50D: 1000 chains, 1000 burn-in, 1000 extra steps
- 2025A&A...699A.373F: Preliminary run 100 walkers ~10^3 steps; fiducial run 250 walkers and 10^4 steps; first 25% discarded as burn-in
- 2025A&A...699A.373F: robust 1.0 (B7 2019, 2021) and 0.0 (others); CLEAN down to 1 sigma with gain 0.02
- 2025A&A...699A.373F: Position uncertainty = 1 mas alignment term plus theta_FWHM/SNR/0.9 in quadrature
- 2020MNRAS.495.3409S: five free parameters: R.A., Dec., flux density, half-light radius, axial ratio
- 2020MNRAS.495.3409S: optimisation repeated ten times from random starting values; lowest chi-square kept
- 2020MNRAS.495.3409S: boosting correction from running median of recovered/input flux vs detection significance
- 2020A&A...635A..94D: Deprojection with PA=356°, i=53°
- 2020A&A...635A..94D: Velocity exponent fixed to 0.5
- 2024A&A...681A.110W: Briggs n=2; clean to 3σ
- 2024A&A...681A.110W: Reff,circ = Reff × sqrt(b/a); Reff ≈ FWHMGaussian/2.43
- 2016ApJ...829....6W: natural weighting; threshold 1/2 sigma_RMS
- 2014ApJ...783L..13P: SR 21 ring+vortex inclination fixed to 15 deg
- 2017ApJ...850...54C: MOM0 cut ±1σ, MOM1 cut ±5σ
- 2020MNRAS.496..138B: Image positions and position angles fixed; 8 free parameters for CO (4 fluxes, 2 widths, 2 axis ratios); 6 free parameters for radio (4 fluxes, 1 width, 1 axis…
- 2025A&A...699A.265G: All 240 channels averaged to eight-channel, four-SPW visibility files before fitting
- 2023ApJ...946L..41S: robust = 0.5; common circular beam = 0.43''; extraction aperture diameter = 0.43''
- 2025Natur.642..905L: ALMA astrometric systematic error of 5% of the beam size (9 mas for combined observation) added in quadrature to statistical MCMC uncertainties.
- 2025A&A...700A.165B: Low-res: +-30 km/s (three channels each side); high-res: 10 km/s width
- 2023MNRAS.526.5401C: Stars separated by less than the beam are listed as one with the mean of two uvmodelfit fluxes
- 2019NatAs...3..230K: 64 walkers, 1000 steps after 1000-step burn-in
- 2019NatAs...3..230K: scale height fixed to 0.05 r
- 2016ApJ...823...37H: Singular elliptical power law plus m=3,4 multipoles plus external shear; 12 free parameters
- 2026MNRAS.552g1700S: Geometry fixed to Band 6 values: inc = 37.0 deg, PA = 45.1 deg; Frankenstein hyperparameters: alpha = 1.05, w_smooth = 0.1
- 2026MNRAS.552g1700S: Pixel size = 10 mas, image size = 1024 pixels; fixed inc = 37.0 deg, PA = 45.1 deg; 13 free parameters; 104 walkers (8 x 13), 8000 steps
- 2020MNRAS.498.4635D: Average within each spectral window and 30-second intervals; phase centre at SMG position
- 2020MNRAS.498.4635D: Fixed b/a=0.753; refit at b/a=0.549 and 0.987 for orientation uncertainties
- 2020MNRAS.498.4635D: Reliable-size limit: MartiVidal2012 Eqn.7, β=0.75, λc=3.84; 2σ size upper limits for SDP.5347 and SDP.6418
- 2021A&A...646A..72H: Phase center J2000 04h39m35.203s +25d41m44.21s from fitting an elliptical Gaussian to continuum visibilities
- 2021A&A...646A..72H: Free parameters: peak intensity, size, inclination, position angle, position offset
- 2021A&A...646A..72H: First run 60 walkers and 1000 steps; second run 120 walkers, 10000 steps; best fit = mean of last 1000 steps of walkers with acceptance ratio >20%
- 2025A&A...693A.309S: Upper limit on continuum size from Eq. (2) of Gomez-Guijarro et al. 2022
- 2019AJ....158..162F: 23 free parameters (7 ring incl. centre offset, plus Gaussian sources)
- 2015ApJ...814...53G: 50<Rout/AU<500, -2<alpha<2, 1e-14<X100<1e-9, R0=100 AU
- 2019ApJ...885..106L: gradient selection >1/100x(peak-rms) for moment 0 maps, >1/1000x(peak-rms) for continuum; Nyquist sampling 4 points per beam
- 2016ApJ...833L...6C: 1.5 sigma cutoff CO(1-0); 2.5 sigma cutoff CO(3-2)
- 2023ApJ...954..197I: 60 s time averaging, 4 SPWs, polar grid delta r = 100 m, delta theta = 1 deg to 90 deg (optimal 10 deg; <= 1.5 deg for Object Y), zero-padded 18.0'' box (from …
- 2024PASJ...76..340K: detection threshold 3x line image rms; J axis PA=68.35 deg
- 2021ApJ...910..148M: Cube velocity widths 0.1 (C18O, N2D+), 0.5 (DCN), 1.0 (CO, SiO) km/s
- 2025A&A...693A.151M: h fixed to 0.03 unless vertically constrained; temperature r^-0.5
- 2025A&A...693A.174E: robust = 2, 15 km/s channels, zeroth-order uvcontsub in line-free channels
- 2018ApJ...865..157A: x = 0.68 encircled luminosity fraction
- 2018ApJ...865..157A: L_mm = F_nu (d/140)^2 s
- 2019ApJ...876..112R: uv-bin size varied 5 to 50 klambda
- 2024ApJ...976..258K: Surface density as the sum of two Gaussians truncated to 150-550 au; temperature a power law defined by T250 and exponent q
- 2024ApJ...976..258K: H2D+: same adopted geometry, constant T = 15 K, uniform surface density 150-450 au
- 2021ApJ...908..192S: Initial positions, flux densities and shapes from SExtractor; 26 morphological components
- 2021ApJ...908..192S: HLS0612 single source; HLS1314 three sources
- 2020MNRAS.492..572A: 120 walkers and 5000 steps; accepted fraction 0.2-0.5
- 2020MNRAS.492..572A: Six free parameters: flux normalisation, FWHM along semi-major axis, inclination, position angle, RA and Dec offsets
- 2020MNRAS.492..572A: Two Gaussians fit simultaneously for resolved binary discs; extra inner cutoff radius for four cavity discs
- 2024A&A...686A.187P: lambda_c = 9 (3 sigma cut-off for upper limits)
- 2019ApJ...881...84S: 1024 walkers, 1.25e4 steps, burn-in 2.5e3
- 2014ApJ...791...42Z: 150 LM runs, then 10 MCMC chains, 5x10^4 models total
- 2018ApJ...863..129S: velocity resolution 20, 30 or 50 km/s
- 2023A&A...674A.101M: Two point-like components; free parameters: f_NE and R = f_NE/f_SW
- 2026A&A...710A..63L: Two circular Gaussian components (W and E) separated by ~5 mas
- 2020ApJ...888...41A: robust = 1 for compact-source images; robust 0.5, uv>300 kλ for disk image
- 2025A&A...698A.183D: scale height H/r < 0.05; stellar flux not included
- 2018A&A...611A..16B: Only 7_7-6_6 and 7_8-6_7 stacked; 8_8-7_7 excluded since it increased noise
- 2018A&A...611A..16B: CO filter compression factors 1/2, 1/3, 1/4 tested
- 2018ApJ...856..121G: n = 0.5, 1, 4 and free tested; errors add systematics from n and b/a in quadrature
- 2024A&A...689A.104D: alpha={1.05,1.2,1.3}, wsmooth={1e-1,1e-4}, Rmax=5.0", p0=1e-35, 300 radial points
- 2024A&A...689A.104D: 80 walkers, 10,000 steps after 2000 burn-in
- 2023A&A...679A.119R: line-free channels: 86.0-88.5 GHz and 90.0-101.0 GHz
- 2023A&A...679A.119R: cleaning threshold: 1.5 sigma
- 2023A&A...679A.119R: fastnoise=False
- 2021AJ....162...99F: 60 walkers, 2000 steps after burn-in
- 2021AJ....162...99F: baselines <650 klambda used in the fit
- 2021AJ....162...99F: phase-centre shift with fixvis, alignment with fixplanet
- 2025ApJ...987...61R: dowtsp=True; fixed continuum parameters (RA offset 0, Dec offset 0, FWHM 0.22 arcsec, flux density 52.7 mJy); 10 varied disk parameters with priors in Table 2
- 2018MNRAS.475.4924K: 40 walkers, 1000 steps, ~100 burn-in; data averaged to 10 s and four channels per SPW; weights recomputed with statwt; reweighting 1/2.5
- 2023ApJ...945...40C: Time averaging window = 300 s; reference frequency = 287 GHz; spectral curvature beta = 0; fiducial spectral index alpha_0 = 0
- 2024A&A...689A.299M: 10 s averaging; spectral window 227.1 GHz
- 2018MNRAS.474.4347C: Priors uniform: Mdisc 0.001-1 Msun, gamma 0-2, Rc 10-100 au, hc 1-10 au, psi 0-2, Rstar 1-8 Rsun, i 10-80 deg
- 2018MNRAS.474.4347C: ~100 walkers, 1000 iterations
- 2017A&A...597A..41G: 10,000-240,000 iterations, 5,000 burn-in
- 2024ApJ...974..306S: Grid of alpha = 1.05-1.30 and log10(w_smooth) = -4 to -1; chosen pairs per dataset in the visibility table
- 2024ApJ...974..306S: Fit in logarithmic brightness space; low-SNR VLA data fitted on visibilities binned at 10 klambda
- 2024ApJ...974..306S: 64 walkers and 10000 steps; ring radii fixed from ALMA profiles (RXJ1615 outer ring radius free)
- 2023MNRAS.519...34H: integration time > 40 min (up to 4 hours)
- 2023MNRAS.519...34H: spatial resolution = 0.5 arcsec, minimal pixel size = 0.17 arcsec, spectral window width >= 0.5 GHz, channel separation = 15.6 MHz
- 2023MNRAS.519...34H: cube r.m.s. <= 5 mJy beam^-1
- 2021A&A...656A.150P: Wavelength 0.9 mm
- 2021A&A...656A.150P: Convolution with a 0.3'' Gaussian beam
- 2021A&A...656A.150P: Dust settling factor chi = 3% for grains larger than 1 micron
- 2024ApJ...961....2K: Image-plane positions only for most models; each family of n images gives 2(n-1) constraints; catalogs in Table 13
- 2018ApJ...869...75M: 100 walkers, 10,000 steps
- 2015ApJ...808..102K: 25 models per target: b_t = {0.6,0.8,1.0,1.2,1.4}, h = {0.95,1.10,1.25,1.40,1.55}
- 2015ApJ...808..102K: pixel 9 AU, 1024x1024 image
- 2021ApJ...908..235I: velocity resolution 100 km/s, channel rms 0.13 mJy/beam
- 2021ApJ...908..235I: continuum map 1 sigma = 17.6 uJy/beam
- 2025A&A...695A.233R: acceptable reduced chi-square < 2
- 2018ApJ...859L..28K: 6 free parameters: gamma, R_gap_in, R_gap_out, delta, R_c, F_total; 100 walkers, 1000 iterations, 500 burn-in
- 2018Sci...361.1016S: time averaging up to 3 min with uv separation <10 m
- 2025A&A...701A.203S: Initial MCMC: 32 walkers, 10^4 steps; second iteration: 64 walkers, 10^5 steps, 30% burn-in; omega < 180 deg
- 2025A&A...701A.203S: Outer disc 40 to 60 au (8600 to 12900 R_sun), dust grain size a = 1 um, 90% water ice + 10% forsterite, intermediate disc 43 to 215 R_sun (0.2 to 1 au)
- 2023MNRAS.521.2962F: 2D Gaussian model with free source positions, major/minor axis FWHMs, position angles, and source fluxes
- 2023MNRAS.521.2962F: Clean threshold of 3 times dirty image RMS for image-plane check
- 2020A&A...633A.114S: 200 walkers, 20000 steps
- 2024MNRAS.535.1533B: Sersic index n free between 0.5 and 5 for lensed sources; n = 0.5 fixed in IMFIT for unlensed sources
- 2019ApJ...875...87D: 50 walkers, 10^5 samples; 0.15 au per pixel
- 2015ApJ...810L...7V: Grid steps 1 degree and 1 AU
- 2020MNRAS.499.3909Y: H30a channel width 45 km s^-1 from -3770 to +700 km s^-1; H39a channel width 15.625 MHz; VLA H52a and H56a channel width 2 MHz
- 2017A&A...606A..88T: R0 = 10 au fixed; gamma in [-2,2], Sigma0 0.05-400 g/cm2, Rc 2-400 au, i 0-90, PA 0-180, offsets +/-2"
- 2017A&A...606A..88T: 100 walkers, burn-in 1000-1500 steps, then 4000-5000 steps
- 2019ApJ...870...80L: lambda fitted for fixed lens model, alternating with MCMC until convergence
- 2024ApJ...966...59S: 50 walkers, 10000 steps; model pixel 3 mas
- 2024ApJ...966...59S: Nuker priors: log10 alpha U(0,2), beta U(0,10), gamma approx uniform (-3,2); point flux U(0,1) mJy
- 2021MNRAS.508.5259M: N_iter = 2000 bootstrap iterations; T_CMB = 2.7255 K; I_0 = 270.06 MJy/sr; mu_e = 1.17; cloud size <= 5'' (~30 kpc) or 1'' (5.8 kpc) for ap5
- 2020ApJ...889...59P: Free: Mdisk, gamma, Rc, H100, Psi plus centroid shift; 240 walkers, 2000 iterations
- 2020ApJ...889...59P: Grid 256x64, 1200 K sublimation inner edge, outer radius 100 au
- 2026A&A...707A.252K: Lens redshifts fixed at z = 0.626 (or 0.636 in text) and z = 1.002; 1000 posterior samples for magnification error
- 2016MNRAS.460.2933M: Free parameters: r0, h, Δr, Mdust, PA, i, RA and Dec offsets; h lower limit 0.03
- 2016A&A...586A..45S: primary beam factor x3.73
- 2020A&A...636A..62K: 10% flux accuracy; position error ~1/10 beam; polarization threshold 9 sigma
- 2018ApJ...869L..49I: 200 walkers, 10^4 burn-in steps, convergence after ~4x10^4 steps
- 2018A&A...613A..34P: eight free parameters
- 2025ApJ...988..106H: Flat priors: cos i [0,1]; P.A. [0,180] deg; dx, dy [-0.1,0.1] arcsec; gamma [0.01,0.15] arcsec; log alpha [-4,5]
- 2025ApJ...988..106H: 24 walkers, 15000 steps, first 1000 steps discarded as burn-in
- 2025ApJ...988..106H: residual image uv taper 0.02 arcsec; synthesized beam 0.046 x 0.030 arcsec (15.9 deg)
- 2020MNRAS.499.5241C: disc model in uvmodelfit; circularised radius sqrt(R_maj R_min)
- 2020MNRAS.499.5241C: annuli in steps of 0.25'' centred on peak pixel of tapered images, measured in natural-weighted images
- 2021A&A...646A..59R: Briggs R = 0.5
- 2021A&A...646A..59R: 0.06 km s^-1; 256 × 256 pixels; 0.1'' pixels
- 2016A&A...591A.108O: 200 walkers, 500 burn-in, 2000 iterations; alpha_in = 5 fixed
- 2014Natur.511..567J: 30 walkers, at least 500 steps, first 150 discarded as burn-in; flat priors except sin i prior for inclination
- 2018ApJ...867..140L: moment-0 maps collapsed over 300 km/s centered at +/-155 km/s
- 2025A&A...694A.147G: uv range limits: 2000 klambda (BP Tau, DL Tau, DR Tau, Sz 98, V1094 Sco), 3000 klambda (CI Tau, GW Lup), 1500 klambda (IQ Tau)
- 2025A&A...694A.147G: Binned visibility widths of 10-20 klambda
- 2025A&A...694A.147G: Only continuum spectral windows for DR Tau, GW Lup, Sz 98 (lower uncertainties) and DL Tau; all spectral windows (lines masked) for the others
- 2025A&A...694A.147G: Minimum number of additional Gaussians giving a good fit to visible features
- 2025A&A...694A.147G: MCMC iterations: 2500 (round 1), 10,000 (round 2), final 5000 used for posterior medians
- 2022MNRAS.515.1751W: tclean threshold set to 3x theoretical sensitivity
- 2022MNRAS.515.1751W: 0.6'' uv taper for total [O III] and [C II] line fluxes; |v| > 1000 km/s for mfs continuum
- 2022MNRAS.513.5790C: 2048 x 2048 grid with pixel sizes of 3 mas (SB16/LB19) and 4 mas (IB17/LB19); uv-range 0.17 to 0.47 Mlambda (SB16/LB19) and 0.17 to 0.71 Mlambda (IB17/LB19)
- 2024A&A...690A.197M: Sérsic index n = 1 (exponential profile), circular disk fixed axis ratio (q = 0 as written in text); two-component fitting when residual map shows second compo…
- 2019ApJ...877L..32M: ~10^6 iterations (100 walkers, 10,000 steps each)
- 2017ApJ...846L..14S: Averaged 24 (J2202) or 6 (J0912) channels, ~200 and 50 km/s
- 2018ApJ...859...32P: radial grid 0-500 au in 0.5 au steps; last 700 steps used
- 2024A&A...683A.141R: Fluxes within 5 sigma contours at the four frequencies
- 2024A&A...683A.141R: Dust mixture 70% water ice and 30% astro-silicates; size distribution slope changed from -3.5 to -3.0; distance 162.9 pc; max dust size 1 cm
- 2023A&A...673A.116K: Lens parameters: (x_L, y_L), ellipticity e_L, position angle phi_L; Source parameters: Sersic profile with (x_S, y_S), flux density, Sersic index, half-light r…
- 2021MNRAS.507.2531Z: 8 parameters per disc component (log F_tot, gamma_1, gamma_2, R_C, i, PA, Delta_alpha, Delta_delta); 100 to 300 walkers; 5x10^3 to 2x10^4 steps; last 1000 step…
- 2018ApJ...853..147M: moment 0 integrated within ±7 km/s of stellar velocity
- 2015ApJ...813...99F: Fixed: d=122 pc, M*=2.3 Msun, PA=312 deg, Mgas=0.09 Msun, CO/H2=1e-4 (unless varied)
- 2018Natur.553...51M: Four Sersic components (1 E, 3 W) for visilens
- 2025ApJ...994..214T: 200 walkers; minimum burn-in 1000 steps; convergence evaluated from 2500 steps
- 2025ApJ...994..214T: Position offsets restricted to initial imfit guess +-0.25 arcsec; V_LSR +-1.2 km/s (+-2.4 km/s for low S/N)
- 2025ApJ...994..214T: Temperature exponent q range expanded from [0,1] to [0,2] for sources piling up at q = 1
- 2022MNRAS.512.2426M: Constant-weight gradient regularisation; 6 to 14 lens mass model parameters plus regularisation and number of source pixels
- 2022ApJ...930L...3W: Number count integration threshold of 0.1 mJy to infinity within >=20% primary-beam response and within 0.1'' from SR 12 c
- 2025A&A...695A..23S: upper limits at 3 sigma assuming a size equal to the beam size
- 2017ApJ...849..123M: robust = 0.5
- 2018ApJ...859..111H: 500 walkers, 1000 iterations; uniform priors on Md, gamma, Rc, H100
- 2017ApJ...834..135T: FWHM = 0.826 R1/2
- 2026A&A...709A.174F: CLEAN threshold = 5 uJy/beam (~1 sigma), elliptic mask R = 0.625'', i = 41.5
- 2026A&A...709A.174F: 15 parameters for HD 34700A, 13 for IRS 48, 23 for HD 142527 (plus eccentricity e and argument of periastron omega for eccentric models)
- 2026A&A...709A.174F: Preliminary run: 100 walkers, ~10^3 steps; Fiducial run: 120 walkers, 2x10^4 steps, 25% burn-in
- 2021MNRAS.503.5583B: Aperture diameter 1-2''; SEARCH thresholds S/N_upper = 3.5 and S/N_lower = 3.0
- 2020ApJ...902L..33G: i = 10 deg, PA = 122 deg for the secondary disk
- 2020ApJ...902L..33G: Null at 5000 +/- 500 klambda gives R_cav = 2.2 +/- 0.25 au
- 2024A&A...689A.283L: CO(2-1) moment-0: -575 to +475 km/s (channels 55 to 69)
- 2024A&A...689A.283L: CO(5-4) moment-0: -605 to +445 km/s (channels 38 to 52)
- 2017MNRAS.466.4201W: 10 chains, 100000 links, acceptance ~26%
- 2019A&A...625A.118K: robust = 0.5
- 2017ApJ...846L..22G: One Gaussian for each CO line; two Gaussians for 450 µm continuum
- 2024A&A...689A..85G: Gaussian ring I(r)=f exp(-0.5((r-r_k)/sigma_k)^2); gamma_SB2=1
- 2022MNRAS.510.3734D: 0.8 x 0.8 arcsec source plane with 400 Voronoi pixels, 7 randomisations per likelihood evaluation, 50 randomisations averaged onto 100 x 100 square pixels for …
- 2020ApJ...905...89Y: Model parameters in Table 3: Mstar, i, PA, Vsys, N0, p, T0, q, Rin, Rout, H0, h, deltaV (which are free versus fixed not stated)
- 2026A&A...705A..81K: lens centers fixed at Einstein ring centers with uniform priors; Einstein radius upper limit slightly above Spilker16
- 2018A&A...619A.161C: 9 model parameters + center (x_c,y_c) + inclination; PA fixed at 62 deg
- 2018A&A...619A.161C: 120 walkers, 24000 likelihoods
- 2024ApJ...961...28H: GR2ARC: 18 free parameters; arcs fixed at a single R_arc in the restricted fit
- 2024ApJ...961...28H: Fit intensity, radial and angular locations and widths, PA, inclination, and phase-center offsets
- 2022A&A...665A...3J: Gaussian kernel determined from continuum (for ID9316 ALMA); point source model at ALMA positions (for NOEMA)
- 2020AJ....160..248A: non-detections: position offsets fixed to zero
- 2020AJ....160..248A: resolved if a/σ_a > 5
- 2024ApJ...963...19N: Channel widths (km/s): SPT0202-61 50, SPT0418-47 70, SPT0441-46 75, SPT2132-58 150, SPT2319-55 75; same widths for [CII]
- 2024ApJ...963...19N: CLEAN threshold 1.5x thermal noise measured in the channel map at the central velocity of the higher-frequency OH doublet component
- 2017NatAs...1E.130Z: v_turb fixed at 0.01 km/s; outer-disk T = 21 K; fixed stellar mass 0.6 Msun, i=7 deg, PA=155 deg
- 2019ApJ...887...40W: uv bins 50 klambda (J0129), 75 klambda (J1044)
- 2025A&A...693A..49S: Setup 1 phase rms threshold 55 deg, seeing threshold not applied
- 2025A&A...693A..49S: Setup 2 phase rms threshold default 70 deg
- 2025A&A...693A..49S: Flagged fractions: 10% (2022 Nov 30), 2% (2022 Dec 17), 43% (bad weather setup 2), 0% (2023 Oct 7)
- 2023A&A...675A..85M: Peak-to-integrated flux ratios of 0.80 (A370) and 0.71 (AS1063) for 4.5 <= S/N < 5 sources
- 2020ApJ...898...36L: 100 walkers, 5000 steps, last 1000 used; grid 0.0001-4" step 0.0005"
- 2025A&A...693A..17D: Free parameters: centre, flux, FWHM major, FWHM minor, position angle; Reff,FIR = half-emission radius from the circularised FWHM
- 2019ApJ...882..160Q: R1 and R2 grid interval of 5 au; vertical boundaries Σ21 = 3.2 and 100; i and PA fixed from continuum
- 2018A&A...619A..39F: line visibilities averaged over -500 to 500 km/s
- 2024A&A...684A.200G: First-order azimuthal modulation, m = 1.
- 2020MNRAS.499.5136C: Reported extent is major-axis FWHM
- 2020MNRAS.499.5136C: Use the five systems with both FIR lines detected at SNR>8 to investigate relative extent
- 2020ApJ...900....7H: 100 walkers, ~2500 steps; distance 131.2±1.7 pc
- 2025MNRAS.536.3757A: Gaussian prior on centre (sigma 1 arcsec); uniform Vmax 0-600 km/s, sigma 0-200 km/s, r_e 0-2", r_t 0-1"
- 2016ApJ...818..156C: p fixed to 1; 12-dimensional posterior
- 2026A&A...710L..10C: N = 120 random positions along projected circular orbit of PDS 70c (excluding within one natural-weight beam of PDS 70c)
- 2026A&A...710L..10C: 20 min sub-EB intervals (6 equal intervals per EB for 7 EBs in IB23, 41 degrees of freedom)
- 2020ApJ...901...74T: Only S/N>10 sources (62) used for size discussion
- 2020ApJ...895..109F: Free: T_atm0, q, R_c, i, δv_turb, R_in, v_sys; fixed PA, γ=1, T_mid0, Z_q0, masses
- 2025ApJ...993L..40S: Natural weighting; 0.5″ uv-plane taper
- 2016ApJ...823L..18H: Sigma_c=5e-5 g/cm2, gamma=1, r_c=100 AU, B=3, r_ring=150 AU, sigma_ring=20 AU
- 2016ApJ...823L..18H: turbulent broadening xi = 0.01 km/s
- 2019MNRAS.489.3939C: 40 walkers; priors p(log Ie)=U(-5,1), p(log Re)=U(-2,0), p(i)=U(0,90) deg, p(PA)=U(180,360) deg
- 2020ApJ...898...33C: secondary lens offset fixed to (-0.025", -0.327")
- 2020ApJ...895..126H: 70 walkers, 100,000 steps, burn-in 100 walkers x 1000 steps; uniform priors
- 2017A&A...603L...6H: cutoff uv radius 60 m for the reported results
- 2018NatAs...2...56Z: lens z=0.776, source z=6.027 fixed
- 2024A&A...682A..55M: Maximum radius R_max = 2'', number of collocation points N = 300, hyperparameter α = 1.2 (also tested α = 1.05, 1.30), wsmooth varied, phase centre shift grid …
- 2024A&A...690L..16J: point-source model at fixed position of the ALMA continuum peak
- 2016ApJ...831..200W: moment 1 clipped at 5σ; moment 0 masks <3σ
- 2016ApJ...828L..21K: bins of 150 kλ
- 2025MNRAS.538.2358S: Frankenstein hyper-parameters: alpha = 1.3, w_smooth = 10^-1; common resolution = 35 mas (5.5 au)
- 2021MNRAS.501.5973F: channel width = 6 channels (72.6 km s^-1)
- 2021MNRAS.501.5973F: uv taper beam = 5.3'' x 4.6''
- 2022A&A...662A.121R: HK Tau B excluded due to edge-on optical depth effects
- 2017ApJ...839...43O: (z/r)up=0.3, rout=100 AU fixed; vary inner radius, lower boundary, power law
- 2019ApJ...876....1T: MCMC 20,000 iterations
- 2024A&A...688A.149D: model images with 4 mas pixels and 2048 pixel image size
- 2024A&A...688A.149D: n_walk = 136 (eight times the number of parameters), 5000 burn-in steps and 6000 sampling steps per walker
- 2020ApJ...902..112B: IRX forced to zero below 10^9 Msun; z~3 average dust correction ~5 for UV-bright galaxies
- 2020A&A...639A.121F: 16 free parameters (LkCa 15), 13 (J1610)
- 2026A&A...705A.209L: continuum polynomial order 0; natural weighting; 30 km/s channels
- 2019MNRAS.482..698C: Free parameters: flux, major/minor FWHM, PA, offsets <1''
- 2019ApJ...877L..23P: Resolved if P_unres <= 10%
- 2024ApJ...976..132H: Adam optimizer, learning rate 0.02, 15,000 iterations; 2000 posterior samples
- 2021ApJ...910...89B: IMFIT results used in the analysis because GALFIT errors are underestimated
- 2020ApJ...895L..18B: 144 chains, 15000 iterations including 10000 burn-in
- 2025ApJ...990L..31B: channels |v|>1000 km/s for fit; hogbom; natural weighting
- 2019ApJ...881..159M: 51 free parameters; 2000 bins; 200 walkers, 100,000 iterations; 5 frequencies
- 2024NatAs...8..587F: Free: J0, sigma_G, delta RA, delta Dec; inclination 46.7 deg and PA 138.0 deg fixed
- 2020MNRAS.494.4090C: Robust detections >4.5σ; further detections ≥3σ.
- 2020MNRAS.494.4090C: Quoted errors are RMS from 1D spectra.
- 2020ApJ...899...55A: uvmodelfit up to 20 iterations; 20 (Lambda_l, Lambda_t) sets; 10-fold CV; MFISTA up to 1000 iterations; keep images with MSE < MSE_best+sigma
- 2018ApJ...854..130W: Free: M_disk, r_c, gamma, T0, q, xi, v_sys, inclination, PA
- 2016A&A...596A..75S: 10% calibration error added in quadrature
- 2024ApJ...977...60Q: Depletion factor grid: coarse logarithmic grid from 0.5 to 3.0 in steps of 0.5 (df = 5 and df = 10^2.5 = 320 shown in Figure 6)
- 2020ApJ...899...37K: PA and inclination within ±10 deg, centres within ±0.2 arcsec of van der Wel values
- 2021AJ....161...38O: Sigma(20au)=35 g cm-2, gamma=-1.3, H(20au)=2 au, p=0.3, mean molecular weight 2.37, T_atm=125 K at 10 au
- 2016ApJ...832..110C: MRN size distribution, 0.005 um min, max 1 um and 1 mm; 80% silicates + 20% graphite
- 2025MNRAS.543.2723P: 7 free parameters (f0, sigma_r, R_peak, inc, PA, dRA, dDec); 8 walkers per parameter; 30,000 steps then final 10,000; uniform priors; 256x256 pixels of 0.02 ar…
- 2020A&A...643A..53F: theta_min = 0.88 theta_beam/sqrt(S/N), theta_beam=0.60''
- 2023MNRAS.523.4970N: Briggs robust = 0.5; Hogbom deconvolver; pixel scale = 6 mas; spectral widths: 1 km/s (12CO) and 0.3 km/s (13CO, C18O); velocity ranges: -6 to 18 km/s (total /…
- 2016A&A...588A.112G: R0=10 AU, 500 chains
- 2026A&A...708L...1Z: M_star = 1, 0.5, 0.05 M_sun; inclination = 8, 30, 55 deg; R_c = 5, 20, 50 au; integration time ~180 s per disk
- 2020ApJ...900....1F: FWHM_major = 0.826 r_e,major; r_e = r_e,major sqrt(q); source center fixed from imfit
- 2025A&A...702A..18D: Reference epoch: 23 May 2023; channels collapsed in each of the 4 spectral windows
- 2019NatAs...3..278K: 64 walkers, 1000 steps after 1000 step burn-in; scale height 0.05r; 2048 pixels of 4.6 mas
- 2024PASJ...76..437Y: Re-weighting factor f_i = stddev^-2 / mean weight, typically 0.1-0.3
- 2020ApJ...897...91G: channel weights w=1/sigma_i^2
- 2021A&A...653A..46V: 3 sigma detection threshold
- 2018ApJ...857...69B: R100 = 100 AU; Rout 100 AU (V4046 Sgr), 180 AU (MWC 480); abundance reduced 1e8 above z/r=0.5; reduced 1e3 below 25 K (V4046 Sgr) or z/r<0.05 (MWC 480)
- 2018MNRAS.479..703C: Detection at fixed position SNR>3.5; free-position SNR>5
- 2025ApJ...990L..70L: alpha = 1.4, omega_smooth = 0.01
- 2021A&A...651L...5V: first order polynomial for uvcontsub
- 2018ApJ...868L...5K: 11 free parameters, flat priors, 100 walkers, 500 burn-in + 500 steps
- 2019MNRAS.490.4956G: compact Reff fixed to 0.10''; extended Reff ~0.5''
- 2021A&A...653L...9V: uniform weighting; beam 0.22x0.20; rms 0.08 mJy/beam; average frequency 240 GHz, 6 GHz bandwidth
- 2017ApJ...836...30G: 0.2 km/s resolution, 60 channels; flat priors -3<alpha<2 and 1e-20<X<1e-8
- 2019ApJ...887..144J: 16 MHz per channel
- 2025ApJ...993...90S: 1000 iterations, 32 walkers, init from SpM cos i and PA
- 2020MNRAS.493L.108B: 0.2'' uv-taper; first moment with 2.5 sigma clip
- 2019A&A...626L...2F: 90 walkers, 18000 steps after 2000 burn-in; uniform priors
- 2019ApJ...873L..19B: position fixed; only flux density free
- 2017ApJ...836..223W: 200 walkers; star 4300 K, 1 Lsun
- 2018ApJ...867L..29W: velocity range chosen to maximize S/N; CO(3-2) used for low S/N
- 2026ApJ..1003L..30W: Mask geometry i = 5 deg, PA = 152 deg, M* = 0.88 Msun, d = 59.5 pc, dr = 0.1
- 2018A&A...610A..24F: 80 chains, 45000 steps after 5000 burn-in
- 2024A&A...687A.188K: Nominal image 512 px at 15 mas; inner 64 px replaced by nest of level n=2 (4^2 oversampling)
- 2016A&A...586A..99H: 4 or 6 free parameters; fixed Sigma_10au=0.39, kappa=3.4, q0=2.6, q1=0.26, R0=7 au
- 2019A&A...628A..95M: 150 walkers, ~20000 steps (1 disk); 200 walkers, >25000 steps (2 disks); 400 walkers, 31000 steps (UZ Tau)
- 2017ApJ...840...23L: inner disk PA fixed 93 deg, inclination fixed 75 deg
- 2017ApJ...845..138S: 62.5 MHz channels, robust = 0.5
- 2017ApJ...840L..12S: Free: L*, Mdisk, alpha, beta, h0, Rgap, delta, Rdisk, inclination, PA, amax, A_K
- 2019PASJ...71..111I: robust = 0.5, gain = 0.1
- 2017ApJ...843..150F: 80 walkers, 1000 steps, first 500 burn-in
- 2019ApJ...874..136S: 200 walkers; ~5000 post-burn-in steps; autocorrelation time ~1000 steps; walkers with chi2-chi2min>44 discarded
- 2018ApJ...869L..48G: uv-points 10 to 10000 kλ in 10 kλ steps; 27 free parameters (23 ring, 4 geometry)
- 2017ApJ...844..158S: R_in = 0.1 au; scale height fixed
- 2017ApJ...851...85B: Free: Sigma0, R_dust, h0, p, inclination, position angle; R_in fixed; minimum temperature 10 K
- 2018ApJ...852..122H: Fiducial: N_CO=3e19 cm-2, R1=15 AU, R2=70 AU, A=3, f=0.025, Tmid10=40 K, Tatm10=125 K, q=0.47, Tfrz=27 K, Rin=0.05, Rout=215 AU
- 2018ApJ...863...61L: Detection if flux >3 sigma near expected position
- 2016Natur.535..258C: alpha = ln(F232.6/F218.0)/ln(218.0/232.6)
- 2019ApJ...882...49L: 100 walkers, 5000 steps, burn-in <1000, posterior from last 1000 steps
- 2018A&A...620A.125M: low-S/N sources: r_eff=0.23'', q=0.58; peak/integrated ratios 0.85, 0.96, 0.96
- 2017ApJ...851L..23C: lambda = 0.1, G = 30, eta = 1.0
- 2016ApJ...831..125P: Upper limits = 3 times the flux uncertainty
- 2018ApJ...859..150R: 12 parameters; PA, inclination, flux, offset, Gaussian width per disk
- 2016ApJ...828...46A: point-source model if a/uncertainty < 5
- 2018A&A...616A..88V: up to n=4 terms, 13 free parameters; rho ranges at least 100 klambda wide
- ... 12 more

### Assumptions (bibcode: value)
- 2017A&A...605A..21C: All three H2CO lines are co-spatial; fluxes are lower limits
- 2017A&A...605A..21C: i = 44 deg, PA = 133 deg, d = 122 pc; OPR = 3 at T>=200 K and exponentially lower below; H2 collision partner; dust continuum optically thin
- 2017A&A...605A..21C: 12CO/C18O = 550 for converting to the CO abundance
- 2018MNRAS.481.1976Z: The correct source position and FWHM are known
- 2018MNRAS.481.1976Z: [C II] emission follows an exponential disk with the optical size; a PSF model would underestimate fluxes
- 2018MNRAS.481.1976Z: Stack size fixed to the average optical size of the sources entering the stack
- 2018MNRAS.481.1976Z: Modified black body beta = 2.0
- 2018MNRAS.481.1976Z: Measured fluxes with uncertainties used even when S/N < 3 instead of upper limits
- 2024ApJ...973..135H: Gas-to-dust ratio fixed to 100
- 2024ApJ...973..135H: PAH abundance 0.1 x ISM; cosmic ray ionization rate 1e-18 s^-1
- 2024ApJ...973..135H: Axisymmetric disk; spiral structure not modelled
- 2024ApJ...973..135H: All C and O initially in gas-phase CO and H2O ice
- 2024ApJ...973..135H: Volatile sulfur begins in atomic form
- 2024ApJ...973..135H: SO radial profiles exclude PA 0-90 deg because models lack the NE clump
- 2021ApJ...921...97J: Velocity separation of ~750 km s^-1 between W and E based on [CII] observations
- 2021ApJ...921...97J: SIE lens mass profile, Sersic source profile; fixed magnification mu = 1.3 for E and mu = 2.2 for p-H2O in W from Marrone et al. (2018)
- 2021ApJ...909..212K: Axisymmetric structure; normalize the profile integrated over the entire disk to Ftot.
- 2021ApJ...909..212K: The disk is almost axisymmetric; the correct phase center minimizes imaginary-image intensity RMS.
- 2021ApJ...909..212K: Star: 1.2 M⊙, 4350 K; test L* = 11 and 22 L⊙.
- 2021ApJ...909..212K: Small grains: size distribution ∝s^-3.5, 0.1 μm–0.1 mm.
- 2021ApJ...909..212K: Large grains: Gaussian in logarithmic size; peak 1 mm, minimum 0.6 mm, maximum 1.7 mm.
- 2021ApJ...909..212K: Large-grain scale height = 0.1 gas scale height; small:large grain mass ratio = 1:9.
- 2021ApJ...909..212K: DSHARP dust compositions; average absorption and scattering coefficients over each component's size distribution.
- 2021ApJ...909..212K: Initial scale-height temperature: T = 220(L*/11L⊙)^1/4(R/1au)^-0.5.
- 2021ApJ...909..212K: Gas-to-dust ratio = 100 for Q estimates.
- 2025A&A...693A.237I: Single Gaussian line profile (double Gaussian for CRISTAL-22a)
- 2025A&A...693A.237I: 2D exponential disk profile (n = 1); standard LambdaCDM cosmology with H0 = 70 km s^-1 Mpc^-1, Omega_M = 0.3, Omega_Lambda = 0.7
- 2025A&A...693A.237I: Single Sérsic n = 1 profile for UV (except CRISTAL-13) and circular exponential disk for FIR continuum
- 2025A&A...693A.237I: Two concentric exponential disk components for double-component fit; average redshift z = 5.22
- 2019MNRAS.489.3670K: astrosilicate, 2.7 g/cm3, kappa=2.5 cm2/g at 610 um, sizes 2.5 um to 1 cm, slope -3.5
- 2019MNRAS.489.3670K: LTE, mu=14, axisymmetric
- 2014ApJ...791L...6W: Circular symmetry
- 2019ApJ...871..100H: Inclination 65 deg from Gaussian aspect ratio; center, PA fixed from 1.38 mm fit; grain size distribution n(a) ∝ a^-a_pow
- 2018A&A...612A..29B: z=1.5930 for velocity conversion
- 2019A&A...632A..61G: Dust spectral index alpha ~3-4 in dust-dominated CND regions to estimate dust fraction at S1
- 2021A&A...645A..33B: Upper limits computed as 3 x rms for a point source
- 2018A&A...617A..23B: Gaussian intensity distribution; uncertainties assume reduced chi2 of 1
- 2025ApJ...989...83B: Dust absorption coefficient at 850 micron (value not given) with beta = 2; T_dust = 25 K (or 100 K); dust-to-gas ratio ~0.015
- 2020ApJ...902..141S: Distance 400 pc; axisymmetric models; Ulrich envelope
- 2026A&A...705A.197Z: Dust opacity 1.9 cm² g⁻¹ at 0.89 mm; 1.3 cm² g⁻¹ at 1.3 mm.
- 2026A&A...705A.197Z: Grain-size slope -3.5; mass composition 70% astrosilicates, 15% crystalline water ice, 15% amorphous carbon.
- 2026A&A...705A.197Z: Vertically Gaussian; H_sigma proportional to radius.
- 2026ApJ..1005...94N: Rest frequency of 12CO(2-1) = 230.538 GHz
- 2020MNRAS.498.1319M: Dust mass counts only grains smaller than 1 cm, set by assumed opacities
- 2020MNRAS.498.1319M: Star modelled with Teff = 6500 K and R = 1.3 Rsun template spectrum
- 2015ApJ...812...43B: Additional lenses at same redshift as primary; maximal-lensing Einstein radii fixed for weakly lensed systems
- 2022Icar..37214722L: Pluto continuum brightness temperature is constant at 33 K
- 2022Icar..37214722L: Channel-dependent emission sizes prescribed from image cube modeling
- 2024A&A...687A.308S: Surface density follows a power law; temperature power law in radius, vertically isothermal
- 2024A&A...687A.308S: Constant C17O abundance (1/2240 of CO), CO abundance 1e-4 relative to H2, no dust in the line model
- 2024A&A...687A.308S: C17O emission solely traces rotationally supported disks; envelope and streamer contributions negligible
- 2022ApJ...939L...6B: Point source model at the stellar position
- 2022ApJ...939L...6B: Point source model for the star
- 2022ApJ...939L...6B: Gaussian temporal profile and power-law spectral dependence F_nu \propto \nu^\alpha
- 2022ApJ...939L...6B: Expected stellar photospheric flux at 1.3 mm is 0.53 mJy
- 2015A&A...582A..91C: Emission unresolved (<0.4'' band 3, <0.2'' band 6)
- 2025ApJ...986L..22R: Gas kinetic temperature 4 K
- 2025ApJ...986L..22R: H2CO-CO collision cross-section 5e-14 cm-2 (thermalization approximation)
- 2025ApJ...986L..22R: Opacities 0.17-0.467 m2/kg; dust at equilibrium temperature
- 2019MNRAS.487.4037D: Te fixed at 7 keV
- 2019MNRAS.487.4037D: Line-of-sight axis equals inverse rms average of sky-plane semi-axes
- 2014A&A...566A..74L: Flat disc, n∝r^-1, T∝r^-0.5, LTE, optically thin, inclination 60 deg
- 2021A&A...653A..53A: Gaussian emission distribution gives an initial envelope-size estimate.
- 2021A&A...650A.153D: EMU subtraction includes only the central radio source
- 2015ApJ...808...36M: distance 110 pc; Tb=2Sc^2/(k nu^2 pi theta_maj theta_min)
- 2025A&A...704A..18O: Continuum is formed by optically thick free-free emission
- 2015ApJ...798..124R: axisymmetric, geometrically and optically thin disk; constant dust opacity across disk
- 2021A&A...647A..87L: SMM1-a background temperature T_bg = 5.2 K from average continuum flux density (0.41 mJy beam^-1); IRAS 16293B T_BG = 21 K (full-beam offset) and 52 K (half-be…
- 2026ApJ..1000..141K: Two compact lensed components can be modeled as two point sources; no significant time variability over the 9-month observation interval
- 2026A&A...707A.255C: Airy disk approximation to the ALMA primary beam
- 2026A&A...707A.255C: Template image I^m has flat spectral index across the band
- 2024A&A...682A.186L: Eight literature gNFW pressure profiles considered (A10 UP/MD, M14 UP/NCC, L15 REF/8.0/8.5, G17 EXT)
- 2024A&A...683A..62M: Both lensed images are unresolved point sources
- 2023PASP..135b5002C: Grid Sources are unresolved on ALMA baselines
- 2022A&A...666A..39M: The morphology and integrated flux density of the extended mini-spiral are constant within each observing track (varying only between tracks from 1.16 to 1.18 …
- 2022A&A...666A..39M: Noise is assumed to follow a Gaussian distribution across ~10^4 beams in the field of view to estimate false positive probability (~10^-8 at 7 sigma)
- 2025MNRAS.543..862V: Constant source; per-bin uncertainty scales with sqrt(N)
- 2014ApJ...792L...2C: T=90 K (ISON), 55 K (Lemmon); excitation by H2O and electron collisions and solar IR pumping
- 2023MNRAS.520.1613M: Image-plane pixel covariance errors are small due to dense uv-plane coverage; lens galaxy light contamination is negligible in Band 7.
- 2018ApJ...865...37M: Axisymmetric emission
- 2018ApJ...865...37M: Dust-to-gas ratio 0.01; distance 160 pc; inclination and PA fixed from step 3
- 2019ApJ...882..107R: SFR linear with rest 150-350 um dust emission (constant T_dust and IMF)
- 2026A&A...705A..49Z: Emission from two thin layers, back surface mirrored from front (z_b = -z_f)
- 2026A&A...705A..49Z: Pure Keplerian rotation and purely thermal line width
- 2026A&A...705A..49Z: Temperature and optical depth profiles equal for front and back surfaces
- 2026A&A...705A..49Z: Model B: emission in the midplane with constant optical depth out to R_out
- 2026A&A...705A..49Z: Distances from Gaia DR3
- 2020ApJ...904..131N: Apertures chosen manually at the radius where the curve of growth flattens
- 2020ApJ...904..131N: Extended component described by an exponential function
- 2021ApJ...908..250H: Foreground cloud absorption negligible in the central CO region because of high inclination
- 2021ApJ...908..250H: Gas-to-dust mass ratio 100
- 2021ApJ...908..250H: Scale height exponent p = 1.25 with T proportional to r^-0.5; size distribution n(s) ~ s^-3.5
- 2025PASP..137l4501T: Source size from zero-order moment maps for the image-plane methods
- 2025PASP..137l4501T: Continuum subtraction and weighting skipped; no redshift flux-scaling correction because all mock fluxes equal
- 2018MNRAS.479.5423M: Dust: 70% astrosilicate, 15% amorphous carbon, 15% water ice; size slope -3.5, 1 um-1 cm; 1.5 cm2/g at 1.1 mm; star 1 Msun, 5750 K, 1 Rsun
- 2018MNRAS.479.5423M: Massless particles; flat disc
- 2013ApJ...774...16R: 80% of gas is H2; constant CO:H2 abundance; CO depleted by 1e8 below freezeout; ISM isotopologue ratios
- 2016A&A...590A..33P: Gas-to-dust ratio 100; Ossenkopf & Henning opacities; optically thin envelope
- 2016A&A...590A..33P: Stellar mass 0.05 Msun (0.2 for VLA 1623 A)
- 2018ApJ...856L...5F: All lines assumed Gaussian
- 2018ApJ...869...27V: continuum slope nu^3.5 (beta=1.5)
- 2021A&A...654L...8C: Unresolved ISM represented by a point source
- 2025A&A...699A.279D: Image plus extended Gaussian flux fixed at 1.1 Jy, as assumed in network calibration.
- 2025A&A...699A.279D: First-order GMRF prior on log-ratio pixel intensities, added to a 40 μas Gaussian mean image; variance and correlation length fitted.
- 2025A&A...699A.279D: Other gain phases: zero-mean von Mises prior with concentration π^{-2}.
- 2020A&A...636A..26H: T_dust = 30 K, gas-to-dust 100, kappa 0.7-2.4 (204 GHz) and 2.2-5.0 (397 GHz) cm2/g
- 2026A&A...705A.196H: Azimuthal symmetry and low optical depth
- 2026A&A...705A.196H: Thin disc (h = 0) for the fits
- 2026A&A...705A.196H: Dust in blackbody equilibrium with the star; Gaussian vertical profile; star at the centre of an axisymmetric disc
- 2025MNRAS.537..520Z: Linear frequency dependence for continuum subtraction in uvcontsub
- 2020ApJ...898..146M: Optically thin; r^-0.5 temperature profile; constant dust opacity
- 2015ApJ...811..124S: Lens parameters fixed to ALMA best fit
- 2022A&A...659L...1L: Spectral index of -0.68 for J2258-2758 between 225.5 GHz and 233 GHz
- 2022A&A...659L...1L: Coma brightness distribution varies as 1/rho, leading to V(sigma) proportional to 1/sigma
- 2026A&A...708A.251X: Single-component graybody emission; Hildebrand (1983) dust opacity kappa_0 = 0.1 cm^2 g^-1 at 300 um (gas+dust), spectral index beta = 2.0, mean molecular weig…
- 2026A&A...708A.251X: Dust temperature changes slowly and 1.3 mm emission is purely thermal dust emission
- 2020ApJ...894...76W: Stars are point sources; absolute flux uncertainty ~10%
- 2020ApJ...894...76W: Rayleigh-Jeans regime, S_nu ∝ nu^(2+beta)
- 2020ApJ...894...76W: Background source has constant flux
- 2025NatAs...9.1476C: Steady-state coma; electron density scaling x_ne=0.2; collisional cross-section with H2O 5e-14 cm^-2; T1=T2
- 2025NatAs...9.1476C: CH3OH/H2O constant over ALMA period, 20% added uncertainty
- 2016ApJ...829L..23B: p_down/p_up = (5M^2-1)/4
- 2020PASJ...72...33K: C3 and W modelled as point sources since consistent with the synthesized beam
- 2019ApJ...875...55W: Sirius A is a point source (0.00602")
- 2015A&A...577L...4V: Distance 92 pc
- 2024Natur.633..323V: top-hat disc profile
- 2013ApJ...777L..25M: Silicate (olivine) + amorphous carbon, Mie theory, size exponent -3.5
- 2021A&A...652A...5M: Two point sources adequately describe the data; third image and weak extensions have negligible effect on the spectra
- 2013A&A...558A.123M: Pseudo-ring and components C, D negligible at ALMA frequencies
- 2024A&A...689A..41V: Unresolved sources are point-like with first-order polynomial spectral behaviour
- 2020AJ....160..270F: YSO calibrators stable in flux and spectral index
- 2018A&A...615A..95P: axisymmetric disk
- 2017ApJ...850...83F: Sersic n=1 exponential disk
- 2025ApJ...986L..11S: Back layer not farther from midplane than front layer
- 2021ApJ...917...99Y: Singular isothermal ellipsoid (SIE) lens mass distribution and single Sérsic source profile
- 2021ApJ...917...99Y: Default lensing model mapping from image plane to source plane
- 2023A&A...676A...4C: Envelope emission is constant within R_i, follows Plummer power law between R_i and R_out, and is zero beyond R_out; compact disk is represented by a 2D Gaussi…
- 2026A&A...709A..14Z: Elliptical Gaussian source model with fixed aperture across all channels and transitions
- 2026A&A...709A..14Z: 2D Gaussian parameters fixed to those obtained from the CO(2-1) stack
- 2017MNRAS.465.2595M: Astrosilicate/amorphous carbon/water ice 70/15/15%, Dohnanyi size distribution q=-3.5, 1 um-1 cm, kappa_abs=3.8 cm2/g at 0.88 mm
- 2017MNRAS.465.2595M: T(r)=42(r/150 AU)^-0.5 K
- 2014ApJ...791...20R: Distance 140 pc; gas-to-dust ratio 100; kappa 0.02 cm2/g_gas at 0.89 mm
- 2017ApJ...849...56A: LTE, vertically isothermal, same density power-law index for disk and envelope
- 2019A&A...628A.118B: intrinsic QSO continuum variation across spw0/spw1 less than 1%
- 2021A&A...654A..37D: For W0410–0913, fix the Gaussian center to the CO redshift and fit only the available blue wing
- 2018ApJ...860..162F: Spherically symmetric gas density and SiS abundance; fixed envelope parameters; dust of amorphous carbon
- 2026MNRAS.546ag167S: H0 = 70 km s^-1 Mpc^-1, Omega_m = 0.3, Omega_Lambda = 0.7
- 2026MNRAS.546ag167S: Point-source component traces unresolved quasar/torus emission while extended Spergel component traces the host galaxy
- 2020A&A...633A.126B: Optically thin continuum; distance 192 pc
- 2026A&A...706A...4R: Star is a point source with constant amplitude on long baselines
- 2026A&A...706A...4R: Grains act as blackbodies around a 7.7 Lsun star, T proportional to r^-1/2
- 2026A&A...706A...4R: Disk optically thin
- 2021AJ....161..271F: Dust: 70% astrosilicate, 15% amorphous carbon, 15% water ice; size power law -3.5, 1 um to 1 cm; Band 7 opacity 1.9 cm2/g
- 2021AJ....161..271F: Band 6 emission scaled from Band 7 via free alpha_mm
- 2015ApJ...810..133I: Symmetric Gaussian profile
- 2021PSJ.....2....3M: Flux calibration errors of ~5% for ALMA, 3% for longest four VLA wavelengths, and 7% at 0.9 cm
- 2024A&A...682A..61C: Optically thin dust and Rayleigh-Jeans: beta = alpha - 2
- 2021A&A...647A.173K: Point source model (delta function in uv-plane)
- 2026ApJ...999L..32R: Insolation-driven r_H^-2 scaling of Q(H2O) from Q(OH); thermalization approximation for CH3OH-H2O collisions; Haser density distribution; constant expansion ve…
- 2019A&A...628A.100D: gamma=5/3; flat LCDM Om=0.30, H0=70; kSZ neglected
- 2023PASJ...75..311K: sources are point-like
- 2024A&A...689A.317G: Continuum constant within each spectral window (spectral index 2, <1% variation)
- 2013ApJ...762L..21M: Inclination 89.5 deg
- 2018ApJ...856..117F: Mdisk=0.05 Msun, CO/H2=1e-6, M*=0.7 Msun, d=54 pc, CO freeze-out at 19 K
- 2019MNRAS.485.2092C: Galaxies unresolved (PSF response)
- 2019MNRAS.485.2092C: Dust temperature as in z=2 MS template
- 2024A&A...692A.155K: Each disk brightness distribution constant over the two years; only relative positions change
- 2024A&A...692A.155K: Azimuthally symmetric models
- 2021ApJ...914...36I: Optically thin modified blackbody with T_dust = 47 K, beta = 1.6, kappa_lambda = 0.77 (850 um / lambda)^beta cm^2 g^-1, CMB temperature T_CMB,z = 22.0 K at z =…
- 2021ApJ...914...36I: Circular Gaussian geometry for uv visibility models
- 2020ApJ...891...48H: Axisymmetric, geometrically thin
- 2020ApJ...891...48H: p = 3.5, a_max = 1 mm; vertically isothermal
- 2019MNRAS.484.1257M: Gaussian vertical profile; all particles share the same eccentricity and pericentre
- 2012ApJ...757..129R: vertically isothermal, mu=2.37, Keplerian, vr=vz=0
- 2017AJ....154...24R: distance prior 52.8 ± 1.0 pc
- 2020MNRAS.496..598C: Systemic z = 1.50849 ± 0.00002
- 2024ApJ...977..190X: Use ALMA CO (6-5) linewidth priors: 229 km s−1 for J2054-0005; 183 km/s for J0129-0035.
- 2024A&A...686A.206Y: optically thin torus; uniform posterior distribution functions for all parameters
- 2024A&A...686A.206Y: blackbody multiplied by (lambda0/lambda)^beta for lambda >= lambda0
- 2024A&A...687A.193W: Heliocentric velocity with optical definition; H0 = 73 km s−1 Mpc−1, Omega_M = 0.27, Omega_Lambda = 0.73
- 2020RSOS....700063K: Data are Gaussian about the model; each visibility has two independent degrees of freedom
- 2023PSJ.....4..206R: Asteroids unresolved (point source)
- 2022ApJ...926..159I: <=10% absolute flux calibration uncertainty
- 2021MNRAS.502..521D: Point source (delta function in uv-plane for ATCA)
- 2025PSJ.....6..183C: uniform disk; CMB temperature 2.7 K
- 2020A&A...638A..70D: non-relativistic tSZ, kSZ neglected, flat ΛCDM Ωm=0.30 H0=70
- 2017ApJ...846L..26W: T = 20 K, kappa = 2.3 cm^2/g, distance 140 pc, optically thin
- 2017ApJ...846L..26W: Flared LTE vertically isothermal Keplerian disk; X_CO=1e-4; mu=2.37; inner radius 0.1 au; distance 140 pc with 20 pc uncertainty added in quadrature
- 2024MNRAS.532.1752R: Wall emission optically thick at these wavelengths; total pixel intensity I_wall + I_disc(1 - f_wall)
- 2023MNRAS.524..923Z: Targets are spatially unresolved point sources at the angular resolution of the observations
- 2023MNRAS.524..923Z: Point-source profile centered at the CO detection position
- 2020A&A...635A..12P: Ring centered on center of mass of system
- 2020A&A...635A..12P: LTE; 12CO and 13CO layers at same temperature; CO = 70 x 13CO
- 2024A&A...685A..80Z: Clumps unresolved
- 2017ApJ...842....8M: Negligible vertical thickness (opening angle ~1 deg); temperature T ∝ r^-0.5; ω_p random 0 to 2π
- 2015ApJ...806..154C: LTE level populations; Keplerian rotation dominated by binary mass; vertical hydrostatic equilibrium; vertically isothermal
- 2016A&A...595L...4L: Elliptical Gaussian spatial distribution
- 2016A&A...595L...4L: Vsys = +1.7 km/s
- 2024A&A...682L...3P: Circular rather than elliptical Gaussians to reduce degrees of freedom; circular polarisation V neglected
- 2026A&A...705A.202M: Dust size distribution 1 um to 1 cm, exponent -3.5
- 2026A&A...705A.202M: Composition 70% astrosilicates, 15% crystalline water ice, 15% amorphous carbon by mass
- 2026A&A...705A.202M: Compact spherical grains, Mie opacities
- 2024MNRAS.532.4645H: AGN SED peaks in the UV like the Habing field; post-shock gas strongly radiative; shocks uniformly distributed
- 2021MNRAS.506.1978L: Grain size distribution a_min = 0.9 um to a_max = 1 cm with power-law slope alpha = 3.5; dust density = 2.7 g cm^-3; composition = 70% astrosilicates, 15% amor…
- 2023PSJ.....4..142C: T_cmb = 2.7 K; 5% flux scale error
- 2024ApJ...963..164R: Disks axisymmetric and geometrically thin; i = arccos(sigma_minor/sigma_major); distance 300 pc
- 2025A&A...696A.232G: Axisymmetric brightness profile; features not visible in the continuum images were not fitted
- 2025A&A...696A.232G: Compact disks defined as dust radius < 30 au
- 2020Natur.584..201R: LCDM cosmology, H0 = 67.8 km/s/Mpc, Omega_m = 0.308, Omega_Lambda = 0.691
- 2020Natur.584..201R: lens is a cored elliptical power-law profile plus external shear
- 2023NatAs...7..684K: V_LSRK = 5.7 km s-1; M_* = 2.4 M_sun for Keplerian mask
- 2023NatAs...7..684K: Continuum and C18O 3-2 emission peaks trace the central star location within the central 0.5" pixel
- 2025MNRAS.537.1163A: Common centre set at the shared stellar and dust peak
- 2018MNRAS.474.4500W: HD 141569A radius ~1.5 Rsun; M dwarf radius ~ R_Jupiter
- 2013ApJ...765L..14Q: Keplerian rotation; Qi11 disk structure; constant abundance in a layer; power-law column density
- 2017A&A...606A.121L: kappa = 1.3 (1.2 mm) and 0.30 cm2/g (2.7 mm), dust-to-gas 0.01, mu=2.33, d=235 pc
- 2019ApJ...875L...1E: Distance 16.8 ± 0.8 Mpc
- 2020A&A...638L..13M: Both lensed images point-like within the beam
- 2024ApJ...960....1L: Source is a circular Gaussian with free S_tot, theta_core, x, y
- 2024ApJ...962..166W: Axisymmetric density; Gaussian radial and vertical profiles; constant h=H/r
- 2024ApJ...962..166W: Blackbody grain temperature profile; L_*=15.5 L_sun; grain properties from (cite: beta_pic_dust)
- 2024ApJ...962..166W: H at R_out assumes inclination >84 degrees and h≥0.08; R_out=R+ΔR/2
- 2025PASJ...77..834O: Same procedure applied to all molecular lines
- 2022MNRAS.517.2546L: Vertical aspect ratio h = H/r = 0.05 (fixed); circular orbits; grain sizes a_min = 1.0 um to a_max = 1 cm with power-law index alpha = 3.5; grain density rho =…
- 2026A&A...706A.292S: Distance 156 pc
- 2022A&A...661A.125W: For 33 GHz T_b calculation, assumed the flux density of the fitted component can also be obtained at 1.4 GHz with the same component size
- 2020ApJ...891...80M: Distance 9.725 pc
- 2019ApJ...882..168P: R21 = 1; CMB effect absorbed into alpha_CO
- 2025ApJ...984L..16G: One center, inclination and position angle; concentric, coplanar rings
- 2021NatAs...5..319P: Circular Gaussian source morphology
- 2021A&A...649A.122P: Axisymmetric dust emission
- 2026A&A...706A.174A: Lens redshift unconstrained; magnification depends mainly on image geometry
- 2016ApJ...828..113M: T ∝ r^-0.5 blackbody; i=35 deg, PA=105 deg from Herschel; no offsets fitted
- 2015ApJ...798...85P: Keplerian rotation, ISM CO abundance, vertically isothermal, axisymmetric
- 2023ApJ...948..134P: Each maser spot in a spectral channel is a single point source; noise sigma is constant across visibilities within a single channel; brightest 183 GHz spot at …
- 2026A&A...712A.244H: Single point source dominates emission at phase center
- 2025A&A...703A..15M: 10% absolute flux calibration uncertainty added in quadrature
- 2021MNRAS.502.5390P: Radial and vertical Gaussian density distribution; radially constant vertical aspect ratio h=H/R; blackbody grains with temperature scaling as r^-0.5
- 2023NatAs...7.1048C: Uniform disk continuum, which misses Jupiter's zone/belt structure and alters the line-to-continuum ratio by up to 30%
- 2024A&A...686A.201N: geometrically thin disk for inclination lower limit
- 2016A&A...593A.111T: Mie opacity; 5.4% silicates, 20.6% carbonaceous, 44% water ice, 30% vacuum; dust-to-gas 1e-2
- 2025A&A...700L...5G: Gaussian vertical density; prescribed mid-plane-to-atmosphere temperature gradient; CO scale height independent of mid-plane temperature.
- 2025A&A...700L...5G: Local line width constant across the disk; no a priori temperature information imposed on the depletion boundary.
- 2022A&A...668L...4G: Primary beam response is B(x,y) = (2 J1(theta)/theta)^2
- 2022A&A...668L...4G: For MRG-0138, two point-source components have relative amplitudes fixed by the ratio of mean magnifications between the two lensed images from N18, and result…
- 2021A&A...649A..19S: DSHARP uv-plane Nuker sizes treated as fiducial CO sizes
- 2025A&A...694A.218B: sources unresolved in the dust continuum
- 2016ApJ...828...25L: Compact astrosilicates (Draine 2003), Mie theory temperatures; Kurucz-Lejeune photosphere
- 2015Natur.520..198O: Inclination 37 deg, turbulence 0.05 km/s, M*=1.8 Msun, non-LTE for HCN/HC3N, LTE for CH3CN, HCN/H13CN=70
- 2018ApJ...869...59W: kappa=0.899 cm2/g, Tdust=15 K, d=140 pc
- 2019ApJ...887...24T: symmetric Gaussian surface brightness
- 2021A&A...654A..90L: Cosmology: Omega_lambda = 0.7, Omega_M = 0.3, H_0 = 70 km s^-1 Mpc^-1; symmetrical models (axial ratio = 1) for collapsed visibility fits
- 2017A&A...599A..59K: Blackbody of 2440 K, radius 25.8 mas = 1.8 R* underlies gas
- 2024A&A...692A.205B: Uncertainties dominated by absolute flux density calibration uncertainties
- 2020AJ....159..171F: Disk intrinsically circular
- 2025MNRAS.541...71M: Star at the phase centre; offsets of the disc centre fitted
- 2020AJ....159..288M: Gaussian radial profile, FWHM = 0.2R
- 2018ApJ...869...17L: Axisymmetry
- 2019ApJ...873...50D: Flat Planck LCDM: h=0.677, Om=0.308, OL=0.691
- 2025A&A...699A.373F: Subtraction uncertainties dominated by ALMA flux uncertainties
- 2025A&A...699A.373F: Disc centre from galario coincides with the star position
- 2020MNRAS.495.3409S: Sersic index fixed at n = 1
- 2020A&A...635A..94D: LTE, sharp outer edge, Gaussian vertical profile, constant local line width
- 2024A&A...681A.110W: Flat ΛCDM: H0 = 67.8 km s−1 Mpc−1, ΩM = 0.308, ΩΛ = 0.692
- 2016ApJ...829....6W: Flux uncertainty dominated by 10% absolute flux scale
- 2014ApJ...783L..13P: Ring emission axisymmetric; PA fixed to 62 deg (SAO 206462) and 16 deg (SR 21)
- 2020MNRAS.496..138B: Optical image positions from Inada et al. (2003) apply to CO and radio components
- 2025A&A...699A.265G: Emission dominated by a central point source at the phase center
- 2025Natur.642..905L: The East source is extragalactic and stationary between the 2016 ALMA and 2024 MIRI epochs.
- 2025A&A...700A.165B: Galaxy unresolved at ACA resolution; GMCs co-spatial with star clusters and unresolved
- 2021ApJ...908...54W: point-like source approximation valid
- 2019NatAs...3..230K: Distance 44.9 pc; CO orbits 1.28 Msun point mass
- 2016ApJ...823...37H: Flat LCDM with Omega_M = 0.267, H0 = 71
- 2026MNRAS.552g1700S: Axisymmetric dust disc; full Planck function (without Rayleigh-Jeans approximation)
- 2026MNRAS.552g1700S: Constant eccentricity e and periastron omega across the three Gaussian rings
- 2020MNRAS.498.4635D: Randomly oriented disks; intrinsic axial ratio q=0.1–0.2
- 2025A&A...693A.309S: delta_gdr = 100 and alpha_CI = 17 +/- 3
- 2019AJ....158..162F: Blackbody grains, opacity 2.3 cm^2/g, constant surface density
- 2015ApJ...814...53G: Disk structure from Table 2 (Guilloteau 2011, Pietu 2007); HCN collision rates used for isotopologues
- 2019ApJ...885..106L: Stokes I gradient as proxy for radiation field
- 2023ApJ...954..197I: Visibility noise variance estimated from half the squared difference between adjacent SPWs.
- 2025A&A...693A.151M: Gaussian radial profile; large grains behave as blackbodies
- 2018ApJ...865..157A: Distances from Gaia DR2 with uniform d prior
- 2019ApJ...876..112R: circularly symmetric Gaussian profile
- 2024ApJ...976..258K: Boltzmann level populations, temperature power law in radius
- 2024ApJ...976..258K: Same vertical distribution for all molecules; constant intrinsic line width with radius
- 2024ApJ...976..258K: Distance 150 pc
- 2021ApJ...908..192S: Gaussian-profile radius bias smaller than median measurement uncertainty
- 2020MNRAS.492..572A: Simple 2D Gaussian disc morphology; model-dependent uncertainty estimated at about 1 degree or less based on DSHARP comparison
- 2024A&A...686A.187P: 2D Gaussian intensity profile (Sersic index n = 0.5), which returns r_eff consistent at a 5% level with an exponential profile (n = 1)
- 2024A&A...686A.187P: Flat LambdaCDM cosmology with Omega_m = 0.3, Omega_lambda = 0.7, h_0 = 0.7
- 2019ApJ...881...84S: Dust blackbody temperature T ∝ r^-1/2
- 2019ApJ...875L...3E: Co-located sites act as zero-baseline interferometer; ALMA total flux from QA2
- 2023A&A...674A.101M: Third lensed image and small Einstein ring extensions are negligible and ignored
- 2026A&A...710A..63L: Flux density uncertainties of 10% (22/43 GHz), 20% (86 GHz), and 30% (129 GHz)
- 2018ApJ...856..121G: Exponential disk motivated by Hodge et al. 2016
- 2024A&A...689A.104D: azimuthally symmetric, geometrically thin, optically thick disk
- 2024A&A...689A.104D: axisymmetric; i=5.8 deg, PA=151.6 deg fixed
- 2023A&A...679A.119R: Constant continuum flux across the spectrum for uvcontsub
- 2021AJ....162...99F: outer ring modelled as a Gaussian ring because no inner disk is detected in single EBs
- 2025ApJ...987...61R: 2D Gaussian spatial brightness profile for disk and continuum; arctan asymptotic rotation curve; constant continuum in frequency; flat rotation curve M(r) = r …
- 2018MNRAS.475.4924K: Dust size 10 um to 1 cm, q=11/6; 880 um opacity 0.17 m2/kg
- 2015ApJ...808L...3A: initial circular orbits about 1.0 mm peak with i, PA from Gaussian uv fit
- 2019A&A...623A.111H: Emission dominated by central point source at phase center
- 2023ApJ...945...40C: Total flux densities rescaled to Table 1 of ALMA Partnership et al. (2015)
- 2024A&A...689A.299M: Negligible circular polarization
- 2018MNRAS.474.4347C: 10,000 K blackbody central source with L=Lbol; amax 3 mm, n(a)∝a^-3.5; kappa_abs(1.3mm)=2.2 cm2/g; viscous heating ignored
- 2024ApJ...974..306S: Imaginary part of the visibilities not used because of the azimuthal symmetry assumption
- 2024ApJ...974..306S: Emission from spinning nanometer-size dust does not contribute
- 2021A&A...656A.150P: Disk composed of silicates with Jena-database optical constants
- 2024ApJ...961....2K: Image families assumed at the same redshift when the redshift of a family is unknown (e.g. PJ011646 families 1 and 2)
- 2024ApJ...961....2K: Lens modelled in the image plane rather than the uv plane
- 2018ApJ...869...75M: Continuous surface density at R_halo; no vertical structure
- 2015ApJ...808..102K: distance 140 pc; constant beta; accretion disk cut at 5 Rc
- 2018ApJ...859L..28K: Optically thin emission, I ∝ T_d τ; q=1/2; fixed i and PA from the image
- 2018Sci...361.1016S: Singular isothermal ellipsoid lens
- 2025A&A...701A.203S: Uninformative prior; infinitely thin elliptical ring (delta-ring) for outer disc; homogeneous ellipse for inner disc
- 2025A&A...701A.203S: Power-law density and temperature profiles, vertically isothermal disc, solar metallicity Z = 0.0122, dust composition of 90% water ice and 10% forsterite
- 2023MNRAS.521.2962F: Spherical dust emission geometry (r_dust = sqrt(a*b)/2)
- 2020A&A...633A.114S: Azimuthally symmetric disk
- 2024MNRAS.535.1533B: Singular Isothermal Ellipsoid (SIE) lens mass profile with external shear; flat Lambda-CDM Planck 2020 cosmology (Omega_m = 0.315, Omega_Lambda = 0.685, h = 0.…
- 2019ApJ...875...87D: opacity 2.3 cm^2/g; dust in blackbody equilibrium; L*=0.09 Lsun; d=9.725 pc; vertically isothermal
- 2017A&A...606A..88T: dust-to-gas ratio 0.01; midplane amax=1.023 cm, q=3.0; kappa890=3.37 cm2/g; minimum temperature 7 K
- 2019ApJ...870...80L: Lens at z=0.9
- 2024ApJ...966...59S: Uniform priors; inclination prior ∝ sin i
- 2021MNRAS.508.5259M: kSZE is the sole contributor to the 233 GHz decrement (tSZE negligible at 233 GHz); no relativistic corrections required.
- 2020ApJ...889...59P: Star Teff 1e4 K, R*=5 Rsun; dust n(a)~a^-3.5 from 0.1 um to 3 mm; kappa_abs=2.2 cm2/g at 1.3 mm
- 2026A&A...707A.252K: Two SIE lens mass profiles and a single Sérsic source profile
- 2016MNRAS.460.2933M: Astrosilicate, 3.5 g/cm3, Dohnanyi q=-3.5, amin 1.3 um, amax 1 cm, kappa_abs=1.1 cm2/g at 1.3 mm
- 2015A&A...584A..16P: Inclination and PA fixed
- 2018MNRAS.481L..40S: Compact emission approximated by delta functions; Gaussians gave unstable results
- 2018ApJ...869L..49I: Axisymmetric dust emission
- 2018A&A...613A..34P: Gaussian uncorrelated noise
- 2025ApJ...988..106H: Disk is axisymmetric and geometrically thin
- 2021A&A...646A..59R: Weak continuum subtraction should not remove significant line flux
- 2025A&A...701A.234Z: CO-SLED of star-forming galaxies at z = 2.0 - 2.7 from ASPECS (Boogaard et al. 2020)
- 2025A&A...701A.234Z: α_CO derived using mass-SFR-metallicity relation from Genzel et al. (2015) and metallicity dependence of α_CO from Tacconi et al. (2018)
- 2016A&A...591A.108O: circular disk
- 2018ApJ...857...18S: Lynden-Bell & Pringle surface density, Ulrich envelope, 10% uncertainty on literature photometry and IRS points
- 2018ApJ...867..140L: Lens within 0.2 arcsec of HST optical centroid; no external shear
- 2025A&A...694A.147G: Literature inclinations and position angles (BP Tau from IMFIT)
- 2022MNRAS.515.1751W: Antenna efficiency factor η ~ 0.7 (A_eff ~ 80 m^2 for 12-m dishes)
- 2022MNRAS.513.5790C: The bulk of PDS 70 is not time-variable between epochs
- 2024A&A...690A.197M: Surface density profiles of dust continuum are represented by a circular exponential profile (n = 1)
- 2019ApJ...877L..32M: Axisymmetric surface brightness I∝r^α with T∝r^-0.5
- 2024A&A...683A.141R: 2 Jupiter-mass planet at about 96 au; Lagrangian dust particles entering the planet Hill radius reinjected elsewhere (no circumplanetary emission predicted)
- 2023A&A...673A.116K: Lens is at z = 0.632; companion magnifications assumed to be mu_comp-N = mu_comp-SW = 1
- 2021MNRAS.507.2531Z: Axisymmetric intensity profile I(R) proportional to (R/R_C)^(-gamma_1) * exp(-(R/R_C)^gamma_2); circumbinary discs excluded; Gaia distances from Williams et al…
- 2015ApJ...813...99F: CO frozen out below 19 K and photodissociated above column threshold (abundance reduced by 8 orders of magnitude); LTE; mu=2.37
- 2016MNRAS.462L.101A: circular disk structure, Keplerian rotation for moment-map check
- 2016MNRAS.462L.101A: circular disk, Gaussian representation
- 2018Natur.553...51M: Lens is a singular isothermal ellipsoid
- 2025ApJ...994..214T: Fixed CO/H2 = 1e-4 and 13CO/H2 = 10^-5.3; mean molecular weight 2.37; hydrostatic equilibrium; vertically isothermal disk
- 2025ApJ...994..214T: Pure Keplerian rotation (with pressure effects through the flared model); the CO traces disk gas, not outflows
- 2022MNRAS.512.2426M: Elliptical power-law surface mass density profile (1 or 2 components) with optional external shear
- 2022ApJ...930L...3W: Point source model for visibility fitting; 10% flux calibration error
- 2025A&A...695A..23S: J2356 source size set to 0.75x0.64 arcsec2, the median FWHM of the four ALMA-resolved quasars
- 2018ApJ...859..111H: Grain sizes 0.1 um to 3 mm, n(a)∝a^-3.5; 30% amorphous carbon/70% astrosilicate; kappa_1.3mm=2.2 cm2/g; Tstar=3859 K, R=0.8 Rsun; Rin 0.05 au; gas-to-dust 100
- 2017ApJ...834..135T: dust emission traces star formation if dust temperature is constant
- 2026A&A...709A.174F: Inner Gaussian fixed to image centre for HD 34700A; no inner Gaussian for IRS 48; same eccentricity for all ring and arc components in eccentric fits
- 2021MNRAS.503.5583B: r_1/2 = 0.5 x FWHM for a Gaussian profile
- 2020ApJ...902L..33G: Face-on narrow ring model: real visibility is a zeroth-order Bessel function and the imaginary part is zero
- 2017ApJ...846L..22G: Gaussian source model adequate
- 2024A&A...689A..85G: Dust mass: T_dust 20 K, wavelength 1.33 mm, kappa 2.254 cm2/g, distance 140±10 pc
- 2022MNRAS.510.3734D: Elliptical power-law volume mass density profile for the foreground lens with zero external shear
- 2020ApJ...905...89Y: Observed emission approximated as Keplerian rotation around a central point mass; fitted Mstar represents the total binary mass
- 2020ApJ...905...89Y: Models are axisymmetric while the disk is asymmetric, leaving significant residuals
- 2018A&A...620A.152F: sources point-like in 0.60 arcsec mosaic
- 2024ApJ...961...28H: Arc model based on the vortex description of (cite: lyra13), also (cite: cazzoletti18)
- 2022A&A...665A...3J: NOEMA sources are unresolved at 3mm
- 2017A&A...601A...7F: Central star not included; inclination and PA from SPHERE fit
- 2017NatAs...1E.130Z: Emission arises from mid-plane or adjacent regions characterized by one temperature; C18O/13C18O constant
- 2025A&A...693A..49S: All detections are unresolved, so a Gaussian fit to the visibilities approximates the observations
- 2023A&A...675A..85M: Low-significance detections have observed effective radius r_eff,obs = 0.23'' and axial ratio q_obs = 0.58 (median of high-S/N sources)
- 2020ApJ...898...36L: axisymmetric profiles; Gaussian inner disk for DS Tau, tapered power law for GO/DL Tau, Gaussian rings
- 2019ApJ...882..160Q: Hyperfine levels in LTE; HCO+ collisional rates used for N2H+
- 2024A&A...684A.200G: Unresolved star; fully resolved halo with zero visibility.
- 2024A&A...684A.200G: Stellar black body at T_eff = 10500 K.
- 2020ApJ...900....7H: 12CO/H2 = 1e-4; canonical isotopologue ratios; vertically isothermal; q=0.5, gamma=1.0, i=56.16 deg fixed
- 2016ApJ...818..156C: Vertically isothermal, radial power-law temperature, hydrostatic equilibrium, Keplerian rotation, LTE
- 2017ApJ...850..170O: Dense gas and low-J CO magnification equal to dust and CO(3-2) values
- 2026A&A...710L..10C: Flat spectral index across the band and fixed point-source position x_0
- 2020ApJ...901...74T: Disk model: axis ratio and PA fixed to Gaussian values
- 2020ApJ...895..109F: T_mid0 fixed from literature (DM Tau 19 K freeze-out at 70 au; MWC 480 18.8 K; V4046 Sgr 12 K); distances from Gaia DR2
- 2016ApJ...823L..18H: LTE; Keplerian velocities; ISM isotopologue ratios 69 and 557; T_atm,10=150 K, q_atm=0.5; C18O traces CO column
- 2026ApJ..1001..124M: Dust and gas thermally coupled; constant temperature in azimuth; albedo up to 0.8 (0.7 representative)
- 2020ApJ...898...33C: single Sérsic source; lens mass ratio not fixed
- 2020ApJ...895..126H: Axisymmetric disks
- 2017A&A...603L...6H: CN and C15N co-spatial
- 2024A&A...682A..55M: Axisymmetric 1D disc brightness distribution; power spectrum prior applied to log(I_ν)
- 2022A&A...664A..63X: Lack of significant size variation between CO and dust continuum when comparing with literature
- 2021MNRAS.501.2934C: Azimuthal symmetry of the disc continuum emission
- 2025MNRAS.538.2358S: Axi-symmetric disc emission for Frankenstein fit; five symmetric Gaussian components (inner disc fixed at r_0 = 0, three main rings, and extended emission)
- 2022A&A...662A.121R: Gas-to-dust size ratios are uncorrelated with stellar mass, allowing unbiased comparison with Lupus
- 2017ApJ...839...43O: LTE justified by densities above 1e6 cm-3
- 2020ApJ...902..112B: Constant SFR for 100 Myr and Chabrier IMF in the UV-to-SFR conversion
- 2024ApJ...976..132H: Geometrically thin disk (flared surface for SO 897); posterior approximated as multivariate normal
- 2021ApJ...910...89B: Sizes trace mass-weighted dust on the Rayleigh-Jeans tail, not luminosity-weighted sizes; five of 18 sources at z > 3 may probe optically thick regime
- 2019ApJ...881..159M: Geometrically thin, vertically isothermal, absorption opacity only, nu0=345 GHz, r0=10 au, axisymmetric
- 2024NatAs...8..587F: Distance 140 pc
- 2018ApJ...854..130W: M*=1.7 Msun, d=103 pc, X_CO=1e-4, mu=2.37, inner radius 0.1 AU, Keplerian, vertically isothermal, single plane
- 2024ApJ...977...60Q: Snowline location fixed from the derivative minima; only depletion factor varied
- 2016ApJ...832..110C: global gas-to-dust ratio 100; Teff 3900 K, R* 2.5 Rsun, M* 1 Msun
- 2025MNRAS.543.2723P: Structured if R_peak > 0.05 arcsec, smooth otherwise; unresolved size upper limit 0.1 arcsec (14.5 au)
- 2016A&A...588A.112G: dust-to-gas 0.01; q=3 midplane amax=0.8(R/10AU)^-1.025 mm
- 2026A&A...708L...1Z: Purely Keplerian rotation (including vertical height of optically thick 12CO layer); gas disk mass = 10^-2 M_star; dust disk mass = 10^-4 M_star
- 2020ApJ...900....1F: Sersic index n=1
- 2020AJ....159..229W: companions are unresolved point sources
- 2019A&A...623A.124C: CH3OH and H2CO co-spatial
- 2023PASP..135f4503Z: Synthetic image is the ground truth
- 2019NatAs...3..278K: CO orbits a point mass of 1.28 Msun
- 2021A&A...653A..46V: Disks azimuthally symmetric for inclination
- 2018ApJ...857...69B: LTE level populations; gas density and temperature held fixed
- 2025ApJ...990L..70L: inclination 37 deg and PA 45 deg fixed; outer ring center used as phase center offsets
- 2018ApJ...868L...5K: Inclination and P.A. fixed to ellipse-fit values
- 2025A&A...698A.165A: Azimuthal symmetry
- 2017ApJ...836...30G: LTE level populations; disk structure fixed
- 2019ApJ...873L..19B: Source unresolved since Re=0.23" << 2" beam
- 2017ApJ...836..223W: 70% silicate/30% graphite, grain size 5 nm to 3 mm, power-law -3.5, giving 2.25 cm2/g at 1.3 mm
- 2026ApJ..1003L..30W: Keplerian rotation with the adopted TW Hya geometry for the HC3N mask
- 2018A&A...610A..24F: axisymmetry; flat priors
- 2016A&A...586A..99H: Constant dust opacity 3.4 cm2/g; geometrically thin, vertically isothermal; cos i ~ 1
- 2025ApJ...991..176W: Azimuthally symmetric Gaussian ring
- 2019A&A...628A..95M: axisymmetric brightness profile, independent geometry per disk
- 2017ApJ...840...23L: distance 145 pc
- 2017ApJ...840L..12S: M3 central star; distance 137 pc; McClure 2009 extinction law
- 2017ApJ...843..150F: d=122 pc, PA=312 deg, Mgas=0.09 Msun, XCO=1e-4 for CO, LTE, ring sigma=0.1 R, v_turb proportional to sound speed
- 2019ApJ...874..136S: X_CO = 1e-4, mu = 2.37, vertically isothermal disk, Keplerian rotation, tapered power-law surface density, LTE
- 2018ApJ...869L..48G: Axisymmetric emission; number of rings chosen by visual inspection
- 2017ApJ...844..158S: Distances 131 pc (L1495), 119 pc (L1688), 140 pc Taurus average
- 2017ApJ...851...85B: Uniform opacity, a^-3.5 size distribution, max grain size 1 cm; Gaussian vertical structure
- 2016ApJ...818L..16Z: flat intensity inside the cavity
- 2018ApJ...852..122H: LTE; thin Keplerian disk; inclination 5 deg, PA 152 deg; mu=2.37; CO freezeout step function p=1e-6 below Tfrz
- 2019ApJ...884...97L: constant component sizes with wavelength; concentric in most trials
- 2016ApJ...828...46A: inclination derived from axis ratio assuming circular disk
- 2019ApJ...871....5T: Gaussian ring emission for beam deconvolution
- 2018ApJ...865..155C: distance 161 pc, inclination 48 deg, Keplerian around 1 Msun
- 2018ApJ...869L..50P: Arc follows steady-state vortex prescription (Lyra & Lin 2013)
- 2016A&A...596A..88L: Flat disk inclination from axis ratio; CO may underestimate true inclination because emission arises above the disk plane
- 2018ApJ...859..131L: Distance 59.5 pc, PA 155 deg, inclination 8 deg, M*=0.8 Msun
- 2016MNRAS.463.2265S: circular disk


### Limitations the authors admit
- 2017A&A...605A..21C: Inner 50 AU cannot be modeled due to low resolution and dust optical depth
- 2017A&A...605A..21C: Matched-filter fluxes are only lower limits
- 2017A&A...605A..21C: Parameterized models include no chemistry; formation route cannot be distinguished
- 2018MNRAS.481.1976Z: Fluxes depend critically on the assumed model size taken from optical images
- 2018MNRAS.481.1976Z: Source size cannot be constrained from individual sources because of low S/N
- 2018MNRAS.481.1976Z: Observed in a more extended configuration than requested, giving 5-10 times higher flux errors
- 2024ApJ...973..135H: Vertical temperature and density structure uncertain (face-on disk, one CO isotopologue line)
- 2024ApJ...973..135H: Chemical network lacks grain-surface SO pathways
- 2024ApJ...973..135H: Shock heating not included in the models
- 2024ApJ...973..135H: Disk models have unexplored degeneracies
- 2021ApJ...921...97J: CO(3-2) from ATCA is spatially unresolved (5-6'') between W and E and had to be distributed by scaling to CO(6-5).
- 2021ApJ...921...97J: Signal-to-noise is insufficient for lensing reconstruction in E and for p-H2O(2_1,1-2_0,2) in W, requiring adoption of fixed magnification factors from Marrone et al. (2018).
- 2021ApJ...921...97J: [CI](2-1) and p-H2O(2_1,1-2_0,2) are not significantly detected in E, and the lack of [CI](1-0) observations prevents direct measurement of the [CI] excitation temperature and confirmation of the [CI…
- 2021ApJ...921...97J: In the LVG models, T_kin/T_dust is assumed constant across all visual extinctions/densities rather than varying with extinction or density.
- 2021ApJ...921...97J: Observations of important neutral gas coolants [OI] (63 um) and [SiII] (35 um), which contribute >50% of total cooling, are unavailable.
- 2021ApJ...909..212K: The ∼1 au cavity is far below the effective spatial resolution; no cavity remains allowed.
- 2021ApJ...909..212K: Spectral-index and grain-size conclusions use a very narrow frequency interval within band 6.
- 2021ApJ...909..212K: Radiative-transfer modeling does not derive uncertainties for all parameters.
- 2021ApJ...909..212K: C43-8-only image flux is 10%–20% below combined-configuration flux because of missing flux.
- 2021ApJ...909..212K: Imaginary-visibility asymmetry depends on the chosen phase center.
- 2021ApJ...909..212K: Imaginary visibilities have relatively large errors at short baselines.
- 2021ApJ...909..212K: The proposed mechanisms do not explain the negative asymmetric feature.
- 2021ApJ...909..212K: Synthetic SEDs underpredict flux above 1 cm; stellar free-free emission is a possible contribution.
- 2025A&A...693A.237I: Multiplicity classification is morphological and does not incorporate kinematical state (e.g., CRISTAL-05 appears single in UV/[C II] morphology but is a line-of-sight pair kinematically), and some H…
- 2025A&A...693A.237I: Limited sample size prevents statistically distinguishing [C II] size distributions across multiplicity classes and yields large uncertainties in size ratios.
- 2025A&A...693A.237I: FIR continuum visibilities have lower S/N than [C II] and were modeled with a single circular exponential disk, preventing fair comparison in multiple-UV and multiple-[C II] systems and yielding an u…
- 2025A&A...693A.237I: Available Ly-alpha measurements come from slit spectroscopy and only probe global properties without spatial information.
- 2019MNRAS.489.3670K: Low resolution gives large uncertainties; [CI] optically thick so mass poorly constrained
- 2019MNRAS.489.3670K: DALI outside its validated range
- 2014ApJ...791L...6W: Disk size near largest recoverable scale; imaginary scatter at long baselines may indicate asymmetry needing higher resolution
- 2019ApJ...871..100H: Offset smaller than beam; calibration issue or proper motion not excluded
- 2018A&A...612A..29B: Outflow mass estimates are order of magnitude given chain of assumptions (alpha_CO, excitation).
- 2019A&A...632A..61G: Models are axisymmetric and chi2 values are large
- 2021A&A...645A..33B: Limited angular resolution hampers continuum morphology study
- 2021A&A...645A..33B: Large uncertainties on M* and f_gas from inclination and alpha_CO
- 2021A&A...645A..33B: Moment-map interpretation for marginally resolved J1549+1245 and J1639+2824 is uncertain
- 2021A&A...645A..33B: Sensitivity too limited to constrain cold-gas outflow luminosity
- 2018A&A...617A..23B: Spherical symmetry assumed despite asymmetric emission
- 2018A&A...617A..23B: Weak lines too low S/N for uv fitting
- 2025ApJ...989...83B: Bandpass calibration effects on tau_0 and tau_CO are not quantified
- 2025ApJ...989...83B: CO(3-2) and CO(2-1) opacities are less reliable than CO(1-0), so LTE reconciliation is not attempted
- 2025ApJ...989...83B: Xa1 maximum recoverable scale cannot entirely rule out diffuse emission over larger regions
- 2020ApJ...902..141S: HOPS-56B envelope mass is more uncertain due to nearby source subtraction
- 2020ApJ...902..141S: HOPS-124 and HOPS-157 envelope masses may be lower limits
- 2026A&A...705A.197Z: Axisymmetric, midplane-peaked models can obscure asymmetric structures and inflate heights in warped disks.
- 2026A&A...705A.197Z: Constant aspect ratio excludes radial variation supported by some other studies.
- 2026A&A...705A.197Z: Chosen radial and vertical functions may bias heights or fail to capture source morphology.
- 2026A&A...705A.197Z: HD 109573 and HD 131488 heights are limited by resolution; AU Mic's smallest inferred height may also be inadequately resolved.
- 2026A&A...705A.197Z: Height–mass correlation is partly imposed by the model; gas effects are omitted.
- 2026A&A...705A.197Z: Inclination conversions are not strictly valid for non-Gaussian vertical profiles; quoted inclination errors omit these assumptions.
- 2026A&A...705A.197Z: Mixed modeling methods and resolutions prevent firm multiwavelength conclusions.
- 2026A&A...705A.197Z: Some scattered light disks are vertically unresolved and scale heights depend on dataset signal-to-noise.
- 2026ApJ..1005...94N: The wide range of published distances to NGC 4061 (68–112 Mpc in NED) introduces a ~37% systematic uncertainty in M_BH, dominating the total error budget.
- 2026ApJ..1005...94N: Parameter degeneracies exist between M_BH and M/L_F814W, between y_cen and v_off (due to the beam size relative to the continuum peak), between inclination i and M/L_F814W, and between flux normaliza…
- 2026ApJ..1005...94N: Adopting the HST F555W band instead of F814W for the stellar mass model introduces an additional ~20% uncertainty in M_BH due to stronger dust attenuation in F555W.
- 2026ApJ..1005...94N: Direct event-horizon-scale imaging of the NGC 4061 SMBH (~0.4 uas) is impossible even with ngEHT (~10 uas resolution).
- 2020MNRAS.498.1319M: Planet mass assumes the gap is empty at its centre; a shallower, broader gap would change the inferred width and mass
- 2020MNRAS.498.1319M: Frankenstein profiles lack a primary beam correction
- 2020MNRAS.498.1319M: Lower S/N makes gap width and depth comparison with other discs difficult
- 2020MNRAS.498.1319M: Derived planet masses must be taken with caution since the gap may be inherited or the planet may have migrated
- 2015ApJ...812...43B: Resolution may cause over-predicted sizes and under-predicted magnifications; optically faint lenses may be missed
- 2022Icar..37214722L: The retrieved latitudinal temperature contrast (7 +/- 3.5 K) is only ~2-sigma significant, improvement over the a priori fit (Delta chi^2) is modest, and temperatures retrieved near the polar limb 'b…
- 2022Icar..37214722L: The 2015 disk-averaged and 2017 disk-resolved datasets do not provide fully consistent results on the HCN vertical distribution, especially if a large lower-atmosphere HCN component is included.
- 2022Icar..37214722L: Models of spatial variations in HCN underpredict the observed HCN line areas and contrasts at/beyond the low-latitude limb (reduced chi^2 up to ~1.4), and a satisfactory physical explanation for enha…
- 2024A&A...687A.308S: Disk parameters other than stellar mass are poorly constrained because strict velocity and uv cuts were needed
- 2024A&A...687A.308S: Additional systematic effects such as the model choice may give larger errors than quoted
- 2024A&A...687A.308S: Emission assumed to trace only rotating disks; infall and streamer contributions assumed negligible
- 2020ApJ...888...44C: Small sample and mismatched control sample (archival sources mostly above main sequence).
- 2022ApJ...939L...6B: Shorter integration times imply higher rms noise, so fainter flares will not be detected.
- 2022ApJ...939L...6B: ACA has fewer and smaller (7-m) antennas, resulting in 3-5x higher rms noise per integration than the 12-m array, preventing detection of flares of this brightness in the ACA data.
- 2022ApJ...939L...6B: Due to limited signal-to-noise, spectral index and fractional linear polarization lower limits can only be computed at the peak of the three flares, and lack of polarization calibration leads to larg…
- 2022ApJ...939L...6B: The 12-m ALMA beam (~1.6'' or ~5 AU) cannot spatially resolve the proposed inner dust belts from the central star, so quiescent flux contains both chromospheric and dust contributions.
- 2015A&A...582A..91C: Unresolved emission: source size and common beam filling factor are the main uncertainties; line blending ~20%
- 2019ApJ...882..118X: Uncertainties may be underestimated since continuum subtraction systematics not included
- 2025ApJ...986L..22R: Two-component model is a simplification of the dual-jet geometry; March 17 S/N lower
- 2019MNRAS.487.4037D: Models differ in components so statistical comparison is misleading; overfitting may hide overpressure; X-ray arithmetic limited to linear perturbations
- 2014A&A...566A..74L: Higher sensitivity and resolution needed to verify the Keplerian disc
- 2021A&A...653A..53A: Missing flux and high noise can significantly alter Gaussian fits; sizes are first approximations.
- 2021A&A...653A..53A: Gaussian-size reliability decreases with increasing MLR.
- 2021A&A...653A..53A: Distance uncertainties affect linear sizes and model comparisons.
- 2021A&A...653A..53A: DY Gem's derived size likely does not represent its true CO(2–1)-emitting size.
- 2021A&A...653A..53A: RZ Sgr and FU Mon sizes are relatively unreliable because of aspherical structures.
- 2021A&A...653A..53A: Weak sources have low S/N and cannot be properly Gaussian-fitted.
- 2021A&A...653A..53A: Intrinsic asymmetric structures require additional observations and modelling.
- 2021A&A...653A..53A: Further molecular detections may require optimized analysis; no additional molecular-emission analysis was attempted.
- 2018AJ....156..164B: Dysnomia detection is weak and needs robust detection at multiple locations
- 2021A&A...650A.153D: Chandra source counts do not constrain the ICM temperature distribution.
- 2021A&A...650A.153D: Most X-ray hardness structures have low significance.
- 2021A&A...650A.153D: Radio resolution, sparse sampling, and weak high-frequency detections prevent a detailed spectral-index map.
- 2021A&A...650A.153D: SZ masses may be biased by nonhydrostatic gas and mass–inner-slope degeneracy.
- 2021A&A...650A.153D: Limited spectral coverage leaves thermal and kinetic SZ strongly degenerate.
- 2021A&A...650A.153D: Interferometric filtering favors compact, low-mass pressure models and limits extrapolation to large scales.
- 2021A&A...650A.153D: Weak-lensing positional precision limits confidence in the southern gas–mass offset.
- 2021A&A...650A.153D: Dust mass and temperature require better high-frequency observations.
- 2015ApJ...808...36M: Mira A size and PA uncertainties dominated by systematics; disagreements with Vlemmings et al. 2015 in Band 3
- 2025A&A...704A..18O: Missing short spacings (largest recoverable scale of 190 mas) cause smooth, extended emission on scales larger than ~190 mas (radius >95 mas) to be resolved out, preventing conclusions on large-scale…
- 2025A&A...704A..18O: The 1D spherical LTE model of the SiO lines is simplified; full non-LTE radiative transfer modeling is beyond the scope of the paper, and the model cannot distinguish between a shock-induced density …
- 2025A&A...704A..18O: Dynamic range limitations in channels containing strong 29SiO v=2 J=6-5 maser emission (~18 Jy/beam) increase the RMS noise up to 2.7 mJy/beam.
- 2025A&A...704A..18O: Single-epoch observations at phase 0.53 cannot constrain variability-phase dependence of molecular abundances and line excitation.
- 2015ApJ...798..124R: Data cannot distinguish between gap and double power-law forms; dust opacity degenerate with surface density
- 2021A&A...647A..87L: Observational spatial scales and extraction positions differ between SMM1-a (~500 au, continuum peak) and IRAS 16293B (~70 au, full-beam offset), which may affect molecular ratio comparisons.
- 2021A&A...647A..87L: Baseline subtraction in IRAS 16293B is challenging due to line-richness and can be over-subtracted, causing dips at some HOCH2CN line positions; two temperature components may also be blended.
- 2021A&A...647A..87L: D2CO lines in SMM1-a are blended and the D/H ratio of H2CO in SMM1-a is unknown, preventing a firm conclusion on the H2CO correlation with HOCH2CN.
- 2026ApJ..1000..141K: The Band 3 and Band 4 observations were separated by ~9 months (October 2016 to July 2017) without simultaneous millimeter monitoring, though a few percent variability would shift T_CMB by < 0.1 K.
- 2026ApJ..1000..141K: The -6 km/s component cannot constrain f_c due to lack of saturation, leaving its T_ex uncertain.
- 2026ApJ..1000..141K: H13CN and H13CO+ transitions have low S/N (~3), limiting their statistical significance.
- 2015MNRAS.452...88K: Low spatial resolution prevents determining inclination and detailed kinematics
- 2026A&A...707A.255C: Severe interferometric flux loss (~70% missing flux; only ~29-30% recovered over the whole mosaic) due to missing short spacings in the 12 m array data.
- 2026A&A...707A.255C: Resolved gradients in physical conditions and SEDs on the ~7'' synthesised beam scale cannot be constrained without 7 m (ACA) data; SEDs and spectral indices can only be reliably extracted on primary…
- 2026A&A...707A.255C: Pure-chi2 imaging (lambda=0) fits noise to some extent, creating positive-definite noise in the template that slightly biases the normalisation slope downwards (a_nu0 = 0.96 +/- 0.005).
- 2026A&A...707A.255C: The Airy-disk approximation to the ALMA Band 1 primary beam causes imperfect single-field point-source subtraction (~5% residuals) for the bright off-axis source DoAr 21, requiring a 4-field joint fi…
- 2024A&A...682A.186L: Diffuse emission within 2 arcsec of the AGN is not observationally constrained
- 2024A&A...682A.186L: SZ normalisation may be underestimated because of interferometric filtering of large scales
- 2024A&A...682A.186L: Low significance of SZ and X-ray signals limits detailed morphological comparison
- 2024A&A...682A.186L: ICM metallicity practically unconstrained
- 2024A&A...683A..62M: LTE assumption may affect column densities
- 2024A&A...683A..62M: Ortho and para lines taken eight years apart, so OPR cannot be measured and quasar structure may have changed
- 2024A&A...683A..62M: Excitation model uses crude collision rates
- 2024A&A...683A..62M: Limited S/N prevents determining the nature of the absorbing gas from the line profile
- 2023PASP..135b5002C: 2018 data were engineering tests without a full suite of calibrators

### Settings cards flag as needed but not stated
- casa version: 42
- casa version and pipeline version: 20
- self-calibration solution intervals: 18
- self-calibration solution intervals and number of iterations: 13
- image size and cell size: 13
- uvmodelfit starting parameters: 11
- line-free channels for continuum subtraction: 11
- line-free channels used for continuum subtraction: 11
- line-free channels used for continuum: 10
- line-free channels for uvcontsub: 10
- flux calibrator and flux scale uncertainty: 10
- self-calibration solution intervals and reference antenna: 7
- source coordinates: 7
- line-free channels used for uvcontsub: 6
- line-free channel selection for continuum: 6
- line-free channels and continuum subtraction method: 6
- clean mask, threshold, cell and image size: 6
- flux scale uncertainty: 5
- continuum subtraction and line-free channels: 5
- self-calibration solution interval and reference antenna: 5
- flux calibrators and flux scale uncertainty: 5
- casa/pipeline version: 5
- line-free channel ranges for continuum subtraction: 5
- primary beam correction details: 5
- line-free channel ranges: 5
- briggs robust value: 5
- self-calibration solution intervals and number of rounds: 4
- self-calibration solution interval: 4
- cell size and image size: 4
- image size, cell size, clean threshold and masks: 4
- flux calibration uncertainty: 4
- self-calibration status: 4
- clean threshold, cell and image size: 4
- casa version used for calibration and imaging: 3
- casa version used: 3
- pipeline version: 3
- casa version and calibration pipeline/manual details: 3
- cell size, image size, masks and clean thresholds: 3
- line-free channel ranges for continuum: 3
- flux calibrator and flux-scale uncertainty: 3

## Paper excerpts (40 of 638, chosen for detail and spread over fields/years)

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

### 2018MNRAS.481.1976Z: The [C II] emission as a molecular gas mass tracer in galaxies at low and high redshifts (2018; high_z_galaxies; observational_alma_primary)
- question: Are z~2 main-sequence galaxies [C II] deficient, and what physical parameter drives [C II] luminosity (is [C II] an empirical molecular gas mass tracer)?
- step 1: Reduce and convert the ALMA data
  - method: Standard ALMA pipeline in CASA, then conversion of calibrated cubes to uvfits for analysis in GILDAS [2.3 [C II] emission line measurements: "The data were reduced with the standard ALMA pipeline based on the CASA software"] [2.3 [C II] emission line measurements: "The calibrated data cubes were then converted to *uvfits* format and analyzed with the software GILDAS"]
  - software: CASA, GILDAS
- step 2: Quantify flux and size recovery and noise penalty for resolved sources
  - method: Simulated 2D Gaussians of varying FWHM with simobserve, fitted in the uv plane with uvmodelfit; repeated with GILDAS on the highest S/N source (ID9347) to derive noise vs size relation [A. Resolution: "We then fitted these mock data in the *uv* plane with the task `uvmodelfit`."] [A. Resolution: "We fitted its velocity-integrated map multiple times with the GILDAS algorithm, first with a point source model and then adopting a Gaussian profile with increasing FWHM."]
  - software: CASA, GILDAS
  - parameter: Polynomial relation y = 1.00 + 0.79x + 0.14x^2 + 0.01x^3 between noise ratio y and FWHM ratio x [A. Resolution: "y = 1.00 + 0.79x + 0.14x^2 + 0.01x^3"]
  - assumption: The correct source position and FWHM are known [A. Resolution: "We notice however that these predictions assume that the correct position and FWHM of the source are known."]
  - fitting: Polynomial fit to the noise ratio versus FWHM ratio [A. Resolution: "By fitting the datapoints with a polynomial curve we obtained the following relation"]
  - validation: Fluxes and sizes well recovered for large galaxies given enough S/N; similar results with GILDAS simulations [A. Resolution: "Both sizes and fluxes are very well recovered even for large galaxies provided the data had large enough S/N."] [A. Resolution: "Very similar results are obtained when simulating sources with GILDAS instead of CASA."]
- step 4: Search for [C II] emission by iterative uv-plane spectral extraction
  - method: Fit a source model (PSF, Gaussian or exponential) in the uv plane channel by channel to all four sidebands at the astrometry-corrected HST position; average channels maximising S/N, refit position, and iterate to convergence [2.3 [C II] emission line measurements: "to all four sidebands and channel per channel"] [2.3 [C II] emission line measurements: "we averaged the data over the channels maximizing the detection S/N"]
  - software: GILDAS
  - parameter: Secure detection: emission line significance > 5 sigma in the optimal channel range [2.3.1 Individual [C II] detections: "they have emission line significance $> 5 \sigma$ in the optimal channel range"]
  - validation: Detections robust against the model used for the 1D spectrum extraction; positions consistent with HST peaks [2.3.1 Individual [C II] detections: "The detections are robust against the model used for the extraction of the 1D spectra"]
- step 6: Measure total [C II] fluxes of the four detections
  - method: Fit velocity-averaged line maps in the uv plane with the Fourier transform of a 2D exponential with fixed size and centre from the optical images (GILDAS uv_fit) [2.3.1 Individual [C II] detections: "by fitting their average emission line maps in the *uv* plane with exponential models"] [2.3 [C II] emission line measurements: "We fixed the size and center of the model on the basis of the effective radius and peak coordinates derived from the optical images"]
  - software: GILDAS, CASA
  - parameter: Exponential model size = effective radius from HST stellar mass map (R_e in Table 2) [2.3 [C II] emission line measurements: "We fixed the size and center of the model on the basis of the effective radius and peak coordinates derived from the optical images"]
  - assumption: [C II] emission follows an exponential disk with the optical size; a PSF model would underestimate fluxes [2.3.1 Individual [C II] detections: "whereas by using a PSF model instead we would have underestimated the fluxes"]
  - fitting: uv-plane model fit with GILDAS; uncertainties from the fit [2.3 [C II] emission line measurements: "We then extracted the"]
  - validation: CASA uvmodelfit gives consistent fluxes; Gaussian model also consistent; channel-to-channel scatter consistent with errors [2.3.1 Individual [C II] detections: "We checked that fluxes and uncertainties determined with the `uvmodelfit` task provided by CASA would give consistent results."] [2.3.1 Individual [C II] detections: "we verified that the uncertainties associated to the flux measurement in each channel are consistent with the channel to channel fluctuations"]
- step 8: Tentative detections, upper limits and average [C II] stack
  - method: For undetected sources, measure at fixed HST position with exponential models of fixed optical size, averaging over 719 km/s around the optical redshift; 3 sigma upper limits; stack detections plus tentative detections plus ID2910 in the u… [2.3.2 Tentative and non detections: "using exponential models with the fixed optical size for each galaxy and conservatively averaging"] [2.3.2 Tentative and non detections: "For the four sources with no detected signal we considered $3\sigma$ flux upper limits"]
  - software: GILDAS
  - parameter: Line map averaged over 719 km/s (3 x MAD redshift accuracy summed in quadrature with average detected line FWHM) [2.3.2 Tentative and non detections: "we created emission line maps by averaging channels over 719 km s$^{-1}$"]
  - parameter: Rest-frame 158 um continuum removed from the stack by reducing the flux by 10% [2.3.3 Average [C II] signal: "We finally subtracted the contribution of the rest-frame 158 $\mu$m continuum by decreasing the estimated flux by 10%"]
  - assumption: Stack size fixed to the average optical size of the sources entering the stack [2.3.3 Average [C II] signal: "We fitted the resulting map with an exponential model with size fixed to the average optical size of the sources entering the stacking."]
  - validation: Expected false detections < 0.1 among the six sources for the 2.3 sigma tentative signals; average ratio from stacking agrees with the mean of individual ratios [2.3.2 Tentative and non detections: "Furthermore, when considering the six sources discussed above, we expect to find $<0.1$ false detections."]
- step 9: Measure continuum fluxes and fit IR SEDs for L_IR, M_dust and <U>
  - method: Exponential-profile uv fits of the 450 and 850 um continuum, combined with Spitzer and Herschel photometry in Draine & Li model and modified black body fits [2.4 Continuum emission: "We extracted the continuum flux by fitting the data with an exponential profile, adopting the same procedure described in Section"] [2.4 Continuum emission: "we fitted the IR photometry with (cite: Draine2007) models, supplemented by the use of a single temperature modified black body (MBB) fit to derive a representative dust temperature of the ISM"]
  - software: GILDAS
  - parameter: L_IR integrated over 8-1000 um from SED fitting [Table 1: "IR luminosity integrated over the wavelength range 8 – 1000 $\mu$m as estimated from SED fitting"]
  - parameter: <U> = L_IR/(125 M_dust) [2.4 Continuum emission: "We also determined the average radiation field intensity as $\langle U\rangle = L_{\mathrm{IR}}/(125 M_{\mathrm{dust}})$"]
  - assumption: Modified black body beta = 2.0 [3.1 The [C II] deficit: "with fixed $\beta$ = 2.0 (the same as used in the SED fitting for our sample galaxies)"]
  - assumption: Measured fluxes with uncertainties used even when S/N < 3 instead of upper limits [2.4 Continuum emission: "In these fits we considered the measured *Spitzer*, *Herschel*, and ALMA flux (even if S/N $<$ 3, e.g. there is no detection)"]
  - fitting: Uncertainties on L_IR and M_dust by Monte Carlo simulations; points weighted by their uncertainties [2.4 Continuum emission: "Uncertainties on $L_{\mathrm{IR}}$ and $M_{\mathrm{dust}}$ were quantified using Monte Carlo simulations"] [2.4 Continuum emission: "The contribution of each photometric point to the best fit is weighted by its associated uncertainty."]
  - validation: Conclusions unchanged if upper limits are used in the fits; median L_IR and M_dust agree with literature MS values [2.4 Continuum emission: "If we were to use upper limits in these fits instead our conclusions would not have changed."]
- result: [C II] luminosity, ID9347 (detection) = 0.95 ± 0.30 1e9 Lsun [Table 1: "21.28 $\pm$ 6.73 | 0.95 $\pm$ 0.30 | 11.80 $\pm$ 0.05 | $1.51^{+0.51}_{-0.50}$"]
- result: [C II] luminosity, ID6515 (detection) = 1.23 ± 0.33 1e9 Lsun [Table 1: "24.50 $\pm$ 6.57 | 1.23 $\pm$ 0.33 | 11.68 $\pm$ 0.04 | $2.57^{+0.73}_{-0.73}$"]
- result: [C II] luminosity, ID10076 (detection) = 2.40 ± 0.76 1e9 Lsun [Table 1: "29.03 $\pm$ 9.14 | 2.40 $\pm$ 0.76 | 11.91 $\pm$ 0.03 | $2.95^{+0.96}_{-0.96}$"]
- result: [C II] luminosity, ID9834 (detection) = 1.29 ± 0.19 1e9 Lsun [Table 1: "15.34 $\pm$ 2.21 | 1.29 $\pm$ 0.19 | 11.99 $\pm$ 0.02 | $1.32^{+0.22}_{-0.22}$"]
- result: [C II] flux and luminosity of the average stack (7 galaxies) = F_[CII] = 15.59 mJy; L_[CII] = 1.25 (1e9 Lsun) ± 1.79 (flux); 0.14 (luminosity) mJy; 1e9 Lsun [Table 1: "15.59 $\pm$ 1.79 | 1.25 $\pm$ 0.14 | 11.81 $\pm$ 0.05"]
- result: Average L_[CII]/L_IR of the stack = 1.94e-3 ± +0.34/-0.32 (1e-3) dimensionless [2.3.3 Average [C II] signal: "stacking of the seven targets mentioned above is $(1.94^{+0.34}_{-0.32})\times 10^{-3}$"]
- result: Range of L_IR (8-1000 um) of the sample = 3.5e11 - 1.2e12 ± not stated Lsun [2.4 Continuum emission: "lie between $3.5 \times 10^{11}$ – $1.2 \times 10^{12}$ L$_{\odot}$"]
- result: Average L_[CII]/L_IR of our data and scatter = ~1.9e-3; scatter ~0.15 dex ± not stated dimensionless [3.1 The [C II] deficit: "The average $L_{\mathrm{[C~{\small II}]}}/L_{\mathrm{IR}}$ ratio of our data is $\sim 1.9 \times 10^{-3}$, and has a scatter of $\sim$ 0.15 dex"]
- limitation (authors): Fluxes depend critically on the assumed model size taken from optical images [2.3.1 Individual [C II] detections: "However, the returned fluxes critically depend on the model size that we used and that we determined from the optical images."]
- limitation (authors): Source size cannot be constrained from individual sources because of low S/N [2.3.1 Individual [C II] detections: "Unfortunately, the size of the emission cannot be constrained from the data on individual sources, given the limited S/N ratio."]
- limitation (authors): Observed in a more extended configuration than requested, giving 5-10 times higher flux errors [2.2 Details of ALMA observations: "Our sources were therefore resolved."]
- not stated (card): CASA and pipeline version used for the Band 9 and Band 7 reductions, and whether the archive-delivered calibration was used as is; Flux, bandpass and phase calibrators and the Band 9 flux scale uncertainty; Whether any self-calibration was done; Which array (12-m / 7-m) and antenna numbers were used; Exact channel ranges (optimal channel range) used for each detection and the line-free channels u…

### 2024ApJ...973..135H: Constraints on the Gas-phase C/O Ratio of DR Tau's Outer Disk from CS, SO, and C<SUB>2</SUB>H Observations (2024; protoplanetary_disks, astrochemistry; multi_facility_alma_minor)
- question: What is the gas-phase C/O ratio in the outer disk of DR Tau, constrained by NOEMA CS, SO and C2H observations compared with DALI thermochemical models?
- step 8: Model disk physical structure (SED, 1.3 mm continuum, C18O) with DALI
  - method: DALI models with two dust populations and a generalized surface density profile; two physical models A and B, parameters varied by hand to match SED, continuum profile and C18O radial profile; synthetic visibilities CLEANed for comparison [Modeling DR Tau's disk physical structu…: "we used the DALI thermochemical code (cite: 2012AA...541A..91B; 2013AA...559A..46B) to model DR Tau’s SED, spatially resolved millimeter continuum, and C$^{18}$O $J=2-1$ images in order to constrain the disk density and temperature."] [Dust modeling: "Synthetic visibilities sampled at the same $uv$ points as the 1.3 mm continuum observations were generated from the model images using the `vis_sample` package"]
  - software: DALI, optool, vis_sample, CASA
  - parameter: f_lg = 0.99 (model A) and 0.90 (model B) [Dust modeling: "We fixed $f_{lg}$ to 0.99 for Physical Model A and to 0.90 for Physical Model B"]
  - parameter: Grain size distribution slope p = 3.5 (MRN) [Disk structure parametrization: "The value of $p$ is fixed to 3.5, corresponding to the MRN distribution from (cite: 1977ApJ...217..425M)."]
  - assumption: Gas-to-dust ratio fixed to 100 [Disk structure parametrization: "and $M_\text{gas}/M_\text{dust}$ was fixed to the ISM value of 100"]
  - assumption: PAH abundance 0.1 x ISM; cosmic ray ionization rate 1e-18 s^-1 [Disk structure parametrization: "The PAH abundance was fixed to $0.1\times$ the ISM value"] [C18O modeling: "the cosmic ray ionization rate was set to a relatively low value of 10$^{-18}$ s$^{-1}$"]
  - assumption: Axisymmetric disk; spiral structure not modelled [Disk structure parametrization: "we employ an axisymmetric disk parametrization"]
  - fitting: Manual iteration of parameters to improve visual match; no sampler or priors [Dust modeling: "We then varied these values to improve the visual match between the dust models and the observations."]
  - validation: C18O model radial profile matched to within ~10% interior to 200 au [C18O modeling: "This procedure was repeated until the model matched the observed C$^{18}$O radial intensity profile to within $\sim10\%$ interior to $r=200$ au."]
- step 9: Model CS, SO and C2H chemistry and constrain C/O
  - method: Chemistry-only DALI runs for 1 Myr on physical structures A and B for input C/O of 0.47, 0.7, 0.9, 1.0; sulfur abundance profile iteratively adjusted to match the observed CS radial profile; SO and C2H profiles then compared with observati… [Modeling Procedure: "we ran chemistry-only models for 1 Myr each using input elemental C/O ratios of 0.47, 0.7, 0.9, and 1.0."] [Modeling Procedure: "We first ran a model with a guess for the sulfur abundance, raytraced the CS image cube, subtracted the continuum, generated and CLEANed synthetic visibilities, and then extracted the radial intensity profile."]
  - software: DALI, vis_sample, CASA
  - parameter: Network of 131 species and 1721 reactions [Chemical Network: "Overall, the network consists of 131 species and 1721 reactions."]
  - parameter: Radial intensity profiles binned at 10 au [Modeling Procedure: "which were binned at intervals of 10 au"]
  - assumption: All C and O initially in gas-phase CO and H2O ice [Modeling Procedure: "We assumed that all of the C and O are initially in gas-phase CO and H$_2$O ice."]
  - assumption: Volatile sulfur begins in atomic form [Chemical Network: "For simplicity, volatile sulfur in our models begins in atomic form."]
  - assumption: SO radial profiles exclude PA 0-90 deg because models lack the NE clump [Chemical modeling results: "azimuthal angles at P.A.s between 0 and $90^\circ$ were excluded, since the models did not include the northeast clump."]
  - fitting: Iterative scaling of the input S abundance by the ratio of observed to model CS radial profiles, linearly interpolated onto model cells; no sampler or priors [Modeling Procedure: "We then performed new model runs after adjusting the input sulfur abundance profile based on the ratio of the observed and model CS radial intensity profiles"]
  - validation: Iteration stopped when CS profiles matched within 10% inside 200 au; test with all sulfur initially in SO and test with input C/O = 0.2 [Modeling Procedure: "We stopped this procedure after the observed and model CS radial intensity profiles matched within 10% at radii within 200 au."] [Chemical modeling results: "We ran tests with an input C/O value of 0.2 and found that the CS and SO column densities barely changed beyond 100 au."]
- result: Gas mass, physical models A and B = 0.015 (A), 0.018 (B) ± not stated Msun [Table 3: "$M_\text{gas}$ ($M_\odot$) | 0.015 | 0.018"]
- result: Gas characteristic radius r_c,gas, models A and B = 100 (A), 80 (B) ± not stated au [Table 3: "$r_{c,\,gas}$ (au) | 100 | 80"]
- result: CO depletion factor f_CO = ~0.08-0.09 ± not stated dimensionless [Comparison with other systems: "Based on modeling of C$^{18}$O emission, we estimated a CO depletion factor of $\sim0.08-0.09$ for DR Tau."]
- result: Model sulfur abundance S/H range = ~1e-9 to 1e-5 ± not stated dimensionless [Comparison with other systems: "Our model S/H values range from $\sim10^{-9}-10^{-5}$."]
- limitation (authors): Vertical temperature and density structure uncertain (face-on disk, one CO isotopologue line) [Model limitations: "the vertical temperature and density structures are uncertain because the disk is nearly face-on and only one CO isotopologue line is used to constrain the models."]
- limitation (authors): Chemical network lacks grain-surface SO pathways [Model limitations: "The limited chemical network used in this study does not include grain surface pathways to produce SO"]
- limitation (authors): Shock heating not included in the models [Model limitations: "Our models do not include the effect of shock heating, which can enhance SO production"]
- not stated (card): Which channels were flagged as line emission when building NOEMA continuum uv-tables, and the channel ranges used for the linear baseline continuum subtraction; Reference antenna, solution settings and pipeline version for the NOEMA GILDAS calibration; flux density model adopted for LkHalpha 101; How the two NOEMA epochs were combined and weighted before imaging; CASA clean parameters not given: …

### 2021ApJ...921...97J: Molecular Line Observations in Two Dusty Star-forming Galaxies at z = 6.9 (2021; high_z_galaxies, star_formation, astrochemistry; observational_alma_primary)
- question: What are the physical properties of the molecular interstellar medium, gas mass, CO-to-H2 conversion factor, gas depletion timescales, and heating mechanisms in the two dusty star-forming galaxies of SPT0311-58 at z = 6.9?
- step 1: Image continuum and spectral lines and extract 1D spectra
  - method: Image continuum by combining LSB and USB excluding line channels; subtract continuum in uv-plane using uvcontsub (order 1); image spectral cubes at 100 km/s resolution and single-channel moment 0 maps; extract 1D spectra using apertures of… [Data Reduction and Imaging: "The continuum images are produced by combining the lower and upper side bands (LSB, USB) and excluding the channels containing the line emission."] [Data Reduction and Imaging: "To generate the spectral cubes, we use the same weighting as with the continuum maps and a velocity averaging of 100 $\rm km\ s^{-1}$, after subtracting the continuum using `CASA` task `uvcontsub` with a polynomial fit of order 1."]
  - software: CASA
  - parameter: Briggs weighting, robust = 0.5 [Data Reduction and Imaging: "Briggs weighting and a robust parameter of 0.5 are used, which provide a good compromise between resolution and noise."]
  - parameter: Spectral cube velocity averaging = 100 km s^-1; Moment 0 single channel width = 1000 km s^-1 (W) and 500 km s^-1 (E) [Data Reduction and Imaging: "To generate the velocity integrated intensity maps (moment 0), we produce single channel cubes with a width of 1000 $\rm km\ s^{-1}$ in W and 500 $\rm km\ s^{-1}$ in E, which is $\sim$2 $\times$ full width at half maximum (FWHM) of the lines."]
  - parameter: Spectral extraction apertures: 2.5'' (W) and 1.2'' (E) [Spectral Line Decomposition: "The spectra in W and E are extracted from the 100 $\rm km\ s^{-1}$ spectral cubes using an aperture of 2.5$\ensuremath{''}$ and 1.2$\ensuremath{''}$, respectively."]
  - assumption: Velocity separation of ~750 km s^-1 between W and E based on [CII] observations [Data Reduction and Imaging: "We consider a velocity separation of $\sim$750 $\rm km\ s^{-1}$ between W and E based on the high resolution \[CII\] observations (cite: marrone18)."]
  - fitting: uvcontsub polynomial fit of order 1 [Data Reduction and Imaging: "To generate the spectral cubes, we use the same weighting as with the continuum maps and a velocity averaging of 100 $\rm km\ s^{-1}$, after subtracting the continuum using `CASA` task `uvcontsub` with a polynomial fit of order 1."]
- step 3: Perform gravitational lens modeling in the visibility plane
  - method: Fit parametric lens models to visibility data of 140 GHz and 101 GHz continuum and single-channel (1000 km/s) CO(6-5), CO(7-6), and CO(10-9) lines in W using visilens with SIE lens profile and Sersic source profile(s). [Lens Modeling: "In this analysis, we perform lens modeling on the 140 and 101 GHz ($\sim$272 and 375 $\mu$m rest-frame, respectively) continuum, and $\rm CO(6-5)$, $\rm CO(7-6)$, and $\rm CO(10-9)$ molecular line transitions in W."] [Lens Modeling: "Since the signal-to-noise is not sufficiently high for pixellated modeling, we use a parametric lens modeling code, `visilens` (cite: spilker16)."]
  - software: visilens, emcee
  - parameter: 1000 MCMC chains; lens parameters constrained within best-fit values of 140 GHz single-lens model [Lens Modeling: "As the best-fit parameters, we take the median value of the 1000 MCMC chains with 1$\sigma$ uncertainty."] [Lens Modeling: "For all the lensing reconstruction in this paper, we vary the lens parameters only within the best-fit values obtained from the high resolution 140 GHz measurement set using a single lens."]
  - assumption: SIE lens mass profile, Sersic source profile; fixed magnification mu = 1.3 for E and mu = 2.2 for p-H2O in W from Marrone et al. (2018) [Lens Modeling: "In this code, the background source is parameterized by one or more S$\rm \acute{e}$rsic (cite: sersic68) profiles with seven free parameters: source position relative to the lens ($\rm x_{S}, y_{S}$), flux density (S), half light radius major axis ($\rm a_{S}$), S$\rm \acute{e}$rsic index ($\rm n_{S}$), axis ratio ($…"] [Lens Modeling: "The lensing source is represented by one or more Singular Isothermal Ellipsoids (SIEs), which has five free parameters: the center of the lens relative to phase center ($\rm x_{L}$, $\rm y_{L}$), the lens mass ($\rm M_{L}$) which determines the strength of lensing, the ellipticity of the lens ($\rm e_{L}$), and the po…"]
  - fitting: MCMC sampling (emcee) in the visibility plane; Deviance Information Criterion (DIC) used to select number of sources [Lens Modeling: "This model uses a Markov Chain Monte Carlo (MCMC) algorithm (`emcee` package; (cite: foremanmackey13)) to sample the parameter space."] [Lens Modeling: "The performance of different models is measured by Deviance Information Criterion (DIC; (cite: spiegelhalter02)) to determine the number of sources to include in the model."]
  - validation: 140 GHz lens parameters compared and found to agree with Marrone et al. (2018) pixellated lens model [Lens Modeling: "The lens parameters obtained from the 140 GHz data agree with (cite: marrone18) model."]
- result: Observed 95 GHz continuum flux density (SPT0311-58 W) = 1.26 ± 0.04 mJy [Table 2: "| 1 & 2 | W | 95 | 1.26 $\pm$ 0.04 | 2.09 $\pm$ 0.06 | 0.60 $\pm$ 0.09 | 16 $\pm$ 4 | 26 $\pm$ 12 |"]
- result: Observed 140 GHz continuum flux density (SPT0311-58 W) = 4.12 ± 0.01 mJy [Table 2: "| 3 | W | 140 | 4.12 $\pm$ 0.01 | 2.09 $\pm$ 0.10 | 1.97 $\pm$ 0.31 | | |"]
- result: Observed 95 GHz continuum flux density (SPT0311-58 E) = 0.04 ± 0.02 mJy [Table 2: "| 1 & 2 | E | 95 | 0.04 $\pm$ 0.02 | 1.3 | 0.03 $\pm$ 0.02 | 3.0 $\pm$ 0.4 | 3.5 $\pm$ 0.7 |"]
- result: Observed 140 GHz continuum flux density (SPT0311-58 E) = 0.24 ± 0.01 mJy [Table 2: "| 3 | E | 140 | 0.24 $\pm$ 0.01 | 1.32 $\pm$ 0.06 | 0.18 $\pm$ 0.03 | | |"]
- result: Continuum magnification at 95 GHz (SPT0311-58 W) = 2.09 ± 0.06 dimensionless [Table 2: "| 1 & 2 | W | 95 | 1.26 $\pm$ 0.04 | 2.09 $\pm$ 0.06 | 0.60 $\pm$ 0.09 | 16 $\pm$ 4 | 26 $\pm$ 12 |"]
- result: Continuum magnification at 140 GHz (SPT0311-58 W) = 2.09 ± 0.10 dimensionless [Table 2: "| 3 | W | 140 | 4.12 $\pm$ 0.01 | 2.09 $\pm$ 0.10 | 1.97 $\pm$ 0.31 | | |"]
- result: CO(6-5) magnification (SPT0311-58 W) = 2.08 ± 0.21 dimensionless [Table 3: "| $\rm CO(6-5)$ | W | 2.33 $\pm$ 0.09 | 10.22 $\pm$ 0.39 | 2.08 $\pm$ 0.21 |"]
- result: CO(7-6) magnification (SPT0311-58 W) = 2.13 ± 0.14 dimensionless [Table 3: "| $\rm CO(7-6)$ | W | 2.15 $\pm$ 0.12 | 11.00 $\pm$ 0.61 | 2.13 $\pm$ 0.14 |"]
- result: CO(10-9) magnification (SPT0311-58 W) = 2.16 ± 0.11 dimensionless [Table 3: "| $\rm CO(10-9)$ | W | 1.41 $\pm$ 0.10 | 10.30 $\pm$ 0.73 | 2.16 $\pm$ 0.11 |"]
- limitation (authors): CO(3-2) from ATCA is spatially unresolved (5-6'') between W and E and had to be distributed by scaling to CO(6-5). [Ancillary Data: "Since $\rm CO(3-2)$ is spatially unresolved ($\sim$5 $-$ 6$''$) into W and E, we distribute the flux density of $\rm CO(3-2)$ by scaling to $\rm CO(6-5)$ in the two galaxies."]
- limitation (authors): Signal-to-noise is insufficient for lensing reconstruction in E and for p-H2O(2_1,1-2_0,2) in W, requiring adoption of fixed magnification factors from Marrone et al. (2018). [Lens Modeling: "Since we do not have a good signal-to-noise for lensing reconstruction in E, we adopt a magnification of 1.3 for all the molecular lines. For the same reason, we adopt $\mu = 2.2$ from (cite: marrone18) in p-$\rm H_{2} O (2_{1,1}-2_{0,2})$ in W."]
- limitation (authors): [CI](2-1) and p-H2O(2_1,1-2_0,2) are not significantly detected in E, and the lack of [CI](1-0) observations prevents direct measurement of the [CI] excitation temperature and confirmation of the [CI] abundance-density relation. [Model Outputs: "However, it has to be noted that, due to the lack of \[CI\]$\rm (1-0)$ observations, we cannot reliably confirm the relationship between \[CI\] abundance and gas density."]
- not stated (card): Imaging task (e.g., tclean vs clean), cell size, image size, stopping threshold, and masking strategy in CASA; Exact channel ranges excluded for continuum imaging and used for uvcontsub; Shape and exact centering coordinates of the 2.5'' and 1.2'' apertures used for spectral extraction; Visibility averaging time/frequency bin size used prior to visilens fitting; Full numerical values in Appendix …

### 2021ApJ...909..212K: ALMA Observation of the Protoplanetary Disk around WW Cha: Faint Double-peaked Ring and Asymmetric Structure (2021; protoplanetary_disks; observational_alma_primary)
- question: Resolve disk substructures and constrain dust density, temperature, and grain-size distribution around WW Cha.
- step 1: Determine geometry and recenter visibilities
  - method: Fit a Gaussian in visibility space; move the phase center to the Gaussian center. [Observations and results: "By using the CASA tool `uvmodelfit`, we fitted the data by a Gaussian shape, and the phase center was corrected to be the center of the Gaussian shape by `fixvis`."]
  - software: CASA, uvmodelfit, fixvis
  - parameter: i = 37.2° ± 0.026°; position angle = 32.4° ± 0.04°. [Observations and results: "The inclination $i=37.2^\circ \pm 0.026^{\circ}$ and position angle $\phi=32.4^\circ \pm 0.04^{\circ}$ are obtained by the Gaussian fit by `uvmodelfit`"]
  - parameter: Adopt the geometry fitted to C43-8. [Observations and results: "We adopted the values of the C43-8 data."]
  - fitting: Gaussian visibility fit with uvmodelfit. [Observations and results: "By using the CASA tool `uvmodelfit`, we fitted the data by a Gaussian shape"]
  - validation: Compare C43-8 and C43-4 geometry fits; test the adopted center using imaginary-image RMS in step 6. [Observations and results: "The fitted inclination and position angle are slightly different in the C43-8 (sparse configuration) and C43-4 (compact configuration) data."] [Asymmetric structure: "Hence, the phase center determined by the Gaussian fit is consistent with the center which minimalize the asymmetry."]
- step 4: Fit the axisymmetric intensity profile
  - method: Fit azimuthally averaged real visibilities with a 16-parameter power law, exponential cutoff, two Gaussian bumps, two enhanced/depleted regions, and an inner cavity. [Model description: "we adopted a simple power-law intensity profile with exponential cutoff with two Gaussian bumps, two intensity enhanced/depleted regions and an inner cavity"] [Model description: "has 16 parameters"]
  - software: vis_sample, emcee
  - parameter: C43-8 only; fit 233.0 and 216.7 GHz separately. [fitting result: "Hence, we used only the C43-8 data for the MCMC fitting"] [fitting result: "We performed the MCMC fitting for the upper and lower band data separately."]
  - parameter: Use ρ < 2000 kλ. [Fitting approach: "Since the amplitude of the visibility is comparable with the noise level in $\rho>2000k\lambda$, we used the visibility in the range of $\rho < 2000k\lambda$ in this modeling."]
  - parameter: Fitting section: bins 10 kλ for ρ > 1200 kλ and 20 kλ for ρ < 1200 kλ; observations section gives the reverse. [Fitting approach: "The bin size is $10k\lambda$ for $\rho>1200k\lambda$, and $20k\lambda$ for $\rho<1200k\lambda$."] [Observations and results: "The bin width are $10k\lambda$ for $\rho<1200k\lambda$ while $20k\lambda$ for $\rho>1200k\lambda$"]
  - parameter: Visibility errors: azimuthal standard deviation divided by square root of bin population. [Fitting approach: "is calculated by dividing the standard deviation of azimuthal direction in the visibility domain by the square root of the number of data within the bin."]
  - parameter: 100 walkers; 1000 burn-in steps followed by 1000 steps. [Fitting approach: "In the MCMC fitting, we run 1000 steps with 100 walkers after the burnin phase with 1000 steps (2000 steps in total)."]
  - parameter: Parameter minima and maxima listed in Table 2; Rcav range 0.0–1.9 au in both bands. [Table 2: "| $R_{\rm cav}$ (au) | $1.296^{-0.490}_{+0.348}$ | 0.0 | 1.9 | $0.986^{-0.450}_{+0.353}$ | 0.0 | 1.9 |"]
  - assumption: Axisymmetric structure; normalize the profile integrated over the entire disk to Ftot. [Fitting approach: "In this modeling, we focus on a symmetric structure, following (cite: Zhang_Blake_Bergin2015)."] [Model description: "is integrated over the entire disk is normalized to be $F_{\rm tot}$ which is one of the parameters of the model."]
  - fitting: emcee MCMC with χ² = sum of squared differences between binned observed and model real visibilities, divided by σobs,k²; prior distributions not stated. [Fitting approach: "\chi^2 &= \sum_{k}^{N} \left(\frac{{\rm Re}\left(\overline{V}\right)_{\rm obs,k} - {\rm Re}\left(\overline{V}\right)_{\rm model,k}}{\sigma_{\rm obs,k}} \right)^2,"] [Fitting approach: "We used the Markov Chain Monte Carlo (MCMC) method in the `emcee` package (cite: emcee)."]
  - validation: Compare observed and model visibilities; reduced χ² = 1.58 (upper) and 1.28 (lower); inspect posterior plots. [fitting result: "the reduced $\chi^2$ for the model of the upper band data is $1.58$ and that of the lower band data is $1.28$, respectively."] [Posteriors of MCMC fitting: "The posterior of the MCMC fitting for the upper hand data is shown"]
- step 5: Validate models and map residuals
  - method: Sample the model with the observed measurement set, image identically, and subtract model and observations in visibility space before residual imaging. [fitting result: "The model image is first converted to the ALMA measurement set by `vis_simple` with the observed measurement set"] [fitting result: "We calculated the residual as the subtraction between the model and the observation in the visibility domain, by using `vis_sample`."]
  - software: vis_simple, vis_sample, tclean
  - parameter: Use the observed-image procedure and Table 1 imaging parameters for mock and residual images. [fitting result: "we made a mock observational image by the same procedure of the imaging of the observed data with the parameters listed in Table"]
  - validation: Compare major-axis profiles and residual maps; check agreement of residual patterns between upper and lower bands. [fitting result: "we show the intensity distributions along the major axis in the mock observational image (model) and the observed image."] [fitting result: "The pattern of the residual in the upper and lower band data are similar to each other."]
- step 6: Test asymmetry without an intensity model
  - method: Image only imaginary visibilities; compare with model residuals and vary the phase center. [Asymmetric structure: "the difference between the original and $180^{\circ}$ rotated images has only imaginary part, namely, twice the imaginary part of the original image."] [Asymmetric structure: "shows the synthesized image produced only from the imaginary part of visibility data."]
  - parameter: Use C43-4 and C43-8, both upper and lower bands. [Asymmetric structure: "We produced the synthesized image using all the data, namely, the C43-4 and C43-8 data in upper and lower bands."]
  - parameter: Shift the phase center by ±2 mas (±0.38 au) horizontally and vertically; compare RMS within 0.6 arcsec (114 au). [Asymmetric structure: "we shift the center in $\pm 2$ mas ($\pm 0.38$ au) in horizontal and vertical directions"] [Asymmetric structure: "We calculated the sum of the root mean square value of the intensity at each pixel within the radius of 0.6 arcsec (114 au) from the center"]
  - assumption: The disk is almost axisymmetric; the correct phase center minimizes imaginary-image intensity RMS. [Asymmetric structure: "It is reasonable to assume that the disk structure is almost axisymmetric, despite the disk has some asymmetric structures."] [Asymmetric structure: "Under this assumption, the image deprojected from the imaginary part with the ’correct’ phase center has the minimum root mean square of the intensity."]
  - validation: Central and upper-left features agree with model-subtracted images; fiducial Gaussian center has minimum RMS among tested centers. [Asymmetric structure: "which is consistent with the difference btween the observed image and the axisymmetric model"] [Asymmetric structure: "The figure with our fiducial phase center has the minimum value of RMS among the listed panels."]
- step 7: Construct physical radiative-transfer models
  - method: Use RADMC-3D with axisymmetric dust surface density motivated by the visibility fit, Gaussian vertical density, and iterative temperature-dependent scale height. [Setup and model description: "We setup a model of an axisymmetric dust surface density distribution which is motivated by the intensity distribution derived in the previous section"] [Setup and model description: "In the vertical direction, we adopt a Gaussian shape distribution"]
  - software: RADMC-3D, vis_sample
  - parameter: Fix structural parameters to Table 2 C43-8 values; use surface-density slope s = 0. [Setup and model description: "are fixed to the values given in Table"] [Setup and model description: "For the parameter $s$ that is related to the slope of the dust surface density, we use $s=0$"]
  - parameter: Radial grid: 0.1–1000 au, 256 logarithmic cells; angular grids: 256 each over 0 < θ < 2π and 0 < φ < π. [Setup and model description: "The radial coordinate extends from $0.1$ au to $1000$ au, which is divided into 256 meshes with logarithmic spacing."] [Setup and model description: "The azimuthal angle $\theta$ and polar angle $\phi$ are divided into 256 meshes in $0<\theta < 2\pi$ and in $0<\phi<\pi$"]
  - parameter: 3 × 10^8 photons for thermal Monte Carlo and imaging; 10^7 photons for SED. [Setup and model description: "We adopted $3\times 10^{8}$ photons for thermal Monte Carlo radiative transfer and imaging, and for the SED, $10^{7}$ photons are adopted."]
  - assumption: Star: 1.2 M⊙, 4350 K; test L* = 11 and 22 L⊙. [Setup and model description: "The mass and the surface temperature of the central star are set to $1.2M_{\odot}$ and 4350 K, respectively (cite: Luhman2007)."] [Setup and model description: "By the SED modeling, the stellar luminosity is estimated by $11L_{\odot}$ (cite: Garufi2020)."]
  - assumption: Small grains: size distribution ∝s^-3.5, 0.1 μm–0.1 mm. [Setup and model description: "one is a small dust component with size distribution $\propto s^{-3.5}$, where $s$ is the size of the grains, and the minimum and maximum sizes are $0.1 \ \mu \mbox{m}$ and $0.1 \ \mbox{mm}$, respectively."]
  - assumption: Large grains: Gaussian in logarithmic size; peak 1 mm, minimum 0.6 mm, maximum 1.7 mm. [Setup and model description: "The other is a large dust component with its size having Gaussian distribution in logarithmic space."] [Setup and model description: "The peak of the size distribution $s_{\rm d,large}$ is $1$ mm with the smallest size $0.6$ mm and with the largest size of $1.7$ mm."]
  - assumption: Large-grain scale height = 0.1 gas scale height; small:large grain mass ratio = 1:9. [Setup and model description: "We assume that the scale height of the large grains is 0.1 times the scale height of the gas."] [Setup and model description: "The mass ratio between the small and large grains is set to be 1:9."]
  - assumption: DSHARP dust compositions; average absorption and scattering coefficients over each component's size distribution. [Setup and model description: "We adopt the same compositions of the dust grains to that adopted in (cite: DSHARP_DUST)"] [Setup and model description: "The absorption and scattering coefficients for each component are averaged by the size distribution."]
  - assumption: Initial scale-height temperature: T = 220(L*/11L⊙)^1/4(R/1au)^-0.5. [Setup and model description: "$T=220(L_{\ast}/11L_{\odot})^{1/4}(R/\rm{1au})^{-0.5}$"]
  - fitting: Vary stellar luminosity and Σ0 for observational agreement, then dust size; no full parameter-uncertainty modeling. [Setup and model description: "We first vary the stellar luminosity and $\Sigma_0$ and check the agreement with observations in order to address the uncertainty of the estimate of the disk physical parameters."] [Setup and model description: "We then vary the dust size in order to address the spectral index distribution."]
  - validation: Temperature converges after 2–3 iterations; changing s from 0 to 0.5 affects midplane temperature by only a few Kelvin. [Setup and model description: "In our case, the temperature distribution is converged after 2–3 iterations."] [Setup and model description: "When we use $s=0.5$, the mid-plane temperature is affected only by a few Kelvin."]
- step 8: Constrain mass, temperature, and gravitational stability
  - method: Sample radiative-transfer images with observed visibilities, image with Table 1 settings, compare brightness temperatures and literature SED, and calculate Toomre’s Q. [Setup and model description: "For the imaging, we converted the output of RADMC-3D to the ALMA measurement set with observed measurement set by use of `vis_sample`."] [Intensity and spectral energy distribut…: "compares the brightness temperatures given by the observations and simulations."]
  - software: RADMC-3D, vis_sample
  - parameter: L* = 11 L⊙ with Σ0 = 3 g/cm²; L* = 22 L⊙ with Σ0 = 1.5 g/cm². [Intensity and spectral energy distribut…: "With $L_{\ast}=11L_{\odot}$, we need $\Sigma_0=3\mbox{ g/cm}^2$ which corresponds to the total dust mass of $7\times10^{-3} M_{\odot}$."] [Intensity and spectral energy distribut…: "If the stellar luminosity is larger by a factor of two ($L_{\ast}=22L_{\odot}$), we found that $\Sigma_0=1.5 \mbox{ g/cm}^2$ is enough to reproduce the observation."]
  - assumption: Gas-to-dust ratio = 100 for Q estimates. [Dust density and temperature: "assuming the gas-to-dust ratio of 100."]
  - fitting: Compare model brightness-temperature profiles and SEDs; quantitative fitting statistic not stated. [Intensity and spectral energy distribut…: "compares the brightness temperatures given by the observations and simulations."] [Intensity and spectral energy distribut…: "Both simulations with $L_{\ast}=11L_{\odot}$ and $22L_{\odot}$ can reproduce the ALMA band 6 flux"]
  - validation: Compare SEDs beyond band 6 and test consistency of predicted instability with the absence of fragments. [Intensity and spectral energy distribut…: "For fluxes at the longer wavelengths, namely $3$ mm $<\lambda < 1$ cm, simulations agree with the observation."] [Dust density and temperature: "However, no fragment-like structure is seen in the dust-continuum image."]
- result: Disk inclination from Gaussian visibility fit = 37.2 ± ±0.026 degrees [Observations and results: "$i=37.2^\circ \pm 0.026^{\circ}$"]
- result: Disk position angle from Gaussian visibility fit = 32.4 ± ±0.04 degrees [Observations and results: "$\phi=32.4^\circ \pm 0.04^{\circ}$"]
- result: Approximate inner bump-peak radius = ∼40 ± not stated au [Ring: "One of the peaks is at $\sim 40$ au and the other is at $\sim 70$ au."]
- result: Approximate outer bump-peak radius = ∼70 ± not stated au [Ring: "One of the peaks is at $\sim 40$ au and the other is at $\sim 70$ au."]
- result: Upper-band fitted inner bump boundary Rg,in,1 = 35.908 ± -0.211/+0.216 (1σ) au [Table 2: "$R_{\rm g,in,1}$ (au) | $35.908^{-0.211}_{+0.216}$"]
- result: Lower-band fitted inner bump boundary Rg,in,1 = 35.630 ± -0.314/+0.245 (1σ) au [Table 2: "$35.630^{-0.314}_{+0.245}$"]
- result: Upper-band fitted Gaussian bump center Rrc,1 = 67.046 ± -0.240/+0.216 (1σ) au [Table 2: "$R_{\rm rc,1}$ (au) | $67.046^{-0.240}_{+0.216}$"]
- result: Lower-band fitted Gaussian bump center Rrc,1 = 68.310 ± -0.742/+0.775 (1σ) au [Table 2: "$68.310^{-0.742}_{+0.775}$"]
- result: Upper-band tentative cavity radius = 1.296 ± -0.490/+0.348 (1σ) au [Table 2: "$R_{\rm cav}$ (au) | $1.296^{-0.490}_{+0.348}$"]
- result: Lower-band tentative cavity radius = 0.986 ± -0.450/+0.353 (1σ) au [Table 2: "$0.986^{-0.450}_{+0.353}$"]
- result: Upper-band fitted total flux Ftot = 493.995 ± -0.553/+0.527 (1σ) mJy [Table 2: "$F_{\rm tot}$ (mJy) | $493.995^{-0.553}_{+0.527}$"]
- result: Lower-band fitted total flux Ftot = 418.431 ± -0.593/+0.558 (1σ) mJy [Table 2: "$418.431^{-0.593}_{+0.558}$"]
- result: Upper-band best-fit reduced χ² = 1.58 ± not stated dimensionless [fitting result: "the reduced $\chi^2$ for the model of the upper band data is $1.58$ and that of the lower band data is $1.28$, respectively."]
- result: Lower-band best-fit reduced χ² = 1.28 ± not stated dimensionless [fitting result: "the reduced $\chi^2$ for the model of the upper band data is $1.58$ and that of the lower band data is $1.28$, respectively."]
- result: Relative displacement of inner and outer structure centers = ∼2 ± not stated mas [Inner cavity and binary: "the center of the inner structure can be different in $\sim 2$ mas from the center of the outer structure."]
- result: Dust mass for Σ0 = 1.5 g/cm² = 3 × 10^-3 ± not stated M⊙ [Setup and model description: "when $\Sigma_0=1.5\mbox{ g/cm}^2$, $M_{\rm dust}=3\times 10^{-3} M_{\odot}$."]
- result: Dust mass required in the L* = 11 L⊙ model = 7 × 10^-3 ± not stated M⊙ [Intensity and spectral energy distribut…: "With $L_{\ast}=11L_{\odot}$, we need $\Sigma_0=3\mbox{ g/cm}^2$ which corresponds to the total dust mass of $7\times10^{-3} M_{\odot}$."]
- result: Required Σ0 in the L* = 22 L⊙ model = 1.5 ± not stated g/cm² [Intensity and spectral energy distribut…: "If the stellar luminosity is larger by a factor of two ($L_{\ast}=22L_{\odot}$), we found that $\Sigma_0=1.5 \mbox{ g/cm}^2$ is enough to reproduce the observation."]
- result: Outer bump-peak midplane temperature = about 30 ± not stated K [Ring: "the temperature around the outer peak is about $30$ K"]
- result: Inner bump-peak midplane temperature = about 50 ± not stated K [Ring: "Around the inner peak, the temperature is about $50$ K."]
- result: Toomre’s Q in the 40–70 au bump, assuming gas-to-dust ratio 100 = ≲1 ± not stated dimensionless [Dust density and temperature: "In particular, the dust bump ($40$ au – $70$ au) is gravitationally unstable because $Q\lesssim 1$ and the dust bump may fragment."]
- limitation (authors): The ∼1 au cavity is far below the effective spatial resolution; no cavity remains allowed. [Inner cavity and binary: "further observations are required to confirm the small cavity, because it is much smaller than the angular resolution with the baselines of $<2000k\lambda$."]
- limitation (authors): Spectral-index and grain-size conclusions use a very narrow frequency interval within band 6. [Spectral index: "We should note that the spectral index discussed in this paper is provided from the very narrow range of the observed frequency within band 6."]
- limitation (authors): Radiative-transfer modeling does not derive uncertainties for all parameters. [Setup and model description: "Full modeling studies that derive the uncertainties of all the parameters are beyond the scope of this paper."]
- not stated (card): Image cell size, image dimensions, CLEAN mask, and deconvolution stopping threshold.; Exact calibrated-data selection, flagging, and self-calibration reference antenna and acceptance criteria.; Absolute flux-scale uncertainty and its propagation into spectral-index and model errors.; Which contradictory visibility-bin prescription was actually used in MCMC fitting.; MCMC prior probability distrib…

### 2025A&A...693A.237I: The ALMA-CRISTAL Survey: Spatial extent of [CII] line emission in star-forming galaxies at z = 4−6 (2025; high_z_galaxies; large_program_or_survey)
- question: Investigate the spatial extent, structure, and physical origin of [C II] line emission in star-forming galaxies at z = 4-6, including a search for an extended secondary halo component.
- step 2: Extract [C II] spectra and create velocity-binned visibility datasets
  - method: Extract 1D spectrum in a 1-arcsec aperture from the 20 km/s data cube, fit a 1D Gaussian (double Gaussian for CRISTAL-22a) to define the +-2 sigma (95% flux) velocity range, subtract continuum in uv-plane, and bin visibilities over this ve… [3.2.1. [C ii ] line emission: "(1) extract spectrum with a 1-arcsec aperture from the data cube (20 km/s width per channel)."] [3.2.1 [C ii] line emission: "contains 95 % (= [2.5 %, 97.5 %]) of the total [C ii] line flux, corresponding to 4σ (±2σ from the central frequency ν 0 ) width of Gaussian (≈ 1.7 Gaussian FWHM)."]
  - software: CASA/tclean, scipy (curve_fit), CASA/uvcontsub, CASA/mstransform
  - parameter: 1-arcsec aperture; 20 km/s channel width; +-2 sigma velocity range (95% flux); nchan = 1 [3.2.1. [C ii ] line emission: "(1) extract spectrum with a 1-arcsec aperture from the data cube (20 km/s width per channel)."] [3.2.1. [C ii ] line emission: "We then binned the visibilities into a single channel by specifying `nchan` `=` `1` in the `CASA/mstransform` task."]
  - assumption: Single Gaussian line profile (double Gaussian for CRISTAL-22a) [3.2.1 [C ii] line emission: "As an exceptional case, we fit the [C ii] spectrum of CRISTAL22a, which shows a clear double-peaked line profile, with a double Gaussian."]
  - fitting: 1D Gaussian fit using scipy curve_fit [3.2.1. [C ii ] line emission: "(2) fit the extracted spectrum with a single Gaussian _f_(ν) ∝ exp[(ν − ν 0)2 /2σ2] using the `curve_fit` function within the `scipy` package (Virtanen et al. 2020)."]
  - validation: Visual inspection confirming the +-2 sigma velocity range includes almost all [C II] line emission. [3.2.1. [C ii ] line emission: "The ±2σ velocity range includes almost all of the [C ii] line emission, which assures that the [C ii] size measurements will be performed by fitting the representative velocity range of the emission."]
- step 3: Measure [C II] structural parameters via visibility modeling
  - method: Fit binned [C II] visibilities directly with 2D exponential disk models (1-component for single/multiple-UV, 2-component for pair/multiple-[C II]) and convert major-axis FWHM and axis ratio to circularized effective radius Re,[CII] and lum… [3.2.1. [C ii ] line emission: "We used the `UVMULTIFIT` (Martí-Vidal et al. 2014) to model the visibilities of the [C ii] line emission in the CRISTAL sample."] [3.2.1. [C ii ] line emission: "For a 2-D exponential disk model, the major axis FWHM and major axis effective radius can be related as _R_ _e_,major = 1.21 × FWHM, therefore we obtained a circularized effective radius by calculating _R_ _e_,[CII] = 1.21 × FWHM √_q_, where _q_ is the minor-to-major axis ratio."]
  - software: UVMULTIFIT
  - parameter: Sérsic index n = 1 (exponential disk); 6 free parameters (R.A., Decl., total flux density, major-axis FWHM, minor-to-major axis ratio q, position angle); q fixed to 1 when peak S/N < 8 [3.2.1 [C ii] line emission: "exponential disk model ( _n_ = 1) for all of the [C ii] components and first allow six parameters (R.A., Decl., total flux density, major-axis FWHM, minorto-major axis ratio, and position angle of major axis) free."]
  - assumption: 2D exponential disk profile (n = 1); standard LambdaCDM cosmology with H0 = 70 km s^-1 Mpc^-1, Omega_M = 0.3, Omega_Lambda = 0.7 [1. Introduction: "Throughout this paper, we assume a standard ΛCDM cosmology with _H_ 0 = 70 km s−1 Mpc−1, Ω M = 0.3, and Ω Λ = 0.7."] [3.2.1. [C ii ] line emission: "We assumed a two-dimensional (2-D) exponential disk model (_n_ = 1) for all of the [C ii] components"]
  - fitting: Visibility fitting in UVMULTIFIT with uncertainties from the post-fit covariance matrix and error propagation [3.2.1. [C ii ] line emission: "We estimate the uncertainty by using error propagation. For the uncertainty of each parameter (FWHM and _q_), we adopt the output from the `UVMULTIFIT`, which is estimated from the post-fit covariance matrix (Martí-Vidal et al. 2014)."]
  - validation: Checked residual maps for absence of >2 sigma peaks in the central 2" region and compared with ALPINE-only visibility fits in Appendix B. [3.2.1. [C ii ] line emission: "As can be seen in Figure 3, the best-fit model characterizes the observed [C ii] line emission well and no signal greater than 2σ significance level is present in the central 2′′-region, securing the validity of the fitting."] [3.2.1. [C ii ] line emission: "To fairly compare with the fitting results from the low-resolution archival data alone, we iterate the above procedure by only using the data taken in the ALPINE Survey."]
- step 4: Compare [C II] sizes with rest-frame UV and FIR continuum sizes
  - method: Calculate ratios of circularized [C II] effective radii to rest-frame UV (HST F160W GALFIT) and FIR (ALMA Band-7 UVMULTIFIT) effective radii from Mitsuhashi et al. (2024) and compare across multiplicity classes. [3.2.2. Rest-frame UV and FIR continuum …: "To evaluate the spatial extent of [C ii] line emission, we refer to two continuum size measurements (observing wavelengths of 1.6 µm and 870 µm), which were both performed in Mitsuhashi et al. (2024)."] [4.1. Size comparison: "We start by comparing the measured effective radii among different tracers (rest-frame UV and FIR continua) to characterize the spatial extent of the [C ii] line emission in the context of star formation activity."]
  - software: GALFIT, SExtractor, UVMULTIFIT
  - parameter: Excluded CRISTAL-21 from FIR size comparison due to unreliable FIR size measurement [4.1. Size comparison: "One galaxy that is well below the one-to-one line is CRISTAL-21, which has an unreliable FIR size measurement due to the insufficient S/N of the visibility data, particularly at short _uv_ distances. Therefore, hereafter, we do not include the results of CRISTAL-21 when the FIR radius is related to the discussions."]
  - assumption: Single Sérsic n = 1 profile for UV (except CRISTAL-13) and circular exponential disk for FIR continuum [3.2.2. Rest-frame UV and FIR continuum …: "A single Sérsic model with an index of _n_ = 1 is assumed (except for CRISTAL-13), and nearby objects seen in the HST images are masked by using `SExtractor` (Bertin & Arnouts 1996)."]
  - fitting: Kolmogorov-Smirnov test to compare size distributions across multiplicity classes [3.2.1. [C ii ] line emission: "Although we expect to find larger [C ii] sizes in pair and multiple-UV systems compared to single systems, we were unable to statistically distinguish their size distributions by performing the Kolmogorov-Smirnov test (with _p_ values of 0.23 and 0.12 for the pair and multiple-UV, respectively), largely due to our lim…"]
  - validation: Checked positional offsets between [C II], UV, and FIR emission peaks. [4.1. Size comparison: "We note that the median (average) positional offset between the [C ii] line and rest-frame UV continuum emission is 0.11 (0.14) arcsec (∼ 0.5 kpc in a physical scale), which is smaller than the typical synthesized beam size of the CRISTAL data."]
- step 5: Test for a secondary extended [C II] halo component via visibility stacking
  - method: Extract real part of visibilities for 16 single galaxies (excluding CRISTAL-23c), stack visibilities and normalized residual visibilities, and perform single-component and concentric double-component ('galaxy' + 'halo') exponential disk fi… [4.2. Constituent of [C ii ] line emissi…: "To further confirm this, we stack the visibility data of 16 single galaxies and again perform the visibility modeling in the same manner. We perform both single component and double component fittings."] [4.2. Constituent of [C ii ] line emissi…: "In order to avoid the stacked visibility data being skewed by the bright objects in which the amplitude of residual visibility is also bright, we normalize the residual visibility by the total [C ii] flux obtained from the best-fit model before the stacking."]
  - software: casatool ms (getdata), UVMULTIFIT
  - parameter: 16 single galaxies; 20 klambda and 100 klambda uv-distance bins; average redshift z = 5.22 [4.2 Constituent of [C ii] line emission: "we stack the visibility data of 16 single galaxies and again perform the visibility modeling in the same manner."] [4.2. Constituent of [C ii ] line emissi…: "We show the average values per both 20 kλ and 100 kλ bins, but no clear excess can be found in either case."]
  - assumption: Two concentric exponential disk components for double-component fit; average redshift z = 5.22 [4.2. Constituent of [C ii ] line emissi…: "Here, we assume two concentric exponential disk components."]
  - fitting: Single and double exponential disk fitting in UVMULTIFIT evaluated with reduced chi^2 [4.2. Constituent of [C ii ] line emissi…: "Since the fittings converge to the same reduced χ2 value, we cannot statistically favor either the single or double component model."]
  - validation: Checked residual visibility flux excess at the shortest uv-distance bin (20 klambda) against standard deviation. [4.2. Constituent of [C ii ] line emissi…: "At the smallest 20 kλ bin of the residual visibility, we find a flux excess of 0.15 mJy (1.2σ significance level)."]
- result: Average [C II] effective radius <Re,[CII]> = 1.90 ± 0.77 kpc [3.2.1. [C ii ] line emission: "We calculate an average value and standard deviation of the [C ii] sizes of ⟨_R_ _e_,[CII]⟩ = 1.90 ± 0.77 kpc."]
- result: Average [C II]-to-UV size ratio <Re,[CII]/Re,UV> (entire sample) = 2.90 ± 1.40 dimensionless [4.1. Size comparison: "The size ratio (_R_ _e_,[CII] /_R_ _e_,UV) ranges from 0.94 (CRISTAL-16) to 5.03 (CRISTAL-20) with the average value and standard deviation of ⟨_R_ _e_,[CII] /_R_ _e_,UV⟩ = 2.90 ± 1.40."]
- result: Average [C II]-to-FIR size ratio <Re,[CII]/Re,FIR> (entire sample) = 1.54 ± 0.63 dimensionless [4.1. Size comparison: "We calculate the average size ratio and standard deviation of ⟨_R_ _e_,[CII] /_R_ _e_,FIR⟩ = 1.54 ± 0.63."]
- result: Average [C II]-to-UV size ratio <Re,[CII]/Re,UV> (single galaxies) = 3.21 ± 1.42 dimensionless [4.1. Size comparison: "For galaxies classified as single, we derive ⟨_R_ _e_,[CII] /_R_ _e_,UV⟩ = 3.21 ± 1.42 and ⟨_R_ _e_,[CII] /_R_ _e_,FIR⟩ = 1.62 ± 0.69, while for pair systems we find ⟨_R_ _e_,[CII] /_R_ _e_,UV⟩ = 2.38 ± 1.22 and ⟨_R_ _e_,[CII] /_R_ _e_,FIR⟩ = 1.36 ± 0.45."]
- result: Average [C II]-to-FIR size ratio <Re,[CII]/Re,FIR> (single galaxies) = 1.62 ± 0.69 dimensionless [4.1. Size comparison: "For galaxies classified as single, we derive ⟨_R_ _e_,[CII] /_R_ _e_,UV⟩ = 3.21 ± 1.42 and ⟨_R_ _e_,[CII] /_R_ _e_,FIR⟩ = 1.62 ± 0.69, while for pair systems we find ⟨_R_ _e_,[CII] /_R_ _e_,UV⟩ = 2.38 ± 1.22 and ⟨_R_ _e_,[CII] /_R_ _e_,FIR⟩ = 1.36 ± 0.45."]
- result: Average [C II]-to-UV size ratio <Re,[CII]/Re,UV> (pair systems) = 2.38 ± 1.22 dimensionless [4.1. Size comparison: "For galaxies classified as single, we derive ⟨_R_ _e_,[CII] /_R_ _e_,UV⟩ = 3.21 ± 1.42 and ⟨_R_ _e_,[CII] /_R_ _e_,FIR⟩ = 1.62 ± 0.69, while for pair systems we find ⟨_R_ _e_,[CII] /_R_ _e_,UV⟩ = 2.38 ± 1.22 and ⟨_R_ _e_,[CII] /_R_ _e_,FIR⟩ = 1.36 ± 0.45."]
- result: Average [C II]-to-FIR size ratio <Re,[CII]/Re,FIR> (pair systems) = 1.36 ± 0.45 dimensionless [4.1. Size comparison: "For galaxies classified as single, we derive ⟨_R_ _e_,[CII] /_R_ _e_,UV⟩ = 3.21 ± 1.42 and ⟨_R_ _e_,[CII] /_R_ _e_,FIR⟩ = 1.62 ± 0.69, while for pair systems we find ⟨_R_ _e_,[CII] /_R_ _e_,UV⟩ = 2.38 ± 1.22 and ⟨_R_ _e_,[CII] /_R_ _e_,FIR⟩ = 1.36 ± 0.45."]
- result: Stacked visibility single-component [C II] effective radius Re,[CII] = 1.97 ± 0.10 kpc [4.2 Constituent of [C ii] line emission: "The model is characterized by an effective radius of _R_ _e_,[CII] = 1.97 ± 0.10 kpc"]
- result: Stacked visibility double-component galaxy effective radius Re,gal = 1.91 ± 0.20 kpc [4.2. Constituent of [C ii ] line emissi…: "The brighter component (1.68 ± 0.23 mJy; hereafter “galaxy” component) has a radius of _R_ _e_,gal = 1.91 ± 0.20 kpc, which is similar to the best-fit single component."]
- result: Stacked visibility double-component halo effective radius Re,halo = 9.17 ± 28.2 kpc [4.2. Constituent of [C ii ] line emissi…: "The other component (0.16 ± 0.27 mJy; hereafter “halo” component) has an extended radius of _R_ _e_,halo = 9.17 ± 28.2 kpc."]
- result: Stacked visibility halo flux fraction = 8.7 ± 13.4 % [4.2. Constituent of [C ii ] line emissi…: "The flux of the “halo” component constitutes 8.7 ± 13.4 % of the total flux"]
- result: CRISTAL-01a [C II] effective radius Re,[CII] = 3.05 ± 1.19 kpc [Table 1: "CRISTAL-01a 10:00:54.508 2:34:34.46 0.68 ± 0.16 789 3.05 ± 1.19 0.59 ± 0.27 21 ± 24 8.62"]
- result: CRISTAL-02 [C II] effective radius Re,[CII] = 2.58 ± 0.28 kpc [Table 1: "CRISTAL-02 10:00:21.499 2:35:11.01 2.63 ± 0.16 533 2.58 ± 0.28 0.52 ± 0.07 153 ± 5 9.31"]
- result: CRISTAL-05 [C II] effective radius Re,[CII] = 1.57 ± 0.28 kpc [Table 1: "CRISTAL-05 10:00:09.422 2:20:13.84 0.94 ± 0.08 523 1.57 ± 0.28 0.31 ± 0.08 160 ± 5 8.90"]
- result: CRISTAL-24 [C II] effective radius Re,[CII] = 3.00 ± 1.03 kpc [Table 1: "CRISTAL-24 10:00:02.715 2:37:39.99 14.76 ± 2.50 1291 3.00 ± 1.03 0.74 ± 0.25 92 ± 31 9.96"]
- result: CRISTAL-25 [C II] effective radius Re,[CII] = 2.45 ± 0.35 kpc [Table 1: "CRISTAL-25 10:01:12.502 2:18:52.55 3.35 ± 0.19 477 2.45 ± 0.35 0.65 ± 0.10 35 ± 10 9.32"]
- limitation (authors): Multiplicity classification is morphological and does not incorporate kinematical state (e.g., CRISTAL-05 appears single in UV/[C II] morphology but is a line-of-sight pair kinematically), and some HST-single sources are pairs in sharper J… [3.1. Classification based on multiplici…: "We note, however, that this is still a crude classification, as we do not consider the dynamical state of each galaxy obtained from kinematical analysis."]
- limitation (authors): Limited sample size prevents statistically distinguishing [C II] size distributions across multiplicity classes and yields large uncertainties in size ratios. [3.2.1. [C ii ] line emission: "Although we expect to find larger [C ii] sizes in pair and multiple-UV systems compared to single systems, we were unable to statistically distinguish their size distributions by performing the Kolmogorov-Smirnov test (with _p_ values of 0.23 and 0.12 for the pair and multiple-UV, respectively), largely due to our lim…"]
- limitation (authors): FIR continuum visibilities have lower S/N than [C II] and were modeled with a single circular exponential disk, preventing fair comparison in multiple-UV and multiple-[C II] systems and yielding an unreliable FIR size for CRISTAL-21. [3.2.2. Rest-frame UV and FIR continuum …: "Unlike [C ii] line emission, all of the FIR continuum emission was fit in a single exponential disk component due to the lower S/N detection compared to the [C ii] line emission."]
- not stated (card): Exact CASA version used for data reduction and analysis; Calibration procedure (pipeline vs manual) and self-calibration details for CRISTAL survey data; Which specific targets used Briggs (R = 0.5) vs Natural (R = 2.0) weighting for initial spectrum extraction; Exact frequency channel ranges used for continuum subtraction in uvcontsub for each target; Exact central frequencies (nu_0) used for sp…

### 2019MNRAS.489.3670K: Imaging [CI] around HD 131835: reinterpreting young debris discs with protoplanetary disc levels of CO gas as shielded secondary discs (2019; debris_disks, astrochemistry; observational_alma_primary)
- question: Can debris discs with protoplanetary-disc levels of CO be secondary (shielded by accumulated neutral carbon) rather than hybrid, tested with new ALMA [CI] and continuum data of HD 131835 plus a semi-analytic model?
- step 1: Fit continuum visibilities with dust ring model
  - method: RADMC-3D images converted to visibilities with GALARIO; emcee MCMC over 8 parameters [3.2: "We use a Bayesian MCMC approach to constrain the 8 free parameters of the model."]
  - software: RADMC-3D, GALARIO, emcee
  - parameter: 100 walkers, 1200 steps after burn-in [3.2: "We ran the MCMC with 100 walkers and for 1200 steps after the burn-in period."]
  - assumption: astrosilicate, 2.7 g/cm3, kappa=2.5 cm2/g at 610 um, sizes 2.5 um to 1 cm, slope -3.5 [3.2: "we assume an astrosilicate composition with a density of 2.7 g$\,$cm$^{-3}$"]
  - fitting: uniform priors, likelihood ∝ exp(-chi2/2) [3.2: "We assume that the priors are uniform"]
  - validation: Best-fit model subtracted in image plane; residuals within noise [3.2: "checked that the remaining residuals were all within the expected noise level"]
- step 2: Fit [CI] cube with Gaussian and double power-law gas models
  - method: RADMC-3D in LTE plus GALARIO, MCMC on visibility cube; LTE checked with LIME [4.2: "We also use RADMC-3D to produce the [CI] gas image and convert to visibilities using GALARIO"]
  - software: RADMC-3D, GALARIO, LIME, emcee
  - parameter: 10 free parameters for double power law [4.2.2: "This leaves us with 10 free parameters that are $R_0$, $\Sigma_0$, $T_0$, $\beta_1^s$ $\beta_2^s$, $\beta_1^t$, $\beta_2^t$, $i$, PA and $v_\star$."]
  - assumption: LTE, mu=14, axisymmetric [4.2: "We thus assume that LTE is a good approximation even for very low carbon ionisation fractions."]
  - fitting: same MCMC procedure as continuum [4.2.2: "We explore the parameter space with the same MCMC procedure as presented for the continuum"]
  - validation: Compared model and data moment-0 visibilities; some residuals remain [4.2.2: "leaves a few significant residuals probably linked to the detailed structure of the emission"]
- result: Dust mass = 0.71 ± +0.03/-0.05 Mearth [Table 1: "$M_{\rm dust}$ (M$_\oplus$) | $0.71^{+0.03}_{-0.05}$"]
- result: Dust ring radius R0 = 90.5 ± +3.8/-3.7 au [Table 1: "$R_0$ (au) | $90.5^{+3.8}_{-3.7}$"]
- result: C0 mass = 3.1e-3 best fit; 2.7e-3 to 1.2e-2 (16-84%) ± percentile range Mearth [4.2.2: "we find that the best fit is for a mass $M_{{\rm C}^0}=3.1 \times 10^{-3}$ M$_\oplus$."]
- result: Gas temperature T0 (double power law) = 30 ± +5/-4 K [Table 2: "$T_0$ (K) | $28^{+4}_{-4}$ | $30^{+5}_{-4}$"]
- result: Stellar radial velocity = 3.57 ± 0.1 km/s [4.2: "3.57$\pm$0.1 km/s (heliocentric frame)"]
- limitation (authors): Low resolution gives large uncertainties; [CI] optically thick so mass poorly constrained [4.2.2: "The C$^0$ mass is not well constrained because the line is optically thick in the whole disc"]
- limitation (authors): DALI outside its validated range [footnote 5: "is strictly outside the parameter range for which DALI – a protoplanetary disc code – is validated to give correct results."]
- not stated (card): Line-free channel ranges for uvcontsub; Image size, cell size, CLEAN threshold/masks; CASA and pipeline versions; MCMC prior bounds and burn-in length; Velocity range used for moment-0; Grid ranges for the 1000-model semi-analytic grid; Whether the archive pipeline products were used as delivered

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

### 2018A&A...612A..29B: Molecular outflow and feedback in the obscured quasar XID2028 revealed by ALMA (2018; agn_and_quasars, high_z_galaxies; observational_alma_primary)
- question: Is there a molecular (CO) outflow and what are the gas content, depletion time and disc kinematics in the obscured QSO XID2028, which hosts a massive ionised outflow?
- step 1: Measure 1.3 mm continuum
  - method: Clean image with Briggs weighting of line-free TDM channels, then Gaussian fit to visibilities [2.1 1.3 mm continuum: "We then estimated the continuum flux by fitting with a Gaussian function the visibilities of the continuum dataset (via the CASA task `uvmodelfit`)."]
  - software: CASA clean, uvmodelfit
  - parameter: Visibility noise 7.5 uJy; flux 142 uJy [2.1 1.3 mm continuum: "We measured a continuum flux of 142 $\mu$Jy for a detection significance of 19$\sigma$"]
  - fitting: Gaussian fit in uv plane [2.1 1.3 mm continuum: "fitting with a Gaussian function the visibilities of the continuum dataset"]
- step 2: Measure CO(5-4) flux and size
  - method: Continuum-subtracted cube; spectrum from polygonal region; Gaussian uvmodelfit in -800 to 800 km/s [2.2 CO(5-4) emission line: "We then estimated the line flux by fitting with a Gaussian function the visibilities of the continuum-subtracted dataset (using the CASA task `uvmodelfit`), in the same velocity range as above."]
  - software: CASA, uvmodelfit
  - parameter: velocity range -800 to 800 km/s; 20 km/s binning for spectrum [2.2 CO(5-4) emission line: "integrated over the velocity range \[-800$\div$800 km s$^{-1}$\] around the expected line frequency"]
  - assumption: z=1.5930 for velocity conversion [2.2 CO(5-4) emission line: "The redshift of the narrow component of the rest-frame optical emission lines (z=1.5930) was adopted to convert the frequency to velocity space"]
  - fitting: Single Gaussian line fit, FWHM~500 km/s, reduced chi2 2.27 [2.2 CO(5-4) emission line: "the fit with a single Gaussian component returns FWHM$\sim$500 km s$^{-1}$"]
- step 3: Fit low-J CO fluxes in PdBI/ALMA Band 3 data with fixed CO(5-4) spatial parameters
  - method: uv-plane model fit using position and FWHM from CO(5-4) [2.3 Other CO transitions from PdBI and …: "We performed the measurement in uv space, where the model of the source is convolved with the beam"]
  - software: CASA
- result: 1.3 mm continuum flux of nucleus = 142 ± 7.5 uJy [Table 1: "S$_{\rm cont, nucleus}$ ($\mu$Jy) | 142$\pm7.5$"]
- result: Continuum deconvolved FWHM = 0.30 ± 0.05 arcsec [Table 1: "FWHM (deconvolved, $''$) | 0.30$''$$\pm$0.05$''$"]
- result: CO(5-4) line intensity = 0.77 ± 0.03 Jy km/s [Table 1: "$I_{\rm CO(5-4)}$ (Jy km s$^{-1}$) | 0.77$\pm$0.03"]
- result: CO(5-4) line luminosity log L' = 9.63 ± 0.05 K km/s pc^2 [2.2 CO(5-4) emission line: "logL’$_{\rm CO(5-4)}$/(K km s$^{-1}$ pc$^2$)=9.63$\pm0.05$"]
- result: CO(2-1) flux (ALMA Band 3) = 0.35 ± 0.12 Jy km/s [2.3 Other CO transitions from PdBI and …: "I$_{\rm CO(2-1)}$=0.35$\pm$0.12 Jy km s$^{-1}$"]
- limitation (authors): Outflow mass estimates are order of magnitude given chain of assumptions (alpha_CO, excitation). [6 High velocity molecular gas: "We stress that the two values suffer from large uncertainties, given the chain of assumptions employed"]
- not stated (card): Briggs robust value, cell size, image size, clean threshold and masks; Exact velocity range/channel selection used for continuum subtraction of the CO cube; Details of the uvmodelfit starting parameters; Exact SLED-extrapolation ratios (r51 etc.) used for CO(1-0) flux; Flux correction and noise estimates for the Band 3 and Band 7 snapshot datasets and how they were imaged; 3D-BAROLO ring setup an…

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

### 2021A&A...645A..33B: The WISSH quasars project. IX. Cold gas content and environment of luminous QSOs at z ∼ 2.4-4.7 (2021; agn_and_quasars, high_z_galaxies; observational_alma_primary)
- question: Systematic study of cold gas (CO, [CII]) and far-IR continuum properties, environment, star formation efficiency, dynamical mass and molecular gas fraction in the host galaxies of hyper-luminous WISSH QSOs at z~2.4-4.7
- step 1: Calibrate, continuum-subtract and image cubes and continuum maps
  - method: ALMA pipeline calibration; uv-plane continuum subtraction with first-order polynomial; tclean cubes (hogbom, natural weighting, 40 km/s channels, 3 x rms threshold); same procedure for continuum maps [2.2 Data reduction and analysis: "ALMA data were calibrated using the CASA software (cite: McMullin07) in the pipeline mode."] [2.2 Data reduction and analysis: "The same deconvolution procedure was adopted to produce continuum maps."]
  - software: CASA, tclean, GILDAS CLIC, MAPPING
  - parameter: 40 km/s channels, natural weighting (except J1639+2824) [2.2 Data reduction and analysis: "a natural weighting of the visibilities and a common spectral channel width of 40 km s"]
  - parameter: J1639+2824 taper beyond 900 klambda [2.2 Data reduction and analysis: "we applied a tapering of the visibilities beyond 900 k$\lambda$"]
  - parameter: Continuum-subtraction fit to |v|>500 km/s, first-order polynomial [2.2 Data reduction and analysis: "We performed a fit in the uv plane to all channels with velocity $|v|>500$ km s$^{-1}$ by adopting a first order polynomial continuum model."]
- step 2: Measure continuum and line flux densities and sizes
  - method: Image-plane 2D Gaussian fit with imfit and uv-plane fit with MAPPING uvfit; point or Gaussian source models; QSO fitted and subtracted before nearby emitters [2.2 Data reduction and analysis: "fitted the data in the image plane with a two-dimensional Gaussian profile by using CASA task"] [2.2 Data reduction and analysis: "performed a fit of the visibilities in the uv plane with MAPPING task uvfit"]
  - software: CASA imfit, MAPPING uvfit
  - parameter: uv channels averaged spectrally and temporally to 30 s [2.2 Data reduction and analysis: "channels associated with the continuum emission, were spectrally and temporally averaged (to 30 s)"]
  - parameter: Gaussian preferred if size differs from zero at >3 sigma and detection significance increases [2.2 Data reduction and analysis: "A Gaussian model was preferred when resulting into an increased significance of the detection and a size different from null size at $>3\sigma$"]
  - assumption: Upper limits computed as 3 x rms for a point source [Table 2 notes: "upper limit computed for a point source as $3\times\sigma_{\rm cont}$"]
  - fitting: Point-source or Gaussian source models fitted to visibilities; image-plane 2D Gaussian [2.2 Data reduction and analysis: "We then fitted point source or Gaussian source models to the visibilities."]
  - validation: Subtracted models give uniform residual noise maps; image and uv fits consistent [2.2 Data reduction and analysis: "We checked that subtracting the models resulted into uniform residual noise maps."] [2.2 Data reduction and analysis: "We verified that (i) and (ii) give consistent sizes and flux density values."]
- result: J1433+0227 rest-frame 1935 GHz continuum flux density = 7.7 ± 0.3 mJy [3.1 Continuum emission: "we measure a strong rest-frame 1935 GHz continuum flux density of $7.7\pm0.3$ mJy"]
- limitation (authors): Limited angular resolution hampers continuum morphology study [3.1 Continuum emission: "The limited angular resolution of most observations presented in this work hampers a detailed study of the continuum emission morphology in these QSOs."]
- limitation (authors): Large uncertainties on M* and f_gas from inclination and alpha_CO [6.5 Gas fraction and feedback from QSO …: "However, we caution that large uncertainties affect these measurements"]
- limitation (authors): Moment-map interpretation for marginally resolved J1549+1245 and J1639+2824 is uncertain [5 CO and [CII] kinematics: "the interpretation of moment maps is not straightforward and can be affected by large uncertainties"]
- not stated (card): Image size and cell size for each tclean run; Line-free channel selection beyond the |v|>500 km/s rule, and exact velocity/frequency range used for integrated line maps and spectra; Cleaning mask details, nsigma and rms used for the threshold, number of iterations; Which MOUS/execution blocks and pipeline versions were used per project; Aperture radius or exact extraction region for 1-D spectra; …

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

### 2025ApJ...989...83B: CO Emission and Absorption-line Survey of the M87 Nucleus Using Archival ALMA Imaging (2025; agn_and_quasars, nearby_galaxies; archival_reuse)
- question: Is there molecular gas in the inner kpc of M87 (CO emission from the circumnuclear disk, ionized-gas filaments and dusty clouds, or CO absorption against the nucleus), as probed by archival ALMA imaging?
- step 4: Subtract continuum in the uv plane and image CO cubes
  - method: uvcontsub with fitorder = 1 with three line-channel exclusion cases, then image continuum-subtracted data at native and coarser (~20-40 km/s) binning [MFS and Spectral Imaging: "Lastly, we subtracted the continuum for MSs containing CO transitions using the `uvcontsub` task (with `fitorder` = 1) with three distinct fitting regions."] [MFS and Spectral Imaging: "We imaged the continuum-subtracted data into spectral cubes at both the native frequency spacing and at more coarse binning ($\sim$20$-$40 km s$^{-1}$) to increase the signal-to-noise ratio (S/N)."]
  - software: CASA, uvcontsub, tclean
  - parameter: Case 1: exclude |v_LOS - v_sys| < 500 km/s (used for the main emission and absorption results) [MFS and Spectral Imaging: "we excluded channels corresponding to either $|\ensuremath{v_\mathrm{LOS}}- \ensuremath{v_\mathrm{sys}}| < 500$ km s$^{-1}$ to probe more standard velocity ranges for extragalactic gas"]
  - parameter: Case 3 (CO(1-0) only): exclude 100 < |v_LOS - v_sys| < 2200 km/s [MFS and Spectral Imaging: "In a third case for CO(1$-$0) only, we excluded the ranges $100 < |\ensuremath{v_\mathrm{LOS}}- \ensuremath{v_\mathrm{sys}}| < 2200$ km s$^{-1}$ to test for possible broad emission-line features"]
  - fitting: Linear (fitorder = 1) continuum fit per visibility [MFS and Spectral Imaging: "Lastly, we subtracted the continuum for MSs containing CO transitions using the `uvcontsub` task (with `fitorder` = 1) with three distinct fitting regions."]
  - validation: Cases 2 and 3 tested; they produce faint, likely spurious spectral deficits or excesses near redshifted CO [MFS and Spectral Imaging: "we explore the second and third `uvcontsub` cases that produce very faint (and likely spurious) spectral deficits or excesses near redshifted CO transitions"]
- step 10: Limit circumnuclear thermal dust from the continuum
  - method: Fit the X2c2 uniform-weighted MFS image with a nuclear source plus an offset Gaussian for N2 (imfit); sample noise with random 0.05 arcsec apertures on the residual image; convert the 1-sigma limit to M_dust and gas mass with a modified bl… [MFS imaging: "We fit the X2c2 MFS image (with uniform weighting; $\theta_\mathrm{maj} \times \theta_\mathrm{min} = 27 \times 21$ mas$^2$ or a FWHM $\sim 2$ pc) using the"] [Circumnuclear Dust: "by shifting a circular ($R = 0.05\ensuremath{''}$) aperture randomly to 100 continuum-free regions of the residual X2c2 MFS image to sample the noise"]
  - software: CASA, imfit, uvmodelfit
  - parameter: 1-sigma flux limit delta S_ext = 0.75 mJy [Circumnuclear Dust: "taking the standard deviation $\delta S_\mathrm{ext} = 0.75$ mJy as an effective 1$\sigma$ limit"]
  - assumption: Dust absorption coefficient at 850 micron (value not given) with beta = 2; T_dust = 25 K (or 100 K); dust-to-gas ratio ~0.015 [Circumnuclear Dust: "assumes a standard dust absorption coefficient $\kappa_\mathrm{850\,\mu m}$ and emissivity index $\beta = 2$"] [Circumnuclear Dust: "For $T_\mathrm{dust} = 25$ K and a standard dust-to-gas mass ratio of $\sim$0.015 (cite: Sandstrom2013)"]
  - fitting: Image-plane imfit with a nuclear point source and an offset elliptical Gaussian [MFS imaging: "with a nuclear source and an additional, offset elliptical Gaussian to characterize the N2 clump"]
  - validation: imfit residuals show no additional sources within the inner 50 mas [MFS imaging: "`imfit` residuals do not support any additional sources within the inner 50 mas"]
- result: Core and N2 integrated flux densities at 232.98 GHz (X2c2 imfit) = 1.220 Jy (core); 50.3 mJy (N2) ± not stated Jy; mJy [MFS imaging: "flux densities of 1.220 Jy and 50.3 mJy, respectively, at 232.98 GHz"]
- result: Dust mass upper limit (T_dust = 25 K) = < 1.1e4 ± upper limit Msun [Circumnuclear Dust: "this modified black body $M_\mathrm{dust} < 1.1\times 10^4$ $M_\odot$ would correspond to a total gas mass $M_\mathrm{gas} \lesssim 7.5\times10^5$ $M_\odot$"]
- limitation (authors): Bandpass calibration effects on tau_0 and tau_CO are not quantified [CO Absorption-line Properties: "However, we do not attempt to quantify here the bandpass calibration effects on"]
- limitation (authors): CO(3-2) and CO(2-1) opacities are less reliable than CO(1-0), so LTE reconciliation is not attempted [Temperature and Column Densities: "Unfortunately, neither $\tau_\mathrm{CO(3-2)}$ or $\overline{\tau}_\mathrm{CO(2-1)}$ values are as reliable as is $\overline{\tau}_\mathrm{CO(1-0)}$"]
- limitation (authors): Xa1 maximum recoverable scale cannot entirely rule out diffuse emission over larger regions [Channel Maps: "cannot entirely rule out diffuse emission spread out over a couple of the larger regions with $\sim$5$''$ extent"]
- not stated (card): CASA and pipeline versions used for each data set (only 'the appropriate pipeline version' is given); Briggs robust value for MFS maps, cell size, image size, niter/threshold, deconvolver and masks for tclean MFS and cube imaging; Which flux calibrator and which spws had setjy rescaling, and the exact rescale factors per spw; Self-calibration details: refant, solint sequence, number of loops, whi…

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

### 2026A&A...705A.197Z: The ALMA survey to Resolve exoKuiper belt Substructures (ARKS): III. The vertical structure of debris disks (2026; debris_disks; large_program_or_survey)
- question: Uniformly extract the vertical dust distributions of highly inclined, well-resolved ARKS debris disks.
- step 2: Generate synthetic continuum visibilities
  - method: Integrate radiative transfer with a Planck source function; apply primary beam; sample model visibilities at observed spatial frequencies. [Radiative transfer: "We approximated the source function with the Planck function:"] [Radiative transfer: "we used `galario` to obtain synthetic visibilities sampled at the same spatial frequencies as the data (cite: Galario_2018)."]
  - software: galario
  - parameter: Gaussian primary beam approximation; mosaic treatment for HD 39060. [Radiative transfer: "After generating the model disk image and multiplying it by a Gaussian approximation of the primary beam,"] [Radiative transfer: "The archival Band 6 observations of HD 39060 are mosaicked. For this source, we apply a primary beam correction at each location in the mosaic field."]
  - parameter: Stellar flux added in visibility domain at disk center; dRA and dDec free. [Radiative transfer: "The stellar flux is added to the image in the visibility domain at the disk center, which is set by free parameters that enable offsets in right ascension (dRA) and declination (dDec) from the phase center."]
  - assumption: Dust opacity 1.9 cm² g⁻¹ at 0.89 mm; 1.3 cm² g⁻¹ at 1.3 mm. [Radiative transfer: "We adopted $\kappa_\nu=$1.9 cm$^{2}$ g$^{-1}$ at 0.89 mm and $\kappa_\nu=$1.3 cm$^{2}$ g$^{-1}$ at 1.3 mm as in (cite: Marino_2026)"]
  - assumption: Grain-size slope -3.5; mass composition 70% astrosilicates, 15% crystalline water ice, 15% amorphous carbon. [Radiative transfer: "who assumed a power law grain size distribution with a slope of -3.5, and a composition of astrosilicates (70%), crystalline water ice (15%), and amorphous carbon (15%) by mass (cite: Draine_2003; Li_1998)."]
- step 3: Fit parametric disk models
  - method: Fit observed visibilities using affine-invariant MCMC. [Model parameters: "We used the affine-invariant MCMC implementation in `emcee` to obtain best-fit model parameters and their posterior distributions (cite: emcee_2013)."]
  - software: emcee, galario.double.chi2Image()
  - parameter: 64 walkers; at least 10^5 post-convergence samples, approximately 1500 steps per walker. [Model parameters: "For each model, we initialized the MCMC with a 64 walker ensemble (more than double the number of free parameters for each model)."] [Model parameters: "we required at least $10^{5}$ samples after convergence, which corresponds to approximately $1500$ steps for each of the 64 walkers."]
  - parameter: Fit inclination, PA, surface density normalization, stellar flux, dRA, dDec and radial/vertical form parameters. [Model parameters: "the free parameters included the disk inclination ($i$), position angle (PA), surface density normalization ($\Sigma_{\mathrm{c}}$), stellar flux ($F_{\star}$) at the observing wavelength"] [Model parameters: "and offsets from the phase center (dRA and dDec)."]
  - parameter: AU Mic: three separate stellar flux values. [Model parameters: "AU Mic exhibited significant variations in the stellar flux across the three observations used here. Thus, we fit three separate stellar flux values as in (cite: Daley_2019)."]
  - fitting: Log-likelihood proportional to -0.5 chi²; weighted squared real and imaginary visibility residuals. Priors not stated. [Model parameters: "The log-likelihood is proportional to $-0.5 \chi^2$, where the model and data are compared using a $\chi^2$ metric"] [Model parameters: "\chi^2=\sum_{j=1}^N w_j \left[\left(\operatorname{ReV}_{{\rm obs}\, j}-\operatorname{ReV}_{\bmod j}\right)^2+\left(\operatorname{ImV}_{{\rm obs}\, j}-\operatorname{ImV}_{\bmod j}\right)^2\right],"]
  - validation: Visual walker and likelihood inspection; discard burn-in and walkers at least 5 sigma below maximum log-likelihood. [Model parameters: "Convergence was determined by visually inspecting the evolution of all walkers in both parameter space and log-likelihood space."] [Model parameters: "We identified convergence once the log-likelihood stabilized and the walkers fluctuated around consistent parameter ranges, discarding earlier steps as burn-in."]
- step 5: Infer vertical aspect ratios with frank
  - method: Fit radial visibility profiles with a Fourier-Bessel series over a height grid; infer height likelihoods. [frank: "`frank` is an open-source code which reconstructs the 1D (azimuthally averaged) radial intensity profile of a disk by fitting the visibilities with a Fourier-Bessel series (cite: Jennings_2020)."] [frank: "we repeated the radial profile fit over a range of scale height assumptions, computing the $\chi^2$ value for each height and estimating its likelihood as $\exp(-\chi^2/2)$."]
  - software: frank, arksia
  - parameter: Fix PA, inclination and offsets to Marino_2026. [frank: "For all fits, we adopt the position angle, inclination, and RA and declination offsets presented in (cite: Marino_2026)."]
  - parameter: Narrow height grid around probability mass; quadratic interpolation. [frank: "Starting from a wide range in $h_{\sigma}$, we narrowed the height grid to more densely sample the region of $h_{\sigma}$ in which the bulk of the probability mass is centered."] [frank: "The sample points were then interpolated quadratically to obtain a finer probability density distribution (PDF)."]
  - assumption: Vertically Gaussian; H_sigma proportional to radius. [frank: "We assumed the disk to be vertically Gaussian, with the scale height $H_{\sigma}$ proportional to the radius, thereby defining an aspect ratio of $h_{\sigma} = H_{\sigma}(r) / r$."]
  - fitting: Median and 16th/84th percentiles for peaked PDFs; 99.7th-percentile upper limit when probability remains nonzero at zero height but vanishes at large height. [frank: "the best-fit height was estimated with the median and the uncertainties with the 16th and 84th percentiles."] [frank: "In such cases, an upper limit was estimated with the 99.7th percentile if the PDF approaches 0 toward large values of $h_{\sigma}$."]
  - validation: Inspect height PDFs and compare with parametric and rave estimates. [frank: "the PDFs are shown in Fig [10](#fig:frank_h)."] [abstract: "The results obtained by nonparametric modeling are generally consistent with the parametric modeling results."]
- result: HD 197481 frank h_HWHM = 0.023 ± +0.002/-0.002 dimensionless [HD 197481 (AU Mic): "`frank` and `rave` find similar aspect ratios: $h_{\rm HWHM}=0.023^{+0.002}_{-0.002}$ and $h_{\rm HWHM}=0.026^{+0.005}_{-0.006}$, respectively."]
- result: HD 10647 frank h_HWHM upper limit = <0.008 ± not stated dimensionless [HD 10647: "However, the upper limit derived from the `frank` fit is much smaller, $h_{\rm HWHM}<0.008$."]
- limitation (authors): Axisymmetric, midplane-peaked models can obscure asymmetric structures and inflate heights in warped disks. [Limitations: "First, we consider only axisymmetric disks with vertical distributions that peak at the disk midplane."]
- limitation (authors): Constant aspect ratio excludes radial variation supported by some other studies. [Limitations: "Second, in this work we assume that aspect ratio is constant with radius."]
- limitation (authors): Chosen radial and vertical functions may bias heights or fail to capture source morphology. [Limitations: "A poor choice of radial profile can result in biased vertical results, (and vice versa)."]
- not stated (card): Per-target mapping of project codes, execution blocks and corrected visibility files.; Correction factors and procedures for visibility weights, phase centers and flux offsets inherited from Marino_2026.; Calibration software versions, calibrators, flux uncertainty and any self-calibration procedure.; Continuum spectral windows, averaging, flagged channels and any line-contamination exclusion.; I…

### 2026ApJ..1005...94N: Dynamical Evidence for a Billion Solar-mass Black Hole in Galaxy NGC 4061 from ALMA <SUP>12</SUP>CO(2─1) Kinematics (2026; nearby_galaxies, agn_and_quasars; observational_alma_primary)
- question: What is the dynamical mass of the supermassive black hole in the massive early-type galaxy NGC 4061, and does it resolve the discrepancy between previous indirect estimates based on conflicting velocity dispersion measurements?
- step 1: Calibrate, combine, and image 1.3 mm continuum and 12CO(2-1) line cube
  - method: Calibrate Cycle 6 and Cycle 7 execution blocks with the ALMA Science Pipeline, combine the three measurement sets with CASA concat using visweightscale, image the 1.3 mm continuum with tclean (MFS) and fit source with imfit, subtract conti… [2.1 Data Reduction: "We combined the visibility data from all three MS into a combined and calibrated MS using the `concat` task in CASA."] [2.2 Creating the Combined 1.3 mm Contin…: "We produced the combined continuum image at 1.3mm using the CASA `tclean` task in multifrequency synthesis mode (cite: Rau11), combining the continuum SPWs with line-free channels from the targeted SPWs of all three MS."]
  - software: CASA, ALMA Science Pipeline, concat, tclean, imfit, uvcontsub
  - parameter: visweightscale = 0.6 (2019.1.00036.S) and 0.2 for each of the two 2018.1.00397.S tracks [2.1 Data Reduction: "The optimal visibility–weight scaling factors applied in the `visweightscale` mode were 0.6 for the `uid_A002_Xea90c0_X334e` MS (2019.1.00036.S), and 0.2 for each of the `uid_A002_Xe03886_X7606` and `uid_A002_Xe03886_Xd75e` MSs (2018.1.00397.S)."]
  - parameter: Briggs robust = 0.5, pixel scale = 0.04'', image size = 512 x 512 pixels^2, channel width = 10 km s^-1, clean threshold = 1.5 sigma_RMS [2.3 Creating the Combined-$^{12}$CO(2$-…: "The resulting cube has dimensions of 512 $\times$ 512 pixels$^2$ with a pixel scale of $0.04\ensuremath{''}$, which adequately samples the synthesized beam while maintaining a manageable file size. We used a channel width of 10 km s$^{-1}$—an optimal choice for SMBH dynamical modeling (cite: Davis14; Nguyen21; Ngo2025…"] [2.3 Creating the Combined-$^{12}$CO(2$-…: "The continuum-subtracted dirty cube was cleaned down to a threshold of 1.5 times the root-mean-squared (RMS) noise level ($\sigma_{\rm RMS}$; measured from line-free channels)."]
  - assumption: Rest frequency of 12CO(2-1) = 230.538 GHz [2.3 Creating the Combined-$^{12}$CO(2$-…: "The velocity axis was referenced to the rest frequency of 230.538 GHz."]
  - fitting: 2D Gaussian fit to the continuum source using CASA imfit; linear power-law continuum fit in uvcontsub [2.2 Creating the Combined 1.3 mm Contin…: "A two-dimensional (2D) Gaussian fit using the `imfit` routine in CASA confirms the source is spatially resolved."] [2.3 Creating the Combined-$^{12}$CO(2$-…: "The continuum was modeled with a linear power-law function and subtracted from the combined and calibrated visibilities in the *uv* plane to isolate the $^{12}$CO(2$-$1) line emission."]
  - validation: Continuum flux density checked against the ~10% ALMA flux calibration uncertainty [2.2 Creating the Combined 1.3 mm Contin…: "with an integrated flux density of $3.48 \pm 0.18$ mJy, consistent within the $\approx$10% ALMA flux calibration uncertainty."]
- result: 1.3 mm continuum integrated flux density = 3.48 ± +/-0.18 mJy [Table 1 (continuum): "| Integrated flux (mJy) | $3.48\pm0.18$ |"]
- result: 1.3 mm continuum deconvolved source size = 0.26 x 0.22 ± +/-0.03 x +/-0.03 arcsec^2 [Table 1 (continuum): "| Deconvolved size (arcsec$^2$) | $(0.26\pm0.03)\times(0.22\pm0.03)$ |"]
- limitation (authors): The wide range of published distances to NGC 4061 (68–112 Mpc in NED) introduces a ~37% systematic uncertainty in M_BH, dominating the total error budget. [4.5.1 Distances: "Since the inferred $M_{\rm BH}$ scales linearly with the assumed distance ($M_{\rm BH} \propto D$), the wide range of distance estimates for NGC 4061 (68–112 Mpc; NED)—primarily based on optical and near-infrared light curves of the Type Ia supernova SN 2008bf—constitutes the dominant source of uncertainty in our $M_{…"]
- limitation (authors): Parameter degeneracies exist between M_BH and M/L_F814W, between y_cen and v_off (due to the beam size relative to the continuum peak), between inclination i and M/L_F814W, and between flux normalization f and sigma_gas. [4.4 Results: "While the other model parameters are well constrained, a clear anti-correlation between $M_{\rm BH}$ and $M/L_{\rm F814W}$ is evident (see both Figure 9 and Figure 10)."]
- limitation (authors): Adopting the HST F555W band instead of F814W for the stellar mass model introduces an additional ~20% uncertainty in M_BH due to stronger dust attenuation in F555W. [4.5.7 Using the Alternative F555W MGE S…: "Overall, adopting the F555W-based stellar mass model introduces an additional uncertainty of approximately 20% in the inferred SMBH mass for NGC 4061, likely reflecting the greater sensitivity of the F555W band to dust attenuation compared to the F814W band."]
- not stated (card): Exact frequency/channel ranges identified as line-free for continuum imaging and uvcontsub; Self-calibration details (Section 2.3 refers to the 'final self-calibrated, cleaned cube', but no self-calibration procedure, solution intervals, or calibration modes are described); Resolution of the discrepancy in reported continuum RMS noise (Section 2.2 text states 120 uJy beam^-1, while Table 1 lists …

### 2020MNRAS.498.1319M: Insights into the planetary dynamics of HD 206893 with ALMA (2020; debris_disks, exoplanets; observational_alma_primary)
- question: What is the radial structure of the HD 206893 debris disc (is there a gap, asymmetry, CO gas, dust around the brown dwarf B), and what does it imply for the dynamics of the companions?
- step 6: Fit parametric gap disc model to visibilities
  - method: Two-power-law surface density with Gaussian gap, radiative transfer with RADMC-3D, MCMC fit in visibility space [3 Parametric axisymmetric disc model: "we fit a parametric disc model with a gap as in (cite: Marino2018hd107; Marino2019), combining radiative transfer simulations (cite: radmc3d) and an MCMC fitting procedure in the visibility space."]
  - software: RADMC-3D
  - parameter: Gap depth fixed to 1 [3 Parametric axisymmetric disc model: "here we fixed the gap depth to 1 (i.e. the surface density is zero at $r_\mathrm{g}$)"]
  - parameter: Vertical extent fixed to 5% of radius, uniform vertical mass distribution [3 Parametric axisymmetric disc model: "We thus choose to fix the vertical extent of the disc to 5% of the radius and use a uniform vertical mass distribution"]
  - parameter: r_min lower limit of 14 au; outer edge fixed at 250 au [3 Parametric axisymmetric disc model: "we impose a lower limit for $r_{\min}$ of 14 au"] [3 Parametric axisymmetric disc model: "we set a fixed outer edge of 250 au"]
  - parameter: Free parameters include disc inclination and PA, phase centre offsets, and position, size (2D Gaussian) and flux of a background SMG ~11.5'' to the SW; spectral index alpha free and uniform [3 Parametric axisymmetric disc model: "we also fit the disc inclination $i$ and position angle PA, and nuisance parameters such as phase center offsets, and the position, size (modelled as a 2D gaussian) and flux of a SMG"] [3 Parametric axisymmetric disc model: "which we leave as a free parameter that is uniform across the disc"]
  - parameter: Reported values are posterior medians with 16th and 84th percentile uncertainties [Table 1: "The quoted values correspond to the median, with uncertainties based on the 16th and 84th percentiles of the marginalised distributions."]
  - assumption: Dust mass counts only grains smaller than 1 cm, set by assumed opacities [3 Parametric axisymmetric disc model: "Note that this dust mass only includes the mass in grains smaller than 1 cm, which is set by the assumed dust opacities (cite: Marino2019)."]
  - assumption: Star modelled with Teff = 6500 K and R = 1.3 Rsun template spectrum [3 Parametric axisymmetric disc model: "The star is modelled with a template spectrum corresponding to an effective temperature of 6500 K and a radius of 1.3 $R_\odot$"]
  - fitting: MCMC in visibility space; sampler, priors and likelihood not stated [3 Parametric axisymmetric disc model: "an MCMC fitting procedure in the visibility space"]
  - validation: Residual maps show no residuals above 3 sigma within 200 au; model without a gap fails to reproduce visibility wiggles beyond 50 klambda [3.1 Results: "We do not find any residuals stronger than $3\sigma$ within 200 au."] [3.1 Results: "The model without a gap fails to reproduce the amplitude of the wiggles beyond 50 k$\lambda$."]
- result: Total dust mass M_d = 0.031 ± 0.002 Earth masses [Table 1: "$0.031\pm0.002$ | total dust mass"]
- result: Disc inner radius r_min = 28 ± +5/-8 au [Table 1: "$28_{-8}^{+5}$ | disc inner radius"]
- result: Disc peak radius r_c = 114 ± +7/-5 au [3.1 Results: "we find that the disc dust density peaks at $r_\mathrm{c}=114^{+7}_{-5}$ au"]
- result: Inner surface density slope gamma_1 = 0.8 ± +-0.4 dimensionless [3.1 Results: "the surface density must increase moderately as $r^{0.8\pm0.4}$"]
- result: Outer surface density slope gamma_2 = -3.9 ± +0.5/-0.6 dimensionless [3.1 Results: "Exterior to that the disc surface density declines steeply as $r^{-3.9\pm0.5}$."]
- result: Gap centre radius r_g = 74 ± 3 au [3.1 Results: "we find that the gap center is well constrained to $74\pm3$ au"]
- result: Gap width w_g (FWHM) = 27 ± 5 au [3.1 Results: "The gap width is constrained to $27\pm5$ au."]
- result: Disc inclination from face-on = 40 ± 3 deg [3.1 Results: "The disc orientation is well constrained with $i=40\pm3\ensuremath{^\circ}$ and PA$=61\pm4\ensuremath{^\circ}$."]
- result: Disc position angle = 61 ± 4 deg [3.1 Results: "The disc orientation is well constrained with $i=40\pm3\ensuremath{^\circ}$ and PA$=61\pm4\ensuremath{^\circ}$."]
- result: Disc spectral index alpha (Table 1) = 2.54 ± 0.17 dimensionless [Table 1: "$2.54\pm0.17$ | disc spectral index"]
- result: Disc spectral index alpha (text value, differs slightly from Table 1) = 2.53 ± 0.16 dimensionless [3.1 Results: "The disc spectral index is found to be $2.53\pm0.16$"]
- result: Background SMG integrated flux at 0.88 mm = 1.5 ± not stated mJy [3.1 Results: "has an integrated flux of 1.5 mJy at 0.88 mm and 0.24 mJy at 1.3 mm"]
- limitation (authors): Planet mass assumes the gap is empty at its centre; a shallower, broader gap would change the inferred width and mass [3.1 Results: "A caveat in this interpretation is that we have assumed the gap is empty at its center."]
- limitation (authors): Frankenstein profiles lack a primary beam correction [2.1.1 Dust radial structure: "no primary beam correction is taken into account"]
- limitation (authors): Lower S/N makes gap width and depth comparison with other discs difficult [5.4 Are gaps common among exoKuiper bel…: "Given the lower S/N in HD 206893 observations, it is hard to compare the gap width and depth with the other two."]
- not stated (card): tclean parameters other than weighting and taper: deconvolver, cell size, image size, mask, threshold, niter; How the ACA and 12m data were combined for imaging and for the visibility fit (joint tclean or separate datasets); Which spectral windows were used for the continuum images, and whether the line window was flagged; Flux calibrator and calibrator-derived flux scale for each execution block…

### 2015ApJ...812...43B: HerMES: ALMA Imaging of Herschel-selected Dusty Star-forming Galaxies (2015; high_z_galaxies; observational_alma_primary)
- question: How does gravitational lensing and multiplicity affect the properties of the brightest Herschel-selected DSFGs, and what do the lens models imply for the bright end of the intrinsic DSFG number counts?
- step 3: Visibility-plane lens modeling
  - method: uvmcmcfit: elliptical Gaussian sources, SIE lenses, ray tracing, compare model visibilities to data [3.1 Model Fitting Methodology: "Sources are assumed to be elliptical Gaussians that are parameterized by the following six free parameters"]
  - software: uvmcmcfit, emcee
  - parameter: 512 walkers; burn-in 500-1000 iterations; final 10 iterations [3.1 Model Fitting Methodology: "We employ a “burn-in” phase with 512 walkers and 500-1000 iterations"]
  - parameter: uniform priors; theta_E 0.1-6 arcsec; q_lens>0.3; q_s>0.2; r_s 0.01-1.5 arcsec [3.1 Model Fitting Methodology: "The axial ratios of the lenses and sources are restricted to be $q_{\rm lens} > 0.3$ and $q_{\rm s} > 0.2$."]
  - assumption: Additional lenses at same redshift as primary; maximal-lensing Einstein radii fixed for weakly lensed systems [3.1 Model Fitting Methodology: "We assume secondary, tertiary, etc., lenses are located at the same redshift as the primary lens."]
  - fitting: emcee affine-invariant ensemble MCMC with Gaussian likelihood in visibility plane [3.1 Model Fitting Methodology: "We use emcee (cite: Foreman-Mackey:2013yq) to sample the posterior probability density function (PDF) of our model parameters."]
  - validation: Bolton ray tracing tested against Gravlens; residual maps inspected [3.1 Model Fitting Methodology: "tests of the Bolton ray-tracing routine indicate it produces results consistent with Gravlens"]
- result: Brightest intrinsic source S870 (HADFS11.0) = 17.5 ± 0.4 mJy [4.1 De-lensing: "with an intrinsic flux density of $S_{870} = 17.5 \pm 0.4\,$mJy"]
- limitation (authors): Resolution may cause over-predicted sizes and under-predicted magnifications; optically faint lenses may be missed [3.1 Model Fitting Methodology: "in some cases the lens models may moderately over-predict the intrinsic sizes of the lensed galaxies and hence under-predict the magnification factors"]
- not stated (card): Line-free channels/continuum definition and clean thresholds, cell and image size; Which targets received selfcal and solint; Exact MCMC convergence criteria; final phase of only 10 iterations; Lens position/Einstein radius fixings are given per object but the SMA data and fits for the combined sample are not tabulated here; Details of logistic regression and running-average smoothing parameters;…

### 2022Icar..37214722L: Pluto's atmosphere observations with ALMA: Spatially-resolved maps of CO and HCN emission and first detection of HNC (2022; solar_system, astrochemistry; observational_alma_primary)
- question: Obtain spatially-resolved measurements of CO(3-2) and HCN(4-3) in Pluto's atmosphere to investigate vertical and horizontal variations in temperature and composition, and search for new atmospheric compounds, primarily hydrogen isocyanide …
- step 1: Calibrate visibilities, perform phase self-calibration, and fix the absolute flux scale
  - method: Calibrate visibilities and apply velocity corrections using the CASA pipeline. Image continuum spectral windows, perform phase self-calibration in AIPS, apply solutions to line spectral windows, fit continuum visibilities, and rescale flux… [Observations and data reduction: "This included calibration and velocity corrections on the spectral visibilities, performed with the CASA pipeline (Muders et al., 2014)."] [Observations and data reduction: "For all four observations, we then imaged the continuum spectral windows (combining the two, for the CO/HCN setup), and used that image to perform self-calibration to correct for atmospheric phase fluctuations, also applying the determined solutions to the spectral line spectral windows."]
  - software: CASA, AIPS
  - parameter: Continuum flux density set to 17.5 mJy at CO(3-2), 18.3 mJy at HCN(4-3), and 11.1 mJy at HNC(3-2) [Observations and data reduction: "This brightness temperature results in a continuum flux density level of 17.5 mJy at CO(3-2), 18.3 mJy at HCN(4-3), and 11.1 mJy at HNC(3-2)."]
  - assumption: Pluto continuum brightness temperature is constant at 33 K [Observations and data reduction: "Because of this, we fixed the flux density scale such that the brightness temperature of Pluto was 33 K, as was found in our 2015 observations (Paper I; Butler et al. 2020)."]
  - fitting: Visibility fitting of continuum spectral windows in AIPS [Observations and data reduction: "We then fitted the self-calibrated visibilities to determine the continuum brightness temperature of Pluto and Charon"]
  - validation: Estimated expected thermal emission decrease from heliocentric distance change over 2015-2017 is only 0.7% [Observations and data reduction: "While the continuum thermal emission of Pluto and Charon may vary with the system’s heliocentric distance $r_h$, a simple scaling of temperatures as $r^{-0.5}_h$ would lead to an expected temperature decrease of only 0.7%"]
- step 2: Extract zero-spacing (total flux density) CO and HCN spectra via visibility fitting and generate image cubes
  - method: Fit spectral line visibilities per channel over u-v range <= 1000 klambda (excluding Charon, forcing Pluto at phase center) to derive zero-spacing spectra for individual dates and combined data. Produce image cubes for combined CO/HCN data… [Observations and data reduction: "For the CO/HCN setup observations, we next fitted the visibilities in the spectral line windows on a per-channel basis, in order to determine the best value of the total flux density (a.k.a. zero spacing flux) as a function of channel."] [Observations and data reduction: "For this fitting, we excluded the Charon contribution and fitted the visibilities over a maximum u-v range of 1000 k$\lambda$, forcing Pluto to be at phase center."]
  - software: AIPS, GILDAS
  - parameter: Maximum u-v range = 1000 klambda; Pluto continuum disk = 0.1009" with limb darkening exponent 0.1 [Observations and data reduction: "fitted the visibilities over a maximum u-v range of 1000 k$\lambda$, forcing Pluto to be at phase center. Pluto’s continuum was described as emission from a 0.1009" disk with some limb darkening (0.1 exponent)."]
  - parameter: Prescribed CO emission size = 1.01, 1.05, 1.40 x Pluto diameter at 5, 1, 0 MHz from line center; HCN emission size = 1.00, 1.40, 1.78 x Pluto diameter at 0.6, 0.5, 0.0 MHz [Observations and data reduction: "For the CO spectral window, the specified emission size was 1.01, 1.05, and 1.40 times the diameter of Pluto, respectively, at 5 MHz, 1 MHz, and 0 MHz from line center (those values were interpolated for intermediate frequency offsets). For HCN, the specified emission size was 1.00, 1.40, and 1.78 times the diameter o…"]
  - parameter: Pixel size = 0.01" (CO/HCN cube), 0.1" (HNC cube); spectral binning factor = 4 (HNC setup) [Observations and data reduction: "The image cube for the CO/HCN data was made with $0.01\mbox{$^{\prime\prime}$}$ pixels, in order to subsample the synthesized beam sufficiently"] [Observations and data reduction: "for the HNC setup, which did not spatially resolve Pluto (resolution $\sim$0.62$\mbox{$^{\prime\prime}$}$ x $\sim$0.45$\mbox{$^{\prime\prime}$}$), the image cube was made with $0.1\mbox{$^{\prime\prime}$}$ pixels, and the spectra were simply extracted at image center. The spectral channels were binned by a factor 4 to…"]
  - assumption: Channel-dependent emission sizes prescribed from image cube modeling [Observations and data reduction: "For the lines, we prescribed channel-dependent values of the emission size based on modeling of the image cube data (see below)."]
  - fitting: Per-channel visibility fitting in AIPS and GILDAS [Observations and data reduction: "This was done in AIPS, but was also repeated in GILDAS, leaving the fitted diameter as a free parameter; this yielded consistent results."]
  - validation: Repeated visibility fitting in GILDAS with diameter as a free parameter and compared spectra across the three individual observing dates [Observations and data reduction: "This was done in AIPS, but was also repeated in GILDAS, leaving the fitted diameter as a free parameter; this yielded consistent results."] [Observations and data reduction: "Within noise level, the CO and HCN lines are the same for the three individual dates"]
- limitation (authors): The retrieved latitudinal temperature contrast (7 +/- 3.5 K) is only ~2-sigma significant, improvement over the a priori fit (Delta chi^2) is modest, and temperatures retrieved near the polar limb 'beyond' the pole are somewhat higher than… [Temperature / CO retrievals: "Within these error bars, the temperature latitude variations are only $\sim$2-$\sigma$ significant"]
- limitation (authors): The 2015 disk-averaged and 2017 disk-resolved datasets do not provide fully consistent results on the HCN vertical distribution, especially if a large lower-atmosphere HCN component is included. [Disk-averaged HCN profile: "A general result is that while the increase with altitude of HCN, inferred from the 2015 spectrum shape, is confirmed from the HCN emission radial distribution in the 2017 data, the two datasets do not appear to provide fully consistent results on the HCN vertical distribution."]
- limitation (authors): Models of spatial variations in HCN underpredict the observed HCN line areas and contrasts at/beyond the low-latitude limb (reduced chi^2 up to ~1.4), and a satisfactory physical explanation for enhanced low-latitude HCN is lacking. [Search for HCN spatial variations: "in fact the HCN line areas and contrasts at/beyond the low-latitude (sky North-East) limbs are somewhat underpredicted by the model (this can be seen e.g. in Fig. 10, at beam positions near (RA, DEC) = (0.04", 0.04"), and the reduced $\chi^2$ between modelled and observed spectra reaches values of $\sim$1.4"]
- not stated (card): Exact CASA and pipeline versions used for initial visibility calibration; AIPS and GILDAS software versions and specific tasks used for self-calibration, visibility fitting, deconvolution, and imaging; Self-calibration solution interval (solint) and S/N threshold; Deconvolution algorithm, visibility weighting scheme (e.g., Briggs robust parameter), and cleaning stopping criteria; Specific spectro…

### 2024A&A...687A.308S: Constraining the stellar masses and origin of the protostellar VLA 1623 system (2024; star_formation; observational_alma_primary)
- question: Constrain the stellar masses of the VLA 1623 components by Keplerian disk modelling of C17O (3-2), and use them to test the origin of the system (ejection, chance alignment, in situ formation) and its stability
- step 4: Fit Keplerian disk models to C17O in the uv plane
  - method: pdspy 2D axisymmetric disk models, RADMC-3D ray tracing, Fourier transformed with galario, fit separately to VLA 1623A, B and W in the uv plane [Modelling: "which fits Keplerian rotating disk models to spectral line datasets directly in the $uv$ plane (cite: Sheehan19)"] [Modelling: "`pdspy` then uses the radiative transfer modelling code `RADMC-3D` and ray tracing to generate synthetic channel maps of the model disk"]
  - software: pdspy, RADMC-3D, galario, dynesty
  - parameter: Free parameters include M*, M_disk, R_disk, gamma, T0, q, a_turb, i, p.a., v_sys, x0, y0 (R_in free for A, fixed at 0.1 au for B and W) [Modelling: "The model parameter values as well as the source system velocity, $v_{sys}$, and location in the field ($x_0$, $y_0$) are optimized to the observations."] [Modelling: "For VLA 1623B and VLA 1623W, we fixed $R_{in}$, the inner radius where the disk is truncated, to 0.1 au."]
  - parameter: Strict priors on source position so each source is fit separately [Modelling: "we provided `pdspy` with relatively strict priors on the location of the source"]
  - parameter: Channel cuts: exclude 3.25-5.5 km/s for A and -2.5 to 6.75 km/s for B [Modelling: "For the channel restrictions, we excluded velocities between 3.25 and 5.5 km s$^{-1}$ from the fit to A and between -2.5 and 6.75 km s$^{-1}$ from the fit to B."]
  - parameter: uv cuts: exclude uv < 100 klambda for B and < 200 klambda for W [Modelling: "For the $uv$ restriction, we excluded baselines with $uv <100$ k$\lambda$ ($\gtrsim2\ensuremath{''}$) for B and $uv <200$ k$\lambda$ ($\gtrsim1\ensuremath{''}$) for W."]
  - assumption: Surface density follows a power law; temperature power law in radius, vertically isothermal [Modelling: "The surface density is described by a power-law function"] [Modelling: "and that the disk is vertically isothermal"]
  - assumption: Constant C17O abundance (1/2240 of CO), CO abundance 1e-4 relative to H2, no dust in the line model [Modelling: "assuming a constant C$^{17}$O abundance with a factor of 1/2240 relative to CO and a fixed CO abundance of $10^{-4}$ relative to molecular hydrogen (cite: Czekala15)"]
  - assumption: C17O emission solely traces rotationally supported disks; envelope and streamer contributions negligible [Results: "we assumed that the C$^{17}$O (3 – 2) emission solely traces the rotationally supported disks and that any potential contributions from the surrounding envelope or gas streamers are negligible"]
  - fitting: dynesty nested sampling; best fit is the maximum-likelihood model from the posterior; priors beyond source position not stated [Modelling: "`dynesty` uses nested sampling to integrate the likelihood function and calculate the Bayesian evidence and the posteriors for each parameter."] [Modelling: "The best-fit values are determined from the maximum likelihood models from the posterior"]
  - validation: Residual channel maps show little emission above 5 sigma near the target disk; PV diagrams compared with Keplerian curves [Modelling: "We find that the models fit the data well, with little or no contours above the $5\sigma$ level appearing in the residual channel maps associated with the target disk."]
- result: Stellar mass VLA 1623A (Aa+Ab combined) = 0.27 ± +0.03/-0.03 Msun [Stellar masses: "a combined stellar mass of $M_\star = 0.27 \pm 0.03$ for VLA 1623A"]
- result: Stellar mass VLA 1623B = 1.9 ± +0.3/-0.2 Msun [Stellar masses: "$M_\star = 1.9^{+0.3}_{-0.2}$ M$_{\odot}$ for VLA 1623B"]
- result: Stellar mass VLA 1623W = 0.64 ± +0.06/-0.06 Msun [Stellar masses: "$M_\star = 0.64 \pm 0.06$ M$_{\odot}$ for VLA 1623W"]
- result: Disk radius R_disk of VLA 1623A / B / W = 316 / 43 / 108 ± +32/-32 ; +5/-5 ; +11/-11 au [Table 1: "$R_{disk}$ (au) | $316^{+32}_{-32}$ | $43^{+5}_{-5}$ | $108^{+11}_{-11}$"]
- result: Inclination of VLA 1623A / B / W = 58.9 / 91 / 74.8 ± +0.6/-0.3 ; +16/-2 ; +0.5/-0.5 deg [Table 1: "$i$ ($^{\circ}$) | $58.9^{+0.6}_{-0.3}$ | $91^{+16}_{-2}$ | $74.8^{+0.5}_{-0.5}$"]
- result: Disk mass M_disk (gas+dust) of VLA 1623A / B / W = 54 / >1 / 1.7 (x1e-3) ± +5/-5 ; not stated ; +0.2/-0.2 1e-3 Msun [Table 1: "$M_{disk}$ ($10^{-3}$ M$_{\odot}$) | $54^{+5}_{-5}$ | $>1$ | $1.7^{+0.2}_{-0.2}$"]
- limitation (authors): Disk parameters other than stellar mass are poorly constrained because strict velocity and uv cuts were needed [Modelling: "We caution against over-interpreting the value of these disk parameters given that we had to impose strict velocity and $uv$ limits."]
- limitation (authors): Additional systematic effects such as the model choice may give larger errors than quoted [Modelling: "There may be additional systematic effects such as the choice of model that lead to larger errors on the measured values than those presented here (cite: Premnath20)."]
- limitation (authors): Emission assumed to trace only rotating disks; infall and streamer contributions assumed negligible [Results: "we assumed that the C$^{17}$O (3 – 2) emission solely traces the rotationally supported disks and that any potential contributions from the surrounding envelope or gas streamers are negligible"]
- not stated (card): CASA version and whether the standard pipeline or manual calibration was used; Which channels are line-free for self-calibration and continuum subtraction; tclean settings: image size, cell size, deconvolver, masks, thresholds, niter, number of channels per line cube; Gain-solution details for self-calibration (combine, spw mapping, minimum SNR); Thresholds in Moment 0 and dust continuum used to …

### 2020ApJ...888...44C: Unveiling Sizes of Compact AGN Hosts with ALMA (2020; nearby_galaxies, agn_and_quasars, high_z_galaxies; observational_alma_primary)
- question: Are obscured AGN host galaxies more compact in rest-frame FIR (ALMA 1 mm) and optical (HST/F814W) size than non-AGN star-forming galaxies at similar redshift and stellar mass?
- step 1: Image own ALMA data and stack non-detections
  - method: TCLEAN imaging; median stack in image plane of nine undetected sources; check with uv-plane STACKER [2.1 Our ALMA Observations: "we stacked their imaging and computed the median values in each pixel to create a stacked imaging"]
  - software: CASA, STACKER
  - parameter: Briggs robust 0.5; natural weighting for stack [Footnote 2: "we used natural weighting with `TCLEAN` in CASA."]
  - validation: Image-plane and uv-plane stack peak fluxes agree (0.09 vs 0.08 mJy) [2.1 Our ALMA Observations: "which is consistent with the stacking results from the image plane."]
- step 2: Test size-recovery vs resolution to select archival sample
  - method: Simulate Gaussian sources with SIMOBSERVE/SIMANALYZE and fit with UVMODELFIT; smooth images with IMSMOOTH [2.2 Complementary Sample from the Archi…: "Nevertheless, the measured size differences are within 20% of the simulated galaxies if the resolution is around $0\ensuremath{''}.1$ to $0\ensuremath{''}.4$."]
  - software: CASA SIMOBSERVE, SIMANALYZE, UVMODELFIT, IMSMOOTH
  - parameter: sizes 0.10-0.40 arcsec, fluxes 0.25-2.00 mJy, 300 s [2.2 Complementary Sample from the Archi…: "as well as fluxes in a range of 0.25 mJy to 2.00 mJy (signal-to-noise ratios in a range of 4 to 50 with 300 seconds total time)"]
  - validation: resolution range 0.1-0.4 arcsec adopted [Footnote 3: "we decided to have a range of $0\ensuremath{''}.1$-$0\ensuremath{''}.4$ as our complementary sample."]
- step 4: Measure FIR and optical sizes
  - method: IMFIT image-plane Gaussians; UVMODELFIT in uv plane (adopted); GALFIT Sersic for ALMA and HST; Re = sqrt(Rmaj*Rmin)/2 [2.4 Size Measurements: "The effective radius by `IMFIT` is calculated by $R_e=\sqrt{R_{Maj} \times R_{Min}}/2$"]
  - software: CASA IMFIT, UVMODELFIT, GALFIT
  - parameter: UVMODELFIT starts from IMFIT values, five iterations [2.4 Size Measurements: "fitted Gaussian models with five iterations by `UVMODELFIT` task"]
  - validation: UVMODELFIT ~2% lower than IMFIT; GALFIT ~10% larger; 20 matches with Fujimoto+18 differ ~0.05±0.10 kpc [2.4 Size Measurements: "The difference of the sizes are with a 2% systematic difference (`UVMODELFIT` gives lower values)."]
- result: FIR size, detected obscured AGN host (972308) = 0.43 ± 0.28 kpc [3 Analysis: "The sizes of our detected (0.43$\pm$0.28 kpc) and stacked (0.90$\pm$0.21 kpc) obscured AGN hosts"]
- result: FIR size, stacked obscured AGN hosts = 0.90 ± 0.21 kpc [3 Analysis: "The sizes of our detected (0.43$\pm$0.28 kpc) and stacked (0.90$\pm$0.21 kpc) obscured AGN hosts"]
- result: Stacked peak flux (image plane) = 0.09 ± 0.03 mJy [2.1 Our ALMA Observations: "The peak flux is 0.09 mJy$\pm$0.03 mJy (3.39 $\sigma$"]
- limitation (authors): Small sample and mismatched control sample (archival sources mostly above main sequence). [3 Analysis: "Most importantly, the number of objects in each sample is limited, especially for AGN sample."]
- not stated (card): Archival data reduction details (pipeline vs manual, CASA versions, calibrators); Cell size, image size, masking, cleaning threshold and deconvolver; Per-source archival weighting/robust used for size measurement; UVMODELFIT initial parameters and error handling beyond five iterations; GALFIT setup (PSF, masks, stamp sizes, constraints); Bootstrap details; Details of image-plane median stacking (…

### 2022ApJ...939L...6B: First Millimeter Flares Detected from ϵ Eridani with the Atacama Large Millimeter/submillimeter Array (2022; stellar_physics, debris_disks; archival_reuse)
- question: Search archival ALMA 12-m and ACA observations of the Sun-like star epsilon Eridani for millimeter flaring emission and characterize its temporal, spectral, and polarization properties, as well as constraints on inner dust belt emission.
- step 1: Continuum imaging and combined visibility fitting
  - method: Create natural weight primary-beam-corrected continuum images using tclean, calculate rms across ten source-free regions, and fit point source models to the combined visibilities using uvmodelfit. [Observations: "Imaging made use of the `tclean` task."] [ALMA 12-m Observations: "In order to calculate the rms, we choose ten regions that do not overlap with known emission sources (i.e., the star and surrounding disk), calculate the rms in each region, and average the values."]
  - software: CASA, tclean, uvmodelfit
  - parameter: natural weighting [ALMA 12-m Observations: "Figure 1 (right panel) displays the primary beam corrected natural weight continuum image."]
  - parameter: ten source-free regions for rms calculation [ALMA 12-m Observations: "In order to calculate the rms, we choose ten regions that do not overlap with known emission sources (i.e., the star and surrounding disk), calculate the rms in each region, and average the values."]
  - assumption: Point source model at the stellar position [ACA Observations: "Fitting a point source model to the combined visibilities yields a flux of $776 \pm 103$ $\mu$Jy."]
  - fitting: Point source visibility fitting with CASA uvmodelfit [ALMA 12-m Observations: "We use the `uvmodelfit` task in `CASA` to fit a point source model to the visibilities"]
  - validation: Compare 12-m stellar flux density (794 +/- 45 uJy) to value reported in Booth et al. 2017 (820 +/- 70 uJy) [ALMA 12-m Observations: "return a flux density of $794\pm45$ $\mu$Jy, consistent within the mutual uncertainties to the $820\pm70$ $\mu$Jy reported in (cite: Booth:2017)."]
- step 2: Create light curves and identify millimeter flares
  - method: Run an automatic pipeline using CASA uvmodelfit to fit point source models to each telescope integration step-by-step in time, flagging flux densities above 3 sigma, and confirm candidates by fitting lower and upper sidebands independently. [Creating Light Curves and Identifying F…: "we have now developed an automatic pipeline approach that makes use of the `uvmodelfit` task in `CASA`. For a given data set, models are fit to each integration from the telescope starting at the beginning of the observations and stepping forward in time."] [Creating Light Curves and Identifying F…: "Once the initial light curve is created, any recorded flux density that is above $3\sigma$ is flagged as a potential flaring event."]
  - software: CASA, uvmodelfit
  - parameter: integration time = 6 sec (ALMA 12-m) and 10 sec (ACA) [Creating Light Curves and Identifying F…: "For the ALMA 12-m and ACA observations, the integration times were 6 and 10 sec, respectively, setting the finest temporal resolution of the final light curves."]
  - parameter: detection threshold > 3 sigma [Creating Light Curves and Identifying F…: "Once the initial light curve is created, any recorded flux density that is above $3\sigma$ is flagged as a potential flaring event."]
  - parameter: sideband flux agreement within 20% [Creating Light Curves and Identifying F…: "We require that the flux densities measured in both sidebands be within 20% of each other."]
  - assumption: Point source model for the star [Creating Light Curves and Identifying F…: "we search for time-variable emission and flares by fitting point source models to the millimeter visibilities."]
  - fitting: CASA uvmodelfit per integration [Creating Light Curves and Identifying F…: "For a given data set, models are fit to each integration from the telescope starting at the beginning of the observations and stepping forward in time."]
  - validation: Require lower and upper sideband flux densities to be within 20% of each other, and compare visibility-derived fluxes with images made before, at peak, and after each flare. [Creating Light Curves and Identifying F…: "We require that the flux densities measured in both sidebands be within 20% of each other. Any events that do not meet this criteria are discarded as spurious noise."] [Creating Light Curves and Identifying F…: "The flux densities obtained from these images are consistent with those obtained from our visibility modeling, adding further credibility to these detections."]
- step 3: Characterize flare temporal structure, spectral index, and linear polarization
  - method: Fit Gaussian functions to flare light curves to measure FWHM (t_1/2), fit point source models with uvmodelfit to upper and lower sidebands independently for spectral index, and fit XX and YY polarizations independently to compute Stokes Q … [Characterizing Millimeter Flaring Emiss…: "To determine the temporal structure of the flaring events, we fit Gaussian functions to the light curves shown in Figure 4."] [Characterizing Millimeter Flaring Emiss…: "To obtain the spectral index, we fit point source models using `uvmodelfit` in `CASA` to the millimeter visibilities of the upper and lower sidebands independently."]
  - software: CASA, uvmodelfit
  - parameter: upper (230 + 232 GHz) and lower (219 + 217 GHz) sidebands [Characterizing Millimeter Flaring Emiss…: "we examine the spectral index (dependence of the flux on the frequency, F$_\nu\propto\nu^\alpha$) of the upper (230 + 232 GHz) and lower (219 + 217 GHz) sidebands"]
  - parameter: ALMA XX and YY polarizations at flare peak [Characterizing Millimeter Flaring Emiss…: "For the fractional linear polarization, we fit point sources models to ALMA’s XX and YY polarizations independently, and compute the Stokes parameters $Q = <{E_{x}}^2>-<{E_{y}}^2>$ and $I = <{E_{x}}^2>+<{E_{y}}^2>$."]
  - assumption: Gaussian temporal profile and power-law spectral dependence F_nu \propto \nu^\alpha [Characterizing Millimeter Flaring Emiss…: "To determine the temporal structure of the flaring events, we fit Gaussian functions to the light curves shown in Figure 4."] [Characterizing Millimeter Flaring Emiss…: "we examine the spectral index (dependence of the flux on the frequency, F$_\nu\propto\nu^\alpha$) of the upper (230 + 232 GHz) and lower (219 + 217 GHz) sidebands"]
  - fitting: Gaussian function fits to light curves; CASA uvmodelfit point source fits to sideband and XX/YY visibilities [Characterizing Millimeter Flaring Emiss…: "To determine the temporal structure of the flaring events, we fit Gaussian functions to the light curves shown in Figure 4."] [Characterizing Millimeter Flaring Emiss…: "To obtain the spectral index, we fit point source models using `uvmodelfit` in `CASA` to the millimeter visibilities of the upper and lower sidebands independently."]
- step 5: Measure quiescent stellar and inner dust excess flux density
  - method: Fit a point source model using CASA uvmodelfit over all available ALMA observations excluding the flare intervals (E1, E2, E3), and subtract the expected photospheric flux at 1.3 mm. [Constraints on Dust Emission from an In…: "We use `uvmodelfit` `CASA` to determine the flux density of the star over all of the available ALMA observations, excluding the time when the star was flaring (i.e., during events E1, E2, and E3)."] [Constraints on Dust Emission from an In…: "The result is $787\pm45$ $\mu$Jy, less than previous millimeter measurement but still in excess of the expected stellar photosphere by $257\pm34$ $\mu$Jy."]
  - software: CASA, uvmodelfit
  - parameter: Exclude flaring intervals E1, E2, and E3 [Constraints on Dust Emission from an In…: "excluding the time when the star was flaring (i.e., during events E1, E2, and E3)."]
  - assumption: Expected stellar photospheric flux at 1.3 mm is 0.53 mJy [Constraints on Dust Emission from an In…: "The effective temperature of $\epsilon$ Eridani is $5039\pm126$ K (cite: Baines:2012), which implies a photospheric flux at 1.3 mm of $0.53$ mJy (cite: Backman:2009)."]
  - fitting: CASA uvmodelfit point source fit to flare-excluded visibilities [Constraints on Dust Emission from an In…: "We use `uvmodelfit` `CASA` to determine the flux density of the star over all of the available ALMA observations, excluding the time when the star was flaring (i.e., during events E1, E2, and E3)."]
  - validation: Compare excess flux with extrapolated SED fits for the inner dust ring from Su et al. 2017 (~0.2-0.3 mJy) [Constraints on Dust Emission from an In…: "Extrapolating the SED fits for the inner dust ring from (cite: Su:2017) yields a predicted flux at 1.3 mm of $\sim0.2-0.3$ mJy, strikingly consistent with what we determine here."]
- result: ACA combined visibility point source flux density = 776 ± 103 \muJy [ACA Observations: "Fitting a point source model to the combined visibilities yields a flux of $776 \pm 103$ $\mu$Jy."]
- result: ALMA 12-m combined visibility point source flux density = 794 ± 45 \muJy [ALMA 12-m Observations: "We use the `uvmodelfit` task in `CASA` to fit a point source model to the visibilities and return a flux density of $794\pm45$ $\mu$Jy"]
- result: Flare E1 peak flux density = 28 ± 7 mJy [Abstract: "with a peak flux density of 28 $\pm$ 7 mJy"]
- result: Flare E1 peak luminosity = 3.4e14 ± 0.9e14 erg s^-1 Hz^-1 [Abstract: "The peak brightness of the largest flare is $3.4 \pm 0.9 \times 10^{14}$ erg s$^{-1}$Hz$^{-1}$"]
- result: Flare E2 peak flux density = 14 ± 3 mJy [Creating Light Curves and Identifying F…: "The other two flares reached lower peak flux densities of $14\pm 3$ mJy (labeled E2) and $9\pm 2$ mJy (labeled E3)"]
- result: Flare E2 peak luminosity = 1.7e14 ± 0.4e14 erg s^-1 Hz^-1 [Creating Light Curves and Identifying F…: "corresponding to peak luminosities of $1.7\pm 0.4 \times 10^{14}$ erg s$^{-1}$ Hz$^{-1}$ and $1.1\pm 0.2 \times 10^{14}$ erg s$^{-1}$ Hz$^{-1}$, respectively."]
- result: Flare E3 peak flux density = 9 ± 2 mJy [Creating Light Curves and Identifying F…: "The other two flares reached lower peak flux densities of $14\pm 3$ mJy (labeled E2) and $9\pm 2$ mJy (labeled E3)"]
- result: Flare E3 peak luminosity = 1.1e14 ± 0.2e14 erg s^-1 Hz^-1 [Creating Light Curves and Identifying F…: "corresponding to peak luminosities of $1.7\pm 0.4 \times 10^{14}$ erg s$^{-1}$ Hz$^{-1}$ and $1.1\pm 0.2 \times 10^{14}$ erg s$^{-1}$ Hz$^{-1}$, respectively."]
- result: Flare E1 duration (t_1/2) = 7.9 ± not stated sec [Characterizing Millimeter Flaring Emiss…: "Event E3 has the shortest duration of only 6.6 sec, while the E1 and E2 flares do not last much longer, at 7.9 and 9.0 sec, respectively."]
- result: Flare E2 duration (t_1/2) = 9.0 ± not stated sec [Characterizing Millimeter Flaring Emiss…: "Event E3 has the shortest duration of only 6.6 sec, while the E1 and E2 flares do not last much longer, at 7.9 and 9.0 sec, respectively."]
- result: Flare E3 duration (t_1/2) = 6.6 ± not stated sec [Characterizing Millimeter Flaring Emiss…: "Event E3 has the shortest duration of only 6.6 sec, while the E1 and E2 flares do not last much longer, at 7.9 and 9.0 sec, respectively."]
- result: Flare E1 spectral index (\alpha) = 1.81 ± 1.94 dimensionless [Abstract: "We find changes in the spectral index (F$_\nu\propto\nu^\alpha$) at the flare peak, with $\alpha$ = 1.81 $\pm$ 1.94"]
- result: Flare E2 spectral index (\alpha) = 7.29 ± 2.89 dimensionless [Table 1: "| | E2 | 14 | 17 | 9.0$^\text{a}$ | 7.29 $\pm$ 2.89 | $>$-0.48 $\pm$ 0.15 | |"]
- result: Flare E3 spectral index (\alpha) = -2.83 ± 2.33 dimensionless [Table 1: "| | E3 | 9 | 11 | 6.6$^\text{a}$ | -2.83 $\pm$2.33 | $>$-0.11$\pm$0.19 | |"]
- result: Flare E1 fractional linear polarization lower limit (|Q/I|) = >0.08 ± 0.12 dimensionless [Abstract: "and a lower limit on the fractional linear polarization $|Q/I| =$ 0.08 $\pm$ 0.12."]
- result: Flare E2 fractional linear polarization lower limit (|Q/I|) = >-0.48 ± 0.15 dimensionless [Table 1: "| | E2 | 14 | 17 | 9.0$^\text{a}$ | 7.29 $\pm$ 2.89 | $>$-0.48 $\pm$ 0.15 | |"]
- result: Flare E3 fractional linear polarization lower limit (|Q/I|) = >-0.11 ± 0.19 dimensionless [Table 1: "| | E3 | 9 | 11 | 6.6$^\text{a}$ | -2.83 $\pm$2.33 | $>$-0.11$\pm$0.19 | |"]
- result: Quiescent stellar flux density (excluding flares) = 787 ± 45 \muJy [Constraints on Dust Emission from an In…: "The result is $787\pm45$ $\mu$Jy, less than previous millimeter measurement but still in excess of the expected stellar photosphere by $257\pm34$ $\mu$Jy."]
- result: Quiescent flux excess over stellar photosphere = 257 ± 34 \muJy [Constraints on Dust Emission from an In…: "The result is $787\pm45$ $\mu$Jy, less than previous millimeter measurement but still in excess of the expected stellar photosphere by $257\pm34$ $\mu$Jy."]
- limitation (authors): Shorter integration times imply higher rms noise, so fainter flares will not be detected. [Creating Light Curves and Identifying F…: "Shorter integration times imply higher rms noise and fainter flares will not be detected."]
- limitation (authors): ACA has fewer and smaller (7-m) antennas, resulting in 3-5x higher rms noise per integration than the 12-m array, preventing detection of flares of this brightness in the ACA data. [Creating Light Curves and Identifying F…: "with fewer antennas in the array and smaller antenna diameters (7-m for the ACA), the total collecting area is reduced and as a result the rms noise in each integration was a factor of $3-5\times$ higher than for the ALMA 12-m observations."]
- limitation (authors): Due to limited signal-to-noise, spectral index and fractional linear polarization lower limits can only be computed at the peak of the three flares, and lack of polarization calibration leads to large uncertainties. [Characterizing Millimeter Flaring Emiss…: "Due to limited signal-to-noise, we are only able to compute the spectral index and lower limit on the fractional linear polarization at the peak of the three detected flares."]
- not stated (card): CASA version used for calibration, imaging, and uvmodelfit; Whether archival data were calibrated via pipeline or manual scripts; Image pixel cell size and image dimensions in tclean; Deconvolver algorithm and stopping threshold/masking in tclean; Exact coordinates or proper-motion-corrected position fixed or fitted in uvmodelfit; How the ten background regions for RMS calculation were defined

### 2015A&A...582A..91C: Exploring the molecular chemistry and excitation in obscured luminous infrared galaxies. An ALMA mm-wave spectral scan of NGC 4418 (2015; nearby_galaxies, astrochemistry; observational_alma_primary)
- question: What are the molecular abundances and excitation in the compact obscured nucleus of NGC 4418, and how do they compare with other Galactic and extragalactic environments?
- step 1: Extract spectrum from visibilities
  - method: Fit point-source model with fixed position, free amplitude to visibilities of each spectral window; merge windows averaging 250 MHz overlaps [2.1 UV-fit of the spectrum: "we fitted the interferometric spectral visibilities of each spectral window assuming a point-source model, with a fixed position but free amplitude."]
  - software: CASA, uvmultifit
  - parameter: 20 km/s common resolution [2.1 UV-fit of the spectrum: "interpolated to a common resolution of 20 km s$^{-1}$across the whole frequency range"]
  - assumption: Emission unresolved (<0.4'' band 3, <0.2'' band 6) [2.1 UV-fit of the spectrum: "We found the emission to be unresolved, with upper limits to the source size of 0$''$.4 and 0$''$.2 for band 3 and band 6, respectively."]
  - validation: Compared with IRAM 30m and SMA fluxes [2.1 UV-fit of the spectrum: "The flux densities measured for the two datasets are within the errors"]
- limitation (authors): Unresolved emission: source size and common beam filling factor are the main uncertainties; line blending ~20% [3.4 Limitations: "Because the emission is unresolved in the ALMA beam, the main uncertainty in our LTE/NLTE fit is the source size."]
- not stated (card): Phase/bandpass calibration details and CASA version; Coordinates of the continuum peak used for the point-source fit; Line-free channel ranges used for the continuum polynomial; Exact line-list/species list and the fitting code (not released); Priors/grid steps of the RADEX grid and the molecule ordering; Flux-scale handling for tunings with 3C 273 as flux calibrator

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

### 2019MNRAS.487.4037D: A joint ALMA-Bolocam-Planck SZ study of the pressure distribution in RX J1347.5-1145 (2019; galaxy_clusters_and_sz; observational_alma_primary)
- question: Can joint forward-modelling of ALMA/ACA visibilities with Bolocam and Planck images constrain the pressure distribution of RX J1347.5-1145, and does the south-eastern SZ excess indicate a strong overpressure or reflect model geometry?
- step 2: Joint Bayesian fit of spherical cool-core gNFW plus point source
  - method: Joint likelihood product of ACA+ALMA visibilities, Bolocam and Planck images; gNFW centred on X-ray peak with fixed Arnaud slopes, Te=7 keV, point source power law [5.1.1: "we fit a spherically symmetric gNW pressure profile whose centroid is set at the position of the peak in the observed X-ray brightness distribution"]
  - software: emcee, GALARIO, FFTW, astropy
  - parameter: Free: Pei, rs (uniform priors), point-source position, flux, spectral index; kappa Gaussian, eta exponential hyperparameters [Table 1: "$\mathcal{E}[1.00]$ is instead the exponential distribution with unitary expectation value"]
  - assumption: Te fixed at 7 keV [5.1.1: "we fix the electron temperature to $T_{\mathrm{e}}=7~\mathrm{keV}$"]
  - fitting: Affine-invariant ensemble MCMC (emcee), medians and 68% intervals [4.3: "we make use of the specific implementation of the affine-invariant ensemble sampling technique"]
  - validation: Data-free prior-only run and mock tests [5.1.1: "This has been performed by sampling the posterior distribution obtained in the case of a constant likelihood"]
- step 4: Fit free-centroid ellipsoidal gNFW
  - method: Free centroid, eccentricity, angle, inner slope gamma, Te=12.5 keV, Gaussian prior on Planck Ycyl [5.1.3: "we now assume an electron temperature of $12.5~\mathrm{keV}$"]
  - software: emcee, GALARIO
  - assumption: Line-of-sight axis equals inverse rms average of sky-plane semi-axes [8 Triaxial ellipsoidal profile: "the extent of the latter is hard-coded with the assumption that it is equal to the inverse root mean square average of the plane-of-sky semi-axes"]
  - fitting: emcee MCMC with uniform priors [Implementation details: "we make use of the specific implementation of the affine-invariant ensemble sampling technique (cite: Goodman2010) provided by the EMCEE PYTHON package (cite: Foreman2013)"]
  - validation: Prior-only sampling shows no bias; residual map shows no significant structure [5.1.3: "the prior-only sampling shows no biases in the reconstruction of the model parameters"]
- result: Spherical gNFW r_s = 3.10 ± 16th 2.97, 84th 3.24 arcmin [Table 2: "$r_{\mathrm{s}}$ | arcmin | $3.10$ | $2.97$ | $3.24$"]
- result: Spherical gNFW P_ei = 5.39e-2 ± 16th 5.16, 84th 5.65 (1e-2) keV cm^-3 [Table 2: "$5.39$ | $5.16$ | $5.65$"]
- result: Point-source flux at 90 GHz = 4.208 ± 16th 4.199, 84th 4.217 mJy [Table 2: "$4.208$ | $4.199$ | $4.217$"]
- result: Point-source spectral index = -0.431 ± 16th -0.462, 84th -0.399 dimensionless [Table 2: "$-0.431$ | $-0.462$ | $-0.399$"]
- result: Planck/ALMA+ACA scaling ratio = 0.993 ± 0.038 dimensionless [5.1.4: "with ratio equal to $0.993\pm 0.038$"]
- limitation (authors): Models differ in components so statistical comparison is misleading; overfitting may hide overpressure; X-ray arithmetic limited to linear perturbations [5.2: "a direct comparison based on statistical considerations would provide misleading results"]
- not stated (card): Exact binning parameters and number of averaged visibilities; Planck MILCA implementation details and Y_cyl Gaussian prior; MCMC walkers, steps, burn-in and convergence; Fitting code is not public/versioned; Chandra reduction details and X-ray arithmetic smooth models; Source of 12.5 keV vs 7 keV temperature choices beyond brief description

### 2014A&A...566A..74L: ALMA observations of the kinematics and chemistry of disc formation (2014; star_formation, astrochemistry; observational_alma_primary)
- question: Is there a Keplerian disc around the Class 0/I protostar IRS7B in the R CrA cloud, and how does the disc relate to the presence of complex organic molecules in the inner envelope?
- step 2: Build C17O PV diagram
  - method: Fit strongest peak per channel in uv data, derive PA and PV diagram [4.1: "Through the CASA task `uvmodelfit` we identify the strongest peak of the C$^{17}$O emission in each channel of the $(u,\varv)$ data."]
  - software: CASA uvmodelfit
  - parameter: PA -65 deg, centre LSR velocity 6.2 km/s [4.1: "We find that the motion has a position angle of $-65$$^\circ$ on the sky and is centred around the channel corresponding to an LSR velocity of 6.2 km s$^{-1}$."]
  - fitting: Weighted least-squares fit of positions [Analysis, A Keplerian disc around IRS7B: "By the method of (cite: goodman93), which uses a weighted least-square fit to the positional data to establish the inclination of the velocity gradient on the plane of sky"]
- step 3: Fit Keplerian disc with finite radius vs infall
  - method: Fit Keplerian profile plus linear branch; compare chi2 with v~r^-1 infall; compare against LIME fiducial disc [4.1: "by fitting a Keplerian profile (blue curve) and a straight line (green curve) to the data we can determine the disc radius very accurately."]
  - software: LIME
  - parameter: free parameters: central mass and disc radius [4.1: "The central mass and the disc radius are the only free parameters."]
  - assumption: Flat disc, n∝r^-1, T∝r^-0.5, LTE, optically thin, inclination 60 deg [4.1: "the disc is assumed to be flat with a radial density profile $n(r) \propto r^{-1}$ and a temperature profile $T(r) \propto r^{-0.5}$."]
  - fitting: chi2 fit weighted by uvmodelfit errors [4.1: "We do a $\chi^2$ fit to the velocities as a function of radius weighted by the `uvmodelfit` errors on the positional fits."]
  - validation: Keplerian chi2 a factor 2.3 lower than infall [4.1: "the Keplerian fit has a $\chi^2$ value a factor 2.3 times lower than the infall fit"]
- result: IRS7B disc radius = 50 ± not stated AU [4.1: "We find the radius of the spatially well-constrained disc to be 0.41$''$ which equals to 50 AU"]
- result: Central mass of IRS7B = 2.3 ± not stated Msun [4.1: "corresponds to a central mass of $M_{\star}=2.3~M_{\odot}$ assuming the most probable inclination of $60\ensuremath{^\circ}$."]
- limitation (authors): Higher sensitivity and resolution needed to verify the Keplerian disc [Conclusions: "To verify that the C$^{17}$O emission on IRS7B originates in a Keplerian disc, higher-sensitivity and higher-resolution observations are needed."]
- not stated (card): Which spw/channels were line-free for continuum and the continuum bandwidth; Self-calibration solution intervals and number of iterations; CASA version and calibration pipeline/manual details; Cell size, image size, masks and clean thresholds; Dust opacity and gas-to-dust ratio used for disc mass; Details of the LIME model (grid, abundance, inclination handling, fitting procedure); Fitting detail…

### 2021A&A...653A..53A: DEATHSTAR: nearby AGB stars with the Atacama Compact Array. II. CO envelope sizes and asymmetries: the S-type stars (2021; evolved_stars, astrochemistry; observational_alma_primary)
- question: Constrain CO circumstellar envelope sizes and deviations from spherical symmetry.
- step 4: Estimate envelope sizes and axis ratios
  - method: Per-channel Gaussian fits to ACA-only visibilities; image-plane Gaussian fits to TP-only CO(2–1) for four sources. [Fitting the emission distribution: "We fit a Gaussian emission distribution model to the data visibilities in CO(2–1) and CO(3–2) in each velocity channel for the sources observed with ACA-only using the UVMULTIFIT library implemented in CASA (cite: uvmultifit)."] [Fitting the emission distribution: "The emission distributions of AI$\,\,$Vol, AFGL$\,\,$3068, R$\,\,$Dor, and IRC-30398 were fitted by a Gaussian model in the image plane on the CO(2–1) TP-only data."]
  - software: CASA, UVMULTIFIT
  - parameter: Position, flux, major axis, minor-to-major axis ratio, and position angle. [Fitting the emission distribution: "For each run, UVMULTIFIT gives the position, flux, major axis, ratio between minor and major axes, and the position angle of the fitted Gaussian."]
  - parameter: Central-channel Gaussian major axes and axis ratios. [Gaussian distribution fitting: "The measured major axes and ratio of the minor to major axis of the best-fitting Gaussian at the central channel"]
  - parameter: Error: average error from the two channels on each side of the central velocity channel. [Gaussian distribution fitting: "We take the error as the average error from the two channels on each side of the central velocity channel."]
  - assumption: Gaussian emission distribution gives an initial envelope-size estimate. [Fitting the emission distribution: "Such fitting of the emission distribution permits initial estimates of the sizes of the CO envelopes and will reveal signs of deviation from spherical symmetry."]
  - fitting: Gaussian model; UVMULTIFIT for ACA-only visibilities; TP diameters from deconvolved image-plane major axes. [Fitting the emission distribution: "We fit a Gaussian emission distribution model to the data visibilities in CO(2–1) and CO(3–2) in each velocity channel for the sources observed with ACA-only using the UVMULTIFIT library implemented in CASA (cite: uvmultifit)."] [Fitting the emission distribution: "The resulting deconvolved major axes give an estimate of the diameters of the CO envelopes."]
  - validation: Inspect velocity-dependent fits for spikes, negative regions, missing flux, and poor Gaussian descriptions. [Gaussian distribution fitting: "Negative regions emerge, which is due to the flux being resolved out."] [Gaussian distribution fitting: "As a consequence, the emission cannot be properly fitted by a Gaussian distribution, leading to fluctuating spikes."]
- result: T Cet CO(2–1) Gaussian major axis = 4.58 ± ±0.34 arcsec [Table 2: "T Cet | 10.8 | 4.58$\pm$0.34 | 0.79$\pm$0.06"]
- result: Z Ant CO(2–1) Gaussian major axis = 3.24 ± ±0.17 arcsec [Table 2: "Z Ant | 6.2 | 3.24$\pm$0.17 | 0.84$\pm$0.06"]
- result: UY Cen CO(2–1) Gaussian major axis = 1.49 ± ±0.71 arcsec [Table 2: "UY Cen | 5.0 | 1.49$\pm$0.71 | 0.52$\pm$0.23"]
- result: AM Cen CO(2–1) Gaussian major axis = 5.59 ± ±0.27 arcsec [Table 2: "AM Cen | 6.8 | 5.59$\pm$0.27 | 0.90$\pm$0.06"]
- result: ST Sco CO(2–1) Gaussian major axis = 4.32 ± ±0.10 arcsec [Table 2: "ST Sco | 10.6 | 4.32$\pm$0.10 | 1.00$\pm$0.02"]
- result: FU Mon CO(2–1) Gaussian major axis = 8.29 ± ±0.17 arcsec [Table 2: "FU Mon | 10.2 | 8.29$\pm$0.17 | 0.84$\pm$0.03"]
- result: NSV 24833 CO(2–1) Gaussian major axis = 3.76 ± ±0.21 arcsec [Table 2: "NSV 24833 | 8.2 | 3.76$\pm$0.21 | 0.96$\pm$0.06"]
- result: DY Gem CO(2–1) Gaussian major axis = 4.50 ± ±0.15 arcsec [Table 2: "DY Gem | 12.7 | 4.50$\pm$0.15 | 0.51$\pm$0.04"]
- result: RZ Sgr CO(2–1) Gaussian major axis = 9.00 ± ±0.09 arcsec [Table 2: "RZ Sgr | 27.6 | 9.00$\pm$0.09 | 0.99$\pm$0.01"]
- result: TT Cen CO(2–1) Gaussian major axis = 6.26 ± ±0.31 arcsec [Table 2: "TT Cen | 14.2 | 6.26$\pm$0.31 | 1.00$\pm$0.07"]
- result: GI Lup CO(2–1) Gaussian major axis = 3.81 ± ±0.14 arcsec [Table 2: "GI Lup | 9.8 | 3.81$\pm$0.14 | 0.95$\pm$0.06"]
- result: RT Sco CO(2–1) Gaussian major axis = 6.99 ± ±0.07 arcsec [Table 2: "RT Sco | 21.6 | 6.99$\pm$0.07 | 1.00$\pm$0.01"]
- result: IRC-10401 CO(2–1) Gaussian major axis = 5.43 ± ±0.42 arcsec [Table 2: "IRC -10401 | 10.6 | 5.43$\pm$0.42 | 0.85$\pm$0.06"]
- result: ST Sgr CO(2–1) Gaussian major axis = 1.52 ± ±0.17 arcsec [Table 2: "ST Sgr | 8.5 | 1.52$\pm$0.17 | 0.98$\pm$0.05"]
- result: T Sgr CO(2–1) Gaussian major axis = 3.55 ± ±0.40 arcsec [Table 2: "T Sgr | 5.8 | 3.55$\pm$0.40 | 0.99$\pm$0.10"]
- result: W Aql CO(3–2) Gaussian major axis = 4.62 ± ±0.05 arcsec [Table 2: "4.62$\pm$0.05 | 1.00$\pm$0.02"]
- result: θ Aps CO(2–1) Gaussian major axis = 4.90 ± ±0.06 arcsec [Table 2: "$\theta$ Aps | 10.1 | 4.90$\pm$0.06 | 0.97$\pm$0.01"]
- result: R Dor TP-only CO(2–1) deconvolved major axis = 14.69 ± ±0.27 arcsec [Table 2: "R Dor$^*$ | 42.7 | 14.69$\pm$0.27 | 0.92$\pm$0.03"]
- result: U Men CO(2–1) Gaussian major axis = 7.15 ± ±0.20 arcsec [Table 2: "U Men | 7.0 | 7.15$\pm$0.20 | 0.88$\pm$0.03"]
- result: IRC-30398 TP-only CO(2–1) deconvolved major axis = 12.24 ± ±0.41 arcsec [Table 2: "IRC-30398$^*$ | 27.5 | 12.24$\pm$0.41 | 0.82$\pm$0.06"]
- result: V1302 Cen CO(2–1) Gaussian major axis = 1.94 ± ±0.28 arcsec [Table 2: "V1302 Cen | 6.3 | 1.94$\pm$0.28 | 1.00$\pm$0.11"]
- result: V996 Cen CO(2–1) Gaussian major axis = 4.58 ± ±0.27 arcsec [Table 2: "V996 Cen | 7.4 | 4.58$\pm$0.27 | 0.85$\pm$0.06"]
- result: X TrA CO(2–1) Gaussian major axis = 6.19 ± ±0.06 arcsec [Table 2: "X TrA | 10.7 | 6.19$\pm$0.06 | 0.99$\pm$0.01"]
- result: AQ Sgr CO(3–2) Gaussian major axis = 0.93 ± ±0.36 arcsec [Table 2: "0.93$\pm$0.36 | 0.90$\pm$0.04"]
- result: V821 Her CO(2–1) Gaussian major axis = 6.53 ± ±0.04 arcsec [Table 2: "V821 Her | 31.5 | 6.53$\pm$0.04 | 0.98$\pm$0.01"]
- result: AI Vol TP-only CO(2–1) deconvolved major axis = 14.56 ± ±0.60 arcsec [Table 2: "AI Vol$^*$ | 37.6 | 14.56$\pm$0.60 | 0.94$\pm$0.06"]
- result: AFGL 3068 TP-only CO(2–1) deconvolved major axis = 17.14 ± ±0.73 arcsec [Table 2: "AFGL 3068$^*$ | 40.3 | 17.14$\pm$0.73 | 0.86$\pm$0.06"]
- result: T Cet CO(2–1) minor-to-major axis ratio = 0.79 ± ±0.06 dimensionless [Table 2: "T Cet | 10.8 | 4.58$\pm$0.34 | 0.79$\pm$0.06"]
- result: UY Cen CO(2–1) minor-to-major axis ratio = 0.52 ± ±0.23 dimensionless [Table 2: "UY Cen | 5.0 | 1.49$\pm$0.71 | 0.52$\pm$0.23"]
- result: FU Mon CO(2–1) minor-to-major axis ratio = 0.84 ± ±0.03 dimensionless [Table 2: "FU Mon | 10.2 | 8.29$\pm$0.17 | 0.84$\pm$0.03"]
- result: DY Gem CO(2–1) minor-to-major axis ratio = 0.51 ± ±0.04 dimensionless [Table 2: "DY Gem | 12.7 | 4.50$\pm$0.15 | 0.51$\pm$0.04"]
- result: RZ Sgr CO(2–1) minor-to-major axis ratio = 0.99 ± ±0.01 dimensionless [Table 2: "RZ Sgr | 27.6 | 9.00$\pm$0.09 | 0.99$\pm$0.01"]
- limitation (authors): Missing flux and high noise can significantly alter Gaussian fits; sizes are first approximations. [Discussion and summary: "A number of the observations presented in this paper are subject to missing or resolved-out flux, or high noise levels that can significantly alter the Gaussian fits."]
- limitation (authors): Gaussian-size reliability decreases with increasing MLR. [Discussion and summary: "The reliability of the Gaussian fit estimates decreases with increasing MLR which will affect the larger sources in particular (cite: deathstar)."]
- limitation (authors): Distance uncertainties affect linear sizes and model comparisons. [Discussion and summary: "The measured sizes are also affected by the large uncertainties in the distances."]
- not stated (card): CASA, pipeline, UVMULTIFIT, and tp2vis versions.; Per-source execution blocks, observing dates, configurations, and baseline ranges.; Self-calibration channel indices, solution intervals, solution type, reference antenna, and iteration sequence.; Image cell sizes, image dimensions, cleaning thresholds, and masks for sources at or below 20 Jy.; Multiscale scale sizes and TP-to-ACA visibility weigh…

### 2018AJ....156..164B: Medium-sized Satellites of Large Kuiper Belt Objects (2018; solar_system; observational_alma_primary)
- question: What are the sizes and albedos of Dysnomia (Eris) and Vanth (Orcus), and do they fit the small icy collisional-satellite paradigm?
- step 1: Reduce visibilities and measure flux densities
  - method: Pipeline calibration in CASA, then AIPS; natural-weight imaging; flux by image, CLEAN components, gaussian fit and visibility fit; decorrelation correction from check source [2 Observations: "flux density in the image; flux density in the CLEAN components; fitting a gaussian in the image; and fitting the visibilities directly."]
  - software: CASA, AIPS
  - parameter: Eris visibility fit: slightly limb-darkened disk, radius 1163 km; others point sources [2 Observations: "For Eris, we used a fit of a slightly limb-darkened disk, with radius of 1163 km (cite: 2011_Sicardy)."]
  - validation: Compared the four flux methods; relatively good agreement [2 Observations: "We found relatively good agreement for all of these techniques."]
- limitation (authors): Dysnomia detection is weak and needs robust detection at multiple locations [Discussion: "robust detection at multiple locations are desired"]
- not stated (card): Phase calibrators, flux calibrator, and antenna numbers/baselines; AIPS imaging parameters (cell, image size, clean depth); Decorrelation correction factors per observation; MCMC sampler details, priors, chain lengths; Beaming parameter priors; Distances/heliocentric geometry for thermal model

### 2021A&A...650A.153D: Multiwavelength view of SPT-CL J2106-5844. The radio galaxies and the thermal and relativistic plasmas in a massive galaxy cluster merger at z ≃ 1.13 (2021; galaxy_clusters_and_sz, agn_and_quasars; archival_reuse)
- question: Reconstruct the intracluster pressure distribution and investigate the merger and diffuse radio emission in SPT-CL J2106-5844.
- step 3: Separate compact and diffuse radio emission
  - method: Image ASKAP and ATCA data; subtract an unresolved central source from EMU and compact CLEAN models from ATCA visibilities. [Evolutionary Map of the Universe Pilot …: "We estimate the flux density of the compact core by subtracting an unresolved source from the image and determining when there were no significant positive or negative residuals on top of the extended emission."] [Australia Telescope Compact Array: "by performing a first imaging run assuming a uniform weighting, and then employing the reconstructed CLEAN components as input models to be subtracted from the each of the raw interferometric data sets."]
  - software: ASKAPsoft, CASA
  - parameter: ASKAP: two Taylor terms; convolve 36 single-beam images to 18″ FWHM; linear mosaic; spectral index T1/T0 [Evolutionary Map of the Universe Pilot …: "utilizing a two Taylor-term (T0 and T1) multi-scale CLEAN algorithm (cite: Rau2011)."] [Evolutionary Map of the Universe Pilot …: "The resulting 36 single-beam images were convolved to a resolution of $18\ensuremath{''}$ full-width-half-maximum and combined with a linear mosaic"]
  - parameter: ATCA: eight spectral windows for calibration; primary calibrator 1934-638; interleaved calibrator amplitude/phase solutions [Australia Telescope Compact Array: "In all cases, we split the 2048 MHz bandwidth into eight spectral windows for calibration."] [Australia Telescope Compact Array: "We use the primary calibrator source 1934-638 to solve for the bandpass in amplitude and phase."]
  - parameter: ATCA 2.1 GHz: natural weighting and three phase self-calibration rounds; whole-band multifrequency synthesis [Australia Telescope Compact Array: "For the 2.1 GHz data, we image using natural weighting and then perform three rounds of self-calibration in phase."] [Australia Telescope Compact Array: "The noise levels of the naturally weighted maps, imaged using multifrequency synthesis over the whole bandwidth, are 40, 20 and 15"]
  - assumption: EMU subtraction includes only the central radio source [Compact sources: "We emphasize that we subtracted from the EMU data only the model corresponding to the central radio source."]
  - fitting: Adjust the unresolved EMU source until no significant positive or negative residuals remain over the extended emission. [Evolutionary Map of the Universe Pilot …: "determining when there were no significant positive or negative residuals on top of the extended emission."]
  - validation: Compare high-resolution ATCA observations with the EMU radio distribution. [Compact sources: "The comparison of high-resolution ATCA observations of SPT-CL J2106-5844 with the distribution of the radio signal in the EMU map provides key information on the population of unresolved sources contaminating the diffuse radio emission."]
- result: EMU compact-core flux = 6.7 ± ±0.3 mJy [Evolutionary Map of the Universe Pilot …: "We find a flux of $6.7\pm 0.3~\mathrm{mJy}$"]
- result: EMU compact-core spectral index = -1.2 ± ±0.1 dimensionless [Evolutionary Map of the Universe Pilot …: "and a spectral index of $-1.2\pm0.1$"]
- result: Diffuse radio structure extent = ∼400 ± not stated kpc [Conclusions and future work: "Removal of the compact radio sources within the field reveals a diffuse radio structure on scales of $\sim400~\mathrm{kpc}$."]
- limitation (authors): Chandra source counts do not constrain the ICM temperature distribution. [Chandra: "The low number of source counts in the available *Chandra* data did not allow for deriving significant constraints on the temperature distribution of the ICM within SPT-CL J2106-5844."]
- limitation (authors): Most X-ray hardness structures have low significance. [Chandra: "aside from the bright core region, it is not possible to identify any structure with a significance higher than $2\sigma$."]
- limitation (authors): Radio resolution, sparse sampling, and weak high-frequency detections prevent a detailed spectral-index map. [Diffuse emission: "the different angular resolutions of the available radio data, combined with the severe sparsity and low significance of the observations at high frequencies, do not allow for building a detailed map of the spectral index distribution"]
- not stated (card): ALMA/ACA calibrated measurement-set release identifiers, calibration CASA/pipeline versions, and any additional flagging or averaging.; Exact visibility likelihood, visibility-weight treatment, and implementation of the 5% flux-calibration uncertainty.; Forward-model map grid, line-of-sight integration limits, primary-beam model, and frequency integration across spectral windows.; Numerical fixed…

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

### 2025A&A...704A..18O: High-angular-resolution ALMA imaging of the inhomogeneous dynamical atmosphere of the asymptotic giant branch star W Hya: SiO, H<SUB>2</SUB>O, SO<SUB>2</SUB>, … (2025; evolved_stars, astrochemistry; observational_alma_primary)
- question: What are the dynamics and chemistry in the atmosphere and inner wind (within a few stellar radii) of the asymptotic giant branch star W Hya, and how do molecular species relate to dust formation and shocks?
- step 1: Determine stellar continuum disk center, angular size, flux density spectrum, and brightness temperature
  - method: Fit visibility data at line-free channels before self-calibration with a uniform elliptical disk using uvmultifit; measure integrated continuum flux densities across the 9 spectral windows and fit a frequency power law. [Observations and data reduction: "In order to determine the position of the stellar disk center, we fit the visibility data at the line-free spectral channels in each spectral window before self-calibration with a uniform ellipse using `uvmultifit` (Martí-Vidal et al. (cite: marti-vidal14))."] [Continuum: "As Fig. [2](#cont_flux_spec) shows, the continuum flux measurements can be well fit with a power law, $F_{\nu} \propto \nu^{2.08 \pm 0.03}$."]
  - software: uvmultifit
  - parameter: Uniform elliptical disk model [Observations and data reduction: "we fit the visibility data at the line-free spectral channels in each spectral window before self-calibration with a uniform ellipse using `uvmultifit`"]
  - assumption: Continuum is formed by optically thick free-free emission [Continuum: "Assuming that the continuum is formed by the optically thick free-free emission, the derived brightness temperatures correspond to the gas temperature in the millimeter-continuum-forming layers."]
  - fitting: Visibility-plane uniform ellipse fit with uvmultifit; power-law fit to continuum flux densities vs frequency [Observations and data reduction: "we fit the visibility data at the line-free spectral channels in each spectral window before self-calibration with a uniform ellipse using `uvmultifit` (Martí-Vidal et al. (cite: marti-vidal14))."] [Continuum: "As Fig. [2](#cont_flux_spec) shows, the continuum flux measurements can be well fit with a power law, $F_{\nu} \propto \nu^{2.08 \pm 0.03}$."]
  - validation: Compared continuum flux density with literature 250 GHz measurement by Dehaes et al. (2007) and spectral index with radio-photosphere model (1.86) [Continuum: "The flux densities are in broad agreement with the measurement by Dehaes et al. ((cite: dehaes07)), who obtained $280.0 \pm 17.2$ mJy at 250 GHz"] [Continuum: "This is close to the power-law index of 1.86 expected from the radio-photosphere model"]
- result: Continuum flux density at 250.727 GHz (spw 1) = 267.7 ± 1.3 mJy [Table 1: "| 1 | 250.727 | 468.75 | 1.17 | $19.7\times16.5$ | 0.57 | $267.7 \pm 1.3$ |"]
- result: Continuum flux density at 251.826 GHz (spw 2) = 270.0 ± 1.4 mJy [Table 1: "| 2 | 251.826 | 468.75 | 1.16 | $19.3\times16.7$ | 0.52 | $270.0 \pm 1.4$ |"]
- result: Continuum flux density at 252.471 GHz (spw 3) = 271.8 ± 1.0 mJy [Table 1: "| 3 | 252.471 | 468.75 | 1.16 | $19.3\times16.7$ | 0.47 | $271.8 \pm 1.0$ |"]
- result: Continuum flux density at 253.703 GHz (spw 4) = 273.7 ± 1.4 mJy [Table 1: "| 4 | 253.703 | 468.75 | 1.15 | $19.1\times16.5$ | 0.52 | $273.7 \pm 1.4$ |"]
- result: Continuum flux density at 265.886 GHz (spw 5) = 301.5 ± 1.6 mJy [Table 1: "| 5 | 265.886 | 468.75 | 1.10 | $18.4\times15.8$ | 0.59 | $301.5 \pm 1.6$ |"]
- result: Continuum flux density at 266.943 GHz (spw 6) = 305.6 ± 1.5 mJy [Table 1: "| 6 | 266.943 | 468.75 | 1.10 | $18.4\times15.8$ | 0.55 | $305.6 \pm 1.5$ |"]
- result: Continuum flux density at 267.198 GHz (spw 7) = 306.0 ± 1.5 mJy [Table 1: "| 7 | 267.198 | 468.75 | 1.10 | $18.3\times15.8$ | 0.60 | $306.0 \pm 1.5$ |"]
- result: Continuum flux density at 267.720 GHz (spw 8) = 306.2 ± 1.3 mJy [Table 1: "| 8 | 267.720 | 937.50 | 1.09 | $18.2\times15.8$ | 0.63 | $306.2 \pm 1.3$ |"]
- result: Continuum flux density at 268.168 GHz (spw 9) = 307.8 ± 1.3 mJy [Table 1: "| 9 | 268.168 | 937.50 | 1.09 | $18.1\times15.7$ | 0.65 | $307.8 \pm 1.3$ |"]
- result: Continuum flux frequency power-law spectral index = 2.08 ± 0.03 dimensionless [Continuum: "As Fig. [2](#cont_flux_spec) shows, the continuum flux measurements can be well fit with a power law, $F_{\nu} \propto \nu^{2.08 \pm 0.03}$."]
- result: Millimeter continuum brightness temperature across 9 spws = 2130–2170 ± not stated K [Continuum: "The uniform elliptical disk fitting in nine spectral windows results in brightness temperatures of 2130–2170 K over the millimeter continuum stellar disk."]
- limitation (authors): Missing short spacings (largest recoverable scale of 190 mas) cause smooth, extended emission on scales larger than ~190 mas (radius >95 mas) to be resolved out, preventing conclusions on large-scale kinematics and global symmetry of Si17O… [Conclusions: "However, diffuse, smooth emission on scales larger than $\sim$190 mas is missing due to the lack of short baselines, which prevented us from drawing a conclusion on the large-scale kinematics."]
- limitation (authors): The 1D spherical LTE model of the SiO lines is simplified; full non-LTE radiative transfer modeling is beyond the scope of the paper, and the model cannot distinguish between a shock-induced density jump and Si depletion onto dust grains a… [Modeling of the $^{30}$SiO $\varv = 1$ …: "We assumed LTE primarily for simplicity, because full non-LTE radiative transfer modeling is beyond the scope of this paper."]
- limitation (authors): Dynamic range limitations in channels containing strong 29SiO v=2 J=6-5 maser emission (~18 Jy/beam) increase the RMS noise up to 2.7 mJy/beam. [Observations and data reduction: "Due to the dynamic range limit, the RMS noise is much higher in the channels containing the strongest emission, up to 2.7 mJy/beam."]
- not stated (card): Exact frequency ranges or channel indices selected as line-free channels in each of the 9 spectral windows for continuum visibility extraction and uvcontsub; tclean image size (number of pixels), stopping threshold, niter, and masking strategy during self-calibration and final cube imaging; Exact beam/aperture size used when extracting spatially resolved single-position spectra (whether single pi…

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

### 2021A&A...647A..87L: The prebiotic molecular inventory of Serpens SMM1. I. An investigation of the isomers CH<SUB>3</SUB>NCO and HOCH<SUB>2</SUB>CN (2021; astrochemistry, star_formation; observational_alma_primary)
- question: Investigate the interstellar chemistry of cyanides (CN) and isocyanates (NCO) and the reservoir of interstellar prebiotic molecules via the C2H3NO isomers CH3NCO and HOCH2CN towards Serpens SMM1-a and IRAS 16293B.
- step 1: Continuum subtraction and spectrum extraction for SMM1-a and IRAS 16293B
  - method: Image spectral windows without continuum subtraction, run STATCONT corrected sigma-clipping to locate line-free channels, run CASA uvcontsub in the uv-plane, re-image, and extract spectra at SMM1-a continuum peak and IRAS 16293B offset pos… [2.1. Observations and spectra of Serpen…: "Therefore, the STATCONT outputs were used to identify the line-free channels in the spectra and the continuum was subtracted in the uv-plane with the uvcontsub task in CASA."] [2.1. Observations and spectra of Serpen…: "From the resulting datacube, the SMM1a hot core spectrum was extracted towards the peak continuum position α J2000 = 18:29:49.793, δ J2000 = +1.15.20.200."]
  - software: CASA, STATCONT
  - parameter: SMM1-a extraction position: α_J2000 = 18:29:49.793, δ_J2000 = +1.15.20.200 [2.1. Observations and spectra of Serpen…: "From the resulting datacube, the SMM1a hot core spectrum was extracted towards the peak continuum position α J2000 = 18:29:49.793, δ J2000 = +1.15.20.200."]
  - parameter: Line-free bandwidth fraction: ≥20% (10% in two spectral windows) [2.1. Observations and spectra of Serpen…: "Line-free channels are sparse, but for most spectral windows, at least 20% of the bandwidth was given as input to the uvcontsub task, with the exception of two spectral windows, where only 10% of the bandwidth was line-free."]
  - assumption: SMM1-a background temperature T_bg = 5.2 K from average continuum flux density (0.41 mJy beam^-1); IRAS 16293B T_BG = 21 K (full-beam offset) and 52 K (half-beam offset) [2.1. Observations and spectra of Serpen…: "From the average continuum flux density (0.41 mJy beam −1 ), the background temperature was determined to be ∼5.2 K."] [2.2. PILS observations and spectra of I…: "At the full-beam offset position T BG = 21 K, while at the half-beam offset position it is T BG = 52 K."]
- limitation (authors): Observational spatial scales and extraction positions differ between SMM1-a (~500 au, continuum peak) and IRAS 16293B (~70 au, full-beam offset), which may affect molecular ratio comparisons. [4. Discussion: "Therefore, the chemical inventory of SMM1-a and the involved chemical processes are investigated on a much larger spatial scale of roughly 500 au, compared to about 70 au for IRAS 16293B."]
- limitation (authors): Baseline subtraction in IRAS 16293B is challenging due to line-richness and can be over-subtracted, causing dips at some HOCH2CN line positions; two temperature components may also be blended. [3.2. IRAS 16293B: "We note that due to the line-richness of the source the baseline subtraction is challenging and in some cases, it can be oversubtracted."]
- limitation (authors): D2CO lines in SMM1-a are blended and the D/H ratio of H2CO in SMM1-a is unknown, preventing a firm conclusion on the H2CO correlation with HOCH2CN. [4.1. SMM1-a: A HOCH 2 CN-rich source: "However, care needs to be taken with this interpretation, since the D 2 CO spectral lines in the SMM1-a spectrum are blended and thus there is a large uncertainty on its column density. At the same time, the D/H ratio of H 2 CO is not known in SMM1-a, which introduces another source of uncertainty."]
- not stated (card): Whether calibration of SMM1 data was pipeline or manual; Whether self-calibration was applied to the SMM1 data; Exact pixel/cell size and image dimensions used in CASA cleaning for SMM1; Clean stopping threshold and masking strategy in CASA; Polynomial fit order used in CASA uvcontsub; Exact J2000 coordinates of the full-beam and half-beam offset positions in IRAS 16293B

### 2026ApJ..1000..141K: First Determination of the Cosmic Microwave Background Radiation Temperature at z = 0.68 Using Molecular Absorption Lines (2026; cosmology, agn_and_quasars, astrochemistry; archival_reuse)
- question: What is the cosmic microwave background (CMB) radiation temperature at z = 0.68 derived from rotational molecular absorption lines toward the lensed quasar B0218+357, and is it consistent with the standard Big Bang cosmological model?
- step 2: Extract absorption spectra toward lensed quasar component A
  - method: Direct visibility fitting in the Fourier plane using a two-point-source model: (1) determine peak positions from continuum visibilities, (2) fit visibilities in each spectral channel at fixed positions [Data Processing: "The spectra toward components A and B of B0218+357 were extracted using the Python-based package $\texttt{UVMULTIFIT}$ (cite: MartiVidal_2014) by directly fitting the visibilities for each component."] [Data Processing: "We adopted a two-point-source model and obtained the spectra through a two-step procedure: (1) determining the peak positions using only the continuum visibilities, and (2) fitting the visibilities in each spectral channel at those positions."]
  - software: UVMULTIFIT
  - parameter: two-point-source model with separation ~0.3 arcsec [Data Processing: "the simple and well-known two-point-source geometry of this system, with a separation of $\!\sim\!0{\overset{\prime\prime}{.}}3$ on the sky, enables spectral extraction via visibility fitting in the Fourier plane (cite: MartiVidal_2014; Wallstrom_2019)."]
  - assumption: Two compact lensed components can be modeled as two point sources; no significant time variability over the 9-month observation interval [Data Processing: "We adopted a two-point-source model and obtained the spectra through a two-step procedure"] [Time Variability: "On the basis of these considerations, we assume that no significant variability in the absorption strength occurred over this short period."]
  - fitting: Visibility-plane fitting per spectral channel [Data Processing: "(1) determining the peak positions using only the continuum visibilities, and (2) fitting the visibilities in each spectral channel at those positions."]
- limitation (authors): The Band 3 and Band 4 observations were separated by ~9 months (October 2016 to July 2017) without simultaneous millimeter monitoring, though a few percent variability would shift T_CMB by < 0.1 K. [Time Variability: "The Band 3 and Band 4 observations used in this study are separated by approximately nine months (from October 2016 to July 2017)"]
- limitation (authors): The -6 km/s component cannot constrain f_c due to lack of saturation, leaving its T_ex uncertain. [HCN, HCO+, and HNC: "In contrast, the $-6\,\mathrm{km\,s^{-1}}$ component shows no evidence of saturation, preventing a meaningful constraint on $f_\mathrm{c}$ in that velocity range; consequently, the associated $T_\mathrm{ex}$ remains uncertain."]
- limitation (authors): H13CN and H13CO+ transitions have low S/N (~3), limiting their statistical significance. [Summary and Future Prospects: "The excitation temperatures derived from H$^{13}$CN and H$^{13}$CO$^{+}$ are also consistent with the prediction of the standard Big Bang model, although their statistical significance is limited by the lower S/N of the data."]
- not stated (card): Exact CASA version and UVMULTIFIT version used for data reduction and visibility fitting; Rest frequencies, Einstein A coefficients, level energies, and partition function values/tables adopted for HCN, HCO+, HNC, H13CN, and H13CO+; Exact velocity ranges defining line-free continuum channels used in UVMULTIFIT to determine peak positions and normalize the absorption spectra; Explicit mathematical…

### 2015MNRAS.452...88K: ALMA detection of a disc-dominated [C II] emission line at z=4.6 in the luminous QSO J1554+1937 (2015; agn_and_quasars, high_z_galaxies; observational_alma_primary)
- question: What is the origin (rotating disc vs bulge) of the broad [C II] line in the luminous z=4.6 QSO J1554+1937, and how does this affect its position relative to the local M-sigma relation?
- step 2: Measure continuum and line sizes and fluxes
  - method: Gaussian fit in the uv-plane with uvmodelfit for continuum and line; moment 0, 1, 2 maps [3 Data Analysis: "we performed a Gaussian fit to the data in the UV-plane using the CASA task `uvmodelfit`"]
  - software: CASA, uvmodelfit
  - parameter: moment 0 over 337.3-338.2 GHz; moment 1 pixels with S/N ≥4 of ~2 mJy rms [3 Data Analysis: "using the frequency range 337.3–338.2 GHz"]
  - fitting: Gaussian in uv-plane [Data Analysis: "To estimate the source size, we performed a Gaussian fit to the data in the UV-plane using the CASA task `uvmodelfit`"]
  - validation: Moment 0 S/N ~10 at edges indicates velocity gradient is real [3 Data Analysis: "In the moment 0 map, the S/N is $\sim10$ at the edges of this region, indicating that this gradient is real."]
- result: [C II] FWHM = 735 ± not stated km/s [3 Data Analysis: "The FWHM is 735 km s$^{-1}$."]
- result: [C II] redshift = 4.627 ± not stated dimensionless [3 Data Analysis: "The actual redshift of the line is approximately 4.627"]
- result: Continuum flux density at ~344 GHz = 12.70 ± 0.12 mJy [3 Data Analysis: "The integrated flux density resulting from the fit is $12.70\pm0.12$ mJy at $\sim344$ GHz."]
- result: [C II] integrated flux = 9.40 ± 0.40 Jy km/s [3 Data Analysis: "The integrated flux density is to be $9.40\pm0.40$ Jy km s$^{-1}$"]
- result: [C II] line luminosity = 5.9e9 ± not stated Lsun [3 Data Analysis: "corresponding to a line luminosity of $5.9\times10^9~\mathrm{L}_\odot$"]
- limitation (authors): Low spatial resolution prevents determining inclination and detailed kinematics [4.4: "The poor spatial resolution prevents us from determining the inclination"]
- not stated (card): Channel width and cell/image size used in clean; Line-free channels used for continuum subtraction and continuum map; Clean threshold, masking and iterations; Self-calibration solution interval; How the moment maps and 20 per cent half-width were measured (visual); Details of the line profile model fitting/inclination integration; Number of execution blocks and observing date

### 2026A&A...707A.255C: ALMA Band 1 observations of the ρ Oph W filament: I. Enhanced power from excess microwave emission at high spatial frequencies (2026; milky_way_ism, astrochemistry; observational_alma_primary)
- question: Reveal the detailed morphology of the excess microwave emission (EME) signal in the rho Oph W filament free from imaging priors, constrain the spectral index of the high-frequency drop, and search for fine structure (PAH combs and CRRLs) i…
- step 1: Fit and subtract bright point sources in the uv-plane
  - method: Bin visibilities into 60-channel bins with CASA mstransform; fit positions, flux densities at 40.15 GHz, and spectral indices for SR 4, ISO-Oph-17, and DoAr 21 in each execution block separately using pyralysis and iminuit; subtract point-… [Point-source subtraction: "These were subtracted in the $uv$ plane, handling the raw (non-gridded) visibility data with the `pyralysis` package (cite: casassus_carcamo2022MNRAS.513.5790C)."] [Point-source subtraction: "In order to reduce the volume of the data, we averaged the visibilities into 60 channel bins (using `CASA` task ` mstransform`)."]
  - software: CASA mstransform, pyralysis, iminuit
  - parameter: reference frequency nu_0 = 40.15 GHz; 60-channel bins; 4 nearest fields used for DoAr 21, closest field for SR 4 and ISO-Oph-17 [Point-source subtraction: "We first fit for the point source positions, their flux densities, $F_{\nu_\circ}$, at the reference frequency, $\nu_\circ = 40.15\,$GHz (corresponding to the centre frequency of the four spectral windows), and spectral indices, $\alpha$."] [Point-source subtraction: "The point-source fits to DoAr 21 required the incorporation of the four nearest fields to reach thermal residuals."]
  - assumption: Airy disk approximation to the ALMA primary beam [Point-source subtraction: "We attribute the imperfect point-source subtraction for DoAr 21 in single-field point-source fits (with $\lesssim 5\%$ residuals) to the accuracy of the Airy disk approximation to the ALMA primary beam."]
  - fitting: chi-squared minimisation in uv-plane with iminuit using the Hessian approximation for uncertainties [Point-source subtraction: "We used the `iminuit` package (cite: James:1975dr; iminuit), using the Hessian approximation to estimate uncertainties."]
  - validation: Extracted point-source flux densities in each channel at best-fit positions and verified consistency with spectral index fits [Point-source subtraction: "As a sanity check on the point-source fits (and provided with their best-fit positions, $\vec{x_\circ}$), we also extracted point-source flux densities in each channel."] [Point-source subtraction: "are consistent with the channel flux densities."]
- step 4: Extract intra-band diffuse emission spectrum and spectral index
  - method: Simulate visibilities on the pure-chi2 deconvolved model image template I^m using pyralysis, perform weighted linear regression in the uv-plane at each frequency channel (or 120-channel bin) to get slope a_nu, and fit a power law in freque… [Extraction of the intra-band diffuse em…: "Instead, we opt for cross-correlation with a template image, for which we use the deconvolved model image, $I^m$, of Fig. 1c, assuming a flat spectral index."] [Extraction of the intra-band diffuse em…: "Example spectra are shown in Fig. 5 for the 120-channel average and extracted over regions along the filament."]
  - software: pyralysis
  - parameter: 120-channel average (16 channels); reference frequency nu_0 = 36.63 GHz; pure-chi2 template (lambda = 0) [Extraction of the intra-band diffuse em…: "Example spectra are shown in Fig. 5 for the 120-channel average and extracted over regions along the filament."] [Extraction of the intra-band diffuse em…: "The slopes $a_{\nu_\circ}$ are slightly biased downwards, with $a_{\nu_\circ} = 0.96\pm0.005$ for $\nu_\circ = 36.63\,$GHz averaged over all fields, which results from the use of the pure-$\chi^2$ model image as template."]
  - assumption: Template image I^m has flat spectral index across the band [Extraction of the intra-band diffuse em…: "Instead, we opt for cross-correlation with a template image, for which we use the deconvolved model image, $I^m$, of Fig. 1c, assuming a flat spectral index."]
  - fitting: Analytic weighted least-squares for linear regression slope a_nu, followed by power-law fit a_nu ~ a_nu0 (nu/nu_0)^alpha_d [Extraction of the intra-band diffuse em…: "We search for a linear-regression slope, $a_\nu$, such that $$\begin{equation} I_\nu = a_\nu I^m, \end{equation}$$ by simulating visibilities on the template image, $V^m_{k,l}$ (cite: casassus_carcamo2022MNRAS.513.5790C), and minimising $$\begin{equation} \chi^2 = \sum_{k=1}^{K} \sum_{l=1}^{M_k} \omega_{k,l} \left| V_…"] [Extraction of the intra-band diffuse em…: "Power-law fits for $$\begin{equation} a_\nu \sim a_{\nu_\circ} (\nu/ \nu_\circ)^{\alpha_d}, \label{eq:diffusespecfit} \end{equation}$$ yield varying spectral indices, $\alpha_d$, over different regions."]
  - validation: Tested spectral extraction on simulated Band 1 visibilities from the IRAC 3.6 um template with input alpha=0, confirming lambda=0 recovers alpha=0 within 1 sigma while lambda=0.1 introduces a bias (alpha = -0.26 +/- 0.09) [Band 1 flux loss and IRAC simulations: "We recover the input spectral index ($\alpha = 0$) within 1$\sigma$ in all cases."] [Band 1 flux loss and IRAC simulations: "In contrast, the entropy-regularised images (with $\lambda=0.1$) yield biased spectral indices, for example $\alpha = -0.26\pm0.09$ for fields 7-10."]
- result: Band 1 diffuse EME spectral index (all fields) = -0.78 ± 0.05 dimensionless [abstract: "It follows a spectral index $\alpha = -0.78\pm0.05$, in frequency, with some variations along the filament."]
- result: Band 1 diffuse EME spectral index (fields 5,6) = -0.16 ± 0.14 dimensionless [Extraction of the intra-band diffuse em…: "The spectral index variations are very significant along the filament, from $\alpha_d = -0.16\pm0.14$ in fields 5 and 6 (south-east of the filament), to $\alpha_d = -1.06\pm0.08$ in fields 7 to 10 (north-west of the filament)."]
- result: Band 1 diffuse EME spectral index (fields 7-10) = -1.06 ± 0.08 dimensionless [Extraction of the intra-band diffuse em…: "The spectral index variations are very significant along the filament, from $\alpha_d = -0.16\pm0.14$ in fields 5 and 6 (south-east of the filament), to $\alpha_d = -1.06\pm0.08$ in fields 7 to 10 (north-west of the filament)."]
- result: Band 1 diffuse EME spectral index (field 6) = -0.24 ± 0.17 dimensionless [Spectral energy distribution: "| 6 | 6.1 | 0.33 | 3.9 | 2.3 | 32 | 89 | 801 | 1447 | 625 | 270 | 107 | 55 | $-0.24\pm0.17$ | 130 | 72 |"]
- result: Band 1 diffuse EME spectral index (fields 7-9) = -1.05 ± 0.08 dimensionless [Spectral energy distribution: "| 7-9 | 12.5 | 0.40 | 7.7 | 4.6 | 64 | 182 | 1525 | 2495 | 1009 | 423 | 164 | 125 | $-1.05\pm0.08$ | 265 | 146 |"]
- result: SR 4 combined flux density at 40.15 GHz = 893 ± 16 uJy [Point-source subtraction: "| | ($893\pm16$)/($2.27\pm0.32$)$^{a}$ |"]
- result: SR 4 combined spectral index = 2.27 ± 0.32 dimensionless [Point-source subtraction: "| | ($893\pm16$)/($2.27\pm0.32$)$^{a}$ |"]
- result: ISO-Oph 17 combined flux density at 40.15 GHz = 2588 ± 29 uJy [Point-source subtraction: "| | ($2588 \pm 29$)/($3.09\pm 0.20$)$^{a}$ |"]
- result: ISO-Oph 17 combined spectral index = 3.09 ± 0.20 dimensionless [Point-source subtraction: "| | ($2588 \pm 29$)/($3.09\pm 0.20$)$^{a}$ |"]
- result: DoAr 21 flux density at 40.15 GHz (2024-03-11) = 21462 ± 26 uJy [Point-source subtraction: "| DoAr 21 | ($21462\pm26$)/($-0.35\pm0.02$) | ($18731\pm 25$) / ($-0.502\pm 0.02$) | ($12819\pm 28$) / ($-0.06\pm0.04$ ) |"]
- result: DoAr 21 flux density at 40.15 GHz (2024-03-12) = 18731 ± 25 uJy [Point-source subtraction: "| DoAr 21 | ($21462\pm26$)/($-0.35\pm0.02$) | ($18731\pm 25$) / ($-0.502\pm 0.02$) | ($12819\pm 28$) / ($-0.06\pm0.04$ ) |"]
- result: DoAr 21 flux density at 40.15 GHz (2024-03-13) = 12819 ± 28 uJy [Point-source subtraction: "| DoAr 21 | ($21462\pm26$)/($-0.35\pm0.02$) | ($18731\pm 25$) / ($-0.502\pm 0.02$) | ($12819\pm 28$) / ($-0.06\pm0.04$ ) |"]
- limitation (authors): Severe interferometric flux loss (~70% missing flux; only ~29-30% recovered over the whole mosaic) due to missing short spacings in the 12 m array data. [Imaging: "As described in Appendix 5, the flux recovered over the whole mosaic is $\sim$30%."]
- limitation (authors): Resolved gradients in physical conditions and SEDs on the ~7'' synthesised beam scale cannot be constrained without 7 m (ACA) data; SEDs and spectral indices can only be reliably extracted on primary-beam scales. [Comparison with the ATCA mosaics: "The present ALMA data cannot, however, be used to constrain resolved gradients in physical conditions across the PDR."]
- limitation (authors): Pure-chi2 imaging (lambda=0) fits noise to some extent, creating positive-definite noise in the template that slightly biases the normalisation slope downwards (a_nu0 = 0.96 +/- 0.005). [Extraction of the intra-band diffuse em…: "The slopes $a_{\nu_\circ}$ are slightly biased downwards, with $a_{\nu_\circ} = 0.96\pm0.005$ for $\nu_\circ = 36.63\,$GHz averaged over all fields, which results from the use of the pure-$\chi^2$ model image as template."]
- not stated (card): Exact J2000 coordinates of the 16 mosaic pointing centres; Best-fit J2000 coordinates for the three subtracted point sources (SR 4, ISO-Oph-17, DoAr 21); Exact rest frequencies used to stack the C56alpha to C53alpha carbon recombination lines; Stopping criterion or niter/threshold used in the CASA-tclean comparison imaging

### 2024A&A...682A.186L: Feeding and feedback processes in the Spiderweb proto-intracluster medium (2024; galaxy_clusters_and_sz, high_z_galaxies; observational_alma_primary)
- question: Derive the thermodynamic profiles of the Spiderweb proto-ICM (z=2.16), test for a cool core, constrain the classical mass deposition rate and estimate the feedback energy budget, by combining Chandra X-ray density with ALMA SZ pressure
- step 5: Reconstruct SZ pressure profile from ALMA+ACA visibilities
  - method: Bayesian forward modelling of uv-plane visibilities with a line-of-sight integrated gNFW pressure model fitted jointly with a radio-galaxy point-component model; centroid fixed to the X-ray centroid; models combined with Bayesian Model Ave… [5 SZ and X-ray combined analysis: "the SZ distribution is obtained as the line-of-sight integral of a generalized Navarro-Frenk-White (NFW, (cite: 2007Nagai)) pressure distribution, with scaling parameters and radial slopes fixed to match specific formulations from the literature"] [5 SZ and X-ray combined analysis: "we inferred the SZ component jointly with the radio galaxy model, defined by the optimal, ordered set of point-like components, as in (cite: 2023DiMascolo)"]
  - software: dynesty
  - parameter: uv upper threshold 65 klambda [5 SZ and X-ray combined analysis: "We also consistently imposed an upper threshold of $65~\mathrm{k\lambda}$ to the analysed visibilities to make the extended radio galaxy unresolved in the direction orthogonal to the jet axis."]
  - parameter: SZ centroid fixed to X-ray centroid so that only the mass term (M500) is free per pressure model [5 SZ and X-ray combined analysis: "we did, however, fix the centroid position of the SZ model component to match the one derived by modeling the soft-band X-ray surface brightness distribution"] [Pressure models: "In such a way, the parameter set for each parameter reduces to the mass term only."]
  - assumption: Eight literature gNFW pressure profiles considered (A10 UP/MD, M14 UP/NCC, L15 REF/8.0/8.5, G17 EXT) [Pressure models: "the self-similar extended pressure model by (cite: 2017Gupta)"]
  - fitting: Nested sampling with dynesty; priors and likelihood details not stated [5 SZ and X-ray combined analysis: "The posterior exploration was performed using the nested sampling algorithm (cite: 2004Skilling; 2022Ashton), as implemented in the `dynesty` package (cite: dynesty; 2022Koposov)."]
  - validation: Model parameters statistically consistent with Di Mascolo et al. 2023; BMA profile used as reference with model variance propagated [5 SZ and X-ray combined analysis: "the parameters for each of the reconstructed models are found to be statistically consistent with the ones reported in (cite: 2023DiMascolo)"] [5 SZ and X-ray combined analysis: "we propagate the variance between the various pressure models in the marginalized posterior distribution"]
- result: M500 for A10 UP pressure model = 2.47 ± +0.44/-0.54 1e13 Msun [Table 1: "$2.47\substack{+0.44\\-0.54}$"]
- result: M500 for A10 MD pressure model = 2.01 ± +0.39/-0.49 1e13 Msun [Table 1: "$2.01\substack{+0.39\\-0.49}$"]
- result: M500 for M14 UP pressure model = 2.82 ± +0.53/-0.65 1e13 Msun [Table 1: "$2.82\substack{+0.53\\-0.65}$"]
- result: M500 for M14 NCC pressure model = 2.84 ± +0.53/-0.66 1e13 Msun [Table 1: "$2.84\substack{+0.53\\-0.66}$"]
- result: M500 for L15 REF pressure model = 2.59 ± +0.42/-0.48 1e13 Msun [Table 1: "$2.59\substack{+0.42\\-0.48}$"]
- result: M500 for L15 8.0 pressure model = 4.30 ± +0.55/-0.68 1e13 Msun [Table 1: "$4.30\substack{+0.55\\-0.68}$"]
- result: M500 for L15 8.5 pressure model = 6.54 ± +0.78/-0.95 1e13 Msun [Table 1: "$6.54\substack{+0.78\\-0.95}$"]
- result: M500 for G17 EXT pressure model = 2.20 ± +0.39/-0.55 1e13 Msun [Table 1: "$2.20\substack{+0.39\\-0.55}$"]
- limitation (authors): Diffuse emission within 2 arcsec of the AGN is not observationally constrained [2.1 Chandra X-ray data: "the surface brightness of the diffuse component within a radius of 2 arcsec is not observationally constrained and was treated as a free parameter"]
- limitation (authors): SZ normalisation may be underestimated because of interferometric filtering of large scales [5.2 Pressure and temperature profiles: "the normalization of the SZ signal may be underestimated compared to the actual pressure distribution due to the impact of the large-scale interferometric filtering"]
- limitation (authors): Low significance of SZ and X-ray signals limits detailed morphological comparison [4 SZ and X-ray combined analysis: "The low significance of both the SZ signal and the X-ray emission from the proto-ICM inevitably limits the possibility of performing a detailed morphological comparison."]
- not stated (card): CASA version and pipeline version for the Band 3 and Band 4 calibration; Flux, bandpass and phase calibrators and the flux-scale uncertainty; Exact Band 4 frequency setup and number of ALMA/ACA execution blocks used; dynesty settings (live points, stopping criterion) and the priors on M500 and radio-galaxy components; Radio-galaxy point-component model and how the 'optimal ordered set' was chosen…

## All papers in this technique

- 2012ApJ...757..129R (2012): Kinematics of the CO Gas in the Inner Regions of the TW Hya Disk
- 2013A&A...549L...3P (2013): Warm water deuterium fractionation in IRAS 16293-2422. The high-resolution ALMA and SMA view
- 2013A&A...558A.123M (2013): Probing the jet base of the blazar PKS 1830-211 from the chromatic variability of its lensed images. Serendipitous ALMA observations of a s…
- 2013ApJ...762L..21M (2013): Millimeter Emission Structure in the First ALMA Image of the AU Mic Debris Disk
- 2013ApJ...765L..14Q (2013): First Detection of c-C<SUB>3</SUB>H<SUB>2</SUB> in a Circumstellar Disk
- 2013ApJ...773...44W (2013): Star Formation and Gas Kinematics of Quasar Host Galaxies at z ~ 6: New Insights from ALMA
- 2013ApJ...774...16R (2013): A Spatially Resolved Vertical Temperature Gradient in the HD 163296 Disk
- 2013ApJ...777L..25M (2013): ALMA Continuum Observations of a 30 Myr Old Gaseous Debris Disk around HD 21997
- 2013Natur.495..344V (2013): Dusty starburst galaxies in the early Universe as revealed by gravitational lensing
- 2013PASJ...65..100I (2013): Submillimeter ALMA Observations of the Dense Gas in the Low-Luminosity Type-1 Active Nucleus of NGC1097
- 2013Sci...341..630Q (2013): Imaging of the CO Snow Line in a Solar Nebula Analog
- 2014A&A...562A..67G (2014): ALMA reveals a warm and compact starburst around a heavily obscured supermassive black hole at z = 4.75
- 2014A&A...563A.136M (2014): UVMULTIFIT: A versatile tool for fitting astronomical radio interferometric data
- 2014A&A...566A..74L (2014): ALMA observations of the kinematics and chemistry of disc formation
- 2014A&A...566A.112M (2014): An ALMA Early Science survey of molecular absorption lines toward PKS 1830-211. Analysis of the absorption profiles
- 2014A&A...566L...6M (2014): Detection of chloronium and measurement of the <SUP>35</SUP>Cl/<SUP>37</SUP>Cl isotopic ratio at z = 0.89 toward PKS 1830-211
- 2014A&A...568L...5C (2014): The ALMA view of the protostellar system HH212. The wind, the cavity, and the disk
- 2014A&A...570L..14R (2014): The wonderful complexity of the Mira AB system
- 2014ApJ...783L..13P (2014): Large-scale Asymmetries in the Transitional Disks of SAO 206462 and SR 21
- 2014ApJ...787...42C (2014): An ALMA Continuum Survey of Circumstellar Disks in the Upper Scorpius OB Association
- 2014ApJ...788L..34P (2014): Resolved Images of the Protoplanetary Disk around HD 100546 with ALMA
- 2014ApJ...791...20R (2014): Brown Dwarf Disks with ALMA
- 2014ApJ...791...42Z (2014): Comparison of the Dust and Gas Radial Structure in the Transition Disk [PZ99] J160421.7-213028
- 2014ApJ...791L...6W (2014): ALMA Hints at the Presence of two Companions in the Disk around HD 100546
- 2014ApJ...792L...2C (2014): Mapping the Release of Volatiles in the Inner Comae of Comets C/2012 F6 (Lemmon) and C/2012 S1 (ISON) Using the Atacama Large Millimeter/Su…
- 2014ApJ...796...82Z (2014): Spectral and Morphological Analysis of the Remnant of Supernova 1987A with ALMA and ATCA
- 2014ApJ...797...27F (2014): Revealing H<SUB>2</SUB>D<SUP>+</SUP> Depletion and Compact Structure in Starless and Protostellar Cores with ALMA
- 2014Natur.511..567J (2014): Misaligned protoplanetary disks in a young binary star system
- 2015A&A...577L...4V (2015): Resolving the stellar activity of the Mira AB binary with ALMA
- 2015A&A...582A..91C (2015): Exploring the molecular chemistry and excitation in obscured luminous infrared galaxies. An ALMA mm-wave spectral scan of NGC 4418
- 2015A&A...582L...4M (2015): Detection of extragalactic argonium, ArH<SUP>+</SUP>, toward PKS 1830-211
- 2015A&A...583A..66H (2015): Probing the final stages of protoplanetary disk evolution with ALMA
- 2015A&A...584A..16P (2015): Testing particle trapping in transition disks with ALMA
- 2015ApJ...798...85P (2015): CO Gas Inside the Protoplanetary Disk Cavity in HD 142527: Disk Structure from ALMA
- 2015ApJ...798..124R (2015): ALMA Observations of the Debris Disk around the Young Solar Analog HD 107146
- 2015ApJ...798L..23K (2015): An ALMA Disk Mass for the Candidate Protoplanetary Companion to FW Tau
- 2015ApJ...799...81S (2015): The SCUBA-2 Cosmology Legacy Survey: ALMA Resolves the Rest-frame Far-infrared Emission of Sub-millimeter Galaxies
- 2015ApJ...805...21C (2015): Gas Inside the 97 AU Cavity around the Transition Disk Sz 91
- 2015ApJ...806..154C (2015): A Disk-based Dynamical Mass Estimate for the Young Binary AK Sco
- 2015ApJ...806..260F (2015): Band-9 ALMA Observations of the [N II] 122 μm Line and FIR Continuum in Two High-z galaxies.
- 2015ApJ...808...36M (2015): New Measurements of the Radio Photosphere of Mira Based on Data from the JVLA and ALMA
- 2015ApJ...808..102K (2015): Resolving Protoplanetary Disks at Millimeter Wavelengths with CARMA
- 2015ApJ...808L...3A (2015): The 2014 ALMA Long Baseline Campaign: First Results from High Angular Resolution Observations toward the HL Tau Region
- 2015ApJ...810..133I (2015): Compact Starbursts in z ∼ 3-6 Submillimeter Galaxies Revealed by ALMA
- 2015ApJ...810L...7V (2015): A Concentration of Centimeter-sized Grains in the Ophiuchus IRS 48 Dust Trap
- 2015ApJ...811...39I (2015): ALMA Observations of the Submillimeter Dense Molecular Gas Tracers in the Luminous Type-1 Active Nucleus of NGC 7469
- 2015ApJ...811..124S (2015): Sub-kiloparsec Imaging of Cool Molecular Gas in Two Strongly Lensed Dusty, Star-forming Galaxies
- 2015ApJ...811L...3T (2015): SXDF-ALMA 1.5 arcmin<SUP>2</SUP> Deep Survey: A Compact Dusty Star-forming Galaxy at z = 2.5
- 2015ApJ...812...43B (2015): HerMES: ALMA Imaging of Herschel-selected Dusty Star-forming Galaxies
- 2015ApJ...812..129Y (2015): No Keplerian Disk &gt;10 AU Around the Protostar B335: Magnetic Braking or Young Age?
- 2015ApJ...812L..23S (2015): A Higher Efficiency of Converting Gas to Stars Pushes Galaxies at z ∼ 1.6 Well Above the Star-forming Main Sequence
- 2015ApJ...813...99F (2015): Weak Turbulence in the HD 163296 Protoplanetary Disk Revealed by ALMA CO Observations
- 2015ApJ...814...53G (2015): Cyanide Photochemistry and Nitrogen Fractionation in the MWC 480 Disk
- 2015MNRAS.452...88K (2015): ALMA detection of a disc-dominated [C II] emission line at z=4.6 in the luminous QSO J1554+1937
- 2015MNRAS.453L..83M (2015): ALMA and Herschel reveal that X-ray-selected AGN and main-sequence galaxies have different star formation rate distributions
- 2015Natur.520..198O (2015): The comet-like composition of a protoplanetary disk as revealed by complex cyanides
- 2015Sci...348..311M (2015): A strong magnetic field in the jet base of a supermassive black hole
- 2016A&A...586A..45S (2016): Star formation efficiency along the radio jet in Centaurus A
- 2016A&A...586A..99H (2016): Steepening of the 820 μm continuum surface brightness profile signals dust evolution in TW Hydrae's disk
- 2016A&A...586L...1G (2016): The shadow of the Flying Saucer: A very low temperature for large dust grains
- 2016A&A...588A.112G (2016): Dust properties across the CO snowline in the HD 163296 disk from ALMA and VLA observations
- 2016A&A...589L...5M (2016): Detection of extragalactic CF<SUP>+</SUP> toward PKS 1830-211. Chemical differentiation in the absorbing gas
- 2016A&A...590A..33P (2016): Constraining the physical structure of the inner few 100 AU scales of deeply embedded low-mass protostars
- 2016A&A...590A.127W (2016): Resolving the extended atmosphere and the inner wind of Mira (o Ceti) with long ALMA baselines
- 2016A&A...591A..73G (2016): ALMA finds dew drops in the dusty spider's web
- 2016A&A...591A.108O (2016): Azimuthal asymmetries in the debris disk around HD 61005. A massive collision of planetesimals?
- 2016A&A...593A..61M (2016): Dual differential polarimetry. A technique to recover polarimetric information from dual-polarization observations
- 2016A&A...593A.111T (2016): Brown dwarf disks with ALMA: Evidence for truncated dust disks in Ophiuchus
- 2016A&A...595L...4L (2016): Hot methanol from the inner region of the HH 212 protostellar system
- 2016A&A...596A..75S (2016): Characterizing elusive, faint dusty star-forming galaxies: a lensed, optically undetected ALMA galaxy at z 3.3
- 2016A&A...596A..88L (2016): ALMA observations of the <ASTROBJ>Th 28</ASTROBJ> protostellar disk. A new example of counter-rotation between disk and optical jet
- 2016ApJ...816...25P (2016): Dust and Gas in the Disk of HL Tauri: Surface Density, Dust Settling, and Dust-to-gas Ratio
- 2016ApJ...816...27S (2016): Resolved Millimeter-wavelength Observations of Debris Disks around Solar-type Stars
- 2016ApJ...818...45S (2016): The Inner Debris Structure in the Fomalhaut Planetary System
- 2016ApJ...818..156C (2016): A Disk-based Dynamical Constraint on the Mass of the Young Binary DQ Tau
- 2016ApJ...818L..16Z (2016): On the Commonality of 10-30 AU Sized Axisymmetric Dust Structures in Protoplanetary Disks
- 2016ApJ...819..102V (2016): Dust Masses of Disks around 8 Brown Dwarfs and Very Low-mass Stars in Upper Sco OB1 and Ophiuchus
- 2016ApJ...822...36O (2016): ALMACAL I: First Dual-band Number Counts from a Deep and Wide ALMA Submillimeter Survey, Free from Cosmic Variance
- 2016ApJ...822..115K (2016): Detection of HF Toward PKS 1830-211, Search for Interstellar H<SUB>2</SUB>F<SUP>+</SUP>, and Laboratory Study of H<SUB>2</SUB>F<SUP>+</SUP>…
- 2016ApJ...823...37H (2016): Detection of Lensing Substructure Using ALMA Observations of the Dusty Galaxy SDP.81
- 2016ApJ...823L..12G (2016): ALMA Resolves the Torus of NGC 1068: Continuum and Molecular Line Emission
- 2016ApJ...823L..18H (2016): Evidence for a CO Desorption Front in the Outer AS 209 Disk
- 2016ApJ...827..142B (2016): ALMA Observations of Circumstellar Disks in the Upper Scorpius OB Association
- 2016ApJ...828...25L (2016): Debris Disks in the Scorpius-Centaurus OB Association Resolved by ALMA
- 2016ApJ...828...46A (2016): ALMA Survey of Lupus Protoplanetary Disks. I. Dust and Gas Masses
- 2016ApJ...828..113M (2016): ALMA Observations of the Debris Disk of Solar Analog τ Ceti
- 2016ApJ...828L..21K (2016): A Resolved Map of the Infrared Excess in a Lyman Break Galaxy at z = 3
- 2016ApJ...829....6W (2016): ALMA Observations of HD 141569’s Circumstellar Disk
- 2016ApJ...829L..23B (2016): ALMA-SZ Detection of a Galaxy Cluster Merger Shock at Half the Age of the Universe
- 2016ApJ...831..125P (2016): A Steeper than Linear Disk Mass-Stellar Mass Scaling Relation
- 2016ApJ...831..200W (2016): ALMA Reveals the Anatomy of the mm-sized Dust and Molecular Gas in the HD 97048 Disk
- 2016ApJ...832..110C (2016): The Coupled Physical Structure of Gas and Dust in the IM Lup Protoplanetary Disk
- 2016ApJ...833..103H (2016): Kiloparsec-scale Dust Disks in High-redshift Luminous Submillimeter Galaxies
- 2016ApJ...833..219P (2016): ALMA Observations of Orion Source I at 350 and 660 GHz
- 2016ApJ...833L...6C (2016): ALMA Reveals Potential Localized Dust Enrichment from Massive Star Clusters in II Zw 40
- 2016MNRAS.458L..29C (2016): A ring-like concentration of mm-sized particles in Sz 91
- 2016MNRAS.459.4518H (2016): The detection of dust around NN Ser
- 2016MNRAS.460.2933M (2016): Exocometary gas in the HD 181327 debris ring
- 2016MNRAS.462L.101A (2016): Dipper discs not inclined towards edge-on orbits
- 2016MNRAS.463.2265S (2016): The peculiar dipping events in the disc-bearing young-stellar object EPIC 204278916
- 2016Natur.535..258C (2016): Imaging the water snow-line during a protostellar outburst
- 2016Natur.538..483T (2016): A triple protostar system formed via fragmentation of a gravitationally unstable disk
- 2016PASJ...68...88K (2016): The Sunyaev-Zel'dovich effect at 5″: RX J1347.5-1145 imaged by ALMA
- 2017A&A...597A..32V (2017): Cavity and other radial substructures in the disk around HD 97048
- 2017A&A...597A..41G (2017): The ALMA Frontier Fields Survey. I. 1.1 mm continuum detections in Abell 2744, MACS J0416.1-2403 and MACS J1149.5+2223
- 2017A&A...599A..59K (2017): An observational study of dust nucleation in Mira (o Ceti). II. Titanium oxides are negligible for nucleation at high temperatures
- 2017A&A...599A.134S (2017): The ALMA Redshift 4 Survey (AR4S). I. The massive end of the z = 4 main sequence of galaxies
- 2017A&A...601A...7F (2017): SPHERE/SHINE reveals concentric rings in the debris disk of HIP 73145
- 2017A&A...602L..10O (2017): The inhomogeneous submillimeter atmosphere of Betelgeuse
- 2017A&A...603L...6H (2017): Direct evidence of multiple reservoirs of volatile nitrogen in a protosolar nebula analogue
- 2017A&A...605A..21C (2017): Increased H<SUB>2</SUB>CO production in the outer disk around HD 163296
- 2017A&A...605A..28D (2017): The extended molecular envelope of the asymptotic giant branch star π<SUP>1</SUP> Gruis as seen by ALMA. I. Large-scale kinematic structure…
- 2017A&A...605A.105C (2017): AGN feedback on molecular gas reservoirs in quasars at z 2.4
- 2017A&A...605A.116K (2017): Rings and filaments: The remarkable detached CO shell of U Antliae
- 2017A&A...606A..88T (2017): Physical properties of dusty protoplanetary disks in Lupus: evidence for viscous evolution?
- 2017A&A...606A.109M (2017): Detection of CH<SUP>+</SUP>, SH<SUP>+</SUP>, and their <SUP>13</SUP>C- and <SUP>34</SUP>S-isotopologues toward PKS 1830-211
- 2017A&A...606A.121L (2017): Complex organics in IRAS 4A revisited with ALMA and PdBI: Striking contrast between two neighbouring protostellar cores
- 2017A&A...607A..55V (2017): An 80 au cavity in the disk around HD 34282
- 2017A&A...608A..45L (2017): The thermal emission of Centaurs and trans-Neptunian objects at millimeter wavelengths from ALMA observations
- 2017A&A...608A..96L (2017): The ortho-to-para ratio of H<SUB>2</SUB>Cl<SUP>+</SUP>: Quasi-classical trajectory calculations and new simulations in light of new observa…
- 2017AJ....153..233F (2017): ALMA Observations of Asymmetric Molecular Gas Emission from a Protoplanetary Disk in the Orion Nebula
- 2017AJ....153..240A (2017): An ALMA Survey of Protoplanetary Disks in the σ Orionis Cluster
- 2017AJ....154...11H (2017): An Updated 2017 Astrometric Solution for Betelgeuse
- 2017AJ....154...19B (2017): The Density of Mid-sized Kuiper Belt Objects from ALMA Thermal Observations
- 2017AJ....154...24R (2017): ALMA Observations of the Young Substellar Binary System 2M1207
- 2017AJ....154..225S (2017): ALMA 1.3 mm Map of the HD 95086 System
- 2017ApJ...834..135T (2017): Bulge-forming Galaxies with an Extended Rotating Disk at z ~ 2
- 2017ApJ...834..178Y (2017): Signs of Early-stage Disk Growth Revealed with ALMA
- 2017ApJ...836...30G (2017): Nitrogen Fractionation in Protoplanetary Disks from the H<SUP>13</SUP>CN/HC<SUP>15</SUP>N Ratio
- 2017ApJ...836..223W (2017): An ALMA and MagAO Study of the Substellar Companion GQ Lup B*
- 2017ApJ...837..182O (2017): ALMACAL II: Extreme Star Formation Rate Densities in Dusty Starbursts Revealed by ALMA 20 mas Resolution Imaging
- 2017ApJ...838..147C (2017): ALMA Mapping of Rapid Gas and Dust Variations in Comet C/2012 S1 (ISON):New Insights into the Origin of Cometary HNC
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
- 2017ApJ...845L...5I (2017): On the Disappearance of a Cold Molecular Torus around the Low-luminosity Active Galactic Nucleus of NGC 1097
- 2017ApJ...846..108C (2017): A Spatially Resolved Study of Cold Dust, Molecular Gas, H II Regions, and Stars in the z = 2.12 Submillimeter Galaxy ALESS67.1
- 2017ApJ...846L..14S (2017): Massive Quenched Galaxies at z ∼ 0.7 Retain Large Molecular Gas Reservoirs
- 2017ApJ...846L..22G (2017): ALMA Resolves the Molecular Gas in a Young Low-metallicity Starburst Galaxy at z = 1.7
- 2017ApJ...846L..26W (2017): An ALMA Dynamical Mass Estimate of the Proposed Planetary-mass Companion FW Tau C
- 2017ApJ...849...14S (2017): Resolved Structure of the Arp 220 Nuclei at λ ≈ 3 mm
- 2017ApJ...849...56A (2017): ALMA Observations of the Protostar L1527 IRS: Probing Details of the Disk and the Envelope Structures
- 2017ApJ...849..123M (2017): Molecular Gas in Debris Disks around Young A-type Stars
- 2017ApJ...850...54C (2017): ALMA CO(3-2) Observations of Star-forming Filaments in a Gas-poor Dwarf Spheroidal Galaxy
- 2017ApJ...850...83F (2017): Demonstrating a New Census of Infrared Galaxies with ALMA (DANCING-ALMA). I. FIR Size and Luminosity Relation at z = 0-6 Revealed with 1034…
- 2017ApJ...850..170O (2017): High Dense Gas Fraction in Intensely Star-forming Dusty Galaxies
- 2017ApJ...851...85B (2017): Measurement of Circumstellar Disk Sizes in the Upper Scorpius OB Association with ALMA
- 2017ApJ...851L..23C (2017): ALMA Observations of Elias 2-24: A Protoplanetary Disk with Multiple Gaps in the Ophiuchus Molecular Cloud
- 2017MNRAS.465.2595M (2017): ALMA observations of the η Corvi debris disc: inward scattering of CO-rich exocomets by a chain of 3-30 M<SUB>⊕</SUB> planets?
- 2017MNRAS.465.4390B (2017): The discovery of gas-rich, dusty starbursts in luminous reddened quasars at z ∼ 2.5 with ALMA
- 2017MNRAS.466..138K (2017): A merger in the dusty, z = 7.5 galaxy A1689-zD1?
- 2017MNRAS.466.4201W (2017): 1.3-mm ALMA observations of the Fomalhaut debris system
- 2017MNRAS.467.3513T (2017): On the dust and gas components of the z = 2.8 gravitationally lensed quasar host RX J0911.4+0551
- 2017MNRAS.468.4205K (2017): ALMA observations of cold molecular gas in AGN hosts at z ∼ 1.5 - evidence of AGN feedback?
- 2017MNRAS.469.4683C (2017): ALMA constraints on star-forming gas in a prototypical z = 1.5 clumpy galaxy: the dearth of CO(5-4) emission from UV-bright clumps
- 2017NatAs...1..848V (2017): The shock-heated atmosphere of an asymptotic giant branch star resolved by ALMA
- 2017NatAs...1E.130Z (2017): Mass inventory of the giant-planet formation zone in a solar nebula analogue
- 2018A&A...610A...4G (2018): IRC +10 216 in 3D: morphology of a TP-AGB star envelope
- 2018A&A...610A..24F (2018): ALMA continuum observations of the protoplanetary disk AS 209. Evidence of multiple gaps opened by a single planet
- 2018A&A...611A..16B (2018): Sulphur monoxide exposes a potential molecular disk wind from the planet-hosting disk around HD 100546
- 2018A&A...611A..22S (2018): Jekyll &amp; Hyde: quiescence and extreme obscuration in a pair of massive galaxies 1.5 Gyr after the Big Bang
- 2018A&A...612A..29B (2018): Molecular outflow and feedback in the obscured quasar XID2028 revealed by ALMA
- 2018A&A...613A..34P (2018): ALMA view of RX J1131-1231: Sub-kpc CO (2-1) mapping of a molecular disk in a lensed star-forming quasar host galaxy
- 2018A&A...613L...4V (2018): Rotation of the asymptotic giant branch star R Doradus
- 2018A&A...614A.106C (2018): Probing midplane CO abundance and gas temperature with DCO<SUP>+</SUP> in the protoplanetary disk around HD 169142
- 2018A&A...615A..95P (2018): Resolved millimeter-dust continuum cavity around the very low mass young star CIDA 1
- 2018A&A...616A..23D (2018): The evolving jet spectrum of the neutron star X-ray binary Aql X-1 in transitional states during its 2016 outburst
- 2018A&A...616A..88V (2018): V1094 Scorpii: A rare giant multi-ringed disk around a T Tauri star
- 2018A&A...616A.110E (2018): Starbursts in and out of the star-formation main sequence
- 2018A&A...616A.171P (2018): Spatially resolved cold molecular outflows in ULIRGs
- 2018A&A...616L...3B (2018): High-resolution observations of the symbiotic system R Aqr. Direct imaging of the gravitational effects of the secondary on the stellar wind
- 2018A&A...617A..10C (2018): Water and interstellar complex organics associated with the HH 212 protostellar disc. On disc atmospheres, disc winds, and accretion shocks
- 2018A&A...617A..23B (2018): Molecular line study of the S-type AGB star W Aquilae. ALMA observations of CS, SiS, SiO and HCN
- 2018A&A...617A..28S (2018): Chemistry in disks. XI. Sulfur-bearing species as tracers of protoplanetary disk physics and chemistry: the DM Tau case
- 2018A&A...617A..89C (2018): Search for high-mass protostars with ALMA revealed up to kilo-parsec scales (SPARKS). I. Indication for a centrifugal barrier in the enviro…
- 2018A&A...618A..35G (2018): High-speed molecular cloudlets around the Galactic center's supermassive black hole
- 2018A&A...618A..85S (2018): Near infrared spectroscopy and star-formation histories of 3 ≤ z ≤ 4 quiescent galaxies
- 2018A&A...618A.164S (2018): Through the magnifying glass: ALMA acute viewing of the intricate nebular architecture of OH 231.8+4.2
- 2018A&A...619A..39F (2018): The dense molecular gas in the z ∼ 6 QSO SDSS J231038.88+185519.7 resolved by ALMA
- 2018A&A...619A.161C (2018): Evidence for a massive dust-trapping vortex connected to spirals. Multi-wavelength analysis of the HD 135344B protoplanetary disk
- 2018A&A...620A..75K (2018): High-resolution observations of gas and dust around Mira using ALMA and SPHERE/ZIMPOL
- 2018A&A...620A.125M (2018): The ALMA Frontier Fields Survey. IV. Lensing-corrected 1.1 mm number counts in Abell 2744, MACS J0416.1-2403 and MACS J1149.5+2223
- 2018A&A...620A.152F (2018): GOODS-ALMA: 1.1 mm galaxy survey. I. Source catalog and optically dark galaxies
- 2018AJ....155...54W (2018): The Taurus Boundary of Stellar/Substellar (TBOSS) Survey. II. Disk Masses from ALMA Continuum Observations
- 2018AJ....156..164B (2018): Medium-sized Satellites of Large Kuiper Belt Objects
- 2018ApJ...852..122H (2018): CO and Dust Properties in the TW Hya Disk from High-resolution ALMA Observations
- 2018ApJ...853..147M (2018): Molecular Reconnaissance of the β Pictoris Gas Disk with the SMA: A Low HCN/(CO+CO<SUB>2</SUB>) Outgassing Ratio and Predictions for Future…
- 2018ApJ...854..130W (2018): The Orbit of the Companion to HD 100453A: Binary-driven Spiral Arms in a Protoplanetary Disk
- 2018ApJ...855L...2M (2018): Detection of a Millimeter Flare from Proxima Centauri
- 2018ApJ...856..117F (2018): Turbulence in the TW Hya Disk
- 2018ApJ...856..121G (2018): Starburst to Quiescent from HST/ALMA: Stars and Dust Unveil Minor Mergers in Submillimeter Galaxies at z ∼ 4.5
- 2018ApJ...856L...5F (2018): ALMA Detections of CO Emission in the Most Luminous, Heavily Dust-obscured Quasars at z &gt; 3
- 2018ApJ...857...18S (2018): Multiple Gaps in the Disk of the Class I Protostar GY 91
- 2018ApJ...857...69B (2018): A Survey of CH<SUB>3</SUB>CN and HC<SUB>3</SUB>N in Protoplanetary Disks
- 2018ApJ...859...21A (2018): ALMA Survey of Lupus Protoplanetary Disks. II. Gas Disk Radii
- 2018ApJ...859...32P (2018): Homogeneous Analysis of the Dust Morphology of Transition Disks Observed with ALMA: Investigating Dust Trapping and the Origin of the Cavit…
- 2018ApJ...859...35G (2018): The Dual Role of Starbursts and Active Galactic Nuclei in Driving Extreme Molecular Outflows
- 2018ApJ...859..111H (2018): The Circumstellar Disk and Asymmetric Outflow of the EX Lup Outburst System
- 2018ApJ...859..131L (2018): The Distribution and Excitation of CH<SUB>3</SUB>CN in a Solar Nebula Analog
- 2018ApJ...859..144A (2018): Resolving the Nuclear Obscuring Disk in the Compton-thick Seyfert Galaxy NGC 5643 with ALMA
- 2018ApJ...859..150R (2018): Multiple Stellar Flybys Sculpting the Circumstellar Architecture in RW Aurigae
- 2018ApJ...859L..28K (2018): Probing Signatures of a Distant Planet around the Young T-Tauri Star CI Tau Hosting a Possible Hot Jupiter
- 2018ApJ...860....7R (2018): A Cavity of Large Grains in the Disk around the Group II Herbig Ae/Be Star HD 142666
- 2018ApJ...860..103S (2018): Molecular Gas Contents and Scaling Relations for Massive, Passive Galaxies at Intermediate Redshifts from the LEGA-C Survey
- 2018ApJ...860..162F (2018): The Maser-emitting Structure and Time Variability of the SiS Lines J = 14-13 and 15-14 in IRC+10216
- 2018ApJ...861....7F (2018): ALMA 26 Arcmin<SUP>2</SUP> Survey of GOODS-S at One Millimeter (ASAGAO): Average Morphology of High-z Dusty Star-forming Galaxies in an Exp…
- 2018ApJ...861...43P (2018): Hidden in Plain Sight: A Massive, Dusty Starburst in a Galaxy Protocluster at z = 5.7 in the COSMOS Field
- 2018ApJ...861...91H (2018): ALMA Observations of Polarized 872 μm Dust Emission from the Protostellar Systems VLA 1623 and L1527
- 2018ApJ...863...19A (2018): The Distinct Evolutionary Nature of Two Class 0 Protostars in Serpens Main SMM4
- 2018ApJ...863...61L (2018): An ALMA Survey of Faint Disks in the Chamaeleon I Star-forming Region: Why Are Some Class II Disks so Faint?
- 2018ApJ...863..129S (2018): Spatially Resolved Dense Molecular Gas Excitation in the Nearby LIRG VV 114
- 2018ApJ...863L..29D (2018): Witnessing Galaxy Assembly at the Edge of the Reionization Epoch
- 2018ApJ...865...37M (2018): Multiple Rings in the Transitional Disk of GM Aurigae Revealed by VLA and ALMA
- 2018ApJ...865..155C (2018): Constraining Gas-phase Carbon, Oxygen, and Nitrogen in the IM Lup Protoplanetary Disk
- 2018ApJ...865..157A (2018): Scaling Relations Associated with Millimeter Continuum Sizes in Protoplanetary Disks
- 2018ApJ...866L...6C (2018): High-resolution Millimeter Imaging of the CI Tau Protoplanetary Disk: A Massive Ensemble of Protoplanets from 0.1 to 100 au
- 2018ApJ...867...48I (2018): Circumnuclear Multiphase Gas in the Circinus Galaxy. II. The Molecular and Atomic Obscuring Structures Revealed with ALMA
- 2018ApJ...867...92S (2018): The Molecular Gas Content and Fuel Efficiency of Starbursts at z ∼ 1.6 with ALMA
- 2018ApJ...867..140L (2018): Resolving Star Formation on Subkiloparsec Scales in the High-redshift Galaxy SDP.11 Using Gravitational Lensing
- 2018ApJ...867L..29W (2018): Revealing the Environmental Dependence of Molecular Gas Content in a Distant X-Ray Cluster at z = 2.51
- 2018ApJ...868...75S (2018): Concurrent Starbursts in Molecular Gas Disks within a Pair of Colliding Galaxies at z = 1.52
- 2018ApJ...868L...5K (2018): A Spatially Resolved au-scale Inner Disk around DM Tau
- 2018ApJ...869...17L (2018): Gaps and Rings in an ALMA Survey of Disks in the Taurus Star-forming Region
- 2018ApJ...869...27V (2018): A Survey of Atomic Carbon [C I] in High-redshift Main-sequence Galaxies
- 2018ApJ...869...59W (2018): Physical and Chemical Conditions of the Protostellar Envelope and the Protoplanetary Disk in HL Tau
- 2018ApJ...869...75M (2018): ALMA Detection of Extended Millimeter Halos in the HD 32297 and HD 61005 Debris Disks
- 2018ApJ...869..158F (2018): ALMA Detections of the Youngest Protostars in Ophiuchus
- 2018ApJ...869L..22W (2018): No Evidence for Enhanced [O III] 88 μm Emission in a z ∼ 6 Quasar Compared to Its Companion Starbursting Galaxy
- 2018ApJ...869L..48G (2018): The Disk Substructures at High Angular Resolution Program (DSHARP). VIII. The Rich Ringed Substructures in the AS 209 Disk
- 2018ApJ...869L..49I (2018): The Disk Substructures at High Angular Resolution Project (DSHARP). IX. A High-definition Study of the HD 163296 Planet-forming Disk
- 2018ApJ...869L..50P (2018): The Disk Substructures at High Angular Resolution Project (DSHARP). X. Multiple Rings, a Misaligned Inner Disk, and a Bright Arc in the Dis…
- 2018MNRAS.474.4347C (2018): The ALMA early science view of FUor/EXor objects - V. Continuum disc masses and sizes
- 2018MNRAS.474.4500W (2018): ALMA and VLA observations of the HD 141569 system
- 2018MNRAS.475.4924K (2018): ALMA observations of the narrow HR 4796A debris ring
- 2018MNRAS.476.3956T (2018): ALMA view of a massive spheroid progenitor: a compact rotating core of molecular gas in an AGN host at z = 2.226
- 2018MNRAS.476.4383D (2018): Modelling high-resolution ALMA observations of strongly lensed highly star-forming galaxies detected by Herschel
- 2018MNRAS.478.3674R (2018): ALMA survey of circumstellar discs in the young stellar cluster IC 348
- 2018MNRAS.479..703C (2018): Merger-driven star formation activity in Cl J1449+0856 at z = 1.99 as seen by ALMA and JVLA
- 2018MNRAS.479.5423M (2018): A gap in the planetesimal disc around HD 107146 and asymmetric warm dust emission revealed by ALMA
- 2018MNRAS.481.1976Z (2018): The [C II] emission as a molecular gas mass tracer in galaxies at low and high redshifts
- 2018MNRAS.481L..40S (2018): A flux-ratio anomaly in the CO spectral line emission from gravitationally lensed quasar MG J0414+0534
- 2018NatAs...2...56Z (2018): A dusty star-forming galaxy at z = 6 revealed by strong gravitational lensing
- 2018Natur.553...51M (2018): Galaxy growth in a massive halo in the first billion years of cosmic history
- 2018Sci...361.1016S (2018): Fast molecular outflow from a dusty star-forming galaxy in the early Universe
- 2019A&A...621A..18M (2019): Submillimeter polarization and variability of quasar PKS 1830-211
- 2019A&A...623A.111H (2019): Magnetic field at a jet base: extreme Faraday rotation in 3C 273 revealed by ALMA
- 2019A&A...623A.124C (2019): Upper limits on CH<SUB>3</SUB>OH in the HD 163296 protoplanetary disk. Evidence for a low gas-phase CH<SUB>3</SUB>OH-to-H<SUB>2</SUB>CO rat…
- 2019A&A...623A.150V (2019): The ALMA Lupus protoplanetary disk survey: evidence for compact gas disks and molecular rings from CN
- 2019A&A...624A..33V (2019): ALMA study of the HD 100453 AB system and the tidal interaction of the companion with the disk
- 2019A&A...625A.118K (2019): Highly structured disk around the planet host PDS 70 revealed by high-angular resolution observations with ALMA
- 2019A&A...626A..81V (2019): Resolving the extended stellar atmospheres of asymptotic giant branch stars at (sub)millimetre wavelengths
- 2019A&A...626L...2F (2019): High gas-to-dust size ratio indicating efficient radial drift in the mm-faint CX Tauri disk
- 2019A&A...628A..65A (2019): Nuclear molecular outflow in the Seyfert galaxy NGC 3227
- 2019A&A...628A..95M (2019): Observational constraints on dust disk sizes in tidally truncated protoplanetary disks in multiple systems in the Taurus region
- 2019A&A...628A.100D (2019): An ALMA+ACA measurement of the shock in the Bullet Cluster
- 2019A&A...628A.118B (2019): The gentle monster PDS 456. Kiloparsec-scale molecular outflow and its implications for QSO feedback
- 2019A&A...629A.104G (2019): Sunyaev-Zel'dovich detection of the galaxy cluster Cl J1449+0856 at z = 1.99: The pressure profile in uv space
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
- 2019ApJ...871..149F (2019): Identifying Variability in Deeply Embedded Protostars with ALMA and CARMA
- 2019ApJ...872...92F (2019): The Planet Formation Potential around a 45 Myr Old Accreting M Dwarf
- 2019ApJ...873...50D (2019): Source Structure and Molecular Gas Properties from High-resolution CO Imaging of SPT-selected Dusty Star-forming Galaxies
- 2019ApJ...873L..19B (2019): Extremely Low Molecular Gas Content in a Compact, Quiescent Galaxy at z = 1.522
- 2019ApJ...874..136S (2019): High-precision Dynamical Masses of Pre-main-sequence Stars with ALMA and Gaia
- 2019ApJ...875...55W (2019): The MESAS Project: Long-wavelength Follow-up Observations of Sirius A
- 2019ApJ...875...87D (2019): The Mass of Stirring Bodies in the AU Mic Debris Disk Inferred from Resolved Vertical Structure
- 2019ApJ...875L...1E (2019): First M87 Event Horizon Telescope Results. I. The Shadow of the Supermassive Black Hole
- 2019ApJ...875L...3E (2019): First M87 Event Horizon Telescope Results. III. Data Processing and Calibration
- 2019ApJ...875L...5E (2019): First M87 Event Horizon Telescope Results. V. Physical Origin of the Asymmetric Ring
- 2019ApJ...875L...9W (2019): The Ophiuchus DIsk Survey Employing ALMA (ODISEA): Disk Dust Mass Distributions across Protostellar Evolutionary Classes
- 2019ApJ...876....1T (2019): CNO Emission of an Unlensed Submillimeter Galaxy at z = 4.3
- 2019ApJ...876..112R (2019): Strong Far-ultraviolet Fields Drive the [C II]/Far-infrared Deficit in z ∼ 3 Dusty, Star-forming Galaxies
- 2019ApJ...877L..23P (2019): The Main Sequence at z ∼ 1.3 Contains a Sizable Fraction of Galaxies with Compact Star Formation Sizes: A New Population of Early Post-star…
- 2019ApJ...877L..32M (2019): Multiple Rings of Millimeter Dust Emission in the HD 15115 Debris Disk
- 2019ApJ...878...16P (2019): An Inner Disk in the Large Gap of the Transition Disk SR 24S
- 2019ApJ...878L...8T (2019): Discovery of An au-scale Excess in Millimeter Emission from the Protoplanetary Disk around TW Hya
- 2019ApJ...880....2W (2019): Spatially Resolved Interstellar Medium and Highly Excited Dense Molecular Gas in the Most Luminous Quasar at z = 6.327
- 2019ApJ...880..130M (2019): A New, Rotating Hot Corino in Serpens
- 2019ApJ...881...84S (2019): The REASONS Survey: Resolved Millimeter Observations of a Large Debris Disk around the Nearby F Star HD 170773
- 2019ApJ...881..159M (2019): Characterization of Ring Substructures in the Protoplanetary Disk of HD 169142 from Multiwavelength Atacama Large Millimeter/submillimeter …
- 2019ApJ...881L...2B (2019): ALMA Observations of the Terahertz Spectrum of Sagittarius A*
- 2019ApJ...882...23B (2019): EHT-HOPS Pipeline for Millimeter VLBI Data Reduction
- 2019ApJ...882...49L (2019): Compact Disks in a High-resolution ALMA Survey of Dust Structures in the Taurus Molecular Cloud
- 2019ApJ...882..107R (2019): ALMA 200 pc Resolution Imaging of Smooth Cold Dusty Disks in Typical z ∼ 3 Star-forming Galaxies
- 2019ApJ...882..118X (2019): ALMA Detection of Vibrationally Excited (v <SUB>t</SUB> = 1, 2) Acetic Acid toward NGC 6334I
- 2019ApJ...882..160Q (2019): Probing CO and N<SUB>2</SUB> Snow Surfaces in Protoplanetary Disks with N<SUB>2</SUB>H<SUP>+</SUP> Emission
- 2019ApJ...882..168P (2019): Low Star Formation Efficiency in Typical Galaxies at z = 5-6
- 2019ApJ...883...22C (2019): The Degree of Alignment between Circumbinary Disks and Their Binary Hosts
- 2019ApJ...883...71C (2019): The Radial Distribution of Dust Particles in the HL Tau Disk from ALMA and VLA Observations
- 2019ApJ...883...81S (2019): Evidence for Inside-out Galaxy Growth and Quenching of a z ∼ 2 Compact Galaxy From High-resolution Molecular Gas Imaging
- 2019ApJ...884...42S (2019): Masses and Implications for Ages of Low-mass Pre-main-sequence Stars in Taurus and Ophiuchus
- 2019ApJ...884...97L (2019): Diagnosing 0.1-10 au Scale Morphology of the FU Ori Disk Using ALMA and VLTI/GRAVITY
- 2019ApJ...885...82L (2019): Sulfur-bearing Molecules in Orion KL
- 2019ApJ...885..106L (2019): Characterizing Magnetic Field Morphologies in Three Serpens Protostellar Cores with ALMA
- 2019ApJ...886L..28M (2019): Anomalously Narrow Line Widths of Compact Massive Star-forming Galaxies at z ∼ 2.3: A Possible Inclination Bias in the Size-Mass Plane
- 2019ApJ...887...24T (2019): Resolving the Interstellar Medium in Ultraluminous Infrared QSO Hosts with ALMA
- 2019ApJ...887...40W (2019): Resolving the Interstellar Medium in the Nuclear Region of Two z = 5.78 Quasar Host Galaxies with ALMA
- 2019ApJ...887...55C (2019): Physical Characterization of an Unlensed, Dusty Star-forming Galaxy at z = 5.85
- 2019ApJ...887..107F (2019): First Identification of 10 kpc [C II] 158 μm Halos around Star-forming Galaxies at z = 5-7
- 2019ApJ...887..144J (2019): Discovery of Four Apparently Cold Dusty Galaxies at z = 3.62-5.85 in the COSMOS Field: Direct Evidence of Cosmic Microwave Background Impac…
- 2019ESC.....3.2110C (2019): The HH 212 Interstellar Laboratory: Astrochemistry as a Tool To Reveal Protostellar Disks on Solar System Scales around a Rising Sun
- 2019MNRAS.482..698C (2019): The Ophiuchus DIsc Survey Employing ALMA (ODISEA) - I: project description and continuum images at 28 au resolution
- 2019MNRAS.484.1257M (2019): A gap in HD 92945's broad planetesimal disc revealed by ALMA
- 2019MNRAS.484L..43Z (2019): First detection of the pre-biotic molecule glycolonitrile (HOCH<SUB>2</SUB>CN) in the interstellar medium
- 2019MNRAS.485..739M (2019): Asymmetric mid-plane gas in ALMA images of HD 100546
- 2019MNRAS.485.2092C (2019): Suppressed CO emission and high G/D ratios in z = 2 galaxies with sub-solar gas-phase metallicity
- 2019MNRAS.486.5552B (2019): Sub-millimetre non-contaminated detection of the disc around TWA 7 by ALMA
- 2019MNRAS.487.4037D (2019): A joint ALMA-Bolocam-Planck SZ study of the pressure distribution in RX J1347.5-1145
- 2019MNRAS.488.1180S (2019): No signs of star formation being regulated in the most luminous quasars at z ∼ 2 with ALMA
- 2019MNRAS.489.3670K (2019): Imaging [CI] around HD 131835: reinterpreting young debris discs with protoplanetary disc levels of CO gas as shielded secondary discs
- 2019MNRAS.489.3939C (2019): Constraints on high-J CO emission lines in z ∼ 6 quasars
- 2019MNRAS.490.4956G (2019): An ALMA survey of the SCUBA-2 Cosmology Legacy Survey UKIDSS/UDS field: high-resolution dust continuum morphologies and the link between su…
- 2019MNRAS.490.5134B (2019): Detecting the halo heating from AGN feedback with ALMA
- 2019NatAs...3..230K (2019): A circumbinary protoplanetary disk in a polar configuration
- 2019NatAs...3..278K (2019): Publisher Correction: A circumbinary protoplanetary disk in a polar configuration
- 2019Natur.572..211W (2019): A dominant population of optically invisible massive galaxies in the early Universe
- 2019PASJ...71..111I (2019): Subaru High-z Exploration of Low-Luminosity Quasars (SHELLQs). VIII. A less biased view of the early co-evolution of black holes and host g…
- 2019RAA....19...43N (2019): ALMA observations of the circumstellar envelope around EP Aqr
- 2020A&A...633A.114S (2020): Demographics of disks around young very low-mass stars and brown dwarfs in Lupus
- 2020A&A...633A.126B (2020): The dynamically young outflow of the Class 0 protostar Cha-MMS1
- 2020A&A...633A.134L (2020): Molecular outflows in local galaxies: Method comparison and a role of intermittent AGN driving
- 2020A&A...635A..12P (2020): GG Tauri A: gas properties and dynamics from the cavity to the outer disk
- 2020A&A...635A..94D (2020): An ALMA/NOEMA study of gas dissipation and dust evolution in the 5 Myr-old HD 141569A hybrid disc
- 2020A&A...635A.119C (2020): Extended Hα over compact far-infrared continuum in dusty submillimeter galaxies. Insights into dust distributions and star-formation rates …
- 2020A&A...636A..26H (2020): Missing water in Class I protostellar disks
- 2020A&A...636A..37D (2020): Dust and gas content of high-redshift galaxies hosting obscured AGN in the Chandra Deep Field-South
- 2020A&A...636A..62K (2020): Investigating the connection between γ-ray activity and the relativistic jet in 3C 273 during 2015-2019
- 2020A&A...637A...7M (2020): Detection of deuterated molecules, but not of lithium hydride, in the z = 0.89 absorber toward PKS 1830-211
- 2020A&A...638A..65O (2020): ALMA and VLA reveal the lukewarm chromospheres of the nearby red supergiants Antares and Betelgeuse
- 2020A&A...638A..70D (2020): The Massive and Distant Clusters of WISE Survey. SZ effect of Verification with the Atacama Compact Array - Localization and Cluster Analys…
- 2020A&A...638L..13M (2020): ALMA full polarization observations of PKS 1830-211 during its record-breaking flare of 2019
- 2020A&A...639A.121F (2020): Annular substructures in the transition disks around LkCa 15 and J1610
- 2020A&A...640A.133R (2020): DEATHSTAR: Nearby AGB stars with the Atacama Compact Array. I. CO envelope sizes and asymmetries: A new hope for accurate mass-loss-rate es…
- 2020A&A...641A.155V (2020): CO emission in distant galaxies on and above the main sequence
- 2020A&A...642A.155Z (2020): GOODS-ALMA: Optically dark ALMA galaxies shed light on a cluster in formation at z = 3.5
- 2020A&A...643A...5D (2020): The ALPINE-ALMA [C II] survey. Molecular gas budget in the early Universe as traced by [C II]
- 2020A&A...643A..30F (2020): GOODS-ALMA: The slow downfall of star formation in z = 2-3 massive galaxies
- 2020A&A...643A..53F (2020): GOODS-ALMA: Using IRAC and VLA to probe fainter millimeter galaxies
- 2020AJ....159..171F (2020): A Ringed Pole-on Outflow from DO Tauri Revealed by ALMA
- 2020AJ....159..215L (2020): Disk-integrated Thermal Properties of Ceres Measured at Millimeter Wavelengths
- 2020AJ....159..229W (2020): ALMA 0.88 mm Survey of Disks around Planetary-mass Companions
- 2020AJ....159..288M (2020): The Big Sibling of AU Mic: A Cold Dust-rich Debris Disk around CP-72 2713 in the β Pic Moving Group
- 2020AJ....160..248A (2020): An ALMA Survey of λ Orionis Disks: From Supernovae to Planet Formation
- 2020AJ....160..270F (2020): On the Accuracy of the ALMA Flux Calibration in the Time Domain and across Spectral Windows
- 2020ApJ...888...41A (2020): Modeling the Accretion Disk around the High-mass Protostar GGD 27-MM1
- 2020ApJ...888...44C (2020): Unveiling Sizes of Compact AGN Hosts with ALMA
- 2020ApJ...889...59P (2020): Resolving the FU Orionis System with ALMA: Interacting Twin Disks?
- 2020ApJ...890...24V (2020): The Properties of the Interstellar Medium of Galaxies across Time as Traced by the Neutral Atomic Carbon [C I]
- 2020ApJ...891...48H (2020): A Multifrequency ALMA Characterization of Substructures in the GM Aur Protoplanetary Disk
- 2020ApJ...891...80M (2020): Properties of M Dwarf Flares at Millimeter Wavelengths
- 2020ApJ...894...76W (2020): The MESAS Project: ALMA Observations of the F-type Stars γ Lep, γ Vir A, and γ Vir B
- 2020ApJ...895..109F (2020): Measuring Turbulent Motion in Planet-forming Disks with ALMA: A Detection around DM Tau and Nondetections around MWC 480 and V4046 Sgr
- 2020ApJ...895..126H (2020): The Evolution of Dust Disk Sizes from a Homogeneous Analysis of 1-10 Myr old Stars
- 2020ApJ...895L..18B (2020): GW Ori: Interactions between a Triple-star System and Its Circumtriple Disk in Action
- 2020ApJ...897...91G (2020): The ALMA Spectroscopic Survey in the HUDF: Deep 1.2 mm Continuum Number Counts
- 2020ApJ...898...33C (2020): ALMA [{N} {II}] 205 μm Imaging Spectroscopy of the Lensed Submillimeter Galaxy ID 141 at Redshift 4.24
- 2020ApJ...898...36L (2020): Dual-wavelength ALMA Observations of Dust Rings in Protoplanetary Disks
- 2020ApJ...898...75I (2020): ALMA Observations of Multiple CO and C Lines toward the Active Galactic Nucleus of NGC 7469: An X-Ray-dominated Region Caught in the Act
- 2020ApJ...898..146M (2020): Dust Populations in the Iconic Vega Planetary System Resolved by ALMA
- 2020ApJ...899...37K (2020): A Comparison of the Stellar, CO, and Dust-continuum Emission from Three Star-forming HUDF Galaxies at z ∼ 2
- 2020ApJ...899...55A (2020): Search for Alignment of Disk Orientations in Nearby Star-forming Regions: Lupus, Taurus, Upper Scorpius, ρ Ophiuchi, and Orion
- 2020ApJ...899..112S (2020): AGN Feedback and Star Formation of Quasar Host Galaxies: Insights from the Molecular Gas
- 2020ApJ...900....1F (2020): The ALPINE-ALMA [C II] Survey: Size of Individual Star-forming Galaxies at z = 4-6 and Their Extended Halo Structure
- 2020ApJ...900....7H (2020): ALMA Observations of Young Eruptive Stars: Continuum Disk Sizes and Molecular Outflows
- 2020ApJ...901...74T (2020): Structural Evolution in Massive Galaxies at z ∼ 2
- 2020ApJ...901...79A (2020): The ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: The Nature of the Faintest Dusty Star-forming Galaxies
- 2020ApJ...902..112B (2020): The ALMA Spectroscopic Survey Large Program: The Infrared Excess of z = 1.5-10 UV-selected Galaxies and the Implied High-redshift Star Form…
- 2020ApJ...902..132B (2020): On the Nature of the T Tauri Triple System
- 2020ApJ...902..141S (2020): The VLA/ALMA Nascent Disk and Multiplicity (VANDAM) Survey of Orion Protostars. III. Substructures in Protostellar Disks
- 2020ApJ...902L..33G (2020): A Tale of Two Transition Disks: ALMA Long-baseline Observations of ISO-Oph 2 Reveal Two Closely Packed Nonaxisymmetric Rings and a ∼2 au Ca…
- 2020ApJ...903...29M (2020): Reconstructing the EUV Spectrum of Star-forming Regions from Millimeter Recombination Lines of H I, He I, and He II
- 2020ApJ...903...50E (2020): Super Star Clusters in the Central Starburst of NGC 4945
- 2020ApJ...904...37W (2020): ALMA and VLA Observations of EX Lupi in Its Quiescent State
- 2020ApJ...904..131N (2020): No Evidence for [C II] Halos or High-velocity Outflows in z ≳ 6 Quasar Host Galaxies
- 2020ApJ...905...89Y (2020): Kinematical Signs of Dust Trapping and Feedback in a Local Pressure Bump in the Protoplanetary Disk around HD 142527 Revealed with ALMA
- 2020CPhy...30...85D (2020): Observation of High Doppler Velocity Wings in the Nascent Wind of R Doradus
- 2020MNRAS.492..572A (2020): Are inner disc misalignments common? ALMA reveals an isotropic outer disc inclination distribution for young dipper stars
- 2020MNRAS.492.3194S (2020): KASHz: No evidence for ionised outflows instantaneously suppressing star formation in moderate luminosity AGN at z ∼ 1.4-2.6
- 2020MNRAS.493.3412F (2020): No nitrogen fractionation on 600 au scale in the Sun progenitor analogue OMC-2 FIR4
- 2020MNRAS.493L.108B (2020): <SUP>13</SUP>C<SUP>17</SUP>O suggests gravitational instability in the HL Tau disc
- 2020MNRAS.494.1323D (2020): An ALMA view of SO and SO<SUB>2</SUB> around oxygen-rich AGB stars
- 2020MNRAS.494.4090C (2020): The [C II]/[N II] ratio in 3 &lt; z &lt; 6 sub-millimetre galaxies from the South Pole Telescope survey
- 2020MNRAS.495.3409S (2020): An ALMA survey of the brightest sub-millimetre sources in the SCUBA-2-COSMOS field
- 2020MNRAS.496..138B (2020): VLA and ALMA observations of the lensed radio-quiet quasar SDSS J0924+0219: a molecular structure in a 3 μJy radio source
- 2020MNRAS.496..598C (2020): Linking the small-scale relativistic winds and the large-scale molecular outflows in the z = 1.51 lensed quasar HS 0810+2554
- 2020MNRAS.498.1319M (2020): Insights into the planetary dynamics of HD 206893 with ALMA
- 2020MNRAS.498.4635D (2020): Overdensity of SMGs in fields containing z ∼ 0.3 galaxies: magnification bias and the implications for studies of galaxy evolution
- 2020MNRAS.499.3909Y (2020): Evidence for a jet and outflow from Sgr A*: a continuum and spectral line study
- 2020MNRAS.499.5136C (2020): Missing [C II] emission from early galaxies
- 2020MNRAS.499.5241C (2020): A kpc-scale-resolved study of unobscured and obscured star formation activity in normal galaxies at z = 1.5 and 2.2 from ALMA and HiZELS
- 2020Natur.584..201R (2020): A dynamically cold disk galaxy in the early Universe
- 2020PASJ...72...33K (2020): Deeply cooled core of the Phoenix galaxy cluster imaged by ALMA with the Sunyaev-Zel'dovich effect
- 2020PASJ...72...36T (2020): Sub-millimeter detection of a Galactic center cool star IRS 7 by ALMA
- 2020RSOS....700063K (2020): The unexpected narrowness of eccentric debris rings: a sign of eccentricity during the protoplanetary disc phase
- 2021A&A...645A..33B (2021): The WISSH quasars project. IX. Cold gas content and environment of luminous QSOs at z ∼ 2.4-4.7
- 2021A&A...646A..59R (2021): Tracing molecular stratification within an edge-on protoplanetary disk
- 2021A&A...646A..72H (2021): Resolved molecular line observations reveal an inherited molecular layer in the young disk around TMC1A
- 2021A&A...647A..87L (2021): The prebiotic molecular inventory of Serpens SMM1. I. An investigation of the isomers CH<SUB>3</SUB>NCO and HOCH<SUB>2</SUB>CN
- 2021A&A...647A.173K (2021): ALMA/NICER observations of GRS 1915+105 indicate a return to a hard state
- 2021A&A...649A..19S (2021): Measuring the ratio of the gas and dust emission radii of protoplanetary disks in the Lupus star-forming region
- 2021A&A...649A.122P (2021): A bright inner disk and structures in the transition disk around the very low-mass star CIDA 1
- 2021A&A...650A.153D (2021): Multiwavelength view of SPT-CL J2106-5844. The radio galaxies and the thermal and relativistic plasmas in a massive galaxy cluster merger a…
- 2021A&A...651A...4B (2021): Structure and dynamics of the inner nebula around the symbiotic stellar system R Aquarii
- 2021A&A...651L...5V (2021): A major asymmetric ice trap in a planet-forming disk. I. Formaldehyde and methanol
- 2021A&A...652A...5M (2021): A study of submillimeter methanol absorption toward PKS 1830‒211:. Excitation, invariance of the proton-electron mass ratio, and systematics
- 2021A&A...653A..46V (2021): Probing protoplanetary disk evolution in the Chamaeleon II region
- 2021A&A...653A..53A (2021): DEATHSTAR: nearby AGB stars with the Atacama Compact Array. II. CO envelope sizes and asymmetries: the S-type stars
- 2021A&A...653A.117B (2021): ORion Alma New GEneration Survey (ORANGES). I. Dust continuum and free-free emission of OMC-2/3 filament protostars
- 2021A&A...653L...9V (2021): If you like C/O variations, you should have put a ring on it
- 2021A&A...654A..24B (2021): Molecular gas kinematics in the nuclear region of nearby Seyfert galaxies with ALMA
- 2021A&A...654A..37D (2021): Kinematics and star formation of high-redshift hot dust-obscured quasars as seen by ALMA
- 2021A&A...654A..90L (2021): SUPER. V. ALMA continuum observations of z ∼ 2 AGN and the elusive evidence of outflows influencing star formation
- 2021A&A...654L...8C (2021): SUPER. VI. A giant molecular halo around a z∼2 quasar
- 2021A&A...656A.150P (2021): Constraining the properties of the potential embedded planets in the disk around HD 100546
- 2021AJ....161...38O (2021): The TW Hya Rosetta Stone Project. I. Radial and Vertical Distributions of DCN and DCO<SUP>+</SUP>
- 2021AJ....161..271F (2021): A Detailed Characterization of HR 8799's Debris Disk with ALMA in Band 7
- 2021AJ....162...99F (2021): The Chemical Inventory of the Planet-hosting Disk PDS 70
- 2021ApJ...907L..27A (2021): Complications in the ALMA Detection of Phosphine at Venus
- 2021ApJ...908...54W (2021): ALMA Measures Rapidly Depleted Molecular Gas Reservoirs in Massive Quiescent Galaxies at z ∼ 1.5
- 2021ApJ...908..192S (2021): ALMA 1.3 mm Survey of Lensed Submillimeter Galaxies Selected by Herschel: Discovery of Spatially Extended SMGs and Implications
- 2021ApJ...908..235I (2021): Subaru High-z Exploration of Low-luminosity Quasars (SHELLQs). XII. Extended [C II] Structure (Merger or Outflow) in a z = 6.72 Red Quasar
- 2021ApJ...908..250H (2021): ALMA Observations of the Inner Cavity in the Protoplanetary Disk around Sz 84
- 2021ApJ...909..212K (2021): ALMA Observation of the Protoplanetary Disk around WW Cha: Faint Double-peaked Ring and Asymmetric Structure
- 2021ApJ...910...89B (2021): The Physical Drivers of the Luminosity-weighted Dust Temperatures in High-redshift Galaxies
- 2021ApJ...910..148M (2021): Revealing a Centrally Condensed Structure in OMC-3/MMS 3 with ALMA High-resolution Observations
- 2021ApJ...914...36I (2021): Subaru High-z Exploration of Low-luminosity Quasars (SHELLQs). XIII. Large-scale Feedback and Star Formation in a Low-luminosity Quasar at …
- 2021ApJ...917...99Y (2021): ALMA Observations of the Sub-kpc Structure of the Host Galaxy of a z = 6.5 Lensed Quasar: A Rotationally Supported Hyper-Starburst System a…
- 2021ApJ...921...97J (2021): Molecular Line Observations in Two Dusty Star-forming Galaxies at z = 6.9
- 2021MNRAS.501.2934C (2021): The Ophiuchus DIsc Survey Employing ALMA (ODISEA) - III. The evolution of substructures in massive discs at 3-5 au resolution
- 2021MNRAS.501.5973F (2021): ALMA detects molecular gas in the halo of the powerful radio galaxy TXS 0828+193
- 2021MNRAS.502..521D (2021): Disc-jet coupling changes as a possible indicator for outbursts from GX 339-4 remaining within the X-ray hard state
- 2021MNRAS.502.5390P (2021): A ∼75 per cent occurrence rate of debris discs around F stars in the β Pic moving group
- 2021MNRAS.503.5583B (2021): Resolving discs and mergers in z ∼ 2 heavily reddened quasars and their companion galaxies with ALMA
- 2021MNRAS.506.1978L (2021): High-resolution ALMA and HST images of q<SUP>1</SUP> Eri: an asymmetric debris disc with an eccentric Jupiter
- 2021MNRAS.507.2531Z (2021): On dust evolution in planet-forming discs in binary systems - II. Comparison with Taurus and ρ Ophiuchus (sub-)millimetre observations: dis…
- 2021MNRAS.507.3139N (2021): Four new planetesimals around typical and pre-main-sequence stars (PLATYPUS) debris discs at 8.8 mm
- 2021MNRAS.508.5259M (2021): An ACA 1 mm survey of HzRGs in the ELAIS-S1: survey description and first results
- 2021NatAs...5..319P (2021): A titanic interstellar medium ejection from a massive starburst galaxy at redshift 1.4
- 2021PSJ.....2....3M (2021): Tropospheric Composition and Circulation of Uranus with ALMA and the VLA
- 2022A&A...659L...1L (2022): Size and albedo of the largest detected Oort-cloud object: Comet C/2014 UN<SUB>271</SUB> (Bernardinelli-Bernstein)
- 2022A&A...661A.125W (2022): Radio properties of the OH megamaser galaxy IIZw 096
- 2022A&A...662A.121R (2022): Observational constraints on gas disc sizes in the protoplanetary discs of multiple systems in the Taurus region
- 2022A&A...664A..63X (2022): Starbursts with suppressed velocity dispersion revealed in a forming cluster at z = 2.51
- 2022A&A...665A...3J (2022): Diagnosing deceivingly cold dusty galaxies at 3.5 &lt; z &lt; 6: A substantial population of compact starbursts with high infrared optical …
- 2022A&A...666A..39M (2022): A first search of transients in the Galactic center from 230 GHz ALMA observations
- 2022A&A...668L...4G (2022): The uncertain interstellar medium of high-redshift quiescent galaxies: Impact of methodology
- 2022ApJ...926..159I (2022): ALMA Sub-arcsecond-resolution 183 GHz H<SUB>2</SUB>O and Dense Molecular Line Observations of Nearby Ultraluminous Infrared Galaxies
- 2022ApJ...930L...3W (2022): ALMA Discovery of a Disk around the Planetary-mass Companion SR 12 c
- 2022ApJ...939L...6B (2022): First Millimeter Flares Detected from ϵ Eridani with the Atacama Large Millimeter/submillimeter Array
- 2022Icar..37214722L (2022): Pluto's atmosphere observations with ALMA: Spatially-resolved maps of CO and HCN emission and first detection of HNC
- 2022MNRAS.510.3734D (2022): A high-resolution investigation of the multiphase ISM in a galaxy during the first two billion years
- 2022MNRAS.512.2426M (2022): Modelling high-resolution ALMA observations of strongly lensed dusty star-forming galaxies detected by Herschel
- 2022MNRAS.513.5790C (2022): Variable structure in the PDS 70 disc and uncertainties in radio-interferometric image restoration
- 2022MNRAS.514.5035L (2022): WISDOM project - XI. Star formation efficiency in the bulge of the AGN-host Galaxy NGC 3169 with SITELLE and ALMA
- 2022MNRAS.515.1751W (2022): Dual constraints with ALMA: new [O III] 88-μm and dust-continuum observations reveal the ISM conditions of luminous LBGs at z 7
- 2022MNRAS.516.4066L (2022): WISDOM Project - XIII. Feeding molecular gas to the supermassive black hole in the starburst AGN-host galaxy Fairall 49
- 2022MNRAS.517.2546L (2022): High-resolution ALMA and HST imaging of κCrB: a broad debris disc around a post-main-sequence star with low-mass companions
- 2023A&A...673A.116K (2023): Exploring the environment, magnetic fields, and feedback effects of massive high-redshift galaxies with [C II]
- 2023A&A...674A.101M (2023): Cosmo-tomography toward PKS 1830‒211: Variability of the quasar and of its foreground molecular absorption monitored with ALMA
- 2023A&A...675A..85M (2023): The ALMA Frontier Fields Survey. VI. Lensing-corrected 1.1 mm number counts in Abell 2744, MACSJ0416.1-2403, MACSJ1149.5+2223, Abell 370, a…
- 2023A&A...676A...4C (2023): FAUST. IX. Multiband, multiscale dust study of L1527 IRS. Evidence for variations in dust properties within the envelope of a class 0/I you…
- 2023A&A...679A.119R (2023): PRUSSIC. II. ALMA imaging of dense-gas tracers in SDP.81: Evidence for low mechanical heating and a sub-solar metallicity in a z = 3.04 dus…
- 2023ApJ...945...40C (2023): Multifrequency Black Hole Imaging for the Next-generation Event Horizon Telescope
- 2023ApJ...946L..41S (2023): The Detection of Hot Molecular Cores in the Small Magellanic Cloud
- 2023ApJ...948..134P (2023): 183 GHz Water Megamasers in Active Galactic Nuclei: A New Accretion Disk Tracer
- 2023ApJ...954..197I (2023): ALMA Measurement of 10 kpc Scale Lensing-power Spectra toward the Lensed Quasar MG J0414+0534
- 2023MNRAS.519...34H (2023): ALMACAL VIII: a pilot survey for untargeted extragalactic CO emission lines in deep ALMA calibration data
- 2023MNRAS.520.1613M (2023): Probing general relativity in galactic scales at z 0.3
- 2023MNRAS.521.2962F (2023): Estimating dust temperature and Far-IR luminosity of high-redshift galaxies using ALMA single-band continuum observations
- 2023MNRAS.523.4970N (2023): Resolving the binary components of the outbursting protostar HBC 494 with ALMA
- 2023MNRAS.524..923Z (2023): The large molecular gas fraction of post-starburst galaxies at z &gt; 1
- 2023MNRAS.526.5401C (2023): An ALMA Survey of M-dwarfs in the Beta Pictoris Moving Group with two new debris disc detections
- 2023NatAs...7..684K (2023): Azimuthal C/O variations in a planet-forming disk
- 2023NatAs...7.1048C (2023): Evidence for auroral influence on Jupiter's nitrogen and oxygen chemistry revealed by ALMA
- 2023PASJ...75..311K (2023): Galaxy clusters at z ∼ 1 imaged by ALMA with the Sunyaev-Zel'dovich effect
- 2023PASJ...75..424O (2023): ALMA Band 6 high-resolution observations of the transitional disk around SY Chamaeleontis
- 2023PASJ...75L...1K (2023): ALMA detection of 321 GHz water maser emission in the radio galaxy NGC 1052
- 2023PASP..135b5002C (2023): A Characterization of the ALMA Phasing System at 345 GHz
- 2023PASP..135f4503Z (2023): Regularized Maximum Likelihood Image Synthesis and Validation for ALMA Continuum Observations of Protoplanetary Disks
- 2023PSJ.....4..142C (2023): Thermal Properties of the Leading Hemisphere of Callisto Inferred from ALMA Observations
- 2023PSJ.....4..193B (2023): Masses and Densities of Dwarf Planet Satellites Measured with ALMA
- 2023PSJ.....4..206R (2023): ALMA Observations of the DART Impact: Characterizing the Ejecta at Submillimeter Wavelengths
- 2024A&A...681A.110W (2024): A<SUP>3</SUP>COSMOS: Dissecting the gas content of star-forming galaxies across the main sequence at 1.2 ≤ z &lt; 1.6
- 2024A&A...682A..55M (2024): High-resolution ALMA observations of compact discs in the wide-binary system Sz 65 and Sz 66
- 2024A&A...682A..61C (2024): A dusty streamer infalling onto the disk of a class I protostar. ALMA dual-band constraints on grain properties and the mass-infall rate
- 2024A&A...682A.186L (2024): Feeding and feedback processes in the Spiderweb proto-intracluster medium
- 2024A&A...682L...3P (2024): Ordered magnetic fields around the 3C 84 central black hole
- 2024A&A...683A..62M (2024): Protonated acetylene in the z = 0.89 molecular absorber toward PKS 1830-211
- 2024A&A...683A.141R (2024): AB Aur, a Rosetta stone for studies of planet formation. III. Continuum observations at 2 and 7 mm
- 2024A&A...684A..23T (2024): Fitting pseudo-Sérsic (Spergel) light profiles to galaxies in interferometric data: The excellence of the uυ-plane
- 2024A&A...684A.200G (2024): The GRAVITY young stellar object survey. XIII. Tracing the time-variable asymmetric disk structure in the inner AU of the Herbig star HD 98…
- 2024A&A...685A..54V (2024): Disk Evolution Study Through Imaging of Nearby Young Stars (DESTINYS): The SPHERE view of the Orion star-forming region
- 2024A&A...685A..80Z (2024): Unveiling [C II] clumps in a lensed star-forming galaxy at z ∼ 3.4
- 2024A&A...686A.187P (2024): The ALPINE-ALMA [CII] survey: Dust emission effective radius up to 3 kpc in the early Universe
- 2024A&A...686A.201N (2024): ALMA view of the L1448-mm protostellar system on disk scales: CH<SUB>3</SUB>OH and H<SUP>13</SUP>CN as new disk wind tracers
- 2024A&A...686A.206Y (2024): First ALMA observations of the HD 105211 debris disc: A warm dust component close to a gigayear-old star
- 2024A&A...687A.188K (2024): Recovering the gas properties of protoplanetary disks through parametric visibility modeling: MHO 6
- 2024A&A...687A.193W (2024): Continuum and spectral-line observations of the OH megamaser galaxy IRAS 01298‒0744
- 2024A&A...687A.308S (2024): Constraining the stellar masses and origin of the protostellar VLA 1623 system
- 2024A&A...688A.149D (2024): Disk Evolution Study Through Imaging of Nearby Young Stars (DESTINYS): PDS 111, an old T Tauri star with a young-looking disk
- 2024A&A...689A..41V (2024): XLSSC 122 caught in the act of growing up: Spatially resolved SZ observations of a z = 1.98 galaxy cluster
- 2024A&A...689A..85G (2024): MINDS: A multi-instrument investigation into the molecule-rich JWST-MIRI spectrum of the DF Tau binary system
- 2024A&A...689A.104D (2024): From traffic jams to roadblocks: The outer regions of TW Hya with ALMA Band 8
- 2024A&A...689A.283L (2024): ALMA reveals a dust-obscured galaxy merger at cosmic noon
- 2024A&A...689A.299M (2024): Prospects of directly using closure traces for imaging in very long baseline interferometry
- 2024A&A...689A.317G (2024): Continuum and molecular emission from the inner regions of the symbiotic system R Aquarii
- 2024A&A...690A..55S (2024): NOEMA formIng Cluster survEy (NICE): Characterizing eight massive galaxy groups at 1.5 &lt; z &lt; 4 in the COSMOS field
- 2024A&A...690A.197M (2024): The ALMA-CRISTAL survey: Widespread dust-obscured star formation in typical star-forming galaxies at z = 4─6
- 2024A&A...690L..16J (2024): A photo-z cautionary tale: Redshift confirmation of COSBO-7 at z = 2.625
- 2024A&A...692A.155K (2024): Binary orbit and disks properties of the RW Aur system using ALMA observations
- 2024A&A...692A.205B (2024): The putative center in NGC 1052
- 2024ApJ...960....1L (2024): A Centiparsec-scale Compact Radio Core in the Nearby Galaxy M60
- 2024ApJ...961....2K (2024): PASSAGES: The Wide-ranging, Extreme Intrinsic Properties of Planck-selected, Lensed Dusty Star-forming Galaxies
- 2024ApJ...961...28H (2024): Dual-band Observations of the Asymmetric Ring around CIDA 9A: Dead or Alive?
- 2024ApJ...962..166W (2024): Vertical Structure of Gas and Dust in Four Debris Disks
- 2024ApJ...963...19N (2024): On the Evidence for Molecular Outflows in High-redshift Dusty Star-forming Galaxies
- 2024ApJ...963..164R (2024): The Disk Orientations of Perseus Protostellar Multiples at ∼8 au Resolution
- 2024ApJ...966...59S (2024): Small and Large Dust Cavities in Disks around Mid-M Stars in Taurus
- 2024ApJ...967..164X (2024): Maser Activity of Organic Molecules toward Sgr B2(N)
- 2024ApJ...970...75Z (2024): The Resolved Star Formation Law in NGC 7469 from JWST, ALMA, and VLA
- 2024ApJ...972..163L (2024): First JVLA Radio Observation on PDS 70
- 2024ApJ...973..135H (2024): Constraints on the Gas-phase C/O Ratio of DR Tau's Outer Disk from CS, SO, and C<SUB>2</SUB>H Observations
- 2024ApJ...974..102S (2024): Hints of Planet Formation Signatures in a Large-cavity Disk Studied in the AGE-PRO ALMA Large Program
- 2024ApJ...974..306S (2024): Constraints on the Physical Origin of Large Cavities in Transition Disks from Multiwavelength Dust Continuum Emission
- 2024ApJ...976..132H (2024): High-resolution ALMA Observations of Richly Structured Protoplanetary Disks in σ Orionis
- 2024ApJ...976..258K (2024): Chemistry in the GG Tau A Disk: Constraints from H<SUB>2</SUB>D<SUP>+</SUP>, N<SUB>2</SUB>H<SUP>+</SUP>, and DCO<SUP>+</SUP> High Angular R…
- 2024ApJ...977...60Q (2024): Evidence for a Sharp CO Snow Line Transition in a Protoplanetary Disk and Implications for Millimeter-wave Observations of CO Isotopologues
- 2024ApJ...977..190X (2024): Constraining the Excitation of Molecular Gas in Two Quasar-starburst Systems at z ∼ 6
- 2024MNRAS.528.5019H (2024): An optimal ALMA image of the Hubble Ultra Deep Field in the era of JWST: obscured star formation and the cosmic far-infrared background
- 2024MNRAS.529.3601R (2024): Observations of spiral and streamer on a candidate proto-brown dwarf
- 2024MNRAS.532.1752R (2024): Inner walls or vortices? Crescent-shaped asymmetries in ALMA observations of protoplanetary discs
- 2024MNRAS.532.4645H (2024): Dust beyond the torus: revealing the mid-infrared heart of local Seyfert ESO 428-G14 with JWST/MIRI
- 2024MNRAS.532L..36R (2024): HCN as a probe of the inner disc in a candidate proto-brown dwarf
- 2024MNRAS.535.1533B (2024): A novel high-z submm galaxy efficient line survey in ALMA Bands 3 through 8 - an ANGELS pilot
- 2024NatAs...8..587F (2024): Resolved ALMA observations of water in the inner astronomical units of the HL Tau disk
- 2024Natur.633..323V (2024): One month convection timescale on the surface of a giant evolved star
- 2024PASJ...76..340K (2024): Sub-parsec-scale jet-driven water maser with possible gravitational acceleration in the radio galaxy NGC 1052
- 2024PASJ...76..437Y (2024): ALMA 2D super-resolution imaging of Taurus-Auriga protoplanetary disks: Probing statistical properties of disk substructures
- 2024PSJ.....5..230D (2024): Surface Properties of the Kalliope─Linus System from ALMA and VLA Data
- 2025A&A...693A..17D (2025): Unveiling dust, molecular gas, and high star-formation efficiency in extremely UV bright star-forming galaxies at z ∼ 2.1─3.6
- 2025A&A...693A..49S (2025): A complete Herbig disk mass survey in Orion
- 2025A&A...693A.151M (2025): REsolved ALMA and SMA Observations of Nearby Stars (REASONS): A population of 74 resolved planetesimal belts at millimetre wavelengths
- 2025A&A...693A.174E (2025): Molecular gas stratification and disturbed kinematics in the Seyfert galaxy MCG-05-23-16 revealed by JWST and ALMA
- 2025A&A...693A.237I (2025): The ALMA-CRISTAL Survey: Spatial extent of [CII] line emission in star-forming galaxies at z = 4−6
- 2025A&A...693A.309S (2025): Behind the dust veil: A panchromatic view of an optically dark galaxy at z = 4.82
- 2025A&A...694A.147G (2025): MINDS: The influence of outer dust disc structure on the volatile delivery to the inner disc
- 2025A&A...694A.218B (2025): Revealing the hidden cosmic feast: A z = 4.3 galaxy group hosting two optically dark, efficiently star-forming galaxies
- 2025A&A...695A..23S (2025): Molecular gas and dust properties in z &gt; 7 quasar hosts
- 2025A&A...695A.233R (2025): A multifrequency study of sub-parsec jets with the Event Horizon Telescope
- 2025A&A...696A.232G (2025): A high-resolution survey of protoplanetary disks in Lupus and the nature of compact disks
- 2025A&A...698A.165A (2025): Confirmation of a ring structure in the disk around MP Mus (PDS 66) with ALMA Band 7 observations
- 2025A&A...698A.183D (2025): Dust populations from 30 to 1000 au in the debris disk of HD 120326: Panchromatic view with VLT/SPHERE, ALMA, and HST/STIS
- 2025A&A...699A.256P (2025): The ALMA-CRISTAL survey: Extended [CII] emission in an interacting galaxy system at z ∼ 5.5
- 2025A&A...699A.265G (2025): First polarization study of the M87 jet and active galactic nuclei at submillimeter wavelengths with ALMA
- 2025A&A...699A.279D (2025): Origin of the ring ellipticity in the black hole images of M87<SUP>*</SUP>
- 2025A&A...699A.373F (2025): Inner disc and circumplanetary material in the PDS 70 system: Insights from multi-epoch, multi-frequency ALMA observations
- 2025A&A...700A.165B (2025): GAMA 526784: The progenitor of a globular cluster-rich ultra-diffuse galaxy?: II. Molecular gas, neutral gas, and environment
- 2025A&A...700A.188C (2025): FAUST: XXVI. The dust opacity spectral indices of protostellar envelopes bridge the gap between interstellar medium and disks
- 2025A&A...700A.278R (2025): CO(1─0) imaging reveals 10-kiloparsec molecular gas reservoirs around star-forming galaxies at high redshift
- 2025A&A...700L...5G (2025): Edge-On Disk Study (EODS): I. Thermal structure of the Flying Saucer disk
- 2025A&A...701A.203S (2025): Multi-scale radiative-transfer model of the protoplanetary disc DoAr 44
- 2025A&A...701A.234Z (2025): Noema formIng Cluster survEy (NICE): A census of star formation and cold gas properties in massive protoclusters at 1.5 &lt; z &lt; 4
- 2025A&A...702A..18D (2025): Multi-frequency observations of PDS70c: Radio emission mechanisms in the circumplanetary environment
- 2025A&A...703A..15M (2025): Discovery of carbon monoxide emission from five debris disks around young A-type stars
- 2025A&A...704A..18O (2025): High-angular-resolution ALMA imaging of the inhomogeneous dynamical atmosphere of the asymptotic giant branch star W Hya: SiO, H<SUB>2</SUB…
- 2025ApJ...984L..16G (2025): exoALMA. XI. ALMA Observations and Hydrodynamic Models of LkCa 15: Implications for Planetary Mass Companions in the Dust Continuum Cavity
- 2025ApJ...986L..11S (2025): Hints of Disk Substructure in the First Brown Dwarf with a Dynamical Mass Constraint
- 2025ApJ...986L..22R (2025): The First Detection of Molecular Activity in the Largest Known Oort Cloud Comet: ALMA Imaging of C/2014 UN271 (Bernardinelli─Bernstein) at …
- 2025ApJ...987...61R (2025): Resolved ALMA [C II] 158 μm Observations at Cosmic Noon: Interstellar Medium Structure and Dynamics of the Starbursting QSO SDSS J1000
- 2025ApJ...988..106H (2025): Grand Design Spiral Arms in the Compact, Embedded Protoplanetary Disk of Haro 6-13
- 2025ApJ...989...83B (2025): CO Emission and Absorption-line Survey of the M87 Nucleus Using Archival ALMA Imaging
- 2025ApJ...990L..31B (2025): ALMA Reveals Bright Circumgalactic Emission and a Biconical Outflow in z ∼ 6.4 Quasar PSOJ183+05
- 2025ApJ...990L..70L (2025): Discovery of Hα Emission from a Protoplanet Candidate around the Young Star 2MASS J16120668─3010270 with MagAO-X
- 2025ApJ...991..176W (2025): Radiative Transfer Modeling of a Shadowed Protoplanetary Disk Assisted by a Neural Network
- 2025ApJ...993...90S (2025): ALMA High-resolution Observation for the Transitional Disk Around IRAS 04125+2902
- 2025ApJ...993..134K (2025): A New Precise Measurement of the Cosmic Microwave Background Radiation Temperature at z = 0.89 toward PKS1830─211
- 2025ApJ...993L..40S (2025): Unusually High Gas-to-dust Ratios Observed in High-redshift Quiescent Galaxies
- 2025ApJ...994..214T (2025): Dynamical Masses for 23 Pre-main-sequence Stars in Upper Scorpius: A Critical Test of Stellar Evolutionary Models
- 2025ApJ...995L..51G (2025): The CO-to-H<SUB>2</SUB> Conversion Factor in the Milky Way's Central Parsec
- 2025MNRAS.536.3757A (2025): The kinematics of massive high-redshift dusty star-forming galaxies
- 2025MNRAS.537..520Z (2025): WISDOM Project - XXII. A 5 per cent precision CO-dynamical supermassive black hole mass measurement in the galaxy NGC 383
- 2025MNRAS.537.1163A (2025): The onset of bar formation in a massive galaxy at z ~ 3.8
- 2025MNRAS.538.2358S (2025): High angular resolution evidence of dust traps from deep ALMA Band 3 observations of LkCa15
- 2025MNRAS.541...71M (2025): ALMA millimetre-wavelength imaging of HD 138965: new constraints on the debris dust composition and presence of planetary companions
- 2025MNRAS.543..862V (2025): Low-frequency spectra of neutron star + OB supergiant binaries: Does wind density drive persistent and flaring modes of accretion?
- 2025MNRAS.543.2723P (2025): Observational constraints on evolution of dust disc properties in Upper Scorpius
- 2025NatAs...9.1476C (2025): A D/H ratio consistent with Earth's water in Halley-type comet 12P from ALMA HDO mapping
- 2025Natur.642..905L (2025): Evidence for a sub-Jovian planet in the young TWA 7 disk
- 2025PASJ...77..834O (2025): Detailed analysis of multiline molecular distributions in the Seyfert galaxy NGC 1068: Possible effect of the active galactic nucleus outfl…
- 2025PASP..137l4501T (2025): The ViSta Method for Stacking in the Fourier Domain and its Application to the Dusty Star-forming Galaxies in the ALMA Science Archive
- 2025PSJ.....6..183C (2025): A Multifrequency Global View of Callisto's Thermal Properties from ALMA
- 2026A&A...705A..49Z (2026): The <SUP>12</SUP>CO gas structures of protoplanetary disks in the Upper Scorpius region
- 2026A&A...705A..81K (2026): Resolving the molecular gas emission of the z ∼ 2.5─2.8 starburst galaxies SPT 0125-47 and SPT 2134-50
- 2026A&A...705A.196H (2026): The ALMA survey to Resolve exoKuiper belt Substructures (ARKS): II. The radial structure of debris discs
- 2026A&A...705A.197Z (2026): The ALMA survey to Resolve exoKuiper belt Substructures (ARKS): III. The vertical structure of debris disks
- 2026A&A...705A.202M (2026): The ALMA survey to Resolve exoKuiper belt Substructures (ARKS): VIII. A dust arc and non-Keplerian gas kinematics in HD 121617
- 2026A&A...705A.209L (2026): A search for cold molecular outflows in cosmic-noon galaxies
- 2026A&A...706A...4R (2026): Resolving the terrestrial planet-forming region of HD 172555 with ALMA: I. Post-impact dust distribution
- 2026A&A...706A.174A (2026): Hiding behind a curtain of dust: Gas and dust properties of an ultra-luminous strongly-lensed z = 3.75 galaxy behind the Milky Way disc
- 2026A&A...706A.292S (2026): Dissecting the dust distribution and polarization around two B213 young stellar objects with ALMA
- 2026A&A...706A.365M (2026): A sub-ppm upper limit on the cosmological variations of the fine structure constant α
- 2026A&A...707A.144S (2026): Spatially resolved star formation relations in local luminous infrared galaxies along the complete merger sequence
- 2026A&A...707A.252K (2026): Detailed lens modeling and kinematics of the submillimeter galaxy G09v1.97: An analysis of CO, H<SUB>2</SUB>O, H<SUB>2</SUB>O<SUP>+</SUP>, …
- 2026A&A...707A.255C (2026): ALMA Band 1 observations of the ρ Oph W filament: I. Enhanced power from excess microwave emission at high spatial frequencies
- 2026A&A...708A.251X (2026): Linear filament and nested cluster evolution tomography (LANCET): I. Capture the evolution of dense gas in 14-parsec filament G316.8
- 2026A&A...708L...1Z (2026): Benchmarking pre-main sequence stellar evolutionary tracks using disk-based dynamical stellar masses
- 2026A&A...709A..14Z (2026): Gas excitation of post-SB galaxies at 0.6 &lt; z &lt; 1.3
- 2026A&A...709A.174F (2026): The circumbinary disc of HD 34700A: II. Analysis of a strong dust asymmetry
- 2026A&A...710A..63L (2026): Constraining the magnetic field strength of a flaring radio core in the compact steep spectrum source 3C 138
- 2026A&A...710L..10C (2026): Hourly radio variability of PDS 70c from time-differential photometry
- 2026A&A...712A.244H (2026): Multiband ALMA polarimetry of the jet base and kiloparsec-scale jet of 3C 273: A multicomponent Faraday structure in the nucleus
- 2026ApJ...999L..32R (2026): CH<SUB>3</SUB>OH and HCN in Interstellar Comet 3I/ATLAS Mapped with the ALMA Atacama Compact Array: Distinct Outgassing Behaviors and a Rem…
- 2026ApJ..1000..141K (2026): First Determination of the Cosmic Microwave Background Radiation Temperature at z = 0.68 Using Molecular Absorption Lines
- 2026ApJ..1001..124M (2026): Multiwavelength ALMA Imaging of HD 34282: Dust-trapping Signatures of a Vortex Candidate
- 2026ApJ..1003L..30W (2026): First Detection of HC<SUB>5</SUB>N in a Class II Disk around TW Hya
- 2026ApJ..1004..126K (2026): An Active Galactic Nucleus in the Antennae Galaxies?
- 2026ApJ..1005...94N (2026): Dynamical Evidence for a Billion Solar-mass Black Hole in Galaxy NGC 4061 from ALMA <SUP>12</SUP>CO(2─1) Kinematics
- 2026MNRAS.546ag167S (2026): Under the glare of a luminous quasar, the FIR continuum is still an excellent tracer of the ISM down to the central kiloparsec
- 2026MNRAS.548ag546D (2026): WISDOM project - XXVIII. Molecular gas measurement of the supermassive black hole mass of the galaxy NGC 1387
- 2026MNRAS.552g1700S (2026): Dust substructures and line perturbations driven by a forming planet in J16120
