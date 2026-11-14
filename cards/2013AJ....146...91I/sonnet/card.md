# ALMA Detection of the Vibrationally Excited HCN J = 4-3 Emission Line in the AGN-hosting Luminous Infrared Galaxy IRAS 20551-4250

`2013AJ....146...91I` | The Astronomical Journal 2013 | first author: Imanishi, Masatoshi | arXiv: 1308.4414 | DOI: 10.1088/0004-6256/146/4/91

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, astrochemistry, agn_and_quasars
- Question: Is vibrationally excited HCN J=4-3 emission present in the AGN-hosting LIRG IRAS 20551-4250, and how does its HCN-to-HCO+ J=4-3 flux ratio compare with starburst galaxies?  
  > "To investigate whether HCN emission is indeed enhanced (relative to other molecular lines) in AGNs compared to starbursts, and to test whether vibrationally excited HCN emission lines are generally present in AGNs" (Introduction)
- Target **IRAS 20551-4250**: coordinates continuum peak (J2000) 20 58 26.79, -42 39 00.3  
  > "(20 58 26.79, $-$42 39 00.3)" (Table 3); "luminous infrared galaxy IRAS 20551$-$4250 at z=0.043, which is diagnosed to contain a luminous buried AGN" (Introduction); z/distance z=0.043 (~190 Mpc)  
  > "(20 58 26.79, $-$42 39 00.3)" (Table 3); "luminous infrared galaxy IRAS 20551$-$4250 at z=0.043, which is diagnosed to contain a luminous buried AGN" (Introduction); distance from redshift with H0=71, OmegaM=0.27, OmegaL=0.73  
  > "(20 58 26.79, $-$42 39 00.3)" (Table 3); "luminous infrared galaxy IRAS 20551$-$4250 at z=0.043, which is diagnosed to contain a luminous buried AGN" (Introduction)

## Data provenance

- ALMA projects: 2011.0.00020.S
- bands: ALMA band 7  
  > "HCO$^{+}$ J=4–3 ($\nu_{\rm rest}$ = 356.734 GHz) lines can be simultaneously observed in ALMA band 7." (2 Observations and Data Analysis)
- frequencies and spectral setup: Four spectral windows (centers 339.890, 341.835, 351.883, 353.589 GHz) for HCN/HCO+; two (347.680, 335.570 GHz) for HNC; 1.875 GHz band mode, 3840 channels  
  > "The widest 1.875 GHz band mode and 3840 total channel number were adopted." (2 Observations and Data Analysis)
- continuum bandwidth: _not stated_
- arrays: 17-19 antennas used  
  > "HNC J=4–3 | 2012 June 2  | 19" (Table 2)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.6 x 0.4 arcsec (continuum-a)  
  > "0.6 $\times$ 0.4 (90$^{\circ}$)" (Table 3)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2012 June 1, June 2, July 26  
  > "HCN/HCO$^{+}$ J=4–3 | 2012 June 1  | 18" (Table 2)
- pi or archival as stated: _not stated_
- Line: HCN J=4-3 (354.505 GHz)
- Line: HCO+ J=4-3 (356.734 GHz)
- Line: HNC J=4-3 (362.630 GHz)
- Line: HCN v2=1 J=4-3 (l=1f) (356.256 GHz)
- Line: H2S 3(2,1)-3(1,2) (369.101 GHz)
- Line: CH3CN (+CCH) v=0 19(3)-18(3) (349.393 GHz)
- External data: IRAS FSC fluxes at 12, 25, 60, 100 um for IR luminosities  
  > "are *IRAS* fluxes at 12 $\mu$m, 25 $\mu$m, 60 $\mu$m, and 100 $\mu$m, respectively, taken from the IRAS *FSC* catalog." (Table 1) [from IRAS FSC catalog]
- External data: NGC 1614 HCN/HCO+ and HCN/HNC J=4-3 ratios for comparison  
  > "The ratios at four different positions in the starburst galaxy NGC 1614, taken with our ALMA Cycle 0 observations (cite: ima13), are overplotted for comparison." (Line Flux Ratio) [from (cite: ima13)]
