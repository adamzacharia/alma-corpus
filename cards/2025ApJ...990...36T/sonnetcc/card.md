# Constraining Star Formation in M87 Using Deep Hubble Space Telescope UV Data

`2025ApJ...990...36T` | The Astrophysical Journal 2025 | first author: Tamhane, Prathamesh | arXiv: 2507.13431 | DOI: 10.3847/1538-4357/adf20d

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, agn_and_quasars, galaxy_clusters_and_sz
- Question: How much star formation (rate and history) is there in M87, as constrained by deep HST F275W imaging, and how does it relate to AGN feedback, the UV filaments and the counterjet hotspot  
  > "We analyzed the deepest Hubble Space Telescope (HST) F275W ultraviolet (UV) imaging of M87 to obtain the most robust constraints on its star formation rate (SFR) and star formation history (SFH)." (abstract)
- Target **M87 (BCG of the Virgo cluster), including its counterjet hotspot**: coordinates _not stated_; z/distance 16.5 Mpc  
  > "M87 is the BCG of the nearby Virgo cluster (16.5 Mpc; (cite: mei07)) and one of the best-studied radio galaxies." (Introduction); distance from (cite: mei07)  
  > "M87 is the BCG of the nearby Virgo cluster (16.5 Mpc; (cite: mei07)) and one of the best-studied radio galaxies." (Introduction)

## Data provenance

- ALMA projects: 2013.1.00862.S
- bands: _not stated_
- frequencies and spectral setup: ALMA flux density quoted at 214.1 x 10^9 Hz; band and spectral setup not stated  
  > "The radio spectral index from 1.4 to 214 GHz is" (Counterjet hotspot)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: archival ALMA pipeline product, project 2013.1.00862.S (PI: Simionescu)  
  > "ALMA image was obtained from the pipeline processed product from the ALMA data archive with project ID 2013.1.00862.S (PI: Simionescu)." (Counterjet hotspot)
- Other facility **HST (ACS, WFC3)**: F275W, F606W, F660N and F814W imaging of the inner 10 kpc of M87; the main data of the paper  
  > "The HST data used in this work were collected with Advanced Camera for Surveys (ACS) and Wide Field Camera 3 (WFC3) instruments focusing on the inner 10 kpc of the galaxy." (HST observations and Data Analysis)
- Other facility **VLA**: radio images of the hotspot (L, C, X, U bands) from the NRAO VLA Archive Survey  
  > "VLA images were obtained from the NRAO VLA Archive Survey Images page[^5]" (Counterjet hotspot)
- Other facility **Chandra ACIS**: about 1 Ms of data from 46 observations used to constrain X-ray emission of the hotspot (not detected)  
  > "We also used $\sim$ 1 Ms of Chandra data from 46 ACIS observations to constrain the X-ray emission for the hotspot" (Counterjet hotspot)
- Other facility **HDUV Legacy Survey (HST)**: comparison field to estimate background source density  
  > "we used the Hubble Deep UV (HDUV) Legacy Survey[^3] to estimate background source density." (Point source detection)
- Other facility **Gaia DR3**: astrometric reference for aligning the HST images  
  > "the images were aligned to the GAIA Data Release 3 catalog (cite: gaia2016; gaia2023)" (HST observations and Data Analysis)
- External data: Classical nova catalog for M87, cross-matched and removed from the UV source catalog  
  > "We also compared our sources to the classical novae detected in M87 by (cite: shara23) and (cite: lessing24)." (Point source detection) [from (cite: shara23); (cite: lessing24)]
- External data: UV-upturn model F275W-F606W colour for M87 and colour profile  
  > "from the (cite: Martocchia25) model, is significantly redder" (Point source detection) [from (cite: Martocchia25)]
- External data: Galactic extinction A_V = 0.0612 from dust maps, with extinction curve R_V = 3.1  
  > "The measured source fluxes were corrected for Galactic extinction using $A_V = 0.0612$ taken from (cite: schlafly11) dust maps and (cite: fitzpatrick99) extinction curve with $R_V = 3.1$" (Point source detection) [from (cite: schlafly11); (cite: fitzpatrick99)]
