# ALMA Band 1 observations of the ρ Oph W filament: I. Enhanced power from excess microwave emission at high spatial frequencies

`2026A&A...707A.255C` | Astronomy and Astrophysics 2026 | first author: Casassus, S. | arXiv: 2602.11356 | DOI: 10.1051/0004-6361/202557944

Card schema 1.0 | model gemini-4-argon | depth full | type observational_alma_primary

## Science

- Fields: milky_way_ism, astrochemistry
- Question: Reveal the detailed morphology of the excess microwave emission (EME) signal in the rho Oph W filament free from imaging priors, constrain the spectral index of the high-frequency drop, and search for fine structure (PAH combs and CRRLs) in its spectrum.  
  > "Deep and high-fidelity imaging and spectroscopy of $\rho$ Oph W may reveal the detailed morphology of the EME signal, free from imaging priors, while also enabling a search for fine structure in its spectrum." (abstract); "The same observations may constrain the spectral index of the high-frequency drop." (abstract)
- Target **rho Oph W**: coordinates _not stated_; z/distance 138.9 pc  
  > "The region of the $\rho$ Ophiuchi molecular cloud exposed to UV radiation from HD 147889 (i.e. $\rho$ Oph W) is among the closest examples of PDRs, located at a distance of 138.9 pc." (The $\rho$ Oph W filament and the breakdown of the radio-IR correlation); distance from _not stated_
- Target **SR 4**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **ISO-Oph-17**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **DoAr 21**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **Compact EME source**: coordinates 16:25:54.154 -24:19:52.5  
  > "An example in the image plane may be the strong peak found at J2000 right ascension (R.A.) of 16:25:54.154 and delination (Dec.) of $-$24:19:52.5, or about $\sim$45$''$ north-west from the centre of images in Fig. 1a" (A compact EME source with no IR counterpart); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2023.1.00265.S
- bands: Band 1  
  > "The ALMA Band 1 observations of $\rho$ Oph W were acquired in ALMA program `2023.1.00265.S` using the 12 m array." (Data acquisition)
- frequencies and spectral setup: 4 spws centred on 37.209, 39.146, 41.167, and 43.104 GHz; 1920 channels per spw; 976.562 kHz channel width (~7 km/s); 1.875 GHz bandwidth per spw  
  > "The correlator was tuned to four spectral windows (spws), centred on 37.209 GHz, 39.146 GHz, 41.167 GHz, and 43.104 GHz, with 1920 channels each." (Data acquisition); "The channel width was set to 976.562 kHz, providing a bandwidth of 1.875 GHz per spw." (Data acquisition); "thus, they are narrower than the channel width of $\sim$7 km s$^{-1}$." (Limits on carbon recombination lines)
- continuum bandwidth: _not stated_
- arrays: 12 m array (36 to 39 antennas)  
  > "The ALMA Band 1 observations of $\rho$ Oph W were acquired in ALMA program `2023.1.00265.S` using the 12 m array." (Data acquisition); "Table notes: The number of antennas ranged from 36 to 39." (Imaging)
- configurations: _not stated_
- baselines: 15-361 m and 15-314 m  
  > "| 2024-03-11:11:17 | 4192 | 58 | 4.8 | 1.48 | 15-361 |" (Imaging); "| 2024-03-12:10:35 | 4131 | 67 | 6.5 | 1.40 | 15-314 |" (Imaging)
- angular resolution: ~7 arcsec (natural-weight dirty beam 8.70'' x 6.44'' / -85.6 deg; effective model resolution ~1/3 of clean beam)  
  > "Here, we report on mosaic observations of $\rho$ Oph W in ALMA Band 1 at $\sim$7 arcsec resolution (or twice as fine as the 39 GHz ATCA data)." (Introduction); "The theoretical noise of the natural-weights dirty map is 1.53 $\mu$Jy beam$^{-1}$, with a beam of 8.70$''$$\times$6.44$''$/–85.6 (in the format major axis $\times$ minor axis / position angle)." (Imaging); "Its effective angular resolution is about one-third the natural-weight clean beam (cite: Casassus2021MNRAS.507.3789C)." (Imaging)
- max recoverable scale: _not stated_
- sensitivity: 1.53 uJy/beam (theoretical noise of natural-weights dirty map); 11 uJy/beam (CASA-tclean rms)  
  > "The theoretical noise of the natural-weights dirty map is 1.53 $\mu$Jy beam$^{-1}$, with a beam of 8.70$''$$\times$6.44$''$/–85.6 (in the format major axis $\times$ minor axis / position angle)." (Imaging); "The root-mean-square (rms) noise is 11 $\mu$Jy beam$^{-1}$, and the signal-to-noise ratio of the peak of the map is 42." (Clean versus gpu-uvmem comparison)
- time on source: 4192 s, 4131 s, 4128 s (and 4242 s on 2024-03-14 excluded)  
  > "| 2024-03-11:11:17 | 4192 | 58 | 4.8 | 1.48 | 15-361 |" (Imaging); "| 2024-03-12:10:35 | 4131 | 67 | 6.5 | 1.40 | 15-314 |" (Imaging); "| 2024-03-13:11:06 | 4128 | 59 | 7.6 | 1.85 | 15-314 |" (Imaging)
- observing dates: 2024-03-11, 2024-03-12, 2024-03-13, 2024-03-14 (excluded)  
  > "The data from the last execution block, on 14-Mar-2024, were corrupted in several ways and were not included in the analysis." (Data acquisition); "| 2024-03-11:11:17 | 4192 | 58 | 4.8 | 1.48 | 15-361 |" (Imaging); "| | 2024-03-11 | 2024-03-12 | 2024-03-13 |" (Point-source subtraction)
- pi or archival as stated: _not stated_
- Line: C C56alpha to C53alpha (not stated)
- Other facility **Spitzer-IRAC (Spitzer Heritage Archive SEIP)**: IRAC 3.6, 4.5, 5.8, and 8.0 um maps used for cross-correlation templates, flux-loss simulations, and SEDs  
  > "As previously noted, the cm-wavelength continuum in $\rho$ Oph W is closely correlated with the NIR emission, in particular as traced in the four bands of the Infrared Array Camera (IRAC) aboard Spitzer (cite: Evans2009ApJS..181..321E)." (Cross-correlations with the Spitzer-IRAC maps); "The IRAC images were obtained from the Set of Enhanced Imaging Products (SEIP), which is part of the Spitzer Heritage Archive." (Cross-correlations with the Spitzer-IRAC maps)
- Other facility **Herschel (Herschel Gould Belt Survey)**: FIR images (70, 160, 250, 350, 500 um) used for counterpart search and FIR SED extraction  
  > "The point source has no FIR counterpart either (Fig. 8k-o), as shown by comparison with images from the Herschel Gould Belt Survey (cite: Herschel_2020A&A...638A..74L)." (A compact EME source with no IR counterpart); "The IR and FIR SEDs were built from the IRAC and Herschel images." (Spectral energy distribution)
- Other facility **ATCA**: 17-39 GHz multi-frequency mosaics used for morphological comparison and low-frequency SED points (17.5 and 20.2 GHz)  
  > "In the ATCA observations (cite: Casassus2021MNRAS.502..589C), at 30 arcsec resolutions, the 17–20 GHz intensities tightly follow the MIR, i.e. $I_{\rm cm} \propto I(8\,\mu{\rm m})$, despite the breakdown of this correlation on larger scales." (Comparison with the ATCA mosaics); "The ATCA images reported in (cite: Casassus2021MNRAS.502..589C) already fill in the missing spatial frequencies by incorporation of prior images in the synthesis imaging strategy." (Spectral energy distribution)
