# The unexpected narrowness of eccentric debris rings: a sign of eccentricity during the protoplanetary disc phase

`2020RSOS....700063K` | Royal Society Open Science 2020 | first author: Kennedy, Grant M. | arXiv: 2005.14200 | DOI: 10.1098/rsos.200063

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type archival_reuse

## Science

- Fields: debris_disks
- Question: Are the eccentric debris rings of Fomalhaut and HD 202628 as wide as expected from secular perturbation by an eccentric planet acting on initially near-circular planetesimals (width ~2ae_f), or narrower?  
  > "This paper shows that the eccentric debris rings seen around the stars Fomalhaut and HD 202628 are narrower than expected in the standard eccentric planet perturbation scenario" (abstract); "the null hypothesis is that the ring widths are consistent with that expected from secular perturbations and initially near-zero eccentricities" (The ring widths of Fomalhaut and HD 202628)
- Target **Fomalhaut**: coordinates _not stated_; z/distance 7.7 pc  
  > "at the 7.7 pc distance of Fomalhaut" (The ring widths of Fomalhaut and HD 202628); distance from _not stated_
- Target **HD 202628**: coordinates _not stated_; z/distance 23.8 pc  
  > "at the 23.8 pc distance of HD 202628" (The ring widths of Fomalhaut and HD 202628); distance from _not stated_

## Data provenance

- ALMA projects: _none stated_
- bands: Band 6 (1.3 mm), both targets  
  > "The Fomalhaut observations were at 1.3 mm (band 6)" (The ring widths of Fomalhaut and HD 202628); "The HD 202628 observations were also at 1.3 mm and use a single pointing." (The ring widths of Fomalhaut and HD 202628)
- frequencies and spectral setup: Fomalhaut: seven pointings; visibilities averaged to a single channel per spw  
  > "seven pointings were required to cover the disc adequately" (The ring widths of Fomalhaut and HD 202628); "spectral averaging to a single channel per spectral window (spw)" (Fomalhaut)
- continuum bandwidth: _not stated_
- arrays: HD 202628: 12m array data used; ACA data excluded  
  > "were obtained from the ALMA archive and calibrated using the observatory-supplied script (the ACA data have insufficient resolution to be valuable here, and are dominated by a background source, so were not included)" (HD 202628)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Fomalhaut 1.6 x 1.2 arcsec; HD 202628 0.9 x 0.8 arcsec  
  > "have a spatial resolution of $1.6 \times 1.2$ arcsec resolution" (The ring widths of Fomalhaut and HD 202628); "The spatial resolution is $0.9 \times 0.8$ arcsec" (The ring widths of Fomalhaut and HD 202628)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Fomalhaut: same data as MacGregor et al. 2017; HD 202628: 12m data from Faramaz et al. 2019 taken from the ALMA archive  
  > "The same seven-pointing data of the Fomalhaut disc that were presented in MacGregor" (Fomalhaut); "were obtained from the ALMA archive" (HD 202628)
- Other facility **ALMA archive**: Archival 12m-array 1.3 mm visibilities of HD 202628 (and Fomalhaut data previously presented by MacGregor et al.)  
  > "were obtained from the ALMA archive" (HD 202628)
- External data: Fomalhaut ring FWHM of 13-13.5 au  
  > "with these works finding full-width at half-maxima (FWHM) of 13-13.5 au" (The ring widths of Fomalhaut and HD 202628) [from White et al. (cite: 2017MNRAS.466.4201W); MacGregor et al. (cite: 2017ApJ...842....8M)]
- External data: Fomalhaut proper eccentricity 0.06 +/- 0.04 and forced eccentricity 0.12 +/- 0.01  
  > "finds a proper eccentricity ($0.06 \pm 0.04$) that is consistent with the forced eccentricity (which was $0.12 \pm 0.01$)" (The ring widths of Fomalhaut and HD 202628) [from MacGregor et al. (cite: 2017ApJ...842....8M)]
- External data: Fomalhaut pericenter angle 23 +/- 4 deg from earlier modelling  
  > "This value is most likely different to the $23 \pm 4^\circ$ found by MacGregor" (Fomalhaut) [from MacGregor et al. (cite: 2017ApJ...842....8M)]
- External data: HD 202628 ring width of 22 au and best-fit eccentricity of 0.09  
  > "the width was found to be 22 au" (The ring widths of Fomalhaut and HD 202628); "Given their best-fit eccentricity of 0.09" (The ring widths of Fomalhaut and HD 202628) [from Faramaz et al. (cite: 2019AJ....158..162F)]
