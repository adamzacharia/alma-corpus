# Tracing Interstellar Heating: An ALCHEMI Measurement of the HCN Isomers in NGC 253

`2022ApJ...939..119B` | The Astrophysical Journal 2022 | first author: Behrens, Erica | arXiv: 2209.06244 | DOI: 10.3847/1538-4357/ac91ce

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: nearby_galaxies, astrochemistry, star_formation
- Question: Can HCN and HNC emission in NGC 253 trace heating processes (mechanical vs cosmic-ray heating), and what are the density and cosmic ray ionization rate in its central GMCs?  
  > "We analyze HCN and HNC emission in the nearby starburst galaxy NGC 253 to investigate its effectiveness in tracing heating processes associated with star formation." (abstract)
- Target **NGC 253 CMZ (10 GMCs)**: coordinates phase center RA(ICRS) 00h47m33.26s, Dec -25d17m17.7s  
  > "at a distance of $3.5\pm0.2$ Mpc (cite: dist_Rekola), NGC 253 is an ideal target for studying extragalactic star formation." (1 Introduction); "The nominal phase center of the observations is $\alpha(ICRS)$ = 00$^h$47$^m$33$^s$.26, $\delta(ICRS)$ = $-25^\circ$17$^\prime$17$^{\prime\prime}.7$." (3.1 ALCHEMI Data); z/distance 3.5±0.2 Mpc  
  > "at a distance of $3.5\pm0.2$ Mpc (cite: dist_Rekola), NGC 253 is an ideal target for studying extragalactic star formation." (1 Introduction); "The nominal phase center of the observations is $\alpha(ICRS)$ = 00$^h$47$^m$33$^s$.26, $\delta(ICRS)$ = $-25^\circ$17$^\prime$17$^{\prime\prime}.7$." (3.1 ALCHEMI Data); distance from Rekola et al. 2005 (cite: dist_Rekola)  
  > "at a distance of $3.5\pm0.2$ Mpc (cite: dist_Rekola), NGC 253 is an ideal target for studying extragalactic star formation." (1 Introduction); "The nominal phase center of the observations is $\alpha(ICRS)$ = 00$^h$47$^m$33$^s$.26, $\delta(ICRS)$ = $-25^\circ$17$^\prime$17$^{\prime\prime}.7$." (3.1 ALCHEMI Data)

## Data provenance

- ALMA projects: 2017.1.00161.L, 2018.1.00162.S
- bands: Bands 3, 4, 6, 7 (Cycle 5), extended to Band 5 (Cycle 6)  
  > "imaged the CMZ within NGC 253 in the ALMA frequency Bands 3, 4, 6, and 7." (3.1 ALCHEMI Data)
- frequencies and spectral setup: ALCHEMI covers 84.2-373.2 GHz; HCN/HNC J=1-0 to 4-3  
  > "The rest-frequency coverage of ALCHEMI ranged from 84.2 to 373.2 GHz." (3.1 ALCHEMI Data)
