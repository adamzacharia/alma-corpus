# Exploring the Mpc Environment of the Quasar ULAS J1342+0928 at z = 7.54

`2024ApJ...967...27R` | The Astrophysical Journal 2024 | first author: Rojas-Ruiz, Sofía | arXiv: 2404.02960 | DOI: 10.3847/1538-4357/ad3bab

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: agn_and_quasars, high_z_galaxies
- Question: Is the z = 7.54 quasar ULAS J1342+0928 surrounded by an overdensity of Lyman-break galaxies in its ~1 pMpc^2 environment?  
  > "We investigate the 1.1 pMpc$^2$ environment of the $z = 7.54$ luminous quasar ULAS J1342+0928." (abstract)
- Target **ULAS J1342+0928**: coordinates RA 205.5337428 deg, Dec 9.4773167 deg  
  > "| QSO–6381 | 205.5337428 | 9.4773167 | 100 | 17 | 100 | 7.59$^{+0.08}_{-0.11}$ | 483.16 | 7.5400$\pm$ 0.0003$^{$\dag$}$ |  |" (Table 1); "Systemic redshift measured using ALMA observations of the \[C ii\]$-158\ensuremath{\mu}m$ emission line from the quasar’s host galaxy in (cite: banados_z_2019)" (Table 1); z/distance z = 7.5400 ± 0.0003  
  > "| QSO–6381 | 205.5337428 | 9.4773167 | 100 | 17 | 100 | 7.59$^{+0.08}_{-0.11}$ | 483.16 | 7.5400$\pm$ 0.0003$^{$\dag$}$ |  |" (Table 1); "Systemic redshift measured using ALMA observations of the \[C ii\]$-158\ensuremath{\mu}m$ emission line from the quasar’s host galaxy in (cite: banados_z_2019)" (Table 1); distance from [C II] ALMA (Bañados et al. 2019)  
  > "| QSO–6381 | 205.5337428 | 9.4773167 | 100 | 17 | 100 | 7.59$^{+0.08}_{-0.11}$ | 483.16 | 7.5400$\pm$ 0.0003$^{$\dag$}$ |  |" (Table 1); "Systemic redshift measured using ALMA observations of the \[C ii\]$-158\ensuremath{\mu}m$ emission line from the quasar’s host galaxy in (cite: banados_z_2019)" (Table 1)

## Data provenance

- ALMA projects: 2017.1.00396.S
- bands: Band 6 (223 GHz [C II]) from previous work, not newly analyzed here  
  > "Currently, the only detection available of this galaxy is from ALMA 223  GHz observations of its \[C ii\] emission at $0.10\pm0.03$ Jy km s$^{-1}$" (5.2 Dusty Star-Forming Galaxy)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: FOV ~39" (~194 pkpc)  
  > "The current ALMA observations of this field cover only a FOV $\sim39"$, i.e. $\sim194$ pkpc, around the quasar" (5.2 Dusty Star-Forming Galaxy)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: [C II] 158 μm (not stated)
- Other facility **HST ACS/WFC3**: F814W, F105W, F125W deep imaging (Prog ID 1165)  
  > "We obtained data in the F814W (ACS, 13 orbits) serving as the non-detection filter, and the F105W and F125W filters (WFC3, 8 and 4 orbits each, respectively)." (2.1 HST data and reduction)
- Other facility **Spitzer/IRAC**: 3.6 and 4.5 μm archival images  
  > "Additional *Spitzer*/IRAC 3.6$\mu$m and 4.5$\mu$m images covering the same area of the quasar environment explored with *HST* are available from cycle 16 archival database (PI: Decarli)." (3.3 Spitzer/IRAC Photometry)
- Other facility **Chandra**: Existing 45 ks X-ray observations, no signal at C-4636  
  > "Existing 45ks *Chandra* observations of this field do not show any X-ray signal at this location" (5.1)
- External data: [C II] emitter at z=7.5341±0.0009 and its ALMA detection 0.10±0.03 Jy km/s  
  > "found to be at $z_{\mathrm{[C\,{\sc II}]}}=7.5341\pm0.0009$" (5.2 Dusty Star-Forming Galaxy) [from (cite: venemans_kiloparsec-scale_2020)]
- External data: Quasar systemic redshift 7.5400 from ALMA [C II]  
  > "where its systemic redshift measured from \[C ii\] emission is $z =7.5400 \pm 0.0003$" (5.1) [from (cite: banados_z_2019)]
- External data: CANDELS GOODS catalog for completeness test  
  > "We build the photometry catalog for `EAZY` using the fluxes from the GOODS catalog" (6.1 Completeness) [from (cite: finkelstein_evolution_2015)]

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

- LBG selection procedure follows earlier work  
  > "This analysis follows closely the procedure for Lyman-break detection in (cite: rojas-ruiz_probing_2020)." (4 Making the Catalogs) [from (cite: rojas-ruiz_probing_2020)]
- IRAC mosaics and PSF modeling  
  > "The mosaics and modeling are performed following (cite: kokorev_alma_2022)" (3.3 Spitzer/IRAC Photometry) [from (cite: kokorev_alma_2022)]

### Not stated but needed to reproduce (our reading)

- ALMA data reduction details (the ALMA data are not reprocessed here)
- QSO-LBG clustering calculation details and excess formula inputs

## Analysis recipe

1. **Reduce and align HST images**: DrizzlePac astrodrizzle/tweakreg alignment to F814W catalog  
  > "we use *tweakreg* on the F105W and F125W *HST* pipeline-reduced *flt.fits* files, with the F814W catalog as reference, `searchrad`=3. and `minobj`=6." (2.1)
   - software: DrizzlePac, Source Extractor
   - fitting: _not stated_
   - validation: Mean deviation between filters ~0.03"; vs Gaia DR2 ~0.05"  
  > "The final mean deviation within the astrometric solutions of the filters is $\sim$0.03$''$." (2.1)
