# Origins of Molecular Clouds in Early-type Galaxies

`2019ApJ...887..149B` | The Astrophysical Journal 2019 | first author: Babyk, Iu. V. | arXiv: 1810.11465 | DOI: 10.3847/1538-4357/ab54ce

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, galaxy_clusters_and_sz
- Question: Is molecular gas in early-type galaxies related to, and condensed from, their hot X-ray atmospheres, as in cluster central galaxies?  
  > "The primary aim of this study is to understand the origin of molecular gas in the cores of low- and high-mass systems." (Molecular gas distribution)
- Target **IC1459, NGC1332, NGC6861 (ALMA Band 6), NGC1407, NGC4696 (ALMA Band 3)**: coordinates IC1459: 22:57:10.608 -36:27:43.997 (J2000)  
  > "| IC1459 | 22:57:10.608 | -36:27:43.997 | 2196 | 45.14 | E3 |  | 0.006011 | 25.503 | 25.8 |" (Table 1); z/distance IC1459 z=0.006011, D_A=25.503 Mpc  
  > "| IC1459 | 22:57:10.608 | -36:27:43.997 | 2196 | 45.14 | E3 |  | 0.006011 | 25.503 | 25.8 |" (Table 1); distance from redshift with H0=70, OmegaM=0.3; SBF for some Virgo galaxies  
  > "| IC1459 | 22:57:10.608 | -36:27:43.997 | 2196 | 45.14 | E3 |  | 0.006011 | 25.503 | 25.8 |" (Table 1)

## Data provenance

