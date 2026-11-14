# ALMA-IMF. XI. The sample of hot core candidates: A rich population of young high-mass protostars unveiled by the emission of methyl formate

`2024A&A...687A.163B` | Astronomy and Astrophysics 2024 | first author: Bonfand, M. | arXiv: 2402.15023 | DOI: 10.1051/0004-6361/202347856

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: star_formation, astrochemistry, milky_way_ism
- Question: Which compact CH3OCHO emission peaks (hot core candidates) exist in the 15 ALMA-IMF protoclusters, and what are their sizes, masses and nature?  
  > "We built a comprehensive census of hot core candidates towards the ALMA-IMF protoclusters based on the detection of two CH$_3$OCHO emission lines at 216.1 GHz." (abstract)
- Target **G327.29**: coordinates 15:53:08.13 -54:37:08.6 (cube center)  
  > "G327.29  | 15:53:08.13    | $-$54:37:08.6                                        | $-$45.0            | 2.5" (Table 1); z/distance 2.5 kpc  
  > "G327.29  | 15:53:08.13    | $-$54:37:08.6                                        | $-$45.0            | 2.5" (Table 1); distance from _not stated_
- Target **W43-MM1**: coordinates 18:47:47.00 -01:54:26.0 (cube center)  
  > "W43-MM1  | 18:47:47.00    | $-$01:54:26.0                                        | +97.0              | 5.5" (Table 1); z/distance 5.5 kpc  
  > "W43-MM1  | 18:47:47.00    | $-$01:54:26.0                                        | +97.0              | 5.5" (Table 1); distance from _not stated_
- Target **W51-E**: coordinates 19:23:44.18 +14:30:28.9 (cube center)  
  > "W51-E    | 19:23:44.18    | +14:30:28.9                                          | +55.0              | 5.4" (Table 1); z/distance 5.4 kpc  
  > "W51-E    | 19:23:44.18    | +14:30:28.9                                          | +55.0              | 5.4" (Table 1); distance from _not stated_
- Target **15 ALMA-IMF protoclusters (G008.67, G010.62, G012.80, G327.29, G328.25, G333.60, G337.92, G338.93, G351.77, G353.41, W43-MM1/2/3, W51-E, W51-IRS2)**: coordinates see Table 1 cube centers  
  > "They were selected to probe massive protoclusters at different evolutionary stages within a distance of 2 - 5.5 kpc." (2 Observations and core catalogs); z/distance 2.0-5.5 kpc  
  > "They were selected to probe massive protoclusters at different evolutionary stages within a distance of 2 - 5.5 kpc." (2 Observations and core catalogs); distance from _not stated_

## Data provenance

- ALMA projects: 2017.1.01355.L, 2013.1.01365.S
- bands: Band 6 (1.3 mm) spw0 for lines; B6 and B3 continuum  
  > "eight at 1.3 mm (ALMA band 6, hereafter B6) and four at 3 mm (ALMA band 3, hereafter B3)" (2.1 Spectral line datacubes)
- frequencies and spectral setup: 234 MHz-wide spw centered on 216.2 GHz, 0.17 km/s (122 kHz) resolution  
  > "we focus our analysis on the 234 MHz-wide spw centered on 216.2 GHz, at 1.3 mm (B6–spw0)" (2.1 Spectral line datacubes)
- continuum bandwidth: _not stated_
- arrays: ALMA 12-m array, up to two configurations combined  
  > "up to two different ALMA 12-m array configurations were combined in the uv-plane for each field" (2.1 Spectral line datacubes)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.4'' to 1.1'' (robust 0), ~2500 au physical  
  > "The resulting angular resolution of the B6–spw0 line cubes, using a robust weighting of 0, ranges from $\sim$ 0.4$\ensuremath{''}$ to 1.1$\ensuremath{''}$" (2.1 Spectral line datacubes)
- max recoverable scale: _not stated_
- sensitivity: line cube rms 2.1-16.7 mJy/beam (0.16-0.99 K)  
  > "G328.25      | 0.75$\times$0.59                                 | -13     | 16.7                | 0.99" (Table 1b)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CH3OCHO 19(2,18)-18(2,17) E (216109.780 MHz)
- Line: CH3OCHO 19(2,18)-18(2,17) A (216115.572 MHz)
- Line: CH3OCHO 19(1,18)-18(1,17) E (216210.906 MHz)
- Line: CH3OCHO 19(1,18)-18(1,17) A (216216.539 MHz)
- Line: DCO+ 3-2 (216112.582 MHz)
- Other facility **Herschel/APEX PPMAP**: Dust temperature maps used for continuum cores without methyl formate  
  > "Dust-based temperature estimates using *Herschel* and APEX data with the resolution-improving PPMAP method" (5.4 Temperature estimates)
