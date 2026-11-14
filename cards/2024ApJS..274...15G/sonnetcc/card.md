# ALMA-IMF. XIV. Free─Free Templates Derived from H41α and Ionized Gas Content in 15 Massive Protoclusters

`2024ApJS..274...15G` | The Astrophysical Journal Supplement Series 2024 | first author: Galván-Madrid, Roberto | arXiv: 2407.07359 | DOI: 10.3847/1538-4365/ad61e6

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type large_program_or_survey

## Science

- Fields: star_formation, milky_way_ism
- Question: Use the H41alpha recombination line to build free-free templates of the ALMA-IMF 3 mm and 1.3 mm continuum maps (separating free-free from dust), then derive HII-region properties (Q0, EM, n_e, spectral type), He abundances and kinematics across 15 massive protoclusters  
  > "We use the H$41\alpha$ recombination line to create templates of the millimeter free-free emission in the ALMA-IMF continuum maps, which allows to separate it from dust emission." (abstract); "We use the derived maps to estimate the properties of up to 34 HII regions across the ALMA-IMF protoclusters." (abstract)
- Target **15 ALMA-IMF protoclusters (G008.67, G010.62, G012.80, G327.29, G328.25, G333.60, G337.92, G338.93, G351.77, G353.41, W43-MM1, W43-MM2, W43-MM3, W51-E, W51-IRS2)**: coordinates _not stated_; z/distance within 5 kpc from the Sun (Introduction); per-protocluster d listed in the HII-region table (2.0 to 5.5 kpc)  
  > "The ALMA-IMF Large Program targeted fifteen of the most massive star-forming clumps within 5 kpc from the Sun" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: _none stated_
- bands: Band 3 (3 mm) and Band 6 (1 mm); H41alpha cubes from Band 3 (spw1)  
  > "The two-band (3 mm and 1 mm), two-configuration, mosaic observing mode allows to map the extent of these protocluster clumps with excellent imaging quality" (Introduction); "We use the H$41\alpha$ line to create maps of the free-free emission at the frequencies of the ALMA-IMF continuum images in Bands 3 and 6." (3.1 Procedure)
- frequencies and spectral setup: Cubes cover H41alpha, He41alpha, C41alpha (rest 92.034434, 92.071938, 92.080355 GHz), total width 270 km/s centred on each protocluster LSR velocity  
  > "The rest frequencies of the targeted lines are respectively 92.034434, 92.071938, and 92.080355 GHz" (2 Data); "All the cubes were made covering a total width of 270 km s$^{-1}$." (2 Data)
- continuum bandwidth: _not stated_
- arrays: 12m array (12M cubes and continuum)  
  > "The ALMA-IMF consortium has provided science-ready data products to the community, including 12m-array continuum images" (Introduction)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Cube beams listed per protocluster in Table 1 (HPBW from 0.39x0.35 arcsec for W51-E to 2.28x1.93 arcsec for G012.80)  
  > "(2) cube half-power beamwidth and position angle" (Table 1)
- max recoverable scale: Cleaning scales extend to ~8 arcsec, about half of the largest recoverable scale (value taken from DiazGonzalez23)  
  > "or about half of the largest recoverable scale in the data" (2 Data)
- sensitivity: Moment 0 noise (MAD std) per protocluster given in Table 1 (5 to 83 mJy/beam km/s)  
  > "(4) MAD standard deviation of the moment 0 image." (Table 1)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: ALMA-IMF Large Program data (consortium data products)  
  > "The ALMA-IMF Large Program targeted fifteen of the most massive star-forming clumps within 5 kpc from the Sun" (Introduction)
- Line: H 41alpha (92.034434 GHz)
- Line: He 41alpha (92.071938 GHz)
- Line: C 41alpha (92.080355 GHz)
- Other facility **VLA**: Ku-band 2.2 cm (13.4 GHz) image of W51 used as independent free-free estimate for validation  
  > "the Ku-band (2.2 cm, 13.4 GHz) VLA image presented in" (3.3 Validation)
- Other facility **ATLASGAL**: Larger parent sample from which the ALMA-IMF protoclusters were selected  
  > "based on the larger ATLASGAL sample across the Galaxy" (Introduction)
- External data: LSR systemic velocities of each protocluster used as cube reference velocities  
  > "The reference velocities for the cube construction were set to the LSR systemic velocities of each protocluster reported in Table 1 of" (2 Data) [from (cite: Motte22)]
- External data: ALMA-IMF continuum images used for the startmodel and for the free-free subtraction  
  > "Also, a `startmodel` is used based on the continuum images published in (cite: Ginsburg22)." (2 Data) [from (cite: Ginsburg22)]
- External data: VLA Ku-band (2.2 cm) image of W51 used for cross-validation  
  > "the Ku-band (2.2 cm, 13.4 GHz) VLA image presented in" (3.3 Validation) [from (cite: Ginsburg16)]
- External data: Hot molecular core catalogue (76 sources) used to check molecular-line contamination  
  > "the 76 sources in the hot molecular core (HMC) catalogue of" (3.3 Validation) [from (cite: Bonfand24_arxiv)]
