# ATOMS: ALMA Three-millimeter Observations of Massive Star-forming regions - XXI. A large-sample observational study of ethanol and dimethyl ether in hot cores

`2025MNRAS.538.2579K` | Monthly Notices of the Royal Astronomical Society 2025 | first author: Kou, Zhiping | arXiv: 2503.07126 | DOI: 10.1093/mnras/staf408

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: star_formation, astrochemistry
- Question: How do the column densities and rotation temperatures of ethanol and dimethyl ether compare across 60 hot cores, and are they chemically linked to CH3OH?  
  > "we aim to provide a large sample analysis of EA and DE with the ALMA (ATOMS) survey towards the 60 hot cores targeted in this work, examining their abundance variations and gaining insights into their formation pathways." (1 Introduction)
- Target **60 hot cores in IRAS clumps (ATOMS sample)**: coordinates per-source coordinates listed in the source table (e.g. I08470-4323 08:48:47.79 -42:54:27.90)  
  > "This sample covers a broad range of luminosities ($\sim$10$^{1.2}$-10$^{7}$ L$_{\odot}$), distances from the Sun ($\sim$1-12 kpc)" (2.2 Hot core sample); z/distance ~1-12 kpc  
  > "This sample covers a broad range of luminosities ($\sim$10$^{1.2}$-10$^{7}$ L$_{\odot}$), distances from the Sun ($\sim$1-12 kpc)" (2.2 Hot core sample); distance from Table A1 of Liu et al. 2020 (cite: 2020MNRAS.496.2790LiuT)  
  > "This sample covers a broad range of luminosities ($\sim$10$^{1.2}$-10$^{7}$ L$_{\odot}$), distances from the Sun ($\sim$1-12 kpc)" (2.2 Hot core sample)

## Data provenance

- ALMA projects: 2019.1.00685.S
- bands: Band 3  
  > "The observations were carried out with ALMA band 3 towards 146 Infrared Astronomical Satellite (IRAS) clumps" (2.1 Observations)
- frequencies and spectral setup: 8 SPWs; SPWs 7-8 broad (1875 MHz, ~1.6 km/s) at 97536-99442 and 99470-101390 MHz; SPWs 1-6 narrow (58.59 MHz)  
  > "2 broad bandwidth windows (SPWs 7-8, bandwidth 1875 MHz with spectral resolution `~`1.6 km s$^{-1}$)" (2.1 Observations)
- continuum bandwidth: _not stated_
- arrays: ACA 7-m and 12-m array; only 12-m data used  
  > "In this study, we only employ 12 m array data as hot cores typically have smaller source sizes" (2.1 Observations)
- configurations: C43-2 or C43-3 (12-m)  
  > "Atacama Compact 7-m Array (ACA) and 12-m array (C43-2 or C43-3 configurations) observations were conducted" (2.1 Observations)
- baselines: _not stated_
- angular resolution: ~1.2''-1.9'' (12-m)  
  > "The angular resolution and maximum recovered angular scale for the 12-m array observations are `~` 1.2$^{''}$ - 1.9$^{''}$" (2.1 Observations)
- max recoverable scale: ~14.5''-20.3''  
  > "`~` 14.5$^{''}$ - 20.3$^{''}$, respectively" (2.1 Observations)
- sensitivity: mean 1σ rms better than 10 mJy/beam per channel  
  > "The mean 1$\sigma$ rms noise of SPWs 7 and 8 are better than 10 mJy beam$^{-1}$ per channel for spectral lines." (2.1 Observations)
- time on source: ~3 min per source (12-m), 8 min (ACA)  
  > "typical on-source times of 3 minutes for 12-m array and 8 minutes per source for ACA 7-m array" (2.1 Observations)
- observing dates: late September to mid-November 2019  
  > "observations were conducted from late September to mid-November 2019" (2.1 Observations)
- pi or archival as stated: PI: Tie Liu; data first presented by Liu et al. 2020  
  > "The data were first presented by (cite: 2020MNRAS.496.2790LiuT; 2020MNRAS.496.2821LiuT)" (2.1 Observations)
