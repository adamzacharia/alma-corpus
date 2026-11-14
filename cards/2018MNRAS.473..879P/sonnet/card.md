# The ALMA early science view of FUor/EXor objects - IV. Misaligned outflows in the complex star-forming environment of V1647 Ori and McNeil's Nebula

`2018MNRAS.473..879P` | Monthly Notices of the Royal Astronomical Society 2018 | first author: Principe, David A. | arXiv: 1709.01924 | DOI: 10.1093/mnras/stx2320

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, protoplanetary_disks
- Question: What are the properties of the V1647 Ori circumstellar disc and the large-scale molecular environment and outflows traced by continuum and CO isotopologue emission?  
  > "Dust continuum and the $(J=2-1)$ $^{12}$CO, $^{13}$CO, C$^{18}$O molecular emission lines were observed to characterize the V1647 Ori circumstellar disc and any large scale molecular features present." (abstract)
- Target **V1647 Ori**: coordinates RA 05:46:13.139, Dec -00:06:04.90 (continuum centroid)  
  > "RA= 05:46:13.139, Dec= -00:06:04.90" (3.1 Continuum Emission); "a distance of 414 $\pm{7}$ pc (cite: Menten2007)" (3.1 Continuum Emission); z/distance 414 ± 7 pc  
  > "RA= 05:46:13.139, Dec= -00:06:04.90" (3.1 Continuum Emission); "a distance of 414 $\pm{7}$ pc (cite: Menten2007)" (3.1 Continuum Emission); distance from Menten2007  
  > "RA= 05:46:13.139, Dec= -00:06:04.90" (3.1 Continuum Emission); "a distance of 414 $\pm{7}$ pc (cite: Menten2007)" (3.1 Continuum Emission)

## Data provenance

- ALMA projects: 2013.1.00710.S
- bands: Band 6 (1.3 mm)  
  > "V1647 Ori was observed with ALMA band-6 at three epochs (December 12th, 2014, April 5th, 2015 and August 30th, 2015)." (2 Observations)
- frequencies and spectral setup: two 2 GHz continuum SPWs at ~232 and ~218 GHz; three 59 MHz line windows (12CO, 13CO, C18O 2-1)  
  > "two broad (2 GHz) continuum spectral windows centered at $\sim$232 GHz and $\sim$218 GHz and three narrow (59 MHz) windows" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: Two epochs with 45 antennas, 14.6-348.5 m baselines; one epoch with 35 antennas, 42-1574 m  
  > "The final epoch had a configuration of 35 antennas and longer baselines of 42-1574 meters resulting in a higher angular resolution of 0.2 $''$." (2 Observations)
- baselines: _not stated_
- angular resolution: ~1.0" (two early epochs); 0.2" (final epoch)  
  > "baselines ranging from 14.6 to 348.5 meters which achieved an angular resolution of $\sim$1.0 $''$" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: Continuum 0.80 mJy/beam (3σ); 12CO and 13CO 45, C18O 36 mJy km/s/beam (3σ)  
  > "| Continuum | 0.26$\times$0.20 | 88.0 | 0.80 \[mJy beam$^{-1}$\] |" (Table 1)
- time on source: _not stated_
- observing dates: 2014-12-12, 2015-04-05, 2015-08-30  
  > "December 12th, 2014, April 5th, 2015 and August 30th, 2015" (2 Observations)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (230.5380 GHz)
- Line: 13CO J=2-1 (220.3987 GHz)
- Line: C18O J=2-1 (219.5603 GHz)
- Other facility **Gemini-GMOS**: R-band optical image (2008) of McNeil's Nebula, from Gemini Science Archive  
  > "Optical Gemini-GMOS imaging observations of V1647 Ori were performed on September 22, 2008 with an exposure time of 60 seconds in R band." (2 Observations)
- External data: Distance 414 ± 7 pc  
  > "a distance of 414 $\pm{7}$ pc (cite: Menten2007)" (3.1 Continuum Emission) [from Menten2007]
