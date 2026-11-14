# Direct detection of quasar feedback via the Sunyaev-Zeldovich effect

`2019MNRAS.483L..22L` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Lacy, Mark | arXiv: 1811.05023 | DOI: 10.1093/mnrasl/sly215 | **HELD OUT (benchmark)**

Card schema 1.0 | model claude-haiku-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, galaxy_clusters_and_sz
- Question: Can the Sunyaev-Zeldovich effect from the thermal wind bubble of the hyperluminous quasar HE 0515-4414 be directly detected with ALMA, and what does it imply for the wind energetics and lifetime?  
  > "we present evidence that we have made the first detection of such a bubble, associated with the hyperluminous quasar HE 0515-4414" (abstract)
- Target **HE 0515-4414 (quasar)**: coordinates 05:17:07.614 -44:10:55.64 (QSO position in point-source table)  
  > "05:17:07.614 | -44:10:55.64" (Table: Point source emission model subtracted from the ALMA data); "HE 0515-4414 ($z=1.71$; Reimers et al. 1998)" (Introduction); "We assume a $\Lambda$ CDM cosmology with" (Introduction); z/distance z=1.71  
  > "05:17:07.614 | -44:10:55.64" (Table: Point source emission model subtracted from the ALMA data); "HE 0515-4414 ($z=1.71$; Reimers et al. 1998)" (Introduction); "We assume a $\Lambda$ CDM cosmology with" (Introduction); distance from Reimers et al. 1998 (redshift); cosmology H0=70 km/s/Mpc, Omega_M=0.3, Omega_Lambda=0.7 as stated  
  > "05:17:07.614 | -44:10:55.64" (Table: Point source emission model subtracted from the ALMA data); "HE 0515-4414 ($z=1.71$; Reimers et al. 1998)" (Introduction); "We assume a $\Lambda$ CDM cosmology with" (Introduction)

## Data provenance

- ALMA projects: 2016.1.00309.S
- bands: ALMA Band 4 (SZE peak near 130 GHz)  
  > "which lies in ALMA band-4." (ALMA)
- frequencies and spectral setup: Four 2 GHz basebands centered at 133, 135, 145 and 147 GHz; single pointing centered on the quasar  
  > "four 2 GHz basebands centered at 133, 135, 145, and 147 GHz." (ALMA)
- continuum bandwidth: 4 x 2 GHz basebands  
  > "four 2 GHz basebands centered at 133, 135, 145, and 147 GHz." (ALMA)
- arrays: _not stated_
- configurations: Two scheduling blocks: one execution in a relatively large configuration (point-source contribution), and 14 executions in a compact configuration (SZE sensitivity)  
  > "one executed once in a relatively large configuration" (ALMA); "one executed 14 times in a compact configuration" (ALMA)
- baselines: _not stated_
- angular resolution: Approximately 0.7 arcsec FWHM (large configuration) and 2.7 arcsec FWHM (compact configuration)  
  > "one executed once in a relatively large configuration" (ALMA); "one executed 14 times in a compact configuration" (ALMA)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Authors' own observations ('Our observations'); PI/program ownership not stated  
  > "Our observations were of a single pointing centered on the quasar" (ALMA)
- Line: Continuum (thermal SZE) not stated (not stated)
- Line: H-beta (optical, HST grism; used for black hole mass) H-beta (not stated)
- Line: O III (optical, HST grism; C1 component) [OIII] (not stated)
- Other facility **Spitzer Space Telescope**: 3.6 and 4.5 micron imaging (DDT program PID 13221)  
  > "Spitzer observations were obtained in a DDT program (PID 13221)." (Optical and Infrared); "The standard pipeline products were used." (Optical and Infrared)
- Other facility **Gemini Observatory**: GMOS Z-band and FLAMINGOS-2 J and Ks imaging (program GS-2017B-FT-12)  
  > "Gemini fast turnaround observations were obtained in program GS-2017B-FT-12 using the GMOS and FLAMINGOS-2 instruments." (Optical and Infrared)
