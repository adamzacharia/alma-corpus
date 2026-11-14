# Low levels of sulphur dioxide contamination of Venusian phosphine spectra

`2022MNRAS.514.2994G` | Monthly Notices of the Royal Astronomical Society 2022 | first author: Greaves, Jane S. | arXiv: 2108.08393 | DOI: 10.1093/mnras/stac1438

Card schema 1.0 | model gemini-4-argon | depth full | type observational_alma_primary

## Science

- Fields: solar_system, astrochemistry
- Question: Could the 1.1 mm absorption features in Venus' atmosphere attributed to phosphine (PH3) be due to sulphur dioxide (SO2) absorption instead, and what is the level of SO2 contamination?  
  > "Critiques of our results have posed three main questions: (1) are the 1.1 mm features robust? (2) could they be due to SO 2 absorption rather than PH 3 ?" (1 INTRODUCTION); "We here expand on some of the technical issues in (1), and then focus on (2), with new analysis quantifying the level of SO 2 contamination of the 1.1 mm features we attributed to PH 3 ." (1 INTRODUCTION)
- Target **Venus**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2019.A.00023.S, 2018.A.00023.S
- bands: 1.1 mm  
  > "New analysis is presented of the 1.1 mm wavelength absorption lines in Venus’ atmosphere that suggested the presence of phosphine." (abstract)
- frequencies and spectral setup: 266.1 & 266.9 GHz, with 1875 & 117 MHz bands  
  > "ALMA 2019.A.00023.S 2019 March 5 3.5 hour block 266.1 & 266.9 GHz, with 1875 & 117 MHz bands" (Table 1)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15-314m (excluding <33m to reduce noise)  
  > "The ALMA interferometer was configured with baselines between antennas of 15-314m, but data shown here exclude baselines of <33m to reduce noise; the largest angular scale detected is then smaller than Venus." (Table 1)
- angular resolution: _not stated_
- max recoverable scale: 4.3 arcsec reliably imaged, 7.1 arcsec largest detected (without short baselines)  
  > "However, without the short baselines, the largest angular scale that is reliably imaged is 4.3 arcsec and the largest detected is 7.1 arcsec (Greaves et al. 2020)." (2.1 ALMA)
- sensitivity: _not stated_
- time on source: 3.5 hour block  
  > "ALMA 2019.A.00023.S 2019 March 5 3.5 hour block 266.1 & 266.9 GHz, with 1875 & 117 MHz bands" (Table 1)
- observing dates: 2019 March 5  
  > "ALMA 2019.A.00023.S 2019 March 5 3.5 hour block 266.1 & 266.9 GHz, with 1875 & 117 MHz bands" (Table 1)
- pi or archival as stated: PI dataset (re-calibrated and re-released by JAO/ESO in late 2020)  
  > "After the observatory (JAO/ESO) re-calibrated and re-released our Venus data in late 2020, the line-shapes were seen to be improved" (2.1 ALMA)
- Line: PH3 1-0 (266.946 GHz)
- Line: SO2 13(3,11)-13(2,12) (267.537 GHz)
- Line: SO2 30(9,21)-31(8,24) (not stated)
- Line: SO2 19(1,19)-18(0,18) (346.65217 GHz)
- Other facility **JCMT**: Whole-planet PH3 1-0 spectrum from June 2017 (project S16BP007) and archival HARP SO2 19(1,19)-18(0,18) spectra from May-June 2017 (project M17AP081)  
  > "The 1.1 mm data discussed here include: from the James Clerk Maxwell Telescope (JCMT), a centred-weighted whole-planet spectrum observed over a week in June 2017" (1 INTRODUCTION); "However, we have now found nearly contemporaneous monitoring of SO 2 in the JCMT public archive." (2.2 JCMT); "JCMT S16BP007 2017 June 16/14/12/11/9 30 minutes ×10 266.946 GHz, 250 MHz band 75% (at ≥ half-power of beam)" (Table 1)
- External data: Temperature-pressure profile of the Venus International Reference Atmosphere (VIRA) and altitude and diffusion profiles  
  > "The model uses the temperature-pressure profile of the Venus International Reference Atmosphere (VIRA), with details of the altitude and diffusion profiles listed in Greaves et al. (2020)." (3 MODELLING) [from Greaves et al. (2020)]
- External data: Mean-estimate of SO2 pressure-broadening coefficient of 0.18 cm^-1/atm and Case D SO2 abundance profile  
  > "We adopt as pressure-broadening coefficient the mean-estimate of 0.18 cm −1 /atm from Lincowski et al. (2021)." (3 MODELLING); "We adapted our simple radiative-transfer code for the SO 2 19(1,19)-18(0,18) transition to use the Case D abundance-profile from Lincowski et al. (2021; we made an empirical fit to the curve in their Figure 1b)." (5.2 Abundances) [from Lincowski et al. (2021)]
