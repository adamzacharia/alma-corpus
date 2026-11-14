# ALMA and VLA observations of recombination lines and continuum toward the Becklin-Neugebauer object in Orion

`2012A&A...547L...3G` | Astronomy and Astrophysics 2012 | first author: Galván-Madrid, R. | arXiv: 1210.1413 | DOI: 10.1051/0004-6361/201220330

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation, milky_way_ism
- Question: What do millimeter and centimeter recombination lines and continuum reveal about the ionized envelope, velocity and flux variability of the BN object in Orion?  
  > "observing hydrogen recombination lines (RLs) can be used to obtain the line-of-sight velocities of the radio sources, which are needed to complement the proper-motion information." (Introduction)
- Target **Becklin-Neugebauer (BN) object, Orion BN/KL**: coordinates pointing center RA 05h35m14.35s, Dec -05d22'35.0" (J2000)  
  > "The pointing center was $\alpha_\mathrm{J2000}=05^\mathrm{h}~35^\mathrm{m}~14\rlap.{^\mathrm{s}}35$, $\delta_\mathrm{J2000}=-05^\circ~22'~35\rlap.{''}0$." (Data); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00009.SV
- bands: _not stated_
- frequencies and spectral setup: 20 spectral windows, 213.72-246.62 GHz, 0.488 MHz (~0.6 km/s) resolution  
  > "The data consisted of 20 different spectral windows covering the frequency range from 213.72 GHz to 246.62 GHz." (Data); "Each spectral window had a uniform spectral resolution of 0.488 MHz ($\sim0.6$ km s$^{-1}$)" (Data)
- continuum bandwidth: _not stated_
- arrays: 16 12-m antennas, compact configuration  
  > "The array used 16 12-m antennas in a compact configuration" (Data)
- configurations: _not stated_
- baselines: 15 to 269 kλ  
  > "baselines in the range of 15 k$\lambda$ to 269 k$\lambda$" (Data)
- angular resolution: HPBW = 1.3" x 0.6" (ALMA continuum)  
  > "e: ALMA SV data, HPBW$=1\rlap.{''}3 \times 0\rlap.{''}6$ (this paper)." (Table 2)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: ~15 minutes per spectral window  
  > "was observed for an on-source time of $\sim 15$ minutes" (Data)
- observing dates: January 19, 2012  
  > "Orion BN/KL was observed on January 19, 2012 with ALMA as part of the SV program." (Data)
- pi or archival as stated: ALMA Science Verification archive data; VLA archival data  
  > "We also present archival Very Large Array[^2] (VLA) data." (Data)
- Line: H30α n=31→30 (231.9009 GHz)
- Line: H53α n=54→53 (42.95197 GHz)
- Other facility **VLA**: H53α B-array data (AR635) and 8.4 GHz A-array continuum epochs  
  > "several epochs of continuum observations at 8.4 GHz in the A configuration were processed using standard methods in the AIPS software." (Data)
- External data: OVRO 218 GHz BN flux 150±50 mJy  
  > "the 218 GHz flux of $S=150\pm50$ mJy (from OVRO observations in 1993 and 1994)" (Continuum.) [from (cite: plambeck95); (cite: blake96)]
- External data: CARMA 231 GHz non-detection of BN, 3σ <~34 mJy  
  > "(cite: fs08) do not detect BN at 231 GHz down to a $3\sigma$ level of $\sim 34$ mJy" (Continuum.) [from (cite: fs08)]
- External data: Four epochs of 3.6 cm BN fluxes  
  > "together with the four epochs reported by (cite: zapata04), also at 3.6 cm" (Continuum.) [from (cite: zapata04)]
- External data: H53α spectrum of BN  
  > "B-array observations have been previously presented by (cite: rodriguez09b) (project AR635)." (Data) [from (cite: rodriguez09b)]

## Processing

### Calibration

- pipeline or manual: Fully calibrated SV visibilities used; CASA processing  
  > "we make use of the fully calibrated visibilities released on April 12, 2012." (Data)
- casa version: CASA 3.3.0 and 3.4.0  
  > "The processing was done in CASA versions 3.3.0 and 3.4.0." (Data)
- pipeline version: _not stated_
- archive products used as is: Calibrated visibilities released by SV team  
  > "we make use of the fully calibrated visibilities released on April 12, 2012." (Data)
- flux calibrator: Callisto and Mars; phase calibrator J0607-085  
  > "The absolute amplitude scale was derived from observations of Callisto and Mars. The phase calibrator was J0607–085." (Data)
