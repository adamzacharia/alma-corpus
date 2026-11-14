# Molecular Gas Properties on Cloud Scales across the Local Star-forming Galaxy Population

`2020ApJ...901L...8S` | The Astrophysical Journal Letters 2020 | first author: Sun, Jiayi | arXiv: 2009.01842 | DOI: 10.3847/2041-8213/abb3be

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type large_program_or_survey

## Science

- Fields: nearby_galaxies, star_formation
- Question: How do cloud-scale (~100 pc) molecular gas surface density, velocity dispersion, turbulent pressure and virial parameter vary across the local star-forming galaxy population and with galactic environment (radius, bars, spiral arms, host galaxy properties)?  
  > "In this Letter, we report measurements of the cloud-scale molecular gas surface density and velocity dispersion, as well as estimates of the turbulent pressure and the virial parameter." (Introduction); "Our results provide key empirical constraints on the physical link between molecular cloud populations and their galactic environment." (abstract)
- Target **70 PHANGS-ALMA nearby star-forming galaxies (66 used for data presentation)**: coordinates _not stated_; z/distance per-galaxy distances given in the Galaxy Sample table (column d)  
  > "We include the 70 PHANGS-ALMA galaxies that had fully-processed ALMA data by December 2019" (Data and Measurements); "(4) Distance (cite: Tully_etal_2009)" (Galaxy Sample table notes); distance from Tully et al. 2009 (Extragalactic Distance Database)  
  > "We include the 70 PHANGS-ALMA galaxies that had fully-processed ALMA data by December 2019" (Data and Measurements); "(4) Distance (cite: Tully_etal_2009)" (Galaxy Sample table notes)

## Data provenance

- ALMA projects: 2012.1.00650.S, 2013.1.01161.S, 2015.1.00925.S, 2015.1.00956.S, 2017.1.00392.S, 2017.1.00886.L, 2018.1.01321.S, 2018.1.01651.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: ALMA interferometric array combined with single dish; three nearest galaxies observed only with ACA 7-m and total power  
  > "They combine ALMA interferometric array and single dish observations to recover emission across the full range of spatial scales" (Data and Measurements); "These three very nearby galaxies are only observed by the ACA 7-m and total power telescopes." (Galaxy Sample table notes)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: native 50-150 pc; convolved to common 150 pc (70 galaxies) and 90 pc (35 galaxies)  
  > "have native spatial resolutions of $50{-}150$ pc at the distances of the target galaxies" (Data and Measurements); "We convolve the data cubes to a common $150$ pc spatial resolution to allow direct comparison between all 70 galaxies." (Data and Measurements)
- max recoverable scale: _not stated_
- sensitivity: 1 sigma noise 0.2-0.3 K per 2.5 km/s channel  
  > "$1\sigma$ noise levels of $0.2{-}0.3$ K per $2.5$ $\rm km\,s^{-1}$ channel" (Data and Measurements)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (not stated)
- Other facility **Extragalactic Distance Database (EDD)**: galaxy distances  
  > "We acknowledge the usage of the Extragalactic Distance Database" (Acknowledgments); "(4) Distance (cite: Tully_etal_2009)" (Galaxy Sample table notes)
- External data: Galaxy distances  
  > "(4) Distance (cite: Tully_etal_2009)" (Galaxy Sample table notes) [from (cite: Tully_etal_2009)]
- External data: Galaxy inclinations and position angles  
  > "(5–6) Galaxy inclination and position angle (cite: Lang_etal_2020)" (Galaxy Sample table notes) [from (cite: Lang_etal_2020)]
- External data: Galaxy global stellar mass, SFR and effective radius  
  > "(7–9) Galaxy global stellar mass, SFR, and the effective (half-mass) radius estimated from the measured stellar scale length (cite: Leroy_etal_2019)" (Galaxy Sample table notes) [from (cite: Leroy_etal_2019)]
