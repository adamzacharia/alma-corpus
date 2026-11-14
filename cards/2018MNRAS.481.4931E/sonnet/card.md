# ALMA reveals the aftermath of a white dwarf-brown dwarf merger in CK Vulpeculae

`2018MNRAS.481.4931E` | Monthly Notices of the Royal Astronomical Society 2018 | first author: Eyres, S. P. S. | arXiv: 1809.05849 | DOI: 10.1093/mnras/sty2554

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: stellar_physics, evolved_stars, astrochemistry
- Question: What are the dust and molecular gas structures in the inner region of CK Vul, and what do they imply about the origin of the 1670 event?  
  > "Here we present high spatial resolution imaging of the dust emission from the inner $\sim24\ensuremath{''}$ of the system, taken with the Atacama Large Millimeter–Submillimeter Array (cite: alma)." (Introduction)
- Target **CK Vul (Nova Vul 1670)**: coordinates _not stated_; z/distance 700 pc  
  > "we adopt a value of $D=700$ pc throughout (cite: hajduk-ck2; kaminski-n)" (3.1 The dust); distance from adopted from Hajduk et al. 2013 and Kaminski et al. 2015  
  > "we adopt a value of $D=700$ pc throughout (cite: hajduk-ck2; kaminski-n)" (3.1 The dust)

## Data provenance

- ALMA projects: 2016.1.00448.S
- bands: Band 6  
  > "Observations were made of CK Vul with ALMA at Band 6" (Observations)
