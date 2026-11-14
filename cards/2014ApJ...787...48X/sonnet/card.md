# ALMA Observations of Warm Molecular Gas and Cold Dust in NGC 34

`2014ApJ...787...48X` | The Astrophysical Journal 2014 | first author: Xu, C. K. | arXiv: 1404.1402 | DOI: 10.1088/0004-637X/787/1/48

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars, star_formation
- Question: How is warm dense molecular gas and cold dust distributed in the nucleus of NGC 34, how is it related to the starburst and AGN, and is there evidence for a molecular outflow?  
  > "(1) How is the warm dense molecular gas distributed in the inner most region of NGC 34? (2) How is the gas related to the starburst and the AGN, respectively?" (Introduction)
- Target **NGC 34**: coordinates _not stated_; z/distance 84 Mpc (1'' = 407 pc)  
  > "a local luminous infrared galaxy (LIRG) at a distance of 84 Mpc ($\rm 1\ensuremath{''} = 407\; pc$)" (abstract); distance from _not stated_

## Data provenance

- ALMA projects: _none stated_
- bands: Band 9 (435 um continuum)  
  > "were carried out using the Band 9 receivers of ALMA in the TDM mode (velocity resolution: 6.8 km sec$^{-1}$)" (2 Observations)
- frequencies and spectral setup: 4 SPWs centered at 679.801, 678.039, 676.271, 674.339 GHz, each ~2 GHz wide  
  > "are centered at the sky frequencies of 679.801, 678.039, 676.271 and 674.339 GHz, respectively, each with a bandwidth of $\sim 2$ GHz" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: Extended (E) and extended & compact (E&C)  
  > "Observations were carried out in both extended (E) and extend & compact (E&C) configurations" (2 Observations)
- baselines: _not stated_
- angular resolution: 0.26'' x 0.23'' (106 x 94 pc), P.A. 46.3 deg  
  > "having the FWHM of $\rm 0.26\ensuremath{''}\times 0.23\ensuremath{''}$ (corresponding to physical scales of $\rm 106\; pc \times 94\; pc$)" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: channel rms 5.5 mJy/beam (34 km/s); continuum rms 1.9 mJy/beam  
  > "channel maps of the CO (6-5) line emission have 1-$\sigma$ rms noise of $\rm 5.5\; mJy\; beam^{-1}$" (2 Observations)
- time on source: 2.25 hours  
  > "The total on-target integration time was 2.25 hours." (2 Observations)
- observing dates: 2012/05/20, 2012/05/21, 2012/08/25  
  > "X4afc39_X43b | 2012/08/25 | 03:30:38 – 05:01:41 | E&C | 27 | 402 | 24.7 | 1058" (Table 1)
- pi or archival as stated: _not stated_
- Line: CO 6-5 (691.473 GHz)
- Line: H13CN 8-7 (690.552 GHz)
- Other facility **Herschel SPIRE**: 350 and 500 um fluxes interpolated to 435 um for single-dish comparison; FTS CO(6-5) flux  
  > "we estimated the total flux of the 435 $\rm \mu m$ continuum of NGC 34 by interpolating SPIRE photometer fluxes" (3.2 Dust continuum emission)
- Other facility **CARMA**: CO(1-0) flux used for gas mass (from Fernandez2014)  
  > "recently observed the CO (1-0) emission of NGC 34 using CARMA with a synthesized beam of $2.48\ensuremath{''} \times 2.12\ensuremath{''}$" (3.3 Gas Mass and Dust Mass)
- External data: CO(1-0) flux 42±4 Jy km/s in central beam  
  > "The integrated flux in the central beam of the CO (1-0) map is $\rm f_{CO(1-0)} = 42\pm 4\; Jy\; km\; s^{-1}$" (3.3 Gas Mass and Dust Mass) [from (cite: Fernandez2014)]
