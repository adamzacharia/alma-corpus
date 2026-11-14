# Stephenson 2 DFK 52: Discovery of an exotic red supergiant in the massive stellar cluster RSGC2

`2025A&A...700L..11S` | Astronomy and Astrophysics 2025 | first author: Siebert, M. A. | arXiv: 2507.11609 | DOI: 10.1051/0004-6361/202555975

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars, stellar_physics
- Question: What are the circumstellar gas and dust structure and mass-loss history of the red supergiant DFK 52 in RSGC2, from continuum, 12CO, 13CO and SiO emission?  
  > "we aim to provide starting insights into the evolutionary status and the mass-loss history of DFK 52" (Introduction)
- Target **DFK 52 (red supergiant in Stephenson 2 / RSGC2)**: coordinates alpha_J2000 = 18h39m23.406s, delta_J2000 = -06d02m16.12s (measured from unresolved SiO emission)  
  > "stellar position $\alpha_{\mathrm{J2000}}=18\mathrm{h}39\mathrm{m}23.406\mathrm{s}$, $\delta_{\mathrm{J2000}}=-06^{\circ}02'16.12''$" (Molecular emission); "The interpretation of these data is reliant on the assumption that DFK 52 is a cluster member, and hence at the cluster distance of $5.8^{+1.91}_{-0.76}$ kpc (cite: davies2007_rsgc2)." (Cluster membership); z/distance 5.8 (+1.91/-0.76) kpc (cluster distance); v_sys = 109 +/- 1.2 km/s  
  > "stellar position $\alpha_{\mathrm{J2000}}=18\mathrm{h}39\mathrm{m}23.406\mathrm{s}$, $\delta_{\mathrm{J2000}}=-06^{\circ}02'16.12''$" (Molecular emission); "The interpretation of these data is reliant on the assumption that DFK 52 is a cluster member, and hence at the cluster distance of $5.8^{+1.91}_{-0.76}$ kpc (cite: davies2007_rsgc2)." (Cluster membership); distance from RSGC2 cluster distance from Davies et al. 2007 (cite: davies2007_rsgc2), assuming DFK 52 is a cluster member  
  > "stellar position $\alpha_{\mathrm{J2000}}=18\mathrm{h}39\mathrm{m}23.406\mathrm{s}$, $\delta_{\mathrm{J2000}}=-06^{\circ}02'16.12''$" (Molecular emission); "The interpretation of these data is reliant on the assumption that DFK 52 is a cluster member, and hence at the cluster distance of $5.8^{+1.91}_{-0.76}$ kpc (cite: davies2007_rsgc2)." (Cluster membership)

## Data provenance

- ALMA projects: 2023.1.01519.S, 2024.A.00018.S
- bands: Band 6 (1.3 mm)  
  > "These observations were performed with two configurations of the main 12m array using the Band 6 receiver" (Observations); "Atacama Large Millimeter/submillimeter Array (ALMA) observations at 1.3mm" (abstract)
- frequencies and spectral setup: Four spectral windows in 214-233 GHz: 12CO J=2-1 (230.538 GHz), SiO J=5-4 (215.596 GHz); ACA adds 13CO J=2-1 (220.399 GHz); 1.27 km/s resolution, 1.8 GHz total bandwidth  
  > "Four spectral windows were positioned in the $214-233$ GHz range targeting $^{12}$CO $J=2-1$ at 230.538 GHz and SiO $J=5-4$ at 215.596 GHz." (Observations); "The spectral resolution is 1.27 km s$^{-1}$, and the total bandwidth is 1.8 GHz." (Observations); "with the addition of the $^{13}$CO $J=2-1$ transition at 220.399 GHz." (Observations)
- continuum bandwidth: _not stated_
- arrays: 12m array (project 2023.1.01519.S) and ACA (project 2024.A.00018.S)  
  > "two configurations of the main 12m array" (Observations); "targeted only DFK 52 with the Atacama Compact Array (ACA)" (Observations)
- configurations: two 12m configurations (not named) plus ACA  
  > "These observations were performed with two configurations of the main 12m array using the Band 6 receiver" (Observations)
- baselines: _not stated_
- angular resolution: 0.35'' at 230 GHz (12m data)  
  > "achieving a spatial resolution of 0.35$''$ at 230 GHz" (Observations)
- max recoverable scale: 12.5'' (12m data); ACA added to recover extended emission  
  > "a maximum recoverable scale (MRS) of 12.5$''$" (Observations)
