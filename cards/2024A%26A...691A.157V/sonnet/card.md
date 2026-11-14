# Identifying the mechanisms of water maser variability during the accretion burst in NGC6334I

`2024A&A...691A.157V` | Astronomy and Astrophysics 2024 | first author: Vorster, J. M. | arXiv: 2408.15700 | DOI: 10.1051/0004-6361/202450751

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation, milky_way_ism
- Question: How do 22 GHz water masers in NGC6334I respond to the 2015 accretion burst of MM1B, and which variability mechanisms (background, pump, hydrodynamic; C- vs J-shock) explain it?  
  > "We aim to observe the 22 GHz water maser response induced by the accretion burst in NGC6334I-MM1B and to identify the underlying maser variability mechanisms." (abstract)
- Target **NGC6334I**: coordinates (17h20m53.44s, -35d47'02.20'') (ALMA phase centre)  
  > "We observed NGC6334I with ALMA in Cycle 6 (PI: T. Hirota, 2018.1.00024.S) in band 7." (2.2 ALMA Band 7 Observations); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2018.1.00024.S
- bands: Band 7  
  > "We observed NGC6334I with ALMA in Cycle 6 (PI: T. Hirota, 2018.1.00024.S) in band 7." (2.2 ALMA Band 7 Observations)
- frequencies and spectral setup: 321.2 GHz narrow-band spw; 0.245 MHz (0.23 km/s) resolution, regridded to 0.25 km/s  
  > "The spectral resolution was 0.245 MHz corresponding to a velocity resolution of 0.23 km s$^{-1}$. We regridded the spectra to a velocity resolution of 0.25 km s$^{-1}$." (2.2 ALMA Band 7 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-7, 48 antennas  
  > "in configuration C43$-$7 with 48 antennas" (2.2 ALMA Band 7 Observations)
- baselines: _not stated_
- angular resolution: 0.14x0.10 arcsec, PA -78 deg  
  > "The beam size was 0.14$\times$0.10 arcsec with a position angle of $-78$ degrees." (2.2 ALMA Band 7 Observations)
- max recoverable scale: _not stated_
- sensitivity: line-free RMS 27 mJy/beam after self-calibration  
  > "After self-calibration, the line-free RMS noise was 27 mJy beam$^{-1}$." (2.2 ALMA Band 7 Observations)
- time on source: 81.2 minutes  
  > "The on-source time was 81.2 minutes." (2.2 ALMA Band 7 Observations)
- observing dates: 1 September 2019  
  > "The observations were carried out on 1 September 2019" (2.2 ALMA Band 7 Observations)
- pi or archival as stated: PI: T. Hirota  
  > "We observed NGC6334I with ALMA in Cycle 6 (PI: T. Hirota, 2018.1.00024.S) in band 7." (2.2 ALMA Band 7 Observations)
- Line: H2O 10(2,9)-9(3,6) (321.225677 GHz)
- Other facility **VERA**: Seven epochs of 22 GHz water maser VLBI, 2014-2016  
  > "We did seven epochs of observations of the 22.23508 GHz water maser transition with VERA between 2014 and 2016." (2.1 VERA Observations)
- Other facility **HartRAO**: 22 GHz single-dish maser monitoring time series (from MacLeod et al. 2018)  
  > "We used HartRAO monitoring data of 22 GHz water masers" (4.2.2 Testing Variance Increase)
- External data: JVLA 22 GHz water maser positions/fluxes (2017.0, 2017.8), including 56 Jy spot used for ratio R  
  > "The 22 GHz spot has a reported integrated flux of 56 Jy, implying $R = F_{\rm 22}/F_{\rm 321} =  2.1$" (4.1.2 Responses of Water Masers) [from (cite: 2018ApJ...866...87B)]
- External data: KaVA proper motions of reference feature for absolute frame  
  > "This was done by setting the pre-burst and burst proper motions of our VERA reference feature equal to the proper motions of the same maser feature in the KaVA observations" (2.1.2 Proper Motions) [from (cite: 2021ApJ...908..175C)]
- External data: Luminosities L(pre)=4300 Lsun, L(post)=49000 Lsun and bolometric increase factor  
  > "The pre-burst and burst luminosity has been estimated with $L_*(t_{\rm pre}) = 4300\pm900L_\odot$ and $L_*(t_{\rm post}) = 49000\pm8000 L_\odot$." (4.3.3 Radiative Heating of H2) [from (cite: 2021ApJ...912L..17H)]

## Processing

### Calibration

- pipeline or manual: EA-ARC calibration pipeline, then phase-only self-calibration in CASA  
  > "The pre-imaging calibration was done by the East-Asian ALMA Regional Center (EA-ARC) calibration pipeline. We then carried out phase-only self-calibration and imaging with the Common Astronomy Software Applications" (2.2 ALMA Band 7 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1924-2914 (amplitude and bandpass); phase calibrator J1717-3342  
  > "The amplitude and bandpass calibrator was J1924-2914, while the phase calibrator was J1717-3342." (2.2 ALMA Band 7 Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA tclean  
  > "The CASA task `tclean` produced the spectral cubes with a robust clean parameter of 0.5 was used with a cell size of 0.0125$'$." (2.2 ALMA Band 7 Observations)
- deconvolver: _not stated_
- weighting robust: robust = 0.5  
  > "robust clean parameter of 0.5" (2.2 ALMA Band 7 Observations)
- uv taper: _not stated_
- cell size: 0.0125 (as printed, with prime symbol)  
  > "was used with a cell size of 0.0125$'$" (2.2 ALMA Band 7 Observations)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: UV-domain continuum subtraction  
  > "Line data were obtained by subtracting the continuum in the UV domain." (2.2 ALMA Band 7 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.14x0.10 arcsec, PA -78 deg  
  > "The beam size was 0.14$\times$0.10 arcsec with a position angle of $-78$ degrees." (2.2 ALMA Band 7 Observations)
- final rms: 27 mJy/beam  
  > "After self-calibration, the line-free RMS noise was 27 mJy beam$^{-1}$." (2.2 ALMA Band 7 Observations)

### Inherited from earlier work

- Maser association names and swapped CM2-W1/W2 convention  
  > "The nomenclature for the maser associations originates from (cite: 2018ApJ...866...87B) and was also used by (cite: 2021ApJ...908..175C)." (Footnote 1) [from (cite: 2018ApJ...866...87B); (cite: 2021ApJ...908..175C)]
- Absolute velocity frame assumes CM2-W2 mean speed equals JVLA upper limit 3.8 mas/yr  
  > "assuming that all the maser features in CM2-W2 have a mean speed equal to the upper limit of $3.8$ mas yr$^{-1}$ set by the JVLA observations of (cite: 2018ApJ...866...87B)" (2.1.2 Proper Motions) [from (cite: 2018ApJ...866...87B)]

### Not stated but needed to reproduce (our reading)

- CASA version and EA-ARC pipeline version
- Self-calibration solution intervals and reference
- Spectral window frequency details, channel range, continuum channels
- Image size and clean threshold/mask
- Fit parameters of 2D Gaussians for 321 GHz maser
- Distance to NGC6334I used for transverse speeds
- Values of eta, r_maser, aspect ratio for temperature estimate
- Details of HartRAO data processing and permutation test (number of permutations)

## Analysis recipe

1. **Image 321 GHz water maser cube**: EA-ARC pipeline calibration, phase-only self-calibration, UV continuum subtraction, tclean cubes  
  > "The pre-imaging calibration was done by the East-Asian ALMA Regional Center (EA-ARC) calibration pipeline." (2.2 ALMA Band 7 Observations)
   - software: CASA, tclean
   - parameter: robust 0.5, cell 0.0125, 0.25 km/s channels  
  > "robust clean parameter of 0.5 was used with a cell size of 0.0125$'$" (2.2 ALMA Band 7 Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit 321 GHz maser per channel and derive brightness temperature**: channel-by-channel 2D Gaussian fits; brightness temperature lower limit from peak intensity and size upper limit  
  > "shows the position, $V_{\rm LSR}$, integrated flux, peak intensity and deconvolved size from channel-by-channel 2D Gaussian fits to the maser feature." (Results, 321 GHz Water Masers)
   - fitting: 2D Gaussian per channel  
  > "channel-by-channel 2D Gaussian fits to the maser feature" (3.4 321 GHz Water Masers)
   - validation: Brightness temperature far above thermal implies maser  
  > "the lower limit of the brightness temperature for the 321 GHz emission is 3.2$\times 10^{4}$ K, implying maser emission" (3.4 321 GHz Water Masers)
3. **Infer shock type from 22/321 GHz flux ratio**: R = F22/F321 using co-spatial JVLA 22 GHz spot; R~1 C-shock, R~10 J-shock  
  > "implying $R = F_{\rm 22}/F_{\rm 321} =  2.1$, which is more consistent with high temperature $T \sim 1000$ K maser emission from a C-shock" (4.1.2 Responses of Water Masers)
   - assumption: equal beaming for the two lines and co-spatial masers  
  > "under the assumption of equal beaming for the two lines" (1.3 Millimetre Water Masers)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Self-calibration and imaging of ALMA data (tclean)  
  > "We then carried out phase-only self-calibration and imaging with the Common Astronomy Software Applications" (2.2 ALMA Band 7 Observations)
- **AIPS** : VERA data reduction and SAD spot fitting  
  > "The data were reduced with standard data-reduction procedures with the Astronomical Image Processing System (AIPS)" (2.1 VERA Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 321 GHz maser peak integrated flux | 27.3 | 0.17 | Jy | 2 | 27.3 (0.17) |
| 321 GHz maser brightness temperature lower limit | 3.2e4 | not stated | K | 2 | the lower limit of the brightness temperature for the 321 GHz emission is 3.2$\times 10^{4}$ K |
| 22 to 321 GHz flux ratio R in CM2-W2 | 2.1 | not stated | dimensionless | 3 | implying $R = F_{\rm 22}/F_{\rm 321} =  2.1$ |
| 321 GHz maser peak velocity | -7.75 | not stated | km/s | 2 | which peaks at $-7.75$ km s$^{-1}$ with an integrated flux of 27.3 Jy |

## Qualitative findings

- Mean proper motion speeds unchanged before and after burst (50±40 vs 54±42 km/s), so variability is excitation not ejecta  
  > "The mean speeds did not change with $\bar{v}_{\rm pre} = 50\pm40$ km s$^{-1}$ and $\bar{v}_{\rm burst} = 54\pm42$ km s$^{-1}$." (3.3 Pre-burst and Burst Proper Motions)

## Claim tuples

- H: CM2-W2 is excited by C-shocks | E: Combine 22 GHz JVLA flux with ALMA 321 GHz maser flux | R: R = 2.1 | F: CM2-W2 consistent with C-shock | **supported**
- H: Burst flare is due to excitation changes rather than jet ejecta | E: VERA proper motions pre-burst vs burst | R: Mean speeds unchanged | F: Excitation effects from variable radiation | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Background continuum increase and radiative (IR) pumping rejected for CM2-W2  
  > "It does not seem that an increase in the background continuum is responsible for the maser flare in CM2-W2." (4.3.1 Change in Background Continuum)
- How they decided it was enough: _not stated_
- Limitation (authors): Heating analysis is simple order-of-magnitude; detailed calculations left for future work  
  > "Our analysis here is relatively simple, and we leave more detailed calculations on each of the steps above for future work." (4.3.3 Radiative Heating of H2)
- Caveat (inferred, ours): Single 321 GHz feature and non-contemporaneous 22 GHz spot (2017.8 vs 2019.7) weakens R
- Caveat (inferred, ours): Absolute velocity frame assumption drives proper-motion speeds
- Caveat (inferred, ours): Heating estimate depends on unconstrained eta and density

## Reproducibility

- Data public (paper): ALMA project code given; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA$\#$2018.1.00024." (Acknowledgements)
- Products in archive: _not stated_
- Missing: VERA and HartRAO data availability
- Missing: CASA version
- Missing: self-calibration parameters
- Data volume (inferred): ALMA Band 7 single narrow spw, likely tens of GB raw
- Score (inferred): 3/5, ALMA part is a small, simply described piece; many parameters missing, and the main results come from VERA/HartRAO.
- Rediscovery candidate: no, ALMA recipe incomplete and main results rely on non-ALMA VLBI data.

## Links

- Companion: (cite: 2018ApJ...866...87B) (JVLA 22 GHz maser observations and association names)
- Companion: (cite: 2021ApJ...908..175C) (KaVA proper motions used for reference frame)
- Related: Maser Monitoring Organization

## Checks

```json
{
 "quotes": 48,
 "quotes_ok": 48,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 38,
  "rate": 0.576
 },
 "evidence_ok": true
}
```
