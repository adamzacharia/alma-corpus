# Inadequate turbulent support in low-metallicity molecular clouds

`2025NatAs...9..406L` | Nature Astronomy 2025 | first author: Lin, Lingrui | arXiv: 2501.07636 | DOI: 10.1038/s41550-024-02440-3

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: milky_way_ism, nearby_galaxies, star_formation
- Question: Are molecular clouds in the low-metallicity Galactic outer disk and in metal-poor dwarf galaxies in virial equilibrium (virial parameter near unity), as measured from optically thin 13CO?  
  > "most previous studies on the dynamic states of molecular clouds were based solely on the more luminous but optically thick" (main text); "but leaves the Galactic outer disk less explored." (main text)
- Target **Galactic outer-disk molecular clouds (9 < Rgc < 25 kpc; IRAM 30 m, ALMA TP, SMT)**: coordinates not stated in the text (per-cloud l, b are given in the Supplementary tables)  
  > "OTF maps towards 26 outer-disk molecular clouds in the third Galactic quadrant" (Observations towards the Galactic outer disk clouds); "For most outer-disk clouds, there were no nearby parallax sources. Consequently, we adopted their kinematic distances based on the Galactic rotation curve." (Distances and Galactocentric radii); z/distance per-cloud kinematic distances (Bayesian PDF); e.g. clouds at Rgc > 15 kpc  
  > "OTF maps towards 26 outer-disk molecular clouds in the third Galactic quadrant" (Observations towards the Galactic outer disk clouds); "For most outer-disk clouds, there were no nearby parallax sources. Consequently, we adopted their kinematic distances based on the Galactic rotation curve." (Distances and Galactocentric radii); distance from BeSSeL Galactic rotation curve code (Reid et al. 2019)  
  > "OTF maps towards 26 outer-disk molecular clouds in the third Galactic quadrant" (Observations towards the Galactic outer disk clouds); "For most outer-disk clouds, there were no nearby parallax sources. Consequently, we adopted their kinematic distances based on the Galactic rotation curve." (Distances and Galactocentric radii)
- Target **LMC regions (N59C, A439, GMC104, GMC1, Planck cold cloud)**: coordinates _not stated_; z/distance 49.59 +/- 0.63 kpc  
  > "(ALMA 12 m only) for N59C, A439, GMC104 and GMC1" (Archival data); "$d_{\rm LMC}=49.59\pm0.63$ kpc (ref. )" (Distances and Galactocentric radii); distance from not stated (citation is blank in the paper text)  
  > "(ALMA 12 m only) for N59C, A439, GMC104 and GMC1" (Archival data); "$d_{\rm LMC}=49.59\pm0.63$ kpc (ref. )" (Distances and Galactocentric radii)
- Target **SMC regions (N22, SWBarN, SWBarS, SWDarkPK)**: coordinates _not stated_; z/distance 62.44 +/- 1.28 kpc  
  > "Four regions in the SMC (N22, SWBarN, SWBarS and SWDarkPK) were observed using the Atacama Compact Array" (Archival data); "$d_{\rm SMC}=62.44\pm1.28$ kpc (ref. )" (Distances and Galactocentric radii); distance from not stated (citation is blank in the paper text)  
  > "Four regions in the SMC (N22, SWBarN, SWBarS and SWDarkPK) were observed using the Atacama Compact Array" (Archival data); "$d_{\rm SMC}=62.44\pm1.28$ kpc (ref. )" (Distances and Galactocentric radii)
- Target **NGC 6822**: coordinates _not stated_; z/distance 474 +/- 13 kpc  
  > "$d_{\rm NGC~6822}=474\pm13$ kpc (ref. )" (Distances and Galactocentric radii); distance from not stated (citation is blank in the paper text)  
  > "$d_{\rm NGC~6822}=474\pm13$ kpc (ref. )" (Distances and Galactocentric radii)
- Target **DDO 70 (literature clump properties)**: coordinates _not stated_; z/distance 1.38 Mpc  
  > "at a distance of 1.38 Mpc) (cite: 2020ApJ...892..147S)" (Archival data); distance from Shi et al. 2020 (cite: 2020ApJ...892..147S)  
  > "at a distance of 1.38 Mpc) (cite: 2020ApJ...892..147S)" (Archival data)

## Data provenance

- ALMA projects: 2021.2.00175.S, 2013.1.00652.S, 2015.1.00581.S, 2019.1.01641.S
- bands: _not stated_
- frequencies and spectral setup: ALMA TP: 12CO and 13CO J=2-1 covered; 13CO J=2-1 rest frequency 220.39868420 GHz, velocity resolution 0.16 km/s  
  > "The $J=2\rightarrow1$ transitions of $^{12}$CO and $^{13}$CO were covered." (Observations towards the Galactic outer disk clouds); "(220.39868420 GHz)" (Observations towards the Galactic outer disk clouds)
