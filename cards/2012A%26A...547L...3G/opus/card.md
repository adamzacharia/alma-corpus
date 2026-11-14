# ALMA and VLA observations of recombination lines and continuum toward the Becklin-Neugebauer object in Orion

`2012A&A...547L...3G` | Astronomy and Astrophysics 2012 | first author: Galván-Madrid, R. | arXiv: 1210.1413 | DOI: 10.1051/0004-6361/201220330

Card schema 1.0 | model claude-opus-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation
- Question: What do mm (H30α) and cm (H53α) recombination lines and mm/cm continuum reveal about the ionized gas, line-of-sight velocity and possible continuum variability of the BN object in Orion?  
  > "In particular, observing hydrogen recombination lines (RLs) can be used to obtain the line-of-sight velocities of the radio sources, which are needed to complement the proper-motion information." (Introduction); "By observing multiple RL transitions, hints to the structure of the ionized nebula can be obtained even in unresolved observations" (Introduction)
- Target **Becklin-Neugebauer (BN) object, Orion BN/KL**: coordinates pointing center 05h35m14.35s, -05d22m35.0s (J2000)  
  > "The pointing center was" (Data); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00009.SV
- bands: _not stated_
- frequencies and spectral setup: 20 spectral windows, 213.72-246.62 GHz, 0.488 MHz (~0.6 km/s) resolution  
  > "The data consisted of 20 different spectral windows covering the frequency range from 213.72 GHz to 246.62 GHz." (Data); "Each spectral window had a uniform spectral resolution of 0.488 MHz" (Data)
- continuum bandwidth: _not stated_
- arrays: 16 12-m antennas  
  > "The array used 16 12-m antennas in a compact configuration with baselines in the range of 15 k" (Data)
- configurations: compact configuration  
  > "The array used 16 12-m antennas in a compact configuration with baselines in the range of 15 k" (Data)
- baselines: 15 kλ to 269 kλ  
  > "The array used 16 12-m antennas in a compact configuration with baselines in the range of 15 k" (Data)
- angular resolution: HPBW = 1.3" x 0.6"  
  > "ALMA SV data, HPBW" (Table 2)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: ~15 minutes per spectral window  
  > "was observed for an on-source time of" (Data)
- observing dates: January 19, 2012  
  > "Orion BN/KL was observed on January 19, 2012 with ALMA as part of the SV program." (Data)
- pi or archival as stated: ALMA Science Verification archive data (calibrated visibilities released April 12, 2012)  
  > "In this paper we make use of the fully calibrated visibilities released on April 12, 2012." (Data)
- Line: H H30α (231.9009 GHz)
- Line: H H53α (42.95197 GHz)
- Other facility **VLA**: Archival H53α B-array data (project AR635) and 8.4 GHz A-configuration continuum epochs  
  > "B-array observations have been previously presented by (cite: rodriguez09b) (project AR635)." (Data); "Finally, several epochs of continuum observations at 8.4 GHz in the A configuration were processed using standard methods in the AIPS software." (Data)
- Other facility **SMA calibrator database**: Flux densities of J0607-085 used to check ALMA amplitude scale  
  > "reports flux densities for J0607–085 within ten days of the ALMA observation" (Data)
- External data: H53α spectrum/observations toward BN  
  > "B-array observations have been previously presented by (cite: rodriguez09b) (project AR635)." (Data) [from (cite: rodriguez09b)]
- External data: Four epochs of 3.6 cm VLA-A fluxes of BN  
  > "together with the four epochs reported by (cite: zapata04), also at 3.6 cm" (Continuum.) [from (cite: zapata04)]
- External data: OVRO 218 GHz flux of BN (150±50 mJy)  
  > "(from OVRO observations in 1993 and 1994) reported by (cite: plambeck95) and (cite: blake96)" (Continuum.) [from (cite: plambeck95; blake96)]
- External data: CARMA 231 GHz non-detection of BN (3σ ~34 mJy)  
  > "(cite: fs08) do not detect BN at 231 GHz down to a" (Continuum.) [from (cite: fs08)]
- External data: Tabulated non-LTE departure coefficients b_n, β_n  
  > "Using the tabulated values in the calculations of (cite: walmsley90)" (cm and (sub)mm recombination lines) [from (cite: walmsley90)]
