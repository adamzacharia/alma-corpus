# Introducing PxP: A Population Synthesis Framework for Predicting Young Stellar Object Properties

`2026ApJ..1001..170P` | The Astrophysical Journal 2026 | first author: Peltonen, J. | arXiv: 2603.29012 | DOI: 10.3847/1538-4357/ae58a7

Card schema 1.0 | model gpt-6.1-sol | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation
- Question: Infer the short timescale (<3 Myr) star formation history from unresolved sources in multiband JWST imaging.  
  > "Our goal is to infer the short timescale ($<3~\mathrm{Myr}$) star formation history from the distribution of fluxes of unresolved sources in multiband JWST imaging data." (Introduction)
- Target **N44**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **NGC 604**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2022.1.00276.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: PI: Rosolowsky  
  > "We use data from ALMA project 2022.1.00276.S (PI: Rosolowsky) reduced with the PHANGS-ALMA pipeline (cite: 2021Leroy)." (YSOC Selection)
- Line: 12CO J=1-0 (not stated)
- Other facility **JWST**: Public DDT 6555 (PI:M.G.Marin); NIRCam F090W, F200W, F444W and MIRI F770W, F1130W, F1500W imaging of NGC 604.  
  > "We retrieved data from the public JWST program DDT 6555 (PI:M.G.Marin)." (Data); "We make use of six imaging filters, three from NIRCam (F090W, F200W, and F444W) and three from MIRI (F770W, F1130W, and F1500W)." (Data)
- Other facility **Spitzer**: Photometry underlying the 49-source N44 YSO catalog used for PxP.  
  > "we use the older YSO catalog of (cite: 2009Gruendl) identified through *Spitzer* photometry, which contains flux measurements for 49 YSOs in the N44 region." (N44)
- Other facility **Mikulski Archive for Space Telescopes (MAST)**: All JWST data presented in the paper.  
  > "All of the JWST data presented in this paper were obtained from the Mikulski Archive for Space Telescopes (MAST) at the Space Telescope Science Institute." (Acknowledgments)
- External data: Kroupa IMF for individual stellar masses.  
  > "We use the IMF from (cite: 2001Kroupa) that gives the probability distribution of individual star masses." (Stellar Mass Distributions) [from (cite: 2001Kroupa)]
- External data: Cluster mass function shape.  
  > "which is adopted from (cite: slug4)." (Stellar Mass Distributions) [from (cite: slug4)]
- External data: Binary population distributions used to assign secondary companions.  
  > "Using the binary population distributions from (cite: 2017Moe), some individual stars were given a secondary companion." (Stellar Mass Distributions) [from (cite: 2017Moe)]
- External data: Modified stellar evolution code assigning primary-star temperature and total luminosity.  
  > "we use a modified version of the (cite: 2012Klassen) stellar evolution code, where all primary stars were assigned a temperature and total luminosity depending on the stellar mass, age, and an adopted accretion prescription." (Star Formation and Accretion Histories) [from (cite: 2012Klassen)]
- External data: Modified turbulent-core accretion history adopted for the main analysis.  
  > "our initial testing showed that the (cite: 2025Richardson) modified turbulent-core accretion was the most effective at replicating observed sources." (Star Formation and Accretion Histories) [from (cite: 2025Richardson)]
- External data: Accretion-history parameterization.  
  > "using the parameterization of (cite: 2011Offner)." (Star Formation and Accretion Histories) [from (cite: 2011Offner)]
- External data: Radiative transfer model geometries spubsmi, s-pbsmi and sp--smi; 60000 models viewed from nine angles.  
  > "Specifically, we chose the “`spubsmi`”, “`s-pbsmi`”, and “`sp--smi`” geometries originally described in (cite: rob17), which contains the simulated flux of 60000 models, each viewed from nine different angles." (Model SEDs); "However, the (cite: 2024Richardson) radiative transfer models have no prescribed evolution or timescale" (Model SEDs) [from (cite: rob17); (cite: 2024Richardson)]
- External data: Average Milky Way extinction parameterization converting A_V to filter extinction.  
  > "We use the extinction parameterization of (cite: 2023Gordon) based on average Milky Way measurements to convert a single value of visual extinction ($A_V$) to the extinction appropriate for each filter." (Model SEDs) [from (cite: 2023Gordon)]
- External data: M33 YSO Candidate catalog minimum fluxes: 10 μJy at 21 μm and 1 μJy at 1.6 μm.  
  > "Specifically, SEDs were excluded for sources lower than the minimum fluxes in the (cite: 2024Peltonen) M33 YSO Candidate catalog (10 $\mu$Jy at 21 $\mu$m and 1 $\mu$Jy at 1.6 $\mu$m)." (Example Results) [from (cite: 2024Peltonen)]
- External data: N44 catalog containing Spitzer flux measurements for 49 YSOs.  
  > "we use the older YSO catalog of (cite: 2009Gruendl) identified through *Spitzer* photometry, which contains flux measurements for 49 YSOs in the N44 region." (N44) [from (cite: 2009Gruendl)]
- External data: N44 total YSO population mass estimate of ~3537 M_sun used for comparison.  
  > "Next, (cite: 2012Carlson) determined the total YSO population mass by fitting the high-mass end of a (cite: 2001Kroupa) IMF to the YSO masses." (N44); "This method yielded an estimated total mass of the N44 YSOs to be $\sim$3537 M$_\odot$." (N44) [from (cite: 2012Carlson)]
