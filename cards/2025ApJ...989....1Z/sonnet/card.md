# The ALMA Survey of Gas Evolution of PROtoplanetary Disks (AGE-PRO). I. Program Overview and Summary of First Results

`2025ApJ...989....1Z` | The Astrophysical Journal 2025 | first author: Zhang, Ke | arXiv: 2506.10719 | DOI: 10.3847/1538-4357/addebe

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: How do gas disk mass and size evolve over the lifetime of protoplanetary disks, and what do they imply for disk evolution mechanisms?  
  > "AGE-PRO aims to systematically trace the evolution of gas disk mass and size throughout the lifetime of protoplanetary disks." (abstract)
- Target **AGE-PRO sample: 10 Ophiuchus, 10 Lupus, 10 Upper Sco disks around M3-K6 stars**: coordinates per-source RA/Dec listed in Table 1  
  > "It uses a carefully selected sample of 30 disks around M3-K6 stars in three nearby star-forming regions: Ophiuchus (0.5-1 Myr), Lupus (1-3 Myr), and Upper Sco (2-6 Myr)." (abstract); "All distances are adopted from (cite: BailerJones2021)." (Table 1); z/distance ~130-160 pc (Lupus/Upper Sco Gaia distances in Table 1; Ophiuchus not listed)  
  > "It uses a carefully selected sample of 30 disks around M3-K6 stars in three nearby star-forming regions: Ophiuchus (0.5-1 Myr), Lupus (1-3 Myr), and Upper Sco (2-6 Myr)." (abstract); "All distances are adopted from (cite: BailerJones2021)." (Table 1); distance from Bailer-Jones et al. 2021  
  > "It uses a carefully selected sample of 30 disks around M3-K6 stars in three nearby star-forming regions: Ophiuchus (0.5-1 Myr), Lupus (1-3 Myr), and Upper Sco (2-6 Myr)." (abstract); "All distances are adopted from (cite: BailerJones2021)." (Table 1)

## Data provenance

