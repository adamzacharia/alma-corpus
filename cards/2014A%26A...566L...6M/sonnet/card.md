# Detection of chloronium and measurement of the <SUP>35</SUP>Cl/<SUP>37</SUP>Cl isotopic ratio at z = 0.89 toward PKS 1830-211

`2014A&A...566L...6M` | Astronomy and Astrophysics 2014 | first author: Muller, S. | arXiv: 1404.7668 | DOI: 10.1051/0004-6361/201423947

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, astrochemistry
- Question: Is chloronium (H2Cl+) detectable in the z=0.89 absorber toward PKS 1830-211, and what is the 35Cl/37Cl isotopic ratio at that look-back time?  
  > "Here, we report the first extragalactic detection of chloronium, in the $z$=0.89 absorber toward the $z$=2.5 blazar PKS 1830$-$211, and a measurement of the $^{35}$Cl/$^{37}$Cl isotopic ratio" (Introduction)
- Target **PKS 1830-211 (SW and NE images; z=0.89 absorber)**: coordinates _not stated_; z/distance absorber z=0.88582; background blazar z=2.5  
  > "All velocities are referred to redshift $z$=0.88582 in the heliocentric frame." (Data); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00405.S
- bands: Band 6  
  > "We used ALMA Band 6 data from four observing runs performed between April and June 2012." (Data)
