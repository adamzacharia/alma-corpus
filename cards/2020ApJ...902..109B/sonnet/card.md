# The ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: CO Excitation and Atomic Carbon in Star-forming Galaxies at z = 1-3

`2020ApJ...902..109B` | The Astrophysical Journal 2020 | first author: Boogaard, Leindert A. | arXiv: 2009.04348 | DOI: 10.3847/1538-4357/abb82f

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: high_z_galaxies, astrochemistry
- Question: What are the CO excitation, atomic carbon abundance and ISM conditions in a cold gas mass-selected sample of 22 star-forming galaxies at z=0.46-3.60 from ASPECS, and what do they imply for the cosmic molecular gas density?  
  > "This paper studies the CO excitation, atomic carbon emission and ISM conditions in a flux-limited sample of 22 CO and/or dust continuum detected galaxies at $z=1-3$ from the ASPECS Large Program (LP)" (1 Introduction)
- Target **22 ASPECS-LP galaxies in the HUDF (e.g. 1mm.C01, 3mm.09)**: coordinates _not stated_; z/distance z=0.46-3.60 (spectroscopic, from fits to CO/[CI] lines)  
  > "It spans redshifts from $z=0.46 - 3.60$, with the majority of the sample being at $z=1-3$." (2.2 ASPECS Sample); distance from line fits using MUSE HUDF redshifts and literature compilation as priors  
  > "It spans redshifts from $z=0.46 - 3.60$, with the majority of the sample being at $z=1-3$." (2.2 ASPECS Sample)

## Data provenance

