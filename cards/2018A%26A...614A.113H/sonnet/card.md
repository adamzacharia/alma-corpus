# ALMA detection of a tentative nearly edge-on rotating disk around the nearby AGB star R Doradus

`2018A&A...614A.113H` | Astronomy and Astrophysics 2018 | first author: Homan, Ward | arXiv: 1803.06207 | DOI: 10.1051/0004-6361/201732246

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars
- Question: Does the spatial offset between blue and red shifted molecular emission in R Dor's inner wind indicate a compact rotating disk, and what are its properties and possible companion?  
  > "we investigate a peculiar feature seen in various molecular transitions of ALMA (cycle 2) Band 7 observations of (hereafter R Dor), which suggest the presence of a compact rotating disk in its inner wind." (1 Introduction)
- Target **R Doradus**: coordinates _not stated_; z/distance 59 pc  
  > "At a distance of only 59 pc (cite: Knapp2003), R Dor is the nearest AGB star to our Sun." (1 Introduction); distance from Knapp et al. 2003  
  > "At a distance of only 59 pc (cite: Knapp2003), R Dor is the nearest AGB star to our Sun." (1 Introduction)

## Data provenance

- ALMA projects: 2013.1.00166.S
- bands: Band 7  
  > "R Doradus was observed with ALMA in Band 7 in August and September 2015" (2.1 Observations)