- External data: Library of simulated star clusters (Chabrier IMF, solar metallicity) used for forward modeling  
  > "We used their extensive library of simulated star clusters with a Chabrier IMF and solar metallicity, spanning a wide range of cluster ages and masses." (Star formation Rate in M87) [from (cite: krumholz19)]
- External data: Globular cluster magnitudes used as a consistency check for Group 1 sources  
  > "The magnitudes of our Group 1 sources are consistent with those of the globular clusters in (cite: bellini15) to within 0.006 mag in all bands." (Point source detection) [from (cite: bellini15)]
- External data: Earlier optical spectral index of the hotspot, 2.23 +/- 0.5, compared with this work's HST value  
  > "lower than the previously reported value of $2.23 \pm 0.5$ from S92 using ground-based optical data" (Counterjet hotspot) [from S92 = (cite: sparks92)]
- Simulation/model as data: SLUG stochastic stellar population simulations (Chabrier IMF, Padova isochrones, metallicities 0.05 and 0.02) compared to Group 2 sources  
  > "we ran SLUG simulations in galaxy mode, modeling both continuous and single-burst SFHs with Chabrier IMF (cite: chabrier03), Padova isochrones including pulsating AGB stars, and metallicities of 0.05 and 0.02." (Star formation Rate in M87)

## Processing

### Calibration

- pipeline or manual: ALMA archive pipeline-processed product used  
  > "ALMA image was obtained from the pipeline processed product from the ALMA data archive with project ID 2013.1.00862.S (PI: Simionescu)." (Counterjet hotspot)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: yes, pipeline processed image taken from the ALMA archive; no background subtraction applied  
  > "No background subtraction was performed for VLA and ALMA data" (Counterjet hotspot)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Forward-modeling likelihood comparison of simulated clusters to observed HST magnitudes  
  > "We then compared the reweighted simulated cluster sample to the observed HST magnitudes using a likelihood function, following the method described in (cite: krumholz19)." (Star formation Rate in M87) [from (cite: krumholz19)]
- Isophotal galaxy-model subtraction procedure  
  > "The diffuse emission was removed by iterative isophotal fitting implemented with PHOTUTILS following the example notebooks[^2]." (Point source detection) [from photutils example notebooks (footnote 2)]
- Two-photon emission estimate for the F275W band  
  > "Using the framework and parameters outlined in Appendix B of (cite: bracco20)" (Excitation mechanisms of the filaments in the F275W Band) [from (cite: bracco20)]
- Chandra ACIS data processing for the hotspot X-ray limits  
  > "following standard Chandra ACIS data processing steps" (Counterjet hotspot) [from standard Chandra ACIS processing, no reference given]

### Not stated but needed to reproduce (our reading)

- ALMA band, frequency setup, array configuration, beam and rms of the 2013.1.00862.S image used for the hotspot, and which pipeline-product image (continuum or spectral window) was measured
- Aperture centre of the elliptical hotspot region (only axes and position angle are given) and the ALMA beam size relative to that aperture
- Whether the ALMA flux was corrected for the primary beam, and how the 0.61 mJy uncertainty was derived
- Fitting method used for the power-law spectral indices (least squares or other) and which data points entered each fit
- SExtractor configuration beyond the 3 sigma threshold and 5x5 Gaussian filter (deblending, minimum area, background mesh)
- Cluster-simulation grid, filter response and likelihood details of the Krumholz et al. forward model (library version, priors on mass, bin sizes)
- Which SLUG parameters set the 35-50 clusters per trial and how the 100 trials were combined in the Bhattacharyya distance
- Dust-absorption contour definition (unsharp-mask scale) used for the extinction estimate
- Exact HST data products and versions used (MAST HLSP link text is blank in the paper)

## Analysis recipe

