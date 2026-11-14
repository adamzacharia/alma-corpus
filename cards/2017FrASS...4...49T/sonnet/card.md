# Fast-growing SMBHs in Fast-growing Galaxies, at High Redshifts: the Role of Major Mergers as Revealed by ALMA

`2017FrASS...4...49T` | Frontiers in Astronomy and Space Sciences 2017 | first author: Trakhtenbrot, Benny | arXiv: - | DOI: 10.3389/fspas.2017.00049

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, high_z_galaxies
- Question: Are fast-growing z≃4.8 SMBH host galaxies interacting with companion galaxies (major mergers), as probed by ALMA [C II] and continuum?  
  > "Here we describe a pilot study with ALMA that aims to identify major galaxy-galaxy interactions among a sample of six fast-growing SMBHs at z ≃ 4.8." (1. INTRODUCTION)
- Target **SDSS J092303.53+024739.5 (J0923)**: coordinates J092303.53+024739.5  
  > "SDSS J092303.53+024739.5 (z QSO = 4.6589; J0923 hereafter)" (3. RESULTS); z/distance z = 4.6589  
  > "SDSS J092303.53+024739.5 (z QSO = 4.6589; J0923 hereafter)" (3. RESULTS); distance from _not stated_
- Target **J1341**: coordinates _not stated_; z/distance z ≃ 4.8 sample  
  > "This is exemplified in the system J1341, which has SFR ≃3,000 M ⊙ yr [−][1]" (4. DISCUSSION AND CONCLUSION); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.01153.S
- bands: Band 7, [C II] and adjacent continuum (~345 GHz)  
  > "The ALMA band-7 observations were designed to detect and resolve, at kpc scales, the emission from the prominent" (2. SAMPLE AND ALMA OBSERVATIONS)
- frequencies and spectral setup: four windows of 1,875 MHz (~1,650 km/s), resolution ~30 km/s  
  > "The chosen spectral setup provided four windows, each covering 1,875 MHz (∼1,650 km s [−][1] ), at a resolution of ∼30" (2. SAMPLE AND ALMA OBSERVATIONS)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C34-4  
  > "We used the extended C34-4 configuration of ALMA" (2. SAMPLE AND ALMA OBSERVATIONS)
- baselines: _not stated_
- angular resolution: ~0.3" at 330 GHz (~2 kpc)  
  > "providing a resolution of ∼0. [′′] 3 at 330 GHz." (2. SAMPLE AND ALMA OBSERVATIONS)
- max recoverable scale: _not stated_
- sensitivity: (4.2–9.2)×10^-2 mJy/beam rms  
  > "The resulting limiting flux densities were F ν ∼ (4.2–9.2)×10 [−][2] mJy/beam" (2. SAMPLE AND ALMA OBSERVATIONS)
- time on source: 11 to 54 min  
  > "On-source integrations lasted between 11 and 54 min" (2. SAMPLE AND ALMA OBSERVATIONS)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: [C II] 2P3/2-2P1/2 (157.74 µm)
- Other facility **Herschel/SPIRE**: Prior FIR detections and stacking SFR estimates  
  > "previous Herschel/SPIRE detection, suggesting SFR >1,000 M ⊙ yr [−][1]" (abstract)
- Other facility **Spitzer**: Companions not detected  
  > "The companion galaxies detected with ALMA were not seen in" (4. DISCUSSION AND CONCLUSION)
- External data: Black hole masses and Eddington ratios of the z≃4.8 sample  
  > "the sample covers a rather limited range in these" (2. SAMPLE AND ALMA OBSERVATIONS) [from Trakhtenbrot et al., 2011 (T11)]
- External data: Herschel FIR-bright/faint SFRs  
  > "(“FIR-bright” systems; see Netzer" (2. SAMPLE AND ALMA OBSERVATIONS) [from Netzer et al., 2014, 2016]
- External data: FIR SED templates  
  > "most sources are consistent with the FIR SED templates of Chary and Elbaz (2001)." (3.1. Quasar Hosts) [from Chary and Elbaz (2001)]

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

- Detailed analysis and assumptions deferred to T17  
  > "The reader is referred to T17 for a detailed discussion of our analysis and assumptions." (3. RESULTS) [from Trakhtenbrot et al., 2017 (T17)]