- External data: ATCA 17-39 GHz mosaics and 17.5 GHz and 20.2 GHz flux densities  
  > "The ATCA images reported in (cite: Casassus2021MNRAS.502..589C) already fill in the missing spatial frequencies by incorporation of prior images in the synthesis imaging strategy." (Spectral energy distribution) [from (cite: Casassus2021MNRAS.502..589C)]
- External data: Herschel Gould Belt Survey FIR images  
  > "The point source has no FIR counterpart either (Fig. 8k-o), as shown by comparison with images from the Herschel Gould Belt Survey (cite: Herschel_2020A&A...638A..74L)." (A compact EME source with no IR counterpart) [from (cite: Herschel_2020A&A...638A..74L)]
- External data: Spitzer-IRAC maps from SEIP  
  > "The IRAC images were obtained from the Set of Enhanced Imaging Products (SEIP), which is part of the Spitzer Heritage Archive." (Cross-correlations with the Spitzer-IRAC maps) [from (cite: Evans2009ApJS..181..321E)]
- Simulation/model as data: Simulated Band 1 visibilities on point-source-subtracted Spitzer-IRAC maps using pyralysis to quantify cross-correlation, spectral index biases, and interferometric flux loss  
  > "where $\left\{V^{\rm IRAC}_{k,l}\right\}$ are the visibilities extracted on a simulation of the Band 1 $uv$-coverage on the (point-source-subtracted) IRAC maps, obtained with the `pyralysis` package." (Cross-correlations with the Spitzer-IRAC maps); "Provided with the radio-IR slopes from Table 1, we scale the IRAC visibilities simulated on the Band 1 $uv$ plane, and add thermal noise as given by the observed visibility weights." (Band 1 flux loss and IRAC simulations)

## Processing

### Calibration

- pipeline or manual: pipeline calibrated by North America ALMA Regional Center staff  
  > "The data were calibrated by staff from the North America ALMA Regional Center, using CASA version 6.5.4.9 and ALMA pipeline version 2023.1.0.124." (Data acquisition)
- casa version: 6.5.4.9  
  > "The data were calibrated by staff from the North America ALMA Regional Center, using CASA version 6.5.4.9 and ALMA pipeline version 2023.1.0.124." (Data acquisition)
- pipeline version: 2023.1.0.124  
  > "The data were calibrated by staff from the North America ALMA Regional Center, using CASA version 6.5.4.9 and ALMA pipeline version 2023.1.0.124." (Data acquisition)
- archive products used as is: _not stated_
- flux calibrator: J1617-5848  
  > "The phase and pointing calibrator was J1625-2527, while the band pass and flux calibrator was J1617-5848." (Data acquisition)
- flux scale uncertainty: ~5% (point-source table notes) to ~10% (SED table notes)  
  > "These measurements do not include a systematic $\sim$5% flux calibration uncertainty." (Point-source subtraction); "Uncertainties in the radio flux densities are dominated by the absolute calibration error, of $\sim$10% at 1$\sigma$." (Spectral energy distribution)
- self calibration: attempted (single iteration of phase-only gaincal/applycal on 60-channel averaged data per execution block) but not used in final dataset as S/N did not improve (101.81 vs 101.96)  
  > "We performed a single iteration of tasks `gaincal` and `applycal`, using phase-only gain calibration, and without additional flagging." (Self-calibration trials); "We concluded that self-calibration was not necessary for this dataset." (Self-calibration trials)

### Imaging

- task: gpu-uvmem (primary) and CASA-tclean (comparison)  
  > "We used the `gpu-uvmem` package (cite: Casassus2006ApJ...639..951C; Carcamo2018A&C....22...16C) to minimise the objective function," (Imaging); "In order to compare the image restoration obtained with ` gpu-uvmem` against a standard CLEAN-based approach, we imaged the point-source subtracted and channel-averaged visibilities using the `CASA-tclean` package (cite: CASA2022)." (Clean versus gpu-uvmem comparison)
- deconvolver: non-parametric least-squares / maximum-entropy (gpu-uvmem, lambda=0, 10 iterations; lambda=0.1 also tested); mtmfs with nterms=1 and gain=0.05 (CASA-tclean comparison)  
  > "We therefore opted to set $\lambda=0$ and truncated the optimisation at ten iterations to avoid excessive clumping." (Imaging); "We used the `mtmfs` deconvolver, assuming a flat spectrum for the emission (` nterms=1`), and adopted the Briggs weighting scheme with ` robust=2` (natural weighting) to maximise sensitivity to diffuse emission." (Clean versus gpu-uvmem comparison); "In addition, a low loop gain (`gain=0.05`) was adopted to ensure stable convergence and to mitigate CLEAN bias when deconvolving low-surface-brightness emission." (Clean versus gpu-uvmem comparison)
- weighting robust: natural weighting (gpu-uvmem restoration); Briggs robust=2 (natural weighting in CASA-tclean)  
  > "Image restoration was carried out by producing a linear mosaic of the residual dirty maps, in natural weights, and by adding the model image smoothed by the Gaussian beam." (Imaging); "We used the `mtmfs` deconvolver, assuming a flat spectrum for the emission (` nterms=1`), and adopted the Briggs weighting scheme with ` robust=2` (natural weighting) to maximise sensitivity to diffuse emission." (Clean versus gpu-uvmem comparison)
- uv taper: _not stated_
- cell size: 1''  
  > "Imaging was performed as an instance of the maximum-entropy method, by fitting a model image, covering $N=1024^2$ pixels, 1$''$$^2$ each, directly to the visibility data." (Imaging); "We employed a set of angular scales ranging from point-like emission to several times the synthesised beam (via the parameter ` scales=[0,15,38,70]`, specified in units of image pixels, with a pixel size of $1''$)." (Clean versus gpu-uvmem comparison)
- image size: 1024 x 1024 pixels  
  > "Imaging was performed as an instance of the maximum-entropy method, by fitting a model image, covering $N=1024^2$ pixels, 1$''$$^2$ each, directly to the visibility data." (Imaging)
- masking: _not stated_
- multiscale scales: scales=[0,15,38,70] pixels (in CASA-tclean comparison)  
  > "We employed a set of angular scales ranging from point-like emission to several times the synthesised beam (via the parameter ` scales=[0,15,38,70]`, specified in units of image pixels, with a pixel size of $1''$)." (Clean versus gpu-uvmem comparison)
- continuum subtraction: Three bright point sources (SR 4, ISO-Oph-17, DoAr 21) fitted and subtracted in the uv-plane from non-gridded visibilities using pyralysis  
  > "There are three bright point sources in the mosaic of $\rho$ Oph W, corresponding to the young stellar objects SR 4, ISO-Oph-17, and DoAr 21." (Point-source subtraction); "These were subtracted in the $uv$ plane, handling the raw (non-gridded) visibility data with the `pyralysis` package (cite: casassus_carcamo2022MNRAS.513.5790C)." (Point-source subtraction)
