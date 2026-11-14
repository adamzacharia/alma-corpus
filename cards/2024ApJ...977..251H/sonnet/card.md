# Molecular Gas Mass Measurements of an Active, Starburst Galaxy at z ≍ 2.6 Using ALMA Observations of the [C I], CO, and Dust Emission

`2024ApJ...977..251H` | The Astrophysical Journal 2024 | first author: Huang, Hao-Tse | arXiv: 2411.04290 | DOI: 10.3847/1538-4357/ad9021

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: What are the molecular gas mass and ISM excitation conditions of a z=2.57 radio-loud starburst galaxy, as inferred from [CI], CO and dust emission?  
  > "The main goal is to use  as a test for various -mass calibrators and to characterize its ISM conditions." (Introduction)
- Target **radio galaxy at z=2.5725 (name not given in text)**: coordinates RA 5h30m25.44s, Dec -54d54m23.19s  
  > "Systemic redshift$^{(b)}$ () | $2.5725\pm0.0003$" (Table 1); "RA$^{(a)}$ | $5^h30^m25^s.44$" (Table 1); z/distance z = 2.5725 ± 0.0003  
  > "Systemic redshift$^{(b)}$ () | $2.5725\pm0.0003$" (Table 1); "RA$^{(a)}$ | $5^h30^m25^s.44$" (Table 1); distance from Man2019 (systemic redshift)  
  > "Systemic redshift$^{(b)}$ () | $2.5725\pm0.0003$" (Table 1); "RA$^{(a)}$ | $5^h30^m25^s.44$" (Table 1)

## Data provenance

- ALMA projects: 2018.1.01669.S, 2013.1.00521.S
- bands: Band 4 and Band 6  
  > "was observed with the ALMA 12 m array using both Band 4 and Band 6 during Cycle 6" (2.1 ALMA observations)
