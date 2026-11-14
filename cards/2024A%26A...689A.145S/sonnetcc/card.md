# The ALMA-CRISTAL survey: Discovery of a 15 kpc-long gas plume in a z = 4.54 Lyman-α blob

`2024A&A...689A.145S` | Astronomy and Astrophysics 2024 | first author: Solimano, M. | arXiv: 2401.04919 | DOI: 10.1051/0004-6361/202449192

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What caused the [C ii] plume in the J1000+0234 system (outflow, inflow, ram pressure stripping or tidal interaction)  
  > "The main question we want to answer in this paper is what caused the \[C ii\] plume in the J1000+0234 system." (5 Discussion)
- Target **J1000+0234 system (J1000+0234-North / the DSFG, and CRISTAL-01a)**: coordinates _not stated_; z/distance z = 4.54  
  > "In this paper, we study the core region of the J1000+0234 system at $z=4.54$, first reported by (cite: Capak2008ExtremeStarburst) as a bright sub-millimeter source with an associated Ly$\alpha$ blob." (2 The J1000+0234 system); "1 ″ corresponds to 6.57   of proper physical scale at $z=4.54$." (1 Introduction); distance from flat LambdaCDM, H0 = 70 km/s/Mpc, Omega_m = 0.3 (proper scale at z = 4.54)  
  > "In this paper, we study the core region of the J1000+0234 system at $z=4.54$, first reported by (cite: Capak2008ExtremeStarburst) as a bright sub-millimeter source with an associated Ly$\alpha$ blob." (2 The J1000+0234 system); "1 ″ corresponds to 6.57   of proper physical scale at $z=4.54$." (1 Introduction)
- Target **CRISTAL-01a**: coordinates _not stated_; z/distance z = 4.5537  
  > "A successful detection of the line provided the first systemic redshift of this source at $z=4.5537$ (cite: Bethermin2020DataProcessing)" (2 The J1000+0234 system); distance from [C ii] systemic redshift from ALPINE (cite: Bethermin2020DataProcessing)  
  > "A successful detection of the line provided the first systemic redshift of this source at $z=4.5537$ (cite: Bethermin2020DataProcessing)" (2 The J1000+0234 system)

## Data provenance

- ALMA projects: 2017.1.00428.L, 2021.1.00280.L, 2019.1.01587.S, 2012.1.00978.S
- bands: Band 7  
  > "We have presented new ALMA Band 7 observations of the inner region of the J1000+0234 system at $z=4.54$" (6 Summary & conclusions)
