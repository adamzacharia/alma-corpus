# Molecular gas inflows and outflows in ultraluminous infrared galaxies at z ∼ 0.2 and one QSO at z = 6.1

`2020A&A...633L...4H` | Astronomy and Astrophysics 2020 | first author: Herrera-Camus, R. | arXiv: 1912.05548 | DOI: 10.1051/0004-6361/201937109

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, high_z_galaxies, agn_and_quasars
- Question: Do ULIRGs at z~0.2-0.3 and a z=6.13 QSO show molecular gas inflows or outflows in OH 119 um absorption, and how strong are they?  
  > "We aim to search and characterize inflows and outflows of molecular gas in four ultraluminous infrared galaxies" (abstract)
- Target **ULAS J131911+095051**: coordinates _not stated_; z/distance z=6.1330  
  > "the fifth one is ULAS J131911+095051, a QSO at $z=6.13$" (Sample and observations); distance from [C II] line detection by Wang et al. 2013  
  > "the fifth one is ULAS J131911+095051, a QSO at $z=6.13$" (Sample and observations)

## Data provenance

- ALMA projects: 2012.1.00391.S
- bands: Band 7  
  > "was observed with ALMA Band 7 as part of Project 2012.1.00391.S" (Sample and observations)
- frequencies and spectral setup: two observing blocks, spectral windows stitched to cover 348.18-355.60 GHz (~±2500 km/s around OH 119 um)  
  > "stitched together pairs of consecutive spectral windows from each block to continuously cover the \[348.18,355.60\] GHz frequency range" (Sample and observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: HPBW = 0.63'' x 0.44''  
  > "${\rm HPBW}=0.63\ensuremath{''} \times 0.44\ensuremath{''}$" (Sample and observations)
- max recoverable scale: _not stated_
- sensitivity: 0.19 and 0.14 mJy/beam in 150 km/s bins  
  > "reaching sensitivities of 0.19 and 0.14 mJy beam$^{-1}$ in 150 km s$^{-1}$ velocity bins, respectively" (Sample and observations)
- time on source: 41 and 80 min with 32 antennas  
  > "The first and second halves of the frequency range were observed for 41 and 80 min with 32 antennas" (Sample and observations)
- observing dates: _not stated_
- pi or archival as stated: PI J. Graciá-Carpio  
  > "Project 2012.1.00391.S (PI J. Graciá-Carpio)" (Sample and observations)
- Line: OH 119 um doublet absorption (not stated)
- Other facility **Herschel/PACS**: OH 119 um spectra of four ULIRGs (program OT2_jgracia_1)  
  > "Observations of the OH 119 $\mu$m doublet for the four ULIRGs were carried out using the PACS instrument" (Sample and observations)
- External data: [C II]-based redshift of the QSO  
  > "The rest-frame velocity is set based on a precise redshift measurement derived from the detection of the \[C II\] line by (cite: rhc_wang13)." (Results) [from (cite: rhc_wang13)]
- External data: Models and galaxy sample used for EW vs mass outflow rate relation  
  > "Figure [6](#fig:EW_dMdt) shows the relation between $\dot{M}_{\rm mol,out}$ –inferred from the models of (cite: rhc_gonzalez-alfonso17)" (OH 119 um equivalent width – mass outflow rate empirical relation) [from (cite: rhc_gonzalez-alfonso17)]
- External data: Molecular gas mass of the QSO from CO(6-5)  
  > "is $M_{\rm mol}=1.5\times10^{10}~M_{\odot}$ (cite: rhc_wang13)" (ALMA dust continuum map and updated SED) [from (cite: rhc_wang13)]

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

- Gaussian-fit procedure for OH doublet  
  > "Following a procedure similar to that used by (cite: rhc_veilleux13) and (cite: rhc_stone16)" (Results) [from (cite: rhc_veilleux13); (cite: rhc_stone16)]
- Inflow/outflow classification by v50 threshold ±50 km/s  
  > "We then follow the conservative criteria by (cite: rhc_rupke05b) to classify the observed gas flows" (Results) [from (cite: rhc_rupke05b)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration pipeline/CASA version and calibrators
- Imaging parameters (weighting, cell, deconvolver) and spectrum extraction aperture details
- Continuum-subtraction/line-free channels
- Gaussian fit initial parameters and significance computation
- Dust SED fit method and priors

## Analysis recipe

1. **fit OH doublet absorption**: Four-Gaussian fit of 16OH doublet, measure v50, v84, EW, flux  
  > "we use the code *PySpecKit* (cite: rhc_ginsburg11) to fit the $^{16}$OH ($\lambda$119.233,119.441 $\mu$m) doublet using four Gaussian components" (Results)
   - software: PySpecKit
   - fitting: _not stated_
   - validation: _not stated_
2. **estimate mass outflow rate**: Empirical relation Mdot = 0.29 x EW(v<-200) x (L_FIR/1e10)^1/2  
  > "The best linear fit, forced to have zero intercept, yields" (OH 119 um equivalent width – mass outflow rate empirical relation)
   - fitting: linear fit forced through zero  
  > "The best linear fit, forced to have zero intercept, yields" (OH 119 $\mu$m equivalent width – mass outflow rate empirical relation)
   - validation: _not stated_

## Software

- **PySpecKit** : Gaussian fitting of OH doublet  
  > "we use the code *PySpecKit* (cite: rhc_ginsburg11) to fit the $^{16}$OH" (Results)
- **HIPE** : Herschel PACS data reduction  
  > "The data were reduced using the PACS data reduction and calibration pipeline included in HIPE" (Sample and observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| QSO OH v50 | -154 | not stated | km/s | 1 | the median ($v_{50}$) and $v_{84}$ velocities are $-154$ km s$^{-1}$ and $-314$ km s$^{-1}$, respectively |
| QSO molecular mass outflow rate | ~200 | not stated | Msun/yr | 2 | we determine a molecular mass outflow rate for ULAS J131911+095051 of $\dot{M}_{\rm out,mol}\sim200~M_{\odot}~{\rm yr}^{-1}$ |
| QSO 125 um rest-frame flux density | 8.56 | 0.12 | mJy | 0 | $S_{\rm 125~\mu m, rest}=8.56\pm0.12$ mJy |
| QSO log L_FIR | 13.4 | 0.16 | log Lsun | 0 | log$_{10}(L_{\rm FIR}/L_{\odot})=13.4\pm0.16$ |

## Qualitative findings

- Tentative (~3 sigma) blueshifted OH absorption in the z=6.13 QSO suggests a modest molecular outflow  
  > "we tentatively detect ($\sim3\sigma$) the OH 119 $\mu$m doublet in absorption in the $z=6.13$ QSO" (abstract)

## Claim tuples

- H: Does the z=6.13 QSO host a molecular outflow traced by OH 119 um? | E: ALMA Band 7 OH spectrum Gaussian fit | R: ~3 sigma blueshifted absorption, v50=-154 km/s | F: Tentative modest outflow of ~200 Msun/yr, feedback subsided | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Deeper, higher resolution ALMA observations needed to confirm the outflow  
  > "deeper and higher angular resolution ALMA observations are required to confirm the existence of the molecular outflow" (Discussion)
- Caveat (inferred, ours): 3 sigma detection is marginal
- Caveat (inferred, ours): Mass outflow rate relies on an empirical relation calibrated on nearby ULIRGs

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Calibration and imaging details
- Missing: Fit settings
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Public ALMA data but few processing details.
- Rediscovery candidate: no, Recipe incomplete and detection marginal.

## Links

- Method: (cite: rhc_gonzalez-alfonso17) (Models underlying mass outflow rate relation)
- Related: Herschel OT2_jgracia_1

## Checks

```json
{
 "quotes": 30,
 "quotes_ok": 30,
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
  "facts": 59,
  "stated": 22,
  "rate": 0.373
 },
 "evidence_ok": true
}
```