1. **align and combine HST images**: align to Gaia DR3 with TWEAKREG, normalize with PHOTEQ, then drizzle with ASTRODRIZZLE to a common pixel scale  
  > "Subsequently, the images in each band were drizzled together using ASTRODRIZZLE, which reduced noise, removed cosmic rays in overlapping regions" (HST observations and Data Analysis); "Images in the same band taken on different dates were photometrically normalized using PHOTEQ in the DRIZZLEPAC." (HST observations and Data Analysis)
   - software: DRIZZLEPAC, TWEAKREG, TWEAKBACK, PHOTEQ, ASTRODRIZZLE
   - parameter: 5 sigma limiting magnitudes 28.21 (F275W), 28.01 (F606W), 28.78 (F814W) in 0.5 arcsec diameter aperture  
  > "The final images have a 5$\sigma$ limiting magnitudes of 28.21 mag, 28.01 mag, and 28.78 mag in F275W, F606W and F814W bands, respectively, in 0$''$.5 diameter circular aperture." (HST observations and Data Analysis)
   - fitting: _not stated_
   - validation: _not stated_
2. **subtract galaxy light and detect point sources**: iterative isophotal fitting with PHOTUTILS, 2D background subtraction elsewhere, then SExtractor detection on F275W and dual-image photometry on F606W and F814W  
  > "For regions not covered by the elliptical fits, we applied 2D background subtraction using photutils with a 50$\times$50 pixel box size to remove large-scale residuals." (Point source detection); "Source detection was performed on the F275W image, while photometry was measured on the F606W and F814W images." (Point source detection)
   - software: PHOTUTILS, SExtractor
   - parameter: detection threshold 3 sigma  
  > "We adopted a detection threshold of 3$\sigma$." (Point source detection)
   - parameter: 5x5 pixel Gaussian smoothing kernel, standard deviation 2.5 pixels  
  > "the image was smoothed using a 5$\times$5 pixel Gaussian kernel with a standard deviation of 2.5 pixels to enhance the detectability of faint sources." (Point source detection)
   - parameter: photometry in 0.5 arcsec diameter circular aperture  
  > "Photometric fluxes were measured in a 0$''$.5 diameter circular aperture centered on each detected source." (Point source detection)
   - fitting: _not stated_
   - validation: artificial point-source injection tests gave M87 completeness of 94% for mag below 26.5, 91% at 27.5 and 80% at 28.5  
  > "M87 image completeness is 94% for sources with mag $<$26.5, 91% at 27.5, and 80% at 28.5." (Point source detection)
3. **clean the source catalog and split into groups**: mask AGN and jet, remove cross-matched novae, keep S/N > 5, correct for Galactic extinction, split into Group 1 (globular clusters) and Group 2 (blue sources) by colour and magnitude  
  > "Finally, we selected 1219 sources with a signal-to-noise ratio greater than 5 for further analysis." (Point source detection); "We categorize sources with F275W$–$F606W $>$ 2.6 mag and F606W $<$ 25 mag as Group 1 and the remaining sources as Group 2." (Point source detection)
   - software: SExtractor
   - parameter: nova cross-match radius 0.07 arcsec; 28 common sources removed  
  > "We cross-matched our source catalog with their nova catalog using a matching radius of 0$''$.07, identifying 28 common sources across the entire image" (Point source detection)
   - assumption: A_V = 0.0612 with R_V = 3.1 for Galactic extinction  
  > "The measured source fluxes were corrected for Galactic extinction using $A_V = 0.0612$ taken from (cite: schlafly11) dust maps and (cite: fitzpatrick99) extinction curve with $R_V = 3.1$" (Point source detection)
   - fitting: _not stated_
   - validation: Group 1 magnitudes agree with published globular clusters to within 0.006 mag  
  > "The magnitudes of our Group 1 sources are consistent with those of the globular clusters in (cite: bellini15) to within 0.006 mag in all bands." (Point source detection)
4. **estimate background contamination and UV-upturn contribution**: apply the same detection to HDUV fields to estimate background source density, and compare Group 2 colours with UV-upturn and blue horizontal branch models  
  > "we used the Hubble Deep UV (HDUV) Legacy Survey[^3] to estimate background source density." (Point source detection); "confirming that UV-upturn stars do not contribute to the Group 2 population" (Point source detection)
   - software: SExtractor
   - parameter: same 3 sigma threshold, 50x50 pixel background box and 5x5 pixel Gaussian filter as for M87  
  > "which is SExtractor with a 3$\sigma$ detection threshold, 50$\times$50 pixel background box, and a 5$\times$5 pixel Gaussian filter." (Point source detection)
   - fitting: _not stated_
   - validation: completeness tests also run on HDUV images: 100% to mag 23.5, 90% at 27, 35% at 28.5  
  > "In the HDUV images, completeness is 100% to mag 23.5, 90% at 27, and 35% at 28.5." (Point source detection)
