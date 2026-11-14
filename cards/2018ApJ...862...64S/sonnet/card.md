# Deciphering the Activity and Quiescence of High-redshift Cluster Environments: ALMA Observations of Cl J1449+0856 at z = 2

`2018ApJ...862...64S` | The Astrophysical Journal 2018 | first author: Strazzullo, V. | arXiv: 1806.06856 | DOI: 10.3847/1538-4357/aacd10

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type observational_alma_primary

## Science

- Fields: galaxy_clusters_and_sz, high_z_galaxies
- Question: How much obscured star formation and how much quiescence is there in the core of the z=2 cluster ClJ1449, and what do ALMA 870um continuum and CO(4-3) say about member galaxies and the forming BCG?  
  > "the quantification of star formation occurring in the core of ClJ1449, for the first time using deep, high-resolution star formation probes not biased by dust attenuation" (1 Introduction)
- Target **ClJ1449+0856**: coordinates _not stated_; z/distance z=2  
  > "the galaxy cluster ClJ1449+0856 (cite: gobat2011) at $z=2$" (1 Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00885.S, 2015.1.01355.S
- bands: Band 7 (870um) mosaic; Band 4 pointing (CO(4-3)); Band 3 (CO(3-2)) not used  
  > "The Cycle 1 program obtained a band 7 mosaic probing 870$\mu$m continuum" (2 Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Band 7 beam ~1.4" x 0.6"; Band 4 beam ~1.2" x 1"  
  > "The synthesised beam of FWHM$\sim 1.4$”$\times 0.6$” is well suited" (2 Observations); "The synthesised beam FWHM is $\sim 1.2$”$\times 1$”." (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: Band 7 rms ~70 uJy/beam; Band 4 rms 10 mJy km/s over 100 km/s  
  > "The map has an rms sensitivity of $\sim$70 $\mu$Jy/beam" (2 Observations); "The rms is 10 mJy km/s over 100 km/s" (2 Observations)
- time on source: Band 7 ~2.3 h; Band 4 ~2 h  
  > "for a total on-source time of $\sim2.3$h" (2 Observations); "for a total on-source time of $\sim2$h" (2 Observations)
- observing dates: Cycle 1 completed December 2014; Cycle 3 completed May 2016  
  > "Observations were completed in December 2014" (2 Observations); "Observations were completed in May 2016" (2 Observations)
- pi or archival as stated: _not stated_
- Line: CO 4-3 (not stated)
- Other facility **HST**: F105W/F140W imaging and grism spectroscopy of cluster galaxies  
  > "**HST** programs GO-11648 and GO-12991" (Acknowledgments)
- External data: Flux measurements of 870um continuum and CO(4-3) from C18  
  > "All the analysis and results below are based on these measurements as described in C18." (2 Observations) [from Coogan et al. 2018 (cite: coogan2018)]
- External data: Blank-field 870um source counts  
  > "higher than expected from blank-field counts (cite: oteo2016)" (3 Overdensity of 870$\mu$m sources) [from (cite: oteo2016)]
- External data: Field GOODS-S control sample photometry, masses, photo-z  
  > "we used the (cite: guo2013) photometry, and stellar masses, photometric redshifts and model SEDs from (cite: schreiber2015; pannella2015)" (4.1.1 Color distribution) [from (cite: guo2013; schreiber2015; pannella2015)]

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

- ALMA data reduction, continuum and line flux measurements, line searches  
  > "We refer the reader to C18 for a full, extensive summary of the *ALMA* observations" (2 Observations) [from C18 (cite: coogan2018)]
- Red cluster sample, colours and stellar masses  
  > "In S16 we investigated the optically red (F105-F140$\gtrsim$1) cluster galaxy population" (4.2 The ALMA view) [from S16 (cite: strazzullo2016)]

### Not stated but needed to reproduce (our reading)

- Reduction/calibration and imaging details (CASA version, weighting, cleaning) are only in C18
- Positions and catalogue of known cluster members
- Per-source flux values for A1-A6 and members
- Flux-boosting correction recipe for CO(4-3)
- CO(5-4)/CO(4-3) ratio values and CO(5-4)-LIR relation coefficients adopted
- Conversion from 870um flux to LIR with Bethermin SEDs (template details)

## Analysis recipe

1. **Count 870um sources and compute overdensity**: Compare six S/N>4 sources >0.5 mJy with blank-field counts; assess lensing magnification with NFW halo  
  > "assuming a spherical NFW halo of mass $6\times10^{13}$ M$_{\odot}$ and a concentration in the range $c=1-5$" (3 Overdensity of 870$\mu$m sources)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive IR luminosities and SFRs**: LIR from 870um flux via MS/SB SEDs and from CO(4-3) via CO SLED and CO(5-4)-LIR relation; SFR via Kennicutt 1998  
  > "The IR luminosity estimate L$_{IR,870\mu m}$ was derived from the measured 870$\mu$m flux using the average MS and starburst (SB) SEDs" (4.1 Dusty star formation)
   - assumption: Salpeter IMF; BzK and ULIRG CO SLEDs  
  > "Stellar masses and star formation rates are quoted for a (cite: salpeter1955) IMF." (1 Introduction)
   - fitting: _not stated_
   - validation: Consistency of the two LIR estimates; A4 and A5 inconsistent hence interlopers  
  > "the consistency of L$_{IR,870\mu m}$ and L$_{IR,CO43}$, besides ensuring cluster membership of the 870$\mu$m detections, also confirms the reliability of the SFR estimates." (4.1 Dusty star formation)
3. **Compare colours with field**: 1000 random draws from GOODS-S control field with same mass/SFR limits  
  > "Considering 1000 realizations of galaxy samples of the same size as the cluster samples" (4.1.1 Color distribution)
   - fitting: _not stated_
   - validation: _not stated_

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total SFR of cluster members | ~700 | ±100 | Msun/yr | 2 | corresponding to a total SFR of $\sim700\pm100$ M$_{\odot}$/yr |
| Total LIR | 4.3e12 | ±0.5e12 | Lsun | 2 | total L$_{IR}\sim4.3\pm0.5\times10^{12}$L$_{\odot}$ |
| SFR/Mhalo lower limit | 1300 | ±400 | Msun/yr/1e14 Msun | 2 | of $\sim$1300$\pm$400 M$_{\odot}$ yr$^{-1}$ / 10$^{14}$ M$_{\odot}$ |
| SFR volume density | 1.0e4 | ±0.1e4 | Msun/yr/Mpc^3 | 2 | SFR volume density $\sim1.0\pm0.1\times10^{4}$ M$_{\odot}$ yr$^{-1}$Mpc$^{-3}$ |

## Qualitative findings

- Of six bright 870um sources only A1, A2, A6 are confirmed members; A4 and A5 are likely interlopers  
  > "Among the six bright 870$\mu$m sources, only A1, A2 and A6 are thus confirmed to belong to the cluster." (3 Overdensity of 870$\mu$m sources)

## Claim tuples

- H: Is the cluster core overdense in mm sources? | E: Count 870um sources vs blank-field counts | R: Overdensity ~10 (>1 mJy), ~6 (>0.5 mJy) | F: Core is strongly overdense in dusty star formers | **supported**
- H: Are the brightest 870um sources cluster members? | E: CO(4-3) and other line searches | R: No lines detected for A4, A5 | F: Likely interlopers | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Small field and low-number statistics; field comparison selection not equivalent  
  > "the very small number statistics of the *ALMA*-detected sample in the cluster" (4.1.1 Color distribution)
- Caveat (inferred, ours): Interloper conclusion rests on non-detection of lines at unprobed redshifts
- Caveat (inferred, ours): SFR conversions depend on assumed SEDs and CO SLED

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Flux measurements are in C18, not this paper
- Missing: Calibration and imaging details
- Data volume (inferred): ~10-50 GB
- Score (inferred): 2/5, Paper relies on companion paper C18 for all ALMA processing and flux measurements.
- Rediscovery candidate: no, Recipe incomplete; measurements inherited from C18.

## Links

- Method: Coogan et al. 2018 (cite: coogan2018) (ALMA reduction and flux measurements)
- Companion: (cite: strazzullo2016) (Photometric red galaxy sample (S16))

## Checks

```json
{
 "quotes": 34,
 "quotes_ok": 34,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 61,
  "stated": 20,
  "rate": 0.328
 },
 "evidence_ok": true
}
```
