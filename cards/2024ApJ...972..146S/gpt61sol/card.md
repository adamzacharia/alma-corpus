# Interstellar Glycolaldehyde, Methyl Formate, and Acetic Acid. II. Chemical Modeling of the Bimodal Abundance Pattern in NGC 6334I

`2024ApJ...972..146S` | The Astrophysical Journal 2024 | first author: Shope, Brielle M. | arXiv: 2409.13673 | DOI: 10.3847/1538-4357/ad5d5f

Card schema 1.0 | model gpt-6.1-sol | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: astrochemistry, star_formation
- Question: Which physical conditions reproduce the extreme MF:GA ratios and bimodal abundance pattern in NGC 6334I?  
  > "By varying these parameters, we investigate which parameter combinations best reproduce the observed isomer abundance ratios in the twelve sources of the star forming regions MM1 and MM2 in the massive protocluster NGC6334I (cite: El_Abd_2019)." (Introduction)
- Target **NGC 6334I MM1**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **NGC 6334I MM2**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **IRAS 16293B**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **Sgr B2(N2)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00712.S, 2013.1.00278.S, 2011.0.00017.S, 2012.1.00012.S
- bands: Band 7; two tunings toward NGC 6334I  
  > "data from two Band 7 ALMA tunings toward the protocluster NGC 6334I." (Observational Comparisons)
- frequencies and spectral setup: spectral resolution of 1.1 km s^-1  
  > "spectral resolution of 1.1 km s$^{-1}$" (Observational Comparisons)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: full-width half-power beam size of 20 arcsec  
  > "These observations were done with a full-width half-power beam size of $20\ensuremath{''}$" (Observational Comparisons)
- max recoverable scale: _not stated_
- sensitivity: rms per channel of 2.0 mJy beam^-1  
  > "rms per channel of 2.0 mJy beam$^{-1}$." (Observational Comparisons)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: methyl formate (MF) not stated (not stated)
- Line: glycolaldehyde (GA) not stated (not stated)
- Line: acetic acid (AA) not stated (not stated)
- External data: MF, GA and AA column densities and ratios at twelve NGC 6334I positions: nine in MM1 and three in MM2  
  > "MF:GA and MF:AA ratios for the 12 sources in NGC 6334I observed by (cite: El_Abd_2019)." (Table 2); "Spectra were extracted from nine positions in MM1 and from three positions in MM2, for a total of twelve locations observed in this star forming region." (Observational Comparisons) [from (cite: El_Abd_2019)]
- External data: PILS column density data for IRAS 16293B  
  > "using column density data from the PILS (cite: jorg2016) and EMoCA (cite: belloche_2016) ALMA line surveys, respectively." (Comparisons with IRAS 16293B and Sgr B2(N)) [from PILS (cite: jorg2016)]
- External data: EMoCA column density data for Sgr B2(N2)  
  > "using column density data from the PILS (cite: jorg2016) and EMoCA (cite: belloche_2016) ALMA line surveys, respectively." (Comparisons with IRAS 16293B and Sgr B2(N)) [from EMoCA (cite: belloche_2016)]
- External data: Observed ratios used by G22: 24 PILS and 19 EMoCA molecular column densities before exclusions  
  > "The observed ratios are the same as those used by G22, which were provided in the review of (cite: jorg_review2020)" (Matching Parameter); "for IRAS 16293B, this included a total of 24 molecular column densities from the PILS survey, while for Sgr B2(N2) 19 values were available from the EMoCA survey." (Matching Parameter) [from (cite: jorg_review2020)]
- External data: Atomic-H surface binding energy 661 K and diffusion barrier 243 K on ASW  
  > "As per G22, the surface binding energy of atomic H is taken as 661 K and the diffusion barrier as 243 K, corresponding to the average values calculated by (cite: SENEVIRATHNE201759) for H on ASW." (Methods) [from (cite: SENEVIRATHNE201759)]
- External data: MF binding energy 4210 K on water ice; GA binding energy greater than MF  
  > "In this model, water has a binding energy of 5700 K, while the value for MF is 4210 K (cite: Burke15), based on desorption from a water-ice surface." (Gas-Phase Split in MF and GA Abundances); "Conversely, GA has much greater binding energy (cite: Burke15) compared with MF" (Gas-Phase Split in MF and GA Abundances) [from (cite: Burke15)]
- External data: Activation barriers for glyoxal–glycolaldehyde–ethylene glycol H-addition and abstraction pathways  
  > "using activation barriers partially based on rates provided by (cite: simons_2020), who based their rate parameters on calculations by (cite: barcia_2018)." (Introduction) [from (cite: simons_2020); (cite: barcia_2018)]
