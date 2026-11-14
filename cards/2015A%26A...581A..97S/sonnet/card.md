# Collisional modelling of the AU Microscopii debris disc

`2015A&A...581A..97S` | Astronomy and Astrophysics 2015 | first author: Schüppler, Ch. | arXiv: 1506.04564 | DOI: 10.1051/0004-6361/201525664

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: debris_disks
- Question: What dust production, dust transport and planetesimal dynamics in the AU Mic debris disc are consistent with the SED, the ALMA 1.3 mm radial profile and scattered light data?  
  > "aiming at a comprehensive understanding of the dust production and the dust and planetesimal dynamics in the system" (abstract)
- Target **AU Mic**: coordinates _not stated_; z/distance 9.9 pc  
  > "AU Mic (GJ 803, HD 197481) is an M1 V dwarf at a distance of 9.9 pc" (2.1 Stellar properties); distance from Perryman1997; vanLeeuwen2007  
  > "AU Mic (GJ 803, HD 197481) is an M1 V dwarf at a distance of 9.9 pc" (2.1 Stellar properties)

## Data provenance

- ALMA projects: 2011.0.00142.S, 2011.0.00274.S
- bands: Band 6 (1.3 mm)  
  > "ALMA observations of AU Mic in Band 6 (1.3 mm) have been carried out as part of the cycle 0 early science observations" (2.2 ALMA observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 21 – 402 m, 20 12-m antennae  
  > "A total of 20 operational 12-m antennae were used, spanning baselines of 21 – 402 m" (2.2 ALMA observations)
- angular resolution: 0.69'' x 0.79'' (dirty beam FWHM)  
  > "effective angular resolution ($FWHM$ of the reconstructed dirty beam) of $0.69\ensuremath{''} \times 0.79\ensuremath{''}$" (2.2 ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 16 June 2012  
  > "The data considered in the present work were taken on 16 June 2012" (2.2 ALMA observations)
- pi or archival as stated: _not stated_
- Other facility **Herschel PACS/SPIRE**: Archival far-IR photometry for the SED  
  > "we included archival *Herschel* (cite: Pilbratt2010) PACS (cite: Poglitsch2010) and SPIRE (cite: Griffin2010; Swinyard2010) data" (2.3 Auxiliary data)
- Other facility **HST/Keck scattered light**: V- and H-band surface brightness profiles and polarisation from literature  
  > "our models are compared with the optical and near-IR surface brightness profiles from (cite: Fitzgerald2007) and (cite: Schneider2014) and with the measured degree of polarisation from (cite: Graham2007)" (2.4 Scattered light)
- External data: Photometric SED points (WISE, Spitzer, IRAS, Akari, SMA, JCMT etc.)  
  > "In addition to the ALMA data, we considered for modelling a variety of photometric data from earlier work." (2.3 Auxiliary data) [from Table of fluxes references (C12, W10, M90, W12, L04, etc.)]
- External data: Photosphere model: Teff 3700 K, L 0.09 Lsun, log g 4.5  
  > "We used the photosphere model of (cite: Augereau&Beust2006) with an effective temperature of 3700 K" (2.1 Stellar properties) [from (cite: Augereau&Beust2006)]
- External data: Disc position angle 128.41 deg  
  > "a position angle of $128.41 \pm 0.13$$^\circ$ (cite: MacGregor2013)" (2.2 ALMA observations) [from (cite: MacGregor2013)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10% absolute photometric calibration  
  > "an absolute photometric calibration uncertainty of 10% (cite: MacGregor2013)" (2.2 ALMA observations)
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

- ALMA data reduction approach  
  > "We followed the approach used by (cite: MacGregor2013) and came to consistent conclusions." (2.2 ALMA observations) [from (cite: MacGregor2013)]
- Profile extraction adopted from Herschel DUNES approach  
  > "we largely adopted the approach used for *Herschel* data obtained in the context of the Open Time Key Programme DUst around NEarby Stars" (2.2 ALMA observations) [from (cite: Loehne2012; Eiroa2013; Ertel2014)]
- Fragmentation strength parameters  
  > "$b_\text{s}=-0.37$, $b_\text{g}=1.38$, and $\kappa=0.5$ (cite: Loehne2012)" (3.2 Grain material) [from (cite: Loehne2012)]

### Not stated but needed to reproduce (our reading)

- CASA version, imaging task and weighting for the re-reduction
- Calibration/flagging details and flux calibrator
- Number of ACE grid points and size range of the grid
- Fitting range and details of SAnD chi2 (error handling)
- Scaling factors applied to ALMA profile per model

## Analysis recipe

1. **Extract ALMA radial profile and fluxes**: Rebin image 10x with cubic spline, rotate by 38.41 deg, integrate 11x11 subpixel boxes along the major axis spaced 0.74''; average SE and NW sides  
  > "rebinned the image with an original pixel scale of 0.1$''$/pixel to a ten times smaller pixel scale using a cubic spline interpolation and rotated it by an angle of 38.41$^\circ$ clockwise" (2.2 ALMA observations)
   - software: CASA
   - parameter: Jy/beam to Jy/pixel factor 0.0185  
  > "multiplying them with a factor of 0.0185 derived by integrating the core of the reconstructed dirty beam" (2.2 ALMA observations)
   - fitting: _not stated_
   - validation: Compared with MacGregor et al. fluxes  
  > "which is consistent with $7.46\pm0.76$ mJy from (cite: MacGregor2013)" (2.2 ALMA observations)
2. **Collisional modelling of outer disc**: ACE simulations varying wind strength, material, e_max, belt width; fit SED vertical scaling by timestep; compare to scaled convolved 1.3 mm profile, scattered light and polarisation  
  > "we vary other initial disc parameters of this reference run in order to more tightly constrain the parameters and reveal degeneracies among them" (4 Resolved outer disc)
   - software: ACE
   - parameter: Belt at 40 au, width 5 au, e_max=0.03, SW50 reference, material M1  
  > "having the full width $\Delta r_\mathrm{PB}=5$ au. In all three runs, the maximum eccentricity of the planetesimals was set to $e_\text{max}=0.03$" (4.1 Stellar wind strength)
   - assumption: Inclination 89.5 deg; Mie spheres; wind speed 400 km/s; stellar mass 0.5 Msun  
  > "we assumed a disc inclination of 89.5$^\circ$ from face-on (cite: Krist2005)" (4.1 Stellar wind strength)
   - fitting: Not fitted; chi2_SED/N used for comparison only  
  > "We stress that the models are not fitted to the data through variations of the initial disc parameters." (4.1.1 Impact on thermal emission)
   - validation: Compare to SED, ALMA profile, scattered light and polarisation  
  > "First, we seek to explain the available observational data on the resolved outer AU Mic disc, including the SED, the ALMA radial brightness profile, and scattered light measurements." (Resolved outer disc)
3. **Power-law parametric fit**: Grid fit of two power laws (radial and size) to SED and ALMA profile, with and without inner ring  
  > "we used the `SAnD` code (cite: Ertel2012; Loehne2012)" (6 Comparison with parametric modelling)
   - software: SAnD
   - assumption: Compact astronomical silicate grains, inclination 90 deg, s_max 2 mm  
  > "We fixed $s_\mathrm{max}$ to 2 mm." (6 Comparison with parametric modelling)
   - fitting: Grid chi2 minimisation with 3 sigma intervals  
  > "we additionally analysed the data with a multidimensional fitting approach." (Comparison with parametric modelling)
   - validation: Compared with collisional results  
  > "In order to find an independent confirmation of the collisional modelling results, we additionally analysed the data with a multidimensional fitting approach." (Comparison with parametric modelling)

## Software

- **CASA** : Re-reduction of ALMA data and dirty beam  
  > "Our re-reduction of the data was carried out in the Common Astronomy Software Applications (cite: McMullin2007)." (2.2 ALMA observations)
- **ACE** : Collisional evolution modelling  
  > "Collisional modelling with our code `ACE` (Analysis of Collisional Evolution)" (3 Collisional modelling)
- **SAnD** : Power-law fits of SED and ALMA profile  
  > "we used the `SAnD` code (cite: Ertel2012; Loehne2012)" (6 Comparison with parametric modelling)
- **HIPE** 11: Herschel data processing  
  > "version 11 and the calibration plan versions v56 and v11 for PACS and SPIRE" (2.3 Auxiliary data)
- **SExtractor** : SPIRE 350/500 micron photometry  
  > "were measured using SExtractor (cite: Bertin&Arnouts1996)" (2.3 Auxiliary data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA total flux density | 8.75 | 0.98 | mJy | 1 | We found a total flux density of $8.75\pm0.98$ mJy |
| Inner unresolved component flux density | 0.29 | 0.05 | mJy | 1 | we estimated a flux density of this component of $0.29 \pm 0.05$ mJy |
| Power-law best-fit R_out | 41.9 | 3 sigma 37.3 – 45.5 | au | 3 | 41.9 \[37.3 – 45.5\] |
| Power-law surface density index alpha | 2.8 | 3 sigma 1.8 – 4.8 | dimensionless | 3 | 2.8 \[1.8 – 4.8\] |
| Max fraction of central emission from inner dust ring | 60 | not stated | % | 2 | emits at most 60% of the observed central emission |

## Qualitative findings

- Dust from a belt with outer edge near 40 au transported inward by winds reproduces SED and ALMA profile shape; scattered light and polarisation deviate  
  > "While the spectral energy distribution and the shape of the ALMA radial profile are well reproduced, the models deviate from the scattered light observations more strongly." (abstract)

## Claim tuples

- H: What stellar wind strength fits the disc? | E: Runs SW0, SW50, SW300 | R: SW50 best matches SED and polarisation; SW300 gives red V-H | F: Mass loss about 50 times solar preferred | **supported**
- H: Can an inner dust ring explain the central ALMA emission? | E: Inner ring models with M1, M3, M5 | R: At most ~60% of central emission | F: Emission partly from stellar chromosphere | **supported**
- H: What planetesimal excitation is preferred? | E: e_max 0.01, 0.03, 0.1 | R: 0.03 matches entire SED best | F: Low excitation preferred | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Mie spheres may be inadequate; HG phase function tested  
  > "we adapted the (cite: Graham2007) best-fit Henyey-Greenstein (HG) model" (4.1.2 Impact on scattered light)
- How they decided it was enough: _not stated_
- Limitation (authors): Axisymmetric discs only; models not unique  
  > "All the models presented here are not unique as a full exploration of the parameter space by collisional modelling is impossible." (7 Conclusions)
- Caveat (inferred, ours): Models underestimate ALMA flux and need scaling factors up to 2
- Caveat (inferred, ours): No formal fitting or uncertainties for collisional models
- Caveat (inferred, ours): Mie theory limits scattered light conclusions

## Reproducibility

- Data public (paper): Cycle 0 archival ALMA data acknowledged by project code  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00274.S and ADS/JAO.ALMA#2011.0.00142." (7 Conclusions)
- Products in archive: _not stated_
- Missing: ACE code availability
- Missing: CASA reduction parameters
- Missing: Final scaling factors
- Data volume (inferred): ~ few GB
- Score (inferred): 3/5, ALMA part is simple but the ACE code is not released and modelling is heavy.
- Rediscovery candidate: no, Main results come from the unreleased ACE code and long simulations.

## Links

- Method: (cite: Loehne2012) (ACE application and SAnD)
- Companion: (cite: MacGregor2013) (Original ALMA analysis of the same data)
- Related: Herschel DUNES

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
 "codes_not_in_obscore": [
  "2011.0.00274.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 37,
  "rate": 0.514
 },
 "evidence_ok": true
}
```
