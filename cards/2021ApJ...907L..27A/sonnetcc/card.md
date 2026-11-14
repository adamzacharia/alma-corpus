# Complications in the ALMA Detection of Phosphine at Venus

`2021ApJ...907L..27A` | The Astrophysical Journal Letters 2021 | first author: Akins, Alex B. | arXiv: 2101.09831 | DOI: 10.3847/2041-8213/abd56a

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type archival_reuse

## Science

- Fields: solar_system, astrochemistry
- Question: Is the 266.94 GHz PH3 feature in the Greaves et al. ALMA Venus data robust to the calibration revisions, and does ALMA line dilution allow SO2 above the 10 ppb limit to go undetected in the wideband data?  
  > "A 266.94 GHz spectral feature is apparent in the narrowband data using the initial calibration procedures, but this same feature can not be identified following calibration revisions." (abstract); "We also investigate the phenomenon of apparent spectral line dilution over varying spatial scales resulting from the ALMA antenna configuration." (abstract)
- Target **Venus**: coordinates _not stated_; z/distance angular diameter 15.36 arcseconds at time of observation  
  > "which is smaller than the angular diameter of Venus at the time of observation (15.36 arcseconds)" (Simulation of ALMA Line Dilution); distance from _not stated_

## Data provenance

- ALMA projects: 2018.A.0023.S
- bands: Band 6 (1.123 mm, near 266.94 GHz)  
  > "The ALMA Band 6 correlator configurations for these observations included wideband" (Introduction); "PH$_3$ 1-0 transition line near 266.94 GHz (1.123 mm)" (Introduction)