- External data: Stellar spectral-type calibrations (O-type and B-type) to convert Q0 to spectral type  
  > "The spectral types of the ionizing stars are determined using the calibrations of" (4 HII region properties) [from (cite: Martins05) for O-type, (cite: Panagia73) for B-type]
- External data: Evolutionary stage (young, intermediate, evolved) of the protoclusters  
  > "the evolutionary stage (young, intermediate, or evolved) of the ALMA-IMF protoclusters determined by (cite: Motte22)" (4 HII region properties) [from (cite: Motte22)]

## Processing

### Calibration

- pipeline or manual: ALMA-IMF data pipeline (imaging and self-calibration pipeline of Ginsburg22)  
  > "using the ALMA-IMF data pipeline (cite: Ginsburg22)" (2 Data); "together with an imaging and self-calibration pipeline (cite: Ginsburg22)" (Introduction)
- casa version: CASA 6.3.0  
  > "The cubes were created in `CASA` version 6.3.0 (cite: CASA2022)" (2 Data)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA tclean, via the ALMA-IMF pipeline  
  > "This is defined using the `threshold` parameter of the `tclean` task." (2 Data)
- deconvolver: Multi-scale clean  
  > "Multi-scale cleaning is used by setting the `deconvolver` and `scales` parameters in `tclean`." (2 Data)
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: Point source, the beamsize, and multiples of x2 the beamsize up to ~8 arcsec  
  > "The scales are selected to clean model components of size zero (point source), the beamsize, and multiples of $\times 2$ the beamsize until reaching $\sim 8$ arcsec" (2 Data)
- continuum subtraction: Cubes are continuum-subtracted (contsub in file names); method not described  
  > "`FIELD_B3_spw1_12M_h41a.JvM.image.contsub.fits`" (Filenames and data products)
- line free channels: _not stated_
- primary beam correction: Applied last, to the free-free map, error map and pure-dust map  
  > "Finally, the primary-beam (PB) correction is applied to the regridded free-free estimation map and the associated error map, as well as to the pure dust map." (3.1 Procedure)
- array combination: _not stated_
- smoothing: Continuum images convolved to the slightly larger beam of the line cube and moment 0 maps  
  > "which in turn are convolved to the slightly larger beamsize" (3.1 Procedure)
- final beam: See Table 1 (cube beams per protocluster)  
  > "(2) cube half-power beamwidth and position angle" (Table 1)
- final rms: Moment 0 MAD std per protocluster in Table 1 (5 to 83 mJy/beam km/s)  
  > "(4) MAD standard deviation of the moment 0 image." (Table 1)

### Inherited from earlier work

- Cube imaging procedures  
  > "We followed the procedures developed for the imaging of cubes as described in (cite: Cunningham2023)." (2 Data) [from (cite: Cunningham2023)]
- Cleaning parameters kept in the pipeline repository script imaging_parameters.py  
  > "The cleaning parameters are available in the `imaging_parameters.py` script in the public repository of the ALMA-IMF data processing pipeline." (2 Data) [from ALMA-IMF reduction pipeline (cite: Ginsburg22)]
- Largest recoverable scale of the data  
  > "or about half of the largest recoverable scale in the data (cite: DiazGonzalez23)" (2 Data) [from (cite: DiazGonzalez23)]
- Free-free intensity equation from H41alpha integrated intensity  
  > "the free-free estimation map $I_\mathrm{ff}$ in units of Jy beam$^{-1}$ is constructed using the following equation (cite: Wilson09; Wenger19):" (3.1 Procedure) [from (cite: Wilson09; Wenger19)]
- Equations for optical depth, EM, n_e and Q0  
  > "We then used the following equations (cite: Wilson09; RS20) to derive their average emission measures" (4 HII region properties) [from (cite: Wilson09; RS20)]
- He+/H+ abundance equation  
  > "We calculate the number abundance of singly-ionized He to ionized H using the following equation (cite: RoelfsemaGoss92):" (5 Helium abundances) [from (cite: RoelfsemaGoss92)]
- Collisional broadening estimate  
  > "Following the equations in the appendix of (cite: GM12), we estimate that collisional broadening is about $0.05$ km s$^{-1}$" (6.3 Evolution of the HII regions) [from (cite: GM12)]

### Not stated but needed to reproduce (our reading)

- tclean weighting (robust value), cell size and image size of the H41alpha cubes
- Channel width and exact spectral window/MS selection of the cubes (only 'spw1' and 270 km/s total width are given)
- Continuum-subtraction method and line-free channels used to make the contsub cubes
- tclean masking strategy, number of iterations and the absolute threshold in each cube (only 3-5 x rms is stated)
- Exact scale list in pixels and the clean-component start model details
- Commit/version of the ALMA-IMF reduction pipeline repository and the imaging_parameters.py values
- Definition and measurement method of the effective diameter D of each HII-region aperture (aperture files are only in the data release)
- Weighting scheme used in the weighted least-squares fits of Q0, n_e and EM versus D
- PySpeckit fit bounds, error estimation and the exact mask/spectrum extraction for each aperture
- Formula and conversion used to deconvolve the dynamical width from thermal and collisional widths
- Source of the distances d used in the HII-region table
- How uncertainties other than the 20% Te error were propagated into Q0, EM and n_e

