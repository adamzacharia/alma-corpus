---
name: alma-polarization-magnetic-fields
description: "Calibrate, image and interpret ALMA full-polarization data: Stokes I/Q/U/V imaging, debiased polarized intensity, fraction and angle maps, deciding between magnetic grain alignment, radiative alignment and dust self-scattering, plane-of-sky field morphology, DCF and structure-function field strengths, Zeeman and Goldreich-Kylafis line polarization, and Faraday rotation of compact synchrotron sources. Use when a user has or wants ALMA polarization data, asks about B-field maps, polarization vectors, DCF, grain alignment vs scattering in disks, Stokes V or rotation measures. Built from 109 ALMA papers (2013-2026), about 55 of them on-topic polarimetry."
---

# Dust polarization, line polarization and magnetic fields

ALMA measures linear polarization (Stokes Q, U) and, less reliably, circular polarization (Stokes V). Papers use it
for three different things: the plane-of-sky magnetic field direction (dust E-vectors rotated by 90 deg), grain size
(self-scattering in disks), and field strength (DCF from angle dispersion, or Zeeman splitting in lines). Two
mistakes matter most: rotating vectors by 90 deg before showing the emission comes from magnetically aligned,
optically thin dust, and trusting polarization fractions from filtered, low-S/N or off-axis interferometer maps.

Counts are from the evidence pack (`skills/packs/polarization-magnetic-fields.md`). The pack was tagged by regex,
so many of its 109 papers are off-topic. By my count of the pack's paper list, about 55 are ALMA polarimetry papers:
17 on protostellar envelopes, cores and clumps, 13 on protoplanetary disks, 8 on line or maser polarization, 14
on compact synchrotron sources (AGN, GRBs, Sgr A*, calibrators) and 2 on galaxies. I left out near-IR scattered-light
polarimetry (for example 2020MNRAS.492.1531M, 2018A&A...620A..75K), star-formation-law papers that only set
B = 0 (2018MNRAS.477.4380S, 2019MNRAS.487.4305S) and papers matched on unrelated words. Aggregate counts (software,
"not stated" settings) cover all 109 papers and are labelled as pack aggregates.

## Agent checklist

1. Never rotate E-vectors by 90 deg until the mechanism is decided (Step 5). In disks, three mechanisms compete:
   self-scattering, radiative (k-RAT) alignment and magnetic alignment.
2. An inclined disk with E-vectors parallel to the minor axis at ~1% is the textbook self-scattering pattern
   (2016ApJ...831L..12K, 2018ApJ...859..165S), but a projected toroidal field with magnetically aligned grains can
   also give E along the minor axis over much of the disk (general practice). Geometry alone does not decide it.
3. The deciding test is wavelength: scattering polarization depends strongly on wavelength relative to grain size,
   so the fraction and pattern change between bands, often to azimuthal at longer wavelength (2018A&A...616A..56A,
   2020ApJ...893...54Y, 2017ApJ...851...55S). Ask for (or find in the archive) a second band before any field claim.
4. Also check optical depth (peak T_b against dust temperature, 2020ApJ...893...54Y) and compare with a
   scattering forward model (RADMC-3D, 2016ApJ...831L..12K).
5. No DCF or structure-function field strengths when scattering or radiative alignment can explain the pattern:
   those methods assume magnetically aligned grains tracing B.
6. Instrumental limits (general practice, ALMA polarimetry specification): per-antenna D-terms of order 1% are
   solved and removed; the residual calibrated leakage is about 0.1% of Stokes I within the inner third of the
   primary beam and larger off-axis. A 1% disk signal on-axis is well above it; off-axis or < 0.3% signals are not.
7. Debias polarized intensity, cut at P/sigma_P >= 3, and quote angle uncertainties (Step 4).

## When to use

- Dust continuum polarization in Class 0/I envelopes, cores and massive clumps, to map the plane-of-sky field
  (2018ApJ...859..165S, 2019ApJ...879...25K, 2020ApJ...893...54Y, 2019A&A...626A..36D, 2025ApJ...992..103Z).
- Protoplanetary disk polarization, to tell scattering from alignment and constrain maximum grain size
  (2016ApJ...831L..12K, 2017ApJ...851...55S, 2018ApJ...860...82H, 2018ApJ...864...81O, 2025ApJ...990..183U).
