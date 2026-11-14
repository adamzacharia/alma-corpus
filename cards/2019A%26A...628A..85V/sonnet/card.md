# Disk masses in the Orion Molecular Cloud-2: distinguishing time and environment

`2019A&A...628A..85V` | Astronomy and Astrophysics 2019 | first author: van Terwisga, S. E. | arXiv: 1905.09804 | DOI: 10.1051/0004-6361/201935378

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks, star_formation
- Question: Are initial disk dust masses in the Orion Molecular Cloud-2 (beyond 0.5 pc from the Trapezium) the same as in low-mass star-forming regions, and how much does external photoevaporation reduce disk masses near the Trapezium?  
  > "This allows us to test if initial disk properties are the same in high- and low-mass SFRs, and enables a direct measurement of the effect of external photoevaporation on disks." (abstract)
- Target **OMC-2 region of Orion A (132 Spitzer-classified disks, 35 protostars)**: coordinates _not stated_; z/distance 414 pc  
  > "Throughout this paper, we will be using the same distance to the OMCs, of 414 pc (cite: menten07)." (2.1 ALMA data); distance from Menten et al. 2007  
  > "Throughout this paper, we will be using the same distance to the OMCs, of 414 pc (cite: menten07)." (2.1 ALMA data)

## Data provenance

