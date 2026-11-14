# A Substellar-mass Protostar and its Outflow of IRAS 15398-3359 Revealed by Subarcsecond-resolution Observations of H<SUB>2</SUB>CO and CCH

`2014ApJ...795..152O` | The Astrophysical Journal 2014 | first author: Oya, Yoko | arXiv: 1410.5945 | DOI: 10.1088/0004-637X/795/2/152

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: What are the outflow inclination and the infalling/rotating envelope structure and protostellar mass of the Class 0 WCCC source IRAS 15398-3359, and is there a rotationally supported disk?  
  > "it is interesting to investigate whether the envelope of IRAS 15398–3359 has a similar structure." (1 Introduction)
- Target **IRAS 15398-3359**: coordinates 15h43m02.24s, -34d09m06.7s (continuum peak, J2000)  
  > "IRAS 15398–3359 is a low-mass Class 0 protostar in the Lupus 1 molecular cloud at a distance of $155$ pc (Lombardi et al. 2008)." (1 Introduction); "The continuum peak is: ($\alpha_{2000}, \delta_{2000}) = (15^{\rm h} 43^{\rm m} 02.24s, -34\ensuremath{^\circ} 09^\prime 06.7\ensuremath{''})$." (2 Observations); z/distance 155 pc  
  > "IRAS 15398–3359 is a low-mass Class 0 protostar in the Lupus 1 molecular cloud at a distance of $155$ pc (Lombardi et al. 2008)." (1 Introduction); "The continuum peak is: ($\alpha_{2000}, \delta_{2000}) = (15^{\rm h} 43^{\rm m} 02.24s, -34\ensuremath{^\circ} 09^\prime 06.7\ensuremath{''})$." (2 Observations); distance from Lombardi et al. 2008  
  > "IRAS 15398–3359 is a low-mass Class 0 protostar in the Lupus 1 molecular cloud at a distance of $155$ pc (Lombardi et al. 2008)." (1 Introduction); "The continuum peak is: ($\alpha_{2000}, \delta_{2000}) = (15^{\rm h} 43^{\rm m} 02.24s, -34\ensuremath{^\circ} 09^\prime 06.7\ensuremath{''})$." (2 Observations)

## Data provenance

- ALMA projects: 2011.0.00628.S, 2011.0.00777.S
- bands: Band 7 (0.8 mm)  
  > "Spectral lines of H$_2$CO and CCH were observed with the Band 7 receiver at frequencies of $349$–$352$ GHz, and $364$ GHz." (2 Observations)
- frequencies and spectral setup: 122 kHz resolution, 469 MHz bandwidth, 0.1 km/s velocity resolution at 366 GHz  
  > "The backend correlator was tuned to a resolution of $122$ kHz and a bandwidth of $469$ MHz, which corresponds to the velocity resolution of $0.1$ km s$^{-1}$ at $366$ GHz." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 13 to 338 m, 25 antennas  
  > "Twenty-five antennas were used in the observations, where the baseline length ranged from $13$ to $338$ m." (2 Observations)
- angular resolution: 0.60"x0.44" (H2CO); 0.70"x0.46" (combined CCH)  
  > "$0.60\ensuremath{''} \times 0.44\ensuremath{''}$ (P.A. $= 46\ensuremath{^\circ}$) for the H$_2$CO image." (2 Observations)
- max recoverable scale: emission over >12" not reliable due to lack of short baselines  
  > "the emission extending over scales of $12^{\prime \prime}$ or larger is not reliable due to the lack of short baselines." (3.1 Overall Distribution of H$_2$CO and CCH)
- sensitivity: rms 0.001 Jy/beam continuum, 0.01 Jy/beam H2CO, 0.015 Jy/beam CCH combined  
  > "The rms noise levels for the continuum and H$_2$CO emission are $0.001$ and $0.01\ {\rm Jy\ beam}^{-1}$, respectively." (2 Observations)
- time on source: 27 min H2CO, 21 min CCH  
  > "The total on-source time was $27$ minutes for H$_2$CO and $21$ minutes for CCH." (2 Observations)
