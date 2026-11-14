# Gas Density Perturbations Induced by One or More Forming Planets in the AS 209 Protoplanetary Disk as Seen with ALMA

`2019ApJ...871..107F` | The Astrophysical Journal 2019 | first author: Favre, Cécile | arXiv: 1812.04062 | DOI: 10.3847/1538-4357/aaf80c

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Is the gas surface density perturbed in the AS 209 disk gaps, as traced by optically thin C18O and DCO+, consistent with forming planet(s)?  
  > "In this paper, we investigate gas perturbations caused by a forming-planet in the disk surrounding the T Tauri star AS 209" (Introduction)
- Target **AS 209**: coordinates RA 16h49m15.296s, Dec -14d22m09.02s (J2000, phase center)  
  > "which is located at 126 pc from the Sun (cite: Gaia-Collaboration:2016)" (Introduction); "towards the following phase-tracking center ($\rm\alpha_{J2000}$=16$\rm^{h}49^{m}15.296s$, $\rm\delta_{J2000}$= $-$14$\ensuremath{^\circ}22\ensuremath{'}09\ensuremath{''}$02)" (Observations and data reduction); z/distance 126 pc  
  > "which is located at 126 pc from the Sun (cite: Gaia-Collaboration:2016)" (Introduction); "towards the following phase-tracking center ($\rm\alpha_{J2000}$=16$\rm^{h}49^{m}15.296s$, $\rm\delta_{J2000}$= $-$14$\ensuremath{^\circ}22\ensuremath{'}09\ensuremath{''}$02)" (Observations and data reduction); distance from Gaia Collaboration 2016  
  > "which is located at 126 pc from the Sun (cite: Gaia-Collaboration:2016)" (Introduction); "towards the following phase-tracking center ($\rm\alpha_{J2000}$=16$\rm^{h}49^{m}15.296s$, $\rm\delta_{J2000}$= $-$14$\ensuremath{^\circ}22\ensuremath{'}09\ensuremath{''}$02)" (Observations and data reduction)

## Data provenance

