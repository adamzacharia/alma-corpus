# Solar Polar Brightening and Radius at 100 and 230 GHz Observed by ALMA

`2019ApJ...871...45S` | The Astrophysical Journal 2019 | first author: Selhorst, Caius L. | arXiv: 1811.12158 | DOI: 10.3847/1538-4357/aaf4f2

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: sun
- Question: Is polar brightening present in ALMA single-dish solar maps at 100 and 230 GHz, how large is it, and how does it (and the solar radius) compare with the FAL-C and SSC atmospheric models?  
  > "Aiming to verify the presence of the polar brightening in the millimetric range, in this work we analysed ALMA single-dish maps observed at 100 and 230 GHz during the Science Verification period in December 2015." (Introduction)
- Target **Sun (quiet Sun, polar regions)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00020.SV
- bands: Band 3 (84-116 GHz), six maps; Band 6 (211-275 GHz), three maps; reference 100 and 230 GHz  
  > "The data comprise six maps obtained in Band 3 (84 –116 GHz) and other three in Band 6 (211 – 275 GHz)." (ALMA solar maps)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: single-dish 12 m antenna, fast-scan maps  
  > "these maps were obtained by a single dish antenna with 12 m of diameter" (ALMA solar maps)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 58" at 100 GHz and 25" at 230 GHz (nominal)  
  > "they present nominal spatial resolutions of 58” at 100 GHz and 25” at 230 GHz" (ALMA solar maps)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2015 December 16-20 (Science Verification)  
  > "The data were observed during the Science Verification period, 2015 December 16-20" (ALMA solar maps)
- pi or archival as stated: _not stated_
- External data: Quiet-Sun brightness temperatures 7280±250 K (100 GHz) and 5900±190 K (230 GHz) for comparison  
  > "in agreement with the values suggested by (cite: White2017) ($7280\pm250$ K)" (Data analysis and results) [from (cite: White2017)]
- External data: FAL-C atmospheric model  
  > "suggested that the observations were best fitted by the average quiet Sun model C (FAL-C) proposed by (cite: FAL1993)." (Atmospheric Models) [from (cite: FAL1993)]
- External data: SSC atmospheric model with extended chromosphere  
  > "The observed polar brightenings were also compared with atmospheric model SSC proposed by (cite: Selhorst2005a)" (Atmospheric Models) [from (cite: Selhorst2005a)]
- External data: Historical radio solar radius compilations  
  > "we combine the historical data compiled by (cite: Rozelot2015) and (cite: Menezes2017)" (Discussion and conclusions) [from (cite: Rozelot2015); (cite: Menezes2017)]
- Simulation/model as data: 1D FAL-C and SSC models expanded to 2D (50x50 km2 pixels), brightness computed every 100 km and convolved with 25" and 58" Gaussians  
  > "Each matrix pixel represents an area of $\rm50\times 50~km^2$." (Atmospheric Models)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Released SV fast-scan maps described by White et al. 2017 used  
  > "We analysed ALMA fast-scan single-dish maps described by (cite: White2017)." (ALMA solar maps)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
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
- smoothing: Band 6 maps convolved with a 54" (18 pixel) Gaussian to match 100 GHz resolution  
  > "convolution of the Band 6 maps and a bi-dimensional gaussian beam with 54” (18 pixels)" (Data analysis and results)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Quiet Sun Tb taken as mean of 120"x120" area at disc center  
  > "Following the method used by (cite: White2017), the $T_{qS}$ of each map was assumed to be the mean brightness temperature of a small area at disc center" (Data analysis and results) [from (cite: White2017)]
- Polar brightening from average of 61 radial profiles  
  > "Following (cite: Selhorst2003; Selhorst2011), the polar brightening was estimated from the average of 61 radial profiles" (Data analysis and results) [from (cite: Selhorst2003; Selhorst2011)]
- Radius defined at 50% of T_qS  
  > "Following (cite: Costa1999), the radius was determined at the point in which the brightness temperature drops to 50% of the $T_{qS}$ value." (Data analysis and results) [from (cite: Costa1999)]

### Not stated but needed to reproduce (our reading)

- Location/format of the SV single-dish maps and calibration details (brightness scale, pointing)
- Pixel size of maps
- How uncertainty on polar brightening was exactly propagated
- Details of polynomial fit to radius vs frequency data
- Exact radius values from literature used in Fig 6

## Analysis recipe

1. **Degrade Band 6 maps**: Convolve with Gaussian of 54" from theta100^2=theta230^2+theta_x^2  
  > "determined by the relation $\theta_{100}^2=\theta_{230}^2+\theta_x^2$, assuming that the ALMA observational beams are gaussian." (Data analysis and results)
   - fitting: _not stated_
   - validation: _not stated_
2. **Quiet Sun temperature**: Mean Tb in 120"x120" disc-centre box  
  > "the $T_{qS}$ of each map was assumed to be the mean brightness temperature of a small area at disc center ($120''\times120''$" (Data analysis and results)
   - fitting: _not stated_
   - validation: Compared with White 2017 and Alissandrakis 2017  
  > "that is in agreement with the values suggested by (cite: White2017) ($7280\pm250$ K)" (Data analysis and results)
3. **Polar brightening**: Average of 61 radial profiles every 1 deg at PA 60-120 (South) and 240-300 (North); peak relative to T_qS  
  > "average of 61 radial profiles through the disc center, that were taken every 1$^\circ$ between 60 and 120$^\circ$, and between 240 and 300$^\circ$ position angles" (Data analysis and results)
   - fitting: _not stated_
   - validation: _not stated_