- External data: CO(2-1)-to-CO(1-0) line ratio R21 = 0.65  
  > "Here $R_{21}=0.65$ is the adopted $\mathrm{CO}\,(2\text{--}1)$-to-$\mathrm{CO}\,(1\text{--}0)$ line ratio (cite: Leroy_etal_2013b; denBrok_etal_2020b)" (Data and Measurements) [from (cite: Leroy_etal_2013b; denBrok_etal_2020b)]
- External data: Metallicity-dependent alpha_CO prescription  
  > "We adopt a metallicity-dependent $\alpha_\mathrm{CO}$ (cite: Accurso_etal_2017):" (Data and Measurements) [from (cite: Accurso_etal_2017)]
- External data: Galaxy global mass-metallicity relation and fixed radial metallicity gradient used to estimate Z'  
  > "assuming a galaxy global mass–metallicity relation (cite: Sanchez_etal_2019) and a fixed radial metallicity gradient within a galaxy (cite: Sanchez_etal_2014)" (Data and Measurements) [from (cite: Sanchez_etal_2019; Sanchez_etal_2014)]
- External data: Bar and spiral-arm classification of galaxies  
  > "(2–3) If the galaxy has identifiable stellar bars and spiral arms (? – ambiguous; see M. Querejeta et al. 2020, in preparation)" (Galaxy Sample table notes) [from M. Querejeta et al. 2020, in preparation]
- External data: CO rotation curves used to check unresolved rotation in line widths  
  > "Using the CO rotation curves from (cite: Lang_etal_2020), we verified that unresolved rotation often represents a minor contribution to our measured line width" (3.2 Correlation with Galactocentric Radius) [from (cite: Lang_etal_2020)]

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
- masking: S/N>3.5 in three consecutive channels, expanded to adjacent S/N>2 in two successive channels  
  > "For the release that we use, the masks begin with all regions with $\text{S/N}>3.5$ in three consecutive channels." (Footnote 3); "These masks are then expanded to include all adjacent regions with $\text{S/N}>2$ in two successive channels." (Footnote 3)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: ALMA interferometric array plus single dish combined (details in A. K. Leroy et al. 2020b, in preparation)  
  > "They combine ALMA interferometric array and single dish observations to recover emission across the full range of spatial scales (see A. K. Leroy et al. 2020b, in preparation)." (Data and Measurements)
- smoothing: convolved to common 150 pc resolution (all 70 galaxies); 90 pc for a subset of 35  
  > "We convolve the data cubes to a common $150$ pc spatial resolution to allow direct comparison between all 70 galaxies." (Data and Measurements); "For a subset of 35 galaxies, we are also able to convolve the cubes to $90$ pc resolution" (Data and Measurements)
- final beam: fixed physical resolution of 150 pc (70 galaxies) and 90 pc (35 galaxies)  
  > "We convolve the data cubes to a common $150$ pc spatial resolution to allow direct comparison between all 70 galaxies." (Data and Measurements)
- final rms: _not stated_

### Inherited from earlier work

- Product creation (masking, moment maps, uncertainty maps) follows companion PHANGS-ALMA data paper  
  > "This product creation scheme closely follows and is detailed in A. K. Leroy et al. (2020b, in preparation)." (Data and Measurements) [from A. K. Leroy et al. (2020b, in preparation)]
- Interferometer plus single dish combination and data processing  
  > "They combine ALMA interferometric array and single dish observations to recover emission across the full range of spatial scales (see A. K. Leroy et al. 2020b, in preparation)." (Data and Measurements) [from A. K. Leroy et al. 2020b, in preparation]
- Effective line width definition sigma_CO = I_CO / (sqrt(2 pi) T_peak)  
  > "$\sigma_\mathrm{CO}= I_\mathrm{CO}/ (\sqrt{2\pi}\, T_\mathrm{peak})$ following (cite: Heyer_etal_2001)" (Data and Measurements) [from (cite: Heyer_etal_2001)]
