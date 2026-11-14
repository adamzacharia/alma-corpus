# JWST + ALMA ubiquitously discover companion systems within ≲18 kpc around four z ≍ 3.5 luminous radio-loud AGN

`2025A&A...696A..88W` | Astronomy and Astrophysics 2025 | first author: Wang, Wuji | arXiv: 2502.20442 | DOI: 10.1051/0004-6361/202553668

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, high_z_galaxies
- Question: Are there companion systems (mergers, gas clouds) within ~18 kpc of four z~3.5 radio galaxies, found jointly from JWST/NIRSpec IFU [O III] kinematics and ALMA Band 8 [C II]?  
  > "we can search for companions, and merger candidates, on tens of kiloparsec scales" (Introduction); "report the ubiquitous discovery of companion systems within $\sim18\,$kpc of the powerful radio AGN using these two independent methods." (Conclusion)
- Target **TN J0121+1320**: coordinates 01:21:42.725, +13:20:58.26 (J2000, radio core)  
  > "(01:21:42.725, +13:20:58.26) | 3.5190" (Table 1); "the systemic redshifts are derived from He ii1640 or" (2.1 HzRGs sample); z/distance z_sys = 3.5190 (+/-0.0004 typical)  
  > "(01:21:42.725, +13:20:58.26) | 3.5190" (Table 1); "the systemic redshifts are derived from He ii1640 or" (2.1 HzRGs sample); distance from systemic redshift from He II 1640 or [C I](1-0) at the radio core (cite: kolwa2023); cosmology H0=70, Om=0.3  
  > "(01:21:42.725, +13:20:58.26) | 3.5190" (Table 1); "the systemic redshifts are derived from He ii1640 or" (2.1 HzRGs sample)
- Target **TN J0205+2242**: coordinates 02:05:10.676, +22:42:50.57 (J2000, radio core)  
  > "(02:05:10.676, +22:42:50.57) | 3.5060" (Table 1); z/distance z_sys = 3.5060 (+/-0.0004 typical)  
  > "(02:05:10.676, +22:42:50.57) | 3.5060" (Table 1); distance from systemic redshift from He II 1640 or [C I] at the radio core (cite: kolwa2023); which line per target is not clear in the text  
  > "(02:05:10.676, +22:42:50.57) | 3.5060" (Table 1)
- Target **4C+03.24**: coordinates 12:45:38.377, +03:23:21.14 (J2000, radio core)  
  > "(12:45:38.377, +03:23:21.14) | 3.5657" (Table 1); z/distance z_sys = 3.5657 (+/-0.0004 typical)  
  > "(12:45:38.377, +03:23:21.14) | 3.5657" (Table 1); distance from systemic redshift from He II 1640 or [C I] at the radio core (cite: kolwa2023); which line per target is not clear in the text  
  > "(12:45:38.377, +03:23:21.14) | 3.5657" (Table 1)
- Target **4C+19.71**: coordinates 21:44:07.512, +19:29:14.58 (J2000, radio core)  
  > "(21:44:07.512, +19:29:14.58) | 3.5892" (Table 1); "based on VLT/SINFONI data (cite: Nesvadba_2017b)" (2.1 HzRGs sample); z/distance z_sys = 3.5892 (+/-0.0004 typical)  
  > "(21:44:07.512, +19:29:14.58) | 3.5892" (Table 1); "based on VLT/SINFONI data (cite: Nesvadba_2017b)" (2.1 HzRGs sample); distance from the text says one target adopts the [O III]5007 redshift from VLT/SINFONI (Nesvadba_2017b); the target is not named in the converted text  
  > "(21:44:07.512, +19:29:14.58) | 3.5892" (Table 1); "based on VLT/SINFONI data (cite: Nesvadba_2017b)" (2.1 HzRGs sample)

## Data provenance

- ALMA projects: 2021.1.00576.S
- bands: Band 8 (~400 GHz)  
  > "Our ALMA Band 8 observations were taken under the program ID 2021.1.00576S (PI: Wuji Wang)." (2.3 ALMA Band 8)
- frequencies and spectral setup: One spw centred on redshifted [C II] (rest 1900.537 GHz); three other spws for dust continuum; spw width 1.875 GHz ~ 1350 km/s; [C II] line often spans two consecutive spws  
  > "We set up one spectral window in Band 8 to be centered at the redshifted frequency of \[C ii\] ($\nu_{\rm rest}=1900.537\,$GHz)." (2.3 ALMA Band 8); "Then, the other three spectral windows were used to observe dust emission." (2.3 ALMA Band 8); "relative to the width of spectral window (1.875$\,$GHz $\sim$ 1350$\,\rm km\,s^{-1}$)" (2.3 ALMA Band 8)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-5  
  > "These observations were carried out in C43-5 configuration between UT 2022 June 17 and 2022 August 10." (2.3 ALMA Band 8)
- baselines: _not stated_
- angular resolution: Synthesized beams of the cleaned cubes: 0.19x0.15 arcsec (J0121), 0.14x0.12 (J0205), 0.23x0.18 (4C03, 4C19)  
  > "Size and position angle of the synthesized beam of the cleaned ALMA cube combined with two consecutive spectral windows." (Table 1); "With $\theta_{\rm 400GHz}=0.23\ensuremath{''} \times 0.18\ensuremath{''}$ and S/N$=13.3$" (4.4 Companion search of 4C+19.71)
- max recoverable scale: _not stated_
- sensitivity: [C II] cube rms 3.0, 1.3, 1.1, 1.0 mJy/beam per channel (14 km/s); continuum rms 76 and 92 uJy/beam for the two detections; 3 sigma upper limits 0.28 and 0.25 mJy/beam for the other two  
  > "The rms noise of the \[C ii\] cubes at the systemic redshift are $3.0\,\rm mJy\,beam^{-1}$, $1.3\,\rm mJy\,beam^{-1}$, $1.1\,\rm mJy\,beam^{-1}$, and $1.0\,\rm mJy\,beam^{-1}$ per channel" (2.3 ALMA Band 8); "we report $3\sigma$ upper limits of $0.28\,\rm mJy\,beam^{-1}$ and $0.25\,\rm mJy\,beam^{-1}$" (2.3 ALMA Band 8)