- Analysis choices motivated by z≳5 quasar sub-mm studies  
  > "many of the choices we made through the analysis of the ALMA data were motivated by recent sub-mm studies of z ≳ 5" (3. RESULTS) [from Wang et al., 2013; Willott et al., 2015; Venemans et al., 2016]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration procedure
- imaging parameters (weighting, cell, masking)
- continuum-subtraction channels
- how [C II] size and FWHM were measured
- how SFR was derived from LFIR (conversion)
- companion-flux correction for Herschel data

## Analysis recipe

1. **FIR luminosity and SFR**: Fit gray-body SED to ALMA continuum, integrate 8–1,000 µm, convert to SFR  
  > "By combining the new ALMA continuum measurements and the assumed FIR SEDs, we estimate (spatially integrated) total" (3.1. Quasar Hosts)
   - assumption: Gray-body Td = 47 K, β = 1.6 (up to ~60 K for some)  
  > "namely a gray-body with dust temperature T d = 47 K and β = 1.6." (3.1. Quasar Hosts)
   - fitting: _not stated_
   - validation: Compared with Herschel stacking  
  > "the ALMA continuum measurements for the FIR-faint sources, are consistent with the" (3.1. Quasar Hosts)
2. **Dynamical masses**: Inclined rotating disk: Mdyn = 9.8e8 (D/kpc)(FWHM/100 km/s)^2 sin^-2(i) Msun  
  > "We therefore assume a simple model of an inclined rotating disk for the [C II ]-emitting ISM in the" (3.1. Quasar Hosts)
   - assumption: Inclination from major-to-minor axis ratio of [C II] region  
  > "The inclination of each system is estimated from the spatial" (3.1. Quasar Hosts)
   - fitting: _not stated_
   - validation: _not stated_

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum flux density, 345 GHz (quasar hosts) | 1.6–18.5 | not stated | mJy | 0 | F ν ≃ 1.6–18.5 mJy |
| Host SFR | 190–3,500 | not stated | Msun/yr | 1 | SFR ∼ 190–3,500 M ⊙ yr [−][1] |
| Host dynamical mass | (3.7–7.4)e10 | not stated | Msun | 2 | M dyn ≃ (3.7–7.4) × 10 [10] M ⊙ |
| Companion separation | ~14–45 | not stated | kpc | 0 | These companions are separated by ∼14–45 kpc |
| Companion dynamical mass | (2.1–10.7)e10 | not stated | Msun | 2 | M dyn ≃ (2.1–10.7) × 10 [10] M ⊙ |

## Qualitative findings

- Three of six quasars have spectroscopically confirmed companions; others show rotation-dominated gas  
  > "We robustly detect companion galaxies for three of the" (3.2. Companion Galaxies)

## Claim tuples

- H: Major mergers drive rapid early SMBH growth | E: ALMA band 7 [C II] and continuum of six z≈4.8 quasars | R: Companions in 3/6, mass ratios ≲2:1 | F: Mergers may be important, with over-dense environments | **supported**
- H: High-SFR hosts are the merging ones | E: Compare companions with Herschel FIR classes | R: 2 of 3 companions near FIR-faint; 2 of 3 FIR-bright lack companions | F: Other processes also fuel growth; diversity | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Larger sample needed; advanced mergers could be unresolved  
  > "a larger sample is needed to clarify which of" (4. DISCUSSION AND CONCLUSION)
- Caveat (inferred, ours): Short summary; small sample of six
- Caveat (inferred, ours): Dynamical masses depend on assumed disk model and inclination

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: All processing details (deferred to T17)
- Data volume (inferred): tens of GB
- Score (inferred): 2/5, Brief proceedings summary; recipe deferred to T17.
- Rediscovery candidate: no, Recipe incomplete here.

## Links

- Companion: Trakhtenbrot et al. 2017, ApJ 836:8 (Full presentation of the study)
- Related: Decarli et al. 2017 z~6 quasar ALMA study

## Checks

```json
{
 "quotes": 34,
 "quotes_ok": 34,
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
  "facts": 63,
  "stated": 24,
  "rate": 0.381
 },
 "evidence_ok": true
}
```
