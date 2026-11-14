# The Evolution of the IR Luminosity Function and Dust-obscured Star Formation over the Past 13 Billion Years

`2021ApJ...909..165Z` | The Astrophysical Journal 2021 | first author: Zavala, J. A. | arXiv: 2101.04734 | DOI: 10.3847/1538-4357/abdb27

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type large_program_or_survey

## Science

- Fields: high_z_galaxies
- Question: Estimate the history of dust-obscured star formation back to z~7 by combining 1.2, 2 and 3 mm ALMA number counts (including new 2 mm MORA counts) with a backward evolution model of the DSFG IR luminosity function  
  > "This study aims at estimating the history of dust-obscured star formation back to $z\sim7$" (Introduction); "allow us to infer the IR luminosity function and dust-obscured star formation in the last 13 billion years of the Universe" (Introduction)
- Target **MORA 2 mm blank field (P10-P20 and P03 mosaics)**: coordinates P10-P20 mosaic centred at RA ~10h00m17s, Dec ~+02d22'30''; P03 mosaic at RA ~10h00m44s  
  > "is centered at $\alpha\rm\approx10\,h\,00\,m\,17\,s$, $\delta\approx+02^\circ\,22'\,30''$" (2 Mapping Obscuration to Reionization ALMA (MORA) Survey); z/distance _not stated_; distance from _not stated_
- Target **Archival ALMA band 3 sample in COSMOS, CDF-S and UDS (Zavala et al. 2018 3 mm sample)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2018.1.00231.S, 2018.1.00478.S, 2019.1.00838.S
- bands: 2 mm band (MORA, two tunings); band 3 (3 mm archival sample)  
  > "in two different tunings in the 2 mm band (centered at 147.3 GHz and 139 GHz, respectively)" (2 Mapping Obscuration to Reionization ALMA (MORA) Survey); "compiled archival ALMA band 3 observations toward three extragalactic legacy fields" (3 Revising the 3 mm number counts)
- frequencies and spectral setup: Two 2 mm tunings centred at 147.3 GHz and 139 GHz  
  > "in two different tunings in the 2 mm band (centered at 147.3 GHz and 139 GHz, respectively)" (2 Mapping Obscuration to Reionization ALMA (MORA) Survey)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: typical beam FWHM ~1.8'' x 1.4'' (MORA)  
  > "with a typical beamsize of $\theta_{\rm FWHM}\approx1.8''\times1.4''$" (2 Mapping Obscuration to Reionization ALMA (MORA) Survey)
- max recoverable scale: _not stated_
- sensitivity: deepest RMS 60 uJy/beam; 101 arcmin2 at or below the proposed depth of 90 uJy/beam  
  > "The deepest portion of the mosaics has an RMS of $\sigma_{\rm 2mm}=60\,\mu\rm Jy\,beam$" (2 Mapping Obscuration to Reionization ALMA (MORA) Survey); "with $101\,$arcmin$^2$ covered at or below the proposed map depth of $90\,\mu\rm Jy\,beam$" (2 Mapping Obscuration to Reionization ALMA (MORA) Survey)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: MORA: PI C. Casey (2018.1.00231.S); 3 mm sample: archival band 3 maps plus follow-up programs 2018.1.00478.S and 2019.1.00838.S (PI J. Zavala)  
  > "(ALMA project code: 2018.1.00231.S, PI: C. Casey)" (2 Mapping Obscuration to Reionization ALMA (MORA) Survey); "(ALMA projects: 2018.1.00478.S and 2019.1.00838.S; PI: J. Zavala)" (3 Revising the 3 mm number counts)
- Other facility **ASPECS (ALMA large program)**: 1.2 mm and 3 mm number counts used as fitting constraints (4.2 arcmin2, 40 continuum sources)  
  > "the 4.2 arcmin$^2$ deep ALMA large program ASPECS survey (at 1.2 mm and 3 mm;" (1 Introduction); "and the 1.2 mm and 3 mm number counts from the ASPECS survey" (4.2 Fitting methodology and data constraints)
- Other facility **GISMO/IRAM 2 mm surveys**: Literature 2 mm number counts used for comparison only  
  > "the only determinations of the number counts reported in the literature beyond our MORA survey measurements come from the GISMO/IRAM surveys" (2.1 The 2 mm number counts)
