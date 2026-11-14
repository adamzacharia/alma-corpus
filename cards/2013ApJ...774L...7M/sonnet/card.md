# ALMA Observations of the Massive Molecular Outflow G331.512-0.103

`2013ApJ...774L...7M` | The Astrophysical Journal Letters 2013 | first author: Merello, Manuel | arXiv: 1307.6244 | DOI: 10.1088/2041-8205/774/1/L7

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism
- Question: What is the structure, kinematics and age of the massive molecular outflow G331.512-0.103 when resolved with ALMA?  
  > "Here we present observations with ALMA that resolve the G331.512$-$0.103 molecular outflow, allowing derivation of the outflow properties including age." (Introduction)
- Target **G331.512-0.103**: coordinates RA(J2000) 16h12m10.09s, Dec -51d28m38.4s  
  > "We observed a single field of view centered at $\alpha_{2000} = 16^h12^m10.09^s$, $\delta_{2000} = -51\ensuremath{^\circ} 28\ensuremath{'} 38.4\ensuremath{''}$." (Observations and results); "The G331.5-0.1 molecular cloud is a giant, elongated (178 by 41 pc) cloud in the Norma spiral arm, at a distance of 7.5 kpc" (Introduction); z/distance 7.5 kpc  
  > "We observed a single field of view centered at $\alpha_{2000} = 16^h12^m10.09^s$, $\delta_{2000} = -51\ensuremath{^\circ} 28\ensuremath{'} 38.4\ensuremath{''}$." (Observations and results); "The G331.5-0.1 molecular cloud is a giant, elongated (178 by 41 pc) cloud in the Norma spiral arm, at a distance of 7.5 kpc" (Introduction); distance from distance of the G331.5-0.1 cloud (Bronfman2008; Merello2013)  
  > "We observed a single field of view centered at $\alpha_{2000} = 16^h12^m10.09^s$, $\delta_{2000} = -51\ensuremath{^\circ} 28\ensuremath{'} 38.4\ensuremath{''}$." (Observations and results); "The G331.5-0.1 molecular cloud is a giant, elongated (178 by 41 pc) cloud in the Norma spiral arm, at a distance of 7.5 kpc" (Introduction)

## Data provenance

- ALMA projects: 2011.0.00524.S
- bands: Band 7 (350 GHz; 0.86 mm), Cycle 0  
  > "at frequencies around 350 GHz (0.86 mm) with ALMA Band 7 in Cycle 0" (Observations and results)
- frequencies and spectral setup: 4 spectral windows, 1875 MHz each, 3840 channels, 488.281 kHz (0.4215 km/s) channels; centers 345.79599, 347.2, 357.3, 358.60587 GHz  
  > "The four spectral windows have a bandwidth of 1875 MHz containing 3840 channels." (Observations and results); "The bands were centered at 345.79599 GHz, 347.2 GHz, 357.3 GHz and 358.60587 GHz." (Observations and results)
- continuum bandwidth: _not stated_
- arrays: 17 12-m antennas  
  > "with 17 (12-m diameter) antennas in the compact configuration" (Observations and results)
- configurations: _not stated_
- baselines: 18.5 m to 269 m  
  > "with baselines ranging from 18.5 m to 269 m" (Observations and results)
- angular resolution: 1.38" x 0.68", PA -37.6 deg  
  > "the synthesized beam was $1.38\ensuremath{''} \times 0.68\ensuremath{''}$, with a position angle (PA) of $-37.6$$^\circ$" (Observations and results)
- max recoverable scale: primary beam 17.8"  
  > "The primary beam was 17.8$''$" (Observations and results)
- sensitivity: ~0.014 Jy/beam in line-free channels; 0.045-0.365 Jy/beam at line velocities  
  > "For line-free channels, the noise was $\sim$0.014 Jy beam$^{-1}$." (Observations and results)
- time on source: 34 minutes on source, 24 minutes on calibrators  
  > "The integration time was 34 minutes on source, with an additional 24 minutes on calibrators." (Observations and results)
- observing dates: 2012 January 12  
  > "The observations were performed on 2012 January 12" (Observations and results)
- pi or archival as stated: _not stated_
- Line: SiO 8-7 (347.33058 GHz)
- Line: H13CO+ 4-3 (346.99835 GHz)
- Line: HCO+ 4-3 (356.73424 GHz)
- Line: CO 3-2 (345.79599 GHz)
- Other facility **APEX**: single-dish SiO spectra for comparison (Merello 2013)  
  > "The high velocity wings in the SiO profile match those in the APEX spectra presented in (cite: Merello2013)" (Observations and results)
- Other facility **8.6 GHz radio continuum**: radio continuum source position (Merello et al. 2013)  
  > "The red ellipse in Figure 3 represents the 50% contour of the radio continuum source at 8.6 GHz (Merello et al. 2013)." (Observations and results)
