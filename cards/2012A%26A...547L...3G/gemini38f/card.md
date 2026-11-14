# ALMA and VLA observations of recombination lines and continuum toward the Becklin-Neugebauer object in Orion

`2012A&A...547L...3G` | Astronomy and Astrophysics 2012 | first author: Galván-Madrid, R. | arXiv: 1210.1413 | DOI: 10.1051/0004-6361/201220330

Card schema 1.0 | model gemini-3.8-flash | depth full | type archival_reuse

## Science

- Fields: star_formation, milky_way_ism
- Question: What are the line-of-sight velocity, physical conditions, and continuum properties of the ionized gas around the Becklin-Neugebauer (BN) object in Orion using millimeter recombination lines and continuum?  
  > "We report observations of RLs (H30alpha at 231.9 GHz, H53alpha at 42.9 GHz) and the millimeter and centimeter continuum toward the Becklin-Neugebauer (BN) object in Orion" (abstract); "In particular, observing hydrogen recombination lines (RLs) can be used to obtain the line-of-sight velocities of the radio sources, which are needed to complement the proper-motion information." (Introduction)
- Target **Orion BN/KL**: coordinates 05h 35m 14.35s, -05d 22' 35.0"  
  > "The pointing center was alpha_J2000=05h 35m 14.35s, delta_J2000=-05d 22m 35.0s." (Data); z/distance _not stated_; distance from _not stated_
- Target **Becklin-Neugebauer (BN) object**: coordinates ~6.7" from the hot-core continuum peak  
  > "The BN object, as traced by its cm continuum, is ~6.7" from the hot-core continuum peak." (Continuum.); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00009.SV
- bands: Band 6 (~1.3 mm)  
  > "The average frequency (wavelength) in this map is 230.17 GHz (1.30 mm)." (Continuum.)
- frequencies and spectral setup: 20 spectral windows covering 213.72 GHz to 246.62 GHz with uniform resolution of 0.488 MHz (~0.6 km s^-1)  
  > "The data consisted of 20 different spectral windows covering the frequency range from 213.72 GHz to 246.62 GHz. Each spectral window had a uniform spectral resolution of 0.488 MHz (~0.6 km s^-1)" (Data)
- continuum bandwidth: _not stated_
- arrays: 16 12-m antennas  
  > "The array used 16 12-m antennas in a compact configuration with baselines in the range of 15 klambda to 269 klambda." (Data)
- configurations: compact configuration  
  > "The array used 16 12-m antennas in a compact configuration with baselines in the range of 15 klambda to 269 klambda." (Data)
- baselines: 15 klambda to 269 klambda  
  > "The array used 16 12-m antennas in a compact configuration with baselines in the range of 15 klambda to 269 klambda." (Data)
- angular resolution: 1.3" x 0.6"  
  > "ALMA SV data, HPBW=1.3" x 0.6" (this paper)." (Table 2)
- max recoverable scale: scales >1.4" filtered out with B_min=100 klambda  
  > "We found that a minimum baseline length of approx 100 klambda gives optimal results, filtering out the emission on scales >1.4"." (Continuum.)
- sensitivity: ~10 to 15 mJy in full map; ~3 mJy with B_min = 100 klambda  
  > "The dynamic range in this image is determined by limitations in the u-v coverage, and it is in the range of ~ 10 to 15 mJy." (Continuum.); "The noise is x 5 lower than in Fig. 1 (~ 3 mJy)." (Continuum.)
- time on source: ~15 minutes per spectral window  
  > "and was observed for an on-source time of ~ 15 minutes." (Data)
- observing dates: January 19, 2012  
  > "Orion BN/KL was observed on January 19, 2012 with ALMA as part of the SV program." (Data)
- pi or archival as stated: archival (SV program)  
  > "In this paper we make use of the fully calibrated visibilities released on April 12, 2012." (Data)
- Line: H 30alpha (231.9009 GHz)
- Line: H 53alpha (42.95197 GHz)
- Other facility **VLA**: Archival H53alpha B-array data (project AR635) and 8.4 GHz continuum A-array data across multiple epochs (1991, 2000, 2006)  
  > "We also present archival Very Large Array (VLA) data. The H53alpha (nu_0=42.95197 GHz) B-array observations have been previously presented by (cite: rodriguez09b) (project AR635)." (Data); "Finally, several epochs of continuum observations at 8.4 GHz in the A configuration were processed using standard methods in the AIPS software." (Data)
