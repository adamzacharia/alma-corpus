# CO Emission and Absorption-line Survey of the M87 Nucleus Using Archival ALMA Imaging

`2025ApJ...989...83B` | The Astrophysical Journal 2025 | first author: Boizelle, Benjamin D. | arXiv: 2503.03249 | DOI: 10.3847/1538-4357/adea52

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type archival_reuse

## Science

- Fields: agn_and_quasars, nearby_galaxies
- Question: Is there molecular gas in the inner kpc of M87 (CO emission from the circumnuclear disk, ionized-gas filaments and dusty clouds, or CO absorption against the nucleus), as probed by archival ALMA imaging?  
  > "In this paper, we present a detailed mm/sub-mm wavelength molecular line search of the M87 nucleus using ALMA archival data." (Introduction)
- Target **M87 (NGC 4486) nucleus**: coordinates _not stated_; z/distance z_obs = 0.004283 (heliocentric); D_L ~ 16.7 +/- 0.6 Mpc; 80.5 pc per arcsec  
  > "We adopt a distance modulus $m-M = 31.11\pm0.08$ mag for M87 from surface brightness fluctuation methods corresponding to a luminosity distance $D_L \sim 16.7\pm0.6$ Mpc (cite: blakeslee09)." (Introduction); "After correcting the observed redshift $z_\mathrm{obs} = 0.004283$ for infall towards the Virgo cluster (cite: mould00), this $D_L$ translates to an angular size scale of 80.5 pc arcsec$^{-1}$." (Introduction); distance from Surface brightness fluctuation distance modulus m-M = 31.11 +/- 0.08 mag (cite: blakeslee09); Virgo infall correction (cite: mould00)  
  > "We adopt a distance modulus $m-M = 31.11\pm0.08$ mag for M87 from surface brightness fluctuation methods corresponding to a luminosity distance $D_L \sim 16.7\pm0.6$ Mpc (cite: blakeslee09)." (Introduction); "After correcting the observed redshift $z_\mathrm{obs} = 0.004283$ for infall towards the Virgo cluster (cite: mould00), this $D_L$ translates to an angular size scale of 80.5 pc arcsec$^{-1}$." (Introduction)

## Data provenance

- ALMA projects: 2011.0.00001.CAL, 2012.1.00661.S, 2013.1.00073.S, 2013.1.01022.S, 2015.1.00030.S, 2015.1.01170.S, 2015.1.01352.S, 2016.1.00021.S, 2016.1.01154.V, 2017.1.00608.S, 2017.1.00841.V, 2017.1.00842.V, 2019.1.00807.S, 2021.1.01398.S
- bands: Bands 3, 4, 6 and 7 (ALMA 12-m); ACA 7-m in Bands 3 and 6  
  > "These heterogeneous data cover Bands 3, 4, 6, and 7" (ALMA Data Properties); "which monitored the Band 3 and 6 variability of M87 around EHT campaigns in 2021 and 2022." (Light Curves and Spectral Slopes)
- frequencies and spectral setup: Heterogeneous setups per project; spectral resolutions ~1 to 63 MHz after online Hanning smoothing; per-spw frequency coverage and channel binning (0.49 to 31.25 MHz native) in Table 3  
  > "The chosen spectral setups resulted in spectral resolutions from $\sim$1 to 63 MHz (after online Hanning smoothing)." (ALMA Data Properties); "give the frequency coverage of each spectral window (spw) along with the associated channel binning" (Table 3)
- continuum bandwidth: _not stated_
- arrays: ALMA 12-m (plus phased-array APP-mode .V data); ACA 7-m used only for continuum SED/light curve  
  > "We also retrieved and analyzed ALMA Compact Array (ACA) 7-m observations in programs 2019.1.00807.S and 2021.1.01398.S." (Archival ALMA Imaging); "these 7-m observations are only used for an analysis of the peak SED and to construct a light curve of the bright nucleus" (Archival ALMA Imaging)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Mean synthesized beam FWHM ~0.03 arcsec to 2.3 arcsec across 12-m data; Xa1 CO(1-0) cube ~0.21 arcsec  
  > "These heterogeneous data cover Bands 3, 4, 6, and 7 with $\overline{\theta}_\mathrm{FWHM}$ ranging from $\sim$0.03$''$ to 2.3$''$." (ALMA Data Properties); "the intermediate-resolution Xa1 data set ($\overline{\theta}_\mathrm{FWHM} \sim 0.21\ensuremath{''}$)" (CO Emission-line Constraints)
- max recoverable scale: Adopted from the ALMA Science Archive and listed per member OUS in Table 3; Xa1 MRS >~ 3 arcsec  
  > "the maximum recoverable scale (MRS; adopted from the ALMA Science Archive)" (Table 3); "cannot entirely rule out diffuse emission spread out over a couple of the larger regions with $\sim$5$''$ extent" (Channel Maps)
- sensitivity: Xa1 CO(1-0) cube: typical rms ~0.4 mJy/beam per 20 km/s channel; MFS rms per member OUS in Table 3  
  > "CO(1$-$0) emission upper limits near the center of M87 from the Xa1 spectral cube with 20 km s$^{-1}$ binning and typical rms $\sim 0.4$ mJy beam$^{-1}$ per channel." (Table 1)
- time on source: Per member OUS in Table 3 (on-source time including latencies)  
  > "Col. (8) reports the on-source integration times, including latencies." (Table 3)
- observing dates: 12-m: 2013 December 1 to 2018 September 25 (per-EB dates in Table 3); ACA: 2021 and 2022  
  > "taken between 2013 December 1 and 2018 September 25" (Archival ALMA Imaging); "which monitored the Band 3 and 6 variability of M87 around EHT campaigns in 2021 and 2022." (Light Curves and Spectral Slopes)
- pi or archival as stated: Archival data; PIs listed per project in Table 3 (e.g. Vlahakis for 2012.1.00661.S and 2016.1.00021.S)  
  > "with the project code and Principle Investigator listed above each synopsis" (Table 3)
- Line: CO J = 1-0 (not stated)
- Line: CO J = 2-1 (not stated)
- Line: CO J = 3-2 (not stated)
- Other facility **HST (WFC3 F475W, GO-14256)**: Dust-absorption map used to define dust-dominated integration regions for the CO search  
  > "To isolate dust features, we used drizzled Wide Field Camera 3 (cite: dressel22) F475W imaging from program GO-14256 (PI: Biretta)." (Optical Imaging)
- Other facility **HST (ACS F660N, GO-12271)**: Halpha+[N II] filament map (polarized images combined into a Stokes I image) used to define atomic-gas integration regions  
  > "we used a series of Advanced Camera for Surveys (cite: ryon22) F660N polarized images from program GO-12271 (PI: Sparks) that we aligned before combining into a single Stokes $I$ image" (Optical Imaging)
- Other facility **Submillimeter Array (SMA)**: SMA monitoring peak flux densities joined with ALMA 12-m and 7-m values to build nuclear light curves  
  > "we joined together ALMA 12 and 7-m peak flux densities with Submillimeter Array (SMA) monitoring of M87 over this time frame (cite: event21c; event24)" (Light Curves and Spectral Slopes)
- External data: Distance modulus m-M = 31.11 +/- 0.08 mag (D_L ~ 16.7 +/- 0.6 Mpc)  
  > "We adopt a distance modulus $m-M = 31.11\pm0.08$ mag for M87 from surface brightness fluctuation methods corresponding to a luminosity distance $D_L \sim 16.7\pm0.6$ Mpc (cite: blakeslee09)." (Introduction) [from (cite: blakeslee09)]
- External data: Systemic velocity v_sys = cz_obs = 1284 +/- 5 km/s with heliocentric z_obs = 0.004283 from stellar absorption-line fits  
  > "from stellar absorption-line fits with a heliocentric $z_\mathrm{obs} = 0.004283$ (cite: cappellari11)" (Introduction) [from (cite: cappellari11)]
