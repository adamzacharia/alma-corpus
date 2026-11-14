# Diffuse X-Ray-emitting Gas in the Central Region of Star-forming Galaxies

`2025ApJ...988..263Z` | The Astrophysical Journal 2025 | first author: Zhang, Chunyi | arXiv: 2506.17663 | DOI: 10.3847/1538-4357/ade71a

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, milky_way_ism
- Question: How does diffuse thermal X-ray luminosity of hot gas in the central regions of 23 nearby star-forming galaxies scale with SFR, spatial scale, stellar mass, molecular gas and baryonic mass?  
  > "we aim to investigate the scaling relation of $L_{\rm 0.5 - 2\,keV}^{\rm gas}$ with SFR on different spatial scales and examine its scale dependence in the central region of the 23 sample galaxies." (Introduction)
- Target **23 PHANGS star-forming galaxies (e.g. NGC 253, NGC 628, NGC 1433, NGC 5236, NGC 7793)**: coordinates _not stated_; z/distance 3.47-23.55 Mpc (Table 1)  
  > "Values in columns (2)$-$(4) are from (cite: 2021_Leroy_ApJS)." (Table 1); "The PHANGS survey selects galaxies with distances less than 24 Mpc" (2 data); distance from Leroy et al. 2021 (PHANGS)  
  > "Values in columns (2)$-$(4) are from (cite: 2021_Leroy_ApJS)." (Table 1); "The PHANGS survey selects galaxies with distances less than 24 Mpc" (2 data)

## Data provenance

- ALMA projects: _none stated_
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: interferometric and single-dish observations combined  
  > "These data include both interferometric and single-dish observations" (2.2 ALMA)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: PHANGS-ALMA Large Program CO(2-1), integrated intensity maps (broad mask) from PHANGS website  
  > "The CO(2-1) data for our sample galaxies were obtained from the PHANGS-ALMA Large Program (cite: 2021_Leroy_ApJS; 2021_Leroy_ApJS_b) at the PHANGS website" (2.2 ALMA)
- Line: CO J=2-1 (not stated)
- Other facility **Chandra**: Archival ACIS X-ray data for diffuse hot gas emission  
  > "All X-ray data used in this work were downloaded from the $Chandra$ Data Archive and reprocessed using CIAO v.4.13 and CALDB v.4.9.6." (2.1 Chandra)
- Other facility **WISE**: W1 3.4 um stellar mass and 22 um for SFR  
  > "We use near-IR imaging data from the Wide-field Infrared Survey Explorer (WISE) to trace the stellar mass." (2.3 WISE and GALEX)
- Other facility **GALEX**: FUV/NUV for SFR  
  > "using the combination of GALEX FUV (154 nm) and WISE 22 $\mu$m data to calculate the SFR." (2.3 WISE and GALEX)
- External data: Distance, inclination, half-mass radius of galaxies  
  > "Values in columns (2)$-$(4) are from (cite: 2021_Leroy_ApJS)." (Table 1) [from (cite: 2021_Leroy_ApJS)]
