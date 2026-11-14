# The evolving jet spectrum of the neutron star X-ray binary Aql X-1 in transitional states during its 2016 outburst

`2018A&A...616A..23D` | Astronomy and Astrophysics 2018 | first author: Díaz Trigo, M. | arXiv: 1804.08322 | DOI: 10.1051/0004-6361/201832693

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, transients
- Question: How does the optically thick-to-thin jet spectral break of the neutron star LMXB Aql X-1 evolve across state transitions in its 2016 outburst, and does it move to lower frequencies in softer states as in BH XRBs?  
  > "The goal was to study the behaviour of the jet break over the transitional states for the first time in a NS LMXB and to test the hypothesis that the jet break moves to lower frequencies" (1 Introduction)
- Target **Aql X-1**: coordinates 19:11:16.024 +00:35:05.900 (J2000, ALMA band 3 peak)  
  > "Its distance was determined from type I X-ray bursts to be 4.5–6 kpc" (1 Introduction); "The peak of radio emission is centred on average at (J2000) 19:11:16.024 $\pm$ 0.005 +00:35:05.900 $\pm$ 0.007" (2.2 ALMA); z/distance 5.2 kpc adopted (4.5–6 kpc)  
  > "Its distance was determined from type I X-ray bursts to be 4.5–6 kpc" (1 Introduction); "The peak of radio emission is centred on average at (J2000) 19:11:16.024 $\pm$ 0.005 +00:35:05.900 $\pm$ 0.007" (2.2 ALMA); distance from type I X-ray bursts (Jonker & Nelemans 2004)  
  > "Its distance was determined from type I X-ray bursts to be 4.5–6 kpc" (1 Introduction); "The peak of radio emission is centred on average at (J2000) 19:11:16.024 $\pm$ 0.005 +00:35:05.900 $\pm$ 0.007" (2.2 ALMA)

## Data provenance

- ALMA projects: 2015.1.00734.T
- bands: Band 3 (97.49 GHz) and Band 7 (302.99 GHz)  
  > "for the three observations in band 3 and at 295.99, 297.93, 307.99 and 309.99 GHz for the observations in band 7" (2.2 ALMA)
- frequencies and spectral setup: four spectral windows of 2 GHz each; 31.2 MHz resolution; band 3 centred 90.49, 92.43, 102.49, 104.49 GHz; band 7 centred 295.99, 297.93, 307.99, 309.99 GHz  
  > "All observations were set up to use four spectral windows, each with a bandwidth of 2 GHz." (2.2 ALMA); "The spectral resolution for each spectral window was 31.2 MHz." (2.2 ALMA)
- continuum bandwidth: _not stated_
- arrays: 12-m antennas, 38 to 46  
  > "The observations were performed using between 38 and 46 12-m antennas." (2.2 ALMA)
- configurations: _not stated_
- baselines: maximum baseline 1.4 km (August) and 3.1 km (September)  
  > "The maximum baseline length was 1.4 and 3.1 km, for the August and September observations, respectively." (2.2 ALMA)
- angular resolution: band 3 beams 0.46"x0.35" to 0.71"x0.50"; band 7 0.37"x0.33" to 0.58"x0.58"  
  > "At 97.49 GHz (band 3), the synthesised beam size was between 0.46$^{\prime\prime}$$\times$0.35$^{\prime\prime}$and 0.71$^{\prime\prime}$$\times$0.50$^{\prime\prime}$, depending on the epoch." (2.2 ALMA)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 3, 5, 7 Aug and 19-20 Sep 2016  
  > "ALMA 97.49 GHz   | 03 Aug 2016 01:39 | 03 Aug 2016 02:06" (Table 1)
- pi or archival as stated: _not stated_
- Other facility **ATCA**: 5.5 and 9 GHz radio flux densities  
  > "All observations were taken simultaneously in two 2-GHz frequency bands, centred at 5.5 and 9.0 GHz." (2.1 ATCA)
