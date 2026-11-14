# The comet-like composition of a protoplanetary disk as revealed by complex cyanides

`2015Natur.520..198O` | Nature 2015 | first author: Öberg, Karin I. | arXiv: 1505.06347 | DOI: 10.1038/nature14276

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Do complex organic molecules (cyanides) exist in a protoplanetary disk with comet-like abundance ratios?  
  > "It has been hitherto unclear whether the same holds for more complex organic molecules outside of the Solar Nebula" (abstract)
- Target **MWC 480**: coordinates _not stated_; z/distance 140 pc  
  > "in the Taurus star forming region at a distance of 140 pc" (main text); distance from _not stated_

## Data provenance

- ALMA projects: _none stated_
- bands: ~245-259 GHz (Band 6)  
  > "centered on 258.983, 245.622 and 257.498 GHz, respectively." (Methods)
- frequencies and spectral setup: 14 SPWs, 61.04 kHz resolution; H13CN in SPW1, HC3N in SPW9, CH3CN in SPW5, each 60-120 MHz wide  
  > "The correlator was configured to observe 14 spectral windows (SPWs) with resolution $\delta\nu$= 61.04 kHz." (Methods)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 18-650 m (15-555 kλ), 33 antennas  
  > "Observations were carried out on 2014 June 15, with 33 antennas and baselines of 18–650 m (15–555 k$\lambda$)." (Methods)
- angular resolution: 0.4-0.6 arcsec (50-70 AU)  
  > "The angular resolution is $0."4-0".6$, corresponding to 50–70 AU" (main text)
- max recoverable scale: _not stated_
- sensitivity: ~2.3 mJy/beam rms in 1 km/s bins  
  > "The resulting rms noise in 1 km/s bins was $\sim$2.3 mJy per beam." (Methods)
- time on source: 22 minutes  
  > "The total on source integration time was 22 minutes." (Methods)
- observing dates: 2014 June 15  
  > "Observations were carried out on 2014 June 15" (Methods)
- pi or archival as stated: _not stated_
- Line: H13CN J=3-2 (259.0118 GHz)
- Line: HC3N J=27-26 (245.6063 GHz)
- Line: CH3CN 14_0-13_0 and 14_1-13_1 (257.5274 and 257.5224 GHz)
- External data: Disk density structure parameters of MWC 480 (from dust continuum fits)  
  > "We adopt a previously developed disk density structure of MWC 480(cite: Guilloteau11)." (Methods) [from (cite: Guilloteau11)]
- External data: Typical comet CH3CN and HC3N abundance relative to HCN (10%)  
  > "A typical comet contains 10% of CH$_3$CN and HC$_3$N with respect to HCN(cite: Mumma11)." (main text) [from (cite: Mumma11)]

## Processing

### Calibration

- pipeline or manual: Calibrated by ALMA/NAASC staff with standard procedures  
  > "The visibility data were calibrated by ALMA/ NAASC staff following standard procedures." (Methods)
- casa version: CASA 4.2.2  
  > "Each SPW was further self-calibrated in phase and amplitude in CASA 4.2.2." (Methods)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0510+1800, 1.50[0.08] Jy  
  > "J0510+1800 was itself calibrated to an absolute flux of 1.50\[0.08\] Jy on 2014 June 29" (Methods)
- flux scale uncertainty: _not stated_
- self calibration: Phase and amplitude per SPW  
  > "Each SPW was further self-calibrated in phase and amplitude in CASA 4.2.2." (Methods)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robustness 1-2  
  > "using the Briggs weighting scheme, with Brigg’s robustness parameter set to 1–2" (Methods)
- uv taper: 1 arcsec for weak CH3CN lines  
  > "For the weak CH$_3$CN lines, a taper of 1$''$ was applied to the visibilties" (Methods)
- cell size: _not stated_
- image size: _not stated_
- masking: Manual CLEAN mask from H13CN emission, applied to HC3N and CH3CN  
  > "A CLEAN deconvolution was performed with a mask produced manually based on the H$^{13}$CN emission" (Methods)
- multiscale scales: _not stated_
- continuum subtraction: Using line-free channels  
  > "The data cubes were subsequently continuum subtracted using channels identified as free of spectral line emission." (Methods)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 257 GHz continuum: 0.65x0.39 arcsec, PA=-7  
  > "the synthesized beam is $0.''65 \times 0.''39$ (PA=-7)" (Methods)
- final rms: continuum 0.3 mJy/beam  
  > "rms noise 0.3 mJy beam$^{-1}$" (Methods)

### Inherited from earlier work

- Disk density structure and stellar mass, inclination, turbulence  
  > "We adopted a disk inclination of 37$^{\circ}$, disk turbulence of 0.05 km/s and a Keplerian velocity field with a stellar mass of 1.8 M$_\odot$(cite: Guilloteau11)." (Methods) [from (cite: Guilloteau11)]
- Fitting approach via visibility chi2 and power-law abundance prescription  
  > "and $\alpha$ is a power law index$^{36}$." (Methods) [from Qi et al. 2013 (ref 36)]

### Not stated but needed to reproduce (our reading)

- Exact robust value per SPW
- Line-free channels used
- Self-calibration solution intervals
- CLEAN threshold and image size/cell size
- LIME settings (photons, grid points)
- Step size of the abundance grid
- Disk chemistry model details

## Analysis recipe

