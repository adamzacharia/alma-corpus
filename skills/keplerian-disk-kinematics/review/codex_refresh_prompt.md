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

=== SKILL.md (keplerian-disk-kinematics) ===
---
name: alma-keplerian-disk-kinematics
description: "Fit Keplerian rotation of disks in ALMA line data to measure central (stellar or protostellar) dynamical masses, disk inclination, position angle, systemic velocity, emission height and Keplerian radius, and to find deviations from Keplerian rotation. Covers velocity-map fits (bettermoments + eddy), forward modelling of channel maps or visibilities (RADMC-3D/LIME, pdspy, csalt, DISCMINER + emcee/dynesty), velocity-aligned stacking for faint disks, and PV-diagram rotation curves for embedded protostars. Use when a paper or task needs a dynamical mass from disk rotation, a Keplerian mask, Keplerian-shifted stacking, or checks on someone else's Keplerian fit. Built from 447 ALMA papers (2012-2026)."
---

# Keplerian disk kinematics and dynamical masses

Measures the central mass and disk geometry from the line-of-sight velocity pattern of a rotating disk,
v_los = sqrt(G M / r) cos(phi) sin(i) + v_sys for a thin disk (general practice). The two mistakes that matter
most: (1) **reporting M* without facing the mass-inclination and mass-distance degeneracies**: the
line of sight only constrains roughly M sin^2 i, and M scales linearly with the adopted distance
(2015ApJ...812...27A reports M* sin^2 i = 0.56 Msun; 2020ApJ...894...74B: "dynamical mass scales linearly
with distance"); and (2) **quoting the MCMC posterior width as the error**: in CQ Tau the formal error was
+-0.002 Msun while different model runs gave 1.47-1.65 Msun (2021A&A...648A..19W); in HD 142527 the mass moved
from 2.29 to 2.53 Msun with the fitted radial range (2021A&A...650A..59B); eddy errors "below 1%" were "likely
underestimated" because pixel correlation was ignored (2026A&A...705A.202M); and in DM Tau / MWC 480
systematics dominate over statistics (2020ApJ...895..109F).

> Always report: tracer and transition, rest frequency, velocity frame and convention, channel width and any
> spectral smoothing, distance (and its source), whether i, PA and centre are fixed (from what) or free,
> emission-surface assumption (thin, conical, flared), fitted radial range, noise model, sampler settings,
> convergence rule and priors, and an error budget that includes distance and model systematics.

Counts come from the pack aggregates (447 papers; 295 protoplanetary-disk, 189 star-formation, 158 astrochemistry,
33 debris-disk, 20 evolved-star tags, papers can carry several) or my own grep of pack lines, as stated. Many
tagged papers only use a Keplerian mask or Keplerian-shifted stacking for chemistry, so software counts overstate
how often masses are measured. "(card)" marks details from a single methods card, each matching a verbatim quote.
About 20 off-topic papers are ignored (listed at the end). Full parameter table: `references/parameters.md`.

## When to use

- Dynamical stellar mass of a Class II star from a resolved CO/13CO/C18O disk, for comparison with
  evolutionary tracks (2017ApJ...844..158S, 2021ApJ...908...46B, 2017ApJ...846L..26W, 2025ApJ...986L..11S).
  For 23 Upper Sco K/M stars, five track sets "consistently underestimate stellar mass by >~25%"
  (2025ApJ...994..214T, card).
- Protostellar mass and Keplerian disk radius in embedded (Class 0/I) sources from PV diagrams or uv-plane
  disk models (2017ApJ...849...56A, 2024A&A...690A..46S, 2018ApJ...864L..25O, 2015ApJ...812...27A;
  separate disks in the VLA 1623 multiple, 2024A&A...687A.308S).
- Disk geometry (i, PA, v_sys, centre) and emission height from velocity maps: 12CO with a conical surface
  (2018ApJ...868..113T), 12CO with a two-power-law surface (2019Natur.574..378T), HCO+ with a flared surface
  (2020ApJ...891...48H), CS first-moment maps for geometry only, with M* fixed at 0.65 Msun (2018ApJ...864..133T).
- Rotation curves and deviations from Keplerian (pressure bumps, spirals, vortices, warps, planets, meridional
  flows) (2018ApJ...868..113T, 2019Natur.574..378T, 2021A&A...650A..59B, 2021A&A...648A..19W,
  2012ApJ...757..129R, 2024MNRAS.534.2904C).
- Low-S/N survey disks where a mass is only reachable by velocity-aligned stacking (2018A&A...616A.100Y,
  2021ApJ...908...46B).
- Building a Keplerian CLEAN mask or Keplerian-shifted spectral stack for weak lines (2013ApJ...774...16R,
  2024ApJ...965..147B, 2021ApJ...908..141H, 2026A&A...705A.198M, 2024ApJ...976..258K).
- Gas in debris belts or disks around evolved stars (2016ApJ...829....6W, 2013ApJ...776...77K,
  2026A&A...705A.201B, 2026A&A...705A.202M, 2016A&A...596A..92K, 2017A&A...597L...5B).
- Massive (proto)star disks, keeping in mind the disk mass is not negligible (2025NatAs...9.1833L,
  2019A&A...622A.206M, 2018ApJ...860..119G).

## When not to use

| Situation | Use instead |
|---|---|
| Rotation in an infalling envelope, centrifugal barrier, infall-rotation transition, streamers | `envelope-kinematics-pv` skill. The pack shows these models (centrifugal barrier M = r_CB v_CB^2 / 2G in 2019ApJ...873...73Z; IRE/FERIA and streamline models in 2025SciA...11.4512O, 2025ApJ...985..166K) but they are not Keplerian disk fits; 2025SciA...11.6953M notes its IRE model "is insensitive to the central mass" |
| Galaxy rotation curves, circumnuclear disks, AGN gas, orbits around Sgr A* | `galaxy-3d-kinematics` skill (3D tilted-ring or kinemetry); the galaxy and Galactic Centre papers tagged here (2015ApJ...811...39I, 2020ApJ...902...99I, 2024ApJ...970...74P) are out of scope |
| Unresolved disk, single spectrum only | A Keplerian double-peak line profile fit gives at most M sin^2 i with an assumed radius; say so, or treat the mass as a limit (2020ApJ...896..127K: "lower limit because inclination is unknown") |
| Ionized disk plus wind traced by radio recombination lines | A dedicated non-LTE disk-plus-wind model, not a plain Keplerian fit: 2020ApJ...897L..33J needed MORELI with a Keplerian ionized disk and an expanding wind (see step 1) |
| Only the dust disk geometry is needed | Continuum visibility fitting (`uv-plane-fitting` skill), which several papers use to fix i and PA before the kinematic fit (2020ApJ...891...48H, 2024ApJ...974..102S, 2024A&A...692A.155K) |
| Gas mass or temperature is the goal | `radiative-transfer-modelling` / `gas-mass-co-conversion`; Keplerian fits mostly fix those as nuisance parameters |

## Steps

1. **Pick the regime and tracer.**
   - Class II disks: 12CO for geometry and emission height (optically thick, elevated surface), 13CO/C18O
     or CN closer to the midplane for masses (2018A&A...616A.100Y stacks 13CO and C18O 3-2, card;
     2021ApJ...908...46B stacks 13CO, C18O and CN, card, assuming "different molecules follow same Keplerian
     rotation"). 13CO and C18O gave velocities within 20-30 m/s of each other in HD 142527 (2021A&A...650A..59B).
   - Embedded protostars: C18O, SO, HCO+, C17O along the disk major axis (2015ApJ...812...27A C18O;
     2018ApJ...864L..25O SO; 2014ApJ...786..114L HCO+; 2024A&A...687A.308S C17O, assumed to trace only the
     rotationally supported disks). Avoid lines dominated by envelope or outflow.
   - Massive protostars: hot-core lines such as CH3CN (2025NatAs...9.1833L). RRLs need more than a Keplerian
     fit: 2020ApJ...897L..33J modelled H21alpha with the non-LTE code MORELI as a Keplerian ionized disk plus
     an expanding wind; the same model without a wind "does not reproduce" the high-velocity centroid
     deviations, some centroid positional errors are large at high velocities, and the RRL masers are
     variable. Carry those caveats into any RRL mass (central mass 15 Msun there).
2. **Calibrate, self-calibrate, subtract continuum, image the cube** (see `self-calibration`,
   `continuum-subtraction`, `imaging-choices`).
   - Verify the spectral axis before fitting or stacking: rest frequency, velocity frame (LSRK) and
     convention. 2013ApJ...774...16R found that "the transformation to the absolute sky frequency in the Band 7
     measurement set" from the SV team was incorrect; cards flag rest frequencies as not stated (pack
     aggregates, 3) and 2017A&A...597L...5B gives no velocity reference (card note in the pack).
     2019ApJ...883...22C binned all line windows to matching 334 m/s LSRK channels (card).
   - Channels: about 0.1 km/s for 12CO disk cubes (2016ApJ...823L..18H, 2025ApJ...989....1Z); 160 m/s in
     2018ApJ...868..113T. State spacing and resolution separately (2024ApJ...966...63Y uses a spacing of half the
     resolution) and any smoothing, which correlates channels (2-channel Hanning in 2013ApJ...776...77K).
   - Weighting: Briggs robust 0.5 in 16 of the 23 pack bibcodes that state a robust value (my grep; e.g.
     2018ApJ...864..133T, 2026A&A...705A.202M); 1.0 in 2024ApJ...976..258K and 2026A&A...705A..49Z, 0.6 in
     2021A&A...648A..19W; natural for sensitivity (2018ApJ...868..113T, 2013ApJ...774...16R).
   - CLEAN with a Keplerian mask: the `keplerian_mask` script is named in 20 matched steps (+3 as "keplerian
     mask", pack aggregates), typically seeded with literature M*, PA, i (2020A&A...638A..38T tunes v_sys and
     line width to maximise S/N; 2024ApJ...976..258K rescales literature geometry to the adopted distance).
     2018ApJ...868..113T first fits a moment map, then re-cleans with a mask built from that fit and checks it
     "encompass[es] the whole emission".
3. **Fix the geometry you can measure independently.** Many papers fix i, PA and centre from continuum
   visibility fits and leave M* and v_sys free (2020ApJ...891...48H; 2024ApJ...974..102S; 2024A&A...692A.155K;
   2025ApJ...986L..11S fixes i = 49.9 deg; 2019ApJ...880...69Y fixes PA 138 deg, i 47 deg); 17 pack bibcodes
   state a fixed inclination (my grep). 2019Natur.574..378T instead puts a tight Gaussian prior on i (46.7 +-
   0.1 deg). Centre on the continuum peak (2018ApJ...869...59W, 2018A&A...616A.100Y). Fixing i transfers any
   inclination error straight into M*; near face-on, compact disks make literature M*, i and PA uncertain
   (2024ApJ...973..135H).
4. **Choose the kinematic method.**

| Method | When | How papers do it |
|---|---|---|
| A. Velocity map + `eddy` | Resolved, bright disk (12CO/13CO/HCO+) | `bettermoments` quadratic or Gaussian velocity map, then `eddy` Keplerian model with emcee; flat or conical surface z = r tan psi (2018ApJ...868..113T), flared z = z0 (r/1")^psi with psi an exponent (2020ApJ...891...48H), two-power-law surface with 10 free parameters (2019Natur.574..378T); also 2021A&A...648A..19W, 2024ApJ...974..102S, 2026A&A...705A.201B, 2026A&A...705A.202M |
| B1. Forward model, M* free (dynamical mass) | Best dynamical masses; moderate S/N | Parametric flared, vertically isothermal LTE disk, ray-traced with RADMC-3D, Fourier-sampled at the data uv points, MCMC; M* free with disk structure as nuisance (2017ApJ...846L..26W, 2017ApJ...835...17M, 2016ApJ...818..156C, 2019ApJ...883...22C with DiskJockey, card). `pdspy` (RADMC-3D + galario) with emcee, 15 free parameters (2025ApJ...994..214T, card) or with dynesty nested sampling (2024A&A...687A.308S, card). `csalt` models visibility spectra in LSRK per timestamp, convolves with the correlator spectral response and uses a spectral-covariance likelihood (2026A&A...705A..49Z, card) |
| B2. Forward model, M* fixed (structure, temperature, turbulence) | Gas structure is the goal | Same machinery with a prescribed mass: M* = 2.3 Msun fixed in 2015ApJ...813...99F, M* = 1.7 Msun in 2018ApJ...854..130W, masses fixed in 2020ApJ...895..109F; DISKFIT least squares on visibilities in 2024ApJ...976..258K. These are not dynamical-mass measurements |
| B3. Channel-map model (DISCMINER) | Kinematic substructure, residual maps | Orientation, M*, v_sys, upper and lower surfaces, intensity, line width and line slope fitted to channel maps (2023A&A...674A.113I); exoALMA residual maps from DISCMINER models (2026ApJ..1000L..15F, card). Its uncertainty is purely statistical (2025ApJ...984L..13H) |
| C. Velocity-aligned stacking | Faint survey disks | Shift each pixel by -v_kep cos(phi) sin(i), stack, grid-search M*, PA, i, v_sys for maximum S/N of the stacked line (2018A&A...616A.100Y); 2021ApJ...908...46B maximises S/N over M* and v_sys with i, PA, position and distance fixed (card) |
| D. PV rotation curve | Embedded, near edge-on protostars | Mean positions or ridge/edge per channel along the major axis, single or double power law in log R-log V; Keplerian if index ~0.5; `SLAM` MCMC (2017ApJ...849...56A uses only pixels above 5 sigma for the mean positions; 2024A&A...690A..46S, 2015ApJ...812...27A). Ridge and edge fits bracket the mass (2024ApJ...966...32E, 2025ApJ...992...18P) |
| E. Tilted rings | Massive protostellar disks | `3DBarolo` on the cube, power-law fit of v_rot(r), Keplerian enclosed mass (2025NatAs...9.1833L, card); see step 8 for converting enclosed mass to M* |
| F. Visual model comparison | Complex systems, illustrative only | Grid or hand-tuned models vs channel maps and PV (2019ApJ...873...73Z, 2018A&A...614A.113H, 2018ApJ...865..131L compares 0.05-0.4 Msun curves by eye). Authors themselves say this gives no fit quality |

5. **Set up the fit.**
   - Preserve each paper's fixed/free split rather than a generic list. M* free: 2017ApJ...846L..26W (Mdisk,
     Rdisk, gamma, T0, q, xi, M*, v_sys, i, PA, offsets), 2017ApJ...835...17M (M*, i, PA, r_c, T10, q, Mgas,
     xi, v_sys, offsets) and 2024A&A...687A.308S (M*, M_disk, R_disk, gamma, T0, q, a_turb, i, PA, v_sys,
     x0, y0). M* fixed: 2018ApJ...854..130W (free Mdisk, r_c, gamma, T0, q, xi, v_sys, i, PA with
     M* = 1.7 Msun) and 2015ApJ...813...99F.
   - Fixed values seen: X_CO = 1e-4, mu = 2.37 (2017ApJ...846L..26W, 2018ApJ...854..130W, 2025ApJ...994..214T);
     gamma = 1 fixed in 2016ApJ...823L..18H, 2019ApJ...883...22C, 2020ApJ...895..109F, but fitted in
     2017ApJ...846L..26W and 2018ApJ...854..130W; xi = 0.01 km/s (2016ApJ...823L..18H, 2017NatAs...1E.130Z).
     Widen a prior when walkers pile at its edge (2025ApJ...994..214T widened q from [0,1] to [0,2]).
   - Restrict the radial range: fit 0.2-2" (2020ApJ...891...48H), 0.33-1.4" (2024ApJ...974..102S), or exclude
     the inner ~5 beams "to mitigate the spatial resolution bias" (2025ApJ...994...98F) or the inner 100 au
     (2021A&A...650A..59B). Vary r_min and r_max to see if results move (2024MNRAS.534.2904C,
     2021A&A...650A..59B).
   - Handle contaminated channels and sides: mask 4.0-7.5 km/s LSRK after checking cloud maps
     (2019ApJ...883...22C, card); exclude 23 contaminated channels (2016ApJ...818..156C, card) or drop
     cloud-absorbed ranges from the likelihood (2026A&A...705A..49Z, card); cut envelope velocities and
     uv < 100-200 klambda (2024A&A...687A.308S); model the absorption as a 3-parameter Gaussian
     (2024A&A...687A.188K); weight to the blueshifted side under redshifted self-absorption (2017ApJ...843...27L).
     The ~30% 12CO absorption on AS 209's western side (2018ApJ...868..113T) is an absorption measurement, not a
     channel-exclusion fraction.
   - Velocity-map S/N cut before fitting: 5 sigma (2017ApJ...840...60B, 2024MNRAS.534.2904C,
     2026A&A...705A.201B) or 2.5 sigma (2020MNRAS.493L.108B). This is an intensity threshold on which pixels
     enter the map; keep it distinct from the per-pixel velocity uncertainties used in the likelihood.
   - Use a noise model that matches the data. 2016MNRAS.460.2933M writes the likelihood "taking into account
     the number of independent beams in the image and the correlation between adjacent channels";
     2019Natur.574..378T uses "only spatially independent pixels, those at least a beam FWHM apart"; csalt
     treats the spectral covariance explicitly (2026A&A...705A..49Z, card); neighbouring annuli are correlated
     within a beam (2018ApJ...864..133T). Model the correlation or count effective independent samples, and
     match the model's channelisation and smoothing to the data. Pixel-by-pixel chi2 on an oversampled map
     shrinks the posterior (recommendation following these papers; 2026A&A...705A.202M gives it as the reason
     its eddy errors are underestimated).
6. **Sample.** emcee is the sampler named most often in the matched steps (35, pack aggregates), a count of
   mentions, not a validated default. Others: dynesty (2024A&A...687A.308S, card), Metropolis-Hastings with
   Gibbs sampling, 3 chains (2016ApJ...829....6W), DiskJockey's Julia sampler (2019ApJ...883...22C, card),
   Levenberg-Marquardt (2024ApJ...976..258K), chi2 grids (2013ApJ...776...77K). State a convergence rule:
   median change < 5% over the last 500 steps (2026A&A...705A..49Z), slope of log M* < 1% over the last 1000
   (2025ApJ...994..214T, card), autocorrelation ~1000 steps (2019ApJ...874..136S). Report 16th-84th
   percentiles (2021A&A...648A..19W) but treat them as a floor.
7. **Inspect residuals and rotation curves.** Subtract the best Keplerian model from the velocity map
   (2024MNRAS.534.2904C, 2021A&A...648A..19W, 2021A&A...650A..59B) or image residual visibilities as channel
   maps and look for 3 and 5 sigma features (2026A&A...705A..49Z, 2024A&A...687A.308S, cards). For v_phi(r)
   fit deprojected spectra in annuli of about a quarter beam (2018ApJ...868..113T with eddy + celerite GP;
   2019Natur.574..378T for v_phi, v_R and v_Z); 2026A&A...705A.202M re-ran eddy ten times with the orientation
   drawn from the Keplerian-fit posterior. exoALMA residual maps came from DISCMINER models
   (2026ApJ..1000L..15F, card). Before naming a cause, report that "velocity residuals are model dependent, and
   the appearance of a Doppler-flip is therefore also model dependent" (2024MNRAS.534.2904C, which varied r_min)
   and that unresolved features "will underestimate the true depth" (2018ApJ...868..113T). Beam smearing alone
   gives 20-80 m/s deviations in a pure Keplerian model at 0.3" (2021A&A...650A..59B). Residual morphology
   alone does not identify a planet, spiral, vortex or warp.
8. **Build the error budget and the reported mass.** Add distance uncertainty in quadrature
   (2017ApJ...846L..26W adds 20 pc at 140 pc) or fit it with a Gaia-parallax prior (2025ApJ...994..214T, card),
   compare runs with different surfaces, masks, tracers and radial ranges, and report the spread.
   2025ApJ...994..214T reports Delta chi2 intervals because standard-deviation errors were 2-3x smaller (card);
   2019Natur.574..378T found systematics 2-3 times the statistical errors on its velocities. A rotation curve
   measures the enclosed mass. Where the disk and surrounding gas are massive, report enclosed mass and stellar
   mass separately and say which gravity model was used: 2025NatAs...9.1833L finds M_cl = 7.6 +- 1.4 Msun
   enclosed, then M* = M_cl - M_disk - sum(M_gas) = 4.89 Msun (card).

## Parameter defaults and ranges

"Typical value" is the value most often reported in the pack lines, not an independently validated default.
"Supporting pack entries" is my count (grep) of distinct bibcodes in the pack's parameter, assumption and
excerpt lines that state the setting, not a paper-level prevalence. More rows (masks, priors, grids, PV
thresholds, gas structure, line widths) and full example lists: `references/parameters.md`.

| Parameter | Typical value (reported settings) | Range seen | Supporting pack entries | Examples |
|---|---|---|---|---|
| Channel width | 0.1 km/s (12CO disks) | 26 m/s to 1.7 km/s | 28 | 2016ApJ...823L..18H, 2018ApJ...868..113T (0.16), 2017ApJ...851..132C (0.4), 2026A&A...705A.201B (26 m/s) |
| Briggs robust | 0.5 | -1 to 2, natural | 23 robust + 3 natural | 2018ApJ...864..133T, 2021A&A...648A..19W (0.6), 2024ApJ...976..258K (1.0), 2026A&A...705A.198M (0.5 or 2) |
| Inclination | fixed from continuum or literature | prior or free | 17 fixed | 2020ApJ...891...48H, 2019A&A...625A.118K (51.7 deg); prior 2019Natur.574..378T; free 2017ApJ...846L..26W |
| Distance | Gaia (DR2, then DR3) | 59 pc to 6.7 kpc | 6 Gaia | 2018ApJ...862L...2F (59 pc), 2020ApJ...895..109F (DR2), 2026A&A...705A..49Z (DR3), 2021A&A...650A.142M (6.7 kpc) |
| Emission surface, 12CO conical | psi ~13-15 deg (z/r = tan psi ~0.23-0.27) | 13.1-15 deg | 2 | 2018ApJ...868..113T, 2013ApJ...774...16R |
| Emission surface, flared | z = z0 (r/1")^psi, psi an exponent | HCO+ z0 0.127", psi 0.81; 12CO/HCO+ z0 0.33", psi 0.76 | 3 | 2020ApJ...891...48H, 2021AJ....162...99F, 2019Natur.574..378T |
| Annulus width | 1/4 beam | 1/5 beam to 2x beam minor axis | 13 | 2018ApJ...868..113T, 2019Natur.574..378T, 2026A&A...705A.202M (20% beam) |
| Walkers / steps / burn-in | see examples | walkers 16-1000, steps 300-40,000 | 17 | 2020ApJ...891...48H (48/3500/500), 2021A&A...648A..19W (200/5000+5000), 2025ApJ...994..214T (200, burn >= 1000) |
| M* prior | broad uniform | U(0,5) Msun; 5-15 Msun massive | 5 | 2025ApJ...994...98F, 2019ApJ...884L..56T (0.1-2), 2019A&A...622A.206M |
| Turbulent broadening xi / v_turb | 0.01 km/s | n/a | 2 | 2016ApJ...823L..18H, 2017NatAs...1E.130Z |

Line widths (xi, intrinsic width, Doppler b, "turbulence") are not interchangeable: check sigma vs b
(sqrt(2) sigma) vs FWHM and whether thermal broadening is included before comparing (general practice).

## Software

Counts are matched steps naming the tool (pack aggregates). They show how often a tool is named, not how often
a method is used.

| Tool | Count | Used for |
|---|---|---|
| CASA (`tclean`, `uvcontsub`, `imfit`, `simobserve`) | 101 (+ tclean 24, casa tclean 7, uvcontsub 13, casa imfit 4) | calibration, Keplerian-masked imaging, synthetic observations of models (2020ApJ...893...51S, 2026A&A...705A.202M) |
| eddy | 39 | Keplerian fits to velocity maps, emission surfaces, rotation curves (2018ApJ...868..113T, 2019Natur.574..378T, 2021A&A...650A..59B) |
| emcee | 35 | sampling Keplerian and disk-model posteriors (2020ApJ...891...48H, 2025ApJ...994...98F, 2026A&A...705A.201B) |
| GoFish | 32 | Keplerian-shifted stacking and radial profiles for weak lines (2024ApJ...965..147B, 2024ApJ...976..258K); Kepler-correcting Stokes I and V for Zeeman fits (2021ApJ...908..141H, see Pitfalls) |
| RADMC-3D (+ radmc3dpy) | 29 | ray-traced line cubes for forward models and beam-smearing tests (2016ApJ...818..156C, 2017ApJ...846L..26W, 2021A&A...650A..59B) |
| bettermoments | 26 | quadratic or Gaussian velocity maps feeding eddy (2020ApJ...891...48H, 2026A&A...705A.202M) |
| keplerian_mask (+ "keplerian mask" 3) | 20 | Keplerian CLEAN and moment masks (2021A&A...648A..19W, 2026A&A...705A.198M) |
| LIME, RATRAN, MCFOST | 11, 3, 5 | line radiative transfer (LIME: 2012ApJ...757..129R, 2013ApJ...774...16R, 2018A&A...614A.113H) |
| VISIBLE | 9 | matched-filter detection of weak lines with Keplerian-mask templates (2024ApJ...976..258K); not a mass method |
| DISCMINER | 7 | channel-map Keplerian models and residual maps (2023A&A...674A.113I, 2025ApJ...984L..13H, 2026ApJ..1000L..15F card) |
| pdspy, galario, csalt, DISKFIT, vis_sample (+ vissample 2), DiskJockey | 5, 4, 3, 5, 4, 3 | uv-plane disk fits (pdspy: 2025ApJ...994..214T, 2024A&A...687A.308S, cards; csalt: 2026A&A...705A..49Z, card; DISKFIT: 2024ApJ...976..258K; vis_sample: 2016ApJ...823L..18H; DiskJockey: 2019ApJ...883...22C, card) |
| Miriad, GILDAS (+ iram-gildas 2) | 5, 5 | older imaging and PV work (2020ApJ...898...10T, 2019A&A...632L..12H) |
| FERIA, SLAM, pvextractor, celerite, MORELI, 3DBarolo, disksurf | 3, 3, 4, 2, 2, not in aggregates, not in aggregates | IRE models, PV rotation curves, PV cuts, GP rotation curves, non-LTE RRL disk-plus-wind models, tilted rings, surface extraction (2025SciA...11.4512O, 2024A&A...690A..46S, 2018ApJ...868..113T, 2020ApJ...897L..33J, 2025NatAs...9.1833L card, 2025ApJ...984L..10G) |

## Pitfalls

- **Mass-inclination degeneracy.** "The inclination and the stellar mass are degenerate" (2013ApJ...776...77K
  took i from the best-fit mass); inclination poorly constrained by the disk model (2015ApJ...812...27A,
  2017A&A...597L...5B, 2018A&A...616A.100Y); edge-on assumed to get a minimum mass (2017NatAs...1E.172L,
  2020ApJ...896..127K). Some masses are quoted without an inclination correction (2025A&A...694A..92B,
  2021A&A...650A.142M) or as M = 0.82 Msun / sin^2 i (2019ApJ...881..112O). If i comes from the continuum, say
  so and propagate its error.
- **Distance.** M is proportional to the adopted distance (2020ApJ...894...74B); several papers state the
  error excludes distance (2024ApJ...967...15K). Check that distances are Gaia-era for older papers.
- **Underestimated errors.** Posterior widths far below run-to-run scatter (2021A&A...648A..19W); eddy errors
  "below 1%" but "likely underestimated" because pixel correlation was ignored (2026A&A...705A.202M; also
  2026A&A...705A.201B); for a 0.99 Msun kinematic mass "the true uncertainties are closer to ~10%, due to
  systematics" (2025ApJ...991..176W, card); DISCMINER uncertainty is purely statistical (2025ApJ...984L..13H,
  pack assumption line); DISKFIT errors
  unreliable where parameters are strongly coupled (2024ApJ...976..258K); systematics from midplane
  temperature and flux calibration dominate (2020ApJ...895..109F); calibration uncertainty left out of the
  MCMC (2020ApJ...892...99C).
- **Radial range.** The fitted mass depends on which radii enter: 2.53 +- 0.04 (100-200 au), 2.29 +- 0.07
  (> 200 au) and 2.36 +- 0.07 Msun (adopted, 100-400 au) for the HD 142527 binary (2021A&A...650A..59B).
- **Spectral axis.** A wrong sky-frequency transformation (2013ApJ...774...16R) or an unstated rest frequency
  or frame shifts v_sys and misaligns stacks. Check it before fitting.
- **Pressure and self-gravity.** A rotation curve cannot separate large-scale pressure support from M*
  (2018ApJ...868..113T). In simulated ARKS observations with input 1.91 Msun, fits returned 1.93 Msun for the
  Keplerian and one pressure-supported model and 1.80 Msun for the other (2026A&A...705A.202M). Disk mass is
  usually neglected (2019ApJ...873...73Z, 2019A&A...622A.206M), which fails for massive disks (disk-to-star
  0.2-0.6 in 2025NatAs...9.1833L, card, where enclosed mass 7.6 Msun becomes M* = 4.89 Msun after subtracting
  disk and gas); 2024ApJ...970..153A fits stellar, pressure and self-gravity terms together.
- **Beam smearing.** Not corrected in the inner 90-100 au in 2018ApJ...864..133T. In 2025ApJ...994...98F the
  resolution bias on intensity/temperature "can extend up to 8 times the size of the beam" with intensity
  underestimated by up to 50%; for the mass fit the same paper excludes the inner ~5 beams. In
  2025ApJ...986L..11S EDDY on the moment-1 map gave 0.043 Msun while the 12CO visibility fit gave 0.092 Msun,
  and the authors note EDDY "does not take the beam convolution into account, which may result in smaller
  stellar mass" (card). Beam smearing plus pressure gradients could not be told apart from a vortex in HD 142527
  (2021A&A...650A..59B), and it flattens extracted v_phi, so the true profile "is likely steeper than the
  extracted one" and deviations are probably underestimated (2026A&A...705A.202M). 2024ApJ...970..153A corrects v_phi with mock-cube factors.
- **Emission height.** 2024MNRAS.534.2904C assumed elevated emission surfaces for four MAPS disks (GM Aur,
  HD 163296, IM Lupi, MWC 480) and flat Keplerian disks for the rest; it did not measure a mass or PA bias from
  that choice. As general modelling guidance, fitting an elevated tracer such as 12CO with a thin disk can
  shift the fitted geometry, so test a surface model. Thin-disk stacking can overestimate the mass: "the stellar
  mass could be overestimated by 20% to 30% with our method, when a disk is highly inclined (i = 80 deg)"
  (2021ApJ...908...46B, card, synthetic disks); the pack line for the same paper calls the scale-height effect
  small (<3%) under its adopted assumptions.
- **Residuals are model dependent.** Doppler-flips and other residual features depend on the subtracted model
  (2024MNRAS.534.2904C), and unresolved features are shallower than they really are (2018ApJ...868..113T).
- **Envelope, infall, jets.** Cannot distinguish infall+Keplerian from pure Keplerian at low S/N
  (2013A&A...560A.103M); embedded masses may be upper limits (2018ApJ...864L..25O) or confused by the jet
  (2024ApJ...961..228S); PV mean-position methods underestimate the break radius at low resolution
  (2015ApJ...812...27A); ridge fitting underestimates and edge fitting overestimates the mass
  (2025ApJ...992...18P); a proto-brown-dwarf candidate stayed "tentative" with 0.27-0.30 Msun from PV curves
  (2018ApJ...865..131L).
- **Missing flux and cloud contamination.** Missing large scales bias rotation at large radii
  (2014ApJ...796..131O; ~25% filtered in 2017A&A...597L...5B); foreground cloud absorption (2018ApJ...868..113T,
  2020ApJ...894...74B, 2024ApJ...969..165D, 2020ApJ...904L...6A), negligible in the central CO of a highly
  inclined disk (2021ApJ...908..250H).
- **Low S/N stacking.** Stellar mass can be overestimated for fluxes below about 400 mJy km/s
  (2018A&A...616A.100Y).
- **Stacking for polarisation.** Stacking red and mirrored blue sides "would destroy any Stokes V signal from a
  vertical magnetic field" (2021ApJ...908..141H). Keep red and blue sides separate when polarity matters, and
  fit only unblended parts of hyperfine lines: that paper used only the low-frequency part of line 5 and the
  high-frequency part of line 7.
- **Maser and RRL disks.** Keplerian-only models miss the wind; maser variability and large high-velocity
  centroid errors limit the mass (2020ApJ...897L..33J); 2D Gaussian centroids underestimate the maser disk size,
  giving a lower enclosed mass (2023ApJ...953L...6P).
- **Binaries and circumbinary disks.** The fit gives the total enclosed mass (2020ApJ...898...10T assumed
  equal masses totalling 0.5 Msun; the fitted Mstar in 2020ApJ...905...89Y is the total binary mass);
  circumbinary disks leave non-Keplerian residuals (2024MNRAS.534.2904C, 2020ApJ...905...89Y). Combine with RV
  orbits for component masses (2016ApJ...818..156C).
- **Conventions.** Inclination and PA conventions differ (2019ApJ...873...73Z defines edge-on as i = 0;
  2018A&A...614A.113H quotes i = 110 deg; 2024A&A...687A.311A measures PA to the blueshifted semi-major axis).
  Convert before comparing.
- **Hand-tuned models.** Many models are "not unique nor optimized" (2012ApJ...757..129R,
  2013ApJ...774...16R) or chosen by eye (2019ApJ...873...73Z, 2018A&A...614A.113H, 2018ApJ...865..131L). Do not
  quote them as fits.
- **Unstated settings.** Cards flag self-calibration intervals (24, plus variants), CASA version (23, plus
  variants), image and cell size (13), flux-scale uncertainty (7), line-free channels (more than 100 across
  phrasings) and rest frequencies (3) as not stated (pack aggregates). Write them down.

## Verification checks

What papers did:
- Recover a known mass from synthetic data: 0.99 +- 0.02 Msun for a 1 Msun model (2025ApJ...994...98F);
  1.93 Msun for a 1.91 Msun input after simobserve and tclean, processed like the data (2026A&A...705A.202M);
  tests on 30 blank-field synthetic images and 24 model disks for the stacking method (2018A&A...616A.100Y,
  card).
- Refit with different surface assumptions (flared, thin, no continuum subtraction): the three radial v_rot
  profiles are "consistent within 3 sigma of one another" (2018ApJ...868..113T). This validates the rotation
  curve, not the mass. 2019Natur.574..378T compared a parametric with a non-parametric surface and with Z1 = 0,
  and refit with v_R fixed to 0 ("no change" in v_phi).
- Refit with and without beam convolution and with velocity errors x10 (2021A&A...648A..19W).
- Compare radial ranges and fitting procedures: features "present independently of the exact fitting
  procedure" while the mass moved with radius (2021A&A...650A..59B).
- Compare image-plane and visibility-plane masses: 0.043 vs 0.092 Msun in 2025ApJ...986L..11S (card), so the
  check can fail; compare masses from different lines: "80% of the measurements from different line data agree
  on a level better than 1 sigma" (2021ApJ...908...46B, card); 12CO, 13CO and joint fits "all agree within
  uncertainties" (2025ApJ...994..214T, card); 13CO and C18O PV curves gave 0.27 and 0.30 Msun
  (2018ApJ...865..131L).
- Vary a fixed structure parameter: the dynamical mass "remained the same" for floating q, q = 0.50 and
  q = 0.75 (2019ApJ...883...22C, card); run the fit at the adopted M* and +-1 sigma (2022A&A...662A.121R).
- Test competing velocity laws: single vs double power law, reduced chi2 1.6 vs 4.0 (2017ApJ...849...56A);
  infalling-rotating envelope rejected (2018ApJ...864L..25O); pure Keplerian rejected (2019ApJ...873...73Z,
  and for the ARKS gas ring, 2026A&A...705A.202M); no-wind model rejected for an RRL disk (2020ApJ...897L..33J).
- Residual channel maps from residual visibilities, checked at 3 and 5 sigma (2026A&A...705A..49Z,
  2024A&A...687A.308S, cards); overlay isovelocity contours or model PV curves on channels
  (2020ApJ...891...48H, 2020ApJ...898...10T).
- Convergence: multiple chains agree, model matches data to ~10% (2016ApJ...829....6W); reduced chi2 0.72
  (2015ApJ...812...27A); explicit stopping rules (2026A&A...705A..49Z, 2025ApJ...994..214T card).
- Gas geometry vs continuum geometry: PA, i and offsets "consistent with those measured for the continuum"
  (2026A&A...705A.201B; also 2026A&A...705A.202M).
- Independent masses: SED fit (2019ApJ...873...73Z), earlier lower-resolution data (2025NatAs...9.1833L),
  stellar-model mass (2026A&A...705A.201B).
- Mask covers all emission (2018ApJ...868..113T); radial profiles also made without the Keplerian mask
  (2024ApJ...976..258K).

What a careful referee adds:
- Is the quoted error dominated by distance and inclination, and are those propagated?
- Does M* change when r_min, r_max, surface height or tracer change (2024MNRAS.534.2904C varies r_min;
  2021A&A...650A..59B shows it can)?
- Does the likelihood account for correlated pixels and channels (2016MNRAS.460.2933M, 2019Natur.574..378T),
  and does the model match the data's channelisation and smoothing?
- Were rest frequency, velocity frame and convention checked and reported?
- Were absorbed or cloud-contaminated channels excluded or modelled, and is the fit symmetric between red and
  blue sides?
- For embedded sources, is the fitted region inside the Keplerian radius and free of envelope/outflow, and
  was the mass from ridge or edge points?
- For massive disks, is the reported number the enclosed mass or the stellar mass?
- Is i from the gas consistent with i from the continuum (2025ApJ...986L..11S reports "consistent solutions of
  inclination and position angle to those from the continuum", card)?
- Was a convergence rule stated, and are residual features shown to survive changes to the subtracted model?

## Source cards

Full list: `references/sources.md` (generated). Most informative for this technique:

- 2018ApJ...868..113T (eddy, conical surface, GP rotation curve, surface tests)
- 2019Natur.574..378T (eddy surface fit, independent pixels, 3D velocities, systematics vs statistics)
- 2020ApJ...891...48H (bettermoments + eddy on HCO+, fixed geometry, emcee settings)
- 2021A&A...648A..19W (eddy runs, underestimated errors, beam tests)
- 2021A&A...650A..59B (radial-range dependence of mass, beam smearing vs vortex)
- 2026A&A...705A.202M (eddy on a debris gas ring, recovery test, underestimated errors)
- 2025ApJ...986L..11S (image vs visibility masses for a brown dwarf)
- 2025ApJ...994..214T (pdspy uv fits for 23 stars, convergence rule, tracks vs dynamical masses)
- 2026A&A...705A..49Z (csalt with spectral covariance, cloud ranges excluded, stopping rule)
- 2024A&A...687A.308S (pdspy + dynesty for a protostellar multiple, channel and uv cuts)
- 2017ApJ...846L..26W (RADMC-3D + emcee visibility fit, M* free, distance in quadrature)
- 2016ApJ...818..156C (disk mass combined with binary RV orbit)
- 2019ApJ...883...22C (DiskJockey dynamical mass, cloud channels)
- 2021ApJ...908...46B (stacked survey masses, thin-disk bias)
- 2018A&A...616A.100Y (velocity-aligned stacking grid, low-flux bias)
- 2025ApJ...994...98F (recovery test, beam-bias correction)
- 2024ApJ...970..153A (pressure and self-gravity in v_phi)
- 2017ApJ...849...56A (PV double power law, Keplerian radius)
- 2024A&A...690A..46S (SLAM ridge and edge fits)
- 2015ApJ...812...27A (C18O disk model, M sin^2 i)
- 2016MNRAS.460.2933M (likelihood with independent beams and channel correlation)
- 2024MNRAS.534.2904C (residuals, r_min dependence, circumbinary)
- 2025NatAs...9.1833L (3DBarolo for a massive disk, enclosed vs stellar mass)
- 2021ApJ...908..141H (GoFish Kepler correction for Zeeman, stacking caveat)
- 2020ApJ...895..109F (systematics dominate)

Off-topic papers in the pack (regex-tagged, ignored here): 2013ApJ...768L..38H, 2015ApJ...811...39I,
2013PASJ...65..100I, 2020ApJ...902...99I and 2017MNRAS.468.1769F (galaxy nuclei and clouds);
2017ApJ...837...93Y, 2017ApJ...842...94T, 2017ApJ...850L...5T, 2019ApJ...871L...1T, 2020PASJ...72L...5T,
2024ApJ...970...74P and 2025A&A...704A...7P (Galactic Centre orbits and black holes); 2021AJ....162...14A
(stellar astrometry); 2019NatAs...3..408D (OH/IR binary); 2023PASJ...75..225M (HII region ring);
2024A&A...689A..85G (JWST-led); 2024ApJ...966..117X (synthetic disk winds); 2015ApJ...808..102K (CARMA,
Toomre Q); 2014A&A...569A..11S and 2016ApJ...830L..37I (core and hot-corino studies without disk fits).

=== references/parameters.md ===
# Parameter table: keplerian-disk-kinematics (full version)

Companion to `../SKILL.md`. "Typical value" is the value most often reported in the evidence pack lines, not an
independently validated default. "Supporting pack entries" is my count of distinct bibcodes in the pack's
parameter, assumption and excerpt lines that state the setting (a grep over those lines, not a paper-level
prevalence). Pack: 447 papers, 2012-2026. Many tagged papers use a Keplerian mask or Keplerian-shifted stacking for
chemistry and never fit a mass, so imaging rows include them; fitting rows mostly come from mass or geometry fits.

## Imaging and spectral setup

| Parameter | Typical value (reported settings) | Range seen | Supporting pack entries | Examples |
|---|---|---|---|---|
| Channel width | 0.1 km/s for 12CO disk cubes | 26 m/s instrumental width to 1.7 km/s | 28 | 2016ApJ...823L..18H (0.1), 2025ApJ...989....1Z (0.1 12CO, 0.2 others), 2025ApJ...989....3D, 2018ApJ...868..113T (0.16), 2024ApJ...967...68H (0.2), 2024ApJ...964..190L (0.20-0.43 per line), 2017ApJ...851..132C (0.4), 2026A&A...705A.201B (26 m/s instrumental width), 2024ApJ...975...72B (0.9 and 1.7) |
| Channel spacing vs resolution | state both | spacing half the resolution | 1 | 2024ApJ...966...63Y (13CN spacing 0.34 km/s, "half the velocity resolution") |
| Spectral resampling of stacked spectra | finer than data for line-centre fits | 40 m/s, 16x finer | 1 | 2019Natur.574..378T |
| Briggs robust | 0.5 (16 of 23 bibcodes that state a robust value, some among several values) | -1 to 2, natural | 23 robust + 3 natural | 0.5: 2026A&A...705A.202M, 2018ApJ...864..133T, 2024ApJ...972...88L, 2025ApJ...984L..18T, 2024RAA....24g5017M; 1.0: 2024ApJ...976..258K, 2026A&A...705A..49Z; 0.6: 2021A&A...648A..19W; 0.3: 2026MNRAS.545f2150S; 0.0 (also tested -2 and 2): 2024A&A...682A..55M; 0.5 or 2: 2026A&A...705A.198M; natural: 2018ApJ...868..113T, 2013ApJ...774...16R, weak lines in 2024ApJ...976..258K |
| Keplerian mask smoothing / padding | Gaussian kernel | sigma 0.7"; 0.5-1.25 beams | 2 | 2013ApJ...774...16R (0.7"), 2025NatAs...9.1486L (0.5, 1.25, 0.75 beam per isotopologue, "chosen by visual inspection") |
| Keplerian mask line width | power law in radius | V0 0.22-0.25 km/s at 100 au, q 0.3; dV0 500 m/s | 2 | 2021ApJ...911..150P, 2023ApJ...956..135W |

## Geometry, distance and emission surface

| Parameter | Typical value (reported settings) | Range seen | Supporting pack entries | Examples |
|---|---|---|---|---|
| Inclination | fixed from continuum or literature | prior, or free in forward models and some eddy fits | 17 fixed | fixed: 2020ApJ...891...48H, 2025ApJ...986L..11S (49.9 deg), 2019A&A...625A.118K (51.7 deg), 2021A&A...650A..59B (27 deg), 2019ApJ...884L..56T (5.8 deg), 2024A&A...692A.155K (i, PA, centre from continuum); Gaussian prior 46.7 +- 0.1 deg: 2019Natur.574..378T; free: 2016ApJ...829....6W, 2017ApJ...846L..26W, 2018ApJ...864..133T, 2026A&A...705A.201B |
| Distance | Gaia (DR2 in older papers, DR3 in newer) | 59 pc to 6.7 kpc | 6 Gaia + many fixed literature values | 2018ApJ...862L...2F (59 pc), 2021A&A...648A..19W (162 pc), 2017ApJ...844..158S (131/119/140 pc), 2024ApJ...967...15K (2.38 and 1.7 kpc), 2021A&A...650A.142M (6.7 kpc); Gaia DR2 2020ApJ...895..109F; Gaia DR3 2026A&A...705A..49Z; cloud distances from Zucker et al. 2026A&A...710A.140M |
| Emission surface, 12CO conical | psi ~13-15 deg (z/r = tan psi ~0.23-0.27) | 13.1-15 deg | 2 | 2018ApJ...868..113T (psi 13.1 deg), 2013ApJ...774...16R (~15 deg) |
| Emission surface, flared power law | z = z0 (r/1")^psi, psi an exponent | HCO+ z0 0.127", psi 0.81; 12CO and HCO+ z0 0.33", psi 0.76; 12CO Z0 265 mas, phi 1.29 | 3 | 2020ApJ...891...48H (HCO+, z/r = 0.127 at r = 1"), 2021AJ....162...99F (PDS 70, used for masks), 2019Natur.574..378T (two-power-law surface, 10 free parameters) |
| Emission surface, exponentially tapered | z0 (r/1")^psi exp(-(r/r_taper)^q_taper) | front and back sides | 3 | 2024A&A...682A..55M, 2026MNRAS.552g1700S, 2025A&A...694A.108P |
| Emission surface, assumed ratio | z/r = 0.13 | 0.13-0.4 | 2 | 2023PASJ...75..424O (0.13), 2025NatAs...9.1486L (0.4 for a water-line mask) |
| Emission surface, thin / midplane | geometrically thin | n/a | 31 (thin, flat or midplane) | 2018A&A...616A.100Y, 2019ApJ...880...69Y, 2021A&A...650A..59B (height "could not precisely constrain"), 2026A&A...705A.202M (elevated fits gave heights consistent with zero), 2024A&A...692A.155K (upper and lower surfaces indistinguishable) |
| PA convention | state it | north to redshifted or blueshifted major axis | 2 | 2024A&A...687A.311A (to the blueshifted semi-major axis), 2020ApJ...901...71S (PA_red) |

## Fitting and sampling

| Parameter | Typical value (reported settings) | Range seen | Supporting pack entries | Examples |
|---|---|---|---|---|
| Fitted radial range | outside the inner few beams | 0.065-0.7" to 0.26-3.75" | 8 | 2020ApJ...891...48H (0.2-2"), 2024ApJ...974..102S (0.33-1.4"), 2019ApJ...884L..56T (0.26-3.75"), 2025NatAs...9.1672Y (0.065-0.7"), 2025ApJ...994...98F (inner ~5 beams excluded), 2021A&A...650A..59B (inner 100 au discarded), 2020ApJ...905...89Y (r > 0.5" for a 0.45" beam) |
| Annulus width (rotation curve, stacking) | 1/4 beam | 1/5 beam to 2x beam minor axis; 4 au; 0.02-0.05" | 13 | 2018ApJ...868..113T, 2019Natur.574..378T (25 mas, ~1/4 beam), 2021ApJS..257....6G, 2024ApJ...965..147B, 2026A&A...705A.202M (20% of beam), 2023A&A...675A.131T (2x minor axis, step 1x), 2018ApJ...864..133T (4 au), 2024ApJ...970..153A (0.05"), 2026A&A...705A.201B (0.02") |
| Pixels in the likelihood | spatially independent | at least a beam FWHM apart | 1 | 2019Natur.574..378T |
| Velocity-map S/N cut | 5 sigma | 2.5-5 sigma | 4 | 2017ApJ...840...60B, 2024MNRAS.534.2904C, 2026A&A...705A.201B (peak < 5 sigma masked), 2020MNRAS.493L.108B (2.5) |
| Surface-extraction S/N clip | per tracer | 5.0 (12CO), 3.5 (13CO), 3.0 (CS) | 1 | 2025ApJ...984L..10G (disksurf, 5 iterations) |
| Sampler walkers / steps / burn-in | see examples | walkers 16-1000, steps 300-40,000, burn-in 50-80,000 | 17 | 2020ApJ...891...48H (48/3500/500), 2021A&A...648A..19W (200/5000 burn + 5000), 2019Natur.574..378T (64/10,000 burn + 10,000), 2025ApJ...994...98F (32/1000/300 for M*), 2025ApJ...994..214T (200, burn-in >= 1000), 2026A&A...705A..49Z (90, 250 burn), 2024A&A...687A.311A (256/40,000/6300), 2026MNRAS.552g1700S (230, burn-in 80,000 for 12CO), 2019ApJ...878..113H (1000 walkers), 2026ApJ..1003...64Y (100/15,000/2000) |
| Convergence rule | rarely stated | see examples | 4 | 2026A&A...705A..49Z (median change < 5% over last 500 steps), 2025ApJ...994..214T (slope of mean and median log M* < 1% over last 1000 steps, card), 2019ApJ...874..136S (autocorrelation ~1000 steps; walkers with chi2 - chi2min > 44 discarded), 2026A&A...705A.201B (visual) |
| M* prior | broad uniform | U(0,5) Msun; 0.1-2 Msun; 5-15 Msun massive; Gaussian 1.5 +- 0.15 | 5 | 2025ApJ...994...98F, 2019ApJ...884L..56T, 2019A&A...622A.206M, 2020MNRAS.491.1335R; walkers seeded from a Chabrier IMF in 2025ApJ...994..214T (card) |
| Inclination and distance priors | geometric on i, Gaussian on d | d ~ N(145, 20) pc; Gaussian in Gaia parallax | 2 | 2016ApJ...818..156C (sin(i)/2 prior on i, card), 2025ApJ...994..214T (parallax Gaussian of width 2 log(2) sigma_Gaia, card) |
| Stacking grid | M* step 0.1 Msun, i step 5 deg | M* 0.1-3, PA 0-355, i 5-85, v_sys step 0.1 km/s | 1 | 2018A&A...616A.100Y |
| Model grid (debris CO) | 5 parameters | M* 0.9-3.0 step 0.3, i 25-39 step 2 | 1 | 2013ApJ...776...77K |
| Channel and uv exclusions | exclude envelope or cloud ranges | velocity windows; uv < 100-200 klambda | 4 | 2024A&A...687A.308S (3.25-5.5 km/s for A; uv < 100 klambda for B, < 200 for W), 2019ApJ...883...22C (4.0-7.5 km/s, card), 2026A&A...705A..49Z (cloud ranges excluded from the likelihood, card), 2019ApJ...884...42S (channels near cloud v_sys ignored) |
| PV mean-position intensity threshold | 5 sigma | 5 sigma | 3 | 2017ApJ...849...56A, 2023ApJ...958...98F (filtered-out channels also excluded), 2019Sci...366...90A |
| PV power-law index | 0.5 (Keplerian) | fitted 0.50-0.53; outer ~1.2; ~1 for infall plus rotation | 4 | 2017ApJ...849...56A (0.50, outer 1.22), 2015ApJ...812...27A (0.53), 2024A&A...690A..46S (fixed 0.5), 2024ApJ...966...32E (p ~0.5 vs ~1) |

## Disk structure in forward models

| Parameter | Typical value (reported settings) | Range seen | Supporting pack entries | Examples |
|---|---|---|---|---|
| Gas structure | X_CO 1e-4, mu 2.37 | gamma fixed at 1 or fitted | 11 | X_CO/mu: 2017ApJ...846L..26W, 2018ApJ...854..130W, 2015ApJ...813...99F, 2025ApJ...994..214T, 2019ApJ...874..136S; gamma = 1 fixed: 2019ApJ...883...22C, 2015ApJ...798...85P, 2016ApJ...823L..18H, 2020ApJ...895..109F, 2015ApJ...806..154C, 2020ApJ...900....7H; gamma fitted: 2017ApJ...846L..26W, 2018ApJ...854..130W, 2024A&A...687A.308S |
| Isotopologue abundance | per paper | C17O = CO/2240 | 1 | 2024A&A...687A.308S |
| Temperature exponent q range | [0,1] | widened to [0,2] when walkers pile at q = 1 | 1 | 2025ApJ...994..214T |
| Turbulent broadening xi / v_turb | 0.01 km/s | n/a | 2 | 2016ApJ...823L..18H (xi), 2017NatAs...1E.130Z (v_turb) |
| Other line-width parameters (not interchangeable) | as defined per paper | see examples | 5 | 2013ApJ...776...77K (intrinsic line width 0.1 km/s), 2015ApJ...798...85P (b = 50 m/s), 2018A&A...616A..34H (micro-turbulence ~0.5 km/s), 2018A&A...614A.113H (turbulence 1 km/s, AGB), 2026A&A...705A..49Z (purely thermal, card) |

Line widths: the pack mixes turbulent xi, intrinsic line width, Doppler b and "turbulence" without a common
convention. Before comparing values, check whether each is a sigma, a Doppler b (sqrt(2) sigma) or a FWHM and
whether thermal broadening is included (general practice).

=== RECONCILIATION (first review, fixes to keep) ===
# Reconciliation: keplerian-disk-kinematics
- SR-01 | FIXED | Split the geometry examples by tracer and quantity: 12CO conical (2018ApJ...868..113T), HCO+ flared (2020ApJ...891...48H), CS moment-1 geometry with M* fixed at 0.65 Msun and no emission height (2018ApJ...864..133T); the old "Emission surface (12CO)" row is now three rows with the HCO+ result labelled as HCO+.
- SR-02 | FIXED | Method B split into B1 (M* free: 2017ApJ...846L..26W, 2017ApJ...835...17M, 2016ApJ...818..156C, 2019ApJ...883...22C) and B2 (M* fixed: 2015ApJ...813...99F 2.3 Msun, 2018ApJ...854..130W 1.7 Msun, 2020ApJ...895..109F); step 5 lists each paper's own fixed/free split; gamma shown as fixed in four papers and fitted in 846W and 854W.
- SR-03 | FIXED | 2017ApJ...849...56A moved to method D and a separate "PV mean-position intensity threshold" row; velocity-map cut now cites 2017ApJ...840...60B, 2024MNRAS.534.2904C, 2020MNRAS.493L.108B and is described as an intensity threshold distinct from velocity uncertainties.
- SR-04 | FIXED | The ~30% figure is now stated as cloud absorption of 12CO on the western side of AS 209, explicitly not a channel-exclusion fraction; channel exclusion examples are 2019ApJ...883...22C (4.0-7.5 km/s masked, card) and 2016ApJ...818..156C.
- SR-05 | REJECTED | The 20-30% overestimate at i = 80 deg is a verbatim quote in the 2021ApJ...908...46B card ("the stellar mass could be overestimated by 20% to 30% with our method, when a disk is highly inclined (i = 80 deg)", section 4.4); kept with the quote and "(card, synthetic disks)", and now also notes the pack line "scale-height effect small (<3%)".
- SR-06 | FIXED | The 8-beam extent is now attributed to the intensity/temperature resolution bias (intensity underestimated up to 50%) in 2025ApJ...994...98F; the separate exclusion of ~5 beams for the mass fit is kept.
- SR-07 | FIXED | Verification check now says the three radial v_rot profiles agree within 3 sigma (2018ApJ...868..113T) and that this validates the rotation curve, not the mass.
- SR-08 | PARTLY | Kept "excludes 23 contaminated channels (card)": the 2016ApJ...818..156C card recipe states "23 contaminated channels excluded" and lists "Which 23 CO channels were excluded" as not stated. Moved the sin(i)/2 inclination prior (card) and Gaussian distance prior out of the M* prior row into its own "Inclination and distance priors" row; M* prior row recounted to 2 entries.
- SR-09 | REJECTED | The 2018A&A...616A.100Y card lists 13CO 3-2 and C18O 3-2 and the tests on "30 synthetic ALMA images of a blank field" and 24 model disks; the 2021ApJ...908...46B card lists 13CO, C18O and CN and a stellar-mass step with "i, PA, position, distance fixed". Kept, now marked "(card)" at each use.
- SR-10 | REJECTED | DISCMINER is verbatim in the 2026ApJ..1000L..15F card ("Residual maps were created by subtracting the model disk obtained from spectral fitting using DISCMINER") and DiskJockey in the 2019ApJ...883...22C card ("see (cite: czekala15a) and the DiskJockey codebase"); both bibcodes are in the pack paper list. Kept with "(card)"; DISCMINER row says it is not in the aggregates.
- SR-11 | REJECTED | The 2025ApJ...986L..11S card gives EDDY 0.043 Msun vs visibility 0.092 Msun and "we find consistent solutions of inclination and position angle to those from the continuum". Kept both claims, now with the numbers, the EDDY beam-convolution quote, and "(card)".
- SR-12 | FIXED | Emission-height pitfall now states 2024MNRAS.534.2904C assumed elevated surfaces for four MAPS disks and did not measure a mass/PA bias; the thin-disk bias is labelled general modelling guidance.
- SR-13 | FIXED | Column renamed "Typical value (reported settings)" with a note that it is not a validated default; emcee described as the most often named sampler (18 mentions), with other samplers listed.
- SR-14 | FIXED | Separate rows for 12CO conical angle (psi 13.1-15 deg, z/r = tan psi ~0.23-0.27), HCO+ flared z = z0 (r/1")^psi with psi 0.81 as an exponent (z/r = 0.127 at r = 1"), and the assumed z/r = 0.13 of 2023PASJ...75..424O.
- SR-15 | FIXED | Turbulence row split into xi/v_turb (0.01 km/s) and "other line-width parameters (not interchangeable)" with each paper's own definition, plus a note to check sigma vs Doppler b vs FWHM and thermal contribution before comparing.
- SR-16 | FIXED | Step 5 now requires a noise model with spatial/spectral correlation or effective independent samples (2016MNRAS.460.2933M quote, 2018ApJ...864..133T) and matching spectral response (Hanning smoothing, 2013ApJ...776...77K); added to pitfalls and referee checks.
- SR-17 | FIXED | Always-report box, step 2, pitfalls and referee checks now cover rest frequency, velocity frame and convention, citing the incorrect Band 7 sky-frequency transformation (2013ApJ...774...16R) and the unstated-settings aggregate (rest frequencies, 2).
- SR-18 | FIXED | Step 8 and pitfalls distinguish enclosed mass (M_cl = 7.6 +- 1.4 Msun) from M* = M_cl - M_disk - sum(M_gas) = 4.89 Msun (2025NatAs...9.1833L) and ask for the gravity model.
- SR-19 | FIXED | RRL workflow now requires MORELI-style non-LTE disk-plus-wind modelling, notes the no-wind model fails, maser variability and large high-velocity centroid errors (2020ApJ...897L..33J); added a "When not to use" row, a pitfall and MORELI in Software.
- SR-20 | FIXED | Added a stacking-for-polarisation pitfall (stacking destroys vertical-field Stokes V; use only unblended hyperfine portions, 2021ApJ...908..141H); GoFish row now separates stacking from Kepler-correcting Stokes I/V.
- SR-21 | FIXED | Step 7, pitfalls and referee checks require reporting model dependence of residuals (2024MNRAS.534.2904C quote) and resolution limits (2018ApJ...868..113T), and say residual morphology alone does not identify a cause.
- SR-22 | FIXED | Distance range corrected to 59 pc (2018ApJ...862L...2F) to 2.38 kpc; VLBA removed; sources now Gaia DR2 (2020ApJ...895..109F) and spectrophotometric for 2024ApJ...967...15K (card).
- SR-23 | FIXED | Column renamed "Supporting pack entries" with a note on how it was counted (distinct bibcodes in pack parameter/assumption/excerpt lines); rows recounted (inclination 12 fixed / 10 free, robust 4 + 3 natural, sampler 7, M* prior 2, velocity cut 3, gas structure 7). Software note: vis_sample corrected to 3 (+ vissample 1) from the current pack aggregates.

=== EVIDENCE PACK (keplerian-disk-kinematics, rebuilt) ===
# Evidence pack: Keplerian rotation and stellar/protostellar dynamical masses (`keplerian-disk-kinematics`)

Scope: fitting Keplerian rotation of disks to get central masses, inclination and disk extent

Built from 447 non-held-out ALMA papers whose methods cards passed mechanical evidence verification (every quote below is verbatim from the paper). Years 2012-2026.
Matcher (regex over analysis steps): `kepler|eddy\b|protostellar mass|stellar mass (?:from|via) (?:the )?(?:\w+ )?(?:rotation|kinematic)|central (?:mass|object)|disk rotation|disc rotation|rotation curve of the disk`
Tagging is by regex, so a few papers may be off-topic: ignore those.

## Aggregates over all papers

### Science fields
- protoplanetary_disks: 295
- star_formation: 189
- astrochemistry: 158
- stellar_physics: 34
- debris_disks: 33
- exoplanets: 26
- milky_way_ism: 20
- evolved_stars: 20
- nearby_galaxies: 8
- agn_and_quasars: 8
- instrumentation: 1

### Software named in the matched steps
- casa: 101
- eddy: 39
- emcee: 35
- gofish: 32
- radmc-3d: 29
- bettermoments: 26
- tclean: 24
- keplerian_mask: 20
- uvcontsub: 13
- lime: 11
- visible: 9
- casa tclean: 7
- discminer: 7
- scipy: 6
- diskfit: 5
- pdspy: 5
- python: 5
- gildas: 5
- miriad: 5
- mcfost: 5
- pvextractor: 4
- scipy.optimize: 4
- vis_sample: 4
- galario: 4
- casa imfit: 4
- numpy: 3
- feria: 3
- imsmooth: 3
- karma: 3
- csalt: 3
- slam: 3
- imfit: 3
- keplerian mask: 3
- ratran: 3
- diskjockey: 3
- iram-gildas: 2
- celerite: 2
- vissample: 2
- moreli: 2
- clean: 2

### Fitting methods (most common phrasings)
- MCMC with 64 walkers, 10,000 burn-in steps and 10,000 sampling steps, flat priors: 1
- Maximum likelihood with a Gaussian Process on the stacked spectra: 1
- Single Gaussian fit with scipy.optimize.curve_fit; FWHM = 2 sqrt(2 ln 2) sigma: 1
- Modified Levenberg-Marquardt least squares on visibilities; error bars from the covariance matrix: 1
- MCMC (Eddy) weighted by per-pixel signal-to-noise for the center and PA; chi-square without radial S/N weighting for ma…: 1
- Keplerian curves for 0.05-0.4 Msun compared by eye; no formal sampler stated: 1
- Manual adjustment of parameters, no formal fit: 1
- Coarse then fine chi2 grid search (not MCMC): 1
- Least-squares fit in SciPy: 1
- Qualitative comparison of observed P-V emission with Keplerian curves: 1
- Qualitative comparison of modeled and observed P-V morphology, especially the central waist and edge-brightening: 1
- Select output with total gas velocity profile consistent with the Keplerian profile of a 20 M☉ protostar: 1
- MPFIT chi2 on visibilities, then manual tweaks; priors not stated: 1
- Qualitative, not optimized: 1
- Grid chi2 minimization with staged parameter sets; uncertainty from delta reduced chi2 = 1 with others fixed: 1
- Trajectory matched to measured ridge peak positions (not a formal fit): 1
- Metropolis-Hastings with Gibbs sampling; flat priors (Table 4); chi^2 likelihood; two parameters updated per trial: 1
- Least-squares-type fit with fixed errors (sampler/likelihood not stated): 1
- emcee affine-invariant ensemble sampler with uniform priors; likelihood not stated: 1
- Qualitative adjustment of three parameters; Gaussian FWHM and peak intensity fitted per azimuth with MCMC: 1
- manual iterative adjustment; no sampler, priors or likelihood: 1
- Uniform grid, flat priors implied; 1D marginal maximum with 68% integrals; inclination from best-fit stellar mass due t…: 1
- Sinusoidal fit of mean Doppler velocity vs position angle (parameters A, B, omega_0 in Table 2): 1
- SLSQP minimizes reduced χ²; MCMC uses listed Keplerian elements as a prior: 1
- Levenberg-Marquardt least squares on the full data set (scipy.optimize.leastsq); uncertainties normalised to data dispe…: 1
- Gaussian fits to beam-sized spectra: 1
- Linear least-squares fits to spatial distribution and position-velocity curves of disk masers: 1
- Keplerian orbit fit followed by MCMC simulations using the Keplerian fit as apriori distribution and adopting the upper…: 1
- emcee; uncertainties are posterior standard deviations: 1
- Gaussian Process via celerite; radial profile also modelled as GP: 1
- emcee MCMC with a likelihood built from the LTE line intensity; best values from 16th, 50th, 84th percentiles; priors, …: 1
- Likelihood and emcee fit per radial bin: 1
- double Gaussian fit to blended C2H J=7/2-5/2 lines: 1
- Manual grid comparison by eye, no sampler: 1
- Visual comparison of all combinations of theta_0 and phi_0, no sampler or likelihood: 1
- Grid search minimizing reduced chi-squared (chi^2/DOF) over central mass and inclination angle; parameter ranges define…: 1
- Grid search minimizing reduced chi-squared over central mass, inclination angle, and (for IRE) centrifugal barrier radi…: 1
- qualitative comparison: 1
- Best-fit by matching the continuum map, HCO+ channel maps, spectrum and PV diagram; no formal sampler stated: 1
- emcee affine-invariant ensemble sampler, chi^2 likelihood with visibility weights; priors not stated: 1

### Validation checks used
- Compared with a non-parametric surface and with a fit that fixes Z1 = 0: 1
- Repeated with v_R fixed to 0, giving no change in v_phi: 1
- Differences between the two emission surfaces used for systematics: 1
- Disk-centre offset between the two executions checked: 1
- Radial profiles also made without Keplerian masking for comparison: 1
- Stacked spectra peak at the systemic velocity, confirming the detections: 1
- Filter response 43 sigma (N2H+) and 20 sigma (DCO+) at 6.4 km/s: 1
- Best-fit radial profile imaged from model visibilities and Kepler-deprojected, compared with the data: 1
- Fit result compared across radial ranges; kinematic features checked to be independent of the fitting procedure: 1
- Both isotopologues give consistent velocities: 1
- Model deviations compared with the observed pattern at R > 150 au: 1
- Beam smearing alone judged unlikely to explain the signal; beam smearing plus pressure gradients cannot be excluded: 1
- Repeated with 13CO, giving similar results: 1
- Two independent assumptions give consistent masses; authors keep the identification tentative: 1
- Model reproduces kinematics along S2 and S5 but not the V-shaped profiles of S1 and S2: 1
- Chi2 shows a ridge-like degeneracy between central mass and inclination; model reproduces curvature in centroid velocit…: 1
- Remaining masers follow Keplerian rotation; using the pseudodisk inclination would give an unphysical >180 Msun mass: 1
- Compare elongation and velocity-gradient orientation with the outflow; inspect compactness and gradient changes with K: 1
- Compare K=3 observations with all four models; compare M4 predictions with all observed K components: 1
- Qualitative comparison of surface density, sub-Keplerian azimuthal motion and radial infall: 1
- Compare model and data channel maps: 1
- Compare channel maps and PV diagrams: 1
- Tested different initial p and q; residuals mostly <=3 sigma: 1
- Infall model reproduces protrusion velocity structure better than coplanar Keplerian model: 1
- 3 chains converge to similar parameters; model agrees with data to ~10%: 1
- Consistent with astrometric displacement between ZIMPOL and ALMA epochs: 1
- Compared with continuum geometry and stellar-model mass; convergence assessed visually: 1
- Profiles checked as function of azimuth before averaging; approximately Gaussian: 1
- Model rejected as it needs unrealistically high temperature, cannot make the X-shape, and overestimates 13CO linewidths: 1
- Compared with data FWHM and RADMC-3D azimuthal pattern: 1
- Both rotation directions tested; no significant emission recovered: 1
- Consistency with VLBA upper limit on second black hole mass: 1
- Co3RaL benchmarked against MORELI with identical inputs; the authors state no comprehensive parameter-space study was d…: 1
- Model reproduces all five lines; outer radius, inclination, stellar mass consistent with independent estimates: 1
- Checked consistency with red-side evaluation and with a scan made at y = 0 in small steps of x; estimated +-1 km s^-1 u…: 1
- Compare alternative orbit solutions and inspect eccentricity–semi-major-axis parameter space: 1
- Compared with previous dynamical masses (Davies 2007, Hicks 2009): 1
- reduced chi2 of 1.2; a third iteration did not change the parameters; adopting Trifonov RV shift gave no significant ch…: 1
- Innermost HCN and HCO+ dynamics roughly agree with VLBI H2O maser dynamics at <0.7 pc: 1
- Consistency of systemic velocity, disk PA, and enclosed mass between H30alpha and H26alpha transitions and with Zhang e…: 1

### Key parameters and settings (bibcode: value)
- 2019Natur.574..378T: Only pixels at least a beam FWHM apart are used in the likelihood
- 2019Natur.574..378T: Annulus width 25 mas
- 2019Natur.574..378T: Resampled to 40 m/s, a factor of 16 higher than the original data
- 2024ApJ...976..258K: tclean hogbom, briggs robust = 1.0 for N2H+ and DCO+; multiscale scales [0,5,15,25] pixels with natural weighting for weak lines
- 2024ApJ...976..258K: Radial range 120 to 550 au; shifted to systemic velocity 6.4 km/s
- 2024ApJ...976..258K: Surface density as the sum of two Gaussians truncated to 150-550 au; temperature a power law defined by T250 and exponent q
- 2024ApJ...976..258K: H2D+: same adopted geometry, constant T = 15 K, uniform surface density 150-450 au
- 2021A&A...650A..59B: inclination fixed to 27 deg; fit binary mass, systemic velocity, PA and center of rotation
- 2021A&A...650A..59B: inner 100 au discarded
- 2021A&A...650A..59B: first step uses R >= 150 au
- 2021A&A...650A..59B: grid cells of 1 au in radius, 2 deg in azimuth and 1 deg in elevation
- 2021A&A...650A..59B: ray-tracing pixel size 20 mas, velocity resolution 10 m/s
- 2021A&A...650A..59B: ideal observations without noise at 25 m/s velocity resolution for Figure 6
- 2018ApJ...865..131L: Disk PA 106.5 deg; inclination 25.2 deg; systemic velocity 6.61 km/s
- 2018ApJ...865..131L: L_acc = G M Mdot/(2R); L_int ~0.05 Lsun; dynamical time ~2.8e4 yr; 10% outflow extraction
- 2025SciA...11.6953M: S2: initial distance 52,000 au, position angle 21 deg, polar angle 70 deg
- 2025SciA...11.6953M: Angular velocity 4e-14 rad/s, initial radial velocity 0.6 km/s
- 2025SciA...11.6953M: Central mass 50-80 Msun
- 2025SciA...11.6953M: Position angle fixed to the velocity gradient in the centroid velocity map
- 2025SciA...11.6953M: Fine-grid ranges: M 20-70 Msun, i 0-20 deg, r_CB 0-200 au, r_out 800-1200 au
- 2025SciA...11.6953M: Southeast and northwest blueshifted/redshifted clusters selected by hand; northeast cluster excluded as outflow-related
- 2025SciA...11.6953M: PA of PV cut fixed to steepest velocity gradient in ALMA data; disk center at the long-baseline 1.3 mm continuum peak
- 2020ApJ...904..181L: Cut P.A. 165 degree; systemic velocity 5.2 km s^-1
- 2020ApJ...904..181L: Keplerian comparison curves: 8.04/sin^2 i, 3.57/sin^2 i and 0.89/sin^2 i M☉
- 2020ApJ...904..181L: M1: pure Keplerian, 20 M☉, 25 degree; M2: pure Keplerian, 4.76 M☉, 60 degree; Table 1 rounds the latter mass to 4.8 M☉
- 2020ApJ...904..181L: M3: Keplerian azimuthal motion around 4.76 M☉ at 60 degree, plus constant radial infall 2.5 km s^-1
- 2020ApJ...904..181L: M4: Ulrich accretion-flow velocity field; arbitrarily assumed centrifugal barrier 90 au
- 2020ApJ...904..181L: Surface-density profile r^-1.1; at 900 au M1 has 0.79 g cm^-2 and M2–M4 have 0.71 g cm^-2
- 2020ApJ...904..181L: Temperature: 430 K at r < 214 au; 430 (r/214)^-0.7 K at r ≥ 214 au
- 2020ApJ...904..181L: CH3CN abundance 2 × 10^-8; abundance truncated at radius 900 au; turbulent velocity 2 km s^-1
- 2020ApJ...904..181L: Initial core: 100 M☉, rigid rotation, 10 K, density ∝r^-3/2, kinetic-by-gravitational energy ratio β=4%
- 2020ApJ...904..181L: Spherical midplane-symmetric domain; inner radius 20 au, outer radius 0.1 pc; grid as printed: Nr=512 × Nφ=81 × Nθ=512
- 2020ApJ...904..181L: Inner sink cell r≤20 au; stated simulation duration 40.0 kyr
- 2012ApJ...757..129R: PA fixed 151 deg; M*=0.8 Msun; inclination free; T10,q free per line
- 2012ApJ...757..129R: dT=3 inside r_hot=4 AU
- 2012ApJ...757..129R: non-Keplerian: r_b≈60 AU, x=0.15
- 2012ApJ...757..129R: warp: i0≈8 deg at r0=5 AU, y=0.15
- 2014ApJ...793....1Y: Fit region central 2''x2'', velocities -6.1 to -2.5 and 2.5 to 7.1 km/s; Rd fixed 200 AU
- 2014ApJ...793....1Y: Initial solid angle theta0±3, phi0±3 deg; n1=3e7 cm-3; flow lengths 5000 AU (red), 2000 AU (blue)
- 2016ApJ...829....6W: 3 chains, 100 thousand links each, ~1000 burn-in; sigma = 0.5 km/s
- 2016A&A...596A..92K: position uncertainty fixed at ±2.5 mas, velocity uncertainty ±0.5 km/s
- 2026A&A...705A.201B: Distance fixed at 117.9 pc; 1500 steps, 32 walkers, 500 burn-in steps
- 2026A&A...705A.201B: Annulus width 0.02 arcsec; inclination, PA, RA and Dec offsets from the Keplerian fit (Table 2)
- 2026A&A...705A.201B: Model cube 678 x 678 pixels of 0.0225 arcsec with 1182 channels of 13 m/s; spectral Gaussian FWHM = 2 x channel width; beam 0.12 x 0.11 arcsec
- 2026A&A...705A.201B: Azimuthal sections of 15 deg for data; Gaussian fits with 2000 steps and 100 burn-in
- 2026A&A...705A.201B: r_orb 73 au; M*, i, beam from HD 121617 ARKS data
- 2020MNRAS.498.1319M: Band 7 cubes 0.43 km/s channels (1.1 km/s effective); Band 6 cubes 1.3 km/s channels (2.0 km/s effective)
- 2020MNRAS.498.1319M: Kinetic temperatures 20 to 200 K
- 2017ApJ...850L...5T: a~1.4e17 cm, e=0.96-0.98, dV~600 km/s
- 2024A&A...692A.151S: Te ~ 15000 K, constant
- 2024A&A...692A.151S: inclination i = 12 deg (models around 17 deg examined)
- 2024A&A...692A.151S: R_out ~ 40 au, R_eq ~ 8 au
- 2024A&A...692A.151S: high-velocity shells: velocity rises from ~70 to ~90 km/s; ~10 km/s inside ~15 au
- 2013ApJ...776...77K: M* 0.9-3.0 Msun step 0.3; rin 5-60 AU; rout 95-175 AU; i 25-39 deg step 2; p 0 to -1.75 step 0.25
- 2013ApJ...776...77K: Intrinsic line width 0.1 km/s; 2-channel Hanning smoothing; 6x spatial oversampling
- 2022MNRAS.510.2363H: Scan step y = 10 mas (0.64 au) along x = 0; V_{z,20} at 20% of max flux density on blue side; ring intervals 30-60, 60-90, 90-120, 120-150 mas; |V_z| < 20 km s…
- 2024ApJ...970...74P: E-stars, DS sources, and Greek-named sources; exclude ι and ϑ because of blending
- 2013PASJ...65..100I: r ~ 40 pc; i = 35 deg
- 2021AJ....162...14A: 2 m/s uniform jitter added in quadrature to RVs; RVs with sigma > 10 m/s rejected; 5 sigma clipping (0.9% of A, 1.0% of B)
- 2020ApJ...902...99I: Keplerian curve V ∝ r^-0.5 for a point mass of 1e7 Msun, and sub-Keplerian V ∝ r^-0.31 from H2O masers
- 2023ApJ...953L...6P: Disk velocity range: -12 to 28 km s^-1; maser spatial extent (diameter 2R): 45 mas (H26alpha) and 54 mas (H30alpha); distance = 1.2 kpc; inclination = 9 deg fr…
- 2022MNRAS.515..543C: Velocity integration ranges for channel maps: B (-11 to +14 km/s, or -16 to +24 km/s for 20_3,17-20_2,18 A), A (-2 to +7 km/s); velocity shifts: +/- 6-7 km/s f…
- 2020PASJ...72L...5T: Keplerian orbit with a ~1 pc, e ~0.8, i ~140 deg
- 2018ApJ...868..113T: 160 m/s channels
- 2018ApJ...868..113T: three cases: flared, thin, flared without continuum subtraction
- 2024ApJ...967...68H: Robust 0.0-0.5 and per-line UV taper (Table 4); pixel about 1/7 beam; channel width 0.2 km/s (0.5 km/s for Band 3)
- 2024ApJ...967...68H: Integrated within outer radius of 4.5 arcsec and between -1.8 and 13.4 km/s
- 2024ApJ...967...68H: Free parameters N_T, T_rot, OPR and Delta v
- 2024ApJ...967...68H: Annulus width equals one-quarter of the beam major axis
- 2021AJ....162...99F: Keplerian mask geometry from Keppler+2019: M_star 0.875 Msun, i 51.7 deg, PA 160.4 deg
- 2021AJ....162...99F: elevated surface z(r)=0.33 x (r/1'')^0.76 for 12CO and HCO+
- 2021AJ....162...99F: weak lines c-C3H2 3_21-2_12 and H2CO 3_21-2_20 additionally uv-tapered by 0.7''
- 2021AJ....162...99F: integration window 3-8 km/s (default); 1.5-9.5 km/s for the two 12CO and HCO+; 2-9 km/s for 13CO, H13CN and C2H
- 2021AJ....162...99F: flux uncertainty from standard deviation of unused velocity bins times sqrt(number of integrated bins)
- 2021AJ....162...99F: C2H J=5/2-3/2 only half covered: only the part of the disk within 80 deg of the red-shifted major axis is used, azimuthal symmetry assumed
- 2021AJ....162...99F: annulus width = 1/4 of the beam major axis
- 2021AJ....162...99F: error bars: standard deviation within annuli divided by sqrt of number of independent beams
- 2019ApJ...873...73Z: h(r)=0.2r; envelope rho~r^-1.5; disk rho~r^-2.5; r_out/d=0.8"
- 2025ApJ...985..166K: sigma_NT 0.18-0.20 km/s; sigma_theta 7-13 deg; xi = 0.5; mean density (6.1-7.1)e-20 g cm-3
- 2025ApJ...985..166K: NW and NNW: i_s = 107 deg, theta_s = -45 deg, r_d = 55 au, M* = 0.14 Msun fixed; theta_0, phi_0 free
- 2025ApJ...985..166K: Streamer edges set at 3 sigma in moment 0 maps
- 2025ApJ...985..166K: Radial range 1-9000 au, distance 151 pc, stellar mass 0.14 Msun, disk radius 55 au, disk mass 1.0e-2 Msun, envelope mass 0.52 Msun, C18O abundance 1.7e-7
- 2025ApJ...985..166K: Disk P.A. 45 deg and inclination 73 deg
- 2025ApJ...985..166K: Lbol = 0.89 Lsun, Lacc = 50% of Lbol, R* = 3 Rsun
- 2020ApJ...904..185O: Inner radius = 50 au (or r_CB = 50 au), outer radius = 300 au, P.A. = 50 deg, V_sys = 3.9 km/s, flared angle = 30 deg, intrinsic FWHM = 1 km/s, emissivity prop…
- 2020ApJ...904..185O: V_sys = 2.5 km/s, outer radius = 30 au, inner radius = 0.56 au (1 pixel) for Keplerian or r_CB = 5, 10, 20 au for IRE, P.A. = 50 deg, flared angle = 30 deg, in…
- 2013ApJ...774...16R: mask smoothing sigma = 0.7 arcsec
- 2013ApJ...774...16R: psi ~15 deg
- 2013ApJ...774...16R: LIME only for level populations; images by own ray tracing on interpolated 2D grid; Poisson equation on fixed grid
- 2014ApJ...786..114L: 7 free parameters: T0, n0, vr0, vphi0, m, q, x(HCO+)
- 2014ApJ...786..114L: Disk outer radius 0.3 arcsec (120 AU), half thickness 0.1 arcsec, inner radius 0.01 arcsec; envelope outer radius 5 arcsec
- 2017ApJ...842....8M: Free: R_belt, Δa, F_belt, F_star, i, PA, e_f, e_p, ω_f, Δα, Δδ
- 2019A&A...629A.136S: θa=60°, θd=6.5°, θw=38°, Rin=29 au, Te=8750 K, Vfast=95 km/s, Vslow=9 km/s, ne=4.3e7 (r/30au)^-2.7 exp(-(θa-θ)/40°) cm^-3 (d=1.7 kpc)
- 2026A&A...705A.202M: Cube: 12CO clean cube with robust 0.5
- 2026A&A...705A.202M: Annuli spaced by 20% of the beam size, oriented at the disc PA and inclination from the Keplerian fit
- 2026A&A...705A.202M: Fit restricted to position angles within 20 deg of the major axis
- 2026A&A...705A.202M: beta=-0.14, T0=38 K, r0=73 au (from ARKS 13CO fit)
- 2026A&A...705A.202M: M_star = 1.91 Msun so that Keplerian speed at 75 au equals the measured azimuthal velocity
- 2026A&A...705A.202M: Cubes with 26 m/s spectral resolution and 10 mas spatial resolution
- 2026A&A...705A.202M: Gaussian radial surface density centred at 74 au, FWHM 17 au, aspect ratio h=0.05, 1.91 Msun star
- 2021MNRAS.506.1978L: uvcontsub fit order = 1, exclusion window = +/- 35 km s^-1; tclean iterations = 0; radial integration = 38-125 au; channel spacing Delta v = 0.423 km s^-1; eff…
- 2021MNRAS.506.1978L: NLTE kinetic temperatures = 10 K, 50 K, 250 K
- 2025A&A...699A..22M: flat priors: M_A 1.1-1.9 Msun; q = M_C/M_A 0.2-0.8; a 5-10 au
- 2025A&A...699A..22M: flat priors: e 0-1; Omega and omega 0-360 deg; i 33-43 deg; tau_0 2009-2024
- 2015MNRAS.447.3936M: 1-sigma single-channel error 30 mJy; 3-sigma 90 mJy
- 2020A&A...633A.115K: outer radius 0.6 au; inner edge 0.19 au; 40% pyroxene, 60% water ice
- 2022PASJ...74..738T: Elapsed time Delta t = 1.698 year
- 2017A&A...608A.134Y: R0 = 1'' (140 au); free parameters V_rot(R0), f, V_sys; high-velocity ranges only
- 2017A&A...608A.134Y: M*=1.8 Msun, i=47 deg, PA=138 deg, Vsys=7.04 km/s
- 2025ApJ...984L..22W: Line profiles of data and model fitted with a Gaussian, except a double-peaked bell profile for HD 34282
- 2025ApJ...984L..22W: For HD 34282 the back-side contribution is subtracted when computing residuals
- 2025ApJ...984L..22W: Maximum velocity v_max at radius r_v
- 2025ApJ...984L..22W: Aspect ratio chi (azimuthal major axis over radial minor axis) and Gaussian width omega_V
- 2025ApJ...984L..22W: Sub-Keplerian background subtracted from the azimuthal velocity input to give the expected residuals
- 2025ApJ...984L..22W: Synthetic 12CO channel maps by ray-tracing at the spectral resolution of the data
- 2025ApJ...984L..22W: Source geometry used and vortex matched radially and azimuthally to the dust asymmetries
- 2021ApJ...906..111T: PA 152°; inclination 5°; stellar mass 0.88 M_sun.
- 2021ApJ...906..111T: Systematic velocity 2.83 km s−1 (V_LSR); outer radius 220 au.
- 2021ApJ...906..111T: 10 au wide radial bins.
- 2021ApJ...906..111T: UVTAPER: [0.0, 0.35 arcsec, −87.8°], [0.23, 0.33 arcsec, 64.7°], [0.18, 0.30 arcsec, 83.5°], respectively.
- 2021ApJ...906..111T: Intrinsic disk-averaged FWHM 0.275 km s−1 from Keplerian-corrected GOFISH spectra.
- 2021ApJ...906..111T: LAMDA degeneracies, upper-state energies, Einstein A coefficients, and frequencies.
- 2021ApJ...906..111T: ExoMol ground-state degeneracies adjusted by dividing by three to remove its assumed OPR of three.
- 2019ApJ...872..176Z: fixed: beam-width 0.06", inner radius 0.005"; power-law indices 0.5 (rotation, infall), 1.0 (intensity)
- 2025A&A...701A.141L: Radius of centrifugal barrier 65 au (semi-major axis of SO ring)
- 2025A&A...701A.141L: theta_view and phi_view fixed to the SO ring values (theta_view = 45 deg during follow-up fitting)
- 2025A&A...701A.141L: Free-fall velocities scaled down by ~1.5
- 2025A&A...701A.141L: r_out ~150 au (~1''), r_in ~35 au
- 2021ApJ...907L..41L: M_*~0.2 M_sun; λ~5.5; W~30
- 2021ApJ...907L..41L: Shell corresponds to model streamlines launched from 4-8 au
- 2021ApJ...907L..41L: Initial SO jet launching radius 0.10-0.20 au
- 2015PASJ...67..122M: stellar mass fixed within 2.2 +/- 0.3 Msun; free: systemic velocity, centre, inclination
- 2015PASJ...67..122M: Keplerian rotation for 2.2 Msun; channel step 0.06 km/s over +/-4.5 km/s; thermal line width
- 2015ApJ...812...27A: fixed i=65 deg, Rin=0.1 AU, Rout=200 AU; 7 free parameters
- 2016MNRAS.460.2933M: ne0 between 1e-2 and 1e7 cm-3; Tk half to twice dust temperature (50 K)
- 2018A&A...614A.113H: radial velocity 1 km/s, turbulence 1 km/s, temperature power-law index -0.5
- 2026A&A...705A.203W: Gas grid: 0.1r0–3r0, 512 logarithmic radial cells; −π–π, 1024 azimuthal cells
- 2026A&A...705A.203W: 10^5 superparticles; initial dust positions 0.9r0–1.1r0; 200 orbits with output every orbit
- 2026A&A...705A.203W: α=10−4; β1μm=0.4; initial local Keplerian dust velocity
- 2026A&A...705A.203W: Cloud-in-cell interpolation and stochastic dust diffusion
- 2026A&A...705A.203W: Minimum detectable displacement: half the beam size
- 2022MNRAS.517.2546L: Delta v = 1.269 km s^-1; effective bandwidth factor = 2.667; integration regions = 0-60 au and 60-240 au; gas temperatures = 10, 20, 50, 100 K
- 2017ApJ...837...93Y: v_z = +50 km/s; wind 20 km/s; ejection 2500, 5000, 7500 yr ago
- 2024A&A...682A.143P: Keplerian period limited to 6310 +/- 1220 d from the Lomb-Scargle periodogram of the light curve (3 sigma)
- 2024A&A...682A.143P: Nine Barnbaum RVs added; extra 0.2 km/s uncertainty on HERMES RVs
- 2017A&A...607A.114W: Inclination 20-60 deg, P.A. 120-170 deg, opening angle 0-20 deg
- 2017A&A...607A.114W: inner inclination 40-90 deg, inner P.A. 40-100 deg, transition radius 40-120 au
- 2026A&A...705A..49Z: 250 burn-in steps; 90 walkers; 1000 steps before first convergence check
- 2026A&A...705A..49Z: Stop when relative change in the median of each parameter is below 5% over the last 500 steps; otherwise continue
- 2026A&A...705A..49Z: Priors chosen per disk for inc, PA, v_sys, M*, r_tau and r_z from the channel maps; Gaussian and uniform priors (example in Table 3)
- 2026A&A...705A..49Z: Best fit = median, uncertainties = 68% interval of posterior
- 2026A&A...705A..49Z: image size 1500 pix, cell 0.01 arcsec, scales (0, 10, 30, 60), robust=1, threshold 20 mJy per beam, Keplerian mask
- 2023ApJ...958...98F: PV cut width = 5 pixels (~0.5''); P.A. = 149 deg; emission threshold > 5 sigma; filtered-out velocity channels excluded
- 2023ApJ...958...98F: M_star = 0.5 M_sun; i = 47 deg; P.A. = 149 deg; near side = 59 deg E of N; For C18O: R_disk = 265 au, R_cloud = 5300 au, h_0 = 1250 au km s^-1, (theta, phi) = …
- 2023ApJ...958...98F: A_v = 24 mag (varied 20-40 mag); R_in = 5 R_star; R_star = 3.0 R_sun (varied 2.0-3.7 R_sun, log g = 3.2); M_star = 0.5 M_sun; T_eff = 3500 K; mu = 2.3; g/d = 1…
- 2018ApJ...869L..24I: R_in = 270 au fixed; R_out steps of ~150 au; mass steps of 5 Msun; infall at 40% of free-fall
- 2025ApJ...995L...7L: C18O abundance fixed at 1.7e-7 relative to H2
- 2025ApJ...995L...7L: inclination ~18 deg to the plane of sky; model spans 10 au to 8000 au
- 2025ApJ...995L...7L: best-fit structure: H0 ~0.4 arcsec (160 au), theta0 ~18 deg, n0 ~1.3e6 cm^-3, p ~ -0.13+/-0.01, T0 ~20+/-1 K, q ~ -0.5+/-0.1
- 2025ApJ...995L...7L: b ~0.38 (l0 ~1333 au km/s, ~530 au km/s at Rd ~160 au)
- 2020ApJ...904...77G: Fixed M_star=33 M_sun, P.A.=100°, T_e=7000 K
- 2013Sci...340.1199V: i=50°, PA=97°, center from CO Keplerian model
- 2013Sci...340.1199V: 2 Msun star, i=50°
- 2014ApJ...796..131O: SO ring 70-120 AU, 32 K, SO abundance 9e-7 (5000x outside); disk 54 AU, 0.3 Msun; j=6.1e-4 km/s pc
- 2019MNRAS.482.3443B: Pixels with continuum SNR >=10 summed for unshifted spectrum
- 2018A&A...614A..58B: Inclination 70 deg to plane of sky axis, PA -15 deg, X(13CO)=1.5e-5, X(12CO)=1.5e-4
- 2025A&A...703A..15M: Channel width 0.4 km/s (12CO) and 1.6 km/s (13CO, C18O); 20 random off-source apertures for uncertainty estimation; 9% upward scaling for HD 155853 12CO flux d…
- 2025A&A...703A..15M: Radial cuts in 5 deg increments from 0 to 360 deg
- 2020MNRAS.492.6067M: maximum Doppler shift of 10 km/s (beyond 1 au if Keplerian)
- 2018ApJ...864..133T: Beams ~0.57x0.5 arcsec; robust 0.5 for B6
- 2018ApJ...864..133T: Free: centre, i, PA, vLSR
- 2018ApJ...864..133T: 4 au annuli
- 2025A&A...694A.108P: i=46.7 deg, PA=313.3 deg, zero center offsets
- 2025A&A...694A.108P: Extraction repeated 20 times with independent spectrum samples; uncertainty = weighted standard deviation
- 2025A&A...694A.108P: Equal Gaussian width for all components
- 2025A&A...694A.108P: Fixed shifts: 2.5 MHz (C2H), 2.09 and 1.54 MHz (HCN); sigma bounded to half the component separation; intensity ratio priors xi in [0.2,1.5] (C2H) and [0.1,1] …
- 2020ApJ...905...89Y: Model parameters in Table 3: Mstar, i, PA, Vsys, N0, p, T0, q, Rin, Rout, H0, h, deltaV (which are free versus fixed not stated)
- 2020ApJ...905...89Y: Discussion limited to radii larger than 0.5 arcsec because of the 0.45 arcsec beam and complicated central velocity field
- 2020ApJ...905...89Y: Dust ring width deconvolved with the 0.19 arcsec 1-sigma beam width
- 2018ApJ...864L..25O: systemic velocity 5.5 km/s
- 2025A&A...694A..92B: Linear fit free parameters: X0, V_star, M; PA fixed to 130 deg
- 2025A&A...694A..92B: Planar fit free parameters: X0, Y0, V_star, PA, inclination, M
- 2025A&A...694A..92B: Mass 15 Msun (not inclination-corrected); j ~4500 (NE) and ~1600 (SW) au km/s
- 2025A&A...694A..92B: Outflow velocity ~30 km/s (also tested ~100 km/s)
- 2023A&A...678A.160E: Velocity intervals: 3.5 to 6 km s^-1 (redshifted lobe) and 0 to 3.5 km s^-1 (blueshifted lobe); minimum intensity threshold of 5-sigma
- 2023A&A...678A.160E: Model parameters: initial distance r_0, radial velocity v_r,0, position angle theta_0, azimuthal angle phi_0, angular velocity Omega_0, central mass, inclinati…
- 2014ApJ...791...42Z: 150 LM runs; uncertainties from Hessian
- 2014A&A...566A..74L: free parameters: central mass and disc radius
- 2019ApJ...878..113H: 1000 walkers, burn-in 100-400 steps, 800-1000 further iterations; sampled area 2 arcsec radius; grid every 1/3 beam; Delta R 0.1 arcsec
- 2017A&A...597L...5B: V(2e15 cm)=2.5 km/s; inclination ~45 deg (±15); X(13CO)~2e-5; X(12CO)~1e-4
- 2026MNRAS.545f2150S: robust = 0.3, nchan = 3
- 2026MNRAS.545f2150S: Velocity / frequency integration range: -8.49 to 15.33 km s^-1 (230.5445 GHz to 230.5262 GHz)
- 2026MNRAS.545f2150S: Keplerian mask parameters: inclination = 40 deg, PA = 17.2 deg, stellar mass = 3.27 M_odot, outer radius = 0.4'' (76 au)
- 2019A&A...632L..12H: threshold 40 mJy/beam; r>0.3''
- 2019A&A...632L..12H: distance 59.5 pc
- 2025NatAs...9.1672Y: Radial range 0.065-0.7 arcsec
- 2025NatAs...9.1672Y: 128 walkers, 5000 steps, first 3000 discarded as burn-in
- 2025NatAs...9.1672Y: Priors: log10 omega_0 ~ U(-4.7, 5.3), log10 omega_f ~ U(-4.7, 5.3), gamma ~ U(-5, 5)
- 2025NatAs...9.1672Y: GI case omega_kep = 0.19 (r/1")^-1.5 deg/yr for 1.1 Msun; planet case 0.30 deg/yr
- 2021A&A...648A..19W: robust = 0.6
- 2021A&A...648A..19W: 200 walkers, 5000 burn-in steps, 5000 sampling steps
- 2017ApJ...849...56A: Pixels above 5 sigma used; V_LSR=5.8 km/s; distance 140 pc; i=85 deg
- 2025ApJ...989...56H: distance 445 pc
- 2025ApJ...989...56H: scaling factor s 0.90 to 1.10
- 2020ApJ...905...25G: Disk radius 350 au, disk mass 1 M_sun, central star 20 M_sun
- 2020ApJ...905...25G: Impactor mass 0.25–0.5 M_sun; impact at 350 au and 10 km s^-1; α=90° for quoted flip
- 2015ApJ...806..154C: 12 free parameters: T10, q, Mco, rc, xi, M*, i_d, phi, offsets, vsys, d; gamma fixed to 1
- 2013A&A...560A.103M: M*=0.2 Msun, PA=35 deg, vlsr=4.0 km/s fixed; free: vwidth 0.1-1.0 km/s, i 0-90 deg, Rout 100-200 AU
- 2019AJ....158..162F: Tkin 10-250 K; stellar mass 1 Msun
- 2019NatAs...3..408D: orbital speeds up to 5 km/s; arm spacing ~1" (OH 26.5+0.6), ~0.58" (OH 30.1-0.7)
- 2026A&A...705A.198M: robust 0.5 or 2; scales [0,5,10]; pixel 1/5 beam
- 2016ApJ...823L..18H: 0.1 km/s channels
- 2016ApJ...823L..18H: Sigma_c=5e-5 g/cm2, gamma=1, r_c=100 AU, B=3, r_ring=150 AU, sigma_ring=20 AU
- 2016ApJ...823L..18H: turbulent broadening xi = 0.01 km/s
- 2024ApJ...966...63Y: 13CN cube channel spacing 0.34 km/s (half the velocity resolution), robust 0.5
- 2024ApJ...966...63Y: 12CN N=2-1 cube channel width 0.1 km/s, robust 1.0
- 2024ApJ...966...63Y: Filter-kernel mask outer radius 1.6 arcsec
- 2024ApJ...966...63Y: Same geometry as for the CLEAN mask; disk outer radius 3.0 arcsec for the 13CN disk-integrated spectrum
- 2023A&A...669A..53B: Briggs robust = +1.0, +0.5, 0.0, -0.5
- 2023A&A...669A..53B: Velocity binning: 0.12 km s^-1 for SO, 0.25 km s^-1 (or 0.24 km s^-1) for SiO and SiS
- 2023A&A...669A..53B: JvM epsilon ~ 0.50 for robust +0.5 line images (0.56 for robust 0.5 continuum)
- 2023A&A...669A..53B: Elliptical aperture semi-major axis = 0.6''
- 2023A&A...669A..53B: Velocity integration range = +/- 7.5 km s^-1
- 2018ApJ...869...59W: Fit velocity ranges V_LSR = 2.5-4.0 and 10.0-11.5 km/s; sigma = 0.4 km/s; vsys = 7 km/s
- 2024A&A...687A.308S: Free parameters include M*, M_disk, R_disk, gamma, T0, q, a_turb, i, p.a., v_sys, x0, y0 (R_in free for A, fixed at 0.1 au for B and W)
- 2024A&A...687A.308S: Strict priors on source position so each source is fit separately
- 2024A&A...687A.308S: Channel cuts: exclude 3.25-5.5 km/s for A and -2.5 to 6.75 km/s for B
- 2024A&A...687A.308S: uv cuts: exclude uv < 100 klambda for B and < 200 klambda for W
- 2021A&A...650A.142M: PA = 133°; average three pixels, 21 mas, perpendicular to the cut
- 2021A&A...650A.142M: Ionized gradient ΔV ≈12 km s−1 across ΔS ≈850 au
- 2013Sci...341..630Q: free: Rin, Rout, p, N100; fixed sigma_s=3.2, sigma_m=100
- 2014ApJ...796..117G: theta_b=1.7", d=1.7 kpc, i=45 deg
- 2025MNRAS.541...71M: Spectrum centred on stellar radial velocity of -9.38 km/s from Gaia DR3
- 2018A&A...609A..47P: x sampled every 0.08" (~1/4 beam); star at continuum peak
- 2025ApJ...989...30Z: CQ Tau: 23 channels of 0.7 km/s; MWC 758: 7 channels of 1.4 km/s
- 2025ApJ...989...30Z: gain=0.01, 1 sigma threshold
- 2025ApJ...989...30Z: natural weighting with Gaussian uv-taper 0.05 arcsec (CQ Tau) and 0.25 arcsec (MWC 758)
- 2025ApJ...989...30Z: Aperture radius set where the cumulative SO emission flattens: 0.33 arcsec (CQ Tau), 0.80 arcsec (MWC 758)
- 2025ApJ...989...30Z: Cubes over >200 km/s velocity range to estimate background noise in line-free channels
- 2023ApJ...948L...2Y: 5 epochs (2012.50, 2014.45, 2015.58, 2018.63, 2021.50); epoch uncertainty = 0.1 yr; astrometric error doubled for resolution < 0.15''
- 2023ApJ...948L...2Y: Eccentricity e = 0.27, systemic velocity = 4.55 km/s
- 2017ApJ...834..178Y: q fixed -0.4; envelope within 80 deg of polar axis zero density
- 2025A&A...696A.202S: Total protocluster mass used for t_dep: ~2820 Msun (dust-based)
- 2025A&A...696A.202S: Mean free-fall time of V-shape cores ~13.6 kyr
- 2025A&A...696A.202S: gamma = 3.1; M = 270 and 2700 Msun giving rho_0 = 3.466 and 34.66 Msun/pc^3
- 2023A&A...677A..80W: a = 0.65" (4088 au), b = 0.41" (2608 au), R_disk = 0.325"
- 2023A&A...677A..80W: FWHM(CH3OH) = 6 km s^-1
- 2013ApJ...765L..14Q: Vertical boundaries fixed: sigma_s = 0.32, sigma_m = 3.2
- 2015ApJ...814...22E: T_dust mass-weighted 111 K; opacity 1.48e-2 cm2/g; gas-to-dust 100
- 2019ApJ...881...84S: Temperatures 10-250 K, full collider density range
- 2024MNRAS.527.3559P: Inclination and PA from scattered light, stellar mass 1.8 Msun
- 2016A&A...592A..49T: Keplerian model with M*=0.69 Msun, i=7 deg for shifting
- 2016A&A...592A..49T: Direct methods only for r>40 au; inclinations 0,5,6,7,8,9 deg
- 2025NatAs...9.1486L: distance 400 pc, stellar mass 1.3 Msun, inclination 38.3 deg, PA 32 deg, emitting region 40-120 au, z/r = 0.4
- 2025NatAs...9.1486L: line width 350 m/s x sqrt(40 au / r); mask shifted by systemic velocity 4.3 km/s
- 2025NatAs...9.1486L: Mask convolved with Gaussian 0.5 (D2O), 1.25 (HDO), 0.75 (H2-18-O) x beam, chosen by visual inspection; channels 1.2-6.4 km/s used
- 2025NatAs...9.1486L: Noise from rms of 520 independent shifted spectra in a 19 arcsec square without primary beam correction, excluding the inner 2.4 arcsec square
- 2020ApJ...891...48H: Fit radii 0.2-2 arcsec; 48 walkers, 3500 steps, 500 burn-in
- 2020ApJ...891...48H: Integration range -1.25 to 12.75 km/s; fit over R = 30-350 au
- 2016ApJ...833..219P: outer radius 50 AU, inner radius 20 AU, turbulent linewidth 4 km/s, PA 142 deg
- 2026ApJ...999...62H: PA = 127 deg; systemic velocity v_CBD = 5.0 km s^-1; outer radius = 1.25" (500 au)
- 2026ApJ...999...62H: Reference velocities: 3.5 km s^-1 (source A), 6.5 km s^-1 (source B); outer rotation radii: 200 au (0.50", source A), 40 au (0.1", source B)
- 2022MNRAS.509..748W: i = 40 deg, R_out = 2000 AU (or 3500 AU for extended lines), R_in = 1700 AU (fixed to beamsize)
- 2015ApJ...798...85P: h=0.1 r, gamma=1, R_c=200 au, T=50 K (r/50au)^-0.3, b=50 m/s, inner truncation 0.3 au
- 2015A&A...579A.114M: inclination 55 deg; central mass 0.2 Msun; free-fall (DCO+) or Keplerian (C18O) velocity
- 2018MNRAS.479.5423M: radii 40-150 au
- 2019A&A...625A.118K: i fixed at 51.7°
- 2019A&A...625A.118K: radial bin width a quarter beam
- 2024AJ....167..165B: Four rounds of phase and one round of amplitude self-calibration
- 2024AJ....167..165B: Cleaned down to 4x the rms of the dirty image with Keplerian masks
- 2024AJ....167..165B: Keplerian filter with outer radius of 150 au (IRS 48) versus 300 au (HD 100546)
- 2021ApJ...911...29C: source velocity = 2.84 km s^-1, inclination = 5 deg, PA = 152 deg, M_* = 0.8 M_sun, distance = 59.5 pc
- 2021ApJ...911...29C: clean threshold = 3 sigma, final beam = 0.5'' round
- 2021ApJ...911...29C: velocity integration range = 2.5 km s^-1 to 3.18 km s^-1
- 2019A&A...622A.206M: priors: 0<=S*<=0.15'', 60.0<=V*<=61.0 km/s, M* in 5-15 Msun
- 2024AJ....167...72D: Jet width taken as transverse beam size b_m
- 2020ApJ...894...23H: M=0.2 Msun, i=55 deg, T0~30 K, T∝R^-0.5, Sigma∝R^-1
- 2013A&A...557A.133D: Rc 110-140 AU step 5; gamma 0-2 step 0.1
- 2013A&A...552L..10S: Free: Vsys, M*, x0, y0, inclination, position angle
- 2016A&A...595A.113S: 27 and 38 points along S1 and S2; h_p in [0.05,0.4]; zeta=3/2; eta=0.25
- 2016A&A...595A.113S: kappa_nu = 0.1 (nu/1e12 Hz) cm2/g, g/d=100; beam 132x94 mas
- 2024A&A...682A..55M: robust = 0.0 (also tested -2.0 and 2), uv taper = 0''.07 for CO, channel width = 768 kHz (1 km/s) for CO, solint = 30s (2019.1.01135), solint = 120s (2017.1.00…
- 2024A&A...682A..55M: robust = 0.0 cube, 1.0 km/s spectral resolution, 3σ threshold; for Sz 65 final fit: fixed inclination = 63.76◦, M_* = 0.76 M_sun, d = 153.1 pc; for Sz 66 fit: …
- 2020NatAs...4..142L: 6 free parameters: R_t, R_o, q, T_t, p, and n_t
- 2020NatAs...4..142L: Disk axis tilted ~18 deg from plane of sky
- 2017ApJ...843...27L: l and M free; r_c = l^2/GM; r_0 = l^2/2GM
- 2025SciA...11.4512O: rc 400-600 au (50 au steps), theta0 75-85, phi0 50-70; inner: r_c=200 au, theta0=89, phi0 140-195, v_r0=0.1 km/s selected
- 2025SciA...11.4512O: inclination 65 deg, P.A. disk -55 deg, centrifugal barrier 250 au
- 2020ApJ...891...61Y: M=0.15 Msun, inclination 130 deg, line width 1 km/s, rin=15 au, rout=50 au
- 2014ApJ...796....1T: M=0.8 Msun, i=62 deg, theta=167 deg
- 2018ApJ...869...10M: Cube -25 to 25 km/s, 0.5 km/s step; star 1.114 Msun
- 2018A&A...616A.100Y: M* 0.1-3 Msun (0.1 steps); PA 0-355 deg (5); i 5-85 deg (5); Vsys 1.7-6.3 km/s (0.1)
- 2018A&A...616A.100Y: detection: peak >4 sigma and >=3 channels above 3 sigma within 2 sigma Gaussian width
- 2024ApJ...961...28H: Initial mask: i = 56°, PA = 284.2° from (cite: rota22)
- 2024ApJ...961...28H: 3σ clip; inclination fixed to 47° ± 2
- 2023A&A...674A.113I: Orientation (i, PA, x_c, y_c), Velocity (M_*, v_sys), Upper and Lower surface (z_0, p, R_t, q), Peak intensity (I_0, p, q), Line width (L_w0, p, q), Line slope…
- 2023A&A...674A.113I: For AS 209 12CO, asymmetric intensity normalisation: 0.65 I_0 for -80 deg < phi < 80 deg, and 1.25 I_0 otherwise
- 2019A&A...629A..29J: Keplerian mass 0.01-1.5 Msun; specific angular momentum 1e4-1.5e5 m2/s; 2.8e5 uniform steps; rest velocity 6.0 km/s
- 2024A&A...686A.235P: Cluster size 40 mpc; 50–1000 stars; resolution/FHWM 3 mpc; data baseline 15 years.
- 2020ApJ...897...59M: Keplerian regime to 20 au (A1), 50 au (A2)
- 2015ApJ...808..102K: Q<~1.5 unstable
- 2017MNRAS.468..685Q: Example 1: 10 000 points, 151 channels, 100 m s^-1 spectral resolution, 0.1 arcsec pixel size, 141 pixels
- 2017MNRAS.468..685Q: Benchmarking (Appendix B): 101 992 points in LIME, 191 shells in RATRAN, 71 channels, 100 m s^-1 resolution, pixel size 0.2 arcsec (and 0.02 arcsec test)
- 2025A&A...698A.115R: centers fixed at 3.8 and 5.5 km/s; widths and peaks free; spectra shifted for Keplerian rotation with GoFish
- 2025A&A...698A.115R: fit stopped at 5.5 km/s (only half of the main component covered by LB)
- 2025A&A...698A.115R: Gaussians spectrally over-sampled and averaged in each spectral bin
- 2025A&A...698A.115R: fiducial radial range ~50-120 au
- 2021ApJ...911..150P: Keplerian mask parameters: V_0 = 0.22-0.25 km/s, R_0 = 100 AU, q = 0.3, and disk-specific theta_alpha, theta_beta, V_LSR, and mask extents (Table 6)
- 2021ApJ...911..150P: Detection criteria: >= 3 sigma in velocity-integrated map and peak >= 3 sigma in at least 3 channels within Keplerian mask
- 2019ApJ...879..101L: Vsys refined to 9.10 km/s LSR
- 2020ApJ...898...10T: v_sys = 6.4 km/s
- 2019AJ....157..117M: M*=0.55 Msun, i=13 deg, PA=91 deg
- 2018ApJ...860L..12T: position angle 132 deg from Keplerian fit to first moment map
- 2025ApJ...994...98F: 16 walkers, 300 steps, 50 burn-in; uniform prior T_m 0-10,000 K
- 2025ApJ...994...98F: uniform prior M* 0-5 Msun, 32 walkers, 1000 steps, 300 burn-in
- 2023A&A...675A.131T: Radial range 0.0" to 3.0", bin width = 2x minor axis of beam, step = 1x minor axis of beam
- 2023A&A...675A.131T: Circular aperture radius 2.5" to 3.0" for bright CO isotopologues; 3.0" circular aperture for upper limits; channel width delta_v = 0.5 km s^-1
- 2018A&A...620A..31M: M 5-50 Msun, Rinner 10-50 au, Router 100-600 au, p+q -2.6 to -1.8
- 2024A&A...682A..61C: Central mass 0.15 Msun; v_sys explored 2.9 to 3.9 km/s
- 2024A&A...682A..61C: PV path width equal to the beam, 1.6 arcsec
- 2023ApJ...956L..45G: Critical density 1.5e6 cm^-3 taken as minimum density of the toroid; toroid size ~780 au x 390 au
- 2013PASJ...65L..14F: free: systemic velocity, center, inclination; stellar mass fixed at 2.2±0.3 Msun
- 2019ApJ...884L..56T: 256 walkers, 500 burn-in steps, 10,000 sampling steps; fit region 0.26'' to 3.75''
- 2019ApJ...884L..56T: Inclination fixed at 5.8 deg
- 2024MNRAS.534.2904C: r_min varied in eddy fit to test residual dependence
- 2024MNRAS.534.2904C: HD 142527: primary 1.8 Msun, length rescale 3.8, i=27 deg, PA=-20 deg
- 2021ApJ...908..141H: Only low-frequency part of line 5 and high-frequency part of line 7 used because of blending
- 2018ApJ...860..119G: 5-sigma threshold
- 2024ApJ...966...32E: PV cut angle = Gaussian-fit position angles; PV line width ~1 beam
- 2024ApJ...966...32E: Source A PV extended to 2 arcsec, source B to 1.5 arcsec; only the opposite side of each disk fitted to limit contamination
- 2021A&A...653A.166C: Central object mass 0.05-0.26 Msun adopted from infall models
- 2013Natur.493..191C: CO abundance 1e-4, HCO+ 1e-7, T=50(r/50AU)^-1/2 K, gap well-depth 1/10, total mass 0.1 Msun
- 2018ApJ...859..111H: Channels with SNR>5 used for astrometry
- 2024ApJ...972...88L: HCO+: Briggs robust = 0.5
- 2024ApJ...972...88L: H13CO+ and N2H+ J = 4 - 3: natural weighting, 0.5 arcsec taper
- 2024ApJ...972...88L: N2H+ J = 3 - 2: natural weighting; both N2H+ masks have three hyperfine components
- 2024ApJ...972...88L: Same Keplerian masks and velocity ranges as observed moment maps
- 2020MNRAS.496.5330F: Threshold >3sigma (sigma = 2.4 mJy/beam) for zero-moment map
- 2020MNRAS.496.5330F: Jet 1 PA = 222 deg, Jet 2 PA = 195 deg, systemic velocity v_lsr = 6.3 km s^-1
- 2017A&A...603A..10B: T = T_rot; T = 200 K; T ∝ r^-0.4 with 1400 K at 10 AU
- 2025A&A...694A.295P: Grid 10x10x5: total mass 5e-4 to 5e-1 Msun, outer radius 20-500 au, inclination 15-75 deg; inner radius 11.2 au
- 2021MNRAS.507.1886F: Reflection nebula direction P.A. ~ 40 deg; systemic velocity v_sys ~ 9 km s^-1
- 2015ApJ...813...99F: Fixed: d=122 pc, M*=2.3 Msun, PA=312 deg, Mgas=0.09 Msun, CO/H2=1e-4 (unless varied)
- 2019ApJ...880...69Y: free parameters M_star, V_sys; PA 138 deg, i 47 deg fixed
- 2025ApJ...994..214T: 200 walkers; minimum burn-in 1000 steps; convergence evaluated from 2500 steps
- 2025ApJ...994..214T: Position offsets restricted to initial imfit guess +-0.25 arcsec; V_LSR +-1.2 km/s (+-2.4 km/s for low S/N)
- 2025ApJ...994..214T: Temperature exponent q range expanded from [0,1] to [0,2] for sources piling up at q = 1
- 2022ApJ...937...10L: Lines with E_u < 120 K
- 2016ApJ...826..213L: systemic velocity refined to 8.85 km/s to fit both sides
- 2026MNRAS.551g1411H: 10,000 walkers, 500 burn-in steps
- 2021PASJ...73..205T: velocity integration range = -2 to +4 km s^-1
- 2017NatAs...1E.130Z: v_turb fixed at 0.01 km/s; outer-disk T = 21 K; fixed stellar mass 0.6 Msun, i=7 deg, PA=155 deg
- 2025ApJ...985...84L: multiscale pixel scales [0,5,15,25]; CLEAN to 4 sigma, sigma from five line-free channels of the dirty image
- 2025ApJ...985...84L: velocity binning to channel spacings 0.13-1.20 km/s depending on the line
- 2025ApJ...985...84L: robust chosen manually to maximize detection SNR
- 2025ApJ...985...84L: uncertainty = standard deviation of fluxes in 500 random Keplerian masks over line-free channels
- 2023ApJ...956..135W: target_res = 0.4 arcsec, dV0 = 500 m/s
- 2023ApJ...956..135W: filters: Keplerian masks of 120 au and 260 au radius
- 2017SciA....3E2935L: Ro=68±12 AU, Rt=36±8 AU, ht=12±4 AU, nt=2.2±0.6e10 cm-3, Tt=73±10 K
- 2024A&A...690A..46S: Systemic velocity 2.84 km/s fixed after first fit
- 2020ApJ...893...51S: M*=1.6 Msun, Mdisk=0.0071 Msun, p=0.5, i=73 deg; inner 0.1-200 au PA 69; outer 300-600 au PA 54
- 2015ApJ...808...69B: free parameters: inner hole radius R_in and M_*
- 2019ApJ...883...22C: q fixed to 0.5; i_disk fixed to 56.15 deg; gamma=1; d=131.2 pc
- 2024ApJ...964..190L: tclean threshold: 3.5 sigma
- 2024ApJ...964..190L: 12CO 2–1: channel width 0.30 km s−1; JvM epsilon=0.61
- 2024ApJ...964..190L: 13CO 2–1: channel width 0.20 km s−1; JvM epsilon=0.46
- 2024ApJ...964..190L: C18O 2–1: channel width 0.40 km s−1; JvM epsilon=0.46
- 2024ApJ...964..190L: 12CO 3–2 and HCO+ 4–3: channel width 0.43 km s−1
- 2020ApJ...899..157T: robust 0 / -1 / 0.5 for Bands 3/6/7
- 2020ApJ...899..157T: inclination 6.5 deg, PA 151 deg; 1.5 km/s window; 40 m/s binning
- 2018A&A...614A..26A: Centre at geometric centre; inclination 80 deg
- 2025A&A...693A..76C: PA_d fixed to 48 deg; Rd=0.3"=490 au
- 2020ApJ...897L..33J: M*=15 Msun, rmin=13 au, Te=5850 K, inclination -25 deg, v0=10 km/s
- 2016ApJ...818..156C: p fixed to 1; 12-dimensional posterior
- 2024AJ....167..164B: uvcontsub fit order 1
- 2024AJ....167..164B: velocity resolution 0.9 km/s for all windows
- 2024AJ....167..164B: Keplerian filter outer radius 300 au
- 2020MNRAS.493L.108B: 0.2'' uv-taper; first moment with 2.5 sigma clip
- 2020MNRAS.493L.108B: instability threshold Q<~1.7
- 2019ApJ...884...42S: Channels around cloud systemic velocity ignored; scale height free; a_dep typically <0.1
- 2026ApJ..1003..219W: Core mass 500 M⊙; radius 0.1 pc; central object 40 M⊙
- 2020A&A...634L..11J: vlsr = -52.5 km/s; mean molecular weight 2.37
- 2016Natur.535..258C: PA 32.4 deg, inclination 38.3±1 deg, v_src 4.3 km/s, distance 414 pc
- 2024ApJ...965..147B: i=6.8 deg, PA=151 deg, Mstar=0.6 Msun, d=60.1 pc
- 2024ApJ...965..147B: Annulus width 1/4 beam FWHM (~80 mas); weights proportional to r^2; centre offset (-52, -155) mas
- 2023MNRAS.518.4481L: Radial range: from beam FWHM to ~500 au (IM Lup 12CO) and ~400 au (GM Aur both lines and IM Lup 13CO)
- 2023MNRAS.518.4481L: Line centroid methods: Gaussian and Quadratic
- 2018ApJ...854...56L: q=0.5, p=1, inclination 80 deg
- 2025ApJ...992...18P: Inclination i = 47 deg
- 2020ApJ...904...78S: L*,pre = 0.5 Lsun; model-derived L*,burst; protostar masses 0.1 to 0.5 Msun
- 2017ApJ...835...17M: Free parameters: M*, i, PA, r_c, T10, q, Mgas, xi, vsys, RA/Dec offsets
- 2026ApJ..1003L..30W: Mask geometry i = 5 deg, PA = 152 deg, M* = 0.88 Msun, d = 59.5 pc, dr = 0.1
- 2026ApJ..1003L..30W: i = 5 deg, PA = 152 deg, distance 60 pc, M* = 0.88 Msun
- 2026ApJ..1003L..30W: Extraction radius 90 AU; integration range 2.0-3.7 km/s
- 2021MNRAS.501.4317P: 1000 bins from 0 to 400 au; 10 million random orbital parameter sets; e in [0, 0.7]; omega in [0, 2pi]; M in [0, 2pi]; a_p = 1.6088'' (KK Oph, d=221 pc) and 1.…
- 2019A&A...623A..77S: H/R=0.1, inclination 10 deg, 20 Msun, CH3CN abundance 2e-8 at 500 au, grid 152x20
- 2026MNRAS.551g1645K: PV contour levels: starting at 3 sigma in increments of 3 sigma; knot interval = 0.2 arcsec
- 2018ApJ...854..130W: Free: M_disk, r_c, gamma, T0, q, xi, v_sys, inclination, PA
- 2025ApJ...984L..18T: Briggs robust 0.5, multiscale scales [0, 5, 15], gain 0.08, small scale bias 0.45
- 2025ApJ...984L..18T: Continuum channels averaged to a maximum width of 125 MHz
- 2025ApJ...984L..18T: Elliptical apertures with the disk aspect ratio and orientation
- 2021ApJ...908..250H: PA 165.71 deg and i 75.13 deg taken from the visibility fit
- 2017ApJ...843...45K: major axis PA 129±3 deg
- 2024ApJ...961..228S: Outflow area: intensity > 0.5 K km/s; v_sys = 4 km/s; i_out = i_ring
- 2023MNRAS.519L..68B: Greenhouse correction factor 4/psi ~ 1/10; HII region timescale ~ 10^5 yr
- 2017ApJ...851..132C: data averaged to 25 channels of 0.4 km/s; fixed d = 388 pc
- 2024A&A...687A.311A: 256 walkers, 40000 steps, first 6300 steps burn-in
- 2024A&A...687A.311A: Reference radius r0 = 100 au; search ranges per parameter listed in Table 5
- 2024A&A...687A.311A: PA defined from north to the blueshifted semi-major axis
- 2022A&A...662A.121R: 5 free parameters (ra, dec, PA, i, v_LSR) and 2 fixed parameters (M_star, d); three fits per target at M_star and +/-1 sigma M_star
- 2018A&A...617A..89C: grid 2x2500 au, 0.7 km/s velocity resolution, n∝r^-1.5, ring 300-900 au, vrot=4.5 km/s at 300 au; Keplerian disk up to 600 au
- 2026A&A...713A.149V: Density profile power-law index p = 0 for prestellar cores and p = 2 for protostellar cores; core radius R = FWHM^dec
- 2014ApJ...788L..34P: moment 0 over -2.1 to 14.0 km/s; moment 1 voxels >3 rms, pixels with integrated intensity >0.4 Jy/beam km/s
- 2018RAA....18...31P: three r intervals 0.4 arcsec wide between 1.3 and 2.5 arcsec; 24 omega intervals of 15 deg
- 2024A&A...684A.174P: robust = 2.0 (C2H), 0.5 (CN); channel spacing 200 m/s (C2H), 100 m/s (CN)
- 2024A&A...684A.174P: Vertical widths up to 50 au give linewidth variation <=25 m/s beyond 150 au
- 2023A&A...678A.146B: uvcontsub fit order = 1; Briggs robust = 0.5 or 2.0; 0.4" uv-taper for 2016.1.00344.S lines (except HC3N); 0.25" uv-taper and 0.2" imsmooth kernel for CS J=7-6
- 2024ApJ...964...34L: Lbol 5.3 Lsun, Rstar 2 Rsun scaling; QR = 4, Tsub = 1500 K
- 2020ApJ...896..127K: R = 2500 au (0.5"), v = 3 km/s
- 2025ApJ...986L...9B: Briggs robust 2.0; channel width 0.55 km s−1.
- 2025ApJ...986L...9B: 1.0 arcsec Keplerian mask for integrated intensity maps.
- 2025ApJ...986L...9B: Flux uncertainty propagated from line-free rms and mask pixel count.
- 2020MNRAS.491.1335R: stellar mass prior 1.5 +/- 0.15 Msun
- 2017ApJ...837..174O: envelope thickness 30 au, density r^-1.5; M, r_CB, i free
- 2024A&A...692A.181Z: Keplerian curves for M sin^2 i = 10 and 15 Msun overlaid (not fitted)
- 2020A&A...634L..12D: i = 63 deg
- 2015A&A...582L...5R: q=0.5, p_d=0.1 fixed
- 2017ApJ...846L..26W: Free: Mdisk, Rdisk, gamma, T0, q, xi, M*, vsys, inclination, PA, small centering offset
- 2026ApJ..1003...64Y: 100 walkers, 15,000 steps, 2,000 burn-in
- 2021A&A...651L...5V: Keplerian mask parameters: d=135 pc, i=50 deg, M*=2.0 M_sun, v_source=4.55 km s^-1
- 2021A&A...651L...5V: Shared flux of blended p-H2CO 5_{4,2}-4_{4,1} and 5_{4,1}-4_{4,0} divided by 2
- 2019A&A...626A..71A: Velocities above ±2 km/s used to avoid envelope
- 2024A&A...686A.146Z: Density contrast C = 100
- 2021A&A...655A..72S: gamma=7/5, mu=2.8 for sound speed
- 2019ApJ...874..136S: 200 walkers; ~5000 post-burn-in steps; autocorrelation time ~1000 steps; walkers with chi2-chi2min>44 discarded
- 2024ApJ...969..165D: 253-1536B mask: inclination 45 deg, PA -90 deg
- 2021ApJS..257....6G: Radial bin size = 1/4 of the beam major axis
- 2021ApJS..257....6G: Averaging wedge = 30 degrees along disk major axis (or full azimuthal average for low S/N: C2H in IM Lup and GM Aur, and H2CO in all sources)
- 2019NatAs...3..517Z: weights w_pos=0.9, w_int=0.1; thermal broadening FWHM 19 km/s
- 2018ApJ...869L..50P: Free: i, PA, vsys, x0, y0; inner/outer radius fixed 0.3 and 250 au
- 2024Sci...383..988B: Stellar masses 0.1, 0.2 and 0.3 M⊙.
- 2024Sci...383..988B: Synthetic channel spacing 0.05 km/s; resampled velocity resolution 0.1 km/s.
- 2020ApJ...904..125S: Aspect-ratio upper bound 0.2; solutions with h_c above 0.2 discarded
- 2019ApJ...881..112O: M=1.0 Msun, i=65 deg, PA 0 deg, radius 100 au, emissivity r^-2.0
- 2024ApJ...970...28O: Disk/envelope height 20 au, R_out 24 au (CH3OH) and 10 au (HCOOH), P.A. 5 deg, i 70-90 deg, Mstar 0.02-0.08 Msun, r_CB 2-9 au
- 2017ApJ...844..158S: R_in = 0.1 au; scale height fixed
- 2024A&A...692A.155K: Elliptical emission masks of 0.4 and 0.28 arcsec for A and B; velocity pixels 4 mas, not downsampled
- 2024A&A...692A.155K: Center, inclination and PA fixed from the continuum outer-disk fit; free: stellar mass and systemic velocity
- 2020ApJ...901...71S: HD 142527: M* = 2.8 Msun, PA_red = 160 deg, i = 28 deg, d = 157 pc; IM Lup: M* = 1 Msun, PA_red = 144 deg, i = 48 deg, d = 158 pc; z0 = 0.1'' for both; IM Lup …
- 2020ApJ...901...71S: rmax where Stokes I drops to 90% of peak moment 0 value, rounded to 3'' (HD 142527) and 4'' (IM Lup); rmin alternates 0 and 0.17'' (HD 142527) or 0 and 0.5'' (…
- 2020ApJ...901...71S: Other GoFish inputs left at defaults
- 2018A&A...612A..72J: Freeze-out factor 0.01 below 30 K; abundances lowered by factor 5 for matching C18O
- 2018A&A...619A.171B: 5 free parameters; 1000 steps, 80 walkers; inner radius 2.2 au, outer 250 au
- 2020ApJ...900....7H: 100 walkers, ~2500 steps; distance 131.2±1.7 pc
- 2019ApJ...872...64K: thermal width 3 km/s; systemic velocity 6 km/s; PA 140 deg
- 2026AJ....172..108L: Velocity integration ranges: -15 to 5 km s^-1 (blueshifted) and 15 to 35 km s^-1 (redshifted)
- 2018ApJ...852..122H: Fiducial: N_CO=3e19 cm-2, R1=15 AU, R2=70 AU, A=3, f=0.025, Tmid10=40 K, Tatm10=125 K, q=0.47, Tfrz=27 K, Rin=0.05, Rout=215 AU
- 2024ApJ...974..102S: fit radii 0.33 to 1.4 arcsec; inc and PA fixed from continuum
- 2022A&A...659A..29B: robust = 0.5
- 2022A&A...659A..29B: phase centre = ICRS 16:27:37.17 -24:30:35.55
- 2022A&A...659A..29B: channel width ~ 1.7 km s^-1
- 2019ApJ...876...72L: Disk inclination, PA, stellar mass from Table 1
- 2025ApJ...989...41A: h_0 = 5 au, p = 1
- 2025ApJ...989...41A: v_sys,* = 3.9 km/s (uncertain by 0.5-1.0 km/s)
- 2025ApJ...989...41A: Outer disk radius 150 au
- 2020ApJ...904L...6A: Central channels of 12CO contaminated by cloud; C18O less contaminated
- 2026MNRAS.551g1639M: R_* = 2 R_sun, d = 138 +/- 2.6 pc
- 2018ApJ...857...69B: blended lines: lower-energy flux = 2x low-velocity horn; extra 30% error added in quadrature
- 2024A&A...686A.120U: 3 sigma threshold
- 2020ApJ...895..109F: Free: T_atm0, q, R_c, i, δv_turb, R_in, v_sys; fixed PA, γ=1, T_mid0, Z_q0, masses
- 2019ApJ...884..146T: reference velocity 13.9 km/s
- 2019A&A...624A...7V: velocity resolution 0.11 km/s
- 2024A&A...687A.188K: Front and back layer heights imposed equal (z_b = -z_f); four free height parameters (z_f0, psi, phi, r_z)
- 2024A&A...687A.188K: Cloud absorption Gaussian with three free parameters: velocity center, width, amplitude
- 2020ApJ...894...74B: free: M*, r_in, R, i, theta, beta, vsys, x0, y0, F
- 2018ApJ...862L...2F: M*=0.7 Msun, i=7 deg, PA=155 deg, vsys=2.7 km/s, d=59 pc, Rout=400 au
- 2025ApJ...984L..10G: 5 iterations; maximum beamsize decreased from 2 beams to 1 beam; minimum SNR increased linearly from 1.0
- 2025ApJ...984L..10G: Final SNR clips 5.0 (12CO), 3.5 (13CO), 3.0 (CS)
- 2025ApJ...984L..10G: Points binned by a quarter of a beamsize
- 2021A&A...646A..59R: Major-axis P.A. ~93.5 degrees; CN B reference
- 2018NatAs...2..646H: Trot 40-80 K
- 2026A&A...705A..96M: Inner τ∝r^p with p=0 and −1.5; mass integration R=rc
- 2023NatAs...7..684K: cell size = 0.5", image region = 20"x20", velocity integration range = -14.5 to 25.5 km s-1, elliptical aperture radius = 5.0"
- 2018ApJ...865..155C: Turbulent velocity 100 m/s; emission limited to 500 AU; 40x oversampled spectral resolution
- 2026MNRAS.552g1700S: 230 walkers; burn-in of 80,000 steps (12CO) and 30,000 steps (13CO) plus 10% sampling steps; 13CO inclination and PA fixed to 37.0 deg and 45.1 deg
- 2023MNRAS.522.2384M: Channels at radial velocities of +/- 2.8 and +/- 3.0 km/s with respect to V_sys = +1.6 km/s, peaking at 0.37'' and 0.33''
- 2026ApJ..1005..199C: PA, incl, M_star, Dist, v_sys, and CO Mask Radius per disk as listed in Table 3; velocity ranges in Table [tab:flux]
- 2022MNRAS.513.5790C: Time interval = 1.75 yr; fake point source flux = 126 uJy; disc inclination i = 130 deg, PA = 160.4 deg
- 2018ApJ...867...43T: PA uncertainty ±10 deg
- 2016ApJ...832..204Y: Radial ranges R<300 AU (DCO+, H2CO), R<200 AU (DCN), 100<R<300 AU (N2D+)
- 2025ApJ...986L..11S: Inclination fixed at 49.9 deg
- 2021ApJ...910...75L: M ~0.25 Msun, Mdot ~5e-6 Msun/yr, Sigma ~1.14 g cm^-2 at R_t
- 2016ApJ...830...32W: CO freeze-out 20 K; dissociation N_H2 > 1.3e21 cm^-2; 12CO/H2 = 1e-4; 12CO/13CO = 70
- 2025ApJ...989....1Z: 0.1 km/s channels for 12CO, 0.2 km/s others
- 2019AJ....157..237R: planet at 20 au, inclination 32 deg, central mass 1.75 Msun
- 2024ApJ...976..132H: Adam optimizer, learning rate 0.02, 15,000 iterations; 2000 posterior samples
- 2021A&A...646A...3L: Stacking with M_star = 1.3 Msun, i = 38 deg, PA = 32 deg; acetaldehyde line frequencies fixed, widths fixed to 2 km/s
- 2024NatAs...8..587F: R_in = 0.1 au; 150 radial and 550 azimuthal points
- 2020ApJ...890..142P: r0 = 100 AU, q = -0.3, v0 = 0.3 km/s (0.6 for 4_14, 4_13; 0.15 for J1604-2130)
- 2018ApJ...859...21A: PA and i from Tazzari 2017 / van der Marel 2018
- 2026ApJ..1002..176C: Absorption Gaussian FWHM 29.65 km/s used as convolution kernel
- 2020MNRAS.492..572A: Mdust 1e-6 to 1e-3 Msun; Rc = 10, 30, 100 au; flaring 1.0-1.30; H0 = 5-20 au at 100 au; gamma 0-1.5; amax 10 to 10000 um
- 2017MNRAS.467L..76S: Keplerian model mass 0.18 Msun, outer radius 160 au
- 2025ApJ...984L..13H: 30 cube samples (convolved); data downsampled 2x2 for the re-fit versus 6x6 in the production fit
- 2023ApJ...948..110Y: Common beam: 0.105'' x 0.105''
- 2017A&A...606A.125S: stellar mass 2.3 Msun
- 2026A&A...708L...1Z: M_star = 1, 0.5, 0.05 M_sun; inclination = 8, 30, 55 deg; R_c = 5, 20, 50 au; integration time ~180 s per disk
- 2020ApJ...898...97B: Detection: flux >3σ and >3σ emission in moment zero map
- 2024ApJ...973..135H: i = 5.4 deg, PA = 3.4 deg (Long 2019); v_sys = 9.9 km/s, M_star = 1.18 Msun (Braun 2021)
- 2024A&A...688A.149D: inclination fixed to the continuum value
- 2017ApJ...840...60B: moment I excludes pixels below 5 sigma
- 2024A&A...687A.299L: Briggs robust 0.5
- 2024A&A...687A.299L: multi-scale scales 0,5,10,20 with a slight uv-taper of 0.05'' x 0.05''
- 2020ApJ...893..101L: templates: 12CO, 13CO, C18O, DCO+, H13CO+, plus H2CO, N2H+, CS from survey
- 2024ApJ...971L..15Y: v_out~5.6 km s^-1
- 2019Sci...366...90A: SNR threshold 5; PV emission >5σ
- 2020A&A...638A..38T: Keplerian mask parameters M*, PA, i, centroid from literature; Vsys and DeltaV_int tuned to maximize S/N
- 2019ApJ...882L..31B: PA 132, inclination 42, source velocity 5.8 km/s
- 2025ApJ...984L..19Y: annulus width 0.05"; i = 6.0 deg fixed
- 2018MNRAS.478.2505I: Initial inclination 45 deg for sources without prior constraint
- 2024ApJ...970..153A: 0.05'' radial bins
- 2023PASJ...75..424O: emitting surface height ratio 0.13
- 2024RAA....24g5017M: Briggs robust 0.5
- 2023NatAs...7...49C: HD 163296 synthesised beam 0.3 arcsec
- 2018ApJ...860L..13P: 1 million SPH particles; central mass 1.9 Msun; disc 50-500 au; gas mass 1e-2 Msun; Sigma critical radius 100 au, p=-1.0, gamma=0.8; H/R 0.08 at 50 au; alpha 1…
- 2025ApJ...984L..21B: 2000 burn-in steps plus 4000 sampling steps; r_in=20 au, r_out=100 au; PA fixed, vLSR=0, distance 140 pc
- 2024AJ....167...66Y: PA 32 deg, i = 38.3 deg, M* = 1.29 Msun, d = 400 pc
- 2018A&A...620L...1G: v_sys ≈ 5.5 km/s
- 2025ApJ...993...90S: 3 sigma_CO threshold
- 2026ApJ...997L..19Q: robust = 0.5, 3-sigma CLEAN threshold, 0.28'' x 0.25'' beam, 2-sigma intensity clip for moments
- 2018ApJ...857...87L: Dust opacity 3.95 cm2/g at 1.3 mm; inclination 42 deg; rotation 132 deg; Keplerian around 2.3 Msun
- 2024A&A...689A..65R: Filter mask outer radius 1 arcsec (218 GHz) and 2 arcsec (244 GHz)
- 2019ApJ...877..100Y: flaring angle phi = 0.02
- 2017A&A...605A..21C: Keplerian mass 2.3 Msun
- 2024ApJ...975...72B: Briggs robust 0.5; velocity resolution 1.7 km/s (2017.1.00834.S) and 0.9 km/s (2021.1.00738.S)
- 2024ApJ...975...72B: Map errors are the rms of line-free regions of the images without Keplerian masking
- 2026ApJ..1009L...3B: Besancon query: distances 0-50 kpc, radius 5 arcmin around Elias 2-24, apparent L' = 15-17 mag, FoV = 2.6 arcsec
- 2018A&A...614A.106C: Keplerian mask with M = 1.65 Msun
- 2024A&A...686A...9M: nu = 283 GHz, T = 20 K, kappa_nu = 2.3 (nu / 230 GHz)^0.4 cm^2 g^-1
- 2017ApJ...836...30G: Detection: Keplerian emission in at least three channels at 3 sigma
- 2025A&A...703A.282R: S/N > 4 threshold for unmasked moment maps; spectral smoothing factor = 3; integration radius = 1.6 arcsec
- 2025A&A...693A.286S: Keplerian mask velocities determined by eye so all emission is enclosed; a mask was applied even when inclination and PA were not available
- 2025ApJ...989....3D: velocity spacing 0.1 km/s for 12CO, 0.2 km/s other lines; CLEAN to 1 sigma
- 2019MNRAS.486.4638U: M*=1.67 Msun, d=162 pc, PA=55 deg, i=35 deg for Keplerian compensation
- 2026A&A...705A.193L: 183 GHz integrated -8.5 to 22.5 km/s
- 2019ApJ...876...25B: Detection: flux >3σ and at least 3 channels >3×rms
- 2017ApJ...840...32T: M* = 2.4 Msun, vsys 5.85 km/s, i 23.2 deg
- 2019ApJ...876L..13S: Ring 0.8'' to 2''


### Assumptions (bibcode: value)
- 2019Natur.574..378T: Distance 101 pc; inclination prior 46.7 +/- 0.1 deg
- 2019Natur.574..378T: Deprojection with i = 46.7 deg
- 2024ApJ...976..258K: Keplerian mask geometry M* = 1.37 Msun, i = 37 deg, PA = 278 deg rescaled to 150 pc
- 2024ApJ...976..258K: Boltzmann level populations, temperature power law in radius
- 2024ApJ...976..258K: Same vertical distribution for all molecules; constant intrinsic line width with radius
- 2024ApJ...976..258K: Distance 150 pc
- 2021A&A...650A..59B: geometrically thin disk (gas scale height not fitted)
- 2021A&A...650A..59B: distance of 157 pc
- 2021A&A...650A..59B: vertical motions neglected in the radial Doppler-shifted structure
- 2021A&A...650A..59B: pure Keplerian rotation around a single star of 2.36 Msun, inclination 27 deg, PA -19 deg
- 2021A&A...650A..59B: gas surface density three to five times larger on the northern side of the disk, with radial pressure gradients adding non-Keplerian motions
- 2018ApJ...865..131L: Circular disk; inclination from arcsin(b/a)
- 2018ApJ...865..131L: L_int is entirely from accretion; constant accretion rate
- 2025SciA...11.6953M: Velocity gradients are interpreted as infall toward the central object
- 2025SciA...11.6953M: Rotating-plane inclination between 0 and 20 deg (0 deg = face-on); 10 deg plane used for the polar angle
- 2025SciA...11.6953M: Model has only a central point mass; 45 Msun best fit considered too massive for an early protostar
- 2025SciA...11.6953M: Stellar mass 8-16 Msun from spectral type B3-B0 gives disk inclination 20-30 deg
- 2020ApJ...904..181L: Axisymmetric circumstellar structure; inclination i=0 is face-on
- 2020ApJ...904..181L: Flattened two-dimensional structure; empirical column-density and temperature profiles; gas-to-dust ratio 100
- 2020ApJ...904..181L: LTE; no interferometric spatial filtering of model cubes
- 2020ApJ...904..181L: Neglect gas self-gravity in the gas-kinematic model calculations
- 2020ApJ...904..181L: Include gas inertia, stellar gravity and circumstellar gas self-gravity
- 2020ApJ...904..181L: Gray approximation for direct stellar irradiation and radiative transport; no magnetic field
- 2012ApJ...757..129R: vertically isothermal, mu=2.37, Keplerian, vr=vz=0
- 2012ApJ...757..129R: vertically thin warped disk aligned with major axis
- 2014ApJ...793....1Y: d=140 pc, LTE, X(C18O)=3e-7, Gaussian line profile
- 2014ApJ...793....1Y: Gravity dominated by 1.6 Msun protostar, conserved angular momentum, zero total energy
- 2016A&A...596A..92K: i = 82 ± 5 deg; parallax 15.61 mas; B mass not subtracted
- 2016A&A...596A..92K: Only one companion besides star A
- 2016A&A...596A..92K: Circular orbit coplanar with the disk
- 2026A&A...705A.201B: Keplerian rotation for stacking
- 2026A&A...705A.201B: Geometrically thin disc
- 2026A&A...705A.201B: Local line shape independent of azimuth, admitted not to hold in the data
- 2026A&A...705A.201B: LTE level populations; Keplerian rotation with 1.89 Msun
- 2026A&A...705A.201B: Vertically thin disc; gradient constant across the beam; Keplerian velocity field
- 2020MNRAS.498.1319M: Optically thin CO emission, non-LTE excitation
- 2020MNRAS.498.1319M: Fractional luminosity ~3e-4, stellar mass 1.3 Msun, luminosity 2.9 Lsun, disc radius 70 au and width 100 au, photodissociation timescale 120 yr
- 2017ApJ...850L...5T: inclination i~0 deg (edge-on orbit); apoastron PA~60 deg to line of sight
- 2024A&A...692A.151S: constant electron temperature across the wind
- 2024A&A...692A.151S: distance 650 pc
- 2024A&A...692A.151S: constant rotation velocity because resolution cannot distinguish Keplerian from momentum-conserving profiles
- 2013ApJ...776...77K: Keplerian rotation, power-law brightness I(r)~r^p, models normalized to observed total intensity
- 2022MNRAS.510.2363H: Gaussian line profile approximation to convert V_{z,20} to effective FWHM line width
- 2024ApJ...970...74P: All fitted sources bound to Sgr A*; black-hole mass 4.02 × 10^6 M⊙
- 2013PASJ...65..100I: Keplerian rotation, thin disk; lower limit due to beam smearing
- 2021AJ....162...14A: reference epoch 2019.5 chosen to match the majority of the ALMA data; second-order effects treated as linear perturbations
- 2021AJ....162...14A: intrinsic RV shift of A taken as zero
- 2020ApJ...902...99I: Torus inclination i ~ 90 deg (edge-on); even i = 34–66 deg raises intrinsic velocity by only 1.1–1.8
- 2023ApJ...953L...6P: Perfectly edge-on Keplerian disk with H26alpha and H30alpha masers localized on two thin annuli of fixed radii equal to the spatial extent of the masers; high-…
- 2017MNRAS.468.1769F: Exponential disk rotation curve of Lundgren 2004b
- 2022MNRAS.515..543C: Inclined Keplerian disk; for B: disk inclination = 74 deg, protostellar mass = 1.7 M_sun, d = 131 pc; for A1: disk inclination = 47 deg, protostellar mass = 0.…
- 2025A&A...704A...7P: Distance to Sgr A* = 8 kpc, mass of Sgr A* = 4x10^6 M_sun (uniform priors)
- 2020PASJ...72L...5T: The NA trajectory is Keplerian; CH3OH decays gradually while the arm falls toward Sgr A*
- 2025ApJ...988L..44F: emission from a Keplerian disk
- 2015A&A...574A...5D: Primary mass 4 Msun, companion less massive
- 2018ApJ...868..113T: i = 35.3 deg fixed
- 2018ApJ...868..113T: i = 35.3 deg fixed; z = r tan psi
- 2024ApJ...967...68H: LTE
- 2024ApJ...967...68H: Same excitation temperature for ortho and para
- 2024ApJ...967...68H: Gaussian line profile centred at v_sys = 5.8 km/s
- 2024ApJ...967...68H: Emitting layer in the midplane (z/r = 0) for the disk-averaged case
- 2024ApJ...967...68H: Background temperature is the maximum of dust continuum brightness temperature and the CMB (2.73 K)
- 2024ApJ...967...68H: LTE, shared T_ex for ortho and para, same emitting region for all lines (acknowledged in footnote)
- 2021AJ....162...99F: line emission follows the Keplerian model fitted to 12CO 3-2
- 2021AJ....162...99F: Keplerian kinematics from Keppler+2019 apply to all lines
- 2019ApJ...873...73Z: Disk mass neglected for Keplerian curve; inclination i defined edge-on = 0
- 2019ApJ...873...73Z: Optically thin emission, universal excitation
- 2025ApJ...985..166K: Core depth equals its 850 um continuum diameter of 140''
- 2025ApJ...985..166K: Surface density from core plus central protostellar mass within a 60'' box
- 2025ApJ...985..166K: NW and NNW streamers share the disk rotation axis and have centrifugal radius equal to the gas disk radius
- 2025ApJ...985..166K: Isothermal 15 K, LTE, optically thin C18O; dust opacity table of Semenov et al. 2003
- 2025ApJ...985..166K: Accretion luminosity is 50% of the bolometric luminosity
- 2020ApJ...904..185O: Optically thin line emission, no radiative transfer, ballistic motion conserving energy and specific angular momentum for IRE model
- 2020ApJ...904..185O: Optically thin line emission, center of gravity at continuum peak A1
- 2013ApJ...774...16R: Keplerian rotation, no v_z
- 2013ApJ...774...16R: circular orbits; self-gravity omitted from hydrostatic density
- 2014ApJ...786..114L: Dust and gas same temperature; LTE; kappa from Beckwith1990 with beta=1; thermal line width only; free-fall infall and constant specific angular momentum in th…
- 2014ApJ...786..114L: R* ~ 2 Rsun for accretion luminosity
- 2017ApJ...842....8M: Negligible vertical thickness (opening angle ~1 deg); temperature T ∝ r^-0.5; ω_p random 0 to 2π
- 2019A&A...629A.136S: edge-on disk, Keplerian rotation, d=1.7 kpc
- 2019A&A...629A.136S: Isothermal, Keplerian disk, rotation also in winds, constant Te, departure coefficients from Storey & Hummer
- 2026A&A...705A.202M: Emission arises from the midplane (elevated-surface models gave heights consistent with zero)
- 2026A&A...705A.202M: Systemic velocity fixed to the value from the Keplerian fit (vertical/systemic degeneracy)
- 2026A&A...705A.202M: Mean molecular weight mu = 14 (C and O dominated, secondary gas) or 2.3 (H2 dominated, primordial); midplane z=0; power-law temperature
- 2026A&A...705A.202M: LTE, kinetic and excitation temperature 38 K at the belt centre decaying with exponent -0.14; mu = 14 or 2.3; radial and vertical velocities zero
- 2021MNRAS.506.1978L: Stellar mass = 1.1 M_sun, radial velocity v_rad = 27.82 +/- 0.15 km s^-1, CO photodissociation time = 120 years
- 2019ApJ...871L...1T: Dynamical center at (l,b,R) = (-0.0096°, -0.0451°, 8 kpc)
- 2025A&A...699A..22M: reference frame of the primary; momentum conservation relates the C tangential velocity to the PMa of A
- 2015MNRAS.447.3936M: CO co-located with dust, Keplerian, axisymmetric ring
- 2020CPhy...30...85D: Rotation velocity of 12 km s^-1 at 6 au (Homan et al. 2018b) for Keplerian test; solid body rotation of 1.0 ± 0.1 km s^-1 at 1.9 au (Vlemmings et al. 2018) for…
- 2026ApJ...999..145T: Keplerian motion of protoplanetary disk
- 2015ApJ...811...39I: HCN(4-3)/HCN(1-0)=0.6±0.2; conversion factor 10; i=45 deg; FWHM~200 km/s
- 2020A&A...633A.115K: Sigma = tau_V/kappa_V; irregular grains; central object 5 MJup, 16.67 Myr
- 2022PASJ...74..738T: Galactic center distance d = 8.0 kpc; GCBH mass M_GCBH ~ 4 x 10^6 M_sun
- 2016ApJ...827...69H: BH mass 1.4e6 Msun, edge-on disk
- 2017A&A...608A.134Y: Disk inclination 47 deg
- 2017A&A...608A.134Y: Arcs in disk plane for thin models; particles anywhere along line of sight for 3D
- 2025ApJ...984L..22W: The other three disks are close to face on and need no lower-surface removal
- 2025ApJ...984L..22W: Elliptical streamlines in the vortex frame, analogous to a shearing box
- 2025ApJ...984L..22W: Illustrative projection with i = 16 deg and PA = 243 deg (as HD 135344B)
- 2025ApJ...984L..22W: Flat disk; vortex magnitude may be underestimated
- 2021ApJ...906..111T: Emitting gas follows Keplerian rotation.
- 2021ApJ...906..111T: The adopted intrinsic linewidth gives an upper limit to opacity.
- 2019ApJ...872..176Z: inclination 55°
- 2019ApJ...872..176Z: optically thin emission; single temperature and density
- 2025A&A...701A.141L: Pure rotation along the ring; Keplerian rotation at 65 au
- 2025A&A...701A.141L: Central mass 0.35 Msun
- 2025A&A...701A.141L: Zero mechanical energy, non-zero specific angular momentum (parabolic orbit)
- 2025A&A...701A.141L: Edge-on rotating rings with Keplerian rotation, V_grad ~ r^-1.5
- 2021ApJ...907L..41L: Steady-state, axisymmetric, self-similar wind from a geometrically thin Keplerian disk
- 2021ApJ...907L..41L: Wind symmetric about disk midplane; extends 185 au north and south
- 2021ApJ...907L..41L: Outer wind 100 K; shell 200 K; jet 300 K
- 2015PASJ...67..122M: 13CO abundance 9e-7, C18O 1.35e-7, no scattering of line emission
- 2015ApJ...812...27A: LTE, X(C18O)=3.0e-7, zero turbulence, mean molecular weight 2.37 mH, position/PA from continuum, Vsys 6.4
- 2015ApJ...812...27A: omega ~ 1 km/s/pc (x2, x0.5), cs=0.19 km/s (10 K)
- 2016MNRAS.460.2933M: h=0.07 and orientation fixed to dust fit; Keplerian rotation; systemic velocity 0.1 km/s; electrons as collision partner
- 2018A&A...614A.113H: gas-to-dust mass ratio 100
- 2018A&A...614A.113H: 1 Msun central star
- 2026A&A...705A.203W: Neglect disc self-gravity, Poynting–Robertson drag and dust-particle collisions
- 2026A&A...705A.203W: Optically thin stellar irradiation; radiation pressure represented by a size-dependent effective gravitational potential
- 2026A&A...705A.203W: Gas-drag arc rotates at local Keplerian rate; resonant arc rotates with the planet
- 2022MNRAS.517.2546L: v_rad = -24.98 +/- 0.14 km s^-1; M_* = 1.8 M_sun (also tested 1.32 M_sun); PA = 146 deg; i = 61 deg; unshielded CO photodissociation timescale = 120 yr
- 2017ApJ...837...93Y: Sgr A* mass 4e6 Msun, distance 8 kpc
- 2024A&A...682A.143P: Period imposed from the light curve
- 2014Sci...343.1490D: stellar mass 1.75 Msun, circular orbits
- 2025PASJ...77..733T: GCBH mass M = 4 x 10^6 M_sun
- 2013ApJ...768L..38H: Black hole mass 1.7e6 Msun; Keplerian rotation
- 2017A&A...607A.114W: Stellar mass 2.4 Msun; Keplerian rotation; emission from flat or double-cone surface
- 2017A&A...607A.114W: Inner disk planar and flat Keplerian
- 2026A&A...705A..49Z: Emission from two thin layers, back surface mirrored from front (z_b = -z_f)
- 2026A&A...705A..49Z: Pure Keplerian rotation and purely thermal line width
- 2026A&A...705A..49Z: Temperature and optical depth profiles equal for front and back surfaces
- 2026A&A...705A..49Z: Model B: emission in the midplane with constant optical depth out to R_out
- 2026A&A...705A..49Z: Distances from Gaia DR3
- 2023ApJ...958...98F: d = 132 pc; i = 47 deg; Keplerian rotation forced to derive M_star
- 2023ApJ...958...98F: Negligible pressure gradient (supersonic flow); rigid-body rotation at spherical cloud boundary; negligible self-gravity (central star dominates); aligned clou…
- 2023ApJ...958...98F: Alcalá et al. (2017) Br-gamma scaling (a = 1.19 ± 0.1, b = 4.02 ± 0.51); Fitzpatrick (1999) extinction law; gas-to-dust ratio = 100; mean molecular weight mu =…
- 2018ApJ...869L..24I: Inclination ~70±10 deg from continuum aspect ratio of flat disk
- 2018ApJ...869L..24I: MM 1b kinematics dominated by Keplerian disk
- 2025ApJ...995L...7L: single power-law density and temperature across envelope, transition region and disk
- 2025ApJ...995L...7L: total mass of protostar plus disk 1.8 Msun; envelope mass neglected in infall velocity
- 2025ApJ...995L...7L: envelope ballistic with conserved angular momentum and energy; rotation and radial velocities same as mid-plane values
- 2020ApJ...904...77G: Disk axis consistent with jet direction; angular momentum points toward observer, i>90°
- 2020ApJ...904...77G: Radial electron emission measure truncated at R_e; n_e=sqrt(EM(r)/w_d)
- 2020ApJ...904...77G: Voigt HRL profile; H38β Lorentz width 8.75 n_e,8 km s^-1, n_e,8 in 10^8 cm^-3
- 2013Sci...340.1199V: 12CO/C17O=2500; H2/12CO=1.2e4; all gas in H2
- 2014ApJ...796..131O: edge-on, inclination 90 deg
- 2019MNRAS.482.3443B: Gas Keplerian with same inclination and PA as dust disc
- 2018A&A...614A..58B: LTE level populations, constant abundances, axial symmetry, D = 1100 pc
- 2025A&A...703A..15M: For non-detections, gas is co-located with dust in Keplerian rotation to define integration velocity range
- 2025A&A...703A..15M: Keplerian rotation around central star
- 2020MNRAS.492.6067M: unresolved emission interior to 4 au
- 2017ApJ...842...94T: GCBH mass ~4e6 Msun
- 2018ApJ...864..133T: M* fixed at 0.65 Msun
- 2025A&A...694A.108P: Exponentially tapered power-law emitting layers z(R) with Paneque et al. parameters; azimuthal symmetry; front side dominates
- 2025A&A...694A.108P: 12CO curve used as smooth Keplerian reference
- 2020ApJ...905...89Y: Observed emission approximated as Keplerian rotation around a central point mass; fitted Mstar represents the total binary mass
- 2020ApJ...905...89Y: Models are axisymmetric while the disk is asymmetric, leaving significant residuals
- 2020ApJ...905...89Y: Pressure bump width inferred from the separation between bump center and turning point, which is about 1.2 to 1.5 times the bump width for Gaussian profiles
- 2018ApJ...864L..25O: Keplerian rotation, no radiative transfer or self-absorption
- 2018ApJ...864L..25O: kappa = 6.8e-4 cm2/g at 1.2 mm; T = 20-100 K
- 2025A&A...694A..92B: Peak map represents a rotating disk
- 2025A&A...694A..92B: Outflow velocity ~30 km/s assumed from water maser proper motions
- 2023A&A...678A.160E: Material is free-falling with conserved angular momentum towards the central mass
- 2014ApJ...791...42Z: Gas-to-dust 100, CO/H2 5e-5, Keplerian rotation M*=1 Msun, i=6 deg, T_CO power law, CO outer edge at 17 K
- 2014A&A...566A..74L: Flat disc, n∝r^-1, T∝r^-0.5, LTE, optically thin, inclination 60 deg
- 2019ApJ...878..113H: T_gas = T_dust in stellar equilibrium, flat Keplerian disk, no turbulence
- 2017A&A...597L...5B: LTE level populations; distance 1 kpc
- 2026MNRAS.545f2150S: Star radial velocity in LSR frame ~1.5 km s^-1 (heliocentric 20.9 ± 0.6 km s^-1); Keplerian rotation around star
- 2020ApJ...892...99C: Mstar 1.7 Msun, i = 83.6 deg
- 2019A&A...632L..12H: Optically thin lines, equal excitation temperature, flux ratio = column density ratio within 1%
- 2025NatAs...9.1672Y: Parametric power-law-plus-floor form for omega(r)
- 2025NatAs...9.1672Y: Self-gravity of the disk neglected for the Keplerian profile
- 2025NatAs...9.1672Y: Planet-induced spirals rotate rigidly at the Keplerian rate at 117 au
- 2021A&A...648A..19W: 12CO optically thick and LTE so TB traces kinetic temperature
- 2021A&A...648A..19W: Razor-thin disc, distance 162 pc, inclination 35 deg
- 2017ApJ...849...56A: Distance 140 pc; inclination 85 deg
- 2025ApJ...989...56H: Edge-on Keplerian ring, disk mass much smaller than stellar mass
- 2025ApJ...989...56H: C18O emission dominated by the extended envelope
- 2025ApJ...989...56H: Inner radii of disk and envelope set to the dust sublimation radius
- 2020ApJ...905...25G: Single major accretion event; constant infall during transition
- 2020ApJ...905...25G: Keplerian disk with gas density constant as a function of radius
- 2015ApJ...806..154C: LTE level populations; Keplerian rotation dominated by binary mass; vertical hydrostatic equilibrium; vertically isothermal
- 2013A&A...560A.103M: d=120 pc; optically thin emission, constant density, adjusted temperature gradient
- 2019AJ....158..162F: Gas co-located with belt, Keplerian, optically thin
- 2019NatAs...3..408D: Circular orbit
- 2026A&A...705A.198M: Gas co-located with dust and near-Keplerian
- 2026A&A...705A.198M: Keplerian rotation, CO co-located with dust
- 2021AJ....161..271F: Toy model inclination 33 deg, stellar mass 1.56 Msun
- 2016ApJ...823L..18H: LTE; Keplerian velocities; ISM isotopologue ratios 69 and 557; T_atm,10=150 K, q_atm=0.5; C18O traces CO column
- 2024ApJ...966...63Y: Keplerian mask geometry: i=5.8 deg, PA=151.6 deg, M*=0.81 Msun, vsys=2.84 km/s
- 2024ApJ...966...63Y: LTE relative optical depth spectrum at T=40 K overplotted for comparison
- 2023A&A...669A..53B: Keplerian rotation around a stellar dynamical mass of 2.2 M_sun, source velocity of 5.7 km s^-1, and disk inclination angle of 32 deg (or 40 deg)
- 2018ApJ...869...59W: Dynamical center fixed at 2.9 mm continuum peak; moment 0 of model equal to observed
- 2024A&A...687A.308S: Surface density follows a power law; temperature power law in radius, vertically isothermal
- 2024A&A...687A.308S: Constant C17O abundance (1/2240 of CO), CO abundance 1e-4 relative to H2, no dust in the line model
- 2024A&A...687A.308S: C17O emission solely traces rotationally supported disks; envelope and streamer contributions negligible
- 2021A&A...650A.142M: Rotation in gravito-centrifugal equilibrium; central mass is a lower limit without an inclination correction
- 2021A&A...650A.142M: Distance 6.7 kpc
- 2013Sci...341..630Q: Keplerian rotation; geometry fixed from earlier work
- 2014ApJ...796..117G: Centrifugal support against central mass
- 2017MNRAS.465.2595M: Inclination 37 deg, same as outer belt
- 2018A&A...616A..61R: Disk aligned with orbital plane, viewed 20 deg below edge-on
- 2025MNRAS.541...71M: Keplerian rotation with the continuum-derived disc extent and orientation
- 2018A&A...609A..47P: Circular Keplerian orbits parallel to midplane; inclination 48 deg; no radial or vertical flows
- 2018A&A...609A..47P: Central mass 1 Msun (PV fit), distance 161 pc
- 2025ApJ...989...30Z: Keplerian velocity field used to shift spectra
- 2023ApJ...948L...2Y: Keplerian velocity v_K = 5.438 km/s at r = 60 au; distance = 136 pc; negligible azimuthal offset between Band 9 and Band 7 peaks; Gaia astrometric error ignored
- 2023ApJ...948L...2Y: Gas is co-moving with the dust
- 2017ApJ...834..178Y: Free-fall infall, constant angular momentum, LTE
- 2025A&A...696A.202S: 45 deg average inclination; V-shape gas with no confirmed inflow onto a central mass may overestimate depletion
- 2025A&A...696A.202S: Simple sphere with only infall and Keplerian rotation
- 2023A&A...677A..80W: Circular disk/toroid perpendicular to the jet with jet inclination i = 8 deg; distance = 6.3 kpc; 1.3 mm continuum dominated by dust
- 2013ApJ...765L..14Q: Keplerian rotation; Qi11 disk structure; constant abundance in a layer; power-law column density
- 2015ApJ...814...22E: Constant infall rate, wind mass loss neglected
- 2019ApJ...881...84S: Gas co-located with dust, Keplerian, optically thin; rock/ice ratio ~4
- 2018A&A...616A..34H: M*~1.5 Msun, companion at ~65 AU, micro-turbulence ~0.5 km/s
- 2024MNRAS.527.3559P: Keplerian rotation
- 2016A&A...592A..49T: CN hyperfine components from same region, main component optically thick
- 2025NatAs...9.1486L: Emission from disk at 40-120 au on a z/r = 0.4 surface; same mask parameters for all three isotopologues
- 2025NatAs...9.1486L: Emission assumed to originate from the disk midplane
- 2020ApJ...891...48H: Keplerian rotation; PA, inclination, offsets fixed to continuum values
- 2016ApJ...833..219P: Edge-on, uniform temperature and density ring
- 2026ApJ...999...62H: Keplerian rotation around a central mass M_cen; distance of 400 pc
- 2026ApJ...999...62H: Disk mass much smaller than stellar mass; edge-on geometry; Keplerian rotation; distance = 400 pc
- 2022MNRAS.509..748W: Thin circumstellar disc with circular symmetry in Keplerian rotation and freefall infall; d = 4.0 kpc
- 2015ApJ...798...85P: Keplerian rotation, ISM CO abundance, vertically isothermal, axisymmetric
- 2018A&A...609A..67K: mass 15 ± 5 Msun
- 2024AJ....167..165B: The normalising CO isotopologue flux is a good proxy for total gas content in each disk
- 2021ApJ...911...29C: Keplerian rotation with inclination 5 deg, PA 152 deg, M_* = 0.8 M_sun at 59.5 pc; linear continuum shape
- 2021ApJ...911...29C: Same disk geometry and stellar mass as Keplerian masking (inclination 5 deg, PA 152 deg, M_* = 0.8 M_sun, d = 59.5 pc)
- 2019A&A...622A.206M: Keplerian rotation; velocity scaled by sin(i); disk mass much less than YSO mass
- 2024AJ....167...72D: Central protostellar mass M_* = 0.05 - 0.30 M_sun (or 0.1 M_sun in Figure 13)
- 2024AJ....167...72D: Excitation temperature T_ex ~ 150 K within the jet; CO abundance ratio X_CO ~ 4 x 10^-4; mean molecular weight mu_H2 = 2.8; shock compression factor = 1/3; con…
- 2024AJ....167...72D: Optically thin CO and SiO emission for X_SiO/X_CO (treated as lower limit since tau_SiO > tau_CO)
- 2024AJ....167...72D: Stellar radius R_* ~ 2 R_sun and protostellar mass M_* = 0.1 M_sun for Mdot_acc
- 2020ApJ...894...23H: Disk axially symmetric, Keplerian
- 2013A&A...557A.133D: Astronomical silicates, size slope -3.5, max radius 1 mm; gas-to-dust 100; CO/H2 1e-4; LTE with Tgas=Tdust; Keplerian rotation
- 2017MNRAS.469.4726N: Circular orbits
- 2016A&A...595A.113S: Keplerian rotation
- 2016A&A...595A.113S: Keplerian disk, optically thin temperature profile
- 2024A&A...682A..55M: Keplerian rotation; for Sz 65 an azimuthally symmetric elevated emission surface z(r) = z0 * (r/1'')^ψ * exp(-(r/r_taper)^q_taper)
- 2020NatAs...4..142L: Vertical hydrostatic equilibrium with Keplerian rotation around M_* ~ 1.5 M_sun, and outer geometric thinning between R_t and R_o
- 2020NatAs...4..142L: Mass density rho = 1.4 n m_H2 (helium at solar abundance) and gas-to-dust mass ratio of 100
- 2020NatAs...4..142L: Dust opacity law kappa_nu = 0.1 (nu / 10^12 Hz)^beta cm^2 g^-1 with beta = 0.6 to 1.0, giving kappa_nu ~ 0.054 - 0.035 cm^2 g^-1 at 343 GHz
- 2017ApJ...843...27L: Flared envelope with parabolic boundaries; fit weighted to blueshifted side because of redshifted self-absorption
- 2025SciA...11.4512O: Central mass 10 Msun, inclination 65 deg, mid-plane trajectory inside centrifugal radius
- 2020ApJ...891...61Y: COM emission optically thin
- 2015ApJ...808L...3A: circular Keplerian motion
- 2014ApJ...796....1T: Geometrically thin disk, circular Keplerian bulk motion
- 2018ApJ...869...10M: CO co-located with dust, vertically flat, Keplerian
- 2018A&A...616A.100Y: geometrically thin Keplerian disk; stellar position at continuum center; distances 150/200 pc
- 2024ApJ...961...28H: Keplerian masking
- 2024ApJ...961...28H: Dust and sub-mm gas disks should not be strongly misaligned; adopt the dust-disk inclination
- 2023A&A...674A.113I: Keplerian rotation with vertical differential rotation sustained by balance of forces in the z-direction
- 2023A&A...674A.113I: Highest intensity between upper and lower surface components taken on each pixel and velocity channel
- 2023A&A...674A.113I: Axisymmetric intensity fields for all model channels except 12CO of AS 209
- 2019A&A...629A..29J: Inclination 75-90 deg; optically thin emission for rest velocity
- 2024A&A...686A.235P: Dusty sources gravitationally bound to Sgr A* on Keplerian orbits.
- 2024A&A...686A.235P: Randomly dispersed stars on Keplerian orbits.
- 2020ApJ...897...59M: Inclination 64 deg from circumbinary structure; 30% mass uncertainty
- 2015ApJ...808..102K: Keplerian rotation; Haro 6-13 accretion rate assumed 1.0e-7 Msun/yr
- 2015ApJ...812..129Y: M* = 0.05 Msun, constant j within 10 AU
- 2017ApJ...842....9M: vertically flat Keplerian disk with dust-ring orbital parameters
- 2017MNRAS.468..685Q: Gas-to-dust ratio of 100
- 2017MNRAS.468..685Q: Ideal gas law, infall velocity for spherical envelope, Keplerian rotation for disc, constant velocity parallel to outflow axis plus infall for outflow
- 2025A&A...698A.115R: hyperfine component optically thin (tau <~ 0.02)
- 2025A&A...698A.115R: same Tex as H13CN/HC15N from the Band 7 resolution rotational diagram
- 2021ApJ...911..150P: Combined thermal and turbulent line width follows power law Delta V ~ V_0 (R_0/100)^q
- 2021ApJ...911..150P: Literature distances in parentheses (140 pc for Taurus, 160 pc for Chamaeleon I, 150 pc for Lupus)
- 2019ApJ...879..101L: Constant specific angular momentum and total energy; M* from disk Keplerian rotation
- 2025NatAs...9.1833L: circular geometry, Keplerian rotation V∝r^-0.5
- 2025NatAs...9.1833L: Q<1-2 unstable
- 2020ApJ...898...10T: Binary mass 0.5 Msun, equal masses
- 2015A&A...579A.106V: Stellar masses from literature
- 2014A&A...568L...5C: Distance 450 pc
- 2018ApJ...860L..12T: Keplerian reference: 2.3 Msun, i = 47.7 deg
- 2025ApJ...994...98F: Keplerian velocity, thermal broadening, small temperature gradient across emitting region
- 2023A&A...675A.131T: Keplerian rotation of the disk (d = 157 pc, M_star = 1.69 M_sun, incl = 27 deg, PA = 160 deg)
- 2023A&A...675A.131T: 10% ALMA flux calibration uncertainty
- 2018A&A...620A..31M: turbulent width 0.5 km/s, surface layer scale height 10 au
- 2024A&A...682A..61C: Parcel of gas feels only the gravity of the central source; inner envelope and streamer mass not included
- 2023ApJ...956L..45G: Keplerian rotation of the inner toroid; ambient V_LSR = +10 km/s
- 2015ApJ...804...37L: circular orbit with 100-300 Msun in A1 at 0.0068 pc
- 2019MNRAS.484.1257M: HCN in LTE at 40 K; CO/H2 ratio 1e-4
- 2019ApJ...884L..56T: Keplerian, razor-thin disk; flat priors (M* 0.1-2 Msun)
- 2024MNRAS.534.2904C: Single central massive body, circular Keplerian
- 2024MNRAS.534.2904C: Elevated emission surface for MAPS discs GM Aur, HD 163296, IM Lupi, MWC 480; flat Keplerian otherwise
- 2021ApJ...908..141H: Inclination, position angle, distance, stellar mass fixed (i=35.3 deg, 126 pc, 1.25 Msun)
- 2021ApJ...908..141H: Fit uncertainties taken as 1 sigma; 3 sigma used for upper limits
- 2018ApJ...860..119G: edge-on disk, point-like gravitational potential
- 2024ApJ...966...32E: p ~ 0.5 consistent with Keplerian rotation; p ~ 1 with rotation plus infall conserving angular momentum; ridge and edge fits bracket the Keplerian mass; inclin…
- 2021A&A...653A.166C: Maximum velocity difference along the line of sight occurs at the core center; envelope mass uses standard dust assumptions
- 2014ApJ...795..152O: infall and rotation velocities both 1 km/s
- 2017MNRAS.464.1415M: M*=1.75 Msun, mu=14, vertically isothermal, Keplerian
- 2018ApJ...859..111H: Stellar mass 0.5 Msun
- 2020MNRAS.496.5330F: Stellar mass M_* = 0.8 M_sun and trial inclinations i = 20 deg, 40 deg, and 65 deg for Keplerian curves
- 2017A&A...603A..10B: Keplerian rotation around 10 Msun
- 2025A&A...694A.295P: DIANA-standard setup, gas-to-dust 100, central object B331
- 2021MNRAS.507.1886F: Total stellar mass M_stars = 40 M_sun and inclination angle i = 45 deg for Keplerian comparison
- 2015ApJ...813...99F: CO frozen out below 19 K and photodissociated above column threshold (abundance reduced by 8 orders of magnitude); LTE; mu=2.37
- 2019ApJ...880...69Y: geometrically thin disk
- 2025ApJ...994..214T: Fixed CO/H2 = 1e-4 and 13CO/H2 = 10^-5.3; mean molecular weight 2.37; hydrostatic equilibrium; vertically isothermal disk
- 2025ApJ...994..214T: Pure Keplerian rotation (with pressure effects through the flared model); the CO traces disk gas, not outflows
- 2022ApJ...937...10L: Keplerian rotation around a central mass of ~ 0.25 M_sun
- 2022ApJ...937...10L: Distance of ~ 400 pc
- 2016ApJ...826..213L: jet inclination ~10 deg, edge-on envelope-disk
- 2026MNRAS.551g1411H: Keplerian two-body orbit
- 2021PASJ...73..205T: Tested Keplerian rotation or infall motion (v proportional to r^-1)
- 2013ApJ...764L..14Z: Keplerian rotation, inclination 5 deg
- 2017NatAs...1E.130Z: Emission arises from mid-plane or adjacent regions characterized by one temperature; C18O/13C18O constant
- 2025ApJ...985...84L: flat (midplane) emitting surface for deprojected radial profiles
- 2023ApJ...956..135W: v_sys 2.86 km/s, distance 60.1 pc, inclination 5.8 deg, PA 151 deg, stellar mass 0.81 Msun
- 2017SciA....3E2935L: p=2, q=0.75, passive disk, Keplerian rotation, rho=1.4 n m_H2
- 2024A&A...690A..46S: Keplerian inside break radius
- 2020ApJ...893...51S: h/r=0.03 (r/1au)^0.25, Keplerian, Semenov dust opacity, T*=4000 K
- 2015ApJ...808...69B: edge-on disk, Keplerian rotation, D=414 pc
- 2019ApJ...883...22C: Keplerian rotation, vertically isothermal, hydrostatic equilibrium, distance 131.2 pc
- 2024ApJ...964..190L: Mask radius 3 arcsec; all emission as elevated as 12CO
- 2018A&A...614A..26A: Inclination 80 deg
- 2025A&A...693A..76C: kappa_d=0.01 cm2/g; halo density ∝ 1/r; dust-free optically thick thin disk
- 2020ApJ...897L..33J: Ne follows r^-2 law
- 2015ApJ...805...21C: gas-to-dust 100, CO freeze-out at 20 K, H2/12CO = 1e4, LTE, Keplerian
- 2016ApJ...818..156C: Vertically isothermal, radial power-law temperature, hydrostatic equilibrium, Keplerian rotation, LTE
- 2024AJ....167..164B: Filter shape must represent the emission; different filters give different S/N
- 2020MNRAS.493L.108B: Stellar mass 1.7 Msun
- 2019ApJ...884...42S: Gaia DR2 distances; power-law temperature and column density
- 2026ApJ..1003..219W: Simple free-fall collapse
- 2020A&A...634L..11J: Keplerian kappa=Omega; Draine MW Rv=5.5 dust
- 2014ApJ...785L..12C: [H2]/[CO] = 10^4; mu~2.3; Keplerian rotation
- 2016Natur.535..258C: Pure Keplerian, no infall
- 2024ApJ...965..147B: 13CCH radial profile follows C2H
- 2023MNRAS.518.4481L: Axisymmetric disc with thin emitting layer z_i(R) and fixed geometry from Table 1
- 2018ApJ...854...56L: kappa = 0.1 (nu/1e12 Hz)^beta cm2/g, beta~0.6; Keplerian rotation; vertical hydrostatic equilibrium
- 2025ApJ...992...18P: Gas in the small region is in Keplerian motion; ridge fitting underestimates and edge fitting overestimates the mass
- 2020ApJ...904...78S: Keplerian disk; dust-to-gas 1:100
- 2014ApJ...796..120W: i_A=65 deg; distance 400 pc
- 2017ApJ...835...17M: Constant CO abundance ~1e-4 (ISM-like); vertically isothermal, hydrostatic equilibrium; Keplerian rotation
- 2026ApJ..1003L..30W: Keplerian rotation with the adopted TW Hya geometry for the HC3N mask
- 2026ApJ..1003L..30W: Well-established TW Hya parameters adopted from the literature
- 2021MNRAS.501.4317P: Elliptic Keplerian orbit with eccentricity uniformly distributed between 0 and 0.7, random orientation, and observational size limits set by the ALMA beam (pri…
- 2019A&A...623A..77S: Gas-to-dust 100, dust opacity 1.0 cm2/g at 1.3 mm, dust and gas temperature equal, LTE
- 2026MNRAS.551g1645K: Keplerian disk rotation around a 0.7 M_sun protostar for translating periodicity timescale to disk radius
- 2020ApJ...889...20L: source velocity 8.5 km/s
- 2018ApJ...854..130W: M*=1.7 Msun, d=103 pc, X_CO=1e-4, mu=2.37, inner radius 0.1 AU, Keplerian, vertically isothermal, single plane
- 2025ApJ...984L..18T: Published fluxes are adopted where available for consistency; C18O (3-2) fluxes scaled down by 2.3 to compare with (2-1)
- 2021ApJ...908..250H: Foreground cloud absorption negligible in the central CO region because of high inclination
- 2017ApJ...843...45K: d = 700±100 pc; mass independent of inclination along major axis
- 2024ApJ...961..228S: mu = 2.8; X_CO = 2.0e20; protostellar mass 1 Msun for Keplerian; constant mass loss rate
- 2023MNRAS.519L..68B: N(H2) of a few 10^24 cm^-2; SHC density profile power-law index between 1 and 2; light-to-mass ratio of 10^3 L_sun M_sun^-1
- 2014A&A...562A..26B: Keplerian rotation around 2 Msun star, inclination 50 deg, PA 100.3 deg
- 2017ApJ...851..132C: vertically isothermal; abundance ratios H2/gas=0.8, H/H2=2, 12CO/H=7.5e-5, 12CO/13CO=69, 12CO/C18O=557; LTE
- 2024A&A...687A.311A: Thin disc with Keplerian rotation, initial emission surfaces set to a thin disc
- 2022A&A...662A.121R: Geometrically thin disc in Keplerian rotation with fixed stellar mass and Gaia DR2 distance
- 2026A&A...713A.149V: Simplified virial theorem limited to volume terms (neglecting surface terms); central protostellar mass neglected (Class 0-like envelopes dominate); cylindrica…
- 2020ApJ...888...41A: Keplerian rotation, inclination-corrected
- 2018RAA....18...31P: T=18 K, tau~10 (T,tau)=(36 K,10) at r~1.5 arcsec
- 2024A&A...684A.174P: Constant intrinsic thermal linewidth across the layer; CN layer lower edge at the best-fit CN surface
- 2018ApJ...863...94L: Inclination 6 deg
- 2024ApJ...964...34L: Ejection-to-accretion rate ratio similar to other Class 0 protostars; Lbol of the whole HOPS 373 system attributed to SW
- 2020ApJ...896..127K: edge-on geometry, so mass is a lower limit
- 2018ApJ...859..131L: LTE excitation; solid angle of beam-convolved Keplerian mask
- 2025ApJ...986L...9B: Expected Keplerian rotation; previously stated disk position and inclination angles; range of radial extents.
- 2020MNRAS.491.1335R: distance 103 pc
- 2017ApJ...837..174O: inclination 80 deg, PA 15 deg for disk/envelope
- 2024A&A...692A.181Z: Central mass from bolometric luminosity (~20 Msun); edge-on disk (~80 deg) taken from literature
- 2017ApJ...846L..26W: Flared LTE vertically isothermal Keplerian disk; X_CO=1e-4; mu=2.37; inner radius 0.1 au; distance 140 pc with 20 pc uncertainty added in quadrature
- 2026ApJ..1003...64Y: H2S ortho-to-para ratio 3; LTE; SO2 radius same as SO; M*=2.0 Msun; i=46.7 deg
- 2021A&A...651L...5V: Equal flux contribution for blended p-H2CO 5_{4,2}-4_{4,1} and 5_{4,1}-4_{4,0} transitions
- 2019A&A...626A..71A: Inclination 70 deg from plane of sky
- 2024A&A...686A.146Z: Velocity of surrounding structures from a Kepler rotation curve around the protocluster mass M0
- 2019ApJ...874..136S: X_CO = 1e-4, mu = 2.37, vertically isothermal disk, Keplerian rotation, tapered power-law surface density, LTE
- 2021ApJS..257....6G: Vertically flat disk geometry
- 2019NatAs...3..517Z: Keplerian rotation; only half of ring emits
- 2024ApJ...967...15K: Distance 2.38 kpc; also tested 1.7 kpc
- 2023PASJ...75..225M: Star mass 20±7 Msun
- 2018ApJ...869L..50P: Stellar mass 1.8 Msun; distance 165 pc
- 2024Sci...383..988B: Viscous accretion disk with Keplerian rotation; listed disk parameters except mass; constant HCN abundance 10−8 relative to H.
- 2020ApJ...904..125S: Keplerian rotation; second index 0.45 following Andrews 2011; linear / weakly non-linear regime
- 2019ApJ...881..112O: Keplerian rotation, no radiative transfer; M = 0.82 Msun / sin^2 i
- 2020ApJ...889...43Z: Td=50 K, gas-to-dust ratio 100
- 2017ApJ...844..158S: Distances 131 pc (L1495), 119 pc (L1688), 140 pc Taurus average
- 2024A&A...692A.155K: Upper and lower emission surfaces cannot be distinguished, so a flat disk is assumed
- 2020ApJ...901...71S: Keplerian rotation with inputs from published disk models
- 2018A&A...612A..72J: Gas and dust temperatures coupled; Keplerian rotation (PP-disk), Terebey et al. velocities (toroid), free-fall elsewhere; LIME model radius 2000 AU
- 2024ApJ...966..117X: fixed 60 Msun initial core
- 2018A&A...619A.171B: 1.5 Msun star, distance 166 pc, razor-thin disk
- 2024ApJ...974...83Y: Gas temperature = dust temperature; constant abundance in regions above sublimation temperature
- 2020ApJ...900....7H: 12CO/H2 = 1e-4; canonical isotopologue ratios; vertically isothermal; q=0.5, gamma=1.0, i=56.16 deg fixed
- 2019ApJ...872...64K: Thin edge-on ring, uniform temperature and density, optically thin emission
- 2026AJ....172..108L: Typical jet/wind velocity V_w ~ 150 km s^-1; ratio of wind mass-loss rate to mass accretion rate M_dot_w / M_dot_acc ~ 0.1; entrainment efficiency f_ent = 0.25
- 2018ApJ...852..122H: LTE; thin Keplerian disk; inclination 5 deg, PA 152 deg; mu=2.37; CO freezeout step function p=1e-6 below Tfrz
- 2024ApJ...974..102S: gas temperature 20 K, c_s ~0.3 km/s
- 2022A&A...659A..29B: distance = 136 pc
- 2016ApJ...830L..16B: VLA 2 disk position angle adopted along the velocity gradient, assumed to be the CO disk of Herczeg et al. (2011)
- 2024A&A...690A.185W: Region rest velocity is a proxy for core velocity
- 2019ApJ...876...72L: Flat disk; mask padded to include flaring layers
- 2025ApJ...989...41A: Stellar mass, inclination and PA from the literature table; axisymmetric disk; only the upper layer; intrinsic line width ignored
- 2020ApJ...904L...6A: Infall from rest with no energy dissipation; protostellar mass M_star
- 2017ApJ...837...86T: binary mass 0.8 Msun, i=62 deg, Source A 0.675 Msun
- 2026MNRAS.551g1639M: L_bol = L_acc, M_A1 / M_A2 = 1, protostellar mass in simulation M_p is the sum of disk mass M_d,p and protostellar mass M_*,p
- 2018ApJ...857...69B: Blended line emission symmetric around source rest velocity
- 2024A&A...686A.120U: NE side is the near side of the disk
- 2024A&A...686A.120U: Flat circular disk in Keplerian rotation
- 2020ApJ...895..109F: T_mid0 fixed from literature (DM Tau 19 K freeze-out at 70 au; MWC 480 18.8 K; V4046 Sgr 12 K); distances from Gaia DR2
- 2019ApJ...884..146T: Keplerian velocity for 1 Msun central mass
- 2024MNRAS.532L..36R: Central object mass of 18 MJup
- 2019A&A...624A...7V: M*=1.4 Msun, i=74 deg
- 2024A&A...687A.188K: Purely Keplerian velocity field; Gaussian local line broadening
- 2024A&A...687A.188K: Optically thick front layer over the whole channel velocity width
- 2020ApJ...894...74B: flat axisymmetric disk, distance 400 pc
- 2017A&A...602A..59C: Keplerian pattern edge-on, zero line width, infinite resolution, not a fit
- 2024ApJ...963...72O: Knot plateau velocity equals Keplerian velocity at launch radius
- 2018ApJ...862L...2F: Keplerian rotation
- 2025ApJ...984L..10G: SNR per point is intensity divided by cube RMS; Keplerian rotation assumed by disksurf
- 2021A&A...646A..59R: Geometrically thin Keplerian disk; distance 120 pc
- 2019ApJ...880..130M: Outflow direction is rotation axis of potential disk
- 2018NatAs...2..646H: CO abundance 1e-4, 16O/18O = 560
- 2026A&A...705A..96M: κ3mm~1 cm² g⁻¹; gas-to-dust ratio=100
- 2026A&A...705A..96M: Literature protostellar masses; M*=1 M☉ when absent; equal component masses for binaries with only combined mass
- 2023NatAs...7..684K: V_LSRK = 5.7 km s-1; M_* = 2.4 M_sun for Keplerian mask
- 2019ApJ...877L..25M: 50% of accreting mass goes to outflow
- 2018ApJ...865..155C: distance 161 pc, inclination 48 deg, Keplerian around 1 Msun
- 2026MNRAS.552g1700S: Keplerian rotation with differential rotation as a function of height z(r); exponentially tapered power-law surfaces for front and back sides
- 2023MNRAS.522.2384M: Keplerian rotation, disk inclination of 80 deg, systemic velocity V_sys(W) = +1.6 km/s, distance d = 131 pc
- 2018ApJ...864L..23V: Optically thin, LTE
- 2026ApJ..1005..199C: Keplerian rotation
- 2022MNRAS.513.5790C: Stellar mass = 0.9 M_sun, distance = 113.4 pc; flat surface density out to 1 au radius for CPD optical depth estimate
- 2016ApJ...832..204Y: Geometrically thin disk, Keplerian rotation
- 2025ApJ...986L..11S: Distance ~140 pc
- 2021ApJ...910...75L: Maximum grain size of 100 um to bound the Rosseland mean opacity (kappa_R < 200 cm^2/g) read from a literature figure
- 2018ApJ...864...76Z: CS traces envelope outside barrier; SO enhanced at barrier
- 2016ApJ...830...32W: Hydrostatic equilibrium, Keplerian rotation, azimuthal symmetry
- 2020A&A...635A..12P: Infall neglected in outer disk; i=35 deg
- 2017NatAs...1E.146H: Keplerian rotation; distance 418 pc
- 2019AJ....157..237R: viscosity and scale height fixed; only planet mass varied
- 2024ApJ...976..132H: Geometrically thin disk (flared surface for SO 897); posterior approximated as multivariate normal
- 2016ApJ...830L..37I: HNCO co-spatial with COMs at 100 K average temperature
- 2024NatAs...8..587F: Stellar mass fixed to 1 Msun in the equation, i=46.7 deg, d=140 pc
- 2016Natur.540..406B: Kinetic temperature 100 K; isotopic ratios 60 (13CO) and 550 (C18O); i=55±10°
- 2026ApJ..1002..176C: v=2-1 profile dominated by Keplerian rotation so only v=1-0 absorption used for column density
- 2020MNRAS.492..572A: Mie scattering, astronomical silicates, Teff = 4000 K, Rin = 0.1 au, amin = 0.01 um; factor 40 from median Kp ~ 13 mag and Kepler faint limit Kp ~ 17 mag
- 2019ApJ...882..160Q: Keplerian rotation
- 2025ApJ...984L..13H: DISCMINER assumes Keplerian rotation; uncertainty is purely statistical
- 2023ApJ...948..110Y: 13CO is optically thick and its brightness temperature equals the gas temperature and C18O excitation temperature; C18O/H2 ratio = 1.79e-7; Gaussian optical de…
- 2017NatAs...1E.172L: Edge-on for minimum mass; inclinations from continuum
- 2026A&A...708L...1Z: Purely Keplerian rotation (including vertical height of optically thick 12CO layer); gas disk mass = 10^-2 M_star; dust disk mass = 10^-4 M_star
- 2016MNRAS.463.3563T: Constant temperature 30 K, C18O/H2 = 4.9e-8
- 2017AJ....153..233F: Optically thin HCO+ emission
- 2024ApJ...973..135H: Literature M_star, i and PA are uncertain because of low inclination and compact disk
- 2021A&A...649A..19S: Empirical profiles with no assumption on disk kinematics (no Keplerian masking)
- 2018ApJ...859..150R: PA 41 deg and inclination 55 deg for A
- 2024A&A...688A.149D: simple disk model
- 2021ApJ...908...46B: Different molecules follow same Keplerian rotation; scale-height effect small (<3%)
- 2018ApJ...861...91H: kappa = 10 (nu/1 THz)^beta cm2/g, beta=1, gas-to-dust 100, Td = 30 K, central mass 0.15 Msun
- 2017ApJ...840...60B: distance 156 pc
- 2024A&A...687A.299L: Keplerian mask with inclination 42, PA 140, distance 110 pc, stellar mass 2.13 Msun, systemic velocity 5.7 km/s
- 2017A&A...607A.130D: Keplerian rotation
- 2024ApJ...971L..15Y: Circumplanetary-disk launching radius R_l~6 R_Jup
- 2019ApJ...879L..25I: Star at disk center
- 2026A&A...710A.140M: Keplerian rotation; distances of 130 pc (Taurus), 140 pc (Ophiuchus, Upper-Scorpius), 160 pc (Lupus), 190 pc (Chamaeleon) from Zucker et al. (2020); inclinatio…
- 2017MNRAS.467L.120M: Keplerian rotation, inclination ~50 deg
- 2025ApJ...984L..19Y: Line wings identical along azimuth
- 2019AJ....157..165A: Flat disk geometry, circular orbits
- 2024ApJ...970..153A: Bias from beam smearing only; mock with Keplerian field, power-law Tb
- 2019ApJ...871..221M: M* = 0.1 Msun
- 2017A&A...607A..55V: Keplerian rotation, inclination 59.3 deg, 1.59 Msun star
- 2024RAA....24g5017M: Inclination 46.7, PA 133.3, M*=2 Msun, d=101 pc
- 2018RAA....18...93Z: inclination unknown
- 2018ApJ...860L..13P: Gas only, dust ignored; vertically isothermal
- 2020ApJ...889..140Y: dust opacity 2.3 cm2/g at 1.3 mm, dust T 20 K, gas-to-dust 100:1
- 2018ApJ...858..112L: Inclination 45 deg
- 2024AJ....167...66Y: emission from the midplane, no vertical extent
- 2018A&A...616A..45S: LTE, optically thin emission
- 2024AJ....167...77D: near Keplerian rotation
- 2018A&A...620L...1G: Inclination 38 deg
- 2025ApJ...993...90S: X_CO=1e-4, T_ex=50 K; alternative CO-to-H2 factor 2.0e20
- 2016MNRAS.462L.101A: circular disk structure, Keplerian rotation for moment-map check
- 2019ApJ...877..100Y: dust opacity 3 cm2 g-1, gas-to-dust ratio 100
- 2024ApJ...966..119L: Distance 388 pc, M*=1.2 Msun, inclination 38.3 deg, PA ~120 deg
- 2026ApJ..1009L...3B: Circular orbit coplanar with the disk (inclination = 23.6 deg, PA = 43.4 deg) and stellar mass = 0.78 +0.35/-0.13 M_sun; interstellar extinction A_V = 8.7 mag.
- 2019A&A...623A.124C: Keplerian rotation, M=2.3 Msun, inclination 44 deg, PA 133 deg
- 2025ApJ...991..176W: Distance 160 pc; true uncertainties ~10% due to systematics
- 2024A&A...686A...9M: Optically thin dust continuum emission at 283 GHz with T = 20 K; nearly Keplerian disk (kappa approx Omega) for Toomre Q; for AS 209, upper limit on M_d taken …
- 2025ApJ...984L..15P: Keplerian rotation
- 2025A&A...703A.282R: M_star = 2.1 M_sun, i = 46.7 deg, PA = 138 deg
- 2019ApJ...871....5T: Keplerian rotation, inclination 49 deg
- 2018A&A...618A.120L: Steady wind, M_star=0.45 Msun, gas flows along conical surface
- 2017ApJ...840...23L: stellar mass 0.85 Msun
- 2018ApJ...869L..49I: i=46.7 deg, stellar mass 2.0 Msun, Keplerian rotation
- 2018ApJ...869L..42H: Keplerian rotation, small disk mass; q = 0.5 for snowline ratios


### Limitations the authors admit
- 2019Natur.574..378T: v_Z is only relative because v_LSR is uncertain; systematics are 2-3 times the statistical errors
- 2024ApJ...976..258K: X-ray chemistry not included
- 2024ApJ...976..258K: Outer disk not modelled because of its complex structure
- 2024ApJ...976..258K: Gaussian ring parameters in DISKFIT are strongly coupled so their errors are unreliable
- 2021A&A...650A..59B: Vortex and beam-smearing-plus-pressure-gradient scenarios currently very difficult to differentiate
- 2021A&A...650A..59B: Vortex velocity profile not measurable from the data (Gaussian assumed)
- 2021A&A...650A..59B: Gas scale height could not be constrained, thin disk used
- 2021A&A...650A..59B: Line emission in the north partly lost to continuum subtraction and dust absorption
- 2018ApJ...865..131L: The accretion rate depends on uncertain parameters (entrainment efficiency, mass-loss ratio, wind velocity) and on the assumption of a constant rate.
- 2018ApJ...865..131L: A stellar mass cannot be ruled out.
- 2025SciA...11.6953M: Accretion rate is a lower limit (optically thin 12CO assumed, missing short spacings) and not corrected for outflow inclination
- 2025SciA...11.6953M: Idealised particle-trajectory model fails to capture the whole system's dynamics
- 2025SciA...11.6953M: IRE model is insensitive to the central mass
- 2025SciA...11.6953M: Theory for a counter-rotating massive disk is unclear
- 2020ApJ...904..181L: Cooler outer temperatures and missing flux beyond 2 arcsec can increase inferred outer masses and flatten the density profile.
- 2020ApJ...904..181L: Several spectral components are blended, uncertain or unidentified.
- 2020ApJ...904..181L: Inclination is not well constrained observationally.
- 2020ApJ...904..181L: M4 specific angular momentum and centrifugal barrier are unknown; 90 au was chosen arbitrarily.
- 2020ApJ...904..181L: Resolution prevents identification of central substructure, small clumps and a putative inner disc.
- 2020ApJ...904..181L: Mass estimates depend on uncertain temperature, dust opacity and variable flux; gas and dust may be thermally decoupled during the burst.
- 2020ApJ...904..181L: The simulated pseudo-disc is smaller than the observed structure; the simulation omits magnetic fields.
- 2020ApJ...904..181L: Temporal variation and chemical differentiation require higher-sensitivity confirmation.
- 2012ApJ...757..129R: Model parameters are not unique nor optimized; limited resolution
- 2014ApJ...793....1Y: Missing flux (~80% of C18O) hinders outer disk radius; p, q, T0, vturb poorly constrained
- 2016ApJ...829....6W: CO mass assumes optically thin LTE and could be larger by a factor of a few or more
- 2016ApJ...829....6W: Debris mass depends strongly on assumed size distribution, density, albedo
- 2016A&A...596A..92K: Mass of B has no firm lower limit; assumes a single companion
- 2016A&A...596A..92K: Extended slow envelope is resolved out by long baselines
- 2026A&A...705A.201B: Keplerian fit uncertainties likely underestimated
- 2026A&A...705A.201B: Mu and 13CO mass depend on the LTE assumption and radial and vertical model choices
- 2026A&A...705A.201B: Different total CO masses or abundance ratios may fit equally well given high optical depth
- 2026A&A...705A.201B: Azimuthal averaging smooths azimuthal variation in line profile
- 2020MNRAS.498.1319M: Planet mass assumes the gap is empty at its centre; a shallower, broader gap would change the inferred width and mass
- 2020MNRAS.498.1319M: Frankenstein profiles lack a primary beam correction
- 2020MNRAS.498.1319M: Lower S/N makes gap width and depth comparison with other discs difficult
- 2020MNRAS.498.1319M: Derived planet masses must be taken with caution since the gap may be inherited or the planet may have migrated
- 2017ApJ...850L...5T: Orbital parameters cannot be uniquely determined from the PV diagram
- 2024A&A...692A.151S: Model is probably not unique; more complex geometries and profiles cannot be dismissed
- 2024A&A...692A.151S: Model fails to reproduce the H30alpha profile asymmetry
- 2024A&A...692A.151S: Continuum SED decomposition is only a rough estimate
- 2024A&A...692A.151S: Distance to M 2-9 is highly uncertain
- 2013ApJ...776...77K: Inner radius only an upper limit; brightness exponent ill-determined; full radiative transfer model postponed
- 2022MNRAS.510.2363H: In the first set of observations (Band 7), sparse and uneven baselines < 500 m limit reliable imaging to R < ~0.2 arcsec and cause an isotropic wind to artificially appear as north-south emission bey…
- 2022MNRAS.510.2363H: The parameterization of the emission in phase opposition to the dominant sine wave in terms of two weaker sine waves with eye-estimated parameters is somewhat arbitrary.
- 2022MNRAS.510.2363H: The inclination angle i of the large-scale expanding wind disc is unknown, making the retained range of 40+-20 deg and the resulting mass loss rate estimate crude and dependent on somewhat arbitrary …
- 2022MNRAS.510.2363H: Below ~1 arcsec from the star, insufficient uv coverage in the first dataset, insufficient angular resolution in the second dataset, and complex dynamics prevent definitively ruling out north/south o…
- 2024ApJ...970...74P: Stellar Keplerian solutions lack individual radial velocities
- 2024ApJ...970...74P: Some stellar orbits have less than 2% coverage
- 2024ApJ...970...74P: Multiple orbital solutions are acceptable; quoted uncertainty ranges describe local solutions
- 2024ApJ...970...74P: Gas–star radial-velocity link used for the cluster distance may be premature
- 2024ApJ...970...74P: Simplified migration simulations omit stellar winds and ambient medium and use equal particle masses
- 2024ApJ...970...74P: IMBH confirmation requires more detailed multiwavelength timing, spectroscopy, and rotating-gas studies
- 2024ApJ...970...74P: Current X-ray sensitivity cannot access the expected IMBH variability timescale
- 2013PASJ...65..100I: Dynamical mass is simple Keplerian estimate and lower limit
- 2013PASJ...65..100I: Submm-HCN diagram is tentative, few samples
- 2021AJ....162...14A: absolute flux scale 10-15% uncertain because no primary flux standard observed
- 2021AJ....162...14A: one October 2018 observation had a 20 mas offset attributed to a tracking error and was dropped
- 2021AJ....162...14A: trigonometric parallax is poorly constrained by the few absolute points
- 2021AJ....162...14A: jitter estimate is only an order of magnitude
- 2021AJ....162...14A: alpha Cen A RVs could not be recomputed with the correct mask because the ESO pipeline is not public
- 2020ApJ...902...99I: Emission larger than the maximum recoverable scale may be resolved out
- 2020ApJ...902...99I: Extended host-galaxy emission is not recovered in the Cycle 6 data, so only compact torus emission is discussed
- 2020ApJ...902...99I: Continuum peak flux uncertainties exclude absolute flux calibration and continuum frequency-range choice
- 2020ApJ...902...99I: C-peak spectra can be contaminated by innermost torus emission because the beam is not much smaller than the separation
- 2020ApJ...902...99I: HCO+-VIB emission candidate is below 3 sigma and may be HOC+
- 2023ApJ...953L...6P: Self-calibration removes absolute position information, causing Band 6 and Band 7 images to lose absolute astrometry and exhibit a slight positional offset.
- 2023ApJ...953L...6P: The ALMA synthesized beam is elongated in the north-south direction and could not resolve the north-south double peaks ('dark lane') seen in centimeter VLA observations.
- 2023ApJ...953L...6P: 2D Gaussian centroid fitting underestimates the true size of the maser disk because the maser emission is spatially extended, leading to a lower enclosed stellar mass estimate than 3D radiative trans…
- 2017MNRAS.468.1769F: Cloud blending in central region makes nuclear mass distribution suspect
- 2022MNRAS.515..543C: Collisional coefficients for CH3OH are lacking for transitions with J >= 16.
- 2022MNRAS.515..543C: LVG analysis is challenged by the limited number of lines with collisional rates (5 lines, with 4 in the narrow E_u = 45-61 K range).
- 2022MNRAS.515..543C: For source A, the E_u range of the 4 detected CH3OH lines (45-61 K) is too narrow for a free rotational diagram fit, only allowing an upper limit on T_rot.
- 2022MNRAS.515..543C: The ~0.4'' (50 au) angular resolution cannot disentangle the binary components A1 and A2 in the continuum and hampers detailed kinematic modeling of the spatially unresolved iCOM emission.
- 2022MNRAS.515..543C: Sub-mm dust opacity may hide iCOM emission around A2 and in the optically thick disk midplane of B.
- 2025A&A...704A...7P: Limited IFU field of view covers only about 33% of X7's elongated structure, introducing a systematic offset of the fitted tip position toward Sgr A*.
- 2025A&A...704A...7P: Low orbital coverage (5-15% for G2/DSO and D9) limits improvement in absolute orbital uncertainties and creates a ~0.6 sigma difference relative to observable-biased priors.
- 2025A&A...704A...7P: OH sky line emission (e.g., at 2.158 um) and high stellar crowding in the S cluster impact extracted spectra and Gaussian fit uncertainties.
- 2025A&A...704A...7P: The putative inverse P Cygni absorption feature in X3 at 2.1667 um is weak and close to noisy rest-wavelength Br-gamma, so an artificial origin cannot be excluded.
- 2025A&A...704A...7P: For X3, no 12.5 mas plate-scale ERIS observations were available, restricting the analysis to the 100 mas setting.
- 2020PASJ...72L...5T: The IRS 13E3 distance bound for the Northern arm test is an assumption, not a measurement
- 2025ApJ...988L..44F: EG temperature not constrained and a more complex temperature structure is possible
- 2025ApJ...988L..44F: Significant line blending at 0.42 km/s resolution; detections tentative
- 2025ApJ...988L..44F: CH3OH column density not reliably measured; canonical 12C/13C may overestimate it
- 2025ApJ...988L..44F: Further higher spectral resolution observations needed to confirm
- 2015A&A...574A...5D: Short observation and sparse uv coverage hamper interpretation
- 2018ApJ...868..113T: Resolution (~29 au) leaves velocity features unresolved, underestimating depth
- 2018ApJ...868..113T: Cannot disentangle pressure gradient from stellar mass; pressure scaling depends on assumed density
- 2024ApJ...967...68H: Vertical height is a lower limit because optically thin emission blurs near and far surfaces
- 2024ApJ...967...68H: OPR uncertainties are purely statistical and ignore modelling assumptions
- 2024ApJ...967...68H: Inner-disk column density drop is unresolved and fit quality is poorer there
- 2024ApJ...967...68H: Tentative OPR variations may reflect deviations from LTE, shared T_ex, or common emitting region assumptions
- 2021AJ....162...99F: Literature C/O models are tuned for disks without large cavities; a PDS 70-specific forward model is needed
- 2021AJ....162...99F: Fractionation conclusions depend on assumed uniform carbon fractionation
- 2021AJ....162...99F: Long-baseline (0.1'') data not yet taken; resolution only ~50 au
- 2019ApJ...873...73Z: Model is simple and illustrative; geometry, abundance and excitation simplified
- 2019ApJ...873...73Z: Resolution too low to get detailed disk rotation profile
- 2025ApJ...985..166K: UCM trajectories are degenerate, so 3D lengths and infall rates are uncertain by up to a factor of four
- 2025ApJ...985..166K: More, unidentified streamers may exist
- 2025ApJ...985..166K: Axisymmetric envelope model does not fully explain the intensity distribution
- 2025ApJ...985..166K: JCMT resolution could smooth out 1000 au cloudlets
- 2025ApJ...985..166K: 12-m-only data may contain artifacts at low velocities
- 2020ApJ...904..185O: Extended structures such as the bridge between Source A and Source B and emission near the systemic velocity suffer from resolving-out effects.
- 2020ApJ...904..185O: C17O (J=2-1) suffers from cold foreground self-absorption near the systemic velocity and line contamination from (CH3)2CO, CH2DOH, and/or an unidentified line at high velocity shifts.
- 2020ApJ...904..185O: Simple 3D Keplerian and infalling-rotating envelope models assume optically thin emission without radiative transfer and cannot fully reproduce the complex kinematic substructures, resulting in large…
- 2020ApJ...904..185O: Dust continuum emission contribution is ignored in H2CS optical depth and temperature calculations, and temperatures become artificially high with large uncertainties where the line ratio approaches …
- 2013ApJ...774...16R: Models are degenerate, not unique or optimal; systematic residuals at large radii
- 2013ApJ...774...16R: Band 7 sky frequency in SV measurement set incorrect
- 2014ApJ...786..114L: Disk is not well resolved, so its radius is an upper limit and the temperature index is rough; model is simple and symmetric and excludes outflow, jet and extended envelope.
- 2017ApJ...842....8M: Resolution (~10 AU) prevents constraints on edge sharpness; Δa and e_p degenerate; large uncertainty on ω from inclination degeneracy
- 2017ApJ...842....8M: 2D model ignores vertical structure, which could loosen width constraints
- 2019A&A...629A.136S: Distance very uncertain; central mass uncertain by up to 25%; slow wind not firmly established; model axisymmetric and cannot reproduce blue-peak asymmetry.
- 2026A&A...705A.202M: Kinematic fit uncertainties likely underestimated (pixel correlation ignored)
- 2026A&A...705A.202M: Dust mass uncertainty excludes opacity uncertainty
- 2026A&A...705A.202M: Beam smearing biases the extracted azimuthal velocity profile, so deviations are probably underestimated
- 2026A&A...705A.202M: Optically thick CO cannot rule out a hidden gas-density asymmetry
- 2021MNRAS.506.1978L: The modified blackbody parameters (lambda_0 and beta_0) for the inner warm component are poorly constrained because the sub-mm slope relies only on low-S/N Band 6 and Band 7 inner excesses.
- 2021MNRAS.506.1978L: Lower sensitivity in the Band 6 image prevents an independent detection of the ~20% SW/NE flux asymmetry seen in Band 7.
- 2021MNRAS.506.1978L: The HST coronagraph occults emission within ~2.25'', limiting the ability to quantify the significance of the minor-axis scattered light asymmetry.
- 2021MNRAS.506.1978L: Visibility-space BIC penalises additional model parameters disproportionately because a large fraction of the 19.4 million visibility points are dominated by noise and unaffected by the disc asymmetr…
- 2021MNRAS.506.1978L: The parametric models assume a simple 2D Gaussian clump or a radially constant eccentricity and pericentre orientation, which may be too simplistic for a broad belt with a radially decaying forced ec…

### Settings cards flag as needed but not stated
- self-calibration solution intervals: 24
- casa version: 23
- self-calibration solution intervals and number of iterations: 18
- line-free channels and continuum subtraction method: 16
- image size and cell size: 13
- line-free channels used for continuum: 12
- line-free channel ranges for continuum: 11
- continuum subtraction method and line-free channels: 10
- line-free channels for continuum subtraction: 9
- line-free channels used for continuum subtraction: 9
- self-calibration solution intervals and number of rounds: 9
- casa version and pipeline version: 8
- continuum subtraction and line-free channels: 8
- line-free channels for uvcontsub: 8
- flux scale uncertainty: 7
- self-calibration solution intervals and reference antenna: 7
- casa version and whether the pipeline or manual calibration was used: 6
- line-free channels used for uvcontsub: 6
- line-free channel ranges: 5
- primary beam correction details: 5
- source coordinates: 5
- self-calibration, if any: 4
- continuum-subtraction line-free channels: 4
- line-free channel selection for continuum: 4
- moment map clipping thresholds: 4
- continuum-subtraction and line-free channels: 4
- flux calibrator and flux-scale uncertainty: 4
- self-calibration solution interval: 4
- image size and cell size for tclean: 4
- casa version and whether pipeline or manual calibration: 4
- line-free channels and continuum subtraction details: 4
- casa version used: 3
- line-free channels and continuum subtraction method for line cubes: 3
- self-calibration solution intervals and reference: 3
- line-free channel ranges for continuum subtraction: 3
- clean threshold, masks, image size and cell size: 3
- self-calibration solution interval and reference antenna: 3
- casa version used for calibration and imaging: 3
- casa version and calibration procedure: 3
- rest frequencies of lines: 3

## Paper excerpts (40 of 447, chosen for detail and spread over fields/years)

### 2019Natur.574..378T: Meridional flows in the disk around a young star (2019; protoplanetary_disks; archival_reuse)
- question: What are the three-dimensional gas velocity components (v_phi, v_R, v_Z) in the upper layers of the HD 163296 disk, and do they show meridional flows at the gap locations?
- step 2: Fit the parametric emission surface
  - method: Fit the Keplerian map with a two-power-law emission surface and 10 free parameters [Deriving an Emission Surface: "leaving 10 free parameters for the model."]
  - software: eddy
  - parameter: Only pixels at least a beam FWHM apart are used in the likelihood [Deriving an Emission Surface: "Only spatially independent pixels, those at least a beam FWHM apart, were considered in the calculation of the likelihood."]
  - assumption: Distance 101 pc; inclination prior 46.7 +/- 0.1 deg [Deriving an Emission Surface: "Flat priors were assumed for all values except the inclination which has a prior of $i = 46.7\ensuremath{^\circ} \pm 0.1\ensuremath{^\circ}$"]
  - fitting: MCMC with 64 walkers, 10,000 burn-in steps and 10,000 sampling steps, flat priors [Deriving an Emission Surface: "64 walkers were run for 10,000 steps for an initial burn-in period, before an additional 10,000 steps were used to sample the posterior distributions."]
  - validation: Compared with a non-parametric surface and with a fit that fixes Z1 = 0 [Deriving an Emission Surface: "Fixing $Z_1 = 0$ results in a comparable geometric parameters"]
- step 4: Measure v_phi and v_R in annuli
  - method: Annuli 25 mas wide; random independent pixels; maximise the Gaussian Process likelihood of the shifted and stacked spectra; 20 realisations per annulus [Measuring the Velocity Structure: "For each annulus, 20 different realisations with different pixels were performed and the posterior distributions combined."]
  - software: eddy
  - parameter: Annulus width 25 mas [Measuring the Velocity Structure: "each 25 mas wide (roughly 1/4 of the beam FWHM)"]
  - fitting: Maximum likelihood with a Gaussian Process on the stacked spectra [Measuring the Velocity Structure: "maximised the likelihood when a Gaussian Process was fit to the shifted and stacked data"]
  - validation: Repeated with v_R fixed to 0, giving no change in v_phi [Measuring the Velocity Structure: "we repeat the procedure fixing $v_{R, {\rm proj}} = 0$ and find no change in the inferred $v_{\phi,\, {\rm proj}}$"]
- step 5: Measure v_Z from the line centre
  - method: Resample the stacked spectra to 40 m/s and fit a Gaussian, first to the whole spectrum and then to the line core; the line centre is v_LSR plus v_Z,proj [Measuring the Velocity Structure: "The measured line center is then considered the sum of the systemic velocity, $v_{\rm LSR}$ and the projected vertical velocity"]
  - software: eddy
  - parameter: Resampled to 40 m/s, a factor of 16 higher than the original data [Measuring the Velocity Structure: "we resample the stacked spectra to ${40}~{\rm m\,s^{-1}}$, a factor of 16 higher than the original data"]
  - assumption: Deprojection with i = 46.7 deg [Measuring the Velocity Structure: "the projected velocity components were corrected for their projection using a disk inclination of $46.7\ensuremath{^\circ}$"]
  - validation: Differences between the two emission surfaces used for systematics [Measuring the Velocity Structure: "We also use the differences between the two methods to estimate the systematic uncertainties on the derived velocities."]
- result: Stellar mass = 2.022 ± +/-0.004 Msun [Deriving an Emission Surface: "$M_{\rm star} = 2.022_{-0.004}^{+0.004}~M_{\rm sun}$"]
- result: v_LSR = 5.763 ± +/-0.001 km/s [Deriving an Emission Surface: "$v_{\rm LSR} = 5.763_{-0.001}^{+0.001}~{\rm km\,s^{-1}}$"]
- result: Inclination (fit) = 46.8 ± +/-0.1 deg [Deriving an Emission Surface: "$i = 46.8_{-0.1}^{+0.1}$"]
- result: Emission surface Z0, phi = Z0 = 265 mas, phi = 1.29 ± Z0 +/-3 mas; phi +0.04/-0.03 mas; dimensionless [Deriving an Emission Surface: "$Z_0 = 265_{-3}^{+3}~{\rm mas}$, $\varphi = 1.29_{-0.03}^{+0.04}$"]
- result: Statistical uncertainty on v_phi and v_R = ~10 ± not stated m/s [abstract: "The resulting statistical uncertainties on $v_{\phi}$ and $v_{R}$ are $\sim$ ${10}~{\rm m\,s^{-1}}$"]
- result: Outer radial outflow speed = ~30 ± not stated m/s [abstract: "the measured $v_{\rm flow} \sim 30~{\rm m\,s^{-1}}$"]
- limitation (authors): v_Z is only relative because v_LSR is uncertain; systematics are 2-3 times the statistical errors [Measuring the Velocity Structure: "the inferred $v_{Z}$ radial profiles are therefore only relative values"]
- not stated (card): Exact DSHARP image product (file name, robust weighting) of the 12CO cube; Choice of Delta V for the line-core fit; Radial range and number of annuli used, and the polynomial fitting range; Emission-surface parameters for gas-temperature and sound-speed conversion beyond the description; FARGO3D setup details such as boundary conditions and the smoothing of the planet potential

### 2024ApJ...976..258K: Chemistry in the GG Tau A Disk: Constraints from H<SUB>2</SUB>D<SUP>+</SUP>, N<SUB>2</SUB>H<SUP>+</SUP>, and DCO<SUP>+</SUP> High Angular Resolution ALMA Obser… (2024; protoplanetary_disks, astrochemistry; observational_alma_primary)
- question: Cold molecular chemistry in the GG Tau A triple T Tauri disk: map N2H+, DCO+ and H2D+ (plus 13CS, SO2 limits), derive surface densities and rotation temperatures, and compare with chemical models across cosmic ray ionization rate, C/O rati…
- step 1: calibrate, self-calibrate and image the line cubes and continuum
  - method: CASA pipeline calibration; five rounds of continuum self-phase calibration per execution; recentre with fixvis on an ellipse-fitted disk centre; concat of executions; first-order uvcontsub; tclean with Keplerian masks [2.1 Data Reduction: "five rounds of continuum self-phase calibration were performed for each execution, selecting line-free channels carefully"] [2.1 Data Reduction: "we fitted the continuum structure with an ellipse, and both executions were recentered to the disk center using the `fixvis` task in CASA"]
  - software: CASA, keplerian_mask
  - parameter: tclean hogbom, briggs robust = 1.0 for N2H+ and DCO+; multiscale scales [0,5,15,25] pixels with natural weighting for weak lines [2.1 Data Reduction: "using `hogbom` deconvolving algorithm with `briggs` weighting (robust=1.0)"] [2.1 Data Reduction: "We adopted the `natural` weighting scheme to enhance the signal-to-noise ratio for the weak lines."]
  - assumption: Keplerian mask geometry M* = 1.37 Msun, i = 37 deg, PA = 278 deg rescaled to 150 pc [2.1 Data Reduction: "with the geometric parameters $M_{*}$ = $1.37 M_{\odot}$, i = 37$^{\circ}$, and PA = 278$^{\circ}$"]
  - validation: Disk-centre offset between the two executions checked [2.1 Data Reduction: "The offset between the disk centers in the two executions was only"]
- step 2: make integrated-intensity maps and radial intensity profiles
  - method: Moment-0 maps with bettermoments using the Keplerian masks and no intensity threshold; azimuthally averaged radial profiles with GoFish in annuli of 1/4 beam major axis [2.2 Observational Results: "The integrated intensity maps were generated by collapsing the image cubes along the velocity axis while applying the Keplerian masks used for cleaning."] [2.2 Observational Results: "by dividing the disk radial range into a series of annular rings with a width 1/4th of the beam major axis and averaging the emission for each ring"]
  - software: bettermoments, GoFish
  - validation: Radial profiles also made without Keplerian masking for comparison [2.2 Observational Results: "We have also shown the radial profiles for all the transitions generated without keplerian masking"]
- step 3: measure disk-integrated line flux, width and peak velocity
  - method: Shift-and-stack Keplerian deprojected spectrum with GoFish integrated_spectrum (120-550 au), Gaussian fit with scipy curve_fit, flux from numpy.trapz over a velocity range chosen by eye [2.2 Observational Results: "We employed the shifting and stacking technique using the `integrated_spectrum` function in the `GoFish` package (cite: GoFish) to generate a disk-integrated spectrum."] [2.2 Observational Results: "We have done a Gaussian fit to the observed spectrum using the `scipy.optimize.curve_fit`"]
  - software: GoFish, scipy, numpy
  - parameter: Radial range 120 to 550 au; shifted to systemic velocity 6.4 km/s [2.2 Observational Results: "The radial range for generating the integrated spectrum is between 120 au and 550 au."] [2.2 Observational Results: "Velocities for each pixel were shifted to the systemic one, 6.4 km/s"]
  - fitting: Single Gaussian fit with scipy.optimize.curve_fit; FWHM = 2 sqrt(2 ln 2) sigma [2.2 Observational Results: "We have done a Gaussian fit to the observed spectrum using the `scipy.optimize.curve_fit` to determine the peak intensity and the velocity at which the peak occurs."]
  - validation: Stacked spectra peak at the systemic velocity, confirming the detections [2.2 Observational Results: "are peaking at the systemic velocity, $v_{\text{LSRK}}$ of 6.4 km/s, confirming the detections"]
- step 4: verify detections with a matched filter
  - method: Cross-correlate observed visibilities with model visibilities from the Keplerian masks using VISIBLE [2.2 Observational Results: "we cross-correlate observed visibility with modelled visibility derived from the Keplerian masks used during cleaning"] [2.2 Observational Results: "We utilized a package called `VISIBLE` (cite: loomis2018visible) for this task."]
  - software: VISIBLE
  - validation: Filter response 43 sigma (N2H+) and 20 sigma (DCO+) at 6.4 km/s [2.2 Observational Results: "we found a filter response of 43 $\sigma$, and for DCO$^+$ (5-4), it is 20 $\sigma$ at the systemic velocity of 6.4 km/s"]
- step 5: fit visibilities with a parametric disk model for geometry, surface density and temperature
  - method: DISKFIT least-squares fit to visibilities of a flared Keplerian disk with two-Gaussian surface density and power-law rotation temperature; stage 1 per-line geometry, stage 2 geometry fixed to the averaged values and 9 remaining parameters … [3.1 DiskFit modelling: "we perform a least-square fit to the observed visibilities to adjust an empirical parametric disk model to the data, using the DISKFIT tool from (cite: Pietu2007)"] [3.1 DiskFit modelling: "In the first stage, geometric parameters are individually fitted for every observed transition."]
  - software: DISKFIT, IMAGER, CASA
  - parameter: Surface density as the sum of two Gaussians truncated to 150-550 au; temperature a power law defined by T250 and exponent q [3.1 DiskFit modelling: "we represented the radial surface density profiles for each molecule by the sum of two Gaussians, truncated to inner and outer radii of 150 and 550 au, respectively"] [3.1 DiskFit modelling: "The rotation temperature is assumed to be a simple power law, defined by its value at 250 au, $T_{250}$ and exponent $q$."]
  - parameter: H2D+: same adopted geometry, constant T = 15 K, uniform surface density 150-450 au [3.1 DiskFit modelling: "a constant temperature of 15 K, and a uniform surface density between 150 and 450 au"]
  - assumption: Boltzmann level populations, temperature power law in radius [3.1 DiskFit modelling: "The model assumes level populations are governed by a Boltzmann law, with the temperature being a power law of radius."]
  - assumption: Same vertical distribution for all molecules; constant intrinsic line width with radius [3.1 DiskFit modelling: "Molecules are assumed to follow the same vertical distribution for simplicity."] [3.1 DiskFit modelling: "we assume that the intrinsic line width remains constant with radius"]
  - assumption: Distance 150 pc [3.1 DiskFit modelling: "using the distance of 150 pc determined from Gaia"]
  - fitting: Modified Levenberg-Marquardt least squares on visibilities; error bars from the covariance matrix [3.1 DiskFit modelling: "A least square minimization is performed on the different visibilities using a modified Levenberg-Marquardt algorithm."] [3.1 DiskFit modelling: "Error bars are derived from the covariance matrix."]
  - validation: Best-fit radial profile imaged from model visibilities and Kepler-deprojected, compared with the data [3.1 DiskFit modelling: "where the best fit radial profile (reconstructed by imaging the model visibilities and applying the Kepler deprojection) is compared with the data"]
- result: N2H+ (4-3) disk-integrated flux = 1570 ± 40 mJy km/s [Table: Properties of the Lines Observed: "1570 $\pm$ 40"]
- result: DCO+ (5-4) disk-integrated flux = 290 ± 20 mJy km/s [Table: Properties of the Lines Observed: "290 $\pm$ 20"]
- result: N2H+ (4-3) line width (FWHM of Gaussian fit) = 0.55 ± 0.01 km/s [Table: Properties of the Lines Observed: "0.55 $\pm$ 0.01"]
- result: DCO+ (5-4) line width (FWHM of Gaussian fit) = 0.46 ± 0.01 km/s [Table: Properties of the Lines Observed: "0.46 $\pm$ 0.01"]
- result: Matched-filter response N2H+ (4-3) = 43 ± not stated sigma [2.2 Observational Results: "we found a filter response of 43 $\sigma$"]
- result: Matched-filter response DCO+ (5-4) = 20 ± not stated sigma [2.2 Observational Results: "for DCO$^+$ (5-4), it is 20 $\sigma$ at the systemic velocity of 6.4 km/s"]
- result: Inclination from N2H+ (4-3) DISKFIT = 36.5 ± 0.4 deg [Table: Geometric parameters: "36.5 $\pm$ 0.4"]
- result: Inclination from DCO+ (5-4) DISKFIT = 37.0 ± 0.4 deg [Table: Geometric parameters: "37.0 $\pm$ 0.4"]
- result: Keplerian velocity at 100 au from N2H+ (4-3) = 3.61 ± 0.03 km/s [Table: Geometric parameters: "3.61 $\pm$ 0.03"]
- result: Keplerian velocity at 100 au from DCO+ (5-4) = 3.54 ± 0.03 km/s [Table: Geometric parameters: "3.54 $\pm$ 0.03"]
- result: N2H+ rotation temperature at 250 au (T250) = 12.2 ± 0.7 K [Table: Best fit parameters: "12.2 $\pm$ 0.7"]
- result: DCO+ rotation temperature at 250 au (T250) = 16.0 ± 1.2 K [Table: Best fit parameters: "16.0 $\pm$ 1.2"]
- result: N2H+ temperature exponent q = -0.32 ± 0.19 dimensionless [Table: Best fit parameters: "-0.32 $\pm$ 0.19"]
- result: DCO+ temperature exponent q = 0.39 ± 0.15 dimensionless [Table: Best fit parameters: "0.39 $\pm$ 0.15"]
- result: N2H+ peak surface density N1 (DISKFIT) = 22 ± 8 1e11 cm-2 [Table: Best fit parameters: "22 $\pm$ 8"]
- result: N2H+ peak surface density N2 (DISKFIT) = 12 ± 2 1e11 cm-2 [Table: Best fit parameters: "12 $\pm$ 2"]
- result: DCO+ peak surface density N1 (DISKFIT) = 2.8 ± 0.6 1e11 cm-2 [Table: Best fit parameters: "2.8 $\pm$ 0.6"]
- result: DCO+ peak surface density N2 (DISKFIT) = 5.3 ± 1.0 1e11 cm-2 [Table: Best fit parameters: "5.3 $\pm$ 1.0"]
- result: DCO+ inner ring peak radius = 210 ± 50 au [6 Conclusions: "The inner ring peaks at $210 \pm 50$ au within the continuum ring region"]
- result: DCO+ outer ring peak radius = 375 ± 10 au [6 Conclusions: "the more intense outer ring peaks at $375 \pm 10$ au in the outer disk"]
- result: o-H2D+ 3 sigma upper limit surface density (DISKFIT) = 2.1e10 ± not stated cm-2 [3.1 DiskFit modelling: "This gives the 3$\sigma$ upper limit on o- to be $2.1 \times 10^{10}$ cm$^{-2}$."]
- result: Total H2D+ 3 sigma upper limit surface density at 15 K (from ortho value) = 6.3e12 ± not stated cm-2 [3.2 Results: "At 15 K, the 3$\sigma$ upper limit on the total surface density, derived from the ortho- value, is $6.3 \times 10^{12}$ cm$^{-2}$."]
- limitation (authors): X-ray chemistry not included [5.2 Chemical Trends: "Additionally, our models do not include X-ray chemistry"]
- limitation (authors): Outer disk not modelled because of its complex structure [5.3 Possible Chemistry in the Outer Disk: "We have not modelled the outer disk due to its complex structure"]
- not stated (card): Line-free channel ranges used for self-calibration, uvcontsub and the continuum image; Self-calibration solution intervals and per-round gain settings; per-execution flux scale uncertainty; Image sizes, cell sizes in arcsec, channel width of the final cubes, and clean niter/threshold; Keplerian mask thresholds and how the robust=1.0 versus natural/multiscale choice maps to each line; Primary beam…

### 2021A&A...650A..59B: Vortex-like kinematic signal, spirals, and beam smearing effect in the HD 142527 disk (2021; protoplanetary_disks; archival_reuse)
- question: Do the 13CO and C18O J=3-2 gas kinematics of the HD 142527 circumbinary disk show deviations from Keplerian rotation consistent with a large vortex around the dust crescent, and can beam smearing explain them instead?
- step 2: Fit Keplerian rotation to the velocity map
  - method: Eddy MCMC fit at R >= 150 au to fix center of rotation and PA, then chi-square fit along major and minor axes between 100 and 400 au for stellar mass and systemic velocity [2.2 Overview of the gas kinematics: "We used the software Eddy described in (cite: Teag2019a) which is based on an MCMC method, and takes into account the signal-to-noise in each pixel of the image."] [2.2 Overview of the gas kinematics: "Second, we used a chi-square method along the minor and major axes of the disk to fit the mass and the systemic velocity V$_{lsr}$ of the system between 100 and 400 au"]
  - software: Eddy
  - parameter: inclination fixed to 27 deg; fit binary mass, systemic velocity, PA and center of rotation [2.2 Overview of the gas kinematics: "We fixed the disk inclination to 27$^{\circ}$ and fit the mass of the binary, the systemic velocity of the system, the PA of the disk, and the center of rotation."]
  - parameter: inner 100 au discarded [2.2 Overview of the gas kinematics: "We discarded the inner 100 au of the system"]
  - parameter: first step uses R >= 150 au [2.2 Overview of the gas kinematics: "we used the MCMC code Eddy well outside from the cavity (i. e., R $\geq$ 150 au)"]
  - assumption: geometrically thin disk (gas scale height not fitted) [2.2 Overview of the gas kinematics: "We used a geometrically thin disk for the fit because we could not precisely constrain the gas scale height"]
  - assumption: distance of 157 pc [2.1 Morphology of the dust and gas emis…: "taking a distance of 157 pc for the system"]
  - fitting: MCMC (Eddy) weighted by per-pixel signal-to-noise for the center and PA; chi-square without radial S/N weighting for mass and V_lsr; priors and likelihood not stated [2.2 Overview of the gas kinematics: "without taking radial variations of the signal-to-noise ratio into account"] [2.2 Overview of the gas kinematics: "takes into account the signal-to-noise in each pixel of the image"]
  - validation: Fit result compared across radial ranges; kinematic features checked to be independent of the fitting procedure [2.2 Overview of the gas kinematics: "Large discrepancies were found depending on the radial distance range considered."] [2.2 Overview of the gas kinematics: "They are present independently of the exact fitting procedure used"]
- step 3: Map velocity deviations from Keplerian rotation and identify kinematic features
  - method: Subtract projected Keplerian velocity to get a 2D residual map and radial cuts at different azimuths; compare 13CO and C18O [3.1 Preliminary analysis: "Radial cuts of the velocity deviations at different azimuthal angles are shown in"] [3.1 Preliminary analysis: "The velocities measured using the $^{13}$CO and C$^{18}$O lines give very similar values, with differences no larger than 20-30 m s$^{-1}$ between $\sim$ 100 and $\sim$ 350 au."]
  - software: Eddy
  - assumption: vertical motions neglected in the radial Doppler-shifted structure [3.1 Preliminary analysis: "at first order, they can probably be neglected in the radial Doppler-shifted structure"]
  - validation: Both isotopologues give consistent velocities [3.1 Preliminary analysis: "This suggests that both isotopologues emit from a similar altitude"]
- step 5: Quantify beam-smearing velocity biases with a Keplerian radiative transfer model
  - method: RADMC-3D 3D model of the circumbinary disk in pure Keplerian rotation, ray-traced and convolved to 0.1 and 0.3 arcsec; measure velocity deviations and the beam-edge emission ratio I_out/I_in [4.1 Velocity deviations are also observ…: "The resulting signal is then convolved by a Gaussian of 0.1$''$ and 0.3$''$ in order to reproduce typical spatial resolutions of molecular lines in ALMA observations."] [4.2 Line intensity gradients skew measu…: "this variation can be estimated by the emission ratio I$_\mathrm{out}$/I$_\mathrm{in}$ between the outer and inner edges of the synthesized beams"]
  - software: RADMC-3D
  - parameter: grid cells of 1 au in radius, 2 deg in azimuth and 1 deg in elevation [A 3D toy model for HD 142527: "using cells of 1 au in radius, 2$^\circ$ in azimuth and 1$^\circ$ in elevation"]
  - parameter: ray-tracing pixel size 20 mas, velocity resolution 10 m/s [A 3D toy model for HD 142527: "we performed the ray-tracing in a square grid with a pixel size of 20 mas and a velocity resolution of 10 m s$^{-1}$"]
  - parameter: ideal observations without noise at 25 m/s velocity resolution for Figure 6 [4.1 Velocity deviations are also observ…: "(i.e., without noise and at a velocity resolution of 25 m s$^{-1}$)"]
  - assumption: pure Keplerian rotation around a single star of 2.36 Msun, inclination 27 deg, PA -19 deg [A 3D toy model for HD 142527: "the gas is in pure Keplerian rotation around a single star of 2.36 $M_\odot$"] [A 3D toy model for HD 142527: "We assume a disk inclination of 27$^\circ$ and a PA of -19$^\circ$."]
  - validation: Model deviations compared with the observed pattern at R > 150 au [4.1 Velocity deviations are also observ…: "At a radius larger than 150 au, the observed kinematic signal is similar to the velocity pattern seen in the pure Keplerian model at 0.3$''$"]
- step 6: Test whether beam smearing, dust and continuum subtraction, and pressure gradients can mimic the vortex signal
  - method: Compare velocity deviations in the model by radial region with the flux ratio after continuum subtraction, then compare model and observed amplitudes and radii of the feature [4.3 Dust also affects the measured gas …: "the measured velocity deviations are in good agreement with the flux variations measured after continuum-subtraction"] [4.4 Beam smearing and gas pressure grad…: "these artifacts are of lower amplitude in our model, with velocities reaching 90 m s$^{-1}$ on the inner side and 20 m s$^{-1}$ on the outer side"]
  - software: RADMC-3D
  - assumption: gas surface density three to five times larger on the northern side of the disk, with radial pressure gradients adding non-Keplerian motions [4.4 Beam smearing and gas pressure grad…: "With a gas surface density three to five times larger on the northern side of the disk, significant non-Keplerian motions may appear"]
  - validation: Beam smearing alone judged unlikely to explain the signal; beam smearing plus pressure gradients cannot be excluded [4.4 Beam smearing and gas pressure grad…: "It therefore appears unlikely that the beam smearing effect alone can produce the azimuthal velocity deviations."]
- result: Binary mass, R = 100-200 au (Eddy) = 2.53 ± 0.04 Msun [2.2 Overview of the gas kinematics: "For R between 100 and 200 au, we obtain a binary mass of 2.53 $\pm$ 0.04 M$_\odot$"]
- result: Binary mass, R > 200 au (Eddy) = 2.29 ± 0.07 Msun [2.2 Overview of the gas kinematics: "where for R $>$ 200 au, we obtain a binary mass of 2.29 $\pm$ 0.07 M$_\odot$"]
- result: Binary mass, fit over the whole circumbinary disk = 2.48 ± 0.03 Msun [2.2 Overview of the gas kinematics: "yielding a binary mass of 2.48 $\pm$ 0.03 M$_\odot$"]
- result: Binary mass, adopted chi-square fit 100-400 au = 2.36 ± 0.07 Msun [2.2 Overview of the gas kinematics: "and obtain a binary mass of 2.36 $\pm$ 0.07 M$_\odot$, and a V$_{lsr}$ of 3730 $\pm$ 20 m s$^{-1}$"]
- result: Systemic velocity V_lsr = 3730 ± 20 m/s [2.2 Overview of the gas kinematics: "and a V$_{lsr}$ of 3730 $\pm$ 20 m s$^{-1}$"]
- result: Disk position angle (Eddy, R >= 150 au) = 161.1 ± 0.4 deg [2.2 Overview of the gas kinematics: "of the PA $=$ 161.1$^{\circ}$ $\pm$ 0.4$^{\circ}$ of the disk"]
- result: Maximum projected velocity deviation of the main kinematic structure = 160 ± not stated m/s [2.2 Overview of the gas kinematics: "a large radial Doppler-shifted structure in the north of the disk with projected velocities up to 160 m s$^{-1}$"]
- result: Velocity deviation of the main structure after deprojection = 0.35 ± not stated km/s [3.1 Preliminary analysis: "or of 0.35 km s$^{-1}$ after deprojection, about 10% of the background Keplerian rotation"]
- result: Transition radius between super- and sub-Keplerian regimes = 185 ± not stated au [3.1 Preliminary analysis: "The transition radius between these two regimes is at 185 au"]
- result: Maximum projected velocity deviations along the spiral arcs = ~50 ± not stated m/s [2.2 Overview of the gas kinematics: "All these arcs and spirals have maximum projected velocity deviations on the order of 50 m s$^{-1}$."]
- result: Beam-smearing velocity deviation in Keplerian model at 0.3 arcsec = 20-80 ± not stated m/s [4.1 Velocity deviations are also observ…: "instead of only 20-80 m s$^{-1}$ in our models"]
- result: Ratio of velocity deviations at 0.3 arcsec to 0.1 arcsec along northern major axis = ~3 ± not stated dimensionless [4.2 Line intensity gradients skew measu…: "the velocity deviations at 0.1$''$ are about three times smaller than at 0.3$''$"]
- result: Beam-smearing artifact amplitude at inner and outer side of the model feature = 90 (inner), 20 (outer) ± not stated m/s [4.4 Beam smearing and gas pressure grad…: "with velocities reaching 90 m s$^{-1}$ on the inner side and 20 m s$^{-1}$ on the outer side"]
- limitation (authors): Vortex and beam-smearing-plus-pressure-gradient scenarios currently very difficult to differentiate [4.4 Beam smearing and gas pressure grad…: "It is then currently very difficult to assess if the signal is due to a real vortex or is produced by beam smearing associated with gas pressure gradients."]
- limitation (authors): Vortex velocity profile not measurable from the data (Gaussian assumed) [3.2 Vortex model: "The exact vortex velocity profile cannot be measured from our current data, and we assume it has a Gaussian profile."]
- limitation (authors): Gas scale height could not be constrained, thin disk used [2.2 Overview of the gas kinematics: "We used a geometrically thin disk for the fit because we could not precisely constrain the gas scale height"]
- not stated (card): Calibration and imaging recipe of the 2012.1.00725.S data (CASA version, calibrators, self-calibration, robust, uv taper, cell and image size, clean threshold): all deferred to Boeh2017; Synthesized beam size and shape and per-channel rms of the 13CO and C18O cubes; Line-free channels used for continuum subtraction and the exact channel range used for moment 1; How the 5 sigma per-pixel threshold…

### 2018ApJ...865..131L: High-resolution ALMA Study of the Proto-brown-dwarf Candidate L328-IRS (2018; star_formation; observational_alma_primary)
- question: Is the proto-brown-dwarf candidate L328-IRS substellar? Measure its central mass via disk kinematics and refine the outflow inclination and mass accretion rate.
- step 2: Derive disk rotation curve and dynamical mass
  - method: PV diagram along the major axis; Gaussian fit to the spectrum at each position; subtract systemic velocity; compare with Keplerian curves [4.1 Rotational kinematics: "We fitted each spectrum with a Gaussian function to obtain the velocity at its peak intensity at each position."]
  - parameter: Disk PA 106.5 deg; inclination 25.2 deg; systemic velocity 6.61 km/s [4.1 Rotational kinematics: "Our obtained systemic velocity is 6.61 $\rm km~s^{-1}$"]
  - assumption: Circular disk; inclination from arcsin(b/a) [4.1 Rotational kinematics: "we assume that the disk is in circular shape when it is viewed face-on"]
  - fitting: Keplerian curves for 0.05-0.4 Msun compared by eye; no formal sampler stated [4.1 Rotational kinematics: "theoretical Keplerian motions in the disk by the central point sources of 0.05 to 0.4 ${\rm\,M_\odot}$"]
  - validation: Repeated with 13CO, giving similar results [4.1 Rotational kinematics: "We found very similar results seen in diagrams for C$^{18}$O line data in Figure 10"]
- step 5: Indirect central mass estimates
  - method: Mass from accretion luminosity matching L_int, and from accreted mass over the dynamical time at constant rate [4.3 ALMA estimation of mass accretion r…: "the total accreted mass would be $\sim 0.023~{\rm\,M_\odot}$ in this case"]
  - parameter: L_acc = G M Mdot/(2R); L_int ~0.05 Lsun; dynamical time ~2.8e4 yr; 10% outflow extraction [4.3 ALMA estimation of mass accretion r…: "with an assumption of $10\%$ extraction of the accreted mass through the outflow"]
  - assumption: L_int is entirely from accretion; constant accretion rate [Table 2: "Valid only if $\dot M_{acc}$ is constant during dynamical time"]
  - validation: Two independent assumptions give consistent masses; authors keep the identification tentative [Summary: "Thus the identification of L328-IRS as a proto-brown dwarf must be considered tentative."]
- result: Systemic velocity = 6.61 ± not stated km/s [4.1 Rotational kinematics: "Our obtained systemic velocity is 6.61 $\rm km~s^{-1}$"]
- result: Keplerian dynamical mass (C18O, 130-60 AU) = ~0.30 ± not stated Msun [4.1 Rotational kinematics: "the best fitted with the Keplerian motions in the disk by a stellar object of $\sim0.30 ~{\rm\,M_\odot}$"]
- result: Keplerian dynamical mass (13CO, 140-60 AU) = ~0.27 ± not stated Msun [4.1 Rotational kinematics: "by a central object of $\sim 0.27{\rm\,M_\odot}$"]
- result: Accretion luminosity for 0.3 Msun = ~1.3 ± not stated Lsun [4.3 ALMA estimation of mass accretion r…: "its accretion luminosity is estimated to be $\sim 1.3~{\rm\,L_\odot}$"]
- result: Mass from internal luminosity = ~0.012 ± not stated Msun [4.3 ALMA estimation of mass accretion r…: "can be estimated to be $\sim 0.012~{\rm\,M_\odot}$"]
- result: Accreted mass over dynamical time = ~0.023 ± not stated Msun [4.3 ALMA estimation of mass accretion r…: "the total accreted mass would be $\sim 0.023~{\rm\,M_\odot}$"]
- limitation (authors): The accretion rate depends on uncertain parameters (entrainment efficiency, mass-loss ratio, wind velocity) and on the assumption of a constant rate. [4.3 ALMA estimation of mass accretion r…: "Our estimation of accretion rate can be affected by various uncertain parameters including the entrainment efficiency"]
- limitation (authors): A stellar mass cannot be ruled out. [4.3 ALMA estimation of mass accretion r…: "we can not completely rule out a possibility that L328-IRS can have a stellar mass, too"]
- not stated (card): CASA version and whether the pipeline or manual calibration was used; Self-calibration, if any; Cell size, image size, clean threshold, masking and deconvolver; Continuum-subtraction line-free channels; Channel width and velocity resolution of the images used for PV and moment maps; Exact PV cut width and Gaussian fit details; Details of the toy model rendering and masking of the observed maps; O…

### 2025SciA...11.6953M: A misaligned protostellar disk fed by gas streamers in a barred spiral-like massive dense core (2025; star_formation, milky_way_ism; observational_alma_primary)
- question: How do massive dense cores assemble and transfer mass across scales (spiral arms, bar, pseudodisk, disk) to form a high-mass young stellar object, and is its disk aligned with the surrounding envelope?
- step 3: Test velocity coherence along arms and bar with PV diagrams
  - method: PV cuts along the identified curves and bar axis; velocity gradients read from PV and moment 1 maps [Spiral-arm-like structures: Gas Kinemat…: "The PV cuts are placed along the curves we identified in the previous section."]
  - assumption: Velocity gradients are interpreted as infall toward the central object [Spiral-arm-like structures: Gas Kinemat…: "The velocity gradients seen in the PV diagrams may indicate that the gas is infalling to the center of the clump driven by the gravitational force of the central object."]
- step 4: Model arm kinematics with an infalling-rotating particle trajectory
  - method: Analytic streamline of a particle in a rotating cloud falling onto a central point mass, parameters adjusted by hand to match peak-intensity and velocity maps of S2 and S5 [Infalling-rotating particle trajectory: "using an analytic solutions *(cite: 2009MNRAS.393..579M, 2020NatAs...4.1158P)* of a particle moving within a rotating cloud toward a central mass"] [Infalling-rotating particle trajectory: "We manually adjust the model and streamline parameters to find the best match parameter set."]
  - parameter: S2: initial distance 52,000 au, position angle 21 deg, polar angle 70 deg [Infalling-rotating particle trajectory: "using the initial distance of 52,000 au, the position angle of 21$^{\circ}$, and the polar angle of 70$^{\circ}$ for S2"]
  - parameter: Angular velocity 4e-14 rad/s, initial radial velocity 0.6 km/s [Infalling-rotating particle trajectory: "The angular velocity is assumed as $4\times10^{-14}~{\rm rad~s^{-1}}$ and the initial radial velocity is 0.6 $\rm km~s^{-1}$."]
  - parameter: Central mass 50-80 Msun [Infalling-rotating particle trajectory: "assuming a central mass of 50-80$\,M_{\odot}$ in S2 and S5"]
  - assumption: Rotating-plane inclination between 0 and 20 deg (0 deg = face-on); 10 deg plane used for the polar angle [Infalling-rotating particle trajectory: "we assume the inclination angle to be between 0$^{\circ}$ to 20$^{\circ}$ (where 0$^{\circ}$ represents a face-on view)"]
  - fitting: Manual adjustment of parameters, no formal fit [Infalling-rotating particle trajectory: "We manually adjust the model and streamline parameters to find the best match parameter set."]
  - validation: Model reproduces kinematics along S2 and S5 but not the V-shaped profiles of S1 and S2 [Spiral-arm discussion: "While this idealized kinematic model with a central mass of 50-80 $M_{\odot}$ successfully reproduces the gas kinematics along S2 and S5"]
- step 5: Fit the pseudodisk geometry and central mass with an infalling-rotating envelope model
  - method: Model CH3OH 4_2-3_1 E1 vt=0 emission as a flattened infalling and rotating envelope with FERIA; chi2 grid search over four free parameters [IRE modeling: "Here we model the pseudodisk as a flattened infalling and rotating envelope (IRE) with the publicly available code FERIA"] [IRE modeling: "The central mass $M_{*,e}$, the centrifugal radius $r_{\rm CB}$, the outer radius of the IRE $r_{\rm out}$ and the inclination $i$ are treated as free parameters."]
  - software: FERIA
  - parameter: Position angle fixed to the velocity gradient in the centroid velocity map [IRE modeling: "The position angle of the IRE model is fixed to the velocity gradient observed in the centroid velocity map."]
  - parameter: Fine-grid ranges: M 20-70 Msun, i 0-20 deg, r_CB 0-200 au, r_out 800-1200 au [Table S1 (parameter range): "20–70"] [Table S1 (parameter range): "800–1200"]
  - assumption: Model has only a central point mass; 45 Msun best fit considered too massive for an early protostar [IRE modeling: "The model only considers a central point mass, and the best-fit 45 $M_{\odot}$ is too massive for a protostar at a very early stage."]
  - fitting: Coarse then fine chi2 grid search (not MCMC) [IRE modeling: "we employed a $\chi^2$ grid search to explore the parameter space in this study."] [IRE modeling: "we began with a coarse $\chi^2$ grid search to constrain the parameter ranges, followed by a fine grid search."]
  - validation: Chi2 shows a ridge-like degeneracy between central mass and inclination; model reproduces curvature in centroid velocity maps; CH3CN lines show similar geometry [IRE modeling: "Notably, the $\chi^2$ distribution in the $i$ – $M_{*,e}$ space reveals a ridge-like pattern, where central mass and inclination are correlated."] [Spirals-bar-disk discussion: "Similar geometry and kinematics of the pseudodisk are also well revealed by other dense gas tracers such as CH$_3$CN lines"]
- step 7: Fit Keplerian rotation to the 12 GHz methanol maser disk
  - method: Project maser spots onto a PV cut and fit a Keplerian rotation curve with scaled enclosed mass M sin^2 i and system velocity free [Dynamics of the maser disk: "we modeled the spatial-kinematics of the maser using a Keplerian rotation model"] [Dynamics of the maser disk: "and the system velocity as free parameters"]
  - software: SciPy
  - parameter: Southeast and northwest blueshifted/redshifted clusters selected by hand; northeast cluster excluded as outflow-related [Dynamics of the maser disk: "We manually selected two blueshifted and redshifted maser clusters in the southeast and northwest"]
  - parameter: PA of PV cut fixed to steepest velocity gradient in ALMA data; disk center at the long-baseline 1.3 mm continuum peak [Dynamics of the maser disk: "The position angle of the position-velocity cut was fixed as the direction of the steepest velocity gradient in the ALMA observation."] [Dynamics of the maser disk: "The disk center was assumed to be the peak of the long-baseline 1.3 mm continuum."]
  - assumption: Stellar mass 8-16 Msun from spectral type B3-B0 gives disk inclination 20-30 deg [Spirals-bar-disk discussion: "Assuming this stellar mass range, the inclination of the maser disk would be $20^{\circ}$ to $30^{\circ}$."]
  - fitting: Least-squares fit in SciPy [Dynamics of the maser disk: "The scaled enclosed mass was estimated using the least-square fitting, implemented in SciPy"]
  - validation: Remaining masers follow Keplerian rotation; using the pseudodisk inclination would give an unphysical >180 Msun mass [Spirals-bar-disk discussion: "the remaining 12 GHz Class II methanol masers follow Keplerian rotation very well"] [Spirals-bar-disk discussion: "the mass of HMYSO $M_{*,d}$ would be over 180 $M_{\odot}$"]
- result: IRE best-fit central mass, inclination, centrifugal radius, outer radius = 45 Msun, 6 deg, 60 au, 950 au ± not stated (central mass poorly constrained, M-i degenerate) Msun, deg, au, au [IRE modeling: "includes $M_{*,e}$ of 45 $M_{\odot}$, $i$ of $6^\circ$, $r_{\rm CB}$ of 60 au, and $r_{\rm out}$ of 950 au"]
- result: Pseudodisk inclination upper bound = <15 ± not stated deg [IRE modeling: "tightly constrains the inclination to $<15^\circ$"]
- result: Maser disk scaled enclosed mass M sin^2 i = 1.93 ± 0.07 Msun [Dynamics of the maser disk: "to be $M_{*,d}\times\sin^2 i=1.93\pm0.07\,M_{\odot}$"]
- result: Dynamical mass if the maser disk had the pseudodisk inclination = over 180 ± not stated Msun [Spirals-bar-disk discussion: "the mass of HMYSO $M_{*,d}$ would be over 180 $M_{\odot}$"]
- result: Maser-disk inclination for an 8-16 Msun star = 20 to 30 ± not stated deg [Spirals-bar-disk discussion: "the inclination of the maser disk would be $20^{\circ}$ to $30^{\circ}$."]
- limitation (authors): Accretion rate is a lower limit (optically thin 12CO assumed, missing short spacings) and not corrected for outflow inclination [Spirals-bar-disk discussion: "Since we assume $^{12}$CO emission is optically thin, and due to the potential missing flux caused by the lack of short spacing of the interferometer, this accretion rate would be the lower limit of the exact accretion rate."]
- limitation (authors): Idealised particle-trajectory model fails to capture the whole system's dynamics [Spiral-arm discussion: "While this idealized kinematic model with a central mass of 50-80 $M_{\odot}$ successfully reproduces the gas kinematics along S2 and S5, it can not capture the entire system"]
- limitation (authors): IRE model is insensitive to the central mass [IRE modeling: "The model is insensitive to central mass but tightly constrains the inclination to $<15^\circ$."]
- not stated (card): Spectral windows, channel widths and velocity resolution of the Band 3 and Band 6 cubes used for each line; CASA tclean settings: deconvolver, niter, threshold, masks, multiscale, primary-beam correction; Continuum definition: line-free channels and continuum subtraction method; How ACA and 12 m (C-2, C-5) data were combined in Band 6 (concat, weights, uv ranges) and which executions were used; S…

### 2020ApJ...904..181L: ALMA View of the Infalling Envelope around a Massive Protostar in S255IR SMA1 (2020; star_formation, astrochemistry; observational_alma_primary)
- question: Characterize the gas around S255IR NIRS3/SMA1 and distinguish a Keplerian disc from a rotating infalling envelope.
- step 6: Measure morphology and inspect rotational kinematics
  - method: Inspect integrated K=3 emission, channel maps and a position-frequency cut through the continuum peak; extract P-V diagrams for K=0–10 and compare Keplerian curves. [CH$_3$CN: distribution and temperature: "the integrated intensity map of the CH$_3$CN $J$=19–18 $K$=3 transition"] [CH$_3$CN: kinematic signatures: "made with a cut running through the SMA1 peak at a P.A. of 165 degree."]
  - parameter: Cut P.A. 165 degree; systemic velocity 5.2 km s^-1 [CH$_3$CN: kinematic signatures: "made with a cut running through the SMA1 peak at a P.A. of 165 degree."] [Observations: "We adopt a systemic velocity of 5.2 km s$^{-1}$ for the target."]
  - parameter: Keplerian comparison curves: 8.04/sin^2 i, 3.57/sin^2 i and 0.89/sin^2 i M☉ [CH$_3$CN: kinematic signatures: "Keplerian rotation of (8.04/$sin^2 i$) M$_\odot$, (3.57/$sin^2 i$) M$_\odot$, and (0.89/$sin^2 i$) M$_\odot$"]
  - assumption: Axisymmetric circumstellar structure; inclination i=0 is face-on [CH$_3$CN: kinematic signatures: "where $i$ represents the inclination angle of the system with $i = 0$ meaning face-on."] [CH$_3$CN: kinematic signatures: "a axisymmetric circumstellar structure with a diameter of 1$''$, a P.A. of 165 degree"]
  - fitting: Qualitative comparison of observed P-V emission with Keplerian curves [CH$_3$CN: kinematic signatures: "the blue curve matches reasonably the emission pattern at the two ends."]
  - validation: Compare elongation and velocity-gradient orientation with the outflow; inspect compactness and gradient changes with K [CH$_3$CN: kinematic signatures: "Since this gradient is closely perpendicular to the general direction of the bipolar outflows, it most plausibly indicates rotation."] [CH$_3$CN: kinematic signatures: "at progressively higher $K$s, the emission extent becomes more compact and the apparent velocity gradient gets steeper."]
- step 7: Test rotating-disc and infalling-envelope models
  - method: Generate SPARX molecular-line cubes for M1–M4, convolve with CASA imsmooth, extract CASA impv diagrams and compare with observed CH3CN P-V structure. [Radiative transfer modeling: "The software package produces image cubes through radiative transfer calculations of molecular line radiation with input physical models."] [Radiative transfer modeling: "We further convolve these synthetic image cubes output by SPARX with the observing resolution (0.14$''$) using the *"imsmooth"* command in CASA and generate the model P-V diagrams with the CASA *"impv"* task."]
  - software: SPARX, CASA, imsmooth, impv
  - parameter: M1: pure Keplerian, 20 M☉, 25 degree; M2: pure Keplerian, 4.76 M☉, 60 degree; Table 1 rounds the latter mass to 4.8 M☉ [Radiative transfer modeling: "In toy Model 1 (M1) and Model 2 (M2), we assumed the emissions are from gas following pure Keplerian rotation."] [Radiative transfer modeling: "their central YSO masses and inclination angles being 20 M$_\odot$and 4.76 M$_\odot$, and 25 degree and 60 degree, respectively."]
  - parameter: M3: Keplerian azimuthal motion around 4.76 M☉ at 60 degree, plus constant radial infall 2.5 km s^-1 [Radiative transfer modeling: "around a central mass of 4.76 M$_\odot$at an inclination angle of 60 degree"] [Radiative transfer modeling: "also bears a radial infall velocity of 2.5 km s$^{-1}$at all radii."]
  - parameter: M4: Ulrich accretion-flow velocity field; arbitrarily assumed centrifugal barrier 90 au [Radiative transfer modeling: "another model (M4) in which the gas follows the accretion flow prescribed by (cite: Ulrich76)."] [Radiative transfer modeling: "For the purposing of testing, we assume arbitrarily its centrifugal barrier at a small radius of 90 au (or 0.05$''$)."]
  - parameter: Surface-density profile r^-1.1; at 900 au M1 has 0.79 g cm^-2 and M2–M4 have 0.71 g cm^-2 [Table 1: "$r^{-1.1}$"] [Table 1: "(0.79 g cm$^{-2}$)"]
  - parameter: Temperature: 430 K at r < 214 au; 430 (r/214)^-0.7 K at r ≥ 214 au [Table 1: "430~\mbox{K} & r < 214~\mbox{au}"] [Table 1: "430~(r/214)^{-0.7}~\mbox{K} & r \geq 214~\mbox{au}"]
  - parameter: CH3CN abundance 2 × 10^-8; abundance truncated at radius 900 au; turbulent velocity 2 km s^-1 [Radiative transfer modeling: "We then set a CH$_3$CN fractional abundance be $2\times 10^{-8}$"] [Radiative transfer modeling: "we truncate the CH$_3$CN abundance at a radius of 900 au"]
  - assumption: Flattened two-dimensional structure; empirical column-density and temperature profiles; gas-to-dust ratio 100 [Radiative transfer modeling: "we first assume that the emission originates from a flattened two-dimensional structure, possibly a disc or an envelope."] [Radiative transfer modeling: "For the molecular gas column density and temperature, we adopt the empirical profiles inferred in Section 3.3."]
  - assumption: LTE; no interferometric spatial filtering of model cubes [Radiative transfer modeling: "We carry out our calculations in the LTE regime since the observed transitions are most likely thermalized."] [Radiative transfer modeling: "no interferometric spatial filtering was applied to form the model cubes during this process"]
  - assumption: Neglect gas self-gravity in the gas-kinematic model calculations [Molecular gas mass estimates: "the subsequent model calculations of gas kinematics without considering their self-gravity should be reasonable."]
  - fitting: Qualitative comparison of modeled and observed P-V morphology, especially the central waist and edge-brightening [Radiative transfer modeling: "the central emission "waist" between the two ends at the two "quadrants" in the simulated P-V pattern is significant narrower than that of the observed emission."] [Radiative transfer modeling: "the emission is stronger on the "edges" of the "waist", similar to that in the observed pattern."]
  - validation: Compare K=3 observations with all four models; compare M4 predictions with all observed K components [Radiative transfer modeling: "we compare the observed $J=19-18, K=3$ emission features"] [Radiative transfer modeling: "the P-V diagram of the observed CH$_3$CN emission for all $K$ components in false color and the corresponding model emission in contours."]
- step 9: Compare the inferred envelope with burst-accretion simulations
  - method: Run PLUTO gravito-radiation-hydrodynamics and compare azimuthally averaged midplane surface density and gas velocities with the inferred envelope. [Comparison to the burst mode of accreti…: "The system is integrated by solving the equations of gravito-radiation-hydrodynamics with the pluto code"] [Comparison to the burst mode of accreti…: "the azimuthally-averaged midplane surface density and gas velocity profiles of the immediate surrounding environment of the simulated massive protostar."]
  - software: pluto
  - parameter: Initial core: 100 M☉, rigid rotation, 10 K, density ∝r^-3/2, kinetic-by-gravitational energy ratio β=4% [Comparison to the burst mode of accreti…: "We initialize the model with the gravitational collapse of a 100 M$_\odot$ rigidly-rotating pre-stellar core."] [Comparison to the burst mode of accreti…: "It has a temperature $T_{\rm c}=10$ K and a density distribution $\rho(r)\propto r^{-3/2}$"]
  - parameter: Spherical midplane-symmetric domain; inner radius 20 au, outer radius 0.1 pc; grid as printed: Nr=512 × Nφ=81 × Nθ=512 [Comparison to the burst mode of accreti…: "a spherical midplane-symmetric computational domain"] [Comparison to the burst mode of accreti…: "of inner radius $r_{\rm in}=20~{\rm au}$ that extends up to $R_{\rm c}=0.1~{\rm pc}$"]
  - parameter: Inner sink cell r≤20 au; stated simulation duration 40.0 kyr [Comparison to the burst mode of accreti…: "The inner boundary ($r\le20~{\rm au}$) is a sink cell localized at the origin of the domain"] [Comparison to the burst mode of accreti…: "We run the simulation up to $t_{\rm end}= 40.0~{\rm kyr}$ after the beginning of the collapse."]
  - assumption: Include gas inertia, stellar gravity and circumstellar gas self-gravity [Comparison to the burst mode of accreti…: "The gas inertia is included in the calculations as described in (cite: Meyer19a)."] [Comparison to the burst mode of accreti…: "The effects of the massive protostar’s gravity is estimated with the total gravitational potential"]
  - assumption: Gray approximation for direct stellar irradiation and radiative transport; no magnetic field [Comparison to the burst mode of accreti…: "The direct stellar irradiation feedback of the central star (cite: Meyer19b) and the radiative transport close to the star (cite: Vaidya11) are both treated within the so-called gray approximation (cite: Kolb13)."] [Comparison to the burst mode of accreti…: "the absence of magnetic field in the simulation."]
  - fitting: Select output with total gas velocity profile consistent with the Keplerian profile of a 20 M☉ protostar [Comparison to the burst mode of accreti…: "We select a simulation output on the basis of a total gas velocity profile consistent with the Keplerian velocity profile of a 20 M$_\odot$ protostar."]
  - validation: Qualitative comparison of surface density, sub-Keplerian azimuthal motion and radial infall [Comparison to the burst mode of accreti…: "The azimuthally-averaged surface density profile at the edge of the inner envelope/psuedo-disc in the simulation is $\approx$ $0.5-1.0$ g cm$^{-2}$."] [Comparison to the burst mode of accreti…: "This appears to be at a comparable level to the surface density (0.71 g cm$^{-2}$) we infer at 900 au."]
- result: Integrated CH3CN emission extent = around 1 arcsec (or 1800) ± not stated au [CH$_3$CN: distribution and temperature: "an extent of around 1$''$ (or 1800 au)"]
- result: Integrated CH3CN elongation position angle = 165 ± not stated degree [CH$_3$CN: distribution and temperature: "a position angle (P.A., measured from north towards east) of 165 degree."]
- result: Morphology-inferred inclination lower limit = no less than 60 ± not stated degree [CH$_3$CN: kinematic signatures: "the minor axis of the structure being roughly half in length of the major axis, would suggest an inclination angle of no less than 60 degree."]
- result: Keplerian-equivalent central mass of the preferred velocity curve at inclination 60 degree = no larger than ∼4.76 ± not stated M☉ [Angular momentum considerations: "This blue Keplerian velocity pattern, at an inclination angle of 60 degree, corresponds to a central mass no larger than $\sim$4.76 M$_\odot$."]
- limitation (authors): Cooler outer temperatures and missing flux beyond 2 arcsec can increase inferred outer masses and flatten the density profile. [Dust continuum, gas column density and …: "the averaged temperature over a larger area would likely be cooler"]
- limitation (authors): Several spectral components are blended, uncertain or unidentified. [Spectral features: "the CH$_3$CN $K$=0 and $K$=1 transitions are blended themselves."]
- limitation (authors): Inclination is not well constrained observationally. [Central YSO mass and the geometry of th…: "this angle in fact has not been very well constrained observationally."]
- not stated (card): CASA version and the observatory calibration script or pipeline version.; Calibrator identities, adopted flux models and flux-scale uncertainty; these are deferred to earlier papers.; Self-calibration solution intervals, phase/amplitude sequence, reference antenna, masks and acceptance criteria.; Continuum spectral windows, usable bandwidth and line-free channel selection.; Whether and how contin…

### 2012ApJ...757..129R: Kinematics of the CO Gas in the Inner Regions of the TW Hya Disk (2012; protoplanetary_disks; archival_reuse)
- question: What do the spatially and spectrally resolved 12CO J=2-1 and J=3-2 line wings from the TW Hya disk reveal about the temperature and kinematic structure of the inner disk?
- step 2: Fit fiducial model
  - method: Parametric viscous-disk model with LIME non-LTE radiative transfer, imaged through CASA; MPFIT chi2 minimization on visibilities then manual adjustment [3.2 The Failure of Standard Models: "utilized the modified Levenberg-Marquardt minimization algorithm `MPFIT` (cite: markwardt09) to help find parameters that produced a low $\chi^2$ in the spectral visibilities"]
  - software: LIME, MPFIT, CASA
  - parameter: PA fixed 151 deg; M*=0.8 Msun; inclination free; T10,q free per line [3.2 The Failure of Standard Models: "the major axis position angle was set to 151$^\circ$ (east of north)"]
  - assumption: vertically isothermal, mu=2.37, Keplerian, vr=vz=0 [3.1 Modeling Overview: "we implicitly assumed that the disk is vertically isothermal (at each radius)"]
  - fitting: MPFIT chi2 on visibilities, then manual tweaks; priors not stated [3.2 The Failure of Standard Models: "the model parameters were slightly adjusted manually to best reproduce the observed channel maps"]
  - validation: Compare model and data channel maps [3.2 The Failure of Standard Models: "The fiducial model is a good match to the ALMA data near the systemic velocity, but notably fails to reproduce the emission line wings"]
- step 4: Alternative models: hot inner disk, non-Keplerian, warp
  - method: Add radius-dependent temperature scaling, velocity scaling f(r), or inclination i(r); warp via quaternion rotation [3.3.3 A Disk Warp: "The velocity field is tilted using a quaternion transformation, as described in more detail in the Appendix."]
  - software: LIME, CASA
  - parameter: dT=3 inside r_hot=4 AU [3.3.1 A Hot Inner Disk: "scaling factor $\delta T = 3$ inside a radius $r_{\rm hot} = 4$ AU"]
  - parameter: non-Keplerian: r_b≈60 AU, x=0.15 [3.3.2 A Non-Keplerian Velocity Field: "Adopting $r_b \approx 60$ AU and $x = 0.15$ to describe $f$"]
  - parameter: warp: i0≈8 deg at r0=5 AU, y=0.15 [3.3.3 A Disk Warp: "with $i_0 \approx 8\ensuremath{^\circ}$ at $r_0 = 5$ AU and a gradient $y = 0.15$"]
  - assumption: vertically thin warped disk aligned with major axis [3.3.3 A Disk Warp: "aligned with the disk major axis (assuming a vertically thin disk; see the Appendix)"]
  - fitting: Qualitative, not optimized [3.3.2 A Non-Keplerian Velocity Field: "The {$r_b$, $x$} values adopted here are not unique (nor optimized)"]
  - validation: Compare channel maps and PV diagrams [3.3.1 A Hot Inner Disk: "as well as in position-velocity diagrams (constructed from a slice along the disk major axis)"]
- result: Hot model temperature scaling = 3 inside 4 AU ± not stated dimensionless [3.3.1 A Hot Inner Disk: "scaling factor $\delta T = 3$ inside a radius $r_{\rm hot} = 4$ AU"]
- result: Warp inclination gradient y = 0.15 ± not stated dimensionless [3.3.3 A Disk Warp: "a gradient $y = 0.15$"]
- result: Fiducial inclination = 5.8 ± not stated deg [Table 2: "$i_{10}$ | \[$^\circ$\] | 5.8 | 5.8 | 6.0 | 8.0 | 5.8"]
- limitation (authors): Model parameters are not unique nor optimized; limited resolution [3.3.3 A Disk Warp: "the warp model parameters we determine or even the formulation we adopt are not unique, nor optimized"]
- not stated (card): CLEAN threshold, polygon mask geometry, cell and image size; Exact line-free channels and polynomial order for continuum subtraction; LIME settings (number of grid points, photons) and CO abundance X_co value; Gas-to-dust ratio and dust properties details for RADMC-3D model; Exact MPFIT setup, initial values and how manual adjustments were made; Distance to TW Hya adopted

### 2014ApJ...793....1Y: ALMA Observations of Infalling Flows toward the Keplerian Disk around the Class I Protostar L1489 IRS (2014; star_formation, protoplanetary_disks; observational_alma_primary)
- question: How does infalling envelope gas connect to the Keplerian disk around the Class I protostar L1489 IRS, and what are the disk and infall properties?
- step 2: Fit thin Keplerian disk to high-velocity C18O
  - method: chi2 fitting of axisymmetric geometrically-thin LTE disk model to convolved channel maps, staged free parameters [Analysis: "we have built axisymmetric disk models with the geometrically-thin approximation, generated model C$^{18}$O images, and performed $\chi^2$ fitting to the observed channel maps of the high-velocity ($|V| \gtrsim 2.5$ km s$^{-1}$) C$^{18}$O emission."]
  - parameter: Fit region central 2''x2'', velocities -6.1 to -2.5 and 2.5 to 7.1 km/s; Rd fixed 200 AU [Analysis: "We select the central 2$\ensuremath{''}$ $\times$ 2$\ensuremath{''}$ region and the velocity ranges of $-$6.1 to $-$2.5 and 2.5 to 7.1 km s$^{-1}$"]
  - assumption: d=140 pc, LTE, X(C18O)=3e-7, Gaussian line profile [Analysis: "$d$ is the distance of 140 pc"]
  - fitting: Grid chi2 minimization with staged parameter sets; uncertainty from delta reduced chi2 = 1 with others fixed [Analysis: "we adopt the parameter range that gives a reduced $\chi^2$ of 1+$\chi^2_{\rm min}$ as the fitting uncertainty"]
  - validation: Tested different initial p and q; residuals mostly <=3 sigma [Analysis: "The levels of of residuals are all $\lesssim$4$\sigma$ and mostly $\lesssim$3$\sigma$"]
- step 5: Model infalling flows
  - method: Trace protrusion ridges, fit parabolic Ulrich trajectories with Rc=300 AU and free theta0, phi0; build infall+disk model and compare moment maps and P-V with Keplerian-protrusion alternative [Analysis: "we adopted the deprojected radius of these intensity peaks ($\sim$300 AU on the assumption the inclination angle of the disk plane $\sim$66$^\circ$) as the centrifugal radius of the infalling material"]
  - parameter: Initial solid angle theta0±3, phi0±3 deg; n1=3e7 cm-3; flow lengths 5000 AU (red), 2000 AU (blue) [Analysis: "both redshifted and blueshifted infall flows have an initial solid angle of $\theta_0\pm3\ensuremath{^\circ}$ and $\phi_0\pm3\ensuremath{^\circ}$, $n_1$ of 3 $\times$ 10$^{7}$ cm$^{-3}$"]
  - assumption: Gravity dominated by 1.6 Msun protostar, conserved angular momentum, zero total energy [Analysis: "On the assumption that the gravity is dominated by the central protostar, parabolic trajectories of infalling material are described as"]
  - fitting: Trajectory matched to measured ridge peak positions (not a formal fit) [Analysis, Non-Keplerian Components: Inf…: "searched for the best-fit trajectories that trace the measured peak positions (green filled squares in Figure [13](#infall)) and reproduce the curvatures of the protrusions."]
  - validation: Infall model reproduces protrusion velocity structure better than coplanar Keplerian model [Analysis: "Figure 16 shows that the velocity structures of the protrusions can be explained by the infalling model better than the Keplerian rotation model."]
- result: Protostellar mass = 1.6 ± 0.5 Msun [Table 1: "Protostellar Mass ($M_*$) | 1.6$\pm$0.5 $M_\ensuremath{\odot}$"]
- result: Inclination = 66 ± 10 deg [Table 1: "Inclination ($i$) | 66$\pm$10$\ensuremath{^\circ}$"]
- result: Systemic velocity = 7.3 ± 0.1 km/s [Table 1: "Systemic Velocity ($V_{\rm sys}$) | 7.3$\pm$0.1 km s$^{-1}$"]
- result: Disk position angle = 68 ± 18 deg [Table 1: "Position Angle ($\psi$) | 68$\pm$18$\ensuremath{^\circ}$"]
- result: Infall trajectory angles = theta0=52, phi0=74 (blue); theta0=124, phi0=262 (red) ± not stated deg [Analysis: "parabolic trajectory of material infalling from $\theta_0$ = 52$\ensuremath{^\circ}$ and $\phi_0$ = 74$\ensuremath{^\circ}$"]
- limitation (authors): Missing flux (~80% of C18O) hinders outer disk radius; p, q, T0, vturb poorly constrained [Analysis: "it is difficult to unambiguously constrain the outer radius of the Keplerian disk due to the effect of the missing flux ($\sim$80%; Hogerheijde et al. 1998)"]
- not stated (card): CLEAN threshold, mask, cell and image size, number of iterations; Line-free channels used for continuum and continuum subtraction; CASA version used; Exact channel width and velocity grid of imaged cubes; Whether the fit used a fixed beam-convolved model and the pixel/likelihood noise definition; Model grid details for infall flows (widths, n1 choice procedure); Whether primary beam correction ap…

### 2016ApJ...829....6W: ALMA Observations of HD 141569’s Circumstellar Disk (2016; debris_disks, protoplanetary_disks; observational_alma_primary)
- question: What are the dust and CO gas structure, kinematics and masses of the HD141569 disk, and is the gas primordial or second-generation (debris-related)?
- step 4: Fit Keplerian disk model to CO velocity field
  - method: Uniform Keplerian disk projected, convolved with beam, compared to first moment map in image domain [5.2 MCMC Modeling: "Model comparison is conducted in the image domain due to the high velocity resolution and signal-to-noise."]
  - software: custom MCMC code
  - parameter: 3 chains, 100 thousand links each, ~1000 burn-in; sigma = 0.5 km/s [5.2 MCMC Modeling: "Each chain contains 100 thousand links of which about 1000 are needed for burn-in."]
  - fitting: Metropolis-Hastings with Gibbs sampling; flat priors (Table 4); chi^2 likelihood; two parameters updated per trial [5.2 MCMC Modeling: "We assume flat prior distributions over the ranges given in Table [4](#mcmc_pri)."]
  - validation: 3 chains converge to similar parameters; model agrees with data to ~10% [5.2 MCMC Modeling: "The most probable model typically shows agreement with the data to about 10%"]
- result: Stellar mass (MCMC) = 2.39 ± 95% interval [2.34, 2.43] Msun [Table 5: "Mass \[M$_{\odot}$\] | $2.39$ | $[2.34,2.43]$"]
- result: Inclination (MCMC) = 53.4 ± 95% interval [52.5, 54.6] deg [Table 5: "Inclination \[$^{\circ}$\] | $53.4$ | $[52.5, 54.6]$"]
- result: Position angle (MCMC) = -3.36 ± 95% interval [-3.78, -2.71] deg [Table 5: "Position Angle \[$^{\circ}$\] | \-$3.36$ | $[-3.78,-2.71]$"]
- result: System velocity (LSRK) = 6.04 ± 95% interval [6.01, 6.06] km/s [Table 5: "System Velocity \[km s$^{-1}$\] | $6.04$ | $[6.01, 6.06]$"]
- result: M sin(i) = 1.92 ± 95% interval [1.89, 1.95] Msun [Table 5: "Mass \[M$_{\odot}$sin(i)\] | $1.92$ | $[1.89,1.95]$"]
- limitation (authors): CO mass assumes optically thin LTE and could be larger by a factor of a few or more [5.3 Gas Mass: "the actual CO gas mass could be larger by a factor of a few"]
- limitation (authors): Debris mass depends strongly on assumed size distribution, density, albedo [5.1 Debris/Dust Mass: "A steeper (shallower) solid size distribution can lead to significantly larger (smaller) masses."]
- not stated (card): CASA version; Number of clean iterations and mask used for CLEAN; image size and cell size; Which channels were treated as CO-free for the continuum and uvcontsub fit order; Velocity-axis reference/ rest frequency used for moment maps; moment-map clipping thresholds; uvmodelfit starting parameters; How the first moment map was sampled (pixels, masking) for chi^2 and how the model was projected; D…

### 2016A&A...596A..92K: ALMA observations of the nearby AGB star L<SUB>2</SUB> Puppis. I. Mass of the central star and detection of a candidate planet (2016; evolved_stars, exoplanets, stellar_physics; observational_alma_primary)
- question: What is the mass of the AGB star L2 Pup A from the Keplerian gas rotation, and is there a companion (source B) detected in continuum and CO emission?
- step 3: Fit Keplerian profile for central mass
  - method: Fit Keplerian velocity profile to inflection points between 2.5 and 4.5 AU; correct for inclination [3.2.2 Mass of the central object: "The yellow curve in Fig. [7](#29SiO-pvd) represents the best-fit Keplerian velocity profile to the inflection points, adjusted between radii of 2.5 and 4.5 AU."]
  - parameter: position uncertainty fixed at ±2.5 mas, velocity uncertainty ±0.5 km/s [3.2.2 Mass of the central object: "The radial position uncertainty in the point of inflection is fixed in the fit at $\pm 2.5$ mas (one reconstructed image pixel), and the velocity uncertainty to $\pm 0.5$ km s$^{-1}$."]
  - assumption: i = 82 ± 5 deg; parallax 15.61 mas; B mass not subtracted [3.2.2 Mass of the central object: "We therefore adopt a value of $i = 82 \pm 5^\circ$."]
  - fitting: Least-squares-type fit with fixed errors (sampler/likelihood not stated) [Analysis, Mass of the central object: "The radial position uncertainty in the point of inflection is fixed in the fit at $\pm 2.5$ mas (one reconstructed image pixel), and the velocity uncertainty to $\pm 0.5$ km s$^{-1}$."]
- step 4: Fit sub-Keplerian outer profile
  - method: Power law fit for 6<R<20 AU [3.3 Sub-Keplerian disk rotation: "The adjustment of a power law to the observed profile in the sub-Keplerian domain ($6 < R < 20$ AU)"]
- step 6: Mass of B from barycenter offset
  - method: Compare photocenter of A (2D Gaussian fit to continuum) with center of rotation G from matching east/west Keplerian velocities; m_B = d(Ph-G)/(d(BA)-d(Ph-G)) x m_A [4.2.1 Mass from molecular disk dynamics: "We measured the position of $G$ by matching the Keplerian velocities on each side of the PVD (east and west) of the $^{29}$SiO$(\varv=0,J=8-7)$ line"]
  - assumption: Only one companion besides star A [4.2.1 Mass from molecular disk dynamics: "We assumed in this reasoning that only one companion source is present in addition to the central star A."]
- step 7: Orbital radius and period of B
  - method: R_B from projected separation and sub-Keplerian projected velocity; Kepler's third law [4.2.2 Orbital period and radius: "Its orbital radius $R_B$ is necessarily larger than its currently observed radius $R_0$ from A"]
  - assumption: Circular orbit coplanar with the disk [4.2.2 Orbital period and radius: "We assumed that the orbit of B is circular and coplanar with the disk."]
  - validation: Consistent with astrometric displacement between ZIMPOL and ALMA epochs [4.2.2 Orbital period and radius: "this period is consistent with the small observed astrometric displacement of source B between the ZIMPOL (2014.93) and ALMA (2015.84) epochs"]
- result: Mass of L2 Pup A = 0.659 ± ±0.011 (stat) ±0.041 (parallax syst); ±0.043 combined (6.6%) Msun [abstract: "$m_A = 0.659\pm 0.011\pm 0.041\,M_\odot$ ($\pm 6.6\%$)"]
- result: m sin i within 2.5 AU = 0.653 ± ±0.011 ±0.041 Msun [3.2.2 Mass of the central object: "$$m_\mathrm{2.5\,AU} \sin(i) = 0.653\pm 0.011\pm 0.041\ M_\odot,$$"]
- result: Mass of B = 12 ± ±16 Mjup [4.2.1 Mass from molecular disk dynamics: "& = & 12\pm 16\,M_\mathrm{Jup}."]
- result: Orbital radius of B = 2.43 ± ±0.16 AU [4.2.2 Orbital period and radius: "$R_B = 2.43 \pm 0.16$ AU"]
- result: Orbital period of B = 4.69 ± ±0.45 yr [4.2.2 Orbital period and radius: "the orbital period is $P_\mathrm{orb} = 4.69 \pm 0.45$ years"]
- result: Sub-Keplerian velocity law, 6-20 AU = v = 40.7 R^-0.853 ± ±5.5 on amplitude, ±0.059 on index km/s (R in AU) [3.3 Sub-Keplerian disk rotation: "v = (40.7\pm 5.5) \times R^{(-0.853\pm 0.059)} \ \mathrm{km}\ \mathrm{s}^{-1}"]
- limitation (authors): Mass of B has no firm lower limit; assumes a single companion [Conclusion: "We emphasize, however, that the properties of source B are still uncertain as we do not have a firm lower limit on its mass."]
- limitation (authors): Extended slow envelope is resolved out by long baselines [Appendix 12CO line: "there exists an extended, slowly expanding, diffuse envelope that is resolved out by the long baselines of the interferometer"]
- not stated (card): Imaging task, deconvolver, clean threshold and masks; Robust/weighting used for line cubes; Line-free channels and continuum subtraction method for line cubes; Self-calibration solution intervals and number of iterations; Software and version used for calibration and imaging (CASA not named); Details of PVD derivative peak finding and Keplerian fit code; Which Hipparcos and photometric inputs wer…

### 2026A&A...705A.201B: The ALMA survey to Resolve exoKuiper belt Substructures (ARKS): VII. Optically thick gas with broad CO gaussian local line profiles in the HD 121617 disc (2026; debris_disks, astrochemistry; observational_alma_primary)
- question: Are the 12CO and 13CO lines in the HD 121617 debris disc optically thick, and what do local line profiles imply for CO mass, temperature and mean molecular weight
- step 2: Derive radial intensity profiles of CO and continuum
  - method: Gas profiles by stacking spectra in annuli assuming Keplerian rotation then integrating; continuum profile with frank [Observational results: "which divides the disc gas emission into annuli and spectrospatially stacks the spectra within each annulus, assuming a Keplerian rotation pattern for the disc"] [Observational results: "Then, we integrated over each annulus’s stacked spectrum to report integrated line intensity as a function of radius."]
  - software: gofish, frank
  - assumption: Keplerian rotation for stacking [Observational results: "assuming a Keplerian rotation pattern for the disc"]
- step 3: Fit Keplerian model to the 12CO velocity map
  - method: Velocity map from bettermoments Gaussian method (pixels below 5 sigma masked), fitted with a thin-disc Keplerian model for PA, inclination, stellar mass, systemic velocity, RA and Dec offsets [Observational results: "The velocity map was then produced using the Gaussian method, where a Gaussian is fitted to each pixel"] [Observational results: "where all pixels with peak intensities below 5$\sigma$ are masked"]
  - software: bettermoments, emcee
  - parameter: Distance fixed at 117.9 pc; 1500 steps, 32 walkers, 500 burn-in steps [Observational results: "We fixed the distance parameter to the known literature value of 117.9"] [Observational results: "for 1500 steps with 32 walkers after an additional burn-in period of 500 steps"]
  - assumption: Geometrically thin disc [Observational results: "assuming a geometrically thin disc"]
  - fitting: emcee affine-invariant ensemble sampler with uniform priors; likelihood not stated [Observational results: "We employed uniform priors with well-defined boundaries, ensuring they were sufficiently distanced from the best-fit values."]
  - validation: Compared with continuum geometry and stellar-model mass; convergence assessed visually [Observational results: "The PA, inclination, RA, and DEC offsets are consistent with those measured for the continuum"] [Observational results: "and visually assessed convergence"]
- step 4: Extract local line profiles in thin annuli
  - method: Align spectra across azimuth to the stellar peak velocity using the Keplerian cos(phi) dependence, then average within 0.02 arcsec annuli [4.1 Local line profile extraction: "We aligned the spectra across different azimuths to the same (stellar) peak velocity"] [4.1 Local line profile extraction: "Next, we averaged the aligned spectra to generate local spectral line profiles"]
  - software: eddy
  - parameter: Annulus width 0.02 arcsec; inclination, PA, RA and Dec offsets from the Keplerian fit (Table 2) [4.1 Local line profile extraction: "annuli of $0.02\ensuremath{''}$ width"] [4.1 Local line profile extraction: "We also adopted the inclination, PA, RA, and DEC-offset values from Table"]
  - assumption: Local line shape independent of azimuth, admitted not to hold in the data [4.1 Local line profile extraction: "this method assumes the local spectral line shape at a given radius is independent of azimuth, which is not the case in our dataset"]
  - validation: Profiles checked as function of azimuth before averaging; approximately Gaussian [4.1 Local line profile extraction: "The profiles are approximately Gaussian in shape, even before azimuthal averaging."]
- step 6: Optically thin RADMC-3D 12CO model compared qualitatively with data
  - method: Gaussian CO surface density (r_peak 73 au, sigma 21 au, fixed from radial profile), Gaussian vertical profile in hydrostatic equilibrium, Keplerian velocity; mu, Tpeak and MCO adjusted by hand against FWHM and peak-intensity azimuthal prof… [5.1.2 Data comparison: "Since we did not formally fit the cube, these parameters were adjusted to achieve the best qualitative agreement with key features of our dataset."] [5.1.1 Model assumptions: "We assumed a Gaussian vertical profile with a vertically constant temperature, as expected from hydrostatic equilibrium."]
  - software: RADMC-3D, emcee
  - parameter: Model cube 678 x 678 pixels of 0.0225 arcsec with 1182 channels of 13 m/s; spectral Gaussian FWHM = 2 x channel width; beam 0.12 x 0.11 arcsec [5.1.1 Model assumptions: "678 $\times$ 678 $0.0225\ensuremath{''}$ pixels with 1182 13 m s$^{-1}$ channels"]
  - parameter: Azimuthal sections of 15 deg for data; Gaussian fits with 2000 steps and 100 burn-in [5.1.2 Data comparison: "The fitting procedure consists of 2000 steps with a burn-in period of 100 steps due to faster convergence."]
  - assumption: LTE level populations; Keplerian rotation with 1.89 Msun [5.1.1 Model assumptions: "For simplicity, we assumed local thermodynamic equilibrium (LTE) to calculate the CO level populations."]
  - fitting: Qualitative adjustment of three parameters; Gaussian FWHM and peak intensity fitted per azimuth with MCMC [5.1.2 Data comparison: "We varied three parameters in our"]
  - validation: Model rejected as it needs unrealistically high temperature, cannot make the X-shape, and overestimates 13CO linewidths [5.1.2 Data comparison: "it requires unrealistically high temperatures, cannot account for the X-shape"]
- step 10: Analytical estimate of Keplerian shear broadening
  - method: Gradient of projected Keplerian velocity in sky coordinates multiplied by beam size; convolved with Gaussian of 26 m/s instrumental width to predict azimuthal FWHM [9 Keplerian shear: "evaluate this velocity difference by multiplying the gradient by the beam size in au"]
  - parameter: r_orb 73 au; M*, i, beam from HD 121617 ARKS data [9 Keplerian shear: "we fix $r_{\rm orb}$ to 73 au as in our peak intensity annulus of HD 121617"]
  - assumption: Vertically thin disc; gradient constant across the beam; Keplerian velocity field [9 Keplerian shear: "We assume that the disc is vertically thin (2D)"]
  - validation: Compared with data FWHM and RADMC-3D azimuthal pattern [9 Keplerian shear: "compares well with `RADMC-3D` models and ARKS observations of the HD 121617 system"]
- result: 12CO and 13CO radial detection extent = ~45 au to 125 au ± not stated au [Observational results: "are detected between $\sim$45 au and 125 au"]
- result: Radial intensity peaks (13CO, 12CO, continuum) = ~72, ~73, ~75 ± not stated au [Observational results: "The $^{13}\textrm{CO}$ emission peaks at $\sim$72 au, $^{12}\textrm{CO}$ at $\sim$73 au and the continuum at $\sim$75 au."]
- result: Position angle (12CO velocity map Keplerian fit) = 59.6 ± 0.01 deg [Table 2: "Position angle (deg) | 59.6 $\pm$ 0.01"]
- result: Inclination (Keplerian fit) = 43.8 ± 0.02 deg [Table 2: "Inclination (deg) | 43.8 $\pm$ 0.02"]
- result: Stellar mass (Keplerian fit) = 1.89 ± 0.001 Msun [Table 2: "Stellar mass (M$_{\odot}$) | 1.89 $\pm$ 0.001"]
- result: System velocity v_BARY (Keplerian fit) = 7860 ± 1 m/s [Table 2: "$v_{\textrm{BARY}}$ (m s$^{-1}$) | 7860 $\pm$ 1"]
- result: 12CO local line FWHM at 0.61-0.63 arcsec = ~1092 ± not stated m/s [4.1 Local line profile extraction: "displaying a full width half maximum (FWHM) of $\sim1092$ m s$^{-1}$"]
- result: Optically thin RADMC-3D model: peak optical depth, Tpeak, mu, CO mass = ~0.11; 380 K; 28; 1e-3 Mearth ± not stated dimensionless; K; dimensionless; Mearth [5.1.2 Data comparison: "We find that an optically thin model with a peak optical depth of $\sim$0.11, $T_{\rm peak} = 380$ K, $\mu = 28$ (CO dominated), and $M_{\rm CO} = 10^{-3}$ M$_{\oplus}$ reproduces many key features of the data."]
- result: Keplerian shear line broadening (analytic) = ~300-700 ± not stated m/s [9 Keplerian shear: "we find Keplerian shear should produce broadening of $\sim300-700$ m s$^{-1}$"]
- limitation (authors): Keplerian fit uncertainties likely underestimated [Table 2: "We note that these uncertainties are likely underestimated."]
- limitation (authors): Mu and 13CO mass depend on the LTE assumption and radial and vertical model choices [5.2.1 13CO RADMC-3D model: "we caution that its derivation is critically dependent on our LTE assumption"]
- limitation (authors): Different total CO masses or abundance ratios may fit equally well given high optical depth [5.2.2 12CO RADMC-3D model: "We, however, caution that different total CO masses/abundance ratios may also fit the data, given the high optical depth of both isotopologues."]
- not stated (card): Which of the 11 listed ALMA projects were actually used for the analysis (only 2022.1.00338.L is described); Line-free channels and continuum subtraction method for the CO cubes; tclean cell size, image size, deconvolver, masks and cleaning threshold for the CO cubes; Velocity-resampling and channel width of the delivered cubes beyond the 26 and 884 m/s resolutions; Time on source, baseline range…

### 2020MNRAS.498.1319M: Insights into the planetary dynamics of HD 206893 with ALMA (2020; debris_disks, exoplanets; observational_alma_primary)
- question: What is the radial structure of the HD 206893 debris disc (is there a gap, asymmetry, CO gas, dust around the brown dwarf B), and what does it imply for the dynamics of the companions?
- step 5: Search for CO emission and derive CO mass and ice fraction limits
  - method: Continuum-subtract, image cubes with tclean, apply a Keplerian mask (both rotation senses), integrate within deprojected radius of 150 au, convert flux limits to CO mass with a non-LTE tool, then to CO+CO2 ice fraction [2.2 CO gas emission: "we applied a Keplerian mask as in (cite: Matra2015; Marino2016; Matra2017fomalhaut)"] [2.2 CO gas emission: "After integrating the emission within a deprojected radius of 150 au"]
  - software: CASA tclean, CO mass tool of Matra et al. 2018
  - parameter: Band 7 cubes 0.43 km/s channels (1.1 km/s effective); Band 6 cubes 1.3 km/s channels (2.0 km/s effective) [2.2 CO gas emission: "This produces data cubes with channel widths of 0.43 km s$^{-1}$(effective bandwidth of 1.1 km s$^{-1}$due to Hanning smoothing) in band 7"] [2.2 CO gas emission: "1.3 km s$^{-1}$(effective resolution of 2.0 km s$^{-1}$due to Hanning smoothing and averaging every 2 channels) in band 6"]
  - parameter: Kinetic temperatures 20 to 200 K [2.2 CO gas emission: "a range of kinetic temperatues from 20 to 200 K"]
  - assumption: Optically thin CO emission, non-LTE excitation [2.2 CO gas emission: "These CO flux upper limits can be translated to CO masses assuming optically thin emission."]
  - assumption: Fractional luminosity ~3e-4, stellar mass 1.3 Msun, luminosity 2.9 Lsun, disc radius 70 au and width 100 au, photodissociation timescale 120 yr [2.2 CO gas emission: "the fractional luminosity of the system ($\sim3\times10^{-4}$)"] [2.2 CO gas emission: "disc radius and width (approximately 70 and 100 au)"]
  - validation: Both rotation directions tested; no significant emission recovered [2.2 CO gas emission: "assuming a disc orientation (derived in §[3](#sec:parmodel)) and sense of rotation— we test both possible directions"]
- result: CO J=3-2 3 sigma line flux upper limit = 66 ± not stated mJy km/s [2.2 CO gas emission: "we estimate 3$\sigma$ upper limits for the line fluxes of 66 mJy km s$^{-1}$for J=3-2 and 12 mJy km s$^{-1}$ for J=2-1"]
- result: CO J=2-1 3 sigma line flux upper limit = 12 ± not stated mJy km/s [2.2 CO gas emission: "we estimate 3$\sigma$ upper limits for the line fluxes of 66 mJy km s$^{-1}$for J=3-2 and 12 mJy km s$^{-1}$ for J=2-1"]
- result: CO mass upper limit (from J=2-1) = 2.4e-6 ± not stated Earth masses [2.2 CO gas emission: "with an upper limit of $2.4\times10^{-6}$ M$_\oplus$"]
- result: Upper limit on CO+CO2 mass fraction in planetesimals = 9 ± not stated percent [2.2 CO gas emission: "we find an upper limit of 9% for the fractional mass of CO+CO$_2$ in planetesimals"]
- limitation (authors): Planet mass assumes the gap is empty at its centre; a shallower, broader gap would change the inferred width and mass [3.1 Results: "A caveat in this interpretation is that we have assumed the gap is empty at its center."]
- limitation (authors): Frankenstein profiles lack a primary beam correction [2.1.1 Dust radial structure: "no primary beam correction is taken into account"]
- limitation (authors): Lower S/N makes gap width and depth comparison with other discs difficult [5.4 Are gaps common among exoKuiper bel…: "Given the lower S/N in HD 206893 observations, it is hard to compare the gap width and depth with the other two."]
- not stated (card): tclean parameters other than weighting and taper: deconvolver, cell size, image size, mask, threshold, niter; How the ACA and 12m data were combined for imaging and for the visibility fit (joint tclean or separate datasets); Which spectral windows were used for the continuum images, and whether the line window was flagged; Flux calibrator and calibrator-derived flux scale for each execution block…

### 2017ApJ...850L...5T: The Second Galactic Center Black Hole? A Possible Detection of Ionized Gas Orbiting around an IMBH Embedded in the Galactic Center IRS13E Complex (2017; milky_way_ism, star_formation; observational_alma_primary)
- question: Does the IRS13E complex near Sgr A* contain an intermediate mass black hole, tested by searching for compact, wide-velocity-width ionized gas in H30alpha with ALMA
- step 3: Estimate enclosed mass from Keplerian eccentric orbit
  - method: Compare PV shape with calculated Keplerian orbits to get a and e; mass from M ~ a dV^2 (...)^-2 / G [The Enclosed Mass of IRS13E3: "The observed velocity width is $\Delta V\sim 600$ km s$^{-1}$, and the enclosed mass of the object is estimated to be $M\sim4-7\times10^{4}$ M$_\odot$"]
  - parameter: a~1.4e17 cm, e=0.96-0.98, dV~600 km/s [The Enclosed Mass of IRS13E3: "for $e=0.96-0.98$ and $a\sim1.4\times10^{17}$ cm"]
  - assumption: inclination i~0 deg (edge-on orbit); apoastron PA~60 deg to line of sight [Keplerian Orbit with High Eccentricity …: "The inclination angle of the orbit would be $i\sim0^\circ$"]
  - validation: Consistency with VLBA upper limit on second black hole mass [The Enclosed Mass of IRS13E3: "there is no conflict between our derived enclosed mass and the upper limit mass of the second black hole"]
- result: Enclosed mass = 4-7e4 ± not stated Msun [The Enclosed Mass of IRS13E3: "$M\sim4-7\times10^{4}$ M$_\odot$, comparable to the mass of an IMBH, for $e=0.96-0.98$"]
- result: Orbital eccentricity = ~0.97 ± not stated dimensionless [Keplerian Orbit with High Eccentricity …: "the eccentricity of the orbit is estimated to be $e\sim0.97$"]
- result: Semi-major axis = 1.4e17 cm (1e4 AU) ± not stated cm [Keplerian Orbit with High Eccentricity …: "the semi-major axis of the orbit is estimated to be $a\sim1.4\times10^{17}$ cm $=1\times10^4$ AU"]
- limitation (authors): Orbital parameters cannot be uniquely determined from the PV diagram [Keplerian Orbit with High Eccentricity …: "it is difficult to determine exclusively the accurate orbital parameters by fitting in the position velocity diagram"]
- not stated (card): Image size, cell size and channel width/line-free channels for H30a cube and continuum fit; Self-calibration solution intervals and reference datasets; Number of tclean iterations and thresholds; Flux scale uncertainty; Pipeline vs manual calibration and CASA version for calibration; Orbit model details: how e=0.97 was chosen from PV comparison, and the 650 vs 600 km/s velocity width definition; …

### 2024A&A...692A.151S: Uncovering the structure and kinematics of the ionized core of M 2-9 with ALMA (2024; evolved_stars; observational_alma_primary)
- question: What are the structure, kinematics and physical conditions of the nascent compact ionized core (wind/jet) of the pPN/yPN candidate M 2-9, probed at 1 and 3 mm continuum and the H30alpha and H39alpha mRRLs down to ~0.03 arcsec?
- step 4: model the ionized wind with non-LTE 3D radiative transfer
  - method: forward modeling of continuum and H30alpha/H39alpha cubes with Co3RaL, starting from the CSC17 model and adjusting parameters by hand to match the ALMA maps, PV diagrams and SED [Non-LTE radiative transfer modeling of …: "To obtain an improved model that fits these new details, we progressively adjusted the parameters of the input model"]
  - software: Co3RaL
  - parameter: Te ~ 15000 K, constant [Non-LTE radiative transfer modeling of …: "The value deduced $T_{\rm e}$$\sim$15000 K"]
  - parameter: inclination i = 12 deg (models around 17 deg examined) [Non-LTE radiative transfer modeling of …: "with the most successful models having an inclination of $i$=12$^\circ$"]
  - parameter: R_out ~ 40 au, R_eq ~ 8 au [Non-LTE radiative transfer modeling of …: "a much narrower bipolar structure (particularly an outer radius value of $R_{\rm out}$$\sim$40 au)"] [Non-LTE radiative transfer modeling of …: "a narrow waist at the base of the wind ($R_{\rm eq}$$\sim$8 au)"]
  - parameter: high-velocity shells: velocity rises from ~70 to ~90 km/s; ~10 km/s inside ~15 au [Non-LTE radiative transfer modeling of …: "within the HVSs, the velocity rises from $\sim$70 to $\sim$90 km s$^{-1}$"]
  - assumption: constant electron temperature across the wind [Non-LTE radiative transfer modeling of …: "To simplify, we maintain a constant value for the electron temperature throughout the various regions of the wind."]
  - assumption: distance 650 pc [M 2-9: "In this study, we adopt a distance of 650 pc for M 2-9"]
  - assumption: constant rotation velocity because resolution cannot distinguish Keplerian from momentum-conserving profiles [Non-LTE radiative transfer modeling of …: "Since the angular resolution of the data does not allow us to distinguish between Keplerian or momentum conservation velocity profiles"]
  - fitting: manual iterative adjustment; no sampler, priors or likelihood [Non-LTE radiative transfer modeling of …: "until a reasonable match was achieved between the model predictions and the data"]
  - validation: Co3RaL benchmarked against MORELI with identical inputs; the authors state no comprehensive parameter-space study was done [Comparison of Co3RaL with MORELI: "This comparison serves as a mutual benchmarking exercise of both codes."] [Model caveats and final modeling remarks: "Although a comprehensive parameter space study has not been performed and is beyond the scope of this paper"]
- result: Electron temperature of the ionized wind (model) = ~15000 ± ~15-20% K [Non-LTE radiative transfer modeling of …: "The value deduced $T_{\rm e}$$\sim$15000 K"]
- result: Ionized mass of the model wind = ~4e-6 ± factor <~2-3 Msun [Non-LTE radiative transfer modeling of …: "$M_{\rm ion}$$\sim$4$\times 10^{\rm -6}$ $M_{\odot}$"]
- result: Average mass-loss rate of the ionized wind (model) = ~7e-7 ± factor <~2-3 Msun/yr [Non-LTE radiative transfer modeling of …: "the average mass-loss rate implied from the model is $\dot{M}$$\sim$7$\times 10^{\rm -7}$ $M_{\odot}$ yr$^{-1}$"]
- result: Model wind inclination = 12 ± not stated deg [Non-LTE radiative transfer modeling of …: "with the most successful models having an inclination of $i$=12$^\circ$"]
- result: Model wind outer radius and equatorial radius = R_out ~40 au; R_eq ~8 au ± not stated au [Non-LTE radiative transfer modeling of …: "a much narrower bipolar structure (particularly an outer radius value of $R_{\rm out}$$\sim$40 au)"]
- result: Velocity in the high-velocity shells = rises from ~70 to ~90 ± not stated km/s [Non-LTE radiative transfer modeling of …: "within the HVSs, the velocity rises from $\sim$70 to $\sim$90 km s$^{-1}$"]
- limitation (authors): Model is probably not unique; more complex geometries and profiles cannot be dismissed [Model caveats and final modeling remarks: "is probably not unique and that more intricate geometries, kinematics, and density and temperature profiles (e.g. latitude-dependent) cannot be dismissed as possibilities."]
- limitation (authors): Model fails to reproduce the H30alpha profile asymmetry [Model caveats and final modeling remarks: "One shortcoming of our model is its failure to predict the asymmetry in the"]
- not stated (card): GILDAS MAPPING parameters: cell size, image size, clean mask, number of iterations or threshold, uv-range and what robust threshold 0.5 means numerically; Self-calibration details: solution intervals, number of iterations, amplitude versus phase, and the initial model used; Line-free channel ranges per SPW and the order or degree of continuum subtraction; Which execution blocks, MOUS and SPWs bel…

### 2013ApJ...776...77K: ALMA Observations of the Molecular Gas in the Debris Disk of the 30 Myr Old Star HD 21997 (2013; debris_disks, protoplanetary_disks; observational_alma_primary)
- question: What are the physical state, origin and evolutionary status of the molecular gas in the 30 Myr old HD 21997 debris disk, and is it co-located with the dust?
- step 4: Fit Keplerian disk model to 12CO(2-1) cube
  - method: Grid of 104,448 models with 5 parameters, Keplerian, convolved with beam; chi2 max over channels; Bayesian probability exp(-chi2/2) marginalized [3.4 Distribution of the CO Gas: "In total, we calculated 104,448 models."]
  - parameter: M* 0.9-3.0 Msun step 0.3; rin 5-60 AU; rout 95-175 AU; i 25-39 deg step 2; p 0 to -1.75 step 0.25 [3.4 Distribution of the CO Gas: "$r_{\rm in}$ between 5 AU and 60 AU in steps of 5 AU, $r_{\rm out}$ between 95 AU and 175 AU in steps of 5 AU"]
  - parameter: Intrinsic line width 0.1 km/s; 2-channel Hanning smoothing; 6x spatial oversampling [3.4 Distribution of the CO Gas: "We used an intrinsic line width of 0.1 km s$^{-1}$"]
  - assumption: Keplerian rotation, power-law brightness I(r)~r^p, models normalized to observed total intensity [3.4 Distribution of the CO Gas: "we normalized the models so that the total intensity equaled the observed total intensity"]
  - fitting: Uniform grid, flat priors implied; 1D marginal maximum with 68% integrals; inclination from best-fit stellar mass due to degeneracy [3.4 Distribution of the CO Gas: "The inclination and the stellar mass are degenerate, thus we did not determine the inclination from the Bayesian probabilities"]
  - validation: Model reproduces all five lines; outer radius, inclination, stellar mass consistent with independent estimates [3.4 Distribution of the CO Gas: "This fact demonstrates that a single disk model with one set of parameters reproduces all five CO lines."]
- result: Disk outer radius = 138 ± ±20 AU [Table 1: "| Disk outer radius | $r_{\rm out}$ (AU) | $138\pm20$ |"]
- result: Stellar mass = 1.8 ± +0.5/-0.2 Msun [Table 1: "| Stellar mass | $M_*$ ($M_{\odot}$) | $1.8^{+0.5}_{-0.2}$ |"]
- result: Inclination = 32.6 ± ±3.1 deg [Table 1: "| Disk inclination | $i$ ($^{\circ}$) | $32.6 \pm 3.1$ |"]
- result: Inner radius = <26 ± 1 sigma upper limit AU [Table 1: "| Disk inner radius | $r_{\rm in}$ (AU) | $< 26$ |"]
- limitation (authors): Inner radius only an upper limit; brightness exponent ill-determined; full radiative transfer model postponed [3.4 Distribution of the CO Gas: "A more detailed physical model, taking into account the vertical disk structure and full radiative transfer, is postponed to our forthcoming paper."]
- not stated (card): robust value, cell size, image size, clean mask and threshold; CASA version and whether calibration used the archive scripts; line-free channels used for uvcontsub; number of flagged data/antennas; aperture/moment-map thresholds; CO excitation/radiative transfer code used for mass; model code for the disk grid not released

### 2022MNRAS.510.2363H: Morpho-kinematics of the wind of asymptotic giant branch star L<SUB>2</SUB> Pup (2022; evolved_stars; archival_reuse)
- question: What is the morpho-kinematics of the wind escaping the gravity of the AGB star L2 Pup, including line broadening in the nascent wind near the star and the presence of predicted collimated radial outflows?
- step 3: Evaluate high Doppler velocity wings, line broadening near the star, and inner disc rotation velocities
  - method: Scan line profiles along x = 0 in steps of y = 10 mas (0.64 au) and evaluate the velocity V_{z,20} at which 20% of the maximal flux density is reached on the blue side; compute mean Doppler velocity averaged over R in successive rings (30-… [High Doppler velocity wings: "Figure 7 illustrates the evolution of the line profile when scanning along this line in steps of $y$$=$10 mas (0.64 au)."] [High Doppler velocity wings: "Yet, to be free of the effect of the strong red-side absorption, we evaluate its evolution from the value $V_{z,20}$ of $V_z$ at which 20% of the maximal flux density is reached on the blue side."]
  - parameter: Scan step y = 10 mas (0.64 au) along x = 0; V_{z,20} at 20% of max flux density on blue side; ring intervals 30-60, 60-90, 90-120, 120-150 mas; |V_z| < 20 km s^-1 [High Doppler velocity wings: "Figure 7 illustrates the evolution of the line profile when scanning along this line in steps of $y$$=$10 mas (0.64 au)."] [High Doppler velocity wings: "To illustrate this point we show in Figure 9 the dependence on position angle of the mean Doppler velocity, averaged over $R$ in successive rings and integrated over $|V_z|$$<$20 km s$^{-1}$."]
  - assumption: Gaussian line profile approximation to convert V_{z,20} to effective FWHM line width [High Doppler velocity wings: "In the approximation of Gaussian line profiles, we estimate that the effective line width (FWHM) remains below 10 km s$^{-1}$down to projected distances of $\sim$4 au and then increases linearly to reach $\sim$20 km s$^{-1}$ near the surface of the star."]
  - fitting: Sinusoidal fit of mean Doppler velocity vs position angle (parameters A, B, omega_0 in Table 2) [Table 2: "| $A$ (km s$^{-1}$) | $B$ (km s$^{-1}$) | $\omega_0$ (degrees) |"]
  - validation: Checked consistency with red-side evaluation and with a scan made at y = 0 in small steps of x; estimated +-1 km s^-1 uncertainties from different evaluation methods of V_{z,20}. [High Doppler velocity wings: "Uncertainties at the scale of $\pm$1 km s$^{-1}$are estimated from the results obtained using different methods to evaluate the values of $V_{z,20}$."] [High Doppler velocity wings: "We have checked that this evaluation is consistent with the results obtained on the red side and with a scan made at $y$$=$0 in small steps of $x$ (Figure 8)."]
- result: Radius of inner line broadening region = 4 ± not stated au [High Doppler velocity wings: "In summary, in spite of being qualitative, this analysis has shown reliably that significant line broadening is observed at projected distances from the star below $\sim$4 au and is absent above."]
- result: Effective line width (FWHM) of 13CO(3-2) beyond 4 au = 5 ± not stated km s^-1 [High Doppler velocity wings: "The values obtained for $^{13}$CO (right panel of Figure 8) are less affected by absorption and are $\sim$5 km s$^{-1}$ and $\sim$20 km s$^{-1}$, respectively ."]
- result: Effective line width (FWHM) near the surface of the star = 20 ± not stated km s^-1 [High Doppler velocity wings: "In the approximation of Gaussian line profiles, we estimate that the effective line width (FWHM) remains below 10 km s$^{-1}$down to projected distances of $\sim$4 au and then increases linearly to reach $\sim$20 km s$^{-1}$ near the surface of the star."]
- result: Rotation velocity amplitude B in inner ring (30 < R < 60 mas) for 12CO(3-2) = -8.2 ± not stated km s^-1 [Table 2: "| 30-60 | $-$0.2 | $-$0.2 | $-$0.5 | $-$8.2 | $-$7.0 | $-$8.4 | 1 | 1 | 2 |"]
- result: Rotation velocity amplitude B in inner ring (30 < R < 60 mas) for 13CO(3-2) = -7.0 ± not stated km s^-1 [Table 2: "| 30-60 | $-$0.2 | $-$0.2 | $-$0.5 | $-$8.2 | $-$7.0 | $-$8.4 | 1 | 1 | 2 |"]
- result: Rotation velocity amplitude B in inner ring (30 < R < 60 mas) for 29SiO(8-7) = -8.4 ± not stated km s^-1 [Table 2: "| 30-60 | $-$0.2 | $-$0.2 | $-$0.5 | $-$8.2 | $-$7.0 | $-$8.4 | 1 | 1 | 2 |"]
- limitation (authors): In the first set of observations (Band 7), sparse and uneven baselines < 500 m limit reliable imaging to R < ~0.2 arcsec and cause an isotropic wind to artificially appear as north-south emission beyond R ~ 0.15 arcsec. [Overall picture: "Baselines smaller than 500 m are sparse and unevenly distributed, limiting the range of reliable imaging to projected distances from the star $R$$<$$\sim$0.2 arcsec."]
- limitation (authors): The parameterization of the emission in phase opposition to the dominant sine wave in terms of two weaker sine waves with eye-estimated parameters is somewhat arbitrary. [The wind of L$_2$ Pup: "All these parameters have been estimated by eye to approximately match the data."]
- limitation (authors): The inclination angle i of the large-scale expanding wind disc is unknown, making the retained range of 40+-20 deg and the resulting mass loss rate estimate crude and dependent on somewhat arbitrary arguments. [The wind of L$_2$ Pup: "Yet, too thin a disc would be highly improbable in the CSE of an AGB star and we retain as a reasonable range of acceptable values of $i$ the interval [20$^\circ$,60$^\circ$], which we write as 40$^\circ$$\pm$20$^\circ$, it being understood that this estimate rests on sensible but somewhat arbitrary arguments."]
- not stated (card): Software versions for both CASA and GILDAS; Deconvolution stopping criteria (threshold, niter) and masking strategies used in CASA and GILDAS cleaning; Image dimensions (number of pixels) for both Band 6 and Band 7 cubes; Exact details of the self-calibration or calibration procedures inherited from Kervella et al. (2016) and Homan et al. (2017); Exact density and velocity profile assumed for the…

### 2024ApJ...970...74P: The Evaporating Massive Embedded Stellar Cluster IRS 13 Close to Sgr A*. II. Kinematic Structure (2024; stellar_physics, star_formation, milky_way_ism; multi_facility_alma_minor)
- question: Kinematic structure and inspiral of IRS 13; whether H30α gas kinematics and the E3 broadband SED support an IMBH
- step 3: Fit stellar orbits and local uncertainties
  - method: Keplerian fits with SLSQP; select minimized reduced χ² solutions; MCMC uncertainties [Keplerian fit: "We use the Sequential Least Squares Programming (SLSQP) method to estimate a Keplerian solution"] [Cluster analysis: "we select the orbits with the highest probability given by the minimized reduced $\chi ^2$"]
  - parameter: E-stars, DS sources, and Greek-named sources; exclude ι and ϑ because of blending [Orbits: "For the Keplerian orbits, we select all E-stars (seven sources) and the DS sources (33 sources)"] [Orbits: "In addition to crowding effects, $\iota$ and $\vartheta$ are blended with nearby sources that hinder a confusion-free analysis."]
  - assumption: All fitted sources bound to Sgr A*; black-hole mass 4.02 × 10^6 M⊙ [Orbits: "we assume that all the sources are gravitationally bound to Sgr A\*"] [Orbits: "adopt the mass of 4.02$\,\times\,10^{6}$M$_{\odot}$ for the supermassive black hole (cite: eht2022; Peissker2022)."]
  - fitting: SLSQP minimizes reduced χ²; MCMC uses listed Keplerian elements as a prior [Keplerian fit: "The SLSQP method calculates the reduced $\chi ^2$ and aims to minimize/optimize the distance between the calculated fit and the input positions (cite: Kraft1988)."] [MCMC simulations: "we present the MCMC simulations using the Keplerian elements"]
  - validation: Compare alternative orbit solutions and inspect eccentricity–semi-major-axis parameter space [Orbits: "we selected another Keplerian solution with an increased $\chi^2$ indicating a statistically poor solution for the given data set."] [Parameter space of the eccentricity and…: "we want to complete this discussion by inspecting possible values for the eccentricity e and the semi-major axis a."]
- limitation (authors): Stellar Keplerian solutions lack individual radial velocities [Limitations of the analysis: "The Keplerian solutions for the projected on-sky positions of the investigated sources lack radial velocities."]
- limitation (authors): Some stellar orbits have less than 2% coverage [Orbits: "the orbital data coverage is less than 2$\%$ for some of the cluster members."]
- limitation (authors): Multiple orbital solutions are acceptable; quoted uncertainty ranges describe local solutions [Cluster analysis: "multiple orbital solutions with comparable probabilities are acceptable."]
- not stated (card): ALMA execution blocks, spectral windows, H30α rest frequency, channel width, and velocity reference frame.; ALMA calibration software/version, flagging, calibrators, and flux-scale uncertainty; reduction is deferred to Paper I.; Whether the ALMA inputs were raw visibilities, calibrated visibilities, or existing image products.; ALMA imaging weighting/robust value, beam, pixel size, masks, continu…

### 2013PASJ...65..100I: Submillimeter ALMA Observations of the Dense Gas in the Low-Luminosity Type-1 Active Nucleus of NGC1097 (2013; nearby_galaxies, astrochemistry, agn_and_quasars; observational_alma_primary)
- question: What are the characteristics of the dense gas around the low-luminosity type-1 AGN of NGC 1097, and what mechanism causes the HCN enhancement?
- step 4: Estimate dynamical mass
  - method: Keplerian thin-disk M_dyn = r v^2/G (sin i)^-2 at r~40 pc [6 Dense molecular gas kinematics: "Assuming a thin disk with Keplerian rotation, the dynamical mass within a radius $r$ is calculated as"]
  - parameter: r ~ 40 pc; i = 35 deg [6 Dense molecular gas kinematics: "we set the radius to $r$ $\sim$ 40 pc, and we adopt an inclination angle of 35$^\circ$ (Fathi et al. 2006)"]
  - assumption: Keplerian rotation, thin disk; lower limit due to beam smearing [6 Dense molecular gas kinematics: "the dynamical mass estimated here is just an lower limit because the rotation velocity may be underestimated due to the beam smearing effect"]
  - validation: Compared with previous dynamical masses (Davies 2007, Hicks 2009) [6 Dense molecular gas kinematics: "This value is within a factor of a few of previous measurements of the dynamical mass of 1.4 $\times$ 10$^8$ $M_{\rm \odot}$"]
- result: Dynamical mass within 40 pc = 2.8e8 ± not stated Msun [6 Dense molecular gas kinematics: "the enclosed dynamical mass within 40 pc is estimated to be $M_{\rm{dyn}}$ $\sim$ $2.8 \times 10^8 M_{\rm{\odot}}$"]
- limitation (authors): Dynamical mass is simple Keplerian estimate and lower limit [6 Dense molecular gas kinematics: "Note that the estimation we present in this section is based on the simple assumptions of Keplerian rotation."]
- limitation (authors): Submm-HCN diagram is tentative, few samples [7.2 Molecular line diagnostics: "this is a tentative view as we do not have clear theoretical evidence to support the use of this diagram, and it is based on few samples"]
- not stated (card): Calibration steps/CASA version and calibrator flux values; Line-free channels used for continuum; CLEAN threshold, image size, and primary beam correction details; Exact moment-map clipping thresholds in MIRIAD and region definitions; Band 3 J=1-0 and SMA J=3-2 maps (not public in paper) for LTE/non-LTE analysis; Observed intensities uncertainty treatment in the chi2 (weights); RADEX script detai…

### 2021AJ....162...14A: Precision Millimeter Astrometry of the α Centauri AB System (2021; exoplanets, stellar_physics; observational_alma_primary)
- question: Can ALMA Band 7 astrometry of alpha Cen A and B give precise absolute and differential positions to refine the orbit, masses, parallax and proper motion, and ultimately to search for planets in the AB system
- step 6: fit orbit from RV plus differential astrometry
  - method: Keplerian two-body model fit for epoch 2019.5 to RVs and differential astrometry, with perspective and light-time corrections applied in a second fitting round [3.2.3 Orbital and proper motion fit pro…: "We first determined the orbital parameters (Keplerian orbital elements, dynamical parallax, total mass of the system, and mass ratio) for epoch 2019.5 based only on the RV and differential astrometry data and a simple Keplerian two-body model."] [3.2.3 Orbital and proper motion fit pro…: "We then computed a second round of orbital and proper motion fitting on these corrected observations"]
  - software: SciPy scipy.optimize.leastsq, Astropy SkyCoord
  - parameter: 2 m/s uniform jitter added in quadrature to RVs; RVs with sigma > 10 m/s rejected; 5 sigma clipping (0.9% of A, 1.0% of B) [3.2.2 Radial Velocity Data: "Therefore we added in quadrature a uniform uncertainty of 2 m s$^{-1}$ to all measurements."] [3.2.2 Radial Velocity Data: "filtered out the RV measurements whose uncertainty is larger than 10 m s$^{-1}$, and cleaned the strongest outliers with a $5\sigma$ clipping with respect to the best fit preliminary solution."]
  - assumption: reference epoch 2019.5 chosen to match the majority of the ALMA data; second-order effects treated as linear perturbations [3.2.3 Orbital and proper motion fit pro…: "This reference time was arbitrarily chosen to correspond to the majority of our ALMA measurements"]
  - assumption: intrinsic RV shift of A taken as zero [3.2.2 Radial Velocity Data: "whose intrinsic shift is assumed to be zero"]
  - fitting: Levenberg-Marquardt least squares on the full data set (scipy.optimize.leastsq); uncertainties normalised to data dispersion [3.2.3 Orbital and proper motion fit pro…: "using a classical multi-parameter Levenberg-Marquardt least-squares fitting algorithm on the complete data set."]
  - validation: reduced chi2 of 1.2; a third iteration did not change the parameters; adopting Trifonov RV shift gave no significant change [3.3 Orbital parameters, masses and bary…: "We obtain a satisfactory reduced $\chi^2$ for the best fit orbit model of 1.2."] [3.2.3 Orbital and proper motion fit pro…: "We checked that a third iteration of fitting did not result in a significant change of the derived parameters."]
- result: semi-major axis of the AB orbit = 17.4930 ± 0.0096 arcsec [Table 8: "$17.4930 \pm 0.0096$"]
- result: orbital period = 79.762 ± 0.019 yr [Table 8: "$79.762 \pm 0.019$"]
- result: orbital eccentricity = 0.51947 ± 0.00015 dimensionless [Table 8: "$0.51947 \pm 0.00015$"]
- result: orbital inclination = 79.2430 ± 0.0089 deg [Table 8: "$79.2430 \pm 0.0089$"]
- result: orbital parallax = 750.81 ± 0.38 mas [3.3 Orbital parameters, masses and bary…: "orbital parallax ($\varpi_\mathrm{orb} =750.81 \pm 0.38$ mas)"]
- result: distance to alpha Cen AB = 1.3319 ± 0.0007 pc [3.4 Prospects for Improved Stellar Prop…: "The parallax determined in the present work ($\varpi = 750.81$ mas, $d=1.3319 \pm 0.0007$ pc)"]
- result: perspective RV acceleration = +0.421 ± not stated m/s/yr [3.2.3 Orbital and proper motion fit pro…: "The RV geometrically increases with an acceleration of $\dot{V} = +0.421$ m s$^{-1}$yr$^{-1}$"]
- limitation (authors): absolute flux scale 10-15% uncertain because no primary flux standard observed [2.2 Data Reduction: "no primary flux calibration standards were observed, thus the absolute calibration uncertainty is 10-15"]
- limitation (authors): one October 2018 observation had a 20 mas offset attributed to a tracking error and was dropped [2.2.1 Absolute Astrometry: "believe it was caused by an error in the ALMA celestial position tracking system of"]
- limitation (authors): trigonometric parallax is poorly constrained by the few absolute points [3.3 Orbital parameters, masses and bary…: "due to relatively poor phase coverage of the parallactic ellipse because of our limited number of absolute measurements"]
- not stated (card): CASA version and whether the standard ALMA pipeline or manual calibration was used (no version given); tclean deconvolver, niter, threshold, masks and uv range; the CLEAN settings beyond weighting, cell and image size; self-calibration details: initial model, solution interval, number of rounds, which data were included; jmfit/imfit fit regions and settings and how component positions were conver…

### 2020ApJ...902...99I: ALMA 0"02 Resolution Observations Reveal HCN-abundance-enhanced Counter-rotating and Outflowing Dense Molecular Gas at the NGC 1068 Nucleus (2020; agn_and_quasars, nearby_galaxies, astrochemistry; observational_alma_primary)
- question: Morphological, dynamical, chemical and physical properties of dense molecular gas in the putative dusty molecular torus of the type-2 AGN NGC 1068, probed at ~0.02'' with HCN/HCO+/HNC J=3-2, 13C isotopologue and vibrationally excited lines
- step 8: Analyse torus rotation along the torus axis and compare with Keplerian and maser curves
  - method: Beam-sized spectra at various distances from the SMBH along PA = 115 deg fitted with Gaussians for peak velocity and width (Figure 14); position-velocity diagrams (Figure 13); compare with Keplerian and H2O maser curves [4.3 Redshifted dense molecular emission…: "Figure 13 shows position velocity diagrams of HCN J=3–2 and HCO$^{+}$ J=3–2 lines along the position angle of PA = 115$^{\circ}$ east of north."] [4.4 Dynamical properties of the torus: "based on the Gaussian fit of beam-sized spectra extracted at various distances from the central SMBH along PA = 115$^{\circ}$"]
  - parameter: Keplerian curve V ∝ r^-0.5 for a point mass of 1e7 Msun, and sub-Keplerian V ∝ r^-0.31 from H2O masers [4.3 Redshifted dense molecular emission…: "overplotted with (1) Keplerian rotation (V $\propto$ r$^{-0.5}$) dominated by a point source with mass of 1 $\times$ 10$^{7}$M$_{\odot}$"]
  - assumption: Torus inclination i ~ 90 deg (edge-on); even i = 34–66 deg raises intrinsic velocity by only 1.1–1.8 [4.4 Dynamical properties of the torus: "it is very likely that the torus inclination is *i* $\sim$ 90$^{\circ}$ (edge-on)"]
  - fitting: Gaussian fits to beam-sized spectra [4.4 Dynamical properties of the torus: "based on the Gaussian fit of beam-sized spectra extracted at various distances from the central SMBH along PA = 115$^{\circ}$"]
  - validation: Innermost HCN and HCO+ dynamics roughly agree with VLBI H2O maser dynamics at <0.7 pc [4.3 Redshifted dense molecular emission…: "Our ALMA data demonstrate that HCN J=3–2 and HCO$^{+}$ J=3–2 emission line dynamics roughly agrees with the VLBI-detected H$_{2}$O maser dynamics at $<$0.7 pc."]
- limitation (authors): Emission larger than the maximum recoverable scale may be resolved out [2 Observations and Data Analyses: "Emission with a spatial extent larger than these MRSs may be resolved out and may not be recovered in our ALMA data."]
- limitation (authors): Extended host-galaxy emission is not recovered in the Cycle 6 data, so only compact torus emission is discussed [3 Results: "We will thus discuss only compact torus emission."]
- limitation (authors): Continuum peak flux uncertainties exclude absolute flux calibration and continuum frequency-range choice [Table 2: "Possible systematic uncertainties coming from absolute flux calibration ambiguity in individual ALMA observations and choice of frequency range to determine the continuum level are not taken into account."]
- not stated (card): CASA version used for uvcontsub, clean and imsmooth, and whether the ALMA-delivered calibration was re-run or used as delivered; Frequency or channel ranges treated as line free for the constant continuum fit in each spectral window (only 'obvious emission and absorption lines excluded'); clean settings other than robust and gain: deconvolver, niter, threshold, masks, image size, uv taper, primar…

### 2023ApJ...953L...6P: Detection of a High-velocity Jet from MWC 349A Traced by Hydrogen Recombination Line Maser Emission (2023; stellar_physics, evolved_stars; observational_alma_primary)
- question: What are the spatial distribution and kinematics of the H26alpha and H30alpha radio recombination line masers and millimeter continuum emission in MWC 349A, particularly in the high-velocity wind?
- step 4: Fit disk geometry, kinematics, enclosed stellar mass, and deprojected jet velocity
  - method: Perform linear least-squares fits to disk masers (-12 to 28 km s^-1) in sky coordinates to determine disk PA and polar axis, fit linear position-velocity relations to derive systemic velocity and velocity-distance slopes, calculate enclose… [Hydrogen Recombination Line Emission: "A linear least-squares fit to these maser points in the disk gives a position angle of the disk axis of $98.6\pm0.007$$^{\circ}$ in H$26\alpha$ and $99.7\pm0.002$$^{\circ}$ in H$30\alpha$."] [Hydrogen Recombination Line Emission: "In this case, the velocity-projected distance slopes can be described by the following relation (assuming Keplerian motion): $$\begin{equation} V_{LOS} = \sqrt{\frac{GM}{R^3}}l \end{equation}$$"]
  - parameter: Disk velocity range: -12 to 28 km s^-1; maser spatial extent (diameter 2R): 45 mas (H26alpha) and 54 mas (H30alpha); distance = 1.2 kpc; inclination = 9 deg from LOS [Hydrogen Recombination Line Emission: "As shown in Figure [3](#fig:maserdist)(b), masers with velocities between -12 km s$^{-1}$ and 28 km s$^{-1}$ are approximately distributed in a linear structure."] [Hydrogen Recombination Line Emission: "The masers have a maximum spatial extent of approximately $45$ mas in the H$26\alpha$ transition and $54$ mas in the H$30\alpha$ transition."]
  - assumption: Perfectly edge-on Keplerian disk with H26alpha and H30alpha masers localized on two thin annuli of fixed radii equal to the spatial extent of the masers; high-velocity masers distributed along the polar axis at 9 deg inclination from LOS [Hydrogen Recombination Line Emission: "Previously, (cite: zhang2017) assumed a model in which the two maser transitions are localized on two thin annuli of different, fixed radii on a perfectly edge-on disk."] [Hydrogen Recombination Line Emission: "For each transition, we took the radius of the annulus to be the spatial extent of the masers; the slopes from the linear fit can then be used to obtain an estimate of the enclosed mass."]
  - fitting: Linear least-squares fits to spatial distribution and position-velocity curves of disk masers [Hydrogen Recombination Line Emission: "A linear least-squares fit to these maser points in the disk gives a position angle of the disk axis of $98.6\pm0.007$$^{\circ}$ in H$26\alpha$ and $99.7\pm0.002$$^{\circ}$ in H$30\alpha$."] [Hydrogen Recombination Line Emission: "The y-intercept of a linear fit to the disk portion of the curve gave an estimate for the systemic velocity of this star-disk system."]
  - validation: Consistency of systemic velocity, disk PA, and enclosed mass between H30alpha and H26alpha transitions and with Zhang et al. (2017) [Hydrogen Recombination Line Emission: "The H$26\alpha$ masers yield an estimate of 9.6 ± 1.6 M$_\odot$, while for the H$30\alpha$ masers it is 11.5 ± 1.7 M$_\odot$. This is in excellent agreement with previous estimates, which put the mass of this system at $10-15$ M$_\odot$ (cite: zhang2017)."]
- result: Disk axis position angle (H26alpha) = 98.6 ± ±0.007 deg [Hydrogen Recombination Line Emission: "A linear least-squares fit to these maser points in the disk gives a position angle of the disk axis of $98.6\pm0.007$$^{\circ}$ in H$26\alpha$ and $99.7\pm0.002$$^{\circ}$ in H$30\alpha$."]
- result: Disk axis position angle (H30alpha) = 99.7 ± ±0.002 deg [Hydrogen Recombination Line Emission: "A linear least-squares fit to these maser points in the disk gives a position angle of the disk axis of $98.6\pm0.007$$^{\circ}$ in H$26\alpha$ and $99.7\pm0.002$$^{\circ}$ in H$30\alpha$."]
- result: Systemic LSR velocity from H30alpha rotation curve = 8.7 ± ±0.2 km s^-1 [Hydrogen Recombination Line Emission: "Using the H30$\alpha$ rotation curve, this linear fit yielded a y-intercept of 8.7 ± 0.2 km s$^{-1}$, and using the H26$\alpha$ rotation curve, we obtain 8.4 ± 0.1 km/s."]
- result: Systemic LSR velocity from H26alpha rotation curve = 8.4 ± ±0.1 km s^-1 [Hydrogen Recombination Line Emission: "Using the H30$\alpha$ rotation curve, this linear fit yielded a y-intercept of 8.7 ± 0.2 km s$^{-1}$, and using the H26$\alpha$ rotation curve, we obtain 8.4 ± 0.1 km/s."]
- result: Position-velocity slope of disk masers (H26alpha) = 771 ± ±7 km s^-1 arcsec^-1 [Hydrogen Recombination Line Emission: "The slopes obtained from these linear fits to the disk maser position-velocity plots were 771 ± 7 km s$^{-1}$ per arcsecond and 661 ± 9 km s$^{-1}$ per arcsecond for H$26\alpha$ and H$30\alpha$ masers, respectively."]
- result: Position-velocity slope of disk masers (H30alpha) = 661 ± ±9 km s^-1 arcsec^-1 [Hydrogen Recombination Line Emission: "The slopes obtained from these linear fits to the disk maser position-velocity plots were 771 ± 7 km s$^{-1}$ per arcsecond and 661 ± 9 km s$^{-1}$ per arcsecond for H$26\alpha$ and H$30\alpha$ masers, respectively."]
- result: Enclosed stellar mass from H26alpha masers = 9.6 ± ±1.6 M_odot [Hydrogen Recombination Line Emission: "The H$26\alpha$ masers yield an estimate of 9.6 ± 1.6 M$_\odot$, while for the H$30\alpha$ masers it is 11.5 ± 1.7 M$_\odot$."]
- result: Enclosed stellar mass from H30alpha masers = 11.5 ± ±1.7 M_odot [Hydrogen Recombination Line Emission: "The H$26\alpha$ masers yield an estimate of 9.6 ± 1.6 M$_\odot$, while for the H$30\alpha$ masers it is 11.5 ± 1.7 M$_\odot$."]
- result: Maximum deprojected space velocity of polar jet masers = 575 ± not stated km s^-1 [Abstract: "If these masers lie close to the polar axis, their velocities could be as high as 575 km s$^{-1}$ which cannot be explained solely by a single expanding wind as proposed in (cite: baez-rubio2013)."]
- limitation (authors): Self-calibration removes absolute position information, causing Band 6 and Band 7 images to lose absolute astrometry and exhibit a slight positional offset. [ALMA: "Since self calibration removes information about absolute position, images in band 6 and 7 lost their absolute astrometry."]
- limitation (authors): The ALMA synthesized beam is elongated in the north-south direction and could not resolve the north-south double peaks ('dark lane') seen in centimeter VLA observations. [Interferometric Continuum Emission: "Unlike previous cm continuum observations, however, we did not detect a “dark lane” separating two lobes in an approximate north-south direction (cite: tafoya2004; white1985). Both images from ALMA consist of a single peak. This is most likely a result of a relatively large beam size elongated in the north-south direc…"]
- limitation (authors): 2D Gaussian centroid fitting underestimates the true size of the maser disk because the maser emission is spatially extended, leading to a lower enclosed stellar mass estimate than 3D radiative transfer models (e.g., 38 M_odot in Baez-Rubi… [Hydrogen Recombination Line Emission: "These estimates of the stellar mass are smaller than the model value of 38 M$_\odot$ in (cite: baez-rubio2013). This is mainly due to the fact that the size of the maser disk is underestimated with the centroid fit since the maser emission is spatially extended as shown in the model by (cite: baez-rubio2013)."]
- not stated (card): Exact CASA version used for calibration and imaging; Exact synthesized beam sizes and position angles for the natural-weighted H30alpha and H26alpha line cubes (only approximate 0.03'' and 0.1'' are stated); Pixel/cell size, image dimensions, and stopping threshold/niter used in CASA CLEAN for continuum and line cubes; Whether continuum subtraction (e.g., uvcontsub) was performed on the spectral …

### 2017MNRAS.468.1769F: The varying mass distribution of molecular clouds across M83 (2017; nearby_galaxies, star_formation, milky_way_ism; archival_reuse)
- question: Does the molecular cloud mass distribution in M83 show a truncation mass that varies with galactocentric radius, like the young massive cluster population?
- step 5: Compute Jeans and Toomre masses
  - method: Radial profiles of Sigma, sigma_v from ALMA/SEST CO and THINGS HI; kappa from exponential disk rotation curve; M_J and M_T formulae [Mass Scales in M83: "We infer $\Sigma$, $\sigma_v$ and $\varkappa$ from the ALMA data and supplementary information."]
  - assumption: Exponential disk rotation curve of Lundgren 2004b [Mass Scales in M83: "They find the rotation curve is well modeled by an exponential disk."]
  - validation: THINGS rotation curve gives comparable results [Mass Scales in M83: "the results are otherwise comparable"]
- limitation (authors): Cloud blending in central region makes nuclear mass distribution suspect [Systematic Effects: "We should therefore regard the clouds in the $R_g<0.45$ kpc bin as particularly suspect"]
- not stated (card): Exact imaging parameters of the JVO QA2 cube (weighting, cell size, deconvolver); CASA version used for the delivered data; Fake-cloud size and line-width parameters used in the injection test; Exact radial bin geometry, inclination and position angle used for deprojection; Method for surface-density and velocity-dispersion profiles in the Toomre/Jeans calculation (radial binning details); Recipe…

### 2022MNRAS.515..543C: FAUST VI. VLA1623-2417 B: a new laboratory for astrochemistry around protostars on 50 au scale (2022; astrochemistry, star_formation, protoplanetary_disks; large_program_or_survey)
- question: What is the molecular complexity (specifically iCOM emission from CH3OH, HCOOCH3, and related species) and its physical and kinematic origin around the protostars in the VLA1623-2417 multiple system on a 50 au scale?
- step 5: Kinematic analysis and estimation of Keplerian emitting radii
  - method: Map red- and blue-shifted CH3OH emission, construct Position-Velocity (PV) diagram along the disk equatorial plane of VLA1623 B, and calculate Keplerian radii from velocity shifts, disk inclinations, and protostellar masses [Kinematics: on the origin of chemical e…: "Figure 8 shows the Position-Velocity (PV) diagram of the CH$_3$OH(4$_{\rm 2,3}$–3$_{\rm 1,2}$) E emission (representative of the line sample) for VLA1623 B."] [Kinematics: on the origin of chemical e…: "If we assume methanol is tracing an inclined Keplerian disk, the bulk of the emission would arise at a radius of 33 au."]
  - software: IRAM-GILDAS
  - parameter: Velocity integration ranges for channel maps: B (-11 to +14 km/s, or -16 to +24 km/s for 20_3,17-20_2,18 A), A (-2 to +7 km/s); velocity shifts: +/- 6-7 km/s for B, +/- 2 km/s for A1 [Kinematics: on the origin of chemical e…: "The emission is integrated between –11 km s$^{-1}$ (–2 km s$^{-1}$) and +14 km s$^{-1}$ (+7 km s$^{-1}$) for VLA1623 B (A) for all the lines eacept 20$_{\rm 3,17}$–20$_{\rm 2,18}$ A, which is integrated in the –16, +24 km s$^{-1}$ range toward VLA1623 B."] [Kinematics: on the origin of chemical e…: "The protostellar mass is 1.7 $M_{\rm \ensuremath{\odot}}$ (cite: Ohashi2022), and the two CH$_3$OH peaks are located at $\pm$ 6–7 km s$^{-1}$ with respect to the systemic velocity."]
  - assumption: Inclined Keplerian disk; for B: disk inclination = 74 deg, protostellar mass = 1.7 M_sun, d = 131 pc; for A1: disk inclination = 47 deg, protostellar mass = 0.1-0.2 M_sun [Kinematics: on the origin of chemical e…: "According to the high-angular resolution continuum measurements from (cite: Harris2018), the VLA1623 B disk inclination derived from the ratio between the observed minor and major axes is 74$\ensuremath{^\circ}$."] [Kinematics: on the origin of chemical e…: "The protostellar mass is 1.7 $M_{\rm \ensuremath{\odot}}$ (cite: Ohashi2022), and the two CH$_3$OH peaks are located at $\pm$ 6–7 km s$^{-1}$ with respect to the systemic velocity."]
  - validation: Derived radii (33 au for B, 12-24 au for A1) are comparable to continuum disk sizes from Harris et al. (2018) and LVG emitting size for B (14-45 au) [Kinematics: on the origin of chemical e…: "Noticeably, this distance is comparable with both the disk size imaged in the continuum by (cite: Harris2018) as well as the methanol-emitting size derived by the present LVG analysis (14–45 au)."] [Kinematics: on the origin of chemical e…: "Again, this size in agreement with $\sim$ 14–21 au disk derived by (cite: Harris2018) from the A1 continuum."]
- result: Keplerian radius of CH3OH ring in VLA1623 B = 33 ± not stated au [Abstract: "Assuming a chemically enriched ring within the accretion disk, close to the centrifugal barrier, its radius is calculated to be 33 au."]
- result: Keplerian radius of CH3OH ring in VLA1623 A1 = 12-24 ± not stated au [Abstract: "The methanol spectra towards A1 are somewhat narrower ($\sim$ 4 km s$^{-1}$), implying a radius of 12–24 au."]
- limitation (authors): Collisional coefficients for CH3OH are lacking for transitions with J >= 16. [Physical properties: LTE and LVG analys…: "Given the lack of collisional coefficients for methanol at transitions with rotational number $J$ $\geq$ 16 (cite: Rabli2010), our approach to deriving physical proporties is twofold:"]
- limitation (authors): LVG analysis is challenged by the limited number of lines with collisional rates (5 lines, with 4 in the narrow E_u = 45-61 K range). [Physical properties: LTE and LVG analys…: "The limited number of methanol lines and the fact that 4 lines out of 5 are in the narrow $E_{\rm u}$ = 45–61 K range make this analysis challenging."]
- limitation (authors): For source A, the E_u range of the 4 detected CH3OH lines (45-61 K) is too narrow for a free rotational diagram fit, only allowing an upper limit on T_rot. [Physical properties: LTE and LVG analys…: "For source A, the $E_{\rm u}$ range sampled by the 4 detected lines is too small to obtain a proper free fit."]
- not stated (card): Specific line-free channel ranges used for continuum extraction, self-calibration, and continuum subtraction; Self-calibration solution intervals, number of phase/amplitude rounds, and application to line cubes; Exact cleaning parameters (pixel/cell size, image dimensions, stopping threshold, masking strategy, and deconvolver algorithm); Method for combining multiple array configurations (e.g., 1…

### 2025A&A...704A...7P: Closing the gap: Follow-up observations of peculiar dusty objects close to Sgr A<SUP>*</SUP> using ERIS (2025; agn_and_quasars, stellar_physics, star_formation, milky_way_ism; multi_facility_alma_minor)
- question: Follow the Keplerian trajectories and spectroscopic evolution of peculiar dusty objects (G2/DSO, D9, X7) in the S cluster and the massive YSO X3 close to Sgr A* using VLT/ERIS to close the 2019-2024 observational gap.
- step 3: Fit Keplerian orbits and estimate orbital parameter uncertainties
  - method: Measure astrometric positions relative to Sgr A* via Gaussian fitting of Br-gamma line maps, fit Keplerian orbits across the 2005-2024 baseline, and run MCMC simulations using the Keplerian fit as the prior distribution. [Keplerian orbits: "From the spectral identification of the Doppler-shifted Br\gamma line and astrometric detection of the sources of interest presented in Sec. 3.1, we expand the existing data baseline from 2005 to 2024."] [MCMC simulations: "We use the results of the Keplerian fit as the apriori distribution. From the fits presented in Fig. 16-18 we extract the 1\sigma posterior uncertainty distribution."]
  - assumption: Distance to Sgr A* = 8 kpc, mass of Sgr A* = 4x10^6 M_sun (uniform priors) [Keplerian orbits: "Using a distance of 8 kpc and a mass for the central gravitational potential Sgr A* of 4\times10^{6}M_{\odot} (cite: eht2022; Peissker2022), the derived Keplerian elements for the S cluster sources G2/DSO, D9, and X7 are listed in Table"] [Incomplete orbits: "resulting in a difference of \approx 0.6\sigma between the observable-biased prior and the uniform priors used in this work for the distance and mass of Sgr A*."]
  - fitting: Keplerian orbit fit followed by MCMC simulations using the Keplerian fit as apriori distribution and adopting the upper 1-sigma posterior limit as the uncertainty. [MCMC simulations: "We use the results of the Keplerian fit as the apriori distribution. From the fits presented in Fig. 16-18 we extract the 1\sigma posterior uncertainty distribution."] [MCMC simulations: "Since the uncertainty range seems slightly asymmetric with a marginal lower limit, we use the upper limit to cover aspects of the data that may be underrepresented in the fit."]
  - validation: Compare updated (2005-2024) orbital elements against previous (2005-2019) orbital solutions. [Astrometric precision: "We compare every individual old and new orbital element and derive an individual deviation listed in Table 4."]
- result: G2/DSO semi-major axis (a, new) = 17.25 ± 0.10 mpc [Keplerian orbits: "G2/DSO - new | 17.25 \pm 0.10 | 0.965 \pm 0.002 | 121.03 \pm 1.71 | 93.85 \pm 2.01 | 63.59 \pm 1.94 | 2014.43 \pm 0.01 | 106.10"]
- result: G2/DSO eccentricity (e, new) = 0.965 ± 0.002 dimensionless [Keplerian orbits: "G2/DSO - new | 17.25 \pm 0.10 | 0.965 \pm 0.002 | 121.03 \pm 1.71 | 93.85 \pm 2.01 | 63.59 \pm 1.94 | 2014.43 \pm 0.01 | 106.10"]
- result: G2/DSO inclination (i, new) = 121.03 ± 1.71 deg [Keplerian orbits: "G2/DSO - new | 17.25 \pm 0.10 | 0.965 \pm 0.002 | 121.03 \pm 1.71 | 93.85 \pm 2.01 | 63.59 \pm 1.94 | 2014.43 \pm 0.01 | 106.10"]
- result: G2/DSO orbital period (T_P, new) = 106.10 ± not stated years [Keplerian orbits: "G2/DSO - new | 17.25 \pm 0.10 | 0.965 \pm 0.002 | 121.03 \pm 1.71 | 93.85 \pm 2.01 | 63.59 \pm 1.94 | 2014.43 \pm 0.01 | 106.10"]
- result: D9 semi-major axis (a, new) = 43.69 ± 0.040 mpc [Keplerian orbits: "D9 - new | 43.69 \pm 0.040 | 0.31 \pm 0.01 | 103.13 \pm 0.45 | 136.36 \pm 4.18 | 257.54 \pm 4.75 | 2321.70 \pm 0.01 | 427.67"]
- result: D9 eccentricity (e, new) = 0.31 ± 0.01 dimensionless [Keplerian orbits: "D9 - new | 43.69 \pm 0.040 | 0.31 \pm 0.01 | 103.13 \pm 0.45 | 136.36 \pm 4.18 | 257.54 \pm 4.75 | 2321.70 \pm 0.01 | 427.67"]
- result: D9 inclination (i, new) = 103.13 ± 0.45 deg [Keplerian orbits: "D9 - new | 43.69 \pm 0.040 | 0.31 \pm 0.01 | 103.13 \pm 0.45 | 136.36 \pm 4.18 | 257.54 \pm 4.75 | 2321.70 \pm 0.01 | 427.67"]
- result: D9 orbital period (T_P, new) = 427.67 ± not stated years [Keplerian orbits: "D9 - new | 43.69 \pm 0.040 | 0.31 \pm 0.01 | 103.13 \pm 0.45 | 136.36 \pm 4.18 | 257.54 \pm 4.75 | 2321.70 \pm 0.01 | 427.67"]
- result: X7 semi-major axis (a, new) = 149.98 ± 0.18 mpc [Keplerian orbits: "X7 - new | 149.98 \pm 0.18 | 0.76 \pm 0.03 | 74.48 \pm 6.87 | 189.07 \pm 10.88 | 25.21 \pm 12.60 | 1975.86 \pm 0.01 | 2720.15"]
- result: X7 eccentricity (e, new) = 0.76 ± 0.03 dimensionless [Keplerian orbits: "X7 - new | 149.98 \pm 0.18 | 0.76 \pm 0.03 | 74.48 \pm 6.87 | 189.07 \pm 10.88 | 25.21 \pm 12.60 | 1975.86 \pm 0.01 | 2720.15"]
- result: X7 orbital period (T_P, new) = 2720.15 ± not stated years [Keplerian orbits: "X7 - new | 149.98 \pm 0.18 | 0.76 \pm 0.03 | 74.48 \pm 6.87 | 189.07 \pm 10.88 | 25.21 \pm 12.60 | 1975.86 \pm 0.01 | 2720.15"]
- result: Averaged deviation between old and new Keplerian elements for G2/DSO = 0.48 ± not stated % [Keplerian orbits: "comparing both orbital solutions, we find an averaged deviation of the six Keplerian elements between the old and new orbit of 0.48\% for G2/DSO, 1.63\% for D9, and 0.21\% for X7."]
- result: Averaged deviation between old and new Keplerian elements for D9 = 1.63 ± not stated % [Keplerian orbits: "comparing both orbital solutions, we find an averaged deviation of the six Keplerian elements between the old and new orbit of 0.48\% for G2/DSO, 1.63\% for D9, and 0.21\% for X7."]
- result: Averaged deviation between old and new Keplerian elements for X7 = 0.21 ± not stated % [Keplerian orbits: "comparing both orbital solutions, we find an averaged deviation of the six Keplerian elements between the old and new orbit of 0.48\% for G2/DSO, 1.63\% for D9, and 0.21\% for X7."]
- limitation (authors): Limited IFU field of view covers only about 33% of X7's elongated structure, introducing a systematic offset of the fitted tip position toward Sgr A*. [X7: "Considering a projected length of the dust emission of X7 of about 0.3 arcsec in 2021 as displayed in (cite: Ciurlo2023), our measurements of the Doppler-shifted Br\gamma line emission only covers about 33\% due to the limited FOV"]
- limitation (authors): Low orbital coverage (5-15% for G2/DSO and D9) limits improvement in absolute orbital uncertainties and creates a ~0.6 sigma difference relative to observable-biased priors. [Keplerian orbits: "However, the absolute uncertainties of the Keplerian elements are only marginally affected by the longer data baseline which is due to the low orbital coverage of the observations (cite: ONeil2019; Ali2020)."]
- limitation (authors): OH sky line emission (e.g., at 2.158 um) and high stellar crowding in the S cluster impact extracted spectra and Gaussian fit uncertainties. [Spectra of the dusty objects: "For the spectrum of G2/DSO shown in Fig. 13, the Gaussian may be impacted by the OH line emission at 2.158\mu m (cite: Rousselot2000), resulting in a fit uncertainty of 8.9 km/s."]
- not stated (card): All ALMA calibration and imaging parameters for 2016.1.00870.S (only used in the Fig. 1 finding chart); Exact MCMC sampler software, number of walkers, burn-in, and step count for the Keplerian orbit uncertainty estimation; Asymmetric Least Squares (ASL) smoothing and weighting parameters used for continuum slope subtraction; Exact historical astrometric and radial velocity data tables from 2005-…

### 2020PASJ...72L...5T: How far actually is the Galactic Center IRS 13E3 from Sagittarius A<SUP>*</SUP>? (2020; milky_way_ism, astrochemistry; archival_reuse)
- question: Can the line-of-sight (3D) distance of IRS 13E3 from Sgr A* be estimated from the presence of a vibrationally excited CH3OH line in the ionized gas stream, given that CH3OH is destroyed by cosmic rays near Sgr A*?
- step 4: Map the CH3OH v=1 feature along the ionized gas stream
  - method: Channel map at V_LSR = 130 km/s (H30alpha reference), width 10 km/s, tracing the feature along the Keplerian stream [Search for the molecular emission line …: "Figure 1d shows the feature D in the channel map of $V_{\mathrm{LSR}}=130$ km s$^{-1}$ referencing to the H30$\alpha$ recombination line"] [Search for the molecular emission line …: "The velocity width is $\Delta V=10$ km s$^{-1}$."]
- step 6: Test the method on the Northern arm and locate the molecular gas front
  - method: PV diagram along the Northern arm; a faint ridge ~400 km/s from the H30alpha ridge is taken as CH3OH v=1; its disappearance point is placed on a Keplerian orbit to obtain the 3D distance [Vibrationally excited CH$_3$OH emission…: "the 3D distance of the disappearance point (molecular gas front) is estimated to be $r \sim 0.4$ pc (please see figure 2c)"]
  - parameter: Keplerian orbit with a ~1 pc, e ~0.8, i ~140 deg [Vibrationally excited CH$_3$OH emission…: "Assuming the trajectory of the NA is described by a Keplerian orbit with the semi-major axis of $a\sim1$ pc, the eccentricity of $e\sim0.8$, and the inclination angle of $i\sim 140^\circ$ ((cite: Zhao2009))"]
  - assumption: The NA trajectory is Keplerian; CH3OH decays gradually while the arm falls toward Sgr A* [Vibrationally excited CH$_3$OH emission…: "The gradual decay would be why CH$_3$OH molecule is survived up to $r \sim 0.4$ pc."]
- result: 3D distance lower limit of IRS 13E3 from Sgr A* (abstract) = >~0.4 ± not stated pc [abstract: "This indicates that IRS 13E3 is located at $r\gtrsim 0.4$ pc from Sgr A$^{\ast}$."]
- result: Apparent velocity at the CH3OH disappearance point in the Northern arm = ~350 ± not stated km/s [Vibrationally excited CH$_3$OH emission…: "The apparent velocity at the disappearance point is $V_\mathrm{LSR} \sim 350$ km s$^{-1}$."]
- result: Projection distance of the CH3OH disappearance point = ~0.1 ± not stated pc [Vibrationally excited CH$_3$OH emission…: "$r_{\mathrm{p}} \sim 0.1$ pc, the 3D distance may be larger than the projection distance"]
- result: 3D distance of the Northern arm molecular gas front = ~0.4 ± not stated pc [Vibrationally excited CH$_3$OH emission…: "the 3D distance of the disappearance point (molecular gas front) is estimated to be $r \sim 0.4$ pc (please see figure 2c)"]
- result: Elapsed time moving from r ~1 pc to r ~0.4 pc along the Northern arm = ~(1-2)x10^3 ± not stated yr [Vibrationally excited CH$_3$OH emission…: "The elapse time moving from $r \sim 1$ pc to $r \sim 0.4$ pc is $\sim(1-2)\times10^3$ yr."]
- limitation (authors): The IRS 13E3 distance bound for the Northern arm test is an assumption, not a measurement [Vibrationally excited CH$_3$OH emission…: "It is assumed here that IRS 13E3 is located at $r \gtrsim 0.4$ pc."]
- not stated (card): Which ALMA project (2015.1.01080.S or 2017.1.00503.S) supplies each figure, and the band, spectral windows and array configurations; CASA version, calibration and any self-calibration applied to the H30alpha cube; Imaging parameters: weighting, robust, cell size, beam, channel width and rms of the cube used for the PV diagrams and channel maps; Continuum subtraction method and line-free channels;…

### 2025ApJ...988L..44F: A Deep Search for Ethylene Glycol and Glycolonitrile in the V883 Ori Protoplanetary Disk (2025; astrochemistry, protoplanetary_disks; observational_alma_primary)
- question: Are ethylene glycol and glycolonitrile, molecular precursors of nucleic acids, present in the V883 Ori protoplanetary disk, and how do their abundances relative to methanol compare with hot cores and comets?
- step 6: Make moment maps of isolated EG and GN lines
  - method: Moment 0 sums 4 EG and 2 GN transitions; moment 1 maps are averages; velocity gradient checked for disk rotation [3 Analysis: "The integrated intensity maps sum the emission from 4 transitions of EG and 2 transitions of GN respectively, while the intensity weighted velocity maps are averages."]
  - assumption: emission from a Keplerian disk [3 Analysis: "This pattern supports our assumption of emission from a Keplerian disk centered at these frequencies."]
  - validation: Moment 1 shows red-to-blue shift along the semi-major axis, consistent with a rotating disk [3 Analysis: "The moment 1 maps show a clear shift from red-shifted to blue-shifted across the disk semi-major axis, consistent with emission from a rotating disk."]
- limitation (authors): EG temperature not constrained and a more complex temperature structure is possible [3 Analysis: "However, it is possible that the data would be better fit by a model with a more complex temperature structure."]
- limitation (authors): Significant line blending at 0.42 km/s resolution; detections tentative [4.5 Uncertainty in the measured abundan…: "there is significant line blending at the current spectral resolution of 0.42 km"]
- limitation (authors): CH3OH column density not reliably measured; canonical 12C/13C may overestimate it [4.5 Uncertainty in the measured abundan…: "Since $\mathrm{CH_3OH}$ column density is not reliably measured, its difficult to constrain from the main isotopologue."]
- not stated (card): Array configurations, baselines, time on source, and calibrators for the six execution blocks; Self-calibration, if any, and how the six execution blocks were combined; Continuum subtraction method and line-free channels; Image size, cell size, deconvolver, masking and cleaning threshold for the cubes; Spectrum extraction aperture/region used for the V883 Ori spectrum (given only in Fadul25 and f…

### 2015A&A...574A...5D: ALMA data suggest the presence of spiral structure in the inner wind of CW Leonis (2015; evolved_stars; observational_alma_primary)
- question: What is the morpho-kinematical structure of the inner wind of the carbon star CW Leo, and does it show a binary-induced spiral?
- step 6: Orbital period, separation, companion mass
  - method: Arm spacing to period via Kim & Taam relation; Kepler's third law; Huggins et al. relation for mass [8.2: "The derived arm spacing hence results in an orbital period of $\sim$55 yr."]
  - assumption: Primary mass 4 Msun, companion less massive [8.2: "assuming a primary initial mass of 4 M$_{\odot}$ for CW Leo"]
- result: Orbital period = 55 ± not stated yr [8.2: "The derived arm spacing hence results in an orbital period of $\sim$55 yr."]
- result: Binary separation = 25 ± 2 au [8.2: "the mean binary separation, $d$, for CW Leo is $\sim$25$\pm$2 au"]
- result: Companion mass (Huggins relation) = ~1.1 ± significant Msun [8.3: "the derived mass for the secondary, $M_s$, is $\sim$1.1 M$_{\odot}$"]
- limitation (authors): Short observation and sparse uv coverage hamper interpretation [8.1: "With an on-source integration time of only 17 minutes, an in-depth understanding of the $^{13}$CO J=6-5 channel maps"]
- not stated (card): CASA version; clean threshold, niter, mask, and robust/uniform weighting parameter; line-free channel ranges for continuum; self-calibration solution intervals; Shape model files and full parameter set (orientation angles, PA); Exact simobserve settings; How the best-fit spiral was judged (visual comparison, no statistic)

### 2018ApJ...868..113T: Evidence for a Vertical Dependence on the Pressure Structure in AS 209 (2018; protoplanetary_disks; archival_reuse)
- question: Can an improved Gaussian-Process rotation-velocity method applied to archival 12CO data of AS 209 reveal pressure perturbations and their relation to mm and NIR rings?
- step 1: Image continuum and 12CO
  - method: tclean with Keplerian mask from moment-map fit; natural weighting for 12CO [3.1 Observations: "The data were then imaged and CLEANed again using this Keplerian mask."]
  - software: CASA
  - parameter: 160 m/s channels [3.1 Observations: "The data were imaged at a velocity resolution of $\approx 160~{\rm m\,s^{-1}}$ ($\approx 244~{\rm kHz}$)."]
  - assumption: i = 35.3 deg fixed [3.1 Observations: "holding the inclination constant at $i = 35.3\ensuremath{^\circ}$ (cite: Fedele_ea_2018)"]
  - validation: Mask checked to encompass whole emission [3.1 Observations: "checked to encompass the whole emission"]
- step 2: Fit Keplerian pattern and emission surface
  - method: Fit line-of-sight velocity map (parabola fit to peak pixel) with conical emission surface, convolved with beam [3.2 Measuring Rotation Curves: "we fit a Keplerian pattern, including a conical emission surface (cite: Rosenfeld_ea_2013) using the MCMC ensemble sampler `emcee`"]
  - software: emcee, bettermoments
  - assumption: i = 35.3 deg fixed; z = r tan psi [3.2 Measuring Rotation Curves: "The emission surface is calculated as $z = r \cdot \tan \psi$"]
  - fitting: emcee; uncertainties are posterior standard deviations [3.2 Measuring Rotation Curves: "The uncertainties are the standard deviation of the posterior distribution."]
  - validation: Emission height cross-checked with Pinte et al. 2018 method, psi ~13 deg [3.2 Measuring Rotation Curves: "we find good agreement with a conical model with $\psi \approx 13\ensuremath{^\circ}$"]
- step 3: Measure azimuthally averaged rotation curve
  - method: Deproject spectra into annuli, shift by v_rot cos(theta), stack, model stack as Gaussian Process and minimise residual variance; annuli of quarter beam [3.2 Measuring Rotation Curves: "we then bin the data into annuli with a width of a quarter of the beam ($\approx 0.05\ensuremath{''}$) and derive a $v_{\rm rot}$ value."]
  - software: eddy, celerite
  - parameter: three cases: flared, thin, flared without continuum subtraction [3.2 Measuring Rotation Curves: "firstly we deproject the sky-plane coordinates into disk coordinates to correctly account for the flaring, secondly we consider a geometrically thin disk, and finally we consider the flared disk with no continuum subtraction."]
  - fitting: Gaussian Process via celerite; radial profile also modelled as GP [3.2 Measuring Rotation Curves: "We further model the radial profile as a Gaussian Process, requiring the profile to be smoothly varying"]
  - validation: Simulated spectra tests (Appendix); three cases consistent within 3 sigma [3.2 Measuring Rotation Curves: "All three scenarios yield comparable radial $v_{\rm rot}$ profiles which are consistent within $3\sigma$ of one another."]
- result: Stellar mass from Keplerian fit (i=35.3 deg) = 1.16 ± 0.01 Msun [3.2 Measuring Rotation Curves: "$M_{\star} = 1.16 \pm 0.01~M_{\rm sun}$"]
- result: Position angle = 86.7 ± 0.1 deg [3.2 Measuring Rotation Curves: "${\rm PA} = 86.7\ensuremath{^\circ} \pm 0.1\ensuremath{^\circ}$"]
- result: v_LSR = 4670 ± 5 m/s [3.2 Measuring Rotation Curves: "$v_{\rm LSR} = 4670 \pm 5~{\rm m\,s^{-1}}$"]
- result: Emission surface angle psi = 13.1 ± 0.3 deg [3.2 Measuring Rotation Curves: "$\psi = 13.1\ensuremath{^\circ} \pm 0.3\ensuremath{^\circ}$"]
- result: 12CO integrated flux = 7.99 ± not stated Jy km/s [3.1 Observations: "we measure an integrated flux of 7.99 Jy km s$^{-1}$"]
- result: Continuum integrated intensity = 251 ± not stated mJy [3.1 Observations: "an integrated intensity of 251 mJy was measured"]
- result: Thin-disk reference Keplerian stellar mass (i=35.7 deg) = 1.25 ± not stated Msun [3.2 Measuring Rotation Curves: "resulting in $M_{\rm star} = 1.25~M_{\rm sun}$"]
- result: Cloud absorption of 12CO on western side = ~30 ± not stated percent [3.1 Observations: "the cloud absorbs $\approx 30\%$ of the $^{12}$CO emission on the Western side of the disk"]
- result: Max deviation from Keplerian rotation = up to 5 ± not stated percent [abstract: "shows substantial deviations from Keplerian rotation of up to $\pm 5\%$"]
- limitation (authors): Resolution (~29 au) leaves velocity features unresolved, underestimating depth [4.3 Pressure Profile: "the velocity features are not resolved and so will underestimate the true depth"]
- limitation (authors): Cannot disentangle pressure gradient from stellar mass; pressure scaling depends on assumed density [3.2 Measuring Rotation Curves: "we are unable to disentangle large scale effects of the pressure gradient from the stellar mass"]
- not stated (card): Line-free channels used for uvcontsub; Self-calibration solution intervals; Clean threshold, cell and image size, and number of iterations; Priors and walker/step settings for the emcee Keplerian fit; Gaussian-Process kernel and hyperparameters in celerite; Rest frequency/transition of 12CO and distance to AS 209; Details of the six-Gaussian perturbation fit (priors, parametrisation); Source of t…

### 2024ApJ...967...68H: Radial and Vertical Constraints on the Icy Origin of H<SUB>2</SUB>CO in the HD 163296 Protoplanetary Disk (2024; protoplanetary_disks, astrochemistry; observational_alma_primary)
- question: Which formation pathway (grain-surface versus gas-phase) dominates H2CO in the HD 163296 disk, constrained by radial, vertical, excitation-temperature and ortho-to-para-ratio (OPR) profiles
- step 2: Image line cubes to a common 0.6 arcsec circular beam with JvM correction
  - method: tclean with Briggs weighting plus per-line UV taper, multiscale CLEAN with Keplerian mask, threshold 4x rms, then JvM correction [Data Reduction: "We used a Briggs weighting and multiscale deconvolver (cite: Cornwell2008) with scales of 0, 5, 15, and 25 pixels"] [Data Reduction: "The images were CLEANed up to a threshold defined as four times the estimated rms of unmasked regions, and subsequently, were corrected for the *JvM effect* (cite: JvM1995)."]
  - software: CASA, tclean, keplerian_mask
  - parameter: Robust 0.0-0.5 and per-line UV taper (Table 4); pixel about 1/7 beam; channel width 0.2 km/s (0.5 km/s for Band 3) [Data Reduction: "All the final cubes have a channel width of $0.2$ km s$^{-1}$, with the exception of the Band 3 transition"]
  - validation: JvM epsilon values reported (0.59-0.99); beam circularity achieved for all lines [Data Reduction: "Our derived $\epsilon$ values are listed in Table"]
- step 3: Measure disk-integrated flux densities
  - method: Extract disk-integrated spectrum within the Keplerian mask; uncertainty from 1000 off-source masks [3.1 Disk-integrated Emission: "we defined the uncertainty associated with the integrated flux density as the standard deviation of the integrated fluxes measured within 1000 off-source Keplerian masks"]
  - software: GoFish
  - parameter: Integrated within outer radius of 4.5 arcsec and between -1.8 and 13.4 km/s [Table 2: "The integrated flux density is measured within an outer radius of $4\hbox{$.\!\!^{\prime\prime}$}5$ and integrating the emission between $-1.8$ and $13.4$ km s$^{-1}$."]
- step 4: Make zeroth-moment maps with bootstrapped noise
  - method: Collapse cubes with bettermoments using one Keplerian mask for all lines, no clipping; rms from 1000 off-source moment maps [3.2 Spatial Distribution of H2CO Emissi…: "We did not apply a threshold clipping to recover accurate fluxes."] [3.2 Spatial Distribution of H2CO Emissi…: "We created 1000 zeroth-moment maps, using the same Keplerian mask but centered at different off-source positions."]
  - software: bettermoments
  - validation: The 6_15-6_16 line not shown since no emission above 3 sigma in channels or unmasked moment map [3.2 Spatial Distribution of H2CO Emissi…: "there is no substantial line emission larger than $3\sigma$ neither in the channel maps nor the unmasked zeroth-moment map"]
- step 6: Fit disk-averaged LTE excitation conditions and OPR
  - method: Simultaneous LTE fit of ortho and para lines for N_T, T_ex, OPR and line width on the Keplerian-corrected disk-averaged spectrum [3.4 H2CO Excitation Conditions and OPR: "we simultaneously model the emission of each line to determine the excitation temperature, the total (ortho + para) column density, and the OPR of H$_2$CO"] [3.4.1 Disk-averaged Analysis: "we used the `average``_``spectrum` function from `GoFish`, which corrects the spectrum for Keplerian rotation before averaging"]
  - software: GoFish, emcee
  - parameter: Free parameters N_T, T_rot, OPR and Delta v [3.4 H2CO Excitation Conditions and OPR: "the free parameters to fit are $N_{\mathrm{T}}$, $T_\mathrm{rot}$, $\mathrm{OPR}$, and $\Delta v$"]
  - assumption: LTE [3.4 H2CO Excitation Conditions and OPR: "If we assume that the line emission occurs under local thermodynamic equilibrium (LTE)"]
  - assumption: Same excitation temperature for ortho and para [3.4 H2CO Excitation Conditions and OPR: "we assume the same excitation temperature since we detected only two o-H$_2$CO lines"]
  - assumption: Gaussian line profile centred at v_sys = 5.8 km/s [3.4 H2CO Excitation Conditions and OPR: "assuming a Gaussian line profile centered at $v_{\mathrm{sys}}=5.8$ km s$^{-1}$ (cite: Teague2019) with a certain $\Delta v$"]
  - assumption: Emitting layer in the midplane (z/r = 0) for the disk-averaged case [3.4.1 Disk-averaged Analysis: "For simplicity, we assume that the emitting layer is in the midplane ($z/r = 0$)"]
  - assumption: Background temperature is the maximum of dust continuum brightness temperature and the CMB (2.73 K) [3.4 H2CO Excitation Conditions and OPR: "where $T_{\mathrm{bg}}$ is the background temperature defined as the maximum between the dust continuum brightness temperature and the cosmic microwave background (CMB) temperature ($T_{\mathrm{CMB}} = 2.73$ K)"]
  - fitting: emcee MCMC with a likelihood built from the LTE line intensity; best values from 16th, 50th, 84th percentiles; priors, walkers and steps not stated [3.4 H2CO Excitation Conditions and OPR: "and use the `emcee` package (cite: Foreman-Mackey2013) to explore the parameter space and get the posterior probability distributions"] [3.4.1 Disk-averaged Analysis: "The best-fit excitation conditions and their corresponding uncertainties are deduced from the 16th, 50th, and 84th percentiles of the posterior distributions"]
  - validation: Optically thin check (tau 0.003-0.074); consistent with 6_15-6_16 nondetection; repeated with Voigt profile giving consistent results [3.4.1 Disk-averaged Analysis: "We also checked that these excitation conditions are consistent with the nondetection of the $6_{15}-6_{16}$ line"] [3.4.1 Disk-averaged Analysis: "Consequently, we performed the same analysis but using a Voigt profile."]
- step 7: Fit radially resolved excitation conditions and OPR
  - method: Deproject spectra into radial annuli with GoFish radial_spectra, shift and stack for Keplerian motion, and repeat the LTE fit in each bin [3.4.2 Radially Resolved Analysis: "we repeat the same line fitting procedure but use the deprojected radial spectra instead of the disk-averaged one"]
  - software: GoFish, emcee
  - parameter: Annulus width equals one-quarter of the beam major axis [3.4.2 Radially Resolved Analysis: "whose width corresponds to one-quarter of the beam"]
  - assumption: LTE, shared T_ex for ortho and para, same emitting region for all lines (acknowledged in footnote) [Footnote 7: "e.g., LTE emission, same $T_{\mathrm{ex}}$ for both isomers and the same emitting region for all the lines"]
  - fitting: Likelihood and emcee fit per radial bin [3.4.2 Radially Resolved Analysis: "we construct a likelihood function for each radial bin to determine the best-fit models at different radii"]
  - validation: Mean values compatible with disk-averaged results; emission confirmed optically thin throughout [3.4.2 Radially Resolved Analysis: "In general, the mean values of each profile are compatible with the disk-averaged results"]
- result: Disk-averaged total H2CO column density N_T (Gaussian fit) = 3.89e12 ± +0.18/-0.18 e12 cm^-2 [3.4.1 Disk-averaged Analysis: "$N_{\mathrm{T}} = 3.89_{-0.18}^{+0.18} \times 10^{12}$ cm$^{-2}$, $T_{\mathrm{ex}} = 19.42_{-1.51}^{+1.59}$ K, and $\mathrm{OPR} = 2.70_{-0.19}^{+0.20}$"]
- result: Disk-averaged excitation temperature T_ex = 19.42 ± +1.59/-1.51 K [3.4.1 Disk-averaged Analysis: "$T_{\mathrm{ex}} = 19.42_{-1.51}^{+1.59}$ K, and $\mathrm{OPR} = 2.70_{-0.19}^{+0.20}$"]
- result: Disk-averaged ortho-to-para ratio = 2.70 ± +0.20/-0.19 dimensionless [3.4.1 Disk-averaged Analysis: "$\mathrm{OPR} = 2.70_{-0.19}^{+0.20}$ for a Gaussian line width of $\Delta v = 0.80_{-0.03}^{+0.03}$ km s$^{-1}$"]
- result: Gaussian line width Delta v (disk-averaged) = 0.80 ± +0.03/-0.03 km/s [3.4.1 Disk-averaged Analysis: "for a Gaussian line width of $\Delta v = 0.80_{-0.03}^{+0.03}$ km s$^{-1}$"]
- result: Disk-averaged line optical depth range = 0.003 to 0.074 ± not stated dimensionless [3.4.1 Disk-averaged Analysis: "The disk-averaged line optical depths are between $\tau_\nu = 0.003$ and $0.074$"]
- result: Radially resolved total column density range = ~1.3e12 to ~2.0e13 ± not stated cm^-2 [3.4.2 Radially Resolved Analysis: "Total column density values range from $\sim 2.0 \times 10^{13} - 1.3\times 10^{12}$ cm$^{-2}$ within a radius of $\sim450$ au"]
- result: Radial T_ex profile range (about 30 K near CO snowline, about 20 K at R_edge) = decreases from 50 to 10 ± not stated K [3.4.2 Radially Resolved Analysis: "We find that the $T_{\mathrm{ex}}$ profile decreases smoothly from $50$ to $10$ K"]
- result: Radial OPR profile level = ~2.7, consistent with 3.0 ± not stated dimensionless [3.4.2 Radially Resolved Analysis: "mostly centered at $\mathrm{OPR}\sim 2.7$ but with uncertainties that remain compatible with the statistically expected value of $\mathrm{OPR}=3.0$"]
- result: Integrated flux density p-H2CO 3_03-2_02 = 1011 ± 13 mJy km/s [Table 2: "$0.6 \times 0.6$ | $47.71$ | $1.20$ | $0.48$ | $1011 \pm 13$"]
- result: Integrated flux density o-H2CO 3_12-2_11 = 1595 ± 13 mJy km/s [Table 2: "$0.6 \times 0.6$ | $45.21$ | $1.52$ | $0.54$ | $1595 \pm 13$"]
- result: Integrated flux density p-H2CO 4_04-3_03 = 1519 ± 11 mJy km/s [Table 2: "$0.6 \times 0.6$ | $-46.72$ | $2.47$ | $0.83$ | $1519 \pm 11$"]
- result: Integrated flux density p-H2CO 4_23-3_22 = 137 ± 11 mJy km/s [Table 2: "$0.6 \times 0.6$ | $-71.43$ | $2.51$ | $0.79$ | $137 \pm 11$"]
- result: Integrated flux density p-H2CO 4_22-3_21 = 141 ± 11 mJy km/s [Table 2: "$0.6 \times 0.6$ | $52.56$ | $2.61$ | $0.84$ | $141 \pm 11$"]
- result: Integrated flux density o-H2CO 4_13-3_12 = 2541 ± 13 mJy km/s [Table 2: "$0.6 \times 0.6$ | $3.84$ | $2.53$ | $0.81$ | $2541 \pm 13$"]
- result: Integrated flux density o-H2CO 6_15-6_16 (upper limit) = <26 ± not stated mJy km/s [Table 2: "$0.6 \times 0.6$ | $-41.20$ | $0.70$ | $0.38$ | $<26$"]
- limitation (authors): Vertical height is a lower limit because optically thin emission blurs near and far surfaces [3.5 Vertical Height of the Emission: "Thus, the determined value should be interpreted as a lower limit."]
- limitation (authors): OPR uncertainties are purely statistical and ignore modelling assumptions [3.4.1 Disk-averaged Analysis: "since the derived uncertainties are purely statistical and do not consider the assumptions mentioned in Section"]
- limitation (authors): Inner-disk column density drop is unresolved and fit quality is poorer there [4.2.1 Radial Distribution of H2CO: "the results should be treated with caution as we are on a region that cannot be resolved with the current angular resolution"]
- not stated (card): Self-calibration details per band and baseline set: which solution intervals, reference antenna, spw combination, S/N thresholds, and the continuum channel selection; Line-free channel ranges used for pseudo-continuum and uvcontsub fit order; Image size, number of CLEAN iterations, and the self-calibration continuum mask; Whether primary beam correction was applied and how; MCMC settings for emce…

### 2021AJ....162...99F: The Chemical Inventory of the Planet-hosting Disk PDS 70 (2021; protoplanetary_disks, astrochemistry, exoplanets; observational_alma_primary)
- question: What is the chemical inventory of the planet-hosting PDS 70 disk (detections, radial profiles, column densities, deuteration and N fractionation, C/O) and what does it imply for the gas accreted by the two planets?
- step 5: Image the line cubes
  - method: uvcontsub first-order continuum subtraction; tclean multiscale with Keplerian masks; lines imaged -6 to +17 km/s with natural and robust 0 weighting, final per-line choice in Table 2; elevated emission surface for 12CO and HCO+ [Observations and data reduction: "Imaging of the spectral lines was performed with `tclean` with the `multiscale` deconvolver, allowing for point sources in the emission"] [Observations and data reduction: "were imaged between -6 and +17 km s$^{-1}$ with both natural and Briggs weighting with a robust parameter equalling zero."]
  - software: CASA tclean, CASA uvcontsub, keplerian_mask.py
  - parameter: Keplerian mask geometry from Keppler+2019: M_star 0.875 Msun, i 51.7 deg, PA 160.4 deg [Observations and data reduction: "We use the following geometrical parameters: M$_{\rm star}=0.875\,M_\odot$, $i=51.7^\circ$, PA$=160.4^\circ$ (cite: keppler19)."]
  - parameter: elevated surface z(r)=0.33 x (r/1'')^0.76 for 12CO and HCO+ [Observations and data reduction: "using the best fit parameters by (cite: keppler19): $z(r)[\ensuremath{''}]=0.33\times(r / 1\ensuremath{''})^{0.76}$"]
  - parameter: weak lines c-C3H2 3_21-2_12 and H2CO 3_21-2_20 additionally uv-tapered by 0.7'' [Line fluxes: "In order to increase the significance of the detections, we image the lines with an additional $uv$-tapering of $0.7\ensuremath{''}$."]
  - assumption: line emission follows the Keplerian model fitted to 12CO 3-2 [Observations and data reduction: "exploit the rotation of the disk well fitted by a Keplerian model in the $^{12}$CO $J$=3-2 line to have a prior on where the molecular lines originate."]
  - validation: multiple imaging runs per line to balance resolution, intensity and channel spacing [Observations and data reduction: "multiple imaging runs have been performed on each line to obtain the best compromise between angular resolution, intensity and channel spacing."]
- step 6: Stack spectra and measure line fluxes and detections
  - method: Deproject and shift local spectra to systemic velocity with GoFish using the Keppler+2019 Keplerian fit, integrate within 3'' (4'' for 12CO 2-1), integrate spectrum over velocity windows; C2H F=4-3 and F=3-2 blend fitted with a double Gaus… [Line fluxes: "at every spatial location we de-project the emission and then shift the local spectrum to the systemic velocity using the `GoFish` package (cite: gofish)."] [Line fluxes: "We then integrate the spectra within $3\ensuremath{''}$ from the disk center"]
  - software: GoFish, VISIBLE, CASA
  - parameter: integration window 3-8 km/s (default); 1.5-9.5 km/s for the two 12CO and HCO+; 2-9 km/s for 13CO, H13CN and C2H [Line fluxes: "To obtain line fluxes, we spectrally integrate the spatially integrated stacked spectrum between 3-8 km s$^{-1}$, with the systemic velocity being $5505\pm2\,$m s$^{-1}$ (cite: keppler19)."] [Line fluxes: "The two $^{12}$CO and the HCO$^+$ lines are integrated between 1.5-9.5 km s$^{-1}$"]
  - parameter: flux uncertainty from standard deviation of unused velocity bins times sqrt(number of integrated bins) [Line fluxes: "The flux uncertainty for all lines is estimated as standard deviation of the velocity bins not included in the velocity integration, times the square root of the number of bins over which we integrate."]
  - parameter: C2H J=5/2-3/2 only half covered: only the part of the disk within 80 deg of the red-shifted major axis is used, azimuthal symmetry assumed [Line fluxes: "we consider only the part of the disk within $80^\circ$ of the red-shifted major axis and then assume azimuthal symmetry to extract the total flux."]
  - assumption: Keplerian kinematics from Keppler+2019 apply to all lines [Line fluxes: "Exploiting the kinematical fit of the Keplerian disk obtained by (cite: keppler19)"]
  - fitting: double Gaussian fit to blended C2H J=7/2-5/2 lines [Line fluxes: "and fluxes have been estimated by fitting a double Gaussian to the profile."]
  - validation: weak-line detections checked in channel maps, in azimuthally averaged spectra on annuli of 1/4 beam major axis, and with a VISIBLE matched filter on the visibilities [Line fluxes: "As a final test to assess the robustness of the detection of the two lines, we divide the projected emission in concentric annuli, separated by one quarter of the major axis of the beam."] [Line fluxes: "This method requires a model image as matched filter, and we thus run the analysis onto the continuum subtracted visibilities with the CS and H$^{13}$CO$^+$ channel maps as filters."]
- step 7: Make integrated intensity maps and radial profiles
  - method: Integrated intensity maps over whole cubes with 2.5 sigma clipping and Keplerian masking; azimuthal average of deprojected moment-0 maps in annuli of 1/4 beam major axis [Integrated maps: "Integrated intensity maps of the 14 detected lines are then created integrating over the whole cubes with a $2.5\sigma$ clipping."] [Radial profiles: "we azimuthally average the de-projected integrated intensity maps shown in Fig."]
  - software: CASA, GoFish
  - parameter: annulus width = 1/4 of the beam major axis [Radial profiles: "The width of the annuli are a quarter of the beam major axis."]
  - parameter: error bars: standard deviation within annuli divided by sqrt of number of independent beams [Radial profiles: "Error bars are estimated from the standard deviations of the emission within the annuli, divided by the square root of the number of independent beams across the azimuthal range."]
  - validation: compared with GoFish stacking-based radial profiles; agreement outside one beam major axis, stacking underestimates inner regions [Radial profiles with GoFish: "For radii larger than the beam major axis, the agreement between the two methods is remarkable"]
- result: 12CO 3-2 line flux (text value) = 12.3 ± 0.1 Jy km/s [Line fluxes: "the bright $^{12}$CO 3-2 line ($12.3\pm0.1\,$Jy km s$^{-1}$) and the faint c-C$_3$H$_2$ 3$_{21}$-2$_{12}$ line ($60\pm14$ mJy km s$^{-1}$)"]
- result: 12CO 3-2 line flux (Table 2) = 12421 ± 147 mJy km/s [Table 2: "345.7959 | nat | 0.11$''$$\times$0.10$''$ (90.3$^\circ$) | 0.42 | 1.1 | 12421 | 147 |"]
- result: 12CO 2-1 line flux = 6109 ± 26 mJy km/s [Table 2: "230.5380 | r=0 | 0.37$''$$\times$0.33$''$ (67.1$^\circ$) | 0.09 | 4.1 | 6109 | 26 |"]
- result: 13CO 2-1 line flux = 1846 ± 14 mJy km/s [Table 2: "220.3986 | r=0 | 0.39$''$$\times$0.35$''$ (69.6$^\circ$) | 0.19 | 3.0 | 1846 | 14 |"]
- result: C18O 2-1 line flux = 465 ± 9 mJy km/s [Table 2: "219.5603 | r=0 | 0.39$''$$\times$0.35$''$ (68.3$^\circ$) | 0.19 | 2.4 | 465 | 9 |"]
- result: H2CO 3_03-2_02 line flux = 710 ± 7 mJy km/s [Table 2: "218.2221 | r=0 | 0.40$''$$\times$0.35$''$ (69.0$^\circ$) | 0.39 | 1.5 | 710 | 7 |"]
- result: H2CO 3_21-2_20 line flux = 53 ± 12 mJy km/s [Table 2: "218.7600 | nat | 0.57$''$$\times$0.52$''$ (100.8$^\circ$) | 0.39 | 1.2 | 53 | 12 |"]
- result: C2H J=7/2-5/2 F=4-3 line flux = 741 ± 12 mJy km/s [Table 2: "262.0042 | r=0 | 0.39$''$$\times$0.32$''$ (107.7$^\circ$) | 0.16 | 3.0 | 741 | 12 |"]
- result: C2H J=7/2-5/2 F=3-2 line flux = 586 ± 14 mJy km/s [Table 2: "262.0064 | r=0 | 0.39$''$$\times$0.32$''$ (107.7$^\circ$) | 0.16 | 3.0 | 586 | 14 |"]
- result: C2H J=5/2-3/2 F=3-2 line flux (half of the line covered, corrected assuming symmetry) = 603 ± 17 mJy km/s [Table 2: "262.0648 | r=0 | 0.39$''$$\times$0.32$''$ (107.7$^\circ$) | 0.16 | 3.0 | 603$^d$ | 17 |"]
- result: C2H J=7/2-5/2 total line flux = ~1327 ± 18 mJy km/s [C/O ratio: "with a total flux of the $J$=$\frac{7}{2}$-$\frac{5}{2}$ transition of $\sim1327\pm18\,$mJy km s$^{-1}$"]
- result: c-C3H2 3_21-2_12 line flux = 60 ± 14 (text); 11 (Table 2) mJy km/s [Line fluxes: "the bright $^{12}$CO 3-2 line ($12.3\pm0.1\,$Jy km s$^{-1}$) and the faint c-C$_3$H$_2$ 3$_{21}$-2$_{12}$ line ($60\pm14$ mJy km s$^{-1}$)"]
- result: H13CN 3-2 line flux = 326 ± 17 mJy km/s [Table 2: "259.0117 | r=0 | 0.39$''$$\times$0.32$''$ (107.1$^\circ$) | 0.33 | 1.9 | 326 | 17 |"]
- result: HC15N 3-2 line flux = 197 ± 16 mJy km/s [Table 2: "258.1571 | nat | 0.56$''$$\times$0.46$''$ (100.6$^\circ$) | 0.33 | 1.7 | 197 | 16 |"]
- result: DCN 3-2 line flux = 209 ± 11 mJy km/s [Table 2: "217.2386 | r=0 | 0.40$''$$\times$0.35$''$ (70.8$^\circ$) | 0.39 | 1.7 | 209 | 11 |"]
- result: HCO+ 4-3 line flux = 5199 ± 122 mJy km/s [Table 2: "356.7342 | nat | 0.21$''$$\times$0.18$''$ (73.1$^\circ$) | 0.21 | 3.3 | 5199 | 122 |"]
- result: H13CO+ 3-2 line flux = 344 ± 12 mJy km/s [Table 2: "260.2553 | r=0 | 0.39$''$$\times$0.32$''$ (108.8$^\circ$) | 0.16 | 3.0 | 344 | 12 |"]
- result: CS 5-4 line flux = 450 ± 6 mJy km/s [Table 2: "244.9355 | r=0 | 0.42$''$$\times$0.34$''$ (108.8$^\circ$) | 1.38 | 0.9 | 450 | 6 |"]
- result: SO 7_6-6_5 line flux 3-sigma upper limit = <27 ± not stated mJy km/s [Table 2: "261.8436 | nat | 0.56$''$$\times$0.44$''$ (103.6$^\circ$) | 1.38 | 1.1 | $<$27$^{c}$ | ... |"]
- result: SO 6_6-5_5 line flux 3-sigma upper limit = <52 ± not stated mJy km/s [Table 2: "258.2558 | nat | 0.56$''$$\times$0.47$''$ (104.4$^\circ$) | 1.38 | 1.0 | $<$52$^{c}$ | ... |"]
- result: CH3OH 10_2-9_3 (A+) line flux 3-sigma upper limit = <32 ± not stated mJy km/s [Table 2: "232.4185 | nat | 0.53$''$$\times$0.50$''$ (96.7$^\circ$) | 1.45 | 0.6 | $<$32$^{c}$ | ... |"]
- result: CH3OH 5_1-4_1 (A-) line flux 3-sigma upper limit = <62 ± not stated mJy km/s [Table 2: "243.9157 | nat | 0.60$''$$\times$0.49$''$ (107.0$^\circ$) | 1.38 | 0.7 | $<$62$^{c}$ | ... |"]
- result: c-C3H2 7_16-7_07 line flux 3-sigma upper limit = <29 ± not stated mJy km/s [Table 2: "218.7327 | nat | 0.57$''$$\times$0.52$''$ (100.8$^\circ$) | 1.00 | 0.9 | $<$29$^{c}$ | ... |"]
- limitation (authors): Literature C/O models are tuned for disks without large cavities; a PDS 70-specific forward model is needed [C/O ratio: "However, we note that all these models have been fine tuned for disks that do not exhibit a large cavity, as is the case for PDS 70."]
- limitation (authors): Fractionation conclusions depend on assumed uniform carbon fractionation [Deuteration and N fractionation: "We thus caution that our conclusions about deuteration and nitrogen fractionation may be affected by the carbon fractionation profile, were this not uniform"]
- limitation (authors): Long-baseline (0.1'') data not yet taken; resolution only ~50 au [Observations and data reduction: "for which the long baseline data have not been taken yet."]
- not stated (card): Image size and cell size for continuum and every line cube; Multiscale scales and clean thresholds/niter per line cube; Line-free channels and spw handling used in uvcontsub; Keplerian mask parameters (mask radii, velocity tolerance, per-line settings); Per-EB flux-scale factors found with gaincal and the Band 3/Band 7 calibrator flux values; Amplitude self-cal solution interval details and which…

### 2019ApJ...873...73Z: An Ordered Envelope-Disk Transition in the Massive Protostellar Source G339.88-1.26 (2019; star_formation; observational_alma_primary)
- question: Does the massive protostar G339.88-1.26 show an ordered transition from an infalling-rotating envelope to a Keplerian disk through a centrifugal barrier, with changes in molecular line emission, as in low-mass star formation (Core Accretio…
- step 3: Moment maps, PV diagrams, spectra to identify rotation and centrifugal barrier
  - method: PV diagrams along cut at P.A.=20 deg perpendicular to SiO jet; centrifugal barrier radius and velocity read from most blue/red-shifted offset emission; mass from r v^2/(2G) [4.1 Velocity Structure: "in Figure [6](#fig:pvdiagram) we show the position-velocity (PV) diagrams of these molecular line emissions, along a cut passing through the continuum peak and perpendicular to the SiO jet (i.e., $\mathrm{P.A.}=20^\circ$)."]
  - assumption: Disk mass neglected for Keplerian curve; inclination i defined edge-on = 0 [4.1 Velocity Structure: "assuming a negligible disk mass"]
  - validation: Comparison with SED-fit mass 12-16 Msun [4.1 Velocity Structure: "The estimated dynamical mass is roughly consistent with the mass estimate of $12-16\:M_\odot$ based on SED fitting ((cite: Liu19))."]
- step 4: Kinematic model of infalling-rotating envelope plus Keplerian disk
  - method: Grid over i (0-40 deg, step 10), r_CB/d (0.1-0.4", step 0.05"), v_CB cos i (3-8 km/s, step 1); best fit by eye against PV diagrams [4.2 Kinematic Model of the Rotating Env…: "and approximately determine the best-fit model by eye (given the approximate nature of the modeling)."]
  - parameter: h(r)=0.2r; envelope rho~r^-1.5; disk rho~r^-2.5; r_out/d=0.8" [4.2 Kinematic Model of the Rotating Env…: "We assume the envelope has a height of $h(r)=0.2r$ on each side of the mid-plane, and the density distribution follows $\rho(r)\propto r^{-1.5}$."]
  - assumption: Optically thin emission, universal excitation [4.2 Kinematic Model of the Rotating Env…: "For simplicity, we assume the emissions are optically thin and the excitation conditions are universal across the region."]
  - fitting: Manual grid comparison by eye, no sampler [4.2 Kinematic Model of the Rotating Env…: "approximately determine the best-fit model by eye"]
  - validation: Alternative pure Keplerian disk model fit (m*=23 Msun) rejected [10 Appendix: "The best-fit model shown in Appendix Figure [21](#fig:model_disk) (solid contours) has a protostellar mass of $m_*=23~M_\odot$."]
- result: Centrifugal barrier radius = 530 ± ±110 au [4.1 Velocity Structure: "$r_\mathrm{CB}/d=0.25\ensuremath{''}\pm0.05\ensuremath{''}$, i.e., $r_\mathrm{CB}=530\pm110~\mbox{au}$"]
- result: Centrifugal barrier velocity = 6/cos i ± ±1 km/s [4.1 Velocity Structure: "$v_\mathrm{CB}=6\pm1~\mbox{km s}^{-1}/\cos i$"]
- result: Central (dynamical) mass = 11 ± +6/-5 Msun [4.1 Velocity Structure: "$m_{*d}=r_\mathrm{CB}v_\mathrm{CB}^2/(2G)=11^{+6}_{-5}~M_\odot/\cos^2 i$"]
- result: Best-fit inclination = 10 ± not stated deg [4.2 Kinematic Model of the Rotating Env…: "The best-fit model has an inclination angle of $i=10^\circ$"]
- result: Inner radius of disk for SO2/H2S = 40 ± not stated au [4.2 Kinematic Model of the Rotating Env…: "we estimate $r_\mathrm{in}/d=0.02\ensuremath{''}$, i.e. $r_\mathrm{in}=$40 au"]
- result: Pure Keplerian disk fit mass = 23 ± not stated Msun [10 Appendix: "has a protostellar mass of $m_*=23~M_\odot$"]
- limitation (authors): Model is simple and illustrative; geometry, abundance and excitation simplified [4.3 The Model Caveats: "We note that the model presented above is only a simple example that is designed to be illustrative."]
- limitation (authors): Resolution too low to get detailed disk rotation profile [4.1 Velocity Structure: "it is difficult to obtain the detailed rotation profile in the disk with the current angular resolution of the data."]
- not stated (card): CASA version and pipeline version; Line-free channels and continuum subtraction method; Clean threshold, cell size, image size, masks, deconvolver; Flux scale uncertainty and calibrator flux values; How PV cuts and moment maps were made (clipping, widths); Details of model PV rendering and intensity comparison (by eye); Data resolution/spectral setup of spectral windows

### 2025ApJ...985..166K: Early Planet Formation in Embedded Disks (eDisk). XXI. Limited Role of Streamers in Mass Supply to the Disk in the Class 0 Protostar IRAS 16544-1604 (2025; star_formation; observational_alma_primary)
- question: What mass do streamers supply to the disk of the Class 0 protostar IRAS 16544-1604, compared with the extended envelope and the parental dense core?
- step 6: Estimate B-field strength and mass-to-flux ratio
  - method: DCF method and the Skalidis formulation using the non-thermal line width, the POL-2 angular dispersion and mean density; mass-to-flux ratio from mean surface density [3.1.3 B-field strength: "We adopt the Davis-Chandrasekhar-Fermi (DCF) method (cite: 1951Davis; 1953Chandrasekhar)"] [3.1.3 B-field strength: "The dimensionless mass-to-flux ratio ($\mu_\mathrm{pos}$) of the dense core on the plane of sky is derived as"]
  - parameter: sigma_NT 0.18-0.20 km/s; sigma_theta 7-13 deg; xi = 0.5; mean density (6.1-7.1)e-20 g cm-3 [3.1.3 B-field strength: "and it is 0.18–0.20 km s$^{-1}$"] [3.1.3 B-field strength: "(6.1–7.1)$\times$10$^{-20}$ g cm$^{-3}$"]
  - assumption: Core depth equals its 850 um continuum diameter of 140'' [3.1.3 B-field strength: "we assume the depth of the dense core to also be 140$\ensuremath{''}$"]
  - assumption: Surface density from core plus central protostellar mass within a 60'' box [3.1.3 B-field strength: "divided by the core area within a box of 60$\ensuremath{''}$ from the protostar"]
  - validation: Two formulations (DCF and Skalidis) compared [3.1.3 B-field strength: "the magnetic field strength in the dense core is estimated to be 23–37 $\mu$G"]
- step 7: Identify streamers and compare with UCM infall trajectories
  - method: Inspect ALMA-only channel maps and moment 0 maps, overplot UCM free-fall trajectories, and check position-velocity diagrams cut along the trajectories [3.2.1 Spatial and velocity structures o…: "Blue and red lines in Figure [4](#fig_almamom0) represent the free-fall trajectories coincident with the elongated structures."] [3.2.1 Spatial and velocity structures o…: "Figure [5](#fig_streamerpv) presents the Position–Velocity (PV) diagrams of the elongated structures cut along the model infalling trajectories."]
  - software: CASA, PVextractor
  - parameter: NW and NNW: i_s = 107 deg, theta_s = -45 deg, r_d = 55 au, M* = 0.14 Msun fixed; theta_0, phi_0 free [3.2.1 Spatial and velocity structures o…: "we fix *i*$_\mathrm{s}$ $=$ 107$\ensuremath{^\circ}$, $\theta_\mathrm{s}$ $=$ $-$45$\ensuremath{^\circ}$, $r_\mathrm{d}$ $=$ 55 au, and $M_*$ $=$ 0.14 $M_\odot$"]
  - parameter: Streamer edges set at 3 sigma in moment 0 maps [3.2.2 Mass infalling rates of streamers: "We set the 3$\sigma$ emissions in the moment 0 maps (Figure [4](#fig_almamom0)) as the edge of the streamers."]
  - assumption: NW and NNW streamers share the disk rotation axis and have centrifugal radius equal to the gas disk radius [3.2.1 Spatial and velocity structures o…: "we assume that their rotational axes are aligned with the disk and that their centrifugal radii are the same as the gas disk radius"]
  - fitting: Visual comparison of all combinations of theta_0 and phi_0, no sampler or likelihood [3.2.1 Spatial and velocity structures o…: "We visually inspect and compare the observed structures with the model trajectories of all combinations of the parameters"]
  - validation: PV diagrams follow the UCM velocities; alternative parameter sets also reproduce the data (degeneracy) [3.2.1 Spatial and velocity structures o…: "These velocity structures are consistent with the UCM model."] [4.1 Degeneracy of the UCM model: "We note that these solutions are not unique because of the projection effect."]
- step 9: Test infall of the extended envelope with a kinematical model
  - method: UCM infalling-rotating envelope with embedded flared Keplerian disk, RADMC-3D C18O LTE image cube, convolved to the feathered beam, PV cuts along disk major and minor axes compared to the feathered data [3.3 Infalling protostellar envelope obs…: "We then perform radiative transfer calculations using RADMC-3D (cite: 2012Dullemond) and generate a model C$^{18}$O image cube of our kinematical model."] [3.3 Infalling protostellar envelope obs…: "The model images are convolved with a Gaussian beam of the same size as that of our feathered map of the C$^{18}$O emission."]
  - software: RADMC-3D, PVextractor
  - parameter: Radial range 1-9000 au, distance 151 pc, stellar mass 0.14 Msun, disk radius 55 au, disk mass 1.0e-2 Msun, envelope mass 0.52 Msun, C18O abundance 1.7e-7 [Table 1: "1-9000 au"] [Table 1: "1.0$\times$10$^{-2}$ $M_\odot$"]
  - parameter: Disk P.A. 45 deg and inclination 73 deg [Table 1: "45$\ensuremath{^\circ}$"] [Table 1: "73$\ensuremath{^\circ}$"]
  - assumption: Isothermal 15 K, LTE, optically thin C18O; dust opacity table of Semenov et al. 2003 [3.3 Infalling protostellar envelope obs…: "For simplicity, the model assumes an isothermal temperature of 15 K as the C$^{18}$O emission in IRAS 16544 is likely optically thin."] [3.3 Infalling protostellar envelope obs…: "Our model adopts the dust opacity table in (cite: 2003Semenov) and the C$^{18}$O abundance of 1.7$\times$10$^{-7}$, assuming LTE condition."]
  - validation: Qualitative agreement of model and observed PV diagrams (diamond shape, minor-axis gradient); axisymmetric model cannot fully explain the intensity distribution [3.3 Infalling protostellar envelope obs…: "The good agreement between the observed and the model velocity structures in the PV diagrams suggests that the extended envelope observed in the feathered map is also infalling."] [3.3 Infalling protostellar envelope obs…: "the observed intensity distribution cannot be fully explained by our axisymmetric envelope model"]
- step 11: Compare streamer infall rate with envelope infall rate and protostellar accretion rate
  - method: Envelope infall rate from JCMT core mass within 4000 au and the free-fall velocity at that radius from the protostellar mass; accretion rate from accretion luminosity: Macc = Lacc R* / (G M*) [4.2 Mass accretion via streamers: "With the dense core mass within a radius of 4000 au measured with JCMT and the free-fall velocity at this radius calculated from the central protostellar mass"] [4.2 Mass accretion via streamers: "The mass accretion rate ($\dot{M}_\mathrm{acc}$) onto the protostar in IRAS 16544 is estimated to be 3.0$\times$10$^{-7}$ $M_\odot$ yr$^{-1}$ from the luminosity of the protostar"]
  - parameter: Lbol = 0.89 Lsun, Lacc = 50% of Lbol, R* = 3 Rsun [4.2 Mass accretion via streamers: "The bolometric luminosity ($L_\mathrm{bol}$) of IRAS 16544 is 0.89 $L_\odot$ (cite: 2023Ohashi)"] [4.2 Mass accretion via streamers: "the stellar radius is 3 $R_\odot$ (cite: 1988Stahler)"]
  - assumption: Accretion luminosity is 50% of the bolometric luminosity [4.2 Mass accretion via streamers: "Assuming that the accretion luminosity is 50$\%$ of the bolometric luminosity (cite: 2008Dunham; 2008Antoniucci)"]
  - validation: Compared with the theoretical isothermal-collapse rate of ~2e-6 Msun/yr and other Class 0 protostars [4.2 Mass accretion via streamers: "the theoretically expected mass infalling rate of $\sim$2$\times$10$^{-6}$ $M_\odot$ yr$^{-1}$ in a collapsing isothermal and spherical dense core"]
- result: Mean volume density of the dense core = (6.1-7.1)e-20 ± range g cm-3 [3.1.3 B-field strength: "(6.1–7.1)$\times$10$^{-20}$ g cm$^{-3}$"]
- result: B-field strength (DCF) = 34-76 ± range uG [3.1.3 B-field strength: "the magnetic field strength is estimated to be 34–76 $\mu$G"]
- result: B-field strength (Skalidis et al. formulation) = 23-37 ± range uG [3.1.3 B-field strength: "the magnetic field strength in the dense core is estimated to be 23–37 $\mu$G"]
- result: Mass-to-flux ratio (DCF and Skalidis) = 1.5-3.8 (DCF); 3.1-5.7 (Skalidis) ± range dimensionless [3.1.3 B-field strength: "estimated to be 1.5–3.8 with the DCF method and 3.1-5.7 with the method in (cite: 2021Skalidis)"]
- result: UCM theta_0, phi_0 for the NW streamer = 20 deg, -10 deg ± not stated deg [3.2.1 Spatial and velocity structures o…: "the model trajectory with $\theta_0$ of 20$\ensuremath{^\circ}$ and $\phi_0$ of $-$10$\ensuremath{^\circ}$ can match the NW elongated structure and that with $\theta_0$ of 70$\ensuremath{^\circ}$ and $\phi_0$ of $-$120$\ensuremath{^\circ}$ can match the NNW elongated structure"]
- result: UCM theta_0, phi_0 for the NNW streamer = 70 deg, -120 deg ± not stated deg [3.2.1 Spatial and velocity structures o…: "the model trajectory with $\theta_0$ of 20$\ensuremath{^\circ}$ and $\phi_0$ of $-$10$\ensuremath{^\circ}$ can match the NW elongated structure and that with $\theta_0$ of 70$\ensuremath{^\circ}$ and $\phi_0$ of $-$120$\ensuremath{^\circ}$ can match the NNW elongated structure"]
- result: Total streamer mass and fraction of the dense core mass (9000 au box) = ~7.5e-3 Msun, ~2% ± not stated Msun; percent [4.2 Mass accretion via streamers: "The total mass of the three streamers is estimated to be $\sim$7.5$\times$10$^{-3}$ $M_\odot$ and is only $\sim$2$\%$ of the total mass of the dense core"]
- result: Streamer mass fraction of core mass within 4000 au = ~6 ± not stated percent [4.2 Mass accretion via streamers: "the mass of the streamers is still only $\sim$6$\%$ of the total core mass"]
- result: Envelope mass infall rate (core mass within 4000 au) = 1 to 5e-6 ± range Msun/yr [4.2 Mass accretion via streamers: "the mass infalling rate in the protostellar envelope is estimated to be 1 to 5$\times$10$^{-6}$ $M_\odot$ yr$^{-1}$ in IRAS 16544"]
- result: Mass accretion rate onto the protostar = 3.0e-7 ± not stated Msun/yr [4.2 Mass accretion via streamers: "is estimated to be 3.0$\times$10$^{-7}$ $M_\odot$ yr$^{-1}$ from the luminosity of the protostar"]
- limitation (authors): UCM trajectories are degenerate, so 3D lengths and infall rates are uncertain by up to a factor of four [4.1 Degeneracy of the UCM model: "the mass infalling rates estimated with these different trajectories only vary within a factor of four"]
- limitation (authors): More, unidentified streamers may exist [4.2 Mass accretion via streamers: "We note that there could be more, unidentified streamers existing in the dense core of IRAS 16544."]
- limitation (authors): Axisymmetric envelope model does not fully explain the intensity distribution [3.3 Infalling protostellar envelope obs…: "the observed intensity distribution cannot be fully explained by our axisymmetric envelope model"]
- not stated (card): Calibration details: pipeline versions and CASA version used for calibration of each eDisk, FAUST and DDT execution block, and any self-calibration applied to the line data; Which spectral windows and channel ranges were extracted with mstransform, and the line-free channels used for uvcontsub; tclean deconvolver, cell size, image size, field/phase center, niter and cleaning threshold, and weight…

### 2020ApJ...904..185O: Substructures in the Disk-forming Region of the Class 0 Low-mass Protostellar Source IRAS 16293-2422 Source A on a 10 au Scale (2020; star_formation, protoplanetary_disks, astrochemistry; observational_alma_primary)
- question: What are the substructures, kinematic structures, and gas-temperature distribution in the disk-forming region of the Class 0 protostellar source IRAS 16293-2422 Source A on a 10 au scale?
- step 3: Model the kinematic structure of the circummultiple structure using C17O (J=2-1)
  - method: Extract PV diagrams centered on the continuum intensity centroid and fit 3D Keplerian disk and infalling-rotating envelope (IRE) models using reduced chi-squared tests on the blue-shifted component [4.3. Kinematic Structure of the C 17 O …: "We here use three-dimensional physical models of a flat disk/envelope with the Keplerian motion or the infalling-rotating motion."] [Appendix A. Reduced Chi-Squared Test fo…: "We calculate the reduced χ 2 value ( χ 2 /DOF), which is the sum of the square of the difference between the modeled and observed PV diagrams along the envelope mid-plane direction at each pixel normalized by the square of the rms in the observation"]
  - parameter: Inner radius = 50 au (or r_CB = 50 au), outer radius = 300 au, P.A. = 50 deg, V_sys = 3.9 km/s, flared angle = 30 deg, intrinsic FWHM = 1 km/s, emissivity proportional to r^-1.5 [4.3.1. Keplerian Model for the C 17 O L…: "Here, the inner and outer radii of the model are fixed to be 50 au and 300 au according to the observed molecular distribution."] [Figure 8 caption: "The emissivity in the model is assumed to be proportional to r − 1 . 5 , where r denotes the distance from the center of gravity, and is to be zero for r < 50 au and r > 300 au. The scale height of the disk is assumed to increase as increasing the distance from the center of gravity with the flared angle of 30 ◦ ."]
  - assumption: Optically thin line emission, no radiative transfer, ballistic motion conserving energy and specific angular momentum for IRE model [4.3. Kinematic Structure of the C 17 O …: "In these models, the line emission is assumed to be optically thin, and the radiation transfer is not considered."] [4.3.2. Infalling-Rotating Envelope Mode…: "In this model, the velocity field is approximated by the ballistic motion. The energy and specific angular momentum of the gas is assumed to be conserved"]
  - fitting: Grid search minimizing reduced chi-squared (chi^2/DOF) over central mass and inclination angle; parameter ranges defined where reduced chi^2 increases by 1 [Appendix A. Reduced Chi-Squared Test fo…: "the parameter ranges are determined from the range where the reduced χ 2 value increases by 1."]
  - validation: Visual comparison of model contours on PV diagrams along 6 position angles [4.3.1. Keplerian Model for the C 17 O L…: "As depicted in Figure 8(a), the PV diagram along the envelope mid-plane direction is reasonably reproduced. However, the PV diagrams along the other directions are not well explained"]
- step 4: Model the kinematic structure of the circumstellar disk around protostar A1 using H2CS
  - method: Extract PV diagrams centered on continuum peak A1 and fit 3D Keplerian disk and infalling-rotating envelope models to H2CS (7_4,3-6_4,2, 7_4,4-6_4,3) along P.A. 50 deg and 140 deg using reduced chi-squared tests [4.4.2. Keplerian Model for the H 2 CS L…: "First, we perform the χ 2 test for the Keplerian model and the H 2 CS (7 4 , 3 –6 4 , 2 , 7 4 , 4 –6 4 , 3 ) line, as the C 17 O case in Section 4.3.1"] [Appendix C. Analysis of H 2 CS: "In contrast to the C 17 O analysis, we use the two PV diagrams of the H 2 CS (7 4 , 3 –6 4 , 2 , 7 4 , 4 –6 4 , 3 ) line prepared along the disk mid-plane direction (P.A. 50 ◦ ) and the direction perpendicular to it (P.A. 140 ◦ ), and use both the red- and blue-shifted components with the velocity range from − 6 km s …"]
  - parameter: V_sys = 2.5 km/s, outer radius = 30 au, inner radius = 0.56 au (1 pixel) for Keplerian or r_CB = 5, 10, 20 au for IRE, P.A. = 50 deg, flared angle = 30 deg, intrinsic FWHM = 1 km/s, emissivity proportional to r^-1.5 [4.4.2. Keplerian Model for the H 2 CS L…: "where the systemic velocity is 2.5 km s − 1 . The inner and outer radii of the model are fixed to be ∼ 0 au and 30 au according to the observed molecular distribution, respectively."] [Figure 10 caption: "The intensity in the models is convolved with the synthesized beam size for each molecular line (Table 1) and the Gaussian line profile with the intrinsic line width (FWHM) of 1 km s − 1 ."]
  - assumption: Optically thin line emission, center of gravity at continuum peak A1 [Figure 10 caption: "The center of gravity for the model is assumed to be at the continuum peak A1"]
  - fitting: Grid search minimizing reduced chi-squared over central mass, inclination angle, and (for IRE) centrifugal barrier radius (5676 pixels) [Table A4: "The pixels with the angular offset from − 0 ′′ . 4 to +0 ′′ . 4 and the velocity from − 6 km s − 1 to +11 km s − 1 are taken into account. 5676 pixels are used for the calculation."]
  - validation: Comparison of Keplerian vs IRE models across multiple P.A.s and H2CS transitions (7_0,7-6_0,6 and 7_2,5-6_2,4), and checking PV diagrams centered on A2, A3, A4 [4.4.3. Infalling-Rotating Envelope Mode…: "As the result, we find that the kinematic structure traced by H 2 CS is worse reproduced by the infalling-rotating envelope model than by the Keplerian model"]
- result: Central mass of circummultiple structure (C17O Keplerian model) = 2.0 ± 1.5 - 2.5 M_sun [4.3.1. Keplerian Model for the C 17 O L…: "the central mass is 2.0 M ⊙ and the inclination angle is 70 ◦ , as shown in Table 4."]
- result: Inclination angle of circummultiple structure (C17O Keplerian model) = 70 ± 66 - 90 deg [4.3.1. Keplerian Model for the C 17 O L…: "the central mass is 2.0 M ⊙ and the inclination angle is 70 ◦ , as shown in Table 4."]
- result: Central mass of circummultiple structure (C17O infalling-rotating envelope model) = 1.0 ± 0.6 - 1.2 M_sun [4.3.2. Infalling-Rotating Envelope Mode…: "the protostellar mass is 1.0 M ⊙ and the inclination angle is 80 ◦ ."]
- result: Inclination angle of circummultiple structure (C17O infalling-rotating envelope model) = 80 ± 70 - 90 deg [4.3.2. Infalling-Rotating Envelope Mode…: "the protostellar mass is 1.0 M ⊙ and the inclination angle is 80 ◦ ."]
- result: Central mass of circumstellar disk around A1 (H2CS Keplerian model) = 0.4 ± 0.4 - 0.8 M_sun [4.4.2. Keplerian Model for the H 2 CS L…: "We obtain the following best fit parameters: the central mass is 0.4 M ⊙ and the inclination angle is 60 ◦ , where the systemic velocity is 2.5 km s − 1 ."]
- result: Inclination angle of circumstellar disk around A1 (H2CS Keplerian model) = 60 ± 40 - 70 deg [4.4.2. Keplerian Model for the H 2 CS L…: "We obtain the following best fit parameters: the central mass is 0.4 M ⊙ and the inclination angle is 60 ◦ , where the systemic velocity is 2.5 km s − 1 ."]
- result: Central mass of circumstellar structure around A1 (H2CS infalling-rotating envelope model) = 0.20 ± 0.15 - 0.25 M_sun [4.4.3. Infalling-Rotating Envelope Mode…: "We obtain the following best fit parameters: the central mas is 0.20 M ⊙ and the inclination angle is 70 ◦ , where the systemic velocity is 2.5 km s − 1 ."]
- result: Inclination angle of circumstellar structure around A1 (H2CS infalling-rotating envelope model) = 70 ± 60 - 90 deg [4.4.3. Infalling-Rotating Envelope Mode…: "We obtain the following best fit parameters: the central mas is 0.20 M ⊙ and the inclination angle is 70 ◦ , where the systemic velocity is 2.5 km s − 1 ."]
- limitation (authors): Extended structures such as the bridge between Source A and Source B and emission near the systemic velocity suffer from resolving-out effects. [3.1. 1.3 mm Continuum: "Although IRAS 16293–2422 is known to have a bridge structure connecting between Source A and Source B (e.g. Jørgensen et al. 2016; van der Wiel et al. 2019), such a structure is missing in our observation probably due to the resolving-out effect."]
- limitation (authors): C17O (J=2-1) suffers from cold foreground self-absorption near the systemic velocity and line contamination from (CH3)2CO, CH2DOH, and/or an unidentified line at high velocity shifts. [3.2.1. C 17 O: "These are contaminations of the (CH 3 ) 2 CO (18 5 , 13 –17 6 , 12 EE and 18 6 , 13 –17 5 , 12 EE at 224.700 GHz) transitions, the CH 2 DOH (7 2 , 6 –7 1 , 7 , e 1 at 224.701 GHz; 20 1 , 19 –20 0 , 20 , e 1 at 224.725 GHz) lines, and/or an unidentified line. An absorption feature of the C 17 O line is seen around the …"]
- limitation (authors): Simple 3D Keplerian and infalling-rotating envelope models assume optically thin emission without radiative transfer and cannot fully reproduce the complex kinematic substructures, resulting in large reduced chi-squared values. [4.3. Kinematic Structure of the C 17 O …: "In these models, the line emission is assumed to be optically thin, and the radiation transfer is not considered."]
- not stated (card): CASA version and pipeline version used for calibration and imaging; Table 1 is missing from the PDF text (contains rest frequencies, beam sizes, and upper state energies for C17O and H2CS lines); Exact frequency ranges of the line-free channels totaling 0.3 GHz used for continuum imaging and uv-continuum subtraction; CLEAN stopping threshold, niter, image pixel dimensions, and masking strategy; V…

### 2013ApJ...774...16R: A Spatially Resolved Vertical Temperature Gradient in the HD 163296 Disk (2013; protoplanetary_disks; archival_reuse)
- question: Can the spatial asymmetry of CO lines in the HD 163296 disk be explained by a vertical temperature gradient, and are the data sensitive to sub-Keplerian gas velocities?
- step 1: Image line cubes
  - method: CLEAN with natural weighting and per-channel Keplerian-pattern masks [3 Results: "we developed a CLEAN mask based on the emission pattern expected from a disk in Keplerian rotation"]
  - software: CASA
  - parameter: mask smoothing sigma = 0.7 arcsec [3 Results: "convolved with a fixed Gaussian kernel ($\sigma = 0.7\ensuremath{''}$)"]
  - validation: SNR per channel improves by ~2-3 vs SV reference maps; intensities agree with SMA within 10% [3 Results: "the signal-to-noise ratio per channel improves by a factor of $\sim$2–3"]
- step 2: Toy double-cone model of emitting surface
  - method: Rotating double cone with opening angle psi; compare isovelocity contours with channel maps [4.1 A Toy Model: "The toy model that we propose is a differentially rotating double cone, oriented along the $z$ axis with an opening angle $\psi \in (0,\pi/2)$"]
  - parameter: psi ~15 deg [4.1 A Toy Model: "double cone structure with $\psi \sim 15^\circ$"]
  - assumption: Keplerian rotation, no v_z [4.1 A Toy Model: "if this near cone is in circular, Keplerian rotation"]
  - fitting: qualitative comparison [4.2.1 A Pedagogical Structure: "Qualitatively, this model does an excellent job of producing both the morphological and brightness asymmetries noted in §[3](#sec:results)."]
  - validation: visual overlay on channel maps [4.1 A Toy Model: "Figure [\[fig:cone_chmaps\]](#fig:cone_chmaps) shows the velocity pattern of this toy model overlaid on the regridded channel maps"]
- step 4: Test sensitivity to gas velocity field
  - method: Models with velocity from vertical geometry, pressure gradient, self-gravity separately and combined; compare to Keplerian [4.3 A Closer Look at the Gas Velocities: "In order to disambiguate these three effects, we will consider separately the three force terms in Equation [\[eq:fullF\]](#eq:fullF) that determine $v$"]
  - software: LIME
  - parameter: LIME only for level populations; images by own ray tracing on interpolated 2D grid; Poisson equation on fixed grid [4.3 A Closer Look at the Gas Velocities: "for these models we only used LIME to calculate the non-LTE level populations."]
  - assumption: circular orbits; self-gravity omitted from hydrostatic density [4.3 A Closer Look at the Gas Velocities: "throughout our analysis we have only considered circular orbits"]
  - validation: Differences significant at >=3 sigma across many channels [4.3 A Closer Look at the Gas Velocities: "The impact of these changes to the velocity field are significant at the $\gtrsim 3 \sigma$ level across many channels."]
- result: 12CO 3-2 integrated intensity = 109 ± ±11 Jy km/s [Table 1: "| Integrated intensity \[Jy km s$^{-1}$\] | $109\pm11$ | $46\pm5$ | $18\pm2$ | $5.8\pm 0.6$ |"]
- result: 12CO 2-1 integrated intensity = 46 ± ±5 Jy km/s [Table 1: "| Integrated intensity \[Jy km s$^{-1}$\] | $109\pm11$ | $46\pm5$ | $18\pm2$ | $5.8\pm 0.6$ |"]
- result: 13CO 2-1 integrated intensity = 18 ± ±2 Jy km/s [Table 1: "| Integrated intensity \[Jy km s$^{-1}$\] | $109\pm11$ | $46\pm5$ | $18\pm2$ | $5.8\pm 0.6$ |"]
- result: C18O 2-1 integrated intensity = 5.8 ± ±0.6 Jy km/s [Table 1: "| Integrated intensity \[Jy km s$^{-1}$\] | $109\pm11$ | $46\pm5$ | $18\pm2$ | $5.8\pm 0.6$ |"]
- result: Cone angle of tau=1 surface = ~15 ± not stated deg [abstract: "make an angle of $\sim 15^\circ$ with respect to the disk midplane"]
- result: Velocity-field difference distinguishable by data = >~5 ± not stated percent [abstract: "a fractional difference in the bulk gas velocity field of $\gtrsim 5$%"]
- limitation (authors): Models are degenerate, not unique or optimal; systematic residuals at large radii [4.2 Physical Model Analysis: "the exact structures we present are neither unique nor necessarily optimal"]
- limitation (authors): Band 7 sky frequency in SV measurement set incorrect [Footnote 2: "The transformation to the absolute sky frequency in the Band 7 measurement set provided by the SV team is incorrect."]
- not stated (card): CASA version; Self-calibration solution intervals and reference antenna; Number of CLEAN iterations/threshold, cell and image size; Line-free channels for continuum subtraction; Stellar mass and distance values adopted; Exact model grid and LIME settings (photons, grid points); Model visibility sampling and chi2 values; How the 'central 49 channels' and mask parameters (phase offset, systemic vel…

### 2014ApJ...786..114L: ALMA Results of the Pseudodisk, Rotating Disk, and Jet in the Continuum and HCO<SUP>+</SUP> in the Protostellar System HH 212 (2014; star_formation, protoplanetary_disks; observational_alma_primary)
- question: Does the Class 0 protostar HH 212 host a rotationally supported disk inside an infalling flattened envelope (pseudodisk), and what are the properties of the HCO+ jet?
- step 2: Analyze HCO+ kinematics (spectra, channel maps, PV diagrams)
  - method: Velocity split into 3 ranges; spectrum, PV diagrams along the equator and the jet axis compared with infall and Keplerian signatures [3.2.1 Flattened Envelope, Disk, and Out…: "we divide the velocity into 3 ranges: $|V_\textrm{\scriptsize off}| \leq 1$ km s$^{-1}$, $1\leq |V_\textrm{\scriptsize off}| \leq 2$ km s$^{-1}$, and $2\leq |V_\textrm{\scriptsize off}| \leq 3$ km s$^{-1}$."]
- step 3: Spatio-kinematic radiative transfer model of envelope and disk
  - method: Model with a flattened envelope (power laws) and a disk (Keplerian) with a density jump m at the interface, LTE radiative transfer, channel maps resampled with the observed uv coverage; fit to continuum and HCO+ simultaneously [4 Model of the envelope and disk: "We first calculate the channel maps with radiative transfer and next map them with the observed $uv$-coverage and velocity resolutions."]
  - parameter: 7 free parameters: T0, n0, vr0, vphi0, m, q, x(HCO+) [4 Model of the envelope and disk: "In our model, there are 7 free parameters, with their best-fit values of $T_\textrm{\scriptsize 0}^e \sim 45$ K"]
  - parameter: Disk outer radius 0.3 arcsec (120 AU), half thickness 0.1 arcsec, inner radius 0.01 arcsec; envelope outer radius 5 arcsec [4 Model of the envelope and disk: "It is assumed to be a flat disk with an outer radius of $r_D=$$0^{\prime\prime}_{^\textrm{.}}3$ (120 AU) and a constant half thickness of $H=$$0^{\prime\prime}_{^\textrm{.}}1$ (40 AU)"]
  - assumption: Dust and gas same temperature; LTE; kappa from Beckwith1990 with beta=1; thermal line width only; free-fall infall and constant specific angular momentum in the envelope [4 Model of the envelope and disk: "For simplicity, dust and HCO$^+$ gas are assumed to have the same temperature."] [4 Model of the envelope and disk: "The line width of the HCO$^+$ emission is assumed to be given by the thermal line width only."]
  - fitting: Best-fit by matching the continuum map, HCO+ channel maps, spectrum and PV diagram; no formal sampler stated [4 Model of the envelope and disk: "The best-fit parameters are obtained by matching the continuum map, HCO$^+$ channel maps, spectrum, and PV diagram in our model to those in the observations"]
  - validation: Compared with model maps; extended envelope effect mimicked by a Gaussian subtracted from the model spectrum [4 Model of the envelope and disk: "After we subtract this Gaussian component from our model spectrum (red spectrum), we can obtain a spectrum (green spectrum) that matches the observed spectrum toward the center at low velocity"]
- step 4: Consistency checks and derived masses
  - method: Keplerian radius, isothermal shock Mach number vs density jump, stellar and disk masses, accretion rate and luminosity [4.1 Consistency Checks: "Therefore, $m\sim 8.0$, the same as that obtained from our model, and thus the jump condition is self-consistent in our model."]
  - assumption: R* ~ 2 Rsun for accretion luminosity [4.1 Consistency Checks: "Assuming $R_\ast \sim 2 R_\odot$, then $L_\textrm{acc} \sim 14$ L$_\odot$"]
  - validation: Disk mass checked against disk continuum flux assuming optically thin emission [4.1 Consistency Checks: "Assuming that the observed disk continuum emission is optically thin, this mass requires the disk to have a representative temperature of $\sim$ 91 K."]
- result: Density jump m = ~8.0 ± not stated dimensionless [4 Model of the envelope and disk: "$m \sim 8.0$, $q \sim 0.6$, and $x_{\textrm{\scriptsize HCO}^{+}}$ $\sim 10^{-9}$"]
- result: Envelope reference temperature T0 at 1 arcsec = ~45 ± not stated K [4 Model of the envelope and disk: "$T_\textrm{\scriptsize 0}^e \sim 45$ K, $n_\textrm{\scriptsize 0}^e \sim 5\times10^6$ cm$^{-3}$"]
- result: Infall velocity v_r0 at 1 arcsec = ~0.9 ± not stated km/s [4 Model of the envelope and disk: "$v_{r\textrm{\scriptsize 0}}^e \sim 0.9$ km s$^{-1}$, $v_{\phi\textrm{\scriptsize 0}}^e \sim 0.35$ km s$^{-1}$"]
- result: Central stellar mass = ~0.18 ± not stated Msun [4.1 Consistency Checks: "the mass of the central star is found to be $\sim$ 0.18 $M_\odot$"]
- result: Disk mass = ~0.014 ± not stated Msun [4.1 Consistency Checks: "M_D = 1.4m_{\textrm{\scriptsize H}_2} \int^{r_D} 2 \pi r (2 H) n^D dr \sim 0.014 \; M_\odot"]
- result: Flattened envelope mass = ~0.10 ± not stated Msun [4.1 Consistency Checks: "\sim 0.10 \; M_\odot"]
- result: Accretion rate = ~5.0e-6 ± not stated Msun/yr [4.1 Consistency Checks: "\sim 5.0\times 10^{-6} \; M_\odot{}\; \textrm{yr}^{-1}"]
- result: Accretion luminosity = ~14 ± not stated Lsun [4.1 Consistency Checks: "then $L_\textrm{acc} \sim 14$ L$_\odot$, comparable to the bolometric luminosity"]
- result: Keplerian radius = ~0.3 ± not stated arcsec (120 AU) [4.1 Consistency Checks: "the Keplerian radius is found to be $\sim$ $0^{\prime\prime}_{^\textrm{.}}3$"]
- limitation (authors): Disk is not well resolved, so its radius is an upper limit and the temperature index is rough; model is simple and symmetric and excludes outflow, jet and extended envelope. [4 Model of the envelope and disk: "The disk is not well resolved in our observations, especially in the minor axis."]
- not stated (card): CASA version and details of the calibration (bandpass, gain, flux scale, self-calibration); Line-free channels and the continuum subtraction method for HCO+; Cleaning parameters (deconvolver, mask, threshold, cell and image size, robust beyond 'super-uniform'); Radiative transfer code, grid, and the fitting procedure and merit function for the 7 free parameters; HCO+ rest frequency and molecular …

### 2017ApJ...842....8M: A Complete ALMA Map of the Fomalhaut Debris Disk (2017; debris_disks, stellar_physics; observational_alma_primary)
- question: What is the complete millimeter structure of the Fomalhaut outer debris disk (geometry, eccentricity, width, azimuthal structure, apocenter glow), and what is the stellar flux at 1.3 mm?
- step 3: Fit eccentric-ring particle model to visibilities
  - method: 2D model of 10^4 particles with forced/proper eccentricity, random mean anomalies, solved Kepler's equation; binned to image; point-source star added; synthetic visibilities via vissample; chi^2 likelihood; emcee MCMC [3.2 Modeling Approach: "To create our two-dimensional model, we complete this calculation for $10^4$ individual disk particles."]
  - software: ast2body newtonm, vissample, emcee
  - parameter: Free: R_belt, Δa, F_belt, F_star, i, PA, e_f, e_p, ω_f, Δα, Δδ [3.2 Modeling Approach: "we fit for the geometry of the disk (inclination, $i$, and position angle, $PA$), as well as offsets of the stellar position from the pointing center"]
  - assumption: Negligible vertical thickness (opening angle ~1 deg); temperature T ∝ r^-0.5; ω_p random 0 to 2π [3.2 Modeling Approach: "impose a radial temperature profile, $T\propto r^{-0.5}$"]
  - fitting: emcee affine-invariant ensemble sampler, chi^2 likelihood with visibility weights; priors not stated [3.2 Modeling Approach: "This iterative process makes use of the `emcee` Markov Chain Monte Charlo (MCMC) package (cite: for13)."]
  - validation: Reduced chi^2 = 1.1; imaged residuals mostly noise [3.3 Results of Model Fits: "Table [2](#tab:diskpar) presents the best-fit model (reduced $\chi^2 = 1.1$) parameters"]
- result: Belt total flux density = 24.7 ± 0.1 (plus 10% calibration) mJy [3.3 Results of Model Fits: "The total belt flux density determined for the best-fit model is $24.7\pm0.1$ mJy"]
- result: Stellar flux density at 1.3 mm = 0.75 ± 0.02 mJy [Table 2: "$0.75\pm0.02$"]
- result: Belt semi-major axis (inner edge) R_belt = 136.3 ± 0.9 AU [Table 2: "$136.3\pm0.9$"]
- result: Belt FWHM width = 13.5 ± 1.8 AU [Table 2: "$13.5\pm1.8$"]
- result: Inclination = 65.6 ± 0.3 deg [Table 2: "$65.6\pm0.3$"]
- result: Position angle = 337.9 ± 0.3 deg [Table 2: "$337.9\pm0.3$"]
- result: Forced eccentricity = 0.12 ± 0.01 dimensionless [Table 2: "$0.12\pm0.01$"]
- result: Proper eccentricity = 0.06 ± 0.04 dimensionless [4.2.2 Determining the Belt Width: "$\Delta a = 12.2\pm1.6$ AU and $e_p = 0.06\pm0.04$"]
- result: Argument of periastron = 22.5 ± 4.3 deg [Table 2: "$22.5\pm4.3$"]
- result: Range of semi-major axes Δa = 12.2 ± 1.6 AU [Table 2: "$12.2\pm1.6$"]
- result: Fractional width ΔR/R = 0.10 ± 0.01 dimensionless [4.2.2 Determining the Belt Width: "$\Delta R/R = 0.10\pm0.01$"]
- limitation (authors): Resolution (~10 AU) prevents constraints on edge sharpness; Δa and e_p degenerate; large uncertainty on ω from inclination degeneracy [4.2.2 Determining the Belt Width: "we are unable to place any strong constraints on the sharpness of the disk edges."]
- limitation (authors): 2D model ignores vertical structure, which could loosen width constraints [3.2 Modeling Approach: "Adding a vertical component to the model would likely loosen the constraints we are able to place on the width of the belt"]
- not stated (card): CLEAN parameters (cell size, image size, masks, threshold, niter); Mosaic pointing coordinates for the seven fields; Prior ranges and walker/step numbers and burn-in for emcee; Pixel scale, image size and the vertical/radial sampling of the model image and how the primary beam was handled in vissample; Which executions were combined and any relative flux scaling between them; Flux density used fo…

### 2019A&A...629A.136S: A rotating fast bipolar wind and disk system around the B[e]-type star MWC 922 (2019; evolved_stars, stellar_physics; observational_alma_primary)
- question: What are the structure, kinematics and physical conditions of the ionized disk and fast wind at the core of the B[e] star MWC 922, and what is its evolutionary nature?
- step 4: Derive kinematics directly from maps
  - method: Peak separation of red/blue H30α emission and PV cuts; edge-on Keplerian rotation gives central mass; wing width gives wind velocity [3.2 Radio recombination lines: "For an edge-on rotating disk, the velocity gradient observed implies a rotation velocity of $\sim$17 km s$^{-1}$ at a radial distance of about 25 au$\times$$\frac{d}{1.7\,kpc}$."]
  - assumption: edge-on disk, Keplerian rotation, d=1.7 kpc [3.2 Radio recombination lines: "Assuming Keplerian rotation, this implies a value for the central mass of $\sim$8 $M_{\odot}$$\times$$\frac{d}{1.7\,kpc}$"]
- step 5: Model free-free continuum and RRLs with MORELI
  - method: Non-LTE radiative transfer model of bicone disk+slow+fast wind; synthetic visibilities via uv_model using the same UV sampling, imaged identically; compared by eye to data and SED [4 Analysis: "we used our input model and the same UV sampling and weighting of our ALMA observations to generate the synthetic or model visibilities."]
  - software: MORELI, GILDAS MAPPING
  - parameter: θa=60°, θd=6.5°, θw=38°, Rin=29 au, Te=8750 K, Vfast=95 km/s, Vslow=9 km/s, ne=4.3e7 (r/30au)^-2.7 exp(-(θa-θ)/40°) cm^-3 (d=1.7 kpc) [Model results table: "Electron density ($n_{\rm e}$) | 4.3$\times 10^{\rm 7}$($\frac{r}{30{\rm au}}$)$^{-2.7}$exp($-(\theta_a-\theta)/40\ensuremath{^\circ}$)"]
  - assumption: Isothermal, Keplerian disk, rotation also in winds, constant Te, departure coefficients from Storey & Hummer [4 Analysis: "we adopt a constant value of the electron temperature ($T_{\rm e}$) within the disk and within the outflow."]
  - validation: Tested alternative models (no fast-wind rotation, 1/r rotation law, d=3 kpc, parameter ranges) [4 Analysis: "We have also run a model adopting an angular-momentum conservation rotation-law ($V_{\rm rot}$$\propto$1/$r$, not shown)."]
- step 7: Constrain nature of the star
  - method: Compare model central mass and luminosity with HR diagram evolutionary tracks and Lyman-continuum model atmospheres [5.2.1 Position in the HR diagram: "we aim to test whether such a position is consistent with a stellar mass $M_{\star}$$\raisebox{-.4ex}{$\stackrel{<}{\scriptstyle \sim}$}$10 or $\raisebox{-.4ex}{$\stackrel{<}{\scriptstyle \sim}$}$18 $M_{\odot}$"]
- result: H30α peak velocities = 15.3 and 50.3 ± not stated km/s (V_LSR) [3.2 Radio recombination lines: "two prominent peaks of emission at $V_{\rm LSR}$$\sim$15.3 and 50.3 km s$^{-1}$"]
- result: H30α wing full width = ~180 ± not stated km/s [3.2 Radio recombination lines: "The full width of the wings ($\sim$180 km s$^{-1}$) indicates a lower limit to the expansion velocity of the fast polar wind of $\sim$90 km s$^{-1}$."]
- result: Central mass (d=1.7 kpc / 3 kpc) = 10 / 18 ± up to 25% Msun [Model results table: "Central mass ($M_{\rm c}$) | 10 $M_{\odot}$ | 18 $M_{\odot}$"]
- result: Fast wind velocity = 95 ± not stated km/s [Model results table: "Fast outflow’s velocity ($V_{\rm fast}$) | 95 km s$^{-1}$ (*radial expansion*)"]
- result: Fast wind mass-loss rate (d=1.7/3 kpc) = 2e-6 / 4e-6 ± not stated Msun/yr [Model results table: "Mass-loss rate of the fast wind ($\dot{M}$$_{\rm fast}$) | 2$\times 10^{\rm -6}$ $M_{\odot}$ yr$^{-1}$ | 4$\times 10^{\rm -6}$"]
- result: Inner cavity radius (d=1.7/3 kpc) = 29 / 51.5 ± not stated au [Model results table: "Inner radius ($R_{\rm in}$) | 29 au | 51.5 au"]
- result: Ionized mass (d=1.7 kpc) = 2e-5 ± not stated Msun [Model results table: "Ionized mass ($M_{\rm ion}$) | 2$\times 10^{\rm -5}$$M_{\odot}$"]
- result: H30α maser optical depth at blue peak = -6 ± not stated dimensionless [4.1 Model results: "with a minimum optical depth at the line (blue) peak $\tau_{30\alpha}$$\sim$$-$6"]
- result: Lyman continuum rate log N_LyC = 46.9 ± not stated s^-1 [5.3 The ionizing central source: "The value found, log$N_{\rm LyC}$$\sim$46.9 s$^{-1}$"]
- limitation (authors): Distance very uncertain; central mass uncertain by up to 25%; slow wind not firmly established; model axisymmetric and cannot reproduce blue-peak asymmetry. [4.2 Model caveats and uncertainties: "The distance to MWC 922 is probably the most uncertain parameter that affects the interpretation and modelling of the data."]
- not stated (card): Robust weighting value used in MAPPING; Line-free channel ranges per SPW; Self-calibration solution intervals and number of iterations; Clean masks and iteration/threshold settings; MORELI code availability and fitting procedure (no formal optimisation or parameter uncertainties given); Dust opacity law/normalisation used for dust mass; Rest frequencies and cell/image sizes

### 2026A&A...705A.202M: The ALMA survey to Resolve exoKuiper belt Substructures (ARKS): VIII. A dust arc and non-Keplerian gas kinematics in HD 121617 (2026; debris_disks, astrochemistry; observational_alma_primary)
- question: Characterise the dust arc, the dust and CO gas distributions, and the gas kinematics (non-Keplerian rotation) of the gas-rich exoKuiper belt HD 121617, to constrain the arc origin and the gas origin
- step 3: Fit a Keplerian model to the 12CO line-of-sight velocity map
  - method: Gaussian-method moment 1 map with BETTERMOMENTS from the robust 0.5 cube, then Keplerian fit with EDDY for orientation, systemic velocity and stellar mass [3.1 2D velocity map: "We extracted a 2D line-of-sight velocity map from the clean cube using the package BETTERMOMENTS and the Gaussian method that fits a Gaussian line profile to each pixel (cite: bettermoments; bettermoments_unc)."] [3.1 2D velocity map: "We fitted a Keplerian model to this velocity map using the EDDY package (cite: eddy) to determine the orientation of the system, systemic velocity, and stellar mass."]
  - software: BETTERMOMENTS, EDDY
  - parameter: Cube: 12CO clean cube with robust 0.5 [3 CO gas kinematics: "We use the clean data cube corresponding to a robust value of 0.5 (cite: gas_arks)."]
  - assumption: Emission arises from the midplane (elevated-surface models gave heights consistent with zero) [3.1 2D velocity map: "Therefore, for the following analysis, we assume that the emission arises from the midplane."]
  - fitting: EDDY Keplerian fit; reported uncertainties <1% but likely underestimated because pixel correlation is ignored [3.1 2D velocity map: "The uncertainties on these values extracted by EDDY are below 1%, but they are likely underestimated as they do not take into account the spatial correlation between pixels."]
  - validation: Inclination and PA compared with the dust-derived values; stellar mass compared with ARKS I value [3.1 2D velocity map: "The derived values for the inclination and position angle are consistent with those derived for the dust emission"]
- step 4: Extract de-projected azimuthal, radial and vertical velocities versus radius
  - method: EDDY in concentric annuli using the Gaussian line centroid and the simple harmonic oscillator (SHO) method for 3D velocities [3.2 De-projected azimuthal velocity: "We used the Gaussian method to derive the line centroid and the ‘simple harmonic oscillator (SHO)’ method to derive the 3D velocities at each radius."]
  - software: EDDY
  - parameter: Annuli spaced by 20% of the beam size, oriented at the disc PA and inclination from the Keplerian fit [3.2 De-projected azimuthal velocity: "We divided the disc into a set of concentric annuli spaced by 20% of the beam size (same as the pixel size) and oriented at the same position angle and inclination as the disc"]
  - parameter: Fit restricted to position angles within 20 deg of the major axis [3.2 De-projected azimuthal velocity: "we also restricted the fit to position angles within 20$^\circ$ from the major axis of the disc"]
  - assumption: Systemic velocity fixed to the value from the Keplerian fit (vertical/systemic degeneracy) [3.2 De-projected azimuthal velocity: "we can fix and approximate the systemic velocity to be the systemic velocity extracted from the Keplerian fit"]
  - fitting: EDDY run ten times with disc orientation drawn from the Keplerian-fit posterior, each with ten retrievals on random pixel subsets per annulus [3.2 De-projected azimuthal velocity: "we ran EDDY ten times, randomising the disc orientation according to the posterior distribution of the Keplerian fit."] [3.2 De-projected azimuthal velocity: "For each orientation, EDDY performs ten retrievals using a different random sample of pixels within each annulus"]
  - validation: Compared with the profile from a simulated beam-smeared Keplerian observation; result also seen when fitting all azimuths or the moment 1 map [3.2 De-projected azimuthal velocity: "This finding is also present if we fit all azimuths, although less strongly, and if we fit the moment 1 instead of the cube."]
- step 5: Retrieve the gas radial density profile from the Keplerian deviations
  - method: Use the deviation of v_phi from Keplerian as a proxy for the radial pressure gradient, solve the midplane force balance for d ln(rho)/dr and integrate over r [3.3 Retrieving the radial density profi…: "we aim to retrieve the gas density profile using the Keplerian deviations as a proxy for the pressure gradient."] [3.3 Retrieving the radial density profi…: "Integrating the right-hand side over $r$, we obtain $\ln[\rho(r)]$ plus a constant that becomes a normalisation factor."]
  - parameter: beta=-0.14, T0=38 K, r0=73 au (from ARKS 13CO fit) [3.3 Retrieving the radial density profi…: "We assume that $\beta=-0.14$, $T_{0}=38$ K, and $r_0$=73 au as found in (cite: line_arks) by fitting the $^{13}$CO data cube."]
  - parameter: M_star = 1.91 Msun so that Keplerian speed at 75 au equals the measured azimuthal velocity [3.3 Retrieving the radial density profi…: "Moreover, we assume that $M_\star=1.91\ M_\odot$, which makes the Keplerian speed at the arc location (75 au) the same as the extracted azimuthal velocity."]
  - assumption: Mean molecular weight mu = 14 (C and O dominated, secondary gas) or 2.3 (H2 dominated, primordial); midplane z=0; power-law temperature [3.3 Retrieving the radial density profi…: "we assume two values for $\mu$: 14 for a disc dominated by C and O (secondary gas), and 2.3 for an H$_2$-dominated disc (primordial gas)."]
  - validation: Retrieved profile compared with the 13CO density profile; method tested on simulated models where it recovered the input density [Appendix 12CO radiative transfer models: "For both non-Keplerian models, the derived profiles reproduce well the true input profile despite the effects of beam smearing and optical depth effects."]
- step 6: Validate the kinematic method with simulated Keplerian and pressure-supported observations
  - method: Synthetic 12CO cubes from DISC2RADMC, simulated ALMA observations with CASA simobserve, imaged with tclean, then processed like the data (velocity map, Keplerian residuals, azimuthal velocities) [Appendix 12CO radiative transfer models: "The simulated ALMA observations are then imaged using TCLEAN using a Briggs weighting, a robust parameter of 0.5, a Keplerian mask and the same pixel size as in (cite: gas_arks)."] [Appendix 12CO radiative transfer models: "Finally, we follow the same procedure as with the real data, and extract the line-of-sight velocities, residuals after a Keplerian model subtraction, and azimuthal velocities from the simulated observations."]
  - software: disc2radmc, CASA, tclean
  - parameter: Cubes with 26 m/s spectral resolution and 10 mas spatial resolution [Appendix 12CO radiative transfer models: "We simulate image cubes with a spectral resolution of 26 m/s and spatial resolution of 10 mas."]
  - parameter: Gaussian radial surface density centred at 74 au, FWHM 17 au, aspect ratio h=0.05, 1.91 Msun star [Appendix 12CO radiative transfer models: "The gas is distributed with a Gaussian radial surface density distribution, centred at 74 au, with a FWHM of 17 au (cite: line_arks), and a vertical aspect ratio $h=0.05$."]
  - assumption: LTE, kinetic and excitation temperature 38 K at the belt centre decaying with exponent -0.14; mu = 14 or 2.3; radial and vertical velocities zero [Appendix 12CO radiative transfer models: "The gas is assumed to be in local thermodynamic equilibrium, and we set the kinetic and excitation temperature at the belt centre to be 38 K"] [Appendix 12CO radiative transfer models: "The radial and vertical velocities are set to zero."]
  - validation: Simulations confirm the observed residual pattern matches pressure-gradient velocity deviations and not pure Keplerian rotation [3.2 De-projected azimuthal velocity: "Our simulations confirm that the observed pattern is consistent with velocity deviations due to the pressure gradient of a gas ring, and inconsistent with a purely Keplerian rotation pattern."]
- result: Keplerian fit position angle = 59.6 ± <1% (likely underestimated) degrees [3.1 2D velocity map: "The best-fit values are -3 mas for the RA offset, 20 mas for the Dec offset, 59.6 for the position angle, 43.8 for the inclination"]
- result: Keplerian fit inclination = 43.8 ± <1% (likely underestimated) degrees [3.1 2D velocity map: "The best-fit values are -3 mas for the RA offset, 20 mas for the Dec offset, 59.6 for the position angle, 43.8 for the inclination"]
- result: Keplerian fit stellar mass = 1.89 ± <1% (likely underestimated) Msun [3.1 2D velocity map: "43.8 for the inclination, 1.89 $M_\odot$ for the stellar mass, and 7.86 km/s for the system line of sight velocity in the Barycentric reference frame"]
- result: Keplerian fit systemic velocity (barycentric) = 7.86 ± <1% (likely underestimated) km/s [3.1 2D velocity map: "43.8 for the inclination, 1.89 $M_\odot$ for the stellar mass, and 7.86 km/s for the system line of sight velocity in the Barycentric reference frame"]
- result: Deviation of azimuthal velocity from Keplerian (as measured) = ~1 ± not stated percent of Keplerian speed [3.2 De-projected azimuthal velocity: "Overall, we find deviations of the order of 1% with the azimuthal velocity decreasing with radius faster than Keplerian."]
- result: Deviation from Keplerian speed towards 65 and 85 au after accounting for beam smearing (estimate) = ~2 ± not stated percent of Keplerian speed [3.2 De-projected azimuthal velocity: "closer to 2% the Keplerian speed towards 65 and 85 au"]
- result: Upper limit on global radial and vertical velocities = <1 ± not stated percent of Keplerian speed [3.2 De-projected azimuthal velocity: "consistent with zero at all radii with upper limits below 1% of the Keplerian speed"]
- result: Width of kinematic density profile for mu=2.3 relative to 13CO density distribution = ~3 ± not stated dimensionless [3.3 Retrieving the radial density profi…: "appears ${\sim}3$ times wider than the $^{13}$CO density distribution"]
- result: Best-fit stellar mass of simulated Keplerian, mu=14 and mu=2.3 models (input 1.91 Msun) = 1.93, 1.93, 1.80 ± not stated Msun [Appendix 12CO radiative transfer models: "The best-fit $M_{\star}$ for the Keplerian, and non-Keplerian $\mu=14$, and $\mu=2.3$ models was 1.93, 1.93 and 1.80 $M_{\odot}$"]
- limitation (authors): Kinematic fit uncertainties likely underestimated (pixel correlation ignored) [3.1 2D velocity map: "The uncertainties on these values extracted by EDDY are below 1%, but they are likely underestimated as they do not take into account the spatial correlation between pixels."]
- limitation (authors): Dust mass uncertainty excludes opacity uncertainty [2.2 Arc parametric fit to continuum emi…: "we note that the small uncertainties do not include the uncertainties in the assumed dust opacity"]
- limitation (authors): Beam smearing biases the extracted azimuthal velocity profile, so deviations are probably underestimated [3.3 Retrieving the radial density profi…: "an important caveat to note is that the true azimuthal velocity profile is likely steeper than the extracted one because the latter is affected by beam smearing"]
- not stated (card): MCMC priors and bounds for all dust-model parameters, number of walkers/steps, burn-in and convergence criteria; Which continuum image/visibility set was fitted, weighting, and how the stellar position/phase centre was handled in the fit; Vertical structure (aspect ratio) and temperature or grid settings of the disc2radmc dust model used for the arc fit; How the arc mass fraction (13%) was comput…

### 2021MNRAS.506.1978L: High-resolution ALMA and HST images of q<SUP>1</SUP> Eri: an asymmetric debris disc with an eccentric Jupiter (2021; debris_disks, exoplanets; observational_alma_primary)
- question: Characterise the asymmetric outer debris belt of q1 Eri at sub-arcsecond resolution using ALMA and HST observations, and consider its relationship to the planetary system architecture, including the known exo-Jupiter q1 Eri b.
- step 5: Extract CO J=3-2 spectral line profile and derive upper limit on CO gas mass
  - method: Subtract continuum with uvcontsub, image barycentric cube within +/-200 km s^-1 with tclean (0 iterations), apply spectro-spatial Keplerian mask in clockwise and anti-clockwise rotation directions between 38-125 au, compute 3 sigma integra… [CO J=3-2 Spectral Line Analysis: "We produced a data cube in the barycentric reference frame excluding all channels further than $200\,\rm{km\,s^{-1}}$ away from the J=3-2 line in velocity space using the CASA tclean algorithm (with zero clean iterations, since there was no significant emission per beam present in any channel)."] [CO J=3-2 Spectral Line Analysis: "We integrated all emission in rotation directions between projected radii of ${\sim}$38-125 au from the star (i.e., within the broad region defined by the full-width half-maxima of the sub-mm emission), which are both shown as a function of radial velocity in Fig. 10."]
  - software: CASA, uvcontsub, tclean
  - parameter: uvcontsub fit order = 1, exclusion window = +/- 35 km s^-1; tclean iterations = 0; radial integration = 38-125 au; channel spacing Delta v = 0.423 km s^-1; effective bandwidth factor = 2.667 [CO J=3-2 Spectral Line Analysis: "To remove continuum emission from any $\rm{CO}$ signal, we used the CASA tool $\rm{uvcontsub}$ with a fit order of 1 external to the region defined by $f_{\rm{CO}} {\pm} \Delta f$, where $\Delta f$ was set to a velocity width ${\pm}35\,\rm{kms}^{-1}$, avoiding fitting to channels where $\rm{CO}$ could be present."] [CO J=3-2 Spectral Line Analysis: "The velocity channel spacing of the data is $\Delta v {=} 0.423\,\rm{kms}^{-1}$, however the effective spectral bandwidth is ${\sim}2.667$ larger than this, since adjacent *ALMA* channels are not fully independent from each other"]
  - parameter: NLTE kinetic temperatures = 10 K, 50 K, 250 K [CO Gas Mass: "For three temperatures $10\,\rm{K}$, $50\,\rm{K}$ and $250\,\rm{K}$ (covering a range of values appropriate for debris discs), together with the stellar flux (see Fig. 3) and the peak emission radius of ${\sim}81.6$ au, Fig. 12 shows the estimated $\rm{CO}$ gas mass as a function of the electron density in the disc."]
  - assumption: Stellar mass = 1.1 M_sun, radial velocity v_rad = 27.82 +/- 0.15 km s^-1, CO photodissociation time = 120 years [CO J=3-2 Spectral Line Analysis: "To do so, we applied a Keplerian mask to the data cube to shift channels in both of the possible disc rotation directions (clockwise and anti-clockwise) based on a stellar mass of 1.1 $M_{\ensuremath{\odot}}$ (cite: Marmier13)."] [CO Gas Mass: "From equation 2 of (cite: Matra17) we can use this upper limit $\rm{CO}$ mass alongside the stellar mass, luminosity, disc fractional luminosity, disc peak emission radius and belt width, with a CO photo-dissociation time of 120 years (cite: Visser09) to estimate an upper bound on the fraction of planetesimals compose…"]
  - validation: Tested both clockwise and anti-clockwise rotation directions and took the larger rms value (7.1 mJy). [CO J=3-2 Spectral Line Analysis: "We found the rms of the two line profiles (clockwise and anti-clockwise rotations) across all velocities, and measured $\rm{rms{=}7.0\,\rm{mJy}}$ in the clockwise-rotated direction, and $\rm{rms{=}7.1\,\rm{mJy}}$ in the anti-clockwise rotated direction. We define our upper bound based on the larger of these two rms va…"]
- result: CO J=3-2 integrated line flux 3 sigma upper limit = 24.0 ± not stated mJy km s^-1 [CO J=3-2 Spectral Line Analysis: "The $3\,\sigma$ limit on this flux is then found as $\delta F_{\rm{CO},3\,\sigma} {=} 2.667 \times \Delta v \times \rm{rms} {=} 24.0\,\rm{mJy\,kms^{-1}}$."]
- result: CO gas mass 3 sigma upper bound (M_CO) = <4e-6 ± not stated M_earth [Abstract: "We find no evidence for CO gas, but set an upper bound on the CO gas mass of $4{\times}10^{-6}$ M$_{\oplus}$ ($3\,\sigma$), consistent with cometary abundances in the Solar System."]
- result: Planetesimal CO+CO2 mass fraction upper bound = <95 ± not stated % [CO Gas Mass: "to estimate an upper bound on the fraction of planetesimals composed of $\rm{CO}+\rm{CO_{2}}$, which is $f_{\rm{CO+CO_{2}}}<95\%$."]
- limitation (authors): The modified blackbody parameters (lambda_0 and beta_0) for the inner warm component are poorly constrained because the sub-mm slope relies only on low-S/N Band 6 and Band 7 inner excesses. [Flux Density Distribution: "However, the parameters defining the blackbody modification are not well constrained (i.e., due to uncertainty on the stellar photosphere and given that the two Band 6 and Band 7 data points these model have only low signal-to-noise excesses) and thus there are a broad range of values for which $\lambda_0$ and $\beta_…"]
- limitation (authors): Lower sensitivity in the Band 6 image prevents an independent detection of the ~20% SW/NE flux asymmetry seen in Band 7. [Flux Profile Analysis: "Despite these Band 6 flux ratios and flux difference not showing evidence for an asymmetry, the lower S/N of this image means that an asymmetry could still be present at broadly the same ${\sim}20$ percent level seen in Band 7. Deeper observations of q$^1$ Eri in Band 6 would be required to determine this."]
- limitation (authors): The HST coronagraph occults emission within ~2.25'', limiting the ability to quantify the significance of the minor-axis scattered light asymmetry. [Scattered Light Analysis: "However, since emission within ${\sim}2.25\ensuremath{''}$ cannot be probed due to coronagraph obscuration, this limits our ability to estimate the significance of this minor axis asymmetry."]
- not stated (card): Exact antenna and baseline flags applied manually to the Band 6 dataset; Image pixel (cell) size, image dimensions, clean threshold, and masking strategy used in CASA tclean for Band 6 and Band 7 continuum and CO line cubes; Whether primary beam correction was applied to the continuum images and CO data cube prior to measuring fluxes and radial profiles; Exact prior distributions and bounds used …

### 2019ApJ...871L...1T: Indication of Another Intermediate-mass Black Hole in the Galactic Center (2019; milky_way_ism, stellar_physics; observational_alma_primary)
- question: Does the high-velocity compact cloud HCN-0.009-0.044 contain gas orbiting an invisible massive object, such as an intermediate-mass black hole?
- step 3: Fit Keplerian orbital geometry
  - method: Least-square fit of orbits to chosen loci of Balloon and Stream [Keplerian Model: "we determined three-dimensional orbital parameters ($a$, $e$, $\Omega$, $\omega$, $i$) for the orbital geometries of the Balloon and Stream by least-square fitting to the loci we chose"]
  - assumption: Dynamical center at (l,b,R) = (-0.0096°, -0.0451°, 8 kpc) [Keplerian Model: "Assuming the dynamical center at $(l,\ b, \ R) = (-0.0096^\circ,\ -0.0451^\circ,\ \rm 8\ kpc)$"]
- step 4: Fit central mass and systemic velocity
  - method: Chi-square minimization of modeled V_Z against moment-1 velocities smoothed to 3'' FWHM [Keplerian Model: "we fitted the modeled velocities $V_Z$ to the observed velocities on the orbits of the Balloon and Stream with free parameters of $M_{\rm dyn}$ and $V_{\rm dyn}$ through a chi-square ($\chi^2$) minimization approach"]
  - validation: confidence contours of M_dyn vs V_dyn [Keplerian Model: "Figure 3(d) shows the confidence level contours as a function of $M_{\rm dyn}$ and $V_{\rm dyn}$."]
- result: Central mass M_dyn = 3.2e4 ± ±0.6e4 Msun [Keplerian Model: "$M_{\rm dyn} = (3.2\pm0.6) \times 10^4$ $M_\odot$"]
- result: V_dyn = -49.5 ± +1.0/-0.7 km/s [Keplerian Model: "$V_{\rm dyn} = -49.5^{+1.0}_{-0.7}$ km s$^{-1}$"]
- result: Balloon semi-major axis = 0.20 ± 0.02 pc [Table 1: "Semi-major axis, $a$ | $0.20 \pm 0.02$ pc | $0.54 \pm 0.15$ pc"]
- limitation (authors): Inclination double degeneracy; UCC broad velocity not explained by Keplerian model. [Keplerian Model: "Note that there remains a double degeneracy in the inclination angle."]
- not stated (card): Line-free channels for uvcontsub and fit order; Cleaning threshold, masks, and niter; How 7-m and 12-m data were combined; Exact loci points chosen for orbit fitting; Uncertainty estimation method for the orbital parameters; Calibration script version and flux scale accuracy; Image sizes and primary beam correction

## All papers in this technique

- 2012ApJ...757..129R (2012): Kinematics of the CO Gas in the Inner Regions of the TW Hya Disk
- 2013A&A...552L..10S (2013): A candidate circumbinary Keplerian disk in G35.20-0.74 N: A study with ALMA
- 2013A&A...557A.133D (2013): Unveiling the gas-and-dust disk structure in HD 163296 using ALMA observations
- 2013A&A...560A.103M (2013): A Keplerian disk around a Class 0 source: ALMA observations of VLA1623A
- 2013ApJ...764L..14Z (2013): ALMA 690 GHz Observations of IRAS 16293-2422B: Infall in a Highly Optically Thick Disk
- 2013ApJ...765L..14Q (2013): First Detection of c-C<SUB>3</SUB>H<SUB>2</SUB> in a Circumstellar Disk
- 2013ApJ...768L..38H (2013): Submillimeter H<SUB>2</SUB>O Maser in Circinus Galaxy—a New Probe for the Circumnuclear Region of Active Galactic Nuclei
- 2013ApJ...774...16R (2013): A Spatially Resolved Vertical Temperature Gradient in the HD 163296 Disk
- 2013ApJ...776...77K (2013): ALMA Observations of the Molecular Gas in the Debris Disk of the 30 Myr Old Star HD 21997
- 2013Natur.493..191C (2013): Flows of gas through a protoplanetary gap
- 2013PASJ...65..100I (2013): Submillimeter ALMA Observations of the Dense Gas in the Low-Luminosity Type-1 Active Nucleus of NGC1097
- 2013PASJ...65L..14F (2013): Local Enhancement of the Surface Density in the Protoplanetary Ring Surrounding HD 142527
- 2013Sci...340.1199V (2013): A Major Asymmetric Dust Trap in a Transition Disk
- 2013Sci...341..630Q (2013): Imaging of the CO Snow Line in a Solar Nebula Analog
- 2014A&A...562A..26B (2014): Gas structure inside dust cavities of transition disks: Ophiuchus IRS 48 observed by ALMA
- 2014A&A...566A..74L (2014): ALMA observations of the kinematics and chemistry of disc formation
- 2014A&A...568L...5C (2014): The ALMA view of the protostellar system HH212. The wind, the cavity, and the disk
- 2014A&A...569A..11S (2014): A necklace of dense cores in the high-mass star forming region G35.20-0.74 N: ALMA observations
- 2014ApJ...785L..12C (2014): Spiral Arms in the Disk of HD 142527 from CO Emission Lines with ALMA
- 2014ApJ...786..114L (2014): ALMA Results of the Pseudodisk, Rotating Disk, and Jet in the Continuum and HCO<SUP>+</SUP> in the Protostellar System HH 212
- 2014ApJ...788L..34P (2014): Resolved Images of the Protoplanetary Disk around HD 100546 with ALMA
- 2014ApJ...791...42Z (2014): Comparison of the Dust and Gas Radial Structure in the Transition Disk [PZ99] J160421.7-213028
- 2014ApJ...793....1Y (2014): ALMA Observations of Infalling Flows toward the Keplerian Disk around the Class I Protostar L1489 IRS
- 2014ApJ...795..152O (2014): A Substellar-mass Protostar and its Outflow of IRAS 15398-3359 Revealed by Subarcsecond-resolution Observations of H<SUB>2</SUB>CO and CCH
- 2014ApJ...796....1T (2014): Angular Momentum Exchange by Gravitational Torques and Infall in the Circumbinary Disk of the Protostellar System L1551 NE
- 2014ApJ...796..117G (2014): The Slow Ionized Wind and Rotating Disklike System that are Associated with the High-mass Young Stellar Object G345.4938+01.4677
- 2014ApJ...796..120W (2014): ALMA Observations of a Misaligned Binary Protoplanetary Disk System in Orion
- 2014ApJ...796..131O (2014): Formation of a Keplerian Disk in the Infalling Envelope around L1527 IRS: Transformation from Infalling Motions to Kepler Motions
- 2014Sci...343.1490D (2014): Molecular Gas Clumps from the Destruction of Icy Bodies in the β Pictoris Debris Disk
- 2015A&A...574A...5D (2015): ALMA data suggest the presence of spiral structure in the inner wind of CW Leonis
- 2015A&A...575L...5H (2015): High-resolution observations of the outer disk around T Chamaeleontis: the view from ALMA
- 2015A&A...579A.106V (2015): Gas density drops inside dust cavities of transitional disks around young stars observed with ALMA
- 2015A&A...579A.114M (2015): A low-mass protostar's disk-envelope interface: disk-shadowing evidence from ALMA DCO<SUP>+</SUP> observations of VLA1623
- 2015A&A...582L...5R (2015): An ALMA survey for disks orbiting low-mass stars in the TW Hya Association
- 2015ApJ...798...85P (2015): CO Gas Inside the Protoplanetary Disk Cavity in HD 142527: Disk Structure from ALMA
- 2015ApJ...804...37L (2015): ALMA Resolves the Spiraling Accretion Flow in the Luminous OB Cluster-forming Region G33.92+0.11
- 2015ApJ...805...21C (2015): Gas Inside the 97 AU Cavity around the Transition Disk Sz 91
- 2015ApJ...806..154C (2015): A Disk-based Dynamical Mass Estimate for the Young Binary AK Sco
- 2015ApJ...808...69B (2015): ALMA Observations of the Largest Proto-Planetary Disk in the Orion Nebula, 114-426: A CO Silhouette
- 2015ApJ...808..102K (2015): Resolving Protoplanetary Disks at Millimeter Wavelengths with CARMA
- 2015ApJ...808L...3A (2015): The 2014 ALMA Long Baseline Campaign: First Results from High Angular Resolution Observations toward the HL Tau Region
- 2015ApJ...809L..25L (2015): The Distribution and Chemistry of H<SUB>2</SUB>CO in the DM Tau Protoplanetary Disk
- 2015ApJ...809L..26H (2015): Detection of N<SUB>2</SUB>D<SUP>+</SUP> in a Protoplanetary Disk
- 2015ApJ...811...39I (2015): ALMA Observations of the Submillimeter Dense Molecular Gas Tracers in the Luminous Type-1 Active Nucleus of NGC 7469
- 2015ApJ...812...27A (2015): ALMA Observations of the Transition from Infall Motion to Keplerian Rotation around the Late-phase Protostar TMC-1A
- 2015ApJ...812..129Y (2015): No Keplerian Disk &gt;10 AU Around the Protostar B335: Magnetic Braking or Young Age?
- 2015ApJ...813...99F (2015): Weak Turbulence in the HD 163296 Protoplanetary Disk Revealed by ALMA CO Observations
- 2015ApJ...814...22E (2015): Detection of Infall in the Protostar B335 with ALMA
- 2015MNRAS.447.3936M (2015): CO mass upper limits in the Fomalhaut ring - the importance of NLTE excitation in debris discs and future prospects with ALMA
- 2015Natur.520..198O (2015): The comet-like composition of a protoplanetary disk as revealed by complex cyanides
- 2015PASJ...67..122M (2015): Significant gas-to-dust ratio asymmetry and variation in the disk of HD 142527 and the indication of gas depletion
- 2016A&A...592A..49T (2016): Measuring turbulence in TW Hydrae with ALMA: methods and limitations
- 2016A&A...595A.113S (2016): Shadows cast on the transition disk of HD 135344B. Multiwavelength VLT/SPHERE polarimetric differential imaging
- 2016A&A...596A..92K (2016): ALMA observations of the nearby AGB star L<SUB>2</SUB> Puppis. I. Mass of the central star and detection of a candidate planet
- 2016ApJ...816...25P (2016): Dust and Gas in the Disk of HL Tauri: Surface Density, Dust Settling, and Dust-to-gas Ratio
- 2016ApJ...818..156C (2016): A Disk-based Dynamical Constraint on the Mass of the Young Binary DQ Tau
- 2016ApJ...823L..18H (2016): Evidence for a CO Desorption Front in the Outer AS 209 Disk
- 2016ApJ...824...88O (2016): Infalling-Rotating Motion and Associated Chemical Change in the Envelope of IRAS 16293-2422 Source A Studied with ALMA
- 2016ApJ...826..213L (2016): Angular Momentum Loss in the Envelope-Disk Transition Region of the HH 111 Protostellar System: Evidence for Magnetic Braking?
- 2016ApJ...827...69H (2016): A Search for Submillimeter H<SUB>2</SUB>O Masers in Active Galaxies: The Detection of 321 GHZ H<SUB>2</SUB>O Maser Emission in NGC 4945
- 2016ApJ...829....6W (2016): ALMA Observations of HD 141569’s Circumstellar Disk
- 2016ApJ...830...32W (2016): Measuring Protoplanetary Disk Gas Surface Density Profiles with ALMA
- 2016ApJ...830L..16B (2016): Misaligned Disks in the Binary Protostar IRS 43
- 2016ApJ...830L..37I (2016): Discovery of a Hot Corino in the Bok Globule B335
- 2016ApJ...832..204Y (2016): Stacking Spectra in Protoplanetary Disks: Detecting Intensity Profiles from Hidden Molecular Lines in HD 163296
- 2016ApJ...833..219P (2016): ALMA Observations of Orion Source I at 350 and 660 GHz
- 2016MNRAS.460.2933M (2016): Exocometary gas in the HD 181327 debris ring
- 2016MNRAS.462L.101A (2016): Dipper discs not inclined towards edge-on orbits
- 2016MNRAS.463.3563T (2016): Morphology and kinematics of the gas envelope of protostar L1527 as obtained from ALMA observations of the C<SUP>18</SUP>O(2-1) line emissi…
- 2016Natur.535..258C (2016): Imaging the water snow-line during a protostellar outburst
- 2016Natur.538..483T (2016): A triple protostar system formed via fragmentation of a gravitationally unstable disk
- 2016Natur.540..406B (2016): Resolved images of a protostellar outflow driven by an extended disk wind
- 2016Sci...353.1519P (2016): Spiral density waves in a young protoplanetary disk
- 2017A&A...597A..32V (2017): Cavity and other radial substructures in the disk around HD 97048
- 2017A&A...597L...5B (2017): A second post-AGB nebula that contains gas in rotation and in expansion: ALMA maps of IW Carinae
- 2017A&A...602A..59C (2017): Chasing discs around O-type (proto)stars: Evidence from ALMA observations
- 2017A&A...603A..10B (2017): Fragmentation and disk formation in high-mass star formation: The ALMA view of G351.77-0.54 at 0.06'' resolution
- 2017A&A...603L...3A (2017): Molecular outflow launched beyond the disk edge
- 2017A&A...605A..21C (2017): Increased H<SUB>2</SUB>CO production in the outer disk around HD 163296
- 2017A&A...606A.125S (2017): DCO<SUP>+</SUP>, DCN, and N<SUB>2</SUB>D<SUP>+</SUP> reveal three different deuteration regimes in the disk around the Herbig Ae star HD 16…
- 2017A&A...607A..55V (2017): An 80 au cavity in the disk around HD 34282
- 2017A&A...607A.114W (2017): CO emission tracing a warp or radial flow within ≲100 au in the HD 100546 protoplanetary disk
- 2017A&A...607A.130D (2017): The Flying Saucer: Tomography of the thermal and density gas structure of an edge-on protoplanetary disk
- 2017A&A...608A.134Y (2017): 1000 au exterior arcs connected to the protoplanetary disk around HL Tauri
- 2017AJ....153..233F (2017): ALMA Observations of Asymmetric Molecular Gas Emission from a Protoplanetary Disk in the Orion Nebula
- 2017ApJ...834..178Y (2017): Signs of Early-stage Disk Growth Revealed with ALMA
- 2017ApJ...835...17M (2017): ALMA Measurements of Circumstellar Material in the GQ Lup System
- 2017ApJ...836...30G (2017): Nitrogen Fractionation in Protoplanetary Disks from the H<SUP>13</SUP>CN/HC<SUP>15</SUP>N Ratio
- 2017ApJ...837...86T (2017): Spiral Arms, Infall, and Misalignment of the Circumbinary Disk from the Circumstellar Disks in the Protostellar Binary System L1551 NE
- 2017ApJ...837...93Y (2017): Tidal Distortion of the Envelope of an AGB Star IRS 3 near Sgr A*
- 2017ApJ...837..174O (2017): L483: Warm Carbon-chain Chemistry Source Harboring Hot Corino Activity
- 2017ApJ...840...23L (2017): A Multi-ringed, Modestly Inclined Protoplanetary Disk around AA Tau
- 2017ApJ...840...32T (2017): Planet Formation in AB Aurigae: Imaging of the Inner Gaseous Spirals Observed inside the Dust Cavity
- 2017ApJ...840...60B (2017): A Close-up View of the Young Circumbinary Disk HD 142527
- 2017ApJ...842....8M (2017): A Complete ALMA Map of the Fomalhaut Debris Disk
- 2017ApJ...842....9M (2017): Detection of Exocometary CO within the 440 Myr Old Fomalhaut Belt: A Similar CO+CO<SUB>2</SUB> Ice Abundance in Exocomets and Solar System …
- 2017ApJ...842...94T (2017): ALMA View of the Galactic Center Minispiral: Ionized Gas Flows around Sagittarius A<SUP>∗</SUP>
- 2017ApJ...843...27L (2017): Formation and Atmosphere of Complex Organic Molecules of the HH 212 Protostellar Disk
- 2017ApJ...843...45K (2017): Mass Transport from the Envelope to the Disk of V346 Nor: A Case Study for the Luminosity Problem in an FUor-type Young Eruptive Star
- 2017ApJ...843..150F (2017): A Three-dimensional View of Turbulence: Constraints on Turbulent Motions in the HD 163296 Protoplanetary Disk Using DCO<SUP>+</SUP>
- 2017ApJ...844..158S (2017): Dynamical Masses of Low-mass Stars in the Taurus and Ophiuchus Star-forming Regions
- 2017ApJ...845...10F (2017): Strongly Misaligned Triple System in SR 24 Revealed by ALMA
- 2017ApJ...846L..26W (2017): An ALMA Dynamical Mass Estimate of the Proposed Planetary-mass Companion FW Tau C
- 2017ApJ...849...56A (2017): ALMA Observations of the Protostar L1527 IRS: Probing Details of the Disk and the Envelope Structures
- 2017ApJ...850L...5T (2017): The Second Galactic Center Black Hole? A Possible Detection of Ionized Gas Orbiting around an IMBH Embedded in the Galactic Center IRS13E C…
- 2017ApJ...851..132C (2017): The Architecture of the GW Ori Young Triple-star System and Its Disk: Dynamical Masses, Mutual Inclinations, and Recurrent Eclipses
- 2017MNRAS.464.1415M (2017): Exocometary gas structure, origin and physical properties around β Pictoris through ALMA CO multitransition observations
- 2017MNRAS.465.2595M (2017): ALMA observations of the η Corvi debris disc: inward scattering of CO-rich exocomets by a chain of 3-30 M<SUB>⊕</SUB> planets?
- 2017MNRAS.467L..76S (2017): Vertical structure of the transition zone from infalling rotating envelope to disc in the Class 0 protostar, IRAS 04368+2557
- 2017MNRAS.467L.120M (2017): The ALMA view of W33A: a spiral filament feeding the candidate disc in MM1-Main
- 2017MNRAS.468..685Q (2017): Modelling the 3D physical structure of astrophysical sources with gass
- 2017MNRAS.468.1769F (2017): The varying mass distribution of molecular clouds across M83
- 2017MNRAS.469.4726N (2017): High-resolution ALMA observation of the <SUP>12</SUP>CO(3-2) and 350 GHz continuum emissions of the debris disc of 49 Ceti
- 2017NatAs...1E.130Z (2017): Mass inventory of the giant-planet formation zone in a solar nebula analogue
- 2017NatAs...1E.146H (2017): Disk-driven rotating bipolar outflow in Orion Source I
- 2017NatAs...1E.172L (2017): Formation of wide binaries by turbulent fragmentation
- 2017SciA....3E2935L (2017): First detection of equatorial dark dust lane in a protostellar disk at submillimeter wavelength
- 2018A&A...609A..47P (2018): Direct mapping of the temperature and velocity gradients in discs. Imaging the vertical CO snow line around IM Lupi
- 2018A&A...609A..67K (2018): The close circumstellar environment of Betelgeuse. V. Rotation velocity and molecular envelope properties from ALMA
- 2018A&A...612A..72J (2018): The ALMA-PILS survey: 3D modeling of the envelope, disks and dust filament of IRAS 16293-2422
- 2018A&A...614A..26A (2018): Chemistry of a newly detected circumbinary disk in Ophiuchus
- 2018A&A...614A..58B (2018): High-resolution observations of IRAS 08544-4431. Detection of a disk orbiting a post-AGB star and of a slow disk wind
- 2018A&A...614A.106C (2018): Probing midplane CO abundance and gas temperature with DCO<SUP>+</SUP> in the protoplanetary disk around HD 169142
- 2018A&A...614A.113H (2018): ALMA detection of a tentative nearly edge-on rotating disk around the nearby AGB star R Doradus
- 2018A&A...616A..34H (2018): An unusual face-on spiral in the wind of the M-type AGB star EP Aquarii
- 2018A&A...616A..45S (2018): Exploring DCO<SUP>+</SUP> as a tracer of thermal inversion in the disk around the Herbig Ae star HD 163296
- 2018A&A...616A..61R (2018): CO envelope of the symbiotic star R Aquarii seen by ALMA
- 2018A&A...616A.100Y (2018): Stellar masses and disk properties of Lupus young stellar objects traced by velocity-aligned stacked ALMA <SUP>13</SUP>CO and C<SUP>18</SUP…
- 2018A&A...617A..89C (2018): Search for high-mass protostars with ALMA revealed up to kilo-parsec scales (SPARKS). I. Indication for a centrifugal barrier in the enviro…
- 2018A&A...618A.120L (2018): The HH30 edge-on T Tauri star. A rotating and precessing monopolar outflow scrutinized by ALMA
- 2018A&A...619A.171B (2018): Shadows and asymmetries in the T Tauri disk HD 143006: evidence for a misaligned inner disk
- 2018A&A...620A..31M (2018): Chasing discs around O-type (proto)stars. ALMA evidence for an SiO disc and disc wind from G17.64+0.16
- 2018A&A...620L...1G (2018): ALMA detects a radial disk wind in DG Tauri
- 2018ApJ...852..122H (2018): CO and Dust Properties in the TW Hya Disk from High-resolution ALMA Observations
- 2018ApJ...853..162B (2018): The Complex Morphology of the Young Disk MWC 758: Spirals and Dust Clumps around a Large Cavity
- 2018ApJ...854...56L (2018): ALMA Dust Polarization Observations of Two Young Edge-on Protostellar Disks
- 2018ApJ...854..130W (2018): The Orbit of the Companion to HD 100453A: Binary-driven Spiral Arms in a Protoplanetary Disk
- 2018ApJ...857...69B (2018): A Survey of CH<SUB>3</SUB>CN and HC<SUB>3</SUB>N in Protoplanetary Disks
- 2018ApJ...857...87L (2018): New Constraints on Turbulence and Embedded Planet Mass in the HD 163296 Disk from Planet-Disk Hydrodynamic Simulations
- 2018ApJ...858..112L (2018): Differences in the Gas and Dust Distribution in the Transitional Disk of a Sun-like Young Star, PDS 70
- 2018ApJ...859...21A (2018): ALMA Survey of Lupus Protoplanetary Disks. II. Gas Disk Radii
- 2018ApJ...859..111H (2018): The Circumstellar Disk and Asymmetric Outflow of the EX Lup Outburst System
- 2018ApJ...859..131L (2018): The Distribution and Excitation of CH<SUB>3</SUB>CN in a Solar Nebula Analog
- 2018ApJ...859..150R (2018): Multiple Stellar Flybys Sculpting the Circumstellar Architecture in RW Aurigae
- 2018ApJ...860..119G (2018): A Keplerian Disk around Orion SrCI, a ∼ 15 M <SUB>☉</SUB> YSO
- 2018ApJ...860L..12T (2018): A Kinematical Detection of Two Embedded Jupiter-mass Planets in HD 163296
- 2018ApJ...860L..13P (2018): Kinematic Evidence for an Embedded Protoplanet in a Circumstellar Disk
- 2018ApJ...861...91H (2018): ALMA Observations of Polarized 872 μm Dust Emission from the Protostellar Systems VLA 1623 and L1527
- 2018ApJ...862L...2F (2018): First Detection of the Simplest Organic Acid in a Protoplanetary Disk
- 2018ApJ...863...94L (2018): ALMA Observations of the Very Young Class 0 Protostellar System HH211-mms: A 30 au Dusty Disk with a Disk Wind Traced by SO?
- 2018ApJ...864...76Z (2018): Rotation in the NGC 1333 IRAS 4C Outflow
- 2018ApJ...864..133T (2018): Temperature, Mass, and Turbulence: A Spatially Resolved Multiband Non-LTE Analysis of CS in TW Hya
- 2018ApJ...864L..23V (2018): Methanol and its Relation to the Water Snowline in the Disk around the Young Outbursting Star V883 Ori
- 2018ApJ...864L..25O (2018): The Co-evolution of Disks and Stars in Embedded Stages: The Case of the Very-low-mass Protostar IRAS 15398-3359
- 2018ApJ...865..131L (2018): High-resolution ALMA Study of the Proto-brown-dwarf Candidate L328-IRS
- 2018ApJ...865..155C (2018): Constraining Gas-phase Carbon, Oxygen, and Nitrogen in the IM Lup Protoplanetary Disk
- 2018ApJ...867...43T (2018): The VLA/ALMA Nascent Disk and Multiplicity (VANDAM) Survey of Perseus Protostars. VI. Characterizing the Formation Mechanism for Close Mult…
- 2018ApJ...868..113T (2018): Evidence for a Vertical Dependence on the Pressure Structure in AS 209
- 2018ApJ...868L...5K (2018): A Spatially Resolved au-scale Inner Disk around DM Tau
- 2018ApJ...869...10M (2018): Comprehensive Analysis of HD 105, A Young Solar System Analog
- 2018ApJ...869...59W (2018): Physical and Chemical Conditions of the Protostellar Envelope and the Protoplanetary Disk in HL Tau
- 2018ApJ...869L..24I (2018): G11.92-0.61 MM 1: A Fragmented Keplerian Disk Surrounding a Proto-O Star
- 2018ApJ...869L..42H (2018): The Disk Substructures at High Angular Resolution Project (DSHARP). II. Characteristics of Annular Substructures
- 2018ApJ...869L..48G (2018): The Disk Substructures at High Angular Resolution Program (DSHARP). VIII. The Rich Ringed Substructures in the AS 209 Disk
- 2018ApJ...869L..49I (2018): The Disk Substructures at High Angular Resolution Project (DSHARP). IX. A High-definition Study of the HD 163296 Planet-forming Disk
- 2018ApJ...869L..50P (2018): The Disk Substructures at High Angular Resolution Project (DSHARP). X. Multiple Rings, a Misaligned Inner Disk, and a Bright Arc in the Dis…
- 2018MNRAS.478.2505I (2018): Radiative transfer modelling of W33A MM1: 3D structure and dynamics of a complex massive star-forming region
- 2018MNRAS.479.5423M (2018): A gap in the planetesimal disc around HD 107146 and asymmetric warm dust emission revealed by ALMA
- 2018NatAs...2..646H (2018): Evidence for the start of planet formation in a young circumstellar disk
- 2018RAA....18...31P (2018): Morphology of the <SUP>13</SUP>CO(3-2) millimetre emission across the gas disc surrounding the triple protostar GG Tau A using ALMA observa…
- 2018RAA....18...93Z (2018): Disks and outflows in the S255IR area of high mass star formation from ALMA observations
- 2019A&A...622A.206M (2019): A 10-M<SUB>☉</SUB> YSO with a Keplerian disk and a nonthermal radio jet
- 2019A&A...623A..77S (2019): Discovery of a sub-Keplerian disk with jet around a 20 M<SUB>☉</SUB> young star. ALMA observations of G023.01-00.41
- 2019A&A...623A.124C (2019): Upper limits on CH<SUB>3</SUB>OH in the HD 163296 protoplanetary disk. Evidence for a low gas-phase CH<SUB>3</SUB>OH-to-H<SUB>2</SUB>CO rat…
- 2019A&A...623A.150V (2019): The ALMA Lupus protoplanetary disk survey: evidence for compact gas disks and molecular rings from CN
- 2019A&A...624A...7V (2019): Spatial segregation of dust grains in transition disks. SPHERE observations of 2MASS J16083070-3828268 and RXJ1852.3-3700
- 2019A&A...624L...7V (2019): Stringent limits on the magnetic field strength in the disc of TW Hya. ALMA observations of CN polarisation
- 2019A&A...625A.118K (2019): Highly structured disk around the planet host PDS 70 revealed by high-angular resolution observations with ALMA
- 2019A&A...626A..71A (2019): Physical and chemical fingerprint of protostellar disc formation
- 2019A&A...627L...6M (2019): Substructures in the Keplerian disc around the O-type (proto-)star G17.64+0.16
- 2019A&A...629A..29J (2019): Organic chemistry in the innermost, infalling envelope of the Class 0 protostar L483
- 2019A&A...629A..75B (2019): First detections of H<SUP>13</SUP>CO<SUP>+</SUP> and HC<SUP>15</SUP>N in the disk around HD 97048. Evidence for a cold gas reservoir in the…
- 2019A&A...629A.136S (2019): A rotating fast bipolar wind and disk system around the B[e]-type star MWC 922
- 2019A&A...632L..12H (2019): Multiple nitrogen reservoirs in a protoplanetary disk at the epoch of comet and giant planet formation
- 2019AJ....157..117M (2019): On the Ubiquity and Stellar Luminosity Dependence of Exocometary CO Gas: Detection around M Dwarf TWA 7
- 2019AJ....157..165A (2019): A Tail Structure Associated with a Protoplanetary Disk around SU Aurigae
- 2019AJ....157..237R (2019): Constraints on a Putative Planet Sculpting the V4046 Sagittarii Circumbinary Disk
- 2019AJ....158..162F (2019): From Scattered-light to Millimeter Emission: A Comprehensive View of the Gigayear-old System of HD 202628 and its Eccentric Debris Ring
- 2019ApJ...871....5T (2019): The Flared Gas Structure of the Transitional Disk around Sz 91
- 2019ApJ...871...48P (2019): High-resolution ALMA Observations of HD 100546: Asymmetric Circumstellar Ring and Circumplanetary Disk Upper Limits
- 2019ApJ...871..221M (2019): A Very Compact Extremely High Velocity Flow toward MMS 5/OMC-3 Revealed with ALMA
- 2019ApJ...871L...1T (2019): Indication of Another Intermediate-mass Black Hole in the Galactic Center
- 2019ApJ...872...64K (2019): Extremely High Excitation SiO Lines in Disk-outflow Systems in Orion Source I
- 2019ApJ...872..176Z (2019): An Asymmetric Keplerian Disk Surrounding the O-type Protostar IRAS 16547-4247
- 2019ApJ...873...73Z (2019): An Ordered Envelope-Disk Transition in the Massive Protostellar Source G339.88-1.26
- 2019ApJ...874..136S (2019): High-precision Dynamical Masses of Pre-main-sequence Stars with ALMA and Gaia
- 2019ApJ...876...25B (2019): A Survey of C<SUB>2</SUB>H, HCN, and C<SUP>18</SUP>O in Protoplanetary Disks
- 2019ApJ...876...72L (2019): Sulfur Chemistry in Protoplanetary Disks: CS and H<SUB>2</SUB>CS
- 2019ApJ...876L..13S (2019): Line Ratios Reveal N<SUB>2</SUB>H<SUP>+</SUP> Emission Originates above the Midplane in TW Hydrae
- 2019ApJ...877..100Y (2019): A Tight Relation between Spiral Arm Pitch Angle and Protoplanetary Disk Mass
- 2019ApJ...877L..25M (2019): The First Bird’s-eye View of a Gravitationally Unstable Accretion Disk in High-mass Star Formation
- 2019ApJ...878..113H (2019): Modeling the Spatial Distribution and Origin of CO Gas in Debris Disks
- 2019ApJ...879..101L (2019): A Pseudodisk Threaded with a Toroidal and Pinched Poloidal Magnetic Field Morphology in the HH 211 Protostellar System
- 2019ApJ...879L..25I (2019): Detection of Continuum Submillimeter Emission Associated with Candidate Protoplanets
- 2019ApJ...880...69Y (2019): HL Tau Disk in HCO<SUP>+</SUP> (3-2) and (1-0) with ALMA: Gas Density, Temperature, Gap, and One-arm Spiral
- 2019ApJ...880..130M (2019): A New, Rotating Hot Corino in Serpens
- 2019ApJ...881...84S (2019): The REASONS Survey: Resolved Millimeter Observations of a Large Debris Disk around the Nearby F Star HD 170773
- 2019ApJ...881..112O (2019): Sulfur-bearing Species Tracing the Disk/Envelope System in the Class I Protostellar Source Elias 29
- 2019ApJ...882..160Q (2019): Probing CO and N<SUB>2</SUB> Snow Surfaces in Protoplanetary Disks with N<SUB>2</SUB>H<SUP>+</SUP> Emission
- 2019ApJ...882L..31B (2019): The First Detection of <SUP>13</SUP>C<SUP>17</SUP>O in a Protoplanetary Disk: A Robust Tracer of Disk Gas Mass
- 2019ApJ...883...22C (2019): The Degree of Alignment between Circumbinary Disks and Their Binary Hosts
- 2019ApJ...884...42S (2019): Masses and Implications for Ages of Low-mass Pre-main-sequence Stars in Taurus and Ophiuchus
- 2019ApJ...884..146T (2019): An ALMA Study of the FU Ori-type Object V900 Mon: Implications for the Progenitor
- 2019ApJ...884L..56T (2019): Spiral Structure in the Gas Disk of TW Hya
- 2019MNRAS.482.3443B (2019): Deep ALMA search for CO gas in the HD 95086 debris disc
- 2019MNRAS.484.1257M (2019): A gap in HD 92945's broad planetesimal disc revealed by ALMA
- 2019MNRAS.486.4638U (2019): A dust and gas cavity in the disc around CQ Tau revealed by ALMA
- 2019NatAs...3..408D (2019): Reduction of the maximum mass-loss rate of OH/IR stars due to unnoticed binary interaction
- 2019NatAs...3..517Z (2019): Dynamics of a massive binary at birth
- 2019Natur.574..378T (2019): Meridional flows in the disk around a young star
- 2019Sci...366...90A (2019): Gas flow and accretion via spiral streamers and circumstellar disks in a young binary protostar
- 2020A&A...633A.115K (2020): ALMA and NACO observations towards the young exoring transit system J1407 (V1400 Cen)
- 2020A&A...634L..11J (2020): Spiral arms and instability within the AFGL 4176 mm1 disc
- 2020A&A...634L..12D (2020): ALMA reveals a large structured disk and nested rotating outflows in DG Tauri B
- 2020A&A...635A..12P (2020): GG Tauri A: gas properties and dynamics from the cavity to the outer disk
- 2020A&A...638A..38T (2020): Constraining the radial drift of millimeter-sized grains in the protoplanetary disks in Lupus
- 2020A&A...642A.165R (2020): Interpreting high spatial resolution line observations of planet-forming disks with gaps and rings: the case of HD 163296
- 2020A&A...644A..61H (2020): ATOMIUM: A high-resolution view on the highly asymmetric wind of the AGB star π<SUP>1</SUP>Gruis. I. First detection of a new companion and…
- 2020ApJ...888...41A (2020): Modeling the Accretion Disk around the High-mass Protostar GGD 27-MM1
- 2020ApJ...889...20L (2020): The Circumstellar Environment around the Embedded Protostar EC 53
- 2020ApJ...889...43Z (2020): Dense Cores, Filaments, and Outflows in the S255IR Region of High-mass Star Formation
- 2020ApJ...889..140Y (2020): High-resolution Near-infrared Polarimetry and Submillimeter Imaging of FS Tau A: Possible Streamers in Misaligned Circumbinary Disk System
- 2020ApJ...890..142P (2020): An ALMA Survey of H<SUB>2</SUB>CO in Protoplanetary Disks
- 2020ApJ...891...48H (2020): A Multifrequency ALMA Characterization of Substructures in the GM Aur Protoplanetary Disk
- 2020ApJ...891...61Y (2020): Constraining the Infalling Envelope Models of Embedded Protostars: BHR 71 and Its Hot Corino
- 2020ApJ...892...99C (2020): The Surprisingly Low Carbon Mass in the Debris Disk around HD 32297
- 2020ApJ...893...51S (2020): Disk Structure around the Class I Protostar L1489 IRS Revealed by ALMA: A Warped-disk System
- 2020ApJ...893..101L (2020): An Unbiased ALMA Spectral Survey of the LkCa 15 and MWC 480 Protoplanetary Disks
- 2020ApJ...894...23H (2020): Determining the Physical Conditions of an Extremely Young Class 0 Circumbinary Disk around VLA 1623A
- 2020ApJ...894...74B (2020): Protoplanetary Disks in the Orion Nebula Cluster: Gas-disk Morphologies and Kinematics as Seen with ALMA
- 2020ApJ...895...73K (2020): A Massive Molecular Torus inside a Gas-poor Circumnuclear Disk in the Radio Galaxy NGC 1052 Discovered with ALMA
- 2020ApJ...895..109F (2020): Measuring Turbulent Motion in Planet-forming Disks with ALMA: A Detection around DM Tau and Nondetections around MWC 480 and V4046 Sgr
- 2020ApJ...896..127K (2020): Multiple Outflows in the High-mass Cluster-forming Region G25.82-0.17
- 2020ApJ...897...59M (2020): Orbital and Mass Constraints of the Young Binary System IRAS 16293-2422 A
- 2020ApJ...897L..33J (2020): The Ionized Warped Disk and Disk Wind of the Massive Protostar Monoceros R2-IRS2 Seen with ALMA
- 2020ApJ...898...10T (2020): Circumbinary Disks of the Protostellar Binary Systems in the L1551 Region
- 2020ApJ...898...97B (2020): An Evolutionary Study of Volatile Chemistry in Protoplanetary Disks
- 2020ApJ...899..157T (2020): The Excitation Conditions of CN in TW Hya
- 2020ApJ...900....7H (2020): ALMA Observations of Young Eruptive Stars: Continuum Disk Sizes and Molecular Outflows
- 2020ApJ...901...71S (2020): Low-level Carbon Monoxide Line Polarization in Two Protoplanetary Disks: HD 142527 and IM Lup
- 2020ApJ...902...99I (2020): ALMA 0"02 Resolution Observations Reveal HCN-abundance-enhanced Counter-rotating and Outflowing Dense Molecular Gas at the NGC 1068 Nucleus
- 2020ApJ...904...77G (2020): A Photoionized Accretion Disk around a Young High-mass Star
- 2020ApJ...904...78S (2020): Constraining the Chemical Signatures and the Outburst Mechanism of the Class 0 Protostar HOPS 383
- 2020ApJ...904..125S (2020): Spiral-arm Substructures in the Asymmetrical Dust Rings of the Circumstellar Disk MWC 758
- 2020ApJ...904..181L (2020): ALMA View of the Infalling Envelope around a Massive Protostar in S255IR SMA1
- 2020ApJ...904..185O (2020): Substructures in the Disk-forming Region of the Class 0 Low-mass Protostellar Source IRAS 16293-2422 Source A on a 10 au Scale
- 2020ApJ...904L...6A (2020): A Case of Simultaneous Star and Planet Formation
- 2020ApJ...905...25G (2020): Multidirectional Mass Accretion and Collimated Outflows on Scales of 100-2000 au in Early Stages of High-mass Protostars
- 2020ApJ...905...89Y (2020): Kinematical Signs of Dust Trapping and Feedback in a Local Pressure Bump in the Protoplanetary Disk around HD 142527 Revealed with ALMA
- 2020CPhy...30...85D (2020): Observation of High Doppler Velocity Wings in the Nascent Wind of R Doradus
- 2020MNRAS.491.1335R (2020): Spiral arms in the protoplanetary disc HD100453 detected with ALMA: evidence for binary-disc interaction and a vertical temperature gradient
- 2020MNRAS.492..572A (2020): Are inner disc misalignments common? ALMA reveals an isotropic outer disc inclination distribution for young dipper stars
- 2020MNRAS.492.6067M (2020): Searching for a dusty cometary belt around TRAPPIST-1 with ALMA
- 2020MNRAS.493L.108B (2020): <SUP>13</SUP>C<SUP>17</SUP>O suggests gravitational instability in the HL Tau disc
- 2020MNRAS.496.5330F (2020): Gas kinematics of key prebiotic molecules in GV Tau N revealed with an ALMA, PdBI, and Herschel synergy
- 2020MNRAS.498.1319M (2020): Insights into the planetary dynamics of HD 206893 with ALMA
- 2020NatAs...4..142L (2020): Spiral structures in an embedded protostellar disk driven by envelope accretion
- 2020PASJ...72L...5T (2020): How far actually is the Galactic Center IRS 13E3 from Sagittarius A<SUP>*</SUP>?
- 2021A&A...646A...3L (2021): Chemically tracing the water snowline in protoplanetary disks with HCO<SUP>+</SUP>
- 2021A&A...646A..59R (2021): Tracing molecular stratification within an edge-on protoplanetary disk
- 2021A&A...646A..72H (2021): Resolved molecular line observations reveal an inherited molecular layer in the young disk around TMC1A
- 2021A&A...648A..19W (2021): A highly non-Keplerian protoplanetary disc. Spiral structure in the gas disc of CQ Tau
- 2021A&A...649A..19S (2021): Measuring the ratio of the gas and dust emission radii of protoplanetary disks in the Lupus star-forming region
- 2021A&A...650A..59B (2021): Vortex-like kinematic signal, spirals, and beam smearing effect in the HD 142527 disk
- 2021A&A...650A.142M (2021): The ionized heart of a molecular disk. ALMA observations of the hyper-compact HII region G24.78+0.08 A1
- 2021A&A...651L...5V (2021): A major asymmetric ice trap in a planet-forming disk. I. Formaldehyde and methanol
- 2021A&A...651L...6B (2021): A major asymmetric ice trap in a planet-forming disk. II. Prominent SO and SO<SUB>2</SUB> pointing to C/O &lt; 1
- 2021A&A...653A.166C (2021): Structured velocity field in the inner envelope of B335: ALMA observations of rare CO isotopologues
- 2021A&A...655A..72S (2021): Physical conditions in the warped accretion disk of a massive star. 349 GHz ALMA observations of G023.01‒00.41
- 2021AJ....161..271F (2021): A Detailed Characterization of HR 8799's Debris Disk with ALMA in Band 7
- 2021AJ....162...14A (2021): Precision Millimeter Astrometry of the α Centauri AB System
- 2021AJ....162...99F (2021): The Chemical Inventory of the Planet-hosting Disk PDS 70
- 2021ApJ...906..111T (2021): The TW Hya Rosetta Stone Project. II. Spatially Resolved Emission of Formaldehyde Hints at Low-temperature Gas-phase Formation
- 2021ApJ...907L..41L (2021): First Detection of Interaction between a Magnetic Disk Wind and an Episodic Jet in a Protostellar System
- 2021ApJ...908...46B (2021): Dynamical Stellar Masses of Pre-main-sequence Stars in Lupus and Taurus Obtained with ALMA Surveys in Comparison with Stellar Evolutionary …
- 2021ApJ...908..141H (2021): ALMA CN Zeeman Observations of AS 209: Limits on Magnetic Field Strength and Magnetically Driven Accretion Rate
- 2021ApJ...908..250H (2021): ALMA Observations of the Inner Cavity in the Protoplanetary Disk around Sz 84
- 2021ApJ...910...75L (2021): What Produces Dust Polarization in the HH 212 Protostellar Disk at 878 μm: Dust Self-scattering or Dichroic Extinction?
- 2021ApJ...911...29C (2021): The TW Hya Rosetta Stone Project IV: A Hydrocarbon-rich Disk Atmosphere
- 2021ApJ...911..150P (2021): An Atacama Large Millimeter/submillimeter Array Survey of Chemistry in Disks around M4-M5 Stars
- 2021ApJS..257....6G (2021): Molecules with ALMA at Planet-forming Scales (MAPS). VI. Distribution of the Small Organics HCN, C<SUB>2</SUB>H, and H<SUB>2</SUB>CO
- 2021MNRAS.501.4317P (2021): Planet formation in intermediate-separation binary systems
- 2021MNRAS.506.1978L (2021): High-resolution ALMA and HST images of q<SUP>1</SUP> Eri: an asymmetric debris disc with an eccentric Jupiter
- 2021MNRAS.507.1886F (2021): Probing the kinematics and chemistry of the hot core Mon R2 IRS 3 using ALMA observations
- 2021PASJ...73..205T (2021): ALMA view of the Galactic super star cluster RCW 38 at 270 au resolution
- 2022A&A...659A..29B (2022): A major asymmetric ice trap in a planet-forming disk. III. First detection of dimethyl ether
- 2022A&A...662A.121R (2022): Observational constraints on gas disc sizes in the protoplanetary discs of multiple systems in the Taurus region
- 2022ApJ...937...10L (2022): Stratified Distribution of Organic Molecules at the Planet-formation Scale in the HH 212 Disk Atmosphere
- 2022MNRAS.509..748W (2022): ALMA observations of the Extended Green Object G19.01-0.03 - I. A Keplerian disc in a massive protostellar system
- 2022MNRAS.510.2363H (2022): Morpho-kinematics of the wind of asymptotic giant branch star L<SUB>2</SUB> Pup
- 2022MNRAS.513.5790C (2022): Variable structure in the PDS 70 disc and uncertainties in radio-interferometric image restoration
- 2022MNRAS.515..543C (2022): FAUST VI. VLA1623-2417 B: a new laboratory for astrochemistry around protostars on 50 au scale
- 2022MNRAS.517.2546L (2022): High-resolution ALMA and HST imaging of κCrB: a broad debris disc around a post-main-sequence star with low-mass companions
- 2022PASJ...74..738T (2022): ALMA astrometry of the objects within 0.5 pc of Sagittarius A<SUP>*</SUP>
- 2023A&A...669A..53B (2023): Sulphur monoxide emission tracing an embedded planet in the HD 100546 protoplanetary disk
- 2023A&A...674A.113I (2023): The Disc Miner. II. Revealing gas substructures and kinematic signatures from planet-disc interaction through line profile analysis
- 2023A&A...675A.131T (2023): Investigating the asymmetric chemistry in the disk around the young star HD 142527
- 2023A&A...677A..80W (2023): ALMA and VLBA views on the outflow associated with an O-type protostar in G26.50+0.28
- 2023A&A...678A.146B (2023): Tracing snowlines and C/O ratio in a planet-hosting disk. ALMA molecular line observations towards the HD 169142 disk
- 2023A&A...678A.160E (2023): FAUST. X. Formaldehyde in the protobinary system [BHB2007] 11: Small-scale deuteration
- 2023ApJ...948..110Y (2023): Multiple Rings and Asymmetric Structures in the Disk of SR 21
- 2023ApJ...948L...2Y (2023): Eccentric Dust Ring in the IRS 48 Transition Disk
- 2023ApJ...953L...6P (2023): Detection of a High-velocity Jet from MWC 349A Traced by Hydrogen Recombination Line Maser Emission
- 2023ApJ...956..135W (2023): Deep Search for Molecular Oxygen in TW Hya
- 2023ApJ...956L..45G (2023): An SiO Toroid and Wide-angle Outflow Associated with the Massive Protostar W75N(B)-VLA2
- 2023ApJ...958...98F (2023): Early Planet Formation in Embedded Disks (eDisk). XII. Accretion Streamers, Protoplanetary Disk, and Outflow in the Class I Source Oph IRS …
- 2023MNRAS.518.4481L (2023): Dynamical mass measurements of two protoplanetary discs
- 2023MNRAS.519L..68B (2023): Positive feedback, quenching, and sequential super star cluster (SSC) formation in NGC 4945
- 2023MNRAS.522.2384M (2023): FAUST - VIII. The protostellar disc of VLA 1623-2417W and its streamers imaged by ALMA
- 2023NatAs...7...49C (2023): UV-driven chemistry as a signpost of late-stage planet formation
- 2023NatAs...7..684K (2023): Azimuthal C/O variations in a planet-forming disk
- 2023PASJ...75..225M (2023): An expanding ring of the hypercompact H II region W 49 N:A2
- 2023PASJ...75..424O (2023): ALMA Band 6 high-resolution observations of the transitional disk around SY Chamaeleontis
- 2024A&A...682A..55M (2024): High-resolution ALMA observations of compact discs in the wide-binary system Sz 65 and Sz 66
- 2024A&A...682A..61C (2024): A dusty streamer infalling onto the disk of a class I protostar. ALMA dual-band constraints on grain properties and the mass-infall rate
- 2024A&A...682A.143P (2024): A dynamic view of V Hydrae. Monitoring of a spectroscopic-binary AGB star with an alkaline jet
- 2024A&A...684A.174P (2024): High turbulence in the IM Lup protoplanetary disk. Direct observational constraints from CN and C<SUB>2</SUB>H emission
- 2024A&A...686A...9M (2024): Rotation curves in protoplanetary disks with thermal stratification. Physical model and observational evidence in MAPS disks
- 2024A&A...686A.120U (2024): Vertical and radial distribution of atomic carbon in HD 163296
- 2024A&A...686A.146Z (2024): Gas inflows from cloud to core scales in G332.83-0.55: Hierarchical hub-filament structures and tide-regulated gravitational collapse
- 2024A&A...686A.235P (2024): Candidate young stellar objects in the S-cluster: Kinematic analysis of a subpopulation of the low-mass G objects close to Sgr A*
- 2024A&A...687A.188K (2024): Recovering the gas properties of protoplanetary disks through parametric visibility modeling: MHO 6
- 2024A&A...687A.299L (2024): Chemistry across dust and gas gaps in protoplanetary disks. Modelling the co-spatial molecular rings in the HD 100546 disk
- 2024A&A...687A.308S (2024): Constraining the stellar masses and origin of the protostellar VLA 1623 system
- 2024A&A...687A.311A (2024): V892 Tau: A tidally perturbed circumbinary disc in a triple stellar system
- 2024A&A...688A.149D (2024): Disk Evolution Study Through Imaging of Nearby Young Stars (DESTINYS): PDS 111, an old T Tauri star with a young-looking disk
- 2024A&A...689A..65R (2024): ALMA high-resolution observations unveil planet formation shaping molecular emission in the PDS 70 disk
- 2024A&A...689A..85G (2024): MINDS: A multi-instrument investigation into the molecule-rich JWST-MIRI spectrum of the DF Tau binary system
- 2024A&A...690A..46S (2024): Early Planet Formation in Embedded Disks (eDisk): XVI. Asymmetric dust disk driving a multicomponent molecular outflow in the young Class 0…
- 2024A&A...690A.185W (2024): Dynamical accretion flows: ALMAGAL: Flows along filamentary structures in high-mass star-forming clusters
- 2024A&A...692A.151S (2024): Uncovering the structure and kinematics of the ionized core of M 2-9 with ALMA
- 2024A&A...692A.155K (2024): Binary orbit and disks properties of the RW Aur system using ALMA observations
- 2024A&A...692A.181Z (2024): Fine structure and kinematics of the ionized and molecular gas in the jet and disk around S255IR NIRS3 from high-resolution ALMA observatio…
- 2024AJ....167...66Y (2024): Chemistry of Complex Organic Molecules in the V883 Ori Disk Revealed by ALMA Band 3 Observations
- 2024AJ....167...72D (2024): ALMA Survey of Orion Planck Galactic Cold Clumps (ALMASOP): Molecular Jets and Episodic Accretion in Protostars
- 2024AJ....167...77D (2024): JWST Imaging of Edge-on Protoplanetary Disks. I. Fully Vertically Mixed 10 μm Grains in the Outer Regions of a 1000 au Disk
- 2024AJ....167..164B (2024): An ALMA Molecular Inventory of Warm Herbig Ae Disks. I. Molecular Rings, Asymmetries, and Complexity in the HD 100546 Disk
- 2024AJ....167..165B (2024): An ALMA Molecular Inventory of Warm Herbig Ae Disks. II. Abundant Complex Organics and Volatile Sulphur in the IRS 48 Disk
- 2024ApJ...961...28H (2024): Dual-band Observations of the Asymmetric Ring around CIDA 9A: Dead or Alive?
- 2024ApJ...961..228S (2024): Ring Gap Structure around Class I Protostar WL 17
- 2024ApJ...963...72O (2024): Revealing Multiple Nested Molecular Outflows with Rotating Signatures in HH270mms1-A with ALMA
- 2024ApJ...964...34L (2024): Multiple Jets in the Bursting Protostar HOPS 373SW
- 2024ApJ...964..190L (2024): Mapping the Vertical Gas Structure of the Planet-hosting PDS 70 Disk
- 2024ApJ...965..147B (2024): The Carbon Isotopic Ratio and Planet Formation
- 2024ApJ...966...32E (2024): Early Planet Formation in Embedded Disks (eDisk). XIII. Aligned Disks with Nonsettled Dust around the Newly Resolved Class 0 Protobinary R …
- 2024ApJ...966...63Y (2024): The First Spatially Resolved Detection of <SUP>13</SUP>CN in a Protoplanetary Disk and Evidence for Complex Carbon Isotope Fractionation
- 2024ApJ...966..117X (2024): Disk Wind Feedback from High-mass Protostars. III. Synthetic CO Line Emission
- 2024ApJ...966..119L (2024): ALMA Spectral Survey of an Eruptive Young Star, V883 Ori (ASSAY). I. What Triggered the Current Episode of Eruption?
- 2024ApJ...967...15K (2024): Infall Motions in the Hot Core Associated with the Hypercompact H II Region G345.0061+01.794 B
- 2024ApJ...967...68H (2024): Radial and Vertical Constraints on the Icy Origin of H<SUB>2</SUB>CO in the HD 163296 Protoplanetary Disk
- 2024ApJ...969..165D (2024): Chemistry in Externally FUV-irradiated Disks in the Outskirts of the Orion Nebula Cluster
- 2024ApJ...970...28O (2024): CH<SUB>3</SUB>OH and Its Deuterated Species in the Disk/Envelope System of the Low-mass Protostellar Source B335
- 2024ApJ...970...74P (2024): The Evaporating Massive Embedded Stellar Cluster IRS 13 Close to Sgr A*. II. Kinematic Structure
- 2024ApJ...970..153A (2024): On Kinematic Measurements of Self-gravity in Protoplanetary Disks
- 2024ApJ...971L..15Y (2024): Outflow Driven by a Protoplanet Embedded in the TW Hya Disk
- 2024ApJ...972...88L (2024): Exploring the Complex Ionization Environment of the Turbulent DM Tau Disk
- 2024ApJ...973..135H (2024): Constraints on the Gas-phase C/O Ratio of DR Tau's Outer Disk from CS, SO, and C<SUB>2</SUB>H Observations
- 2024ApJ...974...83Y (2024): Detection of Dimethyl Ether in the Central Region of the MWC 480 Protoplanetary Disk
- 2024ApJ...974..102S (2024): Hints of Planet Formation Signatures in a Large-cavity Disk Studied in the AGE-PRO ALMA Large Program
- 2024ApJ...975...72B (2024): Measuring the <SUP>34</SUP>S and <SUP>33</SUP>S Isotopic Ratios of Volatile Sulfur during Planet Formation
- 2024ApJ...976..132H (2024): High-resolution ALMA Observations of Richly Structured Protoplanetary Disks in σ Orionis
- 2024ApJ...976..258K (2024): Chemistry in the GG Tau A Disk: Constraints from H<SUB>2</SUB>D<SUP>+</SUP>, N<SUB>2</SUB>H<SUP>+</SUP>, and DCO<SUP>+</SUP> High Angular R…
- 2024MNRAS.527.3559P (2024): The debris disc of HD 131488: bringing together thermal emission and scattered light
- 2024MNRAS.532L..36R (2024): HCN as a probe of the inner disc in a candidate proto-brown dwarf
- 2024MNRAS.534.2904C (2024): Observational signatures of circumbinary discs - II. Kinematic signatures in velocity residuals
- 2024NatAs...8..587F (2024): Resolved ALMA observations of water in the inner astronomical units of the HL Tau disk
- 2024RAA....24g5017M (2024): Investigating Sulfur Chemistry in the HD163296 Disk
- 2024Sci...383..988B (2024): A far-ultraviolet─driven photoevaporation flow observed in a protoplanetary disk
- 2025A&A...693A..76C (2025): Dissecting the disk and the jet of a massive (proto)star: An ALMA view of IRAS 20126+4104
- 2025A&A...693A.286S (2025): Intermediate mass T Tauri disk masses and a comparison to their Herbig disk descendants
- 2025A&A...694A..92B (2025): Protostellar Outflows at the EarliesT Stages (POETS) VI. Evidence of disk-wind in G11.92-0.61 MM1
- 2025A&A...694A.108P (2025): The two-dimensional pressure structure of the HD 163296 protoplanetary disk as probed by multi-molecule kinematics
- 2025A&A...694A.295P (2025): ALMA detections of circumstellar disks in the giant H II region M17: Probing the intermediate- to high-mass pre-main-sequence population
- 2025A&A...696A.202S (2025): ALMA-IMF: XVIII. The assembly of a star cluster: Dense N<SUB>2</SUB>H<SUP>+</SUP> (1─0) kinematics in the massive G351.77 protocluster
- 2025A&A...698A.115R (2025): Radial variations in the nitrogen, carbon, and hydrogen fractionation in the PDS 70 planet-hosting disk
- 2025A&A...699A..22M (2025): An accreting dwarf star orbiting the S-type giant star π<SUP>1</SUP> Gru
- 2025A&A...701A.141L (2025): Sulfur oxides tracing streamers and shocks at low-mass protostellar disk─envelope interfaces
- 2025A&A...703A..15M (2025): Discovery of carbon monoxide emission from five debris disks around young A-type stars
- 2025A&A...703A.282R (2025): Observations of sulfuretted species in HL Tau
- 2025A&A...704A...7P (2025): Closing the gap: Follow-up observations of peculiar dusty objects close to Sgr A<SUP>*</SUP> using ERIS
- 2025ApJ...984L..10G (2025): exoALMA. V. Gaseous Emission Surfaces and Temperature Structures
- 2025ApJ...984L..13H (2025): exoALMA. VIII. Probabilistic Moment Maps and Data Products Using Nonparametric Linear Models
- 2025ApJ...984L..15P (2025): exoALMA. X. Channel Maps Reveal Complex <SUP>12</SUP>CO Abundance Distributions and a Variety of Kinematic Structures with Evidence for Emb…
- 2025ApJ...984L..18T (2025): exoALMA. XIII. Gas Masses from N<SUB>2</SUB>H<SUP>+</SUP> and C<SUP>18</SUP>O: A Comparison of Measurement Techniques for Protoplanetary Ga…
- 2025ApJ...984L..19Y (2025): exoALMA. XIV. Gas Surface Densities in the RX J1604.3−2130 A Disk from Pressure-broadened CO Line Wings
- 2025ApJ...984L..21B (2025): exoALMA. XVI. Predicting Signatures of Large-scale Turbulence in Protoplanetary Disks
- 2025ApJ...984L..22W (2025): exoALMA. XVII. Characterizing the Gas Dynamics around Dust Asymmetries
- 2025ApJ...985...84L (2025): A Multiline Analysis of the Distribution and Excitation of CS and H<SUB>2</SUB>CS in the HD 163296 Disk
- 2025ApJ...985..166K (2025): Early Planet Formation in Embedded Disks (eDisk). XXI. Limited Role of Streamers in Mass Supply to the Disk in the Class 0 Protostar IRAS 1…
- 2025ApJ...986L...9B (2025): Ice Sublimation in the Dynamic HD 100453 Disk Reveals a Rich Reservoir of Inherited Complex Organics
- 2025ApJ...986L..11S (2025): Hints of Disk Substructure in the First Brown Dwarf with a Dynamical Mass Constraint
- 2025ApJ...988L..44F (2025): A Deep Search for Ethylene Glycol and Glycolonitrile in the V883 Ori Protoplanetary Disk
- 2025ApJ...989....1Z (2025): The ALMA Survey of Gas Evolution of PROtoplanetary Disks (AGE-PRO). I. Program Overview and Summary of First Results
- 2025ApJ...989....3D (2025): The ALMA Survey of Gas Evolution of PROtoplanetary Disks (AGE-PRO). III. Dust and Gas Disk Properties in the Lupus Star-forming Region
- 2025ApJ...989...30Z (2025): SO Emission in the Dynamically Perturbed Protoplanetary Disks around CQ Tau and MWC 758
- 2025ApJ...989...41A (2025): Discovery of Jet─Bubble─Disk Interaction: Jet Feedback on a Protoplanetary Disk Via an Expanding Bubble in WSB 52
- 2025ApJ...989...56H (2025): ALMASOP. A Rotating Feature Rich in Complex Organic Molecules in a Protostellar Core
- 2025ApJ...991..176W (2025): Radiative Transfer Modeling of a Shadowed Protoplanetary Disk Assisted by a Neural Network
- 2025ApJ...992...18P (2025): Early Planet Formation in Embedded Disks (eDisk). XXII. Keplerian Disk, Disk Structures, and Jets/Outflows in the Class 0 Protostar IRAS 04…
- 2025ApJ...993...90S (2025): ALMA High-resolution Observation for the Transitional Disk Around IRAS 04125+2902
- 2025ApJ...994...98F (2025): Measuring the Two-dimensional Thermal Structures of Protoplanetary Disks
- 2025ApJ...994..214T (2025): Dynamical Masses for 23 Pre-main-sequence Stars in Upper Scorpius: A Critical Test of Stellar Evolutionary Models
- 2025ApJ...995L...7L (2025): The Rotation Dip in the Envelope─Disk Transition of HH 111: Evidence for Magnetic Braking
- 2025MNRAS.541...71M (2025): ALMA millimetre-wavelength imaging of HD 138965: new constraints on the debris dust composition and presence of planetary companions
- 2025MNRAS.544.3312P (2025): Sculpting protoplanetary discs ─ modelling circumbinary cavities at observable scales with radiation hydrodynamics
- 2025NatAs...9.1486L (2025): Pristine ices in a planet-forming disk revealed by heavy water
- 2025NatAs...9.1672Y (2025): Winding motion of spirals in a gravitationally unstable protoplanetary disk
- 2025NatAs...9.1833L (2025): Detection of a septuple stellar system in formation via disk fragmentation
- 2025PASJ...77..733T (2025): Nuclear stellar disk-like nature in the kinematics of SiO maser stars around Sagittarius A*
- 2025SciA...11.4512O (2025): Massive extended streamers feed high-mass young stars
- 2025SciA...11.6953M (2025): A misaligned protostellar disk fed by gas streamers in a barred spiral-like massive dense core
- 2026A&A...705A..49Z (2026): The <SUP>12</SUP>CO gas structures of protoplanetary disks in the Upper Scorpius region
- 2026A&A...705A..96M (2026): FAUST: XXVIII. High-resolution ALMA observations of Class 0/I disks: Structure, optical depths, and temperatures
- 2026A&A...705A.193L (2026): Zooming into the water snow line: High-resolution water observations of the HL Tau disk
- 2026A&A...705A.198M (2026): The ALMA survey to Resolve exoKuiper belt Substructures (ARKS): IV. CO gas imaging and overview
- 2026A&A...705A.201B (2026): The ALMA survey to Resolve exoKuiper belt Substructures (ARKS): VII. Optically thick gas with broad CO gaussian local line profiles in the …
- 2026A&A...705A.202M (2026): The ALMA survey to Resolve exoKuiper belt Substructures (ARKS): VIII. A dust arc and non-Keplerian gas kinematics in HD 121617
- 2026A&A...705A.203W (2026): The ALMA survey to Resolve exoKuiper belt Substructures (ARKS): IX. Gas-driven origin for the continuum arc in the debris disc of HD121617
- 2026A&A...708L...1Z (2026): Benchmarking pre-main sequence stellar evolutionary tracks using disk-based dynamical stellar masses
- 2026A&A...710A.140M (2026): Observations of highly inclined disks with ALMA: Results from <SUP>12</SUP>CO gas and continuum observations
- 2026A&A...713A.149V (2026): Challenges in probing turbulent and magnetic support in cores: The W43-MM1 protocluster case study
- 2026AJ....172..108L (2026): Formation of a Protostellar Multiple System via Rotational Fragmentation
- 2026ApJ...997L..19Q (2026): Isotopic Ratios in the Disk of HD 163296
- 2026ApJ...999...62H (2026): HOPS-288: A Laboratory for Complex Organics in Proto-binary/Proto-multiple Systems
- 2026ApJ...999..145T (2026): Older Ages for 23 Pre-main Sequence Stars in Upper Scorpius Using Dynamical-mass-constrained Stellar Evolutionary Models
- 2026ApJ..1000L..15F (2026): exoALMA XXII: A Two-dimensional Atlas of Deviations from Keplerian Disks
- 2026ApJ..1002..176C (2026): JWST/MIRI Hydrocarbon and Water Absorption in the Wind of a Young Disk: Signatures of Pebble Drift and Carbon Grain Sublimation
- 2026ApJ..1003...64Y (2026): Compact Hydrogen Sulfide Emission Indicates Sulfur-bearing Ice Sublimation in the Inner Disk of HD 163296
- 2026ApJ..1003..219W (2026): The Keplerian Disk, Envelope, and Streamers Surrounding an Early O-type Protostar in the Sagittarius C Cloud of the Central Molecular Zone
- 2026ApJ..1003L..30W (2026): First Detection of HC<SUB>5</SUB>N in a Class II Disk around TW Hya
- 2026ApJ..1005..199C (2026): The ALMA Survey of Gas Evolution of PROtoplanetary Disks (AGE-PRO): Formaldehyde (H<SUB>2</SUB>CO) Emission and Its Links to Disk Properties
- 2026ApJ..1009L...3B (2026): Searching for Embedded Protoplanets with the Keck/NIRC2 Vortex Coronagraph: Confirmation of a Core-accretion Planet in the Narrow Gap of th…
- 2026MNRAS.545f2150S (2026): HD 44892: the youngest (or oldest?) gas-harbouring debris disc around an intermediate-mass star
- 2026MNRAS.551g1411H (2026): Accurate proper motions of the protostellar system VLA 1623-2417
- 2026MNRAS.551g1639M (2026): Exploring the survivability of higher-order multiple protostellar systems - the case of VLA1623
- 2026MNRAS.551g1645K (2026): A high-velocity SiO jet from S255N SMA3
- 2026MNRAS.552g1700S (2026): Dust substructures and line perturbations driven by a forming planet in J16120
