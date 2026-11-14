# The ALMaQUEST Survey. XIII. Understanding Radial Trends in Star Formation Quenching via the Relative Roles of Gas Availability and Star Formation Efficiency

`2024ApJ...964..120P` | The Astrophysical Journal 2024 | first author: Pan, Hsi-An | arXiv: 2402.07400 | DOI: 10.3847/1538-4357/ad28c1

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type large_program_or_survey

## Science

- Fields: nearby_galaxies
- Question: How do radial profiles of star formation, gas fraction and star formation efficiency change as galaxies move from the star-forming main sequence toward the green valley, and which driver (f_gas or SFE) dominates the suppression of sSFR at different galactocentric radii?  
  > "we investigate the changes in molecular gas and star formation properties as galaxies transit from the star-forming main sequence to the passive regime." (abstract); "Analysis of relative contributions of $f_\mathrm{gas}$ and SFE to $\Sigma_\mathrm{sSFR}$ uncovers a diverse range of quenching modes." (abstract)
- Target **ALMaQUEST main sample (46 MaNGA galaxies: 34 non-starburst, 12 central starburst)**: coordinates _not stated_; z/distance redshift ~0.03 (stated for the 1.5 Re scale)  
  > "The 46 galaxies consist of 34 non-starburst and 12 starburst galaxies." (The ALMaQUEST Survey); "($\sim$ 7 kpc at redshift 0.03)" (Radial Profiles of $\Sigma_{\ast}$, $\Sigma_\mathrm{H2}$ and $\Sigma_\mathrm{SFR}$); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.01225.S, 2017.1.01093.S, 2018.1.00541.S, 2018.1.00558.S
- bands: _not stated_
- frequencies and spectral setup: 12CO(J=1-0) at 115.271 GHz; velocity resolution of the data cube 11 km/s  
  > "115.271 GHz) were designed to match the point-spread function" (Molecular Gas Observations: ALMA); "$\delta v$ $=$ 11 km s$^{-1}$ is the velocity resolution of the data cube" (Molecular Gas Observations: ALMA)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 2.5 arcsec, designed to match the MaNGA PSF  
  > "point-spread function (2.5$\ensuremath{''}$) of the MaNGA observations" (Molecular Gas Observations: ALMA)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: PI: L. Lin (2015.1.01225.S, 2017.1.01093.S, 2018.1.00558.S); PI: S. Ellison (2018.1.00541.S)  
  > "PI: L. Lin – 2015.1.01225. S, 2017.1.01093.S, 2018.1.00558.S; PI: S. Ellison – 2018.1.00541.S" (Molecular Gas Observations: ALMA)
- Line: 12CO J = 1-0 (115.271 GHz)
- Other facility **MaNGA (SDSS-IV) with Pipe3D value-added products (DR15)**: Spaxel-based stellar mass, extinction-corrected Halpha and other emission-line fluxes, D4000, used for Sigma_star and Sigma_SFR  
  > "The MaNGA data used in this study are obtained from the MaNGA DR15 `Pipe3D` value-added products (cite: San18)." (Star Formation Tracers: MaNGA); "we adopt H$\alpha$ emission as a tracer of ongoing star formation activity." (Star Formation Tracers: MaNGA)
- Other facility **SDSS imaging**: gri composite images shown for example galaxies  
  > "The right panel exhibits the SDSS $gri$ composite image of the galaxy" (Relative Importance of $f_\mathrm{gas}$ and SFE in Quenching)
- External data: MaNGA DR15 Pipe3D value-added products (stellar mass, emission lines, global properties)  
  > "The MaNGA data used in this study are obtained from the MaNGA DR15 `Pipe3D` value-added products (cite: San18)." (Star Formation Tracers: MaNGA) [from (cite: San18)]
- External data: Halpha luminosity to SFR calibration  
  > "The extinction-corrected H$\alpha$ luminosity is converted to the SFR using the calibration provided by (cite: Ken98)." (Star Formation Tracers: MaNGA) [from (cite: Ken98)]
- External data: Global star-forming main sequence relation and its scatter (+-0.32 dex)  
  > "the global star-forming main sequence and its typical scatter of $\pm$0.32 dex for the MaNGA sample, as determined by (cite: San19)" (Sample Classification) [from (cite: San19)]
