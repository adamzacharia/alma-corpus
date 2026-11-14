# ALMA detection of 321 GHz water maser emission in the radio galaxy NGC 1052

`2023PASJ...75L...1K` | Publications of the Astronomical Society of Japan 2023 | first author: Kameno, Seiji | arXiv: 2302.04211 | DOI: 10.1093/pasj/psad011

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type archival_reuse

## Science

- Fields: agn_and_quasars, nearby_galaxies
- Question: Is there 321 GHz H2O maser emission in the radio galaxy NGC 1052, and how do its profile and location compare with the known 22 GHz maser?  
  > "So far, no radio-loud AGN has been identified as a 321-GHz maser source." (Introduction); "In this letter we present the first discovery of the 321-GHz maser in NGC 1052" (Introduction)
- Target **NGC 1052**: coordinates _not stated_; z/distance V_sys = 1492 km/s; D_L = 17.6 Mpc  
  > "We employ the systemic velocity of $V_{\rm sys} = 1492$ km s$^{-1}$ and the luminosity distance of $D_L = 17.6$ Mpc." (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2021.1.00341.S
- bands: _not stated_
- frequencies and spectral setup: Four SPWs of 1875 MHz bandwidth centred at 306.4, 308.2, 318.4 and 320.2 GHz; spectral resolution 7.8125 MHz (7.3 km/s)  
  > "Four spectral windows (SPWs) with a 1875-MHz bandwidth were centered at 306.4, 308.2, 318.4 and 320.2 GHz." (2.2 ALMA); "The spectral resolution was 7.8125 MHz corresponding to 7.3 km s$^{-1}$." (2.2 ALMA)
- continuum bandwidth: _not stated_
- arrays: 41 12-m antennas  
  > "The Atacama Large Millimeter/submillimeter Array (ALMA) observations with 41 12-m antennas were carried out on 2022-05-12" (2.2 ALMA)
- configurations: _not stated_
- baselines: array configuration compact, <500.2 m  
  > "The ALMA array configuration was too compact ($<500.2$ m) to rule out the possibility of thermal emission." (3.1 Justification for maser emission)
- angular resolution: synthesized beam 0.68" x 0.56", PA = 79 deg  
  > "with the synthesized beam of $0^{\prime \prime}.68 \times 0^{\prime \prime}.56$ with PA$=79^{\circ}$" (2.2 ALMA)
- max recoverable scale: _not stated_
- sensitivity: image rms 3.3 mJy/beam/ch  
  > "The image rms was 3.3 mJy/beam/ch" (2.2 ALMA)
- time on source: 30 s x 4 scans and a 912 s scan (stated for the phase and bandpass calibrators, 'respectively')  
  > "On-source integration were 30 s $\times 4$ scans and a 912 s scan, respectively." (2.2 ALMA)
- observing dates: 2022-05-12  
  > "observations with 41 12-m antennas were carried out on 2022-05-12" (2.2 ALMA)
- pi or archival as stated: PI science project 2021.1.00341.S targeting a high-redshift galaxy; NGC 1052 was the phase calibrator  
  > "as the PI science project 2021.1.00341.S targeting a high-redshift galaxy" (2.2 ALMA); "The operations software selected NGC 1052 as a phase calibrator" (2.2 ALMA)
- Line: H2O J(Ka,Kc) = 10(2,9) - 9(3,6) (321.225677 GHz)
- Line: H2O (GBT, comparison) J(Ka,Kc) = 6(1,6) - 5(2,3) (22 GHz (exact value not stated))
- Other facility **Green Bank Telescope (GBT)**: 22-GHz H2O maser spectra at 6 epochs (2005-11-18 to 2006-01-13), program GBT 05C-034, spectral resolution 0.33 km/s  
  > "We observed the 22-GHz maser at 6 epochs; 2005-11-18, 2005-11-28, 2005-12-07, 2005-12-20, 2005-12-27, and 2006-01-13 using the Green Bank Telescope (GBT)" (2.1 GBT); "GBT 05C-034 and ADS/JAO.ALMA#2021.1.00341.S" (Summary)
- External data: Absorption-line spectra (H2O 5(5,0)-6(4,3) v2=1, HCN 1-0 and 4-3) overplotted in Figure 1  
  > "together with absorption lines of H$_2$O $5_{5,0}-6_{4,3}$, $v_2=1$, HCN $1-0$, and $4-3$ (cite: 2020ApJ...895...73K; 2023ApJsubmitted)" (3 Results) [from (cite: 2020ApJ...895...73K; 2023ApJsubmitted)]
- External data: Continuum brightness temperature of NGC 1052 exceeding 1e8 K  
  > "Since the brightness temperature of the continuum emission exceeds $10^8$ K (cite: 2004A&A...426..481K)" (3.1 Justification for maser emission) [from (cite: 2004A&A...426..481K)]
- External data: Maser excitation condition: 321-GHz maser needs T_k > 1000 K and n(H2O) > 1e4 cm^-3  
  > "calculated the excitation condition of possible H$_2$O maser transitions for evolved star environments" (Introduction) [from (cite: 2016MNRAS.456..374G)]
- External data: 321 GHz maser properties of Circinus galaxy and NGC 4945 used for comparison (peak-to-continuum ratios 3.2 and 37 for Circinus, 0.29 for NGC 4945)  
  > "In this subsection we compare the properties of the H$_2$O maser in NGC 1052 with those in NGC 4945 and the Circinus galaxy referring to" (3.3 Comparison with the Circinus galaxy and NGC 4945); "The ratio in NGC 4945 was 0.29 on 2012-06-03 and there was a non detection on 2017-05-06." (3.3 Comparison with the Circinus galaxy and NGC 4945) [from (cite: 2021ApJ...923..251H)]
- External data: SO absorption temperatures 26 +/- 4 K (mm) and 344 +/- 43 K (sub-mm)  
  > "found mm (86 – 130 GHz) molecular absorption features and identified different line profiles from sub-mm ones" (3.2 Spectral profiles and location of masers) [from (cite: 2023ApJsubmitted)]

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
- continuum subtraction: spectra are continuum-subtracted (method not stated)  
  > "Continuum-subtracted spectra are shown in" (3 Results)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.68" x 0.56", PA = 79 deg  
  > "with the synthesized beam of $0^{\prime \prime}.68 \times 0^{\prime \prime}.56$ with PA$=79^{\circ}$" (2.2 ALMA)
- final rms: 3.3 mJy/beam/ch  
  > "The image rms was 3.3 mJy/beam/ch" (2.2 ALMA)

### Inherited from earlier work

- Comparison framework and numbers for the Circinus galaxy and NGC 4945 maser properties  
  > "referring to" (3.3 Comparison with the Circinus galaxy and NGC 4945) [from (cite: 2021ApJ...923..251H)]
- GBT spectra reduced with the standard spectral calibration procedure in GBTIDL  
  > "We followed the standard spectral calibration procedure using GBTIDL to obtain spectra with a velocity resolution of 0.33 km s$^{-1}$." (2.1 GBT) [from standard GBTIDL procedure (no citation given)]

### Not stated but needed to reproduce (our reading)

- ALMA band number, pipeline vs manual calibration, CASA/pipeline version, and flux calibrator (only the bandpass calibrator J0423-0120 and phase calibrator NGC 1052 are named)
- Imaging task and parameters: weighting/robust, cell and image size, deconvolver, masking, primary-beam correction
- How the continuum was subtracted and which line-free channels were used
- Whether the line spectrum was extracted at a peak pixel or from an aperture, and the fitting code and initial guesses for the two-Gaussian fit
- How the integrated flux density (10.5 Jy km/s) and the 99% confidence size limits from the uv-plot were computed (fit model, uv bins)
- Source coordinates and the origin of the systemic velocity and D_L = 17.6 Mpc
- Whether the GitHub scripts contain the exact calibration and imaging choices (the paper only points to them)

## Analysis recipe

1. **reduce GBT 22 GHz spectra**: Standard spectral calibration in GBTIDL; spectra at 0.33 km/s resolution for six epochs  
  > "We followed the standard spectral calibration procedure using GBTIDL to obtain spectra with a velocity resolution of 0.33 km s$^{-1}$." (2.1 GBT)
   - software: GBTIDL
   - parameter: rms per epoch 2.3, 2.7, 2.1, 1.4, 4.6, 2.5 mJy; ~10% systematic flux error  
  > "The rms noise of the spectrum at each epoch was 2.3, 2.7, 2.1, 1.4, 4.6, and, 2.5 mJy, respectively." (2.1 GBT)
   - fitting: _not stated_
   - validation: _not stated_
2. **extract and fit the 321 GHz line profile**: Continuum-subtracted ALMA spectrum fitted with two Gaussian components (broad and narrow)  
  > "The 321-GHz H$_2$O emission profile was biased blueward, which was fitted by two Gaussian components" (3 Results)
   - parameter: Broad: centre 1467 +/- 5 km/s, FWHM 208 +/- 12 km/s; narrow: centre 1333 +/- 1 km/s, FWHM 44 +/- 3 km/s  
  > "(b) a narrow component with the center velocity of $1333 \pm 1$ km s$^{-1}$ with FWHM of $44 \pm 3$ km s$^{-1}$." (3 Results)
   - assumption: Systemic velocity 1492 km/s  
  > "We employ the systemic velocity of $V_{\rm sys} = 1492$ km s$^{-1}$" (Introduction)
   - fitting: _not stated_
   - validation: _not stated_
3. **locate the maser emission relative to the continuum**: Channel maps in 20 km/s slices over 1280-1580 km/s; position measured by 2-D Gaussian fitting in each channel map and registered on the continuum image  
  > "We produced channel maps of the 321-GHz H$_2$O line with a velocity slice of 20 km s$^{-1}$" (3 Results); "and measured the position by 2-D Gaussian fitting in the channel maps." (3 Results)
   - parameter: velocity slice 20 km/s  
  > "with a velocity slice of 20 km s$^{-1}$" (3 Results)
   - fitting: 2-D Gaussian fit per channel  
  > "and measured the position by 2-D Gaussian fitting in the channel maps." (3 Results)
   - validation: Outlier channel at 1560 km/s with S/N 4.3 noted separately; no velocity gradient found  
  > "except one outlier offset by $0^{\prime \prime}.29 \pm 0^{\prime \prime}.03$ at 1560 km s$^{-1}$ with a signal-to-noise ratio as low as 4.3." (3 Results)
4. **constrain source sizes from the uv plane**: uv-plot analysis of continuum and continuum-subtracted velocity-integrated line emission giving 99% confidence upper limits on FWHM size  
  > "The upper limits (99% confidence) of the FWHM size were $0^{\prime \prime}.024$ and $0^{\prime \prime}.12$ for the continuum and the continuum-subtracted velocity-integrated emission line" (3 Results)
   - fitting: _not stated_
   - validation: _not stated_
5. **test thermal versus maser origin via brightness temperature**: Brightness temperature lower limit from size upper limit and peak flux density, plus ancillary arguments (absorption against the core, compactness vs CND)  
  > "Nevertheless, ancillary evidence indicates that the emission is non-thermal maser." (3.1 Justification for maser emission); "yields a brightness temperature of $T_{\rm B} \geq 43$ K." (3.1 Justification for maser emission)
   - assumption: Thermal molecular gas covering the bright continuum core would appear in absorption  
  > "molecular gas covering the continuum source must be seen in absorption except non-thermal emission." (3.1 Justification for maser emission)
   - fitting: _not stated_
   - validation: Compared with CO 2-1 and 3-2 emission fluxes and CND extent  
  > "The CND cannot harbor the 321-GHz H$_2$O emission." (3.1 Justification for maser emission)
6. **derive isotropic maser luminosities and compare with Circinus and NGC 4945**: Isotropic luminosity L = 1.04e-3 nu_rest D_L^2 integral S(v) dv for 22 and 321 GHz masers; compare peak-to-continuum ratios  
  > "for 22-GHz and 321-GHz masers, respectively, using the formula" (3.3 Comparison with the Circinus galaxy and NGC 4945)
   - assumption: D_L = 17.6 Mpc  
  > "the luminosity distance of $D_L = 17.6$ Mpc" (Introduction)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **GBTIDL** : standard spectral calibration of GBT 22 GHz data  
  > "We followed the standard spectral calibration procedure using GBTIDL" (2.1 GBT)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 321 GHz H2O isotropic luminosity | 1090 | not stated | L_sun | 6 | the isotropic luminosity of 1090 $L_{\Sol}$. |
| 22 GHz H2O isotropic luminosity | 176 | not stated | L_sun | 6 | The isotropic luminosity is estimated to be 176 $L_{\Sol}$ and 1090 $L_{\Sol}$ for 22-GHz and 321-GHz masers |
| 321 GHz broad component FWHM | 208 | +/-12 | km/s | 2 | (a) a broad component with the center velocity of $1467 \pm 5$ km s$^{-1}$ and FWHM of $208 \pm 12$ km s$^{-1}$ |
| 321 GHz broad component centre velocity | 1467 | +/-5 | km/s | 2 | (a) a broad component with the center velocity of $1467 \pm 5$ km s$^{-1}$ |
| 321 GHz narrow component FWHM | 44 | +/-3 | km/s | 2 | (b) a narrow component with the center velocity of $1333 \pm 1$ km s$^{-1}$ with FWHM of $44 \pm 3$ km s$^{-1}$. |
| 321 GHz narrow component centre velocity | 1333 | +/-1 | km/s | 2 | (b) a narrow component with the center velocity of $1333 \pm 1$ km s$^{-1}$ |
| 321 GHz peak flux density | 0.07 at 1334 km/s | not stated | Jy | 2 | The peak flux density was 0.07 Jy at 1334 km s$^{-1}$. |
| 22 GHz maser centroid velocity | 1685 | +/-4 | km/s | 1 | The centroid of the 22-GHz emission remained at $1685 \pm 4$ km s$^{-1}$ |
| 22 GHz maser redshift relative to systemic velocity | 193 | not stated | km/s | 1 | which was redshifted with respect to the systemic velocity by 193 km s$^{-1}$. |
| Continuum flux density at 307.3 GHz and 319.3 GHz | 0.401 and 0.380 | not stated | Jy | 0 | The continuum component was unresolved with flux densities of 0.401 Jy and 0.380 Jy at 307.3 GHz and 319.3 GHz, respectively. |
| Upper limit (99%) on FWHM size of continuum | 0.024 | 99% confidence upper limit | arcsec | 4 | The upper limits (99% confidence) of the FWHM size were $0^{\prime \prime}.024$ and $0^{\prime \prime}.12$ for the continuum |
| Upper limit (99%) on FWHM size of velocity-integrated line emission | 0.12 | 99% confidence upper limit | arcsec | 4 | The upper limits (99% confidence) of the FWHM size were $0^{\prime \prime}.024$ and $0^{\prime \prime}.12$ for the continuum |
| Offset of channel maser positions from the continuum position (upper limit) | 0.14 arcsec (12 pc) | upper limit | arcsec | 3 | These coincided with the continuum position with an upper limit of $0^{\prime \prime}.14$ corresponding to 12 pc |
| Brightness temperature of the 321 GHz emission (lower limit) | >=43 | lower limit | K | 5 | yields a brightness temperature of $T_{\rm B} \geq 43$ K. |
| Integrated flux density of 321 GHz H2O emission | 10.5 | not stated | Jy km/s | 2 | The integrated flux density of the 321-GHz H$_2$O emission was 10.5 Jy km s$^{-1}$ |
| Ratio of 321 GHz maser peak flux to continuum flux | 0.19 | not stated | dimensionless | 6 | The ratio of the 321-GHz maser peak flux to continuum flux in NGC 1052 is 0.19 |
| Image rms | 3.3 | not stated | mJy/beam/channel | 0 | The image rms was 3.3 mJy/beam/ch |

## Qualitative findings

- First submillimeter maser detection in a radio galaxy and the most luminous 321 GHz H2O maser known to date  
  > "This is the first submillimeter maser detection in a radio galaxy and the most luminous 321-GHz H$_2$O maser known to date" (abstract)
- The 321 GHz profile straddles the systemic velocity, unlike the redshifted 22 GHz maser profile  
  > "The sub-mm maser profile straddles the systemic velocity of the galaxy, similar to sub-mm molecular absorption lines, unlike the redshifted profile of the 22-GHz maser." (Summary)
- The 321 GHz maser is unresolved and coincides with the continuum core within 12 pc  
  > "coincides with the continuum core position within 12 pc" (abstract)
- No high-velocity components (~1000 km/s offset) are seen in NGC 1052, unlike Circinus and NGC 4945  
  > "such components are not identified in NGC 1052." (3.3 Comparison with the Circinus galaxy and NGC 4945)

## Claim tuples

- H: Does NGC 1052 host 321 GHz H2O emission, and is it a maser? | E: ALMA spectra of a serendipitously observed phase calibrator, with brightness temperature and ancillary arguments | R: Emission at 321 GHz with peak 0.07 Jy and T_B >= 43 K; compact array cannot rule out thermal emission, but thermal lines appear in absorption at the core | F: The emission is probably a non-thermal maser | **partially**
- H: Where is the 321 GHz maser located relative to the continuum core? | E: 2-D Gaussian positions in 20 km/s channel maps registered on the continuum image, plus uv-plane size limits | R: Positions coincide with the continuum within 0.14 arcsec (12 pc); line size <= 0.12 arcsec; no velocity gradient | F: The maser is unresolved and located at the compact continuum core | **supported**
- H: How does the 321 GHz profile compare with the 22 GHz maser? | E: Two-Gaussian fit of the ALMA profile compared with GBT 22 GHz spectra taken 16 years earlier | R: 321 GHz: broad component FWHM 208 km/s near systemic plus narrow 44 km/s component blueshifted by 160 km/s; 22 GHz: broad profile redshifted by 193 km/s | F: The two masers trace different gas; 321 GHz amplifies the core continuum through hot dense gas in front of it, while 22 GHz is redshifted inflow in the near side of the torus | **partially**
- H: Why is NGC 1052 so luminous at 321 GHz compared with Circinus and NGC 4945? | E: Isotropic luminosity and peak-to-continuum ratio compared with Circinus and NGC 4945 values from the literature | R: Luminosities 5.5 and 17 times those of Circinus (22 and 321 GHz); peak/continuum ratio 0.19 versus 3.2 and 37 in Circinus | F: High luminosity is ascribed to the brighter continuum with lower amplification gain | **partially**

## Reasoning

- Why this data: Detection was serendipitous: NGC 1052 was selected as a phase calibrator by the operations software in a project targeting a high-redshift galaxy; submillimeter observations are needed to probe inside the obscuring torus  
  > "The Atacama Large Millimeter/submillimeter Array (ALMA) serendipitously detected H$_2$O" (abstract); "In this context, submillimeter (sub-mm) observations are crucial to probe inside the obscuring torus." (Introduction)
- Why this method: _not stated_
- Alternative: Thermal emission from the circum-nuclear disk was rejected because the 321 GHz emission is within 12 pc and much more compact than the CND, and its flux exceeds the CO emission  
  > "The 321-GHz emission locates within 12 pc from the radio continuum, much more compact than the CND." (3.1 Justification for maser emission); "The CND cannot harbor the 321-GHz H$_2$O emission." (3.1 Justification for maser emission)
- Alternative: Downstream of the jets as the maser site is considered unlikely because the mm SO absorber is too cold  
  > "Since the mm SO absorber is too cold to excite the maser, downstream of the jets is unlikely to harbor the 321-GHz maser." (3.2 Spectral profiles and location of masers)
- How they decided it was enough: _not stated_
- Limitation (authors): Array too compact to rule out thermal emission; longer baselines needed for brightness temperature constraint  
  > "The ALMA array configuration was too compact ($<500.2$ m) to rule out the possibility of thermal emission." (3.1 Justification for maser emission); "Longer-baseline ($> 3500$ m) observations would provide more concrete constraints on the brightness temperature $> 2000$ K." (3.1 Justification for maser emission)
- Limitation (authors): 22 GHz monitoring is 16 years older than the ALMA observation so only a qualitative profile comparison is made  
  > "Since the monitoring was taken 16 years earlier than the 321-GHz observation, we do not attempt to perform a detailed comparison however." (Introduction)
- Limitation (authors): Blending of multiple narrower features in the spectrum cannot be established  
  > "It is difficult to establish the degree of blending of multiple narrower features making up the spectrum in these observations however." (3.3 Comparison with the Circinus galaxy and NGC 4945)
- Caveat (inferred, ours): Maser identification rests on indirect arguments; no brightness temperature above thermal values is measured (T_B >= 43 K only)
- Caveat (inferred, ours): Single-epoch ALMA observation with no variability or polarization test
- Caveat (inferred, ours): The 22 GHz comparison uses data 16 years older than the ALMA epoch
- Caveat (inferred, ours): Calibration, imaging and line-fitting details are not given in the paper; reliability of the 3.3 mJy/beam/ch rms and flux scale (no ALMA flux uncertainty stated) cannot be judged without the scripts
- Caveat (inferred, ours): Torus layer temperatures rely on a submitted companion paper

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Code: Reduction scripts and reduced data in GitHub repository kameno seiji/ALMA-2021.1.00341.S  
  > "Reduction scripts and reduced data are available in the GitHub repository" (2 Observations); "https://github.com/kamenoseiji/ALMA-2021.1.00341.S" (Footnote 1)
- Missing: ALMA calibration and imaging parameters are not given in the paper (see unstated_but_needed); must be taken from the GitHub scripts
- Missing: Source coordinates and the origin of the systemic velocity and luminosity distance
- Missing: Two-Gaussian fit and uv-plane size-limit procedures are not described in detail
- Data volume (inferred): Small: one 4-SPW, 41-antenna compact-configuration execution block, likely tens of GB raw; pipeline products smaller
- Score (inferred): 4/5, ALMA project code, observing date, spectral setup, beam, rms and all main numbers are given, and reduction scripts plus reduced data are on GitHub; but calibration, imaging and fitting settings are only in the repository, not in the paper.
- Rediscovery candidate: yes, Single ALMA project (2021.1.00341.S, observed 2022-05-12) with scripts on GitHub and numeric line parameters (FWHM, centre velocities, luminosity) that can be re-derived; public availability of the ALMA data is not stated in the paper and is assumed from the archive link.

## Links

- Method: (cite: 2020ApJ...895...73K) (Earlier ALMA study of NGC 1052 submillimeter molecular absorption lines and CND emission used for the absorption-line comparison)
- Method: (cite: 2021ApJ...923..251H) (Circinus galaxy and NGC 4945 321 GHz maser properties used for the comparison)
- Companion: (cite: 2023ApJsubmitted) (Millimeter (86-130 GHz) molecular absorption features in NGC 1052 and SO temperatures, shown in Figure 1)
- Related: GBT 05C-034 (22 GHz maser monitoring)

## Checks

```json
{
 "quotes": 89,
 "quotes_ok": 89,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 17,
 "numeric_problems": 0,
 "fill": {
  "facts": 86,
  "stated": 48,
  "rate": 0.558
 },
 "evidence_ok": true
}
```
