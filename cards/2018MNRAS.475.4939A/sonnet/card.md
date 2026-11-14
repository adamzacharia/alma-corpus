# ALMA observations of lensed Herschel sources: testing the dark matter halo paradigm

`2018MNRAS.475.4939A` | Monthly Notices of the Royal Astronomical Society 2018 | first author: Amvrosiadis, A. | arXiv: 1801.07282 | DOI: 10.1093/mnras/sty138

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies, cosmology
- Question: Can the standard dark-matter halo paradigm, with halo mass functions and density profiles from simulations including baryons, reproduce the observed distribution of image separations of Herschel-selected lensed submillimetre galaxies?  
  > "We attempted to reproduce the distribution of image separations for the lensed sources using a halo mass function taken from a numerical simulation which contains both dark matter and baryons." (abstract)
- Target **16 lensed Herschel sources from H-ATLAS and HeLMS (e.g. HATLAS J083344.9+000109, HeLMS J001615.8+032435)**: coordinates _not stated_; z/distance spectroscopic redshifts >1 (values in table, not reproduced)  
  > "we selected 42 sources from the H-ATLAS and HELMS surveys with the highest 500-$\mu$m flux densities and with spectroscopic redshifts $>1$." (2 The Pilot Sample and the ALMA Observations); distance from literature references listed in table notes (C11, B13, C14, N16, MN17, M17)  
  > "we selected 42 sources from the H-ATLAS and HELMS surveys with the highest 500-$\mu$m flux densities and with spectroscopic redshifts $>1$." (2 The Pilot Sample and the ALMA Observations)

## Data provenance