- External data: Calculated variation between functionals used to choose a 25% activation-barrier sensitivity test  
  > "This value was chosen to correspond to the approximate degree of variation in activation energy barriers for these reactions calculated by (cite: barcia_2018) when adopting different functionals (see their table A.2)." (Activation-Energy Barrier Testing) [from (cite: barcia_2018)]
- External data: Atomic-H sticking coefficient near 0.3 for a 70 K dust surface and 150 K gas  
  > "(cite: Dupuy_2016) also calculated rates at dust temperatures as high as 70 K" (Density and timescale thresholds for large MF:GA ratios); "with a gas temperature of 150 K, they determined a sticking coefficient of H to an amorphous water-ice surface of $\sim$0.3." (Density and timescale thresholds for large MF:GA ratios) [from (cite: Dupuy_2016)]
- External data: 1-D radiation hydrodynamical trajectories with residence around 1500 yr in the 125–160 K regime  
  > "those determined in the chemical/dynamical models of (cite: Barger_2021); those authors presented 1-D radiation hydrodynamical (RHD) models for hot cores of several different mass-accretion rates." (Density and timescale thresholds for large MF:GA ratios); "Many of these particles remained in the 125–160 K regime for around 1500 yr" (Density and timescale thresholds for large MF:GA ratios) [from (cite: Barger_2021)]
- Simulation/model as data: MAGICKAL three-phase gas, grain-surface and bulk-ice chemistry  
  > "MAGICKAL (cite: Garrod_2013) is a three-phase model used to calculate and solve the coupled rate equations that govern the chemistry occurring in the gas, grain-surface, and bulk-ice phases." (Methods)
- Simulation/model as data: 84 stage-1 models and 756 stage-2 models  
  > "The full grid of physical parameters is varied to test every combination; this results in a total of 84 stage-1 models." (Model Grid Parameters); "The total number of stage-2 model runs is thus 756." (Model Grid Parameters)

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

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- G22 final chemical-model setup, except the chemical network  
  > "Except for the chemical network employed, the chemical model used here is identical to the “`final`” model setup presented by G22." (Methods); "The reader should refer to G22 for detailed descriptions of all of the main features of the model." (Methods) [from G22 (cite: Garrod_2022)]
- M4 chemical network, including additional gas-phase proton-transfer reactions  
  > "The chemical network used here is that presented by (cite: G&H23) for their M4 setup" (Methods) [from (cite: G&H23)]
- Atomic-H binding and diffusion barriers; unity sticking coefficient  
  > "As per G22, the surface binding energy of atomic H is taken as 661 K and the diffusion barrier as 243 K" (Methods); "As in G22, the sticking coefficient for all species is unity." (Methods) [from G22]
- Initial collapse density and initial extinction choices  
  > "The initial density for each stage-1 run is set to the same value for all model runs (cite: Garrod_2022)" (Physical model); "where $A_\mathrm{V,initial}$ assumes a value of either 2 or 3 mag (cite: Garrod_2022)." (Physical model) [from (cite: Garrod_2022)]
- Stage-1 dust temperature as a function of visual extinction  
  > "The dust temperature in stage 1 varies as a function of visual extinction (cite: Garrod_2011)" (Physical model) [from (cite: Garrod_2011)]
- Uniform grain radius 0.1 micrometre and warm-up timescale defined by reaching 200 K  
  > "The dust grains are assumed to have a uniform radius of 0.1 $\mu$m, following past models." (Physical model); "The characteristic warm-up timescale, $t_\mathrm{wu}$, which is varied within the model grid, corresponds to the time taken to reach 200 K, following past models." (Physical model) [from past models]
- NGC 6334I observational column densities and extraction; observation details deferred  
  > "In their work, the column densities of MF, GA, and AA were obtained for lines of sight within the two sources in NGC 6334I, MM1 and MM2." (Observational Comparisons); "More details can be found in (cite: El_Abd_2019), (cite: Hunter_2017), (cite: McGuire2017) and (cite: Brogan_2018)." (Observational Comparisons) [from (cite: El_Abd_2019); (cite: Hunter_2017); (cite: McGuire2017); (cite: Brogan_2018)]
- Peak stage-2 gas-phase abundances used for observational comparisons  
  > "Following G22 and related studies in which output data from the MAGICKAL model has been compared with gas-phase observational abundance values for hot cores/corinos, we use the *peak* gas-phase abundance produced by the stage-2 models for comparison with observations." (Matching parameter) [from G22 and related studies]
- Peak-abundance region/time assumed representative of observed molecular emission  
  > "We therefore assume that this region/time of peak molecular abundance is representative of the observed emission from these molecules (cite: Belloche_2019)." (Matching parameter) [from (cite: Belloche_2019)]