- observing dates: 2012 December 31  
  > "Observations of IRAS 15398–3359 were carried out with ALMA in Cycle 0 operations on 2012 December 31." (2 Observations)
- pi or archival as stated: _not stated_
- Line: H2CO 5_15-4_14 (351.7686450 GHz)
- Line: H2CO 5_05-4_04 (362.7360480 GHz)
- Line: H2CO 5_24-4_23 (363.9458940 GHz)
- Line: CCH N=4-3, J=7/2-5/2, F=4-3 (349.3992756 GHz)
- Line: CCH N=4-3, J=7/2-5/2, F=3-2 (349.4006712 GHz)
- External data: Envelope mass 0.5 Msun  
  > "an envelope mass of $0.5\ M_\odot$ (Kristensen et al. 2012)" (4 Discussion) [from Kristensen et al. 2012]
- External data: Luminosity L = 1.8 Lsun  
  > "$L = 1.8\ L_\odot$ (Jørgensen et al. 2013)" (4 Discussion) [from Jørgensen et al. 2013]
- External data: Outflow dynamical timescale 1-2e3 yr per lobe  
  > "the dynamical timescale of the extended outflow ($1$–$2 \times 10^3$ yr for each lobe; U.A., Yıldız et al. submitted to A&A)" (4 Discussion) [from Yıldız et al. 2014, submitted to A&A]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Mars and Titan  
  > "whereas the absolute flux density scale was derived from Mars and Titan, respectively." (2 Observations)
- flux scale uncertainty: <10%  
  > "uncertainties are less than $10 \%$." (2 Observations)
- self calibration: _not stated_

### Imaging

