# Complex angular structure of three elliptical galaxies from high-resolution ALMA observations of strong gravitational lenses

`2024A&A...688A.110S` | Astronomy and Astrophysics 2024 | first author: Stacey, H. R. | arXiv: 2403.04850 | DOI: 10.1051/0004-6361/202449710

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type archival_reuse

## Science

- Fields: high_z_galaxies, cosmology
- Question: Whether the lens galaxies of three ALMA-observed lensed dusty starbursts show complex angular structure (multipoles m=3,4) beyond a power-law ellipsoid, and how it compares with their stellar isophotes  
  > "we investigated the angular structure in these lens galaxies with multipole expansions of the power-law density profile." (Introduction); "which we use to compare the mass and light distributions of the three lens galaxies" (Hubble Space Telescope observations)
- Target **SPT 0532-50**: coordinates _not stated_; z/distance _not stated_; distance from known source and lens redshifts, cited to Negrello:2010; Spilker:2016 (values in Table 1, not in text)  
  > "These are galaxy-scale lenses with known source and lens redshifts" (ALMA observations)
- Target **SPT 0538-50**: coordinates _not stated_; z/distance _not stated_; distance from known source and lens redshifts, cited to Negrello:2010; Spilker:2016 (values in Table 1, not in text)  
  > "These are galaxy-scale lenses with known source and lens redshifts" (ALMA observations)
- Target **SDP 81**: coordinates _not stated_; z/distance _not stated_; distance from known source and lens redshifts, cited to Negrello:2010; Spilker:2016 (values in Table 1, not in text)  
  > "These are galaxy-scale lenses with known source and lens redshifts" (ALMA observations)

## Data provenance

- ALMA projects: 2011.0.00016.SV, 2016.1.01374.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12 m antennas  
  > "$D$ is the antenna diameter (12 m)" (Bayesian inference)
- configurations: SPT lenses: multiple epochs in compact and extended configurations, only long-baseline configurations used; SDP 81: atypical array configuration from the long baseline campaign  
  > "we considered only the long-baseline configurations for this experiment to maintain the higher angular resolution" (ALMA observations); "using an atypical array configuration" (ALMA observations)
- baselines: SDP 81: only baselines longer than 100 m used  
  > "we only use baselines with lengths greater than 100 m" (ALMA observations)