- External data: Outflow momentum 2.4e3 Msun km/s and kinetic energy 1.4e48 erg from CO(7-6)  
  > "The momentum ($2.4\mbox{${} \times 10^{3}$}$ M$_\odot$ km s$^{-1}$) and kinetic energy (1.4${} \times 10^{48}$ erg) of the outflow were measured by (cite: Bronfman2008) from CO(7-6) observations." (Discussion) [from (cite: Bronfman2008)]
- External data: Luminosity 7e5 Lsun and 66.7 Jy at 0.86 mm in 33" region  
  > "much less than the 66.7 Jy measured at this wavelength in a 33$''$ region (cite: Merello2013)" (Discussion) [from (cite: Merello2013)]
- External data: Outflow compilation values for comparison  
  > "both higher than any values found in the compilation of outflow properties by (cite: wu04)" (Discussion) [from (cite: wu04)]
- External data: H13CO+/H2 abundance 3.3e-11  
  > "an abundance \[H$^{13}$CO$^+$/H$_2$\] = 3.3$\times10^{-11}$ (cite: blake1987)" (Discussion) [from (cite: blake1987)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1604-446 flux; J1427-421 phase and bandpass  
  > "The nearby quasar J1604-446 was used for flux calibration, and J1427-421, located at 27.7$^\circ$ from the G331.512$-$0.103 source, was used for phase and bandpass calibrations." (Observations and results)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: briggs, robust=0.5  
  > "Our images were obtained considering a “briggs" weighting mode on the data with robust=0.5." (Observations and results)
- uv taper: _not stated_
- cell size: 0.14"  
  > "the resulting maps have cells with sizes of 0.14$''$, with 254 cells in each spatial dimension" (Observations and results)
- image size: 254 cells per spatial dimension  
  > "with 254 cells in each spatial dimension" (Observations and results)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum from regions of the spectrum that appeared line free  
  > "The continuum emission was determined from regions of the ALMA Band 7 spectrum that appeared to be line free" (Discussion)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- CASA version and whether the archive pipeline or manual calibration was used
- Which channels were treated as line-free for continuum
- Deconvolver, masks and clean threshold
- Flux calibrator flux density and calibration uncertainty
- Velocity ranges used for moment 0 maps
- PV slice widths and extraction details
- Self-calibration, if any
- Primary beam correction details
- Exact LTE formula/column density assumptions beyond Tex
- OH5 dust opacity gas-to-dust ratio used for mass

## Analysis recipe

1. **Image and measure noise**: CASA imaging with briggs weighting; rms measured in 35x35 arcsec region excluding emission  
  > "The rms noise was assessed over a region of 35$''$$\times$35$''$ centered on the source, avoiding a square area of 11$''$ in size centered on the emission." (Observations and results)
   - software: CASA
   - parameter: robust=0.5, cell 0.14"  
  > "Our images were obtained considering a “briggs" weighting mode on the data with robust=0.5." (Observations and results)
   - fitting: _not stated_
   - validation: SiO ALMA spectrum compared to APEX; differences <10%  
  > "with differences between both profiles of less than 10%, indicating that the ALMA observations recover all the emission seen in the single-dish spectra" (Observations and results)
2. **Fit moment 0 sizes and position angles**: Gaussian fit to moment 0 maps over full velocity extent  
  > "Moment 0 maps were obtained for each emission line over its full velocity extension, and FWHM angular sizes and P.A.s of these maps were fitted using the task IMFIT of CASA" (Observations and results)
   - software: CASA IMFIT
   - assumption: distance 7.5 kpc  
  > "Physical sizes, considering a source distance of 7.5 kpc, are presented in Column 8 of Table 1." (Observations and results)
   - fitting: _not stated_
   - validation: _not stated_
3. **Determine bipolar axis, ring, cavity and shell velocity from channel maps and PV diagrams**: Peak positions at about ±40 km/s for axis; 3 sigma contours for ring edges; PV diagrams along and perpendicular to axis  
  > "The crosses indicate the peak positions at velocities about $\pm 40$ km s$^{-1}$ from the systemic velocity." (Observations and results)
   - fitting: _not stated_
   - validation: Axis uncertainty from varying channels and S/N levels  
  > "Experiments using other channels, different signal-to-noise levels, etc. resulted in variations around this value of only 1.6$^\circ$" (Observations and results)
4. **Crossing time and outflow force**: t_cross = theta/(2 v_max) with v_max=24 km/s  
  > "An estimate for the crossing time is given by $\mbox{$t_{cross}$}= \theta/(2 \mbox{$v_{max}$})$" (Discussion)
   - fitting: _not stated_
   - validation: _not stated_
5. **LTE mass of H13CO+ gas**: optically thin LTE  
  > "estimated considering a local thermodynamic equilibrium (LTE) formalism and optically thin emission (cite: garden1991)" (Discussion)
   - assumption: Tex=100 K, mu=2.72 mH, [H13CO+/H2]=3.3e-11  
  > "Considering an excitation temperature of 100 K, a mean molecular weight $\mu$ = 2.72 $m_{\mathrm H}$" (Discussion)
   - fitting: _not stated_
   - validation: _not stated_
6. **Continuum flux and dust mass**: continuum size and flux; dust mass assuming dust emission at 400 K with OH5 opacities  
  > "Assuming 400 K, and using OH5 opacities, the mass estimated in a region of 2.9$''$ in size, or 0.11 pc, would be 38 M$_\odot$" (Discussion)
   - assumption: Td 400 K, equilibrium range 400-1000 K at 1" with L=7e5 Lsun  
  > "the equilibrium dust temperature would be $400-1000$ K, for a range of dust properties" (Discussion)
   - fitting: _not stated_
   - validation: Point source removed test gave 3.9 Jy  
  > "obtaining a value of 3.9 Jy" (Discussion)

## Software

- **CASA** : data processing, imaging, IMFIT  
  > "The data were processed using the Common Astronomy Software Application (cite: mcmullin2007)" (Observations and results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| SiO bipolar axis PA | 102.5 | 1.6 | deg | 3 | These channels define a “bipolar axis" of symmetry of $102.5\pm 1.6$$^\circ$. |
| shell expansion velocity | ~24 | not stated | km/s | 3 | we estimate that the expanding shell has a velocity of $\sim$24 km s$^{-1}$ |
| crossing time of SiO ring | ~2000 | not stated | yr | 4 | $\sim$2000 yr for the SiO ring with diameter 3$''$ |
| LTE mass ambient gas / bullet | 36 / 1.8 | not stated | Msun | 5 | the LTE mass of the ambient gas and the bullet are 36 M$_\odot$ and 1.8 M$_\odot$, respectively |
| continuum total flux | 4.3 | not stated | Jy | 6 | The continuum emission has a FWHM of 2.94$''$$\times$2.18$''$ and a total flux of 4.3 Jy. |
| dust mass | 38 | not stated | Msun | 6 | would be 38 M$_\odot$ |
| outflow force | 1.2 | not stated | Msun km/s /yr | 4 | the resulting force is 1.2 M$_\odot$ km s$^{-1}$ yr$^{-1}$ |

## Qualitative findings

- SiO and H13CO+ show a ring at systemic velocity around a cavity coincident with the 8.6 GHz source  
  > "the cavity is coincident with a strong and compact radio continuum source observed at 8.6 GHz" (Summary and conclusions)

## Claim tuples

- H: Is the outflow a bipolar jet plus an expanding shocked shell? | E: SiO moment maps, channel maps and PV diagrams | R: Wings to ±70 km/s, ring at systemic velocity, shell ~24 km/s | F: Jet along the line of sight with an expanding shocked shell | **supported**
- H: The outflow is very young | E: Crossing time from shell size and velocity | R: ~2000 yr (<600 yr for the inner hole) | F: One of the youngest massive outflows | **supported**
- H: A molecular bullet exists | E: H13CO+ PV diagram | R: Emission at -59<v<-29 km/s, 2.5"x1.4" | F: Likely a molecular bullet | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: H13CO+ blue-profile dip could be infall or resolved-out ambient emission  
  > "However, such a dip can also be created by resolving out ambient cloud emission, so further observations would be needed to test this interpretation." (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Continuum may be contaminated by line emission; noise higher in strong lines  
  > "though we cannot rule out some level of contamination by line emission" (Discussion)
- Caveat (inferred, ours): Inclination and projection effects not modeled
- Caveat (inferred, ours): Crossing time assumes constant 24 km/s
- Caveat (inferred, ours): Dust temperature and opacity assumptions drive mass
- Caveat (inferred, ours): Cavity unresolved

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: CASA version and calibration script
- Missing: Clean parameters and masks
- Missing: Channel ranges for moments and continuum
- Data volume (inferred): ~20-50 GB raw Cycle 0 visibilities
- Score (inferred): 3/5, Public Cycle 0 data and key parameters given, but imaging and calibration details are missing.
- Rediscovery candidate: no, Recipe incomplete (clean settings, line windows), though results are numeric.

## Links

- Companion: Merello et al. 2013 (cite: Merello2013) (APEX single-dish spectra and 8.6 GHz continuum)
- Companion: Bronfman et al. 2008 (cite: Bronfman2008) (CO(7-6) outflow momentum and energy)

## Checks

```json
{
 "quotes": 61,
 "quotes_ok": 61,
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
  "stated": 41,
  "rate": 0.547
 },
 "evidence_ok": true
}
```
