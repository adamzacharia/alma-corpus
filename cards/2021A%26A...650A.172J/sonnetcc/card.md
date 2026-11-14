# ALMA observations of doubly deuterated water: inheritance of water from the prestellar environment

`2021A&A...650A.172J` | Astronomy and Astrophysics 2021 | first author: Jensen, S. S. | arXiv: 2104.13411 | DOI: 10.1051/0004-6361/202140560

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: Determine the D2O column density and the D2O/HDO ratios in the inner warm envelope of the Class 0 protostars B335 and L483, and use them with HDO/H2O to test whether the water D/H ratio is inherited from the prestellar phase  
  > "We seek to determine the D$_2$O column density and derive the D$_2$O/HDO ratios in the warm region toward the low-mass Class 0 sources B335 and L483." (abstract)
- Target **B335**: coordinates phase center RA 19:37:00.89, Dec +07:34:09.5 (J2000)  
  > "19:37:00.89" (Observations); "+07:34:09.5 for B335, and" (Observations); z/distance _not stated_; distance from _not stated_
- Target **L483**: coordinates phase center RA 18:17:29.91, Dec -04:39:39.6 (J2000)  
  > "18:17:29.91" (Observations); "-04:39:39.6 for L483" (Observations); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2019.1.00720.S, 2017.1.00693.S
- bands: Band 7 for the D2O window (new data); additional spectral windows in Bands 5, 6 and 7 from Jensen et al. 2019 data  
  > "The spectral setup targeted the D$_2$O $1_{1,0}$–$1_{0,1}$ transition at 316.8119 GHz in the ALMA band 7." (Observations); "spectral coverage extends to several spectral windows in ALMA bands 5, 6, and 7." (Synthetic spectrum modeling)
