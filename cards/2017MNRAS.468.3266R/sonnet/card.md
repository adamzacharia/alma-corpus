# The ALMA early science view of FUor/EXor objects - III. The slow and wide outflow of V883 Ori

`2017MNRAS.468.3266R` | Monthly Notices of the Royal Astronomical Society 2017 | first author: Ruíz-Rodríguez, D. | arXiv: 1703.07006 | DOI: 10.1093/mnras/stx703

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, protoplanetary_disks
- Question: What are the morphology, opening angle, velocity and kinematic properties of the molecular outflow and envelope of the FU Ori object V883 Ori, traced by 12CO, 13CO and C18O?  
  > "We describe the molecular outflow and envelope of the system based on the $^{12}$CO and $^{13}$CO emissions, which together trace a bipolar molecular outflow." (abstract)
- Target **V883 Ori**: coordinates 05h 38m 18.10s, -07d 02' 26.00" (J2000)  
  > "V883 Ori, located at a distance of 414 $\pm$7 pc (cite: Menten2007)" (Introduction); "ALMA observations of V883 Ori, located at 05$^{h}$ 38$^{s}$ 18.10$^{s}$ -07$^{o}$ 02$^{'}$ ${26.00}''$" (2.1 Observations); z/distance 414 ± 7 pc  
  > "V883 Ori, located at a distance of 414 $\pm$7 pc (cite: Menten2007)" (Introduction); "ALMA observations of V883 Ori, located at 05$^{h}$ 38$^{s}$ 18.10$^{s}$ -07$^{o}$ 02$^{'}$ ${26.00}''$" (2.1 Observations); distance from Menten et al. 2007  
  > "V883 Ori, located at a distance of 414 $\pm$7 pc (cite: Menten2007)" (Introduction); "ALMA observations of V883 Ori, located at 05$^{h}$ 38$^{s}$ 18.10$^{s}$ -07$^{o}$ 02$^{'}$ ${26.00}''$" (2.1 Observations)

## Data provenance

- ALMA projects: 2013.1.00710.S
- bands: Band 6 (230 GHz/1.3 mm)  
  > "Here, we present ALMA band-6 (230 GHz/1.3 mm) continuum and $^{12}$CO( J=2-1 ), $^{13}$CO( J=2-1 ) and C$^{18}$O( J=2-1 ) line observations" (Introduction)
- frequencies and spectral setup: 12CO, 13CO, C18O J=2-1 at 230.5380, 220.3987, 219.5603 GHz; resolution 0.04 km/s (12CO), 0.08 km/s (13CO, C18O)  
  > "The correlator was configured to provide a spectral resolution of 0.04 km s$^{-1}$ for $^{12}$CO and of 0.08 km s$^{-1}$ for $^{13}$CO and C$^{18}$O." (2.1 Observations)
- continuum bandwidth: 3.9 GHz  
  > "The total bandwidth available for continuum observations was 3.9 GHz." (2.1 Observations)
- arrays: _not stated_
- configurations: C34-2/1 and C34/2 (two epochs), C34-7/6 (third epoch)  
  > "using 37 and 39 antennas on the C34-2/1 and C34/2 configurations, respectively." (2.1 Observations); "a third observation of V883 Ori was performed on August 30$^{th}$, 2015 with 35 antennas in the C34-7/6 configuration" (2.1 Observations)
- baselines: 14 m to 350 m (first two epochs); 42 m to 1.5 km (third epoch)  
  > "the shortest baseline of $\sim$ 14 m and longest of $\sim$ 350 m." (2.1 Observations)
- angular resolution: 0.35"x0.27" (12CO), 0.37"x0.28" (13CO), 0.37"x0.29" (C18O), continuum 0.25"x0.17"  
  > "${0.35}''\times{0.27}''$with P.A. $=$ -90$^{^{\circ}}$ for $^{12}$CO" (2.1 Observations)
- max recoverable scale: ~11"  
  > "our observations have a maximum resolvable angular scale (MRS) of $\sim$11${''}$" (3.4 Outflow Masses and Kinematics)
- sensitivity: rms 12.5 (12CO), 16.0 (13CO), 13.9 (C18O) mJy/beam; continuum 0.25 mJy/beam  
  > "The rms is 12.5 mJy beam$^{-1}$ for $^{12}$CO, 16.0 mJy beam$^{-1}$ for $^{13}$CO and 13.9 mJy beam$^{-1}$ for C$^{18}$O." (2.1 Observations)