- External data: N44 individual YSO ages from Spitzer photometry and Robitaille model fits.  
  > "(cite: 2009Chen) fit each YSO that they identified with *Spitzer* photmetry with a (cite: 2006Robitaille) model." (N44); "The YSOs had a large spread in best-fit ages from 10$^3$-$2\times10^6$ yr." (N44) [from (cite: 2009Chen)]
- External data: Previously reduced NGC 604 JWST imaging.  
  > "These reduced data are described in more detail and first appear in (cite: 2025Sarbadhicary)." (Data) [from (cite: 2025Sarbadhicary)]
- External data: Approximately 8 percent M33 YSOC contamination estimate.  
  > "(cite: 2024Peltonen) estimated the $\approx$8 percent of their YSOCs in M33 were contaminants." (YSOC Selection) [from (cite: 2024Peltonen)]
- External data: NGC 604 embedded stellar mass and older stellar population inferred from Spitzer observations.  
  > "(cite: 2012Martinez) found a mass of $(1.2^{+1.3}_{-0.1})\times10^4$ M$_\odot$ contained in embedded star formation from model fits to unresolved *Spitzer* photometry and spectroscopy." (Model Fit); "They also found that this embedded population is a second generation of star formation, along with an existing older population ($\sim$4 Myr)." (Model Fit) [from (cite: 2012Martinez)]
- External data: M33 star formation maps and NGC 604 Hα star formation rate of 0.016±0.002 M_sun/yr.  
  > "The star formation maps of (cite: 2015Boquien) predict the star formation rate across M33 in a variety of tracers." (Model Fit); "The predicted star formation rate in NGC 604 using H$\alpha$ is 0.016$\pm0.002$ $M_\odot$/yr (cite: 2015Boquien)." (Model Fit) [from (cite: 2015Boquien)]
- Simulation/model as data: 550000 populations: 11 masses from 10^3–10^5 M_sun, 50 ages from 0.3–3 Myr, 1000 realizations per mass and age.  
  > "We began by generating model populations with 11 masses logarithmically spaced from 10$^3$-10$^5$ M$_\odot$ and 50 ages linearly spaced from 0.3-3 Myr." (Fitting); "For each of these masses and ages, we generated 1000 populations for a total of 550000 populations." (Fitting)
- Simulation/model as data: A_V=0–20 magnitudes; 11,550,000 unique sets of SEDs after applying constant extinction screens.  
  > "We then applied a constant extinction screen to each of these SEDs with $A_V$ from 0-20 magnitudes for a total of 11,550,000 unique sets of SEDs." (Fitting)

## Processing

### Calibration

- pipeline or manual: PHANGS-ALMA pipeline  
  > "We use data from ALMA project 2022.1.00276.S (PI: Rosolowsky) reduced with the PHANGS-ALMA pipeline (cite: 2021Leroy)." (YSOC Selection)
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

- ALMA reduction with the PHANGS-ALMA pipeline.  
  > "We use data from ALMA project 2022.1.00276.S (PI: Rosolowsky) reduced with the PHANGS-ALMA pipeline (cite: 2021Leroy)." (YSOC Selection) [from (cite: 2021Leroy)]
- Kroupa IMF.  
  > "We use the IMF from (cite: 2001Kroupa) that gives the probability distribution of individual star masses." (Stellar Mass Distributions) [from (cite: 2001Kroupa)]
- Cluster mass function shape.  
  > "which is adopted from (cite: slug4)." (Stellar Mass Distributions) [from (cite: slug4)]
- Binary population distributions.  
  > "Using the binary population distributions from (cite: 2017Moe), some individual stars were given a secondary companion." (Stellar Mass Distributions) [from (cite: 2017Moe)]
- Modified stellar evolution code.  
  > "we use a modified version of the (cite: 2012Klassen) stellar evolution code" (Star Formation and Accretion Histories) [from (cite: 2012Klassen)]
- Use total luminosity, including accretion luminosity.  
  > "Following (cite: 2025Richardson) we utilize the total luminosity to fully capture the state of YSO." (Star Formation and Accretion Histories) [from (cite: 2025Richardson)]
- Modified turbulent-core accretion and accretion-history parameterization.  
  > "our initial testing showed that the (cite: 2025Richardson) modified turbulent-core accretion was the most effective at replicating observed sources." (Star Formation and Accretion Histories); "using the parameterization of (cite: 2011Offner)." (Star Formation and Accretion Histories) [from (cite: 2025Richardson); (cite: 2011Offner)]
- Radiative transfer geometries spubsmi, s-pbsmi and sp--smi.  
  > "Specifically, we chose the “`spubsmi`”, “`s-pbsmi`”, and “`sp--smi`” geometries originally described in (cite: rob17), which contains the simulated flux of 60000 models, each viewed from nine different angles." (Model SEDs) [from (cite: rob17); (cite: 2024Richardson)]
- Foreground extinction law based on average Milky Way measurements.  
  > "We use the extinction parameterization of (cite: 2023Gordon) based on average Milky Way measurements to convert a single value of visual extinction ($A_V$) to the extinction appropriate for each filter." (Model SEDs) [from (cite: 2023Gordon)]
