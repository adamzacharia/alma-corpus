# ALMA Observations of Warm Dense Gas in NGC 1614—Breaking of the Star Formation Law in the Central Kiloparsec

`2015ApJ...799...11X` | The Astrophysical Journal 2015 | first author: Xu, C. K. | arXiv: 1411.1111 | DOI: 10.1088/0004-637X/799/1/11

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation, agn_and_quasars
- Question: What is the structure of warm dense gas and dust in the central kpc of the LIRG NGC 1614, is there a Compton-thick AGN, and does the Kennicutt-Schmidt law hold on ~100 pc scales?  
  > "In order to study the warm dense gas in nuclear regions of (U)LIRGs, we observed the CO (6-5) line emission (rest-frame frequency = 691.473 GHz) and associated dust continuum emission" (Introduction)
- Target **NGC 1614**: coordinates RA 04h34m00.03s, Dec -08d34m45.1s (8.4 GHz nucleus)  
  > "a local luminous infrared galaxy (LIRG) at a distance of 67.8 Mpc ($\rm 1\ensuremath{''} = 329\; pc$)" (abstract); "$\rm 04{^h}34{^m}00{s}03$" (Table 2); z/distance 67.8 Mpc; system velocity 4723 km/s  
  > "a local luminous infrared galaxy (LIRG) at a distance of 67.8 Mpc ($\rm 1\ensuremath{''} = 329\; pc$)" (abstract); "$\rm 04{^h}34{^m}00{s}03$" (Table 2); distance from _not stated_

## Data provenance

- ALMA projects: _none stated_
- bands: Band 9 (435 um)  
  > "using the Band 9 receivers of ALMA in the time division mode (TDM; velocity resolution: 6.8 km sec$^{-1}$)" (2 Observations)
- frequencies and spectral setup: 4 SPWs centred at 680.539, 682.308, 676.826, 678.764 GHz, 2 GHz each  
  > "The four basebands (i.e. “Spectral Windows”, hereafter SPWs) were centered at the sky frequencies of 680.539, 682.308, 676.826 and 678.764 GHz, respectively, each with a bandwidth of 2 GHz." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: extended & compact (E&C), up to 27 antennae  
  > "Observations were carried out in the extended & compact (E&C) configuration using up to 27 antennae" (2 Observations)
- baselines: max baseline 402 m  
  > "| X49990a_X505 | 2012/08/13 | 11:31:46 – 12:52:33 | E&C | 23 | 402 | 24.7 | 537 |" (Table 1)
- angular resolution: 0.26" x 0.20", PA 280 deg  
  > "having FWHMs of $\rm 0.26\ensuremath{''}\times 0.20\ensuremath{''}$, corresponding to physical scales of $\rm 86\; pc \times 66\; pc$, and a P.A. of $280^\circ$" (2 Observations)
- max recoverable scale: ~3"  
  > "emission features larger than $\sim 3\ensuremath{''}$ are poorly sampled because of limited uv-coverage for short baselines" (2 Observations)
- sensitivity: 8.0 mJy/beam per 6.8 km/s channel; continuum 0.6 mJy/beam; moment-0 0.90 Jy/beam km/s  
  > "1-$\sigma$ rms noise of $\rm 8.0\; mJy\; beam^{-1}$ per $\rm 6.8\; km\; s^{-1}$, and for the continuum it is $\rm 0.6\; mJy\; beam^{-1}$" (2 Observations)
- time on source: 50.4 minutes  
  > "The total on-target integration time was 50.4 minutes." (2 Observations)
- observing dates: 2012/08/13 and 2012/08/28  
  > "| X4b58a4_X1ee | 2012/08/28 | 08:58:50 – 10:23:37 | E&C | 27 | 402 | 24.7 | 756 |" (Table 1)
- pi or archival as stated: _not stated_
- Line: CO 6-5 (691.473 GHz)
- Line: H13CN 8-7 (690.552 GHz)
- Other facility **Herschel SPIRE (FTS and photometer)**: total CO(6-5) flux and 350/500 um fluxes for single-dish comparison  
  > "using SPIRE photometer fluxes $\rm f_{350\mu m, SPIRE}=1916\pm 134\; mJy$ and $\rm f_{500\mu m, SPIRE}=487\pm 34\; mJy$" (3.2 The 435 um Continuum Emission)