- continuum bandwidth: _not stated_
- arrays: 12 m Array and ACA combined  
  > "The combination of the 12 m Array and Atacama Compact Array (ACA) measurements used in this analysis resulted in a common maximum recoverable angular scale of $15^{\prime\prime}$ at all frequencies." (3.1 ALCHEMI Data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.6 arcsec (~27 pc); spectral resolution 8-9 km/s  
  > "The final angular and spectral resolution of the image cubes generated from these measurements were $1.^{\prime\prime}6$ ($\sim27$ pc) and 8-9 km s$^{-1}$, respectively" (3.1 ALCHEMI Data)
- max recoverable scale: 15 arcsec  
  > "common maximum recoverable angular scale of $15^{\prime\prime}$ at all frequencies" (3.1 ALCHEMI Data)
- sensitivity: channel RMS 0.26-12.52 mJy/beam depending on transition  
  > "| $2-1$       | 177.261, 181.325 | 6.41, 12.52     |" (Table 1)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: HCN 1-0 (88.632 GHz)
- Line: HCN 2-1 (177.261 GHz)
- Line: HCN 3-2 (265.886 GHz)
- Line: HCN 4-3 (354.505 GHz)
- Line: HNC 1-0, 2-1, 3-2, 4-3 (90.664, 181.325, 271.981, 362.630 GHz)
- External data: GMC positions/definitions (10 GMCs) from HCN, HCO+, CS imaging  
  > "The GMC positions we have adopted in this analysis (Table [5](#tab:GMCpos)) are derived from the GMC positions reported by (cite: leroy15)" (Appendix GMC Positions) [from Leroy et al. 2015 (cite: leroy15)]
- External data: Radio continuum sources and spectral indices (heating sources: SNRs, HII regions)  
  > "We place heating sources observed using radio continuum (cite: ua97) and vibrationally-excited HC$_{3}$N emission (cite: RV2020) in each of our 10 GMCs" (5.1 The Influence of Heating Sources) [from Ulvestad & Antonucci 1997 (cite: ua97); Rico-Villas et al. 2020 (cite: RV2020)]
- External data: Initial depleted elemental abundances  
  > "use depleted abundances from Table 4 of (cite: jenkins2009) for our initial conditions" (4.1 Model Description) [from Jenkins 2009 (cite: jenkins2009)]
- External data: Gas-phase chemical network UMIST12  
  > "We take our gas phase network from UMIST12 (cite: McElroy2013)" (4.1 Model Description) [from McElroy et al. 2013 (cite: McElroy2013)]
- External data: HNC+O and HNC+H reaction barriers (high 2000 K/1200 K, low 20 K/200 K)  
  > "We test both the high (2000 K, 1200 K) and low (20 K, 200 K) barrier values (cite: hacar20)" (4.1 Model Description) [from Hacar et al. 2020 (cite: hacar20)]

## Processing

### Calibration

- pipeline or manual: Calibration and imaging described in ALCHEMI overview paper; archive products used  
  > "Full details regarding the data acquisition, calibration, and imaging are provided in (cite: ALCHEMI-ACA)." (3.1 ALCHEMI Data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Image cubes and continuum extracted from ALCHEMI archive  
  > "From the ALCHEMI archive we extract the $\sim 1.6$ arcsec resolution mosaics of the central molecular zone of NGC 253" (3.1 ALCHEMI Data)
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
- continuum subtraction: as described in ALCHEMI paper  
  > "The continuum subtraction and imaging processes used in this analysis are described in (cite: ALCHEMI-ACA)." (3.1 ALCHEMI Data)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.6 arcsec  
  > "The final angular and spectral resolution of the image cubes generated from these measurements were $1.^{\prime\prime}6$ ($\sim27$ pc)" (3.1 ALCHEMI Data)
- final rms: _not stated_

### Inherited from earlier work

- Data acquisition, calibration, imaging, continuum subtraction  
  > "Full details regarding the data acquisition, calibration, and imaging are provided in (cite: ALCHEMI-ACA)." (3.1 ALCHEMI Data) [from Martín et al. 2021 (cite: ALCHEMI-ACA)]
- CubeLineMoment moment extraction procedure  
  > "we use the `CubeLineMoment`[^2] script introduced for this same purpose by (cite: mangum19)" (3.2 Spectral Line Signal Extraction) [from Mangum et al. 2019 (cite: mangum19)]
- Interloper contamination procedure  
  > "Using the procedure described in (cite: Holdship2022) we determine that these two interlopers contribute respectively at most 4% and 1%" (3.3 Interloper Analysis) [from Holdship et al. 2022 (cite: Holdship2022)]

### Not stated but needed to reproduce (our reading)

- UCLCHEM run duration/time at which abundances are taken and initial density/temperature setup
- UltraNest number of live points and other sampler settings
- Exact GMC averaging aperture handling and CubeLineMoment parameters
- Which archive product versions/cubes were downloaded
- Source lists and counts per GMC used in the Spearman correlations
- UCLPDR input parameters beyond Av~10

## Analysis recipe

1. **Extract integrated line intensities**: CubeLineMoment masking with each line as its own tracer; moment 0,1,2 maps at 3x channel RMS limit  
  > "Final moment 0 (integrated intensity; Jy km s$^{-1}$), 1 (average velocity; km s$^{-1}$) and 2 (velocity dispersion; km s$^{-1}$) images are generated using a signal limit of three-times the spectral channel baseline RMS" (3.2 Spectral Line Signal Extraction)
   - software: CubeLineMoment
   - fitting: _not stated_
   - validation: Interloper check: H2CO and HNC v2=1 contribute at most 4% and 1% to HNC 4-3; not corrected  
  > "Since the estimated correction required to this single transition is small, we do not apply these corrections to our presented integrated intensities." (3.3 Interloper Analysis)
2. **Average intensities over 10 GMCs**: Average integrated intensity within apertures of diameter equal to beam (1.6 arcsec) at GMC positions  
  > "adopting diameters equal to our beam size ($1.^{\prime\prime}6$, which is much smaller than the maximum recoverable angular scale of $15^{\prime\prime}$ for the ALCHEMI image cubes)" (3.2 Spectral Line Signal Extraction)
   - fitting: _not stated_
   - validation: _not stated_
3. **Coupled chemical and radiative transfer forward model**: UCLCHEM single-point gas-grain model gives abundances; SpectralRadex/RADEX gives integrated intensities  
  > "We model the chemical and physical conditions within each of the 10 GMCs using the chemical modeling code `UCLCHEM`**[^3]** (cite: uclchem) and the radiative transfer code `SpectralRadex`[^4]." (4.1 Model Description)
   - software: UCLCHEM, SpectralRadex, RADEX
   - parameter: uniform line width 100 km/s, beam filling factor 1, zeta_0 = 1.36e-17 s-1  
  > "These integrated intensities are calculated assuming a uniform line width of 100 km s$^{-1}$" (4.1 Model Description)
   - assumption: Homogeneous UV-shielded clouds; H2 collisions only (no electrons); no infrared excitation  
  > "we have opted to not consider electron-induced collisions in our analysis" (4.1 Model Description)
   - fitting: _not stated_
   - validation: Tested high and low reaction barrier values; no discernible effect  
  > "as we find varying the temperature barrier had no discernible effect on our results" (4.4 Modeling Results)
4. **Bayesian nested sampling of T, n, zeta, N_H2**: UltraNest MLFriends with Gaussian likelihood; priors T uniform 50-300 K, n log-uniform 1e3-1e7, zeta 10-1e7 zeta_0, N_H2 1e22-1e25  
  > "| $n$ | Volume Density | 10$^3$–10$^7$ cm$^{-3}$ | Log-uniform |" (Table 3); "These iterations continue until the live point weights are insignificant (fractional remainder $\leq$ 0.01)" (4.3 Nested Sampling)
   - software: UltraNest
   - fitting: Gaussian likelihood on 8 integrated intensities per GMC; MLFriends nested sampling; medians with inner 67% intervals  
  > "We can determine $P(\mathbf{F_d}|\boldsymbol\theta)$ by assuming Gaussian errors giving the standard function" (4.3 Nested Sampling)
   - validation: Optical depth checked against isotopologue ratios; bimodal low-zeta solution dismissed using prior literature  
  > "We found that the ratios of modeled optical depths are consistent with the observationally-derived isotope ratios themselves" (4.4 Modeling Results)
5. **Estimate cosmic ray heating temperature**: UCLPDR gas temperature for derived density and CRIR at Av~10  
  > "`UCLPDR` provides an estimated gas temperature given input volume densities and CRIRs, assuming an $A_{V} \sim10$" (4.5 The Effect of Cosmic Rays on the HCN/HNC Ratio)
   - software: UCLPDR
   - fitting: _not stated_
   - validation: Compared to Mangum et al. 2019 kinetic temperatures  
  > "the high kinetic temperatures from our PDR modeling agree with those derived by (cite: mangum19)" (4.5 The Effect of Cosmic Rays on the HCN/HNC Ratio)
6. **Correlation tests**: Spearman rho via scipy spearmanr on 10,000 Gaussian-resampled sets of 10 GMC points  
  > "create simulated Gaussian datasets for these parameters consisting of 10,000 sets of 10 data points each (1 point for each GMC)" (4.4 Modeling Results)
   - software: SciPy
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CubeLineMoment** : integrated intensity and moment maps  
  > "`CubeLineMoment` uses a series of spectral and spatial masks to extract integrated intensities" (3.2 Spectral Line Signal Extraction)
- **UCLCHEM** : gas-grain chemical modeling  
  > "`UCLCHEM` is a gas-grain chemical modeling code" (4.1 Model Description)
- **SpectralRadex / RADEX** : non-LTE radiative transfer  
  > "we use `SpectralRadex`, a python library which includes a wrapper for the `RADEX`[^5] (cite: radex) program" (4.1 Model Description)
- **UltraNest** : MLFriends nested sampling  
  > "using the `UltraNest`[^6] package (cite: ultranest21)" (4.3 Nested Sampling)
- **UCLPDR** : PDR gas temperature from CRIR  
  > "Photon-Dominated Region (PDR) modeling code `UCLPDR`[^9] which treats heating and cooling" (4.5 The Effect of Cosmic Rays on the HCN/HNC Ratio)
- **SciPy** : Spearman correlation  
  > "by employing the `SciPy` (cite: scipy2020) function `spearmanr`" (4.4 Modeling Results)
- **CASA** : listed in software section  
  > "CASA (cite: casa), `Astropy` (cite: Astropy2013)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Median Spearman rho, CRIR vs HCN/HNC abundance ratio | -0.47 | 0.26 | dimensionless | 6 | find that the median $\rho$ value is $-0.47\pm0.26$ |
| Median Spearman rho, CRIR vs heating sources | 0.67 | 0.21 | dimensionless | 6 | the median $\rho$ values for the CRIR-heating source and density-heating source relationships are 0.67 and 0.60 respectively, with standard deviations of 0.21 and 0.17 |
| Median Spearman rho, density vs heating sources | 0.60 | 0.17 | dimensionless | 6 | the median $\rho$ values for the CRIR-heating source and density-heating source relationships are 0.67 and 0.60 respectively, with standard deviations of 0.21 and 0.17 |
| GMC 5 log10 n | 5.62 | +0.31/-0.34 | log cm-3 | 4 | / 5 /  / NC /  / 5.62$^{+0.31}_{-0.34}$ /  / 5.09$^{+0.39}_{-0.50}$ / |
| GMC 5 log10 zeta | 5.09 | +0.39/-0.50 | log zeta_0 | 4 | / 5 /  / NC /  / 5.62$^{+0.31}_{-0.34}$ /  / 5.09$^{+0.39}_{-0.50}$ / |
| PDR gas temperature, inner GMCs 4-6 | ~200-500 | not stated | K | 5 | result in PDR gas temperatures of $\sim200-500$ K, whereas the conditions in the outer GMCs correspond to temperatures of $\sim100-400$ K |
| Interloper contribution to HNC 4-3 | at most 4% (H2CO) and 1% (HNC v2=1) | not stated | % | 1 | these two interlopers contribute respectively at most 4% and 1% to the HNC $4-3$ integrated emission |

## Qualitative findings

- HCN/HNC integrated intensity ratios range 1-5, lowest (~1-2) in GMCs 3-6  
  > "These ratios are at their lowest ($\sim1-2$) in the central region of the CMZ, which encompasses GMCs 3–6." (3.2 Spectral Line Signal Extraction)
- Kinetic temperature and N_H2 not constrained by HCN/HNC data  
  > "We find that kinetic temperature and H$_{2}$ column density are largely not constrained by our HCN and HNC measurements." (4.4 Modeling Results)

## Claim tuples

- H: HCN/HNC ratio traces mechanical heating in NGC 253 | E: Model HCN/HNC intensities with UCLCHEM+RADEX and nested sampling | R: Abundance ratios low (<10), far below ~50 predicted for mechanical heating | F: Mechanical heating not significant; cosmic rays dominate | **supported**
- H: Density and CRIR differ between central and outer GMCs | E: Posterior parameter estimates per GMC | R: n~10^5.5 cm-3 and zeta~10^-12 s-1 in central GMCs, about an order of magnitude higher than outer | F: Central enhancement of n and CRIR | **supported**
- H: CRIR and density correlate with heating sources | E: Spearman tests with resampled uncertainties | R: rho 0.67 and 0.60 | F: Positive correlations | **partially**
- H: HCN/HNC ratio anticorrelates with CRIR | E: Spearman test | R: rho = -0.47±0.26 | F: Moderate anticorrelation | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Treat cosmic ray ionization and heating separately to distinguish their effects  
  > "In order to fully differentiate between the contributions of cosmic ray chemistry and cosmic ray heating on the molecular ISM, we treat cosmic rays and heating separately in our models." (2 HCN and HNC in Galaxies)
- Alternative: Low-zeta bimodal solution dismissed as unphysical  
  > "we dismiss the lower CRIR solution across all GMCs as unphysical and only present the high CRIR solutions." (4.4 Modeling Results)
- How they decided it was enough: _not stated_
- Limitation (authors): Electron collisions and IR excitation not included  
  > "to defer further analysis of the potential impact of electron collisions in our model to a future analysis" (4.1 Model Description)
- Limitation (authors): Dilution when averaging may underestimate intensities  
  > "Any remaining dilution of the HCN and HNC emission when averaging over the chosen GMC positions will underestimate the intensity of that emission." (3.2 Spectral Line Signal Extraction)
- Caveat (inferred, ours): Single-zone isothermal homogeneous model for GMC-scale gas
- Caveat (inferred, ours): Only 10 GMCs, so correlations have low significance
- Caveat (inferred, ours): Bimodal CRIR posterior resolved by external prior rather than data
- Caveat (inferred, ours): Omission of electron collisions could bias density in outer GMCs

## Reproducibility

- Data public (paper): Data extracted from ALCHEMI archive; project codes given  
  > "From the ALCHEMI archive we extract the $\sim 1.6$ arcsec resolution mosaics" (3.1 ALCHEMI Data)
- Products in archive: _not stated_
- Missing: UltraNest settings
- Missing: UCLCHEM run configuration
- Missing: GMC heating source counts
- Data volume (inferred): tens of GB for ALCHEMI cubes in 4 bands (only HCN/HNC cubes needed, few GB)
- Score (inferred): 3/5, Public data and named public codes, with priors and likelihood given, but key sampler and chemical-model settings are missing.
- Rediscovery candidate: yes, Public archive data, Table 2 intensities, explicit priors and likelihood, numeric results (n, zeta, rho).

## Links

- Method: Martín et al. 2021 (cite: ALCHEMI-ACA) (ALCHEMI data acquisition, calibration, imaging)
- Method: Mangum et al. 2019 (cite: mangum19) (CubeLineMoment script)
- Method: Holdship et al. 2022 (cite: Holdship2022) (interloper procedure)
- Companion: Holdship et al. 2021 (cite: holdship_c2h) (CRIR from C2H)
- Companion: Harada et al. 2021 (cite: harada21) (CRIR from HOC+)
- Related: ALCHEMI

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
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 83,
  "stated": 49,
  "rate": 0.59
 },
 "evidence_ok": true
}
```
