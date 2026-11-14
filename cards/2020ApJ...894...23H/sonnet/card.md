# Determining the Physical Conditions of an Extremely Young Class 0 Circumbinary Disk around VLA 1623A

`2020ApJ...894...23H` | The Astrophysical Journal 2020 | first author: Hsieh, Cheng-Han | arXiv: 1904.00133 | DOI: 10.3847/1538-4357/ab7b69

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation, protoplanetary_disks
- Question: What are the physical conditions, kinematics and accretion/shock environment of the Class 0 circumbinary disk around VLA1623A, and is the 0.2 Msun binary mass from Cycle 0 consistent with Cycle 2 C18O data?  
  > "Our detailed flat and flared disk modeling shows that Cycle 2 C$^{18}$O J = 2-1 data is inconsistent with the combined binary mass of $0.2\,M_\odot$ as suggested by early Cycle 0 studies." (abstract)
- Target **VLA1623A (VLA1623-2417)**: coordinates α(J2000)=16h26m26.390s, δ(J2000)=-24°30'688"  
  > "pointing coordinates ($\alpha$(J2000) = 16^h^26^m^26.390s, $\delta$(J2000) = –24$'$30$''$688)" (Observations, CO); z/distance 120 pc (137.3 pc alternative noted)  
  > "In this paper, the distance of 120 pc (cite: 2013ApJ...764L..15M) is used in the modelling instead of 137.3 pc (cite: 2017ApJ...834..141O)." (Observations, footnote 1); distance from cite: 2013ApJ...764L..15M; 2008ApJ...675L..29L  
  > "In this paper, the distance of 120 pc (cite: 2013ApJ...764L..15M) is used in the modelling instead of 137.3 pc (cite: 2017ApJ...834..141O)." (Observations, footnote 1)

## Data provenance

