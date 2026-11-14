# On the Nature of the Compact Sources in IRAS 16293-2422 Seen at Centimeter to Submillimeter Wavelengths

`2019ApJ...875...94H` | The Astrophysical Journal 2019 | first author: Hernández-Gómez, Antonio | arXiv: 1903.02202 | DOI: 10.3847/1538-4357/ab0c97

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: What is the nature of the compact sources (A1, A2, A2alpha/beta, B) in IRAS 16293-2422, based on their radio-to-submillimeter spectra, sizes, variability and proper motions?  
  > "the exact number of protostars within IRAS 16293–2422, their relative evolutionary stages, and their relationship with known radio sources and outflows in the system, remain elusive." (Introduction)
- Target **IRAS 16293-2422**: coordinates _not stated_; z/distance 141 pc  
  > "so we will use 141 pc for the distance to IRAS 16293–2422 in the rest of the paper." (Introduction); distance from Dzib et al. 2018 (water maser astrometry)  
  > "so we will use 141 pc for the distance to IRAS 16293–2422 in the rest of the paper." (Introduction)

## Data provenance

- ALMA projects: 2013.1.00061.S, 2013.1.00018.S
- bands: _not stated_
- frequencies and spectral setup: ALMA continuum images at 227–695 GHz (0.4–1.3 mm)  
  > "We have also used interferometric ALMA observations covering the frequency range from 230 GHz to 700 GHz" (2.2 ALMA observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: VLA A, BnA and B configurations  
  > "in the most extended configurations (A, BnA, and B) of the array" (2.1 Very Large Array observations)
- baselines: _not stated_
- angular resolution: better than 0.4 arcsec selected for ALMA  
  > "We selected only observations with an angular resolution better than $0\mbox{$''\mskip-7.6mu.\,$}4$ so that the source size of source B could be properly deconvolved" (2.2 ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: ALMA epochs 2012-04-17 to 2015-08-29 (Table 1); VLA 2011–2015  
  > "New Very Large Array (VLA) observations of IRAS 16293–2422 were obtained between 2011 and 2015 in the most extended configurations (A, BnA, and B) of the array" (2.1 Very Large Array observations)
- pi or archival as stated: _not stated_
- Other facility **VLA**: Multi-epoch continuum 2–42 GHz, new data 2011–2015  
  > "They covered the frequency range from 2 to 42 GHz" (2.1 Very Large Array observations)
- Other facility **Japanese Virtual Observatory (JVO)**: Source of ALMA images at 227–453 GHz  
  > "The ALMA project numbers correspond to the ID numbers given in the Japanese Virtual Observatory (JVO) from where the data sets were obtained." (Table 1 notes)
- External data: VLA observations 1986–2008 used for spectra, sizes and proper motions  
  > "we will also make use of the continuum VLA observations from (cite: Chandler2005) and (cite: Pech2010) carried out between 1986 and 2008." (2.1 Very Large Array observations) [from (cite: Chandler2005); (cite: Pech2010)]
- External data: Fraction of luminosity from source A (85%) and B (15%)  
  > "(cite: Jacobsen2018) estimate that around 85% of that the total luminosity of IRAS 16293–2422 is attributable to source A" (3.1 Spectra) [from (cite: Jacobsen2018)]
- External data: Solar motion values for reflex motion  
  > "Assuming the values provided by (cite: schonrich2010) for the Solar motion" (3.4 Astrometry) [from (cite: schonrich2010)]

## Processing

### Calibration

- pipeline or manual: VLA calibration pipeline 1.3.1 for VLA; ALMA images taken from archive/JVO  
  > "We used the VLA calibration pipeline (version 1.3.1) provided by NRAO to flag and calibrate all our datasets with the CASA software package (version 4.2.2)." (2.1 Very Large Array observations)
- casa version: CASA 4.2.2 (VLA)  
  > "with the CASA software package (version 4.2.2)" (2.1 Very Large Array observations)
- pipeline version: _not stated_
- archive products used as is: ALMA 227–453 GHz images downloaded from JVO, not self-calibrated  
  > "These images correspond to data that have not been self-calibrated, and we assume a 10% error on the source sizes derived from them." (2.2 ALMA observations)
- flux calibrator: 3C 286 (VLA)  
  > "The flux scale was set using the standard calibrator 3C 286." (2.1 Very Large Array observations)
- flux scale uncertainty: VLA 10% up to 15 GHz, 15% above; ALMA 15% below 400 GHz, 20% above  
  > "The absolute flux uncertainty, on the other hand, is assumed to be 15% for frequencies below 400 GHz, and 20% above 400 GHz." (2.2 ALMA observations)
- self calibration: Applied to VLA data; ALMA Band 9 SV data self-calibrated  
  > "In addition, we used the Band 9 Science Verification observation of IRAS 16293–2422 as available on almascience.nrao.edu, these data were self-calibrated." (2.2 ALMA observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: robust = 0 in CASA (VLA)  
  > "(robust = 0 in CASA)" (2.1 Very Large Array observations)
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
- final beam: See Table 1 per dataset (e.g. 0.53x0.25 arcsec at 227 GHz)  
  > "$0\mbox{$''\mskip-7.6mu.\,$}53$$\times$$0\mbox{$''\mskip-7.6mu.\,$}25$ ; $+$$87\mbox{$^\circ\mskip-7.6mu.\,$}2$" (Table 1)
- final rms: _not stated_

### Inherited from earlier work

- Reduction of pre-2011 VLA data described in original papers  
  > "The reduction and calibration of these data are described in details in the original papers." (2.1 Very Large Array observations) [from (cite: Chandler2005); (cite: Pech2010)]

### Not stated but needed to reproduce (our reading)

- ALMA project codes for each JVO image (only JVO IDs given in Table 1)
- Mapping of the JVO IDs to archive MOUS/data sets
- Imaging parameters and CASA version for ALMA images
- Self-calibration solution intervals for VLA
- Region definitions and fit initial guesses for flux/size measurements
- Fitting method for spectral index (weights, errors)
- Source of the 0.12 arcsec 300 GHz map (private communication)

## Analysis recipe

1. **Calibrate and image VLA data**: VLA pipeline calibration, self-calibration, imaging with robust=0  
  > "The calibrated visibilities were imaged using a weighting scheme intermediate between natural and uniform (robust = 0 in CASA)" (2.1 Very Large Array observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure flux densities of A and B**: Gaussian fit for B; IMFIT multi-component for A, region for total  
  > "For source B, we used a gaussian fit since its structure at all wavelengths is well defined." (3.1 Spectra)
   - software: CASA
   - fitting: _not stated_
   - validation: Refit excluding extreme points gave nearly identical result  
  > "we also fitted the data ignoring these two extreme points. This fit is very nearly identical to that obtained including all points." (3.1 Spectra)
3. **Fit power-law spectra**: Power-law F ∝ ν^α fits to flux densities; two power laws for A  
  > "the fluxes can be fitted by two separate power laws $F_{\nu} \propto \nu^{\alpha}$" (3.1 Spectra)
   - fitting: _not stated_
   - validation: _not stated_
4. **Measure source sizes and brightness temperatures**: Deconvolved sizes vs frequency (Table 2); Tb in central pixel  
  > "Deconvolved size of source B as a function of frequency" (Table 2)
   - assumption: 10% error on ALMA source sizes  
  > "we assume a 10% error on the source sizes derived from them" (2.2 ALMA observations)
   - fitting: _not stated_
   - validation: _not stated_
5. **Derive proper motions and variability**: Linear proper motion fit to absolute positions; fluxes rescaled to 15 GHz using spectral indices  
  > "These values were obtained by fitting a linear and uniform proper motion to the measured absolute positions." (3.4 Astrometry)
   - assumption: Second-order polynomial fits better but rejected as unphysical  
  > "since accelerated absolute proper motions are unphysical in our case, we will use the linear fits" (3.4 Astrometry)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.2.2: VLA calibration, imaging, IMFIT flux measurement  
  > "We have used CASA to measure the flux densities for A and B." (3.1 Spectra)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Spectral index of source B (2–700 GHz) | 2.28 | 0.02 | dimensionless | 3 | the entire spectrum from 2 to 700 GHz can be modelled by a single power-law with spectral index $\alpha=2.28 \pm 0.02$ |
| Spectral index of B, ALMA points only | 1.83 | 0.08 | dimensionless | 3 | Using only the ALMA points yields a somewhat smaller spectral index of 1.83$\pm$0.08 |
| Spectral index of A at >100 GHz | 2.50 | 0.22 | dimensionless | 3 | At $\nu > 100$ GHz, the spectral index derived from the data is $2.50\pm 0.22$ |
| Spectral index of A at <100 GHz | 0.44 | 0.05 | dimensionless | 3 | $\alpha=0.44 \pm 0.05$ |
| Size of source B in mm regime | 385 | 5 | mas | 4 | the size remains constant at 385$\pm$5 mas (54.3$\pm$0.7 AU assuming a distance of 141 pc |
| Brightness temperature of B at 700 GHz | 182 | not stated | K | 4 | we have $T_b$ = 182 K in the central pixel |
| Mean 15 GHz flux of A | 4.08 (dispersion 0.83) | not stated | mJy | 5 | the mean flux of source A (expressed at the reference frequency of 15 GHz) is found to be 4.08 mJy with a dispersion of 0.83 mJy |
| Proper motion of A2 relative to A2alpha ejecta | 63 | 3 | mas/yr | 5 | respectively 63$\pm$3 mas yr$^{-1}$ at a position angle $+$62$\pm$10$^\circ$ |

## Qualitative findings

- Source B emission is dust-dominated down to 2 GHz and shows no excess free-free; B does not drive a powerful ionized outflow  
  > "We conclude that source B does not drive a powerful ionized outflow." (3.1 Spectra)

## Claim tuples

- H: Is source B's emission dust-dominated across the whole radio-to-submm range? | E: Combined VLA and ALMA flux densities fitted by a power law | R: alpha = 2.28±0.02 from 2 to 700 GHz | F: Dust dominates even at 10 cm | **supported**
- H: Is B a finite dusty structure becoming optically thick? | E: Deconvolved size vs frequency | R: Size increases up to ~41 GHz then constant at 0.39 arcsec | F: Optically thick at mm wavelengths, central T at least ~1000 K | **supported**
- H: Is A2 a protostar driving ejections, and what is A1? | E: Multi-epoch VLA astrometry | R: A2alpha/beta move symmetrically from A2; A1-A2 position angle began to decrease | F: A2 is a protostar; A1 nature remains open (shock feature or hierarchical triple) | **partially**

## Reasoning

- Why this data: Only ALMA observations with resolution better than 0.4 arcsec chosen to deconvolve B  
  > "so that the source size of source B could be properly deconvolved" (2.2 ALMA observations)
- Why this method: _not stated_
- Alternative: Second-order polynomial proper motions fit better but rejected as unphysical  
  > "we find that a second order polynomial does reproduce the data significantly better" (3.4 Astrometry)
- How they decided it was enough: _not stated_
- Limitation (authors): ALMA high-frequency points fall below power law; Tb difference attributed to opacity, with unpublished higher-resolution map  
  > "the highest frequency (ALMA) data points do tend to fall below the power-law fit" (3.1 Spectra)
- Caveat (inferred, ours): ALMA fluxes from unselfcalibrated archive images with assumed errors
- Caveat (inferred, ours): Spectral index and size uncertainties depend on assumed flux errors
- Caveat (inferred, ours): Interpretation of Tb relies on a private-communication map
- Caveat (inferred, ours): Different resolutions and epochs mix variability and source structure

## Reproducibility

- Data public (paper): ALMA images from JVO and almascience archive  
  > "Images at frequencies between 227 and 453 GHz were downloaded from the database hosted by the Japanese ALMA Observatory" (2.2 ALMA observations)
- Products in archive: _not stated_
- Missing: Exact ALMA dataset identification and imaging details
- Missing: VLA imaging and self-cal details
- Missing: Fit procedures
- Data volume (inferred): Small if using archive images (~GBs); tens of GB for VLA visibilities
- Score (inferred): 3/5, Public data and simple measurements, but several processing details unstated.
- Rediscovery candidate: no, Recipe incomplete in imaging and fitting details and uses a private-communication map.

## Links

- Method: (cite: Chandler2005) (Earlier spectra, sizes and VLA data of the same sources)
- Companion: (cite: Pech2010) (Earlier multi-epoch VLA astrometry)
- Related: VLA 10C-222, 12B-088, 14A-313, 15A-363
- Related: ALMA Science Verification Band 9

## Checks

```json
{
 "quotes": 49,
 "quotes_ok": 49,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00007.SV"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 35,
  "rate": 0.5
 },
 "evidence_ok": true
}
```