- External data: ASPECS 1.2 mm and 3 mm number counts used as fitting constraints  
  > "and the 1.2 mm and 3 mm number counts from the ASPECS survey" (4.2 Fitting methodology and data constraints) [from Gonzalez-Lopez et al. 2019, 2020 (cite: Gonzalez-Lopez2019a; Gonzalez-Lopez2020a)]
- External data: Original 3 mm archival sample and number-count procedure, revised in this paper  
  > "compiled archival ALMA band 3 observations toward three extragalactic legacy fields: COSMOS, CDF-S, and the UDS, resulting in a total of 135 individual maps" (3 Revising the 3 mm number counts) [from Zavala et al. 2018 (cite: Zavala2018c)]
- External data: Flux density of ALMA-3mm.03 (ASPECS-3mm.1) adopted from the ASPECS catalog  
  > "we thus adopt the flux density reported in the ASPECS catalog" (3 Revising the 3 mm number counts) [from Gonzalez-Lopez et al. 2019 (cite: Gonzalez-Lopez2019a)]
- External data: Backward evolution model of the DSFG population (SED library, luminosity function parameterization, fixed parameter values)  
  > "The adopted backwards evolution model is described in detail in" (4.1 Model description); "we adopt the same values as in" (4.1 Model description) [from Casey et al. 2018a,b (cite: Casey2018b; Casey2018a)]
- External data: Cosmic variance estimate from 1000 light cones of a dust continuum number-count model  
  > "from which 1000 different light cones of 400 sq. arcmin" (4.4 The history of dust-obscured star formation) [from Popping et al. 2020 built on UniverseMachine (cite: Popping2020a; Behroozi2019a)]
- Simulation/model as data: Backward evolution model: parameterized evolving IR luminosity function plus modified blackbody SED library, used to predict mm number counts  
  > "The model combines a parameterized evolving galaxy IR luminosity function with the thermal SED properties of galaxies’ dust emission to make predictions for galaxy (sub-)millimeter surveys." (4.1 Model description)

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
- final beam: typical beam ~1.8'' x 1.4''  
  > "with a typical beamsize of $\theta_{\rm FWHM}\approx1.8''\times1.4''$" (2 Mapping Obscuration to Reionization ALMA (MORA) Survey)
- final rms: 60 uJy/beam in the deepest portion  
  > "The deepest portion of the mosaics has an RMS of $\sigma_{\rm 2mm}=60\,\mu\rm Jy\,beam$" (2 Mapping Obscuration to Reionization ALMA (MORA) Survey)

### Inherited from earlier work

- MORA catalog, source extraction details and further survey description deferred to a paper in preparation  
  > "Casey et al. (in preparation) will present further details of the survey along with a description of the source catalog" (2 Mapping Obscuration to Reionization ALMA (MORA) Survey) [from Casey et al. (in preparation)]
- 3 mm number counts revised with the same procedure as the original paper  
  > "Here, we revised the 3 mm number counts following exactly the same procedure as described in" (3 Revising the 3 mm number counts) [from (cite: Zavala2018c)]
- Backward evolution model and its remaining parameter values  
  > "The adopted backwards evolution model is described in detail in" (4.1 Model description); "For the rest of the model parameters, we adopt the same values as in" (4.1 Model description) [from (cite: Casey2018b; Casey2018a) and (cite: Zavala2018c)]
- Maximum likelihood grid fit done as in earlier work  
  > "The maximum likelihood approach is done in a similar fashion as reported by" (4.2 Fitting methodology and data constraints) [from (cite: Zavala2018c)]
- Fourth parameter z_cutoff introduced in the Nelder-Mead fit  
  > "we introduce a fourth parameter, $z_{\rm cutoff}$, following" (4.2 Fitting methodology and data constraints) [from (cite: Zavala2018c)]
- CMB heating effects included following earlier work  
  > "with the CMB heating effects taken into account (following" (4.2 Fitting methodology and data constraints) [from (cite: daCunha2013a)]
- Cosmic variance definition  
  > "The cosmic variance is then defined following" (4.4 The history of dust-obscured star formation) [from (cite: Moster2011a)]
