# The ALPINE-CRISTAL-JWST Survey: Chemical Abundance Comparison between the ISM and CGM of Main-sequence Galaxies at z = 4─6

`2026ApJ..1000..308W` | The Astrophysical Journal 2026 | first author: Wang, Wuji | arXiv: 2602.20241 | DOI: 10.3847/1538-4357/ae4b38

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies
- Question: Do the chemical abundances (strong optical line ratios) of the ISM (<~3 kpc) and CGM (~5-10 kpc) differ in main-sequence galaxies at z=4-6?  
  > "We study the variation in chemical composition between the ISM ($\lesssim3\,$kpc) and CGM ($\sim5-10\,$kpc) for a sample of $M_{\star}>10^{9.5}\,M_{\odot}$ main-sequence galaxies at $4<z<6$" (abstract)
- Target **ALPINE-CRISTAL-JWST sample (18 main-sequence galaxies, COSMOS)**: coordinates _not stated_; z/distance z=4-6  
  > "We study the gas-phase chemical abundances in a sample of 18 star-forming main-sequence galaxies at $z=4-6$ as part of the ALPINE-CRISTAL-JWST sample" (2.1 ALPINE-CRISTAL-JWST sample); distance from flat Lambda-CDM, H0=70, Omega_m=0.3  
  > "We study the gas-phase chemical abundances in a sample of 18 star-forming main-sequence galaxies at $z=4-6$ as part of the ALPINE-CRISTAL-JWST sample" (2.1 ALPINE-CRISTAL-JWST sample)

## Data provenance

- ALMA projects: 2022.1.01118.S, 2019.1.00226.S, 2017.1.00428.L, 2021.1.00280.L
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: median beam ~0.36'' x 0.30''  
  > "The median synthesized beam size for the sample is $\theta_{\rm MAJ}\times\theta_{\rm MIN}\sim 0.36\ensuremath{''}\times0.30\ensuremath{''}$." (2.3 ALMA FIR observations)
- max recoverable scale: >~5''  
  > "The largest recoverable angular scale is $\gtrsim5\ensuremath{''}$ for the ALMA dataset which is larger than the focus of this work." (2.3 ALMA FIR observations)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: [C II] 158 um (not stated)
- Other facility **JWST NIRSpec IFU (GO-3045, GO-4265)**: Rest-frame optical emission-line cubes (G235M/G395M)  
  > "The NIRSpec/IFU data were observed through the program GO-3045." (2.2 JWST optical photometric and spectroscopic observations)
- Other facility **JWST NIRCam COSMOS-Web / HST WFC3**: Imaging used to define the ISM region  
  > "We use the NIRCam imaging of our sample, from the COSMOS-Web survey, as a proxy of the distribution of stars, thus the ISM of the galaxies." (3.1 The ISM region)
- External data: ALMA data processing and cubes from ALPINE and CRISTAL  
  > "The data processing of these ALMA data can be found in (cite: Bethermin_2023) and (cite: Devereaux_2024), respectively." (2.3 ALMA FIR observations) [from (cite: Bethermin_2023); (cite: Devereaux_2024)]
- External data: SERRA simulation galaxies compared to observations  
  > "We compared our observations to cosmological simulations, specifically the SERRA simulation" (5.3 [C II] emission in the CGM) [from (cite: Pallottini_2022)]
