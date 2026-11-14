# The Origin of the X-Ray Emission in Two Well-aligned Extragalactic Jets: The Case for IC/CMB

`2019ApJ...883L...2M` | The Astrophysical Journal Letters 2019 | first author: Meyer, Eileen T. | arXiv: 1908.07139 | DOI: 10.3847/2041-8213/ab3db3

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: agn_and_quasars
- Question: Is the X-ray emission of the kpc-scale jets of OJ 287 and PKS 1510-089 due to IC/CMB, as tested by the predicted minimum Fermi/LAT gamma-ray flux?  
  > "We have used archival multiwavelength observations to make precise predictions for the expected minimum flux in the GeV band, assuming that the X-ray emission from the kpc-scale jet is entirely due to the IC/CMB process." (abstract)
- Target **OJ 287**: coordinates _not stated_; z/distance z = 0.306  
  > "At the distance of OJ 287 ($z$ = 0.306) 1$''$ corresponds to a projected distance of 4.36 kpc" (Introduction); distance from _not stated_
- Target **PKS 1510-089**: coordinates _not stated_; z/distance z = 0.36  
  > "for PKS 1510$-$089 ($z=0.36$) it corresponds to 4.87 kpc" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.00406.S, 2016.1.00116.S
- bands: OJ 287: Band 3; PKS 1510-089: Bands 4, 6, 7  
  > "we reduced archival band 4, 6, and 7 observations from project 2016.1.00116.S" (Data Sources and Methods)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: PKS 1510-089 synthesized beams 2.49x1.72, 1.82x1.36, 1.20x0.93 arcsec (Bands 4, 6, 7)  
  > "with synthesized beam sizes of 2.49$''$ $\times$ 1.72$''$, 1.82$''$ $\times$ 1.36$''$, and 1.20$''$ $\times$ 0.93$''$, respectively." (Data Sources and Methods)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: archival  
  > "we reduced archival band 4, 6, and 7 observations from project 2016.1.00116.S" (Data Sources and Methods)
- Other facility **Fermi/LAT**: Gamma-ray minimum-flux SED via progressive binning  
  > "We utilized the progressive binning method to search for the minimum flux or upper limit in the five canonical Fermi/LAT energy bands" (Fermi/LAT)
- Other facility **Chandra**: Jet X-ray fluxes (re-analysis of OBSID 11432 for PKS 1510-089)  
  > "We re-analyzed a deeper 45 ks ACIS-S observation from (OBSID: 11432)" (HST and Chandra)
- Other facility **VLA**: L and C band A-configuration archival data for PKS 1510-089  
  > "we analyzed historical VLA observations at L and C band in A-configuration from project codes AH938 and AO070" (VLA and ALMA)
- External data: OJ 287 radio fluxes at 1.4, 4.8, 8.6 GHz; HST upper limit; Chandra flux  
  > "the radio fluxes for the entire large-scale jet at 1.4 GHz, 4.8 GHz, and 8.6 GHz were taken from (cite: marscher2011)" (VLA and ALMA) [from (cite: marscher2011)]
