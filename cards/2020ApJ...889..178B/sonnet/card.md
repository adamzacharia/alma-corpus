# The Orion Protostellar Explosion and Runaway Stars Revisited: Stellar Masses, Disk Retention, and an Outflow from the Becklin-Neugebauer Object

`2020ApJ...889..178B` | The Astrophysical Journal 2020 | first author: Bally, John | arXiv: 2001.00899 | DOI: 10.3847/1538-4357/ab65f2

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation
- Question: What masses of the runaway stars Src I, BN and Src x follow from center-of-mass momentum constraints, do the radio knots near BN trace an outflow from BN, and did the disks survive the ejection?  
  > "The proper motions of the three stars ejected from Orion’s OMC1 cloud core are combined with the requirement that their center of mass is gravitationally bound to OMC1" (abstract)
- Target **Orion OMC1 (BN, Src I, Src x)**: coordinates BN 5:35:14.110 -5:22:22.70 (J2000)  
  > "We adopt a distance of 400 pc to the OMC1 core, the explosive outflow and associated stars and use this value in all calculations." (Introduction); "| BN | 5:35:14.110 | $-$5:22:22.70 |" (Table 2); z/distance 400 pc  
  > "We adopt a distance of 400 pc to the OMC1 core, the explosive outflow and associated stars and use this value in all calculations." (Introduction); "| BN | 5:35:14.110 | $-$5:22:22.70 |" (Table 2); distance from adopted, between radio parallax values of Menten2007, Kim2008 and Kounkel2017  
  > "We adopt a distance of 400 pc to the OMC1 core, the explosive outflow and associated stars and use this value in all calculations." (Introduction); "| BN | 5:35:14.110 | $-$5:22:22.70 |" (Table 2)

## Data provenance

- ALMA projects: 2016.1.00165.S, 2013.1.00546.S
- bands: Band 6 (1.3 mm) and up to 3 mm continuum  
  > "No compact 1.3 to 3 mm source brighter than 0.1 mJy/beam is seen in the 0.03$''$ resolution ALMA continuum images" (A Slow Radio Jet from BN?)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.03'' continuum images (1.3 mm)  
  > "The 1.3 mm flux limit is $\sim$0.1 mJy in a 0.03$''$ beam." (A Slow Radio Jet from BN?)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **JVLA 6 GHz (2012, 2016)**: Radio proper motions and fluxes of knots near BN  
  > "In 2012, 30 hours of on-source data was acquired over five days in two 1 GHz-wide bands centered at 4.7 and 7.3 GHz." (Observations and Analysis)
- Other facility **Subaru, Gemini South, AAT, APO 3.5 m**: Multi-epoch near-IR images for Src x proper motion  
  > "| Gemini-S | 30 Dec 2012 - 28 Feb 2013 | $\sim$56321 | 1.644, 2.12 $\mu$m | (cite: Bally2015) |" (Table 1)
- External data: Proper motions of BN and Src I  
  > "For Src I and BN, the most reliable proper motion determinations are those of (cite: Rodriguez2017)" (Results) [from (cite: Rodriguez2017)]
- External data: Proper motion of Src x (HST)  
  > "for Src x, the best determinations are the HST-based measurements of (cite: Luhman2017)" (Results) [from (cite: Luhman2017)]
- External data: Src I mass of ~15 Msun from ALMA disk rotation curve  
  > "(cite: Ginsburg2018) derived a mass of $\sim$15$\pm$2 M$_{\odot}$ for Src I." (Introduction) [from (cite: Ginsburg2018)]
- External data: 850 um dust map of Orion A for OMC1 mass  
  > "We use the 850 $\mu$m dust continuum map of Orion A from (cite: Lane2016)" (Constraints on Stellar Masses) [from (cite: Lane2016)]

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

- Orion reference frame defined by mean motion of 79 radio stars  
  > "determined from the mean motion of 79 radio stars which defines a reference frame" (Constraints on Stellar Masses) [from (cite: Dzib2017)]
- 2016 JVLA 6 GHz data  
  > "We use 6 GHz JVLA images obtained on 2016 November 27 (cite: Forbrich2019)" (Observations and Analysis) [from (cite: Forbrich2019)]

### Not stated but needed to reproduce (our reading)

- ALMA data processing, imaging parameters and CASA version
- Details of how the ALMA upper limits were measured
- Proper motion fitting method for the VLA knots (deferred to Vargas-Gonzalez et al. in prep.)
- Registration uncertainties of IR images

## Analysis recipe

