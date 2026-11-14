---
name: alma-disk-substructure-profiles
description: "Measure deprojected radial intensity profiles of protoplanetary, protostellar and debris disks from ALMA data, and locate and characterise rings, gaps, cavities, spirals and azimuthal asymmetries (location, width, depth, contrast, dust radius, spectral index, optical depth, trapping and planet-mass inferences). Use when a task asks for a disk radial profile, ring or gap positions and widths, a parametric or non-parametric (frank) visibility fit of an axisymmetric disk, a substructure census, or planet masses from gaps. Built from 214 on-topic ALMA disk papers (2012-2026)."
---

# Disk radial profiles, rings and gaps

Turns a continuum (or line) dataset of a disk into a deprojected radial profile I(r), then into ring and gap
locations, widths, depths and physical inferences. Two mistakes matter most: (1) reading substructure off a
beam-convolved image profile when the feature is near or below the beam (fit the visibilities, and report a
width as a limit when the data do not constrain the intrinsic width); (2) quoting formal MCMC errors as if they
included geometry, functional-form choice and flux calibration, which authors repeatedly admit they do not.

Evidence base: the `disk-substructure-profiles` pack (266 regex-tagged papers). 52 off-topic papers (galaxies,
prestellar cores, outflows, hot cores, HII regions, filaments; list in `references/parameters.md`) are excluded
from my own counts, leaving 214. Counts marked "pack" are the pack aggregates (per matched analysis step, over
all 266 papers, off-topic ones included). Counts marked "pack lines" are my count of distinct on-topic papers
in the pack's key-parameter, assumption and excerpt lines (the excerpts cover only 40 papers, so these are
lower bounds for the corpus). "(card)" means a verbatim quote in that paper's card, not in the pack.

## When to use

- Continuum images or visibilities of a protoplanetary or protostellar (Class 0/I) disk where rings, gaps,
  cavities, shoulders or inner disks are visible or suspected (2018ApJ...869...17L, 2020ApJ...902..141S,
  2024ApJ...961..228S).
- Debris belts: belt radius, width, inner and outer edges, gaps inside broad belts, eccentricity from the
  star-belt offset (2015ApJ...798..124R, 2019AJ....158..162F, 2026ApJ..1004..182H).
- Line emission rings and gas gaps from deprojected, azimuthally averaged moment-0 maps or stacked spectra
  (2015ApJ...810..112O, 2019ApJ...880...69Y, 2020A&A...644A.119P).
- Multi-band comparisons of the same rings: widths and positions at two wavelengths, radial spectral index,
  optical depth (2020ApJ...891...48H, 2020ApJ...898...36L, 2018A&A...616A..88V).
- Turning measured gaps and rings into dust-trapping or planet-mass statements (2018ApJ...869...17L,
  2024ApJ...976..132H, 2025A&A...697A..64V).

## When not to use

| Situation | Use instead |
|---|---|
| Galaxy disks, tilted-ring rotation curves, spiral-arm masks in nearby galaxies | `alma-galaxy-3d-kinematics`, `alma-star-formation-laws` |
| Prestellar or protostellar cores, filaments, cluster-forming clumps (envelope density profiles) | `alma-core-extraction-cmf` |
| Gas kinematics: Keplerian masks, dynamical masses, velocity deviations from planets | `alma-keplerian-disk-kinematics` |
| Generic visibility fitting machinery (likelihood, weights, samplers) | `alma-uv-plane-fitting` (this skill covers the disk-profile specifics) |
| Total dust mass only, no radial structure | `alma-dust-continuum-mass` |
| Spectral index maps without a radial-structure question | `alma-spectral-index` |
| Full physical disk models (thermochemistry, RT, hydro) | `alma-radiative-transfer-modelling`, `alma-hydro-simulation-comparison` |
| Edge-on, vertically extended or warped emission where a thin-disk deprojection fails | forward modelling of the 3D structure (see step 3 and `alma-radiative-transfer-modelling`) |

## Steps

