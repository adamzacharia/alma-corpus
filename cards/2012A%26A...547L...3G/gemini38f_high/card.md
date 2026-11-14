# ALMA and VLA observations of recombination lines and continuum toward the Becklin-Neugebauer object in Orion

`2012A&A...547L...3G` | Astronomy and Astrophysics 2012 | first author: Galván-Madrid, R. | arXiv: 1210.1413 | DOI: 10.1051/0004-6361/201220330

Card schema 1.0 | model gemini-3.8-flash | depth full | type archival_reuse

## Science

- Fields: star_formation, milky_way_ism
- Question: What is the systemic line-of-sight velocity of the Becklin-Neugebauer (BN) object, what are the physical properties and kinematics of its ionized envelope, and does it exhibit continuum variability at millimeter wavelengths?  
  > "In particular, observing hydrogen recombination lines (RLs) can be used to obtain the line-of-sight velocities of the radio sources, which are needed to complement the proper-motion information." (Introduction); "In this paper we report our findings in the recently released Science Verification (SV) data taken toward Orion BN/KL with the Atacama Large Millimeter/submillimeter Array (ALMA)." (Introduction)
- Target **Becklin-Neugebauer (BN) object**: coordinates pointing center: 05h 35m 14.35s, -05d 22' 35.0''  
  > "The pointing center was $\alpha_\mathrm{J2000}=05^\mathrm{h}~35^\mathrm{m}~14\rlap.{^\mathrm{s}}35$, $\delta_\mathrm{J2000}=-05^\circ~22'~35\rlap.{''}0$." (Data); "The BN object, as traced by its cm continuum, is $\sim 6\rlap.{''}7$ from the hot-core continuum peak." (Continuum.); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00009.SV
- bands: Band 6 (1.3 mm)  
  > "The data consisted of 20 different spectral windows covering the frequency range from 213.72 GHz to 246.62 GHz." (Data); "The average frequency (wavelength) in this map is 230.17 GHz (1.30 mm)." (Continuum.)
- frequencies and spectral setup: 20 spectral windows covering 213.72 GHz to 246.62 GHz, uniform spectral resolution of 0.488 MHz (~0.6 km s^-1)  
  > "The data consisted of 20 different spectral windows covering the frequency range from 213.72 GHz to 246.62 GHz. Each spectral window had a uniform spectral resolution of 0.488 MHz ($\sim0.6$ km s$^{-1}$)" (Data)
- continuum bandwidth: _not stated_
- arrays: 16 12-m antennas  
  > "The array used 16 12-m antennas in a compact configuration with baselines in the range of 15 k$\lambda$ to 269 k$\lambda$." (Data)
- configurations: compact configuration  
  > "The array used 16 12-m antennas in a compact configuration with baselines in the range of 15 k$\lambda$ to 269 k$\lambda$." (Data)
- baselines: 15 klambda to 269 klambda  
  > "with baselines in the range of 15 k$\lambda$ to 269 k$\lambda$." (Data)
- angular resolution: 1.3'' x 0.6''  
  > "ALMA SV data, HPBW$\approx1\rlap.{''}3 \times 0\rlap.{''}6$ (this paper)." (Table 2)
- max recoverable scale: > 1.4'' (filtered out with B_min ~ 100 klambda)  
  > "We found that a minimum baseline length of $\approx 100$ k$\lambda$ gives optimal results, filtering out the emission on scales $>1\rlap.{''}4$." (Continuum.)
- sensitivity: ~3 mJy  
  > "The noise is $\times 5$ lower than in Fig. 1 ($\sim 3$ mJy)." (Continuum.)
- time on source: ~15 minutes  
  > "was observed for an on-source time of $\sim 15$ minutes." (Data)
- observing dates: January 19, 2012  
  > "Orion BN/KL was observed on January 19, 2012 with ALMA as part of the SV program." (Data)
