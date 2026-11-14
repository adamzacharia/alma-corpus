# Transition from Ordered Pinched to Warped Magnetic Field on a 100 au Scale in the Class 0 Protostar B335

`2020ApJ...893...54Y` | The Astrophysical Journal 2020 | first author: Yen, Hsi-Wei | arXiv: 2003.04502 | DOI: 10.3847/1538-4357/ab7eb3

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: How does the magnetic field structure in the Class 0 protostar B335 behave on a 100 au scale, and is it consistent with MHD simulations with aligned or misaligned magnetic field and rotational axis?  
  > "To observationally investigate the effects of the magnetic field on the disk formation in B335, we conducted ALMA polarimetric observations at an angular resolution of 0.2$''$ (20 au)" (1 Introduction)
- Target **B335**: coordinates RA 19h37m00.89s, Dec +07d34m09.6s (J2000, pointing center)  
  > "The pointing center was $\alpha({\rm J2000}) = 19^{\rm h}37^{\rm d}00.\!\!^{\rm s}89$, $\delta({\rm J2000}) =  +7\ensuremath{^\circ}34\ensuremath{'}09.6\ensuremath{''}$." (Observations); "B335 is an isolated Bok globule with an embedded Class 0 protostar at a distance of 100 pc" (Introduction); z/distance 100 pc  
  > "The pointing center was $\alpha({\rm J2000}) = 19^{\rm h}37^{\rm d}00.\!\!^{\rm s}89$, $\delta({\rm J2000}) =  +7\ensuremath{^\circ}34\ensuremath{'}09.6\ensuremath{''}$." (Observations); "B335 is an isolated Bok globule with an embedded Class 0 protostar at a distance of 100 pc" (Introduction); distance from Keene80; Keene83; Stutz08; Olofsson09  
  > "The pointing center was $\alpha({\rm J2000}) = 19^{\rm h}37^{\rm d}00.\!\!^{\rm s}89$, $\delta({\rm J2000}) =  +7\ensuremath{^\circ}34\ensuremath{'}09.6\ensuremath{''}$." (Observations); "B335 is an isolated Bok globule with an embedded Class 0 protostar at a distance of 100 pc" (Introduction)

## Data provenance

- ALMA projects: 2015.1.01018.S
- bands: 0.87 mm (Band 7), full polarization  
  > "The observations were conducted with the full polarization mode and at the frequency ranges of 335.5–339.5 GHz and 347.5–351.5 GHz with a total bandwidth of 8 GHz." (Observations)
- frequencies and spectral setup: 335.5–339.5 GHz and 347.5–351.5 GHz  
  > "at the frequency ranges of 335.5–339.5 GHz and 347.5–351.5 GHz with a total bandwidth of 8 GHz" (Observations)
- continuum bandwidth: 8 GHz total  
  > "with a total bandwidth of 8 GHz" (Observations)
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15 m to 1400 m; 40 to 47 antennae  
  > "40 to 47 antennae were used in the configurations with baseline lengths ranging from 15 m to 1400 m." (Observations)
- angular resolution: 0.19'' x 0.17''  
  > "The achieved synthesized beam is $0.19\ensuremath{''} \times 0.17\ensuremath{''}$." (Observations)
- max recoverable scale: _not stated_
- sensitivity: 40 uJy/beam (Stokes I); 9 uJy/beam (Q and U)  
  > "The noise level in the Stokes *I* image is 40 $\mu$Jy beam$^{-1}$, and it is 9 $\mu$Jy beam$^{-1}$ in the Stokes *Q* and *U* images." (Observations)
- time on source: 7.4 hours  
  > "The on-source integration time was 7.4 hours." (Observations)
- observing dates: 2016 to 2018, 13 executions  
  > "were conducted during 2016 to 2018, consisting of 13 successful executions" (Observations)
- pi or archival as stated: _not stated_
- Other facility **ALMA archive 1.3 mm polarization data**: 1.3 mm polarization maps for comparison of orientations and percentages  
  > "For comparison, we retrieved the polarization maps at 1.3 mm obtained with ALMA (cite: Maury18; Yen19)." (Results)
