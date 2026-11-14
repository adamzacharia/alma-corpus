# ALMA reveals a candidate hot and compact disc around the O-type protostar IRAS 16547-4247

`2015MNRAS.447.1826Z` | Monthly Notices of the Royal Astronomical Society 2015 | first author: Zapata, Luis A. | arXiv: 1411.7421 | DOI: 10.1093/mnras/stu2527

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: Does the O-type protostar IRAS 16547-4247 host a rotating disk, and how do molecular line kinematics at different excitation temperatures trace the jet/outflow versus the disk?  
  > "We report on the detection of a candidate to compact and hot molecular rotating disk with a size of about 1000 AU and with an orientation perpendicular to the radio jet emerging from this object." (Introduction)
- Target **IRAS 16547-4247**: coordinates RA 16h58m17.24s, Dec -42d52m08.09s (J2000, phase center)  
  > "The source is located at a distance of 2.9 $\pm$ 0.6 kpc (cite: rod2008)." (Introduction); "the position of the object IRAS 16547" (Observations); z/distance 2.9 +/- 0.6 kpc  
  > "The source is located at a distance of 2.9 $\pm$ 0.6 kpc (cite: rod2008)." (Introduction); "the position of the object IRAS 16547" (Observations); distance from Rodriguez et al. 2008 (rod2008)  
  > "The source is located at a distance of 2.9 $\pm$ 0.6 kpc (cite: rod2008)." (Introduction); "the position of the object IRAS 16547" (Observations)
- Target **IRAS 16547-W**: coordinates RA 16h58m17.051s, Dec -42d52m07.11s (J2000)  
  > "the other one 2$''$ to its west (IRAS 16547-W)" (Results); z/distance 2.9 kpc (assumed same as IRAS 16547)  
  > "the other one 2$''$ to its west (IRAS 16547-W)" (Results); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00419.S
- bands: 0.85 mm (~345 GHz)  
  > "submillimeter continuum (0.85 mm)" (abstract)
- frequencies and spectral setup: 4 spectral windows of 1875 MHz, 3840 channels each, 0.488 MHz (~0.4 km/s) per channel; centered 350.355, 352.228, 340.117, 341.971 GHz  
  > "The ALMA digital correlator was configured in 4 spectral windows of 1875 MHz and 3840 channels each." (Observations); "The spectral windows were centered at 350.355 GHz, 352.228 GHz, 340.117 GHz, and 341.971 GHz" (Observations)
- continuum bandwidth: 7.5 GHz total, line-free channels  
  > "we used the total bandwidth of the observations (7.5 GHz) selecting only the line-free channels" (Observations)
- arrays: 12 m antennas only, Cycle 0 (16 antennas April, 21 antennas August 2012)  
  > "on April (16 antennas) and August 2012 (21 antennas), during the cycle 0 science data program." (Observations)
- configurations: _not stated_
- baselines: 25 to 364 m projected, 496 baselines  
  > "The 496 independent baselines ranged in projected length from 25 to 364 m." (Observations)
- angular resolution: 0.39'' x 0.34'' PA 69.2 deg  
  > "at an angular resolution of $0\rlap.{''}39$ $\times$ $0\rlap.{''}34$ with a P.A. = $69.2^\circ$" (Observations)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 7 mJy/beam; line rms ~35 mJy/beam km/s  
  > "The resulting r.m.s. noise for the continuum image was 7 mJy beam$^{-1}$" (Observations); "the resulting r.m.s. noise was about 35 mJy beam$^{-1}$ ${\,{\textnormal{km}}\,{\textnormal{s}}^{-1}}$ at the same angular resolution" (Observations)
- time on source: _not stated_
- observing dates: April and August 2012  
  > "on April (16 antennas) and August 2012 (21 antennas)" (Observations)
- pi or archival as stated: _not stated_
- Line: SO2 28(2,26)-28(1,27) (340.31641 GHz)
- Line: OCS 28-27 (340.44927 GHz)
- Line: CH3SH 14(9)-13(9) -/+A (353.67282 GHz)
- Line: CH3OH 16(6,10)-17(5,13) ++ (340.39367 GHz)
- External data: Bolometric luminosity 6.2e4 Lsun  
  > "bolometric luminosity of 6.2 $\times$ 10$^4$ L$_\odot$ (cite: gar2003)" (Introduction) [from (cite: gar2003)]
