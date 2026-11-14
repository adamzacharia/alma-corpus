# Spiral Arms in the Disk of HD 142527 from CO Emission Lines with ALMA

`2014ApJ...785L..12C` | The Astrophysical Journal Letters 2014 | first author: Christiaens, V. | arXiv: 1403.1463 | DOI: 10.1088/2041-8205/785/1/L12

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: What is the morphology of the outer disk of HD 142527 in CO lines, and do spiral arms exist that could be due to embedded planets or other mechanisms?  
  > "This paper focuses on the morphology of the outer disk through ALMA observations of $^{12}$CO J=2-1, $^{12}$CO J=3-2 and $^{13}$CO J=2-1." (abstract)
- Target **HD 142527**: coordinates _not stated_; z/distance 145±15 pc  
  > "for a distance of 145$\pm$15 pc (cite: DeZeeuw1999; Acke2004)" (INTRODUCTION); distance from DeZeeuw1999; Acke2004  
  > "for a distance of 145$\pm$15 pc (cite: DeZeeuw1999; Acke2004)" (INTRODUCTION)

## Data provenance

- ALMA projects: 2011.0.00465.S
- bands: Band 6 (CO 2-1, 13CO 2-1) and Band 7 (CO 3-2)  
  > "respectively for bands 6 (CO 2-1 and $^{13}$CO 2-1) and 7 (CO 3-2)." (2.1 Datasets)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 21 to 379 m  
  > "with baselines comprised between 21 (resolution of $\sim$12.8$''$) and 379 m ($\sim$0.71$''$)." (2.1 Datasets)
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: June 2012 (Cycle 0)  
  > "The observations were obtained with ALMA on June 2012 (Cycle 0)" (2.1 Datasets)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (230.538 GHz)
- Line: 12CO J=3-2 (345.796 GHz)
- Line: 13CO J=2-1 (220.399 GHz)
- External data: LIME model of HD 142527 used for flux-loss estimate  
  > "a LIME (cite: Brinch2010) model of HD 142527 (cite: Perez2014)" (2.2 Moment Maps) [from Perez2014]
- External data: Gas temperature in the gap ~41-43 K  
  > "The gas temperature in the gap is $\sim$41-43 K (cite: Fukagawa2013; Perez2014)." (Physical Diagnostics in the Spiral Arms) [from Fukagawa2013; Perez2014]
- External data: Disk mass 0.1 Msun  
  > "the mass of the disk $M_d$ set to 0.1 $M_{\odot}$ (cite: Verhoeff2011)" (DISCUSSION: ORIGIN OF THE SPIRAL ARMS) [from Verhoeff2011]

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

- task: CASA clean (Cotton-Schwab)  
  > "Next, visibility data were *clean*ed (Cotton-Schwab `CLEAN`)." (2.1 Datasets)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "natural weighting was preferred over Briggs weighting" (2.1 Datasets)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: manual masks per channel at ~5 sigma  
  > "masks were drawn manually in the dirty maps for each velocity channel." (2.1 Datasets)
- multiscale scales: _not stated_
- continuum subtraction: in the visibility domain  
  > "The continuum was first subtracted in the visibility domain." (2.1 Datasets)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: channels binned to 0.2 km/s  
  > "We binned the original spectral channels to 0.2 km s$^{-1}$ bin-width." (2.1 Datasets)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Instrumental setup and calibration  
  > "For details on the instrumental setup and calibration we refer to (cite: Perez2014) and (cite: Casassus2013)" (2.1 Datasets) [from Perez2014 (Band 6); Casassus2013 (Band 7)]

### Not stated but needed to reproduce (our reading)

- Beam sizes and rms of final cubes
- Channel-mask thresholds in detail and line-free channels
- Calibrators and CASA version
- Spiral-tracing points and fit code details
- Velocity range used for I_peak maps

## Analysis recipe

1. **Image CO cubes**: Continuum subtraction, 0.2 km/s binning, natural-weighted CLEAN with manual masks  
  > "Next, visibility data were *clean*ed (Cotton-Schwab `CLEAN`)." (2.1 Datasets)
   - software: CASA
   - fitting: _not stated_
   - validation: Elliptical mask gave similar moment maps  
  > "an elliptical mask identical in all velocity channels, embracing the whole butterfly pattern, yielded similar moment maps." (2.1 Datasets)
2. **Compute moment maps**: Integrated intensity, peak intensity, centroid and dispersion; peak maps averaged over shifted binnings to remove segmentation  
  > "we computed two (resp. four) $I_\mathrm{peak}$ maps with the same velocity bin width (0.2 km s$^{-1}$), but shifted by half (resp. a quarter of) the bin width, and then averaged them." (2.2 Moment Maps)
   - parameter: Iint velocity range 2.6<vlsr<3.6 km/s  
  > "We restrict the velocity range to $2.6 < v_\mathrm{lsr} / \mathrm{km~s}^{-1} <3.6$" (2.2 Moment Maps)
   - fitting: _not stated_
   - validation: Flux loss estimated with LIME model, <=16%  
  > "yields flux losses $\lesssim$16%." (2.2 Moment Maps)