- time on source: Two targets fully observed; for the other two only half of the proposed integration times were executed (absolute times not stated)  
  > "For the remaining two, only half of the proposed integration times were executed." (2.3 ALMA Band 8)
- observing dates: UT 2022 June 17 to 2022 August 10  
  > "These observations were carried out in C43-5 configuration between UT 2022 June 17 and 2022 August 10." (2.3 ALMA Band 8)
- pi or archival as stated: Own PI program (PI: Wuji Wang)  
  > "program ID 2021.1.00576S (PI: Wuji Wang)" (2.3 ALMA Band 8)
- Line: [C II] 158 um fine-structure line (2P3/2-2P1/2) (1900.537 GHz)
- Other facility **JWST NIRSpec IFU (GO-1970, G235H/F170LP)**: Rest-frame optical IFU cubes ([O III]5007, H-beta, H-alpha, etc.) used for warm ionized gas kinematics and companion detection  
  > "Cycle 1 General Observer (GO) program JWST-GO-1970 (PI: Wuji Wang)" (2.2 JWST/NIRSpec IFU); "We downloaded all raw data from the Mikulski Archive for Space Telescopes (MAST)." (2.2 JWST/NIRSpec IFU)
- Other facility **VLA**: Radio maps used only to locate the radio core/jet for WCS alignment (new Ku-band for 4C+03.24, archival C-band and X-band for others)  
  > "In this work, we only used the radio observations to trace the position of the jets." (2.5 Radio maps); "with the VLA in A configuration in the Ku-band covering a frequency range of 12 to 18 GHz (Project 24B-147, PI: Carlos De Breuck)" (2.5 Radio maps)
- Other facility **VLT/MUSE**: Existing MUSE cubes used for foreground-galaxy checks and WCS alignment of TN J0121+1320  
  > "In particular, they have observations from MUSE and ALMA Band 3 focusing on the ionized CGM gas (in rest frame UV) and molecular gas" (2.1 HzRGs sample)
- Other facility **VLT/SINFONI**: Earlier [O III] kinematics used for comparison with the JWST data (published)  
  > "analyzed the ionized gas kinematics of a large sample HzRGs, including our targets." (3.1 Warm ionized gas kinematics)
- External data: Stellar mass and SFR of each HzRG (SED fitting)  
  > "and SFR from (cite: DeBreuck_2010) and (cite: Falkendal_2019) based on SED fitting." (Table 1) [from (cite: DeBreuck_2010); (cite: Falkendal_2019)]
- External data: Systemic redshifts from He II 1640 or [C I](1-0) at the radio core  
  > "emission at the radio core (cite: kolwa2023)" (2.1 HzRGs sample) [from (cite: kolwa2023)]
- External data: [O III]5007 systemic redshift from VLT/SINFONI for one target  
  > "based on VLT/SINFONI data (cite: Nesvadba_2017b)" (2.1 HzRGs sample) [from (cite: Nesvadba_2017b)]
- External data: 8.4 GHz VLA X-band radio maps of one target  
  > "radio maps of published in (cite: Nesvadba_2007a)" (2.5 Radio maps) [from (cite: Nesvadba_2007a)]
- External data: JWST NIRSpec IFU PSF FWHM (~0.11 arcsec)  
  > "PSF used in this work is given as the one constructed in (cite: Vayner_2023Q3D_2)" (2.2 JWST/NIRSpec IFU) [from (cite: Vayner_2023Q3D_2)]
- External data: Virial coefficient k = 1.8 for rotating-disk dynamical mass  
  > "We take $k=1.8$ (cite: deGraaff_2024)." (5.1 Companion kinematics and masses) [from (cite: deGraaff_2024)]
- Simulation/model as data: Bagpipes single starburst model spectrum (solar metallicity, A_V = 1.5 mag, Calzetti law) overlaid on J0121-[C II]-B optical continuum  
  > "We used a single starburst model with solar metallicity." (4.1.2 Results of companion search); "Instead, we overlay a model spectrum generated using Bagpipe (cite: Carnall_2018_Bagpipe)." (4.1.2 Results of companion search)

## Processing

### Calibration

- pipeline or manual: Default ALMA bandpass and phase calibrations adopted (pipeline vs manual not specified)  
  > "The default ALMA bandpass and phase calibrations were adopted." (2.3 ALMA Band 8)
- casa version: CASA v6.6.0  
  > "Common Astronomy Software Applications for Radio Astronomy v6.6.0" (2.3 ALMA Band 8)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean, cleaned down to a 2 sigma level  
  > "The task `tclean` was used to clean the cube down to a $2\sigma$ level." (2.3 ALMA Band 8)
- deconvolver: _not stated_
- weighting robust: Briggs robust = +0.5 (TN J0121+1320, 4C+19.71); robust = +2.0 (TN J0205+2242, 4C+03.24)  
  > "Robust = +0.5 Briggs weighting was applied for TN J0121+1320 and 4C+19.71 and robust = +2.0 Briggs weighting was applied for TN J0205+2242 and 4C+03.24." (Table 1); "This provides higher signal to noise ratio (S/N) with a trade off in spatial resolution." (2.3 ALMA Band 8)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: None in the uv-plane; the two consecutive [C II] spws were cleaned together without continuum subtraction  
  > "together without continuum subtraction in the $uv-$plane." (2.3 ALMA Band 8)
- line free channels: _not stated_
- primary beam correction: Cubes and continuum maps used after primary beam correction  
  > "we used the cubes and continuum maps (for the two with detections) after the primary beam correction." (2.3 ALMA Band 8)
