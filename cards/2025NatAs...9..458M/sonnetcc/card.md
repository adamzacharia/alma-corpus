# The evolution of dust attenuation in z ≈ 2-12 galaxies observed by JWST

`2025NatAs...9..458M` | Nature Astronomy 2025 | first author: Markov, Vladan | arXiv: 2402.05996 | DOI: 10.1038/s41550-024-02426-1

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies
- Question: How the dust attenuation law (slope and UV bump strength) of star-forming galaxies evolves from z ~ 2 to 12, and what this implies for intrinsic dust properties and dust-to-star geometry  
  > "to investigate evolutionary trends of dust attenuation laws and their implications on the intrinsic dust properties and dust-to-star geometry." (Introduction)
- Target **173 dusty JWST NIRSpec galaxies at z ~ 2-11.4 (69 of them in GOODS-South, Abell 2744 and RXJ 2129 fields; 62 with ALMA coverage)**: coordinates _not stated_; z/distance spectroscopic redshifts 2.0 to 11.4, median z ~ 4.5  
  > "The remaining 69 sources of our JWST sample are distributed across the GOODS-South (50), Abell 2744 (17), and RXJ 2129 (2) fields." (Methods, FIR observations); "Out of these 69 galaxies, ALMA data is available for 62 of them." (Methods, FIR observations); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00543.S, 2012.1.00173.S, 2015.1.00098.S, 2017.1.00755.S, 2022.1.00073.S, 2018.1.00035.L