- Poisson uncertainties for small samples  
  > "Poisson uncertainties are added in quadrature according to" (2.1 The 2 mm number counts) [from (cite: Gehrels1986a)]

### Not stated but needed to reproduce (our reading)

- MORA source catalog (positions, flux densities, SNRs of the 13 sources) is deferred to Casey et al. in preparation
- ALMA calibration, CASA version, imaging task and parameters (weighting, robust, cell size, deconvolver) for MORA are not given
- Source-extraction algorithm and the exact detection procedure applied to the SNR maps are not given
- Completeness and flux-boosting correction functions as tabulated functions are not given
- The ASPECS number counts and the flux densities adopted for the revised 3 mm sample are not tabulated beyond Table 2
- Number counts tables are given but the simulated mock-survey setup (area, noise, beams per survey) used inside the model is not described
- Fixed model parameter values taken from Casey et al. 2018a (SED library details, dispersion in L-lambda_peak relation) are not given here
- Likelihood definition for the grid fit is not written explicitly

## Analysis recipe

1. **Build noise and SNR maps and extract MORA sources**: Noise map from minimum noise scaled by the inverse primary beam, or from a 2D boxcar standard deviation after sigma clipping; SNR map = primary-beam-corrected flux map / noise map; candidates found as pixels above a SNR threshold  
  > "Once we have a noise map, we simply divide the primary beam corrected flux map by this noise mosaic in order to obtain a SNR map" (2 Mapping Obscuration to Reionization ALMA (MORA) Survey); "This SNR map is then used to find source candidates by searching for pixels above a SNR threshold." (2 Mapping Obscuration to Reionization ALMA (MORA) Survey)
   - parameter: Detection threshold 5 sigma (13 sources)  
  > "We use the 13 sources detected above $5\sigma$ to estimate the first ALMA galaxy number counts at this wavelength." (abstract)
   - parameter: The two noise-map approaches agree within ~1%  
  > "Both procedures give us consistent results within $\sim1$%." (2 Mapping Obscuration to Reionization ALMA (MORA) Survey)
   - assumption: Noise is Gaussian  
  > "under the assumption that the noise in the ALMA observations is well represented by Gaussian statistics" (2.1 The 2 mm number counts)
   - fitting: _not stated_
   - validation: SNR maps well modelled by Gaussian statistics within -4.5 to 4.5 sigma; near-IR counterparts found for all but the lowest-significance source  
  > "The signal-to-noise ratio (SNR) maps are well modelled by Gaussian statistics" (2 Mapping Obscuration to Reionization ALMA (MORA) Survey); "who found near-IR counterparts for all the MORA detections with the exception of the lowest significance source in the catalog" (2.1 The 2 mm number counts)
2. **Estimate false detection rate**: Simulate Gaussian noise maps, convolve with an average synthesized beam, scale to unit standard deviation, count peaks above threshold with the same source-finding algorithm; repeat 100 times  
  > "the maps are convolved with a beam representative of the average synthesized beam in our observations" (2.1 The 2 mm number counts); "This process is repeated 100 times in order to measure the expected number of false sources and its corresponding uncertainty." (2.1 The 2 mm number counts)
   - parameter: 100 realizations; contamination distributed among the 13 sources according to their SNRs via a normal probability distribution  
  > "the contamination fraction is distributed among the 13 sources according to their SNRs with a proportionality given by a normal probability distribution" (2.1 The 2 mm number counts)
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure completeness and flux boosting by source injection**: Insert artificial sources one at a time at random positions in the real maps (bright detections removed), recover with the same extraction procedure; completeness = recovered/inserted; flux boosting = average intrinsic/recovered flux ratio  
  > "The artificial sources are inserted, one at a time, at random positions around the whole mosaic" (2.1 The 2 mm number counts); "This is done by estimating the average ratio between the sources’ intrinsic flux density and the recovered flux density in the simulations." (2.1 The 2 mm number counts)
   - parameter: Flux density bins of 25 uJy, 10,000 repetitions per bin; recovered if within ~1.5'' (one synthesized beam) of the input position  
  > "In each flux density bin of $25\,\rm\mu Jy$, we repeat this process 10,000 times in order to sample the noise variation across the maps." (2.1 The 2 mm number counts); "A source is considered recovered if it is detected within a synthesized beam from the input position ($\sim1.5''$)." (2.1 The 2 mm number counts)
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive MORA 2 mm cumulative number counts**: Sum per-source contributions eta_i = (1 - f_cont)/(zeta * A_eff) over sources above each flux density; Monte Carlo over flux density, contamination and completeness uncertainties; Poisson errors added in quadrature  
  > "the cumulative number counts, $N(>S)$, are estimated by the sum over all sources with a flux density higher than $S$" (2.1 The 2 mm number counts); "This procedure is repeated 100 times, with the mean values representing the final number counts and the 16th and 85th percentiles their associated confidence interval." (2.1 The 2 mm number counts)
   - parameter: A_eff = 184 arcmin2; 100 Monte Carlo realizations  
  > "is the total area of the MORA maps used for source extraction" (2.1 The 2 mm number counts)
   - parameter: Source MORA-10 removed for star-forming-only counts (about 40% synchrotron contamination)  
  > "we repeat all the process described above after removing this source, aiming at providing the 2 mm number counts of star-forming galaxies only" (2.1 The 2 mm number counts)
   - fitting: _not stated_
   - validation: Compared with GISMO/IRAM 2 mm counts and shark predictions  
  > "The latter are in very good agreement with our estimations while the former lie above by a factor of $\approx2.0-2.5$." (2.1 The 2 mm number counts)