- array combination: _not stated_
- smoothing: Final cubes smoothed to 14 km/s per channel  
  > "The final cubes were smoothed to $14,\rm km,s^{-1}$ per channel." (2.3 ALMA Band 8)
- final beam: Synthesized beam of the cleaned cube (two spws combined): 0.19x0.15, 0.14x0.12, 0.23x0.18, 0.23x0.18 arcsec for J0121, J0205, 4C03, 4C19  
  > "Size and position angle of the synthesized beam of the cleaned ALMA cube combined with two consecutive spectral windows." (Table 1)
- final rms: [C II] cubes 3.0, 1.3, 1.1, 1.0 mJy/beam per channel; continuum 76 and 92 uJy/beam (two detections)  
  > "The rms noise of the \[C ii\] cubes at the systemic redshift are $3.0\,\rm mJy\,beam^{-1}$, $1.3\,\rm mJy\,beam^{-1}$, $1.1\,\rm mJy\,beam^{-1}$, and $1.0\,\rm mJy\,beam^{-1}$ per channel" (2.3 ALMA Band 8); "The rms noise for the continuum maps constructed from the individual spectral windows are $76\,\rm \mu Jy\,beam^{-1}$ and $92\,\rm \mu Jy\,beam^{-1}$" (2.3 ALMA Band 8)

### Inherited from earlier work

- JWST NIRSpec IFU reduction procedure  
  > "Our procedure is similar to (cite: Vayner_2023Q3D) and (cite: Wang_2024)." (2.2 JWST/NIRSpec IFU) [from (cite: Vayner_2023Q3D); (cite: Wang_2024)]
- No separate flux-calibration step for the JWST cubes  
  > "We did not include flux calibration step as in (cite: Wang_2024)" (2.2 JWST/NIRSpec IFU) [from (cite: Wang_2024)]
- q3dfit line fitting with kinematically tied Gaussian components for all lines  
  > "while keeping the Gaussian components for different lines kinematically tied (cite: Vayner_2023Q3D; Wang_2024)" (3.1 Warm ionized gas kinematics) [from (cite: Vayner_2023Q3D; Wang_2024)]
- Alignment of NIRSpec WCS to the 8.4 GHz radio core position  
  > "Similarly, we fit a 2D Gaussian profile to the radio core observed at $8.4\,$GHz (cite: vanOjik_1996; Nesvadba_2007a; Nesvadba_2017b)." (2.4 Astrometric alignment of NIRSpec IFU cubes) [from (cite: vanOjik_1996; Nesvadba_2007a; Nesvadba_2017b)]
- VLA X-band flux scale  
  > "The ﬂux scale was set according to (cite: Perley_2017)." (2.5 Radio maps) [from (cite: Perley_2017)]
- Dispersion-dominated dynamical mass formula  
  > "we estimate $M_{\rm dyn}$ following (cite: ubler_2023)" (5.1 Companion kinematics and masses) [from (cite: ubler_2023)]
- Rotation velocity proxy for [O III] companions, with sin i left unconstrained  
  > "leaving ${\rm sin}\,i$ unconstrained (cite: Nesvadba_2011)" (5.1 Companion kinematics and masses) [from (cite: Nesvadba_2011)]
- AGN/star-formation line-ratio classification  
  > "Simply assuming the (cite: Kewley_2006) empirical classification" (5.2 Nature of [O III] companions) [from (cite: Kewley_2006)]

### Not stated but needed to reproduce (our reading)

- Line-free channels or velocity ranges used to build moment-0 maps and continuum
- tclean cell size, image size, masking strategy, deconvolver, niter and threshold details
- Whether the ALMA calibration used the pipeline or manual scripts, and the pipeline version
- Flux calibrator and flux-scale uncertainty for the Band 8 data
- Whether 7m or total-power data were used (the paper uses only the C43-5 configuration)
- q3dfit configuration: maximum number of Gaussian components, initial guesses, bounds, and the continuum model
- Spaxel-fit settings for the [O III] velocity maps (S/N cuts, binning)
- Exact [C II] aperture centres and the rule for choosing detection positions
- 3DBarolo ring number, radial sampling, and masking and fitting options beyond those given
- Effective radii and axis ratios per companion used in the dispersion mass
- Per-target assignment of the systemic redshift source (He II, [C I], or [O III])

## Analysis recipe

1. **Reduce JWST NIRSpec IFU data to cubes**: Run standard stage 1 and 2 of the jwst pipeline, subtract 1/f noise from rate files, combine dithers with sigma clipping instead of stage 3 outlier rejection  
  > "Specifically, we executed the standard first and second stages of the pipeline." (2.2 JWST/NIRSpec IFU); "We subtracted the $1/f$ noise from the rate files resulted from stage 1." (2.2 JWST/NIRSpec IFU); "Therefore, we used sigma clipping to combine the dithered exposures into the final data cube." (2.2 JWST/NIRSpec IFU)
   - software: jwst Science Calibration pipeline, CRDS
   - parameter: jwst pipeline v1.13.4, CRDS context jwst_1202.pmap  
  > "We used v1.13.4 of the" (2.2 JWST/NIRSpec IFU); "with the Calibration Reference Data System (CRDS) context file jwst_1202.pmap" (2.2 JWST/NIRSpec IFU)
   - assumption: Standard pipeline flux calibration is good enough (relative flux difference <5%)  
  > "since the standard pipeline already has a good performance (i.e., relative flux difference $<5\%$" (2.2 JWST/NIRSpec IFU)
   - fitting: _not stated_
   - validation: _not stated_
