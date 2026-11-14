# The ALMaQUEST Survey: The Molecular Gas Main Sequence and the Origin of the Star-forming Main Sequence

`2019ApJ...884L..33L` | The Astrophysical Journal Letters 2019 | first author: Lin, Lihwai | arXiv: 1909.11243 | DOI: 10.3847/2041-8213/ab4815

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type observational_alma_primary

## Science

- Fields: nearby_galaxies
- Question: Do spaxel-level Sigma_SFR, Sigma_H2 and Sigma_* form a 3D relation, and is the resolved star-forming main sequence a consequence of the SK and molecular gas main sequence relations?  
  > "Our result suggests a scenario in which the resolved SFMS is the least physically fundamental and is the consequence of the combination of the SK and the MGMS relations." (abstract)
- Target **14 star-forming main-sequence MaNGA galaxies from ALMaQUEST**: coordinates _not stated_; z/distance z ~ 0.03  
  > "These galaxies are selected to have $10^{-10.5}$ yr$^{-1} <$ specific star formation rate (sSFR) $<10^{-9.5}$ yr$^{-1}$ without showing strong central starburst features." (SAMPLE and OBSERVATIONS); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.01225.S, 2017.1.01093.S, 2018.1.00558.S, 2018.1.00541.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: matched to MaNGA, FWHM ~ 2.5 arcsec  
  > "follow up MaNGA galaxies with $^{12}$CO(1-0) at a spatial resolution matched to MaNGA (FWHM $\sim 2.5 \ensuremath{''}$)" (SAMPLE and OBSERVATIONS)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO J=1-0 (not stated)
- Other facility **MaNGA (SDSS-IV) DR15 with Pipe3D**: Stellar mass surface density, emission-line fluxes, Halpha SFR  
  > "are obtained from the MaNGA Data Release 15 (DR15) data cubes processed by the Pipe3D pipeline" (SAMPLE and OBSERVATIONS)

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

- CO data processing procedures  
  > "The CO data is processed following the procedures described in (cite: lin17)" (SAMPLE and OBSERVATIONS) [from (cite: lin17); ALMaQUEST survey paper (L. Lin et al., in prep.)]
- Balmer-decrement extinction correction method  
  > "following the method described in the Appendix of (cite: vog13)" (SAMPLE and OBSERVATIONS) [from (cite: vog13)]
- Star-forming spaxel classification with [NII] diagnostic  
  > "following the method of (cite: kau03)" (SAMPLE and OBSERVATIONS) [from (cite: kau03)]

### Not stated but needed to reproduce (our reading)

- CO imaging and calibration details (CASA version, weighting, cleaning, masking)
- Exact list of the 14 galaxies/MaNGA IDs
- Spaxel regridding of CO to MaNGA and how S/N was computed
- ODR fitting weights and errors
- Inclination values used

## Analysis recipe

1. **Derive surface densities**: Convert CO to Sigma_H2 with alpha_CO; Sigma_* and Sigma_SFR (extinction-corrected Halpha, Kennicutt 1998) from MaNGA Pipe3D, inclination-corrected; spaxel selection cuts  
  > "The H$_{2}$ mass surface density ($\Sigma_{\rm~H_{2}}$) is computed from the inclination-corrected CO surface density by adopting a conversion factor ($\alpha_{\mathrm{CO}}$) of 4.3" (SAMPLE and OBSERVATIONS)
   - software: Pipe3D
   - parameter: CO S/N > 2; Sigma_* > 1e7 Msun kpc^-2; S/N>3 strong lines, >2 weak lines  
  > "An S/N $> 2$ cut [^1] in the CO line is applied to our analysis." (SAMPLE and OBSERVATIONS)
   - assumption: alpha_CO = 4.3; Salpeter IMF; Rv = 4.5  
  > "An extinction law with Rv = 4.5 (cite: fis05) is used." (SAMPLE and OBSERVATIONS)
   - fitting: _not stated_
   - validation: Footnote: S/N cuts 1.5-3 do not alter slopes  
  > "Adopting different S/N cuts between 1.5 to 3 do not significantly alter the slopes of the scaling relations presented here" (SAMPLE and OBSERVATIONS)
