# No Evidence for [C II] Halos or High-velocity Outflows in z ≳ 6 Quasar Host Galaxies

`2020ApJ...904..131N` | The Astrophysical Journal 2020 | first author: Novak, Mladen | arXiv: 2010.14875 | DOI: 10.3847/1538-4357/abc33f

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: Do z>~6 quasar host galaxies show extended [C II] / dust halos or high-velocity [C II] outflows, tested with uv-plane stacking of ~1 kpc resolution ALMA data of 27 hosts?  
  > "We revisit this topic by using the deepest available ALMA data and novel analysis techniques." (Introduction); "In this paper, we perform stacking and" (Introduction)
- Target **Sample of 27 z>~6 quasar host galaxies (e.g. P007+04, J0100+2802, J1306+0356, J1342+0928, J2054-0005)**: coordinates per-source RA/Dec in Table 1, measured from [C II] intensity maps (Venemans et al. 2020)  
  > "The main sample for our study consists of 27 quasar host galaxies" (2 Data and samples); "whereas coordinates are measured from the" (2.1 New and archival ALMA data); "Throughout the paper we assume the concordance Lambda cold dark matter" (1 Introduction); z/distance z = 5.8-7.5; mean z = 6.4 (5.5 kpc per arcsec); H0 = 70, OmegaL = 0.7, Omegam = 0.3  
  > "The main sample for our study consists of 27 quasar host galaxies" (2 Data and samples); "whereas coordinates are measured from the" (2.1 New and archival ALMA data); "Throughout the paper we assume the concordance Lambda cold dark matter" (1 Introduction); distance from [C II] redshifts measured from aperture-extracted spectra; flat LCDM cosmology adopted  
  > "The main sample for our study consists of 27 quasar host galaxies" (2 Data and samples); "whereas coordinates are measured from the" (2.1 New and archival ALMA data); "Throughout the paper we assume the concordance Lambda cold dark matter" (1 Introduction)
- Target **J1306+0356 (worked example for methods)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00240.S, 2012.1.00882.S, 2013.1.00273.S, 2015.1.00399.S, 2015.1.00606.S, 2015.1.00692.S, 2015.1.00997.S, 2015.1.01115.S, 2016.1.00544.S, 2016.A.00018.S, 2017.1.00396.S, 2017.1.01301.S, 2018.1.00908.S
- bands: _not stated_
- frequencies and spectral setup: All four science spectral windows used for continuum; up to 3.75 GHz contiguous bandwidth per setup; [C II] of z~6 galaxies at ~270 GHz  
  > "All available continuum data were used (i.e. data from all four science spectral windows)." (2.2.3 Stacking the data in the uv-plane); "In a single spectral setup, ALMA provides up to 3.75 GHz of a contiguous bandwidth coverage" (Footnote 19)
