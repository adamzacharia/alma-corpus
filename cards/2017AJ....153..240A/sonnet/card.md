# An ALMA Survey of Protoplanetary Disks in the σ Orionis Cluster

`2017AJ....153..240A` | The Astronomical Journal 2017 | first author: Ansdell, M. | arXiv: 1703.08546 | DOI: 10.3847/1538-3881/aa69c0

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: How much dust and gas do protoplanetary disks in the 3-5 Myr sigma Orionis cluster retain, how do they compare to other regions, and does external photoevaporation affect them?  
  > "The $\sigma$ Orionis cluster is important for studying protoplanetary disk evolution, as its intermediate age ($\sim$$3$–5 Myr) is comparable to the median disk lifetime." (abstract)
- Target **sigma Orionis cluster (92 disk-bearing members)**: coordinates sigma Ori at 05:38:44.779, -02:36:00.11  
  > "We adopt a cluster distance of 385 pc based on recent orbital parallax measurements of the $\sigma$ Ori triple system (cite: 2016AJ....152..213S)." (2 SAMPLE); z/distance 385 pc  
  > "We adopt a cluster distance of 385 pc based on recent orbital parallax measurements of the $\sigma$ Ori triple system (cite: 2016AJ....152..213S)." (2 SAMPLE); distance from orbital parallax of sigma Ori triple system (Schaefer et al. 2016)  
  > "We adopt a cluster distance of 385 pc based on recent orbital parallax measurements of the $\sigma$ Ori triple system (cite: 2016AJ....152..213S)." (2 SAMPLE)

## Data provenance

- ALMA projects: 2015.1.00089.S
- bands: Band 6 (1.33 mm)  
  > "Our Band 6 ALMA observations were obtained on 2016 July 30 and 31 during Cycle 3" (3 ALMA OBSERVATIONS)
- frequencies and spectral setup: Continuum windows at 234.293 and 216.484 GHz; 12CO, 13CO, C18O windows centred at 230.531, 220.392, 219.554 GHz, 0.122 MHz channels  
  > "These spectral windows were centered on 230.531, 220.392, and 219.554 GHz with bandwidths of 11.719 MHz and channel widths of 0.122 MHz." (3 ALMA OBSERVATIONS)
- continuum bandwidth: 2.000 and 1.875 GHz  
  > "two broadband continuum windows centered on 234.293 and 216.484 GHz with bandwidths of 2.000 and 1.875 GHz" (3 ALMA OBSERVATIONS)
- arrays: 12 m, 36 and 37 antennas  
  > "The array configuration used 36 and 37 12 m antennas on July 30 and 31, respectively" (3 ALMA OBSERVATIONS)
- configurations: _not stated_
- baselines: 15–1124 m  
  > "with baselines of 15–1124 m on both runs" (3 ALMA OBSERVATIONS)
- angular resolution: 0.31"x0.25" average beam (~120x95 AU)  
  > "for an average beam size of 0.31$''$$\times$0.25$''$ ($\sim$120$\times$95 AU at 385 pc)" (3 ALMA OBSERVATIONS)
- max recoverable scale: _not stated_
- sensitivity: average continuum rms 0.15 mJy/beam; line rms 13, 14, 11 mJy/beam per 1 km/s channel (12CO, 13CO, C18O)  
  > "On-source integration times were 1.2 min per object for an average continuum rms of 0.15 mJy beam$^{-1}$" (3 ALMA OBSERVATIONS)
- time on source: 1.2 min per object  
  > "On-source integration times were 1.2 min per object" (3 ALMA OBSERVATIONS)
- observing dates: 2016 July 30 and 31  
  > "obtained on 2016 July 30 and 31 during Cycle 3" (3 ALMA OBSERVATIONS)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (230.538 GHz)
- Line: 13CO J=2-1 (220.399 GHz)
- Line: C18O J=2-1 (219.560 GHz)
- Other facility **Spitzer**: IR-excess disk sample selection  
  > "cross-matching the Class II and transition disk (TD) candidates from the *Spitzer* survey of (cite: 2007ApJ...662.1067H) with the aforementioned Mayrit catalog" (2 SAMPLE)
