# Vertical and radial distribution of atomic carbon in HD 163296

`2024A&A...686A.120U` | Astronomy and Astrophysics 2024 | first author: Urbina, F. | arXiv: 2403.05042 | DOI: 10.1051/0004-6361/202348523

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Where is atomic carbon [CI] 3P1-3P0 located radially and vertically in the HD 163296 disk relative to optically thick 12CO J=2-1, and does this match PDR expectations?  
  > "we aim to test our current knowledge about the expected location of atomic carbon within protoplanetary disks" (1 Introduction); "perform the first direct comparison of this tracer with optically thick line emission" (abstract)
- Target **HD 163296**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00527.S
- bands: Band 8  
  > "We used archival ALMA band 8 observations of HD163296" (2 Observations and data reduction)
- frequencies and spectral setup: Continuum: 2 spws centred at 480.24 and 482.05 GHz, 128 channels each. [CI] line: single spw, 3840 channels of 488.28 KHz spacing, centred at 492.22 GHz  
  > "central frequencies of 480.24 and 482.05 GHz respectively" (2 Observations and data reduction); "line emission was observed in a single spectral window of 3840 channels of spacing 488.28 KHz, with a central frequency of 492.22 GHz" (2 Observations and data reduction)
- continuum bandwidth: 2 GHz per spectral window (2 windows)  
  > "Dust continuum was observed in 2 spectral windows, each one with a bandwidth of 2 GHz, 128 channels" (2 Observations and data reduction)
- arrays: 37 antennas of 12 m  
  > "A configuration of 37 antennas of 12 m" (2 Observations and data reduction)
- configurations: _not stated_
- baselines: projected baselines 5th and 80th percentile 9.92 m and 127.36 m  
  > "the projected baselines 5th and 80th percentile are 9.92 m and 127.36 m respectively" (2 Observations and data reduction)
- angular resolution: Continuum natural-weighted beam 0.675x0.296 arcsec (observations section); [CI] cube beam 0.78x0.49 arcsec, PA 74.46 deg; combined continuum image beam 0.67x0.40 arcsec, PA 76.60 deg  
  > "synthesizing beam for the continuum images of 0.675$\times$0.296" when constructing images with natural weighting" (2 Observations and data reduction); "The synthesised beam of the CI cube is $0.78" \times 0.49"$ with a PA of 74.46°" (2 Observations and data reduction); "with an achieved synthesized beam FWHM dimensions of $0.67" \times 0.40"$ and a PA of 76.60°" (3.1 Imaging)
- max recoverable scale: _not stated_
- sensitivity: Noise RMS: [CI] channel maps 2.16e-2 Jy/beam; moment 0 2.63e-2 (km/s); continuum 6.62e-4 Jy/beam  
  > "2.16$\times 10^{-2}$" (Table 1); "$6.62 \times 10^{-4}$" (Table 1)
- time on source: 13.1 minutes  
  > "the total integration time on source was only 13.1 minutes" (2 Observations and data reduction)
- observing dates: May 2, 2015, single pointing; mean PWV 0.536 mm  
  > "These observations were obtained in a single pointing on May 2, 2015, affected by an average precipitable water vapor of 0.536 mm." (2 Observations and data reduction)
- pi or archival as stated: Archival, PI M. Kama (2013.1.00527.S); 12CO J=2-1 from the public DSHARP data release  
  > "archival ALMA band 8 observations of HD163296 from the project 2013.1.00527.S (PI: M. Kama)" (2 Observations and data reduction); "which where directly obtained from the publically available DSHARP data release" (2 Observations and data reduction)
- Line: [CI] 3P1 - 3P0 (not stated)
- Line: 12CO J=2-1 (not stated)
- Other facility **DSHARP (ALMA large program, public data release)**: 12CO J=2-1 data of HD 163296  
  > "which where directly obtained from the publically available DSHARP data release" (2 Observations and data reduction)
- External data: Outer CO radius of 560 au used to check the measured 600 au  
  > "The outer radius for CO is in good agreement with the value of 560 au reported in (cite: isella2018disk)." (3.2 Radial analysis) [from (cite: isella2018disk)]
