# The Disc Miner. II. Revealing gas substructures and kinematic signatures from planet-disc interaction through line profile analysis

`2023A&A...674A.113I` | Astronomy and Astrophysics 2023 | first author: Izquierdo, A. F. | arXiv: 2304.03607 | DOI: 10.1051/0004-6361/202245425

Card schema 1.0 | model gemini-4-argon | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks
- Question: Identify potential signatures from planet-disc interaction and gas substructures in the circumstellar discs around MWC 480, HD 163296, AS 209, IM Lup, and GM Aur through line profile analysis of CO isotopologues.  
  > "The aim of this work is to identify potential signatures from planet-disc interaction in the circumstellar discs around MWC 480, HD 163296, AS 209, IM Lup, and GM Aur, through the study of molecular lines observed as part of the ALMA large program MAPS." (Abstract)
- Target **MWC 480**: coordinates _not stated_; z/distance 162.0 pc  
  > "MWC 480 ($162.0$ pc)" (Supporting tables); distance from _not stated_
- Target **HD 163296**: coordinates _not stated_; z/distance 101.5 pc  
  > "HD 163296 ($101.5$ pc)" (Supporting tables); distance from _not stated_
- Target **AS 209**: coordinates _not stated_; z/distance 121.0 pc  
  > "AS 209 ($121.0$ pc)" (Supporting tables); distance from _not stated_
- Target **IM Lup**: coordinates _not stated_; z/distance 158.0 pc  
  > "IM Lup ($158.0$ pc)" (Supporting tables); distance from _not stated_
- Target **GM Aur**: coordinates _not stated_; z/distance 159.0 pc  
  > "GM Aur ($159.0$ pc)" (Supporting tables); distance from _not stated_

## Data provenance

- ALMA projects: 2018.1.01055.L
- bands: _not stated_
- frequencies and spectral setup: 0.2 km s^-1 velocity channel spacing  
  > "our analysis focuses on the three brightest CO isotopologues, $^{12}$CO, $^{13}$CO and C$^{18}$O, in the $J=2-1$ rotational transition, observed at an angular resolution of $0.15''$, and a velocity channel spacing of $0.2$ km s$^{-1}$." (Observations and models)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.15''  
  > "our analysis focuses on the three brightest CO isotopologues, $^{12}$CO, $^{13}$CO and C$^{18}$O, in the $J=2-1$ rotational transition, observed at an angular resolution of $0.15''$, and a velocity channel spacing of $0.2$ km s$^{-1}$." (Observations and models)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: publicly available archival data from ALMA large program MAPS  
  > "In this work we make use of publicly available data from molecular line observations of five protoplanetary discs around the young stars MWC 480, HD 163296, AS 209, IM Lup, and GM Aur, as part of the ALMA large program MAPS (cite: oberg+2021)." (Observations and models); "In this work we apply the DISCMINER modelling and analysis techniques on high angular and velocity resolution archival data of $^{12}$CO, $^{13}$CO, and C$^{18}$O $J=2-1$ line emission from five discs around the young stars MWC 480, HD 163296, AS 209, IM Lup, and GM Aur, observed as part of the ALMA large program MAPS (cite: oberg+2021)." (Conclusions)
- Line: 12CO J=2-1 (not stated)
- Line: 13CO J=2-1 (not stated)
- Line: C18O J=2-1 (not stated)
- External data: JvM-corrected images with robust=0.5 from the MAPS survey  
  > "We use the JvM-corrected images with a robust parameter of 0.5 (cite: czekala+2021)" (Observations and models) [from (cite: oberg+2021); (cite: czekala+2021)]
- External data: Non-parametric 12CO emitting layer for MWC 480  
  > "For this experiment, we fix the $^{12}$CO model surface to the non-parametric emitting layer extracted by (cite: paneque+2022), and re-run DISCMINER to find a new set of parameters for the remaining attributes summarised in Table 1." (Extended velocity and line width perturbations) [from (cite: paneque+2022)]
