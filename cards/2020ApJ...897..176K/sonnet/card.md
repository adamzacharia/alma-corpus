# The Molecular Interstellar Medium in the Super Star Clusters of the Starburst NGC 253

`2020ApJ...897..176K` | The Astrophysical Journal 2020 | first author: Krieger, Nico | arXiv: 2006.08262 | DOI: 10.3847/1538-4357/ab9c23

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, astrochemistry, star_formation
- Question: What are the physical and chemical properties of the molecular gas in the 14 embedded (proto-)super star cluster candidates of NGC 253, and what energy sources (PDR, XDR, mechanical, IR pumping) heat them?  
  > "we utilize high-resolution (2.5 pc, 0.15$^{\prime\prime}$) ALMA observations in band 7 ($\sim 350$ GHz) to study the physical and chemical environment of individual embedded (proto-)SSC candidates." (1 Introduction)
- Target **NGC 253 SSCs 1-14**: coordinates _not stated_; z/distance 3.5 Mpc  
  > "is one of the nearest starburst systems, at a distance of 3.5 Mpc (cite: Rekola:2005ha)." (1 Introduction); distance from Rekola et al. 2005  
  > "is one of the nearest starburst systems, at a distance of 3.5 Mpc (cite: Rekola:2005ha)." (1 Introduction)

## Data provenance

- ALMA projects: 2015.1.00274.S
- bands: Band 7 (~350 GHz)  
  > "high-resolution (2.5 pc, 0.15$^{\prime\prime}$) ALMA observations in band 7 ($\sim 350$ GHz)" (1 Introduction)
- frequencies and spectral setup: LSB 342.0-345.8 GHz, USB 353.9-357.7 GHz, 7.6 GHz total  
  > "The sidebands are tuned to $342.0-345.8$ GHz (LSB) and $353.9-357.7$ GHz (USB), yielding a combined 7.6 GHz total bandwidth." (2.1 Observations, calibration and Imaging)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.17" x 0.13" (~2.5 pc)  
  > "both bands are restored with the same beam of $0.17\ensuremath{^{\prime\prime}}\times 0.13\ensuremath{^{\prime\prime}}$" (2.1 Observations, calibration and Imaging)
- max recoverable scale: _not stated_
- sensitivity: per-channel noise 0.37 K (2.5 MHz channels)  
  > "The per-channel noise is 0.37 K." (2.1 Observations, calibration and Imaging)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO 3-2 (not stated)
- Line: HCN 4-3 (not stated)
- Line: HCO+ 4-3 (not stated)
- Line: CS 7-6 (not stated)
- External data: SSC positions, sizes (1.5-4 pc) and properties (masses, densities)  
  > "They found the sizes of the SSCs to be of order the beam size (deconvolved sizes of $\sim 1.5-4$ pc)." (2.2 Spectra) [from Leroy et al. 2018 (cite: 2018ApJ...869..126L)]
- External data: Isotope ratios 12/13C=40±20, 14/15N=200, 16/18O=130±40  
  > "We adopt $^{12/13}$C = $40\pm20$" (4.3 Isotopic ratios and optical depth) [from Henkel 2014; Martin 2010, 2019; Tang 2019; Viti 2019]
- External data: PDR/XDR diagnostic diagrams  
  > "proposed diagnostic diagrams to infer the excitation environment in the nuclear regions of galaxies." (4.2.5 SSC energy source) [from Loenen et al. 2008; Baan et al. 2008]

## Processing

### Calibration

