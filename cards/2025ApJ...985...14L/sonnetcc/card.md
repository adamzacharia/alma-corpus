# Cloud-scale Gas Properties, Depletion Times, and Star Formation Efficiency per Freefall Time in PHANGS─ALMA

`2025ApJ...985...14L` | The Astrophysical Journal 2025 | first author: Leroy, Adam K. | arXiv: 2502.04481 | DOI: 10.3847/1538-4357/adbcab

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type large_program_or_survey

## Science

- Fields: nearby_galaxies, star_formation
- Question: How do the regional mass-weighted cloud-scale (60-150 pc) molecular gas properties (surface density, velocity dispersion, virial parameter, free-fall time) relate to molecular gas depletion time and star formation efficiency per free-fall time in 1.5 kpc regions across PHANGS-ALMA galaxies?  
  > "Then we test how $\tau_{\rm dep}^{\rm mol}$ and $\epsilon_{\rm ff}^{\rm mol}$ vary as functions of the regional mass-weighted mean molecular gas properties on cloud scales (60–150 pc)" (abstract)
- Target **PHANGS–ALMA galaxy sample (67 galaxies, 841 regions after selection)**: coordinates _not stated_; z/distance d <~ 20 Mpc (nearby sample; per-galaxy distances not listed)  
  > "PHANGS–ALMA targeted nearby ($d \lesssim 20$ Mpc), low to moderately inclined ($i \lesssim 75^\circ$)" (2 Data and methods); "We adopt distances and orientation parameters for all PHANGS–ALMA targets as measured and compiled by (cite: LANG20KINEMATICS; ANAND21DISTANCES; PHANGSALMA21SURVEY)." (2 Data and methods); distance from LANG20KINEMATICS; ANAND21DISTANCES; PHANGSALMA21SURVEY  
  > "PHANGS–ALMA targeted nearby ($d \lesssim 20$ Mpc), low to moderately inclined ($i \lesssim 75^\circ$)" (2 Data and methods); "We adopt distances and orientation parameters for all PHANGS–ALMA targets as measured and compiled by (cite: LANG20KINEMATICS; ANAND21DISTANCES; PHANGSALMA21SURVEY)." (2 Data and methods)

## Data provenance

- ALMA projects: 2012.1.00650.S, 2013.1.00803.S, 2013.1.01161.S, 2015.1.00121.S, 2015.1.00782.S, 2015.1.00925.S, 2015.1.00956.S, 2016.1.00386.S, 2017.1.00392.S, 2017.1.00766.S, 2017.1.00886.L, 2018.1.01321.S, 2018.1.01651.S, 2018.A.00062.S, 2019.1.01235.S, 2019.2.00129.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: PHANGS-ALMA data include short- and zero-spacing data (arrays not itemised)  
  > "This total flux is well-measured by summing the PHANGS–ALMA data, which include short- and zero-spacing data, without any aggressive high resolution masking." (2.3 Data selection and completeness)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Fiducial 150 pc (FWHM physical beam); 120, 90 and 60 pc also used for fewer galaxies  
  > "cloud-scale (physical beam size $\ell = 150$ pc) imaging" (3.1 Cloud-scale gas properties); "PHANGS–ALMA also represents the largest survey of CO from galaxies at $120$ pc, $90$ pc, and $60$ pc resolution" (Appendix: PHANGS–ALMA at higher resolution)
- max recoverable scale: _not stated_
- sensitivity: Sensitive to individual ~1e5 Msun GMCs per 60-150 pc beam; CO-bright at 150 pc defined as > 0.6 K km/s, about 3x typical rms integrated intensity noise  
  > "PHANGS–ALMA has sensitivity to detect individual $\sim 10^{5}$ M$_\odot$ GMCs in each $60{-}150$ pc beam" (2.3 Data selection and completeness); "CO bright emission visible to PHANGS–ALMA at 150 pc would be defined as $> 0.6$ K km s$^{-1}$, or about $3\times$ the typical rms integrated intensity noise." (Appendix: Procedure to replicate)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: ALMA data processed as part of the PHANGS–ALMA CO (2-1) survey; analysis uses PHANGS high-level products (mega-tables)  
  > "This paper makes use of the following ALMA data, which have been processed as part of the PHANGS–ALMA CO (2-1) survey:" (Acknowledgments); "We conduct our analysis using the high-level data products" (2 Data and methods)
- Line: CO 2-1 (not stated)
- Other facility **Ground-based narrowband H-alpha**: Default Sigma_SFR tracer (with WISE 22 um); maps from A. Razza et al. (in preparation)  
  > "By default, we estimate $\Sigma_{\rm SFR}$ combining H$\alpha$ narrowband measurements and WISE $22\mu$m mid-infrared emission." (2.2 Star formation rate per unit gas)
