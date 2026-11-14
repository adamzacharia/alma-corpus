# Challenges in probing turbulent and magnetic support in cores: The W43-MM1 protocluster case study

`2026A&A...713A.149V` | Astronomy and Astrophysics 2026 | first author: Valeille-Manet, M. | arXiv: 2607.10029 | DOI: 10.1051/0004-6361/202659121

Card schema 1.0 | model gemini-4-argon | depth full | type archival_reuse

## Science

- Fields: star_formation, milky_way_ism
- Question: Quantify the kinetic and magnetic support operating within the cores of the high-mass protocluster W43-MM1 and test the simple assumptions behind the approximated virial theorem.  
  > "We aim to quantify the kinetic and magnetic support operating within the cores of the high-mass protocluster W43-MM1, and to test the simple assumptions behind the approximated virial theorem, which is used to interpret observations." (abstract)
- Target **W43-MM1**: coordinates W43-Main: RA 18:47:47.00, DEC -1:54:26.90; W43-SW: RA 18:47:44.68, DEC -1:54:40.50 (ICRS)  
  > "Located at a distance of 5.5 kpc, W43-MM1 has an estimated mass of $1.7 \times 10^4\, M_{\odot}$, and an estimated size of 7 $\mathrm{pc}^2$ (see (cite: Nguyen2013; Dell’Ova2023))" (Introduction); "| W43-Main | 18:47:47.00 | -1:54:26.90 |" (Polarization maps); "| W43-SW | 18:47:44.68 | -1:54:40.50 |" (Polarization maps); z/distance 5.5 kpc  
  > "Located at a distance of 5.5 kpc, W43-MM1 has an estimated mass of $1.7 \times 10^4\, M_{\odot}$, and an estimated size of 7 $\mathrm{pc}^2$ (see (cite: Nguyen2013; Dell’Ova2023))" (Introduction); "| W43-Main | 18:47:47.00 | -1:54:26.90 |" (Polarization maps); "| W43-SW | 18:47:44.68 | -1:54:40.50 |" (Polarization maps); distance from Nguyen2013; Dell’Ova2023  
  > "Located at a distance of 5.5 kpc, W43-MM1 has an estimated mass of $1.7 \times 10^4\, M_{\odot}$, and an estimated size of 7 $\mathrm{pc}^2$ (see (cite: Nguyen2013; Dell’Ova2023))" (Introduction); "| W43-Main | 18:47:47.00 | -1:54:26.90 |" (Polarization maps); "| W43-SW | 18:47:44.68 | -1:54:40.50 |" (Polarization maps)

## Data provenance

- ALMA projects: 2017.1.01355.L, 2013.1.01365.S, 2015.1.01273.S, 2015.1.01020.S
- bands: 1.3 mm (continuum and lines) and ~3 mm (91.971 GHz line)  
  > "To map the magnetic field orientation in the plane of the sky toward W43, we used the 12 m ALMA 1.3 mm continuum observations in full polarization from project #2015.1.01020.S" (Polarization maps); "| $\mathrm{CH_3CN\,(5_3}$–$4_3)$ | 91.971 | 488 | 1.6 | $0.59\times 0.37$ | 2590 | $10^5-10^6\,\mathrm{cm^{-3}}$ |" (ALMA-IMF molecular lines)
- frequencies and spectral setup: CH3CN(5_3-4_3) at 91.971 GHz (488 kHz / 1.6 km s^-1); DCN(3-2) at 217.238 GHz (244 kHz / 0.34 km s^-1); 13CS(5-4) at 231.221 GHz (244 kHz / 0.32 km s^-1)  
  > "| $\mathrm{CH_3CN\,(5_3}$–$4_3)$ | 91.971 | 488 | 1.6 | $0.59\times 0.37$ | 2590 | $10^5-10^6\,\mathrm{cm^{-3}}$ |" (ALMA-IMF molecular lines); "| DCN (3-2) | 217.238 | 244 | 0.34 | $0.65 \times 0.47$ | 3030 | $10^7\,\mathrm{cm^{-3}}$ |" (ALMA-IMF molecular lines); "| $\mathrm{^{13}CS}$ (5–4) | 231.221 | 244 | 0.32 | $0.59 \times 0.43$ | 2750 | $10^6\,\mathrm{cm^{-3}}$ |" (ALMA-IMF molecular lines)
- continuum bandwidth: _not stated_
- arrays: 12 m only  
  > "The line data used for this paper are 12 m only line datacubes from the Large Program ALMA-IMF (#2017.1.01355.L, PIs: Motte, Ginsburg, Louvet, Sanhueza)." (ALMA-IMF molecular lines); "To map the magnetic field orientation in the plane of the sky toward W43, we used the 12 m ALMA 1.3 mm continuum observations in full polarization from project #2015.1.01020.S" (Polarization maps)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: CH3CN: 0.59'' x 0.37'' (2590 au); DCN: 0.65'' x 0.47'' (3030 au); 13CS: 0.59'' x 0.43'' (2750 au); polarization mosaics: 0.66'' x 0.63'' (3500 au); 1.3 mm continuum core catalog: 0.51'' x 0.36''  
  > "| $\mathrm{CH_3CN\,(5_3}$–$4_3)$ | 91.971 | 488 | 1.6 | $0.59\times 0.37$ | 2590 | $10^5-10^6\,\mathrm{cm^{-3}}$ |" (ALMA-IMF molecular lines); "| W43-Main | 18:47:47.00 | -1:54:26.90 | 3.86 | 0.11 | 0.12 | 0.11 | 0.66$\times$0.63 | 3500 |" (Polarization maps); "The cores were extracted using the algorithm getsf (cite: Men’shchikov2021), applied on the denoised 1.3 mm continuum map with a resolution of $0.51^{\prime\prime}\times0.36^{\prime\prime}$." (Core catalog)
- max recoverable scale: _not stated_
- sensitivity: W43-Main mosaic (mJy/beam): sigma_I=3.86, sigma_Q=0.11, sigma_U=0.12, sigma_P=0.11; W43-SW mosaic (mJy/beam): sigma_I=0.53, sigma_Q=0.04, sigma_U=0.04, sigma_P=0.04  
  > "| W43-Main | 18:47:47.00 | -1:54:26.90 | 3.86 | 0.11 | 0.12 | 0.11 | 0.66$\times$0.63 | 3500 |" (Polarization maps); "| W43-SW | 18:47:44.68 | -1:54:40.50 | 0.53 | 0.04 | 0.04 | 0.04 | | |" (Polarization maps)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: ALMA-IMF Large Program (PIs: Motte, Ginsburg, Louvet, Sanhueza) and archival/previous projects #2013.1.01365.S, #2015.1.01273.S, #2015.1.01020.S  
  > "The line data used for this paper are 12 m only line datacubes from the Large Program ALMA-IMF (#2017.1.01355.L, PIs: Motte, Ginsburg, Louvet, Sanhueza)." (ALMA-IMF molecular lines); "To map the magnetic field orientation in the plane of the sky toward W43, we used the 12 m ALMA 1.3 mm continuum observations in full polarization from project #2015.1.01020.S, whose data were first presented in (cite: Arce-Tord2020)." (Polarization maps)
