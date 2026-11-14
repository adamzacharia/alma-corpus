# A CO Survey of SpARCS Star-forming Brightest Cluster Galaxies: Evidence for Uniformity in BCG Molecular Gas Processing across Cosmic Time

`2021ApJ...909L..29D` | The Astrophysical Journal Letters 2021 | first author: Dunne, Delaney A. | arXiv: 2103.02463 | DOI: 10.3847/2041-8213/abeb6f

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: galaxy_clusters_and_sz, high_z_galaxies
- Question: How common is molecular gas in star-forming SpARCS BCGs at 0.2<z<1.2, and do their gas mass versus sSFR correlations match those of low-redshift cooling-flow BCGs  
  > "We aim to constrain the processes driving BCG mass growth by studying molecular gas in a large sample of BCGs spanning 6 Gyr of cosmic time." (Introduction); "To test if similar correlations exist in BCGs, we compare the sSFRs and molecular gas masses of our sample to those BCGs detected by" (Direct comparison with lower-redshift BCGs)
- Target **30 SpARCS star-forming BCGs (24 CO detections, 6 non-detections; IDs XMM-CO1..8, ES1-CO1..10, CDFS-CO1..13)**: coordinates RA/Dec in degrees per source in the results table (not quoted here)  
  > "have a confirmed spectroscopic redshift from OzDES (the Australian Dark Energy Survey), taken using the AAOmega spectrograph and 2dF fibre positioner on the 4m Anglo-Australian Telescope" (Target Selection); "Three BCGs were not observed because of the ALMA COVID-19 shutdown." (Observations); z/distance 0.2<z<1.2 (OzDES spectroscopic redshifts, z_OzDES in table)  
  > "have a confirmed spectroscopic redshift from OzDES (the Australian Dark Energy Survey), taken using the AAOmega spectrograph and 2dF fibre positioner on the 4m Anglo-Australian Telescope" (Target Selection); "Three BCGs were not observed because of the ALMA COVID-19 shutdown." (Observations); distance from OzDES spectroscopic redshifts (AAT AAOmega); cosmology H0 = 70, Om = 0.3, OL = 0.7  
  > "have a confirmed spectroscopic redshift from OzDES (the Australian Dark Energy Survey), taken using the AAOmega spectrograph and 2dF fibre positioner on the 4m Anglo-Australian Telescope" (Target Selection); "Three BCGs were not observed because of the ALMA COVID-19 shutdown." (Observations)

## Data provenance