- Other facility **VLT/X-Shooter**: spectral types for some sources  
  > "supplemented with those from medium-resolution VLT/X-Shooter spectra when available from (cite: 2012A&A...548A..56R)" (2 SAMPLE)
- External data: Spectral types for most sources  
  > "Spectral types were primarily taken from the homogenous sample of low-resolution optical spectra analyzed in (cite: 2014ApJ...794...36H)" (2 SAMPLE) [from (cite: 2014ApJ...794...36H)]
- External data: WB14 parametrized gas disk model grid for gas masses  
  > "we can still place rough constraints on $M_{\rm gas}$ by comparing our measured $^{12}$CO and $^{13}$CO line luminosities or upper limits to the WB14 model grid." (5.2 Gas Masses) [from (cite: 2014ApJ...788...59W)]
- External data: DALI model grid for gas masses  
  > "Alternatively, one can estimate $M_{\rm gas}$ by employing the grid of physical-chemical models presented in (cite: 2016A&A...594A..85M) (hereafter M16). Using the code DALI" (Gas Masses) [from (cite: 2016A&A...594A..85M)]
- External data: Literature (sub-)mm fluxes of other regions for comparison  
  > "we calculate $M_{\rm dust}$ uniformly across each region by inputting the (sub-)mm continuum fluxes (or $3\sigma$ upper limits) from the literature into Equation" (6.2 Mdust-Mstar Relation) [from Ansdell et al. 2016; Pascucci et al. 2016; Barenfeld et al. 2016]
- External data: Accretion rates from U-band photometry  
  > "we combine our ALMA observations with the $U$–band survey of (cite: 2011A&A...525A..47R)" (6.5 Relation between Mdisk and Macc) [from (cite: 2011A&A...525A..47R)]

## Processing

### Calibration

- pipeline or manual: Pipeline calibrated by NRAO staff  
  > "The raw data were pipeline calibrated by NRAO staff using the `CASA` package (version 4.5.3)." (3 ALMA OBSERVATIONS)
- casa version: CASA 4.5.3  
  > "The raw data were pipeline calibrated by NRAO staff using the `CASA` package (version 4.5.3)." (3 ALMA OBSERVATIONS)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0522-3627 or J0423-0120  
  > "absolute flux calibration with observations of J0522-3627 or J0423-0120" (3 ALMA OBSERVATIONS)
- flux scale uncertainty: ~10%  
  > "We estimate an absolute flux calibration error of $\sim$10% based on the amplitude variations of gain calibrators over time." (3 ALMA OBSERVATIONS)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs robust = +0.5  
  > "cleaning with a Briggs robust weighting parameter of +0.5" (3 ALMA OBSERVATIONS)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub in CASA  
  > "by subtracting the continuum from the spectral windows containing line emission using the *uvcontsub* routine in `CASA`" (3 ALMA OBSERVATIONS)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.31"x0.25" average  
  > "for an average beam size of 0.31$''$$\times$0.25$''$" (3 ALMA OBSERVATIONS)
- final rms: 0.15 mJy/beam continuum  
  > "average continuum rms of 0.15 mJy beam$^{-1}$" (3 ALMA OBSERVATIONS)

### Inherited from earlier work

- Mdust-Mstar comparison done following the Lupus survey procedure, including uniform dust-mass calculation and MC for unknown stellar masses  
  > "we follow the procedure described in (cite: 2016ApJ...828...46A)" (6.2 Mdust-Mstar Relation) [from (cite: 2016ApJ...828...46A)]
- Bayesian linear regression for Mdust-Mstar  
  > "again using the Bayesian linear regression method of (cite: 2007ApJ...665.1489K)" (6.2 Mdust-Mstar Relation) [from (cite: 2007ApJ...665.1489K)]
- Kaplan-Meier mean dust mass with ASURV  
  > "We follow this procedure to now include results from our ALMA survey" (6.3 Dust Mass Distributions) [from (cite: 2016ApJ...828...46A)]
