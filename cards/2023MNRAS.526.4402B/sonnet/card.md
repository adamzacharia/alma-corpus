# Fragmentation and dynamics of dense gas structures in the proximity of massive young stellar object W42-MME

`2023MNRAS.526.4402B` | Monthly Notices of the Royal Astronomical Society 2023 | first author: Bhadari, N. K. | arXiv: 2309.16472 | DOI: 10.1093/mnras/stad2981

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation, milky_way_ism
- Question: How do dense gas structures around the MYSO W42-MME fragment and what are their dynamics (turbulence, virial state, infall) from core to sub-parsec scales?  
  > "We performed a dendrogram analysis of H$^{13}$CO$^{+}$ (4–3) line data to study multi-scale structures and their spatio-kinematic properties" (abstract)
- Target **W42-MME**: coordinates _not stated_; z/distance 3.8 kpc  
  > "where $D(=3.8 \times 10^{3})$ pc is the distance of W42." (3.2 Physical parameters of dendrogram structures); distance from _not stated_

## Data provenance

- ALMA projects: 2018.1.01318.S, 2019.1.00195.L
- bands: Band 7 (line and 865 um continuum); 1.35 mm continuum for large-area view  
  > "data obtained from the ALMA in Band 7" (Alma Data Sets)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.31" x 0.25" (lines); ~1.2" x 1.1" (1.35 mm)  
  > "The observed data has a beam size of 0$''$.31$\times$ 0$''$.25." (Alma Data Sets)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: 2018.1.01318.S PI Dewangan; 2019.1.00195.L public archive (PI Molinari)  
  > "the publicly available ALMA continuum map at 1.35 mm" (Alma Data Sets)