- Other facility **WISE**: 22 um (WISE4) maps for Sigma_SFR; 3.4-22 um images compiled by LEROY19Z0MGS  
  > "using narrowband H$\alpha$ maps from A. Razza et al. (in preparation) and $22\mu$m WISE4 maps from (cite: LEROY19Z0MGS)" (2.2 Star formation rate per unit gas)
- Other facility **GALEX**: FUV emission combined with WISE 22 um for Sigma_SFR when H-alpha maps are unavailable  
  > "When H$\alpha$ maps are not available, we instead combine GALEX FUV emission and WISE 22$\mu$m emission" (2.2 Star formation rate per unit gas)
- Other facility **IRAC 3.6 um**: 3.6 um images listed among the core data sets aggregated in the mega-tables (specific use not stated here)  
  > "IRAC $3.6\mu$m images" (2 Data and methods)
- External data: PHANGS mega-tables: per-hexagon CO-derived cloud-scale properties, SFR and gas masses  
  > "Calculations and database described in detail in (cite: SUN22CLOUDS) and (cite: SUN23SFGAS)." (Table 1 notes); "They break galaxies into individual sub-galactic regions and then measure a rich set of galaxy structural, stellar, and ISM properties in each region." (2 Data and methods) [from (cite: SUN22CLOUDS; SUN23SFGAS)]
- External data: CO-to-H2 conversion prescription alpha_CO^2-1 (metallicity, emissivity and excitation terms)  
  > "we adopt the new CO-to-H$_2$ conversion factor $\alpha_{\rm CO}^{2-1}$ recommended by (cite: SCHINNERER24REVIEW)" (2.1 Cloud-scale gas properties) [from (cite: SCHINNERER24REVIEW)]
- External data: Emissivity (starburst) term of alpha_CO from dust-based estimates; ~0.2 dex scatter quoted  
  > "who find $\approx 0.2$ dex scatter between their dust-based $\alpha_{\rm CO}^{2-1}$ and the fit to local conditions that we employ" (2.4 Correlation analysis, binning, fitting, and uncertainties) [from (cite: CHIANG24XCO)]
- External data: Sigma_SFR calibration from H-alpha plus WISE 22 um; ~0.15 dex point-to-point scatter vs MUSE  
  > "These measurements follow (cite: BELFIORE23SFRLARGE) as implemented by (cite: SUN23SFGAS)" (2.2 Star formation rate per unit gas); "found $\approx 0.15$ dex point-to-point scatter between the estimators that we use" (2.4 Correlation analysis, binning, fitting, and uncertainties) [from (cite: BELFIORE23SFRLARGE)]
- External data: Galaxy distances and orientation parameters  
  > "We adopt distances and orientation parameters for all PHANGS–ALMA targets as measured and compiled by (cite: LANG20KINEMATICS; ANAND21DISTANCES; PHANGSALMA21SURVEY)." (2 Data and methods) [from (cite: LANG20KINEMATICS; ANAND21DISTANCES; PHANGSALMA21SURVEY)]
- External data: Molecular gas scale height H_mol = 100 pc  
  > "with $H_\mathrm{mol} = 100$ pc the adopted molecular gas disk scale height (cite: HEYER15REVIEW)" (2.1 Cloud-scale gas properties) [from (cite: HEYER15REVIEW)]
- External data: Molecular Kennicutt-Schmidt power-law fit (Sigma_SFR ~ Sigma_mol^1.2) overplotted for comparison  
  > "The selected data agree well with the power-law fit by (cite: SUN23SFGAS), shown by the dashed line," (3 Results) [from (cite: SUN23SFGAS)]
- Simulation/model as data: Turbulence-regulated star formation expectation for fixed tau_ff (dashed line in the tau_dep vs alpha_vir figure)  
  > "the dashed line shows the expected relationship from (cite: PADOAN12EFF) for fixed" (3.3 Molecular gas depletion time as a function of cloud-scale virial parameter)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Uses PHANGS–ALMA high-level products (mega-tables); no ALMA calibration done in this paper  
  > "We conduct our analysis using the high-level data products" (2 Data and methods)
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
- array combination: PHANGS-ALMA data include short- and zero-spacing data  
  > "which include short- and zero-spacing data" (Footnote 4)
