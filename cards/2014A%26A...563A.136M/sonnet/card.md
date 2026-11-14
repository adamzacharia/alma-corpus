# UVMULTIFIT: A versatile tool for fitting astronomical radio interferometric data

`2014A&A...563A.136M` | Astronomy and Astrophysics 2014 | first author: Martí-Vidal, I. | arXiv: 1401.4984 | DOI: 10.1051/0004-6361/201322633

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type technical_calibration_or_instrument

## Science

- Fields: instrumentation, other
- Question: Can a flexible visibility-domain model-fitting library outperform image-plane analysis for sources near or below the resolution limit?  
  > "Fitting models to the direct interferometric observables (i.e., the visibilities) is preferable in the cases of simple (analytical) sky intensity distributions." (abstract)
- Target **PKS 1830-211**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **SN 1993J / M 81***: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00405.S
- bands: Band 3 (~90 GHz), Cycle 0  
  > "the restoring beam of the ALMA B3 ($\sim$90 GHz) observations is 1.5$\times$1.9 arcsec, with a position angle of 80 deg." (3.2.1 ALMA observations of PKS 1830-211)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.5x1.9 arcsec, PA 80 deg  
  > "the restoring beam of the ALMA B3 ($\sim$90 GHz) observations is 1.5$\times$1.9 arcsec, with a position angle of 80 deg." (3.2.1 ALMA observations of PKS 1830-211)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **VLBI**: 1.7, 5.0, 8.4 GHz data of SN 1993J (15 Nov 1997) used to test the code  
  > "We selected VLBI observations of SN 1993J at 1.7, 5.0, and 8.4 GHz, taken on 15 Nov 1997." (3.2.2 VLBI observations of SN 1993J)
- External data: Relative NE-SW positions of PKS 1830-211 images from VLBI astrometry  
  > "Since the relative position between the NE and SW images is well-known from VLBI observations (e.g., (cite: Jin))" (3.2.1 ALMA observations of PKS 1830-211) [from (cite: Jin)]
- External data: Inner/outer shell radius ratio of 0.7 for SN 1993J  
  > "Here, the ratio of the inner shell radius to the outer shell radius is set to 0.7 ((cite: IMV93J))." (3.2.2 VLBI observations of SN 1993J) [from (cite: IMV93J)]
- Simulation/model as data: Synthetic ALMA Cycle 0 compact-configuration data of two point sources 1 arcsec apart (20 and 29 mJy) made with simobserve  
  > "we made use of the ALMA interferometer in its compact configuration at cycle 0." (3.1.2 Simulated interferometer)

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
- weighting robust: Briggs, robustness 0.5 (simulated data)  
  > "4.68$\times$4.15 arcsec, using *Briggs* weighting with a robustness parameter of 0.5" (3.1.3 Results from imaging)
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

- Fitting strategy for PKS 1830-211 absorption spectra copied from the simulation  
  > "Indeed, we used the same fitting strategy to extract the absorption spectra toward the NE and SW images." (3.2.1 ALMA observations of PKS 1830-211) [from Sect. 3.1.4 of this paper]
- Further PKS 1830-211 results deferred to a companion paper  
  > "More details about these results will be given elsewhere (Muller at al. in prep.)." (3.2.1 ALMA observations of PKS 1830-211) [from Muller et al. in prep.]

### Not stated but needed to reproduce (our reading)

- Calibration and CASA version for the PKS 1830-211 ALMA data
- Line-free channel ranges for the PKS 1830-211 continuum fit
- Initial guesses and fitted flux values for PKS 1830-211
- uvmultifit version and exact code for reproduction
- Random seed for the synthetic spectra

## Analysis recipe

1. **Locate sources from continuum channels**: Fit two delta components to line-free channels in one fit (OneFitPerChannel=False), with relative position bounded  
  > "we select a subset of frequency channels corresponding to continuum emission and fit the data with `OneFitPerChannel`=False" (3.1.4 Visibility model-fitting. Locating the sources)
   - software: uvmultifit, CASA
   - parameter: PKS 1830-211: relative position bounded within 10 mas of VLBI astrometry  
  > "we bounded the fit of the relative positions to be within only 10 mas with respect to the VLBI-astrometry results." (3.2.1 ALMA observations of PKS 1830-211)
   - fitting: Levenberg-Marquardt or SIMPLEX chi-square minimization  
  > "is performed using either the Levenberg-Marquardt approach (cite: Levenberg) or the SIMPLEX algorithm (cite: Nesa)" (2.2 Model-fitting algorithm)
   - validation: Fitted positions differ by at most about 15 mas from the true ones in simulations  
  > "the positions fitted in continuum mode only differ by about 15 mas (at most) from the true positions of the sources." (3.1.5 Visibility model-fitting. Recovering the spectra)
