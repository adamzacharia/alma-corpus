# ALMA observations of the dense and shocked gas in the nuclear region of NGC 4038 (Antennae galaxies)

`2017PASJ...69....6U` | Publications of the Astronomical Society of Japan 2017 | first author: Ueda, Junko | arXiv: 1611.00002 | DOI: 10.1093/pasj/psw110

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, astrochemistry
- Question: Where are the dense, shocked and star-forming gas in the nuclear region of NGC 4038, and do molecular shocks arise from inflowing gas colliding with the central molecular complex?  
  > "The purposes of this study are to reveal dusty star forming regions using dense gas tracers and continuum emission, and search for the presence of gas inflows" (Introduction)
- Target **NGC 4038 (Antennae galaxies, northern nucleus)**: coordinates _not stated_; z/distance velocity 1638 km/s (lines redshifted to this)  
  > "redshifted to the velocity of 1638 km s$^{-1}$" (2.1 ALMA Multi-line Observations at Band 3); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00003.SV
- bands: Band 3 (3 mm) multi-line; Band 7 CO (3-2) SV  
  > "The uncertainty of absolute flux calibration is 5% in Band 3" (2.1 ALMA Multi-line Observations at Band 3)
- frequencies and spectral setup: 4 spws, 1.875 GHz bandwidth each, 488 kHz resolution; coverage 87.78–91.51, 97.15–99.02, 111.56–113.43 GHz  
  > "The total frequency coverage is 7.47 GHz (87.78–91.51 GHz, 97.15–99.02 GHz, and 111.56–113.43 GHz)." (2.1 ALMA Multi-line Observations at Band 3)
- continuum bandwidth: _not stated_
- arrays: 12 m antennas, 31 to 33 available  
  > "The number of available 12 m antennas ranged from 31 to 33 depending on the observing run." (2.1 ALMA Multi-line Observations at Band 3)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.68''–0.92'' (line cubes); 0.95''x0.65'' (3 mm continuum)  
  > "The synthesized beam sizes range between 0.68$''$ and 0.92$''$" (2.1 ALMA Multi-line Observations at Band 3)
- max recoverable scale: 1.3 kpc  
  > "The MRS of our data is 1.3 kpc" (3.2 The HCN and HCO+ emission)
- sensitivity: 1.8–2.4 mJy/beam per 10 km/s channel; 3 mm continuum 0.05 mJy/beam  
  > "range between 1.8 mJy beam$^{-1}$ and 2.4 mJy beam$^{-1}$" (2.1 ALMA Multi-line Observations at Band 3)
- time on source: _not stated_
- observing dates: July and August 2014  
  > "carried out using ALMA on July and August, 2014" (2.1 ALMA Multi-line Observations at Band 3)
- pi or archival as stated: _not stated_
- Line: SiO 2-1 (not stated)
- Line: HCN 1-0 (not stated)
- Line: CO 3-2 (SV) (not stated)
- Other facility **VLA archival (PI A. Pedlar)**: 6 cm and 4 cm continuum for spectral index  
  > "we reimaged the 6 cm and 4 cm continuum emission using the VLA archival calibrated data (PI: A. Pedlar)" (3.3 The 3 mm Continuum emission)
- External data: CO (3-2)/(1-0) ratio of 0.6  
  > "assuming the CO (3–2)/(1–0) line ratio of 0.6, which was measured using the CO (1–0) and CO (3–2) maps of NGC 4038" (4.2 Dense gas fraction) [from (cite: Ueda12)]
- External data: alpha_CO = 4.35  
  > "We use a Galactic CO-to-H$_{2}$ mass conversion factor $\alpha_{\rm CO}$ = 4.35" (4.2 Dense gas fraction) [from (cite: Bolatto13)]
- External data: alpha_HCN = 10  
  > "the HCN-to-dense gas mass conversion factor $\alpha_{\rm HCN}$ = 10" (4.2 Dense gas fraction) [from (cite: Gao04)]

## Processing

### Calibration

- pipeline or manual: CASA 4.3.1 calibration; SV data self-calibrated per CASA guide  
  > "According to instructions in the CASA guide, we applied self-calibration to the calibrated visibility data" (2.2 ALMA CO (3–2) Science Verification Data)
- casa version: CASA 4.3.1  
  > "(CASA; Ver. 4.3.1)" (2.1 ALMA Multi-line Observations at Band 3)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ceres; bandpass J1130-1449; phase J1215-1731  
  > "Absolute flux calibration was performed using Ceres." (2.1 ALMA Multi-line Observations at Band 3)
