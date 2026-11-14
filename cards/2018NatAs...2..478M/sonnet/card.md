# The unexpectedly large proportion of high-mass star-forming cores in a Galactic mini-starburst

`2018NatAs...2..478M` | Nature Astronomy 2018 | first author: Motte, F. | arXiv: 1804.02392 | DOI: 10.1038/s41550-018-0452-x

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism
- Question: Is the core mass function (CMF) of the high-mass star-forming cloud W43-MM1 similar to the stellar IMF at masses above ~1 Msun, as found in nearby regions?  
  > "reveals, for the first time, a statistically robust CMF at high masses, with a slope that is markedly shallower than the IMF." (abstract)
- Target **W43-MM1**: coordinates _not stated_; z/distance 5.5 kpc  
  > "∼ 2, 400 AU at 5.5 kpc" (Methods); "located at the tip of the Galactic bar" (main text); distance from not stated (cited Nguyen Luong et al. 2011)  
  > "∼ 2, 400 AU at 5.5 kpc" (Methods); "located at the tip of the Galactic bar" (main text)

## Data provenance

- ALMA projects: 2013.1.01365.S
- bands: 1.3 mm continuum, 33-field mosaic  
  > "The W43-MM1 cloud was imaged with a 33-field mosaic covering its 2.1 pc×1.4 pc extent." (Methods)
- frequencies and spectral setup: eight spectral windows; continuum window centred at 233.45 GHz, 1.9 GHz bandwidth, 977 kHz channels  
  > "centred at 233.45 GHz, with 1.9 GHz bandwidth and 977 kHz channel step" (Methods)
- continuum bandwidth: _not stated_
- arrays: 12 m array; 7 m data not used  
  > "The complementary data taken with the 7 m interferometric array were not used because of their low signal-to-noise ratio." (Methods)
- configurations: _not stated_
- baselines: 13 m to 1045 m  
  > "With baselines ranging from 13 m to 1045 m" (Methods)
- angular resolution: 0.37'' x 0.53'' (~2,400 AU)  
  > "0.37 ′′ ×0.53 ′′ (∼ 2, 400 AU at 5.5 kpc)" (Methods)
- max recoverable scale: 12''  
  > "to the filtering scale of the interferometer for our observations, 12 ′′" (Methods)
- sensitivity: noise ~0.13 mJy/beam in outskirts to ~2.5 mJy/beam towards main filament  
  > "we estimate noise levels from ∼0.13 mJy/beam in the outskirts to ∼2.5 mJy/beam towards the main filament" (Methods)
- time on source: _not stated_
- observing dates: September 2014 to June 2015  
  > "carried out between September 2014 and June 2015" (Methods)
- pi or archival as stated: _not stated_
- Line: 13CS 5-4 (not stated)
- Other facility **Herschel**: 70 to 500 um images for dust temperature (PPMAP)  
  > "estimated using Herschel 70 to 500 µm images, APEX 350 and 870 µm" (main text)
- Other facility **APEX**: 350 and 870 um images for temperature  
  > "APEX 350 and 870 µm" (main text)
- Other facility **IRAM interferometer**: 3 mm mosaic for temperature  
  > "mosaics obtained with the ALMA (present data) and IRAM interferometers at" (main text)
- External data: Dust opacity kappa 1.3mm = 0.01 cm2/g  
  > "We have adopted κ 1.3mm = 0.01 cm 2 g −1" (Methods) [from Ossenkopf & Henning 1994 (35)]
- External data: IMF slope -1.35 for comparison  
  > "is −1.35" (main text) [from Kroupa et al. 2013; Salpeter 1955]
- External data: Distance 5.5 kpc  
  > "∼ 5.5 kpc from the Sun" (main text) [from Nguyen Luong et al. 2011]

## Processing

### Calibration

- pipeline or manual: manual and self-calibration scripts in CASA  
  > "applying manual and SelfCalibration scripts" (Methods)
