# Modelling the 3D physical structure of astrophysical sources with gass

`2017MNRAS.468..685Q` | Monthly Notices of the Royal Astronomical Society 2017 | first author: Quénard, D. | arXiv: 1704.01615 | DOI: 10.1093/mnras/stx404

Card schema 1.0 | model gemini-4-argon | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: protoplanetary_disks, star_formation
- Question: How to generate 3D physical structure models of astrophysical sources (spherical envelopes, outflows, discs) for 3D radiative transfer codes like LIME and compare the resulting synthetic cubes to single-dish and interferometric observations.  
  > "We present GASS (Generator of Astrophysical Sources Structure), a code that allows us to generate the three-dimensional (3D) physical structure model of astrophysical sources." (abstract); "This paper is focused on the results given by the association of GASS and LIME, a 3D radiative transfer code, and we show that the complex geometry observed in star-forming regions can be adequately handled by GASS + LIME." (abstract)
- Target **TW Hya**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **IRAS16293-2422**: coordinates _not stated_; z/distance 120 pc  
  > "The model is based on the physical structure of the low-mass protostar IRAS16293-2422 as derived by Crimier et al. (2010): a collapsing spherical source around a central object located at 120 pc." (B1 Physical model); distance from Crimier et al. (2010)  
  > "The model is based on the physical structure of the low-mass protostar IRAS16293-2422 as derived by Crimier et al. (2010): a collapsing spherical source around a central object located at 120 pc." (B1 Physical model)

## Data provenance

- ALMA projects: 2011.0.00001.SV
- bands: Band 6  
  > "Information about the ALMA Band 6 observations such as the beam size has been taken from Rosenfeld et al. (2012)." (6.2 Example 2 - TW Hya)
- frequencies and spectral setup: CO J = 2 -> 1, channel spacing 0.20 km s^-1  
  > "of CO J = 2 → 1 emission, centred on the rest frequency of the transition. The channel spacing is 0.20 km s [−][1] ." (Figure 15 caption)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: ALMA Science Verification  
  > "we aim at reproducing the CO J = 2 → 1 ALMA Science Verification observations of the TW Hya" (6.2 Example 2 – TW Hya)
- Line: CO J = 2 -> 1 (not stated)
- Line: 13CO J = 2 -> 1 (not stated)
- Line: HCO+ J = 1 -> 0 to J = 13 -> 12 (not stated)
- External data: 'fiducial' and 'high-q' disc models (density and temperature profiles) and ALMA Band 6 observation parameters (such as beam size) for TW Hya  
  > "This example is based on both the 'fiducial' and 'high-q' models presented in Rosenfeld et al. (2012) (see their table 2 for the input parameters)." (6.2 Example 2 - TW Hya); "Information about the ALMA Band 6 observations such as the beam size has been taken from Rosenfeld et al. (2012)." (6.2 Example 2 - TW Hya) [from Rosenfeld et al. (2012)]
- External data: Physical structure of the low-mass protostar IRAS16293-2422  
  > "The model is based on the physical structure of the low-mass protostar IRAS16293-2422 as derived by Crimier et al. (2010): a collapsing spherical source around a central object located at 120 pc." (B1 Physical model) [from Crimier et al. (2010)]
- Simulation/model as data: Synthetic 3D radiative transfer models generated with GASS and LIME (and 1D benchmarking models with RATRAN)  
  > "This paper is focused on the results given by the association of GASS and LIME, a 3D radiative transfer code, and we show that the complex geometry observed in star-forming regions can be adequately handled by GASS + LIME." (abstract); "To perform these tests, we used the RATRAN 1D version of 2013 March and the LIME version 1.5." (APPENDIX B: IMPACT OF LIME PARAMETERS)

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

- Input parameters for the fiducial and high-q models of TW Hya and ALMA Band 6 beam size  
  > "This example is based on both the 'fiducial' and 'high-q' models presented in Rosenfeld et al. (2012) (see their table 2 for the input parameters)." (6.2 Example 2 - TW Hya); "Information about the ALMA Band 6 observations such as the beam size has been taken from Rosenfeld et al. (2012)." (6.2 Example 2 - TW Hya) [from Rosenfeld et al. (2012)]
