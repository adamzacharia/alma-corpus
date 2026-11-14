# Constraints of the Formation and Abundances of Methyl Carbamate, a Glycine Isomer, in Hot Corinos

`2020ApJ...899...65S` | The Astrophysical Journal 2020 | first author: Sahu, Dipen | arXiv: 2006.15629 | DOI: 10.3847/1538-4357/aba0a5

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: astrochemistry, star_formation
- Question: Can methyl carbamate (a glycine isomer) form in hot-corino conditions, and what upper limits on its column density follow from ALMA archival spectra of IRAS 4A2 and IRAS 16293B?  
  > "we present the constraints of methyl carbamate formation under the interstellar conditions." (abstract)
- Target **NGC 1333 IRAS 4A2**: coordinates _not stated_; z/distance ~293 pc  
  > "located in the Perseus molecular cloud at a distance of $\sim$ 293 pc (cite: ortiz18; zucker18)." (4.1 IRAS 4A2); distance from Ortiz-León et al. 2018; Zucker et al. 2018  
  > "located in the Perseus molecular cloud at a distance of $\sim$ 293 pc (cite: ortiz18; zucker18)." (4.1 IRAS 4A2)
- Target **IRAS 16293-2422 B**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00278.S, 2015.1.00147.S
- bands: _not stated_
- frequencies and spectral setup: IRAS 4A2: seven spectral windows, broadband window centered at 350.714 GHz, 1.875 GHz bandwidth, 976 kHz channels (~0.84 km/s); range 349.8-351.6 GHz; IRAS 16293B channel width 0.244 MHz  
  > "deployed seven spectral windows, including one broadband window centered at 350.714 GHz whose bandwidth and spectral channel width are 1.875 GHz and 976 kHz ($\sim$ 0.84 km s$^{-1}$ ), respectively." (4.1 IRAS 4A2); "where the channel width is 0.244 MHz ($\sim 0.2$ km s$^{-1}$ )" (4.2 IRAS 16293)
- continuum bandwidth: _not stated_
- arrays: IRAS 16293B: 12m data only  
  > "we used only the 12m data, suitable to resolve the source without the missing-flux problem." (4.2 IRAS 16293)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: IRAS 4A2 beam ~0.3x0.2 arcsec; IRAS 16293B continuum beam ~0.63x0.39 arcsec  
  > "The synthesized beam size of this spectral data cube is $\sim 0''.3 \times 0''.2$ (PA = $-6.45^{\circ}$)" (4.1 IRAS 4A2); "The synthesized beam size for the dust-continuum map is $\sim 0''.63 \times 0''.39$ (Position angle = $-79.92^{\circ}$)" (4.2 IRAS 16293)
- max recoverable scale: _not stated_
- sensitivity: IRAS 4A2 rms 3 mJy/beam (~0.5 K); IRAS 16293B rms 7-10 mJy/beam (<=0.6 K) as reported by Jørgensen 2016  
  > "the rms noise level ($\sigma$) is 3 mJy beam$^{-1}$ ($\sim 0.5$ K)" (4.1 IRAS 4A2); "(cite: jorgensen16) reported a rms noise level of 7-10 mJy beam$^{-1}$ ($\le 0.6$K)" (4.2 IRAS 16293)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archival ALMA data; IRAS 4A2 data from Sahu et al. 2019 / Su et al. 2019, IRAS 16293 from ALMA archive (Jørgensen et al. 2016)  
  > "The data towards the source were taken from ALMA archive and imaged with the highest possible spectral resolution using CASA pipeline analysis." (4.2 IRAS 16293)
- Line: CH3OC(O)NH2 (methyl carbamate) 18,16,3,1,18-17,15,3,1,17 etc. (351102.99 MHz (also 351056.46, 351162.83, 349907.88, 351232.91 MHz))
- External data: Spectroscopy of methyl carbamate in JPL database  
  > "The spectroscopy data of MC that are available in JPL was studied by (cite: Ilyushin06)." (4.1 IRAS 4A2) [from (cite: Ilyushin06)]
- External data: Observed 13CH3OH column density in IRAS 4A2 and 12C/13C ~35  
  > "we use the observe column density of $\mathrm{^{13}CH_3OH}$ (cite: sahu19) and use $^{12}$C/$^{13}$C ratio $\simeq 35$ (cite: jorgensen16)" (4.1 IRAS 4A2) [from (cite: sahu19); (cite: jorgensen16)]