- sensitivity: 1 mJy/beam (line), 20 uJy/beam (continuum)  
  > "The final brightness sensitivities are 1 mJy/beam for spectral line data and 20 $\mu$Jy/beam for the continuum." (Observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: 2024.A.00018.S obtained with Director's Discretionary Time  
  > "We gratefully acknowledge the use of Director’s Discretionary Time at ALMA under project ADS/JAO.ALMA#2024.A.00018.S." (Acknowledgements)
- Line: 12CO J=2-1 (230.538 GHz)
- Line: SiO J=5-4 (215.596 GHz)
- Line: 13CO J=2-1 (220.399 GHz)
- Other facility **Herschel/PACS**: Archival point-source photometry (incl. 120 um) added to the SED  
  > "archival measurements from the Herschel/PACS point source catalogue (cite: Marton2024_PACS_PSC)" (Spectral energy distribution)
- External data: Cluster distance 5.8 (+1.91/-0.76) kpc used for DFK 52  
  > "at the cluster distance of $5.8^{+1.91}_{-0.76}$ kpc (cite: davies2007_rsgc2)" (Cluster membership) [from Davies et al. 2007 (cite: davies2007_rsgc2)]
- External data: Compiled optical/IR photometry used to build the SED  
  > "to the photometry compiled by (cite: humphreys2020) to construct the SED for DFK 52" (Spectral energy distribution) [from Humphreys et al. 2020 (cite: humphreys2020)]
- External data: Stellar temperature (3800 K) and luminosity (2.4e4 Lsun) in the RT model  
  > ": Physical parameters of the two-component RT model. $^a$Adapted from (cite: humphreys2020)." (Table 1) [from Humphreys et al. 2020 (cite: humphreys2020)]
- External data: Gas-to-dust ratio of 200  
  > "if a gas-to-dust ratio of 200 is assumed (cite: humphreys2020)" (Continuum) [from Humphreys et al. 2020 (cite: humphreys2020)]
- External data: Herschel/PACS point source photometry  
  > "archival measurements from the Herschel/PACS point source catalogue (cite: Marton2024_PACS_PSC)" (Spectral energy distribution) [from Marton et al. 2024 (cite: Marton2024_PACS_PSC)]

## Processing

### Calibration

- pipeline or manual: Standard ALMA calibration pipeline (version not stated)  
  > "Observations for both ALMA projects were reduced with the standard ALMA calibration pipeline (cite: Hunter2023_ALMApipeline)" (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA tclean  
  > "imaging was done with the CASA task" (Observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "using Briggs weighting and a robust parameter of 0.5" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Performed in the visibility plane  
  > "Continuum subtraction was performed in the visibility plane" (Observations)
- line free channels: Line-free channels used for continuum; 12CO spectral window omitted entirely to exclude ISM; ISM-contaminated channels excluded from line analysis (channel ranges not given)  
  > "For continuum maps, line-free channels were used in the imaging process, and the $^{12}$CO spectral window was omitted entirely to ensure the ISM was excluded." (Observations); "we identified the channels where ISM emission or absorption spatially overlaps with circumstellar CO, and did not consider them in our analysis" (Observations)
- primary beam correction: _not stated_
- array combination: Visibilities from different configurations combined in the uv-plane with antenna-specific weighting  
  > "visibilities from different configurations were combined" (Observations); "with antenna-specific weighting" (Observations)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: 1 mJy/beam (line), 20 uJy/beam (continuum)  
  > "The final brightness sensitivities are 1 mJy/beam for spectral line data and 20 $\mu$Jy/beam for the continuum." (Observations)

### Inherited from earlier work

- Dust temperature and mass derivation for clumps follows the methods used for VY CMa and NML Cyg (dust emissivity beta = 0.9)  
  > "Following the methods of (cite: ogorman2015) and (cite: debeck2025_nmlcyg) for VY CMa and NML Cyg and using a dust grain emissivity of $\beta=0.9$" (Continuum) [from O'Gorman et al. 2015 (cite: ogorman2015); De Beck et al. 2025 (cite: debeck2025_nmlcyg)]
- Equatorial density enhancement set-up in the LIME model is similar to an earlier model  
  > "The extended component, similar to the set-up of (cite: Sahai2022_VHya), is modelled as an equatorial density enhancement (EDE)" (Details of the 3D radiative transfer model) [from Sahai et al. 2022 (cite: Sahai2022_VHya)]
- Radiation-pressure momentum formulation and efficiency factor F  
  > "we computed the momentum it can deliver over the acceleration timescale using the formulation by (cite: val2001)" (Equatorial momentum analysis) [from Bujarrabal et al. 2001 (cite: val2001)]
- Standard ALMA calibration pipeline reduction  
  > "Observations for both ALMA projects were reduced with the standard ALMA calibration pipeline (cite: Hunter2023_ALMApipeline)" (Observations) [from Hunter et al. 2023 (cite: Hunter2023_ALMApipeline)]
- Stellar parameters and gas-to-dust ratio taken from earlier SED modelling  
  > ": Physical parameters of the two-component RT model. $^a$Adapted from (cite: humphreys2020)." (Table 1) [from Humphreys et al. 2020 (cite: humphreys2020)]

### Not stated but needed to reproduce (our reading)

- CASA version and ALMA pipeline version
- Names of the two 12m array configurations and the ACA execution details (dates, number of antennas, on-source time)
- Weights and scaling used for the antenna-specific weighting when combining 12m and ACA data
- Which channels were excluded for ISM contamination and which were line-free for the continuum
- Cell size, image size, masks, cleaning threshold, deconvolver and final beam sizes
- Primary beam correction and how the ACA/12m flux scales were checked
- Flux calibrator, flux scale uncertainty, and any self-calibration
- Apertures or regions used to measure the total and clump (A, B, C) continuum fluxes
- Dust opacity law normalisation (kappa at 1.3 mm) used for the dust masses, beyond beta = 0.9
- How the LIME model parameters (r_EDE, sigma_EDE, opening angle, masses, velocities) were chosen or fitted, and LIME grid, population and image settings
- Turbulent or line-broadening parameters, and CO abundance justification in the LIME model
- Photometry list and fitting used for the SED and for the 50 K cold-dust temperature
- Method for scaling the LIME model to the total outflow mass of 0.35 Msun, and the 12CO/13CO ratio channel selection

## Analysis recipe

1. **Image continuum and measure total flux and substructure**: 1.3 mm continuum map made from line-free channels with the 12CO window excluded; total flux and substructures (clumps A, B, arc C, extended N-S component) measured  
  > "The total continuum flux is $17.2\pm1.7$ mJy." (Continuum); "Together, these structures account for ${\sim}$15% of the total flux." (Continuum)
   - software: CASA tclean
   - parameter: Briggs robust 0.5; continuum sensitivity 20 uJy/beam  
  > "using Briggs weighting and a robust parameter of 0.5" (Observations); "20 $\mu$Jy/beam for the continuum" (Observations)
   - fitting: _not stated_
   - validation: Flux recovery checked by comparing images with and without ACA data: ~100% for lines, 80% for continuum in the main-array data  
  > "the total flux recovery is ${\sim}100$% for spectral lines and 80% for the continuum in the main-array dataset." (Observations)
2. **Derive dust temperature and mass of continuum clumps A, B, C**: Dust temperature and mass derived following the VY CMa / NML Cyg methods with beta = 0.9  
  > "Following the methods of (cite: ogorman2015) and (cite: debeck2025_nmlcyg) for VY CMa and NML Cyg and using a dust grain emissivity of $\beta=0.9$" (Continuum)
   - parameter: beta = 0.9; plane-of-sky offsets A ~1.0'', B ~2.1'', C ~3.2''  
  > "This assumes that the A, B, and C continuum components are situated at offsets of $\Delta_{\mathrm{A}}\approx1.0^{\prime\prime}$, $\Delta_{\mathrm{B}}\approx2.1^{\prime\prime}$, and $\Delta_{\mathrm{C}}\approx3.2^{\prime\prime}$ in the plane of the sky" (Continuum)
   - assumption: Optically thin emission; clumps at the stated plane-of-sky offsets; distance 5.8 kpc  
  > "and that their emission is optically thin" (Continuum); "assuming the cluster distance of 5.8 kpc" (Continuum)
   - fitting: _not stated_
   - validation: Masses compared with dust clumps around VY CMa (M ~ 1e-4 Msun)  
  > "These masses are comparable to the estimates for continuum dust clumps around VY CMa" (Continuum)
3. **Estimate total dust and envelope mass from the total continuum flux and SED**: Same method applied to the total ALMA flux with an average dust temperature of 50 K from the far-IR SED peak; gas mass from a gas-to-dust ratio of 200  
  > "Using the same method as before, but for the total ALMA flux, and adopting an average dust temperature of 50 K (inferred from the far-IR SED peak)." (Continuum)
   - parameter: Cold dust peak ~70 um, T ~50 K; spectral index alpha ~3 from ALMA flux to PACS 120 um  
  > "a cold dust component maximum at $\sim70\,\mu$m, yielding a temperature of $\sim50$ K" (Spectral energy distribution); "a linear interpolation from the total ALMA flux to the PACS 120 $\mu$m yields an estimate of $\alpha\approx3$" (Spectral energy distribution)
   - assumption: Gas-to-dust ratio of 200; optically thin dust (alpha ~ 3); dust emission dominated by a cold detached component  
  > "if a gas-to-dust ratio of 200 is assumed (cite: humphreys2020)" (Continuum); "we suggest that the dust emission is dominated by a cold detached component" (Continuum)
   - fitting: _not stated_
   - validation: _not stated_
4. **Characterise SiO and 12CO morphology and kinematics**: Systemic velocity and stellar position from the unresolved parabolic SiO J=5-4 line; 12CO moment maps, channel maps and a position-velocity diagram along the bar at PA = 143 deg  
  > "we measure the systemic velocity $v_{sys}=109\pm1.2$ km s$^{-1}$" (Molecular emission); "the position-velocity (PV) diagram for $^{12}$CO taken along the bar, where a shell shape is clearly seen extending to $v_{\mathrm{sys}}\pm27$ km s$^{-1}$." (Molecular emission)
   - parameter: Bar along PA = 143 deg; line widths Delta v10% ~54 km/s (CO) and ~20 km/s (SiO)  
  > "We identify a bar-like structure extending along position angle $\mathrm{PA}=143^{\circ}$ and across the stellar position." (Molecular emission); "the CO line width of $\Delta v_{10\%}\approx54$ km s$^{-1}$" (Molecular emission)
   - assumption: SiO emission is optically thick thermal emission at the stellar position; bar interpreted as a detached disk-like structure viewed edge-on  
  > "This is consistent with optically thick thermal emission at the stellar position" (Molecular emission); "This pattern suggests that the bar represents a detached disk-like structure viewed edge-on." (Molecular emission)
   - fitting: _not stated_
   - validation: _not stated_
5. **Model the two CO components with 3D radiative transfer**: Two-component LIME model: slow spherical wind with constant mass-loss rate plus a fast detached equatorial density enhancement (Gaussian in radius and height) viewed edge-on, compared with 12CO along the bar PA  
  > "we reproduced the two components outlined above using the radiative transfer (RT) software LIne Modeling Engine (LIME 1.9.5)" (Molecular emission); "In the two-component LIME model, the central component is treated as a spherically symmetric expanding wind with constant mass-loss rate." (Details of the 3D radiative transfer model)
   - software: LIME
   - parameter: Mdot = 3e-6 Msun/yr and v = 10 km/s (central); M_EDE = 0.05 Msun, v = 27 km/s (equatorial); EDE centre at 4'' (4000 yr)  
  > "a fast (27 km s$^{-1}$) detached equatorial component with $M{\sim}0.05$ $M_{\odot}$ and a slow (10 km s$^{-1}$) spherical envelope with $\dot{M}\sim3\times10^{-6}$ $M_{\odot}$ yr$^{-1}$" (abstract)
   - parameter: Torus radius 23000 au; torus height 4000 au (opening angle ~10 deg); T_min = 15 K; power-law temperature slope alpha = 1  
  > "for a torus height of 4000 au ($\approx 10^{\circ}$) and a radius of 23000 au" (Equatorial momentum analysis); "A minimum kinetic temperature, $T_{\mathrm{min}}=15$ K, is also needed" (Details of the 3D radiative transfer model)
   - assumption: Collisionally dominated excitation; the two components do not overlap spatially at any velocity; power-law temperature profile from stellar temperature and radius  
  > "The excitation is collisionally dominated, and the observations indicate that the components do not overlap spatially at any velocity" (Details of the 3D radiative transfer model); "The temperature profile for both structures is a power law in radius with log-slope $\alpha=1$, based on the stellar temperature and radius." (Details of the 3D radiative transfer model)
   - fitting: _not stated_
   - validation: Compared model with observed average surface brightness, radial distribution and normalised line profile; model misses the blueshifted torus side and emission between the components  
  > "is successful at reproducing the average surface brightness and radial distribution of emission both in the compact and extended regions along the position angle of the bar structure" (Molecular emission); "First, the blueshifted side of the torus emission is largely missing from the observational data." (Molecular emission)
6. **Scale the LIME model to the total detached outflow mass**: LIME model (15% of total line flux) scaled to estimate the cumulative mass of detached high-velocity components, then compared with the continuum-derived mass  
  > "the model can be scaled to provide a very rough estimate of the cumulative mass in the detached high-velocity components surrounding DFK 52" (Molecular emission); "Doing so offers a total mass of ${\sim}$0.35 $M_{\odot}$" (Molecular emission)
   - software: LIME
   - assumption: CO excitation conditions are common between the many extended density structures  
  > "If we assume the excitation conditions of CO are common between the many extended density structures" (Molecular emission)
   - fitting: _not stated_
   - validation: Within a factor of four of the continuum-derived mass  
  > "which is within a factor of four agreement with the estimate obtained from the continuum flux" (Molecular emission)
7. **Measure 12CO/13CO ratio to test a stellar origin**: Compared 13CO and 12CO emission in high signal-to-noise channels free of ISM contamination  
  > "comparison of the $^{13}$CO and $^{12}$CO emission across the high signal-to-noise ratio channels free of ISM contamination leads to $^{12}$CO/$^{13}$CO$\approx5$" (Discussion)
   - fitting: _not stated_
   - validation: _not stated_
8. **Test whether radiation pressure can drive the equatorial outflow**: Compare the equatorial linear momentum with the radiative momentum P = F L t_acc / c to derive the required efficiency factor F  
  > "$P = F \cdot P_{\mathrm{rad}} = F \cdot L \cdot t_{\mathrm{acc}} / c$" (Equatorial momentum analysis)
   - parameter: L = 2e4 Lsun; acceleration time 1000 years  
  > "Assuming the current luminosity of $2 \times 10^4\,L_\odot$ and an acceleration time of 1000 years" (Equatorial momentum analysis)
   - assumption: Equatorial outflow ejected over 1000 years; F is a lower limit because the torus intercepts only ~9% of stellar radiation  
  > "so the $F$ calculated above for DFK 52 must be considered a lower limit" (Equatorial momentum analysis); "the EDE could intercept only about 9% of the total stellar radiation" (Equatorial momentum analysis)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Imaging with tclean (Briggs weighting, robust 0.5)  
  > "imaging was done with the CASA task" (Observations)
- **ALMA calibration pipeline** : Calibration of both ALMA projects  
  > "were reduced with the standard ALMA calibration pipeline (cite: Hunter2023_ALMApipeline)" (Observations)
- **LIME** 1.9.5: 3D radiative transfer modelling of the 12CO emission  
  > "the radiative transfer (RT) software LIne Modeling Engine (LIME 1.9.5)" (Molecular emission)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total 1.3 mm continuum flux | 17.2 | 1.7 | mJy | 1 | The total continuum flux is $17.2\pm1.7$ mJy. |
| Dust temperature of clump A | 102 | 9 | K | 2 | we derive dust temperatures $T_{\mathrm{A}}\approx102\pm9$ K, $T_{\mathrm{B}}\approx76\pm7$ K, and $T_{\mathrm{C}}\approx63\pm6$ K |
| Dust temperature of clump B | 76 | 7 | K | 2 | we derive dust temperatures $T_{\mathrm{A}}\approx102\pm9$ K, $T_{\mathrm{B}}\approx76\pm7$ K, and $T_{\mathrm{C}}\approx63\pm6$ K |
| Dust temperature of clump C | 63 | 6 | K | 2 | we derive dust temperatures $T_{\mathrm{A}}\approx102\pm9$ K, $T_{\mathrm{B}}\approx76\pm7$ K, and $T_{\mathrm{C}}\approx63\pm6$ K |
| Dust mass of clump A | 1.7e-4 | 0.36e-4 | Msun | 2 | dust mass estimates $M_{\mathrm{A}}\approx(1.7\pm0.36)\times10^{-4}\,M_{\odot}$, $M_{\mathrm{B}}\approx(1.1\pm0.24)\times10^{-4}\,M_{\odot}$, and $M_{\mathrm{C}}\approx(4.4\pm0.95)\times10^{-4}\,M_{\odot}$ |
| Dust mass of clump B | 1.1e-4 | 0.24e-4 | Msun | 2 | dust mass estimates $M_{\mathrm{A}}\approx(1.7\pm0.36)\times10^{-4}\,M_{\odot}$, $M_{\mathrm{B}}\approx(1.1\pm0.24)\times10^{-4}\,M_{\odot}$, and $M_{\mathrm{C}}\approx(4.4\pm0.95)\times10^{-4}\,M_{\odot}$ |
| Dust mass of clump C | 4.4e-4 | 0.95e-4 | Msun | 2 | dust mass estimates $M_{\mathrm{A}}\approx(1.7\pm0.36)\times10^{-4}\,M_{\odot}$, $M_{\mathrm{B}}\approx(1.1\pm0.24)\times10^{-4}\,M_{\odot}$, and $M_{\mathrm{C}}\approx(4.4\pm0.95)\times10^{-4}\,M_{\odot}$ |
| Total dust mass (T = 50 K) | 6.6e-3 | 0.7e-3 | Msun | 3 | This gives $M_{\mathrm{d}}\approx(6.6\pm0.7)\times10^{-3}\,M_{\odot}$, or a total envelope mass of $1.3$ $M_{\odot}$ if a gas-to-dust ratio of 200 is assumed (cite: humphreys2020). |
| Total envelope mass from continuum (gas-to-dust 200) | 1.3 | not stated | Msun | 3 | or a total envelope mass of $1.3$ $M_{\odot}$ if a gas-to-dust ratio of 200 is assumed (cite: humphreys2020) |
| SED spectral index (ALMA to PACS 120 um) | ~3 | not stated | dimensionless | 3 | a linear interpolation from the total ALMA flux to the PACS 120 $\mu$m yields an estimate of $\alpha\approx3$ |
| Systemic velocity from SiO | 109 | 1.2 | km/s | 4 | we measure the systemic velocity $v_{sys}=109\pm1.2$ km s$^{-1}$ |
| Stellar position (J2000) | 18h39m23.406s, -06d02m16.12s | not stated | hms, dms | 4 | stellar position $\alpha_{\mathrm{J2000}}=18\mathrm{h}39\mathrm{m}23.406\mathrm{s}$, $\delta_{\mathrm{J2000}}=-06^{\circ}02'16.12''$ |
| 12CO line width Delta v10% | ~54 | not stated | km/s | 4 | the CO line width of $\Delta v_{10\%}\approx54$ km s$^{-1}$ traces gas that moves $\sim$2.5 times faster than SiO ($\Delta v_{10\%}\approx20$ km s$^{-1}$). |
| SiO line width Delta v10% | ~20 | not stated | km/s | 4 | the CO line width of $\Delta v_{10\%}\approx54$ km s$^{-1}$ traces gas that moves $\sim$2.5 times faster than SiO ($\Delta v_{10\%}\approx20$ km s$^{-1}$). |
| Position angle of the bar-like 12CO structure | 143 | not stated | deg | 4 | We identify a bar-like structure extending along position angle $\mathrm{PA}=143^{\circ}$ and across the stellar position. |
| Radial extent of 12CO J=2-1 structures | 45,000 | not stated | au | 4 | The physical radial extent of $^{12}$CO $J=2-1$ structures is 45,000 au. |
| Mass-loss rate of slow central component (LIME) | 3e-6 | not stated | Msun/yr | 5 | a slow (10 km s$^{-1}$) spherical envelope with $\dot{M}\sim3\times10^{-6}$ $M_{\odot}$ yr$^{-1}$ |
| Equatorial component mass (LIME) | 0.05 | not stated | Msun | 5 | a fast (27 km s$^{-1}$) detached equatorial component with $M{\sim}0.05$ $M_{\odot}$ |
| Equatorial component expansion velocity | 27 | not stated | km/s | 5 | a fast (27 km s$^{-1}$) detached equatorial component |
| Central component expansion velocity | 10 | not stated | km/s | 5 | a slow (10 km s$^{-1}$) spherical envelope |
| Age of the dramatic mass-loss event | ~4000 | not stated | yr | 5 | This suggests that DFK 52 underwent a dramatic mass-loss event $\sim$4000 years ago |
| Fraction of total 12CO line flux reproduced by the LIME model | 15 | not stated | % | 5 | it reproduces 15% of the total line flux |
| Total mass of detached high-velocity components from scaled LIME model | ~0.35 | not stated | Msun | 6 | Doing so offers a total mass of ${\sim}$0.35 $M_{\odot}$ |
| 12CO/13CO ratio | ~5 | not stated | dimensionless | 7 | leads to $^{12}$CO/$^{13}$CO$\approx5$ |
| Linear momentum of the equatorial outflow | 2.7e38 | not stated | g cm/s | 8 | is approximately $2.7 \times 10^{38}\,\mathrm{g\,cm\,s^{-1}}$ |
| Radiative momentum P_rad | 8.05e37 | not stated | g cm/s | 8 | the resulting radiative momentum is $P_{\mathrm{rad}} \approx 8.05 \times 10^{37}\,\mathrm{g\,cm\,s^{-1}}$ and the implied efficiency factor is $F \approx 3.35$. |
| Implied radiation-pressure efficiency factor F | ~3.35 | not stated | dimensionless | 8 | the resulting radiative momentum is $P_{\mathrm{rad}} \approx 8.05 \times 10^{37}\,\mathrm{g\,cm\,s^{-1}}$ and the implied efficiency factor is $F \approx 3.35$. |
| Total mass in extended outflow regions | 0.1-1 | not stated | Msun | 0 | We conservatively estimate a total mass of $0.1-1$ $M_{\odot}$ in the complex extended regions of the outflow. |

## Qualitative findings

- No centrally peaked continuum source is found at the stellar position  
  > "Notably, no centrally peaked continuum source is found at the position of the star" (Continuum)
- The CO morphology is highly asymmetric with arcs, loops and a bar-like structure, and no local maximum at the stellar position  
  > "The CO morphology is highly asymmetric, containing numerous arcs, loops, and roughly linear components." (Molecular emission); "No local maximum is measured at the stellar position." (Molecular emission)
- Continuum clumps A and B have no CO counterparts, possibly due to channels lost to ISM contamination  
  > "the A and B dust clumps have no counterparts in CO. This may result from the missing channels contaminated by the ISM." (Molecular emission)
- The blueshifted side of the torus emission is missing, implying an azimuthal density asymmetry  
  > "so we conclude that there is an azimuthal density asymmetry in this structure" (Molecular emission)
- None of the other RSGC2 sample sources show similar morphology  
  > "none of the other sources in the RSGC2 sample show morphology anywhere similar to this" (Discussion)

## Claim tuples

- H: Is the circumstellar environment of DFK 52 unusually large compared with other extreme RSGs? | E: Imaged 1.3 mm continuum and 12CO J=2-1 with 12m + ACA and measured radial extents at 5.8 kpc | R: Continuum extends to ~50,000 au and 12CO to 45,000 au, about four times the extent in VY CMa and NML Cyg | F: The outflow size is unprecedented among known RSGs despite a lower stellar luminosity | **supported**
- H: Can a fast detached equatorial component plus a slow spherical wind explain the molecular emission? | E: Two-component LIME model compared with 12CO along the bar position angle | R: Reproduces average surface brightness and radial distribution along the bar PA but only 15% of the total line flux, and misses the blueshifted torus side | F: The molecular emission is only partially reproduced by the two-component model | **partially**
- H: How much mass is in the extended outflow? | E: Dust mass from continuum with T = 50 K and gas-to-dust 200; scaled LIME CO model | R: 1.3 Msun from continuum and ~0.35 Msun from the scaled CO model, within a factor of four | F: Total mass of 0.1-1 Msun in the extended regions (conservative) | **partially**
- H: Is the extended emission stellar in origin rather than an intra-cluster ISM structure? | E: Compared 13CO and 12CO in ISM-free channels and compared RSGC2 sources | R: 12CO/13CO ~5 and no other RSGC2 source shows similar morphology | F: The molecular emission is of stellar origin | **supported**
- H: Could radiation pressure drive the equatorial ejection? | E: Compared equatorial momentum (2.7e38 g cm/s) with radiative momentum for L = 2e4 Lsun over 1000 yr | R: Required efficiency F ~ 3.35 versus an expected 0.09-0.17 | F: An alternate ejection mechanism, such as a binary interaction or merger, is needed; the specific mechanism cannot yet be identified | **partially**

## Reasoning

- Why this data: The ACA follow-up was designed to recover extended emission missed by the 12m configurations  
  > "targeted only DFK 52 with the Atacama Compact Array (ACA) to recover all of the extended emission" (Observations)
- Why this method: Cold detached dust was assumed because of the large physical scales, the double-peaked SED, and the absence of mid-IR excess or mm emission at the star  
  > "Considering the large physical scales in the ALMA image, the secondary peak in the SED, and the lack of mid-IR excess or millimetre emission at the stellar position" (Continuum)
- Alternative: Large-scale emission as interaction of a stellar outflow with a quiescent local intra-cluster density structure; disfavoured by 12CO/13CO ~5 and by the unique morphology among RSGC2 members  
  > "it is possible that the large-scale emission represents interactions between a stellar outflow and a quiescent local density structure in the intra-cluster medium." (Discussion); "This low ratio supports a stellar origin of the presented molecular emission" (Discussion)
- Alternative: Foreground (non-member) star or AGB star alternative; rejected in favour of cluster membership  
  > "For these reasons, we argue for the current assignment that DFK 52 is indeed a cluster member" (Cluster membership)
- Alternative: Radiation pressure as driver of the equatorial outflow; judged insufficient  
  > "This supports the conclusion that an alternate ejection mechanism must be invoked to explain the formation of the EDE observed." (Equatorial momentum analysis)
- How they decided it was enough: _not stated_
- Limitation (authors): ISM contamination in CO forced exclusion of channels  
  > "A common feature across all ALMA observations of RSGC2 was a significant amount of contamination from the interstellar medium (ISM) in CO." (Observations)
- Limitation (authors): LIME model covers only a small fraction of the outflow  
  > "Because the LIME model was constructed to fit only a small fraction of the observed outflow at a specific position angle, it reproduces 15% of the total line flux." (Molecular emission)
- Limitation (authors): Full 3D model of the extended material not possible because of its geometrical complexity  
  > "a full 3D model of the extended material is not yet possible due to the very high degree of geometrical complexity" (Details of the 3D radiative transfer model)
- Limitation (authors): Cluster membership and distance are uncertain  
  > "but a more accurate distance measurement is needed to confirm this" (Cluster membership)
- Limitation (authors): Spectral indices of individual continuum components are unavailable  
  > "Although the spectral indices of the individual continuum components are unavailable with the current ALMA observations" (Spectral energy distribution)
- Caveat (inferred, ours): Dust masses depend on an unstated dust opacity normalisation and on assumed plane-of-sky offsets and optical thinness
- Caveat (inferred, ours): Total envelope mass relies on a literature gas-to-dust ratio of 200 and a single 50 K temperature
- Caveat (inferred, ours): LIME parameters appear hand-tuned with no stated fit, uncertainties or goodness-of-fit
- Caveat (inferred, ours): The model reproduces only 15% of line flux, so scaling to total mass is very rough
- Caveat (inferred, ours): Excluding ISM-contaminated channels may bias the CO mass and morphology
- Caveat (inferred, ours): All physical scales and masses depend on the assumed cluster distance of 5.8 kpc

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Exact LIME input parameters and model files, and how they were tuned
- Missing: Imaging parameters beyond robust = 0.5 (cell, size, masks, thresholds, beam)
- Missing: Channel selection to avoid ISM contamination
- Missing: Flux measurement regions for clumps A, B, C and dust opacity law
- Missing: Software versions for CASA and the pipeline
- Data volume (inferred): Tens to a few hundred GB raw for 12m (13 targets, 2 configs) plus ACA; a few GB of calibrated measurement sets for DFK 52 alone
- Score (inferred): 2/5, Project codes and key numbers are given, but imaging settings, channel selection, LIME parameter choice and dust opacity are not specified, and the RT model is not fitted in a reproducible way.
- Rediscovery candidate: no, The paper does not state that the data are public, and the recipe lacks imaging details, line-free channels and a defined model-fitting procedure, so the main results cannot be redone to a numeric key.

## Links

- Method: Hunter et al. 2023 (cite: Hunter2023_ALMApipeline) (ALMA calibration pipeline used for both projects)
- Method: Brinch & Hogerheijde 2010 (cite: Brinch2010_LIME) (LIME radiative transfer code)
- Method: O'Gorman et al. 2015 (cite: ogorman2015) (Method for dust temperature and mass from continuum)
- Method: Sahai et al. 2022 (cite: Sahai2022_VHya) (Set-up for the equatorial density enhancement model)
- Method: Bujarrabal et al. 2001 (cite: val2001) (Radiation-pressure momentum formulation)
- Companion: Humphreys et al. 2020 (cite: humphreys2020) (Earlier mid-IR SED study of RSGC2 members providing photometry and stellar parameters)
- Companion: De Beck et al. 2025 (cite: debeck2025_nmlcyg) (NML Cyg comparison and dust method)
- Companion: Kaminski 2019 (cite: kaminski_vycma_2019) (VY CMa continuum comparison)
- Related: ALMA 2023.1.01519.S (13 RSGs in RSGC2)
- Related: ALMA 2024.A.00018.S (ACA follow-up of DFK 52)

## Checks

```json
{
 "quotes": 140,
 "quotes_ok": 140,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 28,
 "numeric_problems": 0,
 "fill": {
  "facts": 107,
  "stated": 73,
  "rate": 0.682
 },
 "evidence_ok": true
}
```