1. **Image for inspection, not for measurement.** Goal: see the structure and pick a model family.
   Method: CASA `tclean` continuum images at several weightings; one survey used `mfs`, `nterms=1`,
   multiscale, robust -0.5 to 0.5, cleaned to about 5 sigma (2025A&A...697A..64V); another inspected several
   robust values plus superuniform weighting and excluded tentative features that could be imaging
   artefacts (2020ApJ...902..141S). Software: CASA (pack 63, plus task-named entries).
2. **Fix the geometry (centre, inclination i, PA).** Three routes in the pack:
   - CASA `imfit` 2D Gaussian (2018ApJ...869...17L, 2019A&A...622A..75L); imfit values used to initialise the
     uv fit (2018A&A...616A..88V).
   - Ellipse fit to ring peaks found along cuts: every 10 deg (2013ApJ...777L..25M), every 1 deg in polar
     coordinates (2024ApJ...961..228S); DSHARP fit a 5-parameter ellipse with emcee (30 walkers, 20,000
     steps, 500 burn-in) to each ring and gap (2018ApJ...869L..42H).
   - Free parameters of the visibility fit with priors, e.g. uniform +-20 deg on i and PA and +-0.5 arcsec on
     offsets (2018ApJ...869...17L), or Gaussian priors on PA, i and offsets (2020ApJ...891...48H). For an
     eccentric debris ring, one paper fit a constant-surface-density ring model in visibility space with emcee
     (ring centre offset free) and took the eccentricity as projected star-ring offset over projected
     semimajor axis; independent ellipse fits to HST images were a cross-check, not the ALMA measurement
     (2019AJ....158..162F).
   Many papers instead fix i and PA from earlier work (2015ApJ...810..112O, 2024A&A...689A.104D).
3. **Deprojected image-plane profile.** Goal: a first I(r) and an azimuthal check. Method (general practice,
   valid only for a geometrically thin, roughly planar disk at low to moderate inclination): rotate by PA,
   stretch the minor-axis coordinate by 1/cos i, average in annuli. Near edge-on, vertically extended or
   warped emission this breaks down; the pack's edge-on debris disks were forward-modelled instead
   (2015A&A...581A..97S at i = 90 deg; 2016ApJ...823..108B with an edge-on wedge), and moderate resolution
   plus an axisymmetry assumption limited emission-surface geometry from lines (2021A&A...645A.145G).
   Bin widths seen: 1 au (2020ApJ...891...48H; 2018ApJ...869L..42H, card), a quarter of the beam
   (2018MNRAS.475.5296D, 2024ApJ...965..147B), 0.05 arcsec bins with the innermost bin at a radius of one beam
   (0.1 arcsec, 2019ApJ...880...69Y), 4 au (2018ApJ...864..133T). Bins narrower than the beam are correlated:
   one paper took per-bin error = rms / sqrt(ring solid angle / beam solid angle) (2019ApJ...883...71C); keep
   the covariance between neighbouring bins in any later fit. For lines, average the unclipped moment-0 map
   to avoid clipping bias (2015ApJ...810..112O, 2020A&A...644A.119P).
