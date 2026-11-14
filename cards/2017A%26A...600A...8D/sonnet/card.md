# ALMA observations of 4U 1728-34 and 4U 1820-30: first detection of neutron star X-ray binaries at 300 GHz

`2017A&A...600A...8D` | Astronomy and Astrophysics 2017 | first author: Díaz Trigo, M. | arXiv: 1611.06988 | DOI: 10.1051/0004-6361/201629472

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: stellar_physics, milky_way_ism
- Question: How do jet properties (radio-to-mm spectrum and the optically thick/thin break) of two atoll neutron-star X-ray binaries relate to their hard/soft states, compared with black holes?  
  > "In this paper, we are interested in mapping the jet properties of NS XRBs to their “hard” and “soft” states" (Introduction)
- Target **4U 1728-34**: coordinates ALMA peak (J2000) 17:31:57.6757 -33:50:01.544  
  > "4U 1728$-$34 is a low-mass X-ray binary (LMXB) at a distance of 5.2 kpc (cite: galloway08apj)." (Introduction); z/distance 5.2 kpc  
  > "4U 1728$-$34 is a low-mass X-ray binary (LMXB) at a distance of 5.2 kpc (cite: galloway08apj)." (Introduction); distance from Galloway et al. 2008  
  > "4U 1728$-$34 is a low-mass X-ray binary (LMXB) at a distance of 5.2 kpc (cite: galloway08apj)." (Introduction)
- Target **4U 1820-30**: coordinates ALMA peak (J2000) 18:23:40.5050 -30:21:40.089  
  > "The distance derived from type I X-ray bursts is 6.4 kpc (cite: galloway08apj) and that derived from optical observations is 7.6 $\pm$ 0.4 kpc (cite: 1820:heasley00aj)." (Introduction); z/distance 6.4 kpc (X-ray bursts); 7.6 ± 0.4 kpc (optical)  
  > "The distance derived from type I X-ray bursts is 6.4 kpc (cite: galloway08apj) and that derived from optical observations is 7.6 $\pm$ 0.4 kpc (cite: 1820:heasley00aj)." (Introduction); distance from Galloway et al. 2008; Heasley et al. 2000  
  > "The distance derived from type I X-ray bursts is 6.4 kpc (cite: galloway08apj) and that derived from optical observations is 7.6 $\pm$ 0.4 kpc (cite: 1820:heasley00aj)." (Introduction)

## Data provenance

- ALMA projects: 2013.1.01013.S
- bands: ~300 GHz (302 GHz continuum)  
  > "ALMA 302 GHz" (Table 1)
- frequencies and spectral setup: four 2 GHz spectral windows centred at 295.987, 297.924, 306.002, 308.002 GHz; 31.2 MHz resolution  
  > "Both observations were set up to use four spectral windows with a bandwidth of 2 GHz each and centred at 295.987, 297.924, 306.002 and 308.002 GHz." (2.2 ALMA)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: maximum baseline 650 m, 31 and 33 12-m antennas  
  > "The observations were performed using 31 and 33 12-m antennas for 4U 1728$-$34 and 4U 1820$-$30, respectively, with a maximum baseline length of 650 m." (2.2 ALMA)
- angular resolution: 0.33"x0.29" (4U 1728-34); 0.34"x0.32" (4U 1820-30)  
  > "For 4U 1728$-$34 the synthesized beam size was 0.33$^{\prime\prime}$$\times$0.29$^{\prime\prime}$." (2.2 ALMA)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 2.8 ks (4U 1728-34), 2.9 ks (4U 1820-30)  
  > "ALMA 302 GHz | 2013.1.01013.S | 2.8" (Table 1)
- observing dates: 19 July 2014 (4U 1728-34); 7 July 2014 (4U 1820-30)  
  > "ALMA observed 4U 1728$-$34 on the 19th of July 2014 from 01:05 to 03:32 UTC and 4U 1820$-$30 on the 7th of July 2014 from 04:27 to 07:01 UTC." (2.2 ALMA)