- frequencies and spectral setup: Band 4 SPWs at 126.421, 128.379, 138.483, 140.129 GHz; Band 6 SPWs at 226.200, 228.075, 240.000, 241.875 GHz; 1.875 GHz bandwidth each, 480 channels, 3.90625 MHz native  
  > "The four spectral windows were centered at 226.200 GHz, 228.075 GHz, 240.000 GHz, and 241.875 GHz, respectively" (2.1 ALMA observations); "Each spectral window spanned a bandwidth of 1.875 GHz and contained 480 channels each." (2.1 ALMA observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: Band 4 C43-8; Band 6 roughly C43-6 and C43-7  
  > "43 antennae arranged in an extended configuration (C43-8) with baselines ranging from 92 m to 8547 m" (2.1 ALMA observations)
- baselines: Band 4: 92 m-8547 m; Band 6: 15 m-5893 m  
  > "the baselines ranged from 15 m to 5893 m" (2.1 ALMA observations)
- angular resolution: Band 4 0.13x0.12 arcsec; Band 6 0.14x0.13 arcsec  
  > "0.13$''$$\times$0.12$''$ at PA 48" (Table 2)
- max recoverable scale: _not stated_
- sensitivity: Continuum RMS 10 (Band 4) and 11 (Band 6); line RMS ≈0.25 and ≈0.17 mJy per channel  
  > "$\approx0.17$ per 31.0 km s$^{-1}$ channel" (Table 2)
- time on source: Band 4: 49.28 min; Band 6: 81.06 min  
  > "The total on-source integration time was 49.28 minutes." (2.1 ALMA observations); "resulting in a total on-source integration time of 81.06 minutes" (2.1 ALMA observations)
- observing dates: Band 4: 18 Jul 2019; Band 6: 9, 23 Aug and 18 Sep 2019  
  > "on 9, 23 August, 2019 and 18 September 2019" (2.1 ALMA observations)
- pi or archival as stated: PI Federico Lelli (Cycle 6); Cycle 2 data PI Carlos De Breuck used for comparison only  
  > "project code 2018.1.01669.S, PI: Federico Lelli" (2.1 ALMA observations)
- Line: [CI] 3P2-3P1 (2-1) (not stated)
- Line: CO J=7-6 (not stated)
- Line: [CI] 3P1-3P0 (1-0) (not stated)
- Line: CO J=4-3 (not stated)
- External data: Dust temperature 45 (+23/-17) K and SED fit from Falkendal2019; dust flux 1.33±0.16 mJy  
  > "dust temperature of $\Td=45^{+23}_{-17}\,$K derived from the SED fitting" (3.4 Line ratios) [from (cite: Falkendal2019)]
- External data: CO(4-3)/CO(1-0) ratio r41=0.46 for SMGs  
  > "$r_{41}\equiv\LineLum{\COfourthree}/\LineLum{\COonezero}=0.46$ (cite: Carilli2013)" (3.3.2 The CO approach) [from (cite: Carilli2013)]
- External data: alpha_CO = 0.8 for starbursts  
  > "we adopted the value commonly used for starburst galaxies, 0.8 M$_\odot$/(K$\cdot$km s$^{-1}$$\cdot$pc$^2$) (cite: Bolatto2013)" (3.3.2 The CO approach) [from (cite: Bolatto2013)]
- External data: [CI] abundance 3e-5 (M82)  
  > "we adapted the atomic carbon abundance $\,=\,3\times10^{-5}$ as derived by (cite: Weiss2003) for M82" (3.3.1 The Atomic Carbon approach) [from (cite: Weiss2003)]
- External data: Dust-to-gas calibration alpha_dust=6.7e19 and eq. 16  
  > "Here we use $\alphadust=6.7\cdot10^{19}$ erg s$^{-1}$ Hz$^{-1}$ M$_\odot$$^{-1}$ and equation (16) in (cite: Scoville2016)" (3.3.3 The dust emission approach) [from (cite: Scoville2016)]
- External data: Comparison compilation of high-z line ratios  
  > "the compilation of high-redshift galaxies presented in (cite: Valentino2020)" (3.4 Line ratios) [from (cite: Valentino2020)]

## Processing

### Calibration

- pipeline or manual: Observatory-delivered pipeline calibration script; measurement sets restored with CASA  
  > "using pipeline version 42866M with the calibration script delivered by the observatory" (2.1 ALMA observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0519-4546 (pointing, bandpass, flux); J0550-5732 phase  
  > "J0519-4546 was used as pointing, bandpass and flux calibrators, while J0550-5732 was used as phase calibrator." (2.1 ALMA observations)
- flux scale uncertainty: ~5 percent, not included in analysis  
  > "Note that we do not include flux calibration error in our analysis." (2.1 ALMA observations)
- self calibration: _not stated_

### Imaging

- task: tclean in CASA 5.8.0  
  > "we used the `tclean` task in CASA version 5.8.0 to image the measurement sets" (2.1 ALMA observations)
- deconvolver: _not stated_
- weighting robust: Briggs robust=2  
  > "weighting with `robust=2` (similar to natural weighting)" (2.1 ALMA observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Image plane imcontsub, zeroth-order polynomial per sideband (uvcontsub over-subtracted)  
  > "We thus subtracted the continuum on the image plane using `imcontsub` by modeling it as a zeroth-order polynomial across each side band" (2.2 Continuum modeling and subtraction)
- line free channels: Band 6: three SPWs excluding the one with lines; Band 4: 126.031–127.332, 127.543–128.9, 138.2–139.2, 139.267–140.743 GHz  
  > "126.031–127.332 GHz, 127.543–128.9 GHz, 138.2–139.2 GHz, and 139.267–140.743 GHz" (2.1 ALMA observations)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Cubes binned by 3 (Band 4) and 6 (Band 6) channels to 11.71875 and 23.43704 MHz  
  > "to a channel width of 11.71875 MHz and 23.43704 MHz, respectively" (2.1 ALMA observations)
- final beam: Band 4 0.13x0.12 arcsec PA 48; Band 6 0.14x0.13 arcsec PA -46  
  > "0.14$''$$\times$0.13$''$ at PA $-46$" (Table 2)
- final rms: _not stated_

### Inherited from earlier work

- Same Cycle 2 data analysed earlier; comparison of previous [CI](2-1) mass  
  > "Shallower ALMA Band 6 observations of  were analyzed and published in (cite: Lelli2018) and (cite: Man2019)" (2.1 ALMA observations) [from (cite: Lelli2018); (cite: Man2019)]
- Tex formula assuming optically thin LTE  
  > "As derived in the Appendix of (cite: Schneider2003), by assuming that both of the two  lines are optically thin" (3.3.1 The Atomic Carbon approach) [from (cite: Schneider2003)]
- Line luminosity conversion  
  > "We used equation (3) in (cite: Solomon1992) to convert the observed line fluxes into line luminosities" (3.3.1 The Atomic Carbon approach) [from (cite: Solomon1992)]

### Not stated but needed to reproduce (our reading)

- Spatial extent and orientation of the elliptical extraction aperture
- Exact velocity ranges / channels used in spectral fits and moment maps
- Line-free channels used for imcontsub
- tclean cell size, image size, masks, threshold, niter
- Rest frequencies adopted
- Dust SED/Gamma_RJ value for Td=25 K
- Initial guesses for Gaussian/imfit regions

## Analysis recipe

1. **Image continuum and cubes**: tclean with Briggs robust=2, line-free continuum, binned cubes  
  > "The continuum images are created using line-free channels." (2.1 ALMA observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Confirmed adding semi-pass execution lowered noise  
  > "confirmed that the addition of the calibrated dataset leads to reduced noise in the resulting image" (2.1 ALMA observations)
2. **Fit continuum components**: 2D Gaussian fits with imfit to each component  
  > "by using the CASA task `imfit` to fit a 2D Gaussian profile to each component" (3.1 Continuum fitting)
   - software: CASA imfit
   - fitting: _not stated_
   - validation: Band 4 excluded because spectral index 0.63±0.29 implausible  
  > "Due to the irregular shape of the ALMA Band 4 continuum and the unclear nature of the low spectral index, we present the fitted fluxes of ALMA Band 4 continuum in Table" (3.1 Continuum fitting)
3. **Extract spectra and fit lines**: Elliptical aperture spectrum; Gaussian lines plus first-order polynomial continuum; 1000 Monte Carlo realizations  
  > "We model each emission line with a Gaussian profile and the continuum as a first-order polynomial" (3.2.1 Spectral analysis); "we utilized the Monte Carlo technique to re-sample and fit the spectrum 1000 times" (3.2.1 Spectral analysis)
   - fitting: Gaussian + linear continuum, MC noise resampling  
  > "We model each emission line with a Gaussian profile and the continuum as a first-order polynomial" (3.2.1 Spectral analysis)
   - validation: _not stated_
4. **Moment-0 maps and size**: spectral-cube moment over ±2σ of Gaussian; size from 3σ contour  
  > "The integration range of velocity was chosen to be $[v_{c}-2\sigma_v,v_{c}+2\sigma_v]$" (3.2.2 Emission line morphology)
   - software: spectral-cube
   - fitting: _not stated_
   - validation: _not stated_
5. **Derive molecular gas mass three ways**: [CI] with LTE Tex, CO(4-3) with r41 and alpha_CO, Band 6 dust with Scoville2016  
  > "we are able to derive the molecular gas mass via three different independent approaches" (3.3 Inference of molecular gas masses)
   - assumption: X_CI=3e-5, r41=0.46, alpha_CO=0.8, Td=25 K, alpha_dust=6.7e19, helium factor 1.36  
  > "assuming a mass-weighted dust temperature of $\Td=25$ K" (3.3.3 The dust emission approach)
   - fitting: _not stated_
   - validation: Checked Q10=0.44±0.02 against Papadopoulos2022 value 0.48  
  > "Our value, $Q_{10}=0.44\,\pm\,0.02$, is 8 percent lower than (cite: Papadopoulos2022)’s suggested value." (3.3.1 The Atomic Carbon approach)

## Software

- **CASA** 5.8.0 (pipeline 42866M): calibration restore, tclean, imfit, imcontsub  
  > "we used the `tclean` task in CASA version 5.8.0" (2.1 ALMA observations)
- **spectral-cube** : moment-zero maps  
  > "using the `moment` task from Python package `spectral-cube`" (3.2.2 Emission line morphology)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| [CI](2-1) integrated flux | 4.04 | 0.30 | Jy km/s | 3 | 4.04 $\pm$ 0.30 |
| Band 6 dust host flux | 1.55 | 0.13 | mJy | 2 | Host galaxy    / flux (mJy)                /  1.55 $\pm$ 0.13 |
| Excitation temperature from [CI] | 44 | 16 | K | 5 | $R\,=\,0.84\,\pm\,0.20$ and $\Tex=44\,\pm\,16$ K |
| M_mol from [CI] | 3.1e11 | 0.6e11 | Msun | 5 | $(3.1\pm0.6)\times10^{11}\text{M\ensuremath{_\odot}}$ |
| M_mol from CO(4-3) | 7.3e10 | 0.9e10 | Msun | 5 | $(7.3\ \pm\ 0.9)\times10^{10}$M$_\odot$ |
| M_mol from Band 6 dust | 2.2e11 | 0.2e11 | Msun | 5 | (2.2 $\pm$ 0.2)$\times10^{11}$M$_\odot$ |
| CO(7-6)/CO(4-3) ratio r74 | 0.34 | 0.06 | dimensionless | 5 | $r_{74}=0.34\pm0.06$ |
| CO(4-3) emission size | (7.7±0.9)x(4.9±0.9) | 0.9 kpc | kpc | 4 | (7.7 $\pm$ 0.9)$\times$(4.9 $\pm$ 0.9) kpc |

## Qualitative findings

- Four lines show different morphologies; extended SW emission seen in two lines  
  > "The four emission lines display different morphologies, suggesting spatial variation in the gas excitation conditions." (abstract)

## Claim tuples

- H: Do three tracers give consistent molecular gas mass? | E: [CI], CO(4-3), dust continuum mass estimates | R: 3.1e11, 0.73e11, 2.2e11 Msun | F: All ~1e11 but differ up to factor 4; CO lowest | **partially**
- H: Is [CI] subthermally excited? | E: Tex from [CI] ratio compared to dust temperature | R: Tex=44±16 K vs Td=45 K | F: No case for subthermal excitation | **supported**
- H: Deeper data reveal more extended gas than before | E: Cycle 6 vs Cycle 2 comparison | R: [CI](2-1) flux 4.04 vs 2.0 Jy km/s | F: Previous mass underestimated by ~order of magnitude | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Dust-based Band 6 only because Band 4 contaminated by synchrotron  
  > "the Band 4 dust continuum emission is potentially contaminated by the synchrotron component" (3.3.3 The dust emission approach)
- Alternative: uv-plane continuum subtraction rejected as it over-subtracted  
  > "the continuum appeared to be over-subtracted when performed on the uv-plane especially in Band 6" (2.2 Continuum modeling and subtraction)
- How they decided it was enough: _not stated_
- Limitation (authors): Systematic uncertainties in X_CI, alpha_CO, r41, dust parameters  
  > "The molecular gas mass inferred using three different tracers are all subject to systematic uncertainties." (3.3.4 Uncertainties)
- Caveat (inferred, ours): Flux calibration error not propagated
- Caveat (inferred, ours): Band 4 continuum deblending unreliable
- Caveat (inferred, ours): Aperture choice affects fluxes
- Caveat (inferred, ours): Quoted errors exclude systematics in conversion factors

## Reproducibility

- Data public (paper): ALMA program data cited; public status not explicitly stated  
  > "This paper makes use of data from ALMA program ADS/JAO.ALMA#2013.1.00521.S, ADS/JAO.ALMA#2018.1.01669.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Aperture geometry
- Missing: tclean image parameters
- Missing: Gamma_RJ value and luminosity distance details
- Data volume (inferred): ~50-150 GB raw for two bands
- Score (inferred): 6/5, Standard CASA workflow and explicit formulas, but aperture and imaging parameters not given.
- Rediscovery candidate: yes, Archive data with explicit formulas and numeric results, though some imaging settings missing.

## Links

- Method: (cite: Scoville2016) (dust-based gas mass calibration)
- Method: (cite: Weiss2003) ([CI] mass formula)
- Companion: Lin et al. (accepted in A&A) (3D kinematic analysis of same data)
- Companion: (cite: Man2019) (earlier Cycle 2 analysis)
- Companion: (cite: Lelli2018) (earlier ALMA CO/[CI] disk modeling)

## Checks

```json
{
 "quotes": 72,
 "quotes_ok": 72,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2013.1.00521.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 48,
  "rate": 0.658
 },
 "evidence_ok": true
}
```
