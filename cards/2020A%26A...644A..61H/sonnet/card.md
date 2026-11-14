# ATOMIUM: A high-resolution view on the highly asymmetric wind of the AGB star π<SUP>1</SUP>Gruis. I. First detection of a new companion and its effect on the inner wind

`2020A&A...644A..61H` | Astronomy and Astrophysics 2020 | first author: Homan, Ward | arXiv: 2010.05509 | DOI: 10.1051/0004-6361/202039185

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: evolved_stars
- Question: What is the morphology and inner-wind dynamics of the S-type AGB star pi1 Gru, and is there evidence for a close companion shaping its wind?  
  > "In this work, the brightest CO, SiO, and HCN molecular line transitions are analysed." (abstract)
- Target **pi1 Gruis**: coordinates _not stated_; z/distance 163±20 pc  
  > "Its *Hipparcos* parallax places it at a distance of approximately 163$\pm$20 parsec (cite: VanLeeuwen2007)." (Introduction); distance from Hipparcos parallax (van Leeuwen 2007)  
  > "Its *Hipparcos* parallax places it at a distance of approximately 163$\pm$20 parsec (cite: VanLeeuwen2007)." (Introduction)

## Data provenance

- ALMA projects: 2018.1.00659.L
- bands: Band 6, cycle 6  
  > "we conducted spatially resolved cycle 6 ALMA band 6 observations of the CSE of $\pi^1$Gru using three different antenna configurations" (Introduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: extended, mid, compact (12m), combined with equal weight  
  > "The data were combined with equal weight given to all configurations." (Data acquisition and reduction)
- baselines: _not stated_
- angular resolution: Combined continuum beam 25x23 mas  
  > "| combined | 25$\times$23, 44          | 0.010     | 9.3      |" (Table 1)
- max recoverable scale: 0.4" (extended), 3.9" (mid), 9.3" (compact/combined)  
  > "| combined | 25$\times$23, 44          | 0.010     | 9.3      |" (Table 1)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: October 2018 to July 2019  
  > "$\pi^1$Gru was observed by ALMA between October 2018 and July 2019 using three different antenna array configurations." (Data acquisition and reduction)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (230.5380 GHz)
- Line: HCN J=3-2 (265.8864 GHz)
- Line: SiO J=5-4 (217.1050 GHz)
- External data: Stellar Teff 3100 K and log L/Lsun=3.86  
  > "estimated an effective temperature of $T_*\simeq$ 3100K and a luminosity of $\log (\mathrm{L}/\mathrm{L}_\odot)=3.86$." (Introduction) [from Van Eck 1998]
- External data: Single-dish CO 2-1 integrated flux (SEST) ~1140 Jy km/s rescaled  
  > "for which we have calculated its rescaled integrated flux to $\sim$1140 Jy$\, {\rm km}\, {\rm s}^{-1}$." (4.1) [from Winters et al. 2003]
- External data: APEX CO flux ~3080 Jy km/s  
  > "show APEX data from 2005 for which we calculated an integrated flux of $\sim$3080 Jy$\, {\rm km}\, {\rm s}^{-1}$." (4.1) [from Doan et al. 2017]

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
- deconvolver: multiscale CLEAN, more weight on large scales  
  > "We used multiscale CLEAN to produce the image cubes, with more weight given to large scales." (Data acquisition and reduction)
- weighting robust: _not stated_
- uv taper: 0.02" for HCN and SiO; 0.17" for CO  
  > "a visibility plane taper equivalent to 0.02” was applied to reduce CLEAN instabilities. For CO, a taper of 0.17” was used" (Data acquisition and reduction)
- cell size: _not stated_
- image size: smaller of 0.2 primary beam level (~20" radius) or region of emission  
  > "The total image sizes were set to the smaller of: (i) the 0.2 sensitivity level of the primary beam, with a radius of $\sim$20"" (Data acquisition and reduction)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: all configurations combined with equal weight  
  > "The data were combined with equal weight given to all configurations." (Data acquisition and reduction)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Observation details and data processing  
  > "For more details of observations and data processing see Gottlieb et al. *in prep.*, Sects. 2 and 3." (Data acquisition and reduction) [from Gottlieb et al. in prep.]
- Dust condensation radius ~6 au  
  > "Assuming that the dust condensation radius is around 6 au (see Montargès et al., *in prep.*)" (5.4) [from Montargès et al., in prep.]

### Not stated but needed to reproduce (our reading)

- Calibration pipeline, CASA version, calibrators
- Robust/weighting, cell size, multiscale scales, CLEAN thresholds and masks
- Continuum-subtraction and line-free channels
- Exact spiral-fit procedure for inclination (grid, uncertainty derivation)
- Channel selection details for arc measurements

## Analysis recipe

1. **Measure continuum components**: Identify two maxima in combined continuum, measure peak and integrated flux inside 120 sigma contours  
  > "The two components are separated at the 120$\times \sigma_{\rm rms}$ level." (3)
   - assumption: Distance 163 pc  
  > "about 6.25 au assuming a distance of 163 pc" (3)
   - fitting: _not stated_
   - validation: Compared with blackbody flux 26.5 mJy from stellar parameters  
  > "to be 26.5 mJy, or approximately the total flux within the north loop" (3)
2. **Fit inclination via Archimedean spiral**: Fit inclined Archimedean spiral to CPmom0 map within 5"; inclination maximizing mean pixel value along spiral  
  > "The angle that yields the highest pixel average is assumed to be the inclination of the system, which was determined to be (38$\pm$3)$^\circ$." (5.1)
   - parameter: Tilt 6 deg; arm spacing ~2"  
  > "the tilt of 6$^\circ$ (the PA of the system, see Fig. [15](#COstereo))" (5.1)
   - fitting: _not stated_
   - validation: Agrees with ~40 deg of Doan 2017  
  > "This value is in agreement with the previously visually constrained value of $\sim$40$^\circ$ by (cite: Doan2017)." (5.1)
3. **Locate compact SiO emission**: 2D Gaussian fits to emission >20 sigma per channel; keep those consistent in adjacent channels  
  > "We fitted 2D Gaussian components to each patch of emission above 20$\sigma_{\rm rms}$ in each of the mid-configuration channel maps" (4.4)
   - software: AIPS SAD
   - fitting: _not stated_
   - validation: Position error ~0.5*beam/SNR  
  > "The position error of a fitted Gaussian component is approximately 0.5\*(synthesised beam)/(signal to noise ratio)" (4.4)
4. **Companion mass from maser acceleration**: Free-fall mean acceleration over the blue-shifted maser trail equated to gravitational acceleration  
  > "Assuming the gas is inside the companion’s potential well and undergoing free fall, we equate this acceleration to the theoretically expected mean gravitational acceleration" (5.3)
   - assumption: Inclination 38 deg; no pulsation/dust effects  
  > "no additional effects that contribute to the acceleration of the gas (e.g. pulsations, dust, ...) have been taken into account" (5.3)
   - fitting: _not stated_
   - validation: Consistent with Mayer 2014  
  > "consistent with the rough estimate made by (cite: Mayer2014)" (5.3)
5. **Fit beta-law wind acceleration**: Orthogonal distance regression of beta law to deprojected speed-distance pairs of HCN and CO arcs  
  > "we used the SCIPY.ODR python library to derive a beta-law best-fit" (5.4)
   - software: SciPy ODR
   - parameter: r_dc = 6 au fixed  
  > "Assuming that the dust condensation radius is around 6 au" (5.4)
   - fitting: _not stated_
   - validation: _not stated_
6. **Companion separation from crossing time**: Kepler's third law with ~15 yr crossing time, 1.5 Msun system mass  
  > "assuming a 1.5 $\,{\rm M}_\odot$ system mass (cite: Siess2006; Siess2008), we deduce an orbital separation between the AGB star and the companion of $\sim$7 au." (5.4)
   - fitting: _not stated_
   - validation: Matches secondary continuum peak position  
  > "This coincides precisely with the position of the secondary component observed in the ALMA continuum" (5.4)

## Software

- **AIPS (SAD)** : 2D Gaussian fitting of SiO emission patches  
  > "using the SAD[^1] (search and destroy) task in the AIPS package" (4.4)
- **SciPy (ODR)** : beta-law fit  
  > "we used the SCIPY.ODR python library to derive a beta-law best-fit" (5.4)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum component separation | 0.038 | not stated | arcsec | 1 | The components are separated by approximately 0.038” (or about 6.25 au assuming a distance of 163 pc) |
| Primary continuum integrated flux | 25 | not stated | mJy | 1 | it has a total integrated flux density of 25 mJy within the northern loop |
| Inclination | 38 | ±3 | deg | 2 | which was determined to be (38$\pm$3)$^\circ$ |
| Terminal velocity | 19.5 | ±1.4 | km/s | 5 | a terminal velocity value of $\sim$19.5$\pm$1.4 $\, {\rm km}\, {\rm s}^{-1}$, and an exponent of $\beta$=6.0$\pm$1.1 |
| beta exponent | 6.0 | ±1.1 | dimensionless | 5 | an exponent of $\beta$=6.0$\pm$1.1 |
| Companion mass upper limit | 1.1 | not stated | Msun | 4 | or approximately 1.1 $\,{\rm M}_\odot$ |
| Inner spiral crossing time | 15 | not stated | yr | 6 | have a dynamical crossing time scale of $\sim$15 years |

## Qualitative findings

- HCN traces a clockwise spiral of two windings in the inner 1.5"  
  > "which reveal a clockwise spiral consisting of 2 complete revolutions." (4.2)

## Claim tuples

- H: Is the secondary continuum peak a companion shaping the wind? | E: Compare spiral crossing time and Kepler orbit with continuum peak position | R: Predicted separation ~7 au (0.04" projected) matches secondary position | F: Secondary continuum peak is related to a companion | **supported**
- H: Spiral handedness and geometry | E: CPmom0 map, HCN moment maps, spiral fit | R: Clockwise Archimedean spiral within 5", inclination 38±3 deg | F: Spiral is clockwise, contrary to Doan 2020 | **supported**
- H: Wind acceleration profile | E: Beta-law fit to arc speeds | R: beta=6.0±1.1 | F: Large slow acceleration region | **supported**
- H: SiO masers trace gas flowing to the companion | E: Free-fall acceleration along maser trail | R: ~1.1 Msun | F: Tentative upper limit on companion mass | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Compact rotating disc rejected in favour of spiral hypothesis  
  > "Combined, these arguments thus favour the aforementioned spiral hypothesis." (5.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Combined data miss 27-72% of diffuse CO flux  
  > "This means that between 27% and 72% of the diffuse, larger-scale emission is missing from the data." (4.1)
- Caveat (inferred, ours): Mass estimate relies on a few maser positions and ignores other accelerations
- Caveat (inferred, ours): Calibration and imaging details deferred to an unpublished paper
- Caveat (inferred, ours): Beta-law fit uses four points with overestimated velocity errors

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Calibration and imaging parameters (in Gottlieb et al. in prep.)
- Missing: Dust condensation radius source in prep.
- Data volume (inferred): ~100s of GB to ~1 TB (three configurations, multiple spectral windows)
- Score (inferred): 4/5, Data from the ALMA archive but processing details are deferred to an in-prep paper; the analysis is partly qualitative.
- Rediscovery candidate: no, Processing recipe incomplete and key results are partly morphological.

## Links

- Method: Gottlieb et al. in prep. (Observations and data processing details)
- Companion: Decin et al. 2020 (Atomium overview)
- Companion: Montargès et al. in prep. (Continuum and SPHERE analysis)
- Related: ATOMIUM

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
  "facts": 75,
  "stated": 37,
  "rate": 0.493
 },
 "evidence_ok": true
}
```
