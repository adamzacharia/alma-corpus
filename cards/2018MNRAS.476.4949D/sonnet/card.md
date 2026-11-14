# The ALMA-PILS survey: the sulphur connection between protostars and comets: IRAS 16293-2422 B and 67P/Churyumov-Gerasimenko

`2018MNRAS.476.4949D` | Monthly Notices of the Royal Astronomical Society 2018 | first author: Drozdovskaya, Maria N. | arXiv: 1802.02977 | DOI: 10.1093/mnras/sty462

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: astrochemistry, star_formation
- Question: What is the sulphur-bearing molecule inventory at ~60 au from IRAS 16293-2422 B, and how do its molecular ratios compare with those of comet 67P/C-G measured by ROSINA?  
  > "ALMA Band $7$ data from the large unbiased Protostellar Interferometric Line Survey (PILS) are used to search for S-bearing molecules in the outer disc-like structure, $\sim 60$ au from IRAS 16293–2422 B" (abstract)
- Target **IRAS 16293-2422 B**: coordinates _not stated_; z/distance 120-147 pc  
  > "IRAS 16293–2422 is an embedded low-mass Class $0$ protostellar binary with a separation of $5\ensuremath{''}{1}$ (or $610-750$ au assuming a distance of $120-147$ pc;" (1 Introduction); distance from Loinard2008; OrtizLeon2017  
  > "IRAS 16293–2422 is an embedded low-mass Class $0$ protostellar binary with a separation of $5\ensuremath{''}{1}$ (or $610-750$ au assuming a distance of $120-147$ pc;" (1 Introduction)

## Data provenance

- ALMA projects: 2013.1.00278.S
- bands: Band 7, 329-363 GHz  
  > "carried out with ALMA in the $329-363$ GHz frequency range (Band $7$)" (2 IRAS 16293–2422 observations)
- frequencies and spectral setup: spectral resolution 0.2 km/s (0.244 MHz)  
  > "with a spectral resolution of $0.2$ km s$^{-1}$" (2 IRAS 16293–2422 observations)
