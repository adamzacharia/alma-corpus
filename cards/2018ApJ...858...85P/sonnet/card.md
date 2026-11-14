# Forecasting the Contribution of Polarized Extragalactic Radio Sources in CMB Observations

`2018ApJ...858...85P` | The Astrophysical Journal 2018 | first author: Puglisi, G. | arXiv: 1712.09639 | DOI: 10.3847/1538-4357/aab3c7

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: cosmology, agn_and_quasars
- Question: How does the fractional polarization of extragalactic radio sources depend on frequency (1.4-217 GHz), and how much do polarized ERS contaminate CMB B-mode observations of current and forthcoming experiments?  
  > "We consider data over a very wide frequency range starting from $1.4$ GHz up to $217$ GHz." (abstract); "we assess that polarized ERS can contaminate the cosmological B-mode polarization if the tensor-to-scalar ratio is $< 0.05$" (abstract)
- Target **32 PACO sources (sub-sample of 104 sources with ecliptic latitude < -65 deg)**: coordinates 3 circular regions (10 deg diameter) at ecliptic latitude < -75 deg  
  > "A sub-sample of 104 of these sources with ecliptic latitude $<-65 ^{\circ}$" (PACO with ATCA and ALMA); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: _none stated_
- bands: 95 GHz  
  > "32 of them have been also followed up at 95 GHz" (PACO with ATCA and ALMA)
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
- pi or archival as stated: Details deferred to companion paper (Galluzzi et al. 2018, in prep.)  
  > "Further details will be described in a companion paper (Galluzzi et al. 2018, in prep.)." (PACO with ATCA and ALMA)
- Other facility **ATCA (PACO, AT20G)**: 20 GHz and other polarization/total intensity data  
  > "has been re-observed with high sensitivity in polarization with ATCA in 2014 and 2016 in the $1.1 - 39$ GHz frequency range" (PACO with ATCA and ALMA)
- Other facility **Planck PCCS2**: 30-217 GHz polarized source detections  
  > "including polarimetric detection of sources between $30$ and $353$ GHz from August 2009 to August 2013" (The Second Planck Catalogue of Compact Sources)
- Other facility **VLA, S-PASS, NVSS, JVAS/CLASS, IRAM XPOL**: Public catalogues of polarization fractions at 1.4-86 GHz  
  > "we present the data collected from publicly available catalogues." (Data)
- External data: 20 GHz PACO polarization number counts  
  > "polarization number counts computed by (cite: Galluzzi2017b) at $20$ GHz" (Statistical properties of ERS polarization fraction) [from (cite: Galluzzi2017b)]
- External data: S-PASS/NVSS polarization catalogue  
  > "(cite: Lamee2016) cross-matched it with the NRAO/VLA Sky Survey" (The S-PASS/NVSS joint catalogue) [from (cite: Lamee2016)]
- Simulation/model as data: D05 and C2Ex source number count models  
  > "we make use of both D05 and C2Ex models to assess respectively *conservative* and *realistic* estimates" (Model for Number Counts)

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

- Log-normal model for polarization fraction distribution  
  > "Following (cite: 2011MNRAS.413..132B), we model $\mathcal{P}(\Pi)$ by means of a log-normal distribution" (Statistical properties of ERS polarization fraction) [from (cite: 2011MNRAS.413..132B)]
- Bootstrap-resampling method  
  > "by using a *bootstrap-resampling* method outlined in (cite: Austermann2009)" (Statistical properties of ERS polarization fraction) [from (cite: Austermann2009)]

### Not stated but needed to reproduce (our reading)

- ALMA 95 GHz data processing, calibration, project code and polarization measurements (deferred to Galluzzi et al. 2018)
- Number of bootstrap resamplings N_resamp and exact bin choices
- Fit method for log-normal and linear fits

## Analysis recipe

1. **derive polarization fraction distributions**: Bootstrap resampling of catalogue fluxes, binned fractions, log-normal fit  
  > "Finally, a log-normal distribution function [\[eq:lognorm\]](#eq:lognorm) is fitted from each dataset" (Statistical properties of ERS polarization fraction)
   - parameter: 5 to 15 bins; Poisson errors at 68% confidence  
  > "ranging from 5 to 15 bins depending on the number of data collected in each catalogue" (Statistical properties of ERS polarization fraction)
   - fitting: _not stated_
   - validation: _not stated_
2. **fit frequency dependence of <Pi^2>^1/2**: Linear fit across datasets  
  > "We find a negligible frequency dependence of $\langle \Pi^2 \rangle ^{1/2}$" (Statistical properties of ERS polarization fraction)
   - fitting: _not stated_
   - validation: _not stated_
