# Gas infall and possible circumstellar rotation in R Leonis

`2019A&A...622L..14F` | Astronomy and Astrophysics 2019 | first author: Fonfría, J. P. | arXiv: 1902.02574 | DOI: 10.1051/0004-6361/201834840

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars
- Question: What is the structure and kinematics of the innermost envelope of the AGB star R Leo (continuum, CO and 29SiO lines) at up to 0.026" resolution?  
  > "we present new interferometer observations of CO and $^{29}$SiO toward the AGB star R Leo carried out with the Atacama Large Millimeter Array (ALMA) with an angular resolution of up to 0$.\!\!^{\prime\prime}$026" (Introduction)
- Target **R Leo**: coordinates RA 09h47m33.4915s, Dec +11d25m42.899s  
  > "R Leo is an O-rich Asymptotic Giant Branch star (AGB) located at $\simeq70-85$ pc from Earth (cite: debeck_2010; ramstedt_2014)." (Introduction); "peaking at $(\textnormal{RA},\textnormal{DEC})=(09^h47^m33.\!\!^s4915\pm0.\!\!^s0004,11^\circ25^\prime 42\ensuremath{.\!\!^{\prime\prime}}899\pm0\ensuremath{.\!\!^{\prime\prime}}005)$" (3.1 The structure of the continuum emission); z/distance ~70-85 pc  
  > "R Leo is an O-rich Asymptotic Giant Branch star (AGB) located at $\simeq70-85$ pc from Earth (cite: debeck_2010; ramstedt_2014)." (Introduction); "peaking at $(\textnormal{RA},\textnormal{DEC})=(09^h47^m33.\!\!^s4915\pm0.\!\!^s0004,11^\circ25^\prime 42\ensuremath{.\!\!^{\prime\prime}}899\pm0\ensuremath{.\!\!^{\prime\prime}}005)$" (3.1 The structure of the continuum emission); distance from De Beck et al. 2010; Ramstedt & Olofsson 2014  
  > "R Leo is an O-rich Asymptotic Giant Branch star (AGB) located at $\simeq70-85$ pc from Earth (cite: debeck_2010; ramstedt_2014)." (Introduction); "peaking at $(\textnormal{RA},\textnormal{DEC})=(09^h47^m33.\!\!^s4915\pm0.\!\!^s0004,11^\circ25^\prime 42\ensuremath{.\!\!^{\prime\prime}}899\pm0\ensuremath{.\!\!^{\prime\prime}}005)$" (3.1 The structure of the continuum emission)

## Data provenance

- ALMA projects: 2016.1.01202.S
- bands: _not stated_
- frequencies and spectral setup: Four spectral windows, 212.7-216.8 and 227.5-231.5 GHz, 488 kHz channels  
  > "Four spectral windows covered the frequency ranges $212.7-216.8$ and $227.5-231.5$ GHz with a channel width of 488 kHz." (Observations)
- continuum bandwidth: _not stated_
- arrays: Configurations C40-2, C40-5, C40-6, C43-9 (Cycles 4 and 5)  
  > "Array configurations C40-2, C40-5, C40-6, and C43-9 were used providing baselines from 15 m up to 13.9 km." (Observations)
- configurations: _not stated_
- baselines: 15 m to 13.9 km  
  > "providing baselines from 15 m up to 13.9 km" (Observations)
- angular resolution: Up to 0.026"  
  > "with a maximum angular resolution of $\simeq0\ensuremath{.\!\!^{\prime\prime}}026$ and a MRS $\simeq0\ensuremath{.\!\!^{\prime\prime}}6$" (Summary and Conclusions)
- max recoverable scale: 1.6" (C40-6) down to 0.4-0.6" (C43-9); ~0.6" for highest resolution  
  > "a MRS $\simeq0\ensuremath{.\!\!^{\prime\prime}}6$" (Summary and Conclusions)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2016-Oct-01 to 2017-Oct-27  
  > "C43-9/B   | 2017-Oct-27" (Table 1)
- pi or archival as stated: _not stated_
- Line: CO v=0, J=2-1 (not stated)
- Line: CO v=1, J=2-1 (not stated)
- Line: 29SiO v=0, J=5-4 (not stated)
- Line: 29SiO v=1, J=5-4 (not stated)
- External data: 7 mm continuum size of R Leo vs pulsation phase, used to estimate expected size at phase 0.50  
  > "We can estimate the size of the continuum source at 7 mm at the same pulsation phase as during our observations" (3.1 The structure of the continuum emission) [from Matthews et al. 2018 (cite: matthews_2018)]
