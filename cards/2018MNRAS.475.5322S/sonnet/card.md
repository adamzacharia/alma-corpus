# Deuterated formaldehyde in the low-mass protostar HH212

`2018MNRAS.475.5322S` | Monthly Notices of the Royal Astronomical Society 2018 | first author: Sahu, Dipen | arXiv: 1801.06699 | DOI: 10.1093/mnras/sty190

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation, astrochemistry
- Question: Is HDCO emitted from the inner region of HH212, what does its distribution and kinematics say about its origin, and how does it compare with CH3OH, C34S and C17O?  
  > "Here, we report the HDCO (deuterated formaldehyde) line observation from ALMA data to probe the inner region of HH212." (abstract)
- Target **HH212 (MM1)**: coordinates RA(J2000)=05h43m51.41s, Dec=-01d02'53.17"  
  > "Positions are given with respect to peak continuum of the MM1 protostar located at $\alpha(J2000)= 05^h43^m51^s.41," (3 Results); "HH212 is thought to be a Class 0 object of low-mass proto stellar system, located in Orion at 400pc (cite: koun2017)." (Introduction); z/distance 400 pc  
  > "Positions are given with respect to peak continuum of the MM1 protostar located at $\alpha(J2000)= 05^h43^m51^s.41," (3 Results); "HH212 is thought to be a Class 0 object of low-mass proto stellar system, located in Orion at 400pc (cite: koun2017)." (Introduction); distance from Kounkel et al. 2017  
  > "Positions are given with respect to peak continuum of the MM1 protostar located at $\alpha(J2000)= 05^h43^m51^s.41," (3 Results); "HH212 is thought to be a Class 0 object of low-mass proto stellar system, located in Orion at 400pc (cite: koun2017)." (Introduction)

## Data provenance

- ALMA projects: 2011.0.00647.S
- bands: Band 7  
  > "The HH212 protostar system was observed with ALMA (Band -7) using 24 12m antennas on 2012 December 1" (Observations)
