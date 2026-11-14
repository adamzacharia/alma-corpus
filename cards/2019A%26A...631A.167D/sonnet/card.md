# A dense, solar metallicity ISM in the z = 4.2 dusty star-forming galaxy SPT 0418-47

`2019A&A...631A.167D` | Astronomy and Astrophysics 2019 | first author: De Breuck, Carlos | arXiv: 1909.12554 | DOI: 10.1051/0004-6361/201936169

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies, milky_way_ism
- Question: What are the ISM physical conditions (PDR vs HII, density, AGN contribution, metallicity) of the lensed DSFG SPT 0418-47 at z=4.2 from six far-IR fine structure lines?  
  > "We present a study of six far-infrared fine structure lines in the $z$=4.225 lensed dusty star-forming galaxy SPT 0418-47 to probe the physical conditions of its inter stellar medium (ISM)." (abstract)
- Target **SPT 0418-47 (SPT-S J041839-4751.8)**: coordinates _not stated_; z/distance z=4.2248; D_L=39.150 Gpc  
  > "SPT-S J041839-4751.8 (hereinafter SPT 0418-47) at $z$=4.2248 (cite: weiss2013)" (Introduction); "With a lensing magnification $\mu$=32.7$\pm$2.7 (cite: spilker2016)" (Introduction); distance from Weiss et al. 2013 redshift; Planck 2016 cosmology  
  > "SPT-S J041839-4751.8 (hereinafter SPT 0418-47) at $z$=4.2248 (cite: weiss2013)" (Introduction); "With a lensing magnification $\mu$=32.7$\pm$2.7 (cite: spilker2016)" (Introduction)

## Data provenance