- casa version: CASA 4.3.1  
  > "Data were reduced with the CASA 4.3.1 software" (Methods)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: started from highest-sensitivity map integrated over full 1.9 GHz continuum band  
  > "provided that it started from the highest-sensitivity map integrated over the complete 1.9 GHz continuum band" (Methods)

### Imaging

- task: Clean with MultiScale option  
  > "applied the Clean algorithm with a robust weight of 0.5 and the MultiScale option" (Methods)
- deconvolver: _not stated_
- weighting robust: robust = 0.5  
  > "with a robust weight of 0.5" (Methods)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: selection of line-free channels summing to 65 MHz (channels not listed)  
  > "a selection of line-free channels summing up to 65 MHz" (Methods)
- primary beam correction: _not stated_
- array combination: 12 m only; merged 12m+7m not used  
  > "because the MultiScale cleaning of 12 m-only data provides the optimum image sensitivity for extracting cores" (Methods)
- smoothing: _not stated_
- final beam: 0.37'' x 0.53''  
  > "0.37 ′′ ×0.53 ′′" (Methods)
- final rms: _not stated_

### Inherited from earlier work

- PPMAP dust temperature procedure  
  > "By applying the Bayesian PPMAP procedure, we obtain columndensity maps in different dust-temperature slices." (main text) [from Marsh et al. 2015 (cite 23)]
- Approximate radiation transport model for hot core temperatures  
  > "using an approximate radiation" (main text) [from Motte & André 2001 (26)]

### Not stated but needed to reproduce (our reading)

- Self-calibration solints, iterations and mask choices
- Clean threshold, cell size, image size, scales for multiscale
- Line-free channel selection for 65 MHz image
- getsources parameters (scales, thresholds) and visual-inspection criteria
- PPMAP setup and ten-core luminosity assignment details
- Gas-to-dust ratio used in kappa
- CMF fitting method and binning
- Calibrators

## Analysis recipe

1. **Image continuum**: CASA reduction, self-calibration, multiscale Clean of 12 m data; full-band 1.9 GHz and line-free 65 MHz images  
  > "applied the Clean algorithm with a robust weight of 0.5 and the MultiScale option" (Methods)
   - software: CASA
   - parameter: robust 0.5  
  > "robust weight of 0.5" (Methods)
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract cores**: getsources run simultaneously on both images; post-process by visual inspection to remove extended/elongated sources; 131 cores Sig>5, 94 with Sig>7  
  > "The final catalogue contains 131 sources with Sig > 5 (reliable)" (Methods)
   - software: getsources
   - fitting: _not stated_
   - validation: Compared with MRE-GaussClumps, classic clean and merged images  
  > "extraction methods ( getsources or" (Methods)
3. **Estimate dust temperature and core masses**: PPMAP temperature maps; radiation transport for ten hot cores; mass from flux with opacity correction  
  > "We then use the individual luminosities" (main text)
   - software: PPMAP
   - assumption: kappa1.3mm = 0.01 cm2/g, d = 5.5 kpc, mu=2.8  
  > "d = 5.5 kpc is the distance to the core" (Methods)
   - fitting: _not stated_
   - validation: Absolute masses uncertain by factor of a few, relative ~50%  
  > "relative values between cores to be uncertain by ∼ 50%" (Methods)
4. **Completeness and CMF fit**: Ten Monte-Carlo simulations with 2,000 synthetic cores for completeness; power-law fits to differential and cumulative CMF above 1.6 Msun; 100,000 MC runs for mass-error slope uncertainty  
  > "Monte-Carlo simulations (with 100,000 runs) show that the mass uncertainties correspond to" (Methods)
   - software: getsources, CASA simulator
   - fitting: _not stated_
   - validation: Tests in Supplementary Table 2  
  > "Supplementary Table 2 lists the major tests performed to evaluate the uncertainty of CMF fit." (Methods)

## Software