- continuum bandwidth: _not stated_
- arrays: 12-m and 7-m (ACA) combined  
  > "The observations are a combination of the $12$- and the $7$-m dish arrays" (2 IRAS 16293–2422 observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.5 arcsec circular restoring beam (60-74 au)  
  > "Here, the dataset convolved with a uniform circular restoring beam of $0\ensuremath{''}{5}$ is used." (2 IRAS 16293–2422 observations)
- max recoverable scale: ~13 arcsec  
  > "ensuring that the emission on scales up to $\sim13\ensuremath{''}$ is recovered" (2 IRAS 16293–2422 observations)
- sensitivity: sigma = 10 mJy/beam/channel or 5 mJy/beam km/s adopted  
  > "Hereafter, $\sigma=10$ mJy beam$^{-1}$ channel$^{-1}$ or $5$ mJy beam$^{-1}$ km s$^{-1}$ is adopted." (2 IRAS 16293–2422 observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **Rosetta/ROSINA**: 67P/C-G coma molecular ratios for comparison  
  > "Subsequently, ratios between various molecules are compared to those deduced for the coma gases of 67P/C–G, as measured with the ROSINA instrument" (1 Introduction)
- External data: 67P/C-G ROSINA molecular abundances and ratios  
  > "The cometary values correspond to bulk coma quantities measured with DFMS/ROSINA" (4.3 Comparison with 67P/C-G) [from Calmonte2016]
- External data: Single dish abundances of S-bearing species  
  > "as compiled from previous single dish observations of (cite: Schoier2002)" (4.1 Comparison with single dish observations) [from Schoier2002]
- External data: HDS/H2S D/H = 0.05  
  > "Assuming D/H $=0.05$, as measured with single dish observations of HDS/H$_{2}$S (table $11$ of (cite: vanDishoeck1995))" (3.4 H2S) [from vanDishoeck1995]

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
- continuum subtraction: statistical method from Jorgensen2016  
  > "The data used here are continuum subtracted based on the statistical method described in (cite: Jorgensen2016)." (2 IRAS 16293–2422 observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Calibration and PILS survey details  
  > "All further details on the PILS survey, including calibration, are available in (cite: Jorgensen2016)." (2 IRAS 16293–2422 observations) [from Jorgensen2016]
- Local ISM isotopic ratios  
  > "Isotopic ratios for the local ISM have been taken from (cite: Wilson1999)" (3 Results and analysis) [from Wilson1999]

### Not stated but needed to reproduce (our reading)

- Exact line lists and partition functions/CDMS-JPL entries per molecule for all lines
- Column density table values and the fitted spectra in machine-readable form
- Exact pixel coordinates of the one-beam offset position
- Imaging/calibration parameters (in Jorgensen2016)

## Analysis recipe

1. **line search and LTE modelling**: Line search and LTE modelling at one-beam SW offset of source B, then synthetic spectra  
  > "The initial line searching and local thermal equilibrium (LTE) modelling have been carried out with CASSIS" (3 Results and analysis)
   - software: CASSIS, IDL
   - parameter: Tex = 125 K, FWHM 1 km/s, source size 0.5 arcsec (beam dilution 0.5)  
  > "assuming a constant $T_{\text{ex}}=125$ K for all species" (3 Results and analysis)
   - assumption: LTE; local ISM 32S/34S = 22; solar 32S/33S=125, 32S/36S=4747  
  > "($^{32}$S/$^{34}$S $=22$)" (3 Results and analysis)
   - fitting: Best fit by eye on a grid of synthetic spectra, 25 K Tex steps  
  > "determined as best-fitting by eye based on a grid of synthetic spectra with $25$ K steps" (3 Results and analysis)
   - validation: LTE checked via non-LTE for methanol in Jorgensen2016  
  > "This assumption has also been quantified for the case of methanol (CH$_{3}$OH) in section $5.1$ of (cite: Jorgensen2016)." (3 Results and analysis)
2. **derive main-species column densities and ratios, compare with 67P**: Scale rare-isotopologue columns with isotopic ratios, form ratios to H2S and OCS, compare with ROSINA  
  > "contains the molecular ratios relative to H$_{2}$S and OCS for IRAS 16293–2422 B in comparison to those of 67P/C–G." (Discussion, Comparison with 67P/C-G and ISM ices)
   - assumption: H2S from HDS with D/H = 0.05 (alt. 0.005)  
  > "To account for this other extreme for the case of H$_{2}$S, a D/H $=0.005$ may be assumed" (3.4 H2S)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASSIS** : line searching and LTE modelling  
  > "The initial line searching and local thermal equilibrium (LTE) modelling have been carried out with CASSIS" (3 Results and analysis)
- **IDL** : custom routines for synthetic spectra  
  > "synthetic spectra have been generated with custom IDL routines" (3 Results and analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| SO2 column density | 1.5e15 | not stated | cm-2 | 1 | at a column density of $1.5\times10^{15}$ cm$^{-2}$ |
| OCS column density (best estimate from three isotopologues) | 2.8e17 | 0.7e17 | cm-2 | 1 | $\left( 2.8\pm0.7 \right)\times10^{17}$ cm$^{-2}$ and is the best estimate of the column density of OCS |
| H2S column density (D/H=0.05) | 1.9e17 | 0.3e17 | cm-2 | 1 | $\left( 1.9\pm0.3 \right)\times10^{17}$ cm$^{-2}$ is the best estimate of the column density of H$_{2}$S |
| CH3SH column density | 5.5e15 | not stated | cm-2 | 1 | at a column density of $5.5\times10^{15}$ cm$^{-2}$ |
| 32S/33S in IRAS 16293 B | 93 | 11 | dimensionless | 1 | $^{32}$S/$^{33}$S$ for IRAS 16293–2422 B to be $93\pm11$ |
| SO/SO2 ratio | 0.33 | not stated | dimensionless | 2 | it is $0.33$ for IRAS 16293–2422 B |
| HDCS/H2CS | 0.1 | 0.014 | dimensionless | 1 | HDCS/H$_{2}$CS ratio to be $0.1\pm0.014$ |

## Qualitative findings

- IRAS 16293 B has much more OCS relative to H2S than 67P/C-G; SO/SO2 agrees  
  > "the SO/SO$_{2}$ ratio is in close agreement between the two targets" (abstract)

## Claim tuples

- H: Do S-bearing ratios in IRAS 16293 B match 67P/C-G? | E: LTE fits of PILS Band 7 at one-beam offset, compared with ROSINA ratios | R: OCS/H2S factor 3~33 higher; SO and SO2 lower relative to H2S; SO/SO2 0.33 vs 0.4-0.7 | F: Differences possibly from UV levels and birth-cloud temperature | **partially**

## Reasoning

- Why this data: Source B lines are narrower, giving less blending, ideal for isotopologues  
  > "The choice to focus on source B has been made, because its lines are much narrower than those observed towards source A" (1 Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): H2S column uncertain by an order of magnitude due to unknown HDS/H2S  
  > "the unknown HDS/H$_{2}$S ratio leaves the column density of H$_{2}$S uncertain by at least an order of magnitude" (5 Conclusions)
- Caveat (inferred, ours): Single position, by-eye fits, no formal uncertainties
- Caveat (inferred, ours): Fixed Tex=125 K for all species
- Caveat (inferred, ours): UV explanation is speculative

## Reproducibility

- Data public (paper): PILS project 2013.1.00278.S; ALMA data acknowledged  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00278.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Reduced PILS cubes (Jorgensen2016)
- Missing: IDL routines not released
- Data volume (inferred): ~50-100 GB (PILS cubes)
- Score (inferred): 3/5, Public data and clear LTE recipe, but by-eye fits, custom IDL and processing deferred to Jorgensen2016.
- Rediscovery candidate: no, Fits by eye with custom code and reliance on pre-processed PILS products.

## Links

- Method: Jorgensen2016 (PILS survey description, calibration, continuum subtraction)
- Companion: Coutens2016, Lykke2017, Ligterink2017 (same offset position studied for other species)
- Related: PILS

## Checks

```json
{
 "quotes": 39,
 "quotes_ok": 39,
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
  "facts": 62,
  "stated": 29,
  "rate": 0.468
 },
 "evidence_ok": true
}
```