- ALMA projects: 2015.1.00486.S, 2013.1.00226.S
- bands: Band 6 (1.3 mm)  
  > "The observations cover the frequency range 211–275 GHz in band 6." (Observations and data reduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: about 0.3'' x 0.2'' (~38 x 25 au)  
  > "at a spatial resolution of about 0.3$\ensuremath{''}$ $\times$ 0.2$\ensuremath{''}$ (corresponding to $\sim$ 38 $\times$ 25 au)" (abstract)
- max recoverable scale: _not stated_
- sensitivity: rms 3.5 (CO, 13CO), 2.7 (C18O), 2.6 (DCO+) mJy/beam  
  > "| C$^{18}$O | (2–1) | 219560.4 | 15.8 | 0.02 | 0.26 $\times$ 0.22 | $-$72.41 | 2.7 | 3.4 $\pm$ 2.1 |" (Table 1)
- time on source: _not stated_
- observing dates: 2016 Sep 22 and 26 (Cycle 4 data); Cycle 2 data from Huang et al. 2016  
  > "with 38 antennas on 2016 September 22 and 41 antennas on 2016 September 26" (Observations and data reduction)
- pi or archival as stated: Cycle 4 PI D. Fedele; Cycle 2 data of Huang et al. 2016 (PI Öberg) combined, shared by J. Huang  
  > "CF and DF thank J. Huang for sharing the ALMA-Cycle 2 data." (Acknowledgments)
- Line: CO 2-1 (230538.0 MHz)
- Line: 13CO 2-1 (220398.7 MHz)
- Line: C18O 2-1 (219560.4 MHz)
- Line: DCO+ 3-2 (216112.6 MHz)
- Other facility **VLT/SPHERE**: 1.6 micron scattered light radial profile (Avenhaus et al. 2018)  
  > "1.6$\mu$m scattered light radial profile as observed in H-band with VLT/SPHERE (cite: Avenhaus:2018)" (4 Radial intensity profiles)
- External data: Best-fit dust model and dust surface density profile of AS 209 (Paper I)  
  > "The starting point is the best-fit model of the dust presented in Paper I, which reproduces the 1.3 mm continuum emission." (Model description) [from Fedele et al. 2018 (cite: Fedele:2018), Paper I]
- External data: ISM isotope ratios 16O/18O=557, 12C/13C=70  
  > "Assuming isotopic ratios for the local ISM of $^{16}$O/$^{18}$O = 557 and $^{12}$C/$^{13}$C=70 (cite: Wilson:1999)" (Line opacity) [from Wilson 1999 (cite: Wilson:1999)]
- External data: Cycle 2 ALMA data of AS 209  
  > "we have combined our data with the ones observed by (cite: Huang:2016) with ALMA during its Cycle 2" (Observations and data reduction) [from Huang et al. 2016 (cite: Huang:2016)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.7.2 for reduction, selfcal, continuum subtraction; 5.1.1 for deconvolution and imaging  
  > "software version 4.7.2 for data reduction, selfcalibration, continuum subtraction, and the version 5.1.1 for deconvolution and imaging" (Observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Both datasets self-calibrated individually before merging; Cycle 2 data shifted to common position using a 'false' model point  
  > "the datasets were first individually self-calibrated before being merged, allowing us to properly shift the Cycle 2 observations (via the use of a "false" model point)" (Observations and data reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "To improve the signal-to-noise ratio, we use a natural cleaning." (Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: performed in CASA (method not detailed)  
  > "software version 4.7.2 for data reduction, selfcalibration, continuum subtraction" (Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.25x0.21'' (CO, 13CO), 0.26x0.22'' (C18O), 0.26x0.21'' (DCO+)  
  > "| DCO$^{+}$ | (3–2) $^{b}$ | 216112.6 | 20.7 | 142 | 0.26 $\times$ 0.21 | $-$73.87 | 2.6 |" (Table 1)
- final rms: _not stated_

### Inherited from earlier work

- Observation details (spectral setup, calibration) given in Paper I  
  > "The observations cover the frequency range 211–275 GHz in band 6. For further details, see Paper I." (Observations and data reduction) [from Paper I (cite: Fedele:2018)]
- Disk inclination and PA (35 deg, 86 deg)  
  > "(PA=86$\ensuremath{^\circ}$ and $i$= 35$\ensuremath{^\circ}$, see Paper I)" (Radial intensity profiles) [from Paper I]
- Scale height and flaring exponent, dust surface density, aspect ratio for hydro  
  > "while keeping fixed the scale height[^2] $h_{c}$ (0.133) and the flaring exponent $\psi$ (0.10) as in paper I" (Model description) [from Paper I]

### Not stated but needed to reproduce (our reading)

- Self-calibration solution intervals, number of rounds, and reference models
- Line-free channels and continuum subtraction details
- CLEAN mask, threshold, cell and image size
- Gas-to-dust mass ratio and Sigma_c,gas values for the DALI grid
- Statistic used to compare model and data (best values appear chosen by eye)
- Radial profile bin width and averaging method
- Cycle 2 and Cycle 4 data weighting when combining
- FARGO-3D setup details such as the planet's accretion and smoothing

## Analysis recipe

1. **Combine and image data**: Self-calibrate Cycle 2 and Cycle 4 datasets separately, shift Cycle 2 to the same phase center, merge, continuum subtract and image with natural weighting  
  > "the datasets were first individually self-calibrated before being merged" (Observations and data reduction)
   - software: CASA
   - parameter: spectral resolution 0.2 km/s  
  > "the spectral resolution is 0.2 km s$^{-1}$" (Observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Estimate line opacity**: Use isotopic ratios to estimate tau; check with moment 8 maps with and without continuum subtraction  
  > "Fig. [3](#fg3) shows moment 8 maps generated with and without continuum subtraction" (Line opacity)
   - assumption: ISM isotope ratios 16O/18O=557, 12C/13C=70  
  > "isotopic ratios for the local ISM of $^{16}$O/$^{18}$O = 557 and $^{12}$C/$^{13}$C=70" (Line opacity)
   - fitting: _not stated_
   - validation: Consistency with moment 8 maps  
  > "These estimates are consistent with the maximum peak intensity maps" (Line opacity)
3. **Azimuthally averaged radial profiles**: Deproject for inclination and average azimuthally; CO averaged within +-20 deg of the major axis  
  > "the displayed profile was averaged at $\pm$20$\ensuremath{^\circ}$ along the major west-east emission axis after deprojecting" (Radial intensity profiles)
   - parameter: PA=86 deg, i=35 deg  
  > "PA=86$\ensuremath{^\circ}$ and $i$= 35$\ensuremath{^\circ}$" (Radial intensity profiles)
   - fitting: _not stated_
   - validation: _not stated_
4. **Thermochemical modelling of gas gaps**: Grid of DALI models varying Sigma_c,gas, gamma_gas, R_c,gas, then delta_gap and delta_ring; synthetic channel maps convolved with the observed beam, collapsed to moment maps and compared with the radial profiles  
  > "The data-model comparison is performed in the image plane: DALI creates synthetic channel maps which are then convolved with a Gaussian beam of the same size as the beam of the observations" (Model description)
   - software: DALI
   - parameter: gaps at 54-70 au and 87-119 au, ring at 70-87 au; same delta in both gaps  
  > "\delta_{gap}  & \text{for R $\in$ [54\,au, 70\,au] $\&$ [87\,au, 119\,au]}" (Model description)
   - assumption: Small grain surface density follows large grains; elemental C and O abundances 1.35e-4 and 2.88e-4  
  > "the surface density profile of the small grains population is assumed to follow that of the large grains" (Model description); "we assumed the following standard elemental abundances of carbon and oxygen of 1.35$\times$10$^{-4}$ and 2.88$\times$10$^{-4}$, respectively." (Footnote 1)
   - fitting: Parametric grid study, no formal fit statistic stated  
  > "we have only performed a simple parametric study of the gas perturbation as described below" (Gas gaps thermochemical Modelling)
   - validation: Models without gas gaps cannot reproduce the C18O profile  
  > "Indeed, without gas gaps, our model cannot reproduce the C$^{18}$O profile" (Modelling results)
5. **Hydrodynamical simulations of planet-disk**: 2D inviscid FARGO-3D runs with a 0.2 and a 0.3 M_Jup planet at 95 au for 1000 orbits  
  > "2D hydrodynamical simulations using FARGO-3D (cite: Benitez-Llambay:2016; Rosotti:2016) for a planet of 0.2 M$\rm_{Jupiter}$ and one of 0.3 M$\rm_{Jupiter}$ located at 95 au" (Comparison with hydrodynamical simulations)
   - software: FARGO-3D
   - parameter: grid 19-285 au, 1766 log radial cells, 4096 azimuthal cells; aspect ratio 0.1(R/100 au)^0.225  
  > "using 1766 logarithmically spaced cells in radius and 4096 cells in azimuth" (Comparison with hydrodynamical simulations)
   - assumption: viscosity alpha = 0  
  > "are inviscid (i.e. the viscosity, $\alpha$, is null)" (Comparison with hydrodynamical simulations)
   - fitting: _not stated_
   - validation: Qualitative comparison of gap width/depth with C18O data  
  > "This is commensurate with our C$^{18}$O observations and the results of Section [4](#modeling)." (Comparison with hydrodynamical simulations)

## Software

- **CASA** 4.7.2 (reduction), 5.1.1 (imaging): data reduction, self-calibration, continuum subtraction, deconvolution and imaging  
  > "software version 4.7.2 for data reduction, selfcalibration, continuum subtraction, and the version 5.1.1 for deconvolution and imaging" (Observations and data reduction)
- **DALI** : thermochemical disk modelling  
  > "We used the thermochemical disk model *Dust And LInes* (cite: Bruderer:2012; Bruderer:2013)" (Model description)
- **FARGO-3D** : 2D hydrodynamical simulations of planet-disk interaction  
  > "we have carried out 2D hydrodynamical simulations using FARGO-3D" (Comparison with hydrodynamical simulations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| C18O optical depth | <=0.8 | not stated | dimensionless | 2 | with $\tau$(C$^{18}$O) $\le$ 0.8 |
| 13CO and CO optical depth | >=2.5 | not stated | dimensionless | 2 | optically thick with $\tau$ $\ge$ 2.5 |
| Gas surface density scaling in gaps | about 0.1-0.2 | not stated | dimensionless | 4 | by applying a scaling factor of about 0.1–0.2 compared to the unperturbed profile |
| Best-fit grid values (gamma_gas, R_c,gas, delta_gap, delta_ring) | 0.2, 120 au, 0.1, 0.4 | grid step only | mixed | 4 | / $\delta_{gap}$ / **0.1**, 0.2, 0.3, 0.4 / $\Sigma_{gas}$ scaling factor for the gaps / |
| Isotope-selective photodissociation contribution to C18O in gaps | 10-20% | not stated | % | 4 | contributed to about 10–20$\%$ on the observed C$^{18}$O intensity inside the gaps |
| Inferred planet mass | 0.2-0.3 M_Jupiter at about 100 au | not stated | M_Jupiter | 5 | formation of a planet of 0.2–0.3 M$_{Jupiter}$ at about 100 au is occurring in the AS 209 protoplanetary disk |

## Qualitative findings

- C18O shows a compact centre and an outer ring (~140 au peak); DCO+ shows rings between the dust gaps and beyond the outer gap, anticorrelated with C18O  
  > "the DCO$^{+}$ radial intensity profile is clearly anticorrelated with that of C$^{18}$O and continuum" (Radial intensity profiles)

## Claim tuples

- H: The C18O deficit in the dust gaps reflects a gas surface density drop | E: DALI thermochemical grid with gap scaling factors compared to the C18O radial profile | R: Needs Sigma_gas reduced by factor ~0.1-0.2 in gaps; no-gap model fails | F: Gas gaps are intrinsic density drops, not temperature or opacity effects | **supported**
- H: A forming planet carves the gaps | E: FARGO-3D runs with 0.2 and 0.3 M_Jup planets compared to the gas profiles | R: Simulated gaps are consistent with the C18O deficit | F: A planet of at least 0.2 M_Jup is forming; one vs two planets cannot be distinguished | **partially**
- H: Outer C18O ring is caused by photodesorption | E: Compare C18O outer ring with 1.3 mm dust emission | R: The ring is also seen in dust | F: External photodesorption is ruled out | **supported**
- H: DCO+ traces forming planets | E: Compare DCO+ and C18O radial profiles | R: DCO+ peaks between the dust gaps where C18O is depleted | F: Ion enrichment may be a proxy for planet formation; chemistry not modelled | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Simple parametric study to assess how gas gaps affect molecular emission, not a perfect fit  
  > "As we aim not to perfectly fit the disk temperature and density structures but rather to analyse how gas gaps can affect the molecular emission" (Gas gaps thermochemical Modelling)
- Alternative: External photodesorption rejected; MRI dead zone edge reduces Sigma_gas only by a factor of a few  
  > "magneto-rotational instability can only reduce $\Sigma_{\rm gas}$ by a factor of a few at the edge of the dead zone" (On the physical nature of the C18O gap)
- How they decided it was enough: _not stated_
- Limitation (authors): Model does not fully reproduce observations because of 2D temperature structure uncertainties  
  > "our present modelling does not fully reproduce the observations because of uncertainties on the 2D temperature structure" (Modelling results)
- Limitation (authors): Insufficient sensitivity to see the co-rotation bump  
  > "This feature is not seen in our data because we do not have sufficient sensitivity." (Comparison with hydrodynamical simulations)
- Caveat (inferred, ours): Gas gap depth chosen by eye from a coarse grid without a goodness-of-fit statistic or uncertainties
- Caveat (inferred, ours): Same delta assumed in both gaps
- Caveat (inferred, ours): Temperature structure not fitted, so C18O drop could partly be chemical
- Caveat (inferred, ours): Planet mass range inferred by qualitative comparison with only two hydro runs
- Caveat (inferred, ours): DCO+ interpretation speculative

## Reproducibility

- Data public (paper): Cycle 2 data provided by J. Huang; project codes given  
  > "CF and DF thank J. Huang for sharing the ALMA-Cycle 2 data." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Self-calibration and imaging parameters
- Missing: DALI model setup (Sigma_c,gas values, gas-to-dust ratio, chemistry network) and fit criterion
- Missing: Paper I details for dust model
- Missing: FARGO-3D parameters beyond those given
- Data volume (inferred): ~100-300 GB for the two archival projects (Band 6 multi-EB, 4 lines)
- Score (inferred): 3/5, Archival data are available, but the recipe omits self-calibration, imaging and model details and relies heavily on Paper I.
- Rediscovery candidate: no, Key results come from an eye-judged DALI grid with incomplete setup, so they are hard to reproduce exactly.

## Links

- Method: Bruderer et al. 2012; Bruderer 2013 (DALI thermochemical code)
- Method: Miotello et al. 2014, 2016 (CO isotope-selective photodissociation in DALI)
- Method: Benitez-Llambay & Masset 2016 (FARGO-3D)
- Companion: Fedele et al. 2018 (Paper I) (1.3 mm continuum, dust model and planet hypothesis)
- Companion: Huang et al. 2016 (Cycle 2 AS 209 data)
- Companion: Teague et al. 2018b (AS 209 CO kinematics and geometry)

## Checks

```json
{
 "quotes": 67,
 "quotes_ok": 67,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 79,
  "stated": 46,
  "rate": 0.582
 },
 "evidence_ok": true
}
```