- smoothing: Data convolved to 150 pc (FWHM) for the fiducial cloud-scale measurement; Sigma_mol and Sigma_SFR convolved to the hexagon diameter FWHM for tau_dep  
  > "Convolve the CO or simulated molecular gas data to have a resolution of $150$ pc (FWHM)." (Appendix: Procedure to replicate); "we convolve both $\Sigma_{\rm mol}$ and $\Sigma_{\rm SFR}$ to share a matched Gaussian kernel with FWHM equal to the hex diameter" (Footnote 3)
- final beam: 150 pc physical FWHM (fiducial)  
  > "cloud-scale (physical beam size $\ell = 150$ pc) imaging" (3.1 Cloud-scale gas properties)
- final rms: CO-bright threshold > 0.6 K km/s, about 3x the typical rms integrated intensity noise at 150 pc  
  > "$> 0.6$ K km s$^{-1}$, or about $3\times$ the typical rms integrated intensity noise" (Appendix: Procedure to replicate)

### Inherited from earlier work

- Cross-scale (mass-weighted region averaging) methodology  
  > "We adopt the cross-scale methodology developed in (cite: LEROY16GMCS), (cite: LEROY17SFGAS), (cite: SCHRUBA19GMCS), (cite: SUN20PRESS) and (cite: SUN22CLOUDS)." (1 Introduction) [from (cite: LEROY16GMCS), (cite: LEROY17SFGAS), (cite: SCHRUBA19GMCS), (cite: SUN20PRESS), (cite: SUN22CLOUDS)]
- Mass-weighting scheme for line-of-sight gas properties  
  > "It has been described in detail by (cite: LEROY16GMCS; LEROY17SFGAS; UTOMO18EFF) and (cite: SUN22CLOUDS)." (3.1 Cloud-scale gas properties) [from (cite: LEROY16GMCS; LEROY17SFGAS; UTOMO18EFF) and (cite: SUN22CLOUDS)]
- Size scale R_pix definition with H_mol = 100 pc  
  > "Following (cite: SUN22CLOUDS), we take the relevant scale to be" (2.1 Cloud-scale gas properties) [from (cite: SUN22CLOUDS)]
- Completeness and inclination corrections to cloud-scale Sigma_mol and sigma_mol (lognormal PDF assumption for completeness)  
  > "Corrected for completeness and inclination following (cite: SUN22CLOUDS)." (Table 1); "Apply inclination corrections as in (cite: SUN22CLOUDS) to calculate face-on values of each quantity." (Appendix: Procedure to replicate) [from (cite: SUN22CLOUDS)]
- Effective-width line width definition sigma = I_CO / (sqrt(2 pi) I_pk)  
  > "derived from the ratio of the line integral to the peak, $\sigma \equiv I_{\rm CO} / \sqrt{2 \pi} I_{\rm pk}$" (3.2 Molecular gas depletion time as a function of cloud-scale surface density and line width) [from (cite: HEYER01GMCS; LEROY16GMCS; SUN22CLOUDS)]
- Sigma_SFR convolution to hexagon-diameter kernel and sampling at hexagon centre  
  > "as in (cite: SUN23SFGAS), we convolve both $\Sigma_{\rm mol}$ and $\Sigma_{\rm SFR}$ to share a matched Gaussian kernel with FWHM equal to the hex diameter" (Footnote 3) [from (cite: SUN23SFGAS)]
- PHANGS-ALMA CO (2-1) maps (observing, calibration, imaging done in the survey paper)  
  > "the PHANGS–ALMA CO (2-1) maps (cite: PHANGSALMA21SURVEY)" (2 Data and methods) [from (cite: PHANGSALMA21SURVEY)]

### Not stated but needed to reproduce (our reading)

- Version and exact columns of the PHANGS mega-tables used (Sun et al. 2022/2023 products) and the list of the 67 galaxies out of the 80 in the parent table
- S/N threshold and masking that define the 'high S/N mask' used for the completeness f_comp
- Geometric factor f in the alpha_vir expression and the exact face-on correction of Sigma_mol and sigma_mol
- Metallicity (Z) and stellar surface density (Sigma_star) sources used to evaluate f(Z) and g(Sigma_star) in alpha_CO
- Number of bootstrap resamples, random seed, and the exact likelihood form and prior on intrinsic scatter in the linear fits
- KDE grid size and exact settings behind the plotted median and 16-84% trends
- How hexagonal region grids are laid out and which regions overlap or are treated as independent
- Raw ALMA calibration, imaging and masking choices behind the PHANGS-ALMA maps (only available in the survey paper)
- Narrowband H-alpha maps (A. Razza et al., in preparation) are not yet published

## Analysis recipe

