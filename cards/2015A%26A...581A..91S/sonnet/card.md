# Disentangling the jet emission from protostellar systems. The ALMA view of VLA1623

`2015A&A...581A..91S` | Astronomy and Astrophysics 2015 | first author: Santangelo, G. | arXiv: 1508.05022 | DOI: 10.1051/0004-6361/201526428

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: What are the physical properties and origin of the jets/outflows in the triple protostellar system VLA1623, as traced by high-resolution ALMA CO(2-1) compared to [OI] 63 um and SMA CO(3-2)?  
  > "The goal is to study the physical properties of the jet emission in VLA1623 at high-angular resolution." (Introduction)
- Target **VLA1623 (VLA16234-2417; sources A, B, W)**: coordinates 16h26m26.419s, -24d24m29.99s (J2000 pointing)  
  > "Pointing coordinates were $\alpha_{\rm J2000}$=16$^{\rm h}$26$^{\rm m}$26$.\!\!^{s}$419 and $\delta_{\rm J2000}$=$-$24$^\circ$24$^{\prime}$29$.\!\!^{\prime\prime}$99." (2 Observations); "Located in $\rho$ Ophiuchus (cite: loinard2008), VLA16234$-$2417 (hereafter VLA1623)" (Introduction); z/distance rho Ophiuchus; 1.1" ~132 AU implies ~120 pc (not stated explicitly)  
  > "Pointing coordinates were $\alpha_{\rm J2000}$=16$^{\rm h}$26$^{\rm m}$26$.\!\!^{s}$419 and $\delta_{\rm J2000}$=$-$24$^\circ$24$^{\prime}$29$.\!\!^{\prime\prime}$99." (2 Observations); "Located in $\rho$ Ophiuchus (cite: loinard2008), VLA16234$-$2417 (hereafter VLA1623)" (Introduction); distance from Loinard et al. 2008 (cite: loinard2008), location only  
  > "Pointing coordinates were $\alpha_{\rm J2000}$=16$^{\rm h}$26$^{\rm m}$26$.\!\!^{s}$419 and $\delta_{\rm J2000}$=$-$24$^\circ$24$^{\prime}$29$.\!\!^{\prime\prime}$99." (2 Observations); "Located in $\rho$ Ophiuchus (cite: loinard2008), VLA16234$-$2417 (hereafter VLA1623)" (Introduction)

## Data provenance