2. **Recover per-channel spectra**: Fix positions, fit flux density of each component per channel (OneFitPerChannel=True)  
  > "we only solve for the fluxes of the two delta components at each spectral channel (i.e., we now set `OneFitPerChannel`=True)." (3.1.5 Visibility model-fitting. Recovering the spectra)
   - software: uvmultifit
   - fitting: _not stated_
   - validation: Fitting errors show no line features; typical error ~0.5 mJy  
  > "The typical fitting error is around 0.5 mJy for both components." (3.1.5 Visibility model-fitting. Recovering the spectra)

## Software

- **uvmultifit** : Visibility model fitting  
  > "We present UVMULTIFIT, a versatile library for fitting visibility data, implemented in a Python-based framework." (abstract)
- **CASA** 4.1 (GUI tested): Host package; simobserve and CLEAN  
  > "To generate the synthetic visibilities, we used the casa task `simobserve`." (3.1.2 Simulated interferometer)
- **immultifit** : Extension for fitting large sources using dirty image and PSF  
  > "we have developed an extension called immultifit." (2.2 Model-fitting algorithm)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Core shift of M 81* | 2.05 | 0.13 | mas GHz^-1 | 0 | The simultaneous fit to the three datasets gives us a core shift of $2.05\pm0.13$ mas GHz$^ {-1}$ |
| SN 1993J shell radius | 3.23 | 0.02 | mas | 0 | our estimate of the shell radius is $3.23\pm0.02$ mas |
| SN 1993J spectral index | -0.83 | 0.01 | dimensionless | 0 | the estimated spectral index is $-0.83\pm0.01$ |
| Core-shift position angle | 62 | 4 | deg | 0 | our estimate of the position angle of the core shift is $62\pm4$ deg. |

## Qualitative findings

- Visibility fitting separates spectra of two sources unresolved by the beam, which the CLEAN image cannot  
  > "As can be seen in the figure, the two spectra in the image plane cannot be separated." (3.1.3 Results from imaging)

## Claim tuples

- H: Visibility fitting can separate spectra of sources closer than the beam | E: Simulated ALMA Cycle 0 data of two deltas 1 arcsec apart, two-step fit | R: Spectra decoupled with ~0.5 mJy errors; positions within ~15 mas | F: uvmultifit recovers spectra that imaging cannot | **supported**
- H: The same approach works on real ALMA data | E: Fit to ALMA B3 data of PKS 1830-211 with positions bounded by VLBI | R: Uncorrelated NE and SW absorption spectra | F: The method separates the lensed images | **supported**
- H: Simultaneous multi-frequency fits reproduce published VLBI results | E: Joint fit of SN 1993J at 1.7, 5.0, 8.4 GHz | R: Core shift, radius and spectral index consistent with earlier work | F: The simultaneous fit improves precision | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Mosaic fits require components small relative to the primary beam; no line-profile kinematics in the models  
  > "the size of each individual component must be small compared with the telescope’s primary beam" (2.2 Model-fitting algorithm)
- Caveat (inferred, ours): Only a single simulated configuration and no comparison against other fitting tools
- Caveat (inferred, ours): ALMA real-data results are shown only as a figure with no numbers
- Caveat (inferred, ours): Fitting-bias systematics (~2%) are attributed to position offsets without a full test

## Reproducibility

- Data public (paper): Code is open and downloadable; ALMA project code given  
  > "We distribute uvmultifit under the terms of the general public licence (GPL); the code is open and free." (2.1 Installation and use)
- Products in archive: _not stated_
- Code: Downloadable from nordic-alma.se/support/software-tools  
  > "`http://nordic-alma.se/support/software-tools`" (2.1 Installation and use)
- Missing: PKS 1830-211 calibration and spectral setup
- Missing: SN 1993J VLBI data location
- Missing: Initial parameter guesses
- Data volume (inferred): ~10-50 GB for the ALMA Cycle 0 PKS 1830-211 data
- Score (inferred): 3/5, The simulation is reproducible from the text and the code is open, but the real ALMA analysis is thinly documented.
- Rediscovery candidate: no, The ALMA results are not numeric and the recipe lacks detail.

## Links

- Method: (cite: IMVOver) (Super-resolution formula for the smallest resolvable size)
- Companion: Muller et al. in prep. (Full PKS 1830-211 results)
- Companion: (cite: IMV93J) (Prior SN 1993J VLBI analysis)

## Checks

```json
{
 "quotes": 32,
 "quotes_ok": 32,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 65,
  "stated": 23,
  "rate": 0.354
 },
 "evidence_ok": true
}
```
