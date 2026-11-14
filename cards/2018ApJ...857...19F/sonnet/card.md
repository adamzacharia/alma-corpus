# The ALMA View of GMCs in NGC 300: Physical Properties and Scaling Relations at 10 pc Resolution

`2018ApJ...857...19F` | The Astrophysical Journal 2018 | first author: Faesi, Christopher M. | arXiv: 1801.06238 | DOI: 10.3847/1538-4357/aaad60

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, milky_way_ism, star_formation
- Question: Do GMCs in NGC 300, resolved at 10 pc and 1 km/s, follow the Milky Way scaling relations and mass spectrum, and what sets GMC properties (global vs local environment such as pressure)?  
  > "To test these possibilities, it is necessary to match as nearly as possible the spatial and spectral resolution and sensitivity of Milky Way studies." (Introduction)
- Target **NGC 300 (48 regions near HII regions, DCL6 to DCL140)**: coordinates center 00:54:53.48 -37:41:03.8 (J2000); pointings in Table 1  
  > "we are able to achieve $< 10$ pc and $1~\ensuremath{\rm{km}~\rm{s}^{-1}}$ resolution at the 1.93 Mpc distance of the galaxy (cite: 2004AJ....128.1167G)" (Introduction); "central coordinates of \[$00^{\rm h}54^{\rm m}53^{\rm s}.48$, $-37^{\circ}41\ensuremath{'}03\ensuremath{''}.8$\] (J2000), an inclination of $39.8^{\circ}$" (The GMC distribution across NGC 300); z/distance 1.93 Mpc  
  > "we are able to achieve $< 10$ pc and $1~\ensuremath{\rm{km}~\rm{s}^{-1}}$ resolution at the 1.93 Mpc distance of the galaxy (cite: 2004AJ....128.1167G)" (Introduction); "central coordinates of \[$00^{\rm h}54^{\rm m}53^{\rm s}.48$, $-37^{\circ}41\ensuremath{'}03\ensuremath{''}.8$\] (J2000), an inclination of $39.8^{\circ}$" (The GMC distribution across NGC 300); distance from Gieren et al. 2004 (cite: 2004AJ....128.1167G)  
  > "we are able to achieve $< 10$ pc and $1~\ensuremath{\rm{km}~\rm{s}^{-1}}$ resolution at the 1.93 Mpc distance of the galaxy (cite: 2004AJ....128.1167G)" (Introduction); "central coordinates of \[$00^{\rm h}54^{\rm m}53^{\rm s}.48$, $-37^{\circ}41\ensuremath{'}03\ensuremath{''}.8$\] (J2000), an inclination of $39.8^{\circ}$" (The GMC distribution across NGC 300)

## Data provenance

- ALMA projects: 2013.1.00586.S
- bands: Band 6, CO(2-1) at 230.538 GHz  
  > "The ALMA Band 6 correlator was set up to have three spectral windows" (2.1 ALMA observations)
- frequencies and spectral setup: Two line windows (122 kHz, 469 MHz bandwidth) at 230.538 and 219.560 GHz; one continuum window (15.625 MHz, 1.875 GHz bandwidth) at ~231.5 GHz  
  > "two spectral line windows with resolution 122 kHz ($\sim0.16~\ensuremath{\rm{km}~\rm{s}^{-1}}$), bandwidth 469 MHz, and centered at 230.538 GHz" (2.1 ALMA observations)
- continuum bandwidth: _not stated_
- arrays: ALMA 12 m array  
  > "All targets were observed with the ALMA 12 m array during Cycle 2 on 9, 12, and 15 December 2014." (2.1 ALMA observations)
- configurations: C34-2/1  
  > "ALMA was in configuration C34-2/1 for all three observing nights" (2.1 ALMA observations)
- baselines: 15.0 m to 348.5 m  
  > "arranged with baselines ranging from 15.0 m to 348.5 m" (2.1 ALMA observations)
- angular resolution: ~1.5 x 0.9 arcsec (14 pc x 8.4 pc), PA ~90 deg  
  > "The synthesized beam (i.e., final angular resolution) is approximately $1.5\ensuremath{''} \times 0.9\ensuremath{''}$" (2.3 Imaging and deconvolution)
