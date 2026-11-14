# Molecular Distributions of the Protostellar Envelope and the Outflow of IRAS 15398-3359: Principal Component Analysis

`2020ApJ...900...40O` | The Astrophysical Journal 2020 | first author: Okoda, Yuki | arXiv: 2007.11106 | DOI: 10.3847/1538-4357/aba51e

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation, astrochemistry
- Question: Can PCA characterize, without preconception, the distributions of 15 molecular lines and the continuum around the Class 0 protostar IRAS 15398-3359 on outflow and disk/envelope scales?  
  > "In this paper, we apply the PCA to the molecular-line and continuum images observed toward this source to characterize their distributions." (Introduction)
- Target **IRAS 15398-3359**: coordinates 15:43:02.242, -34:09:06.70 (J2000, field center)  
  > "IRAS 15398$-$3359 is a low-mass Class 0 protostellar source (cite: Jorgensen et al.(2013)) in the Lupus 1 molecular cloud (cite: Lombardi et al.(2008))." (Introduction); "The field center was ($\alpha_{2000}$, $\delta_{2000}$)= (15.43h.02m.242s, $-$34$^\circ$ 09$'$ 06.70$''$)" (Observation); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.01157.S, 2015.1.01380.S
- bands: Band 6 (Cycle 2) and Band 7 (Cycle 3)  
  > "Spectral lines of CCH, SO, and CS listed in Table [1](#observations) were observed in the frequency range from 244 to 263 GHz with the Band 6 receiver." (Observation)
- frequencies and spectral setup: Band 7: 349-365 GHz; line windows 122 kHz resolution, 59 MHz bandwidth; DCN 977 kHz, 938 MHz  
  > "The backend correlator for molecular line observations except for the DCN observation was set to a resolution of 122 kHz and a bandwidth of 59 MHz" (Observation)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 14.70 to 452.72 m (Cycle 3)  
  > "Forty-two antennas were used in the observations, where the baseline length ranged from 14.70 to 452.72 m." (Observation)
- angular resolution: Cycle 3 continuum 0.48x0.45 arcsec; Cycle 2 continuum 0.21x0.15 arcsec  
  > "The original synthesized beam size of the continuum image is 0.48$''$$\times$0.45$''$ (P.A. 83$^\circ$)" (Observation)
- max recoverable scale: 2.5 arcsec  
  > "Since these largest angular sizes are 2.5$''$ for both of these observations" (Observation)
- sensitivity: _not stated_
- time on source: 19.30 minutes (Cycle 3)  
  > "The total on-source time was 19.30 minutes." (Observation)
- observing dates: 2015 July 20 (Cycle 2); 2016 March 31 (Cycle 3)  
  > "The Cycle 2 observation was conducted on 2015 July 20." (Observation); "The Cycle 3 observation was conducted on 2016 March 31." (Observation)
- pi or archival as stated: PI: Yoko Oya  
  > "ADS/JAO.ALMA#2013.1.01157.S and #2015.1.01380.S (PI: Yoko Oya)." (Acknowledgments)
- Line: H2CO 5_{K}-4_{K} (Ka=0-3) (351.769-364.289 GHz)
- Line: CCH N=3-2 and N=4-3 hyperfine groups (262.004 and 349.338-349.415 GHz)
- Line: CS 5-4 (244.9355565 GHz)
- Line: SO 6_7-5_6 (261.8437210 GHz)
- Line: CH3OH 4_{0,4}-3_{1,3} E (350.6876620 GHz)
- Line: DCN 5-4 (362.0457535 GHz)
- Line: c-C3H2 9-8 and 10-9 groups (351.965969 and 351.781578 GHz)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: not applied  
  > "Self-calibration was not applied in this study, because the continuum emission is not bright enough." (Observation)

### Imaging

- task: CLEAN  
  > "Images were prepared by using the CLEAN algorithm, where the Briggs’ weighting with a robustness parameter of 0.5 was employed." (Observation)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "Briggs’ weighting with a robustness parameter of 0.5 was employed" (Observation)
