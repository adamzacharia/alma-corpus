# Resolved Millimeter Observations of the HR 8799 Debris Disk

`2018ApJ...855...56W` | The Astrophysical Journal 2018 | first author: Wilner, David J. | arXiv: 1803.00054 | DOI: 10.3847/1538-4357/aaacd7

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: debris_disks, exoplanets
- Question: What are the structure of the HR 8799 millimeter debris belt (inner edge, width, geometry), the implied mass of planet b, and the millimeter spectral index and grain size distribution?  
  > "To better determine the properties of the cold belt of planetesimals in the HR 8799 system, we used the SMA to obtain new observations at 1.3 millimeters wavelength" (1 Introduction)
- Target **HR 8799**: coordinates 23h07m28.72 +21d08m03.3 (J2000, phase center)  
  > "The phase center was set at $\alpha=23^\text{h}07^\text{m}28.72$, $\delta=+21\ensuremath{^\circ}08\ensuremath{'}03.3\ensuremath{''}$ (J2000)" (2.1 Submillimeter Array); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00482.S
- bands: ALMA Band 6 (archival); SMA 1.3 mm; VLA 9 mm  
  > "We retrieved observations of HR 8799 from the ALMA archive that were made in Band 6 in 2015 January." (2.2 Atacama Large Millimeter/submillimeter Array)
- frequencies and spectral setup: ALMA: four 2 GHz spws, 16 MHz channels, centered 216, 218, 231, 233 GHz  
  > "the correlator setup consisted of four spectral windows with width 2 GHz and channel spacing 16 MHz, centered at 216, 218, 231 and 233 GHz, respectively." (2.2 Atacama Large Millimeter/submillimeter Array)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: ALMA 15-349 m  
  > "The observations included baseline lengths from 15 to 349 meters." (2.2 Atacama Large Millimeter/submillimeter Array)
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: ALMA 2015 January (five executions)  
  > "We calibrated the five individual scheduling block executions using the associated `CASA` 4.3.1 reduction scripts." (2.2 Atacama Large Millimeter/submillimeter Array)
- pi or archival as stated: ALMA data archival, described in Booth et al. 2016  
  > "Details of these observations are described in (cite: booth16)." (2.2 Atacama Large Millimeter/submillimeter Array)
- Line: 12CO J=2-1 (230.53800 GHz)
- Line: 13CO J=2-1 (220.39868 GHz)
- Other facility **SMA**: New 1.3 mm subcompact observations with short baselines (6-69 m)  
  > "in the subcompact configuration that provides projected baselines as short as 6 meters" (2.1 Submillimeter Array)
- Other facility **VLA**: New 9 mm D-configuration continuum  
  > "We observed the HR 8799 system with the VLA at 9 mm wavelength in the most compact D configuration." (2.3 Very Large Array)
- External data: Planet b semi-major axis 68 AU and stellar mass 1.56 Msun  
  > "we adopt the planet semi-major axis $a_\text{pl}=68$ AU and stellar mass $M_* = 1.56$ M$_{\odot}$ from dynamical analysis (cite: soummer11)" (4.2) [from (cite: soummer11)]
- External data: Dust opacity index beta_s = 1.8±0.2  
  > "$1.8\pm0.2$ for interstellar grain materials (cite: draine06)" (4.4) [from (cite: draine06)]

## Processing

### Calibration

- pipeline or manual: ALMA: archive CASA reduction scripts; SMA: MIR; VLA: VLA pipeline  
  > "The basic calibration was done using VLA pipeline processing in the `CASA` package (version 4.7.2) followed by imaging with `clean` task." (2.3 Very Large Array)
- casa version: ALMA calibration CASA 4.3.1; imaging CASA 4.7.2  
  > "Imaging was carried out with the `clean` task in `CASA` (version 4.7.2)." (2.2 Atacama Large Millimeter/submillimeter Array)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: SMA: Uranus; VLA: 3C48  
  > "The absolute flux scale was set using observations of Uranus obtained in each track, with 10% overall accuracy." (2.1 Submillimeter Array)
- flux scale uncertainty: 10% (SMA and VLA)  
  > "with an estimated accuracy of 10%" (2.3 Very Large Array)
- self calibration: _not stated_

### Imaging

- task: CASA clean  
  > "Imaging was carried out with the `clean` task in `CASA` (version 4.7.2)." (2.2 Atacama Large Millimeter/submillimeter Array)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "These images were obtained with natural weighting" (3.1 Continuum Emission)
- uv taper: 4" FWHM Gaussian (SMA-containing 1.3 mm images); 5" for VLA  
  > "those including SMA data use a $4\ensuremath{''}$ FWHM Gaussian taper" (3.1 Continuum Emission)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: ALMA: channels with CO line emission flagged  
  > "Continuum visibilities were output for analysis after flagging the channels with CO line emission, averaging in time to 30 seconds" (2.2 Atacama Large Millimeter/submillimeter Array)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: ~3.8" combined; VLA 6.2"x5.8"  
  > "which gives a beam size of $6.2\ensuremath{''} \times 5.8\ensuremath{''}$ and rms noise of 4.3 $\mu$Jy/beam" (3.1 Continuum Emission)
