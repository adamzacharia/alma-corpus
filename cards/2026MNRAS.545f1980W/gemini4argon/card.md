# SDSS-ALMA Legacy Value Archival Gas Exploration (SALVAGE) ─ I. Global star formation is governed by central (not global) molecular gas

`2026MNRAS.545f1980W` | Monthly Notices of the Royal Astronomical Society 2026 | first author: Wilkinson, Scott | arXiv: 2511.06775 | DOI: 10.1093/mnras/staf1980

Card schema 1.0 | model gemini-4-argon | depth full | type archival_reuse

## Science

- Fields: nearby_galaxies, star_formation
- Question: What role does the spatial distribution of molecular gas and star formation efficiency in the inner versus outer regions play in driving global star formation scaling relations and galaxy quenching?  
  > "With the relative inner and outer distributions of molecular gas fraction and star formation efficiency, we investigate whether the central star formation driving global changes is due to fuel availability or efficiency." (Abstract); "Thus, we now ask the question *does central gas dictate global star formation?*" (What dictates global star-formation?)
- Target **SALVAGE sample (277 SDSS-ALMA galaxies)**: coordinates declination < +47 deg  
  > "To this end, we have assembled a sample of 277 galaxies ($0.02 \lesssim z \lesssim 0.25$) with semi-resolved optical and millimetre $^{12}$CO (1–0) data, wherein the properties of the inner $\thicksim$2 kpc can be distinguished from the outer regions." (Abstract); "In this work, we use the spectroscopic redshifts and require that the spectra are classified as galaxies or quasars." (SDSS Spectroscopic Catalogues); "568,876 have a declination less than +47$^\circ$ (corresponding to an elevation of 20 degrees at the ALMA site) and are thus possibly visible by ALMA." (GalaxyZoo Morphology Catalogue); z/distance 0.02 <= z <= 0.25 (median z = 0.044)  
  > "To this end, we have assembled a sample of 277 galaxies ($0.02 \lesssim z \lesssim 0.25$) with semi-resolved optical and millimetre $^{12}$CO (1–0) data, wherein the properties of the inner $\thicksim$2 kpc can be distinguished from the outer regions." (Abstract); "In this work, we use the spectroscopic redshifts and require that the spectra are classified as galaxies or quasars." (SDSS Spectroscopic Catalogues); "568,876 have a declination less than +47$^\circ$ (corresponding to an elevation of 20 degrees at the ALMA site) and are thus possibly visible by ALMA." (GalaxyZoo Morphology Catalogue); distance from SDSS spectroscopic redshifts with flat LambdaCDM cosmology (Omega_M = 0.3, Omega_Lambda = 0.7, H_0 = 70 km s^-1 Mpc^-1)  
  > "To this end, we have assembled a sample of 277 galaxies ($0.02 \lesssim z \lesssim 0.25$) with semi-resolved optical and millimetre $^{12}$CO (1–0) data, wherein the properties of the inner $\thicksim$2 kpc can be distinguished from the outer regions." (Abstract); "In this work, we use the spectroscopic redshifts and require that the spectra are classified as galaxies or quasars." (SDSS Spectroscopic Catalogues); "568,876 have a declination less than +47$^\circ$ (corresponding to an elevation of 20 degrees at the ALMA site) and are thus possibly visible by ALMA." (GalaxyZoo Morphology Catalogue)

## Data provenance

- ALMA projects: 2011.0.00374.S, 2012.1.00539.S, 2013.1.00058.S, 2013.1.00096.S, 2013.1.00115.S, 2013.1.00530.S, 2013.1.01383.S, 2015.1.00320.S, 2015.1.00389.S, 2015.1.00405.S, 2015.1.00587.S, 2015.1.00820.S, 2015.1.01012.S, 2015.1.01120.S, 2015.1.01225.S, 2016.1.00177.S, 2016.1.00329.S, 2016.1.00852.S, 2016.1.00948.S, 2016.1.01172.S, 2016.1.01265.S, 2016.1.01269.S, 2017.1.00025.S, 2017.1.00496.S, 2017.1.00601.S, 2017.1.00629.S, 2017.1.01093.S, 2017.1.01727.S, 2018.1.00541.S, 2018.1.00558.S, 2018.1.00940.S, 2018.1.01852.S, 2019.1.00260.S, 2019.1.00597.S, 2019.1.01136.S, 2019.1.01757.S, 2021.1.00094.S, 2021.1.00602.S, 2021.1.01089.S, 2022.1.00482.S
- bands: Band 3 (~2.7 mm)  
  > "At the redshift range considered in this work, the 115 GHz $^{12}$CO (1–0) emission line (henceforth CO) is covered by ALMA band 3 ($\thicksim$2.7 mm)." (Data Products from the ALMA Science Archive)
- frequencies and spectral setup: Redshifted 115.27 GHz 12CO(1-0) line; target velocity resolution 25 km/s; 1000 km/s coverage on either side of line  
  > "Must have $^{12}$CO (1–0) line coverage according to the redshifted 115.27 GHz line (using the SDSS spectroscopic redshift) falling within the reported bandwidth." (The SDSS-ALMA Crossmatched Sample); "We select a target velocity resolution of 25 km/s (using `channel_kms` in the key files) to ensure the spectral line is well sampled but also to maximize signal-to-noise." (Imaging); "We choose to include 1000 km/s of spectral coverage on either side of the redshifted CO line frequency to ensure there are sufficient channels to compute robust noise statistics, but also minimize data volume." (Imaging)