- continuum bandwidth: _not stated_
- arrays: 12 m and 7 m (ACA) arrays; datasets are 12 m unless noted in Table 1  
  > "we consider all available 12 m and 7 m ALMA observations performed in cycles 1 through 6" (2.1 New and archival ALMA data); "where all datasets correspond to 12 m array observations, unless noted otherwise" (2.1 New and archival ALMA data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~1 kpc high-resolution dataset per source, plus lower-resolution archival datasets for 20 objects; beam sizes per dataset in Table 1 (computed 0.574 lambda/L80)  
  > "Datasets with lower spatial resolution observations, obtained across multiple ALMA observational cycles, are available for 20 objects in our sample." (2.1 New and archival ALMA data)
- max recoverable scale: MRS per dataset in Table 1, computed as 0.983 lambda/L5 (L5 = 5th percentile of uv-distances); defined as the size recovering at least 10% of a uniform disk  
  > "The last two values are computed based on the baseline statistics following the ALMA Technical Handbook (Eqs. 7.4 and 7.7)" (2.1 New and archival ALMA data); "The MRS is defined as the largest angular size at which at least 10% of the total flux density of a uniform disk is recovered" (2.1 New and archival ALMA data)
- sensitivity: _not stated_
- time on source: Full uv-stacking sample ~34 h (25.5 h with 12 m); clean uv-stacking sample ~18 h; per-dataset TOS in Table 1  
  > "The cumulative on source time is approximately 34 h (out of which 25.5 h were taken with the 12 m array)." (2.4 Data samples); "The cumulative time on source is approximately 18 h." (2.4 Data samples)
- observing dates: _not stated_
- pi or archival as stated: Mix: bulk of high-resolution data from the authors' own programs (2017.1.01301.S, 2018.1.00908.S) plus archival low-resolution data  
  > "The bulk of the high spatial resolution data comes from our recent programs with IDs 2017.1.01301.S and 2018.1.00908.S." (2.1 New and archival ALMA data); "we make use of all available archival data targeting the" (2.1 New and archival ALMA data)
- Line: C+ 2P3/2 -> 2P1/2 ([C II]) (158 um rest wavelength (rest frequency not stated))
- External data: Redshifts, [C II] line fluxes, FWHMs and source coordinates in Table 1 (measured from aperture spectra / intensity maps)  
  > "whereas coordinates are measured from the" (2.1 New and archival ALMA data); "as reported in (cite: venemans20)" (2.1 New and archival ALMA data) [from (cite: venemans20)]
- External data: Mean of individual dust continuum measurements used to check the stacked continuum flux  
  > "is consistent with the mean of individual continuum measurements (cite: venemans20)" (4.2 Spatial extent of the dust continuum emission) [from (cite: venemans20)]
- External data: Assumed stellar masses of 10^10.5-11 Msun for quasar hosts  
  > "Based on the simulations of (cite: marshall19b), which probe the properties of quasar host galaxies, we assume that galaxies in our sample have stellar masses of" (5.1 Spatial extent of the [C II] and dust emission) [from (cite: marshall19b)]
- External data: Stellar mass - size evolution giving stellar half-light radii of 1 - 2 kpc at z~7  
  > "the stellar mass - size evolution fit by (cite: allen17) indicates that our sample should have stellar half-light radii of 1 – 2 kpc" (5.1 Spatial extent of the [C II] and dust emission) [from (cite: allen17)]
- Simulation/model as data: MassiveFIRE cosmological zoom-in simulations (D and E series at z = 6): 5 galaxies, each viewed from 18 random directions; SKIRT dust radiative transfer post-processing; predicted 1.2 mm ALMA maps stacked into a radial profile  
  > "We compare our observational data with predictions from the MassiveFIRE suite of cosmological zoom-in simulations" (5.2 Dust emission from the MassiveFIRE simulation); "each viewed from 18 random directions, and by averaging the flux densities in radial annuli" (5.2 Dust emission from the MassiveFIRE simulation)

## Processing

### Calibration

- pipeline or manual: Default pipeline restoration scripts in the original CASA version; full pipeline calibration also rerun on all 54 datasets in CASA 5.6.1-8 as a check  
  > "we reduced the raw data using the default pipeline restoration scripts executed in the appropriate version of the Common Astronomy Software Applications (CASA) package" (2.2 Data reduction); "we reran the full pipeline calibration process on each of the 54 datasets, using the latest CASA version at the time of writing" (2.2.1 Flux calibration accuracy)
- casa version: CASA 4.1 to 5.4.0-68 (original calibration); 5.6.1-8 for the recheck  
  > "i.e. the same version applied during the original calibration (CASA 4.1 to 5.4.0-68)" (2.2 Data reduction); "using the latest CASA version at the time of writing (version 5.6.1-8)" (2.2.1 Flux calibration accuracy)
- pipeline version: _not stated_
- archive products used as is: Calibrated visibilities from default restoration scripts used, except Pallas/Ceres datasets  
  > "we continued to use the calibrated visibilities provided by the default restoration scripts (except in the case of Pallas and Ceres calibrators as mentioned above)" (2.2.1 Flux calibration accuracy)
- flux calibrator: Nine datasets with wrong Ceres/Pallas models (CASA 4.6 or lower) recalibrated in newer CASA; online ALMA flux calibrator catalog query manually enabled in the recheck  
  > "There are a total of nine datasets affected by this issue" (2.2.1 Flux calibration accuracy); "we manually enabled the query to the online ALMA flux calibrator catalog" (2.2.1 Flux calibration accuracy)
- flux scale uncertainty: 10% (usually reported calibration accuracy); no further flux changes beyond 10% found  
  > "yielded no flux level changes beyond 10%, which is the usually reported calibration accuracy value" (2.2.1 Flux calibration accuracy)
- self calibration: _not stated_

### Imaging

- task: CASA tclean (per-source cubes/maps and uv-stacked images)  
  > "We imaged the calibrated visibilities, using the CASA task tclean, with the Högbom deconvolver, and a channel spacing of 30 MHz" (2.2.2 Data products per galaxy); "We imaged the split, renormalized and re-centered data using the CASA task tclean, considering the full list of all sources and cycles." (2.2.3 Stacking the data in the uv-plane)
- deconvolver: Högbom for per-source data; multi-scale for uv-stacks  
  > "with the Högbom deconvolver" (2.2.2 Data products per galaxy); "applied the multi-scale deconvolver, with scales corresponding to 0 (delta-function), 1, 3, 5 and 10 synthesized beam sizes" (2.2.3 Stacking the data in the uv-plane)
- weighting robust: Briggs, robust = 0.5 (per-source imaging)  
  > "(robust = 0.5) and cleaned (deconvolved) the maps down to" (2.2.2 Data products per galaxy)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: 2 arcsec radius cleaning mask, cleaned to 2 sigma  
  > "Cleaning was performed within a 2" (2.2.3 Stacking the data in the uv-plane); "within a cleaning mask radius of" (2.2.2 Data products per galaxy)
- multiscale scales: 0 (delta-function), 1, 3, 5 and 10 synthesized beam sizes  
  > "with scales corresponding to 0 (delta-function), 1, 3, 5 and 10 synthesized beam sizes" (2.2.3 Stacking the data in the uv-plane)
- continuum subtraction: uvcontsub on the two spectral windows around [C II], first-order fit (fitorder = 1) allowing a continuum slope  
  > "performed the continuum subtraction using the uvcontsub task on the two spectral windows around the" (2.2.2 Data products per galaxy); "while allowing for a continuum slope (fitorder = 1)" (2.2.2 Data products per galaxy)
- line free channels: Channels within a total width of 2.5xFWHM around [C II] excluded (on average ~900 km/s); 8xFWHM used as a check for continuum  
  > "the total excluded bandwidth is on average 900" (2.2.2 Data products per galaxy); "this time excluding a much broader bandwidth of" (2.2.3 Stacking the data in the uv-plane)
- primary beam correction: _not stated_
- array combination: All sources, cycles (and, in the full sample, 7 m data) imaged together in the uv-stack  
  > "considering the full list of all sources and cycles" (2.2.3 Stacking the data in the uv-plane)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Per-galaxy data products (measurement sets, maps, cubes) built as in the first paper of the series  
  > "as described in (cite: venemans20). We briefly summarize these here." (2.2.2 Data products per galaxy) [from (cite: venemans20)]
- uv-stacking method adapted from earlier work and extended to the whole spectrum  
  > "we have adapted the method described in e.g. (cite: fujimoto19), and extended it to be applicable to the whole spectrum" (2.2.3 Stacking the data in the uv-plane) [from (cite: fujimoto19)]
- Residual scaling of aperture fluxes from residual map  
  > "To mitigate this issue we scale the flux collected from the residual map (cite: jorsater95; walter08; novak19)." (3.1.1 Analysis in the image plane) [from (cite: jorsater95; walter08; novak19)]
- Single-beam (single pixel) spectrum at the central [C II] peak  
  > "we performed a single beam (i.e. single pixel) measurement at the central" (4.3 High-velocity outflows) [from following (cite: decarli18)]
- Recalibration of datasets affected by wrong Ceres/Pallas flux models in CASA 4.6 or lower  
  > "As noted by (cite: stanley19), several datasets required recalibration in a newer CASA version" (2.2.1 Flux calibration accuracy) [from (cite: stanley19)]
- Beam size and MRS formulae  
  > "following the ALMA Technical Handbook (Eqs. 7.4 and 7.7)" (2.1 New and archival ALMA data) [from ALMA Technical Handbook]

### Not stated but needed to reproduce (our reading)

- Robust/weighting for the uv-stack tclean runs (only given for per-source imaging; figure file names hint at robust weighting)
- Cell size, image size and primary-beam correction settings for tclean
- Per-source aperture radii (chosen manually after visual inspection) and the line-free channels per source
- Exact rms used to define the 2 sigma clean threshold and number of tclean iterations
- statwt parameters (time bin, channel bin) beyond 'same time and channels bin for all datasets'
- Which exact datasets were excluded for each of the four samples (only footnote markers in Table 1)
- CASA version actually used for each individual dataset and the five datasets where the 5.6.1 rerun failed
- Per-source flux fix factors applied after Ceres/Pallas recalibration
- Annulus widths and centering for the surface brightness profiles and error definition
- Fitting priors and error treatment for the Gaussian+constant and uvmultifit fits
- MassiveFIRE maps and SKIRT outputs (from Liang et al. 2019) needed to repeat the comparison

## Analysis recipe

1. **calibrate and quality-check the visibilities**: Default pipeline restoration scripts in the original CASA version; datasets with wrong Ceres/Pallas models recalibrated; full pipeline rerun in CASA 5.6.1-8 as a flux-scale check  
  > "we reduced the raw data using the default pipeline restoration scripts executed in the appropriate version of the Common Astronomy Software Applications (CASA) package" (2.2 Data reduction); "we reran the full pipeline calibration process on each of the 54 datasets, using the latest CASA version at the time of writing" (2.2.1 Flux calibration accuracy)
   - software: CASA
   - parameter: Original CASA 4.1 to 5.4.0-68; recheck with CASA 5.6.1-8  
  > "i.e. the same version applied during the original calibration (CASA 4.1 to 5.4.0-68)" (2.2 Data reduction)
   - assumption: 10% flux calibration accuracy  
  > "yielded no flux level changes beyond 10%, which is the usually reported calibration accuracy value" (2.2.1 Flux calibration accuracy)
   - fitting: _not stated_
   - validation: Recalibrated Ceres/Pallas datasets lost on average 15% flux; the rerun showed no further flux changes beyond 10%  
  > "with the mean flux level reduction of 15% for these nine datasets" (2.2.1 Flux calibration accuracy); "yielded no flux level changes beyond 10%" (2.2.1 Flux calibration accuracy)
2. **image each source and cycle, subtract continuum, make [C II] maps**: tclean per source/cycle (Högbom, robust 0.5, 30 MHz channels), uvcontsub continuum subtraction, [C II] intensity map from channels over 1.2xFWHM  
  > "We imaged the calibrated visibilities, using the CASA task tclean, with the Högbom deconvolver, and a channel spacing of 30 MHz" (2.2.2 Data products per galaxy); "chosen to optimize the signal-to-noise ratio (S/N)" (2.2.2 Data products per galaxy)
   - software: CASA, tclean, uvcontsub
   - parameter: robust = 0.5; clean to 2 sigma within 2 arcsec radius mask  
  > "(robust = 0.5) and cleaned (deconvolved) the maps down to" (2.2.2 Data products per galaxy)
   - parameter: uvcontsub with fitorder = 1, excluding 2.5xFWHM around the line  
  > "while allowing for a continuum slope (fitorder = 1)" (2.2.2 Data products per galaxy)
   - assumption: Gaussian line profile when correcting for the tails beyond 1.2xFWHM (factor 1.19)  
  > "assuming a Gaussian profile, by multiplying by 1.19" (3.1.1 Analysis in the image plane)
   - fitting: _not stated_
   - validation: Integration width of 1.2xFWHM derived analytically to maximise S/N of a Gaussian line  
  > "Therefore, the total integration width that optimizes the S/N of a Gaussian line is equal to" (Appendix: Optimizing Gaussian line detection)
3. **measure aperture fluxes with residual scaling and uv-plane diagnostics**: Circular-aperture fluxes from dirty, residual and clean-component maps with residual scaling; imfit 2D Gaussians in image plane; uvmodelfit and radially averaged visibility amplitudes in the uv-plane  
  > "To mitigate this issue we scale the flux collected from the residual map (cite: jorsater95; walter08; novak19)." (3.1.1 Analysis in the image plane); "we attempt to fit a 2D Gaussian in the $uv$-plane using the uvmodelfit task in CASA" (3.1.2 uv-plane analysis)
   - software: CASA, imfit, uvmodelfit
   - parameter: Corrected flux F = C + eps R = eps D, eps = C/(D-R) in the aperture  
  > "Corrected flux inside an aperture can be obtained as $F_{\mathrm{correct}}=C +\epsilon R=\epsilon D$, where $\epsilon= C/(D-R)$ is the clean-to-dirty beam area ratio defined inside a specific aperture" (3.1.1 Analysis in the image plane)
   - parameter: Aperture error approximated by rms x sqrt(N beams)  
  > "The error on the aperture flux can be approximated by $\mathrm{rms}\times \sqrt{N}$, where $N$ is the number of beams contained inside the aperture" (3.1.1 Analysis in the image plane)
   - assumption: Apertures chosen manually at the radius where the curve of growth flattens  
  > "Aperture sizes for individual sources were chosen manually (after visual inspection) to be at a radius where the curve of growth begins to flatten" (3.1.3 Comparing flux measurements)
   - fitting: imfit 2D Gaussian limited to a 2 arcsec radius circle; uvmodelfit with no additional constraints  
  > "apply no additional constraints to" (3.1.3 Comparing flux measurements)
   - validation: Different methods agree within a factor of two; natural and Briggs weighting give the same aperture fluxes after residual scaling  
  > "all of the measurements are consistent within a factor of two, and generally consistent within the errors" (3.1.3 Comparing flux measurements); "We note that we recover the same aperture flux densities in both natural and Briggs weighted maps using the residual scaling method explained in a later section." (Footnote 11)
4. **extract aperture spectra and stack them in velocity/sigma_line units**: Residual-scaled aperture flux per channel, Gaussian plus constant fit, spectra rescaled by line width, constant continuum subtracted, stacked without weights  
  > "we apply residual scaling on the aperture flux densities obtained from individual channels before a spectrum is extracted" (3.2.1 Extracting aperture spectra); "it is necessary to rescale the spectra by their respective widths before stacking" (3.2.2 Stacking spectra); "No additional weights to individual spectra are applied." (3.2.2 Stacking spectra)
   - software: CASA
   - parameter: Average sigma_line of 150 km/s  
  > "which has an average value of 150" (3.2.2 Stacking spectra)
   - assumption: Continuum flat within the bandwidth of interest  
  > "where we consider the underlying continuum to be flat, within the bandwidth of interest" (3.2.2 Stacking spectra)
   - fitting: Single Gaussian plus constant  
  > "estimated from the fitting of a Gaussian plus constant profile" (3.2.2 Stacking spectra)
   - validation: Residual after Gaussian subtraction consistent with noise; two different continuum estimation methods mitigate bias  
  > "is consistent with pure noise. There is no indication of an additional broad spectral component." (3.2.1 Extracting aperture spectra); "Having two different methods of continuum estimation largely mitigates any potential bias of subtracting a broad component as continuum." (3.2.2 Stacking spectra)
5. **prepare and image the uv-stacked data**: Split channels from continuum-subtracted visibilities, time-average to 30 s, set ICRS, phase-shift to the [C II] centroid with fixvis, recompute weights with statwt, then tclean (mfs, multi-scale) all sources together; each velocity bin imaged separately and joined with ia.imageconcat  
  > "The data was further time-averaged inside 30 s bins to reduce the data volume" (2.2.3 Stacking the data in the uv-plane); "emission using the task fixvis" (2.2.3 Stacking the data in the uv-plane); "Finally, the data weights were recomputed with the statwt task using the same time and channels bin for all of the datasets." (2.2.3 Stacking the data in the uv-plane); "These separately imaged velocity bin slices were further joined into a single cube using the CASA toolkit task ia.imageconcat." (2.2.3 Stacking the data in the uv-plane)
   - software: CASA, tclean, fixvis, statwt, im.advisechansel, ia.imageconcat
   - parameter: specmode = mfs; multi-scale scales 0, 1, 3, 5, 10 beams; 2 arcsec radius mask to 2 sigma  
  > "We imaged the data in the continuum mode (specmode = mfs) and applied the multi-scale deconvolver" (2.2.3 Stacking the data in the uv-plane)
   - parameter: Velocity bins of fixed 30 km/s or 0.2 sigma_line; channels chosen with im.advisechansel in LSRK, nearest neighbour  
  > "The velocity bin was either of fixed size, i.e. 30" (2.2.3 Stacking the data in the uv-plane); "We used the function im.advisechansel from the CASA toolkit to select the channels of interest in the kinematic local standard of rest frame (LSRK)." (2.2.3 Stacking the data in the uv-plane)
   - assumption: Recomputed weights comparable across datasets so no single source dominates the average  
  > "We manually checked that the ranges of recomputed weights are similar between all datasets" (2.2.3 Stacking the data in the uv-plane)
   - fitting: _not stated_
   - validation: Anomalous-weight datasets removed; continuum exclusion width tested with a much broader 8xFWHM exclusion  
  > "Several anomalous datasets were identified as having (at least) an order of magnitude larger data weights" (2.2.3 Stacking the data in the uv-plane); "We validated that our choice of excluded frequencies/velocities did not bias the dust continuum results by re-imaging the data, this time excluding a much broader bandwidth of" (2.2.3 Stacking the data in the uv-plane)
6. **measure spatial extent of stacked [C II] and dust emission**: Curve of growth and azimuthally averaged surface brightness profile of the uv-stacked [C II] map and continuum map (clean sample); half-light radius at 50% of flux at 10 kpc; exponential fit to the extended component  
  > "We report a simple one parameter size estimate, the half-light radius, defined as the radius where the curve of growth equals to 50% of the value at 10 kpc" (4.1 Spatial extent of the [C II] emission); "The azimuthally-averaged profile measured in the cleaned map (red line) indicates the presence of two components of emission" (4.1 Spatial extent of the [C II] emission)
   - software: CASA, uvmultifit
   - parameter: No residual scaling used for the profile; mean pixel value in annuli, since corrections are negligible  
  > "Here, we did not perform any residual scaling, but instead calculated the mean value of pixels within some annulus, as the corrections are negligible." (4.1 Spatial extent of the [C II] emission)
   - assumption: Extended component described by an exponential function  
  > "is well described by an exponential function with a scale length of 2 kpc" (4.1 Spatial extent of the [C II] emission)
   - fitting: Direct uv-plane fit with uvmultifit of two radially symmetric exponential components (4 free parameters each: two offsets, flux, major axis FWHM) to the clean uv-stack, binned in 5 klambda; priors/sampler not stated  
  > "using the software package uvmultifit" (Appendix: Fitting the stacked data in the uv-plane)
   - validation: Re-imaged without multi-scale (delta functions only), uv-plane fits, and several subsamples all give consistent profiles  
  > "We ascertained to what extent the multi-scale cleaning algorithm may bias the shape of the profile by repeating the imaging process with a different and simpler algorithm." (4.1 Spatial extent of the [C II] emission)
7. **search the stacked spectrum for a broad (outflow) component**: uv-stacked cube of the clean (and full) sample in 0.2 sigma_line slices; 2 arcsec aperture and single-beam spectra fit with one Gaussian; residuals inspected; wings map stacked between 3 and 6 sigma_line; upper limit from wings rms  
  > "radius aperture spectrum (residual corrected) from the" (4.3 High-velocity outflows); "we performed a single beam (i.e. single pixel) measurement at the central" (4.3 High-velocity outflows); "If a broad spectral component were to exist, its S/N would be maximized in such a map" (4.3 High-velocity outflows)
   - software: CASA
   - parameter: 100 slices of 0.2 sigma_line covering +-10 sigma_line; sigma_line = 150 km/s  
  > "There are 100 such slices, covering velocities between" (4.3 High-velocity outflows)
   - assumption: 3 sigma upper limit derived from the wings-map rms and its bandwidth  
  > "By taking the rms level of the wings map, and its bandwidth, we estimate a" (4.3 High-velocity outflows)
   - fitting: Single Gaussian fit to stacked spectrum (also two-Gaussian test on aperture stack); sampler/priors not stated  
  > "Fitting two Gaussians would collect marginally more emission" (4.3 High-velocity outflows)
   - validation: Repeated on the full uv-stacking sample; annulus 1-2 arcsec spectrum equivalent; stacks without line width normalisation reproduced as artifact  
  > "To be certain that we have not missed any fainter, more extended emission, we repeated the analysis on the full" (4.3 High-velocity outflows)
8. **compare extended dust profile with MassiveFIRE simulation**: Stack predicted 1.2 mm ALMA maps of simulated galaxies and average in radial annuli; compare with observed profiles  
  > "We calculate the radial profile of the sub-mm emission by stacking the predicted 1.2 mm ALMA flux density maps of five simulated galaxies, each viewed from 18 random directions, and by averaging the flux densities in radial annuli." (5.2 Dust emission from the MassiveFIRE simulation)
   - software: SKIRT
   - parameter: Simulated halos of (2-6)x10^12 Msun, SFR 70-400 Msun/yr, total IR luminosity ~1e12 Lsun matched to the sample  
  > "These simulated galaxies reside in halos with virial masses of" (5.2 Dust emission from the MassiveFIRE simulation)
   - assumption: SMBH feedback does not severely affect the host at radii beyond 2 kpc; simulated galaxies matched in FIR luminosity only  
  > "assuming that the feedback from the central SMBH does not severely affect the host (gas and dust) at radii beyond 2 kpc" (5.2 Dust emission from the MassiveFIRE simulation)
   - fitting: _not stated_
   - validation: Simulated profile follows the observed dust and [C II] profile beyond 2 kpc; core differs, attributed to selection bias  
  > "The radial dust profile of the stacked MassiveFIRE galaxies closely follows the radial profile of the dust and" (5.2 Dust emission from the MassiveFIRE simulation)

## Software

- **CASA** 4.1 to 5.4.0-68 (original calibration); 5.6.1-8 (recheck): Calibration, imaging (tclean), continuum subtraction (uvcontsub), uv-stack preparation and analysis  
  > "the same version applied during the original calibration (CASA 4.1 to 5.4.0-68)" (2.2 Data reduction)
- **tclean** : Imaging of per-source cubes/maps and of uv-stacks  
  > "We imaged the split, renormalized and re-centered data using the CASA task tclean" (2.2.3 Stacking the data in the uv-plane)
- **uvcontsub** : Continuum subtraction in the uv-plane with a first-order fit  
  > "performed the continuum subtraction using the uvcontsub task on the two spectral windows around the" (2.2.2 Data products per galaxy)
- **fixvis** : Phase-shifting visibilities to the [C II] centroid  
  > "emission using the task fixvis" (2.2.3 Stacking the data in the uv-plane)
- **statwt** : Recomputing data weights before stacking  
  > "the data weights were recomputed with the statwt task" (2.2.3 Stacking the data in the uv-plane)
- **im.advisechansel** : Selecting channels of interest in LSRK  
  > "We used the function im.advisechansel from the CASA toolkit to select the channels of interest" (2.2.3 Stacking the data in the uv-plane)
- **ia.imageconcat** : Joining velocity-bin images into a cube  
  > "joined into a single cube using the CASA toolkit task ia.imageconcat" (2.2.3 Stacking the data in the uv-plane)
- **imfit** : 2D Gaussian fits to source in the image plane  
  > "We do so by employing the imfit task included in CASA." (3.1.1 Analysis in the image plane)
- **uvmodelfit** : 2D Gaussian fit to visibilities in the uv-plane  
  > "using the uvmodelfit task in CASA" (3.1.2 uv-plane analysis)
- **uvmultifit** : Fitting two exponential components to the uv-stacked data  
  > "using the software package uvmultifit" (Appendix: Fitting the stacked data in the uv-plane)
- **SKIRT** : Dust radiative transfer post-processing of MassiveFIRE galaxies  
  > "calculated in post-processing via self-consistent dust radiative transfer calculations with the help of SKIRT" (5.2 Dust emission from the MassiveFIRE simulation)
- **Astropy** : _not stated_
- **Matplotlib** : _not stated_
- **Topcat** : _not stated_

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| [C II] half-light radius of the uv-stacked clean sample | 1.6 | 0.1 | kpc | 6 | The $\text{\textsc{[C ii]}}$ emission half-light radius is $1.6 \pm 0.1$ kpc |
| Dust continuum half-light radius of the uv-stacked clean sample | 0.86 | 0.03 | kpc | 6 | The dust continuum half-light radius, defined as in the previous section, is $0.86 \pm 0.03$ kpc |
| Cumulative [C II] flux of the stack at saturation (10 kpc) | 2.5 | 0.1 | Jy km/s | 6 | The value at which the cumulative flux saturates ($2.5\pm0.1$ $\text{Jy\,km\,s}^{-1}$) |
| Stacked dust continuum flux density | 2.05 | 0.07 | mJy | 6 | The final value of $2.05 \pm 0.07$ mJy is consistent with the mean of individual continuum measurements (cite: venemans20) |
| Fraction of stacked [C II] flux within 2, 3, 4, 5, 10 kpc | 55%, 65%, 75%, 80%, 100% | not stated | dimensionless | 6 | the region within 2, 3, 4, 5 and 10 kpc contains 55%, 65%, 75%, 80% and 100% of the flux, respectively |
| Fraction of stacked dust continuum flux within 2, 3, 4, 5, 10 kpc | 75%, 80%, 85%, 90%, 100% | not stated | dimensionless | 6 | the emission contained within 2, 3, 4, 5 and 10 kpc corresponds to 75%, 80%, 85%, 90% and 100% of the total, respectively |
| Exponential scale length of the extended [C II] component (image plane) | 2 | not stated | kpc | 6 | is well described by an exponential function with a scale length of 2 kpc |
| uv-plane fit, compact [C II] component: flux and scale length | F = 2.8 mJy; l = 0.43 kpc | F +-0.1 mJy; l +-0.02 kpc | mJy; kpc | 6 | $F_{\ensuremath{\text{\textsc{[C ii]}}}}^{\mathrm{comp.}} = 2.8 \pm 0.1$ mJy with $l=0.43 \pm 0.02$ kpc |
| uv-plane fit, extended [C II] component: flux and scale length | F = 3.4 mJy; l = 2.6 kpc | F +-0.2 mJy; l +-0.2 kpc | mJy; kpc | 6 | $F_{\ensuremath{\text{\textsc{[C ii]}}}}^{\mathrm{ext.}} = 3.4 \pm 0.2$ mJy with $l=2.6 \pm 0.2$ kpc |
| uv-plane fit, compact dust component: flux and scale length | F = 1.19 mJy; l = 0.20 kpc | F +-0.03 mJy; l +-0.01 kpc | mJy; kpc | 6 | $F_{\mathrm{dust}}^{\mathrm{comp.}} = 1.19 \pm 0.03$ mJy with $l=0.20 \pm 0.01$ kpc |
| uv-plane fit, extended dust component: flux and scale length | F = 0.76 mJy; l = 1.3 kpc | F +-0.03 mJy; l +-0.1 kpc | mJy; kpc | 6 | $F_{\mathrm{dust}}^{\mathrm{ext.}} = 0.76 \pm 0.03$ mJy with $l=1.3 \pm 0.1$ kpc |
| Peak S/N of the stacked aperture [C II] spectrum in 0.2 sigma_line bins | 32 | not stated | dimensionless | 4 | is detected at a S/N of 32 in velocity bins of |
| [C II] flux in single Gaussian fit to the uv-stacked spectrum (sigma_line = 150 km/s) | 2.9 | 0.1 | Jy km/s | 7 | is equal to $2.9 \pm 0.1\,\ensuremath{\text{Jy\,km\,s}^{-1}}$ |
| rms noise per 0.2 sigma_line channel in the uv-stack (clean sample, within +-6 sigma_line) | 60 | not stated | uJy/beam | 7 | The rms noise in the velocity range between $\pm6\sigma_{\mathrm{line}}$ is 60 $\mu\mathrm{Jy}\,\mathrm{beam}^{-1}$ per channel of $0.2\sigma_{\mathrm{line}}$ |
| rms noise of the wings map (+-3 to 6 sigma_line, clean sample) | 10.8 | not stated | uJy/beam | 7 | This map has an rms noise level of $10.8\,\ensuremath{\mu\mathrm{Jy}\,\mathrm{beam}^{-1}}$ |
| 3 sigma upper limit on outflow flux in the core (single ~1 kpc beam) | 0.03 (<5% of core peak emission) | not stated | Jy km/s | 7 | we estimate a $3\sigma$ upper limit on the outflow in the very core (single $\sim1$ kpc beam) of 0.03 $\text{Jy\,km\,s}^{-1}$ |
| Fraction of observed [C II] emission collected by a single Gaussian | 99% | not stated | dimensionless | 7 | A single Gaussian collects 99% of the observed emission, based on the cumulative flux integral. |
| Mean flux reduction after recalibrating the nine Ceres/Pallas datasets | 15% | not stated | dimensionless | 1 | with the mean flux level reduction of 15% for these nine datasets |

## Qualitative findings

- Both [C II] and dust continuum surface brightness profiles show a steep central component plus a shallower extended exponential component detected to ~10 kpc  
  > "can be described by a steep component within a radius of 2 kpc, and a shallower component with a scale length of 2 kpc, detected up to" (abstract)
- No broad [C II] component indicative of outflows in the stacked spectra; the stacked line is a single Gaussian  
  > "Imaging a wider velocity range, where the broad feature may be expected, also yielded a non-detection." (5.3 Outflows)
- Stacking without line-width normalisation produces apparent broad wings that the authors attribute at least in part to adding Gaussians of different widths  
  > "However, from the shape of the residual, we argue that this is, at least in part, an artifact resulting from the linear addition of Gaussians with various widths." (5.3 Outflows)

## Claim tuples

- H: High-z quasar host galaxies have extended [C II] and dust emission (halos) beyond the central region | E: uv-plane stacking of the 19-host clean sample (32 datasets) in [C II] and continuum, curves of growth and surface brightness profiles | R: Half-light radii 1.6 kpc ([C II]) and 0.86 kpc (dust) with an extended exponential component (scale length 2 kpc) out to ~10 kpc | F: Extended emission is the host ISM; no extra halo component needed | **supported**
- H: [C II] shows broad high-velocity wings indicating quasar-driven outflows | E: Aperture-spectrum stacking and spectral uv-stacking in 0.2 sigma_line bins, single-beam and aperture spectra, wings map, clean and full samples | R: Single Gaussian describes the stack; residuals consistent with noise; wings map consistent with noise; 3 sigma core limit 0.03 Jy km/s | F: High-velocity outflows are atypical in z>6 quasar hosts, though very faint outflows cannot be excluded | **supported**
- H: The extended dust emission follows the [C II] extended emission and arises from star-forming ISM | E: Compare stacked dust and [C II] profiles with a stack of MassiveFIRE simulated 1.2 mm maps of galaxies with similar IR luminosity | R: Extended components have equivalent profiles; simulated dust profile matches the observed profile beyond 2 kpc, core differs | F: Extended emission is part of the main galaxy ISM powered by star formation | **supported**
- H: Earlier reports of broad [C II] components in stacks (e.g. Bischetti et al. 2019) reflect real outflows | E: Re-stack without line-width normalisation and compare residual shape; compare continuum subtraction methods | R: Broad wings appear without normalisation (<4% flux excess); residual shape reproduced by averaging Gaussians of different widths | F: Part of the earlier signal is plausibly a stacking artifact; discrepancy not fully resolved (companions, continuum fit also possible) | **partially**

## Reasoning

- Why this data: High-resolution (~1 kpc) data needed for surface brightness profiles, complemented with lower-resolution archival data to limit missing flux and out-resolving  
  > "but complement our data with lower spatial resolution observations of the same sources to minimize potential issues of missing flux and outresolving sources" (Introduction)
- Why this method: uv-plane stacking avoids dirty-beam residuals and beam matching problems of image-based stacking  
  > "we circumvent various problems present in interferometric image-based stacking (e.g. dirty beam residuals and beam matching)" (Introduction)
- Alternative: Image-plane 2D Gaussian fitting rejected for extended emission; image-plane stacking avoided in favour of uv-stacking; cycle 0 data and sub-kpc data for two hosts excluded  
  > "For this reason we refrain from fitting 2D Gaussians in the image plane in the remainder of the paper." (3.1.3 Comparing flux measurements); "We have excluded cycle 0 data from our selection to avoid possibly lower quality data" (2.1 New and archival ALMA data)
- How they decided it was enough: _not stated_
- Limitation (authors): A very faint outflow below the stack detection limit cannot be ruled out  
  > "However, we cannot rule out the possibility of a very faint outflow, below our stack detection limit." (4.3 High-velocity outflows)
- Limitation (authors): Stack is meaningful only if the mean property is well defined; sub-kpc morphology not recoverable  
  > "which we cannot know a priori, and deeper observations are necessary to confirm any potential structure in individual objects" (2.2.3 Stacking the data in the uv-plane); "Morphological details on sub-kpc scales cannot be recovered with these observations." (2.3 Mergers and companions)
- Limitation (authors): Simulated galaxies and observed quasar hosts are not the same population (core differs)  
  > "Although the simulations and observations do not pertain to the same population of galaxies" (5.2 Dust emission from the MassiveFIRE simulation)
- Caveat (inferred, ours): Stack depends on manually chosen aperture sizes and on the normalisation by sigma_line, which could suppress real broad components
- Caveat (inferred, ours): Continuum subtraction trade-off (excluded ~900 km/s) can absorb or hide a broad component; authors admit this is the weak link
- Caveat (inferred, ours): Mean profile hides source-to-source variation; a few bright hosts may dominate the extended wings
- Caveat (inferred, ours): MassiveFIRE comparison uses only 5 galaxies matched in LIR and has no AGN feedback
- Caveat (inferred, ours): Selection of 'clean' sample by visual merger/companion classification is subjective

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Robust weighting, cell size, image size, primary-beam correction and clean iterations for the uv-stack tclean runs
- Missing: Per-source aperture radii and line-free channel ranges
- Missing: Exact dataset list per sample (only footnote markers in Table 1) and per-dataset CASA versions
- Missing: No analysis code released or referenced
- Missing: MassiveFIRE/SKIRT simulation maps are from other work and not provided
- Data volume (inferred): 54 12 m/7 m execution blocks over 27 sources and ~34 h on source; likely several hundred GB of raw data (order 0.5-1 TB), less if only calibrated target spectral windows are kept
- Score (inferred): 3/5, Scale 1-5. Data and the multi-step recipe (uv-stacking, residual scaling, profile measurement) are described in good detail with quoted numbers, but many tclean and aperture settings are unstated and the heavy data volume plus inherited choices from companion papers make exact reproduction hard.
- Rediscovery candidate: yes, ALMA data of cycles 1-6 for the 13 listed projects are known to be public in the archive; the recipe is mostly complete and results (half-light radii, fluxes, rms, outflow limit) are numeric, though reproduction is data-heavy.

## Links

- Method: (cite: fujimoto19) (uv-stacking method adapted and extended to the whole spectrum)
- Method: (cite: jorsater95; walter08; novak19) (residual scaling of aperture fluxes)
- Method: (cite: venemans20) (data products, sample description and individual-source analysis)
- Companion: (cite: venemans20) (First paper of the series: sample and individual [C II] and dust analysis)
- Companion: (cite: neeleman20b) (Second paper of the series: kinematic modeling and dynamical masses)
- Companion: (cite: decarli18) (Earlier [C II] stack of 23 quasar hosts finding no outflow)
- Companion: (cite: bischetti19) (Stack reporting a broad [C II] component, in tension with this work)
- Companion: (cite: stanley19) (Stack of 26 hosts with marginal broad component; flagged Ceres/Pallas recalibration)
- Related: 2017.1.01301.S
- Related: 2018.1.00908.S
- Related: MassiveFIRE
- Related: FIRE

## Checks

```json
{
 "quotes": 173,
 "quotes_ok": 173,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 13,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 18,
 "numeric_problems": 0,
 "fill": {
  "facts": 121,
  "stated": 93,
  "rate": 0.769
 },
 "evidence_ok": true
}
```