- Other facility **VLA/MERLIN 8.4 GHz radio and HST NICMOS Pa-alpha**: SFR tracers (thermal/nonthermal radio) from Herrero-Illana2014  
  > "we compare the CO (6-5) contours with the radio continuum at 8.4 GHz (beam = $\rm 0.41\ensuremath{''}\times 0.26\ensuremath{''}$, (cite: Herrero-Illana2014))" (4.2)
- External data: Herschel CO(6-5) flux 1423±126 Jy km/s  
  > "Herschel measurement of the integrated CO (6-5) line emission of NGC 1614 ($\rm 1423\pm 126\; Jy\; km\; s^{-1}$ within a beam of $\sim 30\ensuremath{''}$" (3.1) [from (cite: vanderWerf2010; Lu2014)]
- External data: 8.4 GHz radio maps and thermal/nonthermal method  
  > "Following (cite: Herrero-Illana2014), the thermal radio emission is estimated using a high-resolution, extinction-corrected Pa-${\alpha}$ map" (4.2) [from (cite: Herrero-Illana2014)]
- External data: CO(2-1) ring flux 65.4±6.9 Jy km/s and H2 mass 10^8.97 Msun  
  > "the total $\rm H_2$ mass in the ring is $\rm M_{H_2} = 10^{8.97}\; M_\ensuremath{\odot}$ (for D=67.8 Mpc)" (4.2) [from (cite: Konig2013)]