## Analysis recipe

1. **Image H41alpha/He41alpha/C41alpha line cubes**: Build 270 km/s wide cubes in CASA with the ALMA-IMF pipeline, multi-scale clean with a startmodel, then apply the JvM correction  
  > "The cubes were created in `CASA` version 6.3.0 (cite: CASA2022) using the ALMA-IMF data pipeline (cite: Ginsburg22)." (2 Data); "Finally, the JvM correction (cite: JvM95) is applied to the `CASA`-generated cubes in order to correct the flux scale of the residuals and of the restored image" (2 Data)
   - software: CASA, tclean, ALMA-IMF pipeline, beam-volume-tools
   - parameter: Clean threshold 3 to 5 x rms noise of channels with H41alpha emission  
  > "Each cube is cleaned down to a residual level of $\times 3$ to $\times 5$ the rms noise ($\sigma_\mathrm{rms}$) of channels with H$41\alpha$ emission." (2 Data)
   - parameter: gain = 0.08 for all cubes  
  > "The `gain` parameter was set to 0.08 for all the cubes, which is slightly slower than the default (0.1) in `CASA`." (2 Data)
   - parameter: startmodel from the published ALMA-IMF continuum images  
  > "Also, a `startmodel` is used based on the continuum images published in (cite: Ginsburg22)." (2 Data)
   - parameter: Cube width 270 km/s, centred on protocluster LSR velocity  
  > "All the cubes were made covering a total width of 270 km s$^{-1}$." (2 Data)
   - fitting: _not stated_
   - validation: _not stated_
2. **Make H41alpha velocity-integrated (moment 0) maps**: Moment 0 over a visually chosen velocity range per protocluster; free-free estimated only above 5 sigma (MAD std)  
  > "The velocity range is optimized by visual inspection to cover only channels where the line is detected." (3.1 Procedure); "above a threshold of $5\sigma$, where $\sigma$ is defined as the robust standard deviation using the median absolute deviation (MAD) implemented in `astropy.stats.mad_std`" (3.2 Products)
   - software: astropy
   - parameter: Default +-10 km/s about systemic velocity for faint or non-detected protoclusters  
  > "A default value of $\pm 10$ km s$^{-1}$ from the cloud systemic velocity is used for the protoclusters where the line is faint or non-detected" (3.1 Procedure)
   - parameter: Free-free maps of G338.93, W43-MM1 and G328.25 set manually to zero (non-detections / molecular contamination)  
  > "we manually set their free-free maps to zero" (3.2 Products)
   - fitting: _not stated_
   - validation: _not stated_
3. **Convert moment 0 to free-free intensity and error maps**: I_ff = 1.432e-4 (nu0^-1.1 Te^1.15)(1+NHe/NH) x moment 0, rescaled to continuum frequencies with alpha_ff = -0.1; error map combines moment 0 noise and 20% Te error  
  > "the free-free estimation map $I_\mathrm{ff}$ in units of Jy beam$^{-1}$ is constructed using the following equation (cite: Wilson09; Wenger19):" (3.1 Procedure); "Maps of the error of the free-free intensity $\sigma_\mathrm{ff}$ are also generated." (3.1 Procedure)
   - parameter: Te = 7000 K, NHe/NH = 0.08, nu0 = H41alpha central frequency  
  > "where the electron temperature $T_e = 7000$ K, the helium to hydrogen number ratio $N_\mathrm{He}/N_\mathrm{H} = 0.08$, and $\nu_0$ is the central frequency of the H$41\alpha$ line." (3.1 Procedure)
   - parameter: Scaling to Band 3 (98.6 GHz) and Band 6 (224.6 GHz) factors 0.99 and 0.92  
  > "The flux scalings to the Band 3 (98.6 GHz) and Band 6 (224.6 GHz) continuum frequencies are then 0.99 and 0.92, respectively." (3.1 Procedure)
   - parameter: 20% error in Te propagated  
  > "We consider a $20\%$ error in $T_e$ and propagate it through our measurements to acknowledge the possibility of spatial variations in this quantity." (3.1 Procedure)
   - assumption: LTE for the H41alpha line  
  > "assumes LTE conditions, and we found a posteriori that this assumption is generally valid" (3.1 Procedure)
   - assumption: Optically thin free-free at mm wavelengths, alpha_ff = -0.1  
  > "the output free-free map at the frequency of H$41\alpha$ (92.03 GHz) is rescaled to the desired frequency of the continuum image assuming $\alpha_\mathrm{ff} = -0.1$." (3.1 Procedure)
   - assumption: Te = 7000 K chosen near the middle of the expected range and to minimize oversubtraction  
  > "Our selection is close to the middle of this range and minimized regions of oversubtraction of the free-free emission in the continuum maps." (3.1 Procedure)
   - fitting: _not stated_
   - validation: Validated a posteriori against the VLA 2 cm extrapolation (step 5)  
  > "To cross-validate our method, we compare the H$41\alpha$-derived free-free estimation $I_\mathrm{ff,H41}$ at 98 GHz for the W51 protoclusters to an independent estimation $I_\mathrm{ff,2cm}$" (3.3 Validation)