- Other facility **Hubble Space Telescope**: WFC3 F140W, F160W imaging and G141 grism spectra (program 14594, P.I. R. Bielby)  
  > "HST observations of the field of HE 0515-4414 from program 14594 (P.I. R. Bielby) using the WFC3 instrument were recently made available in the HST archive." (Optical and Infrared)
- Other facility **2MASS**: J-band photometry used for the continuum flux in the black hole mass estimate  
  > "2MASS J-band data (Skrutskie et al. 2006)" (Optical and Infrared)
- External data: Redshift of HE 0515-4414 (z=1.71)  
  > "HE 0515-4414 ($z=1.71$; Reimers et al. 1998)" (Introduction) [from Reimers et al. 1998 (ref: 1998A&A...334...96R)]
- External data: Black hole mass formulation (M_BH approx 4.3e10 Msun from Hbeta width and J-band continuum)  
  > "using the formulation of Bennert et al. (2015)" (Optical and Infrared) [from Bennert et al. 2015 (ref: 2015ApJ...809...20B)]
- External data: SUMSS 843 MHz non-detection (<6 mJy) used to derive L_1.4 < 6e25 W/Hz  
  > "undetected in the cm radio" (Thermal Plus Kinetic SZE Model) [from Mauch et al. 2003 (ref: 2003MNRAS.342.1117M)]
- External data: Poor cluster at z=0.28 in the field, estimated mass 6e12 Msun, judged too small to contribute to the SZE  
  > "Bielby et al. (2017) find a poor cluster at" (Results and Discussion); "The estimated mass of this cluster" (Results and Discussion) [from Bielby et al. 2017 (ref: 2017MNRAS.468.1373B)]
- External data: 2MASS J-band continuum flux used for black hole mass  
  > "2MASS J-band data (Skrutskie et al. 2006)" (Optical and Infrared) [from Skrutskie et al. 2006 (ref: 2006AJ....131.1163S)]
- External data: Strong-shock and bubble-expansion model for the bubble (RS11 model), y profile correction of 8%  
  > "Comparison to the $y$ profile in Figure 1 in RS11 shows that the gentle pressure increase in the outer regions of the bubble leads to a correction of 8%." (Interpretation of the SZE Signal) [from Rowe & Silk 2011 (RS11) (ref: 2011MNRAS.412..905R)]
- External data: Enthalpy content of largest ICM cavities from radio jets, used for comparison  
  > "This is similar to the enthalpy content of the largest cavities in the ICM produced by radio jets" (Thermal SZE Model) [from Birzan et al. 2008 (ref: 2008ApJ...686..859B)]
- Simulation/model as data: Self-similar wind bubble model (RS11) used as the expansion model for the conical SZE bubble; tSZE and tSZE+kSZE solutions compared  
  > "We base our treatment of the expansion of the wind bubble on the model in RS11" (Interpretation of the SZE Signal)

## Processing

### Calibration

- pipeline or manual: ALMA pipeline  
  > "Calibration of the data was performed with the ALMA pipeline." (Footnote 1 (ALMA section))
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: Amplitude calibration accuracy of approximately 5% (standard calibration strategy)  
  > "A standard calibration strategy was used resulting in an amplitude calibration accuracy of" (ALMA)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Natural weighting for the detection map; separate tapered image for the SZE signal (robust value not stated)  
  > "No clear signal was readily apparent in the naturally-weighted map" (ALMA); "so tapering was applied to improve the surface brightness sensitivity of the image" (ALMA)
- uv taper: Taper with beam matched to the size of the signal; taper parameters not stated  
  > "The taper with a beam best matched to the size of the signal" (ALMA)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Point-source models for the QSO and sources A1, A3, A5 subtracted in the uv-plane; no line-free channel selection stated (continuum-only data)  
  > "subtract the emission from the quasar itself, and also the three other bright" (ALMA); "the subtraction of point source models in the" (ALMA)
- line free channels: _not stated_
- primary beam correction: 12% correction for the primary beam response  
  > "After a 12% correction for the response of the primary beam, this peak value of the decrement becomes" (ALMA)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: Natural: 3.2 x 2.3 arcsec at PA 106 deg; tapered: 6.7 x 6.4 arcsec at PA 110 deg  
  > "produced an image with" (ALMA)
