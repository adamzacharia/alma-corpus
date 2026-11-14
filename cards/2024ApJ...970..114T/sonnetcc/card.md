# Evidence of Grain Alignment by Magnetically Enhanced Radiative Torques from Multiwavelength Dust Polarization Modeling of HL Tau

`2024ApJ...970..114T` | The Astrophysical Journal 2024 | first author: Thang, Nguyen Tat | arXiv: 2401.00220 | DOI: 10.3847/1538-4357/ad4f74

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: protoplanetary_disks
- Question: Test whether grain alignment by the MRAT mechanism plus self-scattering explains the multi-wavelength (3.1, 1.3, 0.87 mm) ALMA dust polarization of HL Tau, constraining grain magnetic properties and grain size  
  > "our main goal is to test the validity of grain alignment with the MRAT mechanism and put a strong constraint on grain magnetic properties as well as grain growth in HL Tau." (1 Introduction)
- Target **HL Tau**: coordinates _not stated_; z/distance ~140 pc  
  > "located in the Taurus molecular cloud, which is $\sim\,140\,$pc from Earth (cite: 2004AJ....127.1029R)" (1 Introduction); distance from Rebull et al. 2004 (cite: 2004AJ....127.1029R)  
  > "located in the Taurus molecular cloud, which is $\sim\,140\,$pc from Earth (cite: 2004AJ....127.1029R)" (1 Introduction)

## Data provenance