- Detectability cuts from the M33 YSO Candidate catalog.  
  > "Specifically, SEDs were excluded for sources lower than the minimum fluxes in the (cite: 2024Peltonen) M33 YSO Candidate catalog (10 $\mu$Jy at 21 $\mu$m and 1 $\mu$Jy at 1.6 $\mu$m)." (Example Results) [from (cite: 2024Peltonen)]
- JWST reduction details in the earlier presentation of the reduced data.  
  > "The raw data were reduced using PJPIPE developed for PHANGS-JWST (cite: 2024Williams)." (Data); "These reduced data are described in more detail and first appear in (cite: 2025Sarbadhicary)." (Data) [from (cite: 2024Williams); (cite: 2025Sarbadhicary)]
- YSOC selection procedure.  
  > "The YSOC selection was performed according to the procedure outlined in (cite: 2024Peltonen)." (YSOC Selection) [from (cite: 2024Peltonen)]

### Not stated but needed to reproduce (our reading)

- ALMA CO detection threshold, velocity integration interval, spatial matching radius and treatment of map edges or nondetections.
- ALMA product identity, beam, sensitivity, spectral resolution and PHANGS-ALMA pipeline version.
- Exact cluster fraction f_clust, CMF cutoff M_0 and stellar or cluster mass limits used in the generated populations.
- Exact modified stellar evolution and accretion implementation and radiative transfer grid release.
- PCA input scaling, missing-band treatment, numerical basis and histogram bin edges.
- MCMC walker count, initialization, chain length, burn-in, convergence tests and uncertainty-summary convention.
- Adopted target distances and the transformation between Spitzer observations and model filter coverage.
- DOLPHOT configuration, photometric corrections and the resolution of the inconsistent MIRI filter lists.

## Analysis recipe

1. **Generate stellar populations**: Draw individual YSOs and clusters from the IMF and CMF until the total population mass is reached; assign binary companions.  
  > "individual YSOs and clusters are assigned to the population with masses drawn from the Initial mass function (IMF) and cluster mass function (CMF) until the total population mass is reached." (Stellar Mass Distributions); "Using the binary population distributions from (cite: 2017Moe), some individual stars were given a secondary companion." (Stellar Mass Distributions)
   - software: PxP
   - parameter: Total mass M_star, age t_0 and foreground extinction A_V.  
  > "Under these assumptions, we can generate model populations with only three free parameters: total mass ($M_\star$), age ($t_0$, defined as time since the start of protostar formation), and foreground extinction ($A_V$)." (Example Results)
   - assumption: Kroupa IMF and modified turbulent-core accretion.  
  > "We use the IMF from (cite: 2001Kroupa) that gives the probability distribution of individual star masses." (Stellar Mass Distributions); "We thus focus on populations using turbulent-core accretion for the remainder of this work." (Star Formation and Accretion Histories)
   - assumption: Burst and continuous star formation histories.  
  > "The first case is the burst model where all members of a population begin accreting at the same moment in time." (Star Formation and Accretion Histories); "The other case is the continuous star formation history, where the ages of the individual sources is evenly distributed from the beginning of accretion to the current age of the population." (Star Formation and Accretion Histories)
   - fitting: _not stated_
   - validation: Initial comparison of accretion histories against observed sources.  
  > "our initial testing showed that the (cite: 2025Richardson) modified turbulent-core accretion was the most effective at replicating observed sources." (Star Formation and Accretion Histories)
2. **Construct observable source SEDs**: Match isolated YSOs to radiative transfer models in temperature-luminosity quantile space; combine cluster-member and intracluster-medium fluxes.  
  > "For each isolated YSO, a model was randomly selected from the 10 nearest neighbors in temperature-luminosity quantile space (quantile transform fit to the temperature and luminosity of all models)." (Model SEDs); "The final cluster flux in each filter is found by adding the flux contributions of all of the members and the intra-cluster medium." (Model SEDs)
   - software: PxP
   - parameter: Random inclination; largest aperture 10^6 AU for isolated YSOs.  
  > "A random inclination is chosen, then the flux of that star was taken to be the flux in the largest aperture ($10^6$ AU) in each filter, given by the chosen model." (Model SEDs)
   - parameter: Reject model SEDs below 10 μJy at 21 μm and 1 μJy at 1.6 μm.  
  > "Specifically, SEDs were excluded for sources lower than the minimum fluxes in the (cite: 2024Peltonen) M33 YSO Candidate catalog (10 $\mu$Jy at 21 $\mu$m and 1 $\mu$Jy at 1.6 $\mu$m)." (Example Results)
   - assumption: Cluster diameter equals the smallest MIRI resolution element, 0.207 arcsec.  
  > "we used the number of cluster members to determine the average member separation, assuming the cluster diameter is the size of the smallest MIRI resolution element (0.207$''$)." (Model SEDs)
   - assumption: Constant foreground extinction screen across each population.  
  > "In this initial implementation, we adopt a simple screen along the line of sight with a constant extinction across the entire population." (Model SEDs)
   - fitting: _not stated_
   - validation: _not stated_