- Line: CH3CN 5_3 - 4_3 (91.971 GHz)
- Line: DCN 3 - 2 (217.238 GHz)
- Line: 13CS 5 - 4 (231.221 GHz)
- Line: N2D+ 3 - 2 (not stated)
- Line: HC3N 24 - 23 (not stated)
- External data: Core catalog (coordinates, sizes, 1.3 mm integrated fluxes) and bsens-denoised 1.3 mm continuum map  
  > "We make use of the core catalog provided in (cite: Motte2018) and further extended in (cite: Nony2023) with a mass completness of 1.6 $M_\odot$." (Core catalog); "we measured the integrated 1.3 mm flux within the previously defined area (i.e., the three-beam area with pixels from the central core and neighboring cores removed) using the bsens–denoised continuum map from (cite: Nony2023)." (Method) [from Motte2018; Nony2023]
- External data: Classification of cores into prestellar and protostellar (using outflows and hot cores)  
  > "The nature of cores was defined in (cite: Nony2020) leading to the detection of 27 protostellar cores using protostellar outflows by studying the CO (2–1) and SiO (5–4) lines and the hot cores identified by (cite: Brouillet2022) and (cite: Bonfand2024)." (Core catalog); "For this work, we consider core #14 as prestellar, following (cite: Valeille-Manet2025), due to its insufficient evidence of association with an outflow." (Core catalog) [from Nony2020; Brouillet2022; Bonfand2024; Valeille-Manet2025]
- External data: Core temperatures, masses, sizes, and protostellar luminosities; 2.5'' scale dust temperatures  
  > "The core temperatures, masses and protostellar luminosities have been estimated by (cite: Motte2025) and span the 0.3-115 $M_\odot$ and 0.14-12.21$\times 10^3\,L_\odot$ ranges." (Core catalog); "For this conversion, we adopt the dust temperature ($T_{\mathrm{dust}}$) derived by (cite: Dell’Ova2023) at a spatial scale of $2.5^{\prime\prime}$ and listed in (cite: Motte2025):" (Method) [from Motte2025; Dell’Ova2023]
- External data: Magnetic field-density power-law scaling exponent beta = 0.53 (+0.09/-0.07) from Zeeman measurements  
  > "For that, we compute each core density using their mass and size, and we apply the field–density relation, $B \, \propto\, n^{\beta}$ with $\beta = 0.53^{+0.09}_{-0.07}$ (cite: Whitworth2025)." (Method) [from Whitworth2025]

## Processing

### Calibration

- pipeline or manual: ALMA-IMF pipeline for molecular line cubes  
  > "We used here the DCN (3–2) and $\mathrm{^{13}CS}$ (5–4) lines (previously observed in the projects #2013.1.01365.S and #2015.1.01273.S, and then reprocessed in the ALMA-IMF pipeline)" (ALMA-IMF molecular lines); "The data reduction of the line cubes is described in detail in (cite: Cunningham2023)." (ALMA-IMF molecular lines)
- casa version: CASA 5.1.2 (for polarization mosaic imaging)  
  > "We combined three and two pointings toward MM1-Main and MM1-SW to clean and image the different stokes parameters in mosaic mode, using the tclean procedure from CASA 5.1.2 (cite: McMullin2007)." (Polarization maps)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean (in mosaic mode for Stokes I, Q, U)  
  > "We combined three and two pointings toward MM1-Main and MM1-SW to clean and image the different stokes parameters in mosaic mode, using the tclean procedure from CASA 5.1.2 (cite: McMullin2007)." (Polarization maps)
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
- final beam: 0.66'' x 0.63'' (3500 au) for polarization mosaics; 0.59'' x 0.37'' for CH3CN; 0.65'' x 0.47'' for DCN; 0.59'' x 0.43'' for 13CS  
  > "| W43-Main | 18:47:47.00 | -1:54:26.90 | 3.86 | 0.11 | 0.12 | 0.11 | 0.66$\times$0.63 | 3500 |" (Polarization maps); "| $\mathrm{CH_3CN\,(5_3}$–$4_3)$ | 91.971 | 488 | 1.6 | $0.59\times 0.37$ | 2590 | $10^5-10^6\,\mathrm{cm^{-3}}$ |" (ALMA-IMF molecular lines); "| DCN (3-2) | 217.238 | 244 | 0.34 | $0.65 \times 0.47$ | 3030 | $10^7\,\mathrm{cm^{-3}}$ |" (ALMA-IMF molecular lines)
- final rms: W43-Main: sigma_I=3.86, sigma_Q=0.11, sigma_U=0.12, sigma_P=0.11 mJy beam^-1; W43-SW: sigma_I=0.53, sigma_Q=0.04, sigma_U=0.04, sigma_P=0.04 mJy beam^-1  
  > "| W43-Main | 18:47:47.00 | -1:54:26.90 | 3.86 | 0.11 | 0.12 | 0.11 | 0.66$\times$0.63 | 3500 |" (Polarization maps); "| W43-SW | 18:47:44.68 | -1:54:40.50 | 0.53 | 0.04 | 0.04 | 0.04 | | |" (Polarization maps)

### Inherited from earlier work

- Data reduction and imaging of the ALMA-IMF molecular line cubes  
  > "The data reduction of the line cubes is described in detail in (cite: Cunningham2023)." (ALMA-IMF molecular lines) [from Cunningham2023]
- Imaging details for the full polarization 1.3 mm continuum observations  
  > "Imaging details are the same as in (cite: Arce-Tord2020)." (Polarization maps) [from Arce-Tord2020]
- On–Off spectral extraction method to isolate core emission from the surrounding environment  
  > "We used the same On–Off method as described in (cite: Valeille-Manet2025) (see their Sect. 3.1), which allows to isolate the emission of the cores by subtracting the contribution of their local environment." (Method) [from Valeille-Manet2025]
- Pixel-by-pixel debiasing of linear polarization in low SNR regions (<= 5 sigma_P)  
  > "To correct for this bias in low SNR regions, we applied the pixel-by-pixel method proposed by (cite: Hull&Plambeck2015)." (Polarization maps) [from Hull&Plambeck2015]