- Instrumental line broadening correction of sigma_CO (equation 5 of an earlier paper; the citation is missing from the text)  
  > "is subsequently corrected for the instrumental line broadening following (see equation 5 therein)" (Data and Measurements) [from reference not given in the text (equation 5 therein)]
- Estimating local metallicity Z' from global stellar mass and effective radius  
  > "Following (cite: Sun_etal_2020), we estimate $Z'$ based on galaxy global stellar mass and effective radius" (Data and Measurements) [from (cite: Sun_etal_2020)]
- Fixed-scale (90 pc, 150 pc) measurement approach extended from the PHANGS-ALMA pilot sample  
  > "Following our analysis of the PHANGS-ALMA pilot sample of $11$ galaxies (cite: Sun_etal_2018), we derive these measurements on fixed $90$ pc and $150$ pc scales" (Introduction) [from (cite: Sun_etal_2018)]
- Density profile rho(r) proportional to r^-1 assumed for the virial parameter equation  
  > "The second equation assumes in addition that the gas structures have a density profile of $\rho(r) \propto r^{-1}$ (cite: Rosolowsky_Leroy_2006)." (Data and Measurements) [from (cite: Rosolowsky_Leroy_2006)]
- Central/disk and arm/inter-arm region definitions  
  > "The methodology closely follows (cite: Salo_etal_2015) and (cite: Herrera-Endoqui_etal_2015) and is detailed in M. Querejeta et al. (2020, in preparation)." (3.3 Correlation with Galaxy Bars and Spiral Arms) [from (cite: Salo_etal_2015); (cite: Herrera-Endoqui_etal_2015); M. Querejeta et al. (2020, in preparation)]

### Not stated but needed to reproduce (our reading)

- The calibrated, imaged and single-dish-combined CO(2-1) cubes themselves: imaging recipe, CASA version, weighting and deconvolution settings are only in the in-preparation Leroy et al. 2020b paper
- Which data release the cubes come from beyond 'internal data release v3.4', and whether that release is public
- How the noise in each cube (T_noise) was estimated and how uncertainty maps were propagated
- How T_peak was defined and the exact instrumental line-broadening correction (the reference for 'equation 5 therein' is lost)
- The convolution method and kernel used to reach the common 150 pc and 90 pc resolution
- Details of the hexagonal resampling grid (offset, orientation, exact pixel size)
- The Z' values per galaxy and the exact mass-metallicity relation parameters and gradient used for alpha_CO
- How the mass-weighted percentiles and Spearman correlations were computed (tools, handling of uncertainties)
- The exact masks of galaxy centers, disks, arm and inter-arm regions (defined in Querejeta et al. 2020, in preparation)
- Rest frequency of CO(2-1) and the velocity or spectral windows used for masks

## Analysis recipe

1. **Homogenize resolution**: Convolve the data cubes to common 150 pc (70 galaxies) and 90 pc (35 galaxies) spatial resolution  
  > "We convolve the data cubes to a common $150$ pc spatial resolution to allow direct comparison between all 70 galaxies." (Data and Measurements); "For a subset of 35 galaxies, we are also able to convolve the cubes to $90$ pc resolution" (Data and Measurements)
   - fitting: _not stated_
   - validation: _not stated_
2. **Mask cubes to detected emission**: Signal mask: S/N>3.5 in three consecutive channels, expanded to adjacent S/N>2 in two successive channels  
  > "For the release that we use, the masks begin with all regions with $\text{S/N}>3.5$ in three consecutive channels." (Footnote 3); "These masks are then expanded to include all adjacent regions with $\text{S/N}>2$ in two successive channels." (Footnote 3)
   - software: SpectralCubeTools
   - parameter: S/N>3.5 in 3 channels, then S/N>2 in 2 channels  
  > "These masks are then expanded to include all adjacent regions with $\text{S/N}>2$ in two successive channels." (Footnote 3)
   - fitting: _not stated_
   - validation: Censoring function of the mask derived analytically (Appendix) and CO flux completeness f_CO reported per galaxy  
  > "We report in Table [2](#tab:sample) (column 12) the CO flux completeness for each galaxy (the flux within the mask divided by the total flux in the data cube, or $f_\mathrm{CO}$)." (Data and Measurements)