- final rms: Natural: 3.5 uJy/beam; tapered: 6.6 uJy/beam  
  > "No clear signal was readily apparent in the naturally-weighted map" (ALMA); "produced an image with" (ALMA)

### Inherited from earlier work

- Bubble expansion treated with the RS11 conical/self-similar model, which uses the self-similar stellar wind bubble solution of Weaver et al. (1977)  
  > "We base our treatment of the expansion of the wind bubble on the model in RS11, which uses the self-similar stellar wind bubble solution of Weaver et al. (1977)." (Interpretation of the SZE Signal) [from Rowe & Silk 2011 (RS11) (cite: 2011MNRAS.412..905R); Weaver et al. 1977 (ref: 1977ApJ...218..377W)]
- Calibration strategy and 5% amplitude accuracy taken from the ALMA technical handbook  
  > "A standard calibration strategy was used resulting in an amplitude calibration accuracy of" (ALMA) [from ALMA Technical Handbook (Cycle 4) cited in footnote 1]
- Thermal SZE intensity change equation  
  > "The change in the intensity of the CMB due to the SZE is given by (e.g. Sazonov & Sunyaev 1998)" (Interpretation of the SZE Signal) [from Sazonov & Sunyaev 1998 (ref: 1998AstL...24..553S)]
- Equipartition time between protons and electrons used to justify T = T_e  
  > "The equipartition time between protons and electrons is short" (Thermal Plus Kinetic SZE Model) [from Wong & Sarazin 2009 (ref: WS09)]
- Black hole mass estimate formulation  
  > "using the formulation of Bennert et al. (2015)" (Optical and Infrared) [from Bennert et al. 2015 (cite: 2015ApJ...809...20B)]
- Grism spectra extracted with aXe; broad-band images combined with astrodrizzle  
  > "The broad-band images were combined using astrodrizzle, and the aXe software (Kümmel et al. 2009) was used to extract the grism spectra." (Optical and Infrared) [from Kummel et al. 2009 (ref: 2009PASP..121...59K)]

### Not stated but needed to reproduce (our reading)

- Imaging software, task and version used to form the natural and tapered ALMA images (not named)
- Robust weighting value and exact uv-taper parameters (taper beam size) used for the tapered image
- Cell size, image size and deconvolution/cleaning setup for the ALMA maps
- Method and data used to fit or derive the point-source model fluxes subtracted from the uv data
- Whether the ALMA pipeline version and CASA version used for calibration are stated
- Flux calibrator, bandpass and phase calibration choices and any self-calibration
- Exact primary beam model and how the 12% correction was applied
- Definition of the aperture and noise estimate behind the 3.5 sigma significance of the dip
- Adopted electron temperature T_e and gas density assumptions used to convert pressure to y
- Values of y_peak and the RS11 wind parameters used in the conical model, and the f_Omega normalisation details
- Extraction method for the peak decrement and the kSZE/tSZE split (fitting or analytic)
- Whether the ALMA data are public or proprietary and the archive product level used

## Analysis recipe

1. **Remove point sources from the ALMA data**: Point-source models for the QSO and three bright sources (A1, A3, A5) subtracted in the uv-plane; sources unresolved in the compact configuration data  
  > "Fortunately, all sources were unresolved in the smaller configuration data" (ALMA)
   - parameter: Point-source fluxes: QSO 66.2 uJy, A1 41.7 uJy, A3 21.8 uJy, A5 188.2 uJy  
  > "Point source emission model subtracted from the ALMA data" (Table: Point source emission model subtracted from the ALMA data)
   - assumption: Residual diffuse emission around A5 possibly remains  
  > "with the possible exception of a small amount of diffuse extended emission associated with the brightest source, A5." (ALMA)
   - fitting: _not stated_
   - validation: Residual diffuse emission from A5 flagged as possible contamination  
  > "with the possible exception of a small amount of diffuse extended emission associated with the brightest source, A5." (ALMA)