- Other facility **SMA**: Calibrator database flux densities for J0607-085  
  > "The SMA data base reports flux densities for J0607–085 within ten days of the ALMA observation: S_09Jan2012=1.25+-0.06 Jy, S_27Jan2012=1.37+-0.07 Jy." (Data)
- External data: VLA 8.4 GHz continuum flux measurements of BN from 1994 to 1997  
  > "VLA-A, HPBW~0.3" (cite: zapata04)." (Table 2) [from (cite: zapata04)]
- External data: OVRO 218 GHz continuum flux measurement from 1993-1994  
  > "OVRO observations at 218 GHz, HPBW=1.5" x 1.0" (cite: plambeck95; blake96)." (Table 2) [from (cite: plambeck95; blake96)]
- External data: CARMA 231 GHz continuum upper limit from March 2007  
  > "CARMA observations at 231 GHz, HPBW=2.5" x 0.8" (cite: fs08)." (Table 2) [from (cite: fs08)]
- External data: VLA H53alpha B-array data  
  > "The H53alpha (nu_0=42.95197 GHz) B-array observations have been previously presented by (cite: rodriguez09b) (project AR635)." (Data) [from (cite: rodriguez09b)]

## Processing

### Calibration

- pipeline or manual: fully calibrated visibilities released in SV program  
  > "In this paper we make use of the fully calibrated visibilities released on April 12, 2012." (Data)
- casa version: CASA versions 3.3.0 and 3.4.0  
  > "The processing was done in CASA versions 3.3.0 and 3.4.0." (Data)
- pipeline version: _not stated_
- archive products used as is: yes, fully calibrated visibilities  
  > "In this paper we make use of the fully calibrated visibilities released on April 12, 2012." (Data)
- flux calibrator: Callisto and Mars  
  > "The absolute amplitude scale was derived from observations of Callisto and Mars." (Data)
- flux scale uncertainty: ~10 %  
  > "From this, we estimate that the amplitude scale of the ALMA observations is accurate to ~ 10 %." (Data)
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
- continuum subtraction: in the u-v domain by selecting line-free channels and fitting a linear spectral baseline  
  > "Continuum subtraction was done in the u-v domain by carefully selecting the line-free channels in each spectral window and fitting a linear spectral baseline." (Results)
- line free channels: _not stated_
- primary beam correction: Maps presented are uncorrected; corrected fluxes quoted in text and tables  
  > "We present maps that have not been corrected for primary beam attenuation. The corrected fluxes are quoted in the text and tables." (Results)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.3" x 0.6"  
  > "ALMA SV data, HPBW=1.3" x 0.6" (this paper)." (Table 2)
- final rms: ~3 mJy with B_min=100 klambda; ~10 to 15 mJy full map  
  > "The noise is x 5 lower than in Fig. 1 (~ 3 mJy)." (Continuum.); "The dynamic range in this image is determined by limitations in the u-v coverage, and it is in the range of ~ 10 to 15 mJy." (Continuum.)

### Inherited from earlier work

- Formula for combining pressure, dynamical, and thermal line broadening  
  > "The line FWHM of the combined profile is given by (cite: gm09):" (Recombination lines) [from (cite: gm09)]
- Formula for deriving average electron density from RLs  
  > "Finally, using equation 3 of (cite: kzk08), the average electron density traced by these RLs is N_e=8.4x10^6 cm^-3." (Recombination lines) [from (cite: kzk08)]

### Not stated but needed to reproduce (our reading)

- Imaging weighting scheme and robust parameter in CASA
- Cell size and image size for CLEAN imaging
- Specific line-free channel ranges selected in each spectral window
- Aperture size and definition used for extracting spectra from BN

## Analysis recipe