- External data: Cosmology: H0 = 67.8 km/s/Mpc, Omega_m = 0.308, Omega_Lambda = 0.692  
  > "we assume a standard $\Lambda$CDM cosmology with $H_0 = 67.8$ km s$^{-1}$ Mpc$^{-1}$ along with $\Omega_\mathrm{m} = 0.308$ and $\Omega_\Lambda = 0.692$ (cite: planck2016)" (Introduction) [from (cite: planck2016)]
- External data: CO(1-0)-to-H2 conversion factor alpha_CO = 3.1 Msun pc^-2 (K km/s)^-1  
  > "For a standard CO(1$-$0)-to-H$_2$ conversion factor $\alpha_\mathrm{CO} = 3.1$ $M_\odot$ pc$^{-2}$ (K km s$^{-1}$)$^{-1}$ (cite: Sandstrom2013)" (CO Emission) [from (cite: Sandstrom2013)]
- External data: Dust-to-gas mass ratio ~0.015 adopted for the dust-mass limit  
  > "For $T_\mathrm{dust} = 25$ K and a standard dust-to-gas mass ratio of $\sim$0.015 (cite: Sandstrom2013)" (Circumnuclear Dust) [from (cite: Sandstrom2013)]
- External data: Previous SMA CO(2-1) tentative detection S_CO(2-1)dv ~ 8.8 +/- 2.2 (stat) +/- 1.8 (sys) Jy km/s in an ~80 pc aperture  
  > "(cite: tan08) reported a tentative $S_\mathrm{CO(2-1)}\Delta v \approx 8.8\pm2.2(\mathrm{stat})\pm1.8(\mathrm{sys})$ Jy km s$^{-1}$ detection" (Introduction) [from (cite: tan08)]
- External data: Atomic-gas UV/optical absorption lines with v_LOS - v_sys ~ -131 +/- 19 km/s and FWHM <~ 300 km/s  
  > "and moderate intrinsic FWHM $\lesssim 300$ km s$^{-1}$ (cite: tsvetanov99b; sabra03)" (Introduction) [from (cite: tsvetanov99b; sabra03)]
- External data: Total N_H ~ (2-5)e20 cm^-2 towards the nucleus from X-ray spectroscopy  
  > "total $N_\mathrm{H} \sim (2-5)\times 10^{20}$ cm$^{-2}$ towards the M87 nucleus from X-ray spectroscopy (cite: wilson02; dimatteo03)" (Column Densities) [from (cite: wilson02; dimatteo03)]
- External data: CO/H2 abundance ratios: 3.2e-4 standard (Galactic dense gas); ~2e-6 and ~8e-7 for diffuse Galactic sight lines  
  > "A standard CO/H$_2$ abundance ratio of $3.2\times 10^{-4}$ (cite: sofia04; bolatto2013)" (Column Densities); "CO/H$_2$ abundances of $\sim$2$\times$10$^{-6}$ (cite: liszt19) to $\sim$8$\times$10$^{-7}$ (cite: pineda10)" (Column Densities) [from (cite: sofia04; bolatto2013; liszt19; pineda10)]
- Simulation/model as data: Mock Band 3/6/7 light curves from power spectral density fits to other radio galaxies (Emmanoulopoulos method) used to estimate spectral-index uncertainty  
  > "Following the methodology outlined by (cite: emmanoulopoulos13), we simulated an ALMA Band 6 peak light curve spanning 2 yrs with a one-day cadence." (Light Curves and Spectral Slopes)
- Simulation/model as data: Atmospheric transmission curves from the am model (Mauna Kea manual model adjusted to PWV, elevation and ground-layer temperature of each MS)  
  > "we borrowed the realistic `am` manual model for Mauna Kea at nearly the same altitude after adjusting for the average PWV, target elevation, and ground-layer temperature for each MS" (Atmospheric Modeling)

## Processing

### Calibration

- pipeline or manual: Standard CASA pipeline calibration with the pipeline version appropriate to each data set; limited manual improvements (re-flagging, spw flux rescaling)  
  > "we applied standard pipeline calibrations to the 12-m data using the appropriate" (Calibration Processes); "Below, we discuss limited improvements to the standard pipeline calibration processes." (Calibration Processes)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Not as is for 12-m data (re-calibrated, X20f re-processed); .V programs used only as available in the archive (APP-mode columns and tables)  
  > "From the ALMA archive, the available .V datasets only contain columns and calibration tables pertaining to the phased (APP) observing mode." (Calibration Processes); "Removing these manually-flagged channels, re-calibrating the raw visibilities, and re-imaging a new MS resulted in more consistent spectral behavior." (Manual Flagging)
- flux calibrator: Flux calibrator fluxdensity Stokes I levels re-scaled in setjy per spw by up to 2% for 2015.1.00030.S and 2016.1.00021.S; calibrator names not given  
  > "We manually re-scaled their flux calibrator" (Calibration Processes); "for individual spws by up to 2% to ensure more continuous flux densities in image-plane spectral cubes." (Calibration Processes)
- flux scale uncertainty: ~5% in Band 3; 10% in Bands 6 and 7  
  > "Absolute flux calibration uncertainties for MFS images and spectral cubes is about 5% in Band 3 and 10% in Bands 6 and 7 (cite: fomalont14; francis20b; privon24)." (MFS and Spectral Imaging)
- self calibration: Phase (and usually amplitude) self-calibration, final solint per integration (per scan); amplitude self-cal not used for X20d and X1b0 when DR decreased  
  > "We applied phase (and usually amplitude) self-calibration with final solution intervals that were per integration (per scan)." (Calibration Processes); "amplitude self-calibration was not adopted when the multi-frequency synthesis (MFS) image peak/rms dynamic range (DR) decreased noticeably compared to the final phase-only products" (Calibration Processes)

### Imaging

- task: CASA tclean for MFS images and spectral cubes; uvcontsub for continuum subtraction; imfit for continuum fits  
  > "we imaged each MS into a Stokes $I$ MFS map using Briggs weighting (cite: briggs95) in the" (MFS and Spectral Imaging); "Lastly, we subtracted the continuum for MSs containing CO transitions using the `uvcontsub` task (with `fitorder` = 1) with three distinct fitting regions." (MFS and Spectral Imaging)
- deconvolver: _not stated_
- weighting robust: Spectral cubes: Briggs robust r = 0.5; MFS maps: Briggs (robust not given), some also uniform weighting  
  > "with Briggs ($r=0.5$) weighting at the native channel binning given in Table" (MFS and Spectral Imaging); "Some of these data were also deconvolved into MFS images using uniform (natural) weighting for greater resolution (sensitivity)." (MFS and Spectral Imaging)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub with fitorder = 1; three line-channel exclusion cases (|v-vsys| < 500, < 1000 km/s, and 100 < |v-vsys| < 2200 km/s for CO(1-0) only); main results use the first case  
  > "Lastly, we subtracted the continuum for MSs containing CO transitions using the `uvcontsub` task (with `fitorder` = 1) with three distinct fitting regions." (MFS and Spectral Imaging); "we explore relatively narrow emission and absorption-line results derived using the first `uvcontsub` case" (MFS and Spectral Imaging)
- line free channels: Channels with |v_LOS - v_sys| < 500 km/s excluded in the first case (main case)  
  > "we excluded channels corresponding to either $|\ensuremath{v_\mathrm{LOS}}- \ensuremath{v_\mathrm{sys}}| < 500$ km s$^{-1}$ to probe more standard velocity ranges for extragalactic gas" (MFS and Spectral Imaging)
- primary beam correction: Primary beam correction applied to spectral extraction (effect up to 10% on noise away from the phase center)  
  > "due to the impact of the primary beam correction further from the ALMA phase center" (CO Emission-line Constraints)