- task: CLEAN algorithm  
  > "Images were obtained by using the CLEAN algorithm." (2 Observations)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum from line-free channels, subtracted from visibilities  
  > "The continuum image was prepared by averaging line-free channels and the line maps were obtained after subtracting the continuum directly from the visibilities." (2 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: CCH data combined with project 2011.0.00628.S (15-16 antennas)  
  > "The CCH data were combined with those taken in another observing program (2011.0.00628.S; PI: Jes Jørgensen) with $15-16$ antennas." (2 Observations)
- smoothing: _not stated_
- final beam: 0.57"x0.42" PA 49 deg continuum  
  > "The synthesized-beam size is $0.57\ensuremath{''} \times 0.42\ensuremath{''}$ (P.A. $= 49\ensuremath{^\circ}$) for the continuum image" (2 Observations)
- final rms: _not stated_

### Inherited from earlier work

- Infalling rotating envelope toy model applied as in L1527  
  > "Therefore, it is worth applying the same model to the velocity structure observed for H$_2$CO and CCH in IRAS 15398–3359." (3.4 Comparison with an Envelope Model) [from Sakai et al. 2014a, 2014b]
- Parabolic outflow cavity model  
  > "We employ the standard model of an outflow cavity from Lee et al. (2000)" (3.2 Outflow) [from Lee et al. (2000)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration procedure
- CLEAN weighting/robust, cell and image size, masks, thresholds
- line-free channels used for continuum
- how the 2011.0.00628.S and 2011.0.00777.S data were combined
- H2CO PV cut widths and position angles
- model grid values of mass and r_CB, and by-eye comparison criteria

## Analysis recipe

1. **Image continuum and line cubes**: CLEAN imaging, continuum subtracted in visibilities; CCH combined with second project  
  > "Images were obtained by using the CLEAN algorithm." (2 Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive H2CO column density, temperature, ortho/para ratio**: RADEX fit to para-H2CO 5_05-4_04 and 5_24-4_23 intensities  
  > "Using the RADEX program (van der Tak et al. 2007) to fit the intensity of the two temperature sensitive lines of para-H$_2$CO" (3.1 Overall Distribution of H$_2$CO and CCH)
   - software: RADEX
   - assumption: H2 density 1e7-1e8 cm-3, line width 1.8 km/s  
  > "on the assumption that H$_2$ density is $1 \times 10^7$–$1 \times 10^8\ {\rm cm}^{-3}$ and the line width is $1.8\ {\rm km\ s}^{-1}$." (3.1 Overall Distribution of H$_2$CO and CCH)
   - fitting: _not stated_
   - validation: optical depths <1 so lines not opaque  
  > "therefore the lines are not opaque." (3.1 Overall Distribution of H$_2$CO and CCH)
3. **Outflow cavity inclination**: Compare PV diagrams with parabolic cavity model with linear velocity, free parameters C and v0, trying inclinations  
  > "$C$ and $v_0$ are free parameters. The best results are obtained with an inclination angle of $20\ensuremath{^\circ}$" (3.2 Outflow)
   - parameter: R0=z0=1 arcsec  
  > "$R_0$ and $z_0$ are both normalization constants, and are set to be $1^{\prime \prime}$." (3.2 Outflow)
   - fitting: by-eye comparison  
  > "The models with a central mass of $0.02\ M_\odot$ and a radius of the centrifugal barrier of $0 - 30$ AU are chosen as the best simulations among the $20$ models shown in Figure $\ref{H2CO_PVdiff}$ by eye." (Comparison with an Envelope Model)
   - validation: inclination >30 or <10 deg fails for any C, v0  
  > "When the inclination angle is higher than $30\ensuremath{^\circ}$ or less than $10\ensuremath{^\circ}$, the model does not reproduce the observations well with any values of $C$ and $v_0$." (3.2 Outflow)
4. **Upper limit of protostellar mass from velocity shift**: M = r/(2G)(v_infall^2+v_rot^2) at 0.5" (78 AU) with max velocity 1 km/s  
  > "the central mass can roughly be estimated to be smaller than $0.09\ M_\odot$ with a maximum velocity of less than $1$ km s$^{-1}$ at $0.5\ensuremath{''}$ ($78$ AU) from the protostar." (3.3 Protostellar Envelope)
   - assumption: infall and rotation velocities both 1 km/s  
  > "we assume as a robust case that the infalling velocity and the rotating velocity are both the observed maximum value of $1\ {\rm km\ s}^{-1}$" (3.3 Protostellar Envelope)
   - fitting: _not stated_
   - validation: _not stated_
5. **Envelope model PV comparison**: Toy infalling-rotating envelope model, 20 models of M and r_CB compared by eye with H2CO PV diagram, r_CB limited to <=80 AU  
  > "The models with a central mass of $0.02\ M_\odot$ and a radius of the centrifugal barrier of $0 - 30$ AU are chosen as the best simulations among the $20$ models shown in Figure $\ref{H2CO_PVdiff}$ by eye." (3.4 Comparison with an Envelope Model)
   - parameter: flared angle 20 deg, outer radius 240 AU, density ~ r^-1.5, line width 0.5 km/s, beam 0.6"  
  > "The envelope has a flared shape with a flared angle of $20\ensuremath{^\circ}$. Its outer radius is fixed to be $240$ AU" (Appendix)
   - assumption: optically thin, no disk inside centrifugal barrier  
  > "The molecular emission is simply assumed to be optically thin." (Appendix)
   - fitting: _not stated_
   - validation: consistent with step 4 upper limit  
  > "The mass is consistent with the upper limit estimated in Section 3.3." (3.4 Comparison with an Envelope Model)

## Software

- **RADEX** : H2CO column density and temperature  
  > "Using the RADEX program (van der Tak et al. 2007)" (3.1 Overall Distribution of H$_2$CO and CCH)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| outflow inclination | 20 | ±10 deg | deg | 3 | the inclination angle is determined to be $20\ensuremath{^\circ} \pm 10\ensuremath{^\circ}$ |
| outflow model C | 0.8 | not stated | arcsec^-1 | 3 | $C = 0.8$ arcsec$^{-1}$ and $v_0 = 0.38$ km s$^{-1}$ |
| protostellar mass upper limit | <0.09 | not stated | Msun | 4 | the mass of the protostar is estimated to be less than $0.09\ M_\odot$ |
| best model mass | 0.02 | not stated | Msun | 5 | central mass of $0.02\ M_\odot$ and a radius of the centrifugal barrier of $0 - 30$ AU |
| H2CO column density | 3e13 | not stated | cm^-2 | 2 | estimated to be $3 \times 10^{13}\ {\rm cm}^{-2}$ and $36$–$38\ {\rm K}$ |
| kinetic temperature | 36-38 | not stated | K | 2 | $3 \times 10^{13}\ {\rm cm}^{-2}$ and $36$–$38\ {\rm K}$ |
| H2CO ortho/para ratio | 2.8 | not stated | dimensionless | 2 | the ortho/para ratio is estimated to be $2.8$ |
| average accretion rate upper limit | <9.0e-5 | not stated | Msun/yr | 0 | the average accretion rate is calculated to be less than $9.0 \times 10^{-5}\ M_\odot$ yr$^{-1}$. |

## Qualitative findings

- Well-collimated NE-SW outflow cavity, redshifted NE and blueshifted SW, plus compact central component ~2" (310 AU)  
  > "The most prominent feature is a well-collimated outflow extending symmetrically from the protostar along a northeast–southwest axis." (3.1 Overall Distribution of H$_2$CO and CCH)
- No obvious rotation signature; possible faint high-velocity H2CO hints at a disk  
  > "hinted at by a weak high-velocity H$_2$CO emission associated with the protostar." (abstract)

## Claim tuples

- H: Is the outflow pole-on as previously suggested? | E: Fit parabolic cavity model to H2CO PV diagrams | R: Inclination 20±10 deg | F: Outflow is nearly edge-on | **supported**
- H: Is the protostar mass low? | E: Velocity shift at 78 AU and envelope model comparison | R: <0.09 Msun; best model 0.02 Msun | F: Substellar-mass protostar | **supported**
- H: Is a rotationally supported disk present? | E: PV diagrams of H2CO and CCH near protostar | R: No clear rotation; weak high-velocity H2CO | F: Higher resolution needed | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Same toy envelope model as for L1527 used for comparison  
  > "it is worth applying the same model to the velocity structure observed for H$_2$CO and CCH in IRAS 15398–3359." (3.4 Comparison with an Envelope Model)
- Alternative: Dense gas mostly in the outflow rejected since outflow model cannot explain velocity gradient  
  > "the outflow motion cannot well explain the velocity gradient in Figure $\ref{PV2x2}$(b) for H$_2$CO" (3.3 Protostellar Envelope)
- How they decided it was enough: _not stated_
- Limitation (authors): Mass estimate depends on inclination; emission >12" unreliable  
  > "The above mass estimate may suffer from the uncertainty of the inclination angle of the envelope/disk." (4 Discussion)
- Caveat (inferred, ours): Mass limits rely on rough PV velocity reading and by-eye model selection with no formal fit
- Caveat (inferred, ours): Toy model ignores radiative transfer and pressure
- Caveat (inferred, ours): Single 0.5" resolution; velocity shifts near the channel and line widths

## Reproducibility

- Data public (paper): ALMA Cycle 0 data sets cited by project code  
  > "This paper makes use of the following ALMA data set ADS/JAO.ALMA$\#$2011.0.00777.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: Model code and grid not released
- Missing: PV cut definitions
- Data volume (inferred): ~10-50 GB raw for two Cycle 0 projects
- Score (inferred): 3/5, Public Cycle 0 data and a simple, fully described model, but imaging parameters and by-eye fitting are unspecified.
- Rediscovery candidate: no, Key results rely on by-eye model comparison and unstated imaging settings.

## Links

- Method: Lee et al. 2000 (Outflow cavity model)
- Method: Sakai et al. 2014a, 2014b (Infalling rotating envelope model applied to L1527)
- Method: van der Tak et al. 2007 (RADEX)
- Companion: Jørgensen et al. 2013 (Earlier ALMA observation of the same source (H13CO+ ring, CH3OH))
- Related: L1527 ALMA observations

## Checks

```json
{
 "quotes": 66,
 "quotes_ok": 66,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 44,
  "rate": 0.603
 },
 "evidence_ok": true
}
```
