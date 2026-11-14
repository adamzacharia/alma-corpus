# Decoding the molecular torus of NGC 1068: Insights into its structure and kinematics from high-resolution ALMA observations

`2025A&A...699A.187G` | Astronomy and Astrophysics 2025 | first author: Gámez Rosas, V. | arXiv: 2505.05259 | DOI: 10.1051/0004-6361/202453363

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: Dissect the kinematics and morphology of the molecular gas in the near-nuclear region of NGC 1068 to understand what fuels the AGN and how its energy output affects the surrounding molecular gas  
  > "Our study aims to dissect the kinematics and morphology of the molecular gas within the near-nuclear region of NGC 1068 to understand the mechanisms in the central AGN that might be fuelling it, and the impact of its energy output on the surrounding molecular gas." (abstract)
- Target **NGC 1068 (nuclear continuum source S1)**: coordinates S1: RA(J2000) = 02h 42m 40.70905s, DEC(J2000) = -00d 00m 47.945s (phase-shift centre for imaging)  
  > "to the position of the nuclear radio continuum source S1, RA(J2000) = 02h 42m 40.70905s" (Observations, calibration, and data reduction); "It is the closest luminous Seyfert 2 galaxy (D = 14.4 Mpc;" (Introduction); z/distance D = 14.4 Mpc; 1 arcsec = 70 pc  
  > "to the position of the nuclear radio continuum source S1, RA(J2000) = 02h 42m 40.70905s" (Observations, calibration, and data reduction); "It is the closest luminous Seyfert 2 galaxy (D = 14.4 Mpc;" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2019.1.01540.S
- bands: Band 7  
  > "using the longest baseline configuration available for Band 7 (C43-9/10)." (Observations, calibration, and data reduction)
