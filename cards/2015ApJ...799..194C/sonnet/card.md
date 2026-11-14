# An ALMA Survey of Submillimeter Galaxies in the Extended Chandra Deep Field South: Near-infrared Morphologies and Stellar Sizes

`2015ApJ...799..194C` | The Astrophysical Journal 2015 | first author: Chen, Chian-Chou | arXiv: 1412.0668 | DOI: 10.1088/0004-637X/799/2/194

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies
- Question: What are the rest-frame optical/near-IR stellar morphologies, Sérsic indices and sizes of ALMA-identified SMGs, and are they mergers or disks?  
  > "to study their stellar morphologies and sizes" (abstract)
- Target **ALESS SMGs in ECDFS (48 MAIN sample)**: coordinates per-source RA/Dec in Table 1 (from Hodge et al. 2013)  
  > "a flux-limited sample of 126 submillimeter sources in the $0.5^{\circ} \times 0.5^{\circ}$ Extended *Chandra* Deep Field South (ECDFS)" (1 Introduction); z/distance photometric z, mean z = 2.1 for z = 1-3 SMGs  
  > "a flux-limited sample of 126 submillimeter sources in the $0.5^{\circ} \times 0.5^{\circ}$ Extended *Chandra* Deep Field South (ECDFS)" (1 Introduction); distance from photometric redshifts from Simpson et al. 2014 (hyperz)  
  > "a flux-limited sample of 126 submillimeter sources in the $0.5^{\circ} \times 0.5^{\circ}$ Extended *Chandra* Deep Field South (ECDFS)" (1 Introduction)

## Data provenance