- frequencies and spectral setup: both isotopologues in one 1.875 GHz wide spectral window, 0.488 MHz channels, ~257 GHz observed  
  > "The two chloronium isotopologues were observed simultaneously in the same spectral window, 1.875 GHz wide and with a spectral channel spacing of 0.488 MHz." (Data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: resolves the two lensed images separated by 1''  
  > "The two lensed images of the background blazar, separated by 1$''$, were resolved by the ALMA array" (Data)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: approximately 30 min total  
  > "The total resulting on-source integration time was approximately 30 min." (Data)
- observing dates: April to June 2012  
  > "We used ALMA Band 6 data from four observing runs performed between April and June 2012." (Data)
- pi or archival as stated: _not stated_
- Line: H2(35)Cl+ 1_11-0_00 (para) (~485.4 GHz)
- Line: H2(37)Cl+ 1_11-0_00 (para) (~484.2 GHz)
- External data: Chloronium frequencies and hyperfine relative intensities  
  > "The chloronium frequencies and relative intensities of the hyperfine components are taken from the work by (cite: ara01)." (Data) [from (cite: ara01)]
- External data: Dipole moment 1.89 D (ab initio)  
  > "The dipole moment, $\mu$=1.89 D, is from an ab initio calculation by (cite: holger08)." (Data) [from (cite: holger08)]
- External data: Total H2 column densities 2e22 (SW) and 1e21 cm-2 (NE)  
  > "With total H$_2$ column densities of 2$\times$10$^{22}$ and 1$\times$10$^{21}$ cm$^{-2}$ along the SW and NE lines of sight, respectively" (Column densities and abundances) [from (cite: mul11) and Paper I]
- External data: Chemical evolution model predictions of isotope ratios  
  > "we compare the isotopic ratios measured at $z$=0.89 toward PKS 1830$-$211(SW) with theoretical predictions of time/metallicity evolution models by (cite: kob11) in the Milky Way." (Isotopic ratio) [from (cite: kob11)]

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

- Observations and data reduction  
  > "The observations and details of the data reduction are described by (cite: mul14) (hereafter *Paper I*)." (Data) [from (cite: mul14) Paper I]
- SW covering factor ~95% from 557 GHz water saturation  
  > "the covering factor of the SW image is not unity, but $\sim$95%, as shown by the saturation level of the 557 GHz water line (see *Paper I*)." (Column densities and abundances) [from Paper I]

### Not stated but needed to reproduce (our reading)

- Calibration pipeline, CASA version, calibrators (all deferred to Paper I)
- Continuum normalization and uvmultifit settings
- Velocity range for integrated opacity
- Monte Carlo procedure details and initial Gaussian parameters
- Hanning smoothing procedure and relative hyperfine weights used

## Analysis recipe

1. **Extract absorption spectra per lensed image**: Model visibilities with two point sources with fixed relative positions and free flux densities  
  > "by modelling the visibilities with two point-like sources where the relative positions were fixed and the flux densities left as free parameters." (Data)
   - software: uvmultifit
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive column densities and abundances**: Integrated opacity converted to column density of H2(35)Cl+ para line with ortho/para=3  
  > "we derive a column density of $\sim$1.4$\times$10$^{13}$ cm$^{-2}$." (Column densities and abundances)
   - assumption: Tex = T_CMB = 5.14 K, covering factor 1, ortho/para = 3  
  > "Assuming a rotation temperature locked to the temperature of the cosmic microwave background, $T_\mathrm{CMB}$=5.14 K at $z$=0.89" (Column densities and abundances)
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure 35Cl/37Cl ratio**: Simultaneous single-Gaussian fit of both isotopologues in SW spectrum, shared centroid and width  
  > "From a simultaneous fit of the SW spectrum with a single Gaussian component (centroid and width constrained to the same values for both isotopologues)" (Isotopic ratio)
   - assumption: Abundance ratio reflects isotopic ratio (weak fractionation)  
  > "The simple, well-known chlorine chemistry and the most likely weak fractionation between both isotopologues ensure that this ratio reflects the $^{35}$Cl/$^{37}$Cl isotopic ratio." (Isotopic ratio)
   - fitting: Monte Carlo analysis, 68% confidence uncertainties  
  > "where uncertainties correspond to a 68% confidence level from a Monte Carlo analysis." (Isotopic ratio)
   - validation: _not stated_

## Software

- **uvmultifit** : Extract absorption spectra toward each image via visibility modelling  
  > "One absorption spectrum was extracted toward each image with the task uvmultifit ((cite: mar14))" (Data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 35Cl/37Cl toward SW | 3.1 | +0.3/-0.2 (68%) | dimensionless | 3 | we derive an isotopic ratio $^{35}$Cl/$^{37}$Cl of $3.1_{-0.2}^{+0.3}$ |
| 35Cl/37Cl toward NE lower limit | >1.9 | 99.7% confidence | dimensionless | 3 | We estimate a lower limit of $^{35}$Cl/$^{37}$Cl$>$1.9 at a 99.7% confidence level. |
| H2(35)Cl+ column density SW | ~1.4e13 | not stated | cm-2 | 2 | we derive a column density of $\sim$1.4$\times$10$^{13}$ cm$^{-2}$. |
| H2(35)Cl+ column density NE | 4e12 | not stated | cm-2 | 2 | corresponding to a H$_2^{35}$Cl$^+$ column density of 4$\times$10$^{12}$ cm$^{-2}$. |
| H2(35)Cl+ FWHM SW | 32 | 1 | km/s | 1 | wider (FWHM=32$\pm$1 km s$^{-1}$) |
| [H2Cl+]/[H2] SW | ~6e-10 | not stated | dimensionless | 2 | fractional abundances of \[H$_2^{35}$Cl$^+$\]/\[H$_2$\]$\sim$6$\times$10$^{-10}$ (SW) and $\sim$4$\times$10$^{-9}$ (NE) |
| [H2Cl+]/[H2] NE | ~4e-9 | not stated | dimensionless | 2 | fractional abundances of \[H$_2^{35}$Cl$^+$\]/\[H$_2$\]$\sim$6$\times$10$^{-10}$ (SW) and $\sim$4$\times$10$^{-9}$ (NE) |

## Qualitative findings

- First extragalactic detection of chloronium; H2Cl+ more abundant relative to H2 along the more diffuse NE sightline.  
  > "The H$_2$Cl$^+$ relative abundance along the NE line of sight was found to be enhanced by a factor $\sim$7 with respect to the SW line of sight." (Summary and conclusions)

## Claim tuples

- H: Chloronium is present in the z=0.89 absorber and traces diffuse gas | E: Extract ALMA Band 6 absorption spectra toward both images and derive abundances | R: Detected in both images; relative abundance ~7 times higher toward NE | F: H2Cl+ is a good tracer of diffuse, more atomic gas | **supported**
- H: 35Cl/37Cl at z=0.89 differs from local values like other isotope ratios | E: Simultaneous Gaussian fit of H2(35)Cl+ and H2(37)Cl+ toward SW | R: 3.1 +0.3/-0.2 | F: Identical to solar system value within uncertainty and within Galactic range | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): NE covering factor poorly known (0.3<fc<1.0); NE H2(37)Cl+ not detected, only a lower limit on the ratio.  
  > "Note that the covering factor is not well known toward the NE image, but the ALMA data suggest 0.3$<$$f_c$$<$1.0." (Column densities and abundances)
- Caveat (inferred, ours): Hyperfine structure not deconvolved; Gaussian assumption for the profile may bias the ratio
- Caveat (inferred, ours): Single Tex=T_CMB assumption
- Caveat (inferred, ours): Short 30 min integration, limited S/N for 37Cl

## Reproducibility

- Data public (paper): ALMA project 2011.0.00405.S cited; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00405.S." (Summary and conclusions)
- Products in archive: _not stated_
- Missing: Calibration details (in Paper I)
- Missing: Monte Carlo and fit setup details
- Data volume (inferred): ~10-50 GB
- Score (inferred): 4/5, Short letter, data reduction deferred to Paper I, fit details sparse.
- Rediscovery candidate: no, Recipe incomplete without Paper I and the fit details.

## Links

- Method: (cite: mar14) (uvmultifit visibility fitting)
- Companion: (cite: mul14) Paper I (Observations and data reduction)

## Checks

```json
{
 "quotes": 36,
 "quotes_ok": 36,
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
  "facts": 63,
  "stated": 23,
  "rate": 0.365
 },
 "evidence_ok": true
}
```