- continuum bandwidth: _not stated_
- arrays: 12 m main array (50 antennas)  
  > "In this work, we use archival data from the main array, which accounts for 50 antennas, each with dishes 12 m in diameter, that operate together as an interferometric telescope." (Data Products from the ALMA Science Archive)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: < 3 arcsec (typical beam size ~1-3 arcsec)  
  > "Must have a reported spatial resolution smaller than the SDSS central fibre (3 arcsec)." (The SDSS-ALMA Crossmatched Sample); "Since the typical beam size in SALVAGE ($\thicksim 1-3$") is similar to the PHANGS 12 m data ($\thicksim 1-2$"), we use the same cleaning scales of 0, 1, 2.5, 5.0 arcseconds" (Imaging)
- max recoverable scale: > 1.5 Petrosian radii  
  > "Must have a maximum resolvable scale larger than 1.5 Petrosian radii so as to not resolve out significant flux." (The SDSS-ALMA Crossmatched Sample)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: Cycles 0 through 9+ (up to October 16 2024)  
  > "As of October 16 2024, the entirety of the ALMA Science Archive contained 40,934 unique targets." (Data Products from the ALMA Science Archive); "Observations in our sample that were observed in Cycles 0, 1, or 2 were never pipeline calibrated, and thus no script is provided to either restore or run pipeline calibrations." (Calibration)
- pi or archival as stated: archival  
  > "Moreover, we are able to do so using purely archival data from SDSS and ALMA." (SALVAGE Data Collation and Processing)
- Line: 12CO 1-0 (115.27 GHz)
- Other facility **SDSS (2.5 m telescope at Apache Point Observatory)**: DR7 optical spectra (3 arcsec central fibre) and ugriz broadband photometry (Model magnitudes, Fibre magnitudes, Petrosian half-light radii, spectroscopic redshifts)  
  > "The seventh data release of the SDSS (cite: SDSS-DR7) includes optical spectra and *ugriz* broadband photometry for over 900,000 galaxies" (Data Products from the Sloan Digital Sky Survey); "The SDSS spectra have a spectral resolution of R $=\lambda/\Delta\lambda\thicksim$ 800-2200 over the wavelength range 3800-9200 Å and are collected from optical fibres which have an on-sky aperture of three arcseconds." (Data Products from the Sloan Digital Sky Survey)
- Other facility **Dark Energy Camera Legacy Survey (DECaLS)**: Optical gri imaging and morphology inputs for Galaxy Zoo DESI catalogue  
  > "Although our optical data come primarily from SDSS, SALVAGE has complete coverage within the Dark Energy Camera Legacy Survey (cite: Dey19), which provides slightly deeper (23.54 mag 5$\sigma$ point source depth in the $r$-band) and higher-resolution (1.18" FWHM) imaging than SDSS" (GalaxyZoo Morphology Catalogue); "In the left panel of Figure 1, we show the 50" $\times$ 50" *gri* colour image drawn from DECaLS (cite: Dey19)." (Computing molecular gas mass)
- Other facility **CANFAR Science Platform**: Cloud computing, storage, and pre-installed CASA versions for ALMA data reduction  
  > "As such, the work described here is done on the CANFAR Science Platform, which we will refer to throughout." (Data Products from the ALMA Science Archive); "In total, we required 13 different versions of CASA (ranging from v4.2.2 to v6.5.4) that are pre-installed on the CANFAR Science Platform." (Calibration)
- External data: MPA-JHU DR7 catalogue of emission line fluxes, inner/outer/total stellar masses, and inner/outer/total star formation rates  
  > "The Max-Planck-Institute for Astrophysics–John Hopkins University (MPA-JHU) catalogues provide flux measurements of up to 12 emission lines, photometric stellar mass estimates, and hybrid photometry/spectral index SFR estimates (cite: K03; Tremonti04; Brinchmann04)." (Ancillary Data Products from MPA-JHU) [from (cite: K03; Tremonti04; Brinchmann04)]
- External data: Galaxy Zoo DESI morphology catalogue (edge-on disk, merger disturbance, and bar fractions)  
  > "We use the Galaxy Zoo DESI morphology catalogue (cite: Walmsley23) trained on DECaLS Galaxy Zoo responses to predict key morphological features." (GalaxyZoo Morphology Catalogue) [from (cite: Walmsley23)]
- External data: xCOLD GASS and MASCOT global CO luminosities and molecular gas masses for validation and comparison  
  > "19 targets in SALVAGE have previous unresolved global CO measurements from xCOLD GASS (14 targets in common) and MASCOT (5 targets in common)." (Quality Assurance); "Since we are investigating *global* scaling relations of CO-detected galaxies, we compare to CO-detected galaxies from the large and representative (but unresolved) xCOLDGASS (cite: Saintonge17)." (A semi-resolved perspective on global scaling relations) [from (cite: Saintonge17), (cite: Wylezalek22)]
- External data: GALEX-Sloan-WISE Legacy Catalogue (GSWLC-A1) photometric global SFRs and stellar masses  
  > "To address the potential for errors introduced by mixing the inner (spectroscopic) and outer (photometric) components to obtain the total SFR, we compare the total SFRs used in this work with photometric-only total SFRs from the GSWLC (cite: Salim16)." (Comparing MPA-JHU SFRs to GSWLC) [from (cite: Salim16)]

## Processing

### Calibration

- pipeline or manual: Pipeline restoration for Cycle 3+; calibrated measurement sets provided by ALMA Help Desk for Cycles 0, 1, and 2 (46 targets)  
  > "For observations from Cycle 3 or later, we restore the pipeline calibrations using the script included with the downloaded data." (Calibration); "Observations in our sample that were observed in Cycles 0, 1, or 2 were never pipeline calibrated, and thus no script is provided to either restore or run pipeline calibrations. For the 46 such targets from these first three cycles, the calibrated measurement sets were provided to us by the ALMA Help Desk staff." (Calibration)
- casa version: 13 versions ranging from v4.2.2 to v6.5.4  
  > "In total, we required 13 different versions of CASA (ranging from v4.2.2 to v6.5.4) that are pre-installed on the CANFAR Science Platform." (Calibration)
- pipeline version: _not stated_
- archive products used as is: No, raw visibilities were calibrated and re-imaged  
  > "While the optical data in SDSS have been reduced and compiled into catalogues, the ALMA data are uncalibrated and unprocessed." (SALVAGE Data Collation and Processing)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA tclean (via PHANGS-ALMA imaging pipeline)  
  > "Motivated by the need to image hundreds of observations efficiently and in a way that is reproducible by others, we automate our imaging using the pipeline developed by the PHANGS-ALMA team (cite: Leroy21)." (Imaging); "The pipeline then images the data with the `CASA` task `tclean` in a two-step process." (Imaging)
- deconvolver: Two-step: multiscale CLEAN in step 1, standard single-scale Hogbom CLEAN in step 2  
  > "In the first imaging step, the pipeline uses multiscale cleaning with the goal of producing a reliable map to use as input to the second stage of cleaning." (Imaging); "In the second imaging step, the pipeline uses the standard single-scale CLEAN algorithm (cite: Hogbom74) to produce a final deconvolved cube." (Imaging)
