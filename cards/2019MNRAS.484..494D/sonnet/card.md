# An ALMA view of CS and SiS around oxygen-rich AGB stars

`2019MNRAS.484..494D` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Danilovich, T. | arXiv: 1901.00070 | DOI: 10.1093/mnras/stz002

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars, astrochemistry
- Question: What are the radial distributions and abundances of CS and SiS in the CSEs of oxygen-rich AGB stars with different mass-loss rates (IK Tau, W Hya, R Dor)?  
  > "We aim to determine the distributions of molecular SiS and CS in the circumstellar envelopes of oxygen-rich asymptotic giant branch stars" (abstract)
- Target **IK Tau**: coordinates 03 53 28.9 +11 24 21.9  
  > "| IK Tau | 03 53 28.9 |  +11 24 21.9  |                   34                    |" (Table 1); "| Distance \[pc\]                            |  265   |  59   |  78   |" (Table 3); z/distance 265 pc  
  > "| IK Tau | 03 53 28.9 |  +11 24 21.9  |                   34                    |" (Table 1); "| Distance \[pc\]                            |  265   |  59   |  78   |" (Table 3); distance from Danilovich2017 and references therein  
  > "| IK Tau | 03 53 28.9 |  +11 24 21.9  |                   34                    |" (Table 1); "| Distance \[pc\]                            |  265   |  59   |  78   |" (Table 3)
- Target **W Hya**: coordinates 13 49 02.0 -28 22 03.5  
  > "| W Hya  | 13 49 02.0 | $-$28 22 03.5 |                  40.5                   |" (Table 1); z/distance 78 pc  
  > "| W Hya  | 13 49 02.0 | $-$28 22 03.5 |                  40.5                   |" (Table 1); distance from Danilovich2017 and references therein  
  > "| W Hya  | 13 49 02.0 | $-$28 22 03.5 |                  40.5                   |" (Table 1)
- Target **R Dor**: coordinates 04 36 45.6 -62 04 37.8  
  > "| R Dor  | 04 36 45.6 | $-$62 04 37.8 |                   7.5                   |" (Table 1); z/distance 59 pc  
  > "| R Dor  | 04 36 45.6 | $-$62 04 37.8 |                   7.5                   |" (Table 1); distance from Danilovich2017 and references therein  
  > "| R Dor  | 04 36 45.6 | $-$62 04 37.8 |                   7.5                   |" (Table 1)

## Data provenance

