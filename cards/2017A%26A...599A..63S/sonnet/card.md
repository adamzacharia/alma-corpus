# H<SUP>12</SUP>CN and H<SUP>13</SUP>CN excitation analysis in the circumstellar outflow of R Sculptoris

`2017A&A...599A..63S` | Astronomy and Astrophysics 2017 | first author: Saberi, M. | arXiv: 1612.05573 | DOI: 10.1051/0004-6361/201629901

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars, astrochemistry
- Question: Does the circumstellar H12CN/H13CN ratio trace the photospheric 12C/13C ratio in R Scl, testing whether CO isotopologue selective photodissociation explains the 12CO/13CO discrepancy?  
  > "In this paper, we derive the H$^{12}$CN/H$^{13}$CN ratio and compare it with previously reported $^{12}$CO/$^{13}$CO and $^{12}$C/$^{13}$C ratios to probe the effect of UV radiation on the CSE of R Scl." (Introduction)
- Target **R Scl**: coordinates _not stated_; z/distance approximately 370 pc  
  > "R Scl is a carbon-type AGB star at a distance of approximately 370 pc derived using K-band period-luminosity relationships (cite: Knapp03; Whitelock08)." (R Sculptoris); distance from K-band period-luminosity relationships (Knapp03; Whitelock08)  
  > "R Scl is a carbon-type AGB star at a distance of approximately 370 pc derived using K-band period-luminosity relationships (cite: Knapp03; Whitelock08)." (R Sculptoris)

## Data provenance

