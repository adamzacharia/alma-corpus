# ALMA-IMF: XVI. Mass-averaged temperature of cores and protostellar luminosities in the ALMA-IMF protoclusters

`2025A&A...694A..24M` | Astronomy and Astrophysics 2025 | first author: Motte, F. | arXiv: 2412.02011 | DOI: 10.1051/0004-6361/202451931

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type large_program_or_survey

## Science

- Fields: star_formation, milky_way_ism, astrochemistry
- Question: How to estimate the mass-averaged dust temperature of ALMA-IMF cores (and hence their masses) and the luminosity of individual high-mass protostars, given SED images at 2.5 arcsec resolution  
  > "The present study proposes a methodology for estimating the mass-averaged temperature of cores detected with ALMA as well as the luminosity of individual high-mass protostars." (Introduction)
- Target **ALMA-IMF protoclusters (14 of 15 studied)**: coordinates _not stated_; z/distance 2.0-5.4 kpc (see individual entries)  
  > "The ALMA-IMF program surveyed 15 massive ($2.5-33 \times 10^3~\mbox{$M_\odot$}$) relatively nearby ($2-5.5$ kpc) protoclusters" (Introduction); "The G351.77 protocluster is excluded from the present study because the quality of its CO(2-1) datacube precluded investigating outflows in this region" (Footnotes); distance from (cite: motte2022)  
  > "The ALMA-IMF program surveyed 15 massive ($2.5-33 \times 10^3~\mbox{$M_\odot$}$) relatively nearby ($2-5.5$ kpc) protoclusters" (Introduction); "The G351.77 protocluster is excluded from the present study because the quality of its CO(2-1) datacube precluded investigating outflows in this region" (Footnotes)
- Target **W43-MM1, W43-MM2, W43-MM3 (case-study protoclusters)**: coordinates _not stated_; z/distance 5.5 kpc  
  > "the distance of the ALMA-IMF protoclusters to the Sun, 5.5 kpc for the W43 regions, 2.4 kpc for G012.80, and 2.0-5.4 kpc for the others (cite: motte2022)" (4.2 Outside-in estimate using PPMAP dust temperatures); distance from (cite: motte2022)  
  > "the distance of the ALMA-IMF protoclusters to the Sun, 5.5 kpc for the W43 regions, 2.4 kpc for G012.80, and 2.0-5.4 kpc for the others (cite: motte2022)" (4.2 Outside-in estimate using PPMAP dust temperatures)
- Target **G012.80 (case-study protocluster)**: coordinates _not stated_; z/distance 2.4 kpc  
  > "the distance of the ALMA-IMF protoclusters to the Sun, 5.5 kpc for the W43 regions, 2.4 kpc for G012.80, and 2.0-5.4 kpc for the others (cite: motte2022)" (4.2 Outside-in estimate using PPMAP dust temperatures); distance from (cite: motte2022)  
  > "the distance of the ALMA-IMF protoclusters to the Sun, 5.5 kpc for the W43 regions, 2.4 kpc for G012.80, and 2.0-5.4 kpc for the others (cite: motte2022)" (4.2 Outside-in estimate using PPMAP dust temperatures)

## Data provenance