- pi or archival as stated: _not stated_
- Other facility **ATCA**: 5.5 and 9.0 GHz radio flux densities  
  > "We used the Compact Array Broadband Backend (cite: Wilson2011) to observe simultaneously at 5.5 and 9.0 GHz" (2.1 ATCA)
- Other facility **VLT/HAWK-I**: J and Ks photometry of 4U 1728-34  
  > "4U 1728$-$34 was observed in the J and Ks bands with the High Acuity Wide field K-band Imager" (2.3 VLT)
- Other facility **Swift (XRT, BAT)**: X-ray fluxes and state determination  
  > "we determined the state of the source from those two $\it Swift/BAT$ observations." (Results)
- Other facility **HST**: archival F814W/F435W images for counterparts of extra ALMA sources  
  > "We searched for possible optical counterparts to the additional sources in NGC 6624 in *Hubble Space Telescope* (HST) images" (Discussion)
- External data: Deep ATCA 6 km-configuration model of NGC 6624 used to subtract compact sources  
  > "We therefore used a model made from deep images of NGC 6624 at the same observing frequencies (Tudor et al., in prep.)" (2.1 ATCA) [from Tudor et al., in prep.]
- External data: Hard/soft-state 15-50 keV flux thresholds from previous broad-band X-ray observations  
  > "we calculated the 15–50 keV fluxes typical of hard and soft states based on previous observations of the source with broad-band X-ray detectors" (Results) [from Falanga 2006; Tarana 2011; Seifina 2011 (cite: 1728:falanga06aa; 1728:tarana11mnras; 1728:seifina11apj)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: ALMA calibrated products used to regenerate images  
  > "We used the ALMA calibrated products to re-generate images following standard procedures." (2.2 ALMA)
- flux calibrator: Titan (4U 1728-34); J1924-2914 for all calibrations of 4U 1820-30  
  > "the bandpass, flux, and phase calibrators were J1733$-$1304, Titan, and J1744$-$3116, respectively." (2.2 ALMA)
- flux scale uncertainty: _not stated_
- self calibration: self-calibrated on a timescale of 1 hour  
  > "The images were self-calibrated on a timescale of 1 hour." (2.2 ALMA)

### Imaging

- task: CASA used for image generation and analysis  
  > "CASA was used for image generation and analysis." (2.2 ALMA)
- deconvolver: _not stated_
- weighting robust: uniform weighting, central frequency 301.99 GHz  
  > "extracted with uniform weighting and using a central frequency of 301.99 GHz" (2.2 ALMA)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: flux densities determined after primary beam correction  
  > "The flux densities and uncertainties were determined after correcting the maps for primary beam attenuation." (2.2 ALMA)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.33"x0.29" and 0.34"x0.32"  
  > "For 4U 1820$-$30 the synthesized beam size was 0.34$^{\prime\prime}$$\times$0.32$^{\prime\prime}$." (2.2 ALMA)
- final rms: _not stated_

### Inherited from earlier work

- ALMA new-source nomenclature  
  > "we name all the new sources according to the ALMA new source nomenclature at the ALMA Users’ Policies" (2.2 ALMA) [from ALMA Users’ Policies]
- Swift/XRT 3% systematic error  
  > "We fitted the 0.3–10 keV spectrum adding 3% systematic error as suggested by Beardmore et al. 2011" (2.5 Swift) [from Beardmore et al. 2011]

### Not stated but needed to reproduce (our reading)

- CASA version used for ALMA imaging
- tclean parameters: cell size, image size, deconvolver, masking, niter/threshold
- Self-calibration details beyond the 1 h solint
- Fitting method for spectral indices and the break (interpolation procedure)
- Which flux scale uncertainty was applied for ALMA
- Tudor et al. model for ATCA subtraction unavailable

## Analysis recipe

1. **Image ALMA continuum and measure flux**: Re-generate images from calibrated products, self-calibrate, primary-beam correct, fit elliptical Gaussian for peak flux  
  > "the reported flux density for all sources in this section corresponds to the peak flux from the elliptical Gaussian fitted to the source emission in the image plane" (2.2 ALMA)
   - software: CASA
   - parameter: uniform weighting; 301.99 GHz; self-cal 1 h  
  > "The images were self-calibrated on a timescale of 1 hour." (2.2 ALMA)
   - fitting: _not stated_
   - validation: error is rms far from the source  
  > "the error corresponds to the rms of the image measured far away from the source position" (2.2 ALMA)
2. **Determine X-ray spectral state**: Compare Swift/BAT 15-50 keV fluxes with typical hard/soft thresholds (1e-9 erg/cm2/s) and hardness ratio  
  > "We found values below 10$^{-9}$ erg cm$^{-2}$ s$^{-1}$ for the majority of soft state observations" (Results)
   - software: HEASOFT
   - assumption: power-law index 1 or 2 for BAT count-to-flux conversion  
  > "assuming a power law of index 2, and 8.7 $\times$ 10$^{-10}$ and 3.1 $\times$ 10$^{-10}$ erg cm$^{-2}$ s$^{-1}$ assuming a power law of index 1" (Results)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit radio-to-IR SED spectral indices and jet break**: Power-law fits F_nu ∝ nu^alpha to ATCA+ALMA(+IR) points; break from interpolation of thick and thin spectra  
  > "we obtain $\alpha$ = 0.28 $\pm$ 0.05 and a spectral break at $\sim$6 $(\pm$ 5)$\times$10$^{13}$ Hz, from interpolation between the optically thick and optically thin spectra." (Results)
   - fitting: _not stated_
   - validation: _not stated_
4. **Identify nature of additional ALMA sources**: HST counterpart search, isochrone masses (Dartmouth), chance-coincidence and background-source counts  
  > "we found that these counterparts correspond to main-sequence stars with masses of $\sim$0.63 M$_{\odot}$ and $\sim$0.43 M$_{\odot}$." (Discussion)
   - software: Dartmouth Stellar Evolution Program
   - assumption: age 10.6 Gyr, [Fe/H] = -0.69, [alpha/Fe]=0.4, distance modulus 14.63  
  > "assuming an age of 10.6 Gyr, a metallicity \[Fe/H\] = –0.69, enhancement \[$\alpha$/Fe\] = 0.4, and distance modulus \[M-m\]$_0$ = 14.63" (Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : ALMA imaging and analysis; ATCA imaging of 4U 1820-30  
  > "CASA was used for image generation and analysis." (2.2 ALMA)
- **MIRIAD** : ATCA data reduction  
  > "We reduced the data according to standard procedures in the Multichannel Image Reconstruction, Image Analysis and Display software package" (2.1 ATCA)
- **AIPS** : final ATCA imaging of 4U 1728-34  
  > "We therefore performed the final imaging and image-plane fitting using the Astronomical Image Processing System (cite: Greisen2003)" (2.1 ATCA)
- **HAWK-I pipeline / EsoRex** v1.8.18: VLT IR data reduction  
  > "The data were reduced with the dedicated HAWK-I pipeline (v1.8.18) provided by ESO and implemented in the EsoRex package." (2.3 VLT)
- **HEASOFT** v6.19: Swift/XRT analysis  
  > "we used HEASOFT v6.19 and the most recent calibration files" (2.4 Swift)
- **APLpy** : plotting  
  > "This research made use of APLpy, an open-source plotting package for Python" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 4U 1728-34 ALMA 302 GHz peak flux | 1.40 | 0.02 | mJy/beam | 1 | 4U 1728$-$34  / 17:31:57.6757 $\pm$ 0.0003 / -33:50:01.544 $\pm$ 0.005 / 1.40 $\pm$ 0.02 |
| 4U 1820-30 ALMA 302 GHz peak flux | 0.40 | 0.02 | mJy/beam | 1 | 4U 1820$-$30  / 18:23:40.5050 $\pm$ 0.0004 / -30:21:40.089 $\pm$ 0.005 / 0.40 $\pm$ 0.02 |
| 4U 1728-34 radio-IR spectral index (optically thick) | 0.28 | 0.05 | dimensionless | 3 | we obtain $\alpha$ = 0.28 $\pm$ 0.05 and a spectral break at $\sim$6 $(\pm$ 5)$\times$10$^{13}$ Hz |
| 4U 1728-34 jet break frequency | ~6e13 | ±5e13 | Hz | 3 | a spectral break at $\sim$6 $(\pm$ 5)$\times$10$^{13}$ Hz |
| 4U 1820-30 radio-mm spectral slope (5.5 and 302 GHz) | 0.13 | 0.04 | dimensionless | 3 | we obtain a spectral slope of 0.13 $\pm$ 0.04 |
| 4U 1820-30 ATCA 5.5 GHz flux | 236 | 27 | uJy/beam | 0 | with a flux density of $236\pm27$ $\mu$Jy beam$^{-1}$ |
| 4U 1728-34 ATCA 5.5 GHz flux | 424 | 22 | uJy/beam | 0 | $424\pm22$ and $587\pm38$ $\mu$Jy beam$^{-1}$ at 5.5 and 9.0 GHz |

## Qualitative findings

- 4U 1820-30 shows significant radio and mm emission during the soft state, unlike quenched BHs  
  > "The observations of 4U 1820$-$30 confirm the existence of significant emission in the radio and mm bands during the soft state for NSs" (Conclusions)

## Claim tuples

- H: Can ALMA detect NS XRBs at 300 GHz and constrain their jet break? | E: Quasi-simultaneous ATCA, ALMA, VLT, Swift SED of 4U 1728-34 | R: ALMA detection 1.40 mJy; break ~6e13 Hz | F: Break consistent with 4U 0614+091 though state likely transitional | **supported**
- H: Do NSs quench radio emission in the soft state? | E: Radio/mm observations of soft-state 4U 1820-30 | R: detections at 5.5 and 302 GHz, slope 0.13 | F: No quenching in the soft state | **supported**
- H: What are the extra ALMA sources in NGC 6624? | E: HST counterpart search and population arguments | R: counterparts are main-sequence stars but association problematic | F: Origin unresolved | **partially**

## Reasoning

- Why this data: Persistently accreting sources chosen for easier scheduling; 10^11 Hz crucial for break in soft states  
  > "they are persistently accreting, such that scheduling their observations is easier" (Introduction)
- Why this method: _not stated_
- Alternative: Pulsar PSR B1820-30A contamination at 5.5 GHz considered and judged negligible  
  > "the same spectral slope makes the contribution of the pulsar already negligible at 5.5 GHz" (Results)
- How they decided it was enough: _not stated_
- Limitation (authors): Observations not strictly simultaneous; 4U 1728-34 in transitional state  
  > "our observations at different frequencies are not strictly simultaneous." (Results)
- Caveat (inferred, ours): Break frequency rests on one IR/ALMA/ATCA SED with non-simultaneous data and large uncertainty
- Caveat (inferred, ours): Only a few SED points; no unified fitting method
- Caveat (inferred, ours): ATCA 9 GHz data for 4U 1820-30 poor, upper limit ad hoc

## Reproducibility

- Data public (paper): ALMA data identified by project code; calibrated archive products used  
  > "We used the ALMA calibrated products to re-generate images following standard procedures." (2.2 ALMA)
- Products in archive: _not stated_
- Missing: CASA version and tclean parameters
- Missing: ATCA data and Tudor et al. model
- Missing: Exact SED fitting procedure
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, ALMA data public and simple imaging, but few imaging parameters given and multi-facility data needed for SED.
- Rediscovery candidate: yes, Public ALMA data, simple point-source flux measurements with numeric results.

## Links

- Companion: Tudor et al., in prep. (ATCA deep model of NGC 6624)

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
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 47,
  "rate": 0.603
 },
 "evidence_ok": true
}
```
