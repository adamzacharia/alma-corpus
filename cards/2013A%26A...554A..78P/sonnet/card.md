# Acetone in Orion BN/KL. High-resolution maps of a special oxygen-bearing molecule

`2013A&A...554A..78P` | Astronomy and Astrophysics 2013 | first author: Peng, T.-C. | arXiv: 1304.4793 | DOI: 10.1051/0004-6361/201220891

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation, astrochemistry
- Question: What is the distribution, excitation temperature and abundance of acetone in Orion BN/KL, and how does it compare with N- and O-bearing molecules?  
  > "Therefore, it is worth investigating acetone in detail at high angular resolutions." (abstract)
- Target **Orion BN/KL**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00009.SV
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: ALMA-SV: 16 12-m antennas (table lists 12 antennas); main data from IRAM PdBI  
  > "The observations were carried out in 2012 January with 16 12-m antennas (cite: Zapata2012; Niederhofer2012)." (Basic observational parameters)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ALMA-SV synthesized beam 1.92x1.39 arcsec, PA 166  
  > "| ALMA-SV | 12             | $\sim100$              | 9.2 K              | 9.6               | 28.2                      | 0.65                  | $1.92\times1.39$   | 166           |" (Table of ALMA-SV vs PdBI)
- max recoverable scale: _not stated_
- sensitivity: ALMA-SV RMS 9.6 mJy/beam, 0.65 km/s channels  
  > "| ALMA-SV | 12             | $\sim100$              | 9.2 K              | 9.6               | 28.2                      | 0.65                  | $1.92\times1.39$   | 166           |" (Table of ALMA-SV vs PdBI)
- time on source: ~100 min (ALMA-SV)  
  > "| ALMA-SV | 12             | $\sim100$              | 9.2 K              | 9.6               | 28.2                      | 0.65                  | $1.92\times1.39$   | 166           |" (Table of ALMA-SV vs PdBI)
- observing dates: ALMA-SV 2012 January  
  > "The observations were carried out in 2012 January with 16 12-m antennas (cite: Zapata2012; Niederhofer2012)." (Basic observational parameters)
- pi or archival as stated: _not stated_
- Line: (CH3)2CO 17_{7,11}-16_{6,10} EE (223775.253 MHz)
- Other facility **IRAM Plateau de Bure Interferometer**: Main 3 mm and 1.3 mm data sets used for acetone maps and column densities  
  > "We searched for acetone within our IRAM Plateau de Bure Interferometer 3 mm and 1.3 mm data sets." (abstract)
- Other facility **IRAM 30m**: Single-dish data for missing-flux estimates (priv. comm.)  
  > "Using the IRAM 30m single-dish data (J. Cernicharo, priv. comm.), the missing flux for the (CH$_{3}$)$_2$CO lines near 223 GHz is estimated as between 20% and 50%." (IRAM observations and line blending)
- External data: 1.3 mm continuum-based H2 column densities at acetone positions  
  > "An H$_{2}$ column density of $2.4\pm0.2\times10^{24}$ cm$^{-2}$ is derived toward the same position by using the 1 mm continuum emission (cite: Favre2011a)" (Ace-1) [from (cite: Favre2011a)]
