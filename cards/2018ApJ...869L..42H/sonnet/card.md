# The Disk Substructures at High Angular Resolution Project (DSHARP). II. Characteristics of Annular Substructures

`2018ApJ...869L..42H` | The Astrophysical Journal Letters 2018 | first author: Huang, Jane | arXiv: 1812.04041 | DOI: 10.3847/2041-8213/aaf740

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: protoplanetary_disks
- Question: What are the locations, widths, contrasts and trends of annular substructures in the DSHARP 1.25 mm continuum images of 18 single disks, and what do they imply for their origin (planets, snowlines, etc.)?  
  > "We present a systematic analysis of annular substructures in the 18 single-disk systems targeted in this survey." (abstract)
- Target **DSHARP single-disk sample (18 disks, e.g. AS 209, HD 163296, Elias 24, HD 143006)**: coordinates _not stated_; z/distance see Table 1 of Andrews et al. 2018 (not reproduced here)  
  > "DSHARP targeted 20 systems, 18 of which are single-disk systems (i.e., all sources except AS 205 and HT Lup)." (2 Sample overview); "Stellar properties, including distances, masses, accretion rates, ages, and luminosities, are listed in Table 1 of (cite: 2018ApJ...869L..41A)." (2 Sample overview); distance from Gaia  
  > "DSHARP targeted 20 systems, 18 of which are single-disk systems (i.e., all sources except AS 205 and HT Lup)." (2 Sample overview); "Stellar properties, including distances, masses, accretion rates, ages, and luminosities, are listed in Table 1 of (cite: 2018ApJ...869L..41A)." (2 Sample overview)
- Target **TW Hya and HL Tau (comparison, public 1.0 mm data)**: coordinates _not stated_; z/distance TW Hya 60 pc; HL Tau 147 pc  
  > "The distance to TW Hya is 60 pc (cite: 2016AA...595A...2G)" (3.1 Radial locations); "adjusted for the new distance estimate of 147 pc from (cite: 2018ApJ...859...33G)" (3.1 Radial locations); distance from Gaia (TW Hya); Galli et al. 2018 (HL Tau)  
  > "The distance to TW Hya is 60 pc (cite: 2016AA...595A...2G)" (3.1 Radial locations); "adjusted for the new distance estimate of 147 pc from (cite: 2018ApJ...859...33G)" (3.1 Radial locations)

## Data provenance

- ALMA projects: _none stated_
- bands: 1.25 mm continuum (DSHARP fiducial images)  
  > "used ALMA to map the 1.25 millimeter continuum of protoplanetary disks at a spatial resolution of $\sim5$ au" (abstract)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~30 to 60 mas, ~5 to 8 au  
  > "Angular resolutions range from $\sim30$ to 60 mas, probing scales of $\sim5$ to 8 au." (2 Sample overview)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- External data: DSHARP fiducial 1.25 mm images, stellar properties (Table 1) and beam/rms information (Table 4)  
  > "The analysis in this work is based on the “fiducial” images presented in (cite: 2018ApJ...869L..41A)" (2 Sample overview) [from (cite: 2018ApJ...869L..41A)]
- External data: TW Hya 1.0 mm (290 GHz) image  
  > "The TW Hya analysis uses the 1.0 mm image presented in (cite: 2018ApJ...852..122H)" (2 Sample overview) [from (cite: 2018ApJ...852..122H)]
- External data: HL Tau 1.0 mm image and substructure positions (Table 2), rescaled to 147 pc  
  > "the HL Tau analysis uses the 1.0 mm image presented in (cite: 2015ApJ...808L...3A)" (2 Sample overview) [from (cite: 2015ApJ...808L...3A)]
- External data: Binding energies for CO, N2 and CO2 used for freezeout temperatures  
  > "(4) Reference for $E_b$ value." (Table 3 notes) [from (cite: 2016ApJ...816L..28F); (cite: 2014AA...564A...8M)]

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

- Observational setup, calibration and imaging of the fiducial images  
  > "which also provides details about the observational setup and the calibration and imaging procedure." (2 Sample overview) [from (cite: 2018ApJ...869L..41A)]
- Ring position measurement approach  
  > "The positions of such distinct substructures are measured in a manner similar to that employed for the HL Tau disk in (cite: 2015ApJ...808L...3A)." (3.1 Radial locations) [from (cite: 2015ApJ...808L...3A)]
