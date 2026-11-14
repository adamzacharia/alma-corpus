# The Empirical and Radiative Transfer Hybrid (EaRTH) Disk Model: Merging Analyses of Protoplanetary Dust Disk Mineralogy and Structure

`2024ApJ...970..137G` | The Astrophysical Journal 2024 | first author: Grimble, William | arXiv: 2405.11061 | DOI: 10.3847/1538-4357/ad4d91

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type multi_facility_alma_minor

## Science

- Fields: protoplanetary_disks
- Question: Can an empirical mid-IR mineralogy fit be combined with MCFOST radiative transfer to jointly constrain dust composition and disk structure of the MP Mus disk, using Spitzer IRS spectra (primary) and archival ALMA Band 6 continuum (secondary)  
  > "We develop and test this model by fitting high-quality infrared spectral and radio interferometric data available for the nearby T Tauri star/disk system MP Muscae (MP Mus)" (Introduction)
- Target **MP Mus**: coordinates _not stated_; z/distance 97.89 pc  
  > "We adopt a distance of 97.89 pc, as obtained from the inverse of the" (3 Results: Application to the Protoplanetary Disk Orbiting MP Mus); distance from inverse of the Gaia DR3 parallax  
  > "We adopt a distance of 97.89 pc, as obtained from the inverse of the" (3 Results: Application to the Protoplanetary Disk Orbiting MP Mus)

## Data provenance

- ALMA projects: 2017.1.01167.S
- bands: Band 6 (1.3 mm continuum)  
  > "archival continuum mapping data obtained by the ALMA radio telescope at Band 6 (Program ID 2017.1.01167.S)" (3.4 Model Images)
- frequencies and spectral setup: 229.607-247.819 GHz  
  > "with frequencies of 229.607-247.819 GHz" (3.4 Model Images)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 69 mas x 50 mas Gaussian beam, PA -11.88 deg (elsewhere the paper says the ALMA image resolution is 0.01 arcseconds, ~1 au)  
  > "with frequencies of 229.607-247.819 GHz and a 69 mas $\times$ 50 mas Gaussian beam" (3.4 Model Images); "the resolution of the ALMA image is 0.01 arcseconds" (3.3 Model Assessment)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: archival  
  > "archival continuum mapping data obtained by the ALMA radio telescope at Band 6" (3.4 Model Images)
- Other facility **Spitzer Space Telescope IRS (via CASSIS)**: Preprocessed mid-IR spectrum of MP Mus (AORKEY 5198336), the primary data fitted  
  > "We retrieved the spectrum (AORKEY 5198336) from CASSIS" (3 Results: Application to the Protoplanetary Disk Orbiting MP Mus)
- Other facility **VLT/SPHERE IRDIS**: H-band Q_phi polarized image of MP Mus (2016 March 16) compared with model images  
  > "on 2016 March 16; this image was produced by sending the data through the IRDAP pipeline" (3.4 Model Images)
- Other facility **Gaia DR3**: Parallax-based distance to MP Mus  
  > "We adopt a distance of 97.89 pc, as obtained from the inverse of the" (3 Results: Application to the Protoplanetary Disk Orbiting MP Mus)
- External data: Dust disk mass 1.44e-4 Msun, dust disk outer radius 60 au and inclination 32 deg from the ALMA analysis of MP Mus, adopted in the model  
  > "which we adopt as the inclination of our model disk along with the dust disk mass and dust disk outer radius" (3 Results: Application to the Protoplanetary Disk Orbiting MP Mus) [from (cite: 2023A&A...673A..77R)]
- External data: Effective temperature 4920 K from spectral type K1  
  > "effective temperature 4920 K based on this spectral type" (3 Results: Application to the Protoplanetary Disk Orbiting MP Mus) [from (cite: 2013ApJS..208....9P)]