- max recoverable scale: 10.7 arcsec (at 230.5 GHz), ~100 pc  
  > "a maximum recoverable scale of $10.7\ensuremath{''}$ (at 230.5 GHz)" (2.1 ALMA observations)
- sensitivity: RMS 6.6-6.8 mJy/beam per 1 km/s channel (~130 mK)  
  > "The RMS noise in the final data cubes ranges between 6.6 and 6.8 mJy beam$^{-1}$, which corresponds to a surface brightness sensitivity of about 130 mK" (2.3 Imaging and deconvolution)
- time on source: 3.03 minutes per target  
  > "adding up to a total on-source time of 3.03 minutes per target" (2.1 ALMA observations)
- observing dates: 9, 12 (Table 2 lists 13), 15 December 2014  
  > "during Cycle 2 on 9, 12, and 15 December 2014" (2.1 ALMA observations)
- pi or archival as stated: PI C. Lada project  
  > "project code 2013.1.00586.S; PI: C. Lada" (2 Observations and Data)
- Line: 12CO J=2-1 (230.538 GHz)
- Line: C18O J=2-1 (219.560 GHz)
- Other facility **APEX**: Single-dish CO(2-1) survey defining targets, velocities, alpha_CO and used to check flux recovery  
  > "representing all 42 CO detections plus 6 selected CO nondetections from the Atacama Pathfinder EXperiment (APEX) survey of F14" (2 Observations and Data)
- Other facility **Herschel/SPIRE**: 250 um image used to show regions and assign environmental zones  
  > "Figure [1](#fig:almaobs) shows the observed regions on a 250 $\mu$m *Herschel*/SPIRE image obtained by our team" (2 Observations and Data)
- External data: APEX CO integrated intensities, velocities, region metallicity-based alpha_CO  
  > "CO integrated intensity $I_{\rm CO}$, velocity centroid $v_0$, and spectral Gaussian fit FWHM from the APEX single dish observations of (cite: Faesi:2014ib)" (Table 1) [from (cite: Faesi:2014ib)]
- External data: HI gas surface density, velocity dispersion, stellar surface density, v_rot,max for pressure calculation  
  > "We use their results (from their Table 2) for these two quantities." (6.3 Midplane disk pressure) [from (cite: 2011MNRAS.410.2217W)]
- External data: M51 GMC catalog for comparison  
  > "We have downloaded the catalog kindly made publicly available by (cite: 2014ApJ...784....3C)" (6.2 The role of environment: NGC 300 vs. M51) [from (cite: 2014ApJ...784....3C)]

## Processing

### Calibration

- pipeline or manual: Manual calibration by NA ALMA Science Center  
  > "Calibration was performed manually by the North American ALMA Science Center team using CASA version 4.3.0." (2.2 Data processing)
- casa version: CASA 4.3.0 (calibration)  
  > "using CASA version 4.3.0" (2.2 Data processing)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Uranus (Butler-JPL-Horizons 2012 model)  
  > "flux calibration using the Butler-JPL-Horizons 2012 model for Uranus to set the flux scale" (2.2 Data processing)
- flux scale uncertainty: 1% relative, 5% absolute  
  > "We adopt ALMA’s fiducial 1% relative and 5% absolute flux calibration uncertainty" (2.2 Data processing)
- self calibration: _not stated_

### Imaging

- task: CASA CLEAN, manual iterative  
  > "We `CLEAN`ed each of the 48 regions manually and iteratively." (2.3 Imaging and deconvolution)
- deconvolver: multiscale CLEAN, scales 1, 2, 5, 10, 15 x synthesized beam  
  > "we set the `multiscale` parameter to factors of 1, 2, 5, 10, and 15 times the synthesized beam" (2.3 Imaging and deconvolution)
- weighting robust: natural weighting  
  > "thus we used natural weighting" (2.3 Imaging and deconvolution)
- uv taper: _not stated_
- cell size: 0.15 arcsec pixels  
  > "The final cubes have $0.15~\ensuremath{''}$ pixels and a spatial extent of $48~\ensuremath{''}$." (2.3 Imaging and deconvolution)