4. **Regrid, subtract free-free from continuum and apply primary-beam correction**: Regrid ff and error maps to the continuum pixel grid, convolve continuum to the line-cube beam, subtract to obtain pure-dust map, then apply PB correction  
  > "A subtraction is then performed of the convolved continuum image minus the regridded free-free map, resulting in an estimated map of pure-dust emission $I_\mathrm{dust}$." (3.1 Procedure); "Performing the PB correction as a last step has the advantage of working with images with spatially uniform noise levels in the intermediate steps." (3.1 Procedure)
   - software: CASA, astropy
   - fitting: _not stated_
   - validation: _not stated_
5. **Cross-validate H41alpha free-free against VLA 2 cm extrapolation in W51**: Convolve VLA 2 cm image to the H41alpha-map beam, regrid, scale to 98.6 GHz assuming optically thin free-free, mask below 5 sigma and compare pixel by pixel  
  > "Next, we assume that the 2-cm free-free emission is optically thin and rescale the cm map by a factor $(98.6/13.4)^{-0.1}$ to estimate the free-free intensity in the ALMA-B3 map." (3.3 Validation)
   - parameter: Mask pixels below 5 sigma = 5 x 92 microJy/beam  
  > "Finally, we mask out all pixels below $5\sigma = 5 \times 92~\mu$Jy beam$^{-1}$" (3.3 Validation)
   - assumption: 2 cm emission optically thin with spectral index -0.1 up to 98.6 GHz  
  > "Next, we assume that the 2-cm free-free emission is optically thin" (3.3 Validation)
   - fitting: _not stated_
   - validation: 96.8% of 145,862 pixels within 3 sigma of the one-to-one relation; bright outliers at W51 d2 and e2  
  > "$96.8~\%$ are within $3\sigma$ of the one-to-one relation, where $\sigma$ is determined for each pixel using the H$41\alpha$ free-free error map" (3.3 Validation)
6. **Derive HII-region EM, n_e, Q0 and spectral types**: Define apertures on the 3 mm free-free maps; compute tau_ff from mean intensity, then EM, Q0 and n_e for a sphere of diameter D; assign spectral type from Q0  
  > "We then used the following equations (cite: Wilson09; RS20) to derive their average emission measures (EM, pc cm$^{-6}$), electron densities ($n_e$, cm$^{-3}$), and hydrogen ionizing-photon rates ($Q_0$, s$^{-1}$):" (4 HII region properties); "we first define apertures of distinct HII emission in each of the 12 protoclusters with recombination line detection" (4 HII region properties)
   - parameter: alpha_B = 2e-13 case-B recombination coefficient  
  > "$\alpha_\mathrm{B} = 2\times10^{-13}$ cm$^{-3}$ s$^{-1}$ is the case-B hydrogen recombination coefficient." (4 HII region properties)
   - parameter: Spectral types from Martins05 (O) and Panagia73 (B)  
  > "The spectral types of the ionizing stars are determined using the calibrations of (cite: Martins05) for O-type, and of (cite: Panagia73) for B-type." (4 HII region properties)
   - assumption: Spherical geometry, integration path equals diameter D  
  > "thus under spherical geometry the diameter of the emitting HII region is $\int dl = D$." (4 HII region properties)
   - assumption: A single ionizing star per HII region  
  > "A single ionizing star is assumed." (4 HII region properties)
   - fitting: _not stated_
   - validation: Compared with H30alpha 3D radiative transfer Q0 for G010.62  
  > "the inferred $Q_0$ is 6 to $7\times10^{48}$ s$^{-1}$ (cite: GM23), which is consistent the spherical value reported here: $5.1\pm1.4 \times10^{48}$ s$^{-1}$" (4 HII region properties)
7. **Measure He/H abundance from H41alpha and He41alpha Gaussian fits**: Fit Gaussians to H41alpha and He41alpha spectra averaged in each HII-region mask (PySpeckit); N_H/N_He taken from the integrated-line ratio  
  > "We performed Gaussian fitting using `Pyspeckit` (cite: Ginsburg22_pyspeckit)." (5 Helium abundances); "We calculate the number abundance of singly-ionized He to ionized H using the following equation (cite: RoelfsemaGoss92):" (5 Helium abundances)
   - software: PySpecKit
   - parameter: Spectra in brightness temperature versus LSR velocity; cubes without PB correction  
  > "We use the H$41\alpha$ cubes without primary-beam correction to have a noise closer to spatially uniform." (5 Helium abundances)
   - parameter: Reject He fits with peak > 0.3 of the H peak  
  > "we rejected He$41\alpha$ fits with a peak brightness $> 0.3$ of the hydrogen peak." (5 Helium abundances)
   - parameter: Reject He centroids outside +-10 km/s of -122.17 km/s from H41alpha  
  > "we rejected results with a He$41\alpha$ centroid outside a range of $\pm10$ km s$^{-1}$ of its theoretical position at $-122.17$ km s$^{-1}$ from the H$41\alpha$." (5 Helium abundances)
   - assumption: H and He recombination lines of the same quantum number trace the same gas; N_H+/N_He+ approximates N_H/N_He  
  > "Abundances of helium with respect to hydrogen can be derived under the assumption that for a given quantum number the recombination lines of the different atoms trace the same gas" (5 Helium abundances)
   - fitting: Hydrogen-only fit first, then helium added with the first fit as initial guess; initial N_He/N_H = 0.08; C41alpha attempted but not used  
  > "An initial round of fitting included only the hydrogen recombination line, and helium was added later using as initial guesses the parameters of the first fitting." (5 Helium abundances); "The final fits only consider hydrogen and helium lines." (5 Helium abundances)
   - validation: Rejection criteria set empirically from the fit plots  
  > "These criteria were found empirically" (5 Helium abundances)