- Other facility **Swift/XRT and BAT, NuSTAR**: X-ray spectra and light curves for state classification  
  > "$\it Swift$/XRT observed Aql X–1 at numerous times during its 2016 outburst" (2.4 Swift and NuSTAR)
- Other facility **VLT/VISIR, SMARTS, Faulkes/LCO**: mid-IR, near-IR and optical photometry for SEDs  
  > "Mid-IR observations of the field of Aql X–1 were made with the VLT on the 3rd and 4th of August 2016" (2.3 VLT/SMARTS/LCO)
- External data: Suzaku spectra of 2011 outburst (periods P0, P9) for state comparison  
  > "we extracted the spectra from the $\it Suzaku$ X-ray Imaging Spectrometer (cite: Koyama2007) and the Hard X-ray Detector (cite: Takahashi2007) instruments corresponding to periods P0 and P9" (2.4 Swift and NuSTAR) [from Ono et al. 2017 (cite: aqlx1:ono17pasj)]
- External data: Hydrogen column density N_H = 4.4e21 cm-2 used for extinction  
  > "neutral hydrogen absorption column of $N{\rm _H^{abs}}$$= (4.4 \pm 0.1) \times 10^{21}$ cm$^{-2}$ measured by (cite: aql:Campana2014)" (2.3 VLT/SMARTS/LCO) [from Campana et al. 2014 (cite: aql:Campana2014)]

## Processing

### Calibration

- pipeline or manual: Band 7 data re-calibrated manually, flagging antennas with phase variability (beyond 260/400/400 m for obs 1, 2a, 3)  
  > "We re-calibrated the datasets for these observations flagging out the problematic antennas before re-generating the images." (2.2 ALMA)
- casa version: CASA v4.7  
  > "We re-generated images from the ALMA calibrated products following standard procedures with CASA v4.7." (2.2 ALMA)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: bandpass calibrator also flux calibrator (J1751+0939 or J1924-2914); J1733-1304 for second band 3 observation  
  > "The bandpass calibrator was also used as flux calibrator for all observations except the second band 3 observation, for which J1733-1304 was used." (2.2 ALMA)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust=0.5  
  > "extracted with Briggs weighting and robust=0.5 for all the observations" (2.2 ALMA)
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
- final beam: band 3: 0.46"x0.35" to 0.71"x0.50"; band 7: 0.37"x0.33" to 0.58"x0.58"  
  > "At 302.99 GHz (band 7), the synthesised beam size was between 0.37$^{\prime\prime}$$\times$0.33$^{\prime\prime}$ and 0.58$^{\prime\prime}$$\times$0.58$^{\prime\prime}$, depending on the epoch." (2.2 ALMA)
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- Cell size, image size, deconvolver, masking and clean threshold
- Which spectral windows/channels were combined for continuum images
- Exact flagging steps and antenna lists in re-calibration
- Whether flux calibrator models/absolute flux scale uncertainty were applied
- Fit weighting and points used for spectral slopes
- Parameter values imposed for obs 2a and 3 X-ray fits

## Analysis recipe

1. **Re-image ALMA data and measure flux densities**: Re-calibrated band 7 with problem antennas flagged, imaged with CASA, fitted elliptical Gaussian in image plane; error is image rms  
  > "The reported flux density for all sources in this section corresponds to the peak flux from the elliptical Gaussian fitted to the source emission in the image plane" (2.2 ALMA)
   - software: CASA
   - parameter: Briggs robust=0.5  
  > "extracted with Briggs weighting and robust=0.5 for all the observations" (2.2 ALMA)
   - fitting: _not stated_
   - validation: Re-calibrated images show point-like emission, flux densities increased by >~50%  
  > "These images show point-like source emission, similarly to the band 3 observations." (2.2 ALMA)
2. **Measure ATCA flux densities**: Subtract confusing source and field sources in uv-plane, fit target in uv-plane with uvmultifit  
  > "we adopted the values obtained with the second method (the $uv$-plane fitting)" (2.1 ATCA)
   - software: MIRIAD, CASA, uvmultifit
   - fitting: _not stated_
   - validation: Confusing source flux at 9 GHz consistent with VLA expectation; image-plane and uv-plane values broadly consistent  
  > "fully consistent with the 134 $\mu$Jy expected at 9 GHz from the measured VLA spectrum" (2.1 ATCA)