- ALMA projects: _none stated_
- bands: ALMA Cycle 0 Band 7 (870 um)  
  > "We have undertaken an ALMA Cycle 0 band 7 (870 $\mu$m) study of the first large sample of submillimeter sources" (1 Introduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **HST/WFC3 H160**: Deep H160 imaging of 48 ALESS SMGs (15 pointings, 2 orbits each; PID 12866) plus CANDELS/HUDF09 images  
  > "There were 15 pointings and the exposure time was two orbits per pointing." (2.1 Hubble Space Telescope Observations)
- Other facility **Spitzer/IRAC 3.6 um**: Astrometric reference frame for HST images  
  > "we aligned the $H_{160}$-band images to the 3.6-$\mu$m image of the full ECDFS from *Spitzer*/IRAC" (2.1 Hubble Space Telescope Observations)
- Other facility **MUSYC catalog**: Comparison field galaxy sample with photometric redshifts  
  > "We exploit the Multi-wavelength Survey by Yale-Chile (MUSYC) catalog" (2.3 Non-SMG comparison sample)
- External data: ALESS MAIN/SUPPLEMENTARY catalogs and ALMA positions/fluxes  
  > "The full ALESS sample was presented in (cite: Hodge:2013lr), which defined a robust “MAIN” catalog of 99 SMGs" (2 Sample, Observations, and Data Reduction) [from (cite: Hodge:2013lr)]
- External data: Photometric redshifts of ALESS SMGs  
  > "we give the photometric redshifts derived by (cite: Simpson:2014aa)" (Table 1) [from (cite: Simpson:2014aa)]
- External data: 250-870 um photometry used to derive LIR  
  > "we used the 250–870 $\mu$m photometry from (cite: Swinbank:2014ul) to derive infrared luminosities" (2.2 Our sample) [from (cite: Swinbank:2014ul)]

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

- ALMA data reduction, source catalog and positional errors taken from ALESS papers  
  > "sky positions in right ascension (R.A.) and declination (Dec.), both J2000, adopted from (cite: Hodge:2013lr)" (Table 1) [from (cite: Hodge:2013lr)]
- Common astrometric frame (IRAC 3.6 um)  
  > "the common astrometric frame adopted in (cite: Simpson:2014aa)" (2.1 Hubble Space Telescope Observations) [from (cite: Simpson:2014aa)]

### Not stated but needed to reproduce (our reading)

- ALMA reduction details (CASA version, imaging) not given; relies on Hodge et al. 2013
- HST exposure-level reduction parameters for AstroDrizzle
- Exact SExtractor configuration beyond detection threshold
- GALFIT masks and initial guesses per source
- Details of visual classification consensus procedure

## Analysis recipe

1. **Astrometric alignment and source extraction of HST images**: Align H160 images to IRAC 3.6 um via SExtractor catalogs; extract sources with 16 connected 1-sigma pixels, MAG_AUTO fluxes  
  > "set the detection threshold to be 16 connecting 1 $\sigma$ pixels. We adopted the automatic aperture magnitudes (MAG_AUTO) for the flux measurements." (2.1 Hubble Space Telescope Observations)
   - software: SExtractor
   - fitting: _not stated_
   - validation: Random 3.6 um vs H160 offsets show no systematic offset, scatter ~0.16 arcsec  
  > "we found no systematic offset and a scatter of $\sim$ 0$\ensuremath{''}$16 in both R.A. and Dec." (2.1 Hubble Space Telescope Observations)
2. **Visual morphological classification**: Four team members classified H160 morphologies into disk, spheroid, irregular, unresolved, unclassified plus interaction/companion tags; median fractions with bootstrapped errors  
  > "we derived from their classifications the median fraction of all main morphological classes as well as the bootstrapped errors" (3.1 Visual Classifications)
   - fitting: _not stated_
   - validation: Compared with Kartaltepe et al. 2012 classifications and a comparison field sample  
  > "We compare our classifications to those from (cite: Kartaltepe:2012aa)" (4.1 Visual Classifications)
3. **Sérsic profile fitting**: 2D Sérsic fits of each H160 component with GALFIT using TinyTim/stacked-star PSFs, SExtractor-based masks, iteratively varied mask scaling R=3-6; index fixed to 1 or 4 for ~15% of components  
  > "we fixed the Sérsic index to either 1 or 4 (depending on the prefered index early in the iteration process) on a small number of components." (3.2 galfit)
   - software: GALFIT, TinyTim, SExtractor
   - parameter: PSF oversampling factor of 3 for TinyTim  
  > "The PSF profiles were modelled with a pixel resolution three times higher than that of the original *HST* images (oversampling factor of 3)." (3.2 galfit)
   - fitting: GALFIT chi-squared minimisation with sigma maps; CANDELS/HUDF09 sigma scaled by ~40-50% to give unit variance  
  > "derived correction factors of typically $\sim$ 40–50%" (3.2 galfit)
   - validation: Noise added to high chi2 systems gave consistent solutions; fixed-n sources do not change conclusions  
  > "by adding noises into the thumbnails for these high $\chi^2_\nu$ systems and rerunning the galfit analysis we found consistent best fit solutions" (4.2 Sérsic index and Effective Radius)
4. **Median sizes, Sérsic index and positional offsets**: Median r_e and n for components with H160<=24 mag, bootstrapped errors; H160-ALMA offsets and intrinsic scatter  
  > "if we only take components that have $H_{160} \leq$ 24, which should be complete for measured sizes up to $\sim$ 15 kpc" (4.2 Sérsic index and Effective Radius)
   - assumption: Every H160 component overlapping the ALMA beam is a counterpart; mean z = 2.1 for size selection line  
  > "In this analysis we have assumed that every $H_{160}$-band component which overlaps the ALMA synthesized beam is a counterpart of the ALESS SMG." (4.2 Sérsic index and Effective Radius)
   - fitting: _not stated_
   - validation: Repeated using only the H1 component of each SMG; medians unchanged  
  > "We found the median $r_e$ and $n$ unchanged" (4.2 Sérsic index and Effective Radius)

## Software

- **SExtractor** : Source extraction, photometry, segmentation masks  
  > "We used SExtractor (cite: Bertin:1996zr) to extract sources from our *HST* imaging" (2.1 Hubble Space Telescope Observations)
- **GALFIT** 3.0.5: Sérsic surface-brightness fitting  
  > "using the most recent version of GALFIT (v3.0.5, (cite: Peng:2010aa))" (3.2 galfit)
- **TinyTim** : Model PSFs for new WFC3 data  
  > "we first used TinyTim (cite: Krist:2011aa)**, a standard PSF simulation software package for *HST*,** to model the PSF profiles" (3.2 galfit)
- **AstroDrizzle** : HST pipeline drizzling  
  > "The data were processed through the standard pipeline reduction using AstroDrizzle." (2.1 Hubble Space Telescope Observations)
- **hyperz** : Photometric redshifts of ALESS SMGs  
  > "derived using the SED fitting code hyperz (cite: Bolzonella:2000aa)" (2.2 Our sample)
- **Astropy** : General analysis (acknowledged)  
  > "This research made use of Astropy, a community-developed core Python package for Astronomy" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| H160 detection rate of SMGs | 79 | 17% | percent | 1 | In total we detected 38 SMGs[^2], with a detection rate of 79 $\pm$ 17%. |
| Fraction with disturbed morphology (z=1-3) | 82 | 9% | percent | 2 | the percentage of SMGs with disturbed morphologies, meaning they are either irregular or have an interaction tag, is 82 $\pm$ 9%. |
| Comparison field disturbed fraction | 48 | 6% | percent | 2 | we found that only 48 $\pm$ 6% of the comparison far-infrared-faint field sample have disturbed morphologies |
| Median Sérsic index (H160<=24) | 1.2 | 0.3 | dimensionless | 3 | the median $n$ for those $H_{160}$-band components with $H_{160} \leq$ 24 mag is 1.2 $\pm$ 0.3 |
| Median effective radius (H160<=24) | 4.4 | +1.1/-0.5 | kpc | 4 | we obtained a median $r_e$ of 4.4$^{+1.1}_{-0.5}$ kpc |
| Intrinsic scatter of H160-ALMA offset | 0.40 | 0.05 | arcsec | 4 | We also measured an average intrinsic scatter of $0.40\ensuremath{''}\pm0.05\ensuremath{''}$. |

## Qualitative findings


## Claim tuples

- H: Are SMGs mainly undisturbed disks or mergers in stellar light? | E: Visual classification of H160 images of 29 SMGs at z=1-3 versus a field comparison sample | R: 82±9% irregular or interacting versus 48±6% in the field | F: Most SMGs have disturbed stellar morphologies despite disk-like Sérsic indices | **supported**
- H: Are dusty star-forming regions co-located with the stellar light? | E: Compare GALFIT component positions with ALMA 870 um positions | R: Scatter 0.40±0.05 arcsec versus expected 0.24 arcsec | F: Dust and stellar emission are displaced | **supported**
- H: Are z=2-3 SMGs progenitors of z~2 quiescent galaxies? | E: Compare SMG sizes and Sérsic indices with literature quiescent galaxies | R: SMGs larger with lower n | F: A major structural transformation, likely via mergers, is needed | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Non-parametric CAS/Gini/M20 cannot separate irregulars from disks, motivating visual classification plus GALFIT  
  > "This caveat on non-parametric analysis motivates the need to first conduct a visual inspection of the morphology of SMGs" (3 Methodology)
- How they decided it was enough: _not stated_
- Limitation (authors): Size bias toward small r_e near the detection limit; counterpart assumption lacks redshift confirmation  
  > "there is a size bias toward smaller $r_e$ when detecting components close to the detection limit" (4.2 Sérsic index and Effective Radius)
- Caveat (inferred, ours): Visual classification is subjective and not blind to the SMG status
- Caveat (inferred, ours): H160 at z>2 samples rest-frame UV, so the morphological K-correction matters
- Caveat (inferred, ours): Photometric redshifts uncertain for several sources
- Caveat (inferred, ours): The merger conclusion is indirect; there is no kinematic test

## Reproducibility

- Data public (paper): HST data from program 12866 and CANDELS/HUDF09; ALMA data acknowledged as 2011.1.00294.S  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.1.00294.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Per-source GALFIT masks and starting parameters
- Missing: Visual classification individual results
- Missing: ALMA positions come from Hodge et al. 2013, which must be obtained separately
- Data volume (inferred): ~5-20 GB (HST images; ALMA only used via catalog)
- Score (inferred): 3/5, HST data are public and the Table 1 results are given, but the visual classification is subjective and the GALFIT setup is only partly specified.
- Rediscovery candidate: no, ALMA data are used only through a published catalogue; the main results come from HST and a subjective visual classification.

## Links

- Method: (cite: Peng:2010aa) (GALFIT)
- Method: (cite: Hodge:2013lr) (ALESS ALMA survey catalog)
- Companion: (cite: Simpson:2014aa) (ALESS photometric redshifts)
- Companion: (cite: Swinbank:2014ul) (ALESS SEDs and infrared luminosities)
- Related: ALESS
- Related: LESS
- Related: CANDELS
- Related: HUDF09
- Related: MUSYC

## Checks

```json
{
 "quotes": 43,
 "quotes_ok": 43,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00294.S"
 ],
 "codes_printed_but_missing": [
  "2011.1.00294.S"
 ],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 33,
  "rate": 0.458
 },
 "evidence_ok": true
}
```