- PILS and EMoCA comparison and observed ratios used by G22  
  > "Following G22, we also compare our model results with observations of IRAS 16293B and Sgr B2(N2)" (Comparisons with IRAS 16293B and Sgr B2(N)); "The observed ratios are the same as those used by G22, which were provided in the review of (cite: jorg_review2020)" (Matching Parameter) [from G22; (cite: jorg_review2020)]
- Network limitations used to exclude molecules from appendix matching  
  > "we further exclude some species from the analysis for which the G22 chemical network is uncertain or likely incomplete" (Matching Parameter); "(see G22 for a brief discussion of this issue)." (Matching Parameter) [from G22]

### Not stated but needed to reproduce (our reading)

- Numerical initial hydrogen density and initial elemental/chemical abundances for stage 1.
- Complete executable M4 network, reaction-rate coefficients and adopted species binding energies.
- Exact temperature-versus-time warm-up function and extinction-to-dust-temperature prescription.
- MAGICKAL version, numerical solver settings and output sampling used to locate abundance peaks.
- Resolution of the MF abundance-cut discrepancy: 10^-9 n_H in the matching method versus 10^-8 n_H in the warm-up discussion.
- For independent ALMA reanalysis: spectral-window frequencies, fitted transitions, extraction coordinates, column-density fitting settings, calibration and imaging recipe.

## Analysis recipe

1. **Configure the chemical model**: Solve coupled gas, grain-surface and bulk-ice rate equations with the G22 final setup and M4 network  
  > "MAGICKAL (cite: Garrod_2013) is a three-phase model used to calculate and solve the coupled rate equations that govern the chemistry occurring in the gas, grain-surface, and bulk-ice phases." (Methods); "The chemical network used here is that presented by (cite: G&H23) for their M4 setup" (Methods)
   - software: MAGICKAL
   - parameter: 749 gas-phase species; 318 grain-surface species and the same number in bulk ice; 22,401 reactions and processes  
  > "The chemical network includes a total of 749 gas-phase species, and 318 (neutral) grain-surface species, with the same number of species also traced in the bulk ice." (Methods); "There is a total of 22,401 reactions and processes, including transfer of atoms/molecules between the surface and bulk ice." (Methods)
   - parameter: H surface binding energy 661 K; diffusion barrier 243 K; tunneling barrier width 3.2 Å  
  > "As per G22, the surface binding energy of atomic H is taken as 661 K and the diffusion barrier as 243 K" (Methods); "Tunneling rates are used (based on a barrier width of 3.2Å, corresponding to a majority water ice) in cases where those rates exceed the thermal diffusion rates." (Methods)
   - assumption: Bulk diffusion limited to interstitial H and H2; bulk barriers twice surface barriers  
  > "diffusion within the bulk ice is limited to H and H$_2$, which are assumed to exist in interstitial positions within the ice matrix." (Methods); "Bulk-ice diffusion rates for H and H$_2$ are based on barriers twice the strength of the surface barriers." (Methods)
   - assumption: Unity sticking coefficient for all species  
  > "As in G22, the sticking coefficient for all species is unity." (Methods)
   - fitting: _not stated_
   - validation: _not stated_
2. **Generate collapse and warm-up histories**: Free-fall collapse followed by gas/dust warm-up; test every physical-parameter combination  
  > "the first stage represents the isothermal, free-fall collapse of a dense core from an initially diffuse/translucent state, with the gas temperature held constant at 10 K." (Physical model); "Stage 2 of the physical model involves the gradual warm-up of the gas and dust, while all other physical quantities are held steady (using their final values from stage 1)." (Physical model); "The full grid of physical parameters is varied to test every combination" (Model Grid Parameters)
   - software: MAGICKAL
   - parameter: Initial extinction 2 or 3 mag; final n_H from 2×10^6 to 2×10^10 cm^-3, including 6.32×10^7 cm^-3  
  > "The initial visual extinction in stage 1 is set at either 2 or 3 mag." (Model Grid Parameters); "we adopt final hydrogen number densities, $n_{\mathrm{H}}$, from $2\times10^6$ to $2\times10^{10}$ cm$^{-3}$" (Model Grid Parameters); "a logarithmically intermediate value of $6.32\times10^7$ cm$^{-3}$ was included in the grid." (Model Grid Parameters)
   - parameter: CRIR 1.30×10^-18 to 1.30×10^-15 s^-1; constant through both stages  
  > "$1.30\times10^{-18}$" (Table 1); "$1.30\times10^{-15}$" (Table 1); "Each chosen CRIR value is applied throughout both stage 1 and 2, and does not vary with time or column density in these models." (Model Grid Parameters)
   - parameter: Warm-up timescales 2×10^4 to 2×10^6 yr; final temperature 400 K  
  > "ranging from $2\times10^4$ to $2\times10^6$ yr" (Model Grid Parameters); "until they reach a final temperature of 400 K." (Physical model)
   - assumption: Uniform grain radius 0.1 micrometre; visual extinction capped at 500 mag  
  > "The dust grains are assumed to have a uniform radius of 0.1 $\mu$m, following past models." (Physical model); "The visual extinction is capped at a value of 500 mag." (Physical model)
   - fitting: _not stated_
   - validation: Standard model compared with G22 abundance behavior  
  > "The first of the three models (Fig. [1](#fig:abundances1)) is essentially the same as that presented by G22" (Results)