5. **match SLUG simulations to Group 2 sources**: SLUG galaxy-mode simulations for continuous and single-burst SFHs, scored with the Bhattacharyya distance against observed Group 2 sources  
  > "we computed the Bhattacharyya distance between simulated clusters of each parameter set and the observed sources." (Star formation Rate in M87)
   - software: SLUG
   - parameter: 100 trials per SFH; continuous SFR 1e-6 to 1e-4 Msun/yr with 200 Myr timescale; burst peaks 6 to 200 Myr, total mass 1e2 to 1e4 Msun  
  > "For each SFH, we simulated 100 trials using a range of parameters to estimate the expected distribution of star cluster properties under different star formation scenarios." (Star formation Rate in M87); "with burst peaks ranging from 6 Myr to 200 Myr and total stellar masses from 10$^2$ to $10^4$ M$_\odot$." (Star formation Rate in M87)
   - assumption: Chabrier IMF, Padova isochrones including pulsating AGB stars, metallicities 0.05 and 0.02  
  > "Chabrier IMF (cite: chabrier03), Padova isochrones including pulsating AGB stars, and metallicities of 0.05 and 0.02." (Star formation Rate in M87)
   - fitting: minimum Bhattacharyya distance over the parameter grid  
  > "A Bhattacharyya distance of 0 represents identical source distributions with perfect overlap" (Star formation Rate in M87)
   - validation: _not stated_
6. **infer cluster mass, age and SFR by forward modeling**: reweight a library of simulated clusters by age to represent the assumed SFH and compare to observed HST magnitudes with a likelihood; sample the posterior  
  > "Rather than simulating new cluster populations for each assumed SFH, we reweighted each cluster by adjusting its relative probability based on its age to reflect the assumed SFH." (Star formation Rate in M87)
   - software: SLUG
   - parameter: posterior sampled 1e5 times; median with 1 sigma credible intervals  
  > "We sampled the posterior probability distribution functions (PDFs) of stellar mass and age 10$^5$ times to infer the median mass, age, and SFR with 1$\sigma$ credible intervals." (Star formation Rate in M87)
   - assumption: uniform prior on cluster age; Chabrier IMF and solar metallicity library  
  > "We assumed a uniform prior on cluster age, allowing the data to constrain the SFH shape without bias." (Star formation Rate in M87)
   - fitting: likelihood comparison of reweighted simulated clusters to observed HST magnitudes; posterior PDFs of mass and age (sampler not named)  
  > "We then compared the reweighted simulated cluster sample to the observed HST magnitudes using a likelihood function, following the method described in (cite: krumholz19)." (Star formation Rate in M87)
   - validation: _not stated_
7. **estimate dust extinction toward the inner UV filaments**: measure extinction from F606W model and residual fluxes in dust absorption regions, then compute A_V and expected A_275 with an extinction law and compare to observed F275W  
  > "$A_V$ and expected $A_{275}$ were calculated using the (cite: cardelli89) extinction law and $R_V = 3.1$." (UV bright filaments)
   - assumption: Cardelli et al. extinction law with R_V = 3.1  
  > "$A_V$ and expected $A_{275}$ were calculated using the (cite: cardelli89) extinction law and $R_V = 3.1$." (UV bright filaments)
   - fitting: _not stated_
   - validation: observed A_275 compared with the expected value from the extinction law  
  > "is $A_{275} = 0.031 \pm 0.028$, which is close to the expected value." (UV bright filaments)
8. **measure the counterjet hotspot flux in HST, VLA, ALMA and Chandra**: extract flux in one elliptical aperture from continuum-subtracted HST images and the same region from VLA and ALMA images; Chandra upper limits assuming an absorbed power law  
  > "We used the same region to extract flux from the VLA and ALMA images of the hotspot." (Counterjet hotspot); "assuming an absorbed powerlaw model with a photon index of 1.7." (Counterjet hotspot)
   - parameter: elliptical aperture, semi-major 2.32 arcsec, semi-minor 0.81 arcsec, position angle 12 degrees  
  > "We measured the hotspot flux within an elliptical aperture with semi-major and semi-minor axes of 2$''$.32 and 0$''$.81, respectively, and a position angle of 12 degrees" (Counterjet hotspot)
   - assumption: no background subtraction for VLA and ALMA, so hotspot flux may include radio lobe emission  
  > "No background subtraction was performed for VLA and ALMA data; therefore, the hotspot flux density may include some contribution from the radio lobe." (Counterjet hotspot)
   - fitting: _not stated_
   - validation: not stated; errors are statistical only  
  > "The errors are statistical only." (Table 1)
