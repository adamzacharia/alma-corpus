# The VLA/ALMA Nascent Disk and Multiplicity (VANDAM) Survey of Orion Protostars. II. A Statistical Characterization of Class 0 and Class I Protostellar Disks

`2020ApJ...890..130T` | The Astrophysical Journal 2020 | first author: Tobin, John J. | arXiv: 2001.04468 | DOI: 10.3847/1538-4357/ab6f64

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: star_formation, protoplanetary_disks
- Question: What are the dust disk radii and masses of Class 0, Class I and Flat Spectrum protostars in Orion, and how do they evolve and compare with Class II disks, regions and simulations?  
  > "We use the dust continuum emission at 0.87 mm and 9 mm to measure the dust disk radii and masses toward the Class 0, Class I, and Flat Spectrum protostars" (abstract)
- Target **328 Orion A and B protostars (HOPS sample)**: coordinates per-source RA/Dec in Table 2  
  > "The sample of protostars is drawn from the *Herschel* Orion Protostar Survey" (2.1 The Sample); "we take advantage of the availability of *Gaia* data for a large sample of more evolved members within Orion, enabling us to estimate the distance toward each protostellar system." (2.1 The Sample); z/distance ~350-440 pc, per-source estimates  
  > "The sample of protostars is drawn from the *Herschel* Orion Protostar Survey" (2.1 The Sample); "we take advantage of the availability of *Gaia* data for a large sample of more evolved members within Orion, enabling us to estimate the distance toward each protostellar system." (2.1 The Sample); distance from Gaia DR2 parallaxes of nearby YSOs, neural-network interpolation (Appendix A)  
  > "The sample of protostars is drawn from the *Herschel* Orion Protostar Survey" (2.1 The Sample); "we take advantage of the availability of *Gaia* data for a large sample of more evolved members within Orion, enabling us to estimate the distance toward each protostellar system." (2.1 The Sample)

## Data provenance

- ALMA projects: 2015.1.00041.S
- bands: ALMA 0.87 mm (Band 7); VLA Ka-band 9 mm  
  > "ALMA at 0.87 mm at a resolution of $\sim$0.1$''$ (40 au), including observations with the VLA at 9 mm" (abstract)
- frequencies and spectral setup: Two continuum basebands centered at 333 and 344 GHz, 1.875 GHz each; 12CO and 13CO (3-2) basebands; aggregate continuum ~4.75 GHz  
  > "resulting in an aggregate continuum bandwidth of $\sim$4.75 GHz" (2.2 ALMA 0.87 mm Observations)
- continuum bandwidth: _not stated_
- arrays: Three scheduling blocks each executed three times (nine executions)  
  > "Each scheduling block was successfully executed three times for nine executions in total." (2.2 ALMA 0.87 mm Observations)
- configurations: _not stated_
- baselines: ~15 m to ~3700 m  
  > "the combined datasets sample baseline lengths from $\sim$15 m to $\sim$3700 m" (2.2 ALMA 0.87 mm Observations)
- angular resolution: ~0.11'' (44 au) at robust=0.5  
  > "yielding a synthesized beam of $\sim$0.11$''$ (44 au)" (2.2 ALMA 0.87 mm Observations)
- max recoverable scale: _not stated_
- sensitivity: continuum RMS 0.31 mJy/beam  
  > "The typical root-mean-squared (RMS) noise of the continuum, $^{12}$CO, and $^{13}$CO are 0.31 mJy beam$^{-1}$" (2.2 ALMA 0.87 mm Observations)
- time on source: ~0.9 minutes per source  
  > "the total time on each source was $\sim$0.9 minutes" (2.2 ALMA 0.87 mm Observations)
- observing dates: Six executions 2016 September, three 2017 July  
  > "Six were executed in 2016 September, and three were executed in 2017 July." (2.2 ALMA 0.87 mm Observations)