3. **Extract model abundance ratios**: Ratio the separate peak stage-2 gas-phase abundances  
  > "the modeled MF:GA ratio is calculated as the ratio of the peak gas-phase MF abundance to the peak gas-phase GA abundance." (Matching parameter)
   - software: MAGICKAL
   - assumption: Peak-abundance ratios directly comparable with observed column-density ratios despite no spatial model  
  > "In the absence of a spatial model of the distribution of the COMs, we therefore assume that the ratio of peak abundances between different molecules should be directly comparable with observed column density ratios." (Matching parameter)
   - fitting: _not stated_
   - validation: Inspect peak-temperature offsets; variation in ratios at different peak times omitted from matching  
  > "the models will necessarily display some variation depending on whether the ratio is taken, for example, at the time/temperature of the MF peak, or that of GA." (Comparison of Peak Abundance Values); "In the interests of simplicity, this variation is not taken into account in the model comparisons." (Comparison of Peak Abundance Values)
4. **Filter and score models**: Exclude low-abundance models; calculate m = sqrt(sum m_i^2), with m_i = log(R_mod,i/R_obs,i)  
  > "m=\sqrt{m_1^2 + m_2^2 + ...}" (Matching parameter); "m_i = \log\left(\frac{R_{\text{mod,i}}}{R_{\text{obs,i}}}\right)." (Matching parameter); "To avoid the consideration of models with unrealistically low molecular abundances, thresholds were set for the two key molecules methyl formate and methanol." (Comparisons with NGC 6334I)
   - parameter: Reject gas-phase MF below 10^-9 n_H or peak methanol below 10^-6 n_H  
  > "Models for which the gas-phase methyl formate abundance falls below $10^{-9}\text{n}_\text{H}$, are removed from consideration as best-match models." (Comparisons with NGC 6334I); "we also remove models with peak methanol abundances less than $10^{-6}\text{n}_\text{H}$" (Comparisons with NGC 6334I)
   - assumption: Use molecular ratios rather than absolute observed abundances  
  > "$R_\text{obs,i}$ and $R_\mathrm{mod,i}$ are taken as molecular ratios with respect to some standard molecule." (Matching parameter)
   - fitting: Lowest m selects best match; m = 0 is perfect  
  > "independently selects the best matching (lowest $m$) model for each sight-line." (Comparisons with NGC 6334I); "with $m=0$ being a perfect match." (Matching parameter)
   - validation: _not stated_
5. **Match the NGC 6334I sight-lines**: Compare MF:GA and MF:AA under unrestricted, shared-CRIR/extinction, and separate-MM1/MM2 constraints  
  > "comparisons of the chemical models with lines of sight toward NGC 6334I focus specifically on the MF:GA and MF:AA ratios." (Comparisons with NGC 6334I); "No constraints: Matching procedure runs through all models and independently selects the best matching (lowest $m$) model for each sight-line." (Comparisons with NGC 6334I); "For matching procedure #3, the same constraints as matching procedure #2 are used, but sources MM1 and MM2 are considered separately, allowing them to settle on independent best-match" (Comparisons with NGC 6334I)
   - parameter: Procedure #2: 14 CRIR/extinction combinations, each with 54 density/timescale models  
  > "a model dataset of six density values and nine warm-up timescales (a total of 54 models) is compared with each of the twelve NGC 6334I sight-lines." (Comparisons with NGC 6334I); "For each of the 14" (Comparisons with NGC 6334I)
   - parameter: For GA upper limits, model MF:GA at or above the observed lower limit gives m_1 = 0  
  > "In cases where the observational value of MF:GA is based on an upper limit for the column density of GA, models that achieve a ratio that matches *or exceeds* the observed value are assigned a perfect match parameter" (Comparisons with NGC 6334I)
   - assumption: Procedure #2 assumes shared CRIR and initial extinction across all sight-lines  
  > "Assumes that all sight-lines in NGC 6334I must have a shared $\zeta$-value." (Comparisons with NGC 6334I); "A shared $A_\mathrm{V,initial}$ value is also selected, to indicate a common background/ambient visual extinction for the cloud in its initial state." (Comparisons with NGC 6334I)
   - fitting: Combine source best-match m-values; choose the CRIR/extinction combination with lowest overall m  
  > "the $m$-values of the best matching models for each of the sources are combined" (Comparisons with NGC 6334I); "combination with the lowest overall $m$-value is considered the best overall match to the observations." (Comparisons with NGC 6334I)
   - validation: Compare parameter stability across the three matching procedures  
  > "The stage-2 gas density and warm-up timescale, however, appear to be somewhat more robust when imposing the three different matching procedures." (Discussion)
