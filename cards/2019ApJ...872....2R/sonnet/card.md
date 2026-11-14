# ALMA Detection of Extreme Blueshifted Ionized Gas within 0.2 pc of Sgr A* from -480 to -300 km s<SUP>-1</SUP>

`2019ApJ...872....2R` | The Astrophysical Journal 2019 | first author: Royster, M. J. | arXiv: 1901.03715 | DOI: 10.3847/1538-4357/aafd38

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: milky_way_ism
- Question: Is there extreme high-velocity blue-shifted ionized gas within the inner parsec of Sgr A*, and does it indicate a jet or wind-driven outflow?  
  > "Multiple compact and extended sources are detected in the mini-cavity region with extreme negative radial velocities ranging from –480 km s$^{-1}$ to –300 km s$^{-1}$" (abstract)
- Target **Sgr A* / mini-cavity**: coordinates 17h45m40.038s, -29d00m28.069s (J2000, after shift)  
  > "1 pc corresponds to 25$''$ at the 8.5 kpc GC distance" (1 Introduction); "the position of Sgr A\* could be found at $\alpha,~\delta~(J2000)~=~17^h45^m{40}.\!\!^s{038},~-29\hbox{$^\circ$}00\hbox{$^\prime$}{28}\hbox{$.\!\!^{\prime\prime}$}{069}$" (2 Observations and Data Reduction); z/distance 8.5 kpc  
  > "1 pc corresponds to 25$''$ at the 8.5 kpc GC distance" (1 Introduction); "the position of Sgr A\* could be found at $\alpha,~\delta~(J2000)~=~17^h45^m{40}.\!\!^s{038},~-29\hbox{$^\circ$}00\hbox{$^\prime$}{28}\hbox{$.\!\!^{\prime\prime}$}{069}$" (2 Observations and Data Reduction); distance from assumed GC distance, no citation given  
  > "1 pc corresponds to 25$''$ at the 8.5 kpc GC distance" (1 Introduction); "the position of Sgr A\* could be found at $\alpha,~\delta~(J2000)~=~17^h45^m{40}.\!\!^s{038},~-29\hbox{$^\circ$}00\hbox{$^\prime$}{28}\hbox{$.\!\!^{\prime\prime}$}{069}$" (2 Observations and Data Reduction)

## Data provenance

- ALMA projects: 2015.A.00021.S
- bands: Band 6  
  > "The calibrated Band 6 archival data (project code 2015.A.00021.S)" (2 Observations and Data Reduction)