- flux scale uncertainty: 5% in Band 3  
  > "The uncertainty of absolute flux calibration is 5% in Band 3" (2.1 ALMA Multi-line Observations at Band 3)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Band 3: natural; CO(3-2) SV: Briggs robust = 0.5  
  > "We used natural weighting of the visibilities for imaging to obtain the highest sensitivity." (2.1 ALMA Multi-line Observations at Band 3); "by adopting Briggs weighting of the visibilities (robust = 0.5)" (2.2 ALMA CO (3–2) Science Verification Data)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum maps made from line-free channels  
  > "We made the 3 mm continuum map using the line free channels." (2.1 ALMA Multi-line Observations at Band 3)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Discussion maps clipped to similar shortest uv range (12–14 kλ), convolved to 1.2''  
  > "created with visibilities clipped to have similar shortest uv range (uv distance = 12-14 k$\lambda$), and convolved to 1.2$''$ angular resolution" (4 Discussion)
- final beam: CO(3-2) 1.11''x0.65''; 850 um continuum 1.22''x0.73''  
  > "The synthesized beam size is 1.11$''$ $\times$ 0.65$''$" (2.2 ALMA CO (3–2) Science Verification Data)
- final rms: CO(3-2) 4.7 mJy/beam (10 km/s); 850 um 0.47 mJy/beam  
  > "The rms noise level at the velocity resolution of 10 km s$^{-1}$ is 4.7 mJy beam$^{-1}$." (2.2 ALMA CO (3–2) Science Verification Data)

### Inherited from earlier work

- SV CO(3-2) self-calibration and imaging follow the CASA guide  
  > "According to instructions in the CASA guide, we applied self-calibration to the calibrated visibility data" (2.2 ALMA CO (3–2) Science Verification Data) [from CASA guide]
- Dense gas fraction conversion factors same as previous study  
  > "using the same conversion factors as the previous study (cite: Bigiel15)" (4.2 Dense gas fraction) [from (cite: Bigiel15)]

### Not stated but needed to reproduce (our reading)

- Spectral smoothing kernel and spatial smoothing in MOMNT moment maps
- Line-free channel selection
- Image size and cell size
- Clean thresholds and masks
- Self-calibration solint for SV data
- Clumpfind parameters beyond the 2 sigma threshold
- Exact line rest frequencies
- Distance to NGC 4038

## Analysis recipe

1. **Calibrate and image Band 3 data and SV CO(3-2) data**: CASA calibration and imaging; natural weighting for Band 3; SV self-calibration, Briggs 0.5  
  > "Data calibration and imaging was carried out using the Common Astronomy Software Applications package (CASA; Ver. 4.3.1)." (2.1 ALMA Multi-line Observations at Band 3)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Make integrated intensity maps**: smooth and clip cube at 1.5 sigma per channel with MOMNT  
  > "This cube was clipped at the 1.5$\sigma$ level per channel." (3 Results of the new observations)
   - software: AIPS MOMNT
   - fitting: _not stated_
   - validation: _not stated_
3. **Radio spectral index of continuum**: Reimage VLA 6 and 4 cm with matched uv range (9.7 kλ), convolve to 1.2''  
  > "We clipped the visibilities so that the VLA and ALMA data have the same shortest uv range (9.7 k$\lambda$) and convolved both data to 1.2$''$ angular resolution." (3.3 The 3 mm Continuum emission)
   - software: CASA
   - fitting: _not stated_
   - validation: extrapolated 3 mm flux compared to observed  
  > "This is consistent with the observed value within the error." (3.3 The 3 mm Continuum emission)
4. **Line ratios and dense gas fraction**: HCN/CO(3-2) converted to HCN/CO(1-0) with 0.6, then masses with alpha_CO and alpha_HCN  
  > "We convert the HCN (1–0)/CO (3–2) line ratios into HCN (1–0)/CO (1–0) line ratios, assuming the CO (3–2)/(1–0) line ratio of 0.6" (4.2 Dense gas fraction)
   - assumption: alpha_CO = 4.35, alpha_HCN = 10  
  > "$\alpha_{\rm HCN}$ = 10 $M_{\solar}$ (K km s$^{-1}$ pc$^{2}$)$^{-1}$" (4.2 Dense gas fraction)
   - fitting: _not stated_
   - validation: varied CO(3-2)/(1-0) to 0.7 and 0.5  
  > "Assuming the CO (3–2)/CO (1–0) line ratio of 0.7 and 0.5, the average dense gas fraction changes to $\sim$20% and $\sim$14%" (4.2 Dense gas fraction)