6. **Identify the chemical mechanism and threshold**: Inspect time-dependent abundances, summed formation/destruction rates and MF:GA versus density for each warm-up timescale  
  > "These rates correspond to the sum of formation and destruction of the same molecule over all phases (i.e. gas, grain-surface and bulk-ice)." (Early Formation Mechanisms); "plots the peak MF:GA ratio produced in the models against the stage-2 gas density" (Density and timescale thresholds for large MF:GA ratios); "Each curve corresponds to a different warm-up timescale" (Density and timescale thresholds for large MF:GA ratios)
   - software: MAGICKAL
   - parameter: Critical GA surface-destruction regime approximately 125–160 K  
  > "In our model, GA destruction by adsorbed atomic H occurs mainly in the temperature range $\sim$125–160 K" (Density and timescale thresholds for large MF:GA ratios)
   - assumption: Water-ice trapping exposes MF and GA progressively during desorption  
  > "as material is lost from the surface monolayer, material in the bulk ice beneath is exposed, becoming the new surface." (Gas-Phase Split in MF and GA Abundances)
   - fitting: _not stated_
   - validation: Assess sensitivity to H sticking and binding assumptions  
  > "The use of a temperature-dependent sticking coefficient in the model would therefore be expected to shift the density threshold to a higher value than the present models suggest, likely by a factor of a few." (Density and timescale thresholds for large MF:GA ratios)
7. **Test reaction-barrier sensitivity**: Reduce H+GA surface/ice activation barriers by 25% and compare MF:GA density curves  
  > "In a set of test models, the activation-energy barriers of the grain-surface/ice reactions of atomic H with glycolaldehyde were reduced by 25%" (Activation-Energy Barrier Testing)
   - software: MAGICKAL
   - parameter: Three warm-up timescales; standard CRIR; initial extinction 2 mag  
  > "Three timescales were chosen to evaluate the effect of the lowered reaction barrier, using a setup that adopts the standard $\zeta$-value and an initial $A_{\mathrm{V}}$ of 2." (Activation-Energy Barrier Testing)
   - assumption: 25% reduction represents approximate calculated variation between functionals  
  > "This value was chosen to correspond to the approximate degree of variation in activation energy barriers for these reactions calculated by (cite: barcia_2018) when adopting different functionals" (Activation-Energy Barrier Testing)
   - fitting: _not stated_
   - validation: Modest abundance-ratio effect; threshold density essentially unaffected  
  > "This alteration of the GA reaction barriers has a modest and fairly uniform effect on the models tested, especially at densities greater than the threshold value." (Activation-Energy Barrier Testing); "However, the threshold density itself is essentially unaffected by the change." (Activation-Energy Barrier Testing)
8. **Compare with PILS and EMoCA**: Match peak abundances relative to methanol against observed column-density ratios; rank the grid  
  > "$R_\text{mod,i}$ represents the ratio of the peak fractional abundance of molecule $i$ versus that of methanol" (Matching Parameter); "$R_\text{obs,i}$ represents the observed column density ratio of the same two molecules." (Matching Parameter)
   - parameter: 17 PILS and 13 EMoCA molecular column densities after exclusions  
  > "due to the larger number of molecules in the matching procedure (17 versus 13)." (Results)
   - parameter: Exclude acetone, propanal, methyl isocyanate, methyl isocyanide, acetamide, methyl mercaptan and cyanoacetylene  
  > "namely: acetone, (CH$_3$)$_2$CO; propanal, C$_2$H$_5$CHO; methyl isocyanate, CH$_3$NCO; methyl isocyanide, CH$_3$NC; acetamide, CH$_3$C(O)NH$_2$; and methyl mercaptan, CH$_3$SH" (Matching Parameter); "We also exclude cyanoacetylene, HC$_3$N" (Matching Parameter)
   - assumption: Single-point model represents the entirety of each source  
  > "in the context of using a single-point model to represent the entirety of each source" (Results)
   - fitting: Lowest m is best; report four best models and the worst  
  > "The model that has the lowest $m$-value is deemed the best-match model over all of the parameter space" (Results); "we present the top four best-match models for the PILS and EMoCA results" (Results); "Additionally the model that is the worst match to the data (has the highest match parameter value) is included" (Results)
   - validation: Included molecules reproduced within one order of magnitude or better  
  > "In both panels, modeled values for all of the molecules included in the matching procedure come within one order of magnitude (or better) of the observed values." (Results)

