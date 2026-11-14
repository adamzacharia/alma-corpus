# The Dynamics of Infall and Accretion Shocks in the Outer Disk

`2025ApJ...990...53T` | The Astrophysical Journal 2025 | first author: Terebey, Susan | arXiv: 2505.24582 | DOI: 10.3847/1538-4357/ade3c6

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: star_formation, protoplanetary_disks
- Question: Do shocks where infalling envelope gas meets the outer disk produce non-circular (elliptical) gas orbits whose Doppler signatures in line moment maps can be detected with ALMA, as tested against archival C18O data of L1527  
  > "We investigate the role of shocks using a theoretical and modeling framework we call the shock twist-angle Keplerian (STAK) disk, connecting the disk and infalling envelope gas via a shock using general physical principles." (abstract); "We begin by comparing our elliptical and circular modeling framework with ALMA data for the protostar L1527, since there is known evidence for noncircular motions in its outer disk." (5.1 Implications for Observations: a Case Study for L1527)
- Target **L1527 IRS (IRAS 04368+2557)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00210.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.96'' x 0.73'' (archival C18O(2-1) data)  
  > "that have a spatial resolution of 0.96$\ensuremath{''}~\times~0.73\ensuremath{''}$, enough to cover envelope scales" (5.1 Implications for Observations: a Case Study for L1527)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: Cycle 0, 2012 August 26  
  > "that was taken during cycle 0 on 2012 August 26" (5.1 Implications for Observations: a Case Study for L1527)
- pi or archival as stated: Archival data, project 2011.0.00210.S, PI N. Ohashi  
  > "We first compare with ALMA archival data" (5.1 Implications for Observations: a Case Study for L1527); "(Project code: 2011.0.00210.S; PI: N. Ohashi)" (5.1 Implications for Observations: a Case Study for L1527)
- Line: C18O J = 2-1 (not stated)
- Other facility **ALMA**: Archival C18O(2-1) Cycle 0 data of L1527 used for qualitative comparison with the model  
  > "We use the C$^{18}$O(2-1) ALMA data of L1527" (5.1 Implications for Observations: a Case Study for L1527); "ALMA" (Facilities)