- pi or archival as stated: _not stated_
- Line: 12CO J=3-2 (345.79599 GHz)
- Line: 13CO J=3-2 (330.58797 GHz)
- Other facility **VLA Ka-band A-configuration**: 9 mm continuum toward 148 protostars (Class 0 and youngest Class I)  
  > "We conducted observations with the VLA in A-configuration between 2016 October 20 and 2017 January 07" (2.3 VLA Observations)
- Other facility **Herschel Orion Protostar Survey / Spitzer**: Sample selection, Lbol, Tbol, classes  
  > "The sample of protostars is drawn from the *Herschel* Orion Protostar Survey" (2.1 The Sample)
- Other facility **Gaia DR2**: Parallaxes for distance estimates  
  > "selecting sources that have Gaia detection with $\sigma_{\pi}$ $<$ 0.2 mas" (Distance Estimates)
- External data: Protostar Lbol, Tbol, classes and SEDs  
  > "We selected all Class 0, Class I, and Flat Spectrum protostars from the survey that had reliable measurements of bolometric temperature" (2.1 The Sample) [from (cite: fischer2010; stutz2013; furlan2016)]
- External data: Dust opacity 1.84 cm2/g at 0.87 mm  
  > "We adopt $\kappa_{0.87mm}$ = 1.84 cm$^2$ g$^{-1}$ from (cite: ossenkopf1994)" (2.4 Data Analysis) [from (cite: ossenkopf1994)]
- External data: Class II and other protostellar disk mass/radius samples for comparison  
  > "the Lupus disks are from (cite: ansdell2016), the Chamaeleon disks are from (cite: pascucci2016), the Upper Sco disks are from (cite: barenfeld2016) and the Taurus disks are from (cite: tripathi2017)" (4.2 Protostellar Dust Disk Masses versus Class II Dust Disk Masses) [from ansdell2016; pascucci2016; barenfeld2016; tripathi2017; tychoniec2018; williams2019; sheehan2017b]
- Simulation/model as data: Bate (2018) SPH cluster simulation disk masses and radii; Hennebelle et al. (2016) analytic disk radii; Kuffmeier (2017) MHD zoom-ins  
  > "we will focus on comparing our results to those found in the (cite: bate2018) simulations and to a more limited set of MHD zoom-in simulations from (cite: kueffmeier2017)" (4.5 Comparison to Simulations of Protostellar Disks)
- Simulation/model as data: RADMC-3D grid of disk+envelope models used to derive average dust temperature scaling  
  > "we used a grid of radiative transfer models to determine the average dust temperatures" (Average Disk Dust Temperature)

## Processing

### Calibration

- pipeline or manual: Manual reduction by Dutch Allegro ARC node using CASA  
  > "The data were manually reduced by the Dutch Allegro ARC Node using the Common Astronomy Software Application (cite: mcmullin2007)." (2.2 ALMA 0.87 mm Observations)