- Curve-of-growth dust radius method  
  > "using a “curve-of-growth”-type method similar to that described in (cite: 2016ApJ...828...46A)" (3.3 Dust disk radii) [from (cite: 2016ApJ...828...46A)]
- phi=0.02 flaring angle consistent with Dullemond et al.  
  > "The value of $\varphi$ is also chosen to be consistent with the analysis of a subset of the DSHARP sources in (cite: 2018ApJ...869L..46D)" (3.5 Continuum optical depths) [from (cite: 2018ApJ...869L..46D)]

### Not stated but needed to reproduce (our reading)

- Project codes, observing dates and array configurations (only in Paper I)
- Exact image files/pixel size and any primary-beam handling
- Exact initial guesses/Gaussian prior widths for cos i and PA of AS 209, Elias 24, Sz 114, GW Lup
- Search windows and chosen azimuthal spacing per ring
- KDE bandwidth values
- Stellar luminosities per source (from Paper I)

## Analysis recipe

1. **Fit ellipses to ring/gap extrema**: Deproject roughly, find radial extrema along azimuthal cuts, fit 5-parameter ellipse by MCMC  
  > "An ellipse is then fit to the $n$ coordinates extracted for a given annular substructure." (3.1 Radial locations)
   - software: emcee
   - parameter: 30 walkers, 20,000 steps, 500 burn-in; uniform priors on dx, dy, r0 (-4.5",4.5"), ln sigma^2 (-15,-5)  
  > "Each ensemble consists of 30 walkers and proceeds for 20,000 steps, with the first 500 steps discarded as burn-in." (3.1 Radial locations)
   - fitting: Gaussian log-likelihood on orthogonal distances with free ln sigma^2; affine-invariant sampler  
  > "we allow $\ln \sigma^2$ to be a free parameter." (3.1 Radial locations)
   - validation: Autocorrelation time (~10^2) much less than steps; ellipse positions checked against radial profile positions  
  > "Convergence of the MCMC chains is assessed by checking that the number of steps significantly exceeds the autocorrelation time" (3.1 Radial locations)
2. **Deprojected radial profiles and additional extrema**: Deproject using weighted ellipse fits or imfit 2D Gaussians, bin in 1 au annuli, find extrema/plateaus  
  > "binning the pixels in annuli one au wide, and averaging the intensities in each bin." (3.1 Radial locations)
   - software: CASA
   - fitting: _not stated_
   - validation: Gaussian and ellipse-fit geometries agree within one degree  
  > "find that the results generally agree with those from ellipse-fitting within one degree." (3.1 Radial locations)
3. **Measure widths and gap depths**: Gap depth I_d/I_b; widths from half-way intensity I_mean=0.5(I_d+I_b) on profiles interpolated to 0.1 au  
  > "The dividing point between the outer edge of a gap and the inner edge of its immediate exterior ring is defined as the radius $r_{d,o}$" (3.2 Widths and contrasts)
   - fitting: _not stated_
   - validation: _not stated_
4. **Dust disk radius and optical depth**: Curve of growth R_dust enclosing 95% flux; tau from I=B(T_mid)(1-exp(-tau)) with passive flared disk temperature  
  > "$R_\text{dust}$ is defined to be the radius at which the enclosed flux is equal to 95$\%$ of the total flux." (3.3 Dust disk radii)
   - parameter: phi = 0.02 (0.05 for RU Lup)  
  > "we select a somewhat conservative value of $\varphi=0.02$." (3.5 Continuum optical depths)
   - assumption: Midplane T from stellar luminosity, flaring angle phi, radiative equilibrium; optical depths may be off by factor of two  
  > "the optical depth estimates may be up to a factor of two off from the true optical depths" (3.5 Continuum optical depths)
   - fitting: _not stated_
   - validation: _not stated_
5. **Aggregate radial, resonance, snowline and stellar-parameter analysis**: Histograms and Gaussian KDE (leave-one-out bandwidth), radius ratios vs mean-motion resonances within 1%, freezeout temperature shading  
  > "The bandwidth is optimized through leave-one-out cross-validation" (4.1)
   - software: scikit-learn
   - assumption: Keplerian rotation, small disk mass; q = 0.5 for snowline ratios  
  > "Using a representative value of $q = 0.5$" (4.3)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **emcee** : MCMC ellipse fitting  
  > "The posteriors are explored with the affine invariant MCMC sampler implemented in `emcee`" (3.1 Radial locations)
