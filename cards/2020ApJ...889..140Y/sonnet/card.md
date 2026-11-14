# High-resolution Near-infrared Polarimetry and Submillimeter Imaging of FS Tau A: Possible Streamers in Misaligned Circumbinary Disk System

`2020ApJ...889..140Y` | The Astrophysical Journal 2020 | first author: Yang, Yi | arXiv: 1912.11301 | DOI: 10.3847/1538-4357/ab64f9

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks, star_formation
- Question: What disk and streamer structures around the young binary FS Tau A are revealed by Subaru/HiCIAO H-band polarimetry and ALMA CO(2-1), and do they trace streamers in a misaligned circumbinary disk?  
  > "we suggest that these structures can mostly be explained by two streamers that connect the outer circumbinary disk and the central binary components." (abstract)
- Target **FS Tau A**: coordinates _not stated_; z/distance 140 pc  
  > "No Gaia distance is available for this target. Therefore, the typical distance for the Taurus star formation region [^2] is used in this work." (Introduction); "[^2]: 140 pc, (cite: Kenyon1994)" (Introduction); distance from typical Taurus distance (Kenyon1994)  
  > "No Gaia distance is available for this target. Therefore, the typical distance for the Taurus star formation region [^2] is used in this work." (Introduction); "[^2]: 140 pc, (cite: Kenyon1994)" (Introduction)

## Data provenance

- ALMA projects: 2013.1.00105.S
- bands: Band 6 (211-275 GHz)  
  > "The ALMA archival data at Band 6 (211-275 GHz) toward FS Tau A" (Observations and Data Reduction)