- ALMA projects: 2017.1.01355.L, 2013.1.01365.S, 2015.1.01273.S
- bands: 1.3 mm and 3 mm continuum images (core extraction); 1.3 mm used for core fluxes  
  > "identified and characterized cores in the 1.3 mm and 3 mm images" (2.1 ALMA-IMF prestellar and protostellar cores)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: matched ~2000 au across the sample, 0.3 to 0.9 arcsec depending on distance  
  > "was imaged at 1.3 mm with a matched spatial resolution of $\sim$2000 au across the sample, corresponding to $0.3\ensuremath{''}$ to $0.9\ensuremath{''}$, depending on the distance of the protoclusters" (Introduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: ALMA-IMF Large Program, PIs Motte, Ginsburg, Louvet, Sanhueza  
  > "(PIs: Motte, Ginsburg, Louvet, Sanhueza)" (Footnote 1)
- Line: CO and SiO CO(2-1) and SiO(5-4) (not stated)
- Line: CH3OCHO (methyl formate) doublet line (hot-core tracer, from Paper XI) (216.1 GHz)
- Other facility **Herschel**: 70 to 500 micron images used with ALMA in the PPMAP SED fits (via Paper XII)  
  > "with $5.6\ensuremath{''}-35\ensuremath{''}$ resolution images of *Herschel* at $70\,\mu{\rm m}$ to $500\,\mu{\rm m}$ (cite: nguyen2013)" (Introduction)
- Other facility **Spitzer**: mid-infrared (3.6 to 24 micron) warm-component constraint in the PPMAP luminosity SEDs; lacks resolution to split luminosity among cores  
  > "While ALMA provides a good estimate of the relative intensities of protostellar cores in the (sub)millimeter regime, *Herschel* and *Spitzer* observatories lack the angular resolution to do so" (4.3 Inside-out estimate using PPMAP peak luminosities)
- Other facility **APEX**: 350 and 870 micron images used in earlier PPMAP runs (pilot study) and in Paper XII  
  > "also used in the *PPMAP* procedure $350\,\mu{\rm m}$ and $870\,\mu{\rm m}$ images obtained at the APEX telescope, as done in (cite: dellova2024)" (Footnote 2)
- Other facility **NOEMA**: 3 mm images used in the pilot-study PPMAP run  
  > "and 3 mm images from the NOEMA interferometer (cite: louvet2014)" (Footnote 2)
- External data: Homogeneous getsf core catalog for the 15 ALMA-IMF protoclusters (cleanest images)  
  > "We used the homogeneous sample of sources obtained by (cite: louvet2024) for each of the 15 ALMA-IMF protoclusters" (2.1 ALMA-IMF prestellar and protostellar cores) [from (cite: louvet2024)]
- External data: More complete core catalogs for W43-MM1, W43-MM2, W43-MM3 and G012.80 (cleanest plus bsens, MnGSeg-denoised for W43)  
  > "replaced it for the W43-MM1, W43-MM2, W43-MM3, and G012.80 protoclusters by the more complete catalogs of (cite: pouteau2022), (cite: nony2023), and (cite: armante2024)" (2.1 ALMA-IMF prestellar and protostellar cores) [from (cite: pouteau2022); (cite: nony2023); (cite: armante2024)]
- External data: Outflow and hot-core associations used to label cores prestellar or protostellar  
  > "and their association with outflows (cite: nony2020; nony2023; armante2024; valeille2024) and hot cores (cite: brouillet2022; bonfand2024)" (Catalogs of cores and luminosity peaks) [from (cite: nony2020; nony2023; armante2024; valeille2024; brouillet2022; bonfand2024)]
- External data: Classification result: 266 protostellar cores, 617 prestellar core candidates, 81 sources excluded  
  > "In total, the ALMA-IMF survey has identified 266 protostellar cores, 617 prestellar core candidates, and 81 sources associated with neither outflows nor hot cores" (2.1 ALMA-IMF prestellar and protostellar cores) [from Nony et al. in prep.; (cite: nony2023; armante2024; valeille2024; bonfand2024)]
- External data: PPMAP dust temperature images (original and 70 micron opacity-corrected) at 2.5 arcsec for all 15 protoclusters; also column density and luminosity images  
  > "The ALMA-IMF database includes dust temperature images for all 15 protoclusters, at an angular resolution of $2.5\ensuremath{''}$ (cite: dellova2024)." (3.1 Background-diluted dust temperature of cores) [from (cite: dellova2024) (Paper XII)]
- External data: Luminosity peak catalog (getsf on PPMAP luminosity images), used directly for Young and Intermediate protoclusters  
  > "This study also uses luminosity peak catalogs, provided by Paper XII (cite: dellova2024)" (Catalogs of cores and luminosity peaks) [from (cite: dellova2024) (Paper XII)]
- External data: 1.3 mm images corrected for free-free emission, used to build luminosity images for Evolved protoclusters  
  > "built using the 1.3 mm images corrected from free-free emission (cite: diazgonzalez2023; galvanmadrid2024)" (2.2 Luminosity peaks in ALMA-IMF protoclusters) [from (cite: diazgonzalez2023; galvanmadrid2024)]
- External data: Hot-core (methyl formate) source catalog and its COM-based temperatures (100+/-50 K, 300+/-100 K for eight cores)  
  > "(cite: bonfand2024) set a dust temperature of $\mbox{$T_{\rm dust}$}= 100\pm50$ K for the ALMA-IMF protostellar cores associated with candidate hot cores." (6.3.2 COM temperatures of the ALMA-IMF survey) [from (cite: bonfand2024) (Paper XI)]
- External data: Protostellar envelope temperature law normalisation T0 = 25 K, r0 = 6685 au, L0 = 520 Lsun  
  > "$T_0=25$ K, $r_0=6685$ au, and $L_0=520~\mbox{$L_\odot$}$, taken from the model of (cite: terebey1993)" (4.1 Analytical description of dust temperature within protostellar cores) [from (cite: terebey1993)]
- External data: Density index p = 2 +/- 0.3 and emissivity index beta = 1.5 +/- 0.3 for protostellar envelopes  
  > "the best suited power-law indices for their density and dust opacity laws are $p=2\pm 0.3$ ((cite: motte2001; beuther2002; gieser2021)" (4.1 Analytical description of dust temperature within protostellar cores); "and $\beta=1.5\pm 0.3$ (cite: andre1993; rathborne2010; juvela2015; palau2021), respectively." (4.1 Analytical description of dust temperature within protostellar cores) [from (cite: motte2001; beuther2002; gieser2021; andre1993; rathborne2010; juvela2015; palau2021)]
- External data: Prestellar core outer temperature slope -q = 0.1-0.32, median 0.2, from published observed and modeled cores  
  > "of $\mbox{$T_{\rm dust}$}(r) \propto r^{-q}$ with $-q=0.1-0.32$ with a median value of $-q\simeq0.2$ (cite: goncalves2004; crapsi2007; nielbock2012; launhardt2013; marsh2014; juarez2017)" (5.2 Outside-in estimate for prestellar cores using PPMAP dust temperatures) [from (cite: goncalves2004; crapsi2007; nielbock2012; launhardt2013; marsh2014; juarez2017)]
- External data: Luminosity-to-mass ratio L/M of each protocluster  
  > "the luminosity-to-mass ratio, $L/M$, of the ALMA-IMF protoclusters is taken from (cite: dellova2024)" (6.1 Adopted core temperatures) [from (cite: dellova2024)]
- External data: Comparison sample of protostellar cores in nearby clouds in the M-L diagram  
  > "We present the result of surveys for protostellar cores in nearby clouds (cite: bontemps1996; bontemps2010SI; motte2001)" (6.4 Protostellar evolution in massive protoclusters) [from (cite: bontemps1996; bontemps2010SI; motte2001)]
- External data: Comparison samples: Cygnus X IR-quiet protostellar cores and massive clumps hosting UCH II regions  
  > "in the Cygnus X star-forming complex (cite: duarte2013) and a dozen of massive clumps hosting UCH ii regions (cite: vandertak2000)" (6.4 Protostellar evolution in massive protoclusters) [from (cite: duarte2013; vandertak2000)]
- Simulation/model as data: Accretion models and evolutionary tracks of Duarte-Cabral et al. (decreasing, intermittent accretion) overplotted in the M-L diagram  
  > "(cite: duarte2013) proposed several parametrized models, adapted from (cite: bontemps1996) and (cite: andre2000), with constant and decreasing accretion rates, and with continuous or intermittent accretion." (6.4 Protostellar evolution in massive protoclusters)
- Simulation/model as data: Grids of radiative transfer protostar models (Robitaille 2017) used to check the mean-temperature relation to ~20%  
  > "is found, with variations of $\sim$20%, in grids of radiative transfer models describing protostars with a protostellar envelope and an outflow cavity (cite: robitaille2017)" (4.1 Analytical description of dust temperature within protostellar cores)

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
- continuum subtraction: cleanest continuum images (free of line emission) used by Louvet+24; cleanest plus bsens images for W43 and G012.80 catalogs  
  > "used the `cleanest` images, which are computed to be free of contamination by line emission" (2.1 ALMA-IMF prestellar and protostellar cores); "complemented the `cleanest` continuum images with the most sensitive, `bsens`, continuum images of ALMA-IMF (cite: ginsburg2022)" (2.1 ALMA-IMF prestellar and protostellar cores)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Core extraction (getsf) and catalogs of 1.3 mm integrated and peak fluxes, sizes and beams  
  > "We used the homogeneous sample of sources obtained by (cite: louvet2024) for each of the 15 ALMA-IMF protoclusters" (2.1 ALMA-IMF prestellar and protostellar cores) [from (cite: louvet2024); (cite: pouteau2022); (cite: nony2023); (cite: armante2024)]
- First-order free-free correction of 1.3 mm fluxes for some cores  
  > "performed a first-order correction of the 1.3 mm flux of some of these sources" (2.1 ALMA-IMF prestellar and protostellar cores) [from (cite: pouteau2023); (cite: armante2024); (cite: bonfand2024)]
- Core fluxes corrected for line contamination  
  > "Integrated and peak fluxes of cores are corrected for line contamination over the entire ALMA-IMF sample (cite: pouteau2022; nony2023; louvet2024)." (6.2 Resulting core mass) [from (cite: pouteau2022; nony2023; louvet2024)]
- PPMAP dust opacity law kappa proportional to nu^beta with beta = 1.8  
  > "using a dust opacity law of $\kappa_\nu \propto \nu^{\beta}$ with $\beta=1.8$ (cite: planck2011; koehler2015)" (3.1 Background-diluted dust temperature of cores) [from (cite: planck2011; koehler2015); PPMAP by (cite: marsh2015; marsh2017) as run in (cite: dellova2024)]
- 70 micron opacity correction of the PPMAP temperature images, using the column density image and a grid of temperature corrections  
  > "(cite: dellova2024) corrected the dust temperature images for the $70\,\mu{\rm m}$ opacity, using the column density image computed by *PPMAP* and a grid of temperature corrections." (3.1 Background-diluted dust temperature of cores) [from (cite: dellova2024); grid from (cite: motte2018b), (cite: marsh2014)]
- Optically-thick-corrected core mass equation (optical thickness at most close to one)  
  > "We therefore used the equation proposed by (cite: pouteau2022) (cite: motte2018b) to compute the mass of all the 883 ALMA-IMF cores, assuming an optical thickness that at most is close to one" (6.2 Resulting core mass) [from (cite: pouteau2022); (cite: motte2018b)]
- Evolutionary classification of protoclusters as Young, Intermediate, Evolved  
  > "three evolutionary stages: Young, Intermediate, and Evolved (cite: motte2022)" (Introduction) [from (cite: motte2022)]
- Median deconvolved core FWHM sizes used as outer radius R_out  
  > "took their median deconvolved FWHM sizes (cite: motte2022) as a proxy for their outer radius" (4.1 Analytical description of dust temperature within protostellar cores) [from (cite: motte2022)]
- Luminosity peak extraction method (getsf on PPMAP luminosity images) followed for Evolved protoclusters  
  > "Following (cite: dellova2024), we used the *getsf* algorithm version 230712 (cite: men2021getsf)" (2.2 Luminosity peaks in ALMA-IMF protoclusters) [from (cite: dellova2024); (cite: men2021getsf)]

### Not stated but needed to reproduce (our reading)

- The PPMAP temperature, column density and luminosity images themselves (Paper XII) and the PPMAP run setup (temperature and beta grids, priors, beam and weighting of 70 micron to 1.3 mm inputs).
- The getsf detection and extraction parameters (thresholds, scale ranges) for the new luminosity-peak extraction in the four Evolved protoclusters; only the version (230712) and the 1-2 beam size range are given.
- How the Gaussian-smoothed combined temperature image is built numerically (Gaussian width choice and the radius-averaging implementation for the 1.25 arcsec mean).
- Fitting procedure for the power-law plus Gaussian luminosity profiles (algorithm, weights, fit radius range, uncertainty estimation) and the integration limits for L_MF(pow) and L_MF(tot).
- Parameters passed to skimage peak_local_max (min distance, threshold) for temperature peaks.
- Per-core 1.3 mm integrated and peak fluxes, deconvolved FWHM sizes, beams and free-free corrections (inside the companion catalogs, not in this paper).
- The prestellar/protostellar flags that rest on Nony et al. (in prep.), not yet published.
- Per-protocluster distances beyond W43 (5.5 kpc) and G012.80 (2.4 kpc) are only given as a range 2.0-5.4 kpc.
- How the individual-core temperature uncertainties are propagated into mass uncertainties.

## Analysis recipe

1. **Assemble core catalogs and classify cores**: Adopt published getsf core catalogs (Louvet+24 for all fields; Pouteau+22, Nony+23, Armante+24 for W43-MM1/MM2/MM3 and G012.80) and label each core luminous protostellar, low-luminosity protostellar or prestellar from outflow, hot-core and luminosity-peak associations  
  > "We used the homogeneous sample of sources obtained by (cite: louvet2024) for each of the 15 ALMA-IMF protoclusters" (2.1 ALMA-IMF prestellar and protostellar cores); "prestellar cores: cores neither associated with a detected outflow nor with a hot core" (Catalogs of cores and luminosity peaks)
   - software: getsf
   - parameter: 266 protostellar cores and 617 prestellar candidates retained (883 cores)  
  > "In total, the ALMA-IMF survey has identified 266 protostellar cores, 617 prestellar core candidates, and 81 sources associated with neither outflows nor hot cores" (2.1 ALMA-IMF prestellar and protostellar cores)
   - assumption: Sources of unassured nature (no outflow, no hot core, possible free-free contamination) are excluded rather than assumed prestellar  
  > "As long as the prestellar nature of the last group is not assured, we exclude these ALMA-IMF sources from the present study." (2.1 ALMA-IMF prestellar and protostellar cores)
   - fitting: _not stated_
   - validation: _not stated_
2. **Obtain luminosity peaks and associate them with protostellar cores**: Take luminosity peaks from Paper XII for Young and Intermediate protoclusters; re-extract with getsf on luminosity images built from free-free-corrected 1.3 mm images for the four Evolved protoclusters; a core is associated when its centre lies inside the peak FWHM ellipse  
  > "we directly extracted luminosity peaks from the catalog of (cite: dellova2024)" (2.2 Luminosity peaks in ALMA-IMF protoclusters); "lies within the ellipse describing the FWHM of the luminosity peaks" (2.2 Luminosity peaks in ALMA-IMF protoclusters)
   - software: getsf
   - parameter: getsf version 230712; peak sizes one to two times the 2.5 arcsec beam of the luminosity images  
  > "we used the *getsf* algorithm version 230712 (cite: men2021getsf) to extract luminosity peaks with sizes ranging from one to two times the $2.5\ensuremath{''}$ beam of luminosity images" (2.2 Luminosity peaks in ALMA-IMF protoclusters)
   - assumption: Prestellar cores inside luminosity peaks contribute negligibly to the peak luminosity  
  > "should only account for a negligible part of the measured luminosity" (2.2 Luminosity peaks in ALMA-IMF protoclusters)
   - fitting: _not stated_
   - validation: The new extraction recovers the same protostellar-core peaks as the Paper XII extraction (90% overlap)  
  > "the same 111 luminosity peaks associated with protostellar cores ($90\%$ overlap)" (2.2 Luminosity peaks in ALMA-IMF protoclusters)
3. **Measure background-diluted dust temperature at core positions**: Use the opacity-corrected PPMAP temperature image, except at prestellar cores and low-luminosity protostars where the average of the original and corrected images is taken at the core centre and smoothed by Gaussians of the 1.3 mm resolution; read the temperature averaged over a 1.25 arcsec radius  
  > "we used the average between the original and the opacity-corrected images, as measured at the central position of the cores and smoothed by Gaussians representing the resolution elements of the 1.3 mm images." (3.1 Background-diluted dust temperature of cores)
   - software: PPMAP, skimage peak_local_max
   - parameter: PPMAP uncertainty ~16% added in quadrature with the opacity-correction spread  
  > "the quadratic sum of the uncertainty associated with the *PPMAP* fitting procedure ($\sigma_{\rm PPMAP}\sim 16\%$)" (3.1 Background-diluted dust temperature of cores)
   - parameter: Temperature peaks located with skimage peak_local_max  
  > "python function to identify dust temperature peaks" (3.2 Variations of the dust temperature and hot spots)
   - assumption: Column-density-weighted PPMAP temperature approximates the mass-averaged temperature of dense structures, neglecting line-of-sight effects  
  > "Neglecting line-of-sight effects (cite: malinen2011), these maps provide a good approximation of the mass-averaged dust temperature for the densest cloud structures observed at $2.5\ensuremath{''}$ in the ALMA-IMF fields." (3.1 Background-diluted dust temperature of cores)
   - fitting: PPMAP Bayesian SED fit (done in Paper XII, setup not restated)  
  > "was used to fit modified blackbody models to the fluxes measured in the $70\,\mu{\rm m}$ to 1.3 mm wavelength range" (3.1 Background-diluted dust temperature of cores)
   - validation: Consistency between luminosity and temperature images supports the combined temperature images  
  > "The consistency between luminosity and temperature images supports the use of the combined dust temperature images." (Background-diluted dust temperature of cores in the ALMA-IMF protoclusters)
4. **Measure luminosity of the extreme hot-core protostars from radial profiles**: Build median pixel luminosity profiles in annular rings around four positions and fit a power-law plus a Gaussian; integrate the power-law for L_MF(pow) (adopted) and the whole profile for L_MF(tot) (upper limit)  
  > "Here, we model the pixel luminosity profiles by the sum of a power-law and a Gaussian, both centered at angular radius $\theta=0$." (2.3 Highest-luminosity protostars in ALMA-IMF protoclusters); "which is made up of the median luminosity of pixels contained within annular rings, taking their medians in order to attenuate the effect of nearby luminosity peaks on the profile." (2.3 Highest-luminosity protostars in ALMA-IMF protoclusters)
   - parameter: L_MF(pow) adopted as best estimate of protostellar luminosity  
  > "we use $L_{\rm MF}({\rm pow})$ to compute the contribution of each protostar and use it as the best estimate of protostellar luminosities" (2.3 Highest-luminosity protostars in ALMA-IMF protoclusters)
   - assumption: Power-law component = cold envelope emission with rho proportional to r^-2 and T proportional to r^-0.36, giving expected index m of about 1.36  
  > "It follows that the cold component of a protostellar core, with $\rho(r)\propto r^{-2}$ and $\mbox{$T_{\rm dust}$}(r)\propto r^{-0.36}$ profiles" (2.3 Highest-luminosity protostars in ALMA-IMF protoclusters)
   - fitting: Power-law plus Gaussian profile fit; algorithm, weights and priors not stated  
  > "Here, we model the pixel luminosity profiles by the sum of a power-law and a Gaussian, both centered at angular radius $\theta=0$." (2.3 Highest-luminosity protostars in ALMA-IMF protoclusters)
   - validation: Fitted indices are close to the theoretical 1.36  
  > "close to the theoretical value of $m\simeq 1.36$" (2.3 Highest-luminosity protostars in ALMA-IMF protoclusters)
5. **Outside-in mass-averaged temperature of protostellar cores**: Extrapolate the PPMAP temperature averaged over 1.25 arcsec radius down to the core outer radius (deconvolved FWHM) with T proportional to r^-0.36  
  > "to extrapolate the *PPMAP* temperature averaged over a $1.25\ensuremath{''}\times d \in[2500; 7000]$ au radius to the core outer radius" (4.2 Outside-in estimate using PPMAP dust temperatures)
   - parameter: q ~ 0.36 from beta = 1.5  
  > "The emissivity index chosen above yields a power-law index for the temperature profile of $q\simeq 0.36$" (4.1 Analytical description of dust temperature within protostellar cores)
   - parameter: Density index p = 2 +/- 0.3 and beta = 1.5 +/- 0.3  
  > "the best suited power-law indices for their density and dust opacity laws are $p=2\pm 0.3$ ((cite: motte2001; beuther2002; gieser2021)" (4.1 Analytical description of dust temperature within protostellar cores)
   - assumption: Centrally heated, optically thin envelope with power-law temperature profile; result is an upper limit if optically thick, no heating hot spot, or flatter density  
  > "When a protostellar envelope is centrally heated and is optically thin to far-infrared radiation, the temperature inside the envelope follows a power-law as a function of radius" (4.1 Analytical description of dust temperature within protostellar cores)
   - fitting: _not stated_
   - validation: The mean-temperature relation matches radiative transfer model grids to ~20%  
  > "is found, with variations of $\sim$20%, in grids of radiative transfer models describing protostars with a protostellar envelope and an outflow cavity (cite: robitaille2017)" (4.1 Analytical description of dust temperature within protostellar cores)
6. **Distribute luminosity to cores and derive inside-out temperature**: Weight each protostellar core by the luminosity-peak Gaussian evaluated at its position, assign L_i = w_i x (L_bol minus L_bck, with L_bck = 0), then insert L_i into the mean-temperature relation T(L, R_out)  
  > "as the value of the luminosity peak’s Gaussian function at the location of the core" (4.3 Inside-out estimate using PPMAP peak luminosities); "for each luminous protostellar core, thus associated with a luminosity peak, we plugged its protostellar luminosity" (4.3 Inside-out estimate using PPMAP peak luminosities)
   - parameter: Normalisation T0 = 25 K, r0 = 6685 au, L0 = 520 Lsun (Terebey) rescaled to 2100 au and 1100 Lsun  
  > "$T_0=25$ K, $r_0=6685$ au, and $L_0=520~\mbox{$L_\odot$}$, taken from the model of (cite: terebey1993)" (4.1 Analytical description of dust temperature within protostellar cores); "our only constraint at this stage is the median luminosity of protostellar groups: $\sim$$1100~\mbox{$L_\odot$}$ (cite: dellova2024)" (4.1 Analytical description of dust temperature within protostellar cores)
   - assumption: Background luminosity of cores inside a peak set to zero; main bias is chance alignment of cores along the line of sight  
  > "As we have no information whatsoever on the value of this background (at scale between $2.5\ensuremath{''}$ and the core size), we are forced to set it here to zero." (4.3 Inside-out estimate using PPMAP peak luminosities)
   - fitting: _not stated_
   - validation: The two temperature estimates are correlated, differing by 36% on average with 15% dispersion  
  > "their fractional difference is on average $36\%$, with a $1\sigma$ dispersion of about $15\%$" (6.1 Adopted core temperatures)
7. **Mass-averaged temperature of prestellar cores**: Extrapolate the 1.25 arcsec-averaged PPMAP temperature to the core outer radius with T proportional to r^0.2 (rho proportional to r^-2); read directly from the image when core FWHM exceeds the PPMAP beam  
  > "to estimate the mean dust temperature of the ALMA-IMF prestellar cores or directly measured it in the *PPMAP* images when the core FWHM is larger than the *PPMAP* beam" (5.2 Outside-in estimate for prestellar cores using PPMAP dust temperatures)
   - parameter: Temperature index 0.2 set from published prestellar cores and IRDCs  
  > "we therefore assumed the temperature distribution of the background of ALMA-IMF prestellar cores to be following a $\mbox{$T_{\rm dust}$}(r)\propto r^{0.2}$ power-law in the range of radii considered for the extrapolation" (5.2 Outside-in estimate for prestellar cores using PPMAP dust temperatures)
   - assumption: Core background follows rho proportional to r^-2  
  > "We also assume that the core background follows the same density profile as the outer parts of prestellar cores, IRDCs or filaments: $\rho(r) \propto r^{-2}$." (5.2 Outside-in estimate for prestellar cores using PPMAP dust temperatures)
   - fitting: _not stated_
   - validation: Sensitivity only: +/-0.1 in index changes temperature by +/-1 to +/-2 K  
  > "the resulting mass-averaged temperature of prestellar cores could vary by $\pm1$ K in the closest ALMA-IMF protoclusters, and by $\pm2$ K in the furthest protoclusters" (5.2 Outside-in estimate for prestellar cores using PPMAP dust temperatures)
8. **Adopt final temperatures and compute core masses**: Average the two temperature estimates for luminous protostars (uncertainty spans both); compute masses of all 883 cores with the optically-thick-corrected mass equation using 1.3 mm integrated and peak fluxes  
  > "We therefore simply averaged them and list their mean value in Tables" (6.1 Adopted core temperatures); "We therefore used the equation proposed by (cite: pouteau2022) (cite: motte2018b) to compute the mass of all the 883 ALMA-IMF cores, assuming an optical thickness that at most is close to one" (6.2 Resulting core mass)
   - parameter: Dust plus gas mass opacity kappa_1.3mm = 0.01 cm2 g-1  
  > "where the dust $+$ gas mass opacity is set to $\kappa_{\rm 1.3mm} = \rm 0.01~cm^2\,g^{-1}$" (6.2 Resulting core mass)
   - assumption: Optical thickness measured at peak flux applied to the total flux (small overestimate for the few thick cores)  
  > "The core optical thickness, measured for their peak flux, is applied to their total flux." (6.2 Resulting core mass)
   - fitting: _not stated_
   - validation: Temperatures agree with the pilot ALMA-IMF paper to within 40% and with Paper VI / Paper X to within 30%  
  > "on average, the dust temperature of (cite: motte2018b) is consistent with those of the present study to within $40\%$ and those of (cite: pouteau2022) and (cite: armante2024) to within $30\%$." (6.3.1 Dust temperatures in previous ALMA-IMF papers)
9. **Build the mass-luminosity diagram and compare with accretion models**: Place the 151 luminous protostellar cores in the M_core versus L_proto diagram, compare with nearby, Cygnus X and UCH II samples and with the Duarte-Cabral accretion tracks  
  > "presents the $M_{\rm core}-L_{\rm proto\star}$ diagram for the 151 luminous protostellar cores" (6.4 Protostellar evolution in massive protoclusters)
   - parameter: T = 22 000 K line separates ALMA-IMF cores from UCH II regions  
  > "separated by the $T=22\,000$ K line" (6.4 Protostellar evolution in massive protoclusters)
   - assumption: Cygnus X core masses are scaled down by a factor of two to match the 2000 au ALMA-IMF core size  
  > "Dividing the core mass of Cygnus X protostars by this factor of two, would provide a better match" (6.4 Protostellar evolution in massive protoclusters)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **getsf** 230712 (for the new luminosity-peak extraction): Core and luminosity-peak extraction  
  > "we used the *getsf* algorithm version 230712 (cite: men2021getsf) to extract luminosity peaks" (2.2 Luminosity peaks in ALMA-IMF protoclusters)
- **PPMAP** : Bayesian SED fitting giving dust temperature, column density and luminosity images at 2.5 arcsec  
  > "The *PPMAP* procedure (cite: marsh2015; marsh2017) was used to fit modified blackbody models to the fluxes measured in the $70\,\mu{\rm m}$ to 1.3 mm wavelength range" (3.1 Background-diluted dust temperature of cores)
- **skimage peak_local_max** : Identifying dust temperature peaks  
  > "python function to identify dust temperature peaks" (3.2 Variations of the dust temperature and hot spots)
- **Multi-resolution non-Gaussian Segmentation software** : Noise reduction in the W43 images used for the companion core catalogs  
  > "the surveys of the W43 protoclusters used images whose noise has been reduced using the Multi-resolution non-Gaussian Segmentation software (cite: robitaille2019)" (2.1 ALMA-IMF prestellar and protostellar cores)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Cores with dust temperature estimates (prestellar / protostellar) | 883 (617 prestellar, 266 protostellar) | not stated | cores | 1 | For the first time, we provide data-informed estimates of dust temperatures for 883 cores identified with ALMA-IMF: 17–31 K and 28–79 K (5th and 95th percentiles, up to 127 K) for the 617 prestellar and 266 protostellar cores, respectively. |
| Luminosity peaks hosting protostellar cores | 111 of 255 | not stated | peaks | 2 | In total, 111 out of the 255 luminosity peaks host protostellar cores |
| Temperature peaks coinciding with a luminosity peak and protostellar cores | 83 | not stated | peaks | 3 | we identified in the entire ALMA-IMF survey, 83 temperature peaks, which coincide with a luminosity peak and at least one, and up to four, protostellar cores |
| Background-diluted PPMAP core temperature range | 17 to 73 | not stated | K | 3 | which range from 17 K to 73 K |
| PPMAP fitting uncertainty on background-diluted temperature | ~16 | not stated | % | 3 | the quadratic sum of the uncertainty associated with the *PPMAP* fitting procedure ($\sigma_{\rm PPMAP}\sim 16\%$) |
| Power-law index of luminosity profiles of extreme hot cores | 1.2 to 1.9 | not stated | dimensionless | 4 | the best-fit power-laws have indices ranging from $1.2$ to $1.9$ |
| Hot-core luminosity L_MF(pow) | 9e3 to 2e5 | not stated | Lsun | 4 | We measured hot core luminosities ranging from $L_{\rm MF}({\rm pow})=9\times 10^3~\mbox{$L_\odot$}$ to $2\times 10^5~\mbox{$L_\odot$}$ |
| Outside-in mass-averaged dust temperature of protostellar cores | ~17 to ~127 | not stated | K | 5 | The dust temperature of protostellar cores is observed to vary from $\sim$17 K to $\sim$127 K. |
| Inside-out mass-averaged dust temperature of luminous protostellar cores | ~30 to ~143 | not stated | K | 6 | provides values that range from $\sim$30 K to $\sim$143 K and are generally 20 K higher than the outside-in measurements |
| Protostellar cores with an individual luminosity estimate | 151 (55% of protostellar cores) | not stated | cores | 6 | list, for 151 (i.e., $55\%$) ALMA-IMF protostars, an estimate of their protostellar luminosity |
| Protostellar luminosity of luminous protostellar cores (5th to 95th percentile) | 50 to 1.5e4 (up to 8e4) | not stated | Lsun | 6 | and they range from $50~\mbox{$L_\odot$}$ to $1.5\times 10^4~\mbox{$L_\odot$}$ (5th and 95th percentiles, up to $8\times 10^4~\mbox{$L_\odot$}$) |
| Mass-averaged temperature of eight extreme hot-core protostars from L_MF(pow) | 80 to 140 (upper values 100 to 170) | not stated | K | 6 | gives a mass-averaged dust temperature of $80-140$ K, with an upper value of $100-170$ K |
| Prestellar core mass-averaged temperature (5th to 95th percentile, median) | 17 to 31, median 22 | not stated | K | 7 | and range from 17 K to 31 K (5th and 95th percentiles), with a median value of 22 K |
| Median temperature of prestellar cores inside versus outside luminosity peaks | ~24 versus ~22 | not stated | K | 7 | $\sim$24 K versus $\sim$22 K median values |
| Mean temperature of luminous protostellar cores (average of two estimates; 5th to 95th percentile, median) | 38 to 92 (up to 127), median 54 | not stated | K | 8 | Their average gives, for the 151 luminous protostellar cores, temperatures that range from 38 K to 92 K (5th and 95th percentiles) and go up to 127 K, with a median value of 54 K |
| Temperature of low-luminosity protostellar cores (115 cores; 5th to 95th percentile, median) | 26 to 51, median 37 | not stated | K | 8 | and they range from 26 K to 51 K (5th and 95th percentiles), with a median value of 37 K |
| Fractional difference between inside-out and outside-in temperatures | 36 (mean), dispersion 15 | 1 sigma dispersion ~15% | % | 8 | their fractional difference is on average $36\%$, with a $1\sigma$ dispersion of about $15\%$ |
| Mean offset of inside-out over outside-in temperature | ~19 | not stated | K | 8 | the dust temperature estimated from the protostellar luminosity is on average $\sim$19 K higher than the dust temperature estimated from the extrapolation of the background-diluted core temperature |
| Core masses | ~0.1 to ~260 | relative uncertainties 20%, up to ~40% | Msun | 8 | The resulting core masses range from $\sim$0.1$~\mbox{$M_\odot$}$ to $\sim$260$~\mbox{$M_\odot$}$; This leads to relative uncertainties of $20\%$, up to $\sim$$40\%$, for the masses of the entire ALMA-IMF core sample. |
| Fraction of cores with optically thin 1.3 mm emission | ~96 | not stated | % | 8 | For the vast majority, $\sim$$96\%$, of the ALMA-IMF cores, their 1.3 mm emission remains optically thin |
| Median core temperature by protocluster stage (Young, Intermediate, Evolved) | ~22, ~26, ~29 | not stated | K | 8 | the median core temperature increases between these 3 groups: from $\sim$22 K (with G327.29 as the obvious outlier) to $\sim$26 K and finally $\sim$29 K |
| Ratio of COM-line-based to dust-based core temperatures | 1.7 (average) | not stated | dimensionless | 0 | on average $1.7$ times higher than the dust-based estimates of Sect. |

## Qualitative findings

- Previous lower-resolution SED-based dust temperatures validate the method  
  > "Dust temperatures previously estimated from SED-based analyses at a comparatively lower resolution validate our method." (abstract)
- Dust-based hot-core temperatures are systematically lower than those from complex organic molecules  
  > "For hot cores, on the other hand, we estimated systematically lower temperatures than studies based on complex organic molecules." (abstract)
- Protostars appear to accrete from a larger mass reservoir than their host cores  
  > "The ALMA-IMF data favor a scenario in which protostars accrete their mass from a larger mass reservoir than their host cores." (abstract)
- No obvious correlation between protocluster L/M and core temperatures  
  > "displays no obvious correlation between the $L/M$ ratio of ALMA-IMF protoclusters and the median, minimum, and maximum values of its core temperatures" (6.1 Adopted core temperatures)
- G328.25 hosts the coldest and G327.29 the hottest cores  
  > "G328.25 and G327.29 host, on average, the coldest and hottest cores of the ALMA-IMF protoclusters" (6.1 Adopted core temperatures)
- Most temperature peaks are PDR structures rather than protostellar heating  
  > "The large majority, $70\%$, of these hot gas pockets are low-density structures of PDRs" (3.2 Variations of the dust temperature and hot spots)

## Claim tuples

- H: Mass-averaged core temperatures and protostellar luminosities can be derived at core scale by extrapolating 2.5 arcsec PPMAP images with approximate radiative-transfer relations | E: Outside-in and inside-out extrapolations for protostellar cores and a self-shielding power law for prestellar cores, applied to 883 ALMA-IMF cores | R: Prestellar 17-31 K, protostellar 28-79 K (5th-95th percentiles, up to 127 K); luminosities 20-80 000 Lsun | F: The method yields the first data-informed temperatures for the full ALMA-IMF core sample | **supported**
- H: The outside-in and inside-out temperature estimates for luminous protostellar cores are consistent | E: Compared the two estimates for 151 cores | R: Correlated, 36% mean fractional difference with inside-out about 19 K higher | F: Authors call the two consistent but see no reason to favour one, and average them | **partially**
- H: The new temperatures agree with earlier ALMA-IMF dust-temperature estimates | E: Compared with the pilot study, Paper VI and Paper X temperatures and with Paper IX assumed temperatures | R: Agreement within 40% (pilot) and 30% (Papers VI and X) | F: Earlier estimates are validated within these tolerances | **supported**
- H: Dust-based temperatures of hot cores are consistent with COM-line-based temperatures | E: Compared dust temperatures of cores hosting methyl formate hot cores with Paper XI assumed 100 K and 300 K | R: COM-based temperatures are on average 1.7 times higher | F: Dust-based temperature of luminous protostellar cores with hot cores is about half the COM-based value; the discrepancy is unresolved | **refuted**
- H: The M_core versus L_proto diagram of ALMA-IMF protostellar cores is matched by an accretion model where the initial core is the mass reservoir | E: Overplotted the 151 cores on the Duarte-Cabral et al. decreasing, intermittent accretion model | R: Cores are too luminous or not massive enough relative to the model | F: Favours replenished or growing mass reservoirs (core formation efficiency above 100%) rather than the initial core as reservoir | **partially**
- H: Core temperatures increase with protocluster evolution | E: Compared the core temperature distributions per protocluster against L/M and against the Young/Intermediate/Evolved classification | R: No correlation with L/M, but median temperature rises from ~22 K to ~26 K to ~29 K by stage | F: The dense gas affected by HII regions is a better evolutionary tracer than L/M | **supported**

## Reasoning

- Why this data: ALMA-IMF found about a thousand cores whose masses and luminosities need observational constraints  
  > "As ALMA-IMF has captured a large core sample, there is a pressing need for observationally driven constraints on their masses and luminosities." (Introduction)
- Why this method: PPMAP preserves the angular resolution of the best-resolved input data, giving temperature and luminosity at 2.5 arcsec  
  > "The Bayesian point process mapping (*PPMAP*) procedure proposes a partial solution to the issue of measuring the luminosity and temperature of individual cores since it preserves at best the angular resolution of the best resolved datasets" (Introduction)
- Alternative: Optically thin mass equation considered but replaced by the optically-thick-corrected form for all cores  
  > "Since the thermal dust emission of most ALMA-IMF cores is largely optically thin at 1.3 mm, we could have computed the mass of ALMA-IMF cores using the following equation:" (6.2 Resulting core mass)
- Alternative: Neither temperature estimate preferred; the two are averaged  
  > "there is no reason to favor one estimate over the other" (6.1 Adopted core temperatures)
- How they decided it was enough: _not stated_
- Limitation (authors): Study is not complete for intermediate-mass protostars and struggles with low-mass protostars  
  > "The present study will therefore have difficulty characterizing low-mass protostars, nor will it be complete for intermediate-mass protostars of the ALMA-IMF protoclusters" (2.2 Luminosity peaks in ALMA-IMF protoclusters)
- Limitation (authors): Background luminosity within luminosity peaks set to zero, overestimating low-luminosity protostars  
  > "As we have no information whatsoever on the value of this background (at scale between $2.5\ensuremath{''}$ and the core size), we are forced to set it here to zero." (4.3 Inside-out estimate using PPMAP peak luminosities)
- Limitation (authors): Dust emissivity uncertainty dominates mass uncertainty (factor of at least 5)  
  > "Uncertainties on the dust emissivity of dense cloud structures lead to even greater uncertainties in core mass estimates, a factor of at least 5 according to (cite: koehler2015)." (6.2 Resulting core mass)
- Limitation (authors): No radiative transfer modeling exists for prestellar cores in such strong-ISRF protoclusters, so the exponent is an assumption  
  > "The lack of dedicated radiative transfer modeling for these extreme protoclusters nevertheless prevents us from predicting the effect of a strong ISRF on the index studied here." (5.2 Outside-in estimate for prestellar cores using PPMAP dust temperatures)
- Limitation (authors): Fluxes of protostellar cores possibly contaminated by free-free emission are upper limits, so their masses are too  
  > "The remaining protostellar cores potentially contaminated by free-free emission have fluxes that correspond to upper limits, and consequently so do their masses." (6.2 Resulting core mass)
- Caveat (inferred, ours): Extrapolation from 2.5 arcsec to ~2000 au rests on assumed single power laws (rho r^-2, T r^-0.36 or r^0.2) with no resolved test at core scale.
- Caveat (inferred, ours): The two protostellar temperature estimates differ by ~19 K and are simply averaged; the average inherits both systematic errors.
- Caveat (inferred, ours): Mass uncertainty (20-40%) excludes the dust emissivity uncertainty, which the authors say can be a factor of 5.
- Caveat (inferred, ours): Core classification depends on an unpublished outflow survey (Nony et al. in prep.).
- Caveat (inferred, ours): Median prestellar temperature is quoted as 23 K in section 6.3.3 and 22 K in the Conclusion.
- Caveat (inferred, ours): Free-free correction is not homogeneous across protoclusters.

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Paper XII PPMAP temperature and luminosity images and luminosity peak catalog
- Missing: Core catalogs with fluxes, sizes and beams (companion papers; per-core classification relies on an unpublished paper)
- Missing: getsf configuration for the new luminosity-peak extraction
- Missing: Fit procedure for the power-law plus Gaussian luminosity profiles
- Missing: Mass-uncertainty propagation details
- Data volume (inferred): Derived products only (catalog tables plus 14 sets of 2.5 arcsec PPMAP maps and 1.3 mm images): roughly a few GB; no raw ALMA visibilities are reprocessed.
- Score (inferred): 3/5, Equations, constants and exponents are fully given and results are numeric, but the key inputs (PPMAP images, core catalogs, classification) come from other papers and are not restated.
- Rediscovery candidate: no, The temperature and mass recipe is closed-form, but it depends on PPMAP images and catalogs from companion papers, and the paper does not state that these are public.

## Links

- Method: (cite: dellova2024) (Paper XII: PPMAP dust temperature, column density and luminosity images and luminosity peak catalog)
- Method: (cite: marsh2015; marsh2017) (PPMAP procedure)
- Method: (cite: men2021getsf) (getsf source extraction)
- Method: (cite: terebey1993) (Protostellar envelope temperature law and normalisation constants)
- Method: (cite: pouteau2022) (Optically-thick-corrected mass equation and W43-MM3 catalog)
- Companion: (cite: motte2022) (ALMA-IMF Large Program overview, protocluster classification and distances)
- Companion: (cite: louvet2024) (Homogeneous core catalog for all 15 protoclusters)
- Companion: (cite: pouteau2022); (cite: nony2023); (cite: armante2024) (Core catalogs for W43-MM1/MM2/MM3 and G012.80)
- Companion: (cite: bonfand2024) (Methyl formate hot-core survey and COM-based temperatures)
- Companion: (cite: valeille2024) (High-velocity outflows and prestellar core candidates)
- Companion: (cite: brouillet2022) (W43-MM1 hot cores)
- Companion: (cite: diazgonzalez2023); (cite: galvanmadrid2024) (Free-free emission corrected 1.3 mm images)
- Related: ALMA-IMF Large Program (2017.1.01355.L)
- Related: Herschel HOBYS (comparison of prestellar core temperatures)

## Checks

```json
{
 "quotes": 144,
 "quotes_ok": 144,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 22,
 "numeric_problems": 0,
 "fill": {
  "facts": 142,
  "stated": 97,
  "rate": 0.683
 },
 "evidence_ok": true
}
```