- Simulation/model as data: Cloudy photoionization models with BPASS SED at 1, 5, 10, 15 kpc; three density profiles  
  > "The simulation is run using a central ionizing source with the illuminated surface of the cloud being placed, at 1, 5, 10, or 15 kpc" (5.2.1 Ionization modeling)

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
- weighting robust: Briggs robust = +0.5  
  > "We used the cubes with *Briggs* weighting of $\texttt{robust}=+0.5$ in cleaning" (2.3 ALMA FIR observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: high- and low-resolution observations combined  
  > "we adopted the data cubes produced by combining both the high and low resolution observations." (2.3 ALMA FIR observations)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- JWST data processing  
  > "The data processing is described in detail in (cite: Fujimoto_ALPINE_JWST)." (2.2 JWST optical photometric and spectroscopic observations) [from (cite: Fujimoto_ALPINE_JWST)]
- Stellar-to-nebular attenuation ratio f=0.56  
  > "we use $f=0.56$ following (cite: Tsujita_ALPINE_dust) for our sample" (3.2 Spectral fitting) [from (cite: Tsujita_ALPINE_dust)]
- Cloudy source SED  
  > "The spectrum of the central source is modeled using the same SED as that developed in (cite: Veraldi_2025) for ALPINE galaxies" (Cloudy setup) [from (cite: Veraldi_2025)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration, CASA version, and imaging parameters (cell, size, masks, continuum subtraction)
- Exact ISM/CGM mask definitions per galaxy and merger cuts
- q3dfit configuration (fixed redshifts and widths, continuum model)
- Per-galaxy fluxes and ratios table
- Cloudy input files and detailed settings

## Analysis recipe

1. **Define ISM and CGM masks**: ISM = 9 sigma NIRCam contour (PSF-matched); CGM = ISM mask dilated by 0.5'' top-hat kernel minus ISM  
  > "We define the ISM to be the region enclosed within the $9\sigma$ continuum level contour of the NIRCam image, PSF-matched to the NIRSpec IFU data." (3.1 The ISM region)
   - software: SciPy
   - fitting: _not stated_
   - validation: Tested 5 sigma ISM edge, 3 sigma [C II] boundary, and 4 r_[CII] aperture; galight Sersic fit  
  > "neither of these two had a significant impact." (3.1 The CGM region)
2. **Fit emission lines in stacked spectra**: Single Gaussian fits per line with q3dfit; 100 Monte Carlo cube realizations for uncertainties; extinction correction using Balmer decrement  
  > "To obtain the uncertainties of the fitted quantities, a Monte Carlo (MC) procedure was adopted where we generated $100$ realizations of the data cubes" (3.2 Spectral fitting)
   - software: q3dfit, LMFIT
   - parameter: [O II] doublet ratio fixed to unity; [O III] and [N II] doublets fixed to 1/3  
  > "We further fix the doublet line ratio of $F_{\rm [\textup{O\,\textsc{\lowercase{iii}}}]\lambda4959}/F_{\rm [\textup{O\,\textsc{\lowercase{iii}}}]\lambda5007}$" (3.2 Spectral fitting)
   - assumption: Case B Halpha/Hbeta=2.86, Calzetti curve, f=0.56  
  > "by applying a case B ratio of $2.86$ (cite: Cardelli_1989) and a Calzetti attenuation curve (cite: Calzetti_2000)" (3.2 Spectral fitting)
   - fitting: [C II] fit with LMFIT in same masks  
  > "The \[C II\] emission observed by ALMA is extracted in the same ISM and CGM masks and fit in a similar way using `LMFIT`" (3.2 Spectral fitting)
   - validation: G235M vs G395M fluxes compared (~6% difference)  
  > "we find that the ones from G395M are higher by $\sim6\%$." (3.2 Spectral fitting)
3. **Compare ISM and CGM line ratios statistically**: Kendall tau and two-sample KS test on distance to one-to-one line, with 100 MC iterations  
  > "we adopt two statistical tests." (4.1 Statistical tests)
   - fitting: _not stated_
   - validation: _not stated_
4. **Interpret with Cloudy models and SERRA**: Cloudy clouds at varying r with fixed O/H; SERRA 20 matched galaxies compared for [CII]/Halpha  
  > "We use a simple `Cloudy` (cite: Ferland_2017; Chatzikos_2023_cloudy) model to test the impact of a changing distance to the ionization source" (5.2.1 Ionization modeling)
   - software: Cloudy
   - assumption: log(O/H)=-3.6 (0.5 Zsun)  
  > "we set the relative oxygen abundance to $\rm \log(O/H)=-3.6$ which corresponds to $0.5Z_{\odot}$ of gas phase metallicity." (5.2.1 Ionization modeling)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **q3dfit** : Gaussian line fitting of IFU spectra  
  > "we perform Gaussian fits to each line using `q3dfit`" (3.2 Spectral fitting)
- **LMFIT** : fitting [C II]  
  > "fit in a similar way using `LMFIT`" (3.2 Spectral fitting)
- **Cloudy** : ionization modeling  
  > "We use a simple `Cloudy` (cite: Ferland_2017; Chatzikos_2023_cloudy) model" (5.2.1 Ionization modeling)
- **SciPy** : binary_dilation for CGM mask  
  > "using the `binary_dilation` function from `SciPy` Python package" (3.1 The CGM region)
- **galight** : Sersic fits to F444W images  
  > "we conducted a `galight` fit on the F444W images" (3.1 The ISM region)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| O2 shift CGM-ISM | 0.14 | typical 1 sigma standard error 0.06 dex | dex | 3 | The ratio O2 is on average enhanced in the CGM with a $0.14$ dex shift. |
| O32 shift CGM-ISM | -0.15 | not stated | dex | 3 | The ratio O32 is on average decreased in the CGM with a $-0.15$ dex shift. |
| N2O2 shift CGM-ISM | -0.1 | not stated | dex | 3 | skewed towards a deficit in the CGM ($-0.1$ dex shift). |
| SERRA galaxies with lower [CII]/Halpha in CGM | 19 of 20 | not stated | galaxies | 4 | we find that $19$ out of $20$ SERRA galaxies have lower $F_{\rm [\textup{C\,\textsc{\lowercase{ii}}}]}/F_{\rm H\alpha}$ ratios in the CGM than in the ISM |

## Qualitative findings

- ISM and CGM have similar chemical abundances; oxygen ratio differences mainly from lower ionization in CGM; possible N/O deficit; elevated [CII]/Halpha in CGM  
  > "Our comparison shows that the ISM and the CGM have similar chemical abundances." (abstract)

## Claim tuples

- H: CGM is chemically enriched to ISM level at z~5 | E: Compare strong line ratios in ISM and CGM masks of 18 galaxies | R: No significant difference in R23 and N2; marginal differences in O2, O32, O3, N2O2 | F: CGM enriched to similar level as ISM | **supported**
- H: Oxygen line ratio differences arise from ionization | E: Cloudy models with varying distance | R: Higher O2 and lower O32 reproduced by lower ionization | F: Ionization dominates | **supported**
- H: [CII]/Halpha differs between CGM and ISM | E: ALMA [CII] and JWST Halpha in masks; compare to SERRA | R: Enhanced in CGM, not reproduced by SERRA | F: Feedback/mergers may mix metals | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Small sample; results to be treated with caution  
  > "Due to the relatively small sample, we note that the results should be treated with caution." (4.1 Statistical tests)
- Caveat (inferred, ours): Marginal differences with n=18 and non-independent masks
- Caveat (inferred, ours): Balmer decrement assumptions in CGM questionable
- Caveat (inferred, ours): Gaussian PSF approximation and mask choices

## Reproducibility

- Data public (paper): JWST data from MAST; ALMA via archive programs  
  > "The *JWST* data described here may be obtained from the MAST archive" (2.2 JWST optical photometric and spectroscopic observations)
- Products in archive: _not stated_
- Missing: Exact masks and q3dfit setups
- Missing: Cloudy input files
- Missing: ALMA cubes processing details
- Data volume (inferred): tens of GB (JWST IFU cubes plus ALMA cubes)
- Score (inferred): 3/5, Public data and a clear method outline, but many configuration details are not stated.
- Rediscovery candidate: no, ALMA plays a minor role and the main results rely on JWST processing and unstated settings.

## Links

- Method: (cite: Fujimoto_ALPINE_JWST) (JWST data processing)
- Method: (cite: Rupke_2023q3dfit) (line fitting code)
- Companion: (cite: Faisst_ALPINE_JWST) (survey description)
- Companion: (cite: Herrera-Camus_CRISTAL) (CRISTAL ALMA program)
- Related: ALPINE
- Related: CRISTAL
- Related: COSMOS-Web

## Checks

```json
{
 "quotes": 46,
 "quotes_ok": 46,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 33,
  "rate": 0.452
 },
 "evidence_ok": true
}
```