5. **Revise the archival 3 mm number counts**: Recompute counts with the Zavala et al. 2018 procedure after removing three sources not recovered by follow-up (likely spurious) and replacing the flux of ALMA-3mm.03 with the ASPECS catalog value  
  > "show that three of these sources (ALMA-3mm.14, ALMA-3mm.15, and ALMA-3mm.16) are not recovered, meaning they are likely spurious detections." (3 Revising the 3 mm number counts); "we thus adopt the flux density reported in the ASPECS catalog" (3 Revising the 3 mm number counts)
   - fitting: _not stated_
   - validation: Revised counts a factor ~1.5 lower at faint flux densities, consistent with ASPECS within uncertainties  
  > "Nevertheless, the two number counts are consistent with each other within the uncertainties." (3 Revising the 3 mm number counts)
6. **Fit IR luminosity function parameters to 1.2, 2 and 3 mm number counts**: Mock observations from the backward evolution model matched to survey wavelength, depth and resolution (with CMB heating); simulated cumulative counts compared with measured counts jointly. Two methods: maximum likelihood on a 3D grid of alpha_LF, Psi_2, beta_em, and Nelder-Mead minimization of chi2 between real and modeled counts  
  > "we use two different methods: a maximum likelihood approach and a multi-dimensional minimization algorithm." (4.2 Fitting methodology and data constraints); "with values ranging from $\alpha_{\rm LF}: [-0.6,-0.2]$ in steps of 0.05, $\Psi_2: [-8.8,-2.2]$ in steps of 0.4, and $\beta_{\rm em}: [1.5,2.6]$ in steps of 0.05." (4.2 Fitting methodology and data constraints)
   - software: Nelder-Mead (Amoeba) downhill simplex, backward evolution model of Casey et al. 2018
   - parameter: Grid: alpha_LF in [-0.6,-0.2] step 0.05; Psi_2 in [-8.8,-2.2] step 0.4; beta_em in [1.5,2.6] step 0.05  
  > "with values ranging from $\alpha_{\rm LF}: [-0.6,-0.2]$ in steps of 0.05, $\Psi_2: [-8.8,-2.2]$ in steps of 0.4, and $\beta_{\rm em}: [1.5,2.6]$ in steps of 0.05." (4.2 Fitting methodology and data constraints)
   - parameter: Nelder-Mead: random initial starting point per realization, each search limited to 100 evaluations; z_cutoff = 5.5-9.0 added as fourth parameter  
  > "In each realization, we randomly vary the initial starting point of the search, with each search limited to 100 evaluations." (4.2 Fitting methodology and data constraints); "(with a range of $z_{\rm cutoff}=5.5-9.0$)" (4.2 Fitting methodology and data constraints)
   - parameter: Fixed: beta_LF = -3.0, gamma_1 = 2.8, gamma_2 = 1.0, Psi_1 = 0, z_turn = 1.6 - 0.09 Psi_2  
  > "the bright-end slope of the luminosity function is fixed to be $\beta_{\rm LF}=-3.0$." (4.1 Model description); "a modest dependence of $z_{\rm turn}$ on $\Psi_2$ of the form $z_{\rm turn}=1.6-0.09\Psi_2$ has to be adopted" (4.1 Model description)
   - assumption: Cosmology H0 = 67.7 km/s/Mpc, Omega_lambda = 0.69; Chabrier IMF for SFRs  
  > "we assume $H_0=67.7\,\rm km\,s^{-1}\,Mpc^{-1}$ and $\Omega_{\lambda}=0.69$" (1 Introduction); "and a Chabrier initial mass function" (1 Introduction)
   - assumption: Dust effective opacity tau = 1 at rest 100 um; single beta_em across all redshifts; faint and bright slopes fixed with redshift  
  > "($\tau=1$ at $\lambda_{\rm rest}=100\,\rm\mu m$)" (4.1 Model description); "each realization adopts a single value across all redshifts for all sources" (4.1 Model description)
   - assumption: AGN and synchrotron contribution negligible at these wavebands and flux ranges  
  > "AGN contribution or non-thermal emission (e.g. synchrotron emission) is expected to be negligible at these wavebands and at the flux density ranges explored here" (4.2 Fitting methodology and data constraints)
   - fitting: Best-fit = highest-probability grid point; 68%, 95% and 99.7% intervals from integrating the normalized likelihood; second method minimizes chi2 with Nelder-Mead  
  > "the confidence intervals at 68%, 95%, and 99.7% are obtained by integrating the normalized likelihood distribution." (4.2 Fitting methodology and data constraints)
   - validation: Both methods give consistent results; best-fit model reproduces counts used in the fit and other literature counts at 70-850 um  
  > "both methods provide consistent results and good constraints on the model parameters governing the IRLF" (4.3 The IRLF and best-fit parameters); "The model does reproduce the number counts at shorter wavelengths, from $70\,\mu\rm m$ to $850\,\mu\rm m$" (4.2 Fitting methodology and data constraints)