- ALMA projects: 2013.1.00166.S, 2015.1.01446.S
- bands: Band 7, 335–362 GHz (IK Tau, R Dor)  
  > "Spectral scans of IK Tau and R Dor were taken with ALMA in the range 335–362 GHz (in Band 7)" (2.1 ALMA observations and data reduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 40 m–1.6 km (IK Tau, R Dor); 17 m–11 km (W Hya)  
  > "The interferometer baseline lengths were in the range 40 m to 1.6 km" (2.1 ALMA observations and data reduction); "W Hya was observed on baselines from 17 m to 11 km" (2.1 ALMA observations and data reduction)
- angular resolution: ~150 mas (IK Tau, R Dor); ~0.1" for W Hya cubes (35x28 mas at high resolution)  
  > "giving a synthesised beam of about 0.1$''$ (depending on frequency)" (2.1 ALMA observations and data reduction)
- max recoverable scale: 2" (IK Tau, R Dor); ~6" (W Hya)  
  > "which allowed for imaging of structure up to angular scales of 2$''$" (2.1 ALMA observations and data reduction)
- sensitivity: IK Tau 3–9 mJy rms per 1.7 km/s channel; R Dor 2.7–5.7 mJy; W Hya ~2.1–2.5 mJy at 2 km/s  
  > "For R Dor the image cubes have a channel resolution of 0.8–0.9km s$^{-1}$ with rms noise in the range 2.7–5.7 mJy." (2.1 ALMA observations and data reduction)
- time on source: _not stated_
- observing dates: Aug–Sep 2015 (IK Tau, R Dor); 30 Nov, 3 and 5 Dec 2015 (W Hya)  
  > "observed by ALMA with long baselines on 30 November and 3 and 5 December 2015" (2.1 ALMA observations and data reduction)
- pi or archival as stated: _not stated_
- Line: CS 7-6 (342.8828 GHz)
- Line: SiS 19-18 v=0 (344.7795 GHz)
- Other facility **APEX/IRAM single-dish**: Single-dish CS and SiS spectra used as extra model constraints and to check for resolved-out flux  
  > "Where possible we have included previously observed single-dish observations to add constraints to our models" (3.1 Modelling procedure)
- External data: Stellar and CSE parameters (luminosity, distance, T*, mass-loss rate, expansion velocity)  
  > "All parameters are taken from (cite: Danilovich2017) and the references therein." (3.2 Input parameters) [from (cite: Danilovich2017)]
- External data: SiS/CS molecular data and collisional rates  
  > "We used molecular data for SiS that was previously implemented by (cite: Danilovich2018)" (3.2 Input parameters) [from (cite: Danilovich2018)]

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
- weighting robust: W Hya cubes made with higher weighting for short baselines to match R Dor/IK Tau; robust value not stated  
  > "We made image cubes for the whole data set using a higher weighting for short baselines for comparison with the R Dor and IK Tau data" (2.1 ALMA observations and data reduction)
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

- IK Tau and R Dor data reduction and radial profile extraction  
  > "The full survey is presented in (cite: Decin2018), including a detailed discussion of the data reduction." (2.1 ALMA observations and data reduction) [from (cite: Decin2018)]
- Empirical e-folding radius formulae and molecular data  
  > "check the reliability of the empirical formulae found by (cite: Danilovich2018) for finding CS and SiS $e$-folding radii" (1 Introduction) [from (cite: Danilovich2018)]

### Not stated but needed to reproduce (our reading)

- CASA version, calibration and imaging parameters (robust, cell, size)
- Continuum subtraction and line-free channels
- Radiative transfer code name/version and fitting procedure details
- Aperture and annuli definitions for radial profiles
- CO-H2 conversion and H2 density structure

## Analysis recipe

1. **Extract spectra and radial profiles**: Azimuthally averaged radial profiles from zeroth moment maps and spectra from apertures  
  > "Where possible, we extracted azimuthally averaged radial profiles from the zeroth moment maps of the ALMA data." (2.1 ALMA observations and data reduction)
   - fitting: _not stated_
   - validation: ALMA spectra compared with APEX to check for resolved-out flux  
  > "From this we can see that no flux has been resolved out in the ALMA observations." (2.2.1 SiS)
2. **Model abundance distributions**: 1D spherically symmetric accelerated lambda iteration modelling, adjusting models by hand until best fit to radial profiles and spectra  
  > "The models were adjusted until the best fit to the data was found." (3.1 Modelling procedure)
   - software: ALI code
   - parameter: IK Tau SiS inner radius 2e14 cm, Gaussian abundance profile  
  > "at an inner radius of $2\times10^{14}$ cm" (3.3.1 SiS)
   - assumption: Spherical symmetry; stellar parameters from Danilovich2017  
  > "We use a one-dimensional, spherically symmetric model to approximate the molecular emission of CS and SiS." (3.1 Modelling procedure)
   - fitting: Manual adjustment; uncertainties from 90% confidence interval  
  > "The uncertainties calculated are based on a 90% confidence interval." (3.3.1 SiS)
   - validation: Tested collisions off and expanded vibrational levels  
  > "We also tested the significance of the collisional rates" (3.3.1 SiS)
3. **Isotopologue abundances and ratios for IK Tau**: Fix SiS e-folding radius, vary peak abundance of each isotopologue, then compute ratios  
  > "we used the same $e$-folding radius of $3.6\times 10^{15}$ cm that was found for $^{28}$Si$^{32}$S and varied the peak abundance" (3.3.1 SiS)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **ALI (accelerated lambda iteration code)** : Radiative transfer modelling  
  > "The modelling is done using an accelerated lambda iteration method (ALI)" (3.1 Modelling procedure)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| IK Tau SiS inner abundance f0 | 3.4e-6 | 0.5e-6 | relative to H2 | 2 | $f_0 = (3.4\pm0.5)\times 10^{-6}$ |
| IK Tau SiS e-folding radius | 3.6e15 | 0.5e15 | cm | 2 | $R_e = (3.6\pm0.5)\times 10^{15}$ cm |
| W Hya SiS Gaussian peak abundance | 1e-7 | not stated | relative to H2 | 2 | increases to $f_g=1\times 10^{-7}$ |
| R Dor SiS f0 | 1.5e-8 | not stated | relative to H2 | 2 | we found $f_0 = 1.5\times10^{-8}$ relative to H$_2$ |
| R Dor CS f0 | 6.5e-9 | not stated | relative to H2 | 2 | we find a best fitting abundance of $f_0=6.5\times 10^{-9}$ relative to H$_2$ |
| IK Tau 32S/34S | 37 | 14 | dimensionless | 3 | /  $^{32}$S/$^{34}$S  /   $37\pm14$   / 21.6$^{b}$ / |
| IK Tau 28Si/30Si | 40 | 8 | dimensionless | 3 | / $^{28}$Si/$^{30}$Si /   $40 \pm 8$   / |

## Qualitative findings

- Peak SiS and CS abundances increase from R Dor to W Hya to IK Tau, not explained by mass-loss rate alone  
  > "For both SiS and CS, we see a progression in (peak) abundance from R Dor to W Hya to IK Tau." (5.1 Difference between lower and higher mass-loss rate stars)

## Claim tuples

- H: Do CS and SiS abundances differ between low and high mass-loss rate O-rich AGB stars? | E: Radiative transfer modelling of ALMA CS and SiS data for three stars | R: Peak abundances rise from R Dor to W Hya to IK Tau | F: Abundances correlate with pulsation amplitude rather than only wind density | **partially**
- H: Do isotopic ratios in IK Tau indicate its metallicity? | E: Isotopologue abundances from SiS models | R: Ratios higher than solar | F: IK Tau has lower metallicity than the Sun | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): 1D spherical models cannot include asymmetric structures  
  > "Although this precludes the inclusion of asymmetric structures" (3.1 Modelling procedure)
- Caveat (inferred, ours): Fits by hand without a formal likelihood or parameter space exploration
- Caveat (inferred, ours): Uncertainties only given for some fits
- Caveat (inferred, ours): Small sample of three stars

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: Model code and input files
- Missing: Fit criteria
- Data volume (inferred): ~100-300 GB for the two projects raw
- Score (inferred): 3/5, Data are archival, but the modelling is manual and key processing is deferred to other papers.
- Rediscovery candidate: no, The model fitting is manual and the code is not specified.

## Links

- Method: (cite: Decin2018) (Data reduction for IK Tau and R Dor)
- Method: (cite: Danilovich2018) (Molecular data and modelling approach)
- Companion: (cite: Takigawa2017) (First results on W Hya data)

## Checks

```json
{
 "quotes": 51,
 "quotes_ok": 51,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2013.0.00166.S"
 ],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 33,
  "rate": 0.485
 },
 "evidence_ok": true
}
```