- External data: Parameter values from a forthcoming ALMA-based analysis of the MP Mus disk (private communication), listed for comparison  
  > "Another set of parameter values come from a forthcoming Atacama Large Millimeter Array (ALMA)-based analysis of the disk by Aguayo, Caceres, et al. (private communication)." (3 Results: Application to the Protoplanetary Disk Orbiting MP Mus) [from Aguayo, Caceres, et al. (private communication)]
- External data: Set of mineral opacities primarily based on the two-temperature model mineral set  
  > "The set of minerals we use are primarily based on those used with the the two-temperature model by" (2.3 EaRTH Disk Modeling Approach) [from (cite: 2016ApJ...830...71F), partly (cite: 2010ApJ...721..431J)]
- Simulation/model as data: MCFOST radiative transfer models (SEDs, temperature structures, 1.3 mm and H-band images) compared with Spitzer IRS, ALMA and SPHERE data  
  > "to generate simulated images at wavelengths of the" (3.4 Model Images)

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
- final beam: 69 mas x 50 mas Gaussian beam, PA -11.88 deg (the simulated 1.3 mm image is convolved with the same beam)  
  > "the simulated 1.3 mm image is blurred with a Gaussian beam of the same parameters" (3.4 Model Images)
- final rms: _not stated_

### Inherited from earlier work

- Linear fit of component distribution constants to the stellar-subtracted Spitzer spectrum follows the 2-T model approach  
  > "via the same approach used by the 2-T model" (2.1 Empirical Dust Composition Model: Two-Zone Temperature Distribution) [from 2-T model (cite: 2009ApJ...690.1193S; 2009ApJS..182..477S)]
- Inner rim height factor chi = 6.95, the MCFOST default  
  > "we adopt the MCFOST default of $\chi=6.95$" (2.3 EaRTH Disk Modeling Approach) [from MCFOST default]
- Inner radius of the disk derived from Eq. 14 of Dullemond et al. 2001  
  > "via Eq. 14 in" (2.3 EaRTH Disk Modeling Approach) [from (cite: 2001ApJ...560..957D)]
- Maximum grain sizes of large amorphous (2 um) and crystalline (5 um) minerals set following opacities used in earlier work  
  > "based on the opacities used by" (2.3 EaRTH Disk Modeling Approach) [from (cite: 2010ApJ...721..431J)]
- DHS opacity calculation implemented in MCFOST following the Min et al. algorithm  
  > "Simulation of DHS is implemented into MCFOST following the algorithm derived by" (2.3 EaRTH Disk Modeling Approach) [from (cite: 2003A&A...404...35M)]
- Some parameters constrained empirically from standard disk models (flaring exponent, scale height)  
  > "we empirically constrain some parameters based on standard disk models" (2.3 EaRTH Disk Modeling Approach) [from (cite: 2001ApJ...547.1077C; 2001ApJ...560..957D)]

### Not stated but needed to reproduce (our reading)

- Which ALMA product of 2017.1.01167.S was used (archive image, reprocessed, which spw/continuum selection) and how the radial profile was extracted
- Any ALMA calibration, imaging (tclean) or self-calibration settings; none are given
- MCFOST version, grid, photon-packet numbers and the parameter file used
- Differential evolution settings (population size, iterations, seed) for both the TZTD and MCFOST temperature-structure fits
- Full list of minerals, optical-constant sources and size grids (deferred to an appendix not in the text) and the Spitzer IRS preprocessing and mispointing correction
- Model inclination and position angle for rendered images, stellar luminosity and the definition of NRMSE for images (units given as mJy/beam)
- Delta chi-squared procedure used for uncertainties (appendix)

## Analysis recipe