1. **Subtract continuum and create continuum dataset**: Linear baseline fit to line-free channels in the u-v domain across all 20 spectral windows  
  > "Continuum subtraction was done in the u-v domain by carefully selecting the line-free channels in each spectral window and fitting a linear spectral baseline." (Results)
   - software: CASA
   - parameter: 20 spectral windows, average frequency 230.17 GHz  
  > "Figure 1 shows a deep continuum image from the ALMA data obtained by co-adding the line-free continuum visibilities from all spectral windows. The average frequency (wavelength) in this map is 230.17 GHz (1.30 mm)." (Continuum.)
   - assumption: Low contamination from unaccounted line emission across windows  
  > "Continuum images from different spectral windows are consistent with each other, indicating a low contamination from unaccounted line emission." (Results)
   - fitting: linear spectral baseline in u-v domain  
  > "fitting a linear spectral baseline." (Results)
   - validation: Consistency of continuum images from different spectral windows  
  > "Continuum images from different spectral windows are consistent with each other, indicating a low contamination from unaccounted line emission." (Results)
2. **Filter extended emission and image continuum around BN**: Deconvolution with clean after filtering out short baselines (< 100 klambda)  
  > "To disentangle the compact continuum emission from the extended emission in the field, we made cleaned maps after removing the short baselines." (Continuum.); "We found that a minimum baseline length of approx 100 klambda gives optimal results, filtering out the emission on scales >1.4"." (Continuum.)
   - software: CASA
   - parameter: B_min approx 100 klambda  
  > "We found that a minimum baseline length of approx 100 klambda gives optimal results, filtering out the emission on scales >1.4"." (Continuum.)
   - assumption: _not stated_
   - fitting: _not stated_
   - validation: Flux density is stable within 20% regardless of the uv coverage restriction applied  
  > "We note that the flux density for BN is the same, within 20 %, regardless of the u-v coverage restriction applied." (Continuum.)
3. **Extract spectra and fit recombination line profiles**: Gaussian profile fitting to line emission within an aperture adjusted to emitting area  
  > "From Gaussian fits to the spectra shown in Fig. 3 using an aperture adjusted to the emitting area shown in Fig. 4." (Table 3)
   - software: CASA
   - parameter: baselines > 100 klambda used for H30alpha  
  > "Similar to the mm continuum, the H30alpha map uses only baselines with length > 100 klambda." (Recombination lines)
   - assumption: _not stated_
   - fitting: Gaussian fit to peak flux, central velocity, and FWHM  
  > "From Gaussian fits to the spectra shown in Fig. 3 using an aperture adjusted to the emitting area shown in Fig. 4." (Table 3)
   - validation: _not stated_
4. **Derive physical conditions (electron temperature, density, bulk motions) from linewidths**: Deconvolving thermal, dynamical, and pressure broadening contributions using analytic formulae  
  > "The H30alpha line is only broadened thermally and by dynamical motions (Delta v_pr<0.6 km s^-1 from equation A.4)." (Recombination lines); "Therefore, for the gas traced by the H30alpha line, T_e is at most 4900 K, and the bulk gas motions are constrained to be much smaller than the thermal width. Finally, using equation 3 of (cite: kzk08), the average electron density traced by these RLs is N_e=8.4x10^6 cm^-3." (Recombination lines)
   - parameter: T_e <= 4900 K, N_e = 8.4 x 10^6 cm^-3  
  > "Therefore, for the gas traced by the H30alpha line, T_e is at most 4900 K, and the bulk gas motions are constrained to be much smaller than the thermal width. Finally, using equation 3 of (cite: kzk08), the average electron density traced by these RLs is N_e=8.4x10^6 cm^-3." (Recombination lines)
   - assumption: Pure hydrogen gas, close to LTE conditions  
  > "For a pure-hydrogen gas with T_e=9000 K, Delta v_th=20.3 km s^-1." (Linewidth of recombination lines); "As shown below, our simple LTE interpretation seems to be reasonable" (cm and (sub)mm recombination lines)
   - fitting: Analytic inversion from Voigt FWHM formula  
  > "The line FWHM of the combined profile is given by (cite: gm09):" (Recombination lines)
   - validation: Non-LTE calculations showing H30alpha line is amplified by only ~3% and H53alpha is even closer to LTE  
  > "Therefore, the intensity of the H30alpha line is only amplified by ~ 3 %. The H53alpha is even closer to LTE, with b_53 approx 0.999 and beta_53 ~ 0.5." (cm and (sub)mm recombination lines)

## Software

