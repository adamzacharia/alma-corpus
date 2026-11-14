---
name: alma-solar-system-atmospheres
description: "Reduce ALMA spectral-line and continuum data of solar-system bodies (Titan, giant planets, comets, rings) and turn them into temperature profiles, vertical abundance profiles, isotopic ratios or brightness-temperature maps with a radiative-transfer retrieval (mostly NEMESIS). Use when a task involves Titan or planetary submillimeter spectra, ALMA flux-calibrator archival reuse of Titan, disk-averaged versus latitude-resolved extraction, NEMESIS retrieval settings, ephemeris and Doppler handling for moving targets, or comet coma isotopologue mapping. Built from 12 on-topic ALMA papers (2014-2025)."
---

# Solar-system atmospheres with ALMA (planets, Titan, comets)

ALMA measures rotational lines (CO, HCN, HC3N, HNC, CH3CN, CH3D, HDO and isotopologues) and the thermal
continuum of solar-system bodies. Papers image the body in its own rest frame, extract a disk-averaged or
regional spectrum, compare it with a radiative-transfer model integrated over many emission angles, then fit
temperature and abundance profiles. The Titan papers use different temperature strategies: temperature with CO
held at ~50 ppm (2024PSJ.....5..125T, 2018Icar..307..380T), CO and temperature retrieved together from a 50 ppm
a priori (2016ApJ...821L...8S), or an adopted temperature profile (2019AJ....157..219T). Trace gases are then
fit with temperature fixed.

The two mistakes that matter most: (1) treating the absolute flux scale as exact. Several Titan papers rescale
the data to the model continuum: 0.85-1.15 per spectral window (2024PSJ.....5..125T), a single factor of 1.047
(2019AJ....157..219T), and spectra about 10% off the Horizons flux model (2016ApJ...821L...8S). Whether to
rescale or keep the calibrated flux depends on the science goal (see Pitfalls). (2) Forgetting that the beam
is large compared with the disk. Latitude structure is smeared and disk-averaged spectra need many field-of-view points to model the
limb (2018Icar..307..380T, 2019Icar..319..417T).

**Evidence is thin.** The pack holds 13 papers. One (2017A&A...603L...6H, the TW Hya protoplanetary disk) is
off-topic and is ignored here. Of the 12 left, 9 are Titan, 1 Neptune (2019AJ....157..251T), 1 Uranian rings
(2019AJ....158...47M) and 1 comet (2025NatAs...9.1476C). Everything below about giant planets, rings and comets
rests on a single paper each. Titan practice is mostly from one group's NEMESIS pipeline, so "common choice"
often means "the same team reused its setup".

## When to use

- Titan stratosphere/mesosphere: temperature from CO lines, nitrile and hydrocarbon profiles (HCN, HC3N, HNC,
  CH3CN, C3H4, CH3D), isotopic ratios (12C/13C, 14N/15N, 16O/18O, D/H).
- Reusing ALMA archival Titan data taken as flux calibrator: 5 of the 12 papers are archival reuse
  (2016ApJ...821L...8S, 2018Icar..307..380T, 2019AJ....157..219T, 2019Icar..319..417T, 2020ApJ...890...95I).
- Giant-planet continuum maps of latitudinal brightness temperature (2019AJ....157..251T).
- Thermal emission from rings after subtracting the planet (2019AJ....158...47M).
- Comet coma isotopologue ratios such as D/H from HDO and H2O (2025NatAs...9.1476C).

## When not to use

- Protoplanetary-disk isotopic ratios (CN, HCN in disks): use `isotopic-ratios` or `chemical-modelling`; the
  one disk paper in this pack is off-topic for this skill.
- Generic imaging choices for a fixed sidereal source: use `imaging-choices`, `self-calibration`,
  `continuum-subtraction`.
- LTE column densities without a vertical atmosphere: use `rotational-diagram-lte`; non-LTE coma or envelope
  excitation beyond what is below: use `non-lte-excitation` or `radiative-transfer-modelling`.

## Steps