- Vscale: V-J spectral type relation  
  > "(Manara et al. 2017, submitted)" (2 SAMPLE) [from Manara et al. 2017, submitted]

### Not stated but needed to reproduce (our reading)

- Continuum channel selection / line-free channels
- Image size, cell size, clean threshold and masking
- Whether uvmodelfit starting guesses were used
- Integration velocity ranges and aperture radii for each CO detection
- Details of Kelly linmix settings (chains, priors)
- Exact WB14 grid parameters and how the log-mean is computed
- Stacking weighting scheme
- Machine-readable tables only online

## Analysis recipe

1. **Measure continuum flux densities**: Fit point-source models (elliptical Gaussian for 5 resolved sources) to visibilities  
  > "we measure continuum flux densities by fitting point-source models to the visibility data using the *uvmodelfit* routine in `CASA`." (4.1 1.33 mm Continuum Emission)
   - software: CASA uvmodelfit
   - parameter: uncertainties scaled by sqrt of reduced chi2; detection >3 sigma  
  > "We scale the uncertainties on the fitted parameters by the square root of the reduced $\chi^{2}$ value of the fit." (4.1 1.33 mm Continuum Emission)
   - fitting: _not stated_
   - validation: _not stated_
2. **Detect and measure CO lines**: Extract spectra in 0.30" aperture, find >3 rms in multiple channels, zero-moment maps, curve-of-growth aperture photometry; detection if F>4 sigma  
  > "We consider sources as detections when $F_{\rm 12CO}>4 \times E_{\rm 12CO}$." (4.2 CO Line Emission)
   - software: CASA
   - parameter: non-detections: upper limits 3x image rms, integrate ±1 km/s of known RV or 13 km/s (Group 2)  
  > "We found no additional detections, thus took upper limits as 3$\times$ the image rms." (4.2 CO Line Emission)
   - fitting: _not stated_
   - validation: 4 sigma threshold adopted to avoid false detections  
  > "this procedure selects both the velocity range and aperture size that maximize the signal, thus can produce false detections at lower significance levels." (4.2 CO Line Emission)
3. **Derive stellar masses**: Place sources on HR diagram vs Siess et al. tracks; Teff from SpT, L from J band; MC of 1000 perturbations for uncertainty  
  > "We then calculate the uncertainties on $M_{\ast}$ using a Monte Carlo (MC) method, where we take the standard deviation of 1000 estimates of $M_{\ast}$" (2 SAMPLE)
   - assumption: distance 385 pc  
  > "We adopt a cluster distance of 385 pc" (2 SAMPLE)
   - fitting: _not stated_
   - validation: _not stated_
4. **Convert continuum flux to dust mass**: Optically thin Hildebrand formula, Mdust = F d^2/(kappa B(T))  
  > "Equation [\[eqn-mass\]](#eqn-mass) can therefore be approximated as $M_{\rm dust}\approx1.34\times10^{-5}~F_{1.33{\rm mm}}$, where $F_{1.33{\rm mm}}$ is in mJy and $M_{\rm dust}$ is in $M_{\odot}$." (Dust Masses)
   - assumption: Tdust = 20 K; kappa = 10 cm2/g at 1000 GHz, beta = 1; d = 385 pc  
  > "We take the dust grain opacity, $\kappa_{\nu}$, as 10 cm$^{2}$ g$^{-1}$ at 1000 GHz and use an opacity power-law index of $\beta=1$" (5.1 Dust Masses)
   - fitting: _not stated_
   - validation: _not stated_
5. **Estimate gas masses**: Compare 12CO and 13CO luminosities to WB14 grid (mean in log space of consistent models, min/max limits); alternatively M16 DALI relations for 13CO/C18O limits  
  > "we calculate the mean (in log space) of the WB14 model grid points consistent with our measured line luminosities and their associated errors" (5.2 Gas Masses)
   - software: DALI (via M16 models)
   - assumption: [CO]/[H2]=1e-4 (WB14); [C]/[H]=1.35e-4, 1 Myr (M16); [CO]/[13CO]=70  
  > "assumed molecular CO abundance of ${\rm [CO]/[H_{2}]}=10^{-4}$ in the case of WB14" (5.2 Gas Masses)
   - fitting: _not stated_
   - validation: _not stated_