- Line: C2H5OH (ethanol) many, e.g. 8(2,7)-8(1,8) anti (97-101 GHz (e.g. 100990.113 MHz))
- Line: CH3OCH3 (dimethyl ether) many, e.g. 4(1,4)-3(0,3) (97-101 GHz (e.g. 99324-99326 MHz))
- Line: CH3OH 13(-2,12)-12(-3,10) E, vt=0 (velocity reference) (100.6389 GHz)
- Line: H40alpha recombination line (99022.952 MHz)
- External data: CH3OH column densities and continuum source sizes/hot core identification for the sample  
  > "we take the column densities of methanol in our sample from (cite: 2022MNRAS.511.3463Qin)" (4.1) [from (cite: 2022MNRAS.511.3463Qin)]
- External data: Hydrogen column densities (Tables C1-C4)  
  > "The hydrogen column densities were obtained from (cite: 2025A&A...694A.166C) (in their Tables C1-C4)." (3.1 Line identification) [from (cite: 2025A&A...694A.166C)]
- External data: EA, DE, CH3OH column densities and temperatures of hot cores and hot corinos from the literature  
  > "Table [\[tab:A.4\]](#tab:A.4) gives source parameters from the literature used for comparison" (Table A.4) [from literature compilation, Table A.4]
- Simulation/model as data: Chemical model of Garrod et al. 2022 (G22) compared to observed EA and DE abundances  
  > "Compared with chemical models, the three different warm-up timescale models result in the systematic overproduction of EA and the systematic underproduction of DE." (abstract)

## Processing

### Calibration

