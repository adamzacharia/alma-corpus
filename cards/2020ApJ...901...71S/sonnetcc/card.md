# Low-level Carbon Monoxide Line Polarization in Two Protoplanetary Disks: HD 142527 and IM Lup

`2020ApJ...901...71S` | The Astrophysical Journal 2020 | first author: Stephens, Ian W. | arXiv: 2008.04952 | DOI: 10.3847/1538-4357/abaef7

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: Can CO, 13CO and C18O (J=2-1) line polarization from the Goldreich-Kylafis effect be detected, or tightly limited, in the protoplanetary disks HD 142527 and IM Lup, and how does 1.3 mm continuum polarization compare with 870 um?  
  > "We attempt to observe CO(2–1), $^{13}$CO(2–1), and C$^{18}$O(2–1) line polarization toward HD 142527 and IM Lup, which are large, bright protoplanetary disks." (abstract); "We also compare our continuum polarization at 1.3 mm to observations at 870 $\mu$m from previous studies." (abstract)
- Target **HD 142527**: coordinates _not stated_; z/distance 157 pc  
  > "HD 142527 is a close binary system located 157 pc away (cite: Arun2019)." (Targets); distance from Arun2019  
  > "HD 142527 is a close binary system located 157 pc away (cite: Arun2019)." (Targets)
- Target **IM Lup**: coordinates _not stated_; z/distance 158 pc  
  > "IM Lup is a K5 Class II T Tauri star located 158 pc away (cite: Alcala2017; Gaia2018)." (Targets); distance from Alcala2017; Gaia2018  
  > "IM Lup is a K5 Class II T Tauri star located 158 pc away (cite: Alcala2017; Gaia2018)." (Targets)

## Data provenance

- ALMA projects: 2018.1.01172.S, 2015.1.00425.S, 2016.1.00712.S
- bands: Band 6 (1.3 mm)  
  > "Observations were conducted on 2019 April 29 using ALMA Band 6 (1.3 mm) under the project code 2018.1.01172.S (PI: I. Stephens)." (Observing Details and Data Reduction)
- frequencies and spectral setup: Four basebands: continuum baseband centred at 234.5 GHz (2.0 GHz wide); three 59 MHz basebands centred on CO(2-1), 13CO(2-1), C18O(2-1) with 0.079, 0.083, 0.083 km/s spectral resolution; correlator Hanning smoothing, default averaging of 2 channels for line basebands  
  > "One baseband was dedicated for the 1.3 mm dust continuum emission, and it was centered at 234.5 GHz and had a bandwidth of 2.0 GHz." (Observing Details and Data Reduction); "These basebands provided spectral resolutions of 0.079, 0.083, and 0.083 km s$^{-1}$, respectively." (Observing Details and Data Reduction); "We used the default correlator spectral averaging for each baseband, which is 2 channels averaged for the high spectral resolution basebands and no channels averaged for the continuum baseband." (Observing Details and Data Reduction)
- continuum bandwidth: 2.150 GHz total (continuum baseband plus line-free channels of the other three basebands)  
  > "we combined the continuum baseband with the line-free channels of the other three basebands for a total bandwidth of 2.150 GHz." (Observing Details and Data Reduction)
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15 to 704 m, 46 antennas  
  > "ALMA was using 46 antennas with baselines ranging between 15 and 704 m." (Observing Details and Data Reduction)
- angular resolution: ~0.5'' (~80 au); 1.3 mm continuum beam 0.51'' x 0.45'' (HD 142527), 0.51'' x 0.44'' (IM Lup); line beams ~0.56-0.60''; re-imaged 870 um HD 142527 data 0.27'' x 0.24''  
  > "at 0.5$\ensuremath{''}$ ($\sim$80 au) resolution" (abstract); "The final resolution was 0.27$''$ $\times$ 0.24$''$." (Continuum)
- max recoverable scale: _not stated_
- sensitivity: CO(2-1) Stokes QUV noise 3.3 mJy per channel; continuum Stokes I rms 0.037 (HD 142527) and 0.022 (IM Lup) mJy/beam; QUV continuum 0.022 mJy/beam (Table 1)  
  > "the noise across the entire CO(2–1) Stokes $QUV$ cubes are fit very well with a Gaussian, with an average value of 0.0 $\pm$ 3.3 mJy." (Stokes $QUV$ Noise Characterization); "The final continuum and line synthesized beams and noise levels are reported in Table" (Observing Details and Data Reduction)
- time on source: 1 hour per science target  
  > "The total integrated time over each science target was 1 hour." (Observing Details and Data Reduction)
- observing dates: 2019 April 29  
  > "Observations were conducted on 2019 April 29 using ALMA Band 6 (1.3 mm)" (Observing Details and Data Reduction)
- pi or archival as stated: New observations, PI I. Stephens (2018.1.01172.S); 870 um HD 142527 comparison data are archival (2015.1.00425.S, PI A. Kataoka), obtained as calibrated data via the ALMA helpdesk  
  > "under the project code 2018.1.01172.S (PI: I. Stephens)" (Observing Details and Data Reduction); "we requested and downloaded calibrated data via the ALMA helpdesk (project code 2015.1.00425.S, PI: A. Kataoka)." (Continuum)
