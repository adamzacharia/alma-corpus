# A circumbinary protoplanetary disk in a polar configuration

`2019NatAs...3..230K` | Nature Astronomy 2019 | first author: Kennedy, Grant M. | arXiv: - | DOI: 10.1038/s41550-018-0667-x

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: What are the orientation, size and structure of the circumbinary disc around HD 98800BaBb, and is it misaligned/polar and planet-forming?  
  > "To ascertain the disc orientation, size, structure, and evolutionary status we observed the HD 98800 system with the Atacama Large Millimeter/sub-millimeter Array" (main text)
- Target **HD 98800 (BaBb circumbinary disc)**: coordinates BaBb centred at 11 22 05.17437, -24 46 39.5043 (J2000, epoch 2017.874)  
  > "The HD 98800 system is a well known hierarchical quadruple star system 44.9 parsecs from Earth [14]" (main text); z/distance 44.9 pc  
  > "The HD 98800 system is a well known hierarchical quadruple star system 44.9 parsecs from Earth [14]" (main text); distance from Hipparcos (van Leeuwen 2007)  
  > "The HD 98800 system is a well known hierarchical quadruple star system 44.9 parsecs from Earth [14]" (main text)

## Data provenance

- ALMA projects: 2017.1.00350.S
- bands: Band 6 (1.3 mm)  
  > "HD 98800 was observed by ALMA in Band 6 (1.3 mm) in two observing blocks on 2017 November 15 and 19" (Methods)
- frequencies and spectral setup: three 2 GHz continuum windows plus one on CO J=2-1 with 488 kHz (0.73 km/s) resolution  
  > "The correlator configuration used three broad continuum windows with 2GHz bandwidth, and one centred on the CO J=2-1 line with a spectral resolution of 488kHz (0.73km s−1 velocity resolution)." (Methods)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 92 m to 11.8 km  
  > "The shortest and longest baselines were 92 m and 11.8 km." (Methods)
- angular resolution: 46x42 mas (Briggs), 64x56 mas (natural), 32x25 mas (uniform)  
  > "46 × 42mas, the rms is 14 µJy beam−1, and the peak s/n is 280. In a naturally weighted image the beam size is 64 × 56mas" (Methods, Observations and Data Processing)
- max recoverable scale: _not stated_
- sensitivity: rms 14 µJy/beam (Briggs); CO 0.8 mJy/beam per 0.73 km/s channel  
  > "an rms of 0.8 mJy beam−1 in each 0.73 km s−1 channel" (Methods)
- time on source: 34 minutes per block  
  > "The time on-source was 34 minutes for each block." (Methods)
- observing dates: 2017 November 15 and 19  
  > "HD 98800 was observed by ALMA in Band 6 (1.3 mm) in two observing blocks on 2017 November 15 and 19" (Methods)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (not stated)
- Other facility **VLA**: Image of HD 98800B from Ribas et al. re-modelled for comparison  
  > "We modelled the VLA image using the model described above" (Methods)
- Other facility **Washington Double Star catalogue**: Historical AB separations and position angles for orbit fit  
  > "we obtained previous observations of the AB separation and position angle from the Washington Double Star catalogue (WDS)" (Methods)
- External data: BaBb orbit and combined mass 1.28 Msun  
  > "We assume the CO orbits a single point mass with the combined mass of HD 98800BaBb of 1.28 M⊙ [17]." (Methods) [from Boden et al. 2005 (cite: 17)]
- External data: Radial velocities of AaAb and BaBb in early 1990s  
  > "Ref [42] find that the systemic velocity of AaAb (12.75 km s−1) was more positive than BaBb (5.73 km s−1) in the early 1990s" (Methods) [from Torres et al. 1995 (cite: 42)]
- External data: Dust temperature of 160 K from multiwavelength photometry  
  > "assuming a dust temperature of 160K derived from photometry over a range of wavelengths" (Methods) [from not stated]

## Processing

### Calibration

- pipeline or manual: observatory pipeline  
  > "The raw data were calibrated using the observatory pipeline with CASA v5.1." (Methods)