- External data: SO2 line-strengths via the HITRAN database  
  > "The SO 2 line-strengths are from Underwood et al. (2016, via the HITRAN database), but our code now additionally 4 scales line-strengths for temperature as a function of altitude, as described in Appendix A." (3 MODELLING) [from Underwood et al. (2016)]
- External data: Minimum height (60 km) where absorption against the continuum can occur at 346.6 GHz  
  > "The minimum height where absorption against the continuum can occur at this frequency was taken to be 60 km (Piccialli et al. 2017)." (5.2 Abundances) [from Piccialli et al. (2017)]
- Simulation/model as data: Simplified 1D semi-analytical radiative-transfer code calculating single line profiles in Venus' atmosphere from z = 0 to 115 km  
  > "Here we model SO 2 spectra using the simplified radiative-transfer code of Greaves et al. (2021a) — the implementation is described here in Appendix A, where a link is provided to the code." (3 MODELLING); "We develop a semi-analytical one-dimensional model for the line profile, starting at the surface of Venus, height 𝑧 = 0 km, and moving up in height increments based on the same temperature profile used by Greaves et al. (2021a), with the top of the atmosphere at 115 km." (APPENDIX A: LINE PROFILE MODEL)

## Processing

### Calibration

- pipeline or manual: Observatory (JAO/ESO) re-calibrated in late 2020, followed by custom processing scripts from Greaves et al. (2021a)  
  > "After the observatory (JAO/ESO) re-calibrated and re-released our Venus data in late 2020, the line-shapes were seen to be improved" (2.1 ALMA); "The spectra presented here use the processing scripts first published in Greaves et al. (2021a), but here we have recovered phosphine over a larger planetary area." (2.1 ALMA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: no, went beyond JAO-released re-processing by excluding short baselines and applying image-plane fits  
  > "Going beyond the JAO-released re-processing, Greaves et al. (2021a) excluded short antenna-baselines, and applied low-order image-plane fits." (2.1 ALMA)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 0.16 arcsec  
  > "The axes are RA,Dec with 0.16 arcsec pixels." (Figure 1 caption); "The new extracted spectrum is from a planet-spanning RA,Dec “box”, of 97x37 pixels where 1 pixel = 0.16 arcseconds." (4.1 ALMA 2019 data)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Image-plane polynomial fits subtracted (6th-order for narrowband PH3 1-0 data, 3rd-order for wideband SO2 data)  
  > "The second additional procedure involved subtracting image-plane fits, which were of 6 th -order for the narrowband data including PH 3 1-0, and of 3 rd -order for the simultaneous wideband data covering a strong SO 2 transition." (2.1 ALMA); "From left to right: Venus continuum-subtracted cube using all antenna baselines (15-314m) and subtracting only a 1st-order image-plane fit; using only baselines of 33-314m and with a 1st-order image-plane fit; using only baselines of 33-314m and with a 6th-order image-plane fit." (Figure 1 caption)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA data processing scripts (excluding short baselines <33m and applying image-plane polynomial fits)  
  > "Going beyond the JAO-released re-processing, Greaves et al. (2021a) excluded short antenna-baselines, and applied low-order image-plane fits." (2.1 ALMA); "The spectra presented here use the processing scripts first published in Greaves et al. (2021a), but here we have recovered phosphine over a larger planetary area." (2.1 ALMA) [from Greaves et al. (2021a)]
- Simplified radiative-transfer code and temperature-pressure/altitude/diffusion profiles  
  > "Here we model SO 2 spectra using the simplified radiative-transfer code of Greaves et al. (2021a) — the implementation is described here in Appendix A, where a link is provided to the code." (3 MODELLING); "The model uses the temperature-pressure profile of the Venus International Reference Atmosphere (VIRA), with details of the altitude and diffusion profiles listed in Greaves et al. (2020)." (3 MODELLING) [from Greaves et al. (2020); Greaves et al. (2021a)]

### Not stated but needed to reproduce (our reading)

- CASA version and specific imaging parameters (e.g., tclean weighting, robust parameter, masking, deconvolver) used in the Greaves et al. (2021a) scripts
- Exact synthesized beam dimensions for the ALMA cubes
- Exact height increment (Delta z) used in the 1D radiative transfer integration

## Analysis recipe

1. **Re-process ALMA datacubes and extract PH3 and SO2 spectra**: Exclude baselines <33m, subtract image-plane polynomial fits (6th-order for narrowband PH3, 3rd-order for wideband SO2), extract spectra from a 97x37 pixel box (49% of disc), divide by similarly-processed continuum signal from the same area, and for wideband SO2 subtract a template line-free spectrum shifted by +145 km/s to suppress quasi-periodic ripple.  
  > "The second additional procedure involved subtracting image-plane fits, which were of 6 th -order for the narrowband data including PH 3 1-0, and of 3 rd -order for the simultaneous wideband data covering a strong SO 2 transition." (2.1 ALMA); "Line:continuum ratios are finally obtained via a similarly-processed continuum signal extracted from the same area." (2.1 ALMA); "A “template” line-free section of spectral baseline was identified around -145 km/s, which has similar structure to the line region, and so can be shifted in velocity" (2.1 ALMA)
   - parameter: baselines 33-314m; box size 97x37 pixels (0.16 arcsec/pixel, covering 49% of disc, latitudes <= 40 deg); 6th-order fit (narrowband) and 3rd-order fit (wideband); template shift +145 km/s  
  > "using only baselines of 33-314m and with a 6th-order image-plane fit." (Figure 1 caption); "The new extracted spectrum is from a planet-spanning RA,Dec “box”, of 97x37 pixels where 1 pixel = 0.16 arcseconds." (4.1 ALMA 2019 data); "The dotted red histogram is a "template" line-free section of the same spectrum, after an applied shift of +145 km/s." (Figure 2 caption)
   - assumption: Line and continuum sources are similarly spatially distributed; 22% of continuum survives spatial filtering  
  > "This overcomes the difficulties in appropriately calibrating models of Venus, but involves the assumption that line and continuum sources are similarly spatially distributed, as discussed below." (2.1 ALMA); "This effect was modelled by Akins et al. (2021), while Greaves et al. (2021a) calculated from the data that 22% of the continuum survives the spatial filtering." (5.2 Abundances)
   - fitting: Image-plane polynomial fits (6th-order and 3rd-order); line integration over +/-6 km/s for PH3 detection confidence  
  > "This spectrum has 7.7 sigma confidence when line-integrated over ±6 km/s." (4.1 ALMA 2019 data)
   - validation: Tested extractions for PH3 in latitude bands extending to 20, 30, 40, or 50 degrees from the equator, finding fitted PH3 line-depths varied by only ~+/-10% (at the noise level).  
  > "Test-extractions were made for PH 3 for bands of latitude (instead of Declination) that extended to 20, 30, 40 or 50 degrees from the equator. The fitted PH 3 line-depths varied by only ∼±10%, at the level of noise." (4.1 ALMA 2019 data)
2. **Reduce archival JCMT HARP SO2 spectra**: Download raw archival spectra from HARP, create one-(x,y)-pixel datacubes with makecube in SMURF, manually correct for Venus-Earth velocity-differences in SPLAT, and subtract a 4th-order polynomial trendline fitted outside the line region.  
  > "These raw archival spectra from HARP (0.98 MHz spectral resolution) were downloaded, and one-(x,y)-pixel datacubes were created with the ‘makecube’ task in SMURF 2 ,with output spectra viewed and manually corrected for Venus-Earth velocity-differences (>10 km/s) within SPLAT 3 ." (2.2 JCMT); "There is some spectral ripple present, for which a suitable least-parameters approximation is a 4 th -order polynomial." (4.2 JCMT 2017 data)
   - software: SMURF, SPLAT
   - parameter: 0.98 MHz spectral resolution; 14 arcsec beam; 4th-order polynomial baseline  
  > "These raw archival spectra from HARP (0.98 MHz spectral resolution) were downloaded" (2.2 JCMT); "HARP observed at 346.6 GHz with a telescope beam of ≈14 arcsec, while Venus’ diameter on 6 June 2017 was 23 arcsec." (2.2 JCMT); "The dashed trendline is a 4th-order polynomial fitted outside the line region." (Figure 4 caption)
   - assumption: Planet-centre spectrum represents net planetary SO2  
  > "The planet-centre spectrum (with the best S/N) is thus adopted as representing net planetary SO 2 ." (2.2 JCMT)
   - fitting: 4th-order polynomial fitted outside the line region  
  > "The dashed trendline is a 4th-order polynomial fitted outside the line region." (Figure 4 caption)
   - validation: Tested co-adding 30 arcsec-offset receptor spectra with the planet-centre spectrum with weights up to 50%, finding only up to ~10% changes in net SO2 line-depth.  
  > "We tested co-adding these offset line:continuum spectra with the planet-centre spectrum, with various offset-weights up to 50%, and found only up to ∼10% changes in net SO 2 line-depth." (2.2 JCMT)
3. **Model SO2 line profiles and quantify SO2 contamination of PH3 1-0 spectra**: Calculate 1D semi-analytical pencil-beam radiative transfer models of SO2 transitions from z = 0 to 115 km with temperature-scaled HITRAN line strengths, subtract quadratic baselines from models to match data processing, compare to observed ALMA SO2 13(3,11)-13(2,12) and JCMT SO2 19(1,19)-18(0,18) spectra to constrain SO2 abundance, and predict contaminating SO2 30(9,21)-31(8,24) absorption at the PH3 1-0 frequency.  
  > "Here we model SO 2 spectra using the simplified radiative-transfer code of Greaves et al. (2021a) — the implementation is described here in Appendix A, where a link is provided to the code." (3 MODELLING); "We then ran the same model for the SO 2 30(9,21)–3(18,24) transition. Comparing this model to the PH 3 1-0 observation, the SO 2 contamination is <2%, when integrated over ±10 km/s (Figure 3b)." (4.1 ALMA 2019 data); "We then generated models for the contaminating transition SO 2 30(9,21)–31(8,24) using these two abundance profiles. Quadratic baseline-fits were subtracted from these models, over the same ±8 km/s region as for the data." (4.2 JCMT 2017 data)
   - software: Python3, J13.py
   - parameter: z = 0 to 115 km; pressure-broadening coefficient gamma = 0.18 cm^-1/atm; T0 = 300 K; 1.1 mm continuum altitude = 56 km (60 km at 346.6 GHz); ALMA upper limit model: 3 ppb SO2 at >= 80 km (quadratic subtracted outside +/-10 km/s); JCMT models: 20 ppb at >= 75 km and 25 ppb at >= 80 km (quadratic subtracted over +/-8 km/s)  
  > "We adopt as pressure-broadening coefficient the mean-estimate of 0.18 cm −1 /atm from Lincowski et al. (2021)." (3 MODELLING); "The grey curve is an upper-limit model, for 3 ppb of SO 2 at all altitudes ≥80 km, after removal of a quadratic baseline fitted outside ±10 km/s, to simulate the processing of the real data." (Figure 3 caption); "The former model is for 20 ppb of SO 2 at ≥75 km and the latter for 25 ppb at ≥80 km." (4.2 JCMT 2017 data)
   - assumption: Local thermodynamic equilibrium (LTE); constant representative SO2 abundance above a minimum altitude (or Case D profile for comparison); VIRA temperature-pressure profile; neglect scattering, beam convolution, and limb darkening  
  > "We have neglected convolution with the telescope beam, as these effects should be similar for line and continuum." (3 MODELLING); "only, as they are set to be constant over the atmospheric column where absorption arises." (3 MODELLING); "We assume that the atmospheric gas at each height is in local thermodynamic equilibrium and therefore the population of the lower level is proportional to 𝑒 −𝐸 𝐽 /𝑇 ." (APPENDIX A: LINE PROFILE MODEL)
   - fitting: Reduced chi-squared evaluation over +/-20 km/s in velocity for the two representative JCMT models (reduced chi-squared = 1.8 and 1.65)  
  > "These fits have reduced-𝜒 2 of 1.8 and 1.65 respectively, over ±20 km/s in velocity – they are representative only (i.e. use constant abundance), but within these limitations the fits match the observed line adequately, and net-abundance and minimum-altitude are quite tightly constrained." (4.2 JCMT 2017 data)
   - validation: Verified against detailed radiative transfer codes (Lincowski et al. 2021; Greaves et al. 2020), finding simple code generates SO2 lines 15-25% less deep and a 30(9,21)-31(8,24)/13(3,11)-13(2,12) ratio of 1:31 vs 1:40(+/-2) (slightly over-estimating contamination); tested varying minimum continuum altitude by 2-3 km, finding high-J line depth varies by only +/-5%.  
  > "Verification tests (against Lincowski et al. 2021, Figure 2 and Greaves et al. 2020, Figure 4) found that our simple code generates SO 2 lines that are 15-25% less deep than from more detailed models (see discussion in Appendix A)." (3 MODELLING); "The line-depth of this high-J SO 2 transition was found to be uncertain by only ±5% by this method." (3 MODELLING); "Detailed codes (Greaves et al. 2020, Lincowski et al. 2021) have given line-depth ratios for this pair of 1:40(±2), while the simplified code gives 1:31." (3 MODELLING)

## Software

- **SMURF** : Creating one-(x,y)-pixel datacubes from raw archival JCMT HARP spectra using the 'makecube' task  
  > "These raw archival spectra from HARP (0.98 MHz spectral resolution) were downloaded, and one-(x,y)-pixel datacubes were created with the ‘makecube’ task in SMURF 2" (2.2 JCMT)
- **SPLAT** : Viewing output JCMT spectra and manually correcting for Venus-Earth velocity differences  
  > "with output spectra viewed and manually corrected for Venus-Earth velocity-differences (>10 km/s) within SPLAT 3 ." (2.2 JCMT)
- **Python3** 3: Writing and running the 1D semi-analytical line profile radiative transfer model (J13.py)  
  > "This program calculates a single line profile and is written in Python3. Example code to model the SO 2 13(3,11)-13(2,12) transition can be found at http://www.mrao.cam.ac.uk/ pbr27/J13.py." (APPENDIX A: LINE PROFILE MODEL)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| SO2 contamination of ALMA 2019 PH3 1-0 spectrum | <2 | not stated | % | 3 | We also present ALMA 2019 spectra of PH 3 1-0 and an SO 2 transition acquired simultaneously, and infer that SO 2 line-contamination was ≲2% (for the least-noisy half of the planetary disc).; Comparing this model to the PH 3 1-0 observation, the SO 2 contamination is <2%, when integrated over ±10 km/s (Figure 3b). |
| SO2 contamination of JCMT 2017 PH3 1-0 spectrum | 9-11 | not stated | % | 3 | We retrieve a sulphur dioxide observation from the JCMT archive that was simultaneous within a few days of the PH 3 1-0 spectrum obtained in June 2017, and demonstrate via a radiative transfer calculation that contamination of PH 3 by SO 2 was ≈10%.; The model signal, over ±8 km/s, is only 9-11% of the total absorption seen in the PH 3 1-0 observation. |
| ALMA 2019 PH3 1-0 detection significance (integrated over +/-6 km/s) | 7.7 | not stated | sigma | 1 | This spectrum has 7.7 sigma confidence when line-integrated over ±6 km/s. |
| ALMA 2019 PH3 1-0 line centroid velocity | -0.2 | 0.5 | km/s | 1 | The line-centroid is at -0.2 ± 0.5 km/s in the Venus-centric PH 3 1-0 reference-frame, fully in agreement with zero as expected if the absorption is dominated by phosphine. |
| ALMA 2019 mesospheric SO2 abundance upper limit (at altitudes >= 80 km) | 3 | not stated | ppb | 3 | The overlaid grey curve employs 3 ppb of SO 2 at altitudes ≥80 km, to demonstrate that mesospheric sulphur dioxide at greater abundances would likely have been detected (at ≥3-sigma at line-minimum).; Our ≲3 ppb ALMA SO 2 upper-limit from March 2019 lies in the lowest decile of their abundance table, but with correction for spatial-filtering the limit could be higher. |
| JCMT 2017 SO2 19(1,19)-18(0,18) line-to-continuum ratio at line minimum (26, 17, and 6 days before PH3 midpoint) | -0.0043, -0.0029, -0.0044 | not stated | dimensionless | 2 | The SO 2 line-continuum ratios were found to be similar, at -0.0043, -0.0029 and -0.0044 at line-minimum respectively, suggesting an SO 2 abundance variation of ∼±20% about the mean. |
| JCMT 2017 representative SO2 abundance | 20-25 | not stated | ppb | 3 | The former model is for 20 ppb of SO 2 at ≥75 km and the latter for 25 ppb at ≥80 km.; Our 20-25 ppb of SO 2 from JCMT in June 2017 is near the mean, ≈23 ppb, in the Sandor et al. tabulation. |
| JCMT 2017 PH3 1-0 detection significance (before and after removing 10% SO2 contamination) | 6.7 (6.0 after removing contamination) | not stated | sigma | 3 | The PH 3 1-0 detection shown has 6.7-sigma confidence when integrated over ±8 km/s.; The JCMT spectrum has 6.7 sigma confidence, so is at ≈6.0 sigma after removing 10% contamination. |
| Contamination-subtracted PH3 1-0 line-to-continuum minimum (ALMA 2019) | -1.7e-4 | not stated | dimensionless | 1 | After subtracting contamination and adopting uniform ≈3.5 km/s spectral binning, the line-minimum for JCMT is -2.1e-4 and for ALMA it is -1.7e-4, i.e. a variation of ∼10% around the mean. |
| Contamination-subtracted PH3 1-0 line-to-continuum minimum (JCMT 2017) | -2.1e-4 | not stated | dimensionless | 3 | After subtracting contamination and adopting uniform ≈3.5 km/s spectral binning, the line-minimum for JCMT is -2.1e-4 and for ALMA it is -1.7e-4, i.e. a variation of ∼10% around the mean. |
| Span of contamination-subtracted PH3 1-0 line-to-continuum absorption depth across epochs | -1.9e-4 | 0.2e-4 | dimensionless | 3 | The two values span -1.9(±0.2) 10 −4 of the continuum signal (which was re-estimated for ALMA), albeit for differing planetary areas. |

## Qualitative findings

- The 1.1 mm absorption features attributed to PH3 1-0 in Venus' atmosphere cannot be explained by SO2 30(9,21)-31(8,24) contamination, which contributes <2% in the 2019 ALMA data and ~10% in the 2017 JCMT data.  
  > "Figures 3 and 4 show that the absorptions proposed as PH 3 1-0 can not realistically be re-attributed to sulphur dioxide. Contamination of the observed spectra by the high-J SO 2 transition is inferred to be ≲10%, at both epochs." (5.1 Contamination)
- Ad-hoc historical SO2 models (such as Case D of Lincowski et al. 2021) over-predict the nearly contemporaneous June 2017 JCMT SO2 19(1,19)-18(0,18) absorption depth by a factor of ~10.  
  > "Figure 5 demonstrates that this ad-hoc model – based on various historical SO 2 data – will produce ≈10× deeper absorption than was actually seen at JCMT." (5.2 Abundances)
- Contamination-subtracted PH3 1-0 absorption depths relative to the observed continuum were broadly comparable between the June 2017 JCMT and March 2019 ALMA epochs.  
  > "The contamination-subtracted ALMA and JCMT spectra (of 6-8 sigma confidence) are now consistent with similar absorption-depths at the two epochs." (abstract); "Modulo this uncertainty, ALMA and JCMT both sampled large areas of Venus (Table 1), and so the similar spectra hint that phosphine-attributed abundances were broadly comparable in 2017 and 2019." (5.2 Abundances)

## Claim tuples

- H: The 1.1 mm absorption feature at 266.946 GHz attributed to PH3 1-0 in ALMA 2019 observations could be due to SO2 30(9,21)-31(8,24) absorption instead of PH3. | E: Extracted simultaneous ALMA 2019 spectra of PH3 1-0 and SO2 13(3,11)-13(2,12) over a 97x37-pixel box (49% of Venus' disc) after excluding <33m baselines and applying image-plane fits, and modelled both SO2 transitions using a 1D radiative transfer code. | R: PH3 1-0 is detected at 7.7 sigma with line-centroid at -0.2 +/- 0.5 km/s (3-sigma discrepant with SO2 at +1.3 km/s), while non-detection of SO2 13(3,11)-13(2,12) limits mesospheric SO2 to <=3 ppb and SO2 30(9,21)-31(8,24) contamination to <2%. | F: SO2 contamination of the ALMA 2019 PH3 1-0 spectrum is negligible (<2%) and cannot explain the observed absorption feature. | **refuted**
- H: The June 2017 JCMT 266.946 GHz absorption feature attributed to PH3 1-0 was caused by high mesospheric SO2 abundances (e.g., Case D model of Lincowski et al. 2021). | E: Retrieved archival JCMT HARP SO2 19(1,19)-18(0,18) spectra observed on 6 June 2017 (3 days before PH3 observations), fitted 1D radiative transfer models to constrain SO2 abundance, and predicted the SO2 30(9,21)-31(8,24) contribution and the Lincowski et al. Case D prediction. | R: Observed JCMT SO2 19(1,19)-18(0,18) is matched by 20-25 ppb of SO2, predicting only 9-11% SO2 contamination of the PH3 1-0 feature (leaving a ~6.0 sigma PH3 signal), whereas the Case D model produces ~10x deeper SO2 19(1,19)-18(0,18) absorption than observed. | F: Ad-hoc high-SO2 models greatly over-estimate the SO2 present in June 2017; SO2 contamination of the JCMT PH3 1-0 spectrum was ~10%. | **refuted**
- H: Spatial filtering in ALMA interferometric processing could suppress SO2 13(3,11)-13(2,12) while leaving significant SO2 30(9,21)-31(8,24) absorption at the PH3 1-0 frequency. | E: Compared the frequencies, absorbing columns, and atmospheric temperature/spatial distributions of the J=13 and J=31 SO2 transitions. | R: Both line frequencies differ by <1% and arise from the same gas column; enhancing J=31 relative to J=13 would require warm cloud-deck SO2 to be much patchier than mesospheric SO2, contradicting observations of Hadley-cell circulation and super-rotation smearing at lower altitudes. | F: Spatial filtering affects both SO2 transitions similarly and cannot enhance the contaminant J=31 line relative to the J=13 line. | **refuted**
- H: The PH3-attributed absorption depths in Venus' atmosphere were consistent between June 2017 (JCMT) and March 2019 (ALMA). | E: Subtracted estimated SO2 contamination, adopted uniform ~3.5 km/s spectral binning, and normalized the ALMA line by the observed spatially-filtered continuum from the same region. | R: The line-to-continuum minimum is -2.1e-4 for JCMT 2017 and -1.7e-4 for ALMA 2019, spanning -1.9(+/-0.2) x 10^-4 (~10% variation around the mean). | F: Contamination-subtracted spectra are consistent with similar absorption depths and broadly comparable phosphine-attributed abundances in 2017 and 2019, modulo spatial filtering uncertainties. | **supported**

## Reasoning

- Why this data: ALMA 2019 wideband data serendipitously covered SO2 transitions simultaneously with narrowband PH3 1-0, and archival JCMT HARP SO2 observations from 6 June 2017 were taken only 3 days before the 9-16 June 2017 JCMT PH3 run.  
  > "The ALMA wideband data were useful as they serendipitously covered several transitions of SO 2, with none of these frequencies covered in the narrow-band mode." (2.1 ALMA); "The JCMT’s HARP camera-spectrometer monitored Venus from March to June 2017 (most relevant dates listed in Table 1), with the 6 June 2017 data acquired very shortly before our PH 3 observations on 9-16 June 2017." (2.2 JCMT)
- Why this method: Excluding short baselines (<33m) reduces spectral ripple and noise by ~2.5x; subtracting image-plane polynomial fits flattens baselines without user-biased spectral trendlines; extracting over a symmetric planet-spanning box cancels anti-symmetric phase errors; using a 1D pencil-beam code provides transparent, reproducible line-ratio bounds.  
  > "The first procedure removes at an early stage the data that contribute the most spectral "ripple" and noise – Greaves et al. (2021a) demonstrated that including the shorter antenna-baselines increases the noise by a factor ≈2.5." (2.1 ALMA); "This procedure removes the need for any trendlines (which could be user-biased) to be fitted to spectra extracted from the final datacubes." (2.1 ALMA); "The aim here is for the results from simple pencil-beam calculations to be reproducible and to use transparent methods." (3 MODELLING)
- Alternative: Attributing the 266.946 GHz absorption entirely to SO2 30(9,21)-31(8,24) (rejected due to 3-sigma velocity discrepancy in ALMA data and non-detection/low abundance of stronger SO2 transitions in ALMA and JCMT data)  
  > "is however 3-sigma discrepant with the alternative attribution (Lincowski et al. 2021, e.g.) to SO 2 30(9,21)–3(18,24) absorption, which would be centred in this frame at +1.3 km/s." (4.1 ALMA 2019 data); "We conclude that results from observations preclude re-attributing phosphine on Venus to sulphur dioxide." (6 CONCLUSIONS)
- Alternative: Two-layer atmosphere with patchy warm cloud-deck SO2 and smooth cold mesospheric SO2 to enhance J=31 relative to J=13 via spatial filtering (rejected as contrary to observations showing mesospheric SO2 and Hadley-cell/super-rotation smearing at lower altitudes)  
  > "The only pathological case that we can identify would involve weighting the SO 2 abundance-profile to the warmest gas-layer (where the J=31 level-population is higher), and making this layer particularly patchy (so J=31 spatial-filtering is reduced)." (5.1 Contamination); "A smoother SO 2 distribution at lower altitude is the opposite of what is needed for this enhanced-J=31 scenario to work." (5.1 Contamination)
- How they decided it was enough: _not stated_
- Limitation (authors): Excluding short ALMA baselines (<33m) filters out spatial scales larger than 4.3-7.1 arcsec, heavily downweighting the centre of Venus (15.2 arcsec diameter) so that only ~22% of continuum survives and true ALMA line-depths and abundances remain uncertain.  
  > "Hence, as Venus then subtended 15.2 arcsec, most of the centre of the planet is heavily downweighted, with most of the line signal coming from an annulus inwards of the limb." (2.1 ALMA); "The true ALMA line-depth is uncertain due to the unknown effects of spatial filtering; in particular, the absorption could be significantly less deep with a Venus-model continuum rather than the observed filtered continuum." (5.2 Abundances)
- Limitation (authors): Cloud-level PH3 abundance and altitude profiles cannot be quantified because broad pressure-broadened line wings are heavily suppressed by the polynomial baseline subtraction and lack laboratory PH3-CO2 broadening coefficients.  
  > "Addressing (3) will require new observations and better laboratory data, as inversion of line-shapes to altitude-profiles of abundance needs lower-noise spectra and a PH 3 -CO 2 broadening-coefficient that improves on current theoretical estimates." (1 INTRODUCTION); "However, the cloud-level PH 3 contribution is unquantified here, given that line-wings are heavily suppressed in necessary processing." (5.2 Abundances)
- Limitation (authors): The 1D radiative transfer model neglects scattering, beam convolution, and limb darkening, generating SO2 lines 15-25% less deep than detailed 3D/scattering radiative transfer codes.  
  > "Verification tests (against Lincowski et al. 2021, Figure 2 and Greaves et al. 2020, Figure 4) found that our simple code generates SO 2 lines that are 15-25% less deep than from more detailed models (see discussion in Appendix A)." (3 MODELLING); "This one-dimensional model accounts for absorption and thermal emission, but does not treat scattering." (APPENDIX A: LINE PROFILE MODEL)
- Limitation (authors): JCMT SO2 and PH3 observations in June 2017 were not strictly simultaneous, being separated by 3 days between the last SO2 spectrum and the start of PH3 observing.  
  > "Given the rather constant SO 2 that JCMT observed in May-June 2017, it seems unlikely that the planet-wide abundance soared by an order of magnitude in the three days between the last SO 2 spectrum and the start of PH 3 observing." (4.2 JCMT 2017 data)
- Caveat (inferred, ours): Subtracting a 6th-order image-plane polynomial and a shifted off-line template section (+145 km/s) to cancel quasi-periodic wideband spectral ripples is an empirical procedure that could distort or suppress real spectral features or create residual baseline artefacts.
- Caveat (inferred, ours): Normalizing the spatially filtered ALMA line cube by the spatially filtered continuum cube assumes identical spatial distributions for the continuum and trace gas, which may not hold if PH3 or SO2 is latitudinally or diurnally inhomogeneous.

## Reproducibility

- Data public (paper): Raw and processed data are publicly available in the open-access JCMT and ALMA archives  
  > "Raw and processed data are available in the open-access JCMT and ALMA archives, at https://www.cadc-ccda.hia-iha.nrc-cnrc.gc.ca/en/jcmt/ and https://almascience.eso.org/alma-data (and other ALMA repositories)." (DATA AVAILABILITY)
- Products in archive: Processed spectra files to be made available at zenodo.org; ALMA processing scripts published in Greaves et al. (2021a)  
  > "The scripts to reproduce the ALMA results shown here were published in Greaves et al. (2021a). Files of the processed spectra shown here will be made available at zenodo.org." (DATA AVAILABILITY)
- Code: Python3 radiative transfer script (J13.py) publicly available at http://www.mrao.cam.ac.uk/~pbr27/J13.py; ALMA reduction scripts published in Greaves et al. (2021a)  
  > "The scripts to reproduce the ALMA results shown here were published in Greaves et al. (2021a)." (DATA AVAILABILITY); "Example code to model the SO 2 13(3,11)-13(2,12) transition can be found at http://www.mrao.cam.ac.uk/ pbr27/J13.py." (APPENDIX A: LINE PROFILE MODEL)
- Missing: Exact pixel coordinates (centre RA/Dec or Venus-centric coordinates) of the 97x37 pixel extraction box in the ALMA datacube
- Missing: Exact velocity range and width of the -145 km/s template region used for ripple subtraction in the ALMA wideband SO2 spectrum
- Missing: Specific Zenodo DOI/record URL for the processed spectra
- Data volume (inferred): tens of GB (single 3.5-hour ALMA Band 6 execution block plus archival JCMT HARP single-dish spectra)
- Score (inferred): 8/5, Raw and re-calibrated ALMA and JCMT data are public, the 1D radiative transfer code is linked directly (with equations fully specified in Appendix A), and the ALMA reduction scripts are available in Greaves et al. (2021a); only minor box-placement and template-window specifics would need to be inferred or retrieved from the companion scripts.
- Rediscovery candidate: yes, Public archival ALMA and JCMT data, released radiative transfer Python code and reduction scripts, and clear numeric answer keys (line depths, detection significances, centroid velocities, and percentage SO2 contamination).

## Links

- Method: Greaves et al. (2021a) (Published the ALMA data re-processing scripts (baseline cut <33m, image-plane polynomial fitting) and initial simplified radiative-transfer code used in this work)
- Companion: Greaves et al. (2020) (Discovery paper presenting the 2017 JCMT and 2019 ALMA 1.1 mm PH3 1-0 observations of Venus)
- Companion: Greaves et al. (2021a) (Response paper presenting the re-calibrated ALMA Venus data processing and simplified radiative transfer model)
- Companion: Greaves et al. (2021b) (Companion response addressing statistical critiques of the Venus PH3 detections)
- Related: JCMT S16BP007
- Related: JCMT M17AP081

## Checks

```json
{
 "quotes": 122,
 "quotes_ok": 122,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 7,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2019.A.00023.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 79,
  "stated": 52,
  "rate": 0.658
 },
 "evidence_ok": true
}
```