- External data: Herschel FTS CO(6-5) flux 937±63 Jy km/s  
  > "which is $\rm 937 \pm 63 Jy\; km\; s^{-1}$ (Lu et al., in preparation)" (3.1 CO (6-5) line emission) [from Lu et al., in preparation]
- External data: dust opacity kappa_1200GHz = 0.48 m2/kg  
  > "$\rm \kappa_{1200GHz} = 0.48\; m^2kg^{-1}$ (cite: Dale2012)" (3.3 Gas Mass and Dust Mass) [from (cite: Dale2012)]
- External data: 8.44 GHz radio continuum map used for SFR profile  
  > "radio continuum at 8.44 GHz ($\rm beam = 0.39\ensuremath{''}\times 0.29\ensuremath{''}$, (cite: Condon1991))" (4 Comparisons with Previous Results) [from (cite: Condon1991)]
- Simulation/model as data: Meijerink2011 PDR/XDR models used to test H13CN/CO flux ratio  
  > "using models of (cite: Meijerink2011), we found that the observed flux ratio can be reproduced with the following reasonable parameters" (3.1 CO (6-5) line emission)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 3.4  
  > "The data were reduced and calibrated using CASA 3.4." (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Pallas  
  > "Observations of the asteroid Pallas were made for flux calibration." (2 Observations)
- flux scale uncertainty: 15%  
  > "The error in the flux calibration was estimated to be 15%." (2 Observations)
- self calibration: phase and amplitude self-calibration; parameters not given  
  > "Finally, phase and amplitude self-calibrations were carried out to improve the overall sensitivity." (2 Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "The visibilities were imaged with natural weighting and cleaned." (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: CASA uvcontsub; continuum from other SPWs  
  > "The continuum subtraction was carried out using CASA task *UVcontsub*." (2 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: cubes binned to 34 km/s channels  
  > "we binned the spectral cubes into channels with the width of $\rm \delta v = 34\; km\; s^{-1}$" (2 Observations)
- final beam: 0.26'' x 0.23'', PA 46.3 deg  
  > "the P.A. of $46^\circ.3$" (2 Observations)
- final rms: line 5.5 mJy/beam per channel; moment-0 1.2 Jy/beam km/s; continuum 1.9 mJy/beam  
  > "the rms of the continuum map is $\rm 1.9\; mJy\; beam^{-1}$" (2 Observations)

### Inherited from earlier work

- Dust temperature from Scoville (2012) formalism for optically thick nuclear starbursts  
  > "is estimated using the formalism of (cite: Scoville2012) for extremely obscured nuclear starbursts" (3.3 Gas Mass and Dust Mass) [from (cite: Scoville2012)]
- Outflow mass loss rate formalism  
  > "using the formalism of (cite: Rupke2002)" (3.1 CO (6-5) line emission) [from (cite: Rupke2002)]

### Not stated but needed to reproduce (our reading)

- tclean/clean parameters: cell size, image size, masks, iterations, threshold
- self-calibration solution intervals and reference data
- line-free channels and uvcontsub fit order
- how core (r~50 pc) fluxes and Gaussian sizes were measured
- how the CO(6-5) disk size and axis ratio were derived (fit method)
- ALMA project code
- rotating-ring model definition and fitting code
- how CO(6-5) luminosity and gas mass were computed from fluxes

## Analysis recipe

1. **Calibrate and image data**: CASA 3.4 reduction, natural-weighted cleaned cubes, phase+amplitude self-cal, uvcontsub, 34 km/s binning  
  > "The visibilities were imaged with natural weighting and cleaned." (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: CO flux compared to Herschel FTS (ratio 1.07±0.18)  
  > "1004$\pm 151$ | 1.07$\pm 0.18$" (Table 2)
2. **Fit core spectrum with rotating ring**: least-squares fit of rotating ring with density gradient to r=0.125'' aperture spectrum  
  > "we present model fitting to the core spectrum using a simple rotating ring model." (3.1 CO (6-5) line emission)
   - fitting: least squares; free: v_center, v_rot sin i, sigma, rho_max/rho_min  
  > "The least-squares fitting results for the model parameters are as follows" (3.1 CO (6-5) line emission)
   - validation: alternative models (two Gaussians; ring plus Gaussian) fit equally well with more parameters  
  > "can fit the data equally well but with more parameters" (3.1 CO (6-5) line emission)
3. **Gas mass from CO(1-0) luminosity**: L_CO(1-0) from CARMA times alpha_CO  
  > "adopting a Galactic conversion factor $\rm \alpha_{CO} = 4.3\; M_\ensuremath{\odot}\; (K\; km\; s^{-1}\; pc^2)^{-1}$" (3.3 Gas Mass and Dust Mass)
   - assumption: alpha_CO = 4.3 (Galactic) or 0.8 (ULIRG); CO(1-0) emission concentrated in the ALMA disk  
  > "Assuming that this CO (1-0) luminosity is concentrated in the central disk detected by ALMA" (3.3 Gas Mass and Dust Mass)
   - fitting: _not stated_
   - validation: _not stated_
4. **Dust mass from 435 um continuum**: optically thin single-temperature formula M_dust = c^2 f D^2/(2 nu^2 k T kappa)  
  > "The dust mass can be estimated from the continuum flux using the following formula" (3.3 Gas Mass and Dust Mass)
   - parameter: T=43.0 K, kappa_690GHz = 0.16 m2/kg, D=84 Mpc  
  > "The dust temperature, $\rm T= 43.0\; K$" (3.3 Gas Mass and Dust Mass)
   - assumption: R_pc=100 and 70% of L_IR inside radius  
  > "70% of the IR luminosity of NGC 34 is inside this radius" (3.3 Gas Mass and Dust Mass)
   - fitting: _not stated_
   - validation: error budget: 30% kappa, 15% flux cal, ~10% temperature  
  > "Given the 30% error for $\rm \kappa$ (cite: James2002), 15% flux calibration error and $\sim 10\%$ error in the temperature estimate" (3.3 Gas Mass and Dust Mass)
5. **Radial profiles and star formation comparison**: gas and dust column density profiles from CO and continuum with constant M/L; compared with SFR from 8.44 GHz radio and stellar mass from H-band  
  > "These were estimated using radial profiles of the CO (6-5) and the continuum and assuming constant mass-to-luminosity ratios." (4 Comparisons with Previous Results)
   - assumption: Kroupa IMF, BC03 SSP age 4e8 yr, A_H=0.46  
  > "An H-band extinction correction of $\rm A_{H}=0.46$ mag was applied" (4 Comparisons with Previous Results)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 3.4: reduction, calibration, imaging, uvcontsub  
  > "The data were reduced and calibrated using CASA 3.4." (2 Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(6-5) integrated flux | 1004 | 151 | Jy km/s | 1 | integrated flux of $\rm f_{CO~(6-5)} = 1004 (\pm 151) \; Jy\; km\; s^{-1}$ |
| H13CN(8-7) feature flux | 17.7 | ±2.1 (random) ±2.7 (systematic) | Jy km/s | 1 | 17.7 \pm 2.1\pm 2.7 \; Jy\;km\; s^{-1} |
| 435 um continuum flux density | 275 | 41 | mJy | 1 | $\rm f_{435\mu m}=275\pm 41\; mJy$ |
| Dust mass | 10^6.97 | ±0.13 dex | Msun | 4 | $\rm M_{dust} = 10^{6.97\pm 0.13}\; \; M_\ensuremath{\odot}$ |
| Ring model rotation velocity | 173 | 1 | km/s | 2 | $\rm v_{rot}sin(i) = 173\pm 1\; km\; s^{-1}$ |
| Interferometer-to-single-dish continuum ratio | 0.53 | 0.08 | dimensionless | 4 | interferometer-to-single-dish flux ratio of $\rm 0.53\pm 0.08$ |
| Gas mass (Galactic alpha_CO) | 10^9.49 | ±0.04 dex | Msun | 3 | $\rm M_{gas} = 10^{9.49\pm 0.04}\; M_\ensuremath{\odot}$ |
| Outflow mass loss rate (if outflow) | 32 | not stated | Msun/yr | 0 | we estimate a mass loss rate of $\rm \dot{M} = 32\; M_\ensuremath{\odot}\; yr^{-1}$ |

## Qualitative findings

- CO(6-5) disk is regular, compact (200 pc FWHM) rotating, 6x smaller than the CO(1-0) disk; closely follows the radio continuum  
  > "The CO (6-5) disk is a factor of 6 smaller than the CO (1-0) disk found by (cite: Fernandez2014)." (Summary)

## Claim tuples

- H: Warm dense gas in NGC 34 forms a compact regular rotating disk | E: CO(6-5) imaging at 0.25'' with moment maps and P-V diagram | R: Disk FWHM 200 pc, double-horn spectrum, FWHM 406 km/s | F: Compact rotating disk | **supported**
- H: AGN contributes significantly to CO(6-5) and continuum | E: Core flux fraction within r~50 pc | R: Core is 19% of CO and 28% of continuum | F: AGN contribution insignificant | **supported**
- H: Red wing feature is H13CN(8-7) or an outflow | E: Flux ratio compared with NGC 4418 prediction and PDR models; outflow rate estimate | R: Ratio 0.018±0.002 consistent with prediction; outflow rate 32 Msun/yr consistent with upper limit | F: Cannot distinguish the two | **partially**
- H: Nuclear region has very high gas column density | E: Gas and dust profiles from CO and continuum | R: Sigma_gas ≳1e4 Msun/pc2 at r≲100 pc | F: Very high column density | **supported**

## Reasoning

- Why this data: NGC 34 chosen as one of the closest LIRGs with strong CO(6-5) and low zenith angle for Band 9  
  > "its Band 9 observations are affected by minimal atmospheric absorption" (Introduction)
- Why this method: _not stated_
- Alternative: H13CN line versus outflow explanation for the red wing; both retained  
  > "the feature in the red-shifted wing of CO (6-5) profile can be due to the $\rm H^{13}CN$ line emission or/and an outflow" (3.1 CO (6-5) line emission)
- How they decided it was enough: _not stated_
- Limitation (authors): Good map quality only in the central ~3'' due to uv-coverage; astrometric accuracy ~0.1''  
  > "the resulting maps have good quality only in the central region of $\sim 3''$ (limited by the uv-coverage)" (2 Observations)
- Caveat (inferred, ours): Gas mass differs by factor ~5 depending on alpha_CO; rests on CO(1-0) beam assumption
- Caveat (inferred, ours): Single dust temperature from a formalism, not fit
- Caveat (inferred, ours): Feature at red wing ambiguous; no independent line
- Caveat (inferred, ours): Flux uncertainty 15% dominates; no systematic uv-coverage test

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Project code not printed in the paper
- Missing: Imaging parameters
- Missing: Core-extraction method
- Missing: Lu et al. Herschel FTS data in preparation
- Data volume (inferred): ~50-100 GB raw (6 Band 9 execution blocks, TDM)
- Score (inferred): 4/5, Data public (Cycle 0) and recipe partly clear, but imaging details and several measurement methods are missing.
- Rediscovery candidate: no, Project code not stated in paper and imaging recipe incomplete.

## Links

- Method: (cite: Scoville2012) (dust temperature formalism)
- Method: (cite: Rupke2002) (outflow mass rate formalism)
- Method: (cite: Meijerink2011) (PDR/XDR models for line ratios)
- Companion: (cite: Fernandez2014) (CARMA CO(1-0) and VLA HI of NGC 34)
- Related: GOALS
- Related: Herschel SPIRE FTS survey of GOALS

## Checks

```json
{
 "quotes": 60,
 "quotes_ok": 60,
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
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 45,
  "rate": 0.6
 },
 "evidence_ok": true
}
```