- casa version: CASA v5.1  
  > "The raw data were calibrated using the observatory pipeline with CASA v5.1." (Methods)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1127-1857 (also bandpass)  
  > "J1127-1857 was used as the bandpass and flux calibrator." (Methods)
- flux scale uncertainty: 10%  
  > "Including an absolute calibration uncertainty of 10% yields a final flux measurement of 47 ±5 mJy." (Methods)
- self calibration: one cycle of phase self-cal, spws combined, solint 20-40 min  
  > "The data were further processed using one cycle of phase self-calibration (self-cal) to improve the signal to noise ratio (s/n)." (Methods); "the averaging time (‘solint’) was chosen to be relatively long (20-40min)" (Methods)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs robust=0.5 (plus natural and uniform images)  
  > "The rms variation measured in clean images before self-cal with Briggs weighting (robust=0.5) was 27 and 32 µJy beam−1" (Methods)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: CASA uvcontsub for CO  
  > "The continuum was subtracted using the CASA uvcontsub task, the two observations merged using the mstransform task" (Methods)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 46x42 mas Briggs  
  > "46 × 42mas, the rms is 14 µJy beam−1, and the peak s/n is 280." (Methods, Observations and Data Processing)
- final rms: 14 µJy/beam  
  > "the rms is 14 µJy beam−1, and the peak s/n is 280." (Methods, Observations and Data Processing)

### Inherited from earlier work

- SPH simulation parameters  
  > "the simulations used the same SPH parameters as ref [6] and 300,000 particles." (Methods) [from Martin & Lubow 2017 (cite: 6)]
- Visibility re-weighting approach  
  > "based on the expectation that each individual visibility measurement has negligible s/n [35]." (Methods) [from Guilloteau et al. 2011 (cite: 35)]

### Not stated but needed to reproduce (our reading)

- Image size, cell size, clean threshold, masks and niter
- Line-free channels for uvcontsub
- Prior ranges for MCMC parameters
- Reference antenna and phase-up details for self-cal
- Exact CO channel selection for the 40 channels
- Source of 160 K dust temperature
- Code in GitHub not specified by repository

## Analysis recipe

1. **Calibrate and self-calibrate**: Pipeline calibration, one phase self-cal, concatenate two EBs  
  > "Following calibration the two observations were concatenated into a single set of visibilities for imaging and modelling." (Methods)
   - software: CASA
   - parameter: solint 20-40 min  
  > "the averaging time (‘solint’) was chosen to be relatively long (20-40min)" (Methods)
   - fitting: _not stated_
   - validation: Separate continuum fits of each EB agreed in offsets within 0.0002 arcsec and flux within 1%  
  > "the sky offsets of the disc were consistent to within 0.0002 arcsec (0.01au). The difference in integrated flux densities was consistent to within 1%." (Methods)
2. **Model continuum and CO in visibility plane**: Power-law ring line-of-sight integration model fit to visibilities; eccentric inner edge for continuum  
  > "where the dust or gas lies between two limiting radii rin and rout and where the volume density is a power law function of radius rα." (Methods)
   - software: emcee, GALARIO
   - parameter: 64 walkers, 1000 steps after 1000-step burn-in  
  > "The best fitting continuum model was found using 64 ‘walkers’ (parallel MCMC chains) run for 1000 steps" (Methods)
   - parameter: scale height fixed to 0.05 r  
  > "The vertical density structure is Gaussian with the scale height fixed to 0.05r for all models" (Methods)
   - assumption: Distance 44.9 pc; CO orbits 1.28 Msun point mass  
  > "We assume the CO orbits a single point mass with the combined mass of HD 98800BaBb of 1.28 M⊙ [17]." (Methods)
   - fitting: emcee with log likelihood -chi2/2 via GALARIO  
  > "The log likelihood −χ2/2 of each model is computed given the visibility data using GALARIO [38]." (Methods)
   - validation: Residual images show residuals at most 1% of peak  
  > "the residuals are at most only 1% of the peak" (Methods)
