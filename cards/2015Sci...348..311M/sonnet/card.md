# A strong magnetic field in the jet base of a supermassive black hole

`2015Sci...348..311M` | Science 2015 | first author: Martí-Vidal, Ivan | arXiv: 1604.01898 | DOI: 10.1126/science.aaa1784

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars
- Question: Can Faraday rotation be detected at the jet base of PKS 1830-211 with ALMA, and what does the rotation measure imply for the magnetic field strength?  
  > "Studying the polarization of this non-thermal emission from AGN is a direct way to probe the structure and strength of magnetic fields in the vicinity of a black hole." (abstract)
- Target **PKS 1830-211**: coordinates _not stated_; z/distance z = 2.5  
  > "PKS 1830$-$211, a powerful gravitationally-lensed AGN located at a redshift of $z = 2.5$ (cite: lid99)" (main text); distance from Lidman et al. 1999 (cite: lid99)  
  > "PKS 1830$-$211, a powerful gravitationally-lensed AGN located at a redshift of $z = 2.5$ (cite: lid99)" (main text)

## Data provenance

- ALMA projects: 2011.0.00405.S, 2012.1.00056.S, 2013.1.00020.S
- bands: _not stated_
- frequencies and spectral setup: Sky frequencies around 100, 250 and 300 GHz; four spectral windows per epoch  
  > "Our results are based on ALMA observations at sky frequencies around 100, 250, and 300 GHz." (main text)
- continuum bandwidth: ~2 GHz per frequency window  
  > "The bandwidth in each frequency window is $\sim2$ GHz." (Epochs of observation and measurements)
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: sub-arcsecond  
  > "This detection has been possible thanks to the high resolution (sub-arcsecond) of our observations with ALMA" (main text)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 6 epochs in 2012 (9 April to 16 June) and 9 epochs in 2014 (3 May to 27 August)  
  > "one consisting of 6 epochs in 2012 (9 April to 16 June) and another of 9 epochs in 2014 (3 May to 27 August)" (main text)
- pi or archival as stated: _not stated_
- External data: Redshift z = 2.5 of PKS 1830-211  
  > "a powerful gravitationally-lensed AGN located at a redshift of $z = 2.5$ (cite: lid99)" (main text) [from (cite: lid99)]
- External data: Parsec-scale AGN core magnetic fields of ~0.05-0.10 G used for comparison  
  > "where the derived magnetic fields have been independently measured to be $\simeq 0.05-0.10$ Gauss (cite: Gabuzda4; Gabuzda5)" (main text) [from (cite: Gabuzda4; Gabuzda5)]

## Processing

### Calibration

- pipeline or manual: Differential polarimetry on XX and YY flux ratios between lensed images, insensitive to X-Y gain/bandpass differences; no polarization calibration  
  > "The estimate of $R_{pol}$ is, by construction, insensitive to bandpass and/or gain differences among the X and Y signals." (Polarization leakage)
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

- Differential polarimetry technique details  
  > "a new differential polarimetry technique, which we present in (cite: SupportA)" (main text) [from (cite: SupportA)]
- Observation details and ALMA project goals  
  > "More details on these observations, and a summary of the main goals of this ALMA project, can be found elsewhere (cite: mul14)." (main text) [from (cite: mul14)]
- Visibility-fitting of flux ratios  
  > "fitted with the visibility-modelling software presented in (cite: UVMULTIFIT)" (main text) [from (cite: UVMULTIFIT)]

### Not stated but needed to reproduce (our reading)

- Calibration pipeline/CASA version and calibrators
- Source models (number of components) used in UVMULTIFIT
- Initial guesses and parameter bounds of the Rpol fit
- How the data were split into parallactic angle segments
- Antenna configurations and baselines
- Which executions belong to which project code

## Analysis recipe

1. **Measure flux-density ratios of lensed images**: Fit XX and YY visibilities separately with a two-component model, bypassing imaging  
  > "by fitting the models directly to the interferometric observables (i.e., the visibilities), hence bypassing the image deconvolution process." (Epochs of observation and measurements)
   - software: UVMULTIFIT
   - fitting: _not stated_
   - validation: _not stated_
2. **Compute polarization ratio Rpol**: Rpol = 1/2 (R_XX/R_YY - 1) with errors by standard propagation from fit covariance matrix  
  > "The uncertainties have been obtained with the standard error propagation approach, using the uncertainties in $R_{XX}$ and $R_{YY}$" (main text)
   - fitting: _not stated_
   - validation: Simulations with 1% antenna leakage give Rpol errors below 5e-4  
  > "All errors are below 5$\times$10$^{-4}$." (Polarization leakage)
3. **Fit rotation measure**: Least-squares fit of Rpol vs lambda^2 and parallactic angle with a cosine model, for three epochs with quasi-simultaneous 250 and 300 GHz data; 100 GHz data excluded  
  > "The parameter estimates in these three datasets have been performed by least-squares minimization, comparing the measured $R_{pol}$ to the model predictions." (main text)
   - assumption: RMs and fractional polarization wavelength dependence similar for both lensed images, so p_dif and alpha are constant  
  > "their rotation measures should be similar, as well as the wavelength dependence of their fractional polarizations." (Special cases)
   - fitting: Least squares; free parameters RM, p_dif and phase offset  
  > "The parameter estimates in these three datasets have been performed by least-squares minimization, comparing the measured $R_{pol}$ to the model predictions." (Main text, Table 1 discussion)
   - validation: Monte Carlo with 10^4 random datasets; chance probability of equally good fit below 1e-10  
  > "the probability that a random dataset allows us, just by pure chance, to get a fit as good as that from our observations is lower than $10^{-10}$." (Monte Carlo tests)