- image size: 48 arcsec extent; 200 channels centered on 144 km/s  
  > "We imaged 200 velocity channels centered on the NGC 300 systemic velocity of $144~\ensuremath{\rm{km}~\rm{s}^{-1}}$" (2.3 Imaging and deconvolution)
- masking: Hand-drawn polygon CLEAN box around significant coherent emission, extended iteratively; 100 iterations per cycle, gain 0.1, threshold 4 sigma, then final 2 sigma  
  > "We ran `CLEAN` for 100 iterations at a time with loop gain set to 0.1 and a threshold of $4\sigma$" (2.3 Imaging and deconvolution)
- multiscale scales: _not stated_
- continuum subtraction: None; no continuum detected  
  > "No continuum emission was detected in any of the regions studied, and thus we did not attempt to continuum-subtract the spectral line data." (2.4 Continuum data and dust emission upper limits)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Spectral resolution smoothed to 1 km/s  
  > "we smoothed our spectral images to $1~\ensuremath{\rm{km}~\rm{s}^{-1}}$ velocity resolution" (2.3 Imaging and deconvolution)
- final beam: 1.5 x 0.9 arcsec, PA ~90 deg  
  > "with a position angle of roughly $90^{\circ}$ (measured E from N)" (2.3 Imaging and deconvolution)
- final rms: 6.6-6.8 mJy/beam (continuum 0.13-0.15 mJy/beam)  
  > "The RMS noise in the final data cubes ranges between 6.6 and 6.8 mJy beam$^{-1}$" (2.3 Imaging and deconvolution)

### Inherited from earlier work

- APEX comparison procedure follows pilot paper  
  > "The procedure follows that of (cite: Faesi:2016bl), which we briefly summarize again here." (2.5 Comparison to APEX single dish observations) [from (cite: Faesi:2016bl)]
- Cloud identification scheme follows pilot paper, using modified CPROPS  
  > "The cloud identification scheme follows (cite: Faesi:2016bl), which are briefly summarized here." (3 Cloud identification and characterization) [from (cite: Faesi:2016bl); Rosolowsky & Leroy 2006]
- alpha_CO per region from metallicity gradient parameterization (Bolatto et al. 2013)  
  > "We again take the parameterization of $\alpha_{\rm CO}$ from (cite: Bolatto:2013hl)" (3.2 Improving physical parameter estimates) [from (cite: Bolatto:2013hl); F14 (cite: Faesi:2014ib)]
- Size correction factor 1.2 for CO-dark gas  
  > "we simply assume the prediction of (cite: 2010ApJ...716.1191W) that $R_{\rm{H}_2}/R_{\rm CO} \approx 1.2$" (3.2 Improving physical parameter estimates) [from (cite: 2010ApJ...716.1191W)]
- NGC 300 geometry parameters as in F14  
  > "We adopt the same parameters for NGC 300 for these calculations as in F14" (The GMC distribution across NGC 300) [from (cite: Faesi:2014ib)]

### Not stated but needed to reproduce (our reading)

- Exact CASA version used for re-imaging (only calibration version 4.3.0 given)
- Hand-drawn CLEAN polygons per region are not provided
- Line-free channel ranges for noise estimation
- Exact CPROPS modifications (elliptical beam) code not public (private communication)
- Per-region alpha_CO values from F14 not tabulated here
- uv-taper/robust not needed (natural) but tclean parameters like gridder/niter limits per region unspecified
- ODR and bootstrap implementation details and random seeds

## Analysis recipe

1. **Calibrate and image CO(2-1) cubes**: Manual calibration, then multiscale CLEAN with hand-drawn masks to 4 sigma then 2 sigma, natural weighting, 1 km/s channels  
  > "we re-did the entire imaging process in order to tailor the deconvolution algorithm for our particular science goals" (2.3 Imaging and deconvolution)
   - software: CASA
   - parameter: scales 1,2,5,10,15 x beam; 0.15 arcsec pixels; 100 iterations per cycle; gain 0.1  
  > "We ran `CLEAN` for 100 iterations at a time with loop gain set to 0.1 and a threshold of $4\sigma$" (2.3 Imaging and deconvolution)
   - fitting: _not stated_
   - validation: Convergence tests on DCL88-126 (CLEANed flux plateau, residuals look like noise); single vs per-channel boxes gave no significant difference  
  > "We found no significant difference in either RMS noise or cloud properties in comparing these approaches" (2.3 Imaging and deconvolution)
