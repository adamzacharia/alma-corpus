# The evolution of the internal structure of massive star-forming regions in the Milky Way as revealed by ALMA

`2023MNRAS.524.1625D` | Monthly Notices of the Royal Astronomical Society 2023 | first author: Dib, Sami | arXiv: 2209.12905 | DOI: 10.1093/mnras/stad1904

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: star_formation, milky_way_ism
- Question: Whether the internal structure of protocluster clouds, quantified by the delta-variance spectrum of 1.3 mm continuum maps, relates to their evolutionary stage  
  > "we explore if and how features in the spectra relate to the clouds’ evolutionary stages." (INTRODUCTION)
- Target **15 ALMA-IMF protocluster clouds (e.g. W43-MM1, W43-MM2, W43-MM3, W51-E, W51-IRS2, G333.60, G012.80)**: coordinates _not stated_; z/distance ≈2 kpc to 5.5 kpc  
  > "The sample consists of $15$ massive star forming regions located a distances between $\approx 2$ kpc to $5.5$ kpc and that are in different evolutionary stages." (2 DATA); distance from Motte et al. (2022)  
  > "The sample consists of $15$ massive star forming regions located a distances between $\approx 2$ kpc to $5.5$ kpc and that are in different evolutionary stages." (2 DATA)

## Data provenance

- ALMA projects: _none stated_
- bands: 1.3 mm (and 3 mm for flux ratios)  
  > "two versions of a $1.3$ mm and a $3$ mm continuum maps which were obtained using the 12m array configuration of ALMA" (2 DATA)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12m array (7m exists but not used)  
  > "two versions of a $1.3$ mm and a $3$ mm continuum maps which were obtained using the 12m array configuration of ALMA" (2 DATA)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1350 to 2690 au  
  > "the spatial resolution varies from region to region and is in the range of $1350$ to $2690$ au" (2 DATA)
- max recoverable scale: likely 5'' to 12''  
  > "the MRS for these fields are likely to be somewhere between $5\ensuremath{''}$ to $12\ensuremath{''}$." (4 RESULTS)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: H41α recombination line (used by Motte et al. for free-free estimate) (not stated)
- External data: S1.3mm/S3mm flux ratios and H41α free-free surface densities for each cloud, and evolutionary classification  
  > "lists the values of $\left(S_{\rm 1.3 mm}^{\rm cloud}/S_{\rm 3 mm}^{\rm cloud}\right)$ and $\Sigma_{\rm H41\alpha}^{\rm free-free}$ measured by Motte et al. (2022)." (2 DATA) [from Motte et al. 2022 (cite: motte22)]
- External data: Cloud distances  
  > "the distances of the regions that are reported in Motte et al. (2022)" (4 RESULTS) [from Motte et al. 2022 (cite: motte22)]
- Simulation/model as data: Idealized fBm (beta=2.4, 1000x1000 pixels) with 2D Gaussian clumps for testing detectability of dimmed structures  
  > "we assume a $1000\times1000$ pixels fBm with an exponent of $\beta=2.4$" (Appendix A)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: ALMA-IMF delivered cleanest image.tt0.pbcor maps used  
  > "we will focus the analysis on the cleanest $1.3$ mm maps (the image.tt0.pbcor versions)" (2 DATA)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: 882x882 to 2048x2048 pixels  
  > "varies from $882\times882$ pixels up to $2048\times2048$ pixels" (2 DATA)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: cleanest maps built from line-free channels (by ALMA-IMF)  
  > "The second type of maps (cleanest) are built using the line-free channels." (2 DATA)
- line free channels: _not stated_
- primary beam correction: pbcor maps used  
  > "the image.tt0.pbcor versions" (2 DATA)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Map production, MRS discussion and 12m+7m combination issues  
  > "We refer the reader to the original paper by Ginsburg et al. (2022) for a detailed discussion on what could affect the value of the MRS" (4 RESULTS) [from Ginsburg et al. (2022) (cite: ginsburg22)]
- Delta-variance implementation  
  > "we used an improved implementation of the method presented in Ossenkopf et al. (2008a)" (3 ANALYSIS) [from Ossenkopf et al. (2008a)]
- Evolutionary classification Young/Intermediate/Evolved  
  > "following the classification by Motte et al. (2022)" (4 RESULTS) [from Motte et al. (2022)]

### Not stated but needed to reproduce (our reading)

- ALMA project codes and exact map file names/versions
- Pixel scale and distance values used to convert to au
- Exact points used in quadratic interpolation of the peak
- Power-law fit procedure and uncertainties on alpha
- Range of scales and number of lags in delta-variance computation
- Treatment of noise/edges/masking in the maps

## Analysis recipe

1. **Compute delta-variance spectra**: Delta-variance with Mexican-hat filter computed in Fourier space on each 1.3 mm map; spectra normalized by mean  
  > "the calculation is performed as a multiplication in Fourier space (Ossenkopf et al. 2008a)" (3 ANALYSIS)
   - software: Ossenkopf et al. delta-variance code
   - parameter: filter diameter ratio v = 1.5  
  > "we used a value of $v=1.5$" (3 ANALYSIS)
   - fitting: _not stated_
   - validation: Idealized fBm plus Gaussian clump tests  
  > "we present a suite of simple and idealized tests" (Appendix A)
