# Episodic molecular outflow in the very young protostellar cluster Serpens South

`2015Natur.527...70P` | Nature 2015 | first author: Plunkett, Adele L. | arXiv: 1511.01100 | DOI: 10.1038/nature15702

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: What is the structure and ejection history of the molecular outflow and envelope of the Class 0 protostar CARMA-7 in Serpens South?  
  > "We used the Atacama Large Millimeter/sub-millimeter Array (ALMA) in Chile to observe the $J=2-1$ emission line of carbon monoxide isotopologues" (main text)
- Target **CARMA-7 (C7), Serpens South**: coordinates RA 18h30m04.1s, Dec -02d03m02.6s  
  > "located at a distance of 415 parsec (pc) from Earth(cite: Dzi10)" (main text); "C7 is marked by the yellow cross at RA $=$ 18 h 30 min 04.1 s, declination dec. $=-02\mbox{$^\circ$}\ 03\mbox{$^{\prime}$}\ 02.6\mbox{$^{\prime\prime}$}$." (Figure 1 caption); z/distance 415 pc  
  > "located at a distance of 415 parsec (pc) from Earth(cite: Dzi10)" (main text); "C7 is marked by the yellow cross at RA $=$ 18 h 30 min 04.1 s, declination dec. $=-02\mbox{$^\circ$}\ 03\mbox{$^{\prime}$}\ 02.6\mbox{$^{\prime\prime}$}$." (Figure 1 caption); distance from Dzib et al. 2010 (Dzi10)  
  > "located at a distance of 415 parsec (pc) from Earth(cite: Dzi10)" (main text); "C7 is marked by the yellow cross at RA $=$ 18 h 30 min 04.1 s, declination dec. $=-02\mbox{$^\circ$}\ 03\mbox{$^{\prime}$}\ 02.6\mbox{$^{\prime\prime}$}$." (Figure 1 caption)

## Data provenance

- ALMA projects: 2012.1.00769.S
- bands: Band 6  
  > "The ALMA correlator was configured in the frequency division mode (FDM) of Band 6 with four independent spectral windows" (Observations and data analysis)
- frequencies and spectral setup: Four spectral windows: 12CO, 13CO, C18O (234.375 MHz each) and continuum at 231.450 GHz (468.750 MHz)  
  > "The bandwidth for each spectral-line window was 234.375 MHz, and the continuum window had a bandwidth of 468.750 MHz." (Observations and data analysis)
- continuum bandwidth: 996 MHz total  
  > "resulting in a total continuum bandwidth of 996 MHz" (Observations and data analysis)
- arrays: 12-m and 7-m arrays, Cycle 1  
  > "The analysis is based on ALMA Cycle 1 observations made with the 12-metre and 7-metre arrays" (Observations and data analysis)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.9" x 0.6"  
  > "The resulting beam sizes for the $^{12}\textrm{CO}$ and $\textrm{C}^{18}\textrm{O}$ data cubes are $0.9\mbox{$^{\prime\prime}$}\times0.6\mbox{$^{\prime\prime}$}$" (Observations and data analysis)
- max recoverable scale: _not stated_
- sensitivity: rms 9 (12CO) and 8 (C18O) mJy/beam/channel; continuum 0.2-0.3 mJy/beam  
  > "The root-mean-squared (r.m.s.) noise levels are 9 mJy beam$^{-1}$ channel$^{-1}$ and 8 mJy beam$^{-1}$ channel$^{-1}$" (Observations and data analysis)
- time on source: _not stated_
- observing dates: March 2014 and January to June 2014  
  > "during March 2014 and January to June 2014" (Observations and data analysis)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (230.538 GHz)
- Line: C18O J=2-1 (219.560 GHz)
- Line: 13CO J=2-1 (220.399 GHz)
- Other facility **Spitzer**: 4.5 micron map showing H2 bow shocks  
  > "are seen in the Spitzer 4.5-$\mu$m map of the region(cite: Gut08)" (main text)
- External data: Distance to Serpens South of 415 pc  
  > "located at a distance of 415 parsec (pc) from Earth(cite: Dzi10)" (main text) [from (cite: Dzi10)]
- External data: Spitzer 4.5 micron map  
  > "are seen in the Spitzer 4.5-$\mu$m map of the region(cite: Gut08)" (main text) [from (cite: Gut08)]

## Processing

### Calibration

- pipeline or manual: Standard Cycle 1 reduction script in CASA; statwt weights, concat of 12m and 7m  
  > "using the standard reduction script for Cycle 1" (Observations and data analysis)
- casa version: CASA 4.3.0  
  > "(CASA, version 4.3.0)" (Observations and data analysis)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "We used Briggs weighting with a robust parameter of 0.5" (Observations and data analysis)
- uv taper: _not stated_
- cell size: 0.3 arcsec  
  > "we imaged with a cell size of 0.3$^{\prime\prime}$" (Observations and data analysis)
- image size: _not stated_
- masking: Hand-drawn masks in interactive clean  
  > "we drew masks around the emission features, and these masks were used in an interactive ‘clean’ process" (Observations and data analysis)
- multiscale scales: _not stated_
- continuum subtraction: imcontsub  
  > "we subtracted continuum emission from the spectral line data using the task ‘imcontsub’" (Observations and data analysis)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: concat of 12m and 7m uv-data  
  > "combined the calibrated 12-metre and 7-metre array uv-data using the task ‘concat’" (Observations and data analysis)