- External data: getsf 1.3 mm continuum core catalog (807 cores) from ALMA-IMF  
  > "In total 807 compact continuum cores were extracted from the 15 ALMA-IMF protoclusters using *getsf*" (2.2 Continuum maps and core catalogs) [from (cite: louvet2024)]
- External data: PPMAP dust temperature maps (2.5'' resolution)  
  > "The PPMAP temperature maps have a 2.5$\ensuremath{''}$ angular resolution (cite: dellova2024)" (5.5 Mass estimates) [from (cite: dellova2024)]
- External data: Spectroscopic data for CH3OCHO from JPL catalog  
  > "The spectroscopic predictions (frequencies, upper energy levels and Einstein coefficients) are taken from the JPL catalog (cite: pearson2010)." (Table 2) [from (cite: pearson2010)]
- External data: H41alpha ionized gas analysis  
  > "we refer for a detailed analysis to (cite: galvanmadrid2024)" (5.2 Free-free contamination) [from (cite: galvanmadrid2024)]

## Processing

### Calibration

- pipeline or manual: Custom ALMA-IMF imaging pipeline; JvM correction applied  
  > "They were produced using the custom ALMA-IMF imaging pipeline[^2] originally developed to process the continuum data" (2.1 Spectral line datacubes)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: robust = 0  
  > "using a robust weighting of 0" (2.1 Spectral line datacubes)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: STATCONT with sigma-clipping in image plane  
  > "we use the STATCONT software (cite: sanchez2018) with the sigma-clipping algorithm to systematically remove the continuum emission in the image plane" (2.1 Spectral line datacubes)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Constant beam over all channels; continuum unsmoothed catalog used  
  > "The deconvolved datacubes have a constant beam over all the channels." (2.1 Spectral line datacubes)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Data reduction and imaging pipeline of ALMA-IMF line cubes  
  > "The data reduction of the ALMA-IMF spectral windows is described in (cite: cunningham2023)." (2 Observations and core catalogs) [from (cite: cunningham2023)]
- Dust opacity kappa_1.3mm = 0.01 cm2/g and mass equation  
  > "we use the following equation (cite: motte2018nat; pouteau2022)" (5.5 Mass estimates) [from (cite: motte2018nat; pouteau2022)]
- Protostellar phase timescale 3e5 yr  
  > "We assume a time-scale for the protostellar phase of $3\times10^5$ yr based on (cite: Duarte2013)" (6.4 Emergence and life time of hot cores) [from (cite: Duarte2013)]
- Beta/alpha dust index adopted (alpha_dust=3.5)  
  > "we assume $\alpha_{\mathrm{dust}}$ = 3.5, which corresponds to $\beta_{\mathrm{dust}}$ = 1.5" (Appendix free-free) [from earlier ALMA-IMF papers (reference not printed)]

### Not stated but needed to reproduce (our reading)

- GExt2D settings beyond S/N=2.5 (code is 'in prep.'; not publicly specified)
- Exact rms region polygons and the manually chosen noise regions for GExt2D
- Line cleaning parameters per field in the pipeline
- Line-free channels used for STATCONT
- Continuum maps' robust and imaging parameters (deferred to other papers)
- Full data volume and CASA version
- How H41alpha contours define free-free regions

## Analysis recipe

1. **Make CH3OCHO moment 0 maps**: Integrate line pair 2 over ~35 km/s (206 channels); 15 km/s (88 channels) for G012.80 and W43-MM2  
  > "we create moment 0 maps of methyl formate by integrating the spectral intensity over a broad velocity range of $\sim$ 35 km s$^{-1}$ (*i.e.* 206 channels)" (3.1)
   - fitting: _not stated_
   - validation: Narrower velocity range gave consistent parameters for G327.29 and G351.77  
  > "Using a narrower velocity range for the moment 0 maps for these sources gives, however, consistent parameters for the peak position and deconvolved source size." (3.2)
2. **Extract methyl formate sources**: GExt2D curvature-based detection then 2D Gaussian fits on primary-beam corrected moment 0  
  > "*GExt2D* computes the second derivative of the CH$_3$OCHO moment 0 map and looks for local maxima in the curvature map" (3.2)
   - software: GExt2D
   - parameter: Detection threshold S/N = 2.5 in curvature  
  > "We set the detection threshold to a signal-to-noise ratio of 2.5, that is related to the local noise fluctuation in the curvature map." (3.2)
   - fitting: 2D Gaussian  
  > "source sizes (FWHM) and the peak values of the integrated intensity maps (Jy beam$^{-1}$ km s$^{-1}$) are measured for each individual source by fitting 2D Gaussians to its central position" (Source extraction)
   - validation: Visual inspection of single-pixel spectra; keep sources with both line pairs above 3 sigma  
  > "only the sources for which the two CH$_3$OCHO line pairs are detected above the 3 $\sigma$ noise level" (3.2)