2. **Image the SZE signal with natural and tapered weighting**: Natural-weighted map for point-source sensitivity; tapered map matched to the signal size to improve surface-brightness sensitivity; dip measured SW of the quasar  
  > "so tapering was applied to improve the surface brightness sensitivity of the image" (ALMA)
   - parameter: Taper matched to signal size; taper parameters not stated  
  > "The taper with a beam best matched to the size of the signal" (ALMA)
   - fitting: _not stated_
   - validation: Decrement significant at the 3.5 sigma level  
  > "recovers an apparent dip of flux density of" (ALMA)
3. **Measure the peak SZE decrement**: Peak of the tapered-image dip, corrected for primary beam response  
  > "to the SW of the quasar position." (ALMA)
   - parameter: 12% primary beam correction  
  > "After a 12% correction for the response of the primary beam, this peak value of the decrement becomes" (ALMA)
   - assumption: Decrement is on one side only (SW of quasar)  
  > "Our detection appears on only one side of the quasar" (Abstract)
   - fitting: _not stated_
   - validation: _not stated_
4. **Convert the decrement to Compton y, pressure and bubble enthalpy (thermal model)**: Brightness temperature change from the peak decrement, Compton parameter from the thermal SZE spectrum, electron pressure from y and bubble radius, enthalpy energy of the bubble  
  > "For the observed peak decrement, this gives a Compton parameter" (Interpretation of the SZE Signal)
   - parameter: Average projected bubble radius r = 3.9 arcsec = 33 kpc; peak at 10.1 arcsec = 85 kpc; outer edge 12.8 arcsec = 108 kpc (beam-corrected)  
  > "The average projected radius of the bubble is" (Interpretation of the SZE Signal)
   - assumption: Equipartition of ions and electrons so T = T_e; total number density n = 1.92 n_e; enthalpy (5/2) n k T V as minimum energy  
  > "we assume equipartition of ions and electrons, so that" (Thermal SZE Model)
   - assumption: Pure thermal SZE (v_r/c negligible compared to thermal term)  
  > "We first consider a pure thermal SZE model" (Thermal SZE Model)
   - fitting: _not stated_
   - validation: _not stated_
5. **Constrain wind luminosity and lifetime with tSZE-only conical RS11 model**: Solve the RS11 radius relation and the y_max relation simultaneously for L_W and t using observed R and y_max; derive E_W, shock speed and post-shock temperature  
  > "we can estimate both" (Interpretation of the SZE Signal)
   - parameter: Cone half angle 30 deg; axis at 45 deg to line of sight; f_Omega = (1 - cos theta)/2 approx 0.067  
  > "We estimate the half angle of the cone in our system to be" (Interpretation of the SZE Signal)
   - parameter: Observed R approx 112 kpc (deprojected) and y_max approx 2.08e-5  
  > "Since we have observed values for both" (Interpretation of the SZE Signal)
   - assumption: Wind kinetic luminosity L_W of the observed SZE bubble is one-sided; energy doubles for two-sided outflow  
  > "Assumes an intrinsically one-sided outflow and should be doubled for a two-sided outflow." (Table: model parameters (tab:models))
   - assumption: Cooling negligible in the RS11 model; IGM density from cosmological bias and halo overdensity  
  > "The first is that cooling of the hot phase gas is negligible." (Interpretation of the SZE Signal)
   - fitting: Analytic solution of two equations with two unknowns (no sampler stated)  
  > "Equations (6) & (7) in RS11 imply that the outer radius of the SZE bubble is" (Interpretation of the SZE Signal)
   - validation: Total energy agrees fairly well across enthalpy, tSZE-only and kSZE+tSZE methods  
  > "the fair agreement in the total energy estimate between the three different methods" (Thermal Plus Kinetic SZE Model)