3. **Estimate dust and CO masses**: Optically thin dust mass from flux; CO mass assuming tau=1, Tex=70 K; H2/CO=1e4  
  > "We can estimate a minimum CO mass by assuming that the CO emission is marginally optically thick (τ = 1) with an excitation temperature of 70K" (Methods)
   - assumption: dust opacity 1.7 cm2/g, Td=160 K  
  > "Using equation 5 of ref [39] (which assumes an opacity of 1.7 cm2 g−1)" (Methods)
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit AB orbit**: MCMC orbit fit to WDS astrometry plus radial velocity constraints  
  > "we use the python emcee package to find the best-fitting orbits" (Methods)
   - software: emcee
   - assumption: Mass of A 1.3±0.15 Msun prior; B 1.28 Msun  
  > "The mass of A is estimated as 1.3 ± 0.15 M⊙ [21,47]" (Methods)
   - fitting: chi2 likelihood  
  > "The log likelihood −χ2/2 of each model is computed given the visibility data using GALARIO" (Methods, Visibility Modelling)
   - validation: _not stated_
5. **N-body and SPH dynamics of the two disc orientations**: Gas-free n-body with REBOUND whfast for 1 Myr; SPH with Phantom  
  > "We used the ‘whfast’ integrator [50] with a time step of 1/20th of the BaBb orbital period." (Methods)
   - software: REBOUND, Phantom, splash
   - parameter: 300,000 SPH particles  
  > "the simulations used the same SPH parameters as ref [6] and 300,000 particles." (Methods)
   - fitting: _not stated_
   - validation: _not stated_
6. **Population estimate of polar discs**: Monte Carlo of 1e6 random orientations at 16 eccentricities, classify via constant of motion c vs e^2  
  > "we populate the i cos Ω, i sin Ω plane with N = 106 orbits." (Methods)
   - assumption: Uniform eccentricity 0-0.8, isotropic initial orientation, test-particle dynamics  
  > "iii) the binary eccentricity distribution is uniform between 0 and 0.8 [34]." (Methods)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** v5.1: Pipeline calibration, uvcontsub, mstransform, statwt  
  > "The raw data were calibrated using the observatory pipeline with CASA v5.1." (Methods)
- **emcee** : MCMC fits of disc and orbit  
  > "using the Markov-Chain Monte-Carlo (MCMC) package emcee [37]" (Methods)
- **GALARIO** : Likelihood from visibilities  
  > "The log likelihood −χ2/2 of each model is computed given the visibility data using GALARIO [38]." (Methods)
- **REBOUND** : Gas-free n-body simulations  
  > "We simulated the system as gas-free using the REBOUND code [49]" (Methods)
- **Phantom** : SPH simulations  
  > "We used Phantom [51] to simulate the response of the two possible disc configurations" (Methods)
- **splash** : Visualising SPH output  
  > "the images were created using splash [52]" (Methods)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Dust inner edge | 2.5 | ±0.02 | au | 2 | the inner edges of the dust and CO are at 2.5 ± 0.02 and 1.6 ± 0.3 au respectively |
| Dust outer edge | 4.6 | ±0.01 | au | 2 | while the outer edges are at 4.6 ± 0.01 and 6.4 ± 0.5 au |
| CO inner/outer edges | 1.6 and 6.4 | ±0.3 and ±0.5 | au | 2 | the inner edges of the dust and CO are at 2.5 ± 0.02 and 1.6 ± 0.3 au respectively |
| Disc position angle | 16 | ±1 | deg | 2 | the disc has a position angle of 16 ± 1 ◦ (measured anti-clockwise from North) |
| Disc inclination | 26 or 154 | ±1 | deg | 2 | by either 26 or 154 ◦ (±1◦) from the sky plane |
| Total disc flux | 47 | ±5 | mJy | 2 | Including an absolute calibration uncertainty of 10% yields a final flux measurement of 47 ±5 mJy. |
| Dust mass | 0.33 | not stated | Earth masses | 3 | the result is 0.33 M⊕. |
| CO mass (minimum) | 2.8e-5 | not stated | Earth masses | 3 | The best-fit total CO flux of 0.31 Jy km s−1 is then equivalent to a mass of 2.8 × 10−5 M⊕. |
| Total gas mass | 0.28 | not stated | Earth masses | 3 | then the total gas mass is roughly 0.28 M⊕, similar to the dust mass. |
| AB orbit eccentricity | 0.52 | ±0.01 | dimensionless | 4 | which has an eccentricity of 0.52 ± 0.01 and a period of 246 ± 5 years |
| AB orbit period | 246 | ±5 | years | 4 | which has an eccentricity of 0.52 ± 0.01 and a period of 246 ± 5 years |
| Fraction of discs evolving to polar | 46% (about 45% in main text) | not stated | percent | 6 | is the average value across this range of eccentricities, and found to be 46%. |

