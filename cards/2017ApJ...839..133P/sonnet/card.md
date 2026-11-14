# Variation in GMC Association Properties across the Bars, Spiral Arms, Inter-arms, and Circumnuclear Region of M100 (NGC 4321) Extracted from ALMA Observations

`2017ApJ...839..133P` | The Astrophysical Journal 2017 | first author: Pan, Hsi-An | arXiv: 1702.04124 | DOI: 10.3847/1538-4357/aa60c2

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: nearby_galaxies, milky_way_ism
- Question: How do GMA (giant molecular cloud association) properties and star formation activity vary across the circumnuclear ring, bar, spiral arm and inter-arm environments of M100?  
  > "To examine the environmental dependence of GMA properties, GMAs are classified based on their locations in the various environments as circumnuclear ring (CNR), bar, spiral, and inter-arm GMAs." (abstract)
- Target **M100 (NGC 4321)**: coordinates _not stated_; z/distance 14.3 Mpc  
  > "We use the distance obtained using Cepheids, 14.3 Mpc, yielding a linear scale of 1$\ensuremath{''}$ $=$ 69 pc (cite: Fre01)." (1 Introduction); "The adopted inclination and the position angle of the major axis are 27$^{\circ}$ and 153$^{\circ}$, respectively (cite: Kna93)." (1 Introduction); distance from Cepheids (Freedman et al. 2001)  
  > "We use the distance obtained using Cepheids, 14.3 Mpc, yielding a linear scale of 1$\ensuremath{''}$ $=$ 69 pc (cite: Fre01)." (1 Introduction); "The adopted inclination and the position angle of the major axis are 27$^{\circ}$ and 153$^{\circ}$, respectively (cite: Kna93)." (1 Introduction)

## Data provenance