4. **Fit the visibilities (the measurement).** Goal: resolution-limited structure without deconvolution bias.
   - Parametric: central Gaussian or exponentially tapered power law plus Gaussian rings (2018ApJ...869...17L,
     2020ApJ...898...36L); delta function plus Gaussian rings, 21 free parameters (2020ApJ...891...48H);
     Gaussian times cosine terms, up to n=4 and 13 parameters (2018A&A...616A..88V); Nuker profile
     (2024ApJ...966...59S); power law with a gap or double power law for debris belts (2015ApJ...798..124R).
     Model visibilities with galario (pack 25) or vis_sample (pack 8). Sample with emcee (pack 62), pymc
     (2018A&A...616A..88V), dynesty nested sampling (2020ApJ...902..141S), or stochastic variational
     inference in pyro (2024ApJ...976..132H). SVI is approximate: that paper approximated the posterior as a
     multivariate normal and says so. If you use SVI, check for missed modes and non-Gaussian posteriors (for
     example rerun from several initialisations, or compare with a short MCMC run).
   - Non-parametric: frank (8 papers, pack lines) assumes an axisymmetric, geometrically thin disk;
     hyperparameters in the table below (2024A&A...689A.104D, 2024ApJ...971..129C).
   - Add components only when residuals demand it: add a ring or switch to a tapered power law when symmetric
     residuals exceed about 5-10 sigma (2018ApJ...869...17L); compare model complexities with Bayes factors
     (2020ApJ...902..141S) or BIC (2024ApJ...976..132H, 2025ApJ...986L..11S).
   - Check that the visibility weights match the data scatter before fitting, and rescale only when that
     check shows they do not. Reported corrections are dataset specific: pipeline weights multiplied by about
     0.25 to match the image rms (2020ApJ...902..141S); weights scaled down by 2.667 (2020ApJ...891...48H); a
     rescaling factor f "typically about 2" whose direction the pack does not define (2024ApJ...976..132H).
     Inflating the errors of an image-plane profile is a different correction: 2018ApJ...869L..46D multiplied
     its profile errors by sqrt(70). State which quantity you rescaled and in which direction.
   - Image-plane fits appear too, mostly for debris belts. The model must go through the observational
     response first: attenuate it by the primary beam, then convolve with the synthesized (dirty) beam before
     comparing with the dirty image (2017MNRAS.466.4201W), or multiply by the primary beam and sample at the
     observed uv points (2015ApJ...798..124R). Papers fit dirty images with chi2 over dirty-beam-convolved
     pixels (2020MNRAS.497.2811K) and scaled sigma by sqrt(beam area in pixels) for correlated noise
     (2016MNRAS.460L..10B, 2017AJ....154..225S).
5. **Extract substructure metrics from the best-fit (or posterior) profile.**
   - Ring = local maximum, gap = local minimum, shoulder = three consecutive inflection points, evaluated over
     2000 posterior profiles (2024ApJ...976..132H).
   - Gap location at the local minimum, gap width as full width at half depth, contrast = ring peak / gap,
     uncertainties from 100 chain samples (2018ApJ...869...17L).
   - DSHARP defined widths and depths empirically from the gap minimum and ring peak intensities, without
     assuming a functional form, and defined the dust radius as the radius enclosing 95% of the total flux
     (2018ApJ...869L..42H, card). Other size definitions: R_eff at 90% flux (2018ApJ...869...17L),
     R68/R95/R99 (2024A&A...689A.104D).
   - Ring width = Gaussian sigma of the fitted ring (2024ApJ...976..132H, 2020ApJ...898...36L).
6. **Asymmetries and non-axisymmetric structure.** Use polar (r, theta) deprojected maps; DSHARP sampled spiral
   peaks every 6-18 deg in azimuth depending on radius (2018ApJ...869L..43H). Fit arcs and vortices with an
   explicit model (2018ApJ...869L..50P used a steady-state vortex prescription). Unsharp masking (subtract an
   image smoothed by 60 mas, 2020A&A...644A.119P; 66 mas FWHM Gaussian with weight 0.95, 2018ApJ...869L..44K)
   reveals faint rings and spirals but its authors call it arbitrary (2020A&A...644A.119P). Test azimuthal
   brightness variation against the noise and against identical ellipses placed on emission-free sky
   (2013ApJ...777L..25M).
