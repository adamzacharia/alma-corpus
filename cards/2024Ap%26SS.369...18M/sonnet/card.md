# Multi-wavelength observation of MAXI J1348─630 during the outburst in 2019

`2024Ap&SS.369...18M` | Astrophysics and Space Science 2024 | first author: Mandal, Manoj | arXiv: 2104.09926 | DOI: 10.1007/s10509-024-04280-z

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: stellar_physics
- Question: What are the broadband spectral properties of MAXI J1348–630 and its radio/X-ray luminosity correlation during the decay phase of the January 2019 outburst?  
  > "One of the main objectives of this study is to investigate the correlation between the X-ray luminosity and the radio luminosity of MAXI J1348–630" (Radio and X-ray correlation)
- Target **MAXI J1348–630**: coordinates RA 13h48m12.790s, Dec -63d16m28.480s (J2000)  
  > "The phase centre of the continuum image of MAXI J1348–630 is RA $=$ 13 h48m12.790s, Dec $=$ –63$^{ \circ}$16$^{\prime}$28.480$^{\prime \prime}$ (J2000)." (3.1 Continuum image of MAXI J1348–630 using ALMA); "assuming a source distance of 2.2 kpc (cite: Ch21)" (Radio and X-ray correlation); z/distance 2.2 kpc  
  > "The phase centre of the continuum image of MAXI J1348–630 is RA $=$ 13 h48m12.790s, Dec $=$ –63$^{ \circ}$16$^{\prime}$28.480$^{\prime \prime}$ (J2000)." (3.1 Continuum image of MAXI J1348–630 using ALMA); "assuming a source distance of 2.2 kpc (cite: Ch21)" (Radio and X-ray correlation); distance from Chauhan et al. 2021 (HI absorption, ASKAP and MeerKAT)  
  > "The phase centre of the continuum image of MAXI J1348–630 is RA $=$ 13 h48m12.790s, Dec $=$ –63$^{ \circ}$16$^{\prime}$28.480$^{\prime \prime}$ (J2000)." (3.1 Continuum image of MAXI J1348–630 using ALMA); "assuming a source distance of 2.2 kpc (cite: Ch21)" (Radio and X-ray correlation)

## Data provenance

- ALMA projects: 2018.1.01034.T
- bands: Bands 3, 4, 6, 7 (89.56–351.44 GHz)  
  > "The black hole was observed in bands 3, 4, 6, and 7 with XX and YY signal correlators." (2.1 ALMA observation)
- frequencies and spectral setup: 1.875 GHz wide science spectral windows, 1920 channels  
  > "The bandwidth of all science spectral windows is 1.875 GHz, which is divided into 1920 channels." (2.1 ALMA observation)
- continuum bandwidth: _not stated_
- arrays: 12 m array  
  > "we have used 12 m array data from the high-resolution Atacama Large Millimeter/Submillimeter Array" (2.1 ALMA observation)
- configurations: _not stated_
- baselines: 15.1 m to 783.5 m, 43 antennas  
  > "a total of 43 antennas were working with a minimum baseline of 15.1 m and a maximum baseline of 783.5 m." (2.1 ALMA observation)
- angular resolution: 1.22x0.97 arcsec (104, 138 GHz); 0.58x0.44 (242 GHz); 0.35x0.29 (343 GHz)  
  > "the beam sizes are 1.22$^{\prime \prime}\times$0.97$^{\prime \prime}$ for 104 GHz" (3.1 Continuum image of MAXI J1348–630 using ALMA)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 302.4 s, 302.4 s, 423.36 s, 1149.12 s for bands 3, 4, 6, 7  
  > "The on-source total integration times during the observation were 302.400 s, 302.400 s, 423.360 s, and 1149.120 s for *ALMA* bands 3, 4, 6, and 7 respectively." (2.1 ALMA observation)
- observing dates: 2019-05-02  
  > "2018.1.01034.T | Band-3   (89.56–105.43 GHz) | 2019-05-02 | 04:15:00 | 58605.18 |  0.302" (Table 1)
