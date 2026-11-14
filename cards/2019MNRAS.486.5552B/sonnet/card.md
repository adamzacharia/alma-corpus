# Sub-millimetre non-contaminated detection of the disc around TWA 7 by ALMA

`2019MNRAS.486.5552B` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Bayo, A. | arXiv: 1806.09252 | DOI: 10.1093/mnras/stz1133

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: debris_disks
- Question: Is the sub-mm emission near TWA 7 from its debris disk or a contaminant, and can the SED be explained by a single dust belt?  
  > "We show that most of the emission at wavelengths longer than $\sim 300$ $\mu$m is in fact arising from a contaminant source" (abstract)
- Target **TWA 7**: coordinates _not stated_; z/distance 34.029 ± 0.076 pc  
  > "one of the closest ($34.029 \pm 0.076$ pc, (cite: Gaia2018)) and youngest low-mass stars with a debris disk" (Introduction); distance from Gaia DR2 (Gaia2018)  
  > "one of the closest ($34.029 \pm 0.076$ pc, (cite: Gaia2018)) and youngest low-mass stars with a debris disk" (Introduction)

## Data provenance

- ALMA projects: 2015.1.01015.S
- bands: Band 7 (346 GHz)  
  > "in Band 7 (346 GHz), using two different configurations" (2.1 ALMA observations)
- frequencies and spectral setup: continuum SPWs 334.352, 336.242, 348.35 GHz; gas SPW 345.950 GHz  
  > "$334.352$, $336.242$, $348.35$" (Table 1)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: compact (2016-04-22, 42 antennas) and extended (2016-09-01 and 2016-09-15, 36 antennas)  
  > "Extended configuration - Pointed at $10$h$42$m$30.4$s $-33^{\circ}40^{\prime}16.7^{\prime\prime}$ - $36$ antennas" (Table 1)
- baselines: _not stated_
- angular resolution: 0.44" x 0.33" (compact); 0.11" x 0.09" (extended)  
  > "led to a smaller beam size of $0.11\ensuremath{''} \times 0.09\ensuremath{''}$" (2.1 ALMA observations)
- max recoverable scale: 3.908" (compact); 2.046" (extended)  
  > "3.908" (Table 1)
- sensitivity: rms 32 uJy/beam at image center (compact continuum)  
  > "At the center of the image, we measure a root mean square of $32$ $\mu$Jy.beam$^{-1}$." (2.1 ALMA observations)
- time on source: _not stated_
- observing dates: 2016-04-22, 2016-09-01, 2016-09-15  
  > "2016-09-15" (Table 1)
- pi or archival as stated: _not stated_
- Other facility **Herschel PACS/SPIRE**: far-IR fluxes for SED  
  > "Figure [3](#fig:jcmt) shows the *Herschel*/PACS observation at $100$ $\mu$m" (2.3)
- Other facility **JCMT SCUBA-2**: 850 um data, treated as non-detections in SED  
  > "we now treat the JCMT reported fluxes as non-detections" (3 Revised SED model)
- External data: Herschel/SPIRE fluxes  
  > "the *Herschel*/SPIRE observations published in (cite: Cieza2013)" (2.3) [from (cite: Cieza2013)]
- External data: Herschel PACS fluxes 77±7 and 42±9 mJy at 70 and 160 um  
  > "$77 \pm 7$ and $42 \pm 9$ mJy at $70$ and $160$ $\mu$m for (cite: Riviere-Marichalar2013)" (3 Revised SED model) [from (cite: Riviere-Marichalar2013)]
