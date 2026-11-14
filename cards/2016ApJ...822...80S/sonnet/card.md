# The Redshift Distribution of Dusty Star-forming Galaxies from the SPT Survey

`2016ApJ...822...80S` | The Astrophysical Journal 2016 | first author: Strandet, M. L. | arXiv: 1603.05094 | DOI: 10.3847/0004-637X/822/2/80

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: high_z_galaxies
- Question: What is the redshift distribution of 1.4 mm-selected SPT dusty star-forming galaxies, and how do lensing and selection wavelength affect it?  
  > "We discuss how the selection of our sources affects the redshift distribution, focusing on source brightness, selection wavelength, and strong gravitational lensing." (abstract)
- Target **SPT-selected DSFGs (15 in 3 mm scans, 8 in 1 mm follow-up; e.g. SPT0002-52, SPT2349-56)**: coordinates given per source in Table 1, e.g. SPT0002-52 00:02:23.24 -52:31:52.5  
  > "SPT–S J000223-5232.1     | 00:02:23.24              | -52:31:52.5" (Table 1); z/distance z = 1.867 to 5.811 (39 sources)  
  > "SPT–S J000223-5232.1     | 00:02:23.24              | -52:31:52.5" (Table 1); distance from CO/[CI] line detections (ALMA 3 mm/1 mm, APEX, Z-Spec) plus photometry for single-line cases  
  > "SPT–S J000223-5232.1     | 00:02:23.24              | -52:31:52.5" (Table 1)

## Data provenance

- ALMA projects: 2012.1.00844.S, 2012.1.00994.S, 2011.0.00957.S, 2011.0.00958.S
- bands: Band 3 (3 mm) scans; Band 6 (1 mm) follow-up  
  > "to search for a second CO line (CO(6–5) – CO(12–11)) or a [N] line in ALMA band 6 (211 GHz - 275 GHz)" (2.1 ALMA 1 mm follow up observations)
- frequencies and spectral setup: Band 3: five tunings covering 84.2-114.9 GHz, two 3.75 GHz sidebands each  
  > "This setup spans $84.2$$-$$114.9$ GHz, where the range $96.1$$-$$103.0$ GHz is covered twice." (2.2 ALMA 3 mm scans)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: Cycle 1 early science compact array configuration  
  > "The Cycle 1 ALMA 3 mm spectral scans were carried out in 2013 July and 2013 December in the Cycle 1 early science compact array configuration." (2.2 ALMA 3 mm scans)
- baselines: _not stated_
- angular resolution: Band 3 beams 3.7x2.4 to 3.0x1.8 arcsec; Band 6 1.5x0.8 arcsec  
  > "typical synthesized beams of $3.7''\times2.4''$ to $3.0''\times1.8''$ from the low to high-frequency ends of the band" (2.2 ALMA 3 mm scans)
- max recoverable scale: _not stated_
- sensitivity: Band 3 channel noise 1.5-2 mJy/beam (19.5 MHz); continuum 50 uJy/beam. Band 6 channel noise 0.9-1.9 mJy/beam  
  > "The typical noise per channel is 1.5–2 mJy beam$^{-1}$." (2.2 ALMA 3 mm scans)
- time on source: Band 3: 120 s per tuning, ~10 min per source; Band 6: 8-20 min per science block  
  > "The sources were observed for 120 seconds each, in each tuning, which amounts to roughly 10 minutes per source in total." (2.2 ALMA 3 mm scans)
- observing dates: Band 3: 2013 July and December; Band 6: 2013 December to 2014 December  
  > "The observations were carried out from 2013 December to 2014 December." (2.1 ALMA 1 mm follow up observations)
- pi or archival as stated: _not stated_
- Line: CO CO(1-0) to CO(7-6) in Band 3; CO(6-5)-CO(12-11) in Band 6 (not stated)
- Line: [CII] 158 um (APEX/FLASH follow-up) (not stated)
- Other facility **APEX (FLASH, SEPIA, Z-Spec, LABOCA)**: [CII] and CO mid-J redshift confirmation; 870 um photometry  
  > "We further present APEX [C] and CO mid-$J$ observations for seven sources" (abstract)
- Other facility **Herschel SPIRE/PACS**: 100-500 um photometry for SED fits  
  > "The *Herschel*/SPIRE maps at 250 $\mu$m, 350 $\mu$m and 500 $\mu$m were observed in two observing programs" (2.6 Photometry)