- array combination: _not stated_
- smoothing: Continuum-subtracted cubes imaged at native spacing and at ~20-40 km/s binning (20 km/s for the emission search)  
  > "We imaged the continuum-subtracted data into spectral cubes at both the native frequency spacing and at more coarse binning ($\sim$20$-$40 km s$^{-1}$) to increase the signal-to-noise ratio (S/N)." (MFS and Spectral Imaging)
- final beam: Common restoring beam per spectral setup; per-member beams in Table 3 (Xa1 ~0.21 arcsec)  
  > "resulting in 72 continuum-dominated spectral cubes with a common restoring beam for each spectral setup" (MFS and Spectral Imaging)
- final rms: Xa1 CO(1-0) cube: typical rms ~0.4 mJy/beam per 20 km/s channel  
  > "typical rms $\sim 0.4$ mJy beam$^{-1}$ per channel" (Table 1)

### Inherited from earlier work

- Iteratively expanded pixel mask of non-stellar features for the stellar-continuum fit to HST images  
  > "Following (cite: davidson24), we iteratively expanded a pixel mask containing non-stellar features" (Optical Imaging) [from (cite: davidson24)]
- Monte Carlo region-shifting scheme for emission-line flux uncertainties  
  > "we followed a Monte Carlo (MC) resampling technique that iteratively shifted each region by a random amount before re-integrating (cite: boizelle17)" (CO Emission-line Constraints) [from (cite: boizelle17)]
- Adopting the standard deviation of blank-region flux densities as the uncertainty spectrum  
  > "as a good proxy for the true uncertainty spectrum (cite: tsukui23)" (CO Emission-line Constraints) [from (cite: tsukui23)]
- Column-density equations relating CO(2-1) and CO(1-0) opacities with a common excitation temperature  
  > "we first solved column density equations that relate integrated CO(2$-$1) and CO(1$-$0) opacities with a common $T^{21}_\mathrm{ex}$ (cite: godard2010; rose19b) by" (Temperature and Column Densities) [from (cite: godard2010; rose19b)]
- Temperature-dependent 12CO rotational partition function Q_rot  
  > "the temperature-dependent $^{12}$CO rotational partition function $Q_\mathrm{rot}$ (cite: Mangum2015)" (Temperature and Column Densities) [from (cite: Mangum2015)]
- Voronoi tessellation to bin spectra across the central beam to uniform continuum S/N  
  > "Spectra in adjacent spatial pixels were combined together using Voronoi tessellation (cite: cappellari03) prior to refitting" (CO Absorption-line Properties) [from (cite: cappellari03)]
- Noise random-aperture method for the extended thermal continuum flux limit  
  > "as an effective 1$\sigma$ limit (cite: tsukui23)" (Circumnuclear Dust) [from (cite: tsukui23)]
- Light-curve simulation method for estimating spectral-index uncertainty  
  > "Following the methodology outlined by (cite: emmanoulopoulos13), we simulated an ALMA Band 6 peak light curve" (Light Curves and Spectral Slopes) [from (cite: emmanoulopoulos13); PSD fits from (cite: zhang20)]
- Not building Tsys spectra in FDM mode for ozone mitigation (following the ozone-correction approach of the cited work)  
  > "(cite: hunter18) demonstrated that the coarse TDM atmospheric calibration used for these ALMA 12-m data may over/undercorrect for atmospheric ozone" (Atmospheric Modeling) [from (cite: hunter18)]

### Not stated but needed to reproduce (our reading)

- CASA and pipeline versions used for each data set (only 'the appropriate pipeline version' is given)
- Briggs robust value for MFS maps, cell size, image size, niter/threshold, deconvolver and masks for tclean MFS and cube imaging
- Which flux calibrator and which spws had setjy rescaling, and the exact rescale factors per spw
- Self-calibration details: refant, solint sequence, number of loops, which EBs received amplitude self-cal
- Exact line-free channel/spw selections used in uvcontsub for each project and spw, and how overlapping spws were handled
- Pixel/polygon definitions, coordinates and positions of the HST-based integration regions in Table 1, and MGE/GALFIT component parameters and image alignment details
- Frequency windows and error model for the Gaussian + linear-continuum fits of the absorption lines; exact Hanning-smoothing kernel treatment
- Collision-rate files, line-width treatment and chi-square definition (data points, errors) used in the RADEX grid; grid spacing
- Dust absorption coefficient kappa(850 micron) value used for the dust-mass limit
- Rest frequencies used for CO transitions and source coordinates / phase centre
- Exact channel ranges flagged manually in each member OUS

## Analysis recipe

1. **Calibrate 12-m ALMA data**: Standard CASA pipeline calibration with the pipeline version appropriate to each data set; additional manual flagging; X20f re-calibrated after removing mis-flagged ozone channels; flux calibrator fluxdensity rescaled by up to 2% per spw for two projects; .V programs used in APP mode  
  > "we applied standard pipeline calibrations to the 12-m data using the appropriate" (Calibration Processes); "Removing these manually-flagged channels, re-calibrating the raw visibilities, and re-imaging a new MS resulted in more consistent spectral behavior." (Manual Flagging)
   - software: CASA, setjy
   - parameter: setjy flux density rescaling of up to 2% for individual spws (2015.1.00030.S, 2016.1.00021.S)  
  > "for individual spws by up to 2% to ensure more continuous flux densities in image-plane spectral cubes." (Calibration Processes)
   - parameter: Additional manual flagging for high antenna temperature, amplitude disagreement and poor bandpass calibration near spw edges  
  > "We manually flagged a limited number of additional visibilities based on high antenna temperature, amplitude disagreement, and poor bandpass calibration near spw edges." (Manual Flagging)
   - assumption: APP-mode calibration adopted for the .V programs; no interferometric-mode phase self-calibration possible  
  > "We adopted the APP-mode results since other projects covered redshifted CO(2$-$1) and because reconstructing the ALMA interferometric-mode calibration tables is beyond the scope of this archival project (cite: goddi19)" (Calibration Processes)
   - fitting: _not stated_
   - validation: Inter-spw continuum mismatches of 1-3% checked against expected relative flux calibration errors  
  > "In adjacent or overlapping spws, peak continuum spectra show mismatches at the 1–3% level" (Calibration Processes)
2. **Self-calibrate and image continuum (MFS)**: Phase (and usually amplitude) self-calibration loops using gaincal with MFS Stokes I tclean images (Briggs weighting; some uniform/natural)  
  > "As a part of the self-calibration loops, we imaged each MS into a Stokes $I$ MFS map using Briggs weighting (cite: briggs95) in the" (MFS and Spectral Imaging); "clean phase solutions can generally be obtained through iterative self-calibration by using the" (Atmospheric Modeling)
   - software: CASA, tclean, gaincal
   - parameter: Final solution intervals per integration (per scan); resulting dynamic ranges from several hundred to ~9000  
  > "We applied phase (and usually amplitude) self-calibration with final solution intervals that were per integration (per scan)." (Calibration Processes); "DRs spanned from several hundred up to $\sim$9000" (Calibration Processes)
   - fitting: _not stated_
   - validation: Amplitude self-calibration dropped where the MFS peak/rms dynamic range decreased relative to the phase-only product  
  > "amplitude self-calibration was not adopted when the multi-frequency synthesis (MFS) image peak/rms dynamic range (DR) decreased noticeably compared to the final phase-only products" (Calibration Processes)
