# Imaging a Central Ionized Component, a Narrow Ring, and the CO Snowline in the Multigapped Disk of HD 169142

`2017ApJ...838...97M` | The Astrophysical Journal 2017 | first author: Macías, Enrique | arXiv: 1703.02957 | DOI: 10.3847/1538-4357/aa6620

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: protoplanetary_disks
- Question: What is the fine-scale structure of the HD 169142 disk in VLA 7 mm, 9 mm and 3 cm emission (ring, gaps, central source), and where is the CO snowline relative to the outer gap?  
  > "In this paper we present new high angular resolution VLA observations at 7 mm, 9 mm, and 3 cm toward the pre-transitional disk around HD 169142" (Introduction)
- Target **HD 169142**: coordinates _not stated_; z/distance 117 +/- 4 pc  
  > "the recent publication of the first data release of Gaia has revealed that the distance to HD 169142 is $117\pm4$ pc (cite: gai16)." (Introduction); distance from Gaia DR1 (cite: gai16)  
  > "the recent publication of the first data release of Gaia has revealed that the distance to HD 169142 is $117\pm4$ pc (cite: gai16)." (Introduction)

## Data provenance

- ALMA projects: 2013.1.00592.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: C18O beam 0.35x0.23 arcsec PA=-74 deg; DCO+ beam 0.50x0.48 arcsec PA=-65 deg  
  > "synthesized beam of $0\rlap.''35\times0\rlap.''23$, PA=-74$^{\circ}$" (Observations)
- max recoverable scale: _not stated_
- sensitivity: rms ~6 mJy/beam (C18O) and ~7 mJy/beam (DCO+) per ~0.25 km/s channel  
  > "whereas the rms noise of the DCO$^+$(3-2) observations is $\sim7$ mJy beam$^{-1}$" (Observations)
- time on source: _not stated_
- observing dates: ALMA: 2015 August 30  
  > "The observations were carried out on 2015 August 30 (project code: 2013.1.00592.S)" (Observations)
- pi or archival as stated: Archival ALMA data; C18O previously reported by Fedele et al. 2017, DCO+ unpublished  
  > "we report unpublished archival Atacama Large Millimeter/submillimeter Array (ALMA) data of the DCO$^+$(3-2) transition (rest frequency 216.112 GHz)" (Observations)
- Line: DCO+ 3-2 (216.112 GHz)
- Line: C18O 2-1 (219.560 GHz)
- Other facility **VLA**: New 7 mm, 9 mm, 3 cm data plus archival 1.3 cm and 5 cm data  
  > "Archival observations at K ($\sim$1.3 cm; C and DnC configurations) and C bands ($\sim$5 cm; A configuration) were also used" (Observations)
- Other facility **Gaia**: Distance 117 pc and stellar position  
  > "the distance to HD 169142 is $117\pm4$ pc (cite: gai16)" (Introduction)
- External data: Disk model with mid-plane temperatures, used to locate snowlines  
  > "Comparing these temperatures with the mid-plane temperatures obtained from the model presented by (cite: oso14)" (Outer gaps) [from (cite: oso14)]
- External data: Disk inclination 13 deg and PA 5 deg from molecular observations  
  > "matching the inclination and position angle of the disk major axis determined by previous molecular line observations ($i=13^{\circ}$, and PA$=5^{\circ}$; (cite: ram06))" (Outer gaps) [from (cite: ram06)]