3. **Make integrated intensity and line width maps**: Integrate masked cubes along the spectral axis to get I_CO and effective line width sigma_CO = I_CO/(sqrt(2 pi) T_peak), corrected for instrumental broadening; uncertainty maps by error propagation  
  > "We integrate the masked cubes along the spectral axis to produce the integrated intensity ($I_\mathrm{CO}$) and effective line width ($\sigma_\mathrm{CO}$) maps." (Data and Measurements); "We produce associated uncertainty maps via error propagation from the estimated noise in the cube." (Data and Measurements)
   - software: SpectralCubeTools, spectral-cube
   - assumption: Gaussian line profile so that sigma_CO equals the dispersion  
  > "Note that for a Gaussian line profile, $\sigma_\mathrm{CO}$ equals its dispersion." (Footnote 4)
   - fitting: _not stated_
   - validation: _not stated_
4. **Resample to independent sightlines**: Resample maps onto hexagonal pixels matching the beam size so measurements are nearly independent  
  > "We resample the two-dimensional maps of $I_\mathrm{CO}$, $\sigma_\mathrm{CO}$, and their uncertainties with hexagonal pixels matching the beam size." (Data and Measurements); "This ensures that the resampled measurements are nearly mutually independent." (Data and Measurements)
   - fitting: _not stated_
   - validation: _not stated_
5. **Convert to surface density and velocity dispersion**: sigma_mol = sigma_CO; Sigma_mol = alpha_CO R21^-1 I_CO with alpha_CO = 4.35 Z'^-1.6 Msun pc^-2 (K km/s)^-1 and R21 = 0.65  
  > "\Sigma_\mathrm{mol}= \alpha_\mathrm{CO}\;R_{21}^{-1}\;I_\mathrm{CO}" (Data and Measurements); "\alpha_\mathrm{CO}= 4.35\,Z'^{-1.6}" (Data and Measurements)
   - parameter: R21 = 0.65  
  > "Here $R_{21}=0.65$ is the adopted $\mathrm{CO}\,(2\text{--}1)$-to-$\mathrm{CO}\,(1\text{--}0)$ line ratio (cite: Leroy_etal_2013b; denBrok_etal_2020b)" (Data and Measurements)
   - assumption: Metallicity-dependent alpha_CO (Accurso et al. 2017) with Z' from the global mass-metallicity relation and a fixed radial gradient  
  > "assuming a galaxy global mass–metallicity relation (cite: Sanchez_etal_2019) and a fixed radial metallicity gradient within a galaxy (cite: Sanchez_etal_2014)" (Data and Measurements)
   - fitting: _not stated_
   - validation: _not stated_