3. **Make continuum-dominated spectral cubes and peak continuum spectra**: Image each spw (or set of overlapping spws) with tclean at native channel binning with a common restoring beam, then plot peak flux density per channel  
  > "resulting in 72 continuum-dominated spectral cubes with a common restoring beam for each spectral setup" (MFS and Spectral Imaging); "across all unflagged frequencies for the entire sample." (MFS and Spectral Imaging)
   - software: CASA, tclean
   - parameter: Briggs robust r = 0.5 weighting, native channel binning  
  > "with Briggs ($r=0.5$) weighting at the native channel binning given in Table" (MFS and Spectral Imaging)
   - assumption: Absolute flux uncertainty ~5% (Band 3) and 10% (Bands 6, 7)  
  > "Absolute flux calibration uncertainties for MFS images and spectral cubes is about 5% in Band 3 and 10% in Bands 6 and 7 (cite: fomalont14; francis20b; privon24)." (MFS and Spectral Imaging)
   - fitting: _not stated_
   - validation: _not stated_
4. **Subtract continuum in the uv plane and image CO cubes**: uvcontsub with fitorder = 1 with three line-channel exclusion cases, then image continuum-subtracted data at native and coarser (~20-40 km/s) binning  
  > "Lastly, we subtracted the continuum for MSs containing CO transitions using the `uvcontsub` task (with `fitorder` = 1) with three distinct fitting regions." (MFS and Spectral Imaging); "We imaged the continuum-subtracted data into spectral cubes at both the native frequency spacing and at more coarse binning ($\sim$20$-$40 km s$^{-1}$) to increase the signal-to-noise ratio (S/N)." (MFS and Spectral Imaging)
   - software: CASA, uvcontsub, tclean
   - parameter: Case 1: exclude |v_LOS - v_sys| < 500 km/s (used for the main emission and absorption results)  
  > "we excluded channels corresponding to either $|\ensuremath{v_\mathrm{LOS}}- \ensuremath{v_\mathrm{sys}}| < 500$ km s$^{-1}$ to probe more standard velocity ranges for extragalactic gas" (MFS and Spectral Imaging)
   - parameter: Case 3 (CO(1-0) only): exclude 100 < |v_LOS - v_sys| < 2200 km/s  
  > "In a third case for CO(1$-$0) only, we excluded the ranges $100 < |\ensuremath{v_\mathrm{LOS}}- \ensuremath{v_\mathrm{sys}}| < 2200$ km s$^{-1}$ to test for possible broad emission-line features" (MFS and Spectral Imaging)
   - fitting: Linear (fitorder = 1) continuum fit per visibility  
  > "Lastly, we subtracted the continuum for MSs containing CO transitions using the `uvcontsub` task (with `fitorder` = 1) with three distinct fitting regions." (MFS and Spectral Imaging)
   - validation: Cases 2 and 3 tested; they produce faint, likely spurious spectral deficits or excesses near redshifted CO  
  > "we explore the second and third `uvcontsub` cases that produce very faint (and likely spurious) spectral deficits or excesses near redshifted CO transitions" (MFS and Spectral Imaging)
5. **Build HST dust and Halpha maps and define integration regions**: Subtract a Multi-Gaussian-Expansion stellar model fitted with GALFIT from WFC3 F475W and ACS F660N images, producing gas emission and dust absorption maps used to define CO integration regions  
  > "we modeled and subtracted the stellar continuum using a concentric Multi-Gaussian Expansion (cite: emsellem94) with uniform PAs using" (Optical Imaging); "To create integration regions for this ALMA CO line search, we employed pipeline-calibrated HST images" (Optical Imaging)
   - software: GALFIT
   - parameter: F475W from GO-14256 for dust; F660N polarized images from GO-12271 aligned and combined into a Stokes I image  
  > "we used a series of Advanced Camera for Surveys (cite: ryon22) F660N polarized images from program GO-12271 (PI: Sparks) that we aligned before combining into a single Stokes $I$ image" (Optical Imaging)
   - fitting: Concentric MGE with uniform position angles fitted with GALFIT; non-stellar pixels masked iteratively  
  > "Following (cite: davidson24), we iteratively expanded a pixel mask containing non-stellar features" (Optical Imaging)
   - validation: _not stated_
6. **Search for CO(1-0) emission and set upper limits**: Integrate CO(1-0) line profiles from the Xa1 cube (20 km/s channels) over HST-defined regions, a 0.5 arcsec CND aperture and a 0.2-0.5 arcsec annulus, with MC region-shifting noise; convert limits to M_H2 with alpha_CO  
  > "To encompass the entire atomic gas CND, we integrated over a circular aperture with a radius $R = 0.5\ensuremath{''}$ ($\sim$40 pc)." (CO Emission-line Constraints); "we followed a Monte Carlo (MC) resampling technique that iteratively shifted each region by a random amount before re-integrating (cite: boizelle17). After 200 iterations" (CO Emission-line Constraints)
   - software: CASA
   - parameter: Integration velocity range: atomic-gas v_LOS range plus +/-100 km/s buffer; dust regions ~300 km/s centered on v_sys  
  > "In dust-dominated regions seen primarily in the F475W filter, line profiles were integrated over a $\sim$300 km s$^{-1}$ range centered on $v_\mathrm{sys}$." (CO Emission-line Constraints)
   - parameter: 200 MC iterations to build the noise spectrum  
  > "After 200 iterations" (CO Emission-line Constraints)
   - assumption: alpha_CO = 3.1 Msun pc^-2 (K km/s)^-1  
  > "For a standard CO(1$-$0)-to-H$_2$ conversion factor $\alpha_\mathrm{CO} = 3.1$ $M_\odot$ pc$^{-2}$ (K km s$^{-1}$)$^{-1}$ (cite: Sandstrom2013)" (CO Emission)
   - fitting: _not stated_
   - validation: Channel-by-channel inspection of candidate excesses found no clear features; higher-resolution X5 data give ~2x poorer limits  
  > "However, a channel-by-channel inspection of the integration over the velocity range shows no clear features." (CO Emission-line Constraints); "the higher-resolution X5 data yields $\sim$2$\times$ poorer constraints due to the larger number of beams in each integration area" (CO Emission-line Constraints)
7. **Fit CO absorption lines in peak continuum spectra**: Compute opacity tau_nu = -ln(T_nu/T_cont); fit each CO absorption feature with a Gaussian and linear continuum including Hanning smoothing; MC resampling for errors; weighted averages over data sets; Voronoi-binned refit of Xa1 across the central beam  
  > "we fit each CO absorption feature with a Gaussian line profile and a linear continuum to recover the line centroid" (CO Absorption-line Properties); "Here, the peak continuum spectrum $T_\nu \propto S_\nu/\theta_\mathrm{maj}\theta_\mathrm{min}$ is measured in K units and $T_{\nu,\mathrm{cont}}$ is the fitted linear continuum level about the CO line feature." (CO Absorption-line Properties)
   - software: CASA
   - parameter: MC resampling adding noise (std of line-free portions) to the best-fit model and shifting bin centers by a normal fraction (std = 1/4 channel width)  
  > "We estimated parameter uncertainties by an MC resampling technique that adds random noise to the best-fitting model spectrum before refitting." (CO Absorption-line Properties); "These frequency shifts were also drawn from a normal distribution with standard deviation equal to a quarter of the corresponding $\Delta \nu_\mathrm{obs}$ value in Table" (CO Absorption-line Properties)
   - parameter: For CO(2-1) only the Xb APP-mode fit from 2016.1.01154.V is used among .V data  
  > "but we only utilize spectral fits to the most regular Xb data set from program 2016.1.01154.V when calculating CO absorber properties" (CO Absorption-line Properties)
   - assumption: Hanning smoothing incorporated to recover intrinsic line widths  
  > "These fits incorporated Hanning smoothing[^2] to recover intrinsic $\sigma_\mathrm{LOS}$." (CO Absorption-line Properties)
   - fitting: Gaussian + linear continuum least-squares-type fit with MC uncertainties (no sampler or priors stated)  
  > "we fit each CO absorption feature with a Gaussian line profile and a linear continuum to recover the line centroid" (CO Absorption-line Properties)
   - validation: Centroid-frequency ratios of CO(1-0), (2-1), (3-2) broadly consistent with expectations; line detected across multiple data sets and transitions  
  > "and the observed ratios are broadly consistent with expectations" (CO Absorption-line Properties)
