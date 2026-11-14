# ATOMS: ALMA Three-millimeter Observations of Massive Star-forming regions - XXI. A large-sample observational study of ethanol and dimethyl ether in hot cores

`2025MNRAS.538.2579K` | Monthly Notices of the Royal Astronomical Society 2025 | first author: Kou, Zhiping | arXiv: 2503.07126 | DOI: 10.1093/mnras/staf408

Card schema 1.0 | model claude-opus-5-5 | depth full | type large_program_or_survey

## Science

- Fields: star_formation, astrochemistry
- Question: How do the abundances of ethanol (EA) and dimethyl ether (DE) vary across a large, uniformly observed sample of hot cores, and are EA, DE and CH3OH chemically linked (formation pathways)?  
  > "It is still unknown to what extent the physical environment of the source influences the abundances of EA and DE." (Introduction); "examining their abundance variations and gaining insights into their formation pathways." (Introduction)
- Target **60 ATOMS hot cores (IRAS clumps, e.g. I17441-2822, I18056-1952, I16348-4654)**: coordinates per-source RA/Dec listed in the paper's results table (continuum peaks)  
  > "resulting in the identification of a total of 60 hot cores, with 45 being newly detected (cite: 2022MNRAS.511.3463Qin)." (Hot core sample); "(see Table A1 in (cite: 2020MNRAS.496.2790LiuT))" (Hot core sample); z/distance ~1-12 kpc from the Sun  
  > "resulting in the identification of a total of 60 hot cores, with 45 being newly detected (cite: 2022MNRAS.511.3463Qin)." (Hot core sample); "(see Table A1 in (cite: 2020MNRAS.496.2790LiuT))" (Hot core sample); distance from Table A1 of Liu et al. 2020 (cite: 2020MNRAS.496.2790LiuT)  
  > "resulting in the identification of a total of 60 hot cores, with 45 being newly detected (cite: 2022MNRAS.511.3463Qin)." (Hot core sample); "(see Table A1 in (cite: 2020MNRAS.496.2790LiuT))" (Hot core sample)

## Data provenance

- ALMA projects: 2019.1.00685.S
- bands: Band 3 (3 mm)  
  > "The observations were carried out with ALMA band 3 towards 146 Infrared Astronomical Satellite (IRAS) clumps" (Observations)
- frequencies and spectral setup: 8 SPWs: SPWs 1-6 58.59 MHz bandwidth (0.2-0.4 km/s), SPWs 7-8 1875 MHz (~1.6 km/s); SPW 7 97536-99442 MHz, SPW 8 99470-101390 MHz; only SPWs 7-8 used  
  > "Eight spectral windows (SPWs) were configured, including 6 higher spectral resolutions windows (SPWs 1–6, bandwidth 58.59 MHz with spectral resolution" (Observations); "The frequency ranges of SPWs 7 and 8 are 97536-99442 MHz and 99470-101390 MHz respectively." (Observations)
- continuum bandwidth: line-free channels of SPWs 7-8, centred at 99.4 GHz  
  > "SPWs 7-8 were used to create continuum images from the line-free channels centred at 99.4 GHz (or 3 mm)." (Observations)
- arrays: ACA 7-m and 12-m observed; only 12-m data used in this study  
  > "In this study, we only employ 12 m array data as hot cores typically have smaller source sizes and the COM lines are less affected by missing flux issues" (Observations)
- configurations: C43-2 or C43-3  
  > "Atacama Compact 7-m Array (ACA) and 12-m array (C43-2 or C43-3 configurations) observations were conducted from late September to mid-November 2019." (Observations)
- baselines: _not stated_
- angular resolution: ~1.2"-1.9" (12-m)  
  > "The angular resolution and maximum recovered angular scale for the 12-m array observations are" (Observations)
- max recoverable scale: ~14.5"-20.3" (12-m)  
  > "The angular resolution and maximum recovered angular scale for the 12-m array observations are" (Observations)
- sensitivity: mean 1σ rms of SPWs 7 and 8 better than 10 mJy/beam per channel  
  > "rms noise of SPWs 7 and 8 are better than 10 mJy beam" (Observations)