9. **derive hotspot spectral indices**: power-law spectral index S proportional to nu^-alpha, derived separately for HST optical-UV and for radio 1.4 to 214 GHz  
  > "we calculated its spectral index" (Counterjet hotspot); "The radio spectral index from 1.4 to 214 GHz is $0.96 \pm 0.05$" (Counterjet hotspot)
   - assumption: power-law spectrum; synchrotron emission  
  > "Since the hotspot emission is powered by synchrotron radiation (cite: sparks92), we calculated its spectral index" (Counterjet hotspot)
   - fitting: _not stated_
   - validation: optical index compared with earlier ground-based value from S92  
  > "lower than the previously reported value of $2.23 \pm 0.5$ from S92 using ground-based optical data" (Counterjet hotspot)

## Software

- **DRIZZLEPAC (TWEAKREG, TWEAKBACK, PHOTEQ, ASTRODRIZZLE)** : HST image alignment, normalization and drizzling  
  > "using the TWEAKREG tool from the DRIZZLEPAC package." (HST observations and Data Analysis)
- **SExtractor** : point source detection and dual-image photometry  
  > "We performed multi-band photometry using SExtractor’s dual-image mode." (Point source detection)
- **PHOTUTILS** : isophotal galaxy model subtraction and 2D background subtraction  
  > "The diffuse emission was removed by iterative isophotal fitting implemented with PHOTUTILS following the example notebooks[^2]." (Point source detection)
- **SLUG** : stochastic stellar population simulations of young star clusters  
  > "we use the code Stochastically Lighting Up Galaxies (SLUG)[^4]" (Star formation Rate in M87)
- **astropy** : _not stated_
- **CLOUDY** : cited hidden cooling flow simulation of the filaments, from a private communication  
  > "Simulation of a hidden cooling flow (cite: fabian22) with CLOUDY suggests that the filament may be dominated by Fe and Mg emission lines around 2550–2800 Å (private communication)." (Excitation mechanisms of the filaments in the F275W Band)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| time-averaged star formation rate in M87 | 1.8e-5 | +1.7/-0.4 (x 1e-5) | Msun/yr | 6 | The time-averaged SFR in M87 is extremely low, $1.8^{+1.7}_{-0.4} \times 10^{-5}$ M$_\odot$ yr$^{-1}$ |
| total stellar mass formed | 995 | +3446/-573 | Msun | 6 | The total stellar mass formed is $995^{+3446}_{-573}$ M$_\odot$ |
| cluster age | 7.1e7 | +10.0/-4.8 (x 1e7) | yr | 6 | with a cluster age of $7.1^{+10.0}_{-4.8} \times 10^7$ yr |
| best-match Bhattacharyya distance for single burst 125 Myr ago, 1e3 Msun, Z = 0.02 | 0.17 | not stated | dimensionless | 5 | a burst 125 Myr ago with 10$^3$ M$_\odot$ stars formed for solar ($Z=0.02$) metallicity tracks gave the best match between observed and simulated sources with a Bhattacharyya distance of 0.17. |
| number of sources after detection, nova removal and S/N > 5 cut | 1219 | not stated | sources | 3 | Finally, we selected 1219 sources with a signal-to-noise ratio greater than 5 for further analysis. |
| Group 1 and Group 2 source counts | 803 and 416 | not stated | sources | 3 | There are 803 sources in Group 1 and 416 sources in Group 2. |
| Group 2 sources identified as young stellar sources in the inner 30 arcsec | approximately 58 | not stated | sources | 4 | This still leaves approximately 58 Group 2 sources that we identify as young stellar sources. |
| average visual extinction toward inner filaments | 0.015 | 0.008 | mag | 7 | We found an average visual extinction $A_V = 0.015 \pm 0.008$, consistent with previous studies. |
| observed F275W extinction A_275 in the same regions | 0.031 | 0.028 | mag | 7 | is $A_{275} = 0.031 \pm 0.028$, which is close to the expected value. |
| ALMA flux density of the hotspot at 214.1 GHz | 7.90e-3 | 0.61e-3 (statistical) | Jy | 8 | (7.90$\pm$0.61)$\times 10^{-3}$ |
| optical-to-UV spectral index of the hotspot from HST data | 1.81 | 0.04 | dimensionless | 9 | The optical-to-UV spectral index derived from only HST data is $1.81 \pm 0.04$ |
| radio spectral index of the hotspot, 1.4 to 214 GHz | 0.96 | 0.05 | dimensionless | 9 | The radio spectral index from 1.4 to 214 GHz is $0.96 \pm 0.05$ |

