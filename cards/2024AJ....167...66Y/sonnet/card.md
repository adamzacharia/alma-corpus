# Chemistry of Complex Organic Molecules in the V883 Ori Disk Revealed by ALMA Band 3 Observations

`2024AJ....167...66Y` | The Astronomical Journal 2024 | first author: Yamato, Yoshihide | arXiv: 2312.01300 | DOI: 10.3847/1538-3881/ad11d9

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: What is the COM inventory, radial distribution, abundance ratios and isotopic (12C/13C, D/H) composition in the outbursting V883 Ori disk as seen in ALMA Band 3?  
  > "Here we present Atacama Large Millimeter/submillimeter Array (ALMA) Band 3 observations of the disk around the young outbursting star V883 Ori" (abstract)
- Target **V883 Ori**: coordinates ICRS 05h38m18.101s, -07d02m26.00s (disk center)  
  > "a central stellar mass of $1.29\,M_\odot$, and a distance of 400 pc, based on previous works (cite: Cieza2016; Tobin2023)" (3.1 Spectrum Extraction and Line Identification); "$\alpha\mathrm{(ICRS)}= 05^\mathrm{h}38^\mathrm{m}18.101s$, $\delta\mathrm{(ICRS)} = -07^\mathrm{d}02^\mathrm{m}26.00s$" (2.2 Calibration and Imaging); z/distance 400 pc  
  > "a central stellar mass of $1.29\,M_\odot$, and a distance of 400 pc, based on previous works (cite: Cieza2016; Tobin2023)" (3.1 Spectrum Extraction and Line Identification); "$\alpha\mathrm{(ICRS)}= 05^\mathrm{h}38^\mathrm{m}18.101s$, $\delta\mathrm{(ICRS)} = -07^\mathrm{d}02^\mathrm{m}26.00s$" (2.2 Calibration and Imaging); distance from previous works (Cieza2016; Tobin2023)  
  > "a central stellar mass of $1.29\,M_\odot$, and a distance of 400 pc, based on previous works (cite: Cieza2016; Tobin2023)" (3.1 Spectrum Extraction and Line Identification); "$\alpha\mathrm{(ICRS)}= 05^\mathrm{h}38^\mathrm{m}18.101s$, $\delta\mathrm{(ICRS)} = -07^\mathrm{d}02^\mathrm{m}26.00s$" (2.2 Calibration and Imaging)

## Data provenance

- ALMA projects: 2021.1.00357.S
- bands: Band 3 (3.3 mm, 92 GHz continuum)  
  > "The combined dust continuum image at 3.3 mm (or 92 GHz) was made using the `tclean` task" (2.2 Calibration and Imaging)