6. **Derive turbulent pressure and virial parameter**: P_turb ~ rho_mol sigma_mol^2 and alpha_vir computed from Sigma_mol, sigma_mol and beam FWHM D_beam via closed-form scalings (3.3e4 kB K cm^-3 and 3.1 prefactors at Sigma=100 Msun pc^-2, sigma=10 km/s, D=150 pc)  
  > "We use $\Sigma_\mathrm{mol}$ and $\sigma_\mathrm{mol}$ to estimate the mean turbulent pressure in the molecular gas, $P_\mathrm{turb}\approx\rho_\mathrm{mol}\,\sigma_\mathrm{mol}^2$, and the virial parameter, $\alpha_\mathrm{vir}$, via" (Data and Measurements)
   - assumption: D_beam (beam FWHM) is the line-of-sight depth  
  > "Here $D_\mathrm{beam}$ denotes the beam full-width-half-maximum and is assumed to be the depth along the line of sight" (Data and Measurements)
   - assumption: Single, spherical gas structure filling each beam; density profile proportional to r^-1 for alpha_vir  
  > "Both equations assume a single, spherical gas structure filling each beam" (Data and Measurements); "The second equation assumes in addition that the gas structures have a density profile of $\rho(r) \propto r^{-1}$ (cite: Rosolowsky_Leroy_2006)." (Data and Measurements)
   - fitting: _not stated_
   - validation: Compared 90 pc and 150 pc measurements for galaxies with both; also checked unresolved rotation using CO rotation curves  
  > "However, we see little difference in the median values of $\sigma_\mathrm{mol}$ and $\alpha_\mathrm{vir}$ at the two resolutions" (3.1 Statistics of Cloud-scale Molecular Gas Properties); "Using the CO rotation curves from (cite: Lang_etal_2020), we verified that unresolved rotation often represents a minor contribution to our measured line width" (3.2 Correlation with Galactocentric Radius)
7. **Compute statistics and correlations by environment**: Area-weighted and mass-weighted percentile statistics; Spearman rank correlations; compare galaxy centers vs disks (barred and unbarred), arm vs inter-arm at fixed r_gal/R_eff, and galaxy-wide mass-weighted medians vs M*, SFR and offset from main sequence, with and without central regions  
  > "The area-weighted statistics are derived from percentiles weighted by sightline number counts, whereas the mass-weighted statistics from percentiles weighted by molecular gas mass" (Table 1 notes); "and divide the PHANGS-ALMA CO footprint into a central region and a disk region based on near infrared images." (3.3 Correlation with Galaxy Bars and Spiral Arms); "For galaxies with strong spiral arms, we further identify arm regions and the corresponding inter-arm regions covering the same $r_\mathrm{gal}$ range." (3.3 Correlation with Galaxy Bars and Spiral Arms)
   - fitting: _not stated_
   - validation: Central regions excluded to test whether galaxy-to-galaxy trends persist  
  > "Nevertheless, the overall trends persist, and the rank correlation remain significant." (3.4 Correlation with Integrated Galaxy Properties)

## Software

- **CASA** : _not stated_
- **Astropy** : _not stated_
- **spectral-cube** v0.4.5 (from citation key): _not stated_
- **SpectralCubeTools** : Python realization of the signal identification (masking) scheme and of the censoring function calculation  
  > "The `Python` realization of this signal identification scheme is available at <https://github.com/astrojysun/SpectralCubeTools>." (Footnote 3); "The `Python` realization of this censoring function calculation is available at: <https://github.com/astrojysun/SpectralCubeTools>." (Footnote 10)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Independent sightlines at 150 pc | 102 778 (70 galaxies) | not stated | dimensionless | 4 | This yields 102 778 independent measurements at $150$ pc resolution in 70 galaxies, and 79 840 measurements at $90$ pc resolution in 35 galaxies. |
