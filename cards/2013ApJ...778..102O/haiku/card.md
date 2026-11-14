# An Intensely Star-forming Galaxy at z ~ 7 with Low Dust and Metal Content Revealed by Deep ALMA and HST Observations

`2013ApJ...778..102O` | The Astrophysical Journal 2013 | first author: Ouchi, Masami | arXiv: 1306.3572 | DOI: 10.1088/0004-637X/778/2/102

Card schema 1.0 | model claude-haiku-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, star_formation
- Question: Does the luminous z=6.595 galaxy Himiko contain hidden dust and low-metallicity ISM, as probed by deep ALMA 1.2 mm continuum and [CII] 158 micron upper limits, and what powers its extended Lyman alpha nebula?  
  > "We seek to use the cold dust continuum and measures from ALMA to understand its dust content and gas phase metallicity." (Introduction)
- Target **Himiko**: coordinates _not stated_; z/distance z=6.595  
  > "for a luminous ($m_{\rm UV}=25$) galaxy, 'Himiko', at a redshift z=6.595" (abstract); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00115.S
- bands: Band 6 (1.2 mm)  
  > "we carried out deep ALMA Band 6 observations in 2012 July 15, 18, 28, and 31" (ALMA)
- frequencies and spectral setup: 4 spectral windows of 1875 MHz: LSB 250.24 and 252.11 GHz, USB 265.90 and 267.78 GHz; line targeted in lowest LSB window  
  > "265.90 and 267.78 GHz in USB with a bandwidth of 1875 MHz" (ALMA)
- continuum bandwidth: 19.417 GHz total (sum of 4 spectral windows)  
  > "over the the total bandwidth of 19.417 GHz whose 7.5 GHz is sampled" (ALMA)
- arrays: 16 12m-antenna array (ALMA)  
  > "with 16 12m-antenna array under the the extended configuration of 36-400m baseline" (ALMA)
- configurations: extended configuration  
  > "under the the extended configuration of 36-400m baseline" (ALMA)
- baselines: 36-400 m  
  > "extended configuration of 36-400m baseline" (ALMA)
- angular resolution: FWHM beam 0.82 x 0.58 arcsec, PA 79.5 deg (final image)  
  > "The FWHM beam size of the final image is" (ALMA)
- max recoverable scale: _not stated_
- sensitivity: 1-sigma noise 17.4 uJy/beam (continuum, 19.417 GHz); 83.3 uJy/beam (line, 200 km/s channel)  
  > "over the the total bandwidth of 19.417 GHz whose 7.5 GHz is sampled" (ALMA); "Although the ALMA data reach a" (ALMA)
- time on source: 3.17 hours total on-source integration  
  > "The total on-source integration time was 3.17 hours." (ALMA)
- observing dates: 2012 July 15, 18, 28, and 31  
  > "we carried out deep ALMA Band 6 observations in 2012 July 15, 18, 28, and 31" (ALMA)
- pi or archival as stated: PI-led observations as stated ('we carried out'); ALMA data ID given as 2011.0.00115.S  
  > "we carried out deep ALMA Band 6 observations" (ALMA)
- Line: [CII] not stated (1900.54 GHz (157.74 micron rest-frame))
- Other facility **HST WFC3-IR**: Deep J125, H160 and medium-band F098M imaging (program 12265)  
  > "We carried out deep HST/WFC3-IR broad-band" (HST); "These observations are associated with program #12265." (Acknowledgments)
- Other facility **Spitzer IRAC (SEDS, SpUDS)**: 3.6 and 4.5 micron SEDS photometry; 5.8, 8.0, 24 micron SpUDS photometry from Ouchi et al. 2009a  
  > "we use the very deep Spitzer/IRAC SEDS data" (Spitzer)
- Other facility **Subaru telescope**: Discovery optical survey and Lyman alpha narrowband (NB921) imaging  
  > "This source was identified from an extensive 1 deg$^2$ optical survey for $z=6.6$ galaxies in the UKIDSS/UDS field conducted with the Subaru telescope." (Introduction)
- Other facility **Keck DEIMOS**: Spectroscopic redshift confirmation  
  > "The redshift was subsequently confirmed spectroscopically using Keck/DEIMOS." (Introduction)
- Other facility **UKIDSS/UDS DR8**: JHK total magnitudes  
  > "and $JHK$ DR8 data from the UKIDSS/UDS survey" (Improved Physical Properties from the Near-Infrared SED)
