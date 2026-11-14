# Tracing Interstellar Heating: An ALCHEMI Measurement of the HCN Isomers in NGC 253

`2022ApJ...939..119B` | The Astrophysical Journal 2022 | first author: Behrens, Erica | arXiv: 2209.06244 | DOI: 10.3847/1538-4357/ac91ce

Card schema 1.0 | model gemini-3.8-flash | depth full | type large_program_or_survey

## Science

- Fields: nearby_galaxies, astrochemistry, star_formation
- Question: To investigate whether HCN and HNC isomer emission traces star formation-associated heating (mechanical shocks vs. cosmic rays) in the Central Molecular Zone of the starburst galaxy NGC 253.  
  > "We analyze HCN and HNC emission in the nearby starburst galaxy NGC 253 to investigate its effectiveness in tracing heating processes associated with star formation." (abstract); "Our work combines ALCHEMI observations with chemical and physical modeling in order to ascertain the mechanisms driving the high kinetic temperatures in the nucleus of NGC 253." (2 HCN and HNC in Galaxies)
- Target **NGC 253 CMZ**: coordinates 00h47m33s.26, -25d17m17.7s  
  > "It has an inclination of 76 deg (cite: incl_McCormick), and at a distance of 3.5+/-0.2 Mpc (cite: dist_Rekola), NGC 253 is an ideal target for studying extragalactic star formation." (1 Introduction); "The nominal phase center of the observations is alpha(ICRS) = 00h47m33s.26, delta(ICRS) = -25deg17'17''.7." (3.1 ALCHEMI Data); z/distance 3.5 +/- 0.2 Mpc  
  > "It has an inclination of 76 deg (cite: incl_McCormick), and at a distance of 3.5+/-0.2 Mpc (cite: dist_Rekola), NGC 253 is an ideal target for studying extragalactic star formation." (1 Introduction); "The nominal phase center of the observations is alpha(ICRS) = 00h47m33s.26, delta(ICRS) = -25deg17'17''.7." (3.1 ALCHEMI Data); distance from (cite: dist_Rekola)  
  > "It has an inclination of 76 deg (cite: incl_McCormick), and at a distance of 3.5+/-0.2 Mpc (cite: dist_Rekola), NGC 253 is an ideal target for studying extragalactic star formation." (1 Introduction); "The nominal phase center of the observations is alpha(ICRS) = 00h47m33s.26, delta(ICRS) = -25deg17'17''.7." (3.1 ALCHEMI Data)

## Data provenance

- ALMA projects: 2017.1.00161.L, 2018.1.00162.S
- bands: Bands 3, 4, 5, 6, 7  
  > "The ALMA Cycle 5 Large Program ALCHEMI (project code 2017.1.00161.L) imaged the CMZ within NGC 253 in the ALMA frequency Bands 3, 4, 6, and 7. This survey was subsequently extended to Band 5" (3.1 ALCHEMI Data)
- frequencies and spectral setup: 84.2 to 373.2 GHz; spectral resolution 8-9 km s^-1  
  > "The final angular and spectral resolution of the image cubes generated from these measurements were 1.''6 (~27 pc) and 8-9 km s^-1, respectively (cite: Martin19)." (3.1 ALCHEMI Data); "The rest-frequency coverage of ALCHEMI ranged from 84.2 to 373.2 GHz." (3.1 ALCHEMI Data)