1. **Calibrate (or re-calibrate archival data).**
   - Goal: a calibrated MS with a Titan/planet flux scale you understand.
   - Method: run the archive/JAO calibration scripts in CASA, often modified or re-run with an updated Titan
     flux model (2016ApJ...821L...8S, 2018Icar..307..380T, 2019AJ....157..219T, 2019Icar..319..417T); or the
     pipeline/QA2 product (2020ApJ...890...95I, 2025NatAs...9.1476C, 2019AJ....158...47M, 2018ApJ...859L..15C).
   - Cards rarely state the pipeline or CASA version, calibrator names or flux-scale uncertainty; record them.
2. **Self-calibrate on the body itself when the continuum supports it.**
   - 2024PSJ.....5..125T ran phase-only self-cal on the combined continuum with a flat or limb-darkened disk
     starting model at the expected brightness temperature, iterated until the continuum phase distribution was
     about +/-10%, then applied the solutions to the line data. Phase self-cal is also used in
     2016ApJ...821L...8S and 2019AJ....158...47M. Solution intervals are almost never stated.
   - Do it only when the continuum S/N is high and the disk model is a fair description of the body; check
     that the solutions are stable and that the image improves before applying them (general practice, not
     shown in the pack beyond the 2024PSJ.....5..125T convergence criterion).
3. **Fix the position and the frequency frame.**
   - Shift spectral axes to the body's rest frame with JPL Horizons topocentric radial velocities
     (2016ApJ...821L...8S, 2018Icar..307..380T, 2014ApJ...795L..30C uses -0.91 km/s). Regrid before combining
     days (2019AJ....158...76C; 976 kHz channels in 2018ApJ...859L..15C).
   - For a comet, fit a point source to the continuum visibilities and move the peak to phase center with CASA
     `phaseshift`; then `uvcontsub` (2nd-order polynomial) and `cvel2` to the comet frame (2025NatAs...9.1476C).
4. **Continuum subtraction (lines) or planet subtraction (rings/maps).**
   - Lines: uv-plane continuum subtraction (2020ApJ...890...95I, 2025NatAs...9.1476C `uvcontsub`).
     2014ApJ...795L..30C says only "standard routines" in CASA 4.2.0, so its subtraction domain is
     unspecified. Line-free channels are not stated in at least 5 cards (pack "not stated" list).
   - Rings: subtract a Uranus disk model in the uv plane before `tclean` (2019AJ....158...47M). Planet maps:
     subtract a limb-darkened model to show residual bands (2019AJ....157..251T).
5. **Image.** CASA clean, Hogbom or Clark, natural weighting, small pixels, threshold near 2x RMS (table below).
   Neptune: natural weighting inside a circular mask, 1000-2000 iterations, stop when in-disk noise equals sky
   noise; uniform and intermediate weighting gave artificial speckles (2019AJ....157..251T).
6. **Extract spectra.**
   - Disk-averaged: integrate over solid disk plus atmosphere plus a PSF margin: 850 km + 3 sigma_PSF
     (2016ApJ...821L...8S), 2575 km + 1200 km + 2 sigma_PSF (2018Icar..307..380T), a circular aperture
     1.5 arcsec (12,000 km) in diameter centered on Titan (2014ApJ...795L..30C), or "a mask of pixels
     containing at least 90% of Titan's continuum flux" taken from an earlier paper (2019AJ....157..219T). The
     card flags that mask's definition as not stated: it could be a per-pixel threshold or a cumulative
     flux-enclosure region, so settle which before copying it.
   - Regional: North/Center/South footprints chosen to minimise beam overlap (2018Icar..307..380T,
     2019Icar..319..417T); latitude bins and East/West hemispheres (2024PSJ.....5..125T); radial wedges with a
     circularized beam (10 deg, 30 deg for weak species) for latitude and longitude profiles (2019AJ....158...76C;
     its authors call the ALMA retrievals from these only approximate, see Pitfalls).
   - Integrated maps: velocity windows of +/-1 km/s (HNC) and +/-5 km/s (HC3N) (2014ApJ...795L..30C).
