# Tracing Interstellar Heating: An ALCHEMI Measurement of the HCN Isomers in NGC 253

`2022ApJ...939..119B` | The Astrophysical Journal 2022 | first author: Behrens, Erica | arXiv: 2209.06244 | DOI: 10.3847/1538-4357/ac91ce

Card schema 1.0 | model claude-opus-5-5 | depth full | type large_program_or_survey

## Science

- Fields: nearby_galaxies, astrochemistry
- Question: Can HCN and HNC emission trace heating processes (mechanical vs cosmic-ray) associated with star formation in the NGC 253 CMZ, and what densities and cosmic ray ionization rates characterise its GMCs?  
  > "We analyze HCN and HNC emission in the nearby starburst galaxy NGC 253 to investigate its effectiveness in tracing heating processes associated with star formation." (abstract); "Our work combines ALCHEMI observations with chemical and physical modeling in order to ascertain the mechanisms driving the high kinetic temperatures in the nucleus of NGC 253." (Introduction)
- Target **NGC 253 (CMZ, 10 GMCs)**: coordinates phase center RA(ICRS) 00h47m33.26s, Dec(ICRS) -25d17m17.7s; GMC positions in Table 5  
  > "The nominal phase center of the observations is" (3.1 ALCHEMI Data); "NGC 253 is an ideal target for studying extragalactic star formation" (Introduction); "are derived from the GMC positions reported by (cite: leroy15)" (GMC Positions); z/distance 3.5 +/- 0.2 Mpc  
  > "The nominal phase center of the observations is" (3.1 ALCHEMI Data); "NGC 253 is an ideal target for studying extragalactic star formation" (Introduction); "are derived from the GMC positions reported by (cite: leroy15)" (GMC Positions); distance from (cite: dist_Rekola)  
  > "The nominal phase center of the observations is" (3.1 ALCHEMI Data); "NGC 253 is an ideal target for studying extragalactic star formation" (Introduction); "are derived from the GMC positions reported by (cite: leroy15)" (GMC Positions)

## Data provenance

- ALMA projects: 2017.1.00161.L, 2018.1.00162.S
- bands: Bands 3, 4, 6, 7 (Cycle 5) plus Band 5 (Cycle 6)  
  > "The ALMA Cycle 5 Large Program ALCHEMI (project code 2017.1.00161.L) imaged the CMZ within NGC 253 in the ALMA frequency Bands 3, 4, 6, and 7." (3.1 ALCHEMI Data); "This survey was subsequently extended to Band 5 during ALMA Cycle 6 (project code 2018.1.00162.S)." (3.1 ALCHEMI Data)
- frequencies and spectral setup: rest-frequency coverage 84.2-373.2 GHz; spectral resolution 8-9 km/s  
  > "The rest-frequency coverage of ALCHEMI ranged from 84.2 to 373.2 GHz." (3.1 ALCHEMI Data)