- External data: CO-to-H2 conversion factor alpha_CO = 4.35 Msun (K km/s pc^2)^-1  
  > "using a constant Milky Way conversion factor ($\alpha_\mathrm{CO}$) of 4.35 M$_{\odot}$ (K km s$^{-1}$ pc$^{2}$)$^{-1}$ (cite: Bol13)" (Molecular Gas Observations: ALMA) [from (cite: Bol13)]
- External data: Milky Way extinction curve with R_V = 3.1 for the Balmer decrement correction  
  > "The correction is based on a Milky Way extinction curve with a standard reddening parameter $R_{V}$ of 3.1 (cite: Car89)." (Star Formation Tracers: MaNGA) [from (cite: Car89)]
- External data: Hubble T-types from the MaNGA Deep Learning Morphology catalogue  
  > "The T-type values for the ALMaQUEST galaxies are taken from the MaNGA Deep Learning Morphology Value Added Catalogue (cite: Dom22)." (Footnote 3) [from (cite: Dom22)]
- Simulation/model as data: Literature results from FIRE, Illustris, IllustrisTNG, EAGLE and SIMBA used for qualitative comparison (no simulations run in this paper)  
  > "Several recent studies have explored $\Sigma_\mathrm{sSFR}$ in simulated green-valley galaxies using galaxy simulations such as FIRE, Illustris, IllustrisTNG, EAGLE, and SIMBA" (Comparison with Simulations)

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

- ALMA data reduction and imaging  
  > "Detailed information regarding ALMA data reduction and imaging can be found in the survey paper by (cite: Lin20)." (Molecular Gas Observations: ALMA) [from survey paper (cite: Lin20)]
- Spaxel classification by powering source (BPT, EW cuts)  
  > "we follow the method outlined in our previous papers (cite: Blu20a; Lin22)" (Star Formation Tracers: MaNGA) [from (cite: Blu20a; Lin22)]
- Sigma_SFR for non-star-forming spaxels from the Sigma_sSFR-D4000 relation  
  > "as employed in previous MaNGA and ALMaQUEST papers (cite: Spi18; Wan19; Blu20a; Tho22)" (Star Formation Tracers: MaNGA) [from (cite: Spi18; Wan19; Blu20a; Tho22)]
- Fully-quenched spaxels assigned fixed log(Sigma_sSFR) = -12  
  > "following (cite: Blu20a)" (Star Formation Tracers: MaNGA) [from (cite: Blu20a)]
- Constant alpha_CO adopted for consistency  
  > "a constant $\alpha_\mathrm{CO}$ is adopted in this work to maintain consistency with previous ALMaQUEST papers" (Molecular Gas Observations: ALMA) [from previous ALMaQUEST papers (cite: Ell21a; Lin20; Ell23)]
- Ranking of drivers via the Delta f_gas - Delta SFE expression  
  > "This expression allows for a ranking of the two drivers (cite: Ell20a; Bro20; Mor21; Tho22; Gar23)" (Relative Importance of $f_\mathrm{gas}$ and SFE in Quenching) [from (cite: Ell20a; Bro20; Mor21; Tho22; Gar23)]
- Central region defined as R < 0.5 Re  
  > "is also consistent with the analysis taken in previous ALMaQUEST papers (cite: Ell20a; Lin22)" (Relative Importance of $f_\mathrm{gas}$ and SFE at Different Radial Range) [from (cite: Ell20a; Lin22)]
- Selection of the 12 central starburst galaxies  
  > "by at least 50% (cite: Ell20a)" (The ALMaQUEST Survey) [from (cite: Ell20a)]

### Not stated but needed to reproduce (our reading)

