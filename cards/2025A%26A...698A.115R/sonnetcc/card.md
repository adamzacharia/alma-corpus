# Radial variations in the nitrogen, carbon, and hydrogen fractionation in the PDS 70 planet-hosting disk

`2025A&A...698A.115R` | Astronomy and Astrophysics 2025 | first author: Rampinelli, L. | arXiv: 2504.03833 | DOI: 10.1051/0004-6361/202554172

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: What are the radial profiles of nitrogen, carbon and hydrogen fractionation of HCN in the planet-hosting PDS 70 disk, and what fractionation processes do they point to?  
  > "In this work we present the radial profile of nitrogen, carbon, and hydrogen fractionation of the HCN molecule in the PDS 70 disk, where two protoplanets are accreting their atmospheres." (Introduction)
- Target **PDS 70**: coordinates _not stated_; z/distance 113 pc  
  > "and a distance of $113$ pc (cite: brown2018gaia)" (Observations); "$M_\ast = 0.875$ M$_\odot$, $i = 51.7^\circ$, PA$=160.4^\circ$, and $v_\mathrm{sys}=5.5$ km s$^{-1}$ (in LSRK frame), as they were obtained by (cite: keppler2019highly)" (Observations); distance from Gaia (cite: brown2018gaia)  
  > "and a distance of $113$ pc (cite: brown2018gaia)" (Observations); "$M_\ast = 0.875$ M$_\odot$, $i = 51.7^\circ$, PA$=160.4^\circ$, and $v_\mathrm{sys}=5.5$ km s$^{-1}$ (in LSRK frame), as they were obtained by (cite: keppler2019highly)" (Observations)

## Data provenance

- ALMA projects: 2019.1.01619.S, 2022.1.01695.S
- bands: Band 6 (2019.1.01619.S) and Band 7 (2022.1.01695.S) line observations  
  > "we used ALMA Band 6 and 7 line emission observations from projects #2019.1.01619.S (PI S. Facchini) and #2022.1.01695.S (PI M. Benisty)" (Observations); "lists also detected lines in Band 6 data (#2019.1.01619.S, PI S. Facchini)" (Fluxes of Band 6 and 7 molecular lines)
