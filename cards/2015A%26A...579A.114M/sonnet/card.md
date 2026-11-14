# A low-mass protostar's disk-envelope interface: disk-shadowing evidence from ALMA DCO<SUP>+</SUP> observations of VLA1623

`2015A&A...579A.114M` | Astronomy and Astrophysics 2015 | first author: Murillo, N. M. | arXiv: 1505.07761 | DOI: 10.1051/0004-6361/201425118

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: What is the physical and chemical structure of the disk-envelope interface of the Class 0 protostar VLA1623A, as traced by DCO+ (3-2) emission?  
  > "In this paper we present the results of our ALMA observations and simple chemical modeling, aiming to understand the physical structure of the boundary between the envelope and the disk in a Class 0 protostar." (Introduction)
- Target **VLA1623 (VLA1623A)**: coordinates 16:26:26.419 -24:24:29.988 (J2000, pointing)  
  > "pointing coordinates $\alpha$=16:26:26.419 $\delta$=-24:24:29.988 J2000" (Observations); "VLA1623-2417 (hereafter VLA1623) is a triple non-coeval protostellar system located in $\rho$ Ophiuchus at $d\sim$120 pc (cite: murillo2013a)." (Introduction); z/distance ~120 pc  
  > "pointing coordinates $\alpha$=16:26:26.419 $\delta$=-24:24:29.988 J2000" (Observations); "VLA1623-2417 (hereafter VLA1623) is a triple non-coeval protostellar system located in $\rho$ Ophiuchus at $d\sim$120 pc (cite: murillo2013a)." (Introduction); distance from Murillo & Lai 2013 (murillo2013a)  
  > "pointing coordinates $\alpha$=16:26:26.419 $\delta$=-24:24:29.988 J2000" (Observations); "VLA1623-2417 (hereafter VLA1623) is a triple non-coeval protostellar system located in $\rho$ Ophiuchus at $d\sim$120 pc (cite: murillo2013a)." (Introduction)

## Data provenance