4. **Convert to rest frame and infer magnetic field**: RM_true = (1+z)^2 RM_obs; compare with RM integral n B dl and parsec-scale AGN core RMs to bound B  
  > "$RM_{true}$ is $(1+z)^2$ times larger than $RM_{obs}$." (Table 1)
   - assumption: z = 2.5  
  > "$z$ is the redshift ($z = 2.5$)" (main text)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **UVMULTIFIT** : Visibility fitting of flux ratios between lensed images  
  > "fitted with the visibility-modelling software presented in (cite: UVMULTIFIT)" (main text)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| RM_obs 10 Apr 2012 | 9.0 | 0.3 | 10^6 rad/m^2 | 3 | 9.0$\pm$0.3 |
| RM_obs 23 May 2012 | 9.4 | 0.4 | 10^6 rad/m^2 | 3 | 9.4$\pm$0.4 |
| RM_obs 5 May 2014 | 25.3 | 0.8 | 10^6 rad/m^2 | 3 | 25.3$\pm$0.8 |
| RM_true 10 Apr 2012 | 11 | 0.4 | 10^7 rad/m^2 | 4 | 11$\pm$0.4 |
| RM_true 23 May 2012 | 11.5 | 0.5 | 10^7 rad/m^2 | 4 | 11.5$\pm$0.5 |
| RM_true 5 May 2014 | 31.2 | 1.0 | 10^7 rad/m^2 | 4 | 31.2$\pm$1.0 |
| p_dif 10 Apr 2012 | 12.6e-3 | 0.4e-3 | dimensionless | 3 | 12.6$\pm$0.4 |
| Max dRpol/dlambda^2 at lambda^2 = 0.8-1.6 mm^2 | 70e-3 | not stated | mm^-2 | 2 | whereas between 0.8 and 1.6 mm$^2$ it is $70\times 10^{-3}$ mm$^{-2}$ |

## Qualitative findings

- RM increases at shorter wavelengths, so the Faraday screen lies close to the jet base and changes on sub-parsec scales  
  > "The Faraday screen must thus be close to the jet base, and change substantially on sub-parsec scales (Fig. 4)." (main text)

## Claim tuples

- H: Faraday rotation is detectable at submm wavelengths in the AGN jet base | E: Differential polarimetry of the lensed images of PKS 1830-211 across 100, 250 and 300 GHz in 15 epochs | R: Rest-frame RM ~1e8 rad/m^2 at 250-300 GHz, higher in 2014 | F: Detected Faraday rotation, two orders of magnitude above previous AGN values | **supported**
- H: The Faraday screen is a distant external screen | E: Compare Rpol derivatives vs lambda^2 across bands | R: Derivative at short wavelengths much larger than at long wavelengths | F: RM varies with wavelength so the screen is near the jet base | **supported**
- H: Magnetic field strength at the sub-parsec jet base | E: Compare RM with parsec-scale cores | R: RM ~1e5 times larger than parsec-scale cores | F: Fields of at least a few tens of Gauss | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: External spherically symmetric accreting screen or external clouds rejected as the origin of the RM  
  > "Our finding cannot be explained easily if the $RM$ is only caused by an external (e.g. spherically symmetric) screen of material" (main text)
- How they decided it was enough: _not stated_
- Limitation (authors): B, electron density and path length cannot be disentangled from the RM  
  > "it is impossible to unambiguously disentangle the contributions of the magnetic field, electron density and path length" (main text)
- Caveat (inferred, ours): Only three epochs have quasi-simultaneous 250/300 GHz data for the fit; the RM-only fit has 3 free parameters
- Caveat (inferred, ours): Interpretation depends on assumption that both lensed images share the same RM
- Caveat (inferred, ours): Time delay between images and source variability may bias p_dif and phase
- Caveat (inferred, ours): The B-field limit relies on scaling from parsec-scale cores

## Reproducibility

- Data public (paper): ALMA project codes cited; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00405.S, ADS/JAO.ALMA#2012.1.00056.S, and ADS/JAO.ALMA#2013.1.00020.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Source model and UVMULTIFIT configuration
- Missing: Calibration details
- Missing: Parallactic angle segmentation
- Missing: Full Rpol-lambda^2 fit initialisation
- Data volume (inferred): ~50-200 GB for 15 epochs of ALMA continuum observations
- Score (inferred): 3/5, Data and tables of Rpol are given and the method is clear, but calibration, source model and fit details are missing.
- Rediscovery candidate: yes, Rpol per epoch is tabulated and the cosine fit is simple, so RM values can be reproduced from the tables, though the archive data reprocessing needs missing details.

## Links

- Method: (cite: SupportA) (Differential polarimetry technique)
- Method: (cite: UVMULTIFIT) (Visibility fitting software)
- Companion: (cite: IMVPKS) (Earlier ALMA study of PKS 1830-211 and the jet base size)
- Companion: (cite: mul14) (Project overview and observation details)

## Checks

```json
{
 "quotes": 42,
 "quotes_ok": 42,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 27,
  "rate": 0.409
 },
 "evidence_ok": true
}
```