- frequencies and spectral setup: Wideband: 1.875 GHz bandwidth, 976.562 kHz resolution; narrowband: 117.1875 MHz bandwidth, 61.035 kHz resolution; setups centered on PH3 1-0 and on HDO 2(2,0)-3(1,3)  
  > "wideband (1.875 GHz bandwidth, 976.562 kHz spectral resoluton) and narrowband (117.1875 MHz bandwidth, 61.035 kHz spectral resolution) setups" (Introduction); "centered on both the PH$_3$ 1-0 line of interest and the nearby HDO 2$_{2,0}$-3$_{1,3}$ line for validation." (Introduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C-2  
  > "ALMA observed Venus in the C-2 configuration (15-314 m baselines) on March 5, 2019 over two observing sessions" (Methods)
- baselines: 15-314 m (C-2); baselines shorter than 33 m removed in the LB dataset  
  > "ALMA observed Venus in the C-2 configuration (15-314 m baselines)" (Methods); "For one of these copies, baselines shorter than 33 m were removed from the data" (Reduction and Imaging of ALMA Data)
- angular resolution: _not stated_
- max recoverable scale: about 9.8 arcsec for C-2 in Band 6 (all baselines); 7.1 arcsec after removing baselines under 33 m  
  > "The maximum recoverable spatial scale (MRS) of ALMA Band 6 observations using the C-2 antenna configuration is near 9.8 arcseconds" (Simulation of ALMA Line Dilution); "reducing the MRS to 7.1 arcseconds." (Simulation of ALMA Line Dilution)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: March 5, 2019, two observing sessions  
  > "on March 5, 2019 over two observing sessions" (Methods)
- pi or archival as stated: Archival re-analysis of ALMA Director's Discretionary Time data of Greaves et al.  
  > "the observation data were obtained from the ALMA archive" (Methods); "Discretionary Time program 2018.A.0023.S." (Acknowledgements)
- Line: PH3 1-0 (near 266.94 GHz)
- Line: SO2 30(9,21)-31(8,24) (not stated)
- Line: SO2 13(3,11)-13(2,12) (near 267.54 GHz)
- Line: SO2 28(4,24)-28(3,25) (near 267.72 GHz)
- Line: HDO 2(2,0)-3(1,3) (not stated)
- Other facility **JCMT**: Original single-dish detection of the 266.94 GHz feature (not reanalysed here)  
  > "A spectral feature was first observed near this frequency using the James Clerk Maxwell Telescope (JCMT)" (Introduction)
- External data: Greaves et al. initial calibration and imaging scripts (Supplemental Software 2 and 3)  
  > "were initially reduced and imaged using the scripts provided by (cite: Greaves2020) (Supplemental Software 2 and 3)." (Reduction and Imaging of ALMA Data) [from Greaves et al. 2020 (cite: Greaves2020)]
- External data: Revised JAO calibration scripts and image products from the ALMA archive  
  > "The initial calibration procedures were then revised by the Joint ALMA Observatory, and these scripts, as well as revised image products, were made available on the ALMA archive." (Reduction and Imaging of ALMA Data) [from Joint ALMA Observatory; revised procedures also presented in (cite: Greaves2020a)]
- External data: Simulated SO2 spectrum of Venus used as the line model in the dilution simulations  
  > "the simulated SO$_2$ spectrum of Venus presented in Figure 3D of (cite: Lincowski2020) is imposed over several scales" (Simulation of ALMA Line Dilution) [from Lincowski et al. 2020 (cite: Lincowski2020)]
- External data: Maximum recoverable scale of Band 6 C-2 observations  
  > "near 9.8 arcseconds (cite: Remijan2019)" (Simulation of ALMA Line Dilution) [from Remijan et al. 2019, ALMA Technical Handbook (cite: Remijan2019)]
- External data: Mesospheric H2O abundance of 2.5 ppm from prior ALMA observations  
  > "Assuming the (cite: Encrenaz2015) H$_2$O mesospheric abundance of 2.5 ppm" (Discussion) [from Encrenaz et al. 2015 (cite: Encrenaz2015)]
- Simulation/model as data: Limb-darkened disk model of Venus with the Lincowski et al. SO2 spectrum imposed over several spatial scales, Fourier transformed and re-imaged with CASA  
  > "is imposed over several scales on a limb-darkened disk model of Venus." (Simulation of ALMA Line Dilution); "The Fourier Transform of these models are then re-imaged with CASA" (Simulation of ALMA Line Dilution)

## Processing

### Calibration

- pipeline or manual: Manual scripts: initial Greaves et al. scripts, then JAO-revised scripts with 3rd-order amplitude / 5th-order phase polynomial bandpass  
  > "The most significant change was the use of a polynomial fit (3rd order amplitude, 5th order phase) to determine bandpass calibrations from the Callisto observations." (Reduction and Imaging of ALMA Data); "were initially reduced and imaged using the scripts provided by (cite: Greaves2020)" (Reduction and Imaging of ALMA Data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: No; data re-reduced with archive-provided revised scripts, modified only to remove baselines shorter than 33 m  
  > "We used these scripts to re-reduce the dataset, only modifying the archive procedures to remove antenna baselines less than 33 m following (cite: Greaves2020a)." (Reduction and Imaging of ALMA Data)
- flux calibrator: Callisto (flux and bandpass); gain/phase on J2000-1748  
  > "The Venus observations are flux-calibrated and bandpass-calibrated using observations of Callisto prior to antenna gain/phase calibration using observations of J2000-1748." (Reduction and Imaging of ALMA Data)
- flux scale uncertainty: _not stated_
- self calibration: Phase-only self-calibration, solution interval 30 s, starting from a limb-darkened disk model fitted to the calibrated visibilities  
  > "This starting model is used for phase-only self-calibration with a solution interval of 30s" (Reduction and Imaging of ALMA Data)

### Imaging

- task: Multiscale CLEAN of continuum-subtracted and continuum-included data (task name not stated)  
  > "both the continuum-subtracted and continuum-included observations are imaged using a multiscale CLEAN approach." (Reduction and Imaging of ALMA Data)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: First-order continuum subtracted from one copy of the data  
  > "Here the ALMA datasets are again duplicated, and a first-order continuum is subtracted from one of the copies." (Reduction and Imaging of ALMA Data)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Two datasets: LB (baselines shorter than 33 m removed) and AB (all baselines)  
  > "whereas all baselines were retained for the other copy (this dataset will be referred to as AB for" (Reduction and Imaging of ALMA Data)
- smoothing: Spectra spectrally averaged to a common resolution of 1.1 km/s  
  > "These data are then spectrally averaged to a common resolution of 1.1 km/s" (Reduction and Imaging of ALMA Data)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Reduction and imaging scripts for the initial calibration  
  > "were initially reduced and imaged using the scripts provided by (cite: Greaves2020) (Supplemental Software 2 and 3)." (Reduction and Imaging of ALMA Data) [from (cite: Greaves2020) Supplemental Software 2 and 3]
- Multiscale CLEAN imaging of continuum-subtracted and continuum-included data  
  > "As in Supplemental Software 3 from (cite: Greaves2020), both the continuum-subtracted and continuum-included observations are imaged using a multiscale CLEAN approach." (Reduction and Imaging of ALMA Data) [from (cite: Greaves2020) Supplemental Software 3]
- 12th order polynomial baseline fit to narrowband spectra in a 40 km/s window excluding the central 5 km/s  
  > "12th order polynomials are fit to the spectral baseline using a $|$40$|$ km/s window excluding the central $|$5$|$ km/s from the fit in the manner described in (cite: Greaves2020)." (Reduction and Imaging of ALMA Data) [from (cite: Greaves2020)]
- Averaging of north and south mid-latitude and polar regions to form regional spectra  
  > "As per (cite: Greaves2020) Table 1, both north and south mid-latitude and polar regions are averaged to form their respective spectra" (ALMA Data) [from (cite: Greaves2020) Table 1]
- Removal of baselines shorter than 33 m  
  > "only modifying the archive procedures to remove antenna baselines less than 33 m following (cite: Greaves2020a)." (Reduction and Imaging of ALMA Data) [from (cite: Greaves2020a)]
- Starting visibility model for self-calibration  
  > "(for the visibility model, see the Appendix A of (cite: Butler1999))" (Reduction and Imaging of ALMA Data) [from (cite: Butler1999) Appendix A]

### Not stated but needed to reproduce (our reading)

- CASA version used for reduction, self-calibration, imaging and simulations
- Imaging parameters: cell size, image size, multiscale scales, weighting/robust, niter, threshold, masks, restoring beam
- Fitted limb-darkened disk parameters (brightness temperature, limb-darkening law, diameter) and which fitting method was used
- Flagging details and spectral-window/channel selection; how the two sessions were combined
- Definition of equatorial, mid-latitude and polar regions used for the regional spectra
- Polynomial order and fitting window used for the wideband spectra baseline
- How line-to-continuum ratio and the percent line dilution were computed from the images
- Dilution simulations: sizes and positions of the SO2 regions, disk model temperature, uv sampling, noise, whether the continuum-subtracted model used the same CLEAN setup
- Whether the paper's own scripts and reduced cubes are available
- Telluric/line-free channel choices

## Analysis recipe

1. **Initial calibration of archival Venus data**: Apply Tsys, antenna position and WVR tables, flag, duplicate datasets into LB (baselines under 33 m removed) and AB (all baselines); flux and bandpass calibration on Callisto, gain/phase on J2000-1748; combine the two sessions  
  > "System temperature, antenna position, and water vapor radiometer calibration tables were applied to the data prior to initial flagging." (Reduction and Imaging of ALMA Data); "The Venus observations are flux-calibrated and bandpass-calibrated using observations of Callisto prior to antenna gain/phase calibration using observations of J2000-1748." (Reduction and Imaging of ALMA Data)
   - software: CASA
   - parameter: Baselines shorter than 33 m removed in LB copy  
  > "For one of these copies, baselines shorter than 33 m were removed from the data" (Reduction and Imaging of ALMA Data)
   - fitting: _not stated_
   - validation: _not stated_
2. **Re-reduce with revised calibration**: Re-run the JAO-revised scripts, whose main change is a polynomial bandpass fit to Callisto, modified only to remove baselines under 33 m  
  > "The most significant change was the use of a polynomial fit (3rd order amplitude, 5th order phase) to determine bandpass calibrations from the Callisto observations." (Reduction and Imaging of ALMA Data); "We used these scripts to re-reduce the dataset, only modifying the archive procedures to remove antenna baselines less than 33 m following (cite: Greaves2020a)." (Reduction and Imaging of ALMA Data)
   - software: CASA
   - parameter: Bandpass polynomial: 3rd order amplitude, 5th order phase  
  > "(3rd order amplitude, 5th order phase)" (Reduction and Imaging of ALMA Data)
   - fitting: _not stated_
   - validation: Compared spectra from initial vs revised calibration; the narrowband feature appears only with the initial calibration  
  > "While a distinct spectral feature would be apparent following the subtraction of the 12th order polynomial from the narrowband spectra obtained with the initial calibration, no such feature is apparent upon correction of the calibration procedures." (ALMA Data)
3. **Self-calibrate and image spectral cubes**: Fit a limb-darkened disk model to calibrated visibilities as the starting model, phase-only self-calibration, subtract first-order continuum from a copy, multiscale CLEAN of both copies to cubes of 1920 channels  
  > "we adopt a functionally similar approach by fitting a limb darkened disk model to the calibrated visibilities." (Reduction and Imaging of ALMA Data); "The resulting products are spectral image cubes of Venus with 1920 channels for both the wideband and narrowband data." (Reduction and Imaging of ALMA Data)
   - software: CASA
   - parameter: Phase-only self-calibration with 30 s solution interval  
  > "This starting model is used for phase-only self-calibration with a solution interval of 30s" (Reduction and Imaging of ALMA Data)
   - parameter: First-order continuum subtracted from one copy  
  > "a first-order continuum is subtracted from one of the copies." (Reduction and Imaging of ALMA Data)
   - fitting: Limb-darkened disk model fitted to calibrated visibilities  
  > "by fitting a limb darkened disk model to the calibrated visibilities." (Reduction and Imaging of ALMA Data)
   - validation: _not stated_
4. **Extract spectra and remove baseline ripple**: Disk-averaged and regional (equator, mid-latitude, polar) spectra, averaged to 1.1 km/s, background ripple removed with polynomials; line-to-continuum ratios from continuum image fluxes; narrowband baseline uses 12th order polynomial  
  > "We obtain disk-averaged spectra as well as spectra averaged over equators, mid-latitudes, and polar regions." (Reduction and Imaging of ALMA Data); "These data are then spectrally averaged to a common resolution of 1.1 km/s, and the background spectral ripples are subtracted using polynomial functions." (Reduction and Imaging of ALMA Data); "The line-to-continuum ratios are determined using the fluxes of the continuum images for both baseline configurations." (Reduction and Imaging of ALMA Data)
   - software: CASA, CARTA
   - parameter: Narrowband: 12th order polynomial, 40 km/s window, central 5 km/s excluded  
  > "12th order polynomials are fit to the spectral baseline using a $|$40$|$ km/s window excluding the central $|$5$|$ km/s from the fit" (Reduction and Imaging of ALMA Data)
   - fitting: Polynomial baseline fits to the spectra  
  > "the background spectral ripples are subtracted using polynomial functions." (Reduction and Imaging of ALMA Data)
   - validation: Authors note that a high order polynomial can artificially reduce narrowband noise  
  > "we note that the use of a high order polynomial to fit the narrowband data artificially reduces spectral noise in this dataset" (Reduction and Imaging of ALMA Data)
5. **Simulate ALMA line dilution for SO2**: Impose the simulated SO2 spectrum on a limb-darkened Venus disk over several spatial scales, Fourier transform, re-image with CASA using LB and AB baseline coverage, normalise line intensities by the disk-averaged starting model  
  > "The Fourier Transform of these models are then re-imaged with CASA using the corresponding full-baseline coverage and the short-baseline exclusion of the (cite: Greaves2020) ALMA observations." (Simulation of ALMA Line Dilution); "The resulting line intensities are normalized by the disk-averaged intensity of their respective starting models." (Baseline-Dependent Effects and Line Dilution)
   - software: CASA
   - parameter: SO2 enhancement regions distributed from the disk centre to the limb  
  > "the spatial regions of SO$_2$ enhancement are distributed from the center of the disk to the limb." (Simulation of ALMA Line Dilution)
   - assumption: Venus as a limb-darkened disk with the Lincowski et al. simulated SO2 spectrum  
  > "is imposed over several scales on a limb-darkened disk model of Venus." (Simulation of ALMA Line Dilution)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : All data reduction, imaging and the line dilution simulations  
  > "The Common Astronomy Software Applications (CASA) package was used for all data reduction and imaging of the ALMA data, as well as for simulations described in this section." (Methods)
- **CARTA** : Analysis of the spectra of the Venus images  
  > "The spectra of the resulting images of Venus were then analyzed using the Cube Analysis and Rendering Tool for Astronomy (CARTA)." (Methods)
- **Matplotlib** : _not stated_
- **Numpy** : _not stated_

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Line dilution, LB (baselines under 33 m excluded), larger-scale SO2 distributions | ~95 | not stated | percent | 5 | The images excluding short antenna baselines suffer greater line dilution, on the order of 95% for larger scale distributions. |
| Line dilution of model SO2 lines (LB and AB) | many by over 90 | not stated | percent | 5 | the model SO$_2$ spectral lines are diluted considerably, many by over 90%. |
| Line dilution for global and hemispherically symmetric gas distributions | 90-95 | not stated | percent | 5 | gases on global and hemispherically symmetric spatial scales can be diluted on the order of 90-95% |

## Qualitative findings

- A 266.94 GHz narrowband feature appears with the initial calibration plus a 12th order polynomial, and disappears with the revised calibration  
  > "Upon application of the revised calibration procedures, however, no such spectral feature is detected." (Conclusions)
- No 266.94 GHz feature in the wideband data with either calibration  
  > "No 266.94 GHz spectral feature is observed in the wideband data using either set of calibration procedures." (Introduction)
- Wideband spectral ripple is lower in peak-to-peak than in Greaves et al. Extended Data Figure 6  
  > "exhibits a lower peak-to-peak spectral ripple than (cite: Greaves2020) Extended Data Figure 6." (Discussion)
- Wideband SO2 non-detection is potentially consistent with abundances far above the 10 ppb limit because of line dilution  
  > "the non-detection of SO$_2$ in the wideband ALMA data is potentially consistent with a nominal cloud top abundance far greater than the 10 ppb SO$_2$ upper limit" (Conclusions)

## Claim tuples

- H: Is the narrowband 266.94 GHz PH3 feature robust to the calibration revisions? | E: Re-reduced the archival data with initial and revised calibration and subtracted a 12th order polynomial | R: Feature appears with the initial calibration, not with the revised calibration | F: The narrowband detection by Greaves et al. appears highly questionable | **supported**
- H: Is the 266.94 GHz feature present in the simultaneous wideband data? | E: Wideband cubes made with both calibrations | R: No feature with either calibration | F: Lack of wideband detection weakens the argument that the narrowband signal is not spectral ripple | **supported**
- H: Can ALMA line dilution hide SO2 above the 10 ppb limit in the wideband data? | E: Simulated SO2 distributions on a limb-darkened Venus disk imaged with the ALMA C-2 baseline coverage | R: Dilution of 90-95% for global and hemispheric gas distributions | F: SO2 at hundreds of ppb would fall below the noise, though the HDO detection is in tension with this | **partially**
- H: Was PH3 detected in the Venus atmosphere with ALMA? | E: Independent reanalysis of the ALMA data plus dilution modelling | R: Unable to reproduce the detection | F: It appears unlikely that PH3 was detected | **supported**

## Reasoning

- Why this data: Independent verification of the high-impact Greaves et al. detection  
  > "the observations reported by (cite: Greaves2020) must be carefully considered and independently verified by other research groups." (Introduction)
- Why this method: Fit a limb-darkened disk instead of the native CASA Venus model as self-calibration starting model; limb-weighted SO2 placement because the configuration is more sensitive to limb flux  
  > "we adopt a functionally similar approach by fitting a limb darkened disk model to the calibrated visibilities." (Reduction and Imaging of ALMA Data); "Since the ALMA configuration of (cite: Greaves2020) is more sensitive to flux from the limb" (Simulation of ALMA Line Dilution)
- Alternative: A higher-order polynomial bandpass correction (Greaves et al. reanalysis) is considered questionable  
  > "Correcting the bandpass using a higher order polynomial may prove to be questionable" (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): HDO datasets not investigated  
  > "We did not investigate the wideband and narrowband datasets centered on the HDO line." (Reduction and Imaging of ALMA Data)
- Limitation (authors): The HDO detection in the narrowband data contradicts the dilution argument, since water is expected at similar spatial scales  
  > "does contradict with this assessment, as water is expected to be distributed at similar spatial scales." (Discussion)
- Limitation (authors): Limited maximum recoverable scale complicates interpretation of large-scale structure  
  > "This complicates the interpretation of brightness temperature structure at larger angular scales" (Simulation of ALMA Line Dilution)
- Caveat (inferred, ours): No quantitative detection significance, noise or uncertainty values are given for the spectra
- Caveat (inferred, ours): Dilution simulation setup (region sizes, disk temperature, noise) is not specified, so the 90-95% numbers cannot be rebuilt exactly
- Caveat (inferred, ours): Internal inconsistencies: SO2 line at 257.54 GHz in abstract vs 267.54 GHz in text; datasets centered at 299.64 GHz vs 266.94 GHz; Lincowski Figure 3D vs 2D; project code printed as 2018.A.0023.S
- Caveat (inferred, ours): Results depend on the polynomial baseline choice, which the paper itself criticises
- Caveat (inferred, ours): HDO detection tension with the dilution argument is left unresolved

## Reproducibility

- Data public (paper): Data obtained from the ALMA archive; original scripts shared publicly  
  > "the observation data were obtained from the ALMA archive" (Methods); "We thank the authors of the original study for publicly sharing their initial calibration and imaging scripts." (Acknowledgements)
- Products in archive: Revised calibration scripts and revised image products are on the ALMA archive  
  > "these scripts, as well as revised image products, were made available on the ALMA archive." (Reduction and Imaging of ALMA Data)
- Code: Original Greaves et al. calibration and imaging scripts shared; this paper's own scripts and simulation code not stated  
  > "publicly sharing their initial calibration and imaging scripts." (Acknowledgements)
- Missing: CASA version and imaging parameters
- Missing: Simulation set-up details and region definitions
- Missing: Fitted disk model parameters
- Missing: Numeric spectra or line-to-continuum values for the claimed non-detections
- Data volume (inferred): Tens of GB raw for two sessions of Band 6 wideband and narrowband data, plus a few GB of cubes
- Score (inferred): 3/5, Public archival data and public scripts allow a rerun, but imaging and simulation parameters are not given and results are mostly qualitative spectra plus approximate dilution percentages.
- Rediscovery candidate: no, Data are public and scripts exist, but the main results are qualitative non-detections and the simulations are underspecified.

## Links

- Method: Greaves et al. 2020 (cite: Greaves2020) (Original calibration and imaging scripts and the 12th order polynomial method)
- Method: Greaves et al. 2020 follow-on (cite: Greaves2020a) (Revised calibration and baseline removal)
- Method: Villanueva et al. 2020 (cite: Villanueva2020) (Independent reanalysis with bandpass correction)
- Companion: Lincowski et al. 2020 (cite: Lincowski2020) (Companion study; source of the simulated SO2 spectrum)
- Companion: Snellen et al. 2020 (cite: Snellen2020) (Complementary reanalysis)
- Related: ALMA Director's Discretionary Time program 2018.A.0023.S (as printed in the paper)

## Checks

```json
{
 "quotes": 93,
 "quotes_ok": 93,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2018.A.0023.S"
 ],
 "obscore_codes_not_in_card": [
  "2018.A.00023.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 91,
  "stated": 61,
  "rate": 0.67
 },
 "evidence_ok": true
}
```