1. **Convert CO (2-1) intensity to molecular gas mass with a variable alpha_CO**: Local best-estimate alpha_CO^2-1 = alpha_CO,MW^1-0 x f(Z) x g(Sigma_star) x R21(Sigma_SFR)^-1 applied region by region  
  > "Calculated via $\alpha_{\rm CO,MW}^{1-0} \times f(Z) \times g(\Sigma_\star) \times R_{21}(\Sigma_{\rm SFR})^{-1}$" (Table 1)
   - parameter: alpha_CO,MW^1-0 = 4.35 Msun pc^-2 (K km/s)^-1  
  > "$=4.35\;\mbox{$\rm M_\odot~pc^{-2}\ (K~km~s^{-1})^{-1}$}$; Milky Way CO (1-0) conversion factor" (Table 1)
   - parameter: f(Z) = (Z/Zsun)^-1.5 metallicity-dependent term  
  > "$=\left(Z / Z_\odot \right)^{-1.5}$ ; metallicity-dependent" (Table 1)
   - parameter: Emissivity term alpha_CO^1-0 ~ Sigma_star^-0.25 for Sigma_star > 100 Msun pc^-2  
  > "In our prescription, $\alpha_{\rm CO}^{1-0} \propto \Sigma_\star^{-0.25}$ where $\Sigma_\star > 100$ M$_\odot$ pc$^{-2}$ (cite: CHIANG24XCO)" (3.5 The key role of the CO-to-H2 conversion factor)
   - parameter: R21 = 0.65 (Sigma_SFR / 0.018 Msun/yr/kpc2)^0.125, min 0.35, max 1.0  
  > "$=0.65 \left( \Sigma_{\rm SFR}\;/\;0.018~{\rm M}_\odot~{\rm yr}^{-1}~{\rm kpc}^{-2} \right)^{0.125}$ with min 0.35, max 1.0; CO line excitation term" (Table 1)
   - assumption: alpha_CO assumed fixed within each region when averaging  
  > "so when we conduct region-averages we assume a fixed $\alpha_{\rm CO}$ within each region." (Footnote 2)
   - fitting: _not stated_
   - validation: Analysis repeated with a fixed Milky Way alpha_CO  
  > "we repeat our analysis using a fixed $\alpha_{\rm CO}$ instead of our best estimate" (3.5 The key role of the CO-to-H2 conversion factor)
2. **Measure cloud-scale gas properties along each CO-detected line of sight at 150 pc**: Per sightline: Sigma_mol, effective-width sigma_mol, R_pix, then tau_ff and alpha_vir; face-on and completeness corrections  
  > "Within each region of each galaxy, we measure four gas properties for each individual line of sight where CO is detected." (3.1 Cloud-scale gas properties)
   - parameter: tau_ff = sqrt(3 pi / (32 G rho)), rho = 3 M_beam / (4 pi R_pix^3)  
  > "Calculated via $\tau_{\rm ff} = \sqrt{3 \pi / (32 G \rho_{\rm mol}^{\rm cloud})}$" (Table 1)
   - parameter: alpha_vir = 5 sigma^2 R_pix / (f G M_beam)  
  > "Calculated via $\alpha_{\rm vir}^{\rm cloud} = 5 \sigma^2_{\rm mol} R_{\rm pix} / (f G M_{\rm mol}^{\rm beam})$." (Table 1)
   - parameter: R_pix = (l^2 H_mol / (8 cos i))^(1/3), l = 150 pc, H_mol = 100 pc  
  > "Following (cite: SUN22CLOUDS), we take the relevant scale to be $R_{\rm pix} \equiv (\ell^2 H_{\rm mol} / (8 \cos i))^{1/3}$ at the fiducial $\ell=150$ pc resolution, with $H_{\rm mol}=100$ pc." (2.1 Cloud-scale gas properties)
   - assumption: Mass in each beam spread over the whole beam and a line-of-sight depth H_mol / cos i  
  > "This assumes that the mass measured in each beam is spread over the entire beam and over a line-of-sight depth of $H_\mathrm{mol}/\cos{i}$" (2.1 Cloud-scale gas properties)
   - assumption: alpha_vir considers only gas self-gravity  
  > "considering only gas self-gravity" (Table 1)
   - fitting: _not stated_
   - validation: Sun et al. 2022 showed a good match to an object-oriented (cloud-finding) analysis  
  > "showed a good overall match between results for an object oriented analysis, where size is measured from morphological analysis, and this sightline based approach" (2.1 Cloud-scale gas properties)