3. **Build the PCA population likelihood**: Transform source SEDs into the first two principal components; construct 10×10 histograms and fit folded normal count distributions at each grid point.  
  > "We determined the principal component basis using all of our source fluxes (the SED of all of the individual YSOs and unresolved clusters)." (Fitting); "We then created 10$\times$10 two-dimensional (2D) histograms for each cloud-scale population." (Fitting); "Therefore, for each grid point, we fit a folded normal distribution" (Fitting)
   - software: PxP, EMCEE
   - parameter: 11 logarithmically spaced masses, 10^3–10^5 M_sun; 50 linearly spaced ages, 0.3–3 Myr; 1000 realizations per combination.  
  > "We began by generating model populations with 11 masses logarithmically spaced from 10$^3$-10$^5$ M$_\odot$ and 50 ages linearly spaced from 0.3-3 Myr." (Fitting); "For each of these masses and ages, we generated 1000 populations for a total of 550000 populations." (Fitting)
   - parameter: A_V=0–20 magnitudes.  
  > "We then applied a constant extinction screen to each of these SEDs with $A_V$ from 0-20 magnitudes for a total of 11,550,000 unique sets of SEDs." (Fitting)
   - assumption: Flat priors over the sampled model parameter ranges.  
  > "We adopt flat priors over the range of parameters sampled in our models (see above)." (Fitting)
   - fitting: Sum log-probabilities of observed source counts across histogram grid points and sample the posterior with EMCEE.  
  > "can be found by summing the log-probabilities at each grid point using the actual number of sources and the model PDFs." (Fitting); "This sampling is done using the Markov chain Monte Carlo package EMCEE (cite: 2013emcee)." (Fitting)
   - validation: First two components contain approximately 97% of variance; folded normal distributions empirically outperform Poisson and normal distributions.  
  > "these first two components contained $\approx97\%$ of the variance in the full sample." (Fitting); "We adopt the folded normal functional form based on a better empirical match to the population distributions than simpler forms like Poisson or normal distributions." (Fitting)
4. **Test parameter recovery**: Generate new model populations, impose the catalog flux cuts, fit with PxP and compare recovered properties against inputs.  
  > "Using the same population synthesis methodology described in Section [2](#sec:popsyn), we created new populations with a range of properties." (Self-Fit Testing); "We made the same flux cuts only including sources that would be detectable in the (cite: 2024Peltonen) YSOC catalog." (Self-Fit Testing); "We then fit these new populations with PxP and compared the estimated properties to those that were used to generate the model population." (Self-Fit Testing)
   - software: PxP
   - fitting: PxP self-retrieval.  
  > "We then fit these new populations with PxP and compared the estimated properties to those that were used to generate the model population." (Self-Fit Testing)
   - validation: Assess age and mass recovery, including interquartile ranges and source-count limits.  
  > "The age predictions of PxP should not be used unless there are at least 15-40 sources, which translates to 4000 M$_\odot$ population at 1 Mpc." (Self-Fit Testing); "The total mass of the population is predicted more consistently than age." (Self-Fit Testing)
5. **Fit the N44 comparison population**: Apply PxP to the 49-source Spitzer YSO catalog; compare burst and continuous star formation histories.  
  > "we use the older YSO catalog of (cite: 2009Gruendl) identified through *Spitzer* photometry, which contains flux measurements for 49 YSOs in the N44 region." (N44); "Using the continuous star formation history instead of the burst model leads to different estimated properties." (N44)
   - software: PxP
   - assumption: Sources can represent unresolved clusters and binaries.  
  > "our model assumption that many of the sources are associated with unresolved clusters and binaries and not just individual YSOs" (N44)
   - fitting: PxP population fitting.  
  > "Thus, for the PxP analysis, we use the older YSO catalog of (cite: 2009Gruendl)" (N44)
   - validation: Compare against previous N44 masses and ages and inspect observed versus best-fit PCA grids.  
  > "The mass is in the same order of magnitude but higher than the prediction of (cite: 2012Carlson)." (N44); "PxP’s estimate is in the range spanned by the (cite: 2009Chen) sources." (N44); "there is a clear distinction between the real grid and the best-fit median grid." (N44)
6. **Measure NGC 604 point-source photometry**: Use DOLPHOT simultaneously in three NIRCam bands; use the resulting catalog as a warmstart file for the JWST/MIRI module.  
  > "We use the DOLPHOT software (cite: 2000Dolphin; 2016Dolphin) with the JWST/NIRCam module (cite: 2023Weisz) in all three NIRCam bands (F090W, F200W, and F444W) simultaneously." (YSOC Selection); "This catalog of NIRCam identified sources is used as a warmstart file for the DOLPHOT JWST/MIRI module (cite: 2024Peltonen) to obtain photometry in the three JWST bands (F444W, F770W, F1500W)." (YSOC Selection)
   - software: DOLPHOT
   - parameter: Local SNR >25; sharpness squared <0.09; object type 1; no quality flags.  
  > "We retain sources if they have a local signal-to-noise ratio (SNR) $>$25, (sharpness)$^2<$0.09, object type 1, and no quality flags." (YSOC Selection)
   - fitting: _not stated_
   - validation: Visual check of MIRI images found every discernible point source associated with a DOLPHOT source.  
  > "However, we examined the long wavelength images from MIRI by eye and found that all discernible point sources were associated with a DOLPHOT source." (YSOC Selection)