- External data: Eccentricity and relative width of selected debris discs (Figure 9 comparison sample)  
  > "shows the eccentricity and relative width of selected debris discs" (Eccentric ring origins - why so narrow?) [from Hughes et al. (cite: 2018ARA&A..56..541H)]
- Simulation/model as data: Analytic secular-perturbation particle model images (N = 10^7 particles), compared with visibilities; no n-body simulation  
  > "This assumption means that the models are created analytically, with no need for $n$-body simulations." (The model); "Model images computed using $N=10^7$ are compared with the ALMA visibilities using the" (The model)

## Processing

### Calibration

- pipeline or manual: Observatory-supplied calibration script (both targets)  
  > "The data were calibrated using the observatory-supplied script, with the only additional steps being spectral averaging to a single channel per spectral window (spw)" (Fomalhaut); "were obtained from the ALMA archive and calibrated using the observatory-supplied script" (HD 202628)
- casa version: CASA 5.6 (used for statwt reweighting of Fomalhaut)  
  > "30-second time averaging, and re-weighting of all visibilities using the CASA 5.6" (Fomalhaut)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting (image used for Fomalhaut radial profile)  
  > "shows the radial profile for a naturally weighted image" (The ring widths of Fomalhaut and HD 202628)
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
- final beam: Fomalhaut 1.6 x 1.2 arcsec; HD 202628 0.9 x 0.8 arcsec (spatial resolution)  
  > "have a spatial resolution of $1.6 \times 1.2$ arcsec resolution" (The ring widths of Fomalhaut and HD 202628); "The spatial resolution is $0.9 \times 0.8$ arcsec" (The ring widths of Fomalhaut and HD 202628)
- final rms: _not stated_

### Inherited from earlier work

- Fomalhaut seven-pointing dataset and its observational details  
  > "The same seven-pointing data of the Fomalhaut disc that were presented in MacGregor" (Fomalhaut); "The reader is referred to the papers cited below for more observational details." (The ring widths of Fomalhaut and HD 202628) [from MacGregor et al. (cite: 2017ApJ...842....8M)]
- HD 202628 12m-array dataset (taken from archive)  
  > "The 12m array data from Faramaz" (HD 202628) [from Faramaz et al. (cite: 2019AJ....158..162F)]
- Secular-perturbation ring model (slightly extended with a proper-eccentricity dispersion)  
  > "A slightly more complex version of the secular perturbation model used by MacGregor" (The model) [from MacGregor et al. (cite: 2017ApJ...842....8M)]
- Secular perturbation / pericenter-glow framework for eccentric rings  
  > "this section briefly describes the secular perturbation mechanism that is supposed to be the origin of eccentric debris rings" (Motivation and expectations) [from Wyatt et al. (cite: 1999ApJ...527..918W)]

### Not stated but needed to reproduce (our reading)

- Prior ranges (bounds) for each model parameter; paper says only 'uniform priors in linear space' within a 'broad parameter space'
- MultiNest settings beyond 75 live points (tolerance, sampling efficiency) and whether the emcee run is reproducible
- GALARIO settings (image size, pixel scale, oversampling, treatment of the seven-pointing primary beam)
- CASA statwt parameters (time bin, channel bin, data column, uv range) and exact CASA version for HD 202628
- Which execution blocks / spectral windows and observation dates were used (no project codes are printed)
- Flux-scale uncertainty and calibrator flux scale for either dataset
- Details of the HD 202628 point-source component (starting values, priors) and the central frequency/wavelength adopted
- Source code of the ring-model image generator (not released), random seeds, and how the 1/sqrt(r) brightness weighting is normalised
- Star position and flux handling for Fomalhaut (whether the stellar flux is fitted and its prior)
- Swath centring, binning and beam-deconvolution procedure for the Fomalhaut radial profile in Figure 5

## Analysis recipe

