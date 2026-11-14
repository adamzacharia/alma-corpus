# An ALMA Survey of the SCUBA-2 Cosmology Legacy Survey UKIDSS/UDS Field: Number Counts of Submillimeter Galaxies

`2018ApJ...860..161S` | The Astrophysical Journal 2018 | first author: Stach, Stuart M. | arXiv: 1805.05362 | DOI: 10.3847/1538-4357/aac5e5

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: high_z_galaxies
- Question: What are the true (blending-free) 870 um number counts of SMGs, how much multiplicity affects single-dish SCUBA-2 sources, and are multiple SMGs in a single-dish source physically associated?  
  > "From this we construct resolved 870-$\mu$m SMG number counts and investigate the multiplicity in single-dish surveys." (1 Introduction)
- Target **S2CLS UDS field SCUBA-2 sources (716 >4 sigma sources)**: coordinates _not stated_; z/distance not stated (typical SMG z~2-3 mentioned; photometric redshifts used)  
  > "Between Cycles 1, 3 and 4 we observed all 716 $>4\sigma$ sources from the SCUBA-2 map, giving an observed flux density limit of $S_{\rm 850}\geq$ 3.4 mJy" (2.1 Sample Selection); distance from UKIDSS DR11 photometric redshifts (Hartley et al. in prep.) with eazy  
  > "Between Cycles 1, 3 and 4 we observed all 716 $>4\sigma$ sources from the SCUBA-2 map, giving an observed flux density limit of $S_{\rm 850}\geq$ 3.4 mJy" (2.1 Sample Selection)

## Data provenance

- ALMA projects: 2012.1.00090.S, 2015.1.01528.S, 2016.1.00434.S
- bands: Band 7 (344 GHz ~ 870 um)  
  > "Our ALMA targets were observed in Band 7 (344 GHz $\sim$ 870 $\mu$m)" (2.2 Data Reduction and Source Detection)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: 7.5 GHz bandwidth centred at 344 GHz, four basebands  
  > "with observations taken with 7.5 GHz bandwidth centred at 344 GHz using a single continuum correlator set-up with four basebands" (2.2 Data Reduction and Source Detection)
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.15-0.30 arcsec FWHM synthesized beam; Cycle 3 median 0.19 arcsec  
  > "a 0$\ensuremath{''}$15–0$\ensuremath{''}$30 FWHM synthesized beam" (abstract)
- max recoverable scale: _not stated_
- sensitivity: sigma_870 ~0.25 mJy/beam (taper maps: 0.25 C1, 0.34 C3, 0.23 C4)  
  > "$\sigma_{\rm 870}=$ 0.25 mJy beam$^{-1}$ for Cycle 1, $\sigma_{\rm 870}=$ 0.34 mJy beam$^{-1}$ for Cycle 3 and $\sigma_{\rm 870}=$ 0.23 mJy beam$^{-1}$ in Cycle 4" (2.2 Data Reduction and Source Detection)
- time on source: 40 seconds per field  
  > "Observations of 40 seconds were employed" (2.2 Data Reduction and Source Detection)
- observing dates: Cycle 1 2013 Nov 1; Cycle 3 2016 Jul 23-Aug 11; Cycle 4 2016 Nov 9-17 and 2017 May 6  
  > "Cycle 1 observations were carried out on 2013 November 1, Cycle 3 between 2016 July 23 and August 11 and Cycle 4 between 2016 November 9 and 17 and 2017 May 6." (2.2 Data Reduction and Source Detection)
- pi or archival as stated: _not stated_
- Other facility **JCMT SCUBA-2 (S2CLS)**: parent 850 um catalogue of 716 sources  
  > "based on a complete sample of 850-$\mu$m sources selected from the S2CLS map of the UDS field" (2.1 Sample Selection)
- Other facility **UKIDSS DR11 / Spitzer photometry**: photometric redshifts for SMGs  
  > "We use the photometric redshift catalog constructed from the UKIDSS DR11 release (Hartley et al. in prep.)" (3.3 Physical association of the multiple SMGs)