2. **Check flux recovery vs APEX**: Multiply ALMA cube by 27 arcsec Gaussian APEX beam, integrate masked pixels, sum 40 km/s window, ratio to APEX  
  > "we multiplied each plane of the data cube by the APEX beam profile, which we estimate as a Gaussian with FWHM 27$\ensuremath{''}$" (2.5 Comparison to APEX single dish observations)
   - parameter: 3 sigma per-pixel mask; 40 km/s window  
  > "we summed the spectral flux in a $40~\ensuremath{\rm{km}~\rm{s}^{-1}}$ wide window centered on the H I velocity" (2.5 Comparison to APEX single dish observations)
   - fitting: _not stated_
   - validation: Median F_rec 0.63 consistent with SMA pilot  
  > "We find a median $\mathcal{F_{\rm rec}}$ of 0.63 with typical uncertainties of about 0.2" (2.5 Comparison to APEX single dish observations)
3. **Identify and decompose GMCs**: Modified CPROPS: 4 sigma adjacent-voxel seeds, 2 sigma edge, local maxima in 15 pc x 15 pc x 2 km/s cube, SIGDISCONT=5, modified CLUMPFIND assignment; remove duplicates and clouds beyond 29 arcsec  
  > "For our final catalog presented here, we use `SIGDISCONT`=5" (3 Cloud identification and characterization)
   - software: CPROPS
   - parameter: candidate clouds larger than one beam, peak >1 K above merge level  
  > "have a peak brightness temperature $>1~K$ ($\sim51$ mJy for the typical synthesized beam sizes in these observations) above the merge level" (3 Cloud identification and characterization)
   - fitting: _not stated_
   - validation: SIGDISCONT experiments (0,1,2,5,999), added-noise experiments, duplicate-cloud comparison  
  > "We systematically tested `SIGDISCONT` values of 0, 1, 2, 5, and 999." (8 CPROPS parameter experiments)
4. **Derive cloud properties**: R (eta=1.91, deconvolved, extrapolated to 0 K, x1.2), linewidth, L_CO, M_lum=alpha_CO/R21 L_CO, M_vir=189 dV^2 R, alpha_vir, Sigma; bootstrap uncertainties  
  > "Uncertainties in the independent properties are computed using a bootstrap method with 1000 iterations." (3.1 Cloud properties)
   - software: CPROPS
   - parameter: D=1.93 Mpc; R21=0.7; alpha_CO,MW=4.35; Sigma100_GMC=0.69  
  > "arriving at $\Sigma^{100}_{\rm GMC} = 0.69$, i.e. a GMC surface density of $69~\ensuremath{M_{\odot}}$ pc$^{-2}$" (3.2 Improving physical parameter estimates)
   - assumption: Metallicity from radial gradient, CO(2-1)/CO(1-0)=0.7, R_H2/R_CO=1.2, truncated power-law density with beta=1  
  > "This formulation (cite: Solomon:1987uq) assumes a truncated power law density distribution $\rho \propto R^{-\beta}$, taking $\beta = 1$" (3.1 Cloud properties)
   - fitting: _not stated_
   - validation: Sizes below 5 pc discarded; final sample 121 clouds  
  > "We thus exclude all clouds with $R<5$ pc (approximately half our spatial resolution) from the majority of the remaining analysis presented here." (4 Results)
5. **Fit mass spectrum**: Maximum-likelihood fit of cumulative M_lum distribution with truncated and untruncated power laws above completeness limit 8e3 Msun  
  > "We fit the cumulative mass distribution of $M_{\rm lum}$ in our full sample of GMCs using the `mspecfit.pro` IDL code" (5.1 GMC Mass Spectrum)
   - software: mspecfit.pro (IDL)
   - parameter: completeness limit 8e3 Msun  
  > "We adopt a completeness limit of $8\times10^3~\ensuremath{M_{\odot}}$ based on our observational sensitivity." (5.1 GMC Mass Spectrum)
   - fitting: Maximum likelihood (Rosolowsky 2005) accounting for mass uncertainties  
  > "implements a maximum likelihood algorithm to account for uncertainties in both cloud mass and the number distribution" (5.1 GMC Mass Spectrum)
   - validation: Truncated fit significantly better than untruncated  
  > "The truncated power law is a significantly better fit to this cloud population than the standard form" (5.1 GMC Mass Spectrum)