- Other facility **SPT**: 1.4 and 2.0 mm selection and photometry  
  > "The SPT 1.4 mm and 2.0 mm flux densities were extracted and deboosted as described by (cite: mocanu13)." (2.6 Photometry)
- Other facility **ATCA**: low-J CO follow-up  
  > "we carried out follow-up observations with Australia Telescope Compact Array (ATCA) targeting low-$J$ CO transitions" (2.7 Ancillary spectroscopic observations)
- Other facility **VLT/X-shooter**: optical spectrum of SPT2357-51  
  > "Optical spectroscopy was performed for SPT2357-51 on the night of 2013 October 16 with the X-shooter echelon spectrograph" (2.7 Ancillary spectroscopic observations)
- External data: Cycle 0 ALMA 3 mm redshift sample of 26 SPT DSFGs  
  > "In this paper we extend the ALMA redshift survey of 26 SPT-selected sources from (cite: weiss13) with an additional 15 sources." (1 Introduction) [from (cite: weiss13)]
- External data: Lensing probability model vs. redshift  
  > "Figure [8](#Fig:lens-prob), based on the model presented in (cite: hezaveh11), shows the probability of a source undergoing strong gravitational lensing" (4.2.1 Lensing effects) [from (cite: hezaveh11)]
- External data: Model redshift distributions (lensed and unlensed)  
  > "we compare our lensed and lensing-corrected redshift distributions to a lensed and unlensed model population from (cite: bethermin15)" (4.2.1 Lensing effects) [from (cite: bethermin15)]
- External data: Comparison redshift distributions of 1.1 mm and 870 um selected DSFGs  
  > "The final sample consists of 30 sources selected at 1.1 mm with a mix of photometric and spectroscopic redshifts" (4.2.2 Selection wavelength) [from (cite: miettinen15); (cite: simpson14)]
