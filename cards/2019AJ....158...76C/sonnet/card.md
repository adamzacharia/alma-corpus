# ALMA Spectral Imaging of Titan Contemporaneous with Cassini's Grand Finale

`2019AJ....158...76C` | The Astronomical Journal 2019 | first author: Cordiner, M. A. | arXiv: 1907.04374 | DOI: 10.3847/1538-3881/ab2d20

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: solar_system, astrochemistry
- Question: What are the spatial distributions, abundances and chemical/dynamical lifetimes of Titan's nitriles and propane around the 2017 solstice, as seen by ALMA alongside Cassini CIRS?  
  > "Here we demonstrate the use of the Atacama Large Millimeter/submillimeter Array (ALMA) to continue Cassini’s legacy for chemical and climatological studies of Titan’s atmosphere." (abstract)
- Target **Titan**: coordinates _not stated_; z/distance 9.26 AU  
  > "a mask diameter of $1.3''$ (8700 km at Titan’s distance of 9.26 AU)" (2 ALMA Observations); distance from _not stated_

## Data provenance

- ALMA projects: 2016.A.00014.S
- bands: Band 7  
  > "Observations of Titan were carried out using the ALMA Band 7 receiver on 2017-05-08 and 2017-05-16" (2 ALMA Observations)
- frequencies and spectral setup: Two settings: 342-356 GHz and 349-364 GHz; spectral resolution 244-977 kHz (0.2-0.8 km/s)  
  > "(1) 342-356 GHz (877-842 $\mu$m) and (2) 349-364 GHz (859-824 $\mu$m), at a spectral resolution of 244-977 kHz (0.2-0.8 km $\rm{s}^{-1}$)" (2 ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15-1124 m, 46 active antennas  
  > "with 46 active antennas providing baselines in the range 15-1124 m" (2 ALMA Observations)
- angular resolution: ≈0.2'' (natural weighting)  
  > "resulting in a spatial resolution of $\approx0.2''$ (using natural visibility weighting)" (2 ALMA Observations)
- max recoverable scale: _not stated_
- sensitivity: RMS 2-4 mJy/beam/MHz  
  > "leading to RMS noise levels in the range 2-4 mJy beam$^{-1}$ MHz$^{-1}$" (2 ALMA Observations)
- time on source: 18 min in setting 1, 138 min in setting 2  
  > "The total on-source observing time was 18 min in setting 1 and 138 min in setting 2" (2 ALMA Observations)
- observing dates: 2017-05-08 and 2017-05-16  
  > "on 2017-05-08 and 2017-05-16" (2 ALMA Observations)
- pi or archival as stated: Director's discretionary time program  
  > "as part of the director’s discretionary time program 2016.A.00014.S" (2 ALMA Observations)
- Line: HCN 4-3 (354505 MHz)
- Line: HNC 4-3 (362630 MHz)
- Line: HC3N 40-39 (363785 MHz)
- Line: C3H8 8_6-7_5 (360978 MHz)
- Other facility **Cassini CIRS**: Nadir maps and limb spectra for HCN and HC3N (orbits #261, #275) for comparison with ALMA  
  > "The data presented here were obtained on orbits #261 (2017-02-17) and #275 (2017-05-24)" (3 Cassini Observations)
- External data: Atmospheric density profile for the emission model  
  > "The density profile was taken from (cite: kra09)" (4.4 ALMA Limb Abundance Retrievals) [from (cite: kra09)]
- External data: Molecular line parameters from CDMS  
  > "Spectral line fluxes were generated using parameters from the Cologne Database for Molecular Spectroscopy (cite: mul01)" (4.4 ALMA Limb Abundance Retrievals) [from (cite: mul01)]
- External data: Modeled chemical/dynamical lifetimes at 300 km  
  > "Lifetimes ($L_{300}$) are the chemical/dynamical lifetimes at 300 km from (cite: vui19)." (Table 2) [from (cite: vui19)]

## Processing

### Calibration

- pipeline or manual: Automated JAO pipeline scripts  
  > "Data were flagged and calibrated in CASA 5.1 (cite: jae08) using the automated pipeline scripts supplied by the Joint ALMA Observatory (cite: shi15)." (2 ALMA Observations)
- casa version: CASA 5.1  
  > "Data were flagged and calibrated in CASA 5.1 (cite: jae08)" (2 ALMA Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1733-1304, measured 2017-05-04 and 2017-05-17  
  > "The flux of the calibration quasar J1733-1304 was measured on 2017-05-04 and 2017-05-17" (2 ALMA Observations)
- flux scale uncertainty: ±6%  
  > "with an accuracy of $\pm6$%, implying a similar accuracy in the flux scale of our calibrated spectra" (2 ALMA Observations)
- self calibration: _not stated_

### Imaging

- task: Clark clean algorithm  
  > "Imaging and deconvolution were performed using the `Clark clean` algorithm" (2 ALMA Observations)
- deconvolver: _not stated_
- weighting robust: Natural for maps; Briggs robust = 0 for limb profiles  
  > "Briggs weighting of the interferometric data was used (with a $robust$ parameter of zero)" (4.4 ALMA Limb Abundance Retrievals)
- uv taper: _not stated_
- cell size: 0.025''  
  > "with a pixel size of $0.025''$" (2 ALMA Observations)
- image size: _not stated_
- masking: 1.3'' diameter mask; threshold twice expected RMS  
  > "a flux threshold of twice the expected RMS noise and a mask diameter of $1.3''$" (2 ALMA Observations)
- multiscale scales: _not stated_
- continuum subtraction: Low-order polynomial fits to line-free adjacent regions  
  > "Titan’s continuum flux was subtracted using low-order polynomial fits to the (line-free) spectral regions adjacent to our lines of interest." (2 ALMA Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Images degraded to circular PSF equal to the long axis of the beam for latitudinal profiles  
  > "it was first necessary to degrade the resolution of our images so as to produce a circular PSF (with diameter equal to that of the long-axis of the original beam ellipse)" (4.2 Latitudinal Profiles)
- final beam: 0.15x0.13'' (≈900 km) at 362 GHz for robust=0  
  > "leading to a resolution of $0.15\times0.13''$ ($\approx900$ km) at 362 GHz" (4.4 ALMA Limb Abundance Retrievals)
- final rms: _not stated_

### Inherited from earlier work

- Temperatures retrieved from CIRS CH4 limb observations using an earlier method  
  > "using the method of (cite: tea07)" (4.4 ALMA Limb Abundance Retrievals) [from (cite: tea07)]
- Lifetime from model with aerosol sticking for C2H5CN  
  > "The lifetime for C$_2$H$_5$CN is from a model including loss *via* sticking to aerosols." (Table 2) [from (cite: vui19)]
- Date of last circulation reversal (2011)  
  > "(cite: vin15) determined that the last circulation reversal occurred in 2011" (5.2.1 Inferred molecular lifetimes) [from (cite: vin15)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges and polynomial order for continuum subtraction
- Number of clean iterations and spectral windows/channel widths used in the cubes
- Integration velocity ranges for each moment-0 map
- How the two days' data were weighted and combined
- Flux-weighted CIRS temperature profile and exact Simobserve configuration
- Initial guesses and bounds for the MPFIT fits
- Titan ephemeris used for tracking and Doppler shifting

## Analysis recipe

1. **Calibrate and image data**: JAO pipeline calibration; days combined after regridding and Doppler-shifting to Titan's rest frame; position offset corrected; continuum subtracted; Clark clean  
  > "The data from May 8 and May 16 were combined after regridding and Doppler-shifting to Titan’s rest frame." (2 ALMA Observations)
   - software: CASA
   - parameter: pixel 0.025'', mask 1.3''  
  > "with a pixel size of $0.025''$" (2 ALMA Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract spectra and moment maps**: Spectra integrated in 4300 km radius aperture; features >3σ integrated into emission maps  
  > "Spectral features greater than $3\sigma$ above the noise were identified and integrated to produce the emission maps" (4.1 Spectra and Maps)
   - parameter: C2H3CN integration width 1.2 km/s per line, 360.8-361.7 GHz  
  > "adopting a 1.2 km $\rm{s}^{-1}$ integration width for each spectral line" (4.1 Spectra and Maps)
   - assumption: Optically thin emission for most lines  
  > "the majority of the observed molecular emission is expected to be optically thin" (4.1 Spectra and Maps)
   - fitting: _not stated_
   - validation: Compared with CIRS maps  
  > "While the spatial resolution is significantly better than obtained by ALMA, the basic morphology of the resulting maps is similar, with a dominant south-polar emission peak for HC$_3$N" (Spectra and Maps)
3. **Latitudinal and longitudinal flux profiles**: Average flux in radial wedges about Titan's center using circularized beam; east-west difference for HNC  
  > "A wedge size $\phi_w=10^{\circ}$ was used for all molecules apart from C$_2$H$_3$CN and C$_3$H$_8$, for which $30^{\circ}$ was used" (4.2 Latitudinal Profiles)
   - fitting: _not stated_
   - validation: Circularized beam removes beam-smearing artifacts  
  > "Use of a circularized beam renders this result free from any geometrical artifacts related to (elliptical) beam smearing." (4.3 Longitudinal Variability of HNC)
4. **Retrieve limb abundance profiles**: Fit S(r) profiles with spherically symmetric model with polygonal abundance x(z), passed through ALMA simulator  
  > "the resulting images were passed through the ALMA simulator (using the `Simobserve` and `Clean` tasks)" (4.4 ALMA Limb Abundance Retrievals)
   - software: MPFIT, CASA simobserve, CASA clean
   - parameter: Wedges phi=45-135 and 225-315 deg  
  > "averaged within angular regions $\phi=45$-135$^{\circ}$ and $\phi=225$-315$^{\circ}$" (4.4 ALMA Limb Abundance Retrievals)
   - assumption: Optically thin emission; density from Krasnopolsky 2009; temperature from CIRS CH4 limb at -27 deg  
  > "under the assumption of optically thin emission" (4.4 ALMA Limb Abundance Retrievals)
   - fitting: Nonlinear least squares with MPFIT; 1σ errors from covariance matrix  
  > "obtained through nonlinear least-squares optimization using the MPFIT routine (cite: mar12), and $1\sigma$ parameter errors were determined from the covariance matrix" (4.4 ALMA Limb Abundance Retrievals)
   - validation: Contribution functions for altitude sensitivity; comparison with CIRS retrievals  
  > "contribution functions (total flux as a function of altitude) were calculated within an ALMA beam centered at the respective $r_p$ value" (4.4 ALMA Limb Abundance Retrievals)
5. **Derive lifetimes from polar flux decay**: Exponential decay of north polar flux from southern peak flux over 6 yr  
  > "Assuming exponential decay of the form $dF_N/dt=F_Se^{-t/\tau}$, the following lifetimes $\tau$ were derived" (5.2.1 Inferred molecular lifetimes)
   - assumption: South pole at steady state; peak flux equals the north peak at 2011 reversal  
  > "the peak of the spectrally integrated flux in the southern hemisphere ($F_S$) for a given species at the present epoch is taken to be representative of the peak flux that would have been present in the north" (5.2.1 Inferred molecular lifetimes)
   - fitting: _not stated_
   - validation: Compared with Vuitton et al. 2019 model lifetimes  
  > "These values are in reasonable agreement with the chemical/dynamical lifetimes ($L_{300}$) from the model of (cite: vui19)" (Inferred molecular lifetimes)
6. **Retrieve CIRS limb profiles for comparison**: NEMESIS fit of -11 deg limb radiances from orbit #261  
  > "The NEMESIS spectral inversion tool (cite: irw08) was used to fit the $-11^{\circ}$ limb observations from orbit #261" (5 Comparison with Cassini CIRS)
   - software: NEMESIS
   - parameter: cubic b-spline knot spacing 100 km  
  > "a cubic b-spline curve was fitted to the measured radiance profiles at each wavenumber using a knot spacing of 100 km" (5 Comparison with Cassini CIRS)
   - fitting: _not stated_
   - validation: Reliable for 180-400 km  
  > "The profiles obtained are reliable for 180-400 km; below 180 km the line opacity was too high to allow an accurate determination, and above 400 km the signal-to-noise was too low." (Comparison with Cassini CIRS)

## Software

- **CASA** 5.1: Calibration, imaging, simobserve/clean  
  > "Data were flagged and calibrated in CASA 5.1 (cite: jae08)" (2 ALMA Observations)
- **MPFIT** : Nonlinear least-squares fitting of limb profiles  
  > "using the MPFIT routine (cite: mar12)" (4.4 ALMA Limb Abundance Retrievals)
- **NEMESIS** : CIRS limb spectral inversion  
  > "The NEMESIS spectral inversion tool (cite: irw08) was used" (5 Comparison with Cassini CIRS)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HNC lower altitude of emission | 730 | ±60 | km | 4 | found to be confined predominantly to altitudes above $730\pm60$ km |
| HNC east-west asymmetry | 13 | ±3 | % | 3 | which amounts to a ratio $S_E/S_W=(13\pm3)$% |
| HNC eastern flux | 383 | ±7 | mJy km/s | 3 | $S_E=383\pm7$ mJy km $\rm{s}^{-1}$ |
| HNC western flux | 338 | ±7 | mJy km/s | 3 | $S_W=338\pm7$ mJy km $\rm{s}^{-1}$ |
| HNC abundance above 1030 km | 4.3e-5 | ±1.3e-5 | dimensionless | 4 | with an abundance of $(4.3\pm1.3)\times10^{-5}$ above 1030 km |
| HC3N lifetime | 3.4 | not stated | yr | 5 | HC$_3$N: 3.4 yr, C$_2$H$_3$CN: $<11.3$ yr, C$_2$H$_5$CN: 9.3 yr |
| C2H5CN lifetime | 9.3 | not stated | yr | 5 | HC$_3$N: 3.4 yr, C$_2$H$_3$CN: $<11.3$ yr, C$_2$H$_5$CN: 9.3 yr |
| HNC peak emission radius | 3140 | not stated | km | 4 | the very high HNC peak emission radius of 3140 km is particularly surprising |

## Qualitative findings

- HC3N, C2H3CN, C2H5CN show compact south polar peaks; HCN and CH3CN are more uniform in latitude  
  > "whereas the HC$_3$N, C$_2$H$_3$CN and C$_2$H$_5$CN maps are dominated by polar emission, with the southern (winter) pole being strongest for the latter three species." (4.1 Spectra and Maps)

## Claim tuples

- H: HNC is confined to Titan's thermosphere and shows east-west asymmetry | E: Limb profile modeling and wedge flux analysis of HNC map | R: HNC above 730±60 km; E/W flux ratio 13±3% | F: HNC probes rapid ionospheric processes consistent with HCNH+ recombination model | **supported**
- H: ALMA and CIRS give consistent results for HCN and HC3N | E: Compared maps and limb abundance retrievals | R: Morphology and abundances in reasonable agreement | F: ALMA sub-mm results consistent with Cassini IR | **supported**
- H: Nitrile lifetimes match chemical models | E: Polar flux decay lifetimes compared with Vuitton et al. 2019 | R: Few-year lifetimes for C2H3CN and C2H5CN | F: Close agreement with models including aerosol sticking | **supported**

## Reasoning

- Why this data: Contemporaneous with Cassini's final flybys for complementary sub-mm and IR diagnostics  
  > "the final opportunity for contemporaneous observations using ALMA and CIRS" (1 Introduction)
- Why this method: _not stated_
- Alternative: Diurnal temperature variation rejected as explanation for HNC asymmetry  
  > "diurnal temperature variations seem an unlikely explanation for the observed HNC asymmetry" (5.1 Chemistry and dynamics)
- How they decided it was enough: _not stated_
- Limitation (authors): Limb retrievals are approximate due to coarse resolution and simplified polygonal parameterization  
  > "our ALMA retrievals should be considered only approximate" (5.2.2 Comparisons with prior observations and models)
- Limitation (authors): Lifetime derivation relies on gross assumptions  
  > "Additional caution is required for their interpretation due to the gross assumptions made in their derivation." (5.2.1 Inferred molecular lifetimes)
- Caveat (inferred, ours): Lifetimes rest on a single epoch and steady-state assumption
- Caveat (inferred, ours): Optically thin assumption questionable for HCN and HC3N
- Caveat (inferred, ours): No uncertainties on the derived lifetimes
- Caveat (inferred, ours): 1D spherically symmetric limb model ignores latitude and longitude structure

## Reproducibility

- Data public (paper): DDT project data acknowledged; archive release not explicitly stated  
  > "It makes use of ALMA data set ADS/JAO.ALMA#2016.A.00014.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Custom limb emission model code and fit initial values
- Missing: Line-free channel ranges
- Missing: Exact flux integration velocity ranges
- Missing: CIRS data reduction details
- Data volume (inferred): ~50-200 GB raw (two EBs, 46 antennas, high spectral resolution)
- Score (inferred): 3/5, Data are DDT and likely public, but the limb model and several imaging settings are not fully specified.
- Rediscovery candidate: no, Key analysis relies on a custom radiative transfer model and unstated parameters.

## Links

- Method: (cite: tea07) (CIRS limb temperature retrieval method)
- Method: (cite: irw08) (NEMESIS retrieval tool)
- Companion: (cite: cor18) (HC3N vibrationally excited lines and isotopologues from the same data)
- Companion: (cite: lel19) (Contemporaneous ALMA Titan winds and HNC study)
- Companion: (cite: the19) (Prior ALMA equatorial abundance retrievals)
- Related: Cassini CIRS Titan program

## Checks

```json
{
 "quotes": 73,
 "quotes_ok": 73,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 56,
  "rate": 0.683
 },
 "evidence_ok": true
}
```
