# Chlorine-bearing molecules in molecular absorbers at intermediate redshifts

`2019A&A...629A.128W` | Astronomy and Astrophysics 2019 | first author: Wallström, S. H. J. | arXiv: 1908.04188 | DOI: 10.1051/0004-6361/201935860

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: astrochemistry, high_z_galaxies
- Question: What are the chemical properties of chlorine-bearing molecules (H2Cl+, HCl) and the 35Cl/37Cl isotopic ratio in the molecular absorbers toward PKS 1830-211 and B 0218+357?  
  > "with the goal of investigating their chemical properties and measuring the $^{35}$Cl/$^{37}$Cl isotopic ratio in different absorbing sightlines." (Introduction)
- Target **PKS 1830-211 (MA0.89 SW and NE)**: coordinates _not stated_; z/distance z_abs = 0.88582  
  > "The molecular absorber located in front of the quasar PKS 1830$-$211 is a face-on spiral galaxy at a redshift z=0.88582 (hereafter labeled MA0.89)." (Introduction); distance from _not stated_
- Target **B 0218+357 (MA0.68)**: coordinates _not stated_; z/distance z_abs = 0.68466  
  > "It is a nearly face-on spiral galaxy at an intermediate redshift z=0.68466" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00056.S, 2013.1.00020.S, 2016.1.00031.S
- bands: _not stated_
- frequencies and spectral setup: H2Cl+ ortho 189.225 GHz, para 485.418 GHz, HCl 625.919 GHz (rest); 35Cl and 37Cl isotopologs observed simultaneously  
  > "H$^{35}$Cl | 625.919 | 331.908 | 0.9" (Table 1)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: longest baseline 1.7 km (first run) and 1.1 km (second run) for MA0.68  
  > "The array’s longest baseline was 1.1 km." (Observations)