- **CASA** : imfit 2D Gaussian fits for disk geometry  
  > "with the `imfit` task in `CASA`" (3.1 Radial locations)
- **scikit-learn** : Gaussian kernel density estimation  
  > "We also use the `scikit-learn` implementation of Gaussian kernel density estimation" (4.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HD 143006 B65:B41 radius ratio | 1.591 | 0.011 | dimensionless | 5 | / 2:1 / 1.587 / HD 143006 / B65:B41 / $1.591\pm0.011$ / |
| AS 209 inclination | 34.97 | 0.13 | deg | 1 | / AS 209 / $1.9\pm0.5$ / $-2.5\pm0.5$ / $34.97\pm0.13$ / $85.76\pm0.16$ / E / $139\pm1$ / 4.4 / |
| AS 209 dust radius | 139 | 1 | au | 4 | / AS 209 / $1.9\pm0.5$ / $-2.5\pm0.5$ / $34.97\pm0.13$ / $85.76\pm0.16$ / E / $139\pm1$ / 4.4 / |
| Typical ring optical depth | 0.3 to 0.6 | not stated | dimensionless | 4 | the estimated optical depths at the bright rings in the DSHARP sources typically range from 0.3 to 0.6. |

## Qualitative findings

- Substructure morphologies are diverse with no dominant architecture; most widths <10 au  
  > "No dominant architecture emerges from this sample; instead, remarkably diverse morphologies are observed." (abstract)
- No clear trend of substructure positions with stellar properties or snowline temperatures  
  > "suggests that substructures do not occur preferentially near major molecular snowlines." (abstract)

## Claim tuples

- H: Do annular substructures preferentially trace molecular snowlines? | E: Compared normalized intensity profiles vs midplane temperature and radius ratios to snowline predictions | R: No strong correspondence between temperature and positions; few pairs have snowline ratios | F: Most substructures are unlikely to trace snowlines | **supported**
- H: Are substructure spacings clustered at mean-motion resonances? | E: Radius ratios of substructure pairs compared to low-order resonances | R: No significant clustering, some candidate pairs (e.g. HD 143006 B65:B41) | F: No general resonance clustering; a few suggestive cases | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Empirical width/depth definitions used because initial surface density is unknown for observations  
  > "we take a more empirical approach and define width and depth without assuming a functional form for the substructures or an initial surface density." (3.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Width and depth definitions ignore beam effects; narrow features are bounds  
  > "First, the effects of the beam are not accounted for." (3.2)
- Limitation (authors): Selection bias toward bright, large disks  
  > "could be a consequence of the selection for bright continuum sources" (4.4)
- Caveat (inferred, ours): Optical depths rely on a single assumed flaring angle and temperature law
- Caveat (inferred, ours): Ring locations depend on subjective search windows and plateau identification
- Caveat (inferred, ours): Resonance matches may be coincidental given many features

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Image files and project codes (in Paper I)
- Missing: Per-source prior widths and search windows
- Missing: Stellar luminosities and distances table
- Data volume (inferred): Fiducial images small (~GB); raw data from 9 projects tens to hundreds of GB
- Score (inferred): 3/5, Methods are well described but depend on Paper I images and several unstated per-source choices.
- Rediscovery candidate: no, Depends on DSHARP images and per-source choices not fully given; many results are qualitative.

## Links

- Method: (cite: 2018ApJ...869L..41A) (DSHARP data, calibration and imaging)
- Method: (cite: 2015ApJ...808L...3A) (Ring position method and naming for HL Tau)
- Companion: (cite: 2018ApJ...869L..46D) (Gaussian ring modeling, dust trapping)
- Companion: (cite: 2018ApJ...869L..47Z) (Planet mass estimates from gaps)
- Companion: (cite: 2018ApJ...869L..43H) (Spiral arms)
- Related: DSHARP
- Related: Lupus ALMA survey
- Related: ODISEA

## Checks

```json
{
 "quotes": 46,
 "quotes_ok": 46,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2013.1.00226.S",
  "2013.1.00366.S",
  "2013.1.00498.S",
  "2013.1.00601.S",
  "2013.1.00694.S",
  "2013.1.00798.S",
  "2015.1.00486.S",
  "2015.1.00964.S",
  "2016.1.00484.L"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 35,
  "rate": 0.438
 },
 "evidence_ok": true
}
```
