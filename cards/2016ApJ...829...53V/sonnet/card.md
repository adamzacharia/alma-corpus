# A Giant Lyα Nebula in the Core of an X-Ray Cluster at Z = 1.99: Implications for Early Energy Injection

`2016ApJ...829...53V` | The Astrophysical Journal 2016 | first author: Valentino, Francesco | arXiv: 1605.03194 | DOI: 10.3847/0004-637X/829/1/53

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: galaxy_clusters_and_sz, high_z_galaxies
- Question: What powers and sustains a giant Lyα nebula in the core of the z=1.99 X-ray cluster CL J1449+0856, and how much energy do galaxy outflows inject into the ICM?  
  > "We investigate the possibility that cluster galaxies supply the required gas through outflows and we show that their total mass outflow rate matches the replenishment necessary to sustain the nebula." (abstract)
- Target **CL J1449+0856**: coordinates 14:49:13.670, +8:56:28.25 (X-ray centre)  
  > "CL J1449+0856 at $z=1.99$ (cite: gobat_2011; gobat_2013; strazzullo_2013)" (1 Introduction); "The X-ray source is centered on coordinates 14:49:13.670, +8:56:28.25 with a $1\sigma$ uncertainty on the position of $4^{\prime\prime}$" (2.3 Chandra X-ray observations); z/distance z = 1.99  
  > "CL J1449+0856 at $z=1.99$ (cite: gobat_2011; gobat_2013; strazzullo_2013)" (1 Introduction); "The X-ray source is centered on coordinates 14:49:13.670, +8:56:28.25 with a $1\sigma$ uncertainty on the position of $4^{\prime\prime}$" (2.3 Chandra X-ray observations); distance from previous work (G11, G13, S13); velocity dispersion gives z_sys=1.995  
  > "CL J1449+0856 at $z=1.99$ (cite: gobat_2011; gobat_2013; strazzullo_2013)" (1 Introduction); "The X-ray source is centered on coordinates 14:49:13.670, +8:56:28.25 with a $1\sigma$ uncertainty on the position of $4^{\prime\prime}$" (2.3 Chandra X-ray observations)

## Data provenance

- ALMA projects: 2012.1.00885.S
- bands: _not stated_
- frequencies and spectral setup: 870 μm continuum  
  > "or 870 $\mu$m continuum detection in ALMA maps applying a Main-Sequence galaxy template" (4.1 Gas replenishment through galaxy outflows)
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
- Other facility **Keck/LRIS**: NB3640 narrow-band imaging, 3.5 h, Lyα nebula detection; also V band  
  > "We observed CL J1449+0856 (Figure [1](#fig:rgb)) for 3.5 h with the narrow-band filter NB3640 installed in the blue arm of the Keck/LRIS camera on March 27, 2014" (2.1 The Lyα nebula detection)
- Other facility **Chandra**: ACIS-S 94.81 ks follow-up plus archival ACIS-I; cluster and AGN X-ray properties  
  > "In Cycle 16 we followed-up the field with the ACIS-S camera (aimpoint at CCD=7) for a nominal exposure of 94.81 ks in very faint mode." (2.3 Chandra X-ray observations)
- Other facility **VLT/FORS2**: U-band for continuum subtraction  
  > "combined the final narrow-band image with an aligned *U*-band frame from VLT/FORS2" (2.1 The Lyα nebula detection)
- External data: Main-Sequence galaxy template used to convert 870 μm flux to SFR  
  > "or 870 $\mu$m continuum detection in ALMA maps applying a Main-Sequence galaxy template (cite: magdis_2012)" (4.1 Gas replenishment through galaxy outflows) [from (cite: magdis_2012)]

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

- ALMA observations, reduction and analysis deferred to a forthcoming paper  
  > "ALMA observations, reduction and analysis will be presented in a forthcoming paper (Strazzullo et al in prep.)." (4.1 Gas replenishment through galaxy outflows) [from Strazzullo et al. in prep.]

