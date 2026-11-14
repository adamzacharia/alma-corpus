# An ALMA survey of the SCUBA-2 CLS UDS field: physical properties of 707 sub-millimetre galaxies

`2020MNRAS.494.3828D` | Monthly Notices of the Royal Astronomical Society 2020 | first author: Dudzevičiūtė, U. | arXiv: 1910.07524 | DOI: 10.1093/mnras/staa769

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies
- Question: What are the physical properties (redshifts, dust/stellar/gas masses, dust temperatures, SFRs) of the 707 ALMA-located AS2UDS SMGs, and what do they say about the evolutionary role of SMGs?  
  > "We analyse the physical properties of a large, homogeneously selected sample of ALMA-located sub-millimetre galaxies (SMGs)." (abstract)
- Target **AS2UDS SMGs in the SCUBA-2 CLS UDS field**: coordinates _not stated_; z/distance median photometric z = 2.61 +/- 0.08  
  > "The S2CLS map of the UDS covers an area of 0.96 deg$^{2}$ with noise level below 1.3 mJy and a median depth of $\sigma_{850}$ = 0.88 mJy beam$^{-1}$." (2.1 ALMA); distance from magphys photometric redshifts from this paper  
  > "The S2CLS map of the UDS covers an area of 0.96 deg$^{2}$ with noise level below 1.3 mJy and a median depth of $\sigma_{850}$ = 0.88 mJy beam$^{-1}$." (2.1 ALMA)

## Data provenance

- ALMA projects: 2012.1.00090.S, 2015.1.01528.S, 2016.1.00434.S
- bands: Band 7 (344 GHz, 870 um)  
  > "All 716 SCUBA-2 sources detected in the map were observed in ALMA Band 7 (344 GHz or 870 $\mu$m) between Cycles 1, 3, 4 and 5" (2.1 ALMA)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.15-0.5 arcsec FWHM, maps tapered to 0.5 arcsec  
  > "the spatial resolution of the data varies in range 0.15–0.5$''$ FWHM, although all of the maps are tapered to 0.5$''$ FWHM for detection purposes" (2.1 ALMA)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **UKIDSS UDS DR11 (UKIRT)**: K, H, J photometry (K 3-sigma depth 25.7)  
  > "UDS data release 11 (UKIDSS DR11), which is a $K$-band selected photometric catalogue (Almaini et al., in prep.) covering an area of 0.8 deg$^2$ with a 3-$\sigma$ point-source depth of $K$ $=$ 25.7 mag" (2.2.1)
- Other facility **Spitzer IRAC/MIPS (SpUDS)**: 3.6-8.0 um and 24 um photometry  
  > "We obtained reduced SpUDS images of the UDS from the *Spitzer* Science Archive." (2.2.2)
- Other facility **Herschel SPIRE/PACS (HerMES)**: 100-500 um far-infrared photometry, deblended  
  > "These observations were taken as part of the *Herschel* Multi-tiered Extragalactic Survey (HerMES; (cite: 2012oliver))" (2.3.1)
- Other facility **VLA 1.4 GHz**: radio photometry, rms ~6 uJy/beam  
  > "The resulting map has an rms of $\sigma_{\rm 1.4GHz}\simeq$ 6 $\mu$Jy beam$^{-1}$ (cite: 2013simpson)." (2.3.2)
- External data: AS2UDS ALMA catalogue of 708 SMGs (positions, S870)  
  > "The final catalogue contains 708 individual ALMA-identified SMGs spanning $S_{870}$ = 0.6–13.6 mJy ($>$4.3$\sigma$)" (2.1 ALMA) [from (cite: 2019stach)]
- External data: 870-um sizes of 154 SMGs  
  > "derived from the analysis of high-resolution dust continuum observations of 154 SMGs in A2SUDS by (cite: 2019gullberg)" (5.5 The scale of far-infrared emission) [from (cite: 2019gullberg)]
- External data: Local ULIRG comparison sample from GAMA magphys analysis  
  > "For this purpose we select ULIRGs from analysis of the GAMA survey undertaken by (cite: 2018driver)." (4.3) [from (cite: 2018driver)]
- Simulation/model as data: EAGLE Ref-L0100N1504 galaxies (9,431 with SFR>10 Msun/yr, z>0.25) with skirt SEDs used to test magphys  
  > "we select all 9,431 galaxies from EAGLE with SFR \> 10 M$_\odot$ yr$^{-1}$ and $z>$ 0.25" (3.2)

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

- ALMA observations, data reduction and catalogue construction  
  > "A detailed description of the ALMA observations, data reduction and construction of the catalogue for the SMGs in our sample can be found in (cite: 2019stach)." (2.1 ALMA) [from (cite: 2019stach)]
