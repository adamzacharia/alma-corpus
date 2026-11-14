# Tracing Interstellar Heating: An ALCHEMI Measurement of the HCN Isomers in NGC 253

`2022ApJ...939..119B` | The Astrophysical Journal 2022 | first author: Behrens, Erica | arXiv: 2209.06244 | DOI: 10.3847/1538-4357/ac91ce

Card schema 1.0 | model claude-haiku-5-5 | depth full | type archival_reuse

## Science

- Fields: astrochemistry, nearby_galaxies, star_formation
- Question: Whether HCN and HNC emission, modeled with chemistry and radiative transfer, can trace heating processes (mechanical vs cosmic ray) associated with star formation in the NGC 253 CMZ  
  > "We analyze HCN and HNC emission in the nearby starburst galaxy NGC 253 to investigate its effectiveness in tracing heating processes associated with star formation." (abstract)
- Target **NGC 253 (CMZ, GMCs 1-10)**: coordinates nominal phase center 00h47m33s.26, -25°17'17''.7 (ICRS)  
  > "The nominal phase center of the observations is" (Observational Data); "and at a distance of 3.5±0.2 Mpc (cite: dist_Rekola)" (Introduction); z/distance 3.5±0.2 Mpc  
  > "The nominal phase center of the observations is" (Observational Data); "and at a distance of 3.5±0.2 Mpc (cite: dist_Rekola)" (Introduction); distance from Rekola et al. 2005 (cite: dist_Rekola), as stated in Introduction  
  > "The nominal phase center of the observations is" (Observational Data); "and at a distance of 3.5±0.2 Mpc (cite: dist_Rekola)" (Introduction)

## Data provenance

- ALMA projects: 2017.1.00161.L, 2018.1.00162.S
- bands: ALMA Bands 3, 4, 5, 6, 7 (Band 5 added in Cycle 6)  
  > "imaged the CMZ within NGC 253 in the ALMA frequency Bands 3, 4, 6, and 7." (ALCHEMI Data); "This survey was subsequently extended to Band 5 during ALMA Cycle 6" (ALCHEMI Data)
- frequencies and spectral setup: rest-frequency coverage 84.2 to 373.2 GHz  
  > "The rest-frequency coverage of ALCHEMI ranged from 84.2 to 373.2 GHz." (ALCHEMI Data)
