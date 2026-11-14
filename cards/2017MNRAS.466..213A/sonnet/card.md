# New ATCA, ALMA and VISIR observations of the candidate LBV SK -67 266 (S61): the nebular mass from modelling 3D density distributions

`2017MNRAS.466..213A` | Monthly Notices of the Royal Astronomical Society 2017 | first author: Agliozzo, C. | arXiv: 1611.05259 | DOI: 10.1093/mnras/stw2986

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation, milky_way_ism
- Question: What is the ionised nebular mass and mass-loss history of the candidate LBV S61, derived by modelling 3D electron density distributions fitted to ATCA radio maps, and where is its dust (ALMA/VISIR non-detections)?  
  > "to introduce a quantifiable and objective method for determining the nebular mass via Bayesian estimation of geometrical nebula parameters" (Introduction)
- Target **S61 (SK -67 266, AL 418)**: coordinates _not stated_; z/distance 48.5 kpc (LMC)  
  > "assuming a distance of 48.5 kpc" (4.2 Application to the S61 nebula); distance from assumed distance of the LMC  
  > "assuming a distance of 48.5 kpc" (4.2 Application to the S61 nebula)

## Data provenance

- ALMA projects: 2013.1.00450.S
- bands: Band 7 continuum  
  > "A standard Band 7 continuum spectral setup was used" (2.2 The ALMA observation and data reduction)
- frequencies and spectral setup: four 2-GHz spectral windows of 128 channels centred at ~336.5, 338.5, 348.5, 350.5 GHz  
  > "giving four 2-GHz width spectral windows of 128 channels of XX and YY polarisation correlations centred at approximately 336.5 (LSB), 338.5 (LSB), 348.5 (USB) and 350.5 (USB) GHz" (2.2 The ALMA observation and data reduction)
- continuum bandwidth: ~7.5 GHz usable, 343.5 GHz average  
  > "We imaged all spectral windows together ($343.5\,{\rm GHz}$ average; approximately $7.5\,{\rm GHz}$ usable bandwidth)" (2.2 The ALMA observation and data reduction)
- arrays: 40 12m antennas, single execution  
  > "A single execution of 80 minutes total duration, including the three targets, was performed on 2014-12-26 with 40 12m antennas" (2.2 The ALMA observation and data reduction)
- configurations: _not stated_
- baselines: 10 to 245 m projected  
  > "with projected baselines from 10 to 245 m" (2.2 The ALMA observation and data reduction)
- angular resolution: 1.23x0.95 arcsec, PA 78.6 deg  
  > "| ALMA  | 343         | 1.23$\times$0.95   | 6.7    | 78.6        | 0.290        | 0.072        |" (Table 1)
- max recoverable scale: LAS 6.7 arcsec  
  > "| ALMA  | 343         | 1.23$\times$0.95   | 6.7    | 78.6        | 0.290        | 0.072        |" (Table 1)
- sensitivity: rms 72 uJy/beam (proposed 40 uJy/beam)  
  > "yielding RMS noise of $72\,\mu{\rm Jy}\,{\rm beam^{-1}}$ in the image" (2.2 The ALMA observation and data reduction)
- time on source: 16 minutes per target  
  > "integration time per target of 16 minutes" (2.2 The ALMA observation and data reduction)
- observing dates: 2014-12-26  
  > "was performed on 2014-12-26" (2.2 The ALMA observation and data reduction)
- pi or archival as stated: _not stated_
- Other facility **ATCA**: 5.5, 9, 17, 23 GHz radio continuum maps; 17 GHz map used for main modelling  
  > "We split the receiver bandwidth in two 2-GHz sub-bands, one centred at 17 GHz and the other at 23 GHz." (2.1 ATCA observations and data reduction)
- Other facility **VLT/VISIR**: mid-IR imaging at 11.88 and 17.65 um (non-detection)  
  > "narrow bandwidth filters PAH2$\_$2 and Q1, centred respectively at 11.88 and 17.65 $\rm \mu$m" (2.3 VLT/VISIR observations)
- Other facility **HST/WFPC2**: Halpha F656N image  
  > "using the $\rm H \rm \alpha$-equivalent filter F656N" (2.4 Optical data)
- External data: 5.5 and 9 GHz ATCA data and flux densities  
  > "These data were presented in Paper I." (2.1 ATCA observations and data reduction) [from Agliozzo et al. 2012 (cite: 2012Agliozzo) (Paper I)]