## Qualitative findings

- Disc is polar (154 deg case within 4 deg of polar); moderately misaligned case reorients within ~100s of years in SPH  
  > "torques from the inner binary re-orient a gas disc in the moderately misaligned configuration to the polar configuration in several hundred years" (main text)
- Gas is more extended than dust, suggesting grain growth  
  > "our models find that the gas is more extended than the bulk of the dust" (main text)

## Claim tuples

- H: Is the HD 98800BaBb disc strongly misaligned and in a polar configuration? | E: Visibility modelling of continuum and CO, plus n-body and SPH simulations of the two allowed orientations | R: Inclination 26 or 154 deg; 154 deg is 4 deg from polar; the 26 deg case reorients in hundreds of years | F: Disc is in the polar configuration | **supported**
- H: Does the disc show planet-forming disc properties? | E: Compare dust and CO radial extents and masses | R: CO extends 1.6-6.4 au vs dust 2.5-4.6 au | F: Probable evidence of grain growth, like single-star discs | **partially**
- H: Polar discs may be common | E: Monte Carlo population estimate | R: About 45% of discs evolve to polar | F: Circumbinary planets may be more common than thought | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Optically thin line-of-sight model is adequate because the disc is nearly face-on and only surface brightness vs radius is modelled  
  > "the use of a radiative transfer code would make little difference here because the disc is close to face-on" (Methods)
- Alternative: Optical depth parameter tau_SB was consistent with zero, so not needed  
  > "we found that these models were consistent with τSB = 0" (Methods)
- How they decided it was enough: _not stated_
- Limitation (authors): Gas and dust mass estimates have large systematic uncertainties; dust optical depth uncertain  
  > "but do not confirm it because they have large systematic uncertainties" (main text)
- Limitation (authors): Inclination ambiguity (26 vs 154 deg) not resolved by observations  
  > "these observations do not distinguish whether the East or West side of the disc is closer to Earth." (main text)
- Caveat (inferred, ours): Polar vs moderately misaligned choice rests on simulations, not direct data
- Caveat (inferred, ours): Gas mass depends on assumed Tex=70 K and CO/H2
- Caveat (inferred, ours): Eccentric inner edge parameterisation may be non-physical
- Caveat (inferred, ours): Population estimate assumes isotropic initial orientation

## Reproducibility

- Data public (paper): ALMA data in the ALMA Science Archive  
  > "The ALMA data used in this study are available in the ALMA Science Archive" (Data and code availability)
- Products in archive: _not stated_
- Code: Scripts on github (drgmk)  
  > "The post-processing, modelling, and other scripts used in this study are available on github at https://github.com/drgmk." (Data and code availability)
- Missing: Clean parameters (image size, cell, masks, thresholds)
- Missing: Line-free channels for continuum subtraction
- Missing: MCMC priors
- Missing: Origin of 160 K dust temperature
- Data volume (inferred): ~20-50 GB for two EBs
- Score (inferred): 4/5, Public data, clear modelling approach and released scripts, but imaging and prior details are missing.
- Rediscovery candidate: yes, Public data, complete-enough modelling recipe, numeric disc parameters.

## Links

- Method: Tazzari et al. 2018 (GALARIO) (cite: 38) (visibility likelihood)
- Method: Foreman-Mackey et al. 2013 (emcee) (cite: 37) (MCMC sampler)
- Companion: Ribas et al. 2018 (cite: 23) (VLA view of HD 98800 disc for comparison)
- Companion: Martin & Lubow 2017 (cite: 6) (polar alignment theory and SPH parameters)

## Checks

```json
{
 "quotes": 78,
 "quotes_ok": 78,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 88,
  "stated": 59,
  "rate": 0.67
 },
 "evidence_ok": true
}
```