- External data: Gas-to-dust ratio 100 for 12+log(O/H)>8.5  
  > "for galaxies with $\rm 12+log(O/H)> 8.5$, the gas-to-dust ratio is 100 with a 1-$\sigma$ uncertainty of $\sim 0.2$ dex" (3.2) [from (cite: Remy-Ruyer2014)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.1.0  
  > "The final data reduction was done using CASA 4.1.0." (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ceres  
  > "Observations of the minor planet Ceres were made for the flux calibration." (2 Observations)
- flux scale uncertainty: 17%  
  > "The error in the flux calibration was estimated to be 17%." (2 Observations)
- self calibration: phase and amplitude self-cal done  
  > "Both phase and amplitude self-calibrations have been carried out." (2 Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs weighting (robust not stated)  
  > "Images were cleaned using Briggs weighting." (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: CASA UVcontsub; continuum from other 3 SPWs  
  > "The continuum subtraction was carried out using the CASA task *UVcontsub*." (2 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.26" x 0.20", PA 280 deg  
  > "The synthesized beams of these maps are nearly identical" (2 Observations)
- final rms: 8.0 mJy/beam per 6.8 km/s; 0.6 mJy/beam continuum  
  > "has 1-$\sigma$ rms noise of $\rm 0.90\;  Jy\; beam^{-1} \; km\; s^{-1}$" (2 Observations)

### Inherited from earlier work

- Thermal/nonthermal radio decomposition method  
  > "Following (cite: Herrero-Illana2014), the thermal radio emission is estimated using a high-resolution, extinction-corrected Pa-${\alpha}$ map" (4.2) [from (cite: Herrero-Illana2014)]
- SFR calibrations from radio luminosities  
  > "two formulae given in (cite: Murphy2012), respectively" (4.2) [from (cite: Murphy2012)]
- CO SLED LVG modelling procedure  
  > "adopting a similar procedure to that in (cite: Kamenetzky2012)" (4.3) [from (cite: Kamenetzky2012)]

### Not stated but needed to reproduce (our reading)

- Briggs robust value, cell size, image size, clean threshold and masks
- Line-free channels and continuum channel ranges for UVcontsub
- Bandpass/phase calibrator details besides QSO 0423-013, self-cal solution intervals
- Aperture definitions for channel-by-channel flux photometry
- Herschel PACS/SPIRE SED photometry (Chu et al. in prep) and Lu2014b CO fluxes unpublished
- Knot identification and fitting procedure for the seven knots
- Details of cell-by-cell regridding and smoothing to the radio maps
- Pipeline vs manual calibration

## Analysis recipe

1. **Image CO(6-5) cube and continuum**: CASA reduction, Briggs cleaning, self-cal, UVcontsub; SPW-0 cube, continuum from other 3 SPWs  
  > "The continuum was estimated using data in the other 3 SPWs." (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure total CO(6-5) flux and compare with Herschel**: Sum of aperture photometry of individual channels; ratio to Herschel flux  
  > "which is derived from the sum of the aperture photometry of individual channels (centered on the emission features for each given channel)" (3.1)
   - fitting: _not stated_
   - validation: _not stated_
3. **Dust mass and gas mass in the central region; AGN limit**: 2-graybody SED fit for total dust mass, scale by ALMA/SPIRE 435 um flux ratio, gas-to-dust 100; nuclear 3-sigma continuum limit gives N_H upper limit  
  > "A least-squares fit to the IR SED by a 2-graybody model, with the emissivity spectral index $\rm \beta = 2$ for both components" (3.2)
   - assumption: Same cold dust temperature (35 K) in central region; M_gas/M_dust = 10^2.0±0.2  
  > "If dust in the central region has the same $\rm T_C$" (3.2)
   - fitting: least-squares 2-graybody  
  > "A least-squares fit to the IR SED by a 2-graybody model, with the emissivity spectral index $\rm \beta = 2$ for both components, yields a total dust mass" (Results, The 435 μm Continuum Emission)
   - validation: Compared with CO(2-1) gas mass; beta free and DL07 fits give similar results  
  > "Fits by 2-graybody models with $\rm \beta$ as a free parameter or by the model of (cite: DL07) yield very similar results." (3.2)
4. **Derive Sigma_gas and Sigma_SFR and test Kennicutt-Schmidt law**: Sigma_gas from CO(6-5) via calibrated relation; Sigma_SFR from thermal/nonthermal 8.4 GHz via Murphy2012; Spearman rank correlations in 3x3 pixel cells  
  > "individual cells ($\rm 3\time 3$ pixels, pixel=0$''$089) in the ring" (4.2)
   - software: Starburst99
   - assumption: X_CO = 3e20; CO(6-5)/CO(2-1) brightness temperature ratio 0.72; T_e=1e4 K; alpha_nth=1.2  
  > "assuming a brightness temperature ratio of 0.72 between CO (6-5) and CO (2-1)" (4.2)
   - fitting: _not stated_
   - validation: Compared with Kennicutt1998b relation  
  > "the $\rm \Sigma_{SFR}$ vs. $\rm \Sigma_{Gas}$ relation is systematically above that for local starbursts (cite: Kennicutt1998b), indicating a higher star formation efficiency (SFE)." (Discussion, Relation Between Warm Dense Gas and Star Formation)
5. **CO SLED modeling of NGC 1614 and NGC 34**: Two-component RADEX LVG fits of Herschel SLED  
  > "we modeled the observed CO SLEDs using simple two-component RADEX large velocity gradient (LVG) radiative transfer models" (4.3)
   - software: RADEX
   - fitting: _not stated_
   - validation: admitted degeneracy  
  > "Admittedly, results from such model fittings suffer significant degeneracy between parameters (cite: Rosenberg2014a)." (Discussion, NGC 1614 and NGC 34: A Tale of Two LIRGs)

## Software

- **CASA** 4.1.0: data reduction, imaging, UVcontsub  
  > "The final data reduction was done using CASA 4.1.0." (2 Observations)
- **Starburst99** v7.0.0: stellar population models for Pa-alpha extinction correction  
  > "we used Starburst99 (v7.0.0; (cite: Leitherer1999)) to generate a stellar population synthesis model" (Appendix)
- **RADEX** : LVG modelling of CO SLEDs  
  > "simple two-component RADEX large velocity gradient (LVG) radiative transfer models (cite: vanderTak2007)" (4.3)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(6-5) integrated flux | 898 | ±153 | Jy km/s | 2 | integrated flux of $\rm f_{CO~(6-5)} = 898\; (\pm 153)
\; Jy\; km\; s^{-1}$ |
| ALMA/Herschel CO(6-5) flux ratio | 0.63 | ±0.12 | dimensionless | 2 | yields an interferometer-to-single-dish flux ratio of $0.63\pm 0.12$ |
| 435 um continuum flux density | 269 | ±46 | mJy | 1 | $\rm f_{435\mu m}=269\pm 46\; mJy$ |
| ALMA/SPIRE 435 um flux ratio | 0.32 | ±0.06 | dimensionless | 3 | single-dish flux ratio of $\rm 0.32\pm 0.06$ |
| Total dust mass | 10^7.60 | ±0.07 dex | Msun | 3 | $\rm M_{dust, total} = 10^{7.60\pm
    0.07}\; M_\ensuremath{\odot}$ with a cold dust temperature of $\rm T_C = 35\pm 2
  K$ |
| Central gas mass from dust | 10^9.11 | ±0.30 dex | Msun | 3 | $\rm M_{gas, cent} = 10^{9.11\pm 0.30}\;
  M_\ensuremath{\odot}$ |
| Nuclear N_H 3-sigma upper limit | 10^23.1 | ±0.3 dex | cm^-2 | 3 | $\rm
  N_{H} = 10^{23.1\pm 0.3}\; cm^{-2}$ |
| Median CO(6-5)/CO(2-1) brightness temperature ratio | 0.72 | not stated | dimensionless | 4 | with a median brightness temperature ratio of 0.72 |
| Spearman correlation Sigma_SFR,nth vs Sigma_gas | rho = 0.81, p = 1.6e-5 | not stated | dimensionless | 4 | ($\rm \rho =0.81$ and $\rm p = 1.6\times 10^{-5}$) |
| Warm component kinetic temperature NGC 1614 | 445 | not stated | K | 5 | the kinetic temperature of the warm component in NGC 34 (890 K) is 2 times higher than that of NGC 1614 (445 K) |

## Qualitative findings

- CO(6-5) and continuum form a clumpy circum-nuclear ring (100–350 pc) with no detected nucleus  
  > "both showing a ring configuration without a detectable nucleus" (3.1)

## Claim tuples

- H: Is there a Compton-thick AGN in NGC 1614? | E: Nuclear non-detection limits in CO(6-5) and 435 um continuum converted to N_H | R: N_H < 10^23.1 cm^-2 (3 sigma) | F: Compton-thick AGN ruled out with relatively high confidence | **supported**
- H: Does the Kennicutt-Schmidt law hold at ~100 pc in NGC 1614? | E: Compare Sigma_gas from CO(6-5) with Sigma_SFR from radio | R: Weak correlation with thermal and total radio; nucleus SFR/gas ratio about an order of magnitude above nominal | F: Breakdown of the law at ~100 pc, possibly due to starburst feedback/outward propagation | **supported**
- H: Why does the nonthermal radio correlate more strongly with gas? | E: Spearman correlations; consideration of B–n and cosmic-ray heating, PDR/CDR fits | R: rho=0.81 for nonthermal; PDR with mechanical heating fits best | F: Likely magnetic field–density correlation rather than CR heating | **partially**

## Reasoning

- Why this data: Targets chosen as nearby with bright CO(6-5) in Herschel, giving ~100 pc resolution; Band 9 minimal absorption near transit  
  > "because of their close proximity ($\rm D < 85\; Mpc$) and bright CO (6-5) line fluxes" (Introduction)
- Why this method: _not stated_
- Alternative: CR-dominated region models fit the data poorly compared with PDR models with mechanical heating  
  > "PDR models with strong mechanical heating (by turbulence) provide the best fit while CDR models fit the data rather poorly" (4.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Interferometer misses extended emission; dust and gas masses are lower limits  
  > "therefore the dust and gas mass derived from these observations are lower limits" (3.2)
- Limitation (authors): CO conversion factors are very uncertain  
  > "these conversion factors are very uncertain and are the major error sources for the molecular gas mass estimates" (4.3)
- Caveat (inferred, ours): Sigma_gas calibration relies on a ring-averaged CO(6-5)/CO(2-1) ratio and Galactic X_CO
- Caveat (inferred, ours): Missing flux (37% of CO, 68% of continuum) affects surface densities and limits
- Caveat (inferred, ours): Number of cells correlated (oversampled beams), so p-values may be overstated

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: Herschel SED photometry (in prep.)
- Missing: Radio and Pa-alpha maps from Herrero-Illana2014
- Data volume (inferred): ~10-30 GB raw
- Score (inferred): 3/5, Data are Cycle-0 archival with CASA version stated, but imaging parameters and several inputs are missing.
- Rediscovery candidate: no, Key inputs (radio maps, Herschel SED photometry) come from unpublished or other works and imaging details are missing.

## Links

- Method: (cite: Herrero-Illana2014) (thermal/nonthermal radio decomposition)
- Method: (cite: Murphy2012) (SFR calibrations from radio)
- Companion: (cite: Xu2014) (ALMA CO(6-5) observation of NGC 34)
- Companion: (cite: Konig2013) (SMA CO(2-1) of NGC 1614)
- Related: GOALS

## Checks

```json
{
 "quotes": 66,
 "quotes_ok": 66,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00182.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 48,
  "rate": 0.632
 },
 "evidence_ok": true
}
```
