# Dust-depleted Inner Disks in a Large Sample of Transition Disks through Long-baseline ALMA Observations

`2020ApJ...892..111F` | The Astrophysical Journal 2020 | first author: Francis, Logan | arXiv: 2003.00079 | DOI: 10.3847/1538-4357/ab7b63

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks
- Question: Do transition disk cavities host inner mm-dust disks, and what are their sizes, dust masses, orientations and depletion relative to the outer disk?  
  > "We present a high resolution continuum study of inner disks in the cavities of 38 transition disks." (abstract)
- Target **38 transition disks (e.g. PDS 70, WSB 60, DM Tau, GG Tau A, MWC 758)**: coordinates Inner-disk RA/Dec for 18 detected disks in the Appendix table (e.g. PDS70 14:08:10.107 -41:23:52.995)  
  > "Most targets are located within 200 pc with the exception of V1247 Ori and HD 34282, at 400 and 312 pc distance, respectively." (2.1 Sample selection); "We have taken the new distances from Gaia DR2 (cite: Gaia2018)" (2.3 Stellar properties); z/distance most within 200 pc; V1247 Ori 400 pc; HD 34282 312 pc; TW Hya 60 pc  
  > "Most targets are located within 200 pc with the exception of V1247 Ori and HD 34282, at 400 and 312 pc distance, respectively." (2.1 Sample selection); "We have taken the new distances from Gaia DR2 (cite: Gaia2018)" (2.3 Stellar properties); distance from Gaia DR2  
  > "Most targets are located within 200 pc with the exception of V1247 Ori and HD 34282, at 400 and 312 pc distance, respectively." (2.1 Sample selection); "We have taken the new distances from Gaia DR2 (cite: Gaia2018)" (2.3 Stellar properties)

## Data provenance