- **CASA** 4.3.1: data reduction, imaging, simulator  
  > "Data were reduced with the CASA 4.3.1 software" (Methods)
- **getsources** v1.140127: core extraction  
  > "Compact sources were extracted using getsources (v1.140127)" (Methods)
- **PPMAP** : dust temperature and column density maps  
  > "By applying the Bayesian PPMAP procedure" (main text)
- **MRE-GaussClumps** : alternative core extraction  
  > "T.Cs. ran MRE-GaussClumps" (Author Contributions)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of cores | 131 (94 with Sig>=7) | not stated | cores | 2 | the 131 cores returned by getsources, of which 94 are deemed to be very robust |
| 90% completeness | ~1.6 Msun (0.8 outskirts; 4.5 main filament) | ±0.1 | Msun | 4 | ∼ 1.6 ± 0.1 M ⊙ where most cores lie |
| Cumulative CMF slope | -0.96 | ±0.02 (1σ); ±0.13 (5σ global) | dimensionless | 4 | γ cumul ≃−0.96 ± 0.02 |
| Differential CMF slope | -0.90 | ±0.06 | dimensionless | 4 | γ diff ≃−0.90 ± 0.06 |
| Core masses range | ~1 to ~100 | factor of a few absolute | Msun | 3 | masses ranging from ∼ 1 M ⊙ to ∼ 100 M ⊙ |

## Qualitative findings

- Massive cores are over-represented relative to IMF expectations; mapping from CMF to IMF may not be self-similar  
  > "our results imply that the mapping from the CMF to the IMF is not statistically self-similar" (main text)

## Claim tuples

- H: The CMF in W43-MM1 has the same slope as the high-mass IMF | E: Core extraction in 1.3 mm ALMA mosaic, masses from fluxes and temperatures, power-law fit | R: gamma_cumul = -0.96 ± 0.13 vs IMF -1.35 | F: CMF is markedly flatter than the IMF | **supported**
- H: The result is robust to systematics | E: Varied temperature, opacity, extraction, reduction, completeness | R: All slopes remain shallower than -1.35 (-0.90 to -1.10) | F: Flat CMF is robust | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Scenarios A, B1, B2 judged hard to justify or unlikely  
  > "this seems unlikely, because it would require the low-mass period to be nearly ten times longer" (main text)
- How they decided it was enough: _not stated_
- Limitation (authors): Core boundedness of lower-mass cores uncertain; absolute masses uncertain by factor of a few  
  > "the status of lower-mass cores would benefit from further investigation" (main text)
- Caveat (inferred, ours): Single region; cores are not shown bound for all masses
- Caveat (inferred, ours): Mass depends on assumed kappa and temperatures
- Caveat (inferred, ours): Flux filtering by interferometer may bias low-mass cores
- Caveat (inferred, ours): Unresolved multiplicity in massive cores

## Reproducibility

- Data public (paper): Data available on request; ALMA project cited  
  > "are available from the corresponding authors (F.M., T.N., or F.L) upon reasonable request" (Data Availability)
- Products in archive: _not stated_
- Missing: Self-cal and clean parameters
- Missing: getsources configuration
- Missing: PPMAP inputs
- Missing: Core catalogue only partly reproducible without these
- Data volume (inferred): ~100-300 GB for 33-field mosaic raw data
- Score (inferred): 5/5, Core catalog table and key steps given, but many processing parameters and getsources settings are missing.
- Rediscovery candidate: no, Recipe incomplete (extraction and temperature modelling details missing), though data are in archive.

## Links

- Method: Men'shchikov et al. 2012 (cite 20) (getsources algorithm)
- Method: Marsh et al. 2015 (cite 23) (PPMAP)
- Companion: Louvet et al. 2014 (earlier W43-MM1 ridge study)
- Related: Herschel Gould Belt Survey

## Checks

```json
{
 "quotes": 56,
 "quotes_ok": 56,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 44,
  "rate": 0.611
 },
 "evidence_ok": true
}
```
