# PdBI U/LIRG Survey (PULS): Dense molecular gas in Arp 220 and NGC 6240

`2017A&A...604A...2S` | Astronomy and Astrophysics 2017 | first author: Sliwa, Kazimierz | arXiv: 1704.03766 | DOI: 10.1051/0004-6361/201630139

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, astrochemistry
- Question: What are the molecular gas physical conditions and CO isotopologue abundance ratios in Arp 220 and NGC 6240, and how do dense-gas line ratios differ?  
  > "Various lines are used to analyse the physical conditions of the molecular gas including the \[$^{12}$CO\]/\[$^{13}$CO\] and \[$^{12}$CO\]/\[C$^{18}$O\] abundance ratios." (abstract)
- Target **Arp 220**: coordinates 15 34 57.24 +23 30 11.2 (J2000)  
  > "| Arp 220  | 15 34 57.24 | +23 30 11.2 | 1.4 $\times$ 10$^{12}$     | 5434          | 0.018126  | 81.3    | 390                |" (Table 1); z/distance z=0.018126, D_L=81.3 Mpc  
  > "| Arp 220  | 15 34 57.24 | +23 30 11.2 | 1.4 $\times$ 10$^{12}$     | 5434          | 0.018126  | 81.3    | 390                |" (Table 1); distance from 9-year WMAP parameters (Hinshaw2012)  
  > "| Arp 220  | 15 34 57.24 | +23 30 11.2 | 1.4 $\times$ 10$^{12}$     | 5434          | 0.018126  | 81.3    | 390                |" (Table 1)
- Target **NGC 6240**: coordinates 16 52 58.89 +02 24 03.7 (J2000)  
  > "| NGC 6240 | 16 52 58.89 | +02 24 03.7 | 5.4 $\times$ 10$^{11}$     | 7340          | 0.02448   | 108     | 520                |" (Table 1); z/distance z=0.02448, D_L=108 Mpc  
  > "| NGC 6240 | 16 52 58.89 | +02 24 03.7 | 5.4 $\times$ 10$^{11}$     | 7340          | 0.02448   | 108     | 520                |" (Table 1); distance from 9-year WMAP parameters (Hinshaw2012)  
  > "| NGC 6240 | 16 52 58.89 | +02 24 03.7 | 5.4 $\times$ 10$^{11}$     | 7340          | 0.02448   | 108     | 520                |" (Table 1)

## Data provenance

- ALMA projects: 2011.0.00018.SV
- bands: Band 5 (ALMA SV); PdBI 3 mm and 1.4 mm  
  > "Arp 220 was a target for Band 5 SV observations on 16 July 2016." (2.2 ALMA)
- frequencies and spectral setup: ALMA: four spws of 1.875 GHz each on H2O, HNC 2-1, CS 4-3, CH3OH  
  > "The four spectral windows, of 1.875GHz bandwidth each, were placed on H$_{2}$O (3$_{13}$ - 2$_{20}$), HNC $J$=2-1, CS $J$=4-3 and CH$_{3}$OH (4$_{31}$ - 3$_{30}$)." (2.2 ALMA)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: PdBI spacings 24 m to 400 m (up to 760 m in extended configuration)  
  > "the six 15 m antennas were arranged with spacings from 24 m to 400 m." (2.1 PdBI)
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: ALMA SV: 16 July 2016  
  > "Arp 220 was a target for Band 5 SV observations on 16 July 2016." (2.2 ALMA)
- pi or archival as stated: _not stated_
- Line: CS J=4-3 (195.954 GHz)
- Line: CH3CN 10-9 (183.674 - 183.964 GHz)
- Other facility **IRAM PdBI**: Main new line data (13CO, HCN, HCO+, CS, etc.) for Arp 220 and NGC 6240  
  > "We present new IRAM Plateau de Bure Interferometer observations of Arp 220 in HCN, HCO$^{+}$, HN$^{13}$C $J$=1–0" (abstract)
- Other facility **SMA**: 12CO J=3-2 of Arp 220 (Sakamoto2008)  
  > "We also use the SMA observations of $^{12}$CO $J$=3$-$2 in Arp 220 published in (cite: Sakamoto2008)" (2.1 PdBI)
- External data: 12CO J=1-0 and 2-1 of Arp 220 used in RADEX modelling  
  > "The $^{12}$CO lines modelled are the $J$=1-0, 2-1 (cite: Downes1998) and 3-2 (cite: Sakamoto2008)." (4 Radiative Transfer Analysis) [from (cite: Downes1998)]
- External data: 13CO/C18O = 1 to estimate C18O emission  
  > "We use a line ratio of $^{13}$CO/C$^{18}$O = 1 (cite: Matsushita2009; Greve2009) to estimate the emission of C$^{18}$O" (4 Radiative Transfer Analysis) [from (cite: Matsushita2009; Greve2009)]