- frequencies and spectral setup: full spectral scan 335–362 GHz, four 1.875 GHz wide spectral windows per observation  
  > "A full spectral scan between 335–362 GHz was made using four separate observations." (2.1 Observations); "Each observation used four 1.875 GHz wide spectral windows." (2.1 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 0.04–1.6 km  
  > "The range of baseline lengths was 0.04–1.6 km" (2.1 Observations)
- angular resolution: ~150 mas  
  > "allowing imaging of structures on angular scales up to 200 mas at angular resolution $\sim$150 mas." (2.1 Observations)
- max recoverable scale: up to 200 mas  
  > "allowing imaging of structures on angular scales up to 200 mas" (2.1 Observations)
- sensitivity: continuum noise 40 μJy  
  > "the current noise level in the continuum (40 $\mu$Jy)" (4.2)
- time on source: _not stated_
- observing dates: August and September 2015, over 5 days  
  > "The observations took place over 5 days using standard ALMA procedures." (2.1 Observations)
- pi or archival as stated: proposal 2013.1.00166.S, PI L. Decin  
  > "(proposal 2013.1.00166.S, PI L. Decin)" (2.1 Observations)
- Line: 28SiO v=1, J=8→7 (not stated)
- Line: 30SiO v=0, J=8→7 (not stated)
- Line: CO J=3→2 (not stated)
- Line: SO N_J=8_9→7_8 (not stated)
- Other facility **SPHERE**: polarimetric imaging of inner wind, dust disk inner rim 3–6 AU (Khouri2016)  
  > "the pattern is located at a distance of 50 - 100 mas from the star, placing the dust disk’s inner rim at an absolute distance of 3 - 6 AU" (2.2)
- External data: SiO abundance [SiO/H2] = 6e-5 and dust emission model  
  > "The molecular abundance of \[SiO/H$_{\rm 2}$\] = 6$\times$10$^{\rm -5}$ has been taken from (cite: VanDeSande2017)." (3) [from (cite: VanDeSande2017)]
- External data: SiO spectroscopic data from LAMDA  
  > "we adopt the spectroscopic data in the LAMDA database (cite: Schoier2005)" (3) [from (cite: Schoier2005)]
- External data: SiO collisional rates  
  > "the collisional rates are taken from (cite: Yang2010)" (3) [from (cite: Yang2010)]
- External data: stellar blackbody 2500 K and 1 Msun  
  > "emitting as a black body with a temperature of 2500 K and with a mass of 1 $\,{\rm M}_\odot$ (cite: Danilovich2017)" (3) [from (cite: Danilovich2017)]

## Processing

### Calibration

- pipeline or manual: standard scripts in CASA  
  > "following standard scripts for the application of calibration from instrumental measurements such as system temperature and water vapour radiometry" (2.1 Observations)
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

- Detailed observation and data reduction  
  > "A detailed overview of the observation and reduction specificities are provided in (cite: Decin2018)" (2.1 Observations) [from (cite: Decin2018)]
- Disk density prescription and assumed disk height parameters  
  > "Following (cite: Homan2017), its density is described by the analytical solution for a thin, non-self-gravitating, vertically isothermal disk in hydrostatic equilibrium" (3) [from (cite: Homan2017)]

### Not stated but needed to reproduce (our reading)

- CASA version and imaging parameters (weighting, cell, deconvolution)
- continuum subtraction and line-free channels
- flux calibrator names
- LIME settings (number of grid points, photons) and CASA simulation configuration
- exact stellar velocity/lsr used and PV extraction details
- continuum peak position

## Analysis recipe

1. **Stereograms of blue vs red emission**: Sum blue and red channels separately about lsr velocity and overplot  
  > "we separate the channels on the blue shifted side of the lsr velocity from the red shifted channels for a given transition, sum the respective emission separately and overplot the results." (2.2)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Determine position angle and PV diagrams**: Orthogonal pairs of PV diagrams at 5° intervals through image centre; slit width one resolution element, plus 0.9" wide slit  
  > "we made orthogonal pairs of position-velocity (PV) diagrams with axes at $5^\circ$ intervals through the centre of the image." (2.2)
   - parameter: PA 25° and 115°, uncertainty ~5°  
  > "The uncertainty on these estimates is $\sim5^\circ$." (2.2)
   - fitting: _not stated_
   - validation: _not stated_
3. **Disk radiative transfer modelling**: 3D NLTE LIME model of sub-Keplerian disk, passed through CASA observation simulation, compared to PV diagrams  
  > "we aim to reproduce the observed three-dimensional emission distribution by assuming a differentially rotating disk." (3)
   - software: LIME, CASA
   - parameter: radial velocity 1 km/s, turbulence 1 km/s, temperature power-law index -0.5  
  > "The disk temperature is assumed to be a simple power-law with an index of $-$0.5." (3)
   - assumption: gas-to-dust mass ratio 100  
  > "with an assumed gas-to-dust mass ratio of 100" (3)
   - assumption: 1 Msun central star  
  > "with a mass of 1 $\,{\rm M}_\odot$ (cite: Danilovich2017)" (3)
   - fitting: Manual parameter tuning, no formal fit  
  > "whose values have been varied until a reasonable visual resemblance between the model and the data was achieved." (3.1)
   - validation: Visual comparison of PV diagrams; checked LIME level populations for no masing  
  > "We found no indication that the optical depth $\tau$ has become negative at any position or iteration" (3)
4. **Disk mass, angular momentum, companion mass**: Integrate density over volume; angular momentum assuming conservation; companion mass assuming ~30% transfer efficiency  
  > "Having estimated the disk density, we can calculate its mass (to first order) by integrating over the volume." (3.1)
   - assumption: angular momentum transfer efficiency ~30%  
  > "Assuming an angular momentum transfer efficiecy of $\sim$30% (cite: Nordhaus2006; Nordhaus2007)" (4.1)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : data reduction and simulating observations  
  > "All data reduction was done using `CASA` (cite: McMullin2007)" (2.1 Observations)
- **LIME** : 3D NLTE radiative transfer  
  > "Using the 3D non-local-thermodynamical-equilibrium (NLTE) radiative transfer code `LIME` (cite: Brinch2010)" (3)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| disk mass | 3e-6 (6e24 kg) | not stated | Msun | 4 | We recover a disk mass amounting to approximately $6 \times 10^{24} \rm kg$ or $3 \times 10^{-6} \,{\rm M}_\odot$. |
| disk angular momentum | 5e40 | not stated | m^2 kg/s | 4 | This amounts to approximately $5 \times 10^{40}\ {\rm m^2 kg/s}$. |
| inner rim radius | 6 | not stated | AU | 3 | corresponds to an inner rim location of $\sim$6 AU |
| inclination | 110 | 20 | deg | 3 | we assume an uncertainty of 20$^\circ$ on the inclination angle |
| radial density power index p | -2.8 | ~15% | dimensionless | 3 | we estimate an uncertainty on the slope of $\sim$15% or $p=-3\pm0.5$ |
| companion minimum mass | 1.5e25 kg (~2.5 Earth masses) | not stated | kg | 4 | a companion with a mass of at least $1.5 \times 10^{25} \rm kg$ or only about 2.5 earth masses at a distance of 6 AU |
| disk position angle | 115 | ~5 | deg | 2 | around a position angle (PA) of $25^\circ$ |

## Qualitative findings

- Blue blob lacks HCN and continuum counterpart  
  > "Though HCN emission is strong throughout in the CSE of R Dor, it is, surprisingly, altogether lacking in the blob." (4.2)

## Claim tuples

- H: Offset red/blue emission indicates a compact nearly edge-on rotating disk | E: PV diagrams of 28SiO v=1 and LIME disk model | R: Model reproduces global PV shape; disk inclined 110°, inner rim 6 AU, 3e-6 Msun | F: A tentative sub-Keplerian disk is present | **partially**
- H: Disk angular momentum requires a companion | E: Compare disk angular momentum to stellar one | R: Companion of at least 2.5 Earth masses at 6 AU | F: Angular momentum problem solved by a planetary companion | **partially**
- H: The blue blob is associated with a companion planet | E: Compare blob velocity and chemistry with disk inner-rim velocity | R: Mean ~13 km/s vs 12 km/s disk maximum; no HCN, no continuum | F: May be linked to a companion planet | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: 28SiO v=1 chosen for strong spatial confinement avoiding contamination  
  > "does not exhibit extended emission that would otherwise severely contaminate the signal" (2.2)
- Alternative: Blob could be part of an accelerated wind or chemically dissimilar clump  
  > "An increased terminal wind speed would imply that the blob may indeed be part of the wind" (4.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Parameters tuned visually; no statement on fit quality  
  > "Hence, we can make no statements about the quality of the ‘fit’." (3.1)
- Limitation (authors): Insufficient spatial resolution limits kinematics  
  > "the insufficient spatial resolution of the data imposes some important limitations on this analysis" (3.2)
- Caveat (inferred, ours): No formal fit or uncertainties; degenerate parameters
- Caveat (inferred, ours): Disk interpretation at ~2 beams resolution is tentative
- Caveat (inferred, ours): Assumed temperature profile unconstrained
- Caveat (inferred, ours): Maser-prone line used to set inner rim

## Reproducibility

- Data public (paper): ALMA data acknowledged by project code  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA2013.0.00166.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging parameters and CASA version
- Missing: LIME model setup details and simulated observation configuration
- Missing: Reduction details are in Decin et al. 2018
- Data volume (inferred): ~100s GB (full spectral scan, 4 execution blocks)
- Score (inferred): 3/5, Public data and model parameters in a table, but imaging and modelling details are sparse and the fit is by eye.
- Rediscovery candidate: no, Modelling is manual and lacks complete settings; reduction details are deferred to another paper.

## Links

- Method: (cite: Homan2017) (disk density model and angular-momentum analysis)
- Method: (cite: Homan2016) (theoretical PV diagram predictions for inclined disks)
- Companion: (cite: Decin2018) (full data reduction and line survey)
- Companion: (cite: Khouri2016) (SPHERE polarimetry of R Dor)
- Related: L2 Puppis ALMA disk

## Checks

```json
{
 "quotes": 55,
 "quotes_ok": 55,
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
  "facts": 73,
  "stated": 38,
  "rate": 0.521
 },
 "evidence_ok": true
}
```
