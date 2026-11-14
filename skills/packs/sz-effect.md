# Evidence pack: Sunyaev-Zeldovich effect measurements (`sz-effect`)

Scope: SZ decrements with ALMA/ACA, pressure profiles, filtering

Built from 14 non-held-out ALMA papers whose methods cards passed mechanical evidence verification (every quote below is verbatim from the paper). Years 2016-2024.
Matcher (regex over analysis steps): `(?<!shakura.)(?<!shakura & )(?<!shakura and )sunyaev|zel'?dovich|\bsz\b(?![\s-]*\d)|compton[- ]?y|thermal pressure of the (?:icm|intracluster)`
Tagging is by regex, so a few papers may be off-topic: ignore those.

## Aggregates over all papers

### Science fields
- galaxy_clusters_and_sz: 13
- agn_and_quasars: 4
- high_z_galaxies: 3
- cosmology: 1

### Software named in the matched steps
- dynesty: 4
- casa: 3
- colossus: 1
- tclean: 1
- simobserve: 1
- galario: 1
- ciao: 1
- emcee: 1
- casa simalma: 1

### Fitting methods (most common phrasings)
- Bayesian; uniform centroid prior across ACA field; wide uninformative mass/slope and point-source priors; split-normal …: 1
- Bayesian model evidence; same SZ priors as the free run, with declination ordering: 1
- Marginalized posterior for M500 and βz; integrated-flux prior reduces spectral degeneracy: 1
- MCMC: 1
- Static nested sampling with dynesty; significance from Bayes factor against null model: 1
- Normal priors on centroid (sigma 14.3, 15 arcsec); split-normal priors on z; normal prior on flux scaling; wide uninfor…: 1
- Dynamic nested sampling with dynesty; posterior medians and 16/84 percentiles: 1
- Nested sampling with dynesty; priors and likelihood details not stated: 1
- Bayesian inference for mass, concentration, intrinsic shape and equilibrium status: 1
- Multi-probes three-dimensional Bayesian analysis: 1
- emcee MCMC with full covariance likelihood: 1

### Validation checks used
- Test alternate gNFW/point-source priors and observation subsets; both SZ components remain identified.: 1
- Compare Bayesian evidence and inspect raw, model, and residual ACA images; images are display-only.: 1
- Inspect velocity posterior tails and uncertainties; compare masses with the thermal-only fixed-slope estimates.: 1
- Compare predicted and observed core-excised X-ray luminosity and compare ALMA+ACA integrated SZ flux with AdvACT.: 1
- Mock ALMA observations with M=1, 2, 4 shocks: 1
- Residual maps in uv plane; Bayes factor comparisons: 1
- Compared with X-ray, CARMA, ACT catalog masses: 1
- Assessed flux boosting upper limit (~40% assuming 1.5\sigma noise contribution per source) and tested single central je…: 1
- Checked >50 uv tracks and >20 antenna pairs in shortest bin: 1
- data-free runs show no prior-induced biases: 1
- Compared with dirty-image significance for most significant cluster: 1
- Prior-only run; robustness tests varying gNFW slopes and centroid; residual dirty images: 1
- Model parameters statistically consistent with Di Mascolo et al. 2023; BMA profile used as reference with model varianc…: 1
- Compared with the X-ray spectral kT=2.0 keV of Tozzi et al. 2022b; SZ-derived value lower by a factor of ~3, discussed …: 1
- Proposed comparison with ΛCDM predictions after correcting geometrical biases: 1
- Good overall agreement within uncertainties: 1
- Order-of-magnitude only: 1
- Agreement with XMM pressure profile: 1
- FFT approximation vs simalma differs at most ~4%: 1
- y map morphology consistent with X-rays; inner profile agrees with local cool core expectation: 1

### Key parameters and settings (bibcode: value)
- 2021A&A...650A.153D: Free SZ centroid, mass parameter, and inner slope
- 2021A&A...650A.153D: Unresolved sources: point models with power-law spectra
- 2021A&A...650A.153D: Declination ordering for separate modes
- 2021A&A...650A.153D: Also fit a model with all gNFW slopes fixed to the universal pressure profile
- 2021A&A...650A.153D: Fixed universal gNFW slopes; AdvACT cylindrically integrated SZ flux within r500
- 2021A&A...650A.153D: Cylindrical SZ integration aperture: 1.69′, equivalent to AdvACT r500
- 2016ApJ...829L..23B: Free: pressure amplitude, shock radius, Mach number; slopes consistent with X-ray; outer slope marginalized within 30%
- 2016ApJ...829L..23B: Post-shock T_X from 1' region = 16.8 keV
- 2024A&A...689A..41V: Mostly flat priors; Gaussian priors on calibration and redshift
- 2024A&A...689A..41V: Evidence convergence threshold Δln B = 0.01
- 2024A&A...689A..41V: A = 1177.0 km/s, alpha = 0.364
- 2020A&A...638A..70D: free: M500, z, centroid, point source positions and fluxes, flux normalization
- 2020A&A...638A..70D: sigma_eff >~ 3 indicates robust detection
- 2019A&A...628A.100D: Priors in Table 1: P_e,us and T_e,us split-normal from X-ray; shock nose and angle split-normal; M uniform 1-10; alpha uniform -10 to 0; kappa normal(1,0.05)
- 2024A&A...682A.186L: uv upper threshold 65 klambda
- 2024A&A...682A.186L: SZ centroid fixed to X-ray centroid so that only the mass term (M500) is free per pressure model
- 2020ApJ...891...90R: relativistic correction with kT_e = 7 keV; line of sight integration to ±5 R500
- 2019A&A...629A.104G: Compton-y background 1.6e-6
- 2020PASJ...72...33K: Geometrically spaced bins, innermost 0-4 arcsec, size increasing by a factor 1.1


### Assumptions (bibcode: value)
- 2021A&A...650A.153D: Isothermal ICM; thermal SZ relativistic correction from Itoh2004
- 2021A&A...650A.153D: Flat Λ Cold Dark Matter: ΩM=0.30, ΩΛ=0.70, H0=70.0 km s−1 Mpc−1
- 2021A&A...650A.153D: Do not model the extended radio source; extrapolate it with α=−1 to check contamination
- 2021A&A...650A.153D: M500 parametrization assumes a self-similar pressure profile under hydrostatic equilibrium
- 2021A&A...650A.153D: Evidence-to-significance conversion assumes a Gaussian posterior and neglects changes in prior volume
- 2021A&A...650A.153D: Isothermal ICM; Nozawa2006 relativistic corrections; neglect primary CMB anisotropies
- 2021A&A...650A.153D: Use universal-profile masses for the predicted X-ray luminosity
- 2016ApJ...829L..23B: p_down/p_up = (5M^2-1)/4
- 2016ApJ...829L..23B: Upstream X-ray density and temperature measurements independent
- 2024A&A...689A..41V: Unresolved sources are point-like with first-order polynomial spectral behaviour
- 2024A&A...689A..41V: Cosmology Planck2014_XIII, H0=67.7, Om=0.307; non-relativistic SZ (relativistic corrections neglected)
- 2024A&A...689A..41V: ACT and ALMA+ACA likelihoods independent
- 2024A&A...689A..41V: Local scaling relations of Arnaud2010 used for Y to M500
- 2024A&A...689A..41V: Constant temperature along line of sight
- 2021MNRAS.503.1174K: Jet spectral index \alpha = -1.04 \pm 0.03 (explored range -0.7 to -1.5, and -1.2); cavity energy E_cav = 4pV; Lorentz factor 10^3 - 10^5 and photon index 2 fo…
- 2024ApJ...969...56M: pure thermal SZE; kSZE neglected
- 2020A&A...638A..70D: non-relativistic tSZ, kSZ neglected, flat ΛCDM Ωm=0.30 H0=70
- 2019A&A...628A.100D: gamma=5/3; flat LCDM Om=0.30, H0=70; kSZ neglected
- 2024A&A...682A.186L: Eight literature gNFW pressure profiles considered (A10 UP/MD, M14 UP/NCC, L15 REF/8.0/8.5, G17 EXT)
- 2024A&A...682A.186L: Ideal gas law; relativistic SZ correction negligible (<~1.5%); X-ray spectral temperature not used
- 2020EPJWC.22800009E: Three-dimensional triaxial ellipses for gas and total mass
- 2019MNRAS.487.4037D: Overpressurized sphere radius ~90 kpc, offset ~130 kpc; adiabatic index 5/3
- 2020ApJ...891...90R: spherical symmetry
- 2019A&A...629A.104G: Spherical models; M200 extrapolated from M500 assuming GNFW mass distribution
- 2020PASJ...72...33K: M500 = 8.8e14 h^-1 Msun, r500 = 0.92 h^-1 Mpc at z = 0.597