- continuum bandwidth: _not stated_
- arrays: New data: ALMA Total Power (TP) Array, 26 outer-disk clouds. Archival: ACA (7 m + TP) for SMC (2013.1.00652.S), 12 m array for SMC (2015.1.00581.S) and NGC 6822 (2019.1.01641.S), 12 m / 12 m + TP cubes for LMC from Wong et al. 2019  
  > "OTF maps towards 26 outer-disk molecular clouds in the third Galactic quadrant" (Observations towards the Galactic outer disk clouds); "Four regions in the SMC (N22, SWBarN, SWBarS and SWDarkPK) were observed using the Atacama Compact Array (7 m array plus the TP Array; 2013.1.00652.S) and the ALMA 12 m array (2015.1.00581.S)." (Archival data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ALMA TP beam ~29.5 arcsec; SMC cubes restored to 2.0 arcsec (ideal ~1 arcsec); NGC 6822 restored to 2.4 arcsec; LMC cubes 3.5 arcsec  
  > "The $\theta_{\rm beam}$ and the velocity resolution at the rest frequency of $^{13}$CO $J=2\rightarrow1$ (220.39868420 GHz) were $\sim29.5''$ and 0.16 $\rm \;km\;s^{-1}$, respectively." (Observations towards the Galactic outer disk clouds); "The ideal angular resolution of these observations was $\sim1''$." (Archival data)
- max recoverable scale: _not stated_
- sensitivity: ALMA TP typical Tmb,rms ~0.04 K; SMC interferometry cubes ~0.4 K (~0.06 Jy per beam); NGC 6822 ~0.01 K (~0.6 mJy per beam)  
  > "The typical $T_{\rm mb,rms}\approx0.04$ K." (Observations towards the Galactic outer disk clouds); "The typical r.m.s. brightness temperature was $\sim0.4$ K ($\sim$ 0.06 Jy per beam)." (Archival data)
- time on source: _not stated_
- observing dates: ALMA TP: 29 January to 28 September 2022 (Cycle 8)  
  > "were executed during ALMA cycle 8 from 29 January to 28 September 2022." (Observations towards the Galactic outer disk clouds)
- pi or archival as stated: 2021.2.00175.S is PI L. Lin; SMC, NGC 6822 and LMC data are archival / from the literature  
  > "The ALMA observations (Project ID 2021.2.00175.S, PI L. Lin)" (Observations towards the Galactic outer disk clouds); "We retrieved ALMA $^{13}$CO $J=2\rightarrow1$ data from the ALMA archival system" (Archival data)
- Line: 13CO J=1-0 (110.20135430 GHz)
- Line: 13CO J=2-1 (220.39868420 GHz)
- Line: 12CO J=2-1 (ALMA TP) and J=1-0 (IRAM, used for Tex) (not stated)
- Other facility **IRAM 30 m (EMIR, FTS200)**: 13CO J=1-0 (and 12CO J=1-0 in 2023) OTF maps of 14 + 8 outer-disk clouds (Projects 031-17 and 102-22)  
  > "Observations with the IRAM 30 m telescope were executed from 29 August to 5 September 2017 (Project ID 031-17, principal investigator (PI) Z.-Y. Zhang)" (Observations towards the Galactic outer disk clouds)
- Other facility **SMT**: 12CO and 13CO J=2-1 maps; four targets used (Project Lin_L_22B_1)  
  > "The SMT observations (Project ID Lin_L_22B_1, PI L. Lin) were executed from 29 October to 1 November 2022." (Observations towards the Galactic outer disk clouds)
- Other facility **Galactic Ring Survey (FCRAO)**: 13CO J=1-0 data for inner-Galaxy clouds  
  > "for a sample of inner disk molecular clouds" (Archival data)
- Other facility **BeSSeL survey code**: Bayesian distance and Rgc of Galactic clouds  
  > "using the code provided by the BeSSeL survey" (Distances and Galactocentric radii)
- Other facility **WISE, VLASS, NVSS**: Mid-infrared and radio continuum images to check star-formation activity  
  > "Wide-field Infrared Survey Explorer archive" (Low turbulence injection and star-formation activities in the Galactic outer disk)
- External data: LMC 13CO cubes (12 m, and 12 m + TP for the Planck cold cloud)  
  > "We used the $^{13}$CO cubes provided in the literature(cite: 2019ApJ...885...50W) for several regions in the LMC." (Archival data) [from Wong et al. 2019 (cite: 2019ApJ...885...50W)]
- External data: Galactic Ring Survey 13CO J=1-0 inner-Galaxy cloud sample  
  > "We retrieved the $^{13}$CO $J=1\rightarrow0$ data for a sample of inner disk molecular clouds (cite: 2009ApJ...699.1092H) studied by the Galactic Ring Survey (GRS)(cite: 2006ApJS..163..145J)." (Archival data) [from Heyer et al. 2009 (cite: 2009ApJ...699.1092H); Jackson et al. 2006 (cite: 2006ApJS..163..145J)]
- External data: DDO 70 clump properties and boundary surface density Sigma_limit = 756 +/- 468 Msun/pc^2  
  > "We also took the physical properties of molecular clumps from an extremely metal-poor dwarf galaxy DDO 70" (Archival data); "$\Sigma_{\rm limit}=756\pm468\,M_{\odot}\,\rm pc^{-2}$" (Physical properties of molecular clouds) [from Shi et al. 2020 (cite: 2020ApJ...892..147S)]
- External data: 12C/13C = 5.87 Rgc + 13.25 isotopic ratio gradient  
  > "$^{12}$C/$^{13}$C$=5.87R_{\rm gc}+13.25$" (H2 surface density) [from Jacob et al. 2020 (cite: 2020A&A...640A.125J)]
- External data: Galactic O/H gradient proportional to 10^(-0.044(Rgc - Rgc,sun))  
  > "O/H$\propto10^{-0.044(R_{\rm gc}-R_{\rm gc,\odot})}$" (H2 surface density) [from Mendez-Delgado et al. 2022 (cite: 2022MNRAS.510.4436M)]
- External data: Solar-neighbourhood H2/12CO = 6.0e3  
  > "is $6.0\times10^{3}$, measured by absorption lines in nearby clouds against background stars" (H2 surface density) [from Lacy et al. 2017 (cite: 2017ApJ...838...66L)]
- External data: Galactic rotation curve model and distance code (BeSSeL), Rgc,sun = 8.15 kpc  
  > "$R_{\rm gc, \odot}=8.15$ kpc is the Galactocentric radius of the Sun" (Distances and Galactocentric radii) [from Reid et al. 2019 (cite: 2019ApJ...885..131R)]
- External data: Density-profile index k = 1.8 for DDO 70 clumps  
  > "We adopt $k=1.8$ for typical star forming clumps in the Milky Way (cite: 2002ApJS..143..469M)." (Physical properties of molecular clouds) [from Mueller et al. 2002 (cite: 2002ApJS..143..469M)]
- External data: Adopted Tex = 15 K as typical IRDC / Planck cold clump kinetic temperature  
  > "we took $T_{\rm ex}=15$ K, which is the typical kinetic temperature" (H2 surface density) [from Tang et al. 2017 (cite: 2017A&A...598A..30T); Chira et al. 2013 (cite: 2013A&A...552A..40C); Feher et al. 2022 (cite: 2022ApJS..258...17F)]
- External data: Literature 12CO cloud measurements used as a sanity check  
  > "we also collected $^{12}$CO measurements from the literature" (Caveats of studying alpha_vir using low-J 12CO lines) [from Sun et al. 2015 (cite: 2015ApJ...798L..27S); Sun et al. 2017 (cite: 2017ApJS..230...17S); Oka et al. 2001 (cite: 2001ApJ...562..348O)]
- External data: Distances to LMC, SMC, NGC 6822 and H2/13CO = 3e6 for the LMC (citations blank in the paper text)  
  > "We assumed $\rm H_{2}/^{13}CO=3\times10^{6}$ (ref. ) for molecular clouds in the LMC." (H2 surface density) [from not stated (blank ref. in text)]
- Simulation/model as data: Mock Gaussian clouds (major axis 4 to 100 arcsec, aspect ratio 0.2 to 1.0) convolved with the telescope beam and given noise, at peak S/N = 10, to test radius, flux and alpha_vir bias  
  > "we generated a set of mock clouds to mimic real observations." (Possible bias in measuring cloud properties); "The peak values of the Gaussian models were scaled such that the final convolved maps have a peak $S/N=10$" (Possible bias in measuring cloud properties)

## Processing

### Calibration

- pipeline or manual: ALMA TP: standard pipeline; archival interferometry: CASA pipeline; NGC 6822: standard CASA pipeline  
  > "The data were reduced with the standard pipeline." (Observations towards the Galactic outer disk clouds); "We calibrated the data with the standard CASA pipeline." (Archival data)
- casa version: SMC calibration: CASA pipeline v4.5.2-r36115 and v4.2.2-r30986; imaging in CASA v6.5.3  
  > "The interferometry data (12 m plus 7 m arrays) were calibrated with the CASA pipeline (v4.5.2-r36115 and v4.2.2-r30986)." (Archival data); "The imaging was done by `tclean` in CASA v6.5.3." (Archival data)
- pipeline version: _not stated_
- archive products used as is: SMC: product TP cubes feathered with interferometry cubes  
  > "The interferometry cubes were combined with the product TP cubes using the `feather` task." (Archival data)
- flux calibrator: _not stated_
- flux scale uncertainty: 20% adopted for M_mol as a conservative flux-calibration error  
  > "which is a conservative estimate for the flux calibration error for millimetre-wave observations" (Physical properties of molecular clouds)
- self calibration: _not stated_

### Imaging

- task: tclean in CASA v6.5.3 (SMC, NGC 6822); feather for SMC interferometry + TP  
  > "The imaging was done by `tclean` in CASA v6.5.3." (Archival data)
- deconvolver: _not stated_
- weighting robust: briggs, robust = 2.0 (SMC and NGC 6822)  
  > "we imaged the data with $weighting=`briggs$’ ($robust=2.0$), $cell=0.3''$ and $restoringbeam=2.4''$" (Archival data)
- uv taper: _not stated_
- cell size: SMC 0.4 arcsec; NGC 6822 0.3 arcsec  
  > "we imaged the interferometry data with $weighting=`briggs$’ ($robust=2.0$), $cell=0.4''$ and $restoringbeam=2.0''$" (Archival data); "we imaged the data with $weighting=`briggs$’ ($robust=2.0$), $cell=0.3''$ and $restoringbeam=2.4''$" (Archival data)
- image size: _not stated_
- masking: 3DBAROLO source finder: MASK=Search, SNRCUT=3, GROWTHCUT=2.5 (S/N>3 grown to S/N>2.5); GRS: THRESHOLD=0.39, GROWTHTHRESHOLD=0.33  
  > "we set `MASK=Search`, `SNRCUT=3` and `GROWTHCUT=2.5`." (H2 surface density); "we set `THRESHOLD=0.39` and `GROWTHTHRESHOLD=0.33`." (H2 surface density)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: SMC: 12 m + 7 m interferometry cubes combined with product TP cubes using feather  
  > "The interferometry cubes were combined with the product TP cubes using the `feather` task." (Archival data)
- smoothing: Restoring beam fixed to 2.0 arcsec (SMC) and 2.4 arcsec (NGC 6822) for consistency; Galactic cubes smoothed to 2 pc in a robustness test  
  > "First, we smoothed all line cubes for the Galactic molecular clouds to the same physical resolution of 2 pc" (Possible bias in measuring cloud properties)
- final beam: SMC 2.0 arcsec; NGC 6822 2.4 arcsec; LMC 3.5 arcsec  
  > "All cubes have a restored $\theta_{\rm beam}=3.5''$" (Archival data); "we imaged the interferometry data with $weighting=`briggs$’ ($robust=2.0$), $cell=0.4''$ and $restoringbeam=2.0''$" (Archival data)
- final rms: SMC ~0.4 K (~0.06 Jy/beam); NGC 6822 ~0.01 K (~0.6 mJy/beam); LMC ~0.2 K  
  > "The typical r.m.s. brightness temperature was $\sim0.4$ K ($\sim$ 0.06 Jy per beam)." (Archival data)

### Inherited from earlier work

- IRAM 2023 cubes reduced and built with the same procedure as Project 031-17  
  > "We reduced the data and built the spectral cubes following the same procedure used for Project 031-17." (Observations towards the Galactic outer disk clouds) [from Project 031-17 procedure (same paper)]
- Distances and Rgc from the BeSSeL Bayesian code and rotation-curve model  
  > "using the code provided by the BeSSeL survey (cite: 2019ApJ...885..131R)" (Distances and Galactocentric radii) [from (cite: 2019ApJ...885..131R)]
- DDO 70 cloud properties measured independently of XCO, taken from the earlier work  
  > "the cloud properties were measured independently of the uncertain" (Archival data) [from (cite: 2020ApJ...892..147S)]
- Inner-Galaxy cloud sample and GRS data  
  > "We retrieved the $^{13}$CO $J=1\rightarrow0$ data for a sample of inner disk molecular clouds (cite: 2009ApJ...699.1092H) studied by the Galactic Ring Survey (GRS)(cite: 2006ApJS..163..145J)." (Archival data) [from (cite: 2009ApJ...699.1092H); (cite: 2006ApJS..163..145J)]
- SMC ALMA data sets (imaged here with chosen parameters)  
  > "from the ALMA archival system (Project IDs 2013.1.00652.S and 2015.1.00581.S)(cite: 2018ApJ...853..111J)" (Archival data) [from (cite: 2018ApJ...853..111J)]

### Not stated but needed to reproduce (our reading)

- ALMA TP (2021.2.00175.S): pipeline/CASA version, gridding and imaging parameters of the TP cubes, and line-free channels or baseline treatment are not given
- tclean deconvolver, niter/threshold, masking and line-free channels / continuum subtraction for the SMC and NGC 6822 cubes
- The LMC cubes (Wong et al. 2019) are used as-is; their processing is not described here
- Which clouds have complementary 12CO and so a measured Tex versus the Tex = 15 K default is not tabulated in the text
- Criteria for visually identifying clouds and excluding blended ones (GRS, LMC, SMC, NGC 6822) are qualitative
- Citations for the 12C/13C and O/H gradients, the LMC H2/13CO value and the dwarf-galaxy distances are blank in the text, so exact source papers must be recovered from the reference list
- SMT reduction procedure and 12CO maps used for Tex are not described in detail
- Systematic and random error propagation for alpha_vir (adopted 10%, 10%, 20% errors) is stated but the combination formula is not

## Analysis recipe

1. **Reduce single-dish and TP data into cubes**: IRAM: GILDAS/CLASS baseline subtraction per FTS200 unit and xy_map gridding; ALMA TP: standard pipeline  
  > "The OTF mapping data were reduced with `GILDAS/CLASS`." (Observations towards the Galactic outer disk clouds); "The data were reduced with the standard pipeline." (Observations towards the Galactic outer disk clouds)
   - software: GILDAS/CLASS, ALMA pipeline
   - parameter: IRAM cube pixel size 4 arcsec x 4 arcsec  
  > "We used the `xy_map` task to build regular $^{13}$CO spectral cubes with pixel sizes of 4$''\times$4$''$." (Observations towards the Galactic outer disk clouds)
   - assumption: IRAM main beam efficiency 0.78  
  > "Given a main beam efficiency ($\eta_{\rm beam}$) of 0.78" (Observations towards the Galactic outer disk clouds)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive cloud distances and Galactocentric radii**: BeSSeL Bayesian code from l, b, VLSR; spiral-arm term dropped; kinematic distance from the rotation curve for most outer-disk clouds  
  > "The code calculates the probability density function (PDF) of cloud distance through a Bayesian approach" (Distances and Galactocentric radii); "we excluded the spiral arm model for all Galactic molecular clouds." (Distances and Galactocentric radii)
   - software: BeSSeL distance code
   - parameter: Rgc,sun = 8.15 kpc  
  > "$R_{\rm gc, \odot}=8.15$ kpc is the Galactocentric radius of the Sun" (Distances and Galactocentric radii)
   - assumption: Heights above the plane negligible (|b| < 4 deg)  
  > "so the heights from the Galactic plane were negligible." (Distances and Galactocentric radii)
   - fitting: Most probable distance and associated error from the Bayesian PDF  
  > "we used the most probable distance and the associated error given by the Bayesian inference." (Distances and Galactocentric radii)
   - validation: Results unchanged whether or not spiral arm models were used  
  > "Our results were not influenced, regardless of whether the spiral arm models were implemented." (Distances and Galactocentric radii)
3. **Build source masks in each cube**: Source-finding algorithm in 3DBAROLO, with S/N-based growth  
  > "We first generated source masks for each spectral cube using the source-finding algorithm embedded in" (H2 surface density)
   - software: 3DBAROLO
   - parameter: MASK=Search, SNRCUT=3, GROWTHCUT=2.5; GRS: THRESHOLD=0.39 K, GROWTHTHRESHOLD=0.33 K  
  > "we set `MASK=Search`, `SNRCUT=3` and `GROWTHCUT=2.5`." (H2 surface density); "we set `THRESHOLD=0.39` and `GROWTHTHRESHOLD=0.33`." (H2 surface density)
   - fitting: _not stated_
   - validation: _not stated_
4. **Compute 13CO column density under LTE**: Solve 13CO optical depth per voxel from radiative transfer, integrate over velocity to get N(13CO)  
  > "under the assumption of local thermodynamic equilibrium (LTE)." (H2 surface density); "The optical depth of $^{13}$CO ($\tau_{13}$) of each voxel in the line cube was solved by the radiative transfer equation" (H2 surface density)
   - parameter: Tex from optically thick 12CO peak where available, else Tex = 15 K  
  > "we took $T_{\rm ex}=15$ K, which is the typical kinetic temperature" (H2 surface density)
   - assumption: 13CO and 12CO share the same Tex; 12CO optically thick; beam filling factor unity; Tbg = 2.73 K  
  > "The beam filling factor ($f_{\rm bm}$) was assumed to be unity." (H2 surface density); "was taken as the brightness temperature of the cosmic microwave background" (H2 surface density)
   - fitting: _not stated_
   - validation: Tex = 15 K may overestimate N(13CO) by <~20% for J=1-0; LTE deviation <~40%; total within 60%  
  > "Therefore, the overall overestimation due to the assumptions on" (Systematic errors in M_mol and alpha_vir)
5. **Convert N(13CO) to N(H2)**: N(H2) = N(13CO) x 12CO/13CO x H2/12CO with radius-dependent ratios for the Galaxy; fixed H2/13CO for LMC, SMC and NGC 6822  
  > "We assumed $\rm H_{2}/^{13}CO=3\times10^{6}$ (ref. ) for molecular clouds in the LMC." (H2 surface density); "We adopted $\rm H_{2}/^{13}CO=7.5\times10^{6}$ for the SMC and NGC 6822, which was scaled from the LMC value through their metallicity ratio." (H2 surface density)
   - parameter: 12C/13C = 5.87 Rgc + 13.25; H2/12CO at the solar radius 6.0e3, scaling inversely with O/H  
  > "$^{12}$C/$^{13}$C$=5.87R_{\rm gc}+13.25$" (H2 surface density); "is $6.0\times10^{3}$, measured by absorption lines in nearby clouds against background stars" (H2 surface density)
   - assumption: 12CO/13CO equals the isotopic 12C/13C ratio; H2/12CO inversely proportional to O/H  
  > "O/H$\propto10^{-0.044(R_{\rm gc}-R_{\rm gc,\odot})}$" (H2 surface density)
   - fitting: _not stated_
   - validation: Test with constant H2/13CO makes the alpha_vir trend flatter but not removed  
  > "shows a test under an extreme condition" (Systematic errors in M_mol and alpha_vir)
6. **Measure cloud radius, velocity dispersion and mass**: Measurements within the half-peak isophote of N(H2); beam-deconvolved equivalent radius, intensity-weighted sigma_v corrected for channel width, mass from integrated N(H2)  
  > "of molecular clouds were all measured within the half-peak isophote of" (Physical properties of molecular clouds)
   - parameter: Adopted uncertainties: 10% for r_cloud and sigma_v, 20% for M_mol  
  > "We also applied an uncertainty of $10\%$ for $\sigma_{\rm v}$." (Physical properties of molecular clouds); "We adopted an uncertainty of $20\%$ for $M_{\rm mol}$" (Physical properties of molecular clouds)
   - assumption: Mean molecular weight 1.36 including helium  
  > "$\mu\approx1.36$ is the mean molecular weight considering the mass of helium" (Physical properties of molecular clouds)
   - fitting: _not stated_
   - validation: Mock Gaussian-cloud tests: radius and flux within 10% for roundish, marginally resolved clouds  
  > "is within 10%, consistent with the theoretical prediction" (Possible bias in measuring cloud properties)
7. **Compute virial parameter and its trend with metallicity**: alpha_vir = 5 sigma_v^2 R / (G M); galactic metallicity from the O/H gradient; ordinary least-squares fit of log alpha_vir versus log Z  
  > "\alpha_{\rm vir} = \frac{5\sigma_{\rm v}^{2}R_{\rm cloud}}{GM_{\rm mol}}" (The virial parameter); "The gas-phase metallicities of the Galactic clouds were estimated using the Galactic radial gradient of O/H" (Metallicity estimate)
   - parameter: Supervirial: alpha_vir > 1; subvirial: alpha_vir < 1; factor-of-two virial vs equipartition not distinguished  
  > "we could not distinguish them in this work." (The virial parameter)
   - assumption: Uniform sphere (a = 1); a ~ 1.4 +/- 0.3 for realistic density profiles would lower alpha_vir  
  > "Possible deviations from a uniform-spherical cloud ($a>1$) would even further consolidate our results." (The general virial theorem)
   - fitting: Ordinary least squares on the Galactic 13CO measurements  
  > "This correlation was fitted using ordinary least squares for the" (Caveats of studying alpha_vir using low-J 12CO lines)
   - validation: Selection-bias test comparing clouds at similar heliocentric distance; 2 pc smoothing test; 12CO-based sanity check  
  > "have at least $\times$5 smaller" (Selection bias); "Then, we followed the same procedures to measure the cloud" (Possible bias in measuring cloud properties)
8. **Estimate the magnetic field needed to support subvirial clouds**: General virial theorem with magnetic term, assuming efficient ion-neutral momentum transfer; compare required B with B versus nH relation from Zeeman data  
  > "Using the general virial theorem and assuming efficient momentum transfer between ions and neutral species" (main text)
   - parameter: Cosmic-ray ionization rate 1e-17 s^-1; ionization fraction ~1e-7; MHD cutoff wavelength <~0.01 pc  
  > "($\zeta_{\rm H_{2}}=10^{-17}$ s$^{-1}$)" (The general virial theorem)
   - assumption: External pressure neglected in the outer Galaxy; external magnetic field neglected (~10 uG vs ~100 uG required)  
  > "Neglecting the minor contribution from $P_{\rm e}$ in the outer Galaxy" (The general virial theorem)
   - fitting: _not stated_
   - validation: Required B is consistent with the Crutcher B versus nH relation  
  > "field strengths required to support subvirial clouds are consistent with expectations" (main text)

## Software

- **GILDAS/CLASS** : Reducing IRAM 30 m OTF data, xy_map cube building  
  > "The OTF mapping data were reduced with `GILDAS/CLASS`." (Observations towards the Galactic outer disk clouds)
- **CASA (pipeline, tclean, feather)** pipeline v4.5.2-r36115 and v4.2.2-r30986 (SMC calibration); v6.5.3 (imaging): Calibration and imaging of archival SMC and NGC 6822 ALMA data, TP feathering  
  > "The imaging was done by `tclean` in CASA v6.5.3." (Archival data); "The interferometry cubes were combined with the product TP cubes using the `feather` task." (Archival data)
- **3DBAROLO** : Source-finding masks for each cube  
  > "We first generated source masks for each spectral cube using the source-finding algorithm embedded in" (H2 surface density)
- **BeSSeL distance code** : Bayesian cloud distance PDFs and Rgc  
  > "using the code provided by the BeSSeL survey" (Distances and Galactocentric radii)
- **critical_densities (GitHub)** : Critical density of 12CO J=1-0  
  > "Code for calculating the critical densities can be obtained from GitHub" (Code Availability)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Slope of log(alpha_vir) vs log(Z/Zsun), Galactic 13CO clouds (OLS) | 1.5 | 0.1 | dimensionless | 7 | $\log(\alpha_{\rm vir}) = (1.5\pm0.1)\times\log(Z [Z_{\odot}])+(0.56\pm0.03)$ |
| Intercept of log(alpha_vir) vs log(Z/Zsun) fit | 0.56 | 0.03 | dimensionless | 7 | $\log(\alpha_{\rm vir}) = (1.5\pm0.1)\times\log(Z [Z_{\odot}])+(0.56\pm0.03)$ |
| Number of new outer-disk clouds in 9<=Rgc<15, 15<=Rgc<20 and Rgc>=20 kpc bins | 33, 13, six | not stated | clouds | 6 | are 33, 13, and six, respectively. |
| Critical density of 12CO J=1-0 at Tk = 20 K, optically thin | ~3.5e2 | not stated | cm^-3 | 0 | $\sim 3.5\times 10^2$cm$^{-3}$ |
| alpha_vir ratio of Rgc>20 kpc clouds to Rgc~13 kpc clouds at 15-20 kpc distance | at least 5 times smaller | not stated | dimensionless | 7 | have at least $\times$5 smaller |
| Radius and flux measurement bias for roundish, marginally resolved mock clouds | within 10% | not stated | percent | 6 | is within 10%, consistent with the theoretical prediction |

## Qualitative findings

- alpha_vir decreases from supervirial in the inner Galaxy to subvirial at Rgc > 15 kpc (Z < 0.5 Zsun), and metal-poor dwarf galaxies extend the trend  
  > "in the metal-rich inner Galaxy to subvirial states" (main text)
- Classical virial equilibrium between kinetic and gravitational energy is not universal  
  > "Consequently, we found that the classical virial equilibrium between" (main text)
- Magnetic field is the most plausible additional support in low-Z clouds  
  > "The most plausible mechanism appears to be the magnetic field" (main text)
- Cloud dynamic states depend strongly on the ambient environment  
  > "the dynamic states of molecular clouds seem to depend strongly on the ambient environments" (main text)

## Claim tuples

- H: Molecular clouds in low-metallicity environments are in virial equilibrium with alpha_vir ~ 1 | E: 13CO J=1-0 and 2-1 maps of outer-disk clouds (IRAM, ALMA TP, SMT) plus archival Galactic and dwarf-galaxy cubes; N(H2) from LTE 13CO with abundance gradients; alpha_vir per cloud | R: alpha_vir falls from supervirial in the inner Galaxy to subvirial at Rgc > 15 kpc, and low-Z dwarf galaxies follow the trend | F: Classical virial equilibrium is not universal; turbulence alone does not balance self-gravity at low Z | **supported**
- H: Low-Z clouds have lower velocity dispersion than predicted by Larson's relation | E: sigma_v versus R_cloud for Galactic clouds and dwarf-galaxy clouds | R: Clouds at Rgc > 15 kpc and metal-poor dwarf-galaxy clouds lie below the classical sigma_v-R relation | F: Reduced turbulent support in metal-poor clouds | **supported**
- H: Magnetic fields can supply the missing support in subvirial low-Z clouds | E: General virial theorem with magnetic term compared with the B versus nH relation from Zeeman measurements | R: Required B-field strengths are consistent with those expected from the inner-Galaxy relation | F: Magnetic fields can dominate cloud support at low metallicity; mechanism remains speculative | **partially**
- H: The alpha_vir trend is an artifact of resolution, sensitivity or distance selection | E: Mock Gaussian clouds, smoothing all Galactic cubes to 2 pc, comparison at similar heliocentric distances | R: Measured alpha_vir is unbiased for well-sampled clouds and the trend persists after smoothing and distance matching | F: The alpha_vir versus metallicity trend is robust to these biases | **supported**

## Reasoning

- Why this data: Outer-disk low-Z clouds were poorly explored in 13CO  
  > "but leaves the Galactic outer disk less explored." (main text)
- Why this method: 13CO low-J lines are optically thin for most cloud mass and so trace H2 mass and velocity dispersion better than 12CO  
  > "are optically thin for the bulk of the mass in molecular clouds in most cases" (main text)
- Alternative: Spiral-arm prior excluded from the distance PDFs because it is poorly constrained at Rgc >~ 15 kpc  
  > "we excluded the spiral arm model for all Galactic molecular clouds." (Distances and Galactocentric radii)
- Alternative: Extreme test with constant H2/13CO (no abundance gradients) flattens but does not remove the alpha_vir trend  
  > "shows a test under an extreme condition" (Systematic errors in M_mol and alpha_vir)
- How they decided it was enough: _not stated_
- Limitation (authors): Systematic errors are not propagated in the quoted uncertainties  
  > "Systematic errors are not involved in error propagation." (Physical properties of molecular clouds)
- Limitation (authors): Slope of the alpha_vir versus Z trend is sensitive to the adopted H2/13CO abundance ratio  
  > "The slope of this correlation is sensitive to the adopted" (main text)
- Limitation (authors): Physical mechanisms for B-field-dominated dynamics are unclear  
  > "However, the detailed underlying physical mechanisms are still unclear." (Possible mechanisms for B-field-dominated cloud dynamics at low metallicities)
- Caveat (inferred, ours): The metallicity trend depends on extrapolated 12C/13C and O/H gradients beyond 12-18 kpc, which the paper says are poorly constrained
- Caveat (inferred, ours): Kinematic distances at large Rgc carry up to ~40% mass uncertainty and enter alpha_vir directly
- Caveat (inferred, ours): Magnetic support is inferred, not measured; no B-field observations of these clouds
- Caveat (inferred, ours): Dwarf-galaxy points mix different tracers, resolutions and an assumed density profile for DDO 70
- Caveat (inferred, ours): Mixed telescopes and beams (23 to 46 arcsec versus 2 to 3.5 arcsec) sample different physical scales

## Reproducibility

- Data public (paper): Reduced cubes of the new observations on figshare; ALMA data from the ALMA archive  
  > "(1) reduced data cubes of the new observations presented in this work (subfolder GMPMC_line_fitscubes)" (Data Availability); "from the ALMA archival system (Project IDs 2013.1.00652.S and 2015.1.00581.S)" (Archival data)
- Products in archive: _not stated_
- Code: Critical-density code on GitHub; analysis scripts not stated as released  
  > "Code for calculating the critical densities can be obtained from GitHub" (Code Availability)
- Missing: ALMA TP imaging parameters and pipeline version
- Missing: tclean cleaning parameters for archival SMC / NGC 6822 data
- Missing: Blank-reference inputs (dwarf-galaxy distances, LMC H2/13CO, abundance gradient papers) must be recovered
- Missing: Per-cloud 12CO inputs for Tex and exact cloud selection lists
- Missing: No analysis scripts for the half-peak-isophote measurement pipeline
- Data volume (inferred): ALMA TP 26 fields: small (<~10 GB); archival SMC and NGC 6822 interferometry: tens of GB raw; reduced cubes on figshare are far smaller
- Score (inferred): 3/5, Public ALMA and figshare data and a fairly complete equation-level recipe with numeric results, but several inputs are blank-cited and imaging details for the ALMA parts are missing.
- Rediscovery candidate: yes, ALMA TP and archival data are public, the virial-parameter recipe is given in equations, and the main results (alpha_vir versus Z, fit coefficients) are numeric, though some ancillary inputs are not recoverable from the text.

## Links

- Method: Reid et al. 2019 (cite: 2019ApJ...885..131R) (BeSSeL rotation curve and Bayesian distance code)
- Method: Wong et al. 2019 (cite: 2019ApJ...885...50W) (LMC 13CO cubes)
- Method: Jameson et al. 2018 (cite: 2018ApJ...853..111J) (SMC ALMA data)
- Companion: Heyer et al. 2009 (cite: 2009ApJ...699.1092H) (GRS inner-Galaxy 13CO cloud sample and alpha_vir comparison)
- Companion: Shi et al. 2020 (cite: 2020ApJ...892..147S) (DDO 70 clump properties)
- Related: Galactic Ring Survey (GRS)
- Related: BeSSeL survey

## Checks

```json
{
 "quotes": 153,
 "quotes_ok": 153,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 131,
  "stated": 101,
  "rate": 0.771
 },
 "evidence_ok": true
}
```
