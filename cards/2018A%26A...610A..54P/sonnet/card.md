# The ALMA-PILS Survey: Formaldehyde deuteration in warm gas on small scales toward IRAS 16293-2422 B

`2018A&A...610A..54P` | Astronomy and Astrophysics 2018 | first author: Persson, M. V. | arXiv: 1711.05736 | DOI: 10.1051/0004-6361/201731684

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: astrochemistry, star_formation
- Question: What are the excitation temperature, column densities and deuterium fractionation of formaldehyde isotopologues in warm gas on small scales toward IRAS 16293-2422 B, and how do they compare with single dish results and chemical models?  
  > "We determine the excitation temperature, abundances and fractionation level of several formaldehyde isotopologues, including its deuterated forms." (abstract)
- Target **IRAS 16293-2422 B**: coordinates offset position RA 16h32m22.58s, Dec -24d28m32.8s (J2000), ~0.5" SW of continuum peak of B  
  > "located in the $\rho$ Ophiuchus star forming region at a distance of 120 pc (cite: loinard08)" (Introduction); "Located at $\alpha_\mathrm{J2000}$=16$^\mathrm{h}$32$^\mathrm{m}$22$''$58 $\delta_\mathrm{J2000}$=$-$24$^{\circ}$28$^\prime$32$''$8 it is $\sim$0.5$''$ offset" (2 Observations and Analysis); z/distance 120 pc  
  > "located in the $\rho$ Ophiuchus star forming region at a distance of 120 pc (cite: loinard08)" (Introduction); "Located at $\alpha_\mathrm{J2000}$=16$^\mathrm{h}$32$^\mathrm{m}$22$''$58 $\delta_\mathrm{J2000}$=$-$24$^{\circ}$28$^\prime$32$''$8 it is $\sim$0.5$''$ offset" (2 Observations and Analysis); distance from Loinard et al. 2008 (cite: loinard08)  
  > "located in the $\rho$ Ophiuchus star forming region at a distance of 120 pc (cite: loinard08)" (Introduction); "Located at $\alpha_\mathrm{J2000}$=16$^\mathrm{h}$32$^\mathrm{m}$22$''$58 $\delta_\mathrm{J2000}$=$-$24$^{\circ}$28$^\prime$32$''$8 it is $\sim$0.5$''$ offset" (2 Observations and Analysis)

## Data provenance

- ALMA projects: 2013.1.00278.S
- bands: Band 7  
  > "an ALMA band 7 unbiased spectral line survey with complete coverage between 329.15 and 362.90 GHz at 0.244 MHz resolution" (2 Observations and Analysis)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12 m main array plus ACA 7 m  
  > "The observations include both the main array of 12 m dishes, and the 7 m dishes of the Atacama Compact Array (ACA)." (2 Observations and Analysis)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.5" FWHM synthesized beam  
  > "a synthesized beam with a FWHM of 0.5$''$" (2 Observations and Analysis)
- max recoverable scale: ~13"  
  > "with a maximum recoverable scale of $\sim$13$''$" (2 Observations and Analysis)
- sensitivity: RMS 4-8 mJy/beam km/s  
  > "The final spectral image cubes have a RMS of 4–8 mJy beam$^{-1}$ km s$^{-1}$" (2 Observations and Analysis)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: PILS survey data  
  > "This study is based on observations from the Protostellar Interferometric Line Survey (PILS" (2 Observations and Analysis)
- Line: H2CO and isotopologues (H2(13)CO, H2C(18)O, H2C(17)O, HDCO, HDC(18)O, D2CO, D2(13)CO) multiple rotational lines, see Appendix table (329-363 GHz)
- External data: Spectroscopic data and partition functions for all formaldehyde forms from CDMS  
  > "The transition frequencies and other data (including partition function values) of all forms of formaldehyde were taken from the CDMS database" (2.1 Laboratory spectroscopy data) [from (cite: muller01; muller05)]
- External data: Methanol column density and D/H toward IRAS 16293 B  
  > "Using the column density derived for methanol by (cite: jorgensen17) the H$_{2}$CO/CH$_{3}$OH ratio is 0.19" (3.3 Formaldehyde and methanol) [from (cite: jorgensen17)]