- ALMA band, array configurations, integration times, sensitivities and observing dates (all deferred to Lin20)
- CASA version, calibration and imaging recipe (task, weighting, robust, cell size, masking, deconvolution) for the CO cubes
- How CO integrated intensity maps were made from the cubes and how they were matched to the MaNGA spaxel grid and PSF
- Per-galaxy rms noise of the CO cubes used for upper limits and the S/N definition of the CO map
- Effective radius Re, inclination and position-angle sources and their values per galaxy
- Exact SFR calibration coefficient and the Pipe3D table columns used
- D4000 binning of the median Sigma_sSFR-D4000 relation
- How per-radial-bin uncertainties of the profiles and of Delta f_gas - Delta SFE were computed beyond the stated error propagation
- Azimuthal binning scheme that yields the 198 bins
- Criteria and per-galaxy assignment of the visual single-mode vs multiple-driver classification

## Analysis recipe

1. **Derive Sigma_star and Sigma_SFR from MaNGA Pipe3D**: Use Pipe3D spaxel stellar mass and extinction-corrected Halpha (Balmer decrement) converted to SFR, with spaxel area and inclination correction  
  > "we utilize the spaxel-based stellar mass and SFR measurements from `Pipe3D`, taking into account the physical area of the spaxel and applying an inclination correction." (Star Formation Tracers: MaNGA); "The extinction-corrected H$\alpha$ luminosity is converted to the SFR using the calibration provided by (cite: Ken98)." (Star Formation Tracers: MaNGA)
   - software: Pipe3D
   - parameter: R_V = 3.1 Milky Way extinction curve  
  > "The correction is based on a Milky Way extinction curve with a standard reddening parameter $R_{V}$ of 3.1 (cite: Car89)." (Star Formation Tracers: MaNGA)
   - assumption: Salpeter IMF  
  > "A Salpeter initial mass function (cite: Sal55) is assumed in this work." (Introduction)
   - assumption: Cosmology H0 = 70 km/s/Mpc, Omega_m = 0.3, Omega_Lambda = 0.7  
  > "$H_\mathrm{0}$ = 70 km s$^{-1}$ Mpc$^{-1}$, $\Omega_\mathrm{m}$ = 0.3, and $\Omega_\mathrm{\Lambda}$ = 0.7." (Introduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Classify spaxels and assign Sigma_sSFR for non-star-forming and quenched spaxels**: BPT plus Halpha EW cuts define star-forming, AGN-contaminated, retired and fully-quenched spaxels; for non-star-forming spaxels with D4000 < 1.45 Sigma_sSFR is read from the median Sigma_sSFR-D4000 relation built from star-forming spaxels of the 34 non-starburst galaxies, then multiplied by Sigma_star; fully-quenched spaxels fixed at log(Sigma_sSFR/yr^-1) = -12  
  > "We first construct the $\Sigma_\mathrm{sSFR}$-D4000 relation for our sample using star-forming spaxels from the 34 non-starburst star forming galaxies." (Star Formation Tracers: MaNGA); "Then, we convert the $\Sigma_\mathrm{sSFR}$ to $\Sigma_\mathrm{SFR}$ by multiplying it with the $\Sigma_{\ast}$ value of these spaxels." (Star Formation Tracers: MaNGA); "the fully-quenched spaxels are artificially assigned to a fixed value of log($\Sigma_\mathrm{sSFR}$/yr$^{-1}$) $=$ $-$12" (Star Formation Tracers: MaNGA)
   - parameter: BPT limited to S/N > 2 for all required emission lines  
  > "Our BPT analysis is limited to spaxels with a signal-to-noise ratio (S/N) greater than 2 for all required emission lines." (Star Formation Tracers: MaNGA)
   - parameter: Star-forming spaxels: BPT star-forming and Halpha EW > 6 A  
  > "are defined as those satisfying both the BPT star-forming criteria and an H$\alpha$ equivalent width (EW) greater than 6Å (cite: San20; San21)" (Star Formation Tracers: MaNGA)
   - parameter: Retired spaxels: S/N > 2 and EW < 3 A in Halpha  
  > "are identified as those having S/N $>$ 2 and EW $<$ 3 Å in H$\alpha$ (cite: Lin22)" (Star Formation Tracers: MaNGA)
   - parameter: D4000 < 1.45 calibration limit; fully-quenched: S/N < 2 in Halpha or D4000 > 1.45  
  > "Therefore, we only utilize the $\Sigma_\mathrm{sSFR}$-D4000 calibration for spaxels with D4000 $<$ 1.45." (Star Formation Tracers: MaNGA); "as those having S/N $<$ 2 in H$\alpha$ or D4000 $>$ 1.45" (Star Formation Tracers: MaNGA)
   - assumption: Sigma_SFR of AGN-contaminated and retired spaxels is inferred from D4000, trading accuracy for completeness  
  > "some accuracy is traded for completeness" (Star Formation Tracers: MaNGA)
   - fitting: _not stated_
   - validation: Relation compared with the full MaNGA sample; conclusions re-checked excluding fully-quenched spaxels  
  > "is consistent with that derived from the full MaNGA sample (cite: Blu20a; Tho22)" (Star Formation Tracers: MaNGA); "we have verified that our conclusions remain qualitatively consistent even when excluding the fully-quenched spaxels" (Star Formation Tracers: MaNGA)
3. **Derive Sigma_H2 from CO(1-0) with upper limits for non-detections**: Convert 12CO(1-0) luminosity to molecular mass surface density with a constant alpha_CO; assign 3 sigma upper limits to spaxels with S/N < 2 in the CO integrated intensity map  
  > "a 3$\sigma$ upper limit is assigned to spaxels with S/N $<$ 2 in CO integrated intensity map." (Molecular Gas Observations: ALMA); "The 3$\sigma$ upper limits of flux are calculated with $3\sigma\times{\sqrt{\delta v \Delta V}}$" (Molecular Gas Observations: ALMA)
   - software: CASA
   - parameter: alpha_CO = 4.35 Msun (K km/s pc^2)^-1  
  > "using a constant Milky Way conversion factor ($\alpha_\mathrm{CO}$) of 4.35 M$_{\odot}$ (K km s$^{-1}$ pc$^{2}$)$^{-1}$" (Molecular Gas Observations: ALMA)
   - parameter: delta v = 11 km/s; assumed line width Delta V = 40 km/s  
  > "$\delta v$ $=$ 11 km s$^{-1}$ is the velocity resolution of the data cube" (Molecular Gas Observations: ALMA); "$\Delta V$ is the assumed 40 km s$^{-1}$ line width for a bulk of molecular cloud observed at kpc resolution" (Molecular Gas Observations: ALMA)
   - assumption: Constant Milky Way alpha_CO; metallicity-dependent alpha_CO changes global M_H2 by ~0.1 dex on average  
  > "is approximately 0.1 dex" (Molecular Gas Observations: ALMA)
   - fitting: Local line width checked by pixel-by-pixel Gaussian fitting and by CASA immoment (moment 2); both give median ~40 km/s  
  > "Both methods show a median line width of $\sim$40 km s$^{-1}$." (Molecular Gas Observations: ALMA)
   - validation: _not stated_
4. **Classify galaxies by global sSFR**: Split the 34 non-starburst galaxies into SF_h, SF_m, SF_l by global sSFR; the 12 central starbursts (cSB) form a separate class  
  > "For the 34 non central starburst galaxies, there are a total of 12 galaxies classified as SF$_{h}$, 11 galaxies classified as SF$_{m}$, and 11 galaxies classified as SF$_{l}$." (Sample Classification); "The sample classification is defined by the absolute value of global sSFR" (Table 1)
   - parameter: SF_h: log(sSFR/yr^-1) > -10.5; SF_m: -11.0 to -10.5; SF_l: < -11.0  
  > "The sample classification is defined by the absolute value of global sSFR" (Table 1)
   - fitting: _not stated_
   - validation: _not stated_
5. **Build radial profiles of Sigma_SFR, Sigma_star, Sigma_H2, Sigma_sSFR, f_gas and SFE**: Deproject using inclination and position angle; take the median of all valid spaxels (measured, inferred or upper limits) in each deprojected annulus; median of individual profiles per subset  
  > "is considered to deproject the geometries of the galaxies" (Radial Profiles of $\Sigma_{\ast}$, $\Sigma_\mathrm{H2}$ and $\Sigma_\mathrm{SFR}$); "The radial quantities are determined by calculating the median value" (Radial Profiles of $\Sigma_{\ast}$, $\Sigma_\mathrm{H2}$ and $\Sigma_\mathrm{SFR}$); "Additionally, we examine the molecular gas fraction ($f_\mathrm{gas}$) defined as $\Sigma_\mathrm{H2}$/$\Sigma_{\ast}$ and the star formation efficiency (SFE) defined as $\Sigma_\mathrm{SFR}$/$\Sigma_\mathrm{H2}$." (Radial Profiles of $f_\mathrm{gas}$, SFE, and $\Sigma_\mathrm{sSFR}$)
   - parameter: 0.18 Re (~0.8 kpc) radial steps out to 1.5 Re (~7 kpc at z = 0.03)  
  > "The radial profile is sampled with a 0.18 $R_\mathrm{e}$ ($\sim$ 0.8 kpc) steps within 1.5 $R_\mathrm{e}$" (Radial Profiles of $\Sigma_{\ast}$, $\Sigma_\mathrm{H2}$ and $\Sigma_\mathrm{SFR}$)
   - parameter: Shaded height = standard error of the mean at each radial bin  
  > "The height of the shaded regions represents the standard error of the mean at each radial bin." (Radial Profiles of $\Sigma_{\ast}$, $\Sigma_\mathrm{H2}$ and $\Sigma_\mathrm{SFR}$)
   - fitting: _not stated_
   - validation: SF_h and SF_m Sigma_sSFR profiles compared with Blu20b, derived from the full MaNGA DR15 sample  
  > "The comparison validates that the $\Sigma_\mathrm{sSFR}$ trends of the ALMaQUEST sample" (Radial Profiles of $f_\mathrm{gas}$, SFE, and $\Sigma_\mathrm{sSFR}$)
6. **Quantify the relative role of f_gas and SFE via Delta f_gas - Delta SFE**: For each SF_m and SF_l galaxy, compute the deviation of Sigma_sSFR, f_gas and SFE from the SF_h median at each radial bin, then take Delta f_gas - Delta SFE (positive = primarily SFE-driven, negative = primarily f_gas-driven)  
  > "Similarly, we compute the radial $\Delta$$f_\mathrm{gas}$ and $\Delta$SFE using the same approach." (Relative Importance of $f_\mathrm{gas}$ and SFE in Quenching); "specifically the value of the expression $\Delta$$f_\mathrm{gas}$$-$$\Delta$SFE" (Relative Importance of $f_\mathrm{gas}$ and SFE in Quenching)
   - parameter: Combined-driver band -0.15 < Delta f_gas - Delta SFE < 0.15, about twice the typical uncertainty  
  > "The limit of $\pm$0.15 is approximately twice the typical uncertainty of the $\Delta$$f_\mathrm{gas}$$-$$\Delta$SFE profiles." (Relative Importance of $f_\mathrm{gas}$ and SFE in Quenching)
   - fitting: Uncertainty by error propagation from the uncertainties of the raw curves  
  > "is determined through error propagation from the uncertainties of the raw curves." (Relative Importance of $f_\mathrm{gas}$ and SFE in Quenching)
   - validation: _not stated_
7. **Classify individual galaxies and tally drivers by radial range**: Visually classify the 22 quenching galaxies as single-mode or multiple-driver from the Delta profiles; histogram the drivers over 198 azimuthal bins, split into central (R < 0.5 Re, 66 bins) and disk (R > 0.5 Re, 132 bins)  
  > "we undertake a visual classification of galaxies into two distinct groups based on the number of dominant factors influencing star formation within their galactic disks." (Relative Importance of $f_\mathrm{gas}$ and SFE in Individual Galaxies); "illustrates the distribution of the different drivers across 198 azimuthal bins in the 22 quenching galaxies." (Relative Importance of $f_\mathrm{gas}$ and SFE at Different Radial Range)
   - parameter: A bin counts as equally driven when Delta f_gas - Delta SFE is zero or its uncertainty encompasses +-0.15  
  > "or when the associated uncertainty encompasses $\pm$0.15, the region is considered to be equally influenced by both drivers." (Relative Importance of $f_\mathrm{gas}$ and SFE at Different Radial Range)
   - fitting: _not stated_
   - validation: Alternative central definition R < 1.0 Re changes the fractions but not the relative ordering of categories  
  > "We have evaluated our results using an alternative definition of the center as $R$ $<$ 1.0$R_\mathrm{e}$." (Relative Importance of $f_\mathrm{gas}$ and SFE at Different Radial Range)
8. **Compare with literature simulations**: Qualitative comparison of observed radial Sigma_sSFR, Sigma_H2 and f_gas profiles with published results from FIRE, Illustris, IllustrisTNG, EAGLE and SIMBA  
  > "Several recent studies have explored $\Sigma_\mathrm{sSFR}$ in simulated green-valley galaxies using galaxy simulations such as FIRE, Illustris, IllustrisTNG, EAGLE, and SIMBA" (Comparison with Simulations)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **Pipe3D** : Value-added MaNGA DR15 products: stellar mass, emission-line fluxes and spaxel SFR inputs  
  > "The MaNGA data used in this study are obtained from the MaNGA DR15 `Pipe3D` value-added products (cite: San18)." (Star Formation Tracers: MaNGA)
- **CASA (immoment)** : Moment 2 map to measure local CO line width  
  > "the CASA task `immoment` (moment 2)" (Molecular Gas Observations: ALMA)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Fully-quenched spaxel fixed value | -12 | not stated | log(Sigma_sSFR/yr^-1) | 2 | the fully-quenched spaxels are artificially assigned to a fixed value of log($\Sigma_\mathrm{sSFR}$/yr$^{-1}$) $=$ $-$12 |
| Median log Sigma_sSFR of star-forming spaxels at D4000 = 1.45 | -10.7 | not stated | log(yr^-1) | 2 | with a median value of -10.7 |
| Fraction of spaxels with a valid Sigma_SFR | ~98 | not stated | percent | 2 | ensures that $\sim$ 98% of spaxels have a valid $\Sigma_\mathrm{SFR}$ value |
| Median CO line width (two methods) | ~40 | not stated | km/s | 3 | Both methods show a median line width of $\sim$40 km s$^{-1}$. |
| Difference in global M_H2 using metallicity-dependent alpha_CO | ~0.1 | not stated | dex | 3 | is approximately 0.1 dex |
| Median log SFE of SF_h galaxies | -9.5 to -9.0 | not stated | log(yr^-1) | 5 | The median log(SFE/yr$^{-1}$) for SF$_{h}$ galaxies ranges from approximately $-$9.5 to $-$9.0 |
| Disk SFE offset of SF_m below SF_h | 0.2 | not stated | dex | 5 | While the disk SFE of SF$_{m}$ is lower than that of SF$_{h}$ by only 0.2 dex |
| SFE suppression of SF_l relative to SF_h | at least an order of magnitude | not stated | dimensionless | 5 | is significantly suppressed by at least an order of magnitude compared to normal star-forming galaxies |
| cSB Sigma_sSFR enhancement over SF_h (innermost region / R > 0.75 Re) | ~0.5 / ~0.3 | not stated | dex | 5 | cSB galaxies exhibit an enhancement in $\Sigma_\mathrm{sSFR}$ of approximately 0.5 dex in the innermost region and a consistently smaller enhancement of approximately 0.3 dex in the $R$ $>$ 0.75 $R_\mathrm{e}$ regime. |
| Single-mode galaxies (4 SF_m, 6 SF_l; 1 f_gas-driven, 9 SFE-driven) | 10 | not stated | galaxies | 7 | we identify 10 galaxies (4 SF$_{m}$ and 6 SF$_{l}$; 1 $f_\mathrm{gas}$-driven and 9 SFE-driven) categorized as being driven by a single mode |
| Multiple-driver galaxies (7 SF_m, 5 SF_l) | 12 | not stated | galaxies | 7 | and 12 galaxies (7 SF$_{m}$ and 5 SF$_{l}$) classified as being influenced by multiple modes |
| All radial bins: SFE-dominated fraction | ~51 | not stated | percent | 7 | SFE emerges as the dominant factor, accounting for approximately 51% in determining the $\Sigma_\mathrm{sSFR}$. |
| All radial bins: equal f_gas and SFE fraction / f_gas-driven fraction | ~40 / 9 | not stated | percent | 7 | constituting approximately 40%, while cases primarily driven by $f_\mathrm{gas}$ account for only 9% |
| Central region (R < 0.5 Re, 66 bins): SFE-driven / combined / f_gas-driven | 66 / 29 / 5 | not stated | percent | 7 | with SFE driving 66% of radial regions, the combination of $f_\mathrm{gas}$ and SFE playing a significant role in 29% of the regions, and $f_\mathrm{gas}$ being the primary driver in 5% of cases |
| Disk region (R > 0.5 Re, 132 bins): combined / SFE-driven / f_gas-driven | 47 / 43 / 10 | not stated | percent | 7 | $f_\mathrm{gas}$ and SFE are equally important in driving star formation in 47% of the radial bins; SFE takes the lead as the dominant factor in 43% of these radial bins, with $f_\mathrm{gas}$ remaining the least common driver, accounting for only 10% of the regions in the disk region. |

## Qualitative findings

- Median Sigma_star and Sigma_H2 profiles overlap among SF_h, SF_m, SF_l, while Sigma_SFR decreases from SF_h to SF_l at almost all radii  
  > "show no significant variation among the three populations." (Summary)
- Radial Sigma_sSFR, f_gas and SFE decrease with decreasing global sSFR across radii; inside-out quenching supported for these massive galaxies  
  > "Our findings also support an inside-out quenching scenario for these relatively massive galaxies." (Summary)
- SF_l galaxies show lower Sigma_H2 at R < 1.0 Re mainly because of CO non-detections  
  > "This reduction in $\Sigma_\mathrm{H2}$ is attributed to the significant presence of CO non-detection in this region" (Radial Profiles of $\Sigma_{\ast}$, $\Sigma_\mathrm{H2}$ and $\Sigma_\mathrm{SFR}$)

## Claim tuples

- H: Radial profiles of star formation and molecular gas properties change systematically with distance from the star-forming main sequence | E: Median radial profiles of Sigma_sSFR, f_gas and SFE for SF_h, SF_m, SF_l and cSB galaxies out to 1.5 Re | R: Profiles decrease in magnitude from SF_h to SF_l at almost all radii; Sigma_star and Sigma_H2 medians largely overlap | F: Quenching is global with an inside-out signature, and both f_gas and SFE are suppressed | **supported**
- H: Quenching galaxies are each dominated by a single driver (f_gas or SFE) | E: Visual classification of Delta f_gas - Delta SFE radial profiles of 22 SF_m and SF_l galaxies | R: 10 galaxies single-mode (9 SFE-driven, 1 f_gas-driven) and 12 multiple-driver | F: Diverse quenching modes exist, from galaxy to galaxy and within galaxies | **supported**
- H: The dominant quenching driver depends on galactocentric radius | E: Histogram of drivers over 198 radial bins, central (R < 0.5 Re) vs disk (R > 0.5 Re) | R: Center: 66% SFE-driven; disk: 47% combined f_gas and SFE, 43% SFE | F: Central suppression is mainly from reduced SFE; in the disk both f_gas and SFE contribute | **supported**
- H: Observed radial profiles agree with galaxy simulations | E: Qualitative comparison with published simulations (FIRE, Illustris, TNG, EAGLE, SIMBA) | R: Simulations predict both inside-out and outside-in quenching and a central drop in Sigma_H2 and f_gas that observations do not show | F: Discrepancies likely from AGN and star formation prescriptions and observational limits | **partially**

## Reasoning

- Why this data: ALMaQUEST was designed for resolved molecular gas properties matched to MaNGA  
  > "was specifically designed to study the resolved molecular gas properties of various types of galaxies" (Introduction)
- Why this method: Per-galaxy, resolved analysis avoids dilution from averaging over whole galaxies or the whole sample  
  > "To avoid the potential dilution of key physical processes that may occur when averaging properties across entire galaxies" (Relative Importance of $f_\mathrm{gas}$ and SFE in Quenching)
- Alternative: Metallicity-dependent alpha_CO considered; rejected for consistency with previous ALMaQUEST papers  
  > "Given the small difference, a constant $\alpha_\mathrm{CO}$ is adopted in this work to maintain consistency with previous ALMaQUEST papers." (Molecular Gas Observations: ALMA)
- Alternative: Alternative central-region definition R < 1.0 Re tested  
  > "We have evaluated our results using an alternative definition of the center as $R$ $<$ 1.0$R_\mathrm{e}$." (Relative Importance of $f_\mathrm{gas}$ and SFE at Different Radial Range)
- How they decided it was enough: _not stated_
- Limitation (authors): Sigma_SFR for AGN-contaminated and retired spaxels is D4000-inferred and should be interpreted with caution  
  > "Thus, the $\Sigma_\mathrm{SFR}$ values of these spaxels should be interpreted with caution." (Star Formation Tracers: MaNGA)
- Limitation (authors): f_gas profile of SF_l galaxies cannot be determined precisely because of many CO non-detections  
  > "we are not able to precisely quantifying their $f_\mathrm{gas}$ profile due to a significant number of CO non-detections" (Radial Profiles of $f_\mathrm{gas}$, SFE, and $\Sigma_\mathrm{sSFR}$)
- Limitation (authors): Small sample limits identification of the origin of multi-mode drivers  
  > "Given the small size of our sample in this work, it is challenging to pinpoint the exact underlying origin of the multiple-mode drivers" (Relative Importance of $f_\mathrm{gas}$ and SFE in Quenching)
- Limitation (authors): Constant alpha_CO may be wrong in the inner 1 kpc  
  > "galaxies often exhibit a decrease in $\alpha_\mathrm{CO}$ within the inner 1 kpc (cite: San13)" (Molecular Gas Observations: ALMA)
- Caveat (inferred, ours): Only 22 quenching galaxies; per-radius driver fractions have no stated uncertainties or significance tests
- Caveat (inferred, ours): Visual single-mode vs multiple-driver classification is subjective and not reproducible without the criteria
- Caveat (inferred, ours): The fixed -12 value for fully-quenched spaxels and the 3 sigma CO upper limits, taken as the value in the medians, bias Sigma_sSFR and f_gas
- Caveat (inferred, ours): The 2.5 arcsec beam (~1 kpc) smooths the central region where SFE-driven suppression is claimed
- Caveat (inferred, ours): Global-sSFR classification into SF_h/SF_m/SF_l uses absolute boundaries that map to DeltaMS only approximately

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA calibration, imaging and CO moment-map recipe (deferred to Lin20)
- Missing: Data availability statement and derived tables not given in this paper
- Missing: Per-galaxy Re, inclination and position angles
- Missing: Criteria for the visual driver classification and azimuthal bin definition
- Missing: No analysis code released
- Data volume (inferred): ALMA 12CO(1-0) cubes for 46 galaxies from four projects (probably tens of GB raw; MaNGA Pipe3D tables are small)
- Score (inferred): 2/5, The paper analyses published ALMaQUEST CO cubes and Pipe3D products with clear spaxel-level recipes, but ALMA processing is deferred to Lin20, no code or data release is stated, and key classification steps are visual.
- Rediscovery candidate: no, Public availability of the data is not stated in the paper and the ALMA processing and visual classification cannot be redone from the text alone.

## Links

- Method: (cite: Lin20) (ALMaQUEST survey paper holding ALMA data reduction and imaging details)
- Method: (cite: Blu20a) (Spaxel classification and D4000-based Sigma_sSFR method)
- Method: (cite: San18) (Pipe3D value-added products)
- Companion: (cite: Ell20a) (Central starburst sample and f_gas versus SFE analysis)
- Companion: (cite: Lin22) (Earlier ALMaQUEST quenching study of green-valley galaxies)
- Companion: (cite: Tho22) (ALMaQUEST merger sample, relative roles of f_gas and SFE)
- Companion: (cite: Lin24) (Companion dense-gas study (HCN, HCO+) of selected ALMaQUEST galaxies)
- Related: ALMaQUEST
- Related: MaNGA (SDSS-IV)

## Checks

```json
{
 "quotes": 107,
 "quotes_ok": 107,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 15,
 "numeric_problems": 0,
 "fill": {
  "facts": 111,
  "stated": 64,
  "rate": 0.577
 },
 "evidence_ok": true
}
```
