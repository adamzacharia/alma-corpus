# Panchromatic (Sub)millimeter polarization observations of HL Tau unveil aligned scattering grains

`2024MNRAS.528..843L` | Monthly Notices of the Royal Astronomical Society 2024 | first author: Lin, Zhe-Yu Daniel | arXiv: 2309.10055 | DOI: 10.1093/mnras/stae040

Card schema 1.0 | model gpt-6.1-sol | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: Does the polarization transition extend to other wavelengths and agree with optical depth effects of toroidally aligned prolate grains?  
  > "To further test if toroidally aligned prolate grains with varying optical depth can explain the polarization transition, we need additional resolved polarization observations at different wavelengths." (Introduction)
- Target **HL Tau**: coordinates Band 7 fitted center, ICRS: R.A. 04:31:38.430; Dec +18:13:57.14  
  > "| 7 | 04:31:38.430 | +18:13:57.14 | 887.91 $\pm$ 0.57 | 606.3 $\pm$ 0.4 | 137.21 $\pm$ 0.07 |" (Individual Polarization Quantities); "Additionally, the Very Long Baseline Array yielded a distance of $147.3 \pm 0.5$ pc (cite: Galli2018ApJ...859...33G)." (Introduction); "We adopt a distance of 147.3 pc for HL Tau for consistency with the recent high angular resolution study (cite: CarrascoGonzalez2019ApJ...883...71C)." (Introduction); z/distance 147.3 pc  
  > "| 7 | 04:31:38.430 | +18:13:57.14 | 887.91 $\pm$ 0.57 | 606.3 $\pm$ 0.4 | 137.21 $\pm$ 0.07 |" (Individual Polarization Quantities); "Additionally, the Very Long Baseline Array yielded a distance of $147.3 \pm 0.5$ pc (cite: Galli2018ApJ...859...33G)." (Introduction); "We adopt a distance of 147.3 pc for HL Tau for consistency with the recent high angular resolution study (cite: CarrascoGonzalez2019ApJ...883...71C)." (Introduction); distance from VLBA (cite: Galli2018ApJ...859...33G); adopted for consistency with (cite: CarrascoGonzalez2019ApJ...883...71C)  
  > "| 7 | 04:31:38.430 | +18:13:57.14 | 887.91 $\pm$ 0.57 | 606.3 $\pm$ 0.4 | 137.21 $\pm$ 0.07 |" (Individual Polarization Quantities); "Additionally, the Very Long Baseline Array yielded a distance of $147.3 \pm 0.5$ pc (cite: Galli2018ApJ...859...33G)." (Introduction); "We adopt a distance of 147.3 pc for HL Tau for consistency with the recent high angular resolution study (cite: CarrascoGonzalez2019ApJ...883...71C)." (Introduction)

## Data provenance

- ALMA projects: 2016.1.00115.S, 2016.1.00162.S, 2019.1.00134.S, 2019.1.01051.S, 2019.1.00162.S
- bands: ALMA Bands 3 (3.09 mm), 4 (2.07 mm), 5 (1.48 mm), 6 (1.29 mm), 7 (0.87 mm)  
  > "To date, HL Tau has been observed by ALMA at Bands 3 (3.09 mm), 4 (2.07 mm), 5 (1.48 mm), 6 (1.29 mm), and 7 (0.87 mm)" (Observations)
- frequencies and spectral setup: Each band dataset: four 2 GHz spectral windows with 64 channels  
  > "Every dataset of each band consists of four 2 GHz spectral windows with 64 channels." (ALMA Observations)
- continuum bandwidth: Approximately 7.5 GHz per dataset before removal of prominent molecular lines  
  > "The total effective bandwidth of each dataset is approximately 7.5 GHz." (ALMA Observations); "However, we identified some prominent molecular lines that we removed when making the continuum images." (ALMA Observations)
- arrays: _not stated_
- configurations: Band 3: C40-6; Band 4: C43-6/7; Band 5: C43-6 and C43-6/7; Band 6: C40-5; Band 7: C43-6  
  > "C40-6 | 41 | 19-3144 | J0510+1800 | J0423-0120 | J0431+1731 | J0510+1800 | 2016.1.00115.S |  |
| 4 | 2 | 2021 Jul 7 | 1.2 | C43-6/7" (Table 1); "C43-6 | 41 | 16-2517 | J0238+1636 | J0238+1636 | J0431+1731 | J0423-0120 | 2019.1.00134.S |  |
|  | 1 | 2021 Jul 6 | 0.5 | C43-6/7" (Table 1); "C40-5 | 42 | 17-2647 | J0510 +1800 | J0510+1800 | J0431+1731 | J0522–3627 | 2016.1.00162.S |  |
| 7 | 2 | 2021 Jun 30 | 1.2 | C43-6" (Table 1)
- baselines: Band 3: 19-3144 m; Band 4: 41-3396 m; Band 5: 16-2517 m and 41-3638 m; Band 6: 17-2647 m; Band 7: 15-2114 m  
  > "19-3144 | J0510+1800 | J0423-0120 | J0431+1731 | J0510+1800 | 2016.1.00115.S |  |
| 4 | 2 | 2021 Jul 7 | 1.2 | C43-6/7 | 38 | 41-3396" (Table 1); "16-2517 | J0238+1636 | J0238+1636 | J0431+1731 | J0423-0120 | 2019.1.00134.S |  |
|  | 1 | 2021 Jul 6 | 0.5 | C43-6/7 | 41 | 41-3638" (Table 1); "17-2647 | J0510 +1800 | J0510+1800 | J0431+1731 | J0522–3627 | 2016.1.00162.S |  |
| 7 | 2 | 2021 Jun 30 | 1.2 | C43-6 | 41 | 15-2114" (Table 1)
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: Band 3: 2.3 hours; Band 4: 1.2 hours; Band 5: 1.1 and 0.5 hours; Band 6: 1.1 hours; Band 7: 1.2 hours  
  > "2.3 | C40-6 | 41 | 19-3144 | J0510+1800 | J0423-0120 | J0431+1731 | J0510+1800 | 2016.1.00115.S |  |
| 4 | 2 | 2021 Jul 7 | 1.2" (Table 1); "1.1 | C43-6 | 41 | 16-2517 | J0238+1636 | J0238+1636 | J0431+1731 | J0423-0120 | 2019.1.00134.S |  |
|  | 1 | 2021 Jul 6 | 0.5" (Table 1); "1.1 | C40-5 | 42 | 17-2647 | J0510 +1800 | J0510+1800 | J0431+1731 | J0522–3627 | 2016.1.00162.S |  |
| 7 | 2 | 2021 Jun 30 | 1.2" (Table 1)
- observing dates: Band 3: 2016 Oct 12; Band 4: 2021 Jul 7; Band 5: 2021 Jun 14 and Jul 6; Band 6: 2017 Jul 12; Band 7: 2021 Jun 30  
  > "2016 Oct 12 | 2.3 | C40-6 | 41 | 19-3144 | J0510+1800 | J0423-0120 | J0431+1731 | J0510+1800 | 2016.1.00115.S |  |
| 4 | 2 | 2021 Jul 7" (Table 1); "2021 Jun 14 | 1.1 | C43-6 | 41 | 16-2517 | J0238+1636 | J0238+1636 | J0431+1731 | J0423-0120 | 2019.1.00134.S |  |
|  | 1 | 2021 Jul 6" (Table 1); "2017 Jul 12 | 1.1 | C40-5 | 42 | 17-2647 | J0510 +1800 | J0510+1800 | J0431+1731 | J0522–3627 | 2016.1.00162.S |  |
| 7 | 2 | 2021 Jun 30" (Table 1)
- pi or archival as stated: Bands 3 and 6: previously presented data, reimaged after self-calibration; Band 7: deeper, higher-resolution data from Stephens et al., (in press)  
  > "data were first presented in (cite: Kataoka2017ApJ...844L...5K) and (cite: Stephens2017), respectively, but we reimaged the measurement sets after self-calibration." (Observations); "we used deeper and higher resolution data from Stephens et al., (in press)" (Observations)
- Other facility **Karl G. Jansky Very Large Array (VLA)**: Q-band (6.97 mm) full-polarization data; B configuration; 17.5 hours on target after alignment and concatenation; project 19A-388  
  > "by the VLA at Q-band (6.97 mm)." (Observations); "We observed HL Tau with the VLA in its B configuration during three semesters (Legacy project code: 19A-388)." (VLA Q-band Observations); "The final, aligned, and concatenated dataset contains 17.5 hours on target." (VLA Q-band Observations)
