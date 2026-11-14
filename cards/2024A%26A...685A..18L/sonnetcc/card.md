# Forming localized dust concentrations in a dust ring: DM Tau case study. The asymmetric 7 mm dust continuum of the DM Tau disk

`2024A&A...685A..18L` | Astronomy and Astrophysics 2024 | first author: Liu, Hauyu Baobab | arXiv: 2402.02900 | DOI: 10.1051/0004-6361/202348896

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type multi_facility_alma_minor

## Science

- Fields: protoplanetary_disks
- Question: Examine dust growth and filtration in the outer ring of the transitional disk DM Tau using 7 mm JVLA imaging and an 8-700 GHz SED  
  > "We aim to examine dust growth and filtration in the outer ring of DM Tau." (abstract)
- Target **DM Tau**: coordinates _not stated_; z/distance d ~145 pc  
  > "DM Tau is a 0.53 M$_{\odot}$ star ($d\sim$145 pc; (cite: Gaia_2023))" (Introduction); distance from Gaia (cite: Gaia_2023)  
  > "DM Tau is a 0.53 M$_{\odot}$ star ($d\sim$145 pc; (cite: Gaia_2023))" (Introduction)

## Data provenance

- ALMA projects: 2013.1.00498.S, 2013.1.00647.S, 2015.1.00296.S, 2016.1.00565.S, 2016.1.01042.S, 2017.1.01460.S, 2018.1.01755.S
- bands: ALMA archival Band 3 (~95-111 GHz), Band 4 (~144-159 GHz), Band 9 (~659-676 GHz); JVLA Q, Ku, X (2019) plus archival JVLA; SMA 200-400 GHz  
  > "We retrieved the archival ALMA Band 3 ($\sim$95–111 GHz), Band 4 ($\sim$144–159 GHz), and Band 9 ($\sim$659–676 GHz) observations that the maximum recoverable angular scales (MAS) are larger than 3$''$ for the purpose of deriving the (sub)millimeter SEDs." (Data); "We carried out the JVLA observations towards DM Tau at Q (40–48 GHz), Ku (12–18 GHz), and X (8–12 GHz) bands in 2019." (Data)
