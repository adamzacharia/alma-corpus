# Ingredients for solar-like systems: protostar IRAS 16293-2422 B versus comet 67P/Churyumov-Gerasimenko

`2019MNRAS.490...50D` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Drozdovskaya, Maria N. | arXiv: 1908.11290 | DOI: 10.1093/mnras/stz2430

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: astrochemistry, star_formation
- Question: Do relative abundances of volatiles in protostar IRAS 16293-2422 B correlate with bulk abundances in comet 67P/C-G, i.e. are cometary ingredients inherited from protostellar phases?  
  > "The goal of this paper is to compare the chemical inventories of these two targets and thereby test the chemical links that may or may not exist between cometary and interstellar volatiles." (Introduction)
- Target **IRAS 16293-2422 B**: coordinates _not stated_; z/distance 141 pc  
  > "It is composed of two deeply embedded protostars, A and B, at a short distance of $141$ pc (cite: Dzib2018)" (Introduction); distance from Dzib et al. 2018  
  > "It is composed of two deeply embedded protostars, A and B, at a short distance of $141$ pc (cite: Dzib2018)" (Introduction)
- Target **comet 67P/Churyumov-Gerasimenko**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00278.S, 2012.1.00712.S, 2016.1.01150.S, 2011.0.00007.SV, 2017.1.00518.S, 2015.1.01193.S
- bands: PILS Band 7 (329-363 GHz); supplementary Bands 3 and 6  
  > "carried out with ALMA in the $329-363$ GHz frequency range (Band $7$) during Cycle 2 observations, supplemented with ALMA observations in Bands $3$ ($\sim100$ GHz) and $6$ ($\sim230$ GHz)" (2.2 IRAS 16293-2422)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12 m main array combined with ACA 7 m  
  > "The data from the main array of $12$ m dishes are combined with data from the Atacama Compact Array (ACA) of $7$ m dishes" (2.2 IRAS 16293-2422)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: uniform circular beam of 0.5 arcsec (~70 au)  
  > "PILS was carried out at a spectral resolution of $0.2$ km s$^{-1}$ ($0.244$ MHz) and restored with a uniform circular beam of $0\ensuremath{''}{5}$." (2.2 IRAS 16293-2422)
- max recoverable scale: 13 arcsec (12m + ACA)  
  > "hence, resulting in the largest recoverable size of $13\ensuremath{''}$" (2.2 IRAS 16293-2422)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **Rosetta/ROSINA**: in situ bulk coma abundances of 67P/C-G (May 22-June 2, 2015 average)  
  > "Here, the averages of the measurements obtained between the 22nd of May and the 2nd of June, 2015 are used as bulk abundances." (2.1 67P/C-G)
- External data: Bulk cometary abundances from ROSINA  
  > "The majority of cometary data points represent bulk abundances as derived from ROSINA measurements, as explained in Section [2.1](#67P) and published in (cite: Rubin2019a)." (3.1 Correlations) [from (cite: Rubin2019a)]
- External data: Protostellar column densities from the PILS series of papers (10-20 per cent accuracy)  
  > "stem from the series of papers from the PILS team at a relative accuracy of $10-20$ per cent" (3.1 Correlations) [from (cite: Jorgensen2016; Jorgensen2018; Drozdovskaya2018)]

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

- PILS data reduction, imaging and column density derivation  
  > "carried out with ALMA in the $329-363$ GHz frequency range (Band $7$) during Cycle 2 observations" (2.2 IRAS 16293-2422) [from (cite: Jorgensen2016)]

### Not stated but needed to reproduce (our reading)

- Calibration and imaging details for PILS and the other ALMA datasets
- Exact abundance tables (Tables not included in text) and ROSINA values
- Details of the correlation statistics code and error propagation
- Line-free channels, Tex choices per molecule for new column densities

## Analysis recipe

1. **Derive new column densities at one-beam offset from B**: LTE synthetic spectra compared to observed spectra for molecules lacking published values (CO, HCN, HNC, PN, PO, glycine)  
  > "The synthetic spectra have been generated with custom IDL routines under the assumption of local thermal equilibrium (LTE)" (Appendix)
   - software: custom IDL routines, CDMS
   - parameter: Tex = 125 K and 300 K for glycine; 125 K for PN  
  > "estimate upper limits on the column density of glycine for excitation temperatures of $125$ and $300$ K" (Appendix Glycine)
   - fitting: _not stated_
   - validation: _not stated_
2. **Compute relative abundances per chemical family**: Ratios to reference species (CH3OH, CH3CN, CH3SH); isomers summed to match ROSINA masses  
  > "the observed protostellar abundances have been summed to make an appropriate comparison with cometary measurements" (3.1 Correlations)
   - fitting: _not stated_
   - validation: _not stated_