- pipeline or manual: pipeline-calibrated  
  > "The pipeline-calibrated and continuum-subtracted visibilities are imaged in 2.5 MHz channels" (2.1 Observations, calibration and Imaging)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ≲5% systematic  
  > "the systematic flux uncertainty applies with $\lesssim 5\%$ for these observations according to the ALMA specifications." (Table 3)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "using Briggs weighting (robust parameter of 0.5)" (2.1 Observations, calibration and Imaging)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uv-plane subtraction; image-plane subtraction additionally for SSCs 2,5,8,10,13,14  
  > "we also carry out am image-plane continuum subtraction for the affected spectra." (2.1 Observations, calibration and Imaging)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: LSB and USB restored with common beam  
  > "so both bands are restored with the same beam of $0.17\ensuremath{^{\prime\prime}}\times 0.13\ensuremath{^{\prime\prime}}$" (2.1 Observations, calibration and Imaging)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Data reduction and imaging identical to earlier CO(3-2) study, applied to full sidebands  
  > "Data reduction and imaging of our ALMA cycle 4 observations are described in detail in (cite: 2019ApJ...881...43K)." (2.1 Observations, calibration and Imaging) [from Krieger et al. 2019 (cite: 2019ApJ...881...43K)]
- Fixed Trot=130 K as in earlier work, warm ISM component  
  > "The former corresponds to the warm ISM component found by (cite: 2013ApJ...779...33M) and (cite: Gorski:2017es) on lower spatial resolution." (3.2 Spectral fitting procedure) [from Mangum et al. 2013; Gorski et al. 2017]

### Not stated but needed to reproduce (our reading)

- SSC center coordinates (from Leroy et al. 2018)
- line-free channels used for continuum fit
- CASA version and pipeline version
- XCLASS version and exact fit configuration/initial guesses
- Observing dates, array configurations, time on source
- Spectral axis rest-frame velocities of each SSC
- Gaussian fitting details for integrated intensities

## Analysis recipe

1. **Extract spectra and set rest frame**: Single-pixel (0.1"x0.1") spectra at SSC centers; shift to rest frame with velocity from Gaussian fit to dominant CS(7-6) component  
  > "we extract single pixel ($0.1\ensuremath{^{\prime\prime}}\times 0.1\ensuremath{^{\prime\prime}}$) spectra at the recorded center positions." (2.2 Spectra)
   - software: CASA
   - fitting: Gaussian fit to CS(7-6)  
  > "We estimate the velocity from a Gaussian fit and apply the Doppler correction to shift to the rest frequency." (2.2 Spectra)
   - validation: Consistent within <5 km/s with independent imaging by Rico-Villas et al.  
  > "Our estimates of the source velocities are consistent within $<5$ km s$^{-1}$" (2.2 Spectra)
2. **Identify lines**: Splatalogue with CDMS and JPL catalogs; four investigators independently; only consistent lines kept  
  > "The lines consistently identified by all investigators form the final line list" (2.3 Line Identification)
   - software: Splatalogue
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit spectra for column density, linewidth, centroid**: XCLASS LTE radiative transfer in three runs: independent per-species, joint fit with ranges limited to 16-84th percentile of run 1, refinement of Trot for SO2 and H2CS (25-1000 K)  
  > "(1) an unconstrained, independent XCLASS fit of each species individually for each source, followed by (2) a joint fit of all detected species to the whole data range for each source, and (3) refinement fits" (3.2 Spectral fitting procedure)
   - software: XCLASS, MAGIX
   - parameter: Genetic algorithm 50 iterations then Levenberg-Marquardt 50 iterations  
  > "combination of 50 iterations of the “Genetic” algorithm followed by 50 iterations of the “Levenberg-Marquardt” algorithm" (Appendix: Fit algorithm)
   - parameter: Limits: N 1e12-1e25 cm-2, width 5-80 km/s, centroid ±10 km/s  
  > "We apply loose limits on column density ($10^{12} - 10^{25}$ cm$^{-2}$), linewidth ($5-80$ km s$^{-1}$)" (Appendix: XCLASS fit parameters)
   - assumption: Source size fixed to unity (fills beam); Trot=130 K, Tvib=300 K fixed; LTE; emission-only components  
  > "we fix $\mathrm{T_{rot}}=130$ K for the purely rotationally excited species and $\mathrm{T_{vib}}=300$ K for the ro-vibrational transitions." (3.2 Spectral fitting procedure)
   - fitting: Genetic + Levenberg-Marquardt chi2 optimization; molecular data from CDMS  
  > "The molecular parameters required for this task are obtained from the CDMS catalog." (3.2 Spectral fitting procedure)
   - validation: Monte Carlo with 100 noise realizations (sigma 0.46 K); median and 16-84th percentiles  
  > "We draw 100 versions of Gaussian noise and add it to the observed spectra which are then fitted as described above." (Appendix: Error estimation)