- line free channels: _not stated_
- primary beam correction: Airy-disk approximation to the ALMA primary beam and linear mosaic attenuation map A(x)  
  > "The model visibilities, $V^m$, are computed from the model image $I^m$ using the Airy-disk approximation to the ALMA primary beam (cite: ALMA_technical_handbook2019athb.rept.....R), and by propagating the model image to each frequency using a flat spectral index in flux density ($\alpha = 0$)." (Imaging); "The linear mosaic introduces an attenuation map $\mathcal{A(\vec{x})}$ (cite: Casassus2021MNRAS.502..589C)." (Imaging)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 8.70'' x 6.44'' / -85.6 deg (natural-weights dirty map); 8.75'' x 6.47'' / -85.49 deg (CASA-tclean); 8.81'' x 6.53'' (CRRL stacked image)  
  > "The theoretical noise of the natural-weights dirty map is 1.53 $\mu$Jy beam$^{-1}$, with a beam of 8.70$''$$\times$6.44$''$/–85.6 (in the format major axis $\times$ minor axis / position angle)." (Imaging); "The synthesised beam size of the `CASA-tclean` image is $8.75''\times6.47/-85.49''$ (in the format major axis $\times$ minor axis / position angle)." (Clean versus gpu-uvmem comparison); "We stacked all four lines in a joint imaging and obtained a limit of 0.15 mJy beam$^{-1}$, with a $8.81\ensuremath{''} \times 6.53\ensuremath{''}$ beam." (Limits on carbon recombination lines)
- final rms: 1.53 uJy/beam (theoretical natural-weights dirty map); 11 uJy/beam (CASA-tclean); 5 uJy/beam (restored image error on peak); 7.2 uJy/beam (11-Mar-2024 execution block)  
  > "The theoretical noise of the natural-weights dirty map is 1.53 $\mu$Jy beam$^{-1}$, with a beam of 8.70$''$$\times$6.44$''$/–85.6 (in the format major axis $\times$ minor axis / position angle)." (Imaging); "The root-mean-square (rms) noise is 11 $\mu$Jy beam$^{-1}$, and the signal-to-noise ratio of the peak of the map is 42." (Clean versus gpu-uvmem comparison); "As shown in Fig. 8a, this local peak appears to be point-like in the Band 1 model image, and reaches $0.576\pm0.005\,$ mJy beam$^{-1}$ in the restored image Fig. 8f, which rivals the global peak along the filament, at $0.631\pm0.005$ mJy beam$^{-1}$." (A compact EME source with no IR counterpart)

### Inherited from earlier work

- gpu-uvmem image synthesis and linear mosaic attenuation map formalism  
  > "We used the `gpu-uvmem` package (cite: Casassus2006ApJ...639..951C; Carcamo2018A&C....22...16C) to minimise the objective function," (Imaging); "The linear mosaic introduces an attenuation map $\mathcal{A(\vec{x})}$ (cite: Casassus2021MNRAS.502..589C)." (Imaging) [from (cite: Casassus2006ApJ...639..951C; Carcamo2018A&C....22...16C; Casassus2021MNRAS.502..589C)]
- Matched-filter technique for placing limits on PAH rotational frequency combs  
  > "We use the cross-correlation spectrum, $a_\nu$, to place limits on such PAH combs in an adaptation of the matched-filter technique proposed in (cite: Ali-Haimoud2014) and (cite: Ali-Haimoud2015MNRAS.447..315A)." (Limits on PAH combs) [from (cite: Ali-Haimoud2014; Ali-Haimoud2015MNRAS.447..315A)]

### Not stated but needed to reproduce (our reading)

- Exact J2000 coordinates of the 16 mosaic pointing centres
- Best-fit J2000 coordinates for the three subtracted point sources (SR 4, ISO-Oph-17, DoAr 21)
- Exact rest frequencies used to stack the C56alpha to C53alpha carbon recombination lines
- Stopping criterion or niter/threshold used in the CASA-tclean comparison imaging

## Analysis recipe

1. **Fit and subtract bright point sources in the uv-plane**: Bin visibilities into 60-channel bins with CASA mstransform; fit positions, flux densities at 40.15 GHz, and spectral indices for SR 4, ISO-Oph-17, and DoAr 21 in each execution block separately using pyralysis and iminuit; subtract point-source models from unaveraged visibilities and verify by extracting channel-by-channel point-source spectra.  
  > "These were subtracted in the $uv$ plane, handling the raw (non-gridded) visibility data with the `pyralysis` package (cite: casassus_carcamo2022MNRAS.513.5790C)." (Point-source subtraction); "In order to reduce the volume of the data, we averaged the visibilities into 60 channel bins (using `CASA` task ` mstransform`)." (Point-source subtraction); "Provided with models for each point source, we proceeded with their subtraction from the non-channel-averaged visibilities." (Point-source subtraction)
   - software: CASA mstransform, pyralysis, iminuit
   - parameter: reference frequency nu_0 = 40.15 GHz; 60-channel bins; 4 nearest fields used for DoAr 21, closest field for SR 4 and ISO-Oph-17  
  > "We first fit for the point source positions, their flux densities, $F_{\nu_\circ}$, at the reference frequency, $\nu_\circ = 40.15\,$GHz (corresponding to the centre frequency of the four spectral windows), and spectral indices, $\alpha$." (Point-source subtraction); "The point-source fits to DoAr 21 required the incorporation of the four nearest fields to reach thermal residuals." (Point-source subtraction)
   - assumption: Airy disk approximation to the ALMA primary beam  
  > "We attribute the imperfect point-source subtraction for DoAr 21 in single-field point-source fits (with $\lesssim 5\%$ residuals) to the accuracy of the Airy disk approximation to the ALMA primary beam." (Point-source subtraction)
   - fitting: chi-squared minimisation in uv-plane with iminuit using the Hessian approximation for uncertainties  
  > "We used the `iminuit` package (cite: James:1975dr; iminuit), using the Hessian approximation to estimate uncertainties." (Point-source subtraction)
   - validation: Extracted point-source flux densities in each channel at best-fit positions and verified consistency with spectral index fits  
  > "As a sanity check on the point-source fits (and provided with their best-fit positions, $\vec{x_\circ}$), we also extracted point-source flux densities in each channel." (Point-source subtraction); "are consistent with the channel flux densities." (Point-source subtraction)
2. **Deconvolve and image the 16-field mosaic**: Fit a 1024x1024 pixel model image directly to non-gridded visibilities across the 16 fields using gpu-uvmem; restore by adding the Gaussian-smoothed model image to the natural-weighted linear mosaic of residual dirty maps; compare against multi-scale CASA-tclean image.  
  > "Imaging was performed as an instance of the maximum-entropy method, by fitting a model image, covering $N=1024^2$ pixels, 1$''$$^2$ each, directly to the visibility data." (Imaging); "Image restoration was carried out by producing a linear mosaic of the residual dirty maps, in natural weights, and by adding the model image smoothed by the Gaussian beam." (Imaging); "In order to compare the image restoration obtained with ` gpu-uvmem` against a standard CLEAN-based approach, we imaged the point-source subtracted and channel-averaged visibilities using the `CASA-tclean` package (cite: CASA2022)." (Clean versus gpu-uvmem comparison)
   - software: gpu-uvmem, CASA-tclean
   - parameter: N = 1024^2 pixels of 1''x1'', sigma_I = 100 uJy/beam pre-conditioning, lambda = 0 (truncated at 10 iterations) and lambda = 0.1; tclean: mtmfs, nterms=1, robust=2, scales=[0,15,38,70], gain=0.05  
  > "The free parameters are the intensities in each image pixel in units of a fiducial noise value, $p_i = I^m_i / \sigma_I$, where $\sigma_I = 100$ $\mu$Jy beam$^{-1}$ was chosen to be large as a pre-conditioning factor for the optimisation." (Imaging); "We therefore opted to set $\lambda=0$ and truncated the optimisation at ten iterations to avoid excessive clumping." (Imaging); "We employed a set of angular scales ranging from point-like emission to several times the synthesised beam (via the parameter ` scales=[0,15,38,70]`, specified in units of image pixels, with a pixel size of $1''$)." (Clean versus gpu-uvmem comparison)
   - assumption: Flat spectral index in flux density (alpha = 0) when propagating model image across frequencies; Airy-disk primary beam  
  > "The model visibilities, $V^m$, are computed from the model image $I^m$ using the Airy-disk approximation to the ALMA primary beam (cite: ALMA_technical_handbook2019athb.rept.....R), and by propagating the model image to each frequency using a flat spectral index in flux density ($\alpha = 0$)." (Imaging)
   - fitting: Objective function minimisation in gpu-uvmem (pure least-squares with lambda=0 for 10 iterations, or entropy regularisation with lambda=0.1)  
  > "Trials resulted in satisfactory results for $\lambda = 0.1$, with thermal residuals." (Imaging); "We therefore opted to set $\lambda=0$ and truncated the optimisation at ten iterations to avoid excessive clumping." (Imaging)
   - validation: Self-calibration trial on 11-Mar-2024 execution block; comparison with CASA-tclean; uv-plane simulations on IRAC 3.6 um image to test bias and artefacts  
  > "We concluded that self-calibration was not necessary for this dataset." (Self-calibration trials); "The Band 1 point source is not an artefact of the imaging strategy, as verified through simulations of the Band 1 $uv-$coverage on the IRAC images (Fig. 8g-j; see also Appendix 5)." (A compact EME source with no IR counterpart)
