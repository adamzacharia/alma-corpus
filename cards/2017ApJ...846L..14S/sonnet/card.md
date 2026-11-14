# Massive Quenched Galaxies at z ∼ 0.7 Retain Large Molecular Gas Reservoirs

`2017ApJ...846L..14S` | The Astrophysical Journal Letters 2017 | first author: Suess, Katherine A. | arXiv: 1708.03337 | DOI: 10.3847/2041-8213/aa85dc

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, high_z_galaxies
- Question: Do recently quenched massive post-starburst galaxies at z~0.7 still retain large molecular gas reservoirs, as tested with ALMA CO(2-1)?  
  > "we investigate the role of gas supply in suppressing star formation by studying the molecular gas content of post-starburst galaxies." (abstract)
- Target **SDSS J0912+1523**: coordinates _not stated_; z/distance z = 0.747  
  > "| SDSS J0912+1523 | 0.747 |" (Table 1); distance from SDSS spectroscopic redshift (implied)  
  > "| SDSS J0912+1523 | 0.747 |" (Table 1)
- Target **SDSS J2202-0033**: coordinates _not stated_; z/distance z = 0.657  
  > "| SDSS J2202-0033 | 0.657 |" (Table 1); distance from SDSS spectroscopic redshift (implied)  
  > "| SDSS J2202-0033 | 0.657 |" (Table 1)

## Data provenance