- pi or archival as stated: archival (Science Verification release)  
  > "In this paper we make use of the fully calibrated visibilities released on April 12, 2012." (Data)
- Line: H 30alpha (231.9009 GHz)
- Line: H 53alpha (42.95197 GHz)
- Other facility **Very Large Array (VLA)**: Archival H53alpha B-array observations (project AR635) and multi-epoch 8.4 GHz continuum observations in A configuration  
  > "We also present archival Very Large Array (VLA) data. The H$53\alpha$ ($\nu_0=42.95197$ GHz) B-array observations have been previously presented by (cite: rodriguez09b) (project AR635)." (Data); "Finally, several epochs of continuum observations at 8.4 GHz in the A configuration were processed using standard methods in the AIPS software." (Data)
- External data: Phase calibrator J0607-085 flux densities within ten days of the ALMA observation  
  > "The SMA data base reports flux densities for J0607–085 within ten days of the ALMA observation: $S_\mathrm{09Jan2012}=1.25\pm0.06$ Jy, $S_\mathrm{27Jan2012}=1.37\pm0.07$ Jy." (Data) [from SMA data base]
- External data: OVRO 218 GHz continuum flux density of BN (150 +/- 50 mJy)  
  > "OVRO observations at 218 GHz, HPBW$=1\rlap.{''}5 \times 1\rlap.{''}0$ (cite: plambeck95; blake96)." (Table 2) [from (cite: plambeck95; blake96)]
- External data: CARMA 231 GHz continuum upper limit of BN (< 34 mJy)  
  > "CARMA observations at 231 GHz, HPBW$=2\rlap.{''}5 \times 0\rlap.{''}8$ (cite: fs08)." (Table 2) [from (cite: fs08)]
- External data: VLA A-configuration 3.6-cm continuum flux densities from 1994 to 1997  
  > "VLA-A, HPBW$\approx0\rlap.{''}3$ (cite: zapata04)." (Table 2) [from (cite: zapata04)]