1. **Calibrate and reweight the visibilities**: Observatory-supplied calibration script; spectral averaging to one channel per spw, 30-s time averaging, CASA statwt reweighting (Fomalhaut); statwt reweighting of archived 12m data (HD 202628)  
  > "The data were calibrated using the observatory-supplied script, with the only additional steps being spectral averaging to a single channel per spectral window (spw)" (Fomalhaut); "The CASA" (HD 202628)
   - software: CASA
   - parameter: Fomalhaut: single channel per spw, 30-second time averaging, CASA 5.6 statwt  
  > "30-second time averaging, and re-weighting of all visibilities using the CASA 5.6" (Fomalhaut)
   - parameter: HD 202628: all visibilities exported and modelled assuming a single wavelength  
  > "all visibilities were exported and modelled assuming a single wavelength" (HD 202628)
   - assumption: Fomalhaut: chi2 computed with the average frequency of each spw for each of the seven pointings; 28 chi2 values summed; no per-pointing offset parameters  
  > "The $\chi^2$ are therefore computed using visibilities that assume the average frequency for each spectral window, for each of the seven pointings, and the 28 $\chi^2$ values summed." (Fomalhaut); "no per-pointing offset parameters were necessary" (Fomalhaut)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure the empirical radial width of the Fomalhaut ring**: Radial profile of a naturally weighted image through a 1 arcsec wide swath along the disc major axis; widths corrected for the beam  
  > "shows the radial profile for a naturally weighted image with a 1 arcsec wide swath through the star and along the disc major axis" (The ring widths of Fomalhaut and HD 202628)
   - parameter: Beam width about 1.2 arcsec subtracted to get true FWHM  
  > "accounting for the beam width of about 1.2 arcsec these widths are consistent with a true disc FWHM of about 13 au" (The ring widths of Fomalhaut and HD 202628)
   - fitting: _not stated_
   - validation: Compared with FWHM of 13-13.5 au from earlier ALMA studies  
  > "with these works finding full-width at half-maxima (FWHM) of 13-13.5 au" (The ring widths of Fomalhaut and HD 202628)
3. **Generate parametric secular-perturbation ring images**: Draw N particles sampling eccentricity, inclination, semi-major axis and true anomaly, rotate to the sky geometry, bin into a 2-d image with 1/sqrt(r) weighting  
  > "Bascially, $N$ particles are generated that sample distributions of eccentricity, inclination, semi-major axis, and true anomaly." (The model); "including a $1/\sqrt{r}$ weighting to account for decreasing temperature with radius" (The model)
   - parameter: N = 10^7 particles per model image  
  > "Model images computed using $N=10^7$ are compared with the ALMA visibilities using the" (The model)
   - parameter: 15 basic parameters (plus 3 for a point source in HD 202628)  
  > "A total of 15 basic parameters are included, and three more are included in the model for HD 202628 for the position and flux of a bright point source" (The model)
   - assumption: Particles have evolved by secular perturbations and are spread evenly around the forced pericenter in e-omega space  
  > "The fundamental assumption is that the particles have evolved to their current state due to secular perturbations (i.e. are spread evenly around the forced pericenter in $e\omega$-space)." (The model)
   - assumption: Dust observed with ALMA shares the orbits of the parent planetesimals  
  > "The assumption that the dust grains detected with ALMA share the same orbits as the planetesimals from which they are derived will be revisited below." (The ring widths of Fomalhaut and HD 202628)
   - fitting: _not stated_
   - validation: At least 10^6 particles found necessary to avoid shot noise affecting chi2  
  > "at least 10$^6$ particles were found to be necessary" (The ring widths of Fomalhaut and HD 202628)
4. **Fit model images to the visibilities**: GALARIO computes chi2 of model images against the visibilities; parameter space explored with MultiNest and emcee; weights from statwt rescaled by a free factor f_w  
  > "(which returns a $\chi^2$ value for a given model image)" (The model); "Absolute uncertainties are first estimated with the CASA" (The model)
   - software: GALARIO, MultiNest, emcee, CASA
   - parameter: MultiNest with 75 live points; only MultiNest results reported  
  > "Only the Multinest results are reported here, which used 75 live points to search a broad parameter space around previously found best-fit parameters." (The model)
   - parameter: Four model variants per target: Gaussian or Uniform semi-major axis distribution, each full or simple  
  > "Four slightly different models were fitted to the Fomalhaut data" (Fomalhaut)
   - assumption: Data are Gaussian about the model; each visibility has two independent degrees of freedom  
  > "The log likelihood function used in the fitting is therefore derived by assuming that the data are distributed as a Gaussian about the model with the correct normalisation." (footnote 2)
   - fitting: MultiNest (75 live points) with emcee as cross-check; Gaussian log likelihood with weight factor f_w; uniform priors in linear space  
  > "All parameters have uniform priors in linear space." (The model); "While both methods give similar results" (The model)
   - validation: Dirty residual maps show no large residuals except the Fomalhaut NW ansa  
  > "shows that the models are a good representation of the data, with the only large residual in the NW ansa" (Fomalhaut)