7. **Put data and model in the same units, then decide on the flux scale.**
   - Units (general practice): summing Jy/beam pixels over an aperture gives Jy only after dividing by the
     beam area in pixels; a disk-averaged radiance is that flux density divided by the solid angle of the
     extraction region. State which quantity you fit.
   - Model (separate from the unit conversion): the forward model averages radiance over the disk and limb
     with a set of emission angles or field-of-view points: 24 angles to 1200 km (2019AJ....157..219T), 37-44
     points (2018Icar..307..380T, 2019Icar..319..417T), 24-27 points to 3425 km radius (2016ApJ...821L...8S), a
     10-point trapezium rule to 782 km (2014ApJ...795L..30C), or 30 angles per regional extraction location
     (2024PSJ.....5..125T).
   - Flux scale: the Titan papers forward-model continuum-only windows (collision-induced absorption from N2,
     CH4, H2) and rescale the data, per spectral window in 2024PSJ.....5..125T and by one factor in
     2019AJ....157..219T. This is a Titan line-retrieval choice, where the continuum is a known reference and
     the lines carry the science. When the continuum itself is the measurement (rings, giant-planet maps), keep
     the calibrated flux and propagate its uncertainty: 2019AJ....158...47M checks Uranus's total flux against
     earlier measurements instead, and 2019AJ....157..251T scales its maps to the nominal model only as an
     explicitly stated assumption.
8. **Retrieve or adopt temperature.** Pick one strategy and say which:
   - CO held fixed, temperature retrieved: CO 6-5 in Band 9 with CO ~50 ppm and tropospheric temperatures
     fixed to Cassini radio science (2024PSJ.....5..125T); CO 49.6 ppm with a CIRS/Huygens a priori, 5 K a
     priori errors and isothermal 160 K above 600 km (2018Icar..307..380T). In 2018Icar..307..380T the
     troposphere from Cassini radio/HASI is an a priori convolved with the ALMA beam, not a fixed profile.
   - CO and temperature retrieved together from a 50 ppm a priori, CO constant to 850 km (2016ApJ...821L...8S).
   - Temperature adopted, not retrieved: ALMA stratosphere plus HASI/radio-occultation troposphere, CO 50 ppm
     (2019AJ....157..219T).
   - For regional spectra, use the disk-averaged profile as the a priori (2018Icar..307..380T).
9. **Retrieve trace gases at fixed temperature.** Continuous profiles (2019Icar..319..417T,
   2024PSJ.....5..125T), a two-parameter gradient model (abundance at 293 km plus slope;
   2014ApJ...795L..30C, which assumes the profiles do not vary with latitude or longitude, so the fitted profile
   cannot also explain the asymmetries seen in its maps) or a simple scaling of an a priori profile for weak lines (CH3D: 2019AJ....157..219T,
   2024PSJ.....5..125T). Use the temperature profile nearest in time to each observation (2016ApJ...821L...8S).
10. **Isotopic ratios.** Fit each isotopologue line with the CO procedure, temperature fixed, terrestrial a
    priori ratios (2016ApJ...821L...8S); or retrieve isotopologue profiles and convert to the main species with
    fixed ratios (HCN from H13CN and HC15N with 12C/13C = 89.8, 14N/15N = 72.2, 2019Icar..319..417T). The pack
    does not say those isotopologue lines were checked to be optically thin; check the optical depth of the
    lines you use before relying on a thin-line conversion (general practice).
    - CH3D and CH4 (general practice): CH3D has four equivalent H positions, so CH3D/CH4 ~ 4 (D/H) and
      CH4 ~ CH3D / [4 (D/H)]. The reported numbers fit this: 5.54e-6 / (4 x 1.2e-4) = 1.15% in
      2024PSJ.....5..125T (my arithmetic). Using the Huygens CH4 profile only for the CH3D profile shape, as
      2019AJ....157..219T does, is a separate step from the abundance conversion.
    - Comet D/H: coma models in SUBLIME with lmfit are implied by the card's unstated
      items (2025NatAs...9.1476C); the card gives no settings, so this pipeline is unsupported here.