- Outflow cavity wall mathematical definition and gridding process  
  > "As mentioned in Section 2, the outflow model is based on the mathematical definition given by Visser et al. (2012) and assimilated to an ellipse (or a part of an ellipse) centred on a central object" (3.3 Outflow generation) [from Visser et al. (2012)]
- Disc temperature profile equations  
  > "The resulting temperature T(rho, z) in each cell of the disc as a function of rho and z is (Williams & Best 2014)" (3.2 Disc generation) [from Williams & Best (2014)]
- Physical structure of IRAS16293-2422 for LIME vs RATRAN benchmarking  
  > "The model is based on the physical structure of the low-mass protostar IRAS16293-2422 as derived by Crimier et al. (2010): a collapsing spherical source around a central object located at 120 pc." (B1 Physical model) [from Crimier et al. (2010)]

### Not stated but needed to reproduce (our reading)

- Number of grid points, pixel size, and image size used in GASS and LIME for the TW Hya Example 2 simulation
- Exact input files containing the density and temperature profiles of the TW Hya disc fed to GASS
- Exact ALMA beam dimensions (major axis, minor axis, position angle) taken from Rosenfeld et al. (2012) for the TW Hya convolution

## Analysis recipe

1. **Generate 3D random point grid and smooth with Voronoi cells**: Randomly distribute points in 3D computational domain (weighted by density profile for spherical sources, uniform for discs and outflows), build Voronoi diagram, and smooth grid using Lloyd's algorithm by moving points to the centre of mass of Voronoi cells (10 iterations for spheres, 5 for discs/outflows).  
  > "We based the smoothing on the Lloyd algorithm (Lloyd 1982; Springel 2010), which consists in moving every point in the centre of mass of its" (2 Grid generation); "while in GASS each grid point is directly moved to the centre of mass of the Vorono¨ı cell using 10 iterations." (2 Grid generation); "The Lloyd algorithm will then reject more points outside of the grid and to avoid this effect the number of iterations is limited to five and 5 per cent more points are added in this case." (2 GRID GENERATION)
   - software: GASS
   - parameter: 10 iterations for spherical sources (+2.5% extra points); 5 iterations for discs and outflows (+5% extra points)  
  > "To be sure that the minimum number of points will be at least around 10 000 points after rejection, 2.5 per cent more points are arbitrarily added (total of 10 250 points) during the creation of the grid." (2 GRID GENERATION); "The Lloyd algorithm will then reject more points outside of the grid and to avoid this effect the number of iterations is limited to five and 5 per cent more points are added in this case." (2 GRID GENERATION)
   - assumption: Background density of 1 cm^-3 and gas and dust temperature of 2.73 K for points moved outside structures  
  > "These points have a background density of 1 cm^-3 and gas and dust temperature of 2.73 K whereas all others parameters are set to zero." (3 CREATION OF THE PHYSICAL MODEL)
   - fitting: _not stated_
   - validation: Visual inspection of Voronoi cells and cumulative radial point distribution before and after smoothing  
  > "cells before (left) and after (right) the smoothing process with the Lloyd algorithm." (Figure 1 caption); "Cumulated number of points through the grid as a function of the radial distance in arcsec for the three different types of structure." (Figure 2 caption)
