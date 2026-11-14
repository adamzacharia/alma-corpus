# An ALMA survey of submillimeter galaxies in the COSMOS field: Multiwavelength counterparts and redshift distribution

`2017A&A...608A..15B` | Astronomy and Astrophysics 2017 | first author: Brisbin, Drew | arXiv: 1708.05748 | DOI: 10.1051/0004-6361/201730558

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: high_z_galaxies
- Question: What are the multiwavelength counterparts and the redshift distribution of AzTEC/ASTE-selected submillimeter galaxies in COSMOS, and how does it depend on flux density?  
  > "we present counterparts and redshifts for a sample of 129 SMGs that were initially discovered with the AzTEC camera on ASTE, and are now identified with high-resolution 1.25 mm ALMA imaging." (1. Introduction)
- Target **129 AzTEC/ASTE-selected SMG fields in COSMOS**: coordinates _not stated_; z/distance median z=2.48±0.05  
  > "These fields were drawn from Aretxaga et al. (2011) to include a flux-limited sample of AzTEC /ASTE sources with (deboosted) 1.1 mm flux densities ≥3.5 mJy covering the inner 0.72 square degrees of COSMOS." (2.1 ALMA observations); distance from spectroscopic, photometric, FIR and radio-mm redshifts derived in this paper  
  > "These fields were drawn from Aretxaga et al. (2011) to include a flux-limited sample of AzTEC /ASTE sources with (deboosted) 1.1 mm flux densities ≥3.5 mJy covering the inner 0.72 square degrees of COSMOS." (2.1 ALMA observations)

## Data provenance