11. **Non-atmospheric continuum (rings).** Elliptical annuli of 500 km ring-plane width from 35000 to 64500 km,
    planet masked to mean radius + 3 beam FWHM, beam-convolved ring model, emcee MCMC fit of four ring-group
    fluxes (2019AJ....158...47M). Giant-planet maps: Radio-BEAR 2D model on 9455 disk points convolved with the
    beam, scaled so the disk average matches the nominal model (2019AJ....157..251T).

## Parameter defaults and ranges

Counts are mine, from the pack excerpts (12 on-topic papers). Longer list: `references/parameters.md`.

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| Clean algorithm | Hogbom | Hogbom, Clark | Hogbom 5, Clark 2 | 2016ApJ...821L...8S, 2024PSJ.....5..125T; Clark 2019AJ....158...76C, 2018ApJ...859L..15C |
| Weighting | natural | natural; Briggs for some datasets | natural 5 | 2018Icar..307..380T, 2019AJ....157..251T; Briggs unstated values 2019Icar..319..417T |
| Pixel size | 0.025'' | 0.01''-0.1'' | 6 | 0.01'' Band 9 2024PSJ.....5..125T; 0.1'' 2019AJ....157..219T |
| Clean threshold | 2x expected RMS | 2x RMS, 8-10 mJy, in-disk noise = sky noise | 5 | 2016ApJ...821L...8S, 2018Icar..307..380T, 2018ApJ...859L..15C |
| Model top of atmosphere | 1200 km | 782-1200 km | 6 | 782 km 2014ApJ...795L..30C; 850 km 2016ApJ...821L...8S |
| Field-of-view / emission-angle points (disk-averaged) | 24-44 | 10-44 | 5 | 37-44 2019Icar..319..417T, 2018Icar..307..380T; 24-27 2016ApJ...821L...8S; 24 2019AJ....157..219T; 10 2014ApJ...795L..30C |
| Emission angles (regional extractions) | 30 per extraction location | stated once | 1 | 2024PSJ.....5..125T |
| A priori correlation length | 1.5 scale heights | 1.5-3.0 (3.0 for HCN isotopologues) | 3 | 2018Icar..307..380T, 2024PSJ.....5..125T, 2019Icar..319..417T |
| A priori temperature error | 5 K | stated once | 1 | 2018Icar..307..380T |
| A priori abundance error | 100% | stated once | 1 | 2019Icar..319..417T |
| CO (Titan) | 49.6-50 ppm, constant with altitude | 40-60 ppm in a uniqueness test | fixed 3, a priori 1 | fixed: 2024PSJ.....5..125T, 2018Icar..307..380T, 2019AJ....157..219T; 50 ppm a priori, retrieved: 2016ApJ...821L...8S |
| Upper atmosphere temperature | isothermal 160 K above 600 km | stated once | 1 | 2018Icar..307..380T |
| Flux scale factor (Titan line retrievals) | rescale to model continuum | 0.85-1.15 per window (2024PSJ.....5..125T); 1.047 single factor (2019AJ....157..219T); ~10% off Horizons model (2016ApJ...821L...8S) | 3 | not used for rings (2019AJ....158...47M) |
| 12C/13C (Titan) | no single default: values play different roles | prior 89.3 and retrieved 89.9 +/- 3.4 (2016ApJ...821L...8S); fixed conversion ratio 89.8 (2019Icar..319..417T) | 2 | 2016ApJ...821L...8S, 2019Icar..319..417T |
| 14N/15N for HCN | 72.2 | stated once | 1 | 2019Icar..319..417T |
| D/H in CH4 (assumed) | 1.2e-4 | 1.0-1.4e-4 (2024PSJ.....5..125T); 1.13-1.59e-4 for a priori profiles (2019AJ....157..219T); combined envelope 1.0-1.59e-4 | 2 | 2024PSJ.....5..125T, 2019AJ....157..219T |
| Pressure broadening (HC3N) | Gamma 0.1 cm-1/bar, n 0.75 | HNC 1.290, n 0.69 | 2 | 2014ApJ...795L..30C, 2019Icar..319..417T |
| HC3N condensation level | ~71-80 km | | 2 | 2014ApJ...795L..30C, 2019Icar..319..417T |
| Comet continuum fit | 2nd-order polynomial in uvcontsub | stated once | 1 | 2025NatAs...9.1476C |

