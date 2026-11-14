---
name: alma-disk-substructure-profiles
description: "Measure deprojected radial intensity profiles of protoplanetary, protostellar and debris disks from ALMA data, and locate and characterise rings, gaps, cavities, spirals and azimuthal asymmetries (location, width, depth, contrast, dust radius, spectral index, optical depth, trapping and planet-mass inferences). Use when a task asks for a disk radial profile, ring or gap positions and widths, a parametric or non-parametric (frank, rave) fit of an axisymmetric disk, a substructure census, or planet masses from gaps. Built from 434 on-topic ALMA disk papers (2012-2026)."
---

# Disk radial profiles, rings and gaps

Turns a continuum (or line) dataset of a disk into a deprojected radial profile I(r), then into ring and gap
locations, widths, depths and physical inferences. Two mistakes matter most: (1) reading substructure off a
beam-convolved image profile when the feature is near or below the beam (fit the visibilities, and report a
width or depth as a limit when the data do not constrain it); (2) quoting formal MCMC or frank errors as if they
included geometry, functional-form choice, primary-beam and flux calibration, which authors repeatedly admit
they do not.

Evidence base: the `disk-substructure-profiles` pack (584 regex-tagged papers). A title screen marks 150 as
off-topic (galaxies, cores, clumps, filaments, outflows and jets, hot cores, masers, HII regions; list in
`references/parameters.md`), leaving 434. "Pack" counts are pack aggregates (per matched analysis step, all 584
papers, off-topic included). "Pack lines" counts are my count of distinct on-topic papers in the pack's
key-parameter, assumption and excerpt lines (lower bounds). Settings for 15 papers come from the earlier
266-paper pack; those papers are still in this pack's list (named in `references/parameters.md`). "(card)" means
a verbatim quote in that paper's card, not in the pack.

## When to use

- Continuum images or visibilities of a protoplanetary or protostellar (Class 0/I) disk where rings, gaps,
  cavities, shoulders or inner disks are visible or suspected (2018ApJ...869...17L, 2020ApJ...902..141S,
  2024PASJ...76..437Y).
- Debris belts: belt radius, width, edges, gaps inside broad belts, eccentricity from the star-belt offset or
  the outer-edge slope (2015ApJ...798..124R, 2019AJ....158..162F, 2026A&A...705A.196H).
- Line emission rings and gas gaps from deprojected, azimuthally averaged moment-0 maps or stacked spectra
  (2015ApJ...810..112O, 2019ApJ...880...69Y, 2020A&A...644A.119P).
- Multi-band comparisons of the same rings: widths and positions per band, radial spectral index, optical
  depth, radially resolved T_d, Sigma_d and a_max (2020ApJ...891...48H, 2021A&A...648A..33M, 2025MNRAS.538.2358S).
- Turning measured gaps and rings into dust-trapping or planet-mass statements (2018ApJ...869...17L,
  2024ApJ...976..132H, 2025A&A...697A..64V).

## When not to use

| Situation | Use instead |
|---|---|
| Galaxy disks, nuclear rings, tilted-ring rotation curves, spiral-arm masks in galaxies | `alma-galaxy-3d-kinematics`, `alma-star-formation-laws` |
| Prestellar or protostellar cores, filaments, cluster-forming clumps (envelope density profiles) | `alma-core-extraction-cmf` |
| Gas kinematics: Keplerian masks, dynamical masses, velocity deviations from planets | `alma-keplerian-disk-kinematics` |
| Generic visibility fitting machinery (likelihood, weights, samplers) | `alma-uv-plane-fitting` (this skill covers the disk-profile specifics) |
| Total dust mass only, no radial structure | `alma-dust-continuum-mass` |
| Spectral index maps without a radial-structure question | `alma-spectral-index` |
| Full physical disk models (thermochemistry, RT, hydro) | `alma-radiative-transfer-modelling`, `alma-hydro-simulation-comparison` |
| Edge-on, vertically extended or warped emission where a thin-disk deprojection fails | forward modelling of the 3D structure (step 3) or an edge-on non-parametric fit (rave edge-on version, 2026A&A...705A.196H) |

## Steps

1. **Prepare and image for inspection, not for measurement.** Goal: see the structure and pick a model family.
   - Multi-execution data: align phase centres (`fixvis`, Gaia proper motions), rescale flux with `gencal` from
     overlapping deprojected visibilities below 800 klambda, correct offsets > 1/3 beam (2021A&A...648A..33M).
   - CASA `tclean`, `mfs`, `nterms=1`, multiscale, robust -0.5 to 0.5, to about 5 sigma (2025A&A...697A..64V);
     robust 0.5, scales [0, 1, 3] x beam, 1-3 self-cal rounds set by S/N (2024PASJ...76..437Y); compare several
     robust values plus superuniform and drop features that could be artefacts (2020ApJ...902..141S).
   - Sparse-modelling (SpM) super-resolution gained 2-3x resolution in 18 of 43 disks but makes artificial
     clumps near bright inner disks; use it for azimuthal averages only (2024PASJ...76..437Y).