- ALMA projects: 2019.1.01529.S
- bands: Bands 3, 4 and 5  
  > "We used ALMA bands 3, 4, and 5 (chosen to measure the CO (2-1) line) and configurations C43-1, C43-2, and C43-3." (Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-1, C43-2, C43-3  
  > "We used ALMA bands 3, 4, and 5 (chosen to measure the CO (2-1) line) and configurations C43-1, C43-2, and C43-3." (Observations)
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: 3 sigma image RMS 1.2 mJy/beam (z~0.2) to 0.6 mJy/beam (z~1.2) over 100 km/s channels; designed for constant gas mass depth >= 1e10 Msun  
  > "resulting in 3$\sigma$ image RMS depths between 1.2 mJy/beam (z $\sim 0.2$) and 0.6 mJy/beam (z $\sim 1.2$) over 100 km/s channels." (Observations)
- time on source: 30 BCGs observed over a total of ~15 hours  
  > "30 BCGs were observed over a total of $\sim15$ hours." (Observations)
- observing dates: 22 November to 15 December 2019  
  > "between November 22 and December 15, 2019." (Observations)
- pi or archival as stated: PI program, P.I. Webb  
  > "Program ID 2019.1.01529.S, P.I. Webb" (Observations)
- Line: CO J=2-1 (not stated)
- Other facility **OzDES (AAT AAOmega / 2dF)**: Spectroscopic redshifts of the BCGs, used for target selection and to centre stacks of non-detections  
  > "have a confirmed spectroscopic redshift from OzDES (the Australian Dark Energy Survey)" (Target Selection); "centering each around the expected position of the CO line using the OzDES redshifts." (CO (2-1) Molecular Gas Measurements)
- Other facility **Spitzer SWIRE (IRAC 3.6 um, MIPS 24 um)**: Photometry used for stellar masses (3.6 um) and SFRs (24 um); also used for target selection (>100 uJy at 24 um)  
  > "calculated from existing MIPS 24 $\mu$m and IRAC 3.6 $\mu$m fluxes, respectively." (abstract); "c) are IR-luminous ($>100\ \mu$Jy at $24 \ \mu$m) and therefore star-forming" (Target Selection)
- Other facility **SpARCS**: Parent cluster and BCG sample  
  > "The BCGs studied here are drawn from clusters in the Spitzer Adaptation of the Red Sequence Cluster Survey (SpARCS;" (The Parent SpARCS Sample)
- Other facility **Dark Energy Survey (griz photometry)**: Public archival DES data used with 3.6/4.5 um photometry in a FAST SED fit to calibrate the mass-to-light ratio  
  > "This project used public archival data from the Dark Energy Survey (DES)." (Acknowledgments); "SED fit using FAST (cite: kriek2018FAST)" (Stellar Masses and Star Formation Rates)
- External data: Molecular gas masses of the low-redshift Edge BCG comparison sample (corrected to H0 = 70)  
  > "We take the molecular gas masses from (cite: edge2001detection), correcting the values for" (A Low-Redshift BCG Comparison Sample) [from (cite: edge2001detection)]
- External data: 3.6 um fluxes for the Edge sample  
  > "We take 3.6 $\mu$m flux values from (cite: quillen2008infrared), (cite: Yamagishi_2010), and (cite: landt_2010))" (A Low-Redshift BCG Comparison Sample) [from (cite: quillen2008infrared); (cite: Yamagishi_2010); (cite: landt_2010)]
- External data: MIPS 24 um photometry for the Edge sample  
  > "(cite: shi_2005), and the Spitzer Science Source List" (A Low-Redshift BCG Comparison Sample) [from (cite: quillen2008infrared); (cite: Yamagishi_2010); (cite: shi_2005); (cite: 2010ASPC..434..437T)]
- External data: Halo masses of the Edge BCGs based on SDSS DR7  
  > "and halo masses based on SDSS DR7 ((cite: popesso2020_edgemcluster); (cite: yang2005galaxy)) for the (cite: edge2001detection) BCGs." (Discussion) [from (cite: popesso2020_edgemcluster); (cite: yang2005galaxy)]
- External data: Non-BCG cluster galaxy gas masses used in the comparison figure  
  > "Non-BCG cluster galaxies are taken from (cite: noble2019_clustergalmgas), (cite: noble_2017) and (cite: Jablonka_2013)." (footnote 2) [from (cite: noble2019_clustergalmgas); (cite: noble_2017); (cite: Jablonka_2013)]
- External data: SED template for K-correction (11 Gyr SSP, solar metallicity, Salpeter IMF)  
  > "We use an SED template from (cite: bruzual2003stellar) to calculate the" (Stellar Masses and Star Formation Rates) [from (cite: bruzual2003stellar)]
- External data: ALMA nominal flux density calibration uncertainty  
  > "The nominal flux density calibration uncertainty for ALMA sources in these bands is" (Observations) [from (cite: remijan2019alma)]

## Processing

### Calibration

- pipeline or manual: ALMA reduction pipeline scripts  
  > "Data were calibrated using ALMA reduction pipeline scripts in CASA version 5.4.0." (Observations)
- casa version: CASA 5.4.0  
  > "Data were calibrated using ALMA reduction pipeline scripts in CASA version 5.4.0." (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ~5-10% nominal  
  > "The nominal flux density calibration uncertainty for ALMA sources in these bands is $\sim 5 - 10\%$" (Observations)
- self calibration: _not stated_

### Imaging

- task: image cubes cleaned minimally (task name not given)  
  > "We cleaned the image cubes minimally with natural weighting and pixel sizes between" (Observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "We cleaned the image cubes minimally with natural weighting and pixel sizes between" (Observations)
- uv taper: _not stated_
- cell size: 0.2 to 0.4 arcsec pixels  
  > "pixel sizes between 0.2$''$ and 0.4$''$" (Observations)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: images are continuum-subtracted (method not given)  
  > "resulting in continuum-subtracted and primary beam-corrected images with" (Observations)
- line free channels: _not stated_
- primary beam correction: primary beam-corrected images  
  > "resulting in continuum-subtracted and primary beam-corrected images with" (Observations)
- array combination: _not stated_
- smoothing: spectral resolution chosen per cube from the strength of the detection  
  > "We chose the spectral resolution of each image cube individually, based on the strength of the detection." (Observations)
- final beam: _not stated_
- final rms: 3 sigma RMS 1.2 mJy/beam (z~0.2) to 0.6 mJy/beam (z~1.2) over 100 km/s channels  
  > "resulting in 3$\sigma$ image RMS depths between 1.2 mJy/beam (z $\sim 0.2$) and 0.6 mJy/beam (z $\sim 1.2$) over 100 km/s channels." (Observations)

### Inherited from earlier work

- CO line flux converted to CO luminosity with Solomon & Vanden Bout equation 3  
  > "we convert this flux to a CO luminosity using (cite: solomon2005molecular) Equation 3." (CO (2-1) Molecular Gas Measurements) [from (cite: solomon2005molecular) Equation 3]
- SFR from 24 um using Kennicutt (1998) equation 4 with L(24) from Chary & Elbaz  
  > "using (cite: kennicutt1998_SFR) Equation 4 based on the luminosity at" (Stellar Masses and Star Formation Rates) [from (cite: kennicutt1998_SFR); (cite: chary2001interpreting)]
- AGN identification with the IRAC colour wedge criteria  
  > "to the criteria described in (cite: Donley_2012)." (AGN Contamination) [from (cite: Donley_2012)]
- Stellar mass K-correction with a Bruzual & Charlot SED template  
  > "We use an SED template from (cite: bruzual2003stellar) to calculate the" (Stellar Masses and Star Formation Rates) [from (cite: bruzual2003stellar)]
- Galactic alpha_CO and r21 adopted as typical of Main Sequence galaxies  
  > "as these are typical of galaxies on the star-forming Main Sequence (ex. (cite: solomon1997molecular); (cite: freundlich2019phibss2))" (CO (2-1) Molecular Gas Measurements) [from (cite: solomon1997molecular); (cite: freundlich2019phibss2)]

### Not stated but needed to reproduce (our reading)

- tclean/clean parameters: niter, threshold, masking, spectral channel width per source (only an unlabeled table column), and whether imaging used the pipeline cubes or custom runs
- Method and line-free channels used for continuum subtraction (uvcontsub or image-plane)
- Flux, bandpass and phase calibrators and any manual flagging beyond the pipeline
- Pipeline version and whether the archive pipeline products were used as delivered
- CO (2-1) rest frequency and how the observed-frame line frequency was set per source
- How the 2 sigma channel selection for the Moment-0 map is defined (mean and sigma of the first Gaussian fit) and the exact noise/significance definition for the 3 sigma detection
- Which table columns are channel width, beam size and noise (column headers are partly blank), needed to reproduce the per-source cubes
- Details of the FAST SED fit (templates, grid, photometry) and how the 0.83 mass-to-light factor and the 'FAST conversion factor' applied to the Edge SFRs are applied
- ODR implementation and how the 1 sigma confidence regions of the fits are computed
- No code or measured spectra released

## Analysis recipe

1. **calibrate and image the CO cubes**: ALMA pipeline calibration in CASA, then minimally cleaned natural-weighted cubes, continuum-subtracted and primary-beam corrected  
  > "Data were calibrated using ALMA reduction pipeline scripts in CASA version 5.4.0." (Observations); "We cleaned the image cubes minimally with natural weighting and pixel sizes between" (Observations)
   - software: CASA 5.4.0
   - parameter: pixel size 0.2 to 0.4 arcsec; spectral resolution chosen per source from detection strength  
  > "We chose the spectral resolution of each image cube individually, based on the strength of the detection." (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **first-pass spectra and Gaussian fit**: Extract spectrum from an elliptical aperture at the BCG centre, twice the synthesized beam axes and with the same orientation  
  > "we generate first-pass spectral profiles by placing an elliptical aperture with semi-major and semi-minor axes twice as large as those of the synthesized beam, and at the same orientation, at the center of each BCG." (CO (2-1) Molecular Gas Measurements)
   - fitting: single one-dimensional Gaussian  
  > "Spectra are fit with a single one-dimensional Gaussian profile." (CO (2-1) Molecular Gas Measurements)
   - validation: _not stated_
3. **build Moment-0 map and fit its spatial extent**: Collapse cube over channels with significant emission from the first Gaussian fit, then fit a 2D elliptical Gaussian  
  > "We keep channels within 2$\sigma$ (2 standard deviations) of the mean." (CO (2-1) Molecular Gas Measurements); "We then fit potential signal in the Moment-0 map to a two-dimensional, elliptical Gaussian profile." (CO (2-1) Molecular Gas Measurements)
   - parameter: channels kept within 2 sigma of the mean of the Gaussian fit  
  > "We keep channels within 2$\sigma$ (2 standard deviations) of the mean." (CO (2-1) Molecular Gas Measurements)
   - fitting: 2D elliptical Gaussian to Moment-0 map  
  > "We then fit potential signal in the Moment-0 map to a two-dimensional, elliptical Gaussian profile." (CO (2-1) Molecular Gas Measurements)
   - validation: _not stated_
4. **extract final spectra, fit line flux and derive gas masses**: Second-pass spectrum from an elliptical aperture with axes three times the 2D Gaussian FWHM, fit with single or double Gaussian; line flux converted to CO luminosity and gas mass  
  > "we create a second one-dimensional spectral profile, extracted from an elliptical aperture with the parameters of the two-dimensional fitted profile; the new axis sizes are now three times the Gaussian full width at half maximum (FWHM)." (CO (2-1) Molecular Gas Measurements); "we convert this flux to a CO luminosity using (cite: solomon2005molecular) Equation 3." (CO (2-1) Molecular Gas Measurements)
   - parameter: aperture axes = 3 x Gaussian FWHM; line flux = area under the fit  
  > "We take the area under this fit as the total line flux" (CO (2-1) Molecular Gas Measurements)
   - assumption: alpha_CO = 4.36 and r21 = 0.8 (Galactic values)  
  > "We use galactic CO-to-$\mathrm{H}_2$ conversion factors ($\alpha_{CO}=4.36\ M_\odot (\mathrm{K}\ \mathrm{km}\ \mathrm{s}^{-1}\mathrm{pc}^2)^{-1}$, $r_{21}=0.8$)" (CO (2-1) Molecular Gas Measurements)
   - fitting: Least-squares Gaussian fits, single or double peak chosen by reduced chi-squared; uncertainty per flux value is the RMS noise in line-free channels  
  > "by fitting the second-pass spectral profile to either single- or double-peaked Gaussians, depending on which gives the better fit according to its reduced" (CO (2-1) Molecular Gas Measurements); "of the spectral profile as the uncertainty in each flux value, and account for it while performing the least-squares Gaussian fits." (CO (2-1) Molecular Gas Measurements)
   - validation: Alternative alpha_CO (ULIRG-like) does not change the results  
  > "does not affect the results of this paper." (CO (2-1) Molecular Gas Measurements)
5. **stack and set limits for non-detections**: Stack spectra of the 6 non-detections centred on OzDES redshifts; upper limits from collapsing cubes over the mean detected FWHM and taking the 3 sigma RMS  
  > "We also search for CO emission in our 6 non-detections by stacking their spectra" (CO (2-1) Molecular Gas Measurements); "and taking the $3\sigma$ RMS value as an upper limit to the flux." (CO (2-1) Molecular Gas Measurements)
   - parameter: collapse bandwidth = 356 km/s (mean FWHM of detected peaks)  
  > "by collapsing the image cubes over a bandwidth equivalent to the average FWHM of the detected CO peaks ($356\ \mathrm{km}\ \mathrm{s}^{-1}$)" (CO (2-1) Molecular Gas Measurements)
   - fitting: _not stated_
   - validation: Stack shows no significant emission down to 3 sigma  
  > "The stack shows no significant emission, down to 3$\sigma$." (CO (2-1) Molecular Gas Measurements)
6. **derive stellar masses and SFRs**: Stellar mass from IRAC 3.6 um rest-frame K-band luminosity with a template K-correction and a calibrated mass-to-light ratio; SFR from MIPS 24 um luminosity using Kennicutt (1998) eq. 4  
  > "We determine a mass-to-light ratio of 0.83 by comparing our sample of" (Stellar Masses and Star Formation Rates); "using (cite: kennicutt1998_SFR) Equation 4 based on the luminosity at" (Stellar Masses and Star Formation Rates)
   - software: FAST
   - parameter: mass-to-light ratio 0.83; stellar mass uncertainty 0.3 dex; SFR uncertainty 0.15 dex  
  > "We take the scatter in this relation (0.3 dex) as the uncertainty in the stellar masses." (Stellar Masses and Star Formation Rates); "We take the scatter of 0.15 dex described in (cite: kennicutt1998_SFR) to be the uncertainty in the SFRs." (Stellar Masses and Star Formation Rates)
   - assumption: 11 Gyr simple stellar population, solar metallicity, Salpeter IMF  
  > "adopting an 11 Gyr simple stellar population with solar metallicity and a Salpeter Initial Mass Function (IMF;" (Stellar Masses and Star Formation Rates)
   - fitting: FAST SED fit to griz/3.6/4.5 um photometry used to calibrate the mass-to-light ratio  
  > "SED fit using FAST (cite: kriek2018FAST)" (Stellar Masses and Star Formation Rates)
   - validation: Younger template changes mean stellar mass by at most 8%; more modern SFR method gives similar results  
  > "changes the average stellar mass values by at most 8%." (Stellar Masses and Star Formation Rates); "We achieve similar results with more modern SFR methods such as that of (cite: Rieke_2009)." (Stellar Masses and Star Formation Rates)
7. **build a homogeneous low-z comparison sample and remove AGN**: Recompute stellar masses and SFRs for the Edge BCGs with the same methods; flag AGN with the Donley IRAC wedge and exclude them from the analysis  
  > "We therefore calculate both stellar masses and SFRs for these BCGs using the methods outlined in" (A Low-Redshift BCG Comparison Sample); "we thus exclude them from all further analysis but continue to show them on plots." (AGN Contamination)
   - parameter: Donley AGN wedge criteria applied to IRAC colours  
  > "to the criteria described in (cite: Donley_2012)." (AGN Contamination)
   - fitting: _not stated_
   - validation: _not stated_
8. **compare the Mgas-sSFR correlation of the two BCG samples**: Fit a straight line to each sample separately in log space with orthogonal distance regression, restricted to the BCGs with z<0.6 for the main comparison  
  > "we fit a straight line to each sample separately in logarithmic space, using Orthogonal Distance Regression (ODR) to account for uncertainties existing in both axes." (Direct comparison with lower-redshift BCGs); "we first analyze only the BCGs in our sample with redshifts below 0.6 (left panel)." (Direct comparison with lower-redshift BCGs)
   - fitting: ODR straight-line fit in log space with 1 sigma confidence regions  
  > "We show fits, and their 1$\sigma$ confidence regions, in Figure" (Direct comparison with lower-redshift BCGs)
   - validation: Fits of the two samples compared by slope and offset; complete sample overplotted on the Edge fit  
  > "In the right panel of Figure [4](#fig:mgas_vs_ssfr), we plot the complete sample over all redshifts." (Direct comparison with lower-redshift BCGs)

## Software

- **CASA** 5.4.0: Calibration with ALMA pipeline scripts (and presumably imaging)  
  > "Data were calibrated using ALMA reduction pipeline scripts in CASA version 5.4.0." (Observations)
- **ALMA reduction pipeline scripts** : Calibration of the ALMA data  
  > "Data were calibrated using ALMA reduction pipeline scripts in CASA version 5.4.0." (Observations)
- **FAST** : SED fit to calibrate the 3.6 um mass-to-light ratio  
  > "SED fit using FAST (cite: kriek2018FAST)" (Stellar Masses and Star Formation Rates)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO detection rate | 24 of 30 pointings (80%) | not stated | dimensionless | 4 | in 24 of 30 pointings, or at a detection rate of 80%. |
| Molecular gas mass range of the BCGs | 0.7-11.0 x 10^10 | not stated | Msun | 4 | We find these galaxies have molecular gas masses of $0.7-11.0\times 10^{10}\ \mathrm{M}_\odot$ |
| 3 sigma image RMS depth at z~0.2 | 1.2 | not stated | mJy/beam (100 km/s channels) | 1 | 3$\sigma$ image RMS depths between 1.2 mJy/beam (z $\sim 0.2$) and 0.6 mJy/beam (z $\sim 1.2$) over 100 km/s channels. |
| 3 sigma image RMS depth at z~1.2 | 0.6 | not stated | mJy/beam (100 km/s channels) | 1 | 3$\sigma$ image RMS depths between 1.2 mJy/beam (z $\sim 0.2$) and 0.6 mJy/beam (z $\sim 1.2$) over 100 km/s channels. |
| Average FWHM of detected CO peaks | 356 | not stated | km/s | 5 | the average FWHM of the detected CO peaks ($356\ \mathrm{km}\ \mathrm{s}^{-1}$) |
| Stellar mass-to-light ratio | 0.83 | 0.3 dex scatter | dimensionless | 6 | We determine a mass-to-light ratio of 0.83 by comparing our sample of; We take the scatter in this relation (0.3 dex) as the uncertainty in the stellar masses. |
| log(sSFR) vs log(Mgas) slope, SpARCS BCGs at z<0.6 | 0.9 | 0.3 | dimensionless | 8 | With (logarithmic) slopes of $0.9 \pm 0.3$ and $0.9 \pm 0.2$ and offsets of $-10 \pm 3$ and $-10 \pm 2$, respectively |
| log(sSFR) vs log(Mgas) slope, Edge BCGs at z<0.6 | 0.9 | 0.2 | dimensionless | 8 | With (logarithmic) slopes of $0.9 \pm 0.3$ and $0.9 \pm 0.2$ and offsets of $-10 \pm 3$ and $-10 \pm 2$, respectively |
| Average cluster mass of the SpARCS sample | ~1.5e14 | 0.7e14 | Msun | 0 | our clusters have an average cluster mass $\sim (1.5 \pm 0.7)\times10^{14} \ \mathrm{M}_\odot$ |

## Qualitative findings

- CO emission is mostly unresolved  
  > "We detected mostly unresolved CO emission at" (Observations)
- A single BCG (CDFS-CO3) is also detected in radio continuum  
  > "A single BCG (CDFS-CO3) was additionally detected in radio continuum." (Observations)
- BCGs above z~1.0 seem to fall above the Edge-sample relation, a possible change in gas processing (speculative)  
  > "seem to fall above this relation, suggesting a possible change in gas processing" (Direct comparison with lower-redshift BCGs)

## Claim tuples

- H: Molecular gas is common in star-forming BCGs out to z~1.2 | E: ALMA CO(2-1) observations of 30 SpARCS BCGs selected as IR-bright | R: CO detected in 24 of 30 (80%) | F: Molecular gas is common in star-forming BCGs at high redshift | **supported**
- H: BCGs at z<0.6 follow the same gas mass versus sSFR correlation as the low-z cooling-flow BCG sample | E: ODR line fits in log space to the SpARCS and Edge BCGs below z=0.6 | R: Slopes 0.9 +/- 0.3 and 0.9 +/- 0.2, offsets -10 +/- 3 and -10 +/- 2 | F: Both samples process molecular gas in similar ways | **supported**
- H: The same gas processing persists to higher redshift | E: Overplot the complete SpARCS sample on the Edge-sample fit | R: Much of the sample to z~1.0 lies within the 1 sigma region; BCGs above z~1.0 lie above the relation | F: Uniformity may persist but a larger, more complete sample is needed | **partially**
- H: The higher detection rate than earlier BCG surveys comes from selecting on star formation | E: Compare detection rates with earlier BCG CO surveys | R: Earlier surveys had considerably lower detection rates | F: Selection on star formation likely explains the difference | **partially**

## Reasoning

- Why this data: Constrain BCG mass growth processes with molecular gas in a large BCG sample spanning 6 Gyr  
  > "We aim to constrain the processes driving BCG mass growth by studying molecular gas in a large sample of BCGs spanning 6 Gyr of cosmic time." (Introduction)
- Why this method: Galactic alpha_CO and r21 chosen as typical of star-forming Main Sequence galaxies and for easy comparison with existing BCG H2 masses  
  > "as these are typical of galaxies on the star-forming Main Sequence (ex. (cite: solomon1997molecular); (cite: freundlich2019phibss2))" (CO (2-1) Molecular Gas Measurements)
- Alternative: Younger-population SED template for stellar masses changes them by at most 8%, not adopted  
  > "changes the average stellar mass values by at most 8%." (Stellar Masses and Star Formation Rates)
- Alternative: More modern SFR method (Rieke 2009) gives similar results  
  > "We achieve similar results with more modern SFR methods such as that of (cite: Rieke_2009)." (Stellar Masses and Star Formation Rates)
- How they decided it was enough: Observations designed for a constant gas mass depth; low-z objects were observed longer than necessary because of ALMA's minimum integration time  
  > "These observations were designed to be complete to a constant gas mass depth of" (Observations); "were observed for longer than necessary to achieve this molecular gas mass limit" (Observations)
- Limitation (authors): Higher-z similarity is inconclusive because of small sample and selection effects  
  > "but this is inconclusive due to the small sample size and potential selection effects from limited sensitivity." (Direct comparison with lower-redshift BCGs)
- Limitation (authors): Sample is not complete in SFR because of the SWIRE MIPS limit  
  > "our sample is not complete in SFR" (Stellar Masses and Star Formation Rates)
- Limitation (authors): 24 um SFR method is known to overestimate SFRs at high redshift  
  > "We note that this method is known to overestimate SFRs, particularly at high redshifts" (Stellar Masses and Star Formation Rates)
- Limitation (authors): No X-ray data to confirm the dynamical state of the clusters  
  > "Unfortunately, we lack the X-ray measurements necessary to confirm the dynamical state of our clusters." (Discussion)
- Caveat (inferred, ours): Single Galactic alpha_CO and r21 for all BCGs; alpha_CO is uncertain in BCGs and the Edge sample used different CO transitions
- Caveat (inferred, ours): 24 um SFRs may be contaminated by AGN; only IRAC-colour wedge used to screen
- Caveat (inferred, ours): ODR fits to a small z<0.6 subset with large uncertainties; 'same correlation' rests on overlapping errors, not a formal test
- Caveat (inferred, ours): Spectral resolution and apertures chosen per source, so line fluxes depend on analyst choices
- Caveat (inferred, ours): Cluster masses come from richness (N_gal) for SpARCS but from SDSS halo masses for Edge, so the mass comparison is indirect

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: imaging task parameters and per-source spectral channel width
- Missing: continuum subtraction method and line-free channels
- Missing: flux, bandpass and phase calibrators
- Missing: FAST SED fit configuration and the SFR rescaling factor
- Missing: no released spectra, code or analysis scripts
- Data volume (inferred): Tens of GB raw for ~15 h across 30 short pointings in Bands 3-5; calibrated cubes smaller
- Score (inferred): 3/5, Project code and the spectral-extraction recipe are given, and results are tabulated, but imaging and continuum-subtraction settings, calibrators and the SED-fit configuration are not stated.
- Rediscovery candidate: yes, Single project code printed and the extraction/fitting recipe is stated with a numeric table of gas masses, but data publicness is not stated in the paper and imaging parameters are missing.

## Links

- Method: (cite: webb2015_SpARCS) (SpARCS cluster sample, richness and BCG star-forming fraction)
- Method: (cite: lidman2020_newozdes) (OzDES redshifts used for target selection)
- Method: (cite: remijan2019alma) (ALMA flux calibration uncertainty)
- Companion: (cite: edge2001detection) (Low-redshift cooling-flow BCG CO sample used for comparison)
- Companion: (cite: Webb_2017_1049) (SpARCS1049 BCG molecular gas detection shown in the comparison)
- Companion: (cite: noble2019_clustergalmgas) (J0225-303 SpARCS BCG gas detection shown in the comparison)
- Related: SpARCS
- Related: OzDES
- Related: SWIRE
- Related: Dark Energy Survey
- Related: ASPECS
- Related: PHIBSS1
- Related: PHIBSS2

## Checks

```json
{
 "quotes": 111,
 "quotes_ok": 111,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 103,
  "stated": 76,
  "rate": 0.738
 },
 "evidence_ok": true
}
```