- ALMA projects: 2016.1.00133.T, 2018.1.01670.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: ACA for [NII] 205 and 122 µm; ALMA Cycle 3 for [CI] 609 µm (from other papers)  
  > "The \[NII\] 205$\mu$m line was detected as part of an Atacama Compact Array (ACA) survey of 41 SPT sources (cite: cunningham2019)." (2.2 Additional data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: [OI] 3P1-3P0 145 µm (APEX/FLASH) (2060.07 GHz)
- Line: [OIII] 88 µm (APEX/SEPIA) (3393.01 GHz)
- Other facility **APEX**: New [OI] 145 µm (FLASH, 7.3 h) and [OIII] 88 µm (SEPIA, 6.25 h) detections; [CII] from earlier work  
  > "The total on-source integration time was 7.3 hours, with precipitable water vapour (PWV) in the range 0.4–0.8 mm." (2.1 New data from APEX)
- External data: [CII] 158 µm line from APEX/FLASH  
  > "(cite: gullberg2015) report a bright \[CII\] 158 $\mu$m line detected with APEX/FLASH" (2.2 Additional data) [from (cite: gullberg2015)]
- External data: [CI] 609 µm line from ALMA Cycle 3  
  > "(cite: bothwell2017) report the detection of the \[CI\] 609$\mu$m line from ALMA Cycle 3 spectroscopy." (2.2 Additional data) [from (cite: bothwell2017)]
- External data: Lens magnification mu=32.7±2.7  
  > "The lensing amplification factor $\mu$=32.7$\pm$2.7 was derived by (cite: spilker2016)" (2.2 Additional data) [from (cite: spilker2016)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 15% overall APEX calibration uncertainty for the [OI] 145 µm observations  
  > "We estimate the overall calibration uncertainty at 15%." (2.1 New data from APEX)
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

- Assumed L_[CII]^ion/L_[NII] ≃ 3.0±0.5 for the HII fraction  
  > "Following (cite: diaz-santos2017), we assume $L_{[CII]}^{ion}/L_{[NII]}$$\simeq$3.0$\pm$0.5" (4.2 Contributions of PDR and HII regions) [from (cite: diaz-santos2017)]
- Ionization parameter from C(88-122) continuum ratio  
  > "We conservatively adopt the latter, which yields $-$3.2$<$$\log U$$<$-2.0 using Fig. 4 of (cite: rigopoulou2018)." (4.5 Metallicity) [from (cite: rigopoulou2018)]

### Not stated but needed to reproduce (our reading)

- Calibrated ALMA/ACA data reduction details (ACA data come from other papers)
- CLASS baseline and smoothing choices, channel width, and Gaussian fit setup
- CIGALE configuration for the AGN fraction and stellar mass
- PDR toolbox input grid and line-ratio selection
- Quadratic interpolation details for C(88-122)

## Analysis recipe

1. **Reduce APEX spectra and fit lines**: Reduction in CLASS with first-order baseline; unconstrained single Gaussian fits of redshift, width and flux  
  > "We reduced the data using the standard procedures in CLASS, using a first order fit for baseline removal." (2.1 New data from APEX); "We fitted an unconstrained single Gaussian to the observed profiles" (3 Results)
   - software: CLASS
   - fitting: _not stated_
   - validation: _not stated_
2. **Compute line luminosities**: Solomon et al. 1997 formula  
  > "The line luminosities are calculated following (cite: solomon1997)" (3 Results)
   - assumption: Planck cosmology H0=67.8, Om=0.308  
  > "we assume a $\Lambda$CDM cosmology with $H_0$=67.8 s$^{-1}$Mpc$^{-1}$, $\Omega_m$=0.308" (Introduction)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive PDR/HII fractions, density, PDR parameters**: [CII]/[NII]205 ratio for HII fraction; [NII] 122/205 for n_e; PDR toolbox for G0 and n  
  > "From the PDR toolbox modelling of all five PDR-dominated lines, we derive a $G0$$\sim$$10^3$ and $n$$\sim$2$\times$10$^4$ cm$^{-3}$." (4.3 Gas density)
   - software: PDR toolbox
   - fitting: _not stated_
   - validation: _not stated_
4. **AGN fraction and metallicity**: CIGALE SED fit for AGN fraction; continuum ratio C(88-122) gives log U; [OIII]88/[NII]122 with CLOUDY models gives Z  
  > "The observed \[OIII\] 88 $\mu$m to \[NII\] 122 $\mu$m ratio thus suggests 0.3$<$$Z/Z_{\odot}$$<$1.3." (4.5 Metallicity)
   - software: CIGALE, CLOUDY
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CLASS** : APEX data reduction  
  > "We reduced the data using the standard procedures in CLASS" (2.1 New data from APEX)
- **CIGALE** : SED modelling for AGN fraction and stellar mass  
  > "using the CIGALE SED modelling code (cite: noll2009; boquien2019)" (4.4 AGN contributions)
- **PDR toolbox** : PDR modelling of G0 and density  
  > "From the PDR toolbox modelling of all five PDR-dominated lines" (4.3 Gas density)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| [OIII] 88 µm line flux | 108 | ±11 | Jy km/s | 1 | $F_{\rm line}$ \[Jy km/s\] / 108$\pm$11 |
| [OI] 145 µm line flux | 33 | ±7 | Jy km/s | 1 | 33$\pm$7 |
| [CII] HII fraction | 12 | ±2 | % | 3 | we derive an HII fraction of 12$\pm$2% |
| electron density | 50 | ±20 | cm^-3 | 3 | corresponds to an electron density $n_e=50\pm20$ cm$^{-3}$ |
| metallicity | 0.3<Z/Zsun<1.3 | not stated | Zsun | 4 | 0.3$<$$Z/Z_{\odot}$$<$1.3 |
| AGN fraction | <5 | not stated | % | 4 | We derive an AGN fraction $<$5%. |

## Qualitative findings

- [OI]145/[CII] ratio ~5x higher than local galaxy average, indicating dense PDR-dominated ISM  
  > "The \[OI\] 145$\mu$m / \[CII\] 158$\mu$m line ratio is $\sim$5$\times$ higher compared to the average of local galaxies." (abstract)

## Claim tuples

- H: The ISM is PDR-dominated and dense | E: Line ratios [OIII]/[OI]145, [CII]/[NII]205, [NII]122/205 and PDR toolbox | R: [CII] ~88% PDR; n_e=50 cm^-3; PDR n~2e4 cm^-3 | F: Dense PDR-dominated ISM | **supported**
- H: The ISM is chemically enriched | E: [OIII]88/[NII]122 with log U from continuum ratio | R: 0.3<Z/Zsun<1.3 | F: Near-solar metallicity | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): AGN presence is inconclusive from FSL ratios; [NII] 122 line low S/N  
  > "We conclude that while the SED seems to suggest a negligible AGN contribution in SPT 0418-47, the FSL ratio method is more inconclusive." (4.4 AGN contributions)
- Caveat (inferred, ours): Metallicity range is wide (0.3-1.3 Zsun)
- Caveat (inferred, ours): Detections only ~5 sigma
- Caveat (inferred, ours): Lensing differential magnification not fully excluded
- Caveat (inferred, ours): Galaxy-integrated ratios mix phases

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ACA data processing is in other papers
- Missing: Unpublished Cunningham et al. and Phadke et al. results
- Data volume (inferred): small (<10 GB for APEX spectra); ACA data minor
- Score (inferred): 3/5, Mostly APEX data and literature line ratios; ALMA role minor and modelling details sparse.
- Rediscovery candidate: no, Key data are APEX and external ACA products; recipe incomplete.

## Links

- Method: (cite: rigopoulou2018) (log U from continuum ratio method)
- Method: (cite: pereira-santaella2017) (CLOUDY metallicity models)
- Companion: (cite: cunningham2019) (ACA [NII] 205 µm survey)
- Companion: (cite: bothwell2017) ([CI], PDR modelling)
- Related: SPT DSFG sample
- Related: ACA survey of SPT sources

## Checks

```json
{
 "quotes": 37,
 "quotes_ok": 37,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 67,
  "stated": 21,
  "rate": 0.313
 },
 "evidence_ok": true
}
```