- frequencies and spectral setup: H30a at 231.901 GHz; 3 km/s channels (full resolution 0.63 km/s); -1200 to +600 km/s imaged  
  > "A broad velocity range of –1200 km s$^{-1}$ to +600 km s$^{-1}$ was imaged" (2 Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.46" x 0.35" (PA = -67.8 deg)  
  > "This achieved a synthesized beam of 0$.\!\!^{\prime\prime}$46 $\times$ 0$.\!\!^{\prime\prime}$35 (PA = –67$.\!\!^\circ$8)" (2 Observations and Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: H30a cube sigma = 0.4 mJy per channel at 3 km/s; continuum ~0.8 mJy/beam (Jul 12/13), ~1.6 (Jul 18/19)  
  > "The July 12/13 H30$\alpha$ image cube has $\sigma=0.4$ mJy per channel, averaged to 3 km s$^{-1}$." (2 Observations and Data Reduction)
- time on source: _not stated_
- observing dates: 2016 July 12/13 and July 18/19 (Cycle 3)  
  > "observed in Cycle 3 on two epochs, 2016 July 12/13 and July 18/19" (2 Observations and Data Reduction)
- pi or archival as stated: Archival data from a Sgr A* multi-wavelength monitoring campaign  
  > "originally as part of a multi-wavelength monitoring campaign of Sgr A\*" (2 Observations and Data Reduction)
- Line: H30alpha recombination line (231.901 GHz)
- External data: Proper motion transverse velocities of K25 (865 km/s), K33 (313 km/s), K32 (656), K41 (215)  
  > "consider the K25 and K33 sources (cite: zhao09), which are 0$.\!\!^{\prime\prime}$52 and 0$.\!\!^{\prime\prime}$41 away from C1" (4.1 Unbound Mini-cavity) [from Zhao et al. 2009 (cite: zhao09)]
- External data: Radio recombination line relation for line intensity vs EM  
  > "The line intensity at 231.9 GHz can be expressed as (cite: wilson12):" (3.1.4 The Gas Density) [from (cite: wilson12)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA v5.1.1  
  > "CASA (v5.1.1; (cite: mcmullin07))" (Software)
- pipeline version: _not stated_
- archive products used as is: Used calibrated archival dataset, then self-calibrated  
  > "We utilized the calibrated dataset to extract the H30$\alpha$ RL in the inner parsec" (2 Observations and Data Reduction)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Phase self-cal three times with shorter solution intervals, then final phase+amplitude per integration  
  > "prior to deriving and applying phase self-calibration solutions three times for subsequently shorter solution intervals." (2 Observations and Data Reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5  
  > "A Briggs parameter of 0.5 was used to weigh the $uv$ visibilities prior to gridding" (2 Observations and Data Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Linear continuum subtracted in uv plane  
  > "first subtracting a linear continuum in the $uv$ plane" (2 Observations and Data Reduction)
- line free channels: _not stated_
- primary beam correction: Applied with 20% cutoff (37.2" FOV)  
  > "A primary beam correction was applied with a cutoff at 20% (37$.\!\!^{\prime\prime}$2 field of view (FOV))." (2 Observations and Data Reduction)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.46" x 0.35", PA -67.8 deg  
  > "This achieved a synthesized beam of 0$.\!\!^{\prime\prime}$46 $\times$ 0$.\!\!^{\prime\prime}$35 (PA = –67$.\!\!^\circ$8)" (2 Observations and Data Reduction)
- final rms: 0.4 mJy/channel at 3 km/s  
  > "The July 12/13 H30$\alpha$ image cube has $\sigma=0.4$ mJy per channel, averaged to 3 km s$^{-1}$." (2 Observations and Data Reduction)

### Not stated but needed to reproduce (our reading)

- Line-free channels for continuum subtraction
- Self-calibration solution intervals and reference antenna
- Cell size, image size, deconvolver, masking and clean threshold
- How the coordinate shift of +61/-123 mas was derived and which reference dataset
- Flux calibrator and flux-scale details
- Gaussian fitting details and the line-fit procedure
- Origin of the 'size' deconvolution choice and uncertainties on measured values

## Analysis recipe

1. **Self-calibrate and image continuum and H30a cube**: Combine spws, phase self-cal three times then amp+phase, apply to cube after uv linear continuum subtraction; Briggs 0.5  
  > "A final simultaneous phase and amplitude self-calibration solution was derived for each integration time interval before imaging the continuum." (2 Observations and Data Reduction)
   - software: CASA
   - parameter: 3 km/s channels, robust 0.5, PB cutoff 20%  
  > "A primary beam correction was applied with a cutoff at 20% (37$.\!\!^{\prime\prime}$2 field of view (FOV))." (2 Observations and Data Reduction)
   - fitting: _not stated_
   - validation: High-velocity features also detected in the second epoch  
  > "the high-velocity features described here are also detected in the July 18/19 dataset." (2 Observations and Data Reduction)
2. **Locate and characterize high-velocity components C1-C4**: Elliptical Gaussian fits to integrated intensity in narrow velocity ranges; multi-Gaussian spectral fits; PV diagrams  
  > "An elliptical Gaussian was fit to the RL integrated intensity from –460 - –450 km s$^{-1}$." (3.1.1 C1 & C4)
   - software: CASA
   - fitting: Gaussian components fit to spectra  
  > "The resultant spectra of the blue-shifted emission was best fit with two Gaussians at –353 and –264 km s$^{-1}$." (Mini-cavity, The Gas Density)
   - validation: _not stated_
3. **Estimate electron density and mass**: EM from line intensity with Te = 7.5e3-12.5e3 K, path length = source size; density lower limit; total mass of region  
  > "dividing by the path length and taking the square root then gives us the $n_e$." (3.1.4 The Gas Density)
   - assumption: Te 7.5-12.5e3 K (1e4 K for total mass); path length equal to source size  
  > "If a nominal value of $10^4$ K for electron the temperature is assumed" (3.1.4 The Gas Density)
   - fitting: _not stated_
   - validation: _not stated_
4. **Assess boundness and outflow rates**: Escape velocity for 4e6 Msun BH combined with literature proper motions; momentum deposition rate for jet (gamma~2.7) or wind (1250 km/s) outflow  
  > "Adopting a Lorentz factor of $\gamma\sim2.7$ for the mildly relativistic jet" (4.3 Mass Outflow Rate)
   - assumption: Central mass 4e6 Msun, distance 8.5 kpc, flat mass profile  
  > "the mass profile of the inner parsec is flat as derived from stellar kinematics (cite: fritz16)" (4.1 Unbound Mini-cavity)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.1.1: Calibration, self-calibration, imaging, extraction of H30a  
  > "CASA (v5.1.1; (cite: mcmullin07))" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| C1 peak velocity | -455 | not stated | km/s | 2 | / C1 / –0.68, –2.06 / 2.17 / –163 / 320 / 2.06 / –455 / 37.0 / 3.39 - 4.97 / |
| C1 electron density lower limit | 3.39-4.97e4 | not stated | cm^-3 | 3 | / C1 / –0.68, –2.06 / 2.17 / –163 / 320 / 2.06 / –455 / 37.0 / 3.39 - 4.97 / |
| Total mass of blue-shifted gas | 0.052 | not stated | Msun | 3 | an average electron density of 1.6$\times 10^4$ cm$^{-3}$ and total mass of 0.052 M$_{\odot}$ |
| Jet mass outflow rate (mini-cavity) | 1.8e-7 | not stated | Msun/yr | 4 | a mass outflow rate of $1.8\times10^{-7}$ M$_{\odot}$ year$^{-1}$ would satisfy a jet origin |
| Wind mass-loss rate | 4e-5 | not stated | Msun/yr | 4 | the required mass-loss rate is $4\times10^{-5}$ M$_{\odot}$  yr$^{-1}$ |
| Escape velocity at 0.09 pc projected | ~620 | not stated | km/s | 4 | the escape velocity at a *projected* distance of 0.09 pc (2$.\!\!^{\prime\prime}$2) is then $\sim$ 620 km s$^{-1}$ |

## Qualitative findings

- Four extreme blue-shifted components C1-C4 are kinematically isolated from orbiting gas in the mini-cavity  
  > "This new component is kinematically isolated from the orbiting ionized gas." (abstract)

## Claim tuples

- H: Highly blue-shifted ionized gas exists near Sgr A* beyond the inner 1" | E: H30a cube from ALMA Band 6 archival data | R: Components C1-C4 at -366 to -455 km/s at 2-3.4" from Sgr A* | F: Highest velocity ionized gas detected beyond the inner 1" | **supported**
- H: The gas is gravitationally unbound | E: Combine radial velocities with literature proper motions | R: Total velocities 988 and 552 km/s vs escape ~620 km/s | F: Components likely unbound if associated with the proper-motion knots | **partially**
- H: A collimated outflow from Sgr A* explains the blue-shifted mini-cavity gas and red-shifted cometary sources | E: Kinematics and momentum estimates | R: Mass outflow rates of 2e-7 (jet) or 4e-5 Msun/yr (wind) | F: Jet or anisotropic wind outflow interpretation, with the jet favored | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: H30a chosen for high line-to-continuum ratio and broad velocity coverage  
  > "The high sensitivity, long time baseline and broad velocity coverage observations as well as the high line-to-continuum ratio of $\sim$2 for H30$\alpha$ RL" (1 Introduction)
- Alternative: Collision of N and E arms rejected as the origin since the U-shaped mini-cavity is hard to explain  
  > "However, the U-shaped morphology of the mini-cavity embedded in the bar is difficult to explain in this picture both spatially and kinematically." (4.2 Origin of High Velocity Gas)
- How they decided it was enough: _not stated_
- Limitation (authors): Second epoch used only for detection check because of poor data quality; densities are lower limits  
  > "Due to the relatively poor data quality of the second epoch, we chose to use the first (July 12/13) dataset only" (2 Observations and Data Reduction)
- Caveat (inferred, ours): Unbound conclusion relies on assuming association with distant proper-motion knots
- Caveat (inferred, ours): Single-epoch single-array data; no uncertainties on fitted values
- Caveat (inferred, ours): Interpretation as jet is speculative; no polarization or other direct evidence
- Caveat (inferred, ours): Possible He30a contamination and continuum subtraction near Sgr A*

## Reproducibility

- Data public (paper): Archival ALMA project 2015.A.00021.S  
  > "The calibrated Band 6 archival data (project code 2015.A.00021.S)" (2 Observations and Data Reduction)
- Products in archive: _not stated_
- Missing: Self-cal parameters
- Missing: Line-free channels
- Missing: Cleaning parameters (cell, size, mask)
- Missing: Astrometric shift derivation
- Missing: Fit uncertainties
- Data volume (inferred): ~50-200 GB
- Score (inferred): 3/5, Public data and key weighting and version given, but many imaging and self-cal details missing and no uncertainties.
- Rediscovery candidate: yes, Public data, main results (velocities, densities) are numeric, and the recipe is mostly stated, though details are missing.

## Links

- Companion: Zhao et al. 2009 (cite: zhao09) (Proper motions of mini-spiral HII knots used for unbound analysis)
- Companion: Steiner et al. 2013 (cite: steiner13) (Previous IR detection of blueshifted gas in mini-cavity)

## Checks

```json
{
 "quotes": 50,
 "quotes_ok": 50,
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
  "facts": 64,
  "stated": 35,
  "rate": 0.547
 },
 "evidence_ok": true
}
```