8. **Derive excitation temperature and column density (LTE)**: Solve the opacity-ratio equation for T_ex(2-1), then N_CO from CO(1-0) opacity and Q_rot; error bars from Monte Carlo draws of tau_CO; N_H2 from CO/H2 abundance ratios  
  > "To determine a total column density $N_\mathrm{CO}$, we primarily considered CO(1$-$0) absorption and an excitation temperature for the lowest-$J$ transitions:" (Temperature and Column Densities); "After $10^5$ iterations, we used the 15.9 to 84.1 (0.14 to 99.87) percentile levels of the $T^{21}_\mathrm{ex}$ distribution" (Temperature and Column Densities)
   - software: Splatalogue
   - parameter: 10^5 MC iterations with tau_CO drawn from normal distributions (std = 1-sigma uncertainty); 1-sigma and 3-sigma percentile ranges  
  > "We recovered more reliable error bars in a series of trials by drawing individual $\tau_\mathrm{CO}$ randomly from normal distributions centered on their measured value with standard deviations equal to their 1$\sigma$ uncertainties in Table" (Temperature and Column Densities)
   - assumption: Single-zone LTE with adjacent transitions under the same conditions; beam filling factor ignored; CMB negligible; T_K = T_ex  
  > "This assumes a single-zone system in local thermodynamic equilibrium (LTE) where adjacent transitions (e.g., $J = 0\rightarrow1$ and $1\rightarrow2$) originate under the same conditions." (Temperature and Column Densities); "We have ignored beam filling factors and also considered the impact of the CMB background to be negligible" (Temperature and Column Densities)
   - assumption: Diffuse-gas CO/H2 abundance ratios (~2e-6 to ~8e-7) preferred over the standard 3.2e-4 for N_H2  
  > "CO/H$_2$ abundances of $\sim$2$\times$10$^{-6}$ (cite: liszt19) to $\sim$8$\times$10$^{-7}$ (cite: pineda10)" (Column Densities)
   - fitting: Direct solution of the equations with Monte Carlo error propagation (no priors)  
  > "After calculating weighted-average opacities at each iteration, we used the newly-fit $T_\mathrm{ex}$ to find a new $Q_\mathrm{rot}$ and $N_\mathrm{CO}$." (Temperature and Column Densities)
   - validation: CO(3-2)/CO(2-1) opacity ratio is not consistent with LTE expectations, motivating non-LTE modelling  
  > "is not consistent with LTE expectations." (Temperature and Column Densities)
9. **Non-LTE radiative transfer modelling of the absorber**: RADEX uniform-sphere LVG models fitted to the weighted-average peak opacities of CO(1-0), CO(2-1) and CO(3-2) on a grid of n_H2 and T_bg for T_K = 10 K and 30 K  
  > "we employed the one-dimensional non-LTE radiative transfer code `radex` (cite: ferland98; van07) to reproduce the observed peak opacities" (Temperatures and Densities); "and present $\chi^2$ contours over a grid of $n_\mathrm{H_2}$ and $T_\mathrm{bg}$ points" (Temperatures and Densities)
   - software: radex
   - parameter: N_CO = 1e15 cm^-2 fixed from LTE; CO FWHM fixed to 10 km/s  
  > "we adopted $N_\mathrm{CO} = 10^{15}$ cm$^{-2}$ from LTE measurements and fixed the CO line FWHM to 10 km s$^{-1}$" (Temperatures and Densities)
   - parameter: Grid n_H2 = 1e2-1e5 cm^-3 and T_bg = 30-300 K; T_K = 10 K and 30 K tested  
  > "During `radex` modeling, we explored $n_\mathrm{H_2} = 10^2-10^5$ cm$^{-3}$ and background temperature $T_\mathrm{bg} = 30-300$ K." (Temperatures and Densities); "we assumed a cold gas distribution and tested $T_K = 10$ K and 30 K in turn" (Temperatures and Densities)
   - assumption: Uniform, isothermal, homogeneous sphere with large-velocity-gradient escape probability; 12CO traces the whole cloud because tau << 1  
  > "We assumed the gas is organized in a uniform sphere, although different geometries and escape probabilities give similar results for low-$J$ CO transitions." (Temperatures and Densities)
   - fitting: Chi-square grid search over n_H2 and T_bg (no sampler or priors stated)  
  > "and present $\chi^2$ contours over a grid of $n_\mathrm{H_2}$ and $T_\mathrm{bg}$ points" (Temperatures and Densities)
   - validation: Different geometries and escape probabilities give similar results; 1-sigma contours do not close, so only lower limits n_H2 > 1100 cm^-3 and T_bg > 45 K  
  > "While the 1$\sigma$ contours do not close for reasonable $n_\mathrm{H_2}$ and $T_\mathrm{bg}$, they provide $n_\mathrm{H_2} > 1100$ cm$^{-3}$ and $T_\mathrm{bg} > 45$ K lower limits." (Temperatures and Densities)
10. **Limit circumnuclear thermal dust from the continuum**: Fit the X2c2 uniform-weighted MFS image with a nuclear source plus an offset Gaussian for N2 (imfit); sample noise with random 0.05 arcsec apertures on the residual image; convert the 1-sigma limit to M_dust and gas mass with a modified blackbody  
  > "We fit the X2c2 MFS image (with uniform weighting; $\theta_\mathrm{maj} \times \theta_\mathrm{min} = 27 \times 21$ mas$^2$ or a FWHM $\sim 2$ pc) using the" (MFS imaging); "by shifting a circular ($R = 0.05\ensuremath{''}$) aperture randomly to 100 continuum-free regions of the residual X2c2 MFS image to sample the noise" (Circumnuclear Dust)
   - software: CASA, imfit, uvmodelfit
   - parameter: 1-sigma flux limit delta S_ext = 0.75 mJy  
  > "taking the standard deviation $\delta S_\mathrm{ext} = 0.75$ mJy as an effective 1$\sigma$ limit" (Circumnuclear Dust)
   - assumption: Dust absorption coefficient at 850 micron (value not given) with beta = 2; T_dust = 25 K (or 100 K); dust-to-gas ratio ~0.015  
  > "assumes a standard dust absorption coefficient $\kappa_\mathrm{850\,\mu m}$ and emissivity index $\beta = 2$" (Circumnuclear Dust); "For $T_\mathrm{dust} = 25$ K and a standard dust-to-gas mass ratio of $\sim$0.015 (cite: Sandstrom2013)" (Circumnuclear Dust)
   - fitting: Image-plane imfit with a nuclear point source and an offset elliptical Gaussian  
  > "with a nuclear source and an additional, offset elliptical Gaussian to characterize the N2 clump" (MFS imaging)
   - validation: imfit residuals show no additional sources within the inner 50 mas  
  > "`imfit` residuals do not support any additional sources within the inner 50 mas" (MFS imaging)
11. **Measure ACA/ALMA continuum light curve and spectral index**: Pipeline calibration and phase-only self-calibration of ACA data, MFS imaging, combine peak flux densities with SMA monitoring, fit mm/sub-mm spectral index; simulate DRW light curves to estimate non-contemporaneous index error  
  > "We obtained these archival data and applied standard pipeline calibration followed by phase-only self-calibration prior to MFS imaging" (Light Curves and Spectral Slopes); "We then collected these $\alpha^{\prime}$ for a given time separation across the entire synthetic light curve" (Light Curves and Spectral Slopes)
   - software: CASA
   - parameter: Intrinsic alpha = -0.6 for the mock light curves; Band 6 light curve 2 yr with one-day cadence  
  > "Additional Bands 3 and 7 light curves were then created using a consistent (intrinsic) $\alpha_\mathrm{intr} = -0.6$ at each time epoch." (Light Curves and Spectral Slopes)
   - fitting: Spectral-index fit with errors including rms and absolute flux scaling uncertainties  
  > "Fit errors include both rms and absolute flux scaling uncertainties." (Light Curves and Spectral Slopes)
   - validation: Index uncertainty calibrated with synthetic light curves; real 12-m uncertainty likely underestimated by a factor >=3  
  > "underestimates the true uncertainty by at least a factor of 3" (Light Curves and Spectral Slopes)