- pi or archival as stated: _not stated_
- Other facility **NICER**: 0.5–10 keV X-ray spectrum, quasi-simultaneous (ObsID 2200530128)  
  > "We used a quasi-simultaneous *NICER* observation with *ALMA* during the decay phase of the January 2019 outburst." (2.2 NICER observation)
- Other facility **Swift**: UVOT uvm2 upper limit; BAT light curve  
  > "The source remained undetected in the *uvm2* band." (3.3 Broadband spectrum)
- Other facility **MAXI/GSC**: 2–20 keV light curve and hardness ratio  
  > "The evolution of HR was studied by using *MAXI*/GSC fluxes in the energy ranges of 2–6 keV and 6–20 keV." (2 Observation and data analysis)
- External data: Source distance 2.2 kpc  
  > "measured the source distance to be $\sim$2.2 kpc by studying the absorption line of HI" (Introduction) [from (cite: Ch21)]
- External data: L_X–L_R diagram tracks of black holes and neutron stars  
  > "Figure [\[fig:lrlx\]](#fig:lrlx) shows the well-known tracks for different black holes and neutron stars in the $L_{X}$ – $L_{R}$ diagram." (Radio and X-ray correlation) [from (cite: Bah18)]

## Processing

### Calibration

- pipeline or manual: Standard ALMA pipeline with extra flagging tasks  
  > "with the standard data reduction pipeline delivered by *ALMA* observatory." (2.1 ALMA observation)
- casa version: CASA v5.4.1  
  > "We used the Common Astronomy Software Application (`CASA v5.4.1`)" (2.1 ALMA observation)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1427–4206 (Perley-Butler 2017 model)  
  > "the source J1427–4206 was used as a bandpass and flux calibrator, and J1337–6503 was used as a phase calibrator." (2.1 ALMA observation)
- flux scale uncertainty: 5%  
  > "matched with the Perley-Butler 2017 flux calibrator model with 5% accuracy using task `SETJY`" (2.1 ALMA observation)
- self calibration: Applied with gaincal and applycal; background RMS from 15–22 to 3.06–8.36 mJy/beam  
  > "we applied the self-calibration method using the `CASA` tasks `GAINCAL` and `APPLYCAL`." (2.1 ALMA observation)

### Imaging

- task: tclean, Stokes I  
  > "we created the continuum image of MAXI J1348–630 using task `TCLEAN` with Stokes-I and robust parameter 0.5." (2.1 ALMA observation)
- deconvolver: _not stated_
- weighting robust: robust = 0.5  
  > "we created the continuum image of MAXI J1348–630 using task `TCLEAN` with Stokes-I and robust parameter 0.5." (2.1 ALMA observation)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: impbcor  
  > "we applied the task `IMPBCOR` for the correction of the primary beam pattern." (2.1 ALMA observation)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.22x0.97, 1.22x0.97, 0.58x0.44, 0.35x0.29 arcsec at 104, 138, 242, 343 GHz  
  > "0.58$^{\prime \prime}\times$0.44$^{\prime \prime}$ for 242 GHz, and 0.35$^{\prime \prime}\times$0.29$^{\prime \prime}$ for 343 GHz." (3.1 Continuum image of MAXI J1348–630 using ALMA)
- final rms: 3.06–8.36 mJy/beam after self-cal  
  > "the background RMS of the source for *ALMA* bands 3, 4, 6, and 7 varied between 3.06–8.36 mJy beam$^{-1}$." (2.1 ALMA observation)

### Not stated but needed to reproduce (our reading)

- Image size, cell size, number of clean iterations, threshold and masking
- Self-calibration solution intervals, number of rounds, and solution type
- Spectral windows used for each band's continuum and line-free channels
- Method for the molecular line search and column density upper limits (software, excitation temperature, line width)
- Band 6 frequency range is misprinted in Table 1
- Whether the pipeline calibration was rerun or archive products used
- NICER model parameters, simpl scattered fraction, abundances, and the conversion to luminosity
- How the 5 GHz flux density was extrapolated

## Analysis recipe

