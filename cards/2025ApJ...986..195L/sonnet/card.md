# The M<SUB>BH</SUB>─M<SUB>∗</SUB> Relation of the Hyperluminous Dust-obscured Quasars up to z ∼ 4

`2025ApJ...986..195L` | The Astrophysical Journal 2025 | first author: Luo, Yibin | arXiv: 2506.01218 | DOI: 10.3847/1538-4357/addecf

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: agn_and_quasars, high_z_galaxies
- Question: Do hyperluminous Hot DOGs at z=1.5-3.7 follow the local M_BH-M_star relation, and what are their Eddington ratios?  
  > "We investigate the $M_{\rm BH}-M_\star$ relation in these sources using Bayesian spectral energy distribution (SED) fitting or with extra constraints from *Hubble Space Telescope* (HST) image decomposition." (abstract)
- Target **11 hyperluminous Hot DOGs at z=1.5-3.7 (e.g. J0220, J0116, J1126)**: coordinates J0220: SDSS J022052.11+013711.1  
  > "SDSS J$022052.11+013711.1 \,\dagger$ | 3.138" (Table 1); z/distance J0220 z = 3.138 (SDSS redshifts)  
  > "SDSS J$022052.11+013711.1 \,\dagger$ | 3.138" (Table 1); distance from SDSS quasar catalog (Wu2022)  
  > "SDSS J$022052.11+013711.1 \,\dagger$ | 3.138" (Table 1)

## Data provenance

- ALMA projects: _none stated_
- bands: _not stated_
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
- pi or archival as stated: _not stated_
- Other facility **WISE/ALLWISE**: Selection and mid-IR photometry  
  > "We first select sources from ALLWISE Data Release (cite: Cutri2014) using the following selection criteria" (2.1 Sample Selection)
- Other facility **SDSS**: Redshifts, broad-line FWHM, ugriz photometry  
  > "All 14 sources have SDSS DR18 $ugriz$ bands photometry (cite: Almeida2023)." (2.2 Multi-wavelength Data)
- Other facility **HST**: Imaging for 4 sources used in image decomposition  
  > "Four sources (J0851, J0220, J0116, and J0834) have HST imaging from MAST" (2.2 Multi-wavelength Data)
- Other facility **Herschel**: FIR photometry for J0851, J0220, J0116  
  > "three sources (J0851, J0220, and J0116) have *Herschel* data" (2.2 Multi-wavelength Data)
- External data: HAWC+/SOFIA, SCUBA-2, SMA far-IR to mm photometry for J1013  
  > "J1013 has HAWC+/SOFIA 89 $\mu$m and 154 $\mu$m, SCUBA-2/JCMT 450 $\mu$m and 850 $\mu$m, SMA 870 $\mu$m and 1.3mm data from (cite: Toba2020)." (2.2 Multi-wavelength Data) [from (cite: Toba2020)]
- External data: Broad-line FWHM and BH mass recipes from SDSS DR16 quasar catalog  
  > "Then we substitute the FWHM of the broad emission line from the (cite: Wu2022) SDSS quasar catalog" (3.3 Black hole mass estimation) [from (cite: Wu2022)]

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

- Combined image and SED decomposition method with modified likelihood  
  > "Following the method from (cite: Yu2025), we incorporate morphology constraint from image decomposition into SED fitting." (3.2 Combining image and SED decomposition) [from (cite: Yu2025)]

### Not stated but needed to reproduce (our reading)

- Which ALMA project data and what flux values were used for J1126, J0220, J0116
- How ALMA data were reduced and photometry measured
- BayeSED3 priors, sampler settings and parameter ranges
- HST image decomposition details

## Analysis recipe

1. **SED decomposition**: Bayesian SED fitting with stellar, CLUMPY AGN and graybody cold dust components  
  > "The SED analysis from UV to millimeter is performed using the Bayesian SED fitting code BayeSED3" (3.1 SED Analysis)
   - software: BayeSED3
   - assumption: BC03 SSP, Chabrier IMF, Calzetti attenuation, exponentially declining SFH  
  > "We assume the (cite: Chabrier2003) initial mass function (IMF), the (cite: Calzetti2000) dust attenuation law, and an exponentially declining star formation history (SFH)." (3.1 SED Analysis)
   - fitting: _not stated_
   - validation: _not stated_
