# New ALMA and Fermi/LAT Observations of the Large-scale Jet of PKS 0637-752 Strengthen the Case Against the IC/CMB Model

`2017ApJ...835L..35M` | The Astrophysical Journal Letters 2017 | first author: Meyer, Eileen T. | arXiv: 1702.00015 | DOI: 10.3847/2041-8213/835/2/L35

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type multi_facility_alma_minor

## Science

- Fields: agn_and_quasars
- Question: Do new ALMA constraints on the synchrotron SED and deeper Fermi/LAT limits rule out the IC/CMB model for the X-ray emission of the PKS 0637-752 large-scale jet?  
  > "With these deeper limits we rule out the IC/CMB model at the 8.7$\sigma$ level." (abstract)
- Target **PKS 0637-752 large-scale jet (knot wk8.9 and four-knot cluster)**: coordinates _not stated_; z/distance z=0.651  
  > "The radio-loud quasar PKS 0637$-$752 ($z$=0.651) was the first astrophysical source observed by the *Chandra* X-ray observatory" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00075.S
- bands: Band 3 (~3 mm), 6 (~1.2 mm), 7 (~870 um)  
  > "there is available data for PKS 0637$-$752 in ALMA bands 3 ($\sim
3\,{\rm mm}$), 6 ($\sim 1.2 \, {\rm mm}$) and 7 ($\sim 870 \, {\rm \mu
  m}$)." (2.1 ALMA)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: B3 1.03x0.79"; B6 0.38x0.29"; B7 0.33x0.22"  
  > "$\theta_{\rm B3} = 1.03 \times 0.79''$, $\sigma_{\rm B6} = 21.6 \, {\rm \mu Jy \, beam^{-1}}$ and $\theta_{\rm
  B6} = 0.38 \times 0.29''$" (2.1 ALMA)
- max recoverable scale: _not stated_
- sensitivity: B3 66.2, B6 21.6, B7 46.0 uJy/beam  
  > "$\sigma_{\rm B3} = 66.2 \, {\rm \mu Jy
  \, beam^{-1}}$" (2.1 ALMA)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archival calibrator observations from ALMACAL  
  > "PKS 0637$-$752 is a bright southern source which is routinely used as an ALMA calibrator." (2.1 ALMA)
- Other facility **Fermi/LAT**: Pass 8 gamma-ray upper limits, 2008 Aug to 2016 Nov  
  > "corresponding to calendar dates 2008 August 4 to 2016 November 10" (2.2 Fermi)
- Other facility **Chandra, VLA/ATCA, HST**: X-ray, radio and IR/optical SED data taken from M15  
  > "All other data are taken from M15 and references therein." (Data Analysis)
- External data: Radio, IR/optical and X-ray SED data points and synchrotron model curves, unchanged from M15  
  > "The radio and IR/optical data shown as solid points are also unchanged from the previous paper." (3.1 Ruling out IC/CMB with the New Data) [from M15 (cite: meyer2015)]