- Field strength estimates: DCF or structure function on dust or line angles (2019ApJ...884...48C,
  2020ApJ...896..157H, 2024A&A...686A.274V), or Zeeman limits from CN or SiO masers (2021ApJ...908..141H,
  2019A&A...624L...7V, 2017A&A...603A..92V).
- Molecular line polarization (Goldreich-Kylafis, radiative alignment, masers) in evolved-star envelopes and jets
  (2024A&A...686A.274V, 2018NatCo...9.4636L).
- Linear polarization and rotation measure of compact synchrotron sources: AGN cores and jets, GRB afterglows,
  Sgr A* (2024ApJ...975..103P, 2019ApJ...878L..26L, 2018ApJ...868..101B, 2019MNRAS.489..470G).
- Ordered fields in external or high-z galaxies (2020ApJ...893...33L, 2023Natur.621..483G).

## When not to use

- **Only XX and YY were recorded (no cross-hands).** Full Stokes imaging is impossible. Papers instead fit the
  XX/YY ratio against parallactic angle (2016A&A...593A..44L, Stokes U then undetermined), use dual differential
  polarimetry (2016A&A...593A..61M), or report |Q/I| = (XX-YY)/2I as a lower limit (2020ApJ...891...80M).
- **You need a field strength from unresolved dust polarization.** 2023Natur.621..483G states the strength cannot
  be reliably estimated from their z=2.6 dust data; report orientation and ordered fraction only.
- **You need circular polarization from older-cycle data.** Stokes V was unreliable in Cycle 3
  (2019MNRAS.489..470G) and not assured in Cycle 5 (2020ApJ...896..157H); 2018ApJ...864...81O ignored V because it
  was not characterized. For extended lines, V is dominated by beam effects (2024A&A...686A.274V).
- **One wavelength and a disk.** A single band cannot separate scattering from alignment (2018ApJ...864...81O).
  Get a second band or treat the mechanism as unknown.
- **Near-IR polarized scattered light** (SPHERE, NaCo) is a different technique; this skill covers ALMA mm/submm.

## Steps

1. **Polarization calibration.** Goal: remove leakage (D-terms), cross-hand delay and XY phase. Papers use the
   ALMA polarization calibration scripts (2024A&A...686A.274V, 2023Natur.621..483G) or rerun them by hand in CASA:
   `gaincal` without a polarization model, `qufromgain` for the calibrator Q/U, `gaincal` with `gaintype='KCROSS'`
   and `'XYf+QU'`, `xyamb`, then `polcal` for D-terms (2016ApJ...824..132N, 2020ApJ...895...64L,
   2024ApJ...975..103P). Leakage needs wide parallactic-angle coverage of the polarization calibrator, about 90 deg
   in 2019ApJ...878L..26L. 2020ApJ...895...64L repeated the whole calibration with a second reference antenna of a
   different architecture.
2. **Self-calibrate on Stokes I and apply to all correlations.** Phase-only rounds are typical: four rounds
   (2020A&A...644A..11L), two rounds with solint 'inf' then 'int' (2024A&A...686A.274V), final solint 90 s
   (2019ApJ...884...48C). 2024A&A...686A.274V also corrected an amplitude re-normalisation problem first.
3. **Image Stokes I, Q, U (and V).** `tclean` with `stokes='IQUV'`. Briggs robust 0.5 is the most common choice
   (my count of the pack's key-parameter lines: 16 papers, a few of them off-topic such as 2024Ap&SS.369...18M, e.g. 2018ApJ...864...81O, 2020ApJ...893...54Y,
   2025ApJ...992..103Z). For multi-band comparisons, image every band on a common uv range (27-1310 klambda in
   2018A&A...616A..56A; "same uv distance" in 2025NatAs...9..526O) and smooth to a common beam. Other settings seen:
   multiscale at angular scales 0, 0.3, 0.9 arcsec (2016ApJ...831L..12K; CASA `scales` takes pixels, so divide by
   your cell size before copying); `nterms=2`, cell 0.2", robust 1 (2024ApJ...975..103P);
   threshold 10 uJy (2023Natur.621..483G). 2018ApJ...859..165S primary-beam corrected all four Stokes maps;
   2020A&A...644A..11L skipped primary-beam correction for its statistics.