2. **Assign 3D physical properties and run 3D radiative transfer**: Interpolate physical profiles (temperature, H2 density, molecular abundance, velocity field, Doppler parameter) onto grid cells via analytical functions or external input files, generate model.c, and run non-LTE or LTE radiative transfer with LIME.  
  > "The given value for each cell is determined through an interpolation of the physical profile defined as input for each of these parameters." (3.1 Spherical sources generation); "GASS will then simply create the model.c file, taking into account all the LIME parameters set by the user." (4 LIME OPTIONS IMPLEMENTED IN GASS)
   - software: GASS, LIME, LAMDA
   - parameter: Example 1: 10 000 points, 151 channels, 100 m s^-1 spectral resolution, 0.1 arcsec pixel size, 141 pixels  
  > "The output data cube was set with 151 channels and a spectral resolution of 100 m s^-1 to cover a 15 km s^-1 bandwidth. The spatial resolution is 0.1 arcsec with 141 pixels to cover the radial size of 7 arcsec of the model." (6.1 Example 1 - 3D demonstration)
   - parameter: Benchmarking (Appendix B): 101 992 points in LIME, 191 shells in RATRAN, 71 channels, 100 m s^-1 resolution, pixel size 0.2 arcsec (and 0.02 arcsec test)  
  > "LIME number of points 101 992" (Table B1); "We therefore performed the models with a pixel size of 0.02 arcsec with a number of pixels increased from 171 to 1701 to maintain the same map size" (B4 Impact of the pixel size)
   - assumption: Gas-to-dust ratio of 100  
  > "Gas-to-dust ratio 100" (Table B1)
   - assumption: Ideal gas law, infall velocity for spherical envelope, Keplerian rotation for disc, constant velocity parallel to outflow axis plus infall for outflow  
  > "The intensity of the velocity field for each point of the grid for the spherical model is defined as an infall model by" (3.1 Spherical sources generation); "In this figure is also displayed the velocity field, supposed to follow the Keplerian rotation with the equation" (3.2 Disc generation); "The velocity field is defined along the shape of the outflow with a constant value, taking into account that the velocity vector is always parallel to the" (3.3 Outflow generation)
   - fitting: _not stated_
   - validation: Benchmarked 1D spherical model (IRAS16293-2422) in LIME against RATRAN comparing energy level population densities, line profiles, and continuum levels  
  > "In this section, we aim at showing the impact of different input parameters of LIME on the resulting data cubes and confront them to the ones given by RATRAN." (APPENDIX B: IMPACT OF LIME PARAMETERS)
3. **Post-process synthetic data cubes and compare to ALMA observations**: Average multiple model realizations to smooth grid artefacts, calculate moment maps (M0, M1, M2), and convolve synthetic data cubes with a 2D Gaussian representing the interferometric (ALMA) beam to compare with TW Hya ALMA SV channel maps.  
  > "Therefore, it is faster and more efficient to run 10 models with 10 000 points at the same time and average them rather than doing a single run with 100 000 points." (5.1 'Smoothing tool'); "A 2D Gaussian tool allows us to convolve the data cube with the observed beam of the interferometric data by giving the major and minor axes (X_FWHM and Y_FWHM) of the beam and its position angle theta." (5.5 Simulation of interferometric observations); "Once LIME has performed the radiative transfer calculations, we have used GASS to convolve the output data cube by the ALMA beam sizes." (6.2 Example 2 - TW Hya)
   - software: GASS
   - parameter: TW Hya fiducial and high-q models from Rosenfeld et al. (2012), channel spacing 0.20 km s^-1  
  > "This example is based on both the 'fiducial' and 'high-q' models presented in Rosenfeld et al. (2012) (see their table 2 for the input parameters)." (6.2 Example 2 - TW Hya); "The channel spacing is 0.20 km s^-1." (Figure 15 caption)
   - assumption: Good (u, v)-coverage with no flux filtered out when comparing 2D Gaussian convolved models to interferometric data  
  > "It is possible to directly compare the convolved predicted model with the observed data in a case where the (u, v)-coverage of the plane of sky is good and no flux is filtered out during the process." (5.5 Simulation of interferometric observations)
   - fitting: Visual comparison of channel maps for TW Hya; standard chi^2 minimization implemented for single-dish spectra and continuum  
  > "Once all the data cubes have been read and correctly convolved with GASS, the best-fitting model is calculated over all the models, following the standard chi^2 minimization value for N_spec spectra i of N_i points" (5.3 Plots of best modelled versus observed spectra); "Figs 15 and 16 present, respectively, the results of the fiducial and high-q models compared to the ALMA observations." (6.2 Example 2 - TW Hya)
   - validation: Comparison of GASS + LIME TW Hya channel maps against ALMA Science Verification observations and results from Rosenfeld et al. (2012)  
  > "We managed with GASS and LIME to reproduce the results obtained by two models of the study of Rosenfeld et al. (2012), showing that GASS is capable of performing state-of-the-art modelling of discs." (6.2 Example 2 - TW Hya)

## Software

