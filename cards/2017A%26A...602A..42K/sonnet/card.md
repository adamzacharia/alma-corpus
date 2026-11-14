# Subarcsecond imaging of the water emission in Arp 220

`2017A&A...602A..42K` | Astronomy and Astrophysics 2017 | first author: König, S. | arXiv: 1612.07668 | DOI: 10.1051/0004-6361/201630331

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, astrochemistry
- Question: What is the nature (maser vs thermal, AGN vs starburst) of the water emission at 22, 183 and 325 GHz in the two nuclei of Arp 220, using sub-arcsecond imaging?  
  > "We use sub-arcsecond resolution observations to tackle the nature of the water emission in Arp 220." (abstract)
- Target **Arp 220 (East and West nuclei)**: coordinates _not stated_; z/distance 78 Mpc luminosity distance (1" = 378 pc)  
  > "At a luminosity distance of 78 Mpc (1$^{\prime\prime}$ = 378 pc)" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00453.S, 2011.0.00018.SV
- bands: Band 5 (183 GHz) and Band 7 (325 GHz)  
  > "ALMA Band 5 science verification observations of the 183 GHz" (abstract)
- frequencies and spectral setup: Band 5: 1.875 GHz window at 976.562 kHz resolution centred on water line; extra windows on HNC 2-1, CS 4-3, CH3OH  
  > "One spectral window, with a bandwidth of 1.875 GHz and spectral resolution of 976.562 kHz, was centered on the water line." (2.1.1 Band 5)
- continuum bandwidth: _not stated_
- arrays: Band 5: 12 antennas; Band 7: 39 antennas  
  > "The array was composed of 39 antennas." (2.1.2 Band 7)
- configurations: _not stated_
- baselines: 30 m to 480 m (Band 5)  
  > "in a configuration with baselines ranging from 30 m to 480 m" (2.1.1 Band 5)
- angular resolution: 0.79" x 0.71" (Band 5)  
  > "resulting in a beam size of 0.79$^{\prime\prime}$ $\times$ 0.71$^{\prime\prime}$" (2.1.1 Band 5)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: Band 5: 2016 July 16; Band 7: June 16 and July 17, 2014  
  > "were obtained on June 16 and July 17, 2014" (2.1.2 Band 7)
- pi or archival as stated: _not stated_
- Line: H2O 3_13-2_20 (183.310 GHz)
- Line: H2O 5_15-4_22 (325.153 GHz)
- Line: H2O 6_16-5_23 (22.235 GHz)
- Other facility **IRAM 30 m**: Single-dish 183 and 325 GHz water spectra for variability comparison  
  > "were performed in December 2012 (project: 189-12, PI: J. Cernicharo)" (2.2 IRAM 30 m)
- Other facility **VLA**: 22 GHz H2O data (from earlier work)  
  > "supplementary 22 GHz H$_{\rm 2}$O 6$_{\rm 16}-5_{\rm 23}$ VLA observations" (abstract)
- Other facility **APEX**: Literature 183 GHz flux for comparison  
  > "APEX | 35$^{\prime\prime}$ | 50 $\pm$ 6" (Table 1)
- External data: 22 GHz VLA water data and NH3 blending  
  > "is blended with the NH$_{\rm 3}$ (3,1) absorption line, with a major effect towards Arp 220 West (cite: zsch16)" (2.3 22 GHz VLA data) [from (cite: zsch16)]
- External data: Synthetic LTE spectrum model from Band 6/7 survey used to correct blends  
  > "we used the synthetic spectrum model fit to Band 6 and 7 observations (Martín et al. in prep.)" (2.1.3 Contribution of line blending) [from Martín et al. in prep.]
- External data: Collisional rates of H2O  
  > "using new collisional rates of (cite: dan11)" (4.3 Excitation) [from (cite: dan11)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.7.0  
  > "using the “tclean” task in CASA 4.7.0" (2.1.1 Band 5)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Band 5: model from shallow clean of line-free channels in SPW 2 and 3, phase-only gain per integration applied to all SPWs; Band 7 data self-calibrated  
  > "Then, gain phase solutions were determined for each integration and applied to all spectral windows, including the lower sideband." (2.1.1 Band 5)

### Imaging

- task: tclean in CASA 4.7.0; later GILDAS/MAPPING for analysis  
  > "the visibilities were converted into FITS format and imported in the GILDAS/MAPPING" (2.1.1 Band 5)
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
- smoothing: Band 5 averaged to 20 km/s channels; Band 7 imaged to match Band 5 spatial and spectral resolution  
  > "The calibrated visibilities were imaged to match the spatial and spectral resolution of the Band 5 data." (2.1.2 Band 7)
- final beam: 0.79" x 0.71"  
  > "a beam size of 0.79$^{\prime\prime}$ $\times$ 0.71$^{\prime\prime}$" (2.1.1 Band 5)
- final rms: _not stated_

### Inherited from earlier work

- Band 7 calibration details deferred to Martín et al.  
  > "A more detailed description of the calibration of the data will be presented in Martín et al. (in prep.)." (2.1.2 Band 7) [from Martín et al. (in prep.)]

### Not stated but needed to reproduce (our reading)

- Deconvolver, weighting/robust, cell and image size, masks and clean threshold
- Band 5 flux, bandpass and gain calibrator names (lost in text) and flux scale
- Calibration pipeline version for Band 7
- Line-free channels and continuum subtraction method
- Synthetic spectrum model parameters (Martín et al., in prep.)
- Primary beam correction and aperture used for spectra
- MADEX model grid details and how dilution factors were fitted

## Analysis recipe

1. **Image Band 5 and Band 7 cubes**: tclean in CASA; Band 7 imaged to match Band 5 resolution; channels binned to 20 km/s  
  > "For analysis purposes, the channels were further binned to widths of 20 km s$^{\rm -1}$." (2.1.2 Band 7)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Correct water lines for blending**: Subtract contaminants using LTE synthetic spectrum fit to Band 6/7, extrapolated to Band 5  
  > "The model fit was performed assuming LTE conditions and includes the contribution from more than 30 species" (2.1.3 Contribution of line blending)
   - assumption: LTE  
  > "The model fit was performed assuming LTE conditions" (2.1.3 Contribution of line blending)
   - fitting: _not stated_
   - validation: Extrapolated model fits emission outside the water line  
  > "the extrapolation to Band 5 appears to properly fit the emission outside the water line" (2.1.3 Contribution of line blending)
3. **Correct 22 GHz line for NH3 absorption**: Simultaneous Gaussian fit of NH3 (3,1) and (4,2) with shared centroid and width  
  > "We assume a simple Gaussian line profile, with the same centroid velocity and linewidth for both lines" (2.3 22 GHz VLA data)
   - parameter: v0 = -94.5 ± 5.5 km/s, FWHM = 287 ± 13 km/s, ratio 1.14 ± 0.08  
  > "We find v$_{\rm 0}$ = -94.5 $\pm$ 5.5 km s$^{\rm -1}$, FWHM = 287 $\pm$ 13 km s$^{\rm -1}$" (2.3 22 GHz VLA data)
   - fitting: _not stated_
   - validation: _not stated_
4. **Test time variability**: Degrade ALMA data to single-dish beams and compare integrated flux and FWHM with IRAM 30m/APEX  
  > "The flux recovered from the degraded ALMA data (35$^{\prime\prime}$ aperture) is $\sim$56.0 Jy km s$^{\rm -1}$." (4.1 Time variability)
   - fitting: _not stated_
   - validation: Consistent within uncertainties, no variability  
  > "suggests that the water line did not vary in time in between observations" (4.1 Time variability)
5. **Excitation modelling of three water lines**: MADEX non-LTE models over density, Tk (50-300 K), N(H2O)/dv, with/without dust continuum source and a dilution factor  
  > "We have modelled the water emission at 22, 183 and 325 GHz in Arp 220 using the MADEX code (cite: cer12)." (4.3 Excitation)
   - software: MADEX
   - parameter: Central source 5 pc, water layer 1.5 pc from outer radius  
  > "The central source has a size of 5 pc and the layer of water vapor was placed at a distance of 1.5 pc from the outer radius of the continuum source." (4.3 Excitation)
   - assumption: ortho-to-para ratio 3:1; main collider ortho H2; 22 GHz intensity uncertainty 50%  
  > "we assume an ortho-to-para ratio of 3:1" (4.3 Excitation)
   - fitting: Grid comparison by eye to observed brightness temperatures; no sampler  
  > "Fig. [5](#fig:modelling) shows the predicted intensities for a large range of H$_{\rm 2}$ densities, gas temperatures (50 to 300 K) and column densities" (Excitation)
   - validation: No-dust predictions agree with Cernicharo et al. 2006  
  > "The predicted brightness temperatures, in absence of dust, agree very well with those of (cite: cer06)." (4.3 Excitation)

## Software

- **CASA** 4.7.0: Calibration and tclean imaging  
  > "using the “tclean” task in CASA 4.7.0" (2.1.1 Band 5)
- **GILDAS/MAPPING** : Further analysis of visibilities  
  > "imported in the GILDAS/MAPPING" (2.1.1 Band 5)
- **MADEX** : Non-LTE excitation modelling of water lines  
  > "using the MADEX code (cite: cer12)" (4.3 Excitation)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 183 GHz integrated intensity, Arp 220 West | 47.8 | not stated | Jy km/s | 1 | integrated intensity: $\sim$47.8 Jy km s$^{\rm -1}$ |
| 183 GHz integrated intensity, Arp 220 East | 13.7 | not stated | Jy km/s | 1 | ($\sim$13.7 Jy km s$^{\rm -1}$) |
| 325 GHz integrated intensity West / East | 25.3 / 9.1 | not stated | Jy km/s | 1 | Integrated fluxes amount to $\sim$25.3 Jy km s$^{\rm -1}$ and 9.1 Jy km s$^{\rm -1}$ in Arp 220 West and East |
| 22 GHz integrated intensity East / West | 0.34 / 0.17 | not stated | Jy km/s | 3 | integrated intensity: $\sim$0.34 Jy km s$^{\rm -1}$ |
| Degraded ALMA 183 GHz flux (35" aperture) | 56.0 | not stated | Jy km/s | 4 | is $\sim$56.0 Jy km s$^{\rm -1}$ |
| Peak brightness temperature 183 GHz West | 11.1 | not stated | K | 1 | / 183 GHz / 2.9 K  / 11.1 K /    3.8    / |
| Dilution factor range for common solution | 0.0007 to 0.005 | not stated | dimensionless | 5 | the extremes of the estimated dilution factors of 0.0007 and 0.005 would be equivalent to a single source of 0.018$^{\prime\prime}$ (7 pc) and 0.05$^{\prime\prime}$ (18 pc) |

## Qualitative findings

- Brightness temperatures are low and line shapes are broad and smooth, unlike typical megamasers  
  > "These temperatures are much lower than what is typically expected for maser emission" (4.2.1 Ratios)

## Claim tuples

- H: Is the 183/325 GHz water emission variable? | E: Compare degraded ALMA spectra with IRAM 30m and APEX spectra | R: Fluxes and widths agree within uncertainties | F: No evidence for variability | **supported**
- H: Does a single large cloud explain all three lines? | E: MADEX modelling with and without dust | R: No single-cloud solution for all three lines | F: Need many small diluted clouds, Tk 200-300 K, high column density | **supported**
- H: Origin of the water emission | E: Line shapes, brightness temperatures, velocity fields, excitation | R: Low Tb, smooth lines, rotation like CO | F: Many independent masers from star-forming regions, not AGN | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: AGN jet-cloud interaction maser rejected because velocity field shows ordinary rotation  
  > "Thus it seems unlikely that the maser emission is due to an interaction between an AGN jet and molecular clouds in its vicinity." (4.2.2 Line shapes)
- How they decided it was enough: _not stated_
- Limitation (authors): 22 GHz line uncertain due to NH3 contamination; same dilution factor assumed for all lines  
  > "the solution found fitting all three lines has to be taken with caution in view of the uncertainties in the emission of the 22 GHz line" (4.3 Excitation)
- Caveat (inferred, ours): Excitation grid fitting is qualitative with no formal uncertainties
- Caveat (inferred, ours): Blend correction relies on an unpublished model
- Caveat (inferred, ours): Flux comparison for variability has limited S/N and the IRAM data are noisy

## Reproducibility

- Data public (paper): ALMA Band 5 science verification and Band 7 project data cited by project code  
  > "ADS/JAO.ALMA#2011.0.00018.SV and ADS/JAO.ALMA#2012.1.00453.S" (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: Unpublished synthetic spectrum model
- Missing: MADEX grid details
- Data volume (inferred): ~50-100 GB
- Score (inferred): 4/5, Public data, but imaging details and blend model are unstated and the modelling is semi-qualitative.
- Rediscovery candidate: no, Recipe lacks imaging and model details; the key corrections depend on unpublished work.

## Links

- Method: (cite: cer12) (MADEX code)
- Companion: Martín et al. in prep. (Band 6/7 line survey and synthetic spectrum)
- Companion: (cite: zsch16) (22 GHz VLA data)
- Related: ALMA Band 5 science verification
- Related: ALMA Bands 6/7 spectral line survey of Arp 220

## Checks

```json
{
 "quotes": 56,
 "quotes_ok": 56,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.0.00018.SV"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 40,
  "rate": 0.533
 },
 "evidence_ok": true
}
```