- Other facility **ALMA Helpdesk**: Calibrated Band 6 dataset  
  > "The calibrated Band 6 dataset was provided by the ALMA Helpdesk staff." (ALMA Observations)
- External data: Previously presented Band 3 measurement sets  
  > "data were first presented in (cite: Kataoka2017ApJ...844L...5K) and (cite: Stephens2017), respectively, but we reimaged the measurement sets after self-calibration." (Observations) [from (cite: Kataoka2017ApJ...844L...5K)]
- External data: Previously presented Band 6 measurement sets  
  > "data were first presented in (cite: Kataoka2017ApJ...844L...5K) and (cite: Stephens2017), respectively, but we reimaged the measurement sets after self-calibration." (Observations) [from (cite: Stephens2017)]
- External data: Deeper, higher-resolution Band 7 data  
  > "we used deeper and higher resolution data from Stephens et al., (in press)" (Observations) [from Stephens et al., (in press)]
- External data: VLBA distance: 147.3 ± 0.5 pc  
  > "Additionally, the Very Long Baseline Array yielded a distance of $147.3 \pm 0.5$ pc (cite: Galli2018ApJ...859...33G)." (Introduction) [from (cite: Galli2018ApJ...859...33G)]
- External data: Distance convention adopted for consistency  
  > "We adopt a distance of 147.3 pc for HL Tau for consistency with the recent high angular resolution study (cite: CarrascoGonzalez2019ApJ...883...71C)." (Introduction) [from (cite: CarrascoGonzalez2019ApJ...883...71C)]
- External data: Disk major-axis position angle: 138.02°  
  > "The position angle of the disk major axis is $138.02^{\circ}$ based on high angular resolution images from (cite: ALMApartnership2015)." (Principal Frame View) [from (cite: ALMApartnership2015)]
- External data: Far side northeast, determined from blueshifted northeast and redshifted southwest outflow  
  > "The far side of the disk is to the northeast since the outflow direction is blueshifted to the northeast and redshifted to the southwest (cite: ALMApartnership2015; Yen2017A&A...608A.134Y)." (Principal Frame View) [from (cite: ALMApartnership2015; Yen2017A&A...608A.134Y)]
- External data: Geometrically thin dust layer, supporting local plane-parallel slabs  
  > "Since the dust layer responsible for the HL Tau (sub)millimeter continuum is geometrically thin (cite: Pinte2016ApJ...816...25P), one can approximate each local patch of the dust disk as a plane-parallel slab." (Methodology) [from (cite: Pinte2016ApJ...816...25P)]
- External data: 3C147 polarization angle 86° and polarization degree 5.2%  
  > "For the calibration of the polarization angle, we used the known polarization parameters for 3C147, i.e., a polarization angle of 86$^\circ$ and a polarization degree of 5.2% (Perley & Butler 2013)." (VLA Q-band Observations) [from Perley & Butler 2013]
- External data: At 100 au, optical depths ∼0.4 and 0.3 at Bands 3 (2.9 mm) and 6 (1.3 mm); modeling did not consider scattering  
  > "Multiwavelength continuum ray-tracing from (cite: Pinte2016ApJ...816...25P) showed that, at a radius of 100 au, the optical depths at Band 3 (2.9 mm) and 6 (1.3 mm) are $\sim 0.4$ and $0.3$, respectively," (Results); "though the modeling did not consider scattering." (Results) [from (cite: Pinte2016ApJ...816...25P)]
- External data: Including scattering, optical depths ∼1 and ∼3 at Bands 4 and 6 at 100 au  
  > "Nevertheless, including scattering, (cite: CarrascoGonzalez2019ApJ...883...71C) obtained optical depths of $\sim 1$ and $\sim 3$ at Bands 4 (2.1 mm) and 6 (1.3 mm), respectively, at the same radius." (Results) [from (cite: CarrascoGonzalez2019ApJ...883...71C)]
- External data: Gaps at 68 and 78 au; ring at 86 au used to compare with the thermal-polarization radial profile  
  > "The peak at $r\sim 70$ au appears to coincide with the two close and deepest gaps at $68$ and $78$ au (cite: ALMApartnership2015)." (Results); "The minimum at $r\sim 90$ au coincides with the ring at $86$ au." (Results) [from (cite: ALMApartnership2015)]
- External data: Free-free emission confined to central ∼40 mas; used to justify omitting free-free subtraction at detected Q-band vectors  
  > "we did not remove the free-free component as was done in (cite: CarrascoGonzalez2019ApJ...883...71C) because the free-free emission is only within the central $\sim 40$ mas" (Q-Band consistency with toroidally aligned grains) [from (cite: CarrascoGonzalez2019ApJ...883...71C)]
- External data: Q-band disk likely optically thin  
  > "Given that the disk is likely optically thin (cite: CarrascoGonzalez2016ApJ...821L..16C; CarrascoGonzalez2019ApJ...883...71C), we estimate that the intrinsic polarization of grains, $p_{0}$, should be comparable." (Q-Band consistency with toroidally aligned grains) [from (cite: CarrascoGonzalez2016ApJ...821L..16C; CarrascoGonzalez2019ApJ...883...71C)]
- External data: Previous intrinsic polarization estimate: 2% from ALMA wavelengths  
  > "the $2\%$ inferred from the ALMA wavelengths (cite: Lin2022)" (Q-Band consistency with toroidally aligned grains) [from (cite: Lin2022)]
- External data: Resolved ALMA and VLA modeling inferred ∼1 mm grains after accounting for scattering and optical depth  
  > "Even after accounting for scattering and optical depth effects, (cite: CarrascoGonzalez2019ApJ...883...71C) used resolved ALMA and VLA observations and inferred $\sim 1$ mm grains." (Grain structure) [from (cite: CarrascoGonzalez2019ApJ...883...71C)]
- External data: Porous-grain modeling simultaneously explained Stokes I and weak wavelength dependence of polarization; grains can exceed 1 mm depending on porosity  
  > "Indeed, (cite: Zhang2023ApJ...953...96Z) simultaneously modeled the Stokes $I$ and the weak $\lambda$ dependence of polarization assuming porous grains and found that the grains can be greater than 1 mm depending on the porosity." (Grain structure) [from (cite: Zhang2023ApJ...953...96Z)]
- External data: Near-far scattering-asymmetry models for an inclined, optically thick, vertically thick axisymmetric disk  
  > "Thus, we discuss if the near-far side asymmetry matches the expected asymmetry from dust scattering of an axisymmetric disk that is inclined, optically thick, and vertically thick (cite: Yang2017MNRAS.472..373Y; Lin2023MNRAS.520.1210L)." (What can produce the near-far side asymmetry?) [from (cite: Yang2017MNRAS.472..373Y; Lin2023MNRAS.520.1210L)]
- External data: Model q′ near-far difference ∼0.5%, depending on vertical thickness  
  > "the model predicted $\sim 0.5\%$ depending on the vertical thickness of the disk (cite: Lin2023MNRAS.520.1210L)." (What can produce the near-far side asymmetry?) [from (cite: Lin2023MNRAS.520.1210L)]
- Simulation/model as data: Polarized radiation-transfer calculations in simplified plane-parallel geometry underpin linear addition of scattering and thermal polarization  
  > "The technique relies on the approximation that scattering mainly produces a constant polarization due to inclination, thermal polarization produces the azimuthal variation, and both quantities add linearly based on polarized radiation transfer calculations in a simplified plane-parallel geometry." (Polarization Analysis)
- Simulation/model as data: Published scattering models used to interpret the near-far side asymmetry  
  > "Thus, we discuss if the near-far side asymmetry matches the expected asymmetry from dust scattering of an axisymmetric disk that is inclined, optically thick, and vertically thick (cite: Yang2017MNRAS.472..373Y; Lin2023MNRAS.520.1210L)." (What can produce the near-far side asymmetry?)

## Processing

### Calibration

- pipeline or manual: ALMA: calibration pipeline with ALMA-supplied scripts; calibrated Band 6 supplied by ALMA Helpdesk. VLA: modified NRAO Pipeline including polarization calibration after gain calibration  
  > "Prior to self-calibration, we re-ran the data through ALMA’s calibration pipeline using the ALMA-supplied calibration scripts." (ALMA Observations); "The calibrated Band 6 dataset was provided by the ALMA Helpdesk staff." (ALMA Observations); "For the calibration of the data we used CASA and a modified version of the NRAO Pipeline which includes polarization calibration after the usual gain calibration." (VLA Q-band Observations)
