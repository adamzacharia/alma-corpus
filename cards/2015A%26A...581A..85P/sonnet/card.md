# The jet and the disk of the HH 212 low-mass protostar imaged by ALMA: SO and SO<SUB>2</SUB> emission

`2015A&A...581A..85P` | Astronomy and Astrophysics 2015 | first author: Podio, L. | arXiv: 1505.05919 | DOI: 10.1051/0004-6361/201525778

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: What are the physical and dynamical properties of the molecular jet and the disk of HH 212, as traced by SO and SO2, and what are the SO and SO2 abundances?  
  > "We aim to constrain the physical and dynamical properties of the molecular jet and the disk of the HH 212 protostellar system at unprecedented angular scales" (abstract)
- Target **HH 212 (MM1 protostar)**: coordinates RA(J2000) 05h43m51.41s, Dec -01d02m53.17s (MM1 dust continuum peak)  
  > "$\alpha$(J2000) = 05$^h$ 43$^m$ 51$^s$.41, $\delta$(J2000) = $-01\ensuremath{^\circ}$ 02$\ensuremath{'}$ 53$\ensuremath{''}$17" (Observations and data reduction); "The HH 212 region in Orion (at 450 pc)" (Introduction); z/distance 450 pc  
  > "$\alpha$(J2000) = 05$^h$ 43$^m$ 51$^s$.41, $\delta$(J2000) = $-01\ensuremath{^\circ}$ 02$\ensuremath{'}$ 53$\ensuremath{''}$17" (Observations and data reduction); "The HH 212 region in Orion (at 450 pc)" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: _none stated_
- bands: Band 7  
  > "HH 212 was observed in Band 7 in the extended configuration of the ALMA Early Science Cycle 0 operations" (Observations and data reduction)
