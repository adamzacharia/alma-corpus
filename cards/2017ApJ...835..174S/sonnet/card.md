# Spatially resolved CO SLED of the Luminous Merger Remnant NGC 1614 with ALMA

`2017ApJ...835..174S` | The Astrophysical Journal 2017 | first author: Saito, Toshiki | arXiv: 1612.07326 | DOI: 10.3847/1538-4357/835/2/174

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, milky_way_ism
- Question: How do the distribution, kinematics and excitation of multiple CO transitions (J=1-0 to 6-5) differ between the starburst ring and outer disk of NGC 1614, and what heats the gas?  
  > "we present high-resolution, high-sensitivity, and $uv$-matched ALMA observations of the nearby IR-bright galaxy NGC 1614 in order to understand the distribution and kinematics of multiple CO lines and their excitation conditions in the nuclear region." (1 Introduction)
- Target **NGC 1614**: coordinates _not stated_; z/distance 67.8 Mpc (1'' = 330 pc)  
  > "NGC 1614 is a nearby LIRG (cite: Armus09) at a distance of 67.8 Mpc (1$''$ = 330 pc)." (1 Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.01172.S, 2011.0.00182.S, 2011.0.00768.S, 2013.1.00991.S
- bands: Band 3, 6, 7, 9 (12 m); Band 3 ACA  
  > "The Band 3 and Band 6 receivers were tuned to the CO (1–0) and CO (2–1) emission lines in the upper sideband, respectively." (2.1 Band 3 and Band 6 Data: 12 m Array)
- frequencies and spectral setup: four SPWs, each 1.875 GHz bandwidth and 1.129 MHz resolution (~3.0 and 1.4 km/s for Band 3 and 6)  
  > "each of the SPWs with 1.875 GHz bandwidth and 1.129 MHz resolution ($\sim$ 3.0 km s$^{-1}$ and 1.4 km s$^{-1}$ for Band 3 and Band 6, respectively)" (2.1 Band 3 and Band 6 Data: 12 m Array)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: Band 3 28-1060 m; Band 6 15-349 m  
  > "with a projected baseline length ($L_{\rm{baseline}}$) of 28 - 1060 m (C34-6 configuration)" (2.1 Band 3 and Band 6 Data: 12 m Array)
- angular resolution: all images convolved to 1.0'' x 1.0''  
  > "All of the images are convolved to the same resolution (1.0$''$ $\times$ 1.0$''$)." (2.3.1 12 m Array Data)
- max recoverable scale: 4.6'' (uv-clipped at 45 kλ); 17.6'' for ACA+12 m CO(1-0)  
  > "Since the truncated $uv$ range at 45 k$\lambda$ corresponds to the MRS of $\sim$ 4.6$''$ ($\simeq$ 1.5 kpc)" (2.3.1 12 m Array Data)
- sensitivity: _not stated_
- time on source: Band 3 16.9 min; Band 6 7.3 min per pointing (3 pointings)  
  > "($T_{\rm{integ}}$ = 7.3 min per pointing)" (2.1 Band 3 and Band 6 Data: 12 m Array)
- observing dates: Band 3 2014 Aug 30; Band 6 2014 Dec 8 in text (Table 1 gives Aug 14)  
  > "were obtained on 2014 August 30 (on-source time of $T_{\rm{integ}}$ = 16.9 min.)" (2.1 Band 3 and Band 6 Data: 12 m Array)
- pi or archival as stated: _not stated_
- Line: CO J=1-0 (115.271 GHz)
- Line: CO J=2-1 (230.542 GHz)
- Line: CO J=3-2 (345.796 GHz)
- Line: CO J=6-5 (691.473 GHz)
- Other facility **ALMA ACA**: CO (1-0) short-spacing data to recover extended emission  
  > "These ancillary data are used to increase the sensitivity and recover extended emission that we ignore due to the $uv$-clipping" (2.2.2 Band 3 Data: ACA and 12 m)
- External data: Archival calibrated Band 7 (CO 3-2) and Band 9 (CO 6-5) visibilities, originally published  
  > "the data were originally published in (cite: Sliwa14) and (cite: Xu15)." (2.2.1 Band 7 and Band 9 Data) [from (cite: Sliwa14); (cite: Xu15)]
- External data: Radial radio-to-FIR SED and Sigma_SFR derived by earlier paper  
  > "The $\Sigma_{\rm{SFR}}$ were derived by fitting the radial radio-to-FIR SEDs binned at 0.2$''$ intervals up to 1.8$''$ radius" (4.2 Comparing with the Narayanan & Krumholz Model) [from (cite: Saito15b)]
- External data: Single-dish CO fluxes used to compute recovered flux  
  > "compared to single-dish observations (cite: Sanders91; Albrecht07; Wilson08; Xu15) is very low (27 - 59 %)" (2.3.1 12 m Array Data) [from (cite: Sanders91; Albrecht07; Wilson08; Xu15)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.2.1 and 4.2.2 (ACA data)  
  > "We used `CASA` (version 4.2.1 and 4.2.2) to process the data." (2.3.2 ACA Data)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Band 3: J0423-0120; Band 6: Uranus; ACA: J0501-0159  
  > "J0423-0120 (= J0423-013) was also the flux calibrator in Band 3, while Uranus was that in Band 6." (2.1 Band 3 and Band 6 Data: 12 m Array)
- flux scale uncertainty: 5% (B3), 10% (B6), 10% (B7), 15% (B9); 12% for ACA-combined  
  > "estimated to be 5%, 10%, 10%, and 15% for both sidebands in Band 3, Band 6, Band 7, and Band 9, respectively" (2.3.1 12 m Array Data)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5 (CO 2-1 uniform)  
  > "“briggs" means Briggs weighting with `robust` = 0.5." (Table 2)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: maps without PB correction; flux measured after correction  
  > "We made all maps in this Paper without the primary beam correction, although flux measurements were done after that." (2.3.1 12 m Array Data)
- array combination: ACA and 12 m combined after statwt reweighting  
  > "we used `statwt`[^2] task to recalculate visibility weights for all the data." (2.3.2 ACA Data)
- smoothing: all convolved to 1.0'' x 1.0''; 30 km/s channels for uv-matched  
  > "the same velocity resolution of 30 km s$^{-1}$" (Appendix)
- final beam: _not stated_
- final rms: 1.4-8.0 mJy/beam (30 km/s)  
  > "$J$ = 6–5 (12 m) | 691.473 | 116.16 | B9 | 4.6 | briggs | 1.0 $\times$ 1.0 | 8.0" (Table 2)

### Inherited from earlier work

- Detailed data processing procedure  
  > "Detailed procedure for data processing is summarized in ." (2.3.1 12 m Array Data) [from not given (reference missing in text)]
- ACA CO(1-0) project description  
  > "Detailed description of this project is found in (cite: Konig16)" (2.2.2 Band 3 Data: ACA and 12 m) [from (cite: Konig16)]
- Cycle 0 Band 7/9 data reductions  
  > "We obtained the calibrated archival visibility data of the CO (3–2) and the CO (6–5) from the ALMA archive." (2.2.1 Band 7 and Band 9 Data) [from (cite: Sliwa14); (cite: Xu15)]

### Not stated but needed to reproduce (our reading)

- Calibration and imaging scripts, CASA version for 12 m data
- Clean threshold, masks, cell and image size, deconvolver
- Continuum subtraction and line-free channels
- Integration/mask definition for line fluxes and radial profile extraction
- RADEX line widths/beam filling assumptions and fit uncertainty method details
- Sigma_SFR radial values from Saito15b
- Which Band 6 date is correct (text vs Table 1)

## Analysis recipe

1. **Calibrate and image uv-matched CO cubes**: CASA calibration, uv-clip below 45 kλ, convolve to 1.0'' beam, make moment maps  
  > "Before imaging, we flagged the $uv$ range below 45 k$\lambda$, so that the maximum recoverable scale (cite: Lundgen13) of each ALMA observation is consistent." (2.3.1 12 m Array Data)
   - software: CASA
   - parameter: uv > 45 kλ, MRS 4.6''  
  > "Since the truncated $uv$ range at 45 k$\lambda$ corresponds to the MRS of $\sim$ 4.6$''$" (2.3.1 12 m Array Data)
   - fitting: _not stated_
   - validation: Recovered flux compared to single-dish  
  > "the recovered flux of each CO transition compared to single-dish observations" (2.3.1 12 m Array Data)
2. **Line ratio maps and radial CO SLED**: Divide integrated intensity maps by CO(1-0), mask by CO(1-0) outline; radial fluxes binned at 0.2''  
  > "We divide the integrated intensity maps (Figure [2](#figure_2)d, g, and j) by the CO(1-0) integrated intensity map (Figure [2](#figure_2)a) to make the line ratio maps." (3.3 CO Line Ratios)
   - fitting: _not stated_
   - validation: _not stated_
3. **Single-phase RADEX chi2 grid**: Grid search of Tkin, n(H2), N(H2) minimizing chi2 against radial line fluxes  
  > "varied the parameters until the residuals between the observed line fluxes and the modeled line fluxes are minimized in a $\chi^2$ sense" (4.1 Single-phase RADEX Model)
   - software: RADEX
   - parameter: Tkin 10-300 K (1 K), n 10^2-10^7 cm^-3, N(H2) 10^20.5-10^23.5 cm^-2  
  > "We varied the gas kinetic temperature within a range of $T_{\rm{kin}}$ = 10 - 300 K (d$T_{\rm{kin}}$ = 1 K)" (4.1 Single-phase RADEX Model)
   - assumption: expanding sphere dv=200 km/s, Tbg=2.73 K, [CO]/[H2]=3e-4  
  > "an expanding sphere geometry ($dv$ = 200 km s$^{-1}$), the cosmic microwave background temperature ($T_{\rm{bg}}$ = $T_{\rm CMB}$ = 2.73 K)" (4.1 Single-phase RADEX Model)
   - fitting: chi2 minimization on a grid; 90% confidence ranges  
  > "The 90% confidence ranges of $T_{\rm{warm}}$ are 300 - 370" (5.4.1 Two-phase ISM model)
   - validation: Reconstructed CO SLEDs compared with observations  
  > "We reconstructed the best-fit CO SLED from models in order to compare with the observational data" (4.1 Single-phase RADEX Model)
4. **Compare with Narayanan & Krumholz SLED**: Reconstruct CO SLED from Sigma_SFR power-law model  
  > "which can parameterize the CO SLED of galaxies by a power-law function of $\Sigma_{\rm{SFR}}$" (4.2)
   - fitting: _not stated_
   - validation: _not stated_
5. **PDR modelling**: PDR Toolbox grid for n and G0 using 90% range of 2n_H2 from RADEX  
  > "We varied $n$ within the 90% confidence range of 2$n_{\rm{H_2}}$ derived by the single-phase RADEX" (4.3 PDR Model)
   - software: PDR Toolbox
   - parameter: G0 10^-0.5 - 10^6.5 (step 10^0.25)  
  > "$G_{\rm{0}}$ within a range of 10$^{-0.50}$ - 10$^{6.50}$" (4.3 PDR Model)
   - assumption: n_H negligible relative to 2n_H2  
  > "Here we assumed that the $n_{\rm{H}}$ is negligible compared to the 2$n_{\rm{H_2}}$ term" (4.3 PDR Model)
   - fitting: chi2 grid  
  > "varied the parameters until the residuals between the observed line fluxes and the modeled line fluxes are minimized in a $\chi^2$ sense" (4.1 Single-phase RADEX Model)
   - validation: Compared with G0 from IR luminosity prescription of Papadopoulos14  
  > "The derived $G_{\rm{0}}(L_{\rm{IR}})$ is $\lesssim$ 10$^{2.5}$, which is consistent with the average $G_{\rm{0}}$ derived from the CO SLED." (4.3 PDR Model)
6. **Two-phase RADEX model for ring**: Fix cold component (~19 K from outer region), fit warm fraction r, Twarm, N(H2)warm for grids at three warm densities  
  > "we minimize the number of free parameters by fixing the cold gas component using the observed line ratios at the outer region" (5.4.1)
   - software: RADEX
   - parameter: Twarm 10-800 K; N 10^19-10^24; n_warm 10^2, 10^3, 10^4  
  > "$n_{\rm{warm}}$ = 10$^{2.0}$ (grid A), 10$^{3.0}$ (grid B), and 10$^{4.0}$ cm$^{-3}$ (grid C)" (5.4.1)
   - fitting: chi2 grid  
  > "We varied $n$ within the 90% confidence range of 2$n_{\rm{H_2}}$ derived by the single-phase RADEX (d$n$ = 10$^{0.25}$ cm$^{-3}$)" (4.3 PDR Model)
   - validation: Min chi2 lower than single-phase  
  > "which are smaller than the $\chi^2$ values of the single-phase modeling for the starburst ring" (5.4.1)
7. **Conversion factor, energetics and inflow balance**: alpha_CO from RADEX N(H2) and CO luminosity; compare mechanical luminosities; estimate inflow rate from PVD flux  
  > "we estimate molecular gas inflow rate (IFR) using" (5.4.3)
   - parameter: inclination 33°, alpha_CO=0.2 alpha_MW  
  > "Here we adopt $\theta$ of 33$^\circ$ and $\alpha_{{\rm CO}}$ of 0.2$\alpha_{{\rm MW}}$" (5.5)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.2.1, 4.2.2 (ACA): calibration and imaging  
  > "We performed calibration and imaging using `CASA` (cite: McMullin07)." (2.3.1)
- **statwt** : recalculate visibility weights before combining ACA and 12 m  
  > "we used `statwt`[^2] task to recalculate visibility weights for all the data." (2.3.2)
- **RADEX** : non-LTE radiative transfer modeling  
  > "We used the non-LTE radiative transfer code RADEX (cite: van_der_Tak07)" (4.1)
- **PDR Toolbox** : derive G0 and density  
  > "We used the PDR Toolbox (cite: Kaufman06)" (4.3)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Starburst ring radius | 590 | not stated | pc | 1 | the starburst ring (central 590 pc in radius) and an outer disk ($\sim$ 3.3 kpc in radius) |
| ACA+12m CO(1-0) rms | 1.4 | not stated | mJy/beam | 1 | The achieved rms noise level is 1.4 mJy beam$^{-1}$ |
| Recovered CO(1-0) flux, ACA+12m | 113 | 26 | % | 1 | the recovered flux is 113 $\pm$ 26 % |
| Total H2 mass | 4.1e9 | 0.5e9 | Msun | 1 | The total H$_2$ mass is (4.1 $\pm$ 0.5) $\times$ 10$^9$ $M_{\odot}$ |
| Ring single-phase Tkin / log G0 | ~42 K; G0~10^2.7 | not stated | K | 3 | $T_{\rm{kin}}$ $\sim$ 42 K, and $G_{\rm{0}}$ $\sim$ 10$^{2.7}$ |
| Outer disk Tkin / G0 | ~22 K; G0~10^0.9 | not stated | K | 3 | $T_{\rm{kin}}$ $\sim$ 22 K, and $G_{\rm{0}}$ $\sim$ 10$^{0.9}$ |
| alpha_CO(1-0) at ring | 0.2-0.5 (×3e-4/[CO]/[H2]) | not stated | Msun (K km/s pc^2)^-1 | 7 | The derived $\alpha_{\rm{CO(1-0)}}$ at the starburst ring is 0.2 - 0.5 |
| Inflow rate | 54 | factor of three | Msun/yr | 7 | The derived IFR is 54 $M_{\odot}$ yr$^{-1}$ with the uncertainty by a factor of three |
| Depletion time | 17.7 to 56.6 | 4.6 and 9.3 | Myr | 7 | ranges from 17.7 $\pm$ 4.6 Myr ($\alpha_{\rm{CO}}$ = $\alpha_{\rm{MW}}$) to 56.6 $\pm$ 9.3 Myr |

## Qualitative findings

- CO(6-5) is compact and coincides with starburst ring; lower-J CO is extended  
  > "The CO (6–5) line shows a compact distribution which coincides with the starburst ring detected in Pa $\alpha$ and radio-to-FIR continuum emission, while the other lower-$J$ CO lines are extended." (Conclusion)

## Claim tuples

- H: Is the CO SLED in the ring explained by a single PDR-heated gas phase? | E: Single-phase RADEX, PDR Toolbox and N&K model compared with uv-matched CO SLED | R: CO(3-2)/(1-0) and (6-5)/(1-0) underestimated in ring | F: Single-phase fits ring only roughly; extra warm gas needed | **partially**
- H: Does the ring host a two-phase ISM? | E: Two-phase RADEX with cold fixed at 19 K | R: Twarm>70 K, lower chi2 | F: Two-phase fits well; heating likely mechanical from stellar feedback | **supported**
- H: Is there bar-driven cold gas inflow? | E: Velocity fields and PVDs | R: S-shape non-circular motion along N-S bar; IFR 54 Msun/yr | F: Inflow roughly balances SFR+OFR | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Clip inner uv to match MRS across transitions since short-spacing data missing for several lines  
  > "single-dish or ACA data for several transitions are lacking, and thus we chose to clip the inner $uv$" (5.3)
- Alternative: CRDR and XDR neglected because contributions small  
  > "so we only focus on the effect of both PDR and MDR in this Paper." (4)
- How they decided it was enough: _not stated_
- Limitation (authors): Missing flux on scales >4.6'' (1.5 kpc)  
  > "we ignore the missing flux effect on structures smaller than 4.6$''$" (2.3.1)
- Limitation (authors): Only four CO transitions constrain few free parameters; two-phase relies on assumptions  
  > "Because our analysis includes only four CO transitions and can only constrain a small number of free parameters" (4.2)
- Caveat (inferred, ours): Fixed density for warm component and fixed cold component are strong assumptions
- Caveat (inferred, ours): Single-phase chi2 poor in center; RADEX with 1.0'' sampled radial bins are correlated
- Caveat (inferred, ours): uv clipping affects RADEX temperatures versus prior work

## Reproducibility

- Data public (paper): Data retrieved from ALMA archive  
  > "we retrieved those data from the ALMA archive" (2.2.2)
- Products in archive: _not stated_
- Missing: Reduction scripts
- Missing: Imaging parameters beyond robust 0.5
- Missing: Radial Sigma_SFR values
- Data volume (inferred): ~50-150 GB across four projects
- Score (inferred): 5/5, Public data and grid ranges given, but calibration and imaging details deferred to missing reference.
- Rediscovery candidate: no, Key processing details unstated and modelling choices partly ambiguous.

## Links

- Method: (cite: van_der_Tak07) (RADEX)
- Method: (cite: Kaufman06) (PDR Toolbox)
- Companion: (cite: Saito15b) (radio-to-FIR SED and Sigma_SFR)
- Companion: (cite: Sliwa14) (CO 3-2/6-5 ALMA data and modeling)
- Companion: (cite: Konig16) (ACA CO(1-0))

## Checks

```json
{
 "quotes": 76,
 "quotes_ok": 76,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 86,
  "stated": 55,
  "rate": 0.64
 },
 "evidence_ok": true
}
```