- casa version: 4.7.38335: Band 3 calibration; 6.2.1.7: Bands 4, 5, 7 calibration and all ALMA line removal, self-calibration, imaging  
  > "To run the calibration pipeline we used CASA version 4.7.38335 for Band 3, while for Bands 4, 5, and 7 we used version 6.2.1.7." (ALMA Observations); "Line removal, self-calibration, and imaging were performed using the CASA version 6.2.1.7 for all the bands." (ALMA Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: ALMA Band 3: J0423-0120; Band 4: J0510+1800; Band 5: J0238+1636 and J0510+1800; Bands 6, 7: J0510+1800. VLA: 3C147  
  > "J0423-0120 | J0431+1731 | J0510+1800 | 2016.1.00115.S |  |
| 4 | 2 | 2021 Jul 7 | 1.2 | C43-6/7 | 38 | 41-3396 | J0510+1800 | J0510+1800" (Table 1); "J0238+1636 | J0431+1731 | J0423-0120 | 2019.1.00134.S |  |
|  | 1 | 2021 Jul 6 | 0.5 | C43-6/7 | 41 | 41-3638 | J0510+1800 | J0510+1800" (Table 1); "J0510+1800 | J0431+1731 | J0522–3627 | 2016.1.00162.S |  |
| 7 | 2 | 2021 Jun 30 | 1.2 | C43-6 | 41 | 15-2114 | J0510+1800 | J0510+1800" (Table 1)
- flux scale uncertainty: 10% absolute calibration uncertainty for VLA and ALMA; ignored for the rest of the paper  
  > "We assume a 10$\%$ absolute calibration uncertainty based on the VLA and the ALMA technical handbooks, but we ignore it for the rest of the paper." (Construction of Polarization Images)
- self calibration: All five ALMA bands: three phase-only rounds with solution intervals infinity, 30.5 s, 10.4 s  
  > "The data from every band went through three rounds of phase-only self-calibration, with solution intervals *infinity*, 30.5 s, and 10.4 s." (ALMA Observations)

### Imaging

- task: tclean  
  > "We use *tclean* for imaging and use the Briggs robust parameter of 0.5 for each wavelength." (ALMA Observations); "The final images were made using *tclean* and a natural weighting." (VLA Q-band Observations)
- deconvolver: _not stated_
- weighting robust: ALMA: Briggs robust = 0.5 at each wavelength; VLA: natural weighting  
  > "We use *tclean* for imaging and use the Briggs robust parameter of 0.5 for each wavelength." (ALMA Observations); "The final images were made using *tclean* and a natural weighting." (VLA Q-band Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Final deep cleaning of all four Stokes parameters with a cleaning mask covering the HL Tau disk area  
  > "Final deep cleaning of the four Stokes parameters using a cleaning mask covering the HL Tau disk area" (ALMA Observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: Prominent molecular lines removed for continuum images; no significant line emission found in Band 3  
  > "However, we identified some prominent molecular lines that we removed when making the continuum images." (ALMA Observations); "While we did not find significant line emission in the Band 3 data," (ALMA Observations)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: CASA imsmooth; all five ALMA bands convolved to the Band 3 beam for a matched-resolution comparison  
  > "Thus, we conduct the same procedure at the same radius, but with all the data convolved to the same resulting beam size using the CASA *imsmooth* task." (Results); "We use the beam size from Band 3 which is the largest among the five bands." (Results)
- final beam: ALMA major × minor, PA: Band 3 0.43″ × 0.29″, -13°; Band 4 0.21″ × 0.19″, -28°; Band 5 0.19″ × 0.16″, -76°; Band 6 0.27″ × 0.16″, -46°; Band 7 0.20″ × 0.13″, -81°  
  > "0.43 | 0.29 | -13 | 21 | 7.0 | 7.0 | 25.45 | 144 | 1.8 | 75.0 |
| 4 | 2.07 | 0.21 | 0.19 | -28" (Table 2); "0.19 | 0.16 | -76 | 40 | 12 | 12 | 47.16 | 360 | 1.1 | 525 |
| 6 | 1.29 | 0.27 | 0.16 | -46" (Table 2); "| 7 | 0.872 | 0.20 | 0.13 | -81 | 92 | 25 | 24 | 121.16 | 740 | 0.87 | 1880 |" (Table 2)
- final rms: ALMA σI, σQ, σU in μJy/beam: Band 3 (21, 7.0, 7.0); Band 4 (31, 7.7, 7.7); Band 5 (40, 12, 12); Band 6 (72, 15, 15); Band 7 (92, 25, 24)  
  > "21 | 7.0 | 7.0 | 25.45 | 144 | 1.8 | 75.0 |
| 4 | 2.07 | 0.21 | 0.19 | -28 | 31 | 7.7 | 7.7" (Table 2); "40 | 12 | 12 | 47.16 | 360 | 1.1 | 525 |
| 6 | 1.29 | 0.27 | 0.16 | -46 | 72 | 15 | 15" (Table 2); "| 7 | 0.872 | 0.20 | 0.13 | -81 | 92 | 25 | 24 | 121.16 | 740 | 0.87 | 1880 |" (Table 2)

### Inherited from earlier work

- Band 3 data, reprocessed rather than adopting the original imaging  
  > "data were first presented in (cite: Kataoka2017ApJ...844L...5K) and (cite: Stephens2017), respectively, but we reimaged the measurement sets after self-calibration." (Observations) [from (cite: Kataoka2017ApJ...844L...5K)]
- Band 6 data, reprocessed rather than adopting the original imaging  
  > "data were first presented in (cite: Kataoka2017ApJ...844L...5K) and (cite: Stephens2017), respectively, but we reimaged the measurement sets after self-calibration." (Observations) [from (cite: Stephens2017)]
- Deeper, higher-resolution Band 7 data  
  > "we used deeper and higher resolution data from Stephens et al., (in press)" (Observations) [from Stephens et al., (in press)]
- Adopted distance 147.3 pc for consistency  
  > "We adopt a distance of 147.3 pc for HL Tau for consistency with the recent high angular resolution study (cite: CarrascoGonzalez2019ApJ...883...71C)." (Introduction) [from (cite: CarrascoGonzalez2019ApJ...883...71C)]
- Linear polarized-intensity debiasing with a probability density function  
  > "Following (cite: Vaillancourt2006PASP..118.1340V) and (cite: Hull2015JAI.....450005H), we debias the linear polarized intensity by considering the probability density function (PDF):" (Construction of Polarization Images) [from (cite: Vaillancourt2006PASP..118.1340V); (cite: Hull2015JAI.....450005H)]
- Polarization-angle uncertainty  
  > "\sigma_{\chi} = \frac{1}{2} \frac{ \sigma_{P} }{ P }" (Construction of Polarization Images); "(cite: Hull2015JAI.....450005H)." (Construction of Polarization Images) [from (cite: Hull2015JAI.....450005H)]
- Linear decomposition of azimuthally varying thermal polarization and constant scattering polarization; reference-frame convention rederived  
  > "To quantify the transition, we follow the technique developed from (cite: Lin2022) which disentangles the azimuthal variation of polarization from a constant component." (Polarization Analysis); "Note that the coordinate system is different from the definition adopted in (cite: Lin2022), and we provide the derivation of the principal frame that strictly follows the IEEE definition." (Principal Frame View) [from (cite: Lin2022)]
- Disk orientation and near-far identification used for the principal frame  
  > "The position angle of the disk major axis is $138.02^{\circ}$ based on high angular resolution images from (cite: ALMApartnership2015)." (Principal Frame View); "The far side of the disk is to the northeast since the outflow direction is blueshifted to the northeast and redshifted to the southwest (cite: ALMApartnership2015; Yen2017A&A...608A.134Y)." (Principal Frame View) [from (cite: ALMApartnership2015; Yen2017A&A...608A.134Y)]
- Dipole-limit thermal polarization of a prolate grain  
  > "Assuming a prolate grain in the dipole limit, the polarization purely from thermal emission is (cite: Lee1985ApJ...290..211L; Yang2016MNRAS.460.4109Y):" (Methodology) [from (cite: Lee1985ApJ...290..211L; Yang2016MNRAS.460.4109Y)]
- Geometrically thin dust-layer assumption for local plane-parallel slabs  
  > "Since the dust layer responsible for the HL Tau (sub)millimeter continuum is geometrically thin (cite: Pinte2016ApJ...816...25P), one can approximate each local patch of the dust disk as a plane-parallel slab." (Methodology) [from (cite: Pinte2016ApJ...816...25P)]

### Not stated but needed to reproduce (our reading)

- Numerical disk inclination used to deproject positions and evaluate the q′ and u′ models.
- Exact flagged spectral channels and retained continuum bandwidth for each ALMA dataset.
- tclean cell size, image size, deconvolver, stopping threshold, iteration limits, and exact disk masks.
- Self-calibration reference antenna, gaincal combination and solution-selection settings, and application details.
- Band 6 Helpdesk calibration provenance and exact supplied measurement-set version.
- MCMC priors, likelihood, treatment of q′–u′ covariance, initialization, and convergence criteria.
- Exact radial grid, azimuthal sampling origin, and interpolation or extraction procedure.
- VLA epoch identifiers, discarded epoch, modified pipeline, and position-shift corrections.
- Whether and how primary-beam corrections were applied.

## Analysis recipe

1. **Make consistent continuum Stokes images**: Remove prominent molecular lines, self-calibrate each ALMA band, and deep-clean all four Stokes parameters  
  > "However, we identified some prominent molecular lines that we removed when making the continuum images." (ALMA Observations); "For all the ALMA data presented in this paper, including archival and new data, we self-calibrated and imaged the data for all 5 bands so that they would all be imaged in a consistent manner." (ALMA Observations); "Final deep cleaning of the four Stokes parameters using a cleaning mask covering the HL Tau disk area" (ALMA Observations)
   - software: CASA, tclean
   - parameter: CASA 6.2.1.7 for all ALMA line removal, self-calibration, and imaging  
  > "Line removal, self-calibration, and imaging were performed using the CASA version 6.2.1.7 for all the bands." (ALMA Observations)
   - parameter: Three phase-only self-calibration rounds: infinity, 30.5 s, 10.4 s  
  > "The data from every band went through three rounds of phase-only self-calibration, with solution intervals *infinity*, 30.5 s, and 10.4 s." (ALMA Observations)
   - parameter: Briggs robust = 0.5  
  > "We use *tclean* for imaging and use the Briggs robust parameter of 0.5 for each wavelength." (ALMA Observations)
   - fitting: _not stated_
   - validation: Final signal-to-noise ratios ∼1200, 890, 1200, 1100, 1300 for Bands 3–7  
  > "led to signal-to-noise ratios of $\sim 1200$, 890, 1200, 1100, and 1300 from Bands 3 to 7, respectively." (ALMA Observations)
2. **Construct polarization quantities**: Debias linear polarized intensity using its PDF; derive polarization angle, fraction, and normalized Stokes q and u  
  > "Following (cite: Vaillancourt2006PASP..118.1340V) and (cite: Hull2015JAI.....450005H), we debias the linear polarized intensity by considering the probability density function (PDF):" (Construction of Polarization Images); "The polarization angle is defined by" (Construction of Polarization Images); "In addition, the Stokes $Q$ and $U$ normalized by Stokes $I$ are $q \equiv Q / I$ and $u \equiv U/I$" (Construction of Polarization Images)
   - parameter: σP = sqrt[(σQ² + σU²)/2]  
  > "\sigma_{P} = \sqrt{(\sigma_{Q}^{2} + \sigma_{U}^{2}) / 2}" (Construction of Polarization Images)
   - parameter: For Pm ≥ 5σP, P = sqrt(Q² + U² − σP²); use PDF below 5σP  
  > "For high signal-to-noise detections ($P_{m} \geq 5\sigma_{P}$), a simple approximation exists:" (Construction of Polarization Images); "P = \sqrt{ Q^{2} + U^{2} -  \sigma_{P}^{2} }," (Construction of Polarization Images)
   - parameter: Integrate Stokes I above 3σI; polarization detections also require Stokes I above 3σI  
  > "$F_{\nu}$ is the flux density of Stokes $I$ where we use emission above 3 $\sigma_{I}$." (Construction of Polarization Images); "we only consider polarization detections where Stokes $I$ is also detected above $3\sigma_{I}$." (Polarization Morphology)
   - parameter: ALMA polarization-fraction error floor 0.033%  
  > "Thus, we use the error of $0.033\%$ whenever the error" (Construction of Polarization Images); "is less than this value for data from ALMA." (Construction of Polarization Images)
   - assumption: IAU Stokes-sign convention; E-vectors; polarization angle East-of-North  
  > "The sign of the Stokes parameters follows the IAU convention (cite: Contopoulos1974tiau.book.....C; Hamaker1996A&AS..117..137H; Hamaker1996A&AS..117..161H)." (Construction of Polarization Images); "and goes East-of-North." (Construction of Polarization Images); "We only consider the E-vectors" (Construction of Polarization Images)
   - assumption: 10% absolute flux calibration uncertainty ignored thereafter  
  > "We assume a 10$\%$ absolute calibration uncertainty based on the VLA and the ALMA technical handbooks, but we ignore it for the rest of the paper." (Construction of Polarization Images)
   - fitting: Maximize PDF(P | Pm, σP) to estimate true polarized intensity  
  > "which describes the probability of the true linear polarized intensity $P$ given a measured $P_{m}$ and noise level $\sigma_{P}$." (Construction of Polarization Images); "Thus, we obtain $P$ by finding the maximum" (Construction of Polarization Images)
   - validation: _not stated_
3. **Register image centers**: Fit a 2D Gaussian to each band's Stokes I and use the fitted center as the image origin  
  > "we fit a 2D Gaussian to the Stokes $I$ of each band and set the center of the fitted 2D Gaussian as the origin of the image." (Individual Polarization Quantities)
   - software: CASA, imfit
   - parameter: Input noise: σI from Table 2  
  > "We use the CASA task *imfit* for the fitting and we use $\sigma_{I}$" (Individual Polarization Quantities); "as the input noise level." (Individual Polarization Quantities)
   - fitting: 2D Gaussian with fitted center, deconvolved major and minor FWHM, and position angle  
  > "lists the resulting best-fit value and uncertainty of the center, deconvolved major and minor FWHM, and the position angle." (Individual Polarization Quantities)
   - validation: _not stated_
4. **Rotate to the disk principal frame**: Rotate image coordinates by η and Stokes Q, U by 2η; normalize Q′ and U′ by I  
  > "Stokes $Q'$ and $U'$ are related to the Stokes $Q$ and $U$ in the original sky frame with a simple rotation." (Principal Frame View); "\cos 2 \eta & \sin 2 \eta \\" (Principal Frame View); "Let $q'\equiv Q'/I$ and $u'\equiv U'/I$ (i.e., normalized $Q'$ and $U'$ in the principal frame)." (Methodology)
   - parameter: η = 48.02°  
  > "Thus, we have $\eta = 48.02^{\circ}$." (Principal Frame View)
   - assumption: x along disk minor axis toward the far side; y along disk major axis, 90° East-of-North from x  
  > "We define an image frame with coordinates $x$ and $y$, such that the $x$- and $y$-axes are along the disk minor and major axes, respectively." (Principal Frame View); "we arbitrarily fix the positive $x$-direction to the far side of the disk." (Principal Frame View); "The positive $y$-direction is 90$^{\circ}$ (East-of-North) from that." (Principal Frame View)
   - assumption: Disk major-axis PA 138.02°; northeast is the far side  
  > "The position angle of the disk major axis is $138.02^{\circ}$ based on high angular resolution images from (cite: ALMApartnership2015)." (Principal Frame View); "The far side of the disk is to the northeast since the outflow direction is blueshifted to the northeast and redshifted to the southwest (cite: ALMApartnership2015; Yen2017A&A...608A.134Y)." (Principal Frame View)
   - fitting: _not stated_
   - validation: Reference-frame derivation explicitly follows IEEE convention and differs from Lin2022  
  > "Note that the coordinate system is different from the definition adopted in (cite: Lin2022), and we provide the derivation of the principal frame that strictly follows the IEEE definition." (Principal Frame View)
5. **Separate scattering and thermal polarization**: Fit q′ = s + t(cos² i sin² Φ − cos² Φ) and u′ = −t cos i sin 2Φ to azimuthal profiles at 100 au in each ALMA band  
  > "q' &= s + t (\cos^{2} i \sin^{2} \Phi - \cos^{2} \Phi)" (Methodology); "u' &= - t \cos i \sin 2\Phi" (Methodology); "we fit the azimuthal profile of $q'$ and $u'$, respectively, at 100 au first for each band." (Methodology)
   - software: emcee
   - parameter: 100 au; azimuthal sampling steps equal to geometric average of beam size  
  > "we fit the azimuthal profile of $q'$ and $u'$, respectively, at 100 au first for each band." (Methodology); "Sampling the azimuthal profile uses steps equal to the geometric average of the beam size." (Methodology)
   - parameter: ALMA bands only  
  > "We limit the model to the ALMA Bands since the polarization is better detected around the full azimuth." (Methodology)
   - assumption: Axisymmetric inclined disk; prolate-grain alignment axes in the disk midplane and azimuthal direction  
  > "Next, we consider an inclined axisymmetric disk" (Methodology); "The alignment axes of the prolate grains are in the disk midplane and in the azimuthal direction." (Methodology)
   - assumption: Geometrically thin dust layer approximated locally by plane-parallel slabs  
  > "Since the dust layer responsible for the HL Tau (sub)millimeter continuum is geometrically thin (cite: Pinte2016ApJ...816...25P), one can approximate each local patch of the dust disk as a plane-parallel slab." (Methodology)
   - assumption: Scattering contributes a constant s only to q′; thermal polarization supplies azimuthal variation; components add linearly  
  > "The technique relies on the approximation that scattering mainly produces a constant polarization due to inclination, thermal polarization produces the azimuthal variation, and both quantities add linearly based on polarized radiation transfer calculations in a simplified plane-parallel geometry." (Polarization Analysis); "The polarization from the scattering component, which we denote as $s$, is largely constant of azimuth and only contributes to $q'$ since the inclination-induced polarization is always parallel to the disk minor axis." (Methodology)
   - assumption: Prolate grain in dipole limit; p0 ≪ 1; tp(θg) = t sin² θg, with t attenuated by optical depth  
  > "Assuming a prolate grain in the dipole limit, the polarization purely from thermal emission is" (Methodology); "Since $p_{0} \ll 1$, the resulting polarization remains $\propto p_{0} \sin^{2} \theta_{g}$" (Methodology); "where $t$ is $p_{0}$ attenuated by optical depth." (Methodology)
   - assumption: Distance 147.3 pc  
  > "We adopt a distance of 147.3 pc for HL Tau for consistency with the recent high angular resolution study (cite: CarrascoGonzalez2019ApJ...883...71C)." (Introduction)
   - fitting: emcee MCMC; 32 walkers, 2500 steps, first 500 discarded; marginalized medians and 16th/84th percentiles  
  > "We use 32 walkers and a total of 2500 steps. We ignore the first 500 steps to obtain the posterior probability distribution." (Methodology); "The best-fit values are determined from the median of the marginalized distribution, and the $1\sigma$ uncertainties use the 16th and 84th percentile." (Methodology)
   - validation: Changing walking parameters did not significantly change results; model describes both q′ and u′ across all five bands; posterior distributions shown  
  > "Modifying the walking parameters does not significantly change the results." (Methodology); "We find that the linear decomposition model describes all five bands, in both $q'$ and $u'$, remarkably well considering the simplicity of the model." (Results); "show the resulting one- and two-dimensional posterior probability distribution at each wavelength." (Posterior Probability Distribution)
6. **Measure the scattering spectrum**: Fit the scattering component with a(λ/1 mm)^b  
  > "To describe the spectrum of the scattering component, we fit a power-law in the form of $a (\lambda / 1 \text{mm})^{b}$." (Results)
   - software: emcee
   - fitting: emcee fit for a and b  
  > "We again use *emcee* and obtain $a \sim 0.796 \pm 0.016$ $\%$ and $b \sim -0.26 \pm 0.06$." (Results)
   - validation: Two-dimensional posterior distribution included  
  > "The two-dimensional posterior distribution is also included" (Results)
7. **Check sensitivity to spatial resolution**: Convolve all ALMA images to the Band 3 beam, repeat the decomposition at the same radius, and refit the scattering spectrum  
  > "Thus, we conduct the same procedure at the same radius, but with all the data convolved to the same resulting beam size using the CASA *imsmooth* task." (Results); "We use the beam size from Band 3 which is the largest among the five bands." (Results); "Indeed, by fitting the $s$ spectrum, we get $a=0.831 \pm 0.016 \%$, $b=-0.17 \pm 0.05$" (Results)
   - software: CASA, imsmooth
   - parameter: Target beam: Band 3, 0.43″ × 0.29″, PA -13°  
  > "We use the beam size from Band 3 which is the largest among the five bands." (Results); "| 3 | 3.08 | 0.43 | 0.29 | -13 | 21 | 7.0 | 7.0 | 25.45 | 144 | 1.8 | 75.0 |" (Table 2)
   - fitting: Repeat linear decomposition and power-law fit  
  > "Thus, we conduct the same procedure at the same radius," (Results); "Indeed, by fitting the $s$ spectrum, we get $a=0.831 \pm 0.016 \%$, $b=-0.17 \pm 0.05$" (Results)
   - validation: Scattering spectrum comparable to original; thermal spectrum remains monotonically increasing with wavelength  
  > "is comparable to the original profile, which is reasonable since scattering polarization is largely unidirectional" (Results); "remains monotonically increasing with wavelength and does not change significantly" (Results)
8. **Measure radial scattering and thermal profiles**: Repeat azimuthal-profile fitting at each radius using images at original resolution  
  > "We conduct the same process at each radius to obtain the radial dependence of $s$ and $t$ at each wavelength." (Results); "To maximize the benefits of the high angular resolution, we fit the azimuthal profile at the images with their original resolution." (Results)
   - software: emcee
   - parameter: Minimum radius allows at least eight points for sinusoidal fit; maximum radius set by insufficient 3σ detection around azimuth  
  > "The minimum radius is chosen such that we have at least eight points to fit the sinusoidal curve. The maximum radius cuts off where there is not enough $3\sigma$ detection around the azimuth." (Results)
   - assumption: Inner thermal-polarization drop below 50 au likely affected by beam averaging  
  > "The drop towards the inner radius ($< 50$ au) is likely due to beam averaging which artificially decreases the azimuthal variation from thermal polarization by aligned grains." (Results)
   - fitting: Same s, t azimuthal decomposition repeated radially  
  > "We conduct the same process at each radius to obtain the radial dependence of $s$ and $t$ at each wavelength." (Results)
   - validation: Compare shared thermal-profile features across Bands 4–7 with known gaps and ring  
  > "For Bands 4 to 7, $t$ appears to peak at $r\sim70$ au and drop to a minimum at $r\sim 90$ au." (Results); "The peak at $r\sim 70$ au appears to coincide with the two close and deepest gaps at $68$ and $78$ au (cite: ALMApartnership2015)." (Results); "The minimum at $r\sim 90$ au coincides with the ring at $86$ au." (Results)
9. **Measure near-far side asymmetry**: Average principal-frame Stokes parameters across a beam-width minor-axis slit; compare near and far I, Q′, and q′  
  > "The cut uses a slit along the minor axis with a finite width equal to the beam size and averages the Stokes parameters in the principal frame along the width." (Near-far Side Asymmetry); "Likewise, we show $q'$ which fully represents the polarization fraction while retaining the direction of polarization." (Near-far Side Asymmetry)
   - parameter: f = (Inear − Ifar)/[(Inear + Ifar)/2]; q′ comparison uses a difference, not a fractional difference  
  > "f \equiv \frac{ I_{\text{near}} - I_{\text{far}} }{ (I_{\text{near}} + I_{\text{far}}) / 2 }" (Near-far Side Asymmetry); "Note that this is not the *fractional* difference, like that used for Stokes $I$." (Near-far Side Asymmetry)
   - assumption: Along the minor axis U′ ∼0, so Q′ represents polarized intensity while retaining direction  
  > "In the principal frame, $P$ is well represented by Stokes $Q'$, since Stokes $U'$ is $\sim 0$ and using Stokes $Q'$ retains the sign to represent the direction of polarization." (Near-far Side Asymmetry)
   - fitting: Uncertainty of f from error propagation  
  > "The uncertainty of $f$ is estimated through error propagation." (Near-far Side Asymmetry)
   - validation: Consistent offsets across wavelengths strengthen the asymmetry detection; compare with scattering models  
  > "In addition, the consistent offset across wavelengths strengthens the case that the asymmetry is real." (Near-far Side Asymmetry); "The polarization asymmetry from the data (except the inner regions of Band 4) appears to match the model expectation overall." (What can produce the near-far side asymmetry?)
10. **Test Q-band aligned-grain predictions**: Deproject detected-vector locations, predict polarization angles with s = 0, rotate to sky frame, compare normalized angle residuals, and infer t from p  
  > "we can deproject the location of the detected vectors and derive the expected $\chi$ from toroidally aligned prolate grains." (Q-Band consistency with toroidally aligned grains); "but assume $s=0$ to derive the $\chi$ in the principal frame and rotate it to the sky frame." (Q-Band consistency with toroidally aligned grains); "From the deprojected locations, we can estimate the level of $t$ using the observed $p$." (Q-Band consistency with toroidally aligned grains)
   - parameter: Four detected polarization vectors  
  > "the probability for random noise to have 4 points within $\pm 1\sigma_{\chi}$ of the expected polarization direction" (Q-Band consistency with toroidally aligned grains)
   - assumption: s = 0 for predicted polarization angles  
  > "but assume $s=0$ to derive the $\chi$ in the principal frame and rotate it to the sky frame." (Q-Band consistency with toroidally aligned grains)
   - assumption: No free-free subtraction; detections at least ∼1 beam (0.15″) from center and free-free emission confined to ∼40 mas  
  > "we did not remove the free-free component as was done in (cite: CarrascoGonzalez2019ApJ...883...71C) because the free-free emission is only within the central $\sim 40$ mas" (Q-Band consistency with toroidally aligned grains); "and the polarization detections are at least $\sim 1$ beam ($0.15\ensuremath{''}$) away from the center." (Q-Band consistency with toroidally aligned grains)
   - assumption: Likely optically thin disk permits comparing inferred t with intrinsic p0  
  > "Given that the disk is likely optically thin (cite: CarrascoGonzalez2016ApJ...821L..16C; CarrascoGonzalez2019ApJ...883...71C), we estimate that the intrinsic polarization of grains, $p_{0}$, should be comparable." (Q-Band consistency with toroidally aligned grains)
   - fitting: t uncertainties propagated using only uncertainty in p  
  > "where the uncertainty is from error propagation with only the uncertainty from $p$." (Q-Band consistency with toroidally aligned grains)
   - validation: Normalized angle residuals 0.5, -0.4, 0.4, 0.08; random-angle probability ∼7 × 10^-5  
  > "The differences with the observed $\chi$ normalized by the $\sigma_{\chi}$ are 0.5, -0.4, 0.4, and 0.08 which means the observed $\chi$ are consistent with toroidally aligned prolate grains." (Q-Band consistency with toroidally aligned grains); "$\Pi_{i=1}^{4} 2 \sigma_{\chi, i} / 180^{\circ} \sim 7 \times 10^{-5}$" (Q-Band consistency with toroidally aligned grains)
11. **Constrain grain structure**: Compare weak scattering-spectrum wavelength dependence and absence of a thermal-polarization flip with compact and porous-grain expectations  
  > "Aside from the scattering behavior, the lack of any flip in the underlying thermal polarization direction from aligned grains from 870 $\mu$m to 7 mm also constrains the grain structure." (Grain structure); "Based on the weak $\lambda$ dependence of scattering polarization and the lack of any flip in the underlying thermal polarization, we suspect that the grains in HL Tau are porous, and prolate with a maximum size of $\sim 1$ mm." (Grain structure)
   - assumption: For compact elongated grains, Rayleigh-regime thermal polarization follows the projected long axis when λ > 2πa; a flip can occur in the Mie regime  
  > "Compact elongated grains produce thermal polarization following the direction along the projected long axis when $\lambda$ is much larger than grain size $a$, or more specifically when $\lambda > 2 \pi a$ (Rayleigh regime)." (Grain structure); "However, when $\lambda$ is comparable to $2 \pi a$ (Mie regime), the (thermal) polarization direction can flip, i.e., change by $90^{\circ}$, and become perpendicular to the projected long axis" (Grain structure)
   - fitting: _not stated_
   - validation: Detailed modeling of such grains against multiwavelength Stokes I and polarization deferred to future work  
  > "Future efforts to incorporate such grains into detailed modeling for comparison with the multi-wavelength Stokes $I$ and polarization data will be valuable." (Grain structure)

## Software

- **Common Astronomy Software Applications (CASA)** 4.7.38335; 6.2.1.7: ALMA and VLA calibration and imaging; Band 3 pipeline calibration in 4.7.38335; Bands 4, 5, 7 pipeline calibration and all ALMA line removal, self-calibration, imaging in 6.2.1.7  
  > "We used the Common Astronomy Software Applications (CASA) package for all calibration and imaging on the ALMA and VLA data (cite: McMullin2007ASPC..376..127M)." (Observations); "To run the calibration pipeline we used CASA version 4.7.38335 for Band 3, while for Bands 4, 5, and 7 we used version 6.2.1.7." (ALMA Observations); "Line removal, self-calibration, and imaging were performed using the CASA version 6.2.1.7 for all the bands." (ALMA Observations)
- **ALMA calibration pipeline** : ALMA-supplied scripts for bandpass, phase, polarization, and flux calibration  
  > "Prior to self-calibration, we re-ran the data through ALMA’s calibration pipeline using the ALMA-supplied calibration scripts." (ALMA Observations); "These scripts do the standard calibration, which includes bandpass, phase, polarization, and flux calibration." (ALMA Observations)
- **NRAO Pipeline** : Modified VLA calibration pipeline including polarization calibration after gain calibration  
  > "For the calibration of the data we used CASA and a modified version of the NRAO Pipeline which includes polarization calibration after the usual gain calibration." (VLA Q-band Observations)
- **tclean** : ALMA imaging with Briggs robust 0.5 and VLA imaging with natural weighting  
  > "We use *tclean* for imaging and use the Briggs robust parameter of 0.5 for each wavelength." (ALMA Observations); "The final images were made using *tclean* and a natural weighting." (VLA Q-band Observations)
- **imfit** : 2D Gaussian fits to Stokes I for image centering and deconvolved size measurements  
  > "we fit a 2D Gaussian to the Stokes $I$ of each band and set the center of the fitted 2D Gaussian as the origin of the image." (Individual Polarization Quantities); "We use the CASA task *imfit* for the fitting" (Individual Polarization Quantities)
- **imsmooth** : Convolve ALMA data to the common Band 3 beam  
  > "Thus, we conduct the same procedure at the same radius, but with all the data convolved to the same resulting beam size using the CASA *imsmooth* task." (Results); "We use the beam size from Band 3 which is the largest among the five bands." (Results)
- **emcee** : MCMC estimates of s and t and power-law fitting of the scattering spectrum  
  > "We use *emcee*, a Monte Carlo Markov Chain sampling code (cite: ForemanMackey2013PASP..125..306F), to find the best-fit values and uncertainties of $s$ and $t$ at each wavelength." (Methodology); "We again use *emcee* and obtain $a \sim 0.796 \pm 0.016$ $\%$ and $b \sim -0.26 \pm 0.06$." (Results)
- **RIVANNA** : Acknowledged UVA research computing support  
  > "and UVA research computing (RIVANNA)." (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Scattering-spectrum normalization a, original resolution | ∼0.796 | ±0.016 | % | 6 | We again use *emcee* and obtain $a \sim 0.796 \pm 0.016$ $\%$ and $b \sim -0.26 \pm 0.06$. |
| Scattering-spectrum index b, original resolution | ∼-0.26 | ±0.06 | dimensionless | 6 | We again use *emcee* and obtain $a \sim 0.796 \pm 0.016$ $\%$ and $b \sim -0.26 \pm 0.06$. |
| Scattering-spectrum normalization a, common beam | 0.831 | ±0.016 | % | 7 | Indeed, by fitting the $s$ spectrum, we get $a=0.831 \pm 0.016 \%$, $b=-0.17 \pm 0.05$ |
| Scattering-spectrum index b, common beam | -0.17 | ±0.05 | dimensionless | 7 | Indeed, by fitting the $s$ spectrum, we get $a=0.831 \pm 0.016 \%$, $b=-0.17 \pm 0.05$ |
| Thermal-component radial peak, Bands 4–7 | ∼70 | not stated | au | 8 | For Bands 4 to 7, $t$ appears to peak at $r\sim70$ au and drop to a minimum at $r\sim 90$ au. |
| Thermal-component radial minimum, Bands 4–7 | ∼90 | not stated | au | 8 | For Bands 4 to 7, $t$ appears to peak at $r\sim70$ au and drop to a minimum at $r\sim 90$ au. |
| Stokes I near-far fractional differences across bands | ∼5 | not stated | % | 9 | The fractional differences are $\sim 5\%$ across bands based on $f$ |
| Near-side minus far-side q′ at r ∼70 au | ∼0.3 | not stated | % | 9 | At regions with more confident detection, $r \sim 70$ au, the near side $q'$ is larger than the far side $q'$ by $\sim 0.3\%$ across bands. |
| Near-side minus far-side q′ at larger radii | ∼1 | not stated | % | 9 | At even larger radii, the difference increases to $\sim 1\%$, but with less certainty. |
| Q-band thermal component t, vector 1 | 4.1 | ±0.9 | % | 10 | We find that the values are $4.1 \pm 0.9 \%$, $9\pm 3\%$, $15 \pm 5 \%$, and $10\pm 3 \%$ |
| Q-band thermal component t, vector 2 | 9 | ±3 | % | 10 | We find that the values are $4.1 \pm 0.9 \%$, $9\pm 3\%$, $15 \pm 5 \%$, and $10\pm 3 \%$ |
| Q-band thermal component t, vector 3 | 15 | ±5 | % | 10 | We find that the values are $4.1 \pm 0.9 \%$, $9\pm 3\%$, $15 \pm 5 \%$, and $10\pm 3 \%$ |
| Q-band thermal component t, vector 4 | 10 | ±3 | % | 10 | We find that the values are $4.1 \pm 0.9 \%$, $9\pm 3\%$, $15 \pm 5 \%$, and $10\pm 3 \%$ |
| Q-band angle residuals normalized by σχ, vectors 1–4 | 0.5, -0.4, 0.4, 0.08 | not stated | dimensionless | 10 | The differences with the observed $\chi$ normalized by the $\sigma_{\chi}$ are 0.5, -0.4, 0.4, and 0.08 which means the observed $\chi$ are consistent with toroidally aligned prolate grains. |
| Probability of four random angles within ±1σχ of predictions | ∼7 × 10^-5 | not stated | dimensionless | 10 | $\Pi_{i=1}^{4} 2 \sigma_{\chi, i} / 180^{\circ} \sim 7 \times 10^{-5}$ |
| Q-band median polarization fraction | 6.7 | not stated | % | 2 | / Q / 6.97 / 0.16 / 0.14 / 45 / 4.9 / 3.9 / 4.0 / 1.010 / 17 / 6.7 / 4.94 / |
| Band 3 median polarization fraction | 1.8 | not stated | % | 2 | / 3 / 3.08 / 0.43 / 0.29 / -13 / 21 / 7.0 / 7.0 / 25.45 / 144 / 1.8 / 75.0 / |
| Band 4 median polarization fraction | 1.6 | not stated | % | 2 | / 4 / 2.07 / 0.21 / 0.19 / -28 / 31 / 7.7 / 7.7 / 27.53 / 186 / 1.6 / 215 / |
| Band 5 median polarization fraction | 1.1 | not stated | % | 2 | / 5 / 1.48 / 0.19 / 0.16 / -76 / 40 / 12 / 12 / 47.16 / 360 / 1.1 / 525 / |
| Band 6 median polarization fraction | 0.88 | not stated | % | 2 | / 6 / 1.29 / 0.27 / 0.16 / -46 / 72 / 15 / 15 / 81.78 / 590 / 0.88 / 710 / |
| Band 7 median polarization fraction | 0.87 | not stated | % | 2 | / 7 / 0.872 / 0.20 / 0.13 / -81 / 92 / 25 / 24 / 121.16 / 740 / 0.87 / 1880 / |
| Q-band integrated Stokes I flux density | 4.94 | not stated | mJy | 2 | / Q / 6.97 / 0.16 / 0.14 / 45 / 4.9 / 3.9 / 4.0 / 1.010 / 17 / 6.7 / 4.94 / |
| Band 3 integrated Stokes I flux density | 75.0 | not stated | mJy | 2 | / 3 / 3.08 / 0.43 / 0.29 / -13 / 21 / 7.0 / 7.0 / 25.45 / 144 / 1.8 / 75.0 / |
| Band 4 integrated Stokes I flux density | 215 | not stated | mJy | 2 | / 4 / 2.07 / 0.21 / 0.19 / -28 / 31 / 7.7 / 7.7 / 27.53 / 186 / 1.6 / 215 / |
| Band 5 integrated Stokes I flux density | 525 | not stated | mJy | 2 | / 5 / 1.48 / 0.19 / 0.16 / -76 / 40 / 12 / 12 / 47.16 / 360 / 1.1 / 525 / |
| Band 6 integrated Stokes I flux density | 710 | not stated | mJy | 2 | / 6 / 1.29 / 0.27 / 0.16 / -46 / 72 / 15 / 15 / 81.78 / 590 / 0.88 / 710 / |
| Band 7 integrated Stokes I flux density | 1880 | not stated | mJy | 2 | / 7 / 0.872 / 0.20 / 0.13 / -81 / 92 / 25 / 24 / 121.16 / 740 / 0.87 / 1880 / |
| Conditional compact-grain size bound from lack of polarization flip | smaller than ∼140 | not stated | μm | 11 | At face value, the lack of any flip even at our shortest wavelength band implies that the grain size should be smaller than $\sim 140$ $\mu$m. |

## Qualitative findings

- Polarization transitions smoothly from predominantly minor-axis-parallel at shorter wavelengths to azimuthal at longer wavelengths  
  > "The new data strengthens the case for a smooth systematic transition from unidirectional polarization direction to an azimuthal direction as the wavelength increases." (Conclusions)
- Thermal polarization increases monotonically with wavelength; scattering polarization generally decreases slowly  
  > "Evidently, the contribution from thermal polarization, $t$, monotonically increases with increasing wavelength." (Results); "The contribution from scattering, $s$, slowly decreases with increasing wavelength in general with the exception of $s$ at $\lambda$=1.5 mm (Band 5)" (Results)
- Scattering component largely constant with radius, without coherent radial changes across wavelengths  
  > "For each wavelength, $s$ appears largely constant with radius though there is a hint of stronger $s$ at inner radii." (Results); "However, there is a large scatter and there are no obvious coherent radial changes across wavelengths." (Results)
- Thermal component peaks in low-surface-density regions and is minimized in high-surface-density regions, consistent with optical depth effects  
  > "$t$ reaches a peak in the low surface density region and becomes a minimum in the high surface density, which is what we expect from optical depth effects of polarization from aligned grains" (Results)
- Porous, prolate grains with maximum size ∼1 mm are suspected rather than established by detailed grain modeling  
  > "Based on the weak $\lambda$ dependence of scattering polarization and the lack of any flip in the underlying thermal polarization, we suspect that the grains in HL Tau are porous, and prolate with a maximum size of $\sim 1$ mm." (Grain structure)
- ALMA Stokes V detections are largely attributable to instrumental effects  
  > "The inconsistency between the Band 7 images for two different epochs suggests that the current ALMA Stokes $V$ detections are largely due to instrumental effects." (Stokes $V$ Images)

## Claim tuples

- H: The wavelength-dependent polarization transition continues through the previously unobserved intermediate bands. | E: Compare consistently imaged ALMA Bands 3–7 and VLA Q-band polarization. | R: New Bands 4 and 5 fit the transition between the established longer- and shorter-wavelength morphologies. | F: The data strengthen a smooth systematic transition toward azimuthal polarization with increasing wavelength. | **supported**
- H: Scattering and thermal emission of toroidally aligned prolate grains can explain the multiwavelength transition through optical depth effects. | E: Fit a linear decomposition to ALMA azimuthal q′ and u′ profiles. | R: The model describes all five bands; thermal polarization increases with wavelength while scattering decreases slowly. | F: The transition provides further evidence for scattering prolate grains aligned toroidally. | **supported**
- H: Grain structure can explain the weak scattering-spectrum wavelength dependence without a thermal-polarization flip. | E: Compare measured scattering spectrum and thermal-polarization orientation with compact and porous-grain expectations. | R: Weak wavelength dependence and no flip from 870 μm to 7 mm. | F: Porous, prolate grains with maximum size ∼1 mm are suspected; detailed modeling remains necessary. | **partially**
- H: The marginal Q-band vectors agree with toroidally aligned prolate grains. | E: Predict angles at deprojected vector positions with s = 0 and compare against observed angles and errors. | R: Normalized angle residuals 0.5, -0.4, 0.4, 0.08; projection-corrected thermal fractions 4.1 ± 0.9%, 9 ± 3%, 15 ± 5%, 10 ± 3%. | F: Q-band angles are consistent with aligned grains and suggest high intrinsic polarization, subject to limited data. | **partially**
- H: Scattering in an inclined, optically and geometrically thick disk explains the observed near-far asymmetry. | E: Compare beam-width minor-axis cuts of I and q′ with scattering-model expectations. | R: Near-side q′ exceeds far-side q′ by ∼0.3% near 70 au; Stokes I changes asymmetry with radius. | F: Scattering models explain parts of the asymmetry but cannot jointly explain I and q′. | **partially**

## Reasoning

- Why this data: Additional wavelengths test the polarization transition and optical-depth interpretation  
  > "To further test if toroidally aligned prolate grains with varying optical depth can explain the polarization transition, we need additional resolved polarization observations at different wavelengths." (Introduction)
- Why this method: Q and U retain polarization level and direction; linear decomposition avoids full-disk geometry and uncertain grain opacities  
  > "Using Stokes $Q$ and $U$ instead of $P$ is beneficial since they retain the information on both the level of polarization and the direction." (Polarization Analysis); "The approximation enables us to sidestep complications arising from the full disk geometry and (uncertain) grain opacities and directly estimate the contributions from scattering and thermal emission from the azimuthal variation." (Methodology)
- Alternative: Compact grains smaller than ∼140 μm satisfy the no-flip constraint but are unlikely to explain weak scattering-spectrum wavelength dependence or VLA I and P  
  > "At face value, the lack of any flip even at our shortest wavelength band implies that the grain size should be smaller than $\sim 140$ $\mu$m." (Grain structure); "However, such a small grain size is unlikely to explain the weak $\lambda$ dependence of the $s$-spectrum or the level of Stokes $I$ and $P$ at the VLA wavelengths" (Grain structure)
- Alternative: Settled spherical grains of different sizes can reproduce weak wavelength dependence, but most likely in optically thick inner regions  
  > "Dust settling with a spatial distribution of various sizes of spherical grains can reproduce the weak $\lambda$ dependence, the level of polarization, and the multiwavelength Stokes $I$, but most likely for the inner regions" (Grain structure)
- Alternative: Strong forward scattering explains Stokes I asymmetry but fails for q′; scattering without strong forward scattering has the opposite limitation  
  > "Scattering without strong forward scattering can produce the asymmetry of $q'$ but not that of Stokes $I$, while scattering with forward scattering produces the asymmetry of Stokes $I$ but not that of $q'$." (What can produce the near-far side asymmetry?)
- Alternative: Substructure and intrinsic non-axisymmetry remain possible origins of the asymmetries  
  > "Other possibilities include substructures or intrinsically non-axisymmetric features either in the surface density distribution and/or in the grain properties." (What can produce the near-far side asymmetry?)
- Alternative: Gold alignment mechanism requires supersonic speeds and is not applicable to a protoplanetary disk  
  > "However, the Gold mechanism requires supersonic speeds which is not applicable for a protoplanetary disk (cite: Purcell1979ApJ...231..404P; Takeuchi2002ApJ...581.1344T)." (Implications on grain alignment in disks)
- How they decided it was enough: 100 au balances beam-convolution effects and signal-to-noise; radial fits require at least eight points and sufficient 3σ azimuthal detections  
  > "The chosen radius is $\sim 2$ beams away from the center for the Band 3 image, which has the poorest resolution, to minimize the effects of beam convolution," (Methodology); "but is also within a range with enough signal-to-noise for all five bands." (Methodology); "The minimum radius is chosen such that we have at least eight points to fit the sinusoidal curve. The maximum radius cuts off where there is not enough $3\sigma$ detection around the azimuth." (Results)
- Limitation (authors): Few marginal Q-band vectors prevent analysis of azimuthal variation  
  > "Though the few marginally detected polarization vectors at Q-band prohibit an anlaysis of the azimuthal variation," (Grain structure)
- Limitation (authors): Q-band t uncertainties use only p uncertainty  
  > "where the uncertainty is from error propagation with only the uncertainty from $p$." (Q-Band consistency with toroidally aligned grains)
- Limitation (authors): Q-band central vector can be contaminated by scattering or diminished by beam averaging  
  > "However, that particular vector can be contaminated by scattering, which gives positive $Q'$, or artificially diminished due to beam averaging effects since the vector is located near the center." (Q-Band consistency with toroidally aligned grains)
- Limitation (authors): True intrinsic grain polarization requires higher resolution or better long-wavelength data  
  > "Concrete conclusions for the true $p_{0}$ of grains require higher angular resolution images and/or better data at long wavelengths" (Q-Band consistency with toroidally aligned grains)
- Limitation (authors): Stokes I asymmetry depends on the adopted Gaussian-fit center; precise centering is beyond scope  
  > "can depend on the center, but precise determination of the center is beyond the scope of this paper." (What can produce the near-far side asymmetry?)
- Limitation (authors): Band 3's larger beam confounds interpretation of weaker Stokes I asymmetry as an optical-depth effect  
  > "Band 3 also has a much larger beam making it unclear if the difference is truly from optical depth effects." (What can produce the near-far side asymmetry?)
- Limitation (authors): No natural explanation for effectively prolate grains aligned toroidally  
  > "Currently, we do not have a natural explanation for why grains in the disk behave in this manner." (Implications on grain alignment in disks)
- Limitation (authors): 10% absolute calibration uncertainty excluded from subsequent analysis  
  > "We assume a 10$\%$ absolute calibration uncertainty based on the VLA and the ALMA technical handbooks, but we ignore it for the rest of the paper." (Construction of Polarization Images)
- Limitation (authors): ALMA Stokes V signals fall below the minimum detectable circular-polarization threshold  
  > "Indeed, the ALMA peak $|V|$ detections all fall below the minimum detectable threshold" (Stokes $V$ Images)
- Caveat (inferred, ours): The numerical inclination is missing despite entering both the decomposition and Q-band projection corrections.
- Caveat (inferred, ours): Priors, likelihood, and correlated-image-noise treatment are unspecified, limiting reproduction of posterior uncertainties.
- Caveat (inferred, ours): The four-vector random-angle probability is not a complete false-detection assessment without the spatial search and selection procedure.
- Caveat (inferred, ours): The porous ∼1 mm grain interpretation is qualitative rather than a fitted grain-size or porosity measurement.
- Caveat (inferred, ours): The acknowledgements print 2019.1.00162.S, whereas the observations and Table 1 identify Band 6 as 2016.1.00162.S.
- Caveat (inferred, ours): The VLA frequency range is printed as 39-47 Hz; its intended units require clarification.

## Reproducibility

- Data public (paper): Data underlying the article available from the corresponding author upon request  
  > "Data underlying this article is available from the corresponding author upon request." (Data Availability)
- Products in archive: _not stated_
- Missing: Analysis scripts and explicit MCMC priors and likelihood.
- Missing: Numerical inclination and its provenance.
- Missing: Exact imaging commands, masks, line-channel exclusions, and self-calibration application settings.
- Missing: Exact ALMA input-product identifiers, particularly the Helpdesk-provided Band 6 calibration.
- Missing: Modified VLA pipeline, retained epoch list, and alignment offsets.
- Missing: Machine-readable s and t measurements, radial profiles, and posterior samples.
- Missing: Clarification of the inconsistent Band 6 project code.
- Missing: An explicit public location for the data products.
- Data volume (inferred): Cannot estimate reliably from the text; visibility integration sampling, averaging, and delivered product sizes are unspecified.
- Score (inferred): 3/5, The main equations, software, self-calibration intervals, image statistics, and sampler lengths are given. Missing inclination, fit specification, imaging commands, scripts, and product access prevent an exact independent reproduction.
- Rediscovery candidate: no, Main results are numeric, but public availability is not established by the supplied text and essential recipe settings are missing.

## Links

- Method: (cite: Lin2022) (Linear scattering/thermal decomposition and plane-parallel polarized-transfer approximation; reference frame rederived here.)
- Method: (cite: Vaillancourt2006PASP..118.1340V) (Polarized-intensity PDF debiasing.)
- Method: (cite: Hull2015JAI.....450005H) (Polarized-intensity debiasing and polarization-angle uncertainty.)
- Method: (cite: ForemanMackey2013PASP..125..306F) (emcee MCMC sampling.)
- Method: (cite: McMullin2007ASPC..376..127M) (CASA calibration and imaging.)
- Method: (cite: Lee1985ApJ...290..211L; Yang2016MNRAS.460.4109Y) (Dipole-limit thermal polarization of prolate grains.)
- Method: Perley & Butler 2013 (Adopted 3C147 polarization calibration parameters.)
- Method: (cite: Contopoulos1974tiau.book.....C; Hamaker1996A&AS..117..137H; Hamaker1996A&AS..117..161H) (Stokes-sign and polarization-reference-frame conventions.)
- Companion: (cite: Kataoka2017ApJ...844L...5K) (Original presentation of reused Band 3 data.)
- Companion: (cite: Stephens2017) (Original presentation of reused Band 6 data and previous Band 7 comparison.)
- Companion: Stephens et al., (in press) (Source of deeper, higher-resolution Band 7 data and resolved ring/gap polarization comparisons.)
- Companion: (cite: Lin2022) (Previous decomposition of Bands 3 and 6 and predictions tested with the new wavelengths.)
- Companion: (cite: CarrascoGonzalez2019ApJ...883...71C) (Distance convention, optical-depth comparisons, grain-size modeling, and free-free context.)

## Checks

```json
{
 "quotes": 287,
 "quotes_ok": 287,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 5,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2019.1.00162.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 28,
 "numeric_problems": 0,
 "fill": {
  "facts": 167,
  "stated": 147,
  "rate": 0.88
 },
 "evidence_ok": true
}
```