2. **Photometry in PSF-matched images**: Source Extractor dual-mode on Y+J detection image, Kron apertures and 0.4" apertures; IRAC photometry via PSF modeling  
  > "We utilize the Software `Source Extractor` v2.25.0 to measure the photometry of the sources in all three *HST* filters in dual-mode with a coadded $Y_{105}+J_{125}$ as the detection image" (3)
   - software: Source Extractor, pyPHER, GOLFIR
   - parameter: DETECT_THRESH = 1.5, DETECT_MINAREA = 7  
  > "the combination of parameters DETECT_THRESH = 1.5 and DETECT_MINAREA = 7 maximize the number of sources detected while lowering the spurious fraction." (3)
   - fitting: _not stated_
   - validation: _not stated_
3. **Photometric redshifts and candidate selection**: EAZY fit with 14 templates, S/N and P(z) cuts, low-z chi2 test  
  > "The integrated redshift probability $P(z)$ calculated from `EAZY` at $P(6<z<12) > 60\%$, securing that a high-redshift solution dominates over the total probability distribution." (4.2)
   - software: EAZY
   - assumption: flat luminosity prior, z=0.01-12, Inoue 2014 IGM  
  > "assume a flat luminosity prior, as galaxy colors at $z \gtrsim 6$ are not yet well understood" (4.1)
   - fitting: chi2 minimization, linear combination of templates  
  > "`EAZY` calculates the probability distribution function of photometric redshifts $P(z)$ based on a minimized $\chi^2$ fit of the observed photometry in all given filters to different SED models of known galaxy types." (Photometric Redshifts with EAZY)
   - validation: Visual inspection; Δχ² low-z vs high-z >= 4  
  > "If $\Delta{\chi^2_{l-h}} =\chi^2_{lowz} - \chi^2_{highz} < 4$ the goodness of the fit is lower than the threshold of 95% confidence interval" (Selection Criteria for Catalog)
4. **Completeness test vs GOODS**: Reselect with only three HST filters in GOODS catalog and compare to z=7-8 sources  
  > "Hence, we recover in total only 31/125, i.e. $\sim25\%$ of the sources." (6.1)
   - software: EAZY
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **EAZY** 2015-05-08: Photometric redshifts  
  > "version 2015-05-08 to calculate the photometric redshifts of all sources in our catalogs" (4.1)
- **Source Extractor** v2.25.0: Photometry  
  > "We utilize the Software `Source Extractor` v2.25.0" (3)
- **DrizzlePac** : HST image alignment and drizzling  
  > "We use *tweakreg* to align the uncleaned, original *flc.fits* images" (2.1)
- **pyPHER** : PSF matching kernels  
  > "The matching kernel for image convolution is produced with `pyPHER`" (2.2)
- **GOLFIR** : IRAC PSF-model photometry  
  > "a PSF model method is produced using the tools from the Great Observatories Legacy Fields IR Analysis Tools" (3.3 Spitzer/IRAC Photometry)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| C-4636 photometric redshift | 7.69 | +0.33/-0.23 | dimensionless | 3 | / C–4636 / 205.5435057 / 9.4851103 / 100 / 20 / 80 / 7.69$^{+0.33}_{-0.23}$ / 16.51 / |
| C-4636 J125 magnitude | 26.41 | not stated | AB mag | 2 | $mag_{F125W} = 26.41$ at $223$ projected-pkpc from the quasar |
| Recovered fraction in GOODS test | 31/125 (~25%) | not stated | dimensionless | 4 | Hence, we recover in total only 31/125, i.e. $\sim25\%$ of the sources. |

## Qualitative findings

- Only one new LBG candidate near the quasar; two additional z~6.9 candidates near a z=6.84 absorber  
  > "The final catalog results in the recovery of the quasar and one LBG with magnitude $J_{125} = 26.4$" (7 Summary)

## Claim tuples

- H: The z=7.54 quasar resides in an LBG overdensity | E: HST+Spitzer LBG selection and comparison with clustering expectations | R: One LBG candidate; excess 0.46 | F: No clear overdensity; limited by low numbers and incompleteness | **partially**
- H: Filter set limits LBG recovery at z~7.5 | E: Reselect GOODS sources using only three filters | R: ~25% recovered | F: Many LBGs missed without a filter redward of the break | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Low number statistics and low completeness  
  > "Note that this measurement is limited by low number statistics." (6.2)
- Caveat (inferred, ours): Clustering comparison relies on z=4 correlation function
- Caveat (inferred, ours): Single field, cosmic variance

## Reproducibility

- Data public (paper): HST data in MAST, Spitzer archival, ALMA 2017.1.00396.S  
  > "This paper makes use of *HST* data from program cy15/GO 1165 that can be found in MAST" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Clustering excess computation
- Missing: Several selection details lost in text
- Data volume (inferred): ~10-50 GB (HST and Spitzer images)
- Score (inferred): 3/5, Imaging recipe fairly detailed but ALMA plays minor role and some steps are missing
- Rediscovery candidate: no, Main analysis uses HST/Spitzer, not ALMA, and results are few.

## Links

- Method: (cite: rojas-ruiz_probing_2020) (LBG selection procedure)
- Method: (cite: kokorev_alma_2022) (IRAC modeling)
- Companion: (cite: venemans_kiloparsec-scale_2020) (ALMA [C II] companion detection)
- Companion: (cite: banados_z_2019) (Quasar systemic redshift)
- Related: CANDELS GOODS

## Checks

```json
{
 "quotes": 43,
 "quotes_ok": 43,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 31,
  "rate": 0.431
 },
 "evidence_ok": true
}
```
