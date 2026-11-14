# `The Brick' is not a brick: a comprehensive study of the structure and dynamics of the central molecular zone cloud G0.253+0.016

`2019MNRAS.485.2457H` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Henshaw, J. D. | arXiv: 1902.02793 | DOI: 10.1093/mnras/stz471

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: milky_way_ism, star_formation
- Question: What are the internal structure and dynamics of the CMZ cloud G0.253+0.016, and is it a single coherent centrally-condensed cloud or a hierarchically structured complex of line-of-sight components?  
  > "In this paper we provide a comprehensive description of the internal dynamics of G0.253+0.016 (a.k.a. ‘the Brick’)" (abstract)
- Target **G0.253+0.016 (the Brick)**: coordinates _not stated_; z/distance 8.34 ± 0.16 kpc (assumed at Galactic centre distance)  
  > "assuming a distance to the Galactic centre of $8.34 \pm 0.16$ kpc (cite: reid_2014), which we adopt throughout this work, assuming that G0.253+0.016 is at an equivalent distance." (2 Data); distance from Reid et al. 2014  
  > "assuming a distance to the Galactic centre of $8.34 \pm 0.16$ kpc (cite: reid_2014), which we adopt throughout this work, assuming that G0.253+0.016 is at an equivalent distance." (2 Data)

## Data provenance

- ALMA projects: 2011.0.00217.S
- bands: Band 3 (3 mm), Cycle 0  
  > "This paper makes use of the ALMA Early Science Cycle 0 Band 3 observations of G0.253+0.016 originally presented in (cite: rathborne_2014; rathborne_2015)." (2 Data)
- frequencies and spectral setup: four spectral windows at 87.2, 89.1, 99.1, 101.1 GHz; 1875 MHz bandwidth each; 488 kHz channels; spectral resolution 3.4 km/s after Hanning smoothing  
  > "The correlator was configured to use four spectral windows in dual-polarization mode centred at 87.2, 89.1, 99.1, and 101.1 GHz, each with 1875 MHz bandwidth and 488 kHz (1.4-1.7 km s$^{-1}$) channel spacing." (2 Data)
- continuum bandwidth: _not stated_
- arrays: ALMA 12m, 13-point mosaic covering 3' x 1'  
  > "The ALMA 12m observations cover the full $3^{'}\,\times\,1^{'}$ extent of the cloud using a 13 point mosaic." (2 Data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.7 arcsec (~0.07 pc)  
  > "The spatial resolution of the observations is $1.7^{"}$." (2 Data)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: HNCO 4(0,4)-3(0,3) (≈87.925 GHz)
- Other facility **MALT90 (Mopra 22m)**: single-dish data combined with the ALMA data  
  > "The ALMA data were combined with single-dish data available from the Millimetre Astronomy Legacy Team 90 GHz Survey (MALT90; (cite: foster_2011; jackson_2013)) obtained with the Mopra 22m telescope." (2 Data)
- External data: Reduced ALMA Cycle 0 HNCO cube and 3 mm continuum image  
  > "For further information regarding the data reduction and image processing we refer the reader to (cite: rathborne_2015)." (2 Data) [from (cite: rathborne_2014; rathborne_2015)]
- External data: Gas kinetic temperature of 60 K  
  > "Assuming a fixed temperature of 60 K (cite: ginsburg_2016; krieger_2017), $c_{s}=0.46$  km s$^{-1}$." (3.3) [from (cite: ginsburg_2016; krieger_2017)]
- External data: Cloud radius 2.35 pc and mean density 1e4 cm^-3 for radiative transfer  
  > "we consider a uniform density sphere of fixed radius 2.35 pc (cite: federrath_2016) evaluated on a 1-D grid." (5.1.2) [from (cite: federrath_2016)]

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
- array combination: ALMA combined with MALT90 single-dish data (as in Rathborne et al.)  
  > "The ALMA data were combined with single-dish data available from the Millimetre Astronomy Legacy Team 90 GHz Survey" (2 Data)
- smoothing: _not stated_
- final beam: 1.7 arcsec synthesised beam  
  > "The spatial resolution of the observations is $1.7^{"}$." (2 Data)
- final rms: mean rms 0.8 mJy/beam  
  > "The mean rms value is $\langle\sigma_{\rm rms}\rangle=0.8$ mJy beam$^{-1}$." (footnote 15)

### Inherited from earlier work

- ALMA data reduction and image processing  
  > "For further information regarding the data reduction and image processing we refer the reader to (cite: rathborne_2015)." (2 Data) [from (cite: rathborne_2015)]
