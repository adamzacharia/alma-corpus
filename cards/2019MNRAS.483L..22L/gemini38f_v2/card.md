# Direct detection of quasar feedback via the Sunyaev-Zeldovich effect

`2019MNRAS.483L..22L` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Lacy, Mark | arXiv: 1811.05023 | DOI: 10.1093/mnrasl/sly215 | **HELD OUT (benchmark)**

Card schema 1.0 | model gemini-3.8-flash | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, galaxy_clusters_and_sz
- Question: Can ALMA directly detect the Sunyaev-Zeldovich effect decrement from a thermal wind bubble around a hyperluminous radio-quiet quasar?  
  > "In this paper, we describe our attempt to use ALMA to directly detect the SZE from a quasar wind." (1 Introduction)
- Target **HE 0515-4414**: coordinates 05:17:07.614 -44:10:55.64  
  > "QSO | 05:17:07.614 | -44:10:55.64 | 66.2" (Table 1); "HE 0515-4414 ($z=1.71$; Reimers et al. 1998)." (1 Introduction); z/distance z = 1.71  
  > "QSO | 05:17:07.614 | -44:10:55.64 | 66.2" (Table 1); "HE 0515-4414 ($z=1.71$; Reimers et al. 1998)." (1 Introduction); distance from Reimers et al. 1998  
  > "QSO | 05:17:07.614 | -44:10:55.64 | 66.2" (Table 1); "HE 0515-4414 ($z=1.71$; Reimers et al. 1998)." (1 Introduction)

## Data provenance

- ALMA projects: 2016.1.00309.S
- bands: Band 4  
  > "The peak intensity of the thermal SZE decrement is seen at $\approx 130$ GHz (Sunyaev & Zeldovich 1972), which lies in ALMA band-4." (2.1 ALMA)
- frequencies and spectral setup: four 2 GHz basebands centered at 133, 135, 145, and 147 GHz  
  > "four 2 GHz basebands centered at 133, 135, 145, and 147 GHz." (2.1 ALMA)
- continuum bandwidth: 8 GHz  
  > "four 2 GHz basebands" (2.1 ALMA)
- arrays: _not stated_
- configurations: one large configuration (theta_FWHM ~ 0.7'') executed once, and one compact configuration (theta_FWHM ~ 2.7'') executed 14 times  
  > "Two scheduling blocks were made: one executed once in a relatively large configuration (delivering $\theta_{\rm FWHM}$ $\approx$0.7$''$) to measure the point source contribution, and one executed 14 times in a compact configuration (delivering $\theta_{\rm FWHM}$ $\approx$2.7$''$) to maximize our response to the SZE." (2.1 ALMA)
- baselines: _not stated_
- angular resolution: 3.2'' x 2.3'' at PA = 106 deg (naturally-weighted); 6.7'' x 6.4'' at PA = 110 deg (tapered)  
  > "naturally-weighted map (which has the highest point source sensitivity, with an RMS of $\sigma =$ 3.5 $\mu$Jy beam$^{-1}$ and a synthesized beam of $\theta_{\rm FWHM} =$ 3.2$''$$\times$2.3$''$ at a position angle of PA = 106$^{\circ}$)" (2.1 ALMA)
- max recoverable scale: _not stated_
- sensitivity: 3.5 uJy/beam (naturally-weighted); 6.6 uJy/beam (tapered)  
  > "RMS of $\sigma =$ 3.5 $\mu$Jy beam$^{-1}$" (2.1 ALMA); "produced an image with $\sigma =$ 6.6 $\mu$Jy beam$^{-1}$" (2.1 ALMA)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **Spitzer**: IRAC 3.6 and 4.5 um imaging to constrain host galaxy environment  
  > "Spitzer observations were obtained in a DDT program (PID 13221)... 30s frametimes to achieve a 5$\sigma$ depth of AB$\approx 23.1$ in the $3.6$ and $4.5\,\mu$m bands." (2.2 Optical and Infrared)
- Other facility **Gemini**: GMOS Z-band and FLAMINGOS-2 J, Ks imaging  
  > "Gemini fast turnaround observations were obtained in program GS-2017B-FT-12 using the GMOS and FLAMINGOS-2 instruments. GMOS was used to image the field in the NIR $Z$-band... FLAMINGOS-2 imaging was performed through the $J$ and $K_s$ filters." (2.2 Optical and Infrared)
- Other facility **HST**: WFC3 F140W, F160W broadband imaging and G141 grism spectroscopy  
  > "HST observations of the field of HE 0515-4414 from program 14594 (P.I. R. Bielby) using the WFC3 instrument... broad-band images in the F140W and F160W filters, and grism spectra using the G141 dispersive element." (2.2 Optical and Infrared)