5. **Compare model variants**: Schwarz criterion (BIC) test of full versus simple models, plus inspection of residual maps  
  > "A test using the Schwarz criterion" (Fomalhaut); "the $\chi^2$ decreases by 240" (Fomalhaut)
   - parameter: k = 12 (simple) or 15 (full) parameters; n ~ 1.7e6 for Fomalhaut  
  > "k is 12 or 15 for the simple and full models, and $n \approx 1.7 \times 10^6$ for Fomalhaut" (footnote 3)
   - assumption: A BIC decrease of more than about 6 means extra parameters are warranted  
  > "with a decrease of more than about 6 indicating that additional parameters are warranted given the data" (footnote 3)
   - fitting: _not stated_
   - validation: For HD 202628 all four models fit similarly, so the extra parameters are not justified  
  > "including the additional parameters in the full models is not well justified given the data" (HD 202628)
6. **Compare fitted widths with the secular-perturbation expectation**: Compare observed/modelled ring width with expected 2ae_f; proper eccentricity lower than forced eccentricity implies narrower ring than expected  
  > "This width is to be compared to the expectation of $2ae_f = 33$ au." (The ring widths of Fomalhaut and HD 202628); "Fomalhaut and HD 202628 both lie above the dashed line, indicating that their width is narrower than expected given their forced eccentricities." (Eccentric ring origins - why so narrow?)
   - assumption: Initial planetesimal eccentricities are small (damped in the gas-rich phase) in the standard scenario  
  > "Naively, one expects that the initial planetesimal eccentricities are small, the result of damping during the gas-rich protoplanetary disc phase" (Motivation and expectations)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.6: statwt reweighting of visibilities (version stated for Fomalhaut)  
  > "30-second time averaging, and re-weighting of all visibilities using the CASA 5.6" (Fomalhaut)
- **GALARIO** : Compare model images with ALMA visibilities and return chi2  
  > "(which returns a $\chi^2$ value for a given model image)" (The model)
- **MultiNest** : Explore the parameter space (75 live points); only its results are reported  
  > "Only the Multinest results are reported here, which used 75 live points to search a broad parameter space around previously found best-fit parameters." (The model)
- **emcee** : MCMC exploration of parameter space, giving similar results to MultiNest  
  > "While both methods give similar results" (The model)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Fomalhaut disc position angle | 156.4 | +/- 0.1 | deg | 4 | All models find the same disc position angle of $\Omega = 156.4 \pm 0.1^\circ$ |
| Fomalhaut disc inclination | 66.6 | +/- 0.1 | deg | 4 | inclination $i = 66.6 \pm 0.1^\circ$ |
| Fomalhaut pericenter angle from SE ansa | 41 | +/- 1 | deg | 4 | All models find that the pericenter location is located $41 \pm 1^\circ$ anti-clockwise from the SE disc ansa |
| Fomalhaut forced eccentricity e_f (Gaussian full model) | 0.125 | +/- 0.001 | dimensionless | 4 | $0.125 \pm 0.001$ |
| Fomalhaut proper eccentricity e_p (Gaussian full model) | 0.019 | +/- 0.004 | dimensionless | 4 | $0.019 \pm 0.004$ |
| Fomalhaut proper-eccentricity dispersion sigma_e,p (Gaussian full model) | 0.090 | +/- 0.004 | dimensionless | 4 | $0.090 \pm 0.004$ |
| Fomalhaut proper eccentricity e_p (Uniform simple model) | 0.051 | +/- 0.001 | dimensionless | 4 | $0.051 \pm 0.001$ |
| Fomalhaut BIC test: change in chi2 for full vs simple uniform model | decreases by 240 (penalty term increases by 45) | not stated | dimensionless | 5 | increases by 45 for the full models relative to the simple uniform model; the $\chi^2$ decreases by 240 |
| Fomalhaut ring widths along major axis (observed, naturally weighted image) | 16 and 20 (NW ansa narrower) | not stated | au | 2 | The disc widths along the disc major axis are 16 and 20 au, with the NW ansa being narrower |
| Fomalhaut true disc FWHM after accounting for beam | about 13 | not stated | au | 2 | these widths are consistent with a true disc FWHM of about 13 au (i.e. much less than 33 au) |
| Fomalhaut expected ring width 2ae_f | 33 | not stated | au | 6 | This width is to be compared to the expectation of $2ae_f = 33$ au. |
| HD 202628 disc position angle | 130.7 | +/- 0.1 | deg | 4 | All models find the same disc position angle of $\Omega = 130.7 \pm 0.1^\circ$ and inclination $i = 57.4 \pm 0.1^\circ$. |
| HD 202628 disc inclination | 57.4 | +/- 0.1 | deg | 4 | All models find the same disc position angle of $\Omega = 130.7 \pm 0.1^\circ$ and inclination $i = 57.4 \pm 0.1^\circ$. |
| HD 202628 forced eccentricity e_f (Gaussian full model) | 0.12 | +/- 0.02 | dimensionless | 4 | $0.12 \pm 0.02$ |
| HD 202628 proper eccentricity e_p (all models) | <0.08 | upper limit | dimensionless | 4 | $<0.08$ |
| HD 202628 pericenter direction from SE ansa | 143 | not stated | deg | 4 | The latter appears consistent with the value of 143$^\circ$ from the SE ansa found here |
| HD 202628 expected ring width 2ae_f (for e_f of 0.09, from earlier work) | 28 | not stated | au | 6 | the expected width of $2ae_f = 28$ au is larger than observed |

