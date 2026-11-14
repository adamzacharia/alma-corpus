# Mapping the Release of Volatiles in the Inner Comae of Comets C/2012 F6 (Lemmon) and C/2012 S1 (ISON) Using the Atacama Large Millimeter/Submillimeter Array

`2014ApJ...792L...2C` | The Astrophysical Journal Letters 2014 | first author: Cordiner, M. A. | arXiv: 1408.2458 | DOI: 10.1088/2041-8205/792/1/L2

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: solar_system
- Question: Where are HCN, HNC and H2CO released in the inner comae of comets Lemmon and ISON (nucleus vs distributed source)?  
  > "present spatially-resolved measurements of the distributions of HNC, HCN and H$_2$CO within the comae of two comets originally from the Oort Cloud reservoir" (Introduction)
- Target **C/2012 F6 (Lemmon)**: coordinates _not stated_; z/distance rH = 1.47-1.48 AU, Delta = 1.75 AU  
  > "C/2012 F6 | 1 | 2013-06-01 | 11:52-12:32 | 29.6 | 1.47 | 1.75 | 35" (Table 1); distance from JPL Horizons  
  > "C/2012 F6 | 1 | 2013-06-01 | 11:52-12:32 | 29.6 | 1.47 | 1.75 | 35" (Table 1)
- Target **C/2012 S1 (ISON)**: coordinates _not stated_; z/distance rH = 0.54 AU, Delta = 0.88 AU  
  > "C/2012 S1 | 1 | 2013-11-17 | 11:31-12:15 | 34.2 | 0.54 | 0.88 | 85" (Table 1); distance from JPL Horizons  
  > "C/2012 S1 | 1 | 2013-11-17 | 11:31-12:15 | 34.2 | 0.54 | 0.88 | 85" (Table 1)

## Data provenance

- ALMA projects: 2012.A.00020.S, 2012.A.00033.S
- bands: Band 7, 338.6-364.6 GHz  
  > "Observations were made in Cycle 1 Early Science mode using the ALMA Band 7 receiver, covering frequencies between 338.6 and 364.6 GHz (0.82-0.89 mm)." (Observations)