3. **Place upper limits on Carbon Radio Recombination Lines (CRRLs)**: Stack the four CRRLs (C56alpha to C53alpha) within the correlator setup in a joint imaging.  
  > "There are four carbon radio-recombination lines (CRRLs) within our correlator setup, from C56$\alpha$ to C53$\alpha$." (Limits on carbon recombination lines); "We stacked all four lines in a joint imaging and obtained a limit of 0.15 mJy beam$^{-1}$, with a $8.81\ensuremath{''} \times 6.53\ensuremath{''}$ beam." (Limits on carbon recombination lines)
   - parameter: channel width ~7 km/s; beam 8.81'' x 6.53''  
  > "The turbulent linewidths in the filament are likely of the order of $\sim$2 km s$^{-1}$ (cite: Pankonin1978A&A....64..333P); thus, they are narrower than the channel width of $\sim$7 km s$^{-1}$." (Limits on carbon recombination lines); "We stacked all four lines in a joint imaging and obtained a limit of 0.15 mJy beam$^{-1}$, with a $8.81\ensuremath{''} \times 6.53\ensuremath{''}$ beam." (Limits on carbon recombination lines)
   - assumption: Turbulent linewidths ~2 km/s; LTE conditions and negligible depopulation factors above 100 K for comparison  
  > "The physical conditions in $\rho$ Oph W inferred from PDR models (cite: Habart2003) should yield LTE line intensities of $\sim$2 mJy beam$^{-1}$ (cite: Casassus2021MNRAS.502..589C)." (Limits on carbon recombination lines); "Depopulation factors are negligible above 100 K (cite: Salgado2017ApJ...837..141S)." (Limits on carbon recombination lines)
   - fitting: _not stated_
   - validation: _not stated_
4. **Extract intra-band diffuse emission spectrum and spectral index**: Simulate visibilities on the pure-chi2 deconvolved model image template I^m using pyralysis, perform weighted linear regression in the uv-plane at each frequency channel (or 120-channel bin) to get slope a_nu, and fit a power law in frequency.  
  > "Instead, we opt for cross-correlation with a template image, for which we use the deconvolved model image, $I^m$, of Fig. 1c, assuming a flat spectral index." (Extraction of the intra-band diffuse emission spectrum); "Example spectra are shown in Fig. 5 for the 120-channel average and extracted over regions along the filament." (Extraction of the intra-band diffuse emission spectrum)
   - software: pyralysis
   - parameter: 120-channel average (16 channels); reference frequency nu_0 = 36.63 GHz; pure-chi2 template (lambda = 0)  
  > "Example spectra are shown in Fig. 5 for the 120-channel average and extracted over regions along the filament." (Extraction of the intra-band diffuse emission spectrum); "The slopes $a_{\nu_\circ}$ are slightly biased downwards, with $a_{\nu_\circ} = 0.96\pm0.005$ for $\nu_\circ = 36.63\,$GHz averaged over all fields, which results from the use of the pure-$\chi^2$ model image as template." (Extraction of the intra-band diffuse emission spectrum)
   - assumption: Template image I^m has flat spectral index across the band  
  > "Instead, we opt for cross-correlation with a template image, for which we use the deconvolved model image, $I^m$, of Fig. 1c, assuming a flat spectral index." (Extraction of the intra-band diffuse emission spectrum)
   - fitting: Analytic weighted least-squares for linear regression slope a_nu, followed by power-law fit a_nu ~ a_nu0 (nu/nu_0)^alpha_d  
  > "We search for a linear-regression slope, $a_\nu$, such that $$\begin{equation} I_\nu = a_\nu I^m, \end{equation}$$ by simulating visibilities on the template image, $V^m_{k,l}$ (cite: casassus_carcamo2022MNRAS.513.5790C), and minimising $$\begin{equation} \chi^2 = \sum_{k=1}^{K} \sum_{l=1}^{M_k} \omega_{k,l} \left| V_{k,l} - a_\nu V^m_{k,l}\right|^2 , \end{equation}$$" (Extraction of the intra-band diffuse emission spectrum); "Power-law fits for $$\begin{equation} a_\nu \sim a_{\nu_\circ} (\nu/ \nu_\circ)^{\alpha_d}, \label{eq:diffusespecfit} \end{equation}$$ yield varying spectral indices, $\alpha_d$, over different regions." (Extraction of the intra-band diffuse emission spectrum)
   - validation: Tested spectral extraction on simulated Band 1 visibilities from the IRAC 3.6 um template with input alpha=0, confirming lambda=0 recovers alpha=0 within 1 sigma while lambda=0.1 introduces a bias (alpha = -0.26 +/- 0.09)  
  > "We recover the input spectral index ($\alpha = 0$) within 1$\sigma$ in all cases." (Band 1 flux loss and IRAC simulations); "In contrast, the entropy-regularised images (with $\lambda=0.1$) yield biased spectral indices, for example $\alpha = -0.26\pm0.09$ for fields 7-10." (Band 1 flux loss and IRAC simulations)