- ALMA projects: 2016.1.00324.L
- bands: Band 3 (84-115 GHz) and Band 6 (212-272 GHz) spectral scan mosaics; VLA Ka band  
  > "The Band 3 data cube ranges from $84 - 115$ GHz, with a channel width of 7.813 MHz" (2.1 ALMA Spectroscopic Survey Data Reduction); "The Band 6 data cube spans from $212 - 272$ GHz" (2.1 ALMA Spectroscopic Survey Data Reduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: VLA D array, Ka band, two pointings (VLASPECS)  
  > "Two pointings were conducted with the D array in the Ka band" (2.3 Very Large Array Observations (VLASPECS))
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Band 3 ≈1.8"x1.5"; Band 6 ≈1.5"x1.1" (natural weighting)  
  > "The spatial resolution of the naturally weighted cube is $\approx 1.8\ensuremath{''} \times 1.5\ensuremath{''}$ (at 99.5 GHz)." (2.1 ALMA Spectroscopic Survey Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: Band 3 ≈0.2 mJy/beam per channel; Band 6 ≈0.5 mJy/beam per channel; continuum 3.8 uJy/beam (B3), 9.3 uJy/beam (B6)  
  > "The deepest parts of the continuum reach $3.8\,\mu$Jy beam$^{-1}$ in Band 3" (2.1 ALMA Spectroscopic Survey Data Reduction)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=1-0 up to 10-9 (not stated)
- Line: [CI] 3P1-3P0 and 3P2-3P1 (492.161 GHz and 809.342 GHz)
- Other facility **VLA (VLASPECS)**: CO(1-0) follow-up at z=1.99-2.70  
  > "The CO(1–0) transition in the ASPECS galaxies between $z=1.99 - 2.70$ was observed with the Karl G. Jansky Very Large Array" (2.3 Very Large Array Observations (VLASPECS))
- Other facility **Chandra 7 Ms**: X-ray AGN classification  
  > "the X-ray sources in the ASPECS sample are identified and classified using the deep *Chandra* 7 Ms data" (2.4 Multi-wavelength data & SED fitting)
- Other facility **HST and MUSE/3D-HST/Herschel**: Photometry for SED fitting, F160W radii, MUSE redshift priors  
  > "utilizing the UV – 24$\,\mu$m photometry from 3D-HST" (2.4 Multi-wavelength data & SED fitting)
- External data: HST/F160W effective radii  
  > "*HST*/F160W effective radius from (cite: vanderWel2012)" (Table 1) [from (cite: vanderWel2012)]
- External data: VLA CO(1-0) spectra/fluxes  
  > "We therefore use the spectra extracted by (cite: Riechers2020b)" (3.1 Spectral line analysis) [from (cite: Riechers2020b)]
- External data: 1.2 mm and 3 mm continuum flux densities  
  > "Flux density at 1.2 mm (cite: Gonzalez-Lopez2020; Aravena2020)." (Table 4) [from (cite: Gonzalez-Lopez2020; Aravena2020; Gonzalez-Lopez2019)]
- External data: Comparison CO ladders (BzK, SMGs, SPT, local galaxies)  
  > "The BzK-selected SFGs at $\ensuremath{\langle z \rangle}=1.5$ from (cite: Daddi2015), the SMGs at $\ensuremath{\langle z \rangle}=2.2$ from (cite: Bothwell2013)" (5.1 Individual sources) [from (cite: Daddi2015; Bothwell2013; Spilker2014)]
- Simulation/model as data: PDRTOOLBOX PDR model grids used for [CI]/CO/LIR line ratios  
  > "we use the results from the PDRTOOLBOX (cite: Kaufman2006; Pound2008)" (6.2 PDR modeling)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA (version not stated), processed as in Gonzalez-Lopez2019 (B3) and Decarli2020 (B6)  
  > "The raw ASPECS data were processed with CASA (cite: McMullin2007) as described in (cite: Gonzalez-Lopez2019) for Band 3" (2.1 ALMA Spectroscopic Survey Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ALMA ~10%; VLA ~15%  
  > "The absolute flux calibration is expected to be reliable at the $\sim 10\%$ level." (2.1 ALMA Spectroscopic Survey Data Reduction)
- self calibration: _not stated_

### Imaging

- task: TCLEAN  
  > "The visibilities were imaged using the task TCLEAN, adopting natural weighting." (2.1 ALMA Spectroscopic Survey Data Reduction)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "The visibilities were imaged using the task TCLEAN, adopting natural weighting." (2.1 ALMA Spectroscopic Survey Data Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Band 6: first-order polynomial fit to median-filtered spectrum  
  > "We first subtract the continuum in Band 6, which is determined by fitting a first order polynomial to the median filtered spectrum." (3.1 Spectral line analysis)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Cubes convolved to common 2.2" beam  
  > "convolved to a common beam size of 2.2$''$" (3.1 Spectral line analysis)
- final beam: _not stated_
- final rms: continuum 3.8 uJy/beam (B3), 9.3 uJy/beam (B6)  
  > "$9.3\,\mu$Jy beam$^{-1}$ in Band 6, with a beam size of $1.5\ensuremath{''} \times 1.1\ensuremath{''}$" (2.1 ALMA Spectroscopic Survey Data Reduction)

### Inherited from earlier work

- Band 3 data processing  
  > "processed with CASA (cite: McMullin2007) as described in (cite: Gonzalez-Lopez2019) for Band 3" (2.1 ALMA Spectroscopic Survey Data Reduction) [from (cite: Gonzalez-Lopez2019)]
- Band 6 data processing  
  > "(cite: Decarli2020) for Band 6" (2.1 ALMA Spectroscopic Survey Data Reduction) [from (cite: Decarli2020)]
- SED fitting procedure  
  > "We follow the same procedure as described in (cite: Boogaard2019)" (2.4 Multi-wavelength data & SED fitting) [from (cite: Boogaard2019)]
- LVG model  
  > "using a spherical, isothermal large velocity gradient model (LVG), following (cite: Weiss2007)" (5.3 LVG modeling) [from (cite: Weiss2007)]
- alpha_CO=3.6  
  > "We adopt an $\ensuremath{\alpha_{\mathrm{CO}}}=3.6$ $\mathrm{M}_{\odot}$(K km s$^{-1}$ pc$^{2}$)$^{-1}$ (cite: Daddi2010)" (3.2 Deriving line luminosities and molecular gas masses) [from (cite: Daddi2010)]

### Not stated but needed to reproduce (our reading)

- CASA version and exact calibration/imaging parameters (deferred to companion papers)
- Source positions used for single-pixel extraction
- Median-filter width for continuum fitting
- LVG code/priors detail and Bee algorithm settings beyond parameter ranges
- Stacking implementation details (velocity bin handling, error propagation)
- How 3 sigma upper limits and VLA spectra were combined with ALMA in the joint fit
- PDR grid ranges and which line ratios were used per source

## Analysis recipe

1. **Extract spectra and fit lines**: Single-pixel spectra from cubes convolved to 2.2"; simultaneous Gaussian fits of all CO and [CI] lines with tied redshift and width  
  > "All the lines in the continuum-free spectrum are modeled by Gaussian line shapes, whose central frequencies are tied together by a single redshift." (3.1 Spectral line analysis)
   - software: LMFIT
   - parameter: lines <3 sigma treated as upper limits  
  > "we will treat tentative lines with an integrated line flux smaller than $3\sigma$ in the VLA and ALMA data as upper limits." (4.1 Observed emission lines from CO and [CI])
   - assumption: single common line width for all lines of a source  
  > "We therefore model all the lines with a single line width." (3.1 Spectral line analysis)
   - fitting: non-linear least squares  
  > "using the non-linear least square fitting code LMFIT" (3.1 Spectral line analysis)
   - validation: fluxes consistent with channel-integrated values within 1.4xFWHM  
  > "we also compute the line fluxes by integrating the channels within $1.4\times$ the FWHM and confirm these are consistent" (4.1 Observed emission lines from CO and [CI])
2. **Stack CO ladders**: Normalise spectra by CO(2-1)/CO(3-2) flux, stack each transition in velocity space with 1/sigma weighting  
  > "stack them by taking the $1/\sigma$-weighted mean flux in each velocity bin" (5.2 Stacked line fluxes)
   - parameter: channel width 700 km/s (z~1.2), 800 km/s (z~2.5)  
  > "We take a channel width of 700 km s$^{-1}$ for the sources at $\ensuremath{\langle z \rangle}=1.2$ and 800 km s$^{-1}$ for the sources at $\ensuremath{\langle z \rangle}=2.5$" (5.2 Stacked line fluxes)
   - fitting: _not stated_
   - validation: robust to ±100 km/s channel width  
  > "We find the results are robust to modifying the channel width by $\pm 100$ km s$^{-1}$." (5.2 Stacked line fluxes)
3. **LVG modelling of CO ladders**: One- and two-component spherical isothermal LVG fits, probability-weighted mean of solutions to predict unobserved lines, averages by redshift bin  
  > "we fit the observed CO line luminosities using a one- and a two-component LVG model employing a Monte Carlo Bee algorithm" (5.3 LVG modeling)
   - parameter: log n_H2=1-7 cm^-3, Tkin=10-200 K, [CO]/[H2](dv/dr)^-1=1e-3-1e-7, r_eff=1-10000 pc; ~1e6 models per galaxy; prior excluding ladder peak beyond CO(7-6)  
  > "Limits to the parameter space are: $\log_{10}(\ensuremath{n_{\ensuremath{\mathrm{H}_{2}}}}) =1.0-7.0$ cm$^{-3}$, $\ensuremath{T_{\mathrm{kin}}}=10-200$ K" (5.3 LVG modeling)
   - fitting: Bee algorithm, chi^2 evaluation  
  > "evaluated from a $\chi^{2}$ analysis for each model" (5.3 LVG modeling)
   - validation: compared with stacks and Daddi2015  
  > "the average $r_{31} = \ensuremath{0.80 \pm 0.14}$ is fully consistent with the stacked value" (5.3 LVG modeling)
4. **Compare dust luminosity vs CO luminosity**: Estimate rest-frame 850 um luminosity from 1.2 mm and 3 mm continuum and compare to L'CO(1-0) with Scoville2016 relation  
  > "We estimate the rest frame $L_{\nu}(850\,\ensuremath{\mu}m)$ for our sources from the 1.2 mm continuum emission" (5.4 Dust continuum versus low-J CO)
   - assumption: Tdust=25 K, beta=1.8  
  > "assuming $\ensuremath{T_{\mathrm{dust}}}=25$ K and $\beta=1.8$." (Table 4)
   - fitting: _not stated_
   - validation: 3 mm-based luminosities ~10% lower, same conclusions  
  > "are on average $\approx 10\%$ lower than those from the 1.2 mm, but overall we come to the same conclusions." (5.4 Dust continuum versus low-J CO)
5. **Derive [CI] masses and abundances**: Optically thin [CI] mass from line luminosity; abundance [CI]/[H2]=M[CI]/(6 M_H2), M_H2=Mmol/1.36  
  > "where $\ensuremath{M_{\mathrm{H}_{2}}}= \ensuremath{M_{\mathrm{mol}}}/ 1.36$, not including He." (6.1 Atomic carbon abundances)
   - assumption: Tex=30 K; alpha_CO=3.6; r21=0.75, r31=0.77 for sources without CO(1-0)  
  > "we assume a typical value of $\ensuremath{T_{\mathrm{ex}}}= 30$ K" (6.1 Atomic carbon abundances)
   - fitting: _not stated_
   - validation: compared with RJ dust-based masses  
  > "we come to similar conclusions if we use the dust continuum based molecular gas masses instead" (6.1 Atomic carbon abundances)
6. **PDR modelling**: PDRTOOLBOX line ratios ([CI], CO<=4-3, LIR) used to solve for density and G_UV, bootstrapping flux ratios 1000 times  
  > "we bootstrap the observed flux ratios within their error a 1000 times and solve for the ISM density and UV radiation field for each instance." (6.2 PDR modeling)
   - software: PDRTOOLBOX
   - assumption: single PDR, no optical depth correction  
  > "assumes that the ISM of a galaxy can be described by a single PDR with a fixed input abundane" (6.2 PDR modeling)
   - fitting: median and 68% interval of bootstrap solutions  
  > "As the final density and radiation field we take the median of these values." (6.2 PDR modeling)
   - validation: compared to Valentino2018, 2020a  
  > "the galaxies occupy the same parameter space as the main-sequence galaxies" (6.2 PDR modeling)

## Software

- **CASA** : processing of raw ASPECS data and tclean imaging  
  > "The raw ASPECS data were processed with CASA" (2.1 ALMA Spectroscopic Survey Data Reduction)
- **LMFIT** 0.9.13: simultaneous Gaussian line fitting  
  > "using the non-linear least square fitting code LMFIT" (3.1 Spectral line analysis)
- **MAGPHYS** : SED fitting for M*, SFR, LIR  
  > "By modeling the SEDs using the MAGPHYS" (2.4 Multi-wavelength data & SED fitting)
- **PDRTOOLBOX** : PDR model line ratios  
  > "we use the results from the PDRTOOLBOX" (6.2 PDR modeling)
- **TOPCAT, GNUASTRO, IPython, NumPy, Matplotlib, Astropy** : general analysis software  
  > "TOPCAT (cite: Taylor2005), GNUASTRO (cite: Akhlaghi2015), IPYTHON (cite: Perez2007)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| r21 (z<2, two-component LVG) | 0.75 | 0.11 | dimensionless | 3 | ($r_{21} = \ensuremath{0.75 \pm 0.11}$) |
| r31 (z~2.5 stack) | 0.77 | 0.14 | dimensionless | 2 | we measure an average $r_{31} = \ensuremath{0.77 \pm 0.14}$ from the stack of all sources |
| r31 (z>=2, two-component LVG) | 0.80 | 0.14 | dimensionless | 3 | the average $r_{31} = \ensuremath{0.80 \pm 0.14}$ is fully consistent with the stacked value |
| r42 and r52 (z~1.2 stack) | 0.33 and 0.23 | 0.04 and 0.02 | dimensionless | 2 | $r_{42} = \ensuremath{0.33 \pm 0.04}$ and $r_{52} = \ensuremath{0.23 \pm 0.02}$ |
| r71 (z~2.5 stack) | 0.19 | 0.04 | dimensionless | 2 | The mean $r_{71} = \ensuremath{0.19 \pm 0.04}$ |
| Average [CI]/[H2] abundance (CO-based) | 1.9e-5 | 0.4e-5 | dimensionless | 5 | $(\ensuremath{\ensuremath{\mathrm{[C\, \textsc{i}]}}/[\ensuremath{\mathrm{H}_{2}}]})_{\rm CO} = \ensuremath{(1.9 \pm 0.4) \times 10^{-5}}$ |
| Average [CI]/[H2] abundance (dust-based) | 2.2e-5 | 0.3e-5 | dimensionless | 5 | $(\ensuremath{\ensuremath{\mathrm{[C\, \textsc{i}]}}/[\ensuremath{\mathrm{H}_{2}}]})_{\rm RJ} = \ensuremath{(2.2 \pm 0.3) \times 10^{-5}}$ |
| PDR density | >=1e4 | not stated | cm^-3 | 6 | the PDR models predict fairly high densities, $\ge 10^{4}$ cm$^{-3}$, for all sources |

## Qualitative findings

- Excitation higher at z>=2 than z<2; implies ~factor 2 decrease in rho_H2 at z>=2 versus earlier ASPECS results  
  > "the significantly higher excitation at $z\ge2$ implies a factor $2\times$ decrease in $\rho_{\ensuremath{\mathrm{H}_{2}}}$" (7.5 Implications for the cosmic molecular gas density)

## Claim tuples

- H: Are CO(2-1)-selected galaxies at z~1.2 as highly excited in mid-J as BzK galaxies? | E: Individual line ratios and stacking | R: Half show BzK-like excitation, average r52=0.23±0.02 lower than BzK 0.30±0.06 | F: Warm dense component not ubiquitous in gas-selected galaxies | **supported**
- H: Does CO excitation increase from z<2 to z>=2? | E: Stacking and LVG models | R: r21=0.75±0.11, r31=0.77±0.14 | F: Intrinsically higher excitation at z>=2, linked to SFR surface density | **supported**
- H: What are the [CI] abundance and densities? | E: [CI] masses and PDR modelling | R: abundance (1.9±0.4)e-5, n>=1e4 cm^-3 | F: Comparable to Milky Way and main-sequence galaxies | **supported**
- H: Does dust luminosity agree with CO(1-0) luminosity (Scoville relation)? | E: L850 vs L'CO(1-0) | R: Good for CO(3-2) sources; CO(2-1) sources lie low unless thermalized | F: Either r21 higher or relation assumptions break | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: LVG used to predict unobserved lines like interpolating a sparse SED  
  > "our procedure can be viewed as the molecular line correspondence of interpolating a sparsely sampled dust continuum SED." (5.3 LVG modeling)
- Alternative: 1/sigma^2 weighted stack (Spilker2014) rejected in favour of 1/sigma weighting to avoid weighting towards detections  
  > "We use a $1/\sigma$-weighting to avoid strongly weighting towards the detected lines" (5.2 Stacked line fluxes)
- How they decided it was enough: _not stated_
- Limitation (authors): PDR results only qualitative; small sample; selection effects cannot be fully excluded  
  > "Our results should therefore be treated as qualitative measures of the ISM density and UV radiation field." (6.2 PDR modeling)
- Caveat (inferred, ours): Two-component LVG poorly constrained by 2-4 lines
- Caveat (inferred, ours): Low-J excitation relies on VLA CO(1-0) with marginal S/N
- Caveat (inferred, ours): Common-width fitting may bias errors
- Caveat (inferred, ours): Small number of sources per stack

## Reproducibility

- Data public (paper): ALMA data from Large Program 2016.1.00324.L; VLA program 19B-131  
  > "ADS/JAO.ALMA#2016.1.00324.L" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Calibration/imaging details in companion papers
- Missing: Source positions
- Missing: LVG code
- Missing: VLA spectra from Riechers2020b
- Data volume (inferred): large (full ASPECS Band 3 and Band 6 cubes, several hundred GB raw)
- Score (inferred): 6/5, Data public and recipe fairly clear, but processing deferred to companion papers and LVG/stacking details partly unstated.
- Rediscovery candidate: no, Requires ASPECS cubes processed in companion papers plus VLA data and bespoke LVG code.

## Links

- Method: (cite: Gonzalez-Lopez2019) (Band 3 data reduction and line search)
- Method: (cite: Decarli2020) (Band 6 data reduction)
- Method: (cite: Weiss2007) (LVG model)
- Companion: (cite: Riechers2020b) (VLASPECS CO(1-0) data)
- Companion: (cite: Boogaard2019) (ASPECS galaxy properties/SED fits)
- Companion: (cite: Gonzalez-Lopez2020) (1.2 mm continuum)
- Related: ASPECS
- Related: VLASPECS
- Related: COLDz
- Related: MUSE HUDF survey

## Checks

```json
{
 "quotes": 76,
 "quotes_ok": 76,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 89,
  "stated": 59,
  "rate": 0.663
 },
 "evidence_ok": true
}
```