- frequencies and spectral setup: Band 7: four spws of 1.875 GHz, 1920 channels, 977 kHz resolution; 342.483-344.358, 344.379-346.254, 354.483-356.358, 356.441-358.316 GHz  
  > "The spectral setup includes four spectral windows (spws) initially intended for continuum observations, each with a bandwidth of 1.875 GHz, 1920 channels, and a resolution of 977 kHz." (Observations); "The spws cover the same frequency ranges across all EBs: 342.483-344.358 GHz for spw 0, 344.379-346.254 GHz for spw 1, 354.483-356.358 GHz for spw 2, and 356.441-358.316 GHz for spw 3." (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: Band 7: one SB execution block (C-4) and three LB execution blocks (C-7)  
  > "The Band 7 observations consist of four execution blocks (EBs): one short-baseline (SB, ALMA configuration C-4, max baseline 0.8 km) and three long-baseline (LB, configuration C-7, max baseline 3.6 km) configurations." (Observations)
- baselines: Band 7: max baseline 0.8 km (SB), 3.6 km (LB)  
  > "The Band 7 observations consist of four execution blocks (EBs): one short-baseline (SB, ALMA configuration C-4, max baseline 0.8 km) and three long-baseline (LB, configuration C-7, max baseline 3.6 km) configurations." (Observations)
- angular resolution: ~0.20'' (~23 au) and ~0.14'' (~15 au) beam major axes for the Band 6-optimised and Band 7-optimised cubes  
  > "In particular, cubes imaged to maximize Band 6 and Band 7 sensitivity correspond to beam major axes of $\sim0.20\ensuremath{''}$ ($\sim$23 au) and $\sim0.14\ensuremath{''}$ ($\sim$15 au), respectively." (Observations)
- max recoverable scale: _not stated_
- sensitivity: cube RMS (mJy/beam) listed per cube in the imaging tables; evaluated from first and last 5 channels  
  > "RMS is evaluated as standard deviation in the first and last 5 channels of each cube." (Observations)
- time on source: Band 7: 35 min per EB, 2.33 hours total  
  > "Each EB had 35 minutes of on-source time, for a total of 2.33 hours." (Observations)
- observing dates: _not stated_
- pi or archival as stated: 2019.1.01619.S (PI S. Facchini); 2022.1.01695.S (PI M. Benisty)  
  > "projects #2019.1.01619.S (PI S. Facchini) and #2022.1.01695.S (PI M. Benisty)" (Observations)
- Line: H13CN 3-2 (259.0117 GHz)
- Line: H13CN 4-3 (345.3398 GHz)
- Line: HC15N 3-2 (258.1571 GHz)
- Line: HC15N 4-3 (344.2001 GHz)
- Line: DCN 3-2 (217.2386 GHz)
- Line: HCN 4-3 (F=4-3 main hyperfine component) (354.50548 GHz)
- Other facility **Gaia**: distance of 113 pc  
  > "and a distance of $113$ pc (cite: brown2018gaia)" (Observations)
- External data: Stellar mass 0.875 Msun, inclination 51.7 deg, PA 160.4 deg, vsys 5.5 km/s (LSRK) adopted for the analysis  
  > "$M_\ast = 0.875$ M$_\odot$, $i = 51.7^\circ$, PA$=160.4^\circ$, and $v_\mathrm{sys}=5.5$ km s$^{-1}$ (in LSRK frame), as they were obtained by (cite: keppler2019highly)" (Observations) [from (cite: keppler2019highly)]
- External data: Distance 113 pc  
  > "and a distance of $113$ pc (cite: brown2018gaia)" (Observations) [from (cite: brown2018gaia)]
- External data: Radially constant 12C/13C = 69 used to convert H13CN to HCN column density  
  > "assuming a radially constant $\ce{^12C}/\ce{^13C}=69$ ratio (cite: wilson1999isotopes)" (Isotopologue ratios) [from (cite: wilson1999isotopes)]
- External data: ISM D/H value of ~1e-5 used as comparison  
  > "significantly above the ISM D/H value of $\sim10^{-5}$ (cite: linsky2006)" (Isotopologue ratios) [from (cite: linsky2006)]
- External data: 2D temperature structure of the PDS 70 disk used to attempt an HCN emitting-layer estimate  
  > "with the 2D temperature structure of the PDS 70 disk, extracted by (cite: law2024mapping)" (HCN emitting layer from the excitation temperature) [from (cite: law2024mapping)]
- External data: 855 micron continuum integrated intensity profile overplotted for comparison  
  > "The dashed black line shows the integrated intensity profile of the 855 $\mu$m continuum observations (cite: isella2019detection; benisty2021circumplanetary)." (Radial rotational diagram) [from (cite: isella2019detection; benisty2021circumplanetary)]
- External data: Band 6 line fluxes and imaging details taken from the earlier paper  
  > "the reader is referred to (cite: rampinelli2024) for more details on imaging strategies and line flux evaluation." (Fluxes of Band 6 and 7 molecular lines) [from (cite: rampinelli2024)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline, then exoALMA-style self-calibration in CASA  
  > "All the EBs were initially calibrated using the ALMA pipeline, followed by self-calibration based on the pipeline designed by the exoALMA Large Program (Loomis et al., subm.), using the software CASA (cite: CASA2022), version 6.2." (Observations)
- casa version: CASA 6.2 (calibration/self-calibration); CASA v6.65 (imaging)  
  > "using the software CASA (cite: CASA2022), version 6.2" (Observations); "implemented in the `CASA` software (cite: CASA2022) `v6.65`" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10% absolute flux calibration uncertainty included in the likelihood  
  > "a 10% absolute flux calibration uncertainty were considered (sum in quadrature) when generating the likelihood" (Radial rotational diagram)
- self calibration: Band 7: phase-only rounds per EB (EB-long) then SB (EB-long,360,120,60,20 s), concat with LB, phase-only (EB-long,360,120,60,30,18 s), then 2 amplitude+phase rounds (EB-long, scan-long); Band 6 as in Law+2024 / Rampinelli+2024  
  > "A first round of phase-only self-calibration was performed on each EB separately, combining both scans and spws on time intervals over the full EB duration." (Observations); "Multiple rounds with progressively shorter solution intervals were used (EB-long, 360s, 120s, 60s, 20s), stopping when SNR and noise structure began to degrade." (Observations); "Similar to before, we cleaned down to $6\sigma$ at each step, with progressively shorter solution intervals (EB-long, 360s, 120s, 60s, 30s, 18s)." (Observations)

### Imaging

- task: tclean in CASA v6.65  
  > "We imaged the lines using the `tclean` task (cite: hogbom1974aperture; cornwell2008) implemented in the `CASA` software (cite: CASA2022) `v6.65`." (Observations)
- deconvolver: multiscale, scales [0,5,10,20,30] pixels (pixel ~0.02''), threshold 3.5 sigma  
  > "we used a `multiscale` deconvolver with scales \[0,5,10,20,30\] pixels, where the pixel size is $\sim0.02\ensuremath{''}$, and a flux threshold of 3.5$\sigma$." (Observations)
- weighting robust: natural weighting for initial cubes; Briggs robust 0.67 for Band 6 H13CN/HC15N cubes re-imaged to Band 7 resolution; DCN robust 0.3; per-cube robust values in the imaging table  
  > "We first imaged all lines with natural weighting." (Observations); "We therefore imaged the Band 6 and cubes again with Briggs weighting and a robust parameter of 0.67 to match the spatial resolution of Band 7 observations." (12C/13C ratio from the HCN hyperfine component); "Similarly, we re-imaged the DCN cube with a robust parameter of 0.3 to match the beam size of Band 7 observations, and extract the column density profile." (12C/13C ratio from the HCN hyperfine component)
- uv taper: uv-taper and/or robust tuned so cubes share the same spatial resolution (taper values in the imaging table)  
  > "Each time $uv$-taper and/or robust were chosen to obtain cubes with the same spatial resolution." (Observations)
- cell size: _not stated_
- image size: _not stated_
- masking: first CLEAN unmasked; second CLEAN with mask from >7 sigma signal of the first  
  > "We performed a first CLEANing without applying any mask, and a second CLEANing iteration using a mask built by selecting the signal $> 7\sigma$ in the previous iteration (Loomis et al., subm.)." (Observations)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub task on all datasets  
  > "Finally, continuum subtraction was performed on all datasets using the `uvcontsub` task." (Observations)
- line free channels: range of -30 to +30 km/s around each line center flagged before continuum self-calibration  
  > "We flagged the range between -30 km/s to +30 km/s around each line center." (Observations)
- primary beam correction: line fluxes measured on images not primary beam corrected  
  > "used not primary beam corrected images, to ensure uniform noise" (Fluxes of Band 6 and 7 molecular lines)
- array combination: self-calibrated SB EB concatenated with the three LB EBs  
  > "The self-calibrated SB EB was then concatenated with the three LB EBs, and phase-only self-calibration was repeated on the combined dataset." (Observations)
- smoothing: _not stated_
- final beam: ~0.20'' (~23 au) and ~0.14'' (~15 au) beam major axes for the two cube sets  
  > "In particular, cubes imaged to maximize Band 6 and Band 7 sensitivity correspond to beam major axes of $\sim0.20\ensuremath{''}$ ($\sim$23 au) and $\sim0.14\ensuremath{''}$ ($\sim$15 au), respectively." (Observations)
- final rms: _not stated_

### Inherited from earlier work

- Self-calibration pipeline designed by the exoALMA Large Program  
  > "followed by self-calibration based on the pipeline designed by the exoALMA Large Program (Loomis et al., subm.)" (Observations) [from Loomis et al., subm.]
- EB alignment with common uv-grid and phase shifts  
  > "The EBs were then aligned by regridding them to a common uv-grid with natural weighting, retaining only overlapping grid cells, and applying phase shifts to minimize visibility differences (Loomis et al., subm.)." (Observations) [from Loomis et al., subm.]
- Two-pass CLEAN masking strategy  
  > "a second CLEANing iteration using a mask built by selecting the signal $> 7\sigma$ in the previous iteration (Loomis et al., subm.)" (Observations) [from Loomis et al., subm.]
- Band 6 self-calibration  
  > "Self-calibration of Band 6 data was performed as described in (cite: law2024mapping; rampinelli2024)." (Observations) [from (cite: law2024mapping; rampinelli2024)]
- JvM correction by rescaling the residual map  
  > "We applied the so-called JvM correction (cite: jorsater1995high), following (cite: czekala2021molecules), by rescaling the residual map by the ratio between areas of the CLEAN and DIRTY beams" (Observations) [from (cite: czekala2021molecules)]
- Further CLEANing strategy details  
  > "More details on the CLEANing strategies can be found in (cite: rampinelli2024)." (Observations) [from (cite: rampinelli2024)]
- Band 6 imaging and line flux evaluation  
  > "the reader is referred to (cite: rampinelli2024) for more details on imaging strategies and line flux evaluation." (Fluxes of Band 6 and 7 molecular lines) [from (cite: rampinelli2024)]

### Not stated but needed to reproduce (our reading)

- The exoALMA self-calibration pipeline (Loomis et al., subm.) is cited as submitted, so its exact scripts, SNR stop criteria and parameters are not available from this paper.
- ALMA pipeline version, flux/bandpass/phase calibrators and observation dates for the Band 7 and Band 6 EBs are not given.
- Band 6 calibration, self-calibration and imaging details are deferred to Rampinelli et al. 2024 and Law et al. 2024.
- Number of CLEAN iterations, exact mask construction and how the 3.5 sigma / 6 sigma / 1 sigma thresholds were derived (sigma definition per cube) are not given.
- Spectral channel setup for the final cubes (rest-frame regridding, channel width choices per cube beyond table values) and how HCN F-component rest frequencies were applied are not detailed.
- Source of the partition functions Q(T) and Einstein A coefficients (database, version) is not stated in the text.
- How the peak brightness temperature is computed from Jy/beam (Rayleigh-Jeans or full Planck) and how the emitting area Omega is defined in N_u are not stated.
- Radial bin edges and centres for the rotational diagram and hyperfine spectra fits are not listed beyond the 0.1'' annulus width.
- Which cubes are JvM-corrected for flux versus uncorrected for uncertainties in each step is only qualitatively described.

## Analysis recipe

1. **calibrate and self-calibrate Band 7 data, continuum-subtract**: ALMA pipeline then phase-only and amplitude+phase self-calibration on line-free continuum, EB alignment, application to full spectral data, uvcontsub  
  > "All the EBs were initially calibrated using the ALMA pipeline, followed by self-calibration based on the pipeline designed by the exoALMA Large Program (Loomis et al., subm.), using the software CASA (cite: CASA2022), version 6.2." (Observations); "Finally, continuum subtraction was performed on all datasets using the `uvcontsub` task." (Observations)
   - software: ALMA pipeline, CASA, tclean, uvcontsub
   - parameter: lines flagged over -30 to +30 km/s  
  > "We flagged the range between -30 km/s to +30 km/s around each line center." (Observations)
   - parameter: unflagged data averaged to 250 MHz channels  
  > "The remaining unflagged data were averaged into 250 MHz-wide channels." (Observations)
   - parameter: SB self-cal intervals EB-long,360,120,60,20 s; combined EB-long,360,120,60,30,18 s  
  > "Multiple rounds with progressively shorter solution intervals were used (EB-long, 360s, 120s, 60s, 20s), stopping when SNR and noise structure began to degrade." (Observations); "Similar to before, we cleaned down to $6\sigma$ at each step, with progressively shorter solution intervals (EB-long, 360s, 120s, 60s, 30s, 18s)." (Observations)
   - parameter: two amplitude+phase rounds (EB-long, scan-long) after cleaning to 1 sigma  
  > "After this, the data were cleaned down to $1\sigma$, and two rounds of amplitude and phase self-calibration were performed, combining polarizations and spws." (Observations); "The first round used EB-long intervals, while the second used scan-long intervals." (Observations)
   - parameter: full spectral data binned into 30 s intervals  
  > "To reduce dataset size, the full spectral data were binned into 30s intervals." (Observations)
   - fitting: _not stated_
   - validation: flux offsets between EBs minimal (<1%), no flux rescaling needed  
  > "No flux rescaling was necessary, as flux offsets between EBs were minimal ($<1\%$)." (Observations)
2. **image line cubes at matched resolutions**: tclean multiscale CLEAN, two passes (unmasked then 7 sigma mask), JvM correction; two imaging sets tuned to Band 6 and Band 7 sensitivity  
  > "We imaged the lines using the `tclean` task (cite: hogbom1974aperture; cornwell2008) implemented in the `CASA` software (cite: CASA2022) `v6.65`." (Observations); "We performed a first CLEANing without applying any mask, and a second CLEANing iteration using a mask built by selecting the signal $> 7\sigma$ in the previous iteration (Loomis et al., subm.)." (Observations)
   - software: CASA, tclean
   - parameter: multiscale scales [0,5,10,20,30] pixels, pixel ~0.02'', threshold 3.5 sigma  
  > "we used a `multiscale` deconvolver with scales \[0,5,10,20,30\] pixels, where the pixel size is $\sim0.02\ensuremath{''}$, and a flux threshold of 3.5$\sigma$." (Observations)
   - parameter: uv-taper and/or robust chosen for equal resolution across cubes; Band 6 cubes re-imaged with robust 0.67 and DCN with robust 0.3 for the Band 7 resolution set  
  > "Each time $uv$-taper and/or robust were chosen to obtain cubes with the same spatial resolution." (Observations); "We therefore imaged the Band 6 and cubes again with Briggs weighting and a robust parameter of 0.67 to match the spatial resolution of Band 7 observations." (12C/13C ratio from the HCN hyperfine component)
   - parameter: cube RMS from standard deviation in first and last 5 channels  
  > "RMS is evaluated as standard deviation in the first and last 5 channels of each cube." (Observations)
   - fitting: _not stated_
   - validation: JvM correction applied, but not for uncertainty evaluation since it could be underestimated  
  > "except for uncertainty evaluation, which could be underestimated by the JvM correction (cite: casassus2022variable)" (Observations)
3. **build integrated intensity maps**: bettermoments zeroth moment over a velocity range chosen by eye per line  
  > "We calculated integrated intensity maps of the imaged cubes using the `bettermoments` package (cite: teague2019bettermoments), integrating data cubes over a velocity range where each line shows emission in the channel maps." (Observations)
   - software: bettermoments
   - parameter: velocity ranges chosen after visual inspection  
  > "Velocity ranges over which data cubes where collapsed to extract integrated intensity, chosen after visual inspection of the data." (Observations)
   - fitting: _not stated_
   - validation: _not stated_
4. **measure line fluxes**: spatially integrate moment-0 maps inside de-projected circles; uncertainty from the scatter of the flux in 26 emission-free circles  
  > "Line fluxes are obtained by spatially integrating the integrated intensity maps of each line inside a de-projected circle with radius 3$^{\prime\prime}$ for the most extended , and 2$^{\prime\prime}$ for the others." (Fluxes of Band 6 and 7 molecular lines); "The uncertainty is evaluated as the standard deviation of the flux measured in 26 de-projected circles, outside the emitting area of the integrated intensity maps, with the same radius used to extract the flux." (Fluxes of Band 6 and 7 molecular lines)
   - parameter: circle radius 3'' for the most extended line, 2'' for the others; not primary-beam-corrected images  
  > "used not primary beam corrected images, to ensure uniform noise" (Fluxes of Band 6 and 7 molecular lines)
   - fitting: _not stated_
   - validation: _not stated_
5. **extract radial integrated-intensity profiles**: GoFish azimuthal average over 0.1'' wide annuli (full azimuth, because a +/-30 deg wedge had too low S/N)  
  > "we extracted the radial profiles of the integrated intensity of each line, using the `GoFish` package (cite: teague2019gofish)" (Radial rotational diagram); "We therefore extracted the integrated intensity profiles by performing a complete azimuthal average over $0.1\ensuremath{''}$ wide annuli." (Radial rotational diagram)
   - software: GoFish
   - parameter: geometry Mstar=0.875 Msun, i=51.7 deg, PA=160.4 deg, vsys=5.5 km/s, d=113 pc  
  > "$M_\ast = 0.875$ M$_\odot$, $i = 51.7^\circ$, PA$=160.4^\circ$, and $v_\mathrm{sys}=5.5$ km s$^{-1}$ (in LSRK frame), as they were obtained by (cite: keppler2019highly)" (Observations)
   - fitting: _not stated_
   - validation: _not stated_
6. **radial rotational diagram for H13CN and HC15N**: radially resolved rotational diagram with optical-depth correction C_tau, on cubes with equal beams; single Tex fitted jointly for both isotopologues  
  > "we could apply the rotational diagram (cite: goldsmith1999population) analysis to extract their molecular column density $N_\mathrm{t}$ and excitation temperature $T_\mathrm{ex}$" (Radial rotational diagram); "We computed the rotational diagram correcting for the optical depth factor $C_\tau$." (Radial rotational diagram); "we applied a final rotational diagram analysis fitting for a single excitation temperature for both and" (Radial rotational diagram)
   - software: emcee
   - parameter: optical depth from peak brightness temperature and Tex, tau = -ln(1 - Tb/Tex), Tb the azimuthal average of peak Tb in each annulus  
  > "where $T_\mathrm{b}(R)$ is the radial profile of the brightness temperature, taken as the azimuthal average of the peak brightness temperature over each annulus in which we applied the rotational diagram" (Radial rotational diagram)
   - parameter: cubes with smallest channel width allowed by the spectral resolution  
  > "We therefore used cubes imaged with the smallest width of the velocity channel allowed by the spectral resolution of the observations." (Radial rotational diagram)
   - parameter: Band 6-optimised cubes (~0.20'') in the main result; Band 7-optimised (~0.15'') as a consistent alternative  
  > "The two results are consistent, and were both used to extract the radial profiles of N, C, and H fractionation of HCN" (Radial rotational diagram)
   - assumption: optically thin N_u relation, corrected by C_tau  
  > "In the optically thin assumption, $N_\mathrm{u}$ depends on the integrated flux density" (Radial rotational diagram)
   - assumption: excitation temperature equals kinetic temperature (LTE)  
  > "The rotational diagram assumes that the excitation temperature $T_\mathrm{ex}(r)$ is equal to the kinetic temperature $T(r,z)$ (LTE)." (HCN emitting layer from the excitation temperature)
   - fitting: emcee, 128 walkers, 3000 burn-in, 500 steps; uniform priors Tex 10-100 K, Nt 1e10-1e16 cm-2; likelihood includes propagated uncertainties and 10% flux calibration in quadrature  
  > "through a Markov-Chain Monte Carlo (MCMC) method with the `emcee` package (cite: foreman2013emcee), with 128 walkers, 3000 burn-in steps, and 500 steps" (Radial rotational diagram); "We considered a uniform prior with $T_\mathrm{ex}\in (10,100)$ K and $N_\mathrm{t} \in (10^{10}, 10^{16})$ cm$^{-2}$." (Radial rotational diagram); "The propagated uncertainty on the integrated intensity, on the brightness temperature and a 10% absolute flux calibration uncertainty were considered (sum in quadrature) when generating the likelihood." (Radial rotational diagram)
   - validation: spectral smearing tested with 0.4 vs 0.8 km/s channel cubes and found negligible  
  > "This effect is thus negligible in the rotational diagram analysis we performed in this work." (Spectral smearing effect on brightness temperature)
7. **N and H fractionation with fixed 12C/13C**: build posteriors of 69 x N(H13CN)/N(HC15N) and N(DCN)/[69 x N(H13CN)] from column-density posteriors; DCN column density from the rotational-diagram equation with randomly sampled Tex  
  > "ratios were built from the posterior distributions of the column density of , , and DCN." (Isotopologue ratios); "by randomly sampling the excitation temperature from the rotational diagram result, assuming DCN has the same excitation temperature as and" (Isotopologue ratios)
   - parameter: 12C/13C = 69 (radially constant)  
  > "assuming a radially constant $\ce{^12C}/\ce{^13C}=69$ ratio (cite: wilson1999isotopes)" (Isotopologue ratios)
   - parameter: DCN flux sampled from a normal distribution with its statistical uncertainty  
  > "by randomly sampling the flux of the DCN (3-2) line from a normal distribution centered around the median value, with a standard deviation given by its statistical uncertainty" (Isotopologue ratios)
   - assumption: DCN has the same excitation temperature as H13CN and HC15N  
  > "assuming DCN has the same excitation temperature as and" (Isotopologue ratios)
   - fitting: _not stated_
   - validation: radially constant 12C/13C checked against the HCN-hyperfine carbon profile  
  > "the carbon fractionation profile is consistent with the ISM value between $\sim50$ and 100 au, within the errorbars" (Isotopologue ratios using HCN column density)
8. **HCN column density from resolved hyperfine component**: double-Gaussian fit to deprojected spectra in radial bins (hyperfine component at 3.8 km/s and main component at 5.5 km/s), flux posterior, optically thin N(HCN) with Tex from the rotational diagram  
  > "To extract the radial profile of the flux of the hyperfine component, we applied a double-Gaussian fit to the spectrum in multiple radial bins." (Radial profile of HCN column density); "we extracted the radial profile of the column density of HCN, assuming that the hyperfine component is optically thin, and the same excitation temperature inferred from the rotational diagram analysis of and" (12C/13C ratio from the HCN hyperfine component)
   - software: GoFish, emcee
   - parameter: centers fixed at 3.8 and 5.5 km/s; widths and peaks free; spectra shifted for Keplerian rotation with GoFish  
  > "We fixed the center of the two Gaussian components to 3.8 km s$^{-1}$ for the hyperfine and to 5.5 km s$^{-1}$ for the main component respectively, and fit for the two widths and peaks." (12C/13C ratio from the HCN hyperfine component)
   - parameter: fit stopped at 5.5 km/s (only half of the main component covered by LB)  
  > "We extracted the flux associated with the hyperfine component by fitting a double Gaussian to the spectrum, stopping at 5.5  km s$^{-1}$." (12C/13C ratio from the HCN hyperfine component)
   - parameter: Gaussians spectrally over-sampled and averaged in each spectral bin  
  > "we spectrally over-sampled the Gaussian profiles and took the average value inside a spectral bin, to fit the observed spectrum" (12C/13C ratio from the HCN hyperfine component)
   - parameter: fiducial radial range ~50-120 au  
  > "The fiducial radial range is between $\sim50$ and 120 au, because for small radii the two components are blended, and the fit is poorly constrained" (12C/13C ratio from the HCN hyperfine component)
   - assumption: hyperfine component optically thin (tau <~ 0.02)  
  > "by assuming it is optically thin, which is valid since $\tau\lesssim0.02$" (Radial profile of HCN column density)
   - assumption: same Tex as H13CN/HC15N from the Band 7 resolution rotational diagram  
  > "We therefore computed the radial profile of the HCN column density, assuming the same excitation temperature obtained from the rotational diagram of and" (Radial profile of HCN column density)
   - fitting: emcee per annulus, 128 walkers, 500 burn-in, 500 steps; uniform priors: widths (0,5) km/s, hyperfine peak (0,10) mJy/beam, main peak (0,30) mJy/beam; flux from 50th/16th/84th percentiles  
  > "We applied the MCMC sampling to each annulus in which we divided the disk, with 128 walkers, 500 burn-in steps, and 500 steps" (12C/13C ratio from the HCN hyperfine component); "assuming a uniform prior of (0,5) km s$^{-1}$ for the two widths, of (0,10) mJy beam$^{-1}$ for the peak of the hyperfine component, and of (0,30) mJy beam$^{-1}$ for the peak of the main component" (12C/13C ratio from the HCN hyperfine component)
   - validation: in the fiducial range the hyperfine Gaussian width is consistent with a radially constant line width  
  > "in the fiducial range the Gaussian fit to the hyperfine component is consistent with a radially constant line width" (12C/13C ratio from the HCN hyperfine component)
9. **isotopologue ratios using the HCN column density**: form HCN/H13CN, HCN/HC15N and DCN/HCN ratios from column-density posteriors using the Band 7 resolution cubes  
  > "From the HCN column density retrieved from the hyperfine fitting procedure, we extracted the radial profiles of the isotopologue ratios" (Isotopologue ratios using HCN column density)
   - parameter: cubes imaged to maximize Band 7 sensitivity (~0.15'' resolution) because higher resolution is needed for the hyperfine fit  
  > "as a higher angular resolution is needed to perform the hyperfine fitting procedure" (Isotopologue ratios using HCN column density)
   - fitting: _not stated_
   - validation: ratios with fixed 12C/13C=69 and from the HCN column density are consistent within the errors  
  > "are consistent within the errorbars" (Isotopologue ratios using HCN column density)

## Software

- **CASA** 6.2 (calibration); v6.65 (imaging): calibration, self-calibration and imaging  
  > "using the software CASA (cite: CASA2022), version 6.2" (Observations); "implemented in the `CASA` software (cite: CASA2022) `v6.65`" (Observations)
- **ALMA pipeline** : initial calibration of the Band 7 EBs  
  > "All the EBs were initially calibrated using the ALMA pipeline" (Observations)
- **tclean** : multiscale CLEAN imaging of line cubes and self-calibration models  
  > "We imaged the lines using the `tclean` task (cite: hogbom1974aperture; cornwell2008)" (Observations)
- **uvcontsub** : continuum subtraction  
  > "Finally, continuum subtraction was performed on all datasets using the `uvcontsub` task." (Observations)
- **bettermoments** : integrated intensity maps  
  > "using the `bettermoments` package (cite: teague2019bettermoments)" (Observations)
- **GoFish** : radial profiles and Keplerian-corrected spectra  
  > "using the `GoFish` package (cite: teague2019gofish)" (Radial rotational diagram); "corrected for the Keplerian rotation of the disk using the `GoFish` package (cite: teague2019gofish)" (12C/13C ratio from the HCN hyperfine component)
- **emcee** : MCMC sampling of rotational diagram and hyperfine Gaussian fits  
  > "with the `emcee` package (cite: foreman2013emcee), with 128 walkers, 3000 burn-in steps, and 500 steps" (Radial rotational diagram); "We sampled the posterior distribution using an MCMC sampler through the `emcee` package (cite: foreman2013emcee)." (12C/13C ratio from the HCN hyperfine component)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Band 6 H13CN (3-2) line flux | 360 | 8 | mJy km/s | 4 | 360 $\pm$ 8 |
| Band 6 HC15N (3-2) line flux | 176 | 7 | mJy km/s | 4 | 176 $\pm$ 7 |
| Band 6 DCN (3-2) line flux | 230 | 6 | mJy km/s | 4 | 230 $\pm$ 6 |
| Band 7 H13CN (4-3) line flux (345.3398 GHz row) | 530 | 21 | mJy km/s | 4 | 530 $\pm$ 21 |
| Band 7 HC15N (4-3) line flux (344.2003 GHz row) | 234 | 34 | mJy km/s | 4 | 234 $\pm$ 34 |
| Band 7 HCN (4-3) line flux, SB observations only (354.5055 GHz row) | 5902 | 45 | mJy km/s | 4 | 5902 $\pm$ 45 |
| Optical depth of HCN hyperfine component | <~0.02 | not stated | dimensionless | 8 | by assuming it is optically thin, which is valid since $\tau\lesssim0.02$ |
| DCN/HCN deuteration level between 40 and 100 au | ~0.02 | not stated | dimensionless | 9 | The deuteration profile is almost flat (around $\sim0.02$, for radii between 40 and 100 au. |
| Radius of turnover in the HCN/HC15N ratio | ~60 | not stated | au | 9 | ratio shows a turnover at $\sim60$ au, and it decreases below the ISM value at larger radii |
| Fiducial radial range of the hyperfine-based HCN column density | ~50-120 | not stated | au | 8 | The fiducial radial range is between $\sim50$ and 120 au |
| Radius beyond which carbon fractionation may become relevant | ~90 | not stated | au | 9 | our result for the PDS 70 disk shows that carbon fractionation may become relevant beyond $\sim$90 au |

## Qualitative findings

- Nitrogen fractionation (14N/15N from fixed 12C/13C) is decreasing with radius and below the ISM value from ~40 to 100 au.  
  > "The nitrogen fractionation profile is decreasing and below the ISM value from $\sim40$ to 100 au" (Isotopologue ratios)
- Deuteration is mostly constant between ~40 and 100 au and well above the ISM D/H.  
  > "while the deuteration profile is mostly constant between $\sim40$ au 100 au, and significantly above the ISM D/H value of $\sim10^{-5}$ (cite: linsky2006)" (Isotopologue ratios)
- Fractionation profiles show no clear correlation with the continuum profile.  
  > "which do not show any clear correlation with the fractionation profiles" (Isotopologue ratios)
- The decreasing HCN/HC15N trend is argued to be driven by isotope selective photodissociation of N2, in qualitative agreement with Visser et al. 2018 models.  
  > "This qualitative agreement between the result directly extracted from ALMA observations in this work, and the prediction from thermo-chemical models" (Nitrogen)

## Claim tuples

- H: Does the nitrogen fractionation of HCN vary radially in the PDS 70 disk? | E: Radial rotational diagram of H13CN and HC15N, with 12C/13C=69 to convert H13CN to HCN, giving HCN/HC15N versus radius | R: The HCN/HC15N profile is decreasing and below the ISM value from ~40 to 100 au, with a turnover at ~60 au | F: A decreasing HCN/HC15N trend outside the cavity wall, suggested to link to isotope selective photodissociation of N2 | **supported**
- H: What is the radial deuteration profile of HCN in PDS 70? | E: Rotational diagram column densities of DCN and H13CN (times 69), plus an HCN-column-density version from the hyperfine fit | R: DCN/HCN is almost flat, ~0.02 between 40 and 100 au | F: HCN deuteration is far above the ISM D/H and uncorrelated with nitrogen fractionation, consistent with gas-phase isotope exchange | **supported**
- H: Is the radially constant 12C/13C=69 assumption justified, and does carbon fractionation matter? | E: HCN column density from the resolved hyperfine component at 354.5075 GHz via a double-Gaussian fit, then HCN/H13CN | R: The carbon fractionation is consistent with the ISM value between ~50 and 100 au within errors, and may become relevant beyond ~90 au | F: The fixed-ratio assumption is justified inside ~100 au, but carbon fractionation in the outer disk remains uncertain with the large errors | **partially**
- H: How do the PDS 70 isotopologue ratios compare with other evolutionary stages and comets? | E: Compiled literature isotopologue ratios of HCN for cores, YSOs, disks and comets and compared them with the PDS 70 radial profiles | R: HCN/H13CN and HCN/HC15N comet values match the outer disk beyond ~70 au, while the Hale-Bopp DCN/HCN is about an order of magnitude below PDS 70 | F: A possible link between cometary material and outer-disk gas for carbon and nitrogen, but not for deuterium, in a picture the authors call very uncertain | **partially**

## Reasoning

- Why this data: PDS 70 hosts two accreting protoplanets, and isotopic ratios of the disk gas can be compared with planet formation environments  
  > "In this work we present the radial profile of nitrogen, carbon, and hydrogen fractionation of the HCN molecule in the PDS 70 disk, where two protoplanets are accreting their atmospheres." (Introduction)
- Why this method: H13CN and HC15N have two lines each, enabling a rotational diagram; HCN itself is typically optically thick so isotopologues are used  
  > "As two lines are detected for both and , with upper energies ranging from $\sim25$ to 41 K, we could apply the rotational diagram (cite: goldsmith1999population) analysis" (Radial rotational diagram); "as the latter is typically optically thick (cite: guzman2017)" (Isotopologue ratios)
- Alternative: Profiles from a +/-30 deg wedge along the major axis were tried but the S/N for DCN and especially HC15N was too low, so full azimuthal averages were used  
  > "However, the resulting signal-to-noise ratio for DCN and in particular was too low to allow for the analysis presented in this paper." (Radial rotational diagram)
- Alternative: HCN cube could not be smoothed to the lower resolution of the rotational diagram cubes because of hyperfine blending  
  > "We were unable to smooth the HCN cube to match the spatial resolution of" (Radial profile of HCN column density)
- Alternative: Estimating the HCN emitting layer from the excitation temperature was inconclusive  
  > "but the large uncertainties make it inconclusive" (HCN emitting layer from the excitation temperature)
- Alternative: Spectral smearing correction not applied because it is negligible  
  > "which we evaluated to be negligible in our case, and thus did not include in the analysis" (Radial rotational diagram)
- How they decided it was enough: _not stated_
- Limitation (authors): Hyperfine fit limited by half-covered HCN (4-3), 0.9 km/s resolution and low S/N, giving large errors and no robust ratios inside ~40 au or beyond ~100 au  
  > "is strongly limited by the fact that only half of the HCN (4-3) line is covered by LB observations, by the low spectral resolution of $\sim0.9$ km s$^{-1}$, and the lower signal to noise ratio" (Isotopologue ratios using HCN column density)
- Limitation (authors): Profiles inside ~25 au are highly uncertain  
  > "highly uncertain for radii $\lesssim 25$ au, and therefore need to be interpreted with caution" (Nitrogen)
- Limitation (authors): Nitrogen and carbon fractionation cannot be robustly separated, making the interpretation speculative  
  > "which makes the above interpretation only speculative, as the role of nitrogen and carbon fractionation in determining the decreasing trend cannot be robustly distinguished with current observations" (Carbon)
- Caveat (inferred, ours): Main nitrogen and deuteration profiles rely on a fixed 12C/13C=69, while the paper itself finds possible carbon fractionation beyond ~90 au.
- Caveat (inferred, ours): A single Tex shared by H13CN, HC15N, DCN and HCN is assumed, despite different molecules tracing different layers.
- Caveat (inferred, ours): No chemical or radiative-transfer modelling of PDS 70 supports the photodissociation interpretation.
- Caveat (inferred, ours): Rotational diagram with only two lines per species and a 10% calibration term gives limited leverage on Tex and tau.
- Caveat (inferred, ours): Analysis relies on unpublished exoALMA self-calibration and Band 6 processing from earlier papers.

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: exoALMA self-calibration pipeline (Loomis et al., subm.) scripts and parameters
- Missing: Calibrators, pipeline version, observation dates and any Band 6 processing (deferred to Rampinelli+2024 / Law+2024)
- Missing: Per-annulus data products and the analysis code are not released or mentioned
- Missing: Partition function and line-parameter catalogue versions and Tb computation details
- Missing: Radial bin definitions for the hyperfine fits
- Data volume (inferred): On the order of 100-300 GB raw for the two projects (Band 7 with 4 EBs, Band 6 multiple EBs); self-calibrated measurement sets are smaller after binning.
- Score (inferred): 3/5, Two project codes and a fairly detailed recipe (self-cal, tclean, rotational diagram priors, emcee settings, hyperfine fit priors) but key steps are inherited from unpublished or earlier papers, public availability is not stated, and no code is released.
- Rediscovery candidate: no, Data public status is not stated and the self-calibration depends on an unpublished pipeline, although the downstream analysis is well specified and numeric.

## Links

- Method: Rampinelli et al. 2024 (cite: rampinelli2024) (Band 6 imaging, CLEAN strategy and line flux evaluation)
- Method: Loomis et al., subm. (exoALMA) (self-calibration pipeline, EB alignment and masking strategy)
- Method: Czekala et al. 2021 (cite: czekala2021molecules) (JvM correction implementation)
- Method: Law et al. 2024 (cite: law2024mapping) (Band 6 self-calibration and PDS 70 temperature structure)
- Method: Teague 2019 (cite: teague2019gofish) (GoFish radial profiles)
- Companion: Facchini et al. 2021 (cite: bib:facchini2021chemical) (first chemical inventory of the PDS 70 disk)
- Companion: Rampinelli et al. 2024 (cite: rampinelli2024) (high-resolution line emission of PDS 70 molecular tracers)
- Companion: Cataldi et al. 2021 (cite: cataldi2021molecules) (MAPS DCN/HCN profiles used for comparison)
- Companion: Visser et al. 2018 (cite: visser2018nitrogen) (thermo-chemical nitrogen fractionation models used for interpretation)
- Related: exoALMA Large Program
- Related: MAPS

## Checks

```json
{
 "quotes": 159,
 "quotes_ok": 159,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 129,
  "stated": 103,
  "rate": 0.798
 },
 "evidence_ok": true
}
```
