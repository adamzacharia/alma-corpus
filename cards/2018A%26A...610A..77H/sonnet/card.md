# An ALMA study of the Orion Integral Filament. I. Evidence for narrow fibers in a massive cloud

`2018A&A...610A..77H` | Astronomy and Astrophysics 2018 | first author: Hacar, A. | arXiv: 1801.01500 | DOI: 10.1051/0004-6361/201731894

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism
- Question: Are all filaments bundles of fibers? Does the massive Orion ISF contain fibers like low-mass filaments, and what are their properties?  
  > "Are all filaments bundles of fibers? To address this question, we have investigated the gas organization within the paradigmatic Integral Shape Filament (ISF) in Orion." (abstract)
- Target **Orion Integral Shape Filament (OMC-1 and OMC-2/3)**: coordinates _not stated_; z/distance 414 pc  
  > "assuming a distance of D=414 pc" (3.3 Linear masses and stability); distance from not stated explicitly (resolution quoted with (cite: MEN07))  
  > "assuming a distance of D=414 pc" (3.3 Linear masses and stability)

## Data provenance

- ALMA projects: 2015.1.00669.S
- bands: Band 3  
  > "we observed the N$_2$H$^+$ (1-0) line emission in Band 3" (2 ALMA Cycle-3 observations)
- frequencies and spectral setup: N2H+ (1-0) at 30 kHz (0.1 km/s); three 1.8 GHz continuum windows at ~93, 104, 106 GHz  
  > "Three additional broad-band, 1.8 GHz wide spectral windows were observed simultaneously covering the continuum centred at $\sim$ 93, 104, and 106 GHz." (2 ALMA Cycle-3 observations)
- continuum bandwidth: _not stated_
- arrays: ALMA 12m array  
  > "in the most compact configuration of the ALMA 12m array (C36-1 and C36-2)" (2 ALMA Cycle-3 observations)
- configurations: _not stated_
- baselines: 15.1 to 310 m  
  > "with baselines between 15.1 and 310 meters" (2 ALMA Cycle-3 observations)
- angular resolution: ~3.5"x3.0" native; 4.5" final circular beam (0.009 pc)  
  > "(at $\sim3.5"\times3.0"$ resolution) was convolved into a final circular beam ($\theta_{FWHM}$) of 4.5"" (2 ALMA Cycle-3 observations)
- max recoverable scale: _not stated_
- sensitivity: 25 mJy/beam at 0.1 km/s; 0.17 K  
  > "is 25 mJy beam$^{-1}$ at a spectral resolution of 0.1 km s$^{-1}$" (2 ALMA Cycle-3 observations)
- time on source: _not stated_
- observing dates: 26 Dec 2015 to 2 Jan 2016  
  > "between December 26th, 2015 and January 2nd, 2016" (2 ALMA Cycle-3 observations)
- pi or archival as stated: PI: A. Hacar  
  > "ID: 2015.1.00669.S; PI: A. Hacar" (2 ALMA Cycle-3 observations)
- Line: N2H+ J=1-0 (not stated)
- Other facility **IRAM 30m**: single-dish N2H+ (1-0) map used as model and feathering  
  > "in combination with previous single-dish IRAM 30m observations of the ISF (cite: HAC17a)" (2 ALMA Cycle-3 observations)
- Other facility **Herschel-Planck**: column density map for N2H+ intensity-to-N(H2) calibration  
  > "total N(H$_2$) column density derived in previous *Herschel-Planck* studies (cite: LOM14)" (3.3 Linear masses and stability)
- Other facility **GAS-DR1 (NH3)**: gas kinetic temperatures  
  > "we combined our new ALMA observations with the NH$_3$ T$_K$ estimates provided by the GAS-DR1 survey (cite: FRI17)" (3.2 Kinematic properties)
- External data: IRAM 30m N2H+ (1-0) map of the ISF  
  > "previous single-dish IRAM 30m observations of the ISF (cite: HAC17a)" (2 ALMA Cycle-3 observations) [from (cite: HAC17a)]
- External data: Herschel-Planck H2 column densities  
  > "total N(H$_2$) column density derived in previous *Herschel-Planck* studies (cite: LOM14)" (3.3 Linear masses and stability) [from (cite: LOM14)]
- External data: NH3 kinetic temperatures  
  > "NH$_3$ T$_K$ estimates provided by the GAS-DR1 survey (cite: FRI17)" (3.2 Kinematic properties) [from (cite: FRI17)]