1. **Center-of-mass constraint on masses**: Compute CoM velocity of BN, Src I, Src x over grids of masses with proper motion errors, requiring CoM speed below OMC1 escape/circular speed  
  > "We used these measurements and their errors to compute the motion of the center of mass (CoM) on the plane of the sky of the three ejected stars" (Constraints on Stellar Masses)
   - parameter: Mx 1-4, MBN 8-18, MI 5-25 Msun  
  > "the mass of Src I is allowed to vary from $M_I$ = 5 to 25 M$_{\odot}$ in increments of 1 M$_{\odot}$" (Constraints on Stellar Masses)
   - assumption: OMC1 at rest in ONC frame; D = 400 pc  
  > "It is assumed that OMC1 is stationary in the reference frame defined by stars in Orion Nebula Cluster." (Constraints on Stellar Masses)
   - fitting: _not stated_
   - validation: Error circles from varying speeds and position angles  
  > "results in an error circle with a radius of about 0.6 km s$^{-1}$" (Constraints on Stellar Masses)
2. **Predict Src x radial velocity**: Momentum conservation with radial velocities and masses  
  > "it can be estimated from momentum conservation combined with the radial velocities and masses of BN and Src I" (Constraints on the Radial Velocity of Src x)
   - fitting: _not stated_
   - validation: _not stated_
3. **Electron densities of radio knots**: Optically thin free-free emission measure from 6 GHz flux densities  
  > "Thus, we assume that the radio continuum emission is produced by optically thin bremsstrahlung." (Electron Densities of the 6 GHz Features Near BN)
   - assumption: Line-of-sight depth equals minor axis  
  > "assume that for non-round features, the line-of-sight depth is comparable to the minor axis size of the region under consideration" (Electron Densities of the 6 GHz Features Near BN)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : listed in software section; use not described  
  > "CASA (cite: McMullin2007), IRAF" (Software)
- **IRAF GEOMAP/GEOTRAN** : registering IR images to the 2013 epoch  
  > "IRAF routines GEOMAP and GEOTRAN were used to match the infrared images listed in Table 1 to the 2013 data." (Observations and Analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Predicted Src x LSR radial velocity | -28 | ±10 | km/s | 2 | constrain the radial velocity of Src x to be $\rm V_{LSR} = -28 \pm 10$ km s$^{-1}$ |
| Src I mass | ~15 | not stated | Msun | 1 | Src I) is likely to have a mass around 15 M$_{\odot}$ |
| CoM motion error circle (all varied) | 0.6 | not stated | km/s | 1 | results in an error circle with a radius of about 0.6 km s$^{-1}$ |
| Gravitational radius of Src I | 128 | not stated | AU | 0 | $R_G \approx$ 128 AU |
| Electron densities of knots | 10^4 to ~10^5 | not stated | cm^-3 | 3 | Thus the electron densities range from $10^4$ to about $10^5$ cm$^{-3}$ |

## Qualitative findings

- No compact 1.3 mm sources (>0.1 mJy) at the radio knots, so they likely trace ejecta rather than stars  
  > "None of these radio features contain compact 1.3 mm sources in the ALMA continuum image." (A Slow Radio Jet from BN?)

## Claim tuples

- H: Src I mass is constrained by the CoM argument | E: CoM motion grid over masses with proper motions | R: Src I ~15 Msun needed | F: Consistent with ALMA disk rotation mass | **supported**
- H: Radio knots near BN trace an outflow from BN | E: VLA proper motions, ALMA/IR/X-ray non-detections, densities | R: Knots move away from BN at 28-45 km/s, no stellar counterparts | F: Collimated outflow from BN younger than 500 yr | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Knots as low-luminosity protostars or clumps ejected in the explosion  
  > "We consider three possible interpretations for these radio features near BN." (A Slow Radio Jet from BN?)
- How they decided it was enough: _not stated_
- Limitation (authors): Largest uncertainty is the poorly constrained mass of Src x  
  > "the largest uncertainty is caused by the relatively poorly constrained mass of Src x" (Constraints on Stellar Masses)
- Caveat (inferred, ours): Summary gives Src x V_LSR -23 while abstract and text give -28
- Caveat (inferred, ours): ALMA role is only an upper limit with no processing described
- Caveat (inferred, ours): Velocity-dependent conclusions depend on assumed 400 pc distance

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA imaging details
- Missing: VLA proper motions from in-prep paper
- Data volume (inferred): tens of GB if ALMA data reprocessed
- Score (inferred): 3/5, The CoM analysis is reproducible from tabulated values, but the ALMA part is only a stated non-detection with no processing details.
- Rediscovery candidate: no, ALMA role is minor and processing is not described.

## Links

- Method: (cite: FariasTan2018) (N-body ejection simulations and CoM mass constraints)
- Companion: (cite: Ginsburg2018) (ALMA Src I disk rotation curve mass)
- Companion: (cite: Forbrich2016) (2012 JVLA 6 GHz data)

## Checks

```json
{
 "quotes": 39,
 "quotes_ok": 39,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 26,
  "rate": 0.382
 },
 "evidence_ok": true
}
```
