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

=== SKILL.md (lens-modelling) ===
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
2025ApJS..278...45F); my own counts of pack lines exclude them, leaving 55 on-topic papers. Of those, about 35
fit their own lens model; the rest apply a published model or a single magnification.

## When to use

- A submm/mm-bright source shows arcs, an Einstein ring, or multiple compact components around a foreground
  galaxy or cluster (SPT, Herschel, Planck-selected DSFGs: 2013ApJ...767..132H, 2016ApJ...826..112S,
  2021A&A...645A..45C).
- You need intrinsic L_IR, SFR, dust/gas mass, size or surface density of a lensed source (divide by mu; sizes
  scale as r/sqrt(mu), 2017A&A...597A..41G).
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
     z=0.9). For ambiguous cases fit a lens model and test it: 2020ApJ...891...64F fits SIE+shear to four
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
   - Extended arcs or rings in interferometer data: fit visibilities (12 on-topic pack papers by my count,
     e.g. 2013ApJ...767..132H, 2016ApJ...826..112S, 2019ApJ...873...50D, 2018A&A...613A..34P). Authors
     prefer this because "the noise and measurement are well understood" in the uv plane
     (2016ApJ...826..112S).
   - Compact knots, quasar images, clusters: fit image positions (and sometimes flux ratios or time delays)
     with a positional error per image (2015PASJ...67...72T, 2016MNRAS.457.2936I, 2020A&A...641L...2M,
     2025ApJ...995..219F, 2016MNRAS.461..164I).
   - Combined: 2025ApJ...991...53C fits point images first, then a pixelated reconstruction with pixsrc;
     2017ApJ...843L..35W takes structural priors from an HST arc fit before fitting ALMA conjugate points.
4. **Fit a parametric lens plus source model.**
   - Mass: SIE, usually with external shear, is the default (my count: SIE in about 18 on-topic pack papers,
     e.g. 2013ApJ...767..132H, 2018Natur.553...51M, 2019ApJ...870...80L, 2026A&A...705A..81K). Variants:
     elliptical power law (2014A&A...568A..92M, 2015MNRAS.451L..40R, 2018A&A...613A..34P,
     2018ApJ...866L..12G), cored power law plus SMBH point mass (2015ApJ...811..115W, 2017ApJ...843L..35W),
     cored isothermal plus multipoles (2015PASJ...67...72T), softened isothermal (2020A&A...641L...2M),
     extra halo or companions (2025ApJ...991...53C, 2018ApJ...866L..12G), cluster PIEMD/NFW/pseudo-Jaffe
     models (2024A&A...692A.215C, 2025ApJ...995..219F, 2017A&A...600L...3C).
   - Source: Sérsic (2016ApJ...826..112S, 2019ApJ...873...50D, 2026A&A...705A..81K, 2024A&A...684A..56K),
     Gaussian (2013ApJ...767..132H, 2015ApJ...811..124S) or exponential (2019A&A...624A.138Y); add
     components as needed (four Sérsics for SPT0311-58, 2018Natur.553...51M) and select with DIC
     (2019ApJ...873...50D, 2020ApJ...905...85S).
   - Sampler: MCMC almost everywhere; emcee is named in 7 pack papers (not all of them for the lens fit), Metropolis-Hastings (2013ApJ...767..132H,
     2019A&A...624A.138Y), PSO start then emcee (2024ApJ...967...11C), MultiNest (aggregate, 1 paper).
   - Calibration nuisance terms in visibility fits: solve antenna phases at each chain step
     (2013ApJ...767..132H; also amplitude rescaling and astrometric offset per dataset,
     2016ApJ...826..112S), or marginalise over residual calibration errors (2018Natur.553...51M).
5. **Optional pixelated source reconstruction.**
   - Method: source on a pixel, Delaunay or Voronoi grid with regularisation, lens parameters from the
     parametric fit or iterated (2015MNRAS.451L..40R, 2019ApJ...870...80L, 2020ApJ...905...85S,
     2026A&A...705A..81K, 2018ApJ...866L..12G).
   - Regularisation: gradient is the most common form (2015MNRAS.451L..40R, 2018Natur.553...51M,
     2020ApJ...905...85S, 2018Sci...361.1016S; chosen "to prevent the source from being overly smoothed",
     2015MNRAS.451L..40R); constant regularisation in PyAutoLens (2026A&A...705A..81K). Set its strength by
     maximising Bayesian evidence at fixed lens parameters, alternating with the lens MCMC until both converge
     (2020ApJ...905...85S, 2019ApJ...870...80L).
   - Randomised Voronoi grids: average 50 realisations weighted by likelihood (2020ApJ...905..152D).
6. **Line cubes and differential lensing.**
   - Fix the lens from the continuum (or all channels combined, 2018A&A...613A..34P) and reconstruct each
     channel or velocity bin: 40 km/s (2018Natur.553...51M), 50 km/s (2019ApJ...870...80L), 75-250 km/s
     (2019ApJ...873...50D), 105 km/s bins (2019A&A...624A.138Y), red/blue halves at low S/N
     (2026A&A...705A..81K). Test alternative channelisations (100-400 km/s, 2015ApJ...811..124S).
   - For weak lines, transfer the per-channel magnification of a bright line by nearest velocity, which
     assumes the weak line follows the bright line's kinematics (2024A&A...684A..56K).
7. **Magnification and its uncertainty.**
   - Definition: ratio of source-plane to image-plane flux (2015MNRAS.451L..40R), flux-weighted over the
     source (2018Natur.553...51M), luminosity-weighted from amplification maps and the line image
     (2021A&A...645A..45C), restricted to pixels with S/N >= 3 (2018A&A...610A..53M), or mean in an
     aperture (2024A&A...692A.215C). State which.
   - Uncertainty: recompute mu over posterior draws, 100 (2024ApJ...967...11C, 2024A&A...692A.215C, which
     quotes the median and (p84-p16)/2) or 1000 (2025ApJ...995..219F). Report mu per component and per
     tracer.
8. **Source-plane resolution and products.**
   - Lens a mock point source through the best model and reconstruct it to get the effective resolution
     (0.13x0.15 arcsec, 0.12x0.12 near the caustic, 2019ApJ...870...80L; also 2018Sci...361.1016S); or
     reconstruct beams on a grid of image positions (2015ApJ...806L..17S).
   - Make source-plane S/N maps (2026A&A...705A..81K), then morphology (IMFIT, 2019A&A...624A.138Y) and
     kinematics on source-plane cubes (3DBarolo: 2019A&A...624A.138Y, 2025NatAs...9.1553F; galpak3d with
     PSF homogenisation: 2018ApJ...866L..12G).
9. **Intrinsic properties.** Divide fluxes by mu (2013ApJ...767..132H), sizes by sqrt(mu) when not measured
   in the source plane (2017A&A...597A..41G), and only apply the dust-derived mu to the far-IR part of the
   SED (2015MNRAS.451L..40R). If no model exists, a sample median mu (5.5, 2020ApJ...902...78R) makes the
   result an estimate, as those authors say.

## Parameter defaults and ranges

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| Lens mass profile | SIE + external shear | power law, cored PL + SMBH, softened/cored isothermal, multipoles, NFW, PIEMD | SIE in ~18 (my count) | 2013ApJ...767..132H, 2015PASJ...67...72T, 2018A&A...613A..34P |
| SIE free parameters | 5 (theta_E, q, PA, x, y) | 5-12 with shear/multipoles | 4 (stated) | 2013ApJ...767..132H, 2020A&A...641L...2M, 2018A&A...613A..34P, 2015PASJ...67...72T |
| External shear prior | Gaussian, width 0.05 | mean 0.05 or 0.00 | 2 | 2020ApJ...891...64F, 2025ApJ...991...53C |
| Einstein radius prior | uniform | U[0.1, 1.1 arcsec]; lognormal 0.1 dex | 2 | 2019A&A...624A.138Y, 2025ApJ...991...53C |
| Lens centre | tied to optical or ring centre | fixed at ring centre with uniform prior; within 0.2 arcsec of HST centroid | 2 | 2026A&A...705A..81K, 2018ApJ...867..140L |
| Lens axis ratio prior | Normal(0.5, 0.2) | shape priors 0.05-0.20 | 2 | 2019A&A...624A.138Y, 2025ApJ...991...53C |
| Source profile | Sérsic | Gaussian, exponential, point | ~7 Sérsic (my count) | 2016ApJ...826..112S, 2019ApJ...873...50D, 2013ApJ...767..132H |
| Source size prior | Normal(0.1, 0.03 arcsec) in [0, 0.2] | | 1 | 2019A&A...624A.138Y |
| Image-position error | 0.02-0.03 arcsec | 20 mas; beam/4; 0.02 radial / 0.05 tangential | 5 | 2020ApJ...891...64F, 2025ApJ...991...53C, 2015PASJ...67...72T, 2016MNRAS.457.2936I, 2017ApJ...843L..35W |
| Image flux error (position fits) | 10% | | 1 | 2020ApJ...891...64F |
| Visibility time averaging | until binned uv spread ~10 m | 3-10 min, 10-15 m | 3 | 2018Sci...361.1016S, 2019ApJ...873...50D, 2020ApJ...905...85S |
| Line velocity binning | 40-105 km/s | 40-400 km/s; 2 bins at low S/N | 6 | 2018Natur.553...51M, 2019ApJ...873...50D, 2026A&A...705A..81K |
| Regularisation | gradient, evidence-optimised | constant | 5 | 2015MNRAS.451L..40R, 2020ApJ...905...85S, 2026A&A...705A..81K |
| emcee run | 1000 walkers, 1000 burn-in + 1000 steps | chain 5x10^5 (Glee) | 2 | 2019ApJ...873...50D, 2015ApJ...811..115W |
| Posterior draws for mu | 100 | 100-1000 | 3 | 2024ApJ...967...11C, 2024A&A...692A.215C, 2025ApJ...995..219F |
| pixsrc noise level | raised to 80 uJy/beam | | 1 | 2025ApJ...991...53C |
| Cosmology | flat LCDM, H0 ~70, Om ~0.3 | H0 67.4-73.3, Om 0.26-0.308 | 10 (my count) | 2014A&A...568A..92M, 2019ApJ...873...50D, 2020A&A...641L...2M |

Magnifications reported span about 1.3 (2018Natur.553...51M, component E) to ~58 (2020ApJ...891...64F, poorly
constrained); typical galaxy-scale DSFG values are 5-30 (2013ApJ...767..132H, 2019ApJ...873...50D,
2024ApJ...967...11C).

## Software

Counts are the pack's software aggregate over all 61 papers (lens codes only; SED and imaging tools omitted).

| Code | Pack count | Used for | Examples |
|---|---|---|---|
| visilens (+ emcee) | 7 | parametric SIE + Sérsic fits to visibilities | 2016ApJ...826..112S, 2019ApJ...873...50D, 2024A&A...684A..56K |
| emcee | 7 | sampler for visilens, lenstronomy, glafic; also SED and uv fits | 2024ApJ...967...11C, 2025ApJ...995..219F |
| Lenstool | 6 | cluster and group models, amplification maps | 2024A&A...692A.215C, 2021A&A...645A..45C, 2017A&A...600L...3C |
| PyAutoLens / AutoLens | 4 + 1 | uv-plane parametric then Voronoi pixelated sources | 2026A&A...705A..81K, 2019A&A...624A.138Y, 2026ApJ..1002L..28Y |
| glafic | 4 | position-based galaxy and cluster models | 2015PASJ...67...72T, 2020ApJ...891...64F, 2025ApJ...995..219F |
| RIPPLES | 3 | pixelated visibility reconstruction | 2019ApJ...870...80L, 2020ApJ...905...85S |
| gravlens / lensmodel | 3 + 1 | position, flux-ratio and time-delay fits | 2016MNRAS.461..164I, 2020A&A...641L...2M, 2025ApJ...991...53C |
| Glee | 3 | power-law + SMBH models, conjugate points | 2015ApJ...811..115W, 2017ApJ...843L..35W |
| sl_fit | 2 | image-plane parametric lens + source | 2019A&A...624A.138Y |
| lenstronomy | 2 | multi-band JWST models, simulated lensed polarisation | 2024ApJ...967...11C, 2023Natur.621..483G |
| Pixelated code of Hezaveh et al. 2016 (not public) | 3 | gradient-regularised visibility reconstruction | 2018Natur.553...51M, 2018Sci...361.1016S |
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
- **Bimodal posteriors** with compact-array data (2013ApJ...767..132H, 2018Sci...361.1016S); longer
  baselines can break them (2013ApJ...767..132H). Run several chains and look.
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
- **Size bias.** Strongly lensed samples favour compact sources (2015MNRAS.451L..40R); conjugate-point fits
  carry their own degeneracies (2017ApJ...843L..35W).
- **Unreported settings.** Cards most often flag missing priors, MCMC settings, regularisation values, source
  grid sizes and lens code release (2013ApJ...767..132H, 2018Natur.553...51M, 2026A&A...705A..81K,
  2020ApJ...905...85S). Report all of them.

## Verification checks

What papers did:
- Residual images or visibilities consistent with noise: no residuals >3 sigma (2026A&A...705A..81K), <2.5
  sigma (2019A&A...624A.138Y), fraction of >2 sigma residuals 0.2-0.5% (2014A&A...568A..92M), 4.7% and 0.3%
  of visibilities beyond 2 and 3 sigma (2015MNRAS.451L..40R).
- Image-position rms: ~0.015 arcsec (2015ApJ...811..115W), <0.02 arcsec (2025ApJ...991...53C), 0.14 arcsec for
  a cluster model (2025ApJ...995..219F); reduced chi2 < 1 (2017ApJ...843L..35W).
- Second code or method: PyAutoLens pixelated run converges to the sl_fit model (2019A&A...624A.138Y);
  pixelated vs visilens sources agree to <15% (2018Natur.553...51M); glafic vs Glee (2017ApJ...843L..35W);
  in-house vs GRAVLENS chi2 within a few per cent (2016MNRAS.457.2936I).
- Lens parameters consistent across wavelengths (<10%, 2018Natur.553...51M) and with HST/Keck models
  (within 2 sigma, 2018A&A...613A..34P; 2015PASJ...67...72T).
- Flux recovery: mu x L'_intrinsic vs apparent L' (2019ApJ...873...50D); modelled ALMA flux vs LABOCA
  870 um within ~10% (2013ApJ...767..132H).
- Mock tests: point sources across the source plane recovered to ~25% plus a negative-bowl check at >=10% of
  peak (2020ApJ...905...85S); simulated data recover input antenna phases (2013ApJ...767..132H); lens and
  beam do not rotate polarisation (2023Natur.621..483G).
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
- 2016ApJ...826..112S: 47 SPT sources with visilens; systematics discussion
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

=== EVIDENCE PACK (lens-modelling) ===
# Evidence pack: Strong-lens modelling of ALMA sources (`lens-modelling`)

Scope: lens models in uv or image plane, magnification, source-plane reconstruction

Built from 61 non-held-out ALMA papers whose methods cards passed mechanical evidence verification (every quote below is verbatim from the paper). Years 2013-2026.
Matcher (regex over analysis steps): `lens (?:model|mass)|lensing model|lenstool|visilens|pyautolens|autolens|source[- ]plane|magnification|gravitational(?:ly)? lens`
Tagging is by regex, so a few papers may be off-topic: ignore those.

## Aggregates over all papers

### Science fields
- high_z_galaxies: 60
- agn_and_quasars: 12
- cosmology: 5
- galaxy_clusters_and_sz: 3
- milky_way_ism: 2
- star_formation: 2
- astrochemistry: 2
- other: 1

### Software named in the matched steps
- visilens: 7
- emcee: 7
- lenstool: 6
- pyautolens: 4
- glafic: 4
- ripples: 3
- gravlens: 3
- galfit: 3
- glee: 3
- sl_fit: 2
- 3dbarolo: 2
- uvmcmcfit: 2
- lenstronomy: 2
- pixellated reconstruction code (proprietary): 2
- imfit: 1
- custom mcmc code: 1
- casa: 1
- casa statwt: 1
- sli code: 1
- magphys: 1
- lensmodel: 1
- pixsrc: 1
- fast++: 1
- in-house code: 1
- sextractor: 1
- gildas: 1
- casa simobserve: 1
- cigale: 1
- fsps: 1
- prospector: 1
- dynesty: 1
- parrot: 1
- eazy: 1
- hipe: 1
- galpak3d: 1
- astropy: 1
- pixellated lens reconstruction tool (hezaveh et al. 2016): 1
- multinest: 1
- autolens: 1
- crush: 1

### Fitting methods (most common phrasings)
- MCMC Metropolis-Hastings; median and 68% intervals: 1
- Same priors as continuum model; 10x7 parameters: 1
- chi2 minimization; bootstrap uncertainties of 10%: 1
- MCMC with Metropolis-Hastings sampling, tempering (posterior^1/T); noise from differencing adjacent visibilities: 1
- Formal errors from sampling algorithms; sampler not named: 1
- MCMC for lens potential; iterative regularization/MCMC; priors not stated: 1
- best-fit chi2/dof = 6.11/3: 1
- 4 model variants; Gaussian source rejected: 1
- emcee sampling of likelihood in visibilities; 1 sigma range of posterior: 1
- linear regression log r_s vs log F with HerMES comparison: 1
- emcee affine invariant MCMC; priors beyond parameter limits not stated: 1
- MCMC posteriors; chi^2 minimization with priors: 1
- Chi-square minimization in source and image plane; Monte Carlo degeneracy corner plots: 1
- emcee MCMC; median and 1 sigma intervals: 1
- Chi-square minimization with MCMC for 68% intervals: 1
- 3DBarolo tilted-ring fit: 1
- emcee with priors from maximum-likelihood estimator: 1
- Minimizing differences between de-lensed images with astrometric/magnification constraints: 1
- chi^2 minimization; 1 sigma from parameter range with reduced chi^2 < 1: 1
- Maximum a posteriori; noise per baseline from rms of visibilities within an observing block: 1
- Grid of chi_B values, no sampler: 1
- chi^2 against visibilities, MCMC; priors not stated: 1
- two-component Gaussian fit to source-plane spectrum: 1
- Expectation values and standard deviations from the PDF of parameter-bin best-fit models: 1
- Prospector-beta with nested sampling dynesty; Chabrier IMF, 7-bin SFH, two-component dust: 1
- Penalty function with chi2 plus regularisation lambda^2||Hs||^2: 1
- MCMC, position likelihood Gaussian: 1
- emcee MCMC; likelihood from reproduced image positions plus penalty for extra images: 1
- MCMC, best fit by Bayesian evidence: 1
- Median of converged parameters, 16th/84th percentiles as uncertainty: 1
- MCMC with chi^2 metric: 1
- Particle Swarm Optimization pre-sampling, then emcee MCMC run to convergence: 1
- MCMC sampling marginalizing over residual calibration uncertainty: 1
- LENSTOOL MCMC, seven free parameters: 1
- Importance sampling: 1
- MCMC; evidence-maximized regularization: 1
- MCMC: 1
- MultiNest exploration of lens parameter space; priors not stated: 1
- MCMC; free: centroid, sigma_PIEMD, ellipticity, PA; 4000 MCMC iterations for magnification map: 1
- emcee MCMC; DIC for model selection between numbers of components: 1