| Independent sightlines at 90 pc | 79 840 (35 galaxies) | not stated | dimensionless | 4 | This yields 102 778 independent measurements at $150$ pc resolution in 70 galaxies, and 79 840 measurements at $90$ pc resolution in 35 galaxies. |
| Mass-weighted median Sigma_mol at 150 pc (full sample) | 110 | not stated | Msun pc^-2 | 7 | mass-weighted median $\Sigma_\mathrm{mol}=110\;\mbox{$\rm M_{\odot}\,pc^{-2}$}$ and mass-weighted median $\sigma_\mathrm{mol}=9.1\;\mbox{$\rm km\,s^{-1}$}$ |
| Mass-weighted median sigma_mol at 150 pc (full sample) | 9.1 | not stated | km/s | 7 | mass-weighted median $\Sigma_\mathrm{mol}=110\;\mbox{$\rm M_{\odot}\,pc^{-2}$}$ and mass-weighted median $\sigma_\mathrm{mol}=9.1\;\mbox{$\rm km\,s^{-1}$}$ |
| Range (+-3 sigma, 99.7%) of mass-weighted Sigma_mol and sigma_mol | 3.4 dex and 1.7 dex | not stated | dex | 7 | range of the mass-weighted $\Sigma_\mathrm{mol}$ and $\sigma_\mathrm{mol}$ distributions is large, $3.4$ and $1.7$ dex respectively |
| Range of turbulent pressure across the sample | 6.5 dex | not stated | dex | 7 | and turbulent pressures (6.5 dex) across the galaxies in our sample |
| Spearman rank correlation between Sigma_mol and sigma_mol | 0.77 | not stated | dimensionless | 7 | rank correlation coefficient $\rho=0.77$ |
| Mass-weighted median virial parameter alpha_vir at 150 pc | 2.7 | 1 sigma scatter 0.7 dex | dimensionless | 7 | $\alpha_\mathrm{vir}$ has a mass-weighted median value of $2.7$ and a $1\sigma$ scatter of $0.7$ dex |
| Factor by which kinetic energy exceeds gravitational binding energy (150 pc) | 1.3 | not stated | dimensionless | 7 | This means that the kinetic energy in the molecular gas on average slightly exceeds its gravitational binding energy by a factor of $1.3$ on $150$ pc scales. |
| 90 pc vs 150 pc mass-weighted median ratios for I_CO, Sigma_mol, P_turb | 1.5, 1.5, 2.0 | not stated | dimensionless | 7 | at $90$ pc scales to be moderately higher than the $150$ pc scale values by factors of $1.5$, $1.5$, and $2.0$, respectively. |
| Barred-galaxy centers vs disks, mass-weighted median Sigma_mol and sigma_mol | ~20 times and ~5 times higher | not stated | dimensionless | 7 | The centers of barred galaxies show ${\sim}20$ times higher mass-weighted median $\Sigma_\mathrm{mol}$ and ${\sim}5$ times higher mass-weighted median $\sigma_\mathrm{mol}$ compared to the disk regions |
| Arm vs inter-arm Sigma_mol ratio at fixed r_gal/R_eff | 1.5-2 | not stated | dimensionless | 7 | Molecular gas in the arm regions shows typically $1.5{-}2$ times higher $\Sigma_\mathrm{mol}$ relative to the gas in the inter-arm regions at fixed $r_\mathrm{gal}/R_\mathrm{eff}$. |
| Arm vs inter-arm sigma_mol, P_turb, alpha_vir at fixed r_gal/R_eff | ~20% higher sigma_mol, ~2-3 times higher P_turb, ~15% lower alpha_vir | not stated | dimensionless | 7 | the gas in spiral arms shows ${\sim}20\%$ higher $\sigma_\mathrm{mol}$, ${\sim}2{-}3$ times higher $P_\mathrm{turb}$, and ${\sim}15$% lower $\alpha_\mathrm{vir}$ at fixed $r_\mathrm{gal}/R_\mathrm{eff}$ |
| Galaxy-to-galaxy variation of mass-weighted median Sigma_mol and sigma_mol | 2 dex and 1 dex | not stated | dex | 7 | the mass-weighted median $\Sigma_\mathrm{mol}$ and $\sigma_\mathrm{mol}$ vary by $2$ dex and $1$ dex from galaxy to galaxy, respectively |
| Spearman correlation of galaxy-wide Sigma_mol and sigma_mol with global SFR | 0.72 and 0.58 | not stated | dimensionless | 7 | global SFR ($\rho=0.72$ and $0.58$), and offset in SFR from the local star-forming main sequence ($\Delta\text{MS}$; $\rho=0.45$ and $0.35$) |
| Spearman correlation of galaxy-wide alpha_vir with SFR and offset from main sequence | -0.44 and -0.41 | not stated | dimensionless | 7 | ($\rho=-0.44$) and $\Delta\text{MS}$ ($\rho=-0.41$) |