3. **Derive temperatures, scale heights, masses**: Brightness temperature from peak intensity assuming optically thick 12CO; LTE excitation temperature from the 2-1/3-2 ratio; power-law fit of T(r); scale height H=cs/Omega; LTE mass lower limits  
  > "Assuming that $^{12}$CO is optically thick, the peak intensities provide brightness temperatures" (Physical Diagnostics in the Spiral Arms)
   - assumption: [H2]/[CO] = 10^4; mu~2.3; Keplerian rotation  
  > "assuming \[H$_2$\]/\[CO\] = 10$^4$" (Physical Diagnostics in the Spiral Arms)
   - fitting: T∝r^-q fit  
  > "the best fit to the law $T \propto r^{-q}$ yields $q$$\sim$0.5-0.6." (Physical Diagnostics in the Spiral Arms)
   - validation: _not stated_
4. **Model spiral arms**: Least-squares fits of traced spiral points with Muto2012 and Kim2011 formulae  
  > "We then perform least-squares fits to each spiral independently using two different parametric formulae" (Modelling of the Spiral Arms)
   - parameter: alpha=1.5, beta=0.25, h_c=0.15 fixed  
  > "a second set of fits was run fixing as well the value of $h_c$ to 0.15." (Modelling of the Spiral Arms)
   - fitting: Least squares; errors max{bin size, quarter beam}  
  > "Uncertainties in the measured positions of the spirals were set to max{bin size, quarter of the beam size}." (Modelling of the Spiral Arms)
   - validation: chi2 used only to compare models  
  > "we use $\chi^2$ to compare different models rather than assess their statistical significance." (Modelling of the Spiral Arms)

## Software

- **CASA** : Spectral line imaging  
  > "Spectral line imaging was achieved with the `CASA` package." (2.1 Datasets)
- **LIME** : Model to estimate flux loss  
  > "a LIME (cite: Brinch2010) model of HD 142527" (2.2 Moment Maps)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Excitation temperature S2 | 13-15 | not stated | K | 3 | $T_{ex,S2}$$\sim$13-15 K |
| Temperature power-law index q | 0.5-0.6 | not stated | dimensionless | 3 | yields $q$$\sim$0.5-0.6 |
| Aspect ratio at spirals | 0.12-0.13 | not stated | dimensionless | 3 | hence a disk aspect ratio $h_S$$\sim$0.12-0.13 |
| Gas mass lower limit S1 | 1.38e-6 | not stated | Msun | 3 | $M_{S1} \gtrsim 1.38
\times 10^{-6} M_{\odot}$ |
| Toomre Q | ~2.0 | not stated | dimensionless | 0 | we find $Q$$\sim$2.0 similarly to (cite: Fukagawa2013) |

## Qualitative findings

- S2 is a newly detected outer spiral and S3 a faint counterarm; S1 is the radio counterpart of the NIR spiral  
  > "However, the most conspicuous CO spiral arm (S2) lies at the outskirts of the disk and had not been detected before." (abstract)

## Claim tuples

- H: Are there CO spiral arms in the outer disk? | E: Peak-intensity and integrated maps of CO 2-1 and 3-2 | R: Three spirals S1, S2, S3 detected | F: Spirals exist, S2 and S3 newly found | **supported**
- H: Can the spirals be explained by embedded planets? | E: Least-squares fits with Muto2012 and Kim2011 formulae | R: S1 fit well, S2 and S3 poorly | F: S1 consistent with a planet; S2 and S3 likely have other causes | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Tidal interaction and gravitational instability considered for S2 and S3; no companion detected, disk stable but close to instability  
  > "For HD 142527 no such object has been detected." (DISCUSSION: ORIGIN OF THE SPIRAL ARMS)
- How they decided it was enough: _not stated_
- Limitation (authors): Chi2 depends on non-independent error bars; fits degenerate with h_c  
  > "Since $\chi^2$ depends on the estimated error bars, which are not independently determined" (Modelling of the Spiral Arms)
- Caveat (inferred, ours): Spiral tracing uses few points with ad hoc errors
- Caveat (inferred, ours): Fits degenerate and no formal significance
- Caveat (inferred, ours): Temperature from optically thick assumption and intervening cloud absorption

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Calibration details deferred to Perez2014 and Casassus2013
- Missing: Exact masks and traced points
- Data volume (inferred): ~50-100 GB
- Score (inferred): 3/5, Data archival and imaging recipe summarized, but calibration is deferred and mask and fit details are missing.
- Rediscovery candidate: no, Calibration is inherited and manual masking and spiral tracing are not fully specified.

## Links

- Method: Muto2012 (Spiral formula)
- Method: Kim2011 (Archimedean spiral formula)
- Companion: Perez2014 (Band 6 setup and disk model)
- Companion: Casassus2013 (Band 7 data and calibration)

## Checks

```json
{
 "quotes": 44,
 "quotes_ok": 44,
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
  "facts": 67,
  "stated": 32,
  "rate": 0.478
 },
 "evidence_ok": true
}
```