1. **Empirical TZTD fit of Spitzer IRS spectrum**: Two-zone temperature distribution model (warm and cool components): nonlinear parameters by differential evolution, component constants by linear fit  
  > "a global optimization genetic algorithm of a stochastic nature" (2.1 Empirical Dust Composition Model: Two-Zone Temperature Distribution); "we perform a linear fit of the component distribution constants to the stellar-subtracted" (2.1 Empirical Dust Composition Model: Two-Zone Temperature Distribution)
   - software: scipy
   - parameter: Temperature range 19 K to 1500 K for both zones  
  > "a range of 19 K to 1500 K, respectively, where the upper limit corresponds to a nominal dust sublimation temperature" (2.1 Empirical Dust Composition Model: Two-Zone Temperature Distribution)
   - parameter: Allowed exponent ranges: temperature distribution -1.5 to -0.1; grain size power law -3.9 to -3.1  
  > "the allowed ranges for these exponents are $-$1.5 to $-$0.1 and $-$3.9 to $-$3.1, respectively" (2.1 Empirical Dust Composition Model: Two-Zone Temperature Distribution)
   - assumption: Upper temperature limit is a nominal dust sublimation temperature  
  > "where the upper limit corresponds to a nominal dust sublimation temperature" (2.1 Empirical Dust Composition Model: Two-Zone Temperature Distribution)
   - fitting: Differential evolution (global optimizer), minimizing reduced chi-squared; priors not stated beyond parameter bounds  
  > "a global optimization genetic algorithm of a stochastic nature" (2.1 Empirical Dust Composition Model: Two-Zone Temperature Distribution)
   - validation: Reduced chi-squared of 2.63  
  > "where we find the reduced $\chi^2$ value of the fit to be 2.63" (3.1 Disk Mineralogy)
2. **Compute DHS opacities for the detected minerals**: DHS opacities for the minerals found by the empirical fit, computed in MCFOST for a range of grain sizes and the grain size power law  
  > "We then use DHS, assuming $V_{max}=0.9$, to compute the scattering and absorption opacity functions and matrices" (2.3 EaRTH Disk Modeling Approach)
   - software: MCFOST
   - parameter: Small grains 0.01-1 um; large grains minimum 1 um; large amorphous max 2 um, large crystalline max 5 um  
  > "we set small grains, assumed to be sub-$\ensuremath{\mu}m$ size, to range from 0.01-1 $\ensuremath{\mu}m$" (2.3 EaRTH Disk Modeling Approach)
   - assumption: Minimum grain size has negligible effect on the infrared SED  
  > "As minimum dust grain size has a negligible effect on the infrared SED of a disk" (2.3 EaRTH Disk Modeling Approach)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit MCFOST temperature structure to the empirical temperature distributions**: Vary seven MCFOST structural parameters; minimize NRMSE between generated and empirical temperature structures  
  > "The parameter values that minimize the normalized root mean squared error (NRMSE)" (2.3 EaRTH Disk Modeling Approach); "we vary seven other parameters" (2.3 EaRTH Disk Modeling Approach)
   - software: MCFOST, scipy
   - parameter: Viscosity alpha range 1e-4 to 1e-1  
  > "We set the range of the viscosity parameter $\alpha$ to 10$^{-4}$-10$^{-1}$" (2.3 EaRTH Disk Modeling Approach)
   - parameter: Cool-disk scale height fitted at reference radius R = 100 au  
  > "We fit the cool scale height at a reference radius of $R=100$ au." (2.3 EaRTH Disk Modeling Approach)
   - assumption: Dust settling treatment of Dubrulle et al. 1995  
  > "assuming the treatment of dust settling by" (2.3 EaRTH Disk Modeling Approach)
   - fitting: Differential evolution with bounds for each parameter  
  > "We perform this fit using differential evolution, with bounds for each parameter." (2.3 EaRTH Disk Modeling Approach)
   - validation: _not stated_