- scouse fitting procedure and tolerance definitions, AICc model selection  
  > "The procedure followed by scousepy is discussed in detail by (cite: henshaw_2016), but we highlight the key points here." (3.1) [from (cite: henshaw_2016)]
- first-moment velocity range 0-45 km/s and 3 sigma clipping  
  > "Following (cite: federrath_2016), we compute this over a velocity range of $0-45$  km s$^{-1}$ and clip all data below 3$\sigma_{\rm rms}$." (3.2) [from (cite: federrath_2016)]
- Mach number conversion equation  
  > "into an estimate of the turbulent Mach number, $\mathcal{M}_{\sigma_{v_{los}}, {\rm 3D}}$ using (cite: henshaw_2016)" (3.3) [from (cite: henshaw_2016)]

### Not stated but needed to reproduce (our reading)

- Calibration details, CASA version and imaging parameters of the Rathborne et al. cube (robust, cleaning, combination method with single-dish)
- Exact velocity window and handling of the combined ALMA+MALT90 HNCO cube used for fitting
- Manual SAA spectral fits are user-interactive; initial guesses and SAA sizes per bin (log bin edges for delta v_m) not given
- acorns parameters min_height and stop values not given
- Radiative transfer grid ranges and TORUS/RADEX collision rates and setup
- Whether the 0.03 mJy/beam masking threshold is a typo relative to the 0.8 mJy/beam rms

## Analysis recipe

1. **Decompose HNCO spectra into Gaussian components**: scousepy semi-automated multi-component Gaussian fitting with spectral averaging areas, manual fits in pyspeckit, then automated fitting of all pixels  
  > "The spatially averaged spectra extracted from each SAA are then manually fitted by the user. Fitting is performed interactively using pyspeckit" (3.1)
   - software: scousepy, pyspeckit
   - parameter: T1=3.0, T2=1.0, T3=T4=3.0, T5=0.5; spectra with peak below 0.03 mJy/beam masked  
  > "We set both of these tolerance levels to 3.0." (3.1)
   - assumption: spectra decomposable into Gaussians; HNCO likely optically thin  
  > "we assume that the spectra can be decomposed into individual Gaussians." (3.1)
   - fitting: Best solution per pixel chosen by smallest corrected AIC  
  > "the final best-fitting solution for each pixel is that which has the smallest value of the (corrected) Akaike Information Criterion" (3.1)
   - validation: _not stated_
2. **Moment analysis and velocity gradients**: First- and second-order moments; fit first-degree bivariate polynomial to velocity field to get gradient magnitude and direction  
  > "The velocity gradient is estimated as a fit to all $\{l,b,v\}$ data points assuming that the velocity field is well approximated by a first-degree bivariate polynomial" (3.2)
   - assumption: distance 8.34 kpc  
  > "assuming a distance to the Galactic centre of $8.34 \pm 0.16$ kpc" (2 Data)
   - fitting: least squares  
  > "are free-parameters in the least squares fit" (3.2)
   - validation: compared to Federrath et al. 2016, MALT90 and simulations  
  > "The computed velocity gradient is consistent with that reported by (cite: federrath_2016)" (3.2)
3. **Velocity dispersions and Mach number**: Mean of scousepy 1D dispersions; turbulent Mach number from subtracting thermal broadening  
  > "which we estimate by subtracting the contribution of thermal motions from the observed 1-D line-of-sight velocity dispersion in quadrature." (3.3)
   - parameter: T_kin = 60 K, mean molecular mass 2.33 amu, HNCO 43 amu  
  > "Assuming a fixed temperature of 60 K (cite: ginsburg_2016; krieger_2017), $c_{s}=0.46$  km s$^{-1}$." (3.3)
   - assumption: uniform temperature; no unresolved coherent motions  
  > "we assume a uniform temperature" (3.3)
   - fitting: _not stated_
   - validation: compared to dispersion-size relations of Shetty et al. 2012 and Kauffmann et al. 2017  
  > "we can predict the magnitude of the velocity dispersions measured on $0.07$ pc scales" (3.3)
4. **Hierarchical clustering of components**: acorns agglomerative clustering in position, centroid velocity and velocity dispersion on robust components, then relax linking lengths by 50%  
  > "we then relaxed all linking lengths (position, velocity, velocity dispersion) by 50% to further develop the clusters." (4.1)
   - software: acorns
   - parameter: min radius 1.2 arcsec; linking 1.2 arcsec, 3.4 km/s in velocity and dispersion; robust = peak > ~5x rms and sigma > ~1.4 km/s  
  > "we specify that the euclidean distance between the points and the absolute difference in both their measured centroid velocity and velocity dispersion can be no greater than $1.2^{''}$ and 3.4  km s$^{-1}$, respectively." (4.1)
   - fitting: _not stated_
   - validation: Result changes little with 1.7 km/s linking lengths (1231 clusters)  
  > "In this case, the total number of clusters identified is 1231 and these clusters contain $\sim95\%$ of the data." (footnote 17)
