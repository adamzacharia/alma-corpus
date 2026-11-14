# Parameters seen in the pack (solar-system-atmospheres)

Every row is from the evidence pack (`skills/packs/solar-system-atmospheres.md`). One value per paper; "stated
once" rows are single-paper evidence, not a convention.

## Imaging

| Paper | Clean | Weighting | Pixel | Threshold / stop | Other |
|---|---|---|---|---|---|
| 2016ApJ...821L...8S | Hogbom | natural | not stated | 2x expected RMS | phase self-cal, revised JAO scripts |
| 2024PSJ.....5..125T | Hogbom | natural | 0.01'' | not stated | phase self-cal with flat or limb-darkened disk model (Band 9) |
| 2014ApJ...795L..30C | Hogbom | not stated | not stated | not stated | CASA 4.2.0; continuum subtraction by "standard routines", domain not stated |
| 2019AJ....157..219T | Hogbom | not stated | 0.1'' | 10 mJy | archive scripts re-run with updated Titan flux model |
| 2018Icar..307..380T | Hogbom | natural | 0.03'' | 2x RMS | modified JAO scripts |
| 2019AJ....157..251T | tclean MFS | natural | 0.02'', 512x512 | 1000-2000 iterations, in-disk noise = sky noise | circular mask; limb-darkened model subtracted |
| 2019AJ....158...76C | Clark | not stated | 0.025'' | not stated | mask 1.3''; two days regridded and combined |
| 2018ApJ...859L..15C | Clark | natural | 0.025'' | 8 mJy | 976 kHz channels in Titan frame |
| 2019AJ....158...47M | tclean | not stated | not stated | not stated | uv-plane Uranus disk subtraction |
| 2025NatAs...9.1476C | not stated | not stated | not stated | not stated | phaseshift, uvcontsub 2nd order, cvel2 |

## Spectrum extraction and radiance conversion

| Paper | Extraction | Model geometry |
|---|---|---|
| 2016ApJ...821L...8S | disk + atmosphere to 850 km + 3 sigma_PSF | 24-27 FOV points out to 3425 km radius |
| 2018Icar..307..380T | 2575 km disk + 1200 km atmosphere + 2 sigma_PSF; North/Center/South | 37-44 FOV points |
| 2019Icar..319..417T | disk-average and three non-overlapping beam footprints | 37-44 FOV points, retrieval 0-1200 km, reported 50-550 km |
| 2019AJ....157..219T | "mask of pixels containing at least 90% of Titan's continuum flux" (from an earlier paper; per-pixel vs cumulative definition not stated, card) | 24 emission angles to 1200 km; distance 9.038 AU, sub-observer latitude 24.55 deg, Doppler -7.5 km/s |
| 2024PSJ.....5..125T | latitude bins, East/West hemispheres (regional, not disk-averaged) | 30 emission angles per extraction location; Doppler offsets ~1e-5 cm-1 |
| 2014ApJ...795L..30C | circular aperture 1.5 arcsec (12,000 km) in diameter, centered on Titan | 10-point trapezium rule to 782 km |
| 2019AJ....158...76C | radial wedges 10 deg (30 deg for C2H3CN, C3H8), circularized beam | CIRS limb fits with cubic b-spline knots every 100 km |

## Retrieval settings and assumptions

| Paper | Setting |
|---|---|
| 2016ApJ...821L...8S | a priori CO 50 ppm, constant to 850 km, retrieved together with temperature; terrestrial a priori 12C/13C 89.3, 16O/18O 498.8, 16O/17O 2680.6 (retrieved 12C/13C 89.9 +/- 3.4 is a result, not a setting); 2% line-intensity systematic |
| 2018Icar..307..380T | a priori temperature error 5 K; correlation length 1.5 scale heights; CO 49.6 ppm fixed; isothermal 160 K above 600 km; tropospheric a priori from Cassini radio/HASI convolved with the beam |
| 2019Icar..319..417T | a priori abundance error 100%; correlation length 1.5 (3.0 for HCN isotopologues); 12C/13C 89.8, 14N/15N 72.2; condensation below ~80 km; Gamma 0.1 cm-1/bar, n 0.75 for HC3N and C3H4 |
| 2024PSJ.....5..125T | Levenberg-Marquardt; correlation length 1.5; profiles free up to 1200 km; CO ~50 ppm; troposphere fixed to Cassini RS; D/H 1.2e-4 (1.0-1.4e-4); a priori CH4 1.48%; flux scales 0.85-1.15 per spectral window; CH4 = CH3D / (4 D/H) reproduces its 1.15% (my arithmetic) |
| 2019AJ....157..219T | CO 50 ppm; temperature adopted (ALMA stratosphere plus HASI/radio occultation troposphere), not retrieved; a priori CH3D profiles built from the Huygens GCMS CH4 profile and D/H 1.13-1.59e-4 (pack shorthand "CH4 times D/H"; for an abundance conversion use CH3D/CH4 ~ 4 D/H, general practice); data scaled by 1.047 |
| 2014ApJ...795L..30C | profiles assumed not to vary with latitude or longitude; gradient model at z_r = 293 km; HNC step model above 400 km; HC3N condenses below ~71 km; Lorentz half-widths 1.290 (HNC), 0.1 (HC3N) cm-1/bar, exponents 0.69, 0.75 |
| 2019AJ....157..251T | Radio-BEAR nominal model: dry adiabat, 71.5 K at 1 bar, trace gases 30x protosolar (NH3 1x), intermediate H2; 9455 disk points |
| 2019AJ....158...47M | annuli 500 km wide, 35000-64500 km; planet mask mean radius + 3 beam FWHM; ring weights from visible equivalent widths; emcee |
