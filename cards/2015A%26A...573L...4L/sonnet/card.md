# ALMA observations of α Centauri. First detection of main-sequence stars at 3 mm wavelength

`2015A&A...573L...4L` | Astronomy and Astrophysics 2015 | first author: Liseau, R. | arXiv: 1412.3923 | DOI: 10.1051/0004-6361/201425189

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: stellar_physics, sun
- Question: Can ALMA resolve the alpha Cen A and B components at mm/submm wavelengths, give their flux ratios, and extend the SED to 3 mm to probe the chromospheric temperature minimum and free-free emission?  
  > "In the present context, we intend to extend the spectral mapping (SED) to longer wavelengths, where the contrast between stellar photospheric and chromospheric emission becomes increasingly evident." (abstract)
- Target **alpha Cen A and B**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00170.S
- bands: Band 3 (97.5 GHz), Band 7 (343.5 GHz), Band 9 (679 GHz)  
  > "The observations in Band 3, centered on 97.5 GHz (3.1 mm), were taken on 2014 July 3" (Observations and data reduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: 7.5 GHz effective bandwidth over four spectral windows per band  
  > "with $7.5$ GHz effective bandwidth spread over four spectral windows in each of the bands." (Observations and data reduction)
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.72x1.50 (B3), 0.42x0.28 (B7), 0.22x0.16 arcsec (B9)  
  > "0.2$ mJy beam$^{-1}$ (0$\stackrel {\prime \prime}{_{\bf \cdot}}$42 $\times$ 0$\stackrel {\prime \prime}{_{\bf \cdot}}$28, 47$^{\circ}$) in Band 7" (Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: rms 0.02 (B3), 0.2 (B7), 1.0 (B9) mJy/beam  
  > "the rms noise per synthesized beam in the pointing center was $0.02$ mJy beam$^{-1}$" (Observations and data reduction)
- time on source: ~30 min (B3), ~2 min (B7), ~8 min (B9)  
  > "$\sim20$ min of observing time with $\sim2$ min on-source." (Observations and data reduction)
- observing dates: 2014 July 3 (Band 3), July 7 (Band 7), July 18 (Band 9)  
  > "were taken on 2014 July 7 using 32 antennas" (Observations and data reduction)
- pi or archival as stated: _not stated_
- Other facility **Herschel (PACS, SPIRE) / APEX**: Earlier far-IR/submm photometry showing temperature minimum; 70 micron flux ratio  
  > "one observation at 70 $\mu$m with *Herschel*-PACS (cite: molinari2010; wiegert2014) nearly resolved the binary" (Results)
- External data: Stellar radii R_A=1.224, R_B=0.863 Rsun  
  > "$R_{\rm A}=1.224\pm0.003$ $R_{\odot}$ and $R_{\rm B}=0.863\pm0.003$$R_{\odot}$." (footnote 4) [from Table 4 of (cite: wiegert2014)]
- External data: Previous flux ratio B/A = 0.44±0.18 (0.09-70 micron)  
  > "Over the wavelength range $0.09 - 70$ $\mu$m, the ratio was $S_{\!\nu}^{\rm B}/S_{\!\nu}^{\rm A}=0.44\pm0.18$" (Results) [from (cite: wiegert2014)]

## Processing

### Calibration

- pipeline or manual: CASA, standard procedures  
  > "Calibration was performed using the CASA package[^2] following standard procedures" (Observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ceres (Bands 3, 9); Titan (Band 7)  
  > "Titan was used for Band 7 (343.5 GHz, 872.8 $\mu$m)" (Observations and data reduction)
- flux scale uncertainty: 5%, 7%, 15% for Bands 3, 7, 9  
  > "we estimate the absolute flux calibration to be accurate to within $5\%$, $7\%$, and $15\%$ for Bands 3, 7, and 9, respectively." (Observations and data reduction)
- self calibration: Band 9 only, on alpha Cen A  
  > "In Band 9, $\alpha \, {\rm Cen\,A}$ was strong enough to perform self-calibration, improving the rms noise." (Observations and data reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs in Band 7; natural in Bands 3 and 9 (robust value not given)  
  > "imaging was performed using Briggs weighting in Band 7 and natural weighting on Bands 3 and 9." (Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied to final images  
  > "In the final, primary beam-corrected images" (Observations and data reduction)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Brightness temperature formula  
  > "(cite: liseau2013)" (footnote 3) [from (cite: liseau2013)]

### Not stated but needed to reproduce (our reading)

- CASA version
- Briggs robust value
- Method of flux extraction (aperture vs Gaussian fit) and uncertainties
- Phase/pointing offsets and details of self-cal solint
- Distance to alpha Cen used

## Analysis recipe

1. **calibrate and image**: CASA calibration with Ceres/Titan flux scales, quasar gain and bandpass calibrators; imaging with Briggs/natural weighting; B9 self-cal; primary beam correction  
  > "using, for all data sets, the quasar J$1617-5848$ as complex gain calibrator" (Observations and data reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **measure flux densities, ratios and spectral indices**: Fluxes of A and B in each band; B/A ratios; spectral index alpha between bands  
  > "The measured flux densities are reported in Table [\[data\]](#data) and also displayed graphically in Fig. [2](#freq)." (Results)
   - fitting: _not stated_
   - validation: _not stated_
3. **compute brightness temperatures and compare with photospheres**: Convert flux to T_B with stellar radius plus chromospheric height and compare to photospheric levels  
  > "In Fig. [3](#alma_ab), the SEDs are presented for both stars in terms of brightness temperature[^3] versus wavelength." (Results)
   - assumption: Chromospheric height ~0.1% of stellar radius, as in the Sun  
  > "In the Sun, the height of the chromosphere $\int\!dh$ corresponds to about 0.1% of its radius." (Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : calibration and imaging  
  > "Calibration was performed using the CASA package[^2] following standard procedures" (Observations and data reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| alpha Cen A flux density Band 3 (3075 um) | 3.373 | 0.011 | mJy | 2 | $3.373\pm 0.011$ \[307\] |
| alpha Cen B flux density Band 3 | 1.585 | 0.016 | mJy | 2 | $1.585\pm 0.016$    \[99\] |
| alpha Cen A flux density Band 7 | 26.06 | 0.19 | mJy | 2 | $26.06\pm 0.19$ \[137\] |
| alpha Cen B flux density Band 7 | 12.04 | 0.23 | mJy | 2 | $12.04\pm 0.23$    \[52\] |
| alpha Cen A flux density Band 9 | 107.2 | 1.5 | mJy | 2 | $107.2\pm 1.5$      \[71\] |
| alpha Cen B flux density Band 9 | 57.6 | 4.5 | mJy | 2 | $57.6\pm 4.5$      \[13\] |
| flux ratio B/A at 3.1 mm | 0.47 | 0.006 | dimensionless | 2 | $=0.47\pm0.006$ at 3.1 mm |
| flux ratio B/A at 870 um | 0.46 | 0.01 | dimensionless | 2 | $=0.46\pm0.01$ at 870 $\mu$m |
| flux ratio B/A at 440 um | 0.54 | 0.04 | dimensionless | 2 | $S_{\!\nu}^{\rm B}/S_{\!\nu}^{\rm A}=0.54\pm0.04$ at 440 $\mu$m |
| spectral index alpha(7,3) A / B | 1.62 / 1.61 | not stated | dimensionless | 2 | / 2.08                 / 1.62                 / |

## Qualitative findings

- First detection of main-sequence stars at 3.1 mm; both components resolved in all bands  
  > "this ALMA measurement constitutes the first detection of main-sequence stars at 3.1 mm." (Results)
- 3 mm emission greatly exceeds photospheric prediction; chromospheric free-free origin  
  > "The observed 3.1 mm emission greatly exceeds what is predicted from the stellar photospheres" (abstract)

## Claim tuples

- H: ALMA can resolve A and B and give accurate flux ratios consistent with earlier estimates | E: Bands 3, 7, 9 imaging | R: B/A = 0.54±0.04, 0.46±0.01, 0.47±0.006 | F: Ratios agree with earlier 0.44±0.18 | **supported**
- H: mm emission is chromospheric free-free | E: Spectral indices and comparison with photospheres | R: Spectral indices 1.6-2.3, 3 mm far above photosphere | F: Consistent with optically thick free-free | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Sparse spectral sampling prevents a conclusive statement on changing opacities  
  > "a more conclusive statement would require a tighter spectral sampling, including the intermediate ALMA bands." (Discussion)
- Caveat (inferred, ours): Flux extraction method and errors unspecified
- Caveat (inferred, ours): Band 9 calibration uncertainty is 15%, comparable to some differences
- Caveat (inferred, ours): Pointing offset raises noise on B

## Reproducibility

- Data public (paper): Project code given in acknowledgements  
  > "ADS/JAO.ALMA#2013.1.00170.S" (Acknowledgements)
- Products in archive: _not stated_
- Missing: CASA version
- Missing: Briggs robust
- Missing: flux measurement method
- Missing: self-cal parameters
- Data volume (inferred): ~10-50 GB raw
- Score (inferred): 3/5, Simple measurement and public data, but processing details are sparse.
- Rediscovery candidate: yes, Public data, simple numeric fluxes, though details missing.

## Links

- Companion: (cite: liseau2013) (Earlier Herschel detection of temperature minimum)
- Companion: (cite: wiegert2014) (Earlier flux ratio and stellar parameters)
- Related: DUNES

## Checks

```json
{
 "quotes": 40,
 "quotes_ok": 40,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 61,
  "stated": 26,
  "rate": 0.426
 },
 "evidence_ok": true
}
```
