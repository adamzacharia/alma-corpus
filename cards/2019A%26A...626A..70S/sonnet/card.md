# Carbon radio recombination lines from gigahertz to megahertz frequencies towards Orion A

`2019A&A...626A..70S` | Astronomy and Astrophysics 2019 | first author: Salas, P. | arXiv: 1905.02799 | DOI: 10.1051/0004-6361/201834532

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: milky_way_ism, star_formation
- Question: How do carbon radio recombination lines from MHz to GHz frequencies relate to the 158 um [CII] line in the Veil and the dense PDR of Orion A, and what physical conditions do they imply?  
  > "Here we explore the relation between CRRLs and the $158$ $\mu$m-\[CII\] line in light of new observations and models." (abstract)
- Target **Orion A (M42), the Veil and the dense PDR**: coordinates map centred at 5h35m14.5s, -5d22m29.3s (J2000)  
  > "We adopt a distance of $414$ pc to Orion A (cite: Menten2007; Zari2017)." (1 Introduction); z/distance 414 pc  
  > "We adopt a distance of $414$ pc to Orion A (cite: Menten2007; Zari2017)." (1 Introduction); distance from Menten2007; Zari2017  
  > "We adopt a distance of $414$ pc to Orion A (cite: Menten2007; Zari2017)." (1 Introduction)

## Data provenance

