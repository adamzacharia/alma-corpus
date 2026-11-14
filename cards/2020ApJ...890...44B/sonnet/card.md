# ALMA Observations Reveal No Preferred Outflow-filament and Outflow-magnetic Field Orientations in Protoclusters

`2020ApJ...890...44B` | The Astrophysical Journal 2020 | first author: Baug, T. | arXiv: 1912.13240 | DOI: 10.3847/1538-4357/ab66b6

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism
- Question: Do CO(3-2) outflow lobes in 11 massive protoclusters in H II regions have preferred orientations relative to host filaments, large-scale magnetic fields, or the Galactic plane?  
  > "The primary aim of our study is to examine whether the orientation of outflow lobes have a dependence on large-scale filamentary accretion and also with the orientation of the magnetic fields or Galactic plane." (3.2 Identification of host clouds and filaments)
- Target **11 IRAS protoclusters (IRAS 14382-6017 to IRAS 17220-3609)**: coordinates e.g. IRAS 14382-6017: 14 42 02, -60 30 35 (J2000); others in Table 1  
  > "IRAS 14382-6017 | 14 42 02 | -60 30 35 | -60.55 | 4.1$\pm$0.6 | 65 | 71$\pm$4 | 66" (Table 1); "These distances were estimated using a python-based ‘Kinematic Distance Calculation Tool’ of (cite: wenger18)" (Introduction); z/distance 2.6-7.6 kpc (near kinematic distances)  
  > "IRAS 14382-6017 | 14 42 02 | -60 30 35 | -60.55 | 4.1$\pm$0.6 | 65 | 71$\pm$4 | 66" (Table 1); "These distances were estimated using a python-based ‘Kinematic Distance Calculation Tool’ of (cite: wenger18)" (Introduction); distance from Kinematic Distance Calculation Tool (Wenger et al. 2018), VLSR from Liu et al. 2016b  
  > "IRAS 14382-6017 | 14 42 02 | -60 30 35 | -60.55 | 4.1$\pm$0.6 | 65 | 71$\pm$4 | 66" (Table 1); "These distances were estimated using a python-based ‘Kinematic Distance Calculation Tool’ of (cite: wenger18)" (Introduction)

## Data provenance

- ALMA projects: 2017.1.00545.S
- bands: Band 7  
  > "The observations were obtained in four spectral windows in Band 7 (centering at 343.2, 345.1, 354.4, and 356.7 GHz)" (2.1 ALMA observations)
- frequencies and spectral setup: CO(3-2) in 345.1 GHz band; 1.88 GHz baseband, 1.13 MHz resolution  
  > "A baseband of 1.88 GHz with spectral resolution of 1.13 MHz was used for the CO (3–2) observations." (2.1 ALMA observations)