3. **Measure VLSR and line richness**: 1D Gaussian fit to three uncontaminated lines; count channels >3 sigma  
  > "We derive the $V_{\mathrm{LSR}}$ of each methyl formate source by fitting a single component, 1D-Gaussian to each of the three methyl formate lines" (3.4)
   - fitting: single-component 1D Gaussian  
  > "We derive the $V_{\mathrm{LSR}}$ of each methyl formate source by fitting a single component, 1D-Gaussian to each of the three methyl formate lines" ($V_{\mathrm{LSR}}$ estimates)
   - validation: _not stated_
4. **Cross-match with continuum cores**: Associate if offset smaller than line-cube beam FWHM  
  > "We associate a methyl formate source to a continuum core if the angular offset between their respective peak positions is smaller than the diameter (FWHM) of the synthesized beam" (5.1)
   - fitting: _not stated_
   - validation: _not stated_
5. **Correct free-free contamination**: Iterative 1.3/3 mm flux ratio method vs. theoretical dust ratio, for 17 sources  
  > "we rely on the dual band approach of ALMA-IMF and exploit the dust continuum emission at 1.3 mm, and 3 mm" (5.2)
   - assumption: alpha_dust = 3.5, free-free alpha = -0.1, Td 50-150 K  
  > "for a spectral index $\alpha_{\mathrm{freefree}}$ = -0.1 that corresponds to optically thin free-free emission" (Appendix free-free)
   - fitting: _not stated_
   - validation: _not stated_
6. **Deconvolve source sizes**: Analytic ellipse deconvolution from beam; minimum half beam  
  > "We have set a minimum deconvolved size for each region to half the synthesized beam of the line cube" (5.3)
   - software: GILDAS
   - fitting: _not stated_
   - validation: _not stated_
7. **Derive core masses**: Opacity-corrected dust mass equation with Td=100±50 K (300±100 K for six extreme sources)  
  > "we adopt a canonical dust temperature of 100 $\pm$ 50 K for all methyl formate sources" (5.4)
   - parameter: kappa_1.3mm = 0.01 cm2/g  
  > "we adopted a dust opacity coefficient per unit of mass $\kappa_{1.3mm}$ = 0.01 cm$^{2}$ g$^{-1}$ (assuming a gas-to-dust ratio of 100)" (5.5)
   - assumption: Gas-to-dust 100; Ossenkopf & Henning opacities  
  > "which is adapted to dense cores (cite: ossenkopf1994)" (5.5)
   - fitting: 1000 Monte Carlo temperature draws, uniform 50-150 K (200-400 K for extreme)  
  > "we used 1000 realisations of randomly sampled temperatures from a uniform distribution between 50 and 150 K" (5.5)
   - validation: Factor 3 in Td gives at most factor 4.5 in mass  
  > "A factor 3 of difference in the assumed dust temperature leads to at most a factor 4.5 of difference in the mass estimates." (5.5)
8. **Infer heating luminosity and hot core lifetime**: Td(R)=37 K (L/Lsun)^0.25 (R/100 au)^-0.4 at 120-160 K sublimation; hot core fraction x 3e5 yr  
  > "If we assume that the observed CH$_3$OCHO emission traces the thermal sublimation radius with $T_{\rm d}$ = 120–160 K" (6.2)
   - assumption: Protostellar phase 3e5 yr  
  > "We assume a time-scale for the protostellar phase of $3\times10^5$ yr" (6.4)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **GExt2D** : Source extraction of CH3OCHO peaks  
  > "we use the source extraction algorithm *GExt2D* (cite: bontemps2024)" (3.2)
- **STATCONT** : Continuum removal in cubes  
  > "we use the STATCONT software (cite: sanchez2018)" (2.1)
- **getsf** : Continuum core catalog  
  > "the multi-scale source and filament extraction method *getsf* (cite: menshchikov2021) was used" (2.2)
- **GILDAS** : atan2 function in size deconvolution  
  > "which uses the 2-argument arctangent (*atan2*) function of the GILDAS[^4] software." (Appendix)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of methyl formate hot core candidates | 76 | not stated | sources | 2 | Overall, we find a total of 76 methyl formate sources |