- External data: Dust temperature 250 K for IRAS 16547  
  > "a dust temperature of 250 K (cite: her2014) for IRAS 16547" (0.85 mm continuum emission) [from (cite: her2014)]
- External data: Dust opacity kappa(850um)=0.015 cm2/g  
  > "a dust mass opacity $\kappa_{850 \ensuremath{\mu}m}$ = 0.015 cm$^2$ g$^{-1}$ (taking into account the gas-to-dust ratio) (cite: oss1994)" (0.85 mm continuum emission) [from (cite: oss1994)]
- External data: LSR systemic velocity -30.6 km/s  
  > "The LSR systemic velocity of IRAS 16547 is $-$30.6 ${\,{\textnormal{km}}\,{\textnormal{s}}^{-1}}$ (cite: gar2003)." (Line thermal emission) [from (cite: gar2003)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan  
  > "Observations of Titan provided the absolute scale for the flux density calibration." (Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: uniform weighting  
  > "We used uniform weighting in the continuum and lines maps presented in this study." (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: continuum from line-free channels of 7.5 GHz total bandwidth; channels not listed  
  > "selecting only the line-free channels" (Observations)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Synthetic LTE optically thin spectra method  
  > "The synthetic spectra were computed assuming Local Thermodynamic Equilibrium and optically thin emission as in (cite: pal2011)" (Line thermal emission) [from (cite: pal2011)]
- Dust mass formula in practical units  
  > "Writing Eq. (1) in practical units (cite: pau2013)" (0.85 mm continuum emission) [from (cite: pau2013)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration procedure details (manual vs pipeline)
- Which channels were line-free
- Imaging parameters: cell size, image size, deconvolver, masking, clean threshold
- Moment map clipping thresholds
- Column densities and exact synthetic-spectrum fit results
- Radius, velocity and inclination used for dynamical mass
- Flux calibration uncertainty

## Analysis recipe

1. **Continuum imaging and Gaussian fit**: Continuum image from line-free channels, uniform weighting; Gaussian fits to IRAS 16547 and IRAS 16547-W  
  > "Using a gaussian fitting we found for IRAS 16547 a flux density and peak intensity values of 2.1$\pm$0.10 Jy" (0.85 mm continuum emission)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Dust mass from continuum**: Optically thin isothermal dust mass equation  
  > "Assuming that the dust is optically thin and isothermal, and following (cite: hil1983), the dust mass (M$_d$) will be directly proportional to the flux density" (0.85 mm continuum emission)
   - assumption: gas-to-dust 100, D=2.9 kpc, Td=250 K (IRAS 16547), 150 K (W), kappa=0.015 cm2/g  
  > "Taking a gas-to-dust ratio of 100, a distance of 2.9 kpc, a dust temperature of 250 K" (0.85 mm continuum emission)
   - fitting: _not stated_
   - validation: Uncertainty at least factor two from opacity  
  > "have uncertainties of at least a factor two" (0.85 mm continuum emission)
3. **Line identification**: Synthetic LTE optically thin spectra, linewidth 7 km/s (10 for SO2), Trot 70-300 K, column density varied to match  
  > "We then varied the column density until the synthetic spectra reasonably matched the observed spectra." (Line thermal emission)
   - software: JPL catalog, CDMS, Splatalogue
   - assumption: LTE, optically thin  
  > "assuming Local Thermodynamic Equilibrium and optically thin emission" (Line thermal emission)
   - fitting: by-eye matching  
  > "We then varied the column density until the synthetic spectra reasonably matched the observed spectra." (Line thermal emission)
   - validation: _not stated_
4. **Moment-1 maps, PV diagram and dynamical mass**: First-moment maps of SO2/OCS and CH3SH/CH3OH; PV diagram at PA 40 deg; M = 1.13e-3 v^2 R  
  > "$$M[M_\odot]=1.13 \times 10^{-3} v^2 [km s^{-1}] R[AU].$$" (Discussion)
   - software: CASA
   - assumption: Mass uncorrected for inclination  
  > "This value for the mass is uncorrected by the inclination angle." (Discussion)
   - fitting: _not stated_
   - validation: Convolved ALMA SO2 map to SMA resolution and found similar results  
  > "Convolving the ALMA SO$_2$ map to the angular resolution reported in (cite: fra2009) revealed similar results." (Line thermal emission)

## Software

- **CASA** : calibration, imaging and analysis  
  > "The data were calibrated, imaged, and analyzed using the Common Astronomy Software Applications (cite: mc2007)." (Observations)
- **KARMA** : data analysis  
  > "we also used the KARMA (cite: goo96) and AIPS of the National Radio Astronomy Observatory (NRAO) software" (Observations)
- **AIPS** : data analysis  
  > "we also used the KARMA (cite: goo96) and AIPS of the National Radio Astronomy Observatory (NRAO) software" (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| IRAS 16547 continuum flux density | 2.1 | 0.10 | Jy | 1 | flux density and peak intensity values of 2.1$\pm$0.10 Jy and 675$\pm$30 mJy beam$^{-1}$ |
| IRAS 16547-W continuum flux density | 1.6 | 0.20 | Jy | 1 | we found a flux density and peak intensity values of 1.6$\pm$0.20 Jy and 140$\pm$30 mJy beam$^{-1}$ |
| Dust mass IRAS 16547 / IRAS 16547-W | 6.0 / 8.0 | factor of at least 2 | Msun | 2 | of 6.0 M$_\odot$ (integrating in an area $\sim$ 1$''$), and for IRAS 16547-W a mass of 8.0 M$_\odot$ |
| Velocity gradient SO2/OCS | 7 km/s over 3'' (165 km/s/pc) | not stated | km/s | 4 | IRAS 16547 shows a clear velocity gradient of 7 ${\,{\textnormal{km}}\,{\textnormal{s}}^{-1}}$ over a distance of 3$''$ |
| Velocity gradient hot disk | 8 km/s over 1'' (566 km/s/pc) | not stated | km/s | 4 | with a magnitude of 8 ${\,{\textnormal{km}}\,{\textnormal{s}}^{-1}}$ over 1$''$ (equivalent to 566 ${\,{\textnormal{km}}\,{\textnormal{s}}^{-1}}$ pc$^{-1}$) |
| Dynamical mass of central star | ~20 | not stated | Msun | 4 | removing the mass of the disk, the protostar in the middle has a mass of $\sim$ 20 M$_\odot$ |

## Qualitative findings

- Rich chemistry with 15 molecular species including S-bearing molecules and rare CH3SH  
  > "We detected 15 molecular species with different transitions and their isotopologues." (Line thermal emission)

## Claim tuples

- H: Low-excitation lines trace a rotating structure or an outflow | E: Moment-1 maps of SO2 and OCS | R: 7 km/s over 3'' gradient; would imply 60 Msun | F: Gradient is likely from the thermal jet entraining gas, not rotation | **supported**
- H: A compact hot disk exists around IRAS 16547 | E: Moment-1 and PV of high-Eu lines | R: Gradient perpendicular to jet, ~1000 AU | F: Candidate disk, central mass ~20 Msun | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: SO2 gradient as rotation rejected since it gives 60 Msun, inconsistent with luminosity  
  > "which exceeds by one order of magnitude the bolometric luminosity of IRAS 16547" (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Full Keplerian motion not seen; innermost parts unresolved or possibly non-Keplerian  
  > "there is also the possibility that the motions of the innermost parts of the disk are intrinsically non-Keplerian." (Line thermal emission)
- Caveat (inferred, ours): Disk interpretation rests on a moment-1 map and a single PV cut without rotation-curve fitting
- Caveat (inferred, ours): Dynamical mass uncorrected for inclination and rough radius
- Caveat (inferred, ours): Dust temperature for W source uncertain
- Caveat (inferred, ours): Line contamination of continuum

## Reproducibility

- Data public (paper): Cycle 0 project cited  
  > "This paper makes use of ALMA data: ADS/JAO.ALMA#2011.0.00419.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: CASA version and imaging parameters
- Missing: Line-free channel selection
- Missing: Radius and velocity used for the mass estimate
- Data volume (inferred): ~10-50 GB
- Score (inferred): 4/5, Data are public Cycle 0 and the recipe is simple, but imaging details and the mass inputs are missing.
- Rediscovery candidate: no, Imaging and mass-estimate parameters are not given; the kinematic interpretation is qualitative.

## Links

- Companion: Franco-Hernandez et al. 2009 (cite: fra2009) (Earlier SMA/VLA observations of the rotating structure)
- Companion: Rodriguez et al. 2008 (cite: rod2008) (Radio jet and distance)

## Checks

```json
{
 "quotes": 59,
 "quotes_ok": 59,
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
  "stated": 40,
  "rate": 0.548
 },
 "evidence_ok": true
}
```