- External data: Mass accretion rate (1.5-2.7)e-9 Msun/yr  
  > "(cite: wag15) measured a mass accretion rate onto the star HD 169142 of $\dot{M}_{\rm acc}\simeq(1.5$–$2.7)\times10^{-9}~M_{\odot}~{\rm yr}^{-1}$." (Central compact radio source) [from (cite: wag15)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline in CASA 4.3.1 for the ALMA data  
  > "Data calibration was performed using the ALMA pipeline within CASA (version 4.3.1)." (Observations)
- casa version: CASA 4.3.1 (ALMA), 4.5.3 (VLA)  
  > "CASA (v 4.3.1, 4.5.3; (cite: mcm07))" (Software)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CLEAN in CASA  
  > "Deconvolved images were then obtained using the CLEAN task with natural weighting." (Observations)
- deconvolver: _not stated_
- weighting robust: Natural weighting for ALMA; Briggs robust 0.5 only for the VLA 3 cm compact source  
  > "We used Briggs weighting with a robust parameter of 0.5 (as defined in task CLEAN of CASA)" (Results and discussion)
- uv taper: uvtaper applied to DCO+(3-2) (value not given)  
  > "a *uvtaper* was applied to the DCO$^+$(3-2) visibilities in order to achieve a higher signal-to-noise ratio." (Observations)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: C18O 0.35x0.23 arcsec; DCO+ 0.50x0.48 arcsec  
  > "synthesized beam of $0\rlap.''50\times0\rlap.''48$, PA=-65$^{\circ}$" (Observations)
- final rms: ~6 mJy/beam (C18O), ~7 mJy/beam (DCO+)  
  > "The rms noise of the C$^{18}$O(2-1) observations is $\sim6$ mJy beam$^{-1}$" (Observations)

### Inherited from earlier work

- ALMA observations described in Fedele et al. 2017, where C18O was first reported  
  > "are described in (cite: fed17), where the C$^{18}$O(2-1) data were first reported" (Observations) [from (cite: fed17)]
- Disk model used to estimate snowline radii and simulate observations  
  > "using the model presented by (cite: oso14) and the SIMOBSERVE task in CASA" (Results and discussion) [from (cite: oso14)]

### Not stated but needed to reproduce (our reading)

- uvtaper value for DCO+
- clean mask, threshold and channel/velocity range for the moment maps
- velocity-integration range for the radial profiles
- how the C18O slope change was measured
- ALMA configuration and baselines
- Fedele et al. 2017 details for the C18O data
- VLA clean parameters (scales, robust, tapers)

## Analysis recipe

1. **image ALMA lines**: Pipeline calibration, CLEAN with natural weighting and uvtaper for DCO+  
  > "Deconvolved images were then obtained using the CLEAN task with natural weighting." (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **radial profiles of line emission**: Azimuthally averaged velocity-integrated emission in elliptical rings, same procedure as continuum  
  > "We have obtained averaged radial profiles of the velocity-integrated emission for both transitions following the same procedures as for the continuum emission" (Outer gaps)
   - parameter: rings of beam width, i=13 deg, PA=5 deg  
  > "The width of the concentric rings was set to the size of the beam" (Outer gaps)
   - assumption: Distance 117 pc  
  > "the distance to HD 169142 is $117\pm4$ pc (cite: gai16)" (Introduction)
   - fitting: _not stated_
   - validation: _not stated_
3. **locate CO snowline**: DCO+ ring radius and C18O slope change compared with model snowline range  
  > "both molecular transitions indicate that the CO snowline is located at $\sim100$ au in the disk of HD 169142" (Outer gaps)
   - fitting: _not stated_
   - validation: Compared with model snowline radius 90-130 au  
  > "the CO snowline would be located at a distance of $90$–$130$ au" (Outer gaps)

## Software

- **CASA** 4.3.1 (ALMA), 4.5.3 (VLA): Calibration, CLEAN imaging, simobserve simulations  
  > "CASA (v 4.3.1, 4.5.3; (cite: mcm07))" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| DCO+(3-2) ring radius | ~0.80 arcsec (~95 au) | not stated | arcsec/au | 2 | ring morphology (Fig. [5](#fig:dco)) with radius $\sim0\rlap.''80$ ($\sim95$ au) |
| C18O(2-1) radial profile slope change | ~0.85 arcsec (~100 au) | not stated | arcsec/au | 2 | significant change of slope in its radial profile at $\sim0\rlap.''85$ ($\sim100$ au) |
| CO snowline radius | ~100 | not stated | au | 3 | the CO snowline is located at $\sim100$ au in the disk of HD 169142 |
| G3 gap extent (VLA) | ~77-96 | not stated | au | 0 | a new gap comprising the radii $\sim$77–96 au (G3) |
| Central source spectral index | 0.82 | 0.17 | dimensionless | 0 | we estimate a spectral index $\alpha=0.82\pm0.17$ |

## Qualitative findings

- DCO+ shows a ring and C18O changes slope near the G3 gap, locating the CO snowline there  
  > "very close to the G3 gap and in the range of distances estimated with the (cite: oso14) model" (Outer gaps)

## Claim tuples

- H: Is the CO snowline near the new outer gap G3? | E: Radial profiles of archival ALMA DCO+(3-2) and C18O(2-1) compared with the 7/9 mm gap and a disk model | R: DCO+ ring at ~95 au, C18O slope change at ~100 au; G3 at ~77-96 au | F: Grain growth and accumulation near the CO snowline is the favored origin of G3 | **partially**

## Reasoning

- Why this data: DCO+ and C18O are tracers of CO freeze-out and the snowline  
  > "the DCO$^+$ emission has been used as a tracer of the CO freeze-out in disks" (Outer gaps)
- Why this method: _not stated_
- Alternative: Planet-induced or MRI dead-zone origins for G3 considered less likely  
  > "even though we cannot completely discard a magnetically induced or planet-induced origin" (Outer gaps)
- How they decided it was enough: _not stated_
- Limitation (authors): The snowline-G3 link is suggestive; further modeling and observations needed  
  > "Further studies, including both modeling and observations, are needed to fully understand the possible changes in the disk appearance with the observing wavelength." (Outer gaps)
- Caveat (inferred, ours): Snowline position from profile features is qualitative with no uncertainties
- Caveat (inferred, ours): ALMA analysis is brief and lacks processing details
- Caveat (inferred, ours): Low resolution (0.3-0.5 arcsec) relative to the gap width

## Reproducibility

- Data public (paper): Archival ALMA data, project 2013.1.00592.S  
  > "we report unpublished archival Atacama Large Millimeter/submillimeter Array (ALMA) data" (Observations)
- Products in archive: _not stated_
- Missing: Imaging parameters for ALMA cubes
- Missing: Radial profile and line-integration details
- Missing: Snowline determination criterion
- Data volume (inferred): ~10-50 GB for the ALMA archival data
- Score (inferred): 3/5, Public ALMA data but sparse processing details; main ALMA results are approximate radii.
- Rediscovery candidate: no, ALMA recipe incomplete and the key ALMA result is a qualitative snowline radius; the main results are VLA-based.

## Links

- Method: (cite: rau11) (Multi-scale multi-frequency deconvolution used for VLA imaging)
- Companion: (cite: fed17) (First report of the C18O(2-1) data and ALMA 1.3 mm continuum)
- Companion: (cite: oso14) (Earlier VLA 7 mm data and disk model)
- Related: VLA 14A-496
- Related: VLA 13B-260

## Checks

```json
{
 "quotes": 44,
 "quotes_ok": 44,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 65,
  "stated": 33,
  "rate": 0.508
 },
 "evidence_ok": true
}
```