- External data: Observed abundances of COMs in IRAS 16293B (CH3OH, CH3CHO, CH3OCH3 and HNCO, CH3NCO, NH2CHO)  
  > "the observed column densities for $\mathrm{CH_3OH}$ ,$\mathrm{CH_3CHO}$ and $\mathrm{CH_3OCH_3}$ are $1.0\times 10^{19}$, $1.2\times10^{17}$ cm$^{-2}$, and $2.4\times10^{17}$ respectively (cite: jorgensen16; jorgensen18)." (4.2 IRAS 16293) [from (cite: jorgensen16; jorgensen18); (cite: droz19)]
- External data: Physical model 2 (radiation-hydrodynamical)  
  > "We further draw, as Model 2, the physical model from (cite: aikawa08)" (2.3 Physical models) [from (cite: aikawa08)]
- Simulation/model as data: NAUTILUS three-phase gas-grain chemical models (Model 1 toy collapse+warm-up; Model 2 Aikawa et al. 2008)  
  > "Two physical models are adopted for mimicking the emergence of a hot corino." (2.3 Physical models)

## Processing

### Calibration

- pipeline or manual: CASA pipeline for IRAS 16293 data  
  > "imaged with the highest possible spectral resolution using CASA pipeline analysis." (4.2 IRAS 16293)
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
- continuum subtraction: statcont algorithm for IRAS 16293B  
  > "we used the ‘statcont’ algorithm (cite: sanchez18) to get the continuum subtracted emission." (4.2 IRAS 16293)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- IRAS 4A2 ALMA data description, FWHM, systemic velocity  
  > "the ALMA observations carried out in (cite: sahu19) and (cite: su19) deployed seven spectral windows" (4.1 IRAS 4A2) [from (cite: sahu19); (cite: su19)]
- IRAS 16293 full data description  
  > "The whole data description can be found in (cite: jorgensen16)" (4.2 IRAS 16293) [from (cite: jorgensen16)]
- Reaction rate parameterization of NH2CO/HNCO/CH3NCO network  
  > "we parameterized the major reactions (Table [\[tab:network\]](#tab:network)) following (cite: gorai20) and references therein." (2.2) [from (cite: gorai20)]
- Dust opacity kappa=0.0182 cm2/g  
  > "Assuming, $\kappa_\nu$=0.0182 $\rm{cm^2g^{-1}}$ (cite: jorgensen16)" (4.1 IRAS 4A2) [from (cite: jorgensen16)]

### Not stated but needed to reproduce (our reading)

- Calibration details, CASA version and imaging parameters (robust, tclean settings) for both datasets
- Which ALMA project code corresponds to which source (2015.1.00147.S presumably IRAS 4A2, not stated)
- Exact spectrum extraction coordinates
- Line-free channels for statcont and CASSIS fitting procedure (fit by eye?)
- Source size assumed for IRAS 4A2 LTE modeling
- Final continuum-subtracted cube rms for IRAS 16293B

## Analysis recipe

1. **Model MC formation with gas-grain chemistry**: NAUTILUS 3-phase rate-equation model with added radical-radical reaction CH3O + NH2CO on grains, two physical warm-up models  
  > "The rate equation approximation is used in the code to estimate molecular abundances of species in the gas phase, dust surfaces and in the bulk of grain mantle (i.e., a three-phase model)." (2.1)
   - software: NAUTILUS, Gaussian 09
   - parameter: Model 1: 8 K, 2e4 cm-3, 1e6 yr prestellar, collapse to 1e8 cm-3 over ~2.1e5 yr, warm-up to 300 K; zeta = 1.3e-17 s-1; Av 10 to 150  
  > "A constant cosmic-ray ionization rate ($\zeta$) of $1.3 \times 10^{-17}$ s$^{-1}$ is assumed throughout the simulations." (2.3)
   - parameter: MC binding energy 10000 K (vs 7610 K test)  
  > "To check the effect of binding energies, we consider two values 10000 K and 7610 K" (2.4)
   - assumption: Radical-radical reaction assumed barrier-less; NH2CO and CH3O binding energies 5160 K and 4400 K  
  > "Additionally, we assume the radical-radical reaction to be barrier-less." (2.2); "The binding energies of $\mathrm{NH_2CO}$ and $\mathrm{CH_3O}$ are considered to be 5160 K and 4400 K, respectively" (2.2)
   - fitting: _not stated_
   - validation: Best-fit time chosen by comparing modeled COM abundances (CH3OH, NH2CHO, MC) to observed ones  
  > "We estimated the best fit time focussing more on $\mathrm{CH_3OH}$, MC and $\mathrm{NH_2CHO}$." (2.4)