4. **Constrain disk mass, outer radius and cool-disk surface density exponent with ALMA**: Disk mass and outer radius adopted from earlier ALMA analysis; outer radius later tuned to 53 au to match the edge falloff in the ALMA image and radial profile  
  > "We derive and constrain some disk parameters" (2.3 EaRTH Disk Modeling Approach); "based on available ALMA data" (2.3 EaRTH Disk Modeling Approach); "we later tuned it to 53 au to match up with the edge falloff observed in the ALMA image and radial profile" (3.3 Model Assessment)
   - parameter: Dust mass 1.44e-4 Msun, outer radius 53 au (tuned from 60 au)  
  > "we later tuned it to 53 au to match up with the edge falloff observed in the ALMA image and radial profile" (3.3 Model Assessment)
   - fitting: _not stated_
   - validation: _not stated_
5. **Fine-tune MCFOST model to the Spitzer IRS spectrum**: Individual parameter tuning to minimize reduced chi-squared between the stellar-subtracted MCFOST SED and the IRS spectrum  
  > "This fine-tuning focuses on improving the fit to the mid-IR spectrum of the disk via minimization of the reduced" (2.3 EaRTH Disk Modeling Approach)
   - software: MCFOST
   - fitting: Manual/individual tuning after the temperature-structure fit; no Bayesian analysis because of computational cost  
  > "we were not able to perform a Bayesian analysis to extract robust estimates of the errors on our parameter determination" (3.3 Model Assessment)
   - validation: Reduced chi-squared of 10.81 vs 2.63 for the TZTD fit alone  
  > "found to be 10.81" (3.2 Disk Structure)
6. **Compare simulated 1.3 mm image with the ALMA Band 6 image**: Render MCFOST 1.3 mm image, convolve with the ALMA beam, compare images and radial profiles  
  > "The rendered 1.3 mm image is compared to archival continuum mapping data obtained by the ALMA radio telescope at Band 6" (3.4 Model Images)
   - software: MCFOST, pymcfost
   - parameter: Gaussian beam 69 mas x 50 mas, PA -11.88 deg  
  > "the simulated 1.3 mm image is blurred with a Gaussian beam of the same parameters" (3.4 Model Images)
   - fitting: _not stated_
   - validation: Model reproduces image and radial profile within 0.6 arcsec; NRMSE 1.02 (profile) and 1.90 (image) mJy/beam  
  > "the simulated disk image and radial profile well reproduce the observed image and radial profile within a radial angular size of 0.6 arcseconds" (3.4 Model Images)
7. **Test small-grain ring vs shadowing models against the SPHERE H-band image**: Amended MCFOST models: a tapered small-grain ring at 80-130 au, or an outer disk beyond 30 au with shadowing; compared with SPHERE radial profile  
  > "we first include a small grain ring in an amended model" (3.4 Model Images); "we hence tested a model to simulate this shadowing, this time without a small grain ring" (3.4 Model Images)
   - software: MCFOST, pymcfost
   - parameter: Ring from R=80 au to R=130 au, edge parameter 4.5, Rc=100 au  
  > "The radial distribution of the ring is set from R=80 au to R=130 au, with an edge parameter of 4.5" (3.4 Model Images)
   - fitting: _not stated_
   - validation: Both models give NRMSE = 0.99 normalized Q_phi units; degeneracy acknowledged  
  > "This is indicative of the inherent degeneracy in the parameters that must be considered when generating representative models of a disk" (3.4 Model Images)

## Software

- **MCFOST** : 3D radiative transfer disk modelling and opacity generation  
  > "We accomplish radiative transfer modelling in EaRTH Disk via the MCFOST code." (2.2 Radiative Transfer Model: MCFOST)
- **pymcfost** : Rendering images from MCFOST data  
  > "data were rendered by making use of pymcfost" (Acknowledgements)
- **scipy** : scipy.optimize.differential_evolution for global optimization  
  > "via the `scipy.optimize.differential_evolution` function" (2.1 Empirical Dust Composition Model: Two-Zone Temperature Distribution)
- **NumPy** : Used extensively in the program (details not stated)  
  > "The program made significant use of NumPy" (Acknowledgements)