3. **Classify accretion state from X-ray spectra**: Fit Swift/XRT (and NuSTAR) spectra with tbabs*nthcomp(+diskbb, rfxconv), constrained by comparison with Suzaku spectra of previous outbursts  
  > "we used a basic model consisting of thermal Comptonisation absorbed from neutral material (`tbabs*nthcomp` in XSPEC) and, where necessary, we added a disc blackbody" (2.4 Swift and NuSTAR)
   - software: XSPEC
   - parameter: min 20 counts per bin; XRT 0.4–9 keV, NuSTAR 3–30 keV  
  > "used the 0.4–9 keV energy range for analysis" (2.4 Swift and NuSTAR)
   - assumption: 1.4 Msun neutron star, distance 5.2 kpc for Eddington fractions  
  > "the Eddington fraction during obs 2a/2b is $\sim$60–65% for a 1.4 M$_{\odot}$ neutron star" (3.1 Accretion state)
   - fitting: chi-square fitting with simultaneous fits and tied parameters  
  > "we can attempt to constrain the two-component models by fitting all the spectra simultaneously and linking the column density of the absorbing material, expected to be constant." (Observations and data analysis, Swift and NuSTAR)
   - validation: comparison with Suzaku P0/P9, HIDs  
  > "Our obs 1 perfectly matches the P0 interval" (2.4 Swift and NuSTAR)
4. **Fit radio-to-mm spectral slopes and break frequencies**: Power-law slopes F_nu ∝ nu^alpha before/after the break (first four/last three points for obs 1 and 3); upper limit on break from extrapolating thick spectrum to 200 and 250 GHz  
  > "we used the first four points/last three points to determine the spectral slope before/after the break" (3.2 Broad-band spectra)
   - fitting: _not stated_
   - validation: _not stated_
5. **Test correlation of break frequency with X-ray hardness/flux**: Spearman rank test of break frequency vs hardness ratio and MAXI/ASM count rate  
  > "While a Spearman rank test yields a positive correlation of 90$\%$ between the jet break frequency and the hardness of the X-ray spectrum" (4.2 Evolution of the jet spectral break along the outburst)
   - fitting: _not stated_
   - validation: chance probability >5% given 2 degrees of freedom  
  > "such a correlation still has a chance probability $>$ 5$\%$ given the low number of degrees of freedom (2)." (Discussion, Evolution of the jet spectral break along the outburst)

## Software

- **CASA** 4.7: ALMA imaging; ATCA imaging  
  > "following standard procedures with CASA v4.7" (2.2 ALMA)
- **MIRIAD** : ATCA data reduction  
  > "Data reduction was carried out using standard procedures within the Multichannel Image Reconstruction, Image Analysis and Display" (2.1 ATCA)
- **uvmultifit** : uv-plane flux fitting of ATCA data  
  > "directly fitting the target in the $uv$-plane using the uvmultifit algorithm" (2.1 ATCA)
- **XSPEC** 12.9.1: X-ray spectral fitting  
  > "performed using XSPEC (cite: arnaud96conf), version 12.9.1" (2.4 Swift and NuSTAR)
- **nustardas** 1.5.1: NuSTAR screening and products  
  > "We performed standard screening and filtering of the events using the $\it NuSTAR$ data analysis software (`nustardas`) version 1.5.1." (2.4 Swift and NuSTAR)
- **IRAF** : SMARTS reduction and LCO photometry (PHOT)  
  > "Photometry was performed using PHOT in IRAF." (2.3 VLT/SMARTS/LCO)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA 97.49 GHz peak flux density, obs 1 | 636 | 24 | uJy | 1 | the peak flux densities are 636 $\pm$ 24, 406 $\pm$ 26 and 753 $\pm$ 29 $\mu$Jy for epochs 1, 2b and 3, respectively |