- Other facility **Herschel/SPIRE**: stacking at blank-map positions  
  > "We test this by stacking *Herschel*/SPIRE maps at the locations of the 108 “blank” map sources" (3.1 Flux Recovery)
- External data: S2CLS UDS catalogue and parent-sample incompleteness (complete >=5 mJy, ~88% at 4.5, ~83% at 4 mJy)  
  > "the parent sample is effectively complete at $\geq$ 5 mJy, dropping to $\sim$ 88% at $\geq$ 4.5 mJy and $\sim$ 83% at $\geq$ 4 mJy" (3.2 Number Counts) [from (cite: geach2017scuba)]
- External data: S870/S850 = 0.95 from composite SMG SED at z=2.5  
  > "we use a factor of $S_{\rm 870}/S_{\rm 850}=$ 0.95 derived from a redshifted ($z=$ 2.5), composite spectral energy distribution (SED) for SMGs from the ALESS survey" (3.2 Number Counts) [from (cite: swinbank2013alma)]
- External data: UKIDSS DR11 photometric redshift catalogue  
  > "These photometric redshifts are derived from twelve photometric bands" (3.3 Physical association of the multiple SMGs) [from Hartley et al. in prep.; (cite: simpson2013prevalence)]
- Simulation/model as data: Injected model sources (power-law index -2, FWHM 0-0.9 arcsec) in 60,000 simulated noise maps built from ten CASA residual maps  
  > "inserted into 60,000 simulated noise maps" (2.3 Completeness & Flux Deboosting)

## Processing

### Calibration

- pipeline or manual: Calibration with CASA; details deferred to Stach et al. in prep.  
  > "Calibration and imaging were carried out with the COMMON ASTRONOMY SOFTWARE APPLICATION" (2.2 Data Reduction and Source Detection)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CLEAN, multi-frequency synthesis continuum  
  > "The CLEAN algorithm was used to create the continuum maps using multi-frequency synthesis mode with a natural weighting to maximise sensitivity." (2.2 Data Reduction and Source Detection)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "using multi-frequency synthesis mode with a natural weighting to maximise sensitivity" (2.2 Data Reduction and Source Detection)
- uv taper: 0.5 arcsec FWHM Gaussian taper for detection maps  
  > "we created “detection” maps by applying a 0$\ensuremath{''}$5 FWHM Gaussian taper in the *uv*-plane" (2.2 Data Reduction and Source Detection)
- cell size: _not stated_
- image size: _not stated_
- masking: clean to 3 sigma, mask ellipses on >4 sigma sources, clean to 1.5 sigma  
  > "The fields were then initially cleaned to 3 $\sigma$ and then masking ellipses are placed on sources above 4 $\sigma$" (2.2 Data Reduction and Source Detection)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: 1 arcsec aperture fluxes measured on primary-beam-corrected maps  
  > "we then derived a 1$\ensuremath{''}$0 diameter aperture flux density from the primary beam corrected maps" (2.2 Data Reduction and Source Detection)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: detection maps mean 0.73x0.59 (C1), 0.56x0.50 (C3), 0.58x0.55 arcsec (C4)  
  > "mean synthesized beam size of 0$\ensuremath{''}$73 $\times$ 0$\ensuremath{''}$59 for Cycle 1, 0$\ensuremath{''}$56 $\times$ 0$\ensuremath{''}$50 for Cycle 3" (2.2 Data Reduction and Source Detection)
- final rms: _not stated_

### Inherited from earlier work

- Data reduction and source extraction details  
  > "Full details of the data reduction and source detection will be presented in Stach et al. (in prep.)" (2.2 Data Reduction and Source Detection) [from Stach et al. (in prep.)]
- Aperture correction and flux deboosting methodology  
  > "these flux densities are aperture corrected and flux deboosted using the same methodology as (cite: simpson2015scuba2)" (2.2 Data Reduction and Source Detection) [from (cite: simpson2015scuba2)]