## Qualitative findings

- Surface density, velocity dispersion and turbulent pressure increase towards smaller galactocentric radii  
  > "Both $\Sigma_\mathrm{mol}$ and $\sigma_\mathrm{mol}$ tend to increase towards smaller $r_\mathrm{gal}/R_\mathrm{eff}$." (3.2 Correlation with Galactocentric Radius)
- Centers of barred galaxies have exceptionally high surface density and velocity dispersion, and less bound gas  
  > "are exceptionally high in the centers of barred galaxies (where the gas also appears less gravitationally bound)" (abstract)
- Galaxy-wide gas properties correlate with stellar mass, SFR and offset from the main sequence, and the correlations persist when galaxy centers are excluded  
  > "These correlations persist even when we exclude regions with extraordinary gas properties in galaxy centers, which contribute significantly to the inter-galaxy variations." (abstract)

## Claim tuples

- H: Do cloud-scale molecular gas properties vary widely across the local star-forming galaxy population? | E: Pixel-by-pixel analysis of PHANGS-ALMA CO(2-1) cubes of 70 galaxies at fixed 150 pc (and 90 pc) resolution | R: Surface density, velocity dispersion and turbulent pressure span 3.4, 1.7 and 6.5 dex | F: Cloud-scale gas properties vary dramatically across the sample | **supported**
- H: Is molecular gas on ~100 pc scales gravitationally bound? | E: Computed alpha_vir from Sigma_mol, sigma_mol and beam size assuming a beam-filling spherical structure | R: Mass-weighted median alpha_vir = 2.7 at 150 pc | F: Kinetic energy exceeds self-gravitational binding energy by a modest factor (1.3), under simplifying assumptions | **partially**
- H: Do galaxy bars and spiral arms affect cloud-scale gas properties? | E: Compared central vs disk regions in barred and unbarred galaxies, and arm vs inter-arm regions at fixed r_gal/R_eff | R: Barred-galaxy centers ~20x higher Sigma_mol and ~5x higher sigma_mol than disks; arms 1.5-2x higher Sigma_mol than inter-arm | F: Bar centers are extreme (less bound gas); spiral arms moderately enhance properties | **supported**
- H: Do galaxy-wide cloud-scale gas properties correlate with host galaxy properties? | E: Spearman correlations of galaxy mass-weighted medians with M*, SFR and offset from the main sequence, with and without central regions | R: Significant correlations (e.g. rho = 0.72 and 0.58 with SFR for Sigma_mol and sigma_mol); they persist without centers | F: Gas in more massive, more actively star-forming galaxies is denser and more turbulent on ~100 pc scales | **supported**

## Reasoning

- Why this data: PHANGS-ALMA covers essentially all ALMA-visible nearby massive star-forming galaxies at cloud-scale resolution  
  > "The high resolution and sensitivity of the PHANGS-ALMA data offer an unprecedented opportunity to characterize molecular gas properties on" (Introduction)
- Why this method: Fixed-scale pixel-by-pixel analysis gives a simple, reproducible characterization of all detected emission  
  > "This method provides a simple, reproducible characterization of all detected emission" (Data and Measurements)
- Alternative: Cloud-identification (decomposition into individual objects) analyses of the same CO data are done in companion papers and give qualitatively similar conclusions  
  > "Complementary analyses decomposing the same CO data into individual objects (E. Rosolowsky et al. 2020, in preparation; A. Hughes et al., in preparation) yield qualitatively similar conclusions." (Data and Measurements)
- How they decided it was enough: _not stated_
- Limitation (authors): Masking excludes faint CO emission (censoring toward low I_CO, high sigma_CO)  
  > "Our masking scheme guarantees high S/N ratio CO line measurements at the expense of excluding faint CO emission" (Data and Measurements)