- External data: Vertical profile (power-law fit and data points) of small dust grains in HD 163296  
  > "we added to our height profiles the power law fitting of dust grains as well as the data points from the same study." (4.3 um dust grains vertical non co-location with CO) [from (cite: rich2021investigating)]
- External data: NE side of the disk taken as the near side from scattered light imaging  
  > "The NE of the disk is thought to be the near side of the disk as scattered light imaging indicates (cite: 2019ApJ...875...38R)." (3.1 Imaging) [from (cite: 2019ApJ...875...38R)]
- Simulation/model as data: New DALI physical-chemical model of HD 163296 giving CO and [CI] abundances, emission layers and simulated image cubes; parameters in appendix table  
  > "Brand new DALI modelling was employed to perform direct comparison to the data." (abstract); "to obtain CO and \[CI\] abundance vertical profiles as well as their expected emission layers" (4.1 DALI modelling of [CI] and CO in HD 163296)

## Processing

### Calibration

- pipeline or manual: CASA pipeline script delivered with the data  
  > "using the pipeline script delivered with the data" (2 Observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (flux); J1256-0547 (bandpass); J1733-1304 (phase)  
  > "Calibration sources were the quasars J1256-0547 (bandpass) and J1733-1304 (phase) and Titan (flux)." (2 Observations and data reduction)
- flux scale uncertainty: _not stated_
- self calibration: Phase self-cal to final 30 s solution interval, plus amplitude self-cal; solutions applied to line imaging, SNR +20%  
  > "Self calibration was carried out reaching a final solution interval of 30s for phase calibration." (2 Observations and data reduction); "which increased the final SNR by 20% compared to non-selfcalibrated products" (2 Observations and data reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting (continuum images)  
  > "when constructing images with natural weighting" (2 Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum subtracted before [CI] line imaging  
  > "after subtracting the continuum and averaging the spectral windows to a width of 0.3 km/s" (2 Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: spectral averaging to 0.3 km/s channel width  
  > "after subtracting the continuum and averaging the spectral windows to a width of 0.3 km/s" (2 Observations and data reduction)
- final beam: [CI] cube 0.78" x 0.49", PA 74.46 deg; continuum 0.67" x 0.40", PA 76.60 deg  
  > "The synthesised beam of the CI cube is $0.78" \times 0.49"$ with a PA of 74.46°" (2 Observations and data reduction); "with an achieved synthesized beam FWHM dimensions of $0.67" \times 0.40"$ and a PA of 76.60°" (3.1 Imaging)
- final rms: [CI] channel maps 2.16e-2 Jy/beam; continuum 6.62e-4 Jy/beam  
  > "2.16$\times 10^{-2}$" (Table 1); "$6.62 \times 10^{-4}$" (Table 1)

### Inherited from earlier work

- disksurf emission-surface extraction follows the method of Pinte et al. 2018  
  > "implementation of the method first presented in (cite: pintemethod)" (3.3 Vertical analysis) [from (cite: pintemethod)]
- CO vertical analysis done similarly to Paneque-Carreno et al. 2023  
  > "The same is done for carbon monoxide, in a similar fashion as in (cite: Tere)." (3.3 Vertical analysis) [from (cite: Tere)]
- Double-peaked CO surface fit follows the approach of Law et al. 2021  
  > "we followed a similar approach as in (cite: law2021molecules)" (4 Discussions) [from (cite: law2021molecules)]
- DALI model fitting procedure (SED, CO ladder, CO 3-2) taken from earlier work  
  > "The model is fit following the procedure outlined in (cite: kama2016volatile) and (cite: keyte_2023), see those works for a full description of the fitting process." (4.1 DALI modelling of [CI] and CO in HD 163296) [from (cite: kama2016volatile); (cite: keyte_2023)]
- 12CO J=2-1 data reduction is that of the DSHARP release  
  > "which where directly obtained from the publically available DSHARP data release (cite: DSHARP; isella2018disk)" (2 Observations and data reduction) [from (cite: DSHARP; isella2018disk)]
- Keplerian masking uses the keplerian_mask implementation by Teague  
  > "Keplerian masking is applied by using the (cite: rich_teague_2020_4321137) implementation" (3.1 Imaging) [from (cite: rich_teague_2020_4321137)]

### Not stated but needed to reproduce (our reading)

- Distance, inclination, position angle, systemic velocity and stellar mass of HD 163296 used for projection, Keplerian masks and the radial analysis
- CASA version, reference antenna and which spws/scans entered self-calibration; starting solint and number of rounds
- tclean parameters for the [CI] cube and continuum (cell size, image size, niter, threshold, cleaning mask, deconvolver, primary beam correction)
- Line-free channels used for continuum subtraction
- How the 12CO cube was imaged and its beam and rms (DSHARP product or version used)
- disksurf settings (smoothing, x_min/x_max, SNR threshold, mask parameters) and how the surface was binned
- emcee setup: walkers, steps, burn-in, priors and likelihood for the tapered power-law and Gaussian fits
- Number and method of resampling used for the R90 68% intervals; velocity range and regions used for near and far side spectra
- DALI stellar parameters, input stellar spectrum and the SED and CO data used in the fit

## Analysis recipe

1. **Calibrate, self-calibrate and image the [CI] cube and continuum**: Pipeline calibration in CASA, phase and amplitude self-calibration, continuum subtraction, spectral averaging to 0.3 km/s, natural weighting  
  > "using the pipeline script delivered with the data" (2 Observations and data reduction); "Self calibration was carried out reaching a final solution interval of 30s for phase calibration." (2 Observations and data reduction)
   - software: CASA
   - parameter: final phase solint 30 s; channel width 0.3 km/s; natural weighting  
  > "reaching a final solution interval of 30s for phase calibration" (2 Observations and data reduction); "averaging the spectral windows to a width of 0.3 km/s" (2 Observations and data reduction)
   - fitting: _not stated_
   - validation: Amplitude self-cal raised the line SNR by 20% relative to non-self-calibrated products  
  > "which increased the final SNR by 20% compared to non-selfcalibrated products" (2 Observations and data reduction)
2. **Make moment 0 map and measure line and continuum fluxes**: Zeroth moment integrated over 1.3 to 10.6 km/s with pixels below 2 sigma masked; continuum from both spws combined  
  > "obtaining the zeroth moment map of the emission by integrating from 1.3 to 10.6 km/s" (3.1 Imaging); "dust continuum imaging achieved by combining both dedicated spectral windows" (3.1 Imaging)
   - software: bettermoments
   - parameter: velocity range 1.3-10.6 km/s, 2 sigma clip  
  > "integrating from 1.3 to 10.6 km/s and masking all pixels with values lower than $2\sigma$" (3.1 Imaging)
   - fitting: _not stated_
   - validation: _not stated_
3. **Compare near and far side spectra for asymmetry**: Each channel divided along the disk major axis; emission above 3 sigma with Keplerian masking; spectra summed per side  
  > "This is achieved by dividing each channel along the major axis of the disk." (3.1 Imaging); "Only emission above 3$\sigma$ is used and Keplerian masking is applied" (3.1 Imaging)
   - software: keplerian_mask
   - parameter: 3 sigma threshold  
  > "Only emission above 3$\sigma$ is used" (3.1 Imaging)
   - assumption: NE side is the near side of the disk  
  > "The NE of the disk is thought to be the near side of the disk as scattered light imaging indicates" (3.1 Imaging)
   - fitting: _not stated_
   - validation: _not stated_
4. **Constrain inner and outer gas radii from PV diagrams**: Position-velocity diagrams along the major axis with Keplerian rotation relations for maximum velocity and radial velocity  
  > "The inner and outer radii can be constrained by assuming Keplerian rotation of the gas" (3.2 Radial analysis)
   - assumption: Flat circular disk in Keplerian rotation  
  > "assumes a flat circular disk in Keplerian rotation" (4 Discussions)
   - fitting: _not stated_
   - validation: CO outer radius compared with 560 au from Isella et al. 2018  
  > "The outer radius for CO is in good agreement with the value of 560 au reported in (cite: isella2018disk)." (3.2 Radial analysis)
5. **Measure radial extent R90 of dust, [CI] and CO**: Azimuthal average radial profiles of moment 0 maps and continuum; R90 is the radius enclosing 90% of the total integrated profile; repeated on resampled profiles for 68% intervals  
  > "A radial cutoff ($R_{90}$) is defined as the radius where 90% of the total integrated profile value is reached." (3.2 Radial analysis); "By sampling the radial profiles at each radius, several profiles are obtained for which the calculation is repeated." (3.2 Radial analysis)
   - parameter: 90% enclosed, 68% confidence interval  
  > "Their respective 68% confidence interval is estimated." (3.2 Radial analysis)
   - fitting: _not stated_
   - validation: _not stated_
6. **Extract emission surface heights of [CI] and CO**: disksurf iterative mask update, upper surface only (lower side not resolved); 5 iterations for CO and 10 for [CI]; repeated with other robust values  
  > "in particular we used 5 and 10 iterations for obtaining CO and" (3.3 Vertical analysis); "therefore this method in only applied to the upper surface of the disk" (3.3 Vertical analysis)
   - software: disksurf
   - parameter: 5 iterations (CO), 10 iterations ([CI])  
  > "in particular we used 5 and 10 iterations for obtaining CO and" (3.3 Vertical analysis)
   - fitting: _not stated_
   - validation: Repeated with other robust weightings; no surface recovered for robust below 1, those above 1 agreed. Method also tested on DALI simulated cubes.  
  > "All profiles obtained with robust greater than 1 agreed with Fig." (3.3 Vertical analysis); "we repeated the vertical analysis in the simulated image cubes obtained with the DALI modelling" (9 Simulated image cubes surface emission)
7. **Fit parametric surface profiles**: Exponentially tapered power law for both tracers; CO also gets a Gaussian for the local minimum near 270 au (7 parameters total)  
  > "we fitted both surface emissions by using exponentially tapered power law function defined by" (4 Discussions); "for CO the parameter space consists on a total of 7 parameters, 4 from the baseline model and 3 more for the Gaussian feature" (4 Discussions)
   - software: emcee
   - fitting: emcee MCMC sampling of the parameter posteriors; priors and likelihood not stated  
  > "Markov chain Monte Carlo sampling is performed to explore the distribution of parameters" (4 Discussions)
   - validation: Residuals for [CI] range from -40 to 40 au, within the synthesized beam major axis  
  > "The residuals range for \[CI\] goes from -40 to 40 au, which is within the ranges of the synthesized beam major axis" (4 Discussions)
8. **Test whether angular resolution explains the CO versus [CI] height difference**: Convolve CO data with a 2D elliptical Gaussian matching the [CI] beam, repeat the vertical analysis, Welch's t-test on heights within 100-300 au  
  > "the CO data is convolved with a 2D elliptical Gaussian with the same PA, minor and major axis as the synthesized beam of the" (4.2 Angular resolution effects); "We employed a Welch’s t-test to examine the null hypothesis that the convolved CO and" (4.2 Angular resolution effects)
   - software: disksurf
   - parameter: height range 100 to 300 au  
  > "have the same average height within the 100 to 300 au range" (4.2 Angular resolution effects)
   - fitting: _not stated_
   - validation: p-value lower than 1e-10, null rejected  
  > "The analysis yielded a p-value lower than $10^{-10}$" (4.2 Angular resolution effects)
9. **Model [CI] and CO with DALI and compare emission layers**: DALI physical-chemical model: SED fit for structure and dust mass, CO ladder and CO 3-2 for carbon and oxygen abundances, time-dependent chemistry; 75% emission contour compared with derived surfaces  
  > "The total elemental carbon and oxygen abundances are then constrained by fitting the spatially unresolved CO rotational ladder and resolved CO 3-2 observations." (4.1 DALI modelling of [CI] and CO in HD 163296); "shows the comparison of the 75% emission contour with our derived surface emission for CO and" (4.1 DALI modelling of [CI] and CO in HD 163296)
   - software: DALI
   - parameter: chemical age 1 Myr; UMIST 06-based network with 118 species and 1675 reactions  
  > "We run the chemistry time-dependently to a chemical age of 1 Myr" (4.1 DALI modelling of [CI] and CO in HD 163296); "which consists of 118 species and 1675 individual reactions" (4.1 DALI modelling of [CI] and CO in HD 163296)
   - assumption: gas-to-dust ratio 100  
  > "we adopt a gas-to-dust ratio of $\Delta_\text{g/d}=100$" (4.1 DALI modelling of [CI] and CO in HD 163296)
   - fitting: Grid fit following Kama et al. 2016b and Keyte et al. 2023; details not given here  
  > "In short, the physical structure and total dust mass is first determined by fitting the continuum spectral energy distribution using a large grid of models." (4.1 DALI modelling of [CI] and CO in HD 163296)
   - validation: Model [CI] surface agrees with data; CO surface strongly disagrees beyond 100 au  
  > "it strongly disagrees as the predicted emission surface is located at much lower heights from radii higher than 100 au" (4.1 DALI modelling of [CI] and CO in HD 163296)
10. **Compare gas surfaces with small-dust vertical profile**: Overlay power-law fit and data points of small dust grain heights from Rich et al. 2021 on the height profiles  
  > "we added to our height profiles the power law fitting of dust grains as well as the data points from the same study." (4.3 um dust grains vertical non co-location with CO)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibration, flagging and self-calibration with the delivered pipeline script  
  > "using the pipeline script delivered with the data" (2 Observations and data reduction)
- **bettermoments** : Zeroth moment map of [CI]  
  > "the zeroth moment map of the emission by integrating from 1.3 to 10.6 km/s" (3.1 Imaging)
- **keplerian_mask** : Keplerian masking for near and far side spectra  
  > "Keplerian masking is applied by using the (cite: rich_teague_2020_4321137) implementation" (3.1 Imaging)
- **disksurf** : Extraction of the emission surface (vertical structure)  
  > "implementation of the method first presented in (cite: pintemethod)" (3.3 Vertical analysis)
- **emcee** : MCMC fit of the surface height profiles  
  > "Markov chain Monte Carlo sampling is performed to explore the distribution of parameters" (4 Discussions)
- **DALI** : Physical-chemical modelling of CO and [CI] abundances and emission  
  > "to obtain CO and \[CI\] abundance vertical profiles as well as their expected emission layers" (4.1 DALI modelling of [CI] and CO in HD 163296)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| [CI] zeroth moment integrated flux | 7.24 | 0.02 | Jy km/s | 2 | 7.24 $\pm$ $0.02$ (Jy km/s) |
| Continuum integrated flux | 3.51e-2 | 0.04e-2 | Jy | 2 | 3.51 $\pm$ $0.04 \times 10^{-2}$ (Jy) |
| Inner gas radius, CO and [CI] | 40 | not stated | au | 4 | we find an inner radius of 40 au for both tracers and an outer radius of 600 au and 500 au for CO and |
| Outer gas radius, CO and [CI] | 600 (CO), 500 ([CI]) | not stated | au | 4 | we find an inner radius of 40 au for both tracers and an outer radius of 600 au and 500 au for CO and |
| R90 of [CI] | 309.6 | +6.1/-12.1 | au | 5 | $R_{90C} = 309.6^{+6.1}_{-12.1}$au |
| R90 of CO | 323.0 | +3.9/-2.7 | au | 5 | $R_{90CO} = 323.0^{+3.9}_{-2.7}$ au |
| R90 of dust continuum | 115.14 | +6.1/-0.0 | au | 5 | $R_{90 dust}= 115.14^{+6.1}_{-0.0}$ au |
| R90([CI])/R90(dust) | 2.63 | +0.11/-0.13 | dimensionless | 5 | $R_{90C}/R_{90dust} = 2.63^{+0.11}_{-0.13}$ |
| R90(CO)/R90(dust) | 2.78 | +0.03/-0.05 | dimensionless | 5 | $R_{90CO}/R_{90dust} = 2.78^{+0.03}_{-0.05}$ |
| [CI] emission surface z/r | ~0.2 up to 300 au | not stated | dimensionless | 6 | has a ratio $z/r \sim 0.2$ up to 300 au |
| CO emission surface z/r | 0.2 to 0.3 | not stated | dimensionless | 6 | CO is located in the interval $z/r$ from 0.2 to 0.3 |
| Excess near-side flux velocity range | 5.2 to 7.3 | not stated | km/s | 3 | an overall flux excess is observed from 5.2 to 7.3 km/s |
| Decrease of convolved CO surface profile | 10% to 15% | not stated | percent | 8 | The vertical profile of CO decreases on average a 10% to 15% |
| Welch t-test p-value (convolved CO vs [CI] heights, 100-300 au) | < 1e-10 | not stated | dimensionless | 8 | The analysis yielded a p-value lower than $10^{-10}$ |
| DALI disk gas mass | 6.7e-2 | not stated | Msun | 9 | $6.7 \times 10^{-2}M_{\odot}$ |

## Qualitative findings

- [CI] and CO are co-located radially (40 to 500 au) but not vertically; CO is on average higher  
  > "We found that these tracers are collocated radially but not vertically" (abstract)
- [CI] shows excess flux on the near side extending to about 100 au  
  > "that extends up to approximately 100 au from the central star" (4 Discussions)
- DALI predicts [CI] optically thin and CO following tau=1; the model does not reproduce the near-side asymmetry  
  > "we can exclude radiative transfer effects creating the profile showed in Fig." (4.1 DALI modelling of [CI] and CO in HD 163296)

## Claim tuples

- H: [CI] and 12CO J=2-1 are co-located radially in HD 163296 | E: Keplerian PV radii and R90 from azimuthally averaged moment 0 profiles | R: Inner radius 40 au for both; outer 600 au (CO) and 500 au ([CI]); R90 309.6 au vs 323.0 au | F: Radially co-located; CO extends further, plausibly due to [CI] sensitivity | **supported**
- H: [CI], tracing the PDR, lies at or above the optically thick CO emission surface | E: disksurf emission surfaces of [CI] and CO | R: [CI] z/r ~0.2 up to 300 au, CO z/r 0.2-0.3 | F: [CI] is, on average, lower than CO, contrary to expectation | **refuted**
- H: Low angular resolution of the [CI] data causes the lower apparent height | E: Convolve CO to the [CI] beam, rerun surface extraction, Welch's t-test | R: CO profile falls 10-15% but remains significantly higher (p < 1e-10) | F: Resolution does not fully explain the difference | **partially**
- H: Small dust grains lying below the CO layer create a wedge-like PDR so [CI] sits lower | E: Overlay Rich et al. 2021 small-grain heights on the surface profiles | R: Dust profile, constrained by two points, matches the [CI] profile | F: Suggestive observational support for the wedge-like PDR | **partially**
- H: Standard DALI PDR chemistry reproduces the observed [CI] and CO surfaces | E: DALI model compared with derived surfaces | R: Matches [CI] surface; CO surface strongly underestimated beyond 100 au | F: Model agrees for [CI] but not for CO | **partially**

## Reasoning

- Why this data: Archival [CI] data allow the first direct comparison of resolved [CI] with optically thick CO  
  > "perform the first direct comparison of this tracer with optically thick line emission" (abstract)
- Why this method: Natural weighting chosen for the low sensitivity of the faint emission  
  > "This weighting was chosen to compensate for the low sensitivity of the observations as the emission is expected to be faint" (2 Observations and data reduction)
- Alternative: Three explanations for [CI] lying below CO were explored: angular resolution (not sufficient alone), dust grains not co-located with CO (wedge-like PDR), and mixing by meridional flows (expected to contribute least)  
  > "proposing 3 different effects that can contribute to the apparent non-vertical co-location of CO and" (4 Discussions); "we expect this effect to contribute the less compared to the other two we explored before" (4.4 Mixing of upper layers)
- Alternative: Robust weightings below 1 were attempted but failed to recover a surface  
  > "We were not able to recover the emission surface for values of robust parameter lower than 1 due to the low S/N." (3.3 Vertical analysis)
- How they decided it was enough: _not stated_
- Limitation (authors): [CI] inner and outer radii are limits because of low sensitivity  
  > "should be taken as an upper and lower limits for the actual values respectively" (3.2 Radial analysis)
- Limitation (authors): Lower disk side unresolved, so only the upper surface is measured  
  > "the bottom side of the disk is not resolved, therefore this method in only applied to the upper surface of the disk" (3.3 Vertical analysis)
- Limitation (authors): Asymmetry reported in earlier work not recovered; they used additional shorter observations  
  > "We were not able to measure the same asymmetry in the line" (4 Discussions)
- Limitation (authors): Only two data points constrain the dust vertical profile used for the wedge argument  
  > "Even though the vertical profile for the dust grains in HD 163296 is constrained by only two data points" (4.3 um dust grains vertical non co-location with CO)
- Caveat (inferred, ours): Only 13.1 min of integration; [CI] SNR is modest (peak 14 in channels), so surface heights near the beam size are fragile
- Caveat (inferred, ours): Surface heights from peak-finding are biased low when the upper and lower layers blend; the correction test only convolves CO
- Caveat (inferred, ours): Distance, inclination, PA and stellar mass are not stated, so reproduction depends on unpublished choices
- Caveat (inferred, ours): The wedge-PDR interpretation rests on two dust points from another paper
- Caveat (inferred, ours): DALI model details are inherited by reference and the fiducial table has an empty chemistry-time entry

## Reproducibility

- Data public (paper): Archival ALMA project 2013.1.00527.S and public DSHARP data release  
  > "We used archival ALMA band 8 observations of HD163296 from the project 2013.1.00527.S (PI: M. Kama)." (2 Observations and data reduction); "which where directly obtained from the publically available DSHARP data release" (2 Observations and data reduction)
- Products in archive: _not stated_
- Missing: Geometry and stellar mass of HD 163296
- Missing: Self-calibration and tclean parameters
- Missing: disksurf and emcee settings and priors
- Missing: DALI inputs beyond the appendix table and fitting data
- Data volume (inferred): Band 8 single execution, 13.1 min on source, 3840-channel line spw: likely a few GB raw; DSHARP 12CO cube adds to this
- Score (inferred): 3/5, Data are public and the numeric results are clear, but geometry, self-cal, imaging, fitting and DALI setup are unstated or inherited.
- Rediscovery candidate: no, Data are public and results numeric, but missing geometry and imaging/fitting settings and the DALI model make an exact redo ambiguous.

## Links

- Method: (cite: pintemethod) (Method for extracting emission surfaces from channel maps)
- Method: (cite: disksurf) (disksurf implementation of the emission surface method)
- Method: (cite: kama2016volatile); (cite: keyte_2023) (DALI fitting procedure used for the disk model)
- Method: (cite: bruderer2012warm); (cite: 2013A&A...559A..46B) (DALI code)
- Companion: (cite: https://doi.org/10.48550/arxiv.2211.16531) (Earlier analysis of the HD 163296 [CI] kinematic structure, with additional data)
- Companion: (cite: Tere) (Vertical structure of HD 163296 in CO and other tracers, compared against)
- Companion: (cite: rich2021investigating) (Small dust grain vertical profile used for comparison)
- Companion: (cite: Imlup_recent) ([CI] in IM Lup, contrasting result)
- Related: DSHARP
- Related: MAPS
- Related: ALMA project 2015.1.01137.S (PI: T. Tsukagoshi), cited as extra data used by another paper, not used here

## Checks

```json
{
 "quotes": 124,
 "quotes_ok": 124,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00531.S",
  "2013.1.00226.S",
  "2013.1.00366.S",
  "2013.1.00498.S",
  "2013.1.00601.S",
  "2013.1.00694.S",
  "2013.1.00798.S",
  "2015.1.00486.S",
  "2015.1.00964.S",
  "2016.1.00484.L"
 ],
 "codes_printed_but_missing": [
  "2015.1.01137.S"
 ],
 "numeric_results": 15,
 "numeric_problems": 0,
 "fill": {
  "facts": 109,
  "stated": 76,
  "rate": 0.697
 },
 "evidence_ok": true
}
```
