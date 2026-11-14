# An Imperfectly Passive Nature: Bright Submillimeter Emission from Dust-obscured Star Formation in the z = 3.717 “Passive” System, ZF 20115

`2017ApJ...844L..10S` | The Astrophysical Journal Letters 2017 | first author: Simpson, J. M. | arXiv: 1704.03868 | DOI: 10.3847/2041-8213/aa7cf2

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies
- Question: Is the claimed massive post-starburst/quiescent galaxy ZF 20115 at z=3.717 truly passive, or does it host obscured star formation revealed by sub-mm imaging?  
  > "to securely classify a galaxy as quiescent, it is necessary to exclude significant ongoing star formation, something that can be challenging to achieve at high redshifts." (abstract)
- Target **ZF 20115**: coordinates _not stated_; z/distance z = 3.717  
  > "The galaxy ZF 20115, located in the CANDELS region of the COSMOS field, was selected based on its rest-frame optical color in the ZFOURGE survey" (Observations); "a purported “passive” galaxy at $z$ = 3.717." (Introduction); distance from Glazebrook et al. 2017 near-infrared spectroscopy  
  > "The galaxy ZF 20115, located in the CANDELS region of the COSMOS field, was selected based on its rest-frame optical color in the ZFOURGE survey" (Observations); "a purported “passive” galaxy at $z$ = 3.717." (Introduction)

## Data provenance