- Limitation (authors): P_turb and alpha_vir assume an idealized sub-beam gas distribution  
  > "The calculation of $P_\mathrm{turb}$ and $\alpha_\mathrm{vir}$ assumes an idealized sub-beam gas distribution" (3.1 Statistics of Cloud-scale Molecular Gas Properties)
- Limitation (authors): Galaxy-center measurements affected by alpha_CO and R21 uncertainty  
  > "Our measurements in galaxy centers can be affected by uncertainty related to $\alpha_\mathrm{CO}$ and $R_\mathrm{21}$." (3.3 Correlation with Galaxy Bars and Spiral Arms)
- Caveat (inferred, ours): Metallicity-dependent alpha_CO from global scaling relations, applied with no uncertainty propagation, directly sets Sigma_mol and alpha_vir
- Caveat (inferred, ours): Fixed R21=0.65 for all galaxies and environments
- Caveat (inferred, ours): Line widths may include unresolved bulk motions, so sigma_mol may not be purely turbulent
- Caveat (inferred, ours): The masking-induced censoring biases medians and correlations toward bright, narrow-line gas
- Caveat (inferred, ours): Upstream data processing is deferred to papers in preparation, so the full pipeline cannot be checked from this paper
- Caveat (inferred, ours): Uncertainties on the reported correlations and medians are not given

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: Per-sightline measurement table published at 150 pc and 90 pc  
  > "We publish the resultant 102 778 independent measurements at $150$ pc scales and 79 840 measurements at $90$ pc scales in Table" (Summary)
- Code: SpectralCubeTools (masking scheme and censoring function) on GitHub  
  > "The `Python` realization of this signal identification scheme is available at <https://github.com/astrojysun/SpectralCubeTools>." (Footnote 3)
- Missing: Processed PHANGS-ALMA CO(2-1) cubes (internal data release v3.4) or the full imaging and single-dish combination recipe from Leroy et al. 2020b (in preparation)
- Missing: Beam convolution and hexagonal resampling details
- Missing: Region masks (centers, arms, inter-arm) and bar/arm classifications from Querejeta et al. (in preparation)
- Missing: Per-galaxy Z' values and stellar mass, SFR and R_eff source tables
- Data volume (inferred): Raw ALMA data for 8 projects covering 70 galaxies plus ACA and total power is likely several TB; the released cubes are likely hundreds of GB.
- Score (inferred): 3/5, The measurement equations, masking thresholds, conversion factors and released per-sightline table are given and code is public, but cube production and region definitions are deferred to papers in preparation.
- Rediscovery candidate: no, The recipe from cubes to results is clear, but the processed cubes come from an internal release with the imaging recipe in a companion paper, so redoing from the paper alone is incomplete.

## Links

- Method: A. K. Leroy et al. 2020b, in preparation (Details data combination, cube processing and product creation scheme)
- Method: (cite: Sun_etal_2018) (Pilot-sample cloud-scale analysis that this paper extends)
- Method: (cite: Heyer_etal_2001) (Effective line width definition)
- Companion: E. Rosolowsky et al. 2020, in preparation (Cloud identification analysis of the same CO data)
- Companion: M. Querejeta et al. 2020, in preparation (Bar, spiral arm and central region definitions)
- Companion: A. K. Leroy et al. 2020a, in preparation (PHANGS-ALMA survey paper)
- Companion: (cite: Sun_etal_2020) (Related study of molecular gas dynamical state and pressure)
- Related: PHANGS-ALMA
- Related: PHANGS-ALMA Large Program and pilot samples

## Checks

```json
{
 "quotes": 106,
 "quotes_ok": 106,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 8,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2013.1.01161.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 16,
 "numeric_problems": 0,
 "fill": {
  "facts": 99,
  "stated": 55,
  "rate": 0.556
 },
 "evidence_ok": true
}
```