1. **Calibrate and image ALMA continuum**: Pipeline calibration, flux scaling with setjy, extra flagging, mstransform split, tclean continuum imaging, self-calibration, primary beam correction  
  > "After the initial data calibration, we used the task `MSTRANSFORM` to split the corrected target data set with all available rest frequencies." (2.1 ALMA observation)
   - software: CASA, tclean, gaincal, applycal, impbcor
   - parameter: robust = 0.5, Stokes I  
  > "we created the continuum image of MAXI J1348–630 using task `TCLEAN` with Stokes-I and robust parameter 0.5." (2.1 ALMA observation)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure flux densities and spectral index**: 2D Gaussian fit with imfit in each band, then power-law fit to the continuum spectrum  
  > "we fitted the 2D Gaussian over the black hole candidate MAXI J1348–630 using the `CASA` task `IMFIT`." (3.1 Continuum image of MAXI J1348–630 using ALMA)
   - software: CASA imfit
   - fitting: Power law F_nu ∝ nu^alpha; fitting method not stated  
  > "The continuum radio spectrum is fitted using power law ($F_{\nu}\propto \nu ^{\alpha}$) with a spectral index of $\alpha = 0.28\pm 0.02$." (3.1 Continuum image of MAXI J1348–630 using ALMA)
   - validation: _not stated_
3. **Fit NICER X-ray spectrum**: Fit 0.5–10 keV spectrum with tbabs*simpl*diskbb in XSPEC  
  > "The X-ray spectrum in the range of 0.5–10 keV obtained from *NICER* can be described well by using the combinational model consisting of a comptonization component *simpl*" (3.3 Broadband spectrum)
   - software: HEASOFT, nicerl2, nicerl3-spect, nibackgen3C50, XSPEC
   - fitting: _not stated_
   - validation: _not stated_
4. **Compute radio/X-ray luminosities and radio-loudness ratio**: Convert fluxes to luminosities at 2.2 kpc, place in L_X–L_R diagram, and compute the nu I_nu ratio of radio to X-ray  
  > "We have estimated the radio luminosity from the radio flux density using *ALMA* data, assuming a source distance of 2.2 kpc (cite: Ch21)." (Radio and X-ray correlation)
   - assumption: distance 2.2 kpc  
  > "assuming a source distance of 2.2 kpc (cite: Ch21)" (Radio and X-ray correlation)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.4.1: ALMA reduction, imaging, imfit  
  > "We used the Common Astronomy Software Application (`CASA v5.4.1`)" (2.1 ALMA observation)
- **HEASOFT** 6.31: NICER data processing  
  > "We have used the `nicerl2` script to process the *NICER* data in `HEASOFT` 6.31 with the latest caldb version." (2.2 NICER observation)
- **XSPEC** v12.13: X-ray spectral fitting  
  > "We used `XSPEC v12.13` (cite: Ar96) for the spectral fitting." (2.2 NICER observation)
- **nibackgen3C50** : NICER background simulation  
  > "The background corresponding to each epoch of the observation was simulated by using the `nibackgen3C50`" (2.2 NICER observation)
- **uvotsource** : UVOT flux measurement  
  > "We performed the routine `uvotsource` to examine the flux of the source, keeping the background threshold of $5\sigma$." (2.3 Swift observation)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Millimeter flux density range | 12.18–18.47 | not stated | mJy | 2 | The measured flux densities at different frequencies vary between $\sim$12.18 mJy and $\sim$18.47 mJy. |