6. **Fit Larson relations**: Orthogonal distance regression in log space for size-linewidth, virial, mass-size and C_RdV-Sigma; Pearson correlation  
  > "We formally fit a linear function to the logarithms of these two quantities using orthogonal distance regression (ODR)" (5.2.1 Size-linewidth relation)
   - software: ODR
   - fitting: ODR with errors in both variables  
  > "which finds the maximum likelihood power law slope while accounting for errors in both variables simultaneously" (5.2.1 Size-linewidth relation)
   - validation: Monte Carlo of 10^4 random model clouds shows slope 0.27, r=0.37 for covariance test  
  > "We fit this model population as described above, and now find a slope of 0.27 with a correlation coefficient of 0.37." (5.3 The size-linewidth coefficient and virial equilibrium)
7. **Resolution test vs M51**: Smooth cubes to 40 pc and 2 km/s with IMSMOOTH, SPECSMOOTH, IMREBIN, rerun CPROPS  
  > "we used the `CASA` tasks `IMSMOOTH`, `SPECSMOOTH`, and `IMREBIN` to convolve our fully cleaned data cubes" (6.3 The effects of resolution)
   - software: CASA, CPROPS
   - fitting: _not stated_
   - validation: Flux preserved in convolution  
  > "Basic tests demonstrated that the flux in the original data was fully preserved in the convolution." (6.3 The effects of resolution)
8. **Estimate midplane ISM pressure**: P_ISM from Elmegreen 1989 with self-gravitating stellar disk substitution, using literature HI, stellar and scale-height data, compared with Milky Way solar neighborhood and M51  
  > "Following (cite: 1989ApJ...338..178E), we take the midplane gas pressure $P_{\rm ISM}$ to be" (6.4 Midplane disk pressure)
   - parameter: sigma_g=12.5 km/s; h_*=310 pc; Sigma_g~7 Msun/pc^2  
  > "This yields a stellar scale height of $h_* = 310$ pc, which we treat as constant with radius" (6.4 Midplane disk pressure)
   - assumption: Atomic gas dominates molecular; constant stellar scale height; self-gravitating stellar disk  
  > "we assume that the atomic gas dominates the molecular gas over large scales" (6.4 Midplane disk pressure)
   - fitting: _not stated_
   - validation: Milky Way value consistent with Boulares & Cox 1990  
  > "Our result is consistent with the modeled estimate of the kinetic pressure at the solar radius by (cite: 1990ApJ...365..544B)" (6.4 Midplane disk pressure)

## Software

- **CASA** 4.3.0 (calibration): Calibration, imaging (multiscale CLEAN), smoothing  
  > "Our data were processed and imaged entirely using the Common Astronomy Software Applications (CASA) package" (2.2 Data processing)
- **CPROPS** modified (elliptical beam): Cloud identification and property measurement  
  > "we use a modified version of the `CPROPS` algorithm (cite: Rosolowsky:2006cb)" (3 Cloud identification and characterization)
- **mspecfit.pro** : Maximum-likelihood mass spectrum fitting (IDL)  
  > "using the `mspecfit.pro` IDL code" (5.1 GMC Mass Spectrum)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of GMCs (full sample after cuts) | 253 | not stated | clouds | 3 | our sample consists of 253 clouds across these 46 regions after removing duplicates (32 GMCs) |