7. **Select NGC 604 YSO candidates**: Apply color-color and color-magnitude cuts, reject sources without ALMA CO detections, then visually remove background galaxies and ISM sources.  
  > "The YSOC selection was performed according to the procedure outlined in (cite: 2024Peltonen)." (YSOC Selection); "An additional 26 sources were removed that had no ALMA $^{12}$CO J=1-0 detection" (YSOC Selection); "Finally, we perform a visual inspection on the remaining sources to remove background galaxies and ISM sources." (YSOC Selection)
   - parameter: log10(F4.4/F2)>−0.25; log10(F4.4/F15)<−0.25.  
  > "\log_{10}(F_{4.4}/F_{2})>-0.25" (YSOC Selection); "\log_{10}(F_{4.4}/F_{15})<-0.25." (YSOC Selection)
   - parameter: log(F4.4/μJy)>−0.5; log(F4.4/μJy)>2.5 log(F4.4/F2)−1.2.  
  > "\log(F_{4.4}/\mathrm{\mu Jy})>-0.5" (YSOC Selection); "\log(F_{4.4}/\mathrm{\mu Jy})>2.5 \log(F_{4.4}/F_{2}) -1.2." (YSOC Selection)
   - parameter: Keep sources appearing point-like in at least three filters.  
  > "Sources that appeared point-like in at least three filters were kept, leaving 112 YSO candidates (YSOCs)." (YSOC Selection)
   - assumption: Expect approximately 9 contaminants among 112 YSOCs by transferring the earlier M33 contamination estimate.  
  > "Therefore, we expect that $\approx$9 of our 112 YSOCs are contaminants since we followed the YSOC identification strategy of (cite: 2024Peltonen) closely." (YSOC Selection)
   - fitting: _not stated_
   - validation: Visual inspection for point-like appearance and rejection of galaxies and ISM sources.  
  > "Finally, we perform a visual inspection on the remaining sources to remove background galaxies and ISM sources." (YSOC Selection); "Sources that appeared point-like in at least three filters were kept, leaving 112 YSO candidates (YSOCs)." (YSOC Selection)
8. **Fit the NGC 604 population**: Apply PxP to the selected YSOC catalog and compare burst and continuous models.  
  > "Now equipped with a catalog of YSOCs in NGC 604, we can apply PxP." (Model Fit); "The continuous model predictions again differ from the burst model." (Model Fit)
   - software: PxP
   - fitting: PxP fitting with posterior parameters displayed in a corner plot.  
  > "Figure [12](#fig:corner604) shows the resulting corner plot produced by PxP." (Model Fit)
   - validation: Inspect PCA grids and compare the inferred embedded mass with Spitzer estimates.  
  > "The PCA grids show that PxP was able to find a reasonable fit." (Model Fit); "The mass estimate of embedded star formation from *Spitzer* is consistent with the PxP mass estimate." (Model Fit)
9. **Calculate the recent star formation rate**: Divide total population mass by population age; compare burst and continuous estimates with the Hα rate.  
  > "Simply dividing the total mass of the population by the age of the population gives a star formation rate of 0.035$\pm0.003$ $M_\odot$/yr." (Model Fit); "If we consider the continuous model the greater age gives a star formation rate of 0.019$\pm0.002$ $M_\odot$/yr closer but still larger than the (cite: 2015Boquien) estimate." (Model Fit)
   - assumption: Hα traces a later stage, likely the first generation of star formation.  
  > "H$\alpha$ should be tracing a later stage of star formation likely corresponding to the first generation of star formation seen by (cite: 2012Martinez)." (Model Fit)
   - fitting: _not stated_
   - validation: Compare with the literature Hα star formation rate.  
  > "The predicted star formation rate in NGC 604 using H$\alpha$ is 0.016$\pm0.002$ $M_\odot$/yr (cite: 2015Boquien)." (Model Fit)

## Software

- **PxP** : Combine population synthesis and PCA to determine YSO population properties.  
  > "We will refer to the entirety of this approach as PxP since it combines **P**opulation synthesis with **P**CA to determine YSO population properties." (Fitting)
- **PHANGS-ALMA pipeline** : Reduce the ALMA data used for CO detection screening.  
  > "We use data from ALMA project 2022.1.00276.S (PI: Rosolowsky) reduced with the PHANGS-ALMA pipeline (cite: 2021Leroy)." (YSOC Selection)
- **PJPIPE** : Reduce raw JWST data.  
  > "The raw data were reduced using PJPIPE developed for PHANGS-JWST (cite: 2024Williams)." (Data)
- **DOLPHOT** : NIRCam and MIRI point-source photometry using JWST modules.  
  > "We use the DOLPHOT software (cite: 2000Dolphin; 2016Dolphin) with the JWST/NIRCam module (cite: 2023Weisz) in all three NIRCam bands (F090W, F200W, and F444W) simultaneously." (YSOC Selection); "This catalog of NIRCam identified sources is used as a warmstart file for the DOLPHOT JWST/MIRI module (cite: 2024Peltonen) to obtain photometry in the three JWST bands (F444W, F770W, F1500W)." (YSOC Selection)
- **emcee** : Markov chain Monte Carlo sampling of the population-property posterior.  
  > "We then estimate the posterior distribution of YSO population properties by sampling the total log-probability of the model parameters." (Fitting); "This sampling is done using the Markov chain Monte Carlo package EMCEE (cite: 2013emcee)." (Fitting)
