# Origin of the Shell Structure in the Primary Outflow from IRAS 15398−3359

`2025ApJ...986..150H` | The Astrophysical Journal 2025 | first author: Hanawa, Tomoyuki | arXiv: 2505.08470 | DOI: 10.3847/1538-4357/addac0

Card schema 1.0 | model gemini-4-argon | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: star_formation
- Question: Whether the shell structure in the primary outflow of IRAS 15398-3359 is formed by the same physical mechanism (repeated expansion and compression) as the barrel structure in an industrial underexpanded jet.  
  > "We examine the similarity between the primary outflow of IRAS 15398-3359 and industrial underexpanded jet and the possibility that the shell structure of the former is due to repeated expansion and compression" (abstract); "In this paper we compare IRAS 15398 3359 and engineering underexpanded jet outflow and its substructure to examine the possibility that the former’s shell structure and latter’s barrel structure are formed by the same physical mechanism." (1. INTRODUCTION)
- Target **IRAS 15398-3359**: coordinates _not stated_; z/distance 154.9 +3.2/-3.4 pc  
  > "IRAS 15398 − 3359 is a Class 0 protostar in the Lupus I star forming region located at a distance of 154.9 +3 − 3 . . 2 4 pc (Galli et al. 2020) and is associated with multiple outflows." (1. INTRODUCTION); distance from Galli et al. (2020)  
  > "IRAS 15398 − 3359 is a Class 0 protostar in the Lupus I star forming region located at a distance of 154.9 +3 − 3 . . 2 4 pc (Galli et al. 2020) and is associated with multiple outflows." (1. INTRODUCTION)

## Data provenance

- ALMA projects: 2018.1.01205.L, 2013.1.00879.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archival ALMA data from projects 2018.1.01205.L (PI: Satoshi Yamamoto, FAUST large program) and 2013.1.00879.S (Yen et al. 2013)  
  > "The H 2 CO (3 0 , 3 − 2 0 , 2 ) and CS ( J = 5 − 4) lines were observed in the project 2018.1.01205.L (PI: Satoshi Yamamoto), as a part of ALMA large program FAUST" (2.1. Observation Specifications); "The 12 CO ( J = 2 − 1) line was taken from the ALMA archival data (2013.1.00879.S; Yen et al. 2013)." (2.1. Observation Specifications)
- Line: H2CO 3(0,3)-2(0,2) (not stated)
- Line: CS J=5-4 (not stated)
- Line: 12CO J=2-1 (not stated)
- Other facility **JWST**: MIRI images (filters F560W, F770W, F1000W) and Medium Resolution Spectroscopy (MRS) spectral cubes covering 4.9-28 um from program 2151 (CORINOS, PI: Y.-L. Yang), tracing H2, [Fe II], and [Ne II] lines.  
  > "The MIRI images and spectral cubes were taken with the Medium Resolution Spectroscopy (MRS) by the JWST CORINOS program (Yang et al. 2022) (program 2151, PI: Y.-L. Yang)." (2.1. Observation Specifications); "The MIRI images were taken with three filters, F560W, F770W, and F1000W, centered at 5.6, 7.7, and 10.0 µ m, respectively." (2.1. Observation Specifications); "Figure 5 show continuum-subtracted intensity of [Fe II ] 25.99 µ m, 17.935 µ m, and [Ne II ] 12.81 µ m." (2.2. Observation Results)
- External data: Distance to IRAS 15398-3359 of 154.9 +3.2/-3.4 pc  
  > "IRAS 15398 − 3359 is a Class 0 protostar in the Lupus I star forming region located at a distance of 154.9 +3 − 3 . . 2 4 pc (Galli et al. 2020)" (1. INTRODUCTION) [from Galli et al. (2020)]
- External data: Outflow inclination angle of 20 degrees  
  > "The angular separation 5 ′′ correspond to the deprojected distance of 824 au for the assumed inclination angle of 20 ◦ (Oya et al. 2014)." (Figure 1 caption) [from Oya et al. (2014)]