4. **Derive debiased polarized intensity, fraction and angle.** Most papers use the high-S/N approximation
   PI = sqrt(Q^2 + U^2 - sigma_PI^2), P = PI/I, chi = 0.5 arctan(U/Q) (2020ApJ...893...54Y, 2018ApJ...859..165S,
   2025NatAs...9..526O, 2024A&A...686A.274V). sigma_PI is the Q/U noise from emission-free regions, assuming
   sigma_Q ~ sigma_U (2018ApJ...859..165S; 2024A&A...686A.274V uses the mean of sigma_Q and sigma_U;
   2020ApJ...896..157H measures it in emission-free channels). Where Q^2 + U^2 < sigma_PI^2 the estimate is
   undefined: mask the pixel or report an upper limit, do not take the square root of a negative number (general
   practice). Compute fractions only where Stokes I is also detected (I and PI both S/N > 3, 2020ApJ...893...54Y).
   At low S/N, especially on point sources, debias by Monte Carlo over Q, U instead (1e5 draws,
   2019ApJ...878L..26L). Use a two-argument arctangent (atan2, 2019ApJ...884L..58U). Tools: CASA `immath` modes
   `POLI`/`POLA` (2024ApJ...975..103P), MIRIAD `impol` (2020ApJ...899..152H). Angle error at high S/N, written with
   polarized-intensity noise: sigma_chi = 0.5 sigma_PI/PI radians = 28.65 deg x sigma_PI/PI (2025ApJ...992..103Z
   writes sigma_p/I_p with I_p the polarized intensity; 2020ApJ...896..157H writes Delta P / 2P, also radians).
   Do not use the fractional-polarization error here (it carries Stokes I noise, which does not affect the angle);
   when Q and U noise differ or correlate, propagate the Q/U covariance (general practice). Keep only pixels above a
   PI threshold (see table), sample about Nyquist (0.1" pixels, 2020ApJ...893...54Y; 4 pixels per beam,
   2020A&A...644A..11L), and stay inside the inner third of the primary beam (2019A&A...626A..36D,
   2020A&A...640A.111A, 2018ApJ...861...91H).
5. **Decide the polarization mechanism before rotating.** Candidates: magnetic alignment, radiative (k-RAT)
   alignment, self-scattering. Tests papers use:
   - Wavelength dependence: fraction 7.9, 5.3, 3.5% in Bands 3, 6, 7 (2018A&A...616A..56A); orientations at 0.87
     and 1.3 mm differ by 5 +- 4 deg with fraction 1.7x higher at 1.3 mm (2020ApJ...893...54Y); pattern changes with
     wavelength in HL Tau (2017ApJ...851...55S).
   - Morphology: vectors versus disk minor axis (2018ApJ...859..165S), vector flips explained by scattering
     (2016ApJ...831L..12K), offset between angle and radial direction versus azimuth for radiative alignment
     (2018ApJ...864...81O, 2019MNRAS.483.2371Y).
   - Optical depth: peak brightness temperature 30 K against dust temperature 67 K (2020ApJ...893...54Y); spectral
     index with beta = alpha - 2 only under thin Rayleigh-Jeans assumptions (2018A&A...616A..56A).
   - Forward models: RADMC-3D self-scattering (2016ApJ...831L..12K, 2024ApJ...963..134Y), aligned Mie grains
     (2020A&A...634L..15G). 2025ApJ...990..183U used the rough approximation P ~ C P90 omega_eff with C ~ 0.02
     (omega_eff the effective albedo) only as an MCMC prior; its composition preference within 40 au came partly
     from the priors and high optical depth, and it assumed a constant filling factor and a smooth gas disk. Treat
     such a relation as model-dependent: rerun without the prior and check optical depth before reading grain
     properties from it.
   Rotate by 90 deg only when the evidence favours alignment with the magnetic field specifically (not radiative
   alignment, not scattering) and the emission is optically thin (2020ApJ...893...54Y, 2019ApJ...879..101L,
   2020A&A...640A.111A). Thinness plus "aligned grains" is not enough, because radiatively aligned grains also
   polarize. If the alignment axis stays uncertain, show and analyse E-vectors and say so.