- continuum bandwidth: _not stated_
- arrays: 43 12 m antennas, C43-1  
  > "using 43 12 m antennas in C43-1 configuration" (2.1 ALMA observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.8''x0.7''  
  > "resulted a final synthesized beam size of 0.8$''$$\times$0.7$''$" (2.1 ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: 8.3 mJy/beam per 1 km/s channel  
  > "The average cube sensitivity is 8.3 mJy beam$^{-1}$ with 1 km s$^{-1}$ wide velocity channels." (2.1 ALMA observations)
- time on source: _not stated_
- observing dates: 2018 May 18-20 (Cycle 5)  
  > "Observations of these targets were carried out from 2018 May 18 to 2018 May 20 (UTC) (ALMA Cycle 5)" (2.1 ALMA observations)
- pi or archival as stated: PI: Tie Liu  
  > "under the project 2017.1.00545.S (PI: Tie Liu)" (2.1 ALMA observations)
- Line: CO J=3-2 (not stated)
- Other facility **ThrUMMS (Mopra)**: 13CO(1-0) maps used to identify host clouds and filaments  
  > "we used publicly available $^{13}$CO ($J = 1-0$) line maps of the Three-mm Ultimate Mopra Milky Way Survey (cite: barnes15)" (2.2 Molecular line data)
- Other facility **ATLASGAL (APEX)**: 870 um continuum for filament identification  
  > "The ATLASGAL images were also used for our target regions to identify the filamentary structures." (2.3 Submillimeter data)
- Other facility **Planck**: 353 GHz dust polarization for magnetic field PA  
  > "we obtained the *Planck* [^1], 353 GHz (850$\mu$m) dust continuum polarization data (cite: planck16a)" (2.4 Dust polarization data)
- External data: VLSR of targets  
  > "The local standard of rest velocities ($v_\mathrm{lsr}$) were obtained from (cite: liu16b)." (Introduction) [from Liu et al. 2016b (cite: liu16b)]
- External data: Galactocentric solar distance 8.31±0.16 kpc  
  > "adopting the solar Galactocentric distance of 8.31$\pm$0.16 kpc (cite: reid14)" (Introduction) [from Reid et al. 2014 (cite: reid14)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 5.1.1  
  > "using the tclean task in CASA 5.1.1" (2.1 ALMA observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Self-calibration performed  
  > "We performed self-calibration and cleaned the data cube using the tclean task in CASA 5.1.1." (2.1 ALMA observations)

### Imaging

- task: tclean in CASA 5.1.1  
  > "cleaned the data cube using the tclean task in CASA 5.1.1" (2.1 ALMA observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "Briggs weighting with a robust number of 0.5 was used" (2.1 ALMA observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Cubes averaged to 5 km/s channels for outflow identification  
  > "These smaller data cubes were also averaged to a resolution of 5 km s$^{-1}$ (i.e., 5 channels of original data cube)" (3.1 Identification of Outflows)
- final beam: 0.8''x0.7''  
  > "resulted a final synthesized beam size of 0.8$''$$\times$0.7$''$" (2.1 ALMA observations)
- final rms: 8.3 mJy/beam per 1 km/s channel  
  > "The average cube sensitivity is 8.3 mJy beam$^{-1}$ with 1 km s$^{-1}$ wide velocity channels." (2.1 ALMA observations)

### Inherited from earlier work

- Monte Carlo projection-effect methodology for gamma_Fil  
  > "The detailed methodology can be found in (cite: stephens17)." (3.5 Orientation of Outflows and Filaments) [from Stephens et al. 2017 (cite: stephens17)]
- 0.9 mm continuum images and catalog of driving sources, deferred to a forthcoming paper  
  > "Details on the identification of continuum sources and their analyses will be presented in a forthcoming paper." (2.1 ALMA observations) [from forthcoming paper]

### Not stated but needed to reproduce (our reading)

- Self-calibration solution intervals and reference antennas
- Calibrator assignments are incompletely given (flux calibrator not named)
- Image size, cell size, deconvolver, masks and clean threshold
- Line-free channels and continuum subtraction method
- filfinder threshold parameters
- Exact outflow velocity ranges and lobe PA measurement procedure
- Averaging area/pixel selection for Planck PAs
- 0.9 mm continuum map processing

## Analysis recipe

1. **Identify outflow lobes**: Crop cubes to ±200 km/s, average to 5 km/s, visually inspect for red/blue lobes around continuum sources, then check original cubes; lobe extent to 5 sigma  
  > "The peak velocity and extent of each outflow were considered up to a 5$\sigma$ level where $\sigma$ is the rms measured from a few line-free channels." (3.1 Identification of Outflows)
   - software: CASA
   - parameter: ±200 km/s around systemic velocity; 5 km/s channels  
  > "we cropped the observed ALMA data cubes for each region into smaller cubes that only cover $\pm$200 km s$^{-1}$ centering on the systematic velocity of each targets." (3.1 Identification of Outflows)
   - fitting: _not stated_
   - validation: HCN and SiO used to confirm confusing lobes  
  > "other outflow tracers of outflows (e.g., HCN, SiO) were used to confirm a few confusing outflow lobes." (3.1 Identification of Outflows)
2. **Identify host filaments and PA_Fil**: filfinder skeletons on ThrUMMS 13CO / ATLASGAL maps; PA by visual fit averaged over at least 5 pixels of skeleton  
  > "we only considered the large scale PAs of filaments estimated by a visual fit over the large-scale filfinder skeletons." (3.2 Identification of host clouds and filaments)
   - software: filfinder
   - parameter: Elongated clumps with aspect ratio <5 also treated as filamentary  
  > "We also considered elongated clumps (aspect ratio $<$ 5) as filamentary structure" (3.2 Identification of host clouds and filaments)
   - fitting: _not stated_
   - validation: Typical PA uncertainty ≲10 deg; ±10 deg random perturbation test  
  > "visual fits to these large-scale PA$_\mathrm{Fil}$ have typical uncertainty $\lesssim$10$\ensuremath{^\circ}$" (3.2 Identification of host clouds and filaments)
3. **Derive magnetic field PA from Planck**: Stokes Q,U to PA via 0.5 arctan(-U,Q), add 90 deg, convert to equatorial using Corradi et al. 1998, average within cloud extent  
  > "we have estimated the mean magnetic field orientation using the $\theta_{B}$ vectors distributed within the area of the clouds identified in the previous section." (3.3 Magnetic field position angle)
   - fitting: _not stated_
   - validation: _not stated_
4. **Compute lobe-filament/B-field/Galactic plane angles**: gamma = MIN{|PA_lobe - reference|, |PA_lobe - reference| - 90 deg}, range 0-90 deg; histograms and cumulative histograms  
  > "$\gamma_{B} = \mathrm{MIN}\{|\mathrm{PA}_\mathrm{lobe} - \theta_{B}|, |\mathrm{PA}_\mathrm{lobe} - \theta_{B}| - 90\ensuremath{^\circ}\}$" (3.5 PA_lobe with respect to magnetic field and Galactic plane)
   - fitting: _not stated_
   - validation: _not stated_
5. **Test against projected 3D distributions**: Monte Carlo of 2e6 random unit-vector pairs; CDFs of projected angle for parallel (0-20), perpendicular (70-90), random (0-90) gamma_3D; K-S test vs observed CDF  
  > "we randomly generated 2$\times$10$^6$ radially outward pairs of unit vectors on the surface of a sphere." (3.5 Orientation of Outflows and Filaments)
   - fitting: K-S test against random and random+10% preferred (10-40 deg)  
  > "Both the tests produce $p-$values more than 0.8" (4 Discussion)
   - validation: _not stated_

## Software

- **CASA** 5.1.1: self-calibration and tclean imaging  
  > "We performed self-calibration and cleaned the data cube using the tclean task in CASA 5.1.1." (2.1 ALMA observations)
- **filfinder** : tracing filament skeletons  
  > "Python-based filfinder algorithm (cite: koch15) was applied on all the identified molecular clouds to trace the filamentary structures." (3.2 Identification of host clouds and filaments)
- **Kinematic Distance Calculation Tool** : kinematic distances  
  > "These distances were estimated using a python-based ‘Kinematic Distance Calculation Tool’ of (cite: wenger18)" (Introduction)
- **Astropy** : acknowledged as used in research  
  > "This research made use of Astropy, a community-developed core Python package for astronomy (cite: astropy18)." (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of outflow lobes | 105 | not stated | lobes | 1 | We finally identified a total of hundred and five outflow lobes. |
| Targets embedded in filaments | 7 of 11 | not stated | targets | 2 | Filaments are detected toward 7 targets |
| Outflow lobes in filament regions | 49 | not stated | lobes | 4 | These 7 targets contain a total of 49 outflow lobes. |
| Typical dynamical timescale | 5e3 | not stated | yr | 1 | the typical dynamical time-scale is about 5$\times$10$^3$ yr |
| K-S p-values | >0.8 | not stated | dimensionless | 5 | Both the tests produce $p-$values more than 0.8 |
| Extra fraction with preferred gamma_3D 10-40 deg | 10% | not stated | percent | 5 | the observed distribution $\gamma_\mathrm{Fil}$ can be reproduced if additional 10% sources in a random distribution have preferred $\gamma_\mathrm{3D}$ values from 10$\ensuremath{^\circ}$ to 40$\ensuremath{^\circ}$ |

## Qualitative findings

- Outflow lobes show no preferred orientation relative to filaments, B-field, or Galactic plane; the gamma_Fil distribution is consistent with random.  
  > "The random distribution suggests a lack of alignment of outflows with filaments, which may be a result of the evolutionary stage of the clusters." (abstract)

## Claim tuples

- H: Outflows in evolved massive protoclusters are preferentially perpendicular or parallel to host filaments | E: Measured gamma_Fil for 49 lobes in 7 filament regions; compared CDF with Monte Carlo projected models and K-S | R: CDF follows random distribution; K-S p>0.8 | F: No preferred outflow-filament orientation | **supported**
- H: Outflows are aligned with large-scale magnetic field or Galactic plane | E: Compared PA_lobe with Planck-derived B PA and Galactic plane PA | R: No specific trend in gamma_B or gamma_GP histograms | F: No correlation | **supported**
- H: Orientation depends on evolutionary stage | E: Contrast with IRDC results of Wang et al. and Kong et al. | R: H II region protoclusters show random orientation unlike IRDCs | F: Outflow axes might depend on protocluster age | **partially**

## Reasoning

- Why this data: Targets selected from H II regions with strong blue-profile HCN(4-3), ideal for infall and outflows  
  > "These particular 11 targets among them showed strong blue-emission profile of HCN (4–3) which is an efficient tracer of infalling gas." (Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Visual filament PA fit is less accurate than a statistical fit; Planck traces only large-scale field  
  > "Note that a visual fit to filaments might not be as accurate as a statistical fit." (3.2 Identification of host clouds and filaments)
- Caveat (inferred, ours): Small sample (49 lobes in 7 regions) with lobes treated as independent despite shared driving sources
- Caveat (inferred, ours): K-S p>0.8 does not prove randomness; low power
- Caveat (inferred, ours): Planck 5' beam vs 0.8'' ALMA scale
- Caveat (inferred, ours): Plane-of-sky PA only; filament scale ~pc vs outflow scale 0.1 pc

## Reproducibility

- Data public (paper): ALMA project cited; ThrUMMS, ATLASGAL, Planck described as public  
  > "we used publicly available $^{13}$CO ($J = 1-0$) line maps" (2.2 Molecular line data)
- Products in archive: _not stated_
- Missing: Outflow lobe identification is visual and subjective
- Missing: filfinder parameters
- Missing: Self-calibration details
- Missing: Continuum catalog deferred to a forthcoming paper
- Data volume (inferred): ~100-300 GB raw ALMA for 11 fields, plus small ancillary maps
- Score (inferred): 4/5, Data public and statistics simple, but outflow and filament identification are visual with unstated parameters.
- Rediscovery candidate: no, Key measurements depend on subjective visual identification and missing parameters.

## Links

- Method: Koch & Rosolowsky 2015 (cite: koch15) (filfinder algorithm)
- Method: Stephens et al. 2017 (cite: stephens17) (Monte Carlo projection methodology)
- Method: Wenger et al. 2018 (cite: wenger18) (kinematic distances)
- Companion: Liu et al. 2016b (cite: liu16b) (parent sample of H II regions)
- Related: ThrUMMS
- Related: ATLASGAL
- Related: Planck

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
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 43,
  "rate": 0.589
 },
 "evidence_ok": true
}
```