6. **Model the one-sided decrement as tSZE plus kSZE**: Add kinematic SZE term to y_max relation; solve with the same conical RS11 geometry; kSZE and tSZE contributions compared  
  > "Adding this kSZE term to the right side of Equation" (Thermal Plus Kinetic SZE Model)
   - parameter: Kinetic term adds to tSZE; lifetime almost twice the tSZE-only value; L_W factor 3-4 smaller  
  > "The wind luminosity is roughly a factor of 3-4 smaller" (Thermal Plus Kinetic SZE Model)
   - assumption: Approaching and receding halves of the outflow have tSZE and kSZE of same or opposite sign  
  > "In the receding half of the outflow (relative to the observer) the kZSE and tSZE contributions to the SZE are both of the same sign" (Thermal Plus Kinetic SZE Model)
   - fitting: _not stated_
   - validation: Strong-shock assumption checked against halo sound speed; no SZE from quasar after 20 arcsec taper  
  > "we detect no SZE from the quasar" (Thermal Plus Kinetic SZE Model)
7. **Check cooling and equipartition timescales**: Cooling time from average pressure (n_e) using RS11 cooling prescription, bremsstrahlung dominated; equipartition time compared to bubble age  
  > "The average pressure in the bubble implies" (Thermal Plus Kinetic SZE Model)
   - parameter: n_e approx 0.16 cm^-3  
  > "The average pressure in the bubble implies" (Thermal Plus Kinetic SZE Model)
   - assumption: Bremsstrahlung-dominated cooling  
  > "(dominated by bremsstrahlung)" (Thermal Plus Kinetic SZE Model)
   - fitting: _not stated_
   - validation: Cooling time approx 0.6 Gyr so cooling can be ignored; equipartition time approx 4000 yr  
  > "suggesting that cooling effects can be ignored" (Thermal Plus Kinetic SZE Model)
8. **Test whether a starburst could power the wind**: Star formation rate needed to supply the observed wind with mass loading factor unity and wind velocity 1000 km/s  
  > "assuming a mass loading factor of unity and a wind velocity of 1000 km s" (Thermal Plus Kinetic SZE Model)
   - parameter: SFR approx 500 Msun/yr sustained for 1.3e8 yr; stellar mass approx 7e10 Msun  
  > "a star formation rate of approximately" (Thermal Plus Kinetic SZE Model)
   - fitting: _not stated_
   - validation: Starburst origin cannot be ruled out without SFR constraints  
  > "we cannot currently rule out a starburst origin" (Thermal Plus Kinetic SZE Model)

## Software

- **ALMA pipeline** : Calibration of the ALMA data  
  > "Calibration of the data was performed with the ALMA pipeline." (Footnote 1 (ALMA section))
- **IRAF (Gemini IRAF package, GMOS data reduction package)** : Bias subtraction, flat fielding and coaddition of GMOS images; dark subtraction, flat fielding and combination of FLAMINGOS-2 images  
  > "We used the standard GMOS data reduction package in IRAF to subtract the bias, apply the flat field, and coadd the final images." (Optical and Infrared)
- **astrodrizzle** : Combining HST WFC3 broad-band images  
  > "The broad-band images were combined using astrodrizzle" (Optical and Infrared)
- **aXe** : Extraction of HST G141 grism spectra  
  > "the aXe software (Kümmel et al. 2009) was used to extract the grism spectra." (Optical and Infrared)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Peak SZE decrement, tapered image, before primary beam correction | -23.1 | not stated (significant at 3.5 sigma) | uJy | 2 | recovers an apparent dip of flux density of |