- Other facility **JCMT**: Large-scale (6000 au) magnetic field orientations compared with simulations  
  > "We have also compared the magnetic field structures on the large scale in this simulation with those observed with JCMT (cite: Yen19)." (Comparison between the aligned and misaligned cases)
- External data: 1.3 mm ALMA polarization maps of B335  
  > "For comparison, we retrieved the polarization maps at 1.3 mm obtained with ALMA (cite: Maury18; Yen19)." (Results) [from (cite: Maury18; Yen19)]
- External data: Dust temperature of 67 K at 25 au from modeling  
  > "the dust temperature of 67 K at a radius of 25 au estimated by modeling molecular-line and continuum data and the spectral energy distribution of B335 (cite: Shirley11; Evans15)" (Results) [from (cite: Shirley11; Evans15)]
- Simulation/model as data: Non-ideal MHD (ambipolar diffusion) collapse simulations of a dense core: aligned case (mass-to-flux 9.6, cosmic-ray rate 5e-17) from Yen19, and new misaligned (15 deg) case with cosmic-ray rate 1e-16 s^-1; synthetic IQU via SPARX and CASA simulator  
  > "The synthetic *IQU* maps of the simulation results were obtained from (cite: Yen19)." (Simulation with the aligned magnetic field and rotational axis); "we additionally performed non-ideal MHD simulations of a collapsing dense core with its magnetic field misaligned with its rotational axis by 15$^\circ$." (Simulation with the misaligned magnetic field and rotational axis)

## Processing

### Calibration

- pipeline or manual: Manual calibration by EA ARC node  
  > "The data were manually calibrated by the EA ARC node using the Common Astronomy Software Applications (CASA) of the version 5.1.1" (Observations)
- casa version: CASA 5.1.1  
  > "using the Common Astronomy Software Applications (CASA) of the version 5.1.1" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: quasars or the asteroid Pallas  
  > "The flux calibration was performed with the observations of quasars or the asteroid, Pallas." (Observations)
- flux scale uncertainty: _not stated_
- self calibration: Phase self-calibration using Stokes I  
  > "We additionally performed self-calibration of the phase using the Stokes *I* data." (Observations)

### Imaging

