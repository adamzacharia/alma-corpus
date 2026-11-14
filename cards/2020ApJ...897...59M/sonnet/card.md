# Orbital and Mass Constraints of the Young Binary System IRAS 16293-2422 A

`2020ApJ...897...59M` | The Astrophysical Journal 2020 | first author: Maureira, María José | arXiv: 2005.11954 | DOI: 10.3847/1538-4357/ab960b

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: Are the radio sources A1 and A2 in IRAS 16293-2422 A protostars forming a bound binary, and what are their masses and orbit?  
  > "confirming the long-known radio sources as protostellar." (abstract); "The kinematic analysis indicates that A1 and A2 are a bound binary system." (abstract)
- Target **IRAS 16293-2422 A (A1, A2)**: coordinates ICRS 16:32:22.63 -24:28:31.8 (pointing center)  
  > "located in the Ophiuchus molecular cloud at a distance of 141 pc (cite: 2018DzibRevised)" (Introduction); "the pointing center of the observations was ICRS 16:32:22.63 -24:28:31.8" (Observations); z/distance 141 pc  
  > "located in the Ophiuchus molecular cloud at a distance of 141 pc (cite: 2018DzibRevised)" (Introduction); "the pointing center of the observations was ICRS 16:32:22.63 -24:28:31.8" (Observations); distance from (cite: 2018DzibRevised)  
  > "located in the Ophiuchus molecular cloud at a distance of 141 pc (cite: 2018DzibRevised)" (Introduction); "the pointing center of the observations was ICRS 16:32:22.63 -24:28:31.8" (Observations)

## Data provenance

- ALMA projects: 2017.1.01247.S
- bands: Band 3 (3 mm), single pointing  
  > "in Band 3 (single pointing) with a total time on-source of 1.25 hours." (Observations)
- frequencies and spectral setup: One continuum window at 99.988 GHz (128 channels, 2 GHz); four line windows (13CO, C17O, C18O, CS) with 22.070 kHz channels  
  > "one continuum window centered at 99.988 GHz with 128 channels and a total bandwidth of 2 GHz" (Observations)
- continuum bandwidth: 2 GHz  
  > "128 channels and a total bandwidth of 2 GHz" (Observations)
- arrays: _not stated_
- configurations: most extended Cycle 5 configuration, 41.4 m - 16.2 km baselines  
  > "using the most extended Cycle 5 configuration of ALMA (41.4 m - 16.2 km baseline range)" (Observations)
- baselines: _not stated_
- angular resolution: 0.048"x0.046" (6.5 au) continuum; 0.106"x0.084" lines  
  > "The beam size, beam P.A. and noise of the final continuum image are 0.048"$\times$0.046" (6.5 au)" (Observations)
- max recoverable scale: ~0.5" (70 au)  
  > "The maximum recoverable scale is $\sim$0.5" (or 70 au)" (Observations)
- sensitivity: 15 uJy/beam continuum; 1.1 mJy/beam per channel lines  
  > "79.3$^{\circ}$ and 15 $\mu$Jy beam$^{-1}$, respectively" (Observations); "55.7$^{\circ}$ and 1.1 mJy/beam per channel" (Observations)
- time on source: 1.25 hours  
  > "with a total time on-source of 1.25 hours" (Observations)
- observing dates: October 8 and 12, 2017  
  > "IRAS 16293 (A and B) was observed on October 8 and 12, 2017" (Observations)
- pi or archival as stated: Project PI G. Dipierro (Cycle 5)  
  > "project ID:2017.1.01247.S. (PI: G. Dipierro)" (Observations)
- Line: CS 2-1 (97.980953 GHz)
- Line: HNCO 5(3,2)-4(3,1) (109.833487 GHz)
- Line: NH2CHO 5(1,4)-4(1,3) (109.753578 GHz)
- Line: t-HCOOH 5-4 (four sub-levels) (112.287-112.467 GHz)
- Line: 13CO 1-0 (110.201354 GHz)
- Other facility **VLA**: Twelve historical positions of A1 and A2 (1987-2013) used for orbit fitting, from literature  
  > "These criteria resulted in twelve VLA observations with the epochs listed in Appendix Table" (Motion of the protostars)
