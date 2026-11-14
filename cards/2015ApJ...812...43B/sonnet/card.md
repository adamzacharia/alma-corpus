# HerMES: ALMA Imaging of Herschel-selected Dusty Star-forming Galaxies

`2015ApJ...812...43B` | The Astrophysical Journal 2015 | first author: Bussmann, R. S. | arXiv: 1504.05256 | DOI: 10.1088/0004-637X/812/1/43

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: How does gravitational lensing and multiplicity affect the properties of the brightest Herschel-selected DSFGs, and what do the lens models imply for the bright end of the intrinsic DSFG number counts?  
  > "Three aspects of our dataset make it uniquely suited to improving our understanding of the bright end of the intrinsic DSFG number counts." (Data)
- Target **29 HerMES Herschel-selected DSFGs (e.g. HXMM01, HXMM02, HADFS01, HECDFS12)**: coordinates per-source ALMA 870um centroids given in Table (e.g. HELAISS02 00:38:23.587 -43:37:04.15)  
  > "The sample was selected to be the 29 brightest DSFGs in the Southern sky that are not known radio AGN, nearby late-type galaxies, or Galactic emission." (2.1 Selection of DSFG Sample); z/distance not stated (z=2 assumed for some physical sizes)  
  > "The sample was selected to be the 29 brightest DSFGs in the Southern sky that are not known radio AGN, nearby late-type galaxies, or Galactic emission." (2.1 Selection of DSFG Sample); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00539.S
- bands: 870 um (Band 7)  
  > "We present 870$\,\mu$m 0$\ensuremath{''}$45 resolution imaging" (abstract)