6. **Analyse field morphology.** Compare B segments with outflow axes or core orientation and test against random
   (histograms and K-S tests, 2025ApJ...992..103Z, 2020A&A...640A.111A). Compare with models through synthetic
   observations: DustPol + `simobserve`/`simanalyze` over a grid of k = B_p/B_phi (2018A&A...616A..56A), non-ideal
   MHD + SPARX + CASA simulator, scored by the fraction of segments within 30 deg (2020ApJ...893...54Y; its
   misaligned run also used a different cosmic-ray ionization rate and neither run reproduced the intensity
   morphology or N-S asymmetry, so a better angle score there does not isolate the effect of misalignment), toroidal
   torus field with CLUMPY/HYPERCAT (2020ApJ...893...33L), chi-square fit of |B_r|:|B_phi|:|B_z|
   (2025NatAs...9..526O), analytic hourglass matched by eye (2018ApJ...859..165S). For population statistics use
   the angle dispersion function S and P (n = 8 neighbours, lag about half a beam, 2020A&A...644A..11L).
7. **Estimate field strength (optional, order of magnitude).**
   - DCF (general practice): B_pos = xi sqrt(4 pi rho) sigma_v / sigma_phi in cgs (rho in g cm^-3, sigma_v in
     cm s^-1, B in gauss), with sigma_phi in radians and sigma_v the one-dimensional non-thermal velocity dispersion
     (thermal part removed). A line FWHM is not sigma_v: divide a Gaussian FWHM by 2.355 first. xi = 0.5 in
     2020ApJ...896..157H and 2019A&A...626A..36D (card: "correction factor xi=0.5", after Crutcher et al. 2003).
     Variant B0 ~ sqrt(8 pi rho) sigma_v / alpha with alpha from a dispersion/structure function fit
     (2020ApJ...893...33L).
   - sigma_phi: remove the ordered field first. 2020ApJ...896..157H convolved Stokes I, Q and U with a 0.5" Gaussian,
     derived a low-resolution angle map from them, and subtracted it from the 0.1" angle map;
     2019ApJ...879...25K smoothed Q and U with a beam three times larger along both axes (card, "Magnetic field
     strength"). Smooth Q and U, never the angles themselves, and wrap angle residuals into -90..+90 deg before
     taking a dispersion (general practice; angles are 180-deg ambiguous). Alternatives: the EVPA standard deviation
     over regions with at least 10 independent Nyquist points (2019ApJ...884...48C), or the circular-mean variance
     (2019A&A...626A..36D).
   - Structure function fits (Hildebrand/Houde/Koch style) give B_t/B_0 and the number of turbulent cells:
     0.061 +- 0.001 and N ~ 1.2 within ~2" (2024A&A...686A.274V); 0.062 +- 0.025 (2020ApJ...893...33L).
     2024A&A...686A.274V assumes the field is frozen into the gas and the turbulence is isotropic, incompressible
     and made of transverse Alfven waves; state these assumptions, and show the polarization you use traces B
     (for line polarization, that the G-K or alignment mechanism ties the angle to the field) before applying it.
   - sigma_v from a dense-gas line (H13CO+, 2019ApJ...884...48C; 13CS sigma ~0.8 km/s, 2017ApJ...847...92H).
     2020ApJ...896..157H quotes "Delta V ~ 10 km/s" without saying in the pack whether it is a FWHM or a dispersion;
     check the convention before reusing such numbers.
   - Density: there is no transferable default. Derive n for your source and tracer, from dust mass and an assumed
     geometry, and carry its uncertainty. Values in the pack are source-specific: n(H2) = 1e6 cm^-3 in
     2020ApJ...896..157H was adopted to satisfy the SiO maser-pumping model; n_H2 >~ 2e6 cm^-3 in
     2018NatCo...9.4636L; a whole-torus median rho = 1.4e-22 g cm^-3 that makes B an upper limit in
     2020ApJ...893...33L.
   - Total field: 2020ApJ...896..157H converts B_pos to ~30 mG with 4B/pi (citing Crutcher 2004). That factor is a
     statistical average over random field orientations, not a measurement for one source; label it as such.
8. **Zeeman and line polarization (if lines).** For CN 2-1, 2021ApJ...908..141H shifted Stokes I and V by the
   Keplerian velocity with `gofish`, then fit every unblended hyperfine component j jointly:
   V_j = C1 I_j + C2 dI_j/dnu + 0.5 B Z_j dI_j/dnu, with C1 and C2 shared nuisance coefficients
   (general practice: C1 absorbs I-to-V leakage, C2 a derivative-shaped instrumental term) and Z_j the Zeeman coefficient of component j (Hz per unit field;
   it differs between components). B is the line-of-sight field B_LOS. Only the joint fit over components with
   different Z_j separates B from C2; on a single component they multiply the same dI/dnu and are degenerate.
   Uncertainties from the per-channel rms outside the disk; 3-sigma upper limits. State the sign convention for V
   and B_LOS you use (the pack does not give one). SiO masers: V proportional to dI/dnu with z ~ 1500 s^-1 G^-1
   (2017A&A...603A..92V). 2020ApJ...896..157H fit V = b dI/dnu with g Omega/2pi = 230 Hz/G, but rejected the
   result: the implied fields of ~10 G were "implausible" and the J=1-0 and 2-1 transitions gave opposite signs.
   Before accepting any maser Zeeman field, rule out instrumental V (leakage, beam squint, Cycle-dependent V
   calibration) and non-Zeeman origins, and check consistency across transitions. Linear
   line polarization modelled with PORTAL on LIME output (2024A&A...686A.274V) or a G-K code with LAMDA rates
   (2020ApJ...899..152H).
9. **Compact synchrotron sources.** Fit Q and U with position and beam fixed from Stokes I (`imfit`,
   2019ApJ...878L..26L, 2020ApJ...895...64L). For rotation measure, image each SPW at matched resolution and fit
   EVPA versus lambda^2 linearly (CASA `rmfit`, 3-sigma polarized threshold, 2024ApJ...975..103P). That linear fit
   assumes a single Faraday screen and the same opacity at all wavelengths, and its card does not state how the
   n-pi ambiguity was handled; `rmfit` errors there excluded systematics. So check the single-screen and opacity
   assumptions, refit with alternative n-pi unwrappings, and add calibration systematics (EVPA, leakage) to the
   formal `rmfit` errors.

## Parameter defaults and ranges

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| Briggs robust (Stokes IQU) | 0.5 | -2 to 2, natural | 0.5: 16; 1: 3; natural: 3; 2: 2; -0.5: 2; 0: 1; -2: 1 (my count of papers per value over the key-parameter lines, natural also from excerpts; a paper listing several values, e.g. 2020ApJ...892..152H with 2.0, 0.5, -0.5, counts once under each) | 2018ApJ...864...81O; 2017ApJ...851...55S (1); 2020ApJ...893...33L (natural); 2018NatCo...9.4636L (2); 2017A&A...603A..92V (-0.5 continuum); 2018ApJ...861...91H (-2) |
| PI detection threshold (on PI or P/sigma_P) | 3 sigma_PI | 3-5 sigma | 3: 8; 4: 3; 5: 2 (my count of key-parameter and excerpt lines) | 2020ApJ...893...54Y, 2023Natur.621..483G (3); 2018ApJ...859..165S, 2020ApJ...896..157H (4); 2018A&A...616A..56A, 2024A&A...686A.274V (5) |
| Cut on Stokes Q and U separately | 3 sigma on each | | 1 | 2025ApJ...992..103Z |
| Debiasing | sqrt(Q^2+U^2-sigma^2), sigma_Q ~ sigma_U | MC (1e5 draws) at low S/N; none if >3 sigma | 5+ | 2020ApJ...893...54Y; 2019ApJ...878L..26L; 2016ApJ...831L..12K |
| Fraction uncertainty terms (dataset-specific, not universal floors) | estimate for your data | MDP 0.1%; systematic 0.03%; 1-sigma fraction uncertainty 0.1%; extra systematic ~0.09% of I; instrumental P error 0.1% | 5 | 2020ApJ...893...33L (MDP, systematic); 2023Natur.621..483G (0.1% MDP in quadrature); 2018ApJ...859..165S (1-sigma); 2020ApJ...895...64L (systematic); 2017ApJ...851...55S (instrumental) |
| Usable field | inner 1/3 of primary beam | on-axis <=20", off-axis 20-60" checked | 4 | 2019A&A...626A..36D; 2020A&A...640A.111A; 2024ApJ...975..103P |
| D-term level (uncalibrated per-antenna leakage, removed by polcal; residual after calibration ~0.1% on-axis, general practice) | ~1% per antenna | repeat solutions agree within 0.5% | 2 | 2019ApJ...878L..26L; 2016ApJ...824..132N |
| Residual calibrator polarization | ~0.1% | <0.02% stability on phase calibrator | 2 | 2020ApJ...895...64L; 2019ApJ...884L..58U |
| Parallactic angle coverage | ~90 deg | | 1 | 2019ApJ...878L..26L |
| Absolute EVPA accuracy (dataset-specific) | derive for your array | 0.4 deg, from a 2 deg feed misalignment averaged over 29 antennas | 1 | 2016ApJ...824..132N |
| Angle error (high S/N) | 28.65 deg x sigma_PI/PI (PI = polarized intensity) | <~9 deg at S/N>3; <7 deg at S/N>=4 | 3 | 2025ApJ...992..103Z; 2020ApJ...893...54Y; 2020ApJ...896..157H |
| Self-cal (Stokes I) | phase-only, 2-4 rounds | solint inf/int to 90 s | 4 | 2020A&A...644A..11L; 2024A&A...686A.274V; 2019ApJ...884...48C |
| DCF correction xi | 0.5 | | 2 (1 in pack lines, 1 from card) | 2020ApJ...896..157H; 2019A&A...626A..36D (card, section 4.5.1) |
| DCF sigma_v | 1D non-thermal dispersion (not FWHM) | ~0.8 km/s (13CS); Delta v_los ~15 km/s; 10 km/s | 3 | 2017ApJ...847...92H; 2018NatCo...9.4636L; 2020ApJ...893...33L |
| DCF sigma_phi | 4-10 deg | 5 +- 2 deg; 0.38 rad; 30 +- 20 deg | 5 | 2020ApJ...896..157H; 2019ApJ...879...25K (10 deg, card results table); 2020ApJ...893...33L; 2018MNRAS.477.2760M; 2018NatCo...9.4636L |
| DCF density | no default: source- and tracer-specific | 1e6 cm^-3 (set by maser-pumping model); n_H2 >~ 2e6; whole-torus median 1.4e-22 g cm^-3 (upper limit on B) | 3 | 2020ApJ...896..157H; 2018NatCo...9.4636L; 2020ApJ...893...33L |
| Self-scattering a_max | ~100-150 um | best-fit or adopted values 61-150 um; the reported constraint in 2016ApJ...831L..12K spans ~40-300 um | 4 | 2018ApJ...860...82H (61); 2016ApJ...831L..12K (~150, range ~40-300); 2024ApJ...963..134Y (140); 2019MNRAS.482L..29D (~100) |
| Model-data agreement | within 30 deg | mean residual 20-23 deg | 2 | 2020ApJ...893...54Y; 2018A&A...616A..56A |
| RM fit | linear chi vs lambda^2 over 4 SPWs | | 1 | 2024ApJ...975..103P |

Longer tables and per-paper values are in `references/parameters.md`.

## Software

From the pack aggregates (all 109 papers, so some counts include off-topic uses):

| Tool | Use | Count |
|---|---|---|
| CASA (`gaincal` KCROSS/XYf+QU, `qufromgain`, `xyamb`, `polcal`, `tclean`, `immath` POLI/POLA, `imfit`, `rmfit`) | calibration, Stokes imaging, PI/angle maps, point-source and RM fits | casa 62, tclean 3, gaincal 2, imfit/casa imfit 3, polcal 1, qufromgain 1, xyamb 1 |
| MIRIAD (`impol`, `imfit`, `gpcal options=qusolve`, `imdiff`) | debiasing, Gaussian fits, CARMA leakage, XX/YY comparisons | 6 (+ imdiff 1) |
| RADMC-3D | self-scattering and alignment radiative transfer | 6 |
| MCFOST | disk radiative transfer (mostly in near-IR papers) | 3 |
| gofish | Keplerian shifting before Zeeman fits | 2 |
| emcee | MCMC with polarization priors | 2 |
| UVMultiFit | visibility fits of compact sources | 2 |
| CASA simobserve/simanalyze | synthetic observations of B-field models | 2 |
| ARTIST DustPol, SPARX, PORTAL + LIME 1.9.5, G-K code (Yang & Lai 2010) | polarized RT for dust and lines | 1 each |
| lenstronomy | source-plane field for lensed galaxies | 1 |
| MrBeam (with ehtim, pygmo) | closure-trace polarimetric imaging | 2 |

## Pitfalls

- **Interferometric filtering inflates fractions.** Stokes I and Q/U resolve out differently (2016ApJ...831L..12K);
  missing CO flux overestimates line fractions by 2-3x (2024A&A...686A.274V); missing short baselines inflate P
  (2020ApJ...896..157H, 2020ApJ...899..152H, 2020A&A...644A..11L); 30-70% flux loss in 2019A&A...626A..36D.
- **Mechanism ambiguity.** One band cannot separate scattering from alignment, and optically thick regions hide
  midplane grains (2018ApJ...864...81O). Polarization may come from aligned grains rather than scattering, which
  makes derived fragmentation velocities very uncertain (2025ApJ...990...59Y). Polarization toward an embedded disk
  may be affected by self-scattering (2019ApJ...879..101L).
- **DCF is order of magnitude.** Authors say so (2019A&A...626A..36D, 2019ApJ...879...25K); outflows and collapse
  degrade it (2019ApJ...879...25K, card, "Magnetic field strength"); validity uncertain (2018MNRAS.477.2760M); sigma_v extrapolated by a Kolmogorov
  law (2019ApJ...884...48C); a whole-region mean density gives only an upper limit (2020ApJ...893...33L); a
  structure-function result is a lower limit if the field is not frozen in (2024A&A...686A.274V).
- **Instrumental systematics mimic signal.** A 0.27 +- 0.04% GRB afterglow detection (2019ApJ...884L..58U) became
  a 3-sigma upper limit of 0.30% after independent recalibration with a systematic term from the gain calibrator
  (2020ApJ...895...64L), which left the origin of the time-varying systematics uninvestigated. Stokes V detections may be spurious (2017ApJ...851...55S).
- **Off-axis and dynamic range.** Sources outside the inner third of the primary beam are unreliable
  (2018ApJ...861...91H); Stokes I dynamic range limits P interpretation (2020ApJ...892..152H, 2016ApJ...824..132N).
- **Rotation measure traps.** Phase wraps and low-polarization calibration errors make the largest RMs suspect
  (2018ApJ...868..101B); poor parallactic coverage in Bands 7/8 and EVPA variability can mimic RM
  (2019A&A...621A..18M); emission at different wavelengths may come from different regions, which breaks the
  single-screen, common-opacity assumption of a linear lambda^2 fit (2024ApJ...975..103P).
- **Zeeman traps.** Stacking red and mirrored blue sides cancels a vertical field (2021ApJ...908..141H). A
  V proportional to dI/dnu fit can return a number that is not a field: in 2020ApJ...896..157H the SiO fit implied
  ~10 G, judged implausible, with opposite signs between transitions.
- **Small samples and non-simultaneity.** Random versus preferred orientations cannot be separated with few cores
  (2020A&A...640A.111A, 2025ApJ...992..103Z); non-simultaneous multi-band data block joint fits
  (2019MNRAS.489..470G, 2019ApJ...884L..58U).
- **Models are rarely unique.** By-eye matches (2018ApJ...859..165S), non-unique models (2017ApJ...851...55S),
  reduced chi-square ~9-16 (2025NatAs...9..526O). Model comparisons can be confounded: the misaligned MHD run in
  2020ApJ...893...54Y also changed the cosmic-ray ionization rate and missed the intensity morphology.
- **What cards flag as not stated** (pack aggregate): CASA version (12), self-cal solution intervals (5, plus
  related variants), polarization debiasing method (2), polarization calibration details (several single entries).
  Report these explicitly.

## Verification checks

What papers did:
- Compare the polarization calibrator's fraction and angle with the ALMA Calibrator Source Catalogue
  (2018A&A...616A..56A) or monitoring programs (2020ApJ...899..152H).
- Check D-terms (~1%) and XX/YY gain ratio (within ~2% of unity, 2019ApJ...878L..26L); residual calibrator
  polarization after calibration (~0.1%, 2020ApJ...895...64L); on- and off-axis leakage below the analysis
  threshold (2024ApJ...975..103P); repeated D-term solutions on a second calibrator (2016ApJ...824..132N).
- Monte Carlo D-term and XY-phase errors to test a Stokes V result (2017A&A...603A..92V).
- Split the data: by sideband, by execution, by base-band, by antenna type, by reference antenna
  (2020ApJ...895...64L, 2019ApJ...878L..26L, 2016A&A...593A..44L).
- Stokes V rms close to thermal noise (2016ApJ...831L..12K).
- Smooth new data to an older beam and check fractions and angles agree (2018ApJ...864...81O,
  2018ApJ...859..165S).
- Neighbouring channels show the same structure, arguing against missing-flux artefacts (2024A&A...686A.274V);
  other channels give field strengths within 30% (2024A&A...686A.274V).
- Simulate the lens and convolution to show they do not rotate angles or change P (2023Natur.621..483G).
- Compare DCF strength with independent masers or scaling laws (2020ApJ...896..157H, 2020ApJ...893...33L).

What a careful referee adds:
- State the mechanism test that justifies the 90 deg rotation, with optical depth at the polarized positions.
- Quote sigma_I, sigma_Q, sigma_U, the debiasing formula and the threshold, and keep three things apart: the
  minimum detectable fraction, the statistical uncertainty, and the calibration systematic, each estimated for
  this dataset (published values range from 0.03% to 0.1%, see the table) rather than copied.
- Show the fraction is not driven by filtering: give the maximum recoverable scale and, if possible, compare with
  single-dish polarimetry.
- For DCF, give the ordered-field removal method, the number of independent beams, density and sigma_v sources, and
  the correction factor; quote at least a factor-of-2 uncertainty.

## Source cards

Full list: `references/sources.md`. Most informative for this skill:

- 2016ApJ...824..132N: step-by-step CASA polarization calibration and EVPA accuracy on 3C 286
- 2020ApJ...895...64L: independent recalibration, systematic error budget, upper limit
- 2019ApJ...878L..26L: leakage checks, fixed-position Q/U fits, Monte Carlo debiasing
- 2024ApJ...975..103P: Stokes imaging per SPW, leakage limits, `rmfit` rotation measure
- 2020ApJ...893...54Y: debiasing, two-band comparison, optical-depth check, MHD model scoring
- 2018A&A...616A..56A: three-band fractions, common uv range, DustPol model grid
- 2018ApJ...864...81O: radiative alignment test, resolution comparison, limits of one band
- 2016ApJ...831L..12K: self-scattering with RADMC-3D, filtering caveat
- 2017ApJ...851...55S: wavelength transition of the polarization pattern in HL Tau
- 2018ApJ...860...82H: scattering-derived a_max in IM Lup
- 2025NatAs...9..526O: 3D field components from multi-band disk polarization
- 2018ApJ...859..165S: thresholds, disk minor-axis test, hourglass model
- 2019A&A...626A..36D: DCF and structure function in a high-mass region, order-of-magnitude caveat
- 2019ApJ...884...48C: DCF variants and dispersion estimator
- 2020ApJ...896..157H: DCF on SiO line angles, Zeeman test of Stokes V
- 2020A&A...644A..11L: statistics of S and P across Class 0 cores
- 2025ApJ...992..103Z: relative orientation of fields across scales
- 2021ApJ...908..141H: CN Zeeman fitting with `gofish`
- 2024A&A...686A.274V: line polarization, PORTAL modelling, structure function
- 2020ApJ...893...33L: dust polarization and field strength in an AGN torus
- 2023Natur.621..483G: dust polarization in a lensed z=2.6 galaxy