2. **Fix the geometry (centre, inclination i, PA).** Routes in the pack:
   - CASA `imfit` 2D Gaussian (2018ApJ...869...17L), used to initialise the uv fit (2018A&A...616A..88V); an
     ellipse fit to an outer ring or an elliptical Gaussian to the centre (2024PASJ...76..437Y).
   - Ellipse fit to ring peaks along cuts every 10 deg (2013ApJ...777L..25M) or 1 deg (2024ApJ...961..228S);
     DSHARP fit a 5-parameter ellipse with emcee to each ring and gap (2018ApJ...869L..42H).
   - Free geometry in the visibility fit, e.g. uniform +-20 deg on i and PA, +-0.5 arcsec offsets
     (2018ApJ...869...17L), or Gaussian priors (2020ApJ...891...48H). Eccentric debris ring: a constant-surface-
     density ring fitted in visibility space with emcee, e = projected star-ring offset / projected semimajor
     axis; HST ellipse fits were only a cross-check (2019AJ....158..162F).
   - Or fix i and PA from earlier work or from one band (2015ApJ...810..112O, 2024ApJ...974..306S).
3. **Deprojected image-plane profile.** Goal: a first I(r) and an azimuthal check. Method (general practice,
   valid only for a geometrically thin, roughly planar disk at low to moderate inclination): rotate by PA,
   stretch the minor-axis coordinate by 1/cos i, average in annuli. Near edge-on, vertically extended or
   warped emission this breaks down: edge-on debris disks were forward-modelled (2015A&A...581A..97S;
   2016ApJ...823..108B, edge-on wedge), ellipse averaging fails for edge-on discs (2026A&A...705A.196H), and
   axisymmetry plus moderate resolution limited line emission surfaces (2021A&A...645A.145G).
   - Inclined disks: average near the major axis only (20-40 deg from it for i >= 60 deg, 2024PASJ...76..437Y;
     within 20 deg, 2021MNRAS.501.2934C) or mask minor-axis sectors where the deprojected beam is >= 30% of the
     beam major axis (2026A&A...705A.196H).
   - Bins: a quarter of the beam major axis (2021AJ....162...99F) or 1 au (2020ApJ...891...48H); more in the
     table. 2019ApJ...880...69Y used 0.05 arcsec bins with the innermost bin at a radius of one beam (0.1 arcsec).
   - Bins narrower than the beam are correlated: divide the scatter by sqrt(number of independent beams in the
     annulus) (2021AJ....162...99F, 2024PASJ...76..437Y, 2026A&A...705A.196H) or use
     rms / sqrt(Omega_ring / Omega_beam) (2019ApJ...883...71C), and keep the bin covariance in later fits. For
     lines, average the unclipped moment-0 map (2015ApJ...810..112O, 2020A&A...644A.119P).