2. **Extract spectra and identify MC lines**: Extract spectra from a beam-sized region (IRAS 4A2 at continuum peak; IRAS 16293B one-beam SW offset), subtract continuum (statcont for I16293B), compare with LTE synthetic spectra from JPL/CDMS  
  > "The spectra towards IRAS 4A2 are extracted from a region similar to beam size around the peak position of dust-continuum." (4.1 IRAS 4A2)
   - software: CASSIS, statcont
   - parameter: Vsys 6.9 km/s (IRAS 4A2), 3.1 km/s (I16293B); FWHM 2.0 and 1 km/s  
  > "we adopted a systematic velocity of $\sim$ 3.1 km s$^{-1}$ (cite: jorgensen11)" (4.2 IRAS 16293)
   - assumption: LTE with Tex = 100 K and 300 K because rotational temperature cannot be constrained  
  > "we assumed two typical temperatures, 100 K and 300 K, for estimating the upper limit of MC column densities." (Appendix B)
   - fitting: Column density adjusted until synthetic spectrum reproduces observed features (not a formal fit)  
  > "At this temperature, a column density $\sim 7\times 10^{15}$ cm$^{-2}$ could reproduce the observed spectral features." (4.1 IRAS 4A2)
   - validation: Features blended and only 2-3 sigma; only upper limits claimed  
  > "Considering these limitations, we only estimate the upper limit of MC from the observational data set." (4.1 IRAS 4A2)
3. **Compare model and observed abundances relative to other COMs**: Compare MC/CH3OH, CH3CHO, CH3OCH3, HNCO, CH3NCO, NH2CHO ratios in models and observations  
  > "We compare the observed fractional abundances of these COMs with MC in Figure [5](#fig:barplot)." (5)
   - assumption: COM species reside in the same volume  
  > "assuming these COM species reside in the same volume." (5)
   - fitting: _not stated_
   - validation: Agreement within an order of magnitude  
  > "We can see that the observed and model abundances of MC comparing to those COMs match well within an order of magnitude." (5)

## Software

- **NAUTILUS** : gas-grain chemical modeling  
  > "we use the NAUTILUS chemical code." (2.1)
- **CASSIS** : LTE synthetic spectra and line identification  
  > "we used CASSIS (developed by IRAP-UPS/CNRS- http://cassis.irap.omp.eu) software" (4.1 IRAS 4A2)
- **statcont** : continuum subtraction for IRAS 16293B  
  > "we used the ‘statcont’ algorithm (cite: sanchez18) to get the continuum subtracted emission." (4.2 IRAS 16293)
- **Gaussian 09** 09: B3LYP/6-311g++(d,p) reaction enthalpy  
  > "(B3LYP/6-311g++(d,p) method, Gaussian 09 software)" (2.2)
- **CASA** : pipeline imaging of IRAS 16293 archival data  
  > "imaged with the highest possible spectral resolution using CASA pipeline analysis." (4.2 IRAS 16293)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| MC column density upper limit IRAS 4A2, Tex=100 K | 2.5e15 | not stated | cm-2 | 2 | a column density of $2.5\times 10^{15}$ cm$^{-2}$, an excitation temperature of 100 K, and a source velocity of 6.9 km s$^{-1}$ could reproduce the observed spectra. |
