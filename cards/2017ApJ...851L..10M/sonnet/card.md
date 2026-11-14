# The First Detection of a Pulsar with ALMA

`2017ApJ...851L..10M` | The Astrophysical Journal Letters 2017 | first author: Mignani, R. P. | arXiv: 1708.02828 | DOI: 10.3847/2041-8213/aa9c3e

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: stellar_physics
- Question: At what wavelengths does pulsar emission transition from coherent to incoherent; what is the Vela pulsar's mm/sub-mm spectrum?  
  > "it has not been established yet at which wavelengths the transition occurs, a key information for all emission models of pulsar magnetospheres." (abstract)
- Target **Vela pulsar (PSR B0833-45)**: coordinates 08h35m20.61s, -45d10m34.87s (J2000, radio position)  
  > "$\alpha=08^{\rm h}  35^{\rm m} 20.61^{\rm s}$; $\delta  = -45^\circ 10\ensuremath{''} 34.87\ensuremath{''}$ (epoch 2000.0)" (3 Observations and Data Reduction); "At the distance of the Vela pulsar of $287^{+19}_{-17}$ pc (Dodson et al. 2003)" (4 Discussion); z/distance 287 (+19/-17) pc  
  > "$\alpha=08^{\rm h}  35^{\rm m} 20.61^{\rm s}$; $\delta  = -45^\circ 10\ensuremath{''} 34.87\ensuremath{''}$ (epoch 2000.0)" (3 Observations and Data Reduction); "At the distance of the Vela pulsar of $287^{+19}_{-17}$ pc (Dodson et al. 2003)" (4 Discussion); distance from Dodson et al. 2003  
  > "$\alpha=08^{\rm h}  35^{\rm m} 20.61^{\rm s}$; $\delta  = -45^\circ 10\ensuremath{''} 34.87\ensuremath{''}$ (epoch 2000.0)" (3 Observations and Data Reduction); "At the distance of the Vela pulsar of $287^{+19}_{-17}$ pc (Dodson et al. 2003)" (4 Discussion)

## Data provenance

- ALMA projects: 2015.1.01104.S
- bands: Band 3 (97.5 GHz), 4 (145 GHz), 6 (233 GHz), 7 (343.5 GHz)  
  > "Band 3 (97.5 GHz), Band 4 (145 GHz), Band 6 (233 GHz), and Band 7 (343.5 GHz)" (Observations and Data Reduction)