5. **Cross-correlate ALMA Band 1 visibilities with Spitzer-IRAC templates**: Remove stellar point sources from IRAC maps using StarXTerminator in PixInsight; simulate Band 1 visibilities on star-subtracted IRAC maps with pyralysis; compute linear regression slopes a_IR and complex visibility Pearson r coefficients across all baselines and as a function of uv-radius bins.  
  > "We quantified the degree of correlation between the ALMA Band 1 data and the IRAC bands using linear regression and the Pearson $r$ cross-correlation coefficient." (Cross-correlations with the Spitzer-IRAC maps); "where $\left\{V^{\rm IRAC}_{k,l}\right\}$ are the visibilities extracted on a simulation of the Band 1 $uv$-coverage on the (point-source-subtracted) IRAC maps, obtained with the `pyralysis` package." (Cross-correlations with the Spitzer-IRAC maps); "Star subtraction was performed using ` StarXTerminator`, an AI-based tool that employs neural networks to remove stellar sources from astronomical images." (Point-source subtraction in the IRAC images)
   - software: StarXTerminator, PixInsight, pyralysis
   - parameter: 16 channels (120-channel average); uv-radius bins  
  > "Table 1 lists the radio-IR slopes averaged over all spectral windows and fields, and calculated after binning the data into 16 channels (with a 120 channel average)." (Cross-correlations with the Spitzer-IRAC maps)
   - assumption: Coarser angular resolution of IRAC 8.0 um (1.98'') vs ALMA (~7'') introduces negligible bias  
  > "Since most of the 40.2 GHz signal is in the shortest spacings, and the angular resolution of the ALMA map is $\sim 7$ arcsec, biases in the correlations due to the coarser resolution at 8.0 $\mu$m are negligible." (Cross-correlations with the Spitzer-IRAC maps)
   - fitting: Weighted linear regression for a_IR and bootstrap resampling for uncertainties on Pearson r in uv-radius bins  
  > "We estimated the uncertainties in $r$ by bootstrapping." (Cross-correlations with the Spitzer-IRAC maps)
   - validation: Masked stellar locations and correlated star-subtracted IRAC template with original image, finding a correlation slope of unity  
  > "To assess whether the subtraction introduced any bias, we masked the locations of the stars and correlated the star-subtracted template with the original image, finding a correlation slope of unity, which indicates that the subtraction is robust." (Point-source subtraction in the IRAC images)
6. **Estimate interferometric flux loss and extract multi-frequency SEDs**: Integrate product of images and linear mosaic attenuation map A(x) over selected field apertures for ALMA Band 1, ATCA, IRAC, and Herschel maps; estimate Band 1 flux-loss factor f_B1 by comparing input vs gpu-uvmem restored flux density on simulated IRAC 3.6 um visibilities.  
  > "The total Band 1 flux densities are estimated via aperture photometry, and by correcting for the flux loss due to missing interferometer spacings, for which we use the simulations on the IRAC 3.6 $\mu$m template (see Sect. 5 in Appendix)." (Spectral energy distribution); "The flux densities from the IR ancillary data were extracted by aperture photometry; namely, by integrating the product of the IR images with the linear mosaic attenuation map (see Sect. 5 in Appendix)." (Spectral energy distribution); "The integrated flux density in the scaled 3.6 $\mu$m template is 0.66 Jy over the whole mosaic, as estimated by integration of the product with the mosaic attenuation map (cite: Casassus2021MNRAS.502..589C)." (Band 1 flux loss and IRAC simulations)
   - software: gpu-uvmem, pyralysis
   - parameter: Fixed 10% error on radio flux densities; apertures defined by field subsets (all, 5-6, 7-10, 6, 7-9)  
  > "The thermal errors are negligible compared to absolute flux calibration errors, and we opt to consider a fixed 10% error on the flux densities extracted for the radio data." (Spectral energy distribution); "| all | 37.6 | 0.29 | 19.3 | 11.8 | 160 | 463 | 4167 | 7548 | 3216 | 1380 | 540 | 240 | $-0.78\pm0.05$ | \- | \- |" (Spectral energy distribution)
   - assumption: Band 1 signal follows the same large-scale power spectrum as the IRAC 3.6 um template for flux-loss estimation  
  > "The underlying assumption in our strategy for flux loss estimates is that the Band 1 signal follows the same power spectrum as the template, which appears to hold on large scales, but deviates in small scales (see Sect. 3.3)." (Band 1 flux loss and IRAC simulations)
   - fitting: _not stated_
   - validation: _not stated_
7. **Search for and place limits on PAH rotational frequency combs**: Rectify the cross-correlation spectrum a_nu by dividing by the power-law fit and subtracting the weighted mean; project onto a basis of comb functions with line spacing Delta_nu_line using a matched-filter dot product across all 4 spectral windows.  
  > "We use the cross-correlation spectrum, $a_\nu$, to place limits on such PAH combs in an adaptation of the matched-filter technique proposed in (cite: Ali-Haimoud2014) and (cite: Ali-Haimoud2015MNRAS.447..315A)." (Limits on PAH combs); "We first rectify the signal $a_\nu$ by division with the power-law fit of Eq." (Limits on PAH combs)
   - parameter: S = 4 spectral windows, C = 1920 channels each; scan Delta_nu_line from twice the frequency resolution up to 200 MHz, sampling every tenth of a resolution element (~2000 values); tested native resolution and 5-channel bins  
  > "In this application, the domain of the comb basis is split into $S=4$ spectral windows, each composed of $C=1920$ regularly-spaced channels and with channel widths. $\delta {\nu_s}$." (Limits on PAH combs); "We scan $\Delta\nu_{\rm line}$ over the interval from twice the frequency resolution of $a_\nu$ (i.e. the channel width, or its binned versions), and up to 200 MHz, sampling every tenth of a resolution element." (Limits on PAH combs); "Fig.10 illustrates the resulting values for the case of five-channel bins and no channel binning." (Limits on PAH combs)
   - assumption: Imperfect planar PAHs with D6h or D3h quasi-symmetry and permanent dipole arising from defects produce regularly spaced frequency combs  
  > "As shown by (cite: Ali-Haimoud2014), the rotational spectrum of imperfect planar PAHs, with either D$_6$h or D$_3$h quasi-symmetry and a permanent dipole arising from defects, should appear as a regularly spaced frequency comb," (Limits on PAH combs)
   - fitting: Linear projection onto comb basis functions weighted by inverse variance  
  > "In summary, the projection of the rectified signal, $\delta b(\nu_{s,c}),$ on comb $c_j$ with line spacing $\Delta\nu_{\rm line}$, is $$\begin{equation} \mathcal{S}(\delta b) = \frac{\langle \delta\,b(\nu) \cdot c_i(\nu) \rangle}{\langle c_i(\nu) \cdot c_i(\nu) \rangle}, \end{equation}$$" (Limits on PAH combs)
   - validation: _not stated_

## Software

- **CASA** 6.5.4.9: Initial data calibration, visibility channel averaging (mstransform), self-calibration trials (gaincal, applycal), and comparison multiscale imaging (tclean)  
  > "The data were calibrated by staff from the North America ALMA Regional Center, using CASA version 6.5.4.9 and ALMA pipeline version 2023.1.0.124." (Data acquisition); "In order to reduce the volume of the data, we averaged the visibilities into 60 channel bins (using `CASA` task ` mstransform`)." (Point-source subtraction); "We performed a single iteration of tasks `gaincal` and `applycal`, using phase-only gain calibration, and without additional flagging." (Self-calibration trials); "In order to compare the image restoration obtained with ` gpu-uvmem` against a standard CLEAN-based approach, we imaged the point-source subtracted and channel-averaged visibilities using the `CASA-tclean` package (cite: CASA2022)." (Clean versus gpu-uvmem comparison)
- **ALMA pipeline** 2023.1.0.124: Archival pipeline calibration of the ALMA Band 1 observations  
  > "The data were calibrated by staff from the North America ALMA Regional Center, using CASA version 6.5.4.9 and ALMA pipeline version 2023.1.0.124." (Data acquisition)
- **gpu-uvmem** : Non-parametric least-squares and maximum-entropy synthesis imaging directly on non-gridded visibilities  
  > "We used the `gpu-uvmem` package (cite: Casassus2006ApJ...639..951C; Carcamo2018A&C....22...16C) to minimise the objective function," (Imaging)