- External data: eDisk C18O(2-1) moment maps of L1527 at 0.17'' x 0.14'' (22 au), compared by eye with the model  
  > "present moment maps for C$^{18}$O(2-1) and other molecular species that remain consistent with the predicted STAK signature." (5.1 Implications for Observations: a Case Study for L1527) [from van't Hoff et al. 2023 (cite: vanthoff_2023)]
- External data: Upstream gas temperature of about 35 K at the shock location (used for cooling-time estimate)  
  > "we estimate an upstream temperature of approximately T$_{1}$$\sim35$ K at the shock location (cite: Flores-Rivera_2021)" (Post-Shock Cooling Timescale) [from Flores-Rivera et al. 2021 (cite: Flores-Rivera_2021)]
- External data: Planck mean opacity from published figure, used for cooling timescale  
  > "is the Planck mean opacity estimated from Figure 9 in (cite: Bell1994)" (Post-Shock Cooling Timescale) [from Bell & Lin 1994 (cite: Bell1994)]
- External data: L1527 source inclination of 85 deg from 1.3 mm dust continuum versus 95 deg from line data  
  > "while the 1.3 mm dust continuum seem to imply" (5.1 Implications for Observations: a Case Study for L1527) [from (cite: vanthoff_2023) and references therein]
- Simulation/model as data: RadChemT synthetic C18O(2-1) spectral line cube (219 GHz, 6.0 km/s source velocity, 1 au pixels, 100 channels of 0.168 km/s) for circular and elliptical (STAK) disk motion  
  > "contains both continuum and C$^{18}$O(2-1) spectral line emission at 219 GHz, an adopted source radial velocity of 6.0 km s$^{-1}$, with 1 au pixels and 100 frequency channels having 0.168 km s$^{-1}$velocity resolution." (4.2 Constructing Synthetic ALMA Spectral Line Cubes)

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
- final beam: 0.96'' x 0.73'' for the archival C18O data  
  > "that have a spatial resolution of 0.96$\ensuremath{''}~\times~0.73\ensuremath{''}$, enough to cover envelope scales" (5.1 Implications for Observations: a Case Study for L1527)
- final rms: _not stated_

### Inherited from earlier work

- Physical and chemical structure method of the RadChemT models  
  > "We adopted the same physical and chemical structure method as in (cite: Flores-Rivera_2021) to now include the updated ram pressure boundary condition." (3 Modifications to RadChemT) [from (cite: Flores-Rivera_2021)]
- C18O abundance file used to generate the synthetic moment maps  
  > "we adopt the same C$^{18}$O abundance file to generate the synthetic moment maps" (3 Modifications to RadChemT) [from (cite: Flores-Rivera_2021)]
- Three models used for the L1527 comparison derive from earlier modeling and data comparison  
  > "that derive from our previous extensive modeling and data comparison in (cite: Flores-Rivera_2021)" (5.1 Implications for Observations: a Case Study for L1527) [from (cite: Flores-Rivera_2021)]
- Moment map equations (sums and normalization) taken from the ALMA website  
  > "The full equations for the velocity moments, involving sums and normalization factors, are available on the ALMA website (cite: McMullin_2007)." (4.2 Constructing Synthetic ALMA Spectral Line Cubes) [from (cite: McMullin_2007)]
- Disk density structure: radial power law with vertical Gaussian, axial symmetry  
  > "The physical structure of our disk is described in the same way as in (cite: Flores-Rivera_2021)" (6.2 Model advantages and limitations) [from (cite: Flores-Rivera_2021)]

### Not stated but needed to reproduce (our reading)

- ALMA spectral setup (band, correlator configuration, channel width) of project 2011.0.00210.S as used here
- Calibration, imaging parameters (weighting, robust, cell size, deconvolver, continuum subtraction, CASA version) used to make the archival C18O cube and moment 1 map
- How the archival moment 1 map was computed (velocity range, clipping or noise threshold) and the 0.84'' model convolution recipe
- RadChemT / HOCHUNK3D code, input density, luminosity and abundance files needed to regenerate the synthetic cubes
- Disk and envelope parameters of the L1527 model (stellar mass, centrifugal radius beyond the quoted 75 au and 0.22 Msun, infall rate, outflow cavity) are mostly deferred to Flores-Rivera et al. 2021
- Distance to L1527 and source coordinates, position angle used for the comparison
- The model-to-data comparison is by eye, so no quantitative metric or acceptance criterion is available

## Analysis recipe

1. **Define disk surface with ram pressure boundary**: Set ram pressure of envelope gas (including inward velocity) equal to disk gas pressure at grid points, and interpolate between disk and envelope points to get the shock locations (r_shock, theta_1)  
  > "the grid of temperature and density values in RadChemT are used evaluate the terms point-by-point" (3.1 Disk Surface From Updated Ram Pressure Boundary Condition)
   - software: RadChemT, HOCHUNK3D
   - parameter: Boundary condition: rho_disk c_s,disk^2 = rho_env (c_s,env^2 + v_env^2)  
  > "\rho_{disk} c_{s_{disk}}^2 = \rho_{env}( c_{s_{env}}^2 + v_{env}^2)" (3.1 Disk Surface From Updated Ram Pressure Boundary Condition)
   - assumption: Thin disk, solid-body rotation of the pre-collapse cloud, TSC collapse model for envelope, inward motion fully quashed at the first shock  
  > "we follow the same prescriptions given in (cite: Flores-Rivera_2021) and that are based on the sole use of the TSC collapse model." (3 Modifications to RadChemT); "we simplified the ram pressure boundary condition to require that all inward motion be quashed at the first shock" (6.2 Model advantages and limitations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Assign elliptical orbit velocities and rerun MCRT**: Run the Monte Carlo radiative transfer code again to update density and temperature near the new disk surface, then specify disk velocities from elliptical orbits (apoapsis at the shock, angular momentum conserved)  
  > "2) run the MCRT code a second time to update density and temperature near the new disk surface, and 3) specify new velocities within the disk based on elliptical orbits." (3 Modifications to RadChemT)
   - software: RadChemT, HOCHUNK3D
   - parameter: Ellipse set by (1-e) = r_c,kep / r_shock and a = r_shock/(1+e); theta_0 found with an iterative scheme from the parabola equation  
  > "using an iterative scheme to find $\theta_0$ using equation" (2.3 Elliptical gas streamlines within the disk)
   - assumption: Gas cools rapidly after the shock so pressure gradients do not deflect the flow; gravity dominates  
  > "We treat the gas flow as transitioning immediately to elliptical streamlines on crossing the shock." (3.1 Disk Surface From Updated Ram Pressure Boundary Condition)
   - fitting: _not stated_
   - validation: Post-shock cooling timescale estimated analytically with Rankine-Hugoniot jump conditions  
  > "we compute the immediate post-shock temperature and pressure using the jump conditions" (3.1 Disk Surface From Updated Ram Pressure Boundary Condition)
3. **Build synthetic line cube and moment maps**: Make continuum image from first and last (line-free) channels, subtract it from each plane of the C18O cube, then compute moment 0 and classic moment 1 over 2-10 km/s without excluding channels  
  > "The continuum image (not shown) was constructed from off-line channels by averaging the first and last channel of the spectral line cube" (4.2 Constructing Synthetic ALMA Spectral Line Cubes); "by integrating spectral line emission over a velocity range of \[2,10\] km s$^{-1}$." (4.2 Constructing Synthetic ALMA Spectral Line Cubes)
   - software: RadChemT
   - parameter: Inclinations 30, 60, 85 deg shown (95 deg also used for L1527); 2.5 au spatial resolution in model maps; no velocity channels excluded  
  > "However, in this work, no velocity channels have been excluded in the moment maps presented." (4.2 Constructing Synthetic ALMA Spectral Line Cubes); "Each image is continuum subtracted and has 2.5 au spatial resolution." (4.3 Emission Signatures in the Outer Disk)
   - assumption: Emission treated as optically thin for continuum subtraction, with over-subtraction artifacts acknowledged  
  > "thus showing just C$^{18}$O gas when the emission is optically thin." (4.2 Constructing Synthetic ALMA Spectral Line Cubes)
   - fitting: _not stated_
   - validation: _not stated_
4. **Convolve models to ALMA-like beams**: Convolve the 75 au radius disk models with circular Gaussians of FWHM 8, 25 and 75 au to test partially resolved disks  
  > "These images convolve the 75 au radius disk with a Gaussian 2D function having FWHM = 8 au, 25 au, and 75 au" (4.5 Telescope spatial resolution effect)
   - assumption: Circular beam, no position-angle exploration  
  > "a full exploration of beam shapes and position angles is outside the scope of this work." (4.5 Telescope spatial resolution effect)
   - fitting: _not stated_
   - validation: _not stated_
5. **Compare models with archival ALMA moment 1 map of L1527**: Compare the archival C18O(2-1) moment 1 map by eye with circular (i=85 deg) and elliptical (i=85 and 95 deg) models at 0.84'' circular resolution  
  > "Of the three models, the elliptical orbit model at $i=95^{\circ}$ (top right) seems to match most closely to the L1527 C$^{18}$O ALMA data." (5.1 Implications for Observations: a Case Study for L1527)
   - parameter: Model resolution 0.84'' equal to the geometric mean of the 0.96'' x 0.73'' beam  
  > "equivalent circular resolution 0.84$''$, equal to the geometric mean" (5.1 Implications for Observations: a Case Study for L1527)
   - assumption: Disk major axis rotated north-south to match the data  
  > "Notice that the disk major-axis is oriented North-South to match the data" (5.1 Implications for Observations: a Case Study for L1527)
   - fitting: No fit; comparison by eye  
  > "Comparison by eye shows the expected asymmetry in peak red and blue shifted gas locations" (5.1 Implications for Observations: a Case Study for L1527)
   - validation: Peak red/blue positions and the inner twist of the system-velocity contour judged by eye  
  > "Both the peak red and blue shifted gas locations match, and the inner VCA twist tracing the system velocity (green) looks well aligned." (5.1 Implications for Observations: a Case Study for L1527)

## Software

- **RadChemT** : Dynamics, radiative transfer and astrochemistry to make synthetic line cubes, modified to include the STAK velocity field  
  > "RadChemT combines the gas dynamics, radiative transfer and gas-grain chemical abundance calculations to generate predictions that can be directly compared with observations." (3 Modifications to RadChemT)
- **HOCHUNK3D** : Monte Carlo radiative transfer for dust and gas temperature and the disk-envelope density grid  
  > "to obtain the dust and gas temperature profiles" (3 Modifications to RadChemT)
- **astropy** : _not stated_

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Fiducial streamline eccentricity e | 0.43 | not stated | dimensionless | 2 | / 0.43 / 52.10 au / 74.53 au / 42.44 au / 60.15$^{\circ}$ / 83.03$^{\circ}$ / |
| Fiducial streamline semi-major axis a | 52.10 | not stated | au | 2 | / 0.43 / 52.10 au / 74.53 au / 42.44 au / 60.15$^{\circ}$ / 83.03$^{\circ}$ / |
| Fiducial streamline shock radius r_shock | 74.53 | not stated | au | 1 | / 0.43 / 52.10 au / 74.53 au / 42.44 au / 60.15$^{\circ}$ / 83.03$^{\circ}$ / |
| Fiducial streamline circular destination radius r_c,kep | 42.44 | not stated | au | 2 | / 0.43 / 52.10 au / 74.53 au / 42.44 au / 60.15$^{\circ}$ / 83.03$^{\circ}$ / |
| Fiducial streamline polar angles theta_0 and theta_1 | 60.15 and 83.03 | not stated | degrees | 1 | / 0.43 / 52.10 au / 74.53 au / 42.44 au / 60.15$^{\circ}$ / 83.03$^{\circ}$ / |
| Azimuth phi_1 at the shock for the fiducial streamline | 167.7 | not stated | degrees | 2 | leads to $\phi_1=167.7^{\circ}$ at the shock location |
| Smallest theta_0 giving a streamline that avoids the outflow cavity | 21 | not stated | degrees | 1 | occurs at $\theta_0=21^{\circ}$ |
| Ratio v_z / v_c,kep for the fiducial streamline | 0.10 | not stated | dimensionless | 2 | the ratio is 0.10 |
| Free-fall velocity at the shock locations | 2.3-3.2 | not stated | km/s | 1 | find it to range between $v_{ff} \sim 2.3$-3.2 km s$^{-1}$ |
| Post-shock gas temperature for streamlines with r_shock > r_d/2 | approximately 240-440 | not stated | K | 2 | we find the downstream (hence, post-shock) temperatures range from approximately $T_{2}\sim 240$-440 K |
| Post-shock cooling timescale for streamlines with r_shock > r_d/2 | approximately 3-40 | not stated | minutes | 2 | our calculated cooling timescales are notably short, spanning approximately 3-40 minutes. |
| L1527 source inclination preferred by C18O gas motion in archival ALMA data | 95 | not stated | degrees | 5 | best matches a source inclination of 95$^{\circ}$, rather than 85$^{\circ}$. |

## Qualitative findings

- Elliptical post-shock orbits make the moment 1 system-velocity contour twist away from the minor axis (Velocity Crowding Angle below 90 deg), whereas circular orbits give 90 deg  
  > "The VCA is a potential observational measure that can distinguish between the circular case, which should have VCA $=90\ensuremath{^\circ}$" (4.4 Post-shock Velocity Signatures in the Outer Disk)
- Moment 0 asymmetry is lost for beams of 25 au and 75 au but the moment 1 asymmetry remains at all three tested resolutions  
  > "Only the well resolved disk with 8 au resolution noticeably retains spatial asymmetry in the STAK disk." (4.5 Telescope spatial resolution effect)
- Higher resolution eDisk C18O data of L1527 appear consistent with the predicted inner twist  
  > "More recent high-spatial-resolution ALMA data also appear consistent with the predicted inner twist." (7 Conclusions)

## Claim tuples

- H: Gas passing through an envelope-disk shock follows elliptical orbits that leave an observable kinematic signature distinct from circular Keplerian rotation | E: Built the STAK model in RadChemT and made synthetic C18O(2-1) cubes and moment maps for circular and elliptical disks at several inclinations | R: Elliptical models show asymmetric, twisted moment 0 and moment 1 maps relative to the disk major axis, unlike circular models | F: The STAK disk leaves an inner twist detectable with ALMA spectral line data | **supported**
- H: The STAK signature survives limited spatial resolution | E: Convolved the 75 au disk models with Gaussian beams of 8, 25 and 75 au at i=60 and 85 deg | R: Moment 0 asymmetry largely disappears at 25 and 75 au, while the moment 1 velocity asymmetry persists | F: Velocity moment maps are the better diagnostic for marginally resolved disks | **supported**
- H: Archival ALMA C18O(2-1) data of L1527 show STAK-like asymmetries | E: Compared by eye the Cycle 0 moment 1 map (0.96'' x 0.73'') with circular and elliptical models at 0.84'' resolution and i=85 and 95 deg | R: The elliptical model at i=95 deg matches the peak red and blue positions and the inner twist best | F: Improved agreement over the circular model and a preferred inclination of 95 deg, but the match is qualitative | **partially**

## Reasoning

- Why this data: L1527 has known evidence for non-circular motion in its outer disk, and the Cycle 0 data cover envelope scales  
  > "since there is known evidence for noncircular motions in its outer disk." (5.1 Implications for Observations: a Case Study for L1527)
- Why this method: Moment 1 maps are chosen because they are the diagnostic that retains the STAK signature at partial resolution  
  > "the STAK signature is retained best in the velocity moment map." (7 Conclusions)
- Alternative: Higher-resolution C18O data of van 't Hoff et al. 2018 were rejected as too noisy for the moment 1 comparison  
  > "this dataset was too noisy for the particular features we wanted to compare with." (5.1 Implications for Observations: a Case Study for L1527)
- Alternative: Moment 9 or quadratic centroid methods were not used; classic moment 1 was implemented  
  > "This is in contrast to moment 9 or quadratic moment methods that prioritize measuring the spectral line centroid" (4.2 Constructing Synthetic ALMA Spectral Line Cubes)
- How they decided it was enough: _not stated_
- Limitation (authors): Disk density is not updated self-consistently with the new velocities  
  > "one limitation is that we do not update the disk density in a self consistent manner, leaving that to future work." (6.2 Model advantages and limitations)
- Limitation (authors): No standardized method for moment maps, so the comparison may depend on the adopted method  
  > "One caution is that there is no standardized method for constructing velocity moment maps, meaning the comparison may depend on the adopted method." (5.1 Implications for Observations: a Case Study for L1527)
- Limitation (authors): Velocity asymmetries are not a unique signature of the STAK disk  
  > "We note that velocity asymmetries arise naturally at the shock in the STAK dynamic disk, but are not a unique signature." (5.1 Implications for Observations: a Case Study for L1527)
- Caveat (inferred, ours): Model-data comparison is visual with no goodness-of-fit, so the inclination preference of 95 vs 85 deg is not statistically supported
- Caveat (inferred, ours): Only one archival ALMA dataset (coarse 0.84'' effective resolution) is used, so the test is weak for a thin disk of about 75 au radius
- Caveat (inferred, ours): Other mechanisms (infalling envelope ballistic orbits, streamers, warps) could produce similar twists and are not excluded quantitatively
- Caveat (inferred, ours): Only the C18O line is modelled and optical depth and continuum over-subtraction can mimic asymmetries
- Caveat (inferred, ours): Synthetic observations are not passed through ALMA uv sampling or noise, only convolved with a Gaussian

## Reproducibility

- Data public (paper): Archival ALMA data (Cycle 0 project 2011.0.00210.S)  
  > "We examine archival ALMA data for the class 0/I protostar L1527" (abstract)
- Products in archive: _not stated_
- Missing: RadChemT / HOCHUNK3D modifications and model input files are not stated as released
- Missing: Imaging and moment-map recipe for the archival ALMA cube
- Missing: L1527 model parameters, which live in Flores-Rivera et al. 2021
- Missing: Quantitative comparison metric
- Data volume (inferred): Small: one Cycle 0 C18O(2-1) dataset, likely a few GB of raw data
- Score (inferred): 2/5, The ALMA comparison is qualitative and the main work is a semi-analytic model run through unreleased RadChemT code with inherited parameters, so numeric answer keys are limited to model streamline quantities.
- Rediscovery candidate: no, ALMA data are public, but the central results come from custom model code and a by-eye comparison, with no complete numeric recipe for the observational part.

## Links

- Method: Flores-Rivera et al. 2021 (cite: Flores-Rivera_2021) (Original RadChemT modeling method and L1527 models adopted here)
- Method: Whitney et al. 2013 (cite: Whitney_2013) (HOCHUNK3D Monte Carlo radiative transfer used for temperatures)
- Method: Cassen & Moosman 1981 (cite: Cassen_1981) (Parabolic streamline and centrifugal radius prescription)
- Companion: van't Hoff et al. 2023 (cite: vanthoff_2023) (eDisk C18O moment maps of L1527 compared with the STAK signature)
- Companion: Sakai et al. 2014 (cite: Sakai_2014) (Ballistic centrifugal-barrier model for L1527)
- Companion: Ohashi et al. 2023 (cite: Ohashi_2023) (eDisk survey of protostar disks)
- Related: eDisk ALMA survey

## Checks

```json
{
 "quotes": 72,
 "quotes_ok": 72,
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
  "facts": 89,
  "stated": 46,
  "rate": 0.517
 },
 "evidence_ok": true
}
```