- task: tclean  
  > "the images were cleaned using the CASA task *tclean*" (Observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = +0.5  
  > "with the Briggs weighting with a robust parameter of +0.5 to generate Stokes *IQU* images" (Observations)
- uv taper: _not stated_
- cell size: original 0.02''; binned to 0.1'' for polarization detections  
  > "The Stokes *I* and $I_{\rm p}$ maps with their original pixel size of 0.02$''$ are presented below." (Observations)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: 0.87 mm maps convolved to the 1.3 mm beam for comparison  
  > "We convolved our polarization maps at 0.87 mm to have the same beam size as those at 1.3 mm" (Results)
- final beam: 0.19'' x 0.17''  
  > "The achieved synthesized beam is $0.19\ensuremath{''} \times 0.17\ensuremath{''}$." (Observations)
- final rms: 40 uJy/beam (I), 9 uJy/beam (Q, U)  
  > "The noise level in the Stokes *I* image is 40 $\mu$Jy beam$^{-1}$" (Observations)

### Inherited from earlier work

- Polarization detection extraction procedure and criteria for the 1.3 mm comparison  
  > "extracted polarization detections with the same procedure and criteria as those in (cite: Yen19)" (Results) [from (cite: Yen19)]
- Aligned-case simulation setup and synthetic IQU maps  
  > "The details of the simulation are described in (cite: Yen19)." (Simulation with the aligned magnetic field and rotational axis) [from (cite: Yen19)]

### Not stated but needed to reproduce (our reading)

- Clean thresholds, masks, niter, image size for tclean
- Self-calibration solution intervals and number of iterations
- Which executions used which calibrators and flux scale uncertainty
- Details of the 1.3 mm archival data (project codes, beam)
- Simulation code name, resolution and numerical setup of the MHD runs
- SPARX and CASA simulator parameters for synthetic observations
- Exact method of computing the angle-difference histogram

## Analysis recipe

1. **Image Stokes IQU and build polarization maps**: Briggs-weighted tclean imaging of calibrated, phase-self-calibrated data; debiased polarized intensity  
  > "we debiased the polarized intensity ($I_{\rm p}$) with $I_{\rm p} = \sqrt{Q^2 + U^2 - {\sigma_{Q,U}}^2}$" (Observations)
   - software: CASA
   - parameter: robust = +0.5  
  > "with a robust parameter of +0.5" (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract polarization detections**: Bin to 0.1'' pixels; keep detections with Stokes I and Ip S/N > 3  
  > "The polarization detections are extracted when the signal-to-noise ratios (S/N) of both Stokes *I* and $I_{\rm p}$ are larger than three" (Observations)
   - software: CASA
   - parameter: pixel 0.1'', S/N>3, orientation uncertainty <~9 deg  
  > "the expected uncertainties in the polarization orientations are $\lesssim$9$^\circ$" (Observations)
   - fitting: _not stated_
   - validation: _not stated_
3. **Compare 0.87 and 1.3 mm polarization**: Convolve to 1.3 mm beam, extract with same criteria, compare orientations and percentages at same positions  
  > "Then we compared the polarization orientations and percentages at 0.87 mm and 1.3 mm at the same positions." (Results)
   - software: CASA
   - assumption: Polarization orientations rotated by 90 deg to infer B-field if emission from aligned grains and optically thin  
  > "the magnetic field structures in B335 can be inferred by rotating the observed polarization orientations by 90$^\circ$" (Origins of the polarized continuum emission)
   - fitting: _not stated_
   - validation: Optical depth check via peak brightness temperature 30 K vs dust temperature 67 K  
  > "The peak brightness temperature is measured to be 30 K" (Results)
4. **Simulate aligned and misaligned collapsing cores and compare with observations**: Non-ideal MHD simulations, SPARX radiative transfer with constant polarization efficiency, CASA simulator; compare B-field orientations in central 100 au  
  > "on the assumption of a constant polarization efficiency meaning that the polarized intensity is simply proportional to the column density" (Simulation with the aligned magnetic field and rotational axis)
   - software: SPARX, CASA
   - parameter: misalignment 15 deg; cosmic-ray ionization 1e-16 s^-1 (misaligned) vs 5e-17 (aligned); stop at 0.1 Msun  
  > "the cosmic-ray ionization rate was increased to be $1\times10^{-16}$ s$^{-1}$" (Simulation with the misaligned magnetic field and rotational axis)
   - assumption: Barotropic approximation  
  > "Our simulations were performed with the barotropic approximation" (Comparison between the aligned and misaligned cases)
   - fitting: _not stated_
   - validation: Histogram of angle differences; fraction of model segments within 30 deg of observations  
  > "The number of the model segments with their orientations consistent with the observations within 30$\ensuremath{^\circ}$ increases by 50%" (Comparison between the aligned and misaligned cases)

## Software

- **CASA** 5.1.1: Calibration, tclean imaging, and simulated observations  
  > "using the Common Astronomy Software Applications (CASA) of the version 5.1.1" (Observations)
- **SPARX** : Radiative transfer to generate synthetic Stokes IQU maps  
  > "The synthetic *IQU* maps were generated using the radiative transfer code, Simulation Package for Astronomical Radiative Xfer (SPARX" (Simulation with the aligned magnetic field and rotational axis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Beam | 0.19 x 0.17 | not stated | arcsec | 1 | The achieved synthesized beam is $0.19\ensuremath{''} \times 0.17\ensuremath{''}$. |
| Peak brightness temperature | 30 | not stated | K | 3 | The peak brightness temperature is measured to be 30 K |
| Mean difference in B-field orientation between 0.87 and 1.3 mm | 5 | std 4 | deg | 3 | The mean difference in the orientations at the two wavelengths is 5$\ensuremath{^\circ}$ with a standard deviation of 4$\ensuremath{^\circ}$. |
| Polarization percentage ratio 1.3 mm / 0.87 mm | 1.7 | not stated | dimensionless | 3 | On average, the polarization percentages at 1.3 mm are a factor of 1.7 higher. |
| Increase in model segments within 30 deg of observations with misalignment | 50 | not stated | percent | 4 | The number of the model segments with their orientations consistent with the observations within 30$\ensuremath{^\circ}$ increases by 50% |

## Qualitative findings

- B-field changes from ordered pinched on 1000 au to complicated, asymmetric structures within 100 au, connecting to the center along the equatorial plane and 40-60 deg off it  
  > "the magnetic field connects to the center along the equatorial plane as well as along the directions which are $\sim$40$\ensuremath{^\circ}$–60$\ensuremath{^\circ}$ from the equatorial plane" (abstract)

## Claim tuples

- H: Polarized emission at 0.87 mm traces magnetically aligned grains rather than scattering | E: Compare 0.87 mm and 1.3 mm polarization and check optical depth | R: Orientations consistent (5 deg mean diff); percentages 1.7x higher at 1.3 mm; Tb 30 K | F: Emission from aligned grains; B-field inferred by 90 deg rotation | **supported**
- H: Aligned B-field and rotation axis can explain the 100 au field structure | E: Synthetic observations of an aligned non-ideal MHD simulation | R: Explains N-S field along midplane but not NW-SE field near peak | F: Aligned case insufficient | **supported**
- H: Slight misalignment explains the warped field | E: Simulation with 15 deg misalignment and comparison | R: 50% more model segments within 30 deg of observations | F: Envelope likely warped; field dragged by warped accretion flows | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Higher-resolution polarimetry probes the field closer to the disk-forming region  
  > "to probe the magnetic field structures on a scale close to the disk forming region" (1 Introduction)
- Alternative: Dust scattering as the polarization origin rejected based on wavelength dependence and high fractions  
  > "In addition, the observed polarization fraction is higher than typically predicted by scattering models." (Origins of the polarized continuum emission)
- How they decided it was enough: _not stated_
- Limitation (authors): Simulations are axisymmetric, barotropic, with constant polarization efficiency; they do not reproduce N-S asymmetry or the intensity morphology; the misaligned run used a different cosmic-ray rate  
  > "This change in the intensity distribution is not fully consistent with the observations." (Comparison between the aligned and misaligned cases)
- Caveat (inferred, ours): Only one misalignment angle and two cosmic-ray rates were tested; no parameter exploration
- Caveat (inferred, ours): Comparison metric (30 deg agreement) is coarse and lacks significance estimates
- Caveat (inferred, ours): Misaligned case changed the ionization rate, confounding the comparison
- Caveat (inferred, ours): Turbulence contribution is suggested but not simulated

## Reproducibility

- Data public (paper): ALMA project code given; archive data used  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.01018.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: MHD simulation code and inputs
- Missing: tclean clean parameters and self-cal details
- Missing: 1.3 mm archival project details
- Missing: SPARX/CASA simulator settings
- Data volume (inferred): ~100-300 GB raw for 13 executions of Band 7 polarization data
- Score (inferred): 3/5, Observational imaging steps are fairly clear, but the simulations and several imaging/self-cal parameters are not reproducible from the text.
- Rediscovery candidate: no, The key comparison depends on custom MHD simulations and unstated settings; the observational polarization results alone are partly numeric.

## Links

- Method: (cite: McMullin07) (CASA)
- Companion: (cite: Yen19) (1.3 mm ALMA and JCMT polarization data and aligned-case simulation)
- Companion: (cite: Maury18) (1.3 mm ALMA polarization of B335)

## Checks

```json
{
 "quotes": 61,
 "quotes_ok": 61,
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
  "stated": 47,
  "rate": 0.653
 },
 "evidence_ok": true
}
```
