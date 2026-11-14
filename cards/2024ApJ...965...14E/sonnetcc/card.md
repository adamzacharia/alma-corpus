# An Automated Chemical Exploration of NGC 6334I at 340 au Resolution

`2024ApJ...965...14E` | The Astrophysical Journal 2024 | first author: El-Abd, Samer J. | arXiv: 2402.13913 | DOI: 10.3847/1538-4357/ad283f

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type archival_reuse

## Science

- Fields: astrochemistry, star_formation, milky_way_ism
- Question: Can an automated per-pixel spectral fitting routine (molsim-based) map excitation temperature, linewidth, velocity and column densities of 21 molecules across NGC 6334I MM1 and MM2, and do the isomer column-density trends of earlier work hold with the larger sample?  
  > "We have developed an automated fitting routine that visits every pixel in the field of view of an ALMA data cube and determines the best-fit physical parameters, including excitation temperature and column densities, for a given list of molecules." (abstract); "Reproducing such a plot with the plethora of new data points we have produced in this work would serve as an excellent indicator of whether the bimodal trend previously observed was due to the small sample size" (Collating the Column Density Results)
- Target **NGC 6334I (MM1 and MM2)**: coordinates alpha(J2000) = 17h20m53.36s, delta(J2000) = -35d47m00.0s (observation phase center)  
  > "The observations were centered at $\alpha$(J2000) = 17$^h$:20$^m$:53$^s$.36, $\delta$(J2000) = -35$^\circ$:47$^\prime$:00$^{\prime\prime}$.0" (Observations); "At a distance of 1.3 kpc (cite: Reid2014; Chibueze2014)" (Test Case: NGC 6334I); z/distance 1.3 kpc  
  > "The observations were centered at $\alpha$(J2000) = 17$^h$:20$^m$:53$^s$.36, $\delta$(J2000) = -35$^\circ$:47$^\prime$:00$^{\prime\prime}$.0" (Observations); "At a distance of 1.3 kpc (cite: Reid2014; Chibueze2014)" (Test Case: NGC 6334I); distance from Reid2014; Chibueze2014  
  > "The observations were centered at $\alpha$(J2000) = 17$^h$:20$^m$:53$^s$.36, $\delta$(J2000) = -35$^\circ$:47$^\prime$:00$^{\prime\prime}$.0" (Observations); "At a distance of 1.3 kpc (cite: Reid2014; Chibueze2014)" (Test Case: NGC 6334I)

## Data provenance