### Not stated but needed to reproduce (our reading)

- ALMA band, array configuration, beam, rms, exposure and dates
- calibration and imaging procedure and CASA version
- how the 5.5 mJy flux was measured
- template choice and L_IR to SFR conversion details

## Analysis recipe

1. **Derive SFR of bright ALMA source**: 870 μm flux converted to L_IR and SFR with a Main-Sequence template  
  > "Its 870 $\mu$m flux is $F_{\mathrm{870\mu m}} = 5.5$ mJy, corresponding to a total infra-red luminosity between $8-1000$ $\mu$m of $L_{\mathrm{IR}} = 6.6\times10^{12}$ L$_\odot$" (4.1 Gas replenishment through galaxy outflows)
   - assumption: Source excluded from SFR accounting because membership is unconfirmed  
  > "As there is no spectroscopic confirmation that the ALMA source is a member of the cluster, we have conservatively excluded it from the SFR accounting." (4.1 Gas replenishment through galaxy outflows)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **SExtractor** : dual-image source detection in narrow- and broad-band optical images  
  > "We selected individual Ly$\alpha$ absorbers and emitters by running SExtractor in dual image mode" (2.1 The Lyα nebula detection)
- **CIAO** 4.6: Chandra data reprocessing  
  > "reprocessing was carried out using CIAO version 4.6" (2.3 Chandra X-ray observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 870 μm flux of bright ALMA source | 5.5 | not stated | mJy | 1 | Its 870 $\mu$m flux is $F_{\mathrm{870\mu m}} = 5.5$ mJy |
| SFR of ALMA source | 1100 | 0.15 dex (modeling) | Msun/yr | 1 | $\mathrm{SFR} = 1100$ M$_{\odot}$ yr$^{-1}$ at $z=1.99$ |
| Lyα luminosity of nebula | 2.3e43 | 0.2e43 | erg/s | 0 | $L_{\mathrm{Ly\alpha}}=(2.3\pm0.2)\times10^{43}$ erg s$^{-1}$ |

## Qualitative findings

- AGN are the most plausible power source of the nebula  
  > "The most plausible candidates to power the nebula are two Chandra-detected AGN host cluster members" (abstract)

## Claim tuples

- H: Galaxy outflows can supply the gas replenishment needed to sustain the nebula | E: Summed SFR-based and AGN-based mass outflow rates of core members, including an ALMA 870 μm SFR | R: Total SFR ≈1000 Msun/yr and AGN outflows ≈1400 Msun/yr versus required ≳1000 Msun/yr | F: Outflows are sufficient and imply ≈2 keV per particle injected into the ICM | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Young stars, cold flows and classical cooling flows disfavored as the Lyα power source  
  > "disfavoring ionization from very young stars and cooling from the X-ray phase in the form of a stationary classical cooling flow" (5 Conclusions)
- How they decided it was enough: _not stated_
- Limitation (authors): ALMA source membership unconfirmed; it would double the core SFR  
  > "if confirmed to be part of the cluster, this source would increase by a factor of $2\times$ the total SFR in the core" (4.1 Gas replenishment through galaxy outflows)
- Caveat (inferred, ours): ALMA contribution is one flux and an SFR with no processing details
- Caveat (inferred, ours): The SFR rests on a template conversion

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA reduction details, deferred to Strazzullo et al. in prep.
- Data volume (inferred): not stated; likely a few GB for one continuum project
- Score (inferred): 1/5, ALMA is a minor input and its processing is deferred to another paper.
- Rediscovery candidate: no, The ALMA recipe is not given.

## Links

- Companion: Strazzullo et al. in prep. (ALMA observations, reduction and analysis)

## Checks

```json
{
 "quotes": 26,
 "quotes_ok": 26,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 57,
  "stated": 17,
  "rate": 0.298
 },
 "evidence_ok": true
}
```