- **AstroPy** : _not stated_
- **Matplotlib** : Graph plotting  
  > "Graph plotting was done using Matplotlib" (Acknowledgements)
- **IRDAP** : Processing the SPHERE IRDIS polarimetric data  
  > "this image was produced by sending the data through the IRDAP pipeline" (3.4 Model Images)
- **CASSIS** : Source of the preprocessed Spitzer IRS spectrum  
  > "We retrieved the spectrum (AORKEY 5198336) from CASSIS" (3 Results: Application to the Protoplanetary Disk Orbiting MP Mus)
- **HJPDOC** : Retrieval of silicate optical constants  
  > "for the retrieval of silicate optical constants" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Reduced chi-squared of TZTD fit to Spitzer IRS | 2.63 | not stated | dimensionless | 1 | where we find the reduced $\chi^2$ value of the fit to be 2.63 |
| Dust grain size power law (TZTD) | 3.1 | not stated | dimensionless | 1 | and a dust grain size power law of 3.1 |
| TZTD temperature distributions (warm: Tmax 1500 K, q -1.5; cool: Tmax 240 K, q -0.9) | T_warm = 1500 K (r/r_in)^-1.5; T_cool = 240 K (r/r_in)^-0.9 | not stated | K | 1 | The model returns a dust temperature distribution parameterization of $T_{warm}(r)=(1500~K)(\frac{r}{r_{in}})^{-1.5}$ and $T_{cool}(r)=(240~K)(\frac{r}{r_{in}})^{-0.9}$ |
| Warm large amorphous olivine fraction | 56.1 | 14.1 | percent | 1 | 56.1$\pm$14.1 |
| Warm large amorphous pyroxene fraction | 34.8 | 10.2 | percent | 1 | 34.8$\pm$10.2 |
| Cool small amorphous pyroxene fraction | 76.1 | 22.6 | percent | 1 | 76.1$\pm$22.6 |
| Cool large crystalline forsterite fraction | 15.8 | 7.8 | percent | 1 | 15.8$\pm$7.8 |
| Reduced chi-squared of EaRTH (MCFOST) fit to Spitzer IRS | 10.81 | not stated | dimensionless | 5 | found to be 10.81 |
| Warm disk flaring exponent | 0.850 | 0.007 | dimensionless | 5 | 0.850$\pm$0.007 |
| Warm disk surface density exponent | -0.57 | 0.39 | dimensionless | 5 | -0.57$\pm$0.39 |
| Warm disk outer radius | 1.30 x inner radius | 0.11 | multiples of inner radius | 5 | (1.30$\pm$0.11)$\times$Inner Radius |
| Cool disk inner radius | 10.5 x inner radius | 0.4 | multiples of inner radius | 5 | (10.5$\pm$0.4)$\times$Inner Radius |
| Cool disk scale height at R=100 au | 12.5 | 0.4 | au | 5 | 12.5$\pm$0.4 |
| Cool disk flaring exponent | 1.05 | 0.09 | dimensionless | 5 | 1.05$\pm$0.09 |
| Viscosity parameter alpha | 1e-2 | 7e-3 | dimensionless | 5 | $1\times 10^{-2}\pm 7\times 10^{-3}$ |
| Inner radius | 0.08 | 0.25 | au | 5 | 0.08$\pm$0.25 |
| Warm disk scale height at R=100 au | 1.30 | 1.18 | au | 5 | 1.30$\pm$1.18 |
| Cool disk outer radius | 53 | not stated | au | 4 | we later tuned it to 53 au to match up with the edge falloff observed in the ALMA image and radial profile |
| Maximum dust temperature in the MCFOST disk | ~1350 | not stated | K | 5 | The maximum temperature of the dust in the disk is $\sim$1350 K |
| NRMSE between observed and simulated ALMA 1.3 mm radial profile | 1.02 | not stated | mJy/beam | 6 | with a NRMSE of 1.02 mJy beam$^{-1}$ between the observed and simulated radial profile |
| NRMSE between observed and simulated ALMA 1.3 mm image | 1.90 | not stated | mJy/beam | 6 | a NRMSE of 1.90 mJy beam$^{-1}$ between the observed and simulated image |
| NRMSE of SPHERE radial profile with small-grain ring model | 0.99 | not stated | normalized Q_phi units | 7 | the radial profile well represents that of the SPHERE image, with NRMSE=0.99 normalized $Q_{\phi}$ units |