- casa version: CASA 4.7.2 for ALMA imaging; VLA pipeline in CASA 4.4.0 (4.5.2 for delay-error fix)  
  > "The continuum and spectral line data cubes were imaged using the *clean* task of CASA 4.7.2" (2.2 ALMA 0.87 mm Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0510+1800 in some executions (variable quasar)  
  > "The manual reduction was necessary to compensate for variability of the quasar J0510+1800 that was used for absolute flux calibration in some executions." (2.2 ALMA 0.87 mm Observations)
- flux scale uncertainty: ~10%  
  > "The absolute flux calibration accuracy is expected to be $\sim$10%" (2.2 ALMA 0.87 mm Observations)
- self calibration: Up to three rounds phase-only if peak S/N>10; solints scan length, 12.08 s, 3.02 s  
  > "we performed up to three rounds of phase-only self-calibration on the continuum data to increase the S/N." (2.2 ALMA 0.87 mm Observations)

### Imaging

- task: CASA clean (ALMA, 4.7.2); VLA clean in CASA 4.5.1  
  > "The continuum data for all sources were imaged using the *clean* task in CASA 4.5.1" (2.3 VLA Observations)
- deconvolver: _not stated_
- weighting robust: Briggs robust=0.5 (robust=2 for non-detections; also 0 and -0.5 made); VLA Natural, nterms=2  
  > "The aggregate continuum image was reconstructed using *Briggs* weighting with a *robust* parameter of *0.5*" (2.2 ALMA 0.87 mm Observations)
- uv taper: Continuum uv>25 kλ; line data natural weighting >50 kλ with 500 kλ outer taper  
  > "The continuum images are reconstructed only using uv-points at baselines $>$25 k$\lambda$ to mitigate striping" (2.2 ALMA 0.87 mm Observations)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Line data averaged by 2 (12CO) and 4 (13CO) channels  
  > "The spectral line observations were averaged by two and four channels for $^{12}$CO and $^{13}$CO, respectively, to reduce noise." (2.2 ALMA 0.87 mm Observations)
- final beam: ~0.11'' (ALMA continuum); ~0.08'' (VLA)  
  > "a synthesized beam of $\sim$0.08$''$ (32 au)" (2.3 VLA Observations)
- final rms: 0.31 mJy/beam (ALMA); ~7-8 µJy/beam (VLA)  
  > "The final images have an RMS noise of $\sim$7-8 $\mu$Jy beam$^{-1}$" (2.3 VLA Observations)

### Inherited from earlier work

- Gaussian-fit disk radius and mass-estimation approach, dust temperature scaling normalisation reused for Perseus comparison  
  > "we scaled the dust temperature using L$_{bol}$ and the same temperature normalization that was used for the Orion protostars" (4.1 Protostellar Dust Disk Masses) [from Tychoniec et al. (cite: tychoniec2018)]
- Gaussian CDF fit of cumulative distributions to derive mean  
  > "as has been demonstrated by (cite: williams2019)" (3.3 Distribution of Protostellar Dust Disk Masses) [from (cite: williams2019)]

### Not stated but needed to reproduce (our reading)

- Line-free channel selection and exact continuum spectral-window flagging
- Exact imaging mask/threshold, niter, image size and cell size
- Which source flux/size entries were taken as upper limits and detection criteria for fitting imfit regions
- Distance-estimation neural network training details/hyperparameters
- Full Appendix B model parameters (inclination/hour angle simulation process) for reproducing temperature law
- Self-cal solint choices per source

## Analysis recipe

1. **Image continuum and self-calibrate**: Phase-only self-calibration then clean imaging with Briggs robust 0.5, uv>25 kλ  
  > "The aggregate continuum image was reconstructed using *Briggs* weighting with a *robust* parameter of *0.5*" (2.2 ALMA 0.87 mm Observations)
   - software: CASA
   - parameter: self-cal only when peak S/N>10; applymode=calonly  
  > "we only attempted self calibration when the S/N of the emission peak was $>$10" (2.2 ALMA 0.87 mm Observations)
   - fitting: _not stated_
   - validation: Flux densities compared across executions consistent with ~10%  
  > "comparisons of the observed flux densities for the science targets during different executions are consistent with this level of accuracy" (2.2 ALMA 0.87 mm Observations)
2. **Measure flux, size of each source**: Elliptical Gaussian fits; disk radius = 2σ deconvolved major axis (FWHM×2.0/2.355 × distance)  
  > "We fit elliptical Gaussians to each detected source using the *imfit* task of CASA 4.7.2." (2.4 Data Analysis)
   - software: CASA imfit
   - parameter: sources with unreliable sizes (fixed to beam) excluded from radius analysis  
  > "Weak sources that required their major axis, minor axis, and position angle to be fixed to the synthesized beam are not included in these plots." (3.3 Distribution of Protostellar Dust Disk Radii)
   - assumption: Gaussian 2σ approximates disk radius (~95% of flux)  
  > "This radius will contain $\sim$95% of the flux density within the fitted Gaussian." (2.4 Data Analysis)
   - fitting: _not stated_
   - validation: Residuals inspected visually; caveat radii underestimated for large disks  
  > "Visual inspection of the Gaussian fits reveals that there are often residuals outside the Gaussian model." (3.3 Distribution of Protostellar Dust Disk Radii)
3. **Derive dust disk masses**: Optically thin isothermal M=D²Fν/(κνBν(Tdust)) with Tdust=43 K (L/Lsun)^0.25  
  > "We make the assumption that the disk is isothermal and optically thin" (2.4 Data Analysis)
   - parameter: κ0.87mm=1.84 cm2/g; κ9.1mm=0.13 cm2/g (β=1)  
  > "at 9.1 mm we adopt a dust opacity of 0.13 cm$^2$ g$^{-1}$" (2.4 Data Analysis)
   - assumption: T0 = 43 K for 1 Lsun at 50 au, from RADMC-3D models  
  > "where T$_{0}$ = 43 K, and we scale this using L$_{bol}$ for each protostellar system" (2.4 Data Analysis)
   - fitting: _not stated_
   - validation: Temperature law checked with RADMC-3D model grid  
  > "We also confirmed that the average disk dust temperature scales $\propto$ L$^{0.25}$ considering the full set of disk radii" (Average Disk Dust Temperature)
4. **Distribution analysis by class**: Kaplan-Meier survival analysis with left-censoring, log-rank and Anderson-Darling tests, Gaussian CDF fit for mean  
  > "The plots were constructed using survival analysis and the Kaplan-Meier estimator as implemented in the Python package *lifelines*" (3.3 Distribution of Protostellar Dust Disk Masses)
   - software: lifelines, scipy
   - parameter: uncertainties from fitting the 1σ upper/lower bounds of survival CDF  
  > "we performed the same fit on the 1$\sigma$ upper and lower bounds of the cumulative dust disk mass distributions" (3.3 Distribution of Protostellar Dust Disk Masses)
   - assumption: Distributions approximately log-normal  
  > "We note, however, that the observed distributions are not precisely Gaussian" (3.3 Distribution of Protostellar Dust Disk Masses)
   - fitting: scipy curve_fit of Gaussian survival function  
  > "using the *curve_fit* function within *scipy*" (3.3 Distribution of Protostellar Dust Disk Masses)
   - validation: Anderson-Darling test cross-check  
  > "we obtained consistent results from the Anderson-Darling test" (3.3 Distribution of Protostellar Dust Disk Masses)
5. **Gravitational stability (Toomre Q) estimates**: Q≈2(M*/Md)(H/R) with fiducial M*=0.25 Msun, gas-to-dust 100  
  > "we multiply the derived dust disk mass by 100, the gas-to-dust ratio in the interstellar medium" (4.4 Potential for Gravitationally Unstable Disks)
   - assumption: T ∝ R^-0.46 from models  
  > "the relationship that T $\propto$ R$_{disk}^{-0.46}$" (4.4 Potential for Gravitationally Unstable Disks)
   - fitting: _not stated_
   - validation: Envelope-contaminated candidates screened by image inspection  
  > "HOPS-317-B, HOPS-402, HOPS-400-B, HOPS-87, HOPS-403, HOPS-398, and HOPS-404 are likely to have significant envelope contamination" (4.4 Potential for Gravitationally Unstable Disks)

## Software

- **CASA** 4.7.2 (ALMA imaging), 4.4.0/4.5.2/4.5.1 (VLA): calibration, clean imaging, imfit  
  > "using the *imfit* task of CASA 4.7.2" (2.4 Data Analysis)
- **lifelines** v0.21.1: Kaplan-Meier survival analysis and log-rank test  
  > "To statistically compare the distributions, we used the log rank test as implemented in *lifelines*." (3.3 Distribution of Protostellar Dust Disk Masses)
- **scipy** : power-law fits, curve_fit of Gaussian CDF  
  > "is fit with a constant spectral index ($\alpha$) of 2.24$\pm$0.03 using *scipy*" (3.2 Continuum Emission at 0.87 mm and 9 mm)
- **RADMC-3D** : Disk+envelope dust temperature models  
  > "We used the Monte Carlo dust radiative transfer code RADMC-3D (cite: dullemond2012)" (Average Disk Dust Temperature)
- **PyTorch** : Neural network for distance interpolation  
  > "We then used a fully connected neural network constructed in PyTorch with 1 hidden layer and 300 neurons" (Distance Estimates)
- **Astropy / APLpy** : Analysis and plotting  
  > "Astropy (cite: astropy2013; astropy2018), APLpy (cite: aplpy), CASA (cite: mcmullin2007)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mean dust disk radius, Class 0 (all) | 44.9 | +5.8/-3.4 | au | 4 | 44.9$^{+5.8}_{-3.4}$, 37.0$^{+4.9}_{-3.0}$, and 28.5$^{+3.7}_{-2.3}$ au |
| Mean dust disk radius, Class I (all) | 37.0 | +4.9/-3.0 | au | 4 | 44.9$^{+5.8}_{-3.4}$, 37.0$^{+4.9}_{-3.0}$, and 28.5$^{+3.7}_{-2.3}$ au |
| Mean dust disk radius, Flat Spectrum (all) | 28.5 | +3.7/-2.3 | au | 4 | 44.9$^{+5.8}_{-3.4}$, 37.0$^{+4.9}_{-3.0}$, and 28.5$^{+3.7}_{-2.3}$ au |
| Mean dust disk mass, Class 0 (all) | 25.9 | +7.7/-4.0 | Earth masses | 4 | 25.9$^{+7.7}_{-4.0}$, 14.9$^{+3.8}_{-2.2}$, 11.6$^{+3.5}_{-1.9}$ M$_{\ensuremath{\oplus}}$ |
| Mean dust disk mass, Class I (all) | 14.9 | +3.8/-2.2 | Earth masses | 4 | 25.9$^{+7.7}_{-4.0}$, 14.9$^{+3.8}_{-2.2}$, 11.6$^{+3.5}_{-1.9}$ M$_{\ensuremath{\oplus}}$ |
| Mean dust disk mass, Flat Spectrum (all) | 11.6 | +3.5/-1.9 | Earth masses | 4 | 25.9$^{+7.7}_{-4.0}$, 14.9$^{+3.8}_{-2.2}$, 11.6$^{+3.5}_{-1.9}$ M$_{\ensuremath{\oplus}}$ |
| Mean dust disk mass, Class 0 non-multiples | 38.1 | +18.9/-8.4 | Earth masses | 4 | we find mean dust disk masses of 38.1$^{+18.9}_{-8.4}$, 13.4$^{+4.6}_{-2.4}$, and 14.3$^{+6.5}_{-3.0}$ M$_{\ensuremath{\oplus}}$ |
| ALMA detections | 286 of 328 targeted fields; 379 discrete sources | not stated | count | 2 | We detected continuum emission associated with the protostars in 286 fields with at least S/N $>$ 3, corresponding to a 87% detection rate. |
| 0.87-9 mm flux density spectral index | 2.24 | 0.03 | dimensionless | 2 | fit with a constant spectral index ($\alpha$) of 2.24$\pm$0.03 using *scipy* |
| Fraction of disks with R>50 au | ~36% (153/(379+42)) | not stated | percent | 4 | the frequency of protostellar disks with radii greater than $\sim$50 au is $\sim$36% (153/(379+42)) |
| Median dust disk mass Class 0/I/Flat (all) | 25.7, 15.6, 13.8 | not stated | Earth masses | 4 | we find median dust disk masses of 25.7, 15.6, and 13.8 M$_{\ensuremath{\oplus}}$, respectively |
| Mean cos(i) | 0.601 (median 0.596) | not stated | dimensionless | 2 | The median and mean values of cos($i$) are 0.596 and 0.601, respectively |

## Qualitative findings

- Class I and Flat Spectrum mass distributions are statistically consistent; Class 0 masses larger  
  > "However, the differences between the Class I and Flat Spectrum sources are not statistically significant." (3.3 Distribution of Protostellar Dust Disk Masses)
- No significant differences in disk properties between Orion subregions  
  > "the properties of protostellar disks do not show statistically significant differences between sub-regions within the Orion molecular clouds" (3.6 Regional Comparison of Disk Properties)

## Claim tuples

- H: Do protostellar dust disk masses and radii decrease from Class 0 to Flat Spectrum? | E: Gaussian fits to 0.87 mm continuum, mass and radius distributions via survival analysis | R: Mean masses 25.9/14.9/11.6 Earth masses; mean radii 44.9/37.0/28.5 au | F: Masses decrease with evolution; radii decrease or stay constant, contrary to disk-growth predictions (dust radii only) | **supported**
- H: Are protostellar disks more massive than Class II disks? | E: Compare Orion mass distributions with Class II surveys | R: Factor >4 larger | F: Solid growth toward planet cores may begin in protostellar phase | **supported**
- H: Do disk properties vary with region in Orion? | E: Log-rank tests among northern ISF, L1641+southern ISF, Orion B | R: No significant differences | F: Properties are similar across environments | **supported**
- H: Are large (>50 au) protostellar disks common? | E: Count disks with deconvolved 2σ radius >50 au | R: At least 146 (35%) out of 379+42 | F: Large disks are not rare | **supported**

## Reasoning

- Why this data: Orion provides a much larger protostar sample; VLA 9 mm probes optically thick inner disks  
  > "even at submillimeter wavelengths the protostellar disks can be optically thick; therefore, VLA observations at 9 mm are crucial to examine the inner disks" (1 Introduction)
- Why this method: Gaussian fitting is simple and fast for large samples; curve-of-growth and Nuker profiles less suited with envelopes  
  > "While Gaussian fitting has limitations, its advantage lies in its simplicity and ability to rapidly fit a large number of sources." (2.4 Data Analysis)
- Alternative: Curve of growth and Nuker profile radius methods judged less suitable for protostellar disks  
  > "These methods and assumptions are not always possible and/or reliable for protostellar disks, due in large part to the surrounding envelope." (2.4 Data Analysis)
- How they decided it was enough: _not stated_
- Limitation (authors): Optically thick emission yields mass underestimates; envelope contamination possible; Gaussian radius biases  
  > "If the dust emission is not optically thin, then the masses will be lower limits." (2.4 Data Analysis)
- Caveat (inferred, ours): Single-Gaussian radius definition not comparable with 90%-flux radii of other surveys
- Caveat (inferred, ours): Mass depends on assumed opacity and L-scaled temperature; Perseus/Ophiuchus discrepancies unresolved
- Caveat (inferred, ours): Distance from neural-net interpolation uncertain (flat 10 pc error)
- Caveat (inferred, ours): Median/mean statistics mix multiples sharing one Lbol

## Reproducibility

- Data public (paper): ALMA project data and Harvard Dataverse images  
  > "The images for each figure are available from the Harvard Dataverse (https://dataverse.harvard.edu) (cite: alma_images; vla_images)." (Images of all Protostars)
- Products in archive: _not stated_
- Missing: Cell/image size, masks, niter
- Missing: Line-free channels and spectral window flagging
- Missing: Neural-network distance training details
- Missing: Complete RADMC-3D setup details
- Data volume (inferred): ~200-500 GB ALMA raw (nine executions, 328 fields) plus ~100 VLA datasets
- Score (inferred): 4/5, Public data, clear recipe and tables of per-source values; some imaging parameters unstated.
- Rediscovery candidate: yes, Public ALMA data, defined Gaussian-fit and mass recipe, numeric results; but heavy data volume and some missing settings.

## Links

- Method: (cite: ossenkopf1994) (Dust opacity adopted)
- Method: (cite: dullemond2012) (RADMC-3D used for temperature models)
- Method: (cite: williams2019) (Log-normal CDF approach for disk mass distributions)
- Companion: (cite: seguracox2016; seguracox2018) (Earlier VANDAM VLA Perseus disk results)
- Companion: (cite: tychoniec2018) (VLA Perseus disk masses compared)
- Related: VANDAM
- Related: Herschel Orion Protostar Survey (HOPS)
- Related: CALYPSO
- Related: MASSES

## Checks

```json
{
 "quotes": 88,
 "quotes_ok": 88,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 86,
  "stated": 65,
  "rate": 0.756
 },
 "evidence_ok": true
}
```