- ALMA projects: 2013.1.01292.S
- bands: 870 um  
  > "ZF 20115 was observed in ALMA Cycle 2 at 870 $\mu$m for 1.4 min" (Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.1'' x 0.6'' synthesized beam  
  > "The ALMA observations employed 39 antennae yielding a synthesized beam of 1.1$''$ $\times$ 0.6$''$" (Observations)
- max recoverable scale: _not stated_
- sensitivity: sigma_870 = 0.2 mJy/beam  
  > "reach a depth of $\sigma_{870}$ = 0.2 mJy beam$^{-1}$" (Observations)
- time on source: 1.4 min  
  > "ZF 20115 was observed in ALMA Cycle 2 at 870 $\mu$m for 1.4 min" (Observations)
- observing dates: _not stated_
- pi or archival as stated: archival data  
  > "we show the archival ALMA 870 $\mu$m data for ZF 20115" (Analysis)
- Other facility **SCUBA-2/JCMT (STUDIES)**: 450 and 850 um imaging  
  > "We detect ZF 20115–FIR at a 3 $\sigma$ significance level in the 450 $\mu$m imaging" (Observations)
- Other facility **Herschel PACS/SPIRE**: 100-500 um photometry (non-detections)  
  > "ZF 20115 is not detected in the 100–500 $\mu$m imaging." (Observations)
- Other facility **HST/CANDELS and Spitzer IRAC**: rest-frame UV and 3.6/4.5 um imaging  
  > "contoured on the *HST* / CANDELS imaging" (Analysis)
- External data: ZFOURGE photometric catalogue  
  > "we use this photometric catalogue in our analysis (cite: Straatman16)" (Observations) [from Straatman16]
- External data: Template SEDs and stellar masses of ALMA SMGs  
  > "we estimate the contribution by considering the spectroscopically-identified, ALMA-located–SMGs from (cite: Danielson17)" (Discussion) [from Danielson17]

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

- MCMC SED fitting approach  
  > "determined using a Monte-Carlo Markov Chain (MCMC) approach (cite: Simpson17)" (Analysis) [from (cite: Simpson17)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration and imaging details (CASA version, weighting, cleaning)
- Priors and chain settings for MCMC
- Details of mock catalogue construction

## Analysis recipe

1. **measure ALMA source flux**: Model emission with CASA imfit; unresolved  
  > "We use CASA / imfit to model the emission and determine that ZF 20115–FIR is unresolved" (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **fit far-IR SED**: Single-temperature optically thin modified blackbody, MCMC, CMB correction; 100 um excluded  
  > "we fit the far-infrared photometry with a single-temperature, optically-thin, modified blackbody (mBB) function." (Analysis)
   - parameter: beta = 1.8  
  > "The dust emissivity is fixed at $\beta=$ 1.8" (Analysis)
   - assumption: mBB underestimates L_FIR by ~20%; corrected; SFR from Kennicutt98  
  > "A single temperature mBB is known to underestimate the total far-infrared luminosity by $\sim$ 20 %" (Analysis)
   - fitting: MCMC  
  > "determined using a Monte-Carlo Markov Chain (MCMC) approach (cite: Simpson17)" (Analysis)
   - validation: _not stated_
3. **estimate starburst contribution to IRAC/near-IR photometry and stellar mass**: Deblend IRAC with 3 2-D Gaussians via MCMC; subtract average SMG template SED; model residual with magphys  
  > "we subtract the average starburst SED from the global photometry. Using magphys (cite: dacunha15) to model the residual photometry" (Discussion)
   - software: magphys
   - fitting: MCMC for deblending  
  > "Using an MCMC approach we determine that" (Discussion)
   - validation: Two methods broadly consistent  
  > "broadly consistent with our estimates from deblending the IRAC imaging" (Discussion)

## Software

- **CASA** : imfit of ALMA source  
  > "We use CASA / imfit to model the emission" (Observations)
- **magphys** : model residual stellar photometry  
  > "Using magphys (cite: dacunha15) to model the residual photometry" (Discussion)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA 870um flux density | 1.4 | 0.2 | mJy | 1 | total flux density of 1.4 $\pm$ 0.2 mJy beam$^{-1}$ |
| UV-FIR offset | 0.4 | 0.1 | arcsec | 0 | 0.4 $\pm$ 0.1$''$ ($\sim$ 3 kpc in projection) |
| Dust temperature | 30.4 | +1.4/-12.0 | K | 2 | $T_{\mathrm{d}}$ = 30.4$^{+1.4}_{-12.0}$ K |
| Total L_FIR | 9.2e11 | +1.2/-6.2 e11 | Lsun | 2 | $L_{\mathrm{FIR}}$ = 9.2$^{+1.2}_{-6.2}$ $\times$ 10$^{11}$ |
| Obscured SFR | 100 | +15/-70 | Msun/yr | 2 | obscured star-formation rate (SFR) of 100$^{+15}_{-70}$ |
| Chance alignment probability | 1.5e-4 | not stated | dimensionless | 0 | a probability of $\sim$ 1.5 $\times$ 10$^{-4}$ that ZF 20115–UV and ZF 20115–FIR are a chance alignment |
| Stellar mass of ZF 20115-UV | ~0.8e11 | not stated | Msun | 3 | this component has a stellar mass of $\sim$ 0.8 $\times$ 10$^{11}$ |

## Qualitative findings


## Claim tuples

- H: ZF 20115 is a quiescent/post-starburst galaxy | E: ALMA 870um and SCUBA-2 imaging plus SED fitting | R: Obscured starburst with SFR ~100 Msun/yr 0.4'' from the UV component | F: The system is not passive; sub-mm data are needed to claim quiescence | **supported**
- H: Blending biases stellar mass | E: IRAC deblending and SMG template subtraction | R: Starburst contributes ~33% of 1.5-8 um photometry; mass ~0.8e11 Msun | F: Stellar mass less than half the previous estimate; no tension with galaxy formation models | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Large uncertainties on stellar mass; ALMA astrometry could not be independently aligned  
  > "although we stress that the uncertainties on this measurement are large" (Conclusions)
- Caveat (inferred, ours): Only 1.4 min ALMA snapshot, single pointing
- Caveat (inferred, ours): Single-temperature mBB with few photometric points gives very asymmetric errors
- Caveat (inferred, ours): Stellar mass relies on assumed SMG template

## Reproducibility

- Data public (paper): Archival ALMA data used  
  > "we show the archival ALMA 870 $\mu$m data for ZF 20115" (Analysis)
- Products in archive: _not stated_
- Missing: ALMA reduction/imaging parameters
- Missing: MCMC priors
- Missing: Fluxes of other photometry in table form
- Data volume (inferred): <5 GB
- Score (inferred): 3/5, Public short ALMA snapshot, but sparse method details and reliance on external photometry/templates.
- Rediscovery candidate: no, Recipe incomplete and key inputs from external catalogs.

## Links

- Method: Simpson17 (arXiv:1611.03084) (MCMC SED fitting)
- Companion: Glazebrook17 (Original claim of quiescent ZF 20115)
- Related: ZFOURGE
- Related: STUDIES
- Related: CANDELS

## Checks

```json
{
 "quotes": 40,
 "quotes_ok": 40,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 63,
  "stated": 26,
  "rate": 0.413
 },
 "evidence_ok": true
}
```