8. **Search for H41alpha maser amplification**: Look for significantly negative 'potholes' in the pure-dust maps in Bands 3 and 6 and test them against the free-free error maps  
  > "looked for areas that are significantly negative" (6.2 A search for sites with excess recombination line emission); "iii) that the absolute value of the pothole minimum be larger than the respective error in the free-free estimation, both in Band 3 and Band 6." (6.2 A search for sites with excess recombination line emission)
   - parameter: Pothole visible in both bands and larger than one beam area  
  > "i) that the pothole is clearly visible both in the Band 3 and Band 6 subtraction (pure dust) maps" (6.2 A search for sites with excess recombination line emission)
   - assumption: A negative pothole would indicate H41alpha brighter than the LTE expectation  
  > "A naive interpretation of those potholes would be that they are regions where the H$41\alpha$ is brighter than the LTE assumption" (6.2 A search for sites with excess recombination line emission)
   - fitting: _not stated_
   - validation: Candidate potholes consistent with zero within free-free errors (G010.62 within 1 sigma)  
  > "This target was our clearest candidate, yet the central hole is within $1\sigma$ of the free-free estimation error at that position." (6.2 A search for sites with excess recombination line emission)
9. **Correlate HII-region properties with size and fit power laws**: Pearson correlations and weighted least-squares fits in log space of Q0, n_e and EM versus D  
  > "A weighted least-squares fit to the $Q_0$ vs $D$ relation gives $\log [Q_0 / \mathrm{s}^{-1}] = (2.49\pm0.18) \times \log [D/\mathrm{pc}] + (49.89\pm0.23)$." (6.3 Evolution of the HII regions)
   - parameter: Pearson (r,p) for Q0 vs D = (0.89, 1.6e-12)  
  > "$Q_0$ is well correlated with $D$, with a Pearson correlation coefficient $r$ and p-value $(r,p) = (0.89,1.6\times10^{-12})$." (6.3 Evolution of the HII regions)
   - fitting: Weighted least-squares in log-log space; priors/likelihood not applicable  
  > "we fit a posteriori the $n_e$ vs $D$ and EM vs $D$ relations in logarithmic space" (6.3 Evolution of the HII regions)
   - validation: Compared with expected Q0 proportional to D^3 (constant n_e) and D^2 (constant EM)  
  > "the observed $Q_0 \propto D^{2.5}$ relation falls in between the expected relations if $n_e$ or EM were constant among the sample of HII regions" (6.3 Evolution of the HII regions)
10. **Derive dynamical linewidths of the HII regions**: Deconvolve thermal and collisional broadening from the observed H41alpha FWHM and compare with 2 c_s  
  > "was deconvolved from the thermal and collisional widths" (Conclusions); "The thermal FWHM linewidth at $T_e=7000$ K $\pm 20~\%$ is $17.9\pm1.8$ km s$^{-1}$." (6.3 Evolution of the HII regions)
   - parameter: Collisional broadening ~0.05 km/s for densities up to 1e5 cm^-3, neglected  
  > "we estimate that collisional broadening is about $0.05$ km s$^{-1}$ for densities as high as $10^5$ cm$^{-3}$, therefore it can be neglected." (6.3 Evolution of the HII regions)
   - assumption: Ionized-gas sound speed c_s ~ 10 km/s; optically thin HII region expected to show dynamical width <~ 2 c_s  
  > "Therefore, an optically-thin HII region is expected to have an observed dynamical linewidth $\lesssim 2c_s$." (6.3 Evolution of the HII regions)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 6.3.0: Imaging of the H41alpha cubes with tclean  
  > "The cubes were created in `CASA` version 6.3.0 (cite: CASA2022)" (2 Data)
- **tclean** : Multi-scale cleaning with threshold, startmodel, scales and gain settings  
  > "Multi-scale cleaning is used by setting the `deconvolver` and `scales` parameters in `tclean`." (2 Data)
- **ALMA-IMF data pipeline** : Imaging and self-calibration pipeline used to build the cubes  
  > "using the ALMA-IMF data pipeline (cite: Ginsburg22)" (2 Data)
- **JvM correction scripts (beam-volume-tools)** : JvM correction of the CASA-generated cubes  
  > "The scripts to apply the JvM correction that were used for the imaging presented in this paper" (footnote 1)