- External data: VLA B-array H53alpha spectral data toward BN  
  > "The H$53\alpha$ ($\nu_0=42.95197$ GHz) B-array observations have been previously presented by (cite: rodriguez09b) (project AR635)." (Data) [from (cite: rodriguez09b)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: 3.3.0 and 3.4.0  
  > "The processing was done in CASA versions 3.3.0 and 3.4.0." (Data)
- pipeline version: _not stated_
- archive products used as is: yes (fully calibrated visibilities released by ALMA SV used directly)  
  > "In this paper we make use of the fully calibrated visibilities released on April 12, 2012." (Data)
- flux calibrator: Callisto and Mars  
  > "The absolute amplitude scale was derived from observations of Callisto and Mars." (Data)
- flux scale uncertainty: ~10 %  
  > "From this, we estimate that the amplitude scale of the ALMA observations is accurate to $\sim 10~\%$." (Data)
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
- continuum subtraction: linear spectral baseline fitted in the u-v domain using carefully selected line-free channels  
  > "Continuum subtraction was done in the u-v domain by carefully selecting the line-free channels in each spectral window and fitting a linear spectral baseline." (Results)
- line free channels: _not stated_
- primary beam correction: Maps presented without primary beam correction; corrected flux densities quoted in text and tables  
  > "We present maps that have not been corrected for primary beam attenuation. The corrected fluxes are quoted in the text and tables." (Results)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.3'' x 0.6''  
  > "ALMA SV data, HPBW$\approx1\rlap.{''}3 \times 0\rlap.{''}6$ (this paper)." (Table 2)
- final rms: ~3 mJy  
  > "The noise is $\times 5$ lower than in Fig. 1 ($\sim 3$ mJy)." (Continuum.)

### Inherited from earlier work

- Formula for deriving electron density from recombination lines (equation 3)  
  > "Finally, using equation 3 of (cite: kzk08), the average electron density traced by these RLs is $N_e=8.4\times10^6$ cm$^{-3}$." (Recombination lines) [from (cite: kzk08)]
- Combined profile linewidth equation relating thermal, dynamical, and pressure broadening  
  > "The line FWHM of the combined profile is given by (cite: gm09):" (Recombination lines) [from (cite: gm09)]
- Non-LTE departure coefficients b_n and beta_n for hydrogen recombination lines  
  > "Using the tabulated values in the calculations of (cite: walmsley90), $b_{30}\approx 0.98$ and $\beta_{30} \sim -1.5$ for a density $N_e=10^7$ cm$^{-3}$." (cm and (sub)mm recombination lines) [from (cite: walmsley90)]

### Not stated but needed to reproduce (our reading)

- CASA task (clean) weighting scheme and robust parameter value used for imaging.
- Cell size and image pixel dimensions.
- Exact channel ranges designated as line-free across each of the 20 spectral windows.
- Aperture size, position, and shape used for spectral extraction and flux density integration of BN.

## Analysis recipe

1. **Continuum subtraction in visibility space**: Identified line-free channels in each spectral window and fitted a linear baseline to visibilities in the u-v domain  
  > "Continuum subtraction was done in the u-v domain by carefully selecting the line-free channels in each spectral window and fitting a linear spectral baseline." (Results)
   - software: CASA
   - parameter: linear spectral baseline fit across 20 spectral windows  
  > "Continuum subtraction was done in the u-v domain by carefully selecting the line-free channels in each spectral window and fitting a linear spectral baseline." (Results)
   - assumption: Line contamination is low in selected channels across spectral windows  
  > "Continuum images from different spectral windows are consistent with each other, indicating a low contamination from unaccounted line emission." (Results)
   - fitting: linear spectral baseline fit to visibilities  
  > "fitting a linear spectral baseline." (Results)
   - validation: Consistency check of continuum images from different spectral windows  
  > "Continuum images from different spectral windows are consistent with each other, indicating a low contamination from unaccounted line emission." (Results)
2. **Continuum imaging and baseline filtering**: Co-added line-free continuum visibilities across all spectral windows and imaged with a minimum baseline length cutoff (B_min ~ 100 klambda) to filter extended emission  
  > "Figure 1 shows a deep continuum image from the ALMA data obtained by co-adding the line-free continuum visibilities from all spectral windows." (Continuum.); "We found that a minimum baseline length of $\approx 100$ k$\lambda$ gives optimal results, filtering out the emission on scales $>1\rlap.{''}4$." (Continuum.)
   - software: CASA
   - parameter: B_min = 100 klambda; average frequency 230.17 GHz (1.30 mm)  
  > "The average frequency (wavelength) in this map is 230.17 GHz (1.30 mm)." (Continuum.); "We found that a minimum baseline length of $\approx 100$ k$\lambda$ gives optimal results, filtering out the emission on scales $>1\rlap.{''}4$." (Continuum.)
   - assumption: Emission from BN is compact (< 1'') so short-baseline filtering does not resolve out source flux  
  > "Differences in u-v coverage may also mimic flux variations, but since the continuum emission from BN is less than one arcsecond in size, this effect should not be important." (Discussion)
   - fitting: CLEAN deconvolution  
  > "To disentangle the compact continuum emission from the extended emission in the field, we made cleaned maps after removing the short baselines." (Continuum.)
   - validation: Flux recovery was tested across different u-v restrictions and stayed within 20%  
  > "We note that the flux density for BN is the same, within $20~\%$, regardless of the u-v coverage restriction applied." (Continuum.)
3. **Recombination line spectral cube imaging**: Imaged the H30alpha line using baselines > 100 klambda to remove bright molecular line sidelobes from the Orion Hot Core  
  > "Similar to the mm continuum, the H30$\alpha$ map uses only baselines with length $> 100$ k$\lambda$" (Recombination lines)
   - software: CASA
   - parameter: B_min > 100 klambda, spectral resolution 0.488 MHz (~0.6 km s^-1)  
  > "Each spectral window had a uniform spectral resolution of 0.488 MHz ($\sim0.6$ km s$^{-1}$)" (Data); "Similar to the mm continuum, the H30$\alpha$ map uses only baselines with length $> 100$ k$\lambda$" (Recombination lines)
   - assumption: H30alpha emission from BN is sufficiently compact to be preserved after removing baselines < 100 klambda  
  > "The H30$\alpha$ line is also detected in maps that use the complete baseline range, but bright molecular emission from the HC centered at $\sim 10$ MHz blueshifted with respect to the RL creates sidelobes that are for the most part removed by taking only the longest baselines." (Recombination lines)
   - fitting: CLEAN imaging and moment-0 map generation  
  > "Figure 4 shows the velocity-integrated intensity maps (moment 0) for both lines." (Recombination lines)
   - validation: Detection confirmed in maps using the full baseline range  
  > "The H30$\alpha$ line is also detected in maps that use the complete baseline range" (Recombination lines)
4. **Extract spectra and fit Gaussian line profiles**: Extracted spectrum using an aperture adjusted to the moment-0 emitting area and fitted Gaussian components to measure line parameters  
  > "From Gaussian fits to the spectra shown in Fig. 3 using an aperture adjusted to the emitting area shown in Fig. 4." (Table 3)
   - software: CASA
   - parameter: aperture adjusted to the moment 0 emitting area  
  > "From Gaussian fits to the spectra shown in Fig. 3 using an aperture adjusted to the emitting area shown in Fig. 4." (Table 3)
   - assumption: Gaussian profile provides an adequate fit to the line core  
  > "From Gaussian fits to the spectra shown in Fig. 3 using an aperture adjusted to the emitting area shown in Fig. 4." (Table 3)
   - fitting: Gaussian profile fitting to spectrum  
  > "From Gaussian fits to the spectra shown in Fig. 3 using an aperture adjusted to the emitting area shown in Fig. 4." (Table 3)
   - validation: Comparison between H30alpha and archival VLA H53alpha line profiles  
  > "Figure 3 shows the H30$\alpha$ and the H53$\alpha$ (cite: rodriguez09b) spectra toward BN. The line parameters are summarized in Table 3." (Recombination lines)
5. **Constrain gas physical parameters and kinematics**: Decomposed line broadening into thermal, dynamical, and pressure mechanisms using Voigt profile approximation and analytical formulas to deduce electron temperature, electron density, and bulk motion limits  
  > "The line FWHM of the combined profile is given by (cite: gm09):" (Recombination lines); "Finally, using equation 3 of (cite: kzk08), the average electron density traced by these RLs is $N_e=8.4\times10^6$ cm$^{-3}$." (Recombination lines)
   - software: not stated
   - parameter: Delta v_pr < 0.6 km s^-1 for H30alpha; N_e = 8.4 x 10^6 cm^-3; T_e < 4900 K  
  > "The H30$\alpha$ line is only broadened thermally and by dynamical motions ($\Delta v_\mathrm{pr}<0.6$ km s$^{-1}$ from equation A.4)." (Recombination lines); "Therefore, for the gas traced by the H30$\alpha$ line, $T_e$ is at most 4900 K, and the bulk gas motions are constrained to be much smaller than the thermal width. Finally, using equation 3 of (cite: kzk08), the average electron density traced by these RLs is $N_e=8.4\times10^6$ cm$^{-3}$." (Recombination lines)
   - assumption: H30alpha is virtually free from pressure broadening and dominated by thermal and small dynamical motions  
  > "The H30$\alpha$ line is only broadened thermally and by dynamical motions ($\Delta v_\mathrm{pr}<0.6$ km s$^{-1}$ from equation A.4)." (Recombination lines)
   - fitting: Analytic evaluation of Voigt FWHM combination equation and non-LTE departure models  
  > "The line FWHM of the combined profile is given by (cite: gm09):" (Recombination lines)
   - validation: Comparison of observed line-to-continuum ratio between H30alpha and H53alpha against LTE predictions  
  > "Under these assumptions, the expected ratio of the H30$\alpha$ to H$53\alpha$ line-to-continuum ratios is 6.4. However, the observed value is 1.6." (cm and (sub)mm recombination lines)

## Software

- **CASA** 3.3.0 and 3.4.0: Processing ALMA visibilities, continuum subtraction, imaging, and Gaussian fitting  
  > "The processing was done in CASA versions 3.3.0 and 3.4.0." (Data)
- **AIPS** : Processing VLA 8.4 GHz continuum observations  
  > "Finally, several epochs of continuum observations at 8.4 GHz in the A configuration were processed using standard methods in the AIPS software." (Data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| H30alpha peak flux density | 181 | 14 | mJy | 4 | H$30\alpha$ / 231.9009 / $181\pm14$ / $26.3\pm0.5$ / $15.4\pm1.3$ |
| H30alpha peak LSR velocity | 26.3 | 0.5 | km s^-1 | 4 | H$30\alpha$ / 231.9009 / $181\pm14$ / $26.3\pm0.5$ / $15.4\pm1.3$ |
| H30alpha FWHM | 15.4 | 1.3 | km s^-1 | 4 | H$30\alpha$ / 231.9009 / $181\pm14$ / $26.3\pm0.5$ / $15.4\pm1.3$ |
| H53alpha peak flux density | 9.9 | 1.1 | mJy | 4 | H$53\alpha$ / 42.95197 / $9.9\pm1.1$ / $19.8\pm2.1$ / $39.0\pm5.0$ |
| H53alpha peak LSR velocity | 19.8 | 2.1 | km s^-1 | 4 | H$53\alpha$ / 42.95197 / $9.9\pm1.1$ / $19.8\pm2.1$ / $39.0\pm5.0$ |
| H53alpha FWHM | 39.0 | 5.0 | km s^-1 | 4 | H$53\alpha$ / 42.95197 / $9.9\pm1.1$ / $19.8\pm2.1$ / $39.0\pm5.0$ |
| BN 1.3-mm flux density (primary beam corrected) | 126 | 14 | mJy | 2 | 19 Jan 2012 / – / $126\pm14$ |
| Average electron density Ne | 8.4e6 | not stated | cm^-3 | 5 | Finally, using equation 3 of (cite: kzk08), the average electron density traced by these RLs is $N_e=8.4\times10^6$ cm$^{-3}$. |
| Electron temperature upper limit | 4900 | not stated | K | 5 | Therefore, for the gas traced by the H30$\alpha$ line, $T_e$ is at most 4900 K |

## Qualitative findings

- First detection of millimeter recombination line emission (H30alpha) toward the BN object.  
  > "We report the first detection of mm RL emission toward the BN object." (Recombination lines)
- H30alpha emission was not detected toward other radio sources in the field (source I and source n), largely due to line contamination from the Orion Hot Core.  
  > "We also searched for H$30\alpha$ emission in the rest of the Orion BN/KL field, in particular from sources I and n, without success." (Recombination lines)
- The millimeter RL arises from a dense, static base of the ionized envelope, whereas the centimeter line (H53alpha) traces an outflowing component.  
  > "The mm RL appears to be arising from the dense ($N_e=8.4\times10^6$ cm$^{-3}$), static (bulk motions $<<10$ km s$^{-1}$) base of the ionized nebula around the central massive star in BN" (Conclusions); "Compared to the H$30\alpha$ line, the optically thicker H$53\alpha$ seems to trace gas outflowing toward us at $\sim 6.5$ km s$^{-1}$." (Conclusions)
- A significant fraction of the 1.3 mm continuum of BN may originate from line-of-sight dust emission.  
  > "This suggests that dust contributes a significant fraction to the (sub)mm continuum of BN." (cm and (sub)mm recombination lines)

## Claim tuples

- H: Millimeter recombination lines can reliably determine the line-of-sight systemic velocity of the central star in BN. | E: Observed the H30alpha line at 231.9 GHz with ALMA SV data, filtering short baselines to remove extended hot-core sidelobes, and compared its profile with the VLA H53alpha line. | R: H30alpha is detected with v_LSR = 26.3 +/- 0.5 km s^-1 and FWHM = 15.4 +/- 1.3 km s^-1, narrower than H53alpha and redshifted by ~6.5 km s^-1. | F: Because H30alpha is optically thinner and unaffected by pressure broadening, it provides the systemic line-of-sight velocity of BN as v_LSR = 26.3 km s^-1. | **supported**
- H: The ionized gas around BN is characterized by high electron density, low electron temperature, and quiescent base kinematics. | E: Decomposed the H30alpha and H53alpha linewidths and intensity ratios into thermal, pressure, and dynamical components using standard recombination line formulas. | R: The narrow H30alpha linewidth constrains Te < 4900 K and dynamical bulk motions << 10 km s^-1, while H53alpha broadening yields an average electron density Ne = 8.4 x 10^6 cm^-3. | F: The mm recombination line arises from the dense, gravitationally confined base of the ionized envelope around the central ~10 M_sun star. | **supported**
- H: The Becklin-Neugebauer object is variable in the millimeter continuum. | E: Compared the ALMA 1.3 mm flux density (126 +/- 14 mJy) with historical OVRO (150 +/- 50 mJy) and CARMA (< 34 mJy) measurements, alongside multi-epoch VLA 8.4 GHz continuum data. | R: While the 8.4 GHz cm flux is stable within 30%, the CARMA non-detection differs significantly from ALMA and OVRO detections. | F: BN may exhibit large millimeter flux variations, but systematic errors in mm calibration and inhomogeneous u-v coverages preclude a definitive conclusion without uniform monitoring. | **partially**

## Reasoning

- Why this data: Millimeter recombination lines are intrinsically brighter, more optically thin, and unaffected by pressure broadening compared to cm RLs, making ALMA Band 6 data uniquely suited to measure systemic velocity and physical conditions.  
  > "Compared to their centimeter-wavelength counterparts, millimeter recombination lines (RLs) are intrinsically brighter and are free of pressure broadening." (abstract)
- Why this method: Excluding short baselines (< 100 klambda) filters out the strong extended background and sidelobes from the nearby Orion Hot Core, isolating the compact emission from BN.  
  > "We found that a minimum baseline length of $\approx 100$ k$\lambda$ gives optimal results, filtering out the emission on scales $>1\rlap.{''}4$." (Continuum.)
- Alternative: Imaging the hot core and Source I using restricted u-v coverage was rejected due to severe imaging artifacts/sidelobes.  
  > "This degradation of the u-v coverage produces artifacts (closely-spaced sidelobes) close to source I and the HC, and we refrained from using this part of the image." (Continuum.)
- Alternative: Imaging H30alpha without baseline restriction was considered, but sidelobes from blueshifted molecular lines near the HC contaminated the map.  
  > "The H30$\alpha$ line is also detected in maps that use the complete baseline range, but bright molecular emission from the HC centered at $\sim 10$ MHz blueshifted with respect to the RL creates sidelobes that are for the most part removed by taking only the longest baselines." (Recombination lines)
- Alternative: Standard electron temperature of Te = 10^4 K was rejected because pure thermal broadening would exceed the observed H30alpha linewidth.  
  > "Also, in the BN object this line appears to be too narrow (15.4 km s$^{-1}$) even for pure thermal broadening at $T_e=10^4$ K (equation A.2)." (Recombination lines)
- How they decided it was enough: Checked that the measured 1.3 mm flux density of BN remains consistent within 20% across different baseline filtering restrictions.  
  > "We note that the flux density for BN is the same, within $20~\%$, regardless of the u-v coverage restriction applied." (Continuum.)
- Limitation (authors): Inhomogeneity and systematic calibration uncertainties in mm interferometry prevent proving mm continuum variability conclusively.  
  > "However, the significance of these variations can be affected by the inhomogeneity of the mm observations." (Continuum.); "We emphasize that only dedicated multiepoch observations with a uniform setup can clarify this issue." (Discussion)
- Limitation (authors): H30alpha could not be detected toward Source I due to bright molecular line contamination from the nearby Hot Core.  
  > "the proximity of source I to the HC contaminates any emission from the relatively faint RL with brighter, more extended molecular lines with rest frequencies within a few MHz of the H$30\alpha$ line." (Recombination lines)
- Limitation (authors): The observed H30alpha to H53alpha line-to-continuum ratio is smaller than predicted for pure free-free emission (1.6 observed vs 6.4 expected), indicating substantial line-of-sight dust contamination in the 1.3 mm continuum.  
  > "Under these assumptions, the expected ratio of the H30$\alpha$ to H$53\alpha$ line-to-continuum ratios is 6.4. However, the observed value is 1.6." (cm and (sub)mm recombination lines)
- Caveat (inferred, ours): Differences in u-v sampling and flux scale calibrations between CARMA and ALMA could account for the apparent millimeter flux differences rather than true intrinsic variability.
- Caveat (inferred, ours): Potential non-LTE amplification or line-of-sight dust absorption could complicate simple LTE line-to-continuum interpretations.

## Reproducibility

- Data public (paper): yes (ALMA Science Verification archive, released April 12, 2012)  
  > "In this paper we make use of the fully calibrated visibilities released on April 12, 2012." (Data)
- Products in archive: yes (fully calibrated visibilities released)  
  > "In this paper we make use of the fully calibrated visibilities released on April 12, 2012." (Data)
- Missing: CASA imaging script containing clean/tclean parameter settings (weighting, cell size, robust parameter, mask).
- Missing: List of channel ranges used for u-v continuum subtraction in each of the 20 spectral windows.
- Missing: Aperture coordinates and radius used for extracting the H30alpha spectrum.
- Data volume (inferred): 10-25 GB
- Score (inferred): 4/5, The raw and calibrated visibilities are publicly available from the ALMA SV archive, and the analysis uses standard CASA steps (uv-continuum subtraction, baseline filtering at >100 klambda, and Gaussian line fitting). Reproducing the exact flux and profile parameters within 10-20% is straightforward, though exact clean settings and channel intervals are omitted.
- Rediscovery candidate: yes, The dataset is public ALMA SV data (Orion BN/KL Band 6), and applying a 100 klambda baseline cutoff to inspect the H30alpha line profile and measure the BN 1.3 mm flux can directly verify the central claims and numeric values.

## Links

- Method: (cite: kzk08) (Provided equation 3 used to estimate average electron density from recombination lines)
- Method: (cite: gm09) (Provided equation 1 for the combined Voigt recombination line FWHM incorporating thermal, dynamical, and pressure broadening)
- Method: (cite: walmsley90) (Provided tabulated hydrogen recombination non-LTE departure coefficients b_n and beta_n)
- Method: (cite: smirnov84) (Provided analytical formula for electron-collision pressure broadening)
- Method: (cite: gs02) (Reference textbook for recombination line broadening mechanisms and non-LTE radiative transfer relations)
- Companion: (cite: rodriguez09b) (Original presentation of the archival VLA B-array H53alpha observation re-analyzed in this paper)
- Related: ALMA Science Verification

## Checks

```json
{
 "quotes": 100,
 "quotes_ok": 98,
 "quote_pass_rate": 0.98,
 "quotes_too_long": 5,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 89,
  "stated": 72,
  "rate": 0.809
 },
 "evidence_ok": false
}
```