- pipeline or manual: calibrated with CASA; details deferred to Liu et al. 2020  
  > "The data were calibrated and imaged using the Common Astronomy Software Applications package (CASA;" (2.1 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA 5.6 tclean  
  > "Visibility data from the ALMA 12-m arrays are cleaned using the CASA 5.6 tclean task." (2.1 Observations)
- deconvolver: multiscale  
  > "and a multiscale deconvolver" (2.1 Observations)
- weighting robust: natural weighting  
  > "This was done by applying the natural weighting, setting the gridder with the ‘pblimit’ parameter of 0.2, and a multiscale deconvolver." (2.1 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: continuum from line-free channels of SPWs 7-8 centred at 99.4 GHz  
  > "SPWs 7-8 were used to create continuum images from the line-free channels centred at 99.4 GHz (or 3 mm)." (2.1 Observations)
- primary beam correction: all images corrected for primary beam; pblimit 0.2  
  > "All images are corrected for the primary beam." (2.1 Observations)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Spectral setups, flux and phase calibrators  
  > "where more details about the spectral setups, flux and phase calibrators can be found." (2.1 Observations) [from (cite: 2020MNRAS.496.2790LiuT; 2020MNRAS.496.2821LiuT)]
- Procedure to identify and fit EA and DE with XCLASS  
  > "we use the same procedure to identify and calculate parameters for EA and DE, as described in (cite: 2022MNRAS.511.3463Qin)." (3.1 Line identification) [from (cite: 2022MNRAS.511.3463Qin)]
- Continuum contribution correction to line emission  
  > "We have estimated the continuum contribution to the line emission using Eq. (5) from the paper of (cite: 2020A&A...635A..48Manigand)." (3.1 Line identification) [from (cite: 2020A&A...635A..48Manigand)]
- Local noise calculation for spectra  
  > "The method for calculating the local noise for each window was adopted from (cite: 2021NatAs...5..188Loomis)." (Additional figures) [from (cite: 2021NatAs...5..188Loomis)]

### Not stated but needed to reproduce (our reading)

- Initial guesses and prior ranges for MAGIX/XCLASS fits
- Which sources used manual first-step fits versus MAGIX results
- Line-free channel selection and continuum-subtraction method
- Image size, cell size and clean thresholds
- Flux calibration accuracy
- Source sizes per source are in Qin et al. 2022, not reproduced here
- Exact sample list and criteria for 'well fitted' sources

## Analysis recipe

1. **Image and extract spectra**: tclean of 12-m data, spectra extracted from a beam-sized area centred on the continuum peak  
  > "The spectra of our sample were extracted from an area corresponding to the size of the beam, centred on the peak of the continuum." (2.1 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Check continuum contribution and dust attenuation**: Correction factor via Manigand Eq. 5 and dust optical depth via Möller Eq. 4; both found negligible  
  > "The dust optical depths in our sample are less than 0.08." (3.1 Line identification)
   - parameter: correction factors 0.99-1.1  
  > "The correction factors range from 0.99-1.1." (3.1 Line identification)
   - fitting: _not stated_
   - validation: _not stated_
3. **Manual LTE fit**: Source size from continuum deconvolved size; velocity offsets from CH3OH line; Tex, N and line width adjusted manually to match the observed spectra  
  > "The rotation temperature, column density, and line width were manually adjusted to achieve a reasonable match between the synthetic and observed spectra." (3.1 Line identification)
   - software: XCLASS, CDMS, JPL
   - assumption: LTE  
  > "Assuming molecular gas is in local thermodynamic equilibrium (LTE) and solving the radiative transfer equation" (3.1 Line identification)
   - fitting: manual  
  > "The rotation temperature, column density, and line width were manually adjusted to achieve a reasonable match between the synthetic and observed spectra." (3.1 Line identification)
   - validation: blending checked using modelled CH3OH, C2H5CN, CH3OCHO spectra  
  > "We also plot modelled spectra of three molecules (CH$_3$OH, C$_2$H$_5$CN, and CH$_3$OCHO) from (cite: 2022MNRAS.511.3463Qin) in order to assess the potential blending issue." (3.1 Line identification)
4. **Optimised fit with error estimates**: Line width fixed; MAGIX with Levenberg-Marquardt and MCMC to get Tex and N with errors  
  > "the Levenberg-Marquardt algorithm (LM) and the Markov chain Monte Carlo algorithm (MCMC) are employed to estimate the errors in the derived rotation temperatures and column densities." (3.1 Line identification)
   - software: XCLASS, MAGIX
   - parameter: For sources with one or two lines, T fixed at 150 K (100-200 K gave <20% variation)  
  > "We chose a median value of 150 K to derive their column densities." (3.1 Line identification)
   - fitting: LM and MCMC via MAGIX; priors not stated  
  > "the Levenberg-Marquardt algorithm (LM) and the Markov chain Monte Carlo algorithm (MCMC) are employed to estimate the errors in the derived rotation temperatures and column densities." (3.1 Line identification)
   - validation: non-converging sources fall back to step-1 results  
  > "In some sources, the MAGIX calculations do not converge, so we show the results from the first step." (3.1 Line identification)
5. **Correlation and ratio analysis with literature sample**: Compute N(EA or DE)/N(CH3OH), EA/DE ratios, and correlation coefficients combining 39 sources with 28 literature sources  
  > "we include all 39 sources from groups A and B, as well as 28 sources from the literature." (4.1)
   - fitting: _not stated_
   - validation: Compared Tex of EA/DE with literature  
  > "The comparable rotation temperatures between ours and those in the literature indicate that the measured column densities are consistent." (4.1)

## Software

- **CASA** 5.6: calibration, tclean imaging  
  > "cleaned using the CASA 5.6 tclean task" (2.1 Observations)
- **XCLASS** 1.2.5: LTE line identification and fitting  
  > "We used the XCLASS version 1.2.5 for the line fitting" (3.1 Line identification)
- **MAGIX** : optimising Tex and N with LM and MCMC  
  > "We then employ the Modeling and Analysis Generic Interface for eXternal numerical codes (MAGIX;" (3.1 Line identification)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| EA detections | 40 of 60 hot cores | not stated | sources | 3 | EA is detected in 40 hot cores and DE is detected in 59 hot cores. |
| Average Trot EA (groups A+B) | 167 | ±14 | K | 4 | with an average value of $167\pm14$ K |
| Average Trot DE (groups A+B) | 136 | ±12 | K | 4 | with an average value of $136\pm12$ K |
| Average N(EA) | 1.9e17 | ±0.1e17 | cm^-2 | 4 | with an average value of $1.9 \pm 0.1 \times$ 10$^{17}$ cm$^{-2}$ |
| Average N(DE) | 4.2e17 | ±0.1e17 | cm^-2 | 4 | with an average value of $4.2 \pm 0.1 \times$ 10$^{17}$ cm$^{-2}$ |
| Mean EA/DE column density ratio | 0.60 | range 0.1-2.1 | dimensionless | 5 | ranging from 0.1 to 2.1 with an average value of 0.60 |
| Correlation coefficient EA vs DE column densities | 0.92 | not stated | dimensionless | 5 | EA and DE ($\rho$ = 0.92) |

## Qualitative findings

- EA/DE ratios stay within about one order of magnitude regardless of CH3OH column density, temperature, or hot core vs hot corino  
  > "the EA/DE ratios of our sample remain within one order of magnitude regardless of whether the sources are hot corinos or hot cores." (4.2)

## Claim tuples

- H: EA, DE and CH3OH are chemically linked | E: Correlate column densities of EA, DE and CH3OH across 39 ATOMS cores plus 28 literature sources | R: rho = 0.92 (EA-DE), 0.82 (EA-CH3OH), 0.80 (DE-CH3OH); EA/DE nearly constant | F: CH3OH may be a precursor of EA and DE | **supported**
- H: Chemical models reproduce observed EA and DE abundances | E: Compare with Garrod et al. 2022 warm-up models | R: EA overproduced and DE underproduced | F: Models need radical-radical pathways from CH3OH photodissociation products | **supported**
- H: EA and DE have different excitation temperatures | E: XCLASS fits in 25 sources with well-fitted Tex | R: EA 167±14 K vs DE 136±12 K | F: EA generally warmer than DE | **supported**

## Reasoning

- Why this data: Large sample with similar spatial resolution and the same spectral coverage  
  > "large sample observations of EA and DE molecules with similar spatial resolutions and the same spectral coverage are still lacking." (1 Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Source sizes from continuum may bias column densities where line emission is not co-spatial  
  > "the adopted source sizes from the continuum may lead to an underestimation of molecular column densities if the molecular emission more compact than the continuum emissions" (3.1 Line identification)
- Limitation (authors): EA non-detection in some cores cannot be confirmed because low-Eup, high-A lines are not covered  
  > "observations at other wavelengths are needed to confirm the absence of EA in these sources" (3.1 Line identification)
- Caveat (inferred, ours): Many sources have only 1-2 DE lines, with Tex fixed at 150 K
- Caveat (inferred, ours): Manual first-step fits are subjective
- Caveat (inferred, ours): Pearson/Spearman use is not clearly specified
- Caveat (inferred, ours): Literature sources use varied methods and source sizes
- Caveat (inferred, ours): The abstract's rho values are not clearly defined as Spearman or Pearson

## Reproducibility

- Data public (paper): Raw data available in ALMA archive  
  > "The raw data are available in ALMA archive." (Data Availability)
- Products in archive: _not stated_
- Missing: Fit priors and starting values
- Missing: Per-source source sizes (in Qin et al. 2022)
- Missing: Imaging cell/image size
- Missing: Line-free channel selection
- Data volume (inferred): Moderate; ~60 sources of 12-m Band 3 data from one project, likely tens of GB
- Score (inferred): 3/5, Public data and named software, but manual fits and inherited procedures leave key settings unspecified.
- Rediscovery candidate: no, Fitting is partly manual and depends on previous-paper source sizes and fitting setups.

## Links

- Method: (cite: 2022MNRAS.511.3463Qin) (Hot core identification, source sizes, XCLASS procedure)
- Method: (cite: 2020MNRAS.496.2790LiuT) (ATOMS survey data description, calibration)
- Companion: (cite: 2020MNRAS.496.2821LiuT) (ATOMS survey data presentation)
- Related: ATOMS

## Checks

```json
{
 "quotes": 65,
 "quotes_ok": 65,
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
  "facts": 75,
  "stated": 49,
  "rate": 0.653
 },
 "evidence_ok": true
}
```