- frequencies and spectral setup: four 1.875 GHz SPWs centred on 224, 226, 240, 242 GHz; 128 channels each  
  > "in four spectral windows 1.875 GHz in width and centred on 224 GHz, 226 GHz, 240 GHz and 242 GHz." (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C40-3 and an intermediate array similar to C40-6  
  > "10 min 8 sec in array configuration C40–3; and 23 min 18 sec in an intermediate array of approximately the same antenna distribution as array configuration C40–6." (Observations)
- baselines: C40-3: 15.1 m to 460 m; C40-6: 16.7 m to 3.7 km  
  > "with a maximum baseline of 460 m and minimum baseline of 15.1 m." (Observations); "with a maximum baseline of 3.7 km and minimum baseline of 16.7 m." (Observations)
- angular resolution: 280 x 250 mas continuum beam  
  > "The resultant image has a beam of 280 milliarcsec by 250 milliarcsec, with the major axis at position angle $-177^\circ$." (Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 10 min 8 s (C40-3); 23 min 18 s (C40-6)  
  > "10 min 8 sec in array configuration C40–3; and 23 min 18 sec" (Observations)
- observing dates: 2017 April 24 and 2017 July 22  
  > "The C40–3 data were taken starting at 2017 April 24 11:47:53 UT" (Observations); "The C40–6 data were taken starting at 2017 July 22 03:26:07 UT" (Observations)
- pi or archival as stated: _not stated_
- Line: C17O not stated (224.695 GHz)
- Line: CH3OH not stated (241.756 GHz)
- Line: CN not stated (226.634 GHz)
- External data: Dual grey body SED model (T=15 K and 49 K), gas mass ~1 Msun, CO column density, and 75.0 mJy flux  
  > "(cite: kaminski-n) have a dual grey body model for the CK Vul mm/sub–mm SED, with dust temperatures $T=15$ K and $T=49$ K." (3.1.2) [from Kaminski et al. 2015 (cite: kaminski-n)]
- External data: Amorphous carbon mass absorption coefficient 66 cm2/g at 1100 um  
  > "we use the mass absorption coefficient for amorphous carbon (“AC”) from (cite: menella), who give a value 66 cm$^2$ g$^{-1}$ at 1100$\,\mu$m." (3.1.2) [from Mennella et al. 1995 (cite: menella)]

## Processing

### Calibration

- pipeline or manual: standard pipeline scripts from archive  
  > "The data were recovered from the ALMA archive and calibrated using the standard scripts provided by the pipeline." (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J2148+0657 (C40-3); J1751+0939 (C40-6)  
  > "using J2148+0657 as flux calibrator (cite: vanK)" (Observations); "using J1751+0939 as flux and bandpass calibrators" (Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean for continuum; concat to combine  
  > "The continuum channels were used to derive a map of the dust emission, using casa task tclean." (Observations)
- deconvolver: _not stated_
- weighting robust: Briggs robust=2  
  > "Briggs weighting was applied with robust=2." (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub  
  > "These channel ranges were then used to remove the continuum data in the $uv$ plane, using uvcontsub." (Observations)
- line free channels: SPW0 25-118; SPW1 50-75, 90-118; SPW2 all; SPW3 9-35, 95-119 (continuum channels)  
  > "SPW0 25 to 118; SPW1 50 to 75 and 90 to 118; SPW2 all; and SPW3 9 to 35 and 95 to 119." (Observations)
- primary beam correction: _not stated_
- array combination: concat of the two uv datasets, copypointing=False  
  > "with default settings except copypointing=False as we are not mosaicing." (Observations)
- smoothing: _not stated_
- final beam: 280 x 250 mas, PA -177 deg  
  > "The resultant image has a beam of 280 milliarcsec by 250 milliarcsec, with the major axis at position angle $-177^\circ$." (Observations)
- final rms: _not stated_

### Inherited from earlier work

- Distance D=700 pc adopted  
  > "we adopt a value of $D=700$ pc throughout (cite: hajduk-ck2; kaminski-n)" (3.1 The dust) [from (cite: hajduk-ck2; kaminski-n)]
- 15 K dust temperature taken from the SED  
  > "The SED in (cite: kaminski-n) shows the 15 K emission dominates at 230 GHz." (3.1.2) [from (cite: kaminski-n)]

### Not stated but needed to reproduce (our reading)

- Image size, cell size, masking, deconvolver, cleaning threshold
- Spectral cube channel width and rest-frame/velocity settings
- Whether tclean used the combined data and any primary beam correction
- CASA and pipeline versions
- Flux scale uncertainty
- Integration ranges and moment/PV extraction details
- CO column density value used for H2 mass

## Analysis recipe

1. **Combine and calibrate data**: Pipeline calibration, then concat of two configurations  
  > "The two sets of calibrated data were then combined into a single $uv$ measurement set using casa task concat(cite: mcmullin2007)" (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Image continuum and cubes**: tclean on continuum channels; uvcontsub then spectral cubes  
  > "The continuum–subtracted data in each spectral window were then imaged in spectral cube mode to allow examination of the emission." (Observations)
   - software: CASA
   - parameter: robust=2  
  > "Briggs weighting was applied with robust=2." (Observations)
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure dust flux and mass**: Pixel counting within contours, then optically thin mass formula  
  > "we have estimated the flux density using a “pixel counting” method." (3.1.2)
   - parameter: 0.48 mJy/beam contour inner; 0.12 mJy/beam contour total  
  > "we added up the total flux included within the 0.48 mJy beam$^{-1}$ contour" (3.1.2)
   - assumption: D=700 pc, T=15 K, amorphous carbon kappa=66 cm2/g at 1100 um, wavelength 1249 um  
  > "Using this as the temperature of the dust in Fig. [2](#maps)(a), we find a total mass of $M_{\rm dust} \sim
2.04\times10^{-4}$ M$_\odot$." (3.1.2)
   - fitting: _not stated_
   - validation: Uncertainty from rms in emission-free regions  
  > "Estimates of uncertainty were made by calculating the rms brightness in regions containing no dust emission." (3.1.2)
4. **Estimate gas mass and gas-to-dust ratio**: Recompute H2 mass from literature CO column density  
  > "Assuming the CO column density in (cite: kaminski-n), and a CO/H$_2$ ratio of $\sim10^{-3}$ (appropriate for carbon–rich AGB winds), we recalculated a H$_2$ mass of $\sim9.8\times10^{-3}$ M$_\odot$." (3.1.2)
   - assumption: CO/H2 ~1e-3 (carbon-rich); oxygen-rich case gives 3.9e-2 Msun  
  > "If the nebula is considered oxygen–rich, this will give a value $\sim3.9\times10^{-2}$ M$_\odot$." (3.1.2)
   - fitting: _not stated_
   - validation: _not stated_
5. **Map line emission and kinematics**: Integrated intensity maps and position-velocity cuts along N-S  
  > "A position–velocity plot is included in Fig. [3](#maps1)(b)." (3.2 The lines)
   - software: Starlink rv
   - parameter: vLSR = -38 km/s  
  > "Assuming $v_{\rm LSR}=-38$ km s$^{-1}$ calculated for 2017 April 24." (Table 1)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : concat, tclean, uvcontsub  
  > "using casa task tclean." (Observations)
- **Starlink rv** : vLSR calculation  
  > "obtained using the Starlink rv package (cite: wallace; currie)" (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total dust flux density | 132.84 | 0.04 | mJy | 3 | finding a value of 132.84$\pm$0.04 mJy |
| Inner region flux density | 31.31 | 0.04 | mJy | 3 | gave a total flux density of 31.31$\pm$0.04 mJy |
| Total dust mass | 2.04e-4 | not stated | Msun | 3 | we find a total mass of $M_{\rm dust} \sim
2.04\times10^{-4}$ M$_\odot$. |
| Gas-to-dust ratio | ~50 to 200 | not stated | dimensionless | 4 | the gas–to–dust ratio is $\sim50$ to 200 |
| Bubble expansion velocity | ~140 | not stated | km/s | 5 | two bubbles expanding at $\sim140$ km s$^{-1}$ |

## Qualitative findings

- Dust forms two cocoons with a central warped disc; CH3OH traces an S-shaped precessing jet; CN traces bubbles.  
  > "CN lines trace bubbles within the dusty cocoons; CH$_3$OH a north–south S–shaped jet" (abstract)

## Claim tuples

- H: Is the CK Vul event a stellar merger of main-sequence or giant stars? | E: Compared ALMA-derived ejecta mass and literature luminosity with merger models | R: Luminosity and mass constraints exclude those models | F: A white dwarf plus brown dwarf merger is proposed instead | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Main-sequence/giant stellar mergers and planet ingestion rejected based on luminosity and timescales.  
  > "We also exclude planet ingestion as this cannot explain the duration of the brightening events in the 1670s." (Conclusions)
- How they decided it was enough: _not stated_
- Limitation (authors): Velocity resolution is modest and dynamical modelling is deferred.  
  > "We defer modelling of the dynamics of these emission lines to a future, more detailed, paper" (Observations)
- Caveat (inferred, ours): Dust mass depends on assumed T=15 K, kappa and D=700 pc
- Caveat (inferred, ours): Uncertainties on masses are only statistical
- Caveat (inferred, ours): Merger conclusion rests on exclusion arguments, not direct tests
- Caveat (inferred, ours): Pixel-counting flux depends on contour choice

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters beyond robust
- Missing: CASA version
- Missing: CO column density value
- Data volume (inferred): ~20-50 GB
- Score (inferred): 3/5, Data and project code are given and the dust mass recipe is explicit, but many imaging parameters are missing.
- Rediscovery candidate: no, Public-data status is not explicitly stated and imaging details are incomplete.

## Links

- Companion: Kaminski et al. 2015 (cite: kaminski-n) (Prior SMA and APEX results, SED model, and gas mass)

## Checks

```json
{
 "quotes": 52,
 "quotes_ok": 52,
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
  "facts": 72,
  "stated": 38,
  "rate": 0.528
 },
 "evidence_ok": true
}
```
