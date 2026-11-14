# Lack of high-mass pre-stellar cores in the starless MDCs of NGC 6334

`2019A&A...622A..99L` | Astronomy and Astrophysics 2019 | first author: Louvet, F. | arXiv: 1810.12928 | DOI: 10.1051/0004-6361/201732282

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Do starless massive dense cores in NGC6334 host high-mass pre-stellar cores or fragment into many Jeans-mass cores, as predicted by quasi-static versus competitive accretion models?  
  > "The aim of the present work is to bring observational constraints at the scale of high-mass cores (∼0.03 pc)." (abstract)
- Target **9 starless MDCs in NGC6334 (#11, 16, 17, 21, 26, 27, 35, 44, 45)**: coordinates e.g. MDC#16 17:19:05.24 -36:07:57.8 (J2000); see Table 3  
  > "It belongs to the Sagittarius-Carina arm, lying at 1.75 kpc from the sun (Matthews et al. 2008)." (1. Introduction); "NGC6334-MDC#16 17:19:05.24 -36:07:57.8" (Table 3); z/distance 1.75 kpc  
  > "It belongs to the Sagittarius-Carina arm, lying at 1.75 kpc from the sun (Matthews et al. 2008)." (1. Introduction); "NGC6334-MDC#16 17:19:05.24 -36:07:57.8" (Table 3); distance from Matthews et al. 2008  
  > "It belongs to the Sagittarius-Carina arm, lying at 1.75 kpc from the sun (Matthews et al. 2008)." (1. Introduction); "NGC6334-MDC#16 17:19:05.24 -36:07:57.8" (Table 3)

## Data provenance

- ALMA projects: 2015.1.00850.S
- bands: Band 6 (1.4 mm)  
  > "ALMA observations were carried out in Cycle 3 in Band 6 using 39 antennas" (2.1 ALMA observations)
- frequencies and spectral setup: 12CO(2-1) window at 230.53 GHz, 0.485 MHz (0.63 km/s) resolution  
  > "spectral windows centred on the [12] CO(2-1) transition at 230.53 GHz with a high spectral resolution of 0.485 MHz (or 0.63 km s [−][1] )" (2.1 ALMA observations)
- continuum bandwidth: 1.875 GHz centred at 214.5 GHz, 128 channels of 31.25 MHz  
  > "bandwidth spectral window of 1.875 GHz centred at 214.5 GHz (or 1.40 mm) divided in 128 channels of 31.25 MHz each" (2.1 ALMA observations)
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15 m to 459 m  
  > "baselines ranging from 15 m to 459 m" (2.1 ALMA observations)
- angular resolution: ~0.74 arcsec  
  > "gives access to an angular resolution of ∼0.74 [′′] and a filtering scale of 11.6 [′′] at 1.4 mm" (2.1 ALMA observations)
- max recoverable scale: 11.6 arcsec  
  > "a filtering scale of 11.6 [′′] at 1.4 mm" (2.1 ALMA observations)
- sensitivity: ~0.34 mJy/beam continuum; 16.6 mJy/beam per channel in 12CO  
  > "The mean achieved root mean square (rms) noise level is of ∼0.34 mJy/beam in continuum and of 16.6 mJy/beam per channel in [12] CO(2-1)" (2.1 ALMA observations)
- time on source: ~1.4 min per source  
  > "Each of our 9 sources was observed for ∼1.4 min in total." (2.1 ALMA observations)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO 2-1 (230.53 GHz)
- Other facility **MOPRA 22-m**: HCO+(1-0), H13CO+(1-0), N2H+(1-0) lines for 8 of 9 MDCs  
  > "These observations were performed in September 2008 with the ATNF MOPRA 22-m telescope with the 3mm receiver" (2.2 MOPRA observations)
- Other facility **MALT90**: complementary line data for one additional MDC  
  > "The MOPRA data-set is complemented with observations from the MALT90 survey (Jackson et al. 2013) to cover one additional MDC." (2.2 MOPRA observations)
- Other facility **Herschel/HOBYS**: MDC sample, masses, column density maps, temperatures  
  > "As part of the Herschel /HOBYS project, Tigé et al. (2017) analyzed the properties of the MDCs forming in NCG6334" (1. Introduction)
- External data: MDC masses, radii, dust temperatures, densities  
  > "where M MDC is the mass of the MDC, as reported by Tigé et al. (2017)." (3.1 Large-scale view of the MDCs) [from Tigé et al. 2017]
- External data: Density profile index n=1.8  
  > "Garay et al. (2007) and Mueller et al. (2002) find, on average, a radial profile index of 1.8 for massive dense cores." (3.1 Large-scale view of the MDCs) [from Garay et al. (2007); Mueller et al. (2002)]

## Processing

### Calibration

- pipeline or manual: pipeline-calibrated, standard procedures  
  > "The data was pipeline-calibrated using standard procedures of CASA 4.5.2." (2.1 ALMA observations)
- casa version: CASA 4.5.2  
  > "pipeline-calibrated using standard procedures of CASA 4.5.2" (2.1 ALMA observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean-style Clark method, Briggs weighting  
  > "imaged with the Clark method using the weighting Briggs with a robust parameter of 0.5" (2.1 ALMA observations)
- deconvolver: _not stated_
- weighting robust: robust = 0.5  
  > "using the weighting Briggs with a robust parameter of 0.5" (2.1 ALMA observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: all 128 continuum channels concatenated, no line removal  
  > "The continuum was imaged concatenating together the 128 channels of the spectral window dedicated to the continuum emission" (2.1 ALMA observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: 12CO smoothed to 0.7 km/s  
  > "The [12] CO(2-1) emission line was slightly smoothed to a spectral resolution of 0.7 km s [−][1] ." (2.1 ALMA observations)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Concatenating all continuum channels is valid for pre-stellar structures  
  > "which is a valid approach for pre-stellar structures for which no complex organic molecule emission lines are expected (Motte et al. 2018)" (2.1 ALMA observations) [from Motte et al. 2018]
- Dust opacity law  
  > "β = 1.5, which is typical of dense and cool media (Ossenkopf & Henning 1994)" (3.3 ALMA view of the massive dense cores) [from Ossenkopf & Henning 1994]

### Not stated but needed to reproduce (our reading)

- Image size and cell size
- Clean threshold, masks and iterations
- Getsources configuration parameters
- Flux calibrator and flux-scale uncertainty
- Velocity ranges and rms for continuum-free channels
- How MDC masses/radii in Table 1 were rescaled from Tigé et al.

## Analysis recipe

1. **Fit MOPRA lines**: Gaussian fits to HCO+ and H13CO+, hfs fit for N2H+ in CLASS  
  > "to fit the multiplet N 2 H [+] molecular emission line and Gaussian functions to fit the HCO [+] and H [13] CO [+] molecular line emissions" (3.1 Large-scale view of the MDCs)
   - software: CLASS
   - fitting: _not stated_
   - validation: _not stated_
2. **Virial mass and parameter**: M_vir from N2H+ velocity dispersion with density index n=1.8; alpha_vir = M_vir/M_MDC  
  > "We compute the virial parameter α vir = M vir / M MDC, where M MDC is the mass of the MDC, as reported by Tigé et al. (2017)." (3.1 Large-scale view of the MDCs)
   - assumption: n = 1.8  
  > "We use this value of n = 1.8 to derive the virial mass of our MDCs." (3.1 Large-scale view of the MDCs)
   - fitting: _not stated_
   - validation: _not stated_
3. **Infall asymmetry**: δV=(Vthick-Vthin)/σVthin following Mardones et al. 1997; plus line profile inspection  
  > "we quantify the asymmetry parameter δV = (V thick -V thin )/σV thin to measure line asymmetry" (3.2 Infall motion in MDCs)
   - fitting: _not stated_
   - validation: typical error 0.25  
  > "The typical error in line asymmetry parameter is of 0.25" (3.2 Infall motion in MDCs)
4. **Extract compact ALMA cores and derive masses**: Getsources extraction, mass from integrated flux via eq. 2 at Tdust  
  > "To extract the compact sources within the fields we used the source extraction tool Getsources (Men’shchikov et al. 2012)." (3.3 ALMA view of the massive dense cores)
   - software: Getsources
   - parameter: d = 1.75 kpc; kappa1.4mm = 9.9e-3 cm2/g  
  > "The dust mass opacity was taken to be equal to κ 1.4 mm = 9.9 × 10 [−][3] cm [2] g [−][1]" (3.3 ALMA view of the massive dense cores)
   - assumption: gas-to-dust 100, beta = 1.5, T_dust from Tigé et al.  
  > "including a gas to dust ratio of 100 and an opacity index β = 1.5" (3.3 ALMA view of the massive dense cores)
   - fitting: _not stated_
   - validation: _not stated_
5. **Jeans mass/length and predicted fragmentation**: Compute M_Jeans and λ_Jeans from density and temperature; compare predicted number of cores n=M_MDC/(2.5 M_Jeans) with detections  
  > "each core will have a mass close to the thermal Jeans mass ( M Jeans )" (4.1 Comparison with models)
   - parameter: mu = 2.8  
  > "µ = 2.8 the mean molecular weight (Kauffmann et al. 2008)" (4.1 Comparison with models)
   - fitting: _not stated_
   - validation: 5σ mass sensitivity 0.11 Msun compared with Jeans mass  
  > "have a mass equivalent 5σ detection threshold of 0.11 M ⊙, hence we are fully sensitive to the Jeans mass and Jeans scale." (4.1 Comparison with models)
6. **Magnetic field needed for support**: B = σ_A sqrt(μ0 ρ) with σ_A from M_vir,B = M_MDC  
  > "The magnetic field strength is computed as" (4.1 Comparison with models)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.5.2: pipeline calibration and imaging  
  > "pipeline-calibrated using standard procedures of CASA 4.5.2" (2.1 ALMA observations)
- **Getsources** : compact source extraction  
  > "we used the source extraction tool Getsources (Men’shchikov et al. 2012)" (3.3 ALMA view of the massive dense cores)
- **CLASS** : line fitting of MOPRA spectra  
  > "We fitted the lines in CLASS" (3.1 Large-scale view of the MDCs)
- **Livedata and Gridzilla** : MOPRA data reduction  
  > "the data reduction was performed with Livedata and Gridzilla tools" (2.2 MOPRA observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mean Jeans mass | 0.65 | not stated | Msun | 5 | We obtained a mean Jeans mass <M Jeans >=0.65 M ⊙ and a mean Jeans length of < λ Jeans >=0.03 pc. |
| Mean Jeans length | 0.03 | not stated | pc | 5 | mean Jeans length of < λ Jeans >=0.03 pc |
| Core masses | 0.2 to 2.6 | not stated | Msun | 4 | The mass of the cores ranges between 0.2 M ⊙ and 2.6 M ⊙ for a mean size of ∼0.008 pc. |
| 5σ mass sensitivity | 0.11 | not stated | Msun | 4 | down to our detection limit of 0.11 M ⊙ corresponding to a 5σ level |
| Number of compact cores | 8 (3 associated with MDCs) | not stated | dimensionless | 4 | In total we find 8 cores located in the vicinity of the MDCs #16, #26 and #45. |
| Mean magnetic field to support MDCs | ~1.2 | not stated | mG | 6 | The mean value of ∼1.2 mG that we obtain |
| Subvirial alpha_vir | ~0.35 | not stated | dimensionless | 2 | sub-virialized (α vir ∼0.35 for #16, #27, and #35) |

## Qualitative findings

- Most continuum emission in six MDCs is resolved out by the interferometer  
  > "The emission is completely resolved out in the MDCs #11, #17, #21, #27, #35, and #44" (3.3 ALMA view of the massive dense cores)

## Claim tuples

- H: Starless MDCs host high-mass pre-stellar cores (quasi-static models) | E: ALMA 1.4 mm continuum of 9 MDCs | R: Only low-mass cores (max 2.6 Msun) found | F: No high-mass pre-stellar cores; quasi-static models not supported | **supported**
- H: MDCs fragment as predicted by competitive accretion | E: Compare detected cores with Jeans fragmentation expectation | R: Few fragments, ~two orders of magnitude below prediction | F: Incompatible unless fragmentation has not yet begun | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Interferometer filters out most emission; short-spacing data needed  
  > "Combination with short-spacing observations is therefore mandatory to investigate the exact cloud structure of starless MDCs." (4.1 Comparison with models)
- Caveat (inferred, ours): Very short integrations (~1.4 min) and missing short spacings make non-detection of fragmentation ambiguous
- Caveat (inferred, ours): Masses depend on assumed T_dust and kappa
- Caveat (inferred, ours): Virial analysis uses single-dish line widths with assumed density index
- Caveat (inferred, ours): Dust temperature taken from Herschel at coarse resolution

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters (cell, image size, masks, threshold)
- Missing: Getsources settings
- Missing: Tigé et al. 2017 MDC parameters needed as input
- Missing: MOPRA data access details
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, ALMA project code given and recipe broadly described, but imaging and extraction details are missing.
- Rediscovery candidate: no, Key imaging and extraction parameters missing; results depend on external Herschel-derived inputs.

## Links

- Method: Men’shchikov et al. 2012 (Getsources extraction tool)
- Companion: Tigé et al. 2017 (Herschel/HOBYS MDC sample and properties)
- Companion: Motte et al. 2018 (continuum concatenation approach)
- Related: Herschel/HOBYS
- Related: MALT90

## Checks

```json
{
 "quotes": 58,
 "quotes_ok": 58,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 43,
  "rate": 0.551
 },
 "evidence_ok": true
}
```