7. **Multi-wavelength and physical conversion.**
   - Spectral index: smooth to a common beam (CASA `imsmooth`, 2020ApJ...891...48H) or re-image both bands
     with a common 0.25 arcsec beam and uv range, masking pixels with S/N < 2.5 (2018A&A...616A..88V);
     alpha = log(I1/I2)/log(nu1/nu2), with the intensity and frequency ratios in the same order
     (2020ApJ...891...48H). The pack line for 2016Natur.535..258C writes the frequency ratio inverted relative
     to the flux ratio, which flips the sign; do not copy that form. Carry 10% flux calibration per band; for
     close bands it gave a 0.42 systematic error on alpha (2018A&A...616A..88V).
   - Optical depth (as in 2019ApJ...880...69Y): tau_d = -ln(1 - I / (B(T_d) - B(T_bg))), with T_bg = 2.73 K
     and T_d from a disk temperature model. Dropping B(T_bg) is an approximation that only holds when
     B(T_d) >> B(T_bg). Requirements (general practice): I and B in the same specific-intensity units (for
     example Jy/sr, not Jy/beam); the argument 1 - I/(B(T_d) - B(T_bg)) must be positive (if I approaches
     B(T_d), report the ring as optically thick and tau as a lower limit); the formula assumes the emission
     fills the beam and neglects scattering, so beam dilution of a narrow ring biases tau low. T_d is often
     a passive flared disk (flaring angle 0.02 in 2018ApJ...869L..42H, card, and 2024ApJ...971..129C; 0.05 in
     2018ApJ...869...17L); DSHARP warned their optical depths may be off by up to a factor of two
     (2018ApJ...869L..42H, card).
   - Ring dust mass, optically thin: M = F d^2 / (kappa B(T)), typically kappa 2-2.3 cm2/g at 1.3 mm and
     T = 20 K (2020A&A...644A.119P, 2024ApJ...961..228S); a lower limit if the ring is optically thick.
   - Grain sizes: two-band spectral index or optical depth alone does not give a unique grain size. Authors
     say temperature, flux calibration and degeneracies prevent precise grain-size measurements
     (2020ApJ...891...48H), and that two bands constrain four parameters only through priors, with porosity
     unconstrained (2024ApJ...971..129C). Report the priors and the assumed temperature with any grain-size
     statement.