## Software

- **MAGICKAL** : Time-dependent three-phase hot-core chemical kinetics  
  > "The gas-grain chemical kinetics model MAGICKAL is used to simulate the time-dependent chemistry in hot cores." (Methods)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Standard-model peak MF:GA ratio | ~1.7 | not stated | dimensionless | 3 | The MF:GA ratio is $\sim$1.7. |
| Standard-model MF:AA ratio | 32 | not stated | dimensionless | 3 | The “standard” model (panel J) has a MF:AA ratio of 32 |
| Model (ii) peak gas-phase MF:GA ratio | 140:1 | not stated | dimensionless | 3 | The gas-phase MF:GA ratio in this model is 140:1. |
| Model (iii) peak gas-phase MF:GA ratio | 235:1 | not stated | dimensionless | 3 | The large split in peak gas-phase abundances of MF and GA is retained in this high-density model, with a MF:GA ratio of 235:1. |
| Procedure #1 best-model MM2-iii MF:GA ratio | 577 | not stated | dimensionless | 5 | the best model for source MM2-iii (ID number 12) reaches MF:GA and MF:AA ratios of 577 and 43.1, respectively |
| Procedure #1 best-model MM2-iii MF:AA ratio | 43.1 | not stated | dimensionless | 5 | the best model for source MM2-iii (ID number 12) reaches MF:GA and MF:AA ratios of 577 and 43.1, respectively |
| Procedure #2 best-panel overall matching parameter | 1.050 | not stated | dimensionless | 5 | The best-matching panel (G) has an overall $m$-value of 1.050 |
| Procedure #2 second-best-panel matching parameter | 1.125 | not stated | dimensionless | 5 | The second best-matching panel has an $m$-value of 1.125 |
| Procedure #3 best-match MM1 CRIR | 1.30 × 10^-15 | not stated | s^-1 | 5 | our matching procedure #3 indicates that MM1 sources should collectively be best matched by a much higher CRIR than MM2; a value of $1.30 \times 10^{-15}$ versus $4.11 \times 10^{-18}$ s$^{-1}$. |
| Procedure #3 best-match MM2 CRIR | 4.11 × 10^-18 | not stated | s^-1 | 5 | our matching procedure #3 indicates that MM1 sources should collectively be best matched by a much higher CRIR than MM2; a value of $1.30 \times 10^{-15}$ versus $4.11 \times 10^{-18}$ s$^{-1}$. |
| MM2 best-match density under procedures #2 and #3 | 2×10^10 | not stated | cm^-3 | 5 | the high density value of $2\times10^{10}$ cm$^{-3}$ and visual extinction of 2 mag are the same as in matching procedure #2 for these three sources. |
| Procedure #3 best-match MM2 warm-up timescale | 2×10^6 | not stated | years | 5 | a longer warm-up timescale of $2\times10^{6}$ years. |
| Approximate density–warm-up product at MF:GA upturn | 3 × 10^13 | not stated | cm^-3 yr | 6 | a value $n_{\mathrm{H}} t_{\text{wu}} \simeq 3 \times 10^{13}$ cm$^{-3}$yr crudely marks the point at which the upturn begins. |
| GA destruction temperature regime | ~125–160 | not stated | K | 6 | In our model, GA destruction by adsorbed atomic H occurs mainly in the temperature range $\sim$125–160 K |
| Desorption timescale relative to full warm-up timescale | ~17 | not stated | dimensionless | 6 | This desorption timescale is shorter by a factor of $\sim$17 compared with the corresponding full warm-up timescale |
| Maximum MF–GA peak-temperature difference across models | 237 | not stated | K | 3 | The maximum peak-to-peak temperature difference between MF and GA in all our models is 237 K. |
| Best-match IRAS 16293B warm-up timescale | 2.00×10^5 | not stated | yr | 8 | / $\#$1 / 1.33 / 3 / $2.00\times10^{7}$ / $4.11\times10^{-17}$ / $2.00\times10^5$ / |
| Best-match Sgr B2(N2) warm-up timescale | 2.00×10^6 | not stated | yr | 8 | / $\#$1 / 1.95 / 3 / $2.00\times10^{8}$ / $1.30\times10^{-17}$ / $2.00\times10^6$ / |
| Best-match PILS matching parameter | 1.33 | not stated | dimensionless | 8 | / $\#$1 / 1.33 / 3 / $2.00\times10^{7}$ / $4.11\times10^{-17}$ / $2.00\times10^5$ / |
| Best-match EMoCA matching parameter | 1.95 | not stated | dimensionless | 8 | / $\#$1 / 1.95 / 3 / $2.00\times10^{8}$ / $1.30\times10^{-17}$ / $2.00\times10^6$ / |

