# Resolved Lyman-α properties of a luminous Lyman-break galaxy in a large ionized bubble at z = 6.53

`2020MNRAS.492.1778M` | Monthly Notices of the Royal Astronomical Society 2020 | first author: Matthee, Jorryt | arXiv: 1909.06376 | DOI: 10.1093/mnras/stz3554

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies
- Question: What are the spatially resolved Lyα properties of the luminous z=6.53 galaxy VR7 (MUSE), and how do they compare with [CII] (ALMA), the UV (HST) and other galaxies, as a probe of neutral gas around it?  
  > "Can we witness any imprint of re-ionisation on the observed Ly$\alpha$ properties? These are the questions that we aim to address." (1 Introduction)
- Target **VR7**: coordinates RA 22:18:56.36, Dec +00:08:07.32  
  > "R.A.                      |                               22:18:56.36" (Table 1); "VR7, a UV-luminous galaxy at $z=6.532$" (abstract); z/distance z=6.532 (Lyα); z_sys=6.5285 from [CII]  
  > "R.A.                      |                               22:18:56.36" (Table 1); "VR7, a UV-luminous galaxy at $z=6.532$" (abstract); distance from [CII] from Matthee2019  
  > "R.A.                      |                               22:18:56.36" (Table 1); "VR7, a UV-luminous galaxy at $z=6.532$" (abstract)

## Data provenance