- frequencies and spectral setup: CO(2-1) at 230.538 GHz; bandwidth 23.92 MHz; spectral resolution 976.54 kHz (1264.70 m/s)  
  > "tuned at the rest frequency of 230.538 GHz for CO ($J$=2-1) emissions with the bandwidth of 23.92 MHz and the spectral resolution is 976.54 kHz" (Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 41.4 m to 2.3 km, 36 antennas  
  > "with 36 antennas whose baselines range from 41.4 m to 2.3 km" (Observations and Data Reduction)
- angular resolution: 0.16 x 0.22 arcsec  
  > "the obtained beam size is 0.$\ensuremath{''}16\times0.\ensuremath{''}$22" (Observations and Data Reduction)
- max recoverable scale: 3.88 arcsec  
  > "resulting in a maximum recoverable size of 3.$\ensuremath{''}$88" (Observations and Data Reduction)
- sensitivity: _not stated_
- time on source: 120.960 s after flagging  
  > "The integration time on source after data flagging is 120.960 s" (Observations and Data Reduction)
- observing dates: Sep. 19, 2015  
  > "It was observed on Sep. 19, 2015 with 36 antennas" (Observations and Data Reduction)
- pi or archival as stated: archival  
  > "The ALMA archival data at Band 6" (Observations and Data Reduction)
- Line: CO J=2-1 (230.538 GHz)
- Other facility **Subaru/HiCIAO + AO188**: H-band polarized differential imaging (SEEDS) of FS Tau A, Dec 26 2011  
  > "The H-band near-infrared observations of FS Tau A were taken on Dec. 26, 2011, using the HiCIAO near-infrared camera" (Observations and Data Reduction)
- External data: Earlier binary astrometry 1996-2001 used in orbit fit  
  > "Our data, as well as the data taken from the year 1996 to 2001 in (cite: Tamazian2002) are used for fitting." (Results) [from (cite: Tamazian2002)]
- External data: Total 1.3 mm flux 2.72 mJy used for disk mass  
  > "the total millimeter flux of the system (2.72 mJy at 1.3 mm) indicates a low disk mass, $M_{disk}/M_{star}\sim0.5$ (cite: Akeson2019)" (Discussion) [from (cite: Akeson2019)]
- External data: Barycentric radial velocities 16.23 and 16.24 km/s of nearby stars  
  > "have barycentric radial velocities of 16.23 and 16.24 km/s, respectively (cite: Nguyen2012)" (Results) [from (cite: Nguyen2012)]

## Processing

### Calibration

- pipeline or manual: CASA pipeline  
  > "The calibration was done by the pipeline in the Common Astronomy Software Applications (CASA) package 4.3.1" (Observations and Data Reduction)
- casa version: 4.3.1  
  > "The calibration was done by the pipeline in the Common Astronomy Software Applications (CASA) package 4.3.1" (Observations and Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0510+180 (flux); J0510+1800 bandpass; J0426+2327 phase  
  > "J0510+1800 is used for bandpass calibration, J0510+180 is used for flux calibration and J0426+2327 is used for phase calibration." (Observations and Data Reduction)
- flux scale uncertainty: _not stated_
- self calibration: not applied; continuum too weak  
  > "the continuum image of FS Tau A is not strong enough to make self-calibration safely so we do not apply it in CO ($J$=2-1) line imaging." (Observations and Data Reduction)

### Imaging

- task: CLEAN task in CASA  
  > "imaging was done by CLEAN task provided in CASA" (Observations and Data Reduction)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.16 x 0.22 arcsec, PA 26.24 deg  
  > "(beam size: 0.$\ensuremath{''}16\times0.\ensuremath{''}$22; PA: 26.24$^\circ$)" (Sub-millimeter Observations)
- final rms: _not stated_

### Inherited from earlier work

- Instrumental polarization correction method  
  > "The instrumental polarization was corrected based on the method described by (cite: Joos2008)." (Observations and Data Reduction) [from (cite: Joos2008)]
- Radial Stokes Q_phi/U_phi computation  
  > "using the methods suggested by (cite: Avenhaus2014)" (Circumstellar Structures) [from (cite: Avenhaus2014)]
- PSF halo subtraction method  
  > "using the method similar to (cite: Oh2016)" (Circumstellar Structures) [from (cite: Oh2016)]

### Not stated but needed to reproduce (our reading)

- CLEAN parameters: weighting/robust, cell size, image size, mask, threshold, niter
- Continuum subtraction and line-free channels
- Moment-map clipping thresholds and channel ranges' rms
- Which imaging produced channel velocities (LSRK frame, restfreq setup)
- Central mass used for the Keplerian curve in the PV map and disk inclination/PA
- Orbitize settings (walkers, burn-in, convergence)
- Pipeline-delivered vs reprocessed MS
- Bandwidth of 23.92 MHz appears inconsistent with the channel count and spectral window

## Analysis recipe

1. **Fit binary position**: Fit radial profile along PA 110 deg with a two-Gaussian (core+halo) PSF for Aa and Ab using SciPy curve_fit  
  > "The fitting is performed by the SciPy *curve_fit* command, which employs the Levenberg-Marquardt method." (Results)
   - software: SciPy, IRAF
   - assumption: Ab has same s, sigma_h, sigma_c as Aa  
  > "we assume that its PSF has the same $s$, $\sigma_h$, and $\sigma_c$ as those of Aa" (Results)
   - fitting: Levenberg-Marquardt, initial guesses all 1  
  > "The initial guesses of all parameters are 1." (Results)
   - validation: Relative residuals <0.1 within ~90 pixels  
  > "are smaller than 0.1 within a radius of $\sim$90 pixels" (Results)
2. **Fit binary orbit**: MCMC orbit fit with orbitize! using new and 1996-2001 astrometry  
  > "The MCMC algorithm of the code *orbitize!* (cite: Blunt2019) is used to fit the orbit." (Results)
   - software: orbitize!
   - parameter: parallax 7.143±0.001 mas; system mass prior 1.5±0.25 Msun  
  > "we set the initial mass at 1.5$\pm$0.25 $M_\odot$" (Results)
   - fitting: Gaussian priors on parallax and mass; log-uniform a; sine i; uniform others  
  > "The semi-major axis $a$ uses Log Uniform prior $p(x)\propto1/x$, the inclination $i$ uses Sine prior $p(x)\propto sin(x)$" (Results)
   - validation: Best-fit chi2 about 1.88; fits 2001 and 2011 data  
  > "this result fits the observation results of 2001 and 2011 quite well" (Results)
3. **Map NIR circumstellar structures**: Q_phi and U_phi images; test PSF halo subtraction; S1/S2 significance from U_phi noise  
  > "noise level was estimated from the standard deviation of the $U_\phi$ image at the same place" (Results)
   - software: IRAF
   - fitting: _not stated_
   - validation: _not stated_
4. **Moment maps of CO channels**: Integrate blue (channels 1-8) and red (12-25) components into moment 0/1/2 maps; assume systemic heliocentric velocity 16.3 km/s (LSRK 6.90)  
  > "it is reasonable to assume that the heliocentric radial velocity of FS Tau A is 16.3 km/s, corresponding to an LSRK velocity 6.90 km/s." (Results)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
5. **Test for misaligned inner disk and GI**: P-V map of structure A along PA 9.9 deg compared to Keplerian curve; disk mass from 1.3 mm flux  
  > "The P-V map is drawn along a PA of 9.9$^\circ$, a radius of 0.$\ensuremath{''}$5 (70 AU), and a 1-pixel width from the primary star Aa" (Discussion)
   - assumption: dust opacity 2.3 cm2/g at 1.3 mm, dust T 20 K, gas-to-dust 100:1  
  > "assuming a dust opacity of $\tau_{1.3mm} = 2.3 cm^2/g$ (cite: Beckwith1990), an average dust temperature of 20 K, and a gas-to-dust mass ratio of 100:1" (Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.3.1: ALMA pipeline calibration and CLEAN imaging  
  > "The calibration was done by the pipeline in the Common Astronomy Software Applications (CASA) package 4.3.1" (Observations and Data Reduction)
- **IRAF** : geomap/geotran distortion correction, center command  
  > "via the Image Reduction and Analysis Facility (IRAF) *geomap* and *geotran* commands" (Observations and Data Reduction)
- **SciPy curve_fit** : PSF profile fitting  
  > "The fitting is performed by the SciPy *curve_fit* command" (Results)
- **orbitize!** : MCMC binary orbit fit  
  > "The MCMC algorithm of the code *orbitize!* (cite: Blunt2019) is used to fit the orbit." (Results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Binary separation (NIR) | 0.271 | 0.0095 | arcsec | 1 | 0.271 |
| Binary PA | 110 | 2.5 | deg | 1 | the PA of the companion star is about 110$^\circ\pm2.5^\circ$ |
| Orbit semi-major axis (median) | 34.3 | +12.6/-6.3 | AU | 2 | 34.3 |
| Orbit inclination (median) | 44.3 | +11.2/-12.1 | deg | 2 | 44.3 |
| System mass (median) | 1.54 | +0.20/-0.18 | Msun | 2 | 1.54 |
| Disk-to-star mass ratio | ~0.5 | not stated | dimensionless | 5 | indicates a low disk mass, $M_{disk}/M_{star}\sim0.5$ |

## Qualitative findings

- Blue-shifted (LSRK 1.19-5.64 km/s) CO structures match NIR arm S1; red-shifted (8.17-16.43 km/s) arm matches S2  
  > "corresponding to two bar-like structures detected in ALMA observations with an LSRK velocity of 1.19-5.64 km/s." (abstract)

## Claim tuples

- H: The NIR and CO structures are streamers connecting the circumbinary disk and the binary | E: Compare HiCIAO Q_phi and ALMA CO moment maps with simulated streamers | R: S1/S2 correspond to blue/red CO structures; shapes resemble simulations | F: Two streamers, best explained as material flowing away from the stars | **partially**
- H: Structure A is a misaligned inner circumbinary disk | E: P-V map vs Keplerian curve; gap size vs misalignment | R: Velocities not Keplerian; gap would exceed 56 AU | F: Such a disk does not exist | **refuted**
- H: Gravitational instability produced the structures | E: Disk mass from 1.3 mm flux and accretion rate | R: Low accretion rate and low disk mass | F: GI unlikely | **refuted**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Misaligned inner disk and gravitational instability rejected; PSF halo as cause of butterfly pattern disfavored  
  > "we suggest that uncorrected PSF halo may not be the mechanism causing this butterfly pattern" (Circumstellar Structures)
- How they decided it was enough: _not stated_
- Limitation (authors): Radial velocity of FS Tau A not calibrated; assumed from neighbours  
  > "No calibration of FS Tau A’s radial velocity was made." (Sub-millimeter Observations)
- Caveat (inferred, ours): Very short on-source time and narrow band give low S/N; 2-5 sigma features
- Caveat (inferred, ours): Systemic velocity assumed from stars 44 arcmin away
- Caveat (inferred, ours): Streamer interpretation is qualitative, no modelling
- Caveat (inferred, ours): Distance assumed, orbit poorly constrained

## Reproducibility

- Data public (paper): archival ALMA data  
  > "The ALMA archival data at Band 6 (211-275 GHz) toward FS Tau A (Project ID 2013.1.00105.S)" (Observations and Data Reduction)
- Products in archive: _not stated_
- Missing: CLEAN parameters and masks
- Missing: HiCIAO data availability
- Missing: Moment-map clipping
- Data volume (inferred): ~5-20 GB
- Score (inferred): 3/5, ALMA project is given and archive pipeline is used, but imaging settings are missing and results are mostly qualitative.
- Rediscovery candidate: no, Imaging recipe incomplete and main results are morphological.

## Links

- Method: (cite: Blunt2019) (orbitize! orbit fitting)
- Method: (cite: Avenhaus2014) (Q_phi method)
- Companion: (cite: Hioki2011) (earlier NIR imaging of the FS Tau A disk)
- Related: SEEDS

## Checks

```json
{
 "quotes": 58,
 "quotes_ok": 58,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 44,
  "rate": 0.587
 },
 "evidence_ok": true
}
```