3. **Correlate protostellar and cometary abundances**: Pearson and Spearman correlation coefficients, linear and logarithmic scaling  
  > "the correlation coefficients have also been computed with logarithmic scaling" (3.1 Correlations)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **custom IDL routines** : LTE synthetic spectra  
  > "The synthetic spectra have been generated with custom IDL routines under the assumption of local thermal equilibrium (LTE)" (Appendix)
- **CDMS** : spectroscopic data  
  > "The spectroscopic data stem from the Cologne Database of Molecular Spectroscopy (CDMS" (Appendix)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CHO-family Spearman coefficient | 0.88 | two-tailed significance 8.1e-5 | dimensionless | 3 | Pearson correlation coefficient of $1.00$ and a Spearman’s correlation coefficient of $0.88$ (at a two-tailed significance of $8.1\times10^{-5}$ |
| N-family Spearman coefficient | 0.93 | significance 2.5e-3 | dimensionless | 3 | Pearson correlation coefficient of $0.98$ and a Spearman’s correlation coefficient of $0.93$ (at a two-tailed significance of $2.5\times10^{-3}$ |
| S-family Spearman coefficient | 0.32 | significance 0.35 | dimensionless | 3 | Pearson correlation coefficient of $0.50$ and a Spearman’s correlation coefficient of $0.32$ (at a two-tailed significance of $0.35$ |
| P- and Cl-family Spearman coefficient | 0.40 | significance 0.6 | dimensionless | 3 | Pearson correlation coefficient of $0.71$ and a Spearman’s correlation coefficient of $0.40$ (at a two-tailed significance of $0.6$ |
| N(PN) at one-beam offset from B | 2.1e13 | not stated | cm^-2 | 1 | yields $N(\text{PN})=2.1\times10^{13}$ cm$^{-2}$ at the one-beam ($\sim70$ au) offset from source B |
| N(PO) upper limit | 4.4e14 | not stated | cm^-2 | 1 | only an upper limit is derived for the PO column density of $4.4\times10^{14}$ cm$^{-2}$ |

## Qualitative findings

- Cometary relative abundances tend to be higher than protostellar ones for CHO- and N-bearing species  
  > "the relative abundance ratios of 67P/C–G tend to be higher than those of IRAS 16293-2422 for CHO- and N-bearing species" (4.1)

## Claim tuples

- H: Cometary bulk volatiles correlate with protostellar disc-scale volatiles | E: Compare PILS abundances at B with ROSINA bulk abundances per chemical family | R: Pearson 0.50-1.0, Spearman 0.32-0.93 across families | F: Volatile composition of comets is partially inherited from protostellar phases | **supported**
- H: P- and Cl-bearing species also correlate | E: Abundances relative to CH3OH | R: Pearson 0.71, Spearman 0.40, significance 0.6 | F: Only a tentative correlation | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Many points are upper limits or estimates; isomers unresolved by ROSINA; symmetric molecules invisible to ALMA  
  > "it is not possible to determine the abundance of symmetric molecules such as N$_{2}$, CH$_{4}$, CS$_{2}$, and CO$_{2}$" (3.2.1)
- Caveat (inferred, ours): Correlation significance in S and P/Cl families is low
- Caveat (inferred, ours): Pearson on linear scale dominated by few abundant species
- Caveat (inferred, ours): Single comet and single protostar compared
- Caveat (inferred, ours): Upper limits included in correlation

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Abundance tables values not in text
- Missing: PILS calibration and imaging recipe
- Missing: ROSINA abundances from Rubin et al. 2019
- Data volume (inferred): Tens to hundreds of GB for PILS; the paper mostly uses published values
- Score (inferred): 3/5, Mostly literature values; new ALMA analysis limited to a few column densities with sparse details.
- Rediscovery candidate: no, Main results rely on tabulated literature abundances and ROSINA data, with incomplete recipe.

## Links

- Method: (cite: Jorgensen2016) (PILS survey description and data reduction)
- Companion: (cite: Rubin2019a) (ROSINA bulk abundances of 67P/C-G)
- Related: PILS
- Related: Rosetta/ROSINA

## Checks

```json
{
 "quotes": 34,
 "quotes_ok": 34,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 6,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2013.1.00018.S",
  "2013.1.00061.S",
  "2016.1.00457.S",
  "2016.1.01468.S",
  "2017.1.01247.S"
 ],
 "codes_printed_but_missing": [
  "2013.1.00061.S"
 ],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 64,
  "stated": 19,
  "rate": 0.297
 },
 "evidence_ok": true
}
```