- **GASS** : Generating 3D physical structure models (grids and physical profiles) as input for LIME, and post-treatment analysis of output hyper-spectral data cubes (smoothing, moment maps, beam convolution, chi^2 comparison).  
  > "We present GASS (Generator of Astrophysical Sources Structure), a code that allows us to generate the three-dimensional (3D) physical structure model of astrophysical sources." (abstract); "An analysis of the output hyper-spectral cube given by such radiative transfer code can be made directly in GASS using the various post-treatment options implemented, such as calculation of moments or convolution with a beam." (abstract)
- **LIME** 1.5: 3D non-LTE and LTE continuum and gas line radiative transfer calculations.  
  > "Among the choice of 3D radiative transfer codes available to date, LIME is the only one doing a full non-LTE ALI (accelerated lambda iteration) continuum and gas line radiative transfer treatment." (1 INTRODUCTION); "To perform these tests, we used the RATRAN 1D version of 2013 March and the LIME version 1.5." (APPENDIX B: IMPACT OF LIME PARAMETERS)
- **RATRAN** 1D version of 2013 March: 1D radiative transfer code used to benchmark LIME output data cubes, level populations, line profiles, and continuum levels.  
  > "In this section, we aim at showing the impact of different input parameters of LIME on the resulting data cubes and confront them to the ones given by RATRAN." (APPENDIX B: IMPACT OF LIME PARAMETERS); "To perform these tests, we used the RATRAN 1D version of 2013 March and the LIME version 1.5." (APPENDIX B: IMPACT OF LIME PARAMETERS)
- **MatLab** : Scripted version of GASS.  
  > "A scripted MatLab version is also available." (1 INTRODUCTION)
- **CASSIS** : Providing line files (.lis format) that GASS can directly read to compare modelled and observed single-dish spectra.  
  > "GASS can directly read CASSIS [6] line files (.lis format) to perform this comparison." (5.3 Plots of best modelled versus observed spectra)
- **LAMDA** : Database providing dust opacity and molecular collision files for LIME.  
  > "the GASS interface also allows the user to select a dust opacity and a collision file (if needed). These latter are provided by data bases such as the LAMDA [5] data base" (4 LIME options implemented in GASS)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Absolute averaged difference between RATRAN and LIME spectra (HCO+ J=6-5 and J=13-12, pixel size 0.2 arcsec) | < 6 | not stated | per cent | 2 | except for the J = 1 → 0 transition with beams centred on [0,0] arcsec, we find that the absolute value of this average, in any other combination of beam size and position, is less than ∼6 per cent. |
| Maximum pixel-to-pixel difference in central region (R <= 1.5 arcsec) between RATRAN and LIME (pixel size 0.2 arcsec) | 40 | not stated | per cent | 2 | In this central region, the pixel-to-pixel difference (in absolute value) can reach a value of up to 40 per cent |
| Absolute averaged difference between RATRAN and LIME spectra (HCO+ J=13-12, R = 1 arcsec beam, pixel size 0.02 arcsec) | 1 | not stated | per cent | 2 | the absolute difference is now only 1 per cent, versus 6 per cent previously. |

## Qualitative findings

- The high-q model gives a better fit to the TW Hya ALMA CO J = 2 -> 1 observations than the fiducial model, reproducing the results of Rosenfeld et al. (2012).  
  > "The high-q model gives a better fit to the observations than the fiducial model, similarly to results presented in Rosenfeld et al. (2012)." (6.2 Example 2 - TW Hya); "We managed with GASS and LIME to reproduce the results obtained by two models of the study of Rosenfeld et al. (2012), showing that GASS is capable of performing state-of-the-art modelling of discs." (6.2 Example 2 - TW Hya)
- Averaging 10 LIME models with 10 000 grid points each in GASS reduces grid artefacts and is faster than running a single model with 100 000 points.  
  > "Since each model is built with a different grid in GASS, averaging several runs reduces the artefacts due to the grid." (5.1 'Smoothing tool'); "Therefore, it is faster and more efficient to run 10 models with 10 000 points at the same time and average them rather than doing a single run with 100 000 points." (5.1 'Smoothing tool')