- frequencies and spectral setup: CO (J=3-2), HCO+ (J=4-3) and 350 GHz continuum; final channel width 8958 kHz (~7.53 km/s) after averaging  
  > "The observations were tuned to observe CO $(J=3\rightarrow 2)$, HCO$^+$ $(J=4\rightarrow 3)$, and 350 GHz continuum" (Observations, calibration, and data reduction); "The final channel widths are 8958 kHz" (Observations, calibration, and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-9/10  
  > "using the longest baseline configuration available for Band 7 (C43-9/10)." (Observations, calibration, and data reduction)
- baselines: _not stated_
- angular resolution: 16 mas (~1.1 pc); beam 16.3 x 15.1 mas, PA -45 deg  
  > "The angular resolution is 16 mas" (Observations, calibration, and data reduction); "The resulting model cubes were then convolved with the ALMA beam ($16.3 \times 15.1$ mas, PA $-45\ensuremath{^\circ}$)." (5.1 Line broadening)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 3-4 September 2021  
  > "We observed NGC 1068 on 3–4 September 2021 with ALMA" (Observations, calibration, and data reduction)
- pi or archival as stated: Project 2019.1.01540.S, PI: P. van der Werf  
  > "(project 2019.1.01540.S, PI: P. van der Werf)" (Observations, calibration, and data reduction)
- Line: CO J=3-2 (not stated)
- Line: HCO+ J=4-3 (not stated)
- External data: Observed rotation curve and orientation of the H2O megamaser disc, used as input for the 3DBarolo simulation  
  > "We set up the simulation using the observed rotation curve and orientation of the H$_2$O megamaser disc (cite: Gallimore2023)" (5.1 Line broadening) [from (cite: Gallimore2023)]
- External data: VLBI position of the nuclear radio continuum source S1, used as the phase centre  
  > "to the position of the nuclear radio continuum source S1, RA(J2000) = 02h 42m 40.70905s" (Observations, calibration, and data reduction) [from (cite: 2004ApJ...613..794G)]
- External data: Keplerian circular velocity of 315 km/s at 10 mas radius from water maser kinematics  
  > "the estimate of the Keplerian circular velocity at 10 mas radius (0.7 pc) of 315 km/s in (cite: Gallimore2023) based on water maser kinematics." (5.5 Kinematic modelling of the high-velocity feature) [from (cite: Gallimore2023)]
- External data: Mass and bolometric luminosity of NGC 1068 used in the dusty Eddington column-density estimate  
  > "Taking the estimates of the mass and bolometric luminosity of NGC 1068 used in (cite: 2020A&A...634A...1G)" (5.4 Near-nuclear motions and possible filamentary structures) [from (cite: 2020A&A...634A...1G)]
- External data: HCO+ abundance X_HCO+ ~ 3e-9 relative to H2 (diffuse Galactic gas), used to convert N_HCO+ to N_H2  
  > "For an abundance ratio $X_{HCO^+}\equiv N_{HCO^+}/N_{H_2}\simeq 3\times 10^{-9}$ similar to that found in diffuse molecular gas in our Galaxy (cite: 2023ApJ...943..172L)" (5.4 Near-nuclear motions and possible filamentary structures) [from (cite: 2023ApJ...943..172L)]
- External data: CO/HCO+ ratios at CND/AGN position at 100 pc resolution: 9 to 16 in CND regions, 11 at the AGN  
  > "They found much higher values of the CO/HCO$^+$ ratio than those found here, ranging from 9 to 16, and 11 at the AGN" (4.1.1 The CO to HCO+ line ratios) [from (cite: Viti2014)]
- External data: Integrated intensity ratio CO/HCO+ of 1.8 in lower-resolution observations of the torus region (their Table 4)  
  > "From their Table 4 we get an integrated intensity ratio of the CO and HCO$^+$ of 1.8 in lower-resolution observations of the torus region." (5.3 CO to HCO+ line ratios) [from (cite: 2022A&A...665A.102V)]
- Simulation/model as data: 3DBarolo tilted-ring simulations of the H2O megamaser disc (Model 1 constant emissivity, Model 2 emissivity falling as r^-2), 17 rings between 5 and 40 mas, 0.5 mas pixels, convolved with the ALMA beam and refitted with the Gaussian analysis  
  > "In sum, the simulation involved 17 nested rings between 5 and 40 mas radius." (5.1 Line broadening); "Models were calculated on 0.5 mas pixel grids" (5.1 Line broadening)
- Simulation/model as data: Toy kinematic model of a string of clouds on parabolic orbits (peritrepa 0.1 pc and 0.5 pc) falling onto the nucleus, compared with the major-axis PV diagram  
  > "We have attempted to model the kinematics of the western high-velocity redshifted emission and absorption features as an extended filament falling in from infinity on a parabolic orbit." (5.5 Kinematic modelling of the high-velocity feature)

## Processing

### Calibration

- pipeline or manual: Standard ALMA pipeline, applied independently to three observing blocks, then merged  
  > "The data were calibrated in CASA 6.4.1 (cite: 2022PASP..134k4501C) using the standard ALMA pipeline." (Observations, calibration, and data reduction); "The pipeline calibration was applied independently to three separate observing blocks." (Observations, calibration, and data reduction)
- casa version: CASA 6.4.1  
  > "The data were calibrated in CASA 6.4.1 (cite: 2022PASP..134k4501C) using the standard ALMA pipeline." (Observations, calibration, and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0432-0210 (3.6 Jy at 345 GHz); phase calibrator J0239-0234  
  > "The pipeline calibrations include bandpass corrections and flux scale calibration based on observations of J0432" (Observations, calibration, and data reduction); "phase-referencing based primarily on observations of J0239-0234 located 2" (Observations, calibration, and data reduction)
- flux scale uncertainty: _not stated_
- self calibration: 1 round of phase-only self-calibration on the continuum with 40 s solution interval (tclean model from line-free channels, then gaincal and applycal)  
  > "In the end, we performed 1 round of phase-only self-calibration." (Continuum and self-calibration); "We adopted an averaging time of 40 s because it produced the lowest failure rate of gain solutions." (Continuum and self-calibration)

### Imaging

- task: CASA tclean (CLEAN); data merged with concatvis, frequency tolerance 0.6 MHz  
  > "we imaged a large, 9$''$ field around S1 and deconvolved using CLEAN (CASA task `tclean`)." (Spectral line cubes); "(CASA task `concatvis` with frequency tolerance $=0.6$ MHz)" (Observations, calibration, and data reduction)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 2.0  
  > "We used Briggs weighting with the robust parameter set to 2.0 (cite: 1995PhDT.......238B) and 2.5 mas pixels." (Spectral line cubes)
- uv taper: Baselines shorter than 1200 klambda flagged (structures larger than ~0.2 arcsec) to suppress ripple from large-scale emission; no taper stated  
  > "We therefore flagged baselines shorter than $1200~\mbox{k}\lambda$ (structures larger than about 0.2$''$) to reduce the ripple artefacts on the final line images." (Spectral line cubes)
- cell size: 2.5 mas  
  > "We used Briggs weighting with the robust parameter set to 2.0 (cite: 1995PhDT.......238B) and 2.5 mas pixels." (Spectral line cubes)
- image size: CO: 9 arcsec field around S1; HCO+: central 0.75 arcsec  
  > "we imaged a large, 9$''$ field around S1" (Spectral line cubes); "so we imaged only the central 0.75$''$." (Spectral line cubes)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub using line-free channels in each spectral window; five channels at each end of each window excluded  
  > "Before imaging, the spectral line data were continuum-subtracted using line-free channels within each spectral window (CASA task `uvcontsub`); the five channels on either end of a spectral window were also excluded from the continuum subtraction." (Spectral line cubes)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Frequency averaging to 8958 kHz channels, time averaging 40 s; after continuum subtraction, time averaging 300 s  
  > "The final channel widths are 8958 kHz" (Observations, calibration, and data reduction); "the continuum-subtracted data were time-averaged by 300 s." (Spectral line cubes)
- final beam: 16.3 x 15.1 mas, PA -45 deg  
  > "The resulting model cubes were then convolved with the ALMA beam ($16.3 \times 15.1$ mas, PA $-45\ensuremath{^\circ}$)." (5.1 Line broadening)
- final rms: _not stated_

### Inherited from earlier work

- Standard self-calibration techniques for the continuum images  
  > "We used standard self-calibration techniques to improve the final image fidelity of the continuum images (cite: 10.1117/12.958828; 1981MNRAS.196.1067C)." (Continuum and self-calibration) [from (cite: 10.1117/12.958828; 1981MNRAS.196.1067C)]
- H2O megamaser disc rotation curve and orientation as input for the 3DBarolo simulation  
  > "We set up the simulation using the observed rotation curve and orientation of the H$_2$O megamaser disc (cite: Gallimore2023)" (5.1 Line broadening) [from (cite: Gallimore2023)]
- Position of the nuclear continuum source S1 taken as the phase centre and as the assumed position of the 365 GHz source  
  > "to the position of the nuclear radio continuum source S1, RA(J2000) = 02h 42m 40.70905s" (Observations, calibration, and data reduction) [from (cite: 2004ApJ...613..794G)]
- Definition of the circumnuclear disc (CND) region  
  > "This area was first defined in (cite: Viti2014) (see Fig. 1) and has continued to be used in subsequent studies" (Footnote 1) [from (cite: Viti2014)]

### Not stated but needed to reproduce (our reading)

- CLEAN deconvolver, multiscale settings, masks and stopping threshold for tclean
- Which channels were line-free for continuum model and uvcontsub
- Self-calibration solution interval beyond the stated 40 s averaging, reference antenna and gain-solution acceptance criteria
- How the continuum image was made (bandwidth, weighting, robust) and its rms
- Rms noise of the line cubes, needed to reproduce the |A| > 1.5 x rms cut
- Exact uv-range flagging command and primary beam correction
- Rest frequencies and velocity convention used for the cubes
- Phase calibration offset treatment: how the ~25 mas shift of the continuum peak was applied
- Initial guesses and fitter for the pixel-wise Gaussian fits
- Excitation, optical depth and LTE column-density code and constants
- Orbit-model code and parameters for the parabolic filament

## Analysis recipe

1. **calibrate and merge three observing blocks**: Standard ALMA pipeline in CASA 6.4.1 applied to each observing block, then concatenated; data averaged in frequency and time  
  > "The pipeline calibration was applied independently to three separate observing blocks." (Observations, calibration, and data reduction); "After calibration, the separate data sets were merged to produce a single data set for further processing" (Observations, calibration, and data reduction)
   - software: CASA 6.4.1, concatvis
   - parameter: concatvis frequency tolerance 0.6 MHz; time averaging 40 s; channel width 8958 kHz  
  > "(CASA task `concatvis` with frequency tolerance $=0.6$ MHz)" (Observations, calibration, and data reduction); "The final channel widths are 8958 kHz" (Observations, calibration, and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **self-calibrate and image the continuum**: Continuum CLEAN model from line-free channels, then gaincal and applycal, one round of phase-only self-calibration  
  > "Self-calibration involved first producing a CLEAN model for the continuum based on line-free channels (CASA task `tclean`) and then using that model to guide phase corrections (CASA tasks `gaincal` and `applycal`)." (Continuum and self-calibration)
   - software: CASA tclean, gaincal, applycal
   - parameter: Solution time averaging 40 s chosen from a range of intervals because it gave the lowest failure rate of gain solutions  
  > "We adopted an averaging time of 40 s because it produced the lowest failure rate of gain solutions." (Continuum and self-calibration)
   - fitting: _not stated_
   - validation: Tried a range of discrete averaging intervals and compared gain-solution failure rates  
  > "we repeated the initial round of self-calibration trying a range of discrete time averaging intervals." (Continuum and self-calibration)
3. **make continuum-subtracted line cubes**: uvcontsub, 300 s time averaging, flag baselines below 1200 klambda, tclean with Briggs robust 2.0 and 2.5 mas pixels; same approach for CO and HCO+  
  > "Before imaging, the spectral line data were continuum-subtracted using line-free channels within each spectral window (CASA task `uvcontsub`)" (Spectral line cubes); "We used Briggs weighting with the robust parameter set to 2.0 (cite: 1995PhDT.......238B) and 2.5 mas pixels." (Spectral line cubes)
   - software: CASA uvcontsub, CASA tclean
   - parameter: CO imaged over 9 arcsec field, HCO+ over central 0.75 arcsec; uv cut 1200 klambda  
  > "we imaged a large, 9$''$ field around S1" (Spectral line cubes); "We therefore flagged baselines shorter than $1200~\mbox{k}\lambda$ (structures larger than about 0.2$''$) to reduce the ripple artefacts on the final line images." (Spectral line cubes)
   - fitting: _not stated_
   - validation: Initial line images showed a ripple pattern from undersampled large-scale emission, which motivated the short-baseline cut  
  > "Initial line images showed a strong ripple pattern produced by undersampled, large-scale emission." (Spectral line cubes)
4. **fit pixel-by-pixel Gaussian line profiles**: Single Gaussian fitted to the spectrum at each pixel of the central 250 mas (17.5 pc), producing maps of amplitude A, centroid v0 and width s  
  > "we analysed the central 250 mas (17.5 pc) by fitting a single Gaussian profile to the spectrum at each pixel of the line cubes." (3 Spectral line analysis)
   - parameter: v0 constrained to 900-1350 km/s  
  > "We constrained the fits in velocity to 900 km s$^{-1}$$< v_0 < 1350$ km s$^{-1}$ resulting in fitted mean velocities of $v_0 <300$ km s$^{-1}$." (3 Spectral line analysis)
   - parameter: linewidth s constrained to 30-190 km/s; spectra with integrated S/N < 3 rejected  
  > "and the linewidths to 30 km s$^{-1}$$\leq s \leq 190$ km s$^{-1}$." (3 Spectral line analysis); "We rejected spectra for which the integrated signal-to-noise ratio was less than 3." (3 Spectral line analysis)
   - assumption: A single Gaussian captures the main kinematic component near systemic velocity; high-velocity features outside the velocity window are not fitted  
  > "This was done to capture the main kinematic component near the AGN’s systemic velocity." (3 Spectral line analysis)
   - fitting: Gaussian least-squares style fit with bounds on v0, amplitude and width (fitter, priors and likelihood not stated)  
  > "we analysed the central 250 mas (17.5 pc) by fitting a single Gaussian profile to the spectrum at each pixel of the line cubes." (3 Spectral line analysis)
   - validation: Visual inspection of each fit; Gaussian model judged to represent spectra well, except multiple peaks in a few spectra closest to S1  
  > "We performed a careful visual inspection of each of the spectral line fits in emission and concluded that the Gaussian model represents the line spectra well." (3 Spectral line analysis)
5. **build moment maps, line-ratio map and PV diagrams**: Integrated line images over the continuum, CO/HCO+ ratio map, velocity and linewidth maps from the Gaussian fits, major-axis (PA 114 deg) and minor-axis (PA 24 deg) PV diagrams, also from the Gaussian models  
  > "We also plot in Fig. [7](#Fig:pvmajco) (right) the analogue PV-diagrams obtained from the Gaussian models." (4.3 Position–Velocity diagrams)
   - parameter: Major axis PA 114 deg, minor axis PA 24 deg  
  > "Figure [8](#Fig:pvminco) shows the position-velocity diagrams along the minor axis" (4.3 Position–Velocity diagrams)
   - fitting: _not stated_
   - validation: _not stated_
6. **extract and fit nuclear spectra and absorption**: Spectra extracted with the CASA viewer integrated over one beam at the continuum peak; Gaussians fitted to emission and absorption features and S/N computed  
  > "we extracted the spectra of both lines, using the CASA task viewer, integrated over one beam centred at the position of the AGN" (4.2.1 Spectra at the AGN position); "In this section we characterise the profiles of both molecular transitions by fitting Gaussians to their spectra and calculating their significance." (4.2.1 Spectra at the AGN position)
   - software: CASA viewer
   - assumption: Emission and absorption are probably broader than apparent but cancel where they overlap; true absorption optical depth ~0.1 and emission ~0.5 mJy near +400 km/s from interpolation  
  > "Both the emission and absorption features seen in Fig. [6](#Fig:abs) are probably considerably broader than is apparent in the figure, but cancel each other at the velocities where they overlap." (4.2.1 Spectra at the AGN position)
   - fitting: Gaussian fits to spectra (details not stated)  
  > "In this section we characterise the profiles of both molecular transitions by fitting Gaussians to their spectra and calculating their significance." (4.2.1 Spectra at the AGN position)
   - validation: S/N threshold used to accept or reject features  
  > "does not present a S/N high enough to be considered a real detection" (4.2.1 Spectra at the AGN position)
7. **test beam smearing with 3DBarolo**: Simulate an ALMA observation of the H2O megamaser disc with 17 nested rings, two emissivity profiles, convolve with the beam and repeat the Gaussian fitting  
  > "We therefore used 3DBarolo (cite: 2015MNRAS.451.3021D) to simulate an ALMA observation of the H$_2$O megamaser disc" (5.1 Line broadening); "Finally, we repeated the Gaussian fitting analysis for the simulated cubes" (5.1 Line broadening)
   - software: 3DBarolo
   - parameter: Outer radius 40 mas (2.8 pc), velocity dispersion 15 km/s, ring width 2 mas, 0.5 mas pixels; Model 1 constant emissivity, Model 2 emissivity r^-2  
  > "we chose a larger outer radius (40 mas = 2.8 pc) than the observed megamaser disc" (5.1 Line broadening); "The ring width, $\delta r = 2$ mas was chosen as a compromise between finely sampling the Keplerian rotation curve near the inner radius and computation speed." (5.1 Line broadening)
   - assumption: Maser-disc kinematics extend to larger radii (40 mas); sigma = 15 km/s  
  > "This set up has the implicit assumption that the kinematics defined by the H$_2$O masers extend towards larger radii." (5.1 Line broadening)
   - fitting: _not stated_
   - validation: Simulated and observed integrated intensity, velocity and linewidth maps compared; Model 2 gives linewidths comparable to observed  
  > "In Model 2, where the emissivity profile is more centrally concentrated, the linewidths are comparable to those observed in CO" (5.1 Line broadening)
8. **test asymmetric drift for sub-Keplerian rotation**: Estimate v_a/v_c from the axisymmetric Jeans equation using sigma, v_c and density gradients read from the moment maps, for the inner 1-2 pc and outer 2-4 pc  
  > "The behaviour is captured in the axisymmetric Jeans Equation" (5.2 Asymmetric drift and sub-Keplerian rotation)
   - parameter: Inner region: sigma ~ v_c ~ 100 km/s; outer region: sigma ~ 50 km/s, v_c ~ 140 km/s  
  > "$\sigma$ is approximately constant at $\sim 50$ km/s while $\partial \log \rho/\partial\log r\sim -1$, and $v_c\sim 140$ km/s" (5.2 Asymmetric drift and sub-Keplerian rotation)
   - assumption: Isotropic turbulence (sigma_t = sigma_r = sigma) and a negative density gradient in the inner region  
  > "For isotropic turbulence ($\sigma_t\equiv\sigma_r\equiv\sigma$), this yields" (5.2 Asymmetric drift and sub-Keplerian rotation)
   - fitting: _not stated_
   - validation: _not stated_
9. **derive excitation temperature and column densities of the absorbing gas**: Combine continuum brightness temperature, absorption depth and off-nuclear emission to get T_x; LTE column densities from integrated optical depths at T_x = 300 K; N_H2 from an assumed HCO+ abundance; compared with a dusty-Eddington lower limit  
  > "If we nonetheless make the assumption of LTE we can compute the column densities of the molecules." (5.4 Near-nuclear motions and possible filamentary structures)
   - parameter: Integrated optical depths 20 km/s (CO) and 10 km/s (HCO+); T_x = 300 K  
  > "have numerically integrated optical depths, $\int \tau dv$, of 20 km/s and 10 km/s" (5.4 Near-nuclear motions and possible filamentary structures)
   - assumption: LTE; X_HCO+ ~ 3e-9 as in diffuse Galactic gas  
  > "For an abundance ratio $X_{HCO^+}\equiv N_{HCO^+}/N_{H_2}\simeq 3\times 10^{-9}$ similar to that found in diffuse molecular gas in our Galaxy (cite: 2023ApJ...943..172L)" (5.4 Near-nuclear motions and possible filamentary structures)
   - fitting: _not stated_
   - validation: Independent dusty-Eddington lower limit gives N_H ~ 1e24 cm-2 or greater  
  > "a cloud can only be in a stable or infalling orbit if $N_H\sim 1\times 10^{24}$ cm$^{-2}$ or greater" (5.4 Near-nuclear motions and possible filamentary structures)
10. **model the infalling high-velocity filament**: Ballistic model of a string of clouds on a parabolic orbit with the pole in the plane of the sky; two parameters (axis angle to line of sight, peritrepa); simulated PV diagrams compared to observed major-axis PV  
  > "With these assumptions there are two parameters that define an orbit: the angle of the symmetry axis of the parabola from the line of sight and the distance of closest approach to the black hole" (5.5 Kinematic modelling of the high-velocity feature)
   - parameter: Peritrepa 0.1 pc (axis along line of sight) and 0.5 pc (axis perpendicular)  
  > "the axis of the orbit is along the line-of-sight and peritrepa=0.1 pc" (5.5 Kinematic modelling of the high-velocity feature); "it is perpendicular to the line of sight and peritrepa=0.5 pc" (5.5 Kinematic modelling of the high-velocity feature)
   - assumption: Pole of orbit in the plane of sky; features within 80 km/s of systemic ignored; no filament physics (temperature, density, ionisation) included  
  > "For simplicity we have assumed that the pole of the orbit lies in the plane of the sky." (5.5 Kinematic modelling of the high-velocity feature); "We have ignored features within 80 km/s of systemic in the modelling" (5.5 Kinematic modelling of the high-velocity feature)
   - fitting: Orbits chosen by eye to reproduce the main PV features; no formal fit  
  > "The model orbits were chosen to reproduce the main features of the observed filament in the major-axis PV-diagram" (5.5 Kinematic modelling of the high-velocity feature)
   - validation: Qualitative comparison of simulated and observed PV diagrams  
  > "This change improves the kinematic match to the observed PV-diagram" (5.5 Kinematic modelling of the high-velocity feature)

## Software

- **CASA** 6.4.1: Pipeline calibration, concatvis, gaincal, applycal, tclean, uvcontsub and viewer spectrum extraction  
  > "The data were calibrated in CASA 6.4.1 (cite: 2022PASP..134k4501C) using the standard ALMA pipeline." (Observations, calibration, and data reduction); "using the CASA task viewer, integrated over one beam centred at the position of the AGN" (4.2.1 Spectra at the AGN position)
- **3DBarolo** : Simulating beam-smeared ALMA cubes of the H2O megamaser disc to test the contribution of rotation to observed linewidths  
  > "We therefore used 3DBarolo (cite: 2015MNRAS.451.3021D) to simulate an ALMA observation of the H$_2$O megamaser disc" (5.1 Line broadening)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Peak continuum intensity (365/350 GHz) | 8.3 | not stated | mJy/beam | 2 | The continuum is dominated by a compact source with peak intensity 8.3 mJy |
| Continuum brightness temperature at nucleus | 550 | not stated | K | 9 | The 350 GHz continuum flux at the nuclear position is 8.3 mJy or in brightness temperature $T_{c}=550$ K |
| Offset of continuum peak from VLBI position of S1 | ~25 | not stated | mas | 2 | In our ALMA image, the continuum peak is offset by $\sim$25 mas northwest of the VLBI position of S1. |
| CO(3-2) high-velocity absorption centroid and S/N | ~411 km/s, S/N 3.5 | not stated | km/s | 6 | we find high-velocity absorption centred at $\sim 411$ km/s with a signal to noise ratio (S/N) of 3.5. |
| HCO+(4-3) absorption S/N | 3.03 | not stated | dimensionless | 6 | with a Signal-to-Noise Ratio (S/N) of 3.03 |
| CO(3-2) broad emission feature near +170 km/s, significance | S/N 4.5 | not stated | dimensionless | 6 | with a S/N of 4.5 |
| CO(3-2)/HCO+(4-3) integrated line ratio near nucleus | 0.5-2 | not stated | dimensionless | 5 | line ratios in the parsec-sized region around the nucleus are in the range 0.5–2 which is a factor of 10–20 lower than that seen in the CND |
| Linewidth near nucleus and beyond 2 pc | ~200 near nucleus, ~50 at r>2 pc | not stated | km/s | 4 | The linewidths are of the order of 200 km/s close to the nucleus and get abruptly reduced to around 50 km/s |
| Asymmetric drift ratio v_a/v_c, inner region (1 < r < 2 pc) | ~0.5 | not stated | dimensionless | 8 | this yields $v_a/v_c\sim 0.5$, so that the observed velocity would be about half the actual Keplerian circular velocity. |
| Asymmetric drift ratio v_a/v_c, outer region (2-4 pc) | ~0.04 | not stated | dimensionless | 8 | the Jeans equation predicts $v_a/v_c\sim\sigma^2/2v_c^2\sim 0.04$, which is negligible. |
| Excitation temperature of the absorbing gas | ~300 (270-360 range in text) | not stated | K | 9 | These features exhibit high-excitation temperatures around 300 K and significant column densities |
| LTE column densities N_CO and N_HCO+ at T_x = 300 K | N_CO ~ 5e18; N_HCO+ ~ 3e15 | not stated | cm^-2 | 9 | From LTE calculations at $T_x=300$ K, the total column densities in the two molecules are $N_{CO}\sim 5\times 10^{18} {\rm cm}^{-2}$ and $N_{HCO^+}\sim 3\times 10^{15} {\rm cm}^{-2}$. |
| Implied H2 column density from N_HCO+ | ~1e24 | not stated | cm^-2 | 9 | the latter column density implies $N_{H_2}\sim 1\times 10^{24}$ cm$^{-2}$. |

## Qualitative findings

- Strong east-west asymmetry in morphology, velocity and line intensity of the nuclear disc  
  > "Our observations reveal significant asymmetry between the eastern and western sides of the nuclear disc in terms of morphology, velocity, and line intensity." (abstract)
- Low-velocity connections extend to ~13 pc, suggesting interaction with larger-scale structures  
  > "We find low velocity connections extending to 13 pc suggesting interactions with larger scale structures." (abstract)
- High-velocity redshifted clouds seen in absorption and emission at the nuclear position, interpreted as an infalling cloud or filament  
  > "We find high-velocity redshifted clouds in absorption and emission at the nuclear position." (abstract)

## Claim tuples

- H: Do the broad lines within ~2 pc require turbulence, or can beam smearing of a rotating disc explain them? | E: 3DBarolo simulations of the H2O megamaser disc convolved with the ALMA beam and fitted with the same Gaussian analysis | R: Simulated linewidths in the concentrated-emissivity model are comparable to the observed ones | F: Beam smearing of unresolved rotation can explain the broad lines; turbulence is not required | **partially**
- H: Can asymmetric drift explain the sub-Keplerian velocities? | E: Jeans-equation estimate of v_a/v_c from the moment maps in inner and outer regions | R: v_a/v_c ~ 0.5 inside 2 pc and ~0.04 for 2-4 pc | F: Asymmetric drift is plausible inside ~2 pc but cannot explain the low velocities at larger radii | **partially**
- H: Is the high-velocity absorption at the nucleus non-circular infalling gas? | E: Nuclear spectra, PV diagrams, free-fall velocity argument and parabolic-orbit model | R: Redshifted absorption up to ~500 km/s continuous with western redshifted emission | F: An infalling cloud or filament near the nucleus | **supported**
- H: How do CO/HCO+ ratios at the nucleus compare with lower-resolution values? | E: Ratio map of integrated CO(3-2) and HCO+(4-3) at 1.1 pc resolution | R: Ratios 0.5-2 versus 9-16 (11 at the AGN) at 100 pc resolution | F: Much lower ratios at high resolution, with density plus chemistry (AGN radiation) shifts likely | **supported**

## Reasoning

- Why this data: Longest ALMA baselines give 16 mas (~1.1 pc) resolution to resolve the counter-rotation and outflow questions  
  > "Towards addressing these questions, we used ALMA to observe CO $(J=3\rightarrow 2)$ and HCO$^+$ $(J=4\rightarrow 3)$ on the longest available baselines, resulting in 16 mas ($\sim$1.1 pc) angular resolution." (Introduction)
- Why this method: Pixel-wise Gaussian fits used because moment maps are hard to interpret at low S/N  
  > "This approach provides a clearer representation of the velocity structure, as the more conventional moment maps yield representations that are harder to interpret due to the low signal-to-noise ratio of the cubes." (3 Spectral line analysis)
- Alternative: Circularly orbiting ring at ~0.5 pc rejected as the origin of the redshifted absorption  
  > "However, several arguments can be made against a simple model of a ring of molecular gas orbiting at a radius of $\sim 0.5$ parsec" (5.4 Near-nuclear motions and possible filamentary structures)
- Alternative: A real offset of the continuum peak from S1 considered but judged unlikely; position adjusted to S1  
  > "Perhaps the offset is real, but it seems unlikely." (4.1 Integrated line emission)
- How they decided it was enough: Self-calibration stopped after one phase-only round; averaging time chosen by lowest gain-solution failure rate  
  > "We adopted an averaging time of 40 s because it produced the lowest failure rate of gain solutions." (Continuum and self-calibration)
- Limitation (authors): High-velocity features outside the fitted velocity window are not included in the Gaussian maps  
  > "As a result, any high-velocity features outside this range, whether redshifted or blueshifted, are not accounted for in these fits." (3 Spectral line analysis)
- Limitation (authors): Cutting short baselines created negative bowls in both line maps  
  > "We also see that cutting the short baselines during our cleaning process created negative bowls in both line maps" (4.1 Integrated line emission)
- Limitation (authors): 3DBarolo does not simulate absorption, so integrated-intensity comparison is difficult  
  > "It is difficult to compare the integrated intensity images because 3DBarolo does not simulate absorption" (5.1 Line broadening)
- Limitation (authors): Orbit model omits filament physics (temperature, density, ionisation)  
  > "We have not included any detailed physics about the filament such changes in temperature, density or ionisation as it approaches the centre." (5.5 Kinematic modelling of the high-velocity feature)
- Caveat (inferred, ours): Absorption features are only 3.0-3.5 sigma, so the high-velocity infall claim rests on marginal detections
- Caveat (inferred, ours): Beam smearing versus turbulence is not decisively separated; the 3DBarolo test is a two-model toy with an assumed emissivity
- Caveat (inferred, ours): Hard cut at 1200 klambda removes large-scale flux and imprints negative bowls that can bias moment and line-ratio maps
- Caveat (inferred, ours): Temperature and column densities rely on LTE, an assumed HCO+ abundance and a 300 K excitation with no uncertainties
- Caveat (inferred, ours): Orbit models are chosen by eye with no fit statistics
- Caveat (inferred, ours): Continuum peak offset of ~25 mas is attributed to phase-referencing and then removed by hand

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: tclean masks, thresholds, deconvolver and iteration limits
- Missing: line-free channel selection and cube rms
- Missing: self-calibration details beyond 1 phase-only round at 40 s
- Missing: Gaussian-fitting code and initial guesses
- Missing: LTE and orbit-model code
- Data volume (inferred): Likely 100-300 GB raw for three long-baseline Band 7 observing blocks (estimate); averaged working data far smaller
- Score (inferred): 3/5, Project code and key imaging settings (robust 2.0, 2.5 mas, 1200 klambda cut, self-cal 40 s) are given and numeric results are partly reported, but masks, thresholds, line-free channels, cube rms and the modelling code are not stated.
- Rediscovery candidate: no, Recipe lacks imaging thresholds, masks and channel selections and the paper does not itself state that the data are public; several main results are interpretive rather than numeric.

## Links

- Method: (cite: 2015MNRAS.451.3021D) (3DBarolo tilted-ring and beam-smearing modelling)
- Method: (cite: 2022PASP..134k4501C) (CASA reference)
- Method: (cite: 10.1117/12.958828; 1981MNRAS.196.1067C) (Self-calibration technique)
- Companion: (cite: 2019ApJ...884L..28I) (Earlier ALMA HCN absorption and counter-rotation interpretation at the same nucleus)
- Companion: (cite: Gallimore2023) (Maser disc rotation curve and continuum source size used as model inputs)
- Companion: (cite: 2022A&A...665A.102V) (Numerical model of a cloud falling onto a disc in NGC 1068 and lower-resolution CO/HCO+ ratio)
- Related: ALMA project 2019.1.01540.S (PI P. van der Werf)
- Related: GATOS and NUGA AGN samples (line-ratio comparison)

## Checks

```json
{
 "quotes": 128,
 "quotes_ok": 128,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 1,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 113,
  "stated": 84,
  "rate": 0.743
 },
 "evidence_ok": true
}
```
