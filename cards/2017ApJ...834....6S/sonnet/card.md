# Merger-induced Shocks in the Nearby LIRG VV 114 through Methanol Observations with ALMA

`2017ApJ...834....6S` | The Astrophysical Journal 2017 | first author: Saito, Toshiki | arXiv: 1611.01156 | DOI: 10.3847/1538-4357/834/1/6

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, astrochemistry
- Question: Does CH3OH trace kpc-scale merger-induced shocks at the Overlap region of VV 114, and how does the CH3OH abundance vary along the filament?  
  > "we present multiple CH$_3$OH line observations toward the nearby merging galaxy VV 114, which are follow-up observations of our previous CH$_3$OH (2$_K$–1$_K$) detection at Overlap" (INTRODUCTION)
- Target **VV 114**: coordinates _not stated_; z/distance 87 Mpc (1'' = 420 pc)  
  > "We assumed $H_0$ = 70 km s$^{-1}$ Mpc$^{-1}$, $\Omega_{\rm M}$ = 0.3, $\Omega_{\rm \Lambda}$ = 0.7 (1$''$ = 420 pc) throughout this paper." (INTRODUCTION); distance from cosmology with H0 = 70, OmegaM = 0.3, OmegaL = 0.7  
  > "We assumed $H_0$ = 70 km s$^{-1}$ Mpc$^{-1}$, $\Omega_{\rm M}$ = 0.3, $\Omega_{\rm \Lambda}$ = 0.7 (1$''$ = 420 pc) throughout this paper." (INTRODUCTION)

## Data provenance

- ALMA projects: 2013.1.01057.S, 2011.0.00467.S
- bands: Band 3 and Band 4  
  > "We observed VV 114 using Band 3 and Band 4 of ALMA with the spectral scan mode" (2 OBSERVATIONS AND DATA OVERVIEW)
- frequencies and spectral setup: Scan covering 84-111 and 127-154 GHz with eight tunings; spectral windows 1.875 GHz wide with 1.938 MHz resolution  
  > "The correlator was configured to cover 84 - 111 GHz and 127 - 154 GHz using eight tunings." (2 OBSERVATIONS AND DATA OVERVIEW); "The spectral window has a bandwidth of 1.875 GHz with 1.938 MHz resolution" (2 OBSERVATIONS AND DATA OVERVIEW)
- continuum bandwidth: _not stated_
- arrays: 12 m antennas  
  > "Thirty-one to thirty-eight (thirty-six) 12 m antennas with the projected baseline length of 19 - 778 m (21 - 539 m) were assigned for the Band 3 (Band 4) observations." (2 OBSERVATIONS AND DATA OVERVIEW)
- configurations: _not stated_
- baselines: 19-778 m (Band 3); 21-539 m (Band 4)  
  > "Thirty-one to thirty-eight (thirty-six) 12 m antennas with the projected baseline length of 19 - 778 m (21 - 539 m)" (2 OBSERVATIONS AND DATA OVERVIEW)
- angular resolution: 1.47 x 1.12 arcsec (2_K-1_K); 1.60 x 1.04 arcsec (3_K-2_K)  
  > "1.47 $\times$ 1.12 | $-$88.8 | 50 | 0.37" (Table 1)
- max recoverable scale: 18'' (Band 3), 13'' (Band 4)  
  > "the maximum recoverable scale of the assigned configuration for the Band 3 and Band 4 observations (18$''$ and 13$''$, respectively)" (2 OBSERVATIONS AND DATA OVERVIEW)
- sensitivity: rms 0.37 mJy/beam (50 km/s) for 2_K-1_K; 0.69 mJy/beam (20 km/s) for 3_K-2_K  
  > "1.60 $\times$ 1.04 | +67.8 | 20 | 0.69" (Table 1)
- time on source: 47.4 min (Band 3), 20.0 min (Band 4)  
  > "The total on-source time of the Band 3 and Band 4 observations are 47.4 min. and 20.0 min., respectively." (2 OBSERVATIONS AND DATA OVERVIEW)