12. **Test telluric and bandpass origins of spurious spectral features**: Model atmospheric transmission with am for each spw, compare ozone residuals with line catalogs, and compare peak spectra across spws and EBs to evaluate bandpass stability  
  > "To aid in identifying and characterizing faint ozone features, we employed the" (Atmospheric Modeling); "In Figure [14](#fig:bandpass), we compare the spectral behavior for individual spws in a single sideband from all standard ALMA programs covering redshifted CO(1$-$0) and CO(2$-$1) transitions." (Bandpass Calibration Accuracy)
   - software: am, CDMS/JPL catalogs
   - parameter: Ozone lines tabulated down to CDMS/JPL log intensity -5.3  
  > "we indicate the frequencies of the ozone and water vapor transitions that have CDMS/JPL logarithmic intensities" (Atmospheric Modeling)
   - assumption: N_O3 scales linearly with the depth of unsaturated O3 absorption lines  
  > "Assuming that $N_\mathrm{O_3}$ scales linearly with the depth of unsaturated O$_3$ absorption lines" (Atmospheric Modeling)
   - fitting: _not stated_
   - validation: Broad CO deficits and excesses attributed to bandpass patterns because contemporaneous data sets disagree over the same frequency range  
  > "For example, the $S_\nu$ behavior over 102$-$104 GHz in the X5 data set is inconsistent with those covering the same spectral range in Xbe and X135 data sets, which were obtained just weeks apart." (Bandpass Calibration Accuracy)

## Software

- **CASA** : Pipeline calibration, self-calibration and imaging of the ALMA data  
  > "we applied standard pipeline calibrations to the 12-m data using the appropriate" (Calibration Processes)
- **tclean** : MFS continuum maps and spectral cubes with Briggs weighting  
  > "with Briggs ($r=0.5$) weighting at the native channel binning given in Table" (MFS and Spectral Imaging)
- **uvcontsub** : uv-plane continuum subtraction (fitorder = 1)  
  > "Lastly, we subtracted the continuum for MSs containing CO transitions using the `uvcontsub` task (with `fitorder` = 1) with three distinct fitting regions." (MFS and Spectral Imaging)
- **setjy** : Manual rescaling of flux calibrator flux densities per spw  
  > "for individual spws by up to 2% to ensure more continuous flux densities in image-plane spectral cubes." (Calibration Processes)
- **gaincal** : Phase self-calibration solutions as short as the scan length  
  > "clean phase solutions can generally be obtained through iterative self-calibration by using the" (Atmospheric Modeling)
- **imfit** : Fitting the nuclear source and N2 clump in the X2c2 MFS image  
  > "We fit the X2c2 MFS image (with uniform weighting; $\theta_\mathrm{maj} \times \theta_\mathrm{min} = 27 \times 21$ mas$^2$ or a FWHM $\sim 2$ pc) using the" (MFS imaging)
- **uvmodelfit** : uv-plane subtraction of the central point source as a test  
  > "subtraction of the central point source using the" (MFS imaging)
- **GALFIT** : Fitting Multi-Gaussian-Expansion stellar models to HST images  
  > "we modeled and subtracted the stellar continuum using a concentric Multi-Gaussian Expansion (cite: emsellem94) with uniform PAs using" (Optical Imaging)
- **radex** : Non-LTE radiative transfer modelling of the CO absorber  
  > "we employed the one-dimensional non-LTE radiative transfer code" (Temperatures and Densities)
- **ALMA Observing Tool** : Estimating on-source times needed for future CO observations  
  > "To achieve just a 3$\times$ improvement in noise over the Xa1 results (reaching an rms $\sim 0.225$ mJy beam$^{-1}$ in a 20 km s$^{-1}$ channel), the ALMA" (CO Emission)
- **am** : Atmospheric transmission curves to identify telluric ozone and water lines  
  > "To aid in identifying and characterizing faint ozone features, we employed the" (Atmospheric Modeling)
- **Splatalogue** : Einstein coefficients and line identification  
  > "Obtained from Splatalogue" (Footnote 3)
- **CDMS/JPL line catalogs** : Intensities of ozone and water lines marked on spectra  
  > "we indicate the frequencies of the ozone and water vapor transitions that have CDMS/JPL logarithmic intensities" (Atmospheric Modeling)