- External data: 12CO/13CO abundance ratio of 62 and 12CO/H2 of 1e-4  
  > "adopt a $^{12}$CO to H$_{2}$ abundance ratio of 10$^{-4}$ and a $^{12}$CO to $^{13}$CO relative abundance of 62 (cite: Langer1993)" (3.6 Dynamics of the V1647 Ori Environment) [from Langer1993]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline-calibrated, then further reduced in CASA  
  > "The ALMA pipeline-calibrated observations were further reduced with the Common Astronomical Software Application (cite: McMullin2007)." (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ganymede and J0423-013  
  > "Flux calibration was performed with Ganymede and J0423-013" (2 Observations)
- flux scale uncertainty: 10% absolute flux uncertainty of Band 6  
  > "the 10% absolute flux uncertainty of ALMA Band 6" (3.1 Continuum Emission)
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
- continuum subtraction: in the visibility domain; epochs concatenated  
  > "The two epochs of $\sim$1.0$''$ resolution data were continuum subtracted in the visibility domain, concatenated, and cleaned" (2 Observations)
- line free channels: _not stated_
- primary beam correction: Images not PB-corrected; PB-corrected channel maps used for outflow parameters  
  > "The images presented in this work are not primary-beam corrected." (2 Observations)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: Continuum 0.26x0.20"; 12CO 1.61x0.98"; 13CO 1.66x1.03"; C18O 1.69x1.03"  
  > "| Continuum | 0.26$\times$0.20 | 88.0 |" (Table 1)
- final rms: _not stated_

### Inherited from earlier work

- Outflow mass/momentum/energy procedure  
  > "We follow the procedure outlined in (cite: Perez2015)" (3.6 Dynamics of the V1647 Ori Environment) [from Perez2015]
- Dust mass formula (optically thin)  
  > "following (cite: Beckwith1990)" (3.1 Continuum Emission) [from Beckwith1990]
- Dust temperature 20±10 K  
  > "a dust temperature and range of $T=20 \pm 10$ K is chosen based on the median temperature of discs in Taurus-Auriga (cite: Andrews2005)" (3.1 Continuum Emission) [from Andrews2005]
- More in-depth continuum analysis deferred  
  > "A more in-depth analysis of continuum emission from V1647 Ori as well as the other FUor/EXor objects in this series will be presented in (cite: Cieza2017)." (3.1 Continuum Emission) [from Cieza2017]

### Not stated but needed to reproduce (our reading)

- tclean parameters (weighting/robust, cell, image size, deconvolver, masks, niter, threshold)
- line-free channels for continuum subtraction
- CASA version
- channel width of the line cubes
- pipeline version
- how the pipeline calibration was done for each epoch
- phase center/field details of the concatenation
- aperture for flux and fitting details of the 2D Gaussian (imfit settings)
- values of vmax and radii used in dynamical age (measurement method)

## Analysis recipe

1. **Image continuum and lines**: CASA reduction of pipeline-calibrated data, visibility-domain continuum subtraction, concatenation of the two ~1" epochs, cleaning; separate 0.2" continuum  
  > "The two epochs of $\sim$1.0$''$ resolution data were continuum subtracted in the visibility domain, concatenated, and cleaned to form a single dataset for the continuum and each spectral line." (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Moment-0 maps**: immoments using pixels ≥3σ in blue (5.0-9.49), systemic (9.5-10.5), red (10.51-13.0 km/s) ranges  
  > "we created moment 0 images for each spectral line with three distinct velocity ranges: $5.0-9.49$ km s$^{-1}$, $9.5-10.5$ km s$^{-1}$ and $10.51-13.0$ km s$^{-1}$." (2 Observations)
   - software: CASA
   - assumption: systemic velocity ~10.0 km/s from C18O peak  
  > "we estimate a systemic velocity of $\sim$10.0 km s$^{-1}$ assuming the star forms in the densest part of the molecular cloud" (3.2 Gas Emission Lines)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit disc continuum**: 2D Gaussian fit in CASA; inclination from aspect ratio of assumed circular disc; radius from FWHM and distance  
  > "Two-dimensional gaussian fitting of the $\sim$225 GHz continuum emission performed in CASA" (3.1 Continuum Emission)
   - software: CASA
   - assumption: circular disc  
  > "The inclination was calculated using the aspect ratio of an assumed circular disc." (3.1 Continuum Emission)
   - fitting: _not stated_
   - validation: Resolved evidenced by amplitude vs UV distance  
  > "Evidence that the continuum emission from the circumstellar disc is spatially resolved is identified by its amplitude as a function of UV distance" (3.1 Continuum Emission)
4. **Disc dust and total mass**: Optically thin M = F d^2/(kappa B(T))  
  > "assuming continuum emission is thermal and optically thin" (3.1 Continuum Emission)
   - parameter: beta=1, kappa=0.023 cm2/g, T=20 K, d=414 pc  
  > "Assuming values of $\beta$=1, d= 414 pc, $\kappa_\nu$ = 0.023 cm$^{2}$ g$^{-1}$, and a dust temperature of $T=20$ K" (3.1 Continuum Emission)
   - assumption: gas to dust mass ratio of 100  
  > "assuming a gas to dust mass ratio of 100" (3.1 Continuum Emission)
   - fitting: _not stated_
   - validation: Range explored over beta 1±0.5 and T 20±10 K  
  > "the potential range in $\beta$ ($\beta$= 1 $\pm{0.5}$) and dust temperature (T = 20 $\pm{10}$)" (3.1 Continuum Emission)
5. **Extract spectra**: Spectra in 2" and 20" diameter apertures centered on V1647 Ori, 0.25 km/s bins  
  > "An aperture diameter of 2.0 $''$ was chosen to extract spectral information at the precise location of the continuum emission" (3.2 Gas Emission Lines)
   - fitting: _not stated_
   - validation: _not stated_
6. **Outflow dynamical ages**: tau = r_outflow/(v_system - v_max) per line  
  > "their maximum velocities relative to the velocity of the system" (3.6 Dynamics of the V1647 Ori Environment)
   - assumption: low inclination (17 deg) makes ages uncertain; straight-line travel  
  > "these dynamical ages are relatively uncertain given the low inclination of this system" (3.6 Dynamics of the V1647 Ori Environment)
   - fitting: _not stated_
   - validation: Two independent ages per outflow from two lines  
  > "we can estimate two independent dynamical ages for each outflow" (3.6 Dynamics of the V1647 Ori Environment)
7. **Outflow mass, momentum, energy**: Sum over channels within 10" on PB-corrected 12CO and 13CO cubes  
  > "for each velocity channel within a radius of 10$''$ of V1646 Ori" (3.6 Dynamics of the V1647 Ori Environment)
   - assumption: Tex=50 K, filling factor 1, 12CO/H2=1e-4, 12CO/13CO=62  
  > "This analysis assumes a constant excitation temperature of T$_\mathrm{ex}$ = 50 K along the line of sight and a beam filling factor of 1." (3.6 Dynamics of the V1647 Ori Environment)
   - fitting: _not stated_
   - validation: No optical depth correction; 12CO values are lower limits  
  > "the $^{12}$CO parameters estimated in this work (Table [\[momentum_table\]](#momentum_table)) are lower limits" (3.6 Dynamics of the V1647 Ori Environment)

## Software

- **CASA** : Reduction, imaging, immoments, 2D Gaussian fitting  
  > "Integrated intensity images (moment 0) were creating using the CASA routine $immoments$." (2 Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum flux (~225 GHz) | 82.62 | 8.26 | mJy | 3 | a flux, inclination, position angle and centroid of 82.62 $\pm$ 8.26 mJy |
| Disc inclination | 17 | +6/-9 | deg | 3 | ${\it i} = 17^{\circ}$ $^{+6}_{-9}$ |
| Disc dust radius | ~40 | not stated | au | 3 | results in a disc dust radius of $\sim$40 au |
| Disc dust mass | 427 | range 110-2688 | Earth masses | 4 | we estimate the disc dust mass of V1647 Ori to be $M_\mathrm{dust}$ = 427 M$_\mathrm{E}$ |
| Total disc mass | 0.13 | range 0.03-0.80 | Msun | 4 | total disc mass $M_\mathrm{disc}$ = 0.13 $M_{\odot}$ |
| Dynamical age, northern outflow | ~11,700 | ~200 | yr | 6 | has a dynamical age of $\sim$11,700 years |
| Dynamical age, southern outflow | ~17,200 | ~300 | yr | 6 | has a dynamical age of $\sim$17,200 years |
| 12CO total outflow mass (lower limit) | 33.7e-3 | not stated | Msun | 7 | / Total /  15.3 /  33.7 /  55.2 /  100.1 / |
| 13CO total outflow mass | 15.3e-3 | not stated | Msun | 7 | / Total /  7.5 / 15.3 / 14.2 / 15.3 / |

## Qualitative findings

- Blueshifted 12CO cavity coincides with McNeil's Nebula base; dense systemic C18O shapes surrounding gas; redshifted 12CO 'arm' links to a large structure ~20" west.  
  > "The V1647 Ori system is seemingly connected by an "arm" of material to a large unresolved structure located $\sim$20$''$ to the west." (abstract)

## Claim tuples

- H: Does a companion or fragmentation drive the outbursts? | E: Inspect 0.2" continuum image | R: No spirals or clumps seen | F: Companions or fragmentation beyond ~40 au are unlikely | **supported**
- H: Are the two outflows misaligned due to disc precession? | E: Compare PAs and dynamical ages of 13CO/C18O and 12CO/13CO outflows | R: PA 330 and 180 deg, ages ~11,700 and ~17,200 yr | F: Disc precession from anisotropic accretion is most plausible | **partially**
- H: Are outflow velocities slower than predicted? | E: Measure vmax in the CO lines | R: ~1-2 km/s | F: Slower than typical outflows | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Disc warping rejected (R_crit = 2e6 au); tidal companion unlikely; inflow interpretation unlikely  
  > "it is unlikely a disc warp is the origin of its misaligned outflows" (4.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Dynamical ages uncertain at low inclination; 12CO values lower limits; western structure may be artifact outside primary beam  
  > "we caution that this feature may be an artifact from emission outside the primary beam" (4.3)
- Caveat (inferred, ours): Dust temperature and beta assumed, giving a mass range spanning ~25x
- Caveat (inferred, ours): Systemic velocity assumed from C18O
- Caveat (inferred, ours): Outflow velocity with i=17 deg not inclination-corrected
- Caveat (inferred, ours): No error bars on outflow masses

## Reproducibility

- Data public (paper): Project code given; ALMA data  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA #2013.1.00710.S ." (Acknowledgements)
- Products in archive: _not stated_
- Missing: tclean settings
- Missing: line-free channels
- Missing: vmax measurement details
- Missing: CASA version
- Data volume (inferred): ~50-100 GB raw for three epochs
- Score (inferred): 3/5, Data identifiable and analysis simple, but imaging parameters are not given.
- Rediscovery candidate: yes, Public project, simple numerical results (flux, mass, ages), though imaging details must be guessed.

## Links

- Method: Perez2015 (outflow mass/momentum procedure)
- Method: Beckwith1990 (dust mass equation)
- Companion: Zurlo2017; Ruiz-Rodriguez2017a; Ruiz-Rodriguez2017b; Cieza2017 (other FUor/EXor targets in the same ALMA program)
- Related: ALMA Cycle 2 FUor/EXor program (PI L. Cieza)

## Checks

```json
{
 "quotes": 65,
 "quotes_ok": 65,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 81,
  "stated": 45,
  "rate": 0.556
 },
 "evidence_ok": true
}
```