- **pyralysis** : Handling raw non-gridded visibility data for uv-plane point-source subtraction and simulating visibilities on template and IRAC images  
  > "These were subtracted in the $uv$ plane, handling the raw (non-gridded) visibility data with the `pyralysis` package (cite: casassus_carcamo2022MNRAS.513.5790C)." (Point-source subtraction); "where $\left\{V^{\rm IRAC}_{k,l}\right\}$ are the visibilities extracted on a simulation of the Band 1 $uv$-coverage on the (point-source-subtracted) IRAC maps, obtained with the `pyralysis` package." (Cross-correlations with the Spitzer-IRAC maps)
- **iminuit** : Fitting point-source positions, flux densities, and spectral indices in the uv-plane and estimating uncertainties via the Hessian approximation  
  > "We used the `iminuit` package (cite: James:1975dr; iminuit), using the Hessian approximation to estimate uncertainties." (Point-source subtraction)
- **StarXTerminator** : AI neural-network removal of stellar point sources from Spitzer-IRAC images  
  > "Star subtraction was performed using ` StarXTerminator`, an AI-based tool that employs neural networks to remove stellar sources from astronomical images." (Point-source subtraction in the IRAC images)
- **PixInsight** : Image-processing platform hosting the StarXTerminator plug-in for IRAC star subtraction  
  > "This tool was used as a plug-in within the `PixInsight` image-processing platform." (Point-source subtraction in the IRAC images)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Band 1 diffuse EME spectral index (all fields) | -0.78 | 0.05 | dimensionless | 4 | It follows a spectral index $\alpha = -0.78\pm0.05$, in frequency, with some variations along the filament.; / all / 37.6 / 0.29 / 19.3 / 11.8 / 160 / 463 / 4167 / 7548 / 3216 / 1380 / 540 / 240 / $-0.78\pm0.05$ / \- / \- / |
| Band 1 diffuse EME spectral index (fields 5,6) | -0.16 | 0.14 | dimensionless | 4 | The spectral index variations are very significant along the filament, from $\alpha_d = -0.16\pm0.14$ in fields 5 and 6 (south-east of the filament), to $\alpha_d = -1.06\pm0.08$ in fields 7 to 10 (north-west of the filament). |
| Band 1 diffuse EME spectral index (fields 7-10) | -1.06 | 0.08 | dimensionless | 4 | The spectral index variations are very significant along the filament, from $\alpha_d = -0.16\pm0.14$ in fields 5 and 6 (south-east of the filament), to $\alpha_d = -1.06\pm0.08$ in fields 7 to 10 (north-west of the filament). |
| Band 1 diffuse EME spectral index (field 6) | -0.24 | 0.17 | dimensionless | 4 | / 6 / 6.1 / 0.33 / 3.9 / 2.3 / 32 / 89 / 801 / 1447 / 625 / 270 / 107 / 55 / $-0.24\pm0.17$ / 130 / 72 / |
| Band 1 diffuse EME spectral index (fields 7-9) | -1.05 | 0.08 | dimensionless | 4 | / 7-9 / 12.5 / 0.40 / 7.7 / 4.6 / 64 / 182 / 1525 / 2495 / 1009 / 423 / 164 / 125 / $-1.05\pm0.08$ / 265 / 146 / |
| 40.2 GHz uncorrected flux density (all fields) | 240 | 10% | mJy | 6 | / all / 37.6 / 0.29 / 19.3 / 11.8 / 160 / 463 / 4167 / 7548 / 3216 / 1380 / 540 / 240 / $-0.78\pm0.05$ / \- / \- /; Uncertainties in the radio flux densities are dominated by the absolute calibration error, of $\sim$10% at 1$\sigma$. |
| Band 1 flux recovery fraction f_B1 (all fields) | 0.29 | not stated | dimensionless | 6 | / all / 37.6 / 0.29 / 19.3 / 11.8 / 160 / 463 / 4167 / 7548 / 3216 / 1380 / 540 / 240 / $-0.78\pm0.05$ / \- / \- /; The same exercise on the restored map yields 0.19 Jy, so ALMA Band 1 recovers about 29% of the total flux density. |
| SR 4 combined flux density at 40.15 GHz | 893 | 16 | uJy | 1 | / / ($893\pm16$)/($2.27\pm0.32$)$^{a}$ / |
| SR 4 combined spectral index | 2.27 | 0.32 | dimensionless | 1 | / / ($893\pm16$)/($2.27\pm0.32$)$^{a}$ / |
| ISO-Oph 17 combined flux density at 40.15 GHz | 2588 | 29 | uJy | 1 | / / ($2588 \pm 29$)/($3.09\pm 0.20$)$^{a}$ / |
| ISO-Oph 17 combined spectral index | 3.09 | 0.20 | dimensionless | 1 | / / ($2588 \pm 29$)/($3.09\pm 0.20$)$^{a}$ / |
| DoAr 21 flux density at 40.15 GHz (2024-03-11) | 21462 | 26 | uJy | 1 | / DoAr 21 / ($21462\pm26$)/($-0.35\pm0.02$) / ($18731\pm 25$) / ($-0.502\pm 0.02$) / ($12819\pm 28$) / ($-0.06\pm0.04$ ) / |
| DoAr 21 flux density at 40.15 GHz (2024-03-12) | 18731 | 25 | uJy | 1 | / DoAr 21 / ($21462\pm26$)/($-0.35\pm0.02$) / ($18731\pm 25$) / ($-0.502\pm 0.02$) / ($12819\pm 28$) / ($-0.06\pm0.04$ ) / |
| DoAr 21 flux density at 40.15 GHz (2024-03-13) | 12819 | 28 | uJy | 1 | / DoAr 21 / ($21462\pm26$)/($-0.35\pm0.02$) / ($18731\pm 25$) / ($-0.502\pm 0.02$) / ($12819\pm 28$) / ($-0.06\pm0.04$ ) / |
| Stacked CRRL (C56alpha to C53alpha) intensity limit | < 0.15 | not stated | mJy/beam | 3 | We stacked all four lines in a joint imaging and obtained a limit of 0.15 mJy beam$^{-1}$, with a $8.81\ensuremath{''} \times 6.53\ensuremath{''}$ beam. |
| Radio-IR slope a_IR for IRAC 3.6 um | 3.435e-2 | 1.5e-4 | dimensionless | 5 | / 3.6 $\mu$m / $3.435\times 10^{-2} \pm 1.5\times 10^{-4}$ / |
| Radio-IR slope a_IR for IRAC 4.5 um | 6.345e-2 | 3.0e-4 | dimensionless | 5 | / 4.5 $\mu$m / $6.345\times 10^{-2} \pm 3.0\times 10^{-4}$ / |
| Radio-IR slope a_IR for IRAC 5.8 um | 4.463e-3 | 2.1e-5 | dimensionless | 5 | / 5.8 $\mu$m / $4.463\times 10^{-3} \pm 2.1\times 10^{-5}$ / |
| Radio-IR slope a_IR for IRAC 8.0 um | 1.515e-3 | 7.7e-6 | dimensionless | 5 | / 8.0 $\mu$m / $1.515\times 10^{-3} \pm 7.7\times 10^{-6}$ / |
| Increase factor in Band 1 to IRAC 3.6 um slope from short to long baselines (7818 lambda) | 1.77 | 0.01 | dimensionless | 5 | For the best template (i.e. 3.6 $\mu$m), $a_{\rm IR}$ increases from $3.3\times10^{-2}\pm 1.8\times 10^{-4}$ to $5.83\times10^{-2}\pm 2.8\times 10^{-3}$ for the bin starting at 7818$\lambda$.; This corresponds to a factor of $1.77\pm0.01$. |
| Compact radio-only EME source peak intensity in restored image | 0.576 | 0.005 | mJy/beam | 2 | As shown in Fig. 8a, this local peak appears to be point-like in the Band 1 model image, and reaches $0.576\pm0.005\,$ mJy beam$^{-1}$ in the restored image Fig. 8f, which rivals the global peak along the filament, at $0.631\pm0.005$ mJy beam$^{-1}$. |
| Global peak intensity along the filament in restored image | 0.631 | 0.005 | mJy/beam | 2 | As shown in Fig. 8a, this local peak appears to be point-like in the Band 1 model image, and reaches $0.576\pm0.005\,$ mJy beam$^{-1}$ in the restored image Fig. 8f, which rivals the global peak along the filament, at $0.631\pm0.005$ mJy beam$^{-1}$. |
| Significance of PAH comb power S(delta b)/sigma | < 3.5 | not stated | dimensionless | 7 | There is no significant power in comb functions, with a spectral resolution as fine as twice the channel width: $\mathcal{S}(\delta b)/\sigma(\mathcal{S}(\delta b)) < 3.5$ in $\sim$2000 values for $\Delta \nu_{\rm line}$. |