3. **Average cloud-scale properties over 1.5 kpc hexagonal regions with mass weighting**: Each sightline weighted by local gas surface density within each hexagon; tau_ff averaged harmonically so tau_dep ~ <tau_ff> for fixed eps_ff  
  > "Then, we weight each line of sight by the local gas surface density to derive mass-weighted, region-averaged molecular gas properties." (3.1 Cloud-scale gas properties); "In the case of $\tau_{\rm ff}^{\rm mol}$, calculate the average via" (Appendix: Procedure to replicate)
   - parameter: Hexagonal apertures 1.5 kpc diameter (1 kpc for the 120/90/60 pc samples)  
  > "Divide the target region or galaxy into hexagonal apertures with diameter $1.5$ kpc." (Appendix: Procedure to replicate); "work with $1$ kpc diameter hexagonal regions rather than the $1.5$ kpc diameter used for the main results" (Appendix: PHANGS–ALMA at higher resolution)
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive region-level tau_dep and eps_ff**: Convolve Sigma_SFR and Sigma_mol maps to 1.5 kpc FWHM, divide for tau_dep, sample at hexagon centre; eps_ff = <tau_ff> / tau_dep  
  > "Estimate the molecular gas depletion time by convolving the $\Sigma_{\rm SFR}$ and $\Sigma_{\rm mol}$ maps to 1.5 kpc (FWHM) resolution." (Appendix: Procedure to replicate)
   - parameter: Sigma_SFR from H-alpha + WISE 22 um (default); GALEX FUV + WISE 22 um where H-alpha missing; WISE 22 um alone in a handful of cases  
  > "in a handful of cases we use only WISE $22\mu$m emission" (2.2 Star formation rate per unit gas)
   - assumption: Sigma_SFR estimators match VLT/MUSE gold-standard maps to ~0.1 dex accuracy  
  > "matches the results using the “gold standard” VLT/MUSE maps to $\approx 0.1$ dex accuracy" (2.2 Star formation rate per unit gas)
   - fitting: _not stated_
   - validation: _not stated_
5. **Select regions with adequate CO completeness**: Require cloud-scale CO flux completeness > 50% and <Sigma_mol^cloud> > 20 Msun pc^-2  
  > "Based on this figure we impose a $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$ cut at $20$ M$_\odot$ pc$^{-2}$ in addition to requiring $f_{\rm comp}^{\rm CO} > 50\%$." (2.3 Data selection and completeness)
   - parameter: 841 regions in 67 galaxies at 150 pc  
  > "Applying this criteria to the $\ell = 150$ pc resolution PHANGS–ALMA data set in (cite: SUN22CLOUDS), we select $841$ regions in $67$ galaxies." (2.3 Data selection and completeness)
   - assumption: Lognormal surface-density PDF used to correct for completeness (inherited from Sun et al. 2022)  
  > "by assuming lognormal probability distribution function for the surface density, in good agreement with observations" (2.3 Data selection and completeness)
   - fitting: _not stated_
   - validation: Cut chosen so a few high-completeness galaxies do not dominate low-Sigma bins  
  > "avoids the case where a few high completeness galaxies dominate low $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$ bins and drive our results on their own" (2.3 Data selection and completeness)
6. **Correlate and fit tau_dep and eps_ff against cloud-scale gas properties**: Spearman rank correlation plus a linear fit y = m (x - x0) + b in log-log space, treating the gas property as the independent variable; also galaxy-normalised versions and KDE median trends  
  > "We calculate $x_0$ as the median of the $x$ data, then maximize the log-likelihood to infer $m$ and $b$." (2.4 Correlation analysis, binning, fitting, and uncertainties)
   - software: scipy
   - parameter: x0 is the median of x; intrinsic scatter term included but very small; sigma reported as robust rms residual  
  > "We also include an intrinsic scatter term in the fit, but this tends to be very small given our adopted uncertainty estimates (see below)." (2.4 Correlation analysis, binning, fitting, and uncertainties)
   - parameter: Adopted uncertainties: tau_dep 0.3 dex, Sigma_mol 0.2 dex, tau_ff 0.1 dex, sigma_mol 0.15 dex  
  > "we consider any individual $\tau_{\rm dep}^{\rm mol}$ estimate to be uncertain by $\approx 0.3$ dex" (2.4 Correlation analysis, binning, fitting, and uncertainties); "we consider these $\langle \sigma_{\rm mol}^{\rm cloud} \rangle$ values to be uncertain by $\approx 0.15$ dex" (2.4 Correlation analysis, binning, fitting, and uncertainties)
   - assumption: Fit y on x (not x on y, not bivariate); results depend on this choice  
  > "Fitting $x$ as a function of $y$ or conducting a bivariate fit would yield different results." (2.4 Correlation analysis, binning, fitting, and uncertainties)
   - fitting: Maximum-likelihood linear fit with adopted uncertainties and intrinsic scatter term; per-galaxy bootstrap for fit uncertainties  
  > "where we repeatedly re-draw $N$ galaxies from the parent sample and refit the relation between $\tau_{\rm dep}^{\rm mol}$ and gas properties." (2.4 Correlation analysis, binning, fitting, and uncertainties)
   - validation: Galaxy-normalised tau_dep or eps_ff to remove galaxy-to-galaxy offsets; KDE median and 16-84% trend compared with the fits  
  > "We fit lines to the median trends, but found them to be similar to those found fitting the data and only report the fits to the data." (2.4 Correlation analysis, binning, fitting, and uncertainties)