- Herschel SPIRE deblending procedure  
  > "We, therefore, follow the same procedure as (cite: 2014swinbank)." (2.3.1) [from (cite: 2014swinbank)]
- MCMC modified blackbody fitting  
  > "The best-fit temperature is acquired by fitting this modified blackbody function using a Markov Chain Monte Carlo sampler (see (cite: 2017simpson))." (4.3.2) [from (cite: 2017simpson)]

### Not stated but needed to reproduce (our reading)

- magphys code version, redshift grid and library details
- MCMC sampler, priors and likelihood for the modified blackbody fits
- ALMA calibration, imaging and flux values (only in Stach+2019)
- Herschel/IRAC/UKIDSS photometry catalogues are partly in-prep and not public
- Halo-model fitting details (Millennium merger trees, Lagos gas fraction implementation)

## Analysis recipe

1. **Assemble UV-to-radio photometry**: Match ALMA positions to K-band (0.6") , IRAC aperture photometry (2"), MIPS 24um (2"), deblended Herschel, VLA (1.6")  
  > "The two catalogues are then matched using a radius of 0.6$''$" (2.2.1)
   - fitting: _not stated_
   - validation: _not stated_
2. **SED fitting with magphys**: Fit 22 bands with high-z magphys, medians of PDFs with 16-84th percentile errors  
  > "The derived parameters (e.g. photometric redshift, stellar mass, etc) are taken as the median from the PDF, with uncertainties reflecting the 16–84$^{\rm th}$ percentile values of this distribution" (3)
   - software: magphys
   - parameter: non-detections: flux 1.5 +/- 1.0 sigma beyond 10 um; zero with 3-sigma limit up to 8 um  
  > "for non-detected sources in the infrared (beyond 10 $\mu$m), we adopt a flux density of 1.5 $\pm$ 1.0$\sigma$." (3)
   - parameter: IGM absorption coefficient tuned to 0.5  
  > "tuning the IGM coefficient to 0.5 of the initially drawn value minimises the systematic offset" (3.1)
   - assumption: Bruzual & Charlot models, Chabrier IMF, delayed exponential SFH with bursts  
  > "magphys uses stellar population models from (cite: 2003bruzual&charlot), a Chabrier IMF (cite: 2003chabrier)" (3)
   - fitting: chi2 matching to model library  
  > "magphys identifies the models that best-fit the multi-wavelength photometry by matching the model SEDs to the data using a $\chi^2$ test" (3)
   - validation: Compared to 6,719 spectroscopic redshifts and to EAGLE galaxies  
  > "magphys predicts a stellar mass that is 0.46 $\pm$ 0.10 dex lower than the “true” stellar mass in EAGLE" (3.2)
3. **Modified blackbody dust temperatures**: Optically thin MBB fit to PACS, SPIRE and ALMA 870um with MCMC  
  > "we choose to adopt a simpler, more conservative approach and fit modified blackbody functions to the available *Herschel* PACS and SPIRE, and ALMA 870-$\mu$m photometry." (4.3.2)
   - assumption: beta = 1.8, optically thin  
  > "We adopt $\beta$ $=$ 1.8 as used in previous SMG studies" (4.3.2)
   - fitting: MCMC  
  > "The best-fit temperature is acquired by fitting this modified blackbody function using a Markov Chain Monte Carlo sampler" (4.3.2 Characteristic dust temperature)
   - validation: _not stated_
4. **Gas masses and depletion times**: Gas mass = 100 x dust mass; tau_dep = 0.5 Mgas/SFR  
  > "yielding a gas-to-dust ratio, $\delta _{\rm gdr}$, of $\sim$ 100 (cite: 2014swinbank) similar to that estimated for Arp 220, which we adopt for our study." (4.3.6)
   - assumption: half of gas available to form stars  
  > "we estimate assuming half of the gas is available to form stars (the other half being expelled)" (4.3.6)
   - fitting: _not stated_
   - validation: _not stated_
5. **Luminosity, gas and stellar mass functions and halo model**: 1/Vmax functions with Schechter fits (alpha fixed -1.5); halo critical mass from Millennium Simulation x molecular fraction  
  > "we choose to fix it to $\alpha=-$1.5." (5.2.1)
   - fitting: Schechter fits; bootstrap errors  
  > "Errors are estimated using a bootstrap method by re-sampling the photometric redshift and luminosity probability distribution functions. We fit the luminosity functions using Schechter functions of the form" (5.2.1 Far-infrared luminosity function)
   - validation: compared to ASPECS and COLDz  
  > "Here, we compare estimates of the gas mass function derived from the ASPECS blind mid-$J$ CO survey from (cite: 2019decarli) to the space densities for our gas mass functions" (5.2.2 Gas mass function)