- frequencies and spectral setup: Two correlator settings per comet; channel spacing 244 kHz, Hanning-smoothed resolution about 0.42 km/s  
  > "the channel spacing was 244 kHz, leading to a (Hanning smoothed) spectral resolution of about 0.42 km $\rm{s}^{-1}$" (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15.2-2733 m (Lemmon), 17.3-1284 m (ISON); 28-30 12 m antennas  
  > "C/2012 F6 | 2 | 2013-06-02 | 12:11-12:33 | 17.1 | 1.48 | 1.75 | 35 | 357.5 | 28 | 21.4-2733" (Table 1)
- angular resolution: 0.4-0.9 arcsec  
  > "The spatial resolution was 0.4-0.9$''$" (Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 17.1-45.2 min per setting  
  > "C/2012 S1 | 2 | 2013-11-17 | 12:30-13:27 | 45.2 | 0.54" (Table 1)
- observing dates: 2013 June 1-2 (Lemmon), 2013 November 17 (ISON)  
  > "Comet Lemmon was observed 2013 June 1-2 and ISON was observed 2013 November 17" (Observations)
- pi or archival as stated: _not stated_
- Line: H2CO 5(1,5)-4(1,4) (351.769 GHz)
- Line: HCN 4-3 (354.505 GHz)
- Line: HNC 4-3 (362.630 GHz)
- External data: Gas kinetic temperature 90 K for ISON  
  > "For ISON, a gas kinetic temperature $T=90$ K was adopted (cite: agu14)." (Locations of molecular production/release) [from (cite: agu14)]
- External data: Lemmon T=55 K scaled from a measurement assuming T proportional to rH^-1  
  > "For Lemmon, $T=55$ K was obtained by scaling the measurement of (cite: biv13) assuming $T\propto r_H^{-1}$." (Locations of molecular production/release) [from (cite: biv13)]
- External data: Photodestruction lifetimes of H2CO (1,280 s) and HCN (23,100 s) at 0.54 AU  
  > "1,280 s *vs.* 23,100 s for HCN at 0.54 AU; (cite: hue92)" (Molecular maps and radial profiles) [from (cite: hue92)]

## Processing

### Calibration

- pipeline or manual: Standard routines in CASA  
  > "The data were flagged, calibrated and imaged using standard routines in CASA version 4.1.0" (Observations)
- casa version: CASA 4.1.0  
  > "standard routines in CASA version 4.1.0 (cite: mcm07)" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ceres and Titan (ISON), Pallas (Lemmon); quasars for bandpass and phase  
  > "Ceres and Titan were used to calibrate ISON’s flux scale, and Pallas was used for Lemmon." (Observations)
- flux scale uncertainty: <15%  
  > "The absolute flux calibration error is expected to be less than 15%." (Observations)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: Högbom, flux threshold of 2x RMS  
  > "Deconvolution of the point-spread function (PSF) was performed using the Högbom algorithm, with natural visibility weighting and a flux threshold of twice the RMS noise in each image." (Observations)
- weighting robust: natural  
  > "with natural visibility weighting" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: Applied to ISON images (HPBW about 17.5 arcsec)  
  > "Images of ISON were therefore corrected for the response of the ALMA primary beam (half-power beam-width $\approx17.5''$)." (Observations)
- array combination: Antennae DV07, DV19, DV24, DV25 excluded (>500 m from array centre) as no signal beyond ~400 m  
  > "No signal was detected for baselines $\gtrsim400$ m, so the most distant antennae (DV07, DV19, DV24 and DV25; $>500$ m from the array center) were excluded during imaging." (Observations)
- smoothing: _not stated_
- final beam: Gaussian fit to PSF; e.g. 0.88x0.54 to 0.54x0.40 arcsec  
  > "Finally, the deconvolved images were convolved with a Gaussian fit to the PSF." (Observations)
- final rms: _not stated_

### Inherited from earlier work

- Visibility-amplitude modelling method with uniform isotropic outflow  
  > "Following the method of (cite: boi07; boi14), the interferometric visibility amplitudes for the observed molecules were modeled under the assumption of uniform, isotropic outflow." (Locations of molecular production/release) [from (cite: boi07; boi14)]
- Haser parent-daughter paradigm  
  > "In this (cite: has57) paradigm, each molecular distribution is determined by the production rate" (Locations of molecular production/release) [from (cite: has57)]

### Not stated but needed to reproduce (our reading)

- Cell size and image size
- Cube/channel velocity ranges for line integration
- Continuum channel selection and continuum subtraction
- Quasar calibrator names
- Visibility binning and uv-range and phase centre handling in the model
- Excitation model code, collision rates, and electron density
- Photodissociation rates adopted for HNC and H2CO daughters
- Noise treatment/fitting of real visibility amplitudes and error estimation for Lp

## Analysis recipe

1. **Calibrate and image**: Standard CASA calibration; Högbom CLEAN with natural weighting, remote antennae excluded; convolved with fitted Gaussian PSF  
  > "The data were flagged, calibrated and imaged using standard routines in CASA version 4.1.0" (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Radial profiles**: Azimuthally averaged flux in 0.05 arcsec annuli, normalised to first annulus, around HCN peak (continuum peak for continuum)  
  > "The average fluxes inside successive $0.05''$-thick annuli are plotted as a function of annulus radius, normalized to unity in the first annulus." (Molecular maps and radial profiles)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit visibility amplitudes with Haser model**: Model visibility amplitudes with Q and Lp free; least squares on real parts  
  > "Goodness of fit was determined by minimizing the sum of the squares of the differences between the real parts of the observed and modeled visibility amplitudes." (Locations of molecular production/release)
   - parameter: v = 1.0 km/s (ISON), 0.7 km/s (Lemmon) from HCN HWHM  
  > "Respective outflow velocities of $1.0$ km $\rm{s}^{-1}$ and $0.7$ km $\rm{s}^{-1}$ for ISON and Lemmon were obtained from the HWHM of the HCN lines." (Locations of molecular production/release)
   - assumption: T=90 K (ISON), 55 K (Lemmon); excitation by H2O and electron collisions and solar IR pumping  
  > "The molecular excitation calculation considers collisions with H$_2$O and electrons, and pumping by Solar infrared radiation." (Locations of molecular production/release)
   - fitting: Chi-square-like minimisation, Q and Lp free  
  > "with $Q$ and $L_p$ as free parameters" (Locations of molecular production/release)
   - validation: _not stated_

## Software

- **CASA** 4.1.0: Flagging, calibration, imaging  
  > "The data were flagged, calibrated and imaged using standard routines in CASA version 4.1.0" (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HCN Q, Lemmon | 2.3e26 | ~10% | s^-1 | 3 | HCN       / $4-3$             / 354.505   / 42.5     / 8.55(9)               / 2.3 |
| HCN Q, ISON | 3.5e26 | ~10% | s^-1 | 3 | For ISON, our value of $3.5\times10^{26}$ s$^{-1}$ on 2013 November 17 |
| H2CO Lp, ISON | 280 (+50/-50) | 1 sigma | km | 3 | $280^{+50}_{-50}$ |
| H2CO Lp, Lemmon | 1200 (+1200/-400) | 1 sigma | km | 3 | $1200^{+1200}_{-400}$ |
| HNC Lp, ISON | 700 (+1100/-400) | 1 sigma | km | 3 | $700^{+1100}_{-400}$ |
| Q(HNC)/Q(HCN) ISON | 34% | not stated | percent | 3 | Our $Q({\rm HNC})/Q({\rm HCN})$ ratio of 34% is somewhat larger than the value of 18% |
| Q(HNC)/Q(HCN) Lemmon | about 0.4% | not stated | percent | 3 | The $Q({\rm HNC})/Q({\rm HCN})$ ratio in comet Lemmon was only about 0.4% |

## Qualitative findings

- HCN is released from or near the nucleus; HNC distributions clumpy and asymmetric, suggesting anisotropic release; H2CO has a distributed source in both comets  
  > "For both comets, the dominant source of HCN was from (or very near to) the nucleus." (Conclusion)

## Claim tuples

- H: Is HCN a nuclear primary species? | E: Maps and visibility modelling | R: HCN Lp < 50 km in both comets | F: HCN released from or near the nucleus | **supported**
- H: Does HNC come from a distributed or anisotropic source? | E: Maps and visibilities | R: Streams/clumps up to 1000 km in ISON; distributed source required for ISON | F: HNC released in collimated outflows from refractory material | **supported**
- H: Does the H2CO parent scale length scale with solar flux? | E: Haser fits to visibilities | R: Lp a few thousand km in Lemmon, a few hundred km in ISON | F: Consistent with photolysis/thermal degradation scaling with solar flux | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Excitation differences rejected as cause of HCN/HNC difference because of near-identical upper-state energies  
  > "Variations in excitation cannot plausibly explain the observed differences between these molecules" (HCN and HNC)
- How they decided it was enough: _not stated_
- Limitation (authors): Lack of short baselines prevents ruling out additional H2CO sources with sizes >= 5 arcsec  
  > "Due to the lack of short baselines, our ALMA data cannot rule out the presence of additional H$_2$CO sources with angular sizes $\gtrsim5''$." (H2CO)
- Caveat (inferred, ours): Lemmon HNC detection is only 4.4 sigma and Lp poorly constrained
- Caveat (inferred, ours): Fixed temperature and velocity assumptions; no error treatment on these
- Caveat (inferred, ours): Short-baseline flux loss affects profiles

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters (cell, size, channel ranges)
- Missing: Excitation and visibility modelling code
- Missing: Calibrator details
- Data volume (inferred): Tens of GB raw
- Score (inferred): 3/5, ALMA project codes given and CASA version known, but the visibility model code and many imaging settings are missing.
- Rediscovery candidate: no, Model code is not described in enough detail to redo the fits.

## Links

- Method: (cite: boi07; boi14) (Visibility modelling method)
- Companion: (cite: sek14) (ISON non-gravitational acceleration and debris stream)

## Checks

```json
{
 "quotes": 51,
 "quotes_ok": 51,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 35,
  "rate": 0.53
 },
 "evidence_ok": true
}
```
