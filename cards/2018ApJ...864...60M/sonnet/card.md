# SOFIA/HAWC+ Detection of a Gravitationally Lensed Starburst Galaxy at z = 1.03

`2018ApJ...864...60M` | The Astrophysical Journal 2018 | first author: Ma, Jingzhe | arXiv: 1807.06664 | DOI: 10.3847/1538-4357/aad4a0

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: Is the IR luminosity of the lensed starburst J1429-0028 powered by pure star formation or also an AGN, and how well can SED modeling constrain its stellar mass and star formation history?  
  > "Is this high IR luminosity powered by pure star formation (SF) or also an active galactic nucleus (AGN)?" (abstract)
- Target **HATLASJ142935.3-002836 (J1429-0028, G15v2.19)**: coordinates _not stated_; z/distance z = 1.027 (source), z = 0.218 (lens)  
  > "This system consists of an edge-on foreground disk galaxy at $z$ = 0.218 and a nearly complete Einstein ring of an intrinsic ultra-luminous infrared galaxy at $z$ = 1.027." (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: _none stated_
- bands: _not stated_
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
- Other facility **SOFIA/HAWC+**: New 89 micron photometry, 748.4 +/- 101.1 mJy observed  
  > "We extracted the photometry of the source using an 1-FWHM radius aperture and the resultant flux density is 748.4 $\pm$ 101.1 mJy." (2.1 SOFIA/HAWC+)
- Other facility **Herschel, SDSS, VIKING, HST, Spitzer, WISE, IRAM-30, JVLA**: Ancillary photometry from UV to radio  
  > "Multi-wavelength photometry from rest-frame UV to radio has been obtained from SDSS ($u$, $g$, $r$, $i$, $z$), VIKING (Z, Y, J, H, K$_s$), *HST* (F110W)" (Multi-wavelength photometry)
- External data: De-blended, magnification-corrected photometry including ALMA 1.28 and 2.8 mm fluxes, and lensing magnification 9.7 +/- 0.7  
  > "Using a lensing magnification factor of 9.7 $\pm$ 0.7 (cite: Messias2014)" (2.1 SOFIA/HAWC+); "We use the de-blended magnification-corrected photometry for the source to perform SED modeling." (Multi-wavelength photometry) [from (cite: Messias2014)]

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

- ALMA photometry and source/lens de-blending taken from earlier work  
  > "The de-blending of the foreground lens and background source is discussed in detail in (cite: Messias2014)." (Multi-wavelength photometry) [from (cite: Messias2014)]

### Not stated but needed to reproduce (our reading)

- ALMA observation details (bands, configurations, calibration, imaging) are not given
- ALMA project code not printed in the paper
- cigale and sed3fit parameter grids beyond those listed
- CRUSH reduction options

## Analysis recipe

1. **Measure SOFIA 89 um flux**: CRUSH reduction, 1-FWHM radius aperture photometry, de-magnified by lens magnification  
  > "the de-magnified flux density at 89 $\ensuremath{\mu}m$ is 77.2 $\pm$ 11.8 mJy." (2.1 SOFIA/HAWC+)
   - software: CRUSH
   - fitting: _not stated_
   - validation: Lens galaxy contribution estimated at most 3%  
  > "The minor contribution to the observed flux density from the foreground lensing galaxy is estimated to be at most 3%, which is within the quoted uncertainties." (2.1 SOFIA/HAWC+)
2. **Panchromatic SED fitting with AGN and radio components**: Energy-balance Bayesian SED fitting with sed3fit and cigale, varying SFH, attenuation and dust emission models one at a time  
  > "Both cigale and sed3fit fit galaxy SEDs using a Bayesian approach to generate the posterior probability distribution function (PDF) for each parameter of interest" (3 SED models)
   - software: sed3fit, cigale, magphys
   - parameter: Chabrier IMF, BC03 stellar populations; double-tau SFH burst fraction free (0-1) or <=0.1  
  > "($f_{\rm burst}$ $\leq$ 0.1)" (Table 1)
   - assumption: Radio q Gaussian prior mean 2.34, sigma 0.25 in sed3fit  
  > "A Gaussian prior distribution is assumed for the coefficient, $q$, with the mean at 2.34" (Radio emission)
   - fitting: Posterior PDFs; cigale weighted mean and std, sed3fit 16/50/84%  
  > "sed3fit outputs the 16%, 50% (median), 84% values of the PDFs." (3 SED models)
   - validation: Compared codes and models; tested cigale burst fraction recovery on merger simulations  
  > "Likewise, we test cigale using merger simulations to check whether the burst fraction can be reasonably recovered." (4.1 Star formation history)

## Software

- **CRUSH** v2.34-4: HAWC+ data reduction  
  > "The raw data was processed through the CRUSH pipeline v2.34-4 (cite: Kovacs2008)" (2.1 SOFIA/HAWC+)
- **cigale** v0.11: SED fitting  
  > "the Code Investigating GALaxy Emission (cigale version v0.11; (cite: Noll2009; Roehlly2014))" (3 SED models)
- **sed3fit** : SED fitting with AGN  
  > "we employ two SED fitting codes, sed3fit (cite: Berta2013)" (3 SED models)
- **magphys** : Earlier fit and high-z version  
  > "which did not include AGN templates nor radio emission" (3 SED models)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Observed 89 um flux density | 748.4 | 101.1 | mJy | 1 | the resultant flux density is 748.4 $\pm$ 101.1 mJy |
| De-magnified 89 um flux density | 77.2 | 11.8 | mJy | 1 | the de-magnified flux density at 89 $\ensuremath{\mu}m$ is 77.2 $\pm$ 11.8 mJy. |
| AGN IR fraction 3 sigma upper limit | <0.72 | not stated | % | 2 | 3 $\sigma$ upper limit $f^{\rm AGN}_{\rm IR}$ $<$ 0.72% |
| Stellar mass range across models | 2.1e10 to 8.3e11 | not stated | Msun | 2 | / $M_*$ (10$^{10}$ M$_\ensuremath{\odot}$) / 13.2$^{+6.3}_{-4.1}$ / 44$^{+26}_{-18}$ / 83$^{+43}_{-29}$ / 2.1 $\pm$ 0.5 / 3.4 $\pm$ 1.1 / 15.1 $\pm$ 1.2 / |

## Qualitative findings

- Dust luminosity is the best constrained parameter and is consistent across models, >4e12 Lsun  
  > "The dust luminosity is the best constrained parameter with least uncertainty" (4.2 Dusty system)

## Claim tuples

- H: An energetically important AGN contributes to the IR luminosity | E: SED fits with AGN templates in sed3fit and cigale | R: f_AGN,IR upper limit <0.72% | F: AGN contribution is negligible | **supported**
- H: Stellar mass is robust given extensive photometry | E: Compared models and codes | R: Stellar mass varies by up to a factor of about 10 depending on SFH | F: SFH dominates the stellar mass uncertainty | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Blue end of the sed3fit SED is dominated by a spurious AGN component because of upper limits, so SED alone cannot indicate AGN  
  > "We cannot rely on the SED fitting alone to infer AGN activity in this case" (4.3 Negligible AGN contribution)
- Caveat (inferred, ours): ALMA data are only reused photometry
- Caveat (inferred, ours): Model grids are only partly described
- Caveat (inferred, ours): Burst-fraction test with merger simulations is not detailed

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Full cigale/sed3fit parameter grids
- Missing: HAWC+ raw data access details
- Missing: merger simulation test details
- Data volume (inferred): small (photometry table only)
- Score (inferred): 3/5, Photometry table is given and the codes are public, but grids and HAWC+ details are incomplete.
- Rediscovery candidate: no, ALMA data are not directly processed; the SED fits depend on unspecified parameter grids.

## Links

- Method: (cite: Berta2013) (sed3fit)
- Method: (cite: Noll2009; Roehlly2014) (cigale)
- Method: (cite: daCunha2015) (high-z magphys)
- Companion: (cite: Messias2014) (Source photometry, lens model, earlier SED analysis)
- Related: H-ATLAS
- Related: SOFIA Cycle 5 PID05_0087

## Checks

```json
{
 "quotes": 28,
 "quotes_ok": 28,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00476.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 61,
  "stated": 19,
  "rate": 0.311
 },
 "evidence_ok": true
}
```