## Qualitative findings

- Fomalhaut is well fitted by a narrow top-hat core (small e_p) plus a halo from proper-eccentricity dispersion; a range of semi-major axes is not needed  
  > "The semi-major axis distribution does not contribute to the structure, so the Gaussian full model looks the same." (Fomalhaut)
- Narrower discs are also the more eccentric ones in the small sample plotted (circumstantial)  
  > "The possible importance of Figure" (Eccentric ring origins - why so narrow?)
- PDS 70 is singled out as a possible progenitor of eccentric debris ring systems  
  > "is singled out as a possible progenitor of systems such as Fomalhaut and HD 202628" (Conclusions)

## Claim tuples

- H: Fomalhaut and HD 202628 ring widths match secular perturbation with initially near-zero eccentricities (width ~2ae_f) | E: Fit eccentric-ring models to ALMA 1.3 mm visibilities and measure Fomalhaut radial profile | R: Fomalhaut FWHM about 13 au versus expected 33 au; proper eccentricity well below forced eccentricity for both rings | F: Both rings are narrower than expected under the standard scenario | **supported**
- H: The Fomalhaut ring can be fitted by a secular model with proper eccentricity equal to forced eccentricity | E: Four model variants fitted with GALARIO + MultiNest | R: Fits require e_p about 0.02 versus e_f about 0.125 | F: Eccentric ring model works only if proper eccentricities are smaller than the forced eccentricity | **supported**
- H: HD 202628 ring also has proper eccentricity lower than forced | E: Same four models fitted to archival 12m data | R: e_f = 0.12 +/- 0.02 and e_p < 0.08; 2-d posteriors show sigma_a and e_p cannot both be zero | F: Proper eccentricity significantly lower than forced, but constraints are weaker (low s/n) | **partially**
- H: Narrowness arises from non-zero initial planetesimal eccentricities, possibly from the protoplanetary disc phase | E: Discussion of alternative origins (eccentric initial conditions, collisional damping, single event, shepherding planets, massive ring) | R: Qualitative arguments only; no direct test | F: Most likely implication is that planetesimals were not initially near-circular, implying narrow eccentric rings exist in protoplanetary discs | **partially**
- H: Collisional damping could make the mm ring look narrower than the planetesimal belt | E: Qualitative argument based on collision physics | R: Damping judged unlikely to be significant | F: Possibility disfavoured but testable | **partially**

## Reasoning

- Why this data: Best cases: obviously eccentric and narrow rings, and ALMA resolution sufficient to constrain width below 2ae_f  
  > "Here Fomalhaut and HD 202628 are singled out as the best cases, because their debris rings are obviously eccentric and narrow" (The ring widths of Fomalhaut and HD 202628); "because extant ALMA observations have sufficient spatial resolution to constrain the ring width to better than the expected $2ae_f$" (The ring widths of Fomalhaut and HD 202628)
- Why this method: Model is physically tied to initial conditions via the secular perturbation scenario and gives posteriors for relevant parameters  
  > "the advantage here is that the model is physically connected to the initial conditions via the assumed secular perturbation scenario" (Motivation and expectations); "has the benefit that ring parameters directly related to the secular perturbation scenario are derived explicitly" (The ring widths of Fomalhaut and HD 202628)
- Alternative: Gaussian simple model rejected as a poor fit to Fomalhaut  
  > "this is confirmed by a poor fit with the Gaussian simple model, so this model is not discussed further" (Fomalhaut)
