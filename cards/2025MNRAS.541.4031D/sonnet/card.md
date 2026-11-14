# VERTICO ─ IX. Signatures of environmental processing of the gas in Virgo cluster spiral galaxies through mapping of CO isotopologues

`2025MNRAS.541.4031D` | Monthly Notices of the Royal Astronomical Society 2025 | first author: Davis, Timothy A. | arXiv: 2507.17553 | DOI: 10.1093/mnras/staf1230

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: nearby_galaxies, galaxy_clusters_and_sz
- Question: How do 13CO and C18O emission and line ratios in Virgo cluster spirals vary with galaxy properties, and what do they imply about environmental processing of the molecular gas?  
  > "In this work we attempt to unravel the effects of the cluster environment on the cold gas in galaxies in a different way: using the less abundant isotopologues of carbon monoxide, $^{13}$CO and C$^{18}$O." (Introduction)
- Target **48 VERTICO Virgo cluster spiral galaxies**: coordinates _not stated_; z/distance 16.5 Mpc  
  > "Throughout we assume a distance of 16.5 Mpc for all galaxies within the Virgo cluster (cite: 2007ApJ...655..144M)." (Introduction); distance from (cite: 2007ApJ...655..144M)  
  > "Throughout we assume a distance of 16.5 Mpc for all galaxies within the Virgo cluster (cite: 2007ApJ...655..144M)." (Introduction)

## Data provenance