- External data: Systemic velocity of -0.5 km/s  
  > "systemic velocity of $-0.5$ km s$^{-1}$ (cite: teyssier_2006)" (Complex molecular line profiles) [from (cite: teyssier_2006)]
- External data: Pulsation period 310 days and JDmax=2457896 from AAVSO  
  > "pulsation period $=310$ days; JD$_\textnormal{\tiny{max}}=2457896$ following AAVSO" (Table 1) [from AAVSO]

## Processing

### Calibration

- pipeline or manual: Pipeline  
  > "The data calibration was done with the pipeline in CASA 4.7.2" (Observations)
- casa version: CASA 4.7.2  
  > "The data calibration was done with the pipeline in CASA 4.7.2" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0854+2006 or J1058+0133  
  > "The flux, bandpass, and pointing were calibrated in the usual way by observing J0854+2006 or J1058+0133." (Observations)
- flux scale uncertainty: ~5%  
  > "We estimate a flux error $\simeq5\%$." (Observations)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: robust = 1.0 (natural) and 0.1 (uniform) in GILDAS  
  > "Imaging restoration was done adopting a robust parameter of 1.0 and 0.1 (natural and uniform weightings, hereafter)." (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: C40-6 and C43-9 not merged due to pulsation phase incoherence and ~1.1 yr lag  
  > "the data taken with the C40-6 and C43-9 configurations have not been merged to prevent artefacts" (Observations)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Positional uncertainty method from phase calibrator peak position scatter  
  > "from the standard deviation of the emission peak position of the phase calibrator over time (cite: menten_2006; fonfria_2014)" (Observations) [from (cite: menten_2006; fonfria_2014)]
- Larger-scale envelope analysis deferred  
  > "will be presented elsewhere (Fonfría et al., *in preparation*)" (Observations) [from Fonfría et al., in preparation]

### Not stated but needed to reproduce (our reading)

- Rest frequencies and velocity channel widths used for line maps
- Continuum channel selection / line-free channels and continuum subtraction
- Cell size, image size, masking and clean parameters in GILDAS
- Primary beam correction details
- Self-calibration usage
- Details of two-Gaussian fitting procedure
- Details of PV diagram extraction and the infall/rotation model
- Spectral window to line assignment

## Analysis recipe

1. **Calibrate visibilities**: Pipeline calibration; run A of C43-9 discarded due to spikes  
  > "The data quality highly increased during the second run (run B) and run A was deprecated." (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Image continuum and lines per configuration**: Imaging in GILDAS with natural and uniform weighting  
  > "Mapping and data analysis were almost fully performed with GILDAS" (Observations)
   - software: GILDAS
   - fitting: _not stated_
   - validation: _not stated_
3. **Characterise continuum with Gaussian components**: Two Gaussian components fitted (compact + extended); compared with expected 7 mm size  
  > "The continuum emission can be described by two Gaussian-like components: one compact and one extended" (3.1 The structure of the continuum emission)
   - software: GILDAS
   - assumption: Compact component taken as the star  
  > "For simplicity, we hereby consider this compact component as the star." (3.1 The structure of the continuum emission)
   - fitting: Gaussian fit; statistical errors <~5%  
  > "The statistical errors of the Gaussian fit are always $\lesssim5\%$." (Table 1)
   - validation: _not stated_
4. **Analyse line profiles and velocity-channel maps**: Spectra at central pixel, integrated maps in velocity intervals and position-velocity diagram  
  > "The position-velocity diagram along the Southeast-Northwest direction" (3.3 Gas infall and hints of rotation)
   - software: GILDAS
   - assumption: Orbital gas with M~0.5-1.0 Msun, inclination 25-50 deg reproduces Doppler shift  
  > "A similar Doppler shift is expected for gas orbiting a star with a mass of $\simeq 0.5-1.0~M_\odot$ if an orbital inclination of $\simeq 25^\circ-50^\circ$ is assumed." (3.3 Gas infall and hints of rotation)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.2: Pipeline calibration  
  > "The data calibration was done with the pipeline in CASA 4.7.2" (Observations)
- **GILDAS** : Mapping and data analysis  
  > "Mapping and data analysis were almost fully performed with GILDAS" (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum position RA (peak) | 09h47m33.4915s | 0.0004 s | hms | 3 | $(\textnormal{RA},\textnormal{DEC})=(09^h47^m33.\!\!^s4915\pm0.\!\!^s0004 |
| Compact continuum component size (C43-9/B uniform) | 0.045" x 0.030", PA 155 deg | <~5% (statistical) | arcsec | 3 | 16.5              / $0.045\times0.030$ / 155 |
| Extended continuum component ellipticity | 0.83 | not stated | dimensionless | 3 | The ellipticity of this component is $e=1-\theta_\textnormal{\tiny{min}}/\theta_\textnormal{\tiny{maj}}\simeq0.83$ |
| Expected 7 mm continuum size at phase 0.50 | 0.035" x 0.025" | 0.006" x 0.003" | arcsec | 3 | $\simeq (0\ensuremath{.\!\!^{\prime\prime}}035\pm 0\ensuremath{.\!\!^{\prime\prime}}006)\times(0\ensuremath{.\!\!^{\prime\prime}}025\pm 0\ensuremath{.\!\!^{\prime\prime}}003)$ |
| Continuum peak, C43-9/B natural | 45.10 | 0.21 | mJy/beam | 2 | $45.10\pm0.21$ |
| Red-shifted absorption depth (CO v=0, 29SiO v=0 at 0.17") | ~25% of continuum, peaking at ~8 km/s | not stated | % / km/s | 4 | a prominent red-shifted absorption of $\simeq25\%$ of the continuum peaking at $\simeq8$ km s$^{-1}$ |

## Qualitative findings

- Line profiles show red-shifted absorption extending to ~10-15 km/s, above terminal velocity, indicating gas moving away from us in front of the star (inverse P-Cygni in CO)  
  > "All these absorptions extend up to velocities $\simeq10-15$ km s$^{-1}$, higher than the terminal expansion velocity" (Complex molecular line profiles)

## Claim tuples

- H: Is there a compact stellar continuum plus extended dust component? | E: Two-Gaussian fit of the highest-resolution continuum maps | R: Compact source larger than expected 7 mm stellar size plus extended NE-SW component of ellipticity 0.83 | F: A dusty shell around the star with an elongated extended dust component | **supported**
- H: Does the innermost envelope host rotation and/or infall? | E: CO and 29SiO channel maps and PV diagram | R: A ~0.1" torus-like structure with PV diagram like rotating disks plus infalling gas | F: Possible rotating structure with infall or pulsation-driven red-shifted absorption (two models) | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Discrete ballistic clumps rejected since velocity field is highly continuous  
  > "our observations show a highly continuous velocity field around the star difficult to explain assuming randomly ejected, discrete clumps" (3.3 Gas infall and hints of rotation)
- Alternative: Alternative model: red-shifted absorption due to photospheric pulsation motions without infall  
  > "The red-shifted absorptions would be produced by radial movements of photospheric layers (or convective cells) due to the stellar pulsation" (3.3 Gas infall and hints of rotation)
- How they decided it was enough: _not stated_
- Limitation (authors): Array may filter extended emission, so brightness temperatures unreliable  
  > "the array could be filtering emission, preventing us to derive reliable brightness temperatures for the star." (3.1 The structure of the continuum emission)
- Limitation (authors): Resolution insufficient to explore the photosphere  
  > "the angular resolution of our observations is insufficient to explore the stellar photosphere" (3.3 Gas infall and hints of rotation)
- Caveat (inferred, ours): Rotation and infall interpretation is qualitative, with no kinematic modelling
- Caveat (inferred, ours): Different pulsation phases between configurations confound comparisons
- Caveat (inferred, ours): Missing flux from MRS limits continuum interpretation

## Reproducibility

- Data public (paper): Project code given; public status not stated  
  > "under the frame of project 2016.1.01202.S" (Observations)
- Products in archive: _not stated_
- Missing: GILDAS imaging parameters
- Missing: Line cube velocity settings
- Missing: Gaussian fit procedure details
- Missing: PV cut parameters
- Data volume (inferred): ~100-300 GB raw across several configurations
- Score (inferred): 4/5, Data identified and tools named, but imaging and line-analysis details are sparse and results mostly qualitative.
- Rediscovery candidate: no, Main results are largely qualitative and the recipe lacks imaging detail.

## Links

- Companion: Fonfría et al., in preparation (Larger-scale envelope analysis of the same data)

## Checks

```json
{
 "quotes": 53,
 "quotes_ok": 53,
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
  "facts": 69,
  "stated": 36,
  "rate": 0.522
 },
 "evidence_ok": true
}
```