- ALMA projects: _none stated_
- bands: 873 um  
  > "We observed each source for approximately 2-4 minutes with ALMA at 873 $\mu$m with a maximum baseline of 1km, which gives an angular resolution of 0.12 arcsec." (2 The Pilot Sample and the ALMA Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: maximum baseline 1 km  
  > "with a maximum baseline of 1km, which gives an angular resolution of 0.12 arcsec." (2 The Pilot Sample and the ALMA Observations)
- angular resolution: 0.12 arcsec  
  > "with a maximum baseline of 1km, which gives an angular resolution of 0.12 arcsec." (2 The Pilot Sample and the ALMA Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: approximately 2-4 minutes per source  
  > "We observed each source for approximately 2-4 minutes with ALMA at 873 $\mu$m" (2 The Pilot Sample and the ALMA Observations)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **SMA**: 880 um observations of 30 lens candidates (Bussmann et al. 2013) used as a comparison sample  
  > "Bussmann et al. (2013; B13) presented Sub-Millimeter Array (SMA) 880 $\mu$m observations of a sample of 30 candidates strong gravitational lenses" (1 Introduction)
- Other facility **Herschel (H-ATLAS, HeLMS)**: 500 um selection of lensed candidates  
  > "we selected 42 sources from the H-ATLAS and HELMS surveys with the highest 500-$\mu$m flux densities" (2 The Pilot Sample and the ALMA Observations)
- External data: SMA Einstein radii and image separations for the comparison sample  
  > "For three sources (H-ATLAS J083051.0+013225, H-ATLAS J085358.9+015537, H-ATLAS J142413.9+022303) there are also measurements of the Einstein radius from SMA observations" (2 The Pilot Sample and the ALMA Observations) [from Bussmann et al. 2013 (cite: Bussmann2013)]
- External data: EAGLE halo density profile parameters from Table 2  
  > "are determined by fitting 3rd-order polynomials to the values found in Table 2 of Schaller et al. 2015a." (3.1 The Halo Density Profiles) [from Schaller et al. 2015a (cite: Schaller2015a)]
- External data: Halo mass function parameters for the Hydro simulation  
  > "The best fit values of these parameters are obtained from Table 2 of Bocquet et al. (2016) for the Hydro simulation." (3.2 Halo Mass Function) [from Bocquet et al. (2016) (cite: Bocquet2016)]
- Simulation/model as data: EAGLE halo density profiles and Bocquet et al. (2016) hydrodynamical halo mass function  
  > "we use the analytic function for the halo mass function that was derived by Bocquet et al. (2016) by fitting to the results of a numerical simulation that contains both baryons and dark matter" (3.2 Halo Mass Function)

## Processing

### Calibration

- pipeline or manual: standard ALMA pipeline  
  > "The final image products were produced by the standard ALMA pipeline." (2 The Pilot Sample and the ALMA Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
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
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Statistical formalism and SMA comparison sample from the previous study  
  > "In our previous paper (Eales 2015) we investigated whether the standard dark-matter halo paradigm could explain the distribution of Einstein radii measured from the SMA observations." (1 Introduction) [from Eales 2015 (cite: Eales2015)]
- Detailed lensing models, with which Einstein radii were checked  
  > "Modelling of the submillimetre emission, by constructing detailed lensing models, will be presented in two upcoming papers (Dye et al. in preparation; Negrello et al. in preparation)." (2 The Pilot Sample and the ALMA Observations) [from Dye et al. in prep.; Negrello et al. in prep.]

### Not stated but needed to reproduce (our reading)

- ALMA project codes and execution details
- CASA/pipeline version
- Imaging parameters (weighting, cell size, rms, beam)
- Einstein radius table values per source
- Binning of observed image-separation histogram
- Integration grids and numerical settings for the lens statistics code
- Code for lens statistics not released

## Analysis recipe

1. **Measure Einstein radii from ALMA images**: Einstein radii measured directly from images; for arcs a circle was fitted to emission peaks >4 sigma with uniform weighting; checked against preliminary lens models  
  > "In cases where only an arc is visible (e.g HeLMS J001615.8+032435) a rough estimate of the Einstein radius was performed by fitting a circle to the peaks of the emission $( > 4\sigma)$." (2 The Pilot Sample and the ALMA Observations)
   - fitting: _not stated_
   - validation: Compared with preliminary lens models, agreement confirmed  
  > "The Einstein radii were measured directly from the images and subsequently compared with the respective values that arise from preliminary lensing models of these system, whereupon an agreement was confirmed." (2 The Pilot Sample and the ALMA Observations)
2. **Predict image-separation distributions**: Strong-lens statistics: halo mass function times volume element times cross-section for mu>=2, normalised; EAGLE, SIS and SISSA profiles with NFW outside transition masses  
  > "We adopt the standard formalism for computing lensing statistics (cite: TurnerOstrikerGott1984), where we consider a population of dark-matter halos that act as deflectors" (3.4 Formalism of Strong Lens Statistics)
   - parameter: minimum magnification mu_min = 2  
  > "We calculated the cross section using a minimum magnification factor of $\mu_{min} = 2$." (3.3 Cross-Section)
   - parameter: halo-to-stellar mass ratio 30 for SISSA; z_lv = z_l or 2.5  
  > "adopt a constant ratio of halo to stellar mass of 30" (3.1 The Halo Density Profiles)
   - assumption: Spherically symmetric lenses; flat LCDM with Omega_m=0.307, h=0.693  
  > "We always assume that the lens is spherically symmetric, since ellipticity does not significantly affect the statistics of image separations" (3.3 Lensing Properties)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit transition masses to observed distribution**: chi^2 minimisation against normalised observed histogram with Poisson errors; 100 Gaussian resamplings of measured separations for uncertainties  
  > "we perform 100 simulations for each measurement by resampling each value at random from a Gaussian distribution with a standard deviation equal the value’s error." (4.1 Comparison with Observations)
   - assumption: Source J141351.9-000026 excluded  
  > "In our analysis we decided to exclude the object J141351.9-000026" (4.1 Comparison with Observations)
   - fitting: chi^2 minimisation  
  > "by performing a standard $\chi^2$ minimisation method" (4.1 Comparison with Observations)
   - validation: _not stated_

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| log M_max (SIS), ALMA, z_vir=z_l | 13.25 | 0.10 | log10(Msun) | 3 | 13.25 $\pm$ 0.10 |
| log M_max (SISSA), ALMA, z_vir=z_l | 13.20 | 0.11 | log10(Msun) | 3 | 13.20 $\pm$ 0.11 |
| log M_max (SIS), ALMA, z_vir=2.5 | 12.56 | 0.13 | log10(Msun) | 3 | 12.56 $\pm$ 0.13 |
| log M_max (SISSA), ALMA, z_vir=2.5 | 12.48 | 0.10 | log10(Msun) | 3 | 12.48 $\pm$ 0.10 |
| Sample size needed to distinguish density profiles | ~500 | not stated | lensed sources | 0 | we estimate that a sample of $\sim 500$ would be required for this distinction to be made possible. |

## Qualitative findings

- 15 of 16 ALMA-observed sources show clear lensing features  
  > "Out of these sources, 15 show clear evidence of lensing features." (5 Discussion & Conclusions)

## Claim tuples

- H: Simulation-based halo mass function and profiles reproduce the observed image-separation distribution | E: Compared predicted normalised distributions (EAGLE, SIS, SISSA) with ALMA and SMA samples | R: All three profiles agree with the observed distribution; SIS and SISSA need an upper transition mass ~1e13 Msun | F: Standard dark-matter halo paradigm is consistent with the data | **supported**
- H: Virialization redshift affects the transition masses | E: Fitted with z_lv = z_l and z_lv = 2.5 | R: M_max drops to log ~12.5 | F: No evidence supports such a low transition mass | **supported**

## Reasoning

- Why this data: ALMA has better resolution and surface-brightness sensitivity than SMA, so lensing arcs are not missed  
  > "ALMA has much better angular resolution and surface-brightness sensitivity than the SMA, making it a much better instrument for mapping a strongly-lensed submillimetre source." (2 The Pilot Sample and the ALMA Observations)
- Why this method: _not stated_
- Alternative: Oguri (2006b) two-component profile not used because the sample is too small to distinguish models  
  > "However, as our sample is still limited in numbers to make such distinctions between models, we have not considered this approach." (5 Discussion & Conclusions)
- How they decided it was enough: _not stated_
- Limitation (authors): Sample too small to distinguish density profiles; magnification bias not corrected  
  > "we have decided not to do this because the luminosity function for submm sources is still very poorly constrained" (3.3 Magnification Bias)
- Caveat (inferred, ours): Small sample of 15 lenses
- Caveat (inferred, ours): Einstein radii of arcs are rough estimates
- Caveat (inferred, ours): Spherical symmetry assumed
- Caveat (inferred, ours): Redshift selection may bias sample

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA project/MOUS identifiers in text
- Missing: Table of Einstein radii not reproduced in the text
- Missing: Lens statistics code not released
- Data volume (inferred): small, ~tens of GB (16 short continuum observations)
- Score (inferred): 3/5, ALMA role is limited to Einstein radius measurement; the theoretical calculation is described in equations but with no code and missing numerical details.
- Rediscovery candidate: no, Main results depend on a custom lens-statistics model and unstated ALMA data details.

## Links

- Companion: Eales 2015 (cite: Eales2015) (Previous SMA-based lens statistics study)
- Related: H-ATLAS
- Related: HerMES
- Related: HeLMS
- Related: EAGLE

## Checks

```json
{
 "quotes": 37,
 "quotes_ok": 37,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2013.1.00358.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 67,
  "stated": 29,
  "rate": 0.433
 },
 "evidence_ok": true
}
```