- ALMA projects: 2013.1.00229.S, 2015.1.00989.S, 2015.1.01198.S, 2015.1.01572.S
- bands: Band 6 (CO 2-1) for IC1459, NGC1332, NGC6861; Band 3 (CO 1-0) for NGC1407, NGC4696  
  > "IC1459, NGC1332, and NGC6861 were observed in ALMA band 6 to cover the CO(2-1) line emission, while NGC1407 and NGC4696 were observed in band 3 to cover CO(1-0) line emission." (ALMA data reduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Synthesized beams from 0.32x0.24 arcsec (NGC1332) to 2.29x1.74 arcsec (NGC4696)  
  > "| NGC1332 | 2014-09-01 | 22.3 | $0.32\times0.24$ |" (Table 3)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 11.6 to 77.7 min  
  > "| NGC4696 | 2016-01-27 | 77.7 | $2.29\times1.74$ |" (Table 3)
- observing dates: 2014-09-01 to 2016-05-03  
  > "| NGC1407 | 2016-05-03 | 15.0 |" (Table 3)
- pi or archival as stated: Archival ALMA data  
  > "We analyzed archival ALMA data for five galaxies from our sample." (ALMA data reduction)
- Line: CO 2-1 (not stated)
- Line: CO 1-0 (not stated)
- Other facility **Chandra**: X-ray archival data for hot atmosphere profiles of 40 galaxies  
  > "Here, we analyze the thermodynamic properties of the hot atmospheres of 40 early-type galaxies from $Chandra$ archival data." (Introduction)
- Other facility **IRAM 30m**: Single-dish CO masses (ATLAS3D and BCGs)  
  > "ATLAS${}^{3D}$ molecular gas masses and upper limits were measured with single dish IRAM observations (cite: Young:11)." (Sample selection)
- External data: CO molecular gas masses and upper limits for ATLAS3D galaxies  
  > "we also use previously published results of (cite: Young:11; Su:13; Boz) and (cite: Pulido:17)" (ALMA data reduction) [from Young:11; Su:13; Boizelle:17; Pulido:17]
- External data: BCG sample X-ray and CO properties  
  > "Single dish CO measurements from (cite: Edge:01), subsequently analyzed by (cite: Pulido:17), form the cluster central galaxy sample" (Sample selection) [from Edge:01; Pulido:17]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline reduction scripts  
  > "The data were processed in CASA version 4.7.2 using the ALMA pipeline reduction scripts." (ALMA data reduction)
- casa version: CASA 4.7.2  
  > "The data were processed in CASA version 4.7.2 using the ALMA pipeline reduction scripts." (ALMA data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: continuum phase self-calibration applied  
  > "We applied continuum phase self-calibration to each dataset which improved the image quality." (ALMA data reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "The continuum subtracted measurement sets were imaged using natural weighting for better sensitivity with 20 km s$^{-1}$ channels." (ALMA data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub  
  > "To isolate the molecular line emission, the continuum was subtracted using `uvcontsub`." (ALMA data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: 20 km/s channels  
  > "imaged using natural weighting for better sensitivity with 20 km s$^{-1}$ channels." (ALMA data reduction)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Chandra reduction details and X-ray fitting of beta-model profiles  
  > "Data reduction was done using ciao version 4.8 and caldb version 4.7.1 (see (cite: Babyk:17scal; Hogan:17) for more details)." (Data processing) [from (cite: Babyk:17scal; Hogan:17)]
- Line intensity error formula  
  > "the errors in the line intensity ($\sigma_{I}$) were estimated using the formula given in (cite: Young:11)" (ALMA data reduction) [from (cite: Young:11)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and uvcontsub fit order
- Image size, cell size, masks, clean threshold
- Integration velocity ranges per galaxy
- Self-calibration solution intervals
- Which flux calibrator and flux uncertainty were used
- CO(2-1)/(1-0) ratio is assumed, but aperture for flux extraction not given for detections

## Analysis recipe

1. **Image ALMA CO cubes**: Pipeline calibration, continuum self-cal, uvcontsub, natural-weighted imaging with 20 km/s channels, integrate channels with line  
  > "Integrated line emission maps were produced by integrating over all the channels containing line emission." (ALMA data reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: Derived masses consistent with Boizelle et al. measurements  
  > "Our derived cold gas masses are consistent with (cite: Boz) measurements." (ALMA data reduction)
2. **Measure CO line flux and upper limits**: Gaussian fit for NGC4696; numerical integration for NGC1332/NGC6861; 3 sigma limits in 2x2 kpc box assuming 200 km/s FWHM  
  > "For NGC4696, the spectrum was fitted with a single Gaussian profile to get line intensity." (ALMA data reduction)
   - assumption: Line FWHM 200 km/s for upper limits  
  > "which we assume to be 200 km s$^{-1}$" (ALMA data reduction)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive molecular gas mass**: M_mol from CO(1-0) intensity, Solomon & Vanden Bout formula  
  > "The molecular gas mass is calculated using integrated CO(1–0) line intensity as given in (cite: Solomon:05) and (cite: Bolatto:13)" (ALMA data reduction)
   - assumption: X_CO = 2e20 cm^-2 (K km/s)^-1; CO(2-1)/CO(1-0) flux density ratio 3.2  
  > "a constant CO(2-1)/CO(1-0) flux density ratio of 3.2 to convert CO(2-1) flux densities into estimated CO(1-0) values" (ALMA data reduction)
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit M_mol vs X-ray gas mass and density relations**: BCES for detections; survival-analysis likelihood with power law including upper limits  
  > "A bivariate correlated error and intrinsic scatter (BCES) routine (cite: Akritas:96) was used to perform linear modeling in log space." (M_mol-M_X relation)
   - software: BCES
   - fitting: Gaussian likelihood; upper limits sigma = limit/3; 10,000 bootstrap iterations for BCES errors  
  > "Parameter errors are determined using 10,000 iterations of Monte Carlo bootstrap re-sampling." (M_mol-M_X relation)
   - validation: _not stated_

## Software

- **CASA** 4.7.2: ALMA data processing and imaging  
  > "The data were processed in CASA version 4.7.2 using the ALMA pipeline reduction scripts." (ALMA data reduction)
- **CIAO** 4.8: Chandra data reduction  
  > "Data reduction was done using ciao version 4.8 and caldb version 4.7.1" (Data processing)
- **XSPEC** 12.9.1: X-ray spectral fitting  
  > "Spectral analysis was done with xspec version 12.9.1" (Spectral extraction and modeling)
- **DSDEPROJ** : Spectral deprojection  
  > "For this the model-independent DSDEPROJ routine (cite: Russell:08) was adopted." (Galaxy properties)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| M_mol vs M_X slope (10 kpc, BCES, detections) | 1.4 | 0.1 | dimensionless | 4 | $M_{\rm mol}  \propto M_{\rm X}^{1.4\pm0.1}$ |
| M_mol vs n_e slope | 1.8 | 0.3 (abstract); 0.2 (Sec 5.3) | dimensionless | 4 | $M_{\rm mol}  \propto n_{\rm e}^{1.8\pm0.3}$ |
| M_mol NGC1332 (ALMA) | 6.04 | 0.05 | table units (log-style, as printed) | 3 | $38.72\pm 0.31$ / \- / $6.04\pm 0.05$ |
| M_mol NGC6861 (ALMA) | 48.72 | 0.87 | table units as printed | 3 | $89.91 \pm 1.62$ / \- / 48.72$\pm$0.87 |
| M_mol vs M_X slope with survival analysis | 1.37 | 0.21 | dimensionless | 4 | $M_{\rm mol} \propto M_{\rm X}^{1.37\pm0.21}$ |

## Qualitative findings

- CO-detected early-type galaxies have atmospheric cooling time below ~1 Gyr at 10 kpc; no relation with t_c/t_ff  
  > "We find no relationship between the ratio of the cooling time to free fall time, $t_{\rm c}/t_{\rm ff}$, and the presence or absence of molecular clouds in early-type galaxies." (abstract)

## Claim tuples

- H: Molecular gas in ETGs condensed from hot atmospheres, like in BCGs | E: Chandra thermodynamic profiles of 40 ETGs compared with CO masses, combined with BCG sample | R: M_mol ∝ M_X^1.4±0.1, ∝ n_e^1.8±0.3; detections when t_c < ~1 Gyr at 10 kpc | F: Data consistent with much molecular gas condensing from hot atmospheres | **supported**
- H: Thermal instability threshold t_c/t_ff predicts molecular gas | E: Plot t_c/t_ff profiles split by CO detection | R: Minima 10-30; detections do not segregate | F: t_c/t_ff plays no role; t_c is the better indicator | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Mergers and stellar ejecta considered as other sources; all three may contribute  
  > "They may acquire their molecular clouds at some level by all three mechanisms." (Stellar Ejecta)
- How they decided it was enough: _not stated_
- Limitation (authors): Archival selection function is poorly defined; many CO upper limits  
  > "Interpreting trends based on archival analyses can be perilous owing to the poorly-defined selection function." (Sample selection)
- Caveat (inferred, ours): ALMA is minor; most molecular masses come from single-dish literature with differing X_CO
- Caveat (inferred, ours): Early-type galaxy-only slopes are consistent with no correlation
- Caveat (inferred, ours): Mass ratio quoted inconsistently (3-10% vs 10-20%)
- Caveat (inferred, ours): Table 3 mass units for ALMA entries are unclear

## Reproducibility

- Data public (paper): Archival ALMA and Chandra data  
  > "$Chandra$ observations were downloaded from HEASARC[^4] archive." (Data processing)
- Products in archive: _not stated_
- Missing: Imaging parameters and line windows
- Missing: Earlier-paper Chandra details in Babyk 2018
- Missing: Full CO flux literature values
- Data volume (inferred): ~50-150 GB for the five ALMA datasets; Chandra archive data additional
- Score (inferred): 3/5, Chandra pipeline and fitting are described, ALMA part is brief, and key inputs come from other papers.
- Rediscovery candidate: no, ALMA role is minor and main results rely on Chandra and literature CO data with several unstated settings.

## Links

- Method: Babyk:17scal (Chandra reduction and spectral model details)
- Method: Pulido:17 (BCG sample and relations)
- Companion: Babyk17nature (Entropy profiles of the same sample)
- Related: ATLAS3D

## Checks

```json
{
 "quotes": 52,
 "quotes_ok": 52,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 37,
  "rate": 0.529
 },
 "evidence_ok": true
}
```