- Line: CO J=2-1 (not stated)
- Line: 13CO J=2-1 (not stated)
- Line: C18O J=2-1 (not stated)
- External data: 870 um ALMA polarization images of IM Lup (0.50'' x 0.40''), downloaded from the online version of the paper, used for the continuum comparison  
  > "we downloaded the polarization images provided in the online version of (cite: Hull2018), which have a resolution of 0.50$''$ $\times$ 0.40$''$." (Continuum) [from Hull2018]
- External data: Disk models (stellar mass, inclination, position angle, characteristic radius) used as GoFish and morphological-model inputs  
  > "We find estimates for most these parameters from disk models from (cite: PerezS2015) and (cite: Cleeves2016)." (Stacking via `GoFish`) [from PerezS2015; Cleeves2016]
- External data: HD 142527 distance 157 pc  
  > "HD 142527 is a close binary system located 157 pc away (cite: Arun2019)." (Targets) [from Arun2019]
- External data: IM Lup distance 158 pc  
  > "IM Lup is a K5 Class II T Tauri star located 158 pc away (cite: Alcala2017; Gaia2018)." (Targets) [from Alcala2017; Gaia2018]
- External data: Surface density profile form for the morphological model  
  > "We assume a surface density profile that follows the form in (cite: Andrews2011)" (Morphological Model) [from Andrews2011]
- External data: Predicted GK line polarization of disks (PORTAL, CO(3-2)), compared with the observed limits  
  > "So far, (cite: Lankhaar2020) has the only model that predicts line polarization for a disk." (Summary and Discussion) [from Lankhaar2020]
- Simulation/model as data: Morphological model of Stokes Q and U for purely elliptical (or radial) polarization, with surface density following Andrews et al. profile, constant Pfrac, used to choose stacking quadrants (not a GK model)  
  > "we create model images of the expected Stokes $Q$ and $U$ maps for purely elliptical polarization for HD 142527 and IM Lup, which may be expected for a toroidal field." (Morphological Model); "This notably is not a model of the GK effect, as it ignores very important parameters such as the optical depth." (Morphological Model)

## Processing

### Calibration

- pipeline or manual: Manual calibration by North American ARC staff in CASA  
  > "Delivered data were manually calibrated by the North American ARC staff using the Common Astronomy Software Applications (CASA) package (cite: McMullin2007)." (Observing Details and Data Reduction)