| Peak SZE decrement after primary beam correction | -25.9 | not stated | uJy | 3 | After a 12% correction for the response of the primary beam, this peak value of the decrement becomes |
| Brightness temperature change at peak | -37.7 | not stated | microKelvin | 4 | corresponds to a brightness temperature change of |
| Average projected bubble radius | 3.9 arcsec = 33 | not stated | kpc | 4 | The average projected radius of the bubble is |
| Actual (deprojected) outer radius of bubble | 112 | not stated | kpc | 5 | so that the actual radius is about 112 kpc |
| Compton parameter y at peak | 2.08e-5 | not stated | dimensionless | 4 | For the observed peak decrement, this gives a Compton parameter |
| Electron pressure in bubble | 1.26e-11 | not stated | Pa | 4 | The electron pressure in the bubble is then |
| Total energy injected into bubble (enthalpy, thermal model; value as printed) | 2.67e53 (r/33 kpc)^2 (y/2.08e-5) | not stated | W (as printed) | 4 | the total energy injected into the bubble by the outflow is |
| Wind kinetic luminosity, tSZE only | 1.70e11 | not stated | Lsun | 5 | tSZE only / 1.70 / 8.13 / 1.68 / 807 / 0.91 / 0.95 |
| Bubble age, tSZE only | 8.13e7 | not stated | yr | 5 | tSZE only / 1.70 / 8.13 / 1.68 / 807 / 0.91 / 0.95 |
| Wind energy, tSZE only | 1.68e53 | not stated | J | 5 | tSZE only / 1.70 / 8.13 / 1.68 / 807 / 0.91 / 0.95 |
| Shock speed, tSZE only | 807 | not stated | km/s | 5 | tSZE only / 1.70 / 8.13 / 1.68 / 807 / 0.91 / 0.95 |
| Shock temperature, tSZE only | 0.91e7 | not stated | K | 5 | tSZE only / 1.70 / 8.13 / 1.68 / 807 / 0.91 / 0.95 |
| Wind kinetic luminosity, tSZE plus kSZE | 0.429e11 | not stated | Lsun | 6 | tSZE plus kSZE / 0.429 / 12.87 / 0.67 / 510 / 0.36 / 1.50 |
| Bubble age, tSZE plus kSZE | 12.87e7 | not stated | yr | 6 | tSZE plus kSZE / 0.429 / 12.87 / 0.67 / 510 / 0.36 / 1.50 |
| Wind energy, tSZE plus kSZE | 0.67e53 | not stated | J | 6 | tSZE plus kSZE / 0.429 / 12.87 / 0.67 / 510 / 0.36 / 1.50 |
| Shock speed, tSZE plus kSZE | 510 | not stated | km/s | 6 | tSZE plus kSZE / 0.429 / 12.87 / 0.67 / 510 / 0.36 / 1.50 |
| kSZE to tSZE ratio, tSZE plus kSZE model | 1.50 | not stated | dimensionless | 6 | tSZE plus kSZE / 0.429 / 12.87 / 0.67 / 510 / 0.36 / 1.50 |
| Fraction of decrement due to kSZE in tSZE plus kSZE model | 60 | not stated | % | 6 | In this model, about 60% (40%) of the SZE decrement is due to the kSZE (tSZE). |
| Wind luminosity as fraction of bolometric luminosity (abstract) | 0.01 | not stated | % of bolometric luminosity | 5 | constrain the wind luminosity to the lower end of theoretical predictions |
| Wind luminosity as fraction of bolometric luminosity (Discussion, current power) | 0.003 | not stated | % of bolometric luminosity | 5 | it is only a small fraction |
| Wind energy as fraction of radiative energy of black hole, eta=0.1 | 0.01 (0.02 if two-sided) | not stated | % | 5 | (0.02% if the wind is two-sided), is still low compared to the models. |
| Cooling time of bubble | 0.6 | not stated | Gyr | 7 | This corresponds to a cooling time of |
| Bubble age (abstract estimate) | 0.1 | not stated | Gyr | 6 | the age we estimate for the bubble |
| Black hole mass of HE 0515-4414 | 4.3e10 | not stated | Msun | 0 | to estimate the mass of the black hole |
| Equipartition time between protons and electrons | 4000 | not stated | yr | 7 | The equipartition time between protons and electrons is short |
| Radio luminosity upper limit at 1.4 GHz | 6e25 | not stated (upper limit) | W/Hz | 0 | undetected in the cm radio |

## Qualitative findings

- Thermal wind bubble detected via SZE on one side of the quasar, with extended emission-line gas at the same position angle  
  > "The SZE detection is corroborated by the presence of extended emission line gas at the same position angle as the wind." (abstract)
- Wind luminosity is low relative to theoretical predictions, but bubble cooling time is long so bubbles may provide feedback between quasar bursts  
  > "means that such bubbles may be effective at providing feedback between bursts of quasar activity." (abstract)
