# Influence of Mid-infrared Galactic Bubble on Surroundings: A Case Study on IRAS 16489-4431

`2024BSRSL..93..601H` | Bulletin de la Societe Royale des Sciences de Liege 2024 | first author: Hoque, Ariful | arXiv: 2405.17993 | DOI: 10.25518/0037-9565.11811

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation, milky_way_ism
- Question: What is the influence of a massive star on a mid-infrared bubble and its surrounding gas in IRAS 16489-4431?  
  > "We studied the influence of a massive star on a mid-infrared bubble and its surrounding gas in the IRAS 16489-4431 star-forming region using multi-wavelength data." (abstract)
- Target **IRAS 16489-4431**: coordinates RA 253.15107 deg, Dec -44.60557 deg (bubble centre)  
  > "The region is located at a near-kinematic distance of 3.26 kpc (cite: urquhart2018)." (Introduction); "IRAS 16489-4431 region contain a bubble at RA: 253.15107$^\circ$, Dec: -44.60557$^\circ$ having an angular radius of 0.2$'$ (cite: jayasinghe2019)." (3.3 Shocked Bubble); z/distance 3.26 kpc  
  > "The region is located at a near-kinematic distance of 3.26 kpc (cite: urquhart2018)." (Introduction); "IRAS 16489-4431 region contain a bubble at RA: 253.15107$^\circ$, Dec: -44.60557$^\circ$ having an angular radius of 0.2$'$ (cite: jayasinghe2019)." (3.3 Shocked Bubble); distance from near-kinematic distance, Urquhart et al. 2018  
  > "The region is located at a near-kinematic distance of 3.26 kpc (cite: urquhart2018)." (Introduction); "IRAS 16489-4431 region contain a bubble at RA: 253.15107$^\circ$, Dec: -44.60557$^\circ$ having an angular radius of 0.2$'$ (cite: jayasinghe2019)." (3.3 Shocked Bubble)

## Data provenance