- ALMA projects: 2012.1.00097.S
- bands: ALMA Band 7 (275-373 GHz)  
  > "using ALMA band 7 (275-373 GHz)" (3.2 Interferometer data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 14 Dec 2013, 25 Dec, 26 Apr 2014, 24 Jul 2015  
  > "were made on 14 Dec 2013, 25 Dec, 26 Apr 2014, and 24 Jul 2015" (3.2 Interferometer data)
- pi or archival as stated: _not stated_
- Line: H13CN J=4-3 (354.3 GHz)
- Other facility **APEX 12 m (SEPIA band 5, SHeFI-APEX1)**: H12CN(2-1), H13CN(2-1, 3-2) spectra, July 2015  
  > "We used the SEPIA/band 5 and the SHeFI-APEX1 receivers." (3.1 Single-dish data)
- Other facility **SEST**: H12CN(1-0, 3-2) published spectra  
  > "H$^{12}$CN($J$=1-0, 3-2) made with the Swedish-ESO Submillimetre Telescope (SEST) (cite: Olofsson96)" (3.1 Single-dish data)
- Other facility **HHT**: H12CN(4-3) published spectrum  
  > "H$^{12}$CN($J$=4-3) observed with the Heinrich Hertz Submillimeter Telescope (HHT) (cite: Bieging01)" (3.1 Single-dish data)
- External data: Mass-loss rate 2e-7 Msun/yr  
  > "constant mass loss rate $\dot{M}\sim 2\times10^{-7}$ $M_{\odot}$ yr$^{-1}$ (cite: Wong04)" (4.2 Radiative transfer model) [from (cite: Wong04)]
- External data: Photospheric 12C/13C ~ 19 +/- 6  
  > "photospheric $^{12}$C/$^{13}$C$\sim$19 $\pm$ 6 reported by (cite: Lambert86)" (2 R Sculptoris) [from (cite: Lambert86)]
- External data: SEST and HHT H12CN line observations  
  > "we have also used previously published single-dish observations of H$^{12}$CN($J$=1-0, 3-2) made with the Swedish-ESO Submillimetre Telescope (SEST) (cite: Olofsson96)" (3.1 Single-dish data) [from (cite: Olofsson96); (cite: Bieging01)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Uranus primary, bootstrapped to J0143-3206 and J0106-4034  
  > "The primary flux calibration was done using Uranus and bootstrapped to the gain calibrator J0143-3206 (0.27 Jy beam$^{-1}$) and J0106-4034 (0.23 Jy beam$^{-1}$)." (3.2 Interferometer data)
- flux scale uncertainty: around 10%  
  > "the absolute flux has an uncertainty of around 10 $\%$" (3.2 Interferometer data)
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
- smoothing: imsmooth to 0.13'' x 0.13''  
  > "The tasks "imsmooth" and "immoments" in CASA were used to smooth the image to $0.13'' \times 0.13''$ resolution" (3.2 Interferometer data)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA data reduction details deferred to a companion paper  
  > "More details of the data reduction will come in Maercker et al. in prep." (3.2 Interferometer data) [from Maercker et al. in prep.]
- HCN spectroscopic treatment follows earlier work  
  > "For excitation analysis, the same treatment as (cite: Schoier11; Danilovich14) with small adjustments was used." (4.1 Spectroscopic treatment of HCN) [from (cite: Schoier11; Danilovich14)]
- H2 density from constant mass loss  
  > "The H$_2$ number density is calculated assuming a constant mass loss rate, as in (cite: Schoier01)." (4.2 Radiative transfer model) [from (cite: Schoier01)]
- Dust temperature profile from SED modelling  
  > "derived based on SED modelling (Maercker, private communication)" (4.2 Radiative transfer model) [from Maercker, private communication]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration/imaging details (robust, clean parameters, beam, rms)
- Line-free channels and continuum subtraction
- Exact ALMA configuration and integration times
- Collisional rate coefficients and HCN molecular data used
- Source of ALI code implementation details and model grid
- Exact beam convolution/radial offset extraction procedure

## Analysis recipe

1. **Reduce and smooth data**: APEX spectra reduced with XS, first-order baseline; Tmb=T*A/eta_mb. ALMA image smoothed to 0.13'' and moment-0 made with CASA  
  > "A first-order polynomial was subtracted from the spectrum to remove the baseline." (3.1 Single-dish data)
   - software: XS, CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Constrain velocity profile**: Compare model and ALMA H13CN(4-3) line shapes at offsets over grid of b and v_inf  
  > "A series of models with b and $v_\infty$ changing in the ranges $0.4 < b < 8.5$ and $8.5 < v_\infty < 13$ were run" (5.1 Radial expansion velocity profile)
   - software: ALI code
   - parameter: best b = 2.5, v_inf = 10 km/s  
  > "The model with b = 2.5 and $v_\infty$=10 km s$^{-1}$ leads to the best fits" (5.1 Radial expansion velocity profile)
   - assumption: Spherical symmetry, constant mass loss 2e-7, Tdust=Tgas power law T0=1500 K, vmin=3 km/s  
  > "the same temperature profile as the dust temperature was used to describe the kinetic temperature of the gas" (4.2 Radiative transfer model)
   - fitting: visual comparison of line shapes  
  > "The model with b = 2.5 and $v_\infty$=10 km s$^{-1}$ leads to the best fits to the line shape of the H$^{13}$CN(4-3) spectra at the offset positions from the centre." (Results, Radial expansion velocity profile)
   - validation: _not stated_
3. **Fit e-folding radius**: 102-model grid in f0 and Re, reduced chi2 on 9 radial offset average intensities of H13CN(4-3)  
  > "We ran 102 models with the fixed parameters detailed in Table 2 and simultaneously varying $f_0$ and $R_e$" (5.2 Radial distributions of HCN isotopologues)
   - software: ALI code
   - assumption: Same distribution for both isotopologues since both equally photodissociated  
  > "the same molecular distribution is expected for both H$^{12}$CN and H$^{13}$CN isotopologues" (5.2 Radial distributions of HCN isotopologues)
   - fitting: chi2_red = chi2/(N-2), grid search  
  > "To select the model with the best $R_e$, a reduced $\chi^2$ statistic is used. The reduced chi-square is defined as $\chi^2_{red} = \chi^2 / (N-2)$" (Results, Radial distributions of HCN isotopologues)
   - validation: 1 sigma from chi2_red distribution  
  > "The cited error is for 1$\sigma$ uncertainty derived from the $\chi^2_{red}$ distribution." (Results, Radial distributions of HCN isotopologues)
4. **Fit H13CN and H12CN abundances**: With Re fixed, chi2 over f0 using integrated intensities of all lines  
  > "we use the total intensities of all three observed lines H$^{13}$CN(2-1, 3-2, 4-3) in $\chi^2$ calculation" (5.3 The H13CN abundance)
   - software: ALI code
   - parameter: sigma 20% APEX 2-1, 10% ALMA 4-3, 100% for undetected 3-2; H12CN 1-0 excluded (maser)  
  > "assumed to be 20$\%$ for H$^{13}$CN(2-1) APEX data, 10$\%$ for H$^{13}$CN(4-3) ALMA data and 100$\%$ for H$^{13}$CN(3-2) undetected line" (5.3 The H13CN abundance)
   - fitting: _not stated_
   - validation: Asymmetry tested via chi2 in four directions  
  > "To find out the effect of this asymmetry in determining the adjustable parameters, we calculate the $\chi^2_{red}$ statistic in four directions from the central star." (Discussion, Asymmetry in the CSE)
5. **Derive isotopologue ratio**: Ratio of f0 values compared with photospheric 12C/13C  
  > "We have derived a ratio of circumstellar H$^{12}$CN/H$^{13}$CN = 26.3 $\pm$ 11.9 for R Scl" (6.4 Comparison of the isotopologue ratios)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : ALMA data reduction, imsmooth, immoments  
  > "The data reduction was done with the Common Astronomy Software Application (CASA)." (3.2 Interferometer data)
- **XS** : APEX single-dish reduction  
  > "The data reduction was done using XS[^2]." (3.1 Single-dish data)
- **ALI radiative transfer code** : non-LTE excitation modelling  
  > "a non-local thermodynamic equilibrium (LTE) radiative transfer code based on the accelerated lambda iteration (ALI) method was used" (4.2 Radiative transfer model)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| H13CN e-folding radius Re | 2.0e15 | 0.25e15 | cm | 3 | $R_e = (2.0 \pm 0.25) \times 10^{15}$ cm |
| H13CN/H2 f0 | 1.9e-6 | 0.5e-6 (0.4e-6 in abstract) | dimensionless | 4 | $f_0 = (1.9 \pm 0.5) \times 10^{-6}$ |
| H12CN/H2 f0 | 5.0e-5 | 2e-5 | dimensionless | 4 | $f_0 = (5.0 \pm 2)\times 10^{-5}$ |
| H12CN/H13CN | 26.3 | 11.9 | dimensionless | 5 | The derived H$^{12}$CN/H$^{13}$CN = 26.3 $\pm$ 11.9 |
| Velocity profile b, v_inf | b=2.5, v_inf=10 | not stated | km/s (v_inf) | 2 | b = 2.5 and $v_\infty$=10 km s$^{-1}$ |

## Qualitative findings

- Single-dish-only fits prefer larger Re and lower abundance than resolved ALMA fits  
  > "The single-dish observations require a larger $e$-folding radius with less fractional abundance" (6.1 Comparison of the best-fitting criteria)

## Claim tuples

- H: HCN isotopologue ratio traces photospheric 12C/13C despite UV | E: Non-LTE modelling of H12CN and H13CN lines with ALMA-constrained size | R: H12CN/H13CN = 26.3 +/- 11.9 vs 12C/13C ~19 +/- 6 | F: HCN ratio unaffected by UV; supports CO selective photodissociation | **supported**
- H: Resolved data are needed to constrain models | E: Compare chi2 maps from ALMA vs single-dish | R: Best-fit parameters differ | F: Spatially resolved data are essential | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Gas temperature profile of W04 gave no significant change  
  > "We also ran models using the gas temperature profile derived by W04, which led to no significant change in the results." (4.2 Radiative transfer model)
- How they decided it was enough: _not stated_
- Limitation (authors): Spherical symmetry ignores east-west asymmetry from binary companion  
  > "This is a first order approximation, and the east-west asymmetry in the CSE as seen in Fig. 1 possibly due to the binary companion is not taken into account." (6.2 Asymmetry in the CSE)
- Caveat (inferred, ours): Large abundance uncertainties make ratio consistent with a wide range
- Caveat (inferred, ours): Coarse grid, no MCMC; H12CN is optically thick and the fit chi2_red=0.07 suggests overestimated errors
- Caveat (inferred, ours): Spherical model for an asymmetric source

## Reproducibility

- Data public (paper): ALMA project cited; APEX data new  
  > "This paper makes use of ALMA data from project No. ADS/ JAO.ALMA$\#$2012.1.00097.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: ALI code and molecular data
- Missing: Details of ALMA reduction
- Missing: APEX spectra
- Missing: SED-derived temperature details
- Data volume (inferred): ~10-50 GB (single band 7 line project, multiple EBs)
- Score (inferred): 3/5, ALMA project code given, but reduction deferred and the radiative transfer code is not public.
- Rediscovery candidate: no, Reduction details missing and the modelling relies on a non-public code plus unavailable APEX/SEST data.

## Links

- Method: Rybicki & Hummer 1991 (ALI method)
- Method: Maercker et al. 2008 (code implementation)
- Companion: Vlemmings et al. 2013 (12CO/13CO discrepancy)
- Companion: Maercker et al. in prep. (ALMA data reduction)

## Checks

```json
{
 "quotes": 48,
 "quotes_ok": 48,
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
  "facts": 78,
  "stated": 38,
  "rate": 0.487
 },
 "evidence_ok": true
}
```