- angular resolution: approx. 30 mas  
  > "three gravitational lenses observed at an angular resolution of $\approx30$ mas" (Introduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: SDP 81: 2014 ALMA long baseline science verification campaign (other epochs not stated in text)  
  > "The data for SDP 81 were taken during the 2014 ALMA long baseline science verification campaign" (ALMA observations)
- pi or archival as stated: Archival ALMA data for all three lenses  
  > "We obtained data from the ALMA archive for three gravitationally lensed dusty star-forming galaxies" (ALMA observations)
- Other facility **HST/WFC3 (F110W, F160W)**: Archival 1.1 and 1.6 micron imaging used for stellar isophotes of the lens galaxies, programmes GO-12194 and GO-12659  
  > "as part of programmes GO-12194 (PI: Negrello) and GO-12659 (PI: Vieira)" (Hubble Space Telescope observations); "These data were obtained from the HST archive" (Hubble Space Telescope observations)
- External data: Source and lens redshifts of the three systems  
  > "These are galaxy-scale lenses with known source and lens redshifts" (ALMA observations) [from (cite: Negrello:2010; Spilker:2016)]
- External data: PL+MP lens model parameters for SDP 81 used for comparison  
  > "We were not able to find a good model for the data using the PL+MP parameters reported by (cite: Hezaveh:2016)." (Evidence for complex angular structure) [from (cite: Hezaveh:2016)]
- Simulation/model as data: Mock data used to test the minimum number of MultiNest live points  
  > "From tests on mock data, we have found that a minimum of 200 live points are required to recover the correct posterior" (Bayesian inference)

## Processing

### Calibration

- pipeline or manual: SPT lenses: ALMA pipeline in CASA for initial calibration  
  > "For the two SPT lenses, we used the ALMA pipeline in Common Astronomy Software Applications (CASA; (cite: casa2022)) for the initial calibration of the data." (ALMA observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: SDP 81: calibrated continuum-only dataset from the science verification project  
  > "For SDP 81, the calibrated continuum-only dataset was obtained from ALMA via the science verification project." (ALMA observations)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Several rounds; SPT lenses: phase and amplitude gain solutions per observational epoch; SDP 81: phase-only per epoch (approx. 50 mins each); minimum solution interval for S/N > 3 on >90 percent of antennas; iterated while dynamic range improved  
  > "We performed several rounds of self-calibration to correct gain offsets between observational epochs and improve the dynamic range of the data for each target." (ALMA observations); "We chose a minimum solution interval required to achieve a signal-to-noise ratio of greater than 3 for $>90$ percent of antennas" (ALMA observations); "For SDP 81, we derived phase-only corrections of each observational epoch (spanning approximately 50 mins each)." (ALMA observations)

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
- line free channels: SPT 0532-50: two spectral windows with line emission excluded; no line emission for the other SPT lens so all windows used  
  > "these spectral windows are not considered further in our analysis" (ALMA observations)
- primary beam correction: Gaussian primary-beam attenuation with half-power width 1.13 lambda/D folded into the image-plane noise covariance in the lens model  
  > "We accounted for the loss of sensitivity using a Gaussian function with a half-power width of $1.13\times\lambda/D$" (Bayesian inference)
- array combination: Long-baseline configurations only (SPT lenses); baselines > 100 m (SDP 81)  
  > "we considered only the long-baseline configurations for this experiment to maintain the higher angular resolution" (ALMA observations)
- smoothing: No additional time or frequency averaging  
  > "No additional time or frequency averaging was done." (ALMA observations)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Bayesian pixellated lens modelling technique for interferometric data  
  > "We employed the Bayesian pixellated lens modelling technique appropriate for interferometric data introduced by (cite: Powell:2021)." (Bayesian inference) [from (cite: Powell:2021)]
- Power-law convergence profile parameterisation  
  > "Following (cite: Tessore:2015) and (cite: ORiordan:2020), the 2D dimensionless surface mass density profile (convergence) is described by" (Mass distribution) [from (cite: Tessore:2015); (cite: ORiordan:2020)]
- Source regularisation details  
  > "We refer to (cite: Vegetti:2009) and (cite: Powell:2022) for more details." (Bayesian inference) [from (cite: Vegetti:2009); (cite: Powell:2022)]
- Initial optimisation before nested sampling  
  > "Following an initial optimisation (see (cite: Vegetti:2009) for details)" (Bayesian inference) [from (cite: Vegetti:2009)]
- Simultaneous lens-light and lensed-emission fitting for SDP 81 HST image  
  > "(see (cite: Ritondale:2019a) for details of this methodology)" (Isophote and isodensity shapes) [from (cite: Ritondale:2019a)]
- Iterative elliptical isophote fitting method  
  > "that uses an iterative method described by (cite: Jedrzejewski:1987) to fit elliptical isophotes to the lens galaxy light" (Isophote and isodensity shapes) [from (cite: Jedrzejewski:1987)]

### Not stated but needed to reproduce (our reading)

- Which project code (2011.0.00016.SV vs 2016.1.01374.S) belongs to which target, and the execution blocks/epochs used
- Flux, bandpass and phase calibrators and the CASA version used for the pipeline
- Source and lens redshifts and the adopted cosmology (only in Table 1 / cited papers)
- Exact self-calibration solution intervals per target, number of rounds and imaging parameters used during self-cal
- Which spectral windows were dropped for SPT 0532-50 and the spectral setup of each dataset
- Visibility weighting/noise estimation used in the lens model
- Availability of the pixellated lens modelling code (Powell et al. method) and its settings such as source grid size and number of Delaunay vertices
- MultiNest tolerance and sampling settings other than live points and efficiency
- Photutils isophote-fitting setup (radial sampling, masks, version) and the lens-light model for HST
- Numeric lens-model posteriors (Table 3) needed as answer keys are not in the supplied text

## Analysis recipe

1. **Calibrate and prepare ALMA visibilities**: ALMA pipeline calibration in CASA for the SPT lenses; archive calibrated continuum data for SDP 81; visibilities inspected, outliers flagged, line-contaminated windows dropped, SDP 81 limited to baselines > 100 m  
  > "For all of the datasets, the calibrated visibilities were inspected to confirm the quality of the pipeline calibration and any outlying data were flagged." (ALMA observations); "we only use baselines with lengths greater than 100 m" (ALMA observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Visibilities inspected to confirm pipeline calibration quality  
  > "the calibrated visibilities were inspected to confirm the quality of the pipeline calibration" (ALMA observations)
2. **Self-calibrate the visibilities**: Iterative self-calibration, accepting only solutions that increase dynamic range  
  > "only accepted calibrations that increase the dynamic range of the data and do not change the synthesised beam size by more than 10 percent" (ALMA observations)
   - software: CASA
   - parameter: Minimum solution interval giving S/N > 3 on >90 percent of antennas; phase+amplitude for SPT lenses, phase-only for SDP 81  
  > "We chose a minimum solution interval required to achieve a signal-to-noise ratio of greater than 3 for $>90$ percent of antennas" (ALMA observations)
   - fitting: _not stated_
   - validation: Dynamic range must improve and synthesised beam change by no more than 10 percent  
  > "We iterated the procedure for as long as the dynamic range of the data improved." (ALMA observations)
3. **Fit pixellated lens models (PL and PL+MP)**: Bayesian pixellated source reconstruction on Delaunay vertices with a singular power-law ellipsoid plus external shear, with and without m=3 and m=4 multipoles, directly on visibilities  
  > "This method reconstructs the source emission on vertices of Delaunay triangles adapted to the lensing magnification." (Bayesian inference); "We parameterised the underlying global mass distribution of the lens as a singular power-law ellipsoidal density profile." (Mass distribution)
   - software: MultiNest
   - parameter: 240 live points, importance sampling with constant efficiency 0.05  
  > "using 240 live points and importance sampling with a constant efficiency of 0.05 to improve the accuracy of the evidence calculation" (Bayesian inference)
   - parameter: Lens priors uniform within +/-10 to 20 percent of optimised values  
  > "we set uniform priors for the lens model parameters at $\pm10$ to 20 percent of the optimised values" (Bayesian inference)
   - parameter: Shear strength log-uniform in [-3,-1], free position angle  
  > "which was uniform in log space ($\log\Gamma\in[-3,-1]$) with a free position angle ($\theta_\Gamma\in[-90,90]$ deg)" (Bayesian inference)
   - parameter: Multipole coefficient priors uniform +/-0.01  
  > "For the multipole coefficients, we set uniform priors of $\pm0.01$." (Bayesian inference)
   - assumption: Gaussian likelihood with uncorrelated Gaussian noise  
  > "is the likelihood, which we assumed to be Gaussian." (Bayesian inference); "assuming uncorrelated, Gaussian noise" (Bayesian inference)
   - assumption: Multipole orders m=3 and m=4 only  
  > "We consider only up to order 4 here" (Mass distribution)
   - fitting: MultiNest nested sampling; source marginalised, regularisation strength free and log-uniform  
  > "were inferred using MultiNest" (Bayesian inference); "We marginalised over the source surface brightness and left the regularisation strength as a free parameter, which was uniform in log space." (Bayesian inference)
   - validation: Mock-data test that at least 200 live points recover the correct posterior  
  > "From tests on mock data, we have found that a minimum of 200 live points are required to recover the correct posterior" (Bayesian inference)
4. **Choose source regularisation type and compare PL vs PL+MP evidence**: Compared Bayesian evidence for gradient, curvature and area-weighted gradient regularisation; then compared ln evidence of PL+MP and PL  
  > "We compared the Bayesian evidence from MultiNest for the different regularisation types to determine the appropriate type for the remainder of the analysis." (Bayesian inference); "with a relative Bayes factor (difference in $\ln{\mathcal{E}}$) of 28, 75, and 120 for SDP 81, SPT 0532$-$50 and SPT 0538$-$50, respectively" (Evidence for complex angular structure)
   - software: MultiNest
   - fitting: _not stated_
   - validation: Bayes factors interpreted on the Kass and Raftery scale  
  > "strong to decisive evidence in favour of more complex angular structure" (Evidence for complex angular structure)
5. **Fit stellar isophotes of lens galaxies in HST imaging**: Drizzle archival WFC3 images, model and subtract SDP 81 lensed emission, mask interlopers, fit elliptical isophotes with Fourier modes m=3,4  
  > "processed using standard procedures within the astrodrizzle package" (Hubble Space Telescope observations); "We then subtracted model lensed emission from the data so as not to include it in our subsequent isophote fitting." (Isophote and isodensity shapes); "we used the isophote tool in the Python package photutils (cite: Bradley:2023) that uses an iterative method described by (cite: Jedrzejewski:1987) to fit elliptical isophotes to the lens galaxy light" (Isophote and isodensity shapes)
   - software: astrodrizzle, photutils
   - parameter: Images drizzled to 60 mas per pixel  
  > "the images were drizzled to 60 mas pixel$^{-1}$" (Hubble Space Telescope observations)
   - fitting: Iterative elliptical isophote fitting  
  > "that uses an iterative method described by (cite: Jedrzejewski:1987)" (Isophote and isodensity shapes)
   - validation: F110W and F160W isophote fits compared  
  > "F110W and F160W have similar isophote fits." (Isophote and isodensity shapes)
6. **Compare lensing isodensity shapes with stellar isophotes**: Compared PL+MP convergence with F160W isophotes and shape parameters versus radius; tested fixing the ellipticity position angle to the isophote value and re-optimising  
  > "This was done by fixing the ellipticity position angle to that of the isophotes and leaving all other parameters free to optimise." (Isophote and isodensity shapes)
   - fitting: _not stated_
   - validation: Fixed-PA fits give significant residuals and a more disrupted source  
  > "The best fits result in significant residual emission and a more disrupted source" (Isophote and isodensity shapes)

## Software

- **CASA** : ALMA pipeline calibration of the SPT datasets  
  > "we used the ALMA pipeline in Common Astronomy Software Applications (CASA; (cite: casa2022)) for the initial calibration of the data" (ALMA observations)
- **MultiNest** : Nested sampling of lens parameters, source and regularisation, and Bayesian evidence  
  > "were inferred using MultiNest" (Bayesian inference)
- **astrodrizzle** : Processing and drizzling of HST images  
  > "processed using standard procedures within the astrodrizzle package" (Hubble Space Telescope observations)
- **photutils** : Fitting elliptical isophotes to lens galaxy light  
  > "we used the isophote tool in the Python package photutils" (Isophote and isodensity shapes)
- **SciPy, NumPy, Matplotlib, Astropy** : General analysis packages in Python  
  > "Our analysis made use of SciPy, NumPy, Matplotlib, Astropy and Photutils packages for Python" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Relative Bayes factor ln E, PL+MP over PL, SDP 81 | 28 | not stated | dimensionless | 4 | with a relative Bayes factor (difference in $\ln{\mathcal{E}}$) of 28, 75, and 120 for SDP 81, SPT 0532$-$50 and SPT 0538$-$50, respectively |
| Relative Bayes factor ln E, PL+MP over PL, SPT 0532-50 | 75 | not stated | dimensionless | 4 | with a relative Bayes factor (difference in $\ln{\mathcal{E}}$) of 28, 75, and 120 for SDP 81, SPT 0532$-$50 and SPT 0538$-$50, respectively |
| Relative Bayes factor ln E, PL+MP over PL, SPT 0538-50 | 120 | not stated | dimensionless | 4 | with a relative Bayes factor (difference in $\ln{\mathcal{E}}$) of 28, 75, and 120 for SDP 81, SPT 0532$-$50 and SPT 0538$-$50, respectively |
| m=3 and m=4 multipole amplitudes, all three lenses | approx. 0.01 | not stated | dimensionless | 3 | We find non-zero $m=3$ and $m=4$ amplitudes of $\approx0.01$ for all three lenses |
| Convergence difference between PL and PL+MP at the Einstein radius | up to approx. 5 to 10 percent | not stated | percent | 3 | have convergence differences up to $\approx5$ to 10 percent at the Einstein radius |
| Isodensity multipole amplitudes | 0.1 to 1 percent | not stated | percent | 3 | We find isodensity multipole amplitudes in the range of 0.1 to 1 percent |
| Isophote vs isodensity ellipticity position angle offset at Einstein radius, SPT 0532-50 | about 40 | not stated | deg | 6 | the isophote ellipticity position angle is offset by about 40 deg relative to the isodensity profile at the Einstein radius |
| Isophote vs isodensity ellipticity position angle offset at Einstein radius, SPT 0538-50 | around 25 | not stated | deg | 6 | and for SPT 0538$-$50 this offset is around 25 deg |

## Qualitative findings

- Gradient regularisation gives the strongest evidence for SDP 81 and SPT 0538-50; area-weighted gradient for SPT 0532-50  
  > "We find that gradient regularisation gives the strongest evidence for SDP 81 and SPT 0538$-$50, while the area-weighted gradient gives stronger evidence for SPT 0532$-$50." (Bayesian inference)
- The evidence gain comes from smoother sources (higher regularisation), not from lower chi-squared  
  > "This indicates that the models can fit the data equally well, but the source can be smoother in the PL+MP case." (Evidence for complex angular structure)
- Ellipticities agree at the Einstein radius, but isophotes change in ellipticity and position angle with radius, not modelled in the lens model  
  > "In all cases, the ellipticities ($1-q$) are in good agreement at the Einstein radius." (Isophote and isodensity shapes)

## Claim tuples

- H: Lens galaxies need angular structure beyond a power-law ellipsoid at about 30 mas resolution | E: Pixellated lens modelling of three ALMA datasets with PL and PL+MP, compared by Bayesian evidence | R: PL+MP preferred with ln E differences of 28, 75 and 120 | F: Significant m=3 and m=4 multipoles are detected in all three lenses | **supported**
- H: The mass angular structure follows the stellar isophotes | E: Compared lensing isodensity shapes with HST F160W isophotes; fixed isophote position angle in lens fit | R: SDP 81 largely consistent, SPT 0532-50 and SPT 0538-50 offset by about 40 and 25 deg; fixed-PA fits leave residuals | F: Isophote position angles are inconsistent with the total mass distribution for the SPT lenses | **supported**
- H: Previous PL+MP solution for SDP 81 is reproducible with the same data | E: Fitted the same SDP 81 observations and tried the earlier published parameters | R: Posterior differs in ellipticity, shear and multipole amplitudes; earlier parameters give no good fit | F: Their model differs significantly from Hezaveh et al. 2016 | **supported**
- H: Existing studies restricting m=4 to boxy or discy shapes capture the angular complexity of lens galaxies | E: Free m=3 and m=4 multipoles with arbitrary orientation in three lenses | R: Multipole structure is not aligned with the ellipticity or light in general | F: Such models do not encompass the true angular complexity; a larger sample is needed | **partially**
- H: Differences between mass and light shapes reflect non-baryonic structure | E: Interpreted the offsets between isodensity and isophote shapes | R: Offsets present for two of three lenses | F: Suggests misaligned dark matter halo and/or low-mass perturbers | **partially**

## Reasoning

- Why this data: ALMA observations of bright, magnified starbursts give higher angular resolution than optical or infrared, increasing sensitivity to angular structure  
  > "suggesting that the sensitivity to angular structure increases with angular resolution" (Introduction); "given the higher angular resolution when compared to current optical or infrared telescopes" (Introduction)
- Why this method: Pixellated modelling adapted for interferometric data avoids relying on a parametric source and allows multipole flexibility  
  > "By using a pixellated lens modelling methodology adapted for interferometric data" (Introduction)
- Alternative: Three source regularisation forms (gradient, curvature, area-weighted gradient) compared by evidence  
  > "We considered three forms of regularisation: gradient, curvature, and area-weighted gradient." (Bayesian inference)
- Alternative: Isophote position angle imposed on the mass model was rejected because of residuals  
  > "The best fits result in significant residual emission and a more disrupted source" (Isophote and isodensity shapes)
- How they decided it was enough: Self-calibration iterated until dynamic range stopped improving  
  > "We iterated the procedure for as long as the dynamic range of the data improved." (ALMA observations)
- Limitation (authors): SPT 0532-50 isophotes poorly constrained because the lens is faint  
  > "SPT 0532$-$50 has the most scatter and the least well-constrained isophotes because the lens is significantly fainter than those of the other two lens systems" (Isophote and isodensity shapes)
- Limitation (authors): Only three lenses; larger sample needed for statistics  
  > "Future work involving a larger sample of lenses is needed to provide statistics on the level of complex angular structure in lensing galaxies." (Consequences for lensing studies)
- Limitation (authors): Redshifts of neighbouring galaxies are not reported, so group membership is unclear  
  > "the redshifts of any neighbours are not reported in catalogues, so it is not necessarily clear what they are or whether they are associated" (Origin of the angular structure)
- Caveat (inferred, ours): Bayes-factor gain is driven by source regularisation, not chi-squared, so it may reflect source-model degeneracy rather than real mass structure
- Caveat (inferred, ours): Priors on multipoles (+/-0.01) bound the result, and amplitudes near 0.01 sit at the prior edge
- Caveat (inferred, ours): Only m=3,4 considered; no test of m=1 or higher orders or of a composite stellar+halo model
- Caveat (inferred, ours): Isophote vs isodensity comparison needs radial matching and treats lens-light fits of a faint lens (SPT 0532-50) with large scatter
- Caveat (inferred, ours): No uncertainty or posterior numbers are given in the text for key quantities

## Reproducibility

- Data public (paper): Publicly available ALMA archive data  
  > "Here, we have analysed publicly available data from the ALMA archive" (Introduction)
- Products in archive: SDP 81 calibrated continuum-only dataset available via the science verification project  
  > "For SDP 81, the calibrated continuum-only dataset was obtained from ALMA via the science verification project." (ALMA observations)
- Missing: Lens modelling code (Powell et al. pixellated method) availability not stated
- Missing: Per-target self-calibration solution intervals and spectral windows excluded
- Missing: CASA version and calibrators
- Missing: Lens-model posterior tables and redshifts only in tables not in supplied text
- Missing: Photutils isophote fitting settings and HST lens-light model
- Data volume (inferred): Tens of GB for SPT long-baseline pipeline-calibrated data; small for the calibrated SDP 81 continuum product
- Score (inferred): 3/5, Data are public and the modelling approach and sampler settings are described, but the lens modelling code is not stated as released, calibration and self-cal details are partial, and per-target numbers live in tables.
- Rediscovery candidate: no, Data are public but the custom pixellated lens modelling code and several calibration settings are not given, so the main results cannot be redone from the text alone.

## Links

- Method: (cite: Powell:2021) (Bayesian pixellated lens modelling for interferometric data)
- Method: (cite: Powell:2022) (Multipole and shear-gradient lens modelling with VLBI data; regularisation details)
- Method: (cite: Vegetti:2009) (Source reconstruction and initial optimisation procedure)
- Companion: (cite: Hezaveh:2016) (Earlier PL+MP model of SDP 81 from the same observations, compared against)
- Companion: (cite: Rybak:2015a) (Earlier SDP 81 lens model from baselines < 2 km)
- Related: ALMA 2014 Long Baseline Campaign science verification (SDP 81)
- Related: SPT lensed dusty star-forming galaxies

## Checks

```json
{
 "quotes": 97,
 "quotes_ok": 97,
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
  "facts": 98,
  "stated": 67,
  "rate": 0.684
 },
 "evidence_ok": true
}
```