- External data: Local [CII]-SFR scaling relation used as comparison  
  > "the correlation with the star formation rate (SFR) (cite: delooze2011)" (ISM metallicity from Emission) [from (cite: delooze2011)]
- External data: Local starburst SFR-L(FIR) relation used to convert L_FIR to SFR(FIR)  
  > "assuming the local starburst SFR-L(FIR) relation of (cite: kennicutt1998)" (The Low Dust and Metal Content of Himiko) [from (cite: kennicutt1998)]
- External data: Lower-redshift SMG stellar masses used for comparison (about 1/10 of Himiko's mass)  
  > "the stellar mass of Himiko is only about 1/10th that of many submm galaxies (SMGs) at $z\sim 3$ (cite: chapman2005)" (Improved Physical Properties from the Near-Infrared SED) [from (cite: chapman2005)]
- External data: HFLS3 at z=6.34 L[CII]/L_FIR and CII-SFR position used for comparison  
  > "Figure [6] also shows that HFLS3 at $z=6.3$ (cite: riechers2013) follows the local scaling relation." (ISM metallicity from Emission) [from (cite: riechers2013)]
- External data: Dust temperature constraints from Herschel and local samples used to set the T_d range  
  > "Based on the Herschel measurements, (cite: lee2012) find that the average dust temperature is $\sim 30$ K" (Far Infrared SED) [from (cite: lee2012)]
- External data: Optical photometry (B, V, R, i', z', NB921, F098M-era data) from earlier Subaru study  
  > "Measurements obtained in (cite: ouchi2009a)." (Total Magnitudes and Fluxes of Himiko) [from (cite: ouchi2009a)]
- Simulation/model as data: Stellar synthesis models of Bruzual & Charlot 2003 with Calzetti 2000 dust attenuation, Salpeter IMF, used for SED fitting  
  > "using the stellar synthesis models of (cite: bruzual2003) with dust attenuation formulate given by (cite: calzetti2000)." (Improved Physical Properties from the Near-Infrared SED)
- Simulation/model as data: Stellar and nebular photoionization models of Raiter et al. 2010 compared with beta and EW0  
  > "we compare $\beta$ and $EW_0$ for the entire Himiko system and the various clumps with the stellar and nebular models of (cite: raiter2010)" (UV Spectral Slopes on the Spatially Resolved Images)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Neptune and Callisto (absolute flux scale)  
  > "The absolute flux scale was established by observations of Neptune and Callisto." (ALMA)
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
- line free channels: Continuum averaged over LSB 249.30-253.05 GHz and USB 264.96-268.71 GHz, excluding the line-affected range (exact channels not stated)  
  > "We averaged fluxes over the two spectral windows of LSB (249.30-253.05 GHz or 1.203-1.185mm) and USB (264.96-268.71 GHz or 1.131-1.116mm) in the range of frequency free from the line." (ALMA)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Line data rebinned to 166 MHz (200 km/s) channels  
  > "We rebin our data to a resolution of 166 MHz" (ALMA)
- final beam: 0.82 x 0.58 arcsec, PA 79.5 deg  
  > "The FWHM beam size of the final image is" (ALMA)
- final rms: 17.4 uJy/beam continuum (1-sigma); 83.3 uJy/beam per 200 km/s channel (line)  
  > "over the the total bandwidth of 19.417 GHz whose 7.5 GHz is sampled" (ALMA)

### Inherited from earlier work

- Far-infrared luminosity from optically thin graybody with beta_d=1.5 and T_d=40 K, following earlier dust-temperature choices  
  > "Assuming an optically thin graybody of modified blackbody radiation with a dust emissivity power-law spectral index of" (Far Infrared SED) [from (cite: eales1989; klaas1997)]
- SED fitting performed in the same manner as the earlier study, including nebular prescriptions  
  > "undertake $\chi^2$ fitting of a range of stellar synthesis models in the same manner as (cite: ono2010b)" (Improved Physical Properties from the Near-Infrared SED) [from (cite: ono2010b)]
- Nebular continuum and line prescriptions, metallicity-dependent  
  > "following the metallicity-dependent prescriptions presented in (cite: schaerer2009; ono2010b)." (Improved Physical Properties from the Near-Infrared SED) [from (cite: schaerer2009; ono2010b)]
- Escape fraction treatment (f_esc free parameter) following earlier work  
  > "If we allow $f_{\rm esc}$ to be a free parameter, following (cite: ono2012) we find no change from the model above" (Improved Physical Properties from the Near-Infrared SED) [from (cite: ono2012)]
- Spitzer aperture correction  
  > "use an aperture correction given in (cite: yan2005)." (Spitzer) [from (cite: yan2005)]
- Calzetti extinction with k_1600=10 and beta-A1600 relation  
  > "where $k_{1600}$ is $10$ (cite: ouchi2004a)." (UV Spectral Slopes on the Spatially Resolved Images) [from (cite: ouchi2004a; meurer1999)]
- Total magnitude aperture correction for UKIDSS/UDS photometry  
  > "and the aperture correction in the same manner as (cite: ono2010b)." (Total Magnitudes and Fluxes of Himiko) [from (cite: ono2010b)]

### Not stated but needed to reproduce (our reading)

- CASA version and whether reduction was pipeline or manual
- Imaging task, weighting/robust value, cell size and image size for the continuum and line cubes
- Deconvolution and masking settings used to reach the 1-sigma noise values
- Exact channel ranges used for continuum averaging and for line-free estimation
- Bandpass and phase calibrator flux densities and flux scale uncertainty
- Definition of the continuum flux-density aperture and noise per beam versus per pixel used for the 3-sigma limit
- Spatial and spectral extent of the 600 km/s search window and how the 3-sigma line limit was computed
- Multidrizzle drizzle kernel and parameters for the F098M and J125 PSF matching
- SED fitting code, parameter grid spacing, priors and error estimation method
- Calculation details for converting the 1.2 mm limit to L_FIR (flux conversion and K-correction)

## Analysis recipe

1. **Reduce ALMA Band 6 data and derive noise levels**: Reduce ALMA data in CASA, rebin to 200 km/s, average continuum over line-free windows, measure 1-sigma noise for continuum and line  
  > "Our data were reduced with Common Astronomy Software Applications (CASA) package." (ALMA)
   - software: CASA
   - parameter: Rebin to 166 MHz (200 km/s); beam 0.82 x 0.58 arcsec  
  > "We rebin our data to a resolution of 166 MHz" (ALMA)
   - assumption: Bandpass calibrators 3c454.3 and J0423-013; phase calibrator J0217+017  
  > "We used 3c454.3 and J0423-013 for bandpass calibrators and J0217+017 for a phase calibrator." (ALMA)
   - fitting: _not stated_
   - validation: Continuum image checked for a 2 sigma peak and negative pixels at 2-3 sigma level  
  > "However, there are a series of negative pixels nearby that correspond to the $2-3 \sigma$ level per beam." (ALMA)
2. **Measure 3-sigma upper limits on 1.2 mm continuum and [CII] line**: Non-detection: 3-sigma upper limits from continuum and 200 km/s channel noise  
  > "We conclude therefore that Himiko remains undetected in the 1.2mm continuum" (ALMA)
   - software: CASA
   - parameter: Search window over 600 km/s around z=6.595  
  > "We searched for a signal of over 600 km $^{-1}$ around the frequency corresponding to $z_{\rm Ly\alpha}=6.595$." (ALMA)
   - fitting: _not stated_
   - validation: Noise peaks at 3 sigma near 0 and -200 km/s judged not reliable counterparts  
  > "However, neither of these sources is a reliable counterpart of Himiko." (ALMA)
3. **Convert the 1.2 mm limit to a far-infrared luminosity limit**: Optically thin graybody with beta_d=1.5 and T_d=40 K integrated over 8-1000 micron, adopted as conservative limit  
  > "Because the larger assumed dust temperature" (Far Infrared SED)
   - parameter: beta_d=1.5; T_d=40 K  
  > "and a dust temperature of" (Far Infrared SED)
   - assumption: Dust temperature range considered 20-40 K; CMB lower limit gives T_d=21 K at z=6.595  
  > "this yields a lower limit of $T_d=21$ K." (Far Infrared SED)
   - assumption: Upper limit depends on assumed dust temperature and beta_d  
  > "Note that these upper limits depend upon the assumed dust temperature and" (Far Infrared SED)
   - fitting: _not stated_
   - validation: Alternative T_d=25 K and 60 K and beta_d=0 and 2 cases tabulated  
  > "For $T_d=25$K and $T_d=60$K, the $3\sigma$ upper limit luminosities" (Far Infrared SED)
4. **Photometry of HST clumps and UV slopes**: Aperture photometry (0.4 arcsec for clumps and D, 2 arcsec for total) on PSF-matched HST images; beta from J125-H160 color  
  > "We perform 0''.4-diameter aperture photometry for the clumps A-C and location D" (HST)
   - software: WFC3, MULTIDRIZZLE, PyRAF
   - parameter: Matched PSF 0.19 arcsec FWHM; pixfrac 0.5; pixel scale 0.05132 arcsec  
  > "in the multidrizzle processing we chose a final_pixfrac=0.5 and pixel scale of 0''.05132." (HST)
   - assumption: Flat f_nu continuum used for continuum-break color  
  > "Assuming the continuum spectrum is flat" (HST)
   - fitting: beta from equation (J125 - H160) / (2.5 log(lambda1/lambda2)) - 2  
  > "We calculate $\beta$ via" (UV Spectral Slopes on the Spatially Resolved Images)
   - validation: Clump A detected at about 20 sigma in J125 and H160; bias of +0.1 in beta considered  
  > "the UV slope is quite reliable." (UV Spectral Slopes on the Spatially Resolved Images)
5. **Fit stellar population (mass, age, SFR, E(B-V))**: chi-squared grid fitting of BC03 models with Calzetti dust, constant and exponential SFH, with and without nebular emission  
  > "Applying models of constant and exponentially-decaying star-formation histories" (Improved Physical Properties from the Near-Infrared SED)
   - parameter: Salpeter IMF 0.1-100 Msun  
  > "We adopt Salpeter initial mass function" (Improved Physical Properties from the Near-Infrared SED)
   - parameter: Metallicity Z=0.02-1.0 Zsun; E(B-V)=0-1; age 1-810 Myr  
  > "we search for the best-fit model in a parameter space of" (Improved Physical Properties from the Near-Infrared SED)
   - parameter: Pure stellar fit with constant SFR and Z=0.2 Zsun  
  > "For a constant star-formation rate history with no nebular emission and a fixed metallicity of" (Improved Physical Properties from the Near-Infrared SED)
   - assumption: All ionizing photons produce nebular lines (f_esc=0) in the nebular models  
  > "we assume that all ionizing photons lead to nebular emission lines corresponding to an escape fraction" (Improved Physical Properties from the Near-Infrared SED)
   - fitting: Reduced chi-squared minimization over model grid; reduced chi2 3.1 (pure stellar) and 1.6 (stellar+nebular)  
  > "the best fit has a more satisfactory reduced" (Improved Physical Properties from the Near-Infrared SED)
   - validation: Pure stellar fit judged not very satisfactory; nebular model adopted to address 3.6 micron discrepancy  
  > "the fit itself is not very satisfactory" (Improved Physical Properties from the Near-Infrared SED)
6. **Compare [CII] and FIR upper limits with local scaling relations**: Place [CII] upper limit on the de Looze et al. 2011 L[CII]-SFR relation; compute SFR(FIR) from L_FIR limit  
  > "presents the upper limit to the luminosity in the context of" (ISM metallicity from Emission)
   - parameter: SFR(FIR) from Kennicutt 1998 relation applied to L_FIR<8e10 Lsun  
  > "we obtain $SFR({\rm FIR})<14 M_\odot$yr$^{-1}$" (The Low Dust and Metal Content of Himiko)
   - assumption: SFR of local comparison galaxies derived in a similar manner to Himiko  
  > "are derived in a similar manner to that for Himiko" (ISM metallicity from Emission)
   - fitting: _not stated_
   - validation: Discussion of selection biases and dust-free vs dusty SFR tracers  
  > "In this sense, the analysis of (cite: delooze2011) is perhaps more relevant as a prediction of what to expect for Himiko." (ISM metallicity from Emission)
7. **Test whether Lyman alpha is powered by photoionization by star formation**: Compare beta and EW0 for system and clumps with photoionization models of Raiter et al. 2010  
  > "Figure [9] shows that the data points of Himiko fall on the tracks of star-formation photoionization models" (UV Spectral Slopes on the Spatially Resolved Images)
   - parameter: Stellar extinction E(B-V)_s=0.1 used for arrow sizes  
  > "the arrow size in $\beta$ for the stellar extinction of" (UV Spectral Slopes on the Spatially Resolved Images)
   - assumption: Salpeter IMF assumed in Raiter et al. models  
  > "where Salpeter IMF is assumed." (UV Spectral Slopes on the Spatially Resolved Images)
   - fitting: _not stated_
   - validation: Conclusion robust to E(B-V)_s=0.15 correction  
  > "However, the conclusion is robust even if we adopt a moderate dust extinction of" (Nature of Himiko)

## Software

- **CASA** : Reduction of the ALMA Band 6 data (continuum and line imaging)  
  > "Our data were reduced with Common Astronomy Software Applications (CASA) package." (ALMA)
- **WFC3 and MULTIDRIZZLE on PyRAF** : Reduction of HST WFC3 images (drizzling to pixel scale 0.05132 arcsec)  
  > "The various WFC3 images were reduced with WFC3 and MULTIDRIZZLE packages on PyRAF." (HST)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 1.2 mm continuum 3-sigma upper limit | 52.1 | 3-sigma upper limit | uJy | 2 | We conclude therefore that Himiko remains undetected in the 1.2mm continuum |
| 1.2 mm continuum 1-sigma noise | 17.4 | not stated | uJy/beam | 1 | over the the total bandwidth of 19.417 GHz whose 7.5 GHz is sampled |
| [CII] line flux 3-sigma upper limit (200 km/s channel) | 250.0 | 3-sigma upper limit | uJy | 2 | The corresponding $3\sigma$ upper limit for is $250.0\mu$Jy in a channel width of 200 km s$^{-1}$. |
| [CII] line luminosity 3-sigma upper limit | <5.4e7 | 3-sigma upper limit | Lsun | 2 | We likewise provide a strong upper limit for the flux of $158\mu$m, |
| Far-infrared luminosity 3-sigma upper limit (8-1000 micron, T_d=40 K, beta_d=1.5) | <8.0e10 | 3-sigma upper limit | Lsun | 3 | we obtain a $3\sigma$ upper limit of $L_{\rm FIR}<8.0\times 10^{10} L_\odot$ integrated over $8-1000\mu$m. |
| Minimum dust temperature from CMB heating at z=6.595 | 21 | not stated | K | 3 | this yields a lower limit of $T_d=21$ K. |
| SFR from FIR upper limit (Kennicutt 1998) | <14 | upper limit | Msun/yr | 6 | we obtain $SFR({\rm FIR})<14 M_\odot$yr$^{-1}$ |
| [CII] deficit relative to local L[CII]-SFR relation | 30 | not stated | dimensionless | 6 | the deficit amounts to a factor |
| UV-luminosity SFR (no dust correction) | 30 +/- 2 | 2 | Msun/yr | 4 | the UV-luminosity SFR of |
| Total Lyman alpha luminosity (NB921) | 38.4 +/- 1.5 | 1.5 | 10^42 erg/s | 4 | Total$^{a}$ / 2815.4 / 2790.4 |
| UV continuum slope beta, entire system | -2.00 | 0.57 | dimensionless | 4 | We obtain beta=-2.00 +/- 0.57 for the entire system of Himiko |
| UV continuum slope beta, clump A | -2.84 | 0.32 | dimensionless | 4 | Clump A presents a very blue UV slope |
| UV continuum slope beta, clump B | -2.04 | 0.47 | dimensionless | 4 | Clumps B and C have |
| UV continuum slope beta, clump C | -2.22 | 0.28 | dimensionless | 4 | Clumps B and C have |
| Lyman alpha rest-frame equivalent width, clump A | 68 | +14/-13 | Angstrom | 4 | Clump A shows intense Ly alpha emission with a rest-frame equivalent width |
| Stellar mass, stellar+nebular best fit | 1.5 | +0.2/-0.2 (x10^10) | Msun | 5 | we derive a reduced stellar mass of |
| Stellar mass, pure stellar best fit | 3.0 | +0.4/-0.6 (x10^10) | Msun | 5 | we find our best-fit model has a stellar mass of |
| SFR, pure stellar best fit | 98 | +/-2 | Msun/yr | 5 | a SFR of $98^{+2}_{-2}M_\odot$yr$^{-1}$ |
| SFR, stellar+nebular best fit | 100 | +/-2 | Msun/yr | 5 | but similar values for the SFR of |
| Dust extinction E(B-V), best fit | 0.15 | not stated | mag | 5 | and extinction of $E(B-V)=0.15$ with a reduced |
| Stellar age, stellar+nebular best fit | 1.8 | +0.2/-0.2 (x10^8) | yr | 5 | a younger stellar age of |
| Specific SFR, pure stellar | 3.3 +/- 0.5 x 10^-9 | 0.5 (x10^-9) | yr^-1 | 5 | We estimate a specific star-formation rate, sSFR, defined by a ratio of star-formation rate to stellar mass to be |
| Specific SFR, stellar+nebular | 6.7 +/- 0.9 x 10^-9 | 0.9 (x10^-9) | yr^-1 | 5 | We estimate a specific star-formation rate, sSFR, defined by a ratio of star-formation rate to stellar mass to be |
| Lyman alpha escape fraction upper limit | <0.2 | upper limit | dimensionless | 5 | If we allow $f_{\rm esc}$ to be a free parameter, following (cite: ono2012) we find no change from the model above |

## Qualitative findings

- Himiko has submm emission comparable with or weaker than local dwarf irregulars with far lower SFR  
  > "Himiko’s submm emission is comparable with or weaker than that of local dwarf irregulars with far lower star-formation rates" (The Low Dust and Metal Content of Himiko)
- Himiko is not gravitationally lensed  
  > "Thus, we conclude that Himiko is not a gravitational lensed system." (Nature of Himiko)
- The Lyman alpha halo is unlikely to be heated by an AGN  
  > "Thus, we conclude the Ly$\alpha$ halo is unlikely to be heated by an active galactic nucleus." (Nature of Himiko)

## Claim tuples

- H: Himiko contains little dust, so its ALMA 1.2 mm continuum should be weak. | E: Deep ALMA Band 6 continuum imaging at 1.2 mm with 3-sigma non-detection limit converted to L_FIR. | R: 3-sigma continuum upper limit of 52.1 uJy and L_FIR < 8.0e10 Lsun. | F: Himiko has very weak millimeter emission and a low dust content. | **supported**
- H: The ISM of Himiko is metal poor, so its [CII] emission should be weak relative to the SFR scaling relation. | E: [CII] 158 micron line search over 600 km/s, comparison of the upper limit with the local L[CII]-SFR relation. | R: [CII] 3-sigma limit L < 5.4e7 Lsun, about a factor 30 below the local relation. | F: Himiko appears to be a very metal-poor system; the authors judge metal-poor gas the most likely cause among four possibilities. | **partially**
- H: The extended Lyman alpha nebula is powered by star formation rather than an AGN or gravitational lensing. | E: HST morphology and photometry, Spitzer data, X-ray and spectral constraints, and radiative transfer comparison. | R: Three L* clumps, blue UV slope of clump A (beta=-2.84), no point source found, no lensing signature. | F: The Lyman alpha halo is powered by photoionization from star formation; AGN and lensing are excluded. | **supported**
- H: The stellar population of Himiko, with its SFR, can be constrained by deeper HST and Spitzer photometry. | E: chi-squared SED fitting with BC03 and Calzetti dust, Salpeter IMF, with and without nebular emission. | R: M* = 1.5e10 (nebular) to 3.0e10 Msun (pure stellar); SFR about 100 Msun/yr; E(B-V)=0.15. | F: Himiko is a luminous, massive star-forming galaxy with comparable sSFR to z~3 LBGs and SMGs. | **partially**

## Reasoning

- Why this data: Deep ALMA continuum and [CII] plus HST morphology used to constrain dust and metallicity of a single well-studied source.  
  > "We seek to use the cold dust continuum and measures from ALMA to understand its dust content and gas phase metallicity." (Introduction)
- Why this method: Set the spectral setup to target the [CII] line in the lowest LSB window and extend the USB to higher frequency where dust continuum is brighter.  
  > "Because a brighter dust continuum is expected at a higher frequency in the 1.2mm regime, we extended our upper sideband" (ALMA)
- Alternative: Four possibilities for weak [CII]: AGN hard spectrum, high PDR density, low metallicity, large dust column; AGN rejected and low metallicity favoured  
  > "This discovery indicates the following four possibilities" (Discussion)
- Alternative: Lensing rejected based on morphology and Keck velocity gradient  
  > "We can further reject this supposition given there are clear asymmetries in the outermost images" (Nature of Himiko)
- How they decided it was enough: Adopted the largest-temperature (least restrictive) case as a conservative limit.  
  > "Because the larger assumed dust temperature" (Far Infrared SED)
- Limitation (authors): The SED fit is not very satisfactory with reduced chi2 of about 3.1 in the pure stellar case  
  > "the fit itself is not very satisfactory" (Improved Physical Properties from the Near-Infrared SED)
- Limitation (authors): Upper limits depend on assumed dust temperature and beta_d  
  > "Note that these upper limits depend upon the assumed dust temperature and" (Far Infrared SED)
- Caveat (inferred, ours): Continuum and line noise values are given without the imaging weighting, cell size or deconvolution settings that set them.
- Caveat (inferred, ours): The L_FIR limit rests on an assumed graybody with beta_d=1.5 and T_d=40 K; a different T_d changes it by a factor of about 10.
- Caveat (inferred, ours): SED fit with nebular emission uses f_esc=0 and a single constant-SFH model; mass range spans a factor of two.
- Caveat (inferred, ours): [CII] deficit interpretation depends on the adopted local relation and mixes dusty and dust-free SFR tracers.

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: Paper names ALMA data ID 2011.0.00115.S; no archive product list stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00115.S." (Acknowledgments)
- Code: _not stated_
- Missing: CASA version and full imaging recipe (task, weighting, cell and image size, deconvolution)
- Missing: Exact line-free channel selection and continuum averaging
- Missing: Calibrator flux densities and flux scale uncertainty
- Missing: Exact definition of the 3-sigma limit calculation and conversion to L_FIR
- Missing: HST multidrizzle drizzle kernel and PSF-matching kernel
- Missing: SED fitting code, grid spacing and error estimation method
- Data volume (inferred): Small: one ALMA Band 6 continuum image and one line cube for a single target, plus a few HST and Spitzer images.
- Score (inferred): 3/5, Key numbers and SED recipe are given, but the ALMA imaging settings and SED code details are missing.
- Rediscovery candidate: no, Data public status is not stated, so the rediscovery conditions are not met.

## Links

- Method: (cite: bruzual2003) Bruzual & Charlot 2003 (Stellar synthesis models used for SED fitting)
- Method: (cite: calzetti2000) Calzetti et al. 2000 (Dust attenuation law used for SED fitting)
- Method: (cite: delooze2011) de Looze et al. 2011 (Local L[CII]-SFR scaling relation used for comparison)
- Method: (cite: ono2010b) Ono et al. 2010 (Chi-squared SED fitting procedure followed in this paper)
- Method: (cite: raiter2010) Raiter et al. 2010 (Photoionization models for Lyman alpha equivalent width comparison)
- Companion: (cite: ouchi2009a) Ouchi et al. 2009a (Discovery of Himiko with Subaru, Keck and Spitzer data)
- Companion: (cite: riechers2013) Riechers et al. 2013 (HFLS3 at z=6.34, the other well-studied source at this redshift)
- Related: UKIDSS Ultra Deep Survey (UDS)
- Related: Spitzer SEDS and SpUDS surveys
- Related: HST program 12265

## Checks

```json
{
 "quotes": 120,
 "quotes_ok": 120,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 24,
 "numeric_problems": 0,
 "fill": {
  "facts": 110,
  "stated": 83,
  "rate": 0.755
 },
 "evidence_ok": true
}
```

## Figures

- **Figure 1** (moment_map, 1 panel(s), data): ALMA 259 GHz (1.16 mm) continuum intensity map around Himiko, with sigma-level contours marking the non-detection at the galaxy position.
  - axes: x: Right ascension (J2000) [hh:mm:ss]; y: Declination (J2000) [dd:mm:ss]; colour: continuum intensity [not labelled]; contours: significance (sigma levels, -3 to +3) [sigma]
  - supports step 1
  - read off the plot: approx. 1-sigma flux 17.4 uJy/beam (from caption); approx. no significant continuum source at Himiko position (white cross)
- **Figure 2** (channel_maps, 6 panel(s), data): ALMA [CII] velocity channel maps of Himiko in 200 km/s bins centred from -600 to +400 km/s, showing no significant line emission at the galaxy position.
  - axes: x: Right ascension (J2000) [hh:mm:ss]; y: Declination (J2000) [dd:mm:ss]; colour: line intensity per channel [not labelled]; contours: significance [sigma]; channel: velocity relative to z=6.595 [CII] [km/s]
  - supports step 1
  - validation: Checks for [CII] line emission at the Himiko position across velocity channels, giving upper limits.
  - read off the plot: approx. channel centres -600, -400, -200, 0, +200, +400 km/s; approx. 1-sigma 83.3 uJy/beam per channel (from caption)
- **Figure 3** (other, 1 panel(s), data): Colour composite of Himiko with HST/WFC3 J125 and H160 continuum in blue and green and Subaru NB921 Lyman-alpha emission in red, with continuum clumps A, B and C labelled.
  - axes: scale: angular scale [arcsec (1 arcsec bar)]
  - supports step 4
  - read off the plot: approx. scale bar 1 arcsec
- **Figure 4** (other, 9 panel(s), data): Multi-band image grid of Himiko (5 by 5 arcsec cutouts) in HST F098M, J125 and H160, Spitzer 3.6 and 4.5 micron, and Subaru Lyman-alpha continuum-subtracted with contours, marking apertures for clumps A-D and total photometry.
  - axes: x: relative position [arcsec]; y: relative position [arcsec]; colour: surface brightness [not labelled]; contours: Lyman-alpha intensity [not labelled]
  - supports step 1
  - read off the plot: approx. aperture diameter 0.4 arcsec for clumps and 2 arcsec for total magnitudes (from caption)
- **Figure 5** (sed, 1 panel(s), data, literature_comparison, model): Observed-frame optical to far-infrared SED of Himiko compared with redshifted local galaxy templates (Arp220, M82, M51, NGC6946, dwarf irregulars), with the ALMA Band 6 upper limit.
  - axes: x: observed wavelength [micron]; y: flux density f_nu [mJy]; templates: local galaxy SED templates at z=6.595 [not labelled]
  - supports step 2
  - validation: Compares Himiko's photometry and ALMA upper limit with redshifted local galaxy SED templates to constrain dust emission.
  - read off the plot: approx. ALMA 1100 micron upper limit ~0.05 mJy; approx. Arp220 peak ~50 mJy near 600 micron; approx. Spitzer 3.6 micron flux ~1e-3 mJy
  - reproduction target
- **Figure 6** (scatter_or_relation, 1 panel(s), data, literature_comparison): [CII] luminosity versus star formation rate for local galaxies with the local scaling relation and scatter band, with Himiko's 3-sigma [CII] upper limit and HFLS3 plotted.
  - axes: x: log SFR [log(M_sun/yr)]; y: log [CII] luminosity [log(erg/s)]
  - supports step 2
  - validation: Places the Himiko [CII] upper limit against the local L[CII]-SFR relation to test consistency with low [CII] luminosity.
  - read off the plot: approx. Himiko upper limit log L[CII] ~41.3 erg/s at log SFR ~2.0; approx. HFLS3 at log SFR ~3.5
  - reproduction target
- **Figure 7** (sed, 2 panel(s), data, model): Optical to near-infrared SED of Himiko from deep HST and Spitzer data with best-fit stellar synthesis models with and without nebular lines.
  - axes: x: observed wavelength [micron]; y: flux density f_nu [uJy]; model: best-fit stellar synthesis SED [not labelled]
  - supports step 3
  - validation: Fits stellar population models to the broadband photometry to derive SFR, stellar mass and extinction.
  - read off the plot: approx. HST WFC3 fluxes ~0.3-0.4 uJy; approx. Spitzer IRAC 4.5 micron flux ~1 uJy; approx. best-fit SFR 100 M_sun/yr (from caption); approx. best-fit E(B-V) 0.15 (from caption)
  - reproduction target
- **Figure 9** (scatter_or_relation, 1 panel(s), data, model, literature_comparison): UV continuum slope beta versus rest-frame Lyman-alpha equivalent width for the whole system and clumps A, B and C, compared with Raiter et al. (2010) starburst model tracks at several metallicities.
  - axes: x: rest-frame Lyman-alpha equivalent width [Angstrom]; y: UV continuum slope beta [dimensionless]; models: Raiter et al. model tracks (PopIII, Z=1e-5, 0.01, 0.2 Zsun) [not labelled]
  - supports step 4
  - validation: Compares measured clump UV slopes and Lyman-alpha equivalent widths with model predictions for different metallicities and dust.
  - read off the plot: approx. whole system beta ~ -2.0 at EW ~80 A; approx. Clump A beta ~ -2.05 at EW ~3 A; approx. Clump C beta ~ -2.8 at EW ~70 A
  - reproduction target
- **Figure 10** (scatter_or_relation, 1 panel(s), data, literature_comparison): Ratio of [CII] to FIR luminosity as a function of FIR luminosity for local normal galaxies, ULIRGs and high-redshift SF and AGN populations, with Himiko's FIR upper limit and an excluded shaded region.
  - axes: x: FIR luminosity [log(L_sun)]; y: [CII] to FIR luminosity ratio [log(L[CII]/L_FIR)]
  - supports step 2
  - validation: Places Himiko's FIR upper limit against literature [CII]/FIR ratios to test whether its [CII] deficit is consistent with known populations.
  - read off the plot: approx. Himiko limit log L_FIR ~11 L_sun; approx. Himiko log(L[CII]/L_FIR) ~ -2.1; approx. HFLS3 log(L[CII]/L_FIR) ~ -3.3 at log L_FIR ~13.4
  - reproduction target
