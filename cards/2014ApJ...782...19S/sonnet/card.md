# The SCUBA-2 Cosmology Legacy Survey: Ultraluminous Star-forming Galaxies in a z = 1.6 Cluster

`2014ApJ...782...19S` | The Astrophysical Journal 2014 | first author: Smail, Ian | arXiv: 1312.3329 | DOI: 10.1088/0004-637X/782/1/19

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies, galaxy_clusters_and_sz
- Question: How much obscured star formation is there in the z=1.62 cluster Cl 0218.3-0510 and in which environments do the ultraluminous star-forming galaxies lie?  
  > "The goal of this work is therefore is to build upon these earlier studies by undertaking a survey of the far-infrared and submm emission from luminous star-forming galaxies within the cluster and its surroundings" (Introduction)
- Target **Cl 0218.3-0510**: coordinates _not stated_; z/distance z = 1.62  
  > "We analyse new SCUBA-2 submillimeter and archival SPIRE far-infrared imaging of a $z=$ 1.62 cluster, Cl 0218.3$-$0510" (abstract); distance from spectroscopic redshifts of members (z=1.61-1.66 range)  
  > "We analyse new SCUBA-2 submillimeter and archival SPIRE far-infrared imaging of a $z=$ 1.62 cluster, Cl 0218.3$-$0510" (abstract)

## Data provenance

- ALMA projects: 2012.1.00090.S
- bands: Band 7 (870 um) continuum  
  > "These Band 7 (870 $\mu$m) continuum observations reach 1-$\sigma$ depths of $\sim$ 0.2 mJy" (2.5 Matching)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: 1-sigma ~0.2 mJy  
  > "These Band 7 (870 $\mu$m) continuum observations reach 1-$\sigma$ depths of $\sim$ 0.2 mJy" (2.5 Matching)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Cycle 1 program imaging thirty bright S2CLS UDS submm sources; source #37 covered by chance  
  > "was included in a high-priority Cycle 1 ALMA program to image the thirty bright submm sources from the S2CLS map of the UDS" (2.5 Matching)
- Other facility **SCUBA-2/JCMT**: 850 um imaging from S2CLS, 97 sources  
  > "We detect 97 discrete point sources above this significance within the survey area used in this analysis" (2.1 SCUBA-2)
- Other facility **Herschel SPIRE (HerMES)**: 250-500 um maps  
  > "SPIRE 250- 350- and 500-$\mu$m observations of the UDS were taken as part of the *Herschel* Multi-tiered Extra-galactic Survey (HerMES)" (2.3 SPIRE/Herschel)
- Other facility **VLA UDS20 and Spitzer MIPS/IRAC (SpUDS)**: 1.4 GHz and 24 um counterpart catalogs  
  > "We therefore use catalogs of sources detected at 1.4 GHz with the VLA and at 24 $\mu$m using *Spitzer*." (2.2 Radio and MIPS 24um)
- External data: Photometric redshifts for UDS  
  > "The photometric redshifts used here are described in Hartley et al. (2013)" (2.4.3) [from Hartley et al. (2013)]
- External data: [OII] emitter catalog  
  > "We employ the Tadaki et al. catalog, but with a simple optical/near-infrared color-selection applied" (2.4.1) [from Tadaki et al. (2012)]
- External data: Cluster mass 7.7e13 Msun  
  > "we adopt the cluster mass estimate from Pierre et al. (2012) of 7.7$\times$10$^{13}$ M$_\odot$" (3.2) [from Pierre et al. (2012)]
- Simulation/model as data: Millennium database with Font et al. (2008) galaxy formation prescription  
  > "galaxies taken from the Millennium database (Springel et al. 2005), using the prescription for galaxy evolution from Font et al. (2008)" (3.1)

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

- Full details of the ALMA program and data processing  
  > "Full details of the ALMA program are given in Simpson et al. (in prep)." (2.5 Matching) [from Simpson et al. (in prep)]
- SPIRE deblending algorithm  
  > "it is described in full in Swinbank et al. (2014)" (2.3 SPIRE/Herschel) [from Swinbank et al. (2014)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration, CASA version, imaging parameters and beam
- ALMA source flux density and position of #37
- Coordinates of cluster centre

## Analysis recipe

1. **check SCUBA-2 counterpart identification with ALMA**: ALMA Band 7 continuum image of SCUBA-2 source #37 used to confirm the MIPS/radio counterpart  
  > "confirm that the MIPS/radio source with a photometric redshift of $z_{\rm phot}=$ 1.67 we had identified is indeed a bright submm galaxy" (2.5 Matching)
   - fitting: _not stated_
   - validation: Serves as test of the identification process  
  > "This provides a useful test of the reliability of the identification process used in our analysis." (2.5 Matching)

## Software

- **smurf** : SCUBA-2 map-making  
  > "reduced using the map-maker from the smurf package" (2.1 SCUBA-2)
- **eazy** : photometric redshifts  
  > "The photometric redshift estimates are based on eazy" (2.4.3)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Median Lbol of 22 FIR/submm-detected members | 1.7e12 | 0.3e12 | Lsun | 0 | $L_{\rm bol}=(1.7\pm 0.3)\times 10^{12}$ L$_\odot$ and a dust temperature of $T_{\rm d}=$ 33.0$\pm$1.2 K |
| Mass-normalised SFR within 2 Mpc | 800 | 500 | 1e-14 Msun^-1 yr^-1 | 0 | we estimate a mass-normalised SFR within the central 2-Mpc of 800$\pm$500 yr$^{-1}$ |

## Qualitative findings

- Most active members lie in intermediate/low density regions, not densest cores  
  > "the highest density regions in this $z=$ 1.6 structure are devoid of the most actively star-forming galaxies" (3.3)

## Claim tuples

- H: Is the SCUBA-2 identification via MIPS/radio counterpart reliable? | E: Compared with ALMA Band 7 imaging of one source | R: ALMA confirms bright submm galaxy at MIPS/radio position | F: The identification method works for this source | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Only one source covered by ALMA; blending of multiple SMGs possible  
  > "interferometric studies of single-dish submm sources have shown that a significant fraction of these comprises blends of multiple, fainter sources" (3.1)
- Caveat (inferred, ours): ALMA used for a single source; no quantitative ALMA result given
- Caveat (inferred, ours): Interloper contamination of photometric members is 40-60%

## Reproducibility

- Data public (paper): Data obtainable from archives including ALMA  
  > "The data used in this paper can be obtained from the JCMT, UKIRT, *Herschel*, *Spitzer*, VLA, ALMA and Subaru data archives." (Acknowledgments)
- Products in archive: _not stated_
- Missing: ALMA reduction details deferred to Simpson et al. in prep
- Data volume (inferred): small for ALMA part (one field)
- Score (inferred): 2/5, ALMA is a minor check; details deferred.
- Rediscovery candidate: no, ALMA result is qualitative and recipe is deferred.

## Links

- Method: Swinbank et al. (2014) (SPIRE deblending)
- Companion: Simpson et al. (in prep) (ALMA program of S2CLS UDS sources)
- Related: SCUBA-2 Cosmology Legacy Survey
- Related: HerMES
- Related: UKIDSS UDS

## Checks

```json
{
 "quotes": 27,
 "quotes_ok": 27,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 2,
 "numeric_problems": 0,
 "fill": {
  "facts": 59,
  "stated": 22,
  "rate": 0.373
 },
 "evidence_ok": true
}
```