- Error calculation for counts  
  > "As in (cite: karim2013alma) the errors are calculated from both the Poissonian error and the individual flux uncertainties added in quadrature" (3.2 Number Counts) [from (cite: karim2013alma)]
- Multiple-map definition (>1 SMG at S870>=1 mJy in primary beam)  
  > "We follow (cite: simpson2015scuba2) and define a multiple map as any field with more than one $S_{\rm 870}\geq$ 1 mJy SMG" (3.2 Multiplicity) [from (cite: simpson2015scuba2)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration/flagging procedure
- Calibrator choices and flux scale uncertainty for ALMA
- Treatment of sources observed twice (cross-calibration)
- Aperture correction and deboosting functional forms
- Fit method and priors for the double power-law
- Final SMG catalogue (deferred to Stach et al. in prep.)
- Photometric redshift catalogue not public in this paper
- Which ALMA data are used per source in repeated fields

## Analysis recipe

1. **Create tapered detection maps**: CLEAN with natural weighting and 0.5 arcsec uv taper  
  > "The CLEAN algorithm was used to create the continuum maps using multi-frequency synthesis mode with a natural weighting to maximise sensitivity." (2.2 Data Reduction and Source Detection)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Detect sources and assess purity**: SExtractor >2 sigma peaks; SNR from 0.5 arcsec aperture flux and noise from 100 random apertures; cut SNR>=4.3; purity from inverted maps  
  > "SEXTRACTOR was initially used to find $>$ 2 $\sigma$ peaks within the “detection” maps." (2.2 Data Reduction and Source Detection)
   - software: SExtractor
   - parameter: SNR>=4.3 gives 98% purity  
  > "This threshold and aperture size was chosen to give us a 98 % purity rate" (2.2 Data Reduction and Source Detection)
   - fitting: _not stated_
   - validation: Negative-source count consistent with Gaussian expectation (~16, 2.3%)  
  > "This would result in an expected $\sim$ 16 “negative” sources or 2.3 $\pm$ 0.5 %, which is consistent with the number we detect." (2.2 Data Reduction and Source Detection)
3. **Completeness and flux deboosting**: Inject model sources into 60,000 simulated noise maps and re-run detection  
  > "Model sources with flux densities drawn from a steeply declining power-law distribution with an index of $-2$" (2.3 Completeness & Flux Deboosting)
   - software: CASA
   - parameter: recovery within 0.6 arcsec of injected position  
  > "with a successful recovery claimed for detections within the size of a synthesized beam, i.e. 0$\ensuremath{''}$6" (2.3 Completeness & Flux Deboosting)
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive number counts and fit double power law**: Cumulative and differential counts of 299 SMGs >=4 mJy, normalised by 0.96 deg2, corrected for S2CLS incompleteness; errors from Poisson plus 1000 resamples; double power-law fit  
  > "the standard deviation of the mean of the counts for each bin based on 1,000 re-samples of the catalog" (3.2 Number Counts)
   - assumption: S870/S850 = 0.95  
  > "we use a factor of $S_{\rm 870}/S_{\rm 850}=$ 0.95" (3.2 Number Counts)
   - fitting: _not stated_
   - validation: Comparison to S2CLS and ALESS counts  
  > "We also compare these counts to those from the parent single-dish catalog of the S2CLS UDS field" (3.2 Number Counts)
5. **Multiplicity statistics**: Count maps with >1 SMG at S870>=1 mJy, versus deboosted SCUBA-2 flux  
  > "define a multiple map as any field with more than one $S_{\rm 870}\geq$ 1 mJy SMG within our ALMA Band 7 primary beam" (3.2 Multiplicity)
   - fitting: _not stated_
   - validation: _not stated_
6. **Test physical association of multiples**: Compare photo-z differences of 46 SMG pairs to 10,000 random draws of 46 pairs from 497 SMGs  
  > "we sample the random distribution of our unassociated SMGs 10,000 times, each time drawing 46 pairs" (3.3 Physical association of the multiple SMGs)
   - software: eazy
   - parameter: Delta z_phot < 0.25  
  > "We find that 52 % of these pairs (24/46) have $\Delta z_{\rm phot} <$ 0.25." (3.3 Physical association of the multiple SMGs)
   - fitting: _not stated_
   - validation: Repeated for pairs separated >2 arcsec: 53% (23/43)  
  > "This *still* results in 53 % of pairs having $\Delta z_{\rm phot} <$ 0.25 (23/43)." (3.3 Physical association of the multiple SMGs)

## Software

- **CASA** : calibration and imaging  
  > "Calibration and imaging were carried out with the COMMON ASTRONOMY SOFTWARE APPLICATION" (2.2 Data Reduction and Source Detection)
- **SExtractor** : source detection  
  > "SEXTRACTOR was initially used to find $>$ 2 $\sigma$ peaks" (2.2 Data Reduction and Source Detection)
- **eazy** : photometric redshifts  
  > "applied to 296,007 $K$-band-detected sources using eazy" (3.3 Physical association of the multiple SMGs)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of SMGs detected (SNR>=4.3) | 695 | not stated | sources | 2 | The AS2UDS catalog contains 695 SMGs (detected in 606 ALMA maps) |
| Completeness at S870>=4 mJy | 98 | 1 | % | 3 | we estimate our catalog is 98 $\pm$ 1 % complete for all our simulated sources at $S_{870}\geq$ 4 mJy |
| Median deboosting factor at >=4 mJy | 0.98 | 0.04 | dimensionless | 3 | a median correction factor of 0.98 $\pm$ 0.04 |
| Surface density S870>=4 mJy | 390 | +70/-80 | deg^-2 | 4 | At $S_{\rm 870}\geq$ 4 mJy we derive a surface density of 390$^{+70}_{-80}$  deg$^{-2}$ |
| Double power-law N0 | 1200 | +200/-300 | deg^-2 | 4 | $N_{0}=1200^{+200}_{-300}$ deg$^{-2}$, $S_{0}=5.1\pm0.7$ mJy, $\alpha=5.9^{+1.3}_{-0.9}$ and $\beta=0.4\pm0.1$ |
| Double power-law S0 | 5.1 | 0.7 | mJy | 4 | $S_{0}=5.1\pm0.7$ mJy |
| Double power-law alpha | 5.9 | +1.3/-0.9 | dimensionless | 4 | $\alpha=5.9^{+1.3}_{-0.9}$ |
| Double power-law beta | 0.4 | 0.1 | dimensionless | 4 | $\beta=0.4\pm0.1$ |
| Reduction of counts vs SCUBA-2 at >=4 mJy | 28 | 2 | % | 4 | with a reduction of a factor of 28 $\pm$ 2 % at $S_{\rm 870}\geq$ 4 mJy |
| Multiplicity, S850deb>=5 mJy | 28 (51/179) | 2 | % | 5 | The rate of multiples in these brighter SCUBA-2 sources is much higher 51/179 (28 $\pm$ 2 %) |
| Multiplicity, S850deb>=9 mJy | 44 | +16/-14 | % | 5 | rising to 44$^{+16}_{-14}$ % at $S^{\rm deb}_{\rm 850}\geq$ 9 mJy |
| Maps with multiple SMGs | 79 of 716 | 1 % | maps (11%) | 5 | 79 of the 716 observations (11 $\pm$ 1 %) |
| Blank maps | 108 | 15 +/- 2 % | maps | 2 | there are 108 of these “blank” maps (15 $\pm$ 2 % of the survey) |
| Pairs with Delta z_phot<0.25 | 52 (24/46) | not stated | % | 6 | We find that 52 % of these pairs (24/46) have $\Delta z_{\rm phot} <$ 0.25. |
| Random pairs with Delta z_phot<0.25 | 20 | 2 | % | 6 | the median fraction of random pairs with $\Delta z_{\rm phot} <$ 0.25 is 20 $\pm$ 2 % |
| Lower limit on physically associated multiple fields | 30 (24/79) | not stated | % | 6 | we can place a lower limit of at least 30 % (24 pairs out of 79) |

## Qualitative findings

- Most blank maps are genuine ALMA non-detections (SPIRE stacking detects emission), likely extreme multiplicity  
  > "Hence we are confident that the majority of the “blank” maps are a result of genuine non-detections in ALMA and not false positive sources in the S2CLS map." (3.1 Flux Recovery)

## Claim tuples

- H: Single-dish counts overestimate true SMG counts | E: Compare AS2UDS 870 um counts to S2CLS counts | R: Normalisation lower by 28+/-2% at >=4 mJy; shape similar | F: Multiplicity reduces counts; double power law fits | **supported**
- H: Multiplicity rises with single-dish flux | E: Count maps with >1 SMG >=1 mJy vs S850 | R: 28% at >=5 mJy, 44% at >=9 mJy | F: Blending is common and flux dependent | **supported**
- H: Some SMG blends are physically associated | E: Photo-z difference distribution for 46 pairs vs random | R: 52% vs 20% of pairs with Delta z<0.25 | F: At least 30% of multiple-SMG maps arise from associated galaxies | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Fixed 1 mJy limit chosen for multiples because of uniform sensitivity and physical meaning  
  > "Our survey has a relatively uniform sensitivity of $\sigma_{\rm 870}\sim$ 0.25 mJy beam$^{-1}$, and therefore we adopt a fixed $S_{\rm 870}$ limit to identify multiple SMGs." (3.2 Multiplicity)
- How they decided it was enough: _not stated_
- Limitation (authors): Multiplicity is a lower limit since catalogue is incomplete at 1 mJy  
  > "We note that at 1 mJy our ALMA observations are not complete, therefore this sets the multiplicity as a lower limit." (3.2 Multiplicity)
- Limitation (authors): Spectroscopic coverage sparse so photo-zs used  
  > "as the current spectroscopic coverage of SMGs in AS2UDS is sparse, we instead exploit photometric redshifts" (3.3 Physical association of the multiple SMGs)
- Caveat (inferred, ours): Photo-z pair excess does not prove physical association; Delta z<0.25 is broad
- Caveat (inferred, ours): Random-pair control may not account for clustering or lensing
- Caveat (inferred, ours): Counts depend on S2CLS incompleteness correction and flux scale (15%)
- Caveat (inferred, ours): Poorly specified fit method for the double power law

## Reproducibility

- Data public (paper): ALMA data from named programmes; catalogue deferred to later paper  
  > "The ALMA data used in this paper were obtained under programs ADS/JAO.ALMA#2012.1.00090.S, #2015.1.01528.S and #2016.1.00434.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Source catalogue (Stach et al. in prep.)
- Missing: Photometric redshift catalogue (Hartley et al. in prep.)
- Missing: CASA version and calibration details
- Missing: Fit algorithm for double power law
- Data volume (inferred): Large: ~716 short Band 7 pointings, likely several hundred GB to ~1 TB raw
- Score (inferred): 3/5, Data from three public-programme cycles and clear detection/counting recipe, but catalogue, calibration details and photo-z catalogue are deferred to unpublished papers.
- Rediscovery candidate: no, Recipe depends on unpublished catalogue and photo-z papers; large data volume and incomplete processing details.

## Links

- Method: Stach et al. (in prep.) (full data reduction and source extraction)
- Method: (cite: simpson2015scuba2) (flux deboosting, aperture correction, multiplicity definition)
- Method: (cite: karim2013alma) (count error method)
- Companion: (cite: simpson2015scuba2) (Cycle 1 pilot study of 30 bright S2CLS UDS sources)
- Companion: (cite: hill2018high) (SMA follow-up of bright S2CLS sources)
- Related: ALESS
- Related: S2CLS
- Related: UKIDSS UDS

## Checks

```json
{
 "quotes": 71,
 "quotes_ok": 71,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 16,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 48,
  "rate": 0.585
 },
 "evidence_ok": true
}
```
