# Deep Search for Phosphine in a Prestellar Core

`2024ApJ...968L..19F` | The Astrophysical Journal Letters 2024 | first author: Furuya, Kenji | arXiv: 2406.05978 | DOI: 10.3847/2041-8213/ad50cc

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: astrochemistry, star_formation
- Question: Can gas-phase PH3 be detected in the prestellar core L1544, and what does its abundance imply for the volatile phosphorus elemental abundance?  
  > "This characteristic and well-constrained physical properties of L1544 allow us to constrain the upper limit to the volatile P elemental abundance of $5\times10^{-9}$" (abstract)
- Target **L1544**: coordinates RA 05h04m17.21s, Dec +25d10m42.8s (ICRS, pointing center)  
  > "low-mass prestellar core L1544 in Taurus at a distance of 135 pc (cite: schlafly14)" (Introduction); "The pointing center of antennas is RA = 05$^\mathrm{h}$04$^\mathrm{m}$17.21s and Dec = +25$^\circ$10$\ensuremath{'}$42.8$''$" (2 Observations); z/distance 135 pc  
  > "low-mass prestellar core L1544 in Taurus at a distance of 135 pc (cite: schlafly14)" (Introduction); "The pointing center of antennas is RA = 05$^\mathrm{h}$04$^\mathrm{m}$17.21s and Dec = +25$^\circ$10$\ensuremath{'}$42.8$''$" (2 Observations); distance from Schlafly et al. 2014 (cite: schlafly14)  
  > "low-mass prestellar core L1544 in Taurus at a distance of 135 pc (cite: schlafly14)" (Introduction); "The pointing center of antennas is RA = 05$^\mathrm{h}$04$^\mathrm{m}$17.21s and Dec = +25$^\circ$10$\ensuremath{'}$42.8$''$" (2 Observations)

## Data provenance

- ALMA projects: 2022.1.01490.S
- bands: _not stated_
- frequencies and spectral setup: Five spectral windows, 0.07 km/s resolution; PH3 window 266.89–267.01 GHz; continuum window 252.06–253.94 GHz  
  > "The sky frequencies of 250.41–250.47, 250.79–250.85, 265.86–265.92, 266.89–267.01, 267.53–267.59 GHz, are covered by five spectral windows with a velocity resolution of 0.07 km s$^{-1}$" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: ACA stand-alone (7 m), 9-11 antennas  
  > "The total number of 7 m antennas is 9-11, where the minimum–maximum baseline lengths are 8.9–48.9 m." (2 Observations)
- configurations: _not stated_
- baselines: 8.9–48.9 m  
  > "the minimum–maximum baseline lengths are 8.9–48.9 m" (2 Observations)
- angular resolution: 4.8'' x 5.8'' (650 x 780 au)  
  > "The synthesized beam size at the frequency of the PH$_3$ transition is 4.8$''$ $\times$ 5.8$''$" (2 Observations)
- max recoverable scale: about 25''  
  > "The maximum recoverable scale is about 25$\ensuremath{''}$." (2 Observations)
- sensitivity: 3 sigma = 18 mK in 0.07 km/s channels  
  > "The line was not detected down to 3$\sigma$ levels in 0.07 km s$^{-1}$ channels of 18 mK." (abstract)
- time on source: 7.3 hours  
  > "The total on-source integration time is 7.3 hours." (2 Observations)
- observing dates: July and August 2023  
  > "Observations were carried out with the ACA stand-alone mode of ALMA in July and August 2023" (2 Observations)
- pi or archival as stated: Cycle 9 program, PI K. Furuya  
  > "as a Cycle 9 program (2022.1.01490.S, PI: K. Furuya)" (2 Observations)
- Line: ortho-PH3 1_0-0_0 (266.944 GHz)
- External data: Spectroscopic parameters of PH3 transition  
  > "The parameters of the observed transition are taken from the Cologne Database for Molecular Spectroscopy (cite: muller05) and Leiden Atomic and Molecular Database (cite: schoier05)." (3 Observational Results) [from (cite: muller05); (cite: schoier05)]
- External data: Core-center gas temperature 6 K and density/temperature structure of L1544  
  > "The excitation temperature ($T_{\rm ex}$) is assumed to be the same as the gas temperature of the core center, 6 K (cite: keto15)." (3 Observational Results) [from (cite: keto15)]
- External data: Cosmic-ray ionization rate 3e-17 s^-1  
  > "(cite: readelli21) constrained the CR ionization rate to be $3\times10^{-17}$ s$^{-1}$" (4.1 Model description) [from (cite: readelli21)]
- External data: Dust mass absorption coefficient 1.21 cm2/g at 1.16 mm  
  > "we use 1.21 cm$^2$ g$^{-1}$ at 1.16 mm" (Appendix: Derivation of the H2 column density) [from (cite: Oss94)]