- ALMA projects: 2019.1.00763.L, 2017.1.00886.L, 2016.1.00912.S, 2015.1.00956.S
- bands: Band 6  
  > "The data observed as part of the VERTICO program included spectroscopic observations of the ALMA Band 6 continuum, and the $^{12}$CO (2-1) transition" (2.2 ALMA data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: ACA (7-m) plus Total Power for the most extended 25 of 36 new targets  
  > "Total Power (TP) observations were included to recover extended CO emission at large angular scales for the most extended 25 out of 36 targets." (2.2 ALMA data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: typical beam ≈7 arcsec (≈560 pc)  
  > "which have a typical beamsize of $\approx$7$^{\prime \prime}$($\approx$560 pc)." (2.2 ALMA data)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: VERTICO Cycle 7 large program plus 15 galaxies from public archival data (no 13CO in archival)  
  > "36 targets were newly observed, while 15 galaxies were already surveyed and the data were publicly available in the ALMA archive" (2.2 ALMA data)
- Line: 12CO 2-1 (230.542 GHz)
- Line: 13CO 2-1 (220.402 GHz)
- Line: C18O 2-1 (219.564 GHz)
- Other facility **VLA (VIVA survey)**: HI-based sample selection and HI velocity field test  
  > "selected by the Very Large Array Imaging of Virgo in Atomic Gas survey (cite: 2009AJ....138.1741C)" (2.1 Sample)
- External data: VERTICO 12CO moment maps, mean gas and SFR surface densities and other galaxy properties  
  > "These galaxy properties are taken directly from the other VERTICO papers" (3.3 12CO/13CO global line ratios) [from (cite: Brown2021)]
- External data: HI deficiencies  
  > "where the deficiencies are taken from (cite: Yoon2017) and (cite: 2012MNRAS.422.1835S)" (3.5 Correlations with H deficiency) [from (cite: Yoon2017); (cite: 2012MNRAS.422.1835S)]
- External data: HI tail angles  
  > "using the tail angles derived in (cite: 2022MNRAS.517.2912L)" (3.7 Tailed galaxies) [from (cite: 2022MNRAS.517.2912L)]
- External data: Comparison samples: EMPIRE field spirals and ATLAS3D ETGs line ratios  
  > "field spirals from EMPIRE, and field and Virgo cluster ETGs from the ATLAS$^{\rm 3D}$ survey (cite: 2019ApJ...880..127J; 2015MNRAS.450.3874A)" (3.4 Correlations with morphology) [from (cite: 2019ApJ...880..127J); (cite: 2015MNRAS.450.3874A)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: native-resolution cubes as delivered from ACA; reduction in Brown2021  
  > "our results are derived from the original native resolution cubes as delivered from the ACA" (2.2 ALMA data)
- flux calibrator: _not stated_
- flux scale uncertainty: 5-10% nominal ALMA Band 6 Cycle 7  
  > "The nominal flux calibration uncertainty of ALMA in Band 6 during Cycle 7 was 5-10% according to the ALMA Cycle 7 Technical Handbook." (2.2 ALMA data)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Sun2018 masking: core mask S/N≥3.5 in ≥3 consecutive channels, wing mask S/N≥2 in ≥2 channels; noise measured before primary beam correction  
  > "a core mask, selecting spaxels with $\mathrm{S/N}\geq 3.5$ in three consecutive channels or more, and a wing mask for spaxels with $\mathrm{S/N}\geq 2$ in two consecutive channels or more." (2.2 ALMA data)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Data reduction and imaging  
  > "A detailed description of the data reduction and imaging process is available in (cite: Brown2021)." (2.2 ALMA data) [from (cite: Brown2021)]
- Moment map masking  
  > "implementing a masking process described in (cite: Sun2018)" (2.2 ALMA data) [from (cite: Sun2018)]
- [12C/13C]=70 abundance ratio  
  > "With an assumed $[\mathrm{^{12}C/^{13}C}]$ of 70 (cite: 1993A&A...274..730H)" (3.3 12CO/13CO global line ratios) [from (cite: 1993A&A...274..730H)]

### Not stated but needed to reproduce (our reading)

- Calibration pipeline/CASA versions and imaging parameters (robust, channel width) for VERTICO cubes
- GAStimator priors, initial guesses, chain length
- Radial aperture count and widths, and S/N criteria for radial bin detections
- Conversion of Jy km/s to K km/s used for ratios
- Definition of detection threshold in stacks beyond 5 sigma
- LTSFIT settings
- Anderson-Darling test implementation
- Stack-based quadrant wedge angles for tails

## Analysis recipe

1. **Make masked moment maps and directly detect isotopologues**: Moment maps from native cubes with Sun2018 masks; check 13CO and C18O at 5 sigma  
  > "starting from the 5$\sigma$ level and extending to the brightest integrated intensity peak" (3.1 Direct detections)
   - fitting: _not stated_
   - validation: _not stated_
2. **Stack cubes globally with STACKARATOR**: Shift spectra of every 12CO-detected spaxel by 12CO moment-1 velocity and co-add  
  > "we shift the spectra from every $^{12}$CO(2-1) detected spaxel within each galaxy to a common velocity reference according to the $^{12}$CO(2-1) moment one" (2.3 STACKARATOR)
   - software: STACKARATOR
   - fitting: _not stated_
   - validation: Compared stacked 12CO flux with Brown2021 summed flux  
  > "The integrated intensities closely follow the one-to-one black dashed line" (3.2 Stacked global detections)
3. **Fit stacked lines and estimate uncertainties**: Single vs double gaussian (same centre) fitted with MCMC; double only if BIC lower; flux by integrating model; errors from 1000 random off-line window sums  
  > "We sum the stacked spectrum at 1000 randomly chosen off-line locations using a window the same width as the best fit gaussian full-width at zero intensity." (2.3 STACKARATOR)
   - software: GAStimator
   - fitting: MCMC gaussian fits, model selection by BIC  
  > "These models are fitted to the data using Markov chain Monte Carlo (MCMC) fitting code GASTIMATOR" (2.3 STACKARATOR)
   - validation: Tested stricter BIC difference >10; results unchanged  
  > "We tested if more stringent criteria (e.g. the difference in the BIC values needing to be $>10$) improved the fits, but this did not significantly change our results." (2.3 STACKARATOR)
4. **Radial and quadrant stacking**: Stack in concentric elliptical beam-width apertures, and in quadrants toward/away from HI tails  
  > "we stack quadrants of each galaxy towards and away from the direction of the H tail" (3.7 Tailed galaxies)
   - software: STACKARATOR
   - fitting: _not stated_
   - validation: _not stated_
5. **Correlate line ratios with galaxy properties**: Spearman rank, LTSFIT linear fit against mean gas surface density, k-sample Anderson-Darling tests across environment/morphology/HI-deficiency groups  
  > "fitted using the LTSFIT package of (cite: 2013MNRAS.432.1709C)" (3.3.1 Gas and star formation surface density correlations)
   - software: LTSFIT
   - assumption: 13CO optically thin, [12C/13C]=70, temperature effects minor  
  > "the excitation temperatures of the 2–1 transition of $^{12}$CO and $^{13}$CO are very similar (both $\approx10$ K)" (3.3 12CO/13CO global line ratios)
   - fitting: LTSFIT robust linear fit  
  > "As a guide to the eye we show with a dashed line the best-fitting linear correlation for our detected points, fitted using the LTSFIT package of (cite: 2013MNRAS.432.1709C)." (Results, Gas and star formation surface density correlations)
   - validation: _not stated_

## Software

- **STACKARATOR** : Image-plane velocity-aligned stacking of cubes  
  > "using a newly developed code called STACKARATOR." (2.3 STACKARATOR)
- **GAStimator** : MCMC fitting of stacked lines  
  > "Markov chain Monte Carlo (MCMC) fitting code GASTIMATOR" (2.3 STACKARATOR)
- **LTSFIT** : Linear fit of 12CO/13CO vs gas surface density  
  > "fitted using the LTSFIT package of (cite: 2013MNRAS.432.1709C)" (3.3.1 Gas and star formation surface density correlations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Spearman correlation 12CO/13CO vs mean molecular gas surface density | -0.56 | p = 0.002 | dimensionless | 5 | Spearmans rank correlation coefficient (for the detected galaxies) of $\rho=-0.56$, and a $p$-value of 0.002 |
| Best-fit slope of 12CO/13CO vs log Sigma_mol | -4.6 | 0.5 | dimensionless | 5 | (-4.6\pm0.5)\log_{10} |
| Range of 12CO/13CO global ratios | 10-43 | not stated | dimensionless | 3 | ranging from 10 – 43 |
| Spearman correlation with SFR surface density | -0.11 | p = 0.6 | dimensionless | 5 | $\rho=-0.11$, $p$-value of 0.6 |
| C18O global detections | 9 galaxies in Sec 3.2 (8 in Sec 3.8) | not stated | galaxies | 3 | C$^{18}$O, on the other hand, was detected in 9 galaxies. |

## Qualitative findings

- Cluster spirals have higher 12CO/13CO than field spirals; ETGs show the reverse; ratio decreases with HI deficiency  
  > "The VERTICO cluster spiral galaxies have higher average $^{12}$CO/$^{13}$CO line ratios than those found in field systems" (3.4)

## Claim tuples

- H: Cluster environment alters molecular gas conditions as seen in 12CO/13CO | E: Stack 13CO in 48 galaxies and compare ratios with gas density, HI deficiency, morphology, field samples | R: Ratios of 10-43 anticorrelate with gas surface density and HI-deficiency, and exceed field values for spirals | F: Optical depth changes as gas is stripped then settles into dense cores | **partially**
- H: Abundance variations exist among isotopologues | E: Compare 12CO/C18O and 13CO/C18O ratios globally and radially | R: 13CO/C18O varies 2-30 with a spread beyond uncertainties | F: Real abundance variations likely, perhaps in 18O/16O | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Selective photodissociation and fractionation judged unlikely to cause the abundance variations  
  > "Thus it seems unlikely that such large changes in abundance can be caused by dissociation." (4.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Small comparison samples and degeneracy between optical depth and abundance  
  > "While the scenario described above cannot be proven with the existing data (due to the degeneracy with abundance variations)" (4.3)
- Caveat (inferred, ours): Comparison samples are not mass-matched and use different beams/environments
- Caveat (inferred, ours): Stacking noise correlated; negative sidelobes may bias fluxes
- Caveat (inferred, ours): 12CO/13CO interpretation assumes fixed [12C/13C]=70 and optically thin 13CO

## Reproducibility

- Data public (paper): Available from ALMA archive; processed data on VERTICO website  
  > "The data underlying this article is available from the ALMA archive using the project codes listed above." (Data availability)
- Products in archive: _not stated_
- Code: STACKARATOR public on GitHub  
  > "is publicly available at <https://github.com/TimothyADavis/stackarator>" (STACKARATOR CODE DESCRIPTION)
- Missing: VERTICO product moment maps/masks details
- Missing: GAStimator configuration
- Missing: Radial bin definitions
- Data volume (inferred): ~100 GB for ACA cubes of 48 galaxies (or less using VERTICO products)
- Score (inferred): 3/5, Public data and code, but fitting settings, radial analysis details and upstream cubes depend on other papers.
- Rediscovery candidate: yes, Public data, public stacking code, numeric tables of fluxes and ratios exist, though some settings unstated.

## Links

- Method: (cite: Brown2021) (VERTICO data reduction and imaging)
- Method: (cite: Sun2018) (Masking for moment maps)
- Companion: (cite: 2022ApJ...940..176V) (VERTICO stacking of 12CO and gas distribution)
- Companion: (cite: 2022ApJ...933...10Z) (Environmental effects on molecular gas in VERTICO)
- Related: VERTICO
- Related: VIVA
- Related: EMPIRE
- Related: CLAWS
- Related: EDGE-CALIFA
- Related: ATLAS3D

## Checks

```json
{
 "quotes": 52,
 "quotes_ok": 52,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 36,
  "rate": 0.486
 },
 "evidence_ok": true
}
```