- flux scale uncertainty: ~10%  
  > "we estimate that the amplitude scale of the ALMA observations is accurate to $\sim 10~\%$." (Data)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: minimum baseline ≈100 kλ (short baselines removed), filters scales >1.4"  
  > "We found that a minimum baseline length of $\approx 100$ k$\lambda$ gives optimal results, filtering out the emission on scales $>1\rlap.{''}4$." (Continuum.)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uv-domain linear baseline fit to line-free channels  
  > "Continuum subtraction was done in the u-v domain by carefully selecting the line-free channels in each spectral window and fitting a linear spectral baseline." (Results)
- line free channels: _not stated_
- primary beam correction: maps not corrected; fluxes quoted are corrected  
  > "We present maps that have not been corrected for primary beam attenuation. The corrected fluxes are quoted in the text and tables." (Results)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: ~3 mJy in the >100 kλ continuum map  
  > "The noise is $\times 5$ lower than in Fig. 1 ($\sim 3$ mJy)." (Continuum.)

### Inherited from earlier work

- Combined RL FWHM formula  
  > "The line FWHM of the combined profile is given by (cite: gm09):" (Recombination lines) [from (cite: gm09)]
- Electron density from equation 3  
  > "using equation 3 of (cite: kzk08), the average electron density traced by these RLs is $N_e=8.4\times10^6$ cm$^{-3}$." (Recombination lines) [from (cite: kzk08)]

### Not stated but needed to reproduce (our reading)

- CASA tclean/clean parameters (weighting, robust, cell, image size, deconvolver, masks)
- Line-free channel ranges per spectral window
- Aperture used for spectra and Gaussian fitting
- Inputs to the Ne calculation (size, continuum flux, assumed Te)
- Which spectral windows contain H30α and rest-frame velocity convention
- VLA H53α and 8.4 GHz AIPS imaging parameters

## Analysis recipe

1. **Continuum imaging of BN field**: Co-add line-free visibilities from all spectral windows; image with and without short baselines (>100 kλ)  
  > "obtained by co-adding the line-free continuum visibilities from all spectral windows." (Continuum.)
   - software: CASA
   - parameter: minimum baseline ≈100 kλ  
  > "a minimum baseline length of $\approx 100$ k$\lambda$ gives optimal results" (Continuum.)
   - fitting: _not stated_
   - validation: Flux of BN same within 20% for different uv restrictions; continuum from different spws consistent  
  > "We note that the flux density for BN is the same, within $20~\%$, regardless of the u-v coverage restriction applied." (Continuum.)
2. **Reprocess VLA 8.4 GHz epochs for flux variability**: Standard AIPS processing of three archival A-array epochs; compare with ALMA and literature fluxes  
  > "We have reprocessed three epochs of VLA archival data at 3.6 cm (8.4 GHz) to look for possible variations in the continuum emission from BN." (Continuum.)
   - software: AIPS
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure RL parameters**: Gaussian fits to H30α and H53α spectra with aperture matched to emitting area; moment 0 maps with baselines >100 kλ  
  > "From Gaussian fits to the spectra shown in Fig. 3 using an aperture adjusted to the emitting area shown in Fig. 4." (Table 3)
   - software: CASA
   - fitting: Gaussian fit  
  > "From Gaussian fits to the spectra shown in Fig. 3" (Table 3)
   - validation: _not stated_
4. **Constrain Te, bulk motions and Ne from linewidths**: Decompose linewidth into thermal, dynamical and pressure broadening; use H30α narrowness to bound Te; Ne from Keto et al. equation  
  > "Therefore, for the gas traced by the H30$\alpha$ line, $T_e$ is at most 4900 K" (Recombination lines)
   - assumption: LTE approximately valid (b30≈0.98, β30~-1.5 at Ne=1e7)  
  > "$b_{30}\approx 0.98$ and $\beta_{30} \sim -1.5$ for a density $N_e=10^7$ cm$^{-3}$" (cm and (sub)mm recombination lines)
   - fitting: _not stated_
   - validation: Non-LTE check in Appendix B  
  > "In Appendix B we show that the RLs in BN are reasonably close to LTE" (Recombination lines)

## Software

- **CASA** 3.3.0 and 3.4.0: ALMA data processing  
  > "The processing was done in CASA versions 3.3.0 and 3.4.0." (Data)