- External data: PKS 1510-089 HST upper limit  
  > "$^{b}$ (cite: sambruna2004), otherwise this paper" (Table 1) [from (cite: sambruna2004)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline via scriptForPI.py, then self-calibration  
  > "The data were initially processed using the ‘scriptForPI.py’ script with CASA in pipeline mode." (VLA and ALMA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: 1-2 rounds phase-only, then one amplitude and phase round  
  > "we applied 1-2 rounds of phase-only self-calibration before a final round of amplitude and phase self-calibration." (VLA and ALMA)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: core subtraction in the uv plane with uvsub using CLEAN core model, then re-CLEAN  
  > "subtracted these from the visibility data using the CASA task `uvsub`." (VLA and ALMA)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: PKS 1510-089 Bands 4/6/7: 7.3e-5, 1.0e-4, 1.6e-4 Jy  
  > "The final RMS of these images was 7.3 $\times$ 10$^{-5}$ Jy, 1.0 $\times$ 10$^{-4}$ Jy and 1.6 $\times$ 10$^{-4}$ Jy" (VLA and ALMA)

### Inherited from earlier work

- Progressive binning Fermi/LAT method  
  > "The method used is identical to that described in (cite: meyer14) and (cite: meyer15) which we refer to for further details." (Fermi/LAT) [from (cite: meyer14); (cite: meyer15)]
- IC/CMB spectrum predicted by shifting the synchrotron spectrum  
  > "shifted in frequency and luminosity according to the formulae in (cite: geo06)" (Results) [from (cite: geo06)]

### Not stated but needed to reproduce (our reading)

- Imaging parameters (weighting, robust, cell, image size, masks, deconvolver) for ALMA images
- Which ALMA execution blocks and dates were used
- How core-subtracted jet flux was integrated (region) and flux uncertainties
- CASA version for ALMA reduction
- Fermi source model and likelihood settings
- Exact formula implementation and adopted synchrotron SED fit for the IC/CMB prediction

## Analysis recipe

1. **Measure core-subtracted jet radio/mm fluxes**: Calibrate and self-calibrate, CLEAN, subtract core model with uvsub, re-CLEAN  
  > "We then ran a final round of CLEAN on the now-subtracted MS file to produce the image without core emission." (VLA and ALMA)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure Chandra jet flux**: MARX PSF simulation of core subtracted from the jet; power-law fit in Sherpa  
  > "We conducted PSF simulations of the core in order to account for its contribution of flux to the inner jet." (HST and Chandra)
   - software: CIAO, MARX, SHERPA
   - fitting: _not stated_
   - validation: _not stated_
3. **Fermi minimum-flux SED**: Weekly light curve reordered by TS, progressive recombination, minimum flux or upper limit per band  
  > "We then adopt the absolute minimum flux or upper limit in each band individually over the whole recombined binning to generate the minimum SED." (Fermi/LAT)
   - software: Fermi Science Tools
   - fitting: _not stated_
   - validation: _not stated_
4. **Compare with IC/CMB prediction**: Shift radio-optical synchrotron SED to match X-rays; compare with Fermi minimum SED; derive B/delta and delta  
  > "the inverse Compton spectrum is essentially a copy of the synchrotron spectrum, shifted in frequency and luminosity" (Results)
   - assumption: X-ray emission entirely IC/CMB; gamma_min = 10; H0=73, OmegaM=0.27, OmegaL=0.73  
  > "an assumed minimum electron Lorentz factor $\gamma_\mathrm{min}$ of 10" (Discussion and Conclusions)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.3.0 (VLA): Calibration, CLEAN, self-calibration, uvsub  
  > "The data were calibrated using standard procedures in CASA version 5.3.0" (VLA and ALMA)
- **CIAO** 4.11: Chandra analysis  
  > "The analysis was conducted using CIAO 4.11." (HST and Chandra)
- **MARX** : Chandra PSF simulation  
  > "We used the toolset MARX, which provides ray tracing routines for the Chandra optics to simulate the PSF." (HST and Chandra)
- **SHERPA** : Power-law spectral fits  
  > "We also fit the extracted jet spectrum as a power-law in SHERPA" (HST and Chandra)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| PKS 1510-089 Chandra jet flux at 1 keV | 14.8 | 0.2 | nJy | 2 | resulting in an estimate of 14.8 $\pm$ 0.2 nJy at 1 keV |
| PKS 1510-089 jet X-ray spectral index | 0.56 | 0.11 | dimensionless | 2 | yielding a spectral index $\alpha$ = 0.56 $\pm$ 0.11 |
| Required Doppler factors OJ 287 / PKS 1510-089 | 22.5 / 19 | not stated | dimensionless | 4 | the required Doppler factors $\delta$ are 22.5 and 19 to match the gamma-ray minimum level. |
| Minimum IC/CMB jet power OJ 287 / PKS 1510-089 | 1.8e45 / 1.2e45 | not stated | erg s^-1 | 4 | $1.8\times 10^{45}$ and $1.2\times 10^{45}$ erg s$^{-1}$ for OJ 287 and PKS 1510$-$089 respectively |

## Qualitative findings

- OJ 287 shows a plateau in the Fermi progressive-binning curve consistent with a steady IC/CMB floor; PKS 1510-089 shows none.  
  > "In the case of OJ 287, we do see signs of such ‘plateau’ behavior consistent with a steady flux level in the highest energy band" (Results)

## Claim tuples

- H: The minimum Fermi/LAT flux matches the IC/CMB prediction from the radio-to-X-ray SED | E: Progressive binning of Fermi data compared with SED-shifted IC/CMB predictions | R: Minimum fluxes agree extremely well with predictions for both jets | F: IC/CMB emission is detected for OJ 287 and PKS 1510-089; the case is stronger for OJ 287 | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): For PKS 1510-089 the minimum may be a low state of the core matching IC/CMB by chance.  
  > "it cannot be ruled out that the minimum gamma-ray flux level is due to a low state of the variable core which only matches the IC/CMB prediction by chance." (abstract)
- Caveat (inferred, ours): Minimum-flux SED mixes different epochs per band, and the core may contribute
- Caveat (inferred, ours): No quantitative goodness-of-fit between prediction and data
- Caveat (inferred, ours): ALMA role is minor: OJ 287 jet was undetected and only PKS 1510-089 mm fluxes were derived

## Reproducibility

- Data public (paper): Archival ALMA, VLA, Chandra and Fermi data  
  > "we reduced archival band 4, 6, and 7 observations from project 2016.1.00116.S" (VLA and ALMA)
- Products in archive: _not stated_
- Missing: ALMA imaging parameters
- Missing: Fermi analysis configuration details
- Missing: SED fitting and prediction details
- Data volume (inferred): ~50-200 GB for ALMA, VLA and Chandra, plus Fermi photon data
- Score (inferred): 3/5, Public data and the workflow are outlined, but many parameters are missing and the ALMA part is minor.
- Rediscovery candidate: no, The recipe is incomplete and the main result rests on a Fermi comparison with qualitative agreement.

## Links

- Method: (cite: meyer14); (cite: meyer15) (Progressive binning Fermi method)
- Method: (cite: geo06) (IC/CMB prediction formulae)
- Companion: (cite: meyer17) (Earlier Fermi limits on IC/CMB and the SED-shift model)
- Companion: (cite: breiding2017) (Earlier Fermi limits on IC/CMB)
- Related: Fermi/LAT survey of X-ray jets (Breiding et al. 2019, in prep.)

## Checks

```json
{
 "quotes": 37,
 "quotes_ok": 37,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2016.1.00116.S"
 ],
 "obscore_codes_not_in_card": [
  "2016.1.00112.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 29,
  "rate": 0.403
 },
 "evidence_ok": true
}
```