- Alternative: Uniform semi-major axis model giving narrower ring near apocenter not borne out by the fits  
  > "this possibility is not borne out by the modelling, primarily because the best models do not require a range of semi-major axes" (Fomalhaut)
- Alternative: Shepherding planets judged more complicated than required by the data  
  > "the shepherding planet scenario is considered more complicated than is required by the data" (Shepherding panets)
- Alternative: Collisional damping seen as unlikely to be significant  
  > "collisional damping seems unlikely to be significant" (Eccentricity damping)
- How they decided it was enough: Extra parameters kept for Fomalhaut because BIC improved; not justified for HD 202628  
  > "Such a large decrease indicates that for Fomalhaut the inclusion of these extra parameters is justified by the improvement in the fit." (Fomalhaut)
- Limitation (authors): HD 202628 ring is at best marginally resolved radially with modest s/n  
  > "The ring is at best marginally resolved radially and not detected with a high signal to noise ratio" (The ring widths of Fomalhaut and HD 202628)
- Limitation (authors): Small parameter uncertainties partly reflect the restricted model; higher resolution needed for azimuthal width variation  
  > "this is at least in part because of the restricted nature of the models themselves" (Fomalhaut); "further insight into the azimuthal dependence of the ring width can only be gained with higher resolution imaging" (Fomalhaut)
- Limitation (authors): Few eccentric systems limit the width-eccentricity trend  
  > "a lack of eccentric systems limits the numbers in this Figure" (Conclusions)
- Caveat (inferred, ours): Fomalhaut error bars are very small and condition on an inflexible model; posterior widths are probably underestimated
- Caveat (inferred, ours): HD 202628 conclusion rests on upper limits for e_p and sigma_a and a single-wavelength approximation
- Caveat (inferred, ours): Chi2-based comparison of dirty residual maps is qualitative; no independent imaging-based validation of the width
- Caveat (inferred, ours): Model assumes mm dust traces planetesimal orbits, so grain-size effects are untested
- Caveat (inferred, ours): Unit and prior details for table parameters (a_0 in particular) are not given

## Reproducibility

- Data public (paper): HD 202628 12m data obtained from the ALMA archive; Fomalhaut data are the published MacGregor et al. set  
  > "were obtained from the ALMA archive" (HD 202628); "The same seven-pointing data of the Fomalhaut disc that were presented in MacGregor" (Fomalhaut)
- Products in archive: _not stated_
- Missing: ALMA project codes and execution blocks are not printed in the paper
- Missing: Model image generator code not released; must be reimplemented from the verbal recipe
- Missing: Prior bounds, MultiNest tolerance, GALARIO setup and statwt parameters not given
- Missing: Point-source model for HD 202628 not specified in detail
- Data volume (inferred): Fomalhaut seven-pointing 1.3 mm mosaic likely tens of GB raw per project; HD 202628 single pointing a few GB; calibrated, averaged visibilities well under 1 GB
- Score (inferred): 3/5, Data are public and the model and likelihood are described in enough detail to rebuild, but the code is not released, project codes and prior ranges are missing, and results are only given as table values.
- Rediscovery candidate: yes, Data are archival, the generative model, likelihood and sampler are described, and the main outputs (e_f, e_p, sigma_e,p, position angle, inclination, ring width) are numeric and checkable within stated uncertainty.

## Links

- Method: Tazzari et al. (cite: 2018MNRAS.476.4527T) (GALARIO visibility modelling library)
- Method: Feroz et al. (cite: 2009MNRAS.398.1601F) (MultiNest sampler)
- Method: Foreman-Mackey et al. (cite: 2013PASP..125..306F) (emcee sampler)
- Method: Schwarz (cite: 1978AnSta...6..461S) (Schwarz/BIC model comparison criterion)
- Companion: MacGregor et al. (cite: 2017ApJ...842....8M) (Source of Fomalhaut data and the baseline secular ring model)
- Companion: Faramaz et al. (cite: 2019AJ....158..162F) (Source of HD 202628 data and earlier ring model)
- Companion: White et al. (cite: 2017MNRAS.466.4201W) (Earlier ALMA Fomalhaut width measurement)
- Companion: Wyatt et al. (cite: 1999ApJ...527..918W) (Original secular perturbation pericenter-glow model)

## Checks

```json
{
 "quotes": 113,
 "quotes_ok": 113,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2015.1.00966.S",
  "2016.1.00515.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 17,
 "numeric_problems": 0,
 "fill": {
  "facts": 103,
  "stated": 66,
  "rate": 0.641
 },
 "evidence_ok": true
}
```