2. **Subtract uniform background from the JWST cubes**: Extract median background spectrum with sources masked, fit a polynomial, subtract from the whole cube  
  > "Then, we fitted a fifth or sixth order polynomial to the median background spectrum." (2.2 JWST/NIRSpec IFU); "Finally, we subtracted this fitted contribution from the whole data cube." (2.2 JWST/NIRSpec IFU)
   - parameter: Fifth or sixth order polynomial  
  > "Then, we fitted a fifth or sixth order polynomial to the median background spectrum." (2.2 JWST/NIRSpec IFU)
   - fitting: _not stated_
   - validation: _not stated_
3. **Image the ALMA Band 8 cubes and continuum**: CASA tclean cubes with two [C II] spws cleaned together, no uv continuum subtraction, primary-beam correction, smoothing to 14 km/s; continuum maps from individual spws  
  > "The task `tclean` was used to clean the cube down to a $2\sigma$ level." (2.3 ALMA Band 8); "together without continuum subtraction in the $uv-$plane." (2.3 ALMA Band 8); "The shapes of the spectra at the transition frequencies of the two windows were compared to the cubes cleaned individually." (2.3 ALMA Band 8)
   - software: CASA, tclean
   - parameter: robust = +0.5 for J0121 and 4C19; robust = +2.0 for J0205 and 4C03  
  > "Robust = +0.5 Briggs weighting was applied for TN J0121+1320 and 4C+19.71 and robust = +2.0 Briggs weighting was applied for TN J0205+2242 and 4C+03.24." (Table 1)
   - parameter: 14 km/s channels  
  > "The final cubes were smoothed to $14,\rm km,s^{-1}$ per channel." (2.3 ALMA Band 8)
   - fitting: _not stated_
   - validation: No jump in flux between the two spectral windows when compared with individually cleaned cubes  
  > "We did not find any jump in flux." (2.3 ALMA Band 8)
4. **Align NIRSpec IFU astrometry to radio core**: Fit 2D Gaussian to the NIRSpec continuum at 2.6 um (line-free) and to the 8.4 GHz radio core, then shift the NIRSpec WCS; for J0121 use a foreground galaxy ([O II] in MUSE, [S III] in NIRSpec)  
  > "we fitted a 2D Gaussian profile to the continuum of the radio galaxy at observed wavelength $2.6\,\rm \mu m$" (2.4 Astrometric alignment of NIRSpec IFU cubes); "We then shifted the WCS of the NIRSpec IFU to match the radio data." (2.4 Astrometric alignment of NIRSpec IFU cubes)
   - assumption: NIRSpec continuum sits at the position of the radio AGN (radio core)  
  > "The assumption behind this alignment is that the continuum detected by the NIRSpec IFU is at the position of the radio AGN" (2.4 Astrometric alignment of NIRSpec IFU cubes)
   - fitting: _not stated_
   - validation: Continuum centroids lie within 0.1 arcsec of the line brightness peak  
  > "which supports our assumption" (2.4 Astrometric alignment of NIRSpec IFU cubes)
5. **Identify and fit [O III] companions**: Visually inspect [O III]5007 channel maps for kinematically distinct blobs, then fit r=0.1 arcsec aperture spectra with q3dfit (all bright lines fitted together with tied Gaussian components) and map velocities spaxel-by-spaxel in [O III] only  
  > "Specifically, we visually inspect the" (3.1 Warm ionized gas kinematics); "The fitting is done simultaneously for all bright emission lines covered" (3.1 Warm ionized gas kinematics); "Using `q3dfit`, we fit spaxel-based spectra around the companion positions." (3.1 Warm ionized gas kinematics)
   - software: q3dfit
   - parameter: Aperture radius 0.1 arcsec  
  > "by fitting $r=0.1\ensuremath{''}$ aperture-extracted spectra" (3.1 Warm ionized gas kinematics)
   - parameter: Number of components chosen by q3dfit up to a user-set maximum  
  > "The optimized number of components are determined by `q3dfit`, with a maximum allowed number as input." (3.1 Warm ionized gas kinematics)
   - assumption: Doublet ratios fixed by atomic physics ([O III] and [N II] = 3; [S II] ratio limited to 0.4375-1.4484; [O II] doublet ratio = 1)  
  > "The flux ratios of doublets are set according to atomic physics" (3.1 Warm ionized gas kinematics)
   - fitting: q3dfit multi-Gaussian fit with kinematically tied lines; sampler, priors and likelihood not stated  
  > "while keeping the Gaussian components for different lines kinematically tied (cite: Vayner_2023Q3D; Wang_2024)" (3.1 Warm ionized gas kinematics)
   - validation: Companion spectra compared with the same fit at the central AGN position  
  > "For comparison, we also fit the spectra at central AGN positions through the same procedure" (3.1 Warm ionized gas kinematics)
6. **Detect and fit [C II] emitters in ALMA cubes**: Make moment 0 maps from channels with emission, extract 1D spectra in apertures (1x major beam for J0121 and 4C19; 2x for J0205 and 4C03), fit one Gaussian per spectrum  
  > "moment 0 maps constructed from velocity channels where emission is detected" (3.2 [C II] emitters); "For the field of TN J0121+1320 and 4C+19.71, we use apertures with the size of the major synthesized beam." (3.2 [C II] emitters); "We perform line fitting to the 1D spectra with one Gaussian component" (3.2 [C II] emitters)
   - software: CASA
   - parameter: Detection at >~3 sigma; apertures 1x or 2x the major beam  
  > "we increase the aperture to twice the size of major synthesized beam to increase the S/N" (3.2 [C II] emitters)
   - assumption: Lines detected in Band 8 are [C II] at redshifts similar to the central HzRGs  
  > "we assume the lines detected by ALMA Band 8 are" (3.2 [C II] emitters)
   - fitting: Single Gaussian per 1D spectrum; fitting code not stated  
  > "We perform line fitting to the 1D spectra with one Gaussian component" (3.2 [C II] emitters)
   - validation: Comparison with [O III] counterpart at the same position and with dust continuum  
  > "To compare the warm and cold ionized gas at the position of" (3.2 [C II] emitters)