- External data: CO line luminosity ratios from SPT-DSFG stacked spectrum  
  > "Using the stacked spectrum of the SPT-DSFGs (cite: spilker14) we calculate the line luminosity ratio" (3.3.3) [from (cite: spilker14)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Band 3: Uranus or Mars; Band 6: Uranus, Neptune, Ganymede, quasars J0334-401, J0519-454  
  > "Flux calibration was performed on Uranus or Mars and passband and phase calibration were determined from nearby quasars." (2.2 ALMA 3 mm scans)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA used for processing; cubes with 19.5 MHz channels  
  > "We used the CASA package to process the data." (2.2 ALMA 3 mm scans)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "The cubes were created using natural weighting to optimize the sensitivity" (2.2 ALMA 3 mm scans)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: 1 mm spectra smoothed in Figure 3 for visualization  
  > "All 1 mm spectra are shown in Figure [3](#Fig:spectra_cy1) (smoothed to lower velocity resolution for better visualization of the lines)." (3.1 Targeted ALMA 1 mm observations)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Photometric-redshift line identification method  
  > "We do this as in (cite: weiss13); the method is briefly described here." (3.3.3) [from (cite: weiss13)]
- SED fitting method  
  > "To fit the SEDs we use the method described in (cite: greve12)" (3.3.3) [from (cite: greve12)]
- APEX/FLASH observing and reduction  
  > "The observations were performed and the data processed in the same manner as described in (cite: gullberg15)." (2.3 APEX/FLASH [C] follow-up) [from (cite: gullberg15)]
- Z-Spec reduction  
  > "The reduction of the data was done in the same manner as described in (cite: bothwell13)." (2.5 APEX/Z-Spec spectrum) [from (cite: bothwell13)]
- SPT flux extraction and deboosting  
  > "The SPT 1.4 mm and 2.0 mm flux densities were extracted and deboosted as described by (cite: mocanu13)." (2.6 Photometry) [from (cite: mocanu13)]

### Not stated but needed to reproduce (our reading)

- CASA version and whether pipeline or manual calibration
- clean threshold, mask, cell and image size
- how spectra were extracted (aperture) and line fitting procedure
- line detection significance criteria
- exact SED model details (opacity treatment) beyond beta=2 and 100 um
- how the lensing-corrected distribution was binned and errors propagated
- 870 um ALMA data details (project/processing) used for absorption lines

## Analysis recipe

1. **Extract continuum and spectra**: Cleaned natural-weighted cubes (19.5 MHz channels) and continuum from full bandwidth; spectra extracted at 3 mm continuum positions; 3 mm flux as peak of point sources  
  > "The ALMA 3 mm flux densities were extracted as the peak flux density of the point sources on the cleaned continuum map" (2.6 Photometry)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Identify lines and redshifts**: Identify CO/[CI] lines; multi-line gives unambiguous redshift; single lines resolved with photometric redshift and follow-up (ALMA 1 mm, APEX)  
  > "Four sources show two or more lines, yielding an unambiguous redshift from the 3 mm data alone" (3.3.2)
   - assumption: single line assumed to be CO  
  > "We work under the assumption that the line is from a transition in CO." (3.3.3)
   - fitting: _not stated_
   - validation: Second-line confirmation; single-line prediction correct for 12 of 15 sources (80%)  
  > "In a sample of 15 sources with a single line in their ALMA spectrum we correctly predict the redshift for 12 sources ($80$% success rate)." (3.3.3)
3. **Fit dust SEDs and photometric redshifts**: Modified blackbody fits; sample 10^3 temperatures from the Tdust distribution of unambiguous-redshift sources; peak of the probability distribution is z_phot  
  > "we create a photometric redshift probability distribution by randomly sampling $10^3$ temperatures from the $T_{\rm dust}$ distribution" (3.3.3)
   - parameter: beta=2, optically thin/thick transition at 100 um, CMB included, ignore data shortward of rest-frame 50 um; free: Tdust and dust mass  
  > "with a spectral slope of $\beta$=2, the optically thin/thick transition wavelength of 100 $\mu$m, and taking the cosmic microwave background (CMB) into account" (3.3.3)
   - assumption: calibration uncertainty added: 7% PACS, 10% others  
  > "we have added in quadrature an absolute calibration uncertainty of 7% for *Herschel*/PACS and 10% for all other wavelengths." (2.6 Photometry)
   - fitting: _not stated_
   - validation: _not stated_
4. **Build redshift distribution**: Histogram of 39 sources in 0.5 bins; median error from bootstrap (1000 resamples of 39)  
  > "The errors on the median were determined using a bootstrap method, where we randomly sampled 39 sources from the redshift distribution 1000 times and took the standard deviation of the median values." (4.1)
   - fitting: _not stated_
   - validation: K-S test vs Weiss+13 distribution p=0.81  
  > "A KolmogorovÐ Smirnov (K-S) test show that the probability that these two distributions originate from a common sample is $p$$=$$0.81$." (4.1)
5. **Correct for gravitational lensing**: Divide the redshift distribution by the strong-lensing probability vs redshift (Hezaveh & Holder model) with a single mean magnification mu~10  
  > "We do this by dividing the redshift distribution by the probability for strong gravitational lensing as a function of redshift using the average magnification of our sample of $\mu$$\sim$10" (4.2.1 Lensing effects)
   - assumption: no systematic size evolution of DSFGs with redshift  
  > "All of these findings assume that DSFGs do not undergo a systematic size evolution with increasing redshift." (4.2.1 Lensing effects)
   - fitting: _not stated_
   - validation: Compared with Bethermin+15 lensed/unlensed models: chi2=8.9 and 9.7 over 9 bins  
  > "with $\chi^2$=9.7 over 9 bins" (4.2.1 Lensing effects)
6. **Compare with literature selected at other wavelengths**: K-S comparison of lensing-corrected distribution with 1.1 mm (Miettinen+15) and 870 um (Simpson+14) samples, removing z<1.5  
  > "we have removed sources with redshifts below $z$$<$1.5" (4.2.2)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : processing and imaging of ALMA data  
  > "We used the CASA package to process the data." (2.2 ALMA 3 mm scans)
- **HIPE** v9.0: Herschel/SPIRE map production  
  > "The maps were produced via the standard reduction pipeline HIPE v9.0." (2.6 Photometry)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Median redshift of 39 SPT DSFGs | 3.9 | 0.4 | dimensionless | 4 | The median redshift is $z$=3.9$\pm$0.4 |
| Lensing-corrected median redshift | 3.1 | 0.3 | dimensionless | 5 | the median of our distribution decreases from $z$$=$$3.9\pm0.4$ to $z$$=$$3.1\pm0.3$ after the lensing-correction |
| Median dust temperature | 39 | 10 | K | 3 | with the median dust temperature of $T_{\rm dust}$=39$\pm$10 K |
| Redshift success rate of 3 mm scans | >85% (36 of 41) | not stated | dimensionless | 2 | This translates into a success rate for our ALMA 3 mm scan technique of $>85\%$ (36 out of 41 targeted). |
| K-S p, observed vs lensing-corrected | 0.23 | not stated | dimensionless | 5 | A K-S comparison of the observed and lensing-corrected distributions gives a value of $p$$=$$0.23$. |
| K-S p vs Simpson+14 (870 um) | 0.03 | not stated | dimensionless | 6 | Their distribution differs significantly from ours with a K-S comparison probability $p$$=$$0.03$. |
| Highest redshift (SPT2351-57) | 5.811 | 0.002 | dimensionless | 2 | SPT2351-57 / I / **5.811(2)** |

## Qualitative findings

- Single-line plus well-sampled photometry gives reliable redshifts; most probable option confirmed for all but one source in 1 mm follow-up  
  > "they confirm the most probable redshifts as given in (cite: weiss13) for all except one source" (3.1 Targeted ALMA 1 mm observations)
- SPT0551-50 redshift revised from 2.1232 to 3.163  
  > "The favored option based on the dust continuum SED is $z$=3.163(3) with the line in the ALMA 3 mm spectrum being CO(4–3)." (3.2)

## Claim tuples

- H: What is the redshift distribution of SPT-selected DSFGs with the extended sample? | E: ALMA 3 mm scans of 15 new sources plus follow-up, combined with Weiss+13 | R: 39 spectroscopic redshifts, median 3.9±0.4, flat between z=2.5-5.0 | F: SPT DSFGs lie at higher redshift than shorter-wavelength-selected samples, with a significant z>3 tail | **supported**
- H: Does lensing bias the observed redshift distribution? | E: Divide by lensing probability with mu~10 | R: Median drops to 3.1±0.3; K-S p=0.23 | F: Lensing has no statistically significant impact; corrected distribution agrees with models | **supported**
- H: Does selection wavelength affect the redshift distribution? | E: K-S comparison with 1.1 mm and 870 um samples | R: p=0.29 vs 1.1 mm; p=0.03 vs 870 um | F: Selection wavelength is the main driver of differences | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Molecular line scans circumvent the need for counterpart identification and optical spectroscopy  
  > "circumventing the need for high-resolution imaging, counterpart identification, and optical spectroscopy" (1 Introduction)
- Alternative: Sources without lines are dropped rather than placed in the redshift desert as in Weiss+13  
  > "we do not follow this approach, but ignore sources without detected lines" (4.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Single magnification used for lensing correction is a simplification  
  > "We use a single magnification to produce our lensing-corrected redshift distribution, which is a simplified approximation." (4.2.1 Lensing effects)
- Limitation (authors): Not enough high-z size measurements to exclude size evolution  
  > "there are not enough measurements at high redshift ($z$$>$$4$) to exclude the possibility of size evolution entirely" (4.2.1 Lensing effects)
- Caveat (inferred, ours): Comparison samples have mixed photo-z and spec-z and different completeness
- Caveat (inferred, ours): Single-line redshifts rely on an assumed Tdust distribution; 80% success
- Caveat (inferred, ours): Lensing correction is sensitive to assumed mu and size-evolution assumption
- Caveat (inferred, ours): Small-number bins give large Poisson errors

## Reproducibility

- Data public (paper): ALMA project IDs listed in acknowledgments  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA# 2012.1.00844.S, 2012.1.00994.S, 2011.0.00957.S and 2011.0.00958.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version and clean parameters
- Missing: Line fitting and spectrum extraction details
- Missing: Lensing probability curve digitization and binning
- Missing: APEX, Herschel and ATCA data access
- Missing: 870 um ALMA cube details
- Data volume (inferred): ~50-150 GB for the Cycle 1 ALMA datasets (raw)
- Score (inferred): 3/5, ALMA data are public and the high-level recipe is clear, but imaging and extraction parameters are missing, and key results depend on external data and models.
- Rediscovery candidate: no, Main results (redshifts, median) are numeric, but recipe details are incomplete and depend on multi-facility and literature data.

## Links

- Method: (cite: weiss13) (ALMA Cycle 0 scan strategy and photometric single-line redshift method)
- Method: (cite: greve12) (SED fitting method)
- Method: (cite: hezaveh11) (lensing probability model)
- Companion: (cite: gullberg15) (APEX/FLASH [CII] observations of SPT DSFGs)
- Companion: (cite: spilker14) (SPT DSFG line properties and 870 um ALMA data)
- Related: South Pole Telescope 2500 deg2 survey
- Related: ALESS

## Checks

```json
{
 "quotes": 69,
 "quotes_ok": 69,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 87,
  "stated": 52,
  "rate": 0.598
 },
 "evidence_ok": true
}
```