- smoothing: _not stated_
- final beam: 0.9" x 0.6", PA 79.7 deg (12CO), 76.3 deg (C18O)  
  > "with position angles of $79.7\mbox{$^\circ$}$ and $76.3\mbox{$^\circ$}$ for $^{12}\textrm{CO}$ and $\textrm{C}^{18}\textrm{O}$, respectively" (Observations and data analysis)
- final rms: 9 and 8 mJy/beam/channel at 0.16 km/s  
  > "with channel widths of 0.16 km s$^{-1}$" (Observations and data analysis)

### Not stated but needed to reproduce (our reading)

- Line-free channels used for continuum and imcontsub
- Clean threshold and iteration count
- Deconvolver and primary beam correction details
- Criteria and procedure for identifying knots and measuring knot velocities
- Inclination assumed for dynamical timescales beyond the quoted example
- Whether 13CO was analysed
- Mosaic phase centre and flux/bandpass/gain calibrators

## Analysis recipe

1. **Calibrate and combine 12m and 7m data**: Standard Cycle 1 script, statwt, concat  
  > "We assigned weights to the measurement sets using the task ‘statwt’ and combined the calibrated 12-metre and 7-metre array uv-data using the task ‘concat’." (Observations and data analysis)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Image cubes and continuum**: Interactive clean with Briggs weighting, then continuum subtraction  
  > "We used Briggs weighting with a robust parameter of 0.5, and we imaged with a cell size of 0.3$^{\prime\prime}$ and a spectral (velocity) resolution of 0.16 km s$^{-1}$." (Observations and data analysis)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Identify outflow knots and derive dynamical timescales**: Velocity maxima in the PV diagram along the outflow axis; tau_dyn = D/V_flow (cos i / sin i)  
  > "Points correspond to velocity maxima where we identify outflow knots." (Figure 2 caption); "The dynamic timescale for each ejection is given by $\tau_{dyn}=D/V_{flow}(\cos i/\sin i)$" (main text)
   - assumption: Knots travel at constant velocity from launch; inclination unknown  
  > "we assume that the knots travel with constant velocity from the time of their launch" (main text)
   - fitting: Linear trend fit to Delta tau_dyn vs tau_dyn for recent northern ejecta  
  > "Recent northern ejecta (solid points) are fit with a linear trend (orange line)." (Figure 2 caption)
   - validation: _not stated_

## Software

- **CASA** 4.3.0: Calibration, imaging, continuum subtraction (statwt, concat, clean, imcontsub)  
  > "(CASA, version 4.3.0) using the standard reduction script for Cycle 1" (Observations and data analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of knots | 22 (11 north, 11 south) | not stated | knots | 3 | 22 knots (observed clumps of emission from a single ejection event), 11 to the north and 11 to the south |
| Mean Delta tau_dyn of seven recent northern knots | 310 | ±150 | years | 3 | mean $\Delta \tau_{dyn}$ of $310\pm150$ years |
| Dynamical timescale range | 100 to 6,000 | not stated | years | 3 | ranging from 100 years to 6,000 years |
| Peak continuum intensity | 93.9 | not stated | mJy/beam | 2 | with an intensity of 93.9 mJy beam$^{-1}$ |

## Qualitative findings

- C7 drives a clumpy, collimated bipolar outflow, indicating episodic ejection; the C18O envelope shows rotation and infall.  
  > "Clumpy $^{12}\textrm{CO}$ emission suggests an episodic ejection mechanism, rather than a smooth outflow." (main text)

## Claim tuples

- H: C7 drives an episodic outflow | E: 12CO J=2-1 mapping and PV analysis of knots | R: 22 knots; Delta tau_dyn 80-540 yr | F: Episodic ejection with short-period variability | **supported**
- H: The envelope is rotating and infalling | E: C18O moment maps and PV diagram | R: Velocity gradient east-west with PV peaks offset | F: Consistent with rotation plus infall on a slightly inclined disk, with some deviations | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Southern knot velocity deficit could be from denser medium, intrinsic variability or different inclination  
  > "This may be evidence for an inhomogeneous ambient cloud medium" (main text)
- How they decided it was enough: _not stated_
- Limitation (authors): Inclination unknown and constant-velocity assumption  
  > "Uncertainties arise because we do not know the inclination angle" (main text)
- Caveat (inferred, ours): Knot identification is subjective and not reproducible from the text
- Caveat (inferred, ours): Inclination uncertainty dominates the timescales
- Caveat (inferred, ours): Southern lobe contaminated by CARMA-6 and other outflows

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Knot identification procedure
- Missing: Clean parameters
- Missing: Calibrator details
- Data volume (inferred): ~50-100 GB
- Score (inferred): 3/5, Imaging settings are given, but the knot-finding method is vague and the paper is short.
- Rediscovery candidate: no, Knot identification is under-specified, and the public-data status is not stated in the paper.

## Links

- Companion: Plunkett et al. 2015 (cite: Plu15) (Earlier lower-resolution CO study of the region)

## Checks

```json
{
 "quotes": 47,
 "quotes_ok": 47,
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
  "facts": 60,
  "stated": 32,
  "rate": 0.533
 },
 "evidence_ok": true
}
```