- ALMA projects: 2021.1.00128.L, 2019.A.00034.S, 2017.1.00569.S, 2019.1.01135.S, 2015.1.01199.S
- bands: Band 6 and Band 7  
  > "These observations were carried out at ALMA band 6 and 7" (3 Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: 1875 MHz bands; doubled in Band 6 for Upper Sco  
  > "One or two continuum bands with 1875 MHz bandwidth were included in all correlator setups for self-calibration." (3 Observations)
- arrays: 12-meter array  
  > "The ALMA observations of the AGE-PRO program were conducted with the 12-meter array from 2021 December to 2022 August" (3 Observations)
- configurations: _not stated_
- baselines: 15 to 2917 m  
  > "with baseline lengths between 15 to 2917 m" (3 Observations)
- angular resolution: typical CLEAN beam 0.35" (Band 6), 0.7" (Band 7)  
  > "typical for achieving a CLEAN beam of 0.35$''$" (3.2 Imaging Processes)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: Band 6 CO setup ~30 min (Oph, Lupus), ~60 min (Upper Sco); C17O ~60 min; Band 7 N2H+ 60 (Lupus) and 120 min (Upper Sco)  
  > "The Band 7 N$_2$H$^+$ setup had 60 and 120  minutes of on-source time for the Lupus and Upper Sco targets, respectively." (3 Observations)
- observing dates: 2021 December to 2022 August  
  > "conducted with the 12-meter array from 2021 December to 2022 August" (3 Observations)
- pi or archival as stated: New Large Program data plus archival sets for a few sources (Table 3)  
  > "Several archival datasets were used in the AGE-PRO program (see Table [3](#tab:archival_data))." (3.1)
- Line: 12CO J=2-1 (230.538 GHz)
- Line: 13CO J=2-1 (220.398684 GHz)
- Line: C18O J=2-1 (219.560358 GHz)
- Line: C17O J=2-1 (224.714373 GHz)
- Line: N2H+ J=3-2 (279.511760 GHz)
- Other facility **Gaia**: Distances (DR3) used for stellar luminosities  
  > "The literature stellar luminosities were updated with Gaia DR3 distances" (2.1 Sample Selection)
- External data: Spectral types, Teff, L*, Av, accretion rates for the sample  
  > "the references for Class, Spectral type, {$T_{\rm eff}$, $L_\ast$}, A$_v$, and accretion rates" (Table 1) [from Evans09; Cieza19_ODISEA_I; Alcala14_Lupus; Alcala17_Lupus; Luhman2022_uppstars; Manara2020; Fang2023]
- External data: Distances to all sources  
  > "All distances are adopted from (cite: BailerJones2021)." (Table 1) [from (cite: BailerJones2021)]
- External data: Ages of Upper Sco clusters for comparison  
  > "The isochronal ages of Upper Sco clusters were estimated between $\sim$4-14 Myr (cite: Ratzenbock2023a; Ratzenbock2023b)." (2.2) [from Ratzenbock2023a,b]
- Simulation/model as data: Grid of thermo-chemical (DALI) models used to infer gas masses (done in AGE-PRO V)  
  > "The gas disk masses are estimated by comparing line fluxes with a large grid of thermo-chemical models." (4.3)

## Processing

### Calibration

- pipeline or manual: CASA pipeline, then self-calibration  
  > "All execution blocks (EBs) were initially calibrated using the Common Astronomy Software Application (CASA; (cite: CASA2022)) pipeline version 6.2." (3.1)
- casa version: Pipeline 6.2; self-calibration CASA 6.4  
  > "we conducted self-calibration using CASA version 6.4" (3.1)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: EB fluxes consistent within 10%; rescaled if beyond  
  > "We found that most EBs had fluxes consistent within 10%." (3.1)
- self calibration: Phase self-cal on continuum for SNR>20, solint from 'inf' down to 300-60 s, one amplitude round with solint='inf'; based on DSHARP/MAPS  
  > "Self-calibration of the continuum visibilities was performed for sources with continuum SNR larger than 20." (3.1); "The first round of gaincal solutions were computed with `solint=‘inf’` and further iterations use decreasing time intervals, typically between 300 to 60 seconds." (3.1)

### Imaging

- task: tclean multiscale CLEAN  
  > "we utilized the `tclean` task in CASA with the multiscale clean option" (3.2)
- deconvolver: _not stated_
- weighting robust: robust 0.5 for 12CO; 1 for other lines  
  > "A robust parameter of 0.5 was adopted for $^{12}$CO line images to achieve high spatial resolution, while value of 1 was used for all other lines to favor sensitivity." (3.2)
- uv taper: uvtaper to circularize beam for Band 6 lines; uvrange >50 klambda for 12CO of Lupus/Upper Sco  
  > "we use uvrange =‘$>$50klambda’ to remove cloud contamination at scale$>$4$''$" (3.2)
- cell size: 0.025" Band 6; 0.04" Band 7  
  > "Band 6 images were produced with a resolution of 1600$\times$1600 pixels and a pixel size of 0.025$''$" (3.2)
- image size: 1600x1600 Band 6; 864x864 Band 7  
  > "we used 864$\times$864 pixels and a pixel size of 0.04$''$" (3.2)
- masking: Keplerian masks for Lupus/Upper Sco; automask for Ophiuchus  
  > "we constructed “cleaning” Keplerian masks for these sources." (3.2); "we utilized the `automask` option in `tclean`" (3.2)
- multiscale scales: [0,4,12,24,48] pixels Band 6; [0,4] Band 7  
  > "employing scales of \[0, 4, 12, 24, 48\] pixels for Band 6 images and \[0, 4\] for Band 7 images" (3.2)
- continuum subtraction: uvcontsub with all spectral windows together  
  > "we then used the task `uvcontsub` to subtract the continuum with all spectral windows together" (3.1)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: imsmooth to circular beam for Band 6  
  > "`imsmooth` was used to make the final image with a circular beam." (3.2)
- final beam: _not stated_
- final rms: cleaned to 1 sigma, no JvM correction  
  > "We found that CLEAN to 1$\sigma$ and without JvM correction gives the most accurate results" (3.3)

### Inherited from earlier work

- Self-calibration procedure  
  > "Our methodology was based on the self-cal procedures of the DSHARP and MAPS large programs" (3.1) [from (cite: Andrews18b; Czekala21_MAPS)]
- Gas mass derivation details via thermo-chemical model grid  
  > "Please see AGE-PRO V (cite: AGEPRO_V_gasmasses) for details." (4.3) [from (cite: AGEPRO_V_gasmasses)]
- Keplerian mask parameters (M*, inclination, PA)  
  > "can be found in (cite: AGEPRO_III_Lupus; AGEPRO_IV_UpperSco)" (3.2) [from (cite: AGEPRO_III_Lupus; AGEPRO_IV_UpperSco; AGEPRO_X_dust_disks)]
- Gas disk sizes from Nuker profile fits  
  > "AGE-PRO XI (cite: AGEPRO_XI_gas_disk_sizes) fit the $^{12}$CO integrated intensity maps with a 2D Nuker profile" (4.2) [from (cite: AGEPRO_XI_gas_disk_sizes)]
- Dust disk sizes and geometries from visibility fitting  
  > "AGE-PRO X (cite: AGEPRO_X_dust_disks) employs visibility fitting" (4.2) [from (cite: AGEPRO_X_dust_disks)]
- Ophiuchus automask imaging  
  > "as detailed in (cite: AGEPRO_II_Ophiuchus)" (3.2) [from (cite: AGEPRO_II_Ophiuchus)]

### Not stated but needed to reproduce (our reading)

- Per-source robust values for self-calibration (0.5-1.0 range only)
- Exact solint sequence and SNR criteria per source
- Line-free channels and continuum-flagging details per source
- Keplerian mask parameters and R_max per disk (in companion papers)
- Thermo-chemical model grid parameters for gas masses
- Individual line fluxes and uncertainties
- CLEAN thresholds/mask details and Ophiuchus Keplerian-mask settings

## Analysis recipe

1. **Self-calibrate continuum**: Align EBs astrometrically, check flux scale, iterative phase then one amplitude self-cal  
  > "We then aligned the different EBs (with CASA tasks `phaseshift` and `fixplanets`) to a common phase center." (3.1)
   - software: CASA
   - parameter: SNR>20; solint inf then 300-60 s; scales [0,5,15,45]  
  > "multiscale `CLEAN` and `scales=[0, 5, 15, 45]` pixels" (3.1)
   - fitting: _not stated_
   - validation: Peak intensity and SNR improvement per iteration  
  > "The resulting peak intensity to noise ratio on the image were used to evaluate whether another iteration is needed." (3.1)
2. **Image line cubes**: Split, cvel2 to LSRK grid, tclean multiscale with Keplerian masks, deep clean without JvM, circularize beam  
  > "The line visibilities from multiple EBs were then regridded to a constant LSRK velocity grid using the `cvel2` task" (3.2)
   - software: CASA
   - parameter: 0.1 km/s channels for 12CO, 0.2 km/s others  
  > "We adopted a velocity channel width of 0.1  km s$^{-1}$ for the $^{12}$CO (2-1) line and 0.2  km s$^{-1}$ for all other lines" (3.2)
   - fitting: _not stated_
   - validation: Tested CLEAN thresholds 1-4 sigma with/without JvM on flux and radial profiles  
  > "We varied the CLEAN threshold between the 1-4$\sigma$ noise level, with/without applying the JvM corrections." (3.3)
3. **Handle cloud contamination and measure line fluxes**: Keplerian mask on channel maps, curve-of-growth integrated flux; half-spectrum x2 for asymmetric contamination  
  > "The line fluxes of the Lupus and Upper Sco disks were measured using a curve-of-growth method" (4.2)
   - software: GoFish, bettermoments
   - fitting: _not stated_
   - validation: Visual inspection of channel and moment zero maps  
  > "we also visually inspected the channel and moment zero maps" (4.1)
4. **Measure gas disk sizes**: Radius enclosing 90% of 12CO flux from beam-convolved 2D Nuker fits  
  > "measures gas disk sizes from the unconvolved best fit Nuker profiles using the curve-of-growth method" (4.2)
   - fitting: 2D Nuker profile convolved with clean beam (AGE-PRO XI)  
  > "fit the $^{12}$CO integrated intensity maps with a 2D Nuker profile that was convolved with the clean beam" (4.2)
   - validation: _not stated_
5. **Derive gas and dust masses**: Compare 13CO, C18O, N2H+ (Class II) or C17O (Oph) fluxes and 1.3 mm continuum with thermo-chemical model grid; dust mass from optically thin continuum  
  > "we estimate the gas disk masses by comparing the $^{13}$CO, C$^{18}$O, and N$_2$H$^+$ line fluxes, along with the 1.3 mm continuum fluxes, to a large grid of thermo-chemical models" (4.3)
   - software: DALI
   - assumption: kappa = 2.3 (nu/230 GHz) cm2/g, Tdust = 20 K; ISM xCO=1e-4 for Ophiuchus  
  > "assuming a dust opacity of $\kappa_\nu=2.3~(\nu/230\,{\rm GHz})\,$cm$^2$ g$^{-1}$ and an average dust temperature of 20 K" (4.3)
   - fitting: not stated here (AGE-PRO V)  
  > "The gas disk masses are estimated by comparing line fluxes with a large grid of thermo-chemical models. Please see AGE-PRO V (cite: AGEPRO_V_gasmasses) for details." (Analysis: Gas and dust disk masses)
   - validation: _not stated_
6. **Compute regional medians and spectral index**: Kaplan-Meier medians including limits; alpha_mm from Band 7 and Band 6 fluxes  
  > "We calculate the median values for each region using the Kaplan–Meier estimator in the `lifelines` python package" (6)
   - software: lifelines
   - fitting: _not stated_
   - validation: Repeated with four age groups  
  > "we also test separating our results into four age groups and find the general trends still hold" (6)

## Software

- **CASA** 6.2 pipeline; 6.4 self-cal: Calibration, self-calibration, imaging  
  > "we conducted self-calibration using CASA version 6.4" (3.1)
- **ysoisochrone** : Stellar masses and ages from evolutionary tracks  
  > "We use the `Python` package `ysoisochrone`" (2.2)
- **keplerian_mask** : Keplerian CLEAN masks  
  > "Masks were constructed using the `keplerian_mask` function" (3.2)
- **GoFish** : Keplerian masks on channel maps  
  > "we apply a new Keplerian mask to channel maps, using the `gofish` and `bettermoments` package" (4.1)
- **bettermoments** : Moment zero maps with Keplerian masks  
  > "using the `gofish` and `bettermoments` package" (4.1)
- **lifelines** v0.29.0: Kaplan-Meier medians with limits  
  > "using the Kaplan–Meier estimator in the `lifelines` python package" (6)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Median gas mass Ophiuchus | 58 | not stated | 1e-4 Msun | 6 | / Ophiuchus / 58 / 14.4 / 122 / 40.3 / ... / ... / ... / ... / |
| Median gas mass Lupus | 6.5 | not stated | 1e-4 Msun | 6 | / Lupus / 6.5 / 4.7 / 46 / 30.4 / 74.1 / 3.4 / -4.83 / 2.25 / |
| Median gas mass Upper Sco | 4.2 | not stated | 1e-4 Msun | 6 | / Upper Sco / 4.2 / 1.9 / 120 / 42.0 / 109.9 / 3.4 / -4.69 / 2.45 / |
| Median gas-to-dust ratio (Oph, Lupus, Upper Sco) | 122, 46, 120 | not stated | dimensionless | 6 | decreases from 122 in the youngest disks ($<$1 Myr) to 46 in Lupus disks, and then increases to 120 in the Upper Sco disks |
| Median gas disk size Lupus / Upper Sco | 74.1 / 109.9 | not stated | au | 4 | / Upper Sco / 4.2 / 1.9 / 120 / 42.0 / 109.9 / 3.4 / -4.69 / 2.45 / |
| Median spectral index Lupus / Upper Sco | 2.25 / 2.45 | not stated | dimensionless | 6 | / Lupus / 6.5 / 4.7 / 46 / 30.4 / 74.1 / 3.4 / -4.83 / 2.25 / |
| Median dust disk radius Oph / Lupus / Upper Sco | 40.3 / 30.4 / 42.0 | not stated | au | 6 | / Ophiuchus / 58 / 14.4 / 122 / 40.3 / ... / ... / ... / ... / |

## Qualitative findings

- Most Class II disks have xCO ~1e-5, about an order of magnitude CO depletion, with no difference between Lupus and Upper Sco  
  > "We find the majority of our Class II disks have inferred CO abundances around 10$^{-5}$, suggesting an order of magnitude CO depletion with respect to the ISM ratio." (6.1)
- Dust disk sizes similar across regions; substructures in half the sample  
  > "dust substructures are present in half of the AGE-PRO sample" (6.2)

## Claim tuples

- H: Gas disk mass decreases with age | E: Gas masses from CO isotopologue/N2H+ fluxes with thermo-chemical models in three regions | R: Median gas mass Oph ~6 MJup vs 0.68 (Lupus) and 0.44 (Upper Sco) | F: Most gas mass evolution happens early; Lupus and Upper Sco similar | **supported**
- H: Gas and dust evolve on the same timescale | E: Compare median gas-to-dust ratios across regions | R: 122 -> 46 -> 120 | F: Gas and dust evolve on different timescales | **supported**
- H: Typical gas disks are as large as well-studied massive disks | E: 90% 12CO radii | R: Median 74-110 au | F: Typical gas disks are much smaller | **supported**
- H: Which accretion mechanism explains disk populations | E: Population synthesis models compared to AGE-PRO medians (AGE-PRO VII) | R: MHD wind models match; turbulent models overpredict gas mass by ~10x | F: MHD wind-driven accretion with compact disks and declining field favored | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: CO isotopologues plus N2H+ constrain xCO and improve gas mass precision; C17O for optically thin Ophiuchus  
  > "the line flux ratios of CO isotopologue and N$_2$H$^+$ provide constraints of $x_{\rm CO}$ and thus largely improve the precision of gas mass estimates" (2.4.1)
- Alternative: JvM correction rejected in favor of deep clean to 1 sigma  
  > "we adopted cleaning the AGE-PRO molecular line cubes down to 1 $\sigma$ without applying the JvM correction" (3.3)
- How they decided it was enough: _not stated_
- Limitation (authors): Medians are of survivors; survival bias not accounted in medians; absolute ages model-dependent; regions assumed to share initial conditions  
  > "The median values, listed in Table [4](#tab:median), do not take into consideration survival bias" (6)
- Caveat (inferred, ours): Age ordering relies on three different regions assumed to share initial conditions
- Caveat (inferred, ours): Ophiuchus sample is mostly highly inclined and its representativeness is unquantified
- Caveat (inferred, ours): Gas masses depend on thermo-chemical model assumptions such as cosmic-ray ionization rate
- Caveat (inferred, ours): Small sample (10 per region)

## Reproducibility

- Data public (paper): Self-calibrated visibilities, cubes and profiles on AGE-PRO website  
  > "The self-calibrated visibility data, image cubes, and radial profiles of spectral lines are available for download from the AGE-PRO website" (5 Data Release)
- Products in archive: _not stated_
- Missing: Gas mass model grid and fitting (AGE-PRO V)
- Missing: Per-source masks and parameters in companion papers
- Missing: Per-source self-cal settings
- Data volume (inferred): Several TB raw; ~0.5-1 TB calibrated for 30 disks
- Score (inferred): 3/5, Calibration and imaging are well described and data public, but the main gas mass analysis is in companion papers.
- Rediscovery candidate: no, Key results (gas masses) depend on thermo-chemical modelling detailed elsewhere; this paper is an overview.

## Links

- Method: (cite: AGEPRO_V_gasmasses) (Gas mass derivation)
- Method: (cite: AGEPRO_XI_gas_disk_sizes) (Beam-corrected gas sizes)
- Method: (cite: AGEPRO_X_dust_disks) (Dust sizes and geometries)
- Companion: (cite: AGEPRO_II_Ophiuchus) (Ophiuchus results)
- Companion: (cite: AGEPRO_III_Lupus) (Lupus results)
- Companion: (cite: AGEPRO_IV_UpperSco) (Upper Sco results)
- Companion: (cite: AGEPRO_VII_population) (Population synthesis)
- Related: DSHARP
- Related: MAPS
- Related: eDisk
- Related: CAMPOS
- Related: ODISEA

## Checks

```json
{
 "quotes": 91,
 "quotes_ok": 91,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 5,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 85,
  "stated": 64,
  "rate": 0.753
 },
 "evidence_ok": true
}
```