## Software

- **magphys** : UV-to-radio SED fitting  
  > "we employ magphys (cite: 2008dacunha; 2015dacunha; 2019battisti)" (3)
- **skirt** : radiative transfer for EAGLE SEDs (post-processing from literature)  
  > "includes dust reprocessing using the skirt radiative transfer code" (3.2)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| median photometric redshift | 2.61 | 0.08 | dimensionless | 2 | determine a median redshift of $z$ $=$ 2.61 $\pm$ 0.08 |
| median dust mass | 6.8e8 | 0.3e8 | Msun | 2 | $M_{\rm d}$ $=$ (6.8$\pm$0.3) $\times$ 10$^8$ M$_\odot$ |
| median stellar mass | 12.6e10 | 0.5e10 | Msun | 2 | The median stellar mass of the full AS2UDS sample is $M_\ast$ $=$ (12.6 $\pm$ 0.5) $\times$ $10^{10}$ M$_\odot$ |
| median LIR | 2.88e12 | 0.09e12 | Lsun | 2 | the median far-infrared luminosity is $L_{\rm
  IR}$ $=$ (2.88 $\pm$ 0.09) $\times$ 10$^{12}$ L$_\odot$ |
| median characteristic dust temperature (SPIRE-detected) | 30.4 | 0.3 | K | 3 | $T^{\rm MBB}_{\rm d}$ $=$ 30.4 $\pm$ 0.3 K |
| median gas depletion time | 146 | 5 | Myr | 4 | with a median of 146$\pm$5 Myr |
| critical halo mass | ~6e12 | not stated | Msun | 5 | The halo mass of $\sim$6$\times$10$^{12}$M$_\odot$, estimated from the SMG redshift distribution |

## Qualitative findings

- About 17% of SMGs are undetected at K>=25.7 and are dustier (higher A_V), not only higher redshift.  
  > "the $K$-detected SMGs have optical reddening of $A_V$ $=$ 2.61 $\pm$ 0.05, but the $K$-blank SMGs exhibit much higher reddenings" (4.1)

## Claim tuples

- H: Do SMGs show dust temperature evolution at fixed luminosity? | E: MBB fits for LIR-limited subsample at z=1.5-4 | R: no trend of Td with z | F: No evolution in dust temperature at constant LIR | **supported**
- H: Have massive galaxies passed through an SMG phase? | E: Compare duty-cycle corrected SMG and field stellar mass functions | R: ~30% above 3e10, ~100% above 3e11 Msun | F: Almost all galaxies with M*>3e11 passed through an SMG-like phase | **supported**
- H: Does halo growth plus gas fraction explain the SMG z distribution? | E: Millennium halo threshold crossing x gas fraction | R: Mh~6e12 matches | F: SMGs may be efficient collapse of gas-rich massive halos | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): magphys underestimates stellar mass by 0.46 dex vs EAGLE; fixed gas-to-dust ratio  
  > "magphys predicts a stellar mass that is 0.46 $\pm$ 0.10 dex lower than the “true” stellar mass in EAGLE" (3.2)
- Caveat (inferred, ours): Gas masses rely on fixed gas-to-dust ratio of 100
- Caveat (inferred, ours): Optically thin Td is only a characteristic temperature
- Caveat (inferred, ours): Selection biases with redshift in SPIRE-detected subset

## Reproducibility

- Data public (paper): All data available through archives  
  > "All the data required for this project is available through the relevant archives." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Catalogue Table A1 online only; ALMA reduction in Stach+2019
- Missing: magphys configuration details
- Missing: UKIDSS DR11 catalogue in prep.
- Data volume (inferred): Catalogue-level analysis; ALMA data not reprocessed (tens of GB if needed)
- Score (inferred): 3/5, Public catalogues and standard magphys but many details inherited or unstated.
- Rediscovery candidate: no, Depends on non-public/in-prep photometry and inherited ALMA catalogue.

## Links

- Method: (cite: 2019stach) (ALMA reduction and catalogue)
- Method: (cite: 2019battisti) (high-z magphys)
- Companion: (cite: 2019gullberg) (AS2UDS sizes)
- Related: AS2UDS
- Related: ALESS
- Related: S2CLS
- Related: HerMES
- Related: EAGLE

## Checks

```json
{
 "quotes": 50,
 "quotes_ok": 50,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 36,
  "rate": 0.462
 },
 "evidence_ok": true
}
```