- External data: Linewidths 120 and 250 km/s for Arp 220W and E from ALMA 12CO 1-0  
  > "We adopt the following linewidths: 120 km s$^{-1}$ and 250 km s$^{-1}$ for Arp 220W and Arp 220E measured using ALMA $^{12}$CO $J$=1$-$0 observations at 0.09$''$" (4 Radiative Transfer Analysis) [from (cite: Scoville2017)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA v4.7.1  
  > "Using `CASA` v4.7.1, we create datacubes of 20 km s$^{-1}$ channel widths" (2.2 ALMA)
- pipeline version: _not stated_
- archive products used as is: Delivered once phase-only self-calibrated ALMA SV visibilities used  
  > "After checking for any obvious calibration flaws, we use the once phase-only self-calibrated delivered visibility dataset." (2.2 ALMA)
- flux calibrator: PdBI: 3C273 and MWC349  
  > "The primary amplitude calibrators were 3C273" (2.1 PdBI)
- flux scale uncertainty: PdBI ±5% at 3 mm, ±10% at 1.4 mm  
  > "The uncertainties in the flux scales are typically $\pm 5$% at 3 mm and $\pm 10$% at 1.4 mm." (2.1 PdBI)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "we create datacubes of 20 km s$^{-1}$ channel widths with a natural weighting for maximum sensitivity." (2.2 ALMA)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: 2σ cutoff for ALMA integrated intensity maps  
  > "We created integrated intensity maps using a 2$\sigma$ cutoff" (2.2 ALMA)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Gaussian kernel smoothing to common resolution; Arp 220 to 13CO 1-0 beam, NGC 6240 to 1.2"  
  > "we smooth the data cubes using a Gaussian kernel to match angular resolution." (3 Line Ratios)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- RADEX+MultiNest MCMC code and details of priors  
  > "We refer the reader to Kamenetzky et al. (2014) for more details." (4 Radiative Transfer Analysis) [from (cite: Kamenetzky2014)]

### Not stated but needed to reproduce (our reading)

- CASA imaging parameters for ALMA SV cubes (cell, image size, continuum subtraction, line-free channels)
- MCMC prior bounds on Tkin, nH2, N/dV; number of live points
- Which delivered ALMA calibration products/scripts version
- Data release location of PdBI products not given as a specific link

## Analysis recipe

1. **Image ALMA SV CS 4-3 and CH3CN 10-9**: Datacubes of 20 km/s channels, natural weighting, integrated intensity maps with 2σ cutoff  
  > "Using `CASA` v4.7.1, we create datacubes of 20 km s$^{-1}$ channel widths with a natural weighting for maximum sensitivity." (2.2 ALMA)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared total CS 4-3 flux with APEX single dish  
  > "The ALMA SV CS $J$ = 4$-$3 observations total flux agrees with the single dish observations." (5.1 Molecules Detected)
2. **Brightness temperature line ratio maps**: Smooth cubes to common beam, 5σ cut, ratio maps of integrated Tb  
  > "We applied a 5$\sigma$ cut to each map used to produce the the ratio maps." (3 Line Ratios)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Radiative transfer modelling of 12CO, 13CO, C18O**: RADEX models with MultiNest nested sampling likelihood, filling factor, three priors  
  > "This code implements the nested sampling algorithm MultiNest (cite: Feroz2009) using its Python wrapper PyMultiNest (cite: Buchner2014) to constrain parameters." (4 Radiative Transfer Analysis)
   - software: RADEX, MultiNest, PyMultiNest
   - parameter: Free: Tkin, N/dV, nH2, filling factor ≤1; optical depth prior 0-100  
  > "An optical depth range of 0 to 100." (4 Radiative Transfer Analysis)
   - assumption: [12CO]/[H2] = 3e-4; 13CO/C18O = 1; diameter ~700 pc  
  > "Molecular Gas (H$_{2}$) mass assuming \[$^{12}$CO\]/\[H$_{2}$\] = 3 $\times$ 10$^{-4}$" (Table 4 notes)
   - fitting: Nested sampling (MultiNest) with column length, dynamical mass and optical depth priors  
  > "We also implement three priors:" (4 Radiative Transfer Analysis)
   - validation: Arp 220W fit excluded 3-2 line because it gave poor SLED fits  
  > "the addition of the $J$=3-2 line resulted in poor SLED fits" (4 Radiative Transfer Analysis)

## Software

- **CASA** v4.7.1: Analysis of PdBI FITS cubes and imaging of ALMA SV data  
  > "imported into `CASA` (cite: McMullin2007) v4.7.1 for data analysis." (2.1 PdBI)
- **GILDAS/MAPPING** : PdBI data reduction  
  > "All data reductions were done with the MAPPING program in the standard IRAM GILDAS[^2] package." (2.1 PdBI)
- **RADEX** : Escape-probability radiative transfer  
  > "we use the escape-probability radiative transfer program RADEX (cite: vanderTak2007)." (4 Radiative Transfer Analysis)
- **MultiNest/PyMultiNest** : Nested sampling of parameters  
  > "This code implements the nested sampling algorithm MultiNest (cite: Feroz2009) using its Python wrapper PyMultiNest (cite: Buchner2014)" (4 Radiative Transfer Analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Best-fit Tkin Arp 220C | 38 | -1σ 37, +1σ 690 | K | 3 | /  / Best Fit / 38 / 3.35 / 4.9 / -0.036 / 19.20 / 8.69 / 0.3 / 90 / 91 / |
| Best-fit log10 nH2 Arp 220C | 3.35 | -1σ 2.55, +1σ 3.40 | log cm^-3 | 3 | /  / Best Fit / 38 / 3.35 / 4.9 / -0.036 / 19.20 / 8.69 / 0.3 / 90 / 91 / |
| Best-fit [12CO]/[13CO] Arp 220C | 90 | -1σ 58, +1σ 309 | dimensionless | 3 | /  / Best Fit / 38 / 3.35 / 4.9 / -0.036 / 19.20 / 8.69 / 0.3 / 90 / 91 / |
| HCN/HCO+ 1-0 ratio Arp 220E | 2.4 | 0.2 | dimensionless | 2 | / Arp 220E / 15 34 57.342 / +23 30 11.610 / 0.8 $\pm$ 0.1 / 0.8 $\pm$ 0.1   / 23 $\pm$ 3    / 19 $\pm$ 2    / 0.9 $\pm$ 0.1        / 2.4 $\pm$ 0.2   / |
| HCN/HCO+ 1-0 ratio NGC 6240 | 0.80 | 0.09 | dimensionless | 2 | / NGC 6240 / 16 52 58.900 / +02 24 03.810 / 1.0 $\pm$ 0.1 / ...             / ...           / ...           / ...                  / 0.80 $\pm$ 0.09 / |
| CS 4-3 flux Arp 220 (ALMA SV) | 61.0 | not stated | Jy km/s | 1 | /  / CS $J$ = 4$-$3  / 195.954 / 0.9 x 0.7 / 1.4 / 20 / 61.0 / |

## Qualitative findings

- 13CO ratios show east-west gradient across Arp 220 while 12CO ratios vary smoothly  
  > "the line ratios of optically thin lines such as $^{13}$CO show a east-west gradient across Arp 220." (abstract)

## Claim tuples

- H: Molecular gas on ~700 pc scale in Arp 220 conditions | E: RADEX + MultiNest fit of 12CO, 13CO, C18O | R: Best fit Tkin 38 K, nH2 10^3.35 | F: Warm, moderately dense gas averaged over the nuclei | **supported**
- H: Are CO isotopologue abundances enhanced by nucleosynthesis | E: Free abundance ratios in the fit | R: Ratios ~90 for both | F: C18O enhancement explained by stellar nucleosynthesis | **partially**
- H: HCN/HCO+ differs between the two mergers | E: Ratio maps | R: Arp 220 >2, NGC 6240 <1 | F: Significantly different ratios | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Optical depth, selective photodissociation and fractionation ruled out as cause of high 12CO/13CO  
  > "Optical depth effects have been ruled out by our analysis as the best fit solutions have optical depths $>$ 1 for $^{12}$CO and $<<$1 for $^{13}$CO." (5.3 Abundance Ratios)
- How they decided it was enough: _not stated_
- Limitation (authors): Resolution too poor to separate the two nuclei  
  > "Our resolution is too poor to distinguish the nuclei spatially" (Table 3 notes)
- Caveat (inferred, ours): Single-component fit with poorly constrained C18O derived from assumed 13CO/C18O=1
- Caveat (inferred, ours): Mixed-resolution data and missing flux affect ratios
- Caveat (inferred, ours): Best-fit and mean values differ widely, broad posteriors

## Reproducibility

- Data public (paper): PdBI data to be released via IRAM Large Program Archive and NED; ALMA SV public  
  > "The PdBI data presented in this paper will be released via the **IRAM Large Program Archive** and NASA’s Extragalactic Database" (Release of Data)
- Products in archive: _not stated_
- Code: MCMC code of Kamenetzky available on github (pyradexnest)  
  > "https://github.com/jrka/pyradexnest" (footnote)
- Missing: PdBI project codes and raw data
- Missing: MCMC prior ranges and sampler settings
- Missing: CASA imaging details
- Data volume (inferred): ~tens of GB for ALMA SV; PdBI data separate
- Score (inferred): 3/5, ALMA part is small; modelling uses public code but literature inputs and settings partly unspecified.
- Rediscovery candidate: no, Main results rely mostly on PdBI data and literature inputs; ALMA role minor.

## Links

- Method: (cite: Kamenetzky2014) (RADEX MCMC code and priors)
- Companion: (cite: Sliwa2017a) (Similar analysis of NGC 2623)
- Related: PdBI U/LIRG Survey (PULS)

## Checks

```json
{
 "quotes": 54,
 "quotes_ok": 54,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.0.00018.SV"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 41,
  "rate": 0.577
 },
 "evidence_ok": true
}
```
