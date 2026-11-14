# The extended molecular envelope of the asymptotic giant branch star π<SUP>1</SUP> Gruis as seen by ALMA. I. Large-scale kinematic structure and CO excitation properties

`2017A&A...605A..28D` | Astronomy and Astrophysics 2017 | first author: Doan, L. | arXiv: 1709.09435 | DOI: 10.1051/0004-6361/201730703

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars
- Question: What are the 3D structure, density and temperature distribution of the pi1 Gru circumstellar envelope, constrained by spatially resolved CO rotational lines?  
  > "The aim is to make a 3D model of the CSE and to constrain the density and temperature distribution using new spatially resolved observations of the CO rotational lines." (abstract)
- Target **pi1 Gru**: coordinates _not stated_; z/distance about 150 pc  
  > "$\pi^{1}$ Gru is an evolved, S-type AGB star (cite: vecketal98) at a distance of about 150 pc (cite: per97)" (Introduction); distance from Hipparcos (Perryman et al. 1997)  
  > "$\pi^{1}$ Gru is an evolved, S-type AGB star (cite: vecketal98) at a distance of about 150 pc (cite: per97)" (Introduction)

## Data provenance

- ALMA projects: 2012.1.00524.S
- bands: _not stated_
- frequencies and spectral setup: four 2 GHz spectral windows centred on 331, 333, 343, 345 GHz; four-point mosaic  
  > "They were performed using four spectral windows with a width of 2 GHz each, centered on 331, 333, 343, and 345 GHz." (2.1 New CO radio line observations with ALMA)
- continuum bandwidth: _not stated_
- arrays: ALMA-ACA plus ALMA-TP (three 12m antennas, single-dish OTF); SMA for 12CO 2-1  
  > "This array included three 12m antennas, and the observations were performed in single-dish, on-the-fly mapping mode." (2.1 New CO radio line observations with ALMA)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 12CO 3-2: 4.56"x2.56"; 13CO 3-2: 5.19"x2.57"; TP beam 19" at 345 GHz  
  > "$4.56\ensuremath{''}\times2.56\ensuremath{''}$" (Table 1); "The beam size of the TP observation is $19\ensuremath{''}$ at 345 GHz" (2.1 New CO radio line observations with ALMA)
- max recoverable scale: _not stated_
- sensitivity: rms 0.051 Jy/beam (12CO 3-2), 0.045 Jy/beam (13CO 3-2) in combined cubes  
  > "| $^{13}$CO $J$=3-2 | 330.588 | ALMA-ACA | 23.7 | 67.1 | 3 | $5.19\ensuremath{''}\times2.57\ensuremath{''}$ | 0.045 |" (Table 1)
- time on source: ACA 23.7 min; TP 67.1 min  
  > "| $^{12}$CO $J$=3-2 | 345.796 | ALMA-ACA | 23.7 | 67.1 | 2 |" (Table 1)
- observing dates: ACA in 2013; TP in cycle 2 (2015)  
  > "The $^{12}$CO and $^{13}$CO $J$=3-2 emission was observed with the ALMA-ACA in 2013." (2.1 New CO radio line observations with ALMA)
- pi or archival as stated: _not stated_
- Line: 12CO J=3-2 (345.796 GHz)
- Line: 13CO J=3-2 (330.588 GHz)
- Other facility **SMA**: 12CO J=2-1 data (2004), recalibrated and reimaged  
  > "In this study, the upper sideband data has been recalibrated and reimaged using CASA." (2.2 Previously published CO radio line observations)
- Other facility **Herschel/HIFI**: 12CO J=5-4 and 9-8 line profiles, used without recalibration  
  > "In this paper, we adopted the line profiles without any recalibration." (2.2 Previously published CO radio line observations)
- Other facility **APEX**: 12CO J=3-2 profile to check recovered flux  
  > "The $^{12}$CO $J$=3-2 line profile from APEX (cite: rams06) is also plotted to evaluate the recovered flux in the combined ALMA data." (3.2 Line profiles)
- External data: 12CO J=2-1 SMA data originally published  
  > "The data has previously been published by (cite: chiuetal06)." (2.2 Previously published CO radio line observations) [from (cite: chiuetal06)]
- External data: Herschel/HIFI line profiles, setup and reduction  
  > "The technical setup, data reduction, and line profiles were published in (cite: dani15)." (2.2 Previously published CO radio line observations) [from (cite: dani15)]
- External data: 12CO abundance relative to H2 of 6.5e-4  
  > "a value of 6.5$\times 10^{-4}$ (cite: knapetal99) was adopted" (4.2 Density and temperature distribution) [from (cite: knapetal99)]

## Processing

### Calibration

