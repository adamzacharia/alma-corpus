# Mass Functions of Giant Molecular Clouds and Young Star Clusters in Six Nearby Galaxies

`2020ApJ...893..135M` | The Astrophysical Journal 2020 | first author: Mok, Angus | arXiv: 2004.02698 | DOI: 10.3847/1538-4357/ab7a14

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type archival_reuse

## Science

- Fields: nearby_galaxies, star_formation, milky_way_ism
- Question: Do the mass functions of GMCs and young star clusters in six nearby galaxies show physical upper cutoffs, and how do their power-law indices compare?  
  > "We compare the mass functions of young star clusters (ages $\leq 10$ Myr) and giant molecular clouds (GMCs) in six galaxies that cover a large range in mass, metallicity, and star formation rate" (abstract)
- Target **NGC 3627**: coordinates _not stated_; z/distance 10.1 Mpc  
  > "| NGC 3627 | 10.1 | 4.89 | 742 |" (Table 1); distance from _not stated_
- Target **NGC 3256**: coordinates _not stated_; z/distance 36 Mpc  
  > "| NGC 3256 | 36 | 50 | 505 |" (Table 1); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00956.S, 2015.1.00714.S, 2012.1.00762.S, 2011.0.00876.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12-m and 7-m (ACA) arrays  
  > "then combine the results from the 12-meter and 7-meter (ACA) arrays for each galaxy" (2.2 New Catalogs)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: NGC 3627: 0.95x0.88 arcsec (46x43 pc); NGC 3256: 0.45x0.28 arcsec (78x49 pc)  
  > "| NGC 3627$^5$ | CO(2-1) | 4.35 | 0.8 | 0.95$\times$0.88 | 46$\times$43 |" (Table 1 (observations))
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (not stated)
- Other facility **HST (LEGUS, H-alpha LEGUS)**: Cluster catalog for NGC 3627 and other cluster catalogs  
  > "based on broad-band images taken in five filters as part of the LEGUS project (UV, UBVI; (cite: Calzetti15)), plus narrow-band H$\alpha$ photometry" (3.2 New Catalog for NGC 3627)
- External data: GMC catalogs for LMC, M83, M51, Antennae  
  > "Below, we summarize some basic information about the published GMC catalogs in the LMC, M83, M51, and the Antennae" (2.1 Previous Catalogs) [from Wong11; Freeman17; Colombo14; Zaragoza14]
- External data: Cluster catalogs for LMC, M51, M83, Antennae, NGC 3256  
  > "have been collected from the literature, and the resulting mass functions published in (cite: Chandar15; Chandar17)" (3.1 Previous Catalogs) [from Hunter03; Chandar16; Whitmore10; Mulia16]

## Processing

### Calibration

- pipeline or manual: Pipeline-calibrated archive data used  
  > "After downloading the pipeline calibrated datasets" (2.2 New Catalogs)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA tclean, non-interactive, to 2x rms threshold  
  > "run the tclean process until it reaches a clean threshold of twice the measured rms noise" (2.2 New Catalogs)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Performed on individual datasets  
  > "We first perform continuum subtraction for the individual interferometric datasets" (2.2 New Catalogs)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12-m and ACA combined; NGC 3627 feathered with total power  
  > "we also run the feathering routine from CASA to incorporate the zero-spacing information" (2.2 New Catalogs)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Maximum-likelihood fitting procedure  
  > "we uniformly apply the robust maximum-likelihood fitting method developed in (cite: Mok19)" (Introduction) [from Mok19]

### Not stated but needed to reproduce (our reading)

- tclean weighting/robust, cell size, image size, channel width
- line-free channels and continuum subtraction order
- feathering parameters and single-dish data
- CPROPSTOO version and full parameter set
- fitting grid ranges for beta and M*

## Analysis recipe

1. **Image CO cubes**: Continuum subtraction, 12m+7m combination, tclean, feather for NGC 3627  
  > "To image the dataset, we use the non-interactive cleaning process in the tclean routine." (2.2 New Catalogs)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Detect GMCs and derive masses**: CPROPSTOO, >=5 sigma in two adjacent channels, grown to 2 sigma; CO luminosity to H2 mass  
  > "The routine selects objects that are detected at the $\geq 5\sigma$ level in two adjacent channels" (2.2 New Catalogs)
   - software: CPROPSTOO
   - parameter: Delta=2, minimum cloud size 25 pixels  
  > "$\Delta=2$ in SNR units (which sets the required contrast) and a minimum cloud size of 25 pixels" (2.2 New Catalogs)
   - assumption: alpha_CO = 4.35 Msun (K km/s pc^2)^-1; CO(2-1)/CO(1-0) = 0.8  
  > "standard CO-to-H$_2$ conversion factor of 4.35 M$_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$ and a line ratio between CO(2-1) and CO(1-0) of 0.8" (2.2 New Catalogs)
   - fitting: _not stated_
   - validation: Varying Delta 1-3 has small effect  
  > "Tests show that varying the adopted value of $\Delta$ (between 1.0 to 3.0) has only a small effect on our conclusions." (2.2 New Catalogs)