8. **Interpretation.**
   - Dust trapping: compare ring width w_d with the pressure scale height h_p; w_d < h_p argues for trapping
     (2024ApJ...976..132H, 2024ApJ...971..129C). For alpha_r/St = [(w_g/w_d)^2 - 1]^-1 (2025A&A...697A..64V):
     w_d is the Gaussian width of the model dust surface-density ring (not the width of the beam-convolved
     brightness profile); w_g is not measured, so bound it between w_g,min = H_g (gas scale height from the
     temperature) and w_g,max = distance from the ring peak to the deepest point of the gap inside it; the
     relation needs w_g > w_d and assumes the ring is a pressure maximum and the grains are fragmentation
     limited.
   - Planet masses from gap geometry: the Hill radius (general practice) is R_Hill = a (M_p / 3 M_star)^(1/3),
     with a = the planet's orbital radius, taken as the gap centre. 2018ApJ...869...17L "simply assume[d] that
     the gap radius corresponds to 4 R_Hill" (citing Dodson-Robinson 2011); the pack does not say whether
     "gap radius" there means a gap width or half-width, so state the size observable you use (for example the
     measured gap width) and never put the gap's orbital radius into the Hill-radius relation in its place.
     The same paper's alternative is the Rosotti et al. 2016 diagnostic, the normalized gap-ring distance
     (typically 0.2-0.3; 0.25 gave about 15 Earth masses for alpha = 1e-4), with alpha = 1e-4 or 1e-2.
     2016A&A...586A..99H used a gap width of 5 Hill radii. Zhang et al. 2018 width relations with alpha = 1e-3
     and DSHARP opacity (2024ApJ...976..132H). For debris gaps, the chaotic-zone width (2015ApJ...798..124R).
     Always state alpha, h/r and the one-planet-per-gap assumption.
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
| Radial profile form (uv fit) | Gaussian rings + central Gaussian or tapered power law | Gaussian x cosine, Nuker, delta + Gaussians, power law with gap | 14 mention Gaussian rings (pack lines) | 2018ApJ...869...17L, 2020ApJ...891...48H, 2018A&A...616A..88V, 2024ApJ...966...59S |
| emcee walkers | 100 | 24 to 1024 | 30 report walkers; 9 use exactly 100, 1 more "about 100" (pack lines) | 100: 2018ApJ...869...17L, 2020ApJ...898...36L, 2025ApJ...986L..11S, 2018ApJ...869L..46D; extremes: 2025ApJ...984L..19Y (24), 2019ApJ...881...84S (1024) |
| emcee steps / burn-in | example: 5000 steps, about 2000 burn-in, keep the last 1000 (2018ApJ...869...17L) | 500 to 100,000 steps | pack lines (no consensus) | 2018ApJ...869...17L, 2020ApJ...891...48H, 2024A&A...689A.104D, 2020ApJ...895..126H |
| Geometry priors | example: uniform +-20 deg (i, PA), +-0.5 arcsec offsets (2018ApJ...869...17L) | Gaussian priors from image fits; fixed from literature | pack lines (study specific) | 2018ApJ...869...17L, 2020ApJ...891...48H, 2024A&A...689A.104D |
| Ring parameter priors | example: ring centre +-0.05 arcsec around the visual ring | r_peak 10-80 au, sigma 1-50 au | 2 (study specific) | 2020ApJ...898...36L, 2019ApJ...878...16P |
| Model radial grid | 0.0001-4 arcsec, step 0.0005-0.001 arcsec | 0.1-0.5 au steps over 0-500 au | 4 | 2018ApJ...869...17L, 2020ApJ...898...36L, 2017ApJ...839...99P, 2018ApJ...859...32P |
| frank alpha | 1.3 | 1.05-1.3 | 5 (pack lines) | 2024A&A...689A.104D, 2024ApJ...971..129C, 2026ApJ..1001..124M |
| frank w_smooth | no consensus; 1e-4 in 2 of 5 | 1e-4 to 1e-1 | 5 | 2024A&A...689A.104D, 2024ApJ...974..102S, 2025ApJ...986L..11S |
| frank N / Rmax | 300-400 points; Rmax a few arcsec | Rmax 2.1-5 arcsec or 4 R_out | 4 | 2024ApJ...971..129C, 2026ApJ..1001..124M, 2025ApJ...986L..11S |
| Visibility binning (plots, grid fits, model uv grid) | 10 klambda | 7-30 klambda | 5 (pack lines) | 2014ApJ...791L...6W, 2018A&A...616A..88V, 2018ApJ...869L..48G (model uv points in 10 klambda steps), 2013ApJ...777L..25M (7), 2018A&A...610A..24F (30) |
| Image-profile bin width | 1 au or a quarter beam | 0.05-0.15 arcsec, 4 au | 7 | 2020ApJ...891...48H, 2018MNRAS.475.5296D, 2019ApJ...880...69Y, 2018A&A...615L..10M |
| Weight or error rescaling | only when a check shows weights or errors are off; dataset specific | visibility weights x0.25 or /2.667, f about 2 (direction not given); profile errors x sqrt(70) | 4 | 2020ApJ...902..141S, 2020ApJ...891...48H, 2024ApJ...976..132H, 2018ApJ...869L..46D |
| Flux calibration error (absolute) | 10% per band | 10%; separately, DSHARP relative flux scales between executions agreed within 5% (not an absolute error) | 3 (pack lines) | 2024A&A...689A.104D, 2020ApJ...891...48H, 2018A&A...616A..88V; relative: 2018ApJ...869L..41A |
| Dust opacity at 1.3 mm (mass) | 2-2.3 cm2/g | 0.43 (DSHARP absorption) to 2.3 | pack lines | 2024ApJ...961..228S, 2020A&A...644A.119P, 2024ApJ...976..132H |
| Dust temperature (mass estimates) | 20 K | about 10 K (debris belt) to 80 K (inner ring of HD 100546; 60 K disk-wide, 40 K outer ring), or passive-disk T(r) | 20 K in 6 (pack lines) | 20 K: 2024ApJ...961..228S, 2020A&A...644A.119P, 2025ApJ...993...90S; 10 K: 2017ApJ...850L...6A; 40/60/80 K: 2014ApJ...791L...6W; T(r): 2024ApJ...971..129C |
| Turbulence alpha (interpretation) | 1e-3 | 1e-4 to 1e-2 | pack lines | 2024ApJ...976..132H, 2019ApJ...880...69Y, 2018ApJ...869...17L |

More settings by paper (samplers, frank runs, debris belt models, thermal assumptions) are in
`references/parameters.md`.

## Software

Counts are the pack aggregate "Software named in the matched steps" (per matched step, all 266 papers, off-topic
ones included; names lower-cased in the pack). I did not recount per paper.

