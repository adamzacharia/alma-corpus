# Successive deuteration in low-mass star-forming regions: The case of D<SUB>2</SUB>-methanol (CHD<SUB>2</SUB>OH) in IRAS 16293-2422

`2022A&A...659A..69D` | Astronomy and Astrophysics 2022 | first author: Drozdovskaya, Maria N. | arXiv: 2201.07268 | DOI: 10.1051/0004-6361/202142863

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: astrochemistry, star_formation
- Question: What is the column density and excitation temperature of CHD2OH in IRAS 16293-2422 A and B, and how does successive deuteration compare across molecules, sources, experiments and comet 67P?  
  > "The newly computed line list and partition function are used to search for CHD$_{2}$OH towards IRAS 16293-2422 A and B in data from the Atacama Large Millimeter/submillimeter Array (ALMA) Protostellar Interferometric Line Survey (PILS)." (abstract)
- Target **IRAS 16293-2422 B (one-beam SW offset)**: coordinates 16h32m22.58s, -24d28'32.80'' (J2000)  
  > "The coordinates of this position are RA, Dec (J2000) of 16h32m22.58s, -24d28$\ensuremath{'}$32.80$\ensuremath{''}$." (2.3 Spectral analysis); "IRAS 16293-2422 is a frequently studied, well-characterized nearby ($141$ pc; (cite: Dzib2018)) low-mass protostellar system." (Introduction); z/distance 141 pc  
  > "The coordinates of this position are RA, Dec (J2000) of 16h32m22.58s, -24d28$\ensuremath{'}$32.80$\ensuremath{''}$." (2.3 Spectral analysis); "IRAS 16293-2422 is a frequently studied, well-characterized nearby ($141$ pc; (cite: Dzib2018)) low-mass protostellar system." (Introduction); distance from Dzib2018  
  > "The coordinates of this position are RA, Dec (J2000) of 16h32m22.58s, -24d28$\ensuremath{'}$32.80$\ensuremath{''}$." (2.3 Spectral analysis); "IRAS 16293-2422 is a frequently studied, well-characterized nearby ($141$ pc; (cite: Dzib2018)) low-mass protostellar system." (Introduction)
- Target **IRAS 16293-2422 A (one-beam NE offset)**: coordinates 16h32m22.90s, -24d28'36.20'' (J2000)  
  > "with coordinates RA, Dec (J2000) of 16h32m22.90s, -24d28$\ensuremath{'}$36.20$\ensuremath{''}$ and $v_{\text{LSR}}=0.8$ km s$^{-1}$" (Spectral analysis); z/distance 141 pc  
  > "IRAS 16293-2422 is a frequently studied, well-characterized nearby ($141$ pc; (cite: Dzib2018)) low-mass protostellar system." (Introduction); distance from Dzib2018  
  > "IRAS 16293-2422 is a frequently studied, well-characterized nearby ($141$ pc; (cite: Dzib2018)) low-mass protostellar system." (Introduction)

## Data provenance

