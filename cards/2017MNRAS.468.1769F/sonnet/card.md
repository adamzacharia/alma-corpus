# The varying mass distribution of molecular clouds across M83

`2017MNRAS.468.1769F` | Monthly Notices of the Royal Astronomical Society 2017 | first author: Freeman, Pamela | arXiv: 1702.07728 | DOI: 10.1093/mnras/stx499

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: nearby_galaxies, star_formation, milky_way_ism
- Question: Does the molecular cloud mass distribution in M83 show a truncation mass that varies with galactocentric radius, like the young massive cluster population?  
  > "Here, we present a cloud-based analysis of ALMA CO($1\to 0$) observations of M83 to search for such a truncation mass in the molecular cloud population." (abstract)
- Target **M83**: coordinates _not stated_; z/distance 4.5 Mpc  
  > "corresponding to $29\times 18$ pc at the 4.5 Mpc distance of M83" (ALMA Data); "nearly face-on ($i = 24^{\circ}$), massive spiral galaxy (cite: Lundgren_2004b)" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00762.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12-m dishes only; no total power or short spacings  
  > "the QA2 data delivered as part of the project do not include total power or short spacing data" (ALMA Data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.34x0.83 arcsec (29x18 pc; geometric mean 22.8 pc)  
  > "images the CO($1\to 0$) line at $1.34\times 0.83$ arcsecond resolution, corresponding to $29\times 18$ pc at the 4.5 Mpc distance of M83" (ALMA Data)
- max recoverable scale: ~200 pc  
  > "The maximum recovered scale for these data should be $\sim 10\times$ the beam scale or 200 pc" (Systematic Effects)
- sensitivity: median brightness sensitivity 0.89 K per beam; velocity resolution 2.57 km/s  
  > "With a median brightness sensitivity of $\sigma=0.89$ K per beam" (ALMA Data)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archival, PI A. Hirota  
  > "observed as part of ALMA project 2012.1.00762.S (PI: A. Hirota)" (Introduction)
- Line: 12CO J=1-0 (not stated)
- Other facility **THINGS (VLA HI)**: HI 21-cm map for rotation curve and velocity dispersion  
  > "We include the Hi 21-cm map of the galaxy that is part of the THINGS (cite: Walter_2008) survey in our analysis." (Discussion)
- Other facility **SEST**: Low-resolution CO(1-0) and CO(2-1) maps (Lundgren 2004) giving total gas masses and rotation curve  
  > "mapped the galaxy in CO$(1\to0)$ and CO$(2\to1)$ emission using SEST achieving a resolution of $27''$ at best." (Discussion)
- Other facility **HST**: Cluster mass distributions from Adamo et al. 2015  
  > "Archival Hubble Space Telescope data have already been analyzed" (Introduction)
- External data: Cluster truncation masses, indices and maximum cluster masses per radial bin  
  > "The normalization to equal area bins adopts the binning used in (cite: Adamo_2015) to facilitate direct comparison with that work." (Mass distributions) [from (cite: Adamo_2015)]
- External data: Disk rotation curve (M_d=6.4e10 Msun, R_d=2.9 kpc)  
  > "the disk mass $M_d=6.4\times 10^{10}~M_{\odot}$, the scale length $R_d=2.9$ kpc" (Discussion) [from (cite: Lundgren_2004b)]
- External data: CO-to-H2 conversion factor X_CO = 2.0e20  
  > "we adopt a CO-to-H$_2$ conversion factor of $X_{\mathrm{CO}} = 2.0\times 10^{20}$ (K km s$^{-1}$)$^{-1}$ cm$^{-2}$ (cite: Bolatto_2013)" (ALMA Data) [from (cite: Bolatto_2013)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: QA2 delivered data downloaded from JVO  
  > "We used the Quality Assurance, step 2 data (QA2) downloaded from the Japanese Virtual Observatory site" (ALMA Data)
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
- final beam: 1.34x0.83 arcsec  
  > "images the CO($1\to 0$) line at $1.34\times 0.83$ arcsecond resolution" (ALMA Data)
- final rms: 0.89 K per beam median  
  > "With a median brightness sensitivity of $\sigma=0.89$ K per beam" (ALMA Data)

### Inherited from earlier work

- cprops cloud decomposition recommended algorithm for interferometer data  
  > "We utilize their recommended algorithm for identifying GMCs in interferometer data described as follows." (GMC properties) [from (cite: Rosolowsky_2006)]
- Gaussian correction factor for moments  
  > "we correct each measured property by a Gaussian correction factor following (cite: Rosolowsky_2005)." (GMC properties) [from (cite: Rosolowsky_2005)]
- Maximum-likelihood fitting formalism for mass distributions  
  > "we build off the formalism developed by (cite: Clauset_2009), which uses a maximum likelihood framework" (Mass distributions) [from (cite: Clauset_2009)]

### Not stated but needed to reproduce (our reading)

- Exact imaging parameters of the JVO QA2 cube (weighting, cell size, deconvolver)
- CASA version used for the delivered data
- Fake-cloud size and line-width parameters used in the injection test
- Exact radial bin geometry, inclination and position angle used for deprojection
- Method for surface-density and velocity-dispersion profiles in the Toomre/Jeans calculation (radial binning details)
- Recipe for the mass-weighted sum of HI and CO dispersions

## Analysis recipe

1. **Identify clouds in CO cube**: cprops masking (>2.5 sigma in two adjacent channels, extended to 1 sigma) and seeded watershed decomposition  
  > "Emission is then identified as those pixels in the (three-dimensional) data cube that are larger than $2.5\sigma(\alpha,\delta)$ in two adjacent velocity channels." (GMC properties)
   - software: cprops (cpropstoo)
   - parameter: maxima separated by at least 40 pc or 5.14 km/s; 2.5 sigma above saddle  
  > "separated by at least 40 pc spatially or 5.14 km s$^{-1}$ in velocity" (GMC properties)
   - fitting: _not stated_
   - validation: Mask applied to data scaled by -1 gave no false positives  
  > "We find no false positives are included so the masking criteria are likely robust." (GMC properties)
2. **Completeness by fake source injection**: Inject 350 Gaussian clouds at 51 masses (1e5-1e6 Msun), 10 random offsets; fit logistic recovery function  
  > "This process is repeated for 51 different mass values distributed logarithmically between $10^5~M_{\odot}$ and $10^6~M_{\odot}$." (GMC properties)
   - parameter: 50% completeness 3.35e5 Msun  
  > "establishing a 50% completeness limit of $M_{\mathrm{GMC}} > 3.35\times 10^5~M_{\odot}$" (GMC properties)
   - assumption: Fake clouds follow Local Group size-linewidth-luminosity relations  
  > "luminosities, sizes, and line widths set by the characteristic relationships established in the Local Group population" (GMC properties)
   - fitting: logistic function  
  > "We model the recovery fraction \[$f(M)$\] as a logistic function and fit the parameters of the function to obtain an analytic expression for the survey completeness" (Analysis - GMC properties)
   - validation: Gaussian correction selected because it recovers properties of injected clouds  
  > "We select this correction method over others based on it recovering the properties of clouds in our fake source injection test." (GMC properties)
3. **Measure cloud properties**: Moments with Gaussian correction, beam deconvolution; luminous mass from alpha_CO, virial mass 5 sigma^2 R/G, surface density; bootstrap uncertainties  
  > "The virial mass of the cloud is calculated from the radius and line width of the molecular cloud: $M_{\mathrm{vir}} = 5 \sigma^2 R/G$." (GMC properties)
   - software: cprops
   - assumption: alpha_CO = 4.35 Msun pc^-2 (K km/s)^-1  
  > "$\alpha_{\mathrm{CO}}=4.35~M_{\odot}\mbox{ pc}^{-2}~\mathrm{(K~km~s^{-1})^{-1}}$" (GMC properties)
   - fitting: _not stated_
   - validation: Compared with Solomon et al. 1987 scaling relations  
  > "We compare the properties of the molecular clouds to those seen in the Milky Way study of (cite: Solomon_1987)" (GMC properties)
4. **Fit cloud mass distributions in radial bins**: Fit pure power law, Schechter (beta=-2), truncated power law to completeness-corrected CCDF by minimizing Anderson-Darling statistic, with MCMC for uncertainties  
  > "we first optimize the parmeters of the distribution that minimize $A$ and then use the emcee sampler" (Mass distributions)
   - software: emcee
   - parameter: 10 chains, 200 burn-in, 2000 steps, thin by 10  
  > "We use ten sampler chains initialized around the optimal fit, 200 steps of burn in and then 2000 steps of sampling, thinning to every 10th step" (Mass distributions)
   - assumption: log-likelihood approx -A/(2n) for N>30  
  > "the log-likelihood of a random draw from a known PDF generating a statistic of value $A$ is approximately $-A/(2n)$" (Mass distributions)
   - fitting: emcee; flat priors beta in [-20,20], log10(Mc/Mmin) in [0,3]  
  > "We assume ignorant priors: $\beta\in [-20,20]$ and $\log_{10} (M_{c}/M_{\mathrm{min}}) \in [0, 3]$." (Mass distributions)
   - validation: Monte Carlo simulations for A distribution with N=30 to 1000  
  > "We draw a number of random data from our three different distribution functions with known parameters ($N=30$ to $10^3$" (Mass distributions)
5. **Compute Jeans and Toomre masses**: Radial profiles of Sigma, sigma_v from ALMA/SEST CO and THINGS HI; kappa from exponential disk rotation curve; M_J and M_T formulae  
  > "We infer $\Sigma$, $\sigma_v$ and $\varkappa$ from the ALMA data and supplementary information." (Mass Scales in M83)
   - assumption: Exponential disk rotation curve of Lundgren 2004b  
  > "They find the rotation curve is well modeled by an exponential disk." (Mass Scales in M83)
   - fitting: _not stated_
   - validation: THINGS rotation curve gives comparable results  
  > "the results are otherwise comparable" (Mass Scales in M83)

## Software

- **cprops (cpropstoo)** : cloud identification and property measurement  
  > "We use the cpropstoo implementation at <http://github.com/akleroy/cpropstoo>" (GMC properties)
- **emcee** : MCMC sampling of mass distribution parameters  
  > "use the emcee sampler (cite: emcee)" (Mass distributions)
- **Astropy** : general analysis  
  > "This work made use of the Astropy package for Python (cite: Astropy)" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of clouds identified | 873 | not stated | clouds | 1 | This approach extracts 873 clouds. |
| 50% completeness limit | 3.35e5 | not stated | Msun | 2 | 50% completeness limit of $M_{\mathrm{GMC}} > 3.35\times 10^5~M_{\odot}$ |
| Clouds above completeness limit | 711 | not stated | clouds | 2 | Of the 873 clouds identified, 711 are above the 50% completeness limit. |
| Median surface density, Rg>0.5 kpc | 170 | not stated | Msun pc^-2 | 3 | median surface density of $\langle \Sigma \rangle = 170~M_{\odot}\mbox{ pc}^{-2}$ |
| Median surface density, Rg<0.5 kpc | 700 | not stated | Msun pc^-2 | 3 | clouds inside this radius have a median surface density of $\langle \Sigma \rangle = 700~M_{\odot}\mbox{ pc}^{-2}$ |
| Truncated power-law Mc, 0.45-2.3 kpc | 2.1 (+1.4/-0.4) e6 | +1.4/-0.4 | Msun | 4 | $M_{c,\mathrm{TPL}}$ ($10^6 M_{\odot}$) / $7.0^{+10.5}_{- 1.8}$  / $2.1^{+ 1.4}_{- 0.4}$ |
| Maximum cloud mass, 0-0.45 kpc bin | 24.7e6 | not stated | Msun | 4 | $M_{\mathrm{max,GMC}}$ ($10^6 M_{\odot}$)        / 24.7 |
| Max cluster mass / max cloud mass | 1-2% | not stated | percent | 4 | The maximum cluster mass is about 1-2% of the maximum cloud mass. |

## Qualitative findings

- Clouds in M83 follow Milky Way-like scaling relations except enhanced surface density and turbulence in the centre  
  > "there are systematic variations in cloud properties over the face of the galaxy." (Conclusions)
- Toomre and Jeans masses exceed maximum cloud mass; interferometer-only Toomre mass comparable to maximum cloud mass  
  > "Both the Jeans mass and the Toomre mass are larger than the maximum cloud mass across the disk." (Mass Scales in M83)

## Claim tuples

- H: Molecular cloud masses have a truncation that decreases with radius like the cluster masses | E: cprops cloud catalogue, radial-bin mass function fits | R: Truncated power law preferred in inner three bins; Mc and Mmax decrease with radius | F: Maximum cloud mass scale decreases with galactocentric radius | **supported**
- H: Maximum cluster mass tracks maximum cloud mass | E: Compare Mmax,cluster from Adamo et al. with Mmax,GMC per bin | R: Ratio 1-2% | F: Consistent with eps~10% and Gamma~10% | **supported**
- H: Cloud internal conditions explain varying cluster formation efficiency | E: Radial trends in pressure, density, free-fall time | R: Constant for Rg>0.5 kpc | F: Cluster formation efficiency set by large-scale ISM, not cloud internals | **supported**
- H: The cloud mass distribution is a Schechter function like clusters | E: Fit Schechter, power law, truncated power law | R: Schechter excluded in inner bins; outer bins not distinguishable | F: No good evidence for Schechter form | **refuted**

## Reasoning

- Why this data: High-quality archival CO(1-0) of nearby face-on galaxy to compare with HST cluster work  
  > "M83 is an obvious target for exploring molecular cloud properties." (Introduction)
- Why this method: _not stated_
- Alternative: Extrapolation method for mass correction rejected because it biases masses low by 25%  
  > "The extrapolation method discussed in (cite: Rosolowsky_2006) leads to mass values that are biased low by 25%." (GMC properties)
- How they decided it was enough: _not stated_
- Limitation (authors): No short-spacing data; diffuse emission filtered; negative sidelobes  
  > "The data are also likely missing flux from large-scale, diffuse CO emission (cite: Pety_2013)." (ALMA Data)
- Limitation (authors): Cloud blending in central region makes nuclear mass distribution suspect  
  > "We should therefore regard the clouds in the $R_g<0.45$ kpc bin as particularly suspect" (Systematic Effects)
- Caveat (inferred, ours): Single fixed alpha_CO across a galaxy with a nuclear environment
- Caveat (inferred, ours): cprops parameter choices affect decomposition
- Caveat (inferred, ours): Few clouds in outer bins limit model discrimination
- Caveat (inferred, ours): Toomre mass depends on interferometer-filtered surface densities

## Reproducibility

- Data public (paper): Archival data downloaded from JVO  
  > "The data were retrieved from the JVO portal (<http://jvo.nao.ac.jp/portal>) operated by the NAOJ." (Acknowledgements)
- Products in archive: _not stated_
- Code: cpropstoo is public; the custom mass-fitting code is not mentioned  
  > "We use the cpropstoo implementation at <http://github.com/akleroy/cpropstoo>" (GMC properties)
- Missing: Imaging parameters of the QA2 cube
- Missing: Fake-cloud injection details
- Missing: Fitting code for Anderson-Darling MCMC
- Missing: Radial bin geometry details
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Public data and clear cprops and fitting recipe, but several injection, binning and profile details are missing.
- Rediscovery candidate: yes, The data are public, the cprops recipe is specified and the main results are numeric (cloud counts, completeness, fitted masses).

## Links

- Method: (cite: Rosolowsky_2006) (cprops algorithm)
- Method: (cite: Clauset_2009) (power-law fitting formalism)
- Companion: (cite: Adamo_2015) (cluster mass distributions in M83)
- Related: THINGS
- Related: SEST CO survey of M83

## Checks

```json
{
 "quotes": 65,
 "quotes_ok": 65,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 83,
  "stated": 49,
  "rate": 0.59
 },
 "evidence_ok": true
}
```