7. **Fit disk kinematics of the two bright [C II] companions**: 3DBarolo tilted-ring fits to J0121-[C II]-B and 4C19-[C II] on cubes smoothed to 28 km/s, with NORM=AZIM and fixed centres; 4C19 fitted in two steps (all free parameters, then geometry fixed)  
  > "we also conduct spatial fitting using $^{\rm 3D}$BAROLO" (3.2 [C II] emitters); "We set `NORM=AZIM` so that the observed moment-0 map is azimuthally averaged to obtain" (3D BAROLO fit of [C II]); "First, all free parameters are fitted." (3D BAROLO fit of [C II])
   - software: 3DBarolo
   - parameter: J0121-B: initial PA = 193 deg, i = 60 deg, varied by +/-15 deg; best fit PA = 187 deg, i = 61 deg  
  > "The initial values of $PA$ and $i$ are set to 193$^{\circ}$ and 60$^{\circ}$." (3D BAROLO fit of [C II]); "$PA$ and $i$ are 187$^{\circ}$ and 61$^{\circ}$, respectively" (3D BAROLO fit of [C II])
   - parameter: 4C19: initial PA = 100 deg, i = 10 deg, varied by +/-15 and +/-30 deg; best fit PA = 93 deg, i = 30 deg  
  > "The initial values of $PA$ and $i$ are 100$^{\circ}$ and 10$^{\circ}$." (3D BAROLO fit of [C II]); "$PA$ and $i$ are 93$^{\circ}$ and 30$^{\circ}$, respectively" (3D BAROLO fit of [C II])
   - parameter: Ring separation half the beam major axis; centre fixed to initial guess  
  > "The separation between rings is set to half the width of beam major axis by default." (3D BAROLO fit of [C II]); "The center coordinates ($x_{0}$, $y_{0}$) are fixed to the initial guess." (3D BAROLO fit of [C II])
   - fitting: Free parameters v_sys, PA, i, v_rot, sigma_v minimised by 3DBarolo (cost function not stated)  
  > "Initial value of other parameters are guessed by $^{\rm 3D}$BAROLO." (3D BAROLO fit of [C II])
   - validation: Residual moment 2 and position-velocity diagrams inspected; inclination of 4C19 flagged as resolution-limited  
  > "We note that the $i$ fit of 4C19-\[C ii\] is limited by angular resolution and should be treated with caution." (3D BAROLO fit of [C II])
8. **Estimate dynamical masses of companions**: Dispersion-dominated M_dyn = K(n)K(q) sigma_v^2 r_e / G; rotation M_dyn = k r v_rot^2 / G, with csc^2 i left free for [O III] companions  
  > "Under this assumption, we estimate $M_{\rm dyn}$ following (cite: ubler_2023)" (5.1 Companion kinematics and masses); "For J0121-\[C ii\]-B and 4C19-\[C ii\], we obtain $r$ and $v_{\rm rot}$ from $^{\rm 3D}$BAROLO" (5.1 Companion kinematics and masses)
   - software: 3DBarolo
   - parameter: n = 1, q = 1, k = 1.8; r_e set to PSF or major beam (2 theta for J0205-[C II] and 4C03-[C II]); R = 0.11 arcsec PSF for unresolved [O III] blobs  
  > "For simplicity, we take $q=1$." (5.1 Companion kinematics and masses); "We take $k=1.8$ (cite: deGraaff_2024)." (5.1 Companion kinematics and masses); "we use the PSF or major synthesized beam size" (5.1 Companion kinematics and masses)
   - assumption: Gravitational interaction with the central AGN ignored; masses from unresolved sizes are upper limits (dispersion) or lower limits (rotation R)  
  > "we ignore gravitational interactions between the companion and the central AGN" (5.1 Companion kinematics and masses); "We stress that this mass estimate should be treated as an upper limit, as the size is overestimated." (5.1 Companion kinematics and masses)
   - fitting: _not stated_
   - validation: _not stated_
9. **Check ionisation mechanism of [O III] companions**: Build [O III]/H-beta vs [N II]/H-alpha and [S II]/H-alpha diagrams from the 1D fits and classify against Kewley et al. empirical lines  
  > "We use both the \[O iii\]/H$\beta$-\[N ii\]/H$\alpha$ and \[O iii\]/H$\beta$-\[S ii\]/H$\alpha$ diagnostics." (5.2 Nature of [O III] companions)
   - software: q3dfit
   - parameter: Extinction correction with Halpha/Hbeta = 3.1  
  > "by adopting the canonical value of $F_{\rm H\alpha}/F_{\rm H\beta}=3.1$" (5.2 Nature of [O III] companions)
   - assumption: Case B recombination  
  > "assuming Case B recombination (cite: Veilleux_1987; Osterbrock_2006)" (5.2 Nature of [O III] companions)
   - fitting: _not stated_
   - validation: _not stated_
10. **Zeroth-order stellar mass of J0121-[C II]-B**: Overlay a Bagpipes single starburst spectrum on the aperture-extracted optical continuum and read off the consistent stellar mass; derive a 3 sigma limit from the 8 sigma continuum detection  
  > "We find that this continuum level could be consistent with a galaxy with $M_{\star}=10^{9.9}\,M_{\odot}$." (4.1.2 Results of companion search); "we find that the continuum of J0121-\[C ii\]-B is detected at $\sim8\sigma$" (5.1 Companion kinematics and masses)
   - software: Bagpipes
   - parameter: Solar metallicity, A_V = 1.5 mag from Balmer decrement, Calzetti law  
  > "The extinction is set to $A_{V}=1.5\,$mag based on Balmer decrement and (cite: Calzetti_2000) law." (4.1.2 Results of companion search)
   - assumption: Optical continuum flux proportional to stellar mass when deriving the detection limit  
  > "if optical continuum flux is directly proportional to stellar mass" (5.1 Companion kinematics and masses)
   - fitting: Not a fit: model spectrum overlaid and compared by eye  
  > "This model spectrum should simply be considered as a zeroth order indication of the stellar mass." (4.1.2 Results of companion search)
   - validation: _not stated_