## Qualitative findings

- Excess of blue UV point sources in the inner region of M87, not explained by UV-upturn stars  
  > "This trend clearly indicates that there is an excess of UV-bright sources in the inner region of the galaxy." (Point source detection)
- No apparent spatial correlation between the young sources and the optical H-alpha filaments  
  > "Visual inspection reveals no apparent correlation between the sources and the optical H$\alpha$ filaments." (Connection between UV sources and optical/UV filaments)
- Outer UV filaments are co-spatial with H-alpha filaments; inner ones are hidden by dust  
  > "All of these filaments are co-spatial with the H$\alpha$+\[N II\] filaments shown in the right panel of Fig [5](#fig:filaments)." (UV bright filaments)

## Claim tuples

- H: M87 has only very weak recent star formation despite its cool core and multiphase gas | E: Compare Group 2 UV sources to SLUG simulations and forward-model cluster ages and masses | R: time-averaged SFR 1.8e-5 Msun/yr and about 1000 Msun formed, peaking about 125 Myr ago | F: star formation in M87 is extremely low, far below the X-ray cooling rate | **supported**
- H: The excess blue sources are a UV-upturn population rather than young stellar sources | E: Compare Group 2 F275W-F606W colours with UV-upturn and blue horizontal branch models | R: model colours are far redder than Group 2 colours | F: the blue sources are young stellar sources, not UV-upturn stars | **supported**
- H: AGN outbursts trigger star formation in M87 | E: Compare the derived star formation history with known AGN outburst ages | R: no stars with ages matching the recent outbursts; youngest stars match an older outburst | F: recent outbursts did not trigger detectable star formation, earlier ones may have | **partially**
- H: The UV filaments are powered by young stars or two-photon emission | E: Starburst spectrum modeling and a two-photon emission estimate compared with the observed filament flux | R: stellar and two-photon contributions are far too low | F: filaments are likely powered by metal-line emission from collisional ionization | **partially**
- H: The counterjet hotspot SED shows a synchrotron break between radio and optical | E: Measure hotspot flux in VLA, ALMA, HST and Chandra and compute spectral indices | R: optical-UV index 1.81 +/- 0.04, radio index 0.96 +/- 0.05, Chandra not detected | F: a spectral break lies between 214 GHz and 372 THz | **supported**

## Reasoning

- Why this data: very deep HST UV imaging of nearby M87 allows an unusually detailed study of its star formation  
  > "existing very deep HST UV imaging of M87 combined with its proximity allow an unprecedented detailed study of its star formation activity and history." (Introduction)
- Why this method: SLUG samples stars and clusters stochastically, suited to the low star formation regime  
  > "This approach allows the code to capture the effects of stochasticity in young, low-mass star clusters, providing more accurate predictions in the low star formation regime" (Star formation Rate in M87)
- Alternative: UV-upturn old stars and high-metallicity blue horizontal branch stars rejected as the origin of Group 2 sources because their colours are redder  
  > "we compared the colors of blue horizontal branch stars at high metallicity with ages of 10 and 15 Gyr from the (cite: maraston05) model and found that they have F275W$-$F606W colors of 4.17 and 4.30, respectively." (Point source detection)
- Alternative: Two-photon emission rejected as the filament power source (three orders of magnitude too faint)  
  > "This suggests that two-photon emission is negligible in the filaments" (Excitation mechanisms of the filaments in the F275W Band)