- weighting robust: Briggs weighting with robust = 0.5  
  > "Throughout the cleaning process, visibilities are weighted using a Briggs scheme with robust = 0.5, the cell size is chosen to be a round number that samples the minor axis of the beam by $\gtrsim4$, and the primary beam cutoff is set to 0.25." (Imaging)
- uv taper: _not stated_
- cell size: Round number sampling the minor axis of the beam by >= 4  
  > "Throughout the cleaning process, visibilities are weighted using a Briggs scheme with robust = 0.5, the cell size is chosen to be a round number that samples the minor axis of the beam by $\gtrsim4$, and the primary beam cutoff is set to 0.25." (Imaging)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: 0, 1, 2.5, 5.0 arcseconds  
  > "Since the typical beam size in SALVAGE ($\thicksim 1-3$") is similar to the PHANGS 12 m data ($\thicksim 1-2$"), we use the same cleaning scales of 0, 1, 2.5, 5.0 arcseconds (but found that our results did not change significantly with deviations from this)." (Imaging)
- continuum subtraction: CASA uvcontsub with order 0 polynomial using only the spectral window containing the CO line  
  > "The pipeline then conducts a continuum subtraction using the `CASA` task `uvcontsub`. The continuum is fit with an order 0 polynomial using only the spectral window that contains the CO line (and separately for each individual case, if there are multiple observations)." (Imaging)
- line free channels: _not stated_
- primary beam correction: Primary beam cutoff set to 0.25  
  > "Throughout the cleaning process, visibilities are weighted using a Briggs scheme with robust = 0.5, the cell size is chosen to be a round number that samples the minor axis of the beam by $\gtrsim4$, and the primary beam cutoff is set to 0.25." (Imaging)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: ~1-3 arcsec  
  > "Since the typical beam size in SALVAGE ($\thicksim 1-3$") is similar to the PHANGS 12 m data ($\thicksim 1-2$"), we use the same cleaning scales of 0, 1, 2.5, 5.0 arcseconds" (Imaging)
- final rms: _not stated_

### Inherited from earlier work

- ALMA imaging pipeline architecture, masking, and post-processing procedures  
  > "Motivated by the need to image hundreds of observations efficiently and in a way that is reproducible by others, we automate our imaging using the pipeline developed by the PHANGS-ALMA team (cite: Leroy21)." (Imaging); "For any other details, we again refer the reader to (cite: Leroy21)." (Imaging) [from (cite: Leroy21)]
- Full width at zero intensity (FWZI) method for integrating CO line flux  
  > "We do this using the “full width at zero intensity" method (FWZI) also employed in VERTICO (cite: Brown21)." (Computing molecular gas mass) [from (cite: Brown21)]
- Assumed line width of 300 km/s for CO non-detection upper limits  
  > "In the case of non-detections of $S_\text{CO}$ where the signal-to-noise ratio is less than 5, we compute an upper limit assuming a line width of 300 km/s (cite: Saintonge17) as $\sigma\Delta V\sqrt{N}$" (Computing molecular gas mass) [from (cite: Saintonge17)]
- CO line luminosity equation  
  > "We convert the observed line fluxes ($S_\text{CO}$) to CO integrated line luminosities ($L'_\text{CO}$), following equation (3) from (cite: Solomon05):" (Computing molecular gas mass) [from (cite: Solomon05)]
- Constant Milky Way CO-to-H2 conversion factor alpha_CO = 4.35 M_sun (K km s^-1 pc^2)^-1 and alternative metallicity and surface-density dependent prescription  
  > "where $\alpha_\text{CO} = 4.35$ M$_\odot$ (K km s$^{-1}$ pc$^{2}$)$^{-1}$ (cite: Schinnerer24)." (Computing molecular gas mass); "Following the work by (cite: Chiang24), (cite: Schinnerer24) recommend an $\alpha_\text{CO}$ that varies from the constant Milky Way conversion factor of $\alpha_\text{CO} = 4.35$ M$_\odot$ (K km s$^{-1}$ pc$^{2}$)$^{-1}$" (On the assumption of a constant $\alpha_{CO}$) [from (cite: Schinnerer24), (cite: Chiang24)]
- Gas-phase metallicity calibration from [OIII] and [NII] emission lines  
  > "We measure the gas-phase metallicity within the SDSS fibre from the \[OIII\] and \[NII\] emission lines following (cite: Curti17) and an assumed $12 + \log\left({\text{O}/\text{H}}\right)_\odot$ of 8.69 (cite: Asplund09; Chiang24)." (On the assumption of a constant $\alpha_{CO}$) [from (cite: Curti17)]
- Post-starburst galaxy classification method  
  > "The post-mergers in the green valley with $\log{f_\text{gas, inner} / f_\text{gas, outer}} > 0$ are indeed post-starburst galaxies as classified by the methods in (cite: Wilkinson22)." (On the utility of the gas fraction ratio) [from (cite: Wilkinson22)]

### Not stated but needed to reproduce (our reading)

- Exact CASA version used to image the cubes inside the PHANGS-ALMA pipeline (13 versions from v4.2.2 to v6.5.4 are listed for calibration restoration, but the imaging CASA version is not specified)
- Exact line-free velocity channels excluded during uvcontsub continuum fitting for each individual galaxy
- Details of the manual calibration recipes applied by the ALMA Help Desk for the 46 Cycle 0-2 targets

## Analysis recipe

1. **Crossmatch SDSS DR7 and ALMA Science Archive and select sample**: Query ALMA Science Archive with pyVO and crossmatch to SDSS DR7 MPA/JHU sample (Dec < +47 deg) using astropy match_to_catalog_sky within 4 r-band Petrosian radii; filter by CO(1-0) coverage, spatial resolution < 3 arcsec, MRS > 1.5 Petrosian radii, and remove duplicates  
  > "We query the ALMA Science Archive using `pyVO` and match to SDSS using `match_to_catalog_sky` function from `astropy` (cite: Astropy1; Astropy2; Astropy3), which yields 739 unique matches with an on-sky matching tolerance of four SDSS $r$-band Petrosian radii" (The SDSS-ALMA Crossmatched Sample); "After the SDSS crossmatch to the ALMA archive and sample selection, we move forward with processing a sample of 298 targets." (The SDSS-ALMA Crossmatched Sample)
   - software: pyVO, astropy, ALMiner
   - parameter: Matching tolerance = 4 SDSS r-band Petrosian radii; QA2 PASS; scan_intent=TARGET; spatial resolution < 3 arcsec; MRS > 1.5 Petrosian radii  
  > "which yields 739 unique matches with an on-sky matching tolerance of four SDSS $r$-band Petrosian radii and where the data product type is a spectral cube meeting the quality requested by the original PIs (QA2 PASS and `scan_intent=TARGET`)." (The SDSS-ALMA Crossmatched Sample); "Must have a reported spatial resolution smaller than the SDSS central fibre (3 arcsec)." (The SDSS-ALMA Crossmatched Sample); "Must have a maximum resolvable scale larger than 1.5 Petrosian radii so as to not resolve out significant flux." (The SDSS-ALMA Crossmatched Sample)
   - fitting: _not stated_
   - validation: _not stated_
2. **Calibrate and image ALMA CO(1-0) visibilities**: Restore pipeline calibrations in CASA (or use Help Desk MS for Cycles 0-2), split science targets, subtract continuum with uvcontsub, regrid velocity with mstransform, and run two-stage multiscale + single-scale tclean via the PHANGS-ALMA pipeline  
  > "For observations from Cycle 3 or later, we restore the pipeline calibrations using the script included with the downloaded data." (Calibration); "The pipeline then conducts a continuum subtraction using the `CASA` task `uvcontsub`." (Imaging); "The pipeline then images the data with the `CASA` task `tclean` in a two-step process." (Imaging)
   - software: CASA, split, uvcontsub, mstransform, tclean, PHANGS-ALMA pipeline
   - parameter: Target velocity resolution = 25 km/s; spectral coverage = +/- 1000 km/s; multiscale scales = 0, 1, 2.5, 5.0 arcsec; single-scale clean down to S/N = 1; Briggs robust = 0.5; primary beam cutoff = 0.25  
  > "We select a target velocity resolution of 25 km/s (using `channel_kms` in the key files) to ensure the spectral line is well sampled but also to maximize signal-to-noise." (Imaging); "Since the typical beam size in SALVAGE ($\thicksim 1-3$") is similar to the PHANGS 12 m data ($\thicksim 1-2$"), we use the same cleaning scales of 0, 1, 2.5, 5.0 arcseconds" (Imaging); "Throughout the cleaning process, visibilities are weighted using a Briggs scheme with robust = 0.5, the cell size is chosen to be a round number that samples the minor axis of the beam by $\gtrsim4$, and the primary beam cutoff is set to 0.25." (Imaging)
   - fitting: Order 0 polynomial continuum fit in uvcontsub  
  > "The continuum is fit with an order 0 polynomial using only the spectral window that contains the CO line (and separately for each individual case, if there are multiple observations)." (Imaging)
   - validation: Visual inspection of optical images, CO spectral cubes, and spectra (removing 21 galaxies due to off-centre fibres, bad noise structure, or failed reduction, leaving 277 galaxies)  
  > "The optical image from DECaLS, the imaged CO spectral cube from ALMA, and the inner/outer/total integrated spectra were visually inspected to ensure that the data are suitable for our work." (Quality Assurance); "In total, we have 21 cases for which the data could not be included in SALVAGE. This quality assurance check brings our sample size to 277." (Quality Assurance)
3. **Extract inner, outer, and total CO spectra and compute molecular gas masses**: Spatially sum cube pixels in inner (r < 1.5 arcsec), outer (1.5 arcsec to 4 SDSS photometric scale lengths), and total (r < 4 scale lengths) apertures; integrate CO flux using FWZI (1 peak for inner, 3 peaks for outer) with spectral-cube; compute RMS from outer 200 km/s; convert flux to L'_CO and M_mol  
  > "for the inner spectrum, we include pixels within the central 3"-diameter aperture; for the outer spectrum, we include pixels that fall within an annulus with a radial extent from 1.5" to the 4 scale lengths of the best fit SDSS photometric model;" (Computing molecular gas mass); "Next, we measure the CO line emission ($S_\text{CO}$) from each spectrum using `spectral-cube`." (Computing molecular gas mass); "The CO integrated line luminosity is converted to a molecular gas mass estimate, $M_\text{mol}$, using a constant conversion factor:" (Computing molecular gas mass)
   - software: spectral-cube
   - parameter: Inner diameter = 3 arcsec; outer annulus = 1.5 arcsec to 4 scale lengths; RMS region = outer 200 km/s (~16 channels); detection threshold S/N > 5; upper limit line width = 300 km/s (~12 channels)  
  > "The spectrum root mean square (RMS) noise is computed from the standard deviation measured from the outer 200 km/s on either side of the summed spectrum; therefore, the noise is computed over the $\thicksim$16 channels furthest from the emission line." (Computing molecular gas mass); "In the case of non-detections of $S_\text{CO}$ where the signal-to-noise ratio is less than 5, we compute an upper limit assuming a line width of 300 km/s (cite: Saintonge17) as $\sigma\Delta V\sqrt{N}$" (Computing molecular gas mass)
   - assumption: Flat LambdaCDM cosmology (Omega_M = 0.3, Omega_Lambda = 0.7, H_0 = 70 km s^-1 Mpc^-1) and constant alpha_CO = 4.35 M_sun (K km s^-1 pc^2)^-1  
  > "Throughout, we assume a flat $\Lambda$CDM cosmology with $\Omega_\text{M} = 0.3$, $\Omega_\Lambda = 0.7$, and H$_0 = 70$ km s$^{-1}$ Mpc$^{-1}$." (Introduction); "where $\alpha_\text{CO} = 4.35$ M$_\odot$ (K km s$^{-1}$ pc$^{2}$)$^{-1}$ (cite: Schinnerer24)." (Computing molecular gas mass)
   - fitting: _not stated_
   - validation: Comparison of 19 overlapping targets with xCOLD GASS and MASCOT (median L'_CO difference of 0.02 dex with 0.09 dex scatter for 12 detections) and sensitivity test with metallicity/surface-density dependent alpha_CO  
  > "The median difference between our measurement of $L'_\text{CO}$ and those in xCOLD GASS/MASCOT for these 12 detections is 0.02 dex ($\thicksim$5%) with a scatter around zero of $\thicksim$0.09 dex, which is similar to the typical error on xCOLD GASS luminosities ($\thicksim$0.07 dex)." (Quality Assurance); "To test whether our qualitative results are significantly affected by our choice of $\alpha_\text{CO}$, we recompute $f_\text{gas, inner}$ and SFE$_\text{inner}$ for every galaxy in SALVAGE using the (cite: Schinnerer24) recommended prescription." (On the assumption of a constant $\alpha_{CO}$)
4. **Compute multi-wavelength scaling parameters and correlate global Delta_SFR with semi-resolved gas fractions**: Filter for 175 non-edge-on galaxies with secure CO detections (M_mol,total S/N > 5 and either inner or outer S/N > 5); compute sSFR, Delta_SFR, f_gas, and SFE in inner, outer, and total regions; compute Pearson r and intrinsic scatter between Delta_SFR and gas fractions using ltsfit  
  > "There are 175 galaxies in SALVAGE for which a total $M_\text{mol}$ and either an inner or outer $M_\text{mol}$ are securely detected." (Results); "We measure the causal relationship between global $\Delta$SFR and the various gas fractions using the Pearson correlation coefficient (r), which quantifies the linear correlation between two variables, and the intrinsic scatter, accounting for errors on the SFR, M$_\star$ and M$_\text{mol}$ measurements with the `ltsfit` Python package (cite: Cappellari2013a)." (What dictates global star-formation?)
   - software: ltsfit
   - parameter: disk-edge-on_yes_fraction <= 0.5; SFMS matching tolerances: delta_z = 0.005, delta_M* = 0.1 dex, delta_Sigma_5 = 0.1 dex (minimum 5 galaxies); outlier clipping disabled in ltsfit  
  > "where $\log{\text{SFR}_\text{MS}}$ is median SFR of star-forming galaxies (as classified by the (cite: K03) classification, with S/N$>3$) within a tolerance of 0.005 in $z$, 0.1 dex in $M_\star$, and 0.1 dex in $\Sigma_5$." (Multi-wavelength Data Products); "We also remove edge-on galaxies using the DESI GalaxyZoo classification (`disk-edge-on_yes_fraction` $> 0.5$) to ensure that the SDSS fibre probes the central region of the galaxy and not the inclined disk." (Results); "Our measurements exclude any upper limit estimates (though our qualitative results do not change if we include upper limits at face value) and we disable outlier clipping in the `ltsfit` intrinsic scatter measurement." (What dictates global star-formation?)
   - fitting: Linear correlation and intrinsic scatter accounting for measurement errors in ltsfit with outlier clipping disabled  
  > "We measure the causal relationship between global $\Delta$SFR and the various gas fractions using the Pearson correlation coefficient (r), which quantifies the linear correlation between two variables, and the intrinsic scatter, accounting for errors on the SFR, M$_\star$ and M$_\text{mol}$ measurements with the `ltsfit` Python package (cite: Cappellari2013a)." (What dictates global star-formation?)
   - validation: Re-ran correlation and intrinsic scatter analysis using GSWLC-A1 photometric global SFRs and stellar masses instead of MPA-JHU  
  > "Comparing the Pearson correlation coefficients and intrinsic scatter measurements in this test with those in Figure 6, we find that in all cases the strength of the relationship between global $\Delta$SFR and gas fraction is weaker (in terms of both correlation and scatter) when using GSWLC measurements of SFR and stellar mass. More importantly, the relative strength of the correlations remains the same; $f_\text{gas, inner}$ correlates more strongly with $\Delta$SFR$_\text{GSWLC}$ than $f_\text{gas, total}$." (Changing global SFR methods does not impact our results)

## Software

- **pyVO** : Querying the ALMA Science Archive  
  > "We query the ALMA Science Archive using `pyVO` and match to SDSS using `match_to_catalog_sky` function from `astropy` (cite: Astropy1; Astropy2; Astropy3)" (The SDSS-ALMA Crossmatched Sample)
- **astropy** : Crossmatching SDSS and ALMA catalogues on the sky using match_to_catalog_sky  
  > "We query the ALMA Science Archive using `pyVO` and match to SDSS using `match_to_catalog_sky` function from `astropy` (cite: Astropy1; Astropy2; Astropy3)" (The SDSS-ALMA Crossmatched Sample)
- **CASA** 13 versions ranging from v4.2.2 to v6.5.4: Restoring ALMA pipeline calibrations, splitting measurement sets, continuum subtraction, velocity regridding, and tclean imaging  
  > "In total, we required 13 different versions of CASA (ranging from v4.2.2 to v6.5.4) that are pre-installed on the CANFAR Science Platform." (Calibration); "The pipeline then images the data with the `CASA` task `tclean` in a two-step process." (Imaging)
- **split** : Isolating science targets from calibrators and multi-target measurement sets in CASA  
  > "The science data are isolated from other data in the measurement set (i.e. calibrators) using the `CASA` task `split`." (Imaging)
- **uvcontsub** : Subtracting continuum emission from visibilities in CASA  
  > "The pipeline then conducts a continuum subtraction using the `CASA` task `uvcontsub`." (Imaging)
- **mstransform** : Regridding visibility data to a common velocity grid in CASA  
  > "The data are then regridded to a common velocity grid that is unique to each galaxy using `CASA` task `mstransform`." (Imaging)
- **tclean** : Two-step multiscale and single-scale deconvolution of CO spectral cubes in CASA  
  > "The pipeline then images the data with the `CASA` task `tclean` in a two-step process." (Imaging)
- **PHANGS-ALMA pipeline** : Automated staging, continuum subtraction, velocity regridding, imaging, and post-processing of ALMA CO cubes  
  > "Motivated by the need to image hundreds of observations efficiently and in a way that is reproducible by others, we automate our imaging using the pipeline developed by the PHANGS-ALMA team (cite: Leroy21)." (Imaging)
- **ALMiner** : Downloading archival ALMA data  
  > "It downloads the data with `ALMiner` (cite: ALMiner), calibrates the data, prepares the key files for the PHANGS pipeline, and runs the PHANGS pipeline, for each galaxy." (Imaging)
- **spectral-cube** : Measuring CO line emission from extracted inner, outer, and total spectra  
  > "Next, we measure the CO line emission ($S_\text{CO}$) from each spectrum using `spectral-cube`." (Computing molecular gas mass)
- **ltsfit** : Fitting linear correlations and computing intrinsic scatter between Delta_SFR and gas fractions while accounting for measurement errors  
  > "We measure the causal relationship between global $\Delta$SFR and the various gas fractions using the Pearson correlation coefficient (r), which quantifies the linear correlation between two variables, and the intrinsic scatter, accounting for errors on the SFR, M$_\star$ and M$_\text{mol}$ measurements with the `ltsfit` Python package (cite: Cappellari2013a)." (What dictates global star-formation?)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Final SALVAGE sample size | 277 | not stated | dimensionless | 2 | This quality assurance check brings our sample size to 277. |
| CO-detected non-edge-on analysis subsample size | 175 | not stated | dimensionless | 4 | There are 175 galaxies in SALVAGE for which a total $M_\text{mol}$ and either an inner or outer $M_\text{mol}$ are securely detected. |
| Median redshift of SALVAGE sample | 0.044 | not stated | dimensionless | 1 | Objects in SALVAGE have a range of redshifts from $\thicksim0.02$ to $\thicksim0.25$ with a median of $0.044$. |
| Median radius of central region probed by SDSS fibre | 1.3 | not stated | kpc | 1 | The radii of the central region probed by the SDSS fibre size ranges from $\thicksim$0.5-6 kpc, with a median of 1.3 kpc. |
| Median difference in L'_CO between SALVAGE and xCOLD GASS / MASCOT | 0.02 | 0.09 | dex | 3 | The median difference between our measurement of $L'_\text{CO}$ and those in xCOLD GASS/MASCOT for these 12 detections is 0.02 dex ($\thicksim$5%) with a scatter around zero of $\thicksim$0.09 dex, which is similar to the typical error on xCOLD GASS luminosities ($\thicksim$0.07 dex). |
| Pearson correlation coefficient (r) between global Delta_SFR and f_gas,inner | 0.775 | not stated | dimensionless | 4 | Panel B of Figure 6 shows that $\Delta$SFR is more strongly correlated with $f_\text{gas, inner}$ than any of the other gas fraction variables we tested, both in terms of the highest correlation coefficient (r = 0.775) and the lowest intrinsic scatter of the relation ($\sigma = (0.061\pm0.035$) dex). |
| Intrinsic scatter (sigma) between global Delta_SFR and f_gas,inner | 0.061 | 0.035 | dex | 4 | Panel B of Figure 6 shows that $\Delta$SFR is more strongly correlated with $f_\text{gas, inner}$ than any of the other gas fraction variables we tested, both in terms of the highest correlation coefficient (r = 0.775) and the lowest intrinsic scatter of the relation ($\sigma = (0.061\pm0.035$) dex). |
| Pearson correlation coefficient (r) between global Delta_SFR and f_gas,total | 0.737 | not stated | dimensionless | 4 | Panel A of Figure 6 demonstrates that while the correlation between $f_\text{gas, total}$ and $\Delta$SFR is still strong (r = 0.737), it is not as strong as the correlation with $f_\text{gas, inner}$. |
| Intrinsic scatter (sigma) between global Delta_SFR and f_gas,total | 0.120 | 0.039 | dex | 4 | The relationship between the global gas fraction and global $\Delta$SFR also has a larger intrinsic scatter of $\sigma = (0.120 \pm 0.039$) dex. |
| Pearson correlation coefficient (r) between global Delta_SFR and f_gas,outer | 0.640 | not stated | dimensionless | 4 | The weaker correlation and larger scatter between the global gas fraction and global $\Delta$SFR arises from the even weaker correlation and large scatter in the relationship between the outer gas fraction and global $\Delta$SFR (r = 0.640, $\sigma = (0.201 \pm 0.037$) dex); |
| Intrinsic scatter (sigma) between global Delta_SFR and f_gas,outer | 0.201 | 0.037 | dex | 4 | The weaker correlation and larger scatter between the global gas fraction and global $\Delta$SFR arises from the even weaker correlation and large scatter in the relationship between the outer gas fraction and global $\Delta$SFR (r = 0.640, $\sigma = (0.201 \pm 0.037$) dex); |
| Pearson correlation coefficient (r) between global Delta_SFR and f_gas,inner / f_gas,outer | 0.415 | not stated | dimensionless | 4 | Of the four gas fraction variables tested here, $\Delta$SFR exhibits the weakest correlation (r = 0.415) and the largest intrinsic scatter ($\sigma = (0.281 \pm 0.043$) dex) with the inner to outer gas fraction ratio. |
| Intrinsic scatter (sigma) between global Delta_SFR and f_gas,inner / f_gas,outer | 0.281 | 0.043 | dex | 4 | Of the four gas fraction variables tested here, $\Delta$SFR exhibits the weakest correlation (r = 0.415) and the largest intrinsic scatter ($\sigma = (0.281 \pm 0.043$) dex) with the inner to outer gas fraction ratio. |
| Fraction of CO-detected galaxies >= 0.5 dex above SFMS that are post-mergers or interacting pairs | 64 | not stated | per cent | 4 | Indeed, 64 per cent (7/11) of the CO-detected galaxies in SALVAGE 0.5 dex or more above the SFMS appear to be post-mergers or interacting pairs, by visual inspection of their DECaLS images. |

## Qualitative findings

- The global star-forming main sequence (SFMS) is sensitive to where star formation occurs within the galaxy, whereas the global molecular gas main sequence (MGMS) is relatively agnostic to whether molecular gas is concentrated in the inner or outer regions.  
  > "**The global SFMS is sensitive to where the star-formation occurs within the galaxy, but the global MGMS is not sensitive to where the molecular gas is within the galaxy.**" (Summary)
- On the SFMS, median inner and outer gas fractions are equal within error, and a galaxy's position within the scatter of the SFMS is driven by the star formation efficiency in the central few kpc.  
  > "For galaxies on the SFMS (blue shading), we find that the median inner and outer gas fractions are equal within error." (Semi-resolved properties across the main sequence); "**A galaxy’s position within the SFMS is largely dictated by the star-formation efficiency in the central few kpc.**" (Summary)
- Above the SFMS, global starbursts exhibit ~0.8 dex higher inner SFE than outer SFE (which plateaus with Delta_SFR) alongside increasing central gas fraction enhancements.  
  > "Above the SFMS, galaxies have $\thicksim$0.8 dex higher inner SFE relative to their outer SFE, regardless of $\Delta$SFR." (Semi-resolved properties across the main sequence); "Though our results agree that both enhanced central gas and SFE play a role in driving global $\Delta$SFR enhancements above the SFMS, the continued increase of $f_\text{gas, inner}$ and the plateau of SFE$_\text{inner}$ with $\Delta$SFR above the SFMS indicates the strength of the global starburst is controlled by enhanced central gas (see Fig. 5)." (The importance of the central region to quenching in the context of previous works)
- Below the SFMS (in the green valley), galaxies have equally low inner and outer sSFR and SFE, accompanied by a central molecular gas deficit relative to their outer regions.  
  > "Below the SFMS, we find that the $f_\text{gas, inner}$ decreases more than $f_\text{gas, outer}$. This suggests that *global green valley galaxies tend towards central gas deficits* relative to their outer regions." (Semi-resolved properties across the main sequence); "However, below the SFMS, galaxies are equally low in inner and outer sSFR and with equally low SFEs paired with a systematic depletion in inner and outer molecular gas reservoirs, but more depleted in the central region by a factor of $\thicksim2$ at the bottom of the green valley." (Semi-resolved properties across the main sequence)

## Claim tuples

- H: Global star-forming status (Delta_SFR) is governed more strongly by the central molecular gas reservoir than by the global or outer molecular gas reservoir. | E: Compute Pearson correlation coefficients and intrinsic scatter (using ltsfit) between global Delta_SFR and total, inner, outer, and inner-to-outer gas fractions for 175 CO-detected non-edge-on SALVAGE galaxies. | R: Global Delta_SFR correlates more strongly and with lower intrinsic scatter with f_gas,inner (r = 0.775, sigma = 0.061 +/- 0.035 dex) than with f_gas,total (r = 0.737, sigma = 0.120 +/- 0.039 dex) or f_gas,outer (r = 0.640, sigma = 0.201 +/- 0.037 dex). | F: Central molecular gas dictates the global star-forming status of a galaxy more so than the total molecular gas reservoir. | **supported**
- H: A galaxy's position within the scatter of the star-forming main sequence is driven by central star formation efficiency rather than gas fraction differences, while departure from the SFMS into the green valley is driven by central gas depletion. | E: Compare median inner and outer sSFR, f_gas, and SFE across continuous bins of global Delta_SFR from the green valley through the SFMS to the starburst regime, and test robustness against a metallicity and surface-density dependent alpha_CO. | R: On the SFMS, median f_gas,inner and f_gas,outer are equal within error while SFE_inner increases steeply with Delta_SFR; below the SFMS, inner and outer SFE are equally low while f_gas,inner drops below f_gas,outer by a factor of ~2. | F: Position within the SFMS is largely dictated by inner SFE, whereas departure from the SFMS is driven by the availability of central molecular gas. | **supported**
- H: The discrepancy between studies concluding quenching is driven by low central SFE (e.g. iEDGE) versus lack of central gas fuel (SALVAGE) is caused by the physical size of the inner aperture and spatial resolution of the CO data. | E: Compare the SALVAGE 3 arcsec SDSS fibre inner aperture (~1.3 kpc radius) with the iEDGE inner resolution element (~1 R_e, ~6.4 kpc) on a representative green valley galaxy (Delta_SFR = -0.73 dex) CO map. | R: Central gas depletion occurs within the smaller ~1.3 kpc SDSS fibre radius (log f_gas,inner = -1.7 vs log f_gas,outer = -1.1), whereas integrating over the larger ~6.4 kpc iEDGE aperture includes the gas-rich ring/disk, yielding normal f_gas and artificially lower SFE. | F: Whether quenching appears to be caused by low efficiency or lack of fuel in the inner region depends on the resolution of the mm data and the physical definition of the central region. | **supported**

## Reasoning

- Why this data: Combining the ALMA Science Archive with SDSS DR7 central 3 arcsec fibre spectroscopy and broadband photometry provides a statistical sample of 277 semi-resolved galaxies, bridging the gap between large unresolved surveys (e.g. xCOLD GASS) and small kpc-resolved IFU surveys (e.g. ALMaQUEST).  
  > "We call the sample the SDSS-ALMA Legacy Value Archival Gas Exploration (SALVAGE) and it fills a niche in terms of sample size and resolution between that of the large but unresolved xCOLDGASS and the kpc-resolution IFU programs such as ALMaQUEST and EDGE-CALIFA." (Introduction)
- Why this method: The PHANGS-ALMA pipeline was adopted to automate the imaging of hundreds of heterogeneous archival ALMA observations efficiently and reproducibly on the CANFAR Science Platform, while the FWZI method maximizes S/N by summing only contiguous channels containing source flux.  
  > "Motivated by the need to image hundreds of observations efficiently and in a way that is reproducible by others, we automate our imaging using the pipeline developed by the PHANGS-ALMA team (cite: Leroy21)." (Imaging); "To maximize signal-to-noise in the flux measurement, we seek to sum over only the channels that contain flux from the source. We do this using the “full width at zero intensity" method (FWZI) also employed in VERTICO (cite: Brown21)." (Computing molecular gas mass)
- Alternative: Requiring S/N > 5 CO detections in both inner and outer regions simultaneously (rejected because it introduces a selection bias that removes galaxies where CO is entirely centrally concentrated or centrally depleted)  
  > "In principle, detections in both would be preferred, but in practice, such a selection bias removes interesting cases in which all of the CO is centrally concentrated or centrally depleted." (Results)
- Alternative: Metallicity and stellar surface density dependent alpha_CO prescription from Schinnerer & Leroy (2024) / Chiang et al. (2024) (tested as an alternative to constant Milky Way alpha_CO for the inner region; qualitative conclusions unchanged)  
  > "To test whether our qualitative results are significantly affected by our choice of $\alpha_\text{CO}$, we recompute $f_\text{gas, inner}$ and SFE$_\text{inner}$ for every galaxy in SALVAGE using the (cite: Schinnerer24) recommended prescription." (On the assumption of a constant $\alpha_{CO}$)
- Alternative: GSWLC-A1 purely photometric global SFRs and stellar masses (tested in Appendix against MPA/JHU hybrid spectroscopic+photometric SFRs; relative correlation strengths unchanged)  
  > "To address the potential for errors introduced by mixing the inner (spectroscopic) and outer (photometric) components to obtain the total SFR, we compare the total SFRs used in this work with photometric-only total SFRs from the GSWLC (cite: Salim16)." (Comparing MPA-JHU SFRs to GSWLC)
- How they decided it was enough: _not stated_
- Limitation (authors): SALVAGE is an opportunistic, heterogeneous archival sample biased toward high stellar mass, low-redshift galaxies, starbursts, and green valley galaxies, with passive galaxies significantly underrepresented.  
  > "SALVAGE is an opportunistic and heterogeneous ensemble of 277 galaxies built from the individual proposals stored in the ALMA archive." (Description of the SALVAGE Sample); "The left panel of Figure 2 also shows that SALVAGE is biased toward high stellar mass and low-redshift galaxies in SDSS, as these are commonly selected to be more likely to achieve detections." (Description of the SALVAGE Sample); "SALVAGE has a higher propensity for starburst and green valley galaxies, probably because PIs are more likely to propose for extreme populations rather than representative samples." (A semi-resolved perspective on global scaling relations)
- Limitation (authors): The physical radius probed by the fixed 3 arcsec SDSS fibre varies with redshift from ~0.5 kpc to ~6 kpc across the sample.  
  > "The redshift of each target in SALVAGE determines the physical size of the inner region probed by the 3" SDSS fibre, which is shown along the top axis of the left panel. The radii of the central region probed by the SDSS fibre size ranges from $\thicksim$0.5-6 kpc, with a median of 1.3 kpc." (Description of the SALVAGE Sample)
- Limitation (authors): Variable alpha_CO could not be applied to the outer region because SDSS emission-line metallicities are restricted to the central fibre and the outer edge of the galaxy is not well-defined for surface density calculations.  
  > "Second, the “edge” of the outer region is not well-defined for each galaxy and can cause significant uncertainty in $\Sigma_{\star,\text{outer}}$. Lastly, the metallicity measurements from SDSS are based on emission lines that apply to the area within the fibre only." (On the assumption of a constant $\alpha_{CO}$)
- Caveat (inferred, ours): Beam smearing at 1-3 arcsec resolution compared to the 3 arcsec diameter SDSS fibre aperture can mix inner and outer CO flux near the 1.5 arcsec boundary, although no deconvolution of aperture fluxes for the beam size is applied.
- Caveat (inferred, ours): The outer spectrum FWZI integration sums contiguous positive channels around the top 3 flux peaks in a spatially summed annulus spectrum, which may miss faint broad rotation wings or include positive noise spikes in low-S/N outer disks.

## Reproducibility

- Data public (paper): Publicly available from SDSS, DECaLS, and the ALMA Science Archive  
  > "Moreover, we are able to do so using purely archival data from SDSS and ALMA." (SALVAGE Data Collation and Processing)
- Products in archive: Reduced ALMA cubes, moment maps, and higher-order catalogue products are publicly released on CANFAR (DOI: 25.0077)  
  > "The reduced ALMA cubes, moment maps, and higher-order products that were produced by the SALVAGE project are available at <https://www.canfar.net/storage/vault/list/AstroDataCitationDOI/CISTI.CANFAR/25.0077/data>." (Data Availability)
- Code: SALVAGE pipeline implementation and tutorials at https://github.com/sj-wilkinson/SALVAGE and PHANGS-ALMA imaging pipeline at https://github.com/akleroy/phangs_imaging_scripts  
  > "The PHANGS-ALMA imaging pipeline is available at <https://github.com/akleroy/phangs_imaging_scripts>, and the SALVAGE implementation of this pipeline, along with tutorials for interacting with the data, is available at <https://github.com/sj-wilkinson/SALVAGE>." (Data Availability)
- Missing: Calibrated measurement sets for the 46 Cycle 0, 1, and 2 targets that were privately supplied by the ALMA Help Desk rather than generated by archival restoration scripts
- Data volume (inferred): ~5-20 TB of raw/calibrated ALMA measurement sets across 298 targets, plus ~50-200 GB of reduced spectral cubes and optical catalogues
- Score (inferred): 9/5, The paper releases the reduced ALMA cubes, moment maps, and compiled catalogue on CANFAR, and provides the complete processing and analysis code on GitHub alongside detailed parameter descriptions. Only the 46 Cycle 0-2 Help Desk calibrated measurement sets would require an external request to reproduce from raw data.
- Rediscovery candidate: yes, All reduced cubes, catalogues, and pipeline scripts are publicly hosted, the sample selection and FWZI spectral extraction rules are explicitly specified, and the core results are quantitative correlation coefficients and intrinsic scatter values.

## Links

- Method: (cite: Leroy21) (PHANGS-ALMA imaging pipeline used to stage, continuum-subtract, regrid, and image all SALVAGE ALMA CO cubes)
- Method: (cite: Brown21) (VERTICO survey paper defining the FWZI spectral flux integration method used for CO flux measurements)
- Method: (cite: K03; Tremonti04; Brinchmann04) (MPA-JHU SDSS methodology for inner/outer stellar masses and star formation rates)
- Method: (cite: Cappellari2013a) (ltsfit package used to measure linear correlations and intrinsic scatter with measurement uncertainties)
- Companion: Wilkinson et al. in prep. (Next paper in the SALVAGE series investigating central molecular gas depletion in green valley galaxies and its connection to AGN)
- Related: SALVAGE
- Related: SDSS
- Related: DECaLS
- Related: Galaxy Zoo
- Related: PHANGS-ALMA
- Related: ALMaQUEST
- Related: CO-CAVITY
- Related: xCOLD GASS
- Related: MASCOT
- Related: iEDGE
- Related: VERTICO

## Checks

```json
{
 "quotes": 186,
 "quotes_ok": 186,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 25,
 "unsupported_facts": 0,
 "project_codes": 40,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 14,
 "numeric_problems": 0,
 "fill": {
  "facts": 96,
  "stated": 76,
  "rate": 0.792
 },
 "evidence_ok": true
}
```
