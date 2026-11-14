# Arp 220: New Observational Insights into the Structure and Kinematics of the Nuclear Molecular Disks and Surrounding Gas

`2020ApJ...896...43W` | The Astrophysical Journal 2020 | first author: Wheeler, Jordan | arXiv: 2006.09262 | DOI: 10.3847/1538-4357/ab8f32

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies
- Question: What are the morphology, kinematics, outflows and physical conditions (temperature, optical depth, mass) of the Arp 220 nuclear disks and extended gas, as probed by CO, 13CO, HCN and SiO and non-LTE LIME models?  
  > "These observations are compared to non-LTE radiative transfer models created using the Line Modeling Engine (LIME) for simple gas dynamics" (abstract)
- Target **Arp 220 (eastern and western nuclei)**: coordinates Peak continuum: East (15:34:57.294, +23.30.11.34), West (15:34:57.224, +23.30.11.50) J2000  
  > "At a distance of only 77 Mpc, ALMA’s high spatial resolution resolves the emission from the two merging nuclei" (1 Introduction); z/distance 77 Mpc  
  > "At a distance of only 77 Mpc, ALMA’s high spatial resolution resolves the emission from the two merging nuclei" (1 Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00736.S
- bands: Band 7 (12CO 3-2, SiO 8-7) and Band 8 (13CO 4-3, HCN 5-4)  
  > "Arp 220 was observed in $^{13}$CO J = $4 \rightarrow 3$ with ALMA’s band 8 receivers" (2 Observations and Data Reduction)
- frequencies and spectral setup: Band 7: 350.6, 352.4 (continuum), 340.6 (12CO), 342.4 GHz (SiO); Band 8: 432.0 (13CO), 433.8 (HCN/continuum), 421.8 GHz; 15.625 MHz resolution TDM  
  > "The bands observed were centered on 432.0 GHz ($^{13}$CO J = $4 \rightarrow 3$), 433.8 GHz (HCN J = $5 \rightarrow 4$/continuum), and 421.8 GHz (continuum)." (2 Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15 m to 1.4 km  
  > "in a configuration with baselines ranging from 15 m to 1.4 km" (2 Observations and Data Reduction)
- angular resolution: Band 7 beam 0.244" x 0.175"; Band 8 beam 0.177" x 0.125"  
  > "The beam size was 0.244" x 0.175" with a position angle of 0.34$^\circ$." (2 Observations and Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: ~1.5 mJy/beam (Band 7) and ~1.1 mJy/beam (Band 8) per 20 km/s channel  
  > "The 1 $\sigma$ noise in a cleaned 20 km/s spectral channel is $\sim$1.1 mJy/beam." (2 Observations and Data Reduction)
- time on source: 4 min (Band 7, 38 antennas); 102 min (Band 8, 51 antennas)  
  > "The total on-source integration time was 102 minutes using 51 antennas." (2 Observations and Data Reduction)
- observing dates: Band 7: 17 Aug 2016; Band 8: 29-30 Jul and 17-18 Aug 2016  
  > "on July 29$^{th}$ and 30$^{th}$ of 2016 as well as on August 17$^{th}$ and 18$^{th}$ of 2016" (2 Observations and Data Reduction)
- pi or archival as stated: _not stated_
- Line: 12CO J=3-2 (not stated)
- Line: 13CO J=4-3 (not stated)
- Line: SiO J=8-7 (not stated)
- Line: HCN J=5-4 (not stated)
- External data: CO J=1-0 data re-imaged with robust 0.5 and 20 km/s channels; line fluxes 47.3 and 27.8 Jy km/s used for scaling  
  > "The $^{12}$CO J = $1 \rightarrow 0$ data are that of (cite: Scoville2017), but imaged with robust = 0.5 rather than 1" (6 CO morphology versus rotational transition) [from (cite: Scoville2017)]
- External data: CO to H2 conversion factor 0.8 Msun (K km/s pc^2)^-1  
  > "using the conversion factor 0.8 M$_\odot$ (K km/s pc$^2$)$^{-1}$ (cite: DownesSolomon1998)" (5 outflow) [from (cite: DownesSolomon1998)]
- External data: L_FIR from ALMA 691 GHz continuum  
  > "Using the $L_{FIR}$ measured from the ALMA 691 GHz continuum emission from (cite: Wilson2014)." (Table 1) [from (cite: Wilson2014)]
- External data: Default LIME dust opacities  
  > "The default dust opacity values of LIME were used in the models, which are from (cite: Ossenkopf1994)." (6 LIME modeling) [from (cite: Ossenkopf1994)]

## Processing

### Calibration

- pipeline or manual: Calibrated and imaged by ALMA staff; delivered products used without additional processing  
  > "The delivered observations were found to be of high quality and are thus presented here without additional processing." (2 Observations and Data Reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Yes  
  > "The observations were flagged, calibrated, and imaged by ALMA staff prior to delivery." (2 Observations and Data Reduction)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA  
  > "Imaging and cleaning were carried out using the Common Astronomy Software Applications package CASA (cite: CASA)." (2 Observations and Data Reduction)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "The observations were imaged using Briggs weighting, with robust set to 0.5" (2 Observations and Data Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub; imcontsub for LIME comparison  
  > "Both observation sets were continuum subtracted using CASA’s uvcontsub routine." (2 Observations and Data Reduction)
- line free channels: _not stated_
- primary beam correction: Applied  
  > "All observations have been corrected for primary beam attenuation." (2 Observations and Data Reduction)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Disk axis of 17 deg for western nucleus taken from high-resolution CO 1-0 observations  
  > "17$^\circ$ is the deconvolved axis derived from the high spatial resolution observations from (cite: Scoville2017)." (6.2 Arp 220 Western Nucleus) [from (cite: Scoville2017)]
- Gaussian foreground absorber approach  
  > "To simulate the absorption, the approach from (cite: Rangwala2015) was used." (6.1.1 Foreground Absorber Model) [from (cite: Rangwala2015)]

### Not stated but needed to reproduce (our reading)

- Channel/velocity ranges used for continuum fitting and line-free channels in uvcontsub/imcontsub
- Image size, cell size, clean threshold, masks, deconvolver
- Exact velocity ranges for the outflow moment maps and HCN/other moments
- LIME setup: number of grid points, collision rate files, model image pixel size, band velocity resolution
- Distance source and inclination/PA for east disk (45 deg axis) justification
- Interactive figure data / model cubes for the LIME models are not given in text

## Analysis recipe

1. **Image and continuum-subtract**: Use ALMA-delivered products; uvcontsub (imcontsub for model comparison); Briggs robust 0.5; 20 km/s channels  
  > "The observations were imaged using Briggs weighting, with robust set to 0.5" (2 Observations and Data Reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: uvcontsub and imcontsub give same line profiles within noise  
  > "it was confirmed that the two routines produce the same line profiles within the noise levels of the observations" (2 Observations and Data Reduction)
2. **Moment maps and Gaussian fits of nuclei**: Moments 1 and 2 from pixels above 4x rms; Gaussian fits to continuum and line maps  
  > "Moments 1 and 2 were constructed utilizing only pixels with a signal greater than 4 times the rms of pixels without signal." (3.1 12CO)
   - software: CASA
   - assumption: Systemic velocity 5338 km/s for moment 1  
  > "A systemic velocity of 5338 km/s is assumed for moment 1." (3.3 13CO)
   - fitting: _not stated_
   - validation: _not stated_
3. **Outflow masses and mass loss rates**: Moment 0 of high-velocity red/blue gas; L'CO from Solomon 1992 equation; scale 3-2 to 1-0 using nuclear luminosity ratio; mass with alpha=0.8; age = corrected size / corrected velocity  
  > "an age is calculated by dividing the corrected size by the corrected velocity" (5 outflow)
   - software: CASA
   - assumption: CO-to-H2 factor 0.8 Msun (K km/s pc^2)^-1; inclination from LIME models  
  > "using the conversion factor 0.8 M$_\odot$ (K km/s pc$^2$)$^{-1}$" (5 outflow)
   - fitting: Outflow sizes fit with CASA  
  > "The sizes of the outflow were fit using CASA and are shown in Table [2](#out_table)." (5 outflow)
   - validation: _not stated_
4. **Non-LTE LIME disk modeling of nuclei**: Exponential disk density profile with uniform gas/dust temperature and turbulence, CO/H2 = 2e-4; model images convolved with beam, imcontsub, spectra compared at half-beam increments; parameters adjusted by eye  
  > "The spectra are extracted from the model images and the observations at half-beam increments along the plane of the disk as well as orthogonal to it" (6 LIME modeling)
   - software: LIME, CASA
   - parameter: Continuum integrated intensity in model matched to observations  
  > "the integrated intensity in the continuum map that is produced is required to be the same as that measured in the observations" (6 LIME modeling)
   - assumption: 12CO/13CO = 40; gas-to-dust 100; Ossenkopf & Henning dust opacities  
  > "Abundance of $^{12}$CO to $^{13}$CO$^a$" (Table 3)
   - fitting: No statistical fitting; ranges by eye  
  > "although no statistical fitting was carried out" (7 Discussion)
   - validation: Column densities compared with literature values  
  > "The agreement with these other values in the literature help validate this model against other physical measurements of Arp 220 east." (6.1.3)

## Software

- **CASA** : Imaging, continuum subtraction, beam convolution, moment maps, Gaussian fits  
  > "Imaging and cleaning were carried out using the Common Astronomy Software Applications package CASA (cite: CASA)." (2 Observations and Data Reduction)
- **LIME** : Non-LTE 3D radiative transfer disk models  
  > "LIME, the Line Modeling Engine (cite: Brinch2010), is a non-LTE spectral line radiation transfer code for 3D models in arbitrary geometries" (6 LIME modeling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Western outflow red mass | 2.0e7 | not stated | Msun | 3 | a mass of 2.0$\times$10$^7$ M$_\odot$ for the red outflow and 2.0$\times$10$^6$ M$_\odot$ for the blue outflow in the western nucleus |
| Western outflow mass loss rates red/blue | 50 and 8 | not stated | Msun/yr | 3 | the mass loss rates of 50 and 8 M$_\odot$ yr$^{-1}$ for the red and blue outflows respectively were obtained |
| Eastern outflow masses red/blue | 5e6 and 4e6 | not stated | Msun | 3 | This yields a mass of 5$\times$10$^6$ M$_\odot$ and 4$\times$10$^6$ M$_\odot$ for the red and blue outflows respectively. |
| East nucleus gas mass (LIME) | 8e8 | range 4-8e8 | Msun | 4 | $8 \cdot 10^8$, M$_\odot$ |
| West nucleus gas mass (LIME) | 1.6e9 | range 0.8-2.4e9 | Msun | 4 | $1.6 \cdot 10^9$ M$_\odot$ |
| West nucleus 13CO peak optical depth | 18 | not stated | dimensionless | 4 | a peak optical depth at the center of the western nucleus is found to be 18 |
| West nucleus central column density | 4.9e25 | not stated | H2 cm^-2 | 4 | we find a central position column density of 4.9$\times10^{25}$ H$_2$ cm$^{-2}$ |
| Extended 12CO 3-2 emission size | 3.5 arcsec (1.3 kpc) | not stated | arcsec | 2 | has a size of 3.5 arcseconds, corresponding to a physical size of 1.3 kpc |

## Qualitative findings

- Extended 12CO 3-2 emission shows m=2 tidal-like features suggesting gas inflow  
  > "morphology that is indicative of m = 2 tidal features, suggesting gas inflow" (abstract)

## Claim tuples

- H: Is the eastern nucleus line asymmetry caused by a foreground absorber, outflow, or temperature asymmetry? | E: LIME models of 12CO and 13CO line profiles at multiple positions | R: Absorber fails for 13CO; outflow fails off-axis; asymmetric temperature disk fits best | F: Temperature asymmetry best explains the eastern nucleus | **supported**
- H: Is the western nucleus optically thick even in 13CO? | E: LIME model optical depth map and central absorption | R: Peak tau 18 with dust; central dip below zero | F: 13CO 4-3 is optically thick and absorbs continuum | **supported**
- H: Are outflows present in both nuclei? | E: High-velocity 12CO 3-2 moment maps | R: Collimated outflows in both nuclei | F: First strong detection of eastern outflow | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Foreground absorber and pure outflow models rejected for the eastern nucleus asymmetry  
  > "Thus, the asymmetric line profiles observed in $^{13}$CO J = $4 \rightarrow 3$ rule out the possibility of a foreground absorber as the cause of the asymmetry." (6.1.1 Foreground Absorber Model)
- How they decided it was enough: _not stated_
- Limitation (authors): No statistical fitting; parameter ranges by eye; degenerate parameters  
  > "A more quantitative treatment was computationally too expensive." (Table 3)
- Caveat (inferred, ours): Model parameters chosen by eye with no uncertainty or goodness-of-fit estimate
- Caveat (inferred, ours): Red outflow mass contaminated by H13CN
- Caveat (inferred, ours): Single-temperature uniform disks are simplistic
- Caveat (inferred, ours): Only 4 minutes of Band 7 on-source time

## Reproducibility

- Data public (paper): ALMA project 2015.1.00736.S acknowledged; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00736.S." (Conclusions)
- Products in archive: _not stated_
- Code: LIME is public at github; interactive figures stated available online; model scripts not stated  
  > "<https://github.com/lime-rt/lime>" (6 LIME modeling)
- Missing: LIME input parameters and scripts
- Missing: Line-free channels and moment velocity ranges
- Missing: Imaging parameters beyond robust
- Data volume (inferred): ~50-100 GB for both bands
- Score (inferred): 3/5, Archival ALMA data with clear imaging basics, but LIME modeling is by-eye and scripts/parameters are incomplete.
- Rediscovery candidate: no, Main modeling results are by-eye and not reproducible without scripts, though flux and moment measurements could be redone.

## Links

- Method: (cite: Brinch2010) (LIME code)
- Companion: (cite: Scoville2017) (CO 1-0 data and ALMA Arp 220 comparison)
- Companion: (cite: Barcos2018) (Western outflow comparison)

## Checks

```json
{
 "quotes": 58,
 "quotes_ok": 58,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 41,
  "rate": 0.577
 },
 "evidence_ok": true
}
```