- External data: z0MGS WISE and GALEX images and SFR prescription  
  > "These data also come from the z0MGS project (cite: 2019_Leroy_ApJS_24L)" (2.3 WISE and GALEX) [from (cite: 2019_Leroy_ApJS_24L)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: PHANGS-ALMA released CO(2-1) products used  
  > "In this study, we use the integrated intensity maps from the “broad” mask scheme" (2.2 ALMA)
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

- ALMA sample selection, observational setup and data reduction  
  > "The strategy for sample selection, observational setup, and data reduction are described in (cite: 2021_Leroy_ApJS; 2021_Leroy_ApJS_b)." (2.2 ALMA) [from (cite: 2021_Leroy_ApJS; 2021_Leroy_ApJS_b)]
- CO(2-1)-to-CO(1-0) ratio R21=0.65  
  > "$R_{21}$ = 0.65 is the widely used CO(2-1)-to-CO(1-0) line ratio (cite: 2013_Leroy_AJ_19L; 2021_den_Brok_MNRAS_3221D)." (2.2 ALMA) [from (cite: 2013_Leroy_AJ_19L; 2021_den_Brok_MNRAS_3221D)]

### Not stated but needed to reproduce (our reading)

- ALMA project codes and CASA/pipeline versions
- exact PHANGS product version and resolution used
- aperture definitions and centers for molecular gas mass
- how Chandra spectral regions and break radii were set per galaxy
- priors/settings of LINMIX_ERR
- K-band luminosity conversion for faint-source estimate

## Analysis recipe

1. **Compute molecular gas mass from PHANGS CO(2-1)**: Integrated intensity to L'_CO (Solomon et al. 1997), then M_mol = alpha_CO R21^-1 L'_CO  
  > "We then derived the molecular gas mass from the line luminosity $L^\prime_{\rm CO}$ via" (2.2 ALMA)
   - parameter: alpha_CO(1-0)=4.35, R21=0.65  
  > "$R_{21}$ = 0.65 is the widely used CO(2-1)-to-CO(1-0) line ratio" (2.2 ALMA)
   - assumption: Milky Way CO-to-H2 factor for all galaxies  
  > "We assume the factor to be the standard Milky Way value $\alpha_{\rm CO(1-0)}$ = 4.35" (2.2 ALMA)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit X-ray scaling relations**: Bayesian linear regression of log L_X vs log SFR, M_star, M_mol, M_b  
  > "using the Bayesian linear regression method implemented in the IDL routine LINMIX_ERR (cite: 2007_Kelly_Apj)" (3.2)
   - software: LINMIX_ERR
   - fitting: LINMIX_ERR Bayesian regression  
  > "using the Bayesian linear regression method implemented in the IDL routine LINMIX_ERR (cite: 2007_Kelly_Apj)" (3.2)
   - validation: _not stated_

## Software

- **CIAO** v.4.13: Chandra reprocessing, deflare, wavdetect, specextract  
  > "reprocessed using CIAO v.4.13 and CALDB v.4.9.6" (2.1 Chandra)
- **XSPEC** v.12.11.0: X-ray spectral fitting with absorbed APEC  
  > "The spectral fitting was performed using the XSPEC v.12.11.0" (2.1 Chandra)
- **LINMIX_ERR** : Bayesian linear regression  
  > "using the Bayesian linear regression method implemented in the IDL routine LINMIX_ERR (cite: 2007_Kelly_Apj)" (3.2)
- **CARTA** : image visualization (acknowledged)  
  > "CARTA is the Cube Analysis and Rendering Tool for Astronomy" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Center L_X-SFR slope | 1.34 | ±0.16 | dimensionless | 2 | Center / 1.34 $\pm$ 0.16 / 40.15 $\pm$ 0.13 /   0.41   /    0.83 |
| Center L_X-SFR intercept | 40.15 | ±0.13 | log erg/s | 2 | Center / 1.34 $\pm$ 0.16 / 40.15 $\pm$ 0.13 /   0.41   /    0.83 |
| Disk L_X-SFR slope | 0.93 | ±0.16 | dimensionless | 2 | Disk        / 0.93 $\pm$ 0.16 / 40.14 $\pm$ 0.09 /   0.36   /    0.79 |
| L_X-M_mol slope | 1.13 | ±0.25 | dimensionless | 2 | 1.13(\pm0.25) {\rm log}\,\frac{M_{\rm mol}} {M_\odot} + 29.57(\pm2.16) |
| L_X-M_mol Spearman r_s | 0.77 | not stated | dimensionless | 2 | The Spearman rank correlation coefficient of this relation is $r_{\rm s}$ = 0.77 |
| L_X-M_b slope | 1.65 | ±0.38 | dimensionless | 2 | 1.65(\pm0.38) {\rm log}\,\frac{M_{\rm b}} {M_\odot} + 23.67(\pm3.65) |
| Faint compact source contribution (mean) | ~8% | not stated | percent | 0 | The average contribution of all galaxies is $\thicksim$8% |

## Qualitative findings

- Central L_X-SFR slope is super-linear and decreases with aperture radius, reaching the global level by ~2.5 kpc  
  > "Its slope anticorrelates with spatial scale up to 2.5 kpc, where it drops to the global level." (Summary)

## Claim tuples

- H: Central diffuse X-ray luminosity scales super-linearly with SFR | E: Chandra diffuse X-ray luminosity vs WISE/GALEX SFR for 23 galaxies, LINMIX_ERR fit | R: slope 1.34±0.16 for center vs 0.93 disk, 1.08 global | F: Stronger star formation gives more efficient X-ray conversion in centers | **supported**
- H: SFR is a better predictor of hot gas emission than M_star, M_mol, M_b | E: Compare scatter of relations | R: M_mol and M_b scatter 0.58, M_star 0.68, vs SFR 0.41 | F: L_X-SFR is most fundamental | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Two-component APEC+power-law model rejected as it did not improve fits  
  > "we found that the two-component spectral model does not significantly improve the fitting results or better constrain the parameters." (2.1 Chandra)
- How they decided it was enough: _not stated_
- Limitation (authors): Unresolved faint sources cannot be excluded  
  > "Although this cannot currently be excluded, we estimate the contribution of faint compact sources to be less than 30%" (2.1 Chandra)
- Caveat (inferred, ours): Fixed alpha_CO ignores central CO conversion factor variations
- Caveat (inferred, ours): Break radius defined from double beta fits may be degenerate
- Caveat (inferred, ours): ALMA role limited to molecular gas mass

## Reproducibility

- Data public (paper): Chandra archive and PHANGS website data  
  > "at the PHANGS website" (2.2 ALMA)
- Products in archive: _not stated_
- Missing: ALMA project codes
- Missing: per-galaxy region definitions
- Missing: LINMIX_ERR settings
- Data volume (inferred): ~10-50 GB (Chandra event files plus PHANGS moment maps)
- Score (inferred): 3/5, Public data and standard tools, but many analysis details are not given and ALMA part is minor.
- Rediscovery candidate: no, ALMA plays a minor role and the main results rely on Chandra reduction with incomplete region details.

## Links

- Method: (cite: 2021_Leroy_ApJS_b) (PHANGS-ALMA data reduction)
- Method: (cite: 2019_Leroy_ApJS_24L) (z0MGS SFR and stellar mass recipes)
- Companion: (cite: 2024_Zhangcy_ApJL) (earlier nuclear diffuse X-ray study of five galaxies)
- Companion: (cite: 2025_Zhangcy_ApJ_15Z) (M51 diffuse X-ray study)
- Related: PHANGS-ALMA
- Related: PHANGS
- Related: z0MGS

## Checks

```json
{
 "quotes": 40,
 "quotes_ok": 40,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2012.1.00650.S",
  "2013.1.00803.S",
  "2013.1.01161.S",
  "2015.1.00121.S",
  "2015.1.00782.S",
  "2015.1.00925.S",
  "2015.1.00956.S",
  "2016.1.00386.S",
  "2017.1.00392.S",
  "2017.1.00766.S",
  "2017.1.00886.L",
  "2018.1.00484.S",
  "2018.1.01321.S",
  "2018.1.01651.S",
  "2018.A.00062.S",
  "2019.2.00129.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 65,
  "stated": 26,
  "rate": 0.4
 },
 "evidence_ok": true
}
```