## Qualitative findings

- Selective atomic-H destruction of surface GA during desorption drives extreme gas-phase MF:GA  
  > "We identify the destruction of GA on dust grains as the most influential cause of the divergence in gas-phase MF:GA ratios between different sources." (Conclusions)
- MF escapes rapidly; GA remains exposed to H attack because of different water-ice binding energies  
  > "individual MF molecules escape the surface as soon as they are exposed by water loss, while GA lingers and can be substantially destroyed by H, given the right conditions." (Conclusions)
- AA is protected by higher barriers to reaction with atomic H  
  > "Acetic acid on the ice surface is not affected by the presence or absence of atomic H adsorbed from the gas, in spite of its high binding energy, due to the higher barriers to reaction with atomic H." (Conclusions)
- Initial visual extinction has little effect on MF:GA  
  > "Varying the initial visual extinction produces no significant changes in the MF:GA ratio." (Conclusions)

## Claim tuples

- H: Physical-parameter variations can reproduce the observed isomer ratios | E: Compare a MAGICKAL grid with NGC 6334I MF:GA and MF:AA ratios | R: Models reproduce the observed range | F: A common chemical framework can account for typical and extreme ratios | **supported**
- H: High density and prolonged desorption cause extreme MF:GA | E: Track abundance and reaction-rate changes across density and warm-up grids | R: MF:GA rises above a density–timescale threshold as surface GA is destroyed | F: Adsorbed atomic H selectively destroys GA before desorption | **supported**
- H: Cosmic-ray enhancement alone explains the extreme MF:GA ratios | E: Vary CRIR and compare gas and ice abundance responses | R: Higher CRIR enhances MF:GA modestly; extreme CRIR destroys gas-phase COMs | F: CRIR alone is insufficient and is poorly constrained by the two ratios | **refuted**
- H: Extreme-ratio COM emission originates predominantly in a dense disk | E: Interpret the high-density and desorption-duration requirements | R: Extreme ratios favor high density and sustained ice desorption | F: A dense, long-lived circumstellar disk is a possible origin requiring dynamical modeling | **partially**
- H: The shorter-PILS versus longer-EMoCA warm-up trend persists across a larger parameter grid | E: Match methanol-normalized abundances for IRAS 16293B and Sgr B2(N2) | R: Best warm-up timescales are 2.00×10^5 and 2.00×10^6 yr, respectively | F: The broader-grid comparison retains the relative warm-up trend | **supported**

## Reasoning

- Why this data: Explain the bimodal MF:GA behavior in twelve NGC 6334I sight-lines  
  > "Of particular interest is to identify any physical/chemical origins for the bimodal behavior seen in the MF and GA column densities observed by (cite: El_Abd_2019)" (Observational Comparisons)
- Why this method: Logarithmic matching penalizes a single large divergence more than several small divergences  
  > "the chosen method ensures that, in the case of a non-perfect match, a model producing a single, large divergence is disfavored versus a model that produces many small divergences from the observed values." (Matching parameter)
- Alternative: Do not use the previous fast and slow warm-up values; use logarithmically distributed values spanning them  
  > "Here we choose not to use the *fast* ($5\times10^4$ yr) and *slow* ($1\times10^6$ yr) values adopted in past models, as they fall between the logarithmically distributed values that we have adopted to ensure comparability within the grid." (Model Grid Parameters)
- Alternative: High-CRIR bulk-ice divergence alone cannot explain extreme ratios  
  > "Although this effect is notable, it does not appear sufficient on its own to reproduce the observed extreme MF:GA ratios." (Conclusions)
- Alternative: Luminosity outburst effects require explicit multidimensional, recurring-outburst models  
  > "It is therefore difficult to make predictions as the likely effects on the chemical models without an explicit multi-dimensional physical treatments that includes recurring outburst events." (Influence of luminosity outbursts)
- Alternative: Temperature-dependent H sticking would raise the inferred density threshold  
  > "The use of a temperature-dependent sticking coefficient in the model would therefore be expected to shift the density threshold to a higher value than the present models suggest, likely by a factor of a few." (Density and timescale thresholds for large MF:GA ratios)
- How they decided it was enough: _not stated_
- Limitation (authors): Coarse parameter grid and degeneracy limit unique physical-condition inference  
  > "parameter-tuning might produce not only a better match but a substantial change in the underlying parameters due to the degeneracy of the models in reproducing a limited set of observational data." (Discussion)
