# “Super-deblended” Dust Emission in Galaxies. II. Far-IR to (Sub)millimeter Photometry and High-redshift Galaxy Candidates in the Full COSMOS Field

`2018ApJ...864...56J` | The Astrophysical Journal 2018 | first author: Jin, Shuowen | arXiv: 1807.04697 | DOI: 10.3847/1538-4357/aad4af

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies
- Question: Build a super-deblended FIR to (sub)mm photometric catalog in the full COSMOS field and select z>4 dusty galaxy candidates; ALMA archival photometry is used to validate the 850 um photometry.  
  > "We present a “super-deblended” far-infrared to (sub)millimeter photometric catalog in the Cosmic Evolution Survey (COSMOS)" (abstract)
- Target **COSMOS field**: coordinates _not stated_; z/distance z up to ~7 for candidates  
  > "Its nearly 2 square degrees sky coverage, as well as the wealth of deep FIR/(sub)mm imaging" (Introduction); distance from SED fitting; photometric/spectroscopic redshifts  
  > "Its nearly 2 square degrees sky coverage, as well as the wealth of deep FIR/(sub)mm imaging" (Introduction)

## Data provenance

- ALMA projects: _none stated_
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ≈1'' ALMA resolution  
  > "benefiting from the exquisite $\approx1''$ ALMA resolution which resolves all blending issues" (Comparison to ALMA archival photometry)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Public ALMA archival data in COSMOS processed by the A3COSMOS project (private communication catalogs)  
  > "These ALMA data were reduced, imaged and analyzed in the on-going ALMA archive mining project A$^3$COSMOS (D. Liu et al., in prep.)" (Comparison to ALMA archival photometry)
- Other facility **Spitzer/MIPS 24um, Herschel PACS/SPIRE, JCMT SCUBA2, ASTE AzTEC, IRAM MAMBO, VLA 1.4/3 GHz**: Images deblended to produce the main photometric catalog  
  > "The resulting photometry (including data from Spitzer, Herschel, SCUBA2, AzTEC, MAMBO and NSF’s Karl G. Jansky Very Large Array at 3 GHz and 1.4 GHz)" (abstract)
- External data: A3COSMOS ALMA prior-fitting continuum photometry catalog used for comparison  
  > "Here we use their catalogs in advance (priv. comm.)" (Comparison to ALMA archival photometry) [from D. Liu et al., in prep. (A3COSMOS)]
- External data: COSMOS2015 catalog, source of K_s priors, photo-z and stellar masses  
  > "The COSMOS2015 catalog (cite: Laigle2016) from UltraVISTA-DR2 survey contains 1,182,108 $YJHK_s$ sources in total" (3.1) [from (cite: Laigle2016)]

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

- Super-deblending method, SED fitting recipes and parameters, Monte Carlo calibration  
  > "The SED fitting recipes and parameters are identical to those in L18." (4.2) [from (cite: Liu_DZ2017) (L18)]
- ALMA reduction and imaging done by A3COSMOS team  
  > "These ALMA data were reduced, imaged and analyzed in the on-going ALMA archive mining project A$^3$COSMOS (D. Liu et al., in prep.)" (Comparison to ALMA archival photometry) [from D. Liu et al., in prep.]

### Not stated but needed to reproduce (our reading)

- ALMA project codes and observation setups for the archival data used
- A3COSMOS catalog (not yet public at time of paper) and ALMA calibration/imaging details
- Exact matching radius and source selection for the ALMA comparison
- Conversion between ALMA band flux and 850 um

## Analysis recipe