## Software

Counts of software mentions in matched steps are from the pack aggregates (all 13 papers); paper counts are
mine from the excerpts.

| Tool | Used for | Count |
|---|---|---|
| NEMESIS | line-by-line radiative transfer, optimal estimation (Levenberg-Marquardt), continuum scaling, CIRS limb fits | 14 step mentions; 7 papers (all Titan) |
| CASA | calibration scripts, self-cal, `tclean`, `uvcontsub`, `phaseshift`, `cvel2` | 11 step mentions |
| Radio-BEAR | giant-planet 2D brightness-temperature models | 1 (2019AJ....157..251T) |
| emcee, photutils, PyAstronomy | ring annulus photometry and MCMC flux fit | 1 each (2019AJ....158...47M) |
| GILDAS/MAPPING | uv analysis in the off-topic disk paper | 1 (ignore) |

2020ApJ...890...95I does not name its radiative-transfer code or line list (card). Fitting phrasings in the
aggregates are all one-offs: chi^2 minimisation with a priori regularisation, Levenberg-Marquardt, profile
scaling, emcee MCMC.

## Pitfalls

- **Flux scale.** Titan is a flux calibrator; its model can be off by ~10% (2016ApJ...821L...8S). In Titan
  line retrievals that rescale to the model continuum, report the factor for every window and dataset; 2 cards
  flag "scaling factor values per dataset" as not stated. Do not rescale by default: when the continuum is
  the signal (rings, planet brightness maps), a model-based rescaling can erase what you are measuring, so keep
  the calibrated flux, check it against earlier measurements (2019AJ....158...47M) and propagate its
  uncertainty. 2019AJ....157..251T normalizes Neptune's disk average to the nominal model as an explicit
  assumption, which makes its maps relative, not absolute.
- **Beam dilution.** Large beams average latitudes and damp latitudinal contrast (2018Icar..307..380T,
  2019Icar..319..417T, 2024PSJ.....5..125T). Short flux-calibrator integrations limit the significance of
  temporal change (2018Icar..307..380T).
- **Optical depth and altitude range.** HC3N is optically thick at the poles and sensitivity falls above
  ~400 km (2019Icar..319..417T). Report only the altitudes the lines constrain (50-550 km reported from a
  0-1200 km retrieval in 2019Icar..319..417T; 180-400 km reliable for CIRS limb profiles in
  2019AJ....158...76C).
- **Degeneracy.** One line per species cannot fix a vertical distribution (2014ApJ...795L..30C); low-S/N
  CH3D gives only a scale factor and the CH4 value inherits the assumed D/H (2024PSJ.....5..125T). Planet
  models are highly degenerate and omit latitudinal temperature changes (2019AJ....157..251T).
- **Error bars too small.** Retrieval errors only (2019AJ....157..219T); systematic errors from the
  disk-averaged temperature, Voigt profile and broadening coefficients not quantified (2016ApJ...821L...8S).
  2016ApJ...821L...8S adds a 2% line-intensity systematic.
- **Spatial representativeness.** Disk-averaged ALMA data are not directly comparable with the equatorial
  Huygens GCMS CH4 profile (2019AJ....157..219T), yet that profile sets its CH3D a priori shape and its D/H.
  Treat any D/H or CH4 comparison between a disk average and an in situ or local profile as carrying this
  extra, unquantified uncertainty.
- **Isotope priors.** A poorly known 12C/13C in HC3N lets the 14N/15N ratio drop to as low as 43
  (2018ApJ...859L..15C); data quality can leave scenarios indistinguishable (2020ApJ...890...95I).
- **Non-simultaneous lines.** HDO and H2O observed ~2 weeks apart, Q(H2O) from a CH3OH proxy
  (2025NatAs...9.1476C).