2. **BH mass and Eddington ratio**: Single-epoch virial estimator using obscuration-corrected continuum luminosity from CLUMPY model and catalog FWHM  
  > "we use the CLUMPY model (cite: Nenkova2008a; Nenkova2008b) adopted in the SED fitting to derive the obscuration-corrected monochromatic continuum luminosity." (3.3 Black hole mass estimation)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **BayeSED3** : Bayesian SED fitting  
  > "Bayesian SED fitting code BayeSED3" (3.1 SED Analysis)
- **GaLight** : HST image decomposition into Sersic plus point source  
  > "Using `GaLight` (cite: Ding2021), we simultaneously fit the host galaxy and the AGN as a Sersic profile and a point source." (3.2 Combining image and SED decomposition)
- **PSFr** : Constructing PSF  
  > "reconstruct a median stack PSF using PSFr (Birrer et al. in prep)" (3.2 Combining image and SED decomposition)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Median Eddington ratio of 11 high-z Hot DOGs | 1.05 | not stated | dimensionless | 2 | with the median value of 1.05 and the maximum value close to 3 |
| Median log(M_BH/M_star) of eight Hot DOGs (16th, 50th, 84th percentiles) | -1.83 (16th -2.14, 84th -1.31) | not stated | dimensionless | 2 | the 16th, 50th, and 84th percentiles are $-2.14$, $-1.83$, and $-1.31$, respectively |

## Qualitative findings


## Claim tuples

- H: Hot DOGs deviate from the local M_BH-M_star relation | E: SED and HST decomposition for stellar mass; virial BH masses | R: Median M_BH/M_star only slightly above local 1 sigma range, within 2 sigma | F: No significant difference from the local relation | **supported**
- H: Hot DOGs accrete at high Eddington ratios | E: L_AGN from AGN component over L_Edd | R: Median 1.05, maximum close to 3 | F: Super-Eddington accretion possibly linked to overdense environments | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): J0834 fit is unreliable due to an anomalous UV bump and a dominant AGN  
  > "Consequently, the resulting ratio, although retained in the figure, is noted to have low reliability." (5 Discussion)
- Caveat (inferred, ours): ALMA plays a minor role and its use is undescribed
- Caveat (inferred, ours): Small sample with large BH mass and stellar mass uncertainties
- Caveat (inferred, ours): Virial masses rely on model-corrected luminosity

## Reproducibility

- Data public (paper): Data from public archives (ALMA, Herschel, MAST, SDSS)  
  > "Three sources (J1126, J0220, and J0116) have ALMA data collected from ALMA Science Archive" (2.2 Multi-wavelength Data)
- Products in archive: _not stated_
- Missing: ALMA project codes in text and the continuum flux extraction
- Missing: BayeSED3 configuration
- Data volume (inferred): Small; photometry only, tens of GB at most if ALMA data are reprocessed
- Score (inferred): 3/5, Public data and named software, but ALMA handling and fit settings are unstated.
- Rediscovery candidate: no, ALMA role is minor and settings are incomplete.

## Links

- Method: (cite: Yu2025) (Combined image and SED decomposition method)
- Method: (cite: Han2023) (BayeSED3 code)
- Companion: (cite: Li2024) (Earlier Hot DOG M_BH-M_star study)
- Related: WISE
- Related: SDSS
- Related: WISSH

## Checks

```json
{
 "quotes": 24,
 "quotes_ok": 24,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2013.1.00576.S",
  "2015.1.01148.S",
  "2019.2.00085.S",
  "2021.1.00168.S",
  "2021.1.00913.S",
  "2021.1.01496.S",
  "2022.1.00353.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 2,
 "numeric_problems": 0,
 "fill": {
  "facts": 61,
  "stated": 19,
  "rate": 0.311
 },
 "evidence_ok": true
}
```