- ALMA projects: 2011.0.00004.SV
- bands: Band 3 (115 GHz)  
  > "archival ALMA SV data at Band 3 (115 GHz; $^{12}$CO (1-0)) on M100" (2 Data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12-m + ACA (7-m + total power), feathered  
  > "The resulting image is feathered with the total power image to recover the extended emission." (2 Data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 3.87'' x 2.53'' (~267 x 174 pc), PA -89.51 deg  
  > "The spatial resolution of the map is 3.87$\ensuremath{''}$ $\times$ 2.53$\ensuremath{''}$ ($\sim$ 267 $\times$ 174 pc) and P.A. of -89.51$^{\circ}$." (2 Data)
- max recoverable scale: _not stated_
- sensitivity: rms ~0.015 Jy/beam per 5.023 km/s channel (~1e5 Msun per beam per channel)  
  > "The rms noise ($\sigma_{\mathrm{rms}}$) of the data cube is $\sim$ 0.015 Jy beam$^{-1}$" (2 Data)
- time on source: _not stated_
- observing dates: 12-m 2011, 7-m 2013, total power 2014  
  > "The ALMA 12-m, 7-m array, and total power observations were carried out in 2011, 2013, and 2014, respectively." (2 Data)
- pi or archival as stated: Archival ALMA Science Verification data  
  > "using the released Science Verification (SV) data of ALMA" (1 Introduction)
- Line: 12CO J=1-0 (115 GHz (as stated))
- Other facility **William Herschel Telescope (Halpha HII region catalogue)**: Halpha imaging; HII region catalogue of 1948 regions used for SFRs  
  > "From the image, (cite: Kna98) catalogued 1948 HII regions" (3.2 HII Regions and SFR of GMAs)
- External data: HII region catalogue and Halpha fluxes  
  > "The catalogue of HII regions is taken from (cite: Kna98)." (3.2 HII Regions and SFR of GMAs) [from (cite: Kna98)]
- External data: Halpha attenuation: 2.4 mag for CNR, 1.7 mag for bar and spiral  
  > "The value of $A\mathrm{_{H\alpha}}$ $=$ 2.4 mag is adopted for the CNR region, while $A\mathrm{_{H\alpha}}$ $=$ 1.7 mag[^3] is used for the bar and the spiral arms." (3.2 HII Regions and SFR of GMAs) [from (cite: Pre07)]
- External data: Outermost bar isophote used for bar classification  
  > "The outermost bar isophote determined by (cite: She01) is marked with an open ellipse" (4.1 GMA Classification) [from (cite: She01)]
- External data: Spiral arm ridge lines/width  
  > "The spiral arms of M100 are isolated from the **underlying stellar disc** with separate estimates from 3.6 $\mu$m, 4.5 $\mu$m and optical colour by (cite: Ken11)." (4.1 GMA Classification) [from (cite: Ken11)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Processed archival SV data (12-m+7-m+TP), reduction per CASA 4.3 guide  
  > "The full description of the data reduction and the combination of the three observing modes can be found in the Common Astronomy Software Applications (CASA 4.3) guide for this specific dataset" (2 Data)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5  
  > "The combined interferometric map is processed using the CLEAN algorithm with a robust $=$ 0.5 weighting (Briggs) of the visibilities." (2 Data)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: Applied to total flux (~3000 Jy after correction and TP addition)  
  > "it increases to $\sim$ 3000 Jy (after primary-beam correction) upon adding the total power data" (2 Data)
- array combination: 7-m and 12-m combined, then feathered with total power  
  > "In our study, the 7-m and 12-m interferometric data are combined first." (2 Data)
- smoothing: _not stated_
- final beam: 3.87'' x 2.53''  
  > "The spatial resolution of the map is 3.87$\ensuremath{''}$ $\times$ 2.53$\ensuremath{''}$" (2 Data)
- final rms: ~0.015 Jy/beam  
  > "The rms noise ($\sigma_{\mathrm{rms}}$) of the data cube is $\sim$ 0.015 Jy beam$^{-1}$" (2 Data)

### Inherited from earlier work

- Data reduction and 3-mode combination follow the CASA guide for M100 Band 3  
  > "The full description of the data reduction and the combination of the three observing modes can be found in the Common Astronomy Software Applications (CASA 4.3) guide for this specific dataset" (2 Data) [from CASA guide M100_Band3]
- CPROPS parameters m=4, e=1.5 for consistency with previous studies  
  > "To ensure consistency with previous studies, we set $m$ $=$ 4 and $e$ $=$ 1.5." (3.1 GMA identification) [from (cite: Ros06)]
- 50 bootstrap measurements  
  > "(cite: Col14) found that 50 bootstrapping measurements provide a reliable estimate of the uncertainty, and thus, this number is adopted in this work." (3.1 GMA identification) [from (cite: Col14)]
- Halpha SFR calibration  
  > "For the SFR of each HII region, the calibration of (cite: Cal07) is used" (3.2 HII Regions and SFR of GMAs) [from (cite: Cal07)]

### Not stated but needed to reproduce (our reading)

- CPROPS configuration details beyond m, e (e.g. distance/beam inputs, velocity-resolution handling, MAD noise estimation) and the version
- Exact CASA tasks, feathering parameters and the pipeline for the SV data (deferred to a CASA guide)
- Line-free channels and continuum subtraction
- Tables of GMA classification boundaries (ellipse, spiral ridge coordinates) in machine-readable form
- Details of the K-S fits per environment (weights, fit range)
- Exact definition of the two-sample t-test variant

## Analysis recipe

1. **Identify GMAs in the CO cube**: CPROPS cloud decomposition with watershed merge procedure disabled; reject edge GMAs, peaks <5 sigma and failed deconvolutions  
  > "Because of the limitation of the map resolution, we disable this procedure so that the local maxima are forcibly separated and form individual objects." (3.1 GMA identification)
   - software: CPROPS
   - parameter: m = 4, e = 1.5; peak search box ~660 pc x 660 pc x 15 km/s; 50 bootstraps  
  > "The search for the peaks is performed within a cube with a box with dimensions of $\sim$ 660 pc $\times$ 660 pc $\times$ 15 km s$^{-1}$" (3.1 GMA identification)
   - fitting: _not stated_
   - validation: Visual inspection of objects; checked overlap of adjacent GMAs  
  > "We also check the overlap between the edges of adjacent GMAs." (3.1 GMA identification)
2. **Derive GMA physical properties**: CPROPS extrapolation to 0 K; Mc from LCO with Xco; Rc=1.91 sigma_r; Sigma_H2=Mc/(pi Rc^2); sigma_c deconvolved by channel width; alpha_vir=1040 Rc sigma_c^2/Mc  
  > "$R_{\mathrm{c}}$ is calculated as $$\begin{equation}
R_{\mathrm{c}} = 1.91\sigma _{\mathrm{r}}\mathrm{(0K)}.
\end{equation}$$" (4.2.1)
   - software: CPROPS
   - assumption: Galactic Xco = 2e20 cm^-2 (K km/s)^-1 constant across environments; galaxy rotation ignored  
  > "A Galactic value of 2 $\times$ 10$^{20}$ cm$^{-2}$ (K km s$^{-1}$)$^{-1}$ is adopted in this work." (4.2.1)
   - fitting: _not stated_
   - validation: Bootstrap uncertainties  
  > "CPROPS uses bootstrapping of the assigned pixels to estimate the uncertainties of cloud properties." (GMA identification)
3. **Compute SFR of GMAs from HII regions**: Sum Halpha-based SFRs of catalogued HII regions inside GMA observed boundaries, with extinction correction  
  > "The SFR of a GMA is calculated by determining the sum of the SFRs of the HII regions within the GMA." (3.2)
   - parameter: SFR=5.3e-42 L(Halpha) x 10^(A/2.5); A=2.4 (CNR), 1.7 (bar, spiral), none in inter-arm  
  > "The inter-arm regions have little, if any, dust (cite: Kna96; Bec96), and therefore, extinction correction is not applied to the inter-arm HII regions." (3.2)
   - assumption: GMAs and HII regions coexist (no offset at this resolution)  
  > "Therefore, in this study, we assume that the GMAs and the HII regions coexist." (3.2)
   - fitting: _not stated_
   - validation: Total SFR compared with global H-alpha+24um SFR (~75%)  
  > "accounting for $\sim$ 75% of the global SFR derived from the H$\alpha$ + 24 $\mu$m data (cite: Wil09)" (3.2)
4. **Classify environments and compare distributions**: Classify GMAs as CNR (r<15''), bar, spiral, inter-arm; two-sample t-test between environments  
  > "the two-sample $t$-test is applied to check whether the average difference of a GMA property between two environments is really significant." (4.2)
   - fitting: _not stated_
   - validation: _not stated_
5. **Fit scaling relations and K-S relation**: Error-weighted least squares power-law fits with numpy polyfit; correlation coefficients with corrcoef  
  > "The error-weighted fit is performed utilizing the `POLYFIT` function of `PYTHON`’s `NUMPY` package." (4.2.1)
   - software: numpy
   - fitting: 1 sigma uncertainty from covariance matrix of fit  
  > "The 1$\sigma$ uncertainty is estimated from the covariance matrix of the fit." (4.2.1)
   - validation: _not stated_
6. **Test effect of missing flux using 12-m alone**: Repeat GMA identification on 12-m-only cube; match 70 GMAs by position and velocity  
  > "We identify 70 matched GMAs based on their position and velocity in the two data cubes." (6)
   - software: CPROPS
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.3: Data reduction/combination (via the CASA guide), CLEAN imaging  
  > "Common Astronomy Software Applications (CASA 4.3) guide for this specific dataset" (2 Data)
- **CPROPS** : Cloud identification and property measurement  
  > "The molecular cloud structures are identified by the cloud property algorithm CPROPS (cite: Ros06)." (3.1 GMA identification)
- **numpy (polyfit, corrcoef)** : Power-law fits and correlation coefficients  
  > "The correlation coefficients ($cc$) calculated by `corrcoef` of the `NUMPY` package" (4.2.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of GMAs | 165 | not stated | count | 1 | The final number of GMAs is 165, accounting for $\sim$ 55% of the total flux in the data cube. |
| GMAs per environment | 11 CNR, 21 bar, 62 spiral, 71 inter-arm | not stated | count | 4 | 11 CNR GMAs, 21 bar GMAs, 62 spiral GMAs, and 71 inter-arm GMAs |
| Median GMA mass | 8.8e6 | factor ~2 typical | Msun | 2 | The median mass of the GMAs is $\sim$ 8.8 $\times$ 10$^{6}$ M$_{\ensuremath{\odot}}$. |
| Total GMA mass | 2.5e9 | not stated | Msun | 2 | The total mass enclosed within the 165 GMAs is about 2.5 $\times$ 10$^{9}$ M$_{\ensuremath{\odot}}$. |
| Mass-size index a (all GMAs) | 1.01 | 0.14 | dimensionless | 5 | The best fit of $M_{\mathrm{c}}$ and $R\mathrm{_{c}}$ yields an $a$ value of 1.01 $\pm$ 0.14 with all GMAs. |
| sigma-R index b (all GMAs) | 0.10 | 0.11 | dimensionless | 5 | The best fit of all populations yields a power-law index of $b$ $=$ 0.10 $\pm$ 0.11. |
| K-S index N (all GMAs) | ~1.5 | not stated | dimensionless | 5 | An index of $N$ $\approx$ 1.5 is subsequently derived. |
| K-S index N by environment | ~1.7 bar, ~1.0 spiral and inter-arm, ~0.8 CNR | not stated | dimensionless | 5 | The power-law index $N$ decreases from a superlinear relation ($\sim$ 1.7) for the bar GMAs to an almost linear relation ($\sim$ 1.0) for the spiral and inter-arm GMAs, and to a sublinear relation ($\sim$ 0.8) for the CNR GMAs |
| Total SFR in GMAs | ~2 | factor ~2 from A_Halpha | Msun/yr | 3 | The total SFR in the 165 GMAs is $\sim$ 2 M$_{\ensuremath{\odot}}$ yr$^{-1}$ |
| 12-m-only GMA count | 100 | not stated | count | 6 | We identify a total of 100 GMAs and the total mass of the GMAs is $\sim$ 1.1 $\times$ 10$^{9}$ M$_{\ensuremath{\odot}}$ |

## Qualitative findings

- Only spiral GMAs are in general self-gravitating; alpha_vir spans nearly two orders of magnitude  
  > "Only the spiral GMAs are in general self-gravitating." (abstract)

## Claim tuples

- H: GMA properties depend on galactic environment | E: Compare Mc, Rc, Sigma, sigma_c across CNR/bar/spiral/inter-arm with t-tests | R: CNR GMAs massive and compact; inter-arm diffuse with low surface density; CNR and bar have higher sigma_c | F: GMA properties are not uniform among environments | **supported**
- H: Larson's relations hold for GMAs | E: Fit Mc-Rc and sigma-R | R: a=1.01+/-0.14 with varying slopes by environment; b=0.10+/-0.11 | F: Mass-size correlated but with diverse slopes; no sigma-size relation, diverse dynamical states | **partially**
- H: K-S relation is universal across environments | E: Fit Sigma_SFR vs Sigma_H2 per environment | R: N ~1.7 bar, ~1 spiral/inter-arm, ~0.8 CNR | F: Non-universal K-S relation | **supported**
- H: Missing flux affects environmental dependence | E: Compare feathered vs 12-m-only GMAs | R: 12-m-only finds 100 vs 165 GMAs, lower Mc and Rc, most inter-arm GMAs lost | F: Missing flux and extended emission cannot be neglected | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Object-based analysis chosen for reducing line-of-sight projection and eliminating diffuse low S/N emission  
  > "the object-based method is still useful in reducing the line-of-sight projection effect, eliminating diffuse and low S/N emission" (3 Identification of GMAs)
- Alternative: Variable Xco rejected: difference between disc and centre is small relative to Mc differences  
  > "Therefore, instead of adopting a variable $X_{\mathrm{CO}}$ for correcting a relatively small difference, a constant $X_{\mathrm{CO}}$ is adopted in this work." (5.6)
- How they decided it was enough: _not stated_
- Limitation (authors): alpha_vir is difficult to determine and should be interpreted with caution  
  > "We emphasize that $\alpha_{\mathrm{vir}}$ should be interpreted with caution when considering the dynamical state and environmental dependence of GMCs/GMAs." (5.5.2)
- Limitation (authors): GMCs not resolved; SFR may be a lower limit  
  > "As a result, the derived SFR may be a lower limit." (3.2)
- Caveat (inferred, ours): Constant Galactic Xco may bias Mc/SFE, especially in the CNR
- Caveat (inferred, ours): Resolution of ~200-270 pc means GMAs are not single clouds; results depend on CPROPS with watershed disabled
- Caveat (inferred, ours): t-test on non-Gaussian distributions with small CNR sample (11)
- Caveat (inferred, ours): Extinction correction uncertain by factor of 2 in SFR

## Reproducibility

- Data public (paper): Public ALMA Science Verification data with CASA guide  
  > "using the released Science Verification (SV) data of ALMA" (1 Introduction)
- Products in archive: _not stated_
- Missing: Exact CPROPS settings and version
- Missing: Machine-readable environment masks
- Data volume (inferred): ~10-50 GB (processed SV products much smaller)
- Score (inferred): 6/5, Public data and a catalogue table are given, with main parameters (robust, m, e, Xco, extinction), but environment masks and CPROPS details are incomplete.
- Rediscovery candidate: yes, Public data, standard CPROPS recipe and numeric results (slopes, counts, masses) available.

## Links

- Method: (cite: Ros06) (CPROPS algorithm)
- Method: (cite: Cal07) (SFR calibration)
- Companion: (cite: Pan15b; Pan16) (Synthetic observations of simulated galaxy on cloud property bias)
- Related: ALMA Science Verification M100

## Checks

```json
{
 "quotes": 66,
 "quotes_ok": 66,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 81,
  "stated": 47,
  "rate": 0.58
 },
 "evidence_ok": true
}
```