7. **Test robustness to alpha_CO and resolution**: Repeat the analysis with a fixed Galactic alpha_CO and with 120, 90 and 60 pc cloud-scale data in 1 kpc hexagons  
  > "we repeat our analysis using a fixed $\alpha_{\rm CO}$ instead of our best estimate" (3.5 The key role of the CO-to-H2 conversion factor); "We apply the same completeness and surface density cuts, but work with $1$ kpc diameter hexagonal regions rather than the $1.5$ kpc diameter used for the main results." (Appendix: PHANGS–ALMA at higher resolution)
   - fitting: _not stated_
   - validation: Higher-resolution results consistent with the 150 pc results  
  > "Overall all three resolutions show consistent results" (Appendix: PHANGS–ALMA at higher resolution)

## Software

- **scipy** : Two-dimensional Gaussian KDE with default Scott's rule bandwidth for median and 16-84% trends  
  > "allowing the bandwidth to be chosen using the default “Scott’s rule” implement in `scipy`" (2.4 Correlation analysis, binning, fitting, and uncertainties)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of selected 1.5 kpc regions (150 pc resolution) | 841 | not stated | regions | 5 | we select $841$ regions in $67$ galaxies. |
| Number of galaxies in selected sample | 67 | not stated | galaxies | 5 | we select $841$ regions in $67$ galaxies. |
| Median star formation efficiency per free-fall time | 0.39 | not stated | percent | 6 | corresponds to $0.39\%$ of gas formed into stars per free-fall time, and we measure $\pm 0.29$ dex or a factor of $2$ scatter across the sample. |
| Scatter in eps_ff across the sample | 0.29 | not stated | dex | 6 | we measure $\pm 0.29$ dex or a factor of $2$ scatter across the sample. |
| Spearman rank correlation, tau_dep vs <tau_ff> | 0.18 | not stated | dimensionless | 6 | with Spearman rank correlation coefficient $0.18$ |
| Fit slope m, tau_dep vs <tau_ff> | 0.51 | not stated | dimensionless | 6 | relation with slope $m = 0.51$ |
| Spearman rank correlation, galaxy-normalised tau_dep vs <tau_ff> | 0.28 | not stated | dimensionless | 6 | with the rank correlation coefficient increasing to $0.28$ after normalization |
| Fit slope m, galaxy-normalised tau_dep vs <tau_ff> | 0.43 | not stated | dimensionless | 6 | $m = 0.43$, but the overall picture appears similar as in the left panel |
| Fit slope m, tau_dep vs <Sigma_mol^cloud> | -0.3 | not stated | dimensionless | 6 | fixed $\epsilon_{\rm ff}^{\rm mol}$, fixed dynamical state clouds: $m = -0.3$ for |
| Fit slope m, tau_dep vs <sigma_mol^cloud> | -0.48 | not stated | dimensionless | 6 | (compared to $-0.5$ expected) and $m = -0.48$ for |
| Fit slope m, tau_dep vs <alpha_vir^cloud> (raw and galaxy-normalised) | -0.27 (raw); -0.11 (normalised) | not stated | dimensionless | 6 | We find a best-fit slope of $m = -0.27$, though this drops to $m = -0.11$ after normalize each galaxy by its mean |
| rms scatter of individual regions about the median trend after galaxy normalisation | 0.2 | not stated | dex | 6 | with individual regions showing rms scatter $\approx 0.2$ dex about the median trend |
| Sample size at 120 pc resolution (1 kpc regions) | 966 regions in 41 galaxies | not stated | regions | 7 | our sample at $\ell = 120$ pc consists of $966$ 1 kpc regions in $41$ galaxies. |
| Sample size at 90 pc and 60 pc resolution | 552 regions in 28 galaxies (90 pc); 170 regions in 9 galaxies (60 pc) | not stated | regions | 7 | At $\ell = 90$ pc we have 552 regions in $28$ galaxies, and at $\ell = 60$ pc we have 170 regions in $9$ galaxies. |