- External data: VLA proper motions of A1 and A2 used for the boundness test  
  > "We use the most-recent published proper motions for A1 and A2 (cite: 2019HernandezGomezNature) that used data spanning almost 30 years" (Are A1 and A2 bound?) [from (cite: 2019HernandezGomezNature)]
- External data: 7 mm VLA fluxes and spectral indices used for free-free correction  
  > "(cite: 2019HernandezGomezNature) reported a spectral index from VLA observations of $0.5\pm0.2$ and $0.7\pm0.2$ for A1 and A2, respectively." (3.1 ALMA 3 mm continuum emission) [from (cite: 2019HernandezGomezNature)]
- External data: Proper motions of B and its line-of-sight velocity for A-B boundness  
  > "most-recent published proper motions for B (cite: 2019HernandezGomezNature) and previous determinations of its line-of-sight velocity (cite: 2012PinedaFirst)" (Bound analysis A-B) [from (cite: 2019HernandezGomezNature); (cite: 2012PinedaFirst)]

## Processing

### Calibration

- pipeline or manual: standard pipeline  
  > "Calibration of the raw visibility data was done using the standard pipeline." (Observations)
- casa version: CASA 5.4.1  
  > "CASA 5.4.1 (cite: 2007McMullinCASA) was used for both calibration and imaging." (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1517-2422 (bandpass/flux); J1625-2527 phase  
  > "The bandpass/flux calibrator and phase calibrator were J1517-2422 and J1625-2527, respectively." (Observations)
- flux scale uncertainty: _not stated_
- self calibration: iterative phase-only (min solint 9 s), then two amplitude iterations (min solint 60 s); applied to line windows  
  > "iteratively performed phase-only self-calibration with a minimum solution interval of 9 seconds." (Observations); "The continuum self-calibration solutions were applied to all four line windows" (Observations)

### Imaging

- task: tclean  
  > "was imaged using the tclean task with the multiscale deconvolver and a robust parameter of 0.5" (Observations)
- deconvolver: multiscale  
  > "was imaged using the tclean task with the multiscale deconvolver and a robust parameter of 0.5" (Observations)
- weighting robust: continuum robust = 0.5; line cubes natural weighting  
  > "We cleaned CS (2-1), the $J=5-4$ rotational transition of HNCO, NH$_2$CHO and t-HCOOH, and $^{13}$CO (1-0) cubes using natural weighting" (Observations)
- uv taper: 0.06" for line cubes  
  > "a uvtaper parameter of 0.06" to better recover moderately extended features" (Observations)
- cell size: 6 mas continuum; 0.018" line cubes  
  > "The adopted values are four scales of 0, 8, 24 and 72 pixels (pixel size of 6 mas)." (Observations)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: continuum 0, 8, 24, 72 pixels; lines 0, 5, 15 pixels  
  > "multiscale deconvolver with scales of 0, 5 and 15 pixels" (Observations)
- continuum subtraction: CASA uvcontsub with line-free channels  
  > "Continuum subtraction was performed with CASA task uvcontsub by selecting line-free channels." (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: continuum 0.048"x0.046", PA 79.3 deg; lines average 0.106"x0.084", PA 55.7 deg  
  > "The average final beam size, beam P.A., and noise for the lines are 0.106"$\times$0.084", 55.7$^{\circ}$" (Observations)
- final rms: 15 uJy/beam continuum; 1.1 mJy/beam per channel lines  
  > "55.7$^{\circ}$ and 1.1 mJy/beam per channel." (Observations)

### Inherited from earlier work

- Upper-edge method for Keplerian velocity profile and 30% mass uncertainty from its Table 6  
  > "we adopt here a larger $30\%$ uncertainty (based on Table 6 of Seifried et al. 2016)" (3.4.1 A1) [from (cite: 2016SeifriedRevealing)]
- Infall+rotation model similar to earlier centrifugal-barrier model  
  > "we also use a simple model of infall and rotation (Appendix Section [8](#ap:infall_rot)), similar to (cite: 2016OyaInfalling)." (3.4.2 A2) [from (cite: 2016OyaInfalling)]
- Applying continuum self-cal solutions to line windows  
  > "to improve the signal-to-noise ratio (cite: 2018BroganAdvanced)" (Observations) [from (cite: 2018BroganAdvanced)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for uvcontsub
- Self-calibration solint per iteration beyond the minimum, reference antenna and imaging masks
- Tclean mask and threshold, number of iterations
- Exact pipeline version
- Absolute flux scale uncertainty
- Exact A1 and A2 deconvolved-size to FWHM conversion
- Which upper-edge threshold/level was used in p-v diagrams
- Orbitize! version and treatment of VLA position errors
- Data for the one extra unidentified bright line

## Analysis recipe

1. **Calibrate and self-calibrate continuum, image**: Standard pipeline calibration, phase then amplitude self-cal, tclean multiscale imaging  
  > "The final continuum dataset after phase+amplitude self-calibration was imaged using the tclean task with the multiscale deconvolver and a robust parameter of 0.5." (Observations)
   - software: CASA, tclean
   - parameter: robust 0.5; scales 0,8,24,72 pixels; pixel 6 mas  
  > "The adopted values are four scales of 0, 8, 24 and 72 pixels (pixel size of 6 mas)." (Observations)
   - fitting: _not stated_
   - validation: Scales chosen for minimal residuals and no artifacts  
  > "we adopted those that resulted in the minimal residuals and no significant artifacts" (Observations)
2. **Fit compact continuum sources**: 2D Gaussian fits with imfit after spline background subtraction (bisplrep)  
  > "We then made a spline fit of the background with the scipy task bisplrep, masking out the compact emission." (Fits to the compact emission towards A1 and A2)
   - software: CASA imfit, scipy
   - parameter: sub-image 0.20"; A1 mask radius 0.07"; A2 ellipse 0.11"x0.07"  
  > "The mask for source A1 consisted of a circular region of radius 0.07"" (Fits to the compact emission towards A1 and A2)
   - assumption: Circular geometry to infer inclination from sizes  
  > "the inferred inclinations assuming circular geometry are 59$^{\circ}$ $\pm$ 4 and 74$^{\circ}$ $\pm$ 1" (3.1 ALMA 3 mm continuum emission)
   - fitting: _not stated_
   - validation: Residuals compared with and without background subtraction; two-component Gaussian+point-source fit for free-free  
  > "Since the residuals for the fit with background subtraction are substantially better" (Fits to the compact emission towards A1 and A2)
3. **Estimate dust masses**: Optically thin M = 100 d^2 S/(B(T) kappa) with free-free correction  
  > "$S_{\nu}$ is taken from Table [\[tb:3mmfit\]](#tb:3mmfit) and corrected by the free-free contamination." (3.1.1 Masses from 3 mm continuum emission)
   - parameter: kappa 0.23-0.81 cm2/g  
  > "we adopt a range of values between 0.23 cm$^2$g$^{-1}$" (3.1.1 Masses from 3 mm continuum emission)
   - assumption: Td = 100 K, gas-to-dust 100  
  > "We assume a dust temperature of 100 K" (3.1.1 Masses from 3 mm continuum emission)
   - fitting: _not stated_
   - validation: Masses taken as conservative lower limits due to scattering/optical depth  
  > "our estimates for the mass of the compact sources should be taken as conservative lower limits" (3.1.1 Masses from 3 mm continuum emission)
4. **Derive line-of-sight systemic velocities**: Linear gradient fit to Gaussian peaks per channel in p-v cuts of HNCO, NH2CHO, t-HCOOH; average over lines  
  > "For the linear gradient fit, in each channel along the p-v cut, we fit a Gaussian to the emission and then fit the peaks of the Gaussians." (3.3 Line of sight velocities)
   - parameter: cut PA 65 deg (A1), 30 deg (A2); width 5 pixels; fit ranges 0.9-4 and 4.7-8 km/s  
  > "The adopted P.A. corresponds to 65$^{\circ}$ and 30$^{\circ}$ for A1 and A2, respectively." (3.3 Line of sight velocities)
   - fitting: _not stated_
   - validation: Repeated with PA +/-10 deg; consistent  
  > "The resultant velocities are in agreement within uncertainties." (3.3 Line of sight velocities)
5. **Keplerian masses from CS upper edge**: Upper-edge extraction of CS p-v diagram, fit v ∝ r^-0.5 with fixed systemic velocity, inclination correction i=64 deg  
  > "we use the ‘upper edge’ method (cite: 2016SeifriedRevealing) to extract the line-of-sight velocity of the gas as a function of the distance from A1." (3.4.1 A1)
   - parameter: Keplerian regime to 20 au (A1), 50 au (A2)  
  > "consistent with Keplerian rotation (i.e., $v \propto r^{-0.5}$) up to a distance of 50 au" (3.4.2 A2)
   - assumption: Inclination 64 deg from circumbinary structure; 30% mass uncertainty  
  > "Similar to A1, we corrected by an inclination of $i=64^{\circ}$ and assumed an uncertainty of $30\%$" (3.4.2 A2)
   - fitting: _not stated_
   - validation: Repeated with PA +/-10 deg; compared to infall+rotation model  
  > "a centrifugal barrier of 20 au and mass of 0.9 $\ensuremath{M_\odot}$ can reasonably reproduce the velocity profile" (3.4.2 A2)
6. **Test boundness**: Minimum total mass from E_kin+E_pot<=0 using proper motions and line-of-sight velocity difference with deprojected separation  
  > "The minimum mass for A1 and A2 to be a bound pair follows from the following condition:" (Are A1 and A2 bound?)
   - parameter: deprojected separation 95.6 au (PA 50, i 64)  
  > "the deprojected distance between A1 and A2 is 0.678" or 95.6 au" (Are A1 and A2 bound?)
   - assumption: Sources lie in the circumbinary disk plane  
  > "Assuming that the point sources lie in the plane of the circumbinary disk-like material" (Are A1 and A2 bound?)
   - fitting: _not stated_
   - validation: Also computed with zero line-of-sight difference  
  > "we obtain a strict minimum mass of 1.7$\pm$0.3 $M_\odot$ for the system to be bound" (Are A1 and A2 bound?)
7. **Fit orbit to relative positions**: orbitize! parallel-tempered MCMC on 12 VLA + 1 ALMA relative positions and RVs; compared to ballistic fit  
  > "We input the twelve VLA positions and the single ALMA positions and radial velocity measurements." (Orbit fitting)
   - software: orbitize!
   - parameter: 20000 steps, 1000 walkers, 20 temperatures, 10000 burn-in; distance fixed 141 pc  
  > "We ran 20,000 steps with 1,000 walkers per temperature with 20 temperatures." (Orbit fitting)
   - assumption: Distance 141 pc  
  > "The distance was fixed to 141 pc." (Orbit fitting)
   - fitting: Priors: a Gaussian(100,50) au; e U(0,0.85); Mtot LogU(2,6) Msun; i U(40,80); omega, Omega U(0,360); tau Gaussian(0.5,0.3)  
  > "uniform between 0 and 0.85 for eccentricity $e$, LogUniform with a minimum of 2 $M_\odot$ and a maximum of 6 $M_\odot$ for the total mass" (Orbit fitting)
   - validation: Uniform priors give similar results; epoch-dropping tests  
  > "changing all priors to uniform within comparable ranges does not affect significantly our results" (Orbit fitting)

## Software

- **CASA** 5.4.1: calibration, self-calibration, tclean imaging, uvcontsub, imfit  
  > "CASA 5.4.1 (cite: 2007McMullinCASA) was used for both calibration and imaging." (Observations)
- **orbitize!** : Keplerian orbit fitting with parallel-tempered MCMC  
  > "We use the open-source software package orbitize! (cite: 2020BluntOrbitize)" (Orbit fitting)
- **scipy (bisplrep)** : spline background fit before Gaussian fitting  
  > "We then made a spline fit of the background with the scipy task bisplrep" (Fits to the compact emission towards A1 and A2)
- **CASSIS** : line frequencies from CDMS and JPL catalogues  
  > "Frequencies and transitions were based on the full CDMS and JPL catalogues available within the CASSIS software" (Molecular line properties)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| A1 integrated flux at 3 mm | 4.91 | 0.04 | mJy | 2 | / A1 / 16:32:22.878 / -24:28:36.684 / (24.6 $\pm$ 0.8 , 12.8 $\pm$ 1.2) / 119.8 $\pm$ 3.6 / 4.18 $\pm$ 0.02 / 4.91 $\pm$ 0.04 / |
| A2 integrated flux at 3 mm | 4.23 | 0.11 | mJy | 2 | / A2 / 16:32:22.851 / -24:28:36.647 / (87.3 $\pm$ 2.5 , 23.7 $\pm$ 2.0) / 137.9 $\pm$ 1.0 / 1.73 $\pm$ 0.03 / 4.23 $\pm$ 0.11 / |
| Projected separation A1-A2 | 0.38" (54 au) | not stated | arcsec / au | 2 | The projected separation of A1 and A2  is 0.38" or 54 au. |
| Free-free contamination at 3 mm A1, A2 | 37% and 53% | 2% and 3% | percent | 3 | This results in free-free contamination of $37\pm2$% and $53\pm3$% for A1 and A2, respectively. |
| Dust mass A1 and A2 (each) | 1-3e-3 | range from opacity | Msun | 3 | correspond to $1-3\times10^{-3}$ $M_\odot$, $1-3\times10^{-3}$ $M_\odot$, and $0.03-0.1$ $M_\odot$, respectively |
| Circumbinary disk inclination | 64 | 1 | deg | 2 | we inferred an inclination of 64$^{\circ}$ $\pm$ 1 for the circumbinary disk-like structure |
| Line-of-sight velocity A1 | 2.1 | 0.1 | km/s | 4 | We obtained line-of-sight systemic velocities of $2.1\pm0.1$ km s$^{-1}$ and $5.8\pm0.1$ km s$^{-1}$ for A1 and A2 |
| Line-of-sight velocity A2 | 5.8 | 0.1 | km/s | 4 | We obtained line-of-sight systemic velocities of $2.1\pm0.1$ km s$^{-1}$ and $5.8\pm0.1$ km s$^{-1}$ for A1 and A2 |
| Keplerian mass A1 | 0.8 | 0.3 | Msun | 5 | which results in an individual mass of $0.8\pm0.3$ $M_\odot$ |
| Keplerian mass A2 | 1.4 | 0.4 | Msun | 5 | We obtain a mass of $1.4\pm0.4$ $M_\odot$. |
| Infall+rotation model mass for A2 | 0.9 (centrifugal barrier 20 au) | not stated | Msun | 5 | a centrifugal barrier of 20 au and mass of 0.9 $\ensuremath{M_\odot}$ can reasonably reproduce the velocity profile |
| Minimum total mass to be bound | 2.2 | 0.3 | Msun | 6 | This results in a minimum mass of 2.2 $\pm$ 0.3 $M_\odot$. |
| Orbital period | 362 | +133/-73 | yr | 7 | The resultant orbits have a period of $P=362^{+133}_{-73}$ years |
| Orbit semimajor axis | 80.26 | +14.60/-8.81 | au | 7 | semimajor axis of $a=80.26^{+14.60}_{-8.81}$ au |
| Orbit eccentricity | 0.19 | +0.09/-0.06 | dimensionless | 7 | ($e=0.19^{+0.09}_{-0.06}$) |
| Orbit total mass | 3.93 | +1.09/-0.80 | Msun | 7 | $M_{tot}=3.93^{+1.09}_{-0.80}$ $M_\odot$ |

## Qualitative findings

- A1 and A2 are protostellar with at least half of 3 mm flux from thermal dust; A2 shows a ~12 au dust disk perpendicular to the circumbinary structure.  
  > "Thus, at least half of the flux in both sources comes from thermal dust emission tracing the location of two protostars." (3.1 ALMA 3 mm continuum emission)
- Dust substructures coincide with enhanced and higher-velocity line emission, possibly shocks or spirals feeding the circumstellar disks.  
  > "Interestingly, the location where the integrated intensity of our molecular tracers is enhanced (particulary HNCO, NH$_2$CHO and t-HCOOH) coincides with the location of the dust substructures" (3.2 Molecular lines)

## Claim tuples

- H: A1 and A2 are protostars, not a shock feature | E: 3 mm continuum at 6.5 au with free-free correction | R: Two compact dust sources coincident with A1, A2; at least half flux thermal dust | F: Protostellar nature of both confirmed | **supported**
- H: The A1-A2 pair is gravitationally bound | E: Compare minimum bound mass from proper motions plus new line-of-sight velocities with kinematic mass | R: Minimum mass 2.2 Msun vs kinematic 2.2±0.5 Msun | F: Pair is bound | **supported**
- H: Protostellar masses are higher than earlier unresolved estimates | E: Keplerian fits of CS upper edge to each source | R: 0.8±0.3 and 1.4±0.4 Msun | F: Individual masses 0.5≲M1≲M2≲2 Msun | **supported**
- H: Relative motion follows a Keplerian orbit rather than ballistic path | E: Fit VLA+ALMA relative positions with ballistic and Keplerian models | R: ALMA epoch departs from ballistic prediction; Keplerian P=362 yr, Mtot ~4 Msun | F: Orbital motion suggested but ballistic not securely excluded | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Upper-edge method needs ~15 au resolution to identify Keplerian profile, satisfied by data  
  > "Thus, our observations are adequate for applying this method to determine if the profiles are consistent with Keplerian rotation." (3.4.1 A1)
- Alternative: Infalling/rotating material instead of Keplerian rotation for A2 gives smaller but comparable mass  
  > "We note that the value of the masses inferred in the two cases agree under the adopted uncertainty of few tens of percent." (3.4.2 A2)
- Alternative: Quadratic fit of earlier work disagrees with ALMA epoch  
  > "our ALMA observation is in disagreement with the prediction of their quadratic fit." (Motion of the protostars)
- How they decided it was enough: _not stated_
- Limitation (authors): A2 line-of-sight velocity relies on tracers brighter around A1  
  > "Our estimation of the line of sight velocity for A2 has the caveat that it uses the emission from tracers that were brighter around A1." (3.3 Line of sight velocities)
- Limitation (authors): Position errors exclude ejecta contamination; orbit angles poorly constrained  
  > "the errors in Figure [7](#fig:positions_abs_rel) are only those from the Gaussian fit to the compact sources" (Motion of the protostars)
- Caveat (inferred, ours): Mass uncertainty of 30% adopted from simulations rather than measured
- Caveat (inferred, ours): Only one ALMA epoch constrains the orbit; 7 vs 4 parameters
- Caveat (inferred, ours): Inclination 64 deg assumed from extended structure for compact sources
- Caveat (inferred, ours): CS may trace infall rather than Keplerian rotation
- Caveat (inferred, ours): Optically thick dust and free-free uncertainties affect continuum masses

## Reproducibility

- Data public (paper): ALMA project data acknowledged; archive project 2017.1.01247.S  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.01247.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Line-free channel selections
- Missing: Imaging masks and clean thresholds
- Missing: Upper-edge extraction details and p-v data points
- Missing: VLA position values and errors (only epochs/beams tabulated)
- Data volume (inferred): ~100-300 GB raw for long-baseline Band 3 dataset
- Score (inferred): 3/5, ALMA data public and key imaging parameters given, but line-free channels, masks and VLA positions are missing, and the kinematic extraction is partly manual.
- Rediscovery candidate: no, Continuum/Gaussian fits are numeric and reproducible, but the kinematic analysis needs unstated choices and external VLA positions.

## Links

- Method: (cite: 2016SeifriedRevealing) (Upper-edge method and mass uncertainties)
- Method: (cite: 2020BluntOrbitize) (orbitize! orbit fitting package)
- Companion: (cite: 2019HernandezGomezNature) (VLA proper motions and positions of A1 and A2)
- Companion: (cite: 2016OyaInfalling) (earlier ALMA kinematics and centrifugal barrier model)
- Related: ALMA-PILS
- Related: VLA monitoring of IRAS 16293-2422

## Checks

```json
{
 "quotes": 106,
 "quotes_ok": 106,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 16,
 "numeric_problems": 0,
 "fill": {
  "facts": 93,
  "stated": 73,
  "rate": 0.785
 },
 "evidence_ok": true
}
```