- External data: Fiber properties of NGC1333, B213-L1495, Musca for comparison  
  > "(2) (cite: HAC17b); (3) (cite: HAC13); (4) (cite: HAC16)" (Table 2 notes) [from (cite: HAC17b; HAC13; HAC16)]

## Processing

### Calibration

- pipeline or manual: facility-provided pipeline  
  > "Independent visibility data for each mosaic were obtained in CASA (v4.5.3) (cite: CASA07) using the facility provided pipeline." (2 ALMA Cycle-3 observations)
- casa version: CASA 4.5.3 (calibration); 4.7.1 (imaging)  
  > "Our two N$_2$H$^+$ ALMA mosaics were simultaneously imaged in CASA (v4.7.1)" (2 ALMA Cycle-3 observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0423-0120 (bandpass plus amplitude)  
  > "The quasar J0423-0120 was observed for bandpass plus amplitude calibrations" (2 ALMA Cycle-3 observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean with single-dish model, then feathering  
  > "the line visibilities were simultaneously deconvolved with the CASA task *clean* using the single-dish observations as source model" (2 ALMA Cycle-3 observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "a Briggs weighting with robust parameter equal to 0.5" (2 ALMA Cycle-3 observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: line-free continuum level estimated in all sidebands  
  > "we subtracted the continuum emission from our high resolution spectral window based on the line-free continuum level estimated in all sidebands" (2 ALMA Cycle-3 observations)
- line free channels: _not stated_
- primary beam correction: applied  
  > "the resulting primary-beam corrected image" (2 ALMA Cycle-3 observations)
- array combination: feathering of IRAM 30m and ALMA maps  
  > "both single-dish and interferometric maps were combined using the task *feathering*" (2 ALMA Cycle-3 observations)
- smoothing: _not stated_
- final beam: 4.5" circular  
  > "convolved into a final circular beam ($\theta_{FWHM}$) of 4.5"" (2 ALMA Cycle-3 observations)
- final rms: 25 mJy/beam at 0.1 km/s  
  > "is 25 mJy beam$^{-1}$ at a spectral resolution of 0.1 km s$^{-1}$" (2 ALMA Cycle-3 observations)

### Inherited from earlier work

- Detailed data reduction deferred to Paper II  
  > "A detailed discussion on the data reduction process will be presented in a subsequent paper (Paper II; Hacar et al in prep.)." (2 ALMA Cycle-3 observations) [from Paper II; Hacar et al in prep.]
- Fiber main-axis fitting procedure  
  > "using the same fitting procedure introduced in (cite: HAC13)" (3.1 Fibrous substructure of the ISF) [from (cite: HAC13)]
- HiFIVE derived from FIVE algorithm  
  > "using a new version of the FIVE analysis technique (cite: HAC13), hereafter referred to as HiFIVE" (3.1 Fibrous substructure of the ISF) [from (cite: HAC13)]
- Column density calibration method with Herschel  
  > "Introduced in similar studies using N$_2$H$^+$ as line tracer (cite: TAF15; HAC17b)" (3.3 Linear masses and stability) [from (cite: TAF15; HAC17b)]
- N2H+ column density from CAS02 approach  
  > "following the standard approach introduced by (cite: CAS02)" (7.3 Fitting results (II)) [from (cite: CAS02)]

### Not stated but needed to reproduce (our reading)

- Exact HiFIVE code (not released) and implementation details
- Line-free channels used for continuum subtraction
- clean parameters: cell size, image size, niter, threshold, masks
- Flux scale uncertainty and flux density of calibrators
- Feathering parameters (single-dish scaling)
- Rest frequency/hyperfine frequencies used in CLASS HFS fits
- Fiber main-axis fitting and length definition details
- Which spectra pass S/N and how nearest NH3 position is matched

## Analysis recipe

1. **Calibrate and image ALMA+IRAM30m N2H+ cube**: Pipeline calibration; clean with 30m model; convolve to 4.5"; feather with 30m  
  > "both single-dish and interferometric maps were combined using the task *feathering* in order maximize the recovery of the extended emission" (2 ALMA Cycle-3 observations)
   - software: CASA
   - parameter: robust = 0.5; final beam 4.5"  
  > "a Briggs weighting with robust parameter equal to 0.5" (2 ALMA Cycle-3 observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit hyperfine N2H+ spectra**: Subfields of 5x5 spectra; template fitted manually then automatic HFS fit; keep components with S/N>=3  
  > "The entire dataset is subdivided into subfields of 5$\times$5 spectra." (7.1 Fitting procedure); "All hyperfine lines are simultaneously fitted using the HFS method assuming similar excitation conditions and widths" (7.1 Fitting procedure)
   - software: GILDAS/CLASS
   - parameter: >70 000 spectra, >25 000 components with S/N>=3  
  > "we analysed more than 70 000 N$_2$H$^+$ (1-0) spectra in Orion. A total of $>$ 25 000 individual components are detected with S/N $\ge$ 3." (7.1 Fitting procedure)
   - assumption: Similar excitation conditions and widths; Gaussian opacity profiles  
  > "assuming similar excitation conditions and widths, as well as Gaussian opacity profiles for all components in the multiplet" (7.1 Fitting procedure)
   - fitting: CLASS HFS least-squares; lowest possible number of components in doubtful cases  
  > "In case of doubt, the spectra are conservatively fitted with the lowest possible number of components." (7.1 Fitting procedure)
   - validation: Residuals inspected; <5% of fits problematic  
  > "Estimated to affect $<$ 5% of our fits" (7.1 Fitting procedure)
3. **Identify fibers with HiFIVE**: Hierarchical velocity-coherent structure identification in 3 levels with adaptive linking gradient  
  > "HiFIVE carries out a hierarchical segmentation in three recursive levels $(W_i,N_i)$ (i=1,2,3) following a bottom-up approach." (6 Fiber identification)
   - software: HiFIVE
   - parameter: W1=2.3e22, W2=4.0e22, W3=6.0e22 cm^-2; N_i=10  
  > "$W_1=2.3\cdot10^{22}$ cm$^{-2}$ (or $\sim$ 26 A$_v$; median), $W_2=4.0\cdot10^{22}$ cm$^{-2}$" (6 Fiber identification)
   - assumption: PPV continuity corresponds to real PPP structures  
  > "assumes the direct correspondence between the continuous structures identified in the observed Position-Position-Velocity (PPV) space and the real density structure" (6 Fiber identification)
   - fitting: _not stated_
   - validation: Reanalysis of NGC1333 recovers 10 vs 14 fibers; mean properties consistent within 1 sigma  
  > "HiFIVE automatically recovers a total of 10 velocity-coherent structures within NGC1333, that is, 4 less than the 14 fibers identified by (cite: HAC17b)" (6 Fiber identification)
4. **Derive non-thermal velocity dispersion**: sigma_NT from FWHM minus thermal term; compare to c_s(T_K) using GAS NH3 temperatures at nearest position  
  > "we adopt the T$_K$ value for each individual N$_2$H$^+$ component from the nearest position surveyed in NH$_3$" (3.2 Kinematic properties)
   - assumption: NH3 temperatures represent dense N2H+ gas  
  > "these NH$_3$-derived temperatures provide good estimates for the thermal state of the dense gas detected in N$_2$H$^+$" (3.2 Kinematic properties)
   - fitting: _not stated_
   - validation: _not stated_
5. **Derive column density, mass and M_lin and stability**: Empirical N(H2)-I(N2H+)/T_K relation from Herschel vs single-dish; sum masses per fiber, divide by length; compare to critical mass 2 sigma_eff^2/G  
  > "N(H_2)\ [\mathrm{cm}^{-2}]= 67.4\times10^{21}\cdot\left(\frac{I(N_2H^+)\ [\mathrm{K}\ \mathrm{km}\ \mathrm{s}^{-1}]}{T_\mathrm{K}\ [\mathrm{K}]}\right)" (3.3 Linear masses and stability)
   - parameter: D=414 pc; factor ~2 uncertainty  
  > "uncertainties of a factor $\sim$ 2 are expected for all the above estimates" (3.3 Linear masses and stability)
   - assumption: Optically thin N2H+; same correlation valid at ALMA resolution  
  > "our mass calculations adopt an optically thin approximation for N$_2$H$^+$ emission in the ISF" (3.3 Linear masses and stability)
   - fitting: least-squares linear fit  
  > "We have described this relationship using a least-squares fit of all the points" (3.3 Linear masses and stability)
   - validation: Agrees with NGC1333 relation; opacity checked with RADEX  
  > "we find an excellent correspondence between Eq. [\[eq:colden\]](#eq:colden) in Orion and the results obtained from the study of the N$_2$H$^+$ emission in the NGC 1333 region" (3.3 Linear masses and stability)
6. **Measure fiber widths**: Gaussian fits to cuts perpendicular to fiber axes in integrated intensity map (576 cuts)  
  > "the observed FWHM along all the ISF fibers (576 cuts)" (3.4 Fiber widths)
   - parameter: Gaussian fit within innermost 0.05 pc  
  > "obtained from the Gaussian fit of the total integrated N$_2$H$^+$ emission within the innermost 0.05 pc region around the fiber axis" (3.4 Fiber widths)
   - fitting: single Gaussian per cut  
  > "We estimate the typical fiber widths within these regions by fitting a single gaussian function to each of the above cuts (red dashed lines)." (Fiber widths: typical 0.03 pc values)
   - validation: _not stated_
7. **Compare fiber properties across clouds**: Compare fertile fiber surface density vs total M_lin across Musca, Taurus, Perseus, Orion; KS test for lengths; linear fit  
  > "least-square fit $\Sigma(\mathrm{fertile})\sim 0.1\times M_\mathrm{lin}(\mathrm{total})$" (4.2 Towards a unified model)
   - fitting: least-squares  
  > "We have described this relationship using a least-squares fit of all the points included in Fig. [7](#fig:N2H+_cal) (black line) resulting in a linear term:" (Linear masses and stability)
   - validation: _not stated_

## Software

- **CASA** 4.5.3 (calibration), 4.7.1 (imaging): pipeline calibration, clean, feathering  
  > "Independent visibility data for each mosaic were obtained in CASA (v4.5.3)" (2 ALMA Cycle-3 observations)
- **GILDAS/CLASS** : hyperfine (HFS) spectral fitting  
  > "The entire fitting procedure is carried out with the GILDAS/CLASS software" (7.1 Fitting procedure)
- **HiFIVE** : hierarchical fiber identification (new, derived from FIVE)  
  > "hereafter referred to as HiFIVE" (3.1 Fibrous substructure of the ISF)
- **RADEX** : radiative transfer predictions for opacity vs column density  
  > "We have compared our estimates with the radiative transfer predictions provided by RADEX (cite: VDT07)." (7.3 Fitting results (II))
- **APLpy** : plotting  
  > "This research made use of APLpy, an open-source plotting package for Python" (Acknowledgements)
- **Astropy** : general analysis  
  > "This research made use of Astropy, a community-developed core Python package for Astronomy" (Acknowledgements)
- **TOPCAT** : table handling  
  > "This paper made use of the TOPCAT software" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of fibers | 55 | not stated | dimensionless | 3 | Using HiFIVE, we identify a total of 55 velocity-coherent elongated fibers along the ISF. |
| Mean fiber length | 0.16 | 0.10 | pc | 3 | an average total length of $0.16\pm0.10$ pc |
| Median fiber FWHM | 0.035 | not stated | pc | 6 | The ISF fibers show a median FWHM of 0.035 pc |
| Mean sigma_NT/c_s (ISF components) | 0.81 | not stated | dimensionless | 4 | / $\left<\sigma_{NT}/\mathrm{c}_s(T_\mathrm{K})\right>$ / 0.81 / 0.91 / 0.69 / |
| Median M_lin of fibers | ~19 | factor ~2 | Msun/pc | 5 | with a median value of $\sim~19$ M$_\ensuremath{\odot}$ pc$^{-1}$ |
| Dense gas mass in fibers | 288 of 295 Msun (98%) | not stated | Msun | 5 | Among the total 295 M$_{\ensuremath{\odot}}$ of dense gas detected in our high-S/N N$_2$H$^+$ spectra, 288 M$_{\ensuremath{\odot}}$ (i.e. 98%) are recovered as fibers |
| N2H+ to N(H2) conversion slope | 67.4e21 | factor 2-3 | cm^-2 per (K km/s / K) | 5 | N(H_2)\ [\mathrm{cm}^{-2}]= 67.4\times10^{21}\cdot |
| Fertile fiber surface density, ISF | 45.8 | not stated | pc^-2 | 7 | $\Sigma$(fertile) (pc$^{-2}$) / 45.8 / 58.3 / 37.5 |
| Fraction of components subsonic | 76.4% | not stated | percent | 4 | $\sigma_{NT}/\mathrm{c}_s(T_\mathrm{K})\le$ 1 / 76.4% / 68.4% / 85.5% |
| N2H+ abundance | 7.5e-10 | within factor of two | dimensionless | 5 | consistent, within a factor of two, with a constant abundance $X(N_2H^+)=7.5\times 10^{-10}$ |

## Qualitative findings

- Fibers in the ISF are transonic, narrow, near hydrostatic equilibrium, and arranged in hub-like associations following the gravitational potential.  
  > "The ISF fibers are spatially organized forming a dense bundle with multiple hub-like associations likely shaped by the local gravitational potential." (abstract)

## Claim tuples

- H: The massive ISF is a bundle of fibers like low-mass filaments | E: HiFIVE analysis of ALMA+IRAM N2H+ (1-0) mosaics | R: 55 velocity-coherent fibers, 98% of dense gas mass | F: Fibers dominate the internal substructure of the ISF | **supported**
- H: ISF fibers have dynamical properties like low-mass fibers | E: sigma_NT/c_s and M_lin versus critical mass | R: sigma_NT between 0.4 and 1.5 c_s; ~50% with 0.5<=M_lin/m_crit<=1.5 | F: Fibers are transonic and near equilibrium | **supported**
- H: Filaments have a universal 0.1 pc width | E: Gaussian fits across 576 cuts | R: median FWHM 0.035 pc; 85% <0.05 pc | F: ISF fibers are systematically narrower than 0.1 pc | **supported**
- H: Fiber surface density scales with cloud M_lin | E: Compare Musca, Taurus, Perseus, Orion | R: Sigma(fertile) ~ 0.1 x M_lin(total) | F: Cluster formation as scaled-up concentration of fibers | **partially**

## Reasoning

- Why this data: N2H+ selectively traces high-density star-forming gas and has hyperfine structure enabling accurate kinematics  
  > "N$_2$H$^+$ selectively highlights the high-density, star-forming material in compact regions" (3 Results)
- Why this method: _not stated_
- Alternative: Original FIVE with a single parameter set could not recover all structures in OMC-1 and OMC-2, so HiFIVE was created  
  > "no single combination of \[$\nabla V_{lsr,0}$,I$_0$,N$_{friends}$\] values is able to satisfactorily recover all the structures" (6 Fiber identification)
- How they decided it was enough: _not stated_
- Limitation (authors): HiFIVE fails on the most complex structures (fibers 21, 36/37, 42/43); the 55 fibers are a simplified description  
  > "the above 55 fibers should be interpreted as a simplified description of the real dense gas substructure within the ISF" (6 Fiber identification)
- Limitation (authors): Mass conversion uncertain by factor 2-3; lengths not corrected for projection  
  > "Our length measurements do not consider projection effects making our M$_{\mathrm{lin}}$ values upper limits." (3.3 Linear masses and stability)
- Caveat (inferred, ours): PPV-identified fibers may not be physical PPP structures
- Caveat (inferred, ours): Single-dish-calibrated N2H+ to mass conversion applied at ALMA scales
- Caveat (inferred, ours): Fiber counts depend on HiFIVE thresholds (~40% differences vs FIVE)
- Caveat (inferred, ours): Cross-cloud comparison mixes resolutions and tracers; Musca counted as one fiber
- Caveat (inferred, ours): Width measured at 0.009 pc resolution, some fibers marginally resolved

## Reproducibility

- Data public (paper): ALMA data ID given; data products available via CDS  
  > "The data products of this work are available via CDS (link)." (footnote 1)
- Products in archive: _not stated_
- Missing: HiFIVE code
- Missing: detailed reduction (Paper II)
- Missing: IRAM 30m map access/combination details
- Missing: line-free channels and clean parameters
- Data volume (inferred): Large: two 148-pointing Band 3 mosaics; hundreds of GB raw, tens of GB imaged
- Score (inferred): 3/5, Data are public and recipe described, but HiFIVE is unreleased and imaging details are deferred to Paper II.
- Rediscovery candidate: no, Key results depend on unreleased HiFIVE code and unpublished reduction details.

## Links

- Method: (cite: HAC13) (FIVE algorithm and fiber fitting)
- Method: (cite: HAC17b) (N2H+ calibration method with Herschel)
- Method: (cite: CAS02) (N2H+ column density derivation)
- Companion: Paper II; Hacar et al in prep. (detailed data reduction)
- Companion: (cite: HAC17a) (IRAM 30m N2H+ map of the ISF)
- Related: ORION-4D project
- Related: GAS-DR1

## Checks

```json
{
 "quotes": 87,
 "quotes_ok": 87,
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
  "facts": 96,
  "stated": 69,
  "rate": 0.719
 },
 "evidence_ok": true
}
```