- External data: HCN v2=1 to v=0 ratio in NGC 4418  
  > "which is a factor of $\sim$5 smaller than the ratio observed in NGC 4418 (cite: sak10)." (4.1 Vibrationally excited HCN J=4–3 emission line) [from (cite: sak10)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Started from calibrated data provided by JAO  
  > "We started data analysis from calibrated data provided by the Joint ALMA Observatory." (2 Observations and Data Analysis)
- flux calibrator: Neptune (bandpass 3C454.3, phase J2056-472)  
  > "| HCN/HCO$^{+}$ J=4–3 | 2012 June 1  | 18      | 3C454.3  | Neptune | J2056$-$472 |" (Table 2)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA-style task "clean" for line and continuum  
  > "The “clean” procedure was also applied to the continuum data." (2 Observations and Data Analysis)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 0.1 arcsec per pixel  
  > "We employed 40 channel spectral binning ($\sim$17 km s$^{-1}$) and 0.1$''$ pixel$^{-1}$ spatial binning in this clean procedure." (2 Observations and Data Analysis)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum level estimated from line-free channels and subtracted  
  > "We selected channels that were free of these emission lines to estimate the continuum flux level." (2 Observations and Data Analysis)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: 40 channel spectral binning (~17 km/s)  
  > "We employed 40 channel spectral binning ($\sim$17 km s$^{-1}$)" (2 Observations and Data Analysis)
- final beam: 0.6x0.4 arcsec (continuum-a), 0.8x0.4 (continuum-b)  
  > "0.8 $\times$ 0.4 (91$^{\circ}$)" (Table 3)
- final rms: 0.14 mJy/beam (continuum-a), 0.19 (continuum-b)  
  > "| b | 341.6 | 10.1 (52$\sigma$)" (Table 3)

### Not stated but needed to reproduce (our reading)

- CASA version and whether the JAO calibration was the delivered scripts
- clean weighting/robust, deconvolver, masks, threshold
- specific line-free channel ranges
- channel ranges used for moment 0 maps
- Gaussian fitting method and uncertainty treatment
- how the v2=1 line was fit with fixed FWHM=100 km/s (and the choice)
- flux scale uncertainty
- primary beam correction

## Analysis recipe

1. **Image continuum and lines**: Subtract continuum from line-free channels, then clean with 40-channel binning and 0.1" pixels  
  > "We then subtracted this continuum level and performed the task “clean” for molecular line data." (2 Observations and Data Analysis)
   - software: CASA clean
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract spectra and moment maps and fit Gaussians**: Moment 0 maps by combining channels with signal; Gaussian fits to spectra at continuum peak within beam  
  > "Integrated intensity (moment 0) maps of individual molecular lines are created, by combining channels with clearly discernible signals." (Results)
   - fitting: Gaussian fits  
  > "The results of the Gaussian fits for individual molecular lines are summarized in Table 4." (Results)
   - validation: Vib. HCN judged real because several consecutive channels exceed 4 mJy (1 sigma ~1.2 mJy), at expected frequency and peak position  
  > "we judge that the HCN v$_{2}$=1 J=4–3 (l=1f) emission feature is real." (4.1 Vibrationally excited HCN J=4–3 emission line)
3. **Estimate free-free contribution to continuum**: Use eq. (1) of Nakanishi et al. 2005 with far-infrared luminosity, assuming it is all starburst  
  > "by using the equation (1) of (cite: nak05) and even assuming that the far-infrared luminosity is dominated by starburst activity, with no AGN contribution." (Results)
   - assumption: Far-infrared luminosity entirely starburst (upper limit on free-free)  
  > "even assuming that the far-infrared luminosity is dominated by starburst activity, with no AGN contribution" (Results)
   - fitting: _not stated_
   - validation: _not stated_
4. **Compare line flux ratios**: HCN/HCO+ and HCN/HNC J=4-3 flux ratios compared with NGC 1614; vib/v=0 HCN ratio compared with NGC 4418  
  > "IRAS 20551$-$4250 shows a higher HCN-to-HCO$^{+}$ J=4–3 flux ratio than the starburst galaxy NGC 1614." (Line Flux Ratio)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA (task clean)** : Cleaning/imaging of line and continuum data  
  > "performed the task “clean” for molecular line data" (2 Observations and Data Analysis)
- **Splatalogue** : Line identification of rest frequencies  
  > "(http://www.splatalogue.net)" (Results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HCN v2=1 J=4-3 (l=1f) line flux | 0.39 | 0.07 | Jy km/s | 2 | 0.26(5.0$\sigma$); 0.39$\pm$0.07 \[Jy km s$^{-1}$\] |
| HCN J=4-3 flux | 9.5 | 0.2 | Jy km/s | 2 | / HCN J=4–3 / 8.1 (77$\sigma$) / 0.10 |
| HCO+ J=4-3 flux | 14 | 1 | Jy km/s | 2 | / HCO$^{+}$ J=4–3 / 12 (85$\sigma$) / 0.14 |
| HNC J=4-3 flux | 5.8 | 0.2 | Jy km/s | 2 | / HNC J=4–3 / 5.1 (47$\sigma$) / 0.11 |
| Continuum-a peak flux at 346.7 GHz | 9.4 | rms 0.14 | mJy/beam | 1 | / a / 346.7 / 9.4 (67$\sigma$) |
| HCN v2=1 to v=0 flux ratio | ~0.04 | not stated | dimensionless | 4 | The HCN J=4–3 v$_{2}$=1 (l=1f) to v=0 flux ratio is $\sim$0.04 |
| HCN-to-HCO+ J=4-3 flux ratio | ~0.7 | not stated | dimensionless | 4 | The HCN-to-HCO$^{+}$ J=4–3 flux ratio ($\sim$0.7) is higher than in the other starburst-dominated galaxy ($\sim$0.2) |

## Qualitative findings

- First extragalactic detections of H2S and CH3CN(+CCH) lines at these transitions; rotating gas seen in moment 1 maps  
  > "To our knowledge, ours is the first detection of these lines in extragalactic sources." (Results)

## Claim tuples

- H: Is vibrationally excited HCN J=4-3 detectable in an AGN-hosting LIRG? | E: Band 7 ALMA spectrum at continuum peak near HCO+ J=4-3 | R: Weak feature at 341.51-341.58 GHz, peak ~4.8 mJy, ~5 sigma, flux 0.39±0.07 Jy km/s | F: Tentative second extragalactic detection; vibrational excitation of HCN may be common in AGN-hosting galaxies | **partially**
- H: Is HCN-to-HCO+ J=4-3 higher in the AGN LIRG than in starbursts? | E: Compare with NGC 1614 ratios | R: ~0.7 vs ~0.2 | F: Higher in IRAS 20551-4250 but still below unity | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Submillimeter lines are used because dust extinction is small, to probe buried AGNs  
  > "To investigate buried AGNs in dusty LIRG nuclei, we must observe at wavelengths in which dust extinction effects are small." (Introduction)
- Alternative: Spike noise rejected as explanation for the feature since it spans several consecutive spectral elements  
  > "it is very unlikely that the excess feature is caused by a spike noise" (4.1 Vibrationally excited HCN J=4–3 emission line)
- How they decided it was enough: _not stated_
- Limitation (authors): No constraint on HCN 14 um absorption, so no further quantitative discussion of pumping  
  > "no meaningful constraint on the HCN 14 $\mu$m absorption feature is placed for IRAS 20551$-$4250 (cite: lah07), so that further discussion is not possible." (4.1 Vibrationally excited HCN J=4–3 emission line)
- Caveat (inferred, ours): Detection of vib. HCN is only ~5 sigma with the FWHM fixed in the fit
- Caveat (inferred, ours): Blending with the bright HCO+ wing could bias the flux
- Caveat (inferred, ours): Single source; generalization to AGNs is speculative
- Caveat (inferred, ours): Gaussian fits at one position without a stated error budget

## Reproducibility

- Data public (paper): Data from ALMA Cycle 0 program 2011.0.00020.S  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00020.S ." (Acknowledgments)
- Products in archive: _not stated_
- Missing: clean parameters
- Missing: line-free channel ranges
- Missing: moment map channel ranges
- Missing: fit procedure details
- Data volume (inferred): ~20-50 GB raw for four Cycle 0 execution blocks
- Score (inferred): 3/5, Public data and simple analysis, but imaging parameters and fit details are not given.
- Rediscovery candidate: yes, Public data, simple recipe, and numeric line fluxes can be checked, though details are sparse.

## Links

- Companion: Imanishi & Nakanishi 2013, AJ, 146, 47 (cite: ima13) (NGC 1614 ALMA Cycle 0 data used for comparison)
- Companion: Sakamoto et al. 2010 (cite: sak10) (first extragalactic detection of vib. HCN J=4-3 in NGC 4418)
- Related: ALMA Cycle 0 program of HCN/HCO+/HNC J=4-3 in six LIRGs

## Checks

```json
{
 "quotes": 55,
 "quotes_ok": 55,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 64,
  "stated": 34,
  "rate": 0.531
 },
 "evidence_ok": true
}
```