- final rms: VLA 4.3 uJy/beam  
  > "rms noise of 4.3 $\mu$Jy/beam" (3.1 Continuum Emission)

### Inherited from earlier work

- Visibility-fitting belt model procedure  
  > "we model the observations using the visibility fitting procedure described in (cite: macgregor13)" (3.3 SMA/ALMA Disk Model Fits) [from (cite: macgregor13)]
- ALMA observation details and reduction scripts  
  > "Details of these observations are described in (cite: booth16)." (2.2 Atacama Large Millimeter/submillimeter Array) [from (cite: booth16)]

### Not stated but needed to reproduce (our reading)

- Clean parameters (cell, image size, masks, threshold) not given
- Fixed or fitted disk center offsets and handling of ALMA/SMA weights beyond statwt
- Initial positions and full prior ranges for all MCMC parameters
- Aperture size and center for VLA flux
- Dust temperature of 39.7 K source and uncertainty propagation details

## Analysis recipe

1. **Image continuum**: Naturally weighted clean images of SMA, ALMA and combined data with taper  
  > "These images were obtained with natural weighting, and those including SMA data use a $4\ensuremath{''}$ FWHM Gaussian taper" (3.1 Continuum Emission)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit parametric belt model to visibilities**: Power-law thin belt with background point source, sampled with vissample, chi2 likelihood, emcee MCMC  
  > "we calculate synthetic visibilities using `vissample`, a python package for visibility sampling that improves on the sampling and interpolation of the `uvmodel` task" (3.3 SMA/ALMA Disk Model Fits)
   - software: vissample, emcee
   - parameter: 100 walkers, 5,000 steps each (50,000 iterations)  
  > "We explore the posterior with 50,000 iterations ($100$ walkers and $5,000$ steps each)" (3.3 SMA/ALMA Disk Model Fits)
   - assumption: Axisymmetric geometrically thin belt, radial power-law surface brightness  
  > "we make the simple assumption that the structure can be represented by an axisymmetric and geometrically thin belt" (3.3 SMA/ALMA Disk Model Fits)
   - fitting: Uniform priors for SMA (0<Rin<Rout, F>0, -3<x<3); ALMA alone requires Gaussian flux prior 3.0-4.0 mJy and logistic Rout prior; lnL=-chi2/2  
  > "we adopt uniform priors for all parameters, in particular $0<R_\text{in}<R_\text{out}$, $F_\text{belt}>0$, and $-3<x<3$." (3.3 SMA/ALMA Disk Model Fits)
   - validation: Gelman-Rubin R<1.1; noise-like residual image  
  > "check that the Gelman-Rubin statistic (cite: gelman14) is $\hat{R}<1.1$ for all parameters to ensure convergence" (3.3 SMA/ALMA Disk Model Fits)
3. **Measure VLA 9 mm flux**: Circular aperture photometry in CASA with disk diameter from model; noise from ten random apertures  
  > "We determine the uncertainty by measuring the flux density in the same circular aperture at ten random locations in the image and taking the average." (3.4 VLA 9 millimeter Flux Estimate)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
4. **Convert inner edge to planet b mass**: Pearce & Wyatt formula Rin = a + 5a(Mpl/3M*)^(1/3) applied to Rin posterior  
  > "$R_\text{in} = a_\text{pl}+5a_\text{pl}(M_\text{pl}/3M_{*})^{1/3}$, taken in the limit of zero eccentricity" (4.2)
   - assumption: a_pl=68 AU, M*=1.56 Msun, planet b truncates belt  
  > "we adopt the planet semi-major axis $a_\text{pl}=68$ AU and stellar mass $M_* = 1.56$ M$_{\odot}$" (4.2)
   - fitting: _not stated_
   - validation: _not stated_
5. **Spectral index and grain size slope**: alpha_mm from 1.3 and 9 mm fluxes; q=(alpha_mm-alpha_Pl)/beta_s+3  
  > "$q = (\alpha_\text{mm}-\alpha_\text{Pl})/\beta_s +3$" (4.4)
   - assumption: beta_s=1.8±0.2; alpha_Pl=1.92±0.10 for 39.7 K dust  
  > "$\alpha_\text{Pl}$ is the spectral index of the Planck function, $1.92\pm0.10$" (4.4)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.2 (4.3.1 for ALMA calibration): Imaging, statwt, VLA pipeline, flux measurement  
  > "Fourier inversion for continuum and spectral line imaging and `clean` deconvolution were done in the `CASA` software package (version 4.7.2)." (2.1 Submillimeter Array)
- **MIR** : SMA calibration  
  > "All of the basic calibration was performed using standard procedures in the MIR software package." (2.1 Submillimeter Array)
- **vissample** : Synthetic visibility sampling of models  
  > "we calculate synthetic visibilities using `vissample`" (3.3 SMA/ALMA Disk Model Fits)
