# No nitrogen fractionation on 600 au scale in the Sun progenitor analogue OMC-2 FIR4

`2020MNRAS.493.3412F` | Monthly Notices of the Royal Astronomical Society 2020 | first author: Fontani, F. | arXiv: 2002.06045 | DOI: 10.1093/mnras/staa481

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: Does the 14N/15N ratio vary across the OMC-2 FIR4 protocluster at ~600 au core scales, and does it depend on temperature (traced by the N2D+/N2H+ D/H ratio)?  
  > "so that it cannot be excluded the presence of local spots enriched (or depleted) in $^{15}$N." (Introduction); "Overall, our results indicate that: (1) $^{14}$N/$^{15}$N does not change across the region at core scales, and (2) $^{14}$N/$^{15}$N does not depend on temperature variations." (abstract)
- Target **OMC-2 FIR4**: coordinates phase centre RA=05h35m27.0s, Dec=-05d09m56.8s  
  > "at a distance of 388$\pm 5$ pc (Kounkel et al. (cite: kounkel17))" (Source background); "The coordinates of the phase centre were RA=05$^{\rm h}35^{\rm m}27$.$^{\prime\prime}$0, Dec=–05$^{\circ}09^{\prime}56$.$^{\prime\prime}$8." (Observations); z/distance 388 +/- 5 pc  
  > "at a distance of 388$\pm 5$ pc (Kounkel et al. (cite: kounkel17))" (Source background); "The coordinates of the phase centre were RA=05$^{\rm h}35^{\rm m}27$.$^{\prime\prime}$0, Dec=–05$^{\circ}09^{\prime}56$.$^{\prime\prime}$8." (Observations); distance from Kounkel et al. 2017 (cite: kounkel17)  
  > "at a distance of 388$\pm 5$ pc (Kounkel et al. (cite: kounkel17))" (Source background); "The coordinates of the phase centre were RA=05$^{\rm h}35^{\rm m}27$.$^{\prime\prime}$0, Dec=–05$^{\circ}09^{\prime}56$.$^{\prime\prime}$8." (Observations)

## Data provenance

- ALMA projects: 2016.1.00681.S
- bands: Band 3 (3 mm) and Band 4 (2 mm)  
  > "in Band 3 (3 mm) in Dec. 23 – 25, 2016, and in band 4 (2 mm) in Mar. 11, 2017." (Observations)
- frequencies and spectral setup: four spectral windows: N2H+, 15NNH+, N15NH+ (1-0) at 3 mm and N2D+ (2-1) at 2 mm; spectral resolution ~0.2-0.4 km/s  
  > "The correlator was configured in four different spectral windows to cover lines of N$_{2}$H$^{+}$, $^{15}$NNH$^+$, N$^{15}$NH$^+$ (1–0) at 3 mm, and N$_{2}$D$^{+}$ (2–1) at 2 mm." (Observations); "spectral resolution" (Table 1)
- continuum bandwidth: _not stated_
- arrays: 40 antennas, ALMA Cycle 4 (antenna diameter not stated)  
  > "Observations towards OMC–2 FIR4 using 40 antennas of the Atacama Large Millimeter Array (ALMA) in Cycle 4" (Observations)
- configurations: _not stated_
- baselines: 15-491 m (Band 3 lines); 15-321 m (N2D+, Band 4)  
  > "15–491" (Table 1); "15–321" (Table 1)
- angular resolution: ~1.5'' x 1.8'' (~600 au) in Band 3; 1.4'' x 1.8'' in Band 4  
  > "with a spatial resolution of about 600 au" (Introduction)
- max recoverable scale: ~25'' in Band 3 and ~19'' in Band 4 (nominal)  
  > "The nominal maximum recoverable scale (MRS) was $\sim 25$$^{\prime\prime}$ in Band 3 and $\sim 19$$^{\prime\prime}$ in Band 4." (Observations)
- sensitivity: rms per channel ~1.5 mJy (N2H+), ~1.2 mJy (15NNH+, N15NH+), ~3 mJy (N2D+)  
  > "root mean square (rms) noise per channel in each spectral window" (Table 1); "$\sim 3$" (Table 1)