- One-sided appearance is naturally explained by a combined tSZE and kSZE model  
  > "a combined tSZE and kSZE model provides a natural explanation for the one-sided appearance" (Thermal Plus Kinetic SZE Model)

## Claim tuples

- H: A thermal wind from a luminous quasar inflates a hot bubble detectable via the SZE | E: ALMA Band 4 observations of HE 0515-4414 in a compact configuration with tapering, point-source subtraction of bright sources | R: Apparent SZE decrement of -23.1 uJy/beam (-25.9 after primary beam correction) at 3.5 sigma, SW of the quasar | F: First detection of a quasar wind bubble via SZE (single object) | **partially**
- H: The one-sided SZE decrement is explained by a combined thermal and kinetic SZE | E: Compare tSZE-only and tSZE plus kSZE conical RS11 bubble models | R: kSZE contributes about 60% of the decrement; tSZE+kSZE gives L_W 0.429e11 Lsun and t 12.87e7 yr versus 1.70e11 Lsun and 8.13e7 yr for tSZE only | F: Combined tSZE+kSZE model gives a natural explanation for the one-sided appearance | **partially**
- H: Quasar wind luminosity is at the low end of theoretical predictions | E: Compare inferred wind luminosity and wind energy with bolometric and Eddington-based estimates | R: Wind luminosity about 0.01% of the bolometric luminosity; theory predicts about 1-10% | F: Wind is weak relative to model predictions, but this is a single object | **supported**
- H: Bubbles persist long enough to provide feedback between quasar bursts | E: Estimate bubble age and cooling time with bremsstrahlung cooling from average pressure | R: Bubble age about 0.1 Gyr; cooling time about 0.6 Gyr | F: Cooling time is long so bubbles may provide feedback between bursts | **partially**

## Reasoning

- Why this data: Selected the most luminous radio-quiet quasar in the literature with good ALMA visibility  
  > "We selected the most luminous radio-quiet quasar we could find in the literature that had good visibility to ALMA" (Introduction)
- Why this method: Interferometers in compact configurations match the predicted SZE size scale of 10-100 kpc  
  > "Attempts to directly detect the SZE from thermal winds can be made with interferometers such as the Atacama Large Millimeter Array" (Introduction)
- Alternative: Intrinsically one-sided outflow or counter-flow blocked by higher ISM density  
  > "There are a number of possible explanations, including an intrinsically one-sided outflow, or the counter-flow being blocked by a higher ISM density in its path." (Thermal Plus Kinetic SZE Model)
- Alternative: Contamination from intracluster or intragroup medium rejected  
  > "The lack of any other obvious group or cluster in the field argues against significant contamination" (Results and Discussion)
- Alternative: Starburst origin of the wind, not ruled out  
  > "we cannot currently rule out a starburst origin" (Thermal Plus Kinetic SZE Model)
- Alternative: Massive virialized halo with sound speed comparable to shock speed, rejected by absence of SZE from the quasar  
  > "we detect no SZE from the quasar" (Thermal Plus Kinetic SZE Model)
- How they decided it was enough: Detection judged at 3.5 sigma significance in tapered image  
  > "recovers an apparent dip of flux density of" (ALMA)
- Limitation (authors): Single object; population-level conclusions require more objects  
  > "We emphasize though that this is only a single object" (Discussion)
- Limitation (authors): Strong-shock assumption may not hold for high halo mass  
  > "the assumption of a strong shock may not be valid" (Thermal Plus Kinetic SZE Model)
- Limitation (authors): Radio AGN contribution not constrained; further radio observations needed  
  > "Further radio continuum observations are therefore needed" (Thermal Plus Kinetic SZE Model)