- bands: 1.1-1.3 mm surveys (ALMA, archival)  
  > "1.1-1.3 mm surveys." (Methods, FIR observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Existing survey datasets: GOODS-ALMA, ALMA HUDF, HUDF-JVLA-ALMA, GOODS-S, MOSAIC-D, Abell_2744; no new ALMA observations  
  > "Despite the accessibility of ALMA data for these 62 sources, none of them have produced statistically significant detections across the various surveyed datasets." (Methods, FIR observations)
- Other facility **JWST NIRSpec prism (via DAWN JWST Archive)**: Public Cycle 1 and 2 prism spectra, R ~ 30-300, 0.6-5.3 um, used for the SED fitting that yields the attenuation curves  
  > "We use publicly available Near Infrared Spectrograph (NIRSpec) data retrieved from the DAWN JWST Archive (DJA)" (Methods, Spectroscopic data); "Here, we focus on the analysis of NIRSpec prism spectra." (Methods, Spectroscopic data)
- Other facility **HST, JWST NIRCam and NIRISS photometry**: Photometry extracted with the DJA Python tool, used to correct NIRSpec slit losses  
  > "we utilise the Python tool by DJA" (Methods, Slit-loss correction)
- External data: Literature S and B values for local, nearby and intermediate-z galaxy samples, adopted for comparison with the measured S and B  
  > "are directly adopted from the work of Salim & Narayanan (2020)" (Methods, Comparison with the literature) [from Salim & Narayanan (2020) (cite: 2020ARA&A..58..529S)]
- External data: Local reference attenuation/extinction curves (Calzetti, SMC, MW) used as comparison and as templates in model comparison  
  > "Dust attenuation can be modelled using standard empirical templates" (Methods, SED fitting) [from (cite: 2000ApJ...533..682C; 2003ApJ...594..279G; 1989ApJ...345..245C)]
- External data: Detection of the 2175 A bump and its parameters in JADES-GS-z6-0, compared with the authors' own measurement  
  > "reported a UV bump detection (with a $6.4\sigma$) in the JADES-GS-z6-0 galaxy" (Methods, Comparison with the literature) [from Witstok et al. (2023) (cite: 2023Natur.621..267W)]

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
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Target selection (visual inspection of grade 3 prism spectra, continuum and nebular lines required) follows earlier work  
  > "Our target selection process closely follows the one outlined in our recent work" (Methods, Sample selection) [from (cite: 2023A&A...679A..12M)]
- Prior probability densities of the SED model nearly identical to the initial work, with expanded limits  
  > "the selected prior probability densities for model parameters are nearly identical to those of our initial work" (Methods, SED fitting) [from (cite: 2023A&A...679A..12M)]
- Customized BAGPIPES SED fitting code and its testing on synthetic spectra  
  > "Our tool has been thoroughly tested on synthetic spectra attenuated by empirical dust curves" (Methods, SED fitting) [from (cite: 2023A&A...679A..12M)]
- Parameterization of attenuation curve shape by S and B  
  > "we employ the parameterization introduced by Salim & Narayanan (2020)" (Methods, Attenuation curve parametrization) [from (cite: 2020ARA&A..58..529S)]

### Not stated but needed to reproduce (our reading)

- The ALMA data reduction, calibration, imaging and any flux or upper-limit values for the 62 sources are not given; the paper only reports non-detections
- How the non-detection was assessed (aperture, noise level, significance threshold) for ALMA is not stated
- Full prior table lives in Supplementary Table 1, not in the main text; list of the 173 source IDs and DJA data version/date not given
- Which JWST throughput was chosen for each slit-loss correction (visual choice) is not tabulated
- Customized BAGPIPES code modifications are not released; Calzetti-like and c4=0 comparison model priors are not given
- MultiNest settings (live points, tolerance) not stated

## Analysis recipe

1. **Assemble and select NIRSpec prism spectra**: Take public DJA prism spectra, inspect grade 3 spectra visually, keep z>2 sources with S/N>3 in rest-frame 1925-2425 A, discard poor SED fits and near-zero attenuation sources  
  > "We conduct a visual inspection of all grade 3 NIRSpec prism spectra" (Methods, Sample selection); "We select sources at $z>2$ to ensure that we can effectively probe the rest-frame UV-optical wavelength range" (Methods, Sample selection)
   - software: GRIZLI, MSAEXP
   - parameter: average channel S/N > 3 in rest-frame 1925-2425 A  
  > "We further clean our sample by selecting spectra with an average channel Signal-to-Noise (S/N) ratio of $\mathrm{S/N} > 3$, in the rest-frame wavelength range of $1925-2425$ Å" (Methods, Sample selection)
   - parameter: dusty criteria: A_V > 0.1 and A_V/A_V^err > 3  
  > "(1) $V-$band dust attenuation of $A_V > 0.1$; (2) $A_V > 0$ with a significance of $> 3\mathrm{\sigma}$ ($A_V/A_V^{\rm{err}} > 3$)." (Methods, Sample selection)
   - assumption: Spectral region below Lyman alpha masked because of possible IGM contamination  
  > "is selectively masked due to the potential contamination by the intervening neutral intergalactic medium (IGM)." (Methods, Spectroscopic data)
   - fitting: _not stated_
   - validation: _not stated_
2. **Correct NIRSpec slit losses using photometry**: Compare spectra with HST/NIRCam/NIRISS photometry and divide by JWST documentation throughputs until spectrum and photometry align (visual)  
  > "we correct the spectrum by dividing it with one of the throughputs provided by the JWST user documentation" (Methods, Slit-loss correction)
   - software: DJA photometry tool
   - parameter: discrepancy found in 94% of sources, up to a factor of 6-9  
  > "It can reach up to a factor of $6-9$ in the most extreme cases of very extended and/or off-centred sources." (Methods, Slit-loss correction)
   - fitting: Alternative: uncertainty-weighted linear fit of f_phot/f_spec versus wavelength used to correct spectra  
  > "performing an uncertainty-weighted linear fit on these quantities." (Methods, Slit-loss correction)
   - validation: Trends unchanged with the alternative correction or with no slit-loss correction  
  > "remain consistent regardless of the application of slit-loss correction or the method employed for it." (Methods, Slit-loss correction)
3. **Fit each spectrum with customized BAGPIPES**: Bayesian SED fitting with non-parametric continuity SFH, two-component dust screen and the flexible analytical dust law with parameters c1-c4  
  > "We implement the analytical dust attenuation law" (Methods, SED fitting); "to account for extra attenuation toward the stellar birth clouds." (Methods, SED fitting)
   - software: BAGPIPES, CLOUDY, MultiNest
   - parameter: prior limits on UV bump parameter c4: -0.005 < c4 < 0.01  
  > "are set as $-0.005 < c_4 < 0.01$." (Methods, SED fitting)
   - parameter: k = 16 model parameters for the fiducial model  
  > "$k = 16$ for our fiducial model" (Methods, Statistical tests)
   - assumption: Bump central wavelength fixed at 2175 A and FWHM ~ 475 A  
  > "the dust attenuation model sets the central wavelength and FWHM of the UV bump at fixed values of $\lambda_0 = 2175$ Å and $\rm{FWHM} \sim 475$ Å, respectively." (Methods, SED fitting)
   - fitting: MultiNest nested sampling via BAGPIPES; priors in Supplementary Table 1  
  > "The prior probability distributions for each of the parameters of the model are given in Supplementary Table 1." (Methods, SED fitting)
   - validation: Visual inspection, residuals, reduced chi-square  
  > "we initially rely on visual inspection to assess how accurately the SED model captures the features and trends present in the observed spectra." (Methods, Statistical tests)
4. **Derive attenuation curves, S and B**: Build A_lambda/A_V from c1-c4; S = A1500/A_V and B = A_bump/A_2175, with the 2175 A baseline from the analytical fit with c4 = 0  
  > "we derive the 2175 Å baseline by fitting the dust curve with an analytical dust model" (Methods, Attenuation curve parametrization)
   - software: BAGPIPES
   - parameter: per-galaxy S and B uncertainty from 100 curves sampled from the posterior; median curves from 5000 bootstrapped curves  
  > "which involves generating 100 attenuation curves $A_{\lambda}/A_V$ from a random sampling of the $c_1-c_4$ parameters from the posterior." (Methods, Attenuation curve parametrization); "a set of 5000 attenuation curves that are generated using a bootstrapping approach" (Methods, Attenuation curve parametrization)
   - fitting: _not stated_
   - validation: c4 used as an alternative bump-strength proxy  
  > "we observe comparable trends in the redshift evolution of the UV bump strength" (Redshift evolution of the UV bump strength)
5. **Fit redshift trends of S and B**: Bin galaxies in equidistant cosmic time (~0.5 Gyr), take medians per bin, and fit log S vs log z and B vs z linearly  
  > "we split our sample in redshift bins by adopting equidistant cosmic time in each bin" (Redshift evolution of dust attenuation law); "The best-fit values for the model parameters" (Methods, Attenuation curve parametrization)
   - software: numpy polyfit
   - parameter: 13-66 sources per redshift bin  
  > "The number of sources per bin varies in the 13-66 range." (Redshift evolution of dust attenuation law)
   - fitting: numpy polyfit (least squares polynomial), 1 sigma errors propagated  
  > "uncertainties are obtained using a" (Methods, Attenuation curve parametrization)
   - validation: Trends checked in A_V subsets and versus M*, SFR, Z, age and U  
  > "but the overall trends remain regardless of the considered parameters" (Redshift evolution of the slope)
6. **Compare fiducial model with Calzetti-like and bump-free fits**: Reduced chi-square and p-values of the fiducial flexible model against a Calzetti-like template fit and a c4 = 0 model  
  > "We compared the quality of fits between our fiducial model, featuring a flexible analytical dust attenuation model, and a SED fitting model using a Calzetti-like dust attenuation template" (Methods, Statistical tests)
   - software: BAGPIPES
   - fitting: _not stated_
   - validation: Fiducial model better in 148 of 173 sources (p < 0.05) and in 24 of 28 bump-detected sources  
  > "performs significantly better for 148 out of 173 sources" (Methods, Statistical tests)
7. **Check for ALMA far-infrared detections**: Check which sources fall in fields covered by existing ALMA surveys (62 of 69 sources with delta < 20 deg) and whether any are detected  
  > "Out of these 69 galaxies, ALMA data is available for 62 of them." (Methods, FIR observations)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **BAGPIPES** : Customized version for Bayesian SED fitting of spectra with flexible dust attenuation law  
  > "is a Bayesian SED fitting code that generates realistic galaxy spectra using the Stellar Population Synthesis (SPS) models" (Methods, SED fitting)
- **MultiNest** : Nested sampling algorithm used by BAGPIPES  
  > "is based on a Bayesian approach and the MultiNest nested sampling algorithm" (Methods, SED fitting)
- **CLOUDY** : Pre-computed nebular emission models and warm dust emission in HII regions  
  > "nebular emission models pre-computed with" (Methods, SED fitting)
- **GRIZLI** : Uniform reduction of the JWST data in DJA  
  > "Grism redshift and line analysis software for space-based slitless spectroscopy" (Methods, Spectroscopic data)
- **MSAEXP** : Extraction of NIRSpec MSA spectra in DJA  
  > "Tool for extracting JWST NIRSpec Micro-Shutter Assembly (MSA) spectra" (Methods, Spectroscopic data)
- **numpy polyfit** : Linear fits of log S versus log z and B versus z  
  > "uncertainties are obtained using a" (Methods, Attenuation curve parametrization)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Final sample of dusty galaxies | 173 | not stated | galaxies | 1 | We ended up with a final sample of 173 |
| Median A_V of the sample | ~0.38 | not stated | mag | 3 | our overall JWST sample has a median $A_V$ of $\sim 0.38$ |
| Sources with UV bump detected at >3 sigma via B | 28 | not stated | galaxies | 4 | for 28 sources, within the |
| Fraction with secure bump detection via c4 | ~21% | not stated | percent | 4 | we obtain a securely detected UV bump in $\sim 21\%$ of the sources |
| UV bump strength B of 1433_3989 (z ~ 6.14) | 0.43 | 0.05 | dimensionless | 4 | $B = 0.43 \pm 0.05$ ($>9\sigma$) or $c_4 = 0.083 \pm 0.014$ ($>6\sigma$) |
| c4 of 1433_3989 | 0.083 | 0.014 | dimensionless | 4 | $B = 0.43 \pm 0.05$ ($>9\sigma$) or $c_4 = 0.083 \pm 0.014$ ($>6\sigma$) |
| UV bump strength B of 2750_449 (z ~ 7.55) | 0.34 | 0.10 | dimensionless | 4 | $B = 0.34 \pm 0.10$ ($> 3\sigma$) or $c_4 = 0.054 \pm 0.025$ ($> 2\sigma$) |
| c4 of 2750_449 | 0.054 | 0.025 | dimensionless | 4 | $B = 0.34 \pm 0.10$ ($> 3\sigma$) or $c_4 = 0.054 \pm 0.025$ ($> 2\sigma$) |
| Slope-redshift relation: slope coefficient k1 | -0.580 | 0.064 | dimensionless | 5 | \log{S} = (-0.580 \pm 0.064) \log{z} + (0.882 \pm 0.042) |
| Slope-redshift relation: intercept n1 | 0.882 | 0.042 | dimensionless | 5 | \log{S} = (-0.580 \pm 0.064) \log{z} + (0.882 \pm 0.042) |
| Bump-redshift relation: slope coefficient k2 | -0.020 | 0.05 | dimensionless | 5 | B = (-0.020 \pm 0.05) z + (0.167 \pm 0.025) |
| Bump-redshift relation: intercept n2 | 0.167 | 0.025 | dimensionless | 5 | B = (-0.020 \pm 0.05) z + (0.167 \pm 0.025) |
| Reduced chi-square distribution | 4.1 (range 1.5 to 6.3) | not stated | dimensionless | 3 | the distribution of $\chi_\nu^2$ is in the range of $\chi_\nu^2 = 4.1_{1.5}^{6.3}$ |
| Sources where fiducial model beats Calzetti-like model at p < 0.05 | 148 of 173 (~86%) | not stated | galaxies | 6 | performs significantly better for 148 out of 173 sources |
| ALMA-detected sources among 62 with ALMA coverage | 0 | not stated | galaxies | 7 | none of them have produced statistically significant detections across the various surveyed datasets. |

## Qualitative findings

- Attenuation slope flattens and UV bump weakens with increasing redshift, independent of A_V; interpreted as dominance of large grains from SNII dust at early epochs  
  > "Our results show that the attenuation law evolves with redshift." (Discussion); "The redshift evolution of $S$ and $B$ (or $c_4$) we find supports the third scenario." (Discussion)
- Highest-redshift reliable UV bump detection is at z ~ 6.14 (both B and c4), and at z ~ 7.55 with B only  
  > "the highest redshift galaxy of our JWST sample with a reliable UV bump detection is the 1433_3989 source at $z \sim 6.14$" (Redshift evolution of the UV bump strength)

## Claim tuples

- H: Dust attenuation curves evolve with redshift at z ~ 2-12 | E: SED fit 173 JWST NIRSpec prism spectra with a flexible dust law and bin by redshift | R: Median slope flattens and bump weakens with increasing redshift | F: The attenuation law evolves with redshift | **supported**
- H: The redshift evolution of the slope is driven by A_V (radiative transfer with attenuation amount) | E: Repeat the S versus z fits in A_V subsets | R: Flattening toward high z persists in every A_V range | F: A_V is not the driver of the evolution | **refuted**
- H: Changes in intrinsic dust properties (grain size, composition) explain the trends rather than dust-to-star geometry | E: Compare trends with scenarios and published dust-evolution models | R: Shallow slopes and weak bump at z > 5.5 consistent with large SNII grains | F: Third scenario (changing grain properties) is supported; geometry alone seems unlikely | **partially**
- H: Galaxies in the sample may be detectable in FIR dust continuum with ALMA | E: Search existing ALMA survey data for the 62 sources with coverage | R: No statistically significant detections | F: ALMA provides no constraint here | **refuted**

## Reasoning

- Why this data: _not stated_
- Why this method: Flexible analytical dust law reproduces local empirical curves and allows recovery of unconventional curves in early galaxies  
  > "The main advantage of this flexible dust model is its capability to replicate local empirical dust curves" (Methods, SED fitting)
- Alternative: Scenario 1 (A_V-dependent radiative transfer) rejected; scenario 2 (complex dust-to-star geometry) judged unlikely  
  > "We can then rule out the first scenario." (Discussion); "Thus, scenario (2) seems unlikely." (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): B is poorly constrained with high uncertainties due to error propagation  
  > "is not well constrained and exhibits high uncertainties due to error propagation." (Redshift evolution of the UV bump strength)
- Limitation (authors): Fixed bump central wavelength and width may limit capturing bump variations at high z  
  > "This restriction might limit the model’s ability to capture variations of these UV bump parameters" (Methods, SED fitting)
- Limitation (authors): At z ~ 2-2.8 prism coverage restricts rest-frame wavelengths, increasing slope uncertainty  
  > "This constraint in wavelength coverage may contribute to larger uncertainties in inferred slopes" (Methods, Observational and model uncertainties)
- Caveat (inferred, ours): ALMA plays no role in the conclusions (only non-detections reported), so ALMA reproducibility is essentially empty
- Caveat (inferred, ours): Slit-loss correction by visual choice of throughput is subjective
- Caveat (inferred, ours): Dust curve degeneracy with SFH and metallicity in low-resolution prism spectra
- Caveat (inferred, ours): Sample is public-archive selected, with possible selection biases
- Caveat (inferred, ours): Median S/B at high z depend on prior limits of c4

## Reproducibility

- Data public (paper): JWST data public via DAWN JWST Archive  
  > "The data that support the findings of this study are available at" (Data availability)
- Products in archive: _not stated_
- Code: GRIZLI, MSAEXP and BAGPIPES scripts are public; customized BAGPIPES not stated as released  
  > "Python scripts are publicly available at" (Code availability)
- Missing: Customized BAGPIPES version with the Li08 dust law and its priors (Supplementary Table 1)
- Missing: Per-source slit-loss throughput choice and final sample ID list
- Missing: ALMA data processing details and flux limits
- Data volume (inferred): Small for the JWST spectra (1D spectra from DJA, well under 1 GB); ALMA data not needed for the main results
- Score (inferred): 3/5, Public DJA spectra and clear definitions of S, B and fit relations, but customized code, Supplementary priors and per-source slit-loss choices are not available in the text; ALMA part is only non-detections
- Rediscovery candidate: no, ALMA is a minor element; the main JWST analysis relies on a customized, unreleased code version and visual slit-loss corrections

## Links

- Method: Markov et al. 2023 (cite: 2023A&A...679A..12M) (Customized BAGPIPES SED fitting tool and priors)
- Method: Salim & Narayanan 2020 (cite: 2020ARA&A..58..529S) (Definitions of S and B parameters)
- Method: Carnall et al. 2018 (cite: 2018MNRAS.480.4379C) (BAGPIPES code)
- Companion: Fujimoto et al. 2023 (cite: 2023arXiv230907834F) (MOSAIC-D ALMA survey of Abell 2744)
- Companion: Franco et al. 2018 (cite: 2018A&A...620A.152F) (GOODS-ALMA survey)
- Companion: Witstok et al. 2023 (cite: 2023Natur.621..267W) (Earlier 2175 A bump detection in JADES-GS-z6-0)
- Related: GOODS-ALMA
- Related: ALMA Hubble Ultra Deep Field
- Related: HUDF-JVLA-ALMA
- Related: MOSAIC-D
- Related: Abell_2744 ALMA
- Related: DAWN JWST Archive

## Checks

```json
{
 "quotes": 88,
 "quotes_ok": 88,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 6,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 15,
 "numeric_problems": 0,
 "fill": {
  "facts": 95,
  "stated": 52,
  "rate": 0.547
 },
 "evidence_ok": true
}
```