- frequencies and spectral setup: 11 SPWs in FDM; one 937.5 MHz continuum SPW (0.488 MHz res.), ten line SPWs of 58.59 or 117.19 MHz bandwidth (0.141 MHz res.)  
  > "The correlator setup included eleven spectral windows (SPWs) in Frequency Division Mode (FDM), one of which was dedicated to continuum acquisition with a wide bandwidth of 937.5 MHz" (2.1 ALMA Band 3 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: four executions: one compact, three extended  
  > "The observations were carried out in a total of four executions, one with a compact antenna configuration and the other three with an extended antenna configuration." (2.1 ALMA Band 3 Observations)
- baselines: 41–3396 m (extended); 14–740 m (compact)  
  > "2022 Jan. 20 | 41 | 47 | 3.6 | 14–740 | 1.5 | 17.4 | J0423-0120 | J0541-0541" (Table 1)
- angular resolution: ~0.3''–0.4'' (line cubes)  
  > "The typical beam size and the RMS noise level were $\sim0.3\ensuremath{''}$–$0.4\ensuremath{''}$ and 0.6–1 mJy beam$^{-1}$, respectively." (2.2 Calibration and Imaging)
- max recoverable scale: 4.7–5.2'' (extended), 17.4'' (compact)  
  > "2022 Jan. 20 | 41 | 47 | 3.6 | 14–740 | 1.5 | 17.4 | J0423-0120 | J0541-0541" (Table 1)
- sensitivity: line RMS 0.6–1 mJy/beam; continuum 27 uJy/beam  
  > "The beam size and the RMS noise level were $0.39\ensuremath{''}\times0.27\ensuremath{''}$ (P.A. $= -74\ensuremath{^\circ}$) and 27 μJy beam$^{-1}$, respectively." (2.2 Calibration and Imaging)
- time on source: 43, 43, 43 and 47 min per execution  
  > "2021 Nov. 21 | 44 | 43 | 2.2 | 41–3396 | 0.3 | 5.2 | J0423-0120 | J0541-0541" (Table 1)
- observing dates: 2021 Nov 21, 21, 22; 2022 Jan 20  
  > "2021 Nov. 22 | 43 | 43 | 3.8 | 41–3396 | 0.3 | 4.7 | J0423-0120 | J0541-0541" (Table 1)
- pi or archival as stated: PI: S. Notsu, Cycle 8  
  > "V883 Ori was observed in Band 3 during ALMA Cycle 8 (project code: 2021.1.00357.S, PI: S. Notsu)." (Observations)
- Line: CH3OH, CH3CHO, CH3OCHO, CH3OCH3, c-C2H4O, CH3COCH3, t-C2H3CHO, s-C2H5CHO and 13C/D isotopologues, OCS, SO2 many; see Table of detected transitions (85–98 GHz)
- External data: Spectroscopic data (frequencies, A coefficients, partition functions) from JPL and CDMS  
  > "the spectroscopic data of the molecular lines are taken from the Jet Propulsion Spectroscopy (cite: JPL) and the Cologne Database for Molecular Spectroscopy" (3.1) [from (cite: JPL); (cite: CDMS1; CDMS2; CDMS3)]
- External data: Methyl formate partition function incl. 13C species  
  > "we used the one calculated by (cite: Favre2014), who fully considered the contributions from torsional (up to $v_t=6$) and vibrational populations." (Appendix 12.3) [from (cite: Favre2014)]
- External data: Band 6 CH3OH image used for smoothing comparison and emitting region  
  > "we assumed that the emitting region in Band 3 is the same as that of CH$_3$OH in Band 6 (cite: Tobin2023)." (3.3 Column Density Retrieval) [from (cite: Tobin2023)]
- External data: Comparison abundance ratios for IRAS 16293-2422, Oph-IRS 48, comet 67P/C-G  
  > "the warm inner envelopes of the Class 0 protobinary IRAS 16293-2422 A/B (cite: Lykke2017; Jorgensen2018; Manigand2020; Manigand2021)" (4.3) [from Lykke2017; Jorgensen2018; Manigand2020; Manigand2021; Brunken2022; Rubin2019; Schuhmann2019]

## Processing

### Calibration

- pipeline or manual: ALMA staff standard pipeline, then manual self-calibration  
  > "Initial calibrations were performed by the ALMA staff using the standard ALMA calibration pipeline version 2021.2.0.128." (2.2)
- casa version: CASA 6.2.1.7  
  > "Common Astronomy Software Applications (cite: CASA) version 6.2.1.7" (2.2)
- pipeline version: 2021.2.0.128  
  > "standard ALMA calibration pipeline version 2021.2.0.128" (2.2)
- archive products used as is: _not stated_
- flux calibrator: J0423-0120 / J0538-4405 (bandpass/amplitude)  
  > "2021 Nov. 21 | 44 | 43 | 2.0 | 41–3396 | 0.3 | 5.2 | J0538-4405 | J0541-0541" (Table 1)
- flux scale uncertainty: 10% adopted (2.5% 1σ quoted later)  
  > "We adopt a 10% uncertainty as an absolute flux calibration accuracy" (2.2)
- self calibration: compact: 1 phase + 1 amp round; extended concatenated: 2 phase-only + 1 amplitude  
  > "Two rounds of phase-only self-calibration and one round of amplitude self-calibration were performed on the combined data." (2.2)

### Imaging

- task: tclean (parallel mpicasa)  
  > "The `tclean` task was run in parallel using `mpicasa` implementation." (2.2)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5; briggsbwtaper with perchanweightdensity=True  
  > "`briggsbwtaper` was used with independent weight densities for each channel (i.e., `perchanweightdensity = True`)" (2.2)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: automultithresh; cleaned to 3 x RMS at native channel width  
  > "All SPWs were cleaned down to 3 $\times$ RMS with the native channel widths." (2.2)
- multiscale scales: _not stated_
- continuum subtraction: imcontsub in image plane (to mitigate JvM effect)  
  > "the continuum component is subtracted from these image cubes using the `imcontsub` task" (2.2)
- line free channels: identified by visual inspection of dirty cubes; channels not listed  
  > "to accurately specify the line-free channels by visually inspecting the dirty image cubes" (2.2)
- primary beam correction: RMS measured on images without primary beam correction  
  > "The RMS noise level was measured on the images without primary beam correction." (2.2)
- array combination: compact and extended data concatenated  
  > "The extended antenna configuration data were then concatenated and self-calibrated together." (2.2)
- smoothing: _not stated_
- final beam: 0.39''x0.27'' continuum; line 0.36–0.42'' x 0.26–0.31''  
  > "The beam size and the RMS noise level were $0.39\ensuremath{''}\times0.27\ensuremath{''}$ (P.A. $= -74\ensuremath{^\circ}$)" (2.2)
- final rms: 0.59–1.1 mJy/beam per SPW  
  > "10 & 97.979676 & 3839 & 937.036 & 0.244 & 0.75 & 1.5 & 0.36$''$$\times$0.26$''$  (-73$\ensuremath{^\circ}$) & 0.59" (Table 2)

### Inherited from earlier work

- Line identification criteria  
  > "Following (cite: Jorgensen2020), we set two criteria for the identification of molecular species." (3.1) [from (cite: Jorgensen2020)]
- Radial intensity profile reconstruction from line profile  
  > "We used an approach similar to that of (cite: Bosman2021) to construct the radial intensity profiles" (3.2.2) [from (cite: Bosman2021)]
- Disk geometry, stellar mass, distance, systemic velocity, emitting region  
  > "based on previous works (cite: Cieza2016; Tobin2023)" (3.1) [from (cite: Cieza2016; Tobin2023)]
- LTE spectral model formulation  
  > "Following the formulation described in Appendix A of (cite: Yamato2022)" (Appendix 10) [from (cite: Yamato2022)]
- JvM correction  
  > "We applied the JvM correction to our data following (cite: Czekala2021)" (Appendix 7) [from (cite: Czekala2021)]

### Not stated but needed to reproduce (our reading)

- Self-calibration solution intervals, reference antennas and gain tables
- Line-free channel ranges used for continuum
- MCMC priors and ranges for the spectral fit and the radial profile fit
- Image size and cell size
- Initial/ranges for gamma and likelihood form
- Exact CASA parameter values for automultithresh
- Inclination uncertainty treatment and which executions' flux were aligned

## Analysis recipe

1. **Self-calibrate and image continuum and line cubes**: Phase/amp self-cal on line-free continuum, applied to lines; tclean with Briggs 0.5; imcontsub  
  > "Self-calibration was then performed using the continuum visibilities with the `gaincal` and `applycal` tasks." (2.2)
   - software: CASA
   - parameter: robust = 0.5, 3 x RMS clean threshold  
  > "All SPWs were cleaned down to 3 $\times$ RMS with the native channel widths." (2.2)
   - fitting: _not stated_
   - validation: JvM effect examined; residual spectrum shows little line left  
  > "almost no spectral line component remain in the residual spectrum and the line emission is almost fully recovered in the CLEANed image" (Appendix 7)
2. **Extract Keplerian-corrected disk-integrated spectra**: GoFish integrated_spectrum() over 1.2'' aperture, deprojecting and aligning to systemic velocity  
  > "we use the `integrated_spectrum()` function implemented in the Python package `GoFish`" (3.1)
   - software: GoFish
   - parameter: PA 32 deg, i = 38.3 deg, M* = 1.29 Msun, d = 400 pc  
  > "we assume a position angle (32$^\circ$) and inclination angle (38.3$^\circ$) of the disk, a central stellar mass of $1.29\,M_\odot$, and a distance of 400 pc" (3.1)
   - assumption: emission from the midplane, no vertical extent  
  > "We also assume that the emission originates from the midplane of the disk, and do not consider the vertical extent of the emission." (3.1)
   - fitting: _not stated_
   - validation: _not stated_
3. **Identify molecular species**: Fit LTE synthetic spectrum; two criteria for robust/tentative identification  
  > "Alternatively, we fitted a synthetic spectrum to the observed spectra to identify each of these features." (3.1)
   - software: JPL/CDMS databases
   - parameter: Aul >= 1e-8 s-1, Eu <= 1000 K  
  > "Only the transitions with an Einstein A coefficient for spontaneous emission of $\geq10^{-8}$ s$^{-1}$ and an upper state energy of $\leq1000$ K" (3.1)
   - assumption: common emitting size, Tex and line width under LTE  
  > "the model used a common emitting region size, a common excitation temperature, and a common line width under the local thermodynamic equilibrium (LTE) conditions." (3.1)
   - fitting: _not stated_
   - validation: no undetected transitions over-predicted  
  > "Second, no undetected transitions are over-predicted by the synthetic spectrum." (3.1)
4. **Moment maps and radial profile reconstruction**: bettermoments zeroth moments within ±3.5 km/s; forward model of line profile to radial intensity with annuli  
  > "integrating over the velocity range of $\pm3.5$ km s$^{-1}$ with respect to the source systemic velocity" (3.2.1)
   - software: bettermoments, emcee
   - parameter: vsys = 4.25 km/s; r0 = 3,5,7,9 au grids combined; smoothed by 0.1'' Gaussian  
  > "we employed four fits with different radial grid created with different starting radii ($r_0 = 3, 5, 7, 9$ au)" (Appendix 11)
   - assumption: midplane emission, local width 0.05 km/s  
  > "where 0.05 km s$^{-1}$ was used practically" (Appendix 11)
   - fitting: emcee MCMC with each radial intensity as free parameter  
  > "The actual fits were conducted by the MCMC algorithm implemented in the `emcee` package" (Appendix 11)
   - validation: compared to Band 6 radial profile  
  > "which is consistent with the higher-resolution Band 6 profile (cite: Tobin2023)" (3.2.2)
5. **Derive column densities, Tex**: Simultaneous LTE fit of all species, excluding tau>0.2 transitions, emitting annulus 0.1''–0.3''  
  > "The inner and outer radius of the emitting area are fixed to 0.1$''$ and 0.3$''$, respectively." (3.3)
   - software: emcee
   - parameter: 24 free parameters; 100 walkers, 15000 steps, 12000 burn-in  
  > "We run 100 walkers for 15000 steps, and the initial 12000 steps are discarded as burn-in." (3.3)
   - assumption: LTE, common Tex and line width, Lorentzian broadening gamma  
  > "an additional parameter $\gamma$ for line broadening" (3.3)
   - fitting: affine-invariant MCMC (emcee); uncertainties 16th/84th percentiles  
  > "We used the affine-invariant Markov Chain Monte Carlo (MCMC) algorithm implemented in the `emcee` Python package" (3.3)
   - validation: tau threshold 0.4 gives columns lower by <=~2  
  > "the resulting column densities are lower by a factor of $\sim2$ or less" (3.3)
6. **Compute abundance, isotopic and isomer ratios and compare**: Column density ratios vs CH3OH, 12C/13C, D/H compared with IRAS 16293-2422, 67P/C-G  
  > "Figure [6](#fig:ratio_comparison) compares the column density ratios of COMs with respect to CH$_3$OH in the V883 Ori disk" (4.3)
   - fitting: _not stated_
   - validation: ratios insensitive to absolute flux calibration  
  > "the column density ratios, from which we discuss the chemistry of COMs in the following sections, are not affected by the absolute flux calibration uncertainty." (3.3)

## Software

- **CASA** 6.2.1.7: self-calibration, imaging, imfit, imcontsub  
  > "Subsequent self-calibration and imaging were performed using the Common Astronomy Software Applications (cite: CASA) version 6.2.1.7." (2.2)
- **GoFish** : Keplerian-corrected integrated spectra  
  > "we use the `integrated_spectrum()` function implemented in the Python package `GoFish`" (3.1)
- **bettermoments** : zeroth moment maps  
  > "These maps are created using `bettermoments` (cite: bettermoments)" (3.2.1)
- **emcee** : MCMC for spectral fit and radial profile  
  > "We used the affine-invariant Markov Chain Monte Carlo (MCMC) algorithm implemented in the `emcee` Python package" (3.3)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Excitation temperature | 106.7 | +4.3/-3.8 | K | 5 | The derived excitation temperature is $106.7_{-3.8}^{+4.3}$ K |
| CH3OH column density | 3.9e18 | +0.7/-0.6 e18 | cm-2 | 5 | CH$_3$OH                    / $3.9_{-0.6}^{+0.7} \times 10^{18}$ |
| CH3OCHO column density | 7.4e17 | ±0.3e17 | cm-2 | 5 | CH$_3$OCHO                  / |
| Common line width | 0.71 | +0.07/-0.05 | km/s | 5 | $0.71_{-0.05}^{+0.07}$ km s$^{-1}$ |
| CH3OCHO/CH3O13CHO | 23 | ±3 | dimensionless | 6 | CH$_3$OCHO/CH$_3$O$^{13}$CHO / 23$_{-3}^{+3}$ |
| CH3OCHO/13CH3OCHO | 23 | +3/-2 | dimensionless | 6 | CH$_3$OCHO/$^{13}$CH$_3$OCHO / 23$_{-2}^{+3}$ |
| CH2DOH/CH3OH (upper limit) | 0.0057 | +0.0018/-0.0015 | dimensionless | 6 | We derived a CH$_2$DOH/CH$_3$OH ratio of $0.0057_{-0.0015}^{+0.0018}$ |
| SO2/OCS | 0.56 | +0.21/-0.20 | dimensionless | 6 | The SO$_2$/OCS ratios are measured to be $0.56_{-0.20}^{+0.21}$ |
| CH3CHO/c-C2H4O | 9.2 | +1.2/-1.1 | dimensionless | 6 | a CH$_3$CHO/$c$-C$_2$H$_4$O ratio of $9.2_{-1.1}^{+1.2}$ |
| Continuum deconvolved size | 0.23''x0.21'' | not stated | arcsec | 1 | obtained a deconvolved size of $0.23\ensuremath{''}\times0.21\ensuremath{''}$ (P.A. $= 106\ensuremath{^\circ}$) |

## Qualitative findings

- Ten oxygen-bearing COMs robustly identified; N-bearing COMs deficient  
  > "nitrogen-bearing COMs seem to be deficient in the V883 Ori disk compared to those in protostellar envelopes." (4.5)

## Claim tuples

- H: Does the inner emission cavity persist in Band 3 where dust is fainter? | E: Line profile forward modelling of Keplerian wings | R: Radial profiles depressed inside ~40 au, peaking at ~50–60 au | F: Inner cavity likely exists in Band 3 (dust absorption and/or chemical destruction) | **supported**
- H: Are COM abundances in the disk enhanced relative to protostellar envelopes? | E: Column density ratios vs CH3OH | R: Ratios higher than IRAS 16293-2422 by a factor >~5–10, similar to 67P | F: Efficient (re)formation of COMs in disks | **supported**
- H: Is 13C fractionated in disk COMs? | E: 12C/13C from isotopologue column densities | R: ~20–30 vs ISM ~69 | F: Efficient 13C-fractionation of CO | **partially**
- H: Are D/H ratios of COMs similar to IRAS 16293B? | E: Deuterated/normal column density ratios | R: Upper limits lower than IRAS 16293B | F: Possible destruction and reformation of COMs in disks | **partially**

## Reasoning

- Why this data: Band 3 has fainter dust continuum, allowing probing of the inner disk; more species and isotopologues  
  > "This necessitates observations at longer wavelengths, where the dust continuum emission is generally expected to be fainter" (1)
- Why this method: _not stated_
- Alternative: JvM correction rejected in favor of image-plane continuum subtraction  
  > "we mitigate the JvM effect and recover correct flux scale as much as possible by employing the continuum subtraction on the image plane" (Appendix 7)
- How they decided it was enough: _not stated_
- Limitation (authors): Emission only marginally resolved; midplane assumption; CH2DOH spectroscopy uncertain by ~factor 3  
  > "Although the uncertainties of the reconstructed radial intensity profiles are quite large" (4.1)
- Caveat (inferred, ours): Common Tex and emitting region assumed for all species despite marginal resolution
- Caveat (inferred, ours): Several isotopologue ratios rely on tentative detections
- Caveat (inferred, ours): Tau<0.2 cut and LTE slab model may bias columns
- Caveat (inferred, ours): JvM epsilon ~0.28 makes statistical uncertainties possibly underestimated

## Reproducibility

- Data public (paper): ALMA project data acknowledged; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2021.1.00357.S." (Acknowledgments)
- Products in archive: _not stated_
- Code: _not stated_
- Missing: Self-cal parameters
- Missing: Line-free channels
- Missing: MCMC priors
- Missing: Custom LTE code not released
- Missing: Image/cell size
- Data volume (inferred): ~50-200 GB raw for four executions, 11 SPWs
- Score (inferred): 3/5, Data and general recipe given, but custom code and several settings (priors, solints, channels) are missing.
- Rediscovery candidate: no, Custom LTE fit and radial-profile code unreleased, and several parameters missing.

## Links

- Method: (cite: Bosman2021) (radial profile reconstruction from line profiles)
- Method: (cite: Czekala2021) (JvM correction)
- Method: (cite: Yamato2022) (LTE spectral model formulation)
- Companion: (cite: Lee2019) (Band 7 COM detections in V883 Ori)
- Companion: (cite: Tobin2023) (Band 6 water and COM observations)
- Related: ALMA-PILS

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
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 87,
  "stated": 69,
  "rate": 0.793
 },
 "evidence_ok": true
}
```
