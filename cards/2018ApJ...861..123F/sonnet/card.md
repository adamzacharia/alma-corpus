# Why Post-starburst Galaxies Are Now Quiescent

`2018ApJ...861..123F` | The Astrophysical Journal 2018 | first author: French, K. Decker | arXiv: 1805.12132 | DOI: 10.3847/1538-4357/aac8de

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation
- Question: Do CO-luminous but quiescent post-starburst galaxies contain dense gas (HCN, HCO+), and does a lack of dense gas explain their low star formation rates?  
  > "These observations raise the question of why these galaxies have such low star formation rates." (abstract)
- Target **H02**: coordinates RA 141.580383 deg, Dec 18.678055 deg (J2000)  
  > "| H02 | 141.580383 | 18.678055 | 0.0541 |" (Table 1); z/distance z = 0.0541  
  > "| H02 | 141.580383 | 18.678055 | 0.0541 |" (Table 1); distance from _not stated_
- Target **S05**: coordinates RA 146.112335 deg, Dec 4.499120 deg (J2000)  
  > "| S05 | 146.112335 | 4.499120 | 0.0467 |" (Table 1); z/distance z = 0.0467  
  > "| S05 | 146.112335 | 4.499120 | 0.0467 |" (Table 1); distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.00881.S, 2015.1.00665.S