2. **Fit 2D scaling relations**: Orthogonal distance regression of power laws for rSFMS, SK, MGMS; Pearson correlation  
  > "We fit each of the above relations using the orthogonal distance regression (ODR) fitting method with a power law" (3D and 2D scaling relations)
   - fitting: ODR, linear in log  
  > "We fit each of the above relations using the orthogonal distance regression (ODR) fitting method with a power law parametrized as the following:" (The 3D and 2D scaling relations between $\Sigma_{\rm~SFR}$, $\Sigma_{\rm~H_{2}}$, and $\Sigma_{*}$)
   - validation: Monte Carlo: 14 random MaNGA DR13 galaxies, 1000 trials, mean slope 1.11±0.16  
  > "The derived mean slope of the 1000 trials is 1.11$\pm$0.16." (Resolved Star-forming Main Sequence (rSFMS))

## Software

- **Pipe3D** : MaNGA DR15 stellar mass and emission-line measurements  
  > "obtained from the MaNGA Data Release 15 (DR15) data cubes processed by the Pipe3D pipeline" (SAMPLE and OBSERVATIONS)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| rSFMS slope | 1.19 | 0.01 | dimensionless | 2 | the slope of the resolved main sequence (grey points), $1.19\pm0.01$ |
| SK relation slope | 1.05 | 0.01 | dimensionless | 2 | exponent $N \sim 1.05\pm0.01$ |
| MGMS slope | 1.10 | not stated | dimensionless | 2 | $\Sigma_{\rm~H_{2}}$  $\propto$ $\Sigma_{*}$$^{1.10}$ |
| scatter rSFMS / SK / MGMS | 0.25 / 0.19 / 0.20 | not stated | dex | 2 | the rSFMS has the largest scatter ($\sigma$ = 0.25) and is close to the square root of the quadratic sum of the scatters ($\sigma$ = 0.28) from the SK (0.19) and MGMS (0.20) relations |
| Optimal extended SK exponent | -0.3 | not stated | dimensionless | 2 | the scatter of the SK relation reaches a minimum value at $\beta = -0.3$ |

## Qualitative findings

- Spaxels with higher sSFR lie at the upper end of the MGMS  
  > "spaxels with higher sSFR tend to lie on the upper end of the MGMS" (Molecular Gas Main Sequence (MGMS))

## Claim tuples

- H: Sigma_SFR, Sigma_* and Sigma_H2 are mutually correlated, including a Sigma_H2-Sigma_* relation | E: ODR fits of spaxels in 14 MS galaxies | R: Slopes 1.19, 1.05, 1.10 with scatter 0.19-0.25 dex | F: A molecular gas main sequence exists | **supported**
- H: rSFMS results from SK and MGMS | E: Compare slope product and scatter combination and Pearson coefficients | R: 1.05x1.10=1.16 vs 1.19; sqrt-sum scatter 0.28 vs 0.25; rSFMS weakest correlation | F: rSFMS is the least fundamental | **supported**
- H: Extended SK with Sigma_* term reduces scatter | E: Vary exponent between -1 and 1 | R: Minimum at -0.3, not significantly different from 0 | F: No significant improvement | **refuted**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Small number of galaxies may explain steeper rSFMS slope; Sigma_* range only 1.5 dex  
  > "our sample spans only 1.5 orders of magnitude in $\Sigma_{*}$" (SK and Extended SK Relation)
- Caveat (inferred, ours): Fixed alpha_CO could induce correlation between Sigma_H2 and other quantities
- Caveat (inferred, ours): Common-distance and shared-inclination factors may induce correlations among surface densities
- Caveat (inferred, ours): Only S/N>2 CO selection; spaxels are correlated at beam scale (~2.5 arcsec)

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: CO data reduction and imaging details deferred to in-prep paper
- Missing: Galaxy list
- Missing: Fitting error treatment
- Data volume (inferred): ~50-100 GB raw for four ALMA programs; ~14 galaxies
- Score (inferred): 3/5, Public data and simple fitting, but CO processing and sample list are deferred to other papers.
- Rediscovery candidate: no, CO processing and galaxy list not given; recipe incomplete.

## Links

- Method: (cite: lin17) (CO data processing procedures)
- Companion: (cite: ell19) (Effect of gas fraction on local sSFR)
- Related: ALMaQUEST
- Related: MaNGA

## Checks

```json
{
 "quotes": 31,
 "quotes_ok": 31,
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
  "facts": 58,
  "stated": 17,
  "rate": 0.293
 },
 "evidence_ok": true
}
```