- Line: H13CO+ 4-3 (~346.998 GHz)
- Line: H12CO+ 4-3 (~356.734 GHz)
- Line: CH3CCH 21_K-20_K (~358.709-818 GHz)
- Other facility **VLT/NACO**: Ks-band adaptive-optics image (2.18 um, ~0.2")  
  > "The high-resolution Very Large Telescope (VLT) NAOS-CONICA (NACO) NIR adaptive-optics image at $K_{s}$ band" (Alma Data Sets)
- External data: ALMA 865 um continuum map and data reduction  
  > "we have utilized the ALMA continuum data at 865 $\mu$m ($\nu\sim$346.5 GHz) from (cite: Dewangan2022)" (Alma Data Sets) [from (cite: Dewangan2022)]
- External data: VLT/NACO Ks image  
  > "is also utilized from (cite: Dewangan2015b)" (Alma Data Sets) [from (cite: Dewangan2015b)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 0.048" per pixel  
  > "1 pixel= 0$''$.048" (3.1.1 Structure Identification)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.31" x 0.25"  
  > "The observed data has a beam size of 0$''$.31$\times$ 0$''$.25." (Alma Data Sets)
- final rms: 1.6-3 mJy/beam, mean 2.3 mJy/beam (line channels)  
  > "the local noise (or rms) varies from 1.6 to 3 mJy beam$^{-1}$ with mean value of $\sigma_{\rm rms}$=2.3 mJy beam$^{-1}$" (3.1.1 Structure Identification)

### Inherited from earlier work

- Data acquisition and reduction  
  > "The details of data acquisition and reduction are given in (cite: Dewangan2022)." (Alma Data Sets) [from (cite: Dewangan2022)]
- Dendrogram method  
  > "The dendrogram methodology, as described by (cite: Rosolowsky2008)" (3.1 Dendrogram analysis) [from (cite: Rosolowsky2008)]
- Filling-factor correction of sizes  
  > "We have also taken account of the filling factor ($f$) as discussed in (cite: Liu2022)." (3.2 Physical parameters) [from (cite: Liu2022)]
- Moment-map uncertainties  
  > "derived using Equations 5 and 6 from (cite: Teague2019)" (3.2 Physical parameters) [from (cite: Teague2019)]

### Not stated but needed to reproduce (our reading)

- CASA version, calibration and imaging parameters (in Dewangan2022)
- Spectral channel width and cube velocity resolution used for dendrogram
- Primary beam correction and continuum subtraction details
- Fitting method for power laws and line profile Gaussians
- Line-free channels and continuum bandwidth
- Which dendrogram structures lacked temperatures and what T was adopted for them in mass

## Analysis recipe

1. **Dendrogram structure identification**: astrodendro on H13CO+ (4-3) p-p-v cube  
  > "The algorithm ultimately identified 19 structures including 7 branches and 12 leaves." (3.1.1 Structure Identification)
   - software: astrodendro
   - parameter: min_value = 3 sigma = 7 mJy/beam; min_delta = 1 sigma = 2.3 mJy/beam; min_npix = 74 pixels  
  > "“min_npix” was set to be 74 pixels (1 pixel= 0$''$.048)." (3.1.1 Structure Identification)
   - fitting: _not stated_
   - validation: _not stated_
2. **Kinetic temperature from CH3CCH**: Rotation diagram of K=0-4 lines on averaged spectra per structure; T=-1/slope  
  > "The slope a of the fitted straight line, $y = ax+b$, is related to the kinetic temperature, $T_{\rm kin}= -\frac{1}{a}$" (3.2.1)
   - fitting: straight-line fit to rotation diagram  
  > "The slope a of the fitted straight line, $y = ax+b$, is related to the kinetic temperature, $T_{\rm kin}= -\frac{1}{a}$" (3.2.1 Dense gas temperature ($T_{\rm kin}$) estimation)
   - validation: _not stated_
3. **Masses, virial parameters, Mach numbers**: Optically thin dust mass from 865 um flux; virial mass with density profile and geometry factors; sigma_nt from sigma_obs minus thermal  
  > "Using the derived gas temperatures in Section [3.2.1](#sec:temp), $D=3.8$ kpc, and $R_t=100$ (cite: Weingartner2001)" (3.2.2)
   - parameter: kappa = 10 (nu/1.2 THz)^1.5 -> 1.55 cm2/g at 346.58 GHz; rho ~ r^-1.6; mu=30 (H13CO), 2.37 for c_s  
  > "We therefore used $k^{865 \mu m}_{\rm 346.58~GHz}$= 1.55 cm$^{2}$ g$^{-1}$ for the mass estimation." (3.2.2)
   - assumption: gas-to-dust ratio 100; spherical symmetry; distance 3.8 kpc  
  > "We used the assumption of spherical symmetry for the dense cores that were identified" (3.2.2)
   - fitting: _not stated_
   - validation: _not stated_
4. **Infall asymmetry**: Asymmetry parameter A=(Vthick-Vthin)/DeltaVthin from Gaussian fits to leaf-averaged HCO+ lines  
  > "We estimated the $V_{\rm thick}$, $V_{\rm thin}$, and $\Delta V_{\rm thin}$ from the Gaussian fitting of spectral profiles." (3.2.3)
   - fitting: Gaussian fits  
  > "We estimated the $V_{\rm thick}$, $V_{\rm thin}$, and $\Delta V_{\rm thin}$ from the Gaussian fitting of spectral profiles." (Spectral profiles of dendrogram leaves)
   - validation: _not stated_
5. **Scaling relations and velocity structure function**: Power-law fits of dV-L, sigma_nt-L, M-R, n-R with Pearson correlation; second-order VSF from moment-1 map  
  > "the total range of angular separations (i.e., 0$''$.05–19$''$.2) were divided into sub-ranges (or lags) of 0$''$.13" (3.4.2)
   - parameter: VSF uses pixels with peak > 0.01 Jy/beam and FWHM < 2.5 km/s (7566 points)  
  > "the total number of data points were 7566" (3.4.2)
   - fitting: power-law fits; PCC r and p  
  > "The best fit power-law has the form $\delta\mathit{V_{\rm lsr}}=(0.20\pm0.06)\times L^{0.46\pm0.14}$" (Scaling relations from Dendrogram Structures)
   - validation: _not stated_
6. **Dust continuum cores**: Dendrogram on 865 um map, then masses and virial parameters  
  > "the parameters “min_value” and “min_delta” were set to be 0.5 mJy beam$^{-1}$ and 0.2 mJy beam$^{-1}$, respectively." (3.5)
   - software: astrodendro
   - assumption: mean gas temperature 54 K  
  > "we used a mean gas temperature of 54 K" (3.5)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **astrodendro** : Dendrogram structure identification  
  > "we utilized the python-based *astrodendro*[^2] package" (3.1)
- **Astropy** : general analysis  
  > "This work made use of Astropy" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of dendrogram structures | 19 (12 leaves, 7 branches) | not stated | dimensionless | 1 | Our results reveal 19 dense gas structures, out of which 12 are leaves and 7 are branches |
| Leaf Tkin range | 33-70 (mean 54.27) | not stated | K | 2 | The temperature estimates for leaf structures ranged from 33 to 70 K, with the mean (median) values of 54.27 (61.84) K |
| dV_lsr-L power-law index | 0.46 | 0.14 | dimensionless | 5 | $\delta\mathit{V_{\rm lsr}}=(0.20\pm0.06)\times L^{0.46\pm0.14}$ |
| sigma_nt-L exponent | -0.31 | 0.14 | dimensionless | 5 | scaling exponents of $-$0.31$\pm$0.14 |
| VSF global exponent | 0.40 | 0.01 | dimensionless | 5 | $S_{2}(l)^{1/2}=(0.34\pm0.01)\times l^{0.40\pm0.01}$ |
| VSF exponent below ~6000 AU | 0.73 | 0.01 | dimensionless | 5 | $S_{2}(l)^{1/2}=0.23\times l^{0.73\pm0.01}$ |
| M-R power-law index | 1.73 | 0.23 | dimensionless | 5 | $M\propto R_{\rm eff}^{1.73\pm0.23}$ |
| Number of 865 um dust cores | 14 | not stated | dimensionless | 6 | The analysis resulted in the identification of 14 cores. |

## Qualitative findings

- Blue asymmetry in H12CO+ profiles of most leaves indicates infall  
  > "have positive $A$ values, indicating a blue asymmetry, which is suggestive of infall" (3.2.3)

## Claim tuples

- H: Are dense structures near W42-MME turbulent and gravitationally bound? | E: Dendrogram of H13CO+ with virial analysis | R: Mach 1-5, alpha_vir >= 2 (overvirial) | F: Transonic-supersonic, overvirial structures | **supported**
- H: Does L17 satisfy conditions for massive star formation? | E: Mass-size comparison to Kauffmann & Pillai threshold | R: Only L17 lies above threshold | F: L17 meets mass-size conditions | **supported**
- H: Hierarchical and chaotic collapse explains kinematics | E: Scaling relations, VSF, asymmetry | R: Weak negative sigma_nt-L, infall signatures | F: Observations support hierarchical chaotic collapse | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Mass uncertain by factor of few from dust emissivity; interferometric missing flux and gas-to-dust ratio may bias masses  
  > "the interferometric observations are sensitive to strong and compact sources but miss more diffuse and extended emission" (3.5)
- Caveat (inferred, ours): Only 19 structures so correlations have low statistics
- Caveat (inferred, ours): Large virial parameters may result from masses underestimated by missing flux
- Caveat (inferred, ours): Dendrogram parameters affect results; no robustness test
- Caveat (inferred, ours): Single-distance assumption with no uncertainty

## Reproducibility

- Data public (paper): ALMA data public via JVO archive  
  > "are available from the publicly accessible JVO ALMA FITS archive" (DATA AVAILABILITY)
- Products in archive: _not stated_
- Missing: Calibrated cubes and continuum reduction details (in Dewangan2022)
- Missing: Fit procedures and uncertainty methods
- Data volume (inferred): ~10-50 GB
- Score (inferred): 6/5, Public data and well-specified dendrogram parameters, but reduction and fitting details are deferred or missing.
- Rediscovery candidate: yes, Public data, explicit dendrogram parameters and numeric results.

## Links

- Method: (cite: Rosolowsky2008) (dendrogram method)
- Method: (cite: Liu2022) (filling factor correction)
- Companion: (cite: Dewangan2022) (original ALMA data reduction and W42-MME study)

## Checks

```json
{
 "quotes": 52,
 "quotes_ok": 52,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 34,
  "rate": 0.442
 },
 "evidence_ok": true
}
```