- ALMA projects: 2016.1.01126.S
- bands: Band 4  
  > "using the ALMA Band 4 receivers" (3 ALMA Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 2.2x3.0'' (J2202-0033), 1.7x2.4'' (J0912+1523), natural weighting  
  > "The observations reach a spatial resolution of 2.2$\times$3.0$''$(16$\times$22$\,$kpc) and 1.7$\times$2.4$''$(12$\times$17$\,$kpc)" (3 ALMA Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: ~100 min per target (two 80 min blocks each)  
  > "The total on-source integration time for each target was $\sim$100 min." (3 ALMA Observations)
- observing dates: January and March 2017  
  > "in January and March 2017" (3 ALMA Observations)
- pi or archival as stated: PI R. Bezanson  
  > "program 2016.1.01126.S (PI: R. Bezanson)" (3 ALMA Observations)
- Line: CO J=2-1 (not stated)
- Other facility **SDSS DR12**: Spectra for sample selection, stellar masses, SFRs  
  > "we select galaxies from the SDSS DR12 (cite: dr12) spectroscopic catalog with $i<19$" (2 Sample Selection)
- Other facility **WISE**: 12 micron data to constrain obscured SFR  
  > "We additionally constrain the obscured star formation with WISE 12$\mu$m data (cite: mainzer11)" (7 Discussion)
- External data: Comparison samples of K+A post-starbursts' gas and SFR  
  > "we show for comparison the low-redshift ‘K+A’ post-starburst galaxies in (cite: french15)" (4 Molecular Gas Masses) [from (cite: french15)]
- External data: alpha_CO fitting formula vs CO surface brightness  
  > "We estimate the value of $\alpha_{\rm{CO}}$ using the numerical models of (cite: narayanan12)." (4 Molecular Gas Masses) [from (cite: narayanan12)]

## Processing

### Calibration

- pipeline or manual: Standard ALMA pipeline; manual bandpass for one J2202-0033 block  
  > "The data were reduced using the standard ALMA pipeline, which produced good results for both SDSS J0912+1523 observing blocks and one SDSS J2202-0033 block." (3 ALMA Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "in images inverted using natural weighting, which maximizes sensitivity at the expense of slightly lower spatial resolution" (3 ALMA Observations)
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

### Not stated but needed to reproduce (our reading)

- CASA/pipeline version
- Flux calibrator and flux scale uncertainty
- Spectral setup and frequencies
- Cell/image size, cleaning parameters, continuum-subtraction channels
- uvmultifit model parameters and positions
- Rest frequency used for line luminosity

## Analysis recipe

1. **Extract spectra**: Fit point source or circular Gaussian to visibilities, averaging channels  
  > "we fit a point source (SDSS J2202-0033) or a circular Gaussian (SDSS J0912+1523) to the visibility data using the *uvmultifit* package" (3 ALMA Observations)
   - software: uvmultifit
   - parameter: Averaged 24 (J2202) or 6 (J0912) channels, ~200 and 50 km/s  
  > "averaging 24 (SDSS J2202-0033) or 6 (SDSS J0912+1523) channels, yielding a velocity resolution of $\approx\,$200 and 50 $\rm{km\,s}^{-1}$" (3 ALMA Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure line flux and luminosity**: Gaussian profile fit to spectra; convert flux to L'CO  
  > "We fit simple Gaussian profiles to these spectra, which yield integrated line fluxes of $1.07\pm0.05$ and $0.27\pm0.03$ Jy $\rm{km\,s}^{-1}$" (4 Molecular Gas Masses)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive molecular gas mass**: M_gas = alpha_CO x L'CO(1-0), with r21 = 1  
  > "we therefore adopt $\alpha_{\rm{CO}}$= 4.0 for both of our targets." (4 Molecular Gas Masses)
   - assumption: alpha_CO = 4.0; CO(2-1)/CO(1-0) = 1 (thermalized)  
  > "We assume thermalized emission in our analysis." (4 Molecular Gas Masses)
   - fitting: _not stated_
   - validation: alpha_CO checked against Narayanan et al. formula  
  > "Our data spatially resolve SDSS J0912+1523; combined with its CO luminosity, this implies $\ensuremath{\alpha_{\rm{CO}}}\sim3.5$." (4 Molecular Gas Masses)
4. **Constrain obscured SFR**: 2 mm continuum upper limit with modified blackbody; WISE 12um with Dale templates  
  > "We assume that the dust emission follows a standard modified blackbody function with $\ensuremath{T_{\rm{dust}}}=30$ K (cite: magdis12)." (7 Discussion)
   - assumption: T_dust = 30 K  
  > "$\ensuremath{T_{\rm{dust}}}=30$ K (cite: magdis12)" (7 Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **uvmultifit** : Fit visibilities to extract spectra  
  > "using the *uvmultifit* package (cite: martividal14)" (3 ALMA Observations)
- **FAST** : Stellar population fits for stellar masses  
  > "we fit the SDSS spectra with the stellar population synthesis fitting code FAST (cite: kriek2009)" (2 Sample Selection)
- **EZ_Ages** : Measuring Hdelta_A  
  > "we measured H$\delta_A$ using EZ_Ages (cite: graves08)" (6 Comparison to other studies)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| M_gas SDSS J0912+1523 | 34.0e9 | 1.6e9 | Msun | 3 | $\ensuremath{M_{\rm{gas}}}=(34.0\pm1.6)\times10^9$ $\rm{M}_\odot$ for SDSS J0912+1523 |
| M_gas SDSS J2202-0033 | 6.4e9 | 0.8e9 | Msun | 3 | $\ensuremath{M_{\rm{gas}}}=(6.4\pm0.8)\times10^9$ $\rm{M}_\odot$ for SDSS J2202-0033 |
| CO(2-1) flux J0912+1523 | 1.07 | 0.05 | Jy km/s | 2 | integrated line fluxes of $1.07\pm0.05$ and $0.27\pm0.03$ Jy |
| CO(2-1) flux J2202-0033 | 0.27 | 0.03 | Jy km/s | 2 | integrated line fluxes of $1.07\pm0.05$ and $0.27\pm0.03$ Jy |
| 2 mm continuum 3sigma upper limit | <75 | not stated | uJy | 4 | with a 3$\sigma$ upper limit $<75$ $\mu$Jy |
| Deconvolved FWHM J0912+1523 | 1.9 | 0.3 | arcsec | 1 | deconvolved source FWHM of 1.9 $\pm$ 0.3$''$(14 $\pm$ 2$\,$kpc) |

## Qualitative findings

- Gas masses are an order of magnitude above comparable-mass local galaxies; quenching need not remove molecular gas.  
  > "Our observations suggest that quenching does not require the total removal or depletion of molecular gas" (abstract)

## Claim tuples

- H: Quenching requires depletion/removal of molecular gas | E: ALMA CO(2-1) of two z~0.7 post-starburst galaxies | R: M_gas of 6.4e9 and 34e9 Msun, high for their SFR | F: Quenching can occur with large gas reservoirs | **supported**
- H: Obscured star formation explains the gas excess | E: 2 mm continuum and WISE 12um limits | R: Upper limits ~50 and ~60 Msun/yr | F: Cannot rule out obscured SF for J0912+1523 | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Lower alpha_CO, bottom-heavy IMF, short-term SFR variations, or obscured SF could explain high gas masses  
  > "there are several alternative explanations for the high gas masses in SDSS J0912+1523 and SDSS J2202-0033." (7 Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Factor of two systematic uncertainty from CO excitation and alpha_CO; very small sample  
  > "there are also factor of two systematic uncertainties associated with the CO excitation and conversion factor." (4 Molecular Gas Masses)
- Caveat (inferred, ours): Only two galaxies
- Caveat (inferred, ours): alpha_CO and r21 assumed
- Caveat (inferred, ours): No CO(1-0) or higher-J data
- Caveat (inferred, ours): Resolution coarse

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters and uvmultifit setup
- Missing: Pipeline version
- Missing: Rest frequency/line luminosity formula details
- Data volume (inferred): ~10-30 GB
- Score (inferred): 3/5, Simple analysis with public ALMA project, but imaging/fitting details are sparse.
- Rediscovery candidate: yes, Public data, simple numeric results (line flux, M_gas), though details are thin.

## Links

- Method: (cite: martividal14) (uvmultifit)
- Method: (cite: narayanan12) (alpha_CO prescription)
- Companion: (cite: french15) (low-z K+A post-starburst gas comparison)
- Related: SDSS
- Related: COLD GASS
- Related: ATLAS-3D
- Related: MASSIVE
- Related: PHIBSS

## Checks

```json
{
 "quotes": 41,
 "quotes_ok": 41,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2016.1.00126.S"
 ],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 30,
  "rate": 0.423
 },
 "evidence_ok": true
}
```