- observing dates: Band 3: 2014 July 3, 4, 2015 June 11; Band 4: 2015 May 25  
  > "were obtained on 2014 July 3, 2014 July 4, and 2015 June 11" (2 OBSERVATIONS AND DATA OVERVIEW)
- pi or archival as stated: _not stated_
- Line: CH3OH 2_K-1_K (blended) (96.74 GHz (obs ~94.84 GHz))
- Line: CH3OH 3_K-2_K (blended) (145.09-145.14 GHz (obs ~142.24 GHz))
- Other facility **ALMA Cycle 0 data (2011.0.00467.S)**: Additional CH3OH 2_K-1_K data combined to increase sensitivity  
  > "we combined the cycle 0 CH$_3$OH (2$_K$–1$_K$) data (ID: 2011.0.00467.S) in order to increase the sensitivity" (2 OBSERVATIONS AND DATA OVERVIEW)
- External data: 880 um dust continuum map and N_H2 from previous ALMA observations  
  > "Molecular hydrogen column density derived from the 880 $\mu$m dust continuum emission (cite: Saito15)." (Table 2) [from (cite: Saito15)]
- External data: 110 GHz continuum used for SFR surface density  
  > "Star formation rate surface density derived from the 110 GHz continuum emission (cite: Saito15)." (Table 2) [from (cite: Saito15)]
- External data: Hot-core parameters for NGC 2264 CMM3 (single-dish CH3OH intensity, mass, distance)  
  > "We used a single-dish measurement toward one of the local hot-cores NGC 2264 CMM3" (DISCUSSION & SUMMARY) [from (cite: Watanabe15)]