- continuum bandwidth: _not stated_
- arrays: 12 m Array + Atacama Compact Array (ACA), combined  
  > "The combination of the 12 m Array and Atacama Compact Array (ACA) measurements used in this analysis resulted in a common maximum recoverable angular scale of" (3.1 ALCHEMI Data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.6 arcsec (~27 pc)  
  > "mosaics of the central molecular zone of NGC 253 in the HCN and HNC" (3.1 ALCHEMI Data)
- max recoverable scale: 15 arcsec at all frequencies  
  > "The combination of the 12 m Array and Atacama Compact Array (ACA) measurements used in this analysis resulted in a common maximum recoverable angular scale of" (3.1 ALCHEMI Data)
- sensitivity: channel RMS (mJy/beam) HCN/HNC: 1-0 0.27/0.26; 2-1 6.41/12.52; 3-2 1.46/1.98; 4-3 2.70/3.47  
  > "0.27, 0.26" (Table 1); "6.41, 12.52" (Table 1)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: ALCHEMI Large Program mosaics extracted from the ALCHEMI archive  
  > "From the ALCHEMI archive we extract the" (3.1 ALCHEMI Data)
- Line: HCN 1-0 (88.632 GHz)
- Line: HNC 1-0 (90.664 GHz)
- Line: HCN 2-1 (177.261 GHz)
- Line: HNC 2-1 (181.325 GHz)
- Line: HCN 3-2 (265.886 GHz)
- Line: HNC 3-2 (271.981 GHz)
- Line: HCN 4-3 (354.505 GHz)
- Line: HNC 4-3 (362.630 GHz)
- Line: H2CO 5_05-4_04 (interloper) (362.736048 GHz)
- Line: HNC 4-3 v2=1 (interloper) (362.554351 GHz)
- External data: Positions of 10 GMCs in the CMZ (with corrected reference position and GMC 5 shifted 0.5 arcsec, via private communication)  
  > "we average the integrated intensity emission inside each of the 10 GMC-like structures identified by (cite: leroy15)." (3.2 Spectral Line Signal Extraction); "GMC 5 has been shifted down in declination by 0.5 arcsec relative to that reported in (cite: leroy15)." (GMC Positions) [from (cite: leroy15)]
- External data: Compact radio continuum sources and spectral indices (SNRs, HII regions) used as heating sources  
  > "We place heating sources observed using radio continuum (cite: ua97) and vibrationally-excited HC$_{3}$N emission (cite: RV2020) in each of our 10 GMCs" (5.1 The Influence of Heating Sources) [from (cite: ua97)]
- External data: Super hot cores identified with vibrationally-excited HC3N (only GMCs 3-6 sampled)  
  > "We place heating sources observed using radio continuum (cite: ua97) and vibrationally-excited HC$_{3}$N emission (cite: RV2020) in each of our 10 GMCs" (5.1 The Influence of Heating Sources) [from (cite: RV2020)]
- External data: Kinetic temperatures and N_H2 from dust continuum used to set T and N_H2 priors  
  > "This kinetic temperature prior is based on the results of the (cite: mangum19) kinetic temperature measurements toward the NGC 253 CMZ." (4.2 Defining Bayesian Priors) [from (cite: mangum19)]
- External data: Previous CRIR estimates used to set the CRIR prior upper limit and to reject low-CRIR mode  
  > "We adopt this upper limit by taking into consideration estimates made by (cite: holdship_c2h) and (cite: harada21)" (4.2 Defining Bayesian Priors) [from (cite: holdship_c2h); (cite: harada21); (cite: Holdship2022)]
- External data: HCN/H13CN and HCN/HC15N integrated intensity isotopic ratios for optical-depth check  
  > "we use integrated intensity isotopic ratios for HCN/H$^{13}$CN and HCN/HC$^{15}$N (cite: Martin19)" (4.4 Modeling Results) [from (cite: Martin19)]
- External data: UMIST12 gas-phase network and depleted initial abundances (Table 4 of Jenkins 2009)  
  > "We take our gas phase network from UMIST12 (cite: McElroy2013)" (4.1 Model Description); "use depleted abundances from Table 4 of (cite: jenkins2009) for our initial conditions" (4.1 Model Description) [from (cite: McElroy2013); (cite: jenkins2009)]
- External data: HNC + O reaction and high/low temperature barrier values  
  > "which has been shown to be important in the chemistry of HCN and HNC (cite: hacar20)" (4.1 Model Description) [from (cite: hacar20)]
- External data: NGC 253 supernova rate 0.14-0.3 /yr  
  > "The supernova rate for NGC 253 has been estimated to be in the range 0.14 to 0.3 yr$^{-1}$ (cite: Lenc2006AJ; ua97)" (5.2 The Connection Between CRIR and Supernovae) [from (cite: Lenc2006AJ; ua97)]
- External data: Milky Way CRIR upper limit vs supernova energetics used to scale CRIR to supernova rate  
  > "based on a general consideration of energies released in supernovae, (cite: Spitzer1968) estimated that the probable upper limit" (5.2 The Connection Between CRIR and Supernovae) [from (cite: Spitzer1968); (cite: Dalgarno2006)]
- Simulation/model as data: Meijerink et al. 2011 model HCN/HNC ratios vs mechanical heating used for comparison (Figure 2)  
  > "(cite: meijerink11) also find that mechanical heating that would raise the kinetic temperature to such values could increase the HCN/HNC abundance ratio by up to two orders of magnitude" (HCN and HNC in Galaxies)

## Processing

### Calibration

- pipeline or manual: Calibration and imaging done by ALCHEMI as described in Martin et al. 2021 (ALCHEMI-ACA); not redone here  
  > "Full details regarding the data acquisition, calibration, and imaging are provided in (cite: ALCHEMI-ACA)." (3.1 ALCHEMI Data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: ALCHEMI archive mosaics used  
  > "From the ALCHEMI archive we extract the" (3.1 ALCHEMI Data)
- flux calibrator: _not stated_
- flux scale uncertainty: absolute flux calibration uncertainties from ALCHEMI-ACA (value not given)  
  > "Uncertainties are calculated taking into account spectral channel RMS values, line widths, and absolute flux calibration uncertainties (cite: ALCHEMI-ACA)" (3.2 Spectral Line Signal Extraction)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: CubeLineMoment spectral and spatial masks; each line used as its own tracer; 3x channel RMS signal limit  
  > "`CubeLineMoment` uses a series of spectral and spatial masks to extract integrated intensities for a defined list of target spectral frequencies." (3.2 Spectral Line Signal Extraction); "As the HCN and HNC emission measured toward NGC 253 is quite intense in all transitions we were able to use each as its own tracer." (3.2 Spectral Line Signal Extraction)
- multiscale scales: _not stated_
- continuum subtraction: as described in ALCHEMI-ACA  
  > "The continuum subtraction and imaging processes used in this analysis are described in (cite: ALCHEMI-ACA)." (3.1 ALCHEMI Data)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12 m + ACA combined  
  > "The combination of the 12 m Array and Atacama Compact Array (ACA) measurements used in this analysis resulted in a common maximum recoverable angular scale of" (3.1 ALCHEMI Data)
- smoothing: _not stated_
- final beam: 1.6 arcsec circular (theta_max = theta_min = 1.6 arcsec)  
  > "are the FWHMs of the major and minor axes of our Gaussian beam" (4.3 Nested Sampling)
- final rms: per Table 1 channel RMS (0.26-12.52 mJy/beam)  
  > "2.70, 3.47" (Table 1)

### Inherited from earlier work

- Data acquisition, calibration, imaging and continuum subtraction  
  > "Full details regarding the data acquisition, calibration, and imaging are provided in (cite: ALCHEMI-ACA)." (3.1 ALCHEMI Data) [from (cite: ALCHEMI-ACA)]
- CubeLineMoment moment-extraction procedure  
  > "we use the `CubeLineMoment` script introduced for this same purpose by (cite: mangum19)." (3.2 Spectral Line Signal Extraction) [from (cite: mangum19)]
- Absolute flux calibration uncertainties  
  > "Uncertainties are calculated taking into account spectral channel RMS values, line widths, and absolute flux calibration uncertainties (cite: ALCHEMI-ACA)" (3.2 Spectral Line Signal Extraction) [from (cite: ALCHEMI-ACA)]
- Interloper contamination estimation procedure  
  > "Using the procedure described in (cite: Holdship2022) we determine that these two interlopers contribute respectively at most 4% and 1% to the HNC" (3.3 Interloper Analysis) [from (cite: Holdship2022)]
- GMC definition and positions  
  > "Using this definition, (cite: leroy15) identify 10 GMCs in the NGC 253 CMZ" (3.2 Spectral Line Signal Extraction) [from (cite: leroy15)]
- Spearman Monte Carlo procedure reused for heating-source correlations  
  > "Following the procedure we outlined in Section [4.4](#sec:mod_res)" (5.1 The Influence of Heating Sources) [from Section 4.4 (this paper); footnote URL jonathan-liu.com correlation analysis]

### Not stated but needed to reproduce (our reading)

- Exact CubeLineMoment configuration (spectral mask widths, tracer velocity windows) beyond 3-sigma limit
- Numerical values of absolute flux calibration uncertainty per band
- UCLCHEM version, model evolution time / which time step abundances are taken at, grain parameters, freeze-out/desorption settings
- SpectralRadex/RADEX collisional data files (LAMDA versions), background temperature
- UltraNest number of live points and other run settings beyond frac_remainder 0.01
- How the bimodal posterior was split into high- and low-CRIR modes quantitatively
- UCLPDR inputs beyond n, CRIR and A_V~10 (UV field, metallicity)
- List of heating sources assigned per GMC (counts in Figure 8 only)
- Treatment of upper limits in the Spearman Monte Carlo simulation

## Analysis recipe

1. **make moment maps of HCN/HNC lines**: CubeLineMoment spectral/spatial masking, each line as its own tracer; moment 0, 1, 2 with 3x channel RMS signal limit  
  > "As the HCN and HNC emission measured toward NGC 253 is quite intense in all transitions we were able to use each as its own tracer." (3.2 Spectral Line Signal Extraction)
   - software: CubeLineMoment
   - parameter: signal limit 3 x spectral channel baseline RMS  
  > "images are generated using a signal limit of three-times the spectral channel baseline RMS for the respective transition under study" (3.2 Spectral Line Signal Extraction)
   - fitting: _not stated_
   - validation: _not stated_
2. **GMC-averaged integrated intensities**: average integrated intensity in 10 GMC apertures with diameter equal to beam (1.6 arcsec)  
  > "We extract HCN and HNC integrated intensities for each of the four transitions and average each of them over these GMCs, adopting diameters equal to our beam size" (3.2 Spectral Line Signal Extraction)
   - parameter: aperture diameter 1.6 arcsec at Leroy+15 GMC positions (Table 5)  
  > "adopting diameters equal to our beam size" (3.2 Spectral Line Signal Extraction)
   - assumption: emission smooth enough that not centering on peaks does not matter  
  > "we find that the emission is smooth enough that any potential offset between the centers of the two species’ emission would not substantially affect our calculated integrated intensities" (3.2 Spectral Line Signal Extraction)
   - fitting: _not stated_
   - validation: _not stated_
3. **assess line blending**: sample-spectrum check; contamination of HNC 4-3 by H2CO and HNC v2=1 estimated, not corrected  
  > "Since the estimated correction required to this single transition is small, we do not apply these corrections to our presented integrated intensities." (3.3 Interloper Analysis)
   - software: CubeLineMoment
   - fitting: _not stated_
   - validation: consistent with multi-species LTE analysis of ALCHEMI-ACA  
  > "This contamination estimate is consistent with the multi-species LTE analysis of molecular column densities described in (cite: ALCHEMI-ACA)." (3.3 Interloper Analysis)
4. **forward chemical + radiative transfer model**: UCLCHEM single-point gas-grain model gives abundances; column = abundance x N_H2 (on-the-spot); SpectralRadex/RADEX gives integrated intensities  
  > "We use a single point model to replicate the environment in the GMCs by assuming these gas clouds are homogeneous" (4.1 Model Description); "Given `UCLCHEM` chemical abundances and user-defined temperature, density, and H$_{2}$ column density values, we can use `RADEX` to connect chemical abundances to integrated intensities" (4.1 Model Description)
   - software: UCLCHEM, SpectralRadex, RADEX
   - parameter: zeta_0 = 1.36e-17 s^-1 base CRIR  
  > "from which the cosmic ray ionization rates are scaled" (4.1 Model Description)
   - parameter: barriers for HNC+O and HNC+H tested high (2000 K, 1200 K) and low (20 K, 200 K); high reported  
  > "as we find varying the temperature barrier had no discernible effect on our results" (4.4 Modeling Results)
   - assumption: uniform line width 100 km/s and beam-filling factor 1  
  > "and a beam-filling factor of 1" (4.1 Model Description)
   - assumption: only H2 collisional excitation; electron collisions ignored  
  > "we only consider excitation through collisions with H$_{2}$ and therefore ignore electron collisions" (4.1 Model Description)
   - assumption: no infrared pumping  
  > "we did not see a justification for including infrared excitation in our radiative transfer model" (4.1 Model Description)
   - assumption: clouds UV-shielded, homogeneous  
  > "they have high enough visual extinctions such that they are shielded from UV radiation (cite: harada21)" (4.1 Model Description)
   - fitting: _not stated_
   - validation: _not stated_
5. **infer T, n, CRIR, N_H2 per GMC**: nested sampling (MLFriends, UltraNest) with Gaussian likelihood on 8 integrated intensities converted Jy km/s to K km/s  
  > "We sample our parameter space to obtain input for our chemical models using nested sampling techniques by implementing the Monte Carlo algorithm MLFriends" (4.3 Nested Sampling)
   - software: UltraNest, MLFriends, UCLCHEM, SpectralRadex
   - parameter: priors: T 50-300 K uniform; n 1e3-1e7 cm^-3 log-uniform; zeta 10-1e7 zeta_0 log-uniform; N_H2 1e22-1e25 cm^-2 log-uniform  
  > "50–300 K" (Table 3); "We adopt a log-uniform distribution for densities over the range" (4.2 Defining Bayesian Priors)
   - parameter: stopping: fractional remainder <= 0.01  
  > "These iterations continue until the live point weights are insignificant (fractional remainder $\leq$ 0.01)" (4.3 Nested Sampling)
   - assumption: Gaussian errors  
  > "We can determine $P(\mathbf{F_{d}}|\boldsymbol\theta)$ by assuming Gaussian errors" (4.3 Nested Sampling)
   - assumption: low-CRIR posterior mode dismissed as unphysical based on prior ALCHEMI studies  
  > "As such, we dismiss the lower CRIR solution across all GMCs as unphysical and only present the high CRIR solutions." (4.4 Modeling Results)
   - fitting: medians with inner 67% intervals; 83rd percentile upper limits when posterior peaks at lower prior edge  
  > "In cases where the posterior distributions peak at the lower end of our parameter space, we instead report the 83rd percentile of the distribution as an upper limit" (4.4 Modeling Results)
   - validation: observed vs modeled fluxes compared (Figure 9); n-zeta degeneracy argued not driving trend  
  > "Thus we believe the behavior demonstrated in Figure [8](#fig:samp_results) is a physical solution rather than resulting from a degeneracy." (4.4 Modeling Results)
6. **check optical depths**: RADEX optical depths over all sampled iterations; isotopologue ratios compared to observed HCN/H13CN and HCN/HC15N  
  > "We model the optical depth for all iterations of our `UltraNest` sampling algorithm and analyze the middle 67% of the resulting distribution." (4.4 Modeling Results)
   - software: RADEX, UltraNest
   - fitting: _not stated_
   - validation: modeled optical depth ratios consistent with observed isotope ratios  
  > "We found that the ratios of modeled optical depths are consistent with the observationally-derived isotope ratios themselves" (4.4 Modeling Results)
7. **correlate CRIR with HCN/HNC abundance ratio**: Spearman rho via scipy spearmanr on 10,000 Monte Carlo Gaussian resamplings of 10 GMC values  
  > "to create simulated Gaussian datasets for these parameters consisting of 10,000 sets of 10 data points each (1 point for each GMC)" (4.4 Modeling Results)
   - software: SciPy
   - parameter: 10,000 simulated sets  
  > "consisting of 10,000 sets of 10 data points each" (4.4 Modeling Results)
   - fitting: _not stated_
   - validation: _not stated_
8. **estimate cosmic-ray heating temperature**: UCLPDR gas temperature for fitted n and CRIR at A_V ~ 10, compared with observed T_K  
  > "we estimate the heating that would result from these CRIRs via the Photon-Dominated Region (PDR) modeling code `UCLPDR`" (4.5 The Effect of Cosmic Rays on the HCN/HNC Ratio)
   - software: UCLPDR
   - parameter: A_V ~ 10  
  > "in this case in order to model the inner, UV-shielded part of the cloud" (4.5 The Effect of Cosmic Rays on the HCN/HNC Ratio)
   - assumption: deficit between PDR and observed T would be mechanical heating  
  > "We can assume that if these PDR-derived temperatures were lower than those calculated from observations, the additional heating needed to equate the temperatures would be from mechanical heating." (4.5 The Effect of Cosmic Rays on the HCN/HNC Ratio)
   - fitting: _not stated_
   - validation: compared with Mangum+19 kinetic temperatures  
  > "the high kinetic temperatures from our PDR modeling agree with those derived by (cite: mangum19)" (4.5 The Effect of Cosmic Rays on the HCN/HNC Ratio)
9. **relate n, CRIR to heating sources and supernova rate**: count radio sources and SHCs within each GMC on the sky; Spearman MC; scale CRIR to SN rate via Spitzer & Tomasko limit  
  > "by simply identifying which sources fall within a GMC on the plane of the sky (i.e. no distance component is considered)" (5.1 The Influence of Heating Sources)
   - software: SciPy
   - assumption: zeta_MW 1.2e-15 s^-1 corresponds to SN rate 0.01 /yr  
  > "corresponds roughly to a supernova rate of 0.01 yr$^{-1}$" (5.2 The Connection Between CRIR and Supernovae)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CubeLineMoment** : masked moment map / integrated intensity extraction  
  > "`CubeLineMoment` uses a series of spectral and spatial masks to extract integrated intensities for a defined list of target spectral frequencies." (3.2 Spectral Line Signal Extraction)
- **UCLCHEM** : gas-grain chemical modeling  
  > "`UCLCHEM` is a gas-grain chemical modeling code that incorporates user-defined chemical networks" (4.1 Model Description)
- **SpectralRadex** : python wrapper for RADEX radiative transfer  
  > "we use `SpectralRadex`, a python library which includes a wrapper for the `RADEX`" (4.1 Model Description)
- **RADEX** : non-LTE escape-probability radiative transfer and optical depths  
  > "Optical depth effects are treated within `RADEX` using an escape probability method." (4.1 Model Description)
- **UltraNest (MLFriends)** : nested sampling of posterior  
  > "using the `UltraNest` package (cite: ultranest21)" (4.3 Nested Sampling)
- **SciPy (spearmanr)** : Spearman correlation coefficients  
  > "by employing the `SciPy` (cite: scipy2020) function `spearmanr`" (4.4 Modeling Results)
- **UCLPDR** : PDR heating/cooling gas temperature estimates  
  > "`UCLPDR` provides an estimated gas temperature given input volume densities and CRIRs" (4.5 The Effect of Cosmic Rays on the HCN/HNC Ratio)
- **CASA** : listed in Software section (use not specified)  
  > "CASA (cite: casa)" (Software)
- **Astropy** : listed in Software section (use not specified)  
  > "`Astropy` (cite: Astropy2013)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HCN/HNC integrated intensity ratio range (all transitions) | 1 to 5 | not stated | dimensionless | 2 | the HCN/HNC integrated intensity ratio for all four transitions ranges from 1 to 5 |
| HCN 1-0 integrated intensity, GMC 4 | 13.27 | 0.57 (1 sigma) | Jy km/s | 2 | 13.27(1.99) |
| Max interloper contribution to HNC 4-3 (H2CO, HNC v2=1) | 4% and 1% | not stated | percent | 3 | these two interlopers contribute respectively at most 4% and 1% to the HNC |
| log10 n, GMC 5 | 5.62 | +0.31/-0.34 | log cm^-3 | 5 | 5.62^{+0.31}_{-0.34} |
| log10 zeta, GMC 5 | 5.09 | +0.39/-0.50 | log zeta_0 | 5 | 5.09^{+0.39}_{-0.50} |
| log10 n, GMC 1 | 3.81 | +0.90/-0.48 | log cm^-3 | 5 | 3.81^{+0.90}_{-0.48} |
| log10 zeta, GMC 1 | 3.87 | +0.15/-0.22 | log zeta_0 | 5 | 3.87^{+0.15}_{-0.22} |
| HCN/HNC abundance ratio | <10 | not stated | dimensionless | 5 | The HCN/HNC abundance ratios are low (<10) in the NGC 253 CMZ. |
| Spearman rho CRIR vs HCN/HNC abundance ratio | -0.47 | 0.26 | dimensionless | 7 | the median \rho value is -0.47\pm0.26 |
| PDR gas temperature, inner (4-6) / outer GMCs | ~200-500 / ~100-400 | not stated | K | 8 | result in PDR gas temperatures of \sim200-500 K, whereas the conditions in the outer GMCs correspond to temperatures of \sim100-400 K |
| Spearman rho CRIR-heating sources / density-heating sources | 0.67 / 0.60 | std 0.21 / 0.17 | dimensionless | 9 | the median \rho values for the CRIR-heating source and density-heating source relationships are 0.67 and 0.60 respectively, with standard deviations of 0.21 and 0.17 |
| CRIR upper limit implied by SN rate 0.3/yr | ~3000 | not stated | zeta_0 | 9 | an upper limit to the supernova rate of 0.3 yr^{-1} would imply an upper limit to the CRIR of \sim 3000 \zeta_0 |

## Qualitative findings

- Kinetic temperature and N_H2 are largely unconstrained; n and CRIR are constrained  
  > "We find that kinetic temperature and H$_{2}$ column density are largely not constrained by our HCN and HNC measurements." (4.4 Modeling Results)
- At high CRIR HCN and HNC both form via HCNH+ recombination at identical rates, decoupling the ratio from temperature  
  > "As a result, at high CRIRs, HCN and HNC chemistry is dominated by cosmic rays rather than kinetic temperature." (4.5 The Effect of Cosmic Rays on the HCN/HNC Ratio)
- Temperature barrier choice for isomerization has no discernible effect  
  > "as we find varying the temperature barrier had no discernible effect on our results" (4.4 Modeling Results)
- Optical depths do not inhibit modeling  
  > "Thus, we conclude that optical depth issues do not inhibit the use of our observed integrated intensities in constraining our models." (4.4 Modeling Results)

## Claim tuples

- H: HCN/HNC ratio traces strong mechanical heating in the NGC 253 CMZ | E: Measure GMC-averaged HCN/HNC intensities and model with UCLCHEM+RADEX; compare with Meijerink+11 predictions; UCLPDR heating | R: Ratios 1-5, abundance ratios <10, far below ~50 expected for significant mechanical heating; CR heating reproduces high T | F: Cosmic ray heating dominates; mechanical heating not significant for HCN/HNC chemistry | **supported**
- H: Density and CRIR vary across the CMZ | E: Bayesian nested-sampling fits per GMC | R: Central GMCs n ~10^5.5 cm^-3, zeta ~10^-12 s^-1 vs outer ~10^4 and ~10^-13 | F: n and CRIR enhanced by ~an order of magnitude in central GMCs | **supported**
- H: HCN/HNC ratio depends on CRIR | E: Monte Carlo Spearman correlation of modeled abundance ratio vs CRIR | R: rho = -0.47 +/- 0.26 | F: Moderate anti-correlation: lower ratio where CRIR higher | **supported**
- H: Star-formation heating sources drive density and CRIR | E: Count radio sources/SHCs per GMC; Spearman correlations; SN-rate scaling of CRIR | R: rho 0.67 (CRIR) and 0.60 (density); SN-implied CRIR limit ~3000 zeta_0 at low end of measured range | F: Positive correlations with heating sources; quantitative connection between supernovae and CRIR suggested | **partially**

## Reasoning

- Why this data: HCN/HNC isomer ratio proposed as mechanical heating/temperature probe; bright, multiple transitions available in ALCHEMI  
  > "Additionally, HCN and HNC transitions are relatively bright in an extragalactic context and thus easy to detect." (HCN and HNC in Galaxies)
- Why this method: Treat cosmic ray ionization and heating separately to disentangle effects  
  > "we treat cosmic rays and heating separately in our models" (HCN and HNC in Galaxies)
- Alternative: Infrared pumping excitation not included since no ratios <1 observed  
  > "we did not see a justification for including infrared excitation in our radiative transfer model" (4.1 Model Description)
- Alternative: Low-CRIR posterior mode rejected as unphysical  
  > "we dismiss the lower CRIR solution across all GMCs as unphysical and only present the high CRIR solutions" (4.4 Modeling Results)
- Alternative: Low vs high isomerization barriers tested; no effect  
  > "The most likely parameters found using each of the two temperature barriers were well within the error bars of the opposing model’s parameter estimates." (4.4 Modeling Results)
- Alternative: n-zeta degeneracy considered as explanation of gradient and rejected  
  > "One explanation for this increase in volume density and CRIR could be a degeneracy between these two quantities." (4.4 Modeling Results)
- How they decided it was enough: Nested sampling stops at fractional remainder <= 0.01  
  > "indicating the vast majority of the probability density has been sampled" (4.3 Nested Sampling)
- Limitation (authors): Electron collisions ignored though possibly important in lower-density regions  
  > "Even though electron-induced collisions could be important in the lower-density regions within the NGC 253 CMZ, we have opted to not consider electron-induced collisions in our analysis" (4.1 Model Description)
- Limitation (authors): Dilution from averaging over GMC positions may underestimate intensities  
  > "Any remaining dilution of the HCN and HNC emission when averaging over the chosen GMC positions will underestimate the intensity of that emission." (3.2 Spectral Line Signal Extraction)
- Limitation (authors): T and N_H2 degenerate and unconstrained  
  > "the inability to constrain kinetic temperature with our measurements also prevents us from constraining column density" (4.5 The Effect of Cosmic Rays on the HCN/HNC Ratio)
- Limitation (authors): Super hot core census covers only GMCs 3-6; heating-source assignment ignores line-of-sight distance  
  > "(i.e. no distance component is considered)" (5.1 The Influence of Heating Sources)
- Caveat (inferred, ours): Rejecting the low-CRIR mode relies on external priors, making CRIR results partly prior-driven
- Caveat (inferred, ours): Fixed 100 km/s line width and unity filling factor for all GMCs at 27 pc beam may bias n/N_H2
- Caveat (inferred, ours): Correlations use only 10 points with large uncertainties and several upper limits
- Caveat (inferred, ours): Single-point steady chemistry ignores time dependence and structure along line of sight

## Reproducibility

- Data public (paper): ALCHEMI mosaics extracted from the ALCHEMI archive; ALMA project codes given  
  > "From the ALCHEMI archive we extract the" (3.1 ALCHEMI Data)
- Products in archive: _not stated_
- Code: No new code released; uses public CubeLineMoment, UCLCHEM, SpectralRadex, UltraNest (URLs in footnotes)  
  > "we use the `CubeLineMoment` script introduced for this same purpose by (cite: mangum19)" (3.2 Spectral Line Signal Extraction)
- Missing: UCLCHEM run configuration (time, grain/surface settings, version)
- Missing: RADEX collisional data files and background temperature
- Missing: UltraNest live points
- Missing: Flux calibration uncertainty values
- Missing: Heating source counts per GMC
- Missing: Exact CubeLineMoment masks
- Data volume (inferred): Only 8 line cubes (~1.6 arcsec mosaics) from the ALCHEMI release are needed, a few GB at most; the full ALCHEMI raw data are far larger.
- Score (inferred): 6/5, Data public and the observable extraction plus priors and likelihood are clear, but chemical-model settings, RADEX inputs and the sampler configuration are incomplete, and the results depend on model details.
- Rediscovery candidate: yes, ALCHEMI data are public and the paper gives GMC positions, intensities, priors and likelihood. The main results (per-GMC n, CRIR, Spearman rho) are numeric, though exact reproduction depends on unstated UCLCHEM settings.

## Links

- Method: (cite: ALCHEMI-ACA) (ALCHEMI data acquisition, calibration, imaging, continuum subtraction, flux uncertainties)
- Method: (cite: mangum19) (CubeLineMoment method; temperature and N_H2 priors)
- Method: (cite: uclchem) (UCLCHEM chemical code)
- Method: (cite: radex) (RADEX radiative transfer)
- Method: (cite: ultranest14; ultranest19; ultranest21) (MLFriends/UltraNest nested sampling)
- Method: (cite: Holdship2022) (interloper procedure and electron fractions)
- Companion: (cite: holdship_c2h) (ALCHEMI C2H CRIR study)
- Companion: (cite: harada21) (ALCHEMI HOC+ CRIR and density study)
- Companion: (cite: Holdship2022) (ALCHEMI H3O+/SO CRIR study)
- Companion: (cite: Haasler2022); (cite: Humire2022) (other ALCHEMI series papers)
- Related: ALCHEMI (ALMA Comprehensive High Resolution Molecular Inventory)

## Checks

```json
{
 "quotes": 140,
 "quotes_ok": 140,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 126,
  "stated": 93,
  "rate": 0.738
 },
 "evidence_ok": true
}
```