- continuum bandwidth: _not stated_
- arrays: 12 m Array and Atacama Compact Array (ACA)  
  > "The combination of the 12 m Array and Atacama Compact Array (ACA) measurements used in this analysis resulted in a common maximum recoverable angular scale of 15'' at all frequencies." (3.1 ALCHEMI Data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.6 arcsec (~27 pc)  
  > "The final angular and spectral resolution of the image cubes generated from these measurements were 1.''6 (~27 pc) and 8-9 km s^-1, respectively (cite: Martin19)." (3.1 ALCHEMI Data)
- max recoverable scale: 15 arcsec  
  > "The combination of the 12 m Array and Atacama Compact Array (ACA) measurements used in this analysis resulted in a common maximum recoverable angular scale of 15'' at all frequencies." (3.1 ALCHEMI Data)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: archival  
  > "From the ALCHEMI archive we extract the ~ 1.6 arcsec resolution mosaics of the central molecular zone of NGC 253 in the HCN and HNC 1-0, 2-1, 3-2, and 4-3 rotational transitions." (3.1 ALCHEMI Data)
- Line: HCN 1-0 (88.632 GHz)
- Line: HNC 1-0 (90.664 GHz)
- Line: HCN 2-1 (177.261 GHz)
- Line: HNC 2-1 (181.325 GHz)
- Line: HCN 3-2 (265.886 GHz)
- Line: HNC 3-2 (271.981 GHz)
- Line: HCN 4-3 (354.505 GHz)
- Line: HNC 4-3 (362.630 GHz)
- External data: GMC positions (10 GMC-like structures in NGC 253 CMZ)  
  > "The GMC positions we have adopted in this analysis (Table 5) are derived from the GMC positions reported by (cite: leroy15)" (7 GMC Positions) [from (cite: leroy15)]
- External data: Radio continuum sources / spectral indices for supernova remnants and HII regions  
  > "The strong star formation activity in NGC 253 is evidenced by at least 64 individual compact radio continuum sources within the CMZ (cite: ua97)" (1 Introduction) [from (cite: ua97)]
- External data: Super Hot Cores identified via vibrationally-excited HC3N emission  
  > "containing Super Hot Cores (SHCs) identified by (cite: RV2020) using vibrationally-excited HC3N emission." (1 Introduction) [from (cite: RV2020)]
- External data: Depleted element abundances for initial chemical conditions  
  > "and use depleted abundances from Table 4 of (cite: jenkins2009) for our initial conditions." (4.1 Model Description) [from (cite: jenkins2009)]
- External data: Isotopic integrated intensity ratios HCN/H13CN and HCN/HC15N  
  > "To confirm these optical depth estimates, we use integrated intensity isotopic ratios for HCN/H13CN and HCN/HC15N (cite: Martin19), as well as their isotopomers" (4.4 Modeling Results) [from (cite: Martin19)]

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
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.6 arcsec  
  > "The final angular and spectral resolution of the image cubes generated from these measurements were 1.''6 (~27 pc) and 8-9 km s^-1, respectively (cite: Martin19)." (3.1 ALCHEMI Data)
- final rms: 0.27, 6.41, 1.46, 2.70 mJy/beam for HCN (1-0, 2-1, 3-2, 4-3); 0.26, 12.52, 1.98, 3.47 mJy/beam for HNC  
  > "1-0 | 88.632, 90.664 | 0.27, 0.26 
2-1 | 177.261, 181.325 | 6.41, 12.52 
3-2 | 265.886, 271.981 | 1.46, 1.98 
4-3 | 354.505, 362.630 | 2.70, 3.47" (Table 1)

### Inherited from earlier work

- CubeLineMoment moment extraction methodology and masking procedure  
  > "In order to extract integrated spectral line intensities from our measurements we use the CubeLineMoment script introduced for this same purpose by (cite: mangum19)." (3.2 Spectral Line Signal Extraction) [from (cite: mangum19)]
- Interloper contribution assessment method for HNC 4-3  
  > "Using the procedure described in (cite: Holdship2022) we determine that these two interlopers contribute respectively at most 4% and 1% to the HNC 4-3 integrated emission." (3.3 Interloper Analysis) [from (cite: Holdship2022)]
- Data acquisition, calibration, continuum subtraction, and imaging pipeline  
  > "Full details regarding the data acquisition, calibration, and imaging are provided in (cite: ALCHEMI-ACA)." (3.1 ALCHEMI Data); "The continuum subtraction and imaging processes used in this analysis are described in (cite: ALCHEMI-ACA)." (3.1 ALCHEMI Data) [from (cite: ALCHEMI-ACA)]

### Not stated but needed to reproduce (our reading)

- Exact spatial masking thresholds and smoothing parameters used within the CubeLineMoment script for generating the moment maps.
- Specific line-free channels and polynomial orders used in CASA for continuum subtraction in the ALCHEMI cubes.

## Analysis recipe

1. **Extract spectral line moment maps and measure GMC integrated intensities**: CubeLineMoment script using a signal limit of 3 times the spectral channel baseline RMS to create moment 0 maps; average intensity over 1.6 arcsec diameter circular apertures centered on 10 GMC positions.  
  > "Final moment 0 (integrated intensity; Jy km s^-1), 1 (average velocity; km s^-1) and 2 (velocity dispersion; km s^-1) images are generated using a signal limit of three-times the spectral channel baseline RMS" (3.2 Spectral Line Signal Extraction); "We extract HCN and HNC integrated intensities for each of the four transitions and average each of them over these GMCs, adopting diameters equal to our beam size (1.''6" (3.2 Spectral Line Signal Extraction)
   - software: CubeLineMoment
   - parameter: Signal limit = 3 * sigma_chan; aperture diameter = 1.6 arcsec  
  > "generated using a signal limit of three-times the spectral channel baseline RMS for the respective transition under study." (3.2 Spectral Line Signal Extraction); "adopting diameters equal to our beam size (1.''6" (3.2 Spectral Line Signal Extraction)
   - assumption: GMC emission is smooth enough that offsets between HCN and HNC peaks do not substantially affect calculated integrated intensities; beam-filling factor is 1.  
  > "we find that the emission is smooth enough that any potential offset between the centers of the two species' emission would not substantially affect our calculated integrated intensities." (3.2 Spectral Line Signal Extraction); "These integrated intensities are calculated assuming a uniform line width of 100 km s^-1, which is consistent with the line widths derived from our spectral line extraction procedure (Section 3.2) and a beam-filling factor of 1." (4.1 Model Description)
   - fitting: _not stated_
   - validation: Sample spectrum checks around HNC 4-3 to assess interlopers (H2CO 5_05-4_04 and vibrationally excited HNC v2=1).  
  > "Our CubeLineMoment analysis includes a sample spectrum check to reveal potential spectral line blending. Only the HNC 4-3 transition is found to have spectral neighbors" (3.3 Interloper Analysis)
2. **Gas-grain chemical and non-LTE radiative transfer modeling coupled with Bayesian nested sampling**: Forward model coupling UCLCHEM gas-grain chemistry with RADEX non-LTE radiative transfer wrapped in SpectralRadex, sampled across parameter space using UltraNest MLFriends nested sampling.  
  > "We model the chemical and physical conditions within each of the 10 GMCs using the chemical modeling code UCLCHEM (cite: uclchem) and the radiative transfer code SpectralRadex" (4.1 Model Description); "We sample our parameter space to obtain input for our chemical models using nested sampling techniques by implementing the Monte Carlo algorithm MLFriends (cite: ultranest14; ultranest19) using the UltraNest package (cite: ultranest21)." (4.3 Nested Sampling)
   - software: UCLCHEM, RADEX, SpectralRadex, UltraNest
   - parameter: Priors: T_K uniform [50, 300] K; log10 n log-uniform [3, 7] cm^-3; log10 zeta log-uniform [1, 7] zeta_0; log10 N_H2 log-uniform [22, 25] cm^-2; delta_v = 100 km s^-1  
  > "T | Temperature | 50-300 K | Uniform 
n | Volume Density | 10^3-10^7 cm^-3 | Log-uniform 
zeta | Cosmic Ray Ionization Rate | 10-10^7 zeta_0 | Log-uniform 
N_H2 | H2 Column Density | 10^22-10^25 cm^-2 | Log-uniform" (Table 3); "These integrated intensities are calculated assuming a uniform line width of 100 km s^-1" (4.1 Model Description)
   - assumption: Homogeneous, isothermal clouds shielded from UV radiation; on-the-spot approximation for column densities; collisions with H2 only (electron collisions ignored); no IR pumping.  
  > "We use a single point model to replicate the environment in the GMCs by assuming these gas clouds are homogeneous because they have high enough visual extinctions such that they are shielded from UV radiation" (4.1 Model Description); "It is also important to note that we only consider excitation through collisions with H2 and therefore ignore electron collisions." (4.1 Model Description); "we did not see a justification for including infrared excitation in our radiative transfer model." (4.1 Model Description)
   - fitting: Bayesian nested sampling with UltraNest using Gaussian likelihood comparing observed and predicted integrated intensities until live point weights fractional remainder <= 0.01.  
  > "We can determine P(Fd|theta) by assuming Gaussian errors giving the standard function P(Fd|theta) = exp(-0.5 * sum((Fd,i - Ft,i)^2 / sigma_F,i^2))" (4.3 Nested Sampling); "These iterations continue until the live point weights are insignificant (fractional remainder <= 0.01), indicating the vast majority of the probability density has been sampled." (4.3 Nested Sampling)
   - validation: Dismissal of lower CRIR bimodality mode as unphysical based on independent molecular literature; optical depths validated via isotopic ratios HCN/H13CN and HCN/HC15N.  
  > "As such, we dismiss the lower CRIR solution across all GMCs as unphysical and only present the high CRIR solutions." (4.4 Modeling Results); "To confirm these optical depth estimates, we use integrated intensity isotopic ratios for HCN/H13CN and HCN/HC15N (cite: Martin19), as well as their isotopomers, to modify our HCN and HNC abundance values" (4.4 Modeling Results)
3. **Estimate gas kinetic heating via PDR modeling**: UCLPDR code used to estimate gas temperature given input densities and CRIRs assuming visual extinction Av ~ 10 mag.  
  > "we estimate the heating that would result from these CRIRs via the Photon-Dominated Region (PDR) modeling code UCLPDR which treats heating and cooling. UCLPDR provides an estimated gas temperature given input volume densities and CRIRs, assuming an A_V ~ 10" (4.5 The Effect of Cosmic Rays on the HCN/HNC Ratio)
   - software: UCLPDR
   - parameter: A_V ~ 10 mag  
  > "assuming an A_V ~ 10 (in this case in order to model the inner, UV-shielded part of the cloud)." (4.5 The Effect of Cosmic Rays on the HCN/HNC Ratio)
   - assumption: Visual extinction A_V ~ 10 models the UV-shielded interior of the cloud.  
  > "(in this case in order to model the inner, UV-shielded part of the cloud)." (4.5 The Effect of Cosmic Rays on the HCN/HNC Ratio)
   - fitting: _not stated_
   - validation: Comparison of PDR-predicted gas temperatures (200-500 K in central GMCs) to H2CO-derived kinetic temperatures from Mangum et al. (2019).  
  > "However, the high kinetic temperatures from our PDR modeling agree with those derived by (cite: mangum19) and overlap with the kinetic temperatures found through UCLCHEM modeling, when constrained." (4.5 The Effect of Cosmic Rays on the HCN/HNC Ratio)
4. **Statistical correlation analysis between derived parameters and heating sources**: Monte Carlo Spearman rank correlation analysis generating 10,000 sets of Gaussian samples from derived posterior distributions.  
  > "In order to determine the significance of this apparent anti-correlation, we calculate the Spearman coefficient rho for the relationship between CRIR and the HCN/HNC abundance ratio by employing the SciPy (cite: scipy2020) function spearmanr" (4.4 Modeling Results); "We use our modeled abundance ratios and CRIR estimates for each GMC in combination with their uncertainties to create simulated Gaussian datasets for these parameters consisting of 10,000 sets of 10 data points each" (4.4 Modeling Results)
   - software: SciPy
   - parameter: 10,000 Monte Carlo iterations across 10 GMCs  
  > "consisting of 10,000 sets of 10 data points each (1 point for each GMC)." (4.4 Modeling Results)
   - assumption: Errors on parameters follow Gaussian distributions for the Monte Carlo sampling.  
  > "to create simulated Gaussian datasets for these parameters consisting of 10,000 sets of 10 data points each" (4.4 Modeling Results)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Data processing and reduction  
  > "CASA (cite: casa), Astropy (cite: Astropy2013), MLFriends (cite: ultranest14; ultranest19), UltraNest (cite: ultranest21), SciPy (cite: scipy2020)" (6 Software)
- **CubeLineMoment** : Extracting moment 0, 1, and 2 integrated spectral line intensity maps using masking  
  > "In order to extract integrated spectral line intensities from our measurements we use the CubeLineMoment script introduced for this same purpose by (cite: mangum19)." (3.2 Spectral Line Signal Extraction)
- **UCLCHEM** : Gas-grain chemical network modeling to calculate chemical abundances  
  > "UCLCHEM is a gas-grain chemical modeling code that incorporates user-defined chemical networks to produce chemical abundances given the input physical conditions of the gas" (4.1 Model Description)
- **RADEX** : Non-LTE statistical equilibrium radiative transfer code using escape probability  
  > "RADEX is a 1D non-Local Thermodynamic Equilibrium (LTE) statistical equilibrium radiative transfer code that assumes an isothermal and homogeneous environment." (4.1 Model Description)
- **SpectralRadex** : Python wrapper library for RADEX to connect abundances to integrated intensities  
  > "To incorporate radiative transfer modeling, we use SpectralRadex, a python library which includes a wrapper for the RADEX program." (4.1 Model Description)
- **UltraNest** : Bayesian nested sampling package implementing the MLFriends algorithm  
  > "We sample our parameter space to obtain input for our chemical models using nested sampling techniques by implementing the Monte Carlo algorithm MLFriends (cite: ultranest14; ultranest19) using the UltraNest package (cite: ultranest21)." (4.3 Nested Sampling)
- **MLFriends** : Monte Carlo nested sampling algorithm  
  > "implementing the Monte Carlo algorithm MLFriends (cite: ultranest14; ultranest19) using the UltraNest package (cite: ultranest21)." (4.3 Nested Sampling)
- **UCLPDR** : Photon-Dominated Region modeling code to compute gas heating and cooling temperatures  
  > "we estimate the heating that would result from these CRIRs via the Photon-Dominated Region (PDR) modeling code UCLPDR which treats heating and cooling." (4.5 The Effect of Cosmic Rays on the HCN/HNC Ratio)
- **SciPy** : Statistical analysis, calculating Spearman rank correlation coefficients with spearmanr  
  > "calculate the Spearman coefficient rho for the relationship between CRIR and the HCN/HNC abundance ratio by employing the SciPy (cite: scipy2020) function spearmanr" (4.4 Modeling Results)
- **Astropy** : General astronomy data handling and analysis  
  > "CASA (cite: casa), Astropy (cite: Astropy2013), MLFriends (cite: ultranest14; ultranest19), UltraNest (cite: ultranest21), SciPy (cite: scipy2020)" (6 Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Median Spearman correlation coefficient between CRIR and HCN/HNC abundance ratio | -0.47 | +/-0.26 | dimensionless | 4 | We calculate rho for each set of 10 data points in the simulated distributions and find that the median rho value is -0.47+/-0.26 (Figure 13). |
| Median Spearman correlation coefficient between CRIR and number of heating sources | 0.67 | 0.21 | dimensionless | 4 | we find that the median rho values for the CRIR-heating source and density-heating source relationships are 0.67 and 0.60 respectively, with standard deviations of 0.21 and 0.17. |
| Median Spearman correlation coefficient between volume density and number of heating sources | 0.60 | 0.17 | dimensionless | 4 | we find that the median rho values for the CRIR-heating source and density-heating source relationships are 0.67 and 0.60 respectively, with standard deviations of 0.21 and 0.17. |
| Volume density log10(n) for GMC 5 | 5.62 | +0.31/-0.34 | log10(cm^-3) | 2 | 5 / NC / 5.62^+0.31_-0.34 / 5.09^+0.39_-0.50 / 23.50^+0.87_-0.67 |
| CRIR log10(zeta) for GMC 5 | 5.09 | +0.39/-0.50 | log10(zeta_0) | 2 | 5 / NC / 5.62^+0.31_-0.34 / 5.09^+0.39_-0.50 / 23.50^+0.87_-0.67 |
| Volume density log10(n) for GMC 1 | 3.81 | +0.90/-0.48 | log10(cm^-3) | 2 | 1 / 172.53^+75.77_-67.79 / 3.81^+0.90_-0.48 / 3.87^+0.15_-0.22 / 22.85^+0.82_-0.54 |
| CRIR log10(zeta) for GMC 1 | 3.87 | +0.15/-0.22 | log10(zeta_0) | 2 | 1 / 172.53^+75.77_-67.79 / 3.81^+0.90_-0.48 / 3.87^+0.15_-0.22 / 22.85^+0.82_-0.54 |

## Qualitative findings

- Volume density and cosmic ray ionization rates are enhanced by about an order of magnitude in the nuclear central GMCs (4, 5, 6) compared to the outer GMCs.  
  > "We find that the volume density n_H2 and cosmic ray ionization rate (CRIR) zeta are enhanced by about an order of magnitude in the galaxy's central regions as compared to those further from the nucleus." (abstract)
- HCN/HNC integrated intensity and abundance ratios are low (<10, typically 1-5), contradicting expectations of large mechanical shock heating.  
  > "The HCN/HNC abundance ratios are low (<10) in the NGC 253 CMZ. This result is consistent with findings in other extragalactic systems but is at odds with previous theoretical work that suggested this ratio should be high" (6 Conclusions)
- Cosmic ray heating dominates the interstellar heating budget, producing high gas temperatures (~200-500 K), while mechanical heating does not significantly affect HCN/HNC chemistry.  
  > "Though previous studies suggested HCN and HNC may reveal strong mechanical heating processes in NGC 253's CMZ, we find cosmic ray heating dominates the heating budget, and mechanical heating does not play a significant role in the HCN and HNC chemistry." (abstract)
- HCN and HNC formation is dominated by temperature-independent dissociative recombination of HCNH+ at high CRIR, rendering the HCN/HNC ratio insensitive to kinetic temperature.  
  > "Both species then form mainly through the reactions HCNH+ + e- -> HCN + H and HCNH+ + e- -> HNC + H which have identical rates at all temperatures. Once the CRIR is large enough for these reactions to dominate, both species form at roughly identical rates." (4.5 The Effect of Cosmic Rays on the HCN/HNC Ratio)

## Claim tuples

- H: HCN and HNC emission ratios in starburst galaxies probe mechanical heating via shocks. | E: Observed 4 rotational transitions of HCN and HNC across 10 GMCs in NGC 253 CMZ with ALMA, and modeled chemistry and non-LTE line radiative transfer using UCLCHEM and RADEX. | R: HCN/HNC integrated intensity ratios are low (1-5) even in regions of high kinetic temperature (200-500 K); high CRIR drives identical formation rates for both isomers. | F: Mechanical heating does not dominate the HCN and HNC chemistry; cosmic ray heating dominates the heating budget, and high CRIR explains the low ratio. | **refuted**
- H: Cosmic ray ionization rate and gas volume density are enhanced in the central GMCs of NGC 253. | E: Nested sampling parameter estimation using UltraNest constraining density and CRIR with UCLCHEM + RADEX models. | R: GMCs 4, 5, and 6 show n ~ 10^5.5 cm^-3 and zeta ~ 10^-12 s^-1 (10^4-10^5 zeta_0), an order of magnitude higher than outer GMCs. | F: Star formation activity in the central CMZ enhances both volume density and cosmic ray ionization rates. | **supported**
- H: Cosmic ray ionization rates correlate with the presence and distribution of star formation heating sources and supernovae. | E: Spearman rank correlation test on Monte Carlo realizations linking derived CRIR and density to counts of radio continuum compact sources and super hot cores. | R: Positive Spearman rank correlations with median rho = 0.67 (CRIR vs heating sources) and 0.60 (density vs heating sources). | F: Supernova remnants and massive star-forming regions are the primary sources driving cosmic ray enhancement in the CMZ. | **supported**

## Reasoning

- Why this data: ALCHEMI covers multiple rotational transitions (J=1-0 through 4-3) of both HCN and HNC at matching high spatial resolution (1.6 arcsec, ~27 pc) capable of resolving GMC scales across the entire CMZ.  
  > "ALCHEMI allows for the study of GMC-scale structures (~50 pc) located in NGC 253's CMZ due to its sensitivity to physical size scales from 255 pc (15'') to 28 pc (1.''6)." (1 Introduction)
- Why this method: Coupled gas-grain chemical networks (UCLCHEM) and non-LTE radiative transfer (RADEX) within a Bayesian nested sampling framework allow simultaneous exploration of density, temperature, column density, and CRIR without assuming LTE.  
  > "To understand the conditions and associated heating mechanisms within NGC 253's dense gas, we employ Bayesian nested sampling techniques applied to chemical and radiative transfer models which are constrained using our HCN and HNC measurements." (abstract)
- Alternative: Low-CRIR mode (zeta ~ 10 zeta_0) in posterior bimodality was rejected as unphysical because multiple independent ALCHEMI molecular tracers require zeta > 10^3 zeta_0.  
  > "Strong evidence from previous studies based on other sets of molecular lines observed in ALCHEMI (cite: holdship_c2h; harada21; Holdship2022) indicates that the CRIR in the inner GMCs, some of which show bimodality in our models, is >10^3 zeta_0. As such, we dismiss the lower CRIR solution across all GMCs as unphysical" (4.4 Modeling Results)
- Alternative: Infrared vibrational pumping (v2=1) was considered but rejected because measured line ratios were >= 1 across all GMCs.  
  > "Since we do not measure spectral line intensity ratios less than 1 toward the NGC 253 CMZ (Section 3.2), we did not see a justification for including infrared excitation in our radiative transfer model." (4.1 Model Description)
- Alternative: Electron collision excitation was evaluated but deferred as almost all hydrogen is molecular and electron fractions are low.  
  > "we have opted to not consider electron-induced collisions in our analysis, and to defer further analysis of the potential impact of electron collisions in our model to a future analysis." (4.1 Model Description)
- Alternative: Varying reaction temperature barriers (high vs low) for HNC + O and HNC + H was tested but produced no discernible change in parameter estimates.  
  > "We show results using the high temperature barriers (2000 K, 1200 K) for the HNC + O and HNC + H reactions, as we find varying the temperature barrier had no discernible effect on our results." (4.4 Modeling Results)
- How they decided it was enough: _not stated_
- Limitation (authors): Kinetic temperature and molecular hydrogen column density could not be constrained by the HCN and HNC measurements due to chemical insensitivity at high CRIR and degeneracy between T_K and N_H2.  
  > "We find that kinetic temperature and H2 column density are largely not constrained by our HCN and HNC measurements. Nearly all values of kinetic temperature and H2 column density have an equal likelihood of describing our data" (4.4 Modeling Results); "Because there is a clear degeneracy between temperature and column density, which is demonstrated by the negative relationship shown in the N_H2 versus T_K corner plot panels in Figures 10 and 11, the inability to constrain kinetic temperature with our measurements also prevents us from constraining column density." (4.5 The Effect of Cosmic Rays on the HCN/HNC Ratio)
- Limitation (authors): Heating source association was performed only on the plane of the sky without 3D line-of-sight distance components.  
  > "We place heating sources observed using radio continuum (cite: ua97) and vibrationally-excited HC3N emission (cite: RV2020) in each of our 10 GMCs by simply identifying which sources fall within a GMC on the plane of the sky (i.e. no distance component is considered)." (5.1 The Influence of Heating Sources)
- Caveat (inferred, ours): Optical depth effects could potentially distort line ratios, requiring validation using 13C and 15N isotopologue ratios.
- Caveat (inferred, ours): Bimodality in the CRIR posterior distributions needed careful physical justification to rule out the low-CRIR solution branch.

## Reproducibility

- Data public (paper): ALCHEMI project data 2017.1.00161.L and 2018.1.00162.S are publicly available in the ALMA archive.  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00161.L and ADS/JAO.ALMA#2018.1.00162.S." (6 Conclusions)
- Products in archive: _not stated_
- Code: CubeLineMoment repository at https://github.com/keflavich/cube-line-extractor  
  > "In order to extract integrated spectral line intensities from our measurements we use the CubeLineMoment script introduced for this same purpose by (cite: mangum19)." (3.2 Spectral Line Signal Extraction)
- Code: UCLCHEM available at https://uclchem.github.io/  
  > "using the chemical modeling code UCLCHEM (cite: uclchem)" (4.1 Model Description)
- Code: SpectralRadex available at https://spectralradex.readthedocs.io  
  > "and the radiative transfer code SpectralRadex." (4.1 Model Description)
- Code: RADEX available at https://home.strw.leidenuniv.nl/~moldata/radex.html  
  > "SpectralRadex, a python library which includes a wrapper for the RADEX program." (4.1 Model Description)
- Code: UltraNest available at https://johannesbuchner.github.io/UltraNest/  
  > "using the UltraNest package (cite: ultranest21)." (4.3 Nested Sampling)
- Code: UCLPDR available at https://uclchem.github.io/ucl_pdr/  
  > "Photon-Dominated Region (PDR) modeling code UCLPDR which treats heating and cooling." (4.5 The Effect of Cosmic Rays on the HCN/HNC Ratio)
- Missing: Specific scripts or pipeline wrapping UCLCHEM, SpectralRadex, and UltraNest together for the exact Bayesian sampling runs.
- Missing: Specific line-free frequency channel ranges used in continuum subtraction.
- Data volume (inferred): 500 GB - 1 TB
- Score (inferred): 8/5, The observational inputs are fully tabulated (integrated intensities and uncertainties for all 8 transitions across all 10 GMCs) and all modeling software, reaction network additions, and prior ranges are clearly specified with public URLs. Full re-modeling from Table 2 is straightforward.
- Rediscovery candidate: yes, All 80 GMC-averaged integrated line flux measurements are explicitly tabulated with 1-sigma errors, priors for the 4 physical parameters are provided with bounds, and standard open-source codes (UCLCHEM, RADEX/SpectralRadex, UltraNest) can reproduce the main quantitative parameter posteriors and correlations.

## Links

- Method: (cite: ALCHEMI-ACA) (ALCHEMI survey description, observational strategy, data calibration, and imaging products)
- Method: (cite: mangum19) (CubeLineMoment moment extraction methodology and masking workflow)
- Method: (cite: uclchem) (UCLCHEM gas-grain chemical modeling code)
- Method: (cite: radex) (RADEX non-LTE radiative transfer code)
- Method: (cite: ultranest21) (UltraNest Bayesian nested sampling package)
- Companion: (cite: Martin19) (Isotopic abundance ratios in NGC 253 ALCHEMI data)
- Companion: (cite: harada21) (ALCHEMI chemical study of HOC+ and ionization rate in NGC 253)
- Companion: (cite: holdship_c2h) (ALCHEMI study of C2H and cosmic ray ionization rate in NGC 253)
- Companion: (cite: Holdship2022) (ALCHEMI study of H3O+ and SO tracing CRIR and interloper analysis)
- Companion: (cite: Haasler2022) (ALCHEMI companion paper analyzing molecular inventory in NGC 253)
- Companion: (cite: Humire2022) (ALCHEMI companion paper analyzing molecular conditions in NGC 253)
- Related: ALCHEMI

## Checks

```json
{
 "quotes": 103,
 "quotes_ok": 83,
 "quote_pass_rate": 0.806,
 "quotes_too_long": 6,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 97,
  "stated": 65,
  "rate": 0.67
 },
 "evidence_ok": false
}
```