4. **Derive integrated intensities**: Gaussian fits to XCLASS-deblended spectra  
  > "This is done through Gaussian fits to the de-blended spectra." (3.4 Derivation of integrated intensity)
   - software: XCLASS
   - fitting: _not stated_
   - validation: _not stated_
5. **Line and column density ratios; PDR/XDR diagnostics**: Compute ratios for main velocity component; compare with Loenen et al. 2008 and Baan et al. 2008 diagrams, correcting H15NC to H14NC via 14N/15N  
  > "we can correct the detected H$^{15}$NC using the $^{14}$N/$^{15}$N isotope ratio obtained from HCN and HC$^{15}$N." (4.2.5 SSC energy source)
   - assumption: Steady-state PDR/XDR models  
  > "with the assumption of steady-state chemistry." (4.2.5 SSC energy source)
   - fitting: _not stated_
   - validation: Repeated with line intensity ratios, same qualitative result  
  > "we also construct Figure [4](#figure: XDR PDR column densities) with observational (instead of modelled) data" (4.2.5 SSC energy source)
6. **Estimate optical depth from isotopologue ratios**: tau13 = Tb13/Tb12; tau12 = tau13 x [12C]/[13C]  
  > "$$\tau^{^{12}\mathrm{C}} = \tau^{^{13}\mathrm{C}} \times [^{12}\mathrm{C}]/[^{13}\mathrm{C}]$$" (4.3 Isotopic ratios and optical depth)
   - assumption: Optically thick main species, thin isotopologues; equal filling factors and common Tex  
  > "Further assumptions are equal beam filling factors and a common excitation temperature for both isotopologues." (4.3 Isotopic ratios and optical depth)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : data reduction and imaging  
  > "CASA (cite: McMullin:2007tj), astropy (cite: Collaboration:2013cd; Collaboration:2018ji), XCLASS(cite: 2018ascl.soft10016M)" (Software)
- **XCLASS** : LTE spectral line fitting  
  > "We therefore optimize model spectra to the observed spectra using the eXtended CASA Line Analysis Software Suite" (3 Spectral Line Fitting with XCLASS)
- **RADEX** online: estimate CO(3-2)/HCN(4-3) vs (1-0) ratio  
  > "a simple estimation with the RADEX (cite: 2007A&A...468..627V) radiative transfer code" (4.2.1 Ratios with CO)
- **astropy** : listed software  
  > "astropy (cite: Collaboration:2013cd; Collaboration:2018ji)" (Software)
- **Splatalogue** : line identification  
  > "with the help of Splatalogue[^1]" (2.3 Line Identification)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of lines/species detected in SSC 14 | 55 lines, 19 species | not stated | dimensionless | 2 | we detect 55 lines belonging to 19 different chemical species |
| Mean SO2 rotational temperature | 127 | not stated | K | 3 | The mean rotational temperature over the SSCs with good estimates is 127 K in SO$_2$. |
| SSC 14 SO2 Trot | 228 | +15/-20 | K | 3 | 14 / 141$^{+ 15}_{- 16}$ / 228$^{+ 15}_{- 20}$ |
| HCN tau range | 2.0-12 | not stated | dimensionless | 6 | we obtain $\tau_\mathrm{H^{13}CN} = 0.05 - 0.3$ and $\tau_\mathrm{HCN} = 2.0 - 12$. |
| HCN/H13CN range | 3.2-66 | not stated | dimensionless | 5 | We detect HCN/H$^{13}$CN with a large spread of $\sim$ one order of magnitude in the range $3.2-66$. |
| CO/HCN line ratio SSC 14 | 2.3 | +0.0/-0.1 | dimensionless | 5 | / 14  / $2.3^{+ 0.0}_{- 0.1}$  / $2.6^{+ 0.2}_{- 0.1}$ |