- ALMA projects: 2017.1.01451.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: [CII] PSF-FWHM ≈0.7'' as imaged here; 0.5'' in Matthee2019  
  > "here imaged with spatial resolution with PSF-FWHM $\approx0.7''$" (6.1 Lyα line-profile variations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: [CII] 158 micron (not stated)
- Other facility **VLT/MUSE**: Lyα IFU spectroscopy, program 099.A-0462, 16740 s max exposure  
  > "VR7 was observed with VLT/MUSE (cite: Bacon2010) in service mode through program 099.A-0462 (PI: Matthee)" (2.1 Observations & reduction)
- Other facility **HST/WFC3**: resolved rest-frame UV imaging  
  > "UV imaging from *HST*" (abstract)
- External data: ALMA [CII] redshift z=6.5285, FWHM, UV properties (M1500, beta, SFR) and morphology of VR7  
  > "systemic redshift traced by \[CII\]$_{158 \rm \mu m}$ ($z=6.5285$; (cite: Matthee2019)" (3 General properties of VR7) [from (cite: Matthee2019)]

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

- ALMA [CII] data reduction, imaging and morphological models taken from earlier paper  
  > "(here imaged with spatial resolution with PSF-FWHM $\approx0.7''$; (cite: Matthee2019))" (6.1 Lyα line-profile variations) [from (cite: Matthee2019)]
- Shell-model fitting pipeline  
  > "using the pipeline described in (cite: Gronke2015)" (6.2 Lyα shell models) [from (cite: Gronke2015)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration, CASA version and imaging parameters (done in Matthee2019)
- Shell-model priors and sampler settings
- Grid ranges for the core/halo fit
- Exact [CII] cube used for the comparison spectra

## Analysis recipe

1. **Reduce MUSE data**: MUSE pipeline v2.2 in Esorex, then CubEx for flat-fielding, sky residual removal and combination  
  > "We reduce the data using the MUSE pipeline v2.2 (cite: Weilbacher2014) included in Esorex." (2.1 Observations & reduction)
   - software: Esorex, CubEx
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit Lyα sizes**: Imfit PSF-convolved exponential fit to the continuum-subtracted Lyα image, bootstrap errors  
  > "Imfit simulates PSF-convolved models (using the reference star image) and finds the best-fitting solution using the Levenberg-Marquardt algorithm." (5.1 Lyα)
   - software: Imfit
   - parameter: 1000 bootstrap resamples  
  > "Uncertainties are estimated by performing the fitting procedure on 1000 bootstrap-resamples" (5.1 Lyα)
   - fitting: Levenberg-Marquardt  
  > "Imfit simulates PSF-convolved models (using the reference star image) and finds the best-fitting solution using the Levenberg-Marquardt algorithm." (Sizes and extended emission, Ly$\alpha$)
   - validation: HST continuum model checked against MUSE 920-930 nm continuum  
  > "The right panel shows that no significant residuals are seen" (Appendix)
3. **Core+halo decomposition**: Grid of model images with UV-like core and exponential halo; likelihood exp(-chi2/2)  
  > "For each model we also calculate the likelihood as $\mathcal{L} \propto {\rm exp}(-\chi^2/2)$." (5.3 Two-component Lyα fit)
   - software: Imfit
   - assumption: core and halo co-spatial; core r_eff fixed to UV size 1.34 kpc  
  > "we assume the core and halo components to be co-spatial in our modelling below." (5.3 Two-component Lyα fit)
   - fitting: grid chi2 marginalised posterior  
  > "Here, the quoted values represent the median and the difference to the 16th and 84th percentile of the marginalised posterior distribution." (Sizes and extended emission, Two-component Ly$\alpha$ fit)
   - validation: _not stated_
4. **Spectral variations and shell model**: PV diagrams compared with [CII]; shell-model Bayesian fits to spectra in four regions  
  > "we perform ‘shell-model’ fitting on continuum-subtracted Ly$\alpha$ spectra in different regions" (6.2 Lyα shell models)
   - assumption: Gaussian prior on z_sys (6.5285, 0.001) from [CII]  
  > "gaussian prior $(\mu,\,\sigma)=(6.5285,\,0.001)$ based on \[CII\]" (6.2 Lyα shell models)
   - fitting: Bayesian pipeline of Gronke2015  
  > "we perform ‘shell-model’ fitting on continuum-subtracted Ly$\alpha$ spectra in different regions (the four directions in the PV-diagram; Fig. $\ref{fig:PV}$) of VR7 using the pipeline described in (cite: Gronke2015)." (Resolved Ly$\alpha$ properties, Ly$\alpha$ shell models)
   - validation: _not stated_

## Software

- **Imfit** : PSF-convolved surface brightness modelling  
  > "We use Imfit to fit an exponential profile to VR7’s Ly$\alpha$ image." (5.1 Lyα)
- **CubEx** : data cube combination and emitter search  
  > "we use CubEx to identify line-emitters in the continuum-subtracted data-cube" (4 Environment around VR7)
- **MUSE pipeline** v2.2: MUSE reduction in Esorex  
  > "We reduce the data using the MUSE pipeline v2.2" (2.1 Observations & reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Lyα effective radius (exponential) | 2.05 | ±0.16 | kpc | 2 | We measure r$_{\rm eff, Ly\alpha}=2.05\pm0.16$ kpc |
| UV effective radius | 1.34 | ±0.06 | kpc | 2 | r$_{\rm eff, UV, core}$                        /          $1.34\pm0.06$ kpc |
| [CII] effective radius | 2.14 | +0.24/-0.22 | kpc | 2 | r$_{\rm eff, [CII]}=2.14^{+0.24}_{-0.22}$ kpc |
| Lyα halo effective radius | 3.45 | +1.08/-0.87 | kpc | 3 | r$_{\rm eff, halo} = 3.45^{+1.08}_{-0.87}$ kpc |
| Lyα velocity offset from [CII] | +213 | +19/-20 | km/s | 0 | velocity offset of $+213^{+19}_{-20}$ km s$^{-1}$ to the systemic redshift |
| Lyα FWHM | 374 | +21/-23 | km/s | 0 | The line-width FWHM is $374^{+21}_{-23}$ km s$^{-1}$ |

## Qualitative findings

- Lyα and [CII] have similar spatial variations tied to two UV components  
  > "there are spatial variations that are qualitatively similar in both lines and coincide with resolved UV components" (abstract)

## Claim tuples

- H: Is Lyα more extended than the UV and similar to [CII]? | E: Single exponential Imfit fits to MUSE, HST and ALMA images matched to the MUSE PSF | R: r_eff Lyα 2.05 kpc, UV 1.34 kpc, [CII] 2.14 kpc | F: Lyα and [CII] are similarly extended beyond the UV | **supported**
- H: Is there evidence of a more neutral vicinity at z>6? | E: Compare halo scale lengths and velocity offsets to literature | R: Halo sizes similar across redshift; velocity shifts typically smaller | F: Little indication of more neutral vicinity | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): MUSE data not deep or wide enough to identify moderate over-densities  
  > "our MUSE data is not deep (and/or wide) enough to be used to identify moderate over-densities." (4 Environment around VR7)
- Caveat (inferred, ours): Single-pixel PSF-limited MUSE resolution limits component separation
- Caveat (inferred, ours): [CII] as systemic proxy
- Caveat (inferred, ours): Shell model degeneracies

## Reproducibility

- Data public (paper): ALMA project code is stated, but public status is not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.01451.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: ALMA reduction details (in Matthee2019)
- Missing: MUSE reduced cube not released
- Missing: CubEx is unpublished
- Data volume (inferred): ~10 GB MUSE cube plus small ALMA cube
- Score (inferred): 3/5, MUSE analysis is described, but the ALMA part is inherited and cube access is uncertain.
- Rediscovery candidate: no, Main results rely on MUSE data and inherited ALMA products.

## Links

- Method: (cite: Gronke2015) (shell-model fitting pipeline)
- Method: (cite: Erwin2015) (Imfit)
- Companion: (cite: Matthee2019) (ALMA and HST analysis of VR7)
- Related: MUSE program 099.A-0462

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
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 27,
  "rate": 0.397
 },
 "evidence_ok": true
}
```