3. **forecast ERS contamination for CMB experiments**: Compute number counts and Poissonian power spectra with PS4C, compare with CAMB CMB and rescaled Galactic foregrounds  
  > "we assume their distribution in the sky to be Poissonian" (Forecasts for forthcoming CMB ground-based experiment)
   - software: PS4C, CAMB
   - parameter: r=0.05, Planck best fit cosmology  
  > "assuming the *Planck* best fit cosmological parameters (cite: 2016A&A...594A..13P) and a tensor to scalar ratio $r=0.05$" (Forecasts for forthcoming CMB ground-based experiment)
   - assumption: Polarization angle uniformly distributed; C_B ≈ C_E ≈ C_U ≈ C_Q  
  > "we can approximate $C_{\ell} ^B\simeq  C_{\ell} ^E\simeq C_{\ell} ^U\simeq C_{\ell} ^Q$" (Forecasts for forthcoming CMB ground-based experiment)
   - fitting: _not stated_
   - validation: Compared PS4C counts with DZ16 estimates  
  > "Comparison of surface densities of polarized ERSs brighter than $P_{4 \sigma}$ estimated by (cite: 2016arXiv160907263D)(DZ16) and by PS4C." (PS4C with future space missions)

## Software

- **PS4C** : Forecast of ERS contribution to CMB power spectra  
  > "a `Python` package Point Source ForeCast (PS4C) made publicly available" (Forecasts for forthcoming CMB ground-based experiment)
- **CAMB** : CMB power spectra  
  > "We compute one realization of CMB power spectra by means of the CAMB package" (Forecasts for forthcoming CMB ground-based experiment)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Slope of <Pi^2>^1/2 vs frequency (flat-spectrum) | 0.005 | 0.006 | GHz^-1 | 2 | \left( {0.005 } \pm 0.006 \mathrm{ GHz^{-1}}\right) \nu |
| Intercept of <Pi^2>^1/2 fit (flat-spectrum) | 4.170 | 0.22 | % | 2 | \left({4.170}\pm 0.22 \right) |
| <Pi^2>^1/2 at 95 GHz (PACO-ALMA, flat spectrum) | 4.94 | 1.32 | % | 1 | / 95           / 32        / $1.09 \pm 0.21$  / $2.13 \pm 0.23$  / $0.97 \pm 0.09$  / $3.20 \pm 0.60$       / $2.07 \pm 0.24$ / $4.94 \pm 1.32$               / This work             / |
| Max polarized sources detected at 3 sigma by CMB-S3 LA (30 GHz) | 2329 | not stated | sources | 3 | the maximum number of polarized sources detected above a $3\sigma$ level and using the large aperture telescope is $2329$ |

## Qualitative findings

- Fractional polarization of ERS at ν>20 GHz is about 4% with negligible frequency dependence and no flux dependence.  
  > "Notice that for $\nu >20$ GHz, we found $\langle \Pi^2 \rangle ^{1/2} \sim 4 \%$" (Statistical properties of ERS polarization fraction)

## Claim tuples

- H: Does ERS fractional polarization depend on frequency at CMB frequencies? | E: Combine 10 catalogues including ALMA 95 GHz sample, fit log-normal distributions and a linear relation | R: Slope 0.005±0.006 GHz^-1; ~4% above 20 GHz | F: Mild/negligible frequency dependence | **supported**
- H: Do polarized ERS contaminate B-modes in forthcoming experiments? | E: PS4C forecasts for QUIJOTE, CMB-S2, CMB-S3, LiteBIRD, CORE | R: ~200 up to ~2000 polarized ERS detected; undetected ERS matter for r<0.05 | F: ERS must be controlled for de-lensing and low r | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Planck detections may be biased upward toward high fractional polarization; forecasts limited to ≤150 GHz, excluding dusty galaxies  
  > "the statistics of ERS polarization can be biased upward" (The Second Planck Catalogue of Compact Sources)
- Caveat (inferred, ours): ALMA sample (32 sources) is small and selected from bright sources
- Caveat (inferred, ours): Heterogeneous catalogues combined without common completeness correction
- Caveat (inferred, ours): Linear fit with large uncertainties on slope

## Reproducibility

- Data public (paper): Catalogues from VizieR/Planck Legacy Archive; ALMA data unpublished here  
  > "we present the data collected from publicly available catalogues." (Data)
- Products in archive: _not stated_
- Code: PS4C at https://gitlab.com/giuse.puglisi/PS4C  
  > "<https://gitlab.com/giuse.puglisi/PS4C>" (Forecasts for forthcoming CMB ground-based experiment)
- Missing: ALMA 95 GHz polarization measurements and processing (companion paper)
- Missing: bootstrap settings
- Data volume (inferred): Negligible for catalogue analysis; ALMA raw data not needed
- Score (inferred): 3/5, Catalogue-based analysis with public code but ALMA part is deferred to a companion paper.
- Rediscovery candidate: no, ALMA role is minor and not processed here; catalogue values are partly from literature.

## Links

- Method: (cite: 2011MNRAS.413..132B) (log-normal polarization fraction model)
- Companion: Galluzzi et al. 2018, in prep. (ALMA 95 GHz observations and polarization properties)
- Companion: (cite: Galluzzi2017b) (PACO 20 GHz polarization)
- Related: PACO
- Related: AT20G
- Related: Planck PCCS2
- Related: S-PASS
- Related: QUIJOTE
- Related: LiteBIRD
- Related: CMB-S3

## Checks

```json
{
 "quotes": 34,
 "quotes_ok": 34,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2015.1.01522.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 25,
  "rate": 0.368
 },
 "evidence_ok": true
}
```