## Qualitative findings

- Innermost 1.5 kpc regions show high Sigma_mol^cloud, sigma_mol^cloud and alpha_vir^cloud together with low tau_dep  
  > "The innermost $1.5$ kpc hexes show high $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$, high $\langle \sigma_{\rm mol}^{\rm cloud} \rangle$, high $\langle \alpha_{\rm vir}^{\rm cloud} \rangle$, and low $\tau_{\rm dep}^{\rm mol}$." (3.4 tau_dep, gas properties, and galactocentric radius)
- A fixed Milky Way alpha_CO gives nearly constant tau_dep and removes or reverses the correlations  
  > "The fixed $\alpha_{\rm CO}$ leads to a nearly constant $\tau_{\rm dep}^{\rm mol}$, in contrast to the fiducial results with our best-estimate $\alpha_{\rm CO}$." (3.5 The key role of the CO-to-H2 conversion factor)
- Surface density at 150 pc is a good predictor of the 60 pc surface density despite a 6x difference in beam area  
  > "provide an outstanding predictor of the $\ell = 60$ pc $\langle \Sigma_{\rm mol}^{\rm cloud} \rangle$ despite $6\times$ difference in beam area" (4.3 Surface density, physical density, and resolution)

## Claim tuples

- H: Denser gas (shorter cloud-scale free-fall time) has shorter molecular gas depletion time | E: Spearman correlation and linear fit of log tau_dep vs log <tau_ff> for 841 regions in 67 galaxies | R: Weak positive correlation (rank 0.18, 0.28 after galaxy normalisation); slope m = 0.51, shallower than the slope of 1 expected for fixed eps_ff | F: Density plays a role in setting star formation rate per unit gas, but the dependence is shallower than for constant eps_ff | **supported**
- H: tau_dep depends on cloud-scale surface density and velocity dispersion as expected for fixed eps_ff and dynamical state | E: Fits of log tau_dep vs log <Sigma_mol^cloud> and log <sigma_mol^cloud> | R: Anti-correlations with slopes -0.3 and -0.48, shallower than -0.5 and -1 expected | F: tau_dep anti-correlates with both quantities; tau_dep vs sigma is highlighted as a cleaner comparison because alpha_CO affects only the vertical axis | **supported**
- H: Gas with lower virial parameter forms stars faster and more efficiently, as predicted by turbulence-regulated theory | E: Compare tau_dep and eps_ff with <alpha_vir^cloud> | R: tau_dep weakly anti-correlates with alpha_vir (m = -0.27); eps_ff is nearly flat or mildly positive with alpha_vir | F: The predicted relation is not seen, likely because alpha_vir based on self-gravity alone misses stellar gravity in galaxy centres | **refuted**
- H: A single star formation efficiency per free-fall time describes the sample | E: Compute eps_ff = <tau_ff> / tau_dep per region and compare with gas properties | R: Median eps_ff 0.39% with +/- 0.29 dex scatter; almost no correlation with Sigma_mol or sigma_mol | F: A fixed eps_ff is a reasonable approximate description at the 0.3 dex level, with caveats from correlated axes | **supported**
- H: The inferred correlations depend on the adopted CO-to-H2 conversion factor | E: Repeat the analysis with a fixed Milky Way alpha_CO instead of the Schinnerer et al. 2024 prescription | R: Fixed alpha_CO yields nearly constant tau_dep and weaker or reversed correlations | F: Excitation and emissivity corrections to alpha_CO in inner galaxies are key to the results | **supported**

## Reasoning

- Why this data: PHANGS-ALMA is the largest homogeneous cloud-scale molecular gas data set in galaxies  
  > "using the largest homogeneous cloud-scale data set on molecular gas in galaxies, PHANGS–ALMA" (1 Introduction)
- Why this method: kpc-sized regions average out the time evolution of individual star-forming regions and allow lower-resolution IR SFR tracers  
  > "By working with these kpc-sized regions, we average out the time evolution of individual star-forming regions" (1 Introduction)
- Alternative: Fixed Milky Way alpha_CO run as a comparison to the fiducial variable alpha_CO  
  > "we also run our analysis using a fixed Galactic $\alpha_{\rm CO}$" (2.1 Cloud-scale gas properties)
- Alternative: Fitting x on y or a bivariate fit not adopted; would give different results  
  > "Fitting $x$ as a function of $y$ or conducting a bivariate fit would yield different results." (2.4 Correlation analysis, binning, fitting, and uncertainties)