## Qualitative findings

- The Band 1 EME spectrum is a smooth power law with spectral index alpha = -0.78 +/- 0.05 overall and significant variations along the filament, showing no detectable fine structure from PAH rotational combs or carbon recombination lines.  
  > "The spectrum is a power law, with no detectable fine structure." (abstract); "It follows a spectral index $\alpha = -0.78\pm0.05$, in frequency, with some variations along the filament." (abstract)
- ALMA Band 1 emission exhibits enhanced power at high spatial frequencies relative to IRAC templates, including bends, clumps, and a compact (<7'') EME source at 16:25:54.154 -24:19:52.5 with no NIR or FIR counterpart.  
  > "Interestingly, the Band 1 power at high spatial frequencies increases relative to that of the IR signal, with a factor of two more power in Band 1 at $\sim 20\ensuremath{''}$ than at $\sim 100\,\ensuremath{''}$ (relative to IRAC 3.6 $\mu$m)." (abstract); "An extreme of such radio-only structures is a compact EME source, without IR counterpart." (abstract)
- DoAr 21 exhibits strong day-to-day flux density and spectral index variability in Band 1, whereas SR 4 and ISO-Oph 17 are steady with spectral indices consistent with Rayleigh-Jeans dust emission.  
  > "the flux densities for ISO-Oph 17 and SR 4 were consistent in each execution block, with no indication of variability." (Point-source subtraction); "However, the very bright non-thermal emission from DoAr 21 turned out to be highly variable." (Point-source subtraction)

## Claim tuples

- H: The high-frequency drop of the excess microwave emission (EME) in rho Oph W between 36 and 44 GHz follows a steep power law and varies across the PDR filament. | E: Extracted intra-band spectra in the uv-plane by cross-correlating ALMA Band 1 visibilities with the pure-chi2 gpu-uvmem deconvolved model template over the whole mosaic and sub-regions. | R: Measured an overall spectral index alpha = -0.78 +/- 0.05, varying from alpha_d = -0.16 +/- 0.14 in fields 5-6 (south-east) to alpha_d = -1.06 +/- 0.08 in fields 7-10 (north-west). | F: The EME spectrum in Band 1 is a power law with significant spatial variations in spectral index along the filament. | **supported**
- H: Quasi-symmetric planar PAHs with permanent dipoles produce detectable evenly spaced rotational frequency combs in the Band 1 EME spectrum. | E: Applied a matched-filter comb projection to the rectified cross-correlation spectrum across all 4 spectral windows for comb spacings from twice the channel width up to 200 MHz. | R: No significant comb power was detected, with S(delta b)/sigma < 3.5 across ~2000 spacing values and < 3 x 0.06 of flux density in ~200 MHz combs. | F: There is no detectable comb-like fine structure in the Band 1 EME spectrum, likely because a large number of isomer configurations, non-planar geometries, and defect sites superimpose too many weak lines. | **refuted**
- H: The EME morphology in rho Oph W tightly follows the IR PAH emission morphology down to small angular scales. | E: Cross-correlated Band 1 visibilities with star-subtracted Spitzer-IRAC templates as a function of uv-radius and compared high-resolution gpu-uvmem Band 1 images with IRAC and Herschel maps. | R: The Band 1 to IRAC 3.6 um slope increases by a factor of 1.77 +/- 0.01 from short baselines to 7818 lambda (~20'' vs ~100''), Pearson r drops strongly with baseline length, and a compact (<7'') EME peak of 0.576 +/- 0.005 mJy/beam has no NIR or FIR counterpart. | F: The radio-IR correlation breaks down at small scales within the filament, with Band 1 showing a factor of ~2 enhanced power at high spatial frequencies and radio-only structures including a compact pure EME source. | **refuted**
- H: Carbon radio recombination lines (C56alpha to C53alpha) from the C II PDR region should be detectable at LTE intensities of ~2 mJy/beam. | E: Stacked the four CRRLs (C56alpha to C53alpha) present in the Band 1 correlator setup in a joint image. | R: Non-detection with an upper limit of 0.15 mJy/beam in an 8.81'' x 6.53'' beam. | F: CRRLs are undetected at levels well below simple LTE predictions, possibly because collisional de-excitation in denser regions creates an unstructured emission map that is filtered out by the interferometer. | **refuted**

## Reasoning

- Why this data: ALMA Band 1 (35-50 GHz) with ~39 antennas provides twice finer angular resolution (~7'') and much higher fidelity than the 5-antenna ATCA 39 GHz data, allowing imaging without an IR prior, clean removal of contaminating point sources like SR 4, and a search for spectral fine structure and CRRLs.  
  > "The commissioning of the Band 1 receivers on the Atacama Large Millimetre Array (ALMA), covering 35 GHz to 50 GHz, offers the opportunity to map the filament with much better fidelity than with ATCA, and at finer angular resolutions." (Introduction); "The same ALMA observations can be used to search for fine structure in the EME spectrum, which may be used to identify its carriers (cite: Ali-Haimoud2014; Ali-Haimoud2015MNRAS.447..315A)." (Introduction)
- Why this method: Visibility-plane cross-correlation with a pure-chi2 (lambda=0) gpu-uvmem model template avoids aperture photometry on faint single-channel diffuse emission, avoids negative bowls seen in CLEAN, and avoids the spectral index bias introduced by entropy regularisation (lambda=0.1) or differing IR template morphologies.  
  > "The diffuse emission from $\rho$ Oph W is too faint for the extraction of its spectrum in individual channels through aperture photometry." (Extraction of the intra-band diffuse emission spectrum); "It does, however, become detectable with the introduction of entropy, which is the reason we avoided regularisation." (Extraction of the intra-band diffuse emission spectrum); "In contrast, `gpu-uvmem` naturally suppresses large-scale negative artefacts, leading to a more physically plausible reconstruction in low-signal regions." (Clean versus gpu-uvmem comparison)
- Alternative: Entropy regularisation (lambda = 0.1) in gpu-uvmem was tested and gave thermal residuals, but was rejected for spectral extraction because it introduced a significant bias in the derived spectral index (e.g. alpha = -0.26 +/- 0.09 on flat-spectrum simulations).  
  > "However, with entropy regularisation, the spectral extraction technique turned out to be significantly biased (see Appendix 5)." (Imaging); "We therefore opted to set $\lambda=0$ and truncated the optimisation at ten iterations to avoid excessive clumping." (Imaging)
