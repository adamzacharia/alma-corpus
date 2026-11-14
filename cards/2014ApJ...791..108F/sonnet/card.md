# Distributed Low-mass Star Formation in the IRDC G34.43+00.24

`2014ApJ...791..108F` | The Astrophysical Journal 2014 | first author: Foster, Jonathan B. | arXiv: 1407.6003 | DOI: 10.1088/0004-637X/791/2/108

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation, milky_way_ism
- Question: Is there a distributed population of low-mass protostars in the IRDC G34.43+00.24, and do low-mass stars form before or with high-mass stars in the filament?  
  > "We find a population of distributed low-mass protostars, suggesting that low-mass protostars may form earlier than, or contemporaneously with, high-mass protostars in such a filament." (abstract)
- Target **G34.43+00.24**: coordinates _not stated_; z/distance 3.9 kpc  
  > "we adopt the kinematic/extinction distance of 3.9 kpc for this cloud." (Introduction); distance from kinematic/extinction distance (parallax 1.56 kpc rejected)  
  > "we adopt the kinematic/extinction distance of 3.9 kpc for this cloud." (Introduction)

## Data provenance

- ALMA projects: _none stated_
- bands: ALMA Band 6 (1.3 mm), Cycle 0  
  > "These observations were carried out during ALMA Cycle 0 using ALMA Band 6." (2.5 Continuum Submillimeter/Millimeter Data)