- Direct computation of polarization angle dispersion from Stokes Q and U  
  > "As shown in (cite: LeGouellec2020), the angle dispersion can be computed following:" (Method) [from LeGouellec2020]

### Not stated but needed to reproduce (our reading)

- tclean imaging parameters for polarization mosaics (weighting/robust, cell size, image size, stopping threshold, self-calibration) inherited from Arce-Tord et al. (2020)
- Calibration and imaging parameters for ALMA-IMF molecular line cubes (continuum subtraction, weighting, multiscale settings, rms noise per channel) inherited from Cunningham et al. (2023)
- Exact spectral window / velocity range used for constructing the moment-0 and moment-1 maps around each core
- Quantitative criteria used to judge whether an On-Off spectrum exhibits a 'clean, single-Gaussian profile' before falling back to the next tracer or On spectrum

## Analysis recipe

1. **Create Stokes I, Q, U mosaics and debiased linear polarization and magnetic field angle maps**: Combine three pointings for MM1-Main and two pointings for MM1-SW using CASA tclean in mosaic mode; compute linear polarization P, debias using Hull & Plambeck (2015) for <=5 sigma_P and sqrt(Q^2 + U^2 - sigma_P^2) for >5 sigma_P; compute polarization angle chi = 0.5 arctan(U/Q) and rotate by 90 deg to get B_POS orientation above 3 sigma_P.  
  > "We combined three and two pointings toward MM1-Main and MM1-SW to clean and image the different stokes parameters in mosaic mode, using the tclean procedure from CASA 5.1.2 (cite: McMullin2007)." (Polarization maps); "To correct for this bias in low SNR regions, we applied the pixel-by-pixel method proposed by (cite: Hull&Plambeck2015). For high SNR polarized emission ($>5\,\sigma_\mathrm{P}$), we simply use $P = \sqrt{Q^2 + U^2 - \sigma_{\mathrm{P}}^2}$." (Polarization maps); "The polarization angle maps are derived following $\vcenter{\hbox{$\chi$}} = 0.5\,\mathrm{arctan}\left(U/Q\right)$." (Polarization maps)
   - software: CASA, tclean
   - parameter: 3 sigma_P threshold for plotting and selecting polarization vectors; 5 sigma_P transition between low-SNR and high-SNR debiasing  
  > "which is used to define the $3\,\sigma_\mathrm{P}$ threshold to plot the polarization vectors." (Polarization maps)
   - assumption: Radiative alignment torque (RAT) mechanism aligns oblate dust grains with short axis along B field so thermal dust polarization is perpendicular to B_POS  
  > "As a result, aligned elongated oblate grains emit polarized thermal radiation, with the polarization oriented perpendicular to the magnetic field. By rotating the observed polarization angle by $90^{\circ}$, we can thus infer the morphology of the magnetic field projected onto the POS." (Polarization maps)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure core-scale velocity dispersions via On-Off spectral extraction and Gaussian fitting**: Extract On spectrum (mean within core elliptical area) and Off spectrum (mean in annulus of 2.5 to 3.5 times getsf source size, masking overlapping neighboring cores); fit a single Gaussian following the hierarchy: DCN(3-2) On-Off -> 13CS(5-4) On-Off -> DCN(3-2) On -> 13CS(5-4) On, and use CH3CN(5_3-4_3) for hot cores #1 and #4; scale 13CS velocity dispersions by 0.98/1.28 to match DCN.  
  > "The On spectrum is computed as the mean of the pixels within the elliptical area defining the source, while the Off spectrum corresponds to the mean signal in an annulus located between 2.5 and 3.5 times the getsf catalog source size" (Method); "For most cores, we use the DCN (3–2) and $\mathrm{^{13}CS}$ (5–4) lines, except for cores #1 and #4 (the two brightest hot cores of W43-MM1, (cite: Brouillet2022; Bonfand2024)) for which we use the $\mathrm{CH_3CN\,(5_3}$–$4_3)$ line." (Method); "We therefore apply a correction factor of 0.98/1.28 to the velocity dispersions derived from $^{13}$CS to place them on the same scale as the DCN measurements before combining the two sets of values." (Turbulence level in cores)
   - parameter: Off annulus inner/outer radii = 2.5 and 3.5 times getsf source size; 13CS to DCN scaling factor = 0.98/1.28  
  > "while the Off spectrum corresponds to the mean signal in an annulus located between 2.5 and 3.5 times the getsf catalog source size" (Method); "We therefore apply a correction factor of 0.98/1.28 to the velocity dispersions derived from $^{13}$CS to place them on the same scale as the DCN measurements before combining the two sets of values." (Turbulence level in cores)
   - assumption: Vicinity of each core in the annulus is representative of its local environment; gas temperature equals dust temperature (full thermalization); molecular weights mu = 28 (DCN), 45 (13CS), 41 (CH3CN)  
  > "where $\mu$ is the mean molecular weight of the line specie used to trace the velocity dispersion, $k_{\mathrm{B}}$ is the Boltzmann constant and $T$ is the gas temperature, which we assume coincides with the dust temperature (full thermalization)." (Method); "This method relies on the assumption that the vicinity of each core is representative of its local environment, such that subtracting the Off spectrum isolates the emission arising from the core itself from the surrounding environmental contribution." (Method); "The mean molecular weights are 28 for DCN, 45 for $^{13}$CS, and 41 for $\mathrm{CH_3CN}$." (Thermal and turbulent supports)
   - fitting: Single-Gaussian fit to extracted On-Off or On spectra  
  > "To investigate the turbulent support at the core-scale, we used the lines presented in Sect. 2.2 and measured the velocity dispersion of the line using a simple Gaussian fit." (Method)
   - validation: KS test comparing On-Off (27 cores) and On (18 cores) samples yields p > 0.05; tested four alternative annulus sizes (1.5-2.5, 2.0-4.0, 3.5-4.5, 4.5-5.5 core sizes) on five cores (#2, #7, #11, #14, #15), finding a maximum discrepancy of 0.17 km s^-1 (smaller than DCN spectral resolution).  
  > "A Kolmogorov–Smirnov (KS) test was performed to compare the On–Off and On samples, yielding a p-value greater than 0.05." (Turbulence level in cores); "All configurations yield linewidths consistent with those obtained with the 2.5–3.5 annulus, with a maximum discrepancy of 0.17 $\mathrm{km\,s^{-1}}$, which is smaller than the spectral resolution of the DCN cube." (Turbulence level in cores)
3. **Measure three-beam scale polarization angle dispersion, surrounding gas density, and gradient-corrected velocity dispersion**: In a circular three-beam area (diameter 3.6 x beam major axis, ~2.3'' / ~12,500 au) centered on each core with >=20 polarization semi-vectors (sampled at 4 semi-vectors per beam above 3 sigma_P), compute angle dispersion sigma_theta from Stokes Q and U (Eq. 3). Mask central and neighboring cores from the three-beam area; extract spectrum, fit single Gaussian, and subtract in quadrature both the standard deviation of the moment-1 velocity map within the mask and the thermal velocity dispersion. Measure integrated 1.3 mm flux in the same masked area from the Nony et al. (2023) bsens-denoised continuum map to compute mass M_3beam (Eq. 4) and volume density.  
  > "This area corresponds to a diameter of 3.6 beams major axis centered on the core and will be referred to as the three-beam scale or three-beam area from now on." (Method); "To maximize the number of cores for which a magnetic field strength can be derived, we included all cores containing at least 20 semi-vectors." (Method); "We computed the standard deviation of the pixel velocities inside each three-beam mask from the moment-1 map, which quantifies the magnitude of these coherent gradients. This value is then subtracted in quadrature from the velocity dispersion derived from the Gaussian line fits" (Velocity structures in the three-beam area)
   - parameter: Three-beam diameter = 3.6 x beam major axis (~2.3'', ~12500 au); sampling = 4 semi-vectors per beam; minimum 20 semi-vectors above 3 sigma_P  
  > "To satisfy the Nyquist spatial sampling criterion, we consider four semi-vectors (representing the magnetic field orientation) per beam (two in each direction, see Fig. 2)." (Method); "This area corresponds to a diameter of 3.6 beams major axis centered on the core and will be referred to as the three-beam scale or three-beam area from now on." (Method); "To maximize the number of cores for which a magnetic field strength can be derived, we included all cores containing at least 20 semi-vectors." (Method)
   - assumption: Distance d = 5.5 kpc; dust+gas mass opacity kappa_1.3mm = 0.01 cm^2 g^-1 (Ossenkopf & Henning 1994) assuming gas-to-dust ratio of 100; 2.5'' dust temperatures from Dell'Ova et al. (2023) / Motte et al. (2025); mean of spherical and oblate ellipsoidal geometries for density  
  > "where $S_{1.3 \,\mathrm{mm}}$ is the integrated flux at 1.3 mm, $d=5.5$ kpc is the distance of the W43-MM1 protocluster, $\kappa_{1.3 \,\mathrm{mm}}$ is the dust $+$ gas mass opacity set to $0.01 \, \mathrm{cm^2\, g^{-1}}$ (cite: Ossenkopf1994) assuming a gas-to-dust ratio of 100" (Method); "To account for this geometrical uncertainty, we adopt the mean value between the spherical and ellipsoidal estimates for the three-beam scale $B_\mathrm{POS}$, with its associated uncertainty." (Magnetic field strength in cores)
   - fitting: Single-Gaussian fit to three-beam masked spectrum, corrected in quadrature for moment-1 velocity dispersion and thermal dispersion  
  > "As described in Sect. 3.1, we then extracted the spectra of each source within this area and attempted to fit them with a single-Gaussian profile." (Method); "We also subtract the thermal velocity component (in quadrature) from the three-beam velocity dispersion, as the magnetic field strength estimate should only account for non-thermal turbulent motions." (Velocity structures in the three-beam area)
   - validation: Tested random removal of 1 to 25 semi-vectors (1000 draws each) on cores #1 and #14 (45 semi-vectors), finding angle dispersion varies by <=10%; compared velocity dispersions with Polychronakis et al. (2025) moment-2 mean method (~20% larger); compared spherical vs oblate ellipsoidal geometries (10% density difference, 5% B_POS difference).  
  > "We recalculated the dispersion after randomly removing between 1 and 25 semi-vectors (performing 1000 random draws for each case). As shown in Appendix 7, the resulting angle dispersion varies by 10 % at most" (Method); "Applying this method to the 17 cores with DCN measurements, we find that the resulting velocity dispersions are on average ${\sim}20$ % larger than those derived with our approach." (Velocity structures in the three-beam area); "We find that ellipsoidal geometries yield three-beam scale densities that are on average 10 % smaller than the spherical estimates, translating into $B_\mathrm{POS}$ values that are on average 5 % smaller." (Magnetic field strength in cores)
4. **Estimate plane-of-sky magnetic field strength B_POS at three-beam scale and extrapolate to core scale**: Apply the classical Davis-Chandrasekhar-Fermi (DCF) equation B_POS = Q * sqrt(4 pi rho) * sigma_v,NT / sigma_theta (Eq. 2) with Q = 0.5 at the three-beam scale, then extrapolate to core scales (~2500 au) using the core volume density and the empirical scaling B proportional to n^beta with beta = 0.53 (+0.09/-0.07).  
  > "We used the Davis-Chandrasekhar-Fermi method (cite: Davis1951; Chandrasekhar&Fermi1953) to obtain the magnetic field strength in the POS ($B_{\mathrm{POS}}$) from the dust polarized emission, following:" (Method); "and $Q$ is an empiric correction factor to account for overestimations of the magnetic field strength ($Q=0.5$, (cite: Ostriker2001; Padoan2001; Heitsch2001; Liu2019))." (Method); "For that, we compute each core density using their mass and size, and we apply the field–density relation, $B \, \propto\, n^{\beta}$ with $\beta = 0.53^{+0.09}_{-0.07}$ (cite: Whitworth2025)." (Method)
   - parameter: DCF correction factor Q = 0.5; density scaling exponent beta = 0.53 (+0.09/-0.07) (mean uncertainty 0.08 used for error propagation)  
  > "We therefore opted to keep $Q=0.5$, consistent with the value adopted in much of the literature." (Method); "For that, we compute each core density using their mass and size, and we apply the field–density relation, $B \, \propto\, n^{\beta}$ with $\beta = 0.53^{+0.09}_{-0.07}$ (cite: Whitworth2025)." (Method); "The uncertainties are derived following a mean uncertainty of 0.08 on the density power-law index of the density-field relation." (Core properties)
   - assumption: Isotropic turbulent motions; DCF reliability regime sigma_theta < 25 deg (cores #3, #4, #5, #9 with sigma_theta > 25 deg retained for statistics); spherical symmetry for core densities  
  > "This classical DCF method is typically used in regions where $\sigma_\theta < 25^{\circ}$ (cite: Ostriker2001)." (Method); "which here is the case for all the cores except cores #3, #4, #5 and #9 that we decided to keep in the following analysis in order to preserve the statistical significance of the sample." (Magnetic field strength in cores); "The masses and sizes are extracted from (cite: Motte2025) and the densities are derived assuming a spherical symmetry." (Core properties)
   - fitting: _not stated_
   - validation: Compared classical DCF with Skalidis & Tassis (2021) compressible method (gives B_POS ~20% smaller on average); compared beta=0.53 extrapolation with ideal MHD flux-freezing B proportional to n^(2/3) (which gives 1 to 70 mG).  
  > "Applying this method to our sample of 21 cores, we obtain magnetic field strengths that are on average ${\sim}20$ % smaller than those derived with our approach." (Magnetic field strength in cores); "In the flux-freezing case, our extrapolated $B_{\mathrm{POS}}$ values would range from 1 to 70 mG, with five cores exceeding 40 mG." (Magnetic field strength in cores)
5. **Compute virial parameters, mass-to-flux ratios, and contaminant infall velocities**: Calculate kinetic virial parameter alpha_kin (Eq. 5), mass-to-magnetic-flux ratio lambda_B (Eq. 6), magnetic virial mass M_phi (Eq. 7), and total virial parameter alpha_vir,B (Eq. 8). For the 11 protostellar cores with both estimates and alpha_vir,B > 1, compute the contaminant velocity that must be subtracted to bring them to alpha_vir,B = 1, and test reducing non-thermal support by a factor of two.  
  > "If we only account for kinetic support, the virial parameter can be expressed as: $$\begin{equation} \label{eq:alpha_kin} \alpha_{\mathrm{kin}} = \frac{M_{\mathrm{kin}}}{M_{\mathrm{core}}}=3\left(\frac{5-2 p}{3-p}\right) \frac{F W H M^{\mathrm{dec}}\,\sigma_\mathrm{v}^2}{G\, M_{\mathrm{core}}}, \end{equation}$$" (Thermal and turbulent supports); "To quantify the magnetic field support alone, we can use the mass-to-magnetic flux ratio $\lambda_\mathrm{B}$ following (cite: McKee&Ostriker2007) and (cite: Pillai2015):" (Magnetic support and its relative contribution); "We computed the velocity that would need to be subtracted in order to bring them back to a state of gravitational equilibrium (i.e., $\alpha_{\mathrm{vir,B}} = 1$)." (Limitations of current observational estimates of the non-thermal supports)
   - parameter: Density profile power-law index p = 0 for prestellar cores and p = 2 for protostellar cores; core radius R = FWHM^dec  
  > "The power-law index $p$ will be chosen equal to 0 (flat density profile) for prestellar cores and equal to 2 (peaked density profile) for protostellar cores for the rest of the study." (Thermal and turbulent supports); "with $\left\langle N_{\mathrm{H}_2}\right\rangle$ the mean column density of each core, which can be approximated as $M_{\mathrm{core}}/(\pi\,R^2)$ assuming cylindrical geometry (for column density), with $R$ the radius of the core (assumed to be the deconvolved $FWHM$)." (Magnetic support and its relative contribution)
   - assumption: Simplified virial theorem limited to volume terms (neglecting surface terms); central protostellar mass neglected (Class 0-like envelopes dominate); cylindrical geometry for mean column density <N_H2>  
  > "Using the velocity dispersions and the magnetic field strengths derived in the sections above, we can apply the simplified virial theorem, which is limited to volume terms (e.g., (cite: Dib2007), Chevalier et al. in prep) because only these can be constrained by observations." (Thermal and turbulent supports); "We note that, for protostellar cores, the mass of the central protostar is not included in the total mass, as reliable measurements are not available." (Thermal and turbulent supports)
   - fitting: _not stated_
   - validation: Evaluated the impact of adopting a single median velocity dispersion for all cores (Appendix 10), which artificially reproduces the inverse alpha-mass relation found in earlier studies; tested reducing non-thermal support by a factor of two to account for surface terms and bulk motion contamination.  
  > "We reproduce in Fig. 12 the same figure as Fig. 6, but using the median velocity dispersion at both the core-scale and the three-beam scale for all sources." (Impact of a common velocity dispersion on core support); "On the second y-axis of Fig. 6, we show the resulting $\alpha_\mathrm{vir,B}$ values after reducing the non-thermal support (kinetic only, or kinetic plus magnetic) by a factor of two." (Limitations of current observational estimates of the non-thermal supports)

## Software

- **CASA** 5.1.2: Cleaning and imaging Stokes I, Q, and U parameters in mosaic mode  
  > "We combined three and two pointings toward MM1-Main and MM1-SW to clean and image the different stokes parameters in mosaic mode, using the tclean procedure from CASA 5.1.2 (cite: McMullin2007)." (Polarization maps)
- **tclean** : Deconvolution and mosaic imaging of polarization Stokes parameters  
  > "We combined three and two pointings toward MM1-Main and MM1-SW to clean and image the different stokes parameters in mosaic mode, using the tclean procedure from CASA 5.1.2 (cite: McMullin2007)." (Polarization maps)
- **getsf** : Core extraction on the denoised 1.3 mm continuum map in the catalog of Motte et al. (2018) / Nony et al. (2023)  
  > "The cores were extracted using the algorithm getsf (cite: Men’shchikov2021), applied on the denoised 1.3 mm continuum map with a resolution of $0.51^{\prime\prime}\times0.36^{\prime\prime}$." (Core catalog)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Core-scale velocity dispersion range (45 cores) | 0.34 to 4.48 | not stated | km s^-1 | 2 | The velocity dispersions range from 0.34 to 4.48 $\mathrm{km\,s^{-1}}$.; We end up with velocity dispersions for the whole sample between 0.34 and 4.48 $\mathrm{km\,s^{-1}}$ with a mean of 1.10 $\mathrm{km\,s^{-1}}$. |
| Mean core-scale velocity dispersion (all 45 cores) | 1.10 | not stated | km s^-1 | 2 | We end up with velocity dispersions for the whole sample between 0.34 and 4.48 $\mathrm{km\,s^{-1}}$ with a mean of 1.10 $\mathrm{km\,s^{-1}}$. |
| Mean core-scale velocity dispersion for DCN(3-2) (30 cores) | 0.98 | not stated | km s^-1 | 2 | For the 30 cores with DCN detections, we find a mean velocity dispersion of 0.98 $\mathrm{km\,s^{-1}}$. |
| Mean core-scale velocity dispersion for 13CS(5-4) before scaling (13 cores) | 1.28 | not stated | km s^-1 | 2 | For the 13 cores with $^{13}$CS detections, the mean velocity dispersion is 1.28 $\mathrm{km\,s^{-1}}$ |
| Mean core-scale velocity dispersion for CH3CN(5_3-4_3) (2 cores) | 3.82 | not stated | km s^-1 | 2 | The mean velocity dispersion derived from $\mathrm{CH_3CN}$ is 3.82 $\mathrm{km\,s^{-1}}$. |
| Thermal velocity dispersion range of cores | 0.06 to 0.14 | not stated | km s^-1 | 2 | Mass averaged dust temperature of cores range from 17 to 69 K, which correspond to thermal velocity dispersions of 0.06 to 0.14 $\mathrm{km\,s^{-1}}$ depending on the tracer and the source. |
| Corrected three-beam scale velocity dispersion range (21 cores) | 0.63 to 3.12 | not stated | km s^-1 | 3 | These corrected velocity dispersions at the three-beam scale range from 0.63 to 3.12 |
| Mean corrected three-beam scale velocity dispersion (21 cores) | 1.70 | not stated | km s^-1 | 3 | with a mean value of 1.70 |
| Plane-of-sky magnetic field strength B_POS at three-beam scale (21 cores) | 1.1 to 22.5 | not stated | mG | 4 | The three-beam scale $B_\mathrm{POS}$ values span 1.1–22.5 mG, which extrapolate to 1.1–49.3 mG at the core-scale.; We derive $B_\mathrm{POS}$ at the three-beam scale ranging from 1.1 to 22.5 mG. |
| Extrapolated core-scale plane-of-sky magnetic field strength B_POS (21 cores) | 1.1 to 49.3 | not stated | mG | 4 | The three-beam scale $B_\mathrm{POS}$ values span 1.1–22.5 mG, which extrapolate to 1.1–49.3 mG at the core-scale.; We obtained resulting $B_\mathrm{{POS}}$ values from 1.1 to 49.3 mG. |
| Kinetic virial parameter alpha_kin for Core #1 | 1.49 | not stated | dimensionless | 5 | / 1 / Proto / 1.49 / 2.40 / 1.71 / 6.53 / |
| Total virial parameter alpha_vir,B for Core #1 | 1.71 | not stated | dimensionless | 5 | / 1 / Proto / 1.49 / 2.40 / 1.71 / 6.53 / |
| Core-scale B_POS for Core #1 | 48.6 | 7.6 | mG | 4 | / 1 / Proto / $115.2 \pm 49.6$ / 2520 / $218.0 \pm 93.8$ / 4.48 / 3.12 / 21.5 / 45 / $17.6 \pm {0.5}$ / $48.6 \pm {7.6}$ / / |
| Core-scale B_POS for Core #24 | 49.3 | 8.8 | mG | 4 | / 24 / Pre / $6.4 \pm 1.2$ / 1450 / $63.6 \pm 11.9$ / 0.71 / 1.45 / 5.4 / 42 / $15.4 \pm {0.4}$ / $49.3 \pm {8.8}$ / / |
| Fraction of cores with only turbulence measurements that have alpha_kin > 1 | 16 out of 24 (~70%) | not stated | dimensionless | 5 | Using the virial theorem, we find 16 out of the subset of 24 cores with turbulence alone ($\sim70\,\%$) to be stable against gravitational collapse. |
| Fraction of cores with magnetic field measurements that have lambda_B < 1 | 10 out of 21 (~50%) | not stated | dimensionless | 5 | From the subset of 21 cores with both estimates, 10 cores ($\sim 50\,\%$) appear to be magnetically supported against gravity when considering magnetic fields alone.; We find that 10 out of the 21 cores (four prestellar and six protostellar) have mass-to-flux ratios below unity, while the remaining 11 cores (two prestellar and eight protostellar) are magnetically supercritical. |
| Fraction of cores with both turbulence and magnetic field measurements that have alpha_vir,B > 1 | 18 out of 21 (~85%) | not stated | dimensionless | 5 | Combining both estimates, 18 cores ($\sim 85\,\%$) are found with $\alpha_{\mathrm{vir,B}} > 1$. |
| Contaminant infall / bulk flow velocity required to bring supervirial protostellar cores to alpha_vir,B = 1 | 1.0 to 3.1 | not stated | km s^-1 | 5 | We computed the velocity that would need to be subtracted in order to bring them back to a state of gravitational equilibrium (i.e., $\alpha_{\mathrm{vir,B}} = 1$).; The resulting velocities range from 1.0 to 3.1 $\mathrm{km\,s^{-1}}$, depending on the core. |

## Qualitative findings

- Thermal motions (0.06 to 0.14 km s^-1) contribute only marginally to total core linewidths and are dynamically negligible compared to non-thermal motions.  
  > "Thermal motions therefore contribute only marginally to the total linewidths, and are dynamically negligible." (Thermal and turbulent supports)
- Moment-1 maps at the three-beam scale systematically reveal coherent velocity gradients and organized structures across the masks, violating the DCF assumption of purely isotropic turbulence.  
  > "The moment-1 maps clearly reveal organized velocity structures and gradients across the three-beam masks, which indicate that large-scale motions add to micro-turbulence to widen the line width." (Velocity structures in the three-beam area)
- In the most massive cores (> 20 M_sun), kinetic support dominates over magnetic support (M_kin/M_phi > 1), opposite to trends found when assuming a uniform velocity dispersion across all cores.  
  > "However, for the most massive objects (five cores above $20\,M_\odot$, one prestellar and four protostellar), turbulence appears to provide a more significant support than magnetic fields. This trend is opposite to that reported by (cite: Cortes2019)." (Magnetic support and its relative contribution)
- Both velocity dispersions and magnetic field strengths in W43-MM1 cores are substantially higher than in low-mass star-forming regions, showing that massive protoclusters operate in a different dynamical and magnetic regime.  
  > "Our results therefore emphasize that massive star-forming environments operate in a qualitatively different dynamical regime mimicking a different turbulent regime from their low-mass counterparts." (Comparison with low-mass studies and models); "Like for motions, this emphasizes the different magnetic regimes operating in low- and high-mass star-forming environments." (Comparison with low-mass studies and models)

## Claim tuples

- H: Core-scale kinetic and magnetic support can be reliably quantified using molecular linewidths, DCF polarization analysis, and the volume-only virial theorem. | E: Measured core-scale velocity dispersions for 45 cores (DCN, 13CS, CH3CN) and extrapolated DCF magnetic field strengths for 21 cores to compute alpha_kin, lambda_B, and alpha_vir,B. | R: 16 of 24 cores with turbulence alone (~70%) have alpha_kin > 1, and 18 of 21 cores with both estimates (~85%, including 11 protostellar cores) have alpha_vir,B > 1 (16 with alpha_vir,B > 2). | F: Simplified volume-only virial analysis and raw linewidth measurements systematically overestimate non-thermal support in cores because of contamination by organized motions (1-3 km s^-1 infall/converging flows) and the omission of virial surface terms. | **refuted**
- H: Using individual core velocity dispersions and temperatures alters the inferred scaling of virial support and magnetic vs. kinetic dominance with core mass compared to assuming a uniform velocity dispersion. | E: Computed M_kin/M_phi and alpha_vir,B using individual core linewidths and temperatures, and compared with Appendix 10 where a single median velocity dispersion is applied to all cores. | R: With individual velocity dispersions, no anti-correlation between alpha_vir,B and core mass is found, and all five cores above 20 M_sun have M_kin/M_phi > 1; using a single median velocity dispersion artificially recovers the anti-correlation where massive cores appear gravitationally dominated. | F: Adopting core-specific velocity dispersions is essential for virial analyses and shows that kinetic motions dominate over magnetic support in the most massive cores (> 20 M_sun). | **supported**
- H: The high-mass prestellar cores in W43-MM1 (#17, #134, #136) are supported against gravitational collapse by non-thermal (turbulent + magnetic) pressure. | E: Computed total virial parameter alpha_vir,B and kinetic-to-magnetic support ratio M_kin/M_phi for cores #17, #134, and #136. | R: alpha_vir,B is 2.19 (core #17), 3.12 (core #134), and 11.84 (core #136); cores #17 and #136 have M_kin/M_phi < 1 (0.36 and 0.62, B_core > 30 mG), whereas core #134 has M_kin/M_phi = 3.78 (B_core = 12.1 mG); core #6 (no B measurement) has alpha_kin = 0.32 (or 0.55 in text). | F: High-mass prestellar cores in W43-MM1 appear sufficiently supported when combining turbulent and magnetic support, though small statistics and virial uncertainties prevent establishing whether turbulence or magnetic fields universally dominate. | **partially**

## Reasoning

- Why this data: W43-MM1 is a young, massive, highly dynamical mini-starburst protocluster with high polarization fractions (~5%), a well-characterized core catalog from ALMA-IMF, and dense gas tracers (DCN, 13CS) that reliably peak on cores.  
  > "In the high-mass star-forming regime, the W43-MM1 massive protocluster is an excellent target to investigate the influence of non-thermal support in cores." (Introduction); "We note that we did not identify any superior tracers that more reliably peak on and trace the cores. (cite: Mininni2025) also showed that DCN is one of the molecular lines that best matches the dust emission toward cores." (ALMA-IMF molecular lines)
- Why this method: On-Off spectral extraction isolates core emission from environmental gas; the three-beam area (~2.3'') encompasses 10 independent beams to keep DCF angle dispersion uncertainty within 15%; classical DCF with Q=0.5 avoids circularity with Mach-number-dependent Q; Whitworth et al. (2025) Zeeman scaling extrapolates B_POS to core scale.  
  > "We used the same On–Off method as described in (cite: Valeille-Manet2025) (see their Sect. 3.1), which allows to isolate the emission of the cores by subtracting the contribution of their local environment." (Method); "To ensure a statistically meaningful estimate of the angular dispersion within each core, we computed it over an area that encompasses 10 beam-independent points. It assures a dispersion value within 15 % from the true dispersion (cite: Cortes2019)." (Method); "However, since estimating the Alfvénic Mach number itself requires an assumed value of $Q$, adopting a Mach-number-dependent $Q$ would introduce circularity into our analysis. We therefore opted to keep $Q=0.5$, consistent with the value adopted in much of the literature." (Method)
- Alternative: Searching N2D+(3-2) and HC3N(24-23) lines for the 11 cores without DCN or 13CS detections (rejected due to non-detection).  
  > "We also searched for emission in the $\mathrm{N_2D^+}$ (3–2) and $\mathrm{HC_3N}$ (24–23) transitions, other efficient tracers of dense gas available in the ALMA-IMF dataset, but without success." (Turbulence level in cores)
- Alternative: Alternative On-Off annulus configurations (1.5-2.5, 2.0-4.0, 3.5-4.5, and 4.5-5.5 core sizes) tested on five cores; retained 2.5-3.5 for consistency with Valeille-Manet et al. (2025) as differences were <= 0.17 km s^-1.  
  > "We considered four additional configurations (1.5–2.5, 2.0–4.0, 3.5–4.5, and 4.5–5.5 core sizes) and applied them to five cores with existing DCN On-Off measurements (#2, #7, #11, #14, and #15)." (Turbulence level in cores); "The choice of annulus size therefore has no significant impact on the derived linewidths, and we retained the 2.5–3.5 configuration for consistency with the approach adopted in (cite: Valeille-Manet2025)." (Turbulence level in cores)
- Alternative: Adopting a Mach-number-dependent DCF factor Q (Skalidis et al. 2021) or the compressible DCF formulation of Skalidis & Tassis (2021) (gives B_POS ~20% smaller; classical DCF with Q=0.5 retained).  
  > "However, since estimating the Alfvénic Mach number itself requires an assumed value of $Q$, adopting a Mach-number-dependent $Q$ would introduce circularity into our analysis. We therefore opted to keep $Q=0.5$, consistent with the value adopted in much of the literature." (Method); "We also compared our results with the method of (cite: Skalidis_Tassis2021), which proposes to replace $Q/\sigma_\theta$ by $1/\sqrt{2\sigma_\theta}$ in the DCF formula to account for non-Alfvénic compressible modes." (Magnetic field strength in cores)
- Alternative: Estimating three-beam velocity dispersion from the mean of the second moment map following Polychronakis et al. (2025) (yielded ~20% larger values; Gaussian fit with moment-1 std subtraction retained).  
  > "We also compared our three-beam scale velocity dispersion estimates with the method proposed by (cite: Polychronakis2025), which consists in taking the mean of the second moment map within the three-beam mask of each core as a proxy for the velocity dispersion used in magnetic field estimates." (Velocity structures in the three-beam area)
- Alternative: Ideal MHD flux-freezing extrapolation B proportional to n^(2/3) (Mestel 1966) instead of B proportional to n^0.53 (rejected because n^(2/3) only holds for spherical collapse without dynamically important B or resistive effects).  
  > "However, as shown by (cite: Tritsis2015), the relation $B \,\propto\, n^{2/3}$ is only valid in the case of spherical collapse, which is not expected when magnetic fields are dynamically important and resistive effects are present." (Magnetic field strength in cores)
- How they decided it was enough: Included all cores with at least 20 polarization semi-vectors above 3 sigma_P after Monte Carlo subsampling tests on cores #1 and #14 showed that reducing from 45 to 20 semi-vectors changes angle dispersion by at most 10%.  
  > "To maximize the number of cores for which a magnetic field strength can be derived, we included all cores containing at least 20 semi-vectors." (Method); "As shown in Appendix 7, the resulting angle dispersion varies by 10 % at most, demonstrating that the magnetic field strength estimate is robust against moderate incompleteness in the sampling." (Method)
- Limitation (authors): Core linewidths cannot disentangle micro-turbulence from organized motions (infall, rotation, converging flows) at the core scale because the beam size is comparable to the core size.  
  > "We will refer this as the turbulence level but we put forward that, within the cores, we cannot disentangle turbulence from other types of gas motion." (Turbulence level in cores); "Given that the beam size is comparable to the core size, the observed velocity field mainly reflects averaged motions at this scale, while potential sub-beam velocity structures would remain unresolved." (Velocity structures in the three-beam area)
- Limitation (authors): Using different molecular tracers (DCN, 13CS, CH3CN) may introduce small systematic differences in linewidth because they trace different gas layers.  
  > "The use of different tracers may introduce small systematic differences in linewidth values as they do not necessarily trace the same gas, but it is essential in order to make a statistical study of cores." (Method)
- Limitation (authors): Cores #3, #4, #5, and #9 have polarization angle dispersions sigma_theta > 25 deg, exceeding the regime where the classical DCF method is strictly reliable.  
  > "As explained in Sect. 4.1, the DCF method is reliable for regions with $\sigma_\theta < 25^{\circ}$, which here is the case for all the cores except cores #3, #4, #5 and #9 that we decided to keep in the following analysis in order to preserve the statistical significance of the sample." (Magnetic field strength in cores)
- Limitation (authors): Mass-to-flux ratios lambda_B only account for the plane-of-sky magnetic field (representing a lower limit to the 3D ratio) and suffer from projection/simulation biases noted by Tritsis et al. (2026).  
  > "It is important to note that this mass-to-flux ratio, which only accounts for the plane-of-sky magnetic field, represents a lower limit to the true mass-to-flux ratio that includes the full three-dimensional magnetic field." (Magnetic support and its relative contribution); "We also note that, as pointed out by (cite: Tritsis2026), mass-to-flux ratio estimates derived from $B_{\mathrm{POS}}$ are subject to significant limitations." (Magnetic support and its relative contribution)
- Limitation (authors): The simplified virial analysis neglects surface terms (confining thermal, kinetic, and magnetic pressure) and central protostellar masses, and depends on assumed temperature, geometry, and density profile index p.  
  > "We note that, for protostellar cores, the mass of the central protostar is not included in the total mass, as reliable measurements are not available." (Thermal and turbulent supports); "The surface terms (such as the confining pressure exerted by the surrounding medium) are extremely difficult to be constrained observationally and are therefore not included here, even though they would further reduce the effective values of $\alpha_{\mathrm{vir,B}}$." (Limitations of current observational estimates of the non-thermal supports)
- Caveat (inferred, ours): Extrapolating B_POS from the ~12,500 au three-beam scale down to ~2,500 au core scales using a literature Zeeman power-law (B proportional to n^0.53) assumes a smooth, universal scaling across a dynamical region where 3 cores (#4, #10, #146) actually have higher surrounding density than core density.
- Caveat (inferred, ours): In Table 1 vs Section 5.4 text, core #6's alpha_kin is listed as 0.32 in Table 1 but cited as 0.55 in the text of Section 5.4, indicating a minor internal inconsistency (likely due to p=0 vs p=2 or an earlier catalog mass).
- Caveat (inferred, ours): The two most massive hot cores (#1 and #4) rely on CH3CN(5_3-4_3) at 1.6 km s^-1 spectral resolution without an empirical scaling factor to DCN, which may systematically affect the high-mass end of the kinetic support distribution.

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Exact getsf core ellipse parameters (RA, DEC, semi-major/minor axes, position angle) and 1.3 mm integrated fluxes from Nony et al. (2023) and core temperatures from Motte et al. (2025) if not bundled with the paper
- Missing: Exact velocity integration ranges and sigma clipping thresholds used to generate the moment-0 and moment-1 maps for the three-beam velocity gradient subtraction
- Missing: CASA tclean script or exact parameters (robust, cell size, niter, threshold) used to mosaic the polarization pointings from #2015.1.01020.S
- Data volume (inferred): ~10–50 GB (three 12 m spectral line cubes for W43-MM1 from ALMA-IMF plus five full-polarization continuum pointings from 2015.1.01020.S)
- Score (inferred): 75/5, All four ALMA project codes, target coordinates, line frequencies, equations, and per-core intermediate and final measurements (Table 1 and Table B.1) are explicitly provided, though full end-to-end reproduction requires external ALMA-IMF catalog tables (Nony et al. 2023; Motte et al. 2025) and inherited imaging parameters (Cunningham et al. 2023; Arce-Tord et al. 2020).
- Rediscovery candidate: yes, All ALMA datasets are public, the mathematical recipe for On-Off/On line fitting, DCF angle dispersion, density extrapolation, and virial parameters is explicit, and complete core-by-core numeric answer keys (Tables 1 and B.1) are published in the paper.

## Links

- Method: Men’shchikov2021 (getsf source extraction algorithm used to build the core catalog)
- Method: Hull&Plambeck2015 (Pixel-by-pixel linear polarization debiasing method for low-SNR regions)
- Method: Valeille-Manet2025 (On-Off spectral extraction method to isolate core emission from surrounding environment)
- Method: Davis1951; Chandrasekhar&Fermi1953 (Davis-Chandrasekhar-Fermi (DCF) method to estimate plane-of-sky magnetic field strength)
- Method: LeGouellec2020 (Direct formula for computing polarization angle dispersion from Stokes Q and U)
- Method: Whitworth2025 (Empirical magnetic field-density scaling relation B proportional to n^0.53 used to extrapolate B_POS to core scales)
- Companion: Motte2018 (Initial W43-MM1 ALMA continuum core catalog)
- Companion: Nony2020 (Outflow-based prestellar/protostellar core classification in W43-MM1)
- Companion: Arce-Tord2020 (First presentation and imaging methodology of the W43-MM1 ALMA 1.3 mm dust polarization data (#2015.1.01020.S))
- Companion: Motte2022 (ALMA-IMF Large Program overview paper)
- Companion: Cunningham2023 (ALMA-IMF 12 m spectral line data reduction and DCN/13CS datacube release)
- Companion: Nony2023 (Extended W43-MM1 core catalog and bsens-denoised 1.3 mm continuum map)
- Companion: Valeille-Manet2025 (Study of high-mass prestellar cores in W43-MM1 introducing the On-Off spectral method)
- Companion: Motte2025 (Refined core dust temperatures, masses, and protostellar luminosities used in this study)
- Related: ALMA-IMF

## Checks

```json
{
 "quotes": 168,
 "quotes_ok": 168,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 10,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 18,
 "numeric_problems": 0,
 "fill": {
  "facts": 94,
  "stated": 65,
  "rate": 0.691
 },
 "evidence_ok": true
}
```