6. **Stack non-detections**: Average images in image plane after centering on expected positions, then aperture photometry  
  > "To stack the images, we average them in the image plane after centering them on their expected source locations." (5.3 Stacking Analysis)
   - fitting: _not stated_
   - validation: Compared with mean of catalog fluxes  
  > "We confirm this non-detection by calculating the mean and standard error on the mean from the continuum fluxes reported in Table" (5.3 Stacking Analysis)
7. **Fit Mdust-Mstar relation and compare regions**: Kelly (2007) Bayesian linear regression with upper limits; Kaplan-Meier means and two-sample tests with ASURV  
  > "we derive a linear fit with $\alpha=1.0\pm0.2$, $\beta=2.0\pm0.4$, and $\delta=0.6\pm0.1$ dex" (6.2 Mdust-Mstar Relation)
   - software: ASURV, linmix (Kelly 2007)
   - parameter: Mstar >= 0.1 Msun  
  > "We only consider sources in our ALMA sample with $M_{\ast}\ge0.1~M_{\odot}$" (6.2 Mdust-Mstar Relation)
   - fitting: Bayesian linear regression (Kelly 2007); priors not stated  
  > "Here we derive the $M_{\rm dust}$–$M_{\ast}$ relation for $\sigma$ Orionis disks, again using the Bayesian linear regression method of (cite: 2007ApJ...665.1489K)." (M_dust–M_* Relation)
   - validation: Refit without highest-mass undetected source gave same parameters  
  > "when re-fitting the distribution without this source, we recover the same parameters." (6.2 Mdust-Mstar Relation)

## Software

- **CASA** 4.5.3: Pipeline calibration, imaging, uvcontsub, uvmodelfit  
  > "pipeline calibrated by NRAO staff using the `CASA` package (version 4.5.3)" (3 ALMA OBSERVATIONS)
- **ASURV** : Kaplan-Meier means and two-sample tests with upper limits  
  > "derived the average dust mass using the Kaplan-Meier estimator in the `ASURV` package" (6.3 Dust Mass Distributions)
- **DALI** : Underlying code of the M16 gas model grid  
  > "Using the code DALI (cite: 2012A&A...541A..91B), M16 investigated a range of realistic disk and stellar parameters" (5.2 Gas Masses)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum detections | 37 of 92 | not stated | sources | 1 | We detect only 37 out of the 92 observed sources at $>3\sigma$ significance |
| Disks with Mdust>10 Mearth | 11 | not stated | disks | 4 | only 11 disks have $M_{\rm dust}>10~M_{\oplus}$ |
| Stack of 55 continuum non-detections | 0.05 | 0.03 | mJy | 6 | The measured continuum mean signal is 0.05$\pm$0.03 mJy (1.7$\sigma$). |
| 3 sigma average dust mass upper limit of undetected | 0.4 | not stated | Mearth | 6 | This provides a 3$\sigma$ upper limit on the average dust mass of individually undetected continuum sources of 0.4 $M_{\oplus}$ |
| Mdust-Mstar fit slope beta | 2.0 | 0.4 | dimensionless | 7 | $\alpha=1.0\pm0.2$, $\beta=2.0\pm0.4$, and $\delta=0.6\pm0.1$ dex |
| Mean dust mass sigma Ori | 7 | 1 | Mearth | 7 | we find average disk dust masses of $7\pm1$ $M_{\oplus}$ for $\sigma$ Orionis |
| Gas masses of 3 disks detected in 12CO and 13CO | 2–7 | not stated | MJup | 5 | these values span 2–7 $M_{\rm Jup}$ |
| Transition disk fraction among continuum detections | 16% (6/37) | not stated | percent | 0 | Thus 16% (6/37) of our ALMA continuum detections are TDs |