- time on source: 136 min (Band 3 lines); 32 min (N2D+, Band 4)  
  > "int. time" (Table 1); "$136$" (Table 1); "$32$" (Table 1)
- observing dates: Band 3: 23-25 Dec 2016; Band 4: 11 Mar 2017  
  > "in Band 3 (3 mm) in Dec. 23 – 25, 2016, and in band 4 (2 mm) in Mar. 11, 2017." (Observations)
- pi or archival as stated: PI observations, PI F. Fontani  
  > "as part of the project 2016.1.00681.S (PI: F. Fontani)" (Observations)
- Line: N2H+ 1-0 (93.173402 GHz)
- Line: 15NNH+ 1-0 (90.263833 GHz)
- Line: N15NH+ 1-0 (91.205695 GHz)
- Line: N2D+ 2-1 (154.217011 GHz)
- Other facility **IRAM-30m**: single-dish 14N/15N ratio (R) for comparison, from Kahane et al.  
  > "that obtained by Kahane et al. ((cite: kahane18)) with the IRAM-30m telescope" (14N/15N)
- External data: Distance to OMC-2 FIR4, 388 +/- 5 pc  
  > "at a distance of 388$\pm 5$ pc (Kounkel et al. (cite: kounkel17))" (Source background) [from Kounkel et al. (cite: kounkel17)]
- External data: Line rest frequencies, E_u, S_ij mu^2, A_ij from CDMS  
  > "taken from the Cologne Molecular Database for Spectroscopy (CDMS; Endres et al. (cite: endres))" (Table 1) [from Endres et al. (cite: endres)]
- External data: Single-dish IRAM-30m 14N/15N value in OMC-2 FIR4 (R~270), used for comparison  
  > "They derived the same *R* value, $\sim$270, in all the five molecules" (Introduction) [from Kahane et al. (cite: kahane18)]
- External data: 82 GHz continuum map shown as reference in Fig. 1  
  > "As reference, in the same plot we show the 82 GHz continuum map published by Fontani et al. ((cite: fontani17))." (Results) [from Fontani et al. (cite: fontani17)]
- External data: Kinetic temperatures 35 K and 45 K in the OMC-2 FIR4 envelope, used as fixed Tex in fits  
  > "the two extreme values of kinetic temperature measured in the envelope of OMC–2 FIR4, namely 35 and 45 K, in previous works" (14N/15N) [from Ceccarelli et al. (cite: ceccarelli14a); Friesen & Pineda et al. (cite: friesen17)]
- External data: Average H2 volume density of OMC-2 FIR4, 1.2e6 cm-3  
  > "the average H$_2$ volume density is $1.2\times 10^6$ cm$^{-3}$ (Ceccarelli et al. (cite: ceccarelli14a))" (14N/15N) [from Ceccarelli et al. (cite: ceccarelli14a)]
- External data: Relative intensities of the hyperfine components (~0.1111) for 15NNH+ and N15NH+  
  > "see e.g. Dore et al. (cite: dore09) for $^{15}$NNH$^+$ and N$^{15}$NH$^+$ (1–0)" (14N/15N) [from Dore et al. (cite: dore09); JPL catalog for N2H+]

## Processing

### Calibration

- pipeline or manual: standard ALMA calibration scripts (CASA)  
  > "The data were calibrated using standard ALMA calibration scripts of the Common Astronomy Software Applications" (Observations)
- casa version: CASA 4.7.0  
  > "version 4.7.0) package" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0423-0120 (flux and bandpass); phase/amplitude gain calibrator J0541-0541  
  > "Flux and bandpass calibration were obtained through observations of J0423-0120." (Observations); "Visibility phases and amplitudes were calibrated on quasar J0541-0541." (Observations)
- flux scale uncertainty: not quantified; a 10% missing-flux level is said to be comparable to the flux calibration uncertainty  
  > "which is comparable to the uncertainty on the flux calibration" (Results)
- self calibration: _not stated_

### Imaging

