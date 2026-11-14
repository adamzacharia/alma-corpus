# GA-NIFS: Early-stage feedback in a heavily obscured active galactic nucleus at z = 4.76

`2024A&A...684A..24P` | Astronomy and Astrophysics 2024 | first author: Parlanti, Eleonora | arXiv: 2309.05713 | DOI: 10.1051/0004-6361/202347914

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: agn_and_quasars, high_z_galaxies
- Question: What are the BH properties, outflow and host-galaxy kinematics of the obscured AGN ALESS073.1 at z=4.755 from JWST NIRSpec IFS, compared with ALMA [CII] kinematics?  
  > "We use NIRSpec observations to study the properties of the BH and investigate the impact of AGN-driven outflows (if any) on the host galaxy." (Introduction)
- Target **ALESS073.1**: coordinates RA 03h32m29.290s, Dec -27d56m19.30s  
  > "ALESS073.1 is part of the Extended Chandra Deep Field South (cite: Lehmer:2005) (RA: 03h32m29.290s, DEC:-27d56m19.30s)." (2.1 Target); "a massive ($M_\star \sim 10^{11}$ M$_{\odot}$) SMG at $z = 4.755$" (Introduction); z/distance z = 4.755  
  > "ALESS073.1 is part of the Extended Chandra Deep Field South (cite: Lehmer:2005) (RA: 03h32m29.290s, DEC:-27d56m19.30s)." (2.1 Target); "a massive ($M_\star \sim 10^{11}$ M$_{\odot}$) SMG at $z = 4.755$" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2017.1.01471.S, 2015.1.00040.S