- frequencies and spectral setup: spectral windows 333.7-337.4 GHz and 345.6-349.3 GHz; 488 kHz (~0.43 km/s) resolution  
  > "The observed spectral windows were 333.7-337.4 GHz and 345.6-349.3 GHz" (Observations); "The datacubes have a spectral resolution 488 KHz ($\sim 0.43$ km s$^{-1}$)" (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 20 m to 360 m  
  > "the shortest and the longest baselines were respectively 20m and 360m." (Observations)
- angular resolution: 0.65" x 0.47" at PA ~49 deg  
  > "a typical beam FWHM of $0.''65 \times 0.''47$ at position angle (PA) $\sim 49^{\circ}$" (Observations)
- max recoverable scale: _not stated_
- sensitivity: 3-4 mJy/beam in 0.43 km/s channels  
  > "the typical rms level was 3-4 mJy beam$^{-1}$ in 0.43 km s$^{-1}$ channels" (Observations)
- time on source: _not stated_
- observing dates: 2012 December 1 (Cycle 0)  
  > "on 2012 December 1 (Early Science Cycle 0 phase" (Observations)
- pi or archival as stated: _not stated_
- Line: HDCO 5(1,4)-4(1,3) (335.09678 GHz)
- Line: CH3OH v0 7(1,7)-6(1,6) (335.58202 GHz)
- Line: C17O J=3-2 (337.06112 GHz)
- Line: C34S J=7-6 (337.396459 GHz)
- External data: Spectroscopic data from CDMS and JPL databases  
  > "molecular data has been taken from the CDMS (cite: muller01; muller05) and JPL molecular database (cite: pic1998)." (Introduction) [from (cite: muller01; muller05; pic1998)]
- External data: CH3CHO temperature 87±47 K  
  > "from optically thin LTE analysis of CH$_3$CHO they suggested a temperature of $87\pm47$K" (3.1 HDCO emission) [from (cite: code2016)]
- External data: Methanol D/H 2.4±0.4e-2  
  > "Methanol deuteration (D/H) for the HH212 is 2.4$\pm 0.4 \times 10^{-2}$ as reported by (cite: bian2017)." (Discussion) [from (cite: bian2017)]
- External data: X_CO/X_C17O = 1792  
  > "we use $X_{CO}/X_{C^{17}O}$=1792 (cite: wilson1994)" (3.4 disk mass) [from (cite: wilson1994)]

## Processing

### Calibration

- pipeline or manual: calibrated with CASA; quasars J0538-440 and J0607-085 passband, J0607-085 gain  
  > "The data were calibrated with the CASA package, with quasars J0538-440 and J0607-085 as the passband calibrators, quasar J0607-085 as the gain calibrator" (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Callisto and Ganymede  
  > "Callisto and Ganymede as the flux calibrators" (Observations)
- flux scale uncertainty: 20% calibration error assumed  
  > "If we consider a calibration error of 20% then the same uncertainty will be added" (3.3)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "We used Briggs weighting with robustness parameter 0.5 for CLEANing the image." (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum subtracted in visibility data  
  > "We generated spectral cubes by subtracting the continuum emission in visibility data." (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.66" x 0.47" PA 49.6 deg (HDCO)  
  > "synthesized beam size $0.66'' \times 0.47'', {\rm PA}\quad 49.6^{\circ}$" (3 Results)
- final rms: _not stated_

### Inherited from earlier work

- Source position and systemic velocity ~1.7 km/s taken from earlier work  
  > "close to the systematic velocity $\sim$1.7 km s$^{-1}$ (cite: lee2014)" (3 Results) [from (cite: lee2014)]
- Disk mass from continuum follows earlier method, beta=1, kappa0  
  > "Following earlier work (cite: tobin2012), we assume the spectral index $\beta$=1 (cite: kwon2009)" (3.4) [from (cite: tobin2012)]

### Not stated but needed to reproduce (our reading)

- CASA version
- tclean parameters other than robust (cell, image size, masks, niter, threshold)
- line-free channels for continuum subtraction
- how the continuum flux for the continuum disk mass was measured
- integration windows and Gaussian fit details for column densities
- partition function values used
- method for centroid determination
- region definitions beyond 0.5 arcsec circles

## Analysis recipe

1. **Image line cubes**: Continuum subtraction in visibilities and Briggs-weighted CLEAN  
  > "We used Briggs weighting with robustness parameter 0.5 for CLEANing the image." (Observations)
   - software: CASA
   - parameter: robust = 0.5  
  > "We used Briggs weighting with robustness parameter 0.5 for CLEANing the image." (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Channel maps and centroid positions of velocity channels**: Compare HDCO with C34S, CH3OH and C17O via channel maps and emission centroids per velocity channel  
  > "we plot centroid emission positions of various velocity channels of C$^{34}$S and HDCO line in Figure  [4]" (3.1)
   - fitting: _not stated_
   - validation: _not stated_
3. **Column densities of HDCO and C17O**: Optically thin LTE column density from integrated intensity over 0.5" circular regions, with a range of Trot  
  > "We calculate the column densities of C$^{17}$O and HDCO, assuming the lines are optically thin." (3.3)
   - parameter: Trot = 20, 40, 90, 160, 300 K  
  > "we have considered five excitation temperatures (20, 40, 90, 160, 300 K) for our calculations." (3.1)
   - parameter: source size 0.2" for beam dilution  
  > "Here, we consider source size $\sim 0.2''$." (3.3)
   - assumption: Optically thin, LTE  
  > "Here we assume the HDCO emission region to be optically thin and local thermodynamic equilibrium (LTE) condition is satisfied." (3.1)
   - fitting: Gaussian fitting of spectra for errors  
  > "The errors for column density are calculated for noise and statistical (Gaussian) fitting." (3.3)
   - validation: _not stated_
4. **Disk mass from C17O and from continuum**: C17O N to H2 via X_CO/X_C17O=1792 and X_CO~1e-4, then mass from disk geometry; cross-check with optically thin dust continuum at 90 K  
  > "With T$_{dust}$=90 K, the disk mass is 0.0159 M$_\odot$, which is close to 0.016 M$_\odot$" (3.4)
   - parameter: disk radius 90 AU, H~40 AU  
  > "We consider H$\sim 40$AU and the disk radius to be 90 AU (cite: lee2014)." (3.4)
   - assumption: beta=1, kappa0=0.035 g cm-2 at 850 um, Tdust=90 K  
  > "the dust opacity $\kappa_0$=0.035 g cm$^{-2}$ at 850 $\mu$m (cite: andrew2005)" (3.4)
   - fitting: _not stated_
   - validation: Two mass estimates agree with each other and with Lee et al. 2014  
  > "It is close to the value 0.014 M$_\odot$, estimated by (cite: lee2014)." (3.4)

## Software

- **CASA** : calibration and imaging  
  > "The data were calibrated with the CASA package" (Observations)
- **Splatalogue** : line search  
  > "The line search is performed using splatalouge (www.splatalouge.net)" (Introduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HDCO column density, region M, Trot=160 K | 5.6e14 | 22.8% | cm^-2 | 3 | / M       / 12.3            / 5.6             / 3.1             / 2.0             / ..              / 22.8% / |
| Disk mass from C17O | 0.016 | not stated | Msun | 4 | we derive the disk mass to be 0.016 M$_\odot$. |
| Disk mass from continuum (90 K) | 0.0159 | not stated | Msun | 4 | With T$_{dust}$=90 K, the disk mass is 0.0159 M$_\odot$ |
| HDCO abundance | ~1e-10 | not stated | relative to H2 | 3 | Considering the H$_2$ column density $\sim 10^{24}$cm$^{-2}$ (see next section), X$_{HDCO} \sim 10^{-10}$. |

## Qualitative findings

- HDCO emission is partially resolved, extended along the jet, and resembles the C34S X-shaped outflow cavity near systemic velocity  
  > "it is significantly similar to the C$^{34}$S emission near the systematic velocity." (3.1)

## Claim tuples

- H: Where does HDCO emission originate in HH212? | E: Maps, channel maps and centroids compared to C34S, CH3OH, C17O | R: Emission is extended and similar to C34S near systemic velocity; centroid shifts away from the disk plane | F: HDCO is associated with the outflow base rather than disk or envelope Keplerian rotation | **partially**
- H: Is gas-phase HDCO formation active in the hot corino? | E: Compare central and outflow HDCO column densities scaled by C17O | R: Central HDCO is a factor ~3 higher than expected from density scaling | F: Gas-phase HDCO formation likely active in the central region | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Only one HDCO transition, so excitation temperature cannot be derived; resolution too low to confirm rotation  
  > "Here we observe only one transition of HDCO. Thus we cannot determine the excitation temperature." (Conclusions)
- Caveat (inferred, ours): Rotation inferred from sub-beam centroid shifts of faint emission
- Caveat (inferred, ours): Column densities depend on assumed Trot and source size; deuteration comparisons with D2CO are speculative
- Caveat (inferred, ours): No H2CO observed, so the D/H claim is indirect

## Reproducibility

- Data public (paper): ALMA archival dataset 2011.0.00647.S  
  > "we use ALMA archival dataset 2011.0.00647.S" (Introduction)
- Products in archive: _not stated_
- Missing: CASA version and clean parameters
- Missing: line-free channels
- Missing: regions' exact definitions and integration ranges
- Missing: partition functions used
- Data volume (inferred): ~10-30 GB
- Score (inferred): 5/5, Public data and a simple LTE recipe with Trot grid, but imaging details and region/integration choices are missing.
- Rediscovery candidate: yes, Public archival data, stated line frequencies and formulas, numeric column densities in a table.

## Links

- Companion: Codella et al. 2014 (cite: code2014) (Original publication of the same dataset)
- Companion: Lee et al. 2017a (cite: lee2017a) (Higher-resolution D2CO and CH2DOH in HH212)

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
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 39,
  "rate": 0.549
 },
 "evidence_ok": true
}
```