- External data: Archival IR flux densities from WISE, AKARI, Spitzer MIPS, Herschel PACS  
  > "we extracted the flux densities in the *WISE* bands W3 and W4" (5.2 Extinction map and nebular dust) [from (cite: 2012aCutri; 2010aIshihara; 2010aArdila; 2013Meixner)]
- External data: Nebular expansion velocity ~27 km/s  
  > "the expansion velocity is 27 $\rm km\,s^{-1}$ (cite: Weis2003)" (5.1 The mass-loss history) [from (cite: Weis2003)]
- External data: Electron temperature 6120 K  
  > "Adopting as electron temperature $6120\,\rm K$ (cite: 1999Pasquali)" (5.2 Extinction map and nebular dust) [from (cite: 1999Pasquali)]

## Processing

### Calibration

- pipeline or manual: manual non-standard calibration steps in CASA, deferred to another article  
  > "Extra non-standard calibration steps were required to minimise image degradation due to phase smearing" (2.2 The ALMA observation and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Pictor A (PKS J0519-4546) for flux scale; QSO J0538-4405 bandpass  
  > "QSO$\,$J0538-4405 and Pictor A(PKS J0519-4546; an ALMA secondary flux calibrator ‘grid’ source) were used for interferometric bandpass and absolute flux scale calibration" (2.2 The ALMA observation and data reduction)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA  
  > "Data were calibrated and imaged with the Common Astronomy Software Applications (CASA) package" (2.2 The ALMA observation and data reduction)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "We derived the intensity image from naturally weighted visibilities to maximise sensitivity and image quality" (2.2 The ALMA observation and data reduction)
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

- Non-standard ALMA calibration techniques deferred to another paper  
  > "we defer discussion of these techniques to an article on the other sources in the sample (Agliozzo et al. 2016, submitted)" (2.2 The ALMA observation and data reduction) [from Agliozzo et al. 2016, submitted]
- Y=1 for ionised He/H as in Paper I  
  > "Y is a factor incorporating the ionised He/H ratios (assumed to be 1, as in Paper I)" (5.2 Extinction map and nebular dust) [from Paper I (cite: 2012Agliozzo)]

### Not stated but needed to reproduce (our reading)

- CASA version for ALMA reduction
- Details of the non-standard calibration (phase smearing correction, shadowed antennas)
- Cell size, image size, and any CLEAN parameters for the ALMA image
- Source of the nebular-extent region used for the ALMA upper limit
- Priors on shell parameter offsets beyond 'narrow Gaussians' (widths)

## Analysis recipe

1. **Measure radio flux densities and spectral index**: Integrate 17 GHz emission above 3 sigma in CASA viewer; weighted power-law fit to 5.5, 9, 17 GHz; per-pixel spectral index map  
  > "we selected with the polygonal tool the area above $3\sigma$ level and integrated the emission over the nebula" (3 The Radio Emission)
   - software: CASA
   - fitting: weighted power-law fit  
  > "through a weighted fit of the power-law $S_{\nu}\propto\nu^{\alpha}$" (3 The Radio Emission)
   - validation: _not stated_
2. **Fit 3D electron density shell models to emission measure maps**: RHOCUBE models (truncated normal shell, power-law shell exponents 0,-1,-2) fit to EM maps with MCMC; analytic global scale S via chi-squared  
  > "we can find a global scale $S$ such that the likelihood is maximised, or equivalently, the chi-squared statistic" (4.2 Bayesian parameter inference)
   - software: RHOCUBE, MCMC
   - parameter: 2e4 MCMC samples; 41x41 and 101x101 pixel maps; distance 48.5 kpc  
  > "These posteriors were obtained after drawing $2\times10^4$ MCMC samples." (4.2 Application to the S61 nebula)
   - assumption: distance 48.5 kpc; spherical shell; gas only ionised hydrogen  
  > "under the assumption that the gas comprises only ionised hydrogen" (4.3 Ionised mass)
   - fitting: Metropolis-Hastings MCMC, uniform priors on radii/widths, narrow truncated Gaussian priors on offsets, chi-squared likelihood  
  > "We used uniform prior probability distributions" (4.2 Application to the S61 nebula)
   - validation: reduced chi-squared of MAP models, azimuthal mean profiles compared with data  
  > "Panel (7) illustrates azimuthal mean profiles derived from 18 extracted cuts" (4.2 Application to the S61 nebula)
3. **Derive ionised mass and ionising photon flux**: Sum n_e over voxels times m_p; posterior of derived mass from chains  
  > "Thanks to the MCMC approach we can use the entire converged chains of model parameter values to compute posterior distributions of *derived* quantities" (4.3 Ionised mass)
   - software: RHOCUBE
   - fitting: _not stated_
   - validation: compared to Paper I estimate  
  > "The value derived with this new approach is about 2.7 times smaller than the previous estimate." (4.3 Ionised mass)
4. **Derive mass-loss history**: Each voxel mapped to kinematical age using expansion velocity; integrate mass over shells  
  > "each voxel of our datacube corresponds to a kinematical age" (5.1 The mass-loss history)
   - assumption: expansion velocity 27 km/s; isotropic mass loss  
  > "we can assume that the star has lost mass isotropically" (5.1 The mass-loss history)
   - fitting: _not stated_
   - validation: compared to empirical mass-loss rate following Vink et al. 2000  
  > "We now compare the mass-loss history with the empirical mass-loss rate" (5.1 The mass-loss history)
5. **Extinction map and dust constraints**: Compare 17 GHz radio with Halpha (Pottasch); greybody SED fit to mid/far-IR; extrapolate to 343 GHz and VISIR bands; dust mass from M_d=S D^2/(B kappa)  
  > "We fitted a single-temperature greybody with power-law opacity index $\beta$ at longer wavelengths and constant opacity at shorter wavelengths" (5.2 Extinction map and nebular dust)
   - parameter: beta = 0.55, 1, 1.5; lambda0 18-25 um  
  > "we explored the cases for $\beta = 0.55, 1$ and $1.5$) and $\lambda_{0}$ (between 18 and 25 $\rm \mu$m)" (5.2 Extinction map and nebular dust)
   - assumption: kappa(343 GHz)=1 cm^2/g  
  > "assuming $\kappa_{343\rm \,GHz}= 1\rm \,cm^{2}\,g^{-1}$" (5.2 Extinction map and nebular dust)
   - fitting: single-temperature greybody fit  
  > "We fitted a single-temperature greybody with power-law opacity index $\beta$ at longer wavelengths and constant opacity at shorter wavelengths" (Extinction map and nebular dust)
   - validation: _not stated_

## Software

- **CASA** : ALMA calibration and imaging; viewer for flux integration  
  > "Data were calibrated and imaged with the Common Astronomy Software Applications (CASA) package" (2.2 The ALMA observation and data reduction)
- **MIRIAD** : ATCA reduction and imaging  
  > "We performed the data reduction and imaging using the MIRIAD package" (2.1 ATCA observations and data reduction)
- **RHOCUBE** : 3D density modelling  
  > "a PYTHON code to model 3D density distributions" (4.1 3D density model RHOCUBE)
- **VISIR pipeline kit / Esoreflex** 4.0.7 / 2.8: VISIR data reduction  
  > "recipe $visir\_image\_combine.xml$ of the VISIR pipeline kit (version 4.0.7) in the environment Esoreflex 2.8" (2.3 VLT/VISIR observations)
- **IRAF** : HST image combination  
  > "following a standard procedure in IRAF" (2.4 Optical data)
- **SEABORN** : kernel density estimation of chain histograms  
  > "Computed with SEABORN" (4.2 Application to the S61 nebula)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA 343 GHz rms noise | 72 | not stated | uJy/beam | 0 | yielding RMS noise of $72\,\mu{\rm Jy}\,{\rm beam^{-1}}$ in the image |
| ALMA 3-sigma upper limit over nebula | ~3.6 | not stated | mJy | 5 | yields a 3$\sigma$ upper limit of $\sim 3.6\,\rm mJy$ |
| 17 GHz integrated flux density | 1.97 | 0.10 | mJy | 1 | / 2.1$\pm$0.1 / 2.2$\pm$0.3 / 1.97$\pm$0.10 / 4.5$\times$4.9 /     -0.06$\pm$0.06     / |
| global spectral index | -0.06 | 0.06 | dimensionless | 1 | The “global” spectral index $\langle\alpha\rangle=-0.06\pm0.06$ is consistent with optically thin free-free emission. |
| ionised mass, TNS 17 GHz (median) | 0.03 | +0.04/-0.02 | Msun | 3 | $0.03^{+0.04}_{-0.02}$ |
| ionised mass, TNS 17 GHz (MAP) | 0.13 | not stated | Msun | 3 | The MAP-model values are $0.29~\ensuremath{M_\odot}$ and $0.13~\ensuremath{M_\odot}$. |
| peak mass-loss rate | 1.5e-5 at ~19100 yr | not stated | Msun/yr | 4 | the peak of the mass-loss has occurred at epoch $\sim 19100$ yr with a rate of $1.5\times10^{-5}\,\rm \ensuremath{M_\odot}\,yr^{-1}$ |
| dust mass | 5e-3 to 2.7e-2 | not stated | Msun | 5 | we derived a dust mass $M_{d} = 5\times10^{-3}$ to $2.7\times10^{-2}\,\rm \ensuremath{M_\odot}$ |
| expected ALMA 343 GHz flux density | 0.8 | +1.2/-0.5 | mJy | 5 | $0.8^{+1.2}_{-0.5}\,\rm mJy$ |
| log ionising photon flux | 44.5 | not stated | dimensionless (log) | 3 | We find $\rm Log(F_{UV})=44.5$ |

## Qualitative findings

- Radio nebula resembles a spherical shell like the Halpha nebula, with more substructure; emission is optically thin free-free with hints of self-absorption.  
  > "The emission mechanism is optically thin free-free, as evidenced by the spectral index map, although there are regions that suggest self-absorption." (Conclusions)
- Nebula likely density bounded.  
  > "The nebula is very likely density bounded, meaning that part of the stellar UV flux escapes from the nebula." (Conclusions)

## Claim tuples

- H: Is the ionised mass of S61's nebula as large as earlier estimates? | E: Bayesian MCMC fits of 3D shell models to 9 and 17 GHz EM maps | R: All well-fitting geometries give ~0.1 Msun | F: Mass an order of magnitude smaller than previous estimates | **supported**
- H: Was the nebula formed by eruptions or winds? | E: Compared modelled mass-loss history to empirical wind mass-loss rate | R: Rates consistent with ~6.6e-6 Msun/yr empirical and bi-stability scenario | F: Formed by stellar winds rather than eruptions | **partially**
- H: Can ALMA/VISIR detect dust in the nebula? | E: Band 7 and mid-IR imaging | R: Non-detections; expected extended emission below sensitivity | F: Dust is extended, diffuse within the ionised region | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Power-law shell exponents smaller than -2 gave lower-quality results and were not discussed.  
  > "We noticed that exponents smaller than -2 were producing lower-quality results and therefore we will not comment on them." (4.2 Application to the S61 nebula)
- How they decided it was enough: _not stated_
- Limitation (authors): The data cannot constrain the electron density distribution.  
  > "with the current data we cannot constrain the electron density distribution in the S61 nebula" (4.2 Application to the S61 nebula)
- Limitation (authors): ALMA sensitivity target not reached; single execution.  
  > "which could not be achieved as no further executions were possible during the appropriate array configuration in Cycles 2 and 3" (2.2 The ALMA observation and data reduction)
- Caveat (inferred, ours): Reduced chi-squared values of 22-100 indicate poor model fits
- Caveat (inferred, ours): Single-distance assumption and spherical symmetry drive mass
- Caveat (inferred, ours): ALMA is only an upper limit; dust mass relies on assumed kappa and extrapolated SED
- Caveat (inferred, ours): MAP and median masses differ by factor of several

## Reproducibility

- Data public (paper): Code and FITS data supplied in public git repository  
  > "A git repository for this manuscript, holding all supplementary files including the data FITS files, is accessible at" (7 Supplements)
- Products in archive: _not stated_
- Code: RHOCUBE and analysis scripts at github.com/rnikutta/rhocube and s61-supplements  
  > "RHOCUBE (cite: rhocube) is a general-use, stand-alone code and is distributed as such in the following git repository" (7 Supplements)
- Missing: Non-standard ALMA calibration details
- Missing: CASA version
- Missing: MCMC sampler implementation details and offset prior widths
- Data volume (inferred): ~10 GB (single ALMA execution, plus small ATCA/VISIR data)
- Score (inferred): 3/5, Main results come from ATCA maps and a public code; ALMA part is a non-detection with undescribed calibration.
- Rediscovery candidate: no, ALMA is a non-detection; main numerical results rely on ATCA data and custom modelling.

## Links

- Method: (cite: rhocube) (Modelling code)
- Method: (cite: 1995SaultMiriad) (ATCA reduction package)
- Companion: Agliozzo et al. 2012 (Paper I) (Earlier ATCA 5.5/9 GHz observations of S61)
- Companion: Agliozzo et al. 2016, submitted (ALMA non-standard calibration for other sample sources)

## Checks

```json
{
 "quotes": 71,
 "quotes_ok": 71,
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
  "facts": 84,
  "stated": 55,
  "rate": 0.655
 },
 "evidence_ok": true
}
```