- ALMA projects: 2013.1.00118.S, 2011.0.00539.S
- bands: Band 6 (1.25 mm, 240 GHz)  
  > "Band 6 continuum observations were taken with an aggregate bandwidth of 7.5 GHz centered on 240 GHz." (2.1 ALMA observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: 7.5 GHz aggregate  
  > "Band 6 continuum observations were taken with an aggregate bandwidth of 7.5 GHz centered on 240 GHz." (2.1 ALMA observations)
- arrays: _not stated_
- configurations: compact, 32-40 antennas, max baseline ~340 m  
  > "We used the array in a relatively compact configuration using between 32 and 40 antennas, with a maximum baseline of ∼ 340 m." (2.1 ALMA observations)
- baselines: _not stated_
- angular resolution: 1.6×0.93" synthesized beam (natural weighting)  
  > "using natural weighting, resulting in a synthesized beam size of 1.6×0.93”." (2.1 ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: ~150 µJy/beam RMS  
  > "All fields reach a homogenous RMS of ∼150 µJy beam [−][1] at an effective wavelength of 1.25 mm." (2.1 ALMA observations)
- time on source: _not stated_
- observing dates: 9-11 December 2014 (Cycle 2)  
  > "The observations were taken between 09 and 11 December 2014, under good weather conditions." (2.1 ALMA observations)
- pi or archival as stated: _not stated_
- Other facility **COSMOS2015 catalog**: UV-NIR photometry for counterparts  
  > "We used the latest COSMOS photometric catalog (COSMOS2015 hereafter; Laigle et al. 2016)" (2.2 UV-NIR)
- Other facility **VLA 1.4 and 3 GHz**: radio counterparts  
  > "We also cross-matched our ALMA catalog with an internal VLA-COSMOS 1.4 GHz catalog (see Schinnerer et al. 2007) as well as a 3 GHz catalog (Smolˇci´c et al. 2017)." (3.2 Radio counterparts)
- Other facility **Herschel (HerMES, PEP)**: FIR photometry 100-500 µm  
  > "The Herschel photometry includes PACS and SPIRE photometry at 100,160, 250, 350, and 500 µm." (3.3 FIR - (sub-)mm counterparts and photometry)
- External data: AzTEC/ASTE 1.1 mm parent catalog  
  > "These fields were drawn from Aretxaga et al. (2011)" (2.1 ALMA observations) [from Aretxaga et al. 2011]
- External data: COSMOS spectroscopic redshift catalog  
  > "In total, over 97,000 spectroscopic redshifts are listed in the catalog, including 24 of our ALMA sources." (2.3 Spectroscopy) [from M. Salvato et al., in prep.]
- External data: X-ray based photometric redshifts for 7 sources  
  > "Marchesi et al. (2016) used the combined X-ray and UV-IR SEDs to fit photometric redshifts" (4.2 AGN templates and X-ray detected sources) [from Marchesi et al. (2016)]
- Simulation/model as data: Béthermin et al. (2015) and Hayward et al. (2013b) model predicted median redshifts compared with data  
  > "In Fig. 9 we show the Béthermin et al. (2015) predicted median redshifts at 1.2 mm as a function of flux limit" (5. Discussion)

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
- weighting robust: natural weighting  
  > "using natural weighting, resulting in a synthesized beam size of 1.6×0.93”." (2.1 ALMA observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: tight boxes around >5σ single-pixel sources; clean to 2.5σ  
  > "Sources which were detected in single pixels at significance levels above 5σ were then masked with tight boxes around the source, and cleaned down to a 2.5σ threshold." (2.1 ALMA observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: ~150 µJy/beam  
  > "All fields reach a homogenous RMS of ∼150 µJy beam [−][1] at an effective wavelength of 1.25 mm." (2.1 ALMA observations)

### Inherited from earlier work

- Photometry extraction and deblending procedure for 38 counterparts  
  > "This was done following the procedure described in detail in Smolˇci´c et al. (2012a), and further applied in Smolˇci´c et al. (2012b)." (3.1 UV-NIR counterparts and photometry) [from Smolčić et al. 2012a,b]
- Photo-z method (Hyper-z with GRASIL SMG templates)  
  > "We adopt this procedure from Smolˇci´c et al. (2012a), Smolˇci´c et al. (2012b), and Miettinen et al. (2015a)." (4.1 Spectroscopic and photometric) [from Smolčić et al. 2012a,b; Miettinen et al. 2015a]
- Radio-mm redshift method with Arp 220 template  
  > "We follow the method presented in Aravena et al. (2010) in using the modeled SED of Arp 220 as an emission template" (4.3 Radio - millimeter redshifts) [from Aravena et al. 2010]
- Far-IR photometry extraction and deblending  
  > "Source photometry was extracted and deblended according to techniques detailed in Magnelli et al. (2013)" (3.3 FIR - (sub-)mm counterparts and photometry) [from Magnelli et al. (2013)]
- Redshift density likelihood construction  
  > "constructed as in Miettinen et al. (2015a)" (4.6 Redshift distribution) [from Miettinen et al. (2015a)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration pipeline/CASA versions and calibrators
- Clean task, iteration limits and pixel/image size
- Source-finding algorithm and flux extraction method for ALMA catalog (deferred to Aravena et al. in prep)
- Hyper-z template details beyond reference, exact band selection
- Exact flux values per source (ALMA catalog not in this paper)

## Analysis recipe

1. **Detect ALMA sources**: Natural-weighted continuum images, sources >=5σ within AzTEC beam, cleaned to 2.5σ  
  > "After cleaning the resulting images, 152 sources were detected at ≥5σ, within the beam width of the initial AzTEC observations in each target field." (2.1 ALMA observations)
   - fitting: _not stated_
   - validation: Simulations inserting false sources at 2-40σ showed flux boosting does not exceed map RMS  
  > "Simulation tests, performed by inserting false sources with signals in the range 2-40 σ confirm that at ≥5σ, flux boosting does not exceed map RMS." (2.1 ALMA observations)
2. **Identify multiwavelength counterparts**: Cross-match to COSMOS2015, IRAC, VLA 1.4/3 GHz catalogs with visual inspection; manual photometry for 38 sources  
  > "In total, we find counterparts for 135/152 (94%) sources." (3.1 UV-NIR counterparts and photometry)
   - parameter: radio search radii 1.8" (1.4 GHz) and 0.75" (3 GHz)  
  > "Using search radii matching the mean resolutions in the radio surveys (1.8 and 0.75” at 1.4 GHz and 3 GHz respectively)" (3.2 Radio counterparts)
   - fitting: _not stated_
   - validation: _not stated_
3. **Photometric redshifts**: χ2 minimization with SMG-optimized GRASIL templates for sources with ≥4 bands; likelihood L∝exp(-χ2/2); linear correction applied  
  > "The minimization is done using Hyper-z (Bolzonella et al. 2000) [1] assuming a Calzetti et al. (2000) extinction law, reddening varying from 0 to 5, and allowing for a redshift range of 0-7." (4.1 Spectroscopic and photometric)
   - software: Hyper-z
   - assumption: Calzetti extinction law, z range 0-7  
  > "assuming a Calzetti et al. (2000) extinction law, reddening varying from 0 to 5, and allowing for a redshift range of 0-7." (4.1 Spectroscopic and photometric)
   - fitting: χ2 minimization; correction zspec = 0.95 zphot + 0.20  
  > "Weighing by the photometric redshift uncertainty we find z spec = 0.95 × z phot + 0.20." (4.1 Spectroscopic and photometric)
   - validation: Compared with spectroscopic redshifts, ⟨Δz/(1+zspec)⟩=0.096  
  > "⟨∆ z /(1 + z spec )⟩=0.096" (4.1 Spectroscopic and photometric)
4. **Radio-mm redshifts**: Spectral index between 240 GHz and 3/1.4 GHz vs. redshift using Arp 220-like template  
  > "This model is closely matched by a modified black body dust emission with T d =45 K and dust emissivity index β=1" (4.3 Radio - millimeter redshifts)
   - parameter: dust temperature range 25-60 K for uncertainty  
  > "assuming a range of dust temperatures from 25 to 60 K" (4.3 Radio - millimeter redshifts)
   - assumption: upper limit z=7 where index turns over; 3σ radio limits give lower limits  
  > "In these cases we assume an upper limit of z =7" (4.3 Radio - millimeter redshifts)
   - fitting: _not stated_
   - validation: Compared with spectroscopic redshifts (Fig. 5)  
  > "Ultraviolet-NIR photometric redshifts have a well established record of use (e.g., Smolˇci´c et al. 2012a,b, Ilbert et al 2009), and they compare well to spectroscopic redshifts in our sample." (4.5 Redshift comparison)
5. **Far-infrared redshifts**: Parabola fit to FIR SED peak wavelength, calibrated on 16 spec-z training sources; linear z=m×λpeak+b; uncertainty inflated 2.5x  
  > "We fit this correlation with a straight line, z = m × λ peak + b, and find m = 0.0187 ± 0.0007, and b = −3.8 ± 0.2." (4.4 Far-infrared redshifts)
   - fitting: χ2 minimization  
  > "We fit the observed SED of each source with a simple parabola through χ [2] minimization" (4.4 Far-infrared redshifts)
   - validation: Error bars encompass 68% (28/41) of literature sources with spec-z  
  > "The expanded error bars encompass 68% (28 out of 41) of the tested literature sources with spectroscopic redshifts." (4.4 Far-infrared redshifts)
6. **Combine redshifts and derive distribution**: Synthetic likelihoods for ambiguous photo-z; summed redshift likelihoods; 1000 Monte-Carlo median trials; KS tests  
  > "Redshifts are then randomly sampled from each of the 152 redshift likelihood functions and the sample median is determined in each of 1000 Monte-Carlo trials." (4.6 Redshift distribution)
   - fitting: _not stated_
   - validation: strict vs extended samples compared with KS test  
  > "a Kolmogorov-Smirnov (KS) test comparing the strict sample to the 27 sources in the complementary sample finds an associated probability of 0.32" (4.6 Redshift distribution)

## Software

- **Hyper-z** : photometric redshift fitting  
  > "The minimization is done using Hyper-z (Bolzonella et al. 2000)" (4.1 Spectroscopic and photometric)
- **GRASIL** : spectral templates  
  > "a set of spectral templates developed in GRASIL (Silva et al. 1998; Iglesias-Paramo et al. 2007)" (4.1 Spectroscopic and photometric)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA sources detected at ≥5σ | 152 | not stated | sources | 1 | detecting 152 galaxies at S/N≥5 with an average continuum RMS of 150 µJy |
| Median redshift of redshift density distribution | 2.48 | ±0.05 | dimensionless | 6 | The median of this distribution is ˜ z =2.48±0.05. |
| Median z, strict sample (116 sources) | 2.3 | ±0.6 | dimensionless | 6 | The strict sample consists of 116 sources and has a median redshift z ˜=2.3±0.6 |
| Median z, S1.25mm<1.25 mJy | 2.18 | ±0.09 | dimensionless | 6 | Our faintest sources, with S 1.25mm <1.25 mJy, have a median redshift of z ˜=2.18±0.09 |
| Median z, S1.25mm>1.8 mJy | 3.08 | ±0.17 | dimensionless | 6 | while the brightest sources, S 1.25mm >1.8 mJy, have a median redshift of ˜ z =3.08±0.17. |
| FIR training fit slope m | 0.0187 | ±0.0007 | per µm | 5 | m = 0.0187 ± 0.0007, and b = −3.8 ± 0.2. |
| Photo-z/spec-z mean scatter | 0.096 | not stated | dimensionless | 3 | ⟨∆ z /(1 + z spec )⟩=0.096 |

## Qualitative findings

- Likely physical associations in nine multi-component systems; 13 possible  
  > "we have identified nine likely and 13 possible physical associations of SMGs." (6. Summary)

## Claim tuples

- H: Brighter mm sources lie at higher redshift | E: Split sample by 1.25 mm flux and compare redshift density medians with KS test | R: Median z rises from ~2.2 to ~3.1; KS p=1.4e-3 (extended) | F: Redshift distribution depends on flux density/survey depth | **supported**
- H: Our SMG redshift distribution is consistent with earlier surveys once flux limits are matched | E: Compare with Simpson 2014, Danielson 2017, Chapman 2005, Strandet 2016 via KS test and flux scaling | R: KS probability 0.87 vs Simpson, 0.23 vs Danielson; z=3.25 above Strandet-equivalent cut | F: Differences are explained by flux limits and selection | **supported**
- H: Models predict the flux dependence of median redshift | E: Compare medians at flux cuts to Béthermin et al. 2015 | R: 2.49, 2.7, 3.1 vs predicted 2.49, 2.70, 2.86 | F: Consistent with Béthermin model | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Third-degree polynomials and modified blackbodies for FIR fits gave weaker overall z correlation than parabola  
  > "the overall correlation between spectroscopic redshift and FIR model redshift is strongest with the simple parabola-fitting method." (4.4 Far-infrared redshifts)
- How they decided it was enough: _not stated_
- Limitation (authors): FIR and radio-mm redshifts have large uncertainty; FIR model ignores physical dust conditions  
  > "Our simple model does not attempt to characterize the physical dust conditions such as mass, emissivity, multiple dust components" (4.4 Far-infrared redshifts)
- Caveat (inferred, ours): ALMA catalog and flux measurements deferred to an unpublished companion paper
- Caveat (inferred, ours): Photo-z linear correction derived from only ~26 sources
- Caveat (inferred, ours): Selection function from ASTE 1.1 mm and ALMA sensitivity not fully modelled

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Per-source ALMA fluxes (Aravena et al. in prep)
- Missing: Internal COSMOS spectroscopic and radio catalogs
- Missing: Unpublished CO redshifts
- Data volume (inferred): ~100 GB-scale for 129 Band 6 fields; the analysis needs catalogs more than visibilities
- Score (inferred): 3/5, ALMA data are archival but analysis relies on external catalogs and unpublished companion papers.
- Rediscovery candidate: no, Recipe depends on proprietary or in-prep catalogs and unspecified ALMA catalog.

## Links

- Method: Smolčić et al. 2012a (photometry extraction and photo-z procedure)
- Method: Aravena et al. 2010 (radio-mm redshift method)
- Method: Miettinen et al. 2015a (redshift likelihood construction)
- Companion: M. Aravena et al. (in prep) (observations and source catalog)
- Companion: Miettinen et al. (2017a) (radio emission analysis)
- Companion: Miettinen et al. (2017b) (multiwavelength SEDs)
- Related: COSMOS
- Related: AzTEC/ASTE
- Related: ALESS

## Checks

```json
{
 "quotes": 59,
 "quotes_ok": 59,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 46,
  "rate": 0.561
 },
 "evidence_ok": true
}
```