- ALMA projects: 2013.1.01004.S, 2015.1.00084.S, 2016.1.01468.S, 2011.0.00902.S
- bands: Continuum Band 7; DCO+ Band 6  
  > "The observation is done in Band 7 with an integration time of 4798 seconds." (2.3 Continuum data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12m array plus 7m ACA and Total Power (C18O, DCO+); 12m only for CO  
  > "We also include the 7m Atacama Compact Array (ACA) (hereafter 7m array) and Total Power Array of ACA in our analysis." (2.2 C18O)
- configurations: CO: C34-1; C18O: C34-5 and C34-1  
  > "using 47 antenna of 12 m array in C34-1 compact configuration" (2.1 CO)
- baselines: CO 15.1-360.6 m; C18O C34-5 18.9-1090 m, C34-1 14.2-347.3 m, 7m 7.1-48.9 m  
  > "12m array configuration C34-5 (baseline range $18.9 \sim 1090$ m), C34-1 (baseline range $14.2 \sim 347.3$ m), and 7m array (baseline range $7.1 \sim 48.9$ m)" (2.2 C18O)
- angular resolution: _not stated_
- max recoverable scale: C18O 23.26"; CO 4.33"; SO 3.9"; continuum 0.88"  
  > "Maximum Recoverable Scale" (Table 1)
- sensitivity: _not stated_
- time on source: CO 10 minutes; continuum 4798 s  
  > "The total on-source integration time is 10 minutes" (2.1 CO)
- observing dates: CO 2019 March 15; SO 4 March 2017  
  > "The observation was taken on 2019 March 15" (2.1 CO)
- pi or archival as stated: CO own proposal (Hsieh); others archival from other PIs  
  > "(project ID: 2018.1.00388S, PI: Chenghan Hsieh)" (2.1 CO)
- Line: CO 3-2 (345.79599 GHz)
- Line: C18O 2-1 (219.56036 GHz)
- Line: DCO+ 3-2 (216.11402 GHz)
- Line: SO v=0, J=8_8-7_7 (344.31061 GHz)
- External data: Cycle 0 C18O result: 0.2 Msun, inclination 55 deg, Sigma0 = 6.173e21 cm^-2  
  > "we adopted the number to be $6.173\times 10^{21}$ cm$^{-2}$, and the disk inclination angle is $55^{\circ}$" (3.4 Flat Disk Model) [from (cite: 2013A&A...560A.103M)]
- External data: Temperature ~30 K at 100 AU from DCO+ 5-4/3-2  
  > "we adopted a temperature of $\sim30$ K at 100 AU based on the DCO$^{+}$ 5-4/3-2 data" (3.4 Flat Disk Model) [from (cite: 2018arXiv180505205M)]
- External data: Disk mass 0.02 Msun and dendrogram/CMU results  
  > "we normalized the $\rho_0$ such that the total mass of the circumbinary disk is 0.02 $M_{\odot}$ (Cheong et al. 2019; submitted)" (3.5 Flared Disk Model) [from Cheong et al. 2019; submitted]

## Processing

### Calibration

- pipeline or manual: CO: ALMA pipeline; SO and Total Power: ARC/ALMA calibration scripts  
  > "The data is calibrated by the ALMA calibration script" (2.5 SO data)
- casa version: CASA 5.4.0-70 (CO data)  
  > "Common Astronomy Software Applications (CASA) version 5.4.0-70 is used to calibrate the visibility data" (2.1 CO)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1924+2914 (CO bandpass/flux); J1625+2527 phase  
  > "with J1924+2914 as the calibrator for bandpass and flux calibration and J1625+2527 for phase calibration" (2.1 CO)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA CLEAN  
  > "We used CASA CLEAN task with briggs 0.5 weighting and Hogbom as deconvolver for imaging." (2.1 CO)
- deconvolver: Hogbom  
  > "Hogbom algorithm is used for the deconvolution process" (2.2 C18O)
- weighting robust: CO 0.5; C18O Briggs -1.5/-1.0/natural; DCO+ robust -0.5; SO robust 0.0; continuum uniform  
  > "with a weighting parameter of Briggs -1.5, Briggs -1.0, and a natural weighting" (2.2 C18O)
- uv taper: 0.25" (C18O Briggs -1.5/-1.0); 1.0" (DCO+)  
  > "the UV taper range is set to 1$''$0" (2.4 DCO+)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12m and 7m combined in CLEAN; Total Power not combined  
  > "We did not combine the Total Power data with the 12m+7m array data" (3.3 Large scale emission)
- smoothing: _not stated_
- final beam: C18O natural 0.52x0.31"; CO 0.99x0.59"; DCO+ 0.51x0.31"; SO 1.11x0.76"  
  > "Beam Size" (Table 1)
- final rms: C18O 9 mJy/beam (natural); CO 11; DCO+ 5; SO 20; continuum 0.5  
  > "Rms noise" (Table 1)

### Inherited from earlier work

- Dendrogram analysis, CMU modelling, disk mass, data preparation  
  > "More technical details of dendrogram data preparation and accretion flows modeling can be found in Cheong et al. (2019; submitted)’s paper." (3.3 Dendrograms) [from Cheong et al. 2019; submitted]
- Flared disk model equations  
  > "We followed the equations of Guilloteau & Dutrey to develop a 3D flared disk model" (3.5 Flared Disk Model) [from (cite: 1998A&A...339..467G; 2014ApJ...793....1Y)]

### Not stated but needed to reproduce (our reading)

- Dendrogram parameters (min value, delta, min npix) and moment map thresholds
- Line-free channels and continuum subtraction method
- Image sizes and cell sizes
- Absolute flux scale uncertainty
- Details of SimObserve/SimAnalyze settings (integration times, weather)
- Quantitative fitting metric; model comparison is by eye with isophote contours
- Calibration details for archival data besides CO
- Number of Gaussian initial guesses for total power fit

## Analysis recipe

1. **Compare Cycle 0 and Cycle 2 C18O**: Compare PV diagrams and recoverable scales of both datasets  
  > "These features do not show in the Cycle 0 observations because there is not enough sampling in the short baselines." (3.1)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit Total Power spectrum for large-scale emission**: Five Gaussians fit to Total Power spectrum  
  > "five Gaussian functions are used to fit the total power spectrum" (3.3)
   - fitting: Gaussian least-squares, chi2/dof=29.29  
  > "$\chi^{2}/dof=29.29$" (Table 2)
   - validation: _not stated_
3. **Identify accretion flows and disk size**: Dendrogram in PPV space on low-resolution C18O; disk edge from gap in blue-shifted channel maps  
  > "The dendrogram algorithm is used to identify the connected structures in the position-position-velocity (PPV) space" (3.3)
   - assumption: Disk axially symmetric, Keplerian  
  > "without loss of generality, we can assume the disk is axially symmetric and use the blue-shifted side to constrain the disk size" (3.3)
   - fitting: _not stated_
   - validation: CMU model comparison in Cheong et al.  
  > "Cheong et al. (2019; submitted) further compared the data with the CMU model (cite: 1976ApJ...210..377U; 1981Icar...48..353C), a rotating collapse model with conserved specific angular momentum" (Using Dendrograms to identify Accretion flows and set constraint on disk size)
4. **Flat Keplerian disk model**: LTE ray tracing, convolved with SimObserve/SimAnalyze, compared to PV diagram  
  > "A simple ray tracing radiative transfer calculation scheme assuming local thermal equilibrium (LTE) with a thermal broadening of 0.2 kms$^{-1}$" (3.4)
   - software: CASA SimObserve, CASA SimAnalyze
   - parameter: M=0.2 Msun, i=55 deg, T0~30 K, T∝R^-0.5, Sigma∝R^-1  
  > "For temperature distribution we assume the temperature power law exponent to be -0.5" (3.4)
   - fitting: _not stated_
   - validation: _not stated_
5. **Flared disk grid to constrain a and h0**: RADMC-3D models over 36 combinations of h0 and a, compared with red-shifted PV by isophote contours and overlap with 7 sigma  
  > "we run the parameters $h_{0}= 1.0,\,2.5, \,5.0,\,10.0,\,15.0,\,25.0$ (AU) and $a = 2.0,\,2.3,\,2.6,\,3.0,\,3.3,\,4.0$ for a total of 36 parameter combinations" (3.5)
   - software: RADMC-3D, CASA SimObserve, CASA SimAnalyze
   - parameter: b=1.29, C18O/H2=1.7e-7, disk mass 0.02 Msun, radius 180 AU, i=55 deg, d=120 pc, 500^3 grid at 0.72 AU, T0=30 K  
  > "we set the C$^{18}$O to H$_{2}$ ratio to be $1.7\times 10^{-7}$" (3.5)
   - assumption: Hydrostatic equilibrium; fixed temperature profile  
  > "Assuming hydrostatic equilibrium, the scale height $b=1+v-q/2$" (3.5)
   - fitting: Grid comparison by eye, no formal likelihood  
  > "Isophote contours for each simulation model are plotted in order to compare the observational data with simulation models." (Flared Disk Model)
   - validation: Parameter sensitivity discussion for inclination, distance, temperature  
  > "Even for 5$^{\circ}$ variation of inclination angle, the velocity stretching factor is less than 7 %." (3.6.1)
6. **SO shocks and outflow comparison**: Moment maps, channel maps and PV diagrams of SO vs C18O, DCO+ and CO outflow  
  > "we use SO as a shock tracer to understand the interactions between the accretion flows and the circumbinary disk" (3.7)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.4.0-70: calibration and imaging with CLEAN, SimObserve, SimAnalyze  
  > "Common Astronomy Software Applications (CASA) version 5.4.0-70 is used to calibrate the visibility data" (Observations, CO)
- **RADMC-3D** : synthetic flared disk images  
  > "We apply the RADMC-3D radiative transfer code on flared disk model to create synthetic images" (3.5)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Circumbinary disk radius | 180 | ~30 AU (half beam) | AU | 3 | the circumbinary disk size is constrained to be 180 AU |
| Density power law index a | ≤3.3 | not stated | dimensionless | 5 | we can only constrain the density power-law $a$ for the VLA1623A circumbinary disk to be $a \leq 3.3$ |
| Scale height at 100 AU | ≤15 | not stated | AU | 5 | vertical scale height at 100 AU to be $h_{0} \leq 15\,$ AU |
| Specific angular momentum at centrifugal radius | 120 | not stated | AU km/s | 0 | The corresponding specific angular momentum is 120 AU kms$^{-1}$. |
| Main Total Power component velocity | 3.632 | not stated | km/s | 2 | 3.632 |
| Combined binary mass | 0.3-0.5 | not stated | Msun | 0 | The combined binary mass for VLA1623A should be modified to $0.3\sim0.5\,M_\odot$. |

## Qualitative findings

- Wall-like structure south of VLA1623B, at least 780 AU wide  
  > "the wall on the south side of VLA1623B has a plane of sky width at least 780 AU" (3.8)

## Claim tuples

- H: Is the high-velocity inner emission due to disk flaring? | E: Flared disk grid in RADMC-3D vs PV diagram | R: No model reproduces the super-Keplerian peak; h0≤15 AU | F: Not due to projection of a flared disk | **supported**
- H: Is 0.2 Msun binary mass consistent with Cycle 2 data? | E: Keplerian models and escape velocity of accretion flow I | R: Inconsistent; flows match 0.5 Msun escape velocity | F: Binary mass 0.3-0.5 Msun, though degenerate with envelope mass | **partially**
- H: Are there two overlapping outflows? | E: Dendrogram structures II and VIII with CO and SO | R: Two cavity walls at same position, different velocities | F: Outflows from both VLA1623A and B | **supported**

## Reasoning

- Why this data: Cycle 2 has more antennas and larger recoverable scale than Cycle 0  
  > "Cycle 2 observations have increased sensitivity from the larger number of antennas and larger recoverable scale." (3.1)
- Why this method: _not stated_
- Alternative: Infall collision explanation judged unlikely given short orbital period  
  > "making them unlikely to be observed if the infalling materials are not continuously supplied by the envelope." (4.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Temperature and density degeneracy; fixed temperature profile  
  > "This will affect the density and scale height modeling, making it even more difficult to break the degeneracy" (3.6.2)
- Caveat (inferred, ours): Model comparison is by eye with no formal fit or uncertainties
- Caveat (inferred, ours): Temperature profile and mass fixed from other work
- Caveat (inferred, ours): Resolution does not resolve binary
- Caveat (inferred, ours): Dendrogram analysis relies on unpublished paper

## Reproducibility

- Data public (paper): Archival data from ALMA Archive  
  > "We use the high resolution continuum data from the ALMA Archive" (2.3 Continuum data)
- Products in archive: _not stated_
- Missing: Dendrogram settings
- Missing: Model grid scripts
- Missing: Moment map thresholds
- Data volume (inferred): ~100-300 GB for several multi-array projects
- Score (inferred): 3/5, Public data and many imaging details, but modelling by eye and key inputs from an unpublished paper.
- Rediscovery candidate: no, Main results rely on qualitative comparison and unpublished dendrogram analysis.

## Links

- Method: (cite: 1998A&A...339..467G) (Flared disk equations)
- Companion: Cheong et al. 2019; submitted (Dendrogram and CMU accretion flow analysis)
- Companion: (cite: 2013A&A...560A.103M) (Cycle 0 C18O disk analysis)

## Checks

```json
{
 "quotes": 66,
 "quotes_ok": 66,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2018.1.00388.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 48,
  "rate": 0.64
 },
 "evidence_ok": true
}
```
