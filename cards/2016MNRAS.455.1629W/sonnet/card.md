# Probing star formation in the dense environments of z ∼ 1 lensing haloes aligned with dusty star-forming galaxies detected with the South Pole Telescope

`2016MNRAS.455.1629W` | Monthly Notices of the Royal Astronomical Society 2016 | first author: Welikala, N. | arXiv: 1510.01359 | DOI: 10.1093/mnras/stv2302

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies, cosmology
- Question: How much star formation is in the dense environments of z~1 lensing halos aligned with SPT-selected lensed DSFGs, as probed by Planck and Herschel stacks?  
  > "We probe star formation in the environments of massive ($\sim10^{13}\Msolar$) dark matter halos at redshifts of $z$$\sim$$1$." (abstract)
- Target **65 SPT-selected lensed DSFGs (S220>20 mJy)**: coordinates _not stated_; z/distance mean z=3.5; lensing halos z~1  
  > "The mean redshift of the SPT sample is $\langle z\rangle=3.5$, as determined by (cite: weiss2013) through a CO redshift survey conducted with ALMA for a sample of 26 of these DSFGs." (2.1 South Pole Telescope selection); distance from Weiss et al. 2013 (CO redshifts); Hezaveh & Holder 2011 for lens redshift  
  > "The mean redshift of the SPT sample is $\langle z\rangle=3.5$, as determined by (cite: weiss2013) through a CO redshift survey conducted with ALMA for a sample of 26 of these DSFGs." (2.1 South Pole Telescope selection)

## Data provenance

- ALMA projects: 2011.0.00957.S
- bands: ALMA 100 GHz (3 mm) continuum, used only for positions of 26 DSFGs  
  > "derived from ALMA 100 GHz (3 mm) continuum observations whenever they are available." (2.6 ALMA)
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
- Other facility **Planck HFI**: Public 217-857 GHz maps stacked at SPT DSFG positions  
  > "we use the public  HFI maps, which can be obtained from the  Legacy Archive" (2.2 Planck)
- Other facility **Herschel SPIRE**: 250/350/500 micron maps for resolved sources; HerMES Lockman-SWIRE reference field  
  > "We use *Herschel* Spectral and Photometric Imaging Receiver (SPIRE) observations of the SPT DSFGs" (2.5 Herschel)
- Other facility **SPT**: Sample selection, 220 GHz flux densities  
  > "In this work, our parent sample comprises 65 DSFGs discovered by SPT over 2500 ${\rm deg}^2$" (2.1 South Pole Telescope selection)
- Other facility **APEX/LABOCA**: 345 GHz flux densities and positions  
  > "All the SPT sources from the $2500\,{\rm deg}^2$ survey data were imaged at 345 GHz with the Large APEX BOlometer CAmera (LABOCA) at APEX" (2.4 APEX continuum imaging)
- Other facility **IRIS**: 3000 GHz maps  
  > "We combine the -HFI data with 3000 GHz IRIS photometry" (2.3 IRIS)
- External data: ALMA 100 GHz positions of 26 SPT DSFGs  
  > "The ALMA positions used here were reported in (cite: weiss2013)." (2.6 ALMA) [from (cite: weiss2013)]

## Processing

### Calibration

- pipeline or manual: _not stated_
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

- ALMA positions taken from earlier paper, not reprocessed  
  > "The ALMA positions used here were reported in (cite: weiss2013)." (2.6 ALMA) [from (cite: weiss2013)]

### Not stated but needed to reproduce (our reading)

- ALMA positions themselves (table values) are not given
- Which 26 sources have ALMA positions
- No ALMA calibration/imaging details

## Analysis recipe

1. **Stack Planck maps and fit compact source plus clustered component**: Aperture photometry within 3.5' on stacks; fit compact (Gaussian PSF), clustered (w~theta^-0.8) and constant background  
  > "We fit the clustered component around the source using an angular correlation function $w(\theta)\propto{\theta}^{-0.8}$ that is first convolved with the  PSF FWHM at each frequency" (Appendix 11)
   - software: HEALPix
   - fitting: Linear least squares for three normalisations  
  > "Minimizing $s^2$ with respect to $\alpha,
\beta$ and $\gamma$ leads to a simple matrix equation" (Appendix 11)
   - validation: Bootstrap, stacking simulations, random rotations, synchrotron-source stack  
  > "In Appendix [12](#app:clustering_tests), we describe three tests to verify that the clustered component is real and not simply an artefact of the stacking procedure." (4.1.1)
2. **Herschel resolved source excess**: STARFINDER extraction with S857>50 mJy within 3.5', FASTPHOT deblending, compare with Lockman-SWIRE  
  > "We use the `STARFINDER` algorithm (cite: diolaiti2000) which was developed to blindly extract sources from confused maps" (3.2)
   - software: STARFINDER, FASTPHOT
   - fitting: _not stated_
   - validation: Monte Carlo source injection  
  > "the completeness is higher than 95$\%$ and flux boosting (due to Malmquist and Eddington bias and from source confusion) is below 5$\%$" (3.2)

## Software

- **STARFINDER** : Source extraction in Herschel maps  
  > "We use the `STARFINDER` algorithm (cite: diolaiti2000)" (3.2)
- **FASTPHOT** : Photometry at known positions  
  > "we measure the 1200 GHz flux density at the 857 GHz position using `FASTPHOT`" (3.2)
- **PMClib** : Halo auto-correlation computation  
  > "The computation is performed using the `PMClib` tools" (5 Modeling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Excess SFR from Planck clustered component within 3.5' | 2700 | 700 | Msun/yr | 1 | $(2700\pm700)\,\Msolar\,{\rm yr}^{-1}$ |
| Excess SFR per resolved Herschel source | 370 | 40 | Msun/yr | 2 | $(370\pm40)\,\Msolar\,{\rm yr}^{-1}$ per resolved, clustered source |
| Clustered flux density at 857 GHz | 209.6 | 78.0 | mJy | 1 | 209.6$\pm$78.0 |

## Qualitative findings


## Claim tuples

- H: Environments of z~1 lensing halos host intense star formation | E: Stack Planck at SPT DSFG positions and use Herschel | R: Excess SFR 2700±700 Msun/yr within 3.5' | F: Dense z~1 environments are actively forming stars | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Caveat (inferred, ours): ALMA plays only a positional role
- Caveat (inferred, ours): Large uncertainties on Planck excess

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA positions table
- Data volume (inferred): small for ALMA part
- Score (inferred): 2/5, ALMA only supplies positions from earlier paper.
- Rediscovery candidate: no, ALMA data not central; main results rely on Planck/Herschel.

## Links

- Companion: (cite: weiss2013) (ALMA CO redshifts and positions)
- Related: SPT 2500 deg2 survey
- Related: HerMES

## Checks

```json
{
 "quotes": 25,
 "quotes_ok": 25,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 59,
  "stated": 19,
  "rate": 0.322
 },
 "evidence_ok": true
}
```