- time on source: ~3 min per source (12-m), 8 min (ACA 7-m)  
  > "Observational mode was set to single-point mode, with typical on-source times of 3 minutes for 12-m array and 8 minutes per source for ACA 7-m array." (Observations)
- observing dates: late September to mid-November 2019  
  > "observations were conducted from late September to mid-November 2019." (Observations)
- pi or archival as stated: ATOMS project data, PI: Tie Liu  
  > "(2019.1.00685.S, PI: Tie Liu)" (Observations)
- Line: C2H5OH (ethanol) many g-, g+ and anti transitions in SPWs 7-8 (Eup 35-793 K); moment 0 map at 100990 MHz (97535.98-101243.61 MHz (e.g. 100990.11310 MHz))
- Line: CH3OCH3 (dimethyl ether) AA/EE/EA/AE sub-states in SPWs 7-8 (Eup 10-490 K); moment 0 map at 99324 MHz (4(1,4)-3(0,3)) (97990.63-100951.25 MHz (e.g. 99325.2 MHz))
- Line: CH3OH 13(-2,12)-12(-3,10) E, vt=0 (velocity reference) (100.6389 GHz)
- Line: H40α recombination line (HII region tracer) (99022.952 MHz)
- Other facility **CDMS and JPL spectroscopic databases**: spectroscopic data for XCLASS modelling  
  > "We used the XCLASS version 1.2.5 for the line fitting, which incorporates an embedded SQLite database file containing spectroscopic data from CDMS and JPL." (Line identification)
- Other facility **IRAS / CS J=2-1 surveys**: parent sample of 146 massive clumps  
  > "The 146 massive clumps were selected from the CS J = 2 - 1 surveys (cite: bronfman1996cs)." (Observations)
- External data: Hot core identification and deconvolved continuum source sizes (Table 1)  
  > "In the first step, we take deconvolved angular sizes of the continuum sources as source sizes which are given by (cite: 2022MNRAS.511.3463Qin) in their Table 1." (Line identification) [from (cite: 2022MNRAS.511.3463Qin)]
- External data: CH3OH column densities of the sample  
  > "we take the column densities of methanol in our sample from (cite: 2022MNRAS.511.3463Qin)" (Comparison with other sources and parameter correlations) [from (cite: 2022MNRAS.511.3463Qin)]
- External data: Modelled spectra of CH3OH, C2H5CN, CH3OCHO for blending assessment  
  > "from (cite: 2022MNRAS.511.3463Qin) in order to assess the potential blending issue." (Line identification) [from (cite: 2022MNRAS.511.3463Qin)]
- External data: Hydrogen column densities (Tables C1-C4) for dust optical depth  
  > "The hydrogen column densities were obtained from (cite: 2025A&A...694A.166C) (in their Tables C1-C4)." (Line identification) [from (cite: 2025A&A...694A.166C)]
- External data: Column densities and temperatures of CH3OH, EA, DE for 28 literature hot cores and hot corinos (Table A.4)  
  > "In Table [\[tab:A.4\]](#tab:A.4), we summarize the column densities of CH$_3$OH, EA, and DE from the literature." (Comparison with other sources and parameter correlations) [from literature references 1-13 in Table A.4]
- External data: Source luminosities and distances  
  > "(see Table A1 in (cite: 2020MNRAS.496.2790LiuT))" (Hot core sample) [from (cite: 2020MNRAS.496.2790LiuT)]
- External data: HII-region association of hot cores  
  > "(UCHii regions) (cite: 2022MNRAS.511.3463Qin; 2023MNRAS.520.3245Z)" (Hot core sample) [from (cite: 2022MNRAS.511.3463Qin; 2023MNRAS.520.3245Z)]
- Simulation/model as data: Chemical models of G22 (three warm-up timescale models) compared with observed abundances  
  > "Compared with chemical models, the three different warm-up timescale models result in the systematic overproduction of EA and the systematic underproduction of DE." (abstract); "There are two main production pathways for EA in the chemical models of G22" (Implications for the chemistry of EA and DE)

## Processing

### Calibration