- ALMA projects: 2011.0.00902.S, 2013.1.01004.S
- bands: Band 6 (230 GHz)  
  > "Observations were done in Band 6 (230 GHz) using the extended configuration" (2 Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: extended configuration, 16 antennae  
  > "they consisted of 16 antennae with a baseline range of $\sim$36$-$400 m" (2 Observations)
- baselines: ~36-400 m  
  > "they consisted of 16 antennae with a baseline range of $\sim$36$-$400 m" (2 Observations)
- angular resolution: 0.74" x 0.58" (PA=93 deg)  
  > "The synthesised beam is 0$.\!\!^{\prime\prime}$74$\times$0$.\!\!^{\prime\prime}$58 (PA$=$93$^{\circ}$)." (2 Observations)
- max recoverable scale: 4"  
  > "The minimum baseline of 36 m yields a maximum recoverable scale of 4$^{\prime\prime}$ at the selected frequency" (2 Observations)
- sensitivity: 3-5 mJy/beam per 1 km/s channel  
  > "The rms noise is 3$-$5 mJy beam$^{-1}$ per 1 km s$^{-1}$ channel." (2 Observations)
- time on source: one hour total observing time  
  > "for a total observing time of one hour" (2 Observations)
- observing dates: April 8, 2012  
  > "on April 8, 2012 (PI Murillo)" (2 Observations)
- pi or archival as stated: PI Murillo, Cycle 0 Early Science  
  > "during the Early Science Cycle 0 phase on April 8, 2012 (PI Murillo)" (2 Observations)
- Line: CO J=2-1 (not stated)
- Other facility **SMA**: CO(3-2) maps for comparison  
  > "in comparison with previous SMA CO(3$-$2) and *Herschel*-PACS \[Oi\] 63 $\mu$m observations" (abstract)
- Other facility **Herschel-PACS**: [OI] 63 um line emission  
  > "the PACS \[Oi\] 63 $\mu$m line emission from (cite: nisini2015)" (3 Results)
- External data: Herschel-PACS [OI] 63 um maps  
  > "the PACS \[Oi\] 63 $\mu$m line emission from (cite: nisini2015)" (3 Results) [from Nisini et al. 2015 (cite: nisini2015)]
- External data: SMA CO(3-2) data  
  > "previously detected in CO(3$-$2) with SMA (cite: murillo2013a)" (3 Results) [from Murillo & Lai 2013 (cite: murillo2013a)]
- External data: Inclination of 75 deg for A outflow  
  > "assuming an inclination angle with respect to the line of sight of 75$^{\circ}$ as for the A outflow (cite: davis1999)" (3 Results) [from Davis et al. 1999 (cite: davis1999)]

## Processing

### Calibration

- pipeline or manual: _not stated_
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

- Observation details, calibration and data reduction  
  > "The details of the observations, calibration, and data reduction were presented in (cite: murillo2013b)." (2 Observations) [from Murillo et al. 2013b (cite: murillo2013b)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration details (deferred to Murillo+2013b)
- Imaging weighting/robust, cell and image size, deconvolution
- Continuum subtraction method and line-free channels
- Rest frequency and velocity systemic value used
- Channel map velocity ranges and integration limits for moment maps
- Which project code corresponds to the data used (two codes in acknowledgements)
- Distance adopted

## Analysis recipe

1. **Image and analyse CO(2-1) data**: Data analysed with GILDAS; velocity-integrated and channel maps compared with SMA CO(3-2) and PACS [OI]  
  > "Data was analysed using the GILDAS[^1] package." (2 Observations)
   - software: GILDAS
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive de-projected jet velocities and dynamical timescales**: Correct projected velocities for inclination; timescale from projected distance and velocity  
  > "assuming an inclination angle of 75$^{\circ}$ as for the A outflow (cite: davis1999), the dynamical timescale of Br1 and Bb1" (4 Discussion)
   - assumption: Inclination 75 deg (A outflow value), alternative 45 deg  
  > "Even assuming an inclination angle of 45$^{\circ}$, de-projected velocities of about 20 km s$^{-1}$ are derived." (3 Results)
   - fitting: _not stated_
   - validation: Compared two scenarios (precessing A jet vs jet from B) using alignment and PV diagram  
  > "Two possible scenarios may explain the present observational results: 1) precession of the A jet, and 2) the presence of a fast compact jet associated with source B." (4 Discussion)

## Software

- **GILDAS** : Data analysis  
  > "Data was analysed using the GILDAS[^1] package." (2 Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| De-projected velocity of collimated jet (i=75 deg) | 54 | not stated | km/s | 2 | correspond to de-projected velocities of 54 km s$^{-1}$ |
| De-projected velocity (i=45 deg) | ~20 | not stated | km/s | 2 | de-projected velocities of about 20 km s$^{-1}$ are derived |
| Dynamical timescale of Br1/Bb1 (i=75 deg) | ~4 | not stated | yr | 2 | is $\sim$4 yr. |
| Dynamical timescale of Br1/Bb1 (i=45 deg) | ~14 | not stated | yr | 2 | the dynamical timescale would be $\sim$14 yr. |

## Qualitative findings

- Newly detected collimated jet component associated with [OI] 63 um at ~8" from B, inversely oriented to the A large-scale outflow  
  > "This newly detected jet component is inversely oriented with respect to the large-scale outflow driven by source A" (abstract)
- No compact outflow emission associated with source W  
  > "Finally, no compact outflow emission is associated with source W." (abstract)

## Claim tuples

- H: Does source B drive its own fast, collimated jet distinct from A's outflow? | E: ALMA CO(2-1) maps compared with [OI] and SMA CO(3-2); PV diagram along the B jet | R: Collimated red/blue knots aligned with B and with closest [OI] peaks, misaligned with A disk perpendicular | F: Source B likely younger than A and drives a faster, more compact jet | **partially**
- H: Does source W drive a compact outflow? | E: Search in ALMA CO(2-1) maps | R: No compact outflow emission | F: W may be older, or its outflow is filtered out | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Precessing A jet scenario, not firmly excluded but disfavoured by the alignment of secondary [OI] peaks with the A disk perpendicular  
  > "However, the direction of the secondary, hence (in this view) of older \[Oi\] 63 $\mu$m peaks, is consistent with the direction perpendicular to the A disk" (4 Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Interferometric filtering removes extended emission near systemic velocity and the large-scale outflow  
  > "the lack of CO emission in our map near the systemic velocity is probably due to interferometric spatial filtering" (4 Discussion)
- Caveat (inferred, ours): No quantitative uncertainties on velocities or timescales
- Caveat (inferred, ours): Short note with no stated imaging parameters
- Caveat (inferred, ours): Only extended configuration data; interpretation is qualitative and ambiguous between scenarios

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Calibration and imaging recipe (in Murillo+2013b)
- Missing: Exact map parameters and integration velocity ranges
- Missing: Reduced SMA and PACS data
- Data volume (inferred): ~5-20 GB raw
- Score (inferred): 2/5, Short research note; processing deferred to another paper and results are mainly qualitative.
- Rediscovery candidate: no, Recipe incomplete and results mostly qualitative.

## Links

- Method: Murillo et al. 2013b (cite: murillo2013b) (Observations, calibration and reduction of the ALMA data)
- Companion: Murillo & Lai 2013 (cite: murillo2013a) (SMA CO(3-2) and triple system identification)
- Companion: Nisini et al. 2015 (cite: nisini2015) (Herschel-PACS [OI] observations)

## Checks

```json
{
 "quotes": 41,
 "quotes_ok": 41,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 61,
  "stated": 28,
  "rate": 0.459
 },
 "evidence_ok": true
}
```