- frequencies and spectral setup: spectral resolution 488 kHz (0.42-0.43 km/s); lines at 334.7-347.3 GHz  
  > "The obtained datacubes have a spectral resolution of 488 kHz ($0.42-0.43$ km s$^{-1}$)" (Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: 24 antennas of 12-m  
  > "using 24 antennas of 12-m" (Observations and data reduction)
- configurations: _not stated_
- baselines: 20 m to 360 m  
  > "The shortest baseline was about 20 m and the longest one 360 m" (Observations and data reduction)
- angular resolution: 0.65'' x 0.47'' at PA~49 deg  
  > "a typical beam FWHM of $0.65\ensuremath{''} \times 0.47\ensuremath{''}$ at PA$\sim 49\ensuremath{^\circ}$" (Observations and data reduction)
- max recoverable scale: 3'' at 850 micron  
  > "hence the maximum unfiltred scale is of 3$\ensuremath{''}$ at 850$\mu$m" (Observations and data reduction)
- sensitivity: rms ~3-4 mJy/beam per 0.43 km/s channel  
  > "an rms noise of $\sim 3-4$ mJy/beam in the 0.43 km s$^{-1}$ channel" (Observations and data reduction)
- time on source: _not stated_
- observing dates: December 1 2012  
  > "on December 1 2012" (Observations and data reduction)
- pi or archival as stated: _not stated_
- Line: SO2 8(2,6)-7(1,7) (334673.352 MHz)
- Line: SO 10(11)-10(10) (336553.346 MHz)
- Line: SO 9(8)-8(7) (346528.481 MHz)
- Line: CO 3-2 (345795.990 MHz)
- Line: SiO 8-7 (347330.631 MHz)
- Line: C17O 3-2 (337061.130 MHz)
- External data: Disk mass of 0.014 Msun from HCO+ 4-3, used for comparison  
  > "close to the disk mass of $0.014$ M$_{\odot}$  estimated by (cite: lee14) from HCO$^{+}$ $4-3$" (4.3 Disk properties) [from (cite: lee14)]
- External data: Envelope infall rate ~6e-6 Msun/yr  
  > "$\dot{M}_{\rm inf} \sim 6 \times 10^{-6}$ M$_{\odot}$ yr$^{-1}$, (cite: lee06)" (4.3 Jet physical and dynamical properties) [from (cite: lee06)]
- External data: Jet inclination i ~4 deg  
  > "Assuming an inclination angle $i \sim 4\ensuremath{^\circ}$ (cite: claussen98)" (3.3 The fast and collimated molecular jet) [from (cite: claussen98)]
- External data: Solar sulfur abundance (S/H) ~1.38e-5  
  > "Assuming a sulfur elemental abundance (S/H)$_{\odot} \sim 1.38 \times 10^{-5}$ (cite: asplund05)" (4.2 SO and SO2 abundance in the jet) [from (cite: asplund05)]
- External data: C17O/CO = 1/1792  
  > "assuming $N_{\rm C^{17}O} / N_{\rm CO} = 1/ 1792$ and $X_{\rm CO} = N_{\rm CO} / N_{\rm H_2} = 10^{-4}$ (cite: wilson94)" (Table 2) [from (cite: wilson94)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: quasars J0538-440, J0607-085, Callisto and Ganymede  
  > "The calibration was carried out following standard procedures and using quasars J0538–440, J0607–085, as well as Callisto and Ganymede." (Observations and data reduction)
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

- Systemic velocity estimated with same method as Codella et al.; C17O, CO, SiO data presented there  
  > "which is estimated following the same method as in (cite: codella14b)" (Observations and data reduction) [from (cite: codella14b)]
- MM1 protostar position from dust continuum peak  
  > "Offsets are given with respect to the MM1 protostar position as determined from the dust continuum peak by (cite: codella14b)" (Observations and data reduction) [from (cite: codella14b)]
- CO column density derived following Cabrit et al. 2012 (optically thin LTE)  
  > "Following (cite: cabrit12) also the beam-averaged CO column density is derived from the CO 3–2 intensity" (4.2 SO and SO2 abundance in the jet) [from (cite: cabrit12)]
- Velocity intervals same as Cabrit et al. 2007  
  > "the defined velocity intervals are the same as in (cite: cabrit07b)" (footnote 3) [from (cite: cabrit07b)]
- Compression factor ~3 for mass loss rate  
  > "following (cite: lee07a; lee07b) we correct the mass loss rate for a compression factor of $\sim 3$" (4.3 Jet physical and dynamical properties) [from (cite: lee07a; lee07b)]

### Not stated but needed to reproduce (our reading)

- ALMA project code and archive MOUS/data location
- CASA version and calibration script details
- Imaging parameters (weighting, robust, cell, image size, deconvolver, masks)
- Continuum subtraction and line-free channels
- Primary beam correction
- Exact beam-dilution factor derivation and RADEX input grids/collision data files
- Knot extraction aperture/position coordinates
- Absolute flux scale uncertainty

## Analysis recipe

1. **Image line cubes and define velocity components**: Cubes from CASA/GILDAS; systemic, LV, IV, HV intervals defined relative to Vsys=+1.3 km/s  
  > "Spectral line imaging and data analysis were performed using the CASA and the GILDAS packages." (Observations and data reduction)
   - software: CASA, GILDAS
   - parameter: Vsys = +1.3 ± 0.2 km/s  
  > "gives $V_{\rm sys} = + 1.3 \pm 0.2$ km s$^{-1}$" (Observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract PV diagrams and knot spectra; derive kinematic/timescale properties**: PVs along and perpendicular to jet (PA 22 deg, disk PA 112 deg); 1D spectra at knots; de-projected V=Vpeak/sin(i), tau_dyn  
  > "we estimate the knot de-projected velocity, $V = V_{\rm peak} / sin(i)$, and derive the knots dynamical timescale" (3.3 The fast and collimated molecular jet)
   - assumption: inclination ~4 deg  
  > "Assuming an inclination angle $i \sim 4\ensuremath{^\circ}$ (cite: claussen98)" (3.3 The fast and collimated molecular jet)
   - fitting: _not stated_
   - validation: Compared with SiO and CO profiles; timescale uncertainty factor 2-3  
  > "We conclude that the estimated knot timescales are affected by an uncertainty of a factor 2-3" (3.3 The fast and collimated molecular jet)
3. **Constrain SO excitation and jet column density/abundance**: RADEX grids compared to SO line ratio and intensities; then LTE optically thin N_SO and N_CO; X_SO = X_CO N_SO/N_CO  
  > "Then, the abundance of SO is derived as $X_{\rm SO} = X_{\rm CO} \times N_{\rm SO} / N_{\rm CO}$" (4.2 SO and SO2 abundance in the jet)
   - software: RADEX
   - parameter: TK = Tex = 50-500 K; nH2 1e5-1e7 cm-3  
  > "kinetic temperatures ($T_{\rm K} = 50 -500$ K) and H$_2$ densities ($n_{H_2}$ from $10^{5}$ to $10^{7}$ cm$^{-3}$)" (4.2 SO and SO2 abundance in the jet)
   - assumption: X_CO = 1e-4; CO optically thin (lower limit in B2)  
  > "the abundance of CO with respect to H$_2$ is assumed to be $X_{\rm CO} = N_{\rm CO} / N_{\rm H_2} = 10^{-4}$" (4.2 SO and SO2 abundance in the jet)
   - fitting: _not stated_
   - validation: RADEX with n=3e5 gives factor 2-4 higher columns  
  > "are from a factor 2 (for $T_{\rm K} = 500$ K) to a factor 4 (for $T_{\rm K} = 50$ K) larger than in the LTE-optically thin case" (4.2 SO and SO2 abundance in the jet)
4. **Jet density and mass loss rate**: NH2 from NCO; cylinder geometry for nH2; Mdot = 1/3 m_H2 (N_CO/X_CO) HPBW_tr V_jet  
  > "$\dot{M}_{\rm jet} = 1/3 \times m_{\rm H_2} \times (N_{\rm CO} / X_{\rm CO}) \times HPBW_{\rm tr} \times V_{\rm jet}$" (4.3 Jet physical and dynamical properties)
   - parameter: V_jet ~165 km/s; HPBW_tr = 0.47''; jet width ~90 AU  
  > "($V_{\rm jet} \sim 165$ km s$^{-1}$) and $HPBW_{\rm tr}$ is the beam size across the jet width ($HPBW_{\rm tr} = 0.47\ensuremath{''}$)" (4.3 Jet physical and dynamical properties)
   - assumption: compression factor ~3, uncertain by factor ~3  
  > "therefore the $\dot{M}_{\rm jet}$ values are affected by a factor $\sim 3$ uncertainty" (4.3 Jet physical and dynamical properties)
   - fitting: _not stated_
   - validation: _not stated_
5. **Disk mass and SO abundance**: RADEX for SO 10-10 and ratio; LTE optically thin SO and C17O columns over |V-Vsys|=1.9-3.5 km/s; disk mass from C17O over beam area, blue+red lobes  
  > "$M_{\rm disk} \sim \left( 1.4 \times m_{\rm H_2} \times (N_{\rm C^{17}O} / X_{\rm C^{17}O}) \times A_{\rm beam} \right)_{\rm blue + red}$" (4.4 Disk properties: mass and SO abundance)
   - software: RADEX
   - parameter: beam dilution factor ~8; R_disk ~90 AU  
  > "strongly diluted in the $0.65\ensuremath{''} \times 0.47\ensuremath{''}$ beam (dilution factor $\sim 8$)" (4.4 Disk properties: mass and SO abundance)
   - assumption: C17O/CO=1/1792, X_CO=1e-4, Tex 50-500 K, factor 1.4 for He  
  > "We assume optically thin emission at LTE with $T_{\rm ex} = 50-500$ K." (Table 2)
   - fitting: _not stated_
   - validation: Compared with disk mass 0.014 Msun from HCO+  
  > "This value is close to the disk mass of $0.014$ M$_{\odot}$  estimated by (cite: lee14) from HCO$^{+}$ $4-3$." (4.4 Disk properties: mass and SO abundance)

## Software

- **CASA** : spectral line imaging and data analysis  
  > "Spectral line imaging and data analysis were performed using the CASA[^1] and the GILDAS[^2] packages." (Observations and data reduction)
- **GILDAS** : spectral line imaging and data analysis  
  > "Spectral line imaging and data analysis were performed using the CASA[^1] and the GILDAS[^2] packages." (Observations and data reduction)
- **RADEX** : statistical equilibrium radiative transfer for SO lines  
  > "one-dimensional radiative transfer code RADEX adopting plane parallel slab geometry (cite: vandertak07)" (4.2 SO and SO2 abundance in the jet)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Jet mass loss rate | >=0.2-2e-6 | factor ~3 | Msun/yr | 4 | $\dot{M}_{\rm jet} \ge 0.2 - 2 \times 10^{-6}$ M$_{\odot}$ yr$^{-1}$ |
| Jet ejection efficiency Mdot_jet/Mdot_inf | >=0.03-0.3 | not stated | dimensionless | 4 | $\dot{M}_{\rm jet}/\dot{M}_{\rm inf} \ge 0.03-0.3$ |
| SO abundance in jet | ~1e-7 to 2e-6 | temperature range 50-500 K | dimensionless | 3 | ($X_{\rm SO} \sim 10^{-7}-2 \times 10^{-6}$) |
| SO2/SO ratio in jet | ~0.5-4 | not stated | dimensionless | 3 | we find SO$_2$/SO$\sim 0.5-4$ in HH 212 |
| Knot dynamical timescales | 15 yr (B3), 30 yr (B2, R2) | factor 2-3 | yr | 2 | $\tau_{\rm dyn} \sim 15$ years for B3 and $\sim 30$ years for the symmetrically located blue- and red-shifted knots B2 and R2 |
| Disk mass | >=0.002-0.013 | not stated | Msun | 5 | The disk mass turns out to be $\sim 0.002 - 0.013$ M$_{\odot}$. |
| SO abundance in disk | ~1e-8 to 1e-7 | not stated | dimensionless | 5 | $X_{\rm SO} = X_{\rm C^{17}O} \times N_{\rm SO} / N_{\rm C^{17}O} \sim 10^{-8} - 10^{-7}$ |
| Systemic velocity | +1.3 | 0.2 | km/s | 1 | gives $V_{\rm sys} = + 1.3 \pm 0.2$ km s$^{-1}$ |
| Fraction of sulfur in SO and SO2 in jet | 1% to 40% | not stated | percent | 3 | from 1% up to 40% of the elemental S is in the form of SO and SO$_2$ in the HH 212 jet |

## Qualitative findings

- SO and SO2 trace cavity walls at systemic velocity, a wide-angle outflow at low velocity, and the collimated fast jet at high velocity  
  > "these molecules probe different components in the inner $\sim 1300$ AU of the HH 212 protostellar system" (Conclusions)
- No velocity gradient across the jet axis detected; jet unresolved transversally  
  > "The figure shows no evidence of a velocity gradient across the jet axis" (5.1 Searching for jet rotation)

## Claim tuples

- H: SO and SO2 trace the molecular jet in HH 212 | E: Channel maps, PVs and knot spectra compared with CO and SiO | R: At |V|>~8 km/s SO PV is similar to CO and SiO; knots B3, B2, R2 identified | F: SO and SO2 are effective jet tracers within a few hundred AU | **supported**
- H: The jet carries a high mass flux and ejection efficiency | E: CO column density to Mdot_jet at knots | R: Mdot_jet >= 0.2-2e-6 Msun/yr | F: High ejection efficiency >= 0.03-0.3 | **supported**
- H: SO 10(11)-10(10) arises partly in the rotating disk | E: Channel maps and PVs of SO 10-10 compared with C17O | R: Peaks displaced along disk axis at 1.9-3.5 km/s; PV across jet shows rotation-like lobes | F: Emission from both the disk and the jet base, with SO abundance 1e-8 to 1e-7 in the disk | **partially**
- H: SO enhancement in disk is explained by shocks | E: Compare disk SO abundance with evolved disks | R: 3-4 orders of magnitude above evolved disks | F: Accretion shock or spiral shocks possible but not distinguished | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Line broadening due to conical jet geometry versus internal jet shock/bowshock; bowshock favoured by earlier work  
  > "The bowshock scenario is favored by (cite: codella07) and further supported by the SiO maps and transverse PVs of (cite: lee08)." (3.3 The fast and collimated molecular jet)
- How they decided it was enough: _not stated_
- Limitation (authors): Resolution too low to fully resolve the disk; edge-on view unfavourable  
  > "The angular resolution ($\sim 0.5\ensuremath{''}$) is too low to fully resolve the disk" (4.4 Disk properties)
- Limitation (authors): Mass loss rate is a lower limit and uncertain by factor ~3; SO data cannot constrain density and temperature  
  > "the avalaible SO observations do not allow constraining the density and temperature of the emitting gas" (4.2 SO and SO2 abundance in the jet)
- Caveat (inferred, ours): Abundances rely on assumed X_CO=1e-4 and a wide Tex range of 50-500 K
- Caveat (inferred, ours): SO2 assumed co-spatial with CO over a narrow velocity range
- Caveat (inferred, ours): No formal uncertainties or fitting; ranges only
- Caveat (inferred, ours): Single low-resolution Cycle 0 dataset; disk and jet-base contributions to SO 10-10 are not separated

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Project code not printed in paper
- Missing: Imaging parameters and CASA version
- Missing: Knot extraction details
- Data volume (inferred): ~10-50 GB (single Cycle 0 Band 7 execution)
- Score (inferred): 4/5, Analysis recipe is simple and explicit, but project code, imaging and calibration details are not given.
- Rediscovery candidate: no, Project code is not stated in the paper and imaging details are missing, although the archive links 2011.0.00647.S.

## Links

- Method: (cite: codella14b) (Source of the CO, SiO, C17O data and the Vsys method)
- Method: (cite: cabrit12) (Method for CO column density in the jet)
- Method: (cite: vandertak07) (RADEX code)
- Companion: (cite: codella14b) (Same ALMA observations: CO, SiO, C17O, C34S)
- Companion: (cite: lee14) (ALMA HCO+ disk observations of HH 212)

## Checks

```json
{
 "quotes": 68,
 "quotes_ok": 68,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00647.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 84,
  "stated": 46,
  "rate": 0.548
 },
 "evidence_ok": true
}
```