- **PlotDigitizer** : _not stated_

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| H2 mass upper limit over the atomic-gas CND | < 2.3e5 | upper limit | Msun | 6 | We find no evidence for CO emission in the central $\sim$kpc and place an upper limit of $M_\mathrm{H_2} < 2.3\times 10^5$ $M_\odot$ in the atomic gas CND region |
| Nuclear CO(1-0) integrated flux (R<0.5 arcsec) | < 0.109 | 1-sigma upper limit | Jy km/s | 6 | we estimated nuclear $S_\mathrm{CO(1-0)} \Delta v < 0.109$ Jy km s$^{-1}$ (1$\sigma$ uncertainty) |
| CO(1-0) integrated flux, outer jet region (highest S/N candidate) | 1.19 | 0.36 | Jy km/s | 6 | with an integrated $S_\mathrm{CO(1-0)}\Delta v \approx 1.19 \pm 0.36$ Jy km s$^{-1}$ that just exceeds the 3$\sigma$ threshold |
| Global CO(1-0) flux over inner ~2 kpc | < 4.8 | 1-sigma upper limit | Jy km/s | 6 | returns only an $S_\mathrm{CO(1-0)}\Delta v < 4.8$ Jy km s$^{-1}$ 1$\sigma$ upper limit over the entire $\pm$500 km s$^{-1}$ range |
| Global H2 mass upper limit (R = 2 kpc aperture) | < 4e6 | upper limit | Msun | 6 | we find a similar $<$4$\times$10$^6$ $M_\odot$ global upper limit |
| Weighted-average peak opacity tau_0 CO(1-0) | 0.00239 | 0.00054 | dimensionless | 7 | we also constructed final weighted-average peak opacities $\overline{\tau}_\mathrm{0,CO(1-0)} = 0.00239\pm 0.00054$ and $\overline{\tau}_\mathrm{0,CO(2-1)} = 0.00390\pm 0.00063$ |
| Weighted-average peak opacity tau_0 CO(2-1) | 0.00390 | 0.00063 | dimensionless | 7 | we also constructed final weighted-average peak opacities $\overline{\tau}_\mathrm{0,CO(1-0)} = 0.00239\pm 0.00054$ and $\overline{\tau}_\mathrm{0,CO(2-1)} = 0.00390\pm 0.00063$ |
| Integrated opacity tau_CO(1-0), weighted average | 0.0281 | 0.0045 | km/s | 7 | The integrated opacity $\overline{\tau}_\mathrm{CO(1-0)} = 0.0281 \pm 0.0045$ km s$^{-1}$ |
| Integrated opacity tau_CO(2-1), weighted average | 0.0410 | 0.0041 | km/s | 7 | $\overline{\tau}_\mathrm{CO(2-1)} = 0.0410 \pm 0.0041$ km s$^{-1}$ |
| Weighted-average absorber velocity offset v_LOS - v_sys (CO(1-0) and CO(2-1)) | -77.21 | 0.44 | km/s | 7 | the weighted-average $\overline{v}_\mathrm{LOS} - \ensuremath{v_\mathrm{sys}}= -77.21 \pm 0.44$ km s$^{-1}$ |
| Weighted-average absorber line width sigma_LOS | 4.65 | 0.47 | km/s | 7 | the observed $\overline{\sigma}_\mathrm{LOS} = 4.65\pm0.47$ km s$^{-1}$ is typical of disk-like clouds |
| Velocity gradient of CO(1-0) absorption across the central beam | <= 3 km/s across ~10 pc | not stated | km/s | 7 | shows the velocity gradient to be no more than 3 km s$^{-1}$ across $\sim$10 pc |
| Excitation temperature T_ex(2-1) (median) | 7.77 | +1.34/-1.94 (1-sigma); +14.88/-2.90 (3-sigma) | K | 8 | we used the 15.9 to 84.1 (0.14 to 99.87) percentile levels of the $T^{21}_\mathrm{ex}$ distribution to find a median $T^{21}_\mathrm{ex} = 7.77^{+1.34}_{-1.94}\left(^{+14.88}_{-2.90}\right)$ K |
| CO column density N_CO | 1.16e15 | +0.21/-0.28 (1-sigma); +3.55/-0.47 (3-sigma), in 1e15 | cm^-2 | 8 | $N_\mathrm{CO}/10^{15}\,\mathrm{cm}\ensuremath{^{-2}}= 1.16^{+0.21}_{-0.28}\left(^{+3.55}_{-0.47}\right)$ with 1$\sigma$ (3$\sigma$) error bars |
| Excitation temperature T_ex(3-2) (median) | 28.6 | +26.7/-14.9 | K | 8 | we find higher median $T^{32}_\mathrm{ex} = 28.6^{+26.7}_{-14.9}$ K with $N_\mathrm{CO} \sim 10^{16}$ cm$^{-2}$ |
| H2 column density range N_H2 (in 1e20) | 0.92 to 2.3 | +0.68/-0.36 and +1.7/-0.9 (1-sigma) | cm^-2 | 8 | $N_\mathrm{H_2}/10^{20}\,\mathrm{cm}\ensuremath{^{-2}}= 0.92^{+0.68}_{-0.36} - 2.3^{+1.7}_{-0.9}$ (1$\sigma$ uncertainties) |
| RADEX best-fit n_H2 and T_bg for T_K = 10 K | n_H2 ~ 5100 cm^-3; T_bg ~ 62 K | 1-sigma contours do not close; lower limits n_H2 > 1100 cm^-3 and T_bg > 45 K | cm^-3 and K | 9 | best-fitting $n_\mathrm{H_2} \sim 5100$ cm$^{-3}$ and $T_\mathrm{bg} \sim 62$ K; they provide $n_\mathrm{H_2} > 1100$ cm$^{-3}$ and $T_\mathrm{bg} > 45$ K lower limits |
| Core and N2 integrated flux densities at 232.98 GHz (X2c2 imfit) | 1.220 Jy (core); 50.3 mJy (N2) | not stated | Jy; mJy | 10 | flux densities of 1.220 Jy and 50.3 mJy, respectively, at 232.98 GHz |
| Dust mass upper limit (T_dust = 25 K) | < 1.1e4 | upper limit | Msun | 10 | this modified black body $M_\mathrm{dust} < 1.1\times 10^4$ $M_\odot$ would correspond to a total gas mass $M_\mathrm{gas} \lesssim 7.5\times10^5$ $M_\odot$ |
| mm/sub-mm spectral index alpha' from ACA data (program 2021.1.01398.S) | -0.60 | 0.07 | dimensionless | 11 | we measured an apparent mm/sub-mm spectral index $\alpha^{\prime} = -0.60\pm0.07$ |
| mm/sub-mm spectral index alpha' from ALMA 12-m data (2012.1.00661.S and 2015.1.01352.S) | -0.47 | 0.11 (likely underestimated by >= 3x) | dimensionless | 11 | result in a best-fit $\alpha^{\prime} = -0.47\pm0.11$ |
| Change in line-of-sight ozone column during a single EB | up to ~6% over 30 min | not stated | percent | 12 | suggest that either stratospheric or ground-layer $N_\mathrm{O_3}$ along the line of sight changed by up to $\sim$6% over just 30 min. |

## Qualitative findings

- No CO(1-0) emission is clearly identified in the CND, filaments or dusty clouds  
  > "Despite the deep ALMA imaging and multiple spws containing redshifted CO transitions, we did not clearly identify any CO emission." (Conclusion)
- The claimed CO emission and absorption measurements of an earlier analysis are not recovered  
  > "We cannot recover similar emission-line results, and nor do we support their absorption-line measurements." (Introduction)
- A spurious deep absorption feature near redshifted CO(2-1) in X20f was introduced by a mis-flagged ozone line in the bandpass calibrator  
  > "This introduced a spurious and deep absorption feature in the peak continuum spectrum of M87 that was coincidentally very close to redshifted $\nu_\mathrm{CO(2-1)}$ (cite: ray24)." (Manual Flagging)
- The CO absorber is kinematically distinct from the blueshifted atomic-gas absorption and is not interpreted as entrained in an outflow  
  > "and we disfavor interpreting this CO absorber as arising from molecular gas entrained in an outflow." (Conclusion)
- CO excitation does not follow LTE  
  > "CO excitation temperatures spanning $T_\mathrm{ex} \sim 8$ K to $\sim$30 K do not follow local thermodynamic equilibrium (LTE) expectations" (abstract)
- The absorber is most consistent with a thin, pressure-confined filament seen slightly off-center from the nucleus  
  > "Taken together, the observed CO absorption lines are most consistent with a thin, pressure-confined filament seen slightly off-center from the M87 nucleus." (abstract)
- Bandpass calibration limitations can create broad, very low S/N spurious absorption and emission signatures  
  > "demonstrate how bandpass calibration limitations may introduce broad but very low S/N and spurious absorption and emission signatures" (abstract)

## Claim tuples

- H: Does the M87 nucleus host CO(1-0) emission from a circumnuclear disk, ionized filaments or dusty clouds at levels reported earlier? | E: Integrate CO(1-0) line profiles of the archival Band 3 Xa1 (and X5) cubes over HST-defined regions with Monte Carlo noise estimation, then convert limits to H2 mass | R: No unambiguous emission; nuclear S_CO(1-0)dv < 0.109 Jy km/s giving M_H2 < 2.3e5 Msun; global < 4e6 Msun within 2 kpc | F: There is no evidence for a molecular CND; limits are ~20x lower than previous surveys and conflict with ~1e7 Msun claimed earlier | **supported**
- H: Is there extragalactic CO absorption against the bright M87 nucleus? | E: Fit Gaussian profiles to opacity spectra from peak continuum spectra in 6 data sets covering CO(1-0), (2-1) and (3-2) | R: Narrow (sigma ~4.7 km/s) blueshifted absorption at -75 to -84 km/s with tau_CO ~0.02-0.06 km/s | F: CO absorption is detected in three transitions, though CO(2-1) and CO(3-2) are less confident than CO(1-0) | **supported**
- H: Is the CO absorber part of the outflowing atomic gas seen in UV/optical absorption? | E: Compare CO line centroids and widths with literature atomic absorption lines | R: CO is at about -77 km/s with narrow width versus about -131 km/s and FWHM <~300 km/s for the atomic absorber | F: The CO absorber appears kinematically distinct from the outflowing atomic gas | **supported**
- H: What are the physical conditions of the CO absorber (temperature, density, radiation field)? | E: LTE analysis of opacity ratios and Monte Carlo errors, then non-LTE RADEX chi-square grid models | R: T_ex(2-1) ~ 7.8 K, T_ex(3-2) ~ 29 K, N_CO ~ 1.2e15 cm^-2; RADEX best fit n_H2 ~ 5100 cm^-3 and T_bg ~ 62 K for T_K = 10 K, with only lower limits at 1-sigma | F: Non-LTE modelling agrees better than LTE and favours a cold, dense absorber in a hot radiation field | **partially**
- H: Is the CO absorber a gravitationally bound cloud or a filament? | E: Compare sigma_LOS, N_H2, n_H2 and pressure arguments with cloud virial and filament models | R: A bound cloud would need implausibly high surface density; a thin filament with n_H2 > 1000 cm^-3 is consistent but the cold T_K is hard to explain | F: A thin pressure-confined filament is the preferred origin, though no fully coherent explanation is found | **partially**
- H: Are broad weak CO deficits or excesses seen near redshifted CO real outflow or disk signals? | E: Re-do continuum subtraction with wider channel exclusions and compare spw spectra across contemporaneous observations with am telluric models | R: Broad features at ~0.1-0.3% of continuum vary between data sets and match bandpass stability limits | F: They are spurious bandpass calibration patterns, not CO outflow or disk | **supported**