- casa version: CASA v5.6.0 (stated for imaging and self-calibration; calibration CASA version not stated)  
  > "We imaged the continuum and spectral lines using CASA v5.6.0." (Observing Details and Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1427–4206 flux and bandpass; J1610–3958 phase; J1517–2422 polarization  
  > "J1427–4206 was used as the flux and bandpass calibrator, J1610–3958 was the phase calibrator, and J1517–2422 was the polarization calibrator." (Observing Details and Data Reduction)
- flux scale uncertainty: 10% absolute flux; polarization uncertainties from D-terms less than 5%  
  > "ALMA Band 6 observations have a typical absolute flux uncertainty of 10%, and the polarization uncertainties as determined by the D-terms were less than a 5%." (Observing Details and Data Reduction)
- self calibration: Three phase-only rounds on continuum Stokes I, solution intervals infinite, 25 s, 10 s; solutions applied to continuum QUV and line IQUV  
  > "We ran three phase-only self-calibration iterations on the continuum Stokes $I$ data." (Observing Details and Data Reduction); "The solution intervals used for the first, second, and third self-calibrations were infinite, 25 s, and 10 s, respectively." (Observing Details and Data Reduction)

### Imaging

- task: CASA tclean  
  > "To clean the images, we use the CASA task" (Observing Details and Data Reduction)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "using Briggs weighting with a robust parameter of 0.5." (Observing Details and Data Reduction)
- uv taper: _not stated_
- cell size: 0.11''  
  > "The pixel size for our maps is 0.11$''$." (Observing Details and Data Reduction)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum fit to each baseband's line-free channels and subtracted from the line data  
  > "For each spectral line, we subtracted the continuum emission by fitting the continuum using the baseband’s line-free channels." (Observing Details and Data Reduction)
- line free channels: _not stated_
- primary beam correction: All images primary-beam corrected (noise characterisation done before correction)  
  > "All images in this paper have been corrected for the primary beam." (Observing Details and Data Reduction)
- array combination: _not stated_
- smoothing: 870 um HD 142527 image smoothed to the 1.3 mm resolution for comparison; same for IM Lup 870 um images  
  > "we smoothed the 870 $\mu$m to have the same resolution as the 1.3 mm observations." (Continuum)
- final beam: See Table 1: continuum 0.51'' x 0.45'' PA 64.5 deg (HD 142527) and 0.51'' x 0.44'' PA 69.5 deg (IM Lup); lines 0.56''-0.60''  
  > "The final continuum and line synthesized beams and noise levels are reported in Table" (Observing Details and Data Reduction)
- final rms: _not stated_

### Inherited from earlier work

- Channel-to-channel covariance from Hanning smoothing plus 2-channel averaging equals 0.3 times the variance  
  > "As shown in (cite: Loomis2018), this Hanning smoothing plus a spectral averaging of 2" (Stokes $QUV$ Noise Characterization) [from Loomis2018]
- De-biasing of polarized intensity  
  > "We de-bias the values following (cite: Hull2015)." (Observing Details and Data Reduction) [from Hull2015]
- Optical depth from the ratio of brightness temperatures  
  > "The optical depth can be estimated from the ratio of brightness temperatures (cite: Lyo2011)." (Optical Depth) [from Lyo2011]
- Elliptical polarization pattern image construction  
  > "Following (cite: Yang2019), we create an image of an elliptical polarization pattern for a disk with inclination, $i$." (Morphological Model) [from Yang2019]
- Disk parameters (mass, inclination, PA, Rc) taken from published disk models  
  > "We find estimates for most these parameters from disk models from (cite: PerezS2015) and (cite: Cleeves2016)." (Stacking via `GoFish`) [from PerezS2015; Cleeves2016]
- Surface density profile form  
  > "We assume a surface density profile that follows the form in (cite: Andrews2011)" (Morphological Model) [from Andrews2011]

### Not stated but needed to reproduce (our reading)

- tclean parameters other than weighting and robust: niter, threshold, deconvolver, masks, image size, uv-taper, spectral grid and rest frequencies
- Which channels were treated as line-free for continuum subtraction and the fit order
- Reference antenna, gain tables and spw/channel selections used in the three self-calibration rounds
- CASA version used by the ARC for manual calibration and the delivered calibration scripts
- Velocity ranges used for the moment 0 maps and for the 90% peak r_max definition details
- GoFish version and the 'default' stacking options (e.g. resample, method, centroid handling)
- Exact aperture-search script (channel start range, aperture centering grid, tie-breaking), only described in words
- How the 870 um HD 142527 data were calibrated and which imaging settings were used (referred to as the same as the 1.3 mm data)
- Position-dependent upper-limit map settings beyond velocity intervals (masks, smoothing)

## Analysis recipe

1. **Self-calibrate on continuum and transfer solutions**: Three phase-only self-calibration iterations on continuum Stokes I, with solutions applied to continuum Stokes QUV and line Stokes IQUV  
  > "We ran three phase-only self-calibration iterations on the continuum Stokes $I$ data." (Observing Details and Data Reduction); "The self-calibration solutions from the continuum Stokes $I$ were then applied to the continuum Stokes $QUV$ and the spectral line Stokes $IQUV$." (Observing Details and Data Reduction)
   - software: CASA
   - parameter: Solution intervals: infinite, 25 s, 10 s  
  > "The solution intervals used for the first, second, and third self-calibrations were infinite, 25 s, and 10 s, respectively." (Observing Details and Data Reduction)
   - fitting: _not stated_
   - validation: SNR improvement by a factor of 6 (HD 142527) and 3 (IM Lup)  
  > "Self-calibration improved the continuum Stokes $I$ signal-to-noise ratio for HD 142527 and IM Lup by a factor of 6 and 3, respectively." (Observing Details and Data Reduction)
2. **Image continuum and line cubes**: tclean with Briggs weighting robust 0.5; continuum made from continuum baseband plus line-free channels; line continuum subtracted; primary-beam corrected  
  > "using Briggs weighting with a robust parameter of 0.5." (Observing Details and Data Reduction); "All images in this paper have been corrected for the primary beam." (Observing Details and Data Reduction)
   - software: CASA, tclean
   - parameter: Robust = 0.5; pixel size 0.11''; continuum bandwidth 2.150 GHz  
  > "The pixel size for our maps is 0.11$''$." (Observing Details and Data Reduction); "for a total bandwidth of 2.150 GHz." (Observing Details and Data Reduction)
   - fitting: _not stated_
   - validation: _not stated_
3. **Build polarization maps (P_I, Pfrac, chi)**: Compute polarized intensity, polarization fraction and position angle from Stokes IQU, with de-biasing following Hull et al. 2015  
  > "From the Stokes $IQU$ images, we constructed polarized intensity ($P_I$), $P_{\text{frac}}$, and position angle ($\chi$) maps where:" (Observing Details and Data Reduction); "We de-bias the values following (cite: Hull2015)." (Observing Details and Data Reduction)
   - fitting: _not stated_
   - validation: _not stated_
4. **Characterise Stokes QUV noise**: Gaussian fit of CO(2-1) QUV cube noise before primary-beam correction, moment 6 (rms) maps for spatial variation, and autocorrelation along the spectral axis  
  > "We thus analyze the CO(2–1) Stokes $QUV$ noise on the maps before the primary beam correction." (Stokes $QUV$ Noise Characterization); "We checked the autocorrelation of our $QUV$ cubes to search for serial correlations for the noise along the spectral axis of these data." (Stokes $QUV$ Noise Characterization)
   - fitting: _not stated_
   - validation: Noise is Gaussian, spatially and spectrally uniform, with covariance 0.3 between consecutive channels  
  > "Correlation was found between consecutive channels, but no correlation was detected for the rest of the bandwidth" (Stokes $QUV$ Noise Characterization)
5. **Compare 1.3 mm and 870 um continuum polarization**: Re-image archival 870 um HD 142527 data (calibrated by helpdesk) the same way, regrid and smooth to the common resolution; use published 870 um IM Lup images; compare polarized intensity, Pfrac ratio and angle difference  
  > "We re-imaged the calibrated data in the same manner as discussed in Section" (Continuum); "The third panel shows the ratio of $P_{\text{frac}}$ between 1.3 mm and 870 $\mu$m, and the fourth shows the polarization position angle differences between 1.3 mm and 870 $\mu$m." (Continuum)
   - software: CASA
   - parameter: HD 142527 regridded to 0.06'' pixels; IM Lup to 0.1'' pixels  
  > "We regridded the 1.3 mm observations to have the same pixel size used at 870 $\mu$m (0.06$''$)" (Continuum); "we regridded the 1.3 mm observations to have the same pixel size that we used at 870 $\mu$m (0.1$''$)" (Continuum)
   - fitting: _not stated_
   - validation: _not stated_
6. **Estimate line optical depths**: Solve numerically the line-ratio equation R = F1/F2 for tau, per channel and from integrated intensity maps, using isotopic ratios  
  > "The optical depth was solved for numerically." (Optical Depth); "We made optical depth maps (not shown) both channel by channel and from the integrated intensity maps of each line." (Optical Depth)
   - assumption: [12CO]/[13CO] = 70 and [12CO]/[C18O] = 500  
  > "= 70 and \[$^{12}$CO\]/\[C$^{18}$O\] = 500" (Optical Depth)
   - assumption: Flux-to-brightness-temperature conversion roughly identical for the lines (varies <1%), so flux ratio is used  
  > "(vary by less than 1%)" (Optical Depth)
   - fitting: _not stated_
   - validation: _not stated_
7. **Model expected Q and U morphology**: Build elliptical-polarization Q and U maps with Stokes I following a surface-density profile, smoothed to the beam and normalised to U_max, to choose stacking quadrants  
  > "Following (cite: Yang2019), we create an image of an elliptical polarization pattern for a disk with inclination, $i$." (Morphological Model); "We then smoothed each map to have the same resolution as our observations." (Morphological Model)
   - parameter: HD 142527: PA = 160 deg, i = 28 deg, Rc = 200 au; IM Lup: PA = 144 deg, i = 48 deg, Rc = 100 au; gamma = 1  
  > "For HD 142527 we assume PA = 160$^\circ$ and $i$ = 28$^\circ$ (cite: PerezS2015), and for IM Lup we assume PA = 144$^\circ$ and $i$ = 48$^\circ$ (cite: Cleeves2016)." (Morphological Model); "For HD 142527 and IM Lup, we assume $R_c$ is 200 and 100 au, respectively (cite: PerezS2015; Cleeves2016)." (Morphological Model)
   - assumption: Pfrac constant across the disk; surface density proportional to Stokes I  
  > "For this model, we assume $P_{\text{frac}}$ to be constant across the disk." (Morphological Model)
   - fitting: _not stated_
   - validation: _not stated_
8. **Stack Stokes parameters along Keplerian rotation**: Use GoFish to align spectra to deprojected Keplerian centroid velocities, stacking over the whole disk and over 90 deg quadrants (two starting angles, alternating rmin), for CO, 13CO, C18O  
  > "A signal can be stacked for the Stokes parameters by aligning their spectra to common centroid velocities based on a disk’s deprojected Keplerian rotational profile." (Stacking via `GoFish`); "we select four 90$^\circ$ quadrants where we start at PA$_{\text{red}}$, and another four where we start at PA$_{\text{red}}$ $-$ 45$^\circ$." (Stacking via `GoFish`)
   - software: GoFish
   - parameter: HD 142527: M* = 2.8 Msun, PA_red = 160 deg, i = 28 deg, d = 157 pc; IM Lup: M* = 1 Msun, PA_red = 144 deg, i = 48 deg, d = 158 pc; z0 = 0.1'' for both; IM Lup x-offset 0.8''  
  > "For both disks we assume $z_0$ = 0.1$''$." (Stacking via `GoFish`); "For HD 142527, we assume $M_\star$ = 2.8 $M_\odot$, PA$_{\text{red}}$ = 160$^\circ$, $i$ = 28$^\circ$, and $d$ = 157 pc." (Stacking via `GoFish`)
   - parameter: rmax where Stokes I drops to 90% of peak moment 0 value, rounded to 3'' (HD 142527) and 4'' (IM Lup); rmin alternates 0 and 0.17'' (HD 142527) or 0 and 0.5'' (IM Lup)  
  > "We choose a value where the Stokes $I$ flux drops to 90% of the peak value of the Stokes $I$ moment 0 map." (Stacking via `GoFish`)
   - parameter: Other GoFish inputs left at defaults  
  > "were all assumed to be their defaults." (Stacking via `GoFish`)
   - assumption: Keplerian rotation with inputs from published disk models  
  > "We find estimates for most these parameters from disk models from (cite: PerezS2015) and (cite: Cleeves2016)." (Stacking via `GoFish`)
   - fitting: _not stated_
   - validation: No significant signal in any quadrant or radius choice tried  
  > "No significant detection was found for any quadrant." (Stacking via `GoFish`)
9. **Search for Q signal in optimised circular apertures**: Inspect average spectra in circular apertures, then a custom script varying aperture size and position to maximise SNR_Q = |sum Q| / sigma over N consecutive channels, with channel covariance included  
  > "We then developed a script that alters the size and position of the circular aperture to find the location with the highest signal to noise." (Searching for Signal within an Aperture); "there exists a covariance between consecutive channels that is 0.3 times the variance in the spectrum." (Searching for Signal within an Aperture)
   - parameter: Aperture centred on a pixel with integer radii  
  > "the aperture was centered on a pixel and radii had sizes that were integers." (Searching for Signal within an Aperture)
   - fitting: _not stated_
   - validation: Moment 0 Stokes Q map checked for the fraction of pixels above 2 sigma compared with the 2.3% expected for pure noise  
  > "we note that for an image that is purely noise, only 2.3% of the area is expected to be above the 2$\sigma$ value." (Searching for Signal within an Aperture)
10. **Monte Carlo test of aperture-search false-signal rate**: Run the same SNR_Q maximisation at each 0.11'' pixel within 15'' of the map centre over a range of aperture radii and channel windows, to obtain the expected maximum SNR distribution  
  > "We used a Monte Carlo simulation to find the typical SNR that one would expect at each pixel of our CO(2–1) Stokes $Q$ maps." (Searching for Signal within an Aperture); "We focused on pixels within a radius of 15$\ensuremath{''}$ from the center of the map" (Searching for Signal within an Aperture)
   - parameter: Aperture radii 1 to 27 pixels; 2 to 32 consecutive channels (~0.16 to 2.5 km/s)  
  > "We tried circular apertures with integer radii sizes between 1 and 27 pixels" (Searching for Signal within an Aperture); "we looked for the highest SNR$_Q$ possible for 2 to 32 consecutive channels" (Searching for Signal within an Aperture)
   - fitting: _not stated_
   - validation: Off-disk pixels reach SNR_Q comparable to the on-disk detections, so the detections are marginal  
  > "we consider these Stokes $Q$ detections as marginal." (Searching for Signal within an Aperture)
11. **Derive pixel-by-pixel 3 sigma Pfrac upper limits**: For each unmasked pixel find the channel sum maximising sum I over N channels and compute 3 sigma_PI sqrt(1.6N-0.6)/sum I, for several velocity intervals  
  > "We first mask out pixels where the moment 0 maps" (Constraining the Polarization Percentage of the Observations); "We generate multiple 3$\sigma$ upper limit maps, each for $N$ channels spanning velocity intervals that are a factor of 0.5 km s$^{-1}$." (Constraining the Polarization Percentage of the Observations)
   - parameter: Velocity intervals 0.5, 1, 1.5 km/s shown; sigma_PI = sigma_Q = sigma_U; pixels with moment 0 SNR < 10 masked  
  > "where the polarized intensity sensitivity $\sigma_{\text{PI}}$ = $\sigma_Q$ = $\sigma_U$." (Constraining the Polarization Percentage of the Observations)
   - fitting: _not stated_
   - validation: _not stated_
12. **Derive upper limits from stacked spectra and test robustness**: Apply the same upper-limit equation to GoFish stacked spectra (whole disk and quadrants) using the noise of the Stokes V stacked spectrum; one thousand Monte Carlo runs perturbing mass, inclination and PA  
  > "We take $\sigma_{\text{PI}}$ to be the noise of the Stokes $V$ stacked spectrum." (Constraining the Polarization Percentage of the Observations); "In these runs, we randomly add Gaussian noise to the mass, inclination, and position angles because the Keplerian profile strongly depends on these parameters." (Constraining the Polarization Percentage of the Observations)
   - software: GoFish
   - parameter: Gaussian sigma of 15% for mass and 5 deg for inclination and PA  
  > "we assume that $\sigma$ of the Gaussian noise is 15% of the estimated masses of the disks." (Constraining the Polarization Percentage of the Observations)
   - fitting: _not stated_
   - validation: Medians and means of the Monte Carlo values almost identical to the quoted values; typical standard deviation <10%  
  > "the typical standard deviation for the 1000 runs is $<$10% of its value." (Constraining the Polarization Percentage of the Observations)

## Software

- **CASA** v5.6.0: Imaging, self-calibration, tclean (manual calibration by ARC staff with CASA)  
  > "We imaged the continuum and spectral lines using CASA v5.6.0." (Observing Details and Data Reduction)
- **tclean** CASA v5.6.0: Cleaning images with Briggs weighting, robust 0.5  
  > "using Briggs weighting with a robust parameter of 0.5." (Observing Details and Data Reduction)
- **GoFish** : Stacking Stokes parameters along the Keplerian rotation pattern  
  > "A signal can be stacked for the Stokes parameters by aligning their spectra to common centroid velocities based on a disk’s deprojected Keplerian rotational profile." (Stacking via `GoFish`)
- **APLpy** : Listed in the Software section; specific use not stated  
  > "APLpy (cite: Robitaille2012), CASA v5.6.0, (cite: McMullin2007), GoFish (cite: GoFish), PySpecKit (cite: Ginsburg2011)" (Software)
- **PySpecKit** : Listed in the Software section; specific use not stated  
  > "APLpy (cite: Robitaille2012), CASA v5.6.0, (cite: McMullin2007), GoFish (cite: GoFish), PySpecKit (cite: Ginsburg2011)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total CO(2-1) polarization fraction, HD 142527 (abstract) | 1.57 | 0.18 | % | 9 | The total CO(2–1) polarization fractions are 1.57 $\pm$ 0.18% and 1.01 $\pm$ 0.10% for HD 142527 and IM Lup, respectively. |
| De-biased CO(2-1) Pfrac at max-SNR_Q aperture, HD 142527 (text/summary value) | 1.56 | 0.18 | % | 9 | the de-biased $P_{\text{frac}}$ is 1.56 $\pm$ 0.18% and 1.01 $\pm$ 0.10%, respectively. |
| De-biased CO(2-1) Pfrac at max-SNR_Q aperture, IM Lup | 1.01 | 0.10 | % | 9 | the de-biased $P_{\text{frac}}$ is 1.56 $\pm$ 0.18% and 1.01 $\pm$ 0.10%, respectively. |
| Sum of Stokes Q over pink channels, HD 142527 and IM Lup | 10.8 and 9.9 (SNR_Q = 8.7 and 9.6) | 1.2 and 1.0 | mJy/beam | 9 | 10.8 $\pm$ 1.2 mJy bm$^{-1}$ (SNR$_Q$ = 8.7) and 9.9 $\pm$ 1.0 mJy bm$^{-1}$ (SNR$_Q$ = 9.6), respectively. |
| Sum of Stokes U over the same channels, HD 142527 and IM Lup | 2.7 and 3.7 | 1.5 and 1.2 | mJy/beam | 9 | are 2.7 $\pm$ 1.5 mJy bm$^{-1}$ and 3.7 $\pm$ 1.2 mJy bm$^{-1}$, respectively. |
| Position angle chi at max-SNR_Q aperture, HD 142527 and IM Lup | 6.9 and 10.1 | 3.9 and 3.2 | deg | 9 | The position angles $\chi$ are 6.9$^\circ$ $\pm$ 3.9$^\circ$ and 10.1$^\circ$ $\pm$ 3.2$^\circ$, respectively. |
| Monte Carlo mean maximum SNR_Q per pixel, HD 142527 | 4.7 | standard deviation 0.9 | dimensionless | 10 | For HD 142527, the mean SNR$_Q$ for each pixel is 4.7 with a standard deviation of 0.9. |
| Monte Carlo mean maximum SNR_Q per pixel, IM Lup | 5.0 | standard deviation 1.0 | dimensionless | 10 | For IM Lup, the mean SNR$_Q$ for each pixel is 5.0 with a standard deviation of 1.0 |
| Highest Stokes U SNR within the gaseous disks (Monte Carlo), HD 142527 and IM Lup | 6.9 and 8.0 | not stated | dimensionless | 10 | the highest values of SNR$_U$ within the areas of the gaseous disks are 6.9 and 8.0 for HD 142527 and IM Lup respectively. |
| Moment 0 QUV sensitivity, HD 142527 | 0.78 | not stated | mJy/beam km/s | 9 | given the sensitivity in the $QUV$ moment 0 maps is $\sigma$ = 0.78 mJy bm$^{-1}$ km s$^{-1}$ |
| CO(2-1) Stokes QUV cube noise | 0.0 mean, 3.3 rms | 3.3 | mJy | 4 | with an average value of 0.0 $\pm$ 3.3 mJy. |
| Self-calibration SNR gain, HD 142527 and IM Lup | 6 and 3 | not stated | dimensionless | 1 | Self-calibration improved the continuum Stokes $I$ signal-to-noise ratio for HD 142527 and IM Lup by a factor of 6 and 3, respectively. |
| CO(2-1) optical depth, HD 142527 | >30 almost everywhere, as low as 14 at disk center | not stated | dimensionless | 6 | We find that CO(2–1) optical depths are $>$30 for all locations except the center of the disk, where the optical depth is as low as 14. |
| 13CO(2-1) optical depth range, HD 142527 | ~1 to 7 | not stated | dimensionless | 6 | range from $\sim$1 to 7, and the optical depth for C$^{18}$O(2–1) is between 0.1 and 1. |
| C18O(2-1) optical depth range, HD 142527 | 0.1 to 1 | not stated | dimensionless | 6 | range from $\sim$1 to 7, and the optical depth for C$^{18}$O(2–1) is between 0.1 and 1. |
| CO(2-1) optical depth, IM Lup | typically ~40, range ~10-100 | not stated | dimensionless | 6 | we find that CO(2–1) optical depths are typically about 40, but range from about 10–100. |
| Continuum Pfrac ratio 1.3 mm / 870 um and angle difference in northern HD 142527 | ratio up to ~5; angle difference up to 90 deg | not stated | dimensionless (ratio); deg | 5 | reaching values as high as $\sim$5, and the difference in polarization angle is as large as $90^\circ$ (i.e., perpendicular). |
| Pixel-wise 3 sigma Pfrac upper limits at brightest continuum spots, HD 142527 | <3% CO(2-1) and 13CO(2-1); <4% C18O(2-1) | not stated | % | 11 | the polarization 3$\sigma$ upper limits are typically less than 3% for CO(2–1) and $^{13}$CO(2–1), and 4% for C$^{18}$O(2–1). |
| Pixel-wise 3 sigma Pfrac upper limits at brightest continuum spots, IM Lup | <3% CO(2-1); <4% 13CO(2-1); <12% C18O(2-1) | not stated | % | 11 | the polarization 3$\sigma$ upper limits are typically less than 3% for CO(2–1), 4% for $^{13}$CO(2–1), and 12% for C$^{18}$O(2–1). |
| GoFish stacked 3 sigma Pfrac limits, CO(2-1) (HD 142527 whole disk, quadrants; IM Lup whole disk, quadrants) | 0.2-0.3%; 0.3-0.9%; 0.2-0.3%; 0.3-0.5% | not stated | % | 12 | 0.2% – 0.3% / 0.3% – 0.9% / 0.2% – 0.3% / 0.3% – 0.5% |
| GoFish stacked 3 sigma Pfrac limits, 13CO(2-1) (HD 142527 whole disk, quadrants; IM Lup whole disk, quadrants) | 0.3-0.4%; 0.4-0.9%; 0.3-0.5%; 0.6-1.0% | not stated | % | 12 | 0.3% – 0.4% / 0.4% – 0.9% / 0.3% – 0.5% / 0.6% – 1.0% |
| GoFish stacked 3 sigma Pfrac limits, C18O(2-1) (HD 142527 whole disk, quadrants; IM Lup whole disk, quadrants) | 0.4-0.5%; 0.5-1.1%; 1.1-1.4%; 1.9-3.3% | not stated | % | 12 | 0.4% – 0.5% / 0.5% – 1.1% / 1.1% – 1.4% / 1.9% – 3.3% |
| Stacking limit improvement over pixel-by-pixel analysis | up to a factor of ~10 lower | not stated | dimensionless | 12 | the stacking method performs better, having lower 3$\sigma$ upper limits by a factor of up to $\sim$10. |

## Qualitative findings

- Polarization is detected only for CO(2-1) Stokes Q and only marginally; 13CO and C18O show nothing despite better optical depths  
  > "Despite the above expectations for optical depth, polarization is only detected for CO(2–1), and only for small parts of the disk." (Summary and Discussion)
- The lines are thermalized in the midplane, so any detected polarization would come from above the midplane  
  > "However, the lines are thermalized in the midplane, suggesting the detected line polarization would come from regions above the midplane." (Summary and Discussion)
- HD 142527 northern dust trap polarization changes strongly between 870 um and 1.3 mm  
  > "The polarization toward the northern dust trap in HD 142527 shows a rapid change in the morphology and $P_{\text{frac}}$ with wavelength." (Summary and Discussion)
- First published attempt to resolve linear line polarization in circumstellar disks  
  > "These observations are the first published attempt to resolve linear line polarization for circumstellar disks." (Summary and Discussion)

## Claim tuples

- H: GK-effect linear polarization of CO(2-1), 13CO(2-1) or C18O(2-1) is detectable in HD 142527 and IM Lup | E: Spatial averaging in optimised apertures with spectral integration of Stokes Q, U, V cubes, plus Monte Carlo test of the search | R: Q signal in CO(2-1) in both disks (SNR_Q 8.7 and 9.6), with comparable off-disk SNR in Monte Carlo; no U or V signal and no signal in 13CO or C18O | F: The CO(2-1) Stokes Q signals are marginal detections, insufficient to infer a polarization or field pattern | **partially**
- H: Keplerian-rotation stacking of Stokes parameters reveals line polarization | E: GoFish stacking over whole disks and 90 deg quadrants with a range of radii and wedges | R: No significant signal in Stokes Q, U, V | F: No polarization found by stacking; it yields 3 sigma Pfrac upper limits ~0.2-3.3% depending on line and region | **refuted**
- H: Line polarization fraction can be constrained across the disks at the observing resolution | E: Per-pixel 3 sigma upper limits over velocity intervals of 0.5-1.5 km/s and stacked upper limits | R: Pixel-wise limits typically <3-4% for CO and 13CO and up to 12% for C18O in IM Lup; stacking gives limits up to a factor ~10 lower | F: Line polarization in these disks is low; stacking limits may hide small-scale structure | **supported**
- H: 1.3 mm continuum polarization differs from 870 um polarization in HD 142527 and IM Lup | E: Compared 1.3 mm polarization with re-imaged archival (HD 142527) and published (IM Lup) 870 um data at common resolution | R: HD 142527 north shows a changed morphology and Pfrac ratio up to ~5 with angle differences up to 90 deg; IM Lup 1.3 mm is more azimuthal with Pfrac ratio mostly >1 | F: Significant wavelength dependence; consistency with scattering needs detailed modeling | **supported**
- H: The optical depths of the CO isotopologues favour 13CO and C18O for detecting GK polarization | E: Line-ratio optical depth maps with fixed isotopic ratios | R: CO(2-1) tau typically >30 (HD 142527) or ~40 (IM Lup); 13CO ~1-7; C18O 0.1-1 | F: Optical depth alone favours 13CO and C18O but polarization was found only in CO(2-1) | **partially**

## Reasoning

- Why this data: Band 6 is the only band where CO, 13CO and C18O can be observed simultaneously; large bright disks with simple CO morphologies chosen  
  > "We chose Band 6 because this is the only ALMA band where the spectral lines CO, $^{13}$CO, and C$^{18}$O can be observed simultaneously." (Observing Details and Data Reduction); "These two targets are among the largest and brightest known disks with simple CO morphologies." (Targets)
- Why this method: Polarization is not obvious in the Stokes images, so stacking and spatial averaging over an integrated velocity range were used for a deeper search  
  > "We decided to do a deeper search for a polarized signal via spectral stacking and via spatial averaging over an integrated velocity range." (Searching for a Polarized Signal in Spectral Lines)
- Alternative: A vast mixture of wedges and radii was tried for stacking on all three lines; none gave a significant signal  
  > "We tried a vast mixture of wedges and radii for all 3 spectral lines." (Stacking via `GoFish`)
- Alternative: Velocity intervals above 1.5 km/s (2, 2.5, 3 km/s) give worse upper limits and were not reported  
  > "Any higher velocity intervals (e.g., 2, 2.5, and 3 km s$^{-1}$) largely result in much worse upper limit sensitivities across the map." (Constraining the Polarization Percentage of the Observations)
- How they decided it was enough: _not stated_
- Limitation (authors): Marginal Q detection only; inferring the magnetic field morphology is too difficult due to GK ambiguity and possible resonant scattering  
  > "Moreover, trying to infer the magnetic field morphology from these observations is too difficult, given the ambiguity of the GK effect" (Searching for Signal within an Aperture)
- Limitation (authors): Stacking can average out small-scale polarization structure  
  > "but we note that the stacking method can potentially average out small-scale polarization structure." (Summary and Discussion)
- Limitation (authors): IM Lup phase center was offset 0.8'' west from the disk centre  
  > "For IM Lup, the phase center of the observations was errantly located 0.8$''$ west from the disk center." (Observing Details and Data Reduction)
- Limitation (authors): Only CO(2-1) Stokes Q marginal signals in each disk is peculiar and may indicate more complex noise behaviour than tested  
  > "finding a marginal signal for each disk only for CO(2–1) Stokes $Q$ is peculiar and may indicate a more complex noise behavior that could not be found with our tests." (Searching for Signal within an Aperture)
- Caveat (inferred, ours): The aperture-search signal is selected by maximising SNR over position, size and channels; the Monte Carlo shows off-disk pixels reach similar SNR, so significance is not established
- Caveat (inferred, ours): Abstract (1.57%) and text (1.56%) disagree on the HD 142527 CO polarization fraction
- Caveat (inferred, ours): Stokes Q-only signal with no matching U or V could arise from instrumental leakage; leakage (D-term) calibration residuals are only bounded at <5% for polarization
- Caveat (inferred, ours): Upper limits from stacking use the Stokes V stacked noise as the polarized-intensity noise, assuming V is noise-only
- Caveat (inferred, ours): Disk geometry and stellar masses come from literature models without uncertainty propagation beyond a 1000-run perturbation

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Code: Custom aperture-search script described, no release or repository stated; GoFish is a cited public package  
  > "We then developed a script that alters the size and position of the circular aperture to find the location with the highest signal to noise." (Searching for Signal within an Aperture)
- Missing: The custom aperture-search script and its exact search grid
- Missing: Full tclean parameters (niter, threshold, masks, image size, spectral grid) and line-free channel definitions
- Missing: Calibration scripts and CASA version for the ARC manual calibration
- Missing: Velocity ranges for the moment 0 maps and the pink integrated channels
- Missing: GoFish version and non-default options
- Data volume (inferred): About 10-50 GB for the single Band 6 execution of 2018.1.01172.S (1 hour per target, 46 antennas, a 2 GHz continuum plus three high-resolution line basebands); the 870 um comparison adds another dataset
- Score (inferred): 3/5, ALMA data (project 2018.1.01172.S) are archival and results are numeric, but imaging details, channel selections and the custom aperture-search script are not given, and the detection significance depends on those choices.
- Rediscovery candidate: yes, Data come from a single archived ALMA project, the main results are numeric (Pfrac, SNR_Q, upper limits) and the analysis algorithm (aperture SNR maximisation, GoFish stacking, upper-limit equation) is described in enough detail to redo approximately.

## Links

- Method: GoFish (Teague 2019) (Stacking software used)
- Method: Hull2015 (Polarization de-biasing method)
- Method: Loomis2018 (Channel covariance from Hanning smoothing and spectral averaging)
- Method: Lyo2011 (Optical depth from brightness temperature ratio)
- Companion: Kataoka2016b (870 um polarization of HD 142527)
- Companion: Ohashi2018 (870 um polarization analysis of HD 142527)
- Companion: Hull2018 (870 um polarization of IM Lup)
- Companion: PerezS2015 (HD 142527 disk model parameters)
- Companion: Cleeves2016 (IM Lup disk model parameters)
- Companion: Lankhaar2020 (PORTAL GK disk model predictions)
- Related: ALMA 2015.1.00425.S (PI A. Kataoka)
- Related: ALMA 2016.1.00712.S (listed in acknowledgments)
- Related: ALMA 2018.1.01172.S (PI I. Stephens)

## Checks

```json
{
 "quotes": 154,
 "quotes_ok": 154,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 23,
 "numeric_problems": 0,
 "fill": {
  "facts": 126,
  "stated": 90,
  "rate": 0.714
 },
 "evidence_ok": true
}
```