- **Coma source geometry.** Low HDO S/N leaves the parent scale length L_p unconstrained for the 50%
  distributed-source case (2025NatAs...9.1476C). Run the production-rate fit over the plausible L_p range
  and show how much the inferred ratio moves before quoting it.
- **Simplified retrievals and lifetimes.** 2019AJ....158...76C calls its ALMA limb retrievals only
  approximate (coarse resolution, simplified polygonal parameterization) and says its molecular lifetimes rest
  on gross assumptions. Its 180-400 km reliability range applies to the CIRS limb profiles, not to the ALMA
  retrievals.
- **Horizontal homogeneity.** The 2014ApJ...795L..30C gradient-model profiles assume no variation with
  latitude or longitude, while its maps show an offset HNC peak. A disk-integrated profile from such a model
  is an average; do not use it to explain mapped asymmetries.
- **Unmodelled physics.** Ring surface roughness not modelled, so beaming and thermal inertia are degenerate
  (2019AJ....158...47M); clouds ignored and LTE assumed for Neptune (2019AJ....157..251T).
- **Settings cards flag as not stated** (pack list, counted over all 13 pack papers): line-free channels (at least 5 cards), pipeline version
  (2), self-cal intervals (3), clean mask/iterations (4), NEMESIS a priori covariance (2), ephemeris for the
  Doppler correction (1), noise estimate in chi^2 (1). Write these down for your own run.

## Verification checks

What the papers did:
- Uniqueness: fix CO at 40-60 ppm and retrieve temperature only (2016ApJ...821L...8S); start from several a
  priori profiles and confirm convergence (2019AJ....157..219T, 2019Icar..319..417T).
- Temperature sensitivity: perturb temperature by 5 K; abundance moved < 20% (2019Icar..319..417T).
- Internal consistency: the same isotopologue from two transitions agrees (C18O 3-2 and 2-1,
  2016ApJ...821L...8S); neighbouring lines fit by earlier profiles (2024PSJ.....5..125T); inspect residual
  spectra (2024PSJ.....5..125T).
- Model resolution: confirm the number of annuli is sufficient (24 in 2019AJ....157..219T).
- Flux scale: compare the scale factor with earlier ALMA flux-calibration work (2019AJ....157..219T); compare
  the planet's total flux with earlier mm measurements (2019AJ....158...47M).
- External: compare with Cassini CIRS and radio occultation (2018Icar..307..380T) and with earlier VMR
  profiles (2014ApJ...795L..30C); fit ALMA and VLA disk averages with one nominal model (2019AJ....157..251T).
- Imaging artefacts: test weightings (2019AJ....157..251T); use a circularized beam for asymmetry claims
  (2019AJ....158...76C).

What a careful referee adds (my recommendation, not shown in the pack):
- Propagate the flux-scale uncertainty and the isotope/D/H prior range into the final error.
- Show averaging kernels or the altitude range each line constrains before quoting a profile.
- Forward-model the beam (simulate the observation) before claiming a latitudinal or temporal change.

## Source cards

Full list: `references/sources.md`. Most informative:

- 2018Icar..307..380T: full disk-averaged then regional NEMESIS temperature workflow, a priori settings.
- 2019Icar..319..417T: trace-gas retrievals, a priori errors, sensitivity tests.
- 2024PSJ.....5..125T: Band 9 self-cal with disk model, per-window flux scaling, CH3D to CH4.
- 2016ApJ...821L...8S: CO abundance and isotope ratios, uniqueness test.
- 2019AJ....157..219T: CH3D scaling retrieval, flux-scale factor, annulus test.
- 2014ApJ...795L..30C: gradient-model profiles, aperture spectra, broadening parameters.
- 2019AJ....158...76C: wedge profiles with circularized beam, CIRS comparison.
- 2018ApJ...859L..15C: HC3N isotopologue imaging and the 12C/13C caveat.
- 2020ApJ...890...95I: archival 14N/15N in CH3CN (thin methods).
- 2019AJ....157..251T: Neptune continuum maps with Radio-BEAR.
- 2019AJ....158...47M: Uranian ring photometry after planet subtraction.
- 2025NatAs...9.1476C: comet D/H, moving-target uv handling.