## Qualitative findings

- Dust masses decline toward the central O9 star; CO detections only at projected separations >1.5 pc, consistent with external photoevaporation  
  > "dust masses clearly decline with decreasing separation from the photoionizing source, and the handful of CO detections exist at projected separations $>1.5$ pc." (abstract)

## Claim tuples

- H: Do most sigma Ori disks retain enough dust to form giant planet cores? | E: Convert 1.33 mm fluxes to dust masses for 92 disks | R: Only 11 disks have Mdust>10 Mearth | F: Most disks lack dust for giant planet cores after a few Myr | **supported**
- H: Is external photoevaporation affecting disks? | E: Dust mass vs projected separation from sigma Ori | R: Lack of massive disks within ~0.5 pc and smooth distance dependence; CO detections only at large separation | F: External FUV photoevaporation affects disks throughout the cluster | **supported**
- H: Does the Mdust-Mstar relation steepen with age? | E: Kelly regression compared across regions | R: beta = 2.0±0.4 vs 1.7–1.8 for younger and 2.4 for Upper Sco | F: Consistent with steepening, but errors large | **partially**

## Reasoning

- Why this data: Sensitivity chosen to give 3–4 sigma detections of the mean stacked SCUBA-2 signal  
  > "The sensitivity of our ALMA survey was therefore chosen to provide $\sim$3–4$\sigma$ detections of such disks at 1.3 mm" (3 ALMA OBSERVATIONS)
- Why this method: _not stated_
- Alternative: Isothermal Tdust used rather than luminosity-scaled temperature relation  
  > "we use an isothermal disk temperature as more detailed modeling of resolved disks suggests that $T_{\rm dust}$ is independent of stellar parameters." (5.1 Dust Masses)
- How they decided it was enough: _not stated_
- Limitation (authors): Many upper limits, uncertain stellar properties; gas masses could be underestimated by carbon depletion  
  > "due to the abundance of upper limits in our ALMA sample, and the need for better constraints on stellar properties" (7 Summary)
- Caveat (inferred, ours): Single-opacity isothermal dust mass assumption
- Caveat (inferred, ours): Gas masses rely on CO abundance and have large range
- Caveat (inferred, ours): Regression dominated by upper limits
- Caveat (inferred, ours): Photometric spectral types for 23 sources
- Caveat (inferred, ours): Mass segregation and external photoevaporation may bias trends

## Reproducibility

- Data public (paper): Project ID and ALMA acknowledgement given; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA2015.1.00089.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Image/cell sizes, masks, clean thresholds
- Missing: Line velocity ranges and aperture sizes
- Missing: Machine-readable tables (online only)
- Missing: linmix settings
- Missing: Manara et al. 2017 V-J relation (submitted)
- Data volume (inferred): ~100 GB to a few hundred GB raw for 92 short-pointing fields (Band 6 two executions)
- Score (inferred): 3/5, Data and recipe mostly stated with CASA and clear formulae, but imaging details and several procedure parameters are missing.
- Rediscovery candidate: yes, Public ALMA project, clear photometry and mass formulae, numeric results (detections, dust masses, stacks) can be reproduced.

## Links

- Method: (cite: 2016ApJ...828...46A) (Lupus survey methodology followed for comparison)
- Method: (cite: 2007ApJ...665.1489K) (Bayesian regression method)
- Method: (cite: 2014ApJ...788...59W) (gas mass model grid)
- Companion: (cite: 2016ApJ...831..125P) (Chamaeleon I ALMA survey compared)
- Companion: (cite: 2016ApJ...827..142B) (Upper Sco ALMA survey compared)
- Related: ALMA Lupus survey
- Related: ALMA Upper Sco survey
- Related: ALMA Chamaeleon I survey
- Related: JCMT/SCUBA-2 sigma Orionis survey

## Checks

```json
{
 "quotes": 73,
 "quotes_ok": 73,
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
  "facts": 87,
  "stated": 57,
  "rate": 0.655
 },
 "evidence_ok": true
}
```