- time on source: _not stated_
- observing dates: 12 Dec 2014, 15 Apr 2015, 30 Aug 2015  
  > "Two of three observations were performed on December 12$^{th}$, 2014 and April 15$^{th}$, 2015" (2.1 Observations)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (230.5380 GHz)
- Line: 13CO J=2-1 (220.3987 GHz)
- Line: C18O J=2-1 (219.5603 GHz)
- Other facility **Magellan Clay 6.5 m / MIKE**: High-resolution optical spectrum of Halpha showing P Cygni profile  
  > "we observed V883 Ori on the night of 29 February, 2016 with the Magellan Inamori Kyocera Echelle" (2.2 Optical Spectrum)
- External data: Systemic velocity 4.3 km/s, disk PA 32.4 deg and inclination 38.3 deg  
  > "from the major and minor axes of this emission an inclination ($i$) of $\sim$ 38.3$^{^{\circ}}$$\pm$ 1.0." (3 Results) [from (cite: Cieza2016a)]
- External data: Abundance ratio [12CO]/[13CO] = 62  
  > "is taken as 62 (cite: Langer1993)" (3.4 Outflow Masses and Kinematics) [from (cite: Langer1993)]
- External data: Distance 414 ± 7 pc  
  > "located at a distance of 414 $\pm$7 pc (cite: Menten2007)" (Introduction) [from (cite: Menten2007)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA v4.4  
  > "The visibility data were edited, calibrated and imaged in CASA v4.4 (cite: McMullin2007)." (2.1 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0423-013 and Ganymede  
  > "J0423-013 and Ganymede were used as Flux calibrators" (2.1 Observations)
- flux scale uncertainty: 10%  
  > "The flux density calibration uncertainty is 10 $\%$." (2.1 Observations)
- self calibration: _not stated_

### Imaging

- task: CLEAN  
  > "We used the CLEAN algorithm to image the data" (2.1 Observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0  
  > "using a robust parameter equal to zero, a briggs weighting was performed" (2.1 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: three nights concatenated and processed together  
  > "The observations from all three nights were concatenated and processed together to increase the signal to noise and $uv$-coverage." (2.1 Observations)
- smoothing: _not stated_
- final beam: 0.35"x0.27" PA -90 (12CO); 0.37"x0.28" PA 86.5 (13CO); 0.37"x0.29" PA 87 (C18O); continuum 0.25"x0.17" PA -85.5  
  > "${0.37}''\times{0.28}''$ with P.A. $=$ 86.5$^{^{\circ}}$ for $^{13}$CO" (2.1 Observations)
- final rms: 12.5/16.0/13.9 mJy/beam (12CO/13CO/C18O); continuum 0.25 mJy/beam  
  > "The rms is 12.5 mJy beam$^{-1}$ for $^{12}$CO, 16.0 mJy beam$^{-1}$ for $^{13}$CO and 13.9 mJy beam$^{-1}$ for C$^{18}$O." (2.1 Observations)

### Inherited from earlier work

- Outflow mass and kinematics procedure follows Section 3.4 of the HBC 494 paper  
  > "Thus, following the process described in Section 3.4 in (cite: RuizRodriguez2016), we estimate these quantities from the blue- and red-shifted emissions, separately." (3.4 Outflow Masses and Kinematics) [from (cite: RuizRodriguez2016)]
- Outflow quantities derived in the standard manner  
  > "in the standard manner (cite: Cabrit1990; Dunham2014)" (3.4 Outflow Masses and Kinematics) [from (cite: Cabrit1990; Dunham2014)]
- Opening angle relation  
  > "is the distance along the outflow where the angle is measured (cite: Lee2005)" (3.1 12CO Emission) [from (cite: Lee2005)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and method of continuum subtraction
- CLEAN threshold, masks, image size and cell size
- Calibration pipeline vs manual and script details
- Gas excitation temperature choice rationale (20 and 50 K only) and CO abundance/ conversion constants for mass
- Exact velocity-weighting/data-point selection for parabola fit of T12/T13
- Reduction parameters for MIKE spectrum beyond bias and flat-fielding

## Analysis recipe

1. **Image cubes and continuum**: Concatenate three epochs, calibrate and image with CLEAN, Briggs weighting  
  > "We used the CLEAN algorithm to image the data and, using a robust parameter equal to zero, a briggs weighting was performed" (2.1 Observations)
   - software: CASA
   - parameter: robust = 0  
  > "using a robust parameter equal to zero" (2.1 Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Moment maps, channel maps and opening angle**: Moment-1 maps over 2.0-6.25 km/s; opening angle from southern 12CO cavity using Lee & Ho relation  
  > "an opening angle of $\sim 150$$^{^{\circ}}$ is revealed beyond $\sim$ 600 au from the central source" (3.1 12CO Emission)
   - parameter: inclination 38.3 deg adopted; distance 414 pc  
  > "Here, we adopted this inclination value to describe the orientation of the outflows." (3 Results)
   - fitting: _not stated_
   - validation: _not stated_
3. **Optical depth correction of 12CO**: Ratio T12/T13 with X=62; parabola fitted to weighted mean ratios and extrapolated to all 12CO channels  
  > "it is necessary to extrapolate values from a parabola fitted to the weighted mean values of the form" (3.4 Outflow Masses and Kinematics)
   - parameter: channels above 3.5 sigma used for ratio  
  > "from all the channels with detection above 3.5$\sigma$" (3.4 Outflow Masses and Kinematics)
   - assumption: 13CO optically thin; [12CO]/[13CO] = 62  
  > "$^{13}$CO, as an optically thin tracer, is used to correct for optical depth effects in the $^{12}$CO data." (3.4 Outflow Masses and Kinematics)
   - fitting: Parabola T12/T13 = 0.57 + 0.34(v-vLSR)^2, minimum fixed at zero velocity, chi2 = 0.6; points where 12CO becomes thin excluded  
  > "The best fit with a $\chi^{2}$ of 0.6 is shown in Figure [12](#Fig:factor) as a solid green line" (3.4 Outflow Masses and Kinematics)
   - validation: Authors caution the fit is poor and depends on the last data point  
  > "the fitted parabola and the derived outflow parameters must be taken with caution because of the poor fitting" (3.4 Outflow Masses and Kinematics)
4. **Outflow mass and kinematics**: Mass, momentum, energy, luminosity, mass loss from channels above 5 sigma, blue 1.5-4.25 and red 4.5-7.0 km/s, at 20 and 50 K; v_flow = P/M; kinematic age from extent over velocity  
  > "The characteristic velocity of the outflow of $\sim$0.65 km s$^{-1}$ is estimated using $\rm v_{flow}=\frac{P_{flow}}{M_{flow}}$" (3.4 Outflow Masses and Kinematics)
   - parameter: temperatures 20 and 50 K; extent 7300 au (17.5")  
  > "Table [\[table:kinematics\]](#table:kinematics) shows the estimates[^7] at temperatures of 20 and 50 K." (3.4 Outflow Masses and Kinematics)
   - assumption: Not corrected for inclination; kinematic age is a lower limit  
  > "the estimate of the dynamical timescale is a lower limit since we have only used our ALMA data" (3.4 Outflow Masses and Kinematics)
   - fitting: _not stated_
   - validation: Compared with other FUor and YSO outflows  
  > "Nevertheless, these values are on the order of other FU Ori objects such as, V2775 Ori, L1165, HBC 494" (4.1 The extension and velocity of the outflow in the V883 Ori system)

## Software

- **CASA** 4.4: Editing, calibration and imaging of visibilities  
  > "The visibility data were edited, calibrated and imaged in CASA v4.4 (cite: McMullin2007)." (2.1 Observations)
- **Carnegie Python tools** : Bias subtraction and flat-fielding of MIKE data  
  > "by using the Carnegie Python tools[^5] (cite: Kelson2003)" (2.2 Optical Spectrum)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Outflow opening angle (12CO blue-shifted) | ~150 | not stated | deg | 2 | we estimate a *wide* opening angle of $\sim$ 150$^{^{\circ}}$ for the outflow cavities |
| Characteristic outflow velocity | 0.65 | not stated | km/s | 4 | characteristic velocity of only 0.65 km s$^{-1}$ |
| Outflow extent (12CO blue) | 7300 | not stated | au | 2 | an extension of 7300 au assuming a distance of 414 $\pm$7 pc |
| Kinematic age | ~10000 | lower limit | yr | 4 | we estimated a kinematic age for V883 Ori of $\sim$10000 years |
| Total outflow mass, combined, 20 K (corrected 12CO + 13CO, uncorrected) | 4.22e-2 | not stated | Msun | 4 | / Total / Mass (10$^{-2}$ M$_{\odot}$)                  / 3.56          / 5.35           / 4.65         / 7.03          / 4.22          / 6.20          /   / |
| Parabola fit T12/T13 | 0.57 + 0.34 (v-vLSR)^2 | chi2 = 0.6 | dimensionless | 3 | \frac{\textrm{T}_{12}}{\textrm{T}_{13}} = 0.57 + 0.34(\textrm{v-v}_{\textrm{\textsc{LSR}}})^{2}. |
| Dip in 12CO emission at continuum peak | ~15 times weaker | not stated | dimensionless | 2 | which is significantly weaker by a factor of $\sim$15 compared with the immediately surrounding emission |

## Qualitative findings

- 12CO traces the southern (blue) cavity and 13CO the northern one, together a bipolar outflow; C18O traces a Keplerian disk  
  > "The C$^{18}$O emission traces the rotational motion of the circumstellar disk." (abstract)
- Halpha P Cygni profile indicates a wind  
  > "we present a P Cygni profile observed in the high-resolution optical spectrum, evidence of a wind driven by the accretion" (abstract)

## Claim tuples

- H: Does V883 Ori host a molecular outflow and what is its geometry? | E: 12CO and 13CO moment and channel maps at 0.3 arcsec | R: Bipolar cavities with ~150 deg opening angle | F: A wide-angle bipolar outflow is detected | **supported**
- H: Is the outflow velocity typical of FUors? | E: Outflow momentum/mass characteristic velocity from 12CO and 13CO | R: Characteristic velocity ~0.65 km/s | F: The outflow is unusually slow | **supported**
- H: Is the current outburst responsible for the outflow? | E: Kinematic age from extent and velocity | R: Age >1e4 yr vs outburst ~1e2 yr | F: Ongoing outburst cannot directly drive the observed outflow | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Red 12CO emission near 4.5 km/s attributed to ambient cloud rather than outflow  
  > "seems to be better explained as being dominated by ambient emission rather than from an outflow emission" (3.1 12CO Emission)
- How they decided it was enough: _not stated_
- Limitation (authors): Maximum recoverable scale ~11" smaller than cavities, so flux may be missing  
  > "a fraction of the total outflow emission might be missing" (3.4 Outflow Masses and Kinematics)
- Limitation (authors): Optical depth correction poorly constrained  
  > "this optical depth correction must be taken with caution." (Summary)
- Caveat (inferred, ours): Outflow properties depend strongly on assumed temperature and uncorrected inclination
- Caveat (inferred, ours): Envelope contamination in few channels may bias results
- Caveat (inferred, ours): No uncertainties on most derived quantities

## Reproducibility

- Data public (paper): Program 2013.1.00710.S cited; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA No. 2013.1.00710.S ." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CLEAN parameters (masks, thresholds, image size)
- Missing: Line-free channels / continuum subtraction
- Missing: Exact constants and abundances for mass computation
- Data volume (inferred): ~50-200 GB raw for three EBs
- Score (inferred): 3/5, Public ALMA data and a mostly described recipe, but many imaging details and mass-calculation constants are missing.
- Rediscovery candidate: no, Mass derivation relies on inherited procedure and unspecified parameters; the fit is acknowledged as poor.

## Links

- Method: (cite: RuizRodriguez2016) (Outflow mass and kinematics procedure)
- Method: (cite: Cabrit1990; Dunham2014) (Standard outflow kinematic calculation)
- Companion: (cite: Cieza2016a) (V883 Ori disk, snow line and stellar parameters from same ALMA program)
- Companion: (cite: Zurlo2016) (V2775 Ori in the same program)
- Companion: (cite: Principe2016) (V1647 Ori in the same program)
- Related: ALMA program 2013.1.00710.S FUor/EXor survey

## Checks

```json
{
 "quotes": 68,
 "quotes_ok": 68,
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
  "stated": 49,
  "rate": 0.653
 },
 "evidence_ok": true
}
```