- frequencies and spectral setup: D2O 1(1,0)-1(0,1) at 316.8119 GHz; imaged spectral windows have 1920 channels of 122 kHz (0.11 km/s)  
  > "The imaged spectral windows contain 1920 channels with a width of 122 kHz (0.11 km s$^{-1}$)." (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: Max baseline 697 m (L483), 784 m (B335); 42 antennas each  
  > "J1924$-$2914 | 697 | 42 | 4.5" (Table 1); "J1924$-$2914 | 784 | 42 | 8.3" (Table 1)
- angular resolution: Synthesized beam in the D2O spectral window 0.38 x 0.37 arcsec (B335), 0.56 x 0.46 arcsec (L483); abstract quotes <~0.5 arcsec (<~100 au)  
  > "The synthesized beam size in spectral window centered on the D$_2$O transition are $0.\!\!^{\prime\prime}38\times0.\!\!^{\prime\prime}37$ and $0.\!\!^{\prime\prime}56\times0.\!\!^{\prime\prime}46$ for B335 and L483, respectively." (Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: L483: 2019 October 29; B335: 2019 October 8  
  > "2019 October 29" (Table 1); "2019 October 8" (Table 1)
- pi or archival as stated: Cycle 7 PI program (PI Sigurd S. Jensen), plus additional spectral windows from the data of Jensen et al. 2019  
  > "The low-mass protostars B335 and L483 were observed with ALMA during Cycle 7 (PI: Sigurd S. Jensen, projectid: 2019.1.00720.S)." (Observations); "we also utilize additional spectral windows from the data presented in (cite: jensen2019) toward both sources" (Observations)
- Line: D2O 1(1,0)-1(0,1) (316.8119 GHz)
- Line: CH3OD (blended with D2O) not stated (316.7916 GHz (one of the potential blended components))
- Line: CH3OCH3 (blended with D2O) not stated (316.7904 GHz (one of the potential blended components))
- Line: HDO and H2(18)O not stated (from Jensen et al. 2019 spectral windows) (not stated)
- External data: Spectroscopic data for D2O, HDO and H2(18)O used to identify the lines  
  > "The spectroscopic data used to identify D$_2$O, HDO, H$_{2}^{18}$O are from (cite: D2O_ref), (cite: hdo_ref), and (cite: h218o_ref), respectively." (Observations) [from (cite: D2O_ref), (cite: hdo_ref), (cite: h218o_ref)]
- External data: Spectroscopic data for CH3OCH3 and CH3OD  
  > "spectroscopic data for CH$_3$OCH$_3$, and CH$_3$OD are from (cite: CH3OCH3_ref) and (cite: CH3OD_ref), respectively." (Observations) [from (cite: CH3OCH3_ref), (cite: CH3OD_ref)]
- External data: 16O/18O ratio of 560 to convert H2(18)O to H2O  
  > "adopting a ${}^{16}$O/${}^{18}$O ratio of 560 (cite: wilson1994)" (Observations) [from (cite: wilson1994)]
- External data: HDO column densities from the HDO transitions of Jensen et al. 2019 (1.9e17 cm-2 for B335 at Tex 220 K, source size 0.2 arcsec; 1.2e17 cm-2 for L483), and the HDO/H2(18)O data combined with D2O  
  > "The HDO transitions presented in (cite: jensen2019) give a HDO column density of $1.9\times10^{17}$ cm$^{-2}$ at the same excitation temperature" (Least-squares fitting) [from (cite: jensen2019)]
- External data: IRAS 2A D2O/HDO of ~1% (and D2O/H2O ~2e-5) used for comparison  
  > "Interferometric detections of D$_2$O on inner envelope scales prior to this work are limited to (cite: coutens2014), who found a high D$_2$O/HDO ratio of $\sim 1\%$" (Introduction) [from (cite: coutens2014)]
- External data: Comet 67P D2O/HDO and HDO/H2O from ROSINA used for comparison  
  > "They found D$_2$O/HDO $= (1.8\pm0.9)\times10^{-2}$ and HDO/H$_2$O $= (1.05\pm0.14)\times10^{-3}$" (Environmental and cometary discussion) [from (cite: altwegg2017)]
- Simulation/model as data: Furuya et al. 2017 2D axisymmetric chemical model, predicting fD2/fD1 ~10 for prestellar water and ~0.1 for in-disk water, used as comparison  
  > "Quantitatively, the model of (cite: furuya2017) shows that a f$_\mathrm{D2}$/f$_\mathrm{D1}$ ratio around $\sim10$ is formed in the prestellar phase" (Inheritance of water D/H ratio)
- Simulation/model as data: Jensen et al. 2021 3D MHD plus chemical models of water deuteration, used as comparison  
  > "(cite: jensen2021) studied the D/H ratio of water during the formation of several low-mass protostars in a dynamic 3D magnetohydrodynamics simulation of a molecular cloud region." (Inheritance of water D/H ratio)

## Processing

### Calibration

- pipeline or manual: ALMA pipeline calibration with CASA 5.6  
  > "Each dataset was pipeline-calibrated using casa 5.6 (cite: casa)." (Observations)
- casa version: CASA 5.6  
  > "Each dataset was pipeline-calibrated using casa 5.6 (cite: casa)." (Observations)
- pipeline version: _not stated_
- archive products used as is: L483: ALMA pipeline product used (self-cal gave no improvement); B335: self-calibrated data used  
  > "for L483, no improvement in S/N level was achieved, and therefore the ALMA pipeline product was preferred." (Observations)
- flux calibrator: _not stated_
- flux scale uncertainty: ~10% inherent ALMA flux density uncertainty  
  > "Overall, both methods agree, given the inherent flux density uncertainty of ALMA ($\sim10\%$)" (Least-squares fitting)
- self calibration: Phase self-calibration attempted with CASA 5.6 for both; successful for B335 (S/N improved ~25%), no improvement for L483  
  > "Subsequent phase self-calibration was attempted for each dataset with casa 5.6." (Observations); "For B335, self-calibration was successful with an improved signal-to-noise ratio (S/N) of $\sim 25\%$" (Observations)

### Imaging

- task: tclean  
  > "Imaging was performed with the tclean algorithm with a robust parameter of 0.5." (Observations)
- deconvolver: _not stated_
- weighting robust: robust = 0.5  
  > "Imaging was performed with the tclean algorithm with a robust parameter of 0.5." (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: sigma-clipping with statcont (uvcontsub in CASA judged challenging because of rich hot corino emission)  
  > "Continuum subtraction for each spectral window was performed using the sigma-clipping method with the statcont code presented in detail in (cite: statcont)." (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.38 x 0.37 arcsec (B335), 0.56 x 0.46 arcsec (L483) in the D2O spectral window  
  > "The synthesized beam size in spectral window centered on the D$_2$O transition are $0.\!\!^{\prime\prime}38\times0.\!\!^{\prime\prime}37$ and $0.\!\!^{\prime\prime}56\times0.\!\!^{\prime\prime}46$ for B335 and L483, respectively." (Observations)
- final rms: _not stated_

### Inherited from earlier work

- Additional spectral windows (bands 5, 6, 7) and their observational details come from the earlier ALMA data  
  > "this latter work gives a detailed description of those observations" (Observations) [from (cite: jensen2019)]
- HDO and H2(18)O detections/column densities combined with the new D2O to derive ratios  
  > "We combine the D$_2$O detections with previous detections of HDO and H$_{2}^{18}$O toward the sources to derive D$_2$O/HDO, D$_2$O/H$_2$O and HDO/H$_2$O ratios consistently." (Introduction) [from (cite: jensen2019)]
- Synthetic spectrum calculation method with an added optical depth correction  
  > "The synthetic spectrum was calculated following the methodology presented in (cite: moller2017) with the addition of an optical depth correction from (cite: goldsmith1999)." (Synthetic spectrum modeling) [from (cite: moller2017); (cite: goldsmith1999)]
- LTE column density from fitted line profile  
  > "The column density is estimated from the fitted line profile by assuming local thermodynamic equilibrium (LTE) (cite: mangum2015)." (Least-squares fitting) [from (cite: mangum2015)]
- CH3OD partition function scaled from the CH3(18)OH partition function  
  > "the current analysis relies on a partition function scaled from the CH$_{3}^{18}$OH partition function, similar to (cite: jorgensen2018)" (Observations) [from (cite: jorgensen2018)]
- Definition of isolated versus clustered protostars  
  > "Following the definitions of (cite: jensen2019), B335 and L483 are isolated protostars" (Environmental impact on the D/H ratio) [from (cite: jensen2019)]

### Not stated but needed to reproduce (our reading)

- Self-calibration details (solution intervals, reference antenna, number of iterations, which spectral windows or continuum selection used)
- Pipeline version and flux calibrator for each execution block (only bandpass and phase calibrators are tabulated)
- tclean cell size, image size, deconvolver, masks, niter and threshold, primary-beam correction, and the spectral windows and channel width of the final cubes
- statcont sigma-clipping parameters and the line-free channels or noise level
- Exact pixel position used for the single-pixel spectrum and the spectrum rms
- Which HDO and H2(18)O transitions and spectral windows from Jensen et al. 2019 were used, and the measured line parameters
- Name and implementation of the synthetic spectrum code (source size, source size for L483, line width and velocity inputs, list of lines excluded from chi2), and how the uncertainties on the ratios (e.g. 6.3 +/- 1.5 e-3) were computed
- Bounds and initial guesses for the Gaussian fits and how the Gaussian-fit ratio uncertainties were derived
- Beam filling factor and source size for L483 (a 0.2 arcsec source size is stated only for B335 HDO)
- Rest frequencies and spectroscopic parameters of the HDO and H2(18)O lines actually modeled

## Analysis recipe

1. **calibrate visibilities and attempt self-calibration**: ALMA pipeline calibration in CASA 5.6, then phase self-calibration attempted; kept for B335, pipeline product kept for L483  
  > "Each dataset was pipeline-calibrated using casa 5.6 (cite: casa)." (Observations); "for L483, no improvement in S/N level was achieved, and therefore the ALMA pipeline product was preferred." (Observations)
   - software: CASA 5.6
   - fitting: _not stated_
   - validation: S/N compared before and after self-calibration  
  > "For B335, self-calibration was successful with an improved signal-to-noise ratio (S/N) of $\sim 25\%$" (Observations)
2. **image continuum and line cubes**: tclean imaging with robust 0.5; continuum image at 302 GHz made for each source  
  > "Imaging was performed with the tclean algorithm with a robust parameter of 0.5." (Observations); "Toward each source, a continuum image at 302 GHz was created and compared with previous ALMA observations toward the sources." (Observations)
   - software: CASA 5.6, tclean
   - parameter: robust = 0.5  
  > "Imaging was performed with the tclean algorithm with a robust parameter of 0.5." (Observations)
   - fitting: _not stated_
   - validation: Continuum intensities and morphologies compared with previous interferometric observations and found consistent  
  > "The intensities and morphologies of the continuum images are consistent with previous interferometric observations of the sources" (Observations)
3. **subtract continuum**: statcont sigma-clipping continuum subtraction on each spectral window  
  > "Continuum subtraction for each spectral window was performed using the sigma-clipping method with the statcont code presented in detail in (cite: statcont)." (Observations)
   - software: statcont
   - fitting: _not stated_
   - validation: _not stated_
4. **extract spectra and identify lines**: Single-pixel spectrum at the continuum peak; lines identified with JPL, CDMS and Splatalogue; feature identified as D2O blended with two CH3OD transitions and possibly one CH3OCH3 transition  
  > "For the line analysis, we extracted the spectrum from a single pixel toward the continuum peak position for each source." (Observations); "The emission feature was identified as D$_2$O blended with two CH$_3$OD transitions and, potentially, one CH$_3$OCH$_3$ transition." (Results)
   - software: Splatalogue, JPL catalog, CDMS
   - fitting: _not stated_
   - validation: Identification consistent with the feature toward IRAS 2A  
  > "This identification is consistent with the observed feature toward IRAS 2A (cite: coutens2014)." (Results)
5. **fit synthetic spectrum to get column densities**: Synthetic LTE spectrum of D2O, CH3OD and CH3OCH3 (plus HDO and H2(18)O) over bands 5, 6, 7 with optical depth correction, fitted by chi2 minimization; Tex 220 K (B335) and 165 K (L483) derived from this model  
  > "The synthetic spectrum was calculated following the methodology presented in (cite: moller2017) with the addition of an optical depth correction from (cite: goldsmith1999)." (Synthetic spectrum modeling); "We adopted an excitation temperature of 220 K, which is derived from the synthetic spectrum" (Least-squares fitting)
   - software: synthetic spectrum code of Moller et al. 2017 (name not stated)
   - parameter: Unblended lines: B335 two CH3OD and four CH3OCH3; L483 three CH3OD and three CH3OCH3  
  > "For B335, two unblended transitions of CH$_3$OD and four unblended transitions of CH$_3$OCH$_3$ were identified." (Synthetic spectrum modeling); "For L483, three unblended transitions of CH$_3$OD and three unblended transitions of CH$_3$OCH$_3$ were identified." (Synthetic spectrum modeling)
   - assumption: Single excitation temperature and similar spatial extent for the three water isotopologs; 16O/18O = 560  
  > "under the assumption of a single excitation temperature and similar spatial extent for the three water isotopologs." (abstract); "adopting a ${}^{16}$O/${}^{18}$O ratio of 560 (cite: wilson1994)" (Observations)
   - fitting: chi2 minimization of data around emission lines; blended and highly optically thick lines excluded manually  
  > "The best fit was determined by $\chi^2$ minimization of the data around emission lines." (Synthetic spectrum modeling); "Blended lines and transitions with high optical thickness were manually excluded from the $\chi^2$ estimation." (Synthetic spectrum modeling)
   - validation: L483 model deviates from observed profile but D2O column density is robust to changes in the CH3OD and CH3OCH3 components  
  > "the D$_2$O column density is robust: changing the parameters of the CH$_3$OD and CH$_3$OCH$_3$ components has little impact on the D$_2$O abundance." (Synthetic spectrum modeling)
6. **fit Gaussian profiles for a second column density estimate**: Least-squares Gaussian fit (up to four components for B335, single Gaussians for L483), then LTE column density at the Tex from the synthetic model, with HDO column density from Jensen et al. 2019 data using a beam filling factor for B335  
  > "the line profiles were fitted using the least-squares method with the scipy routine curve_fit" (Least-squares fitting); "when a beam filling factor is applied for a source size of $0.\!\!^{\prime\prime}2$" (Least-squares fitting)
   - software: scipy curve_fit
   - parameter: Tex = 220 K (B335), 165 K (L483)  
  > "For L483, an excitation temperature of 165 K was used, which was derived from the synthetic spectrum model." (Least-squares fitting); "We adopted an excitation temperature of 220 K, which is derived from the synthetic spectrum" (Least-squares fitting)
   - assumption: LTE for water emission from the warm envelope  
  > "Both methods assume that water emission from the warm envelope is in LTE." (Least-squares fitting)
   - fitting: scipy curve_fit least squares; bounds from the HDO data and other non-blended lines; fourth Gaussian component not needed for B335; single Gaussians for L483 after double-peaked fits failed  
  > "Bounds on the fits were estimated from the HDO data, and other non-blended emission lines in the dataset." (Least-squares fitting); "Instead, single Gaussians were fitted to each transition, which provided reasonable fits" (Least-squares fitting)
   - validation: Compared with the synthetic-spectrum result; LTE validity supported by earlier radiative transfer and non-LTE comparisons  
  > "Evidently, the D$_2$O/HDO ratios toward B335 are somewhat higher when using the Gaussian fits, however both methods yield high D$_2$O/HDO ratios $\gtrsim 10^{-2}$." (Least-squares fitting); "found that the LTE approach is valid for these transitions" (Least-squares fitting)
7. **derive isotopolog ratios**: Combine N(D2O), N(HDO) and N(H2(18)O) (x560 for H2O) into D2O/HDO (fD2), HDO/H2O (fD1), fD2/fD1 and D2O/H2O  
  > "We denote HDO/H$_2$O as f$_\mathrm{D1}$ and D$_2$O/HDO as f$_\mathrm{D2}$, and use both terms interchangeably." (Introduction); "adopting a ${}^{16}$O/${}^{18}$O ratio of 560 (cite: wilson1994)" (Observations)
   - fitting: _not stated_
   - validation: Two independent methods agree within ALMA flux uncertainty (~10%) and fitting uncertainty (~10%)  
  > "Overall, both methods agree, given the inherent flux density uncertainty of ALMA ($\sim10\%$) and the uncertainties in the fitting ($\sim10\%$)." (Least-squares fitting)
8. **compare with models, literature and comets**: Compare fD2/fD1 with Furuya et al. 2017 and Jensen et al. 2021 models, IRAS 2A (Coutens et al. 2014), isolated versus clustered protostars and comet 67P  
  > "Quantitatively, the model of (cite: furuya2017) shows that a f$_\mathrm{D2}$/f$_\mathrm{D1}$ ratio around $\sim10$ is formed in the prestellar phase" (Inheritance of water D/H ratio); "For L483, B335, and IRAS 2A, the D$_2$O/H$_2$O is $9\times10^{-5}$, $4\times10^{-5}$, and $2\times10^{-5}$, respectively." (Environmental impact on the D/H ratio)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.6: pipeline calibration, phase self-calibration and imaging  
  > "Each dataset was pipeline-calibrated using casa 5.6 (cite: casa)." (Observations); "Subsequent phase self-calibration was attempted for each dataset with casa 5.6." (Observations)
- **tclean** : imaging with robust 0.5  
  > "Imaging was performed with the tclean algorithm with a robust parameter of 0.5." (Observations)
- **statcont** : sigma-clipping continuum subtraction of each spectral window  
  > "Continuum subtraction for each spectral window was performed using the sigma-clipping method with the statcont code presented in detail in (cite: statcont)." (Observations)
- **scipy (curve_fit)** : least-squares Gaussian fits of the line profiles  
  > "the line profiles were fitted using the least-squares method with the scipy routine curve_fit" (Least-squares fitting)
- **Splatalogue** : querying spectroscopic line databases for line identification  
  > "All querying was done through the Splatalogue interface" (Observations)
- **JPL and CDMS catalogs** : line identification  
  > "The emission lines presented in this work are identified using data from the Jet Propulsion Laboratory (cite: JPL) and the Cologne Database for Molecular Spectroscopy (cite: CDMS)." (Observations)
- **matplotlib** : listed as used by the paper (purpose not stated)  
  > "This paper makes use of matplotlib (cite: hunter2007) and scipy (cite: 2020SciPy-NMeth)." (Acknowledgements)
- **RADMC-3D** : temperature structure of envelopes in the cited Jensen et al. 2021 models (not run in this paper)  
  > "The temperature structure of the envelopes was calculated using the Monte Carlo radiative transfer code radmc-3d (cite: dullemond2012)." (Inheritance of water D/H ratio)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| N(D2O), B335, synthetic spectrum | 3.5e15 | not stated | cm^-2 | 5 | a synthetic model with $N$(D$_2$O) = $3.5\times10^{15}$ cm$^{-2}$ |
| N(CH3OD) and N(CH3OCH3), B335, synthetic spectrum | 2.5e17 and 1.3e17 | not stated | cm^-2 | 5 | $N$(CH$_3$OD) = $2.5\times10^{17}$ cm$^{-2}$, and $N$(CH$_3$OCH$_3$) = $1.3\times10^{17}$ cm$^{-2}$ |
| HDO/H2O, B335, synthetic spectrum | 6.3e-3 | 1.5e-3 | dimensionless | 5 | HDO/H$_2$O $= (6.3\pm1.5)\times10^{-3}$ and D$_2$O/HDO $= (1.4\pm0.1)\times10^{-2}$ for B335 |
| D2O/HDO, B335, synthetic spectrum | 1.4e-2 | 0.1e-2 | dimensionless | 5 | HDO/H$_2$O $= (6.3\pm1.5)\times10^{-3}$ and D$_2$O/HDO $= (1.4\pm0.1)\times10^{-2}$ for B335 |
| N(D2O), L483, synthetic spectrum | 1.1e15 | not stated | cm^-2 | 5 | $N$(D$_2$O) = $1.1\times10^{15}$ cm$^{-2}$ |
| N(CH3OD) and N(CH3OCH3), L483, synthetic spectrum | 1.7e17 and 7.9e16 | not stated | cm^-2 | 5 | $N$(CH$_3$OD) = $1.7\times10^{17}$ cm$^{-2}$, and $N$(CH$_3$OCH$_3$) = $7.9\times10^{16}$ cm$^{-2}$ |
| HDO/H2O, L483, synthetic spectrum | 4.0e-3 | 0.5e-3 | dimensionless | 5 | HDO/H$_2$O $= (4.0\pm0.5)\times10^{-3}$ and D$_2$O/HDO $= (1.0\pm0.2)\times10^{-2}$ |
| D2O/HDO, L483, synthetic spectrum | 1.0e-2 | 0.2e-2 | dimensionless | 5 | HDO/H$_2$O $= (4.0\pm0.5)\times10^{-3}$ and D$_2$O/HDO $= (1.0\pm0.2)\times10^{-2}$ |
| Tex derived from synthetic spectrum, B335 | 220 | not stated | K | 5 | We adopted an excitation temperature of 220 K, which is derived from the synthetic spectrum |
| Tex derived from synthetic spectrum, L483 | 165 | not stated | K | 5 | For L483, an excitation temperature of 165 K was used, which was derived from the synthetic spectrum model. |
| N(D2O), B335, Gaussian fit | 4.0e15 | not stated | cm^-2 | 6 | this method results in a D$_2$O column density of $4.0\times10^{15}$ cm$^{-2}$ |
| D2O/HDO, B335, Gaussian fit | 2.1e-2 | 0.6e-2 | dimensionless | 6 | This method then results in a D$_2$O/HDO ratio of $(2.1\pm0.6)\times10^{-2}$. |
| N(D2O), L483, Gaussian fit | 1.7e15 | not stated | cm^-2 | 6 | The fitted Gaussian profiles result in $N$(D$_2$O) = $1.7\times10^{15}$ cm$^{-2}$ |
| D2O/HDO, L483, Gaussian fit | 1.4e-2 | 0.4e-2 | dimensionless | 6 | yield D$_2$O/HDO $= (1.4\pm0.4)\times10^{-2}$ |
| fD2/fD1 = (D2O/HDO)/(HDO/H2O), L483 and B335 | ~2.5 (L483), ~2 (B335) | not stated | dimensionless | 7 | The derived f$_\mathrm{D2}$/f$_\mathrm{D1}$ ratios for L483 and B335 are $\sim$2.5 and $\sim$2, respectively. |
| D2O/H2O, L483 and B335 | 9e-5 (L483), 4e-5 (B335) | not stated | dimensionless | 7 | For L483, B335, and IRAS 2A, the D$_2$O/H$_2$O is $9\times10^{-5}$, $4\times10^{-5}$, and $2\times10^{-5}$, respectively. |

## Qualitative findings

- D2O emission is blended with CH3OD and possibly CH3OCH3 and is confined to the inner envelope  
  > "The emission feature was identified as D$_2$O blended with two CH$_3$OD transitions and, potentially, one CH$_3$OCH$_3$ transition." (Results); "The spatial extent of the D$_2$O and CH$_3$OD emission is confined to the inner envelope" (Results)
- Observed D2O/HDO in warm envelopes is similar to that of comet 67P  
  > "providing tentative evidence of a common chemical evolution of the water that sublimates in the warm envelope and water incorporated in comets and icy planetesimals" (Summary and outlook)

## Claim tuples

- H: D2O can be detected and its abundance measured in the inner warm envelopes of isolated Class 0 protostars | E: ALMA Band 7 observations of the D2O 1(1,0)-1(0,1) line toward B335 and L483, analysed with synthetic spectrum modeling and Gaussian fitting | R: D2O/HDO is (1.4 +/- 0.1)e-2 for B335 and (1.0 +/- 0.2)e-2 for L483 (synthetic spectrum) | F: D2O is detected toward both sources with D2O/HDO of order 1e-2 | **supported**
- H: Water in the warm envelope is inherited from the prestellar phase rather than reprocessed locally | E: Compare D2O/HDO with HDO/H2O (fD2/fD1) against the Furuya et al. 2017 and Jensen et al. 2021 models | R: fD2/fD1 is about 2 to 2.5, so D2O/HDO exceeds HDO/H2O by a factor of at least 2 | F: Strong indication of chemical inheritance of water from the prestellar phase to the inner warm envelope | **supported**
- H: Isolated protostars have higher water D/H than clustered ones | E: Compare D2O/H2O for L483, B335 (isolated) with IRAS 2A (clustered) | R: D2O/H2O is 9e-5 (L483), 4e-5 (B335) and 2e-5 (IRAS 2A) | F: The D2O abundances corroborate a higher D/H of water toward isolated protostars, but the sample is small | **partially**
- H: The water in warm envelopes is chemically linked to cometary water | E: Compare envelope D2O/HDO with comet 67P values from the literature | R: D2O/HDO in hot corinos is similar to the comet 67P value of ~1e-2 | F: Tentative evidence of a common chemical evolution of envelope and cometary water | **partially**

## Reasoning

- Why this data: Modeling suggests D2O/HDO versus HDO/H2O is a powerful probe of inheritance versus local formation of water  
  > "Recent modeling suggests that comparisons of the D$_2$O/HDO and HDO/H$_2$O ratios are a powerful way to trace the chemical evolution of water" (abstract)
- Why this method: statcont used for continuum subtraction because the rich hot corino emission made CASA uvcontsub challenging  
  > "We preferred to use this method because both sources display rich hot corino emission, which made continuum subtraction through the uvcontsub routine in casa challenging (cite: jorgensen2016)." (Observations)
- Alternative: CASA uvcontsub rejected in favour of statcont for continuum subtraction  
  > "which made continuum subtraction through the uvcontsub routine in casa challenging (cite: jorgensen2016)" (Observations)
- Alternative: Double-peaked Gaussians for all four potential L483 lines were tried and rejected in favour of single Gaussians  
  > "attempts to fit double-peaked Gaussians to all four potential emission lines did not produce good results" (Least-squares fitting)
- Alternative: A fourth Gaussian component for B335 was not included in the final fit  
  > "i.e., only three Gaussian profiles were included in the final fit" (Least-squares fitting)
- How they decided it was enough: _not stated_
- Limitation (authors): Heavy line blending makes the D2O column density estimate challenging  
  > "As the line is heavily blended, estimation of the column density is challenging" (Results)
- Limitation (authors): L483 synthetic fit deviates from the observed profile  
  > "For L483, the best-fit spectral model shows some deviation from the observed profile" (Synthetic spectrum modeling)
- Limitation (authors): Sample of sources is too small for definite conclusions on the environmental dichotomy  
  > "However, the sample size remains too small to draw definite conclusions and should be further expanded." (Environmental impact on the D/H ratio)
- Limitation (authors): Results depend on methodology and assumptions (column densities differ from Jensen et al. 2019)  
  > "The differences in the reported HDO/H$_2$O ratios in this work and in (cite: jensen2019) illustrate the dependence on the methodology and assumptions" (Least-squares fitting)
- Caveat (inferred, ours): Single-pixel spectrum plus an assumed common Tex and spatial extent for D2O, HDO and H2(18)O; the 0.2 arcsec HDO source size is applied without independent constraint
- Caveat (inferred, ours): Heavy blending with CH3OD and CH3OCH3 makes the D2O column dependent on the blend model; the two methods differ by up to ~50% in D2O/HDO
- Caveat (inferred, ours): Uncertainties (e.g. 0.1e-2 on D2O/HDO) look small relative to the method spread and do not clearly include Tex and source-size systematics
- Caveat (inferred, ours): HDO/H2O inputs come from different spectral windows and earlier data, so the ratios mix datasets and cleaning choices
- Caveat (inferred, ours): Only two sources, so the isolated versus clustered comparison rests on one IRAS 2A value from a different study

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Self-calibration and tclean parameters (solints, cell size, image size, masks, cleaning thresholds)
- Missing: statcont parameters and line-free channel choices
- Missing: Synthetic spectrum code and input parameters (source size, line widths, excluded lines) and the HDO/H2(18)O line list used
- Missing: Exact pixel used for the spectrum and how ratio uncertainties were computed
- Missing: Which Jensen et al. 2019 spectral windows are needed and their processing
- Data volume (inferred): Two Band 7 executions (42 antennas, 1920-channel windows) from 2019.1.00720.S plus Band 5-7 data from 2017.1.00693.S; likely tens of GB raw per project, a few GB for the calibrated spectral windows
- Score (inferred): 3/5, Project codes, CASA 5.6, robust 0.5, statcont, Tex values and tabulated column densities are given, but self-cal, imaging and synthetic-model inputs are missing and HDO/H2(18)O data come from an earlier paper.
- Rediscovery candidate: no, Public ALMA project codes and numeric results exist, but the synthetic spectrum code and the processing details are not complete enough to redo the recipe from the paper alone.

## Links

- Method: Jensen et al. 2019 (cite: jensen2019) (Describes the earlier band 5-7 observations and the HDO and H2(18)O column densities used here)
- Method: Moller et al. 2017 (cite: moller2017) (Synthetic spectrum methodology)
- Method: Sanchez-Monge et al. 2018 (cite: statcont) (statcont continuum subtraction)
- Method: Mangum & Shirley 2015 (cite: mangum2015) (LTE column density from line profile)
- Companion: Jensen et al. 2021 (cite: jensen2021) (3D MHD plus chemical models of water deuteration compared to these observations)
- Companion: Coutens et al. 2014 (cite: coutens2014) (Earlier D2O detection toward NGC1333 IRAS 2A used as comparison)
- Related: 2017.1.00693.S (data of Jensen et al. 2019, listed in the acknowledgements)

## Checks

```json
{
 "quotes": 125,
 "quotes_ok": 125,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 16,
 "numeric_problems": 0,
 "fill": {
  "facts": 106,
  "stated": 72,
  "rate": 0.679
 },
 "evidence_ok": true
}
```
