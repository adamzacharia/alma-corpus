# SEDEBLEND: a new method for deblending spectral energy distributions in confused imaging

`2016MNRAS.463...10M` | Monthly Notices of the Royal Astronomical Society 2016 | first author: MacKenzie, Todd P. | arXiv: 1512.04615 | DOI: 10.1093/mnras/stw1890

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies
- Question: Can source deblending and SED fitting be combined in one forward-modelling MCMC to derive far-IR luminosities and dust temperatures of ALESS submm galaxies from confused Herschel imaging plus ALMA fluxes?  
  > "by combining source deblending and SED fitting into the same procedure. We call this method “SEDeblend.”" (abstract)
- Target **ALESS (ALMA follow-up of LESS) submm galaxies in ECDFS**: coordinates _not stated_; z/distance photometric redshifts (Table 1)  
  > "We apply our method to the Atacama Large Millimeter/submillimeter Array (ALMA) Survey of Submillimetre Galaxies (cite: alma) in the Extended Chandra Deep Field South (ECDFS)" (1 Introduction); distance from Simpson et al. 2014 (cite: simpson)  
  > "We apply our method to the Atacama Large Millimeter/submillimeter Array (ALMA) Survey of Submillimetre Galaxies (cite: alma) in the Extended Chandra Deep Field South (ECDFS)" (1 Introduction)

## Data provenance

- ALMA projects: 2011.0.00294.S
- bands: Band 7 (345 GHz, 870 um); Band 9 only simulated  
  > "The data used in this study are at 345 GHz in ALMA Band 7" (2.3 Model fitting)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **Herschel SPIRE**: 250, 350, 500 um confused imaging  
  > "Fig. [1](#subtraction) shows the ECDFS field at the three *Herschel*-SPIRE wavelengths" (2.2 Herschel-SPIRE sky residuals)
- Other facility **Herschel PACS**: 160 um imaging  
  > "Because the 160 $\mu$m PACS data are dominated by instrumental noise" (2.3 Model fitting)
- Other facility **Spitzer MIPS 24um and VLA**: positional prior catalogue (NMJS)  
  > "the catalogue of nearby Multiband Imaging Photometer for Spitzer (MIPS) 24 $\mu$m and Very Large Array (VLA) sources provided in (cite: swinbank)" (2.2 Herschel-SPIRE sky residuals)
- External data: ALESS 870 um fluxes and positions  
  > "we use the ALMA 870 $\mu$m fluxes and positions from (cite: alma)" (4 ALESS properties) [from Hodge et al. 2013 (cite: alma)]
- External data: photometric redshifts used as Gaussian priors  
  > "The photometric redshift constraints are considered to be $\pm1\,\sigma$ Gaussian priors in our model." (4 ALESS properties) [from Simpson et al. 2014 (cite: simpson)]
- External data: NMJS catalogue of 24um and VLA sources  
  > "henceforth referred to as the NMJS catalogue" (2.2 Herschel-SPIRE sky residuals) [from Swinbank et al. 2014 (cite: swinbank)]