- External data: BN stellar mass ≈10 Msun  
  > "The BN object is known to be a young star with a mass" (Discussion) [from (cite: rodriguez05)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 3.3.0 and 3.4.0  
  > "The processing was done in CASA versions 3.3.0 and 3.4.0." (Data)
- pipeline version: _not stated_
- archive products used as is: fully calibrated SV visibilities used  
  > "In this paper we make use of the fully calibrated visibilities released on April 12, 2012." (Data)
- flux calibrator: Callisto and Mars; phase calibrator J0607-085  
  > "The absolute amplitude scale was derived from observations of Callisto and Mars. The phase calibrator was J0607–085." (Data)
- flux scale uncertainty: ~10%  
  > "From this, we estimate that the amplitude scale of the ALMA observations is accurate to" (Data)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uv domain, linear spectral baseline fit to line-free channels in each spw  
  > "Continuum subtraction was done in the u-v domain by carefully selecting the line-free channels in each spectral window and fitting a linear spectral baseline." (Results)
- line free channels: _not stated_
- primary beam correction: maps not corrected; quoted fluxes corrected  
  > "We present maps that have not been corrected for primary beam attenuation. The corrected fluxes are quoted in the text and tables." (Results)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.3" x 0.6"  
  > "ALMA SV data, HPBW" (Table 2)
- final rms: ~3 mJy in >100 kλ map (x5 lower than full map, dynamic-range limited at ~10-15 mJy)  
  > "lower than in Fig. 1" (Continuum.); "The dynamic range in this image is determined by limitations in the u-v coverage" (Continuum.)

### Inherited from earlier work

- H53α VLA data and reduction  
  > "B-array observations have been previously presented by (cite: rodriguez09b) (project AR635)." (Data) [from (cite: rodriguez09b)]
- Combined Voigt linewidth formula  
  > "The line FWHM of the combined profile is given by (cite: gm09):" (Recombination lines) [from (cite: gm09)]
- Electron density from two-line RL analysis  
  > "Finally, using equation 3 of (cite: kzk08), the average electron density traced by these RLs is" (Recombination lines) [from (cite: kzk08)]
- Pressure broadening formulas  
  > "They produce a broadening of width (cite: smirnov84):" (Linewidth of recombination lines) [from (cite: gs02; smirnov84)]

### Not stated but needed to reproduce (our reading)

- Which channels were treated as line-free in each spw
- Weighting/robust, cell size, image size, clean thresholds and masks for ALMA images
- Exact aperture sizes/shapes used for flux and spectrum extraction
- Whether SV visibilities were self-calibrated
- VLA 8.4 GHz imaging parameters in AIPS
- Treatment/version of H53α spectrum taken from rodriguez09b
- T_e assumed when deriving N_e via kzk08 eq. 3

## Analysis recipe

1. **continuum subtraction and deep continuum image**: uv-plane linear continuum fit; co-add line-free visibilities of all spws  
  > "Figure [1](#f1_continuum) shows a deep continuum image from the ALMA data obtained by co-adding the line-free continuum visibilities from all spectral windows." (Continuum.)
   - software: CASA
   - parameter: average frequency 230.17 GHz (1.30 mm)  
  > "The average frequency (wavelength) in this map is 230.17 GHz (1.30 mm)." (Continuum.)
   - fitting: _not stated_
   - validation: continuum images from different spws consistent  
  > "Continuum images from different spectral windows are consistent with each other, indicating a low contamination from unaccounted line emission." (Results)
2. **isolate compact BN continuum with uv cut**: image with short baselines removed (minimum ~100 kλ), filter scales >1.4"  
  > "To disentangle the compact continuum emission from the extended emission in the field, we made cleaned maps after removing the short baselines." (Continuum.); "gives optimal results, filtering out the emission on scales" (Continuum.)
   - software: CASA
   - parameter: B_min = 100 kλ  
  > "The error is determined by variations in the obtained flux with different apertures in the" (Table 2)
   - fitting: _not stated_
   - validation: flux same within 20% regardless of uv restriction  
  > "regardless of the u-v coverage restriction applied" (Continuum.)
3. **test cm continuum variability**: reprocess archival VLA 8.4 GHz A-config epochs, compare with literature mm and cm fluxes  
  > "We have reprocessed three epochs of VLA archival data at 3.6 cm (8.4 GHz) to look for possible variations in the continuum emission from BN." (Continuum.)
   - software: AIPS
   - parameter: amplitude calibrator 1331+305 at 5.21 Jy  
  > "In all epochs 1331+305 was used as amplitude calibrator with an adopted flux density of 5.21 Jy." (Data)
   - fitting: _not stated_
   - validation: _not stated_
4. **extract and fit RL spectra**: Gaussian fits to H30α and H53α spectra in aperture matched to emitting area; H30α moment-0 from >100 kλ baselines  
  > "From Gaussian fits to the spectra shown in Fig. 3 using an aperture adjusted to the emitting area shown in Fig. 4." (Table 3); "Similar to the mm continuum, the H30$\alpha$ map uses only baselines with length" (Recombination lines)
   - software: CASA
   - fitting: Gaussian fit  
  > "From Gaussian fits to the spectra shown in Fig. 3" (Table 3)
   - validation: _not stated_
5. **linewidth decomposition: Te and bulk motions**: decompose FWHM into thermal, dynamical, pressure broadening (Voigt formula)  
  > "The total RL width ($\Delta v$) has contributions from thermal broadening" (Recombination lines)
   - assumption: pure hydrogen gas thermalized to T_e, microturbulence neglected  
  > "it is assumed that all the gas is thermalized to the electron temperature" (Linewidth of recombination lines)
   - fitting: _not stated_
   - validation: _not stated_
6. **derive electron density**: equation 3 of kzk08 using both RLs  
  > "Finally, using equation 3 of (cite: kzk08), the average electron density traced by these RLs is" (Recombination lines)
   - fitting: _not stated_
   - validation: _not stated_
7. **non-LTE and line-to-continuum check**: non-LTE correction with Walmsley (1990) b_n; compare H30α/H53α line-to-continuum ratios with LTE optically thin expectation  
  > "Under these assumptions, the expected ratio of the H30$\alpha$ to H$53\alpha$ line-to-continuum ratios is 6.4." (cm and (sub)mm recombination lines)
   - assumption: optically thin, Rayleigh-Jeans regime  
  > "Therefore, in the optically thin regime, the line-to-continuum ratio increases almost linearly with frequency" (cm and (sub)mm recombination lines)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 3.3.0 and 3.4.0: ALMA data processing  
  > "The processing was done in CASA versions 3.3.0 and 3.4.0." (Data)
- **AIPS** : VLA 8.4 GHz continuum processing  
  > "were processed using standard methods in the AIPS software" (Data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| BN 1.3 mm peak intensity (full uv) | 55 (112 pb-corrected) | not stated | mJy beam^-1 | 1 | we detect BN with a peak intensity of 55 mJy beam |
| BN 1.3 mm flux density in >100 kλ map, not pb-corrected | 62 | not stated | mJy | 2 | The 1.3-mm flux density of BN in this image is 62 mJy. |
| BN 1.3 mm flux density, pb-corrected | 126 | ±14 | mJy | 2 | After primary beam correction, the flux density of BN is |
| H30α vLSR of BN | 26.3 | ±0.5 | km s^-1 | 4 | the central line-of-sight LSR velocity of BN is 26.3 km s |
| H30α FWHM | 15.4 | ±1.3 | km s^-1 | 4 | this line appears to be too narrow (15.4 km s |
| H30α peak flux | 181 | ±14 | mJy | 4 | 231.9009 |
| H53α peak flux / vLSR / FWHM | 9.9 / 19.8 / 39.0 | ±1.1 / ±2.1 / ±5.0 | mJy / km s^-1 / km s^-1 | 4 | 42.95197 |
| Electron temperature upper limit | <4900 | not stated | K | 5 | is at most 4900 K, and the bulk gas motions are constrained to be much smaller than the thermal width |
| Electron density | 8.4e6 | not stated | cm^-3 | 6 | Finally, using equation 3 of (cite: kzk08), the average electron density traced by these RLs is |
| Observed ratio of H30α to H53α line-to-continuum ratios | 1.6 (expected 6.4) | not stated | dimensionless | 7 | However, the observed value is 1.6. |
| Free-free part of 1.3 mm continuum needed for expected ratio | ~32 | not stated | mJy | 7 | mJy of the 1.3-mm continuum are due to free-free then the line-to-continuum ratio would increase to the expected value |
| H53α gas blueshift relative to systemic | ~6.5 | not stated | km s^-1 | 4 | blueshifted with respect to the systemic |

## Qualitative findings

- First detection of mm RL emission toward BN; H30α not detected toward sources I and n  
  > "We report the first detection of mm RL emission toward the BN object." (Recombination lines)
- No molecular emission detected from BN  
  > "Also, no molecular emission was detected from BN." (Results)
- 3.6 cm flux of BN is stable; mm flux possibly variable  
  > "Based on this data set, the 3.6-cm flux is quite stable" (Continuum.); "It is possible that BN is variable in the (sub)mm continuum." (Continuum.)
- New faint compact mm source 4.3" south of BN  
  > "This newly detected source is possibly associated with the extended mid-infrared sources IRc6 and IRc6 N" (Continuum.)
- Dust may contribute significantly to the 1.3 mm continuum of BN  
  > "This suggests that dust contributes a significant fraction to the (sub)mm continuum of BN." (cm and (sub)mm recombination lines)

## Claim tuples

- H: H30α traces BN's stellar systemic velocity better than H53α | E: Gaussian fits to ALMA H30α and VLA H53α spectra | R: H30α narrower and redshifted relative to H53α; vLSR 26.3±0.5 km/s | F: H30α gives BN's line-of-sight velocity of 26.3 km/s | **supported**
- H: The mm RL arises from dense, slowly moving ionized gas | E: Linewidth decomposition and kzk08 density estimate | R: Te < 4900 K, bulk motions << thermal width, Ne = 8.4e6 cm^-3 | F: RL emission comes from dense static base of BN's ionized envelope | **supported**
- H: BN is variable in mm continuum | E: Compare ALMA 1.3 mm flux with OVRO/CARMA literature and VLA 3.6 cm epochs | R: 126 mJy vs 150±50 (OVRO) and <34 (CARMA); 3.6 cm stable within 30% | F: Possible mm variability, unconfirmed due to inhomogeneous setups | **partially**
- H: H53α traces outflowing gas | E: Compare H53α vs H30α velocities with optical depth interpretation | R: H53α blueshifted by ~6.5 km/s | F: H53α seems to trace gas outflowing toward us | **partially**

## Reasoning

- Why this data: mm RLs are brighter, optically thinner and free of pressure broadening; cm lines sensitive to density  
  > "However, longer wavelength lines are a valuable complement because they are sensitive to the gas density." (Introduction)
- Why this method: uv cut removes extended hot-core emission around BN  
  > "However, at the position of BN, where emission is fainter, the restricted u-v coverage effectively removes the extended emission around BN." (Continuum.)
- Alternative: Flux differences may be due to systematic calibration errors rather than variability; uv coverage effects judged unimportant  
  > "One possible explanation for the differences in the mm fluxes that have been reported for BN is that they are, at least partially, caused by systematic errors in the measurements." (Discussion)
- Alternative: Dust in a dense core around BN considered unlikely  
  > "Therefore, it is unlikely that this line-of-sight dust arises in a dense core around BN." (cm and (sub)mm recombination lines)
- How they decided it was enough: _not stated_
- Limitation (authors): Dynamic range limited by low declination, bright hot core and uv coverage  
  > "limit the dynamic range of synthesis imaging and complicate the detection of weak sources in this field at (sub)mm wavelengths" (Continuum.)
- Limitation (authors): Inhomogeneous mm observations limit variability test  
  > "However, the significance of these variations can be affected by the inhomogeneity of the mm observations." (Continuum.)
- Limitation (authors): Region near source I/HC unusable in uv-cut maps due to artifacts  
  > "we refrained from using this part of the image" (Continuum.)
- Caveat (inferred, ours): Comparison of ALMA and literature H53α measured in different apertures/beams
- Caveat (inferred, ours): Single ~15 min SV epoch; RL fit errors may underestimate systematics from nearby molecular lines
- Caveat (inferred, ours): Ne derivation depends on unstated Te and simplified model

## Reproducibility

- Data public (paper): ALMA SV data released publicly; VLA data archival  
  > "recently released Science Verification (SV) data" (Introduction)
- Products in archive: fully calibrated visibilities and a released continuum image  
  > "Our continuum map is" (Continuum.)
- Missing: Imaging parameters (weighting, cell, clean depth)
- Missing: Line-free channel ranges
- Missing: Extraction aperture definitions
- Missing: H53α data products from rodriguez09b
- Data volume (inferred): Few GB (16 antennas, 20 spw, ~15 min SV dataset)
- Score (inferred): 6/5, Public data and clear key choices (uv cut, Gaussian fits), but imaging settings, apertures and line-free channels unstated
- Rediscovery candidate: yes, Public SV data, simple recipe, numeric results (flux, vLSR, FWHM) reproducible approximately

## Links

- Method: (cite: kzk08) (Electron density equation and RL interpretation)
- Method: (cite: gm09) (Combined linewidth formula)
- Method: (cite: gs02) (RL physics, pressure broadening, non-LTE)
- Method: (cite: walmsley90) (Non-LTE departure coefficients)
- Companion: (cite: rodriguez09b) (H53α VLA observations of BN)
- Related: ALMA Science Verification Orion BN/KL

## Checks

```json
{
 "quotes": 90,
 "quotes_ok": 90,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 93,
  "stated": 61,
  "rate": 0.656
 },
 "evidence_ok": true
}
```