## Qualitative findings

- The MP Mus warm and cool disks are predominantly amorphous silicates, with large grains in the warm disk, small pyroxene in the cool disk, and crystalline silicates indicating grain processing  
  > "The results indicate that both disks are predominantly composed of amorphous minerals" (3.1 Disk Mineralogy)
- The EaRTH model implies a small inner cavity (0.08 au) and a gap from ~0.1 to ~0.85 au that ALMA and SPHERE could not resolve  
  > "it is possible that there is a small inner cavity in the disk of MP Mus that these images could not show" (3.3 Model Assessment)

## Claim tuples

- H: Empirical mid-IR mineralogy can be used as input to MCFOST to fit the SED with both mineralogical and structural parameters | E: TZTD fit of Spitzer IRS spectrum, then MCFOST temperature-structure fit and SED fine-tuning | R: TZTD reduced chi-squared 2.63; EaRTH reduced chi-squared 10.81 | F: The hybrid model gives a robust IR fit, though the TZTD fit alone is better | **supported**
- H: What dust composition do the warm and cool zones of the MP Mus disk have | E: TZTD fit with the new opacity set | R: Warm: large amorphous olivine 56.1 and pyroxene 34.8 percent; cool: small amorphous pyroxene 76.1 and large crystalline forsterite 15.8 percent | F: Both disks are mostly amorphous with grain growth in warm and cool regions and significant crystalline silicate | **supported**
- H: The Spitzer-constrained model implies a small inner cavity and gap not excluded by ALMA/SPHERE | E: Compared EaRTH inner radius and temperature structure with ALMA and SPHERE resolution limits | R: Inner radius 0.08 au, gap ~0.1 to ~0.85 au, below the ALMA ~1 au resolution | F: A small inner cavity is possible but not detected by current images | **partially**
- H: The MCFOST model reproduces the ALMA 1.3 mm continuum image | E: Rendered 1.3 mm image convolved with the ALMA beam and compared radial profiles | R: Good match within 0.6 arcsec, NRMSE 1.02 and 1.90 mJy/beam, but model flux falls off faster than observed | F: Model fits the inner image but is limited by simplified surface density assumptions | **partially**
- H: The SPHERE ring near 80 au is due to a small-grain ring or to shadowing | E: Two amended MCFOST models compared with the SPHERE H-band radial profile | R: Both give NRMSE 0.99; ring model gives a closer-looking image and better mid-IR SED | F: Models are degenerate, but the ring model is qualitatively closer | **partially**

## Reasoning

- Why this data: MP Mus has high-quality infrared spectral and radio interferometric data and is a nearby disk  
  > "We develop and test this model by fitting high-quality infrared spectral and radio interferometric data available" (Introduction)
- Why this method: Fit temperature structure first because it is much faster than fitting SEDs and ties MCFOST to the empirical fit  
  > "because this method is significantly faster, allowing many iterations to tune parameters" (2.3 EaRTH Disk Modeling Approach)
- Alternative: Tested shadowing of intermediate disk regions as alternative to a small-grain ring for the SPHERE ring; ring model preferred qualitatively  
  > "we hence tested a model to simulate this shadowing, this time without a small grain ring" (3.4 Model Images)
