# ALMA photometry of extragalactic radio sources

`2019MNRAS.485.1188B` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Bonato, M. | arXiv: 1901.08976 | DOI: 10.1093/mnras/stz465

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type data_release_or_catalog

## Science

- Fields: agn_and_quasars, cosmology
- Question: Can ALMA calibrator photometry validate the Planck PCNT photometry, positions and completeness, and be used to extrapolate 100 GHz radio source counts to higher ALMA bands?  
  > "We have exploited the ALMA data to validate the photometry given in the new *Planck* Multi-frequency Catalogue of Non-thermal sources (PCNT), for which an external validation was not possible so far." (abstract)
- Target **3,364 ALMA calibrators (mostly blazars)**: coordinates equatorial J2000 coordinates given in the catalogue  
  > "Almost all sources ($\sim$97%) were found to be blazars." (1 Introduction); z/distance redshifts from literature for 2245 sources (67%)  
  > "Almost all sources ($\sim$97%) were found to be blazars." (1 Introduction); distance from literature search  
  > "Almost all sources ($\sim$97%) were found to be blazars." (1 Introduction)

## Data provenance

- ALMA projects: _none stated_
- bands: Bands 3, 4, 6, 7, 8, 9, 10  
  > "25,907 observations of 3,310 different sources in band 3 (84$-$116 GHz), 671 observations of 171 sources in band 4 (125$-$163 GHz)" (Introduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: May 2011 to July 2018  
  > "These sources were observed between May 2011 and July 2018, for a total of 47,115 pointings in different bands and epochs." (abstract)
- pi or archival as stated: _not stated_
- Other facility **Planck (PCNT, PCCS2)**: Flux densities and positions of counterparts for validation  
  > "we cross-matched the ACC with the PCNT outside the GAL070 mask" (2 Validation)
- Other facility **Herschel H-ATLAS**: PCCS2 completeness limits at 857 GHz  
  > "These authors found PCCS2 90% completeness limits of $S_{\rm Herschel}=650\,$mJy at 857 GHz" (2 Validation)
- External data: ALMACAL catalogue of 754 calibrators, 16,263 observations  
  > "have published a catalogue of ALMA flux density measurements of 754 calibrators for a total of 16,263 observations in different bands and epochs (ALMACAL catalogue)." (Introduction) [from (cite: Bonato2018)]
- External data: ALMA Calibrator Source Catalogue (ACSC) flux densities  
  > "Combining such catalogue with the “ALMA Calibrator Source Catalogue” (ACSC)" (Introduction) [from ACSC, almascience.eso.org/sc]
- External data: Classifications from Roma Multi-frequency Catalogue of Blazars  
  > "About 41% (1391) of our sources are listed in the 5th edition of the Roma Multi-frequency Catalogue of Blazars" (Introduction) [from (cite: Massaro2009)]
- External data: 100 GHz Euclidean counts from Planck and SPT  
  > "The combination of *Planck* (cite: PCNT) and SPT (cite: Mocanu2013) data has provided an observational determination of radio source number counts" (3 High frequency number counts) [from (cite: PCNT), (cite: Mocanu2013)]
- Simulation/model as data: Tucci et al. models C2Co and C2Ex for comparison of counts  
  > "The comparison with the two preferred models by (cite: Tucci2011), “C2Co” and “C2Ex”" (3 High frequency number counts)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 5% for ALMACAL sources; ACSC quoted uncertainties adopted  
  > "Following (cite: Bonato2018) we adopt at 5% calibration uncertainty for ALMACAL sources." (Introduction)
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

- ALMACAL calibration and imaging analysis  
  > "The calibration and imaging analyses are described in (cite: Bonato2018)." (Introduction) [from (cite: Bonato2018)]
- Classification of sources not in Roma-BZCAT  
  > "We have classified the remaining objects following (cite: Bonato2018)." (Introduction) [from (cite: Bonato2018)]

### Not stated but needed to reproduce (our reading)

- ACSC measurement procedure and raw flux values
- How ACSC and ALMACAL entries were merged/duplicates handled
- How characteristic band frequencies (e.g. 95 GHz) were derived
- Cross-match procedure details beyond the 3 arcmin radius
- Binning used for validation and completeness plots
- Method for fitting polynomial representations of counts

## Analysis recipe

1. **Build ALMA Calibrator Catalogue**: Combine ALMACAL catalogue with ACSC; add redshifts and classification  
  > "Combining such catalogue with the “ALMA Calibrator Source Catalogue” (ACSC)[^2], we have collected ALMA observations for 3,364 bright, (mostly) compact radio sources." (Introduction)
   - parameter: ACSC uncertainties adopted after median absolute differences of 6% (Bands 3, 6) and 8% (Band 7) within 30 d  
  > "We have therefore adopted the ACSC uncertainties." (Introduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Cross-match with PCNT and compare photometry**: Cross-match within 3 arcmin outside GAL070 mask; compare mean ALMA flux densities with MTFX photometry, frequency-shifted with fixed spectral indices  
  > "The comparison with PCNT flux densities was made using the mean values and adopting the standard deviation, summed in quadrature with the calibration uncertainty, as an estimate of the uncertainty." (2 Validation)
   - parameter: Band 7 to 353 GHz with S∝ν^-0.45; Bands 8/9 to 545 GHz with S∝ν^-0.62  
  > "Band 7 flux densities were converted to 353 GHz with $S\propto \nu^{-0.45}$" (2 Validation)
   - fitting: _not stated_
   - validation: Expected spurious associations about 1 (0.1%)  
  > "Thus the expected number of spurious associations is $\simeq 1$, i.e. $\simeq 0.1\%$ of *Planck* counterparts." (2 Validation)
3. **Assess PCNT completeness**: Fraction of ACC objects with PCNT counterparts (SNR>=3) versus ALMA flux density; 10,000 Gaussian simulations for 143 GHz  
  > "we have performed 10,000 simulations of *Planck* observations of the 100 ALMA calibrators." (2 Validation)
   - fitting: _not stated_
   - validation: Compared with PCCS2 90% completeness limits  
  > "At 100, 217, 353 and 545 GHz our results are in excellent agreement with the estimates of the 90% completeness limits given by (cite: PCCS2)." (2 Validation)
4. **Extrapolate 100 GHz counts to higher bands**: Convolve the 100 GHz counts polynomial with Gaussian distribution of log(S95/Sν) from ALMA band ratios  
  > "By convolving eq. ([\[eq:100GHzcounts\]](#eq:100GHzcounts)) with the appropriate distribution of flux density ratios, assumed to be a Gaussian" (3 High frequency number counts)
   - assumption: Flux density ratio distribution is Gaussian  
  > "assumed to be a Gaussian with mean and standard deviation given by Table" (3 High frequency number counts)
   - fitting: _not stated_
   - validation: Compared to available data and Tucci et al. models C2Co, C2Ex  
  > "The extrapolated counts are fully consistent with the available data." (3 High frequency number counts)

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA-Planck position offset peak | 0.38 | not stated | arcmin | 2 | The positional differences peak at $\sim0'.38$ and have a standard deviation $\sigma \simeq 0'.64$. |
| ALMA-Planck position offset standard deviation | 0.64 | not stated | arcmin | 2 | The positional differences peak at $\sim0'.38$ and have a standard deviation $\sigma \simeq 0'.64$. |
| Unique Planck counterparts with SNR>=3 | 1120 of 3364 | not stated | sources | 2 | We found unique *Planck* counterparts with $\hbox{SNR}\ge 3$ for 1,120 out of the 3,364 ALMA calibrators. |
| PCNT 90% completeness at 100/143/217/353/545 GHz | 266/312/170/296/597 | not stated | mJy | 3 | / 100 / 269 / 266 / 562 / |
| Mean log(S95/Sν) band 6 (233 GHz) | 0.25 | sigma 0.14 | dimensionless | 4 | / 6 / 233 / 859 / 0.25 / 0.14 / |
| Mean log(S95/Sν) band 7 (285 GHz) | 0.37 | sigma 0.17 | dimensionless | 4 | / 7 / 285 / 2102 / 0.37 / 0.17 / |

## Qualitative findings

- Good consistency of MTFX and ALMA photometry above PCCS2 90% completeness limits; Eddington bias below  
  > "Above the PCCS2 90% completeness limits (vertical dotted red lines) we find good consistency between the MTFX and the ALMA photometry." (2 Validation)

## Claim tuples

- H: PCNT MTFX photometry is consistent with ALMA photometry | E: Cross-match ACC with PCNT and compare flux densities | R: Good agreement above PCCS2 90% completeness limits; dispersion about 0.2 dex ascribed to variability | F: MTFX photometry validated externally | **supported**
- H: PCNT completeness limits differ from PCCS2 | E: Fraction of ACC sources with PCNT counterparts versus flux | R: Consistent at 100, 217, 353, 545 GHz; higher at 143 GHz but marginal | F: Completeness limits essentially unchanged | **supported**
- H: Extrapolated high-frequency counts discriminate between Tucci models | E: Convolve 100 GHz counts with ALMA band ratio distributions | R: C2Ex agrees; C2Co overpredicts above 145 GHz | F: C2Ex favoured, C2Co disfavoured | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Planck and ALMA data are non-simultaneous so blazar variability adds dispersion  
  > "Blazars are known to be strongly variable and *Planck* and ALMA measurements are non-simultaneous." (Footnote 5)
- Caveat (inferred, ours): Calibrator sample is flux-biased and not a complete survey, which may bias band ratios
- Caveat (inferred, ours): Non-simultaneous observations with variable sources
- Caveat (inferred, ours): Gaussian assumption for ratios and a single spectral index for extrapolation

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: Catalogue available online as supplementary material and on Italian ARC website  
  > "The catalogue is available online as supplementary material and on the website of the Italian ALMA Regional Center (ARC; <http://arc.ia2.inaf.it>)." (Conclusions)
- Missing: Original flux measurement pipeline lives in Bonato2018
- Missing: PCNT catalogue needed
- Missing: No code or scripts released
- Data volume (inferred): Small: catalogue tables only (MB) if using released ACC; raw ALMA calibrator data would be very large
- Score (inferred): 3/5, Catalogue-level analysis is simple and data are public, but ACC construction and many details rely on other papers and no code is given.
- Rediscovery candidate: no, Underlying catalogues are inherited from other works and the statistical procedures are only briefly described, although results are numeric.

## Links

- Method: (cite: Bonato2018) (ALMACAL calibration, imaging and classification)
- Method: (cite: Herranz2008; Herranz2009) (MTFX photometry method)
- Companion: (cite: PCNT) (Planck catalogue being validated)
- Related: ALMACAL
- Related: Planck PCCS2
- Related: PCNT
- Related: ALMA Calibrator Source Catalogue

## Checks

```json
{
 "quotes": 39,
 "quotes_ok": 39,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2011.0.00001.CAL"
 ],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 29,
  "rate": 0.42
 },
 "evidence_ok": true
}
```