| Final sample size (R>=5 pc) | 121 | not stated | clouds | 4 | our final cloud catalog comprises 121 GMCs |
| Median ALMA/APEX recovered flux fraction | 0.63 | typical 0.2 | dimensionless | 2 | We find a median $\mathcal{F_{\rm rec}}$ of 0.63 with typical uncertainties of about 0.2 |
| Size-linewidth slope | 0.48 | 0.05 | dimensionless | 6 | / Size-linewidth / $0.48\pm0.05$ / 0.55 / $4\times10^{-11}$ / $0.5\ensuremath{^{a}}$ / |
| Virial relation slope (M_lum vs M_vir) | 1.00 | 0.05 | dimensionless | 6 | we find (again via ODR fitting) a slope of $1.00\pm0.05$ |
| Mass-size slope | 2.00 | 0.12 | dimensionless | 6 | we find a power law slope of $2.00\pm0.12$ |
| C_RdV-Sigma slope | 0.43 | 0.04 | dimensionless | 6 | we find a best-fit slope of $0.43\pm0.04$ |
| Median surface density (final sample) | 60.6 | not stated | Msun pc^-2 | 4 | / $\Sigma$ / $M_{\odot}$ pc$^{-2}$ / 13.8 / 397.0 / 60.6 / |
| Truncated mass spectrum slope gamma | -1.76 | 0.07 | dimensionless | 5 | we derive a slope of $\gamma = -1.76\pm0.07$ with a truncation mass $M_0 = 9.0\pm2.2\times10^5~\ensuremath{M_{\odot}}$ |
| Truncation mass M0 | 9.0e5 | 2.2e5 | Msun | 5 | $M_0 = 9.0\pm2.2\times10^5~\ensuremath{M_{\odot}}$ and $N_u = 8.3\pm3.0$ clouds |
| Untruncated slope | -1.90 | 0.05 | dimensionless | 5 | The best-fit straight power law has an exponent of $\gamma=-1.90\pm0.05$ |
| Median deconvolved aspect ratio | 2.4 | not stated | dimensionless | 4 | with a median value of 2.4 within the final sample |
| Median C_RdV NGC 300 | 0.46 | scatter 0.14 | km s^-1 pc^-1/2 | 4 | the median $C_{R \Delta V}$ in NGC 300 is 0.46 $\rm{km}~\rm{s}^{-1}$ pc$^{-1/2}$ with a scatter of 0.14 |
| ISM pressure NGC 300 | 8.4e3 at 0.9 kpc to 4.1e3 at 3.7 kpc | median error 1.3e3 | K cm^-3 | 8 | from a value of $P/k \approx 8.4 \times 10^3$ K cm$^{-3}$ at 0.9 kpc to $4.1 \times 10^3$ K cm$^{-3}$ at 3.7 kpc |
| ISM pressure Milky Way solar radius | 1.2e4 | range 8.5-19.8e3 | K cm^-3 | 8 | we find the ISM midplane pressure at the solar radius is $1.2\times10^4$ K cm$^{-3}$ |
| 3 sigma mass surface density sensitivity | 13.2 | not stated | Msun pc^-2 | 1 | this implies a 3$\sigma$ mass surface density sensitivity of $13.2~\ensuremath{M_{\odot}}$ pc$^{-2}$ |

## Qualitative findings

- No systematic trends of cloud properties with galactocentric radius or environmental zone  
  > "implying that GMC properties do not vary systematically across NGC 300" (4.2 The GMC distribution across NGC 300)
- Observed C_RdV-Sigma correlation can result from Larson relations plus measurement scatter  
  > "We demonstrate that this observed trend can be readily explained by the Larson relations holding in the presence of observational scatter" (7 Summary and Conclusions)

## Claim tuples

- H: Do NGC 300 GMCs obey the Milky Way Larson relations? | E: ODR fits of size-linewidth, virial and mass-size relations for 121 resolved clouds | R: Slopes 0.48±0.05, 1.00±0.05, 2.00±0.12; median Sigma 60.6 Msun/pc^2 | F: GMCs resemble Milky Way disk clouds, mostly virialized with near-constant surface density | **supported**
- H: Is the NGC 300 GMC mass spectrum like that of inner disks? | E: Maximum-likelihood fit of cumulative mass function above 8e3 Msun | R: gamma=-1.76±0.07 with truncation at ~9e5 Msun | F: Similar to inner Milky Way and spiral disks, shallower than outer disks | **supported**
- H: Are differences between NGC 300 and M51 GMCs due to resolution? | E: Smoothed NGC 300 cubes to 40 pc, 2 km/s and reanalyzed | R: C_RdV preserved at 0.43; median Sigma lower (45 Msun/pc^2) | F: Differences are not resolution artifacts; likely environmental | **supported**
- H: Does midplane pressure explain GMC property differences? | E: Computed P_ISM for NGC 300, Milky Way, compared to literature M51 | R: NGC 300 and MW ~1e4 K cm^-3; M51 >=10x higher | F: Pressure plausibly a key environmental variable | **partially**