- **emcee** : MCMC posterior sampling  
  > "We make use of the `emcee` package (cite: foreman13) to sample the posterior probability distribution" (3.3 SMA/ALMA Disk Model Fits)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Belt inner edge Rin (SMA+ALMA) | 104 | +8/-12 | AU | 2 | $104. (+8., -12.)$ |
| Belt outer edge Rout (SMA+ALMA) | 361 | +16/-18 | AU | 2 | $361. (+16., -18.)$ |
| Total belt flux at 1.3 mm (SMA+ALMA) | 3.44 | +0.31/-0.56 | mJy | 2 | $3.44 (+0.31, - 0.56)$ |
| Inclination | 32.8 | +5.6/-9.6 | deg | 2 | $32.8 (+5.6, -9.6)$ |
| Position angle | 35.6 | +9.4/-10.1 | deg | 2 | $35.6 (+9.4, -10.1)$ |
| Power-law index x | -0.38 | ±0.47 | dimensionless | 2 | the best-fit power law index for the millimeter emission radial profile is $x=-0.38\pm0.47$ |
| VLA 9 mm flux | 32.6 | 9.9 | uJy | 3 | $F_\text{9mm} = 32.6\pm9.9$ $\mu$Jy |
| Planet b mass | 5.8 | +7.9/-3.1 | MJup | 4 | $M_\text{pl} = 5.8_{-3.1}^{+7.9}$ M$_{\rm Jup}$ |
| Millimeter spectral index | 2.41 | 0.17 | dimensionless | 5 | $\alpha_\text{mm} = 2.41\pm0.17$ |
| Grain size index q | 3.27 | 0.10 | dimensionless | 5 | $q = 3.27\pm0.10$ |

## Qualitative findings

- No significant azimuthal asymmetries in residuals; 13CO emission shows no rotation signature and is likely cloud-related  
  > "the imaged residuals reveal no significant azimuthal brightness asymmetries" (3.3)

## Claim tuples

- H: Is the mm belt broad and consistent with planet orbital geometry? | E: Fit belt model to combined SMA+ALMA visibilities | R: Rin=104 AU, Rout=361 AU, i=32.8, PA=35.6 | F: Broad belt compatible with coplanarity with planets within large uncertainties | **supported**
- H: Can planet b truncate the belt inner edge? | E: Translate Rin posterior to mass via chaotic zone formula | R: 5.8 (+7.9/-3.1) MJup | F: No need for an additional outer planet; consistent with hot-start models | **supported**
- H: Is the grain size distribution consistent with a collisional cascade? | E: Spectral index from SMA+ALMA and VLA fluxes | R: alpha=2.41±0.17, q=3.27±0.10 | F: Close to classical collisional cascade | **supported**

## Reasoning

- Why this data: SMA short baselines needed to recover large-scale emission missed by ALMA  
  > "sensitive to larger angular scales than the previous millimeter interferometer studies" (1 Introduction)
- Why this method: _not stated_
- Alternative: Image-based fitting for VLA rejected because of difficulty choosing a function for the visibilities  
  > "We adopt this image-based approach instead of fitting to the millimeter visibilities due to the difficulty in selecting a function" (3.4)
- How they decided it was enough: _not stated_
- Limitation (authors): ALMA alone gives no constraint on Rout and flux without strong priors; planet mass uncertainties are large; VLA detection ~3 sigma  
  > "we must impose strong priors on both $R_\text{out}$ and $F_\text{tot}$" (3.3)
- Caveat (inferred, ours): Planet mass depends on a single assumed truncation formula and circular orbit
- Caveat (inferred, ours): Spectral index relies on a ~3 sigma VLA flux and an assumed 39.7 K dust temperature
- Caveat (inferred, ours): Simple power-law belt may not capture the structure; SMA flux partly in extended cloud confusion

## Reproducibility

- Data public (paper): ALMA archival; SMA and VLA data not stated as public  
  > "We retrieved observations of HR 8799 from the ALMA archive" (2.2)
- Products in archive: _not stated_
- Code: vissample publicly available on GitHub  
  > "`vissample` is publicly available at <https://github.com/AstroChem/vis_sample>" (footnote)
- Missing: SMA and VLA raw data access not stated
- Missing: Clean and image parameters
- Missing: MCMC initialization
- Data volume (inferred): ~50-100 GB for ALMA archival raw data; SMA and VLA additional
- Score (inferred): 3/5, Model and sampler are described with parameters and results in a table, but SMA/VLA data availability and imaging settings are missing.
- Rediscovery candidate: no, Key SMA data are not stated as public, so the main result cannot be redone from ALMA data alone.

## Links

- Method: (cite: macgregor13) (Visibility-fitting belt model procedure)
- Companion: (cite: booth16) (Original ALMA analysis of the same data)

## Checks

```json
{
 "quotes": 61,
 "quotes_ok": 61,
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
  "facts": 76,
  "stated": 44,
  "rate": 0.579
 },
 "evidence_ok": true
}
```