- Using a pixel size smaller than the scale of steep physical gradients (or increasing the anti-alias parameter) in LIME reduces continuum and line profile discrepancies with RATRAN from 6 per cent to 1 per cent in the central region.  
  > "the absolute difference is now only 1 per cent, versus 6 per cent previously." (B4 Impact of the pixel size); "the pixel size should be small enough to correctly probe the steepest gradient of the physical model over the scale that the user is interested in." (B6 Summary)

## Claim tuples

- H: Complex 3D geometries observed in star-forming regions (envelopes, discs, outflows) can be adequately modelled and analysed by coupling GASS and LIME. | E: Constructed a 3D multi-component model (envelope, protoplanetary disc, bipolar outflow) for 13CO J = 2 -> 1 in GASS, ran 10 realizations in LIME, averaged them, and computed moment 0 and moment 1 maps at various viewing angles. | R: Outflow cavities, Keplerian disc rotation, and 13CO freeze-out depletion regions are clearly identified in the resulting moment 0 and moment 1 maps. | F: The association of GASS and LIME adequately handles complex 3D geometries in star-forming regions. | **supported**
- H: GASS coupled with LIME can reproduce state-of-the-art protoplanetary disc modelling of real ALMA observations. | E: Input the fiducial and high-q disc models of TW Hya from Rosenfeld et al. (2012) into GASS, ran radiative transfer with LIME for CO J = 2 -> 1, convolved with the ALMA Band 6 beam in GASS, and compared channel maps to ALMA Science Verification data. | R: GASS and LIME successfully reproduced the channel maps of the two models from Rosenfeld et al. (2012), showing that the high-q model fits the ALMA observations better than the fiducial model. | F: GASS is capable of performing state-of-the-art modelling of protoplanetary discs. | **supported**
- H: A pixel size larger than the scale of variation of physical properties in LIME causes inaccurate continuum and line intensity calculations. | E: Benchmarked LIME v1.5 against 1D RATRAN on a spherical model of IRAS16293-2422 for HCO+ transitions, comparing pixel sizes of 0.2 arcsec and 0.02 arcsec. | R: Reducing the pixel size from 0.2 arcsec to 0.02 arcsec decreased the pixel-to-pixel discrepancy in the central region and reduced the averaged spectrum difference in a 1 arcsec beam from 6 per cent to 1 per cent for HCO+ J = 13 -> 12. | F: The pixel size in LIME must be small enough to probe the steepest physical gradient of the model (or anti-alias must be increased) to avoid distorted continuum and line results. | **supported**

## Reasoning

- Why this data: TW Hya is well studied in the literature with several standard models available, making its ALMA Science Verification CO J = 2 -> 1 observations a good candidate to test GASS on a real astrophysical source.  
  > "This disc has been well studied in the literature and several standard models are available (e.g. Thi et al. 2010; Andrews et al. 2012; Rosenfeld et al. 2012) so it is a good candidate to test GASS with a real astrophysical source." (6.2 Example 2 - TW Hya)
- Why this method: LIME is the only 3D radiative transfer code doing a full non-LTE ALI continuum and gas line treatment, and pre-generating a smoothed Voronoi grid in GASS saves computation time and provides an easy interface for complex 3D structures.  
  > "Among the choice of 3D radiative transfer codes available to date, LIME is the only one doing a full non-LTE ALI (accelerated lambda iteration) continuum and gas line radiative transfer treatment." (1 INTRODUCTION); "It is important to keep in mind that an input file is a huge gain in time since the model is created before giving it to LIME." (2 GRID GENERATION)
- Alternative: Calculating disc gas mass from Voronoi cell volumes was rejected in favour of Delaunay tetrahedra volumes because Voronoi cell volume calculation is not trivial.  
  > "An accurate mass calculation would need to consider the volume of each Vorono¨ı cell but this is not trivial, so we chose to" (3.2 Disc generation)
- Alternative: Implementing SED fitting via chi^2 minimization was delayed due to the T_dust - beta degeneracy.  
  > "Kelly et al. (2012, and references therein) have shown that there is a T_dust - beta degeneracy (producing an anti-correlation between the two) when doing chi^2 minimization of SED fitting, leading to erroneous estimates of T_dust and/or beta (see also Juvela & Ysard 2012)." (5.4 Plots of best continuum model versus observations); "We therefore delay the implementation of SED fitting to a future version of GASS." (5.4 Plots of best continuum model versus observations)