- **astropy (astropy.stats.mad_std)** : Robust (MAD) standard deviation of the moment 0 maps  
  > "the median absolute deviation (MAD) implemented in `astropy.stats.mad_std`" (3.2 Products)
- **PySpecKit** : Gaussian fitting of H41alpha and He41alpha spectra  
  > "We performed Gaussian fitting using `Pyspeckit` (cite: Ginsburg22_pyspeckit)." (5 Helium abundances)
- **ffsub.py and ff_tools.py (h41a-freefree scripts)** : Recalculate any free-free estimation image  
  > "permit the user to easily recalculate any free-free estimation image by editing `ffsub.py`, which makes use of the functions defined in `ff_tools.py`." (3.2 Products)
- **APLpy** : Listed in the Software section; specific use not stated  
  > "APLpy (cite: APLpy)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Q0 versus D power-law slope | 2.49 | 0.18 | dimensionless | 9 | $\log [Q_0 / \mathrm{s}^{-1}] = (2.49\pm0.18) \times \log [D/\mathrm{pc}] + (49.89\pm0.23)$ |
| Q0 versus D intercept (log Q0 at log D = 0) | 49.89 | 0.23 | dimensionless | 9 | $\log [Q_0 / \mathrm{s}^{-1}] = (2.49\pm0.18) \times \log [D/\mathrm{pc}] + (49.89\pm0.23)$ |
| Pearson (r,p) for Q0 versus D | r = 0.89, p = 1.6e-12 | not stated | dimensionless | 9 | $(r,p) = (0.89,1.6\times10^{-12})$ |
| Pearson (r,p) for n_e vs D and EM vs D | n_e: (-0.25, 0.15); EM: (0.12, 0.50) | not stated | dimensionless | 9 | with $(r,p) = (-0.25,0.15)$ and $(0.12,0.50)$, respectively |
| n_e versus D log-log slope and intercept | -0.23 and 3.70 | 0.08 and 0.10 (1 sigma) | dimensionless | 9 | ($-0.23\pm0.08$, $3.70\pm0.10$) and ($0.52\pm0.17$, $7.39\pm0.22$) |
| EM versus D log-log slope and intercept | 0.52 and 7.39 | 0.17 and 0.22 (1 sigma) | dimensionless | 9 | ($-0.23\pm0.08$, $3.70\pm0.10$) and ($0.52\pm0.17$, $7.39\pm0.22$) |
| Number of HII regions defined | 34 | not stated | count | 6 | We defined 34 regions of HII emission and measured their photometry. |
| Free-free flux scaling factors from 92.03 GHz to Band 3 and Band 6 | 0.99 (98.6 GHz) and 0.92 (224.6 GHz) | not stated | dimensionless | 3 | The flux scalings to the Band 3 (98.6 GHz) and Band 6 (224.6 GHz) continuum frequencies are then 0.99 and 0.92, respectively. |
| Fraction of validation pixels within 3 sigma of the one-to-one relation | 96.8 % (of 145,862 pixels) | not stated | percent | 5 | $96.8~\%$ are within $3\sigma$ of the one-to-one relation, where $\sigma$ is determined for each pixel using the H$41\alpha$ free-free error map |
| Q0 of central HII region in G010.62 | 5.1e48 | 1.4e48 | s^-1 | 6 | $5.1\pm1.4 \times10^{48}$ s$^{-1}$ |
| Q0 of W51-E | 7.4e48 | 1.7e48 | s^-1 | 6 | W51-E is found to have the second largest $Q_0$ ($7.4\pm1.7\times10^{48}$ s$^{-1}$) among the ALMA-IMF protoclusters. |
| Total Q0 of G333.60 | ~3e49 | not stated | s^-1 | 6 | totalling $Q_0\approx3\times10^{49}$ s$^{-1}$ |
| N_He/N_H, G010.62 HII region 2 (low outlier) | 0.028 | 0.012 | dimensionless | 7 | HII region 2 in G010.62 with $0.028\pm0.012$, and HII region 3 in G012.80 with $0.045\pm0.005$ |
| N_He/N_H, G012.80 HII region 3 (low outlier) | 0.045 | 0.005 | dimensionless | 7 | HII region 2 in G010.62 with $0.028\pm0.012$, and HII region 3 in G012.80 with $0.045\pm0.005$ |
| N_He/N_H, W43-MM2 HII region 2 (MM13, high outlier) | 0.187 | 0.058 | dimensionless | 7 | with $N_\mathrm{He} / N_\mathrm{H} = 0.187\pm0.058$ |
| Relative He mass abundance Y range (excluding outliers) | 0.202 to 0.288 | 0.012 and 0.010 | dimensionless | 7 | this translates into $Y = 0.202\pm0.012$ to $Y = 0.288\pm0.010$. |
| Thermal FWHM linewidth at Te = 7000 K | 17.9 | 1.8 | km/s | 10 | The thermal FWHM linewidth at $T_e=7000$ K $\pm 20~\%$ is $17.9\pm1.8$ km s$^{-1}$. |
| Dynamical linewidth of W43-MM2 HII region 2 (MM13) | 39.1 | 2.0 | km/s | 10 | $\Delta V_\mathrm{dyn} = 39.1\pm2.0$ km s$^{-1}$ |
| Pearson (r,p) for dynamical width versus D and versus Q0 | (0.34, 0.05) and (0.33, 0.06) | not stated | dimensionless | 10 | with $(r,p) = (0.34, 0.05)$ and $(0.33,0.06)$, respectively |

