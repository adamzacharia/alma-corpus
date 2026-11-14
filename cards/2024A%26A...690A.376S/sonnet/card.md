# Emergence of high-mass stars in complex fiber networks (EMERGE): IV. Environmental dependence of the fiber widths

`2024A&A...690A.376S` | Astronomy and Astrophysics 2024 | first author: Socci, A. | arXiv: 2408.16427 | DOI: 10.1051/0004-6361/202451177

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type archival_reuse

## Science

- Fields: star_formation, milky_way_ism
- Question: How do fiber widths (FWHM) vary across different star-forming environments in Orion, and do they depend on peak column density and external pressure?  
  > "Here, we aim to characterise the variation in the fiber widths under the different conditions explored by this survey." (abstract)
- Target **Orion A and B regions (OMC-1, OMC-2, OMC-3, OMC-4 South, LDN 1641N, NGC 2023, Flame Nebula)**: coordinates _not stated_; z/distance 414 pc  
  > "Considering 0.027 pc as resolution limit (dotted grey line; $3\times\theta_\mathrm{beam}$ at 414 pc)" (Appendix: Changes to the public version); distance from _not stated_

## Data provenance

- ALMA projects: 2019.1.00641.S, 2015.1.00669.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: ALMA + IRAM-30m  
  > "with new suite of Atacama Large Millimetre Array (ALMA) plus IRAM-30m observations" (Introduction)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 4.5" (~2000 au)  
  > "These targets were homogeneously surveyed at a resolution of $\theta_\mathrm{beam}\sim2000$ au (or 4.5$''$)" (Introduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: N2H+ 1-0 (not stated)
- Other facility **IRAM-30m**: Short-spacing/single-dish N2H+ data combined with ALMA  
  > "This work is based on IRAM-30m telescope observations carried out under project numbers 032-13, 120-20, 060-22, and 133-22." (Acknowledgements)
- Other facility **Herschel**: Column density calibration of N2H+ maps  
  > "By calibrating our N$_2$H$^+$ maps against *Herschel* observations in the same region, we were able to derive a high-resolution column density map" (3 Non-isothermal narrow fibers)
- External data: Herschel Gould Belt Survey filament widths and peak column densities per region  
  > "we try to compare the results obtained from our study and the HGBS (cite: arzoumanian19) by adding the filament properties they derived per region to Fig. [6]" (4.1 FWHM-N0 anti-correlation) [from (cite: arzoumanian19)]
- External data: Theoretical FWHM-N0 relations for pressure-confined and magnetised filaments  
  > "we corrected by a factor of 2 the models from (cite: fischera12), which were originally determined for the density of H nucleons." (4.2 Comparison with the theoretical models) [from (cite: fischera12); (cite: heitsch13)]

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

- Fiber identification (152 fibers), column density and temperature maps from N2H+ calibrated against Herschel  
  > "In a previous paper of this series, (cite: socci24) (hereafter Paper III) identified a total of 152 velocity-coherent, sonic fibers." (1 Introduction) [from (cite: socci24) Paper III]
- ALMA+IRAM-30m observations and data reduction  
  > "with a new set of ALMA+IRAM-30m observations (see Paper I)." (3 Non-isothermal narrow fibers) [from Paper I (cite: hacar24)]
- FilChap radial fitting routine  
  > "we implemented the automatic fitting routine FilChap (cite: suri19) in our filament-finding algorithm" (3.2 Radial fits) [from (cite: suri19)]

### Not stated but needed to reproduce (our reading)

- Paper III column density map and temperature map products
- Fiber axis catalog
- ALMA calibration, imaging and combination details (in Papers I/II)
- Fit initial guesses and bounds in FilChap
- Details of Plummer-fit A_p and error estimation

## Analysis recipe

1. **Radial profile fitting with FilChap**: Modified FilChap samples column density map perpendicular to fiber axis, averages the profile, fits Gaussian (also Plummer p=2, 4 for tests); temperature sampled along same cuts without averaging  
  > "The column density map is sampled to determine the average density profile along the axis of each structure, which is then fitted with different orthogonal cuts" (3.2 Radial fits)
   - software: FilChap
   - parameter: avg_len = 1, n2 = 2, npix = 45 and 43, dist_normal = 3 x theta_beam, order = 3  
  > "We therefore set `avg`$\_$`len` = 1 and `n2` = 2 to have the radial sampling performed only around these points;" (Appendix: Changes to the public version)
   - parameter: peak limit 5 x sigma, sigma ~3e21 cm-2  
  > "obtaining $\sigma\sim3\times10^{21}$ cm$^{-2}$ for a typical temperature of 20 K seen across our fields." (Appendix: Changes to the public version)
   - assumption: No baseline subtraction since column density floor term removed  
  > "we avoid any baseline subtraction, usually applied by FilChap, since we removed the column density floor term" (3.2 Radial fits)
   - fitting: Gaussian chosen over Plummer: fewest unresolved widths, lowest reduced chi2, fewest free parameters (3 vs 4)  
  > "it has the lowest degeneracy given the lower number of free parameters (3) compared to the Plummer profile (4)" (3.2 Radial fits)
   - validation: Compared Gaussian and Plummer fits via skewness, kurtosis, peak counts, reduced chi2, resolved fraction  
  > "Figure [11] shows the reduced $\chi^2$ calculated for each cut as additional quality assessment for the fit." (Appendix: Peaks, shoulders, and asymmetries)
2. **Estimate temperature gradients**: Gradient = (T_bg - T_K^0)/Δx with Δx = ±0.1 pc from column density peak  
  > "we chose a radial distance of $\pm0.1$ pc from the column density peak as representative of the environment outside the fiber." (3.6 Non-isothermal fibers)
   - fitting: _not stated_
   - validation: _not stated_
3. **Compare FWHM vs N0 with HGBS and models, estimate volume density and external pressure**: n0 ~ N0/FWHM; P_ext/kB = (1 - m/m_vir) N0/FWHM T_K^0 for sub-virial fibers  
  > "we can then estimate the value of $P_\mathrm{ext}$ in our fibers as" (4.3 Are fibers pressured confined?)
   - assumption: Fibers isothermal, sub-critical, pressure-confined filaments  
  > "Assuming our fibers as isothermal, sub-critical, and pressure-confined filaments, the mean volume density can be determined in a first-order approximation" (4.3 Are fibers pressured confined?)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **FilChap** : Automatic radial profile fitting of fibers  
  > "we implemented the automatic fitting routine FilChap (cite: suri19) in our filament-finding algorithm" (3.2 Radial fits)
- **HiFIVe** : Fiber identification  
  > "Each fiber is labelled with a corresponding ID during the identification process carried out by HiFIVe (cite: hacar18)" (Additional maps and tables)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Median fiber FWHM (all cuts) | 0.05 | +0.02/-0.01 (IQR) | pc | 1 | The corresponding median width is $FWHM=0.05^{+0.02}_{-0.01}$ pc |
| Convergent radial cuts | 991 of 1052 | not stated | cuts | 1 | FilChap was able to provide a convergent fit for 991 of these cuts |
| Median peak column density N0 | 5e22 | not stated | cm^-2 | 1 | Our EMERGE Early ALMA Survey shows a median value of $N_0\sim5\times10^{22}$ cm$^{-2}$ |
| Median temperature gradient | 80 | not stated | K pc^-1 | 2 | / Sample       / 152    / 1209            / 0.74                              / 0.091  / 36                        / 0.78                   / 80                      / 19               / 5.1 |
| External pressure range | ~4e5 (OMC-4 South) to ~8e6 (OMC-1) | not stated | K cm^-3 | 3 | retrieves mean external pressures between $P_\mathrm{ext}/k_\mathrm{B}\sim 8\times10^6$ K cm$^{-3}$ in OMC-1 and $\sim 4\times10^5$ K cm$^{-3}$ in OMC-4 South |
| Fraction of cuts with FWHM > 0.1 pc | 4% | not stated | percent | 1 | only 4% of our cuts show a $FWHM$ above 0.1 pc |

## Qualitative findings

- Fiber widths vary systematically between regions; narrowest in OMC-1, OMC-2 and Flame Nebula, broadest in NGC 2023 and LDN 1641N  
  > "Regions such as OMC-1, OMC-2, and the Flame Nebula have the narrowest individual cuts, with a median value of $\sim0.03-0.04$ pc." (4 Environmental variation in the fiber widths)

## Claim tuples

- H: Fibers share a characteristic width of ~0.1 pc | E: Gaussian fits of 991 radial cuts across 7 Orion regions | R: Median FWHM 0.05 pc; only 4% of cuts above 0.1 pc | F: Fibers are narrower than 0.1 pc and no unique characteristic width exists | **supported**
- H: Fiber FWHM varies with environment | E: Compare per-region FWHM distributions | R: Median FWHM ranges 0.034 to 0.074 pc between regions | F: Systematic region-to-region variation in widths | **supported**
- H: FWHM anti-correlates with N0 above ~1e22 cm^-2 as predicted by models | E: Compare fiber and HGBS FWHM-N0 with Fischera & Martin and Heitsch models | R: Width drops with N0 above ~4e22 cm^-2 | F: Anti-correlation observed, though models cannot fully fit | **partially**
- H: Fibers are isothermal | E: Estimate temperature gradients across cuts | R: Median gradient ~80 K/pc, >30 K/pc in most cuts | F: Fibers are non-isothermal | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Plummer fits with p=2 and p=4 rejected in favour of Gaussian  
  > "Based on the previous tests, the Plummer ($p=2$) function appears as the worst choice to fit the radial profiles of the Orion fibers." (Appendix: Peaks, shoulders, and asymmetries)
- How they decided it was enough: _not stated_
- Limitation (authors): Model applicability limited: fibers are non-isothermal prolate spheroids; pressure estimates assume equilibrium  
  > "the above first-order calculations assume an equilibrium solution for these objects." (4.3 Are fibers pressured confined?)
- Caveat (inferred, ours): Different resolutions and N2H+ density selectivity may bias widths versus Herschel
- Caveat (inferred, ours): Column-density conversion depends on Paper III calibration
- Caveat (inferred, ours): FWHM-N0 correlation uses small dynamic range and region averages
- Caveat (inferred, ours): Pressure estimate is order-of-magnitude

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Code: FilChap public repository (modified version not stated as released)  
  > "<https://github.com/astrosuri/filchap>" (footnote)
- Missing: Modified FilChap code
- Missing: Paper III column density and temperature maps and fiber axes
- Missing: Reduction details of the ALMA+IRAM data
- Data volume (inferred): Large raw ALMA data (~100s GB) for 7 mosaics; derived maps are small
- Score (inferred): 2/5, Analysis depends on unpublished/companion products (Paper III maps, modified FilChap); parameters partly given.
- Rediscovery candidate: no, Needs Paper III derived maps and modified code not included here.

## Links

- Method: (cite: suri19) (FilChap routine)
- Method: (cite: hacar18) (HiFIVe fiber identification)
- Companion: (cite: hacar24) (Paper I: EMERGE Early ALMA Survey)
- Companion: (cite: socci24) (Paper III: fiber identification and column density maps)
- Companion: (cite: bonanomi2024) (ALMA+IRAM-30m observations)
- Related: EMERGE Early ALMA Survey
- Related: Herschel Gould Belt Survey

## Checks

```json
{
 "quotes": 40,
 "quotes_ok": 40,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 26,
  "rate": 0.377
 },
 "evidence_ok": true
}
```