11. **Derive encounter time and merger fraction**: Encounter time = d_RG / Delta v for typical Delta v of 100-500 km/s, assuming no projection; major merger fraction from the four-source sample  
  > "the zeroth order estimate of encounter time is around 10 to 100$\,$Myr" (5.3 Impact on galaxy evolution)
   - assumption: No projection effects; companions in post-encounter phase  
  > "Assuming the companions are in the post-encounter phase, i.e., after the first pericenter passage" (5.3 Impact on galaxy evolution)
   - fitting: _not stated_
   - validation: Compared with observed time after jet launch from the literature  
  > "this time scale is consistent with the observed time after jet launch" (5.3 Impact on galaxy evolution)

## Software

- **CASA** v6.6.0: Calibration products processing and imaging of ALMA Band 8 data; VLA reductions  
  > "Common Astronomy Software Applications for Radio Astronomy v6.6.0" (2.3 ALMA Band 8)
- **tclean** : Cleaning ALMA cubes and VLA images  
  > "The task `tclean` was used to clean the cube down to a $2\sigma$ level." (2.3 ALMA Band 8)
- **gaincal** : Self-calibration of the VLA C-band data  
  > "Imaging and self-calibration were then performed using the tasks `tclean` and `gaincal` respectively." (2.5 Radio maps)
- **AIPS (Astronomical Image Processing System)** : Flagging and cross-calibration of the archival VLA X-band data  
  > "cross-calibrated using Astronomical Image Processing System (cite: Greisen_2003)" (2.5 Radio maps)
- **JWST Science Calibration pipeline (jwst)** v1.13.4: Reducing NIRSpec IFU data (stages 1 and 2) with CRDS jwst_1202.pmap  
  > "We used v1.13.4 of the" (2.2 JWST/NIRSpec IFU); "Specifically, we executed the standard first and second stages of the pipeline." (2.2 JWST/NIRSpec IFU)
- **q3dfit** : Multi-line spectral decomposition of 1D and spaxel NIRSpec spectra  
  > "The fitting is done simultaneously for all bright emission lines covered" (3.1 Warm ionized gas kinematics)
- **3DBarolo** : Tilted-ring fits to [C II] cubes of the two bright companions  
  > "we also conduct spatial fitting using $^{\rm 3D}$BAROLO" (3.2 [C II] emitters)
- **Bagpipes** : Model stellar continuum overlaid on J0121-[C II]-B optical spectrum  
  > "we overlay a model spectrum generated using Bagpipe (cite: Carnall_2018_Bagpipe)" (4.1.2 Results of companion search)