- frequencies and spectral setup: four 234 MHz basebands between 228 and 245 GHz; continuum from line-free channels  
  > "averaging the line-free channels of the four 234 MHz basebands between 228 and 245 GHz, which gives the continuum at 1.3 mm." (2.5 Continuum Submillimeter/Millimeter Data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.82"x0.61" synthesized beam  
  > "The synthesized beam is 0$''$.82$\times$0$''$.61 and the rms noise in the continuum image is 0.3-0.4 mJy beam$^{-1}$." (2.5 Continuum Submillimeter/Millimeter Data)
- max recoverable scale: _not stated_
- sensitivity: rms 0.3-0.4 mJy/beam  
  > "the rms noise in the continuum image is 0.3-0.4 mJy beam$^{-1}$." (2.5 Continuum Submillimeter/Millimeter Data)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **Keck II NIRC2 (AO)**: Deep H and K imaging of 7 fields  
  > "The near-infrared images were taken using NIRC2 on Keck II with adaptive optics." (2.1 H and K Imaging with Keck)
- Other facility **UKIDSS GPS**: Wide-field NIR catalog, background luminosity function  
  > "We used Data Release 8 downloaded from the WFCAM Science Archive." (2.2 UKIDSS GPS)
- Other facility **IRTF SpeX**: K-band spectra of extended sources  
  > "we obtained near-infrared spectra of the brightest extended $K$ band sources in Field 6 using SPeX on the IRTF." (2.3 K band Spectra with IRTF)
- Other facility **GBT KFPA**: NH3 (1,1) and (2,2) maps for line widths  
  > "This cloud was mapped in January, 2011 with the para-NH$_3$ (1,1) and (2,2) inversion transitions" (2.4 NH3 with the GBT)
- Other facility **Herschel Hi-GAL and IRAM 30m MAMBO**: Dust temperature and column density maps  
  > "in order to derive the column density of the cloud." (2.5 Continuum Submillimeter/Millimeter Data)
- External data: ALMA Cycle 0 Band 6 continuum data of Field 6 (MM3)  
  > "we compare with the ALMA observations presented in (cite: Sakai:2013)" (2.5 Continuum Submillimeter/Millimeter Data) [from (cite: Sakai:2013)]
- External data: MAMBO 1.2 mm map  
  > "the MAMBO IRAM 30 m dust continuum map at 1.2 mm from (cite: Rathborne:2006)" (2.5 Continuum Submillimeter/Millimeter Data) [from (cite: Rathborne:2006)]
- External data: Protostar candidates and masses from Spitzer SED fits  
  > "The protostellar mass estimates from (cite: Shepherd:2007) are from fitting the *Spitzer* fluxes to the (cite: Robitaille:2006) model grid" (6.4 Distributed versus Clustered Star Formation) [from (cite: Shepherd:2007)]
- Simulation/model as data: Besancon stellar model for background star counts with 1.5 mag/kpc diffuse extinction  
  > "We include 1.5 mag of visual extinction per kpc as the diffuse extinction component in this model." (4.2 Overdensities of Red Sources)

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

- ALMA observations, reduction and continuum image taken from Sakai et al.  
  > "we compare with the ALMA observations presented in (cite: Sakai:2013)" (2.5 Continuum Submillimeter/Millimeter Data) [from (cite: Sakai:2013)]
- NH3 hyperfine forward modeling for line width  
  > "under the assumption of a homogeneous slab with uniform intrinsic velocity dispersion and excitation conditions for all hyperfine transitions (cite: Rosolowsky:2008)" (3.2 Line Width from NH3) [from (cite: Rosolowsky:2008)]

### Not stated but needed to reproduce (our reading)

- ALMA project code and calibration/imaging details (CASA version, weighting, deconvolution) for the Cycle 0 data
- Flux scale uncertainty of ALMA data
- Coordinates of target and ALMA field center

## Analysis recipe

1. **dust temperature from Herschel**: Per-pixel graybody fit with Ossenkopf & Henning opacities, not optically thin, at 37" resolution  
  > "For each pixel, we fit for the dust temperature using a graybody fit" (3.1 Dust Temperature from Herschel)
   - software: HIPE
   - assumption: gas-to-dust 100:1, mu_H2 = 2.8, single temperature along line of sight  
  > "We used $\mu_{\mathrm{H_2}} = 2.8$ and $\kappa_{\nu}$ as explained above." (3.1 Dust Temperature from Herschel)
   - fitting: _not stated_
   - validation: _not stated_
2. **column density map from MAMBO**: Convert 1.2 mm flux to N using Herschel temperature; kappa = 0.0102 cm2/g  
  > "For the MAMBO data $\lambda = 1200\, \mu$m, $\theta_{\mathrm{HPBW}} =$ 11$''$, and $\kappa_{\nu} = 0.0102~$(cm$^{2}$ g$^{-1}$) (cite: Ossenkopf:1994)." (Column Density from MAMBO)
   - assumption: N_H2 = 9.4e20 cm^-2 A_V; A_K = 0.118 A_V  
  > "A_K = 0.118 A_V," (3.3 Column Density from MAMBO)
   - fitting: _not stated_
   - validation: _not stated_
3. **identify red-source overdensities**: Poisson probability of red sources vs Besancon background after extinction correction, 11" radius, significance <0.5%  
  > "We define significance as less than a 0.5% chance that the red sources in this region could be reproduced by background stars." (4.2 Overdensities of Red Sources)
   - software: Source Extractor
   - parameter: H-K > 2 mag red cut  
  > "adopting a limit of $H-K > 2$ mag is a good conservative estimate" (4.2 Overdensities of Red Sources)
   - fitting: _not stated_
   - validation: Agreement with extended K-band sources  
  > "provides an important independent validation of this statistical method." (4.1 Extended K-band Sources)
4. **virial parameter along filament**: alpha = 84 (dV)^2/(M/l) in 11" steps with median NH3 FWHM  
  > "adopting a fixed length step of 11$''$, the resolution of our column density map, and using the median $\Delta V$" (3.4 Estimating the Dynamical State of the Filament)
   - assumption: isothermal cylinder; ignores magnetic fields and external pressure  
  > "This analysis ignores magnetic fields and the influence of external pressure" (3.4 Estimating the Dynamical State of the Filament)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **Source Extractor** : aperture photometry  
  > "Aperture photometry was performed using Source Extractor (cite: Bertin:1996)" (2.1 H and K Imaging with Keck)
- **Spextool** : SpeX spectra reduction  
  > "Reduction was performed using Spextool" (2.3 K band Spectra with IRTF)
- **HIPE** v9.2: Herschel data reduction  
  > "(HIPE v9.2)" (2.5 Continuum Submillimeter/Millimeter Data)
- **Astropy** : general analysis  
  > "This research made use of Astropy" (Acknowledgements)
- **APLpy** : plotting  
  > "This research made use of APLpy" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Jeans length near Overdensity B/MM3 | 0.15 | not stated | pc | 0 | $\lambda_J$ = 0.15 pc or 3.1$\times10^4$ AU |
| Column density in MM3 and Overdensity B | ~0.1 | not stated | g cm^-2 | 2 | Our estimated column densities in MM3 and Overdensity B are roughly 0.1 g cm$^{-2}$ |
| Virial parameter of high-mass protostar regions | <0.2 | not stated | dimensionless | 4 | the high-mass protostars seem to be found in the most bound portions of the cloud ($\alpha$ $<$ 0.2) |

## Qualitative findings

- Most of the filament has alpha < 1 except the ends, so it is globally bound.  
  > "The majority of the cloud has $\alpha < 1$, except at the ends of the filament, suggesting that the cloud is globally bound." (3.4 Estimating the Dynamical State of the Filament)

## Claim tuples

- H: Low-mass protostars are distributed between clumps in the IRDC | E: Red-source overdensity analysis and extended K-band sources in Keck and UKIDSS | R: Overdensities A, B, C and nine extended K-band sources found | F: Distributed low-mass protostars exist in the inter-clump medium | **supported**
- H: High-mass protostars form in the most bound filament portions | E: Virial parameter per unit length vs Spitzer protostar masses | R: High-mass protostars at alpha < 0.2 | F: Qualitative suggestion only | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: VERA parallax distance 1.56 kpc rejected in favor of 3.9 kpc  
  > "we adopt the kinematic/extinction distance of 3.9 kpc for this cloud." (Introduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Mass uncertain by at least a factor of two from opacity; distance conflict; no magnetic or external pressure  
  > "The emissivity, $\kappa$, and hence the mass, is uncertain by at least a factor of two." (6.4 Distributed versus Clustered Star Formation)
- Caveat (inferred, ours): ALMA data only used qualitatively for comparison
- Caveat (inferred, ours): Protostar identification is statistical and distance dependent

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA project code and reduced images
- Missing: Besancon model run setup
- Missing: Keck reduced images
- Data volume (inferred): Small for the ALMA part (one Cycle 0 continuum field); full study needs Keck, UKIDSS, Herschel, GBT data
- Score (inferred): 2/5, ALMA is minor and taken from another paper; most data are non-ALMA and details are partial.
- Rediscovery candidate: no, ALMA role is a qualitative comparison and the main results rely on non-ALMA data.

## Links

- Method: (cite: Rosolowsky:2008) (NH3 hyperfine fitting)
- Method: (cite: Ossenkopf:1994) (dust opacities)
- Companion: (cite: Sakai:2013) (source of the ALMA Cycle 0 observations)
- Related: Herschel Hi-GAL
- Related: UKIDSS GPS

## Checks

```json
{
 "quotes": 41,
 "quotes_ok": 41,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00656.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 35,
  "rate": 0.449
 },
 "evidence_ok": true
}
```