- ALMA projects: 2011.0.00902.S, 2013.1.01004.S
- bands: Band 6 (230 GHz)  
  > "in Band 6 (230 GHz)" (Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: Cycle 0 12-m array (16 antennas) and Cycle 2 ACA  
  > "comprised of 16 antennas with a maximum baseline of $\sim$400 m" (Observations); "our ALMA Cycle 2 Atacama Compact Array (ACA) observations carried out on 7 August 2014" (Observations)
- configurations: _not stated_
- baselines: max baseline ~400 m (12-m)  
  > "comprised of 16 antennas with a maximum baseline of $\sim$400 m" (Observations)
- angular resolution: 12-m: 0.85" x 0.65", P.A. 96 deg; ACA: 8.6" x 4.2", P.A. -76 deg  
  > "The synthesized beam size for the images is 0.85$\ensuremath{''}$ $\times$ 0.65$\ensuremath{''}$ with P.A. = 96$^{\circ}$." (Observations); "with a synthesized beam of 8.6$\ensuremath{''} \times 4.2\ensuremath{''}$ with P.A. = -76$^{\circ}$" (Observations)
- max recoverable scale: 12-m: 4"; ACA provides 4"-18" scales  
  > "Our ALMA observations provide a maximum scale of 4$\ensuremath{''}$ and a field of view (FOV) of 24$\ensuremath{''}$" (Observations)
- sensitivity: 12-m: 12 mJy/beam per 0.0847 km/s channel; ACA: 73 mJy/beam per 0.021 km/s  
  > "The rms noise of the channel map is 12 mJy beam$^{-1}$ for a spectral resolution of 0.0847 km s$^{-1}$, giving a peak S/N = 7." (Observations); "The rms noise of the channel map is 73 mJy beam$^{-1}$ for a spectral resolution of 0.021 km s$^{-1}$" (Observations)
- time on source: 12-m: one hour total observing time (58% duty cycle); ACA: 2 hours  
  > "Total observing time was one hour with a 58% duty cycle." (Observations); "Total observing time was 2 hours." (Observations)
- observing dates: 8 April 2012 (Cycle 0); 7 August 2014 (ACA)  
  > "during the early science Cycle 0 period on 8 April 2012" (Observations)
- pi or archival as stated: _not stated_
- Line: DCO+ 3-2 (216.11258 GHz)
- External data: Density and temperature profile of VLA1623 from DUSTY modeling of JCMT continuum and SED (n ∝ r^-1.4; 30 K at ~1.5")  
  > "we use the density and temperature profile of VLA1623 obtained by (cite: jorgensen2002) where 30 K is at $\sim$1.5" assuming a distance of 120 pc." (Analysis) [from Jørgensen et al. 2002 (cite: jorgensen2002)]
- External data: Keplerian disk models and C18O results (central mass 0.2 Msun, inclination 55 deg)  
  > "we assume a free-fall velocity profile with a central mass of 0.2 $M_{\rm \odot}$ (cite: murillo2013b)" (Analysis) [from Murillo et al. 2013 (cite: murillo2013b)]
- External data: Molecular data from LAMDA  
  > "Molecular data for and are obtained from LAMDA ((cite: schoeier2005);" (Analysis) [from Schöier et al. 2005 (cite: schoeier2005)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Cycle 0: Titan; ACA: J1517-243 and Mars  
  > "Data calibration was done with 3C 279, 1733-130, and Titan for bandpass, gain, and flux calibration, respectively." (Observations); "Data calibration was done with J1517-243 and Mars for flux" (Observations)
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
- final beam: 0.85" x 0.65" (12-m); 8.6" x 4.2" (ACA)  
  > "The synthesized beam size for the images is 0.85$\ensuremath{''}$ $\times$ 0.65$\ensuremath{''}$ with P.A. = 96$^{\circ}$." (Observations)
- final rms: 12 mJy/beam (12-m); 73 mJy/beam (ACA)  
  > "The rms noise of the channel map is 12 mJy beam$^{-1}$ for a spectral resolution of 0.0847 km s$^{-1}$" (Observations)

### Inherited from earlier work

- Calibration details of the Cycle 0 data  
  > "Further calibration details and results from the other observed lines can be found in (cite: murillo2013b)." (Observations) [from (cite: murillo2013b)]
- Radiative transfer disk+envelope methods  
  > "radiative 2D disk plus envelope models using radiative transfer methods as in (cite: harsono2013)" (Discussion) [from (cite: harsono2013)]
- CO abundance profile (Constant/Drop) models  
  > "we study the effect of abundance through the use of different abundance profiles following the models detailed in (cite: jorgensen2005) and (cite: yildiz2010)." (Analysis) [from (cite: jorgensen2005); (cite: yildiz2010)]

### Not stated but needed to reproduce (our reading)

- CASA version and imaging parameters (weighting, cleaning, masks, cell/image size) for both datasets
- Continuum subtraction method and line-free channels
- Which ALMA project code corresponds to which dataset
- Reaction network table entries (reactions blank in text) and full RATRAN setup/grid
- Exact velocity range used for integrated-intensity maps and radial cut extraction method
- Details of the ALMA simulator test and the full time-dependent network

## Analysis recipe

1. **Map DCO+ emission and kinematics**: Integrated intensity, moment 1 maps and PV diagrams compared with Keplerian and infall+Keplerian models from earlier work  
  > "The Position-Velocity (PV) diagrams of and emission (Fig. [3](#figpv)) are constructed and over-plotted with the best fitting thin disk models" (Results)
   - fitting: _not stated_
   - validation: _not stated_
2. **Steady-state analytic chemical network for DCO+**: Simple network with free Tev, nde, X_CO and o/p H2D+ ratio, run on density and temperature profiles  
  > "The evaporation temperature $T_{\rm ev}$, desorption density $n_{\rm de}$ and CO abundance $X_{\rm CO}$ are free parameters." (Analysis)
   - parameter: Cases a-f of Drop abundance (Tev 30-35 K, nde 7e4-3e6 cm-3, XD 1e-6 to 1e-8) and Tests 1-4 varying density/temperature  
  > "We set up 4 tests, including the original profile from (cite: jorgensen2002) referred to as Test 1, by increasing or decreasing by a constant factor either the density or temperature profile." (Analysis)
   - assumption: X_HD = 1e-5 relative to hydrogen nuclei; lower limit o/p 1e-3; Tgas = Tdust  
  > "We assume the density profile is equal to the density $n_{\rm \ce{H2}}$ and the abundance of $X_{\rm \ce{HD}}$ = 10$^{-5}$ with respect to the total hydrogen nuclei density $n_{H}$" (Analysis, chemical network and model)
   - fitting: Manual parameter variation, no sampler  
  > "We set up 4 tests, including the original profile from (cite: jorgensen2002) referred to as Test 1, by increasing or decreasing by a constant factor either the density or temperature profile." (Modeling results, Physical properties)
   - validation: Comparison with full time-dependent UMIST RATE06 deuterated network  
  > "We find that the large network confirms both the general trend found in the simple network" (Analysis)
3. **Line radiative transfer and comparison with observed radial profiles**: 1-D RATRAN level populations, 2-D ray tracing, convolved with the beam, continuum subtracted, radial profiles compared with observed  
  > "we calculate the level populations with the 1-D version of RATRAN, and then run the level populations with the 2-D ray tracing to form the ring structure." (Analysis)
   - software: RATRAN
   - parameter: inclination 55 deg; central mass 0.2 Msun; free-fall (DCO+) or Keplerian (C18O) velocity  
  > "For both emission lines, we use an inclination of 55$^{\circ}$ (90$^{\circ}$ = face-on)" (Analysis)
   - fitting: _not stated_
   - validation: ALMA simulator test showed no significant difference in peak position  
  > "We find no significant difference in the peak position between the method used here and running the models through the ALMA simulator" (Analysis)
4. **Test disk-shadowing with 2D disk+envelope dust temperature models**: Radiative transfer disk+envelope models with and without disk, centrifugal radius 200 and 50 AU  
  > "Two values for the centrifugal radius $R_{\rm c}$, 200 AU and 50 AU, are chosen." (Discussion)
   - parameter: L=1 Lsun, envelope 1 Msun, disk 0.02 Msun, 180 AU, cavity opening angle 30 deg, scale height 0.1 AU  
  > "a disk mass of 0.02 M$_{\odot}$ and radius of 180 AU" (Discussion)
   - fitting: _not stated_
   - validation: Compared with the temperature needed by the chemical model and ACA outflow-direction profile  
  > "The temperature conditions required to reproduce the observed emission with our simple chemical model are therefore in agreement with the results obtained from the 2D radiative transfer disk plus envelope model." (Discussion)

## Software

- **RATRAN** : 1-D and 2-D line radiative transfer  
  > "The results of the analytic chemical network are run through the molecular excitation and line radiative transfer program RATRAN to generate line emission maps." (Analysis)
- **DUSTY** : continuum radiative transfer for the adopted density/temperature profile (from Jørgensen et al. 2002)  
  > "fitting single dish JCMT continuum images and the spectral energy distribution (SED) with continuum radiative transfer modeling using DUSTY" (Analysis)
- **ALMA simulator** : checking effect of interferometric filtering on models  
  > "running the models through the ALMA simulator with the actual ALMA configuration" (Analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Offset of southern DCO+ clump from VLA1623A | 2.5 (~300 AU) | not stated | arcsec | 1 | is offset by about 2.5$\ensuremath{''}$ (300 AU) from VLA1623A |
| Dust temperature at DCO+ peak | 11-16 | not stated | K | 3 | Examining the temperature profile shows that the emission peaks at a range of 11-16 K. |
| Temperature decrease factor needed | 1.5 | not stated | dimensionless | 3 | a drop abundance with a decreased temperature profile by a factor of 1.5 generates a peak at the same position as the observed emission |
| Freeze-out region radius without disk | ~400 (150 AU further than with disk) | not stated | AU | 4 | omitting the disk causes the freeze out region to move outward to $\sim$400 AU, 150 AU further out than the models including a disk. |

## Qualitative findings

- DCO+ emission is clumpy and borders the Keplerian disk, with velocity gradient similar to C18O  
  > "shows a clumpy structure with two main clumps to the north and south of VLA1623A" (Results)
- ACA emission along the outflow axis peaks at larger radii (~5"), consistent with unmodified constant-abundance models  
  > "the emission along the outflow axis lies at larger radii, $\sim$5$\ensuremath{''}$" (Conclusions)

## Claim tuples

- H: Is the DCO+ ring position explained by chemistry or by lower temperature? | E: Varied abundance, o/p ratio, density and temperature in the chemical model plus RATRAN | R: Only a temperature reduced by a factor 1.5 reproduces the peak | F: Emission location is due to physical conditions, a lowered temperature, not special chemistry | **supported**
- H: Does the disk shield the interface from heating? | E: 2D disk+envelope dust temperature models with and without disk; ACA comparison | R: Temperature beyond 200 AU drops below 20 K; freeze-out moves inward by 150 AU | F: Disk shadowing causes the DCO+ ring and shows broken density/temperature transition | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: VeLLO/episodic accretion relic rejected because heating timescales are short and luminosity 0.4-2 Lsun is too high  
  > "Hence VLA1623A has not recently come out of the quiescent accretion phase" (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): C18O emission too weak for further kinematical analysis  
  > "However the emission is too weak, peaking at 7$\sigma$ in the channel map, to carry out further kinematical analysis." (Results)
- Caveat (inferred, ours): Models tuned by hand to a single peak position without uncertainties or fit statistics
- Caveat (inferred, ours): Peak S/N only ~7 and 12-m data filter out emission beyond 4"
- Caveat (inferred, ours): Spherical/thin-disk assumptions and Tdust=Tgas

## Reproducibility

- Data public (paper): ALMA project codes cited in acknowledgements  
  > "This paper made use of the following ALMA data: ADS/JAO.ALMA 2011.0.00902.S and 2013.1.01004.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging parameters and CASA version
- Missing: Full chemical network input files and RATRAN configuration
- Missing: No quantified fit criteria
- Data volume (inferred): ~10-30 GB
- Score (inferred): 3/5, Public data and model description, but imaging and many model details missing, and results are qualitative.
- Rediscovery candidate: no, Main results are model-comparison peak positions, with incomplete recipe.

## Links

- Method: Murillo et al. 2013 (cite: murillo2013b) (Cycle 0 calibration and disk models)
- Method: Jørgensen et al. 2002 (cite: jorgensen2002) (Source density/temperature profile)

## Checks

```json
{
 "quotes": 59,
 "quotes_ok": 59,
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
  "facts": 72,
  "stated": 41,
  "rate": 0.569
 },
 "evidence_ok": true
}
```