- ALMA projects: 2015.1.00669.S
- bands: Band 3 (3 mm), effective frequency 99.5 GHz  
  > "leading to an effective frequency of 99.5 GHz for the observations discussed here." (2.1 ALMA data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: three 1.8 GHz windows at 93, 104, 108 GHz, line-contaminated ranges removed  
  > "The continuum data span three windows, of $1.8$ GHz each, at 93, 104 and 108 GHz." (2.1 ALMA data)
- arrays: 12-m array, mosaic of two 148-pointing sub-mosaics  
  > "The full image consists of two, 148-pointing sub-mosaics" (2.1 ALMA data)
- configurations: _not stated_
- baselines: 3.5 to 92 kλ  
  > "This was achieved by using baselines between 3.5 and 92 k$\lambda$." (2.2 A point-source map of OMC-2)
- angular resolution: 2.7'' x 1.6'' beam  
  > "which has a $2.7'' \times 1.6''$ beam" (2.2 A point-source map of OMC-2)
- max recoverable scale: ~1' for the unfiltered 12-m data; ~7'' after the 30 kλ cut  
  > "which leads to a largest resolvable scale of around $7''$ or $\sim 3000$ AU at the $414$ pc distance of Orion." (2.2 A point-source map of OMC-2)
- sensitivity: 1 sigma 0.1 mJy/beam in the southern part; 3 sigma dust mass limit 17 Earth masses (32 in the northern part)  
  > "an effective $1\sigma$ noise level of $0.1$ mJy beam$^{-1}$ in the southern (deeper) part of the image." (2.2 A point-source map of OMC-2)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Program of PI A. Hacar, reused  
  > "taken as part of observing program 2015.1.00669.S (PI: A. Hacar)" (2.1 ALMA data)
- Other facility **Spitzer (Megeath et al. 2012 YSO catalog)**: Base catalog of Disks and Protostars used for flux extraction  
  > "the base catalog is the *Spitzer* survey of young stellar objects in the Orion A and B clouds by (cite: megeath12)." (2.3 Spitzer catalog of sources)
- Other facility **VISTA VISION**: Ks-band counterparts for sources  
  > "the Vienna Survey In Orion (VISION) (cite: meingast16) are used to provide context" (3.1.2 Non-Spitzer point sources)
- Other facility **Chandra COUP, Herschel HOPS, ALMA Kainulainen+17**: Counterpart classification of unidentified sources  
  > "the *Chandra* Orion Ultradeep Point Source Catalog (cite: getman05)" (3.1.2 Non-Spitzer point sources)
- External data: Comparison disk dust mass distributions: Lupus, Taurus, Cham I, Upper Sco, sigma Ori, ONC  
  > "In addition to the regions shown here, the same procedure was also followed for disk masses in Taurus (cite: andrews13) and $\sigma$ Ori (cite: ansdell17)." (4 Discussion) [from Ansdell et al. 2016; Eisner et al. 2018; Barenfeld et al. 2016; Andrews et al. 2013; Ansdell et al. 2017]
- External data: Median free-free emission strength and spectral index for correction (0.25 mJy at 3 mm)  
  > "we have applied a correction based on the results presented in (cite: tychoniec18) for the median free-free emission strength and spectral index." (3.3.2 Contamination by free-free contamination at 3 mm) [from (cite: tychoniec18)]
- External data: FRIED grid of externally irradiated disk mass-loss rates  
  > "we have also used the FRIED grid of externally irradiated disks (cite: haworth18)." (4.1 Environmental dependence) [from (cite: haworth18)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0423-0120 (amplitude and bandpass); J0541-0541 phase  
  > "J0423-0120 for amplitude and bandpass; J0541-0541 for phase" (2.1 ALMA data)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA 5.4.0 tclean with mosaic gridder  
  > "we used the CASA version 5.4.0 implementation of the CLEAN algorithm in the `tclean` task" (2.2 A point-source map of OMC-2)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: baselines shorter than 30 kλ removed prior to imaging  
  > "removing all baselines shorter than $30$ k$\lambda$ prior to imaging" (2.2 A point-source map of OMC-2)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: noise weighted by primary beam coverage  
  > "which we take into account throughout the following by weighting the image noise with the primary beam coverage at all points." (2.1 ALMA data)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 2.7'' x 1.6''  
  > "which has a $2.7'' \times 1.6''$ beam" (2.2 A point-source map of OMC-2)
- final rms: 0.1 mJy/beam (southern part)  
  > "an effective $1\sigma$ noise level of $0.1$ mJy beam$^{-1}$ in the southern (deeper) part of the image." (2.2 A point-source map of OMC-2)

### Inherited from earlier work

- Same calibrators, mosaic area and data reduction as the original N2H+ survey  
  > "Our data analysis relies on the same calibrators (J0423-0120 for amplitude and bandpass; J0541-0541 for phase), and covers the same area in a mosaic" (2.1 ALMA data) [from Hacar et al. 2018 (cite: hacar18)]
- Dust mass prescription: beta=1, kappa(1000 GHz)=10 cm2/g, T=20 K, as in comparison surveys  
  > "These are the same values that are used in the articles that present the disk masses to which we compare the OMC-2 sample" (3.2 Disk masses in the OMC-2 field) [from Beckwith et al. 1990; Ansdell et al. 2016; Barenfeld et al. 2016; Eisner et al. 2018]
- Point-source filtering by uv cut  
  > "as done in other studies (cite: felli93; eisner08; eisner18)" (2.2 A point-source map of OMC-2) [from Felli et al. 1993; Eisner et al. 2008, 2018]

### Not stated but needed to reproduce (our reading)

- tclean weighting/robust, cell size, image size, niter, threshold and masks
- Which spectral ranges were excluded as line-contaminated
- Calibration details (CASA version of calibration, pipeline vs manual) and flux scale uncertainty
- peak_local_max parameters (threshold, min distance) for the unidentified source search
- Exact log-rank and Kaplan-Meier implementation, including the mass-scaling fit procedure for the 0.18 ratio
- Dust mass conversion detail: how flux was scaled from 99.5 GHz and the free-free subtraction per source

## Analysis recipe

1. **Make point-source continuum map**: Remove baselines <30 kλ, combine line-free continuum, image with tclean mosaic  
  > "This task’s `mosaic` gridder option leads to the image used in this article" (2.2 A point-source map of OMC-2)
   - software: CASA
   - parameter: uv cut 30 kλ; effective frequency 99.5 GHz  
  > "removing all baselines shorter than $30$ k$\lambda$ prior to imaging" (2.2 A point-source map of OMC-2)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure fluxes at Spitzer YSO positions**: Brightest pixel within 2.5'' of catalog position; 3 sigma detection with primary-beam-weighted noise; visual check  
  > "Fluxes for all sources were measured by searching for the brightest pixel within a $2.5''$ radius of the catalog positions in the ALMA point-source map" (3.1.1 Spitzer-detected sources)
   - fitting: _not stated_
   - validation: Visual check of each position; no detections changed  
  > "a simple visual check was also performed on each position, but no detections were removed or added to the sample as a result." (3.1.1 Spitzer-detected sources)
3. **Find non-Spitzer point sources**: peak_local_max on the image, flux in the same 2.5'' aperture, cross-match with other surveys  
  > "The `peak‘_local‘_max`-function from `scikit-image` was used to identify point sources in the image but not in the *Spitzer* catalog" (3.1.2 Non-Spitzer point sources)
   - software: scikit-image
   - fitting: _not stated_
   - validation: _not stated_
4. **Convert flux to dust mass**: Optically thin blackbody equation with free-free correction of 0.25 mJy  
  > "The effective temperature of the emitting material is taken to be $T_{\text{eff}} = 20$ K" (3.2 Disk masses in the OMC-2 field)
   - parameter: beta=1, kappa_1000GHz=10 cm2/g, T=20 K (30 K test), d=414 pc  
  > "usually, $\beta = 1$ is used and $\kappa_{1000\,\text{GHz}} = 10$ cm$^{2}$ g$^{-1}$ (cite: beckwith90)." (3.2 Disk masses in the OMC-2 field)
   - assumption: Optically thin dust emission  
  > "is assumed to be due to blackbody emission from optically thin dust with an average temperature $T_{\text{eff}}$" (3.2 Disk masses in the OMC-2 field)
   - fitting: _not stated_
   - validation: Tested 30 K temperature, including unidentified sources, removing the brightest disks, with/without free-free  
  > "In Figure [2](#fig:impact), the mass distribution of disks is shown when assuming a higher temperature of 30 K." (3.3.3 The impact of disk temperature and optical depth assumptions)
5. **Disk mass distribution and comparison to other regions**: Kaplan-Meier estimator with upper limits; log-rank tests; log-rank with mass scaling factor vs ONC  
  > "we perform a log-rank test comparing the masses of the ONC population with the masses of the OMC-2 sample multiplied by a constant" (4.1 Environmental dependence)
   - fitting: _not stated_
   - validation: _not stated_
6. **Derive photoevaporation mass-loss rate**: Compare ratio with Scally & Clarke formula and FRIED grid for fiducial disk  
  > "Assuming a typical disk around a solar-mass star in our sample, with a dust mass of 20 $M_{\oplus}$, an outer radius of 40 AU, and a gas-to-dust ratio of 100" (4.1 Environmental dependence)
   - software: FRIED grid
   - assumption: Fiducial disk 20 Earth masses, 40 AU, gas-to-dust 100, 0.5 Myr exposure  
  > "but which has been exposed to FUV radiation for $0.5$ Myr" (4.1 Environmental dependence)
   - fitting: _not stated_
   - validation: Agreement of observed and model rates  
  > "This is a remarkably close correspondence." (4.1 Environmental dependence)

## Software

- **CASA** 5.4.0: tclean imaging of the mosaic  
  > "we used the CASA version 5.4.0 implementation of the CLEAN algorithm in the `tclean` task" (2.2 A point-source map of OMC-2)
- **scikit-image** : peak_local_max source finding  
  > "The `peak‘_local‘_max`-function from `scikit-image` was used to identify point sources" (3.1.2 Non-Spitzer point sources)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Detected disks | 37 of 132 (28%) | not stated | dimensionless | 2 | Of the disks, 37 are detected by our ALMA observations at at least $3\sigma$, for a detection rate of $28\%$. |
| Protostar detection rate | 26 of 35 (69%) | not stated | dimensionless | 2 | 26 detections give a detection rate of $69\%$ for these objects. |
| Unidentified point sources | 34 | not stated | sources | 3 | This sample – the Unidentified point sources – consists of $N=34$ sources. |
| Disk dust mass range | 6.9 to 273 | not stated | Earth masses | 4 | between $273 \pm 9.8\,M_{\oplus}$ and $6.9 \pm 6.4\,M_{\oplus}$ |
| ONC/OMC-2 disk mass ratio | 0.18 | +0.18/-0.11 | dimensionless | 5 | This leads to a mass ratio of $0.18^{+0.18}_{-0.11}$ between the regions |
| Log-rank p-value OMC-2 vs Lupus | 0.87 | not stated | dimensionless | 5 | we cannot distinguish between the Lupus and OMC-2 disks ($p = 0.87$) |
| Log-rank p-value OMC-2 vs Taurus | 0.76 | not stated | dimensionless | 5 | the same is true for the comparison to Taurus ($p = 0.76$) |
| Log-rank p-value OMC-2 vs Cham I | 0.2 | not stated | dimensionless | 5 | Cham I ($p = 0.2$) |
| Photoevaporative mass loss rate | 8e-8 (abstract); 1e-8 from observations vs 8e-8 from Scally & Clarke | not stated | Msun/yr | 6 | our observations imply a photoevaporative mass loss rate of $1 \times 10^{-8}\,M_{\odot}\,\text{yr}^{-1}$ in the ONC. |

## Qualitative findings

- Class II disk masses in OMC-2 are statistically indistinguishable from young low-mass regions; the brightest disks are comparable to the most massive in Lupus/Taurus  
  > "disks in OMC-2 appear to be most similar to young nearby star-forming regions, and may be somewhat more massive." (4.2 Time evolution)

## Claim tuples

- H: Initial disk masses in a massive cloud differ from those in low-mass SFRs | E: Compare Kaplan-Meier disk mass distributions with log-rank tests | R: p=0.87 (Lupus), 0.76 (Taurus), 0.2 (Cham I) | F: Age, not cloud environment, dominates disk evolution outside the Trapezium region | **supported**
- H: External photoevaporation reduces disk mass near the Trapezium | E: Scale the OMC-2 masses to match the ONC distribution with a log-rank test | R: mass ratio 0.18 (+0.18/-0.11) | F: Consistent with FUV-driven mass loss | **supported**
- H: Results are robust against assumptions and biases | E: Vary T to 30 K, add unidentified sources, free-free correction, remove brightest disks | R: Effects small compared to Kaplan-Meier errors | F: Conclusions robust | **supported**

## Reasoning

- Why this data: Mosaic covers a large area beyond 0.5 pc from the Trapezium  
  > "these observations cover a large area containing the population of interest for this study, which is located beyond 0.5 pc from the Trapezium." (1 Introduction)
- Why this method: Same mass prescription and statistics as comparison surveys for a consistent comparison  
  > "in order to compare our sample as fairly as possible to those results" (3.3.3 The impact of disk temperature and optical depth assumptions)
- Alternative: Imaging the full 12-m data was rejected because of resolved-out cloud contamination  
  > "imaging and analysing the continuum from the ALMA 12-m array data products directly is not suitable for our purposes" (2.2 A point-source map of OMC-2)
- How they decided it was enough: _not stated_
- Limitation (authors): Spitzer catalog is incomplete, so low-mass disks may be underrepresented  
  > "However, this catalog is not complete" (2.3 Spitzer catalog of sources)
- Limitation (authors): Dust masses assume optically thin emission and a fixed temperature; the D31 binary is variable  
  > "While this would mean our ‘dust mass’ is incorrect" (3.3.3 The impact of disk temperature and optical depth assumptions)
- Caveat (inferred, ours): Disk temperature in Orion may differ from the 20 K assumption, affecting the absolute mass ratio and mass loss rate
- Caveat (inferred, ours): The mass-loss rate depends on the assumed fiducial disk and exposure time
- Caveat (inferred, ours): Class I contamination and the nature of unidentified sources are uncertain
- Caveat (inferred, ours): Free-free correction is a single median value applied to all sources

## Reproducibility

- Data public (paper): Reduced data available at the ORION-4D website; ALMA program cited  
  > "The reduced data for this project are available online, at the ORION-4D project website" (footnote)
- Products in archive: _not stated_
- Missing: Imaging parameters (weighting, cell, size, masks, threshold)
- Missing: peak_local_max settings
- Missing: Exact line-contaminated channel ranges
- Missing: Log-rank scaling implementation
- Data volume (inferred): Large mosaic, likely tens to hundreds of GB raw; imaging a single continuum cube is moderate
- Score (inferred): 3/5, Public data and a clear simple method, but imaging parameters and the statistical procedure are missing.
- Rediscovery candidate: yes, Public data, simple flux extraction and mass conversion with numeric results; imaging details need choices.

## Links

- Method: Hacar et al. 2018 (cite: hacar18) (Original data description and reduction)
- Method: Ansdell et al. 2016 (cite: ansdell16) (Disk mass method and Lupus comparison sample)
- Companion: Eisner et al. 2018 (cite: eisner18) (ONC disk sample used for comparison)
- Related: Megeath et al. 2012 Spitzer Orion YSO survey
- Related: VISION
- Related: COUP
- Related: Herschel Orion Protostar Survey

## Checks

```json
{
 "quotes": 62,
 "quotes_ok": 62,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 48,
  "rate": 0.6
 },
 "evidence_ok": true
}
```