- External data: L17 data and model fits for comparison  
  > "we show as green open circles and dashed lines the data and model fits recently presented in (cite: lucchini2016)" (3.2 The Importance of a Complete Synchrotron SED) [from (cite: lucchini2016)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline per scheduling block, then self-calibration, per ALMACAL  
  > "for each scheduling block of a given science project, we run the ALMA pipeline and extract the calibrated visibilities of all calibrators used." (2.1 ALMA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10% adopted for all ALMA fluxes  
  > "current estimates suggest 10% as the maximum value, which we use for all ALMA fluxes presented in this paper." (2.1 ALMA)
- self calibration: One self-calibration run, then dominant core point source subtracted from visibilities  
  > "Then a run of self-calibration is carried out (always possible thanks to the brightness of the calibrators) and the dominant point-source component at the phase centre is subtracted" (2.1 ALMA)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "natural weighing is used during imaging" (2.1 ALMA)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: flux measured on primary-beam-corrected maps  
  > "in the ALMA band 3, 6 and 7 primary-beam-corrected maps" (2.1 ALMA)
- array combination: all available visibilities per band combined  
  > "for a given calibrator, we combine all available visibilities on each band to create a deep image" (2.1 ALMA)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA data extraction and calibration follow ALMACAL  
  > "We refer the reader to (cite: Oteo2016a) for details on data extraction and calibration." (2.1 ALMA) [from (cite: Oteo2016a)]
- Progressive-binning Fermi method  
  > "we utilize the ‘progressive-binning’ approach first described in (cite: meyer2014), which can be consulted for further details as well as M15." (2.2 Fermi) [from (cite: meyer2014); M15 (cite: meyer2015)]
- IC/CMB prediction via shift formulae  
  > "using the shift formulae given in G06" (3.1 Ruling out IC/CMB with the New Data) [from G06 (cite: georganopoulos2006)]

### Not stated but needed to reproduce (our reading)

- Which ALMA execution blocks and projects went into each band's combined image
- Contour regions used for knot flux measurement
- Exact Fermi analysis tool and version, IRFs, zenith and energy cuts
- Cell and image size, masking of imaging
- Pipeline and CASA versions
- Details of the empirical SED fit beyond by eye

## Analysis recipe

1. **Make ALMACAL deep images**: Pipeline calibration, self-calibration, core subtraction, combine visibilities per band, natural-weighted imaging  
  > "Finally, for a given calibrator, we combine all available visibilities on each band to create a deep image" (2.1 ALMA)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure knot fluxes**: Contours around each knot on primary-beam-corrected maps  
  > "using contours around each knot using `casaviewer`, as the knots are resolved" (2.1 ALMA)
   - software: casaviewer
   - parameter: 10% flux error  
  > "current estimates suggest 10% as the maximum value, which we use for all ALMA fluxes presented in this paper." (2.1 ALMA)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fermi progressive-binning upper limits**: 155 light-curve bins ordered by TS and progressively combined; power law index 2.7 fixed; 95% limits in five energy bands  
  > "We ordered the 155 light curve bins according to TS and then progressively combined them in our analysis" (2.2 Fermi)
   - software: make3FGLxml
   - parameter: 13 new sources added to the 3FGL model  
  > "We added 13 new sources to the base model populated with 3FGL catalog sources" (2.2 Fermi)
   - assumption: fixed spectral index 2.7  
  > "using a power-law model with a fixed spectral index of 2.7" (2.2 Fermi)
   - fitting: maximum likelihood  
  > "using a maximum-likelihood approach as described in M15" (2.2 Fermi)
   - validation: free spectral index check gave no significant change  
  > "Results are not significantly altered by using a free spectral index" (2.2 Fermi)
4. **Empirical synchrotron SED and IC/CMB prediction**: By-eye power law with exponential cutoff; shift to X-rays via G06 formulae  
  > "The empirical (by eye) fit is simply a power-law with a scaled exponential cutoff," (3.1 Ruling out IC/CMB with the New Data)
   - parameter: four knots: N=2e-14, gamma=0.35, nu1=4e11 Hz, beta=0.25  
  > "$\gamma=0.35$, $\nu_1=4\times
 10^{11}$ Hz, and $\beta=0.25$" (3.1 Ruling out IC/CMB with the New Data)
   - fitting: by eye  
  > "The empirical (by eye) fit is simply a power-law with a scaled exponential cutoff," (3.1 Ruling out IC/CMB with the New Data)
   - validation: ALMA points fall on the M15 model  
  > "note that they fall nearly exactly on the synchrotron model curves which are unchanged from M15" (3.1 Ruling out IC/CMB with the New Data)
5. **Significance of exclusion**: Profile likelihood per band, combined with inverse normal method  
  > "IC/CMB is ruled out at a 8.7$\sigma$ limit when we combine the individual band results using the inverse normal method." (3.1 Ruling out IC/CMB with the New Data)
   - fitting: 2DeltaL ~ chi2 with 1 dof  
  > "the statistic $2\Delta L$ is distributed as a $\chi^2$ with one degree of freedom when all other parameters are fixed" (3.1 Ruling out IC/CMB with the New Data)
   - validation: _not stated_

## Software

- **CASA** : ALMA data processing and imaging  
  > "CASA (cite: 2012ASPC..461..849P)" (Software)
- **casaviewer** : knot flux measurement  
  > "using contours around each knot using `casaviewer`" (2.1 ALMA)
- **make3FGLxml** : Fermi base source model  
  > "supplied by the `make3FGLxml` tool" (2.2 Fermi)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| wk8.9 ALMA flux (Bands 3, 6, 7) | 1.9, 3.2, 2.6 | 10% | mJy | 2 | For wk8.9, we measured fluxes in the three bands of 1.9, 3.2, and 2.6 mJy, respectively. |
| Combined knots ALMA flux (Bands 3, 6, 7) | 6.0, 10.7, 7.9 | 10% | mJy | 2 | For the combined knots the values are 6.0, 10.7, and 7.9 mJy. |
| IC/CMB exclusion significance, four knots combined | 8.7 | not stated | sigma | 5 | Overall, IC/CMB is ruled out at a 8.7$\sigma$ limit when we combine the individual band results |
| IC/CMB exclusion significance, wk8.9 | 5.3 | not stated | sigma | 5 | implies an overall 5.3$\sigma$ upper limit for the single X-ray brightest knot |
| Doppler factor upper limit, four knots | <5.3 | 95% limit | dimensionless | 5 | the limit for the four brightest knots is $\delta<5.3$ |

## Qualitative findings

- L17 underproduces ALMA fluxes owing to a steeper radio spectrum, and an empirical SED is equivalent to physical models for the IC/CMB test  
  > "an empirical description of the synchrotron SED is equivalent to physical models" (Summary & Conclusions)

## Claim tuples

- H: Does the new ALMA data confirm the M15 synchrotron SED? | E: Measured wk8.9 and four-knot fluxes in bands 3, 6, 7 and overplotted on the model | R: ALMA points lie on the M15 model curves | F: Synchrotron peak near 10^13.5 Hz; empirical model confirmed | **supported**
- H: Is IC/CMB ruled out by deeper Fermi limits? | E: Progressive-binning Fermi Pass 8 limits compared to predicted IC/CMB | R: 8.7 sigma combined exclusion | F: IC/CMB ruled out | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: L17 claim that IC/CMB is not ruled out is attributed to a missing ALMA data and incorrect radio index  
  > "A recent claim for the opposite (L17) stems from using a dataset that did not include critical ALMA observations" (Summary & Conclusions)
- How they decided it was enough: _not stated_
- Caveat (inferred, ours): Empirical by-eye SED fit has no uncertainties
- Caveat (inferred, ours): ALMA flux from core-subtracted self-calibrated data with 10% assumed error
- Caveat (inferred, ours): Fermi limits depend on the fixed index 2.7 and selection of quiescent bins

## Reproducibility

- Data public (paper): ALMA calibrator data from the archive (ALMACAL); Fermi data public (implied)  
  > "The ALMA data used in this paper have been taken from ALMACAL" (2.1 ALMA)
- Products in archive: _not stated_
- Missing: Fermi analysis software and cuts
- Missing: ALMACAL scheduling blocks used
- Missing: Knot contour definitions
- Data volume (inferred): Large (hundreds of GB to TB) for all ALMA calibrator execution blocks, plus ~8 yr of Fermi data
- Score (inferred): 3/5, Methods are described briefly with heavy reliance on ALMACAL and M15; the numerical results are clear but key settings are missing.
- Rediscovery candidate: no, Recipe incomplete and depends on a custom ALMACAL pipeline and Fermi analysis details.

## Links

- Method: (cite: Oteo2016a) (ALMACAL data extraction and calibration)
- Method: (cite: meyer2014) (progressive-binning Fermi method)
- Method: (cite: georganopoulos2006) (IC/CMB shift formulae)
- Companion: (cite: meyer2015) (Earlier Fermi limits and SED data for PKS 0637-752)
- Companion: (cite: lucchini2016) (Competing claim that IC/CMB is not ruled out)
- Related: ALMACAL

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
 "obscore_codes_not_in_card": [
  "2012.1.00335.S",
  "2012.1.00554.S",
  "2012.1.00603.S",
  "2012.1.00641.S",
  "2012.1.01108.S",
  "2013.1.00063.S",
  "2013.1.00070.S",
  "2013.1.00280.S",
  "2013.1.00287.S",
  "2013.1.00319.S",
  "2013.1.00450.S",
  "2013.1.00535.S",
  "2013.1.00700.S",
  "2013.1.00993.S",
  "2013.1.01136.S",
  "2013.1.01155.S",
  "2015.1.00190.S",
  "2015.1.00204.S",
  "2015.1.00979.S"
 ],
 "codes_printed_but_missing": [
  "2012.1.00335.S",
  "2012.1.00554.S",
  "2012.1.00603.S",
  "2012.1.00641.S",
  "2012.1.01108.S",
  "2013.1.00063.S",
  "2013.1.00070.S",
  "2013.1.00280.S",
  "2013.1.00287.S",
  "2013.1.00319.S",
  "2013.1.00450.S",
  "2013.1.00535.S",
  "2013.1.00700.S",
  "2013.1.00993.S",
  "2013.1.01136.S",
  "2013.1.01155.S",
  "2015.1.00190.S",
  "2015.1.00204.S",
  "2015.1.00979.S"
 ],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 39,
  "rate": 0.527
 },
 "evidence_ok": true
}
```
