# Differences in the Gas and Dust Distribution in the Transitional Disk of a Sun-like Young Star, PDS 70

`2018ApJ...858..112L` | The Astrophysical Journal 2018 | first author: Long, Zachary C. | arXiv: 1804.00529 | DOI: 10.3847/1538-4357/aaba7c

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: What are the structures of the gas and dust in the PDS 70 transitional disk, and do the gas features have dust counterparts?  
  > "This is of particular interest to our study due to the existence of features which appear in the gas disk but are not present in the dust disk." (Introduction)
- Target **PDS 70**: coordinates _not stated_; z/distance 140 pc  
  > "PDS 70 is a pre-main-sequence star with spectral type K5 and assumed to be part of the Centaurus association, estimated to be at a distance of 140 pc (cite: riaud06)." (Introduction); distance from Riaud et al. 2006 (Centaurus association)  
  > "PDS 70 is a pre-main-sequence star with spectral type K5 and assumed to be part of the Centaurus association, estimated to be at a distance of 140 pc (cite: riaud06)." (Introduction)

## Data provenance

- ALMA projects: 2015.1.000888.S
- bands: _not stated_
- frequencies and spectral setup: CO 3-2 at 345.761 GHz, HCO+ 4-3 at 356.698 GHz, continuum at 343.955 and 355.497 GHz; line bandwidth 468.75 MHz, 244.141 kHz resolution (~0.21 km/s)  
  > "The correlator was tuned at the center frequency of 345.761 GHz for CO J=3–-2, 356.698 GHz for HCO^+^ J=4–-3, and 343.955 GHz and 355.497 GHz for continuum observations" (2 Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15.1 m to 1.5 km, 38-39 12 m antennas  
  > "The array configuration provides a maximum and minimum baseline length of 1.5 km and 15.1 m, respectively." (2 Observations and Data Reduction)
- angular resolution: 0.19"x0.15" (continuum, CO); 0.18"x0.15" (HCO+)  
  > "the final synthesized beam of approximately $0.19\ensuremath{''}\times0.15\ensuremath{''}$ for the continuum image and CO J=3–2 map" (2 Observations and Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: rms 0.0551 mJy/beam continuum, 1.204 mJy/beam CO, 1.118 mJy/beam HCO+  
  > "The achieved rms was 0.0551 mJy beam$^{-1}$ for the continuum, 1.204 mJy beam$^{-1}$ for CO J=3–2, and 1.118 mJy beam$^{-1}$ for HCO^+^ J=4–3." (2 Observations and Data Reduction)
- time on source: about 56 minutes after flagging  
  > "The total integration time on source after flagging is about 56 minutes." (2 Observations and Data Reduction)
- observing dates: August 14 and 18, 2016 (Cycle 3)  
  > "Observations were conducted on August 14 and 18, 2016 in the ALMA cycle 3 program" (2 Observations and Data Reduction)
- pi or archival as stated: _not stated_
- Line: CO J=3-2 (345.761 GHz (tuned center))
- Line: HCO+ J=4-3 (356.698 GHz (tuned center))
- Other facility **IRTF SpeX**: Near-IR spectrum for gas accretion and stellar classification  
  > "PDS 70 was observed on 13 Jan. 2017 UT using the SpeX spectrograph (cite: rayner03) on NASA’s Infrared Telescope Facility (IRTF)." (Appendix A)
- Other facility **REM**: Optical/NIR photometry for SED  
  > "We also observed PDS 70 on 10 June 2016 UT using the Rapid Eye Mount (REM) telescope in the g$'$r$'$i$'$z$'$JH filters." (Appendix A)
- Other facility **Spitzer IRS**: Spectrum constraining silicate bands in the model  
  > "we also include data obtained with the $Spitzer$ InfraRed Spectrograph (IRS) in our analysis" (3.2.2 Model Fitting)
- External data: H-band polarized imagery of PDS 70 used to compare with model  
  > "we compared model images to both the 0.87 mm continuum data (Figure [10](#fig:model_87)) and the $H$-band data (cite: hashimoto12)" (3.2.3 Final Model) [from (cite: hashimoto12)]
- External data: Stellar radius 1.39 Rsun and temperature 4400 K  
  > "a radius of 1.39 R$\astrosun$, and a temperature of 4400 K as suggested by (cite: gregorio02)" (3.2.1 Initial Model) [from (cite: gregorio02)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.7  
  > "Data reduction was performed using version 4.7 of the Common Astronomy Software Applications package (CASA)." (2 Observations and Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1427-4206 (bandpass, flux, phase); J1407-4302 second calibrator  
  > "A quasar J1427-4206 was used for bandpass, flux, and phase calibrations, and another quasar J1407-4302 was selected as a second calibrator." (2 Observations and Data Reduction)
- flux scale uncertainty: _not stated_
- self calibration: Continuum self-calibration repeated until rms minimum; gain table applied to CO and HCO+  
  > "gain calibration was repeated until the rms reached minimum." (2 Observations and Data Reduction)

### Imaging

- task: CLEAN in CASA  
  > "We used the task CLEAN in CASA and a continuum image was generated by combining the line-free channels in all of the spectral windows." (2 Observations and Data Reduction)
- deconvolver: _not stated_
- weighting robust: Natural weighting  
  > "Natural weighting was applied in both continuum and line imaging for better sensitivity." (2 Observations and Data Reduction)
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
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Model started from earlier PDS 70 models and same grain types as Hashimoto et al.  
  > "We used a model similar to those of (cite: hashimoto15) and (cite: dong12) as our starting point." (3.2.1 Initial Model) [from (cite: hashimoto15); (cite: dong12)]
- Surface density from Whitney et al. 2013 eq. 15  
  > "via the method described in (cite: whitney13) eq. 15" (3.2.2 Model Fitting) [from (cite: whitney13)]

### Not stated but needed to reproduce (our reading)

- Clean threshold, masks, number of iterations, cell and image size
- Line-free channels and continuum subtraction method
- Self-calibration solution intervals and number of rounds
- Primary beam correction and moment-map clipping thresholds
- HOCHUNK3D fitting procedure, parameter grid and goodness-of-fit metric
- Ellipse-fitting and dynamical mass fitting details (Keplerian model, systemic velocity)

## Analysis recipe

1. **Measure continuum geometry and flux**: Ellipse fitting of brightest ring emission; edges at half beam width from detectable disk edges; flux integrated within 1.00"  
  > "measured via ellipse fitting of the brightest emission along the ring of the disk" (3.1 Continuum)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Check reality of HCO+ bridge**: Simulated observation of a toy gas model with bridge and azimuthal gap  
  > "This was produced using the CASA 5.2 task simobserve with the thermal noise set to default and the antennas set to the ALMA cycle 4 configuration, alma.cycle4.3.cfg." (3.2 HCO+)
   - software: CASA simobserve, HOCHUNK3D
   - fitting: _not stated_
   - validation: Bridge SNR ~5; simulation reproduces asymmetric features only with dimmer region and bridge  
  > "The bridge structure is likely to be real, with a signal-to-noise ratio of $\sim$ 5." (3.2 HCO+)
3. **MCRT model of dust disk and SED**: HOCHUNK3D two-component disk fit to SED, ALMA 0.87 mm image and H-band image  
  > "we included a less dense, though still optically thick, inner disk disk comprised of only small grains which extends from the sublimation radius to 15 au." (3.2.2 Model Fitting)
   - software: HOCHUNK3D
   - parameter: flaring b=1.15±0.02; density exponent a=2.25±0.02 (large), 1.5±0.02 (small)  
  > "we find b = 1.15 $\pm$ 0.02 and a = 2.25 $\pm$ 0.02 for the large grains in our disk" (3.2.2 Model Fitting)
   - assumption: Stellar mass 0.82 Msun, distance 140 pc, K5 star with 4400 K  
  > "Stellar Distance | 140 pc" (Table 1)
   - fitting: Manual adjustment; no sampler or likelihood stated  
  > "To fit the model with these new constraints we included a less dense, though still optically thick, inner disk disk comprised of only small grains which extends from the sublimation radius to 15 au." (Model Fitting)
   - validation: Model images convolved with beam/PSF compared with ALMA and H-band data; Finner/Fouter ~0.004 in both  
  > "$\frac{Finner}{Fouter}$ $\sim0.004$ in both cases" (3.2.3 Final Model)
4. **Dynamical stellar mass**: Compare CO moment 1 with Keplerian model at inclination 45 deg  
  > "we used the CO J=3–2 moment 1 data to find the dynamical mass of PDS 70." (3.2.2 Model Fitting)
   - assumption: Inclination 45 deg  
  > "Here we assumed a disk inclination of 45$\ensuremath{^\circ}$, based on our modeling" (3.2.2 Model Fitting)
   - fitting: _not stated_
   - validation: Consistent with Riaud et al. 2006 mass  
  > "is in agreement with the (cite: riaud06) estimation" (3.2.2 Model Fitting)

## Software

- **CASA** 4.7 (5.2 for simobserve): Calibration, self-calibration, imaging, simulated observations  
  > "Data reduction was performed using version 4.7 of the Common Astronomy Software Applications package (CASA)." (2 Observations and Data Reduction)
- **HOCHUNK3D** : Monte Carlo radiative transfer dust disk model  
  > "We modeled the dust disk using the Monte Carlo radiative transfer code HOCHUNK3D (cite: whitney13) using a two disk components." (abstract)
- **Spextool** : SpeX data reduction  
  > "Data reduction was done using the Spextool package (cite: cushing04) running under IDL." (Appendix A)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Dust ring inner edge radius | 0.42 | 0.05 | arcsec (~60 au) | 1 | measures a radial distance of $0.42\ensuremath{''} \pm 0.05\ensuremath{''}$ ($\sim$60 au) from the center at the edge |
| Dust ring outer edge radius | 0.79 | 0.05 | arcsec (~110 au) | 1 | $0.79\ensuremath{''} \pm 0.05\ensuremath{''}$ ($\sim$110 au) at the outer edge |
| 0.87 mm flux density within 1" | 233 | 3 | mJy | 1 | The measured flux density is 233 $\pm$ 3 mJy integrated at a radius of $1.00\ensuremath{''}$ |
| Dynamical stellar mass | 0.6-0.8 | not stated | Msun | 4 | a mass of 0.6 - 0.8 M$\astrosun$ (Figure [8](#fig:dynamical_mass)) produces a good fit to the data |
| Model disk inclination | 45 | not stated | deg | 3 | best reproduced with a model inclination of 45$\ensuremath{^\circ}$ from face on |
| Model gap | 15-60 | not stated | au | 3 | Gap / 15-60 au |

## Qualitative findings

- HCO+ shows an azimuthal gap and a bridge with no dust counterpart; inner disk is gas-poor.  
  > "The sub-au region of the disk is gas poor despite evidence for a dusty inner disk component." (Conclusion)

## Claim tuples

- H: Do small and large grains have different gap radii in PDS 70? | E: Compared ALMA 0.87 mm continuum with H-band imagery and MCRT model | R: Similar radial extent, gap to ~60 au | F: No grain-size segregation in the outer disk; earlier difference due to SMA resolution | **supported**
- H: Are there gas structures without dust analogues? | E: HCO+ and CO moment maps compared to continuum | R: Azimuthal gap and bridge in gas only | F: Cause unresolved; several options proposed | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Mass transfer and polar outflow rejected for the bridge since no velocity change is seen  
  > "there appears to be no significant change in velocity in the region of the bridge" (3.2 HCO+)
- How they decided it was enough: _not stated_
- Limitation (authors): Cause of gas features cannot be determined with existing data  
  > "Although we cannot determine a definitive cause for these features with existing data" (Conclusion)
- Caveat (inferred, ours): Model fit is qualitative with no formal fitting or uncertainties on most parameters
- Caveat (inferred, ours): Bridge SNR ~5 only; reality tested with a hand-edited toy model
- Caveat (inferred, ours): Inconsistent disk mass between text (~7.3 MJ) and Table 1 (0.42 MJ)

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters and masks
- Missing: HOCHUNK3D input files and fit procedure
- Missing: Seed image for simobserve test
- Data volume (inferred): ~50-100 GB
- Score (inferred): 3/5, Public Cycle 3 data and standard CASA, but imaging and modeling details are sparse.
- Rediscovery candidate: no, Modeling is manual and imaging recipe incomplete.

## Links

- Method: (cite: whitney13) (HOCHUNK3D code)
- Companion: (cite: hashimoto15) (Earlier SMA 1.3 mm and model of PDS 70)

## Checks

```json
{
 "quotes": 50,
 "quotes_ok": 50,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2015.1.000888.S"
 ],
 "obscore_codes_not_in_card": [
  "2015.1.00888.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 38,
  "rate": 0.535
 },
 "evidence_ok": true
}
```
