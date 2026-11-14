# A Luminous Molecular Gas Pair beyond Redshift 7

`2019ApJ...880L..19K` | The Astrophysical Journal Letters 2019 | first author: Koptelova, Ekaterina | arXiv: 1907.02721 | DOI: 10.3847/2041-8213/ab2ed9

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: Is molecular gas (CO) detected in the quasar candidate PSO J145.5964+19.3565 at z>7, and what are its properties and those of its companion?  
  > "we report the discovery of a luminous molecular gas pair at $z=7.09$ using the CO(6–5) and CO(7–6) line observations of $z>6.5$ quasar candidates" (Introduction)
- Target **PSO J145.5964+19.3565 (PSO145+19) and PSO145+19N**: coordinates PSO145+19: 09:42:23.14 +19:21:23.55; PSO145+19N: 09:42:23.00 +19:21:27.02  
  > "| RA (hh:mm:ss.ss) | 09:42:23.14 | 09:42:23.00 |" (Table 1); "| $z_{\rm CO}$ | 7.092$\pm$0.006 | 7.093$\pm$0.004 |" (Table 1); z/distance z_CO = 7.092±0.006 (PSO145+19); 7.093±0.004 (N)  
  > "| RA (hh:mm:ss.ss) | 09:42:23.14 | 09:42:23.00 |" (Table 1); "| $z_{\rm CO}$ | 7.092$\pm$0.006 | 7.093$\pm$0.004 |" (Table 1); distance from mean redshift of CO(6-5) and CO(7-6) lines  
  > "| RA (hh:mm:ss.ss) | 09:42:23.14 | 09:42:23.00 |" (Table 1); "| $z_{\rm CO}$ | 7.092$\pm$0.006 | 7.093$\pm$0.004 |" (Table 1)

## Data provenance

- ALMA projects: 2015.1.01452.S
- bands: Band 3  
  > "PSO145+19 was observed in Band 3 of the Atacama Large Millimeter Array (ALMA) on August 20 and 30, 2016." (2.1 ALMA observations)