- pipeline or manual: calibrated and imaged with CASA; details in Liu et al. 2020  
  > "The data were calibrated and imaged using the Common Astronomy Software Applications package (CASA; (cite: 2007ASPC..376..127McMullin))." (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA 5.6 tclean  
  > "Visibility data from the ALMA 12-m arrays are cleaned using the CASA 5.6 tclean task." (Observations)
- deconvolver: multiscale  
  > "This was done by applying the natural weighting, setting the gridder with the ‘pblimit’ parameter of 0.2, and a multiscale deconvolver." (Observations)
- weighting robust: natural  
  > "This was done by applying the natural weighting, setting the gridder with the ‘pblimit’ parameter of 0.2, and a multiscale deconvolver." (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum from line-free channels of SPWs 7-8  
  > "SPWs 7-8 were used to create continuum images from the line-free channels centred at 99.4 GHz (or 3 mm)." (Observations)
- line free channels: _not stated_
- primary beam correction: all images PB-corrected; pblimit = 0.2  
  > "All images are corrected for the primary beam." (Observations)
- array combination: none; 12-m only  
  > "In this study, we only employ 12 m array data" (Observations)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: better than 10 mJy/beam per channel (SPWs 7-8)  
  > "rms noise of SPWs 7 and 8 are better than 10 mJy beam" (Observations)

### Inherited from earlier work

- Spectral setups, flux and phase calibrators and data presentation  
  > "The data were first presented by (cite: 2020MNRAS.496.2790LiuT; 2020MNRAS.496.2821LiuT), where more details about the spectral setups, flux and phase calibrators can be found." (Observations) [from (cite: 2020MNRAS.496.2790LiuT; 2020MNRAS.496.2821LiuT)]
- Line identification and parameter-calculation procedure  
  > "In this work, we use the same procedure to identify and calculate parameters for EA and DE, as described in (cite: 2022MNRAS.511.3463Qin)." (Line identification) [from (cite: 2022MNRAS.511.3463Qin)]
- Continuum contribution estimate (Eq. 5)  
  > "We have estimated the continuum contribution to the line emission using Eq. (5) from the paper of (cite: 2020A&A...635A..48Manigand)." (Line identification) [from (cite: 2020A&A...635A..48Manigand)]
- Dust opacity equation (Eq. 4) for dust optical depth  
  > "To evaluate the dust attenuation, we used the dust opacity equation (see Eq.(4) of (cite: 2021A&A...651A...9Moller) to calculate the dust optical depth." (Line identification) [from (cite: 2021A&A...651A...9Moller)]
- Local noise calculation per window  
  > "The method for calculating the local noise for each window was adopted from (cite: 2021NatAs...5..188Loomis)." (Additional figures) [from (cite: 2021NatAs...5..188Loomis)]

### Not stated but needed to reproduce (our reading)

- Exact line-free channel ranges used for continuum and whether/how continuum was subtracted from line cubes
- Self-calibration (if any) and the CASA/pipeline version used for calibration
- Cell size, image size, masking/cleaning threshold and per-source synthesized beams
- Exact extraction aperture per source (beam size) and the deconvolved source sizes (taken from Qin et al. 2022 Table 1)
- Initial guesses and criteria for the manual XCLASS adjustment in step 1, and MAGIX parameter ranges, MCMC settings and convergence criteria
- Which correlation coefficient (Pearson or Spearman) and which fitting is used for the ρ = 0.92/0.82/0.80 column-density correlations, and whether done in log space
- Velocity offsets and line widths per source
- Dust opacity law, temperature and gas-to-dust parameters in the dust optical depth estimate
- Detection threshold definition for H40α-based HII association

## Analysis recipe

1. **image continuum and line cubes**: CASA tclean of 12-m data for SPWs 7-8; continuum from line-free channels; primary beam correction  
  > "Visibility data from the ALMA 12-m arrays are cleaned using the CASA 5.6 tclean task." (Observations)
   - software: CASA
   - parameter: natural weighting, pblimit 0.2, multiscale deconvolver  
  > "This was done by applying the natural weighting, setting the gridder with the ‘pblimit’ parameter of 0.2, and a multiscale deconvolver." (Observations)
   - assumption: 12-m only suffices because hot cores are compact and COM lines less affected by missing flux  
  > "hot cores typically have smaller source sizes and the COM lines are less affected by missing flux issues" (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **extract spectra**: spectra extracted over beam-sized area centred on the continuum peak  
  > "The spectra of our sample were extracted from an area corresponding to the size of the beam, centred on the peak of the continuum." (Observations)
   - fitting: _not stated_
   - validation: _not stated_
3. **assess continuum and dust attenuation effects**: continuum contribution via Manigand Eq. 5; dust optical depth via Möller Eq. 4 with literature N(H2)  
  > "The correction factors range from 0.99-1.1." (Line identification); "The dust optical depths in our sample are less than 0.08." (Line identification); "Thus, we neglect continuum emission and dust attenuation in our spectral line fitting." (Line identification)
   - fitting: _not stated_
   - validation: _not stated_
4. **identify EA and DE lines and initial LTE fit**: XCLASS LTE radiative transfer modelling; source size fixed to deconvolved continuum size; Trot, N and line width manually adjusted  
  > "Assuming molecular gas is in local thermodynamic equilibrium (LTE) and solving the radiative transfer equation, XCLASS produces theoretical spectra" (Line identification); "The rotation temperature, column density, and line width were manually adjusted to achieve a reasonable match between the synthetic and observed spectra." (Line identification)
   - software: XCLASS
   - parameter: lines above 3σ identified; velocity referenced to CH3OH at 100.6389 GHz  
  > "The velocity offsets are determined with reference to the rest frequency of the" (Line identification)
   - assumption: LTE; source sizes from Qin et al. 2022 Table 1  
  > "In the first step, we take deconvolved angular sizes of the continuum sources as source sizes which are given by (cite: 2022MNRAS.511.3463Qin) in their Table 1." (Line identification)
   - fitting: manual adjustment  
  > "The rotation temperature, column density, and line width were manually adjusted to achieve a reasonable match between the synthetic and observed spectra." (Line identification)
   - validation: blending checked against modelled CH3OH, C2H5CN, CH3OCHO spectra from Qin et al. 2022  
  > "from (cite: 2022MNRAS.511.3463Qin) in order to assess the potential blending issue." (Line identification)
5. **optimize Trot and N with errors**: MAGIX optimization with line width fixed from step 1; LM and MCMC for errors  
  > "In the second step, the line width is set as a fixed parameter based on the first step." (Line identification); "In the calculation, the Levenberg-Marquardt algorithm (LM) and the Markov chain Monte Carlo algorithm (MCMC) are employed to estimate the errors in the derived rotation temperatures and column densities." (Line identification)
   - software: MAGIX, XCLASS
   - fitting: Levenberg-Marquardt + MCMC; step-1 results used when MAGIX does not converge  
  > "In some sources, the MAGIX calculations do not converge, so we show the results from the first step." (Line identification)
   - validation: _not stated_
6. **column densities for poorly constrained sources**: fixed Trot = 150 K for sources with only one or two lines; tested 100/150/200 K  
  > "We calculated the column densities using three different temperatures (100 K, 150 K, and 200 K), which showed a slight increase in column density, with the variation remaining within 20%." (Line identification); "We chose a median value of 150 K to derive their column densities." (Line identification)
   - software: XCLASS
   - assumption: Trot = 150 K  
  > "We chose a median value of 150 K to derive their column densities." (Line identification)
   - fitting: _not stated_
   - validation: column densities vary within 20% over 100-200 K  
  > "with the variation remaining within 20%." (Line identification)
7. **classify sources by detections and HII association**: 5 groups based on EA/DE detection and H40α-traced HII region association  
  > "Based on whether EA and DE are detected and whether hot cores are associated with Hii regions, we classified them into 5 groups" (Line identification)
   - fitting: _not stated_
   - validation: _not stated_
8. **map EA and DE emission**: moment 0 maps of unblended EA (100990 MHz) and DE (99324 MHz) lines compared with continuum  
  > "These two lines are not blended with other molecules." (Line identification); "Overall, the molecular line emissions and the continuum emissions show very similar morphologies in most sources." (Line identification)
   - fitting: _not stated_
   - validation: _not stated_
9. **statistics and correlations of Trot, N, abundances and ratios**: Pearson coefficients between Trot and N; correlations of N(EA), N(DE), N(CH3OH) combined with 28 literature sources; EA/DE ratios and abundances relative to CH3OH  
  > "we include all 39 sources from groups A and B, as well as 28 sources from the literature." (Comparison with other sources and parameter correlations); "We computed the molecular abundances relative to methanol by f$_{\rm CH_3OH}$ = N(EA or DE)/N(CH$_3$OH)" (Comparison with other sources and parameter correlations)
   - fitting: _not stated_
   - validation: comparable rotation temperatures to literature used to argue consistency  
  > "The comparable rotation temperatures between ours and those in the literature indicate that the measured column densities are consistent." (Comparison with other sources and parameter correlations)
10. **compare with chemical models and experiments**: compare observed abundances with G22 warm-up models and laboratory radical–radical recombination results  
  > "Compared with chemical models, the three different warm-up timescale models result in the systematic overproduction of EA and the systematic underproduction of DE." (abstract)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.6 (tclean): calibration and imaging  
  > "Visibility data from the ALMA 12-m arrays are cleaned using the CASA 5.6 tclean task." (Observations)
- **XCLASS** 1.2.5: LTE line identification and fitting; database updated with UpdateDatabase  
  > "We used the XCLASS version 1.2.5 for the line fitting, which incorporates an embedded SQLite database file containing spectroscopic data from CDMS and JPL." (Line identification); "We upgraded this database file by using the XCLASS task UpdateDatabase." (Line identification)
- **MAGIX** : optimizing rotation temperatures and column densities  
  > "(MAGIX; (cite: 2013A&A...549A..21Moller)) to obtain optimized rotation temperatures and column densities." (Line identification)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of hot cores with EA detected | 40 | not stated | sources | 4 | EA is detected in 40 hot cores and DE is detected in 59 hot cores. |
| Number of hot cores with DE detected | 59 | not stated | sources | 4 | EA is detected in 40 hot cores and DE is detected in 59 hot cores. |
| Hot cores with both EA and DE | 39 | not stated | sources | 4 | Of these, EA and DE are simultaneously detected in 39 hot cores. |
| EA rotation temperature range and average (40 hot cores) | 91-215; average 154 | not stated | K | 5 | Rotation temperatures towards 40 hot cores range from 91 to 215 K with an average value of 154 K. |
| DE rotation temperature range and average (59 hot cores) | 102-197; average 143 | not stated | K | 5 | Rotation temperatures towards 59 hot cores range from 102 to 197 K, with an average value of 143 K. |
| Average EA rotation temperature (25 well-fitted group A/B sources) | 167 | ±14 | K | 9 | with EA having a temperature of $167\pm14$ K compared to $136\pm12$ K of DE. |
| Average DE rotation temperature (25 well-fitted group A/B sources) | 136 | ±12 | K | 9 | with EA having a temperature of $167\pm14$ K compared to $136\pm12$ K of DE. |
| Average DE column density (groups A/B) | 4.2e17 | ±0.1e17 | cm^-2 | 9 | with DE having a column density of $4.2\pm0.1$ $\times$ 10$^{17}$ cm$^{-2}$ |
| Average EA column density (groups A/B) | 1.9e17 | ±0.1e17 | cm^-2 | 9 | compared to $1.9\pm0.1$ $\times$ 10$^{17}$ cm$^{-2}$ of EA. |
| Correlation coefficient N(EA)-N(DE) | 0.92 | not stated | dimensionless | 9 | we find strong column density correlations among EA and DE ($\rho$ = 0.92), EA and CH$_3$OH ($\rho$ = 0.82), as well as DE and CH$_3$OH ($\rho$ = 0.80). |
| Correlation coefficient N(EA)-N(CH3OH) | 0.82 | not stated | dimensionless | 9 | we find strong column density correlations among EA and DE ($\rho$ = 0.92), EA and CH$_3$OH ($\rho$ = 0.82), as well as DE and CH$_3$OH ($\rho$ = 0.80). |
| Correlation coefficient N(DE)-N(CH3OH) | 0.80 | not stated | dimensionless | 9 | we find strong column density correlations among EA and DE ($\rho$ = 0.92), EA and CH$_3$OH ($\rho$ = 0.82), as well as DE and CH$_3$OH ($\rho$ = 0.80). |
| EA/DE column density ratio (67 sources) | 0.1-2.1; average 0.60 | not stated | dimensionless | 9 | The column density ratios of EA to DE are within one order of magnitude, ranging from 0.1 to 2.1 with an average value of 0.60. |
| Abundance relative to CH3OH | EA 0.02-0.19; DE 0.06-0.29 | not stated | dimensionless | 9 | The relative abundances range from 0.02 to 0.19 for EA and from 0.06 to 0.29 for DE, respectively |
| Pearson coefficient Trot vs N for EA | 0.4 | not stated | dimensionless | 9 | Pearson’s co-efficient for EA between rotation temperatures and column densities is 0.4, indicating that column densities of EA are not correlated with rotation temperatures. |
| Pearson coefficient Trot vs N for DE | 0.5 | not stated | dimensionless | 9 | Pearson’s co-efficient for DE between rotation temperatures and column densities is 0.5 |
| Pearson coefficient Trot(EA) vs Trot(DE) | 0.44 | not stated | dimensionless | 9 | Rotation temperatures between EA and DE show no correlation, with Pearson’s co-efficient of 0.44. |
| Dust optical depth | < 0.08 | not stated | dimensionless | 3 | The dust optical depths in our sample are less than 0.08. |

## Qualitative findings

- Average rotation temperature of EA is higher than DE; average column density of EA lower than DE  
  > "The average rotation temperature of EA is higher than that of DE, whereas the average column density of EA is lower than that of DE." (abstract)
- EA/DE ratios show no trend with CH3OH column density or rotation temperature, suggesting independence from physical environment  
  > "The nearly stable ratios suggest that the EA/DE ratio does not depend on the physical environment." (Implications for the chemistry of EA and DE)
- Line emission morphologies mostly resemble continuum, but not in some sources  
  > "It should be noted that in some sources, the molecular line emissions of EA and DE are not well associated with the continuum emissions." (Line identification)

## Claim tuples

- H: EA, DE and CH3OH are chemically linked | E: Correlate column densities for 39 ATOMS hot cores plus 28 literature sources | R: ρ = 0.92 (EA-DE), 0.82 (EA-CH3OH), 0.80 (DE-CH3OH); EA/DE ratio 0.1-2.1, mean 0.60 | F: CH3OH may be a precursor of EA and DE | **supported**
- H: EA/DE ratio depends on physical environment | E: Plot EA/DE vs N(CH3OH) and vs Trot of EA and DE | R: No obvious upward or downward trend | F: EA/DE ratio does not depend on physical environment | **refuted**
- H: Radical products of CH3OH dissociation dominate EA and DE formation | E: Compare stable observed ratios with laboratory radical–radical recombination results | R: Observed ratios within one order of magnitude, consistent with experiments | F: Radical–radical recombination may be the predominant mechanism | **partially**
- H: Current chemical models reproduce EA and DE abundances | E: Compare observed abundances with three warm-up timescale models (G22) | R: EA systematically overproduced, DE underproduced | F: Models need revision; sample provides constraints | **refuted**

## Reasoning

- Why this data: Large sample with similar spatial resolution and identical spectral coverage was lacking  
  > "To the best of our knowledge, large sample observations of EA and DE molecules with similar spatial resolutions and the same spectral coverage are still lacking." (Introduction)
- Why this method: Continuum and dust attenuation negligible, so pure LTE line fitting without continuum  
  > "Thus, we neglect continuum emission and dust attenuation in our spectral line fitting." (Line identification)
- Alternative: Fixed temperatures of 100, 200 K tested vs adopted 150 K for poorly constrained sources  
  > "We calculated the column densities using three different temperatures (100 K, 150 K, and 200 K), which showed a slight increase in column density, with the variation remaining within 20%." (Line identification)
- Alternative: DE formation via ground-state CH2 + methanol considered and judged not the main pathway  
  > "We propose that DE formation in chemical models involving ground-state CH$_2$ reactions may not represent the main pathway." (Implications for the chemistry of EA and DE)
- How they decided it was enough: _not stated_
- Limitation (authors): Continuum-based source sizes may bias column densities where line and continuum emission differ  
  > "the adopted source sizes from the continuum may lead to an underestimation of molecular column densities if the molecular emission more compact than the continuum emissions and vice versa." (Line identification)
- Limitation (authors): Rotation temperature unconstrained when only one or two lines are detected  
  > "For sources where only one or two molecular lines of DE and EA were detected, the rotation temperature could not be constrained." (Line identification)
- Limitation (authors): Low-Eup EA lines not covered, so EA non-detections need confirmation at other wavelengths  
  > "observations at other wavelengths are needed to confirm the absence of EA in these sources" (Line identification)
- Limitation (authors): MAGIX did not converge for some sources  
  > "In some sources, the MAGIX calculations do not converge, so we show the results from the first step." (Line identification)
- Caveat (inferred, ours): Average DE temperature quoted as 136±12 K in Sect. 3.2/conclusions but 131±11 K in Sect. 4.1; inconsistency.
- Caveat (inferred, ours): Correlations of column densities across 4 orders of magnitude of CH3OH may be partly driven by shared source size/beam dilution and sample heterogeneity (hot corinos vs hot cores), not necessarily chemistry.
- Caveat (inferred, ours): Several detections rest on single or blended lines; manual first-step fitting introduces subjectivity.
- Caveat (inferred, ours): Correlation coefficient type and significance (p-values) for ρ not given.
- Caveat (inferred, ours): Model comparison details (G22 model parameters, abundances) only briefly presented.

## Reproducibility

- Data public (paper): Raw data in ALMA archive  
  > "The raw data are available in ALMA archive." (Data Availability)
- Products in archive: _not stated_
- Missing: Per-source source sizes, velocity offsets and line widths (from Qin et al. 2022 and step 1)
- Missing: MAGIX/MCMC configuration and parameter bounds
- Missing: Imaging cell/image size, clean thresholds, masks
- Missing: Exact line-free channel selection
- Missing: Literature compilation values for comparison (Table A.4 references)
- Missing: Correlation method details
- Data volume (inferred): Raw 12-m Band 3 data for ~50 ATOMS fields (of 146) of order hundreds of GB; SPW 7-8 cubes per field of order a few GB.
- Score (inferred): 6/5, Public data and named software/versions with clear two-step XCLASS/MAGIX scheme, but manual fitting, inherited source sizes and procedures from Qin et al. 2022, and missing fit/imaging parameters limit exact reproduction.
- Rediscovery candidate: yes, Data are public in the ALMA archive, the LTE fitting recipe (XCLASS 1.2.5 + MAGIX, fixed 150 K fallback) is described, and the main results (detection counts, average Trot, N, correlation coefficients, EA/DE ratio) are numeric; manual initial fitting adds tolerance needs.

## Links

- Method: (cite: 2017A&A...598A...7Moller) (XCLASS software)
- Method: (cite: 2013A&A...549A..21Moller) (MAGIX optimization)
- Method: (cite: 2020A&A...635A..48Manigand) (Eq. 5 continuum contribution correction)
- Method: (cite: 2021A&A...651A...9Moller) (Eq. 4 dust opacity)
- Method: (cite: 2021NatAs...5..188Loomis) (local noise calculation)
- Method: (cite: 2007ASPC..376..127McMullin) (CASA)
- Method: (cite: 2005JMoSt.742..215M); (cite: 1998JQSRT..60..883Pickett) (CDMS and JPL spectroscopic databases)
- Companion: (cite: 2020MNRAS.496.2790LiuT; 2020MNRAS.496.2821LiuT) (ATOMS survey overview, observations and calibration)
- Companion: (cite: 2022MNRAS.511.3463Qin) (ATOMS hot core identification, source sizes, CH3OH column densities and fitting procedure)
- Companion: (cite: 2023MNRAS.520.3245Z) (HII region association)
- Companion: (cite: 2025A&A...694A.166C) (hydrogen column densities)
- Related: ATOMS (ALMA Three-millimeter Observations of Massive Star-forming regions)
- Related: Bronfman et al. 1996 CS J=2-1 survey of IRAS sources

## Checks

```json
{
 "quotes": 118,
 "quotes_ok": 118,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 18,
 "numeric_problems": 0,
 "fill": {
  "facts": 105,
  "stated": 73,
  "rate": 0.695
 },
 "evidence_ok": true
}
```