2. **Fit self-similar slope alpha**: Power-law fit over conservative scale ranges avoiding beam-smearing and bump  
  > "We adopted a conservative approach and fit the spatial ranges of the spectra that display a clear self-similar regime, avoiding perturbed scales at both ends." (4 RESULTS)
   - fitting: _not stated_
   - validation: Shifting fit range bounds by 1000 au gives identical exponents within 1 sigma  
  > "shifting the lower and upper bound of the range by 1000 au to larger scales, individually or simultaneously" (4 RESULTS)
3. **Measure bump scale L_hub**: Quadratic interpolation around spectrum peak  
  > "we derived a more accurate estimate of its value with a simple quadratic interpolation using several points around the peak" (4 RESULTS)
   - fitting: _not stated_
   - validation: Compared with assumed MRS of 5, 8, 12 arcsec; 12m vs 12m+7m comparison for G328.25  
  > "the position of the peak is roughly the same in both cases and it only shifts by about $50\%$ to larger values" (Appendix B)
4. **Correlate alpha and L_hub with evolutionary indicators**: Spearman rank correlation with Motte et al. flux ratio and free-free surface density, excluding G328.25  
  > "we have again excluded the G328.25 region as its measured value of $L_{\rm hub}$ is very close to the resolution limit." (4 RESULTS)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **Delta-variance code of Ossenkopf et al. 2008a** : computing delta-variance spectra  
  > "we used an improved implementation of the method presented in Ossenkopf et al. (2008a)" (3 ANALYSIS)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| L_hub range | ≈7000 to 60000 | not stated | au | 3 | falls in the range of $\approx 7000$ au to $60000$ au |
| Spearman rho, L_hub vs S1.3/S3 | -0.62 | significance of deviation from zero 0.012 | dimensionless | 4 | Spearman $\rho$ coefficient of $-0.62$ with a significance for the deviation from zero of $0.012$ |
| Spearman rho, L_hub vs Sigma_H41a | 0.53 | significance 0.03 | dimensionless | 4 | Spearman $\rho$ coefficient of $0.53$ and a significance of deviation from zero of $0.03$ |
| Spearman rho, alpha vs S1.3/S3 | 0.16 | significance 0.56 | dimensionless | 4 | (Spearman $\rho$ coefficient of 0.16) |
| Spearman rho, alpha vs Sigma_H41a | 0.10 | significance 0.73 | dimensionless | 4 | (Spearman $\rho$ coefficient of 0.10) |

## Qualitative findings

- All spectra deviate from a single power law and show a bump; more evolved clouds have bumps at larger scales  
  > "the peaks of the spectra are present at larger physical scales that those found in the less evolved, young regions" (4 RESULTS)

## Claim tuples

- H: Does the size of the densest region depend on evolutionary stage? | E: Delta-variance of 15 ALMA-IMF 1.3 mm maps correlated with evolutionary indicators | R: L_hub anti-correlates with flux ratio and correlates with free-free surface density | F: Larger clumps are more evolved; gravity regulates growth with ongoing accretion | **supported**
- H: Is the self-similar slope set by turbulent cascade alone? | E: Compare alpha with evolutionary indicators | R: No correlation, large scatter | F: Gravity-driven turbulence and feedback contribute | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): 12m-only maps filter large-scale emission; MRS uncertain and 12m+7m combination available for one region only  
  > "some of the emission at the largest scales can be filtered out" (4 RESULTS)
- Caveat (inferred, ours): Only 14 points in correlations; no uncertainties on L_hub propagated
- Caveat (inferred, ours): Evolutionary indicators and L_hub both may depend on distance/resolution
- Caveat (inferred, ours): L_hub may be affected by interferometric filtering

## Reproducibility

- Data public (paper): ALMA-IMF products public via project website; paper's own data on request  
  > "The data underlying this article will be available upon reasonable request." (Data availability)
- Products in archive: _not stated_
- Missing: Exact fit settings and interpolation points
- Missing: Project codes not printed
- Data volume (inferred): ~1 GB (15 continuum maps)
- Score (inferred): 3/5, Public maps and simple method but parameters for fits and peak finding are underspecified.
- Rediscovery candidate: yes, Public ALMA-IMF maps, simple method, numeric table of L_hub and correlations.

## Links

- Method: Ossenkopf et al. 2008a (delta-variance implementation)
- Method: Stutzki et al. 1998 (delta-variance technique)
- Companion: Motte et al. 2022 (cite: motte22) (ALMA-IMF overview, flux ratios, classification)
- Companion: Ginsburg et al. 2022 (cite: ginsburg22) (ALMA-IMF data products)
- Related: ALMA-IMF

## Checks

```json
{
 "quotes": 38,
 "quotes_ok": 38,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2013.1.01365.S",
  "2017.1.01355.L"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 65,
  "stated": 29,
  "rate": 0.446
 },
 "evidence_ok": true
}
```