| New hot core candidates | 56 (76%) | not stated | sources | 2 | Overall, we find 56 sources that could be considered as new hot core candidates |
| Median deconvolved size | ~2300 | not stated | au | 6 | with a median size of about 2300 au |
| Core mass range | ~0.2 to ~80 | not stated | Msun | 7 | the methyl formate sources range in mass from $\sim$ 0.2 $\ensuremath{\mathrm M_{\odot}}$ to $\sim$80 $\ensuremath{\mathrm M_{\odot}}$ |
| Median mass of methyl formate sources | ~3.8 | not stated | Msun | 7 | with a median mass of $\sim$ 3.8 |
| Fraction of continuum cores >8 Msun with CH3OCHO | 38-48% | range over 1000 temperature draws | percent | 7 | We find that 38–48% of the dust continuum cores with masses above 8 $\ensuremath{\mathrm M_{\odot}}$ are associated with methyl formate emission |
| Hot core phase duration | 0.9e5 to 2.4e5 | factor of a few | yr | 8 | we find that the time scales for the hot core phase is between 0.9$\times10^5$ yr and 2.4$\times10^5$ yr |
| Pearson correlation continuum vs CH3OCHO peak | 0.7 | P<0.001 | dimensionless | 0 | with a Pearson’s coefficient $\rho$ = 0.7 and assorted with a $P_{\mathrm{value}} <$ 0.001 |
| Sources with mass >8 Msun (highest estimate) | 38 (~50%) | not stated | sources | 7 | 38 sources have their highest estimated mass (*i.e.* for $T_{\mathrm{d}}$ = 50 or 200 K) above 8 $\ensuremath{\mathrm M_{\odot}}$ |

## Qualitative findings

- All 15 protoclusters host at least one methyl formate source; G353.41 is a chemically poor outlier.  
  > "We found one outlier, G353.41 that clearly lacks strong emission from COMs." (Summary)

## Claim tuples

- H: Hot core candidates exist across protoclusters regardless of stage | E: GExt2D extraction on CH3OCHO moment 0 maps in 15 fields | R: 76 sources; all fields have at least one; fraction never >25% of cores | F: Number of candidates is independent of clump mass and evolutionary stage | **supported**
- H: All massive cores go through the hot core phase | E: Compare fraction of continuum cores with CH3OCHO vs mass | R: 41% above 8 Msun, 90% above 39 Msun | F: Fraction increases with mass; massive cores enter hot core phase rapidly | **supported**
- H: Lower-mass CH3OCHO sources are hot corinos | E: Compare sizes, masses and sensitivity with hot corinos | R: Sizes 1000-4700 au, too large and too bright for corinos | F: Origin uncertain: shocks or evolved stage | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Single CH3OCHO tracer chosen as spectrally well-resolved and compact compared to other tracers  
  > "hence provide a potentially more confused view of hot cores compared to that of the selected spectrally well-resolved CH$_3$OCHO lines" (2.1)
- Alternative: Line richness not used as classification criterion because of sensitivity limits  
  > "the fraction of channels containing emission in B6-spw0 is not used as an additional quantitative criterion to classify potential hot cores" (3.3)
- How they decided it was enough: _not stated_
- Limitation (authors): Temperature assumed uniformly (100 K), uncertain; free-free may be overestimated  
  > "the adopted temperatures may be subject to significant uncertainties" (5.4)
- Caveat (inferred, ours): Mass threshold of 8 Msun for classification depends on assumed Td and opacity
- Caveat (inferred, ours): Single-line tracer cannot distinguish thermal from shock origin
- Caveat (inferred, ours): Angular resolution ~2500 au blends multiple sources
- Caveat (inferred, ours): GExt2D is unpublished

## Reproducibility

- Data public (paper): ALMA-IMF data; core catalogs on ALMA-IMF website  
  > "The core catalogs can be found on the ALMA-IMF large program website [^3]" (2.2)
- Products in archive: _not stated_
- Code: ALMA-IMF imaging pipeline on GitHub  
  > "https://github.com/ALMA-IMF/reduction" (footnote 2)
- Missing: GExt2D code and parameters
- Missing: Processed line cubes' exact versions
- Missing: getsf catalog from Louvet et al. 2024
- Missing: PPMAP maps from Dell'ova et al. 2024
- Data volume (inferred): ~hundreds of GB (15 fields, B6 spw0 cubes plus continuum)
- Score (inferred): 3/5, Public data and clear recipe, but depends on unreleased GExt2D and companion catalogs.
- Rediscovery candidate: no, Key tools and catalogs are from unpublished companion papers.

## Links

- Method: (cite: bontemps2024) (GExt2D algorithm)
- Method: (cite: cunningham2023) (ALMA-IMF spectral window data reduction)
- Method: (cite: menshchikov2021) (getsf source extraction)
- Companion: (cite: louvet2024) (Continuum core catalogs)
- Companion: (cite: galvanmadrid2024) (H41alpha free-free analysis)
- Companion: (cite: dellova2024) (PPMAP temperatures)
- Related: ALMA-IMF
- Related: ATLASGAL
- Related: ATOMS

## Checks

```json
{
 "quotes": 76,
 "quotes_ok": 76,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2013.1.01365.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 98,
  "stated": 56,
  "rate": 0.571
 },
 "evidence_ok": true
}
```