- How they decided it was enough: _not stated_
- Limitation (authors): No Bayesian error analysis because of computational cost  
  > "we were not able to perform a Bayesian analysis to extract robust estimates of the errors on our parameter determination" (3.3 Model Assessment)
- Limitation (authors): Degeneracies between model dust components, especially cool amorphous silicates  
  > "We note that degeneracies may be present between model dust components" (3.1 Disk Mineralogy)
- Limitation (authors): Simplified assumptions limit fit to the ALMA image  
  > "This is a limitation caused by some of the simplified assumptions of the EaRTH Disk Model" (3.4 Model Images)
- Caveat (inferred, ours): ALMA is only a secondary constraint; mass and outer radius were adopted from Ribas et al. 2023 rather than fitted
- Caveat (inferred, ours): Reduced chi-squared of 10.81 is large and uncertainties come from a Delta chi-squared approach, not posterior sampling
- Caveat (inferred, ours): The paper gives two different ALMA resolutions (69x50 mas beam vs 0.01 arcsec)
- Caveat (inferred, ours): Fitted vs adopted parameters, and the large uncertainty on inner radius (0.08 +/- 0.25 au), weaken the cavity claim

## Reproducibility

- Data public (paper): ALMA data are archival (2017.1.01167.S); Spitzer spectrum retrieved from CASSIS; SPHERE data not stated as archival  
  > "archival continuum mapping data obtained by the ALMA radio telescope at Band 6" (3.4 Model Images); "We retrieved the spectrum (AORKEY 5198336) from CASSIS" (3 Results: Application to the Protoplanetary Disk Orbiting MP Mus)
- Products in archive: _not stated_
- Missing: Code for the TZTD fit and EaRTH pipeline not stated as released
- Missing: ALMA image production and radial profile extraction details
- Missing: MCFOST configuration and full mineral opacity set (appendices not in the text)
- Missing: Spitzer preprocessing and mispointing correction (appendices not in the text)
- Data volume (inferred): Small: one Spitzer IRS spectrum (KB) plus one Band 6 continuum image (MB) for a single target; raw ALMA MS would be larger (likely GB scale) but is not needed if archive images are used
- Score (inferred): 3/5, Data are public and the structural parameters are tabulated with uncertainties, but ALMA image processing, MCFOST setup, opacity set and preprocessing are not fully given and no code is released
- Rediscovery candidate: no, ALMA plays a secondary role, the recipe depends on unstated MCFOST and preprocessing details, and results are model fits that are hard to redo exactly

## Links

- Method: (cite: 2009ApJ...690.1193S; 2009ApJS..182..477S) (Two-temperature empirical mineralogy model used as a basis for the TZTD)
- Method: (cite: 2009ApJ...695.1024J; 2010ApJ...721..431J) (Two-layer temperature distribution model used as a basis for the TZTD)
- Method: (cite: 2006A&A...459..797P; 2009A&A...498..967P) (MCFOST radiative transfer code)
- Method: (cite: 2003A&A...404...35M) (Distribution of hollow spheres opacity algorithm)
- Method: (cite: 2016ApJ...830...71F) (Mineral set used with the two-temperature model)
- Companion: (cite: 2023A&A...673A..77R) (ALMA analysis of MP Mus whose dust mass, outer radius and inclination are adopted)
- Companion: Aguayo, Caceres, et al. (private communication) (Forthcoming ALMA-based analysis of the MP Mus disk)
- Companion: (cite: 2016ApJ...818L..15W) (Detection of the ring in MP Mus scattered-light imaging)
- Related: ALMA 2017.1.01167.S
- Related: Spitzer IRS AORKEY 5198336 via CASSIS
- Related: VLT/SPHERE IRDIS observation of 2016 March 16

## Checks

```json
{
 "quotes": 101,
 "quotes_ok": 101,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 22,
 "numeric_problems": 0,
 "fill": {
  "facts": 104,
  "stated": 64,
  "rate": 0.615
 },
 "evidence_ok": true
}
```