7. **Integrate the best-fit IRLF to obtain the dust-obscured SFRD with cosmic variance**: Integrate the best-fit IR luminosity function over log(L/Lsun) 9-13.8 and propagate uncertainties; add cosmic variance from 1000 light cones of 400 arcmin2  
  > "can now be calculated by integrating the best-fit infrared galaxy luminosity function" (4.4 The history of dust-obscured star formation); "The IR luminosity function is integrated over the interval log$(L/L_\odot):[9,13.8]$." (Footnote 5)
   - parameter: Cosmic variance sigma^2 = (<N^2> - <N>^2)/<N>^2 - 1/<N>, from 1000 light cones of 400 arcmin2; predictions limited to z <~ 7  
  > "from which 1000 different light cones of 400 sq. arcmin" (4.4 The history of dust-obscured star formation); "Therefore, the model predictions presented in this work are limited to $z\lesssim7.0$." (4.4 The history of dust-obscured star formation)
   - fitting: _not stated_
   - validation: Compared with other FIR/sub-mm and UV/optical CSFRD measurements and with IllustrisTNG, shark and SIDES model predictions  
  > "our results are in good agreement with the aforementioned studies, pointing towards a convergence between galaxy evolution models and observations." (4.4.1 Comparison to other measurements and model predictions)

## Software

- **Nelder-Mead (Amoeba) downhill simplex** : Multi-dimensional minimization of chi2 between real and modeled cumulative number counts  
  > "relies on a downhill simplex algorithm to perform a multidimensional minimization of a given parameter" (4.2 Fitting methodology and data constraints)
- **Backward evolution model of Casey et al. 2018** : Predicting mm number counts from an evolving IR luminosity function and SED library  
  > "The adopted backwards evolution model is described in detail in" (4.1 Model description)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of MORA sources detected above 5 sigma | 13 | not stated | dimensionless | 1 | We use the 13 sources detected above $5\sigma$ to estimate the first ALMA galaxy number counts at this wavelength. |