- Limitation (authors): Two isomer ratios do not constrain CRIR adequately  
  > "these ratios are not sufficient to determine the most likely CRIR for each source." (Cosmic-Ray Ionization Rates)
- Limitation (authors): Peak ratios omit temporal variation and source spatial structure  
  > "In the interests of simplicity, this variation is not taken into account in the model comparisons." (Comparison of Peak Abundance Values); "The observed molecular abundances are dependent on the spatial arrangement of the molecules and the local density and temperature structure." (Comparison of Peak Abundance Values)
- Limitation (authors): Monotonically increasing temperatures may not represent outburst histories  
  > "the monotonically increasing temperature profiles used in the present chemical models may not be accurate." (Influence of luminosity outbursts)
- Limitation (authors): Exact density and timescale requirements need a dynamical model including disk evolution  
  > "Identifying a very specific timescale or density required to produce a high MF:GA ratio would be best achieved using a more physically and dynamically exact model of hot-core evolution, such as one that includes circumstellar disk evolution." (Density and timescale thresholds for large MF:GA ratios)
- Caveat (inferred, ours): Treat the stated 20 arcsec beam literally; verify it against the cited observational study before re-extraction.
- Caveat (inferred, ours): Resolve the conflicting MF abundance thresholds before selecting acceptable models.
- Caveat (inferred, ours): The text says seven warm-up values, whereas Table 1 and the 756-model accounting require nine.
- Caveat (inferred, ours): The displayed m formula is a root-sum-square without normalization, although the prose calls it root-mean-square.
- Caveat (inferred, ours): Some table entries conflict with the grid: Table 2 includes 6.43×10^5 yr, while Table 1 gives 6.32×10^5 yr.
- Caveat (inferred, ours): Table 5 prints density units as cm^-1; do not silently use this as a physical density unit.
- Caveat (inferred, ours): The disk interpretation is indirect; no disk-resolved emission simulation establishes it.
- Caveat (inferred, ours): The barrier test covers a limited perturbation and does not validate the full reaction network.

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: MAGICKAL source/version and executable G22 final/M4 configuration.
- Missing: Full initial abundances, physical-history functions and numerical integration settings.
- Missing: Resolved abundance-cut and grid-entry inconsistencies.
- Missing: Chemical output tables and matching scripts; outputs are offered only upon request.
- Missing: Complete observational column-density inputs, uncertainties and upper limits from the cited studies.
- Missing: Project-to-target mapping and the observational calibration, imaging and spectral-fitting details needed for a raw-ALMA reproduction.
- Data volume (inferred): Not quantifiable from the text; comparison uses literature column densities and 756 chemical-model histories, with no file sizes or ALMA visibility volumes given.
- Score (inferred): 4/5, The grid and matching logic are described, but essential chemical and physical prescriptions are inherited, executable code is not supplied, outputs require a request, and several settings conflict.
- Rediscovery candidate: no, Numeric model targets are available, but public data access is not established in the text and the executable recipe is incomplete.

## Links

- Method: (cite: Garrod_2013) (MAGICKAL three-phase chemical kinetics model.)
- Method: G22 (cite: Garrod_2022) (Inherited final model setup, physical treatment, nondiffusive chemistry and comparison assumptions.)
- Method: (cite: G&H23) (M4 chemical network.)
- Method: (cite: Garrod_2011) (Stage-1 dust-temperature prescription.)
- Method: (cite: SENEVIRATHNE201759) (Consistent atomic-H binding and diffusion barriers.)
- Method: (cite: Burke15) (Isomer binding-energy inputs underlying selective desorption.)
- Method: (cite: simons_2020); (cite: barcia_2018) (H-addition/abstraction rates, barriers and sensitivity-test motivation.)
- Method: (cite: Belloche_2019) (Representative peak-abundance emission assumption.)
- Companion: (cite: El_Abd_2019) (NGC 6334I observational isomer ratios and bimodal pattern modeled here.)
- Companion: (cite: Hunter_2017); (cite: McGuire2017); (cite: Brogan_2018) (Further details of the NGC 6334I observations.)
- Companion: (cite: jorg2016) (PILS observational comparison.)
- Companion: (cite: belloche_2016) (EMoCA observational comparison.)
- Companion: (cite: jorg_review2020) (Compiled observed ratios used in the appendix.)
- Related: PILS
- Related: EMoCA

## Checks

```json
{
 "quotes": 168,
 "quotes_ok": 168,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 20,
 "numeric_problems": 0,
 "fill": {
  "facts": 134,
  "stated": 82,
  "rate": 0.612
 },
 "evidence_ok": true
}
```