3. **Fit Schechter and power-law mass functions**: Unbinned maximum likelihood above completeness limit, Nelder-Mead, contours from chi-square; with and without 0.3 dex log-normal errors  
  > "we find the maximum-likelihood $L_{\rm max}$ using the (cite: Nelder65) method" (4 Maximum-Likelihood Fits)
   - parameter: Upper integration limit 100x most massive object  
  > "we set the upper integration limit in equation (1) to be 100 times the mass of the most massive cluster in that sample" (4 Maximum-Likelihood Fits)
   - assumption: GMC mass uncertainty 0.3 dex  
  > "We will adopt this as a fiducial value for the errors in the GMC masses." (2.1 Previous Catalogs)
   - fitting: _not stated_
   - validation: AIC and relative likelihood compare power law vs Schechter  
  > "We calculate the Akaike Information Criterion" (4.3)

## Software

- **CASA** : Reduction, tclean imaging, feathering  
  > "we perform our data reduction and imaging using the CASA software package" (2.2 New Catalogs)
- **CPROPSTOO** : GMC detection and properties  
  > "We use the publicly available CPROPSTOO code" (2.2 New Catalogs)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| GMC power-law index beta_PL | -2.3 | 0.3 | dimensionless | 3 | $\beta_{\rm PL}=-2.3\pm0.3$ for our GMC sample |
| Cluster power-law index beta_PL | -2.0 | 0.3 | dimensionless | 3 | $\beta_{\rm PL}=-2.0\pm0.3$ for the cluster sample |
| NGC 3627 GMC beta_PL | -2.30 | [2.20, 2.40] 1 sigma | dimensionless | 3 | / NGC 3627 / 6.5 / 7.85 / 189 / 1.98 \[1.65, 2.25\] / 7.72 \[7.40, 8.45\] / 2.30 \[2.20, 2.40\] / |
| NGC 3256 GMC beta_PL | -2.10 | [2.00, 2.20] 1 sigma | dimensionless | 3 | / NGC 3256 / 7.6 / 8.89 / 123 / 1.61 \[1.25, 1.95\] / 8.71 \[8.40, 9.00\] / 2.10 \[2.00, 2.20\] / |

## Qualitative findings

- M51 is the only galaxy with a cutoff in both GMC and cluster populations  
  > "M51 is the only galaxy that shows some evidence for an upper cutoff ($M_*$) in both populations." (abstract)

## Claim tuples

- H: GMC and cluster mass functions have physical upper cutoffs | E: Maximum-likelihood Schechter fits in six galaxies | R: Most are consistent with pure power laws; only M51 shows cutoffs in both | F: Physical cutoffs are the exception | **supported**
- H: GMC and cluster slopes are similar, as FKM predicts | E: Compare beta_PL across galaxies | R: -2.3±0.3 vs -2.0±0.3 | F: SFE largely independent of mass | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Small sample; heterogeneous data prevent SFE estimates; LMC not directly comparable  
  > "Our results are based on the GMC and cluster populations in a relatively small number of galaxies." (6 Conclusions)
- Caveat (inferred, ours): Heterogeneous CO transitions, resolutions and coverage
- Caveat (inferred, ours): Fixed alpha_CO for LIRG mergers
- Caveat (inferred, ours): Completeness limits chosen by eye

## Reproducibility

- Data public (paper): Archival ALMA data downloaded from the archive  
  > "from the ALMA archive" (2.2 New Catalogs)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: Completeness limit determination details
- Missing: Cluster catalogs for some galaxies
- Data volume (inferred): ~100-300 GB
- Score (inferred): 3/5, Public data and method, but imaging details are sparse.
- Rediscovery candidate: no, Imaging recipe incomplete and the fit relies on external catalogs.

## Links

- Method: Mok19 (Maximum-likelihood method)
- Method: Rosolowsky06 (CPROPS cloud detection)
- Related: LEGUS
- Related: PAWS
- Related: PHANGS

## Checks

```json
{
 "quotes": 39,
 "quotes_ok": 39,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2012.1.00762.S",
  "2011.0.00876.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 67,
  "stated": 27,
  "rate": 0.403
 },
 "evidence_ok": true
}
```