- **LMFIT** : _not stated_
- **Astropy** : _not stated_
- **SciPy** : _not stated_
- **NumPy** : _not stated_

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| J0121-[O III] velocity offset and width | Delta v = 434 km/s; sigma_v = 95 | +/-2 (Delta v from Table); +/-3 (sigma_v) | km/s | 5 | is $434\,\rm km\,s^{-1}$ redshifted from the systemic velocity and has a width $\sigma_{v}=95\pm3\,\rm km\,s^{-1}$ |
| J0205-[O III] velocity offset | -1426 | +/-8 | km/s | 5 | has $\Delta v=-1426\,\rm km\,s^{-1}$ with respect to the systemic redshift of |
| J0205-[O III] velocity dispersion | 309 | +/-7 | km/s | 5 | The fitted line width is relatively broad with $\sigma_{v}=309\,\rm km\,s^{-1}$ |
| 4C03-[O III] velocity offset | 1395 | +/-47 | km/s | 5 | precisely, $\Delta v=1395\pm47\,\rm km\,s^{-1}$ using fitting results from Table |
| 4C03-[O III] narrow and broad component dispersions | 55 (narrow); 574 (broad) | +/-16; +/-5 | km/s | 5 | $\sigma_{v}=55\pm16\,\rm km\,s^{-1}$ and $574\pm5\,\rm km\,s^{-1}$, respectively |
| 4C19-[O III] velocity offset and dispersion | Delta v = -584; sigma_v = 210 | Table: +/-9 and +/-9 | km/s | 5 | with $\Delta v=-584\,\rm km\,s^{-1}$ and $\sigma_{v}=210\,\rm km\,s^{-1}$ |
| J0121-[C II]-B redshift, offset, dispersion and flux | z = 3.5197; Delta v = 49 km/s; sigma_v = 345 km/s; flux 2.49 Jy km/s | z +/-0.0003; Delta v +/-19; sigma_v +/-19; flux +/-0.12 | km/s; Jy km/s | 6 | 3.5197$\pm$0.0003 / 49$\pm$19 / 345$\pm$19 / 2.49$\pm$0.12 |
| 4C19-[C II] redshift, offset, dispersion and flux | z = 3.5881; Delta v = -71 km/s; sigma_v = 256 km/s; flux 1.62 Jy km/s | z +/-0.0002; Delta v +/-12; sigma_v +/-12; flux +/-0.06 | km/s; Jy km/s | 6 | 3.5881$\pm$0.0002 / -71$\pm$12 / 256$\pm$12 / 1.62$\pm$0.06 |
| 4C19-[C II] positional accuracy and chance coincidence with the AGN | ~0.019 arcsec; ~5% probability the dust is at the AGN position | not stated | arcsec; percent | 6 | there is only a $5\%$ probability that the dust is at the same position as the AGN |
| J0121-[C II]-B 3DBarolo best-fit PA and inclination | PA = 187 deg; i = 61 deg | not stated | degrees | 7 | $PA$ and $i$ are 187$^{\circ}$ and 61$^{\circ}$, respectively |
| 4C19-[C II] 3DBarolo best-fit PA and inclination | PA = 93 deg; i = 30 deg | not stated | degrees | 7 | $PA$ and $i$ are 93$^{\circ}$ and 30$^{\circ}$, respectively |
| J0121-[C II]-B dynamical mass (dispersion; rotation) | 48; 9.0 (x10^10 Msun); d_RG = 6.4 kpc | not stated | 1e10 Msun | 8 | (01:21:42.667, +13:20:58.52) / 0.88/6.4 / 48 / 9.0 |
| 4C19-[C II] dynamical mass (dispersion; rotation) | 32; 7.0 (x10^10 Msun); d_RG = 0.3 kpc | not stated | 1e10 Msun | 8 | (21:44:07.515, +19:29:14.59) / 0.04/0.3 / 32 / 7.0 |
| Range of companion dispersion-based dynamical masses | approximately 1e10 to 1e11 Msun (upper limits) | not stated | Msun | 8 | are approximately $10^{10-11}\,M_{\odot}$ |
| J0121-[C II]-B stellar mass (zeroth order) | 10^9.9 | not stated (zeroth order) | Msun | 10 | consistent with a galaxy with $M_{\star}=10^{9.9}\,M_{\odot}$ |
| 3 sigma stellar mass detection limit in the NIRSpec cubes | ~10^9.5 | not stated | Msun | 10 | the $3\sigma$ $M_{\star}$ detection limit in the cube is $\sim10^{9.5}\,M_{\odot}$ |
| Median projected companion distance | ~7 kpc | not stated | kpc | 11 | the companions have a median $d_{\rm RG}\simeq7\,$kpc |
| Encounter time d_RG / Delta v | 10 to 100 | zeroth order | Myr | 11 | the zeroth order estimate of encounter time is around 10 to 100$\,$Myr |
| Companion detection rate and major merger fraction | 100%; f_MM ~ 25% | not stated (four sources) | dimensionless | 11 | The detection rate of companions in our randomly selected sample is $100\%$.; the major merger fraction in our four-source sample is $f_{\rm MM}\sim25\%$ |
| ALMA [C II] cube rms per channel | 3.0, 1.3, 1.1, 1.0 (J0121, J0205, 4C03, 4C19 in text order) | not stated | mJy/beam | 3 | The rms noise of the \[C ii\] cubes at the systemic redshift are $3.0\,\rm mJy\,beam^{-1}$, $1.3\,\rm mJy\,beam^{-1}$, $1.1\,\rm mJy\,beam^{-1}$, and $1.0\,\rm mJy\,beam^{-1}$ per channel |
| ALMA Band 8 continuum 3 sigma upper limits (two non-detections) | 0.28 and 0.25 | not stated | mJy/beam | 3 | we report $3\sigma$ upper limits of $0.28\,\rm mJy\,beam^{-1}$ and $0.25\,\rm mJy\,beam^{-1}$ |

## Qualitative findings

- J0121-[C II]-C and J0121-[O III] may trace the same companion system  
  > "Therefore, J0121-\[C ii\]-C and J0121-\[O iii\] may trace the same companion system." (4.1.2 Results of companion search)
- 4C19-[C II] velocity is closer to the molecular gas ([C I]) than to the warm ionized gas, suggesting two different systems  
  > "suggests that the cold and warm gas are associated with two different systems" (4.4 Companion search of 4C+19.71)
- No clear evidence that the four HzRGs live in dense environments at large scales  
  > "there is no clear evidence that the four HzRGs studied here live in dense environments" (5.1 Companion kinematics and masses)

## Claim tuples

- H: Do the four z~3.5 HzRGs have nearby companions on <~18 kpc scales? | E: Joint search with JWST NIRSpec IFU [O III] kinematics and ALMA Band 8 [C II] emission in each field | R: At least one [O III] or [C II] companion per field; seven [C II] and four [O III] components listed | F: Companion systems are ubiquitous around these radio AGN (detection rate 100% of four) | **supported**
- H: How massive are the companions? | E: Dispersion-based and rotation-based dynamical mass estimates from [O III] and [C II] kinematics | R: Dispersion masses ~1e10-1e11 Msun (upper limits); rotation masses ~1e9-1e10 Msun | F: Dynamical masses of 1e9-1e11 Msun suggest possible minor mergers, with large uncertainties | **partially**
- H: Are the [O III] companions photoionised by the AGN, or part of outflows? | E: Line-ratio diagnostics from the 1D q3dfit fits against Kewley et al. classifications | R: All but one [O III] companion fall in the AGN-photoionised region | F: Companions are likely AGN-photoionised gas, but outflow origin cannot be ruled out | **partially**
- H: Do the bright [C II] companions show regular rotation? | E: 3DBarolo tilted-ring fits of J0121-[C II]-B and 4C19-[C II] | R: Velocity gradients consistent with disk rotation with residuals in moment 2 and PV diagrams | F: Disk rotation detected with residuals suggesting more chaotic underlying motions | **supported**
- H: Do companions trigger or alter radio jets? | E: Comparison of companion positions, encounter time scale and radio morphology | R: Encounter time 10-100 Myr consistent with time since jet launch; companions on the side of compact jets or deflected jets | F: Supports the merger trigger scenario for jets (based on zeroth order arguments) | **partially**

## Reasoning

- Why this data: Targets chosen for multi-wavelength 3D coverage and a range of host and radio properties; [C II] is a better tracer of cold gas dynamics than AGN-affected optical lines  
  > "Besides the prerequisite selection for multi-wavelength coverage in three dimensions, these four HzRGs also have a wide range of host properties and radio morphologies." (2.1 HzRGs sample); "is a more reliable tracer of cold gas dynamics than the warm ionized optical lines which are affected by strong AGN" (Introduction)