| MORA survey area | 184 | not stated | arcmin^2 | 0 | The project was only partially observed, covering $\rm184\,$arcmin$^2$ in two separate mosaics |
| Deepest 2 mm RMS | 60 | not stated | uJy/beam | 0 | The deepest portion of the mosaics has an RMS of $\sigma_{\rm 2mm}=60\,\mu\rm Jy\,beam$ |
| Expected number of false detections at 5 sigma | 0.8 | 0.2 | dimensionless | 2 | the expected number of false detections in the MORA catalog is $0.8\pm0.2$ |
| Flux boosting factor just above threshold | ~5 | not stated | % | 3 | we find flux boosting factors of around $5\%$ for those source detected just above our SNR threshold |
| Faint-end slope alpha_LF | -0.42 | +0.02/-0.04 | dimensionless | 6 | The faint-end slope of the infrared luminosity function is found to be flat, with $\alpha_{\rm LF}=-0.42^{+0.02}_{-0.04}$. |
| Number density evolution index Psi_2 | -6.5 | +0.8/-1.8 | dimensionless | 6 | the best-fit $\Psi_2$ value of $-6.5^{+0.8}_{-1.8}$ implies a steep redshift evolution of the IR number density |
| Dust emissivity index beta_em | 1.8 | 0.1 | dimensionless | 6 | the dust emissivity spectral index is well-constrained to be $\beta_{\rm em}=1.8\pm0.1$ |
| Cosmic variance at z>3 | ~35 | not stated | % | 7 | the cosmic variance is estimated to be $\approx35\%$ |
| Dust-obscured fraction of total SFRD at z=5 | 35 | +10/-25 | % | 7 | At $z=5$, the dust-obscured star formation represents $35\%^{+10\%}_{-25\%}$ of the total SFRD |
| Dust-obscured fraction of total SFRD at z=6 | 25 | +15/-20 | % | 7 | decreases to $25\%^{+15\%}_{-20\%}$ at $z=6$ |
| Peak epoch of dust-obscured SFRD and its share of total SFRD | z = 2-2.5; ~80% of total SFRD | not stated | redshift; % | 7 | with a peak era between $z=2-2.5$ ($\sim10-11\,$Gyr ago) and contributing around $\sim80\%$ of total SFRD |

## Qualitative findings

- Steep redshift evolution of the space density of DSFGs; dusty galaxies are rare at early epochs  
  > "This indicates that dusty star-forming galaxies are indeed *rare* at early epochs." (4.3 The IRLF and best-fit parameters)
- Three sources of the original 3 mm sample are likely spurious, so the earlier false-detection rate was underestimated  
  > "Thus, we have revised the false detection rate to be higher than the value reported in the original work of" (3 Revising the 3 mm number counts)

## Claim tuples

- H: What is the 2 mm galaxy number count from the MORA survey? | E: Source extraction at >5 sigma in the 184 arcmin2 mosaic with contamination, completeness and flux-boosting corrections | R: 13 sources above 5 sigma; counts reported in Table 1 | F: First ALMA 2 mm number counts, in good agreement with GISMO/IRAM Magnelli et al. 2019 and the shark model | **supported**
- H: Is the IR luminosity function faint-end slope flat at high redshift? | E: Joint fit of 1.2, 2 and 3 mm ALMA number counts with a backward evolution model | R: alpha_LF = -0.42 +0.02/-0.04 | F: The faint-end slope is flat, so deep pencil-beam mm surveys would not detect many more sources | **supported**
- H: How fast does the characteristic number density of DSFGs evolve at z>2? | E: Fit Psi_2 in the model to the number counts | R: Psi_2 = -6.5 +0.8/-1.8, ruling out values above ~-4 | F: Steep evolution, disfavouring the dust-rich model with Psi_2 = -2.5 | **supported**
- H: When did dust-obscured star formation dominate, and how much exists at z=5-7? | E: Integrate best-fit IRLF with cosmic variance and compare to UV/optical measurements | R: Obscured SFRD peaks at z=2-2.5, comparable to unobscured at z~4; 35% of total at z=5 and 25% at z=6 | F: Dust-obscured star formation dominated the last ~12 Gyr back to z~4, with a minor contribution in the first billion years | **supported**

## Reasoning