- External data: Millimetre continuum disc inclination for MWC 480  
  > "For better comparison, we also fix the disc inclination in both the smooth and irregular-surface model to the value found by (cite: liu+2019) from mm continuum modelling." (Extended velocity and line width perturbations) [from (cite: liu+2019)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: JvM-corrected images from MAPS data release  
  > "In this work we make use of publicly available data from molecular line observations of five protoplanetary discs around the young stars MWC 480, HD 163296, AS 209, IM Lup, and GM Aur, as part of the ALMA large program MAPS (cite: oberg+2021)." (Observations and models); "We use the JvM-corrected images with a robust parameter of 0.5 (cite: czekala+2021)" (Observations and models)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: 0.5  
  > "We use the JvM-corrected images with a robust parameter of 0.5 (cite: czekala+2021)" (Observations and models)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: both continuum-subtracted and non-continuum-subtracted cubes tested  
  > "To assess the effect of continuum subtraction on these velocity profiles, we performed the same analysis on intensity cubes of all three CO isotopologues for MWC 480 without continuum subtraction and, as illustrated in Fig. 36, we found no differences with respect to the continuum-subtracted cubes that could affect any of the results summarised in this Section." (Azimuthal and meridional velocity flows)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.15''  
  > "our analysis focuses on the three brightest CO isotopologues, $^{12}$CO, $^{13}$CO and C$^{18}$O, in the $J=2-1$ rotational transition, observed at an angular resolution of $0.15''$, and a velocity channel spacing of $0.2$ km s$^{-1}$." (Observations and models)
- final rms: _not stated_

### Inherited from earlier work

- MAPS JvM-corrected image cubes with robust = 0.5  
  > "We use the JvM-corrected images with a robust parameter of 0.5 (cite: czekala+2021)" (Observations and models) [from (cite: oberg+2021); (cite: czekala+2021)]
- DISCMINER line profile analysis techniques, generalised bell kernel, and clustering algorithm for localised perturbation detection  
  > "In this article, we employ the line profile analysis techniques developed in (cite: izquierdo+2021), implemented in the DISCMINER package, to search for gas substructures and kinematic signatures that may point to, or refute, the presence of embedded planets in the discs observed by the ALMA large program MAPS." (Introduction); "In (cite: izquierdo+2022), we applied this technique on DSHARP data (cite: andrews+2018) of the $^{12}$CO disc around HD 163296, finding two significantly localised perturbations possibly driven by massive planets embedded in the disc at wide orbits: one at 94 au, referred to as P94, and another at 261 au, or P261." (Detections in the disc of HD 163296: Velocity) [from (cite: izquierdo+2021); (cite: izquierdo+2022)]

### Not stated but needed to reproduce (our reading)

- MCMC setup details for EMCEE (number of walkers, burn-in steps, total steps, priors, likelihood noise estimate)
- Some columns in the Supporting Tables (e.g., inclination i, stellar mass M_*, z_0, I_0, L_w0, L_s0) are missing or truncated in the text conversion
- Number of clusters k chosen for the K-means clustering algorithm

## Analysis recipe

1. **Model channel-by-channel molecular line intensity cubes**: Fit parametric 3D channel-map models to the observed data cubes using a generalised bell function line profile kernel for upper and lower emission surfaces  
  > "DISCMINER aims to reproduce the channel-by-channel intensity of molecular line emission from discs by modelling various types of parameters which can be classified in four groups" (Model parameters and attributes); "These parameters are then assembled together in a two-component line profile kernel (one per emission surface), or in a single-component profile (if the lower surface is not resolved), to compute the model intensity, $I_m$, as a function of the disc cylindrical coordinates, $(R,z)$, and the velocity channel, $\upsilon_{\rm ch}$." (Model parameters and attributes)
   - software: DISCMINER, EMCEE
   - parameter: Orientation (i, PA, x_c, y_c), Velocity (M_*, v_sys), Upper and Lower surface (z_0, p, R_t, q), Peak intensity (I_0, p, q), Line width (L_w0, p, q), Line slope (L_s0, p); normalisation D_0=100 au  
  > "$G$ is the gravitational constant; $D_0=100$ au is a normalisation factor." (Table 1)
   - parameter: For AS 209 12CO, asymmetric intensity normalisation: 0.65 I_0 for -80 deg < phi < 80 deg, and 1.25 I_0 otherwise  
  > "we used a different intensity normalisation factor for each side of the disc: $0.65I_0$ for $-80^\circ<\phi<80^\circ$, and $1.25I_0$ otherwise" (Data versus model channel maps)
   - assumption: Keplerian rotation with vertical differential rotation sustained by balance of forces in the z-direction  
  > "Thus, the model rotation velocity is assumed Keplerian for all discs, with vertical differential rotation sustained by balance of forces in the $z-$direction." (Model parameters and attributes)
   - assumption: Highest intensity between upper and lower surface components taken on each pixel and velocity channel  
  > "To combine the contribution of the upper and lower emission surfaces to the total line profile, we take the highest intensity between the two components on each pixel and velocity channel." (Model parameters and attributes)
   - assumption: Axisymmetric intensity fields for all model channels except 12CO of AS 209  
  > "We assume axisymmetric intensity fields for all model channels except for the $^{12}$CO disc of AS 209." (Data versus model channel maps)
   - fitting: MCMC random sampler EMCEE coupled to DISCMINER  
  > "Finally, to find best-fit model channel maps to the data we couple DISCMINER with a Markov chain Monte Carlo (MCMC) random sampler, EMCEE (cite: foreman+2013), which walks over a vast range of parameters to determine a subset of them that best reproduces the projected intensity of the input datacube on each velocity channel." (Model parameters and attributes)
   - validation: Tested runs with fixed continuum inclination; tested non-parametric irregular emission surface on MWC 480; tested symmetric vs asymmetric intensity model on AS 209  
  > "To explore the influence of disc inclination and different tracers on the retrieved dynamical mass, we also made runs assuming disc inclination fixed at the continuum value for all sources and tracers, and reported the obtained parameters in the same tables." (Model parameters and attributes); "For this experiment, we fix the $^{12}$CO model surface to the non-parametric emitting layer extracted by (cite: paneque+2022), and re-run DISCMINER to find a new set of parameters for the remaining attributes summarised in Table 1." (Extended velocity and line width perturbations)
2. **Extract line profile observables and compute deprojected residual maps**: Fit Gaussian kernels to both data and model line profiles to extract peak intensity, line width, and centroid velocity; subtract model from data and deproject onto the disc reference frame using retrieved vertical structure and orientation  
  > "The three observables are extracted from Gaussian kernels fitted to both the data and model line profiles, and compared against each other to produce residual maps, as illustrated in Figure 3 for the $^{12}$CO disc around MWC 480." (Line profile observables to compare data and models); "Using information of the disc vertical structure and orientation retrieved by DISCMINER, these line profile observables and their residuals can then be deprojected onto the disc reference frame for quantitative studies of the physical location, extent, and magnitude of the retrieved signatures in the gas disc." (Line profile observables to compare data and models)
   - software: DISCMINER
   - parameter: Peak intensity, line width, and centroid velocity  
  > "We employ three observables from line intensity profiles, (i) peak intensity, (ii) line width, and (iii) centroid velocity, to search for gas surface density, temperature and velocity substructures in all discs and tracers considered in this work." (Line profile observables to compare data and models)
   - fitting: Gaussian kernel fits to line profiles  
  > "The three observables are extracted from Gaussian kernels fitted to both the data and model line profiles, and compared against each other to produce residual maps, as illustrated in Figure 3 for the $^{12}$CO disc around MWC 480." (Line profile observables to compare data and models)
   - validation: _not stated_
3. **Detect localised velocity and line width perturbations via clustering**: Fold residual maps across the disc minor axis, divide disc radial extent into annuli, extract peak residuals per annulus, group peak residuals into radial and azimuthal clusters using K-means, and identify significant clusters  
  > "To do so, we first split the disc radial extent into annuli with a width of a quarter of the beam size. Next, in each annulus, we perform an azimuthal scan to extract the peak residual and take record of its magnitude and azimuthal location. Finally, using a K-means algorithm, we group these peak residuals into clusters along both the radial and azimuthal coordinates of the disc." (Localised velocity and line width perturbations)
   - software: DISCMINER
   - parameter: Annulus width = 1/4 of the beam size; significance threshold = 3 sigma of spectral variance of peak residuals  
  > "To do so, we first split the disc radial extent into annuli with a width of a quarter of the beam size." (Localised velocity and line width perturbations); "A cluster is classified as significant when the spectral variance of the peak residuals within the cluster is above a threshold of 3$\sigma$ set by the variances of the other clusters." (Localised velocity and line width perturbations)
   - fitting: K-means clustering algorithm  
  > "Finally, using a K-means algorithm, we group these peak residuals into clusters along both the radial and azimuthal coordinates of the disc." (Localised velocity and line width perturbations)
   - validation: Comparison of detections across three CO isotopologues and with previous DSHARP detections  
  > "Here, very similar results are obtained if the same analysis is carried out on the MAPS observations of this disc in the three CO isotopologues of interest." (Detections in the disc of HD 163296: Velocity)
4. **Decompose velocity residuals into azimuthal and vertical (meridional) velocity components and radial profiles**: Compute azimuthal averages (over 2pi or symmetric section psi) of standard velocity residuals to obtain vertical velocity v_z, and of absolute velocity residuals to obtain azimuthal velocity perturbation Delta v_phi, alongside azimuthally averaged radial profiles of peak intensity and line width residuals  
  > "Now, assuming that the three-dimensional components of the velocity field are axisymmetric, one can obtain the azimuthal and vertical components on each radius by computing azimuthal averages of these absolute and standard velocity residuals, respectively." (Decomposition method to extract azimuthal and meridional velocities); "it is possible to readily obtain an estimate of the azimuthal and vertical components of the velocity perturbation field by computing azimuthal averages of different kinds of velocity residual maps." (Azimuthal and meridional velocity flows)
   - software: DISCMINER
   - parameter: Standard residuals (v_0,d - v_0,m) and absolute residuals (|v_0,d - v_sys,m| - |v_0,m - v_sys,m|)  
  > "While the former consists of a direct subtraction of the model centroid velocities to those retrieved from the data, $\upsilon_{0, d} - \upsilon_{0, m}$ (as in e.g. Fig. 5), the latter is the difference between the absolute values referred to the model systemic velocity, $|\upsilon_{0, d} - \upsilon_{{\rm sys}, m}| - |\upsilon_{0, m} - \upsilon_{{\rm sys}, m}|$." (Decomposition method to extract azimuthal and meridional velocities)
   - assumption: Three-dimensional components of the velocity field are axisymmetric and line-of-sight velocities are dominated by azimuthal velocities  
  > "Now, assuming that the three-dimensional components of the velocity field are axisymmetric, one can obtain the azimuthal and vertical components on each radius by computing azimuthal averages of these absolute and standard velocity residuals, respectively." (Decomposition method to extract azimuthal and meridional velocities); "Now, it is useful to note that under the reasonable assumption that the observed line-of-sight velocities are dominated by azimuthal velocities, the absolute value of the data and model velocities can also be written as" (Azimuthal average of absolute velocity residuals)
   - fitting: _not stated_
   - validation: Tested on cubes with and without continuum subtraction for MWC 480; computed quadrant-by-quadrant azimuthal averages to assess non-axisymmetric variations  
  > "To assess the effect of continuum subtraction on these velocity profiles, we performed the same analysis on intensity cubes of all three CO isotopologues for MWC 480 without continuum subtraction and, as illustrated in Fig. 36, we found no differences with respect to the continuum-subtracted cubes that could affect any of the results summarised in this Section." (Azimuthal and meridional velocity flows); "This is illustrated in Figure 16 for the disc of MWC 480, where we show azimuthal averages of the three residual observables obtained for $^{12}$CO, in the four quadrants delimited by the disc main axes as projected in the sky." (Non-axisymmetric variations in the radial profiles of the disc around MWC 480)

## Software

- **DISCMINER** : Channel-map modelling, extraction of line profile observables, deprojection, velocity decomposition, and clustering analysis  
  > "The majority of the analysis presented in this paper is performed with the DISCMINER channel-map modelling tool, whose main capabilities were introduced in and first applied to actual data in (cite: izquierdo+2022) with the aim of looking for planetary signatures in the kinematics of the disc around HD 163296 using $^{12}$CO $J=2-1$ line observations." (Discminer models)
- **EMCEE** : Markov chain Monte Carlo random sampling to find best-fit model channel map parameters  
  > "Finally, to find best-fit model channel maps to the data we couple DISCMINER with a Markov chain Monte Carlo (MCMC) random sampler, EMCEE (cite: foreman+2013), which walks over a vast range of parameters to determine a subset of them that best reproduces the projected intensity of the input datacube on each velocity channel." (Model parameters and attributes)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HD 163296 12CO localised velocity perturbation (P94) orbital radius | 93 | not stated | au | 3 | The $^{12}$CO perturbation, detected at an orbital radius of $R=93$ au and an azimuth of $\phi=51^\circ$ in the disc reference frame, is in excellent agreement with the P94 perturbation found by (cite: izquierdo+2022). |
| HD 163296 12CO localised velocity perturbation (P94) azimuth | 51 | not stated | deg | 3 | The $^{12}$CO perturbation, detected at an orbital radius of $R=93$ au and an azimuth of $\phi=51^\circ$ in the disc reference frame, is in excellent agreement with the P94 perturbation found by (cite: izquierdo+2022). |
| HD 163296 12CO localised velocity perturbation (P94) folded magnitude | ~0.4 | not stated | km s^-1 | 3 | While the $^{12}$CO perturbation yields a folded magnitude of $\sim\!0.4$ km s$^{-1}$, the $^{13}$CO perturbation peaks at $\sim\!0.3$ km s$^{-1}$ velocities. |
| HD 163296 13CO localised velocity perturbation (P81) orbital radius | 81 | not stated | au | 3 | The $^{13}$CO perturbation, or P81 hereafter, is detected at $R=81$ au and $\phi=70^\circ$, namely interior to the D86 dust gap, and centred at an azimuth closer to the disc minor axis than that of the P94 perturbation. |
| HD 163296 13CO localised velocity perturbation (P81) azimuth | 70 | not stated | deg | 3 | The $^{13}$CO perturbation, or P81 hereafter, is detected at $R=81$ au and $\phi=70^\circ$, namely interior to the D86 dust gap, and centred at an azimuth closer to the disc minor axis than that of the P94 perturbation. |
| HD 163296 13CO localised velocity perturbation (P81) folded magnitude | ~0.3 | not stated | km s^-1 | 3 | While the $^{12}$CO perturbation yields a folded magnitude of $\sim\!0.4$ km s$^{-1}$, the $^{13}$CO perturbation peaks at $\sim\!0.3$ km s$^{-1}$ velocities. |
| HD 163296 13CO localised line width perturbation orbital radius | 79 | not stated | au | 3 | The centre of the $^{13}$CO perturbation is detected at $R=79$ au, $\phi=74^\circ$, and that of the C$^{18}$O perturbation is detected at $R=86$ au, $\phi=75^\circ$. |
| HD 163296 13CO localised line width perturbation azimuth | 74 | not stated | deg | 3 | The centre of the $^{13}$CO perturbation is detected at $R=79$ au, $\phi=74^\circ$, and that of the C$^{18}$O perturbation is detected at $R=86$ au, $\phi=75^\circ$. |
| HD 163296 C18O localised line width perturbation orbital radius | 86 | not stated | au | 3 | The centre of the $^{13}$CO perturbation is detected at $R=79$ au, $\phi=74^\circ$, and that of the C$^{18}$O perturbation is detected at $R=86$ au, $\phi=75^\circ$. |
| HD 163296 C18O localised line width perturbation azimuth | 75 | not stated | deg | 3 | The centre of the $^{13}$CO perturbation is detected at $R=79$ au, $\phi=74^\circ$, and that of the C$^{18}$O perturbation is detected at $R=86$ au, $\phi=75^\circ$. |
| MWC 480 planet candidate orbital radius | 245 | not stated | au | 2 | In MWC 480, we identified non-axisymmetric line width enhancements around the radial separation of candidate planet-driven buoyancy spirals, which we used to narrow the location of the possible planet to an orbital radius of $R=245$ au and $\rm{PA}=193^\circ$, at a projected distance of $1.33"$ from the star.; Considering this and the fact that the vertical velocity signatures are in good agreement with those expected for a planet-driven buoyancy spiral, we propose a planet candidate in the disc of MWC 480 at an orbital radius of $R=245$ au, namely at the radial location proposed by (cite: teague+2021), but at an azimuth of $\phi=-128^\circ$, where the peak in $^{12}$CO line width residuals is found. |
| MWC 480 planet candidate disc azimuth | -128 | not stated | deg | 2 | Considering this and the fact that the vertical velocity signatures are in good agreement with those expected for a planet-driven buoyancy spiral, we propose a planet candidate in the disc of MWC 480 at an orbital radius of $R=245$ au, namely at the radial location proposed by (cite: teague+2021), but at an azimuth of $\phi=-128^\circ$, where the peak in $^{12}$CO line width residuals is found. |
| MWC 480 planet candidate projected distance | 1.33 | not stated | arcsec | 2 | In MWC 480, we identified non-axisymmetric line width enhancements around the radial separation of candidate planet-driven buoyancy spirals, which we used to narrow the location of the possible planet to an orbital radius of $R=245$ au and $\rm{PA}=193^\circ$, at a projected distance of $1.33"$ from the star. |
| AS 209 peak 12CO line width enhancement orbital radius | 210 | not stated | au | 2 | In the disc of AS 209, we found excess $^{12}$CO line widths centred at $R=210$ au, $\rm{PA}=151^\circ$, at a projected distance of $1.44"$, spanning around the immediate vicinity of a circumplanetary disc candidate proposed previously, which further supports its presence. |
| AS 209 peak 12CO line width enhancement projected distance | 1.44 | not stated | arcsec | 2 | In the disc of AS 209, we found excess $^{12}$CO line widths centred at $R=210$ au, $\rm{PA}=151^\circ$, at a projected distance of $1.44"$, spanning around the immediate vicinity of a circumplanetary disc candidate proposed previously, which further supports its presence. |
| MWC 480 12CO systemic velocity | 5.10 | not stated | km s^-1 | 1 | $5.10$ $[5.10]$ |
| HD 163296 12CO systemic velocity | 5.77 | not stated | km s^-1 | 1 | $5.77$ $[5.77]$ |
| AS 209 12CO systemic velocity | 4.64 | not stated | km s^-1 | 1 | $4.64$ $[4.63]$ |
| IM Lup 12CO systemic velocity | 4.52 | not stated | km s^-1 | 1 | $4.52$ $[4.52]$ |
| GM Aur 12CO systemic velocity | 5.63 | not stated | km s^-1 | 1 | $5.63$ $[5.63]$ |

## Qualitative findings

- Convincing evidence for four giant planets at wide orbits across three discs: two around HD 163296, one in MWC 480, and one in AS 209.  
  > "We find convincing evidence for the presence of four giant planets located at wide orbits in three of the discs in the sample: two around HD 163296, one in MWC 480, and one in AS 209." (Abstract)
- No clear localised or extended kinematic signatures associated with massive planets or gravitational instabilities are found in IM Lup or GM Aur.  
  > "We report no clear localised or extended kinematic signatures in the discs of IM Lup or GM Aur that could be associated with the presence of planets or gravitational instabilities." (Abstract)
- Nine out of eleven millimetre dust continuum rings in the sample co-locate with gas pressure bumps traced by kinematic modulations.  
  > "Finally, we show that nine out of eleven millimetre dust continuum rings in the sample are co-located with pressure bumps traced by kinematic modulations, indicating that aerodynamic confinement via pressure traps is a common mechanism for the formation of dust substructures in these discs." (Abstract)
- Pressure minima exhibit line width minima counterparts in optically thick emission, making them robust tracers of gas surface density gaps when combined with azimuthal velocity flows.  
  > "On the other hand, we demonstrate that pressure minima exhibit line width minima counterparts in optically thick emission, making them robust tracers of gaps in the gas surface density when analysed together with azimuthal velocity flows." (Abstract)

## Claim tuples

- H: Embedded giant planets produce detectable localised and extended perturbations in both velocity and line width across multiple CO isotopologues. | E: Fit DISCMINER Keplerian channel-map models to 12CO, 13CO, and C18O J=2-1 cubes for five MAPS discs, extract centroid velocity and line width residuals, and apply a K-means clustering algorithm to folded residual maps. | R: Localised velocity perturbations detected in HD 163296 in 12CO (R=93 au, phi=51 deg) and 13CO (R=81 au, phi=70 deg) alongside localised line width perturbations in 13CO (R=79 au, phi=74 deg) and C18O (R=86 au, phi=75 deg); non-axisymmetric line width enhancements found in MWC 480 (peaking at R=245 au, phi=-128 deg) and AS 209 (peaking at R=210 au, PA=151 deg). | F: Line widths are powerful tracers of planet-forming sites alongside velocity perturbations, confirming candidate P94 in HD 163296 across multiple scale heights and supporting planet candidates in MWC 480 and AS 209. | **supported**
- H: The strong intensity kink observed in the south of the AS 209 disc around R~200 au originates from a localised planet-driven kinematic perturbation. | E: Inspect deprojected velocity residual maps and compare isovelocity contours from data and DISCMINER models against decomposed vertical velocity flows in AS 209. | R: No localised velocity perturbation is detected near the CPD candidate at R=203 au; instead, an upward meridional flow at R~190 au extends across the entire azimuth of the disc. | F: The kink-like feature in 12CO channel maps of AS 209 does not originate from a localised kinematic perturbation, but is driven by an azimuthally extended upward meridional flow. | **refuted**
- H: Millimetre dust continuum rings in protoplanetary discs are formed by aerodynamic confinement in gas pressure traps. | E: Decompose velocity residuals into azimuthal velocity perturbation profiles to locate pressure maxima (negative radial gradients of azimuthal velocity) and compare their radial locations to millimetre dust continuum rings. | R: At least nine out of eleven millimetre dust continuum rings in the sample co-locate with gas pressure bumps traced by negative azimuthal velocity gradients. | F: Aerodynamic confinement via gas pressure traps is a common mechanism for the formation of millimetre dust substructures in these discs. | **supported**
- H: Pressure minima in discs are dominated by surface density gaps that produce line width minima in optically thick tracers. | E: Compare azimuthally averaged radial profiles of azimuthal velocity gradients, line width residuals, and peak intensity (brightness temperature) residuals across 12CO, 13CO, and C18O. | R: Positive gradients in azimuthal velocity (pressure minima) co-locate with line width minima in all discs, especially in 12CO and 13CO, whereas brightness temperature peaks and troughs show no clear correlation. | F: Simultaneous detection of positive azimuthal velocity gradients and line width minima in optically thick emission robustly traces gas surface density gaps. | **supported**

## Reasoning

- Why this data: MAPS observations provide unprecedented angular (0.15'') and spectral (0.2 km s^-1) resolution together with high sensitivity across three bright CO isotopologues to probe 3D disc kinematics and morphology.  
  > "The unprecedented angular and spectral resolution together with the high sensitivity of these observations allow us to apply dedicated state-of-the-art techniques to study the kinematics and morphology of these objects with exquisite precision." (Observations and models)
- Why this method: DISCMINER models both upper and lower emission surfaces simultaneously with a generalised bell line profile kernel, preventing systematic velocity centroid shifts caused by the lower surface and allowing full line profiles to be fitted with high velocity precision.  
  > "As explained in , this kernel performs better than a Gaussian at reproducing optically thick lines which are flat at the top and decay rapidly towards the wings, as is usually the case for $^{12}$CO and $^{13}$CO lines (cite: beckwith+1993), but at the same time it is flexible enough to account for optically thinner lines if needed." (Model parameters and attributes); "The inclusion of the lower surface contribution to the line profiles of our model aims to partly alleviate this effect and enables us to consider the bulk of velocity channels to measure the line centroid shift in velocity with little loss of precision." (Upper and lower emission surfaces)
- Alternative: Using non-parametric irregular emission surfaces (rejected because it leads to higher intensity and velocity residuals and quadruple velocity residual patterns modulated by velocity perturbations).  
  > "As illustrated in Figure 31, we find that using an irregular surface leads to higher intensity and velocity residuals overall." (Extended velocity and line width perturbations); "Hence, we only consider smooth parametric surfaces found by DISCMINER for the rest of the analysis." (Extended velocity and line width perturbations)
- Alternative: Measuring velocities only on or around the line peak to isolate the upper surface (rejected because it loses velocity precision and struggles when emission is optically thin or marginally optically thick).  
  > "To overcome this, at the cost of velocity precision, some methods measure velocities on, or around, the peak of the line profile to account primarily for the centroid velocity of the disc upper surface (cite: teague+2018_bettermoments; teague+2021). However, when the emission is optically thin, or just marginally optically thick, these methods struggle at distinguishing between upper and lower surfaces because the intensity contrast between both is generally small in these scenarios." (Upper and lower emission surfaces)
- Alternative: Modelling gas mass and radial pressure profile steepness directly in the background DISCMINER velocity model (rejected as computationally expensive and out of scope).  
  > "Although accountable by DISCMINER, modelling these parameters is computationally expensive and out of the scope of this paper. Thus, the model rotation velocity is assumed Keplerian for all discs, with vertical differential rotation sustained by balance of forces in the $z-$direction." (Model parameters and attributes)
- How they decided it was enough: _not stated_
- Limitation (authors): Strong correlation between disc inclination and stellar mass leads to ~5-10% differences in M_* for inclination variations within ~1-4 deg.  
  > "We note that differences in $M_\star$ range between $\sim\!5-10$% for variations in inclination within $\sim\!1-4^\circ$, which is a consequence of the strong correlation between these two parameters (cite: izquierdo+2022)." (Model parameters and attributes)
- Limitation (authors): Velocity decomposition into azimuthal and vertical components assumes axisymmetry, which breaks in the presence of non-axisymmetric features like spirals and can impact the retrieved velocity amplitudes.  
  > "As a final note, we highlight that velocity perturbations to the Keplerian rotation are not necessarily axisymmetric as originally imposed by this type of decomposition methods (cite: teague+2019nat)." (Decomposition method to extract azimuthal and meridional velocities); "However, despite the fact that such features would impact the amplitude of the velocity components retrieved by this method, other less-affected observable quantities such as the radial location of velocity peaks, troughs, and gradients, can still provide invaluable clues about the presence and direction of azimuthal and vertical flows of material, generally interpreted as due to variations in the disc pressure structure, as explained and illustrated in Sect. 4." (Decomposition method to extract azimuthal and meridional velocities)
- Limitation (authors): Strong diffuse emission in-between 12CO layers in IM Lup is not accounted for by the DISCMINER model, so velocity perturbations near its projected minor axis may be unphysical.  
  > "However, due to the strong diffuse emission in-between $^{12}$CO layers not accounted by the DISCMINER model, these signatures may not represent physical disturbances and should be interpreted with care." (Extended velocity and line width perturbations)
- Limitation (authors): Sample size of five discs is not statistically representative.  
  > "Although not statistically representative, a ratio of four massive planets found at large orbital radii in five protoplanetary discs is noteworthy." (Giant planets around HD 163296, MWC 480, AS 209)
- Caveat (inferred, ours): Fitting Gaussian kernels to extract observables from model and data profiles when the underlying optically thick model profiles are flat-topped generalised bell functions could introduce systematic biases in line width and centroid estimates where optical depth varies rapidly.
- Caveat (inferred, ours): K-means clustering requires pre-specifying the number of clusters, which is not stated and could affect the 3-sigma cluster variance threshold used to claim significant detections.

## Reproducibility

- Data public (paper): Publicly available on https://alma-maps.info/data.html  
  > "In this work we make use of publicly available data from molecular line observations of five protoplanetary discs around the young stars MWC 480, HD 163296, AS 209, IM Lup, and GM Aur, as part of the ALMA large program MAPS (cite: oberg+2021)." (Observations and models); "Publicly available on https://alma-maps.info/data.html" (Footnotes)
- Products in archive: JvM-corrected images with robust=0.5 publicly available on MAPS website  
  > "We use the JvM-corrected images with a robust parameter of 0.5 (cite: czekala+2021)" (Observations and models); "Publicly available on https://alma-maps.info/data.html" (Footnotes)
- Code: DISCMINER is publicly available on https://github.com/andizq/discminer  
  > "Publicly available on https://github.com/andizq/discminer" (Footnotes)
- Missing: Number of clusters k and exact radial boundaries used in the K-means clustering algorithm
- Missing: Exact azimuthal masking angles psi used for IM Lup and GM Aur velocity decompositions
- Missing: MCMC hyperparameters (number of walkers, steps, burn-in, parameter prior bounds)
- Data volume (inferred): ~10-30 GB (15 high-resolution JvM-corrected spectral cubes: 5 discs x 3 CO isotopologues at 0.15'' resolution and 0.2 km/s channel spacing)
- Score (inferred): 9/5, Both the input JvM-corrected MAPS image cubes and the DISCMINER analysis software are publicly available online, equations and functional forms for the model attributes and velocity decomposition are explicitly derived, and best-fit parameters are tabulated.
- Rediscovery candidate: yes, Public MAPS cubes and public DISCMINER code allow direct end-to-end reproduction of the best-fit disc parameters, deprojected residual maps, velocity decompositions, and localised planet perturbation coordinates.

## Links

- Method: (cite: izquierdo+2021) (Introduced the DISCMINER channel-map modelling framework, generalised bell kernel, and clustering algorithm for planet detection.)
- Method: (cite: izquierdo+2022) (First application of DISCMINER to observational ALMA data (HD 163296 DSHARP 12CO).)
- Method: (cite: czekala+2021) (Describes the imaging and JvM correction procedure for the MAPS spectral line data cubes.)
- Method: (cite: foreman+2013) (Reference for the EMCEE Markov chain Monte Carlo ensemble sampler.)
- Companion: (cite: izquierdo+2021) (Paper I of The Disc Miner series.)
- Companion: (cite: oberg+2021) (Overview paper of the ALMA MAPS Large Program providing the data.)
- Related: MAPS (Molecules with ALMA at Planet-forming Scales)
- Related: DSHARP

## Checks

```json
{
 "quotes": 103,
 "quotes_ok": 103,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 31,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2013.1.00601.S",
  "2016.1.00484.L"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 20,
 "numeric_problems": 0,
 "fill": {
  "facts": 95,
  "stated": 55,
  "rate": 0.579
 },
 "evidence_ok": true
}
```