## Qualitative findings

- Three protoclusters (W43-MM1, G338.93, G328.25) show no ionized-gas emission; the youngest protoclusters lack detectable ionized gas  
  > "The youngest protoclusters (W43-MM1, G338.93, G328.25) lack detectable emission from ionized gas." (Conclusions)
- Bright outlier pixels in the W51 validation coincide with UC HII regions d2 (W51-IRS2) and e2 (W51-E)  
  > "Further inspection reveals that these pixels are located exactly at the position of the two well known UC HII regions: d2 in W51-IRS2 and e2 W51-E" (3.3 Validation)
- Molecular line contamination is important only in three hot molecular cores (G327 HMC 1, G337 HMCs 1 and 4)  
  > "Analysis of the spectra around their positions shows that recombination line emission dominates in all cases except for G327 HMC 1 and G337 HMCs 1 and 4." (3.3 Validation)
- No significant evidence for H41alpha masers in the ALMA-IMF data  
  > "We conclude that there is no significant evidence for H$41\alpha$ masers in the ALMA-IMF data" (6.2 A search for sites with excess recombination line emission)
- Most HII regions have dynamical widths between about one and two times the ionized-gas sound speed; MM13 is an outlier  
  > "$\Delta V_\mathrm{dyn}$ increases from about one to two times the ionized-gas sound speed." (abstract)

## Claim tuples

- H: H41alpha-derived free-free templates agree with independent centimeter-extrapolated free-free estimates | E: Compare H41alpha free-free map at 98.6 GHz with the VLA 2 cm map rescaled with alpha = -0.1 for W51-E and W51-IRS2 | R: 96.8% of 145,862 pixels lie within 3 sigma of one-to-one; two UC HII regions are bright outliers | F: The procedure agrees within errors for the vast majority of pixels, with exceptions at a few UC HII regions | **supported**
- H: HII-region ionizing-photon rates and spectral types follow the proposed evolutionary sequence of the protoclusters | E: Derive Q0 and spectral type for 34 HII regions from the 3 mm free-free maps and compare with the Motte22 evolutionary classes | R: Youngest protoclusters lack ionized gas; total Q0 rises from ~1e45 to >1e49 s^-1 with evolution | F: Q0 and spectral types follow the evolutionary trend | **supported**
- H: Helium abundances in the ionized gas are consistent with the Galactic ISM | E: Fit H41alpha and He41alpha Gaussians in 25 HII regions and compute N_He/N_H | R: Most values near 0.08; two low outliers (G010.62 HII 2, G012.80 HII 3) and one high candidate (W43-MM2 HII 2, 0.187+-0.058) | F: Abundances broadly consistent with the ISM, with a few outliers discussed | **supported**
- H: H41alpha maser amplification could be present at some sites | E: Search for negative potholes in the Band 3 and Band 6 pure-dust maps and test against the free-free errors | R: All potholes are consistent with zero within the free-free estimation errors | F: No significant evidence for H41alpha masers | **refuted**
- H: Smaller UC HII regions are the dynamically younger versions of larger ones | E: Correlate Q0, n_e and EM with HII-region size D and fit power laws | R: Q0 proportional to D^(2.49+-0.18); n_e and EM correlations with D are weak | F: Smaller UC HII regions are on average ionized by less massive stars rather than being younger | **supported**
- H: The outlier HII region south of W43-MM2 (MM13) has a distinct ionization or kinematic origin | E: Compare its dynamical width, He abundance and line profile with the sample | R: Broadest line (dynamical width 39.1+-2.0 km/s), double-peaked, N_He/N_H = 0.187+-0.058 | F: Suggested embedded stellar or disk wind, not firmly established | **partially**

## Reasoning

- Why this data: Free-free emission contaminates the dust continuum of the ALMA-IMF dense-core science case  
  > "The free-free estimations are useful to the main scientific case of the ALMA-IMF project of characterizing the dust emission of the dense-core population in the target protoclusters." (3.1 Procedure)
- Why this method: Using H41alpha within the same data set gives the same uv coverage and beam as the continuum and a free-free estimate at a similar frequency  
  > "This method offers several advantages, namely: covering the whole survey, having approximately the same uv-coverage and beamsize as the corresponding continuum images" (Introduction)
- Alternative: Extrapolating centimeter-wavelength VLA maps to the millimeter (used only for validation; 10 of 15 protoclusters are hard to observe with the VLA)  
  > "ten out of fifteen ALMA-IMF protoclusters have declinations $< -15^\circ$, which makes them difficult to observe with the VLA" (3.3 Validation)
- Alternative: Fits including C41alpha were attempted but rejected: extra parameters had low S/N and did not improve the fit  
  > "Valid fits including C$41\alpha$ were found occasionally, but the extra fitted parameters had low S/N and did not improve the overall fit quality." (5 Helium abundances)