- How they decided it was enough: _not stated_
- Limitation (authors): GASS interferometric 2D Gaussian convolution tool does not account for (u,v)-filtering or antenna configurations and is only valid when (u,v)-coverage is good and no flux is filtered out.  
  > "It is possible to directly compare the convolved predicted model with the observed data in a case where the (u, v)-coverage of the plane of sky is good and no flux is filtered out during the process." (5.5 Simulation of interferometric observations); "Therefore, this tool can be used to compare models with observations but it cannot be used to predict interferometric observations since it does not take into account the position and the number of antennas for instance." (5.5 Simulation of interferometric observations)
- Limitation (authors): Some LIME options (anti-alias, line blending, polarization) are not yet implemented in GASS.  
  > "All available LIME options are not yet implemented in GASS (anti-alias, line blending, polarization,...) mainly because we need more time to include them into the code." (4 LIME OPTIONS IMPLEMENTED IN GASS)
- Limitation (authors): When multiple structures overlap, outflows and discs overwrite spherical envelope properties rather than combining them self-consistently.  
  > "This is only done for the spherical sources whereas outflows and discs impose their own physical properties in the region where they are defined, without considering the presence of the spherical sources (see Section 3.3)." (3.1 Spherical sources generation)
- Caveat (inferred, ours): Convolving a model cube with a 2D Gaussian in the image plane rather than sampling the (u,v)-plane can bias comparisons with interferometric data if extended emission is resolved out.
- Caveat (inferred, ours): The TW Hya comparison is purely visual on channel maps without quantitative residual maps or goodness-of-fit metrics.

## Reproducibility

- Data public (paper): ALMA Science Verification data ADS/JAO.ALMA#2011.0.00001.SV  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00001.SV." (Acknowledgements); "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00001.SV." (ACKNOWLEDGEMENTS)
- Products in archive: _not stated_
- Code: GASS is freely available upon request (website under construction at http://quenarddavid.wixsite.com/astrophysics/gass-code) as a standalone application and scripted MatLab version.  
  > "GASS is freely available for the community (upon request at the moment, website in construction [4] ) as a standalone application for Mac OS X, Windows and any Unix-based operating system. A scripted MatLab version is also available." (1 Introduction)
- Missing: The GASS code itself (only available upon request at the time of publication)
- Missing: Exact input density and temperature tabular files used for the TW Hya models
- Missing: Number of grid points, image size, and pixel size used for the TW Hya LIME runs
- Data volume (inferred): < 5 GB (ALMA Science Verification TW Hya Band 6 cube and synthetic LIME FITS cubes)
- Score (inferred): 55/5, Mathematical equations for 3D structure generation, post-processing, and Example 1 / Appendix B parameters are thoroughly documented, and ALMA SV data are public, but the GASS code is only available upon request and the exact numerical grid settings and input files for the TW Hya ALMA reproduction (Example 2) are delegated to Rosenfeld et al. (2012) or unstated.
- Rediscovery candidate: no, This is a software/methods paper introducing GASS; the ALMA comparison on TW Hya is a qualitative visual reproduction of an existing model from Rosenfeld et al. (2012) rather than a new quantitative measurement.

## Links

- Method: Brinch & Hogerheijde (2010) (LIME 3D radiative transfer code and grid generation/smoothing methodology)
- Method: Hogerheijde & van der Tak (2000) (RATRAN 1D radiative transfer code used for benchmarking)
- Method: Lloyd (1982); Springel (2010) (Lloyd's algorithm for Voronoi grid smoothing)
- Method: Williams & Best (2014) (Parametric protoplanetary disc temperature structure)
- Method: Chiang & Goldreich (1997); Dullemond & Dominik (2004) (Protoplanetary disc density distribution profile)
- Method: Visser et al. (2012) (Mathematical definition and gridding of outflow cavity walls)

## Checks

```json
{
 "quotes": 87,
 "quotes_ok": 87,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 3,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 85,
  "stated": 46,
  "rate": 0.541
 },
 "evidence_ok": true
}
```