## Qualitative findings

- All SSCs where diagnostics possible favor PDR over XDR chemistry; no AGN signature  
  > "All SSCs favor PDR chemistry over XDR chemistry as indicated by combinations of the line ratios of HCN, HCO$^+$, HNC and CS" (5 Summary)
- Vibrationally excited HCN and HC3N imply strong IR fields trapped by high continuum opacity  
  > "The widespread existence of vibrationally excited HCN and HC$_3$N transitions implies strong IR radiation fields" (abstract)

## Claim tuples

- H: Are the SSCs dense-gas dominated? | E: CO/HCN, CO/HCO+, CO/CS ratios from XCLASS-deblended lines | R: CO/HCN ~1-10 | F: High dense gas fractions | **supported**
- H: Is an AGN/XDR influencing the SSCs? | E: Compare HCN, HCO+, HNC, CS ratios with PDR/XDR models | R: All in PDR regime | F: No XDR; AGN does not play a major role | **supported**
- H: Is the gas hot? | E: Fit Trot of SO2 and H2CS | R: mean SO2 Trot ~127 K | F: Gas temperatures high | **supported**
- H: Does HCN/HC3N trace cluster age? | E: Compare ordering with Rico-Villas dating | R: Almost inverted sequence | F: Not a reliable age tracer | **refuted**

## Reasoning

- Why this data: _not stated_
- Why this method: Line blending makes fixed-range integration overestimate intensities; XCLASS deblends and gives physical quantities  
  > "an integration over a line over a fixed velocity range will overestimate the actual intensity of the line." (3 Spectral Line Fitting with XCLASS)
- How they decided it was enough: _not stated_
- Limitation (authors): LTE assumption and fixed Tex give systematic column density errors of a factor of two; absorption may bias ratios  
  > "the derived column densities should be understood with a systematic error of a factor of two." (Appendix: XCLASS fit parameters)
- Caveat (inferred, ours): Single-pixel spectra assume beam-filling and isothermal LTE
- Caveat (inferred, ours): Fixed Tex for most species drives column densities
- Caveat (inferred, ours): Multi-component/absorption treatment is ad hoc
- Caveat (inferred, ours): Optical depth depends on adopted isotope ratios

## Reproducibility

- Data public (paper): ALMA project 2015.1.00274.S acknowledged; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA #2015.1.00274.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: SSC coordinates
- Missing: CASA/pipeline versions
- Missing: line-free channel selection
- Missing: XCLASS configuration details
- Missing: observing details
- Data volume (inferred): tens of GB (single cycle 3 Band 7 project, raw plus calibrated)
- Score (inferred): 3/5, Imaging inherited from earlier paper and XCLASS setup partly described; many details absent, but fit procedure and ratios tabulated.
- Rediscovery candidate: no, Imaging recipe is delegated to a previous paper and SSC positions come from another work.

## Links

- Method: Krieger et al. 2019 (cite: 2019ApJ...881...43K) (data reduction and imaging)
- Method: Möller et al. 2018 (cite: 2018ascl.soft10016M) (XCLASS)
- Companion: Leroy et al. 2018 (cite: 2018ApJ...869..126L) (SSC identification)
- Companion: Rico-Villas et al. 2020 (cite: 2020MNRAS.491.4573R) (HC3N super hot cores in same SSCs)

## Checks

```json
{
 "quotes": 59,
 "quotes_ok": 59,
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
  "facts": 79,
  "stated": 43,
  "rate": 0.544
 },
 "evidence_ok": true
}
```