5. **Identify molecular complexes and infall**: Clumpfind on CO(3-2) SV cube with 2 sigma threshold; velocity comparison with rotation  
  > "using the recommended 2$\sigma$ threshold to identify robust molecular clumps" (4.5 Possibilities of the shock origin)
   - software: Clumpfind
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.3.1: calibration and imaging  
  > "(CASA; Ver. 4.3.1)" (2.1 ALMA Multi-line Observations at Band 3)
- **AIPS MOMNT** : smoothing/clipping moment maps  
  > "using the AIPS task, MOMNT" (3 Results of the new observations)
- **Clumpfind** : clump identification in CO(3-2)  
  > "automatic clump identification algorithm Clumpfind (cite: Williams94)" (4.5 Possibilities of the shock origin)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 3 mm continuum total flux | 0.59 | 0.03 | mJy | 1 | 0.59 $\pm$ 0.03 mJy |
| radio spectral index | -0.18 | 0.34 | dimensionless | 3 | $\alpha$ = -0.18 $\pm$ 0.34 |
| average CN/HCN ratio | 0.7 | 0.3 | dimensionless | 4 | CN/HCN = 0.7 $\pm$ 0.3 |
| average dense gas fraction | 17% | 8% | percent | 4 | 17 % $\pm$ 8% |
| L_HCN/L_CO(1-0) | 0.08 | 0.03 | dimensionless | 4 | 0.08 $\pm$ 0.03 |
| gas mass within 0.6'' of CO peak | 1.1e8 | not stated | Msun | 4 | 1.1 $\times$ 10$^{8}$ $M_{\solar}$ |
| Complex 1 gas mass | 3.2e8 | not stated | Msun | 5 | $3.2 \times 10^{8}~M_{\solar}$ |
| Complex 1 radius | 144 | 30 | pc | 5 | 144 $\pm$ 30 pc |
| CH3OH/HNCO peak ratio at CH3OH peak | 1.7 | 0.1 | dimensionless | 0 | 1.7$\pm$0.1 |

## Qualitative findings

- CH3OH, HNCO and CN detected for the first time in NGC 4038 nucleus; 3 mm continuum is free-free dominated  
  > "Three molecules (CN, CH$_{3}$OH, and HNCO) were detected for the first time in the nuclear region of NGC 4038." (abstract)

## Claim tuples

- H: Star-forming regions are PDRs | E: CN/HCN ratio map vs continuum | R: CN/HCN ≈0.8–1.2 near 3 mm and 850 um peaks | F: PDRs present | **supported**
- H: Shocks driven by inflow colliding with central complex | E: Clumpfind on CO(3-2) and velocity comparison with shock tracers | R: Inflowing gas component connects with Complex 1 where shocked gas is seen | F: Inflow-complex collisions suggested; outflows disfavored | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Star-formation outflows rejected as unlikely, requiring 3.2 outflows pc^-2 across a few 100 pc  
  > "it is unlikely that such star-forming regions is forming across a few 100 pc$^{2}$" (4.5 Possibilities of the shock origin)
- How they decided it was enough: _not stated_
- Limitation (authors): Dense gas fraction uncertain due to assumed CO(3-2)/(1-0) ratio and conversion factors  
  > "our estimation has a large uncertainty because the dense gas fraction changes depending on the assumed CO (3–2)/CO (1–0) line ratio" (4.2 Dense gas fraction)
- Caveat (inferred, ours): Single CO(3-2)/(1-0) ratio and Galactic alpha_CO applied to a starburst nucleus
- Caveat (inferred, ours): Inflow interpretation based on velocity geometry in a disturbed system
- Caveat (inferred, ours): SiO non-detection limits shock-strength conclusions

## Reproducibility

- Data public (paper): Project codes cited; SV data public  
  > "ADS/JAO.ALMA#2012.0.01000.S and ALMA Science Verification data: ADS/JAO.ALMA#2011.0.00003.SV" (Acknowledgements)
- Products in archive: _not stated_
- Missing: Image and cell parameters
- Missing: Smoothing details for moment maps
- Missing: Clumpfind settings
- Data volume (inferred): ~50–150 GB
- Score (inferred): 3/5, Public data and main steps given but many imaging and smoothing parameters missing.
- Rediscovery candidate: no, Recipe lacks key parameters for exact redo.

## Links

- Companion: (cite: Schirm16) (Previous ALMA HCN/HCO+ data of Antennae compared)
- Related: ALMA Science Verification Antennae CO(3-2)

## Checks

```json
{
 "quotes": 56,
 "quotes_ok": 56,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2012.1.01000.S"
 ],
 "codes_printed_but_missing": [
  "2012.0.01000.S"
 ],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 39,
  "rate": 0.549
 },
 "evidence_ok": true
}
```