## Reasoning

- Why this data: Nearby southern galaxy allows <10 pc resolution for direct comparison with Milky Way clouds  
  > "By targeting a nearby, southern galaxy, we are able to achieve $< 10$ pc and $1~\ensuremath{\rm{km}~\rm{s}^{-1}}$ resolution" (Introduction)
- Why this method: Natural weighting and multiscale CLEAN chosen to maximize sensitivity to extended GMC structure  
  > "we aimed to maximize sensitivity in order to most reliably identify and detect the full extent of GMCs, thus we used natural weighting" (2.3 Imaging and deconvolution)
- Alternative: Channel-by-channel CLEAN boxes tested and found equivalent, so single box used  
  > "thus utilized the far less time-intensive method of a single `CLEAN` box for each data cube" (2.3 Imaging and deconvolution)
- Alternative: SIGDISCONT of 0,1,2,999 rejected in favor of 5 as over-decomposing or not decomposing  
  > "we select the most conservative value for `SIGDISCONT` of 5 which still separates clearly different clouds that happen to overlap in space or velocity" (8 CPROPS parameter experiments)
- How they decided it was enough: _not stated_
- Limitation (authors): Missed flux relative to APEX (median 63% recovered), possibly low surface brightness emission  
  > "This means there may be low surface brightness CO emission we are unable to detect in the ALMA data." (2.5 Comparison to APEX single dish observations)
- Limitation (authors): Sampled range of environments limited to inner rising rotation curve  
  > "so the range of environments sampled in this study is somewhat limited" (4.2 The GMC distribution across NGC 300)
- Caveat (inferred, ours): Results depend on alpha_CO prescription and 1.2 size factor, which affect masses and surface densities
- Caveat (inferred, ours): Decomposition choices (SIGDISCONT) influence mass spectrum and mass-size slopes
- Caveat (inferred, ours): Pressure comparison relies on many literature inputs and assumed scale heights
- Caveat (inferred, ours): Hand-drawn CLEAN masks introduce subjectivity
- Caveat (inferred, ours): Only ~half of clouds resolved; deconvolved sizes near beam are unreliable

## Reproducibility

- Data public (paper): ALMA project 2013.1.00586.S cited; archive data used (public implied by acknowledgement)  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00586.S (PI. C. Lada)." (Acknowledgements)
- Products in archive: _not stated_
- Code: _not stated_
- Missing: Hand-drawn CLEAN masks per region
- Missing: Modified CPROPS version with elliptical beam (private communication)
- Missing: Per-region alpha_CO values from F14
- Missing: CASA version used for imaging
- Data volume (inferred): ~50-200 GB raw for 3 execution blocks, 48 fields
- Score (inferred): 3/5, Public data and detailed recipe, but manual masking, modified private CPROPS and inherited alpha_CO/F14 inputs hinder exact reproduction.
- Rediscovery candidate: no, Manual iterative cleaning and a modified, unreleased CPROPS version make an exact redo difficult, though results are numeric.

## Links

- Method: Rosolowsky & Leroy 2006 (cite: Rosolowsky:2006cb) (CPROPS algorithm)
- Method: Rosolowsky 2005 (cite: Rosolowsky:2005gt) (mass spectrum fitting method)
- Method: Cornwell 2008 (cite: 2008ISTSP...2..793C) (multiscale CLEAN)
- Companion: Faesi et al. 2016 (cite: Faesi:2016bl) (SMA pilot study of NGC 300 with same procedures)
- Companion: Faesi et al. 2014 (cite: Faesi:2014ib) (APEX survey and alpha_CO/metallicity inputs)
- Companion: Colombo et al. 2014 (cite: 2014ApJ...784....3C) (M51 PAWS GMC catalog for comparison)
- Related: PAWS (M51)
- Related: APEX NGC 300 survey (F14)

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
 "numeric_results": 16,
 "numeric_problems": 0,
 "fill": {
  "facts": 95,
  "stated": 77,
  "rate": 0.811
 },
 "evidence_ok": true
}
```