- How they decided it was enough: _not stated_
- Limitation (authors): LTE assumption for H41alpha and molecular-line contamination may fail in some objects  
  > "However, the method is not without its caveats, mainly that the line can be out of LTE under certain conditions (cite: Walmsley90; Peters12), and molecular line contamination." (Introduction)
- Limitation (authors): The recombination-line free-free map is less sensitive than the continuum, so faint ionized emission is missed  
  > "the free-free map derived from the recombination line is less sensitive than the corresponding millimeter continuum image" (6.1 On the subtraction of free-free contamination)
- Limitation (authors): Templates should not be used blindly where free-free dominates or at line-rich hot molecular cores  
  > "We caution the user against blindly using the calculated free-free templates in regions where it dominates the total continuum emission, or at the position of line rich hot molecular cores." (3.2 Products)
- Limitation (authors): Spherical HII-region approximation is only good for isolated, round regions  
  > "Our spherical approximation will be good for HII regions that are isolated and round." (4 HII region properties)
- Caveat (inferred, ours): Single fixed Te = 7000 K and 20% error for all HII regions; Te dominates many error bars and could vary between regions
- Caveat (inferred, ours): Q0 and spectral type assume a single ionizing star and spherical geometry; compact regions in clusters may be multiple stars
- Caveat (inferred, ours): Correlation significance for dynamical width is marginal (p about 0.05)
- Caveat (inferred, ours): LTE for H41alpha is argued a posteriori and bright outliers in W51 show departures or optical-thickness effects

## Reproducibility

- Data public (paper): ALMA-IMF science-ready products released to the community; the paper distributes its input cubes, free-free templates and scripts  
  > "The ALMA-IMF consortium has provided science-ready data products to the community" (Introduction); "With this paper we distribute the input cubes, the derived data products, and associated scripts" (Conclusions)
- Products in archive: Products hosted on Harvard Dataverse (doi 10.7910/DVN/LWILNE); not stated to be in the ALMA archive  
  > "We make available the following FITS images in the following url, hosted by the Harvard Dataverse service:" (Filenames and data products)
- Code: Scripts ffsub.py and ff_tools.py in the public h41a-freefree repository  
  > "<https://github.com/ALMA-IMF/h41a-freefree>" (footnote 3); "permit the user to easily recalculate any free-free estimation image by editing `ffsub.py`, which makes use of the functions defined in `ff_tools.py`." (3.2 Products)
- Code: ALMA-IMF data-processing pipeline (reduction) repository  
  > "<https://github.com/ALMA-IMF/reduction>" (footnote 2)
- Missing: ALMA project code(s) are not printed in the paper (only 'ALMA-IMF Large Program')
- Missing: Cube imaging settings beyond threshold, gain and scales (robust, cell, image size, channel width, masks) are only in the pipeline imaging_parameters.py
- Missing: Aperture definitions are in the released .reg files, not described numerically in the text
- Missing: Fit weighting and exact PySpeckit configuration
- Missing: Per-protocluster distances are tabulated without stated source
- Data volume (inferred): Large if re-imaging from raw ALMA data (15 mosaic fields, Band 3 spw1 12m line cubes); small (a few GB) if the released H41alpha cubes and continuum images are used
- Score (inferred): 4/5, Public ALMA-IMF data, released cubes and templates, released scripts, explicit equations and parameters (Te, NHe/NH, alpha_ff, thresholds), and tabulated numeric results; only low-level imaging settings and aperture/fit details are deferred to other works or repositories.
- Rediscovery candidate: yes, Data and scripts are public, the free-free recipe and HII-region equations are fully given, and main results (Q0, EM, n_e, He abundances, power-law fits) are tabulated numbers.

## Links

- Method: Ginsburg et al. 2022, A&A 662, A9 (cite: Ginsburg22) (ALMA-IMF imaging and self-calibration pipeline and continuum images)
- Method: Cunningham et al. 2023, A&A 678, A194 (cite: Cunningham2023) (Cube imaging procedures followed here)
- Method: Motte et al. 2022, A&A 662, A8 (cite: Motte22) (Survey description, systemic velocities and evolutionary classification)
- Method: Diaz-Gonzalez et al. 2023, ApJS 269, 55 (cite: DiazGonzalez23) (Combination with single-dish data, largest recoverable scale, spectral index maps)
- Companion: Pouteau et al. 2022, 2023 (cite: Pouteau22; Pouteau23) (Core mass function of young protoclusters)
- Companion: Nony et al. 2023 (cite: Nony2023) (Core mass function study using spectral-index information)
- Companion: Armante et al. 2024 (cite: Armante24) (CMF of G012.80 using results of this paper)
- Companion: Bonfand et al. 2024 (cite: Bonfand24_arxiv) (Hot molecular core catalogue used to check line contamination)
- Related: ALMA-IMF Large Program
- Related: ATLASGAL

## Checks

```json
{
 "quotes": 149,
 "quotes_ok": 149,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2017.1.01355.L"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 19,
 "numeric_problems": 0,
 "fill": {
  "facts": 136,
  "stated": 104,
  "rate": 0.765
 },
 "evidence_ok": true
}
```