- ALMA projects: 2013.1.00546.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: ALMA total power plus ACA (cubes from Bally et al. 2017)  
  > "observations of the C$30\alpha$ line using the Atacama Large Millimeter Array (ALMA) total power array plus ALMA compact array (ACA) at a spatial resolution of $28\ensuremath{''}$ (cite: Bally2017)" (2.3 Literature data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 28 arcsec  
  > "observations of the C$30\alpha$ line using the Atacama Large Millimeter Array (ALMA) total power array plus ALMA compact array (ACA) at a spatial resolution of $28\ensuremath{''}$ (cite: Bally2017)" (2.3 Literature data)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: C C30alpha (n=30 RRL) (not stated)
- Other facility **GBT**: L-band CRRL map and archival pointings towards M42  
  > "We observed Orion A with the National Radio Astronomy Observatory (NRAO) Robert C. Byrd Green Bank Telescope" (2.1.1 L-band CRRL maps)
- Other facility **LOFAR**: C351alpha absorption at 150 MHz  
  > "This resulted in a detection of the C$351\alpha$ line in absorption with a signal-to-noise ratio of $4.5$." (2.2 LOFAR observations)
- Other facility **SOFIA upGREAT**: 158 um [CII] cube  
  > "This cube has a spatial resolution of $18\ensuremath{''}$ and a velocity resolution of $0.2$ km s$^{-1}$" (2.3 Literature data)
- External data: ALMA C30alpha cubes  
  > "We searched for CRRLs in the ALMA cubes presented by (cite: Bally2017)." (3.2.2 C30alpha) [from Bally2017]
- External data: C65alpha and C91alpha intensities  
  > "(cite: Wyrowski1997) provides measurements of the C$65\alpha$ and C$91\alpha$ intensity." (4.2.1 CRRLs) [from Wyrowski1997]
- External data: 158 um [CII] cube  
  > "The observations and reduction used to produce the $158$ $\mu$m-\[CII\] line cube are described in detail in (cite: Pabst2019)." (2.3 Literature data) [from Pabst2019]
- Simulation/model as data: Meudon PDR code models and Salgado2017a CRRL level population models  
  > "we use the *Meudon* PDR code (cite: Lepetit2006) to generate temperature and density profiles." (3.3 PDR models)

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

- ALMA C30alpha cube reduction taken from earlier paper  
  > "We searched for CRRLs in the ALMA cubes presented by (cite: Bally2017)." (3.2.2 C30alpha) [from Bally2017]

### Not stated but needed to reproduce (our reading)

- ALMA C30alpha cube processing, beam, rms and flux scale (in Bally et al. 2017)
- How C30alpha line intensity was integrated over the 40 arcsec region
- Smoothing to common resolution for line ratios

## Analysis recipe

1. **Measure C30alpha intensity and ratios to C65/C91**: Compare C30alpha intensity with C65alpha and C91alpha over a 40 arcsec region  
  > "The C$30\alpha$ line intensity over this region is $71\pm13$ mK km s$^{-1}$." (4.2.1 CRRLs)
   - assumption: Background continuum is zero for the PDR interface  
  > "the background continuum will be zero (cite: Natta1994)." (4.2.1 CRRLs)
   - fitting: _not stated_
   - validation: _not stated_
2. **Constrain gas T and ne from ratios with [CII]**: Compare ratios to departure-coefficient models; [CII] column from [13CII]  
  > "this sets a lower limit to the gas thermal pressure of $5\times10^{7}$ K cm$^{-3}$." (4.2.3 Combined constraints)
   - software: CRRLpy
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CRRLpy** : Analysis of CRRL observations  
  > "Analysis of CRRL observations was done using CRRLpy (cite: crrlpy)." (Acknowledgements)
- **Meudon PDR code** : PDR temperature and density profiles  
  > "we use the *Meudon* PDR code (cite: Lepetit2006) to generate temperature and density profiles." (3.3 PDR models)
- **LMFIT** : Gaussian fitting  
  > "LMFIT, a nonlinear least-squares minimization and curve-fitting package for Python (cite: newville_2014_11813)" (Acknowledgements)
- **GBTGRIDDER** : Gridding GBT maps  
  > "Then all the data was gridded together using the stand-alone *GBTGRIDDER*" (2.1.1 L-band CRRL maps)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| C30alpha line intensity | 71 | 13 | mK km/s | 1 | The C$30\alpha$ line intensity over this region is $71\pm13$ mK km s$^{-1}$. |
| C30alpha/C65alpha ratio | 0.12 | 0.02 | dimensionless | 1 | the C$30\alpha$/C$65\alpha$ line ratio is $0.12\pm0.02$ |
| C30alpha/[CII] ratio | 1.4e-4 | 0.2e-4 | dimensionless | 2 | For the C$30\alpha/$\[CII\] ratio we have a value of $(1.4\pm0.2)\times10^{-4}$. |
| Thermal pressure lower limit (dense PDR) | 5e7 | not stated | K cm^-3 | 2 | this sets a lower limit to the gas thermal pressure of $5\times10^{7}$ K cm$^{-3}$. |
| Veil gas temperature | 30-45 | 3 sigma range | K | 0 | $30$ K$\leq T_{\mathrm{e}}\leq45$ K and $0.65$ cm$^{-3}\leq n_{\mathrm{e}}\leq0.95$ cm$^{-3}$ |

## Qualitative findings

- Radio lines trace colder gas than the [CII] line in the dense PDR, near the C+/C/CO interface  
  > "in a dense PDR the radio lines trace colder gas than the FIR line." (5 Summary)

## Claim tuples

- H: Combined CRRL and [CII] constrain Veil conditions | E: C280alpha, C351alpha and [CII] ratios | R: 30-45 K, 0.65-0.95 cm^-3 | F: Veil temperature and density determined | **supported**
- H: Isobaric PDR models explain dense PDR CRRL and [CII] data | E: Compare line intensities with Meudon models | R: G0=1e5, Pth=5e7 K cm^-3 best | F: Stationary isobaric models reproduce the observations | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Constant density PDR models cannot explain the observed line properties with reasonable inputs  
  > "This shows that constant density PDR models are not able to explain the observed line properties given reasonable input parameters." (4.2.4 PDR models)
- How they decided it was enough: _not stated_
- Limitation (authors): Higher signal-to-noise CRRL detections needed to constrain properties independently  
  > "higher signal-to-noise detections of the observed lines are required." (4.2.1 CRRLs)
- Caveat (inferred, ours): ALMA C30alpha is a minor part and relies on previously published cubes
- Caveat (inferred, ours): Different beams among lines may bias ratios

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Processed ALMA C30alpha cube details
- Missing: Exact model grids
- Data volume (inferred): tens of GB for ALMA cubes
- Score (inferred): 3/5, ALMA part is small and depends on earlier reduction; multiple non-ALMA datasets.
- Rediscovery candidate: no, ALMA role is minor and processing is not described.

## Links

- Method: Salgado2017a (CRRL level population models)
- Companion: Pabst2019 (SOFIA [CII] map)

## Checks

```json
{
 "quotes": 35,
 "quotes_ok": 35,
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
  "facts": 65,
  "stated": 24,
  "rate": 0.369
 },
 "evidence_ok": true
}
```