### Limitations the authors admit
- 2021A&A...650A.153D: Chandra source counts do not constrain the ICM temperature distribution.
- 2021A&A...650A.153D: Most X-ray hardness structures have low significance.
- 2021A&A...650A.153D: Radio resolution, sparse sampling, and weak high-frequency detections prevent a detailed spectral-index map.
- 2021A&A...650A.153D: SZ masses may be biased by nonhydrostatic gas and mass–inner-slope degeneracy.
- 2021A&A...650A.153D: Limited spectral coverage leaves thermal and kinetic SZ strongly degenerate.
- 2021A&A...650A.153D: Interferometric filtering favors compact, low-mass pressure models and limits extrapolation to large scales.
- 2021A&A...650A.153D: Weak-lensing positional precision limits confidence in the southern gas–mass offset.
- 2021A&A...650A.153D: Dust mass and temperature require better high-frequency observations.
- 2016ApJ...829L..23B: Short-spacing problem makes Mach number anti-correlated with pressure normalization
- 2016ApJ...829L..23B: Pre-shock temperature unconstrained in Chandra data
- 2024A&A...689A..41V: Lack of short baselines makes beta–P0 degeneracy and template discrimination weak; gNFW poorly suited for filaments
- 2021MNRAS.503.1174K: Small sample size of 10 cluster galaxies prevents detection of subtle deviations in the q_TIR vs M_* relation
- 2021MNRAS.503.1174K: Radio luminosity and cavity power estimates depend strongly on the unknown radio spectral index, which cannot be tightly constrained without deeper low-frequency observations
- 2021MNRAS.503.1174K: Low S/N (4\sigma) of the diffuse X-ray ICM emission prevents direct detection of X-ray cavities, measurement of cluster binding energy, or precise localisation of the X-ray peak
- 2021MNRAS.503.1174K: Possible flux boosting of up to ~40% in the faint radio-jet flux measurements
- 2019MNRAS.490.5134B: Only dof=1 for short baselines; limited SNR prevents 2D fitting
- 2024ApJ...969...56M: Halo mass estimate from Lya gas dynamics is uncertain
- 2024ApJ...969...56M: tSZE cannot be separated from kSZE without deep observations at other frequencies
- 2024ApJ...969...56M: Stack insensitive to non-spherically symmetric kSZE
- 2024ApJ...969...56M: Best-fitting model chi-square similar to zero signal
- 2020A&A...638A..70D: Limited angular dynamic range, short integrations and unresolved-source contamination limit mass inference
- 2019A&A...628A.100D: Systematics from cluster geometry and complex post-shock gas distribution; model does not capture X-ray morphology
- 2024A&A...682A.186L: Diffuse emission within 2 arcsec of the AGN is not observationally constrained
- 2024A&A...682A.186L: SZ normalisation may be underestimated because of interferometric filtering of large scales
- 2024A&A...682A.186L: Low significance of SZ and X-ray signals limits detailed morphological comparison
- 2024A&A...682A.186L: ICM metallicity practically unconstrained
- 2020EPJWC.22800009E: ALMA and NIKA2 images are very preliminary.
- 2020EPJWC.22800009E: Missing high-resolution SZ data at radial scales from 30 to 100 arcsec.
- 2020EPJWC.22800009E: More sensitive observations and a larger cluster sample are needed.
- 2019MNRAS.487.4037D: Models differ in components so statistical comparison is misleading; overfitting may hide overpressure; X-ray arithmetic limited to linear perturbations
- 2020ApJ...891...90R: Outermost pressure bin likely biased low; unquantified additional systematic
- 2019A&A...629A.104G: Residual positive signal from undetected sources means significance is conservative; S/N too low to strongly constrain pressure models
- 2020PASJ...72...33K: Equation-of-state limit is weak
- 2020PASJ...72...33K: Absolute values of the X-ray pseudo pressure are arbitrary
- 2020PASJ...72...33K: Temperature at r > 250 kpc cannot be constrained by the ALMA data
- 2020PASJ...72...33K: X-ray-only deprojection includes statistical errors only