- ALMA projects: 2015.A.00022.T
- bands: _not stated_
- frequencies and spectral setup: Two tunings, four spectral windows each, 1.87 GHz per pair of windows; centers 280.1, 282.0, 292.1, 294.0 GHz and 337.1, 339.0, 349.1, 351.0 GHz; channel width 976.6 kHz (cubes at 1.1 km/s); 7.48 GHz total, 280-351 GHz  
  > "The observations consisted of two tunings, each with four spectral windows, with a bandwidth of 1.87 GHz per pair of windows." (Observations); "The first set of spectral windows were centered at 280.1, 282.0, 292.1, and 294.0 GHz." (Observations); "The second set of spectral windows were centered at 337.1, 339.0, 349.1, and 351.0 GHz." (Observations); "producing a channel width of 976.6 kHz" (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: smoothed to a uniform circular 0.26 arcsec  
  > "The cubes were smoothed to a uniform circular angular resolution of $0.26\ensuremath{''}$ before analysis" (Observations)
- max recoverable scale: _not stated_
- sensitivity: rms per channel 1.8 mJy/beam (lower tuning), 3.0 mJy/beam (upper tuning)  
  > "with an rms noise per channel of 1.8 mJy beam$^{-1}$ for the lower tuning and 3.0 mJy beam$^{-1}$ for the upper tuning." (Observations)
- time on source: _not stated_
- observing dates: Cycle 3, 2016  
  > "The ALMA data toward NGC 6334I used for this study were observed during Cycle 3 in 2016, under project code 2015.A.00022.T." (Observations)
- pi or archival as stated: _not stated_
- Line: 21 molecules fitted over the full band (including methanol, methyl cyanide, formamide, methyl formate, glycolaldehyde, acetic acid and 13C isotopologues; full list in a garbled table) all transitions in the catalogs within 280-351 GHz (not stated)
- Line: CS J=6-5 (not stated)
- External data: Rotational line catalogs (frequencies, upper-state energies, partition functions) from CDMS and JPL  
  > "The catalogs were obtained from both the CDMS (cite: Muller:2005:215) and JPL (cite: Pickett:1998:883) spectroscopic databases." (Table 1) [from Muller:2005:215; Pickett:1998:883]
- External data: Absolute flux calibration uncertainty of 10%  
  > "An additional factor of 10% of the final fitted value was added in quadrature with the final rms noise value to account for the absolute flux calibration uncertainty (cite: CortesPaulo:2023:)." (Excitation Temperature) [from CortesPaulo:2023:]
- External data: Source distance 1.3 kpc  
  > "At a distance of 1.3 kpc (cite: Reid2014; Chibueze2014)" (Test Case: NGC 6334I) [from Reid2014; Chibueze2014]
- External data: Previous isomer column densities / abundance trends for NGC 6334I and other star-forming regions used for comparison  
  > "the relative abundances of the three molecules were compared across select locations toward both MM1 and MM2 along with measurements for other star-forming regions that were found in the literature" (Previous Findings) [from El-Abd:2019:129]
- Simulation/model as data: molsim forward-modeled synthetic spectra (LTE, shared Tex, linewidth, velocity per pixel) fitted to the observed cubes  
  > "we derive values for excitation temperature ($T_{ex}$), linewidth ($\Delta V$), velocity ($v_{LSR}$), and column density ($N_T$) by forward-modeling the spectra of each species" (Technique)

## Processing

### Calibration

- pipeline or manual: reprocessed with the ALMA Cycle 8 pipeline to correct the spectral renormalization issue  
  > "have since been reprocessed with the ALMA Cycle 8 pipeline (cite: Hunter2023) to account for an ALMA renormalization issue" (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10% absolute flux calibration uncertainty added in quadrature  
  > "An additional factor of 10% of the final fitted value was added in quadrature with the final rms noise value to account for the absolute flux calibration uncertainty (cite: CortesPaulo:2023:)." (Excitation Temperature)
- self calibration: self-calibrated on the bright continuum; solutions also applied to continuum-subtracted line data  
  > "The data were self-calibrated using the bright continuum emission, and the solutions were also applied to the continuum-subtracted line data" (Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: robust = 0.2 (lower tuning), 0.5 (higher tuning)  
  > "using `robust` image weighting values of 0.2 and 0.5 for the lower and higher frequency tunings, respectively" (Observations)
- uv taper: _not stated_
- cell size: beam oversampled by a factor of 5 relative to the minor axis  
  > "the beam was oversampled by a factor of 5 relative to the minor axis of the synthesized beam" (Observations)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: as described in Brogan et al. 2018  
  > "the continuum subtraction was performed as described in (cite: Brogan:2018:87)" (Observations)
- line free channels: _not stated_
- primary beam correction: images corrected for the primary beam response  
  > "the images were corrected for the primary beam response" (Observations)
- array combination: _not stated_
- smoothing: smoothed to uniform circular beam of 0.26 arcsec  
  > "The cubes were smoothed to a uniform circular angular resolution of $0.26\ensuremath{''}$ before analysis" (Observations)
- final beam: _not stated_
- final rms: 1.8 mJy/beam per channel (lower tuning), 3.0 mJy/beam (upper tuning)  
  > "with an rms noise per channel of 1.8 mJy beam$^{-1}$ for the lower tuning and 3.0 mJy beam$^{-1}$ for the upper tuning." (Observations)

### Inherited from earlier work

- Data are the same as in El-Abd et al. 2019 (reprocessed)  
  > "These are the same data used in (cite: El-Abd:2019:129)" (Observations) [from El-Abd:2019:129]
- Continuum subtraction method  
  > "the continuum subtraction was performed as described in (cite: Brogan:2018:87)" (Observations) [from Brogan:2018:87]
- Further data processing details  
  > "Further data processing details are given in (cite: McGuire:2017:L46), (cite: Hunter:2017:L29), and (cite: Brogan:2018:87)." (Observations) [from McGuire:2017:L46; Hunter:2017:L29; Brogan:2018:87]
- Starting molecule list taken from earlier model  
  > "the molecules included in the models of (cite: El-Abd:2019:129) served as the starting point" (Molecules Included in the Model) [from El-Abd:2019:129]
- Excitation temperature formalism for optically thick lines  
  > "we can directly solve for the excitation temperature adopting the formalism of (cite: Turner:1991:617)" (Technique) [from Turner:1991:617]
- Column density equation for an optically thin transition  
  > "The column density can be related to the intensity of a single optically thin transition with the following equation (cite: Hollis:2004:L45)" (Column Density) [from Hollis:2004:L45]
- Velocity uncertainty approximation for a Gaussian centre  
  > "The uncertainty in the central value of a Gaussian can be approximated with the following equation (cite: Campbell:2018:)" ($V_{LSR}$) [from Campbell:2018:]

### Not stated but needed to reproduce (our reading)

- CASA and ALMA pipeline version numbers and the exact imaging task, image size and cell size
- Self-calibration solution intervals, number of rounds and reference antennas
- Line-free channels used for continuum subtraction (deferred to Brogan et al. 2018)
- The complete list of the 21 molecules and vibrational states with partition functions (Table 1 is garbled in the text), and the actual E_up exclusion threshold values
- Initial column density value, absolute bounds on Tex/column density, and the minimizer tolerances for the bounded L-BFGS fit
- The peak-finding algorithm and histogram binning used for the linewidth estimate
- Whether the fitting code (beyond molsim) is released; pixel start positions for MM1 and MM2
- Whether the ALMA data are public and which product (calibrated MS or reprocessed cubes) to start from

## Analysis recipe

1. **Prepare calibrated, smoothed cubes**: Reprocess with ALMA Cycle 8 pipeline, self-calibrate on continuum, image with CASA, continuum-subtract, primary-beam correct and smooth to a common 0.26 arcsec beam  
  > "have since been reprocessed with the ALMA Cycle 8 pipeline (cite: Hunter2023) to account for an ALMA renormalization issue" (Observations); "The cubes were smoothed to a uniform circular angular resolution of $0.26\ensuremath{''}$ before analysis" (Observations)
   - software: CASA
   - parameter: robust = 0.2 (lower tuning) and 0.5 (higher tuning); channel width 1.1 km/s  
  > "using `robust` image weighting values of 0.2 and 0.5 for the lower and higher frequency tunings, respectively" (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure background temperature and excitation temperature per pixel**: Assume the brightest lines are optically thick and solve for Tex from the mean intensity of channels near peak intensity, using the background temperature from the continuum image of each spectral window  
  > "The excitation temperature is measured by assuming the brightest lines in our spectral range are optically thick" (Technique); "the background temperature (measured from the continuum image of each spectral window)" (Technique)
   - software: molsim
   - assumption: Source fills the beam; brightest lines optically thick; LTE  
  > "where the source is assumed to fill the beam" (Technique); "(assuming local thermodynamic equilibrium)" (Introduction)
   - fitting: _not stated_
   - validation: Tex from optically thick lines gives fits to optically thin lines within expected uncertainties  
  > "indeed find that the excitation temperatures derived from our optically thick lines result in fits to the optically thin lines well within expected uncertainties" (Technique)
3. **Measure linewidth per pixel**: Peak-finding over the full band, Gaussian fit to each peak, histogram of FWHMs fitted with a Gaussian whose centre is the pixel linewidth  
  > "Another Gaussian is fit to the histogram itself, with the central value of this final Gaussian adopted as the canonical linewidth for the pixel in question." (Technique)
   - software: lmfit
   - parameter: peaks below 10 sigma excluded  
  > "excluding any peaks below $10\sigma$" (Technique)
   - assumption: All molecules share a single Tex, linewidth and velocity per pixel; column density varies per molecule  
  > "we made the assumption that all of the molecules in the model share a single excitation temperature, linewidth, and velocity for each pixel while we allow the column density to vary on a molecule-by-molecule basis." (Technique)
   - fitting: Gaussian fits (lmfit) to line peaks and to the FWHM histogram  
  > "taken directly from the uncertainty automatically calculated by the `lmfit` package used for the Gaussian fit to the histogram" (Linewidth)
   - validation: Visual inspection of fits and residuals  
  > "Visual inspection of the fits and examination of residuals in numerous spectra show that the values extracted from this procedure indeed robustly describe the vast majority of spectral lines." (Technique)
4. **Exclude problematic channels**: Mask channels contaminated by low-E_up transitions of methyl cyanide and formamide (threshold tied to local background temperature), by all methanol vt=0,1 transitions, and by molecules with few unblended lines  
  > "The exclusion threshold is dependent on the mean background temperature at that pixel (measured for each of four spectral windows)" (Exclusion of Channels); "All of the $v_t = 0,1$ transitions were used to exclude channels from the observations as above regardless of their upper state energy." (Exclusion of Channels)
   - software: molsim
   - parameter: methanol fitted only with vt = 2 transitions  
  > "splitting the catalog into separate vibrational states such that we only attempted to fit the $v_t = 2$ transitions" (Exclusion of Channels)
   - fitting: _not stated_
   - validation: _not stated_
5. **Fit velocity and column densities pixel by pixel**: Least-squares fit of the combined synthetic spectra; start at one pixel with all molecules at the same column density, then step north up the column, then launch parallel row scripts using the previous pixel as the starting point  
  > "the fitting itself begins with a single pixel on the image with every molecule initialized to the same column density." (Technique); "Scripts are then launched in parallel that each use one of the pixels in this first column as a starting point and then moves across the rest of the corresponding row in the image." (Technique)
   - software: molsim, scipy
   - parameter: velocity bound +/-1.0 km/s and column density bound +/-0.4 dex around the previous pixel's fit  
  > "the velocity was allowed to vary by $\pm$ 1.0 km s$^{-1}$ from pixel-to-pixel, while the column density for each molecule was allowed to vary by $\pm$ 0.4 dex" (Technique)
   - fitting: Bounded limited-memory BFGS least-squares minimizer; no priors  
  > "specifically, the bounded limited-memory BFGS algorithm (cite: Zhu:1997:550)" (Technique)
   - validation: Rerun excluding poorly constrained molecules gave well-matched parameters for the rest; MM1C pixel block masked as a poor fit  
  > "we conducted another run of the fitting routine that was identical in every way except for the exclusion of these molecules." (Molecules Included in the Model); "we decided to mask the region in its entirety for the column density maps" (Identifying Areas of Concern)
6. **Propagate uncertainties**: Propagate rms and flux calibration uncertainty for Tex, lmfit uncertainty for linewidth, centroid formula for VLSR, intensity-weighted mean over optically thin transitions for column density  
  > "The uncertainties in the values produced by the fitting are estimated through the propagation of uncertainties in the fundamental measurements with the exception of the linewidth" (Uncertainties)
   - software: lmfit
   - parameter: 10% flux calibration uncertainty added in quadrature  
  > "An additional factor of 10% of the final fitted value was added in quadrature with the final rms noise value to account for the absolute flux calibration uncertainty (cite: CortesPaulo:2023:)." (Excitation Temperature)
   - fitting: _not stated_
   - validation: _not stated_
7. **Mask, map ratios and compare with literature trends and moment maps**: Mask pixels with fewer than 3 transitions above 5x rms; build isomer column-density ratio maps and scatter plots (also coloured by Tex); compare column density and velocity images with moment 0 and 1 maps of 13-methyl formate  
  > "any pixel with less than 3 transitions with intensities greater than 5x the rms noise was masked" (Column Densities); "The comparison of the two methods in this work was conducted with 13-methyl formate." (Comparison with Traditional Moment Maps)
   - software: Astropy, APLpy
   - assumption: 13C isotopologue of methyl formate used because the standard isotopologue is too optically thick  
  > "we are instead using the $^{13}$C isotopologue of methyl formate for this work, as the standard isotopologue was too optically thick for many of the positions in our field of view." (Collating the Column Density Results)
   - fitting: _not stated_
   - validation: Compared with El-Abd et al. 2019 trends  
  > "the conclusions of (cite: El-Abd:2019:129) would appear to be upheld" (Collating the Column Density Results)

## Software

- **molsim** : Forward-modeling synthetic rotational spectra of molecules for the per-pixel fit  
  > "`molsim` is a publicly-available Python package tailored for the analysis of high spectral resolution spectroscopic observations of astronomical sources." (Technique)
- **CASA** : Imaging of the cubes  
  > "the images were created with CASA (cite: CASA2022)" (Observations)
- **lmfit** : Gaussian fit to the linewidth histogram and its uncertainty  
  > "taken directly from the uncertainty automatically calculated by the `lmfit` package used for the Gaussian fit to the histogram" (Linewidth)
- **scipy** : Listed in the software section; use not otherwise stated  
  > "lmfit (cite: Newville:2014:), molsim (cite: Lee:2023:), scipy (cite: Gommers:2023:)" (Software)
- **Astropy** : Listed in the software section and acknowledgments; use not otherwise stated  
  > "Astropy, a community-developed core Python package for Astronomy (cite: AstropyCollaboration:2022:167)" (Acknowledgments)
- **APLpy** : Plotting of images  
  > "APLpy, an open-source plotting package for Python (cite: aplpy2012)" (Acknowledgments)
- **Jupyter** : Listed in the software section; use not otherwise stated  
  > "Jupyter (cite: Kluyver:2016:87)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of molecules fitted | 21 | not stated | dimensionless | 5 | Parameters were found for 21 distinct molecules by generating synthetic spectra across 7.48 GHz of spectral bandwidth between 280 and 351 GHz. |
| Spectral bandwidth fitted | 7.48 | not stated | GHz | 5 | Parameters were found for 21 distinct molecules by generating synthetic spectra across 7.48 GHz of spectral bandwidth between 280 and 351 GHz. |
| Number of fitted pixels | >8000 | not stated | pixels | 5 | Spatial images of the derived parameters for each of the $>8000$ pixels are presented |
| Continuum peak brightness temperature MM1 (350 GHz) | 222 | not stated | K | 1 | MM2 (129 K continuum peak at 350 GHz) is a source with significantly lower brightness temperature than MM1 (222 K continuum peak) |
| Continuum peak brightness temperature MM2 (350 GHz) | 129 | not stated | K | 1 | MM2 (129 K continuum peak at 350 GHz) is a source with significantly lower brightness temperature than MM1 (222 K continuum peak) |
| Flux-scaling correction from reprocessing, CS (J=6-5) | of order 10% | not stated | percent | 1 | these corrections were found to be of order 10% for the most affected transition, CS (J=6-5) |
| Rms noise per channel, lower tuning | 1.8 | not stated | mJy/beam | 1 | with an rms noise per channel of 1.8 mJy beam$^{-1}$ for the lower tuning and 3.0 mJy beam$^{-1}$ for the upper tuning. |
| Rms noise per channel, upper tuning | 3.0 | not stated | mJy/beam | 1 | with an rms noise per channel of 1.8 mJy beam$^{-1}$ for the lower tuning and 3.0 mJy beam$^{-1}$ for the upper tuning. |
| Moment 1 versus fitted velocity divergence around MM1F | several | not stated | km/s | 7 | with the greatest divergence occurring around MM1F on the order of several kilometers per second |

## Qualitative findings

- In MM1 the excitation temperature tracks the continuum, and linewidth broadening is seen to the north and south, consistent with the N-S outflow  
  > "In MM1, the excitation temperature tracks rather well with the continuum emission with little to no variation otherwise." (The Shared Parameters - $T_{ex}$, $\Delta V$, and $V_{LSR}$); "This broadening is consistent with our understanding of the kinematics of MM1" (The Shared Parameters - $T_{ex}$, $\Delta V$, and $V_{LSR}$)
- Glycolaldehyde is relatively depleted toward the continuum peak (possibly an optical-depth underestimate), while its ratio with acetic acid is remarkably constant  
  > "The stand-out feature is the relative depletion of glycolaldehyde towards the continuum peak" (Column Density Ratios); "The ratio with acetic acid, on the other hand, is remarkably constant over the field of view." (Column Density Ratios)
- Glycolaldehyde column densities in MM2 should be treated as upper limits  
  > "The presented column densities for glycolaldehyde in MM2 should be treated as upper limits." (MM2 Results)

## Claim tuples

- H: An automated per-pixel spectral fit can characterize physical conditions and molecular column densities across NGC 6334I-MM1 and MM2 | E: Per-pixel molsim-based fit of 21 molecules over 7.48 GHz of ALMA data | R: Maps of Tex, linewidth, velocity and column densities for more than 8000 pixels | F: The automated approach is feasible for this complex source | **supported**
- H: The bimodal isomer trends seen in El-Abd et al. 2019 persist with a much larger sample of pixels | E: Scatter plots of 13-methyl formate against acetic acid and glycolaldehyde column densities, colored by source and Tex | R: Trends broadened with several regimes; acetic acid forms a single trend across MM1 and MM2, glycolaldehyde two separate trends | F: Conclusions of the earlier work are upheld | **supported**
- H: Fitted velocity images are more reliable than moment 1 maps of a single transition | E: Compared velocity image with moment 1 map of 13-methyl formate in MM1 and MM2 | R: Divergences of several km/s around MM1F and toward the warmer region in MM2 | F: The fitting routine more accurately represents the emission velocity | **supported**
- H: Moment 0 maps are a good proxy for molecular column density | E: Compared integrated-intensity maps with fitted column-density images of 13-methyl formate | R: Dips in integrated intensity in MM1 due to high optical depth; better agreement in lower-opacity MM2 | F: Moment 0 maps are shortcomings-prone proxies for column density | **refuted**

## Reasoning

- Why this data: NGC 6334I hosts two line-rich hot cores with distinct conditions, a challenging test case  
  > "This massive Galactic protocluster hosts two extremely rich hot core line sources, each with distinct physical conditions and kinematics" (Introduction)
- Why this method: Independent per-pixel Tex and linewidth measurements, since a full minimizer fit failed in bright-continuum and absorption pixels  
  > "we found that it would be better to make independent measurements of the excitation temperature and linewidth for each pixel and rely on the minimizer to fit the velocity and column densities" (Technique)
- Alternative: Fitting all parameters (including Tex and linewidth) with the minimizer gave unsatisfactory results in pixels with bright continuum or absorption  
  > "we were left with less than satisfactory results in pixels that had a particularly bright continuum or showed substantial absorption signals" (Technique)
- Alternative: Poorly constrained molecules dropped from later runs because they raised computation time  
  > "we continued to exclude these molecules from future runs of the fitting routine as their inclusion drastically increased the required computation time" (Molecules Included in the Model)
- How they decided it was enough: _not stated_
- Limitation (authors): Per-pixel fit parameters are not claimed to be as accurate as manual fits of individual pixels  
  > "we are not claiming that the final fit parameters for each pixel are necessarily as accurate as those that would be derived were one to manually fit each of the molecules by hand in one of the pixels." (Introduction)
- Limitation (authors): A single Tex per pixel is required because molsim cannot do multi-temperature radiative transfer  
  > "a full radiative transfer analysis would be needed in order to simulate contributions from molecules at more than one excitation temperature, which is not possible in the current version of `molsim`." (Technique)
- Limitation (authors): A poor fit in one pixel can affect the next; MM1C block masked  
  > "a poor fit in one pixel has the potential to adversely affect the fit in the subsequent pixel" (Technique)
- Caveat (inferred, ours): Fits are initialised and bounded from the previous pixel, so results depend on the path through the image and on the starting pixel
- Caveat (inferred, ours): A single Tex shared by all molecules and optically thick Tex estimate may bias column densities of species with different emitting regions
- Caveat (inferred, ours): No independent validation against manual spectral fits is given beyond visual inspection
- Caveat (inferred, ours): Fitting code and exact molecule/threshold settings are not given, so the maps cannot be exactly regenerated

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Code: molsim is publicly available; release of the per-pixel fitting routine itself is not stated  
  > "`molsim` is a publicly-available Python package tailored for the analysis of high spectral resolution spectroscopic observations of astronomical sources." (Technique)
- Missing: Per-pixel fitting scripts and parameter files
- Missing: Full molecule list with vibrational states and E_up exclusion thresholds
- Missing: CASA/pipeline versions, imaging parameters, self-calibration and continuum-subtraction details
- Missing: Statement of data availability for the reprocessed cubes
- Data volume (inferred): Several tens of GB: two tunings of four spectral windows each, Cycle 3 single-field observations, plus the imaged cubes
- Score (inferred): 2/5, The ALMA project code and imaging choices are given, but processing details are deferred to earlier papers, the fitting code and exact molecule/threshold settings are not published, and public availability of the data is not stated.
- Rediscovery candidate: no, The fitting recipe is only partially described and the code is not released, and the main results are maps and qualitative trends rather than numeric answer-key values.

## Links

- Method: Brogan:2018:87 (Continuum subtraction and further data processing)
- Method: Hunter2023 (ALMA Cycle 8 pipeline reprocessing for spectral renormalization)
- Method: Lee:2023: (molsim package used for the spectral modeling)
- Companion: El-Abd:2019:129 (Earlier analysis of the same data and isomer column-density trends)
- Companion: Hunter:2017:L29 (Further data processing details and the MM1 accretion outburst)
- Companion: McGuire:2017:L46 (Further data processing details)

## Checks

```json
{
 "quotes": 104,
 "quotes_ok": 104,
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
  "facts": 100,
  "stated": 68,
  "rate": 0.68
 },
 "evidence_ok": true
}
```