- External data: Symeonidis sample catalogue of luminosities and dust temperatures  
  > "We obtained the catalogue of sources used to create the estimate of the $L$–$T_\mathrm{d}$ relation of (cite: symeonidis)" (4.2) [from Symeonidis et al. 2013 (cite: symeonidis)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ALMA 10% (Band 7), 20% (Band 9); PACS 5%; SPIRE 4% correlated + 1.5% uncorrelated  
  > "Calibration uncertainties are 10% and 20% in Bands 7 and 9, respectively." (2.3 Model fitting)
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
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Forward-modelling MCMC method and modified blackbody SED with power-law  
  > "We adopt a modified blackbody SED with a power-law component for the shorter wavelengths, as in M14." (2.1) [from MacKenzie et al. 2014 (cite: Mackenzie2014)]
- Duplicate NMJS source rejection within 1.5 arcsec  
  > "As in (cite: swinbank), we treat any source in the NMJS catalogue as a duplicate if it is within 1.5 arcseconds of an ALESS source or another NMJS source." (4) [from (cite: swinbank)]

### Not stated but needed to reproduce (our reading)

- MCMC chain length, convergence criteria and proposal settings
- Priors on luminosity normalisation and background
- Exact SED model parameterisation (power-law component details)
- Region sizes used for likelihood radius
- Details of SPIRE/PACS map versions and pixel preparation
- Detection limit used per source for selection test

## Analysis recipe

1. **Build SPIRE residual maps**: Maximum-likelihood fit of model SEDs to all NMJS and ALESS sources, equal pixel weights, then subtract  
  > "we use the ECDFS SPIRE residuals, after subtracting our model SED, fit to every NMJS and ALESS source simultaneously." (2.2)
   - parameter: Region with 250 um instrumental noise < 1.2 mJy, 4024 sources  
  > "We limit this process to the region where the 250 $\mu$m instrumental noise is less than 1.2 mJy, which includes 4024 sources" (2.2)
   - fitting: _not stated_
   - validation: Stacking on real and model sky gave consistent results  
  > "Because the stacking on the real and model sky give consistent results, we conclude that we are not significantly over-subtracting flux density from our maps." (2.2)
2. **Estimate sky covariance**: Inverse covariance from random 10x10 pixel cutouts of residuals; median per angular separation, polynomial for cross-band  
  > "We can estimate the covariance for an image of $10\times10$ pixels at each of the three SPIRE channels by selecting randomly chosen cutouts from the residuals" (2.3)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit SEDs and deblend simultaneously**: MCMC Metropolis-Hastings with Gibbs sampling, SPIRE correlated likelihood, PACS and ALMA Gaussian likelihoods  
  > "the model is fit to the data using an MCMC Metropolis-Hastings algorithm (cite: mcmc1; mcmc2) with Gibbs sampling (cite: gibbs)." (2.3)
   - parameter: beta fixed at 1.5; Td hard prior 10-100 K; LFIR integrated 8-1000 um  
  > "we simply fix it to a nominal value of 1.5" (4); "Far-IR luminosities are calculated by integrating the model SED from 8 to 1000 $\mu$m." (4)
   - assumption: Photometric redshift as +/-1 sigma Gaussian priors; Planck cosmology  
  > "The photometric redshift constraints are considered to be $\pm1\,\sigma$ Gaussian priors in our model." (4)
   - fitting: Likelihoods as given in Eqs 2-5; reports medians and 68% credible intervals  
  > "We provide the median values of our MCMC chains and report 68 percent credible intervals throughout." (4)
   - validation: Monte Carlo injection of 441 fake sources into residual maps  
  > "We inject a total of 441 fake sources for each case we test below." (3.1)
4. **Test temperature evolution with selection effects**: Bootstrap Symeonidis sample, assign ALESS redshifts, apply 3.5 sigma ALMA 870 um limit, compute mean Td for L=1e12-1e13  
  > "We retain those sources that have a predicted flux density greater than the 3.5 $\sigma$ ALMA flux limit at 870 $\mu$m and calculate the mean dust temperature of this sample of sources." (4.2)
   - fitting: _not stated_
   - validation: _not stated_

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mean Td of ALESS sample, full | 33.9 | 2.4 | K | 3 | For the full sample, we find an average dust temperature of (33.9$\pm$2.4) K. |
| Mean Td, selection-biased Symeonidis sample (L 1e12-1e13) | 35.6 | 0.8 | K | 4 | We find a mean dust temperature of (35.6$\pm$0.8) K. |
| Mean Td, ALESS sample (L 1e12-1e13) | 33.7 | 4.2 | K | 4 | we find a mean dust temperature of (33.7$\pm$4.2) K for the ALESS sample |
| Td offset vs Swinbank et al. | ~4 (warmer here) | not stated | K | 3 | An apparent systematic shift towards warmer dust temperatures is seen for our results, with an amplitude around 4 K |
| SPIRE residual standard deviations (250/350/500) | 1.5, 1.6, 1.4 | not stated | mJy | 1 | The standard deviations of the residuals are 1.5, 1.6 and 1.4 mJy at 250 $\mu$m, 350 $\mu$m and 500 $\mu$m, respectively |

## Qualitative findings

- Source degeneracies with neighbours dominate parameter uncertainties; a second ALMA band helps most when the SED peak is straddled  
  > "degeneracies between the two sources are nearly eliminated when adding a second ALMA band." (3.2)

## Claim tuples

- H: The method yields correct uncertainties | E: Injected 441 simulated sources | R: Good agreement with expected uncertainties | F: Method validated | **supported**
- H: Average dust temperature evolves with redshift | E: Compared ALESS to selection-matched Symeonidis sample | R: 35.6±0.8 K vs 33.7±4.2 K | F: No evidence of evolution | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Free beta over 1-2.5 rejected since data lack constraining power  
  > "We found that our data have almost no constraining power on the dust emissivity index, $\beta$" (4)
- How they decided it was enough: _not stated_
- Limitation (authors): SED model lacks a hot short-wavelength component and shorter/longer wavelength data  
  > "primarily the lack of a shorter wavelength hot component to our SED model" (4.1)
- Caveat (inferred, ours): Fixed beta=1.5 drives temperature offsets
- Caveat (inferred, ours): Only point-source Gaussian beams assumed
- Caveat (inferred, ours): Redshift priors from photometric estimates dominate some results

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Code not released
- Missing: MCMC settings
- Missing: Herschel map versions
- Data volume (inferred): small (<10 GB; ALMA catalogue fluxes plus Herschel maps)
- Score (inferred): 3/5, Method and priors described, but MCMC details and code absent; uses published catalogues.
- Rediscovery candidate: no, Recipe incomplete and code unavailable; ALMA data enter only as catalogue fluxes.

## Links

- Method: MacKenzie et al. 2014 (cite: Mackenzie2014) (original forward-modelling method)
- Companion: Swinbank et al. 2014 (cite: swinbank) (comparison two-step ALESS SED analysis)
- Companion: Hodge et al. 2013 (cite: alma) (ALESS ALMA catalogue)
- Related: ALESS
- Related: LESS
- Related: HerMES

## Checks

```json
{
 "quotes": 37,
 "quotes_ok": 37,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 27,
  "rate": 0.386
 },
 "evidence_ok": true
}
```