- frequencies and spectral setup: dual polarisation, 7.5 GHz band, four 1.875 GHz spectral windows, 128 channels each  
  > "dual polarisation in a 7.5 GHz wide band, divided in four spectral windows (1.875 GHz each), with 128 channels" (Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: 12-m array, average 38 antennas  
  > "executed with the 12-m array, with an average of 38 antennas" (Observations and Data Reduction)
- configurations: _not stated_
- baselines: max baselines 495 m (Band 7) to 867 m (Band 3)  
  > "maximum baselines ranging from 495 m (Band 7) to 867 m (Band 3)" (Observations and Data Reduction)
- angular resolution: ~0.6 to 0.8 arcsec  
  > "allowing a spatial resolution ranging from $\sim 0.6\ensuremath{''}$ to $0.8\ensuremath{''}$" (Observations and Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: ~20 uJy/beam (1 sigma) per band  
  > "provided a $1 \sigma$ sensitivity of $\sim$ 20 $\mu$Jy/beam in each of the selected bands" (Observations and Data Reduction)
- time on source: ~3.3 hours total  
  > "The total time spent on the target was $\sim$ 3.3 hours" (Observations and Data Reduction)
- observing dates: Cycle 3, March to July 2016  
  > "during Cycle 3, from March to July 2016" (Observations and Data Reduction)
- pi or archival as stated: _not stated_
- Other facility **VLT/NACO**: archival unpublished Ks-band AO images confirming the extended structure  
  > "we used archival, unpublished, K$_{\rm s}$-band high spatial resolution images of the Vela pulsar field" (The Nebula)
- Other facility **HST/ACS**: F606W comparison image  
  > "the 606W filter ($\lambda=0.59 \mu$m; $\Delta \lambda=0.25\mu$m)" (The Nebula)
- Other facility **Chandra HRC-I**: X-ray comparison image (Obs. ID 1966)  
  > "High Resolution Camera in imaging mode (HRC-I; Obs. ID 1966)" (The Nebula)
- External data: Pulsar radio position and proper motion  
  > "using its radio coordinates as a reference (Dodson et al. 2003)" (Observations and Data Reduction) [from Dodson et al. 2003 (cite: dodson03)]
- External data: Radio flux densities 400 MHz-24 GHz  
  > "eight flux density values in the frequency range between 400 MHz and 24 GHz (Manchester et al. 2005; Johnston et al. 2006; Keith et al. 2011)" (The pulsar) [from Manchester et al. 2005; Johnston et al. 2006; Keith et al. 2011]
- External data: UV-optical-NIR PL spectrum and Ks flux  
  > "flat UV-optical-near-IR PL spectrum (Zyuzin et al. 2013)" (The pulsar) [from Zyuzin et al. 2013 (cite: zyuzin13)]
- External data: Mid-IR Spitzer flux densities  
  > "extrapolation of the mid-IR flux densities (Danilenko et al. 2011)" (The pulsar) [from Danilenko et al. 2011 (cite: danilenko11)]

## Processing

### Calibration

- pipeline or manual: CASA and ALMA pipeline  
  > "Raw data were calibrated using the Common Astronomy Software Applications (CASA) software package (version 4.5.3) and the ALMA pipeline (Pipeline-Cycle3-R4-B)." (Observations and Data Reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1107-4449 (Bands 4,6,7); Callisto with Butler-JPL-Horizons 2012 (Band 3)  
  > "we used flux measurements of the quasar J1107$-$4449." (Observations and Data Reduction); "we fixed the flux density scale using data from Callisto observations, and using the Butler-JPL-Horizons 2012 standard model" (Observations and Data Reduction)
- flux scale uncertainty: 10%  
  > "We, conservatively, assume the uncertainty on the flux density to be 10%." (Observations and Data Reduction)
- self calibration: _not stated_

### Imaging

- task: CASA clean  
  > "We produced images from the calibrated data using the task `clean` in CASA." (Observations and Data Reduction)
- deconvolver: _not stated_
- weighting robust: natural  
  > "The images were generated using "natural” weighting, in order to maximise the sensitivity." (Observations and Data Reduction)
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
- final beam: 0.75x0.68, 0.77x0.74, 0.88x0.73, 0.66x0.49 arcsec (Bands 3,4,6,7)  
  > "| 7 | 343.5 | March 10,26,28 | 120 | 0.66 $\times$ 0.49 | 18 | 67$\pm$19 |" (Table 1)
- final rms: 25, 20, 18, 18 uJy/beam (Bands 3,4,6,7)  
  > "| 3 | 97.5 | July 23 | 22 | 0.75 $\times$ 0.68 | 25 | 252$\pm$35 |" (Table 1)

### Not stated but needed to reproduce (our reading)

- clean threshold, niter, cell and image size
- masking
- continuum channel selection / flagging
- whether pipeline products or re-calibrated data were used
- how the 10% flux error was combined with statistical error
- spectral index fit method (weights)
- brightness temperature emitting-size assumptions in detail
- nebula flux aperture details

## Analysis recipe

1. **Calibrate and image**: CASA 4.5.3 + ALMA pipeline calibration; natural-weighted clean images per band  
  > "The images were generated using "natural” weighting, in order to maximise the sensitivity." (Observations and Data Reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Identify pulsar by position**: Compute pulsar position at observing epochs from radio coordinates and proper motion; compare with ALMA source position  
  > "we computed the pulsar position at the epochs of our ALMA observations using its radio coordinates as a reference" (Observations and Data Reduction)
   - parameter: astrometric accuracy 56, 48, 43, 123 mas in Bands 3,4,6,7  
  > "is 56, 48, 43, 123 mas, in Band 3, 4, 6, and 7, respectively." (Observations and Data Reduction)
   - fitting: _not stated_
   - validation: astrometric reference quasar J0811-4929  
  > "we used as a reference the radio position of the quasar J0811$-$4929" (Observations and Data Reduction)
3. **Measure flux densities**: Fit elliptical Gaussian within 1 arcsec square aperture centred on the pulsar  
  > "within a square aperture of 1$''$ size centred on its position by fitting an elliptical Gaussian to the source brightness profile" (Results)
   - fitting: elliptical Gaussian  
  > "We measured the pulsar flux density in the four ALMA bands within a square aperture of 1$''$ size centred on its position by fitting an elliptical Gaussian to the source brightness profile." (Results)
   - validation: brightness profile consistent with PSF  
  > "its brightness profile is consistent with the instrument point spread function (PSF)" (Results)
4. **Fit mm spectrum and derive brightness temperature**: Power-law fit to four flux densities; compare with radio and IR/optical extrapolations; Tb from radio-peak flux for emitting region smaller than a neutron star radius  
  > "can be fitted by a PL with spectral index $\alpha =  -0.93 \pm 0.16$ ($\chi^{2}=0.7$)" (Results)
   - assumption: emitting region of one neutron star radius (or 50 R_NS alternative)  
  > "A size as large as, e.g. 50 neutron star radii (Kijak & Gil 2003) would decrease $T_{\rm b}$ by three orders of magnitude." (The pulsar)
   - fitting: power law, chi2=0.7  
  > "The flux densities of the Vela pulsar in the four ALMA bands (Table 1) can be fitted by a PL with spectral index $\alpha =  -0.93 \pm 0.16$ ($\chi^{2}=0.7$)." (Results)
   - validation: _not stated_
5. **Characterise the nebula**: Flux down to 5 sigma contour in Band 7; compare with HST, Chandra, Gemini and archival VLT/NACO Ks images  
  > "flux of $278\pm 33$ $\mu$Jy computed down to a $5 \sigma$ intensity contour" (Results)
   - assumption: distance 287 pc  
  > "At the distance of the Vela pulsar of $287^{+19}_{-17}$ pc (Dodson et al. 2003)" (The Nebula)
   - fitting: _not stated_
   - validation: same structure detected in Gemini and VLT/NACO images  
  > "The same structure seen in the former image is also detected at exactly the same position in the latter" (The Nebula)

## Software

- **CASA** 4.5.3: calibration and imaging (clean)  
  > "Common Astronomy Software Applications (CASA) software package (version 4.5.3)" (Observations and Data Reduction)
- **ALMA pipeline** Pipeline-Cycle3-R4-B: calibration  
  > "the ALMA pipeline (Pipeline-Cycle3-R4-B)" (Observations and Data Reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Pulsar flux density Band 3 (97.5 GHz) | 252 | 35 | uJy | 3 | 252$\pm$35 |
| Pulsar flux density Band 4 (145 GHz) | 170 | 26 | uJy | 3 | 170$\pm$26 |
| Pulsar flux density Band 6 (233 GHz) | 122 | 22 | uJy | 3 | 122$\pm$22 |
| Pulsar flux density Band 7 (343.5 GHz) | 67 | 19 | uJy | 3 | a flux density of 67$\pm$19 $\mu$Jy |
| Spectral index | -0.93 | 0.16 | dimensionless | 4 | spectral index $\alpha  =  -0.93 \pm 0.16$ |
| Nebula Band 7 flux | 278 | 33 | uJy | 5 | flux of $278\pm 33$ $\mu$Jy |
| Nebula spectral index (Ks to Band 7) | -0.79 | 0.02 | dimensionless | 5 | which corresponds to a PL with $\alpha = -0.79 \pm 0.02$ |
| Nebula Band 7 luminosity | ~6e25 | not stated | erg/s | 5 | the Band 7 luminosity of the nebula would be $\sim 6 \times 10^{25}$ erg s$^{-1}$ |

## Qualitative findings

- Transition to incoherent emission must occur at wavelengths shorter than 0.87 mm  
  > "must occur at wavelengths shorter than 0.87 mm, somewhere between the sub-mm and the near-IR" (Summary and Conclusions)

## Claim tuples

- H: Is Vela detectable with ALMA and is its mm emission non-thermal? | E: ALMA Bands 3,4,6,7 imaging and power-law fit | R: Detected in all four bands; alpha=-0.93±0.16 | F: Non-thermal emission from the magnetosphere | **supported**
- H: Does coherent emission extend to the sub-mm? | E: Brightness temperature estimates from ALMA fluxes | R: Tb ~1e17 to 1e15 K | F: Coherence likely maintained in mm/sub-mm | **partially**
- H: Is the NIR extended structure real and visible with ALMA? | E: Band 7 image compared with Gemini and VLT/NACO | R: Extended source 1.4 arcsec SE seen in ALMA and NIR | F: Same object, possibly a counter-jet | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Low-temperature blackbody (cold debris disc) ruled out by ALMA slope  
  > "the slope of the ALMA spectrum rules out a possibility that the mid-IR–to–sub-mm spectrum of the Vela pulsar is described by a low-temperature blackbody" (The pulsar)
- How they decided it was enough: _not stated_
- Limitation (authors): Band 7 detection low significance  
  > "although with a lower significance (S/N $\sim$3.7)" (Results)
- Caveat (inferred, ours): Band 7 detection only ~3.7 sigma
- Caveat (inferred, ours): Brightness temperature depends on assumed emission size
- Caveat (inferred, ours): Only four flux points for the power-law fit
- Caveat (inferred, ours): Extended-structure identification by morphology only

## Reproducibility

- Data public (paper): ALMA project 2015.1.01104.S named; VLT data archival  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.01104.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: clean parameters
- Missing: aperture and fit details
- Missing: Gemini image source
- Data volume (inferred): tens of GB
- Score (inferred): 3/5, Simple recipe and public data, but imaging parameters are missing.
- Rediscovery candidate: yes, Public data, point-source flux measurements and a power-law fit with numeric answers.

## Links

- Companion: Zyuzin et al. 2013 (cite: zyuzin13) (NIR detection of the extended structure and the UV-NIR spectrum)

## Checks

```json
{
 "quotes": 62,
 "quotes_ok": 62,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 45,
  "rate": 0.616
 },
 "evidence_ok": true
}
```