- External data: Acetone spectroscopy from JPL database  
  > "Acetone spectroscopic data were taken from the JPL database based on the compilation of several data sets" (Table notes) [from (cite: Groner2002)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Calibrated ALMA-SV data retrieved from ESO archive  
  > "The calibrated ALMA-SV data were retrieved from the ESO archive." (Basic observational parameters)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: Clark algorithm in GILDAS, same as PdBI  
  > "the acetone emission images were cleaned with the same Clark algorithm as for the PdBI data" (Basic observational parameters)
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

- PdBI continuum images and H2 column densities  
  > "Our continuum emission images were presented in (cite: Favre2011a) where the H$_{2}$ column densities of selected clumps were also estimated." (IRAM observations and line blending) [from (cite: Favre2011a)]

### Not stated but needed to reproduce (our reading)

- ALMA-SV calibration/reduction version and spectral window setup
- Line-free channels and cell/image size for ALMA-SV imaging
- Observing frequency setup for ALMA-SV
- Clean masks and weighting

## Analysis recipe

1. **Image ALMA-SV acetone and compare with PdBI**: ALMA-SV data analyzed with GILDAS, cleaned with Clark algorithm; channel maps and spectra compared with PdBI at Ace-1, Ace-2, Ace-3, HC and MF-3  
  > "The ALMA-SV data were analyzed with the GILDAS package, and the acetone emission images were cleaned with the same Clark algorithm as for the PdBI data" (Basic observational parameters)
   - software: GILDAS
   - fitting: _not stated_
   - validation: Missing flux vs IRAM 30m estimated 10-20% for ALMA-SV  
  > "The missing flux of the ALMA-SV data is estimated to be 10–20% compared with the IRAM 30m single-dish data" (Basic observational parameters)

## Software

- **GILDAS** : Reduction and imaging of PdBI and ALMA-SV data  
  > "The ALMA-SV data were analyzed with the GILDAS package" (Basic observational parameters)
- **Weeds** : Synthesized acetone spectra  
  > "The synthesized spectra of acetone (Fig. [5](#model-spectra-1)) were produced with Weeds (cite: Maret2011) in the GILDAS package" (Synthesized spectra of acetone)
- **3D Slicer** : 3D visualization of cubes  
  > "we have prepared the three-dimensional (R.A., Dec., and $V_{\rm LSR}$) images of different molecules in Orion BN/KL using the 3D Slicer program" (Three-dimensional view)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Ace-1 acetone column density | 3.4e16 | ±0.1e16 | cm^-2 | 0 | an acetone column density is estimated to be $3.4\pm0.1\times10^{16}$ cm$^{-2}$ with an excitation temperature of $159\pm13$ K |
| Ace-1 rotational temperature | 159 | ±13 | K | 0 | an acetone column density is estimated to be $3.4\pm0.1\times10^{16}$ cm$^{-2}$ with an excitation temperature of $159\pm13$ K |
| Ace-2 rotational temperature | 145 | ±16 | K | 0 | We derived an acetone rotational temperature of $145\pm16$ K and a column density of $2.1\pm0.1\times10^{16}$ cm$^{-2}$ |
| ALMA-SV missing flux | 10–20 | not stated | % | 1 | The missing flux of the ALMA-SV data is estimated to be 10–20% compared with the IRAM 30m single-dish data |

## Qualitative findings

- PdBI distribution is consistent with ALMA-SV, but extended emission toward Ace-3 and the south is filtered out in PdBI.  
  > "Our PdBI spatial distribution and individual spectra are very consistent with the new ALMA-SV data toward Orion BN/KL." (Summary)

## Claim tuples

- H: Does PdBI filtering affect the acetone results? | E: Compared PdBI and ALMA-SV acetone maps and spectra at 223 GHz | R: ALMA-SV detects acetone at Ace-3 and the south that PdBI largely filters out | F: PdBI is consistent but resolves out extended emission | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Column density uncertainties from missing flux likely below a factor of two; beam filling factor uncertain.  
  > "the column density uncertainties owing to the missing flux are likely to be less than a factor of two" (Excitation temperature and column density)
- Caveat (inferred, ours): ALMA is minor; main results rely on PdBI data not reproduced here
- Caveat (inferred, ours): Missing-flux estimates rely on private-communication 30m data

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: PdBI raw data and reduction details
- Missing: 30m single-dish data (priv. comm.)
- Missing: ALMA-SV imaging parameters
- Data volume (inferred): ~10-50 GB for ALMA-SV
- Score (inferred): 2/5, ALMA only used in an appendix comparison with sparse processing detail.
- Rediscovery candidate: no, Main results come from PdBI data; ALMA recipe is incomplete.

## Links

- Companion: (cite: Favre2011a) (PdBI Orion BN/KL data sets, continuum and H2 columns)
- Related: ALMA Science Verification Orion BN/KL

## Checks

```json
{
 "quotes": 29,
 "quotes_ok": 29,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 56,
  "stated": 20,
  "rate": 0.357
 },
 "evidence_ok": true
}
```