| MC column density upper limit IRAS 4A2, Tex=300 K | ~7e15 | not stated | cm-2 | 2 | At this temperature, a column density $\sim 7\times 10^{15}$ cm$^{-2}$ could reproduce the observed spectral features. |
| MC column density IRAS 16293B, Tex=100 K and 300 K | 1.0e15 and 2.3e15 | not stated | cm-2 | 2 | the column densities of $1.0\times 10^{15}$ cm$^{-2}$ and $2.3\times 10^{15}$ cm$^{-2}$ best match with the observed spectral features |
| Modeled MC fractional abundance, Model 1 / Model 2 | 1.7e-10 / 0.9e-10 | not stated | dimensionless (wrt H2) | 1 | / $\mathrm{H_2NCO_2CH_3}$ / 1.7e-10 / 0.9e-10 / |
| Enthalpy of CH3O + NH2CO reaction | -80.79 | not stated | kcal/mol | 1 | The enthalpy of the reaction is found to be $-80.79$ Kcal/mol |
| Average H column density IRAS 4A2 | ~2.5e25 | not stated | cm-2 | 2 | the average (from extended and compact emission) hydrogen column density is $\sim 2.5 \times 10^{25}$ cm$^{-2}$. |
| CH3OH column density IRAS 4A2 | 1.12e19 | not stated | cm-2 | 2 | the resultant column density is $1.12\times 10^{19}$ cm$^{-2}$. |

## Qualitative findings

- MC forms on grains during warm-up and thermally desorbs above ~100 K; peak gas abundance depends on assumed binding energy  
  > "It is evident, based on Figure [1](#fig:models), that MC forms during the warm up phase and thermally desorbs into the gas phase." (2.4)
- MC features are weak and blended; no detection claimed, only upper limits  
  > "the emission features presented in this paper are not sufficient yet for claiming a tentative detection of MC" (4.2 IRAS 16293)

## Claim tuples

- H: Radical-radical reaction CH3O + NH2CO on grains can produce MC in hot corinos | E: NAUTILUS modeling with two physical models | R: Gas-phase MC abundance ~1e-10 after warm-up | F: MC production is favored in hot-corino environments (>~110 K) | **supported**
- H: MC is present toward IRAS 4A2 and IRAS 16293B | E: LTE comparison of ALMA archival spectra near 350 GHz | R: Column density upper limits ~1e15-7e15 cm-2 | F: Model abundance consistent with observed upper limits | **partially**

## Reasoning

- Why this data: IRAS 16293B chosen because narrow lines reduce line confusion; IRAS 4A2 spectra show similar emission in the same range  
  > "I16293B therefore is an ideal target to search for MC." (4.2 IRAS 16293)
- Why this method: _not stated_
- Alternative: Reaction CH3OCO + NH2 not included because CH3OCO formation is not well known  
  > "we did not include this reaction in our network as the formation of $\mathrm{CH_3OCO}$ radical is not well known." (2.2)
- How they decided it was enough: _not stated_
- Limitation (authors): MC lines are partially or fully blended; Tex cannot be constrained; only limited transitions  
  > "there are only a limited number of transitions with their features being weak and blended." (4.2 IRAS 16293)
- Caveat (inferred, ours): Upper limits rest on by-eye LTE matching without formal fit or uncertainty
- Caveat (inferred, ours): Model validated by only a few COMs and a chosen best-fit time; no sensitivity to many parameters
- Caveat (inferred, ours): Only one reaction pathway; barrier-less assumption untested
- Caveat (inferred, ours): Source-size and beam-dilution assumptions for IRAS 4A2 uncertain

## Reproducibility

- Data public (paper): Data taken from ALMA archive  
  > "The data towards the source were taken from ALMA archive" (4.2 IRAS 16293)
- Products in archive: _not stated_
- Missing: Reduced cubes / calibration scripts
- Missing: Exact spectrum extraction positions and CASSIS settings
- Missing: NAUTILUS network files (only partially tabulated)
- Data volume (inferred): ~50-200 GB raw for two ALMA projects
- Score (inferred): 3/5, Public data and tabulated network, but spectral analysis by-eye with missing processing details.
- Rediscovery candidate: no, Results are upper limits from by-eye LTE matching and a custom chemical network; recipe incomplete.

## Links

- Method: Ruaud et al. 2016 (cite: ruaud16) (NAUTILUS formalism)
- Method: Sánchez-Monge et al. 2018 (cite: sanchez18) (STATCONT continuum determination)
- Companion: Sahu et al. 2019 (cite: sahu19) (IRAS 4A2 ALMA data and line forest)
- Companion: Jørgensen et al. 2016 (cite: jorgensen16) (IRAS 16293B ALMA data (PILS))
- Related: PILS

## Checks

```json
{
 "quotes": 60,
 "quotes_ok": 60,
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
  "stated": 43,
  "rate": 0.544
 },
 "evidence_ok": true
}
```