- continuum bandwidth: _not stated_
- arrays: 12 m Array combined with Atacama Compact Array (ACA)  
  > "The combination of the 12 m Array and Atacama Compact Array (ACA) measurements used in this analysis" (ALCHEMI Data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.6 arcsec (~27 pc) final image cube resolution; 8-9 km/s spectral resolution  
  > "The final angular and spectral resolution of the image cubes generated from these measurements were" (ALCHEMI Data)
- max recoverable scale: 15 arcsec common maximum recoverable scale at all frequencies  
  > "resulted in a common maximum recoverable angular scale of" (ALCHEMI Data)
- sensitivity: per-transition spectral channel RMS 0.26-12.52 mJy/beam (Table 1)  
  > "Table 1 lists the transitions, frequencies, and spectral channel RMS values for all measurements studied." (Table 1)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: archival: ALCHEMI survey data extracted from the ALCHEMI archive  
  > "From the ALCHEMI archive we extract the" (ALCHEMI Data)
- Line: HCN J=1-0 (88.632 GHz)
- Line: HNC J=1-0 (90.664 GHz)
- Line: HCN J=2-1 (177.261 GHz)
- Line: HNC J=2-1 (181.325 GHz)
- Line: HCN J=3-2 (265.886 GHz)
- Line: HNC J=3-2 (271.981 GHz)
- Line: HCN J=4-3 (354.505 GHz)
- Line: HNC J=4-3 (362.630 GHz)
- External data: GMC positions (10 GMCs) adopted from leroy15, with two corrections from private communication  
  > "The GMC positions we have adopted in this analysis (Table 5) are derived from the GMC positions reported by (cite: leroy15)" (GMC Positions) [from (cite: leroy15)]
- External data: kinetic temperature constraints: about 50 K on ~5 arcsec scales and at least 300 K on ≲1 arcsec scales (used as temperature prior)  
  > "On the largest angular scales" (Defining Bayesian Priors) [from (cite: mangum19)]
- External data: H2 column density range 10^23 to 7x10^24 cm^-2 for GMCs 3-7 (used for N(H2) prior)  
  > "Millimeter dust continuum measurements over similar spatial scales as those modelled here were used to derive" (Defining Bayesian Priors) [from (cite: mangum19)]
- External data: radio continuum sources and spectral indices, used to place heating sources and estimate SN fraction  
  > "We place heating sources observed using radio continuum (cite: ua97)" (Discussion) [from (cite: ua97)]
- External data: super hot core identifications from vibrationally-excited HC3N emission  
  > "identified by (cite: RV2020) using vibrationally-excited HC$_{3}$N emission." (Introduction) [from (cite: RV2020)]
- External data: isotopic ratios HCN/H13CN and HCN/HC15N used to check modeled optical depths  
  > "To confirm these optical depth estimates, we use integrated intensity isotopic ratios" (Modeling Results) [from (cite: Martin19)]
- External data: C2H, HOC+, H3O+/SO CRIR estimates (10^3-10^6 zeta0 and related values) used for prior and comparison  
  > "which derive $\zeta$ ranges from" (Defining Bayesian Priors) [from (cite: holdship_c2h); (cite: harada21); (cite: Holdship2022)]
- External data: Milky Way CRIR lower limit and local interstellar ionization estimate from Voyager/Pioneer data  
  > "The energy density derived from this analysis is" (The Connection Between CRIR and Supernovae) [from (cite: Webber1998)]
- External data: NGC 253 supernova rate range 0.14 to 0.3 per yr  
  > "The supernova rate for NGC 253 has been estimated to be in the range 0.14 to 0.3" (The Connection Between CRIR and Supernovae) [from (cite: Lenc2006AJ); (cite: ua97)]
- Simulation/model as data: UCLCHEM gas-grain chemistry coupled to SpectralRadex/RADEX non-LTE line modeling, sampled per GMC over T, n, zeta, N(H2) priors  
  > "We model the chemical and physical conditions within each of the 10 GMCs using the chemical modeling code" (Model Description)

## Processing

### Calibration

- pipeline or manual: not described in this paper; deferred to ALCHEMI-ACA  
  > "Full details regarding the data acquisition, calibration, and imaging are provided in (cite: ALCHEMI-ACA)." (ALCHEMI Data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: absolute flux calibration uncertainties taken from ALCHEMI-ACA and propagated into integrated intensity errors  
  > "absolute flux calibration uncertainties (cite: ALCHEMI-ACA)" (Spectral Line Signal Extraction)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: CubeLineMoment spectral and spatial masks; signal limit of three times the spectral channel baseline RMS for moment 0-2 images; each transition used as its own tracer  
  > "using a signal limit of three-times the spectral channel baseline RMS for the respective transition under study." (Spectral Line Signal Extraction); "we were able to use each as its own tracer." (Spectral Line Signal Extraction)
- multiscale scales: _not stated_
- continuum subtraction: described in ALCHEMI-ACA; not detailed here  
  > "The continuum subtraction and imaging processes used in this analysis are described in (cite: ALCHEMI-ACA)." (ALCHEMI Data)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.6 arcsec (~27 pc)  
  > "The final angular and spectral resolution of the image cubes generated from these measurements were" (ALCHEMI Data)
- final rms: per-transition channel RMS 0.27, 0.26 (1-0); 6.41, 12.52 (2-1); 1.46, 1.98 (3-2); 2.70, 3.47 (4-3) mJy/beam  
  > "Table 1 lists the transitions, frequencies, and spectral channel RMS values for all measurements studied." (Table 1)

### Inherited from earlier work

- calibration, imaging and continuum subtraction of the ALCHEMI cubes  
  > "Full details regarding the data acquisition, calibration, and imaging are provided in (cite: ALCHEMI-ACA)." (ALCHEMI Data) [from (cite: ALCHEMI-ACA)]
- CubeLineMoment integrated-intensity extraction method and masking approach  
  > "we use the CubeLineMoment script introduced for this same purpose by (cite: mangum19)" (Spectral Line Signal Extraction) [from (cite: mangum19)]
- interloper contribution procedure for HNC 4-3  
  > "Using the procedure described in (cite: Holdship2022) we determine" (Interloper Analysis) [from (cite: Holdship2022)]
- initial depleted abundances from Table 4 of jenkins2009  
  > "and use depleted abundances from Table 4 of (cite: jenkins2009) for our initial conditions." (Model Description) [from (cite: jenkins2009)]
- single-point homogeneous clouds shielded from UV, following earlier ALCHEMI modeling  
  > "We use a single point model to replicate the environment in the GMCs by assuming these gas clouds are homogeneous because they have high enough visual extinctions" (Model Description) [from (cite: harada21)]
- on-the-spot approximation for column density  
  > "we multiply the fractional abundance at the source of the emission by our" (Model Description) [from (cite: Dyson1997)]
- HNC + O and HNC + H temperature barriers (high 2000 K, 1200 K; low 20 K, 200 K) and HNC + O reaction  
  > "We test both the high (2000 K, 1200 K) and low (20 K, 200 K) barrier values (cite: hacar20)" (Model Description) [from (cite: hacar20)]
- GMC positions  
  > "The GMC positions we have adopted in this analysis (Table 5) are derived from the GMC positions reported by (cite: leroy15)" (GMC Positions) [from (cite: leroy15)]

### Not stated but needed to reproduce (our reading)

- Continuum subtraction method (line-free channels, fit order) for the ALCHEMI cubes
- Imaging parameters (weighting/robust, cell size, deconvolver, masks) and how the 1.6 arcsec beam was set
- Primary-beam correction status of the mosaic and any flux-scale correction applied to the moment maps
- Velocity range or line-width mask used by CubeLineMoment for each transition
- Number of live points and stopping settings beyond the fractional remainder threshold in UltraNest
- Priors and fits for each GMC's kinetic temperature and column density where unconstrained (upper-limit rule details)
- Software versions for UCLCHEM, UltraNest, SpectralRadex and CubeLineMoment
- Exact GMC aperture handling (pixels averaged, background treatment) and the GMC position table values after the stated corrections
- Whether electron collisions or infrared pumping were excluded in all model runs (both stated as excluded but treatment in table outputs unclear)

## Analysis recipe

1. **extract integrated intensities of HCN and HNC transitions**: CubeLineMoment masking with each bright line used as its own tracer; moment 0, 1, 2 images made with 3x channel RMS signal limit  
  > "Final moment 0 (integrated intensity; Jy km s$^{-1}$), 1 (average velocity; km s$^{-1}$) and 2 (velocity dispersion; km s$^{-1}$) images are generated using a signal limit of three-times the spectral channel baseline RMS" (Spectral Line Signal Extraction)
   - software: CubeLineMoment
   - parameter: 3 sigma per-transition signal limit; 1.6 arcsec mosaics  
  > "using a signal limit of three-times the spectral channel baseline RMS for the respective transition under study." (Spectral Line Signal Extraction)
   - assumption: emission representative of each transition used as its own mask tracer  
  > "we were able to use each as its own tracer." (Spectral Line Signal Extraction)
   - fitting: _not stated_
   - validation: sample spectrum check for spectral blending  
  > "Our CubeLineMoment analysis includes a sample spectrum check to reveal potential spectral line blending." (Interloper Analysis)
2. **average intensities over GMCs**: average integrated intensity inside 10 GMC-like positions using apertures equal to the 1.6 arcsec beam; uncertainties from channel RMS, line widths and absolute flux calibration  
  > "adopting diameters equal to our beam size" (Spectral Line Signal Extraction)
   - software: CubeLineMoment
   - parameter: aperture diameter = 1.6 arcsec beam  
  > "adopting diameters equal to our beam size" (Spectral Line Signal Extraction)
   - assumption: offset between HCN and HNC centers does not substantially affect integrated intensities  
  > "any potential offset between the centers of the two species’ emission would not substantially affect our calculated integrated intensities." (Spectral Line Signal Extraction)
   - fitting: _not stated_
   - validation: _not stated_
3. **check HNC 4-3 line blending**: estimate interloper contributions and decide not to apply correction  
  > "Since the estimated correction required to this single transition is small, we do not apply these corrections" (Interloper Analysis)
   - parameter: at most 4% (H2CO) and 1% (HNC v2=1) contribution  
  > "contribute respectively at most 4% and 1% to the HNC" (Interloper Analysis)
   - fitting: _not stated_
   - validation: consistent with multi-species LTE analysis in ALCHEMI-ACA  
  > "This contamination estimate is consistent with the multi-species LTE analysis of molecular column densities described in (cite: ALCHEMI-ACA)." (Interloper Analysis)
4. **compute chemical abundances per GMC model point**: UCLCHEM gas-grain chemistry with UMIST12 gas network, added HNC+O reaction, both high and low isomerization barriers tested, scaled cosmic-ray rates from zeta0  
  > "We take our gas phase network from UMIST12 (cite: McElroy2013)" (Model Description); "The cosmic ray reaction rates use a cosmic ray ionization rate of" (Model Description)
   - software: UCLCHEM
   - parameter: zeta0 = 1.36e-17 s^-1  
  > "The cosmic ray reaction rates use a cosmic ray ionization rate of" (Model Description)
   - parameter: priors: T 50-300 K uniform; n 10^3-10^7 cm^-3 log-uniform; zeta 10-10^7 zeta0 log-uniform; N(H2) 10^22-10^25 cm^-2 log-uniform  
  > "we sample kinetic temperatures between 50 and 300 K, adopting a flat prior distribution" (Defining Bayesian Priors)
   - assumption: homogeneous, UV-shielded single-point cloud  
  > "We use a single point model to replicate the environment in the GMCs" (Model Description)
   - assumption: cosmic ray ionization and heating treated separately; grain surface reactions included by default  
  > "We further include UCLCHEM’s default grain surface reactions including freeze out, non-thermal desorption, and diffusive reactions between species adsorbed to the grain." (Model Description)
   - fitting: _not stated_
   - validation: _not stated_
5. **convert chemistry to line intensities**: SpectralRadex non-LTE escape-probability calculation with H2 collisions only, uniform line width 100 km/s and beam-filling factor 1; Jy km/s converted to K km/s using 13.59 (300 GHz/nu)^2 with 1.6 arcsec beam  
  > "These integrated intensities are calculated assuming a uniform line width of 100" (Model Description); "so we can use the following equation to convert our observed beam-averaged integrated intensities from Jy km" (Nested Sampling)
   - software: SpectralRadex, RADEX
   - parameter: line width 100 km/s; beam-filling 1; electron collisions excluded  
  > "and a beam-filling factor of 1." (Model Description)
   - assumption: isothermal, homogeneous 1D environment; no infrared pumping of vibrational bending modes  
  > "Since we do not measure spectral line intensity ratios less than 1 toward the NGC 253 CMZ" (Model Description)
   - fitting: _not stated_
   - validation: optical depth check in step 7  
  > "we have used our RADEX analysis to estimate the optical depth of our HCN and HNC transitions" (Modeling Results)
6. **constrain physical conditions per GMC**: UltraNest MLFriends nested sampling of T, n, zeta, N(H2) with Gaussian likelihood; report median and inner 67% interval, 83rd percentile upper limits where posterior peaks at lower bound  
  > "by implementing the Monte Carlo algorithm MLFriends (cite: ultranest14; ultranest19)" (Nested Sampling); "we report the median values of the posterior distributions for each parameter with uncertainties that represent the inner 67% of the distributions." (Modeling Results)
   - software: UltraNest, MLFriends
   - parameter: log-uniform priors in n, zeta, N(H2); uniform in T  
  > "We adopt a log-uniform distribution for densities over the range" (Defining Bayesian Priors)
   - assumption: Gaussian errors in the likelihood  
  > "by assuming Gaussian errors giving the standard function" (Nested Sampling)
   - assumption: high temperature barriers (2000 K, 1200 K) used for reported results  
  > "We show results using the high temperature barriers (2000 K, 1200 K) for the HNC + O and HNC + H reactions" (Modeling Results)
   - fitting: UltraNest MLFriends nested sampling; sampling stops when fractional remainder is insignificant  
  > "These iterations continue until the live point weights are insignificant" (Nested Sampling)
   - validation: bimodal CRIR solutions examined; low-zeta mode dismissed as unphysical  
  > "As such, we dismiss the lower CRIR solution across all GMCs as unphysical and only present the high CRIR solutions." (Modeling Results)
7. **check optical depth and abundance ratios**: model optical depths over middle 67% of UltraNest samples; compare modeled isotopologue optical-depth ratios with observed isotope ratios  
  > "We model the optical depth for all iterations of our UltraNest sampling algorithm and analyze the middle 67% of the resulting distribution." (Modeling Results)
   - software: UCLCHEM, SpectralRadex
   - fitting: _not stated_
   - validation: modeled isotopologue optical depth ratios consistent with observed isotope ratios  
  > "We found that the ratios of modeled optical depths are consistent with the observationally-derived isotope ratios themselves" (Modeling Results)
8. **test HCN/HNC vs CRIR and heating-source correlations**: Spearman rank correlation with Monte Carlo simulated Gaussian datasets of 10 GMC points; median rho reported with standard deviation  
  > "We use our modeled abundance ratios and CRIR estimates for each GMC in combination with their uncertainties to create simulated Gaussian datasets" (Modeling Results)
   - software: SciPy
   - parameter: 10,000 simulated sets of 10 points  
  > "consisting of 10,000 sets of 10 data points each (1 point for each GMC)" (Modeling Results)
   - assumption: modeled CRIR and ratio uncertainties treated as Gaussian  
  > "We use our modeled abundance ratios and CRIR estimates for each GMC in combination with their uncertainties to create simulated Gaussian datasets" (Modeling Results)
   - fitting: _not stated_
   - validation: _not stated_
9. **estimate gas heating from cosmic rays**: UCLPDR PDR modeling for gas temperature given density and CRIR at A_V ~10, compared with kinetic temperatures from mangum19 and UCLCHEM  
  > "`UCLPDR` provides an estimated gas temperature given input volume densities and CRIRs, assuming an" (The Effect of Cosmic Rays on the HCN/HNC Ratio)
   - software: UCLPDR
   - parameter: A_V ~ 10  
  > "assuming an $A_{V} \sim10$ (in this case in order to model the inner, UV-shielded part of the cloud)." (The Effect of Cosmic Rays on the HCN/HNC Ratio)
   - fitting: _not stated_
   - validation: agreement with mangum19 kinetic temperatures where constrained  
  > "the high kinetic temperatures from our PDR modeling agree with those derived by (cite: mangum19)" (The Effect of Cosmic Rays on the HCN/HNC Ratio)
10. **relate CRIR to supernova rate**: scale zeta_MW from Milky Way supernova-driven estimates to a supernova rate and compare with NGC 253 rate range  
  > "These analyses suggest a quantitative connection between supernovae and the CRIR" (The Connection Between CRIR and Supernovae)
   - parameter: zeta0 = 1.36e-17 s^-1; SN rate 0.3 per yr upper limit  
  > "an upper limit to the supernova rate of 0.3 yr$^{-1}$ would imply an upper limit to the CRIR of" (The Connection Between CRIR and Supernovae)
   - assumption: Milky Way-based supernova energetics applied to NGC 253  
  > "As summarized by (cite: Dalgarno2006), a lower-limit to the Milky Way CRIR" (The Connection Between CRIR and Supernovae)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CubeLineMoment** : integrated intensity and moment map extraction from ALCHEMI cubes  
  > "we use the CubeLineMoment script introduced for this same purpose by (cite: mangum19)" (Spectral Line Signal Extraction)
- **UCLCHEM** : gas-grain chemical modeling of HCN and HNC abundances  
  > "We model the chemical and physical conditions within each of the 10 GMCs using the chemical modeling code" (Model Description)
- **SpectralRadex** : python wrapper for RADEX to compute integrated intensities from abundances  
  > "we use SpectralRadex, a python library which includes a wrapper for the RADEX program." (Model Description)
- **RADEX** : 1D non-LTE radiative transfer with escape probability  
  > "RADEX is a 1D non-Local Thermodynamic Equilibrium (LTE) statistical equilibrium radiative transfer code" (Model Description)
- **UltraNest** : MLFriends nested sampling of posterior distributions  
  > "using the UltraNest package (cite: ultranest21)" (Nested Sampling)
- **UCLPDR** : PDR modeling of gas temperature from density and CRIR  
  > "we estimate the heating that would result from these CRIRs via the Photon-Dominated Region (PDR) modeling code" (The Effect of Cosmic Rays on the HCN/HNC Ratio)
- **SciPy** : spearmanr function for rank correlation  
  > "employing the SciPy (cite: scipy2020) function" (Modeling Results)
- **CASA** : listed in Software section; the purpose is not described in the text  
  > "CASA (cite: casa), Astropy (cite: Astropy2013)" (Software)
- **Astropy** : listed in Software section; the purpose is not described in the text  
  > "CASA (cite: casa), Astropy (cite: Astropy2013)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| log10 volume density n(H2), GMC 5 (median, inner 67%) | 5.62 | +0.31/-0.34 | log10 cm^-3 | 6 | NGC 253 GMC Physical Parameters; we are able to constrain volume density and cosmic ray ionization rate |
| log10 CRIR zeta, GMC 5 (median, inner 67%) | 5.09 | +0.39/-0.50 | log10 zeta0 | 6 | NGC 253 GMC Physical Parameters |
| CRIR zeta in central GMCs | ~10^-12 | not stated | s^-1 | 6 | We see higher cosmic ray ionization rates in the center of the CMZ |
| CRIR zeta in outer GMCs | ~10^-13 | not stated | s^-1 | 6 | as compared to those on its outskirts |
| volume density in outer GMCs | <=10^4 | not stated | cm^-3 | 6 | as compared to the outer GMCs |
| Spearman rho, CRIR vs HCN/HNC abundance ratio (median) | -0.47 | ±0.26 | dimensionless | 8 | indicates there is a moderately anti-correlated relationship between CRIR and the HCN/HNC abundance ratio |
| median Spearman rho, CRIR vs heating sources | 0.67 | standard deviation 0.21 | dimensionless | 8 | are 0.67 and 0.60 respectively, with standard deviations of 0.21 and 0.17. |
| median Spearman rho, density vs heating sources | 0.60 | standard deviation 0.17 | dimensionless | 8 | are 0.67 and 0.60 respectively, with standard deviations of 0.21 and 0.17. |
| HCN/HNC abundance ratio in central GMCs | ~1-2 (lowest, intensity ratio) | not stated | dimensionless | 2 | These ratios are at their lowest |
| CRIR upper limit implied by SN rate 0.3 per yr | ~3000 | not stated | zeta0 | 10 | an upper limit to the supernova rate of 0.3 yr$^{-1}$ would imply an upper limit to the CRIR of |
| CRIR zeta0 equivalent supernova rate | ~10^-4 | not stated | per yr | 10 | the CRIR represented by $\zeta_0$ corresponds to a supernova rate of |
| PDR gas temperature in inner GMCs 4-6 | ~200-500 | not stated | K | 9 | the density and CRIR estimates in the inner GMCs (4–6) result in PDR gas temperatures of |
| HNC 4-3 interloper contribution | at most 4% (H2CO) and 1% (HNC v2=1) | not stated | dimensionless | 3 | contribute respectively at most 4% and 1% to the HNC |
| modeled optical depth | peaks at reasonably low values | not stated | dimensionless | 7 | the optical depth distributions peak at reasonably low |

## Qualitative findings

- cosmic ray heating dominates the heating budget; mechanical heating not significant for HCN/HNC chemistry  
  > "we find cosmic ray heating dominates the heating budget, and mechanical heating does not play a significant role in the HCN and HNC chemistry." (abstract)
- density and CRIR enhanced in central GMCs by about an order of magnitude  
  > "are enhanced by about an order of magnitude in the galaxy’s central regions as compared to those further from the nucleus." (abstract)
- anticorrelation between HCN/HNC ratio and CRIR  
  > "we see an anticorrelation between the HCN/HNC ratio and CRIR, indicating that this ratio will be lower in regions where" (abstract)

## Claim tuples

- H: Does the HCN/HNC ratio indicate strong mechanical heating in the NGC 253 CMZ? | E: Compare measured HCN/HNC integrated intensity ratios with meijerink11 predictions and fit UCLCHEM+RADEX models to the ratios | R: Ratios are low (<10; ~1-2 in central GMCs), far below the ~50 predicted for significant mechanical heating | F: Low mechanical heating; NGC 253 lies in a regime of high cosmic ray ionization rate | **supported**
- H: Are density and CRIR enhanced in the central GMCs relative to outer GMCs? | E: UltraNest sampling of UCLCHEM+RADEX models per GMC with physical priors | R: Central GMCs 4-6 show higher n and zeta; GMC 5 log10 n = 5.62 and log10 zeta = 5.09 zeta0 | F: Density and CRIR gradient across the CMZ, with CRIR ~10^-12 s^-1 at the center | **supported**
- H: Do CRIR and density correlate with the number of star formation heating sources per GMC? | E: Spearman correlations between per-GMC CRIR/density and counts of SNRs, HII regions and SHCs, with Monte Carlo error estimates | R: Median rho 0.67 (CRIR) and 0.60 (density), standard deviations 0.21 and 0.17 | F: Likely positive correlations, based on 10 GMCs | **partially**
- H: Is mechanical heating needed to explain the high kinetic temperatures in the NGC 253 CMZ? | E: UCLPDR PDR modeling of gas temperature from the derived densities and CRIRs, compared with mangum19 kinetic temperatures | R: PDR temperatures of ~200-500 K in inner GMCs, consistent with observed high temperatures | F: Cosmic ray heating alone can produce high kinetic temperatures; little mechanical heating contribution | **partially**

## Reasoning

- Why this data: ALCHEMI survey provides multiple HCN and HNC transitions over the CMZ at uniform resolution  
  > "we can use combinations of chemical tracers from ALCHEMI’s robust dataset" (HCN and HNC in Galaxies)
- Why this method: Treating cosmic ray chemistry and heating separately is needed to disentangle their effects  
  > "we treat cosmic rays and heating separately in our models." (Introduction)
- Alternative: infrared pumping of HCN/HNC vibrational bending modes not included, since measured ratios are not below 1  
  > "we did not see a justification for including infrared excitation in our radiative transfer model." (Model Description)
- Alternative: electron-induced collisions not considered; deferred to future work  
  > "we have opted to not consider electron-induced collisions in our analysis" (Model Description)
- Alternative: low-CRIR posterior mode dismissed as unphysical  
  > "we dismiss the lower CRIR solution across all GMCs as unphysical" (Modeling Results)
- Alternative: HNC 4-3 interloper correction not applied  
  > "we do not apply these corrections to our presented integrated intensities." (Interloper Analysis)
- How they decided it was enough: Nested sampling continued until remaining live-point weight fraction was at most 0.01  
  > "These iterations continue until the live point weights are insignificant" (Nested Sampling)
- Limitation (authors): kinetic temperature and H2 column density largely unconstrained by HCN and HNC  
  > "We find that kinetic temperature and H$_{2}$ column density are largely not constrained by our HCN and HNC measurements." (Modeling Results)
- Limitation (authors): the temperature barrier choice had no discernible effect on results  
  > "we find varying the temperature barrier had no discernible effect on our results." (Modeling Results)
- Caveat (inferred, ours): Table 4 note states uncertainties are ±33% of the posterior while the text states inner 67%; the interval definition is inconsistent.
- Caveat (inferred, ours): Dismissing the low-CRIR posterior mode relies on external CRIR estimates, which shapes the reported CRIR results.
- Caveat (inferred, ours): Results rest on a single homogeneous point model per GMC and 1.6 arcsec beam-sized apertures; no resolution test is presented.
- Caveat (inferred, ours): GMC positions were corrected using private communication with the leroy15 author, which cannot be checked from the paper.
- Caveat (inferred, ours): Heating-source counts use projected sky positions with no distance term, and the SN fraction is an estimate from ua97 statistics.
- Caveat (inferred, ours): Supernova-CRIR link uses Milky Way energetics scaled to NGC 253 without independent calibration.

## Reproducibility

- Data public (paper): ALMA data cited by ADS/JAO identifiers; public or proprietary status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00161.L and ADS/JAO.ALMA#2018.1.00162.S." (Acknowledgements)
- Products in archive: 1.6 arcsec mosaics extracted from the ALCHEMI archive  
  > "From the ALCHEMI archive we extract the" (ALCHEMI Data)
- Code: software links given for CubeLineMoment, UCLCHEM, SpectralRadex, RADEX, UltraNest and UCLPDR; analysis scripts release not stated  
  > "https://github.com/keflavich/cube-line-extractor" (Footnote 2)
- Missing: Exact ALCHEMI calibration and imaging settings (deferred to ALCHEMI-ACA)
- Missing: Continuum subtraction and line-free channel selection
- Missing: Per-GMC aperture and CubeLineMoment velocity/mask settings
- Missing: UltraNest sampler settings (live points) and seed
- Missing: UCLCHEM, SpectralRadex and UCLPDR version and input files
- Missing: Full GMC position table after the stated private-communication corrections
- Data volume (inferred): not stated; ALCHEMI cubes over 84-373 GHz at 1.6 arcsec resolution imply large cubes (likely tens of GB, inferred)
- Score (inferred): 6/5, Modeling recipe and most numbers are stated, but calibration/imaging is deferred to ALCHEMI-ACA and several sampler and extraction settings are missing.
- Rediscovery candidate: no, Data are archival ALMA products but their public status is not stated in the paper, and the imaging and continuum steps are not fully specified.

## Links

- Method: (cite: mangum19) (CubeLineMoment extraction method and kinetic temperature/N(H2) priors)
- Method: (cite: uclchem) (UCLCHEM chemical modeling code)
- Method: (cite: radex) (RADEX non-LTE radiative transfer)
- Method: (cite: ultranest21) (UltraNest nested sampling package)
- Companion: (cite: ALCHEMI-ACA) (ALCHEMI survey data acquisition, calibration and imaging)
- Companion: (cite: Holdship2022) (ALCHEMI H3O+/SO CRIR study and interloper procedure)
- Companion: (cite: harada21) (ALCHEMI HOC+ CRIR and density constraints)
- Companion: (cite: holdship_c2h) (ALCHEMI C2H CRIR constraints for GMCs 3-7)
- Related: ALCHEMI (ALMA Comprehensive High Resolution Molecular Inventory) large program

## Checks

```json
{
 "quotes": 136,
 "quotes_ok": 135,
 "quote_pass_rate": 0.993,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 14,
 "numeric_problems": 0,
 "fill": {
  "facts": 129,
  "stated": 95,
  "rate": 0.736
 },
 "evidence_ok": false
}
```

## Figures

- **Figure 1** (sky_image, 1 panel(s), data): Locations of radio continuum sources and super hot cores within the NGC 253 CMZ, overlaid on the 212 GHz ALCHEMI dust continuum map, with numbered GMCs marked.
  - axes: x: RA (J2000) [hours:minutes:seconds]; y: Dec (J2000) [degrees:arcmin:arcsec]; colour: Intensity [Jy beam-1]
  - read off the plot: approx. colour scale spans 2e-4 to 0.1 Jy beam-1; approx. beam size 1.6 arcsec
- **Figure 2** (model_vs_data, 1 panel(s), model): HCN and HNC column densities and their ratio as a function of cosmic ray ionization rate for PDR models at fixed density and FUV field, for three mechanical heating rates.
  - axes: x: Cosmic ray ionization rate zeta [s-1]; y: HCN and HNC column density [cm-2]; right y: [HCN]/[HNC] abundance ratio [unitless]
  - supports step 8
  - read off the plot: approx. N(HCN) peak about 1e18 cm-2 at lowest zeta for Gamma_mech 2e-17 erg cm-3 s-1; approx. [HCN]/[HNC] about 100 at zeta near 1e-15 s-1 for Gamma_mech 2e-17; approx. N(HNC) about 1e15 cm-2 at lowest zeta for Gamma_mech 2e-17
- **Figure 3** (moment_map, 4 panel(s), data): HCN integrated intensity (moment 0) maps at 1-0, 2-1, 3-2 and 4-3 toward NGC 253, with GMC numbers, the TH2 radio peak and 85-355 GHz continuum contours.
  - axes: x: RA (ICRS) [hours:minutes:seconds]; y: Dec (ICRS) [arcsec]; colour: HCN integrated intensity [Jy km/s]; contours: Continuum flux [Jy]
  - supports step 1
  - read off the plot: approx. HCN 1-0 colour scale up to about 10 Jy km/s; approx. HCN 4-3 colour scale up to about 80 Jy km/s; approx. HCN 2-1 colour scale up to about 40 Jy km/s
  - reproduction target
- **Figure 4** (moment_map, 4 panel(s), data): HNC integrated intensity (moment 0) maps at 1-0, 2-1, 3-2 and 4-3 toward NGC 253 with the same markings and contours as Figure 3.
  - axes: x: RA (ICRS) [hours:minutes:seconds]; y: Dec (ICRS) [arcsec]; colour: HNC integrated intensity [Jy km/s]; contours: Continuum flux [Jy]
  - supports step 1
  - read off the plot: approx. HNC 1-0 colour scale up to about 10 Jy km/s; approx. HNC 4-3 colour scale up to about 80 Jy km/s
  - reproduction target
- **Figure 5** (moment_map, 4 panel(s), data): HCN/HNC integrated intensity ratio maps at 1-0, 2-1, 3-2 and 4-3 with HCN integrated intensity contours.
  - axes: x: RA (ICRS) [hours:minutes:seconds]; y: Dec (ICRS) [arcsec]; colour: HCN/HNC integrated intensity ratio [unitless]; contours: HCN integrated intensity [Jy km/s]
  - supports step 1
  - read off the plot: approx. ratio colour scale from about 0.5 to 5
  - reproduction target
- **Figure 6** (spectrum, 1 panel(s), data): Spectrum of GMC 6 around HNC 4-3 with Gaussian fits, showing the blending of the v2=1 vibrationally excited HNC line and the H2CO 5(1,5)-4(1,4) line.
  - axes: x: Rest frequency [GHz]; y: Flux density [mJy beam-1]
  - supports step 3
  - validation: Checks whether the HNC 4-3 line is blended with the vibrationally excited HNC v2=1 line and an H2CO line by fitting multiple Gaussian components.
  - read off the plot: approx. HNC 4-3 v=0 peak about 900 mJy beam-1 at 362.63 GHz; approx. H2CO blend component peak about 100 mJy beam-1 near 362.74 GHz; approx. HNC v2=1 component peak about 40 mJy beam-1 near 362.55 GHz
- **Figure 7** (schematic, 1 panel(s), schematic): Flow chart of the nested sampling coupled to UCLCHEM chemistry and SpectralRadex radiative transfer for fitting GMC conditions.
  - supports step 6
- **Figure 8** (other, 2 panel(s), model, data): Top: number of heating sources per GMC by type. Bottom: median modeled volume density and cosmic ray ionization rate per GMC with 16th-84th percentile error bars.
  - axes: x: GMC number [unitless]; y (top): Number of heating sources [count]; y (bottom): Volume density n and zeta/zeta0 [cm-3 and unitless]
  - supports step 6
  - read off the plot: approx. GMC 5 median n about 4e5 cm-3; approx. GMC 1 median n about 6e3 cm-3; approx. GMC 5 median zeta/zeta0 about 1.2e5; approx. GMC 5 has 10 heating sources in total
- **Figure 9** (other, 2 panel(s), data, model): Observed integrated intensities versus upper-level energy for HCN and HNC in GMC 1 and GMC 6, compared with the modeled flux distributions.
  - axes: x: Upper level energy Eu [K]; y: Integrated intensity [K km s-1]
  - supports step 4
  - validation: Compares observed HCN and HNC line fluxes with the modelled flux distributions per GMC, checking that the fitted model reproduces the data.
  - read off the plot: approx. GMC 1 HCN integrated intensity about 245 K km/s at Eu 4 K; approx. GMC 6 HCN integrated intensity about 850 K km/s at Eu 4 K; approx. GMC 6 HNC integrated intensity about 640 K km/s at Eu 4 K; approx. GMC 1 HNC integrated intensity about 105 K km/s at Eu 4 K
  - reproduction target
- **Figure 10** (corner_plot, 16 panel(s), model): Posterior distributions of gas temperature, log volume density, log cosmic ray ionization rate and log H2 column density for GMC 1.
  - axes: x and y: T_K, log10 n, log10(zeta/zeta0), log10 N_H2 [K, log10 cm-3, unitless, log10 cm-2]
  - supports step 6
  - read off the plot: approx. T_K 173 K (+76/-68); approx. log10 n 3.8 cm-3 (+0.9/-0.5); approx. log10(zeta/zeta0) 3.0 (+1.0/-1.6); approx. log10 N_H2 22.9 cm-2 (+0.8/-0.5)
  - reproduction target
- **Figure 11** (corner_plot, 16 panel(s), model): Posterior distributions of gas temperature, log volume density, log cosmic ray ionization rate and log H2 column density for GMC 6.
  - axes: x and y: T_K, log10 n, log10(zeta/zeta0), log10 N_H2 [K, log10 cm-3, unitless, log10 cm-2]
  - supports step 6
  - read off the plot: approx. T_K 199 K (+70/-100); approx. log10 n 5.4 cm-3 (+0.4/-0.8); approx. log10(zeta/zeta0) 4.7 (+0.5/-2.5); approx. log10 N_H2 23.4 cm-2 (+1.1/-0.9)
  - reproduction target
- **Figure 12** (other, 10 panel(s), model): Violin plots of modeled HCN/HNC abundance ratios for each of the 10 GMCs using the most likely 67% of models.
  - axes: x: GMC [unitless]; y: X(HCN)/X(HNC) abundance ratio [unitless]
  - supports step 7
  - read off the plot: approx. GMC 1 median ratio about 6; approx. GMC 5 median ratio about 2; approx. GMC 10 median ratio about 3
  - reproduction target
- **Figure 13** (scatter_or_relation, 2 panel(s), data, model): Top: HCN/HNC abundance ratio versus log cosmic ray ionization rate per GMC. Bottom: distribution of Spearman coefficients from simulated Gaussian data.
  - axes: x (top): log10(zeta/zeta0) [unitless]; y (top): X(HCN)/X(HNC) [unitless]; x (bottom): Spearman rho [unitless]; y (bottom): Probability density [unitless]
  - supports step 8
  - validation: Tests whether the HCN/HNC ratio correlates with CRIR, using Spearman coefficients from a simulated dataset with uncertainties to assess significance.
  - read off the plot: approx. rho = -0.47 +/- 0.26; approx. HCN/HNC ratio about 6 at log10(zeta/zeta0) about 3.8; approx. HCN/HNC ratio about 2 at log10(zeta/zeta0) about 5.1
  - reproduction target
- **Figure 14** (model_vs_data, 1 panel(s), model): UCLPDR gas temperature as a function of volume density and cosmic ray ionization rate, with boxes for outer and inner GMC regimes and points for GMC 1 and GMC 6.
  - axes: x: log10(zeta/zeta0) [unitless]; y: log10 n [log10 cm-3]; colour: Gas temperature Tgas [K]
  - supports step 6
  - read off the plot: approx. GMC 6 point at log n 5.4 and log(zeta/zeta0) 5.0, Tgas about 400 K; approx. GMC 1 point at log n 3.8 and log(zeta/zeta0) 3.8, Tgas about 100 K