- External data: Redshift of HE 0515-4414 (z = 1.71)  
  > "HE 0515-4414 ($z=1.71$; Reimers et al. 1998)." (1 Introduction) [from Reimers et al. 1998]
- External data: Mass and redshift of foreground poor cluster at z = 0.28  
  > "Bielby et al. (2017) find a poor cluster at $z=0.28$ in the field based on absorption lines in the spectrum of the quasar and follow-up integral field spectroscopy. The estimated mass of this cluster, $6\times 10^{12}M_{\odot}$" (3.1 The quasar host galaxy and its environment) [from Bielby et al. (2017)]
- External data: 2MASS J-band continuum flux  
  > "continuum flux from 2MASS $J$-band data (Skrutskie et al. 2006)" (2.2 Optical and Infrared) [from Skrutskie et al. (2006)]
- External data: SUMSS 843 MHz upper limit (< 6 mJy)  
  > "HE 0515$-$4414 is undetected in the cm radio ($<$6 mJy at 843 MHz in the SUMSS survey, Mauch et al. 2003" (3.2.2 Thermal Plus Kinetic SZE Model) [from Mauch et al. 2003]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline  
  > "Calibration of the data was performed with the ALMA pipeline." (2.1 ALMA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ~5%  
  > "A standard calibration strategy was used resulting in an amplitude calibration accuracy of $\approx 5$%" (2.1 ALMA)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural  
  > "No clear signal was readily apparent in the naturally-weighted map" (2.1 ALMA)
- uv taper: taper yielding 6.7'' x 6.4'' synthesized beam  
  > "tapering was applied to improve the surface brightness sensitivity of the image. The taper with a beam best matched to the size of the signal produced an image with $\sigma =$ 6.6 $\mu$Jy beam$^{-1}$ and $\theta_{\rm FWHM} =$ 6.7$''$$\times$6.4$''$ at PA $= 110^{\circ}$" (2.1 ALMA)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Point source models subtracted in the uv-plane  
  > "subtraction of point source models in the $uv$-plane was adequate to remove them" (2.1 ALMA)
- line free channels: _not stated_
- primary beam correction: 12% primary beam correction applied at the peak decrement position  
  > "(After a 12% correction for the response of the primary beam, this peak value of the decrement becomes $-25.9 \, \mu$Jy.)" (2.1 ALMA)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 3.2'' x 2.3'' at PA = 106 deg (naturally-weighted); 6.7'' x 6.4'' at PA = 110 deg (tapered)  
  > "synthesized beam of $\theta_{\rm FWHM} =$ 3.2$''$$\times$2.3$''$ at a position angle of PA = 106$^{\circ}$" (2.1 ALMA); "$\theta_{\rm FWHM} =$ 6.7$''$$\times$6.4$''$ at PA $= 110^{\circ}$" (2.1 ALMA)
- final rms: 3.5 uJy/beam (naturally-weighted); 6.6 uJy/beam (tapered)  
  > "RMS of $\sigma =$ 3.5 $\mu$Jy beam$^{-1}$" (2.1 ALMA); "$\sigma =$ 6.6 $\mu$Jy beam$^{-1}$" (2.1 ALMA)

### Inherited from earlier work

- Self-similar wind bubble expansion model and scaling relations from Rowe & Silk (2011)  
  > "We base our treatment of the expansion of the wind bubble on the model in RS11, which uses the self-similar stellar wind bubble solution of Weaver et al. (1977)." (3.2.1 Thermal SZE Model) [from Rowe & Silk 2011 (RS11)]
- Black hole mass formulation using H-beta FWHM and J-band continuum  
  > "estimate the mass of the black hole, $M_{\bullet}\approx 4.3\times 10^{10}\,M_{\odot}$, based on the width of the H$\beta$ line (9440 km s$^{-1}$) and the continuum flux from 2MASS $J$-band data (Skrutskie et al. 2006) using the formulation of Bennert et al. (2015)." (2.2 Optical and Infrared) [from Bennert et al. (2015)]

### Not stated but needed to reproduce (our reading)

- Specific uv-taper function and cutoff values used to achieve the 6.7'' x 6.4'' beam
- Specific CASA task used for point source fitting and uv subtraction (e.g. uvsub)
- Image size and cell size for naturally-weighted and tapered maps

## Analysis recipe

1. **Subtract compact point source emission in the uv-plane**: Point source modeling and uv-plane subtraction  
  > "subtraction of point source models in the $uv$-plane was adequate to remove them, with the possible exception of a small amount of diffuse extended emission associated with the brightest source, A5." (2.1 ALMA)
   - parameter: Point source flux densities subtracted: A1 (41.7 uJy), A3 (21.8 uJy), A5 (188.2 uJy), QSO (66.2 uJy)  
  > "three other bright ($>20\, \mu$Jy) sources in the field (A1, A3, and A5; Figure 1)" (2.1 ALMA)
   - assumption: Quasar and three bright field sources are point sources in the ALMA data.  
  > "all sources were unresolved in the smaller configuration data" (2.1 ALMA)
   - fitting: Point source models fit and subtracted in the uv-plane  
  > "the subtraction of point source models in the $uv$-plane was adequate to remove them" (2.1 ALMA)
   - validation: High-resolution configuration observations verified point source contribution  
  > "Two scheduling blocks were made: one executed once in a relatively large configuration (delivering $\theta_{\rm FWHM}$ $\approx$0.7$''$) to measure the point source contribution" (2.1 ALMA)
2. **Image the field with uv-tapering to optimize surface brightness sensitivity**: uv-tapering of point-source-subtracted visibilities  
  > "tapering was applied to improve the surface brightness sensitivity of the image." (2.1 ALMA)
   - parameter: uv-taper yielding 6.7'' x 6.4'' synthesized beam, rms 6.6 uJy/beam  
  > "The taper with a beam best matched to the size of the signal produced an image with $\sigma =$ 6.6 $\mu$Jy beam$^{-1}$ and $\theta_{\rm FWHM} =$ 6.7$''$$\times$6.4$''$ at PA $= 110^{\circ}$" (2.1 ALMA)
   - fitting: _not stated_
   - validation: Detection confirmed at 3.5-sigma significance  
  > "recovers an apparent dip of flux density of $-23.1\,\mu$Jy, significant at the 3.5$\sigma$ level, to the SW of the quasar position." (2.1 ALMA)
3. **Model SZE energetics using thermal and kinematic SZE conical bubble models**: Rowe & Silk (2011) self-similar wind bubble solution modified for conical outflow  
  > "We base our treatment of the expansion of the wind bubble on the model in RS11, which uses the self-similar stellar wind bubble solution of Weaver et al. (1977)." (3.2.1 Thermal SZE Model)
   - parameter: Decrement -25.9 uJy (primary beam corrected), Delta T_b = -37.7 uK  
  > "The peak brightness of the SZE decrement of $-$25.9 $\mu$Jy (Section 2.1) corresponds to a brightness temperature change of $\Delta T_{\rm b,peak} = -37.7$ $\mu$K." (3.2 Interpretation of the SZE Signal)
   - assumption: Conical wind geometry with half-angle 30 deg, inclination 45 deg to line of sight  
  > "we assume that our observed SZE signal comes from a region which is a spherical cone, with the cone apex and the center of curvature located at the QSO. We estimate the half angle of the cone in our system to be $\theta = 30^{\circ}$" (3.2.1 Thermal SZE Model); "We further assume that the axis of the outflow is at an angle of 45$^{\circ}$ to the outward extension of our line of sight." (3.2.1 Thermal SZE Model)
   - fitting: Analytic inversion of two equations for outer radius and maximum Compton y  
  > "Equations (3) and (4) are two relations with two unknowns. Since we have observed values for both $R \approx 112$ kpc (corrected for projection) and $y_{\rm max} \approx 2.08 \times 10^{-5}$, we can estimate both $L_W$ and $t$" (3.2.1 Thermal SZE Model)
   - validation: Consistency across enthalpy, pure tSZE, and tSZE+kSZE energy estimates  
  > "Furthermore, the fair agreement in the total energy estimate between the three different methods (total enthalpy, tSZE only and kSZE+tSZE) suggests that our estimate of that quantity at least is fairly robust." (3.2.2 Thermal Plus Kinetic SZE Model)

## Software

- **ALMA pipeline** : Calibration of ALMA visibility data  
  > "Calibration of the data was performed with the ALMA pipeline." (2.1 ALMA)
- **IRAF** : Reduction and combination of Gemini GMOS and FLAMINGOS-2 data  
  > "We used the standard GMOS data reduction package in IRAF to subtract the bias, apply the flat field, and coadd the final images." (2.2 Optical and Infrared)
- **astrodrizzle** : Combining HST WFC3 broad-band images  
  > "The broad-band images were combined using astrodrizzle" (2.2 Optical and Infrared)
- **aXe** : Extracting HST WFC3 G141 grism spectra  
  > "and the aXe software (Kümmel et al. 2009) was used to extract the grism spectra." (2.2 Optical and Infrared)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| apparent dip peak flux density (un-corrected) | -23.1 | 6.6 | uJy | 2 | recovers an apparent dip of flux density of $-23.1\,\mu$Jy, significant at the 3.5$\sigma$ level, to the SW of the quasar position. |
| peak SZE flux decrement (primary-beam corrected) | -25.9 | not stated | uJy | 2 | (After a 12% correction for the response of the primary beam, this peak value of the decrement becomes $-25.9 \, \mu$Jy.) |
| peak brightness temperature change | -37.7 | not stated | uK | 3 | corresponds to a brightness temperature change of $\Delta T_{\rm b,peak} = -37.7$ $\mu$K. |
| average projected radius of the bubble | 33 | not stated | kpc | 3 | The average projected radius of the bubble is $r \approx 3.9\ensuremath{''} = 33$ kpc. |
| projected distance of peak decrement from QSO | 85 | not stated | kpc | 3 | The peak is located at a distance of $r_{\rm max} \approx 10.1\ensuremath{''} = 85$ kpc from the QSO. |
| projected outer radius of the bubble | 108 | not stated | kpc | 3 | The distance from the QSO to the outer edge of the bubble is about $R \approx 12.8\ensuremath{''} = 108$ kpc. |
| Compton y parameter (pure tSZE) | 2.08e-5 | not stated | dimensionless | 3 | Compton parameter $y=\tau k_{\rm B} T_{\rm e}/(m_{\rm e}c^2) \approx 2.08 \times 10^{-5}$. |
| kinetic power (tSZE plus kSZE) | 0.429 | not stated | 10^11 L_sun | 3 | tSZE plus kSZE / 0.429 / 12.87 / 0.67 / 510 / 0.36 / 1.50 |
| bubble age (tSZE plus kSZE) | 12.87 | not stated | 10^7 yr | 3 | tSZE plus kSZE / 0.429 / 12.87 / 0.67 / 510 / 0.36 / 1.50 |
| wind energy E_W (tSZE plus kSZE) | 0.67 | not stated | 10^53 J | 3 | tSZE plus kSZE / 0.429 / 12.87 / 0.67 / 510 / 0.36 / 1.50 |
| black hole mass | 4.3e10 | not stated | M_sun | 0 | estimate the mass of the black hole, $M_{\bullet}\approx 4.3\times 10^{10}\,M_{\odot}$ |

## Qualitative findings

- Extended optical/NIR emission line gas aligns with the position angle of the SZE decrement, corroborating a broad outflow cone.  
  > "The SZE detection is corroborated by the presence of extended emission line gas at the same position angle as the wind." (abstract); "Taken together with the SZE detection, we hypothesize that C1 and C2 help to define a broad outflow cone" (3.1 The quasar host galaxy and its environment)
- The long cooling time (~0.6 Gyr) indicates thermal wind bubbles can provide feedback between episodic bursts of quasar activity.  
  > "the age we estimate for the bubble, $\sim 0.1$ Gyr, and the long cooling time, $\sim 0.6$ Gyr, means that such bubbles may be effective at providing feedback between bursts of quasar activity." (abstract)

## Claim tuples

- H: Quasar thermal winds blow bubbles into the IGM that produce a detectable SZE decrement | E: ALMA Band 4 continuum observations with compact configuration and uv-tapering after subtracting point sources | R: Detected a flux decrement of -23.1 uJy (-25.9 uJy after 12% primary beam correction) at 3.5 sigma significance SW of the quasar | F: First direct detection of an SZE bubble produced by a quasar wind | **supported**
- H: The asymmetry (one-sidedness) of the SZE decrement can be explained by kinematic SZE effects | E: Analytical modeling of tSZE and kSZE contributions to the decrement | R: In the combined model, ~60% of the decrement is kSZE and 40% is tSZE | F: The one-sided nature of the SZE signal is explained by combined thermal and kinetic SZE where approaching counter-flow components cancel | **supported**
- H: Quasar wind kinetic luminosity matches standard theoretical predictions of 1-10% bolometric luminosity | E: Comparison of derived wind kinetic energy and luminosity to quasar bolometric and accretion energy | R: Wind luminosity is ~0.003% of bolometric luminosity and E_W / (eta M_BH c^2) ~ 0.01% | F: The wind kinetic luminosity is at the lower end of theoretical models (~0.01% of bolometric/accretion power vs 1-10% predicted) | **refuted**

## Reasoning

- Why this data: HE 0515-4414 was chosen as the most luminous radio-quiet quasar with good ALMA visibility to maximize the expected SZE signal.  
  > "We selected the most luminous radio-quiet quasar we could find in the literature that had good visibility to ALMA, HE 0515-4414 ($z=1.71$; Reimers et al. 1998)." (1 Introduction)
- Why this method: ALMA Band 4 was chosen because the peak intensity of the thermal SZE decrement occurs at ~130 GHz.  
  > "The peak intensity of the thermal SZE decrement is seen at $\approx 130$ GHz (Sunyaev & Zeldovich 1972), which lies in ALMA band-4." (2.1 ALMA)
- Alternative: Contamination from an intracluster medium or intragroup medium ruled out based on small cluster mass and lack of obvious groups/clusters in Spitzer/Gemini/HST imaging.  
  > "The estimated mass of this cluster, $6\times 10^{12}M_{\odot}$ is much too small for it to contribute to the observed SZE though." (3.1 The quasar host galaxy and its environment); "The lack of any other obvious group or cluster in the field argues against significant contamination of the SZE signal by the intracluster medium of a compact cluster or intragroup medium" (3.1 The quasar host galaxy and its environment)
- Alternative: Starburst-driven wind considered as an alternative origin, requiring SFR ~ 500 M_sun/yr for 1.3e8 yr; cannot be ruled out without SFR constraints.  
  > "Given the relatively low power of the wind, it is also worth investigating whether it can be produced by a starburst in the quasar host galaxy... In the absence of constraints on the star formation rate in this object, we cannot currently rule out a starburst origin." (3.2.2 Thermal Plus Kinetic SZE Model)
- How they decided it was enough: _not stated_
- Limitation (authors): Cannot rule out a starburst-driven wind origin due to lack of star formation rate constraints.  
  > "In the absence of constraints on the star formation rate in this object, we cannot currently rule out a starburst origin." (3.2.2 Thermal Plus Kinetic SZE Model)
- Limitation (authors): Results are based on a single object and need confirmation in the broader quasar population.  
  > "We emphasize though that this is only a single object, and that studies of further objects are needed to confirm this in the general quasar population." (3.3 Discussion)
- Limitation (authors): Strong shock assumption may not be valid if the quasar resides in a massive halo (>~ 1e13 M_sun).  
  > "in this model, the shock speed is relatively low ($\approx 500\;$kms$^{-1}$), and it is possible that if the quasar is in a sufficiently massive virialized dark matter halo ($\stackrel{>}{_{\sim}}10^{13} M_{\odot}$) with a sound speed comparable to the estimated shock speed, the assumption of a strong shock may not be valid." (3.2.2 Thermal Plus Kinetic SZE Model)
- Caveat (inferred, ours): The 3.5-sigma decrement detection is modest and reliant on uv-tapering and accurate uv-subtraction of four point sources.
- Caveat (inferred, ours): The physical interpretation relies heavily on geometric cone assumptions (opening angle 30 deg, inclination 45 deg) and strong shock approximations.

## Reproducibility

- Data public (paper): ALMA data available under ADS/JAO.ALMA#2016.1.00309.S  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00309.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Exact uv-taper parameter or filter function applied in CASA/imaging software
- Missing: Specific CASA task and parameters used for uv-plane point source fitting and subtraction (e.g., uvsub or ft/cltool)
- Missing: Exact pixel size and image size for ALMA maps
- Data volume (inferred): 15 - 30 GB
- Score (inferred): 7/5, The ALMA observations, source subtraction method, and analytical bubble modeling are clearly explained, and the raw data are public in the ALMA archive. However, specific imaging parameters such as the exact uv-taper weighting details and pixel size are omitted.
- Rediscovery candidate: yes, ALMA raw visibilities are public under project 2016.1.00309.S; point source positions and fluxes are tabulated, and the main result is a 3.5-sigma flux decrement and derived wind parameters.

## Links

- Method: Rowe & Silk 2011 (Theoretical framework for SZE bubbles driven by quasar winds and self-similar expansion equations)
- Method: Weaver et al. 1977 (Interstellar wind bubble dynamical solutions underlying RS11 model)
- Method: Bennert et al. 2015 (Virial black hole mass calibration from H-beta FWHM and optical/NIR luminosity)
- Related: SUMSS
- Related: 2MASS

## Checks

```json
{
 "quotes": 82,
 "quotes_ok": 78,
 "quote_pass_rate": 0.951,
 "quotes_too_long": 7,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 54,
  "rate": 0.701
 },
 "evidence_ok": false
}
```