- **AIPS** : VLA 8.4 GHz continuum processing  
  > "processed using standard methods in the AIPS software" (Data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| BN 1.3 mm flux density (primary-beam corrected) | 126 | ±14 | mJy | 1 | / 19 Jan 2012 / – / $126\pm14$ / e / |
| H30α peak flux | 181 | ±14 | mJy | 3 | / H$30\alpha$ / 231.9009 / $181\pm14$ / $26.3\pm0.5$ / $15.4\pm1.3$ / |
| BN vLSR from H30α | 26.3 | ±0.5 | km/s | 3 | / H$30\alpha$ / 231.9009 / $181\pm14$ / $26.3\pm0.5$ / $15.4\pm1.3$ / |
| H30α FWHM | 15.4 | ±1.3 | km/s | 3 | / H$30\alpha$ / 231.9009 / $181\pm14$ / $26.3\pm0.5$ / $15.4\pm1.3$ / |
| H53α peak flux | 9.9 | ±1.1 | mJy | 3 | / H$53\alpha$ / 42.95197 / $9.9\pm1.1$ / $19.8\pm2.1$ / $39.0\pm5.0$ / |
| H53α FWHM | 39.0 | ±5.0 | km/s | 3 | / H$53\alpha$ / 42.95197 / $9.9\pm1.1$ / $19.8\pm2.1$ / $39.0\pm5.0$ / |
| Electron temperature upper limit | <4900 | not stated | K | 4 | Therefore, for the gas traced by the H30$\alpha$ line, $T_e$ is at most 4900 K |
| Average electron density | 8.4e6 | not stated | cm^-3 | 4 | the average electron density traced by these RLs is $N_e=8.4\times10^6$ cm$^{-3}$. |
| Faint source south of BN, 1.3 mm flux | 26 | not stated | mJy | 1 | A faint compact source with primary beam corrected flux $S_\mathrm{1.3mm}=26$ mJy is also detected $4\rlap.{''}3$ south of BN. |

## Qualitative findings

- H53α is broader and blueshifted relative to H30α, interpreted as pressure broadening and optical depth effects in an outflowing envelope  
  > "The H$30\alpha$ line is narrower than the H$53\alpha$ line, and it is redshifted by a few km s$^{-1}$." (Recombination lines)
- Dust may contribute significantly to the 1.3 mm continuum of BN  
  > "This suggests that dust contributes a significant fraction to the (sub)mm continuum of BN." (cm and (sub)mm recombination lines)

## Claim tuples

- H: Can mm RLs be detected from BN and trace its ionized envelope? | E: ALMA SV H30α spectra and VLA H53α compared | R: H30α detected, FWHM 15.4 km/s, Te<4900 K, Ne=8.4e6 | F: RL arises from dense, slowly moving base of the envelope | **supported**
- H: Is BN variable in the mm continuum? | E: Compared ALMA 1.3 mm flux with earlier OVRO and CARMA values and cm VLA epochs | R: 126 mJy vs 150±50 and <34 mJy; 3.6 cm stable within 30% | F: Possible variability, but inhomogeneous setups prevent confirmation | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Removing short baselines isolates compact BN emission from extended hot-core emission  
  > "at the position of BN, where emission is fainter, the restricted u-v coverage effectively removes the extended emission around BN." (Continuum.)
- Alternative: Flux differences may be systematic errors from flux-scale and uv-coverage rather than variability  
  > "One possible explanation for the differences in the mm fluxes that have been reported for BN is that they are, at least partially, caused by systematic errors in the measurements." (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Inhomogeneity of mm observations affects significance of variability  
  > "the significance of these variations can be affected by the inhomogeneity of the mm observations." (Continuum.)
- Caveat (inferred, ours): Single ALMA epoch; variability claim rests on heterogeneous literature data
- Caveat (inferred, ours): Te and Ne derived with simple LTE homogeneous assumptions and no uncertainties
- Caveat (inferred, ours): Imaging parameters absent, limiting exact flux reproduction

## Reproducibility

- Data public (paper): ALMA Science Verification data released publicly; VLA archival data  
  > "recently released Science Verification (SV) data taken toward Orion BN/KL" (Results)
- Products in archive: _not stated_
- Missing: tclean parameters
- Missing: line-free channels
- Missing: spectral extraction aperture
- Missing: Ne calculation inputs
- Data volume (inferred): ~10-30 GB for ALMA SV plus small VLA datasets
- Score (inferred): 3/5, Public data and numeric results, but imaging details are missing and analysis is simple.
- Rediscovery candidate: yes, Public SV data, numeric line and flux results; recipe is short though imaging parameters must be chosen.

## Links

- Method: (cite: gm09) (Linewidth formula combining broadening mechanisms)
- Method: (cite: kzk08) (Electron density equation and RL interpretation)
- Companion: (cite: rodriguez09b) (Previously presented VLA H53α data)
- Related: ALMA Science Verification Orion BN/KL

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
