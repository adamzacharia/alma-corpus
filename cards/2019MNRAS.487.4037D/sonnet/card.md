# A joint ALMA-Bolocam-Planck SZ study of the pressure distribution in RX J1347.5-1145

`2019MNRAS.487.4037D` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Di Mascolo, Luca | arXiv: 1812.01034 | DOI: 10.1093/mnras/stz1550

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: galaxy_clusters_and_sz
- Question: Can joint forward-modelling of ALMA/ACA visibilities with Bolocam and Planck images constrain the pressure distribution of RX J1347.5-1145, and does the south-eastern SZ excess indicate a strong overpressure or reflect model geometry?  
  > "we have shown that the SZ signal can be well-described by a single smooth ellipsoidal generalized Navarro–Frenk–White profile, where the best-fitting centroid is located between the two brightest cluster galaxies." (abstract)
- Target **RX J1347.5-1145**: coordinates X-ray peak 13h47m30.593s, -11d45m10.050s  
  > "the galaxy cluster RX J1347.5–1145 ($z=0.451$)" (1 Introduction); "1 arcsec corresponds to a physical scale of 5.94 $\mathrm{kpc}$ at the redshift of RX J1347.5–1145." (1 Introduction); z/distance z=0.451  
  > "the galaxy cluster RX J1347.5–1145 ($z=0.451$)" (1 Introduction); "1 arcsec corresponds to a physical scale of 5.94 $\mathrm{kpc}$ at the redshift of RX J1347.5–1145." (1 Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00246.S
- bands: Band 3; four 2 GHz spectral windows centred at 85, 87, 97, 99 GHz  
  > "The spectral windows were centred at $85$, $87$, $97$, and $99~\mathrm{GHz}$, that is in ALMA Band 3" (3.1 Atacama Large Millimeter Array)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: ALMA 12m array and 7m ACA, Cycle 2, seven mosaic pointings  
  > "RX J1347.5–1145 was observed by both the main ALMA $12\mathrm{m}$ array and $7\mathrm{m}$ Atacama Compact Array" (3.1 Atacama Large Millimeter Array)
- configurations: _not stated_
- baselines: uv range 2.1 to 115.9 klambda  
  > "visibilities covering the $uv$-plane between $2.1$ and $115.9~\mathrm{k}\lambda$" (3.1 Atacama Large Millimeter Array)
- angular resolution: ALMA (4.1, 2.4) arcsec; ACA (20.5, 11.1) arcsec  
  > "$( 4.1, 2.4)~\mathrm{arcsec}$" (Table 1)
- max recoverable scale: ALMA 58.8 arcsec; ACA 99.7 arcsec  
  > "$58.8~\mathrm{arcsec}$" (Table 1)
- sensitivity: ALMA 12 uJy/beam; ACA 83 uJy/beam average RMS  
  > "$12~\mathrm{\mu Jy~beam^{-1}}$" (Table 1)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **Bolocam**: 140 GHz SZ map, 58 arcsec resolution, plus 1000 sky realizations for noise covariance  
  > "the data products comprise a set of 1000 realizations of the $140~\mathrm{GHz}$ astronomical sky" (3.2 Bolocam)
- Other facility **Planck**: HFI 2015 maps used to make a MILCA-like Compton y map at 10 arcmin  
  > "We applied a component separation method analogous to the modified Internal Linear Combination algorithm (MILCA)" (3.3 Planck)
- Other facility **Chandra**: archival X-ray data (OBSIDs 3592, 13516, 13999, 14407) for pressure profile and X-ray arithmetic  
  > "We employ archival Chandra observations (OBSIDs: 3592,13516,13999,14407)." (5.1.2)
- External data: Cool-core gNFW slopes alpha=1.2223, beta=5.4905, gamma=0.7736  
  > "$\alpha=1.2223$, $\beta=5.4905$, and $\gamma=0.7736$" (5.1.1) [from Arnaud2010]
- External data: Suzaku hot component T=25.3 (+6.1/-4.5) keV in SE region  
  > "$T=25.3\substack{+6.1\\-4.5}~\mathrm{keV}$ (cite: Ota2008)" (5.2.2) [from Ota2008]
- External data: Zitrin lensing contours/kappa map  
  > "which includes the lensing contours from (cite: Zitrin2015)" (2 RX J1347.5–1145) [from Zitrin2015]
- Simulation/model as data: Mock observations with correlated or independent CMB realizations used to test the joint likelihood assumptions  
  > "We tested the validity of the above assumptions by running our model reconstruction technique on a sample of mock observations" (4.1)

## Processing

### Calibration

- pipeline or manual: manual calibration  
  > "We performed manual calibration of the ACA and ALMA measurement sets" (3.1)
- casa version: CASA 4.7.2 for calibration; 5.3.0 for images  
  > "version 4.7.2 of the Common Astronomy Software Applications" (3.1)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 6% for ALMA and ACA  
  > "uncertainty on the overall flux calibration of $6\%$ for both the ALMA and ACA data" (3.1)
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
- primary beam correction: primary beam models from CLEAN per pointing used in the fit  
  > "The primary beam model images obtained by running the CLEAN task independently for each pointing are used" (3.1)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Detailed ACA+ALMA observation description  
  > "We refer to (cite: Kitayama2016) for a more detailed description of the combined ACA+ALMA observation of RX J1347.5–1145." (Atacama Large Millimeter Array) [from Kitayama2016]
- Visibility binning scheme  
  > "over a set of optimal bins defined as in (cite: Hobson1995)" (3.1) [from Hobson1995]
- Bolocam reduction  
  > "An overview of the reduction process and data products is provided in (cite: Sayers2013)." (3.2) [from Sayers2013]
- X-ray deprojected profile procedure  
  > "using the procedure described in (cite: Churazov2003)" (5.1.2) [from Churazov2003]

### Not stated but needed to reproduce (our reading)

- Exact binning parameters and number of averaged visibilities
- Planck MILCA implementation details and Y_cyl Gaussian prior
- MCMC walkers, steps, burn-in and convergence
- Fitting code is not public/versioned
- Chandra reduction details and X-ray arithmetic smooth models
- Source of 12.5 keV vs 7 keV temperature choices beyond brief description

## Analysis recipe

1. **Prepare ALMA/ACA visibilities**: Manual calibration, spectral-window averaging and uv binning of visibilities per field  
  > "we consider spectral window-averaged visibilities for each of the fields" (3.1)
   - software: CASA
   - assumption: Diagonal noise covariance; CMB and confusion negligible  
  > "we then assume the ACA+ALMA block of the noise covariance matrix to be diagonal" (3.1)
   - fitting: _not stated_
   - validation: _not stated_
2. **Joint Bayesian fit of spherical cool-core gNFW plus point source**: Joint likelihood product of ACA+ALMA visibilities, Bolocam and Planck images; gNFW centred on X-ray peak with fixed Arnaud slopes, Te=7 keV, point source power law  
  > "we fit a spherically symmetric gNW pressure profile whose centroid is set at the position of the peak in the observed X-ray brightness distribution" (5.1.1)
   - software: emcee, GALARIO, FFTW, astropy
   - parameter: Free: Pei, rs (uniform priors), point-source position, flux, spectral index; kappa Gaussian, eta exponential hyperparameters  
  > "$\mathcal{E}[1.00]$ is instead the exponential distribution with unitary expectation value" (Table 1)
   - assumption: Te fixed at 7 keV  
  > "we fix the electron temperature to $T_{\mathrm{e}}=7~\mathrm{keV}$" (5.1.1)
   - fitting: Affine-invariant ensemble MCMC (emcee), medians and 68% intervals  
  > "we make use of the specific implementation of the affine-invariant ensemble sampling technique" (4.3)
   - validation: Data-free prior-only run and mock tests  
  > "This has been performed by sampling the posterior distribution obtained in the case of a constant likelihood" (5.1.1)
3. **Compare SZ pressure profile to Chandra X-ray pressure**: X-ray pressure from deprojected density times temperature compared with SZ model  
  > "by multiplying the radial profiles of deprojected electron density and temperature distributions" (5.1.2)
   - software: CIAO
   - fitting: _not stated_
   - validation: Good overall agreement within uncertainties  
  > "shows good overall agreement with the X-ray profile within the uncertainties of the two independent determinations" (5.1.2)
4. **Fit free-centroid ellipsoidal gNFW**: Free centroid, eccentricity, angle, inner slope gamma, Te=12.5 keV, Gaussian prior on Planck Ycyl  
  > "we now assume an electron temperature of $12.5~\mathrm{keV}$" (5.1.3)
   - software: emcee, GALARIO
   - assumption: Line-of-sight axis equals inverse rms average of sky-plane semi-axes  
  > "the extent of the latter is hard-coded with the assumption that it is equal to the inverse root mean square average of the plane-of-sky semi-axes" (8 Triaxial ellipsoidal profile)
   - fitting: emcee MCMC with uniform priors  
  > "we make use of the specific implementation of the affine-invariant ensemble sampling technique (cite: Goodman2010) provided by the EMCEE PYTHON package (cite: Foreman2013)" (Implementation details)
   - validation: Prior-only sampling shows no bias; residual map shows no significant structure  
  > "the prior-only sampling shows no biases in the reconstruction of the model parameters" (5.1.3)
5. **Classify X-ray perturbations and estimate SZ excess**: X-ray arithmetic in two Chandra bands; crude sphere estimate of dy/y  
  > "The ‘X-ray arithmetic’ method reported in (cite: Churazov2016)" (5.2.1)
   - assumption: Overpressurized sphere radius ~90 kpc, offset ~130 kpc; adiabatic index 5/3  
  > "sphere of overpressurized gas with radius $\sim 90~\mathrm{kpc}$" (5.2.1)
   - fitting: _not stated_
   - validation: Order-of-magnitude only  
  > "These are of course only an order-of-magnitude estimates, given the complexity of the cluster and the assumptions made." (X-ray imaging constraints on the nature of the ICM perturbations)

## Software

- **CASA** 4.7.2 (calibration), 5.3.0 (imaging): Calibration and dirty images  
  > "All the interferometric images presented in this work, which are not used for analysis, were generated with CASA version 5.3.0." (3.1)
- **emcee** : MCMC sampling  
  > "provided by the EMCEE PYTHON package" (4.3)
- **GALARIO** : Synthetic visibilities (modified)  
  > "We modified the core GALARIO library" (4.3)
- **FFTW/pyFFTW** : Fourier transforms  
  > "The Fourier transforms are computed using the FFTW library" (4.3)
- **Astropy** : Astronomical tasks  
  > "exploiting the community-developed package ASTROPY" (4.3)
- **CIAO** : Chandra analysis  
  > "application packages CIAO, CHIPS, and SHERPA" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Planck Y_cyl(15 arcmin) | 3.24e-3 | 0.54e-3 | arcmin^2 | 0 | Y_{\mathrm{cyl}}(15~\mathrm{arcmin}) = (3.24\pm0.54)\times10^{-3}~\mathrm{arcmin}^2 |
| Spherical gNFW r_s | 3.10 | 16th 2.97, 84th 3.24 | arcmin | 2 | $r_{\mathrm{s}}$ / arcmin / $3.10$ / $2.97$ / $3.24$ |
| Spherical gNFW P_ei | 5.39e-2 | 16th 5.16, 84th 5.65 (1e-2) | keV cm^-3 | 2 | $5.39$ / $5.16$ / $5.65$ |
| Point-source flux at 90 GHz | 4.208 | 16th 4.199, 84th 4.217 | mJy | 2 | $4.208$ / $4.199$ / $4.217$ |
| Point-source spectral index | -0.431 | 16th -0.462, 84th -0.399 | dimensionless | 2 | $-0.431$ / $-0.462$ / $-0.399$ |
| Planck/ALMA+ACA scaling ratio | 0.993 | 0.038 | dimensionless | 2 | with ratio equal to $0.993\pm 0.038$ |
| Observed SE excess dy/y | 0.24 | not stated | dimensionless | 5 | $\delta \vary/\vary\sim 0.24$ |

## Qualitative findings

- Spherical X-ray-centred model leaves a SE residual; a free-centroid ellipsoidal model removes significant residuals.  
  > "the residual amplitude of the SZ effect to the south-east is dramatically reduced when shifting the centroid away from the X-ray peak" (5.1.3)

## Claim tuples

- H: Is the SE SZ excess a strong shock-induced overpressure? | E: Fit spherical gNFW at X-ray peak vs free ellipsoidal model | R: Spherical model leaves a SE residual; ellipsoidal model leaves none significant | F: Excess partly geometric; pressure may be more regular | **supported**
- H: SZ and X-ray pressure profiles agree | E: Compare SZ gNFW with Chandra-derived pressure | R: Good agreement out to ~1 Mpc | F: Partial validation of method | **supported**
- H: SE structure is isobaric vs adiabatic | E: X-ray arithmetic and dy/y estimate | R: dy/y~0.24 observed vs ~0.8 (fully adiabatic) and ~0.3 | F: Predominantly isobaric | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Visibility-space fitting avoids deconvolution artefacts and noise correlation  
  > "a straightforward solution may be to fit the visibility data directly in Fourier space through a forward-modelling procedure" (1 Introduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Models differ in components so statistical comparison is misleading; overfitting may hide overpressure; X-ray arithmetic limited to linear perturbations  
  > "a direct comparison based on statistical considerations would provide misleading results" (5.2)
- Caveat (inferred, ours): Fixed temperatures strongly affect y and relativistic corrections
- Caveat (inferred, ours): Results depend on centroid choice and ellipsoid geometry assumptions
- Caveat (inferred, ours): No model comparison metric
- Caveat (inferred, ours): Radio source variability not resolved

## Reproducibility

- Data public (paper): Bolocam and Planck public; ALMA project cited; Chandra archival  
  > "We complement the ACA+ALMA data with the publicly available Bolocam observation" (3.2 Bolocam)
- Products in archive: _not stated_
- Missing: Fitting code not released
- Missing: MCMC settings
- Missing: Visibility binning details
- Data volume (inferred): ~tens of GB raw ALMA+ACA; small for Bolocam/Planck
- Score (inferred): 5/5, Public data and a detailed model with priors, but custom unreleased code and missing sampler/binning details.
- Rediscovery candidate: no, Requires bespoke unreleased joint-fitting code and unstated settings.

## Links

- Method: Tazzari2018 (galario visibility modelling library)
- Method: Churazov2016 (X-ray arithmetic method)
- Companion: Kitayama2016 (Earlier analysis of same ACA+ALMA data)

## Checks

```json
{
 "quotes": 64,
 "quotes_ok": 64,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 50,
  "rate": 0.61
 },
 "evidence_ok": true
}
```