- Alternative: Self-calibration (phase-only gaincal/applycal) was tested on individual execution blocks but rejected as unnecessary because S/N did not improve (101.81 vs 101.96).  
  > "For comparison, before self-calibration the same restoration yields essentially the same value, with a somewhat larger S/N=101.96." (Self-calibration trials); "We concluded that self-calibration was not necessary for this dataset." (Self-calibration trials)
- Alternative: Using Spitzer-IRAC maps directly as templates to extract the Band 1 spectral index was rejected because the Band 1 and IRAC morphologies/power spectra differ as a function of uv-radius.  
  > "This confirms that the Band 1 and IRAC morphologies are appreciably different, and limits the use of the IRAC bands as templates to estimate the spectral index of the Band 1 signal, since varying frequencies correspond to varying $uv$-radii." (Cross-correlations with the Spitzer-IRAC maps)
- Alternative: Multi-scale CASA-tclean was compared against gpu-uvmem and showed large-scale negative bowls and lower dynamic range.  
  > "As explained in Appendix 6, after point-source subtraction `gpu-uvmem` generates images with much higher dynamic range than achievable with CASA-`tclean`." (Self-calibration trials); "However, on the largest angular scales the CLEAN image exhibits negative bowls, reflecting the limited ability of CLEAN to recover smoothly distributed emission in the presence of incomplete short-spacing coverage." (Clean versus gpu-uvmem comparison)
- How they decided it was enough: _not stated_
- Limitation (authors): Severe interferometric flux loss (~70% missing flux; only ~29-30% recovered over the whole mosaic) due to missing short spacings in the 12 m array data.  
  > "As described in Appendix 5, the flux recovered over the whole mosaic is $\sim$30%." (Imaging)
- Limitation (authors): Resolved gradients in physical conditions and SEDs on the ~7'' synthesised beam scale cannot be constrained without 7 m (ACA) data; SEDs and spectral indices can only be reliably extracted on primary-beam scales.  
  > "The present ALMA data cannot, however, be used to constrain resolved gradients in physical conditions across the PDR." (Comparison with the ATCA mosaics); "The combination of 7 m (ALMA Compact Array) observations with the present 12 m observations could allow for such a resolved multi-frequency analysis." (Comparison with the ATCA mosaics)
- Limitation (authors): Pure-chi2 imaging (lambda=0) fits noise to some extent, creating positive-definite noise in the template that slightly biases the normalisation slope downwards (a_nu0 = 0.96 +/- 0.005).  
  > "The slopes $a_{\nu_\circ}$ are slightly biased downwards, with $a_{\nu_\circ} = 0.96\pm0.005$ for $\nu_\circ = 36.63\,$GHz averaged over all fields, which results from the use of the pure-$\chi^2$ model image as template." (Extraction of the intra-band diffuse emission spectrum)
- Limitation (authors): The Airy-disk approximation to the ALMA Band 1 primary beam causes imperfect single-field point-source subtraction (~5% residuals) for the bright off-axis source DoAr 21, requiring a 4-field joint fit.  
  > "We attribute the imperfect point-source subtraction for DoAr 21 in single-field point-source fits (with $\lesssim 5\%$ residuals) to the accuracy of the Airy disk approximation to the ALMA primary beam." (Point-source subtraction)
- Caveat (inferred, ours): Flux-loss correction relies on the IRAC 3.6 um template power spectrum matching the Band 1 EME power spectrum, even though the paper demonstrates that the two power spectra diverge by a factor of ~2 between ~100'' and ~20'' scales.
- Caveat (inferred, ours): Truncation of unregularised (lambda=0) gpu-uvmem optimisation at exactly 10 iterations is an ad-hoc regularisation choice whose sensitivity on the small-scale clumping and spectral index is not systematically explored.

## Reproducibility

- Data public (paper): ALMA program 2023.1.00265.S calibration details available in the ALMA science archive; Spitzer SEIP and Herschel Gould Belt Survey data obtained from public archives  
  > "Full details on the calibration can be obtained through the ALMA science archive, in the quality assurance reports." (Data acquisition); "The IRAC images were obtained from the Set of Enhanced Imaging Products (SEIP), which is part of the Spitzer Heritage Archive." (Cross-correlations with the Spitzer-IRAC maps)
- Products in archive: _not stated_
- Code: Uses open-source packages gpu-uvmem, pyralysis, and iminuit (cited), plus commercial/proprietary PixInsight and StarXTerminator (URLs given); project-specific analysis scripts are not stated as released.  
  > "We used the `gpu-uvmem` package (cite: Casassus2006ApJ...639..951C; Carcamo2018A&C....22...16C) to minimise the objective function," (Imaging); "These were subtracted in the $uv$ plane, handling the raw (non-gridded) visibility data with the `pyralysis` package (cite: casassus_carcamo2022MNRAS.513.5790C)." (Point-source subtraction); "Star subtraction was performed using ` StarXTerminator`, an AI-based tool that employs neural networks to remove stellar sources from astronomical images." (Point-source subtraction in the IRAC images)
- Missing: Exact J2000 coordinates of the 16 mosaic field centres and the fitted positions of SR 4, ISO-Oph-17, and DoAr 21
- Missing: Exact rest frequencies used for the C56alpha to C53alpha line stacking
- Missing: Star-subtracted Spitzer-IRAC FITS templates (since StarXTerminator + PixInsight is commercial closed-source neural-network software)
- Data volume (inferred): ~50-150 GB of raw/calibrated ALMA Band 1 visibilities (4 execution blocks, 36-39 antennas, 16 fields, 4 spws x 1920 channels)
- Score (inferred): 78/5, The calibration versions, flagging, equations for visibility-plane point-source fitting, cross-correlation, and comb matched-filtering are explicitly written out, and imaging parameters for both gpu-uvmem and CASA-tclean are well documented. Reproduction is slightly hindered by reliance on proprietary AI star-removal software (PixInsight/StarXTerminator) for the IRAC templates and unstated fitted coordinates for the subtracted point sources.
- Rediscovery candidate: yes, The ALMA dataset (2023.1.00265.S) is standard pipeline-calibrated data, the mathematical equations for uv-plane point-source fitting, template cross-correlation, and comb filtering are fully specified in the text, and the main results (point-source fluxes/spectral indices, diffuse EME spectral indices, CRRL upper limit) are concrete numeric targets.

## Links

- Method: (cite: Casassus2006ApJ...639..951C; Carcamo2018A&C....22...16C) (gpu-uvmem non-parametric visibility-plane synthesis imaging package)
- Method: (cite: casassus_carcamo2022MNRAS.513.5790C) (pyralysis visibility handling, point-source subtraction, and visibility simulation package)
- Method: (cite: Ali-Haimoud2014; Ali-Haimoud2015MNRAS.447..315A) (Matched-filter formalism for searching for PAH rotational frequency combs)
- Method: (cite: Casassus2021MNRAS.502..589C) (Linear mosaic attenuation map formalism and ATCA prior-based imaging of rho Oph W)
- Companion: companion article (in prep.) (Interpretation and modelling of the measured multi-frequency SEDs in terms of the spinning dust hypothesis)
- Related: Herschel Gould Belt Survey (HGBS)
- Related: Spitzer Heritage Archive Set of Enhanced Imaging Products (SEIP)

## Checks

```json
{
 "quotes": 200,
 "quotes_ok": 200,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 5,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 23,
 "numeric_problems": 0,
 "fill": {
  "facts": 118,
  "stated": 88,
  "rate": 0.746
 },
 "evidence_ok": true
}
```