- frequencies and spectral setup: ~84–92 and 96–104 GHz  
  > "The observations were carried out in frequency intervals $\sim$84–92 and 96–104 GHz" (2.1 ALMA observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.9"x0.7" (Aug 20) and 0.7"x0.4" (Aug 30)  
  > "were $\sim0.9\ensuremath{''}\times0.7\ensuremath{''}$ and $0.7\ensuremath{''}\times0.4\ensuremath{''}$, respectively." (2.1 ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: about 19 min per epoch  
  > "The total on-source time at each epoch was about 19 min." (2.1 ALMA observations)
- observing dates: August 20 and 30, 2016  
  > "on August 20 and 30, 2016" (2.1 ALMA observations)
- pi or archival as stated: _not stated_
- Line: CO 6-5 (691.47 GHz)
- Line: CO 7-6 (806.65 GHz)
- Line: H2O 1_10-1_01 (possible maser) (793.62 GHz)
- Other facility **Gemini North GMOS**: near-infrared spectrum with Lyα detection  
  > "The near-infrared spectrum of PSO145+19 ($4\times950$ s exposures) was obtained using the Gemini Multi-Object Spectrograph" (2.2 Near-infrared observations)
- Other facility **UH2.2 telescope**: deep J-band images  
  > "We also took deep $J$-band images of PSO145+19 with the UH2.2 telescope of the University of Hawaii" (2.2 Near-infrared observations)
- Other facility **Pan-STARRS1**: quasar candidate selection and y/z photometry  
  > "To select PSO145+19, we used the first and second internal releases of the PS1 catalogs" (3.2 Lyα line)
- External data: CO SLED ratios of SMM J16359+6612 used to derive CO(1-0) luminosity  
  > "$L^{'}$$_{\rm CO(6-5)}$/$L^{'}$$_{\rm
CO(1-0)}\approx0.37$ and $L^{'}$$_{\rm CO(7-6)}$/$L^{'}$$_{\rm
CO(1-0)}\approx0.13$" (4.1 CO excitation and molecular gas mass) [from (cite: 2005A&A...440L..45W)]
- External data: Water maser line prediction at 793.62 GHz and conditions  
  > "predicted by the calculations of (cite: 2016MNRAS.456..374G)" (3.1 CO and water emission lines) [from (cite: 2016MNRAS.456..374G)]

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

- task: CASA CLEAN  
  > "The visibility data were imaged using task CLEAN of the Common Astronomy Software Applications" (2.1 ALMA observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "with a cell of 0$\ensuremath{''}$12, natural weighting and channel width of 23.44 MHz" (2.1 ALMA observations)
- uv taper: 1"  
  > "We run CLEAN with a taper parameter of 1$\ensuremath{''}$ to reduce noise fluctuations." (2.1 ALMA observations)
- cell size: 0.12"  
  > "with a cell of 0$\ensuremath{''}$12" (2.1 ALMA observations)
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

- Quasar candidate selection criteria  
  > "$z_{\rm PS1}<24$ AB magnitudes (cite: 2017NatSR...741617K)" (2.1 ALMA observations) [from (cite: 2017NatSR...741617K)]
- Line luminosity formulae  
  > "The luminosities of the emission lines were computed using formulae (1) and (3) of (cite: 2005ARA&A..43..677S)." (3.1 CO and water emission lines) [from (cite: 2005ARA&A..43..677S)]

### Not stated but needed to reproduce (our reading)

- CASA version
- Calibration pipeline/manual and calibrators
- Clean threshold, niter, masks
- Final rms and beam of the cubes
- Gaussian fitting method and how N_beam was set
- Weighting scheme for averaging CO(1-0) luminosities

## Analysis recipe

1. **Search for emission lines**: Intensity maps averaging five channels (~400 km/s) with IMMOMENTS moments=-1; search for SNR>3 peaks at expected CO frequencies  
  > "The maps were calculated using CASA task IMMOMENTS with MOMENTS=–1." (2.1 ALMA observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Spurious probability of two lines at fixed separation ~1e-29  
  > "the probability of such a simultaneous event is on the order of 10$^{-29}$." (3.1 CO and water emission lines)
2. **Extract spectra and line fluxes**: Integrate within 4" apertures; Gaussian fits; sum channels within ±2σ  
  > "integrating the intensities within apertures of 4$\ensuremath{''}$ in diameters centered on the two peaks." (3.1 CO and water emission lines)
   - software: CASA
   - fitting: Gaussian line profiles  
  > "The observed line profiles were fitted with Gaussians." (3.1 CO and water emission lines)
   - validation: _not stated_
3. **Measure sizes**: 2D Gaussian fit to CO(6-5) maps; size is quadratic mean of FWHMs  
  > "we fitted their CO(6–5) intensity distributions with two-dimensional Gaussians using CASA’s task IMFIT." (3.1 CO and water emission lines)
   - software: CASA IMFIT
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive molecular gas mass**: CO(1-0) luminosity from CO SLEDs of SMM J16359+6612 and IRAS F10214+4724, weighted mean, times alpha  
  > "the CO(1–0) luminosities of PSO145+19 and PSO145+19N were estimated as the weighted means of the CO(1–0) luminosities independently derived from the CO(6–5) and CO(7–6) lines." (4.1 CO excitation and molecular gas mass)
   - assumption: alpha = 0.8 Msun (K km/s pc^2)^-1  
  > "$\it
\alpha=\rm0.8$$M_{\odot}$ (K km s$^{-1}$ pc$^{2}$)$^{-1}$" (4.1 CO excitation and molecular gas mass)
   - fitting: _not stated_
   - validation: Two SLEDs compared to show uncertainty  
  > "The differences in the gas masses using these two comparison SLEDs reflect the uncertainties related to the unknown shape of the CO SLEDs" (4.1 CO excitation and molecular gas mass)
5. **Dynamical mass**: Isotropic virial estimator M_dyn=2.8e5 FWHM^2 R  
  > "$M_{\rm dyn}=2.8\times10^{5}$(FWHM)$^{2}R$" (4.2 Spatial extent and dynamical mass)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : imaging (CLEAN), moment maps, IMFIT  
  > "The visibility data were imaged using task CLEAN of the Common Astronomy Software Applications" (2.1 ALMA observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| I_CO(6-5) PSO145+19 | 2.81 | 0.36 | Jy km/s | 2 | / $I_{\rm CO(6-5)}$ (Jy km s$^{-1}$) / 2.81$\pm$0.36 / 3.12$\pm$0.40 / |
| I_CO(6-5) PSO145+19N | 3.12 | 0.40 | Jy km/s | 2 | / $I_{\rm CO(6-5)}$ (Jy km s$^{-1}$) / 2.81$\pm$0.36 / 3.12$\pm$0.40 / |
| M_H2 (SMM J16359 SLED) PSO145+19 / N | 25.7 / 29.1 | 2.9 / 3.1 | 1e10 Msun | 4 | / $M_{\rm H_{2}}$$^{a}$ (10$^{10}M_{\bigodot}$) / 25.7$\pm$2.9 / 29.1$\pm$3.1 / |
| M_dyn PSO145+19 / N | 36.6 / 61.7 | 13.8 / 7.8 | 1e10 Msun | 5 | / $M_{\rm dyn}$ (10$^{10}M_{\bigodot}$) / 36.6$\pm$13.8 / 61.7$\pm$7.8 / |
| Dust continuum 3-sigma upper limit | 0.99 | not stated | mJy | 0 | The three-sigma upper limit on the flux of the dust continuum estimated at the position of PSO145+19 is 0.99 mJy. |
| Separation of the two companions | 20.7 | not stated | kpc | 0 | The linear distance between PSO145+19 and PSO145+19N is 20.7 kpc |

## Qualitative findings

- Possible 793.62 GHz water maser detected in PSO145+19N at SNR 5  
  > "We also detected a third strong emission line in the spectrum of PSO145+19N with a line SNR of 5." (3.1 CO and water emission lines)

## Claim tuples

- H: Is there molecular gas at z>7 associated with the quasar candidate? | E: ALMA Band 3 CO(6-5) and CO(7-6) search | R: Two CO companions at z~7.09, integrated SNRs 5-12 | F: First detection of molecular gas beyond z=7, a luminous pair separated by 20.7 kpc | **supported**
- H: How massive is the molecular gas? | E: CO SLED scaling to CO(1-0) with alpha=0.8 | R: (16-29)e10 Msun per companion | F: Among the largest known reservoirs at high z, dependent on assumed SLED | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Deeper observations are needed to strengthen results  
  > "Further, deeper observations in the near-infrared/submm wavelengths are needed to strengthen the results reported here." (4.2 Spatial extent and dynamical mass)
- Caveat (inferred, ours): CO(7-6) peak SNR only 2-3; detection relies on integrated SNR
- Caveat (inferred, ours): Gas masses depend on assumed SLED and alpha
- Caveat (inferred, ours): Water maser identification is tentative
- Caveat (inferred, ours): Low resolution; no reduction details

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: CASA version and calibration details
- Missing: Clean parameters and masks
- Missing: Line fitting and weighted-mean procedures
- Data volume (inferred): ~10-30 GB raw for two Band 3 executions
- Score (inferred): 4/5, Short letter; data likely public, but calibration and imaging details are sparse.
- Rediscovery candidate: no, Recipe is incomplete (no CASA version, calibration, or clean details), though the results are numeric.

## Links

- Method: (cite: 2005ARA&A..43..677S) (luminosity formulae and conversion factor)
- Method: (cite: 2017NatSR...741617K) (candidate selection)
- Companion: (cite: koptelova2019) (related work on UV line blueshifts in high-z quasars)
- Related: Pan-STARRS1

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
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 32,
  "rate": 0.464
 },
 "evidence_ok": true
}
```