- frequencies and spectral setup: Frequency Domain Mode, 7.5 GHz usable bandwidth, spws at 335.995, 337.995, 345.995, 347.996 GHz  
  > "providing a total usable bandwidth of 7.5$\,$GHz with spectral windows centered at 335.995$\,$GHz, 337.995$\,$GHz, 345.995$\,$GHz, 347.996$\,$GHz" (2.2 ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 20 m to 400 m  
  > "The antennas were configured with baseline lengths of 20$\,$m to 400$\,$m" (2.2 ALMA Observations)
- angular resolution: ~0.45 arcsec (0.5x0.4 arcsec beam)  
  > "providing a synthesized beamsize of $\approx 0.5\ensuremath{''} \times
0.4\ensuremath{''}$ FWHM" (2.2 ALMA Observations)
- max recoverable scale: _not stated_
- sensitivity: sigma ~0.2 mJy/beam (0.14 mJy in CDFS, ELAISS, COSMOS)  
  > "For the observations targeting the CDFS, ELAISS, and COSMOS fields, the data reach $\sigma \approx 0.14\,$mJy per beam." (2.2 ALMA Observations)
- time on source: ~10 min per target  
  > "This typically required 10 minutes of on-source integration time." (2.2 ALMA Observations)
- observing dates: 2012 June to 2012 December (Cycle 0)  
  > "ALMA data were obtained during Cycle 0 over the from 2012 June to 2012 December" (2.2 ALMA Observations)
- pi or archival as stated: PI: D. Riechers  
  > "(Program 2011.0.00539.S; PI: D. Riechers)" (2.2 ALMA Observations)
- Other facility **Gemini-South GMOS**: u,g,r,i,z imaging to identify lensing galaxies  
  > "The goal of the program is to use shallow $u$, $g$, $r$, $i$, and $z$ imaging to identify structure at redshifts below unity" (2.3 Gemini-South Imaging)
- Other facility **Herschel SPIRE**: source selection and 250/350/500 um photometry  
  > "individual catalogs were generated for each of the 250$\, \mu$m, 350$\,\mu$m, and 500$\,\mu$m *Herschel* Spectral and Photometric Imaging REceiver" (2.1 Selection of DSFG Sample)
- Other facility **HST / Keck / Spitzer**: existing imaging for lens identification and 24um priors  
  > "We also used *Spitzer*/MIPS (cite: 2004ApJS..154...25R) imaging" (2.1 Selection of DSFG Sample)
- External data: Herschel-SMA magnification measurements combined with ALMA sample  
  > "In this section, we combine our ALMA and SMA measurements of magnification factors" (5 Implications) [from (cite: Bussmann:2013lr)]
- External data: ALESS intrinsic number counts and COSMOS counts (broken power-law)  
  > "One is the number counts measured in ALESS (cite: Karim:2013lr)" (5.1 Statistical Predictions) [from (cite: Karim:2013lr)]
- External data: ALESS redshift distribution used for sources  
  > "which is based on photometric redshifts of optical counterparts to ALMA sources identified in ALESS (cite: Simpson:2014lr)" (5.1 Statistical Predictions) [from (cite: Simpson:2014lr)]
- Simulation/model as data: Mock DSFG catalogs from Bolshoi-based model (Hayward et al.) and galform lightcones (Cowley et al.) compared to dN/dA  
  > "we make use of mock catalogs of DSFGs that are based on numerical simulations" (4.3 Spatial Distribution)

## Processing

### Calibration

- pipeline or manual: Re-reduced NAASC-processed data in CASA; excluded high Tsys / poor phase data  
  > "We used the Common Astronomy Software Applications (CASA, version 4.2.1) package to re-reduce the data provided by the North American ALMA Science Center (NAASC)." (2.2 ALMA Observations)
- casa version: CASA 4.2.1  
  > "(CASA, version 4.2.1)" (2.2 ALMA Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Callisto, Neptune, Titan, Uranus; J2258-279 for HELAISS02; Butler-JPL-Horizons 2012 models  
  > "Finally, we updated the absolute flux calibration to use the Butler-JPL-Horizons 2012 solar system models" (2.2 ALMA Observations)
- flux scale uncertainty: ~10%  
  > "Uncertainties in flux density do not include the absolute calibration uncertainty of $\approx 10\%$." (Table 1)
- self calibration: phase selfcal for a handful of targets with peak S/N>20, ~10% S/N improvement  
  > "we obtained a $\approx 10\%$ improvement in S/N by using the CASA selfcal task with the clean component model as input" (2.2 ALMA Observations)

### Imaging

- task: CASA clean, Briggs weighting, multi-frequency synthesis  
  > "we used the CASA Clean task with Briggs weighting and “robust = $+$0.5”" (2.2 ALMA Observations)
- deconvolver: _not stated_
- weighting robust: robust = +0.5  
  > "we used the CASA Clean task with Briggs weighting and “robust = $+$0.5”" (2.2 ALMA Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: custom masks per target on high S/N regions  
  > "We designed custom masks for each target in CASA to ensure that only regions with high S/N were considered during the cleaning process." (2.2 ALMA Observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: flux divided by primary beam factor at source center  
  > "corrected for the primary beam by dividing the total flux density by the primary beam correction factor at the center of the source" (2.2 ALMA Observations)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Lens modeling methodology (visibility-plane fitting) follows earlier SMA work  
  > "The methodology used in this paper is similar in many aspects to that used in (cite: Bussmann:2012lr)" (3.1 Model Fitting Methodology) [from (cite: Bussmann:2012lr; Bussmann:2013lr)]
- Statistical lensing magnification model procedure  
  > "Our methodology follows the procedures outlined in previous efforts to predict magnification factors for DSFGs" (5.1 Statistical Predictions) [from (cite: Lima:2010fk; Wardlow:2013lr; Fialkov:2015eu)]
- Mock catalog generation (Bolshoi and galform models) described in other papers  
  > "We begin with the simulations, summarizing the methodology used to generate the mock catalogs here" (4.3 Spatial Distribution) [from Hayward et al. 2013 (cite: HB13); Cowley et al. (cite: Cowley:2015lr)]

### Not stated but needed to reproduce (our reading)

- Line-free channels/continuum definition and clean thresholds, cell and image size
- Which targets received selfcal and solint
- Exact MCMC convergence criteria; final phase of only 10 iterations
- Lens position/Einstein radius fixings are given per object but the SMA data and fits for the combined sample are not tabulated here
- Details of logistic regression and running-average smoothing parameters
- Mock-catalog processing settings beyond summary

## Analysis recipe

1. **Re-reduce and image ALMA data**: Re-reduce NAASC data in CASA, flag poor Tsys/phase data, selfcal for bright targets, Clean with Briggs weighting  
  > "For imaging, we used the CASA Clean task with Briggs weighting and “robust = $+$0.5” to achieve an optimal balance between sensitivity and spatial resolution." (2.2 ALMA Observations)
   - software: CASA
   - parameter: robust = +0.5  
  > "“robust = $+$0.5”" (2.2 ALMA Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Identify sources**: By-eye cataloging of sources with peak >5 sigma  
  > "We identify and catalog by-eye all sources with peak flux density greater than 5$\sigma$." (2.2 ALMA Observations)
   - fitting: _not stated_
   - validation: _not stated_
3. **Visibility-plane lens modeling**: uvmcmcfit: elliptical Gaussian sources, SIE lenses, ray tracing, compare model visibilities to data  
  > "Sources are assumed to be elliptical Gaussians that are parameterized by the following six free parameters" (3.1 Model Fitting Methodology)
   - software: uvmcmcfit, emcee
   - parameter: 512 walkers; burn-in 500-1000 iterations; final 10 iterations  
  > "We employ a “burn-in” phase with 512 walkers and 500-1000 iterations" (3.1 Model Fitting Methodology)
   - parameter: uniform priors; theta_E 0.1-6 arcsec; q_lens>0.3; q_s>0.2; r_s 0.01-1.5 arcsec  
  > "The axial ratios of the lenses and sources are restricted to be $q_{\rm lens} > 0.3$ and $q_{\rm s} > 0.2$." (3.1 Model Fitting Methodology)
   - assumption: Additional lenses at same redshift as primary; maximal-lensing Einstein radii fixed for weakly lensed systems  
  > "We assume secondary, tertiary, etc., lenses are located at the same redshift as the primary lens." (3.1 Model Fitting Methodology)
   - fitting: emcee affine-invariant ensemble MCMC with Gaussian likelihood in visibility plane  
  > "We use emcee (cite: Foreman-Mackey:2013yq) to sample the posterior probability density function (PDF) of our model parameters." (3.1 Model Fitting Methodology)
   - validation: Bolton ray tracing tested against Gravlens; residual maps inspected  
  > "tests of the Bolton ray-tracing routine indicate it produces results consistent with Gravlens" (3.1 Model Fitting Methodology)
4. **Compute magnifications and de-lens sample**: mu870 = ratio of lensed to intrinsic flux; KS tests of apparent vs intrinsic distributions; multiplicity rate  
  > "This is done simply by taking the ratio of the total flux density in the lensed image of the model ($S_{\rm
out}$) to the total flux density in the unlensed, intrinsic source model ($S_{\rm in}$)." (3.1 Model Fitting Methodology)
   - fitting: _not stated_
   - validation: _not stated_
5. **Spatial distribution of multiples versus simulations**: dN/dA vs separation from centroid; compared with random placement and two mock catalogs  
  > "The simulated datasets consist of 200 runs of DSFGs with the same flux density and multiplicity as the observed datasets" (4.3 Spatial Distribution of Multiple Sources)
   - fitting: _not stated_
   - validation: Degraded ALMA data to ALESS resolution to test excess persistence  
  > "This excess persists (although at significantly lower amplitude) even when the quality of our ALMA observations are degraded" (4.3 Spatial Distribution of Multiple Sources)
6. **Test intrinsic number counts via magnification statistics**: Predict <mu870> and P(mu>mu_min) for ALESS and COSMOS broken power-law counts; compare with data via logistic regression  
  > "Instead of computing a running average of the data, we show a logistic regression fit to the data (cite: scikitlearn)." (5.2 Comparing Models with Data)
   - software: Scipy, scikit-learn
   - parameter: z_mu=1.5, sigma_z=0.2; SIS+NFW lenses  
  > "where $a_z = 1 + z$, $z_\mu = 1.5$ (to reflect the relatively blue SPIRE colors of the sample), and $\sigma_z = 0.2$." (5.1 Statistical Predictions)
   - assumption: flat cosmology H0=69, Om=0.29  
  > "we assume a flat cosmology with $H_0=$69 km s$^{-1}$ Mpc$^{-1}$, $\Omega_{\rm m_0} = 0.29$" (1 Introduction)
   - fitting: logistic regression  
  > "Instead of computing a running average of the data, we show a logistic regression fit to the data" (4.2 Comparing Models with Data)
   - validation: _not stated_

## Software

- **CASA** 4.2.1: data re-reduction, selfcal, imaging  
  > "(CASA, version 4.2.1)" (2.2 ALMA Observations)
- **uvmcmcfit** : MCMC visibility-plane lens modeling  
  > "We created and made publicly available custom software, called uvmcmcfit" (3.1 Model Fitting Methodology)
- **emcee** : posterior sampling  
  > "We use emcee (cite: Foreman-Mackey:2013yq) to sample the posterior probability density function (PDF)" (3.1 Model Fitting Methodology)
- **Gravlens** : used in earlier works for ray tracing; replaced here  
  > "we used the publicly available Gravlens software (cite: Keeton:2001lr)" (3.1 Model Fitting Methodology)
- **MIRIAD** : uvmodel routine ported to Python  
  > "the code used in uvmcmcfit is a direct Python port of uvmodel" (3.1 Model Fitting Methodology)
- **IRAF Gemini GMOS** : Gemini optical reduction  
  > "The data were reduced using the standard IRAF Gemini GMOS reduction routines" (2.3 Gemini-South Imaging)
- **Scipy** : griddata and gaussian_filter for running average  
  > "using the Scipy griddata package and then smoothing the resulting grid using a Gaussian filter" (5.2 Comparing Models with Data)
- **scikit-learn** : logistic regression  
  > "we show a logistic regression fit to the data (cite: scikitlearn)" (5.2 Comparing Models with Data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of ALMA sources above 5 sigma | 62 | not stated | sources | 2 | We identify 62 sources down to the $5\sigma$ point-source sensitivity limit in our ALMA sample |
| Sources with mu870>1.1 | 36 of 62 | not stated | sources | 4 | 36 experience significant amplification ($\mu>1.1$) |
| Multiplicity rate | 20/29 (69%) | not stated | percent | 4 | We find that 20/29 *Herschel* DSFGs break down into multiple ALMA sources, implying a multiplicity rate of 69%. |
| Median S870 drop due to lensing | 1.6 | KS p=0.044 | dimensionless | 4 | the median flux density in the *Herschel*-ALMA sample drops by a factor of 1.6 when lensing is taken into account |
| Brightest intrinsic source S870 (HADFS11.0) | 17.5 | 0.4 | mJy | 3 | with an intrinsic flux density of $S_{870} = 17.5 \pm 0.4\,$mJy |
| Median mu870 of lensed subset | 1.6 | not stated | dimensionless | 4 | The median amplification in the subset that experiences lensing is $\mu_{870} =
            1.6$. |
| dN/dA excess at 0.5 arcsec | ~10 | not stated | dimensionless | 5 | we find an excess in $dN/dA$ by a factor of $\approx
10$ compared to a random, uniformly distributed population |
| Transition flux S_trans from data | 24 | 3 | mJy | 6 | the logistic regression fit yields $S_{\rm trans} = 24\pm3\,$mJy |
| S_trans for ALESS and COSMOS counts | 37 and 69 | not stated | mJy | 6 | the models based on the ALESS and COSMOS number counts yield $S_{\rm trans} = 37\,$mJy $S_{\rm trans} = 69\,$mJy, respectively |

## Qualitative findings

- Multiple ALMA counterparts are located much closer together than predicted by simulations or seen in ALESS.  
  > "Our ALMA sources are located significantly closer to each other than expected based on results from theoretical models" (abstract)

## Claim tuples

- H: Do bright Herschel DSFGs break into multiple ALMA sources at a high rate? | E: Count ALMA components per Herschel source at 0.45 arcsec resolution | R: 20/29 multiple (69%); 80% excluding strongly lensed singles | F: Brighter sources have higher multiplicity than ALESS | **supported**
- H: Are multiples closer together than random or simulated populations? | E: dN/dA vs separation compared with random placement and two mock catalogs | R: Excess ~10x at 0.5 arcsec; models under-predict small separations | F: Favors interactions/mergers, though blending not excluded | **partially**
- H: Which intrinsic number counts match measured magnifications? | E: Compare P(mu>2) vs S870 for ALESS and COSMOS broken power-laws with data | R: ALESS counts (steep fall off above 8 mJy) match better | F: Tentatively favors steep fall off above 8 mJy | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Visibility-plane fitting avoids correlated pixel errors in cleaned images  
  > "The best way to deal with this situation is to compare model and data visibilities rather than surface brightness maps." (3.1 Model Fitting Methodology)
- Alternative: Alternative HXMM30 model with sub-mm luminous lens deemed unlikely  
  > "An alternative model in which the lens is sub-mm luminous cannot be ruled out, but we consider this unlikely for a number of reasons." (3.2 Individual Model Fits)
- How they decided it was enough: _not stated_
- Limitation (authors): Resolution may cause over-predicted sizes and under-predicted magnifications; optically faint lenses may be missed  
  > "in some cases the lens models may moderately over-predict the intrinsic sizes of the lensed galaxies and hence under-predict the magnification factors" (3.1 Model Fitting Methodology)
- Caveat (inferred, ours): Many weakly lensed magnifications are maximal-lensing upper limits with fixed Einstein radii
- Caveat (inferred, ours): Sample biased toward blends; selection not flux-limited in a clean way
- Caveat (inferred, ours): Final MCMC phase of 10 iterations is short for uncertainty estimation
- Caveat (inferred, ours): Number-count test relies on small sample and fixed lens/redshift model

## Reproducibility

- Data public (paper): ALMA data cited by project code; uvmcmcfit public on GitHub  
  > "using uvmcmcfit, a publicly available [^1] modified version of the visibility plane lens modeling software" (Introduction)
- Products in archive: _not stated_
- Code: uvmcmcfit at https://github.com/sbussmann/uvmcmcfit  
  > "<https://github.com/sbussmann/uvmcmcfit>" (Footnote 1)
- Missing: SMA magnification data for combined sample
- Missing: Mock catalogs from simulation papers
- Missing: Gemini/HST/Keck ancillary images
- Missing: Clean parameters like cell size, thresholds
- Data volume (inferred): ~50-150 GB raw for 29 Cycle 0 targets; tens of GB after splitting
- Score (inferred): 3/5, Public ALMA data and public code, but several imaging/fitting details and external SMA and simulation inputs are missing.
- Rediscovery candidate: no, Requires external SMA data, ancillary imaging and simulation catalogs; many lens model choices are per-object manual.

## Links

- Method: (cite: Bussmann:2012lr; Bussmann:2013lr) (original visibility-plane lens modeling approach)
- Method: (cite: Foreman-Mackey:2013yq) (emcee sampler)
- Companion: (cite: Wardlow:2013lr) (Herschel lens candidate selection overlapping sample)
- Companion: (cite: Calanog:2014lr) (HST/Keck imaging of lenses)
- Companion: (cite: Hodge:2013qy) (ALESS comparison sample)
- Related: HerMES
- Related: H-ATLAS
- Related: ALESS
- Related: LESS

## Checks

```json
{
 "quotes": 74,
 "quotes_ok": 74,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 89,
  "stated": 60,
  "rate": 0.674
 },
 "evidence_ok": true
}
```