- uv taper: _not stated_
- cell size: _not stated_
- image size: 2048 x 2048 pixels  
  > "The pixel sizes were set to be (2048, 2048) for the whole observed area in the CLEAN procedure." (Observation)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum from line-free channels, subtracted from visibilities  
  > "the line images were obtained after subtracting the continuum component directly from the visibilities" (Observation)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: imsmooth Gaussian kernel to 0.5"x0.5"  
  > "the beam size was set to be 0.5$''\times0.5''$ by using a gaussian kernel with $imsmooth$" (Observation)
- final beam: 0.5"x0.5"  
  > "the beam size was set to be 0.5$''\times0.5''$" (Observation)
- final rms: _not stated_

### Inherited from earlier work

- Other details of the Cycle 2 observations  
  > "Other details of the observations are described elsewhere (cite: Okoda et al.(2018))." (Observation) [from Okoda et al.(2018)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration procedure/calibrators
- line-free channels and velocity ranges for moment 0 maps
- clean masks, thresholds, and cell size
- spectral setup of Cycle 2 in detail
- LVG/RADEX collision data, density and line-width assumptions for the blob temperature fits
- image regions/pixel selection for the two PCA scales

## Analysis recipe

1. **Image lines and continuum**: CLEAN with Briggs weighting, continuum subtraction in uv, smooth to 0.5" beam, make moment 0 maps  
  > "the line images were obtained after subtracting the continuum component directly from the visibilities" (Observation)
   - software: CASA
   - parameter: robust = 0.5; beam 0.5"x0.5"  
  > "a robustness parameter of 0.5 was employed" (Observation)
   - fitting: _not stated_
   - validation: _not stated_
2. **PCA of distributions**: Diagonalize correlation matrix of 16 (whole) or 15 (disk/envelope) images using pixels above 3 sigma in both distributions  
  > "these functions are obtained by diagonalizing the correlation matrix, because the intensities are different from molecular line to molecular line." (Principal Component Analysis)
   - software: numpy, matplotlib, pandas, astropy
   - parameter: threshold = 3 x rms  
  > "Three times the rms noise level (Tables [2](#corr_outflow)) is employed as the threshold level." (Principal Component Analysis)
   - fitting: _not stated_
   - validation: 1000 Monte Carlo realizations with beam-convolved Gaussian noise added; standard deviations of PC values computed  
  > "This procedure is repeated 1000 times, and the standard deviations of the PCA components are finally calculated." (Effect of noise)
3. **Gas temperature of outflow blobs**: Non-LTE LVG analysis of H2CO lines at blobs A-D and center  
  > "The gas kinematic temperature for each blob is evaluated from the detected H$_{2}$CO lines under the non-LTE (local thermodynamic equilibrium) method assuming the large velocity gradient (LVG) approximation." (4.1 PCA of the whole structure)
   - fitting: _not stated_
   - validation: _not stated_
4. **c-C3H2/H2CO column density ratio**: RADEX at c-C3H2 peaks using H2CO Ka=0 only  
  > "We employ only the H$_{2}$CO ($K_a=0$) line to estimate the column density of H$_{2}$CO" (5 Comparison)
   - software: RADEX
   - parameter: H2 density 1e6 cm^-3; Tkin 20-40 K  
  > "the H$_2$ density 10$^6$ cm$^{-3}$, and the gas kinematic temperature from 20 K to 40 K" (5 Comparison)
   - assumption: H2CO ortho/para ratio = 3  
  > "the ortho para ratio of H$_{2}$CO is 3 (statistical value)" (5 Comparison)
   - fitting: _not stated_
   - validation: ratio computed at same temperature to mitigate temperature dependence  
  > "In this case, the temperature dependence is mitigated." (5 Comparison)

## Software

- **CASA** : imsmooth and CLEAN imaging  
  > "$imsmooth$, which is the task of the Common Astronomy Software Applications package (CASA)" (Observation)
- **numpy, matplotlib, pandas, astropy** : custom PCA code  
  > "We write the code for the PCA by using python libraries, $numpy, matplotlib, pandas$, and $astropy$." (Principal Component Analysis)
- **RADEX** : column densities of c-C3H2 and H2CO  
  > "by using the RADEX code (cite: van der Tak et al.(2007))" (5 Comparison)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 0.8 mm continuum peak intensity (Cycle 3) | 23.95 | 0.48 | mJy/beam | 1 | whose peak intensity is 23.95$\pm$0.48mJy beam$^{-1}$ |
| PC1 contribution ratio (whole structure) | 42.1 | not stated | % | 2 | PC1 and PC2 have the two largest contribution ratios, 42.1 % and 20.3 %, respectively. |
| PC2 contribution ratio (whole structure) | 20.3 | not stated | % | 2 | PC1 and PC2 have the two largest contribution ratios, 42.1 % and 20.3 %, respectively. |
| PC1+PC2 contribution (disk/envelope) | 76.7 | not stated | % | 2 | On the disk/envelope scale, PC1 and PC2 stand for 76.7 % of the contribution ratio. |
| Gas kinematic temperature of blobs | 43 to 63 | 2-4 | K | 3 | The derived gas kinematic temperature ranges from 43 K to 63 K (Table [8](#tempvalue)). |
| c-C3H2/H2CO ratio NW / SE | 0.2-0.3 / 0.1-0.2 | not stated | dimensionless | 4 | The ratios for the northwestern and southeastern sides are from 0.2 to 0.3 and from 0.1 to 0.2, respectively. |

## Qualitative findings

- Higher-Ka H2CO lines are more compact around the protostar (PC2 increases with Ka).  
  > "This trend represents that the emissions of the higher excitation lines (i.e., higher $K_a$ lines) tend to be more concentrated around the protostar." (4.2)

## Claim tuples

- H: PCA can classify line distributions on the disk/envelope scale | E: PCA of 14 lines + continuum | R: PC2 separates compact (SO, CH3OH, high-Ka H2CO) from extended (CCH, CS, low-Ka H2CO) distributions | F: PCA is effective for extracting distribution features without bias | **supported**
- H: Outflow blobs are shocked | E: LVG analysis of H2CO at four blobs | R: Tkin 43-63 K | F: Blobs likely local shocks from outflow impact on clumps | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Many lines are hard to characterize one-by-one and line selection can bias interpretation  
  > "physical and chemical structures are often explored by using only a few selected lines, where interpretations could be biased by the selection." (Introduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Cycle 3 velocities shifted by 2.5 km/s; extended structure beyond 2.5" resolved out; PCA result depends on field range  
  > "the velocity of all spectral windows is blue-shifted by 2.5 km s$^{-1}$ due to the fault in the observation setting." (Observation); "the result of the PCA depends on the field range which we select." (Summary)
- Caveat (inferred, ours): Negative eigenvalues in the correlation matrix arise from pixel-pair thresholding and are not discussed
- Caveat (inferred, ours): Temperature fits have limited line constraints and unstated density
- Caveat (inferred, ours): Pixel-wise correlated noise after smoothing is not treated beyond MC

## Reproducibility

- Data public (paper): ALMA projects 2013.1.01157.S and 2015.1.01380.S acknowledged  
  > "This paper makes use of the following ALMA data set: ADS/JAO.ALMA#2013.1.01157.S and #2015.1.01380.S (PI: Yoko Oya)." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version
- Missing: line-free channels and moment integration ranges
- Missing: PCA code not released
- Missing: LVG setup details
- Data volume (inferred): ~20-50 GB
- Score (inferred): 3/5, Imaging recipe partly given and PCA well described, but calibration, moment ranges and LVG setup missing.
- Rediscovery candidate: yes, Archival data, PCA fully described, numeric tables of correlation matrices and eigenvalues available for checking.

## Links

- Method: Jolliffe(1986) (PCA method)
- Method: Spezzano et al.(2017) (PCA applied to L1544 chemical structure)
- Companion: Okoda et al.(2018) (Cycle 2 data and SO Keplerian disk)

## Checks

```json
{
 "quotes": 56,
 "quotes_ok": 56,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 65,
  "stated": 35,
  "rate": 0.538
 },
 "evidence_ok": true
}
```