- Why this method: Higher robust (+2.0) used for the shallow fields to gain S/N at the cost of resolution; 14 km/s channels balance S/N, continuum coverage and channel number for dynamics  
  > "This provides higher signal to noise ratio (S/N) with a trade off in spatial resolution." (2.3 ALMA Band 8); "The choice of resolution element is a balance among S/N, continuum coverage and a sufficient number of channels for dynamical study" (2.3 ALMA Band 8)
- Alternative: Wide [O III] components of 4C03-[O III] and J0205-[O III] could be due to jet-gas interaction or AGN impact instead of a companion  
  > "Alternatively, this may suggest a strong jet gas interaction." (4.3 Companions of 4C+03.24); "Another possibility is that this broad line width is due to the impact from the central AGN." (4.2 Companion search of TN J0205+2242)
- Alternative: Western JWST continuum of TN J0121+1320 not used for WCS correction because it may not be associated with the radio galaxy  
  > "this western continuum may not be the emission associated with the radio galaxy" (2.4 Astrometric alignment of NIRSpec IFU cubes)
- How they decided it was enough: _not stated_
- Limitation (authors): Companion search is not complete  
  > "We note that our analysis may not be complete in the sense of detecting all possible companion sources in the fields of the radio galaxies" (3 Analysis)
- Limitation (authors): Dispersion-based masses are upper limits because sizes of unresolved sources are overestimated  
  > "We stress that this mass estimate should be treated as an upper limit, as the size is overestimated." (5.1 Companion kinematics and masses)
- Limitation (authors): [C II] emitters without [O III] or dust counterparts could be other lines at other redshifts  
  > "Without further information, we cannot rule out the possibility that the" (3.2 [C II] emitters)
- Caveat (inferred, ours): Companion status of [O III] blobs rests on kinematic offsets from SINFONI-era bulk motion; outflow or illuminated debris cannot be excluded
- Caveat (inferred, ours): Only four targets and two of the ALMA fields at half depth, so the 100% rate and f_MM ~ 25% are weak statistically
- Caveat (inferred, ours): Low-S/N [C II] detections (3-4 sigma) have no independent confirmation of redshift
- Caveat (inferred, ours): Dynamical masses depend on unconstrained inclination and sizes set by the beam or PSF
- Caveat (inferred, ours): Band 8 astrometry alignment of the NIRSpec cubes depends on assuming the continuum sits at the radio core

## Reproducibility

- Data public (paper): JWST raw data downloaded from MAST; public status of the ALMA data not stated  
  > "We downloaded all raw data from the Mikulski Archive for Space Telescopes (MAST)." (2.2 JWST/NIRSpec IFU)
- Products in archive: _not stated_
- Missing: ALMA line-free channels, masking and image size settings
- Missing: q3dfit input configuration for the 1D and spaxel fits
- Missing: Exact per-companion positions and apertures used for the 1D [C II] spectra beyond the table coordinates
- Missing: Effective radii and axis ratios used in the mass formulas for each companion
- Missing: No released code or analysis scripts; no machine-readable catalogue stated
- Data volume (inferred): Roughly 100-300 GB (ALMA Band 8 C43-5 measurement sets for four fields plus four JWST NIRSpec IFU datasets of ~4 h each)
- Score (inferred): 3/5, Data sources, software versions, robust values and many fit parameters are given, and results are numeric, but imaging masks, line-free channels and q3dfit setup are not stated and no code is released.
- Rediscovery candidate: no, ALMA public status is not stated and key imaging and q3dfit settings are missing, so the main numeric results could not be redone with confidence from the paper alone.

## Links

- Method: Wang, W. et al. 2024, A&A, 683, A169 (cite: Wang_2024) (JWST NIRSpec IFU reduction, q3dfit use and WCS alignment approach followed here)
- Method: Vayner, A. et al. 2023a, ApJ, 955, 92 (cite: Vayner_2023Q3D) (NIRSpec IFU reduction procedure and kinematically tied q3dfit fitting)
- Method: Wylezalek, D. et al. 2022 (cite: Wylezalek_2022q3d); Rupke, D. et al. 2023 (cite: Rupke_2023q3dfit) (q3dfit code used for spectral decomposition)
- Method: Di Teodoro, E. M. & Fraternali, F. 2015 (cite: DiTeodoro_2015) (3DBarolo tilted-ring fitting code)
- Method: Ubler, H. et al. 2023 (cite: ubler_2023) (Dynamical mass formula for dispersion-dominated systems)
- Companion: Wang, W. et al. 2023, A&A, 680, A70 (cite: wang2023) (MUSE and ALMA Band 3 data of the same HzRG sample)
- Companion: Kolwa, S. et al. 2023, MNRAS, 525, 5831 (cite: kolwa2023) ([C I] and He II systemic redshifts and molecular gas of the sample)
- Companion: Nesvadba, N. P. H. et al. 2017a (cite: Nesvadba_2017b) (VLT/SINFONI [O III] kinematics and radio data of the targets)
- Companion: Falkendal, T. et al. 2019, A&A, 621, A27 (cite: Falkendal_2019) (SED fitting giving stellar masses and SFRs)
- Companion: Kukreti et al. (in prep.) (Detailed radio analysis of 4C+03.24)
- Related: JWST-GO-1970 (NIRSpec IFU of the four HzRGs)
- Related: ALMA 2021.1.00576.S (Band 8)
- Related: VLA project 24B-147 (Ku-band, 4C+03.24)
- Related: VLA projects 12B-243 and AY92 (archival, reprocessed)

## Checks

```json
{
 "quotes": 186,
 "quotes_ok": 186,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 21,
 "numeric_problems": 0,
 "fill": {
  "facts": 145,
  "stated": 110,
  "rate": 0.759
 },
 "evidence_ok": true
}
```