4. **Solar radius**: Contour at 0.5 T_qS, 1440 points, circle fit  
  > "solar limb position determined by `contour` procedure of IDL at the level equal to half of $T_{qS}$; c) 1440 points determined over the curve resulting from step b; d) a circumference fit adjusted to the points." (Data analysis and results)
   - software: IDL
   - fitting: _not stated_
   - validation: _not stated_
5. **Model limb brightening**: Compute Tb from FAL-C and SSC with H and H- free-free opacities, 2D expansion with R=696 Mm, Gaussian convolution to 25" and 58"  
  > "the brightness temperature was computed every 100 km in the center-to-limb direction, and these results convolved with a Gaussian function with the same resolutions of the observed maps" (Atmospheric Models)
   - assumption: R_sun = 696 Mm (959.64")  
  > "$R_\Sun=696$ Mm or $959''.64$" (Atmospheric Models)
   - fitting: _not stated_
   - validation: Compared model and observed profiles  
  > "the shape of the simulated center-to-limb profiles generally agrees with the observations when the uncertainties are considered." (Atmospheric Models)

## Software

- **IDL** : contour procedure for limb position  
  > "solar limb position determined by `contour` procedure of IDL" (Data analysis and results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mean polar brightening 100 GHz South | 6.1 | 2.8 | % | 3 | $T_B/T_{qS} = 6.1\%\pm 2.8$ and $5.1\%\pm2.7$, respectively for the South and North poles |
| Mean polar brightening 100 GHz North | 5.1 | 2.7 | % | 3 | $T_B/T_{qS} = 6.1\%\pm 2.8$ and $5.1\%\pm2.7$, respectively for the South and North poles |
| Mean polar brightening 230 GHz South | 9.2 | 4.7 | % | 3 | $T_B/T_{qS} = 9.2\% \pm 4.7$ for the South and $8.7\% \pm 4.4$ for the North pole intensities |
| Mean polar brightening 230 GHz North | 8.7 | 4.4 | % | 3 | $T_B/T_{qS} = 9.2\% \pm 4.7$ for the South and $8.7\% \pm 4.4$ for the North pole intensities |
| Solar radius 100 GHz | 965.9 | 3.2 | arcsec | 4 | mean values of $965''.9\pm3''.2$ at 100 GHz and $961''.6\pm2''.1$ at 230 GHz |
| Solar radius 230 GHz | 961.6 | 2.1 | arcsec | 4 | mean values of $965''.9\pm3''.2$ at 100 GHz and $961''.6\pm2''.1$ at 230 GHz |
| Mean T_qS 100 GHz | 7220 | 200 | K | 2 | The average $T_{qS}$ obtained for the six 100 GHz maps was $7220\pm 200$ K |
| Mean T_qS 230 GHz | 6280 | 200 | K | 2 | the mean $T_{qS}$ obtained for the three maps was $6280\pm200$ K |
| SSC limb brightening 100 GHz (58" beam) | 10.5 | not stated | % | 5 | The convolution with a $58''$ Gaussian-beam resulted in limb intensities of 10.5% at 100 GHz and 13.3% at 230 GHz. |

## Qualitative findings

- South pole brighter than North in eight of nine maps, though differences are within the standard deviation  
  > "with larger brightness intensities at the South pole in eight of the nine maps analyzed" (abstract)

## Claim tuples

- H: Polar brightening exists at 100 and 230 GHz | E: Radial profiles of ALMA single-dish maps at polar position angles | R: Mean polar brightening 5-6% at 100 GHz and 9% at 230 GHz | F: Polar intensity exceeds disk intensity at both frequencies (lower limits) | **supported**
- H: Atmospheric models reproduce observed limb brightening | E: Compute FAL-C and SSC limb profiles convolved with ALMA beams | R: Both give larger limb intensities than observed; SSC closer | F: SSC better but still overpredicts, possibly due to spicules | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Sidelobes not removed so polar brightening is a lower limit; poor resolution  
  > "there should be non-zero sidelobes in a radio telescope beam. Therefore, the derived polar brightening should be a lower limit." (Discussion and conclusions)
- Caveat (inferred, ours): Large uncertainties; pole differences insignificant
- Caveat (inferred, ours): No sidelobe deconvolution
- Caveat (inferred, ours): Only nine maps at different times with varying T_qS

## Reproducibility

- Data public (paper): SV data released publicly in early 2017  
  > "released in the beginning of 2017" (ALMA solar maps)
- Products in archive: _not stated_
- Missing: Map file details and pixel scale
- Missing: Model atmosphere tables in numeric form
- Data volume (inferred): small, ~1 GB (nine single-dish maps)
- Score (inferred): 3/5, Data public and method simple, but several settings unstated and models require external tables.
- Rediscovery candidate: yes, Public SV maps, simple profile analysis and numeric results.

## Links

- Method: (cite: White2017) (Description of the ALMA SV solar maps and T_qS method)
- Companion: (cite: Alissandrakis2017) (Same data set, center-to-limb variation)
- Related: ALMA Science Verification solar observations

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
 "codes_not_in_obscore": [
  "2011.0.00020.SV"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 27,
  "rate": 0.386
 },
 "evidence_ok": true
}
```