| Software | Used for | Pack count |
|---|---|---|
| emcee | posterior sampling for profile, ring, belt and ellipse fits | 62 |
| casa (tclean, imfit, imsmooth, imstat, simobserve) | imaging, geometry, common-beam smoothing, ring fluxes, mock observations | 63, plus task-named entries (simobserve 5, imfit 3, tclean 3, clean 2, viewer 2, uvmodelfit 2) |
| galario | model visibilities from a radial profile or model image | 25 |
| radmc-3d | physical and RT disk models compared with profiles | 16 |
| gofish | stacked line spectra and radial profiles of gas | 11 |
| dali, lime | thermochemical and line RT models of rings | 10, 8 |
| vis_sample | model visibilities | 8 |
| miriad | imaging and uv modelling in older papers | 7 |
| bettermoments | moment maps for line profiles | 6 |
| frank / frankenstein | non-parametric 1D visibility fit | 5 + 5 (8 distinct on-topic papers in pack lines) |
| eddy | disk geometry and surfaces from lines | 5 |
| mcfost | settling and dust RT models (2025A&A...697A..64V) | 4 |
| uvmultifit, pymc, dynesty | alternative uv fitting and inference (2018A&A...616A..88V, 2020ApJ...902..141S) | 3, 2, 1 |
| pyro | stochastic variational inference (2024ApJ...976..132H) | named in that excerpt only |
| rave | non-parametric belt profiles for debris disks (2026ApJ..1004..182H) | 3 |
| fargo | hydrodynamic planet-gap models | 2 |

## Pitfalls

- **Formal errors are too small.** Authors say fit errors are likely underestimated (2018ApJ...869...17L) and
  that ring uncertainties depend on the chosen functional form (2020ApJ...898...36L). Calibration uncertainty
  is often left out of the MCMC (2020ApJ...892...99C). SVI posteriors are a multivariate-normal approximation
  (2024ApJ...976..132H).
- **Widths and shapes are poorly constrained near the beam.** Gap and ring widths are hard to constrain
  (2018A&A...616A..88V); a two-ring model and a Gaussian gap model cannot be told apart at the resolution
  (2019ApJ...877L..32M); a gap and a double power law likewise for a debris belt (2015ApJ...798..124R); a belt
  resolved by only about 1.7 beams gives neither its density distribution nor the star offset
  (2017AJ....154..225S); Band 8 resolution did not resolve the outer substructure (2024A&A...689A.104D).
  Image-plane widths fitted without beam deconvolution are upper limits (2024ApJ...961..228S), and the DSHARP
  width definitions do not account for the beam (2018ApJ...869L..42H, card). A visibility fit can constrain a
  width below the image beam, but only if S/N, uv sampling and the assumed functional form allow it; test with
  injection and recovery rather than assuming either way.
- **Thin-disk deprojection fails for edge-on or thick disks.** Edge-on debris disks were forward-modelled
  (2015A&A...581A..97S, 2016ApJ...823..108B); symmetry and moderate resolution limited line-surface geometry
  (2021A&A...645A.145G).
- **Tentative rings.** BIC preferred no ring for a low S/N brown dwarf disk (2025ApJ...986L..11S); ring clumps
  at 3-5 sigma need deeper data (2025ApJ...993...85Y).
- **Axisymmetry hides asymmetry.** Axisymmetric models fail to reproduce azimuthal asymmetry amplitudes
  (2018ApJ...869...17L); residuals up to 8.4 sigma remained in GM Aur (2020ApJ...891...48H).
- **Missing flux and primary beam.** A disk near the largest recoverable scale (2014ApJ...791L...6W) or ring
  ansae near the primary beam edge (2017MNRAS.466.4201W) make outer structure and N/S asymmetries unreliable.
- **Optical depth and temperature drive the physics.** Optically thick rings make masses lower limits;
  optical depth is degenerate with scale height (2025A&A...697A..64V); temperature uncertainty dominates
  dust-trap and planet-mass estimates (2024ApJ...976..132H); optical depth estimates may be off by up to a
  factor of two (2018ApJ...869L..42H, card); two-band data cannot pin down grain size, porosity stays
  unconstrained (2024ApJ...971..129C, 2020ApJ...891...48H).
- **Planet masses are model-bound.** They assume one planet per gap and fixed alpha and h/r
  (2024ApJ...976..132H, 2018ApJ...869...17L); rings as pressure maxima and fragmentation-limited grains are
  explicit assumptions (2025A&A...697A..64V); gas-gap depths need an abundance assumption and a vertically
  isothermal disk (2019ApJ...880...69Y).