- Caveat (inferred, ours): Detection is only 3.5 sigma in a single tapered map with a 6.7 x 6.4 arcsec beam; sensitivity to the imaging and taper choice is not shown.
- Caveat (inferred, ours): Imaging software, robust value and taper parameters are not stated, so the -23.1 uJy value cannot be reproduced exactly from the text.
- Caveat (inferred, ours): Spherical RS11 model is adapted to a cone by assumption; the 30 deg cone, 45 deg axis angle and 8% correction are judgement calls.
- Caveat (inferred, ours): Wind-luminosity fraction is quoted as 0.01% in the abstract and 0.003% in the Discussion; the paper does not reconcile these.
- Caveat (inferred, ours): The enthalpy energy formula carries units of W, which looks like a units slip for an energy.
- Caveat (inferred, ours): Name given as HE 0515-4415 in one place versus HE 0515-4414 elsewhere.
- Caveat (inferred, ours): A diffuse component near the bright source A5 may remain after point-source subtraction.
- Caveat (inferred, ours): Tapered-beam check at 20 arcsec is claimed but not shown.
- Caveat (inferred, ours): Starburst scenario and radio AGN contribution are not constrained.

## Reproducibility

- Data public (paper): Paper states it uses ALMA data 2016.1.00309.S; public or proprietary status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00309.S." (Acknowledgments)
- Products in archive: _not stated_
- Code: _not stated_
- Missing: Imaging software, task, cell size, image size, deconvolver and robust weighting
- Missing: Taper parameters and the uv range used for the tapered image
- Missing: Point-source model fluxes: how they were derived and from which data
- Missing: ALMA pipeline and CASA versions
- Missing: Primary beam model and exact application of the 12% correction
- Missing: RS11 model parameters (y_peak, cooling prescription details) and the fitting or solving code
- Missing: Dip extraction aperture and noise estimate for the 3.5 sigma significance
- Missing: Adopted T_e, n and gas parameters used in the thermal calculation
- Data volume (inferred): Small: one pointing, four 2 GHz basebands, and 15 scheduling block executions (1 large plus 14 compact); likely a few gigabytes (inferred).
- Score (inferred): 2/5, Scale 0-5. Data identified and the analytic model is clear, but imaging software, weighting, taper, cell size and point-source handling are unstated, so a reproducer would not get the same map.
- Rediscovery candidate: no, Data public status is not stated, and the imaging recipe is too incomplete to redo the 3.5 sigma detection reliably.

## Links

- Method: Rowe & Silk 2011 (RS11) (ref: 2011MNRAS.412..905R) (Wind bubble expansion and y profile model used for the conical SZE interpretation)
- Method: Weaver et al. 1977 (ref: 1977ApJ...218..377W) (Self-similar stellar wind bubble solution underlying RS11)
- Method: Sazonov & Sunyaev 1998 (ref: 1998AstL...24..553S) (Frequency-dependent SZE intensity expression)
- Method: Bennert et al. 2015 (ref: 2015ApJ...809...20B) (Black hole mass estimate formulation)
- Companion: Bielby et al. 2017 (ref: 2017MNRAS.468.1373B) (Source of HST program data and the z=0.28 cluster in the field)
- Companion: Alatalo et al. 2015 (ref: 2015ApJ...798...31A) (Related Lacy-group outflow work cited for molecular gas and feedback context)

## Checks

```json
{
 "quotes": 139,
 "quotes_ok": 139,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 1,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 27,
 "numeric_problems": 0,
 "fill": {
  "facts": 117,
  "stated": 86,
  "rate": 0.735
 },
 "evidence_ok": false
}
```

## Figures

- **Figure 1** (sky_image, 4 panel(s), data, schematic): Greyscale HST, Spitzer and Gemini optical/infrared images of the field of HE 0515-4414 overlaid with red ALMA contours, labelling the quasar, companion sources A1-A6 and wind components C1 and C2, and the SZ decrement with a putative outflow cone in the uv-tapered panel.
  - axes: x: J2000 Right Ascension [hh mm ss.ss s]; y: J2000 Declination [dd mm ss.s arcsec]; contours: ALMA continuum flux density (naturally weighted, and uv-tapered in right panels) [µJy]
  - supports step 3
  - validation: Shows the SZ decrement location relative to the quasar and optical/infrared wind emission, and the ALMA sources removed as point sources, as a spatial check of the detection.
  - read off the plot: approx. naturally weighted contour levels -7, 7, 14, 28, 56 and 128 µJy; approx. uv-tapered contour levels -20, -10, 10, 20 µJy (-3, -1.5, 1.5, 3 sigma)