- External data: Systemic velocity v_sys = 5.24 km s^-1 measured from C18O (J=2-1)  
  > "Throughout this paper we adopt the systemic velocity of v sys = 5 . 24 km s − 1 , the central value measured by Yen et al. (2017) from the C 18 O ( J =2 − 1) emission line." (2.2. Observation Results) [from Yen et al. (2017)]
- External data: H2 temperature and column density distributions from JWST MIRI MRS observations  
  > "Okoda et al. (2025) derived the temperature and column density of H 2 molecules from the JWST MIRI MRS observations" (2.2. Observation Results) [from Okoda et al. (2025)]
- External data: Ambient gas density around IRAS 15398-3359 of n_H2 = 2.6 x 10^4 cm^-3 from Herschel continuum emission  
  > "Redaelli et al. (2019) estimated the gas density to be n H 2 = 2 . 6 × 10 4 cm − 3 around IRAS 15398 − 3359 from the radio and far infrared continuum emission observed with Herschel." (5. DISCUSSIONS AND SUMMARY) [from Redaelli et al. (2019)]
- Simulation/model as data: 2D axisymmetric ideal gas hydrodynamic simulations (Models A, B, and C) using a second-order accurate finite volume method with a flux split method based on an approximate Riemann solver.  
  > "We make a hydrodynamic model to reproduce the shell structure seen in IRAS 15398 − 3359." (4.1. Model Setting); "We use the finite volume method in our numerical simulations." (4.1. Model Setting); "We employ a flux split method based on approximate Riemann solution to avoid negative density and pressure." (4.1. Model Setting)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
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
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA observation parameters for H2CO, CS, and 12CO  
  > "The observation parameters are described by Okoda et al. (2021a), Okoda et al. (2023), and Yen et al. (2017)." (2.1. Observation Specifications) [from Okoda et al. (2021a), Okoda et al. (2023), Yen et al. (2017)]
- ALMA data reduction details for 2018.1.01205.L and 2013.1.00879.S  
  > "The data reduction details of both data are also given by Okoda et al. (2025)." (2.1. Observation Specifications) [from Okoda et al. (2025)]