- bands: Band 3 (84-116 GHz), two spectral windows  
  > "We use the Band 3 receiver (84-116 GHz) with two spectral windows to observe HCN 1–0 (88.63 GHz rest frame)" (2.1 ALMA Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12m array; 43 antennas for H02, 41-46 for S05  
  > "The 12m array was used for both datasets, using 43 antennas for H02 and 41-46 antennas for S05." (2.1 ALMA Observations)
- configurations: C40-5 (H02), C40-4 (S05)  
  > "The observations were carried out in configurations C40-5 and C40-4 for H02 and S05, respectively." (2.1 ALMA Observations)
- baselines: _not stated_
- angular resolution: beam 1-1.5 arcsec (1.0-1.4 kpc)  
  > "have a beam size of 1-1.5$''$ (or 1.0-1.4 kpc)" (2.1 ALMA Observations)
- max recoverable scale: 7.6 arcsec  
  > "with a maximum recoverable scale of 7.6$''$" (2.1 ALMA Observations)
- sensitivity: H02 HCN 5.5 mJy/beam, HCO+ 2.7 mJy/beam; S05 570 uJy/beam both  
  > "a sensitivity of 5.5 mJy/beam at a spectral resolution of 0.252 km/s" (2.1 ALMA Observations)
- time on source: _not stated_
- observing dates: H02: 4 Nov 2016; S05: 22 and 25 Nov 2016, 4 May 2017  
  > "The observations of H02 were executed in one block on November 4, 2016." (2.1 ALMA Observations)
- pi or archival as stated: Own Cycle 4 program, PI French  
  > "(program 2016.1.00881.S; PI: French)" (2.1 ALMA Observations)
- Line: HCN 1-0 (88.63 GHz)
- Line: HCO+ 1-0 (89.19 GHz)
- Line: HNC 1-0 (90.66 GHz)
- Other facility **IRAM 30m**: CO (1-0) line widths and unresolved CO (2-1) fluxes  
  > "We integrate over the velocity width of the CO (1–0) lines as measured using the IRAM 30m" (3 Results)
- Other facility **VLA FIRST**: 1.4 GHz upper limits for SFRs  
  > "We use the VLA FIRST Survey (cite: Becker1995) to study the 1.4 GHz radio continuum emission as a SFR tracer." (2.2 Star Formation Rates)
- External data: CO (1-0) luminosities and CO linewidths of H02 and S05  
  > "$^{a}$ (cite: French2015)" (Table 1) [from (cite: French2015)]
- External data: TIR, [CII] and [NeII]+[NeIII] SFRs and dust masses  
  > "S05 has a TIR SFR consistent with the other measures from the optical and radio, at 0.71 M$_\ensuremath{\odot}$yr$^{-1}$" (2.2 Star Formation Rates) [from (cite: Smercina2018)]
- External data: HCN and CO comparison samples of star-forming and early-type galaxies  
  > "comparison samples of star-forming and early type galaxies with both HCN and CO measurements (cite: Gao2004; Crocker2012)" (3 Results) [from (cite: Gao2004; Crocker2012)]
- External data: HCO+ comparison sample  
  > "The comparison samples of star-forming and starbursting galaxies are from (cite: Gracia2008)" (3 Results) [from (cite: Gracia2008)]
- External data: Early-type SFRs  
  > "For the early type galaxies, SFRs are from (cite: Davis2014)" (3 Results) [from (cite: Davis2014)]

## Processing

### Calibration

- pipeline or manual: pipeline-calibrated  
  > "The data were pipeline-calibrated using CASA version 4.7.2." (2.1 ALMA Observations)
- casa version: CASA 4.7.2  
  > "The data were pipeline-calibrated using CASA version 4.7.2." (2.1 ALMA Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: 5 arcsec taper as a robustness test  
  > "First, we taper the data to 5$''$, but still do not detect either galaxy in HCN (1–0)." (2.1 ALMA Observations)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: H02 HCN 1.0x0.73 arcsec, HCO+ 1.1x0.72; S05 HCN 1.4x1.2, HCO+ 1.3x1.2  
  > "The S05 observations of HCN (1–0) have a final beamsize of 1.4$''$$\times$1.2$''$" (2.1 ALMA Observations)
- final rms: _not stated_

### Inherited from earlier work

- CO linewidths (172 km/s H02, 350 km/s S05) used for upper-limit integration  
  > "we assume the same linewidths as the CO observations: 172 km/s for H02 and 350 km/s for S05." (2.1 ALMA Observations) [from (cite: French2015)]
- Matched filter technique for robustness check  
  > "we use a matched filter technique (cite: Loomis2018) using the prior information from the CO observations" (2.1 ALMA Observations) [from (cite: Loomis2018)]
- DESPOTIC GMC and ULIRG conditions  
  > "for the typical Milky Way GMC and ULIRG conditions described by (cite: Krumholz2013)" (4.3 Variations in luminosity to mass conversion) [from (cite: Krumholz2013)]

### Not stated but needed to reproduce (our reading)

- Imaging task, weighting/robust, cell and image size, and cleaning parameters
- Continuum subtraction and line-free channels
- How the 3 sigma upper limits and noise were computed (channel width, integration window)
- Luminosity distance/cosmology adopted
- Monte Carlo procedure details (sample selection, draws, definition of 'as low as')
- DESPOTIC input parameters
- Self-calibration and flux calibrator details

## Analysis recipe

1. **Image cubes and check for HCN/HCO+ detections**: Pipeline-calibrated data imaged; no lines detected; tests with 5 arcsec taper and matched filter  
  > "Second, we use a matched filter technique (cite: Loomis2018) using the prior information from the CO observations, but do not find any significant detections just below our sensitivity limit." (2.1 ALMA Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Taper to 5 arcsec and matched filter  
  > "We test the robustness of these upper limits in several ways." (2.1 ALMA Observations)
2. **Compute 3 sigma line luminosity upper limits**: L' = 3.25e7 (1+z)^-3 nu_obs^-2 S dv D_L^2 integrated over CO (1-0) linewidth  
  > "L^{\prime}_{line} = 3.25\times10^7 (1+z)^{-3} \ \nu_{\rm obs}^{-2} \ S_{line} \Delta v \ D_L^2" (3 Results)
   - parameter: Linewidths 172 km/s (H02), 350 km/s (S05)  
  > "172 km/s for H02 and 350 km/s for S05" (2.1 ALMA Observations)
   - fitting: _not stated_
   - validation: _not stated_
3. **Adopt SFRs**: Compare SFRs from Halpha, Dn4000, FIRST 1.4 GHz and infrared tracers; adopt SFR <1 Msun/yr for H02  
  > "we adopt a conservative upper limit of $<1$ M$_\ensuremath{\odot}$yr$^{-1}$ on the SFR of H02" (2.2 Star Formation Rates)
   - fitting: _not stated_
   - validation: _not stated_
4. **Compare with L'-SFR relations and HCN/CO ratios of comparison samples**: Monte-Carlo drawing pairs of galaxies from comparison samples to assess probability of ratios as low as post-starbursts  
  > "We perform a Monte-Carlo analysis, drawing pairs of galaxies at random from these comparison samples" (3 Results)
   - assumption: Early-type conversion from main beam temperature to flux density 4.73 Jy/K  
  > "we use the conversion factor from main beam temperature to flux density of 4.73 Jy/K from (cite: Young2011)" (3 Results)
   - fitting: _not stated_
   - validation: _not stated_
5. **Test conversion factor variations**: DESPOTIC models of alpha_CO and alpha_HCN for MW GMC and ULIRG conditions  
  > "ULIRG conditions result in $\alpha_{\rm CO}$ values $\sim5\times$ lower than in Milky Way GMC conditions, as expected." (4.3 Variations in luminosity to mass conversion)
   - software: DESPOTIC
   - assumption: Same HCN-to-dense gas conversion for post-starbursts and other galaxies  
  > "We assume that the conversion factor from $L^{\prime}($HCN$)$ to dense molecular gas mass is the same for post-starbursts and other galaxies." (4.3 Variations in luminosity to mass conversion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.2: pipeline calibration  
  > "The data were pipeline-calibrated using CASA version 4.7.2." (2.1 ALMA Observations)
- **DESPOTIC** : modeling alpha_CO and alpha_HCN  
  > "We test this possibility using `DESPOTIC` (cite: Krumholz2013)" (4.3 Variations in luminosity to mass conversion)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| L'(HCN) upper limit H02 | <29.3e6 | 3 sigma limit | K km/s pc^2 | 2 | $<           29.3$ |
| L'(HCN) upper limit S05 | <8.9e6 | 3 sigma limit | K km/s pc^2 | 2 | $<            8.9$ |
| L'(HCO+) upper limit H02 | <28.1e6 | 3 sigma limit | K km/s pc^2 | 2 | $<           28.1$ |
| L'(HCO+) upper limit S05 | <8.8e6 | 3 sigma limit | K km/s pc^2 | 2 | $<            8.8$ |
| Probability two galaxies from combined comparison sample have HCN/CO as low as post-starbursts | 5% | not stated | percent | 4 | the probability of finding two galaxies with HCN/CO as low as the post-starbursts is 5% |
| Same probability, early-type sample only | 16% | not stated | percent | 4 | we find that two galaxies have HCN/CO luminosity ratios as low as the two post-starbursts 16% of the time |
| Same probability, normal star-forming sample | 2% | not stated | percent | 4 | we find two galaxies with HCN/CO as low as the post-starbursts only 2% of the time |
| alpha_CO ULIRG vs MW GMC ratio from DESPOTIC | ~5x lower (alpha_HCN lowered by same factor) | not stated | dimensionless | 5 | However, $\alpha_{\rm HCN}$ is lowered by the same factor. |

## Qualitative findings

- Neither HCN nor HCO+ is detected, and the upper limits are consistent with the low SFRs and with early-type galaxies  
  > "The upper limits are consistent with the low star formation rates and with early-type galaxies." (abstract)

## Claim tuples

- H: Do post-starbursts lack dense gas? | E: ALMA Band 3 HCN and HCO+ (1-0) observations of two CO-luminous post-starbursts | R: No detection of either line; low upper limits | F: Low dense gas fraction explains low SFRs | **supported**
- H: Is the HCN/CO ratio unusually low relative to other galaxy types? | E: Monte-Carlo comparison with starburst, star-forming and early-type samples | R: Probabilities 5% (all), 2% (star-forming), 16% (early-type) | F: Low relative to star-forming and starbursts; not distinguishable from early types | **partially**
- H: Could conversion factor changes make the dense gas fraction normal? | E: DESPOTIC models | R: alpha_CO and alpha_HCN both decrease by ~5x for ULIRG conditions | F: Low HCN/CO likely reflects low dense gas mass ratios | **supported**

## Reasoning

- Why this data: Beam size chosen to match CO (2-1) sizes  
  > "The beam size is chosen to match the observed CO (2–1) sizes" (2.1 ALMA Observations)
- Why this method: _not stated_
- Alternative: Unaccounted dust extinction, bottom-heavy IMF, and missed star formation in aperture corrections disfavored  
  > "The observed discrepancy is not likely driven by un-accounted for dust extinction or significant low-mass star formation" (3 Results)
- How they decided it was enough: _not stated_
- Limitation (authors): H02 SFR uncertain (0.09-1 Msun/yr) across tracers  
  > "the SFR for H02 is uncertain, with various tracers estimating $\sim 0.09-1$ M$_\ensuremath{\odot}$yr$^{-1}$" (3 Results)
- Caveat (inferred, ours): Only two galaxies, non-detections only
- Caveat (inferred, ours): H02 upper limits are weak relative to comparison samples
- Caveat (inferred, ours): Mechanism for suppressed collapse is speculative

## Reproducibility

- Data public (paper): ALMA program cited; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00881.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: Noise/upper limit procedure
- Missing: Monte Carlo details
- Missing: Cosmology
- Data volume (inferred): ~10-50 GB raw for two Band 3 datasets
- Score (inferred): 3/5, Simple non-detection analysis and archive data, but imaging and Monte Carlo details are missing.
- Rediscovery candidate: yes, Public ALMA data, simple recipe, numeric upper limits, though imaging details need to be inferred.

## Links

- Method: (cite: Loomis2018) (matched filter technique)
- Method: (cite: Krumholz2013) (DESPOTIC)
- Companion: (cite: French2015) (CO-detected post-starburst sample)
- Companion: (cite: Smercina2018) (infrared SFR and dust analysis)
- Related: ALMA 2015.1.00665.S (PI Smith)
- Related: Atlas-3D

## Checks

```json
{
 "quotes": 60,
 "quotes_ok": 60,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2015.1.00665.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 79,
  "stated": 43,
  "rate": 0.544
 },
 "evidence_ok": true
}
```