- ALMA projects: 2019.1.00685.S, 2017.1.00545.S
- bands: Band 3 (3 mm)  
  > "The region was observed on 3 November 2019 with ALMA 12-m array in band 3." (Data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12-m array  
  > "The region was observed on 3 November 2019 with ALMA 12-m array in band 3." (Data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~2'' x 2'' beam  
  > "we used 3 mm continuum and H$^{13}$CO$^{+}$ data with a beam size of $\sim2''\times 2''$" (Data)
- max recoverable scale: _not stated_
- sensitivity: rms 0.2 mJy/beam (continuum), 6.4 mJy/beam per 0.122 MHz channel (H13CO+)  
  > "having rms noise of 0.2 mJy beam$^{-1}$ and 6.4 mJy beam$^{-1}$ per 0.122 MHz channel, respectively." (Data)
- time on source: _not stated_
- observing dates: 3 November 2019  
  > "The region was observed on 3 November 2019 with ALMA 12-m array in band 3." (Data)
- pi or archival as stated: ATOMS survey, PI Tie Liu  
  > "ALMA data from ATOMS survey (Project ID: 2019.1.00685.S; PI: Tie Liu) are used in this study." (Data)
- Line: H13CO+ not stated (not stated)
- Other facility **Spitzer GLIMPSE/MIPSGAL**: IRAC and 24 um images for ratio map, YSO identification and SED  
  > "*Spitzer Space Telescope* Galactic Legacy Infrared Mid-Plane Survey Extraordinaire (cite: benjamin2003), Multiband Infrared Photometer for *Spitzer* (cite: carey2005)" (Data)
- Other facility **2MASS and WISE**: Archival near/mid-IR photometry  
  > "Two Micron All Sky Survey (cite: skrutskie2006)" (Data)
- Other facility **Herschel**: Dust temperature map (PPMAP)  
  > "we examined the *Herschel* dust temperature map (cite: marsh2017)." (4.1 Cores)
- External data: Herschel PPMAP dust temperature map (~12'' resolution)  
  > "The final resolution of the temperature map is $\sim$12$''$." (4.1 Cores) [from (cite: marsh2017)]
- External data: Bubble identification and position/radius  
  > "having an angular radius of 0.2$'$ (cite: jayasinghe2019)" (3.3 Shocked Bubble) [from (cite: jayasinghe2019)]
- External data: Bolometric luminosities 2690 and 3900 Lsun  
  > "The corresponding bolometric luminosities of 2690 and 3900 L$_\odot$ are adopted from (cite: lang1999)." (3.3 Shocked Bubble) [from (cite: lang1999)]
- External data: Wind velocity ~700 km/s and mass-loss rate ~10^-9.4 Msun/yr for B1V star  
  > "$V\sim$700 km s$^{-1}$ and $\dot{\mathrm{M}}$ of $\sim$10$^{-9.4}$ M$_\odot$ yr$^{-1}$ for a typical B1V star were obtained from (cite: oskinova2011)." (3.3 Shocked Bubble) [from (cite: oskinova2011)]

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

- ALMA observation details and data reduction  
  > "More details of the ALMA observations and data reduction can be found in (cite: liu2020)." (Data) [from (cite: liu2020)]
- Pressure components computation method  
  > "we computed different pressure components following the similar method outlined in (cite: baug2019)." (3.3 Shocked Bubble) [from (cite: baug2019)]

### Not stated but needed to reproduce (our reading)

- Calibration, CASA version and imaging parameters (robust, cleaning) of the ATOMS data
- dendrogram min_value/min_delta settings
- imfit regions and procedure
- H13CO+ moment/integration velocity range and rest frequency
- how project 2017.1.00545.S was used (outflow data not described)
- SED-fit input fluxes beyond Table 2 (Spitzer/Herschel) and error handling

## Analysis recipe

1. **identify dust cores**: Dendrogram on ALMA 3 mm continuum; leaves with area >33 pixels and S/N>5 are cores; parameters refined with CASA imfit  
  > "We considered only those leaves (structures with no sub-structures) as cores that have area more than 33 pixels (i.e., size of the beam in pixel) in ALMA 3 mm dust continuum image and have signal-to-noise ratio of more than 5." (4.1 Cores)
   - software: astrodendro, CASA imfit
   - fitting: _not stated_
   - validation: _not stated_
2. **estimate core masses**: Optically thin dust mass equation of Hildebrand 1983  
  > "With the assumption that dust emission is optically thin, the masses of the four identified cores are estimated using the equation from (cite: hildebrand1983)" (4.1 Cores)
   - parameter: Tdust = 21 K, beta = 1.5 and 2.0  
  > "The mass of the cores were estimated for two $\beta$ values of 1.5 and 2.0" (4.1 Cores)
   - assumption: gas-to-dust ratio 100; kappa = 10 (nu/1.2 THz)^beta; distance 3.26 kpc  
  > "R$_{\mathrm{gd}}$ is gas-to-dust ratio (adopted as 100)" (4.1 Cores)
   - fitting: _not stated_
   - validation: _not stated_
3. **fit SED of the influencing source to get mass**: Robitaille et al. 2007 SED fitter with distance 3.0-3.6 kpc and Av 3-30; models with chi2-chi2best<=3 used  
  > "the models satisfying $\chi^2-\chi^2_\mathrm{best} \leq3$ were only considered in computing the mass of the source." (3.3 Shocked Bubble)
   - software: SED-fitter (Robitaille 2007)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **astrodendro** : core identification  
  > "using the Python-based astrodendro package (cite: rosolowsky2008)" (4.1 Cores)
- **CASA imfit** : refine core parameters  
  > "further refined their parameters using the CASA-imfit task" (4.1 Cores)
- **astropy** : used in the research  
  > "This research makes use of astropy, a community-developed core python package for Astronomy" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mass of core C3 (beta=1.5, T=21 K) | 48.3 | 2.2 | Msun | 2 | C3 \[253.1381;-44.6038\] / 1.4$''\times$0.8$''$ / 13.2$\pm$0.9  / 8.7$\pm$0.4           / 48.3$\pm$2.2 |
| Mass of influencing star | 7.9 | 0.7 | Msun | 3 | The estimated mass of 7.9$\pm$0.7 M$_{\odot}$ is referring to a B2-B1 type star. |
| Number of YSOs | 8 Class I and 5 Class II | not stated | count | 0 | We found a total of 8 Class I and 5 Class II sources within the targeted regions. |

## Qualitative findings

- Radiation pressure dominates over stellar wind pressure  
  > "shows that the radiation pressure dominates over stellar pressure" (3.3 Shocked Bubble)

## Claim tuples

- H: A massive star drives the MIR bubble and influences star formation at its edge | E: Multiwavelength analysis: IRAC ratio map, SED fitting, pressure estimates, ALMA cores and H13CO+ | R: 7.9 Msun star with radiation pressure dominant; four cores and YSOs at the periphery | F: Radiation pressure from the star triggered the bubble and might have influenced star formation around its periphery | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Caveat (inferred, ours): Triggering is not demonstrated; spatial coincidence only
- Caveat (inferred, ours): Single-temperature 21 K from 12'' map applied to 2'' cores
- Caveat (inferred, ours): Outflow claim is not backed by shown analysis
- Caveat (inferred, ours): Mass depends strongly on beta
- Caveat (inferred, ours): Stellar parameters for wind are generic B1V values

## Reproducibility

- Data public (paper): ATOMS survey data cited with project ID  
  > "ALMA data from ATOMS survey (Project ID: 2019.1.00685.S; PI: Tie Liu) are used in this study." (Data)
- Products in archive: _not stated_
- Missing: ATOMS calibration/imaging details (only via Liu 2020)
- Missing: dendrogram parameters
- Missing: SED fitter inputs
- Data volume (inferred): ~10-50 GB for the ATOMS band 3 data
- Score (inferred): 3/5, Simple analysis with public data and a few stated parameters, but imaging details are deferred to another paper.
- Rediscovery candidate: yes, Public data and core identification and mass estimates are numeric and fairly simple, though imaging settings are deferred.

## Links

- Method: (cite: liu2020) (ATOMS observations and data reduction)
- Method: (cite: baug2019) (pressure calculation method)
- Related: ATOMS
- Related: CORNISH-South

## Checks

```json
{
 "quotes": 40,
 "quotes_ok": 40,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 67,
  "stated": 29,
  "rate": 0.433
 },
 "evidence_ok": true
}
```