- Hydrodynamic simulation code previously applied to gas accretion onto protostellar disks  
  > "It has been applied to gas accretion to a gas disk rotating around a protostar (Hanawa & Matsumoto 2021; Hanawa et al. 2022, 2024)." (4.1. Model Setting) [from Hanawa & Matsumoto (2021), Hanawa et al. (2022, 2024)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration/imaging parameters for the ALMA datasets (deferred to Okoda et al. 2021a, 2023, 2025 and Yen et al. 2017)
- Exact angular resolution (beam size), channel width, and rms noise of the ALMA H2CO, CS, and 12CO cubes
- Intensity clip thresholds used to generate the ALMA Moment 1 maps in Figure 3
- Slit width used for extracting the ALMA position-velocity diagrams in Figure 4
- Source code or exact flux-splitting algorithm for the custom hydrodynamic simulation code

## Analysis recipe

1. **Measure shell positions and barrel diameters from JWST MIRI imaging**: Measure projected distances and diameters of shells 1 and 2 from the composite three-filter (F560W, F770W, F1000W) MIRI image and deproject distances along the outflow.  
  > "Figure 1 shows the southwest part of the primary outflow by RGB image built from a composite of three filter (F560W, F770W, and F1000W) MIRI images (Okoda et al. 2025)." (2.2. Observation Results); "The first shell is d s1 =340 au (2 ′′ . 06 from the protostar on the sky) while the diameter of the barrel is D w1 = 322 au (2 ′′ . 08)." (2.2. Observation Results)
   - software: JWST Calibration Pipeline
   - assumption: Distance of 154.9 pc and outflow inclination angle of 20 degrees  
  > "IRAS 15398 − 3359 is a Class 0 protostar in the Lupus I star forming region located at a distance of 154.9 +3 − 3 . . 2 4 pc (Galli et al. 2020)" (1. INTRODUCTION); "The angular separation 5 ′′ correspond to the deprojected distance of 824 au for the assumed inclination angle of 20 ◦ (Oya et al. 2014)." (Figure 1 caption)
   - fitting: _not stated_
   - validation: _not stated_
2. **Analyze molecular outflow kinematics using ALMA Moment 1 maps and PV diagrams**: Construct Moment 1 (intensity-weighted velocity) maps of H2CO (3_0,3-2_0,2), CS (J=5-4), and 12CO (J=2-1), and extract position-velocity (PV) diagrams of H2CO and CS along the outflow axis (P.A. 235 deg).  
  > "Moment 1 maps of (a) H 2 CO (3 0 , 3 − 2 0 , 2 ) (b) CS ( J = 5 − 4) and (c) 12 CO ( J = 2 − 1)." (Figure 3 caption); "Figure 4 shows the position velocity diagrams for H 2 CO (3 0 , 3 − 2 0 , 2 ) and CS ( J = 5 − 4) along the outflow axis shown in the left panel of Figure 3a." (2.2. Observation Results); "PV diagrams along the outflow axis (P.A. 235 ◦ )." (Figure 4 caption)
   - parameter: Outflow axis P.A. = 235 deg  
  > "PV diagrams along the outflow axis (P.A. 235 ◦ )." (Figure 4 caption)
   - assumption: Systemic velocity v_sys = 5.24 km s^-1  
  > "Throughout this paper we adopt the systemic velocity of v sys = 5 . 24 km s − 1 , the central value measured by Yen et al. (2017) from the C 18 O ( J =2 − 1) emission line." (2.2. Observation Results)
   - fitting: _not stated_
   - validation: _not stated_
3. **Map ionized gas emission lines from JWST MIRI MRS**: Extract continuum-subtracted intensity maps of [Fe II] 25.99 um, [Fe II] 17.935 um, and [Ne II] 12.81 um and compare with the shell positions.  
  > "Figure 5 show continuum-subtracted intensity of [Fe II ] 25.99 µ m, 17.935 µ m, and [Ne II ] 12.81 µ m." (2.2. Observation Results)
   - software: JWST Calibration Pipeline
   - fitting: _not stated_
   - validation: _not stated_
4. **Simulate underexpanded jet hydrodynamics and compare with observations**: Solve 2D axisymmetric hydrodynamical equations numerically using a second-order accurate finite volume scheme with a flux split method based on an approximate Riemann solution for three parameter sets (Models A, B, C), and measure barrel width and height from velocity profile discontinuities.  
  > "We use the cylindrical coordinates, ( r, φ, z ) and assume the symmetry in the φ -direction ( ∂/∂φ = 0)." (4.1. Model Setting); "We solve the hydrodynamical equations numerically with the second order accurate scheme which can capture a shock wave without spurious oscillations." (4.1. Model Setting); "We measure the width and height of the barrel from the velocity profile." (4.2. Canonical Model)
   - parameter: Grid N_r = 780, N_z = 7560, uniform cell width dr = 0.714 au in main domain (0 <= r <= 557 au, 0 <= z <= 5400 au)  
  > "The spatial resolution, i.e., the numerical cell width is uniform at ∆ r in the main part of the computation domain, 0 ≤ r ≤ N r ∆ r and 0 ≤ z ≤ N z ∆ z , where N r and N z are 780 and 7560, respectively." (4.1. Model Setting); "The spatial resolution is ∆ r = 0 . 714 au in the main part of the computation box of 0 ≤ r ≤ 557 au and 0 ≤ z ≤ 5400 au." (4.2. Canonical Model)
   - parameter: Nozzle radius R = 50 au, initial jet velocity v_jet = 0.845 km s^-1, initial jet density n_0 = 10^7 cm^-3, initial jet temperature T_0 = 2000 K  
  > "First we show model A in which the model parameters are taken to be n 0 = 10 7 cm − 3 , n ∞ = 5 × 10 6 cm − 3 , T 0 = 2000 K, and T ∞ = 100 K." (4.2. Canonical Model); "The jet is assumed to emerge from the circle of R = 50 au with the initial velocity v jet = 0 . 845 km s − 1" (4.2. Canonical Model)
   - parameter: Model A: P_0/P_inf = 40, n_0/n_inf = 2.0, T_inf = 100 K; Model B: P_0/P_inf = 62.5, n_0/n_inf = 3.125, T_inf = 100 K; Model C: P_0/P_inf = 40, n_0/n_inf = 0.4, T_inf = 20 K  
  > "A 40 2.0 2000 K 100 K 0.85 km s − 1 B 62.5 3.125 2000 K 100 K 0.85 km s − 1 C 40 0.4 2000 K 20 K 0.85 km s − 1" (Table 1)
   - assumption: Ideal gas with mean molecular weight mu = 2.3 and specific heat ratio gamma = 7/5; ignore gravity, magnetic field, and radiative cooling/heating  
  > "We ignore gravity, magnetic field, radiative cooling/heating processes for simplicity." (4.1. Model Setting); "The gas is assumed to be an ideal gas having the mean molecular weight µ = 2 . 3 and the specific heat ratio, γ = 7 / 5." (4.1. Model Setting)
   - fitting: _not stated_
   - validation: Code validated on shock tube problem.  
  > "Our numerical code has been proved to reproduce a strong shock wave by solving the shock tube problem." (4.1. Model Setting)

## Software

- **JWST Calibration Pipeline** 1.14.0: Reduction of JWST MIRI imaging data using calibration reference data jwst_1231.pmap  
  > "The imaging data were reduced with JWST calibration pipeline v.1.14.0 (Bushouse et al. 2024) using the calibration reference data jwst 1231.pmap" (2.1. Observation Specifications)
- **JWST Calibration Pipeline** 1.12.5: Reduction of JWST MIRI MRS spectroscopic data using calibration reference data jwst_1183.pmap  
  > "while the spectroscopic data were reduced with JWST calibration pipeline v.1.12.5 (Bushouse et al. 2023) using the calibration reference data jwst 1 183.pmap ." (2.1. Observation Specifications)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Deprojected distance to first shell (d_s1) | 340 | not stated | au | 1 | The first shell is d s1 =340 au (2 ′′ . 06 from the protostar on the sky) while the diameter of the barrel is D w1 = 322 au (2 ′′ . 08). |
| Projected angular distance to first shell | 2.06 | not stated | arcsec | 1 | The first shell is d s1 =340 au (2 ′′ . 06 from the protostar on the sky) while the diameter of the barrel is D w1 = 322 au (2 ′′ . 08). |
| Diameter of first barrel (D_w1) | 322 | not stated | au | 1 | The first shell is d s1 =340 au (2 ′′ . 06 from the protostar on the sky) while the diameter of the barrel is D w1 = 322 au (2 ′′ . 08). |
| Aspect ratio of first shell (d_s1 / D_w1) | 1.05 | not stated | dimensionless | 1 | The aspect ratio, d s1 /D w1 = 1 . 05, gives a clue to estimate the pressure ratio when an underexpanded outflow model is applied. |
| Deprojected distance to second shell (d_s2) | 1060 | not stated | au | 1 | The second shell is d s2 = 1060 au (6 ′′ . 42) away from the protostar and the jet diameter is d w2 = 448 au (2 ′′ . 87). |
| Diameter of second barrel (d_w2) | 448 | not stated | au | 1 | The second shell is d s2 = 1060 au (6 ′′ . 42) away from the protostar and the jet diameter is d w2 = 448 au (2 ′′ . 87). |
| Maximum Mach number before Mach disk in Model A | 4.75 | not stated | dimensionless | 4 | The Mach number, the ratio of the flow velocity and sound speed, reaches 4.75 and drops suddenly at z = 293 au, i.e., just in front of the Mach disk. |
| Distance of Mach disk drop in Model A at t = 1.498e4 yr | 293 | not stated | au | 4 | The Mach number, the ratio of the flow velocity and sound speed, reaches 4.75 and drops suddenly at z = 293 au, i.e., just in front of the Mach disk. |
| Diameter of Mach disk in Model A at t = 7.47e3 yr | 210 | not stated | au | 4 | The diameter of the Mach disk is 210 au at the stage shown in Figure 6. |
| Inferred outflow velocity from thermal energy conversion at T_0 = 2000 K | 7 | not stated | km s^-1 | 4 | Equations (3) and (4) suggest that the outflow is accelerated to ∼ 7 km s − 1 if most of the initial thermal energy is converted into the kinetic energy at T 0 = 2000 K. |

## Qualitative findings

- Semi-periodic velocity variations are found in both the blue and red lobes of the IRAS 15398-3359 primary outflow in H2CO, CS, and 12CO.  
  > "We find a semi-periodic change in the velocity not only in the blue lobe but also in the red lobe." (2.2. Observation Results)
- No significant velocity gradient perpendicular to the outflow axis is observed, indicating that rotation around the outflow axis is insignificant.  
  > "We do not find significant asymmetry with respect to the outflow axis, which means that rotation around the outflow axis is insignificant." (2.2. Observation Results)
- Both blue-shifted and red-shifted velocity components are present in the blue lobe between the protostar and shell 3, indicating diverging/converging flow or reverse flow near the axis.  
  > "Note the red-shifted emission in the blue lobe and the blue-shifted one in the red lobe (see also Figure 2 of Okoda et al. 2025)." (2.2. Observation Results); "Existence of the two components imply either diverging or converging flow along the line of sight" (2.2. Observation Results)
- [Fe II] and [Ne II] emission lines are strong around the protostar and between shells 1 and 2, with a gap near shell 1.  
  > "[Fe II ], [Ne II ], and [Ne II ] emissions are strong around the protostar and between the first and second shells. In other words, they have a gap near the first shell" (2.2. Observation Results)

## Claim tuples

- H: The shell structure in the primary outflow of IRAS 15398-3359 is produced by an underexpanded jet mechanism (adiabatic expansion followed by shock compression at a Mach disk and subsequent re-expansion) rather than episodic accretion outbursts. | E: Compare ALMA molecular line kinematics (H2CO, CS, 12CO) and JWST MIRI infrared maps of IRAS 15398-3359 with 2D axisymmetric hydrodynamic simulations of a high-pressure underexpanded jet. | R: The hydrodynamic model with P_0/P_inf = 40, T_0 = 2000 K, and nozzle radius R = 50 au reproduces the Mach disk at z ~ 300 au, semi-periodic velocity variations, anti-correlation between temperature and velocity, outflow velocities of ~ 7 km s^-1, and reverse flow (v_z < 0) near the axis beyond the Mach disk. | F: A stationary underexpanded jet source can explain the shell structure, velocity variations, temperature-velocity anti-correlation, and reverse flow without invoking short-timescale variability in outflow ejection. | **supported**
- H: The decrease in gas temperature from the protostar to shell 1 is caused by adiabatic expansion rather than radiative cooling. | E: Examine the spatial correlation of H2 temperature, column density, ionized line emission ([Fe II], [Ne II]), and ALMA molecular line Doppler shifts between the protostar and shell 2. | R: As temperature decreases from ~1300 K near the protostar to below 1000 K at shell 1 and column density drops from 10^20 to 10^19.5 cm^-2, the blue-shifted velocity increases steeply, and hot gas reappears between shells 1 and 2. | F: Adiabatic expansion converts thermal energy into kinetic energy, cooling and accelerating the gas before it is shock-heated again at the Mach disk. | **supported**
- H: The ambient gas density around the primary outflow must be lower than the initial outflow gas density for the underexpanded jet to propagate effectively. | E: Compare hydrodynamic simulations with lower ambient density (Models A and B, n_0/n_inf = 2.0 and 3.125) against a cold, dense ambient gas model (Model C, n_0/n_inf = 0.4, T_inf = 20 K). | R: In Model C, where the ambient gas is 2.5 times denser than the injected gas, the outflow is less prominent and propagates substantially more slowly due to the inertia of the ambient gas. | F: The ambient gas density must be low enough relative to the initial jet density, which in IRAS 15398-3359 may have been achieved by earlier outflow generations blowing off surrounding gas. | **supported**

## Reasoning

- Why this data: IRAS 15398-3359 has sub-arcsecond imaging and spectroscopy from both ALMA and JWST showing correlated shell substructures in infrared and radio molecular lines.  
  > "IRAS 15398 − 3359 is one of the sources that both ALMA and JWST have observed to obtain sub-arcsecond images in the radio and infrared wavelengths." (1. INTRODUCTION); "Since the internal structure seen in the infrared emission is correlated with that observed in the radio line emissions, they are likely to have a common origin." (1. INTRODUCTION)
- Why this method: Industrial underexpanded jets are well-studied in aeronautical engineering and naturally produce semi-periodic barrel structures via adiabatic expansion and shock compression, offering an alternative to inconclusive episodic outburst or MHD instability scenarios.  
  > "However, these scenarios are not conclusive. It is worth seeking another possibility as an origin of the internal structure in the primary outflow." (1. INTRODUCTION); "However, industrial jets have been studied much more intensively and the theory is verified by experiments and well established." (3. UNDEREXPANDED JET)
- Alternative: Time variability of outflow activity (four accretion outbursts initiating four outflow episodes, Vazzano et al. 2021) or magnetohydrodynamical instability (Shang et al. 2023).  
  > "A possible origin of the internal structure is time variability of the outflow activity. Vazzano et al. (2021) considered a scenario that IRAS 15398 − 3359 has undergone four accretion outbursts which have initiated four times of outflow activities." (1. INTRODUCTION); "Another possibility is magnetohydrodynamical instability of the outflow (see, e.g., Shang et al. 2023)." (1. INTRODUCTION)
- Alternative: Radiative cooling as the cause of the temperature decrease with distance from the protostar.  
  > "The temperature decrease with the distance from the protostar is not likely to be radiative cooling. If the thermal energy is lost by radiative cooling, we need another heating source for the hot region between shells 1 and 2." (2.2. Observation Results)
- How they decided it was enough: _not stated_
- Limitation (authors): The hydrodynamic model ignores gravity, magnetic fields, and radiative cooling/heating processes.  
  > "We ignore gravity, magnetic field, radiative cooling/heating processes for simplicity." (4.1. Model Setting)
- Limitation (authors): The model assumes the outflow source maintains constant pressure, density, and temperature after a sudden onset and has uniform density in the source region, whereas real outflow activity likely decays.  
  > "We assumed that the outflow source maintains constant pressure, density and temperature after a sudden onset. However, the outflow activity is likely to decay after a short rise." (5. DISCUSSIONS AND SUMMARY); "Uniform density in the source region is also an oversimplification." (5. DISCUSSIONS AND SUMMARY)
- Limitation (authors): JWST temperature measurements and highest-resolution ALMA observations only cover a limited region around the protostar.  
  > "Though JWST observed IRAS 15398 − 3359, the measurement of the gas temperature is limited to a narrow region around the protostar (see Figure 8 of Okoda et al. 2025), i.e., the field of view of the spectroscopic observation." (5. DISCUSSIONS AND SUMMARY); "Similarly, ALMA observed only a limited portion of the primary outflow with the highest observation (Thieme et al. 2023)." (5. DISCUSSIONS AND SUMMARY)
- Caveat (inferred, ours): Radiative cooling by H2 and CO could be significant at T ~ 1000-2000 K and n ~ 10^5-10^7 cm^-3, potentially altering the adiabatic expansion and shock heating behavior.
- Caveat (inferred, ours): Magnetic fields are neglected, yet protostellar jets are widely thought to be magnetocentrifugally launched and magnetically collimated.
- Caveat (inferred, ours): The 2D axisymmetric assumption suppresses 3D non-axisymmetric instabilities in the turbulent post-Mach disk region.
- Caveat (inferred, ours): No synthetic molecular line observations or radiative transfer modeling were performed on the hydrodynamic simulations to directly compare with ALMA Moment 1 and PV diagrams.

## Reproducibility

- Data public (paper): Archival ALMA (2013.1.00879.S, 2018.1.01205.L) and JWST (MAST program 2151, DOI: 10.17909/wv1n-rf97) data are publicly available.  
  > "Our analysis is based on the archival data of ALMA and JWST." (2.1. Observation Specifications); "The specific observations analyzed can be accessed via DOI: 10.17909/wv1n-rf97 and Salyk et al. (2024)." (ACKNOWLEDGEMENTS); "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00879.S and ADS/JAO.ALMA#2018.1.01205.L." (ACKNOWLEDGEMENTS)
- Products in archive: _not stated_
- Missing: Custom hydrodynamic simulation code is not publicly released
- Missing: ALMA data reduction and imaging parameters are not in this paper (must be retrieved from Okoda et al. 2021a, 2023, 2025 and Yen et al. 2017)
- Missing: Exact intensity clipping thresholds for ALMA Moment 1 maps and extraction width for PV diagrams
- Data volume (inferred): Tens of GB for reduced ALMA spectral cubes and JWST MIRI MRS cubes; several hundred GB if re-reducing raw ALMA visibilities from 2018.1.01205.L and 2013.1.00879.S.
- Score (inferred): 55/5, Archival ALMA and JWST datasets are clearly identified with project codes and DOIs, and the 2D hydrodynamic model equations, grid setup, boundary conditions, and parameter tables are well specified. However, the custom hydro code is not released, and all ALMA data reduction/imaging details are deferred to earlier companion papers.
- Rediscovery candidate: no, The primary new contribution is a qualitative and semi-quantitative comparison with a custom 2D hydrodynamic simulation rather than quantitative measurements derived directly from the ALMA data.

## Links

- Method: Hanawa & Matsumoto (2021); Hanawa et al. (2022, 2024) (Describes the numerical hydrodynamic code (second-order finite volume with approximate Riemann flux splitting) used for the simulations.)
- Method: Crist et al. (1966); Addy (1981); Franquet et al. (2015) (Analytical and empirical scaling laws for Mach disk distance and diameter in underexpanded jets.)
- Companion: Okoda et al. (2025) (Provides the JWST MIRI composite image, H2 temperature/column density maps, and ALMA data reduction details used directly in this study.)
- Companion: Okoda et al. (2021a); Okoda et al. (2023) (Describes the ALMA FAUST observations of H2CO and CS in IRAS 15398-3359.)
- Companion: Yang et al. (2022) (JWST CORINOS overview paper presenting the MIRI observations of IRAS 15398-3359.)
- Companion: Yen et al. (2017) (Describes the ALMA 2013.1.00879.S 12CO observations and systemic velocity measurement.)
- Related: FAUST (Fifty AU Study of the chemistry in the disk/envelope system of Solar-like protostars)
- Related: CORINOS (JWST program 2151)

## Checks

```json
{
 "quotes": 92,
 "quotes_ok": 92,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 5,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 83,
  "stated": 40,
  "rate": 0.482
 },
 "evidence_ok": true
}
```