- Alternative: Second-moment or Gaussian-fit line widths not used; effective width adopted instead  
  > "it will be interesting to explore whether other methods (e.g., second moment, gaussian model fit) show more or less anti-correlation" (4.4 tau_dep-sigma anti-correlation)
- How they decided it was enough: _not stated_
- Limitation (authors): Correlated axes when plotting eps_ff vs cloud-scale properties  
  > "we caution that comparing $\epsilon_{\rm ff}^{\rm mol}$ to cloud-scale gas properties unavoidably involves plotting highly correlated quantities against one another" (2.2 Star formation rate per unit gas)
- Limitation (authors): alpha_CO is the largest uncertainty  
  > "Finally, improved knowledge of $\alpha_{\rm CO}$ remains the single largest uncertainty." (4.6 Next steps)
- Limitation (authors): Measurements are population averages, not initial conditions and outcomes of individual clouds  
  > "We do not measure the initial conditions and final outcomes for individual clouds." (4.2 What this measurement is not)
- Limitation (authors): Fit slopes depend on the choice of dependent variable and fitting method  
  > "Again we caution that the adopted methodology affects the precise value of the fit slopes." (3.2 tau_dep vs cloud-scale surface density and line width)
- Caveat (inferred, ours): All main trends rest on one alpha_CO prescription; a fixed alpha_CO reverses several signs, so the physical conclusions are conditional on the emissivity and excitation terms
- Caveat (inferred, ours): Rank correlations are weak (0.18 to 0.31) and fit slopes depend on regression direction; no uncertainties on slopes are tabulated in the text
- Caveat (inferred, ours): Same PHANGS-ALMA sample and mega-tables as Sun et al. 2023, so results are not independent of earlier work
- Caveat (inferred, ours): Selection to high Sigma_mol regions (f_comp > 0.5) leaves leverage mostly from few galaxy-centre regions
- Caveat (inferred, ours): Effective-width line widths in galaxy centres may be biased by multiple velocity components

## Reproducibility

- Data public (paper): Full region-by-region measurement table available online as a machine-readable table; raw ALMA data public status not stated  
  > "The full table is available online as part of a machine readable table." (Table 2 notes)
- Products in archive: _not stated_
- Missing: Mega-table input products (Sun et al. 2022, 2023) are needed and are not reproduced here
- Missing: Bootstrap count, seed, likelihood and KDE grid details are not given
- Missing: Metallicity and stellar-mass-surface-density inputs to alpha_CO
- Missing: Unpublished H-alpha maps (Razza et al. in preparation)
- Missing: No code release is mentioned
- Data volume (inferred): Small (megabytes) if started from the mega-tables; many terabytes if re-deriving from raw ALMA data of 16 projects
- Score (inferred): 4/5, The paper gives a step-by-step appendix, explicit formulae and numeric fit tables, but depends on mega-tables and inputs from earlier papers and omits bootstrap and fit settings.
- Rediscovery candidate: yes, Region tables are online and the appendix gives a complete recipe; headline slopes and eps_ff are numeric, so a reproduction from the mega-tables is feasible.

## Links

- Method: (cite: SUN22CLOUDS) (Defines cloud-scale property calculation, completeness and inclination corrections, and the hexagon database)
- Method: (cite: SUN23SFGAS) (Defines kpc-scale mega-table, Sigma_SFR processing and Sigma_mol/Sigma_SFR convolution)
- Method: (cite: SCHINNERER24REVIEW) (Source of the adopted alpha_CO prescription)
- Method: (cite: PHANGSALMA21SURVEY) (PHANGS-ALMA CO (2-1) survey data and processing)
- Method: (cite: BELFIORE23SFRLARGE) (Sigma_SFR calibration from H-alpha plus 22 um)
- Companion: (cite: LEROY17SFGAS) (Earlier cross-scale tau_dep and alpha_vir study of M51)
- Companion: (cite: SCHRUBA19GMCS) (Cloud-property and star formation comparison across eight galaxies)
- Companion: (cite: TENG24XCO) (Shows alpha_CO anti-correlates with line width in PHANGS-ALMA)
- Companion: (cite: UTOMO18EFF) (Earlier PHANGS-ALMA eps_ff measurement)
- Related: PHANGS-ALMA
- Related: PHANGS mega-tables
- Related: z0MGS
- Related: HERACLES
- Related: COMING

## Checks

```json
{
 "quotes": 130,
 "quotes_ok": 130,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 16,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2019.1.01235.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 14,
 "numeric_problems": 0,
 "fill": {
  "facts": 112,
  "stated": 76,
  "rate": 0.679
 },
 "evidence_ok": true
}
```