- External data: Chemical model ratios vs time  
  > "the D/H ratio in HDCO is 4.1% and 0.18% for D$_{2}$CO (Table 7 in (cite: taquet14))" (3.2.2 Models) [from (cite: taquet14)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ~5%  
  > "a flux calibration uncertainty of $\sim5\%$" (2 Observations and Analysis)
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
- array combination: ACA included to fill short baselines  
  > "The inclusion of the ACA observations fills in the shorter baselines" (2 Observations and Analysis)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Observing conditions, calibration and imaging  
  > "For details, including observing conditions, calibration and imaging, see (cite: jorgensen16a)." (2 Observations and Analysis) [from (cite: jorgensen16a)]
- Continuum correction of column densities  
  > "The column densities are corrected for the continuum emission from the surrounding dense dust (cite: jorgensen16a)." (2.2 Abundances) [from (cite: jorgensen16a)]
- Extraction of offset spectrum and LTE+CASSIS method  
  > "Similar to the analysis presented in (cite: lykke17), (cite: coutens16) and (cite: ligterink17), the spectrum from an offset position toward source B was extracted." (2 Observations and Analysis) [from (cite: lykke17; coutens16; ligterink17)]

### Not stated but needed to reproduce (our reading)

- Imaging details (CASA version, weighting, tclean settings) only in PILS paper
- Exact line-by-line fit windows and continuum level used for the correction
- Source size / beam filling assumption for LTE model
- Calibration pipeline/version
- Details of combining asymmetric errors
- CASSIS version

## Analysis recipe

1. **Extract spectrum at offset position**: Spectrum extracted at position ~0.5" SW of continuum peak of B to avoid absorption and continuum optical depth  
  > "toward the continuum peak, lines are affected by varying degrees of absorption and continuum optical depth" (2 Observations and Analysis)
   - fitting: _not stated_
   - validation: _not stated_
2. **Constrain Tex and Ntot of HDCO**: LTE synthetic spectrum compared with observed; chi2 grid in Tex and column density, minimum taken as best fit  
  > "For HDCO a full grid in excitation temperature and column density is calculated and the coordinates of the minimum $\chi^2$ are taken as the best estimates." (2.2 Abundances)
   - software: CASSIS
   - parameter: line width 1.15 km/s FWHM, vsys 2.7 km/s  
  > "A line width of 1.15 km s$^{-1}$ (FWHM) and system velocity of 2.7 km s$^{-1}$ were used" (2.2 Abundances)
   - assumption: LTE; only optically thin, unblended lines used  
  > "Only optically thin lines are included in the analysis to minimize any opacity effects." (3 Results)
   - fitting: chi2 minimization; delta chi2=2.3 region taken as 1 sigma  
  > "The region with an added $\Delta\chi^2=2.3$ is taken as the $1\sigma$ error in $T_\mathrm{ex}$ and $N_\mathrm{tot}$ for HDCO" (3.1 Excitation temperature)
   - validation: Model reproduces all isotopologue lines; upper limit of a non-detected HDCO line used as constraint  
  > "This temperature, together with the constrained column densities reproduce the lines for all isotopologues well." (3.1 Excitation temperature)
3. **Column densities of all isotopologues**: Fix Tex from HDCO; vary column density to match integrated line fluxes of optically thin unblended lines via chi2; uncertainty from lower and upper Tex bounds (93 and 119 K)  
  > "The uncertainty in abundance is estimated by finding the minimum $\chi^2$ for the lower and upper bound excitation temperature (i.e. 93 and 119 K" (2.2 Abundances)
   - software: CASSIS
   - fitting: chi2 on integrated line flux  
  > "calculating the integrated line flux for each line not affected by optical depth effects or significant blending by other species and comparing to the observed line flux by calculating the $\chi^2$ estimate." (Abundances)
   - validation: HDC18O/H2C18O agrees with HDCO/H2CO  
  > "it agrees with the main isotopologues HDCO/H$_{2}$CO ratio of 6.8% (D/H ratio of 3.4%), confirming the method used for constraining the column densities." (3.2.1 Measured D/H ratios)
4. **Derive ratios and D/H**: Error-propagated column density ratios; D/H = HDCO/H2CO x0.5, D2CO/HDCO x2, sqrt(D2CO/H2CO); combine multiple estimates  
  > "D/H is given by HDCO/H$_{2}$CO$\times0.5$, D$_{2}$CO/HDCO$\times$2 and $\sqrt{\mathrm{D_2CO/H_2CO}}$" (3.2.1 Measured D/H ratios)
   - fitting: _not stated_
   - validation: _not stated_
5. **Compare with chemical model**: Compare ratios with Taquet et al. 2014 time-dependent model  
  > "are best reproduced by the model at $t=1.1\times10^5$ years" (3.2.2 Models)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASSIS** : Support tool to check line blending; LTE synthetic spectra  
  > "CASSIS[^2] was used as a support tool to e.g. check for possible line blending from other species" (2.2 Abundances)
- **Astropy** : Python package used in the research  
  > "This research made use of Astropy and Astroquery" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Excitation temperature (HDCO) | 106 | ±13 | K | 2 | The excitation temperature was determined to be $106\pm13$ K by fitting the spectrum of HDCO |
| HDCO/H2CO | 6.5 | ±1 | % | 4 | HDCO/H$_2$CO=6.5$\pm$1%, D$_2$CO/HDCO=12.8$^{+3.3}_{-4.1}$% |
| D2CO/HDCO | 12.8 | +3.3/-4.1 | % | 4 | D$_{2}$CO / HDCO / 12.8$^{+3.3}_{-4.1}$ % |
| D2CO/H2CO | 0.6(4) | ±0.1 | % | 4 | D$_2$CO/H$_2$CO=0.6(4)$\pm$0.1% |
| H2CO column density | 1.9e18 | +0.1/-0.2 e18 | cm^-2 | 3 | H$_{2}$CO        / 1.9$^{+0.1}_{-0.2}$ $\times$10$^{18}$ |
| HDCO column density | 1.3e17 | ±0.2e17 | cm^-2 | 3 | HDCO             / 1.3$\pm0.2\,\times$10$^{17}$ |
| 16O/18O | 805 | +43/-79 | dimensionless | 4 | $^{16}$O/$^{18}$O=805$^{+43}_{-79}$ |
| 12C/13C | 56 | +8/-11 | dimensionless | 4 | $^{12}$C/$^{13}$C=56$^{+8}_{-11}$ |
| 18O/17O | 3.2 | +0.2/-0.3 | dimensionless | 4 | $^{18}$O/$^{17}$O=3.2$^{+0.2}_{-0.3}$ |

## Qualitative findings

- H2C17O and D2(13)CO detected for the first time in the ISM  
  > "Numerous isotopologues of formaldehyde are detected, among them H$_2$C$^{17}$O, and D$_2^{13}$CO for the first time in the ISM." (abstract)

## Claim tuples

- H: Warm-gas HDCO/H2CO on small scales is lower than single dish values | E: LTE analysis of optically thin lines in PILS data at offset position near B | R: HDCO/H2CO=6.5±1% versus 14-33% from single dish | F: Single dish ratios overestimate inner warm region deuteration | **supported**
- H: D2CO/HDCO follows the statistical expectation (1/4 HDCO/H2CO) | E: Compared measured ratios with Eq. 1 | R: D2CO/HDCO about twice HDCO/H2CO | F: More complex interpretation than simple statistics needed; consistent with formation after CO freeze-out | **supported**
- H: Observed ratios constrain evolutionary stage via chemical models | E: Compared with Taquet et al. 2014 model | R: Best reproduced at t=1.1e5 yr | F: Source is early Class 0 | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Interferometric data probe small warm scales and weaker minor isotopologue lines reduce optical depth issues  
  > "The higher sensitivity makes it possible to detect weaker lines of minor isotopologues where optical depth effects are less important." (Introduction)
- Alternative: Continuum peak not used because of absorption and continuum optical depth  
  > "toward the continuum peak, lines are affected by varying degrees of absorption and continuum optical depth" (2 Observations and Analysis)
- How they decided it was enough: _not stated_
- Limitation (authors): Uncertainty in abundance dominated by Tex uncertainty; single temperature assumed  
  > "The uncertainty in abundance is dominated by the uncertainty in excitation temperature." (3.2 Column densities and ratios)
- Caveat (inferred, ours): Single Tex from HDCO applied to all isotopologues
- Caveat (inferred, ours): H2CO main lines optically thick, so H2CO column rests on one line plus one limit
- Caveat (inferred, ours): LTE assumed at high densities with no source-size treatment stated
- Caveat (inferred, ours): No comparison with non-LTE

## Reproducibility

- Data public (paper): ALMA project 2013.1.00278.S cited; public status not stated explicitly  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00278.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Calibrated/imaged PILS cubes (Jorgensen et al. 2016)
- Missing: Exact fit settings and continuum values
- Data volume (inferred): ~100s GB raw; PILS cubes tens of GB
- Score (inferred): 5/5, Analysis method clear and line tables given, but imaging inherited from PILS paper and several fit details missing.
- Rediscovery candidate: no, Requires PILS reduced cubes and CASSIS fit details not given in the paper.

## Links

- Method: Jørgensen et al. 2016 (cite: jorgensen16a) (PILS survey observations, calibration, imaging)
- Method: (cite: lykke17; coutens16; ligterink17) (Same LTE analysis approach)
- Companion: (cite: jorgensen17) (Methanol and other PILS molecules)
- Related: ALMA-PILS

## Checks

```json
{
 "quotes": 54,
 "quotes_ok": 54,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 36,
  "rate": 0.507
 },
 "evidence_ok": true
}
```