- External data: Solar P abundance 2.57e-7  
  > "The solar abundance of phosphorus is $2.57\times10^{-7}$ with respect to hydrogen (cite: asplund21)." (5 Discussion and Conclusions) [from (cite: asplund21)]
- Simulation/model as data: Gas-ice rate-equation chemical models A-D (6/9 K, 1e6/3e6 cm-3, atomic/molecular initial abundances)  
  > "We consider four different models, varying in temperature, gas density, and initial abundances" (4.1 Model description)

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

- task: tclean  
  > "The CASA task $\mathtt{tclean}$ is used for imaging, and the masking is done using the auto-multithresh algorithm." (2 Observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust 0.5  
  > "with the Briggs weighting and a robustness parameter of 0.5" (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: auto-multithresh  
  > "the masking is done using the auto-multithresh algorithm" (2 Observations)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub in CASA  
  > "The continuum emission is subtracted from the spectral data using the $\mathtt{uvcontsub}$ task in CASA." (2 Observations)
- line free channels: _not stated_
- primary beam correction: impbcor  
  > "corrected for the primary beam pattern using the $\mathtt{impbcor}$ task in CASA" (2 Observations)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 4.8'' x 5.8''  
  > "4.8$''$ $\times$ 5.8$''$ with the Briggs weighting" (2 Observations)
- final rms: _not stated_

### Inherited from earlier work

- LTE column density upper limit calculation  
  > "the 3$\sigma$ intensity upper limit is converted to the upper limit to the column density ($N(\ce{PH3})$) following (cite: mangum15)" (3 Observational Results) [from (cite: mangum15)]
- Binding energy distribution method  
  > "We consider a binding energy distribution for all surface species using the method developed by (cite: furuya23)" (4.1 Model description) [from (cite: furuya23)]
- Chemical code  
  > "We utilize the gas-ice astrochemical code based on the rate equation approach (cite: furuya15)." (4.1 Model description) [from (cite: furuya15)]
- Chemical network base  
  > "Our gas-ice chemical network is based on that of (cite: garrod13)" (4.1 Model description) [from (cite: garrod13)]

### Not stated but needed to reproduce (our reading)

- Line-free channels used for continuum and uvcontsub
- Image size, cell size, clean threshold/niter
- Calibrators and pipeline version
- Flux scale uncertainty
- Full P chemical network reaction list and rate parameters (partly in Furuya 2023 submitted)
- Spectral rms in K converted from Jy/beam details

## Analysis recipe

1. **Image cube and continuum**: CASA tclean with auto-multithresh, uvcontsub, impbcor; continuum from continuum window plus line-free channels  
  > "The aggregate continuum image is constructed by using the continuum window in addition to the line-free channels selected from the other five spectral windows." (2 Observations)
   - software: CASA
   - parameter: Briggs robust 0.5  
  > "with the Briggs weighting and a robustness parameter of 0.5" (2 Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract spectrum and flux in elliptical region**: 5.0'' x 9.0'' ellipse at continuum peak  
  > "The spectrum and continuum flux are extracted from the 5.0$''$ $\times$ 9.0$''$ (700 au $\times$ 1260 au) elliptical region" (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **PH3 column density upper limit**: 3 sigma sqrt(Delta v delta v) integrated intensity upper limit converted under LTE  
  > "We obtain the upper limit to the column density from the 3$\sigma$ upper limit to the integrated intensity $3\sigma \sqrt{\Delta v \delta v}$" (3 Observational Results)
   - parameter: Delta v = 0.3 km/s; Tex = 6 K (or 9 K)  
  > "$\Delta v$ is assumed to be 0.3 km s$^{-1}$, similar to those of the high-density tracers" (3 Observational Results)
   - assumption: LTE, ortho-to-para ratio of unity  
  > "Then we assume that the ortho-to-para ratio of is unity (cite: hama16)." (3 Observational Results)
   - fitting: _not stated_
   - validation: Non-LTE check with RADEX giving similar limits  
  > "These results are similar to that obtained with the LTE approximation ($<1.2\times10^{11}$ cm$^{-2}$)." (Appendix: critical density)
4. **H2 column density from dust continuum**: Optically thin dust emission equation  
  > "Based on the standard treatment of optically thin dust emission, we apply the following equation to calculate the H$_2$ column density" (Appendix: H2 column density)
   - assumption: Td = Tgas = 6 K; kappa 1.21 cm2/g at 1.16 mm; dust-to-gas 0.008  
  > "we use a canonical value of 0.008 for the solar neighborhood" (Appendix: H2 column density)
   - fitting: _not stated_
   - validation: Compared with Crapsi et al. 2005; factor ~4 lower, attributed to resolved-out extended emission  
  > "Our $N({\ce{H2}})$ is a factor of $\sim$4 lower than the value obtained by (cite: crapsi05)" (Appendix: H2 column density)
5. **Gas-ice chemical modeling to constrain volatile P**: Rate-equation three-phase model at 1e5 yr, varying volatile P elemental abundance from 2.57e-7 to 2.57e-9; gas-phase PH3 scales with P abundance  
  > "The gas-phase abundance is almost proportional to the assumed total volatile P elemental abundance in all four models." (4.2 Model results)
   - parameter: Chemical desorption probability 4%; xi = 3e-17 s^-1  
  > "The chemical desorption probability of upon reaction between and atomic H is set to 4 %" (4.1 Model description)
   - assumption: Photodesorption yield 1e-3 per UV photon for P species  
  > "We assume the yield of 10$^{-3}$ per incident UV photon for all P-bearing species." (4.1 Model description)
   - fitting: _not stated_
   - validation: Conclusion holds for 3e4 yr and 1e6 yr; desorption probability 2% and 8% tested  
  > "We confirmed that this conclusion holds, even if a different time other than 10$^5$ yr ($3\times 10^4$ yr or 10$^6$ yr) is chosen." (4.2 Model results)

## Software

- **CASA** 6.4.1: Data processing, imaging (tclean), uvcontsub, impbcor  
  > "Raw data is processed with the *Common Astronomy Software Applications* (CASA) package (version 6.4.1)." (2 Observations)
- **RADEX** : Non-LTE check of PH3 column density  
  > "we also perform non-LTE analysis with RADEX (cite: vandertak07)" (Appendix: critical density)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| N(PH3) upper limit (Tex=6 K) | 1.2e11 | not stated | cm^-2 | 3 | the upper limit to $N(\ce{PH3})$ is estimated to be $1.2\times10^{11}$ cm$^{-2}$ |
| N(H2) in examined region | 2.6e22 | not stated | cm^-2 | 4 | We estimate the column density of the examined region to be $2.6\times10^{22}$ cm$^{-2}$ |
| PH3 gas-phase abundance upper limit (Tex=6 K) | 5e-12 | not stated | relative to H2 | 3 | the upper limit to the gas-phase abundance is $5\times10^{-12}$ with respect to |
| N(PH3) upper limit (Tex=9 K) | 7.6e10 | not stated | cm^-2 | 3 | the upper limits to $N(\ce{PH3})$ and the abundance are $7.6\times10^{10}$ cm$^{-2}$ and $6.7\times10^{-12}$ |
| Volatile P elemental abundance upper limit | 5e-9 | not stated | relative to H | 5 | the volatile P elemental abundance in L1544 is less than $5\times10^{-9}$ |

## Qualitative findings

- PH3 not detected in L1544; majority of P must be in refractory form  
  > "Then the majority of P should exist in refractory forms." (abstract)

## Claim tuples

- H: Gas-phase PH3 is detectable in a prestellar core where non-thermal desorption occurs | E: Deep ACA observation of PH3 1_0-0_0 toward L1544 continuum peak | R: Not detected; abundance < 5e-12 vs H2 | F: Strict upper limit on PH3 abundance | **supported**
- H: Volatile P is depleted in L1544 | E: Gas-ice chemical modeling linking gas PH3 abundance to volatile P | R: Volatile P < 5e-9, factor ~60 below solar | F: Most P is in refractory dust | **supported**
- H: Refractory P is converted to volatile P between presolar core and protosolar disk | E: Compare L1544 limit with 67P coma P/O | R: 67P volatile P close to solar, higher than L1544 | F: Conversion, e.g. shock sputtering, may have occurred | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Non-thermally desorbed PH3 in a prestellar core probes volatile P; hot corinos not chosen since PH3 may be quickly converted to PO/PN in warm gas  
  > "Therefore, we focus on the latter approach in this work." (Introduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Collisional rate coefficients for PH3-H2 unavailable; extended continuum emission resolved out may explain lower N(H2)  
  > "The contribution from the largely-extended ($>$25") continuum emission that was resolved out in the ACA observations may account for the above discrepancy." (Appendix: H2 column density)
- Caveat (inferred, ours): Upper limit depends on assumed Tex, line width, and OPR
- Caveat (inferred, ours): Model-dependent scaling (chemical desorption 4%, unmeasured P photodesorption/sputtering yields)
- Caveat (inferred, ours): Only volatile small P species in network

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters beyond robust
- Missing: Chemical network files and model code
- Missing: Calibration details
- Data volume (inferred): ~10-30 GB raw ACA data
- Score (inferred): 3/5, ALMA data are linked to a project code but imaging and model details are partial and the chemical code is not released.
- Rediscovery candidate: no, Main result is an upper limit that depends on a custom chemical model whose network and code are not provided.

## Links

- Method: (cite: mangum15) (LTE column density formulation)
- Method: (cite: furuya23) (Binding energy distribution method)
- Companion: (cite: caselli19) (Previous ACA continuum observations of L1544)
- Companion: (cite: caselli22) (Previous ACA line observations of L1544)

## Checks

```json
{
 "quotes": 62,
 "quotes_ok": 62,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 48,
  "rate": 0.615
 },
 "evidence_ok": true
}
```