5. **Statistics of dominant trees**: Per-tree velocity PDF moments, normality tests (D'Agostino, Anderson-Darling), gradient fits, gradient-subtracted dispersions, KS tests of dispersions  
  > "A two-sample Kolmogorov-Smirnov test for each of the six unique parings of the four tree samples reveals that none of the samples are drawn from the same distribution" (4.3.2)
   - software: scipy
   - fitting: normal distribution fit to centroid velocities  
  > "we fit a normal distribution to the centroid velocities measurements associated with each tree" (4.3.1)
   - validation: _not stated_
6. **Test optical thickness of HNCO**: Radiative transfer with LVG (RADEX) and 3-D spherical model with LTE/NLTE in TORUS over density-abundance grid, compared with observed brightness temperatures  
  > "We perform radiative transfer calculations using both the large velocity gradient (LVG) approximation and a 3-D model evaluated on a 1-D grid." (5.1.2)
   - software: TORUS, RADEX
   - parameter: T_kin 60 K, line width 4.4 km/s, sphere radius 2.35 pc, abundance 1e-9, density 1e4 cm^-3  
  > "We adopt a kinetic temperature of 60 K, (cite: ginsburg_2016) and a fixed turbulent line width of 4.4  km s$^{-1}$" (5.1.2)
   - assumption: spherical symmetry; uniform abundance, density and temperature  
  > "our calculations assume spherical symmetry, as well as a uniform abundance, density, and temperature." (5.1.2)
   - fitting: _not stated_
   - validation: compared with observed T_B distribution (~1.75 K mean)  
  > "three standard deviations from the mean scousepy-derived brightness temperature $\sim1.75$ K" (5.1.2)

## Software

- **scousepy** : spectral line decomposition  
  > "Our kinematic decomposition of the ALMA HNCO data is performed using a newly-developed Python implementation of the Semi-Automated multi-COmponent Universal Spectral-line fitting Engine (scouse)" (3.1)
- **acorns** : hierarchical clustering of decomposed data  
  > "a hierarchical n-dimensional clustering algorithm designed for use with discrete spectroscopic data" (abstract)
- **pyspeckit** : interactive fitting of SAA spectra  
  > "Fitting is performed interactively using pyspeckit" (3.1)
- **TORUS** : Monte Carlo NLTE/LTE radiative transfer  
  > "We employ the NLTE statistical equilibrium solver in the Monte Carlo radiation transport code TORUS (cite: rundle_2010)" (5.1.2)
- **astrodendro** : comparison with acorns on test data  
  > "the bottom right-hand image of Fig. [19] displays the result of running astrodendro on the same data cube." (9.3)
- **spectralcube** : listed as used software  
  > "spectralcube (part of the radio-astro-tools package hosted at <http://radio-astro-tools.github.io/>)" (Software)
- **scikit-learn** : listed as used; generated test data  
  > "The filament was generated using the clustering examples in Python’s scikit-learn package." (9.2)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| mean 1D line-of-sight velocity dispersion | 4.4 | 2.1 (std dev) | km/s | 3 | with a mean value $\langle\sigma_{v_{los}, {\rm 1D}}\rangle=4.4\,{\rm km\,s^{-1}}$ (median $=4.0$  km s$^{-1}$) and a standard deviation of $2.1\,{\rm km\,s^{-1}}$. |
| mean turbulent Mach number | 16.45 | 0.01 | dimensionless | 3 | we derive a mean Mach number of $\langle\mathcal{M}_{\sigma_{v_{los}}, {\rm 3D}}\rangle~=~16.45\,\pm~\,0.01$ |
| velocity gradient from moment 1 | 4.0 | not stated | km/s/pc | 2 | we find $4.0$ km s$^{-1}$ pc$^{-1}$ |
| velocity gradient from scousepy | 4.3 | not stated | km/s/pc | 2 | Here, we find $\mathscr{G}=4.3$ km s$^{-1}$ pc$^{-1}$ |
| scousepy components fitted | 457264 components in 133065 of 315219 pixels | not stated | count | 1 | This resulted in best-fitting solutions to 133065 out of a total 315219 pixels |
| acorns forest | 1182 clusters, 195 trees | not stated | count | 4 | the forest consists of a total of 195 trees. |
| ratio sigma_los/sigma_pos | 1.2 | 0.3 | dimensionless | 5 | $\langle \sigma_{v_{los}, {\rm 1D}} /\sigma_{v_{pos}, {\rm 1D}} \rangle=1.2\,\pm\,0.3$ |
| per-tree sigma_pos (A,B,C,D) | 3.5, 5.2, 4.6, 4.5 | not stated | km/s | 5 | we measure $\sigma_{v_{pos}, {\rm 1D}} = \{3.5, 5.2, 4.6, 4.5\}$  km s$^{-1}$ |

## Qualitative findings

- HNCO is likely optically thin and the cloud is a hierarchically structured complex of line-of-sight velocity components, not a single centrally condensed cloud  
  > "G0.253+0.016 is a complex, hierarchically-structured molecular cloud exhibiting an intricate network of velocity components situated along the line-of-sight." (6)

## Claim tuples

- H: Moment analysis adequately describes the kinematics of the Brick | E: Compare scousepy decomposition with moment maps | R: Dispersion from moments is 11.1 km/s versus 4.4 km/s from fits; multiple components in ~96% of the map | F: Moment analysis misses substantial kinematic structure | **supported**
- H: Velocity dispersions follow steep CMZ dispersion-size relations | E: Compare measured 0.07 pc dispersions to predictions | R: Measured 4.4 km/s versus predicted ~0.5-1.0 km/s | F: Dispersions broader than predicted; possibly large line-of-sight depth | **supported**
- H: The Brick is a single coherent centrally-condensed cloud with depletion | E: Radiative transfer for HNCO optical depth and kinematic argument | R: HNCO optically thin unless abundance enhanced by 1-2 orders of magnitude; PPV profile requires unobserved gradients | F: Scenario disfavoured | **supported**
- H: The C-shaped arc is relic evidence of formation by cloud-cloud collision | E: acorns tree association of the arc | R: Arc is ~17% of fitted components, exclusive to tree B | F: Unlikely a relic of formation of the whole cloud | **supported**

## Reasoning

- Why this data: HNCO selected as it is bright and extended  
  > "we select the HNCO 4(0,4)–3(0,3) transition (rest freq. $\approx~87.925$ GHz) as our primary tracer of the kinematics since it is bright and extended." (2 Data)
- Why this method: _not stated_
- Alternative: Baked Alaska centrally condensed depleted cloud; optically thick scenario; cloud-cloud collision formation  
  > "(cite: rathborne_2014a) favour the former of the two scenarios, which we assess in this section." (5.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Coarse spectral resolution (3.4 km/s) may overestimate dispersions and Mach number; Mach number is an upper bound  
  > "This should be taken as an upper bound on the level of turbulent motion" (3.3)
- Limitation (authors): Cloud line-of-sight extent unknown; PPV not equivalent to physical space  
  > "we do not know the extent of the cloud along the line-of-sight." (3.3)
- Caveat (inferred, ours): Gaussian decomposition at 3.4 km/s resolution with unresolved components allowed may bias dispersions
- Caveat (inferred, ours): Isotropy ratio interpretation as geometry is speculative and untested with simulations
- Caveat (inferred, ours): Uniform T=60 K and spherical radiative transfer are crude
- Caveat (inferred, ours): Results depend on user-interactive SAA fits and acorns linking lengths

## Reproducibility

- Data public (paper): ALMA project 2011.0.00217.S acknowledged; Rathborne provided the data product  
  > "We would like to thank Jill Rathborne for making the data product used in this paper available for use." (Acknowledgements)
- Products in archive: _not stated_
- Code: scousepy and acorns on GitHub  
  > "acorns (<https://github.com/jdhenshaw/acorns>)" (Software)
- Missing: Combined ALMA+MALT90 HNCO cube (reduced by Rathborne et al.) not described in detail
- Missing: Manual SAA fits not recorded
- Missing: Full acorns and radiative transfer inputs
- Data volume (inferred): Tens of GB raw; processed HNCO cube a few GB
- Score (inferred): 3/5, Code is public and key parameters are given, but the cube is a prior-paper product and manual SAA fitting is not reproducible exactly.
- Rediscovery candidate: no, Depends on a combined data product from earlier work and interactive manual fitting.

## Links

- Method: (cite: henshaw_2016) (original scouse algorithm)
- Method: (cite: rathborne_2015) (data reduction of the ALMA cube)
- Companion: (cite: federrath_2016) (previous moment analysis of same data)
- Companion: (cite: rathborne_2014a) (Baked Alaska model from MALT90)
- Related: MALT90
- Related: CMZoom

## Checks

```json
{
 "quotes": 68,
 "quotes_ok": 68,
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
  "stated": 53,
  "rate": 0.596
 },
 "evidence_ok": true
}
```
