# Rings and filaments: The remarkable detached CO shell of U Antliae

`2017A&A...605A.116K` | Astronomy and Astrophysics 2017 | first author: Kerschbaum, F. | arXiv: 1708.02915 | DOI: 10.1051/0004-6361/201730665

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars
- Question: Characterize the detached-shell carbon star U Ant morphologically and physically to study mass-loss evolution after a possible thermal pulse  
  > "Our goal is to characterize the intermediate age, detached shell carbon star U Antliae morphologically and physically in order to study the mass-loss evolution after a possible thermal pulse." (abstract)
- Target **U Antliae**: coordinates _not stated_; z/distance 260 pc  
  > "this object (260 pc from *Hipparcos*) had a spatially extended detached dust shell with a radius of about 50$''$" (Introduction); distance from Hipparcos  
  > "this object (260 pc from *Hipparcos*) had a spatially extended detached dust shell with a radius of about 50$''$" (Introduction)

## Data provenance

- ALMA projects: _none stated_
- bands: Band 3 and Band 6  
  > "in band 3 (B3) and band 6 (B6), targeting the $^{12}$CO(J=1–0) and $^{12}$CO(J=2–1) lines." (Observations and data reduction)
- frequencies and spectral setup: B3 CO(1-0) at 115.271 GHz, 244.019 kHz resolution = 0.635 km/s; B6 CO(2-1) at 230.538 GHz, same velocity resolution  
  > "using a spectral resolution of 244.019 kHz, which corresponds to a velocity resolution of 0.635 km/s." (Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: 12 m array (MA), 7 m ACA, and total power (TP)  
  > "short-baseline observations with the 7 m-array (ACA) and single-dish measurements with the total power (TP) array to recover all spatial scales were carried out." (Observations and data reduction)
- configurations: intermediate and compact 12 m configurations; mosaics of 23 (B3) and 85 (B6) pointings covering 110''x110''  
  > "The CSE of U Ant was covered by a mosaic of 23 and 85 individual pointings in B3 and B6, respectively, resulting in a map of 110$''$$\times$110$''$." (Observations and data reduction)
- baselines: _not stated_
- angular resolution: 1.82''x1.63'' (PA=80.5°) CO(1-0); 1.37''x1.00'' (PA=86.6°) CO(2-1)  
  > "The beam sizes in the reduced maps are 1.82$''$ $\times$1.63$''$  (PA=80.5$^\circ$) for CO(1–0) and 1.37$''$ $\times$1.00$''$  (PA=86.6$^\circ$) for CO(2–1)." (Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO J=1-0 (115.271 GHz)
- Line: 12CO J=2-1 (230.538 GHz)
- Other facility **Herschel PACS 70 micron**: Dust shell contours compared with ALMA CO moment 0  
  > "mapped onto polar coordinates with Herschel PACS 70 $\mu$m contours (cite: Kerschbaum2010; Cox2012)" (Morphology of the detached shell)
- External data: Herschel PACS 70 micron images used for comparison  
  > "mapped onto polar coordinates with Herschel PACS 70 $\mu$m contours (cite: Kerschbaum2010; Cox2012)" (Morphology of the detached shell) [from (cite: Kerschbaum2010; Cox2012)]
- External data: Single-dish CO data used in the radiative transfer modelling  
  > "to model the ALMA data as well as the existing single-dish data in a preliminary analysis" (Recent and older mass loss) [from (cite: Schoeier2005)]

## Processing

### Calibration

- pipeline or manual: CASA pipeline scripts as delivered, no major adjustments  
  > "The calibration was done with the Common Astronomy Software Application (CASA) pipeline scripts as delivered to the principal investigator and no major adjustments needed to be done." (Observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Mars and Ganymede  
  > "Flux calibrators for the individual data sets were Mars and Ganymede" (Observations and data reduction)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CLEAN in CASA via custom python scripts, iterative and interactive  
  > "These scripts make use of an iterative and interactive imaging procedure with the CLEAN algorithm" (Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: Briggs, robustness = 0.5  
  > "using Briggs weighting (with robustness = 0.5), multi-scale cleaning, and iterative masking with decreasing thresholds" (Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: iterative masks with decreasing thresholds, adapted by hand  
  > "our strategy employs more mask iterations with finer thresholds and the CLEAN masks are carefully adapted where necessary." (Observations and data reduction)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: MA and ACA combined in the uv-plane; TP added via feathering  
  > "the TP single-dish data were added via feathering." (Observations and data reduction)
- smoothing: velocity binning to 1 km/s for final products  
  > "velocity binning to 1 km/s was applied during the imaging to increase the signal-to-noise ratio in the fainter parts of the shell." (Observations and data reduction)
- final beam: 1.82''x1.63'' (B3), 1.37''x1.00'' (B6)  
  > "The beam sizes in the reduced maps are 1.82$''$ $\times$1.63$''$  (PA=80.5$^\circ$)" (Observations and data reduction)
- final rms: _not stated_

### Inherited from earlier work

- Radiative transfer method, code, CO abundance and shell temperature follow Schöier et al. 2005  
  > "We use the same method and code here to model the ALMA data as well as the existing single-dish data in a preliminary analysis" (Recent and older mass loss) [from (cite: Schoeier2005)]
- CO photodissociation results used in the model  
  > "the (cite: Mamon1988) results for the photodissociation of CO that are used in the model" (Recent and older mass loss) [from (cite: Mamon1988)]
- Thermal-pulse high-luminosity timescale adopted as shell formation timescale  
  > "we adopt the timescale of the high-luminosity phase during a thermal pulse, a few $\times$ 10$^2$ yr (cite: karakaslattanzio2007)" (Recent and older mass loss) [from (cite: karakaslattanzio2007)]

### Not stated but needed to reproduce (our reading)

- Number of MA/ACA execution blocks and observing dates
- Multi-scale scales, clean thresholds, cell and image size
- Feathering parameters and TP scaling
- CASA version
- Line-free channels and continuum subtraction
- Radiative transfer code name and version, and model grid or fit procedure
- Details of the weighting used when combining MA and ACA
- Aperture and method for expansion velocity measurement

## Analysis recipe

1. **Recalibrate and reimage MA+ACA+TP data**: CASA pipeline calibration; MA and ACA combined in uv-plane; custom iterative CLEAN with multi-scale; TP feathered  
  > "The calibrated data sets of the MA and ACA were combined in the uv-plane with appropriate weighting." (Observations and data reduction)
   - software: CASA
   - parameter: Briggs robust = 0.5; 1 km/s velocity binning  
  > "using Briggs weighting (with robustness = 0.5), multi-scale cleaning, and iterative masking with decreasing thresholds" (Observations and data reduction)
   - fitting: _not stated_
   - validation: Thorough analysis suggests TP inclusion does not alter data significantly  
  > "thorough analysis suggests that the TP inclusion via this process does not alter the data significantly." (footnote 3)
2. **Measure shell morphology, radius, expansion velocity and age**: Inspect channel maps near systemic velocity, polar-coordinate maps and integrated spectra; compute expansion age from radius, velocity and distance  
  > "At a distance of 260 pc this corresponds to an expansion age of about 2700 years and a physical radius of 0.05 pc." (Morphology of the detached shell)
   - assumption: Distance 260 pc  
  > "At a distance of 260 pc this corresponds to an expansion age of about 2700 years" (Morphology of the detached shell)
   - fitting: _not stated_
   - validation: _not stated_
3. **Model present-day mass loss and shell mass**: Radiative transfer model following Schöier et al. 2005, fitted to ALMA radial brightness profiles and single-dish data  
  > "A present-day mass-loss rate of 4$\times$10$^{-8}$ $M_\odot$ yr$^{-1}$ (twice that of (cite: Schoeier2005)) and a shell mass of 2$\times$10$^{-3}$ M$_\odot$" (Recent and older mass loss)
   - assumption: CO/H2 = 1e-3; shell kinetic temperature 200 K  
  > "we assume a CO abundance with respect to H$_2$ of 10$^{-3}$, and for the shell a kinetic temperature of 200 K (not well constrained)" (Recent and older mass loss)
   - fitting: _not stated_
   - validation: Reasonably good fit to all data including ALMA radial brightness distributions; red/blue peak contrast not reproduced  
  > "The line intensity contrast between the red- and blue-shifted peaks of the shell emission cannot be reproduced by the model." (Recent and older mass loss)
4. **Estimate mass-loss rate during shell ejection**: Shell mass divided by assumed formation timescale of a few hundred years  
  > "we estimate an average mass-loss rate during the ejection of the shell of the order of $\approx$ 10$^{-5}$ $M_\odot$ yr$^{-1}$." (Recent and older mass loss)
   - assumption: Shell formation timescale equals thermal pulse high-luminosity phase, a few x 10^2 yr  
  > "we adopt the timescale of the high-luminosity phase during a thermal pulse, a few $\times$ 10$^2$ yr" (Recent and older mass loss)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibration pipeline and custom imaging scripts (CLEAN)  
  > "these scripts were executed in CASA" (Observations and data reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Detached shell radius | 42.5 | not stated | arcsec | 2 | detached CO shell of about 42.5$''$ radius expanding at a velocity of about 19 km/s |
| Shell expansion velocity | 19 | not stated | km/s | 2 | detached CO shell of about 42.5$''$ radius expanding at a velocity of about 19 km/s |
| Shell expansion age | 2700 | not stated | yr | 2 | corresponds to an expansion age of about 2700 years and a physical radius of 0.05 pc |
| Present-day expansion velocity (B3, B6) | 4.7 and 4.2 | not stated | km/s | 2 | shows much smaller expansion velocities of only 4.7 and 4.2 km/s in B3 and B6, respectively |
| Present-day mass-loss rate | 4e-8 | not stated | Msun/yr | 3 | A present-day mass-loss rate of 4$\times$10$^{-8}$ $M_\odot$ yr$^{-1}$ |
| Shell mass | 2e-3 | not stated | Msun | 3 | a shell mass of 2$\times$10$^{-3}$ M$_\odot$ |
| Mass-loss rate during shell ejection | ~1e-5 | order of magnitude | Msun/yr | 4 | we estimate an average mass-loss rate during the ejection of the shell of the order of $\approx$ 10$^{-5}$ $M_\odot$ yr$^{-1}$. |

## Qualitative findings

- Shell is thin, overall spherically symmetric, with barely resolved filaments splitting up to 5''  
  > "In several regions the shell is split into two basically unresolved filaments differing in radius by up to 5$''$." (Morphology of the detached shell)
- Gas shell is co-spatial with shell 3 and not dust shell 4; partial anti-correlation of dust and gas brightness  
  > "This partial anti-correlation is surprising since possible photodissociation effects would act the other way round" (Morphology of the detached shell)

## Claim tuples

- H: The detached shell is thin and spherical with substructure | E: ALMA B3 and B6 CO mosaics, MA+ACA+TP | R: Radius 42.5'', width small, filaments split up to 5'' | F: Short high mass-loss period ~2700 yr ago lasting a few hundred years | **supported**
- H: Filaments result from instabilities in wind interaction | E: Compared channel maps and spectra with hydrodynamic models from literature | R: Morphological similarity with instabilities in wind-ISM interaction | F: Plausible but needs full hydrodynamical models | **partially**
- H: Mass loss declined after the thermal pulse | E: Central-aperture spectra and radiative transfer model | R: Present-day v_exp ~4.5 km/s, 4e-8 Msun/yr vs 1e-5 during ejection | F: Consistent with predicted interpulse evolution | **supported**

## Reasoning

- Why this data: Single-dish and optical/IR data lack spatial resolution or velocity information  
  > "a complete picture is hampered by the low spatial resolution of the single dish mm-CO data, and the lack of velocity information in the optical and IR observations." (Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Feathering is imperfect and may introduce artefacts  
  > "The authors are aware of the fact that the resulting images may contain artefacts" (footnote 3)
- Limitation (authors): Modelling is preliminary; photodissociation of material between star and shell not considered  
  > "a substantial amount of emission from material between the star and the detached shell may be missing due to photodissociation of CO" (Recent and older mass loss)
- Caveat (inferred, ours): Mass-loss rate during ejection rests on an assumed timescale
- Caveat (inferred, ours): No fit uncertainties given for model parameters
- Caveat (inferred, ours): Filament splitting is near the resolution limit
- Caveat (inferred, ours): Feathering artefacts possible

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: Reduced FITS cubes available at CDS  
  > "The reduced ALMA FITS data cubes used in this paper are available in electronic form at the CDS" (footnote 2)
- Missing: Custom imaging scripts
- Missing: Radiative transfer code configuration and fit details
- Missing: CASA version
- Data volume (inferred): Several hundred GB raw for two bands with mosaics of MA, ACA and TP
- Score (inferred): 4/5, Data and pipeline calibration are clear and cubes are public, but imaging parameters and the model setup are sparse.
- Rediscovery candidate: no, The imaging recipe is incomplete and modelling is preliminary, so numeric results are hard to reproduce precisely.

## Links

- Method: (cite: Schoeier2005) (Radiative transfer method and code used for modelling)
- Companion: (cite: Maercker2016) (ALMA study of the detached shell of R Scl for comparison)

## Checks

```json
{
 "quotes": 52,
 "quotes_ok": 52,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2015.1.00007.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 39,
  "rate": 0.557
 },
 "evidence_ok": true
}
```