- **Unsharp masking is arbitrary** in kernel size and weight; treat the morphology with caution
  (2020A&A...644A.119P).
- **Settings papers rarely report.** The pack aggregate "Settings cards flag as needed but not stated" lists
  exact phrasings, so the same item is split across many lines. Summing the listed phrasings by keyword (my
  sum, a lower bound, all 266 papers): line-free channels or continuum subtraction (66), self-calibration
  intervals or rounds (43), CASA or pipeline version (36), cell size, image size, clean mask or threshold
  (24), flux-scale calibrator or uncertainty (10), primary-beam correction (6), moment-map clipping (4),
  Briggs robust (3). Excerpt cards also flag missing MCMC walkers, steps and priors (2019AJ....158..162F,
  2018ApJ...869...17L). Record all of these in your own output.

## Verification checks

What papers did:
- Compare model and data in the visibility domain (binned real and imaginary parts), in images, and in radial
  cuts; inspect residual images made with the same uv coverage (2018ApJ...869...17L, 2014ApJ...791L...6W,
  2020ApJ...898...36L).
- Select between model complexities with Bayes factors or BIC (2020ApJ...902..141S, 2024ApJ...976..132H).
- Cross-check parametric and non-parametric (frank) profiles (2024ApJ...976..132H); show results are robust to
  frank alpha and w_smooth (2024A&A...689A.104D).
- Convergence: steps much larger than the autocorrelation time (2018ApJ...869L..42H, card); autocorrelation
  negligible after thinning (2017MNRAS.466.4201W); vary walker starting positions (2015ApJ...798..124R) or
  initial i, PA and centre (2018A&A...616A..88V).
- Geometry consistency: ellipse-fit and Gaussian geometries agree within one degree (2018ApJ...869L..42H,
  card); visibility and image-plane fits agree (2017AJ....154..225S).
- Independent data: short-baseline ACA data not used in the fit (2020ApJ...902..141S), earlier fluxes
  (2018ApJ...869...17L), scattered-light ellipse fits (2019AJ....158..162F), previous ring catalogues
  (2025A&A...697A..64V); smooth to the other instrument's beam before comparing (2024ApJ...961..228S).
- Forward-model physical models through the same beam before comparing profiles (2020ApJ...898...36L
  convolved to 0.1 arcsec; 2018A&A...616A..88V imaged DALI models with the 0.25 arcsec beam).

What a careful referee adds:
- Inject and recover a synthetic ring or gap of the claimed width and depth in the real uv coverage (a debris
  paper injected gaps to find the widest undetectable one, 2026ApJ..1004..182H). Use this, not the beam size
  alone, to decide whether a sub-beam width is a measurement or a limit.
- Propagate geometry, flux calibration and functional-form uncertainty, not only the sampler posterior.
- Put the beam (or the effective frank resolution) next to every width, and report a width as a limit when the
  posterior or the recovery test shows the intrinsic width is not constrained.
- For SVI or other approximate inference, compare against a sampler on at least one target.
- Check rings for azimuthal variation before trusting an azimuthal average.
- Check units and the sign convention in every spectral-index and optical-depth formula before applying it.

## Source cards

Full list: `references/sources.md` (generated). Most informative for this technique:

- 2018ApJ...869...17L: Taurus survey; uv fits with galario and emcee, gap and ring metrics, snowline and planet tests.
- 2018ApJ...869L..42H: DSHARP annular substructures; ellipse fits, 1 au profiles, width and depth definitions.
- 2018ApJ...869L..43H: DSHARP spirals; polar deprojection and azimuthal sampling.
- 2018ApJ...869L..46D: DSHARP thin rings and dust trapping.
- 2020ApJ...891...48H: GM Aur two-band uv fits, spectral index, RT geometry tests.
- 2020ApJ...898...36L: dual-wavelength ring widths, priors, dust evolution comparison.
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
- 2019AJ....158..162F: HD 202628 eccentric debris ring from the star-ring offset.
- 2026ApJ..1004..182H: gamma Oph broad belt; rave and frank profiles, gap injection.
- 2025ApJ...986L..11S: brown dwarf disk; frank plus BIC against a tentative ring.