1. **Compare super-deblended 850um fluxes to ALMA photometry**: Cross-match common sources with A3COSMOS prior-fitting catalog; histogram of flux difference normalized by quadrature-summed uncertainty  
  > "we further show the histogram of the flux difference between the two works normalized by the total uncertainty (quadratic sum of both errors from this work and A$^3$COSMOS)" (Comparison to ALMA archival photometry)
   - fitting: Gaussian with sigma fixed to 1 overlaid  
  > "A Gaussian fit with sigma fixed to 1 is overlaid on the histogram" (Comparison to ALMA archival photometry)
   - validation: Median and scatter of normalized difference  
  > "The median of the distribution is -0.14 and the sigma (scatter) is 0.9, which is very close to 1, indicating that the scatter is consistent with the photometric error." (Comparison to ALMA archival photometry)

## Software

- **galfit** : PSF fitting photometry on prior positions  
  > "We obtain PSF-fitting photometry with *galfit* (cite: Peng2002; Peng2010)" (3.2)
- **SExtractor** : Blind extraction of sources in residual maps  
  > "we blindly extract residual sources with SExtractor (cite: Bertin1996) in the residual maps" (4.5)
- **PyBDSM** : Blind source extraction in A3COSMOS ALMA catalog  
  > "blind source extraction (mainly with the code PyBDSM)" (Comparison to ALMA archival photometry)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Median of normalized flux difference, SD vs ALMA 850um | -0.14 | not stated | dimensionless | 1 | The median of the distribution is -0.14 and the sigma (scatter) is 0.9 |
| Scatter of normalized flux difference | 0.9 | not stated | dimensionless | 1 | The median of the distribution is -0.14 and the sigma (scatter) is 0.9 |
| Galaxies with S/N_FIR+mm>5 | 11220 | not stated | galaxies | 0 | We detect 11,220 galaxies over the 100–1200 $\mu$m range |
| z>4 candidates | 85 | not stated | galaxies | 0 | We conservatively selected a sample of 85 $z>4$ high redshift candidates |

## Qualitative findings


## Claim tuples

- H: Super-deblended 850um fluxes and errors are correct | E: Compare with A3COSMOS ALMA photometry for common sources | R: Median -0.14, scatter 0.9 in normalized difference; no systematic bias | F: Fluxes and uncertainties are well defined | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): ALMA covers only a small fraction of COSMOS  
  > "while ALMA, on the other hand, currently only covers a very small fraction of the COSMOS field" (Comparison to ALMA archival photometry)
- Caveat (inferred, ours): ALMA comparison relies on unpublished private-communication catalogs
- Caveat (inferred, ours): ALMA pre-selection biases the bright subsample

## Reproducibility

- Data public (paper): ALMA data are public archival; photometric catalog publicly released  
  > "We further use 1000+ public ALMA archival data at submm-wavelengths in the COSMOS field" (Comparison to ALMA archival photometry)
- Products in archive: _not stated_
- Missing: A3COSMOS catalog and ALMA project list
- Missing: Pipeline code for super-deblending not stated as released
- Data volume (inferred): Large (hundreds of GB for non-ALMA maps; ALMA part is a catalog comparison)
- Score (inferred): 2/5, ALMA role is a catalog comparison using unpublished catalogs; main work is on non-ALMA data.
- Rediscovery candidate: no, ALMA catalogs were private; main recipe relies on L18 and non-ALMA data.

## Links

- Method: (cite: Liu_DZ2017) (Super-deblending method)
- Related: A3COSMOS
- Related: COSMOS
- Related: HerMES
- Related: S2CLS

## Checks

```json
{
 "quotes": 24,
 "quotes_ok": 24,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00097.S",
  "2011.0.00539.S",
  "2012.1.00978.S",
  "2013.1.00034.S",
  "2013.1.00118.S",
  "2013.1.00208.S",
  "2013.1.00884.S",
  "2013.1.01292.S",
  "2015.1.00055.S",
  "2015.1.00137.S",
  "2015.1.00568.S",
  "2015.1.01074.S",
  "2015.1.01495.S",
  "2016.1.00478.S",
  "2016.1.00735.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 55,
  "stated": 18,
  "rate": 0.327
 },
 "evidence_ok": true
}
```