- External data: JCMT upper limits derived from reported uncertainties  
  > "the $3\sigma$ upper limits are estimated from the uncertainties reported by (cite: Matthews2007) and (cite: Holland2017)" (3 Revised SED model) [from (cite: Matthews2007); (cite: Holland2017)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10% flux calibration uncertainty  
  > "a $10$% flux calibration uncertainty added in quadrature" (2.4)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs weighting (robust not stated)  
  > "where Briggs weighting was selected by default in the CLEAN algorithm" (2.1 ALMA observations)
- uv taper: 2" u-v taper on combined compact+extended data  
  > "We then applied a $2\ensuremath{''}$ u-v taper to down-weight long baselines" (2.4)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: compact and extended configurations combined  
  > "First, we combined both the compact and extended configurations together" (2.4)
- smoothing: _not stated_
- final beam: ~3" with taper  
  > "likely marginally resolved at the $\sim 3\ensuremath{''}$ resolution attained with u-v tapering" (2.4)
- final rms: _not stated_

### Inherited from earlier work

- Stellar properties and SED modelling code  
  > "We refer the reader to (cite: Olofsson2018) for the description of the stellar properties and of the code used to model the SED." (3 Revised SED model) [from (cite: Olofsson2018)]
- Analysis of CO line  
  > "The analysis of the detected CO line is presented in (cite: Matra2019)." (2.1 ALMA observations) [from (cite: Matra2019)]

### Not stated but needed to reproduce (our reading)

- Briggs robust value
- Image size, cell size, clean threshold and masks
- Calibrators and calibration details
- Stellar parameters for the SED (in Olofsson2018)
- Epochs/number of points in the proper-motion fit and how the PUC data were reduced
- Which dataset (and pointing) went into the contaminant-subtracted image details

## Analysis recipe

1. **Image continuum and locate sources**: CASA Briggs-weighted continuum imaging, primary-beam corrected  
  > "Figure [1](#fig:alma) shows the continuum primary beam corrected image for the first dataset" (2.1 ALMA observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Check proper motion of TWA 7**: Linear fit of multi-epoch archival and new optical positions, excluding Herschel, JCMT and ALMA  
  > "The positions from Herschel, JCMT and ALMA were ignored in the final astrometric fitting process" (2.2)
   - assumption: parallax not fitted  
  > "we did not attempt to fit for parallax motion" (2.2)
   - fitting: _not stated_
   - validation: compared with Gaia DR2 proper motion  
  > "consistent with previous values available in the literature" (2.2)
3. **Recover disk emission with tapering**: Combine both configurations and apply a 2" u-v taper  
  > "We then applied a $2\ensuremath{''}$ u-v taper to down-weight long baselines" (2.4)
   - software: CASA
   - parameter: taper 2"  
  > "We then applied a $2\ensuremath{''}$ u-v taper" (2.4)
   - fitting: _not stated_
   - validation: _not stated_
4. **Subtract contaminant and measure disk flux**: Fit 2D Gaussian to contaminant in uv-plane, subtract, re-image with taper, integrate emission above 2 sigma  
  > "we model it as a 2D Gaussian in u-v space using the `uvmodelfit` task within CASA" (2.4)
   - software: CASA uvmodelfit
   - fitting: _not stated_
   - validation: confirm emission is not an imaging artifact of the nearby contaminant  
  > "To confirm that this extended emission component at the location of the star is not an artifact of imaging" (2.4)
5. **Single-belt SED modelling**: Fit SED with one belt, r0=25 au and alpha_in=5 fixed, free alpha_out, s_min, composition; dust mass from least-squares scaling  
  > "we fix its reference radius $r_0 = 25.0$ au" (3 Revised SED model)
   - software: emcee
   - parameter: p=-3.5, s_max=5 mm  
  > "with $p$ fixed to $-3.5$ following (cite: Dohnanyi1969), with fixed $s_{\mathrm{max}} = 5$ mm" (3 Revised SED model)
   - assumption: astro-silicates from Draine2003  
  > "we used the astro-silicates optical constant from (cite: Draine2003)" (3 Revised SED model)
   - fitting: emcee, 20 walkers, 1000 burn-in, 2000 step chain, uniform priors  
  > "with $20$ “walkers”, a burn-in phase of $1,000$ steps, and a final chain of $2,000$ steps" (3 Revised SED model)
   - validation: acceptance ratio 0.44  
  > "We obtained an acceptance ratio of $0.44$" (3 Revised SED model)
6. **Stellar wind estimate**: Solve beta + beta_wind = 0.5 at s_min with assumed wind speed 400 km/s  
  > "We find that $\beta + \beta_{\mathrm{wind}} = 0.5$ can be reached for a size of $\sim 0.16$ $\mu$m" (3 Revised SED model)
   - assumption: v_sw = 400 km/s, C_D ~2  
  > "(assumed to be $400$ km.s$^{-1}$)" (3 Revised SED model)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7: data reduction, imaging, uvmodelfit  
  > "Both datasets were reduced using CASA (version 4.7, (cite: McMullin2007))" (2.1 ALMA observations)
- **emcee** : MCMC SED fit  
  > "we used the affine invariant ensemble sampler (`emcee`, (cite: Foreman-Mackey2012))" (3 Revised SED model)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Disk integrated flux density at 870 um | 2.1 | 0.4 | mJy | 4 | of $2.1 \pm 0.4$ mJy |
| Contaminant offset from TWA 7 | 6.6 | not stated | arcsec | 1 | a compact source is detected at about $\sim 6.6\ensuremath{''}$ East of TWA 7 |
| Contaminant best-fit flux | 3.9 | not stated | mJy | 4 | finding a best-fit flux of $3.9$ mJy, a FWHM of $0.27\ensuremath{''}$ |
| Proper motion mu_alpha cos delta | -109 | 1 | mas/yr | 2 | $\mu_ \alpha$ cos$(\delta)=-109 \pm 1$ mas.yr$^{-1}$ |
| alpha_out | -4.5 | +0.2/-0.3 | dimensionless | 5 | $-4.5_{-0.3}^{+0.2}$ |
| s_min | 0.16 | +0.04/-0.02 | um | 5 | $0.16_{-0.02}^{+0.04}$ |
| Dust mass | 0.018 | +0.002/-0.001 | M_earth | 5 | $0.018_{-0.001}^{+0.002}$ |

## Qualitative findings


## Claim tuples

- H: Sub-mm emission near TWA 7 comes from the disk | E: Band 7 imaging in two configurations | R: compact source 6.6" east; none at star in Briggs image | F: A background source dominates the sub-mm flux | **supported**
- H: The disk can be detected after removing contaminant | E: Tapered imaging after uvmodelfit subtraction | R: 2.1±0.4 mJy | F: Disk detected at 870 um | **supported**
- H: Two dust belts are needed for the SED | E: emcee SED fit with single belt | R: good fit with one belt | F: Single belt suffices | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): SPIRE 350 um may be contaminated and was excluded  
  > "we cannot assess whether the background object is contributing significantly at those wavelengths" (2.3)
- Caveat (inferred, ours): Disk flux depends on taper and 2 sigma integration region
- Caveat (inferred, ours): Single Gaussian contaminant model may leave residuals
- Caveat (inferred, ours): Dust composition fixed to astro-silicate
- Caveat (inferred, ours): Disk radius fixed from SPHERE

## Reproducibility

- Data public (paper): ALMA data acknowledged by project code  
  > "ADS/JAO.ALMA#2015.1.01015.S" (Acknowledgements)
- Products in archive: _not stated_
- Missing: Briggs robust, image parameters, clean settings
- Missing: SED stellar model inputs
- Missing: Contaminant-subtraction details
- Data volume (inferred): ~10-50 GB raw for three execution blocks
- Score (inferred): 5/5, Public data and clear approach but many imaging and SED details missing or deferred.
- Rediscovery candidate: no, Imaging parameters and SED inputs incomplete.

## Links

- Method: (cite: Olofsson2018) (SED code and stellar properties)
- Companion: (cite: Matra2019) (CO line analysis)

## Checks

```json
{
 "quotes": 53,
 "quotes_ok": 53,
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
  "facts": 76,
  "stated": 41,
  "rate": 0.539
 },
 "evidence_ok": true
}
```