- Why this data: 2 and 3 mm interferometric surveys are crucial for constraining the IRLF at high redshift  
  > "which are crucial to constraining the infrared (IR) luminosity function (IRLF) at high-redshift" (1 Introduction)
- Why this method: Cumulative counts preferred over differential counts because of fewer sources per bin  
  > "The cumulative number counts are preferred over the differential number counts since the latter suffer from larger uncertainties due to the relative small number of sources in each flux density bin." (4.2 Fitting methodology and data constraints)
- Alternative: Differential counts tested instead of cumulative; results not significantly changed  
  > "Though we test that adopting the differential number counts instead do not change significantly our results." (4.2 Fitting methodology and data constraints)
- Alternative: Reversed (gamma_2 <= 0) or rapid (gamma_2 >= 1.5) L_star evolution rejected  
  > "Adopting a reversal evolution ($\gamma_2\le0$) under-predicts the number counts at wavelengths longer than $\sim850\rm\,\mu m$" (4.1 Model description)
- How they decided it was enough: _not stated_
- Limitation (authors): Several model parameters (faint and bright slopes, beta_em across redshift, L_0, Phi_0) are fixed or not unique  
  > "Therefore, in the absence of more information, we choose to fix these quantities." (4.1 Model description)
- Limitation (authors): Cosmic variance grows at z~7 and constraining power is lost  
  > "At $z\approx7.0$, the cosmic variance increases significantly and our data-sets suffer a loss of constraining power." (4.4 The history of dust-obscured star formation)
- Limitation (authors): z_cutoff is not constrained by the data  
  > "we find that $z_{\rm cutoff}$ is not well constrained by the data and has a minor impact on the analysis." (4.2 Fitting methodology and data constraints)
- Caveat (inferred, ours): The MORA catalog, calibration and imaging are all deferred to an in-preparation paper, so the key input counts cannot be rebuilt from this paper alone
- Caveat (inferred, ours): Model-dependent results: key IRLF parameters are fixed to Casey et al. 2018 values, so alpha_LF and Psi_2 errors do not include those systematic choices
- Caveat (inferred, ours): The Psi_2 uncertainty is large and asymmetric, and the SFRD fractions at z=5-6 have large uncertainties
- Caveat (inferred, ours): The 3 mm counts rest on a heterogeneous archival sample with revised false-detection rate

## Reproducibility

- Data public (paper): ALMA data archived at the ALMA science archive  
  > "This paper makes use of the following ALMA data: ADS/JAO. ALMA#2018.1.00231.S, ADS/JAO.ALMA #2018.1.00478.S, and ADS/JAO.ALMA#22019.1.00838.S, archived at" (Data and materials availability)
- Products in archive: _not stated_
- Missing: MORA source catalog and calibration/imaging recipe (deferred to Casey et al. in prep)
- Missing: Completeness and flux-boosting functions
- Missing: Backward evolution model code and fixed SED parameters from Casey et al. 2018a
- Missing: Mock-survey setup for each constraining survey
- Data volume (inferred): MORA 2 mm mosaic (184 arcmin2) plus 3 mm follow-up and archival band 3 maps: likely hundreds of GB to ~1 TB of raw/calibrated visibilities
- Score (inferred): 2/5, ALMA data are public and final numbers are given, but the catalog and processing are deferred to a paper in preparation and the model code and fixed parameters are in earlier work
- Rediscovery candidate: no, The core MORA source extraction and imaging recipe is not given, so the number counts cannot be redone from this paper alone

## Links

- Method: Zavala et al. 2018 (cite: Zavala2018c) (Original 3 mm number counts and fitting procedure)
- Method: Casey et al. 2018a,b (cite: Casey2018b; Casey2018a) (Backward evolution model)
- Companion: Casey et al. (in preparation) (MORA catalog and source properties)
- Companion: Gonzalez-Lopez et al. 2019, 2020 (cite: Gonzalez-Lopez2019a; Gonzalez-Lopez2020a) (ASPECS number counts)
- Related: MORA
- Related: ASPECS
- Related: GISMO/IRAM 2 mm surveys

## Checks

```json
{
 "quotes": 106,
 "quotes_ok": 106,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 106,
  "stated": 64,
  "rate": 0.604
 },
 "evidence_ok": true
}
```