| Millimeter spectral index alpha | 0.28 | 0.02 | dimensionless | 2 | spectral index of $\alpha = 0.28\pm 0.02$ |
| NICER photon index | 1.68 | 0.01 | dimensionless | 3 | The photon index during the observation is 1.68 $\pm$ 0.01 |
| Inner disk temperature | 0.38 | 0.02 | keV | 3 | The inner disk temperature is found to be nearly 0.38 $\pm$ 0.02 keV |
| Unabsorbed 1–10 keV X-ray flux | 5.4e-9 | not stated | erg cm^-2 s^-1 | 3 | The unabsorbed X-ray flux in the band 1–10 keV is estimated to be 5.4 $\times 10^{-9}$ erg cm$^{-2}$ s$^{-1}$ |
| Radio luminosity at 5 GHz | 1.5e29 | not stated | erg/s | 4 | the corresponding radio luminosity is found to be 1.5 $\times 10^{29}$ erg s$^{-1}$ |
| X-ray luminosity 1–10 keV | 3.1e36 | not stated | erg/s | 4 | the corresponding luminosity is $\sim$3.1 $\times 10^{36}$ erg s$^{-1}$ |
| Radio to X-ray nu I_nu ratio | 1.5e-12 | not stated | dimensionless | 4 | The estimated ratio for MAXI J1348–630 is $\sim 1.5\times 10^{-12}$ |
| Comptonised fraction F_simpl/F_total | ~70% | not stated | percent | 3 | The ratio (F$_{\text simpl}$/F$_{ \text Total}$) is found to be $\sim$70% |

## Qualitative findings

- No molecular lines of H2CO, CH3OH, SO2, 13C34S, OH detected near the source; 3 sigma upper limits derived  
  > "We cannot find the line emission of those molecules in the background." (3.1 Continuum image of MAXI J1348–630 using ALMA)
- Source unresolved in bands 3, 6, 7; band 4 marginally resolved  
  > "the band 4 image was marginally resolved." (3.1 Continuum image of MAXI J1348–630 using ALMA)

## Claim tuples

- H: Is the mm emission from compact jets and how strong is it relative to X-rays? | E: Fit ALMA bands 3–7 continuum spectrum and compare with NICER X-ray flux | R: alpha = 0.28±0.02, flux ratio ~1.5e-12 | F: Weak self-absorbed compact jet synchrotron; source is 'radio-quiet' during decay | **supported**
- H: Does the source follow the standard L_X–L_R track? | E: Place quasi-simultaneous ALMA/NICER luminosities in L_X–L_R diagram | R: Off the well-known tracks | F: Source is a new member of a restricted group of sources | **partially**
- H: What spectral state was the source in? | E: Fit NICER spectrum with tbabs*simpl*diskbb | R: Gamma=1.68, ~70% Comptonised | F: Close to hard state | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Cannot draw conclusions on continuum morphology  
  > "So, we cannot draw any conclusions about the continuum morphology of MAXI J1348–630." (3.1 Continuum image of MAXI J1348–630 using ALMA)
- Caveat (inferred, ours): A single epoch of ALMA; the radio-quiet interpretation rests on a ratio compared with AGN SEDs, which is not well justified for X-ray binaries
- Caveat (inferred, ours): Observations are not strictly simultaneous (NICER ~3 h later; UVOT a day later)
- Caveat (inferred, ours): Extrapolating the mm flux to 5 GHz assumes the same power law with no turnover
- Caveat (inferred, ours): Flux uncertainties and calibration systematics are not propagated into luminosities
- Caveat (inferred, ours): Background rms of 3–8 mJy/beam is comparable to source flux, implying low S/N for flux densities

## Reproducibility

- Data public (paper): ALMA and X-ray data public  
  > "The *ALMA* data are publicly available at <https://almascience.nao.ac.jp/asax/> (project id: 2018.1.01034.T)." (Data availability)
- Products in archive: _not stated_
- Missing: Imaging parameters (cell, size, masks, iterations)
- Missing: Self-calibration details
- Missing: Line search method and column density assumptions
- Missing: NICER fit details
- Data volume (inferred): ~50-100 GB for ALMA raw data plus small NICER/Swift
- Score (inferred): 3/5, Data public and the main steps are named, but imaging and self-calibration, line analysis and X-ray fit details are missing.
- Rediscovery candidate: no, Recipe lacks important details, though results are numeric and data are public.

## Links

- Method: (cite: Per07) (Perley-Butler flux calibrator model)
- Method: (cite: St09) (simpl Comptonisation model)
- Companion: (cite: Car21) (Radio/X-ray study of the same outburst)
- Companion: (cite: Zh20) (NICER study of the outburst)

## Checks

```json
{
 "quotes": 59,
 "quotes_ok": 59,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 42,
  "rate": 0.6
 },
 "evidence_ok": true
}
```