- How they decided it was enough: _not stated_
- Limitation (authors): ALMA and VLA hotspot fluxes have no background subtraction and may include radio lobe emission  
  > "No background subtraction was performed for VLA and ALMA data; therefore, the hotspot flux density may include some contribution from the radio lobe." (Counterjet hotspot)
- Limitation (authors): No detailed hotspot SED modeling  
  > "We did not perform the detailed modeling of the hotspot SED as it is beyond the scope of this paper." (Counterjet hotspot)
- Limitation (authors): Flux errors are statistical only  
  > "The errors are statistical only." (Table 1)
- Limitation (authors): Distinguishing galaxy-associated sources from background sources is challenging  
  > "Since distinguishing galaxy-associated and background sources is challenging" (Point source detection)
- Caveat (inferred, ours): The ALMA measurement is a single flux density from an archive pipeline image with no stated beam, band or rms, so the 214 GHz point and the 0.96 radio index depend on unreported details
- Caveat (inferred, ours): ALMA and VLA apertures were not background-subtracted and the VLA/ALMA beams likely differ from the aperture, so the radio index may be biased by lobe emission and resolution mismatch
- Caveat (inferred, ours): The Bhattacharyya match and the forward-model posterior depend on simulated cluster libraries and the Group 2 selection and background correction, which are not independently validated

## Reproducibility

- Data public (paper): HST data from MAST, ALMA product from the public ALMA archive; the paper's HST products are said to be on MAST as a High Level Science Product  
  > "All our data products are available at MAST as a High Level Science Product" (HST observations and Data Analysis); "ALMA image was obtained from the pipeline processed product from the ALMA data archive with project ID 2013.1.00862.S (PI: Simionescu)." (Counterjet hotspot)
- Products in archive: ALMA pipeline-processed product obtained directly from the ALMA archive  
  > "ALMA image was obtained from the pipeline processed product from the ALMA data archive with project ID 2013.1.00862.S (PI: Simionescu)." (Counterjet hotspot)
- Code: _not stated_
- Missing: ALMA image identity (band, spectral window, beam, rms) and the aperture centre for the hotspot
- Missing: SExtractor configuration details and the cluster library settings for the forward model
- Missing: MAST HLSP link text is empty in the paper
- Missing: Data and method for the Chandra upper limits beyond a photon index of 1.7
- Data volume (inferred): ALMA: one pipeline-processed image product (well under 1 GB); HST: multi-epoch F275W, F606W, F660N and F814W imaging from six programs (tens of GB raw, smaller as drizzled products)
- Score (inferred): 3/5, Scale 1-5. HST pipeline and SLUG recipe are described with key parameters and numeric results, but the ALMA part is a single flux point with no instrument settings, and several analysis choices are inherited from Krumholz et al. 2019 or left unstated
- Rediscovery candidate: no, Data are public, but the ALMA contribution is minor and unspecified, and the main SFR result depends on inherited forward-model settings and unstated SExtractor and library details

## Links

- Method: (cite: krumholz19) (forward-modeling method and cluster library used to infer mass, age and SFR)
- Method: (cite: krumholz15); (cite: dasilva12) (SLUG stochastic stellar population synthesis code)
- Method: (cite: bracco20) (framework for the two-photon emission estimate)
- Companion: (cite: bellini15) (earlier HST UV study of M87 globular clusters used as a consistency check)
- Companion: (cite: shara23); (cite: lessing24) (M87 classical nova catalogs removed from the UV source list)
- Companion: (cite: Martocchia25) (UV-upturn model for M87 compared with Group 2 colours)
- Companion: (cite: sparks92) (earlier optical spectral index of the hotspot)
- Related: ALMA project 2013.1.00862.S (PI: Simionescu)
- Related: HST proposals 10543, 12271, 12989, 13731, 14618, 16894
- Related: Hubble Deep UV (HDUV) Legacy Survey
- Related: NRAO VLA Archive Survey (NVAS)

## Checks

```json
{
 "quotes": 103,
 "quotes_ok": 103,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 117,
  "stated": 73,
  "rate": 0.624
 },
 "evidence_ok": true
}
```