## Reasoning

- Why this data: Archival ALMA gives an order-of-magnitude better resolution and sensitivity than earlier mm interferometers, enabling a deep CO search; the Xa1 and X5 cubes had the best sensitivity and resolution  
  > "which provides an order-of-magnitude improvement in both angular resolution and limiting sensitivity over previous mm-wavelength interferometers" (Introduction); "These had the best combination of sensitivity and angular resolution to detect and isolate possible emission." (CO Emission-line Constraints)
- Why this method: HST dust and Halpha maps are used to define where molecular gas is expected, so integration regions follow the optical gas and dust features  
  > "To create integration regions for this ALMA CO line search, we employed pipeline-calibrated HST images" (Optical Imaging)
- Alternative: Program 2016.1.000415.S excluded because of pipeline calibration difficulties from changing polarization calibrators  
  > "one semipass program (2016.1.000415.S; PI: Marti-Vidal) was not included due to pipeline calibration difficulties arising from changing polarization calibrators between Execution Blocks" (Archival ALMA Imaging)
- Alternative: Reconstructing ALMA interferometric-mode calibration tables for the .V programs was not attempted  
  > "because reconstructing the ALMA interferometric-mode calibration tables is beyond the scope of this archival project (cite: goddi19)" (Calibration Processes)
- Alternative: Molecular outflow interpretation of the CO absorber rejected  
  > "and we disfavor interpreting this CO absorber as arising from molecular gas entrained in an outflow." (Conclusion)
- Alternative: Spherical gravitationally bound cloud rejected in favour of a thin filament  
  > "that is not consistent with a spherical, gravitationally bound cloud" (Conclusion)
- How they decided it was enough: _not stated_
- Limitation (authors): Bandpass calibration effects on tau_0 and tau_CO are not quantified  
  > "However, we do not attempt to quantify here the bandpass calibration effects on" (CO Absorption-line Properties)
- Limitation (authors): CO(3-2) and CO(2-1) opacities are less reliable than CO(1-0), so LTE reconciliation is not attempted  
  > "Unfortunately, neither $\tau_\mathrm{CO(3-2)}$ or $\overline{\tau}_\mathrm{CO(2-1)}$ values are as reliable as is $\overline{\tau}_\mathrm{CO(1-0)}$" (Temperature and Column Densities)
- Limitation (authors): Xa1 maximum recoverable scale cannot entirely rule out diffuse emission over larger regions  
  > "cannot entirely rule out diffuse emission spread out over a couple of the larger regions with $\sim$5$''$ extent" (Channel Maps)
- Limitation (authors): No interferometric-mode calibration tables for .V data, so phase self-calibration is not possible and peak flux densities are lower by ~30%  
  > "Without interferometric-mode calibration tables, phase self-calibration is not possible" (Calibration Processes)
- Limitation (authors): No fully coherent physical explanation of sigma_LOS, T_K, N_H2 and n_H2 for the absorber  
  > "but do not find a fully coherent explanation for the measured" (Origin of the CO Absorption)
- Caveat (inferred, ours): CO(2-1) detections depend on ozone-line correction (tau suppressed by 20-30%); one CO(2-1) point is only S/N ~1.4
- Caveat (inferred, ours): The CO(3-2) centroid is ~3 sigma discrepant, and T_ex(3-2) has large errors, so LTE/non-LTE conclusions rest on low-S/N data
- Caveat (inferred, ours): RADEX fit uses fixed N_CO and FWHM and a 1-sigma contour that does not close, so n_H2 and T_bg are weakly constrained
- Caveat (inferred, ours): Absorber location (foreground filament versus near-nuclear) rests on a T_bg interpretation that is degenerate with n_H2
- Caveat (inferred, ours): Non-detection limits depend on HST-defined region shapes and alpha_CO = 3.1 and may differ for another region choice
- Caveat (inferred, ours): Conclusions about spurious broad features rely on qualitative comparison of spws rather than a quantitative bandpass model

## Reproducibility

- Data public (paper): All ALMA data are archival from the ALMA archive; HST data from MAST  
  > "We obtained archival ALMA 12-m imaging from eleven single-pointing data sets" (Archival ALMA Imaging); "we employed pipeline-calibrated HST images retrieved from the Mikulski Archive for Space Telescopes" (Optical Imaging)
- Products in archive: Archive calibration scripts and calibration tables used (including manual flagging); authors' derived products not stated as archived  
  > "calibration scripts from the archive often included manual flagging of the science target as well as the flux and bandpass calibrators" (Manual Flagging)
- Missing: CASA and pipeline versions and per-EB self-calibration parameters
- Missing: Imaging parameters (robust for MFS, cell and image size, thresholds, masks) and exact spw and channel selections
- Missing: Region definitions for the HST-derived integration regions and MGE parameters
- Missing: Exact fitting windows and Hanning treatment for the absorption-line fits, and the RADEX chi-square setup
- Missing: Kappa value for the dust mass limit
- Missing: No analysis code released
- Data volume (inferred): Large: about 11 12-m single-pointing EBs plus about 30 ACA EBs; raw plus calibrated MS likely several hundred GB to over 1 TB
- Score (inferred): 3/5, Data are public and the main results are numeric with clear equations and MC procedures, but many calibration, imaging and region-definition parameters are not stated and no code is released.
- Rediscovery candidate: yes, Public archival data, a mostly complete recipe (uvcontsub, Gaussian opacity fits, LTE and RADEX equations) and numeric results (tau, N_CO, M_H2 limit) allow an independent attempt, though region definitions and imaging parameters must be re-derived.

## Links

- Method: (cite: hunter18) (Ozone telluric correction and atmospheric line identification in ALMA data)
- Method: (cite: kameno14) (Bandpass calibration stability limits used to interpret broad features)
- Method: (cite: boizelle17) (Monte Carlo resampling of line-profile integration regions)
- Method: (cite: davidson24) (Iterative masking of non-stellar features for the HST stellar fit)
- Method: (cite: godard2010; rose19b) (Column-density and excitation equations for absorption lines)
- Companion: (cite: ray24) (Earlier analysis of two of the same ALMA data sets claiming CO emission and absorption that this paper disputes)
- Companion: (cite: simionescu18) (ALMA CO(2-1) detection of a molecular cloud ~40 arcsec southeast of the nucleus)
- Companion: (cite: tan08) (Previous SMA CO(2-1) tentative detection and upper limit)
- Companion: (cite: osorno23) (Ionized-gas kinematics of the M87 circumnuclear disk and filaments)
- Related: EHT+ALMA VLBI campaigns (APP-mode .V programs)
- Related: ACA monitoring of M87 around EHT campaigns in 2021 and 2022
- Related: Calibration programs of ALMA flux and bandpass monitoring

## Checks

```json
{
 "quotes": 224,
 "quotes_ok": 224,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 14,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.0.00001.CAL"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2013.1.00862.S",
  "2016.1.000415.S"
 ],
 "numeric_results": 22,
 "numeric_problems": 0,
 "fill": {
  "facts": 158,
  "stated": 136,
  "rate": 0.861
 },
 "evidence_ok": true
}
```