- ALMA projects: 2013.1.00278.S
- bands: Band 7, 329-363 GHz  
  > "These data cover the $329-363$ GHz frequency range (ALMA Band $7$)" (2.1 Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12m array plus 7m ACA  
  > "The observations are a combination of the 12m array and the 7m Atacama Compact Array (ACA)" (2.1 Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.5'' (70 au), uniform circular restoring beam  
  > "at a spatial resolution of $\sim0.5\ensuremath{''}$ ($70$ au; the applied uniform circular restoring beam)" (2.1 Observations)
- max recoverable scale: ~13''  
  > "sampling extended structures up to $\sim13\ensuremath{''}$ ($\sim2~000$ au; largest recoverable size)" (2.1 Observations)
- sensitivity: 8-10 mJy/beam/channel; channel 0.2 km/s (0.244 MHz)  
  > "spectral resolution of $0.2$ km s$^{-1}$ ($0.244$ MHz) and reached a sensitivity of $\sigma=8-10$ mJy beam$^{-1}$ channel$^{-1}$" (2.1 Observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: PILS survey, PI Jes K. Jørgensen, Cycle 2  
  > "project-id: 2013.1.00278.S, PI: Jes K. Jørgensen) carried out with ALMA in Cycle $2$" (2.1 Observations)
- Line: CHD2OH 105 unique non-blended optically thin lines used in fit (e.g. 348.710 GHz) (329-363 GHz range; 348.710 GHz for moment map)
- External data: CH3OH column density at B: (1.0±0.2)e19 cm-2; at A: (1.3±0.4)e19 cm-2  
  > "The last two rows give the methanol column densities adopted for the calculations of D/H ratios and the corresponding references." (Table 2) [from Jorgensen2018 (B); Manigand2020 (A)]
- External data: Rotation-torsion line position analysis of CHD2OH used to build the spectroscopic database  
  > "The results of the global line position analysis of (cite: Coudert2021) were used to build a spectroscopic database for CHD$_{2}$OH." (2.2 Spectroscopy) [from Coudert2021]
- External data: Dipole moment components mu_x=-1.37 and mu_z=0.8956 D  
  > "The values are $\mu_{x}=-1.37$ and $\mu_{z}=0.8956$ D as reported by (cite: Amano1981)." (2.2 Spectroscopy) [from Amano1981]
- External data: Reference-spectrum molecule Tex and N from other PILS papers; D/H of other molecules, other protostars, lab and Rosetta data used for comparison  
  > "This spectrum contains computed emission lines from all molecules detected with the ALMA-PILS survey at this position at their determined excitation temperatures ($T_{\text{ex}}$) and column densities ($N$)" (2.3 Spectral analysis) [from PILS papers (Jorgensen2016, Jorgensen2018, etc.); Paquette2021; Drozdovskaya2021]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 5% calibration uncertainty  
  > "the data themselves (calibration uncertainty of $5\%$)" (3.1 Line profiles)
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
- continuum subtraction: Continuum-subtracted following Jorgensen2016 methodology  
  > "continuum-subtracted (based on methodology described in (cite: Jorgensen2016)) data cube" (2.3 Spectral analysis)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.5'' circular  
  > "the applied uniform circular restoring beam" (2.1 Observations)
- final rms: 8-10 mJy/beam/channel  
  > "reached a sensitivity of $\sigma=8-10$ mJy beam$^{-1}$ channel$^{-1}$" (2.1 Observations)

### Inherited from earlier work

- Data set and its reduction  
  > "The full details about the data set and its reduction are available in (cite: Jorgensen2016)." (2.1 Observations) [from Jorgensen2016]
- Pessimistic errors of 10% on Tex and 20% on N  
  > "pessimistic errors of $10\%$ and $20\%$ on $T_{\text{ex}}$ and $N$, respectively, are adopted" (3.1 Line profiles) [from Jorgensen2018]
- Source A FWHM 2.2 km/s and position  
  > "only FWHM is changed to $2.2$ km s$^{-1}$ as deduced from previous analysis of this position (cite: Manigand2020)." (2.3 Spectral analysis) [from Manigand2020]
- VINE map method  
  > "This method was developed by (cite: Calcutt2018a) and produces so-called Velocity-corrected INtegrated emission (VINE) maps." (3.2 Integrated intensity maps) [from Calcutt2018a]

### Not stated but needed to reproduce (our reading)

- Exact PILS calibrated cubes and continuum-subtraction details (in Jorgensen2016)
- Thinning/autocorrelation values and random seeds for emcee
- Custom Python LTE/MCMC code not released as a package
- Likelihood has no noise term (unweighted residuals)
- Data file of the CHD2OH line list is at CDS only
- Selection of specific 105 line frequencies requires visual blending inspection

## Analysis recipe

1. **Build CHD2OH spectroscopy**: Compute rotation-torsion lines up to J=26 for 0<=vt<=2 from Coudert2021 global fit; compute partition function; JPL-format catalog with intensity cutoff  
  > "All rotation-torsion lines within and between the first three torsional states, $0\leq v_{t}\leq2$, were computed up to $J=26$." (2.2 Spectroscopy)
   - parameter: LOGSTR0 = LOGSTR1 = -9; minimum ERR 10 kHz; lines below 500 GHz  
  > "LOGSTR0 and LOGSTR1 are two dimensionless constants both set to $-9$." (2.2 Spectroscopy)
   - fitting: _not stated_
   - validation: Compared with earlier line list of Mukhopadhyay2016a; 32 transitions differ by >0.5 MHz  
  > "lists the $32$ transitions with a frequency discrepancy larger than $0.5$ MHz." (2.2 Spectroscopy)
2. **Select usable lines**: Extract single-position spectrum, shift by vLSR, overlay reference spectrum, visually remove blended lines and optically thick lines (tau>0.1 at Tex=50 or 300 K, N=1.3e17)  
  > "These are assumed to be lines that have $\tau>0.1$ either at $T_{\text{ex}}=50$ or $300$ K at $N=1.3\times10^{17}$ cm$^{-2}$" (2.3 Spectral analysis)
   - software: custom Python scripts
   - parameter: vLSR=2.7 km/s for B, 0.8 km/s for A; 554 lines covered, 525 unique, 105 retained  
  > "There are in total $554$ lines of CHD$_{2}$OH covered in the observed ALMA-PILS frequency range, of which $525$ have unique rest frequencies." (2.3 Spectral analysis)
   - assumption: LTE  
  > "The computation is performed under the local thermal equilibrium (LTE) approximation." (2.3 Spectral analysis)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit Tex and N with MCMC**: LTE synthetic spectrum with emcee; two runs (300 walkers x 250 steps, then 300 walkers x 1000 steps near the best fit); 10% burn-in; thinning 0.3%  
  > "The second has $300$ walkers for each parameter with each taking $1000$ steps, but now initiated in a small region around the best-fitting $T_{\text{ex}}$ and $N$ of the first run." (2.3 Spectral analysis)
   - software: emcee
   - parameter: Fixed: beam 0.5'', source size 0.5'', FWHM 1 km/s (B) or 2.2 km/s (A); priors Tex 50-400 K, N 1e13-1e18 cm-2  
  > "Several parameters are fixed: beam size of $0.5\ensuremath{''}$, source size of $0.5\ensuremath{''}$, and line full width half-maximum (FWHM) of $1$ km s$^{-1}$." (2.3 Spectral analysis)
   - assumption: Beam-filling factor 0.5; Sobolev/LVG optical depth correction  
  > "the dilution of the observed emission is accounted for by the beam-filling factor: $\eta_{\text{BF}} = \text{source size}^{2} / \left( \text{source size}^{2} + \text{beam size}^{2} \right) = 0.5$" (2.3 Spectral analysis)
   - fitting: Likelihood: -1/2 sum of squared residuals over +-FWHM/2 around each of the 105 lines; flat priors; stretch moves; best fit = 50th percentile  
  > "The walkers undertake the default “stretch moves” of EMCEE" (2.3 Spectral analysis)
   - validation: Acceptance fraction 70%; corner plots; autocorrelation times; fixed Tex=150 and 300 K runs  
  > "the mean acceptance fraction of the $300$ walkers is $70\%$" (2.3 Spectral analysis)
4. **Derive D/H ratios**: Divide N(CHD2OH) by N(CH3OH) with statistical correction (3 (D/H)^2)  
  > "\frac{\text{CHD}_{2}\text{OH}}{\text{CH}_{3}\text{OH}} &= 3 \left( \frac{\text{D}}{\text{H}} \right) _{\text{CH}_{3}\text{OH}}^{2}" (Statistical corrections)
   - assumption: 20% error on each N gives 30% on ratio  
  > "the $20\%$ error on each $N$, which gives an error of $30\%$ on the ratio of two column densities" (4.1 Deuteration in IRAS 16293-2422)
   - fitting: _not stated_
   - validation: _not stated_
5. **Make VINE moment-0 maps**: Integrate over 25 bins (~5 km/s) with per-pixel rest frequency from the 337.519 GHz methanol line velocity map  
  > "Here, the integration is performed over $25$ spectral bins, corresponding to a $\sim5$ km s$^{-1}$ range" (3.2 Integrated intensity maps)
   - fitting: _not stated_
   - validation: Compared with classical constant-vLSR moment maps  
  > "Both of these points indicate that the VINE map is doing a better job at recovering the line emission near source A." (Integrated intensity maps details)

## Software

- **emcee** : MCMC fitting of Tex and N  
  > "a newly developed routine based on the Markov chain Monte Carlo (MCMC) Python package EMCEE" (2.3 Spectral analysis)
- **custom Python scripts** : Spectrum analysis and LTE modelling  
  > "it is analyzed with custom-made Python scripts" (2.3 Spectral analysis)
- **CASSIS** : LTE model code based on its formalisms  
  > "The code behind the LTE model is based on the formalisms used in CASSIS." (2.3 Spectral analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Tex of CHD2OH, I16293B | 90.0 | ±9 | K | 3 | $T_{\text{ex}}$ (K) / $90.0\pm9$ / $127\pm13$ |
| N(CHD2OH), I16293B | 1.78e17 | ±0.36e17 | cm-2 | 3 | $(1.78\pm0.36)\times10^{17}$ |
| Tex of CHD2OH, I16293A | 127 | ±13 | K | 3 | $T_{\text{ex}}$ (K) / $90.0\pm9$ / $127\pm13$ |
| N(CHD2OH), I16293A | 2.22e17 | ±0.44e17 | cm-2 | 3 | $(2.22\pm0.44)\times10^{17}$ |
| D/H of CH3OH, B | 7.7% | ±1.2% | percent | 4 | yield high D/H ratios of CHD$_{2}$OH in IRAS 16293-2422 A and B of $7.5\pm1.1\%$ and $7.7\pm1.2\%$, respectively. |
| D/H of CH3OH, A | 7.5% | ±1.1% | percent | 4 | yield high D/H ratios of CHD$_{2}$OH in IRAS 16293-2422 A and B of $7.5\pm1.1\%$ and $7.7\pm1.2\%$, respectively. |
| N(CHD2OH) at fixed Tex=150 K, B | 1.07e17 | ±0.21e17 | cm-2 | 3 | for the $T_{\text{ex}}=150$ K model the best-fitting column density is $N=(1.07\pm0.21)\times10^{17}$ cm$^{-2}$ |
| N(CHD2OH) at fixed Tex=300 K, B | 6.62e16 | ±1.32e16 | cm-2 | 3 | $N=(6.62\pm1.32)\times10^{16}$ cm$^{-2}$ |
| Mean D/H of di-deuterated relative to mono-deuterated | 20.7 | ±6.2 | percent | 0 | Di-deuterated molecular D/H ratios span $10-33\%$ with a mean of $20.7\pm6.2\%$. |
| CHD2OH/CH3OH ratio, B | 1.78e-2 | ±0.5e-2 | dimensionless | 4 | this ratio is $1.78\pm0.5\times10^{-2}$ and $1.71\pm0.6\times10^{-2}$ for source B and A, respectively |

## Qualitative findings

- IRAS 16293-2422 is not abnormally deuterium-rich compared with other low-mass protostars.  
  > "Fig. [5] does not yield enough evidence to support I16293B being abnormally deuterium-rich among low-mass protostars." (4.2 Comparison)
- CHD2OH emission is compact towards A and B at the present resolution.  
  > "CHD$_{2}$OH emission is compact towards A and B" (3.2 Integrated intensity maps)

## Claim tuples

- H: CHD2OH can be accurately quantified in I16293 A and B with new spectroscopy | E: MCMC LTE fit of 105 unblended optically thin lines in ALMA-PILS spectra | R: B: N=1.78e17, Tex=90 K; A: N=2.22e17, Tex=127 K; D/H 7.7% and 7.5% | F: High D/H of CHD2OH in both sources | **supported**
- H: Di-deuterated molecules have higher D/H than mono-deuterated ones | E: Compare D/H chains of several molecules in I16293B | R: Di/mono ratios 14-25%, mean 20.7±6.2% | F: Trend holds consistently and resembles lab H-D substitution | **supported**
- H: I16293 is more deuterated than other low-mass protostars | E: Compare D/H with L483, SVS13-A, NGC1333 sources | R: No systematic differences | F: Not abnormally D-rich | **supported**
- H: Protostellar D/H matches comet 67P | E: Compare with ROSINA/COSIMA ratios | R: Cometary D2O, CHD2OH, NH2D, HDS lower by at least an order of magnitude | F: Solar natal cloud may have had lower D, been warmer, or been reprocessed | **partially**

## Reasoning

- Why this data: Proximity and narrow lines enable spatially resolved, sensitive searches for minor species  
  > "The proximity of IRAS 16293-2422 enables spatially resolved observations at high sensitivity to be carried out, making it an optimal target for searches for minor chemical constituents." (Introduction)
- Why this method: _not stated_
- Alternative: Fixed Tex=150 and 300 K models tested; lower D/H by at most 1.6 but conclusions unchanged  
  > "by at most a factor of $1.6$); however, the conclusions of this paper are not changed" (3.1 Line profiles)
- How they decided it was enough: _not stated_
- Limitation (authors): MCMC errors underestimate true uncertainty; LTE single Tex assumption; resolution cannot separate A1 and A2  
  > "These errors are very small for well-converged runs and do not take all origins of uncertainty in observations into account" (2.3 Spectral analysis)
- Limitation (authors): Tex lower than ~300 K for methanol isotopologs; origin unclear (physics or spectroscopy)  
  > "whether this is reflecting actual differences between the methanol isotopologs or rather uncertainties in the spectroscopy for these transitions remains unclear" (3.1 Line profiles)
- Caveat (inferred, ours): Likelihood is unweighted and ignores noise, so MCMC errors are not meaningful
- Caveat (inferred, ours): Single-Tex LTE and fixed source size 0.5'' assumed
- Caveat (inferred, ours): D/H depends on the CH3OH column from 18O isotopolog with assumed isotope ratio
- Caveat (inferred, ours): Comparisons with other protostars use inhomogeneous analyses

## Reproducibility

- Data public (paper): PILS data under project 2013.1.00278.S; line list at CDS  
  > "The line list is published as an electronic Table at the Centre de Données astronomiques de Strasbourg (CDS)" (2.2 Spectroscopy)
- Products in archive: _not stated_
- Code: _not stated_
- Missing: Custom MCMC code not released
- Missing: Line selection (105 frequencies) list not given in text
- Missing: Calibrated PILS cubes require archive/Jorgensen2016 reduction
- Data volume (inferred): tens of GB (PILS Band 7 12m+ACA, single-position spectrum analysis)
- Score (inferred): 3/5, Public data and clear fitting recipe, but custom code, line list selection and calibrated cubes are not provided.
- Rediscovery candidate: no, Requires custom code, the new CDS line list and PILS reduction details; recipe is incomplete although results are numeric.

## Links

- Method: Jorgensen2016 (PILS survey data and reduction)
- Method: Coudert2021 (CHD2OH spectroscopic analysis)
- Method: Calcutt2018a (VINE map method)
- Method: ForemanMackey2013 (emcee)
- Companion: Jorgensen2018 (PILS methanol isotopologs and D/H in I16293B)
- Companion: Manigand2020 (PILS analysis of source A)
- Related: ALMA-PILS
- Related: TIMASSS
- Related: Rosetta ROSINA/COSIMA

## Checks

```json
{
 "quotes": 70,
 "quotes_ok": 70,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 84,
  "stated": 50,
  "rate": 0.595
 },
 "evidence_ok": true
}
```