1. **Image line cubes and continuum**: Self-calibrate, Briggs-weighted cubes, continuum subtract, CLEAN with H13CN mask  
  > "The self-calibrated phase and gain SPW-specific solutions were applied to create individual SPW line data cubes" (Methods)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Moment maps and spectra**: immoments with 1 sigma clip; spectra with CLEAN masks vs Keplerian masks  
  > "Integrated emission maps were produced using the $immoments$ task in CASA, adding emission $>$1$\sigma$ from each channel." (Methods)
   - software: CASA
   - fitting: _not stated_
   - validation: Lower clipping levels do not change result at 10%  
  > "Lower clipping levels do not change the result at the 10% level." (Methods)
3. **Fit abundance profiles in visibility space**: Grid of power-law abundance models, LIME radiative transfer, chi2 minimization on visibilities  
  > "The best-fit models are obtained by minimizing $\chi^2$, the weighted difference between the real and imaginary part of the complex visibility" (Methods)
   - software: LIME
   - parameter: x_100AU 1e-14 to 1e-10; alpha ranges 0-1 (H13CN), 1-2 (HC3N), 0-2 (CH3CN); Rout 100 AU  
  > "covers $x_{\rm 100AU}$ from $10^{-14}-10^{-10}$ with respect to $n_{\rm H}$" (Methods)
   - assumption: Inclination 37 deg, turbulence 0.05 km/s, M*=1.8 Msun, non-LTE for HCN/HC3N, LTE for CH3CN, HCN/H13CN=70  
  > "For CH$_3$CN, we assumed LTE" (Methods)
   - fitting: chi2 minimization over grid; 3 sigma range  
  > "the 3$\sigma$ abundance range is in \[\]." (Table 1)
   - validation: Tested vertical freeze-out layer and LTE vs non-LTE (within 20%)  
  > "found a good agreement (within 20%) between LTE and non-LTE models" (Methods)
4. **Compare to comets, and ice-to-gas chemistry modelling**: Abundance ratios relative to HCN at 30 and 100 AU; gas-phase and grain-surface disk chemistry models for 1 Myr with varying turbulence  
  > "We ran a number of complete disk chemistry models for 1Myr" (Methods)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.2.2: Self-calibration, imaging, immoments  
  > "self-calibrated in phase and amplitude in CASA 4.2.2" (Methods)
- **LIME** : Radiative transfer and molecular excitation  
  > "We use the three-dimensional Monte Carlo code LIME$^{39}$ to calculate the radiative transfer and molecular excitation." (Methods)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| H13CN integrated flux | 47 | 8 | mJy km/s beam-1 | 2 | 47\[8\] |
| HC3N integrated flux | 66 | 8 | mJy km/s beam-1 | 2 | 66\[8\] |
| CH3CN 14_0-13_0 integrated flux | 30 | 6 | mJy km/s beam-1 | 2 | 30\[6\] |
| 257 GHz continuum flux density | 331 | 33 | mJy | 1 | The 257 GHz continuum flux density was determined to be 331$\pm$33 mJy |
| CH3CN abundance at 30 AU | 4.8e-13 | 3 sigma range 2.3-7.5 | n_H^-1 | 3 | 4.8 \[2.3–7.5\] |
| CH3CN/HCN ratio at 30 and 100 AU (best fit) | 0.05 and 0.2 | factors of a few | dimensionless | 4 | the best-fit HC$_3$N and CH$_3$CN abundances with respect to HCN are 0.4 and 0.05 at 30 AU, and 5 and 0.2 at 100 AU |

## Qualitative findings

- Gas-phase CH3CN cannot be explained by gas-phase chemistry alone; grain surface chemistry needed  
  > "The observed high abundance of CH$_3$CN gas with respect to HCN therefore implies that grain surface chemistry contributes significantly" (Methods)

## Claim tuples

- H: MWC 480 disk cyanide composition is comet-like | E: Detect lines and fit parametric abundance models, compare ratios to HCN | R: CH3CN and HC3N relative to HCN ~5% at 30 AU and ~20% at 100 AU versus ~10% in comets | F: Gas-phase cyanide composition is cometary | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Inheritance from protostars rejected as sole explanation  
  > "The MWC 480 cyanide composition is thus difficult to explain by inheritance alone" (main text)
- How they decided it was enough: _not stated_
- Limitation (authors): HC3N/HCN may be overestimated by an order of magnitude; vertical distribution unconstrained  
  > "the HC$_3$N/HCN abundance ratio may be overestimated by an order of magnitude using our simple abundance model" (main text)
- Caveat (inferred, ours): CH3CN detections are marginal (5 and 3.5 sigma)
- Caveat (inferred, ours): Disk structure fixed rather than fit
- Caveat (inferred, ours): Ice ratios rely on generic chemical models not fit to MWC 480

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: LIME setup
- Missing: Chemical model inputs
- Data volume (inferred): ~20-50 GB raw
- Score (inferred): 3/5, Data stated with project code but imaging and modelling details sparse.
- Rediscovery candidate: no, Recipe incomplete for imaging and modelling.

## Links

- Method: Qi et al. 2013 (ref 36) (Abundance fitting approach)
- Method: Brinch & Hogerheijde 2010 (LIME code)
- Companion: (cite: Guilloteau11) (Disk density structure of MWC 480)

## Checks

```json
{
 "quotes": 48,
 "quotes_ok": 48,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2013.1.00226.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 37,
  "rate": 0.561
 },
 "evidence_ok": true
}
```