- **astropy** : _not stated_
- **JWST pipeline** : _not stated_
- **corner** : _not stated_
- **matplotlib** : _not stated_
- **MATCH** : Main-sequence population synthesis cited as background.  
  > "This approach is known as population synthesis and has been used to great effect in main-sequence populations with codes like `MATCH` (cite: 2002Dolphin)." (Introduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Sources rejected for lacking an ALMA CO detection | 26 | not stated | sources | 7 | An additional 26 sources were removed that had no ALMA $^{12}$CO J=1-0 detection |
| Final NGC 604 YSO candidate count | 112 | not stated | YSOCs | 7 | Sources that appeared point-like in at least three filters were kept, leaving 112 YSO candidates (YSOCs). |
| N44 burst-model population mass | 1.1×10^4 | ±0.1×10^4 | M_sun | 5 | After fitting these YSOs, PxP recovers a mass of (1.1$\pm0.1$)$\times10^4$ M$_\odot$, an extinction of $A_V =3.2\pm0.4$, and an age of $t_0 = 0.74^{+0.06}_{-0.03}$ Myr |
| N44 burst-model foreground extinction A_V | 3.2 | ±0.4 | magnitudes | 5 | After fitting these YSOs, PxP recovers a mass of (1.1$\pm0.1$)$\times10^4$ M$_\odot$, an extinction of $A_V =3.2\pm0.4$, and an age of $t_0 = 0.74^{+0.06}_{-0.03}$ Myr; with $A_V$ from 0-20 magnitudes |
| N44 burst-model age t_0 | 0.74 | +0.06/-0.03 | Myr | 5 | After fitting these YSOs, PxP recovers a mass of (1.1$\pm0.1$)$\times10^4$ M$_\odot$, an extinction of $A_V =3.2\pm0.4$, and an age of $t_0 = 0.74^{+0.06}_{-0.03}$ Myr |
| N44 continuous-model age | 2.2 | ±0.2 | Myr | 5 | The age estimate is 2.2$\pm0.2$ Myr, approximately $3\times$ older than the age predicted by the burst model. |
| N44 continuous-model population mass | 1.7×10^4 | ±0.2×10^4 | M_sun | 5 | The mass estimate is $M_\star=(1.7\pm0.2)\times10^4$ M$_\odot$ and the derived extinction is $A_V=3.2\pm0.4$, which are comparable to the estimates from the burst model. |
| N44 continuous-model foreground extinction A_V | 3.2 | ±0.4 | magnitudes | 5 | The mass estimate is $M_\star=(1.7\pm0.2)\times10^4$ M$_\odot$ and the derived extinction is $A_V=3.2\pm0.4$, which are comparable to the estimates from the burst model.; with $A_V$ from 0-20 magnitudes |
| NGC 604 burst-model population mass | 2.2×10^4 | ±0.2×10^4 | M_sun | 8 | the best-fitting parameters for the YSOC population in NGC 604 are a mass of $M_\star = (2.2\pm0.2)\times10^4$ $M_\odot$, $A_V=10.5\pm0.3$, and $t_0 = 0.62\pm0.01$ Myr. |
| NGC 604 burst-model foreground extinction A_V | 10.5 | ±0.3 | magnitudes | 8 | the best-fitting parameters for the YSOC population in NGC 604 are a mass of $M_\star = (2.2\pm0.2)\times10^4$ $M_\odot$, $A_V=10.5\pm0.3$, and $t_0 = 0.62\pm0.01$ Myr.; with $A_V$ from 0-20 magnitudes |
| NGC 604 burst-model age t_0 | 0.62 | ±0.01 | Myr | 8 | the best-fitting parameters for the YSOC population in NGC 604 are a mass of $M_\star = (2.2\pm0.2)\times10^4$ $M_\odot$, $A_V=10.5\pm0.3$, and $t_0 = 0.62\pm0.01$ Myr. |
| NGC 604 continuous-model population mass | 3.6×10^4 | ±0.3×10^4 | M_sun | 8 | The continuous model predicts a mass of $M_\star = (3.6\pm0.3)\times10^4$ $M_\odot$, $A_V=8.8\pm0.4$, and $t_0 = 1.9\pm0.4$ Myr. |
| NGC 604 continuous-model foreground extinction A_V | 8.8 | ±0.4 | magnitudes | 8 | The continuous model predicts a mass of $M_\star = (3.6\pm0.3)\times10^4$ $M_\odot$, $A_V=8.8\pm0.4$, and $t_0 = 1.9\pm0.4$ Myr.; with $A_V$ from 0-20 magnitudes |
| NGC 604 continuous-model age t_0 | 1.9 | ±0.4 | Myr | 8 | The continuous model predicts a mass of $M_\star = (3.6\pm0.3)\times10^4$ $M_\odot$, $A_V=8.8\pm0.4$, and $t_0 = 1.9\pm0.4$ Myr. |
| NGC 604 burst-model star formation rate | 0.035 | ±0.003 | M_sun/yr | 9 | Simply dividing the total mass of the population by the age of the population gives a star formation rate of 0.035$\pm0.003$ $M_\odot$/yr. |
| NGC 604 continuous-model star formation rate | 0.019 | ±0.002 | M_sun/yr | 9 | If we consider the continuous model the greater age gives a star formation rate of 0.019$\pm0.002$ $M_\odot$/yr closer but still larger than the (cite: 2015Boquien) estimate. |
| Self-fit minimum source count for age predictions | 15-40 | not stated | sources | 4 | The age predictions of PxP should not be used unless there are at least 15-40 sources, which translates to 4000 M$_\odot$ population at 1 Mpc. |
| Self-fit age IQR at 4000 M_sun | ≈0.2 | not stated | dex | 4 | The interquartile range (IQR) of the predicted ages is $\approx0.2$ dex at 4000 M$_\odot$ and $<0.1$ dex for populations $\geq10000$ M$_\odot$. |
| Self-fit age IQR for populations ≥10000 M_sun | <0.1 | not stated | dex | 4 | The interquartile range (IQR) of the predicted ages is $\approx0.2$ dex at 4000 M$_\odot$ and $<0.1$ dex for populations $\geq10000$ M$_\odot$. |

## Qualitative findings

- Mass is recovered more consistently than age in self-fitting tests.  
  > "The total mass of the population is predicted more consistently than age." (Self-Fit Testing)
- The burst model fits both observed populations better than the continuous model.  
  > "We find that the probability of the continuous model generating the observed data is eight orders of magnitude worse than the burst model." (N44); "Again the continuous model is a worse fit with the total probability being 10 orders of magnitude worse than the burst model." (Model Fit)
- NGC 604 star formation activity has not decreased and may have increased in the second generation.  
  > "Therefore, our estimate implies that star formation activity has not decreased with the second generation and has possibly even increased." (Model Fit)

## Claim tuples

- H: PxP can recover YSO population mass and age from source SED distributions. | E: Fit newly generated model populations and compare recovered parameters with their inputs. | R: Mass is recovered more consistently; age predictions require at least 15-40 sources. | F: Self-retrieval supports the framework within source-count and age-dependent limits. | **partially**
- H: PxP can describe the observed NGC 604 YSO population. | E: Fit the selected NGC 604 YSOC catalog with PxP and inspect the PCA grids. | R: M_star=(2.2±0.2)×10^4 M_sun, A_V=10.5±0.3 and t_0=0.62±0.01 Myr. | F: A reasonable population fit is obtained and the mass agrees with the earlier Spitzer estimate. | **supported**
- H: Burst and continuous star formation histories can be distinguished for the two observed populations. | E: Fit N44 and NGC 604 using both histories and compare their probabilities. | R: Continuous-model probabilities are eight orders of magnitude worse for N44 and 10 orders worse for NGC 604. | F: The burst model is preferred within the tested model family. | **supported**
- H: The second generation of star formation in NGC 604 has maintained or increased its activity. | E: Divide the fitted population mass by its age and compare with the literature Hα rate. | R: The burst-model rate is 0.035±0.003 M_sun/yr, compared with 0.016±0.002 M_sun/yr from Hα. | F: Activity has not decreased and may have increased, but the comparison traces different stages. | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Use PCA because no single infrared color-magnitude or color-color diagram captures SED complexity.  
  > "However, there is no single color-magnitude or color-color diagram in the infrared that can represent the complexity of the SEDs (cite: 2017Jones)." (Fitting); "To discriminate between different YSO populations, we perform dimensionality reduction through PCA" (Fitting)
- Alternative: Other accretion histories were generated; modified turbulent-core accretion best replicated observed sources in initial testing.  
  > "We generated populations using all of the accretion histories" (Star Formation and Accretion Histories); "our initial testing showed that the (cite: 2025Richardson) modified turbulent-core accretion was the most effective at replicating observed sources." (Star Formation and Accretion Histories)
- Alternative: Folded normal distributions were preferred to Poisson and normal distributions.  
  > "We adopt the folded normal functional form based on a better empirical match to the population distributions than simpler forms like Poisson or normal distributions." (Fitting)
- Alternative: Continuous histories fit worse than burst histories for both N44 and NGC 604.  
  > "We find that the probability of the continuous model generating the observed data is eight orders of magnitude worse than the burst model." (N44); "Again the continuous model is a worse fit with the total probability being 10 orders of magnitude worse than the burst model." (Model Fit)
- How they decided it was enough: Use two components containing approximately 97% of variance and 10 histogram bins to balance resolution against small-number statistics.  
  > "these first two components contained $\approx97\%$ of the variance in the full sample." (Fitting); "We adopted 10 bins to have sufficient resolution while avoiding small-number statistics." (Fitting)
- Limitation (authors): Simplified star formation histories introduce systematic age uncertainty.  
  > "In the absence of these more sophisticated star formation histories, the simple model will introduce systematic uncertainty into the age estimations." (Star Formation and Accretion Histories)
- Limitation (authors): Accretion varies smoothly in the implementation; stochastic accretion is not explored.  
  > "Another important caveat is that the current implementation prescribes smooth variations in accretion, which differs from observed stochastic accretion (cite: 2023Fischer)." (Star Formation and Accretion Histories); "Our framework is capable of handling other varieties of accretion history, such as stochastic, but we do not explore those here." (Star Formation and Accretion Histories)
- Limitation (authors): F335M, F770W and F1130W may be poorly represented because PAH emission is not well simulated.  
  > "specifically F335M, F770W, and F1130W, which are often dominated by polycyclic aromatic hydrocarbons that are not well simulated in the models." (Example Results)
- Limitation (authors): Low source counts and older ages limit age recovery; the lower mass prior boundary biases 1000 M_sun populations upward.  
  > "However, lower mass populations with fewer sources do not give an accurate age prediction." (Self-Fit Testing); "populations older than $\sim2$ Myr are indistinguishable from one another for $M_\star < 10^4~M_\odot$." (Self-Fit Testing); "populations of $1000$ M$_\odot$ are predicted to have a systematically higher mass, which is due to $1000$ M$_\odot$ being the minimum allowed value in our flat mass prior." (Self-Fit Testing)
- Limitation (authors): N44 fits are affected by inconsistent SED coverage, catalog completeness and limited high-luminosity models.  
  > "These inconsistent SEDs could be leading to inconsistent PCA fits shifting the number of sources contained at each grid point." (N44); "Second, the completeness of the YSO catalogs could be resulting in fewer than expected faint sources being included in the population fits." (N44); "Third, the models have limited models at very high luminosities, which could lead to our model populations not accurately representing the brightest observed sources." (N44)
- Limitation (authors): The NIRCam-first catalog may omit deeply embedded sources.  
  > "This catalog may be missing some deeply embedded sources that are mid-infrared bright and near-infrared dim." (YSOC Selection)
- Limitation (authors): Two regions are insufficient for rigorous conclusions about changing star formation histories.  
  > "While no conclusions can be rigorously drawn from a sample of two regions" (Model Fit)
- Caveat (inferred, ours): The ALMA rejection cannot be audited without a detection threshold, velocity window and spatial association rule.
- Caveat (inferred, ours): Self-fitting tests assess recovery within the generating model family, rather than robustness to incorrect physical assumptions.
- Caveat (inferred, ours): The six-filter data description and the MIRI photometry filter list disagree: the latter includes F444W and omits F1130W.
- Caveat (inferred, ours): Quoted posterior uncertainties should be distinguished from uncertainty in accretion history, cluster fraction, completeness and contamination.
- Caveat (inferred, ours): The description does not explain how likelihoods are evaluated between sampled model grid points.

## Reproducibility

- Data public (paper): JWST program DDT 6555 is public.  
  > "We retrieved data from the public JWST program DDT 6555 (PI:M.G.Marin)." (Data)
- Products in archive: _not stated_
- Code: A full public PxP release is planned to accompany the future Milky Way analysis.  
  > "A full public release of PxP is planned to accompany this Milky Way analysis." (Conclusion)
- Missing: A released PxP implementation and the exact modified stellar evolution code.
- Missing: Numerical population-model settings, PCA transformations, histogram edges and fitted count-distribution grids.
- Missing: MCMC configuration and definitions of reported central values and uncertainties.
- Missing: Exact ALMA products and the CO-based rejection rule, including the identities of rejected candidates.
- Missing: JWST reduction and photometry configuration, adopted distances and treatment of missing or mismatched filters.
- Missing: The full machine-readable YSOC table, which is referenced but only partly supplied in this text.
- Data volume (inferred): Cannot estimate ALMA data volume from the stated project code and transition alone.
- Score (inferred): 40/5, The paper provides numeric results, selection cuts and a substantial conceptual recipe, but exact ALMA screening, model settings and sampling details are missing; the full PxP release is deferred.
- Rediscovery candidate: no, Main results are numeric and JWST data are stated to be public, but ALMA public availability is not stated and the end-to-end recipe lacks essential code and settings.

## Links

- Method: (cite: 2021Leroy) (PHANGS-ALMA reduction pipeline.)
- Method: (cite: 2024Williams) (PJPIPE JWST reduction.)
- Method: (cite: 2000Dolphin; 2016Dolphin) (DOLPHOT photometry.)
- Method: (cite: 2023Weisz) (DOLPHOT JWST/NIRCam module.)
- Method: (cite: 2024Peltonen) (DOLPHOT JWST/MIRI module, YSOC selection and model detectability cuts.)
- Method: (cite: 2013emcee) (MCMC posterior sampling.)
- Method: (cite: 1987Murtagh) (Principal component analysis.)
- Method: (cite: 2012Klassen) (Underlying stellar evolution code.)
- Method: (cite: 2011Offner) (Accretion-history parameterization.)
- Method: (cite: 2025Richardson) (Modified accretion implementation and use of total luminosity.)
- Method: (cite: rob17); (cite: 2024Richardson) (Radiative transfer models and selected geometries.)
- Method: (cite: 2023Gordon) (Foreground extinction parameterization.)
- Method: (cite: 2001Kroupa) (Adopted IMF.)
- Method: (cite: slug4) (Adopted CMF shape.)
- Method: (cite: 2017Moe) (Binary population distributions.)
- Companion: (cite: 2025Sarbadhicary) (First presentation and fuller description of the reduced NGC 604 JWST data.)
- Companion: Richardson (in prep.) (Planned investigation of differences between accretion histories.)
- Related: JWST DDT 6555
- Related: PHANGS-JWST
- Related: PHANGS-ALMA

## Checks

```json
{
 "quotes": 180,
 "quotes_ok": 180,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 19,
 "numeric_problems": 0,
 "fill": {
  "facts": 147,
  "stated": 97,
  "rate": 0.66
 },
 "evidence_ok": true
}
```