- frequencies and spectral setup: Only passbands that detected DM Tau and showed no significant line emission were used for the ALMA SED  
  > "We visually inspected the spectra and only utilized the passbands that detected DM Tau and did not present significant spectral line emission." (Data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: JVLA Q band A, B/BnA and C configurations combined with weights 4, 2, 1  
  > "the A, (B & BnA), and C array configuration observations were re-weighed (by factors of 4, 2, and 1, respectively) to yield a synthesized beam that is approximately Gaussian." (Data and reduction)
- baselines: _not stated_
- angular resolution: JVLA Q band ~0.06'' (~8.7 au); ALMA archival SED data not given in text outside table  
  > "We performed $\sim$0.06$''$ ($\sim$8.7 au) resolution Karl G. Jansky Very Large Array (JVLA) 40–48 GHz ($\sim 7$ mm; Q band) continuum observations" (abstract)
- max recoverable scale: ALMA archival data selected with MAS larger than 3''  
  > "We retrieved the archival ALMA Band 3 ($\sim$95–111 GHz), Band 4 ($\sim$144–159 GHz), and Band 9 ($\sim$659–676 GHz) observations that the maximum recoverable angular scales (MAS) are larger than 3$''$ for the purpose of deriving the (sub)millimeter SEDs." (Data)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: ALMA data are archival; JVLA 40-48 GHz new in 2019 plus archival JVLA since 2010  
  > "We retrieved the archival ALMA Band 3 ($\sim$95–111 GHz), Band 4 ($\sim$144–159 GHz), and Band 9 ($\sim$659–676 GHz) observations that the maximum recoverable angular scales (MAS) are larger than 3$''$ for the purpose of deriving the (sub)millimeter SEDs." (Data); "In addition, we retrieved and analyzed the archival JVLA data which were taken since August 22, 2010." (Data)
- Other facility **JVLA**: New Q (40-48 GHz), Ku and X band observations in 2019 plus archival data (Disk@EVLA AC982, BL175, 13B-364)  
  > "We carried out the JVLA observations towards DM Tau at Q (40–48 GHz), Ku (12–18 GHz), and X (8–12 GHz) bands in 2019." (Data); "Most of those data were taken from the Disk@EVLA project (project code: AC982; PI: C. Chandler)" (Data)
- Other facility **SMA**: 200-400 GHz SED point from a Taurus Class II survey  
  > "The present work utilizes the 200–400 GHz SED provided by this SMA survey, which was carefully calibrated." (Data)
- Other facility **Gaia DR3**: Proper motions used to align ALMA and JVLA images, and distance  
  > "we corrected for the proper motions (R.A.: 11.788 mas yr$^{-1}$ and Decl.: $-$18.361 mas yr$^{-1}$) quoted from the Gaia Data Release 3 (cite: Gaia_2023)" (Data)
- External data: High-angular-resolution ALMA 216-233 GHz images of DM Tau used to reference JVLA features  
  > "we utilized the high-angular-resolution ALMA 216–233 GHz images towards DM Tau, which were detailed in (cite: Kudo2018ApJ...868L...5K)" (Data) [from (cite: Kudo2018ApJ...868L...5K); c.f. (cite: Hashimoto2021ApJ...911....5H)]
- External data: JVLA Ku and X band 2019 observations (free-free emission)  
  > "The Ku and X bands observations which mainly traced free-free emission have been reported elsewhere (cite: Terada2023ApJ...953..147T)." (Data) [from (cite: Terada2023ApJ...953..147T)]
- External data: 2013 X-band JVLA project 13B-364 data (8-10 GHz non-detection)  
  > "project 13B-364 (PI: L. F. Rodriguez; (cite: Zapata2017ApJ...834..138Z))" (Data) [from (cite: Zapata2017ApJ...834..138Z)]
- External data: 200-400 GHz SMA SED and spectral index from unpublished survey  
  > "The full survey will be reported in an upcoming paper (Chung et al. submitted)." (Data) [from Chung et al. submitted]
- External data: Default DSHARP size-dependent dust opacity tables  
  > "We adopted the formulations and the default DSHARP size-dependent dust opacity tables published in (cite: Birnstiel2018ApJ...869L..45B) for the dust emission component." (Spectral index distribution and model) [from (cite: Birnstiel2018ApJ...869L..45B)]
- External data: Inclination 35.2 deg and position angle 157.8 deg used to deproject visibilities  
  > "After deprojecting the data using $i=$35.2$^{\circ}$ and P.A.$=$157.8$^{\circ}$ (cite: Kudo2018ApJ...868L...5K)" (Asymmetry appendix) [from (cite: Kudo2018ApJ...868L...5K)]
- Simulation/model as data: DSHARP compact-grain opacity model (water ice, silicates, troilite, refractory organics) used as the dust emission model  
  > "The default DSHARP opacity table assumes that the dust grains are compact and composed of water ice (cite: Warren1984ApOpt..23.1206W), astronomical silicates (cite: Drain2003ARA&A..41..241D), troilite, and refractory organics" (Spectral index distribution and model)

## Processing

### Calibration

- pipeline or manual: JVLA data calibrated manually in CASA; ALMA calibration not stated  
  > "We manually calibrated the JVLA data following the standard strategy (see details below) using the CASA software package." (JVLA data processing)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA tclean, multi-frequency synthesis nterms=2  
  > "We performed multi-frequency synthesis (nterms$=$2) imaging ((cite: Rau2011A&A...532A..71R)) using the CASA `tclean` task." (JVLA data processing)
- deconvolver: _not stated_
- weighting robust: Briggs Robust = 2.0 for per-epoch images; Robust < 2 gave higher noise  
  > "the achieved synthesized beams and root-mean-square (RMS) noise in the Briggs Robust$=$2.0 weighted images are summarized in Table" (JVLA data processing); "Using Briggs Robust$<2$ weighting (e.g., Robust$=$0, 1) to yield smaller synthesized beams significantly enhanced the thermal noise level" (JVLA data processing)
- uv taper: Various tapering tried when jointly imaging Q band; parameters not given  
  > "We tried jointly imaging some Q band (40–48 GHz) observations using various combinations of observations and tapering." (JVLA data processing)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Q band A, B/BnA, C data re-weighted by 4, 2, 1; fiducial image limited to uv distance >200 klambda  
  > "the A, (B & BnA), and C array configuration observations were re-weighed (by factors of 4, 2, and 1, respectively) to yield a synthesized beam that is approximately Gaussian." (JVLA data processing); "We created the fiducial Q band image by limiting the *uv* distance range to $>$200 $k\lambda$." (JVLA data processing)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: Joint C band 2011 image RMS 5.3 uJy/beam (non-detection)  
  > "which yielded a 5.3 $\mu$Jy beam$^{-1}$ RMS noise" (JVLA data processing)

### Inherited from earlier work

- SED modelling approach with unresolved dust and free-free components  
  > "Therefore, we followed the approach of (cite: Liu2019ApJ...884...97L) to model the integrated flux densities" (SED modeling using MCMC) [from (cite: Liu2019ApJ...884...97L)]
- Multicomponent flux equation  
  > "In our models, the overall flux density is described by (quoting Equation 3 of (cite: Liu2019ApJ...884...97L))" (Spectral index distribution and model) [from (cite: Liu2019ApJ...884...97L)]
- Free-free emission formulation  
  > "we adopted the approximated formulation outlined in (cite: Mezger1967ApJ...147..471M) and (cite: Keto2003ApJ...599.1196K)" (Spectral index distribution and model) [from (cite: Mezger1967ApJ...147..471M); (cite: Keto2003ApJ...599.1196K)]
- JVLA calibration follows the standard strategy  
  > "We manually calibrated the JVLA data following the standard strategy (see details below) using the CASA software package." (JVLA data processing) [from standard strategy (no reference given)]
- Ku and X band JVLA 2019 data reduction  
  > "The Ku and X bands observations which mainly traced free-free emission have been reported elsewhere (cite: Terada2023ApJ...953..147T)." (Data) [from (cite: Terada2023ApJ...953..147T)]
- Size distribution slope q=3.5  
  > "We assumed q=3.5 ((cite: Mathis1977ApJ...217..425M; Doi2023arXiv230816574D))" (Spectral index distribution and model) [from (cite: Mathis1977ApJ...217..425M; Doi2023arXiv230816574D)]
- Calibrated 200-400 GHz SMA flux densities  
  > "The present work utilizes the 200–400 GHz SED provided by this SMA survey, which was carefully calibrated." (Data) [from Chung et al. submitted]

### Not stated but needed to reproduce (our reading)

- How the archival ALMA Band 3, 4 and 9 flux densities were derived (pipeline vs manual, CASA version, flux scale, aperture or fit used, which spectral windows kept)
- Roles of ALMA projects 2013.1.00498.S and 2017.1.01460.S, which are acknowledged but absent from the flux table
- CASA version and JVLA flux/gain calibration details beyond the table
- Robust value, uv taper, cell and image size, masking, clean threshold and weights for the fiducial Q-band image
- Aperture used for photometry of the Q-A image and fitting region for 2D Gaussian flux extraction
- SED likelihood form, treatment of absolute flux calibration errors, and exact SMA 200-400 GHz flux densities (unpublished)
- Initial parameter values are tabulated but MCMC convergence diagnostics are not given
- Exact deprojected visibility moment code and error treatment for the Bessel-function fit (to be published separately)

## Analysis recipe

1. **Calibrate JVLA data**: Manual CASA calibration: delay, bandpass and complex gain with absolute flux scaling  
  > "we bootstrapped delay fitting and passband calibrations, and then performed a complex gain calibration." (JVLA data processing)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Image JVLA Q band and align with ALMA**: tclean mtmfs imaging, joint imaging of epochs with re-weighting, fiducial uv>200 klambda; proper motion correction with fixplanets  
  > "We performed multi-frequency synthesis (nterms$=$2) imaging ((cite: Rau2011A&A...532A..71R)) using the CASA `tclean` task." (JVLA data processing); "using the `fixplanets` task of the Common Astronomy Software Applications (CASA; (cite: McMullin2007ASPC..376..127M)) software package" (Data)
   - software: CASA, tclean, fixplanets
   - parameter: Briggs Robust = 2.0 for per-epoch images  
  > "the achieved synthesized beams and root-mean-square (RMS) noise in the Briggs Robust$=$2.0 weighted images are summarized in Table" (JVLA data processing)
   - fitting: _not stated_
   - validation: Compared Q-A, Q-B, Q-AB and Q-all images to check consistency of features  
  > "The consistency between these JVLA images is hard to explain if the resolved features were spuriously created due to thermal noise or imaging artifacts." (Results)
3. **Test azimuthal asymmetry in visibilities**: Deproject visibilities, bin in 50 radial uv bins, compute m=0 and m=1 moments, compare with Bessel functions  
  > "the $uv$-plane is divided into 50 radial bins having similar data weights." (Asymmetry appendix); "We performed a model-independent assessment of the azimuthal asymmetry at Q band by examining the dipole ($m=1$) moments of the B and BnA configuration visibility amplitudes" (Results)
   - parameter: Data averaged over all spectral windows and 30 s  
  > "we average the data over all the spectral windows in 40–43 GHz band and the integration over 30 s to improve the S/N and reduce the data size" (Asymmetry appendix)
   - assumption: Inclination 35.2 deg, P.A. 157.8 deg from Kudo et al.  
  > "After deprojecting the data using $i=$35.2$^{\circ}$ and P.A.$=$157.8$^{\circ}$ (cite: Kudo2018ApJ...868L...5K)" (Asymmetry appendix)
   - fitting: 0th-order Bessel function fit to the m=0 moment; dipole not robustly fit  
  > "Owing to the high noise, and due to the fact that the noise in the visibility amplitudes is positively biased, we are unable to robustly fit the dipole moments with a Bessel function." (Results)
   - validation: Checked that deconvolution does not affect the moments  
  > "For our dataset, we have checked that deconvolution does not affect our results and therefore, we present the analyses without deconvolution in this paper." (Asymmetry appendix)
4. **Measure SED flux densities**: Aperture photometry for 2019 Q-A image; 2D Gaussian fits for other observations  
  > "We measured the 40–48 GHz flux density in 2019 from the Q-A image using aperture photometry." (Results); "The flux densities of the other observations were extracted using two-dimensional (2D) Gaussian fittings." (Results)
   - fitting: _not stated_
   - validation: _not stated_
5. **Assess free-free contamination at Q band**: Compare Q-fiducial knots with X and Ku band free-free morphology and intensity, scaled with spectral index -0.1 to 0  
  > "we based on the morphology resolved in the Q-fiducial image and the intensity of free-free emission resolved in the previous X band (8–12 GHz) and Ku band (12–18 GHz) observations" (Free-free contamination appendix)
   - assumption: Free-free optically thin above 10 GHz with spectral index in the range -0.1 to 0  
  > "the free-free emission likely becomes optically thin at $>$10 GHz frequency" (Free-free contamination appendix)
   - fitting: _not stated_
   - validation: _not stated_
6. **Fit two-dust plus free-free SED model**: Unresolved multicomponent SED model (small dust, grown dust, free-free) fit with MCMC  
  > "The free parameters of these components were optimized using the Markov chain Monte Carlo (MCMC) method" (Spectral index distribution and model)
   - software: emcee
   - parameter: 250 samplers, 5e5 iterations, first 1e4 discarded as burn-in  
  > "We used 250 samplers." (SED modeling using MCMC); "We advanced the positions of the samplers for 5$\times$10$^{5}$ iterations, discarding the first 10$^{4}$ iterations as the burn-in steps." (SED modeling using MCMC)
   - parameter: Flat linear priors centered on initial guesses, bounded by 10 and 0.1 times the guesses  
  > "These flat probability distributions are centered at our initial guesses and are upper and lower bounded by 10 and 0.1 times the initial guesses." (SED modeling using MCMC)
   - assumption: DSHARP opacities, power-law grain size distribution with q=3.5 and a_min=1e-4 mm  
  > "We assumed q=3.5 ((cite: Mathis1977ApJ...217..425M; Doi2023arXiv230816574D)) and nominally fixed the value of $a_{\mbox{\scriptsize min}}$ to $10^{-4}$ mm" (Spectral index distribution and model)
   - assumption: Uniform physical properties within each component; spatially unresolved source  
  > "we assumed that the physical properties within each component are uniform" (SED modeling using MCMC)
   - assumption: Electron temperature fixed to 8000 K  
  > "We nominally fixed $T_{\mbox{\scriptsize e}}$ to 8,000 K which is typical for ionized gas." (SED modeling using MCMC)
   - fitting: emcee; best fit = 50th percentile; log likelihood set to -inf if model exceeds 2019 Q flux or falls below lowest 2012 41-43 GHz flux; X and Ku errors set equal to flux  
  > "Setting the log likelihood to negative infinity when the model flux densities are (i) higher than the observed flux densities at 40–48 GHz in 2019, (ii) lower than the lowest observed 41–43 GHz flux density in 2012." (SED modeling using MCMC); "We regarded the parameters represented by the 50th percentile of the MCMC samples as the best-fit parameters." (Spectral index distribution and model); "artificially setting the RMS errors (1-$\sigma$) of the X and Ku bands measurements to be identical to the observed flux densities" (SED modeling using MCMC)
   - validation: _not stated_
7. **Compare with single-dust-component fit**: Same MCMC approach with only one dust component  
  > "we also tried fitting the observed SED with only one dust component" (Spectral index distribution and model)
   - software: emcee
   - fitting: Same MCMC approach as the two-component model  
  > "Using a similar approach as what was introduced in Appendix Section" (Single dust component model)
   - validation: Single-component model reproduces the 90-700 GHz data less closely; authors note goodness-of-fit ambiguity  
  > "It is difficult to objectively determine which model is better." (Single dust component model)

## Software

- **CASA** : JVLA calibration, tclean imaging and fixplanets proper-motion correction  
  > "We manually calibrated the JVLA data following the standard strategy (see details below) using the CASA software package." (JVLA data processing)
- **tclean** : Multi-frequency synthesis imaging (nterms=2)  
  > "We performed multi-frequency synthesis (nterms$=$2) imaging ((cite: Rau2011A&A...532A..71R)) using the CASA `tclean` task." (JVLA data processing)
- **fixplanets** : Correcting proper motions before comparing ALMA and JVLA images  
  > "using the `fixplanets` task of the Common Astronomy Software Applications (CASA; (cite: McMullin2007ASPC..376..127M)) software package" (Data)
- **emcee** : MCMC optimisation of the SED model  
  > "We optimized the free parameters in our model using the MCMC method, which was implemented with the `emcee` software package." (SED modeling using MCMC)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| C band 2011 joint image RMS | 5.3 | not stated | uJy/beam | 2 | which yielded a 5.3 $\mu$Jy beam$^{-1}$ RMS noise |
| Ring radius from m=0 visibility zero crossing (~500 klambda) | ~0.15'' (~23 au) | not stated | arcsec | 3 | It crosses zero at $\sim$500 k$\lambda$ *uv*-distance, which corresponds to a $\sim$0.15$''$ ($\sim$23 au) ring radius. |
| Ring radius from Bessel fit to m=0 moment | ~0.16'' (~23 au) | not stated | arcsec | 3 | indicates that the radius of the ring is $\sim$0.16$''$ ($\sim$23 au) which agrees with the $\sim$25 au ring seen in the ALMA image. |
| Peak of m=1 dipole signal | ~600 klambda (signals at 500-1000 klambda) | not stated | klambda | 3 | it is still possible to visually identify weakly enhanced signals (with respect to pure noise) at 500–1000 k$\lambda$ with a peak at $\sim$600 k$\lambda$. |
| Brightest southern knot flux in Q-fiducial image | ~60 | not stated | uJy | 2 | the brightest knot in the south ($\sim$ 60 $\mu$Jy) may be at least 100% brighter than the opposite side of the ring |
| Knot detection significance in Q-fiducial image | ~3-6 sigma | not stated | dimensionless | 2 | several knots are detected at $\sim$3–6$\sigma$ level in east to south within the 25 au ring |
| Peak intensity upper limit of brightest free-free knot at Q band | <~30 | not stated | uJy/beam | 5 | the intensity of the brightest free-free emission knot will have a $\lesssim$30 $\mu$Jy beam$^{-1}$ peak intensity |
| Time-smeared free-free flux after combining three A-config epochs | <~9 | not stated | uJy/beam | 5 | the flux density of the time-smeared free-free emission will become $\lesssim$9 $\mu$Jy beam$^{-1}$ |
| Spectral index between 400 and 659 GHz | ~0.5 | not stated | dimensionless | 4 | The directly measured spectral index between 400 GHz and 659 GHz was only $\sim$0.5. |
| Small dust temperature (two-component MCMC) | 12.4 | +2.7/-1.7 | K | 6 | 12.4$^{+2.7}_{-1.7}$ |
| Small dust column density | 2.51 | +0.81/-0.56 | g cm^-2 | 6 | 2.51$^{+0.81}_{-0.56}$ |
| Small dust maximum grain size | 0.055 | +0.021/-0.028 | mm | 6 | 0.055$^{+0.021}_{-0.028}$ |
| Small dust mass | 640 | +490/-300 | Earth masses | 6 | 640$^{+490}_{-300}$ |
| Grown dust temperature | 14.5 | +6.1/-4.2 | K | 6 | 14.5$^{+6.1}_{-4.2}$ |
| Grown dust column density | 9.55 | +3.9/-3.7 | g cm^-2 | 6 | 9.55$^{+3.9}_{-3.7}$ |
| Grown dust maximum grain size | 0.306 | +0.195/-0.087 | mm | 6 | 0.306$^{+0.195}_{-0.087}$ |
| Grown dust mass | 840 | +870/-520 | Earth masses | 6 | 840$^{+870}_{-520}$ |
| Free-free emission measure (two-component model) | 4.5e8 | +3.5/-2.8 (x1e8) | cm^-6 pc | 6 | 4.5$^{+3.5}_{-2.8}$$\cdot$10$^{8}$ |
| Total dust mass in best-fit two-component model | 1440 | +1360/-820 | Earth masses | 6 | The overall dust mass in our best-fit model is 1440$^{+1360}_{-820}$ Earth masses ($M_{\oplus}$). |
| Single-component maximum grain size | ~21 | 0.02+/-0.01 mm in table (+0.02/-0.01) | um | 7 | This fitting favors a small $a_{\mbox{\scriptsize max}}$ value of $\sim$21 $\mu$m while it yields a similar overall dust mass as what was given by the two-component fitting |
| Single-component dust mass | 1280 | +80/-100 | Earth masses | 7 | 1280$^{+80}_{-100}$ |

## Qualitative findings

- JVLA 7 mm image resolves azimuthally highly asymmetric knotty dust emission near the inner edge of the outer ring  
  > "Intriguingly, the Q band image resolved the azimuthally highly asymmetric, knotty dust emission sources close to the inner edge of the outer ring." (abstract)
- Q-band knots are more likely dust than free-free emission  
  > "In other words, the $>$3-$\sigma$ sources in our Q-fiducial image more likely trace dust emission instead of free-free emission." (Free-free contamination appendix)
- DM Tau cannot be optically thin at 225 GHz  
  > "Conversely, the large contrast between the morphology resolved at 225 GHz and 40-48 GHz means that DM Tau cannot be optically thin at 225 GHz." (Spectral index distribution and model)

## Claim tuples

- H: Is the outer dust ring of DM Tau azimuthally asymmetric at 7 mm? | E: High-resolution JVLA Q-band imaging combined from several epochs and configurations, plus visibility moment analysis | R: Knots at ~3-6 sigma in the east to south of the ~25 au ring; brightest knot at least 100% brighter than the opposite side; weak dipole signal | F: The ring is highly asymmetric and knotty at 40-48 GHz while only weakly asymmetric at 225 GHz | **supported**
- H: Do the knots and the rest of the ring host different maximum grain sizes? | E: Two-dust-plus-free-free unresolved SED model fitted to 8-700 GHz flux densities with emcee | R: Grown dust a_max ~0.3 mm; small dust a_max below 100 um (best fit 0.055 mm) | F: a_max is likely at least 300 um in the knots and at most 50 um in the rest of the ring | **supported**
- H: Are the 40-48 GHz knots free-free emission rather than dust? | E: Compared Q-band knots with the X and Ku band free-free images and scaled intensities | R: Free-free knots are at most ~30 uJy/beam and mostly inside the cavity, while knots are 50-70 uJy/beam and tied to the ring | F: The >3 sigma Q-band knots are most likely dust emission | **supported**
- H: What produces the azimuthal asymmetry and dust concentration? | E: Discussion of the grain growth, trapping, planet-disk interaction and vortex scenarios in light of the SED and images | R: Grown dust is found at the inner edge of the ring | F: Trapping of inward-migrating grown dust is proposed but the mechanism is not identified | **partially**
- H: Does apparent symmetry of transitional disks depend on optical depth at the observing frequency? | E: Compared DM Tau morphology at 225 GHz and 40-48 GHz | R: Weak asymmetry at 225 GHz and strong asymmetry at 40-48 GHz | F: Asymmetry is difficult to diagnose at 225 GHz or above owing to high optical depth | **partially**

## Reasoning

- Why this data: JVLA is advantageous for probing mm and larger sized dust  
  > "observations of DM Tau, which is advantageous for probing $\gtrsim$1 mm sized dust" (Introduction)
- Why this method: Spatially resolved modelling would be too degenerate, so an unresolved multicomponent SED model is used  
  > "our assessment is that a spatially resolved model would be too degenerated to provide any valid information" (SED modeling using MCMC)
- Alternative: Single-dust-component SED fit (reproduces data less closely)  
  > "we also tried fitting the observed SED with only one dust component" (Spectral index distribution and model)
- Alternative: JVLA epochs D-1 and D-2 omitted for poor image quality and high noise  
  > "owing to the compromised image quality and high RMS noise compared to the other observations taken at proximate time and frequency." (JVLA data processing)
- Alternative: Robust < 2 weighting rejected for raising thermal noise  
  > "Using Briggs Robust$<2$ weighting (e.g., Robust$=$0, 1) to yield smaller synthesized beams significantly enhanced the thermal noise level" (JVLA data processing)
- How they decided it was enough: Used the smallest number of components able to approximate the observed flux densities  
  > "For the sake of robustness, we were restricted to use the smallest possible number of components that can approximate the observed flux densities." (SED modeling using MCMC)
- Limitation (authors): Dipole moments could not be robustly fitted owing to noise  
  > "Owing to the high noise, and due to the fact that the noise in the visibility amplitudes is positively biased, we are unable to robustly fit the dipole moments with a Bessel function." (Results)
- Limitation (authors): Free-free parameters barely constrained owing to variability  
  > "As a consequence of the poorly constrained variability, the free parameters of the free-free emission components were barely constrained" (Spectral index distribution and model)
- Limitation (authors): Dust masses are upper limits for the assumed DSHARP opacities  
  > "Our dust mass estimates may be regarded upper limits, since the default DSHARP dust are not as opaque as those that included graphitic carbons" (Spectral index distribution and model)
- Caveat (inferred, ours): ALMA flux densities are taken from heterogeneous archival data with no stated reduction or flux-scale uncertainty, and the SED is non-simultaneous across 2010-2019 for a variable source
- Caveat (inferred, ours): Two-component model is weakly constrained and results depend on hand-set likelihood constraints and artificial uncertainties for X and Ku bands
- Caveat (inferred, ours): Asymmetry significance relies on ~3-6 sigma knots and a visibility test with positively biased noise
- Caveat (inferred, ours): Spatial association of grown dust with knots is inferred, not fitted

## Reproducibility

- Data public (paper): ALMA and JVLA data are archival (retrieved); SMA survey is unpublished  
  > "In addition, we retrieved and analyzed the archival JVLA data which were taken since August 22, 2010." (Data); "The full survey will be reported in an upcoming paper (Chung et al. submitted)." (Data)
- Products in archive: _not stated_
- Missing: ALMA flux extraction recipe and calibration
- Missing: Q-fiducial imaging parameters (cell, image size, masks, taper)
- Missing: SMA 200-400 GHz fluxes (unpublished)
- Missing: Likelihood details, uncertainty treatment and code for the SED model and visibility moments
- Data volume (inferred): Large: JVLA A-array Q-band measurement sets over several epochs plus archival ALMA Band 3/4/9 data, likely hundreds of GB raw
- Score (inferred): 2/5, Public archival JVLA and ALMA data and key MCMC settings are given, but ALMA flux derivation, fiducial imaging parameters and SMA fluxes are missing and the model code is not released
- Rediscovery candidate: no, The key result is JVLA-based with unspecified imaging parameters, ALMA flux extraction is not described, and part of the SED comes from an unpublished SMA survey

## Links

- Method: (cite: Liu2019ApJ...884...97L) (Unresolved multicomponent SED modelling approach and flux equation)
- Method: (cite: Birnstiel2018ApJ...869L..45B) (DSHARP opacity tables used for the dust model)
- Method: (cite: Kudo2018ApJ...868L...5K) (ALMA 216-233 GHz images and disk geometry used)
- Companion: (cite: Terada2023ApJ...953..147T) (JVLA X and Ku band 2019 observations of free-free emission)
- Companion: (cite: Hashimoto2021ApJ...911....5H) (Higher-resolution ALMA 225 GHz image with weak asymmetry)
- Companion: Chung et al. submitted (SMA 200-400 GHz survey providing the SED point and spectral index)
- Related: Disk@EVLA (AC982)
- Related: Gould's Belt Very Large Array Survey (BL175)
- Related: JVLA project 13B-364
- Related: DSHARP opacity tables

## Checks

```json
{
 "quotes": 119,
 "quotes_ok": 119,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 7,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 21,
 "numeric_problems": 0,
 "fill": {
  "facts": 103,
  "stated": 71,
  "rate": 0.689
 },
 "evidence_ok": true
}
```
