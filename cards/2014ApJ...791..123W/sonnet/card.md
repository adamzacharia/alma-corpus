# A Study of Dynamical Processes in the Orion KL Region Using ALMA—Probing Molecular Outflow and Inflow

`2014ApJ...791..123W` | The Astrophysical Journal 2014 | first author: Wu, Yuefang | arXiv: 1407.8370 | DOI: 10.1088/0004-637X/791/2/123

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation, astrochemistry
- Question: What are the dynamical processes (outflow origin and infall) in Orion KL, probed with high-excitation CH3CN and CH3OH lines and 1.3 mm continuum?  
  > "To examine the dynamical processes and especially to uncover the origin of the outflow in this region, observations with tracers of high excitation temperature and critical density are needed." (1 Introduction)
- Target **Orion KL (BN/KL)**: coordinates phase center RA 05h35m14.35s, Dec -05d22m35.0s  
  > "here 414 pc was adopted as the distance (cite: men07)." (3.1 Continuum); "The phase center was at R.A. = $05^{h}35^{m}14^{s}.35$ and Dec. = -$05\ensuremath{^\circ}22\ensuremath{'}35\ensuremath{''}.0$." (2 Observations); z/distance 414 pc  
  > "here 414 pc was adopted as the distance (cite: men07)." (3.1 Continuum); "The phase center was at R.A. = $05^{h}35^{m}14^{s}.35$ and Dec. = -$05\ensuremath{^\circ}22\ensuremath{'}35\ensuremath{''}.0$." (2 Observations); distance from Menten et al. 2007 (cite: men07)  
  > "here 414 pc was adopted as the distance (cite: men07)." (3.1 Continuum); "The phase center was at R.A. = $05^{h}35^{m}14^{s}.35$ and Dec. = -$05\ensuremath{^\circ}22\ensuremath{'}35\ensuremath{''}.0$." (2 Observations)

## Data provenance

- ALMA projects: 2011.0.00009.SV
- bands: Band 6 (~1.3 mm), science verification  
  > "The data used in this paper was obtained from ALMA science verification (SV) at band 6." (2 Observations)
- frequencies and spectral setup: 20 SPWs of 1.875 GHz, 3840 channels, 0.488 MHz (~0.7 km/s) resolution  
  > "There are 20 spectral windows (SPW) of 1.875 GHz wide. Each spectral window consists of 3840 channels with a spectral resolution of 0.488 MHz" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: 16 x 12 m antennas  
  > "The observations were made with 16$\times$12 m antennas of ALMA on January 20, 2012" (2 Observations)
- configurations: _not stated_
- baselines: 18 to 253 kλ  
  > "with baselines ranging from 18 to 253 k$\lambda$" (2 Observations)
- angular resolution: ~1.5 arcsec; continuum beam 1.66x1.35 arcsec  
  > "with a spatial resolution of $\sim$1.5$^{\prime\prime}$" (abstract)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 8 mJy/beam (0.07 K); line channel rms ~20 mJy/beam (0.18 K)  
  > "The typical channel rms for lines is about 20 mJy  beam$^{-1}$ per channel (0.18 K)." (2 Observations)
- time on source: _not stated_
- observing dates: January 20, 2012  
  > "on January 20, 2012" (2 Observations)
- pi or archival as stated: _not stated_
- Line: CH3CN 12(4)-11(4) (not stated)
- Line: CH3OH 8(-1,8)-7(0,7) (not stated)
- Line: 13CH3CN 12(3)-11(3), 13(3)-12(3) (not stated)
- Other facility **Spitzer/IRAC**: 3.6 and 4.5 micron images for [4.5/3.6] ratio map  
  > "Emissions of IRAC 3.6 and 4.5 $\mu$m was included in the analysis." (5 Conclusion)
- External data: H2 2.12 micron finger-like jet image  
  > "We thank Jony Bally to send us the fits data of the H$_2$ jet image" (Acknowledgements) [from Bally et al. 2011 (cite: bally11)]