| ALMA 302.99 GHz flux density, obs 1 and 3 | 532 and 598 | 42 and 63 | uJy | 1 | the peak flux density is 532 $\pm$ 42 and 598 $\pm$ 63 $\mu$Jy for obs 1 and 3, respectively |
| ALMA 302.99 GHz 3 sigma upper limit, obs 2a | <189 | not stated | uJy | 1 | the 3$\sigma$ upper limit is $<$ 189 $\mu$Jy |
| Spectral indices obs 1 (before/after break) | 0.11 and -0.15 | 0.06 each | dimensionless | 4 | we obtain indices of 0.11 $\pm$ 0.06 and –0.15 $\pm$ 0.06 before and after the break |
| Spectral indices obs 3 (before/after break at ~100 GHz) | 0.34 and -0.21 | 0.05 and 0.01 | dimensionless | 4 | for obs 3, we obtain indices of 0.34 $\pm$ 0.05 and -0.21 $\pm$ 0.01 |
| Spectral slope obs 2a (5.5 and 9 GHz) | -1.76 | 0.25 | dimensionless | 4 | For obs 2a we obtain a spectral slope of –1.76 $\pm$ 0.25 considering only the 5.5 and 9 GHz detections. |
| Upper limit on obs 1 break frequency | 250 | not stated | GHz | 4 | we set a conservative upper limit of 250 GHz for the break frequency |
| Eddington fraction obs 2a/2b | ~60–65% | not stated | percent | 3 | the Eddington fraction during obs 2a/2b is $\sim$60–65% for a 1.4 M$_{\odot}$ neutron star |

## Qualitative findings

- Radio and mm emission with negative spectral slope detected in the soft state at 60–65% Eddington, unlike earlier outbursts where radio was quenched  
  > "Our observations 2a and 2b demonstrate the existence of radio to mm emission with a negative slope after the source has transited into the soft state" (4.1 Jet emission during soft states)

## Claim tuples

- H: The jet break moves to lower frequencies as the NS evolves to softer states, as in BH MAXI J1836-194 | E: Quasi-simultaneous ATCA, ALMA and IR/X-ray SEDs at four epochs | R: Break ~100 GHz in hard/intermediate obs 1 and 3; below ~5 GHz in soft obs 2a/2b | F: Break frequency evolves with state in a NS as in BHs | **supported**
- H: Break frequency correlates with X-ray hardness | E: Spearman test with 4 epochs | R: 90% positive correlation, chance probability >5% | F: Possible but unconfirmed | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Observations not strictly simultaneous, spanning many hours across transitions; X-ray spectral model degeneracy  
  > "Besides the spectral degeneracy, a caveat to the classification above is that the multi-wavelength observations span several hours." (3.1 Accretion state)
- Caveat (inferred, ours): Only four epochs, so the correlation tests have ~2 degrees of freedom
- Caveat (inferred, ours): Break frequency in obs 1 and 3 poorly constrained, sparse points
- Caveat (inferred, ours): X-ray models for obs 2a and 3 were imposed rather than fitted

## Reproducibility

- Data public (paper): ALMA data cited by project code in acknowledgements  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00734.T." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging parameters (cell, size, masks)
- Missing: Details of flagging in re-calibration
- Missing: Fit procedure for spectral indices
- Data volume (inferred): ~50-100 GB for ALMA raw data across 6 observations
- Score (inferred): 3/5, Public ALMA data and clear numerical results, but imaging and re-calibration details are sparse.
- Rediscovery candidate: no, Re-calibration and slope fitting details are incomplete, and the multi-facility datasets (ATCA, Swift, VLT) are needed.

## Links

- Method: Díaz Trigo et al. 2017 (cite: 1820:diaz17aa) (Earlier exploratory ALMA study of NSs)
- Companion: Russell et al. (in preparation) (Full VISIR mid-IR to UV SED analysis)

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
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 42,
  "rate": 0.568
 },
 "evidence_ok": true
}
```