- task: MAPPING of GILDAS (data exported from CASA to FITS)  
  > "and then imaged and deconvolved with software MAPPING of the GILDAS package using standard procedures" (Observations)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: line-free channels around each line, subtracted in the (u,v) domain  
  > "Continuum subtraction was performed by taking the line-free channels around the lines in each individual spectral window" (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: ~1.5'' x 1.8'' (Band 3 lines); 1.4'' x 1.8'' (N2D+)  
  > "The ALMA images, having synthesised beam of $\sim 1$.$^{\prime\prime}$$5 \times 1$.$^{\prime\prime}$8, i.e. $\sim 600$ au" (abstract)
- final rms: per-channel rms ~1.5 / 1.2 / 1.2 mJy (N2H+, 15NNH+, N15NH+), ~3 mJy (N2D+)  
  > "root mean square (rms) noise per channel in each spectral window" (Table 1)

### Inherited from earlier work

- Hyperfine spectroscopic parameters of the three N2H+ isotopologue lines  
  > "Full spectroscopic parameters of the hyperfine structure of the three lines are given, e.g., in Kahane et al." (14N/15N) [from Kahane et al. ((cite: kahane18)); Colzi et al. ((cite: colzi19))]
- MADCUBA-AUTOFIT non-linear least-squares fitting approach  
  > "The tool MADCUBA-AUTOFIT provides the best fit parameters via a non-linear least squared fit algorithm (see also Colzi et al. (cite: colzi19))." (14N/15N) [from Colzi et al. (cite: colzi19)]
- Treatment of MADCUBA fit errors when a parameter (Tex) is fixed  
  > "as discussed in Martín et al. ((cite: martin19)), when one of the fit parameters in MADCUBA is fixed, then the error associated is zero" (14N/15N) [from Martín et al. (cite: martin19)]
- ALMA continuum maps from this dataset deferred to a forthcoming paper  
  > "a study totally devoted to the continuum emission will be presented in a forthcoming paper (Neri et al. in prep.)" (Results) [from Neri et al. in prep.]

### Not stated but needed to reproduce (our reading)

- Which ALMA array (12 m vs 7 m) and which antenna configurations were used for each band
- Whether the calibration used the pipeline or manual scripts and which pipeline version
- Imaging parameters in GILDAS MAPPING: weighting/robust, cell size, image size, deconvolution algorithm, masks, clean threshold
- Which channels were line-free for continuum subtraction in each spectral window
- Pixel-level region definitions (polygons) for FIR4-east, -west, -peak, -north and -tot; regions were drawn by hand
- Initial guesses, priors/bounds, and fixed parameters in the MADCUBA fits
- Primary beam correction and spectral smoothing/channel widths used before extraction
- Exact angular source sizes theta_s used in the brightness temperature conversion for N2D+
- Beam sizes per spectral window and noise per region other than the per-channel values in Table 1

## Analysis recipe

1. **calibrate visibilities**: standard ALMA calibration scripts run in CASA  
  > "The data were calibrated using standard ALMA calibration scripts of the Common Astronomy Software Applications" (Observations)
   - software: CASA
   - parameter: Flux and bandpass calibrator J0423-0120; phase/amplitude calibrator J0541-0541  
  > "Flux and bandpass calibration were obtained through observations of J0423-0120." (Observations); "Visibility phases and amplitudes were calibrated on quasar J0541-0541." (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **image the cubes and subtract continuum**: export to FITS/GILDAS, image and deconvolve with MAPPING, subtract line-free-channel continuum in the uv-domain  
  > "and then imaged and deconvolved with software MAPPING of the GILDAS package using standard procedures" (Observations); "Continuum subtraction was performed by taking the line-free channels around the lines in each individual spectral window" (Observations)
   - software: GILDAS, MAPPING
   - parameter: Nominal MRS ~25'' (Band 3) and ~19'' (Band 4)  
  > "The nominal maximum recoverable scale (MRS) was $\sim 25$$^{\prime\prime}$ in Band 3 and $\sim 19$$^{\prime\prime}$ in Band 4." (Observations)
   - fitting: _not stated_
   - validation: Checked missing extended flux by extracting spectra over the IRAM-30m beam: all 15N-isotopologue flux recovered, at most 10% missing in N2H+ (1-0)  
  > "we recover the whole flux in the $^{15}$N isotopologues, and we miss at most $10\%$ of extended flux in N$_{2}$H$^{+}$ (1–0)" (Results)
3. **define regions and extract spectra**: five coarse regions (FIR4-east, -west, -peak, -north, -tot) defined manually following contours of intensity maps; spectra extracted from each  
  > "their borders contain one dominant intensity peak of one isotopologue" (Results); ""FIR4-tot" coincides with the union of regions "FIR4-east", "FIR4-west" and "FIR4-peak"" (Results)
   - parameter: FIR4-east and FIR4-west borders follow ~3 sigma contour of 15NNH+ and N15NH+ maps  
  > "the borders follow roughly the $3\sigma$ rms contour of the average $^{15}$NNH$^+$ and N$^{15}$NH$^+$ (1–0) emission maps" (Results)
   - parameter: FIR4-peak and FIR4-north follow the 15 sigma N2D+ contour  
  > "and roughly follows its $15\sigma$ rms contour to well separate this peak to the secondary one" (Results)
   - parameter: N2D+ flux density converted to brightness temperature with T_SB=1.222e3 F/(nu^2 theta_s^2)  
  > "$T_{\rm SB}=1.222\times10^3 F_{\nu}/(\nu^2\theta_{\rm s}^2)$" (Results)
   - assumption: theta_s is the diameter of the circular region with the same area as the core  
  > "defined as the diameter of the circular region having the same area of the core considered" (Results)
   - fitting: _not stated_
   - validation: _not stated_
4. **fit hyperfine structure of all lines**: MADCUBA-AUTOFIT synthetic hyperfine profile fit (single Tex, FWHM, Vp) giving peak flux, Vp, FWHM, optical depth and column density  
  > "performs a fit to the lines hyperfine structure creating a synthetic profile assuming for all components a single excitation temperature" (14N/15N); "The software also computes the best fit line velocity at the intensity peak" (14N/15N)
   - software: MADCUBA
   - parameter: For N2H+ (1-0), Tex either free or fixed at 35 K or 45 K  
  > "assuming three different $T_{\rm ex}$: the best fit $T_{\rm ex}$ when leaving this parameter free" (14N/15N)
   - assumption: Single excitation temperature for all hyperfine components; velocity separations fixed to laboratory values  
  > "and separation in velocity given by the laboratory value" (14N/15N)
   - fitting: non-linear least squares (MADCUBA-AUTOFIT); priors and likelihood not stated  
  > "The tool MADCUBA-AUTOFIT provides the best fit parameters via a non-linear least squared fit algorithm" (14N/15N)
   - validation: Residuals inspected; FWHM and opacities of the compared components checked for consistency; fits generally good except an extra feature at ~9 km/s in some N15NH+ spectra  
  > "The fits shown in Fig. [\[spectra-tot\]](#spectra-tot) provide generally good results" (14N/15N)
5. **derive 14N/15N ratio R**: ratio of peak flux densities of the isolated N2H+ F1=0-1 hyperfine component to the F=0-1 component of 15NNH+ and N15NH+, per region  
  > "we have divided the flux density peak of the F$_1$=0–1 hyperfine component of N$_{2}$H$^{+}$ (1–0), with rest frequency 93.17613 GHz" (14N/15N)
   - software: MADCUBA
   - parameter: Compared 15N components at rest frequencies 90.2645 and 91.2086 GHz  
  > "at rest frequencies 90.2645 and 91.2086 GHz, respectively" (14N/15N)
   - assumption: Compared hyperfine components have the same Tex, the same line width, are optically thin, and have the same relative intensity (~0.1111)  
  > "(1) have the same excitation temperature, (2) have the same line widths, (3) are all optically thin." (14N/15N)
   - fitting: _not stated_
   - validation: Optical-depth correction factor tau/(1-exp(-tau)) ~1.21 applied in the worst cases (FIR4-tot, FIR4-west): R becomes ~340+/-100 and ~400+/-120; conclusions unchanged. Also compared with IRAM-30m R.  
  > "in both cases the peak brightness temperature should be corrected by the factor $\tau/(1-\exp{(-\tau)})\sim 1.21$" (14N/15N)
6. **derive D/H from N2D+ and N2H+ column densities**: ratio of total column densities of N2D+ and N2H+ obtained with MADCUBA fits, for Tex free, 35 K and 45 K  
  > "the D/H ratio has been estimated by dividing the total column densities of N$_{2}$D$^{+}$ and N$_{2}$H$^{+}$ computed by fitting the lines with MADCUBA" (D/H); "We have fitted the lines with three temperatures" (D/H)
   - software: MADCUBA
   - parameter: Spectra fitted in synthesised temperature units  
  > "The fits to the hyperfine structure have been performed to both N$_{2}$H$^{+}$ and N$_{2}$D$^{+}$ spectra converted in "synthesised temperature" units." (D/H)
   - assumption: Tex fixed at 35 K and 45 K as two cases, plus one free-Tex case  
  > "the two extreme values of kinetic temperature measured in the envelope of OMC–2 FIR4, namely 35 and 45 K, in previous works" (14N/15N)
   - fitting: _not stated_
   - validation: D/H does not change within uncertainties for the three Tex assumptions, though column densities change by ~1.5; N2D+ residual near 154.2165 GHz (possible CH3CHO contamination, <5% of integrated intensity) judged not to prevent a good fit  
  > "the D/H ratios do not change within the uncertainties" (D/H)
7. **compare R across cores, with D/H, with single dish and with the envelope**: compare R and D/H across regions, versus IRAM-30m R, and derive lower limits on R in the envelope where 15N isotopologues are undetected  
  > "we have extracted spectra in different points of the envelope surrounding FIR4, in which N$_{2}$H$^{+}$ is detected but the $^{15}$N isotopologues are not" (Discussion and conclusions)
   - assumption: D/H is used as a temperature/evolutionary indicator, anti-correlated with gas temperature  
  > "it is well anti-correlated to the gas temperature" (Discussion and conclusions)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.0: calibration with standard ALMA calibration scripts  
  > "version 4.7.0) package" (Observations)
- **GILDAS** : analysis of FITS cubes after conversion to GILDAS format  
  > "The calibrated data cubes were converted in fits format" (Observations)
- **MAPPING (GILDAS)** : imaging and deconvolution  
  > "imaged and deconvolved with software MAPPING of the GILDAS package" (Observations)
- **MADCUBA (incl. MADCUBA-AUTOFIT)** : hyperfine-structure line fitting giving peak flux, Vp, FWHM, opacity and column density  
  > "The best fit peak fluxes, $F_{\nu}$, of the analysed hyperfine components have been obtained with the software MADCUBA" (14N/15N)
- **CDMS** : spectroscopic line parameters in Table 1  
  > "taken from the Cologne Molecular Database for Spectroscopy (CDMS; Endres et al. (cite: endres))" (Table 1)
- **JPL catalog** : relative hyperfine intensities for N2H+ (1-0)  
  > "and the Jet Propulsion Laboratory (JPL) catalog" (14N/15N)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| R = 14N/15N from 15NNH+, FIR4-tot | 280 | 60 | dimensionless | 5 | 280$\pm$60 |
| R = 14N/15N from N15NH+, FIR4-tot | 280 | 50 | dimensionless | 5 | 280$\pm$50 |
| R from 15NNH+, FIR4-east | 360 | 140 | dimensionless | 5 | 360$\pm$140 |
| R from N15NH+, FIR4-east | 200 | 70 | dimensionless | 5 | 200$\pm$70 |
| R from 15NNH+ and N15NH+, FIR4-west | 330 (both) | 80 | dimensionless | 5 | 330$\pm$80 |
| R from 15NNH+ and N15NH+, FIR4-peak | 370 (both) | 150 | dimensionless | 5 | 370$\pm$150 |
| R from 15NNH+, FIR4-north | 330 | 120 | dimensionless | 5 | 330$\pm$120 |
| R from N15NH+, FIR4-north | 270 | 100 | dimensionless | 5 | 270$\pm$100 |
| R for FIR4-tot after optical depth correction (both isotopologues) | ~340 | 100 | dimensionless | 5 | to about $340\pm 100$ for both |
| R for FIR4-west after optical depth correction | 400 | 120 | dimensionless | 5 | to $400\pm 120$ |
| Optical depth correction factor tau/(1-exp(-tau)) for tau=0.4 | ~1.21 | not stated | dimensionless | 5 | $\tau/(1-\exp{(-\tau)})\sim 1.21$ |
| Lower limit on R in the diffuse envelope | >= 100-150 | not stated | dimensionless | 7 | $\geq 100-150$ |
| Fraction of extended N2H+ (1-0) flux missed relative to IRAM-30m beam | at most 10 | not stated | percent | 2 | we miss at most $10\%$ of extended flux in N$_{2}$H$^{+}$ (1–0) |
| N(N2H+) range across regions | ~0.7-1.7 x 10^14 | see Table 6 | cm^-2 | 6 | are in the range $\sim 0.7 - 1.7\times 10^{14}$ cm$^{-2}$ for N$_{2}$H$^{+}$ |
| N(N2D+) range across regions | ~2.5-13.8 x 10^11 | see Table 6 | cm^-2 | 6 | $\sim 2.5 - 13.8\times 10^{11}$ cm$^{-2}$ for N$_{2}$D$^{+}$ |
| D/H (Tex free / 35 K / 45 K), FIR4-tot | 5 / 6 / 6 x 10^-3 | +/-1 each | dimensionless | 6 | 5$\pm1$ - 6$\pm$1 - 6$\pm$1 |
| D/H (Tex free / 35 K / 45 K), FIR4-east | 2.6 / 2.9 / 2.9 x 10^-3 | +/-0.5, 0.6, 0.6 | dimensionless | 6 | 2.6$\pm$0.5 - 2.9$\pm$0.6 - 2.9$\pm$0.6 |
| D/H (Tex free / 35 K / 45 K), FIR4-peak | 8 / 9 / 9 x 10^-3 | +/-2 each | dimensionless | 6 | 8$\pm$2 - 9$\pm$2 - 9$\pm$2 |
| D/H (Tex free / 35 K / 45 K), FIR4-north | 12 / 14 / 14 x 10^-3 | +/-2, 3, 3 | dimensionless | 6 | 12$\pm$2 - 14$\pm$3 - 14$\pm$3 |
| H/D range across regions | ~70 (FIR4-north) to ~380 (FIR4-east) | not stated | dimensionless | 7 | H/D varies from $\sim 70$ in "FIR4-north" to $\sim 380$ in "FIR4-east" |

## Qualitative findings

- Rare 15N isotopologues are much more compact than N2H+ and not detected in the diffuse N2H+ envelope, probably due to the uniform sensitivity achieved.  
  > "clearly the rare isotopologues are not detected towards the diffuse N$_{2}$H$^{+}$ emission" (Results)
- No significant extended N2H+ emission is resolved out by the interferometer.  
  > "Hence, we can conclude that our analysis is not affected by any significant extended emission resolved out." (Results)
- A filamentary N2H+ feature connects FIR4 to FIR5 towards the south.  
  > "A filamentary N$_{2}$H$^{+}$ feature connects FIR4 to FIR5 towards the south." (Results)

## Claim tuples

- H: Does 14N/15N vary between cores in OMC-2 FIR4 and differ from the single-dish value? | E: Ratio of hyperfine peak fluxes of N2H+ to 15NNH+ and N15NH+ in five regions, compared with IRAM-30m | R: R is ~200-370 in all regions within large errors and consistent with single-dish values | F: 14N/15N does not change from core to core nor from single-dish to interferometric scales | **supported**
- H: Do the two 15N-bearing isotopologues give different R? | E: R computed separately from 15NNH+ and N15NH+ in each region | R: Largest discrepancy in FIR4-east (360+/-140 vs 200+/-70), still consistent within errors | F: no significant difference between the two isotopologues | **supported**
- H: Does N fractionation depend on temperature, as traced by D/H? | E: D/H from N2D+ and N2H+ column densities compared with R in each region | R: D/H ranges from 2.6e-3 (FIR4-east) to 1.4e-2 (FIR4-north) while R stays constant | F: 14N/15N does not depend on temperature variations (no N-H fractionation correlation) | **supported**
- H: Is the 15N enrichment seen in Solar System objects inherited from the protocluster stage? | E: Compare R across OMC-2 FIR4 cores with pristine Solar System values and pre-stellar cores | R: R constant at core scales (~600 au), but only a lower limit R>=100-150 in the envelope | F: variations are likely not inherited from the protocluster stage; an envelope-to-core change cannot be ruled out | **partially**

## Reasoning

- Why this data: Single-dish measurements average over ~10000 au, so local 15N enriched or depleted spots could be hidden; ALMA gives ~600 au resolution.  
  > "so that it cannot be excluded the presence of local spots enriched (or depleted) in $^{15}$N." (Introduction)
- Why this method: Peak flux ratio of isolated hyperfine components is equivalent to the total-flux ratio when optically thin with equal widths; D/H needed column densities because of different quantum numbers.  
  > "then the ratio between the peak flux densities of these components is equivalent to the ratios between the total flux densities of the lines." (14N/15N); "Due to the different quantum numbers of these transitions" (D/H)
- Alternative: N2H+ was fitted with three Tex assumptions (free, 35 K, 45 K) to test hyperfine anomalies and opacity effects  
  > "we have performed a more accurate analysis of the line profile assuming three different $T_{\rm ex}$" (14N/15N)
- Alternative: Two alternative scenarios for the 15N enrichment: at the protoplanetary disk stage, or at different stages depending on the molecule  
  > "we propose hence two alternative scenarios for the $^{15}$N enrichment" (Discussion and conclusions)
- How they decided it was enough: _not stated_
- Limitation (authors): Uncertainties on opacities are underestimated when Tex is fixed in MADCUBA  
  > "we stress that in some cases the uncertainties on the opacities are underestimated" (14N/15N)
- Limitation (authors): A change of R from envelope to protocluster cannot be excluded; envelope limit R>=100-150 is not stringent  
  > "hence not sufficient to put stringent constraints" (Discussion and conclusions)
- Limitation (authors): Residual feature in N2D+ possibly from CH3CHO contamination; extra feature in some N15NH+ spectra at ~9 km/s  
  > "This could be due to a contamination from the transition" (D/H)
- Caveat (inferred, ours): R uncertainties are large (20-40%), so the claim of no variation is weakly constraining
- Caveat (inferred, ours): Regions were hand-drawn and overlap (FIR4-tot is a union of other regions), so values are not independent
- Caveat (inferred, ours): Low S/N for 15NNH+ in FIR4-east (~4.2) and single-line peak-flux ratio ignores hyperfine anomalies beyond a rough estimate
- Caveat (inferred, ours): D/H spans a factor ~5 yet the abstract calls it an order of magnitude

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters and the GILDAS MAPPING scripts
- Missing: Region polygons for the five regions
- Missing: MADCUBA fit configuration and initial parameters
- Missing: Array and configuration details and calibration pipeline/manual choice
- Data volume (inferred): Roughly tens of GB of raw visibilities for 136 min Band 3 plus 32 min Band 4 with 40 antennas (estimate, not stated)
- Score (inferred): 3/5, ALMA project code is given and key numeric results are tabulated, but imaging parameters, line-free channels, hand-drawn region boundaries and MADCUBA fit setup are not given.
- Rediscovery candidate: no, The paper does not state data are public, and regions drawn by hand plus unstated imaging and fit settings prevent a complete recipe, though the results are numeric.

## Links

- Method: Kahane et al. 2018 (cite: kahane18) (Single-dish 14N/15N method and hyperfine parameters)
- Method: Colzi et al. 2019 (cite: colzi19) (Interferometric R from N2H+ and MADCUBA-AUTOFIT approach)
- Method: Martín et al. 2019 (cite: martin19) (MADCUBA fixed-parameter error treatment)
- Companion: Neri et al. in prep. (Forthcoming paper on the continuum emission of this ALMA dataset)
- Companion: Fontani et al. 2017 (cite: fontani17) (82 GHz continuum map of OMC-2 FIR4 shown for reference)
- Related: ALMA project 2016.1.00681.S (PI: F. Fontani)

## Checks

```json
{
 "quotes": 122,
 "quotes_ok": 122,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2016.0.00681.S"
 ],
 "numeric_results": 20,
 "numeric_problems": 0,
 "fill": {
  "facts": 103,
  "stated": 75,
  "rate": 0.728
 },
 "evidence_ok": true
}
```