- External data: Transition parameters (line strengths, energies) from Splatalogue and CDMS  
  > "We take the transition parameters necessary for calculating the equation (Table [1](#table_1)) from Splatalogueand the Cologne Database for Molecular Spectroscopy" (4 LTE CALCULATION) [from (cite: Muller01; Muller05)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Neptune and Uranus; cycle 0 data re-calibrated with Butler-JPL-Horizons 2012 model  
  > "Neptune and Uranus were used for the flux calibration of the both bands." (2 OBSERVATIONS AND DATA OVERVIEW); "we re-calibrated the cycle 0 data using Butler-JPL-Horizons 2012 model" (2 OBSERVATIONS AND DATA OVERVIEW)
- flux scale uncertainty: 5% for Band 3 and Band 4  
  > "The systematic error of absolute flux scaling factor using a solar system object is 5% for Band 3 and Band 4" (2 OBSERVATIONS AND DATA OVERVIEW)
- self calibration: _not stated_

### Imaging

- task: CASA  
  > "The data reduction, calibration, and imaging were carried out using `CASA` (cite: McMullin07)." (2 OBSERVATIONS AND DATA OVERVIEW)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "All maps are reconstructed with the natural weighting to minimize noise rms levels." (2 OBSERVATIONS AND DATA OVERVIEW)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: subtracted in the uv-plane  
  > "continuum emission was subtracted in the $uv$-plane" (2 OBSERVATIONS AND DATA OVERVIEW)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Cycle 0 and Cycle 2 CH3OH (2_K-1_K) data combined before imaging  
  > "Before imaging, we combined the cycle 0 CH$_3$OH (2$_K$–1$_K$) data (ID: 2011.0.00467.S)" (2 OBSERVATIONS AND DATA OVERVIEW)
- smoothing: _not stated_
- final beam: 1.47x1.12 arcsec PA -88.8 (2_K-1_K); 1.60x1.04 arcsec PA +67.8 (3_K-2_K)  
  > "1.47 $\times$ 1.12 | $-$88.8" (Table 1)
- final rms: 0.37 mJy/beam (2_K-1_K, 50 km/s); 0.69 mJy/beam (3_K-2_K, 20 km/s)  
  > "Noise rms in the data which have velocity resolution of $\delta v$." (Table 1)

### Inherited from earlier work

- Other imaging properties to be detailed in a forthcoming paper  
  > "Other imaging properties are listed in Table [1](#table_1), and will be introduced in detail by Saito et al. in preparation." (2 OBSERVATIONS AND DATA OVERVIEW) [from Saito et al. in preparation]
- H2 column density from 880 um continuum following Scoville formulation  
  > "to derive molecular gas mass (i.e., $N_{\rm H_2}$) using the formulation described in (cite: Scoville15)" (4 LTE CALCULATION) [from (cite: Scoville15)]
- Free-free flux to SFR conversion  
  > "applied the free-free flux to SFR conversion (cite: Yun&Carilli02)" (DISCUSSION & SUMMARY) [from (cite: Yun&Carilli02)]
- Blended-line flux equation with least squares  
  > "the CH$_3$OH flux can be expressed by using the least squares method with the following equation (cite: Martin06a; Watanabe14)" (4 LTE CALCULATION) [from (cite: Martin06a; Watanabe14)]

### Not stated but needed to reproduce (our reading)

- Phase centre/coordinates of VV 114 and pointing
- CASA version and whether pipeline or manual calibration was used
- Line-free channels and continuum-subtraction fit order
- Image size, cell size, cleaning threshold, masking
- Primary beam correction details
- Details of the 880 um-to-N_H2 conversion (opacity, gas-to-dust ratio) and exact map used
- Aperture positions are in Table 2 but integration/velocity ranges for fluxes not given
- Fitting uncertainties handling and partition function source for the rotation diagram
- Cycle 0 configuration and observing details

## Analysis recipe

1. **Image CH3OH cubes**: CASA imaging with natural weighting; Cycle 0 and Cycle 2 2_K-1_K data combined; uv continuum subtraction; cubes at 50 and 20 km/s resolution  
  > "We made the data cubes with a velocity resolution of 50 km s$^{-1}$ ($\sim$ 14.4 MHz) for CH$_3$OH (2$_K$–1$_K$) and 20 km s$^{-1}$ ($\sim$ 9.8 MHz) for CH$_3$OH (3$_K$–2$_K$)." (2 OBSERVATIONS AND DATA OVERVIEW)
   - software: CASA
   - fitting: _not stated_
   - validation: Checked blending with other species via Splatalogue and literature line surveys  
  > "We checked possible blending with other species using the molecular line database Splatalogue" (RESULTS)
2. **Rotation diagram of blended CH3OH lines**: Least-squares fit of blended A- and E-type transitions in eleven 3'' apertures to derive Trot and N_CH3OH  
  > "We performed the calculation for eleven apertures of 3$''$ diameter along the filament" (4 LTE CALCULATION)
   - parameter: Trot = 7.4 K adopted for regions without 2_K-1_K detection  
  > "we used $T_{\rm rot}$ = 7.4 K to derive $N_{\rm CH_3OH}$" (4 LTE CALCULATION)
   - assumption: LTE, optically thin, same beam-averaged column density for A and E types  
  > "By assuming that both types of CH$_3$OH have the same beam-averaged column density" (4 LTE CALCULATION)
   - fitting: least squares  
  > "can be expressed by using the least squares method" (4 LTE CALCULATION)
   - validation: Tested effects of higher Trot and c-C3H2 contamination; trend robust  
  > "For both cases, $X_{\rm CH_3OH}$ will decrease by a few tens of % around the eastern nucleus, so that our discussion and conclusion do not change." (4 LTE CALCULATION)
3. **Derive CH3OH abundance X_CH3OH**: Divide N_CH3OH by N_H2 from 880 um dust continuum  
  > "we divided the $N_{\rm CH_3OH}$ by the H$_2$ column density ($N_{\rm CH_3OH}/N_{\rm H_2}$ = $X_{\rm CH_3OH}$)" (4 LTE CALCULATION)
   - assumption: Tdust = 25 K; N_H2 tracer has same beam filling factor  
  > "Assuming a constant dust temperature ($T_{\rm dust}$) of 25 K, we derived $X_{\rm CH_3OH}$ along the filament." (4 LTE CALCULATION)
   - fitting: _not stated_
   - validation: X only increases ~2 times at most for Trot 7.4-14.8 K and Tdust 25-50 K  
  > "$X_{\rm CH_3OH}$ only increases $\sim$ 2 times at most when adopting $T_{\rm rot}$ = 7.4–14.8 K and $T_{\rm dust}$ = 25–50 K" (4 LTE CALCULATION)
4. **Compare X_CH3OH with SFR surface density**: Sigma_SFR from 110 GHz free-free continuum; correlation with X_CH3OH  
  > "We employed 110 GHz continuum (cite: Saito15) assuming that free-free (bremsstrahlung) emission dominates" (DISCUSSION & SUMMARY)
   - assumption: Free-free emission dominates 110 GHz  
  > "assuming that free-free (bremsstrahlung) emission dominates" (DISCUSSION & SUMMARY)
   - fitting: _not stated_
   - validation: _not stated_
5. **Estimate hot-core contribution**: Scale local hot-core CH3OH intensities (NGC 2264 CMM3, OMC-1, Sgr B2) to Region 6 gas mass at 87 Mpc  
  > "To account for all the molecular gas mass of Region 6 ($\sim$ 8.1 $\times$ 10$^8$ $M_{\odot}$) of VV 114, we need $\sim$ 2.0 $\times$ 10$^7$ CMM3." (DISCUSSION & SUMMARY)
   - assumption: All gas mass in Region 6 is in hot cores (upper limit)  
  > "we assumed an extreme case that all gas masses contained in Region 6 are associated to hot-cores" (DISCUSSION & SUMMARY)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Data reduction, calibration and imaging  
  > "The data reduction, calibration, and imaging were carried out using `CASA` (cite: McMullin07)." (2 OBSERVATIONS AND DATA OVERVIEW)
- **Splatalogue** : Line blending check and transition parameters  
  > "We checked possible blending with other species using the molecular line database Splatalogue" (RESULTS)
- **CDMS** : Transition parameters for CH3OH  
  > "the Cologne Database for Molecular Spectroscopy (cite: Muller01; Muller05)" (4 LTE CALCULATION)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CH3OH (2_K-1_K) integrated intensity | 0.91 | 0.11 | Jy km/s | 1 | The total CH$_3$OH (2$_K$–1$_K$) and CH$_3$OH (3$_K$–2$_K$) integrated intensities are 0.91 $\pm$ 0.11 and 2.31 $\pm$ 0.18 Jy km s$^{-1}$, respectively. |
| CH3OH (3_K-2_K) integrated intensity | 2.31 | 0.18 | Jy km/s | 1 | The total CH$_3$OH (2$_K$–1$_K$) and CH$_3$OH (3$_K$–2$_K$) integrated intensities are 0.91 $\pm$ 0.11 and 2.31 $\pm$ 0.18 Jy km s$^{-1}$, respectively. |
| Average Trot (Regions 5-8) | 7.4 | 0.5 | K | 2 | The average $T_{\rm rot}$ is 7.4 $\pm$ 0.5 K for regions detected in both blended CH$_3$OH sets |
| Average N_CH3OH | 2.3e14 | 1.0e14 | cm^-2 | 2 | The average $N_{\rm CH_3OH}$ is (2.3 $\pm$ 1.0) $\times$ 10$^{14}$ cm$^{-2}$ |
| X_CH3OH at Region 6 | 7.2e-9 | 3.6e-9 | dimensionless | 3 | 6 / 16.9465 / -17.5073 / 0.51 $\pm$ 0.09 / 1.20 $\pm$ 0.12 / 7.8 $\pm$ 0.9 / 3.2 $\pm$ 1.6 / 7.5 $\pm$ 0.4 / 4.5 $\pm$ 0.5 / 7.2 $\pm$ 3.6 |
| Correlation coefficient log Sigma_SFR vs X_CH3OH | -0.94 | not stated | dimensionless | 4 | with the correlation coefficient of $-$0.94 |
| Hot-core contribution to Region 6 CH3OH(2-1) using CMM3 | 0.5 | not stated | % | 5 | This is 0.5% of the observed CH$_3$OH (2$_K$–1$_K$) flux at Region 6 |

## Qualitative findings

- CH3OH emission forms a ~3 kpc filament across the progenitor disks, strongest at Overlap and only marginal at the nuclei  
  > "The strongest peak is located at Overlap, whereas the emission is only marginally detected in the stellar nuclei" (RESULTS)

## Claim tuples

- H: Kpc-scale merger-induced shocks enhance CH3OH abundance at Overlap | E: Rotation-diagram LTE abundance mapping and hot-core contribution estimates | R: X_CH3OH peaks at Overlap (~8e-9), an order of magnitude above the eastern nucleus; hot-core contribution small (0.5-23%) | F: Kpc-scale shocks from galaxy collision are the likely explanation | **supported**
- H: Low nuclear CH3OH is due to star formation/AGN effects | E: Compare X_CH3OH with Sigma_SFR | R: Anticorrelation with coefficient -0.94 | F: Photodissociation or inefficient production on grains suppresses CH3OH in nuclei | **partially**

## Reasoning

- Why this data: Spectral scan follow-up since earlier observations covered only ten molecular lines  
  > "since we were only able to observe ten molecular lines, the chemical composition in the filament is not fully understood" (INTRODUCTION)
- Why this method: _not stated_
- Alternative: Hot-core-like environments rejected as dominant source of CH3OH at Overlap  
  > "the contribution from hot-cores at Region 6 is still small (0.7-0.9%, 6.2%, and 23.5%, respectively)" (DISCUSSION & SUMMARY)
- How they decided it was enough: _not stated_
- Limitation (authors): LTE and optically thin assumptions; higher-J observations needed for non-LTE; K-ladder blending  
  > "higher-$J$ CH$_3$OH observations are required to address more realistic, finite optical depth and non-LTE excitation conditions" (DISCUSSION & SUMMARY)
- Limitation (authors): Possible c-C3H2 contamination of 3_K-2_K  
  > "so CH$_3$OH (3$_K$–2$_K$) intensity might be slightly overestimated" (RESULTS)
- Caveat (inferred, ours): Trot of ~7 K from heavily blended lines at coarse velocity resolution is poorly constrained
- Caveat (inferred, ours): Single constant Tdust of 25 K and uncertain dust-to-H2 conversion
- Caveat (inferred, ours): Shock interpretation is indirect; no independent shock tracer
- Caveat (inferred, ours): Beam filling factor ignored

## Reproducibility

- Data public (paper): Both ALMA projects cited with ADS/JAO.ALMA codes  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00467.S and ADS/JAO.ALMA#2013.1.01057.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Full imaging parameters (deferred to a paper in preparation)
- Missing: 880 um and 110 GHz maps from Saito et al. 2015
- Missing: Line-free channel and flux integration definitions
- Data volume (inferred): ~20-50 GB
- Score (inferred): 3/5, Public data and clear LTE recipe, but imaging parameters and N_H2/SFR inputs rely on other papers.
- Rediscovery candidate: no, Key inputs (880 um N_H2, 110 GHz SFR maps) come from a previous paper and imaging details are missing.

## Links

- Method: (cite: Scoville15) (H2 column density from 880 um dust continuum)
- Method: (cite: Goldsmith&Langer99) (rotation diagram method)
- Method: (cite: Yun&Carilli02) (free-free to SFR conversion)
- Companion: (cite: Saito15) (Previous ALMA observations of VV 114 providing continuum and line data)
- Companion: (cite: Iono13) (Earlier ALMA Cycle 0 observations of VV 114)

## Checks

```json
{
 "quotes": 68,
 "quotes_ok": 68,
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
  "facts": 79,
  "stated": 52,
  "rate": 0.658
 },
 "evidence_ok": true
}
```