- **CASA** 3.3.0 and 3.4.0: Processing and imaging ALMA SV data  
  > "The processing was done in CASA versions 3.3.0 and 3.4.0." (Data)
- **AIPS** : Processing VLA 8.4 GHz continuum observations  
  > "Finally, several epochs of continuum observations at 8.4 GHz in the A configuration were processed using standard methods in the AIPS software." (Data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA 1.3-mm continuum flux density of BN (primary beam corrected) | 126 | 14 | mJy | 2 | 19 Jan 2012 / – / 126+-14 / e |
| ALMA 1.3-mm peak intensity of BN (uncorrected) | 55 | not stated | mJy beam^-1 | 2 | In the map shown in Fig. 1 we detect BN with a peak intensity of 55 mJy beam^-1 (112 mJy beam^-1 when primary beam attenuation is taken into account). |
| H30alpha peak flux density of BN | 181 | 14 | mJy | 3 | H30alpha / 231.9009 / 181+-14 / 26.3+-0.5 / 15.4+-1.3 |
| H30alpha peak LSR velocity of BN | 26.3 | 0.5 | km s^-1 | 3 | H30alpha / 231.9009 / 181+-14 / 26.3+-0.5 / 15.4+-1.3 |
| H30alpha FWHM linewidth of BN | 15.4 | 1.3 | km s^-1 | 3 | H30alpha / 231.9009 / 181+-14 / 26.3+-0.5 / 15.4+-1.3 |
| H53alpha peak flux density of BN | 9.9 | 1.1 | mJy | 3 | H53alpha / 42.95197 / 9.9+-1.1 / 19.8+-2.1 / 39.0+-5.0 |
| H53alpha peak LSR velocity of BN | 19.8 | 2.1 | km s^-1 | 3 | H53alpha / 42.95197 / 9.9+-1.1 / 19.8+-2.1 / 39.0+-5.0 |
| H53alpha FWHM linewidth of BN | 39.0 | 5.0 | km s^-1 | 3 | H53alpha / 42.95197 / 9.9+-1.1 / 19.8+-2.1 / 39.0+-5.0 |
| Derived electron density Ne | 8.4x10^6 | not stated | cm^-3 | 4 | Finally, using equation 3 of (cite: kzk08), the average electron density traced by these RLs is N_e=8.4x10^6 cm^-3. |
| Upper limit on electron temperature Te | 4900 | not stated | K | 4 | Therefore, for the gas traced by the H30alpha line, T_e is at most 4900 K, and the bulk gas motions are constrained to be much smaller than the thermal width. |

## Qualitative findings

- First detection of millimeter recombination line emission (H30alpha) toward the Becklin-Neugebauer object  
  > "We report the first detection of mm RL emission toward the BN object." (Recombination lines)
- The H30alpha line is narrower and redshifted relative to H53alpha, consistent with pressure broadening in H53alpha and optical depth effects in an outflowing ionized envelope  
  > "The H30alpha line is narrower than the H53alpha line, and it is redshifted by a few km s^-1. This behavior has been observed in hypercompact HII regions around embedded young massive stars" (Recombination lines)
- Millimeter continuum variations in BN are possible given historical CARMA non-detection, but multi-epoch observations with uniform setups are required to rule out systematic calibration and uv-coverage differences  
  > "One possible explanation for the differences in the mm fluxes that have been reported for BN is that they are, at least partially, caused by systematic errors in the measurements." (Discussion)

## Claim tuples

- H: Millimeter recombination line H30alpha traces the systemic line-of-sight velocity of the central star in the BN object better than centimeter lines | E: Measure and fit Gaussian line profiles to ALMA H30alpha and VLA H53alpha recombination line spectra toward BN | R: H30alpha has FWHM = 15.4 +- 1.3 km s^-1 and peak velocity v_LSR = 26.3 +- 0.5 km s^-1, narrower than H53alpha (39.0 +- 5.0 km s^-1) | F: H30alpha is virtually free of pressure broadening and traces the dense, static base of the ionized nebula, giving a systemic velocity v_LSR(BN) = 26.3 +- 0.5 km s^-1 | **supported**
- H: The ionized gas around BN has low bulk motion and moderate electron temperature | E: Analyze the narrow linewidth of H30alpha using standard broadening equations (thermal, dynamical, and pressure) | R: The total linewidth is 15.4 km s^-1, which is smaller than thermal width alone for Te = 10^4 K | F: The electron temperature is Te <= 4900 K, bulk motions are << 10 km s^-1, and average electron density is 8.4 x 10^6 cm^-3 | **supported**
- H: The Becklin-Neugebauer object exhibits millimeter continuum flux variability | E: Compare the ALMA 1.3-mm flux density (126 +- 14 mJy) with previous measurements from OVRO (150 +- 50 mJy) and CARMA (< 34 mJy), as well as multi-epoch VLA 3.6-cm fluxes | R: ALMA detects BN at 126 mJy, while CARMA previously reported a non-detection (< 34 mJy), but VLA 3.6-cm flux is stable within 30% | F: Millimeter continuum variations are possible, though systematic errors in calibration and inhomogeneous uv-coverage could also contribute | **partially**

## Reasoning

- Why this data: ALMA Science Verification data toward Orion BN/KL provide high sensitivity at 1.3 mm covering H30alpha to study recombination lines and continuum  
  > "In this paper we report our findings in the recently released Science Verification (SV) data taken toward Orion BN/KL with the Atacama Large Millimeter/submillimeter Array (ALMA)." (Introduction)
- Why this method: Excluding baselines shorter than 100 klambda filters out confusing extended emission from the hot core to isolate BN  
  > "We found that a minimum baseline length of approx 100 klambda gives optimal results, filtering out the emission on scales >1.4"." (Continuum.)
- Alternative: Considered using the full baseline range for imaging BN and H30alpha, but rejected for primary analysis because extended emission and sidelobes from the hot core create contamination  
  > "The H30alpha line is also detected in maps that use the complete baseline range, but bright molecular emission from the HC centered at ~ 10 MHz blueshifted with respect to the RL creates sidelobes that are for the most part removed by taking only the longest baselines." (Recombination lines)
- How they decided it was enough: _not stated_
- Limitation (authors): Dynamic range is limited by uv coverage limitations and bright extended hot core emission  
  > "The dynamic range in this image is determined by limitations in the u-v coverage, and it is in the range of ~ 10 to 15 mJy." (Continuum.)
- Limitation (authors): Flux variability cannot be definitively confirmed without dedicated multi-epoch observations with uniform setup  
  > "We emphasize that only dedicated multiepoch observations with a uniform setup can clarify this issue." (Discussion)

## Reproducibility

- Data public (paper): yes, ALMA SV public release  
  > "In this paper we make use of the fully calibrated visibilities released on April 12, 2012." (Data)
- Products in archive: yes, calibrated visibilities in ALMA Science Verification archive  
  > "obtained from the Atacama Large Millimeter/submillimeter Array (ALMA) Science Verification archive and the Very Large Array (VLA)." (abstract)
- Missing: Exact uv-baseline weighting parameters and CLEAN imaging parameters (robust value, threshold, iterations, pixel size) in CASA
- Missing: List of exact channel numbers used as line-free continuum channels in each spectral window
- Missing: Specific aperture region definition used to extract the 1D spectrum of BN
- Data volume (inferred): 10-30 GB
- Score (inferred): 7/5, The paper uses publicly available ALMA Science Verification data and well-described filtering criteria (baselines > 100 klambda). The steps from visibilities to spectra and continuum measurements are straightforward, though exact imaging parameters and channel masks are omitted.
- Rediscovery candidate: yes, ALMA SV data are public, baseline cutoff is explicitly specified (100 klambda), and key numerical line properties and continuum fluxes are well-defined.

## Links

- Method: (cite: gm09) (Voigt linewidth approximation formula combining thermal, dynamical, and pressure broadening)
- Method: (cite: kzk08) (Formula relating RL parameters to electron density)
- Companion: (cite: rodriguez09b) (Reports the VLA H53alpha observation and analysis for the BN object)
- Related: ALMA Science Verification

## Checks

```json
{
 "quotes": 84,
 "quotes_ok": 42,
 "quote_pass_rate": 0.5,
 "quotes_too_long": 3,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 59,
  "rate": 0.72
 },
 "evidence_ok": false
}
```