- bands: Band 7  
  > "ALESS073.1was observed with ALMA Band-7, with a total integration time of $\sim 1.5$ h, to target the [C] emission line." (2.3 ALMA observation and data reduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 14 m to 2516 m  
  > "The maximum and minimum baselines are 2516 and 14 m, respectively." (2.3 ALMA observation and data reduction)
- angular resolution: 0.17'' x 0.14'' beam  
  > "The resulting datacube has a beam size of $0.17 \ensuremath{''} \times 0.14\ensuremath{''}$." (2.3 ALMA observation and data reduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: ~1.5 h total integration  
  > "with a total integration time of $\sim 1.5$ h" (2.3 ALMA observation and data reduction)
- observing dates: _not stated_
- pi or archival as stated: Archival, PI Lelli  
  > "We retrieve the [C] raw data from the ALMA archive (2017.1.01471.S, PI: Lelli)" (2.3 ALMA observation and data reduction)
- Line: [CII] 158 um fine-structure (not stated)
- Other facility **JWST NIRSpec IFS (GA-NIFS, program 1216)**: G235H/F170LP and G395H/F290LP cubes; Halpha, [NII], BLR, outflow and kinematics  
  > "with both G235H/F170LP and G395H/F290LP gratings/filters combinations to target the emission of the galaxy from 1.7 to 5.2 $\mu$m" (2.2 JWST observations and data reduction)
- Other facility **HST, Subaru, Spitzer, Herschel**: Photometry for SED fitting  
  > "The UV-to-NIR photometry is taken from (cite: Merlin:2021)" (SED fitting)
- External data: Stellar mass (4.7±1.6)e10 Msun from [CII] kinematics and inclination 22 deg  
  > "we use the stellar mass of $M_\star = (4.7\pm1.6) \times 10^{10}~ \rm M_\odot$ computed by (cite: Lelli:2021) with a kinematic analysis" (5 Black hole properties) [from (cite: Lelli:2021)]
- External data: Photometry for SED fitting (UV-NIR)  
  > "The UV-to-NIR photometry is taken from (cite: Merlin:2021)" (SED fitting) [from (cite: Merlin:2021)]
- External data: N_H = 17.0 x 10^23 cm^-2 from X-ray  
  > "estimation of the column density of $N_{\rm H} = 17.0^{+11.7}_{-6.8} \times 10^{23}$ cm$^{-2}$ (cite: Circosta:2019)" (2.1 Target) [from (cite: Circosta:2019)]

## Processing

### Calibration

- pipeline or manual: Pipeline scripts included in the dataset used for calibration in CASA  
  > "we use the pipeline scripts included in the datasets to calibrate the visibilities with the Common Astronomy Software Application `CASA`" (2.3 ALMA observation and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA tclean  
  > "Using the `CASA` task `tclean`, we perform the cleaning on the calibrated visibilities" (2.3 ALMA observation and data reduction)
- deconvolver: _not stated_
- weighting robust: natural  
  > "with a `natural` weighing scale and a spaxel scale of 0.05$''$" (2.3 ALMA observation and data reduction)
- uv taper: _not stated_
- cell size: 0.05''  
  > "with a `natural` weighing scale and a spaxel scale of 0.05$''$ to create the final datacube" (2.3 ALMA observation and data reduction)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: ALMA cube convolved with Photutils matching kernel to the JWST PSF (0.20''x0.17'')  
  > "we used the Python library `Photutils` to create a matching kernel between ALMA and JWST PSFs." (7 Gas kinematics)
- final beam: 0.17'' x 0.14''  
  > "The resulting datacube has a beam size of $0.17 \ensuremath{''} \times 0.14\ensuremath{''}$." (2.3 ALMA observation and data reduction)
- final rms: _not stated_

### Inherited from earlier work

- Kinematic modelling approach with KinMS+emcee  
  > "Following (cite: Parlanti:2023), we model the H$\alpha$ kinematics using the publicly available python library KINMS" (7 Gas kinematics) [from (cite: Parlanti:2023)]
- JWST pipeline modifications  
  > "These corrections are presented in detail in (cite: Perna:2023), but here we mention only the major changes." (2.2 JWST observations and data reduction) [from (cite: Perna:2023)]
- Outflow mass prescription  
  > "The mass of gas expelled by the outflow can be estimated by following (cite: Cresci:2023)" (6 Outflow) [from (cite: Cresci:2023)]

### Not stated but needed to reproduce (our reading)

- CASA version used for ALMA calibration and imaging
- Cleaning threshold, mask, niter and channel width of the [CII] cube
- Continuum subtraction and line-free channels for [CII]
- Spaxel-wise [CII] Gaussian fitting details and S/N cuts
- MCMC priors/walkers/convergence for KinMS fits
- Modified JWST pipeline code not public in the text

## Analysis recipe

1. **Image ALMA [CII] cube**: Calibrate with delivered pipeline scripts, then tclean with natural weighting, 0.05'' pixels  
  > "Using the `CASA` task `tclean`, we perform the cleaning on the calibrated visibilities with a `natural` weighing scale" (2.3 ALMA observation and data reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Match ALMA to JWST PSF and compare velocity dispersion maps**: Convolve ALMA cube with matching kernel, fit single Gaussian per spaxel to [CII], compare sigma maps with Halpha  
  > "The [C] moment maps are created by fitting spaxel-by-spaxel singular Gaussian component to the ALMA spectrum." (7 Gas kinematics)
   - software: Photutils
   - fitting: single Gaussian per spaxel  
  > "The [C] moment maps are created by fitting spaxel-by-spaxel singular Gaussian component to the ALMA spectrum." (Gas kinematics)
   - validation: Double Gaussian gives higher chi2 and BIC supports single component  
  > "the double Gaussian model returns a higher $\chi^2$ in all spaxel and the BIC test supports the single component fit." (7 Gas kinematics)
3. **Fit Halpha nuclear spectrum and spaxels (JWST)**: Least-squares Gaussian decomposition: BLR, outflow, host narrow; BIC selection per spaxel  
  > "we performed a least-square fitting by modeling the emission-line spectrum as a sum of Gaussian profiles." (3.1 Spectral fit of the central region)
   - fitting: _not stated_
   - validation: Delta BIC > 2 threshold  
  > "in those cases where the difference between BIC without outflow and BIC with outflow was larger than 2, we selected the model with two components" (Spatially resolved emission)
4. **Nonparametric Halpha ring kinematic model**: KinMS rings of 0.6 kpc with Gaussian continuity priors, inclination fixed at 22 deg, fitted by MCMC  
  > "the H$\alpha$ kinematics is modeled as a series of concentric circular rings having a width of 0.6 kpc" (7 Gas kinematics)
   - software: KinMS, emcee
   - assumption: inclination fixed to 22 deg  
  > "we fixed the inclination angle of the galaxy to 22 $\deg$ as found by (cite: Lelli:2021)" (7 Gas kinematics)
   - fitting: emcee MCMC  
  > "The best-fit parameter values for the kinematic model are found using the package EMCEE (cite: Foreman:2013) that allows us to estimate the posterior probability distribution" (Gas kinematics)
   - validation: Exponential-disk model disfavored by BIC  
  > "The BIC test for the velocity map extremely favors the nonparametric modeling ($\Delta BIC > 100$)." (Alternative kinematic fitting)

## Software

- **CASA** : Calibration and tclean imaging of ALMA data  
  > "Using the `CASA` task `tclean`" (2.3 ALMA observation and data reduction)
- **KinMS** : Halpha kinematic modelling  
  > "using the publicly available python library KINMS" (7 Gas kinematics)
- **emcee** : MCMC fit  
  > "using the package EMCEE" (7 Gas kinematics)
- **dynesty** : 2D morphological fit of Halpha map  
  > "The fit was carried out by using DYNESTY" (3.3 Morphology of the host galaxy)
- **Photutils** : Matching kernel between ALMA and JWST PSFs  
  > "we used the Python library `Photutils` to create a matching kernel" (7 Gas kinematics)
- **CIGALE** : SED fitting  
  > "by using the publicly available code `CIGALE`" (SED fitting)
- **webbpsf** : Theoretical JWST PSF  
  > "The `webbpsf` python tool (cite: Perrin:2014) generates the theoretical PSF" (IFS point spread function)
- **JWST Science Calibration Pipeline** 1.8.2: Reduction of NIRSpec data  
  > "modified version of the JWST Science Calibration Pipeline version 1.8.2" (2.2 JWST observations and data reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| BLR Halpha FWHM | 9008 | ±407 | km/s | 3 | $FWHM$ H$\alpha$$_{\rm BLR}$ / 9008 $\pm$ 407 |
| BH mass | log(MBH/Msun) > 8.7 | lower limit | dimensionless | 3 | we can only determine a lower limit on the BH mass: $\log{( M_{\rm BH}/M_\odot)} > 8.7$. |
| Eddington ratio | <0.18 | upper limit | dimensionless | 3 | we obtain an Eddington ratio of $\lambda_{\rm Edd} < 0.18$ |
| Ionized outflow rate | 11 | +57/-5.5 | Msun/yr | 3 | We infer a mass outflow rate of $\Dot{M}_{\rm out} = 11 ^{+57}_{-5.5}~ \rm M_\odot~ yr^{-1}$. |
| Mean sigma_Halpha - sigma_[CII] in north-south region | 100 | not stated | km/s | 2 | In these regions $\langle\sigma_{\rm H\alpha} - \sigma_{\rm [CII]}\rangle=100$ ${\rm km~s^{-1}}$ |
| Halpha disk velocity ring 1 | 337 | ±91 | km/s | 4 | Ring 1 / $0\leq r<0.6$ / $337^{+91}_{-91}$ |

## Qualitative findings

- Halpha velocity curve consistent with [CII]; Halpha dispersion higher than [CII] in inner 1.5 kpc  
  > "the velocity curves of the two tracers are consistent within the errors. The data however highlight a difference between H$\alpha$ and [C] in terms of velocity dispersion." (8 Discussion)

## Claim tuples

- H: Is ALESS073.1 a Type 1 AGN despite high N_H? | E: Fit nuclear Halpha spectrum | R: Broad Halpha FWHM ~9000 km/s | F: Type 1 AGN with MBH > 10^8.7 Msun, sub-Eddington | **supported**
- H: Does the outflow quench star formation? | E: Outflow energetics and mass loading | R: Mass loading ~0.06 | F: Outflow too weak to halt star formation | **supported**
- H: Do Halpha and [CII] trace the same kinematics? | E: Compare ring models and PSF-matched dispersion maps | R: Similar velocity curves, higher Halpha dispersion in centre | F: Outflow injects turbulence in warm gas but not dense gas | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Exponential-disk parametric kinematic model rejected by BIC in favour of nonparametric rings  
  > "The BIC test for the velocity map extremely favors the nonparametric modeling ($\Delta BIC > 100$)." (Alternative kinematic fitting)
- How they decided it was enough: _not stated_
- Limitation (authors): Outflow marginally resolved; mass outflow rate may be a lower limit; Hbeta undetected  
  > "We note that the outflow radius might be smaller than the angular resolution, therefore the reported mass outflow rate may be considered a lower limit." (6 Outflow)
- Caveat (inferred, ours): Assumed electron density 1000 cm^-3 dominates outflow uncertainty
- Caveat (inferred, ours): Halpha-[CII] dispersion difference may depend on different fitting approaches and beam smearing
- Caveat (inferred, ours): Inclination fixed at 22 deg strongly affects rotation velocities

## Reproducibility

- Data public (paper): ALMA data retrieved from archive; JWST from MAST  
  > "We retrieve the [C] raw data from the ALMA archive (2017.1.01471.S, PI: Lelli)" (2.3 ALMA observation and data reduction)
- Products in archive: _not stated_
- Missing: Modified JWST pipeline
- Missing: CASA version and clean parameters
- Missing: Priors and run settings for fits
- Data volume (inferred): ALMA Band 7 cube ~ tens of GB raw; JWST cubes from MAST ~ few GB
- Score (inferred): 3/5, Public data and many analysis details, but ALMA processing sparse and main results rely on JWST.
- Rediscovery candidate: no, ALMA plays a minor role and main results come from JWST data with modified pipeline.

## Links

- Method: (cite: Parlanti:2023) (Kinematic modelling with KinMS)
- Method: (cite: Perna:2023) (JWST pipeline modifications)
- Companion: (cite: Lelli:2021) ([CII] kinematics of ALESS073.1 from same ALMA data)
- Related: GA-NIFS

## Checks

```json
{
 "quotes": 59,
 "quotes_ok": 59,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 44,
  "rate": 0.587
 },
 "evidence_ok": true
}
```