- pipeline or manual: CASA used for calibration and imaging; manual vs pipeline not stated  
  > "We used the Common Astronomy Software Application (CASA) for calibration and imaging (cite: casa)." (2.1 New CO radio line observations with ALMA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Uranus (ACA); bandpass J0006-0623, gain J2235-4835  
  > "Uranus was used for flux calibration." (2.1 New CO radio line observations with ALMA)
- flux scale uncertainty: TP calibration about 5%  
  > "The overall uncertainty of the TP calibration is about 5%." (2.1 New CO radio line observations with ALMA)
- self calibration: _not stated_

### Imaging

- task: CLEAN with iteratively decreasing threshold  
  > "Then the ALMA-ACA data was re-imaged using the CLEAN package in an iterative procedure with a decreasing threshold parameter." (2.1 New CO radio line observations with ALMA)
- deconvolver: _not stated_
- weighting robust: 13CO 3-2 natural weighting; SMA Briggs (robust not stated)  
  > "the $^{13}$CO $J$=3-2 visibility data was imaged using natural weighting to improve the sensitivity." (2.1 New CO radio line observations with ALMA)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: TP regridded, used as clean model, then ACA and TP combined with FEATHER  
  > "Finally, the ALMA-TP and ALMA-ACA images were combined via the FEATHER package." (2.1 New CO radio line observations with ALMA)
- smoothing: binned from ~0.5 km/s to 2 km/s (12CO) and 3 km/s (13CO)  
  > "has been binned to 2 km s$^{-1}$ for $^{12}$CO $J$=3-2 and 3 km s$^{-1}$ for $^{13}$CO $J$=3-2" (2.1 New CO radio line observations with ALMA)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Microturbulent velocity of 2 km/s  
  > "A microturbulent velocity of 2 km s$^{-1}$ (cite: chiuetal06) was adopted." (4.3 Radiative transfer modeling and imaging) [from (cite: chiuetal06)]
- Temperature law form adopted from earlier torus models  
  > "(cite: chiuetal06) and (cite: knapetal99) successfully applied this temperature distribution when they modeled the torus." (4.2 Density and temperature distribution) [from (cite: goldetal76); (cite: chiuetal06); (cite: knapetal99)]

### Not stated but needed to reproduce (our reading)

- Robust value and clean mask/threshold for ACA and SMA imaging
- Line-free channels for continuum
- SHAPE model files and the feather scaling
- Stellar position and coordinates
- Number of ACA configurations/pointings and SMA calibration details
- Quantitative uncertainties on model parameters; chi-square values not given

## Analysis recipe

1. **Calibrate and image ACA, TP, SMA data**: Calibrate in CASA, clean ACA with TP as model, feather ACA with TP  
  > "In this procedure the ALMA-TP map was used as a model for initial cleaning." (2.1 New CO radio line observations with ALMA)
   - software: CASA
   - fitting: _not stated_
   - validation: Combined maps recover ~90% of APEX flux  
  > "The combined ALMA maps contain $\backsim$90% of the flux observed by APEX in 2005, which is within the calibration uncertainties." (3.2 Line profiles)
2. **Build 3D non-LTE radiative transfer model**: Three-component envelope (torus, central component, bipolar outflow) with power-law density and temperature; LVG non-LTE level populations in SHAPEMOL  
  > "calculates the non-LTE level populations via the large velocity gradient (LVG) approximation." (4.3 Radiative transfer modeling and imaging)
   - software: SHAPE, SHAPEMOL
   - parameter: 128^3 grid cells, 150 channels over +-100 km/s, 17 lowest rotational transitions  
  > "The envelope was constructed of 128$^3$ grid cells and rendered through a velocity interval of $\pm$100 km s$^{-1}$ around the systemic velocity." (4.3 Radiative transfer modeling and imaging)
   - assumption: distance 150 pc; 12CO/H2 = 6.5e-4  
  > "assuming a distance of 150 pc (cite: per97)" (5.1 Finding the best-fit model)
   - fitting: Manual parameter adjustment, by eye on channel maps and line profiles; chi-square on line profiles with 20% assumed uncertainty  
  > "$\sigma$ is the measurement uncertainty of the observed flux, assumed to be 20% on average." (5.1 Finding the best-fit model)
   - validation: Compared model line profiles and channel maps to data; alternative models tested  
  > "Some additional test models with different velocity fields, morphologies, and temperature distributions (see Appendix A) were considered to find the best-fit model." (5.1 Finding the best-fit model)
3. **Simulate observations of model**: Simulate visibilities with simobserve using original on-source time and configurations, image like real data, TP via beam convolution, feather  
  > "Using the SIMOBSERVE task in CASA, we simulated the visibilities of the observation using the resulting brightness distribution from the radiative transfer calculation." (4.3 Radiative transfer modeling and imaging)
   - software: CASA, SHAPEMOL
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive mass-loss rate, outflow mass and momentum**: Integrate best-fit density distribution; momentum = mass x velocity integrated; compare to L/c  
  > "when applying an average particle mass of 3$\times$10$^{-24}$ g and integrating the density distribution across the structure." (5.3 Outflow linear momentum)
   - assumption: average particle mass 3e-24 g  
  > "when applying an average particle mass of 3$\times$10$^{-24}$ g" (5.3 Outflow linear momentum)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : calibration, imaging, feathering, simobserve  
  > "We used the Common Astronomy Software Application (CASA) for calibration and imaging (cite: casa)." (2.1 New CO radio line observations with ALMA)
- **SHAPE+SHAPEMOL** : 3D non-LTE radiative transfer modeling  
  > "The radiative transfer calculation was performed via SHAPE+SHAPEMOL (cite: stefetal11; santetal15)" (4.3 Radiative transfer modeling and imaging)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum flux density at 343 GHz | 82.2 | 4.7 | mJy | 1 | The continuum flux densities are 32.7$\pm$6 mJy at 230 GHz and 82.2$\pm$4.7 mJy at 343 GHz. |
| Average mass-loss rate during torus creation | 7.7e-7 | not stated | Msun/yr | 4 | this corresponds to an average mass-loss rate of about 7.7$\times$10$^{-7}$ M$_{\odot}$ yr$^{-1}$. |
| Bipolar outflow mass | 7.3e-4 | not stated | Msun | 4 | $M_{\rm{outflow}}$=7.3$\times$10$^{-4}$ M$_{\odot}$ |
| Outflow linear momentum | 9.6e37 | not stated | g cm/s | 4 | $P_{\rm{outflow}}$=9.6$\times$10$^{37}$ g cm s$^{-1}$ |
| 12CO/13CO abundance ratio | 50 | not stated | dimensionless | 2 | The model gives a value of 50 for the $^{12}$CO/$^{13}$CO abundance ratio |
| Torus inclination | 40 | not stated (changes >10 deg disfavoured) | deg | 2 | / Inclination$^{*}$    / 40$^{\circ}$                    / |
| Temperature scale T0 | 190 | not stated | K | 2 | The temperature in our model is lower ($T_{0}=190$ K instead of 300 K) |
| Kinematic timescales of torus and outflow | 730 and 160 | not stated | yr | 4 | the kinematic timescale of the torus and outflow is about 730 yrs and 160 yrs, respectively. |

## Qualitative findings

- Model reproduces the two-peaked 12CO 2-1 and central-peaked 3-2 distributions without a central cavity  
  > "This means that the model without the central cavity can reproduce the data features." (5.2 Best-fit model)

## Claim tuples

- H: Can a torus plus fast bipolar outflow 3D model reproduce the CO data? | E: SHAPEMOL non-LTE modeling of ALMA, SMA and HIFI data | R: Three-component model matches line profiles and low/intermediate velocity channel maps | F: Torus-bipolar structure confirmed | **supported**
- H: Can radiation pressure alone drive the fast outflow? | E: Compared outflow momentum with L/c | R: Would take about 3300 yr versus kinematic timescale 160 yr | F: Radiation pressure insufficient; momentum excess of ~20 | **supported**

## Reasoning

- Why this data: TP observations added to recover extended emission lacking in the ACA u-v coverage  
  > "Observations with the ALMA-TP array was performed in cycle 2 (in 2015) to recover the most extended emission from the source and produce high fidelity images." (2.1 New CO radio line observations with ALMA)
- Why this method: _not stated_
- Alternative: Constant torus velocity, collimated outflow field, model without central component, and Knapp et al. temperature law were tested and rejected  
  > "A model using a constant expansion velocity for the whole torus could not reproduce the line profile nor the channel maps." (Appendix A)
- How they decided it was enough: _not stated_
- Limitation (authors): Weak bimodal high-velocity emission not reproduced; 12CO 9-8 peak ~20% low; LVG may not apply to torus  
  > "The weak bimodal emission distribution at very high-velocity channels (Fig. [2](#fig:maps12CO32)) was not reproduced by our model." (5.2 Best-fit model)
- Caveat (inferred, ours): Fit by eye with no parameter uncertainties or degeneracy exploration
- Caveat (inferred, ours): Many assumed power-law laws and fixed CO abundance
- Caveat (inferred, ours): SMA flux scaled by factor 2 approximately
- Caveat (inferred, ours): Distance from Hipparcos only

## Reproducibility

- Data public (paper): ALMA project cited in acknowledgements; SMA/HIFI data previously published  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00524.S." (Acknowledgements)
- Products in archive: _not stated_
- Code: SHAPEMOL described as publicly available  
  > "via the publicly available radiative transfer code SHAPEMOL (cite: santetal15)" (Introduction)
- Missing: SHAPE model files
- Missing: Imaging parameters (robust, masks, thresholds)
- Missing: Herschel/HIFI profiles from Danilovich et al. 2015
- Missing: TP data reduction details
- Data volume (inferred): ~10-50 GB (ACA, TP, plus SMA)
- Score (inferred): 3/5, Public ALMA data and public code, but model fit is manual and imaging details are missing.
- Rediscovery candidate: no, Main results come from manual by-eye 3D modeling that is hard to redo mechanically.

## Links

- Method: (cite: santetal15) (SHAPEMOL radiative transfer code)
- Method: (cite: stefetal11) (SHAPE modeling tool)
- Companion: (cite: chiuetal06) (Previous SMA 12CO 2-1 observations and torus model)
- Companion: (cite: dani15) (Herschel/HIFI line profiles)
- Related: Herschel SUCCESS program

## Checks

```json
{
 "quotes": 57,
 "quotes_ok": 57,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 42,
  "rate": 0.583
 },
 "evidence_ok": true
}
```
