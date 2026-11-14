# Connecting the growth of galaxies to the large-scale environment in a massive node of the Cosmic Web at z ∼ 3

`2025A&A...696A..95G` | Astronomy and Astrophysics 2025 | first author: Galbiati, M. | arXiv: 2410.03822 | DOI: 10.1051/0004-6361/202452493

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: How the local and large-scale environment around the z~3.25 quasar CTS G18.01 (MQN01 field) affects the stellar mass assembly and star formation of its galaxies  
  > "unveil the roles of both the local and large-scale environment on the stellar mass assembly and star formation activity of the galaxies populating this unique field" (Introduction)
- Target **CTS G18.01 (MQN01 field)**: coordinates _not stated_; z/distance z ~ 3.25  
  > "We present in this work a multiwavelength survey of the large-scale galaxy environment around the $z\approx3.25$ quasar CTS G18.01" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2021.1.00793.S
- bands: Band 3 and Band 6 mosaics  
  > "with Band 3 and Band 6 mosaics to detect dusty star forming galaxies via their 1.2 mm continuum emission or CO(4–3) emission lines" (Multiwavelength photometry and ancillary data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Cycle 8 ALMA programme 2021.1.00793.S, PI S. Cantalupo (data reduced and published by Pensabene et al. 2024)  
  > "targeted the field with a Cycle 8 ALMA programme (ID 2021.1.00793.S, PI S. Cantalupo)" (Multiwavelength photometry and ancillary data)
- Line: CO 4-3 (not stated)
- Other facility **VLT/MUSE**: Main dataset: mosaic of four pointings (about 2x2 arcmin, 4x4 cMpc^2) around the quasar, GTO programme 0102.A-0448(A)  
  > "The main dataset consists of a mosaic of four VLT/MUSE pointings around the quasar CTS G18.01." (MUSE observations); "The observations are part of a MUSE Guaranteed Time of Observations (GTO) programme ID 0102.A-0448(A), PI S. Cantalupo." (MUSE observations)
- Other facility **VLT/FORS2**: U, B, R imaging over about 24x24 cMpc^2 (programme 110.23ZX) used to select Lyman break galaxies  
  > "We followed-up the MUSE observations with a joint VLT/FORS2 and VLT/HAWK-I programme (ID 110.23ZX, PI S.Cantalupo)." (FORS2 and HAWK-I mosaics)
- Other facility **VLT/HAWK-I**: CH4, H and Ks imaging over the same area, used as photometry for SED fitting  
  > "We observed the field with a set of three filters: CH4 (1h on source" (FORS2 and HAWK-I mosaics)
- Other facility **Chandra/ACIS**: 600 ks X-ray data used to identify X-ray AGN among the galaxies (from Travascio et al., submitted)  
  > "Travascio et al., (submitted) collected 600ks of broadband" (Multiwavelength photometry and ancillary data)
- Other facility **HST/ACS**: F625W and F814W imaging, 22 orbits in Cycle 30 (PID 17065), used in the SED photometry  
  > "We also observed the field with the Hubble Space Telescope (HST) for a total of 22 orbits in Cycle 30" (Multiwavelength photometry and ancillary data)
- Other facility **JWST/NIRCam**: F150W2 and F322W2 pre-imaging from GO programme 1835, used in the SED photometry  
  > "Details on the data reduction are reported in (cite: Wang2024_bigwheel)." (Multiwavelength photometry and ancillary data)
- External data: ALMA Band 3/Band 6 dusty galaxy catalogue and CO(4-3) emitters in the field (Pensabene et al. 2024), cross-matched with the MUSE galaxies  
  > "to that of dusty star-forming galaxies detected with ALMA by (cite: Pensabene2024)" (MUSE spectroscopic sample of galaxies) [from (cite: Pensabene2024)]
- External data: Blank-field R-band luminosity function used to compute the overdensity  
  > "the overdensity estimated relative to the completeness corrected luminosity function from (cite: Reddy2009)" (Appendix: The UV luminosity function of LBGs) [from (cite: Reddy2009)]
- External data: COSMOS2020 stellar mass function at 3.0<z<3.5 used as the field reference  
  > "We thus take as a reference the stellar mass function computed by (cite: Weaver2023) in the COSMOS2020 field within the redshift range $3.0<z<3.5$" (Galaxies’ stellar mass function) [from (cite: Weaver2023)]
- External data: Star-forming main sequence parametrisations  
  > "We parametrized the main sequence with the functional forms from (cite: Speagle2014) (blue), (cite: Popesso2022) (green) and (cite: Koprowski2024) (purple) at the quasar redshift" (Galaxies’ star formation activity compared to the field) [from (cite: Speagle2014); (cite: Popesso2022); (cite: Koprowski2024)]
- External data: Galaxy-galaxy auto-correlation computed from the MUSE UDF spectroscopic catalogue  
  > "from the UDF catalog (cite: Bacon2023)" (Clustering analysis) [from (cite: Bacon2023)]
- External data: IGM absorption sightlines used to post-process the BPASS models  
  > "We thus generated 500 IGM realizations randomly extracted from 1000 sightlines from (cite: Steidel2018)" (Photometric selection of Lyman break galaxies) [from (cite: Steidel2018)]
- External data: X-ray AGN sample from Chandra, cross-matched with the MUSE galaxies  
  > "we cross-match the catalogue of MUSE galaxies to the sample of X-Ray emitting AGN observed with" (MUSE spectroscopic sample of galaxies) [from Travascio et al., (submitted)]
- External data: MAGG survey MUSE galaxy sample, used for a comparison cross-correlation measurement  
  > "Such galaxies have been identified by (cite: Lofthouse2020) running sextractor" (Appendix: MQN01 clustering compared to the MAGG survey) [from (cite: Lofthouse2020)]
- Simulation/model as data: BPASS v2.2-100bin-t8.0-Z001 stellar population models post-processed with IGM absorption, used to calibrate the UBR/UGR colour selection  
  > "To calibrate the selection region, we used BPASS SPS models ((cite: BPASS2018), v2.2-100bin-t8.0-Z001)" (Photometric selection of Lyman break galaxies)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
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

- ALMA data and reduction steps  
  > "The data and the reduction steps are detailed in (cite: Pensabene2024)." (Multiwavelength photometry and ancillary data) [from (cite: Pensabene2024)]
- JWST data reduction  
  > "Details on the data reduction are reported in (cite: Wang2024_bigwheel)." (Multiwavelength photometry and ancillary data) [from (cite: Wang2024_bigwheel)]
- Redshift confidence scoring  
  > "We attribute confidence scores to the redshift measurements following the method illustrated in (cite: Bielby2019)." (MUSE spectroscopic sample of galaxies) [from (cite: Bielby2019)]
- Clustering formalism (projected auto- and cross-correlation, eq. 10)  
  > "We follow the formalism from (cite: Trainor2012), TS12 hereafter" (Clustering analysis) [from (cite: Trainor2012)]
- CIGALE input parameter grid  
  > "The full input grid of parameters is adapted from (cite: Barrufet2020) and (cite: Riccio2023)" (Galaxies’ physical properties and SED fitting) [from (cite: Barrufet2020); (cite: Riccio2023)]
- Combination of photometric and model uncertainties for stellar mass and SFR  
  > "we follow (cite: Pacifici2023) and combine the observed uncertainties inherited from photometry" (Galaxies’ physical properties and SED fitting) [from (cite: Pacifici2023)]
- Nth-neighbour local density estimator  
  > "by using the $N_{th}$ neighbor estimator with the same formalism presented by (cite: Shimakawa2017)" (Appendix: Alignment of the LBGs with the large-scale overdensity) [from (cite: Shimakawa2017)]

### Not stated but needed to reproduce (our reading)

- All ALMA observing and processing details (array configurations, spectral setup, calibration, imaging parameters, source catalogue) are deferred to Pensabene et al. 2024, so nothing about the ALMA part can be redone from this paper
- ALMA data are used only as a cross-match catalogue; the list of ALMA-detected sources and their positions is not given here
- Quasar coordinates are not given
- The final MUSE galaxy catalogue (positions, redshifts, confidence flags) is only tabulated for the 21 central galaxies, and the redshift assignments in Marz are manual
- Photometry used in the CIGALE fits (apertures, filters actually used per galaxy) is not listed
- Radial bins, expected-count normalisation and bootstrap settings for the correlation functions are not tabulated
- Chandra AGN catalogue comes from a submitted paper
- Quasar nebula and filament information comes from an in-preparation paper

## Analysis recipe

1. **Reduce and post-process the MUSE cube**: ESO MUSE pipeline reduction followed by CubExtractor post-processing (CubeFix, CubeSharp, CubeCombine) to correct flat-fielding and sky subtraction  
  > "we post-process the final products using the CubExtractor (CubEx hereafter, (cite: DeBeer2023) and Cantalupo et al., in prep.) package, version 1.8, and its subroutines" (MUSE observations)
   - software: ESO MUSE pipeline, CubExtractor
   - fitting: _not stated_
   - validation: _not stated_
2. **Reduce FORS2 and HAWK-I imaging and measure depth and completeness**: ESO pipeline recipes, photutils background subtraction, scamp astrometry to Gaia DR3, swarp mosaicking; completeness from injection/recovery of mock point sources with SExtractor  
  > "we aligned the astrometry of each individual frame with stars from Gaia DR3 catalog (cite: Gaia2016; Gaia2023) by using the scamp package (cite: Bertin2006)" (FORS2 and HAWK-I mosaics); "we convolved point sources with the PSF and randomly injected 1500 mocks for each" (FORS2 and HAWK-I mosaics)
   - software: ESO pipeline recipes, EsoRex, photutils, scamp, swarp, SExtractor, PSFEx, DrizzlePac
   - fitting: _not stated_
   - validation: Completeness and limiting magnitudes tabulated per filter; PSF variation across the field <~10%  
  > "We then run SExtractor and measured the fraction of sources we can recover as a function of the magnitude." (FORS2 and HAWK-I mosaics)
3. **Select Lyman break galaxies at z~3-3.5 in the FORS2 field**: UBR colour selection calibrated on BPASS models with IGM absorption; R-band detection with SExtractor  
  > "(ii) $U-B>1.89$" (Photometric selection of Lyman break galaxies); "(iv) $0.31<B-R<2.20$" (Photometric selection of Lyman break galaxies)
   - software: SExtractor
   - parameter: Not detected in U above 3 sigma of the background  
  > "(i) $U>U_{\rm BKG}^{3\sigma}$" (Photometric selection of Lyman break galaxies)
   - parameter: SExtractor threshold=1.5, minarea=5 pixels, default deblending, 3x3 Gaussian filter  
  > "i) threshold=1.5 weighted on the mosaic exposure map to assure a uniform threshold across the FoV; ii) minarea=5 pixels" (Photometric selection of Lyman break galaxies)
   - assumption: Constant star formation history, age 100 Myr, Z=0.001, E(B-V)=0-0.20, Salpeter IMF  
  > "We assumed a constant star formation history and stellar age of $t=10^8{\rm\,Yr}=100\rm\,Myr$" (Photometric selection of Lyman break galaxies)
   - fitting: _not stated_
   - validation: Cross-matched to MUSE spectroscopic sample (UBR success 53%, 10/19)  
  > "The quality of the color selections is tested by cross-matching the catalogue of LBG candidates to the spectroscopic sample of galaxies identified in MUSE" (Photometric selection of Lyman break galaxies)
4. **Build the MUSE spectroscopic galaxy sample**: SExtractor on the MUSE white-light image, spectra extracted in 2.5 R_Kron apertures, redshifts from Marz with confidence scores; at least two UV features required for high confidence  
  > "we run SExtractor in the MUSE white-light image, obtained by collapsing the datacube along the wavelength direction" (MUSE spectroscopic sample of galaxies); "We thus require at least two of the following stellar and interstellar absorption or nebular emission lines to be clearly recognizable in the rest-frame UV spectra" (MUSE spectroscopic sample of galaxies)
   - software: SExtractor, Marz
   - parameter: threshold=2.5, minarea=6 pixels, deblend_mincont=0.0001  
  > "i) threshold=2.5 rescaled by the RMS of the background to guarantee a uniform threshold across the FoV; ii) minarea=6 pixels" (MUSE spectroscopic sample of galaxies)
   - parameter: Linking window |dv| <= 1000 km/s from the quasar  
  > "we identify 21 galaxies with high-confidence spectroscopic redshifts lying within a line-of-sight separation" (MUSE spectroscopic sample of galaxies)
   - fitting: _not stated_
   - validation: Selection robust to a wider velocity window (|dv|<=2500 km/s adds <~10% sources)  
  > "found that the number of sources increases only marginally" (MUSE spectroscopic sample of galaxies)
5. **Assemble control-field samples**: Continuum-detected galaxies with high-confidence redshifts in public ~10 h MUSE cubes without bright z~3-3.5 quasars (MUSE-FIELD), plus a control sample from the MQN01 cube excluding |dv|<=1500 km/s  
  > "As a result, we identify 43 galaxies" (Control-field samples); "we also identified a control sample from our own MUSE datacube of the MQN01 including 11 continuum-detected galaxies" (Control-field samples)
   - fitting: _not stated_
   - validation: _not stated_
6. **Derive stellar mass, SFR and Av with SED fitting**: CIGALE with BC03 models, Chabrier IMF, Calzetti dust law, AGN (Fritz) and X-ray modules; solar metallicity and exponentially declining SFH adopted  
  > "We chose high-resolution (cite: BC03) stellar population models, (cite: Chabrier2003) initial mass function and (cite: Calzetti2000) dust law." (Galaxies’ physical properties and SED fitting)
   - software: CIGALE
   - parameter: Metallicity 0.20 (solar), 0.08 and 0.04 in separate runs, as written  
  > "We fixed both the stellar and the gas-phase metallicity to 0.20 (solar), 0.08 and 0.04 in separate runs." (Galaxies’ physical properties and SED fitting)
   - parameter: Uncertainties adopted: 0.2 dex on stellar mass and 0.3 dex on SFR  
  > "We adopted an uncertainty value of $0.2\rm\,dex$ for the stellar mass (cite: Conroy2013) and of $0.3\rm\,dex$ for the SFR." (Galaxies’ physical properties and SED fitting)
   - fitting: _not stated_
   - validation: Refit with MC-SPF; median differences 0.048 dex (mass) and 0.054 dex (SFR)  
  > "is $0.048\pm0.050\rm\,dex$ for the stellar mass and $0.054\pm0.055\rm\,dex$ for the star formation rate" (Appendix: Results from SED fitting)
7. **Measure the luminosity function and overdensity amplitude**: Cumulative R-band luminosity function of the 21 galaxies in nine magnitude bins, with Poisson errors, divided by the blank-field (MUSE-FIELD / Reddy 2009) luminosity function  
  > "within nine intervals of $\Delta M_{\rm R}=0.175\rm\,mag$ and associate uncertainties from Poisson statistics" (Luminosity Function and amplitude of the overdensity)
   - assumption: Same selection function across samples, no completeness correction applied  
  > "we assume the selection function to be the same across the samples and do not apply any completeness corrections to the above luminosity functions" (Luminosity Function and amplitude of the overdensity)
   - fitting: _not stated_
   - validation: Field normalisation consistent with Reddy et al. 2009  
  > "The luminosity functions of these two independent field samples are consistent with each other, both in shape and normalization." (Luminosity Function and amplitude of the overdensity)
8. **Measure quasar-galaxy and galaxy-galaxy correlation lengths**: Projected correlation function from observed over expected counts in radial bins, fitted with eq. 10 of Trainor et al. 2012 with the slope fixed  
  > "In each radial bin, we compute $w_{\rm GG,QG}(R)=(N_{\rm obs}/N_{\rm exp})-1$" (Clustering analysis); "We derive the correlation length by fitting the equation 10 from TS12 to the data." (Clustering analysis)
   - parameter: Slope fixed to 1.5 and 1.8  
  > "The slope, $\gamma$, is degenerate with the correlation length and therefore fixed to different values" (Clustering analysis)
   - assumption: Power-law 3D correlation function xi=(r/r0)^-gamma  
  > "the correlation functions are typically modelled by a power law" (Clustering analysis)
   - fitting: Fit to binned data; uncertainties from the 16th and 84th percentiles of bootstrap distributions  
  > "The uncertainties are obtained from the 16th and 84th percentiles of the bootstrap distributions." (Clustering analysis)
   - validation: Auto-correlation consistent with an upper limit from the MQN01 field with |dv|<=1500 km/s masked; MAGG cross-correlation measured for comparison  
  > "we proved this result to be consistent with upper limits for the auto-correlation of the galaxies identified in our field" (Clustering analysis)
9. **Compare star formation and stellar mass function with field samples**: Compare galaxies to main-sequence parametrisations (0.3 dex dispersion) and to the control-field sample (KS tests); cumulative stellar mass function compared to COSMOS2020 scaled by the overdensity  
  > "it is more informative to directly compare the properties of the galaxies in the overdensity to those included in a field sample with a similar selection function" (Galaxies’ star formation activity compared to the field)
   - parameter: KS test significant at 2 sigma for p<=0.05  
  > "by performing a KS test (significant at $2\sigma$ level for $p$-values$\leq0.05$)" (Galaxies’ star formation activity compared to the field)
   - parameter: Mass function errors: bootstrap over SED uncertainties 1000 times plus Poisson  
  > "we bootstrap varying the fiducial values within the uncertainties derived from the galaxies’ SED fitting for 1000 times" (Galaxies’ stellar mass function)
   - fitting: _not stated_
   - validation: _not stated_
10. **Relate galaxy properties to local overdensity**: Voronoi tessellation (one element per cell) for local density; Spearman rank correlation against SFR, stellar mass and sSFR; edge cells (7/21) excluded  
  > "Open cells at the edge of the FoV (7/21) are excluded from the analysis" (Connecting the local overdense environment to the galaxy properties)
   - parameter: Significance threshold p<=0.05  
  > "We require $p$-value$\leq0.05$ for a correlation to be significant at least at 2$\sigma$ confidence level." (Connecting the local overdense environment to the galaxy properties)
   - fitting: _not stated_
   - validation: _not stated_
11. **Map LBG overdensity on the 24x24 cMpc^2 FORS2 field**: Grid of cells normalised by volume and compared to the field density, oversampled and Gaussian smoothed; alignment tested with Nth-neighbour density (N=5) and random injections  
  > "The LBGs appear to be overdense ($\rho/\bar{\rho}\gtrsim1$) across the entire $\approx24\times24\,\rm cMpc^2$ FoV, even at large distances from the central quasar." (Probing the structure on larger scales)
   - parameter: N=5 neighbour estimator  
  > "We choose N=5." (Appendix: Alignment of the LBGs with the large-scale overdensity)
   - assumption: LBGs span the entire redshift range 3.0<z<3.5  
  > "Assuming the LBGs span the entire redshift range $3.0<z<3.5$" (Appendix: Alignment of the LBGs with the large-scale overdensity)
   - fitting: _not stated_
   - validation: Nth-neighbour estimator agrees with Voronoi for N>=5; random-position injections repeated 1,000 times  
  > "but the two methods turn out to be consistent for $N\geq5$" (Appendix: Alignment of the LBGs with the large-scale overdensity)

## Software

- **ESO MUSE pipeline** : Initial MUSE data reduction  
  > "The raw data were initially reduced with the ESO Muse pipeline (cite: Weilbacher2014)." (MUSE observations)
- **CubExtractor (CubEx; CubeFix, CubeSharp, CubeCombine)** 1.8: Post-processing of the MUSE cube  
  > "we post-process the final products using the CubExtractor (CubEx hereafter, (cite: DeBeer2023) and Cantalupo et al., in prep.) package, version 1.8, and its subroutines" (MUSE observations)
- **ESO pipeline recipes for FORS2** : FORS2 bias, flat and flux calibration  
  > "we used the ESO pipeline recipes for FORS2 (cite: Izzo2010) to apply standard bias, flat and flux calibrations" (FORS2 and HAWK-I mosaics)
- **photutils** : 2D background modelling and subtraction  
  > "The 2D background was locally modelled and subtracted using the python package photutils (cite: Bradley2023)." (FORS2 and HAWK-I mosaics)
- **scamp** : Astrometric alignment to Gaia DR3  
  > "by using the scamp package (cite: Bertin2006)" (FORS2 and HAWK-I mosaics)
- **swarp** : Combining FORS2 frames into a mosaic  
  > "combined into the large-scale mosaic using swarp (cite: Bertin2010)" (FORS2 and HAWK-I mosaics)
- **PSFEx** : PSF measurement across the FORS2 field  
  > "we used the software PSFEx (cite: Bertin2011)" (FORS2 and HAWK-I mosaics)
- **SExtractor** 2.24.2: Source detection and completeness tests in FORS2 and MUSE white-light images  
  > "as identified by SExtractor ((cite: Bertin1996), version 2.24.2)" (FORS2 and HAWK-I mosaics)
- **EsoRex / HAWK-I pipeline** EsoRex 3.13.6; HAWK-I recipes 2.4.13: HAWK-I reduction  
  > "ESO Pipeline recipes for HAWK-I imaging (version 2.4.13) implemented in EsoRex ((cite: EsoRex2015), version 3.13.6)" (FORS2 and HAWK-I mosaics)
- **DrizzlePac** : Registering the HAWK-I mosaic astrometry to Gaia  
  > "we registered the astrometry of the final mosaic to Gaia by using the DrizzlePac package" (FORS2 and HAWK-I mosaics)
- **Marz (M. Fossati fork)** : Spectroscopic redshift measurement  
  > "of Marz tool (cite: Hinton2016), which includes additional high-resolution templates suitable for high-redshift galaxies" (MUSE spectroscopic sample of galaxies)
- **CIGALE** 2022.1: SED fitting with AGN and X-ray components  
  > "we use the publicly available code CIGALE" (Galaxies’ physical properties and SED fitting)
- **MC-SPF** : Independent SED fit as a cross-check  
  > "using the Monte Carlo Spectro-Photometric Fitter" (Appendix: Results from SED fitting)
- **Astropy, NumPy, SciPy, Matplotlib** : Acknowledged as used in this work  
  > "Numpy (cite: Numpy2020), SciPy (cite: SciPy2020), and Matplotlib (cite: Matpltolib2007)" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| High-confidence spectroscopic galaxies within |dv|<=1000 km/s of the quasar | 21 | not stated | galaxies | 4 | we identify 21 galaxies with high-confidence spectroscopic redshifts lying within a line-of-sight separation |
| X-ray detected AGN among the MUSE galaxies | 5 | not stated | galaxies | 4 | We identified a total of five AGN detected in X-Ray, three of which are also CO(4–3) line emitters |
| UBR-selected LBGs at z~3.0-3.5 over 24x24 cMpc^2 | 535 | not stated | galaxies | 3 | As a result, we identified 535 $z\approx3.0-3.5$ LBGs across $24\times24\rm\,cMpc^2$. |
| Galaxies in MUSE-FIELD control sample | 43 | not stated | galaxies | 5 | As a result, we identify 43 galaxies |
| Overdensity of spectroscopic galaxies at M_R <= -19.25 mag | 53 | 17 | dimensionless | 7 | we measure an overdensity $\rho/\bar{\rho}=53\pm17$ at $M_{\rm R}\leq-19.25\rm\,mag$ |
| Overdensity of UBR-selected LBGs with spectroscopic z in MUSE FoV at M_R <= -19.25 mag | 24 | 14 | dimensionless | 7 | is $\rho/\bar{\rho}=24\pm14$ at $M_{\rm R}\leq-19.25\rm\,mag$ |
| Blank-field comoving density, color-selected LBGs | 2.4e-3 | 0.2e-3 | cMpc^-3 | 7 | $\bar{\rho}_{\rm LBGs}=(2.4\pm0.2)\times10^{-3}\rm\,cMpc^{-3}$ and $\bar{\rho}_{\rm spec-z}=(2.5\pm0.8)\times10^{-3}\rm\,cMpc^{-3}$ |
| Blank-field comoving density, MUSE spectroscopic sample | 2.5e-3 | 0.8e-3 | cMpc^-3 | 7 | $\bar{\rho}_{\rm LBGs}=(2.4\pm0.2)\times10^{-3}\rm\,cMpc^{-3}$ and $\bar{\rho}_{\rm spec-z}=(2.5\pm0.8)\times10^{-3}\rm\,cMpc^{-3}$ |
| Surface density excess of galaxies in the redshift bin closest to the quasar vs field | ~8 | not stated | dimensionless | 7 | the surface density of galaxies identified in the redshift bin closest to the quasar is a factor of $\approx8$ larger than the field |
| Quasar-galaxy cross-correlation length (gamma=1.8) | 15.71 | +1.79/-1.83 | h^-1 cMpc | 8 | we obtained a quasar-galaxy cross-correlation length of $r_0=15.71^{+1.79}_{-1.83}~h^{-1}{\rm cMpc}$ |
| Galaxy-galaxy auto-correlation length, UDF (gamma=1.8) | 3.54 | +1.05/-1.08 | h^-1 cMpc | 8 | galaxy-galaxy correlation length of $r_0=3.54^{+1.05}_{-1.08}~h^{-1}{\rm cMpc}$ for fixed $\gamma=1.8$ |
| Cross-correlation length in MAGG fields (gamma=1.5) | 3.8 | 0.8 | h^-1 cMpc | 8 | We derived a cross-correlation length of $r_0=(3.8\pm0.8)~h^{-1}\rm cMpc$ for fixed $\gamma=1.5$. |
| MQN01 cross-correlation length relative to Trainor et al. 2012 (|dv|<=1500 km/s) | ~3.2 | not stated | dimensionless | 8 | around the quasar is $\approx3.2$ times larger compared to TS12 |
| KS test p-value, sSFR distributions (MQN01 vs control) | ~0.01 | not stated | dimensionless | 9 | While the distributions of sSFR are unlikely drawn from the same parent one, $p-$value$\approx0.01$ |
| Number density of massive (M*>~10^10.5) star-forming galaxies vs blank field | 217 | +200/-183 | dimensionless | 9 | is $217^{+200}_{-183}$ times higher around the quasar than in a blank field |
| Excess of massive galaxies after accounting for the overdensity | 4 | +2/-3 | dimensionless | 9 | the presence of massive galaxies exceeds by a factor of $4^{+2}_{-3}$ the expectations for the field |
| Stellar mass function excess in the two bins at log(M*/Msun)>~10.5 after accounting for the overdensity | 4 and 24 | 2 and 11 | dimensionless | 9 | with $4\pm2$ and $24\pm11$ times more sources in the two bins at $\log(M_\star/M_\odot)\gtrsim10.5$ |
| Spearman test of SFR vs local overdensity, p-value | 0.29 | not stated | dimensionless | 10 | we do not observe any significant environmental effect on the star formation rate itself ($p-$value$\approx0.29$) |
| Spearman |rho| of stellar mass and sSFR vs local overdensity, p-value | |rho| >~ 0.45, p ~ 0.05 | not stated | dimensionless | 10 | ($/\rho_{\rm spearman}/\gtrsim0.45$ and $p$-value$\approx0.05$) |
| Median difference between CIGALE and MC-SPF stellar mass | 0.048 | 0.050 | dex | 6 | is $0.048\pm0.050\rm\,dex$ for the stellar mass and $0.054\pm0.055\rm\,dex$ for the star formation rate |

## Qualitative findings

- Star-forming galaxies around the quasar lie on the main sequence at z~3.25, with no significant offset  
  > "we do not observe any significant offset from the main sequence calibrated on blank fields at $z\approx3$ for the clustered galaxies" (Galaxies’ star formation activity compared to the field)
- LBG overdensity extends well beyond the MUSE field and shows a North-South orientation  
  > "show a preferential vertical orientation, which corresponds to the North-South direction on the sky" (Probing the structure on larger scales)

## Claim tuples

- H: Does the quasar sit in an overdensity of star-forming galaxies, and how strongly clustered is it? | E: Cumulative luminosity function of 21 MUSE spectroscopic galaxies compared with field, plus quasar-galaxy cross-correlation | R: Overdensity 53 +/- 17; cross-correlation length about 3.2 times that of Trainor et al. 2012 | F: Galaxies are more clustered, or live in a more massive structure, than around average quasars | **supported**
- H: Do galaxies in the overdensity differ from the field in star formation rate? | E: Compare SED-derived SFR and mass with main-sequence fits and a control field sample | R: No significant offset from the main sequence | F: Galaxies form stars at main-sequence rates | **supported**
- H: Is the structure richer in massive galaxies than the field? | E: Cumulative stellar mass function compared with COSMOS2020 scaled by the overdensity | R: About 4 times higher number density at log(M*/Msun)>=10.5 | F: Excess of massive galaxies | **partially**
- H: Does the overdensity extend beyond the MUSE field? | E: Map the density of UBR-selected LBGs over 24x24 cMpc^2 and test alignment | R: Overdensity along the North-South direction aligned with the Lyα nebula | F: Gaseous structure may extend for tens of cMpc | **partially**

## Reasoning

- Why this data: U, B and R bands chosen to avoid contamination from bright Lyα emission driven by the quasar  
  > "We carefully choose those photometric bands to avoid any possible contamination due to the presence of bright Ly$\alpha$ emission" (Photometric selection of Lyman break galaxies)
- Why this method: Control field with similar selection function used because main-sequence calibrations differ in selection and SFR estimates  
  > "it is more informative to directly compare the properties of the galaxies in the overdensity to those included in a field sample with a similar selection function" (Galaxies’ star formation activity compared to the field)
- Alternative: Different metallicities and star formation histories in CIGALE gave results consistent within 1 sigma; solar metallicity and exponentially declining SFH adopted  
  > "lead to results that are consistent within $1\sigma$ with each other" (Galaxies’ physical properties and SED fitting)
- How they decided it was enough: _not stated_
- Limitation (authors): Findings limited to one individual rare structure  
  > "our findings are limited to one individual and rare structure, which prevent us from generalizing them to the broader population of protoclusters" (Caveats and future prospects)
- Limitation (authors): Selection excludes passive and very red galaxies  
  > "our selection tends to exclude passive or extremely red galaxies" (Galaxies’ star formation activity compared to the field)
- Limitation (authors): Only a small area has MUSE spectroscopic confirmation  
  > "Only a small area of the MQN01 structure, as probed through our LBG survey, currently has MUSE coverage and thus spectroscopic confirmation." (Caveats and future prospects)
- Caveat (inferred, ours): Small samples (21 galaxies, 11 control galaxies) make the Spearman and KS results marginal (p ~ 0.05)
- Caveat (inferred, ours): Blank-field density is taken from a different set of fields with 10 h MUSE exposures, so the overdensity depends on that normalisation
- Caveat (inferred, ours): Redshift assignment is manual and subjective
- Caveat (inferred, ours): SED uncertainties are set to fixed 0.2 and 0.3 dex rather than propagated
- Caveat (inferred, ours): ALMA contributes only as a cross-match, so the paper does not test ALMA-based quantities itself

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA reduction details live in Pensabene et al. 2024
- Missing: MUSE-FIELD galaxy catalogue and redshifts not tabulated
- Missing: Chandra AGN catalogue and nebula work are in submitted or in-prep papers
- Missing: No scripts or catalogues released
- Data volume (inferred): ALMA data not processed here; MUSE (4 pointings, ~10 h each) plus FORS2/HAWK-I mosaics would be tens of GB
- Score (inferred): 2/5, ALMA use is a catalogue cross-match deferred to another paper, and key inputs (MUSE galaxy catalogue, Chandra AGN, field fits) are not released, though the statistical recipe and numeric results are well described.
- Rediscovery candidate: no, Data public status is not stated, the ALMA part is minor and deferred to another paper, and the recipe depends on unreleased catalogues.

## Links

- Method: (cite: Pensabene2024) (Describes the ALMA data and reduction)
- Method: (cite: Trainor2012) (Clustering formalism)
- Method: (cite: Wang2024_bigwheel) (JWST data reduction)
- Method: (cite: Lofthouse2020) (MAGG survey galaxy identification and CubEx use)
- Method: (cite: Bielby2019) (Redshift confidence scoring)
- Companion: (cite: Pensabene2024) (ALMA dusty galaxies and CO(4-3) emitters in the same field)
- Companion: Travascio et al., (submitted) (Chandra X-ray AGN overdensity)
- Companion: (cite: Borisova2016) (Discovery of the extended Lyα emission)
- Related: MQN01
- Related: MAGG survey
- Related: MUSEQuBES
- Related: MUSE GTO 0102.A-0448(A)
- Related: ESO programme 110.23ZX
- Related: HST PID 17065
- Related: JWST GO 1835

## Checks

```json
{
 "quotes": 116,
 "quotes_ok": 116,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 20,
 "numeric_problems": 0,
 "fill": {
  "facts": 133,
  "stated": 82,
  "rate": 0.617
 },
 "evidence_ok": true
}
```