- frequencies and spectral setup: ALPINE tuned to the [C ii] line at 349.1 GHz, 40 km/s velocity resolution; CRISTAL 10 km/s per channel; 2019.1.01587.S spectral windows tuned around the DSFG rest-frame velocity, only partial overlap (red half of CRISTAL-01a's line)  
  > "tuned to cover the line at 349.1 GHz with a velocity resolution of 40 km s^−1^" (3.1 ALMA); "and with a higher spectral resolution (10 km s^−1^ per channel) than that of the ALPINE data." (3.1 ALMA); "the spectral windows were tuned around the DSFG’s rest-frame velocity, so the frequency overlap with previous data is partial" (3.1 ALMA)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: ALPINE: C43-1; CRISTAL: C43-1 and C43-4; 2019.1.01587.S: C43-6  
  > "The ALPINE observations were carried out with the most compact configuration (C43-1)" (3.1 ALMA); "include deeper integrations in two antenna configurations, namely C43-1 and C43-4" (3.1 ALMA); "the 2019.1.01587.S dataset was observed using a longer baseline configuration (C43-6)" (3.1 ALMA)
- baselines: _not stated_
- angular resolution: CRISTAL designed for ~0.25″ beam (1.65 kpc at z = 4.54); ALPINE natural-weighting beam 1.25″ x 0.78″; 2019.1.01587.S nominal 0.06″; Briggs robust=0.5 synthesized beam 0.25″ x 0.23″  
  > "These observations were designed to resolve the \[C ii\] emission with a beam of $\sim$0.25 ″, equivalent to 1.65   at $z = 4.54$." (3.1 ALMA); "providing a nominal resolution of 0.06″" (3.1 ALMA); "With this weighting, the synthesized beam ($\ang{;;0.25}\times\ang{;;0.23}$) fits comfortably within each aperture, making them independent." (4.3 Spectral properties of the [C II]-emitting plume)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Combines ALPINE, CRISTAL (Herrera-Camus et al. in prep.) and archival project 2019.1.01587.S (PI: F. Lelli)  
  > "from three different programs, namely the ALPINE survey (cite: LeFevre2020AlpineSurveyDesign), the CRISTAL survey (Herrera-Camus et al. in prep.), and an archival dataset from project 2019.1.01587.S (PI: F. Lelli)" (3.1 ALMA)
- Line: C+ [C ii] 158 μm (redshifted) (not stated)
- Other facility **VLT/MUSE**: Archival IFU cube of the Ly-alpha blob (16 exposures of 900 s, 4 h total; ESO programs 0102.A-0448 and 0103.A-0272), used for Ly-alpha morphology  
  > "These observations, comprising 16 exposures of 900 s (total 4 h), were taken as part of ESO GTO programs 0102.A-0448 (PI: S. Lilly) and 0103.A-0272 (PI: S. Cantalupo)" (3.2 MUSE)
- Other facility **HST**: ACS/F606W, ACS/F814W, WFC3/F105W, F125W, F160W imaging (plus F140W in the stack) from MAST; used for rest-frame UV morphology and a WFC3-IR stack  
  > "We found observations in the ACS/F606W, ACS/F814W, WFC3/F105W, WFC3/F125W and WFC3/F160W bands" (3.3 HST); "In this section we present the stack of HST imaging in the F105W, F125W, F140W and F160W filters." (8 Stack of HST images)
- Other facility **Gaia DR2**: Astrometric reference for MUSE and HST alignment  
  > "we apply a simple 2D translation to the WCS to match the positions of the two Gaia DR2" (3.2 MUSE)
- External data: Global properties of the DSFG and CRISTAL-01a in Table 1 (redshift, stellar mass, dynamical mass, UV slope, SFRs)  
  > "The global properties of each galaxy are extracted from the literature and listed in Table [1](#tab:glob_tab)." (2 The J1000+0234 system) [from References 1-3 of Table 1 (not named in the text)]
- External data: Chandra X-ray luminosity upper limit of the DSFG, used for the AGN bolometric luminosity estimate  
  > "Recalling that the X-ray luminosity of the DSFG is $L_\mathrm{2-10keV} < \SI{1.3e43}{\erg\per\second}$ (cite: Smolcic2015PhysicalPropertiesSmgsCosmos)" (5.1 Conical outflow) [from (cite: Smolcic2015PhysicalPropertiesSmgsCosmos)]
- External data: Virial mass, virial radius, gas reservoir and rotation velocity of the DSFG  
  > "Following the estimation of (cite: Fraternali2021FastRotators) for the J1000+0234 system, we assume a virial mass of $M_\mathrm{vir}=\SI{2e12}{M\ensuremath{_\odot}}$" (5.2 Gas accretion); "the DSFG has a maximum rotation velocity of 550 km s^−1^ at a radius of 3.5   (cite: Fraternali2021FastRotators)" (5.4 Gravitational interactions) [from (cite: Fraternali2021FastRotators)]
- External data: Previously published centers and effective radius used as Gaussian priors for the DSFG Sersic fit  
  > "we adopted broad Gaussian priors centered on previously published values (cite: Fraternali2021FastRotators)" (4.2 Parametric morphology) [from (cite: Fraternali2021FastRotators)]
- External data: Conversion factor kappa_[CII] = 1.5 Msun/Lsun for maximal excitation and solar abundance  
  > "Following (cite: HerreraCamus2021OutflowHZ4), we assume the collisions are dominated by atomic hydrogen" (5.1 Conical outflow) [from (cite: HerreraCamus2021OutflowHZ4)]
- External data: Cold-stream inflow velocity V_stream ~ 0.9 V_vir for halos at z ~ 4  
  > "found that halos of similar mass at $z \sim 4$ accrete at $V_\mathrm{stream}\approx 0.9 V_\mathrm{vir}$" (5.2 Gas accretion) [from (cite: GoerdtAndCeverino2015InflowVelocitiesColdStreams)]

## Processing

### Calibration

- pipeline or manual: Self-calibrated and combined measurement sets processed with the CRISTAL reduction pipeline (Herrera-Camus et al. in prep.)  
  > "the self-calibrated and combined measurement sets were processed with CRISTAL’s reduction pipeline as described in Herrera-Camus et al. (in prep.)" (3.1 ALMA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Two phase-only rounds per observation on ALPINE and CRISTAL continuum visibilities before combination: first combining spectral windows and scans, second only scans; ~11% decrease in continuum rms  
  > "we performed self-calibration on the continuum visibilities of both ALPINE and CRISTAL datasets before combination" (3.1 ALMA); "This was done in two “phase-only” rounds for each observation" (3.1 ALMA); "This process resulted in a $\approx$11% decrease in continuum rms" (3.1 ALMA)

### Imaging

- task: CASA tclean with automasking, run multiple times to make cubes with different weightings and channel widths; CASA used to combine the observations  
  > "automasking multiple times, producing cubes with different weightings and channel widths" (3.1 ALMA); "We use CASA (cite: CasaTeam2022CasaRefPaper) to combine ALMA observations" (3.1 ALMA)
- deconvolver: _not stated_
- weighting robust: Natural or Briggs robust = 0.5; 20 km/s channels  
  > "we use datacubes with 20 km s^−1^ channel width and either natural or Briggs" (3.1 ALMA); "We extract the spectra from the Briggs-weighted (robust=0.5) datacube without continuum subtraction." (4.3 Spectral properties of the [C II]-emitting plume)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Visibility-space continuum subtraction with CASA uvcontsub in the pipeline (line-free channels not stated)  
  > "it starts by subtracting the continuum on the visibility space using CASA’s" (3.1 ALMA)
- line free channels: _not stated_
- primary beam correction: Applied to the FIR luminosity limits (primary beam gain decrement)  
  > "After correcting for primary beam gain decrement, we quote the resulting limits in Table" (4.3 Spectral properties of the [C II]-emitting plume)
- array combination: Multi-configuration data combined; JvM correction measured and applied per channel range with similar beam properties, following Czekala et al. 2021; mean factor epsilon ~ 0.37 (Briggs) and ~ 0.31 (natural) in the [C ii] channels  
  > "Since the data combines different array configurations, it is important to measure and apply the “JvM” correction" (3.1 ALMA); "we compute and apply the correction in channel ranges with similar beam properties" (3.1 ALMA); "We find a mean multiplicative correction factor of $\epsilon\approx 0.37$ in the channels covering the \[C ii\] line emission when using Briggs weighting, and $\epsilon\approx0.31$ when using natural weighting." (3.1 ALMA)
- smoothing: _not stated_
- final beam: 0.25″ x 0.23″ (Briggs robust=0.5)  
  > "With this weighting, the synthesized beam ($\ang{;;0.25}\times\ang{;;0.23}$) fits comfortably within each aperture, making them independent." (4.3 Spectral properties of the [C II]-emitting plume)
- final rms: _not stated_

### Inherited from earlier work

- CRISTAL reduction pipeline (uvcontsub, tclean automasking, cube production)  
  > "processed with CRISTAL’s reduction pipeline as described in Herrera-Camus et al. (in prep.)" (3.1 ALMA) [from Herrera-Camus et al. in prep.]
- ALPINE observation setup and natural-weighting beam  
  > "a natural weighting beam size of $\SI{1.25}{\arcsecond}\times\SI{0.78}{\arcsecond}$ (cite: Bethermin2020DataProcessing)" (3.1 ALMA) [from (cite: Bethermin2020DataProcessing)]
- JvM correction method  
  > "We do this by following the method of (cite: Czekala2021JvMGuidelines)." (3.1 ALMA) [from (cite: Czekala2021JvMGuidelines)]
- MUSE variance-cube scaling to match observed noise levels  
  > "We then follow the steps described in (cite: Solimano2022LymanAlphaSGASJ1226) to scale the variance cube and match the observed noise levels." (3.2 MUSE) [from (cite: Solimano2022LymanAlphaSGASJ1226)]
- MUSE reduction details of the earlier independent reduction  
  > "Here we use an independent reduction from that of , but we refer the reader to their work for further details about the observations." (3.2 MUSE) [from Jimenez-Andrade et al. 2023 (reference marker missing in the text)]
- Matched-filter template (point-like source with Gaussian spectral profile) following LSDCAT  
  > "Following (cite: Herenz2017LsdCat) we built our template as a point-like source with a Gaussian spectral profile of $\mathrm{FWHM}=\SI{250}{\kilo\meter\per\second}$" (4.1 Adaptive masking of datacubes) [from (cite: Herenz2017LsdCat)]
- Noise covariance matrix estimated in source-free regions  
  > "The covariance matrix is estimated in source-free regions of the image using the method and the code[^3] presented by (cite: Tsukui2022CorrelatedNoiseInterferometry)." (4.2 Parametric morphology) [from (cite: Tsukui2022CorrelatedNoiseInterferometry)]
- Sersic index prior centered at n = 1 based on a disk characterization of the DSFG  
  > "based on previous work that characterized this source as a disk (cite: Jones2017DynamicsTiltedRingSmgs), we adopt a Gaussian prior for the Sérsic index centered at $n=1$" (4.2 Parametric morphology) [from (cite: Jones2017DynamicsTiltedRingSmgs)]
- Maximum outflow velocity prescription v_out = |dv| + 2 sigma_broad  
  > "For the maximum outflow velocity we use the prescription of (cite: Genzel2011SinsSurvey)" (5.1 Conical outflow) [from (cite: Genzel2011SinsSurvey)]
- Local Sigma_[CII]-Sigma_SFR relation used to interpret the surface brightness  
  > "according to the local $\Sigma_\mathrm{[CII]}-\Sigma_\mathrm{SFR}$ relation (cite: HerreraCamus2015CiiAsSfrTracerKingFish)" (4.1 Adaptive masking of datacubes) [from (cite: HerreraCamus2015CiiAsSfrTracerKingFish)]

### Not stated but needed to reproduce (our reading)

- CASA version used for combination, self-calibration, tclean and uvcontsub
- The CRISTAL pipeline settings (line-free channels for uvcontsub, tclean masking parameters, cell size, image size, niter and threshold detail, restoring beam) are deferred to an in-preparation paper
- Self-calibration solution intervals, reference antenna and solution tables beyond 'two phase-only rounds'
- Relative weighting applied when combining the ALPINE, CRISTAL and 2019.1.01587.S datasets and the continuum channel selection
- Per-channel-range JvM factors beyond the mean values
- Custom script for the [C ii] adaptive mask is not described in enough detail to rebuild identically (kernel widths are given, rms measurement region is not)
- Priors for the CRISTAL-01a two-component fit ('broad uniform or Gaussian priors') are not listed
- Width of the Gaussian priors for the DSFG centers and effective radius
- Placement and exact geometry of the six plume apertures (centers, position angle 14 deg east of north is given)
- Observing dates, on-source times and achieved sensitivities of each ALMA execution

## Analysis recipe

1. **Self-calibrate, combine and image the three ALMA datasets**: Self-calibrate ALPINE and CRISTAL continuum visibilities, combine with the archival data, then run the CRISTAL pipeline (uvcontsub and tclean with automasking) to make cubes  
  > "we performed self-calibration on the continuum visibilities of both ALPINE and CRISTAL datasets before combination" (3.1 ALMA); "In this paper, we use datacubes with 20 km s^−1^ channel width and either natural or Briggs" (3.1 ALMA)
   - software: CASA, tclean, uvcontsub
   - parameter: Two phase-only self-calibration rounds per observation; 20 km/s channels; natural or Briggs robust = 0.5 weighting; cleaned down to 1 sigma  
  > "This was done in two “phase-only” rounds for each observation" (3.1 ALMA); "In all cases the data are cleaned down to $1\sigma$." (3.1 ALMA)
   - fitting: _not stated_
   - validation: ~11% decrease in continuum rms and mitigation of patchy noise patterns after self-calibration  
  > "This process resulted in a $\approx$11% decrease in continuum rms and the mitigation of patchy patterns in the noise." (3.1 ALMA)
2. **Apply the JvM correction to the multi-array cubes**: Measure and apply the JvM correction per channel range with similar beam properties, following Czekala et al. 2021, instead of the pipeline's single factor per spectral window  
  > "While the CRISTAL pipeline provides JvM-corrected products, it uses a single correction factor per spectral window." (3.1 ALMA); "we compute and apply the correction in channel ranges with similar beam properties" (3.1 ALMA)
   - software: CASA
   - parameter: Mean epsilon ~ 0.37 (Briggs) and ~ 0.31 (natural) in the [C ii] channels  
  > "We find a mean multiplicative correction factor of $\epsilon\approx 0.37$ in the channels covering the \[C ii\] line emission when using Briggs weighting, and $\epsilon\approx0.31$ when using natural weighting." (3.1 ALMA)
   - fitting: _not stated_
   - validation: _not stated_
3. **Build adaptive 3D masks and moment maps (Ly-alpha from MUSE, [C ii] from ALMA)**: Matched-filter style 3D masking: LSDCAT on the MUSE cube; a custom script on the ALMA cube (smooth, threshold at 2 x rms, then CASA immoments on the original cube)  
  > "For the MUSE data, we used the off-the-shelf software LSDCAT (cite: Herenz2017LsdCat), while for the ALMA cubes we used a custom script." (4.1 Adaptive masking of datacubes); "Finally, we split cells above and below a $2\times\mathrm{rms}$ threshold into a 3D mask, which we then fed to CASA task" (4.1 Adaptive masking of datacubes)
   - software: LSDCAT, CASA, immoments
   - parameter: ALMA: naturally-weighted cube in 20 km/s channels smoothed with a sigma = 30 km/s spectral Gaussian and a sigma = 0.1″ spatial Gaussian, rms measured in signal-free regions, 2 x rms threshold  
  > "we convolved with a $\sigma=\SI{30}{\kilo\meter\per\second}$ Gaussian kernel along the velocity axis, and a $\sigma=\ang{;;0.1}$ 2D Gaussian kernel in the spatial axes" (4.1 Adaptive masking of datacubes)
   - parameter: MUSE: 250 km/s FWHM template, S/N >= 2 between 6729 and 6776 Angstrom, spaxels with fewer than three voxels above threshold excluded, regions under 55 connected spaxels pruned  
  > "Finally, we selected all voxels with $\mathrm{S/N}\geq 2$ between 6729 Å and 6776 Å" (4.1 Adaptive masking of datacubes); "prune the regions with less than 55 connected spaxels" (4.1 Adaptive masking of datacubes)
   - fitting: _not stated_
   - validation: 55-spaxel pruning chosen because it masks remaining spurious signal; the plume is also seen in individual channels  
  > "We find that this number successfully masks any remaining spurious signal." (4.1 Adaptive masking of datacubes); "this elongated diffuse emission was already apparent in the individual channels of our cubes" (4.1 Adaptive masking of datacubes)
4. **Fit Sersic profiles to the DSFG dust continuum and [C ii] maps**: Image-plane 2D Sersic fit with PyAutoGalaxy/PyAutoFit, full noise covariance matrix in the likelihood, on unmasked intensity maps; two independent fits (160 um continuum and [C ii])  
  > "We account for the noise correlation in the images by feeding the full covariance matrix into the calculation of the likelihood." (4.2 Parametric morphology); "We performed two independent fits." (4.2 Parametric morphology)
   - software: PyAutoGalaxy, PyAutoFit, dynesty, ESSENCE
   - parameter: [C ii] map integrated between 342.293 GHz and 344.006 GHz (1492.7 km/s)  
  > "we integrated between 342.293 GHz and 344.006 GHz, corresponding to a bandwidth of 1492.7 km s^−1^" (4.2 Parametric morphology)
   - parameter: Seven free parameters; priors: broad Gaussian on center and effective radius, uniform intensity 0 to image maximum, Gaussian Sersic index (mean 1, sigma 1) limited to 0.2-10  
  > "we choose to fit a single 2D Sérsic profile (cite: Sersic1968AtlasdeGalaxias), with a total of seven free parameters." (4.2 Parametric morphology); "but allowed $n$ to vary between 0.2 and 10" (4.2 Parametric morphology)
   - assumption: Dust and gas have disk-like geometries, share the same inclination and are optically thin (for the axis-ratio comparison)  
  > "Assuming instead that the dust and gas both have disk-like geometries, share the same inclination, and are optically thin" (4.2 Parametric morphology)
   - fitting: dynesty nested sampler via PyAutoFit with 50 live points  
  > "The parameter space was explored using the DYNESTY (cite: Speagle2020Dynesty; Koposov2022DynestyZenodoV203) nested sampler backend with 50 live points." (4.2 Parametric morphology)
   - validation: Residual maps inspected; the authors refrain from claiming the gas is more extended than the dust because Sersic indices and S/N differ  
  > "we refrain from claiming the gas is more extended than the dust" (4.2 Parametric morphology)
5. **Fit the two [C ii] clumps of CRISTAL-01a**: Two-component model: elliptical 2D Sersic (SW clump) plus circular Gaussian (NE clump), 11 free parameters, on an unmasked intensity map; continuum not detected  
  > "We thus model the emission with two independent profiles, an elliptical 2D Sérsic for the brighter component (hereafter SW clump) and a circular Gaussian profile for the fainter component (hereafter NE clump)." (4.2 Parametric morphology); "This model has a total of 11 free parameters." (4.2 Parametric morphology)
   - software: PyAutoGalaxy, PyAutoFit, dynesty
   - parameter: Map integrated between 342.088 GHz and 342.454 GHz, which encloses 85% of the line flux  
  > "We construct the unmasked intensity map by integrating the cube between 342.088 GHz and 342.454 GHz, which encloses only 85% of the total line flux" (4.2 Parametric morphology)
   - fitting: Same Sersic-index prior as before for the SW clump; other priors broad uniform or Gaussian (not listed)  
  > "For the rest of the quantities we use either broad uniform or Gaussian priors covering reasonable limits in the parameter space." (4.2 Parametric morphology)
   - validation: 2D residuals shown (Fig. 2)  
  > "The right panel of Fig. [2](#fig:residuals) shows the 2D residuals." (4.2 Parametric morphology)
6. **Extract and fit spectra along the plume in six apertures**: Six adjacent rectangular apertures along the plume (PA 14 deg east of north) on the Briggs robust=0.5 cube without continuum subtraction; single 1D Gaussian per spectrum, first-order polynomial continuum in apertures 1 and 2 with -700 to 0 km/s masked  
  > "we place six adjacent rectangular $\ang{;;0.4}\times\ang{;;0.9}$ apertures covering the full extent of the plume" (4.3 Spectral properties of the [C II]-emitting plume); "We then fit each extracted spectrum independently with a single 1D Gaussian" (4.3 Spectral properties of the [C II]-emitting plume); "In these apertures we also mask emission from −700 km s^−1^ to 0 km s^−1^" (4.3 Spectral properties of the [C II]-emitting plume)
   - software: PyAutoFit, dynesty
   - parameter: Uniform priors: velocity center -200 to 1000 km/s, FWHM 60 to 1000 km/s, total flux 0 to 1.0 Jy km/s  
  > "We adopt uniform priors for the three fitted parameters, namely the velocity center between −200 km s^−1^ and 1000 km s^−1^; the FWHM between 60 and 1000 km s^−1^" (4.3 Spectral properties of the [C II]-emitting plume)
   - parameter: Per-channel (20 km/s) rms from 3-sigma-clipped standard deviation of 300 random apertures of the same size and orientation  
  > "we measure the rms as the $3\sigma-$clipped standard deviation of the flux densities of 300 random apertures with the same size and orientation as the extraction apertures" (4.3 Spectral properties of the [C II]-emitting plume)
   - fitting: PyAutoFit with dynesty static nested sampler, Gaussian likelihood on rms-weighted residuals  
  > "We assume a Gaussian likelihood for the sum of the rms-weighted residuals (data minus model)." (4.3 Spectral properties of the [C II]-emitting plume)
   - validation: Beam fits within each aperture so apertures are independent; systematic uncertainty of aperture #1 tested with a symmetric-difference correction  
  > "making them independent" (4.3 Spectral properties of the [C II]-emitting plume); "These differences illustrate the systematic uncertainties associated with aperture #1, that make flux and FWHM less reliable." (4.3 Spectral properties of the [C II]-emitting plume)
7. **Correct aperture #1 for host contamination (symmetric difference)**: Subtract a velocity-inverted spectrum from the aperture mirrored about the projected rotation axis (cropped to avoid overlap), after shifting and scaling it to match the original peak, then refit the Gaussian  
  > "we subtract a velocity-inverted spectrum from an aperture that mirrors aperture #1 by the projected rotation axis" (4.3 Spectral properties of the [C II]-emitting plume); "We thus shift and scale the mirrored spectrum to match the peak of the original and then perform the subtraction." (8 Symmetric difference correction of aperture #1’s [C ii] spectrum)
   - software: PyAutoFit
   - parameter: Spectra from the robust=0.5, 20 km/s cube without continuum subtraction; first-order polynomial continuum fitted to channels between +/-1330 and +/-1000 km/s; negative velocities down to -700 km/s masked in the fit  
  > "fitting a first-order polynomial to channels between $\pm\SI{1330}{\kilo\meter\per\second}$ and $\pm\SI{1000}{\kilo\meter\per\second}$ independently for each spectrum" (8 Symmetric difference correction of aperture #1’s [C ii] spectrum)
   - assumption: The DSFG rotator is axially symmetric about the projected rotation axis (taken where the second moment is maximal)  
  > "If the DSFG rotator is axially symmetric, we expect any aperture-extracted spectrum from one side of the DSFG to be similar" (8 Symmetric difference correction of aperture #1’s [C ii] spectrum)
   - fitting: 1D Gaussian fit as in step 6  
  > "we fit a 1D Gaussian using PYAUTOFIT" (8 Symmetric difference correction of aperture #1’s [C ii] spectrum)
   - validation: Corrected fit gives lower flux and FWHM with a consistent central velocity  
  > "After this correction, we find both lower fluxes and FWHM, but a consistent central velocity" (4.3 Spectral properties of the [C II]-emitting plume)
8. **Measure transverse width and put limits on FIR luminosity and [C ii]/FIR**: Custom intensity maps per aperture (velocity window 1.1 x best-fit FWHM) with Gaussian fits to 1D spatial profiles for the transverse FWHM; continuum upper limits from 600 random apertures on the robust=0.5 160 um map, converted to L_FIR with a modified blackbody SED  
  > "we create custom intensity maps for each aperture, integrating over a velocity window of size 1.1 times the best-fit spectral FWHM for maximal S/N" (4.3 Spectral properties of the [C II]-emitting plume); "we randomly placed 600 rectangular apertures of size" (4.3 Spectral properties of the [C II]-emitting plume)
   - parameter: 5 sigma detection limit with sigma = 38.8 uJy; T_dust = 45 K, beta_dust = 1.5, nu L_nu(158 um)/L_FIR = 0.185; L_FIR integrated between 42 and 122 um  
  > "Taking $5\sigma$ as the detection limit" (4.3 Spectral properties of the [C II]-emitting plume); "Such an SED gives the ratio $\nu L_\nu(\SI{158}{\micro\meter})/L_\mathrm{FIR} = 0.185$." (4.3 Spectral properties of the [C II]-emitting plume); "Defined as the integral of the rest-frame SED between 42 μm and 122 μm." (Footnote 4)
   - assumption: T_dust = 45 K modified blackbody with beta_dust = 1.5, chosen to roughly describe the average SED of z > 4 star-forming galaxies; limits rise 1.7x and 2.4x for 55 K and 65 K  
  > "a choice that roughly describes the average SED of star-forming galaxies at $z>4$" (4.3 Spectral properties of the [C II]-emitting plume); "produce $1.7\times$ and $2.4\times$ higher $L_\mathrm{FIR}$ limits, respectively" (4.3 Spectral properties of the [C II]-emitting plume)
   - fitting: Gaussian fit to the transverse profiles after beam deconvolution  
  > "We then fit a Gaussian to these profiles to obtain the transversal (spatial) FWHM of the plume." (4.3 Spectral properties of the [C II]-emitting plume)
   - validation: _not stated_
9. **Derive plume gas mass, outflow velocity and mass outflow rates under the outflow hypothesis**: M_out = kappa_[CII] x L_[CII] per aperture; mass outflow rate = M_out x v_out x tan(i) / R with v_out = |dv| + 2 sigma_broad and |dv| = v_cen  
  > "the gas mass in each aperture is $M_\mathrm{out}=\kappa_\mathrm{[CII]}\times L_\mathrm{[CII]}$" (5.1 Conical outflow); "$v_\mathrm{out}=\left|\Delta v\right| + 2\sigma_\mathrm{broad}$" (5.1 Conical outflow); "Since we only detect a single spectral component along the plume, we take $\left|\Delta v\right|=v_\mathrm{cen}$" (5.1 Conical outflow)
   - parameter: kappa_[CII] = 1.5 Msun/Lsun; R = 2.63 kpc (projected aperture short side); mean inclination 57.3 deg  
  > "adopt $\kappa_\mathrm{[CII]}=\SI{1.5}{M\ensuremath{_\odot}\per\lumsol}$" (5.1 Conical outflow); "Assuming $\left<i\right>=\ang{57.3}$" (5.1 Conical outflow)
   - assumption: Optically thin [C ii], negligible background, collisions dominated by atomic hydrogen, maximal excitation (T >> 90 K, n >> 1e3 cm^-3) and solar abundance; masses are lower limits  
  > "In the optically thin limit, and assuming negligible background emission" (5.1 Conical outflow); "the masses we derive will effectively represent lower limits" (5.1 Conical outflow)
   - fitting: _not stated_
   - validation: Compared with starburst SFR scaling and AGN wind scaling relations (Fiore et al. 2017) using L_bol < 1.3e44 erg/s (bolometric correction of 10)  
  > "In summary, our mass outflow rates are consistent with the scaling relations for molecular outflows in both starbursts and AGN." (5.1 Conical outflow)
10. **Test inflow, ram-pressure stripping and tidal scenarios with order-of-magnitude estimates**: Compare the plume velocities, line widths and timescales with predicted cold-stream speeds, the Gunn and Gott ram-pressure criterion and a dynamical age; qualitative discussion of tidal scenarios  
  > "Here we present a qualitative discussion of three different ways this interaction could have happened." (5.4 Gravitational interactions)
   - parameter: Inflow: M_vir = 2e12 Msun and R_vir = 70 kpc give V_vir ~ 350 km/s and V_stream = 0.9 V_vir = 315 km/s  
  > "so for the DSFG we would expect $V_\mathrm{stream}=\SI{315}{\kilo\meter\per\second}$" (5.2 Gas accretion)
   - parameter: RPS: Sigma_gas = 1.6e7 Msun/kpc^2, v_rot = 100 km/s, R_gal = 200 pc, V = 166 km/s give n_CGM >~ 1 cm^-3  
  > "we obtain $n_\mathrm{CGM}=\rho_\mathrm{CGM}/m_{H}\gtrsim\SI{1}{\per\cubic\centi\meter}$" (5.3 Ram pressure stripping)
   - parameter: Dynamical age of the plume: length divided by the velocity difference between its ends, apertures 2-6 only  
  > "To first order, we divide the length of the plume by the velocity difference between its two ends." (5.4 Gravitational interactions)
   - assumption: Average inclination for random viewing angles, <sin i> = 0.79, for de-projection  
  > "Using again the average inclination for a random distribution of viewing angles, $\left<\sin{i}\right>=0.79$" (5.2 Gas accretion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Combining the ALMA observations, self-calibration, uvcontsub, tclean and immoments  
  > "We use CASA (cite: CasaTeam2022CasaRefPaper) to combine ALMA observations" (3.1 ALMA)
- **LSDCAT** : Matched-filter 3D masking of the MUSE cube  
  > "For the MUSE data, we used the off-the-shelf software LSDCAT" (4.1 Adaptive masking of datacubes)
- **PyAutoGalaxy** : 2D light-profile (Sersic) fitting of the DSFG and CRISTAL-01a maps  
  > "we make use of 2D light profile modeling code PYAUTOGALAXY (cite: Nightingale2023PyAutoGalaxy)" (4.2 Parametric morphology)
- **PyAutoFit** : Probabilistic programming framework for the image fits and the plume spectral fits  
  > "Once again, we use PYAUTOFIT with the DYNESTY" (4.3 Spectral properties of the [C II]-emitting plume)
- **dynesty** v2.0.3 (cited Zenodo release): Nested sampler backend (50 live points in the image fits; static nested sampler for the spectra)  
  > "nested sampler backend with 50 live points" (4.2 Parametric morphology)
- **ESSENCE** : Estimating the noise covariance matrix in source-free regions  
  > "ESSENCE, (cite: Tsukui2023Essence)" (Footnote 3)
- **MUSE pipeline with EsoRex** : Standard MUSE calibrations and data reduction  
  > "The standard calibrations and procedures are performed using the MUSE pipeline (cite: Weilbacher2020MUSE_DPP) within the ESO Recipe Execution Tool (EsoRex) environment" (3.2 MUSE)
- **ZAP (Zurich Atmosphere Purge)** : Sky-line residual removal in the MUSE cube  
  > "We then apply the Zurich Atmosphere Purge (cite: Soto2016ZAP) post-processing tool to further remove sky line residuals." (3.2 MUSE)
- **ASTRODRIZZLE / DRIZZLEPAC within GRIZLI** : Drizzling the HST images (square kernel, pixel fraction 0.5; 0.03″ ACS and 0.06″ WFC3/IR pixels)  
  > "All images were then drizzled with a square kernel and a pixel fraction of 0.5 using the ASTRODRIZZLE routine from DRIZZLEPAC" (3.3 HST)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| JvM correction factor, Briggs weighting (mean over [C ii] channels) | 0.37 | not stated | dimensionless | 2 | We find a mean multiplicative correction factor of $\epsilon\approx 0.37$ in the channels covering the \[C ii\] line emission when using Briggs weighting, and $\epsilon\approx0.31$ when using natural weighting. |
| JvM correction factor, natural weighting (mean over [C ii] channels) | 0.31 | not stated | dimensionless | 2 | We find a mean multiplicative correction factor of $\epsilon\approx 0.37$ in the channels covering the \[C ii\] line emission when using Briggs weighting, and $\epsilon\approx0.31$ when using natural weighting. |
| Decrease in continuum rms from self-calibration | ~11 | not stated | percent | 1 | This process resulted in a $\approx$11% decrease in continuum rms |
| DSFG 160 um dust: circularized effective radius | 0.74 | 0.003 (Table 2: 0.740 ± 0.003) | kpc | 4 | dust emisison is fitted by a single 2D Sérsic profile with circularized effective radius of $R_\mathrm{eff}\approx\SI{0.74}{\kilo\parsec}$, Sérsic index $n\approx1.29$ and axis ratio $\approx0.4$ |
| DSFG 160 um dust: Sersic index | 1.29 | 0.01 (Table 2) | dimensionless | 4 | Sérsic index $n\approx1.29$ and axis ratio $\approx0.4$ |
| DSFG [C ii]: circularized effective radius | 1.13 | 0.04 (Table 2: 1.13 ± 0.04) | kpc | 4 | the \[C ii\] emission is fitted by 2D Sérsic profile of $R_\mathrm{eff}\approx\SI{1.13}{\kilo\parsec}$, $n\approx0.7$ and axis ratio $\approx\num{.34}$ |
| DSFG [C ii]: Sersic index | 0.71 | 0.08 (Table 2) | dimensionless | 4 | $n\approx0.7$ and axis ratio $\approx\num{.34}$ |
| Ratio of [C ii] to dust effective radius in the DSFG | ~1.5 | not stated | dimensionless | 4 | The effective radius of the gas component is approximately 1.5 times larger than that of the dust |
| CRISTAL-01a SW clump effective radius and axis ratio | R_eff 2.4, axis ratio 0.82 | 0.4 and 0.09 (Table 3) | kpc (R_eff); dimensionless (axis ratio) | 5 | the southwestern clump with an elliptical exponential of $R_\mathrm{eff}\approx\SI{2.4}{\kilo\parsec}$ and axis ratio $\approx0.82$ |
| CRISTAL-01a NE clump effective radius | 0.8 | 0.3 (Table 3) | kpc | 5 | We model the northeastern clump with a circular exponential profile of $R_\mathrm{eff}\approx\SI{0.8}{\kilo\parsec}$ |
| Projected length of the [C ii] plume | 2.4 arcsec (~15 kpc) | not stated | arcsec | 3 | in a 2.4″-long plume extending north of the DSFG |
| Total [C ii] flux of plume apertures #2 to #6 | 0.50 | 0.04 | Jy km/s (unit not shown in the text) | 6 | Summing apertures from #2 to #6 yields a total flux of 0.50 ± 0.04 |
| [C ii] luminosity of the plume (apertures #2 to #6) | 3.1e8 | 0.25e8 | Lsun (unit not shown in the text) | 6 | amounts to a \[C ii\] luminosity of 3.1 ± 0.25 × 10^8^ |
| Plume central velocity gradient relative to the DSFG systemic velocity | 180 to 400 km/s from the base to the outer end | not stated | km/s | 6 | increasing the line central velocity as a function of radial distance from 180 km s^−1^ to 400 km s^−1^ |
| Plume line FWHM trend | 450 km/s near the DSFG decreasing to 190 km/s at the farthest point | not stated | km/s | 6 | showing a smooth drop from 450 km s^−1^ at the center of the DSFG to 190 km s^−1^ at the farthest measured point |
| Transverse (spatial) FWHM of the plume after beam deconvolution | 0.4 to 0.8 arcsec, average 0.6 arcsec | not stated | arcsec | 8 | we obtain FWHMs between 0.4″ and 0.8″ with an average of 0.6″ |
| Aperture #1 flux and FWHM after symmetric-difference correction | flux ~0.3 Jy km/s, FWHM ~420 km/s | not stated | Jy km/s; km/s | 7 | this fit yields a significantly lower flux ($\approx\SI{0.3}{\jansky\kilo\meter\per\second}$) and FWHM ($\approx\SI{420}{\kilo\meter\per\second}$) |
| Continuum flux-density noise per 0.9 x 0.4 arcsec aperture (sigma-clipped) | 38.8 | not stated | uJy | 8 | We obtain a distribution of flux densities with $\sigma-$clipped standard deviation of $\sigma=\SI{38.8}{\micro\jansky}$. |
| 5-sigma continuum limit on the plume per aperture | 194 | not stated | uJy | 8 | down to $5\sigma=\SI{194}{\micro\jansky}$ per |
| Lower limits on the [C ii]/FIR ratio along the plume (T_dust = 45 K) | ~0.2% (aperture #6) to ~0.6% (aperture #2) | not stated | percent | 8 | we obtain lower limits on the \[C ii\]/FIR ratio between $\approx$0.2% (aperture #6) and $\approx$0.6% (aperture #2) |
| Total minimum gas mass of the plume (kappa_[CII] = 1.5 Msun/Lsun) | 7.1e8 | 0.4e8 | Msun | 9 | The sum of all the apertures gives 7.1 ± 0.4 × 10^8^ |
| Maximum outflow velocity across the plume | 530 to 620 | not stated | km/s | 9 | The maximum outflow velocities across the plume range from 530 km s^−1^ to 620 km s^−1^. |
| Resolved mass outflow rates (Summary; Sec. 5.1 text quotes 15 to 85) | 16 to 83 | not stated | Msun/yr (unit not shown in the text) | 9 | we infer resolved mass outflow rates between 16 M $_\odot$ ^−1^ and 83 M $_\odot$ ^−1^ |
| Conical outflow opening angle | ~15 | not stated | deg | 9 | we estimate $\theta\approx\ang{15}$ |
| Dynamical age of the plume | 115 | not stated | Myr | 10 | $\tau_\mathrm{dyn}=\SI{13.15}{\kilo\parsec}/\SI{112}{\kilo\meter\per\second} = \SI{115}{\mega\year}$ |
| Stacked HST WFC3-IR 5-sigma depth (per square arcsec) | 26.2 | not stated | mag per arcsec^2 (unit not shown in the text) | 0 | obtain a $5\sigma$ depth of 26.2 |

## Qualitative findings

- A faint, diffuse [C ii] plume extends north from the DSFG with a velocity gradient along its long axis and a line width that decreases with distance  
  > "the plume displays a gradient along its long axis, with a mild increase in velocity as one moves away from the DSFG" (4.1 Adaptive masking of datacubes)
- No dust continuum is detected from the plume, and the [C ii]/FIR lower limits do not rule out UV photoelectric heating  
  > "consistent with UV photoelectric heating of the gas" (6 Summary & conclusions)
- The DSFG [C ii] and dust morphologies are slightly different (gas effective radius ~1.5x larger, smaller axis ratio) but the authors do not claim the gas is more extended  
  > "we refrain from claiming the gas is more extended than the dust" (4.2 Parametric morphology)
- The origin of the plume is not settled: outflow, inflow and tidal tail each have pros and cons, and ram-pressure stripping needs very special conditions  
  > "Further observations and modeling are needed to discriminate between them." (6 Summary & conclusions)

## Claim tuples

- H: Is there extended [C ii] emission beyond the two galaxies in J1000+0234? | E: Adaptive 3D masking of the combined ALPINE/CRISTAL/archival [C ii] cube, channel maps and aperture spectra | R: A 2.4″ (~15 kpc) plume north of the DSFG with a velocity gradient, a decreasing line width and no dust continuum | F: A faint diffuse [C ii] plume extends ~15 kpc from the DSFG | **supported**
- H: Is the plume a collimated outflow from the DSFG? | E: Opening angle, misalignment with the minor axis, mass outflow rates versus SFR and AGN scaling relations, kinematic trends versus outflow expectations | R: Opening angle ~15 deg and 40 deg offset from the minor axis favor an AGN driver; outflow rates are consistent with scaling relations; the decreasing line width is in mild tension | F: The outflow scenario is a natural explanation but struggles with the kinematic structure | **partially**
- H: Does the plume trace an inflowing cold-gas filament? | E: Compare the measured velocities with the stream speed expected from the virial velocity of the halo, and stack HST images for associated UV sources | R: Measured velocities match V_stream ~ 315 km/s, but the gas appears to slow down as it falls and must be metal enriched | F: The cold accretion filament is qualitatively sound but needs a deceleration mechanism and significant enrichment | **partially**
- H: Is the plume a ram-pressure-stripped tail? | E: Gunn and Gott criterion applied to aperture #1 and comparison of the line-width trend with stripped-tail observations and simulations | R: Requires a CGM density of at least ~1 cm^-3; observed line width decreases with distance whereas stripped tails show an increase | F: Ram-pressure stripping is at odds with the observed kinematics and requires very special hydrodynamic conditions | **refuted**
- H: Is the plume tidal debris from a gravitational interaction? | E: Qualitative discussion of a flyby of CRISTAL-01a, a late-stage merger remnant and tidal stripping of a satellite, plus a dynamical-age estimate | R: Flyby and merger scenarios have problems (mass ratio ~1:10, one-sided tail), the 115 Myr plume age is plausible for a surviving tail | F: Gravitational interactions can produce such structures but the details are very uncertain; the first two cases are slightly disfavored | **partially**

## Reasoning

- Why this data: Deep, higher-resolution ALMA [C ii] data from CRISTAL are needed to confirm and understand extended [C ii] emission at high redshift  
  > "confirming and understanding extended \[C ii\] emission at high redshift requires deeper and higher angular resolution ALMA observations" (1 Introduction)
- Why this method: An adaptive matched-filter mask is used instead of a simple collapse because a pseudo-narrowband image hides narrow, low-surface-brightness features  
  > "a simple pseudo-narrowband “collapse” around the line will hide narrow and low surface brightness (SB) features below the noise level." (4.1 Adaptive masking of datacubes)
- Alternative: The Cycle 2 dataset 2012.1.00978.S was not combined because of its shallower depth and weighting complexities  
  > "because its shallower depth plus the complexities of weighting data that was processed with old versions of the pipeline" (3.1 ALMA)
- Alternative: The adaptive (masked) intensity map was not used for the morphology fits because its noise properties are ill-defined  
  > "we refrained from using the adaptive intensity map, since the noise properties are not well defined after the masking procedure" (4.2 Parametric morphology)
- How they decided it was enough: Cubes are cleaned down to 1 sigma in all cases  
  > "In all cases the data are cleaned down to $1\sigma$." (3.1 ALMA)
- Limitation (authors): Only [C ii] is available so the dominant gas phase is unknown  
  > "Since \[C ii\] is the only line available, the dominant gas phase producing the emission remains unknown." (5.1 Conical outflow)
- Limitation (authors): Aperture #1 flux and FWHM are less reliable because of contamination from the DSFG  
  > "These differences illustrate the systematic uncertainties associated with aperture #1, that make flux and FWHM less reliable." (4.3 Spectral properties of the [C II]-emitting plume)
- Limitation (authors): Derived gas masses are lower limits and outflow rates depend on the assumed kappa_[CII]  
  > "the masses we derive will effectively represent lower limits" (5.1 Conical outflow)
- Limitation (authors): The FIR limits depend on the assumed dust temperature  
  > "We note, however, that these values depend on the assumed temperature." (4.3 Spectral properties of the [C II]-emitting plume)
- Caveat (inferred, ours): The [C ii]/FIR lower limits and kappa_[CII] mass conversion rest on assumed dust temperature, excitation and abundance, so mass and outflow-rate conclusions are order-of-magnitude only
- Caveat (inferred, ours): Aperture #1 values depend on a symmetric-difference correction that assumes an axisymmetric DSFG rotator
- Caveat (inferred, ours): Scenario discrimination is qualitative; no hydrodynamic or N-body modelling is done
- Caveat (inferred, ours): Image-plane fits use unmasked integrated maps with a covariance matrix; results on the plume depend on a hand-chosen aperture layout

## Reproducibility

- Data public (paper): MUSE data retrieved from the ESO archive, HST data from MAST, project 2019.1.01587.S described as archival; public status of the ALPINE and CRISTAL data is not stated  
  > "We retrieved observations of the J1000+0234 field from the ESO archive" (3.2 MUSE); "We retrieved from MAST" (3.3 HST); "an archival dataset from project 2019.1.01587.S (PI: F. Lelli)" (3.1 ALMA)
- Products in archive: _not stated_
- Code: An in-house script was used for the ALMA adaptive masking; no release is stated  
  > "for the ALMA cubes we used a custom script" (4.1 Adaptive masking of datacubes)
- Missing: CRISTAL pipeline description (in preparation), including line-free channels, tclean parameters and image geometry
- Missing: CASA version and self-calibration solution intervals
- Missing: Custom ALMA masking script
- Missing: Priors for the CRISTAL-01a fit and widths of the DSFG priors
- Missing: Exact plume aperture positions
- Missing: Whether the ALPINE and CRISTAL data are public
- Data volume (inferred): Several hundred GB to ~1 TB of raw ALMA data across three projects, plus ~4 h of MUSE cubes and a few HST images
- Score (inferred): 2/5, Key ALMA settings are deferred to an in-preparation CRISTAL pipeline paper, the masking script is custom and unreleased, and several fit priors and aperture geometries are not given, although many numeric results and several fit setups are stated.
- Rediscovery candidate: no, The ALPINE and CRISTAL data and the CRISTAL pipeline settings are not fully specified or stated to be public, so the main plume results cannot be redone from the paper alone.

## Links

- Method: Herrera-Camus et al. in prep. (CRISTAL) (Describes the CRISTAL reduction pipeline used to make the cubes)
- Method: (cite: Czekala2021JvMGuidelines) (JvM correction method)
- Method: (cite: Herenz2017LsdCat) (LSDCAT matched filtering for MUSE)
- Method: (cite: Tsukui2022CorrelatedNoiseInterferometry) (Noise covariance estimation)
- Method: (cite: Bethermin2020DataProcessing) (ALPINE data processing and ALPINE beam)
- Companion: (cite: LeFevre2020AlpineSurveyDesign) (ALPINE survey that provided the first [C ii] data and the parent sample)
- Companion: (cite: Fraternali2021FastRotators) (Earlier [C ii] kinematics of the DSFG and source of its published properties)
- Companion: (cite: Jones2017DynamicsTiltedRingSmgs) (Earlier [C ii] analysis of the DSFG that characterised it as a disk)
- Companion: (cite: Jimenez-Andrade2023LyaNebulaeGalaxyPair) (MUSE observations of the Ly-alpha blob and the C iv and He ii emission)
- Related: ALMA ALPINE survey
- Related: ALMA CRISTAL Large Program

## Checks

```json
{
 "quotes": 181,
 "quotes_ok": 181,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 26,
 "numeric_problems": 0,
 "fill": {
  "facts": 135,
  "stated": 103,
  "rate": 0.763
 },
 "evidence_ok": true
}
```