- ALMA projects: 2013.1.01070.S, 2015.1.00889.S, 2017.A.00006.S, 2012.1.00303.S
- bands: Band 6, Band 7, and Band 3 (for HD135344B, T Cha, SR21, SR24S)  
  > "For the majority of disks, Band 6 (1.3 mm or 230 GHz) or Band 7 (0.87 mm or 345 GHz) data at high resolution is available" (2.1 Sample selection)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: typically 0.05-0.1'' or 7-15 au  
  > "typically $0.05-0.1\ensuremath{''}$ or $7-15$ au resolution" (Introduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: archival data; about half already published  
  > "About half of our datasets have been published already; references are provided in the same table." (2.1 Sample selection)
- Other facility **Gaia DR2**: distances  
  > "We have taken the new distances from Gaia DR2 (cite: Gaia2018)" (2.3 Stellar properties)
- Other facility **2MASS, WISE, Spitzer-IRAC, BVRI surveys**: SED photometry  
  > "Photometric data was taken from *BVRI* surveys, *2MASS* (JHK), *WISE* and *Spitzer-IRAC*." (2.3 Stellar properties)
- External data: Spectral types and accretion rates from literature  
  > "For all targets in our sample spectral types and accretion rates are taken from the literature." (2.3 Stellar properties) [from references in Stellar Properties table]
- External data: Outer-disk inclination and position angle from literature where available  
  > "taken from the literature where available (references in Table [\[tab:disk_sample\]](#tab:disk_sample))" (3.3 Disk surface density profiles) [from refs in sample table]
- External data: TW Hya reduced image  
  > "except TW Hya, for which the reduced image from (cite: Andrews2016) was used." (2.2 ALMA data reduction) [from (cite: Andrews2016)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline scripts provided with archive data  
  > "All data were calibrated using the ALMA pipeline reduction scripts provided with the raw data from the ALMA archive" (2.2 ALMA data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean in CASA 5.5.0  
  > "Images of each target were created using the `tclean` task in version 5.5.0 of the Common Astronomy Software Applications (CASA) package." (2.2 ALMA data reduction)
- deconvolver: _not stated_
- weighting robust: robust 2.0, 0.5 or -2.0 chosen per disk to maximize inner-disk S/N; TW Hya 0.0  
  > "we individually selected the weighting for each image that maximized the S/N of the inner disk." (2.2 ALMA data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: long baselines combined with compact-configuration data from other projects where needed  
  > "Where necessary, long baseline observations were combined with more compact configuration ALMA data from other projects" (2.2 ALMA data reduction)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Opacity kappa=10 cm2/g at 1000 GHz with beta=1  
  > "where we take $\kappa_{\nu}$ as 10 cm$^2$ g$^{-1}$ at 1000 GHz and use an opacity power-law index of $\beta$ = 1.0 (cite: Beckwith1991)" (3.2) [from (cite: Beckwith1991)]
- NIR excess definition  
  > "we compute the percentage near-infrared (NIR) following the definition from (cite: Pascual2016)" (2.4 NIR excess) [from (cite: Pascual2016)]
- PTD/TD classification by K-band excess  
  > "using the K-band (2.2 $\mu$m) excess of the SED over the stellar photosphere (cite: Espaillat2007)" (2.4 NIR excess) [from (cite: Espaillat2007)]
- Luminosity-flux scaling in size-luminosity relation  
  > "scaled to a distance of 140 pc and a frequency of 340 GHz for a spectral index $\alpha_{mm}$=2.5 (similar to (cite: Andrews2018size))" (4.4) [from (cite: Andrews2018size)]

### Not stated but needed to reproduce (our reading)

- Line-free channels / continuum bandwidth and spectral windows used for each continuum image
- Image size, cell size, masking and clean threshold
- Which specific execution blocks and configurations were combined per target
- Self-calibration, if any
- How the inner-disk inclination/PA and errors were derived from imfit
- Pipeline version and flux calibrator uncertainty
- Outer-disk fluxes' aperture centers and uncertainties; inner disk mass uncertainty propagation
- Literature outer-disk inclinations/PAs used per target

## Analysis recipe

1. **Image archival continuum data**: tclean with robust 2.0, 0.5 or -2.0 chosen to maximize inner-disk S/N  
  > "we individually selected the weighting for each image that maximized the S/N of the inner disk." (2.2 ALMA data reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: verified each project contained sufficient short baselines to recover the largest scales  
  > "we verified that each ALMA project contained sufficient short baselines to recover the largest scales in the disk." (2.2 ALMA data reduction)
2. **Detect and fit inner disk**: Detection above 3x RMS at stellar location; Gaussian fit with imfit; otherwise 3 RMS upper limit; R_inner = HWHM or largest ellipse fitting in beam if unresolved  
  > "A detection is defined as the measurement of a flux at the stellar location above a threshold of 3 times the RMS image noise level." (3.1)
   - software: CASA imfit
   - assumption: Unresolved inner disks have same inclination and PA as outer disk  
  > "where unresolved, we assume the inner disk has the same inclination and position angle as the outer disk" (3.1)
   - fitting: Gaussian model  
  > "For each of the 18 detections, a Gaussian model is fit using the CASA `imfit` task." (3.1 Inner disk detection and modelling)
   - validation: _not stated_
3. **Derive inner disk dust mass**: Optically thin Rayleigh-Jeans flux with passively heated flared disk T(r), Sigma_d propto 1/r, between R_sub and R_inner  
  > "This means that the mm-dust mass can computed accurately with the optically thin assumption." (3.2)
   - parameter: flaring angle 0.02; R_sub=0.07 sqrt(L*) au; kappa 10 cm2/g at 1000 GHz, beta=1; assumed R_inner=5 au for unresolved  
  > "with $\sigma_B$ the Stefan-Boltzmann constant, $\phi$ the flaring angle (taken as 0.02) and $L_*$ the stellar luminosity." (3.2)
   - assumption: Scattering and free-free emission ignored  
  > "in this approach using the blackbody approximation we ignore scattering, which might result in an underestimate of the inner disk dust mass" (3.2)
   - fitting: _not stated_
   - validation: Optical depth checked against expected thick/thin flux vs L*  
  > "First, we check the optical depth by estimating the expected flux based on basic radiative transfer calculations, given the stellar luminosity." (3.2)
4. **Build dust surface density profiles and delta_dust**: R_cav from azimuthally averaged profile; R_outer from curve-of-growth at 95% flux; delta_dust is inner/outer surface density ratio  
  > "successively larger photometric apertures are applied until the measured flux is 95% of the total flux" (3.3)
   - fitting: Gaussian ring chi2 fit for 7 outer disks lacking orientation  
  > "a $\chi^2$ minimization with steps of 0.005" in radial direction and 1$^{\circ}$ results in the best fit values" (Orientation outer disk)
   - validation: R_cav within 20% of literature values  
  > "Our derived values for $R_\text{cav}$ are generally within 20% of the literature values" (3.3)
5. **Correlation and regression tests**: Kelly (2007) linear regression with upper limits for NIR excess, accretion rate, size-luminosity  
  > "Using the linear regression procedure of (cite: Kelly2007), which takes into account upper limits and intrinsic scatter in the data" (4.2)
   - software: linmix (Kelly 2007)
   - fitting: Kelly 2007 Bayesian linear regression  
  > "Using the linear regression procedure of (cite: Kelly2007), which takes into account upper limits and intrinsic scatter in the data" (4.2 NIR vs millimeter emission)
   - validation: _not stated_
6. **Infer gas-to-dust ratio and alpha**: Viscous alpha-disk relation linking Sigma_g, accretion rate and T(r); solve xi_inner for alpha=1e-3 or alpha for xi=100  
  > "we use Equation [\[eqn:gdr\]](#eqn:gdr) to calculate $\xi_\text{inner}$ for a low $\alpha$=10$^{-3}$" (4.5 Gas content of the inner disks)
   - assumption: mu~2, vertically isothermal; 0.5 dex uncertainty on accretion rates  
  > "We assume an uncertainty of half a dex on the accretion rates." (2.3 Stellar properties)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.5.0: tclean imaging and imfit  
  > "using the `tclean` task in version 5.5.0 of the Common Astronomy Software Applications (CASA) package" (2.2 ALMA data reduction)
- **Python** 2.7: analysis  
  > "Python version 2.7, astropy (cite: astropy2013), and matplotlib (cite: matplotlib2007)." (Acknowledgements)
- **astropy** : analysis  
  > "Python version 2.7, astropy (cite: astropy2013), and matplotlib (cite: matplotlib2007)." (Acknowledgements)
- **matplotlib** : plotting  
  > "Python version 2.7, astropy (cite: astropy2013), and matplotlib (cite: matplotlib2007)." (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Inner disks detected | 18 of 38 | not stated | disks | 2 | We detect an inner disk in 18 of the 38 images. |
| Resolved inner disks | 14 | not stated | disks | 2 | Of the 18 detected inner disks, we are able to resolve 14 of them |
| Mean R_inner | ~5 | not stated | au | 2 | which has a mean value of $\sim$5 au. |
| Misaligned resolved disks | 8 of 14 | not stated | disks | 2 | In 8 of 14 resolved disks, a significant ($>2\sigma$ probability) misalignment in either position angle or inclination is found. |
| Median delta_dust | ~1e-2 | not stated | dimensionless | 4 | with a median of $\delta_\text{dust}\approx 10^{-2}$ |
| Correlation of dust mass with NIR excess | 0.30 | 0.18 | dimensionless | 5 | the correlation coefficient $r_\text{corr}=0.30 \pm 0.18$ |
| Size-luminosity fit slope B | 0.3 | 0.2 | dimensionless | 5 | with best-fit parameters $A= 1.2\pm0.6$ and $B=0.3\pm0.2$ |
| Gas-to-dust ratio for alpha=1e-3 | 1e4-1e5 | not stated | dimensionless | 6 | find gas-to-dust ratios of $10^4-10^5$ for the majority of the (detected) disks |

## Qualitative findings

- Inner mm-dust disks are depleted relative to outer disks, uncorrelated with accretion rate and NIR excess  
  > "The near-infrared excess is uncorrelated with the mm dust mass of the inner disk." (abstract)

## Claim tuples

- H: Inner disks in transition disk cavities are frequently misaligned | E: Compare inclination/PA of resolved inner and outer disks | R: 8 of 14 resolved disks significantly misaligned | F: Misaligned inner disks are common | **supported**
- H: NIR excess traces mm inner dust | E: Regression of dust mass vs NIR excess | R: r=0.30+-0.18 | F: NIR excess is not a reliable tracer | **supported**
- H: Inner disks follow the size-luminosity relation | E: Regression of R_inner vs L_mm | R: slope 0.3+-0.2 consistent with Andrews 2018 | F: Consistent with radial drift | **partially**
- H: PDS 70 inner disk differs because planets recently opened the gap | E: Compare R_inner and xi_inner | R: PDS 70 and WSB 60 have large inner disks and xi~100 | F: Hypothesis of recent gap opening | **partially**

## Reasoning

- Why this data: Archival data chosen to best resolve the dust cavity and inner disk  
  > "The archival ALMA data collected for each disk was chosen in order to best resolve the dust cavity and inner disk (if present)." (2.2 ALMA data reduction)
- Why this method: _not stated_
- Alternative: Free-free jet emission as alternative to inner dust disk, not ruled out  
  > "One other explanation for apparent misalignment of the inner disk in the millimeter is that we are not measuring inner disk dust emission, but free-free emission from a jet" (4.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Sensitivity non-uniform so occurrence is likely underestimated; sample biased toward large bright disks  
  > "As our sensitivity is extremely non-uniform across the sample, this is likely an underestimate of the occurrence rate of inner disks." (5 Conclusions)
- Caveat (inferred, ours): Blackbody optically thin mass with fixed phi=0.02 and kappa ignores scattering and uncertain temperatures
- Caveat (inferred, ours): Gas-to-dust inference relies on alpha-disk assumption and literature accretion rates with 0.5 dex error
- Caveat (inferred, ours): Heterogeneous images (weighting chosen to maximize inner disk S/N) bias detections
- Caveat (inferred, ours): Possible free-free contamination
- Caveat (inferred, ours): Inner disk size from Gaussian fits near beam size is uncertain

## Reproducibility

- Data public (paper): Archival ALMA data  
  > "Measurements of the dust mass from archival Atacama Large Millimeter/Submillimeter Array observations" (abstract)
- Products in archive: _not stated_
- Missing: Exact imaging parameters (cell, size, masks, channels)
- Missing: Execution blocks selection per target
- Missing: Literature outer-disk orientation values
- Missing: Code for mass and gas-to-dust calculation
- Data volume (inferred): Large: ~38 targets, ~38 ALMA projects, likely several hundred GB to a few TB raw
- Score (inferred): 3/5, Data public and equations given, but imaging details and many literature inputs are not specified.
- Rediscovery candidate: no, Heavy multi-project archival imaging with unstated settings and many literature inputs.

## Links

- Method: (cite: Kelly2007) (linear regression with upper limits)
- Method: (cite: Dullemond2001) (temperature profile and sublimation radius)
- Method: (cite: Pascual2016) (NIR excess definition)
- Companion: (cite: Andrews2018size) (size-luminosity relation comparison)
- Related: Gaia DR2

## Checks

```json
{
 "quotes": 65,
 "quotes_ok": 65,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2012.1.00303.S"
 ],
 "obscore_codes_not_in_card": [
  "2011.0.00399.S",
  "2012.1.00129.S",
  "2012.1.00158.S",
  "2012.1.00631.S",
  "2012.1.00761.S",
  "2013.1.00100.S",
  "2013.1.00198.S",
  "2013.1.00498.S",
  "2015.1.00192.S",
  "2015.1.00224.S",
  "2015.1.00678.S",
  "2015.1.00686.S",
  "2015.1.00888.S",
  "2015.1.00979.S",
  "2015.1.00986.S",
  "2015.1.01083.S",
  "2015.1.01207.S",
  "2015.1.01301.S",
  "2016.1.00344.S",
  "2016.1.00629.S",
  "2016.1.00826.S",
  "2016.1.01042.S",
  "2016.1.01164.S",
  "2016.1.01205.S",
  "2016.A.00026.S",
  "2017.1.00449.S",
  "2017.1.00492.S",
  "2017.1.00884.S",
  "2017.1.00969.S",
  "2017.1.01151.S",
  "2017.1.01167.S",
  "2017.1.01404.S",
  "2017.1.01424.S",
  "2017.1.01460.S",
  "2017.1.01578.S"
 ],
 "codes_printed_but_missing": [
  "2011.1.00399.S",
  "2012.1.00129.S",
  "2012.1.00158.S",
  "2012.1.00631.S",
  "2012.1.00761.S",
  "2013.1.00100.S",
  "2013.1.00198.S",
  "2013.1.00498.S",
  "2015.1.00192.S",
  "2015.1.00224.S",
  "2015.1.00678.S",
  "2015.1.00686.S",
  "2015.1.00888.S",
  "2015.1.00979.S",
  "2015.1.00986.S",
  "2015.1.01083.S",
  "2015.1.01207.S",
  "2015.1.01301.S",
  "2016.1.00344.S",
  "2016.1.00629.S",
  "2016.1.00826.S",
  "2016.1.01042.S",
  "2016.1.01164.S",
  "2016.1.01205.S",
  "2016.A.00026.S",
  "2017.1.00449.S",
  "2017.1.00492.S",
  "2017.1.00884.S",
  "2017.1.00969.S",
  "2017.1.01151.S",
  "2017.1.01167.S",
  "2017.1.01404.S",
  "2017.1.01424.S",
  "2017.1.01460.S",
  "2017.1.01578.S"
 ],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 81,
  "stated": 45,
  "rate": 0.556
 },
 "evidence_ok": true
}
```