### Settings cards flag as needed but not stated
- alma/aca calibrated measurement-set release identifiers, calibration casa/pipeline versions, and an…: 1
- exact visibility likelihood, visibility-weight treatment, and implementation of the 5% flux-calibra…: 1
- forward-model map grid, line-of-sight integration limits, primary-beam model, and frequency integra…: 1
- numerical fixed gnfw parameters and the complete pressure-to-mass normalization inherited from arna…: 1
- sampling configuration, stopping criteria, convergence diagnostics, and reproducible model-evidence…: 1
- exact modified power-law equation and the dust-model parameter priors.: 1
- numerical herschel upper limits, aperture sizes, backgrounds, and likelihood treatment of nondetect…: 1
- functional form and uncertainty treatment of the advact integrated-flux prior.: 1
- x-ray spectral model, abundance and absorption choices, fitting statistic, extraction regions, and …: 1
- exact compact-source subtraction models and diffuse-emission apertures used in the radio analysis.: 1
- additional flagging details for the alma data: 1
- specifics of the mcmc-in-casa uv-fitting code, sampler and priors: 1
- casa and ciao versions (only caldb 4.7.1 given): 1
- clean parameters (cell, size, masking, threshold): 1
- gnfw parameter values and priors on amplitude, shock radius, mach number: 1
- binning of chandra profile and x-ray temperature fitting details: 1
- priors for the radio/b-field calculation and cooling assumptions: 1
- exact upstream-temperature scaling chain: 1
- exact alma/aca uv-selection, channel binning and weights used in the visibility fits: 1
- dynesty settings (live points, bounding, sampling): 1
- exact act dr6 map products, beams, transfer functions and cutout size: 1
- tapering and tclean parameters for display images: 1
- how evidence-weighted mass average across models is computed: 1
- y-to-m500 conversion implementation details: 1
- band 4 point-source model details and line-channel ranges removed: 1
- casa version used for jvla and gmrt data reduction: 1
- exact flagging commands and channel ranges for jvla spectral windows 13, 14, and 15: 1
- pre-reduced alma 870 um continuum image from coogan et al. (2018) and 92 ghz sz residual map from g…: 1
- cell size and image size for tclean: 1
- mask and clean threshold/iterations: 1
- mcmc sampler type, priors, number of walkers/steps for galario fits: 1
- exact visibility binning/weighting and which data columns were used: 1
- procedure for inferring the 3.35 sigma with dof=1 details and per-bin values: 1
- model for correction factor beyond fable comparison; noise realisation details of simulations: 1
- manual mask definitions (regions) for qso and serendipitous sources in each of the ten fields: 1
- which channels were flagged as line-contaminated per spw and the continuum reference frequency used: 1
- tclean deconvolver, niter, cleaning threshold value, weighting scheme details, and uv-taper values/…: 1
- self-calibration solution parameters beyond 'scan length' (refant, gaincal combine, number of itera…: 1
- exact mad weighting formula and how masked pixels and noise were handled in the stack: 1
- beam-to-compton-y conversion details (effective frequency, t_cmb, how jy/beam is converted to y, an…: 1

## Paper excerpts (14 of 14, chosen for detail and spread over fields/years)

### 2021A&A...650A.153D: Multiwavelength view of SPT-CL J2106-5844. The radio galaxies and the thermal and relativistic plasmas in a massive galaxy cluster merger at z ≃ 1.13 (2021; galaxy_clusters_and_sz, agn_and_quasars; archival_reuse)
- question: Reconstruct the intracluster pressure distribution and investigate the merger and diffuse radio emission in SPT-CL J2106-5844.
- step 5: Search for SZ pressure peaks and compact contamination
  - method: Jointly forward-model Band 3/4 ALMA+ACA visibilities; project a gNFW pressure model and sample its Fourier transform at measured uv coordinates; search for point sources. [SZ modeling: "the reconstruction method is devised to sample the Fourier transform of a map of the SZ effect from a model galaxy cluster to the $u\varv$-plane coordinates of the sampled visibilities."] [Free modeling run: "is obtained by numerical integration of a generalized Navarro-Frenk-White (cite: Nagai2007) pressure profile along the line-of-sight direction"]
  - parameter: Free SZ centroid, mass parameter, and inner slope [Free modeling run: "We perform a first modeling run assuming the universal parametrization by (cite: Arnaud2010) but allow the model centroid, mass parameter, and slope at small radii to vary."]
  - parameter: Unresolved sources: point models with power-law spectra [Free modeling run: "we use point source models to describe the contamination from unresolved compact sources with flux characterized by a simple power-law spectral dependence."]
  - assumption: Isothermal ICM; thermal SZ relativistic correction from Itoh2004 [SZ modeling: "We compute the average relativistic corrections to the thermal SZ spectrum by means of the approximation by (cite: Itoh2004)."] [SZ modeling: "Given the large uncertainties on the temperature distribution, we assume this to be described by an isothermal model"]
  - assumption: Flat Λ Cold Dark Matter: ΩM=0.30, ΩΛ=0.70, H0=70.0 km s−1 Mpc−1 [Introduction: "Throughout this work, we assume a spatially flat $\Lambda$ Cold Dark Matter cosmological model, with $\Omega_{\mathrm{M}}=0.30$, $\Omega_{\Lambda}=0.70$, and $H_0=70.0~\mathrm{km\,s^{-1}\,Mpc^{-1}}$."]
  - assumption: Do not model the extended radio source; extrapolate it with α=−1 to check contamination [Free modeling run: "We do not consider any model component to describe the extended radio source, which should not significantly contaminate the measured SZ signal."] [Free modeling run: "by assuming a power law spectrum with average spectral index $\alpha=-1$"]
  - fitting: Bayesian; uniform centroid prior across ACA field; wide uninformative mass/slope and point-source priors; split-normal temperature prior from the X-ray estimate. [Free modeling run: "The centroid coordinates are assumed to have a uniform prior extending over the field of view of ACA, while we consider wide uninformative priors for both the mass and slope parameters."] [Free modeling run: "Uninformative priors are assumed for the position, amplitude, and spectral index."]
  - validation: Test alternate gNFW/point-source priors and observation subsets; both SZ components remain identified. [Free modeling run: "checked that the two SZ components are identified independent of any prior assumptions on the gNFW parameters or point-like component, or of the specific subsets of observations employed in the modeling."]
- step 6: Fit two SZ components and compare model evidence
  - method: Fit two universal-profile SZ components plus a central point source with modified power-law spectrum; compare against zero- and one-SZ-component models. [Multicomponent model: "we repeat the analysis this time including two separate SZ components along with the point-like feature with a modified power-law spectrum describing the central radio source."] [Multicomponent model: "Again, we assume a universal profile (cite: Arnaud2010) with free mass parameter and inner slope for each of the SZ model components."]
  - parameter: Declination ordering for separate modes [Multicomponent model: "in order to enforce the identifiability of the separate modes, we introduce an ordering condition on their declinations as detailed in Appendix A2 of (cite: Handley2015)."]
  - parameter: Also fit a model with all gNFW slopes fixed to the universal pressure profile [Multicomponent model: "when fixing all the gNFW slopes to the values for the universal pressure profile in (cite: Arnaud2010)"]
  - assumption: M500 parametrization assumes a self-similar pressure profile under hydrostatic equilibrium [Multicomponent model: "the presence of $M_{500}$ in our parameter set follows from the specific parametrization adopted by (cite: Arnaud2010) to get a self-similar pressure profile under the assumption of hydrostatic equilibrium."]
  - assumption: Evidence-to-significance conversion assumes a Gaussian posterior and neglects changes in prior volume [Multicomponent model: "is performed under the assumption of a Gaussian posterior distribution and neglecting any change in the prior volume due to the difference in the parameter sets between the models with and without the thermal SZ components."]
  - fitting: Bayesian model evidence; same SZ priors as the free run, with declination ordering [Multicomponent model: "We consider the same uniform priors as in Sect. [3.2.1](#sec:res:sz:onesz) for each of the SZ components."] [Multicomponent model: "the inclusion of the two-component model for the thermal SZ effect from SPT-CL J2106-5844 is found to improve the Bayesian log-evidence by $\Delta\log\mathcal{Z}=120.72\pm0.16$"]
  - validation: Compare Bayesian evidence and inspect raw, model, and residual ACA images; images are display-only. [Multicomponent model: "Also, two components are found to be preferred over one SZ model at the $\sim9.9\sigma$ level."] [Multicomponent model: "the reconstructed images of the raw, best-fit model, and corresponding residual interferometric data"]
- step 8: Test for kinetic SZ contributions
  - method: Add kinetic SZ terms to both subclusters and fit mass and line-of-sight velocity with an integrated-SZ-flux prior. [Constraining the kinetic SZ signal: "a multicomponent model analogous to the one introduced in the previous section but including a kinetic SZ term for both the subclusters."] [Constraining the kinetic SZ signal: "Further, we introduced a prior on the integrated SZ flux in order to break (or, at least, reduce) the degeneracy between the thermal and kinetic spectral components of the SZ signal."]
  - parameter: Fixed universal gNFW slopes; AdvACT cylindrically integrated SZ flux within r500 [Constraining the kinetic SZ signal: "we restricted the analysis to the case with all the slopes of the gNFW pressure distributions fixed to the values for the universal pressure model (cite: Arnaud2010)."] [Constraining the kinetic SZ signal: "we considered the estimate of the cylindrically integrated SZ flux within $r_{500}$"]
  - assumption: Isothermal ICM; Nozawa2006 relativistic corrections; neglect primary CMB anisotropies [Constraining the kinetic SZ signal: "Under the same assumption adopted in the previous section of an isothermal model"] [Constraining the kinetic SZ signal: "and is computed according to the approximation provided by (cite: Nozawa2006)."]
  - fitting: Marginalized posterior for M500 and βz; integrated-flux prior reduces spectral degeneracy [Constraining the kinetic SZ signal: "the marginalized posterior for the main parameters — the mass $M_{500}$ and the line-of-sight component of the peculiar velocity in units of the speed of light $\beta_{\mathrm{z}}$"]
  - validation: Inspect velocity posterior tails and uncertainties; compare masses with the thermal-only fixed-slope estimates. [Constraining the kinetic SZ signal: "the determination of the best-fit value of the parameter is driven by the high $\beta_{\mathrm{z}}$ tail of the posterior distribution."] [Constraining the kinetic SZ signal: "systematically lower but consistent with the estimates reported in the previous section considering the same universal profile slopes."]
- step 10: Compare gas, mass, galaxies, and merger scenarios
  - method: Compare SZ peaks with weak lensing, X-ray brightness/hardness, BCG and galaxy redshifts; predict X-ray luminosity from SZ masses. [Discussion: "provides a comparative view of the SZ signature of SPT-CL J2106-5844 (both model and dirty image) with the weak lensing and X-ray surface brightness distribution in the cluster."] [Discussion: "one can predict the X-ray luminosities of the two substructures using the scaling relation from (cite: Mantz2016)."]
  - parameter: Cylindrical SZ integration aperture: 1.69′, equivalent to AdvACT r500 [The dynamics of the ICM substructures: "The reported SZ flux density is computed as the cylindrically integrated SZ signal within an aperture of $1.69\ensuremath{'}$, equivalent to the AdvACT estimate for SPT-CL J2106-5844’s $r_{500}$."]
  - assumption: Use universal-profile masses for the predicted X-ray luminosity [Discussion: "When considering the masses estimated under the assumption of a universal pressure model"]
  - validation: Compare predicted and observed core-excised X-ray luminosity and compare ALMA+ACA integrated SZ flux with AdvACT. [Discussion: "lower than the corresponding value of $20.5\substack{+1.0\\-1.0}\cdot10^{44}~\mathrm{erg~s^{-1}}$ measured from the core-excised X-ray observations"] [The dynamics of the ICM substructures: "lower than the measurement $4.7\substack{+1.1\\-1.3}\cdot 10^{-4}~\mathrm{arcmin^2}$ inferred from the AdvACT catalog (cite: Hilton2020)."]
- result: Two-SZ-component log-evidence improvement over no SZ = 120.72 ± ±0.16 dimensionless [Multicomponent model: "improve the Bayesian log-evidence by $\Delta\log\mathcal{Z}=120.72\pm0.16$ with respect to the model without any SZ components"]
- result: SZ detection significance relative to null model = 15.6 ± not stated σ [Multicomponent model: "roughly corresponding to a $15.6\sigma$ detection in comparison to the null model."]
- result: Preference for two SZ components over one = ∼9.9 ± not stated σ [Multicomponent model: "Also, two components are found to be preferred over one SZ model at the $\sim9.9\sigma$ level."]
- result: Northern SZ component M500, free inner slope = 2.60 × 10^14 ± +0.57/-0.54 × 10^14 M⊙ [Multicomponent model: "$2.60\substack{+0.57\\-0.54}\cdot 10^{14}~\mathrm{M_{\odot}}$"]
- result: Southern SZ component M500, free inner slope = 1.34 × 10^14 ± +0.52/-0.52 × 10^14 M⊙ [Multicomponent model: "$1.34 \substack{+0.52\\-0.52}\cdot 10^{14}~\mathrm{M_{\odot}}$"]
- result: Northern SZ component inner slope = 0.47 ± +0.11/-0.12 dimensionless [Multicomponent model: "$0.47\substack{+0.11\\-0.12}$"]
- result: Southern SZ component inner slope = 0.86 ± +0.25/-0.24 dimensionless [Multicomponent model: "$0.86\substack{+0.25\\-0.24}$"]
- result: Northern SZ component mass, fixed universal slopes = 3.10 × 10^14 ± +0.10/-0.10 × 10^14 M⊙ [Multicomponent model: "we obtain masses of $3.10\substack{+0.10\\-0.10} \cdot 10^{14}~\mathrm{M_{\odot}}$ and $3.26\substack{+0.25\\-0.25} \cdot 10^{14}~\mathrm{M_{\odot}}$ for the northern and southern SZ components, respectively."]
- result: Southern SZ component mass, fixed universal slopes = 3.26 × 10^14 ± +0.25/-0.25 × 10^14 M⊙ [Multicomponent model: "we obtain masses of $3.10\substack{+0.10\\-0.10} \cdot 10^{14}~\mathrm{M_{\odot}}$ and $3.26\substack{+0.25\\-0.25} \cdot 10^{14}~\mathrm{M_{\odot}}$ for the northern and southern SZ components, respectively."]
- result: Central source flux at 5 GHz, multicomponent fit = 0.690 ± +0.037/-0.037 mJy [Multicomponent model: "$0.690\substack{+0.037\\-0.037}~\mathrm{mJy}$"]
- result: Central source spectral index, modified power law = -1.10 ± +0.05/-0.05 dimensionless [Multicomponent model: "$-1.10\substack{+0.05\\-0.05}$"]
- result: Central source spectral curvature = 0.123 ± +0.022/-0.022 dimensionless [Multicomponent model: "$0.123\substack{+0.022\\-0.022}$"]
- result: Northern component βz = 1.7 × 10^-2 ± +2.0/-1.5 × 10^-2 dimensionless [Constraining the kinetic SZ signal: "We measure values for $\beta_{\mathrm{z}}$ of $1.7\substack{+2.0\\-1.5}\cdot10^{-2}$ and $0.2\substack{+2.0\\-0.8}\cdot10^{-2}$ for the northern and southern SZ features, respectively"]
- result: Southern component βz = 0.2 × 10^-2 ± +2.0/-0.8 × 10^-2 dimensionless [Constraining the kinetic SZ signal: "We measure values for $\beta_{\mathrm{z}}$ of $1.7\substack{+2.0\\-1.5}\cdot10^{-2}$ and $0.2\substack{+2.0\\-0.8}\cdot10^{-2}$ for the northern and southern SZ features, respectively"]
- result: Northern component line-of-sight velocity = 5088 ± +6092/-4435 km s−1 [Constraining the kinetic SZ signal: "equivalent to line-of-sight velocities of $5088\substack{+6092\\-4435}~\mathrm{km~s^{-1}}$ and $463\substack{+6027\\-2538}~\mathrm{km~s^{-1}}$."]
- result: Southern component line-of-sight velocity = 463 ± +6027/-2538 km s−1 [Constraining the kinetic SZ signal: "equivalent to line-of-sight velocities of $5088\substack{+6092\\-4435}~\mathrm{km~s^{-1}}$ and $463\substack{+6027\\-2538}~\mathrm{km~s^{-1}}$."]
- result: Northern component mass with kinetic SZ = 2.26 × 10^14 ± +0.83/-0.72 × 10^14 M⊙ [Constraining the kinetic SZ signal: "the inclusion of the kinetic SZ term causes a variation in the masses to $2.26\substack{+0.83\\-0.72}\cdot10^{14}~\mathrm{M_{\odot}}$"]
- result: Predicted total X-ray luminosity, universal-profile SZ masses = 11.4 × 10^44 ± +2.1/-1.8 × 10^44 erg s−1 [Discussion: "this leads to the total X-ray luminosity in the $0.1-2.4~\mathrm{keV}$ band of $11.4\substack{+2.1\\-1.8}\cdot10^{44}~\mathrm{erg~s^{-1}}$"]
- result: Measured core-excised X-ray luminosity, 0.1-2.4 keV comparison = 20.5 × 10^44 ± +1.0/-1.0 × 10^44 erg s−1 [Discussion: "the corresponding value of $20.5\substack{+1.0\\-1.0}\cdot10^{44}~\mathrm{erg~s^{-1}}$ measured from the core-excised X-ray observations"]
- result: Northern SZ centroid offset from BCG = around 24 ± not stated kpc [The dynamics of the ICM substructures: "We measure an offset of around $24~\mathrm{kpc}$ and $69~\mathrm{kpc}$ between the reconstructed SZ centroid and, respectively, the BCG and X-ray peak."]
- result: Northern SZ centroid offset from X-ray peak = 69 ± not stated kpc [The dynamics of the ICM substructures: "We measure an offset of around $24~\mathrm{kpc}$ and $69~\mathrm{kpc}$ between the reconstructed SZ centroid and, respectively, the BCG and X-ray peak."]
- result: Southern SZ peak offset from weak-lensing component = >50 ± not stated kpc [Discussion: "We observe a moderate offset ($>50~\mathrm{kpc}$) between the southern SZ peak and the corresponding weak-lensing component"]
- result: Cylindrically integrated model SZ signal within 1.69′, free inner slopes = 2.17 × 10^-4 ± +0.26/-0.18 × 10^-4 arcmin² [The dynamics of the ICM substructures: "for our SZ model of $2.17\substack{+0.26\\-0.18}\cdot10^{-4}~\mathrm{arcmin^2}$"]
- result: Cylindrically integrated model SZ signal within 1.69′, universal pressure model = 3.01 × 10^-4 ± +0.74/-0.77 × 10^-4 arcmin² [The dynamics of the ICM substructures: "($3.01\substack{+0.74\\-0.77}\cdot10^{-4}~\mathrm{arcmin^2}$ in the case of universal pressure model)"]
- limitation (authors): Chandra source counts do not constrain the ICM temperature distribution. [Chandra: "The low number of source counts in the available *Chandra* data did not allow for deriving significant constraints on the temperature distribution of the ICM within SPT-CL J2106-5844."]
- limitation (authors): Most X-ray hardness structures have low significance. [Chandra: "aside from the bright core region, it is not possible to identify any structure with a significance higher than $2\sigma$."]
- limitation (authors): Radio resolution, sparse sampling, and weak high-frequency detections prevent a detailed spectral-index map. [Diffuse emission: "the different angular resolutions of the available radio data, combined with the severe sparsity and low significance of the observations at high frequencies, do not allow for building a detailed map of the spectral index distribution"]
- not stated (card): ALMA/ACA calibrated measurement-set release identifiers, calibration CASA/pipeline versions, and any additional flagging or averaging.; Exact visibility likelihood, visibility-weight treatment, and implementation of the 5% flux-calibration uncertainty.; Forward-model map grid, line-of-sight integration limits, primary-beam model, and frequency integration across spectral windows.; Numerical fixed…

### 2016ApJ...829L..23B: ALMA-SZ Detection of a Galaxy Cluster Merger Shock at Half the Age of the Universe (2016; galaxy_clusters_and_sz; observational_alma_primary)
- question: Can ALMA SZ measurements detect the pressure discontinuity of a merger shock at the NW radio relic of El Gordo, and what Mach number and relic magnetic field result when combined with Chandra and ATCA data?
- step 3: Fit SZ shock model to ALMA uv-data
  - method: GNFW pressure plus R-H pressure boost at shock radius, fit directly to visibilities by MCMC within CASA [2.3 ALMA-SZ data: "This is done using an MCMC method within CASA and is computationally expensive, due to the large data volume."]
  - software: CASA
  - parameter: Free: pressure amplitude, shock radius, Mach number; slopes consistent with X-ray; outer slope marginalized within 30% [2.3 ALMA-SZ data: "leaving the pressure amplitude, shock radius and the Mach number as free parameters"]
  - assumption: p_down/p_up = (5M^2-1)/4 [2.3 ALMA-SZ data: "$p_{\mathrm{down}}/p_{\mathrm{up (GNFW)}} = (5{\cal M}^2 -1)/4$"]
  - fitting: MCMC [2.3 ALMA-SZ data: "This is done using an MCMC method within CASA"]
  - validation: Mock ALMA observations with M=1, 2, 4 shocks [2.3 ALMA-SZ data: "We make extensive simulations for mock ALMA observations"]
- step 4: Joint SZ/X-ray Mach number
  - method: Derive pre-shock pressure prior from X-ray density and temperature (upstream T scaled from downstream T via R-H) and apply to SZ fit [3.3 Joint SZ/X-Ray modeling: "we scale from the downstream $T_\mathrm{X}$ value using the Mach number in a chain, from the R-H condition for temperature jump."]
  - parameter: Post-shock T_X from 1' region = 16.8 keV [3.3 Joint SZ/X-Ray modeling: "The post-shock temperature is measured from a wider $1{^{\prime}}$ region ($T_\mathrm{X} = 16.8^{+2.4}_{-1.8}$ keV)"]
  - assumption: Upstream X-ray density and temperature measurements independent [3.3 Joint SZ/X-Ray modeling: "we use a pressure prior assuming the upstream X-ray density and temperature measurements are independent"]
- result: SZ shock radius = 870 ± +14/-13 kpc [3.1 SZ shock modeling: "$r_{\mathrm{sh}}=870^{+14}_{-13}$ kpc"]
- result: Mach number from SZ alone = 1.4 ± +1.2/-0.2 dimensionless [3.1 SZ shock modeling: "${\cal M}= 1.4^{+1.2}_{-0.2}$, supporting ${\cal M}> 1$ at more than $98\%$ confidence"]
- result: Mach number SZ with weak-lensing mass prior = 1.5 ± +0.5/-0.2 dimensionless [3.1 SZ shock modeling: "reduces the errors to ${\cal M}= 1.5^{+0.5}_{-0.2}$"]
- result: Joint SZ/X-ray Mach number = 2.4 ± +1.3/-0.6 dimensionless [3.3 Joint SZ/X-Ray modeling: "${\cal M}= 2.4^{+1.3}_{-0.6}$"]
- result: Post-shock temperature = 16.8 ± +2.4/-1.8 keV [3.3 Joint SZ/X-Ray modeling: "$T_\mathrm{X} = 16.8^{+2.4}_{-1.8}$ keV"]
- limitation (authors): Short-spacing problem makes Mach number anti-correlated with pressure normalization [2.3 ALMA-SZ data: "its amplitude is anti-correlated with the pressure normalization. This is an inherent limitation of the current ALMA observation"]
- limitation (authors): Pre-shock temperature unconstrained in Chandra data [3 Results and Discussion: "the pre-shock temperature in this high-$z$ object remains unconstrained due to the high background-to-cluster photon ratio"]
- not stated (card): Additional flagging details for the ALMA data; Specifics of the MCMC-in-CASA uv-fitting code, sampler and priors; CASA and CIAO versions (only CALDB 4.7.1 given); CLEAN parameters (cell, size, masking, threshold); GNFW parameter values and priors on amplitude, shock radius, Mach number; Binning of Chandra profile and X-ray temperature fitting details; Priors for the radio/B-field calculation and …

### 2024A&A...689A..41V: XLSSC 122 caught in the act of growing up: Spatially resolved SZ observations of a z = 1.98 galaxy cluster (2024; galaxy_clusters_and_sz; observational_alma_primary)
- question: What are the dynamical state and morphology of the ICM of the z=1.98 cluster XLSSC 122, as traced by resolved SZ observations?
- step 1: Model compact-source contamination
  - method: Fit point-source models (RA, Dec, amplitude, spectral slope, calibration scales) jointly to Band 3 and Band 4 in the uv-plane with lower uv-cut of 11 kλ; subtract bright source before SZ modeling [4 Interloper and cluster member removal: "with a lower *uv*-cut of 11 k$\lambda$ to exclude extended emission."]
  - software: dynesty
  - assumption: Unresolved sources are point-like with first-order polynomial spectral behaviour [4 Interloper and cluster member removal: "Unresolved, compact sources are modeled using point-like (Dirac delta) emission models with a first-order polynomial to describe their spectral behavior."]
- step 2: Single-component ICM forward modeling
  - method: gNFW (theoretical) and A10/M14 template (empirical) pressure models integrated to Compton y, converted to SZ brightness per band, Fourier transformed, sampled at data uv-points with primary beam; Gaussian likelihood on unbinned visibilitie… [3 Methodology: "We then apply the ALMA and ACA transfer function to the model to account for the missing baselines and compute the likelihood of the resulting model on the unbinned visibilities"]
  - software: dynesty
  - parameter: Mostly flat priors; Gaussian priors on calibration and redshift [3.3 Joint likelihood modeling: "we mainly use flat priors except for the calibration and redshift uncertainty parameters which we marginalize over."]
  - parameter: Evidence convergence threshold Δln B = 0.01 [3.3 Joint likelihood modeling: "set to $\Delta\ln\mathcal{B}=0.01$"]
  - assumption: Cosmology Planck2014_XIII, H0=67.7, Om=0.307; non-relativistic SZ (relativistic corrections neglected) [1 Introduction: "$H_0=67.7$ kms$^{-1}$Mpc$^{-1}$ and $\Omega_{\rm m} = 0.307$"]
  - assumption: ACT and ALMA+ACA likelihoods independent [3.3 Joint likelihood modeling: "Hence, we assume no covariance between the ACA+ALMA observations and the ACT maps."]
  - fitting: Static nested sampling with dynesty; significance from Bayes factor against null model [3.2 Visibility-based modeling of the ICM: "The implementation uses the static nested sampling method implemented in the `dynesty` package"]
  - validation: Residual maps in uv plane; Bayes factor comparisons [5.1.1 The theoretical formalism: "The residuals in Figure [1] are obtained by subtracting the model in the visibility plane from the data."]
- step 5: Derive SZ and dynamical masses
  - method: Evidence-weighted average of empirical-formalism masses (ALMA+ACA+ACT); velocity dispersion biweight of 32 members with Munari scaling, converted to M500 with colossus [7 Mass estimates: "Our SZ mass is calculated by taking the evidence-weighted average of the mass estimates from the empirical formalism runs"]
  - software: colossus
  - parameter: A = 1177.0 km/s, alpha = 0.364 [7 Mass estimates: "with $A = 1177.0$ km s$^{-1}$ and $\alpha = 0.364$"]
  - assumption: Local scaling relations of Arnaud2010 used for Y to M500 [7 Mass estimates: "we make use of local scaling relations from (cite: Arnaud2010) to convert $Y_{\rm 500,c}$ to an SZ-derived halo mass"]
  - validation: Compared with X-ray, CARMA, ACT catalog masses [Mass estimates: "We also quote the derived cluster mass of XLSSC 122 as reported in the ACT cluster catalog (cite: Hilton2021)."]
- step 6: Pseudo-temperature map
  - method: Ratio of SZ flux over sqrt of X-ray surface brightness at ~5'' resolution [8.2 Thermodynamical implications: "taking the ratio of the SZ flux over the square root of the X-ray surface brightness"]
  - assumption: Constant temperature along line of sight [8.2 Thermodynamical implications: "under the assumption of constant temperature along the line of sight"]
- result: SZ detection significance, ALMA+ACA = ~10.9–11.2 ± not stated sigma [5.1 ALMA+ACA modeling: "we detect the SZ effect at $\sim10.9-11.2\sigma$ in the ACA+ALMA data"]
- result: SZ detection significance, ALMA+ACA+ACT = 15 ± not stated sigma [9 Conclusions: "which increases to $15\sigma$ when ACT observations are included"]
- result: M500,c (SZ) = 1.66e14 ± +0.23/-0.20 e14 Msun [7 Mass estimates: "$M_{500,\mathrm{c}} = 1.66^{+0.23}_{-0.20} \times 10^{14}~\rm M_\odot$"]
- result: Eccentricity (ALMA+ACA+ACT) = 0.46 ± +0.12/-0.16 dimensionless [5.2 ALMA+ACA+ACT joint likelihood model…: "likelihood-weighted average of $e=0.46^{+0.12}_{-0.16}$"]
- result: Velocity dispersion sigma200,c = 1014 ± 169 km/s [7 Mass estimates: "We found a $\sigma_{200,\mathrm{c}} = 1014~\pm169$ km s$^{-1}$"]
- result: log10 M500,c dynamical = 14.69 ± +0.13/-0.18 log Msun [7 Mass estimates: "$\log_{10} M_{500,\mathrm{c}}^{\mathrm{dyn}} = 14.69^{+0.13}_{-0.18}~\rm M_\odot$"]
- result: Y(<r500,c) A10-MD = 2.0e-5 ± +0.6/-0.4 e-5 Mpc^2 [8.3 Time scales: "we find $Y(<r_{500,\mathrm{c}}) = 2.0^{+0.6}_{-0.4} \times 10^{-5}~\textnormal{Mpc}^2$"]
- result: SZ peak offset from BCG/X-ray peak = 10'' (80 kpc) ± 1'' (7 kpc) arcsec [8.1 Morphological implications: "offset from the BCG and the peak of the X-ray emission by $10\ensuremath{''}\pm 1\ensuremath{''}$ ($80\pm7$ kpc)"]
- limitation (authors): Lack of short baselines makes beta–P0 degeneracy and template discrimination weak; gNFW poorly suited for filaments [5.1.2 The empirical formalism: "the lack of short baselines in the ALMA+ACA observations explains why the mass estimates vary between models"]
- not stated (card): Exact ALMA/ACA uv-selection, channel binning and weights used in the visibility fits; dynesty settings (live points, bounding, sampling); Exact ACT DR6 map products, beams, transfer functions and cutout size; Tapering and tclean parameters for display images; How evidence-weighted mass average across models is computed; Y-to-M500 conversion implementation details; Band 4 point-source model detail…

### 2021MNRAS.503.1174K: Feedback factory: multiple faint radio jets detected in a cluster at z = 2 (2021; high_z_galaxies, agn_and_quasars, galaxy_clusters_and_sz; multi_facility_alma_minor)
- question: What is the role of AGN radio-jet based kinetic feedback and the compliance of cluster galaxies to the TIR-radio correlation within the z=2 galaxy cluster CL J1449+0856?
- step 5: Calculate integrated radio-jet luminosity, mechanical cavity power, SZ residual correlation, and Inverse-Compton X-ray contribution
  - method: Integrate rest-frame 10 MHz - 10 GHz radio luminosity from the 6 jets, convert to cavity power P_cav via the O'Sullivan et al. (2011) scaling relation, compare jet locations with the ALMA+ACA 92 GHz SZ residual map, and estimate IC X-ray f… [Radio emission: How much do we really h…: "To make a comparison, we add up the contributions of all the detected jets in place of the jets from a central AGN, which gives us a flux of 30.6\pm3.3 \, \mu Jy and a corresponding integrated radio luminosity (10 MHz–10 GHz rest-frame) of 2.1 ~(\pm 0.2)~ \times 10^{41} ~ergs~ s^{-1}."] [Quantifying the feedback: "We can hence use the integrated radio luminosity from all these jets"]
  - assumption: Jet spectral index \alpha = -1.04 \pm 0.03 (explored range -0.7 to -1.5, and -1.2); cavity energy E_cav = 4pV; Lorentz factor 10^3 - 10^5 and photon index 2 for IC calculation [Radio emission: How much do we really h…: "With a robust sample of 190 extragalactic radio-jets, they find a mean spectral index of -1.04 \pm 0.03 that we use in our calculation."] [Quantifying the feedback: "This comes out to be 4pV under the assumption that the cavity is dominated by relativistic plasma."]
  - validation: Assessed flux boosting upper limit (~40% assuming 1.5\sigma noise contribution per source) and tested single central jet R1 alone [Radio emission: How much do we really h…: "We can also have flux boosting contributions and we estimate a generous upper limit of the resulting overestimation of the jet flux to be \sim40\%, by assuming an additional noise contribution of 1.5\sigma for each source."] [Radio emission: How much do we really h…: "But repeating the same analysis with the central jet (R1) only brings down the luminosity by a factor of 4, keeping it well within the scatter and still slightly above the average."]
- result: Integrated radio luminosity (10 MHz - 10 GHz rest-frame) of the 6 jets (for \alpha = -1.04) = 2.1e41 ± 0.2e41 ergs s^{-1} [Radio emission: How much do we really h…: "To make a comparison, we add up the contributions of all the detected jets in place of the jets from a central AGN, which gives us a flux of 30.6\pm3.3 \, \mu Jy and a corresponding integrated radio luminosity (10 MHz–10 GHz rest-frame) of 2.1 ~(\pm 0.2)~ \times 10^{41} ~ergs~ s^{-1}."]
- result: AGN-jet cavity power P_cav (for \alpha = -1.04) = 1.14e44 ± 0.55e44 ergs s^{-1} [Quantifying the feedback: "to get a $\rm P_{\rm cav}=1.14 ~(\pm 0.55)~ \times 10^{44} ~\rm ergs~ s^{-1}$"]
- result: AGN-jet cavity power P_cav upper limit (for \alpha = -1.5) = 4.7e44 ± not stated ergs s^{-1} [Quantifying the feedback: "The details of this distribution, although indeterminable with the current data, have large implications especially since the –1.5 limit results in a P_{cav} \sim 4.7 ~ \times 10^{44} ~ergs~ s^{-1}."]
- result: AGN-jet cavity power P_cav (for \alpha = -1.2) = 1.8e44 ± not stated ergs s^{-1} [Quantifying the feedback: "This gives a P_{cav} \sim 1.8 ~ \times 10^{44} ~ergs~ s^{-1}."]
- result: Inverse-Compton X-ray luminosity upper limit from Chandra stacking = 2.2e42 ± not stated ergs s^{-1} [Inverse-Compton contribution: "The generous upper limit hence derived from the total counts detected is 2.2~ \times 10^{42}~ ergs~s^{-1} or 3\% of the ICM X-ray luminosity."]
- limitation (authors): Small sample size of 10 cluster galaxies prevents detection of subtle deviations in the q_TIR vs M_* relation [TIR-radio correlation: "As shown in Fig. 4, we see an agreement within 1\sigma (0.2 dex), although acknowledging the inability of our limited dataset to detect a more subtle digression in the behaviour of q_{TIR}, if it exists."]
- limitation (authors): Radio luminosity and cavity power estimates depend strongly on the unknown radio spectral index, which cannot be tightly constrained without deeper low-frequency observations [Radio emission: How much do we really h…: "It is worth noting however that this luminosity calculation is strongly dependent on the radio spectral index which can be anywhere between –0.7 (cite: delhaize17) to –1.5 (the upper limit we calculate based on our GMRT 325 MHz measurements)."]
- limitation (authors): Low S/N (4\sigma) of the diffuse X-ray ICM emission prevents direct detection of X-ray cavities, measurement of cluster binding energy, or precise localisation of the X-ray peak [Radio emission: How much do we really h…: "However, we can only estimate a rough peak of the X-ray emission with the limited S/N, which still seems to be within this region."]
- not stated (card): CASA version used for JVLA and GMRT data reduction; Exact flagging commands and channel ranges for JVLA spectral windows 13, 14, and 15; Pre-reduced ALMA 870 um continuum image from Coogan et al. (2018) and 92 GHz SZ residual map from Gobat et al. (2019), as ALMA reduction parameters are not restated in this paper

### 2019MNRAS.490.5134B: Detecting the halo heating from AGN feedback with ALMA (2019; agn_and_quasars, high_z_galaxies; archival_reuse)
- question: Can the SZ decrement from AGN-heated halo gas around quasar HE0515-4414 be detected in the ALMA visibility plane after subtracting compact positive sources?
- step 4: inspect residuals for SZ
  - method: Subtract model from visibilities; bin residuals in 1 klambda bins; tclean residual images [3 Results: "The residuals were found by subtracting the model presented in Fig. 4 from the observed visibilities."]
  - software: CASA, tclean
  - validation: Checked >50 uv tracks and >20 antenna pairs in shortest bin [3.2 Visibility Plane: "We plotted the uv coordinates of the visibilities inside that bin and observed over 50 uv-tracks."]
- step 6: compare with FABLE simulation
  - method: simobserve of FABLE SZ map, same pipeline; derive correction factor 2.5 [4.2 Comparison with Simulations: "This suggests a total SZ flux of 0.5 mJy from HE0515-4414 after correcting for the primary beam attenuation and the flux resolved out by the array (i.e. a correction factor of 2.5)."]
  - software: CASA, simobserve
- result: SZ flux (uncorrected) = ~0.2 ± not stated mJy [Conclusion: "We report a SZ flux of $\sim$ 0.2 mJy"]
- result: Corrected SZ flux = ~0.5 ± not stated mJy [Conclusion: "$\sim$ 0.5 mJy after applying a correction factor"]
- result: SW bowl significance = 3.2 ± not stated sigma [3.1 Image Plane: "In our analysis this feature has a slightly lower significance, 3.2$\sigma$."]
- limitation (authors): Only dof=1 for short baselines; limited SNR prevents 2D fitting [3.3 Significance: "Our positive emission model, however, has 17 parameters, leaving dof=1."]
- not stated (card): Cell size and image size for tclean; Mask and clean threshold/iterations; MCMC sampler type, priors, number of walkers/steps for GALARIO fits; Exact visibility binning/weighting and which data columns were used; Procedure for inferring the 3.35 sigma with dof=1 details and per-bin values; Model for correction factor beyond FABLE comparison; noise realisation details of simulations

### 2024ApJ...969...56M: Observational Constraints on Sunyaev─Zeldovich Effect Halos around High-z Quasars (2024; agn_and_quasars, galaxy_clusters_and_sz; observational_alma_primary)
- question: Is there hot, ionized circumgalactic gas (thermal SZE) around high-z ultraluminous quasars, and what halo mass and AGN feedback wind power does a stacked ALMA continuum limit imply?
- step 5: Convert stacked flux to Compton y
  - method: Interpret stacked continuum decrement as thermal SZE and convert to Compton parameter using the Sazonov & Sunyaev formulation [2.2 Stacked SZE Signal: "We interpret the stacked continuum flux observations as SZE signal by converting to Compton parameter"]
  - assumption: pure thermal SZE; kSZE neglected [2.2 Stacked SZE Signal: "For stacked QSO environments we use a pure thermal SZE model to determine the Compton parameters."] [2.2 Stacked SZE Signal: "Our stacking analysis will not be sensitive to the non-spherically symmetric kSZE."]
- result: Peak y in 6 arcsec stacked image (east side, r ~5 arcsec) = 2.4e-5 (~2.6 sigma) ± not stated dimensionless [2.2 Stacked SZE Signal: "peaking at $y= 2.4e-5$ or $\sim2.6\sigma$."]
- limitation (authors): Halo mass estimate from Lya gas dynamics is uncertain [Introduction: "uncertain due to radiative transfer effects and possible non-gravitational motions in the Ly"]
- limitation (authors): tSZE cannot be separated from kSZE without deep observations at other frequencies [Introduction: "It is also not possible to separate the tSZE from any kSZE contribution without further very deep observations at other frequencies."]
- limitation (authors): Stack insensitive to non-spherically symmetric kSZE [2.2 Stacked SZE Signal: "Our stacking analysis will not be sensitive to the non-spherically symmetric kSZE."]
- not stated (card): Manual mask definitions (regions) for QSO and serendipitous sources in each of the ten fields; Which channels were flagged as line-contaminated per SPW and the continuum reference frequency used; tclean deconvolver, niter, cleaning threshold value, weighting scheme details, and uv-taper values/units used for the 6 and 3 arcsec images; Self-calibration solution parameters beyond 'scan length' (ref…

### 2020A&A...638A..70D: The Massive and Distant Clusters of WISE Survey. SZ effect of Verification with the Atacama Compact Array - Localization and Cluster Analysis (2020; galaxy_clusters_and_sz; observational_alma_primary)
- question: Can ACA Band 3 observations robustly validate MaDCoWS cluster candidates through the thermal SZ effect, and what cluster masses do they give?
- step 2: fit SZ + point-source model to visibilities
  - method: Bayesian forward modeling of raw visibilities with gNFW pressure model (fixed shape parameters) plus Dirac-delta point sources with flat spectrum [3 Analysis technique: "we perform a Bayesian forward-modeling analysis directly on the visibilities of the ACA MaDCoWS sample"]
  - parameter: free: M500, z, centroid, point source positions and fluxes, flux normalization [3.3 Parameter priors: "The position $\bm{x}_{\textsc{ps}}$ and the source flux $i_{\textsc{ps}}$ are left free to vary."]
  - assumption: non-relativistic tSZ, kSZ neglected, flat ΛCDM Ωm=0.30 H0=70 [3.1 Estimating cluster masses: "we neglect any temperature-dependent corrections arising from the fully relativistic treatment of the thermal SZ effect"]
  - fitting: Normal priors on centroid (sigma 14.3, 15 arcsec); split-normal priors on z; normal prior on flux scaling; wide uninformative priors on point source flux [3.3 Parameter priors: "we adopt split-normal priors (cite: Wallis2014) on the redshifts $z$"]
  - validation: data-free runs show no prior-induced biases [3.3 Parameter priors: "have shown no biases in the parameter inference related to choice in the prior distributions"]
- step 3: assess detection significance
  - method: Bayes factor between SZ+point-source and point-source-only models, converted to sigma_eff [4 Results and discussion: "$\sigma_{\mathrm{eff}}\simeq\sqrt{2\Delta\log{\mathcal{Z}}}$"]
  - parameter: sigma_eff >~ 3 indicates robust detection [4 Results and discussion: "a value of $\sigma_{\mathrm{eff}}\gtrsim3$ is indicative of a robust detection"]
  - validation: Compared with dirty-image significance for most significant cluster [4 Results and discussion: "corresponding to a statistical significance of $4.06\sigma$"]
- result: clusters with significant SZ detection = 7 of 10 ± not stated clusters [abstract: "we obtain a significant detection of the SZ effect for seven out of the ten VACA LoCA clusters"]
- result: highest sigma_eff (universal profile) = 7.77 ± not stated dimensionless [4 Results and discussion: "$\sigma_{\mathrm{eff}}=7.77$"]
- result: M500 of most significant cluster (universal) = 2.57 ± +0.30/-0.30 1e14 Msun [Table 3: "$2.57\substack{+0.30\\-0.30}$"]
- result: point source flux in radio-lobe cluster field = 0.20 ± +0.06/-0.04 mJy [4.3 Unresolved sources: "$i_{\textsc{ps}}=0.20\substack{+0.06\\-0.04}~\mathrm{mJy}$"]
- limitation (authors): Limited angular dynamic range, short integrations and unresolved-source contamination limit mass inference [abstract: "the limited angular dynamic range of the ACA in Band 3 alone, short observational integration times, and possible contamination from unresolved sources"]
- not stated (card): Sampler name and settings (the evidence is computed, but the nested-sampling code is not named); Cluster IDs are missing from the converted tables, so rows cannot be matched to clusters; Spectral-window averaging and uv-data weighting or flagging applied before fitting; Redshift split-normal prior widths per cluster beyond the table values; Exact mass-richness fit procedure and likelihood; Code u…

### 2019A&A...628A.100D: An ALMA+ACA measurement of the shock in the Bullet Cluster (2019; galaxy_clusters_and_sz; observational_alma_primary)
- question: What are the Mach number and electron-ion equilibration behaviour of the western shock in the Bullet Cluster, measured from the thermal SZ pressure jump with ALMA+ACA plus X-ray priors?
- step 3: Forward-model SZ signal and fit visibilities
  - method: Integrate 3D pressure model (power-law downstream, gNFW upstream) along LoS, apply SZ spectrum with relativistic correction, FFT and sample at uv points, fit jointly ALMA+ACA [2.1 ALMA/ACA observations: "The SZ model image is then Fourier transformed and sampled to the position of the sparse interferometric data."]
  - software: galario, dynesty
  - parameter: Priors in Table 1: P_e,us and T_e,us split-normal from X-ray; shock nose and angle split-normal; M uniform 1-10; alpha uniform -10 to 0; kappa normal(1,0.05) [Table 1: "$\mathcal{M}$ | uniform | $\mathrm{min}=1$, $\mathrm{max}=10$"]
  - assumption: gamma=5/3; flat LCDM Om=0.30, H0=70; kSZ neglected [2.2.2 Bulk pressure distribution: "we then decide to not include the kinetic SZ effect in our model"]
  - fitting: Dynamic nested sampling with dynesty; posterior medians and 16/84 percentiles [2.3 Implementation details: "we improved the posterior sampling algorithm by adopting the dynamic nested sampling by (cite: Higson2017)."]
  - validation: Prior-only run; robustness tests varying gNFW slopes and centroid; residual dirty images [2.2 Sunyaev-Zeldovich model: "We test for biases in the parameter reconstruction arising from our specific choice for the distribution of priors by performing a *prior-only* run"]
- result: Delta log evidence (instantaneous vs adiabatic) = 1.30 ± +0.71/-1.48 dimensionless [3.2 Collisional equilibration: "$\Delta\log{\mathcal{Z}}=1.30\substack{+0.71\\-1.48}$"]
- limitation (authors): Systematics from cluster geometry and complex post-shock gas distribution; model does not capture X-ray morphology [abstract: "Our analysis is however limited by systematics related to the overall cluster geometry and the complexity of the post-shock gas distribution."]
- not stated (card): Exact binning parameters for visibilities; dynesty settings (live points, stopping criterion); Likelihood form and noise treatment details; Hyperbola shock-geometry best-fit values and X-ray image/region selection; Which ALMA/ACA execution blocks, calibrators and flagging were used; Gridding pixel scale and galario settings; Chandra X-ray values for prior derivation (Markevitch in prep. unpublish…

### 2024A&A...682A.186L: Feeding and feedback processes in the Spiderweb proto-intracluster medium (2024; galaxy_clusters_and_sz, high_z_galaxies; observational_alma_primary)
- question: Derive the thermodynamic profiles of the Spiderweb proto-ICM (z=2.16), test for a cool core, constrain the classical mass deposition rate and estimate the feedback energy budget, by combining Chandra X-ray density with ALMA SZ pressure
- step 5: Reconstruct SZ pressure profile from ALMA+ACA visibilities
  - method: Bayesian forward modelling of uv-plane visibilities with a line-of-sight integrated gNFW pressure model fitted jointly with a radio-galaxy point-component model; centroid fixed to the X-ray centroid; models combined with Bayesian Model Ave… [5 SZ and X-ray combined analysis: "the SZ distribution is obtained as the line-of-sight integral of a generalized Navarro-Frenk-White (NFW, (cite: 2007Nagai)) pressure distribution, with scaling parameters and radial slopes fixed to match specific formulations from the literature"] [5 SZ and X-ray combined analysis: "we inferred the SZ component jointly with the radio galaxy model, defined by the optimal, ordered set of point-like components, as in (cite: 2023DiMascolo)"]
  - software: dynesty
  - parameter: uv upper threshold 65 klambda [5 SZ and X-ray combined analysis: "We also consistently imposed an upper threshold of $65~\mathrm{k\lambda}$ to the analysed visibilities to make the extended radio galaxy unresolved in the direction orthogonal to the jet axis."]
  - parameter: SZ centroid fixed to X-ray centroid so that only the mass term (M500) is free per pressure model [5 SZ and X-ray combined analysis: "we did, however, fix the centroid position of the SZ model component to match the one derived by modeling the soft-band X-ray surface brightness distribution"] [Pressure models: "In such a way, the parameter set for each parameter reduces to the mass term only."]
  - assumption: Eight literature gNFW pressure profiles considered (A10 UP/MD, M14 UP/NCC, L15 REF/8.0/8.5, G17 EXT) [Pressure models: "the self-similar extended pressure model by (cite: 2017Gupta)"]
  - fitting: Nested sampling with dynesty; priors and likelihood details not stated [5 SZ and X-ray combined analysis: "The posterior exploration was performed using the nested sampling algorithm (cite: 2004Skilling; 2022Ashton), as implemented in the `dynesty` package (cite: dynesty; 2022Koposov)."]
  - validation: Model parameters statistically consistent with Di Mascolo et al. 2023; BMA profile used as reference with model variance propagated [5 SZ and X-ray combined analysis: "the parameters for each of the reconstructed models are found to be statistically consistent with the ones reported in (cite: 2023DiMascolo)"] [5 SZ and X-ray combined analysis: "we propagate the variance between the various pressure models in the marginalized posterior distribution"]
- step 7: Derive the temperature profile from SZ pressure and X-ray density
  - method: Marginalize the pressure model realizations within each X-ray annulus, then divide by the binned electron density: kT_e = P_e/n_e [5.2 Pressure and temperature profiles: "we post-processed the pressure profiles to estimate the $P_e(r)$ by marginalizing the values of the analytic realizations within each annulus"] [5.2 Pressure and temperature profiles: "the average electron temperature within a given annulus is finally computed as the ratio $k_{B}T_{e}(r)=P_{e}(r)/n_e(r)$"]
  - assumption: Ideal gas law; relativistic SZ correction negligible (<~1.5%); X-ray spectral temperature not used [5.2 Pressure and temperature profiles: "When simply assuming the ideal gas law"] [5.2 Pressure and temperature profiles: "we do not make use of the information provided by the X-ray spectral analysis"]
  - validation: Compared with the X-ray spectral kT=2.0 keV of Tozzi et al. 2022b; SZ-derived value lower by a factor of ~3, discussed as metallicity, non-thermal contamination or SZ filtering systematics [5.2 Pressure and temperature profiles: "this value is lower by a factor of $\sim 3$ with respect to that obtained in (cite: 2022bTozzi) with the X-ray spectral analysis"]
- result: M500 for A10 UP pressure model = 2.47 ± +0.44/-0.54 1e13 Msun [Table 1: "$2.47\substack{+0.44\\-0.54}$"]
- result: M500 for A10 MD pressure model = 2.01 ± +0.39/-0.49 1e13 Msun [Table 1: "$2.01\substack{+0.39\\-0.49}$"]
- result: M500 for M14 UP pressure model = 2.82 ± +0.53/-0.65 1e13 Msun [Table 1: "$2.82\substack{+0.53\\-0.65}$"]
- result: M500 for M14 NCC pressure model = 2.84 ± +0.53/-0.66 1e13 Msun [Table 1: "$2.84\substack{+0.53\\-0.66}$"]
- result: M500 for L15 REF pressure model = 2.59 ± +0.42/-0.48 1e13 Msun [Table 1: "$2.59\substack{+0.42\\-0.48}$"]
- result: M500 for L15 8.0 pressure model = 4.30 ± +0.55/-0.68 1e13 Msun [Table 1: "$4.30\substack{+0.55\\-0.68}$"]
- result: M500 for L15 8.5 pressure model = 6.54 ± +0.78/-0.95 1e13 Msun [Table 1: "$6.54\substack{+0.78\\-0.95}$"]
- result: M500 for G17 EXT pressure model = 2.20 ± +0.39/-0.55 1e13 Msun [Table 1: "$2.20\substack{+0.39\\-0.55}$"]
- result: Pressure profile average slope = ~1 ± not stated dimensionless [5.2 Pressure and temperature profiles: "with an average slope of $\sim 1,$ which is significantly flatter than the density profile"]
- result: Temperature at ~15 kpc and beyond 100 kpc = ~0.6 keV at ~15 kpc; ~1.8 keV beyond 100 kpc ± not stated keV [5.2 Pressure and temperature profiles: "a clear temperature gradient with value increasing from $\sim 0.6$ keV at $\sim 15$ kpc up to $\sim 1.8$ keV beyond 100 kpc"]
- result: Density-weighted SZ temperature at r>2 arcsec = 0.7 ± 0.3 keV [5.2 Pressure and temperature profiles: "$kT_{SZ,EW}= (0.7 \pm 0.3)$ keV"]
- limitation (authors): Diffuse emission within 2 arcsec of the AGN is not observationally constrained [2.1 Chandra X-ray data: "the surface brightness of the diffuse component within a radius of 2 arcsec is not observationally constrained and was treated as a free parameter"]
- limitation (authors): SZ normalisation may be underestimated because of interferometric filtering of large scales [5.2 Pressure and temperature profiles: "the normalization of the SZ signal may be underestimated compared to the actual pressure distribution due to the impact of the large-scale interferometric filtering"]
- limitation (authors): Low significance of SZ and X-ray signals limits detailed morphological comparison [4 SZ and X-ray combined analysis: "The low significance of both the SZ signal and the X-ray emission from the proto-ICM inevitably limits the possibility of performing a detailed morphological comparison."]
- not stated (card): CASA version and pipeline version for the Band 3 and Band 4 calibration; Flux, bandpass and phase calibrators and the flux-scale uncertainty; Exact Band 4 frequency setup and number of ALMA/ACA execution blocks used; dynesty settings (live points, stopping criterion) and the priors on M500 and radio-galaxy components; Radio-galaxy point-component model and how the 'optimal ordered set' was chosen…

### 2020EPJWC.22800009E: SZ contribution to characterize the shape of galaxy cluster haloes (2020; galaxy_clusters_and_sz, cosmology; multi_facility_alma_minor)
- question: Determine cluster baryonic and dark mass distributions, 3D shapes and hydrostatic mass bias using joint X-ray, SZ and lensing analysis.
- step 1: Deproject lensing constraints in the CLUMP-3D framework
  - method: Use X-ray and SZ shape and orientation information to deproject lensing mass and concentration. [Introduction: "In a nutshell, lensing constrains the 2D mass and concentration which are deprojected thanks to the information on shape and orientation from X-ray (surface brightness and temperature) and SZ."]
  - fitting: Bayesian inference for mass, concentration, intrinsic shape and equilibrium status [Introduction: "The mass and concentration can be then determined together with the intrinsic shape and equilibrium status of the cluster as required by precision astronomy through a Bayesian inference method."]
- step 2: Constrain the temperature profile in the proposed joint analysis
  - method: Combine SZ thermal pressure with X-ray gas density. [The case of MACS1206: "to constrain the temperature profile by combining the thermal pressure from SZ and the gas density from X-ray observations"]
- step 3: Fit gas and total-mass shapes in the proposed Heritage analysis
  - method: Fit three-dimensional triaxial ellipses to combined X-ray, SZ and lensing data. [3D analysis in the context of the Herit…: "Multi-probes three-dimensional Bayesian analysis will be applied to combined X-ray, SZ and lensing data to fit three-dimensional triaxial ellipses to the gas and total mass distribution,"]
  - assumption: Three-dimensional triaxial ellipses for gas and total mass [3D analysis in the context of the Herit…: "to fit three-dimensional triaxial ellipses to the gas and total mass distribution"]
  - fitting: Multi-probes three-dimensional Bayesian analysis [3D analysis in the context of the Herit…: "Multi-probes three-dimensional Bayesian analysis will be applied to combined X-ray, SZ and lensing data"]
  - validation: Proposed comparison with ΛCDM predictions after correcting geometrical biases [3D analysis in the context of the Herit…: "assessing their consistency with $\Lambda$CDM predictions and their equilibrium once geometrical biases (like projection) are corrected for."]
- limitation (authors): ALMA and NIKA2 images are very preliminary. [The case of MACS1206: "In Figure [3](#fig:prel), we present very preliminary images from our proprietary ALMA and NIKA2 exposures."]
- limitation (authors): Missing high-resolution SZ data at radial scales from 30 to 100 arcsec. [The case of MACS1206: "We are therefore missing high resolution SZ data at radial scales from 30 to 100 arcsec."]
- limitation (authors): More sensitive observations and a larger cluster sample are needed. [3D analysis in the context of the Herit…: "We need a combination of more sensitive observational data and a larger cluster sample, as available in the Heritage project"]
- not stated (card): ALMA observing band, frequencies, spectral windows and usable continuum bandwidth.; Execution identifiers, observed integration times, configurations and baseline coverage.; Calibration software, calibrators, flagging and flux-scale uncertainty.; SZ imaging or visibility-fitting procedure, weighting, beam, noise and compact-source treatment.; Relative calibration and spatial-filtering treatment w…

### 2019MNRAS.487.4037D: A joint ALMA-Bolocam-Planck SZ study of the pressure distribution in RX J1347.5-1145 (2019; galaxy_clusters_and_sz; observational_alma_primary)
- question: Can joint forward-modelling of ALMA/ACA visibilities with Bolocam and Planck images constrain the pressure distribution of RX J1347.5-1145, and does the south-eastern SZ excess indicate a strong overpressure or reflect model geometry?
- step 3: Compare SZ pressure profile to Chandra X-ray pressure
  - method: X-ray pressure from deprojected density times temperature compared with SZ model [5.1.2: "by multiplying the radial profiles of deprojected electron density and temperature distributions"]
  - software: CIAO
  - validation: Good overall agreement within uncertainties [5.1.2: "shows good overall agreement with the X-ray profile within the uncertainties of the two independent determinations"]
- step 5: Classify X-ray perturbations and estimate SZ excess
  - method: X-ray arithmetic in two Chandra bands; crude sphere estimate of dy/y [5.2.1: "The ‘X-ray arithmetic’ method reported in (cite: Churazov2016)"]
  - assumption: Overpressurized sphere radius ~90 kpc, offset ~130 kpc; adiabatic index 5/3 [5.2.1: "sphere of overpressurized gas with radius $\sim 90~\mathrm{kpc}$"]
  - validation: Order-of-magnitude only [X-ray imaging constraints on the nature…: "These are of course only an order-of-magnitude estimates, given the complexity of the cluster and the assumptions made."]
- result: Observed SE excess dy/y = 0.24 ± not stated dimensionless [5.2.1: "$\delta \vary/\vary\sim 0.24$"]
- limitation (authors): Models differ in components so statistical comparison is misleading; overfitting may hide overpressure; X-ray arithmetic limited to linear perturbations [5.2: "a direct comparison based on statistical considerations would provide misleading results"]
- not stated (card): Exact binning parameters and number of averaged visibilities; Planck MILCA implementation details and Y_cyl Gaussian prior; MCMC walkers, steps, burn-in and convergence; Fitting code is not public/versioned; Chandra reduction details and X-ray arithmetic smooth models; Source of 12.5 keV vs 7 keV temperature choices beyond brief description

### 2020ApJ...891...90R: Pressure Profiles and Mass Estimates Using High-resolution Sunyaev-Zel'dovich Effect Observations of Zwicky 3146 with MUSTANG-2 (2020; galaxy_clusters_and_sz; multi_facility_alma_minor)
- question: Can MUSTANG-2 90 GHz SZ data constrain the pressure profile and mass (M500, M2500) of the relaxed cluster Zwicky 3146, and how consistent are different mass estimators?
- step 2: Fit pressure profiles (NP and gNFW) with point sources
  - method: Compton y profile to T_B, matched to Minkasi bins with full covariance; 12 NP bins 5'' to 5'; A10 gNFW [4.2 Pressure profile fitting: "We define twelve bins with twelve logarithmically spaced radii between 5$''$ and 5$'$."]
  - software: emcee
  - parameter: relativistic correction with kT_e = 7 keV; line of sight integration to ±5 R500 [4.2 Pressure profile fitting: "we assume $k_B T_e = 7$ keV"]
  - assumption: spherical symmetry [4.2 Pressure profile fitting: "The choice of adopting spherical symmetry is motivated by (1) the ease of interpretation of results and comparison to the literature"]
  - fitting: emcee MCMC with full covariance likelihood [4.2 Pressure profile fitting: "In both cases, the fitting is done with the MCMC package `emcee` (cite: foreman2013)."]
  - validation: Agreement with XMM pressure profile [7 Conclusions: "The pressure profile recovered is in excellent agreement with the pressure profile derived from *XMM*."]
- limitation (authors): Outermost pressure bin likely biased low; unquantified additional systematic [7 Conclusions: "there is an additional systematic error due the issues discussed in the previous two paragraphs, but which we are currently unable to quantify."]
- not stated (card): Minkasi code/version and availability; MCMC settings and priors for pressure profile fits; Y-M relation parameters (tabulated A,B but sources unnamed in text); Flux calibration uncertainty derivation; Point source fit details

### 2019A&A...629A.104G: Sunyaev-Zel'dovich detection of the galaxy cluster Cl J1449+0856 at z = 1.99: The pressure profile in uv space (2019; galaxy_clusters_and_sz; observational_alma_primary)
- question: Can the thermal SZ decrement of the z=1.99 cluster Cl1449 be detected with ALMA+ACA at 92 GHz after subtracting FIR point sources in uv space, and what do the pressure profile and total mass imply?
- step 3: Fit pressure models and derive mass
  - method: Project GNFW profiles (LeB15, A10, S16, McD14) with fixed shapes, simulate with simalma, compare to uv profile with free mass; chi2 ranking [Modelling: "While we keep the GNFW parameters fixed to the various models’ values, we let the mass vary freely."]
  - software: CASA simalma
  - parameter: Compton-y background 1.6e-6 [Modelling: "including an average Compton-*y* background of $1.6\times10^{-6}$"]
  - assumption: Spherical models; M200 extrapolated from M500 assuming GNFW mass distribution [Modelling: "We here therefore extrapolate $M_{200}$ from $M_{500}$, assuming that the mass distribution follows the GNFW profile."]
  - validation: FFT approximation vs simalma differs at most ~4% [uv plane modelling: "We find a relative difference between both of at most $\sim$4% (Fig. [10](#fig:fft))"]
- step 5: Test SZ-X-ray peak offset significance
  - method: Monte Carlo of simulated A10 decrement with noise from visibility weights, point-source fit with free position [Peak offset significance: "We then perform a point-source extraction with free position, as described in Section [\[cooking\]](#cooking), which we compare to the observed offsets."]
- result: AGN 8.5 model mass = ~1.8e14 ± not stated Msun [Results and discussion: "only AGN 8.5 yields a higher mass of $\sim$$1.8\times10^{14}$ M$_{\odot}$"]
- limitation (authors): Residual positive signal from undetected sources means significance is conservative; S/N too low to strongly constrain pressure models [Conclusions: "The final S/N of the data, conservatively estimated, is not quite high enough to strongly constrain ICM pressure models."]
- not stated (card): CASA version; Fit method/statistic and uncertainty treatment for model amplitude and mass (chi2 minimisation details); How M200 was extrapolated from M500 numerically; simalma setup details (configurations, antenna lists); Point-source subtraction details for source grouping; Details of how ALMA and ACA were weighted when merged; Whether 2012.1.00885.S and 2015.1.01355.S data were used directly (…

### 2020PASJ...72...33K: Deeply cooled core of the Phoenix galaxy cluster imaged by ALMA with the Sunyaev-Zel'dovich effect (2020; galaxy_clusters_and_sz; observational_alma_primary)
- question: How much thermal gas is cooling to low temperatures in the Phoenix cluster core, probed with an ALMA SZE image combined with Chandra X-ray data independent of the X-ray spectrum
- step 5: Derive the Compton y map and compare the inner pressure profile
  - method: Divide ALMA image by c1 = 0.94, subtract mean signal at theta = 42 arcsec, apply relativistic correction with projected X-ray temperature, azimuthally average and compare with generalized NFW pressure profiles of cluster samples [4.3 Compton y-parameter map and the inn…: "the ALMA image was divided by the correction factor for the missing flux of 0.94"] [4.3 Compton y-parameter map and the inn…: "the mean signal (consistent with zero) at $\theta = 42''$ is subtracted"]
  - parameter: Geometrically spaced bins, innermost 0-4 arcsec, size increasing by a factor 1.1 [4.3 Compton y-parameter map and the inn…: "the bins are geometrically spaced with the inner-most bin at $0 < \theta < 4''$ and the size increasing by a factor of 1.1"]
  - assumption: M500 = 8.8e14 h^-1 Msun, r500 = 0.92 h^-1 Mpc at z = 0.597 [4.3 Compton y-parameter map and the inn…: "assuming $M_{500} = 8.8 \times 10^{14} h^{-1} M_{\odot}$ and $r_{500} = 0.92 h^{-1}$Mpc at $z=0.597$ for the Phoenix cluster"]
  - validation: y map morphology consistent with X-rays; inner profile agrees with local cool core expectation [4.3 Compton y-parameter map and the inn…: "overall morphology of the Compton $y$-parameter map does not exhibit deviation from that of X-rays."]
- result: Peak incremental Compton y = 5.3e-4 ± 0.4 (stat) and 0.3 (sys), in units of 1e-4 dimensionless [4.3 Compton y-parameter map and the inn…: "The peak value is $\Delta y = (5.3 \pm 0.4 \mbox{ [statistical]} \pm 0.3 \mbox{ [systematic]})\times 10^{-4}$"]
- limitation (authors): Equation-of-state limit is weak [4.1 Comparison to X-ray data: "While the limit is still weak, the observed perturbations in the Phoenix cluster core is consistent with being isobaric"]
- limitation (authors): Absolute values of the X-ray pseudo pressure are arbitrary [4.1 Comparison to X-ray data: "Note that absolute values of the pseudo pressure are arbitrary"]
- limitation (authors): Temperature at r > 250 kpc cannot be constrained by the ALMA data [4.4 Deprojected electron temperature an…: "As the temperature at $r > 250$ kpc ($\theta > 37''$) cannot be constrained by the ALMA data"]
- not stated (card): Phase centre (target field centre) coordinates are blank in the text; tclean image size, cell size, niter / number of minor cycles, gridder and phasecenter for the 7-pointing mosaic; Calibration CASA/pipeline version and whether QA2 products were used unmodified or re-calibrated; any self-calibration; Starting parameters, weighting and error treatment used in uvmodelfit; source positions are blan…

## All papers in this technique

- 2016ApJ...829L..23B (2016): ALMA-SZ Detection of a Galaxy Cluster Merger Shock at Half the Age of the Universe
- 2019A&A...628A.100D (2019): An ALMA+ACA measurement of the shock in the Bullet Cluster
- 2019A&A...629A.104G (2019): Sunyaev-Zel'dovich detection of the galaxy cluster Cl J1449+0856 at z = 1.99: The pressure profile in uv space
- 2019MNRAS.487.4037D (2019): A joint ALMA-Bolocam-Planck SZ study of the pressure distribution in RX J1347.5-1145
- 2019MNRAS.490.5134B (2019): Detecting the halo heating from AGN feedback with ALMA
- 2020A&A...638A..70D (2020): The Massive and Distant Clusters of WISE Survey. SZ effect of Verification with the Atacama Compact Array - Localization and Cluster Analys…
- 2020ApJ...891...90R (2020): Pressure Profiles and Mass Estimates Using High-resolution Sunyaev-Zel'dovich Effect Observations of Zwicky 3146 with MUSTANG-2
- 2020EPJWC.22800009E (2020): SZ contribution to characterize the shape of galaxy cluster haloes
- 2020PASJ...72...33K (2020): Deeply cooled core of the Phoenix galaxy cluster imaged by ALMA with the Sunyaev-Zel'dovich effect
- 2021A&A...650A.153D (2021): Multiwavelength view of SPT-CL J2106-5844. The radio galaxies and the thermal and relativistic plasmas in a massive galaxy cluster merger a…
- 2021MNRAS.503.1174K (2021): Feedback factory: multiple faint radio jets detected in a cluster at z = 2
- 2024A&A...682A.186L (2024): Feeding and feedback processes in the Spiderweb proto-intracluster medium
- 2024A&A...689A..41V (2024): XLSSC 122 caught in the act of growing up: Spatially resolved SZ observations of a z = 1.98 galaxy cluster
- 2024ApJ...969...56M (2024): Observational Constraints on Sunyaev─Zeldovich Effect Halos around High-z Quasars