- ALMA projects: 2016.1.00115.S, 2016.1.00162.S, 2019.1.01051.S
- bands: Band 3 (3.1 mm), Band 6 (1.3 mm), Band 7 (0.87 mm)  
  > "for three well-studied ALMA Bands 3, 6, and 7 corresponding to the wavelengths" (1 Introduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Beam 0.45x0.29 arcsec (3.1 mm), 0.33x0.24 arcsec (1.3 mm), 0.20x0.13 arcsec (0.87 mm)  
  > "& 3.1 & 58 & 22 & 0.45 & 0.29" (Table 1); "6 & 1.3 & 170 & 37 & 0.33 & 0.24" (Table 1); "7 & 0.87 & 409 & 92 & 0.20 & 0.13" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: Stokes I noise 58 / 170 / 409 uJy/beam and polarized-intensity noise 22 / 37 / 92 uJy/beam at 3.1 / 1.3 / 0.87 mm  
  > "& 3.1 & 58 & 22 & 0.45 & 0.29" (Table 1); "6 & 1.3 & 170 & 37 & 0.33 & 0.24" (Table 1); "7 & 0.87 & 409 & 92 & 0.20 & 0.13" (Table 1)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Data taken from the ALMA archive (PIs listed as Kataoka and Stephens)  
  > "The observational data is taken directly from the ALMA archive, which has been reduced and calibrated by ALMA staff." (2 Dust and Disk Models)
- External data: Dust composition (astronomical silicate, troilite, refractory organics, water ice)  
  > "We adopt a dust model with compositions from (cite: 2018ApJ...869L..45B), where dust grains are a mixture of astronomical silicate, troilite, refractory organics, and water ice." (2.1 Dust Model) [from (cite: 2018ApJ...869L..45B)]
- External data: Refractive indices of silicate, troilite, organics and water ice  
  > "The refractive index used in the calculation is from (cite: 2003ARA&A..41..241D) for astronomical silicate, (cite: 1996A&A...311..291H) for troilite, and (cite: 2008JGRD..11314220W) for refractory organics and water ice." (2.1 Dust Model) [from (cite: 2003ARA&A..41..241D); (cite: 1996A&A...311..291H); (cite: 2008JGRD..11314220W)]
- External data: Disk surface density profile  
  > "for simplicity, we assume a surface density profile taken from (cite: 2011ApJ...741....3K)" (2.2 Disk Model) [from (cite: 2011ApJ...741....3K)]
- External data: Magnetic field strength profile (toroidal, MRI-driven accretion)  
  > "with the strength’s profile as estimated in (cite: 2011ApJ...739...50B)" (2.2 Disk Model) [from (cite: 2011ApJ...739...50B)]
- External data: Accretion rate used in the magnetic field profile  
  > "is the accretion rate measured by (cite: 2004ApJ...616..998W)" (2.2 Disk Model) [from (cite: 2004ApJ...616..998W)]
- External data: Reference alignment-component polarization degree -q'_100 = 1.95 used as the fitting target for iron-cluster constraints  
  > "due to the alignment component as decomposed in (cite: 2022MNRAS.512.3922L) will be chosen as the reference value" (4.2 Constraints on Iron Abundance within Grains in the form of Clusters) [from (cite: 2022MNRAS.512.3922L)]
- External data: Ring/gap structure of HL Tau used for the appendix ring/gap model  
  > "reported ring and gap structures with the new ALMA observations." (7 Disk model with ring/gap structures) [from (cite: 2023Natur.623..705S)]
- Simulation/model as data: Own POLARIS radiative-transfer and ray-tracing models of an axisymmetric HL Tau disk with MRAT grain alignment and self-scattering, compared with ALMA polarization at three bands  
  > "Here, using our updated POLARIS code, we perform numerical modeling of dust polarization" (abstract)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Archive data reduced and calibrated by ALMA staff, used with only further polarization de-biasing  
  > "The observational data is taken directly from the ALMA archive, which has been reduced and calibrated by ALMA staff." (2 Dust and Disk Models); "We only further perform de-biasing the polarized intensity and polarization degree via the method described in" (2 Dust and Disk Models)
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
- final beam: 0.45x0.29 arcsec (3.1 mm), 0.33x0.24 arcsec (1.3 mm), 0.20x0.13 arcsec (0.87 mm)  
  > "& 3.1 & 58 & 22 & 0.45 & 0.29" (Table 1); "6 & 1.3 & 170 & 37 & 0.33 & 0.24" (Table 1); "7 & 0.87 & 409 & 92 & 0.20 & 0.13" (Table 1)
- final rms: Stokes I 58 / 170 / 409 uJy/beam; polarized 22 / 37 / 92 uJy/beam  
  > "& 3.1 & 58 & 22 & 0.45 & 0.29" (Table 1); "6 & 1.3 & 170 & 37 & 0.33 & 0.24" (Table 1); "7 & 0.87 & 409 & 92 & 0.20 & 0.13" (Table 1)

### Inherited from earlier work

- Polarized intensity and polarization-degree de-biasing method  
  > "We only further perform de-biasing the polarized intensity and polarization degree via the method described in (cite: 2014ApJS..213...13H) and (cite: 2015JAI.....450005H)." (2 Dust and Disk Models) [from (cite: 2014ApJS..213...13H); (cite: 2015JAI.....450005H)]
- Grain-alignment physics (MRAT, internal/external alignment) as implemented in updated POLARIS  
  > "The procedure to calculate the alignment degree of dust grains with magnetic fields in POLARIS is nicely summarized in Figure 2 of (cite: 2023MNRAS.520.3788G)." (2.1 Dust Model) [from (cite: 2023MNRAS.520.3788G)]
- Alignment Measure (AM) metric for comparing polarization orientation  
  > "as introduced in (cite: 2017ApJ...835...41G) to compare the polarization orientation." (3.2 Mixture of MRAT Grain Alignment and Self-scattering: Final Results) [from (cite: 2017ApJ...835...41G)]
- Dust-settling factor f_settle = 10 applied in self-scattering calculation  
  > "which is defined as the dust-settling factor from the disk scale height, following (cite: 2016ApJ...820...54K)" (2.2 Disk Model) [from (cite: 2016ApJ...820...54K)]
- Grain size power-law index q = -3.5  
  > "power-law distribution with a power index $q = -3.5$ (cite: 1977ApJ...217..425M)" (2.1 Dust Model) [from (cite: 1977ApJ...217..425M)]
- Mean refractive index of grain mixture from Bruggeman effective medium theory  
  > "the mean refractive index of the mixture is then calculated with the effective medium theory using Bruggeman rule (cite: 1998asls.book.....B)" (2.1 Dust Model) [from (cite: 1998asls.book.....B)]
- Self-scattering MCRT run with an older POLARIS branch (master-old) instead of the updated code  
  > "we use the POLARIS code taken from <https://github.com/polaris-MCRT/POLARIS/tree/master-old> instead." (Footnote 1) [from POLARIS master-old (cite: 2016A&A...593A..87R)]

### Not stated but needed to reproduce (our reading)

- Which archive products (MOUS, image cubes or FITS Stokes I/Q/U maps, pipeline version) were downloaded for each of the three projects
- Disk inclination and position angle and the distance adopted in the model images
- How model images were convolved/regridded to the ALMA beams and the pixel grid, and the mask or S/N cut for the pixel-by-pixel c_P and AM comparison
- POLARIS settings: photon numbers, grid layout and resolution, wavelength sampling, ray-tracing setup
- Grid of a_max and N_cl values actually run beyond the typical models shown in the table
- Access to the updated POLARIS code with the grain-alignment physics (obtained from a coauthor, release not stated)
- Exact procedure and parameters used to normalize and fit Stokes I (how the dust mass was found, residual metric)
- Background radiation field, central-star spectrum and number of grain-size bins used in radiative heating and alignment calculation
- Details of how the -q'_100 curves in Figure 5 were computed across phi_sp, N_cl and Q_X values

## Analysis recipe

1. **Debias the archival polarization images**: Use archive-reduced ALMA polarization images and de-bias polarized intensity and polarization degree  
  > "We only further perform de-biasing the polarized intensity and polarization degree via the method described in (cite: 2014ApJS..213...13H) and (cite: 2015JAI.....450005H)." (2 Dust and Disk Models)
   - parameter: Polarization degree uncertainty floored at 0.033%  
  > "Hence, we use the error of 0.033% when the polarization degree uncertainty is less than this value." (2 Dust and Disk Models)
   - assumption: Minimum detectable polarization degree of 0.1%, taken as three times the systematic calibration uncertainty  
  > "The ALMA minimum detectable polarization degree is expected at 0.1%, and defined as three times the systematic calibration uncertainty." (2 Dust and Disk Models)
   - fitting: _not stated_
   - validation: _not stated_
2. **Define the dust model**: Mixture of silicate, troilite, organics and water ice with power-law size distribution, a_max left wavelength-dependent; ray-tracing grains oblate with optical properties from DDSCAT; MCRT grains spherical (Mie)  
  > "we leave $a_{\rm max}$ as a wavelength-dependent parameter." (2.1 Dust Model); "pre-calculated with DDSCAT (cite: 1994JOSAA..11.1491D)" (2.1 Dust Model); "For the MCRT calculation, we adopt spherical grains" (2.1 Dust Model)
   - software: POLARIS, DDSCAT
   - parameter: Oblate grains with aspect ratio s = 1/2 for ray tracing  
  > "we choose an average value of $s=1/2$ for simplicity" (2.1 Dust Model)
   - parameter: Paramagnetic iron fraction f_p = 0.1  
  > "we assign the value of the fraction of iron atoms diffusely distributed within grains as $f_{\rm p} = 0.1$" (2.1 Dust Model)
   - parameter: Superparamagnetic iron-cluster volume filling factor phi_sp = 0.1, N_cl varied  
  > "we fix the volume filling factor of iron clusters to $\phi_{\rm sp}$ = 0.1" (2.1 Dust Model); "and vary the number of iron atoms per cluster $N_{\rm cl}$ to describe different degree of grain alignment enhancement" (2.1 Dust Model)
   - parameter: Internal alignment efficiency Q_X,high-J = 0.4; Q_X,low-J = 0.4 (right IA) or -0.4 (wrong IA)  
  > "When grains are aligned at high-$J$ attractors, the internal alignment efficiency is $Q_{\rm X,high-J}$ = 0.4." (2.1 Dust Model); "We set $Q_{\rm X,low-J}$ = 0.4 for the case of grains aligning at right internal alignment, and $Q_{\rm X,low-J} = -0.4$ at wrong internal alignment." (2.1 Dust Model)
   - assumption: Same grain population throughout the disk; Rayleigh regime for the polarization calculation  
  > "We assume the grain population to be the same throughout the disk." (2.1 Dust Model); "We assume the Rayleigh regime (cite: 1985ApJ...290..211L) for the polarization calculation." (2.1 Dust Model)
   - assumption: Compact grains; grain alignment induced only by MRAT  
  > "Assuming compact grains, the mean refractive index of the mixture is then calculated" (2.1 Dust Model); "In the present work, grain alignment is considered to be induced only by MRAT." (2.1 Dust Model)
   - fitting: _not stated_
   - validation: _not stated_
3. **Build axisymmetric disk model and calibrate dust mass to Stokes I**: Radiative transfer for dust temperature with a central protostar, parametrized surface density and Gaussian vertical structure; total dust mass tuned so synthetic Stokes I matches the three ALMA images  
  > "The radiation field and dust temperature within the disk are then calculated using radiative transfer calculation." (2.2 Disk Model); "we take the total dust mass of the system $M_{\rm d}$ as a calibrating parameter to reproduce the three Stokes $I$ emissions" (2.2 Disk Model)
   - software: POLARIS
   - parameter: T_star = 4000 K, R_star = 7 R_sun  
  > "The protostar has the effective temperature $T_{\star}$ = 4000 K and radius $R_{\star}=7R_\odot$" (2.2 Disk Model)
   - parameter: R_c = 78.9 AU, gamma = -0.2  
  > "$R_{\rm c}$ = 78.9 AU and $\gamma = -0.2$" (2.2 Disk Model)
   - parameter: Scale height h0 = 10 AU at 100 AU, flaring beta = 1.15  
  > "with $h_0$ = 10 AU being the scale height at" (2.2 Disk Model); "$\beta$ = 1.15 the exponent factor characterizing the flaring effect of the disk" (2.2 Disk Model)
   - parameter: Gas mass normalized to M_g = 0.1 M_sun (gas-to-dust ratio ~10)  
  > "we normalize the density profile with $M_{\rm g}\,=\,0.1\,M_{\odot}$" (2.2 Disk Model)
   - assumption: Gas temperature equals dust temperature  
  > "We assume gas temperature to be the same as the dust temperature for simplicity." (2.2 Disk Model)
   - assumption: Toroidal-dominated magnetic field  
  > "we assume that it is dominated by toroidal component as indicated in (cite: 2015A&A...574A..68F)" (2.2 Disk Model)
   - fitting: Dust mass tuned by eye to match total Stokes I at a_max = 100 um; no further parameter search  
  > "Therefore, we will not further search for more optimal parameter sets." (2.2 Disk Model)
   - validation: Compared synthetic and observed Stokes I at three wavelengths (Figure 2); residuals still significant  
  > "which produces total emissions comparable to the observations as shown in Figure" (2.2 Disk Model); "Although the residuals are still significant" (2.2 Disk Model)
4. **Simulate polarization from MRAT-aligned grains over alignment scenarios**: Ray-tracing of thermal emission from aligned grains for perfect, right and wrong internal alignment with paramagnetic and superparamagnetic grains (N_cl = 1e3, 1e4), initially without self-scattering at 3.1 mm  
  > "we investigate the effect of grain magnetic properties on disk polarization due to the MRAT mechanism" (3.1 Effect of Grain Magnetic Properties on Disk Polarization)
   - software: POLARIS
   - fitting: _not stated_
   - validation: _not stated_
5. **Add self-scattering and combine with aligned-grain emission**: Self-scattering polarization from MCRT with spherical grains and dust settling; Stokes parameters of aligned-grain emission and scattered emission are combined  
  > "we combine their Stokes parameters to obtain the combined linear polarization from the dust emission" (2 Dust and Disk Models); "we take into account the effect of dust-settling by dividing the scale height $h_{\rm d}$ by a factor $f_{\rm settle}=10$" (2.2 Disk Model)
   - software: POLARIS (master-old)
   - assumption: Scattering with non-spherical grains neglected  
  > "we neglect the effect of scattering with non-spherical grains for simplicity" (2.1 Dust Model)
   - fitting: _not stated_
   - validation: _not stated_
6. **Compare models with observations to pick the best a_max and N_cl**: Pixel-by-pixel correlation of polarization degree (c_P) and mean Alignment Measure of polarization angles between model and observations  
  > "We check the pixel-by-pixel correlation for the polarization degree" (3.2 Mixture of MRAT Grain Alignment and Self-scattering: Final Results); "We then take its average value across the image $\overline{AM}$ to represent the overall correlation between polarization vectors of the model and observations." (3.2 Mixture of MRAT Grain Alignment and Self-scattering: Final Results)
   - software: POLARIS
   - fitting: Grid comparison over a_max and N_cl at each wavelength, best model chosen by AM and c_P closest to unity; no sampler or likelihood  
  > "The closer the values of $\overline{AM}$ and $c_{\rm P}$ to unity, the better the model compared to the observations." (Table 3)
   - validation: AM ranges from -1 to 1, with 1 a perfect match of vectors  
  > "where $AM=1$ corresponds to a perfect match of polarization vectors" (3.2 Mixture of MRAT Grain Alignment and Self-scattering: Final Results)
7. **Constrain iron cluster volume filling factor**: Treat phi_sp as free and track -q'_100 versus N_cl at 3.1 mm against a reference value of 1.95 with 0.5% error  
  > "we treat $\phi_{\rm sp}$ as a free parameter to investigate its effect on disk polarization." (4.2 Constraints on Iron Abundance within Grains in the form of Clusters); "An error of 0.5$\%$ is assigned to represent the uncertainty of the method." (4.2 Constraints on Iron Abundance within Grains in the form of Clusters)
   - software: POLARIS
   - fitting: _not stated_
   - validation: N_cl ~9e2 consistent with the -q'_100 reference at phi_sp = 0.1  
  > "our constrained value of $N_{\rm cl}\sim 9 \times 10^2$ is consistent with the $-q'_{100}$ reference" (4.2 Constraints on Iron Abundance within Grains in the form of Clusters)
8. **Constrain internal alignment efficiency for slow internal relaxation**: Compute -q'_100 over N_cl = 1e2 to 1e4 for extreme values of Q_X,high-J and Q_X,low-J with phi_sp = 0.3 and compare with the reference value  
  > "we consider the extreme scenarios where parameters involved in the internal alignment process are set to their respective extremes" (4.3 Constraints on Internal Alignment Efficiency for Slow Internal Relaxation)
   - software: POLARIS
   - fitting: _not stated_
   - validation: _not stated_
9. **Assess alternative alignment mechanisms (Gold, v-MET)**: Estimate Stokes number from a_max and gas surface density to judge the grain-gas drift direction and compare predicted patterns with observed ones  
  > "the Stokes number is estimated to be $St \sim 5.4 \times 10^{-3}$" (4.4 Other Grain Alignment Mechanisms)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **POLARIS** updated version (cite: 2023MNRAS.520.3788G); master-old branch for self-scattering: Radiative transfer, dust temperature, grain alignment and polarization ray tracing and self-scattering  
  > "Here, using our updated POLARIS code, we perform numerical modeling of dust polarization" (abstract); "we use the POLARIS code taken from <https://github.com/polaris-MCRT/POLARIS/tree/master-old> instead." (Footnote 1)
- **DDSCAT** : Pre-calculating extinction and RAT efficiencies of oblate grains  
  > "pre-calculated with DDSCAT (cite: 1994JOSAA..11.1491D)" (2.1 Dust Model)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Best-fit total dust mass | 1.3e-2 | not stated | M_sun | 3 | $M_{\rm d}$ = $1.3\times10^{-2}M_{\odot}$ is found to be the best-fitted value |
| Disk mid-plane temperature profile | T(R) = 347 (R/1 AU)^-0.64 | not stated | K | 3 | T(R) = 347\left(\frac{R}{1\,\text{AU}}\right)^{-0.64}~{\rm K} |
| Spectrum-weighted wavelength of radiation and anisotropy parameter in the inner disk | ~140 um and ~0.1 | not stated | um; dimensionless | 3 | Calculations show that the radiation at this region is dominated at $\overline{\lambda}\sim$ 140$\;\mu$m, with anisotropy parameter $\overline{\gamma}\sim 0.1$. |
| Polarization degree for ideal perfect internal alignment | up to ~10 | not stated | % | 4 | which results in the radial polarization pattern with a very high polarization degree of up to the level of $\sim$10%. |
| Polarization degree for paramagnetic grains with right internal alignment | ~0.01 | not stated | % | 4 | When grains are made of paramagnetic material, the polarization degree is $\sim$0.01%. |
| Number of iron atoms per cluster N_cl (best model) | ~9e2 | not stated | dimensionless | 6 | The abundance of iron embedded inside grains in the form of clusters is constrained to be $\gtrsim 16$%, and the number of iron atoms per cluster is $N_{\rm cl} \sim 9\times10^2$. |
| Abundance of iron embedded in grains as clusters | >~16 | not stated | % | 7 | The abundance of iron embedded inside grains in the form of clusters is constrained to be $\gtrsim 16$%, and the number of iron atoms per cluster is $N_{\rm cl} \sim 9\times10^2$. |
| Minimum iron cluster volume filling factor phi_sp | ~0.05 | not stated | dimensionless | 7 | This test puts a constraint on $\phi_{\rm sp}$ with its minimum value at $\sim$0.05, which corresponds to $\sim$16% of iron locked inside grains in the form of cluster. |
| Allowed N_cl range within valid phi_sp | ~2e2 - 2e3 | not stated | dimensionless | 7 | the range of $N_{\rm cl}$ is also found to be at $\sim$$2 \times 10^2$ - $2 \times 10^3$ within the valid values of $\phi_{\rm sp}$. |
| Maximum grain size a_max at 0.87, 1.3 and 3.1 mm | ~60, ~80, ~90 | not stated | um | 6 | Maximum grain sizes probed at wavelengths $\lambda$ = 0.87, 1.3, and 3.1$\,$mm are constrained at $\sim$ 60, 80, and 90$\,\mu$m, respectively. |
| Mean Alignment Measure for best model (3.1, 1.3, 0.87 mm) | 0.93, 0.93, 0.93 | not stated | dimensionless | 6 | **0.93** & **0.69**; **0.93** & **0.63**; **0.93** & **0.09** |
| Polarization-degree correlation c_P for best model (3.1, 1.3, 0.87 mm) | 0.69, 0.63, 0.09 | not stated | dimensionless | 6 | **0.93** & **0.69**; **0.93** & **0.63**; **0.93** & **0.09** |
| Maximum |Q_X,high-J| and minimum |Q_X,low-J| | ~0.8 and ~0.15 | not stated | dimensionless | 8 | we can deduce the maximum possible value of $/Q_{\rm X,high-J}/$ is $\sim$0.8, while the minimum value of $/Q_{\rm X,low-J}/$ is at $\sim$0.15. |
| Stokes number for a_max ~100 um and Sigma_g ~5 g/cm^2 | ~5.4e-3 | not stated | dimensionless | 9 | the Stokes number is estimated to be $St \sim 5.4 \times 10^{-3}$ |

## Qualitative findings

- Superposition of azimuthal aligned-grain polarization and self-scattering gives the observed transition from azimuthal to parallel-to-minor-axis patterns from 3.1 to 0.87 mm  
  > "As a result of their superposition at different wavelengths, the polarization shows a transition from azimuthal to parallel to the disk minor axis patterns as in the observations." (3.2 Mixture of MRAT Grain Alignment and Self-scattering: Final Results)
- Large grains with slow internal relaxation must have wrong internal alignment to reproduce azimuthal polarization  
  > "but very large grains with slow internal relaxation must have wrong internal alignment." (4.1 Comparison to Previous Studies and Implications)

## Claim tuples

- H: Can iron-bearing grains aligned by MRAT explain the HL Tau polarization, and what grain magnetic properties are needed? | E: Modeled polarization for paramagnetic and superparamagnetic grains with right/wrong internal alignment and compared with ALMA | R: Paramagnetic grains give ~0.01% polarization; superparamagnetic grains with N_cl ~9e2 and wrong internal alignment reproduce the pattern and ~1% level | F: Grains must contain iron in clusters (superparamagnetic), with >~16% iron abundance | **supported**
- H: Does MRAT alignment plus self-scattering reproduce the multi-wavelength polarization? | E: Combined aligned-grain and self-scattering Stokes maps at 3.1, 1.3 and 0.87 mm and compared with ALMA using AM and c_P | R: Best model has mean AM 0.93 at all bands with c_P 0.69, 0.63 and 0.09 | F: The mixture reproduces the observed polarization morphology at all three wavelengths | **supported**
- H: What maximum grain sizes are probed at each wavelength? | E: Grid of a_max at each wavelength with lambda-dependent a_max | R: a_max ~60, 80 and 90 um at 0.87, 1.3 and 3.1 mm | F: Grains probed are ~100 um scale, smaller than the ~1 mm from spectral-index SED fitting | **supported**
- H: Is MRAT the only grain alignment mechanism that explains the HL Tau polarization? | E: Compared MRAT results with Gold alignment and v-MET arguments | R: Gold and v-MET were argued to be incompatible with observed patterns, while grain drift enhancement could not be ruled out | F: MRAT is the only mechanism in current theory that explains the aligned-grain component | **partially**

## Reasoning

- Why this data: HL Tau seen as the prime example for the field, with multi-band ALMA polarization at three wavelengths  
  > "HL Tau is a perfect example to illustrate the evolutionary process of the field." (1 Introduction)
- Why this method: Earlier work found grain alignment plus self-scattering plausible but lacked alignment-physics modeling, so they added self-scattering to the MRAT scenario  
  > "we limit our grain alignment model to this scenario and add the effect of self-scattering to reproduce the observational data." (3.2 Mixture of MRAT Grain Alignment and Self-scattering: Final Results)
- Alternative: Gold alignment rejected as requiring supersonic gas speed, which is subsonic in disks  
  > "However, the possibility of the Gold mechanism causing grain alignment in disk environments is highly questionable" (4.4 Other Grain Alignment Mechanisms)
- Alternative: v-MET alignment argued incompatible with observed elliptical patterns (circular or radial predicted)  
  > "Both cases are not compatible with the elliptical patterns from observations (cite: 2019MNRAS.483.2371Y)." (4.4 Other Grain Alignment Mechanisms)
- How they decided it was enough: Stopped optimizing the disk model because only an axisymmetric continuum match was aimed for  
  > "Therefore, we will not further search for more optimal parameter sets." (2.2 Disk Model)
- Limitation (authors): Inconsistent grain shapes between emission ray tracing (oblate) and MCRT scattering (spherical)  
  > "Our model is subject to the unresolved grain shape inconsistency." (4.7 Caveats)
- Limitation (authors): Smooth disk model ignores observed gaps and rings and asymmetries; residuals in Stokes I remain significant  
  > "is assumed to have a smooth radial distribution and ignore all the gaps and rings observed with higher spatial resolution" (2.2 Disk Model); "Although the residuals are still significant" (2.2 Disk Model)
- Limitation (authors): Grain drift enhancement of alignment neglected  
  > "we cannot rule out the possibility of enhanced alignment with grain drift (cite: 2022AJ....164..248H), which is neglected in our model." (4.4 Other Grain Alignment Mechanisms)
- Caveat (inferred, ours): Parameter constraints come from a coarse grid with no sampler or formal uncertainties, so quoted N_cl, a_max and iron abundance have no error bars
- Caveat (inferred, ours): c_P at 0.87 mm is only 0.09 for the best model, so polarization-degree agreement there is weak despite AM = 0.93
- Caveat (inferred, ours): Results depend on assumed Q_X values, fixed phi_sp, gas mass 10x lower than the Stokes I fit implies, and an assumed toroidal field profile
- Caveat (inferred, ours): Self-scattering uses a different POLARIS branch with less-tested scattering than the alignment code

## Reproducibility

- Data public (paper): Archive data with project codes listed  
  > "The observational data is taken directly from the ALMA archive, which has been reduced and calibrated by ALMA staff." (2 Dust and Disk Models)
- Products in archive: Reduced and calibrated products taken from the ALMA archive  
  > "The observational data is taken directly from the ALMA archive, which has been reduced and calibrated by ALMA staff." (2 Dust and Disk Models)
- Code: POLARIS master-old branch is on GitHub; updated POLARIS with the alignment physics was provided by a coauthor and public release is not stated  
  > "we use the POLARIS code taken from <https://github.com/polaris-MCRT/POLARIS/tree/master-old> instead." (Footnote 1); "for providing the updated POLARIS and significant discussion about the code" (Acknowledgements)
- Missing: Public access to the updated POLARIS grain-alignment code
- Missing: Disk inclination, position angle and exact model-to-image convolution and masking for AM and c_P
- Missing: POLARIS run settings and the full grid of models behind the quoted best fit
- Missing: Which archive image products were used and their processing versions
- Data volume (inferred): Small: three polarization continuum image sets (calibrated archive products, likely under a few GB); raw data would be much larger but is not needed
- Score (inferred): 2/5, ALMA data are public and numeric results are given, but the key alignment code is an updated POLARIS not clearly public and model, grid and image-comparison settings are incomplete.
- Rediscovery candidate: no, Data are public, but the recipe depends on a specialized updated code and unstated simulation settings, so the main results are not readily redoable.

## Links

- Method: (cite: 2023MNRAS.520.3788G) (Grain alignment physics (MRAT, internal/external alignment) implemented in updated POLARIS)
- Method: (cite: 2014ApJS..213...13H); (cite: 2015JAI.....450005H) (Polarization de-biasing method used on ALMA data)
- Method: (cite: 2016A&A...593A..87R) (POLARIS radiative transfer code)
- Method: (cite: 2022AJ....164..248H) (Realistic grain alignment theory with internal and external alignment)
- Companion: (cite: 2024MNRAS.528..843L) (Reference listed for the ALMA observations of all three bands)
- Companion: (cite: 2017ApJ...844L...5K) (Reference listed for the 3.1 mm observations)
- Companion: (cite: 2017ApJ...851...55S) (Reference listed for the 3.1 and 1.3 mm observations)
- Companion: (cite: 2022MNRAS.512.3922L) (Decomposition of alignment and scattering components used as reference value)
- Companion: (cite: 2023Natur.623..705S) (High-resolution 0.87 mm ring/gap polarization used for the appendix model)

## Checks

```json
{
 "quotes": 122,
 "quotes_ok": 122,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 14,
 "numeric_problems": 0,
 "fill": {
  "facts": 110,
  "stated": 69,
  "rate": 0.627
 },
 "evidence_ok": true
}
```