4. **Fit the visibilities (the measurement).** Goal: resolution-limited structure without deconvolution bias.
   - Parametric: central Gaussian or tapered power law plus Gaussian rings (2018ApJ...869...17L,
     2020ApJ...898...36L); delta plus Gaussian rings, 21 parameters (2020ApJ...891...48H); Gaussian x cosine,
     up to 13 parameters (2018A&A...616A..88V); Nuker (2024ApJ...966...59S); power laws, error functions and
     Gaussians with Gaussian gaps for debris belts (2015ApJ...798..124R, 2026A&A...705A.196H). Model
     visibilities with galario (pack 44) or vis_sample (pack 14); sample with emcee (pack 113), pymc
     (2018A&A...616A..88V), dynesty (2020ApJ...902..141S) or SVI in pyro (2024ApJ...976..132H). SVI is
     approximate (that paper's posterior is a multivariate normal, as it says): check for missed modes and
     non-Gaussian posteriors by rerunning from several starts or against a short MCMC run.
   - Convergence: steps > 100 autocorrelation times with the estimate stable to 1%, burn-in 2 tau, thinning
     tau/2 (2024A&A...689L...5M); walkers = 8 x the number of parameters (2024A&A...688A.149D).
   - frank (pack 18 + 13 as "frankenstein"; 11 on-topic papers give hyperparameters): a Fourier-Bessel fit to
     the real visibilities with a Gaussian-process prior, often in log brightness (2024ApJ...974..306S). It
     assumes a thin axisymmetric disk and has no primary-beam correction (2026A&A...705A.196H,
     2020MNRAS.498.1319M). Choose hyperparameters so the profile has no oscillatory artefacts and the
     reconstructed power spectrum matches the data without over-fitting sparse long baselines
     (2026A&A...705A.196H); too small a w_smooth gave artificial ripples (2025NatAs...9.1176R).
   - rave: concentric annuli fitted to the CLEAN image, errors from 100 Monte Carlo annulus partitions, an
     edge-on version for inclined discs, N annuli = largest without oscillations (2026A&A...705A.196H).
   - Add components only when residuals demand it: a ring or tapered power law when symmetric residuals exceed
     about 5-10 sigma (2018ApJ...869...17L); compare models with Bayes factors (2020ApJ...902..141S), BIC
     (2024ApJ...976..132H, 2025ApJ...986L..11S) or AIC (2024A&A...689L...5M).
   - Check that visibility weights match the data scatter before fitting; rescale only when that check fails.
     Corrections are dataset specific: `statwt` (2024A&A...686A.206Y); f = scatter^-2 / mean weight, 0.1-0.3
     (2024PASJ...76..437Y); x about 0.25 (2020ApJ...902..141S); /2.667 (2020ApJ...891...48H); f "typically about
     2", direction not defined in the pack (2024ApJ...976..132H). Inflating image-profile errors is a different
     correction (x sqrt(70), 2018ApJ...869L..46D). State which quantity you rescaled and in which direction.
   - Image-plane fits (mostly debris belts) must pass the model through the instrument: primary-beam
     attenuation, then synthesized-beam convolution before comparing with the dirty image
     (2017MNRAS.466.4201W), or primary beam then sampling at the observed uv points (2015ApJ...798..124R).
     Papers used chi2 over dirty-beam-convolved pixels (2020MNRAS.497.2811K) with sigma scaled by sqrt(beam
     area in pixels) for correlated noise (2016MNRAS.460L..10B, 2017AJ....154..225S).
5. **Extract substructure metrics from the best-fit (or posterior) profile.**
   - Ring = local maximum, gap = local minimum, shoulder = three consecutive inflection points, over 2000
     posterior profiles (2024ApJ...976..132H); or use D(r) = (1/I) dI/dr, inflections at D'' = 0 (Kneed), gap
     depth = I(r_ring)/I(r_gap), with unresolved-gap depths kept as limits (2024PASJ...76..437Y).
   - Gap location at the local minimum, width as full width at half depth, contrast = ring peak / gap, errors
     from 100 chain samples (2018ApJ...869...17L); DSHARP's empirical widths and depths use no functional form
     (2018ApJ...869L..42H, card). Ring width = fitted Gaussian sigma (2024ApJ...976..132H, 2020ApJ...898...36L).
   - Debris rings: peak radius, 25/50/75%-of-peak radii per edge, FWHM from the 50% radii, edge width 25-75%,
     gap minimum as the baseline next to a gap (2026A&A...705A.196H).
   - Sizes: R95 by curve of growth (2018ApJ...869L..42H, card; 2024PASJ...76..437Y), R_eff at 90%
     (2018ApJ...869...17L), R68/R95/R99 (2024A&A...689A.104D).
6. **Asymmetries and non-axisymmetric structure.** Use polar (r, theta) deprojected maps; DSHARP sampled spiral
   peaks every 6-18 deg in azimuth depending on radius (2018ApJ...869L..43H). Fit arcs and vortices with an
   explicit model: a steady-state vortex prescription (2018ApJ...869L..50P), or a uniform disk plus ring with
   azimuthal modulation plus crescent, overlaid with an analytic planet-driven spiral (2017ApJ...848L..11K).
   Compare the two disk halves by subtracting their radial profiles (2020MNRAS.498.1319M). Unsharp masking
   (60 mas, 2020A&A...644A.119P; 66 mas FWHM with weight 0.95, 2018ApJ...869L..44K) reveals faint rings and
   spirals but its authors call it arbitrary (2020A&A...644A.119P). Test azimuthal variation against the noise
   and against identical ellipses on emission-free sky (2013ApJ...777L..25M).
7. **Multi-wavelength and physical conversion.**
   - Spectral index: smooth to a common beam (CASA `imsmooth`, 2020ApJ...891...48H), re-image both bands with a
     common beam and uv range, masking S/N < 2.5 (2018A&A...616A..88V), or image jointly with `mtmfs`,
     `nterms=2` (2021A&A...648A..33M). alpha = log(I1/I2)/log(nu1/nu2), ratios in the same order
     (2020ApJ...891...48H); the pack line for 2016Natur.535..258C inverts the frequency ratio, which flips the
     sign: do not copy that form. Carry the absolute flux error per band, 10% (2020ApJ...891...48H) or 10% in
     Band 7 and 5% in Bands 3-6 (2021A&A...648A..33M); close bands amplify it (0.42 on alpha,
     2018A&A...616A..88V; 0.083 for Bands 3 and 7, 2024ApJ...974L..25D).
   - Optical depth (as in 2019ApJ...880...69Y): tau_d = -ln(1 - I / (B(T_d) - B(T_bg))), with T_bg = 2.73 K
     and T_d from a disk temperature model. Dropping B(T_bg) is an approximation that only holds when
     B(T_d) >> B(T_bg). Requirements (general practice): I and B in the same specific-intensity units (for
     example Jy/sr, not Jy/beam); the argument 1 - I/(B(T_d) - B(T_bg)) must be positive (if I approaches
     B(T_d), report the ring as optically thick and tau as a lower limit); the formula assumes the emission
     fills the beam and neglects scattering, so beam dilution of a narrow ring biases tau low. T_d is often
     a passive flared disk (flaring angle 0.02 in 2018ApJ...869L..42H, card, 2024ApJ...971..129C,
     2024PASJ...76..437Y and 2025ApJ...993..166J; 0.05 in 2018ApJ...869...17L); DSHARP warned their optical
     depths may be off by up to a factor of two (2018ApJ...869L..42H, card). Use the full Planck function, not
     Rayleigh-Jeans, for brightness temperatures (2025MNRAS.538.2358S, 2024A&A...689L...5M).
   - Ring dust mass, optically thin: M = F d^2 / (kappa B(T)), typically kappa 2-2.3 cm2/g at 1.3 mm and
     T = 20 K (2020A&A...644A.119P, 2021MNRAS.501.2934C); a lower limit if the ring is optically thick. One
     paper tried 20, 14.7 and about 30 K to show the temperature dependence (2021A&A...649A.122P).
   - Radially resolved multi-band fits of T_d, Sigma_d and a_max per radius: emcee (24 walkers, 10,000 steps,
     sampled every 1/3 resolution element, 2025MNRAS.538.2358S) or a grid (2023ApJ...948..110Y). The
     temperature posterior can be mostly prior and a_max poorly bounded (2021A&A...648A..33M).
   - Grain sizes: two-band spectral index or optical depth alone does not give a unique grain size: temperature,
     flux calibration and degeneracies prevent it (2020ApJ...891...48H), and two bands constrain four
     parameters only through priors, porosity unconstrained (2024ApJ...971..129C). Report priors and T.
8. **Interpretation.**
   - Dust trapping: compare ring width w_d with the pressure scale height h_p; w_d < h_p argues for trapping
     (2024ApJ...976..132H, 2024ApJ...971..129C). For alpha_r/St = [(w_g/w_d)^2 - 1]^-1 (2025A&A...697A..64V):
     w_d is the Gaussian width of the model dust surface-density ring (not the width of the beam-convolved
     brightness profile); w_g is not measured, so bound it between w_g,min = H_g (gas scale height from the
     temperature) and w_g,max = distance from the ring peak to the deepest point of the gap inside it; the
     relation needs w_g > w_d and assumes the ring is a pressure maximum and the grains are fragmentation
     limited.
   - Ring thickness: near-far and azimuthal asymmetries of self-scattering polarization (Q' after rotating
     Stokes maps by PA) constrained H/R per ring in HL Tau (about 0.1 in the first ring, below about 0.05 outside 30 au;
     2025ApJ...989L..43Y).
   - Planet masses from gap geometry: the Hill radius (general practice) is R_Hill = a (M_p / 3 M_star)^(1/3),
     with a = the planet's orbital radius, taken as the gap centre. 2018ApJ...869...17L "simply assume[d] that
     the gap radius corresponds to 4 R_Hill" (citing Dodson-Robinson 2011); the pack does not say whether
     "gap radius" there means a gap width or half-width, so state the size observable you use (for example the
     measured gap width) and never put the gap's orbital radius into the Hill-radius relation in its place.
     Other papers state it: gap width (ring peak minus gap minimum) = k R_Hill with k = 4.5-8
     (2024A&A...682A..55M), 4.5-7 for dust gaps (2023ApJ...948..110Y), 5 R_Hill (2016A&A...586A..99H). The
     Rosotti et al. 2016 diagnostic is the normalized gap-ring distance (typically 0.2-0.3; 0.25 gave about 15
     Earth masses for alpha = 1e-4) (2018ApJ...869...17L). Zhang et al. 2018 width relations with alpha = 1e-3,
     h/r 0.05 and s_max 0.1 mm (2021ApJ...923..121Y, which lists the constants; 2024PASJ...76..437Y;
     2024ApJ...976..132H). For debris gaps, the chaotic-zone width w_g = 3 a_p mu^(2/7) (2020MNRAS.498.1319M,
     2026A&A...705A.196H, 2015ApJ...798..124R). Always state alpha, h/r and the one-planet-per-gap assumption.
   - Gas gaps and the Kanagawa depth relation (as in 2019ApJ...880...69Y): apply it to gas surface density,
     not to line brightness or continuum contrast. That paper first derived HCO+ column density and
     excitation temperature per radial bin from the (3-2)/(1-0) ratio with line optical depth, then assumed
     a constant HCO+ abundance between 17 and 37 au to turn column density into a gas depletion, and defined
     the depth as the unperturbed column density (a power law interpolated from 17 and 37 au) divided by the
     gap value, giving 4-8. (The pack's own wording reads as gap over interpolation; only the reciprocal gives
     a depth above 1.) The Kanagawa formula assumes a vertically isothermal disk; inputs were M_star 2.1 Msun,
     T 60 K, alpha 1e-3. The innermost-bin line widths were overestimated, so inner column densities, Tex and
     tau may be underestimated. A dust gap is not a gas gap: report continuum contrast and gas depletion
     separately.
   - Snowlines: compare gap radii with midplane temperatures of N2 12-15 K, CO 23-28 K, clathrate 41-46 K
     (2018ApJ...869...17L).

## Parameter defaults and ranges

Rows marked "example" are settings from one or a few papers, not an established default. Choose MCMC run length
from convergence diagnostics (autocorrelation time) and priors from the target and model, not from this table.

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| Radial profile form (uv fit) | Gaussian rings + central Gaussian or tapered power law | Gaussian x cosine, Nuker, delta + Gaussians, power laws with Gaussian gaps | pack lines (no recount) | 2018ApJ...869...17L, 2020ApJ...891...48H, 2018A&A...616A..88V, 2026A&A...705A.196H |
| emcee walkers | 100 | 16 to 1024 | 33 report walkers; 9 use exactly 100, 1 "about 100"; 120 and 200 in 4 each (pack lines) | 100: 2018ApJ...869...17L, 2020ApJ...898...36L, 2019ApJ...877L..32M, 2021ApJ...909..212K; extremes: 2024ApJ...974L..25D (16), 2019ApJ...881...84S (1024) |
| emcee steps / burn-in | example: 5000 steps, about 2000 burn-in, keep the last 1000 (2018ApJ...869...17L) | 500 to 300,000 steps | pack lines (no consensus) | 2018ApJ...869...17L, 2020ApJ...891...48H, 2024A&A...689A.104D, 2024A&A...689L...5M |
| Geometry priors | example: uniform +-20 deg (i, PA), +-0.5 arcsec offsets (2018ApJ...869...17L) | Gaussian priors from image fits; fixed from literature or one band | pack lines (study specific) | 2018ApJ...869...17L, 2020ApJ...891...48H, 2024ApJ...974..306S |
| Ring parameter priors | example: ring centre +-0.05 arcsec around the visual ring | r_peak 10-80 au, sigma 1-50 au | 2 (study specific) | 2020ApJ...898...36L, 2019ApJ...878...16P |
| frank alpha | 1.3 | 1.01-1.3 | 11 (pack lines, both packs); 1.3 in 5, 1.2 in 3, 1.05 in 2, 1.01 in 1, one grid (one paper used two values) | 2024A&A...689A.104D, 2025MNRAS.538.2358S, 2024A&A...682A..55M, 2020MNRAS.498.1319M |
| frank w_smooth | no consensus; 1e-2 most frequent (4) | 1e-4 to 1e-1 | 10 (pack lines, both packs) | 2020MNRAS.498.1319M, 2025NatAs...9.1176R, 2024ApJ...971..129C, 2024MNRAS.532.1752R |
| frank N / Rmax | 300-400 points; Rmax a few arcsec | Rmax 2-5 arcsec, 400 au or 4 R_out | 6 | 2024ApJ...971..129C, 2024A&A...682A..55M, 2020MNRAS.498.1319M, 2025ApJ...986L..11S |
| Visibility binning (plots, grid fits, model uv grid) | 10 klambda | 7-30 klambda | 7 (pack lines, both packs) | 2014ApJ...791L...6W, 2018A&A...616A..88V, 2024ApJ...974..306S, 2021ApJ...909..212K (10-20), 2013ApJ...777L..25M (7), 2018A&A...610A..24F (30) |
| Image-profile bin width | a quarter of the beam major axis, or 1 au | 0.5-10 au, 0.05-0.15 arcsec | 12 (pack lines, both packs) | 2021AJ....162...99F, 2020ApJ...891...48H, 2015ApJ...806L...7Z, 2019ApJ...880...69Y |
| Weight or error rescaling | only when a check shows weights or errors are off; dataset specific | statwt; visibility weights x0.1-0.3, x0.25 or /2.667; f about 2 (direction not given); profile errors x sqrt(70) | 6 | 2024PASJ...76..437Y, 2024A&A...686A.206Y, 2020ApJ...902..141S, 2020ApJ...891...48H, 2018ApJ...869L..46D |
| Flux calibration error (absolute) | 10% per band | 5% (Bands 3-6) to 10% (Band 7); separately, DSHARP relative flux scales agreed within 5% (not an absolute error) | 5 (pack lines) | 2020ApJ...891...48H, 2018A&A...616A..88V, 2021A&A...648A..33M, 2024ApJ...974L..25D; relative: 2018ApJ...869L..41A |
| Dust opacity at 1.3 mm (mass) | 2.3 cm2/g, often as 2.3 (nu/230 GHz)^0.4 | 0.43 (DSHARP absorption) to 2.3 | 2.3 in 6 (pack lines) | 2021A&A...656A.150P, 2021MNRAS.501.2934C, 2024ApJ...961..228S (2.0), 2024PASJ...76..437Y (0.43) |
| Dust temperature (mass estimates) | 20 K | about 10 K (debris belt) to 80 K (inner ring of HD 100546), or passive-disk T(r) | 20 K in 7 (pack lines) | 20 K: 2024ApJ...961..228S, 2021MNRAS.501.2934C, 2024A&A...682A..55M; 10 K: 2017ApJ...850L...6A; 40/60/80 K: 2014ApJ...791L...6W; T(r): 2024ApJ...971..129C |
| Turbulence alpha (interpretation) | 1e-3 | 1e-4 to 1e-2 | pack lines | 2024ApJ...976..132H, 2021ApJ...923..121Y, 2019ApJ...880...69Y, 2018ApJ...869...17L |

More settings by paper (samplers, frank runs, profile extraction, debris belt models, thermal assumptions) are
in `references/parameters.md`.

## Software

Counts are the pack aggregate "Software named in the matched steps" (per matched step, all 584 papers, off-topic
ones included; names lower-cased in the pack). I did not recount per paper.

| Software | Used for | Pack count |
|---|---|---|
| casa (tclean, imfit, imsmooth, gencal, statwt, simobserve, uvmodelfit) | imaging, geometry, flux alignment, weights, mock observations | 127, plus task-named entries (tclean 17 + 4, imfit 7 + 4, simobserve 7, uvmodelfit 5, clean 3, fixvis 3) |
| emcee | posterior sampling for profile, ring, belt and ellipse fits | 113 |
| gofish | stacked line spectra and radial profiles of gas | 45 |
| galario | model visibilities from a radial profile or model image | 44 |
| radmc-3d | physical and RT disk models compared with profiles | 40 |
| frank / frankenstein | non-parametric 1D visibility fit | 18 + 13 |
| dali, lime, mcfost, prodimo | thermochemical, line and dust RT models of rings | 26, 13, 13, 3 |
| vis_sample | model visibilities | 14 |
| bettermoments | moment maps for line profiles | 12 |
| miriad, gildas | imaging and uv modelling in older papers | 9, 7 |
| eddy | disk geometry and surfaces from lines | 7 |
| rave | non-parametric belt profiles in the image plane (2026A&A...705A.196H) | 5 |
| uvmultifit, uvplot, pymc | alternative uv fitting, binned-visibility plots, MCMC | 5, 4, 3 |
| optool | dust opacities | 4 |
| fargo | hydrodynamic planet-gap models | 3 |
| dynesty, pyro, Kneed, linmix, dustpy | nested sampling (2020ApJ...902..141S), SVI (2024ApJ...976..132H), inflection points and regressions (2024PASJ...76..437Y), dust evolution (2025MNRAS.538.2358S) | named in excerpts or pack lines only |

## Pitfalls

- **Formal errors are too small.** Authors say fit errors are likely underestimated (2018ApJ...869...17L), frank
  uncertainties likewise (2026A&A...705A.196H), and ring uncertainties depend on the chosen functional form
  (2020ApJ...898...36L). Calibration uncertainty is often left out of the MCMC (2020ApJ...892...99C). SVI
  posteriors are a multivariate-normal approximation (2024ApJ...976..132H).
- **frank has no primary-beam correction** and assumes a thin, axisymmetric disk; this can bias large discs
  (2026A&A...705A.196H, 2020MNRAS.498.1319M). Over-small w_smooth adds ripples (2025NatAs...9.1176R).
- **Widths and depths are poorly constrained near the beam.** 13 of 33 gaps in a 43-disk survey were not fully
  resolved and their depths were kept as limits (2024PASJ...76..437Y); gap and ring widths are hard to constrain
  (2018A&A...616A..88V); a two-ring model and a Gaussian gap cannot be told apart (2019ApJ...877L..32M), nor a gap
  and a double power law in a debris belt (2015ApJ...798..124R); a belt resolved by about 1.7 beams gives neither
  its density distribution nor the star offset (2017AJ....154..225S). Fitting radii without model convolution
  lets beam dilution in, mostly in narrow gaps (2021A&A...648A..33M). Image-plane widths fitted without beam
  deconvolution are upper limits (2024ApJ...961..228S), and the DSHARP width definitions do not account for the
  beam (2018ApJ...869L..42H, card). A visibility fit can constrain a width below the image beam, but only if S/N,
  uv sampling and the assumed functional form allow it; test with injection and recovery.
- **Super-resolution artefacts.** SpM can create clumps and speckles around bright inner disks
  (2024PASJ...76..437Y).
- **Thin-disk deprojection fails for edge-on or thick disks.** Edge-on debris disks were forward-modelled
  (2015A&A...581A..97S, 2016ApJ...823..108B); symmetry and moderate resolution limited line-surface geometry
  (2021A&A...645A.145G).
- **Tentative rings.** BIC preferred no ring for a low S/N brown dwarf disk (2025ApJ...986L..11S); ring clumps
  at 3-5 sigma need deeper data (2025ApJ...993...85Y).
- **Axisymmetry hides asymmetry.** Axisymmetric models fail to reproduce azimuthal asymmetry amplitudes
  (2018ApJ...869...17L); residuals up to 8.4 sigma remained in GM Aur (2020ApJ...891...48H).
- **Missing flux and primary beam.** A disk near the largest recoverable scale (2014ApJ...791L...6W), ring
  ansae near the primary beam edge (2017MNRAS.466.4201W), or a partly observed ring without short baselines
  (2017MNRAS.469.3200B) make outer structure, fluxes and asymmetries unreliable.
- **Optical depth and temperature drive the physics.** Optically thick rings make masses lower limits;
  optical depth is degenerate with scale height (2025A&A...697A..64V); temperature uncertainty dominates
  dust-trap and planet-mass estimates (2024ApJ...976..132H); a multi-band temperature posterior can be mostly
  prior (2021A&A...648A..33M); optical depths may be off by up to a factor of two (2018ApJ...869L..42H, card);
  two-band data cannot pin down grain size and porosity (2024ApJ...971..129C, 2020ApJ...891...48H).
- **Planet masses are model-bound.** They assume one planet per gap and fixed alpha and h/r
  (2024ApJ...976..132H, 2018ApJ...869...17L); width-only masses ignore gap depth (2026A&A...705A.196H); debris
  chaotic-zone masses assume an empty gap and a planet that has not migrated (2020MNRAS.498.1319M); planet-disk
  relations are uncertain for wide Jupiter-mass gaps (2024PASJ...76..437Y); rings as pressure maxima and
  fragmentation-limited grains are explicit assumptions (2025A&A...697A..64V); gas-gap depths need an abundance
  assumption and a vertically isothermal disk (2019ApJ...880...69Y).
- **Unsharp masking is arbitrary** in kernel size and weight; treat the morphology with caution
  (2020A&A...644A.119P).
- **Settings papers rarely report.** The pack aggregate "Settings cards flag as needed but not stated" lists
  its top 40 exact phrasings. Summing them by keyword (my sum, a lower bound, all 584 papers): line-free
  channels or continuum subtraction (100), self-calibration intervals or rounds (53), CASA or pipeline version
  (42), cell size, image size, clean mask or threshold (32), flux-scale calibrator or uncertainty (20),
  primary-beam correction (10), moment-map clipping (5), uvmodelfit starting values (3). Excerpt cards also
  flag missing MCMC walkers, steps, priors and frank or rave versions (2026A&A...705A.196H,
  2019AJ....158..162F). Record all of these in your own output.

## Verification checks

What papers did:
- Compare model and data in the visibility domain (binned real and imaginary parts), in images, and in radial
  cuts; inspect residual images made with the same uv coverage (2018ApJ...869...17L, 2014ApJ...791L...6W,
  2020ApJ...898...36L). A no-gap model failing to reproduce visibility wiggles beyond 50 klambda, with no
  residual above 3 sigma for the gap model, supported a debris gap (2020MNRAS.498.1319M).
- Select between model complexities with Bayes factors, BIC or AIC (2020ApJ...902..141S, 2024ApJ...976..132H,
  2024A&A...689L...5M).
- Cross-check methods: parametric vs frank (2024ApJ...976..132H); frank vs rave vs parametric
  (2026A&A...705A.196H); SpM vs CLEAN-model profiles and published frank fits (2024PASJ...76..437Y); robustness
  to frank alpha and w_smooth (2024A&A...689A.104D) and to the CLEAN robust value for rave
  (2026A&A...705A.196H).
- Convergence: steps much larger than the autocorrelation time (2018ApJ...869L..42H, card; 2024A&A...689L...5M);
  autocorrelation negligible after thinning (2017MNRAS.466.4201W); vary walker starting positions
  (2015ApJ...798..124R) or initial i, PA and centre (2018A&A...616A..88V).
- Geometry consistency: ellipse-fit and Gaussian geometries agree within one degree (2018ApJ...869L..42H,
  card); visibility and image-plane fits agree (2017AJ....154..225S); flux scales of executions aligned on
  overlapping baselines (2021A&A...648A..33M).
- Independent data: short-baseline ACA data not used in the fit (2020ApJ...902..141S), earlier fluxes
  (2018ApJ...869...17L), scattered-light ellipse fits (2019AJ....158..162F), previous ring catalogues
  (2025A&A...697A..64V), earlier dark-ring positions (2015ApJ...806L...7Z); smooth to the other instrument's beam
  before comparing (2024ApJ...961..228S).
- Forward-model physical models through the same beam before comparing profiles (2020ApJ...898...36L
  convolved to 0.1 arcsec; 2018A&A...616A..88V imaged DALI models with the 0.25 arcsec beam).
- Planet-mass sensitivity: masses barely changed for alpha from 1e-4 to 1e-2 (2024PASJ...76..437Y).

What a careful referee adds:
- Inject and recover a synthetic ring or gap of the claimed width and depth in the real uv coverage (a debris
  paper injected gaps to find the widest undetectable one, 2026ApJ..1004..182H; ARKS checked that a thin-ring
  test would resolve narrow rings, 2026A&A...705A.196H). Use this, not the beam size alone, to decide whether
  a sub-beam width is a measurement or a limit.
- Propagate geometry, flux calibration, primary-beam and functional-form uncertainty, not only the sampler
  posterior or frank error band.
- Put the beam (or the effective frank or SpM resolution) next to every width, and report a width or depth as a
  limit when the posterior or the recovery test shows it is not constrained.
- For SVI or other approximate inference, compare against a sampler on at least one target.
- Check rings for azimuthal variation before trusting an azimuthal average.
- Check units and the sign convention in every spectral-index and optical-depth formula before applying it.

## Source cards

Full list: `references/sources.md` (generated). Most informative for this technique:

- 2018ApJ...869...17L: Taurus survey; uv fits with galario and emcee, gap and ring metrics, snowline and planet tests.
- 2024PASJ...76..437Y: 43 Taurus disks in SpM super-resolution; ring, gap and inflection definitions, depths, Zhang planet masses.
- 2026A&A...705A.196H: ARKS debris discs; frank, rave and parametric profiles, edge metrics, chaotic-zone planet masses.
- 2018ApJ...869L..42H: DSHARP annular substructures; ellipse fits, 1 au profiles, width and depth definitions.
- 2018ApJ...869L..43H: DSHARP spirals; polar deprojection and azimuthal sampling.
- 2018ApJ...869L..46D: DSHARP thin rings and dust trapping.
- 2020ApJ...891...48H: GM Aur two-band uv fits, spectral index, RT geometry tests.
- 2020ApJ...898...36L: dual-wavelength ring widths, priors, dust evolution comparison.
- 2021A&A...648A..33M: TW Hya four-band flux alignment, mtmfs spectral index, radial dust properties.
- 2025MNRAS.538.2358S: LkCa 15 Band 3; frank plus per-radius T_d, Sigma_d, a_max fits.
- 2024ApJ...976..132H: sigma Orionis; SVI fits, substructure definitions, trapping and planet masses.
- 2024A&A...689A.104D: TW Hya Band 8; frank hyperparameters, Gaussian-ring emcee fit, disk sizes.
- 2024ApJ...971..129C: Elias 2-24 dust-trapping ring; frank plus trapping width limits.
- 2025A&A...697A..64V: 33-disk settling study; wedges, iterative surface density, alpha/St from widths.
- 2018A&A...616A..88V: V1094 Sco; Gaussian x cosine uv model, spectral index profile.
- 2020ApJ...902..141S: VANDAM protostellar substructures; dynesty, Bayes factors, ACA check.
- 2024ApJ...961..228S: WL 17 Class I ring; ellipse fit, deprojected profile, ring mass.
- 2019ApJ...880...69Y: HL Tau HCO+ gas gaps; stacked spectra, gap depth to planet mass.
- 2015ApJ...810..112O: IM Lup DCO+ double rings; unclipped deprojected line profiles.
- 2020A&A...644A.119P: DG Tau line rings and an unsharp-masked dust ring.
- 2015ApJ...798..124R: HD 107146 debris gap; uv fits of gap vs double power law.
- 2020MNRAS.498.1319M: HD 206893 debris gap; RADMC-3D gap model, frank, chaotic-zone planet mass.
- 2019AJ....158..162F: HD 202628 eccentric debris ring from the star-ring offset.
- 2026ApJ..1004..182H: gamma Oph broad belt; rave and frank profiles, gap injection.
- 2025ApJ...986L..11S: brown dwarf disk; frank plus BIC against a tentative ring.