- External data: Near-infrared source positions  
  > "The known infrared sources were plotted on the map and shown by crosses (cite: shu04)." (3.1 Continuum) [from (cite: shu04)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Calibrated SV data used  
  > "The synthesized images with the calibrated data were carried out by use of the Common Astronomy Software Applications (CASA) package and MIRIAD (cite: sau95)." (2 Observations)
- flux calibrator: Callisto (bandpass and flux); J0607-085 phase  
  > "Callisto was used for bandpass calibration and flux calibration while quasar J0607-085 provided the phase calibration." (2 Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "The natural-weighted beam size and the rms noise level for the continuum are 1$\ensuremath{''}.66\times1\ensuremath{''}.35$" (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: continuum from line-free channels of five highest-frequency SPWs  
  > "The continuum map was constructed from the line-free channels of the five spectral windows at highest frequency bands." (2 Observations)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.66" x 1.35", PA -20.7 deg (continuum)  
  > "1$\ensuremath{''}.66\times1\ensuremath{''}.35$ with P.A.=-20$\ensuremath{^\circ}$.7" (2 Observations)
- final rms: 8 mJy/beam continuum  
  > "8 mJy  beam$^{-1}$ (0.07 K), respectively" (2 Observations)

### Inherited from earlier work

- Infall velocity from absorption peak vs systemic velocity  
  > "The material infall velocity can be estimated as 1.5 km s$^{-1}$ from the V$_{sys}$ and V$_{obs}$ of the absorption peak (cite: wel87)." (4.3 Dynamics of Source I and the hot core MM1) [from (cite: wel87)]
- Blue profile asymmetry parameter definition  
  > "the asymmetry parameter $\delta V$ ($=V_{thick}-V_{thin})/\delta V_{thin}$) defined by (cite: mar97) was calculated" (3.4) [from (cite: mar97)]
- Infall velocity model for MM1  
  > "The infall velocity is calculated with the model of (cite: mye96)" (4.3 Dynamics of Source I and the hot core MM1) [from (cite: mye96)]

### Not stated but needed to reproduce (our reading)

- CASA/MIRIAD versions and calibration details of the SV data
- Line-free channel ranges and continuum subtraction method
- Image size, cell size, deconvolution settings and masks
- Rest frequencies and line list used for RTD (upper-level energies, column partition function)
- Source I and MM1 spectral extraction apertures
- How average high-velocity velocity was computed for dynamical age
- Source I V_sys and how T_BD, T_RD, T_D were measured

## Analysis recipe

1. **Image continuum and fit cores**: 1.3 mm continuum map; 2D Gaussian fits to cores  
  > "Two dimensional gaussian fits were made toward the continuum cores." (3.1 Continuum)
   - software: CASA, MIRIAD
   - assumption: Distance 414 pc  
  > "here 414 pc was adopted as the distance (cite: men07)." (3.1 Continuum)
   - fitting: _not stated_
   - validation: _not stated_
2. **Rotational temperatures and virial masses**: Rotation temperature diagram of 13CH3CN; Gaussian fits for Vlsr and line width; virial mass M=210 R dV^2  
  > "Only the lines not blended and with high S/N levels ($>5\sigma$) are used for RTD analysis." (3.1 Continuum)
   - assumption: LTE and optically thin lines  
  > "Assuming that the local thermodynamic equilibrium (LTE) holds and the lines are optical thin, T$_{rot}$ values are obtained" (3.1 Continuum)
   - fitting: _not stated_
   - validation: _not stated_
3. **Map high-velocity outflow and spectra**: Line profiles per core, channel maps (3 km/s), integrated high-velocity blue (-13 to -3) and red (15 to 24 km/s) CH3CN emission  
  > "the blue and red-shifted high velocity gas range from -13 to -3 km s$^{-1}$ and 15 to 24 km s$^{-1}$, respectively." (3.3)
   - fitting: _not stated_
   - validation: Absorption dips argued not due to missing flux since emission lies inside primary beam and MM2 lines are symmetric  
  > "These absorption dips are unlikely to be caused by missing flux since the emission of the KL region falls well inside the primary beam" (3.2)
4. **IRAC shock ratio map and dynamical age**: [4.5/3.6] ratio map, ratio>1.5 marks shocks; age from BN-to-center distance (8.9") over mean outflow velocity  
  > "the dynamic time is estimated to be 1280 years" (5.2.1)
   - fitting: _not stated_
   - validation: compared with numerical experiments  
  > "which is consistent with the numerical experiments of gradational slingshot (cite: chat12)" (5.2.1)
5. **Infall velocity and accretion rate**: Source I: free fall dM/dt=3Vin^3/2G; MM1: Myers et al. 1996 blue-profile model, sigma 2.7 km/s  
  > "Assuming the inflow is free fall (cite: pi14), the mass accretion rate of 1.2$\times$10$^{-3}$M$_{\ensuremath{\odot}}$/Yr can be obtained with dM/dt=3V$_{in}^3$/2G" (5.3)
   - assumption: Source I Vsys same as MM1; dip optically thick  
  > "Here we take the V$_{sys}$ of Source I as same as that of the core MM1." (5.3)
   - fitting: _not stated_
   - validation: Consistent with ~10 Msun mass of Source I  
  > "The result is consistent with the mass of Source I, which is about 10 M$_{\ensuremath{\odot}}$ (cite: tes10; liu13)." (5.3)

## Software

- **CASA** : imaging calibrated data  
  > "by use of the Common Astronomy Software Applications (CASA) package and MIRIAD (cite: sau95)" (2 Observations)
- **MIRIAD** : imaging calibrated data  
  > "by use of the Common Astronomy Software Applications (CASA) package and MIRIAD (cite: sau95)" (2 Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Source I infall velocity | 1.5 | not stated | km/s | 5 | material infall velocities of 1.5 km s$^{-1}$ and $\sim$ 0.6 km s$^{-1}$ |
| Source I mass accretion rate | 1.2e-3 | not stated | Msun/yr | 5 | 1.2$\times$10$^{-3}$M$_{\ensuremath{\odot}}$/Yr and 8.0$\times$10$^{-5}$M$_{\ensuremath{\odot}}$/Yr |
| MM1 infall velocity | ~0.6 | not stated | km/s | 5 | Taking the average value $\sim$0.6 km s$^{-1}$ as V$_{in}$ |
| MM1 mass accretion rate | 8.0e-5 | not stated | Msun/yr | 5 | the mass accretion rate of 8.0$\times$10$^{-5}$M$_{\ensuremath{\odot}}$/Yr was obtained |
| Explosion dynamical age | 1280 | not stated | yr | 4 | the dynamic time is estimated to be 1280 years |
| MM1 rotational temperature | 198 | +36/-26 | K | 2 | 198$^{+36}_{-26}$ |
| MM1 virial mass | 59 | not stated | Msun | 2 | / MM1/hot core / (2.90$\pm$0.05,3.61$\pm$0.08) / 6.6 / 1.34(0.06) / 6.18 / 5.4(0.3) / 6.5(0.3) / 198$^{+36}_{-26}$ / 59 / |
| MM1 blue/red peak ratio (CH3OH) | 2.16 | not stated | dimensionless | 5 | with a ratio of T$_B$/T$_R$=2.16 |

## Qualitative findings

- Gas consists of jet-propelled cores in the ridge and dense cores east and south, shaped like a wedge ring; outflow has multiple lobes not driven by YSOs  
  > "The outflow has multiple lobes, which may originate from an explosive ejection and is not driven by young stellar objects." (abstract)

## Claim tuples

- H: Is the Orion KL high-velocity outflow driven by a YSO? | E: Mapped high-velocity CH3CN gas and compared with YSOs, IRAC bubbles and H2 jets | R: Multiple lobes overlapping JPCs; Source I and MM1 outside or not the center; four IR bubbles around BN | F: Explosive origin centered on BN, age <=1300 yr | **partially**
- H: Is there infall toward Source I and hot core? | E: Line profile analysis (inverse P Cygni, blue profile) of CH3OH and CH3CN | R: Infall 1.5 km/s (Source I), ~0.6 km/s (MM1) | F: Gravitational collapse supports accretion formation of high-mass stars | **supported**

## Reasoning

- Why this data: High excitation temperature and critical density tracers needed  
  > "observations with tracers of high excitation temperature and critical density are needed." (1 Introduction)
- Why this method: _not stated_
- Alternative: Absorption dips attributed to missing flux or instrument effects rejected  
  > "indicating that the instrument effect cannot account for the absorption" (3.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Explosive-center identification needs more theory and observation  
  > "More theoretical analysis and observation are needed to confirm our identification." (5.2.2)
- Caveat (inferred, ours): Absorption/inverse P Cygni may be due to missing short spacings or foreground gas, not only infall
- Caveat (inferred, ours): Single-epoch data; 1280 yr age rests on projected distance and mean velocity
- Caveat (inferred, ours): Source I Vsys taken from MM1; MM3 Trot uncertain ('100?')
- Caveat (inferred, ours): Blue-profile criteria with one line pair; CH3CN may be blended/optically thick

## Reproducibility

- Data public (paper): ALMA SV data, project 2011.0.00009.SV  
  > "This paper makes use of the following ALMA data: ADS$\diagup$JAO.ALMA$\#$ 2011.0.00009.SV." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging parameters and line-free channel choices
- Missing: RTD molecular constants and aperture definitions
- Missing: Spectral extraction positions and IRAC data selection
- Data volume (inferred): ~50-100 GB (SV Band 6 spectral-line dataset, 20 SPWs)
- Score (inferred): 3/5, Public data and formulae given, but imaging and extraction details are sparse.
- Rediscovery candidate: no, Recipe incomplete for imaging and line extraction, and several results are qualitative.

## Links

- Method: Myers et al. 1996 (cite: mye96) (infall velocity model)
- Method: Mardones et al. 1997 (cite: mar97) (blue profile asymmetry parameter)
- Companion: Zapata et al. 2012 (cite: zap12) (ALMA SiO outflow in Orion KL)
- Companion: Hirota et al. 2014 (cite: hir14) (ALMA disk around Source I)
- Related: ALMA Science Verification Orion KL

## Checks

```json
{
 "quotes": 59,
 "quotes_ok": 59,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 41,
  "rate": 0.569
 },
 "evidence_ok": true
}
```