- angular resolution: ~1.0" x 0.6" (PA=-176 deg) at 100 GHz for MA0.68 combined  
  > "the two datasets result in a synthesized beam of $\sim 1.0 \ensuremath{''} \times 0.6 \ensuremath{''}$ (P.A.$=-176^\circ$) at 100 GHz" (Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2014-2017 (see Table 1)  
  > "Observations of H$_2$Cl$^+$ were obtained on 2016 October 22 and 2017 May 02." (Observations)
- pi or archival as stated: _not stated_
- Line: ortho-H2Cl+ 1_10-1_01 (189.225 GHz)
- Line: para-H2Cl+ 1_11-0_00 (485.418 GHz)
- Line: HCl 1-0 (625.919 GHz)
- Other facility **ATCA**: 7 mm spectral scan constraining CH3Cl toward PKS 1830-211 (from earlier work)  
  > "covered in a deep spectral scan in the 7 mm band with the Australia Telescope Compact Array toward PKS 1830$-$211" (4.1.3 HCl+ and CH3Cl)
- External data: Molecular fractions, cosmic-ray ionization rates and OH+/H2O+ ratios for MA0.89  
  > "(cite: Muller2016b)" (Table 3) [from (cite: Muller2016b)]
- External data: N_Cl vs N_H2 correlation used for Cl fractions  
  > "from an independent least-squares fit of the data from (cite: Moomey2012) and (cite: Balashev2015)." (4.1.2) [from (cite: Moomey2012; Balashev2015)]
- External data: Spectroscopic hyperfine data for H2Cl+ and HCl  
  > "Data for H$_2$Cl$^+$ are from (cite: Araki2001), taken from the Cologne Database for Molecular Spectroscopy (cite: Muller2001)." (Spectroscopic data) [from (cite: Araki2001; Cazzoli2004)]

## Processing

### Calibration

- pipeline or manual: CASA, standard procedures  
  > "The data calibration was done with the CASA package following standard procedures." (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: phase self-calibration with a model of two point sources (MA0.68); on the quasar for MA0.89  
  > "We further improved the data quality with a step of self-calibration of the phase, using a model of two point-sources for MA0.68." (Observations)

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

- Earlier H2Cl+ observations of MA0.89 taken from previous papers  
  > "We complemented previous observations of the ortho and para forms of H$_2$Cl$^+$ toward MA0.89 presented by (cite: Muller2014) and (cite: LeGal2017)" (Observations) [from (cite: Muller2014); (cite: LeGal2017)]
- G0 derivation assumptions (nH = 35 cm-3) following earlier method  
  > "again following (cite: Muller2016b) in the assumption of $n_{\rm{H}}$ = 35 cm$^{-3}$." (4.1) [from (cite: Muller2016b)]

### Not stated but needed to reproduce (our reading)

- Calibrator for flux scale and CASA version
- Number of velocity components/initial guesses for fits of NE and MA0.68 beyond one component
- UVMULTIFIT point-source positions and flux ratios
- Weights for the averaged spectrum
- Details of the HCl observing setup for MA0.89 (arrays, baselines)
- Velocity range/channel selection for continuum normalization

## Analysis recipe

1. **Extract spectra toward each lensed image**: Fit visibilities with a two point-source model per spectral channel, then weighted-average spectra from separate datasets  
  > "we extracted the spectra along each line of sight by directly fitting each visibility set separately using the CASA-Python task UVMULTIFIT" (Observations)
   - software: CASA, UVMULTIFIT
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit hyperfine-deconvolved opacity profiles and isotopic ratio**: Sum of Gaussian velocity components convolved with hyperfine structure; 35Cl and 37Cl fitted jointly with the ratio free  
  > "Both the $^{35}$Cl- and $^{37}$Cl-isotopologs were treated in a common fit, with the $^{35}$Cl/$^{37}$Cl ratio as a free parameter." (3 Results)
   - parameter: 4 Gaussians for MA0.89 SW; 1 Gaussian for MA0.89 NE and MA0.68  
  > "so we limited the number of Gaussian components to one for sake of simplicity" (3 Results)
   - assumption: Covering factor f_c = 1, optically thin; OPR = 3  
  > "we consider $f_c=1$ for all species and all sightlines" (3 Results)
   - fitting: chi2 minimization, 1 sigma errors  
  > "using $\chi^2$ minimization and taking the errors to be 1$\sigma$" (3 Results)
   - validation: Ortho and para H2Cl+ fitted separately for MA0.89 SW; residuals at noise level  
  > "we fitted the ortho and para lines of H$_2$Cl$^+$ separately for MA0.89 SW" (3 Results)
3. **Derive radiation field from analytic steady-state chemistry**: Derive x_e from [OH+]/[H2O+], then G0 from [H2Cl+]/[HCl]  
  > "The \[H$_2$Cl$^+$\]/\[HCl\] ratio then allows for the derivation of G$_0$" (4.1)
   - assumption: T = 100 K, nH = 35 cm-3  
  > "assuming T = 100 K." (4.1)
   - fitting: _not stated_
   - validation: Compared with Neufeld & Wolfire 2009 models  
  > "Our simple model is broadly consistent with the results of (cite: Neufeld2009)" (4.1)
4. **Estimate fraction of Cl in molecules**: Use N_Cl-N_H2 correlation to infer neutral Cl and compare to H2Cl+ and HCl  
  > "we can infer the column density of neutral chlorine corresponding to the column density of H$_2$ in the different sightlines." (4.1.2)
   - assumption: Neutral chlorine vastly dominant  
  > "assuming neutral chlorine is vastly dominant" (4.1.2)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Data calibration  
  > "The data calibration was done with the CASA package following standard procedures." (Observations)
- **UVMULTIFIT** : Visibility-domain spectral extraction for each lensed image  
  > "using the CASA-Python task UVMULTIFIT (cite: Marti-Vidal2014)" (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 35Cl/37Cl MA0.89 SW (H2Cl+) | 2.99 | 0.05 | dimensionless | 2 | $2.99 \pm 0.05$ $^b$ |
| 35Cl/37Cl MA0.89 SW (HCl) | 3.28 | 0.08 | dimensionless | 2 | $3.28 \pm 0.08$ $^c$ |
| 35Cl/37Cl MA0.89 NE | 3.3 | 0.3 | dimensionless | 2 | $3.3 \pm 0.3$ $^b$ |
| 35Cl/37Cl MA0.68 | 2.2 | 0.3 | dimensionless | 2 | $2.2 \pm 0.3$ $^b$ |
| N(H2Cl+) MA0.89 SW | 2.3e13 | 0.3e13 | cm-2 | 2 | $(2.3 \pm 0.3) \times 10^{13}$ |
| N(HCl) MA0.89 SW | 2.7e13 | 0.5e13 | cm-2 | 2 | $(2.7 \pm 0.5) \times 10^{13}$ |
| N(H2Cl+) MA0.89 NE | 5.2e12 | 0.5e12 | cm-2 | 2 | $(5.2 \pm 0.5) \times 10^{12}$ |
| N(H2Cl+) MA0.68 | 1.4e13 | 0.2e13 | cm-2 | 2 | $(1.4 \pm 0.2) \times 10^{13}$ |
| N(HCl) MA0.89 NE upper limit | <2.4e11 | not stated | cm-2 | 2 | $< 2.4 \times 10^{11}$ |
| G0 MA0.89 SW | ~0.5 (lower limit) | not stated | Draine units | 3 | $\sim$ 0.5 $^\dagger$ |

## Qualitative findings

- H2Cl+ traces low-f_H2 gas and HCl traces high-f_H2 gas  
  > "H$_2$Cl$^+$ and HCl trace the gas component with low and high $f_{\rm H_2}$ gas, respectively." (5 Summary)

## Claim tuples

- H: Do H2Cl+ and HCl trace different gas phases? | E: Compare opacity profiles with other species and between sightlines | R: H2Cl+ matches H2O+ with wings; HCl matches H2S; HCl not detected in NE | F: HCl traces high-f_H2 gas, H2Cl+ low-f_H2 gas | **supported**
- H: Does the 35Cl/37Cl ratio differ between absorbers? | E: Joint hyperfine fits of isotopologs | R: ~3 in MA0.89 sightlines, 2.2±0.3 in MA0.68 | F: MA0.68 may have higher metallicity | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Column densities are lower limits given f_c=1 assumption; G0 underestimated due to extinction  
  > "can be viewed, strictly speaking, as lower limits." (3 Results)
- Caveat (inferred, ours): f_c=1 assumed for all species
- Caveat (inferred, ours): Few Gaussian components for low-S/N sightlines
- Caveat (inferred, ours): Uncertain DR rate coefficients make the chemical model crude
- Caveat (inferred, ours): MA0.68 ratio difference only ~2.7 sigma

## Reproducibility

- Data public (paper): Project codes listed; spectra available at CDS  
  > "This paper uses the following ALMA data:\ ADS/JAO.ALMA#2012.1.00056.S" (Summary and conclusions)
- Products in archive: _not stated_
- Missing: Calibrator and fit initial values
- Missing: UVMULTIFIT setup details
- Missing: CASA version
- Data volume (inferred): ~50-200 GB raw for three projects
- Score (inferred): 5/5, Public data and clear spectral fitting approach, but calibration and fit details sparse.
- Rediscovery candidate: no, Recipe lacks fitting specifics and calibration details.

## Links

- Method: (cite: Marti-Vidal2014) (UVMULTIFIT)
- Companion: (cite: Muller2014) (Earlier MA0.89 H2Cl+ data)
- Companion: (cite: LeGal2017) (Ortho-to-para ratio from same data)
- Companion: (cite: Muller2017) (Companion data for same tuning and profiles)

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
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 31,
  "rate": 0.431
 },
 "evidence_ok": true
}
```