### Validation checks used
- Residuals <2.5 sigma; PyAutoLens pixelized reconstruction converged to same model: 1
- Image-plane moment maps and per-channel residuals; image vs source-plane moment maps match: 1
- Residuals <1% of emission: 1
- Simulated observations recover input antenna phases; extended-array data compared with predictions: 1
- LABOCA 870 um flux agrees with modeled ALMA flux within ~10%: 1
- Residuals checked at >3σ; compared with literature magnifications: 1
- Source-plane S/N maps: 1
- Deviance information criterion, negative-bowl check (>=10% of peak), mock point-source tests across source plane (recov…: 1
- Model positions and intrinsic fluxes consistent with observations within errors: 1
- Models compared; magnification consistent across models: 1
- compared with fluxes from 1.5'' tapered images; injected fake sources: 1
- phase calibrator positions compared to literature: 1
- Fraction of >2 sigma residuals 0.2% (7 GHz) and 0.5% (CO): 1
- Compared model image peaks, shapes and orientations to observed ALMA images; rms offset <0.02'': 1
- Compared continuum and [C II] best-fit lens models, sizes and axis ratio: 1
- Chain convergence, residual images, DIC model selection: 1
- Compare mu*L'_intrinsic to apparent L' (Figure 3, Figure 8): 1
- Compared with independent ALMA (Rybak15, Dye15) and HST (Dye14) models: 1
- Monte Carlo mock cubes show Vmax/sigma0 overestimated by 4±2%; PVsplit classification indicates single disk: 1
- Photo-z compared to dropout bands and MUSE spec-z; mismatches removed: 1
- Residual position errors <0.003'' below HST errors: 1
- Code compared with GRAVLENS, chi^2 within a few percent; compared with literature models: 1
- Hypothetical observation with beam convolution gives <4% error: 1
- Visibility residuals consistent with Gaussian noise; consistency between spws and bands; error from rms scatter between…: 1
- Residuals consistent with noise; repeated on M2: 1
- Five flux methods compared; conclusions unchanged: 1
- Lens and convolution do not rotate or change P; noise adds ~10 deg uncertainty: 1
- Mock point-source visibilities reconstructed to give effective source-plane resolution: 1
- Compared with SFRs from LIR conversions and with BC03 and two-component SFH: 1
- all 27 spec-z sources have |dz|/(1+z)<0.15; outlier fraction zero: 1
- Compared with MAGPHYS where direct SED fit possible: 1
- Compared with HST and Keck lens models; within 2 sigma: 1
- rms image offset ~0.015'' for power-law models: 1
- 1000 posterior resamples for magnification uncertainty; systematics acknowledged not included: 1
- Median reduced chi2 = 1.08: 1
- Residuals consistent with noise; alternative channelizations tested: 1
- Cross-check with backwards ray tracing of F277W, F356W, F444W using the lens model: 1
- Lens parameters consistent to <10% between wavelengths; source properties agree to <15% between codes: 1
- Compared with preliminary lens models, agreement confirmed: 1
- Reduced chi2 <1: 1

### Key parameters and settings (bibcode: value)
- 2019A&A...624A.138Y: Priors: Einstein radii uniform [0.1,1.1'']; axis ratios Normal(0.5,0.2); source positions uniform ±0.2''; source axis ratio uniform [0.1,0.9]; Reff Normal(0.1'…
- 2019A&A...624A.138Y: q0 = 0.2
- 2013ApJ...767..132H: Source: 4 params; SIE lens: 5 params
- 2026A&A...705A..81K: lens centers fixed at Einstein ring centers with uniform priors; Einstein radius upper limit slightly above Spilker16
- 2026A&A...705A..81K: constant regularization scheme with one coefficient
- 2020ApJ...905...85S: visibilities averaged temporally unless binned visibility spans >10 m in uv
- 2020ApJ...891...64F: positional error 0.03''; flux error 10%
- 2017A&A...597A..41G: 10,000-240,000 iterations, 5,000 burn-in
- 2014A&A...568A..92M: limits: beta<3, T<100 K observed-frame, lambda0<2000 um
- 2025ApJ...991...53C: position uncertainty 0.03''; Einstein radius lognormal priors 0.1 dex; shape priors 0.20 (mild) or 0.05 (strong); shear 0.00±0.05
- 2025ApJ...991...53C: pixsrc noise increased to 80 uJy/beam
- 2020ApJ...905..152D: 50 Voronoi realisations per slice
- 2020ApJ...905..152D: L_IR defined at rest-frame 8-1000 um
- 2020A&A...641L...2M: Eight free parameters: source position, lens position, mass scale, softening length, ellipticity, position angle
- 2019ApJ...873...50D: time averaging up to 10 min with uv separation <15 m; velocity bins 75-250 km/s
- 2019ApJ...873...50D: 1000 chains, 1000 burn-in, 1000 extra steps
- 2015PASJ...67...72T: Position uncertainty 20 mas; 100–200 mas for 10 blended knots; 130–200 mas for HST images; N_DOF = 88
- 2025NatAs...9.1553F: free: V, sigma, PA, inclination; ring width (0.5-1.0) x PSF FWHM; AZIM normalization
- 2020A&A...633A.160C: 2500 iterations x 100 walkers per source for beta
- 2016MNRAS.457.2936I: position errors 1/4 of beam (6x8 mas); G error 0.02 arcsec
- 2016MNRAS.457.2936I: aperture radii 0.04, 0.05, 0.06 arcsec
- 2015MNRAS.451L..40R: Gradient regularisation
- 2023Natur.621..483G: 801x801 grid, 0.01'' pixel; pwv 0.6 mm; antenna configuration 2 (Cycle 8)
- 2019ApJ...870...80L: lambda fitted for fixed lens model, alternating with MCMC until convergence
- 2015ApJ...812...88M: Maraston05 SPS, Kroupa IMF, solar metallicity; grids in age, tau, A_V, delta, alpha
- 2018A&A...613A..34P: eight free parameters
- 2015ApJ...811..115W: MCMC chain length 5x10^5
- 2025ApJ...995..219F: rms image-position separation 0.14"
- 2015ApJ...811..124S: Each Gaussian has up to four free parameters: centroid, flux, size
- 2018Natur.553...51M: Four Sersic components (1 E, 3 W) for visilens
- 2015A&A...576L...2S: µ = 49 ± 5
- 2018MNRAS.475.4939A: minimum magnification mu_min = 2
- 2018MNRAS.475.4939A: halo-to-stellar mass ratio 30 for SISSA; z_lv = z_l or 2.5
- 2025ApJ...990...29H: beta_d = 2.0, Td = 80 K, mu = 1.43, L_IR error 50%
- 2018Sci...361.1016S: time averaging up to 3 min with uv separation <10 m
- 2018ApJ...867..140L: moment-0 maps collapsed over 300 km/s centered at +/-155 km/s
- 2018A&A...610A..53M: magnification mu = F_LP/F_SP for SNR>=3 pixels
- 2019A&A...628A..23A: bins from -400 to 400 km/s; outer bins widened by 4x
- 2017A&A...600L...3C: r_core=0.15 kpc, r_cut=100 kpc fixed
- 2016A&A...596A..75S: sigma ~209+-20 km/s


### Assumptions (bibcode: value)
- 2019A&A...624A.138Y: Both source components have constant magnification across SED; deflectors at z=0.626 and 1.002
- 2019A&A...624A.138Y: CO and H2O emission identical up to flux normalization
- 2019A&A...624A.138Y: R and B are thin disks
- 2013ApJ...767..132H: WMAP7 cosmology h=0.71, Om=0.27, OL=0.73
- 2013ApJ...767..132H: Standard starburst SFR conversion (Kennicutt 1998)
- 2020ApJ...905...85S: Regularization strength set by maximizing Bayesian evidence for fixed lens parameters, iterated
- 2020ApJ...891...64F: Gaussian prior on shear gamma=0.05±0.05; no prior on SIE centroid
- 2024A&A...684A..56K: Other lines follow bulk kinematics of [CII]
- 2017A&A...597A..41G: z=2 (range 1-3) for sources without spectroscopic redshift
- 2014A&A...568A..92M: Chabrier IMF; H0=70, Om=0.3, OL=0.7
- 2025ApJ...991...53C: All galaxies and halo at the same redshift z~1
- 2020ApJ...905..152D: Errors exclude systematic uncertainty of the parametric lens model
- 2020A&A...641L...2M: Flat universe Omega_m=0.3, Omega_L=0.7; H0 = 67.4 or 73.3; second absorber at z=0.19 neglected
- 2019ApJ...873...50D: Flat Planck LCDM: h=0.677, Om=0.308, OL=0.691
- 2015PASJ...67...72T: Flat universe Ωm=0.26, ΩΛ=0.74, H0=72
- 2015PASJ...67...72T: M/L = 2 Msun/Lsun at ~1 µm
- 2025NatAs...9.1553F: circular rotation
- 2020A&A...633A.160C: BC03 SEDs, Chabrier IMF, tau=1e11 yr, 0.2 Zsun, Calzetti law with 0<=A_V<=1
- 2016MNRAS.457.2936I: SIE plus external shear
- 2015MNRAS.451L..40R: Only far-infrared part of the SED considered, where magnification is valid
- 2024A&A...685A..80Z: Clumps unresolved
- 2023Natur.621..483G: Constant polarization fraction of unity/1% and constant B orientation in source plane; continuum matches CO morphology
- 2019ApJ...870...80L: Lens at z=0.9
- 2015ApJ...812...88M: Flat LCDM H0=70, OmegaM=0.3; ALMA magnification applied to stellar emission
- 2025ApJS..278...45F: AID20 assumed z=2.0; AID60 assumed z=9.0
- 2020ApJ...902...78R: kappa = 0.015 (nu/250 GHz)^beta m^2/kg, beta=2; gas-to-dust ratio 100; Kroupa IMF; flat LCDM H0=68.1
- 2018A&A...613A..34P: Gaussian uncorrelated noise
- 2018A&A...613A..34P: dust traced by molecular gas, same magnification mu_CO = 7.3
- 2015ApJ...811..115W: SMBH at mass centroid; uniform prior on log M_BH [6.5, 9.5]
- 2020A&A...634L...3Y: Similar H2O(4_23-3_30)/H2O(2_11-2_02) flux ratio in R and B
- 2018ApJ...866L..12G: Both lenses at same redshift for M/L ratio
- 2018ApJ...866L..12G: alpha=0, Gaussian vertical profile
- 2015ApJ...811..124S: Lens parameters fixed to ALMA best fit
- 2018Natur.553...51M: Lens is a singular isothermal ellipsoid
- 2015A&A...576L...2S: Missing short-spacing flux negligible
- 2018MNRAS.475.4939A: Spherically symmetric lenses; flat LCDM with Omega_m=0.307, h=0.693
- 2013ApJ...767...88W: Average magnification 15
- 2017ApJ...843L..35W: Results same if source twice as large
- 2018Sci...361.1016S: Singular isothermal ellipsoid lens
- 2018ApJ...867..140L: Lens within 0.2 arcsec of HST optical centroid; no external shear
- 2018A&A...610A..53M: Singular Isothermal Ellipsoid lens
- 2016ApJ...826..112S: Flat WMAP9 cosmology, h=0.693, Om=0.286
- 2018A&A...620A.115B: Local 5-4/4-3 ratio applies; differential lensing negligible; Planck2015 cosmology, Chabrier IMF
- 2019A&A...632L...7J: mu = 5.6±0.1; SFR = 3.6e3 Msun/yr
- 2016A&A...586L...7B: Chabrier IMF; magnification 5.7
- 2017MNRAS.466.2825B: Lens models from dust emission apply to [CI] gas
- 2018ApJ...860...87F: alpha_CO 0.8 for B, 4.3 for A; magnification 2.38; W1 gas bound with isotropic turbulence
- 2017MNRAS.466..138K: z = 7.5, CMB temperature ~23.4 K, magnification 9.3
- 2016A&A...593L...2N: all four are multiple images of the same region


### Limitations the authors admit
- 2019A&A...624A.138Y: Source-plane uncertainties may be underestimated; mass-sheet degeneracy not explored
- 2013ApJ...767..132H: Only compact-configuration data used; SPT0529-54 posterior bimodal
- 2026A&A...705A..81K: Low per-channel S/N prevents full delensed cubes; source plane resolution insufficient to resolve clumps; results preliminary.
- 2020ApJ...905...85S: Limited ALMA bandwidth prevents detection of redshifted P Cygni emission and caps vmax
- 2020ApJ...905...85S: Conservative classification is S/N dependent and may exclude weak outflows
- 2020ApJ...891...64F: Lens model poorly constrained; magnification uncertain by a factor of a few
- 2024A&A...684A..56K: Data not standardized, resolution limited, CO SLED turnover unconstrained
- 2018ApJ...862...64S: Small field and low-number statistics; field comparison selection not equivalent
- 2016MNRAS.461..164I: Primary lenses assumed SIE; multipoles and non-isothermal profiles not included
- 2017A&A...597A..41G: Possible unaccounted systematics at 5-10% level; non-uniform sensitivity in two mosaics
- 2014A&A...568A..92M: Knot C in rest-frame optical poorly fitted by the lens model
- 2025ApJ...991...53C: Halo internal structure and magnification are poorly constrained; lens redshifts uncertain
- 2020ApJ...905..152D: Errors exclude lens-model systematics
- 2020ApJ...905..152D: Lines incomplete in the band coverage; roughly 10% flux missing
- 2020A&A...641L...2M: Goal was a plausible model, not ultimate modeling; no H0 constraint because time delay is uncertain.
- 2026ApJ..1002L..28Y: T_dust and beta assumed; multi-band FIR needed
- 2026ApJ..1002L..28Y: Pair fraction is a lower limit because the survey is incomplete
- 2019ApJ...873...50D: Parameterized Sérsic modeling cannot independently constrain faint emission at large radii
- 2019ApJ...873...50D: Simple Sérsic profiles unlikely to fully characterize source structure
- 2015PASJ...67...72T: Core radius and velocity dispersion highly degenerate; BH mass and core radius degenerate
- 2025NatAs...9.1553F: Magnification systematic uncertainty up to ~25%
- 2025NatAs...9.1553F: Clump number may increase with better data; ALMA beam larger than clumps so gas mass only for 7 clumps
- 2020A&A...633A.160C: Stellar masses below ~10^8.5 Msun likely incomplete; selection biases at low mass
- 2020A&A...633A.160C: Stacked values biased toward high-weight sources
- 2020ApJ...892L..18I: Core component interpretation not conclusive.
- 2016MNRAS.457.2936I: Canonical lens model may be too simple; core, power-law deviation, multipoles could explain anomalies
- 2015MNRAS.451L..40R: Results may not extrapolate to general SMG population due to size-bias
- 2024A&A...685A..80Z: Clump C is tentative and needs confirmation; dynamical modelling is beyond scope
- 2023Natur.621..483G: Lack sensitivity and resolution to map B-field at ~100 pc scales; field strength cannot be reliably estimated from dust polarization
- 2019ApJ...870...80L: Constant dust temperature assumed, uncertainty within factor ~2
- 2015ApJ...812...88M: Stellar mass depends strongly on inputs; uncertainties dominated by few optical/NIR points; differential lensing not measured
- 2025ApJS..278...45F: 1-2 sources may be spurious; no completeness correction for IRLF; z>9 detections marginal
- 2020ApJ...902...78R: Lens models exist for only 39 sources; median magnification adopted for rest, so intrinsic properties are estimates
- 2018A&A...613A..34P: SED fit limited by differential magnification precision and lack of short-wavelength data
- 2015ApJ...811..115W: Fluxes of A, B, C not used owing to differential magnification (~30-50%)
- 2025ApJ...995..219F: Lens model systematics not included; mass-sheet degeneracy possibly unbroken
- 2025ApJ...995..219F: Gas mass is a lower limit given alpha_CO
- 2020A&A...634L...3Y: Models neglect spatially varying Tdust, which could lower inferred N_H2O; AGN contribution cannot be ruled out
- 2018ApJ...866L..12G: Deblending of HNC/CN depends strongly on redshift; outflow rate cannot be estimated; limited tracers
- 2015ApJ...811..124S: Systematic uncertainties in alpha_CO ~100% per method
- 2024ApJ...967...11C: Lens light subtraction was done separately from lens modeling, which hindered modeling with background noise
- 2024ApJ...967...11C: Constraints on SPT0418B are less robust owing to limited photometric detections
- 2021A&A...645A..45C: Strong parameter degeneracies in LVG models
- 2018Natur.553...51M: IRAC fluxes for W unreliable due to blending with lens; stellar mass of W unconstrained
- 2015A&A...576L...2S: Delivered data did not meet requested sensitivity; ~25% flux calibration uncertainty
- 2024A&A...692A.215C: Scatter in r31 and r41 relations adds systematic errors
- 2018MNRAS.475.4939A: Sample too small to distinguish density profiles; magnification bias not corrected
- 2013ApJ...767...88W: Eight ambiguous redshifts hamper determination of the distribution shape; small sample
- 2013ApJ...767...88W: Dust temperatures not physical; lensing size-evolution bias cannot be excluded
- 2025ApJ...990...29H: Only three free parameters due to few observables; single-phase ionized gas cannot reproduce [O II]
- 2017ApJ...843L..35W: ~50% of data flagged due to antenna problems
- 2017ApJ...843L..35W: Conjugate points cause degeneracies; position uncertainties overestimated
- 2015ApJ...806L..17S: The pressure estimate has considerable uncertainty
- 2018Sci...361.1016S: Mass outflow rates highly uncertain (optical depth, geometry, OH abundance)
- 2018Sci...361.1016S: Bimodal lens solution
- 2018ApJ...867..140L: Lens model lacks external shear and mass-profile variation; ALMA may resolve out flux
- 2018A&A...610A..53M: Low X-ray photon counts limit spectral constraints; only two objects, cannot constrain evolutionary models
- 2019A&A...628A..23A: LVG model not fully constrained because the CO SLED peak is not traced
- 2017A&A...600L...3C: Image family association is difficult as velocities overlap
- 2016ApJ...826..112S: Lens model uncertainties on source properties are dominated by systematics from source parameterization
- 2018A&A...620A.115B: Low S/N; conversion 5-4 to 4-3 uncertain; differential lensing neglected
- 2016ApJ...822...80S: Single magnification used for lensing correction is a simplification
- 2016ApJ...822...80S: Not enough high-z size measurements to exclude size evolution
- 2019A&A...632L...7J: Outflow loading factor poorly constrained; shell thickness unconstrained
- 2016A&A...586L...7B: Depletion time may be underestimated if source is at end of starburst; differential magnification may affect line ratios
- 2017MNRAS.466.2825B: Cannot rule out AGN; Tex assumed; X_CI assumed; differential lensing possible
- 2016A&A...596A..75S: Herschel fluxes of the SMG derived through indirect procedure with unverified assumptions; Y-band scatters ~2 sigma from best fit
- 2019A&A...631A..91G: A521 lacks resolution along the major axis, so differences may be hidden
- 2018ApJ...860...87F: GBT cannot spatially disentangle excitation; alpha_CO for component A is highly uncertain.
- 2017MNRAS.466..138K: [CII] feature only tentative (3 sigma); systemic redshift may not be covered
- 2017MNRAS.466..138K: ALMA data quality insufficient to confirm elongated clumps
- 2016A&A...593L...2N: Lens model preliminary, awaiting HST imaging
- 2019MNRAS.486.2366M: Temperature, velocity gradient and density poorly constrained and correlated
- 2018ApJ...864...60M: Blue end of the sed3fit SED is dominated by a spurious AGN component because of upper limits, so SED alone cannot indicate AGN

### Settings cards flag as needed but not stated
- casa version: 6
- flux calibrator and flux scale uncertainty: 3
- flux calibrators and flux scale uncertainty: 3
- cell size and image size: 2
- line-free channels used for continuum: 2
- line-free channels and continuum subtraction details: 2
- line-free channels and continuum subtraction method: 2
- image size and cell size: 2
- clean threshold, mask, cell and image size: 2
- number of tclean iterations, thresholds, masks and cell/image sizes: 1
- self-calibration solution intervals and number of rounds: 1
- line-free channel selection: 1
- uv-range or taper settings: 1
- source-plane flux-binning details and mcmc chain length/convergence: 1
- details of the modified blackbody sed fit (fitted data points, priors, two-temperature split): 1
- deflector optical positions used for priors: 1
- exact pyautolens and 3dbarolo settings: 1
- casa version and calibration scripts: 1
- imaging parameters (weighting, cleaning, cell size): 1
- mcmc chain length, priors, tempering schedule t: 1
- greybody fit parameters (t_dust, beta) and fir luminosity integration range: 1
- lens priors and source-model starting values: 1
- phase calibrator names: 1
- code for lens modeling not released: 1
- line-free channels used for uvcontsub: 1
- annular aperture radii for spectrum/continuum extraction: 1
- cell size, image size and clean thresholds/masks: 1
- regularization coefficient values (file names hint at coefficients, not explained), mesh resolution…: 1
- channel ranges of red and blue bins and channels used in lens modeling: 1
- gaussian fitting details: 1
- private tclean scripts: 1
- gas-to-co conversion/sfr values from aravena16 for depletion times: 1
- casa version and pipeline versions per cycle: 1
- line-free channel ranges and continuum-subtraction method for each source: 1
- cell size, image size, clean masks and exact tclean parameters: 1
- self-calibration solution intervals per source and exact flux/bandpass/phase calibrators: 1
- mcmc settings (sampler, priors, chain lengths) for lens models; visilens/ripples configuration: 1
- pixel grid sizes in source and image planes: 1
- exact aperture definition for integrated spectra: 1
- systemic redshift velocity zero points used for each source: 1

## Paper excerpts (40 of 61, chosen for detail and spread over fields/years)

### 2019A&A...624A.138Y: CO, H<SUB>2</SUB>O, H<SUB>2</SUB>O<SUP>+</SUP> line and dust emission in a z = 3.63 strongly lensed starburst merger at sub-kiloparsec scales (2019; high_z_galaxies; observational_alma_primary)
- question: What are the spatial and kinematic structure, dust and gas content (CO, H2O, H2O+) of the lensed SMG G09v1.97 at sub-kpc scales in the source plane, and is it a merger?
- step 3: Lens model from dust continuum
  - method: Joint fit of 1.94 and 0.87 mm images with two SIE deflectors and two exponential-profile source components; image-plane fit [4.1 Fitting the dust continuum emission: "we used the 1.94 and 0.87 mm dust continuum images (Fig. [1](#fig:g09-image)) to constrain simultaneously the mass distribution (SIE model) of G1 and G2 and the dust emission"]
  - software: sl_fit
  - parameter: Priors: Einstein radii uniform [0.1,1.1'']; axis ratios Normal(0.5,0.2); source positions uniform ±0.2''; source axis ratio uniform [0.1,0.9]; Reff Normal(0.1'',0.03'') in [0,0.2''] [4.1 Fitting the dust continuum emission: "The prior on both Einstein radii is uniform in the range $[0.1\ensuremath{''},1.1\ensuremath{''}]$."]
  - assumption: Both source components have constant magnification across SED; deflectors at z=0.626 and 1.002 [4.1 Fitting the dust continuum emission: "each of the two background components has a constant magnification across its entire far-IR spectral energy distribution (SED)"]
  - fitting: MCMC Metropolis-Hastings; median and 68% intervals [4 Lens Modeling: "implementing the standard Metropolis-Hastings algorithm"]
  - validation: Residuals <2.5 sigma; PyAutoLens pixelized reconstruction converged to same model [4.1 Fitting the dust continuum emission: "The analysis converges to the same lens model and reconstructs a source galaxy with the same global structure as the double-disk model"]
- step 4: Source-plane line cube reconstruction
  - method: Cube binned into 10 velocity bins of 105 km/s (−478 to 467); fixed mass model; one elliptical exponential per bin; H2O+ in 2 bins [4.2 Fitting the CO and H2O Line Emission: "the data cube was binned into 10 velocity channel bins of 105 km s$^{-1}$ from $-$478 to 467 km s$^{-1}$"]
  - software: sl_fit
  - assumption: CO and H2O emission identical up to flux normalization [4.2 Fitting the CO and H2O Line Emission: "we assume that, up to a normalizing flux constant, the emission is identical between the ${\mathrm{CO}}(6\text{--}5)$ and H~2~O($2_{11}\text{--}2_{02}$) lines"]
  - fitting: Same priors as continuum model; 10x7 parameters [4.2 Fitting the CO and H2O Line Emission: "We thus fit for the 10$\times$7 parameters defining the source emission"]
  - validation: Image-plane moment maps and per-channel residuals; image vs source-plane moment maps match [5.2 Kinematic structure: "The moment maps from the image and source plane match very well, suggesting that our lens model is robust."]
- step 5: Morphology and kinematics in source plane
  - method: Three-disk IMFIT of CO moment-0 map; inclination from axis ratio with q0=0.2; 3DBarolo tilted-ring test; PV diagrams [5.1 Morphology: "we performed a fit to the 0$^{\rm th}$ moment map of ${\mathrm{CO}}(6\text{--}5)$ in the source plane with a disk model using `IMFIT`"]
  - software: IMFIT, 3DBarolo
  - parameter: q0 = 0.2 [5.1 Morphology: "Choosing a typical value of $q_0=0.2$ for disk galaxies"]
  - assumption: R and B are thin disks [5.1 Morphology: "Assuming that both R and B are thin disks, the inclination angle can be derived"]
  - fitting: chi2 minimization; bootstrap uncertainties of 10% [5.1 Morphology: "Using bootstrap resampling, the uncertainties from the fit are determined with uncertainties of 10%."]
  - validation: Residuals <1% of emission [5.1 Morphology: "maximum differences are less than 1% of the emission"]
- result: Total magnification (dust) = 10.3 ± 0.5 dimensionless [4.1: "$\mu_{\rm tot}$ = $10.3\pm 0.5$"]
- result: Compact dust Reff = 0.63 ± 0.15 kpc [4.1: "$R_{\rm eff,\,1}$ = $0.63 \pm 0.15\, {\rm kpc}$"]
- result: Extended dust Reff = 1.37 ± 0.05 kpc [4.1: "$R_{\rm eff,\,2}$ = $1.37 \pm 0.05\, {\rm kpc}$"]
- result: Einstein radius G1 = 0.39 ± ±0.01 arcsec [4.1: "Einstein radius of $0.39\ensuremath{''} ^{+0.01}_{-0.01}$ for G1"]
- result: Einstein radius G2 = 0.63 ± ±0.01 arcsec [4.1: "$0.63\ensuremath{''}^{+0.01}_{-0.01}$ for the more distant G2"]
- result: Semi-major half-light radius R and B = 1.2 and 0.4 ± 10% kpc [5.1: "of 1.2 kpc and 0.4 kpc, are separated by a projected distance of 0.18$''$ (1.3 kpc)"]
- result: Inclinations R, B = 82, 66 ± not stated deg [5.1: "we infer inclinations for R and B of 82$^\circ$ and 66$^\circ$, respectively"]
- limitation (authors): Source-plane uncertainties may be underestimated; mass-sheet degeneracy not explored [Appendix: "the uncertainties of $\mu$ (and on the intrinsic source flux and size) do not account for the effect of mass-sheet degeneracy"]
- not stated (card): Number of tclean iterations, thresholds, masks and cell/image sizes; Self-calibration solution intervals and number of rounds; Line-free channel selection; Uv-range or taper settings; Source-plane flux-binning details and MCMC chain length/convergence; Details of the modified blackbody SED fit (fitted data points, priors, two-temperature split); Deflector optical positions used for priors; Exact …

### 2013ApJ...767..132H: ALMA Observations of SPT-discovered, Strongly Lensed, Dusty, Star-forming Galaxies (2013; high_z_galaxies; observational_alma_primary)
- question: Are four SPT-discovered dusty sources gravitationally lensed, and what are their magnifications and intrinsic properties from visibility-plane lens modeling?
- step 2: Visibility-plane lens modeling with integrated phase self-calibration
  - method: Gaussian source lensed by SIE, Fourier transformed and sampled at ALMA uv; chi^2 vs visibilities with antenna phases solved at each chain step [3.1 Lens Modeling: "We model the lenses by generating model lensed images that are subjected to simulated observations and compared to the data."]
  - software: custom MCMC code
  - parameter: Source: 4 params; SIE lens: 5 params [3.1 Lens Modeling: "The lens is modelled as a Singular Isothermal Ellipsoid (SIE) with five free parameters"]
  - assumption: WMAP7 cosmology h=0.71, Om=0.27, OL=0.73 [1 Introduction: "with WMAP7 parameters, with $h=0.71$, $\Omega_M=0.27$, and $\Omega_\Lambda=0.73$"]
  - fitting: MCMC with Metropolis-Hastings sampling, tempering (posterior^1/T); noise from differencing adjacent visibilities [3.1 Lens Modeling: "We explore the model parameter space using a Markov Chain Monte Carlo (MCMC) method with Metropolis-Hastings sampling."]
  - validation: Simulated observations recover input antenna phases; extended-array data compared with predictions [Lens Model Self-Calibration: "The excellent agreement between input and recovered phase demonstrates that the simultaneous fitting of the lens model and antenna phases does not bias the antenna phase measurement"]
- step 3: Derive intrinsic properties
  - method: Divide observed fluxes by magnification; greybody SED for L_FIR; SFR from Kennicutt conversion [4 Discussion: "The lens models permit the calculation of some intrinsic properties of the lensed galaxies by simply dividing observed properties by the magnification."]
  - assumption: Standard starburst SFR conversion (Kennicutt 1998) [4 Discussion: "assuming a standard conversion for starbursting galaxies (cite: kennicutt98)"]
  - validation: LABOCA 870 um flux agrees with modeled ALMA flux within ~10% [2.3 Other Supporting Data: "agree with the total flux density in the modeled ALMA data (described below) to within calibration uncertainties, typically 10%"]
- result: SPT0346-52 magnification = 5.4 ± 0.2 dimensionless [Table 1: "5.4$\pm$0.2"]
- result: SPT0418-47 magnification = 21.0 ± 3.5 dimensionless [Table 1: "21.0$\pm$3.5"]
- result: SPT0529-54 magnification = 9.4 ± 1.0 dimensionless [Table 1: "9.4$\pm$1.0"]
- result: SPT0346-52 Einstein radius = 1.124 ± 0.004 arcsec [Table 1: "1.124$\pm$0.004"]
- result: SPT0346-52 intrinsic L_FIR = 37.3 ± 2.8 1e12 Lsun [Table 1: "37.3$\pm$2.8"]
- result: SPT0346-52 SFR surface density = 4200 ± not stated Msun/yr/kpc^2 [4 Discussion: "implying a star-formation rate of 4200 M$_{\odot}$ yr$^{-1}$ kpc$^{-2}$"]
- result: SPT0346-52 magnification from extended data = 5.26 ± 0.12 dimensionless [High Resolution Observations of SPT0346…: "$5.26 \pm 0.12$"]
- limitation (authors): Only compact-configuration data used; SPT0529-54 posterior bimodal [4 Discussion: "The extended array data on this source can possibly break this degeneracy."]
- not stated (card): CASA version and calibration scripts; Imaging parameters (weighting, cleaning, cell size); MCMC chain length, priors, tempering schedule T; Greybody fit parameters (T_dust, beta) and FIR luminosity integration range; Lens priors and source-model starting values; Phase calibrator names; Code for lens modeling not released

### 2026A&A...705A..81K: Resolving the molecular gas emission of the z ∼ 2.5─2.8 starburst galaxies SPT 0125-47 and SPT 2134-50 (2026; high_z_galaxies; archival_reuse)
- question: What are the source-plane morphology and kinematics of the lensed DSFGs SPT 0125-47 and SPT 2134-50 from CO(3–2), and do they show clumps, companions or mergers?
- step 3: Parametric uv-plane lens modeling
  - method: PyAutoLens on uvcontsub visibilities, SIE lens, Sérsic source with linear light profiles, line channels only [Parametric source modeling: "we model the lens as a single isothermal ellipsoid (SIE) mass distribution assumed to not have light distributions"]
  - software: PyAutoLens, CASA
  - parameter: lens centers fixed at Einstein ring centers with uniform priors; Einstein radius upper limit slightly above Spilker16 [Parametric source modeling: "We fixed the centers of the mass distributions to be in the center of the observed Einstein rings using uniform priors."]
  - fitting: Formal errors from sampling algorithms; sampler not named [Nonparametric source modeling: "are formal statistical errors from the sampling algorithms in the lens model fitting"]
  - validation: Residuals checked at >3σ; compared with literature magnifications [SPT 0125-47: "We found a good parametric lens mass model for the CO(3–2) emission with no residuals at $>3\sigma$ levels."]
- step 4: Nonparametric source reconstruction and error maps
  - method: Adaptive Voronoi mesh with constant regularization using the optimized parametric lens model; error maps from visibility errors via statwt [Nonparametric source modeling: "This methodology employs an adaptive Voronoi mesh, maintaining regions of higher magnification and, thus, higher angular resolution, around the caustic lines in the source plane."]
  - software: PyAutoLens, CASA statwt
  - parameter: constant regularization scheme with one coefficient [Nonparametric source modeling: "Here, we used a constant regularization scheme, which was parameterized by a regularization coefficient that regulated the smoothness of the emission."]
  - validation: Source-plane S/N maps [Nonparametric source modeling: "making it straightforward to produce a S/N map in the source plane"]
- step 5: Differential lensing and red/blue bin reconstructions
  - method: Split line into red and blue bins, parametric lens modeling of each, then nonparametric source models [Differential lensing: "We investigated whether this is caused by differential lensing across the line profile by dividing each emission line into red and blue spectral bins."]
  - software: PyAutoLens
- result: Magnification SPT 0125-47 (CO(3-2)) = 10.7 ± 0.002 dimensionless [SPT 0125-47: "we found a magnification factor of $\mu_{\rm CO(3-2)} = 10.7 \pm 0.002$"]
- result: Magnification SPT 2134-50 (CO(3-2)) = 7.6 ± 0.002 dimensionless [SPT 2134-50: "we find a magnification factor of $\mu_{\rm CO(3-2)} = 7.6 \pm 0.002$"]
- result: Differential magnification SPT 0125-47 = mu_blue ~14, mu_red ~9 ± not stated dimensionless [Differential lensing: "For SPT 0125-47, we found $\mu_{\rm blue} \sim 14$ and $\mu_{\rm red} \sim 9$."]
- result: Differential magnification SPT 2134-50 = mu_blue ~14, mu_red ~4.4 ± not stated dimensionless [Differential lensing: "For SPT 2134-50, we found $\mu_{\rm blue} \sim 14$ and $\mu_{\rm red} \sim 4.4$."]
- limitation (authors): Low per-channel S/N prevents full delensed cubes; source plane resolution insufficient to resolve clumps; results preliminary. [Implications: "these results should be considered as preliminary and require confirmation through deeper observations or observations of brighter emission lines"]
- not stated (card): Line-free channels used for uvcontsub; Annular aperture radii for spectrum/continuum extraction; Cell size, image size and clean thresholds/masks; Regularization coefficient values (file names hint at coefficients, not explained), mesh resolution, sampler and priors for PyAutoLens; Channel ranges of red and blue bins and channels used in lens modeling; Gaussian fitting details; Private tclean scr…

### 2020ApJ...905...85S: Ubiquitous Molecular Outflows in z &gt; 4 Massive, Dusty Galaxies. I. Sample Overview and Clumpy Structure in Molecular Outflows on 500 pc Scales (2020; high_z_galaxies; observational_alma_primary)
- question: How common are molecular outflows (traced by OH 119 um absorption) in z>4 lensed dusty star-forming galaxies, and what is their spatial structure on ~500 pc scales?
- step 4: Lens model continuum and reconstruct OH absorption components
  - method: Pixellated visibility-space lens modeling with SIE (+shear, multipoles) and gradient regularization; lens parameters from continuum then applied to OH velocity ranges [3.3 Lens Modeling Methods and Tests: "We fit for the lensing potential using a Markov Chain Monte Carlo (MCMC) sampling algorithm."]
  - software: ripples, visilens
  - parameter: visibilities averaged temporally unless binned visibility spans >10 m in uv [3.3 Lens Modeling Methods and Tests: "which we average temporally unless doing so would cause a binned visibility to span more than 10m in the $uv$ plane"]
  - assumption: Regularization strength set by maximizing Bayesian evidence for fixed lens parameters, iterated [3.3 Lens Modeling Methods and Tests: "The best-fit strength of the regularization is determined by maximizing the Bayesian evidence given a fixed set of parameters for the lensing potential."]
  - fitting: MCMC for lens potential; iterative regularization/MCMC; priors not stated [3.3 Lens Modeling Methods and Tests: "we perform an iterative process of fitting for the regularization strength, MCMC fitting for the lens parameters, and re-fitting for the regularization strength until all parameters have converged."]
  - validation: Deviance information criterion, negative-bowl check (>=10% of peak), mock point-source tests across source plane (recover fluxes to ~25%) [3.3.1 Model Selection and Tests: "This final test shows that even these weak signals are recoverable to $\approx$25% accuracy."]
- limitation (authors): Limited ALMA bandwidth prevents detection of redshifted P Cygni emission and caps vmax [4.1 Molecular Outflow Detection Rate: "our ability to detect redshifted emission as in the classic P Cygni profile is limited due to the small ALMA bandwidth"]
- limitation (authors): Conservative classification is S/N dependent and may exclude weak outflows [3.2 Molecular Outflow Classification: "This definition has the drawback of being signal-to-noise dependent, which may exclude weak outflows"]
- not stated (card): CASA version and pipeline versions per cycle; Line-free channel ranges and continuum-subtraction method for each source; Cell size, image size, clean masks and exact tclean parameters; Self-calibration solution intervals per source and exact flux/bandpass/phase calibrators; MCMC settings (sampler, priors, chain lengths) for lens models; visilens/ripples configuration; Pixel grid sizes in source a…

### 2020ApJ...891...64F: Truth or Delusion? A Possible Gravitational Lensing Interpretation of the Ultraluminous Quasar SDSS J010013.02+280225.8 at z = 6.30 (2020; agn_and_quasars, high_z_galaxies; observational_alma_primary)
- question: Is the resolved quadruple ALMA 1-mm continuum structure of the z=6.30 quasar J0100+2802 due to strong gravitational lensing or to multiple star-forming regions, and how would lensing change its BH mass?
- step 3: Lens mass model fit to four ALMA peaks
  - method: SIE plus external shear fit to peak positions and fluxes; lens at z=2.33 [3.1 ALMA: "The mass model consists of a singular isothermal ellipsoid (SIE) and an external shear."]
  - software: glafic
  - parameter: positional error 0.03''; flux error 10% [3.1 ALMA: "The flux errors are assumed to be 10 %."]
  - assumption: Gaussian prior on shear gamma=0.05±0.05; no prior on SIE centroid [3.1 ALMA: "we add a Gaussian prior on the amplitude of the external shear of $\gamma=0.05 \pm 0.05$"]
  - fitting: best-fit chi2/dof = 6.11/3 [3.1 ALMA: "we obtain the best-fit mass model with the $\chi^2$ over the degree of freedom of 6.11/3"]
  - validation: Model positions and intrinsic fluxes consistent with observations within errors [3.1 ALMA: "We find that all the four positions are consistent within the errors."]
- step 5: Correct M_BH for magnification
  - method: Apply magnification to UV luminosity in Mg II virial estimator [4 Discussion: "If we apply the total magnification correction to the UV luminosity in Equation [\[eq:Mbh\]](#eq:Mbh), the intrinsic $M_{\rm BH}$ estimate is decreased by a factor of $\sim$17.3."]
- result: Einstein radius = 0.14 ± not stated arcsec [3.1 ALMA: "the Einstein radius is 0.14$''$ which corresponds to the line-of-sight velocity dispersion of the lensing galaxy of 121 km s$^{-1}$"]
- result: Total ALMA magnification = ~58 (2sigma range 18-117) ± 2 sigma range dimensionless [3.1 ALMA: "The best-fitting mass model predicts the total magnification of $\sim 58$ for the ALMA source"]
- result: Lens ellipticity = 0.14 ± ±0.09 dimensionless [4 Discussion: "the ellipticity is not very well constrained in our model with $e=0.14\pm0.09$ ($1\sigma$)"]
- result: Total magnification of HST emission = ~450 ± factor of a few dimensionless [3.2 Comparison with HST: "our fiducial mass model predicts the total magnification factor of $\sim450$ for the quadruple images in the HST map"]
- limitation (authors): Lens model poorly constrained; magnification uncertain by a factor of a few [4 Discussion: "our estimate of the total magnification factor should be uncertain by a factor of a few or so"]
- not stated (card): Spectral window line-free channel selection; Cell size and image size; Exact tclean parameters (niter, gain, mask settings); glafic fitting setup details and best-fit SIE parameters (other than Einstein radius and e); How the 0.8'' aperture flux and peak positions were measured; Details of simobserve configuration and noise

### 2024A&A...684A..56K: Probing the interstellar medium of the quasar BRI 0952‒0115. An analysis of [C II], [C II], CO, OH, and H<SUB>2</SUB>O (2024; agn_and_quasars, high_z_galaxies, milky_way_ism; archival_reuse)
- question: What are the ISM properties and heating mechanisms (PDR vs XDR) of the lensed quasar BRI 0952-0115 at z=4.432, and what is its evolutionary stage?
- step 3: per-channel lensing magnification
  - method: Visilens fit of each [CII] channel with Sersic source, magnification extrapolated to other lines by nearest velocity [Spectral Reconstruction: "we used a closest value finding algorithm to search for the velocity bin in the \[C ii\] data which is nearest the velocity bin of the particular line"]
  - software: Visilens
  - assumption: Other lines follow bulk kinematics of [CII] [3.3 Lensing Reconstruction: "as long as the other line species detected follow the bulk motion and systematic kinematics of the entire galaxy, as traced by \[C ii\], this method of extrapolating the magnification factor is valid."]
  - fitting: 4 model variants; Gaussian source rejected [Visilens Modelling: "the fit from VISILENS for this model was sufficiently poor that we disregarded it."]
  - validation: Models compared; magnification consistent across models [Visilens Modelling: "the magnification factor across the velocity range does not change greatly depending on the model used."]
- limitation (authors): Data not standardized, resolution limited, CO SLED turnover unconstrained [5.3: "these observations are not standardized and suffer from angular resolution limitations"]
- not stated (card): Line-free channel ranges per band; Velocity ranges for moment maps and spectral extraction; Extraction ellipse coordinates; Taper size for band 3; Visilens parameter ranges and priors; Gaussian fit procedure details; Band 7 reduction details (in Kade23); Band 3 and 4 CASA versions inconsistent; Starburst99 assumptions; SFR and LIR values used for depletion time

### 2018ApJ...862...64S: Deciphering the Activity and Quiescence of High-redshift Cluster Environments: ALMA Observations of Cl J1449+0856 at z = 2 (2018; galaxy_clusters_and_sz, high_z_galaxies; observational_alma_primary)
- question: How much obscured star formation and how much quiescence is there in the core of the z=2 cluster ClJ1449, and what do ALMA 870um continuum and CO(4-3) say about member galaxies and the forming BCG?
- step 1: Count 870um sources and compute overdensity
  - method: Compare six S/N>4 sources >0.5 mJy with blank-field counts; assess lensing magnification with NFW halo [3 Overdensity of 870$\mu$m sources: "assuming a spherical NFW halo of mass $6\times10^{13}$ M$_{\odot}$ and a concentration in the range $c=1-5$"]
- limitation (authors): Small field and low-number statistics; field comparison selection not equivalent [4.1.1 Color distribution: "the very small number statistics of the *ALMA*-detected sample in the cluster"]
- not stated (card): Reduction/calibration and imaging details (CASA version, weighting, cleaning) are only in C18; Positions and catalogue of known cluster members; Per-source flux values for A1-A6 and members; Flux-boosting correction recipe for CO(4-3); CO(5-4)/CO(4-3) ratio values and CO(5-4)-LIR relation coefficients adopted; Conversion from 870um flux to LIR with Bethermin SEDs (template details)

### 2016MNRAS.461..164I: On the origin of the flux ratio anomaly in quadruple lens systems (2016; cosmology, high_z_galaxies; theory_or_simulation_compared_to_alma)
- question: Whether flux ratio anomalies in 11 quadruple lens systems are caused mainly by subhaloes or by line-of-sight structures
- step 1: Fit smooth lens models
  - method: Fit SIE plus external shear to fluxes, positions and time delays by chi^2 [5 Lens model: "simultaneous $\chi^2$ fitting of the fluxes, positions, and time delay of lensed images"]
  - software: GRAVLENS
- limitation (authors): Primary lenses assumed SIE; multipoles and non-isothermal profiles not included [Conclusion and Discussion: "This assumption may be too simple."]
- not stated (card): Fitted lens model parameters for each system (only referenced); Observational errors on flux ratios and eps_0 per system; Host halo concentration and mass mapping details; Data points for the redshift correlation fits

### 2017A&A...597A..41G: The ALMA Frontier Fields Survey. I. 1.1 mm continuum detections in Abell 2744, MACS J0416.1-2403 and MACS J1149.5+2223 (2017; high_z_galaxies; observational_alma_primary)
- question: Can ALMA 1.1 mm mosaics of three Frontier Fields lensing clusters detect sub-mJy dusty star-forming galaxies, and what are their fluxes, sizes and NIR counterpart offsets?
- step 3: measure flux densities and sizes in uv-plane
  - method: uvmcmcfit elliptical Gaussian in uv-plane after PB-weighting pointings within 19'' [4.2.2 uv-plane fit: "We estimate an initial source position based on the continuum images and select all pointings which lie within 19$''$ (PB$\geq$0.1) of the initial position."]
  - software: uvmcmcfit, emcee
  - parameter: 10,000-240,000 iterations, 5,000 burn-in [4.2.2 uv-plane fit: "Between 10,000–240,000 iterations were required, depending on the speed of convergence."]
  - fitting: emcee sampling of likelihood in visibilities; 1 sigma range of posterior [4.2.2 uv-plane fit: "`uvmcmcfit` uses `EMCEE` (cite: Foreman-mackey2013) to sample the posterior probability density function (PDF) of the model parameters."]
  - validation: compared with fluxes from 1.5'' tapered images; injected fake sources [4.2.2 uv-plane fit: "We see that the two estimates agree within the errors"]
- step 4: demagnify sizes and fluxes
  - method: magnification from 16/50/84th percentiles of FF lens models; r/sqrt(mu), F/mu [4.3 Source sizes: "We correct the effective radius as $r_{s}/\sqrt{\mu}$ and the flux density as $F_{\rm uv-fit}/\mu$."]
  - assumption: z=2 (range 1-3) for sources without spectroscopic redshift [4.3 Source sizes: "we will assume that they lie at $z$$=$2 and use the range $z$$=$1–3 as an estimate of the error"]
  - fitting: linear regression log r_s vs log F with HerMES comparison [4.3 Source sizes: "we fit a linear regression between flux density and effective radius as $\log{r_{\rm s}} = m\times\log{F_{\nu}} + b$"]
- step 5: measure ALMA-HST positional offsets
  - method: 2D Gaussian centroid of F160W counterpart vs ALMA; source plane offsets via Zitrin-NFWv3 and LTMv1 [4.4 Positional Offsets: "we tracked the positions of the centroids in ALMA and *HST* to the source plane using the lensing models of Zitrin-NFWv3 and Zitrin-LTMv1"]
  - validation: phase calibrator positions compared to literature [4.4 Positional Offsets: "By comparing the observed positions of the phase calibrators used in the ALMA observations to those in the literature"]
- result: A2744-ID01 uv-fit flux = 1.570 ± 0.073 mJy [Table 4: "| A2744-ID01 | $1.495 \pm 0.081$ | $1.545 \pm 0.081$ | 1.7 | 1.6 | $1.570\pm0.073$ |"]
- result: A2744-ID02 uv-fit flux = 2.816 ± 0.229 mJy [Table 4: "| A2744-ID02 | $1.656 \pm 0.131$ | $3.262 \pm 0.213$ | 10.3 | 2.2 | $2.816\pm0.229$ |"]
- result: size-flux regression slope m = -0.08 ± 0.10 dimensionless [4.3 Source sizes: "The best-fit regression values are $m=-0.08\pm0.10$ and $b=-0.95\pm0.05$"]
- result: size-flux regression intercept b = -0.95 ± 0.05 dimensionless [4.3 Source sizes: "The best-fit regression values are $m=-0.08\pm0.10$ and $b=-0.95\pm0.05$"]
- result: median offset Delta DEC (NIR-mm) = -0.13 ± 0.02 arcsec [4.4 Positional Offsets: "$\Delta{\rm DEC}$$=$$-$0.13$''$$\pm$0.02$''$"]
- result: A2744-ID02 source-plane offset = 0.48 ± 0.04 arcsec [4.4 Positional Offsets: "is $0.48\ensuremath{''}\pm0.04\ensuremath{''}$ including only the uncertainties"]
- limitation (authors): Possible unaccounted systematics at 5-10% level; non-uniform sensitivity in two mosaics [3.2 High-significance continuum detecti…: "we only caution that there may be unaccounted for systematic errors at the 5–10% level."]
- not stated (card): DBSCAN parameters (eps, min_samples); Priors and initial parameter ranges for uvmcmcfit; Number of walkers; Exact simobserve settings (PWV, integration time); Which lens models and versions exactly were used per cluster; Cosmology parameters; Details of fake point-source injection (flux grid, number)

### 2014A&A...568A..92M: Herschel-ATLAS and ALMA. HATLAS J142935.3-002836, a lensed major merger at redshift 1.027 (2014; high_z_galaxies; observational_alma_primary)
- question: Confirm the lensing hypothesis for H1429-0028, model the background source's morphology and dynamics, and provide a full physical characterisation.
- step 2: Lens model fit
  - method: SLI simultaneous fit of CO(4-3) moment-0 and 7 GHz maps with elliptical power-law mass profile, no external shear [4.1.1 Lens characterisation: "the images given as input are the velocity-integrated CO(4$\to$3) line map and the 7-GHz continuum map."]
  - software: SLI code
  - validation: Fraction of >2 sigma residuals 0.2% (7 GHz) and 0.5% (CO) [4.1.1 Lens characterisation: "we measure a fraction of $>2\sigma$ residuals of 0.2% and 0.5% for the 7 GHz and CO (J:4$\to$3) data respectively."]
- step 3: Source-plane reconstruction and dynamics
  - method: Apply best-fit lens model to CO(4-3) cube; dynamical mass via isotropic virial estimator; r1/2 from moment minimisation and bootstrapping [4.1.3 Source dynamical analysis: "The uncertainties were found via bootstrapping, i.e., the pixel flux values were shifted within $\pm$r.m.s., and $r_{1/2}$, $x_c$, and $y_c$ were recomputed for a total of 10,000 iterations."]
- step 4: SED fitting of foreground and background
  - method: magphys flux PDFs after galfit foreground removal, extinction scenarios and demagnification; emcee modified blackbody fits [4.2 Foreground and background SEDs: "Given the lack of spatially resolved photometry, we avoid working with best-fit solutions and consider instead flux probability distribution functions (PDFs)."]
  - software: magphys, galfit, emcee
  - parameter: limits: beta<3, T<100 K observed-frame, lambda0<2000 um [4.2 Foreground and background SEDs: "it was necessary to limit $\beta$ below 3, the temperature to observed-frame 100 K, and, in the optically-thick case, $\lambda_0$ below observed-frame 2000 $\mu$m."]
  - assumption: Chabrier IMF; H0=70, Om=0.3, OL=0.7 [1 Introduction: "H$_{0} = 70$ km s$^{-1}$ Mpc$^{-1}$, $\Omega_{M} = 0.3$, $\Omega_{\Lambda} = 0.7$, and a Chabrier initial mass function."]
  - fitting: emcee affine invariant MCMC; priors beyond parameter limits not stated [4.2 Foreground and background SEDs: "using an affine invariant Markov chain Monte Carlo method (cite: Foreman12)"]
- result: Lens Einstein radius = 2.18 ± +0.19/-0.27 kpc [4.1.1 Lens characterisation: "$\theta_{\rm E}=2.18_{-0.27}^{+0.19}\,$kpc"]
- result: Magnification mu_TOT CO(4-3) = 9.7 ± 0.7 dimensionless [Table 1: "ALMA CO (J:4$\to$3) | $9.7\pm0.7$"]
- result: Dynamical mass of NS component = 5.8e10 ± 1.7e10 Msun [4.1.3 Source dynamical analysis: "the dynamical mass to be $5.8\pm1.7\times10^{10}\,$M$_\odot$"]
- result: Background SFR = 394 ± +91/-88 Msun/yr [Table magphys: "394$_{-88}^{+91}$"]
- limitation (authors): Knot C in rest-frame optical poorly fitted by the lens model [4.1.2 Source-plane reconstruction: "Still, the fit is poor."]
- not stated (card): tclean/clean parameters (deconvolver, threshold, cell, image size, masks); robust/taper details and line-free channel ranges; Self-calibration solution interval and reference; CASA version; Lens model priors, regularisation and source-plane pixel scale; Moment-map velocity ranges and clipping; MAGPHYS modified code with upper limits not public

### 2025ApJ...991...53C: HerS-3: An Exceptional Einstein Cross Reveals a Massive Dark Matter Halo (2025; high_z_galaxies, cosmology; observational_alma_primary)
- question: What is the lensing configuration of the HerS-3 Einstein cross (with a fifth central image), and does it require a massive dark matter halo in the lensing galaxy group?
- step 4: Lens modeling: point images then pixel-based source reconstruction
  - method: Two-stage: point-source modeling with four SIE galaxies plus shear (with and without a fifth cored-isothermal or NFW halo), then pixsrc reconstruction on ALMA 292 GHz data [4: "we conducted the lens modeling in a two-stage approach."]
  - software: lensmodel, pixsrc
  - parameter: position uncertainty 0.03''; Einstein radius lognormal priors 0.1 dex; shape priors 0.20 (mild) or 0.05 (strong); shear 0.00±0.05 [Appendix 8.1: "We assumed position uncertainties of $0.03\ensuremath{''}$."]
  - parameter: pixsrc noise increased to 80 uJy/beam [Appendix 8.2: "increasing the noise level in *pixsrc* to $\rm 80 \, \mu Jy/beam$ provides the best balance between goodness of fit and regularization"]
  - assumption: All galaxies and halo at the same redshift z~1 [4: "The additional mass component is assumed to lie at the same redshift as the four visible galaxies."]
  - fitting: MCMC posteriors; chi^2 minimization with priors [Table 3: "| G1 | $11.85$ | $11.99_{-0.15}^{+0.08}$ |"]
  - validation: Compared model image peaks, shapes and orientations to observed ALMA images; rms offset <0.02'' [4: "with a rms offset between the observed and model brightness peaks of better than $0.02\ensuremath{''}$"]
- result: Total magnification (cored halo) = 19 ± +14/-5 dimensionless [5.1.2: "$\rm \mu = 19^{+14}_{-5}$ for the cored halo model"]
- result: Total magnification (NFW halo) = 17 ± +5/-4 dimensionless [5.1.2: "$\rm \mu = 17^{+5}_{-4}$ for the NFW halo model"]
- result: Enclosed dark matter mass range = log M_DM = 12.2 to 13.0 ± not stated Msun [4: "the enclosed dark matter mass ranges from $\log M_{\rm DM}/{\rm M_{\odot}} = 12.2$ up to $13.0$"]
- result: Halo velocity dispersion (cored) = 633 ± +185/-129 km/s [4: "$\sigma = 633_{-129}^{+185}$ km/s"]
- result: Source-plane inclination = ~66 ± not stated deg [5.1: "yielding $i \sim 66^\circ$ for both the cored halo and NFW profile models"]
- result: Predicted C-image delay relative to NE (cored) = 273.6 ± +53.3/-71.2 days [Table 4: "| C | $273.6_{-71.2}^{+53.3}$ |"]
- limitation (authors): Halo internal structure and magnification are poorly constrained; lens redshifts uncertain [6: "the internal structure of the dark matter halo cannot be constrained with the current data"]
- not stated (card): ALMA calibrator flux values, flux calibrator name and self-calibration use; CLEAN threshold, cell size, image size and deconvolver for ALMA continuum; Priors and MCMC sampler settings for lens model; Regularization strength in pixsrc; SED fit priors and sampler for MBB; LVG priors on component sizes and temperatures; Magnification adopted for the intrinsic properties beyond mu~18

### 2020ApJ...905..152D: [N II] Fine-structure Emission at 122 and 205 μm in a Galaxy at z = 2.6: A Globally Dense Star-forming Interstellar Medium (2020; high_z_galaxies; observational_alma_primary)
- question: What is the average electron density of the ionised ISM in the lensed SMG 9io9 at z=2.6, from the [N II] 122/205 micron line ratio, and how does it relate to the dense molecular gas?
- step 2: Reconstruct source-plane cubes
  - method: Semi-linear inversion with the Geach et al. 2018 lens model; each slice reconstructed with 50 randomised Voronoi grids, averaged weighted by log-likelihood [Lens model: "Each slice was reconstructed with 50 realisations of a randomised Voronoi source plane grid (cite: dye_modelling_2018) and the mean taken, weighted by the log of the likelihood of each realisation."]
  - parameter: 50 Voronoi realisations per slice [Lens model: "Each slice was reconstructed with 50 realisations of a randomised Voronoi source plane grid"]
  - assumption: Errors exclude systematic uncertainty of the parametric lens model [Lens model: "The errors quoted for the intrinsic source properties do not include any systematic uncertainty introduced by the prescribed parametric lens model"]
- step 3: Measure L_IR from continuum SED
  - method: Single-temperature modified blackbody fit with free beta, Td, normalisation; luminosity summed within the 3 sigma Band 8 contour in the source plane [Line and continuum measurements: "We fit the observed emission with a single-temperature modified blackbody spectrum, allowing the dust emissivity ($\beta$), dust temperature ($T_{\rm d}$) and normalisation to be free parameters."]
  - parameter: L_IR defined at rest-frame 8-1000 um [Line and continuum measurements: "we can estimate $L_{\rm IR}$ (rest-frame 8–1000 $\mu$m)"]
- result: L_IR (8-1000 um) = 1.1e13 ± 0.2e13 Lsun [Line and continuum measurements: "we measure a total $L_{\rm IR}=(1.1\pm 0.2)\times 10^{13}\,\mathrm{L}_\odot$"]
- result: Source-plane continuum flux density at 400 and 680 GHz = 12 mJy and 43 mJy ± not stated mJy [Line and continuum measurements: "the total Band 8 and Band 9 source plane continuum flux densities are 12 mJy and 43 mJy at observed frequencies of 400 and 680 GHz"]
- limitation (authors): Errors exclude lens-model systematics [Lens model: "The errors quoted for the intrinsic source properties do not include any systematic uncertainty introduced by the prescribed parametric lens model"]
- limitation (authors): Lines incomplete in the band coverage; roughly 10% flux missing [Line and continuum measurements: "we estimate we are missing $\approx 10\%$ of the total line flux for both lines"]
- not stated (card): Lens model parameters and the source-plane reconstruction code/setup (in Geach et al. 2018); Cell size, image size, channel width and velocity resolution of the cubes; Line-free channel ranges used for continuum fitting; Modified blackbody details: beta/Td fit results, fit method, rest-frame wavelengths and flux errors; Flux calibrator and flux scale uncertainty; Band 9 manual calibration details…

### 2020A&A...641L...2M: All good things come in threes: the third image of the lensed quasar PKS 1830-211 (2020; agn_and_quasars, cosmology; observational_alma_primary)
- question: Can ALMA high-resolution, high-dynamic-range continuum imaging unambiguously identify the faint third (central) lensed image of PKS 1830-211 and thereby refine the lens model?
- step 4: Fit point-source lens model
  - method: Softened isothermal ellipsoid fit to three image positions and flux ratios; image C position as initial lens center [4 Revising the lens model: "We took the position of the third image as an initial guess for the center of the lens, because both are expected to be very close."]
  - software: GravLens
  - parameter: Eight free parameters: source position, lens position, mass scale, softening length, ellipticity, position angle [4 Revising the lens model: "the lens model has therefore eight free parameters"]
  - assumption: Flat universe Omega_m=0.3, Omega_L=0.7; H0 = 67.4 or 73.3; second absorber at z=0.19 neglected [Appendix A.1: "with a flat Universe defined by $\Omega_m=0.3$ and $\Omega_{\Lambda}=0.7$"]
  - fitting: Chi-square minimization in source and image plane; Monte Carlo degeneracy corner plots [4 Revising the lens model: "The outcome of the fit is shown in the form of Monte-Carlo degeneracy parameter plots ("corner plots")"]
- result: Lens ellipticity e = 0.19 ± 0.02 dimensionless [Table 3: "| | Ellipticity $e$ | $0.19 \pm 0.02$ | \[0.0; 0.3\] | |"]
- result: Time delay t_AB = 28.6 (H0=67.4); 26.3 (H0=73.3) ± not stated days [Table 3: "| Time delay | $t_{\rm AB}$ (d) | 28.6; 26.3 | | \(11\) |"]
- result: Time delay t_AC = 33.7; 31.0 ± not stated days [Table 3: "| | $t_{\rm AC}$ (d) | 33.7; 31.0 | | \(11\) |"]
- result: Magnifications A, B, C = 3.1, -2.9, 0.022 ± not stated dimensionless [Table 3: "| | $\mu_{\rm C}$ | $0.022$ | | |"]
- result: Enclosed mass within 1 arcsec diameter = ~4e11 ± not stated Msun [Appendix A.1: "which we find to be $\sim 4 \times 10^{11}$ M$_\odot$ within a region of $1\ensuremath{''}$ in diameter"]
- limitation (authors): Goal was a plausible model, not ultimate modeling; no H0 constraint because time delay is uncertain. [4 Revising the lens model: "Our goal was not to achieve the ultimate modeling of the system, but to build one plausible model"]
- not stated (card): Robust/weighting and clean threshold/masks for each band; CASA version; Self-calibration reference model and image used; Method and software for measuring image positions/fluxes (point-source fits in uv or image plane); Details of global spectral-index fit; MCMC settings (sampler, priors, chains) for the corner plots; Flagging details and which channels were flagged

### 2026ApJ..1002L..28Y: A Close Quasar Pair in a Massive Galaxy Merger at z = 5.7 (2026; agn_and_quasars, high_z_galaxies; observational_alma_primary)
- question: Is J2037–4537 a physical close quasar pair in a galaxy merger at z=5.7 rather than a doubly-imaged lensed quasar, and what are the host galaxy properties and implied pair fraction?
- step 4: Lens modeling test
  - method: Fit continuum and [C II] with singular isothermal ellipsoid plus external shear lens and Sersic sources [3.1 Confirming the Close Quasar Pair Hy…: "We assume a singular isothermal elliptical density profile for the potential lensing galaxy, and add an external shear component"]
  - software: PyAutoLens
  - validation: Compared continuum and [C II] best-fit lens models, sizes and axis ratio [3.1 Confirming the Close Quasar Pair Hy…: "The best-fit lensing models for the continuum and the \[C ii\] line have significantly different deflector galaxy positions and Einstein radii"]
- limitation (authors): T_dust and beta assumed; multi-band FIR needed [3.2 Quasar Host Galaxy Properties: "Future multi-band FIR photometry is needed to directly constrain $T_\text{dust}$ and $\beta$ for J2037–4537."]
- limitation (authors): Pair fraction is a lower limit because the survey is incomplete [4.1 Quasar Pair Fraction: "This value is a lower limit because the survey of (cite: yue21) is incomplete."]
- not stated (card): Number of channels/channel width and velocity resolution of the [C II] cube; Cell size, image size, masks and clean thresholds; Calibrators and whether the pipeline or manual calibration was used; MCMC sampler, priors and likelihood for Gaussian line fits; PyAutoLens model setup, priors and settings; Which line-free channels were used given the line at the spectrum edge; Procedure for sigma used …

### 2019ApJ...873...50D: Source Structure and Molecular Gas Properties from High-resolution CO Imaging of SPT-selected Dusty Star-forming Galaxies (2019; high_z_galaxies; observational_alma_primary)
- question: How do the sizes, magnifications and kinematics of high-J CO and dust continuum compare in lensed SPT DSFGs, and does differential magnification bias LVG-derived gas properties?
- step 2: Visibility-based lens modeling of continuum and CO channels
  - method: SIE lens(es) plus Sérsic sources fit to visibilities; continuum and channels fit simultaneously with shared lens parameters; also single-channel models [3 Lens modeling: "we fit the continuum and the CO line channels simultaneously, i.e. fitting multiple source components with one shared set of lens parameters."]
  - software: visilens, emcee
  - parameter: time averaging up to 10 min with uv separation <15 m; velocity bins 75-250 km/s [3 Lens modeling: "For line data we divide the data into 75–250 km s$^{-1}$ velocity bins, depending on the flux distribution and SNR of the line."]
  - parameter: 1000 chains, 1000 burn-in, 1000 extra steps [3 Lens modeling: "Generally, we run 1000 chains with 1000 burn-in steps and 1000 extra chain steps."]
  - assumption: Flat Planck LCDM: h=0.677, Om=0.308, OL=0.691 [1 Introduction: "we assume a flat Planck $\Lambda$CDM cosmology, where $h = 0.677$, $\Omega_m = 0.308$, and $\Omega_\Lambda = 0.691$"]
  - fitting: emcee MCMC; median and 1 sigma intervals [3 Lens modeling: "We quote the median value of each parameter of the sample as the estimated value and the $1\sigma$ interval as the uncertainty."]
  - validation: Chain convergence, residual images, DIC model selection [3 Lens modeling: "we use the Deviance Information Criterion (cite: Spiegelhalter02) for model selection"]
- step 3: Compare CO and dust sizes and magnifications
  - method: Circularized half-light size sqrt(a_S b_S) from MCMC chains for CO single channels (500-800 km/s) vs continuum; magnification comparisons across channels, continuum and transitions [4.1 Source Sizes: "We calculate the circularized size and its uncertainty from the MCMC chains as $\sqrt{a_S b_S}$"]
  - software: visilens
  - validation: Compare mu*L'_intrinsic to apparent L' (Figure 3, Figure 8) [4 Analysis: "We quantify the ability of the lens models to recover the line fluxes by comparing the apparent CO line luminosities ($L^\prime_\mathrm{apparent}$) to the product of the magnification and intrinsic line luminosities"]
- result: SPT0346-52 CO(8-7) magnification (150 km/s channels) = 6.0 ± 0.2 dimensionless [Table 4: "| SPT0346-52 | CO(2-1) | 5 | 150 | 0.26 $\pm$ 0.02 | 7.20 $\pm$ 0.53 | 6.1 $\pm$ 0.7 |"]
- result: Continuum magnification SPT0346-52 / 0529-54 / 0532-50 / 2147-50 = 5.1 / 12.4 / 7.9 / 4.8 ± 0.1 / 0.6 / 0.2 / 0.2 dimensionless [Table 3: "| SPT0529-54 | 1.94 $\pm$ 0.15 | 3.06 $\pm$ 0.80 | 662.0 | 7.59 $\pm$ 0.03 | 0.57 $\pm$ 0.04 | 12.4 $\pm$ 0.6 |"]
- result: Dust vs CO circularized size, SPT0346-52 = r_dust 0.55, r_CO 0.73 ± 0.02, 0.04 kpc [Table 3: "| SPT0346-52 | 0.55 $\pm$ 0.02 | 0.73 $\pm$ 0.04 | 966.7 | 14.75 $\pm$ 0.03 | 2.95 $\pm$ 0.05 | 5.1 $\pm$ 0.1 |"]
- result: Dust vs CO circularized size, SPT2147-50 = r_dust 1.14, r_CO 2.20 ± 0.06, 0.61 kpc [Table 3: "| SPT2147-50 | 1.14 $\pm$ 0.06 | 2.20 $\pm$ 0.61 | 659.2 | 4.30 $\pm$ 0.02 | 0.88 $\pm$ 0.05 | 4.8 $\pm$ 0.2 |"]
- result: SPT2147-50 CO(2-1) vs CO(6-5) magnification = ~8 vs ~5 (~60% higher) ± not stated dimensionless [4.2 Magnification: "for SPT2147-50 we see CO(6-5) magnified by a factor $\sim$5 and CO(2-1) magnified by $\sim$8$\times$, $\sim$60% higher than the high-J CO magnification."]
- limitation (authors): Parameterized Sérsic modeling cannot independently constrain faint emission at large radii [4.1 Source Sizes: "the faint emission at large radii is not independently constrained because of our parameterized modeling"]
- limitation (authors): Simple Sérsic profiles unlikely to fully characterize source structure [3 Lens modeling: "While simple Sérsic profiles are unlikely to fully characterise the source structure"]
- not stated (card): Imaging parameters (cell size, image size, mask, threshold, channel binning) for CLEAN; Pipeline/CASA version; Line-free channels for continuum subtraction; Priors on lens/source parameters in visilens; Flux calibrators and flux scale uncertainty; Which lower-J line fluxes (Table 2) come from which references and how apparent line luminosity uncertainties were propagated; Likelihood form and trea…

### 2015PASJ...67...72T: High-resolution ALMA observations of SDP.81. I. The innermost mass profile of the lensing elliptical galaxy probed by 30 milli-arcsecond images (2015; high_z_galaxies, agn_and_quasars; observational_alma_primary)
- question: What is the innermost mass profile and central SMBH mass of the foreground elliptical lensing SDP.81, derived from lens modeling of 30 mas ALMA images?
- step 4: Fit lens mass model
  - method: Isothermal ellipsoid with core, external shear, third-order and (4,2) multipole perturbations fit to image positions with MCMC errors [3.1 Methods and results: "We then refine the mass model by adding the higher-order perturbations (the number of independent parameters is 12) and fitting all of the identified multiple images."]
  - software: GLAFIC
  - parameter: Position uncertainty 20 mas; 100–200 mas for 10 blended knots; 130–200 mas for HST images; N_DOF = 88 [3.1 Methods and results: "The positional uncertainty of the knots used for optimization is set to 20 mas"]
  - assumption: Flat universe Ωm=0.26, ΩΛ=0.74, H0=72 [1 Introduction: "we assume a flat universe with $\Omega_\mathrm{m} = 0.26$, $\Omega_{\Lambda} = 0.74$, and $H_0 = 72$ km s$^{-1}$ Mpc$^{-1}$"]
  - fitting: Chi-square minimization with MCMC for 68% intervals [3.1 Methods and results: "the $1\sigma$ confidence intervals are computed by Marcov-chain Monte Carlo simulations"]
  - validation: Compared with independent ALMA (Rybak15, Dye15) and HST (Dye14) models [3.1 Methods and results: "The best-fit parameters of the isothermal ellipsoid and external shear are in good agreement with those independently obtained using the same ALMA images"]
- step 5: Compare lens mass profile with stellar light
  - method: Convergence profile vs HST profile scaled by M/L = 2, lens model smoothed by HST PSF [3.2 Mass profile of SDSS J0903: "the stellar surface mass is scaled using a fiducial mass-to-light ratio of $2~M_{\solar}~L_{\solar}^{-1}$"]
  - assumption: M/L = 2 Msun/Lsun at ~1 µm [3.2 Mass profile of SDSS J0903: "which is a typical value for local massive ellipticals"]
- result: Core radius of isothermal ellipsoid = 48 ± +169/-28 mas [3.2 Mass profile of SDSS J0903: "$r_\mathrm{core} = 48 ^{+169}_{-28}$ mas"]
- result: Velocity dispersion = 265 ± +15/-4 km/s [4 Discussions and conclusions: "$\sigma_v = 265 ^{+15}_{-4}$ km s$^{-1}$"]
- result: Position angle of ellipsoid = 11 ± 13 deg [3.2 Mass profile of SDSS J0903: "$\theta_e = 11 \pm 13 \ensuremath{^\circ}$"]
- result: Total magnification = ~22 ± not stated dimensionless [3.1 Methods and results: "the total magnification factor is expected to be $\mu_\mathrm{g} \sim 22$"]
- result: Lens-model chi2 = 3.45 ± not stated dimensionless [3.1 Methods and results: "($\chi^2 = 3.45$)"]
- limitation (authors): Core radius and velocity dispersion highly degenerate; BH mass and core radius degenerate [3.1 Methods and results: "Note that the core radius ($r_\mathrm{core}$) and velocity dispersion ($\sigma_v$) of the isothermal ellipsoid are highly degenerate."]
- not stated (card): ALMA imaging/calibration settings (tclean parameters, robust, CASA version) are deferred to other papers; Exact positions and fluxes of the 46 identified knots; Initial parameter values and MCMC settings (chain length, priors) for GLAFIC; Fixed reference position of the non-thermal source; Mass-to-light ratio uncertainty treatment

### 2025NatAs...9.1553F: Primordial rotating disk composed of at least 15 dense star-forming clumps at cosmic dawn (2025; high_z_galaxies; observational_alma_primary)
- question: How do the internal clumpy substructure and the underlying gas dynamics of a lensed young galaxy at z=6.072 relate, and how does this compare with simulations?
- step 2: Fit 3D tilted-ring kinematics
  - method: 3DBarolo on source-plane cubes of [C II], Halpha, [O III]; inclination from F150W axis ratio [9. Kinematic modeling: "we obtain the axis ratio of $q\simeq0.53$ and calculate $i=\arccos(q)\simeq57.9$ deg"]
  - software: 3DBarolo
  - parameter: free: V, sigma, PA, inclination; ring width (0.5-1.0) x PSF FWHM; AZIM normalization [9. Kinematic modeling: "We use $V$, $\sigma$, PA, and inclination as free parameters."]
  - assumption: circular rotation [9. Kinematic modeling: "under the assumption of circular rotation"]
  - fitting: 3DBarolo tilted-ring fit [9. Kinematic modeling: "A 3D tilted-ring model is employed in `3DBarolo`, allowing us to derive rotation curves and gas dynamics in a non-parametric fashion, under the assumption of circular rotation."]
  - validation: Monte Carlo mock cubes show Vmax/sigma0 overestimated by 4±2%; PVsplit classification indicates single disk [9. Kinematic modeling: "the $V_{\rm max}/\sigma_{0}$ value could be overestimated by $4\pm2\%$ for our observation setup"]
- result: Vmax/sigma0 ([C II]) = 3.58 ± 0.74 dimensionless [Extended Data Table 5: "3.58 $\pm$ 0.74"]
- result: Inclination = 57.9 ± not stated deg [9. Kinematic modeling: "$i=\arccos(q)\simeq57.9$ deg"]
- limitation (authors): Magnification systematic uncertainty up to ~25% [4. Lens model: "we conclude that the magnification uncertainty in this study does not exceed $\sim$25%"]
- limitation (authors): Clump number may increase with better data; ALMA beam larger than clumps so gas mass only for 7 clumps [7. Properties of the individual star-fo…: "while this number could be increased with further high-resolution observations in the future"]
- not stated (card): Line-free channels and frequency range used for continuum fit; Source-plane reconstruction algorithm details and resulting cube pixel scale; 3DBarolo parameter file settings (ring widths, normalization details, masking thresholds); Calibrators and flux-scale uncertainty for ALMA data; Exact SExtractor/GALFIT convergence setup and PSF used for GALFIT; How [C II] luminosity per pixel was derived fr…

### 2020A&A...633A.160C: The ALMA Frontier Fields Survey. V. ALMA Stacking of Lyman-Break Galaxies in Abell 2744, Abell 370, Abell S1063, MACSJ0416.1-2403 and MACSJ1149.5+2223 (2020; high_z_galaxies, galaxy_clusters_and_sz; large_program_or_survey)
- question: What are the IR properties and IR excess (IRX) of UV-selected LBGs at z~2-8 behind five Frontier Fields clusters, individually and via stacking, and how do they compare with IRX-beta and IRX-M* relations?
- step 2: Derive LBG properties from HST photometry
  - method: FAST++ photo-z and stellar mass/SFR; MCMC power-law fit for beta; magnification from CATS lens model capped at 10 [2.4 Photometric redshifts: "we used the `C++` version[^5] of the code `FAST` (cite: 2009ApJ...700..221K) with a bin size of $\Delta z_{ph} {=} 0.001$ and $500$ Monte Carlo simulations per source"]
  - software: FAST++, emcee
  - parameter: 2500 iterations x 100 walkers per source for beta [2.6 UV-continuum slope: "For each LBG candidate, $2500$ iterations were performed per each one of the $100$ "random-walkers" which were set for this procedure."]
  - assumption: BC03 SEDs, Chabrier IMF, tau=1e11 yr, 0.2 Zsun, Calzetti law with 0<=A_V<=1 [2.7 Stellar masses: "setting $\log_{10}{(\tau / \mathrm{yr})}{=}11$ with an exponentially declining star formation history (SFR ${\propto} \exp(-t/\tau)$) and a metallicity of $0.2 Z/Z_{\odot}$"]
  - fitting: emcee with priors from maximum-likelihood estimator [2.6 UV-continuum slope: "As priors for the model fitting, we used the outputs of a simple maximum likelihood estimator with Eq."]
  - validation: Photo-z compared to dropout bands and MUSE spec-z; mismatches removed [2.4 Photometric redshifts: "Among the 238 matches, only 14 candidates have strong differences between their photometric and spectroscopic redshifts; all 14 were removed."]
- limitation (authors): Stellar masses below ~10^8.5 Msun likely incomplete; selection biases at low mass [5.1.5 M-beta correlation: "we could have strong selection effects that bias the resulting fitted relations at low stellar masses."]
- limitation (authors): Stacked values biased toward high-weight sources [3.3 Considerations on stacking weighting: "our stacked result can be biased toward the candidates with the highest weights."]
- not stated (card): CLEAN parameters (robust/threshold/niter/cell/image size, masking) for the mosaic images; Exact B19 LBG catalog (in prep) needed to reproduce the sample; Dust temperature formula parameters and SED normalization details; STACKER run parameters; Flux calibrators and flux scale uncertainty; Exact bin assignment of the 4.0>=z<=7.0 boundary and how 1580 vs 1582 sources were handled; Weights/treatment…

### 2020ApJ...892L..18I: ALMA 50-parsec-resolution Imaging of Jet-ISM Interaction in the Lensed Quasar MG J0414+0534 (2020; agn_and_quasars, high_z_galaxies; observational_alma_primary)
- question: Is there jet-ISM interaction in the host of the lensed quasar MG J0414+0534 at z=2.639, as seen in resolved continuum and CO(11-10) at ~50 pc resolution?
- step 2: Lens modeling and de-lensing
  - method: SIE+cored isothermal sphere+shear background model fit to HST/VLBI/MIR constraints; subhalo perturbations fit with ALMA continuum; de-lensed images from linear combination of A1, A2, B [Lens modeling and de-lensing: "Using the best-fit lensing model, we reconstructed de-lensed images of the continuum and CO(11-10) line from a linear combination of three de-lensed images of A1, A2 and B."]
  - fitting: Minimizing differences between de-lensed images with astrometric/magnification constraints [Lens modeling and de-lensing: "We obtained a best-fit model by minimizing the differences between the de-lensed images"]
  - validation: Residual position errors <0.003'' below HST errors [Lens modeling and de-lensing: "The residual errors in the relative positions are $<0.003\ensuremath{''}$"]
- result: Magnification, continuum = 37 ± 4 dimensionless [Lens modeling and de-lensing: "the total magnification factors for the continuum and CO(11-10) are $37\pm4$ and $28\pm 3$, respectively."]
- result: Magnification, CO(11-10) = 28 ± 3 dimensionless [Lens modeling and de-lensing: "the total magnification factors for the continuum and CO(11-10) are $37\pm4$ and $28\pm 3$, respectively."]
- limitation (authors): Core component interpretation not conclusive. [Continuum: "Though not conclusive, our result suggests that *q* corresponds to quasar circumnuclear dust emission or synchrotron radiation"]
- not stated (card): Calibrator names and pipeline vs manual calibration; Cycle 2 array configuration and dates; Line-free channels used for continuum; Self-cal solution intervals; Image size, cell size, clean threshold/masks; Lens model parameters and code (inoue2020 in preparation); Gaussian PSF subtraction amplitudes; RADEX input details and line width/size assumptions

### 2016MNRAS.457.2936I: ALMA imprint of intergalactic dark structures in the gravitational lens SDP.81 (2016; high_z_galaxies, cosmology; archival_reuse)
- question: Whether anomalous flux ratios and astrometric shifts in the lensed images of SDP.81 reveal perturbations from intergalactic dark structures along the line of sight
- step 1: Fit SIE+external shear lens model
  - method: Simultaneous chi^2 fit of positions of bright clump peaks (S/N>~10) and the lens galaxy AGN centroid in band 7 continuum [3.1 Canonical Lens Model: "In order to implement the simultaneous $\chi^2$ fitting of the positions of the centroids of lensed images and the lensing galaxy, we used our developed code."]
  - software: in-house code, GRAVLENS
  - parameter: position errors 1/4 of beam (6x8 mas); G error 0.02 arcsec [3.3 Modelling: "the 1$\,\sigma$ errors are 1/4 of $\theta_{\textrm{beam}}$, i.e., $6 \times 8$ mas with the same PA direction."]
  - assumption: SIE plus external shear [3.1 Canonical Lens Model: "we adopt a singular isothermal ellipsoid (SIE) (cite: kormann1994)"]
  - fitting: chi^2 minimization; 1 sigma from parameter range with reduced chi^2 < 1 [4.1 Best-fitted Model: "The 1 $\sigma$ uncertainty in the model parameters are obtained by finding a range of each parameter that gives the reduced $\chi^2$ less than 1."]
  - validation: Code compared with GRAVLENS, chi^2 within a few percent; compared with literature models [3.1 Canonical Lens Model: "The obtained $\chi^2$ values are consistent each other within a few percent."]
- step 2: Measure source-plane aperture flux ratios
  - method: Invert images to source plane, uniform/magnification weighted combination, compute aperture fluxes of B,C,D relative to A; errors from Monte Carlo of 100 random points in noise ring [4.2 Flux in Aperture: "First, we randomly selected 100 points within a ring region with an angular distance $R$ from the centre of the lens satisfying $3.5<R<4.3$ arcsec."]
  - parameter: aperture radii 0.04, 0.05, 0.06 arcsec [4.2 Flux in Aperture: "computed the fluxes in circles with aperture radius $0.04,0.05,0.06$ arcsec"]
  - validation: Hypothetical observation with beam convolution gives <4% error [4.2 Flux in Aperture: "We have found that the errors in the aperture flux ratios are less than 4 percent."]
- result: Reduced chi^2 of best-fit SIEES = 0.22 (0.647/(16-13)) ± not stated dimensionless [4.1 Best-fitted Model: "the reduced $\chi^2$ ($=\chi^2$/dof) is $0.647/(16-13)=0.22$"]
- result: Einstein radius b = 1.605 ± +0.030/-0.004 arcsec [Table 1: "$1.605^{+0.030}_{-0.004}$"]
- result: Aperture flux ratio B/A (best-fit, 0.06 arcsec) = 0.820 ± 0.062 dimensionless [Table 4: "ratio | 0.820 | 0.801 | 0.945"]
- result: Aperture flux ratio C/A (best-fit, 0.06 arcsec) = 0.801 ± 0.060 dimensionless [Table 4: "ratio | 0.820 | 0.801 | 0.945"]
- limitation (authors): Canonical lens model may be too simple; core, power-law deviation, multipoles could explain anomalies [6 Conclusion and Discussion: "The canonical lens model that we have considered may have been too simple."]
- not stated (card): Own lens-fitting code not released; optimizer details missing; Exact pixel coordinates of the clump peaks used as fit positions; Image-plane CLEAN products' exact archive file names; Channel velocity-to-index mapping and noise rms per channel; Aperture centres in the source plane; Details of CASA version used for archive images

### 2015MNRAS.451L..40R: ALMA imaging of SDP.81 - I. A pixelated reconstruction of the far-infrared continuum emission. (2015; high_z_galaxies; observational_alma_primary)
- question: What is the pixelated source-plane structure, magnification and star-formation rate density of the lensed starburst SDP.81 from ALMA 1 and 1.3 mm continuum visibilities?
- step 2: Lens mass model and pixelated source reconstruction
  - method: Bayesian visibility-space fit with Delaunay-tessellated source grid, gradient regularisation, elliptical power-law mass plus external shear; each spw reconstructed separately then averaged [3 Gravitational lens mass modelling: "The modelling method optimises the Bayesian evidence by minimising a combination of the $\chi^2$ measured in the visibility space and a regularisation performed on the source plane grid."]
  - parameter: Gradient regularisation [3 Gravitational lens mass modelling: "we adopt the gradient rather than the curvature regularisation to prevent the source from being overly smoothed"]
  - fitting: Maximum a posteriori; noise per baseline from rms of visibilities within an observing block [3 Gravitational lens mass modelling: "We estimate the noise level for each baseline at a given time and frequency by calculating the rms of the visibilities measured within the same observing block"]
  - validation: Visibility residuals consistent with Gaussian noise; consistency between spws and bands; error from rms scatter between spws [3 Gravitational lens mass modelling: "4.7 and 0.3 percent of the visibilities are out with the 2- and 3-$\sigma$ levels, respectively"]
- step 3: Magnification and intrinsic properties
  - method: Magnification as ratio of source-plane to image-plane emission; scale SED-derived properties of Negrello14 by it [4 The intrinsic source properties of SD…: "We estimate the lensing magnification $\mu$ of the source by calculating the ratio of the reconstructed emission in the source-plane and image-plane."]
  - assumption: Only far-infrared part of the SED considered, where magnification is valid [4 The intrinsic source properties of SD…: "we only consider the properties derived from the far-infrared part of the spectrum"]
- result: Total magnification = 17.6 ± 0.4 dimensionless [4 The intrinsic source properties of SD…: "The total magnification is found to be $\mu_{\rm tot} =$ 17.6 $\pm$ 0.4."]
- result: Star-forming disk magnification = 25.2 ± 2.6 dimensionless [4 The intrinsic source properties of SD…: "$\mu_{\rm SF~disk} =$ 25.2 $\pm$ 2.6"]
- result: Intrinsic SFR = 315 ± 60 Msun/yr [abstract: "giving an intrinsic total star-formation rate of 315 $\pm$ 60 M$_\odot$ yr$^{-1}$"]
- result: Dust mass = 6.4e8 ± 1.5e8 Msun [abstract: "a dust mass of 6.4 $\pm$ 1.5 $\times$ 10$^{8}$ M$_{\odot}$"]
- result: Total flux density Band 6 / Band 7 (<=0.5 Mλ) = 21.7 / 38.9 ± 2.2 / 3.9 mJy [2 ALMA continuum imaging: "21.7 $\pm$ 2.2 and 38.9 $\pm$ 3.9 mJy, respectively"]
- limitation (authors): Results may not extrapolate to general SMG population due to size-bias [4 The intrinsic source properties of SD…: "the results for this source should not necessarily be extrapolated to the general sub-mm galaxy population"]
- not stated (card): Regularisation strength / evidence optimisation details and priors on lens parameters; Source-grid pixel number and resolution; Which calibrated products/scripts were used and CASA version; How the 28 per cent flux offset in Band 6 spw0 was corrected; Conversion from far-IR luminosity to SFR (calibration) and how SFR density map was scaled; Rybak et al. 2015 method paper was in preparation; Image…

### 2024A&A...685A..80Z: Unveiling [C II] clumps in a lensed star-forming galaxy at z ∼ 3.4 (2024; high_z_galaxies; observational_alma_primary)
- question: Are there [C II]-emitting clumps (parent molecular clouds) in a lensed z~3.4 galaxy that hosts UV clumps, and what are their gas masses and depletion times?
- step 1: Model UV continuum of HST image
  - method: GALFIT Sérsic diffuse component plus PSF/Sérsic clump components; BCG subtracted; fluxes divided by magnification [3.1 Modeling the UV continuum 2D light …: "We then modeled the 2D surface brightness of our target with a 2D Sérsic profile (the galaxy “diffuse” component) and subtracted the best-fit model"]
  - software: GALFIT, SExtractor
  - validation: Residuals consistent with noise; repeated on M2 [3.1 Modeling the UV continuum 2D light …: "We repeated this analysis independently on M2 and reached consistent conclusions."]
- step 5: Measure clump [C II] fluxes
  - method: uv-plane fit of 2D PSF per channel with free centre (method 3), summed over adjacent channels; compared to image-plane and Gaussian fits; corrected by average magnification [3.6 Measuring clumps [C II] flux: "We decided to adopt the flux measurements obtained by fitting clumps with PSF models"]
  - software: GILDAS
  - assumption: Clumps unresolved [3.6 Measuring clumps [C II] flux: "as they are expect to be unresolved at the resolution of our observations"]
  - validation: Five flux methods compared; conclusions unchanged [3.6 Measuring clumps [C II] flux: "Even when adopting fluxes obtained with the other reported methods, the conclusions of our work do not change substantially."]
- limitation (authors): Clump C is tentative and needs confirmation; dynamical modelling is beyond scope [3.5 Identifying clumps: "More observations with higher S/N are needed to confirm it."]
- not stated (card): Line-free channel ranges used for the continuum map; Exact uv_fit/imaging settings (cell size, image size, uv taper) in GILDAS; Absolute flux calibration uncertainty and phase calibrators; Full details of the lens model and magnification maps (from Iani2021); Kennicutt UV-SFR conversion constants after IMF scaling; Area definition used for the surface densities of clumps; Number of ALMA antennas …

### 2023Natur.621..483G: Polarized thermal emission from dust in a galaxy at redshift 2.6 (2023; high_z_galaxies; observational_alma_primary)
- question: Is there a large-scale ordered magnetic field in a z=2.6 lensed starburst galaxy, as traced by polarized dust emission?
- step 3: Constrain source-plane B-field orientation via lens simulation
  - method: Lens source-plane Gaussian disk with constant chi_B and P=1%, lensed with SIE+shear, simulated with simobserve, cleaned like data; compare Stokes U detection [Constraining the B-field orientation: "We can constrain the orientation by rotating the *B*-field until the corresponding Stokes $U$ image shows a $3\sigma$ detection in the synthetic polarimetric observations."]
  - software: lenstronomy, CASA simobserve
  - parameter: 801x801 grid, 0.01'' pixel; pwv 0.6 mm; antenna configuration 2 (Cycle 8) [Lens modelling: "Using a grid of $801\times801$ pixels$^{2}$ with a scale of $0.01\mbox{$^{\prime\prime}$}$ pixel$^{-1}$"]
  - assumption: Constant polarization fraction of unity/1% and constant B orientation in source plane; continuum matches CO morphology [Lens modelling: "The *B*-field orientation in the source plane is assumed to be constant, $\chi_{B,{\rm sp}}$, with a constant polarization fraction of unity"]
  - fitting: Grid of chi_B values, no sampler [Methods, Constraining the B-field orien…: "With a polarization fraction of 1% we set a range of constant $\chi_{B,{\rm sp}}$ orientations in the source plane."]
  - validation: Lens and convolution do not rotate or change P; noise adds ~10 deg uncertainty [Constraining the B-field orientation: "We conclude that the lens model and convolution do not produce rotation or change in the polarization fraction from the source plane to the image plane."]
- result: Source-plane B-field orientation = 5 ± +5/-10 deg east of north [main text: "orientated $\chi_{\rm B} =5^{+5}_{-10}$ degrees east of north"]
- limitation (authors): Lack sensitivity and resolution to map B-field at ~100 pc scales; field strength cannot be reliably estimated from dust polarization [main text: "We currently lack the sensitivity and resolution to map the configuration of the *B*-field strength at scales $\sim$100 pc"]
- not stated (card): Image size and cell size for tclean; Polarization calibration script details and polarization calibrator model; Self-calibration, if any; Pipeline version; Masking used in cleaning; Exact sensitivity-weighted selection of pixels for averages; Total on-source time

### 2019ApJ...870...80L: Spatially Resolved [C II] Emission in SPT0346-52: A Hyper-starburst Galaxy Merger at z ∼ 5.7 (2019; high_z_galaxies; observational_alma_primary)
- question: What is the source-plane structure and kinematics of the lensed DSFG SPT0346-52 in [CII] and dust continuum, and does the [CII] deficit hold on sub-kpc scales?
- step 2: Fit lens model to continuum
  - method: Pixellated visibility-plane reconstruction with SIE (z=0.9) plus external shear; lens parameters from MCMC, regularization lambda iterated [3.2: "We model the lensing galaxy as a singular isothermal ellipsoid at $z=0.9$ with an external shear component."]
  - software: RIPPLES
  - parameter: lambda fitted for fixed lens model, alternating with MCMC until convergence [3.1: "We fit for $\lambda$, then run the MCMC with RIPPLES. These two steps are repeated until the chains have converged"]
  - assumption: Lens at z=0.9 [3.2: "singular isothermal ellipsoid at $z=0.9$"]
  - fitting: chi^2 against visibilities, MCMC; priors not stated [3.1: "The model visibilities are compared to the observed visibilities via a $\chi^2$ goodness-of-fit test."]
  - validation: Mock point-source visibilities reconstructed to give effective source-plane resolution [3.3 Source Plane Resolution: "we created a set of mock visibilities for a point source in the source plane that was lensed by the best-fit lens model."]
- step 3: Reconstruct [CII] per channel and build maps/spectra
  - method: Apply best-fit lens model to each 50 km/s channel with fixed lambda; sum channels into moment maps; sum pixels for source spectrum and fit two Gaussians [3.2: "The best-fit model was then applied to the \[CII\] line in each $50\ \rm{km\ s^{-1}}$ channel."]
  - software: RIPPLES
  - fitting: two-component Gaussian fit to source-plane spectrum [3.2: "A two-component Gaussian was fit to the spectrum"]
- result: Blue component velocity = -287 ± 22 km/s [3.2: "The blue component is centered at $-287\pm 22\ \rm{km\ s^{-1}}$ and has a FWHM of $337\pm 22\ \rm{km\ s^{-1}}$."]
- result: Red component velocity = +158 ± 22 km/s [3.2: "The red component is centered at $+158 \pm 22\ \rm{km\ s^{-1}}$ with a FWHM of $319 \pm 15\ \rm{km\ s^{-1}}$."]
- result: Effective source-plane resolution = 0.13x0.15 arcsec (0.12x0.12 near caustic) ± not stated arcsec [3.3: "the effective resolution is $0.13\ensuremath{''} \times 0.15\ensuremath{''}$"]
- result: Lens mass log = 11.43 ± 0.02 log Msun [Table 2: "$\rm{\log{Mass[M_{\odot}]}}$ | $11.43 \pm 0.02$"]
- limitation (authors): Constant dust temperature assumed, uncertainty within factor ~2 [4.1: "the variation caused by variable dust temperatures in the galaxy is within a factor of $\sim 2$."]
- not stated (card): Image size, cell size, clean masks/threshold and number of iterations; Line-free channels for UVCONTSUB and continuum bandwidth; RIPPLES source pixel grid size, priors and MCMC settings; Value of regularization lambda for the [CII] cube; Spectral windows and which data were combined for the reconstruction; Dust-continuum frequency/flux scale and amplitude calibration uncertainty; Rest frequency o…

### 2015ApJ...812...88M: Stellar Masses and Star Formation Rates of Lensed, Dusty, Star-forming Galaxies from the SPT Survey (2015; high_z_galaxies; multi_facility_alma_minor)
- question: What are the stellar masses, IR luminosities, SFRs and specific SFRs of six strongly lensed SPT dusty star-forming galaxies, after de-blending the lens from the source in Spitzer/IRAC?
- step 3: SED fitting for stellar mass, LIR and SFR
  - method: CIGALE fit of HST to SPT photometry with single-component tau-model SFH, grid of parameters, magnification correction [5 SED fitting: "we utilize the code CIGALE (cite: burgarella05; noll09)[^3] to fit our photometric data from near-IR to far-IR."]
  - software: CIGALE
  - parameter: Maraston05 SPS, Kroupa IMF, solar metallicity; grids in age, tau, A_V, delta, alpha [5 SED fitting: "We adopt the (cite: maraston05) (2005; M05) stellar population synthesis model, a (cite: kroupa01) initial mass function (IMF), and a solar metallicity as our baseline."]
  - assumption: Flat LCDM H0=70, OmegaM=0.3; ALMA magnification applied to stellar emission [1 Introduction: "we use a standard cosmological model with $H_0=70$ ${\rm km}$ ${\rm s}^{-1}$${\rm Mpc}^{-1}$, $\Omega_M=0.3$, and $\Omega_{\Lambda}=0.7$."]
  - fitting: Expectation values and standard deviations from the PDF of parameter-bin best-fit models [5.2 SED fitting results: "Expectation values and standard deviations for the output galaxy properties are derived from the probability distribution function of the parameter-bin-specific best-fit models."]
  - validation: Compared with SFRs from LIR conversions and with BC03 and two-component SFH [5.2 SED fitting results: "All of the SFRs derived by CIGALE SED fitting are consistent with those by the conversion recipes."]
- result: Median stellar mass = ~5e10 ± not stated Msun [abstract: "with a median value $\sim$ 5 $\times 10^{10}M_{\Sun}$"]
- result: SPT0103-45 stellar mass = 5.5e10 ± +6.1/-2.9 e10 Msun [Table 5: "| SPT0103-45 | $5.5 ^{+ 6.1}_{- 2.9}\times10^{10}$ |"]
- result: SPT0346-52 SFR (CIGALE) = 4840 ± +1090/-890 Msun/yr [Table 5: "$4840 ^{+ 1090}_{- 890}$"]
- result: SPT0538-50 stellar mass = 3.9e10 ± +8.0/-2.6 e10 Msun [Table 5: "$3.9 ^{+ 8.0}_{- 2.6}\times10^{10}$"]
- result: SPT2147-50 sSFR = 64.0 ± +68.6/-33.1 Gyr^-1 [Table 5: "$64.0 ^{+ 68.6}_{- 33.1}$"]
- result: Best-fit burst ages = 20-80 ± not stated Myr [5.2 SED fitting results: "The best-fit burst ages are 20 – 80 Myr."]
- limitation (authors): Stellar mass depends strongly on inputs; uncertainties dominated by few optical/NIR points; differential lensing not measured [5.2.1 Systematics: "Our uncertainties are dominated by the limited number of photometric data points at optical/near-IR wavelengths."]
- not stated (card): ALMA calibration/imaging software and CASA version; Final ALMA beam and rms; Magnification values from Spilker et al. (in prep) beyond Table 2; Exact CIGALE version and module configuration; PyGFit masks and aperture radii per source; Reduced HST/Spitzer data access details

### 2025ApJS..278...45F: DUALZ—Deep UNCOVER-ALMA Legacy High-Z Survey (2025; high_z_galaxies, galaxy_clusters_and_sz; large_program_or_survey)
- question: Establish a joint ALMA and JWST legacy field in Abell 2744 and, through a blind 1.2-mm survey with NIRCam/NIRSpec counterparts, characterize the faint dust continuum sources, HST-/JWST-dark galaxies, a z=6.33 [CII] emitter, z>9 galaxies, a…
- step 5: Redshifts and physical properties
  - method: Prospector-beta SED fitting (dynesty, parrot) and EAZY; use zspec if available, else zphot; EAZY adopted if estimates differ by >1.0; magnification from Furtak lens model [3.4: "In a few cases, the two $z_{\rm phot}$ estimates deviate by more than 1.0, and in such cases, we adopt the $z_{\rm phot}$ estimate from `EAZY`"]
  - software: Prospector, dynesty, parrot, EAZY, FSPS
  - assumption: AID20 assumed z=2.0; AID60 assumed z=9.0 [3.4: "For AID60 that lacks a NIRCam counterpart, we assume $z=9.0$"]
  - fitting: Prospector-beta with nested sampling dynesty; Chabrier IMF, 7-bin SFH, two-component dust [3.4: "A sampling of the posterior space is performed using the nested sampler `dynesty`"]
  - validation: all 27 spec-z sources have |dz|/(1+z)<0.15; outlier fraction zero [3.4: "all 27 sources fall in the range of $|z_{\rm spec}-z_{\rm phot}|/(1+z_{\rm spec}) < 0.15$"]
- result: Median redshift, magnification, intrinsic flux = z=2.30, mu=1.7, S_int=0.24 mJy ± not stated mixed [3.4: "median values of $z=2.30$, $\mu=1.7$, and $S_{\rm 1.2mm}^{\rm int}=0.24$ mJy"]
- result: Spectroscopically confirmed sources = 27 ± not stated sources [3.4: "This yields 27 sources whose redshifts have been spectroscopically determined."]
- limitation (authors): 1-2 sources may be spurious; no completeness correction for IRLF; z>9 detections marginal [3.1: "This implies that $\sim$1–2 out of the 69 sources might be spurious"]
- not stated (card): Flux calibrator and flux-scale uncertainty; Which channels/spectral windows used for continuum maps; Cube-based line search method and S/N criteria (only prior-based [CII] search described); Details of aperture photometry for the [CII] line optimized extraction; Final Wide/Deep PB-corrected noise maps and mosaic phase centers; Full SED fitting and NIRSpec reduction details (deferred to Wang et al…

### 2020ApJ...902...78R: The Complete Redshift Distribution of Dusty Star-forming Galaxies from the SPT-SZ Survey (2020; high_z_galaxies; large_program_or_survey)
- question: What is the complete spectroscopic redshift distribution and the intrinsic properties of the SPT-selected lensed DSFGs, and how do they compare with unlensed DSFGs and galaxy formation models?
- step 4: Derive intrinsic properties
  - method: LFIR 42.5-122.5 um, LIR 8-1000 um; dust mass from rest 345 GHz flux; SFR from Murphy+11 conversion; demagnify with lens models or median mu=5.5 [2.3.3: "The apparent FIR luminosity ($L_{\rm FIR}$) is calculated by integrating the fitted SED over the wavelength range $42.5-122.5\, \mathrm{\mu m}$"]
  - assumption: kappa = 0.015 (nu/250 GHz)^beta m^2/kg, beta=2; gas-to-dust ratio 100; Kroupa IMF; flat LCDM H0=68.1 [2.3.3: "We adopt $\kappa(\nu)/\, \mathrm{m^2 kg^{-1}} = 0.015 \times (\nu_r/250\, \mathrm{GHz})^{\beta}$"] [4.3: "Molecular gas mass was obtained by assuming a constant gas-to-dust ratio (taken to be $100$; e.g. (cite: casey14))."]
  - validation: Compared with MAGPHYS where direct SED fit possible [4.3: "When a direct SED fit is possible, the two methods produce results that agree within the stated errors, with no bias."]
- result: Median intrinsic dust mass = 1.4e9 ± 0.1e9 Msun [3.2.2: "the SPT sources have a median intrinsic dust mass of $1.4(1)$$\times$$10^{9}\, \mathrm{M_\odot}$"]
- result: Median SFR = 2.3e3 ± 0.2e3 Msun/yr [4.3: "which corresponds to a median SFR of $2.3(2)\times 10^3\, \mathrm{{{\rm M}_{\odot} }yr^{-1}}$ for the SPT sample"]
- result: Median intrinsic LFIR = 7.1e12 ± 0.5e12 Lsun [3.2.2: "The median SPT intrinsic FIR luminosity is $7.1(5)$$\times$$10^{12}\, \mathrm{L_\odot}$"]
- limitation (authors): Lens models exist for only 39 sources; median magnification adopted for rest, so intrinsic properties are estimates [3.2.2: "given that the median magnifications are merely an estimate, the intrinsic properties for these sources should be also treated as estimates"]
- not stated (card): CASA version and whether pipeline or manual calibration was used; tclean cell size, image size, cleaning threshold and masks; Line fitting details (MCMC priors, line-free channels, line widths) for redshift determination; emcee settings (walkers, steps, priors on Tdust and redshift); Lens magnifications for the 42 unmodeled sources beyond the median 5.5; Exact ALESS data used and SED fitting adju…

### 2018A&A...613A..34P: ALMA view of RX J1131-1231: Sub-kpc CO (2-1) mapping of a molecular disk in a lensed star-forming quasar host galaxy (2018; high_z_galaxies, agn_and_quasars; observational_alma_primary)
- question: What are the distribution, kinematics and intrinsic properties of the molecular gas in the lensed quasar host galaxy RX J1131-1231, recovered by source reconstruction of ALMA CO(2-1) visibilities?
- step 2: Fit lens mass model on visibilities
  - method: Fit elliptical power-law main lens plus isothermal satellite, with external shear, to all CO channels combined in visibility space [4 Lens modelling and source reconstruct…: "We find the best fitting mass distribution parameters $\boldsymbol{\eta}_{best}$ by combining all channels in the CO (2-1) emission line together"]
  - parameter: eight free parameters [4 Lens modelling and source reconstruct…: "our mass model has eight free parameters"]
  - assumption: Gaussian uncorrelated noise [4 Lens modelling and source reconstruct…: "(assumed to be Gaussian and uncorrelated)"]
  - fitting: Penalty function with chi2 plus regularisation lambda^2||Hs||^2 [4 Lens modelling and source reconstruct…: "The optimisation is performed in the visibility space via the following penalty function"]
  - validation: Compared with HST and Keck lens models; within 2 sigma [4 Lens modelling and source reconstruct…: "are in agreement generally within 2-$\sigma$ with those derived by"]
- step 4: Dust SED, LIR and SFR
  - method: Modified blackbody fit to FIR and mm continuum; LIR 8-1000 um and SFR [5.2 Star-formation rate, far-infrared l…: "modified black body spectrum that was fitted to the far-infrared and mm-wavelength continuum emission"]
  - software: HIPE
  - assumption: dust traced by molecular gas, same magnification mu_CO = 7.3 [5.2 Star-formation rate, far-infrared l…: "we assume that the dust emission is traced by the molecular gas distribution and hence has the same magnification ($\mu_{CO} = 7.3$)"]
- result: Dust temperature = 21.0 ± +6.0/-4.6 K [3.1 Continuum emission: "$T_{\rm dust} = 21.0^{+6.0}_{-4.6}$ K"]
- result: SFR = 69 x (7.3/mu_IR) ± +41/-25 Msun/yr [5.2 Star-formation rate, far-infrared l…: "${\rm SFR} = 69^{+41}_{-25} \times (7.3 / \mu_{\rm IR})$ M$_{\odot}$ yr$^{-1}$"]
- limitation (authors): SED fit limited by differential magnification precision and lack of short-wavelength data [5.2 Star-formation rate, far-infrared l…: "This fit is limited by the precision of differential magnification and the lack of short wavelength data"]
- not stated (card): Line-free channels used for continuum imaging; Clean threshold, cell and image size; Lens-model sampler, priors and optimisation details; Regularisation form H and prior ranges; Modified blackbody fit method and photometry for SED; Dust and temperature assumptions for LIR and SFR conversion; How magnification of 7.3 was derived; Uncertainty derivation for dynamical mass and alpha; Surface density…

### 2015ApJ...811..115W: The Innermost Mass Distribution of the Gravitational Lens SDP.81 from ALMA Observations (2015; high_z_galaxies, agn_and_quasars; archival_reuse)
- question: Can the non-detection of the demagnified central image of lens SDP.81 in ALMA long-baseline CO maps constrain the lens galaxy's inner mass profile and SMBH mass?
- step 3: Fit lens mass models to image positions
  - method: Cored power-law (R_core 0.08'' or 0.15'' priors) and composite stellar+NFW models, plus SMBH point mass and external shear, using positions of three source features [3.3 Lens Mass Modeling: "We try two models for the mass distribution of the lens galaxy: a cored elliptical power-law mass distribution, and a composite model with separate stellar and dark matter components."]
  - software: Glee
  - parameter: MCMC chain length 5x10^5 [3.3 Lens Mass Modeling: "we first sample $L_{\rm pos}\times Q$ via MCMC of chain length $5\times10^5$, and then weight these samples by $L_{\rm flux}$"]
  - assumption: SMBH at mass centroid; uniform prior on log M_BH [6.5, 9.5] [3.3.1 Cored Elliptical Power-Law Model: "We assume that the SMBH is located at the center of the mass distribution and adopt a uniform prior on its logarithmic mass"]
  - fitting: MCMC, position likelihood Gaussian [Lens Mass Modeling: "In practice, we first sample $L_{\rm pos}\times Q$ via MCMC of chain length $5\times10^5$, and then weight these samples by $L_{\rm flux}$."]
  - validation: rms image offset ~0.015'' for power-law models [4.1 Lens Modeling Results: "we can reproduce the observed image positions with an rms offset between the observed and predicted image positions of $\sim 0.015\ensuremath{''}$"]
- result: Stellar M/L = 1.1 ± +0.1/-0.1 Msun/Lsun [4.1 Lens Modeling Results: "The predicted stellar mass-to-light (M/L) ratio is $1.1^{+0.1}_{-0.1}~\mathrm{M}_{\odot}~\mathrm{L}_{\odot}^{-1}$"]
- result: Dark matter fraction within Einstein radius = ~50 ± not stated percent [4.1 Lens Modeling Results: "The dark matter fraction within the Einstein radius is $\sim50$%"]
- limitation (authors): Fluxes of A, B, C not used owing to differential magnification (~30-50%) [3.1 Constraints From the Multiple Images: "we do not use the fluxes of these images as constraints due to the high uncertainty from differential magnification"]
- not stated (card): CLEAN parameters (weighting, robust, deconvolver, mask) for archival images; CO line velocity ranges and line-free channels for continuum subtraction; Exact archival image products used; Glee code availability and MCMC sampler details/burn-in; Rest frequencies of lines; How the E region and flux-extraction apertures were defined

### 2025ApJ...995..219F: PASSAGES: The Discovery of a Strongly Lensed Protocluster Core Candidate at Cosmic Noon (2025; high_z_galaxies, star_formation; observational_alma_primary)
- question: Is the Planck-selected lensed source PJ0846+15 a single DSFG or a strongly lensed protocluster core at z~2.67, and what are its lens model, SFR, gas/dust masses, dynamical mass and kinematics?
- step 4: Build strong lens model of foreground cluster
  - method: Parametric GLAFIC model with pseudo-Jaffe cluster members, NFW halo, second NFW for z=0.357 perturber; constrained by image positions, penalty for singly-imaged sources [4 The Lens Model: "To construct the lens model we used `GLAFIC` (cite: Oguri2010; Oguri2021), employing a parametric approach"]
  - software: GLAFIC, emcee, GALFIT
  - parameter: rms image-position separation 0.14" [4.4 The J0846 Model Results: "The best fit model reproduces the angular positions of identified multiply imaged systems to an rms separation of $0.14^{\prime\prime}$."]
  - fitting: emcee MCMC; likelihood from reproduced image positions plus penalty for extra images [4.4 The J0846 Model Results: "We construct the likelihood function based on the ability of the model to reproduce the positions of the observed multiply imaged systems."]
  - validation: 1000 posterior resamples for magnification uncertainty; systematics acknowledged not included [4.4 The J0846 Model Results: "we randomly resampled 1000 model iteration from the MCMC posterior distribution."]
- result: Global magnification (CO-weighted) = 7.7 ± 1.5 dimensionless [5.1 Star Formation Activity: "of $\mu=7.7\pm1.5$"]
- result: Lens model image-position rms = 0.14 ± not stated arcsec [4.4 The J0846 Model Results: "rms separation of $0.14^{\prime\prime}$"]
- limitation (authors): Lens model systematics not included; mass-sheet degeneracy possibly unbroken [4.4 The J0846 Model Results: "We acknowledge that this does not account for the systematics that arise from cluster lens modeling, that likely dominate the overall uncertainties."]
- limitation (authors): Gas mass is a lower limit given alpha_CO [5.2 Estimates of molecular gas and dust…: "thereby sets a lower limit for the molecular gas masses"]
- not stated (card): Line-free channel ranges and continuum-subtraction fit order; Clean threshold, niter, masking and deconvolver for tclean; Self-calibration and flux calibrator details; ALMA flux scale uncertainty; Exact line-extraction aperture masks and multi-Gaussian fit initial conditions; Lens model GLAFIC constraints, priors, parameter ranges, and MCMC settings (walkers, steps); Mass absorption coefficient u…

### 2020A&A...634L...3Y: First detection of the 448 GHz ortho-H<SUB>2</SUB>O line at high redshift: probing the structure of a starburst nucleus at z = 3.63 (2020; high_z_galaxies; observational_alma_primary)
- question: Can the first high-z detection of the 448 GHz ortho-H2O line, with other H2O lines and dust continuum, constrain the structure of the dusty ISM in the lensed SMG G09v1.97-R?
- step 2: Isolate R component and correct magnification
  - method: Associate detection (>=5 sigma) only with red component; correct line fluxes with mu_R=20; scale continuum down by 25 with 20% uncertainty [4 Analysis and Discussion: "Therefore, here we scale down the measured continuum fluxes by a factor of 25 and include an uncertainty of 20% associated with the flux scaling."]
  - assumption: Similar H2O(4_23-3_30)/H2O(2_11-2_02) flux ratio in R and B [4 Analysis and Discussion: "Assuming a similar flux ratio of H~2~O($4_{23}\text{--}3_{30}$)/H~2~O($2_{11}\text{--}2_{02}$) in R and B"]
- result: 448 GHz line luminosity in G09v1.97-R = 8.5e5 ± not stated Lsun [4 Analysis and Discussion: "the 448 GHz ortho-H~2~O($4_{23}\text{--}3_{30}$) line has a luminosity of $8.5 \times 10^{5}$ $L_\odot$"]
- result: Observed flux ratio F(1208)/F(448) = ≈11 ± not stated dimensionless [4 Analysis and Discussion: "The observed flux ratio in G09v1.97-R is only $\approx$ 11"]
- limitation (authors): Models neglect spatially varying Tdust, which could lower inferred N_H2O; AGN contribution cannot be ruled out [4 Analysis and Discussion: "our models do not include the effects of spatially varying $T_{\mathrm{dust}}$"]
- not stated (card): Model code and grid ranges not public (González-Alfonso et al., in prep.); Line-free channels, continuum subtraction and image size/cell size; Method to extract line flux and fit for 448 GHz line (aperture, velocity range); Continuum flux densities used in the fit and their sources; Priors/grid spacing for Tdust, tau100, NH2O, nH2; Lens model for magnification as a function of velocity

### 2018ApJ...866L..12G: A Magnified View of Circumnuclear Star Formation and Feedback around an Active Galactic Nucleus at z = 2.6 (2018; high_z_galaxies, agn_and_quasars; observational_alma_primary)
- question: What are the resolved molecular gas properties on sub-kpc scales around the AGN in the lensed galaxy 9io9 at z=2.6, and does the AGN affect star formation in the circumnuclear ring?
- step 3: Lens modelling and source-plane cubes
  - method: Semi-linear inversion with power-law primary lens, SIS companion, external shear, Bayesian evidence, MCMC on CO(4-3) integrated map, random Voronoi source pixelization; source-plane cube per channel [3.2 Lens modelling: "The set of parameters is optimized using the Markov Chain Monte Carlo (MCMC) method (Suyu et al. 2006)"]
  - assumption: Both lenses at same redshift for M/L ratio [3.2 Lens modelling: "assuming that both lie at the same redshift"]
  - fitting: MCMC, best fit by Bayesian evidence [3.2 Lens modelling: "until the global best fit has been obtained according to the Bayesian evidence (Suyu et al. 2006)"]
- step 4: Fit ring kinematics
  - method: galpak3d ring/disk model on source-plane CO(4-3) cube after PSF homogenisation (135 mas kernel); tanh rotation curve; 1000 chains of up to 5000 iterations with 10% perturbed starts [3.3 Dynamical modelling: "run 1000 independent chains, each with a maximum of 5000 iterations"]
  - software: galpak3d
  - assumption: alpha=0, Gaussian vertical profile [3.3 Dynamical modelling: "As in previous works, we fix $\alpha=0$"]
  - fitting: Median of converged parameters, 16th/84th percentiles as uncertainty [3.3 Dynamical modelling: "We take the 50th percentile of the converged parameters over the 1000 chains as the final estimate"]
  - validation: Median reduced chi2 = 1.08 [3.3 Dynamical modelling: "with a median reduced $\chi^2=1.08$"]
- result: Total magnification = 14.7 ± 0.3 dimensionless [3.2 Lens modelling: "The total magnification is $\mu=14.7\pm0.3$"]
- result: Ring outer radius Rmax = 2647 ± +88/-160 pc [3.3 Dynamical modelling: "$R_{\rm max}=322^{+11}_{-20}$ mas ($2647^{+88}_{-160}$ pc)"]
- result: Vmax = 360 ± +49/-11 km/s [3.3 Dynamical modelling: "$V_{\rm max}=360^{+49}_{-11}$ km s$^{-1}$"]
- result: Inclination = 50 ± +3/-8 degrees [3.3 Dynamical modelling: "$i=50^{+3}_{-8}$ degrees"]
- limitation (authors): Deblending of HNC/CN depends strongly on redshift; outflow rate cannot be estimated; limited tracers [4.2 A possible dense molecular outflow: "deeper observations will be required to properly model the complex"]
- not stated (card): Line-free channels used for continuum subtraction; Cell size and image size; Mask definition for clean; Lens model priors, number of pixels, and Voronoi settings; galpak3d starting values and priors, and the code modification; Details of how HNC/CN fit was done (fitter, priors); Flux calibrator and flux scale uncertainty; Whether CASA pipeline version was recorded; Continuum flux measurement

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

### 2024ApJ...967...11C: TEMPLATES: Characterization of a Merger in the Dusty Lensing SPT0418─47 System (2024; high_z_galaxies; multi_facility_alma_minor)
- question: Is the lensed dusty galaxy SPT0418-47 isolated or interacting with a companion, and how do the stellar masses and star formation of the two galaxies compare to the main sequence?
- step 2: Source plane reconstruction and lens model
  - method: SIE plus external shear, Sersic source, multi-band fit in F277W-F770W, with shapelets added [4.1 Source Plane Reconstruction and Kin…: "we use a Singular Isothermal Ellipsoid (SIE) with external shear."]
  - software: lenstronomy, emcee
  - fitting: Particle Swarm Optimization pre-sampling, then emcee MCMC run to convergence [4.1 Source Plane Reconstruction and Kin…: "We then use this approximate solution to seed the Markov Chain Monte Carlo (MCMC) sampler `emcee`"]
  - validation: Cross-check with backwards ray tracing of F277W, F356W, F444W using the lens model [4.1 Source Plane Reconstruction and Kin…: "This approach provides an alternative to the joint parametric - shapelet fitting"]
- step 3: Derive magnifications and photometry
  - method: Magnifications from 100 random MCMC draws; fixed-aperture photometry [4.2 Stellar Mass Ratios: "The uncertainties on the magnifications are derived from 100 random draws of the MCMC"]
- result: Projected physical separation of SPT0418A and B = 4.42 ± 0.05 kpc [4.1 Source Plane Reconstruction and Kin…: "the projected physical separation between the centers of the two galaxies is $4.42\pm 0.05$ kpc"]
- result: Total magnification SPT0418A = 29.5 ± 1.2 dimensionless [abstract: "$\mu=29.5\pm1.2$ and $\mu=4.2\pm 0.9$ for SPT0418A and SPT0418B"]
- result: Total magnification SPT0418B = 4.2 ± 0.9 dimensionless [abstract: "$\mu=29.5\pm1.2$ and $\mu=4.2\pm 0.9$ for SPT0418A and SPT0418B"]
- result: Fraction of FIR flux in SPT0418A = 96 ± 2 % [4.2 Stellar Mass Ratios: "we measure that $96\pm 2$% of the flux is associated with SPT0418A"]
- limitation (authors): Lens light subtraction was done separately from lens modeling, which hindered modeling with background noise [4.1 Source Plane Reconstruction and Kin…: "it would be prudent to perform the lens light subtraction within the software used to conduct the lens modeling"]
- limitation (authors): Constraints on SPT0418B are less robust owing to limited photometric detections [4.2 Stellar Mass Ratios: "The constraints on SPT0418B are less robust due to the more limited set of photometric detections"]
- not stated (card): tclean parameters: weighting/robust, deconvolver, cell and image size, masks, niter/threshold; line-free channel ranges for continuum subtraction; CASA version and calibration/self-calibration details of the ALMA data; how the [CII] velocity offset (-56 km/s) was measured; the 96% flux fraction method for SPT0418A; SED fitting priors beyond metallicity, burst parameters and photometric apertures

### 2021A&A...645A..45C: Planck's Dusty GEMS. VIII. Dense-gas reservoirs in the most active dusty starbursts at z ∼ 3 (2021; high_z_galaxies, astrochemistry; multi_facility_alma_minor)
- question: What are the dense-gas properties (line ratios, excitation, heating, star-formation law, dense-gas fractions) of lensed dusty starbursts at z~3 from HCN, HCO+ and HNC lines?
- step 3: Differential magnification of HNC vs CO
  - method: Luminosity-weighted magnification from lens model amplification maps and ALMA line image [3.4: "We found $\mu = 16.3 \pm 1.8$, lower than the factor $\mu = 22.0 \pm 1.3$ for CO(4–3)"]
  - software: Lenstool
- result: magnification HNC(5-4) = 16.3 ± 1.8 dimensionless [3.4: "We found $\mu = 16.3 \pm 1.8$"]
- limitation (authors): Strong parameter degeneracies in LVG models [4.2: "illustrates the strong parameter degeneracies that prevent us measuring the exact gas conditions"]
- not stated (card): CASA version; Cell size, image size, clean masks and thresholds; Line-free channels used for continuum; Flux scale uncertainty; Spatial template details and H2O correction details; CO fluxes and lens model files from earlier papers

### 2018Natur.553...51M: Galaxy growth in a massive halo in the first billion years of cosmic history (2018; high_z_galaxies; observational_alma_primary)
- question: What are the structure, physical conditions, masses and host halo rarity of the z=6.900 dusty galaxy SPT0311-58, resolved with high-resolution ALMA imaging?
- step 1: Lens modelling of continuum
  - method: Fit visibilities with visilens (Sersic source components, SIE lens, MCMC), then pixellated reconstruction with gradient regularization at 160 and 90 um; 110 um reconstructed with fixed deflections [Methods, Lens Modeling: "After determining the lens parameters using `visilens`, we used the best-fit values as initial input to a pixellated reconstruction code(cite: hezaveh16)."]
  - software: visilens, pixellated reconstruction code (proprietary)
  - parameter: Four Sersic components (1 E, 3 W) for visilens [Methods, Lens Modeling: "modeled with four Sérsic components, one for the SPT0311–58E and three for W."]
  - assumption: Lens is a singular isothermal ellipsoid [Methods, Lens Modeling: "the lens galaxy is modeled as a singular isothermal ellipsoid"]
  - fitting: MCMC sampling marginalizing over residual calibration uncertainty [Methods, Lens Modeling: "posterior parameter distributions are sampled using a Markov Chain Monte Carlo technique"]
  - validation: Lens parameters consistent to <10% between wavelengths; source properties agree to <15% between codes [Methods, Lens Modeling: "intrinsic source flux densities, sizes, and magnifications that agree to $<$15%"]
- step 2: Channelized [CII] lens modelling
  - method: Pixellated reconstruction of 39 channels of 40 km/s using 160 um lens deflections, regularization fit per channel [Methods, Lens Modeling: "using 39 consecutive channels of 40 km/s width, each with a peak signal-to-noise ranging from 9–34."]
  - software: pixellated reconstruction code (proprietary)
- step 3: Derive magnifications
  - method: Flux-weighted source-averaged magnifications from 90 um pixellated model [Methods, Lens Modeling: "We determine the source magnifications using the 90 $\mu\rm{m}$ pixellated model"]
- result: Magnification E / W / total = 1.3 / 2.2 / 2.0 ± not stated dimensionless [Methods, Lens Modeling: "$\mu_{\rm E} = 1.3$, $\mu_{\rm W} = 2.2$, $\mu_{\rm tot} = 2.0$"]
- result: Einstein radius = 0.29 ± not stated arcsec [Methods, Lens Modeling: "The lens model for this source indicates $\theta_{E}=0.29$$^{\prime\prime}$"]
- result: Source-plane separation of E and W = 8 ± not stated kpc [main text: "the two galaxies are separated by a projected (proper) distance of 8 kpc in the source plane"]
- limitation (authors): IRAC fluxes for W unreliable due to blending with lens; stellar mass of W unconstrained [Methods, Image de-blending: "we do not believe the *Spitzer*/IRAC fluxes to be reliable"]
- not stated (card): CASA version and calibration/imaging procedure (tclean parameters, weighting, robust, cell/image size, masks); Continuum-subtraction and line-free channels for [CII] and [OIII]; Self-calibration usage; Spectral setups for B6/B8 beyond LO frequencies; Pixellated lens code is proprietary; regularization and prior details not given; Aperture used to measure intrinsic flux densities; Lens model prior…

### 2015A&A...576L...2S: ALMA detection of [C ii] 158 μm emission from a strongly lensed z = 2.013 star-forming galaxy (2015; high_z_galaxies; observational_alma_primary)
- question: What are the ISM/PDR properties ([CII]/FIR and [CII]/CO ratios) of a typical, IR-faint lensed star-forming galaxy at z=2.013, compared with nearby and high-z galaxies?
- step 3: measure [CII] line flux and luminosity
  - method: Integrate primary-beam-corrected spectrum in box over 630.5-631.0 GHz; divide by magnification [2.1 ALMA observations and results: "The flux integrated in the range 630.5-631.0 GHz is S CII = 37.7 ± 3.7 Jy km s −1"]
  - parameter: µ = 49 ± 5 [2.1 ALMA observations and results: "We estimate an uncertainty of µ = 49 ± 5."]
  - assumption: Missing short-spacing flux negligible [2.1 ALMA observations and results: "Therefore, the flux lost due to missing short spacings should be small"]
- result: S_CII = 37.7 ± ± 3.7 Jy km/s [Table 1: "S CII b 37.7 ± 3.8 Jy km/s"]
- result: Intrinsic L_CII = 1.21e8 ± ± 0.12e8 (formal, excl. ~25% calibration) Lsun [Table 1: "(1.21 ± 0.12) × 10 [8] L ⊙"]
- result: [CII] frequency = 630.743 ± ± 0.015 GHz [Table 1: "ν CII 630.743 ± 0.015 GHz"]
- limitation (authors): Delivered data did not meet requested sensitivity; ~25% flux calibration uncertainty [2.1 ALMA observations and results: "Although the delivered data did not meet our requested sensitivity, it is sufficient to examine the average ISM/PDR properties"]
- not stated (card): CASA version and whether the pipeline or manual scripts were used; clean parameters (threshold, masks, niter, cell, image size, taper value); box coordinates for spectrum integration; continuum-subtraction/line-free channels; conversion from flux to luminosity formula; how the L_FIR range was obtained; flux scaling of J0423-013 values

### 2024A&A...692A.215C: Molecular gas budget of strongly magnified low-mass star-forming galaxies at cosmic noon (2024; high_z_galaxies; observational_alma_primary)
- question: What is the molecular gas content (CO and dust based) of strongly magnified low-mass star-forming galaxies at cosmic noon, and do they show a molecular gas deficit relative to scaling relations?
- step 3: Lens magnification
  - method: LENSTOOL models; mean magnification in aperture from 100 MCMC realizations; new PIEMD+shear model for J1429 [2.3.3: "we used the median of the 100 samples as the nominal value and we adopted $\sigma_{\mu}\equiv(p_{84} - p_{16})/2$ as the uncertainty"]
  - software: LENSTOOL
  - fitting: LENSTOOL MCMC, seven free parameters [2.3.3: "We then optimized the seven free parameters of the model using LENSTOOL’s Markov Chain Monte Carlo (MCMC) sampling."]
- step 6: Stacking
  - method: Single-pixel spectra and continuum stacked with 1/sigma^2 weights after magnification correction; significance threshold 1.5 sigma [3.5 Stacking: "we observed that the signal-to-noise ratio was optimized when galaxies were weighted by $1/\sigma^2$"]
- result: CO all arcs stack integrated flux = 1.3 ± 0.6 mJy km/s [Stacking table: "CO all arcs&1.3$\pm$0.6&-&2.68 &2.0$\pm$0.9 & 9.6,0.09 & 0.96,0.07"]
- result: Continuum B6/7 all arcs stack flux = 4.9 ± 0.9 microJy [Stacking table: "Continuum B6/7 all arcs&-& 4.9$\pm$0.9&2.96& 22$\pm$4 & 9.6, 0.1& 1.0,0.1"]
- limitation (authors): Scatter in r31 and r41 relations adds systematic errors [3.6.1: "both derived relations present significant scatter, which incorporates systematic errors into our molecular gas estimations."]
- not stated (card): Cell size and image size for cubes and MFS images; Line-free channels / continuum selection for MFS in bands 3-4; Exact apertures and regions for flux extraction; CIGALE module parameter grids (only on Zenodo); Velocity ranges collapsed for moment maps for each arc; Functional form and fit parameters of r31 and r41 vs Sigma_SFR; Which CASA version applies to which project; Flux calibrators and fl…

### 2018MNRAS.475.4939A: ALMA observations of lensed Herschel sources: testing the dark matter halo paradigm (2018; high_z_galaxies, cosmology; multi_facility_alma_minor)
- question: Can the standard dark-matter halo paradigm, with halo mass functions and density profiles from simulations including baryons, reproduce the observed distribution of image separations of Herschel-selected lensed submillimetre galaxies?
- step 1: Measure Einstein radii from ALMA images
  - method: Einstein radii measured directly from images; for arcs a circle was fitted to emission peaks >4 sigma with uniform weighting; checked against preliminary lens models [2 The Pilot Sample and the ALMA Observa…: "In cases where only an arc is visible (e.g HeLMS J001615.8+032435) a rough estimate of the Einstein radius was performed by fitting a circle to the peaks of the emission $( > 4\sigma)$."]
  - validation: Compared with preliminary lens models, agreement confirmed [2 The Pilot Sample and the ALMA Observa…: "The Einstein radii were measured directly from the images and subsequently compared with the respective values that arise from preliminary lensing models of these system, whereupon an agreement was confirmed."]
- step 2: Predict image-separation distributions
  - method: Strong-lens statistics: halo mass function times volume element times cross-section for mu>=2, normalised; EAGLE, SIS and SISSA profiles with NFW outside transition masses [3.4 Formalism of Strong Lens Statistics: "We adopt the standard formalism for computing lensing statistics (cite: TurnerOstrikerGott1984), where we consider a population of dark-matter halos that act as deflectors"]
  - parameter: minimum magnification mu_min = 2 [3.3 Cross-Section: "We calculated the cross section using a minimum magnification factor of $\mu_{min} = 2$."]
  - parameter: halo-to-stellar mass ratio 30 for SISSA; z_lv = z_l or 2.5 [3.1 The Halo Density Profiles: "adopt a constant ratio of halo to stellar mass of 30"]
  - assumption: Spherically symmetric lenses; flat LCDM with Omega_m=0.307, h=0.693 [3.3 Lensing Properties: "We always assume that the lens is spherically symmetric, since ellipticity does not significantly affect the statistics of image separations"]
- limitation (authors): Sample too small to distinguish density profiles; magnification bias not corrected [3.3 Magnification Bias: "we have decided not to do this because the luminosity function for submm sources is still very poorly constrained"]
- not stated (card): ALMA project codes and execution details; CASA/pipeline version; Imaging parameters (weighting, cell size, rms, beam); Einstein radius table values per source; Binning of observed image-separation histogram; Integration grids and numerical settings for the lens statistics code; Code for lens statistics not released

### 2013ApJ...767...88W: ALMA Redshifts of Millimeter-selected Galaxies from the SPT Survey: The Redshift Distribution of Dusty Star-forming Galaxies (2013; high_z_galaxies; observational_alma_primary)
- question: What is the redshift distribution of strongly lensed, mm-selected SPT dusty star-forming galaxies, measured through a blind ALMA 3 mm CO line survey, and how does lensing and selection bias affect it?
- step 3: Assess selection and lensing biases
  - method: Compare lensing probability and size-evolution scenarios for lensed vs unlensed dn/dz [4.2 Redshift biases due to gravitationa…: "we compare an assumed intrinsic redshift distribution to the model distribution of strongly lensed sources"]
  - assumption: Average magnification 15 [4.3 The redshift distribution: "Adopting an average magnification of $\bar \mu=15$ for the sources studied here"]
- limitation (authors): Eight ambiguous redshifts hamper determination of the distribution shape; small sample [4.3 The redshift distribution: "The determination of the shape of our redshift distribution is currently hampered by the eight ambiguous redshifts."]
- limitation (authors): Dust temperatures not physical; lensing size-evolution bias cannot be excluded [3.2 Ambiguous cases: "the “temperatures” should not be interpreted as physical temperatures"]
- not stated (card): CASA version and calibration/imaging task parameters (weighting, cleaning, masks); Line-free channels and continuum subtraction method; Line detection/integration procedure and SNR>5 criteria details; Gaussian line-fit procedure for redshift uncertainties; Calibrator names per session; Exact probability calculation for dust temperature/redshift options; Intrinsic dn/dz and size-evolution lensing …

## All papers in this technique

- 2013ApJ...767...88W (2013): ALMA Redshifts of Millimeter-selected Galaxies from the SPT Survey: The Redshift Distribution of Dusty Star-forming Galaxies
- 2013ApJ...767..132H (2013): ALMA Observations of SPT-discovered, Strongly Lensed, Dusty, Star-forming Galaxies
- 2014A&A...568A..92M (2014): Herschel-ATLAS and ALMA. HATLAS J142935.3-002836, a lensed major merger at redshift 1.027
- 2015A&A...576L...2S (2015): ALMA detection of [C ii] 158 μm emission from a strongly lensed z = 2.013 star-forming galaxy
- 2015ApJ...806L..17S (2015): ALMA Resolves the Properties of Star-forming Regions in a Dense Gas Disk at z ∼ 3
- 2015ApJ...811..115W (2015): The Innermost Mass Distribution of the Gravitational Lens SDP.81 from ALMA Observations
- 2015ApJ...811..124S (2015): Sub-kiloparsec Imaging of Cool Molecular Gas in Two Strongly Lensed Dusty, Star-forming Galaxies
- 2015ApJ...812...88M (2015): Stellar Masses and Star Formation Rates of Lensed, Dusty, Star-forming Galaxies from the SPT Survey
- 2015MNRAS.451L..40R (2015): ALMA imaging of SDP.81 - I. A pixelated reconstruction of the far-infrared continuum emission.
- 2015PASJ...67...72T (2015): High-resolution ALMA observations of SDP.81. I. The innermost mass profile of the lensing elliptical galaxy probed by 30 milli-arcsecond im…
- 2016A&A...586L...7B (2016): An ALMA view of the interstellar medium of the z = 4.77 lensed starburst SPT-S J213242-5802.9
- 2016A&A...593L...2N (2016): Planck's Dusty GEMS. II. Extended [CII] emission and absorption in the Garnet at z = 3.4 seen with ALMA
- 2016A&A...596A..75S (2016): Characterizing elusive, faint dusty star-forming galaxies: a lensed, optically undetected ALMA galaxy at z 3.3
- 2016ApJ...822...80S (2016): The Redshift Distribution of Dusty Star-forming Galaxies from the SPT Survey
- 2016ApJ...826..112S (2016): ALMA Imaging and Gravitational Lens Models of South Pole Telescope—Selected Dusty, Star-Forming Galaxies at High Redshifts
- 2016MNRAS.457.2936I (2016): ALMA imprint of intergalactic dark structures in the gravitational lens SDP.81
- 2016MNRAS.461..164I (2016): On the origin of the flux ratio anomaly in quadruple lens systems
- 2017A&A...597A..41G (2017): The ALMA Frontier Fields Survey. I. 1.1 mm continuum detections in Abell 2744, MACS J0416.1-2403 and MACS J1149.5+2223
- 2017A&A...600L...3C (2017): Planck's dusty GEMS. III. A massive lensing galaxy with a bottom-heavy stellar initial mass function at z = 1.5
- 2017ApJ...843L..35W (2017): ALMA Observations of the Gravitational Lens SDP.9
- 2017MNRAS.466..138K (2017): A merger in the dusty, z = 7.5 galaxy A1689-zD1?
- 2017MNRAS.466.2825B (2017): ALMA observations of atomic carbon in z ∼ 4 dusty star-forming galaxies
- 2018A&A...610A..53M (2018): Chandra and ALMA observations of the nuclear activity in two strongly lensed star-forming galaxies
- 2018A&A...613A..34P (2018): ALMA view of RX J1131-1231: Sub-kpc CO (2-1) mapping of a molecular disk in a lensed star-forming quasar host galaxy
- 2018A&A...620A.115B (2018): Dense-gas tracers and carbon isotopes in five 2.5 &lt; z &lt; 4 lensed dusty star-forming galaxies from the SPT SMG sample
- 2018ApJ...860...87F (2018): The Discovery of a New Massive Molecular Gas Component Associated with the Submillimeter Galaxy SMM J02399-0136
- 2018ApJ...862...64S (2018): Deciphering the Activity and Quiescence of High-redshift Cluster Environments: ALMA Observations of Cl J1449+0856 at z = 2
- 2018ApJ...864...60M (2018): SOFIA/HAWC+ Detection of a Gravitationally Lensed Starburst Galaxy at z = 1.03
- 2018ApJ...866L..12G (2018): A Magnified View of Circumnuclear Star Formation and Feedback around an Active Galactic Nucleus at z = 2.6
- 2018ApJ...867..140L (2018): Resolving Star Formation on Subkiloparsec Scales in the High-redshift Galaxy SDP.11 Using Gravitational Lensing
- 2018MNRAS.475.4939A (2018): ALMA observations of lensed Herschel sources: testing the dark matter halo paradigm
- 2018Natur.553...51M (2018): Galaxy growth in a massive halo in the first billion years of cosmic history
- 2018Sci...361.1016S (2018): Fast molecular outflow from a dusty star-forming galaxy in the early Universe
- 2019A&A...624A.138Y (2019): CO, H<SUB>2</SUB>O, H<SUB>2</SUB>O<SUP>+</SUP> line and dust emission in a z = 3.63 strongly lensed starburst merger at sub-kiloparsec scal…
- 2019A&A...628A..23A (2019): Imaging the molecular interstellar medium in a gravitationally lensed star-forming galaxy at z = 5.7
- 2019A&A...631A..91G (2019): Towards sub-kpc scale kinematics of molecular and ionized gas of star-forming galaxies at z ∼ 1
- 2019A&A...632L...7J (2019): Detection of a high-redshift molecular outflow in a primeval hyperstarburst galaxy
- 2019ApJ...870...80L (2019): Spatially Resolved [C II] Emission in SPT0346-52: A Hyper-starburst Galaxy Merger at z ∼ 5.7
- 2019ApJ...873...50D (2019): Source Structure and Molecular Gas Properties from High-resolution CO Imaging of SPT-selected Dusty Star-forming Galaxies
- 2019MNRAS.486.2366M (2019): The molecular gas properties in the gravitationally lensed merger HATLAS J142935.3-002836
- 2020A&A...633A.160C (2020): The ALMA Frontier Fields Survey. V. ALMA Stacking of Lyman-Break Galaxies in Abell 2744, Abell 370, Abell S1063, MACSJ0416.1-2403 and MACSJ…
- 2020A&A...634L...3Y (2020): First detection of the 448 GHz ortho-H<SUB>2</SUB>O line at high redshift: probing the structure of a starburst nucleus at z = 3.63
- 2020A&A...641L...2M (2020): All good things come in threes: the third image of the lensed quasar PKS 1830-211
- 2020ApJ...891...64F (2020): Truth or Delusion? A Possible Gravitational Lensing Interpretation of the Ultraluminous Quasar SDSS J010013.02+280225.8 at z = 6.30
- 2020ApJ...892L..18I (2020): ALMA 50-parsec-resolution Imaging of Jet-ISM Interaction in the Lensed Quasar MG J0414+0534
- 2020ApJ...902...78R (2020): The Complete Redshift Distribution of Dusty Star-forming Galaxies from the SPT-SZ Survey
- 2020ApJ...905...85S (2020): Ubiquitous Molecular Outflows in z &gt; 4 Massive, Dusty Galaxies. I. Sample Overview and Clumpy Structure in Molecular Outflows on 500 pc …
- 2020ApJ...905..152D (2020): [N II] Fine-structure Emission at 122 and 205 μm in a Galaxy at z = 2.6: A Globally Dense Star-forming Interstellar Medium
- 2021A&A...645A..45C (2021): Planck's Dusty GEMS. VIII. Dense-gas reservoirs in the most active dusty starbursts at z ∼ 3
- 2023Natur.621..483G (2023): Polarized thermal emission from dust in a galaxy at redshift 2.6
- 2024A&A...684A..56K (2024): Probing the interstellar medium of the quasar BRI 0952‒0115. An analysis of [C II], [C II], CO, OH, and H<SUB>2</SUB>O
- 2024A&A...685A..80Z (2024): Unveiling [C II] clumps in a lensed star-forming galaxy at z ∼ 3.4
- 2024A&A...692A.215C (2024): Molecular gas budget of strongly magnified low-mass star-forming galaxies at cosmic noon
- 2024ApJ...967...11C (2024): TEMPLATES: Characterization of a Merger in the Dusty Lensing SPT0418─47 System
- 2025ApJ...990...29H (2025): Compact Ionized Gas Region Surrounded by Porous Neutral Gas in a Dusty Lyman Break Galaxy at Redshift z = 8.312
- 2025ApJ...991...53C (2025): HerS-3: An Exceptional Einstein Cross Reveals a Massive Dark Matter Halo
- 2025ApJ...995..219F (2025): PASSAGES: The Discovery of a Strongly Lensed Protocluster Core Candidate at Cosmic Noon
- 2025ApJS..278...45F (2025): DUALZ—Deep UNCOVER-ALMA Legacy High-Z Survey
- 2025NatAs...9.1553F (2025): Primordial rotating disk composed of at least 15 dense star-forming clumps at cosmic dawn
- 2026A&A...705A..81K (2026): Resolving the molecular gas emission of the z ∼ 2.5─2.8 starburst galaxies SPT 0125-47 and SPT 2134-50
- 2026ApJ..1002L..28Y (2026): A Close Quasar Pair in a Massive Galaxy Merger at z = 5.7
