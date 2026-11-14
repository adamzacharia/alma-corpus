# The Kinematics of z ≳ 6 Quasar Host Galaxies

`2021ApJ...911..141N` | The Astrophysical Journal 2021 | first author: Neeleman, Marcel | arXiv: 2102.05679 | DOI: 10.3847/1538-4357/abe70f | **HELD OUT (benchmark)**

Card schema 1.0 | model claude-haiku-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: Dynamical support, dynamical mass vs SMBH mass, and molecular gas fraction of 27 z>~6 quasar host galaxies from resolved [CII] kinematics  
  > "We explore the kinematics of 27 $z \gtrsim 6$ quasar host galaxies" (abstract)
- Target **Sample of 27 z>~6 quasar host galaxies**: coordinates per-object values in Table 1 (not summarized in text)  
  > "Throughout this manuscript we assume a standard, flat" (Methods: Kinematic Modeling); z/distance per-object z_kin in Table 1 (not summarized in text)  
  > "Throughout this manuscript we assume a standard, flat" (Methods: Kinematic Modeling); distance from not stated; cosmology assumed (flat Lambda-CDM, H0 = 70)  
  > "Throughout this manuscript we assume a standard, flat" (Methods: Kinematic Modeling)

## Data provenance

- ALMA projects: 2012.1.00240.S, 2012.1.00882.S, 2013.1.00273.S, 2015.1.00339.S, 2015.1.00692.S, 2016.A.00018.S, 2016.1.00544.S, 2017.1.00396.S, 2017.1.01301.S, 2018.1.00908.S
- bands: _not stated_
- frequencies and spectral setup: [CII] line; channel spacing 30 MHz; ALMA line-spread function about 1 MHz  
  > "the channel spacing of 30 MHz is much larger than the line-spread function of ALMA" (Section 3.2 qubefit)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: about 0.25 arcsec for the modeled sample; sample range 0.10 to 0.25 arcsec  
  > "at a resolution of $\approx$ $0.25\ensuremath{''}$" (abstract); "The observations range in resolution between" (Sample Selection)
- max recoverable scale: _not stated_
- sensitivity: RMS 0.13 to 0.54 mJy/beam per 30 MHz channel, average 0.27 mJy/beam  
  > "and have root mean square (RMS) sensitivities between 0.13 and 0.54 mJy beam$^{-1}$, with an average of 0.27 mJy beam$^{-1}$, per 30 MHz channel" (Sample Selection)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: mixed: new observations from the team plus previous team data and archival data at the same resolution  
  > "We supplement this data with previous data obtained by our team, as well as archival data at the same resolution." (Sample Selection)
- Line: C II 158 micron fine-structure line (not stated)
- External data: Local bulge mass - black hole mass relation used for comparison  
  > "we compare these measurements with the relationship between bulge mass and black hole mass for local galaxies" (Comparison between Dynamical and SMBH Mass) [from (cite: Kormendy2013)]
- External data: SMBH masses from Mg II (C IV for three, Eddington-limit for three); most taken from a NIR spectroscopic study  
  > "Nearly all of the SMBH mass estimates are taken from a recent study analyzing NIR spectra from a large sample of $z \gtrsim 6$ quasars" (Comparison between Dynamical and SMBH Mass) [from (cite: Schindler2020)]
- External data: SMBH mass for P167-13 from literature  
  > "except for P167$-$13 (cite: Mazzucchelli2017) and J1342$+$0928 (cite: Onoue2020)" (Comparison between Dynamical and SMBH Mass) [from (cite: Mazzucchelli2017)]
- External data: SMBH mass for J1342+0928 from literature  
  > "except for P167$-$13 (cite: Mazzucchelli2017) and J1342$+$0928 (cite: Onoue2020)" (Comparison between Dynamical and SMBH Mass) [from (cite: Onoue2020)]
- External data: [CII]-to-molecular gas conversion, alpha = 31 Lsun/Msun for z~2 main-sequence galaxies  
  > "with $\alpha_{\rm [CII]} = 31~L_\odot/M_\odot$ as calibrated for $z \sim 2$ main-sequence galaxies" (Gas Masses versus Dynamical Masses) [from (cite: Zanella2018)]
- External data: Dust mass opacity coefficient kappa = 0.77 (850 micron / lambda)^beta cm^2 g^-1  
  > "a dust mass opacity coefficient of $\kappa_\lambda = 0.77 (850 \mu{\rm m}/\lambda)^\beta$ cm$^2$ g$^{-1}$ (cite: Dunne2000)" (Gas Masses versus Dynamical Masses) [from (cite: Dunne2000)]
- External data: Previous [CII] FWHM of total emission for each source  
  > "The second column lists the FWHM of the total \[C II\] emission as reported in (cite: Venemans2020)" (Methods for Estimating Circular Velocities) [from (cite: Venemans2020)]
- External data: Velocity dispersion measurements of lower-redshift galaxies for comparison  
  > "the velocity dispersion measurements for both individual galaxies (cite: Livermore2015; Turner2017; FoersterSchreiber2018)" (Large Velocity Dispersions) [from (cite: Livermore2015; Turner2017; FoersterSchreiber2018)]
- Simulation/model as data: Simulations predict the cold ISM quickly settles into a cold, thin rotating disk  
  > "The first scenario is predicted by simulations (cite: Lupi2019)" (Models)

## Processing

### Calibration

- pipeline or manual: not stated here; reduction described only in Venemans2020  
  > "Details of the observations and data reduction procedure for the data used in this paper are given in (cite: Venemans2020)" (Sample Selection)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: cleaned data cube used; cleaning algorithm and settings not stated  
  > "We therefore run the fitting code on a small region containing the emission in the" (Section 3.2 qubefit)
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: all pixels with at least a 3 sigma signal, expanded by a buffer of at least one independent measurement  
  > "The mask used for the analysis in this paper is generated from all pixels with at least a 3$\sigma$-significant signal" (Section 3.2 qubefit)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: approximately 0.25 arcsec  
  > "at a resolution of approximately $0.25\ensuremath{''}$" (Summary and Concluding Remarks)
- final rms: 0.13 to 0.54 mJy/beam per 30 MHz channel (average 0.27)  
  > "and have root mean square (RMS) sensitivities between 0.13 and 0.54 mJy beam$^{-1}$, with an average of 0.27 mJy beam$^{-1}$, per 30 MHz channel" (Sample Selection)

### Inherited from earlier work

- Observations, data reduction and cube products used for all 27 sources  
  > "Details of the observations and data reduction procedure for the data used in this paper are given in (cite: Venemans2020)" (Introduction) [from (cite: Venemans2020)]
- Thin disk model description (nine parameters)  
  > "has been previously summarized in Appendix C of (cite: Neeleman2019)" (Thin Disk Model) [from (cite: Neeleman2019)]
- Velocity offset v_c(z_kin) from the fiducial redshift of [CII]  
  > "as derived in (cite: Venemans2020)" (Thin Disk Model) [from (cite: Venemans2020)]
- Methods for deriving velocity and velocity dispersion fields  
  > "there exist several methods to create these velocity fields from the data (cite: Deblok2008)" (Mean Velocity and Velocity Dispersion Fields) [from (cite: Deblok2008)]
- eta = 2 r / R_D for an exponential turbulent pressure-supported disk  
  > "Following (cite: Burkert2010), if we model the mass distribution as an exponential, turbulent, pressure-supported disk" (Methods for Estimating Circular Velocities) [from (cite: Burkert2010)]
- Dust-based molecular mass conversion (dust temperature, emissivity, CMB correction)  
  > "we convert the dust continuum flux measurement into a dust mass assuming the method described in detail in (cite: Venemans2016)" (Gas Masses versus Dynamical Masses) [from (cite: Venemans2016; cite: DaCunha2013)]
- [CII]-to-molecular mass conversion with 0.3 dex uncertainty  
  > "assuming the conversion given in (cite: Zanella2018)" (Gas Masses versus Dynamical Masses) [from (cite: Zanella2018)]
- Circular velocity for non-ordered rotation: 0.52 FWHM  
  > "If the velocities are dominated by non-ordered rotation, the circular velocity can be approximated by (cite: Decarli2018)" (Methods for Estimating Circular Velocities) [from (cite: Decarli2018)]
- Circular velocity for ordered rotation: 0.75 FWHM / sin i (FWHM to W20 for Gaussian)  
  > "Here $i$ is the inclination of the galaxy and the factor of 0.75 comes from the conversion of the FWHM to the full width at 20% of the peak intensity" (Methods for Estimating Circular Velocities) [from (cite: Ho2007)]
- Double-exponential [CII] surface brightness profile (faint extended component) used as caveat on R_e  
  > "is actually best described by a double exponential profile with a bright, compact component" (Radial Extent for Dynamical Mass Estimate) [from (cite: Novak2020)]

### Not stated but needed to reproduce (our reading)

- Continuum flux densities and the continuum-based dust masses for each source (not tabulated; Table 4 gives only derived gas masses)
- Cleaning and imaging parameters (weighting, robust value, taper, cell size, image size, deconvolver settings) for the cubes used in the fits
- Line-free channel selection and continuum subtraction method for the [CII] cubes
- Spectral window and velocity range fitted per source, and the image region cut out for qubefit
- Flat prior bounds for each free parameter and the number of walkers and steps for emcee
- How the beam Gaussian was fit to each cube, and which beam (per source) was used in the convolution
- Velocity field clipping threshold used for moment maps in the comparison (Appendix), and the exact pixel size
- Source-by-source membership in the radial profile sample beyond the 13-galaxy statement, and the exact bin edges used
- Dust temperature/beta uncertainty propagation details and the systematic budget combination rule
- SMBH masses for the 18 undisturbed and 9 disturbed sources as used in Figure 7 are given only as Table 4 entries; line-based mass recipes from Schindler2020 are needed to verify them

## Analysis recipe

1. **fit kinematic models to the [CII] data cubes**: Fit a thin disk (nine parameters) and a dispersion-dominated bulge (six parameters) model to the 3D [CII] cube with a modified chi-squared likelihood, using MCMC  
  > "For this paper we use a modified $\chi^2$ likelihood function of the form" (Methods: Kinematic Modeling); "The thin disk model is described by nine parameters" (Thin Disk Model); "In total, the bulge model is described by six parameters." (Dispersion-Dominated Bulge Model)
   - software: qubefit, emcee
   - parameter: f_beam adjustment assumes Nyquist sampling at about 2 samples per FWHM  
  > "Under the assumption that the beam can be Nyquist-sampled at approximately 2 samples per FWHM of the beam" (Section 3.2 qubefit)
   - parameter: beam modeled as 2D Gaussian from a Gaussian fit to the data cube beam  
  > "We model the beam with a 2D-Gaussian with size and position angle as determined from a Gaussian fit to the beam of the data cube." (Section 3.2 qubefit)
   - parameter: mask from 3 sigma pixels with one-measurement buffer  
  > "The mask used for the analysis in this paper is generated from all pixels with at least a 3$\sigma$-significant signal" (Section 3.2 qubefit)
   - assumption: gas gravitationally supported, emission modeled as thin disk or bulge  
  > "under the assumption that the gas is gravitationally supported" (Models)
   - assumption: velocity dispersion constant over the full extent of the emission  
  > "we assume the velocity dispersion profile is constant over the full extent of the emission" (Dispersion-Dominated Bulge Model)
   - assumption: exponential emission profile I = I0 exp(-r/R_D)  
  > "The emission of the disk is assumed to be axisymmetric and exponentially decreasing with distance from the center." (Thin Disk Model)
   - fitting: emcee affine-invariant ensemble sampler; two independent ensembles with flat uninformed priors; first 30 percent removed as burn-in; median and 16th-84th percentiles reported; unconstrained parameters given as 3 sigma limits  
  > "We assume flat, uninformed priors on all of the parameters, and run two independent ensembles using different initial values." (Section 3.2 qubefit); "For those parameters that are constrained by the model, we report median values with 16$^{\rm th}$ to 84$^{\rm th}$ percentile ranges of the PDFs." (Section 3.2 qubefit)
   - validation: compare the two ensembles with each other to check convergence; for P183+05 the combined chain has 420 000 realizations  
  > "To check for the convergence of the ensemble, we compare the ensemble both with itself and with the other ensemble." (Section 3.2 qubefit); "with a total of 420 000 realizations" (Analysis of the Kinematic Modeling)
2. **assess goodness of fit and residual noise**: Reduced chi-squared and one-sample KS probability of residuals, using one measurement per beam within the union of the fitting mask and the 1 sigma model contour  
  > "we calculate two goodness-of-fit statistics: a simple reduced-$\chi^2$ statistic and a one-sample Kolmogorov-Smirnov (KS) probability" (Goodness of Fit)
   - software: SciPy
   - parameter: one independent measurement per beam  
  > "we only take one measurement per beam" (Goodness of Fit)
   - assumption: residuals compared to Gaussian with the observed RMS of the data cube  
  > "The one-sample KS-statistic is calculated by comparing the residuals for the $n$ independent measurements to a Gaussian distribution with the observed RMS of the data cube." (Goodness of Fit)
   - fitting: _not stated_
   - validation: KS probability of 0.05 as a 95 percent rejection threshold  
  > "a value of 0.05 would indicate that we can reject the null hypothesis" (Goodness of Fit)
3. **derive mean velocity and velocity dispersion fields**: Single Gaussian fit to the spectrum of each spaxel, with moment-map initial guesses; chosen over moment (M1/M2) maps  
  > "we use the fitting routines in `astropy` (cite: Astropy2013; Astropy2018) to fit a single Gaussian to the spectrum of each individual spaxel" (Two Methods for Deriving Mean Velocity and Velocity Dispersion Fields)
   - software: astropy
   - parameter: no clipping of input needed for Gaussian fits  
  > "The main advantage of using a fitting function is that no input needs to be clipped." (Two Methods for Deriving Mean Velocity and Velocity Dispersion Fields)
   - assumption: spectra assumed Gaussian  
  > "for quasars the spectra appear Gaussian" (Two Methods for Deriving Mean Velocity and Velocity Dispersion Fields)
   - fitting: per-spaxel single Gaussian least-squares fit (fitting method not further specified)  
  > "fit a single Gaussian to the spectrum of each individual spaxel" (Two Methods for Deriving Mean Velocity and Velocity Dispersion Fields)
   - validation: no systematic skew found when compared to moment maps on P183+05  
  > "There is no evidence that the assumption of a Gaussian profile is systematically skewing the measurements in either field." (Two Methods for Deriving Mean Velocity and Velocity Dispersion Fields)
4. **measure radial profiles of rotation and dispersion**: Invert the line-of-sight velocity equation per pixel to get v_rot, bin by de-projected radius; exclude within 30 deg of minor axis; compare with beam-convolved constant-velocity model  
  > "We remove measurements within 30$\ensuremath{^\circ}$ of the minor axis" (Radial Profiles of the Mean Velocity and Velocity Dispersion); "Here we will only consider the 13 galaxies that show no signs of mergers, and are resolved over more than two beams" (Radial Profiles of the Mean Velocity and Velocity Dispersion)
   - parameter: 13 undisturbed galaxies resolved over more than two beams  
  > "Here we will only consider the 13 galaxies that show no signs of mergers, and are resolved over more than two beams" (Radial Profiles of the Mean Velocity and Velocity Dispersion)
   - assumption: all velocity is in-plane rotation (no radial motion)  
  > "Assuming that all of the velocities are due to rotational motion within this plane, i.e., we ignore any radial motion of the gas" (Thin Disk Model)
   - fitting: _not stated_
   - validation: constant-velocity beam-convolved model reproduces the rise in rotation velocity  
  > "indicating that the increase in rotational velocity for all galaxies is largely driven by the effects of beam smearing" (Radial Profiles of the Mean Velocity and Velocity Dispersion)
5. **estimate circular velocity**: Three estimators: FWHM-based non-ordered (0.52 FWHM), ordered (0.75 FWHM/sin i), and kinematic v_circ = sqrt(v_rot^2 + eta sigma^2) with eta = 3.4 (fiducial)  
  > "This rotational velocity is either directly taken as the circular velocity estimate, or the velocity dispersion measurement is taken into account by adding it in quadrature" (Methods for Estimating Circular Velocities)
   - parameter: eta = 3.4 at r = R_e for exponential disk (r = 1.678 R_D)  
  > "resulting in $\eta = 3.4$" (Methods for Estimating Circular Velocities)
   - assumption: eta range 2 to larger than 6 across literature; 40 percent systematic covers eta range  
  > "We note, however, that the reported systematic uncertainties in the dynamical mass include a 40 % contribution that encompasses the expected range in $\eta$." (Methods for Estimating Circular Velocities)
   - assumption: inclination from kinematic model used for ordered estimate; 55 deg used in literature  
  > "For the ordered rotation circular velocity estimate, we take the inclination as derived from the kinematic modeling." (Methods for Estimating Circular Velocities)
   - fitting: _not stated_
   - validation: kinematic estimate usually bracketed by the two FWHM-based estimates  
  > "This circular velocity estimate in most cases is bracketed by the other two methods" (Methods for Estimating Circular Velocities)
6. **compute dynamical mass at 2 R_e**: Spherical estimate M_dyn(R) = v_circ^2 R / G = 2.33e5 v_circ^2 R at R = 2 R_e, with R_e = 1.678 R_D  
  > "where the latter equality holds if the circular velocity, $v_{\rm circ}$, is given in km s$^{-1}$, $R$ in kpc, and the dynamical mass is returned in $M_\odot$" (Dynamical Masses); "we can now estimate the dynamical mass of $z \gtrsim 6$ quasar host galaxies at $2R_{\rm e}$" (Dynamical Masses)
   - parameter: radius 2 R_e (85 percent of flux for exponential)  
  > "which for an exponential profile contains 85% of the total flux" (Radial Extent for Dynamical Mass Estimate)
   - assumption: spherically symmetric mass distribution; disk potential may overestimate mass by up to 30 percent  
  > "will overestimate the dynamical mass up to 30 %, if all of the mass was constrained within a thin disk" (Dynamical Masses)
   - fitting: _not stated_
   - validation: systematic budget: 20 percent toward lower mass, 50 percent on lower bound for R_e tracer, 40 percent for R_e underestimate  
  > "we conservatively increase the dynamical mass uncertainty by 20 % toward lower masses" (Dynamical Masses); "we will conservatively add a 50% systematic uncertainty to the lower bound of the dynamical mass estimate" (Radial Extent for Dynamical Mass Estimate)
7. **estimate molecular gas masses**: Two methods: dust continuum mass with constant dust-to-gas ratio, and [CII] luminosity conversion  
  > "Estimates for the molecular mass are determined in two ways." (Gas Masses versus Dynamical Masses)
   - parameter: T_d = 47 K, beta = 1.6; uncertainty T_d 30 to 60 K, beta 1.4 to 1.8  
  > "we assume a dust temperature of T$_{\rm d}$ = 47 K, an emissivity index of $\beta$ = 1.6" (Gas Masses versus Dynamical Masses); "Uncertainties are calculated assuming T$_{\rm d}$ ranges between 30 and 60 K and $\beta$ ranges between 1.4 and 1.8." (Gas Masses versus Dynamical Masses)
   - parameter: dust-to-gas ratio 100; molecular-to-total gas fraction 0.75  
  > "Dust masses are converted into molecular masses assuming a dust-to-gas ratio of 100 and a molecular-to-total gas mass fraction of 0.75." (Gas Masses versus Dynamical Masses)
   - assumption: [CII]-to-molecular conversion from z~2 main-sequence galaxies applied to quasar hosts  
  > "with $\alpha_{\rm [CII]} = 31~L_\odot/M_\odot$ as calibrated for $z \sim 2$ main-sequence galaxies" (Gas Masses versus Dynamical Masses)
   - fitting: _not stated_
   - validation: [CII] conversion uncertainty 0.3 dex; the conversion is judged not valid at z>~6 by the authors  
  > "This suggests that the conversion factor derived for main-sequence galaxies at $z \sim 2$ is not valid for quasar host galaxies at $z \gtrsim 6$." (Gas Masses versus Dynamical Masses)
8. **compare dynamical mass with SMBH mass and local relation**: Compare sample mean dynamical mass with the local bulge mass - black hole mass relation of Kormendy2013, using black hole masses mostly from Mg II  
  > "Comparing the mean of the $z \gtrsim 6$ quasar sample" (Comparison between Dynamical and SMBH Mass)
   - parameter: black hole masses mostly from Mg II; C IV for three; Eddington assumption for three  
  > "For 21 of the quasars in our sample, the Mg II emission line was used for the SMBH mass determination." (Comparison between Dynamical and SMBH Mass)
   - assumption: dynamical mass taken as equivalent to bulge mass  
  > "If we assume that the dynamical mass and the bulge mass are roughly equivalent between these studies" (Comparison between Dynamical and SMBH Mass)
   - fitting: _not stated_
   - validation: result unchanged when only Mg II black hole masses are used  
  > "We note that this result remains unchanged if we only consider those quasars that have a black hole estimate from Mg II." (Comparison between Dynamical and SMBH Mass)

## Software

- **qubefit** : fit thin disk and dispersion-dominated bulge models to the [CII] data cubes with an MCMC likelihood  
  > "calculate the best-fit parameters and associated uncertainties for these models using a Markov Chain Monte Carlo (MCMC) approach" (Section 3.2 qubefit)
- **emcee** : affine-invariant MCMC ensemble sampling of model parameter posteriors  
  > "we use the affine-invariant MCMC ensemble sampler, `emcee`, to sample the multidimensional parameter space (cite: ForemanMackey2013)" (Section 3.2 qubefit)
- **Astropy** : Gaussian fits to the spectrum of each spaxel for velocity and dispersion fields  
  > "we use the fitting routines in `astropy` (cite: Astropy2013; Astropy2018) to fit a single Gaussian to the spectrum of each individual spaxel" (Two Methods for Deriving Mean Velocity and Velocity Dispersion Fields)
- **SciPy** : KS probability conversion for residual goodness of fit  
  > "using standard recipes within `scipy`" (Goodness of Fit)
- **NumPy** : _not stated_
- **CASA** : _not stated_
- **Matplotlib** : _not stated_
- **Corner** : _not stated_

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| mean dynamical mass, undisturbed subsample (at 2 R_e) | 5.0 | +/-0.8 (statistical); +/-3.5 systematic | 10^10 Msun | 6 | with a mean mass of $5.0 \pm 0.8\,(\pm 3.5) \times 10^{10} M_\odot$. |
| mean velocity dispersion, undisturbed sample | 129 | +/-10 | km s^-1 | 1 | The mean velocity dispersion for the undisturbed sample is $129 \pm 10$ km s$^{-1}$. |
| median velocity dispersion of sample | 123 | not stated | km s^-1 | 1 | with a median of 123 km s$^{-1}$ |
| mean velocity dispersion, no-velocity-gradient subsample vs gradient subsample | 153 vs 95 | +/-32 and +/-25 | km s^-1 | 1 | $153 \pm 32$ compared to $95 \pm 25$ km s$^{-1}$ |
| mean inclination, undisturbed subsample | 33 | +/-5 | degrees | 5 | This inclination is on average $33 \pm 5 \ensuremath{^\circ}$ for those quasars in the undisturbed subsample. |
| mean effective radius, undisturbed sample | 1.11 | +/-0.11 | kpc | 4 | The mean effective radius for the undisturbed sample is $1.11 \pm 0.11$ kpc. |
| kinematic eta at R_e for exponential disk | 3.4 | not stated | dimensionless | 5 | We will take this value as our fiducial value |
| mean SMBH mass | 2.2 | +/-0.5 | 10^9 Msun | 8 | The sample has a mean SMBH mass of $2.2 \pm 0.5$ $\times 10^{9} M_\odot$. |
| significance of offset from local bulge mass - BH mass relation | 2.4 | not stated | sigma | 8 | which is a 2.4$\sigma$ deviation from the local correlation. |
| dynamical mass relative to local relation (factor smaller) | about 7 | not stated | dimensionless | 8 | shows that the dynamical masses of these quasars are smaller by about a factor of seven |
| molecular-to-dynamical mass ratio from dust continuum | 0.3 | not stated | dimensionless | 7 | When we use the dust continuum emission to estimate the molecular mass, we find a molecular-to-dynamical mass ratio of 0.3. |
| median molecular-to-dynamical mass ratio from [CII] luminosity | 1.7 | not stated | dimensionless | 7 | with a median molecular-to-dynamical mass ratio of 1.7 |
| molecular gas fraction (conservative lower limit) | >10 | not stated | percent | 7 | we still find that the molecular gas accounts for $>$10 % of the total dynamical mass of the system |
| number of disturbed sources in the sample | 9 of 27 | not stated | galaxies | 0 | One third (9 out of 27) of quasar host galaxies have disturbed |

## Qualitative findings

- The [CII] kinematics of z>~6 quasar hosts are varied: about a third show disks, a third show disturbed emission, and a third show dispersion-dominated gas with no velocity gradient  
  > "there are equally as many sources that show the gas being disturbed by a recent merger and those that have turbulent gas dynamics" (Summary and Concluding Remarks)
- The sample lies offset from the local bulge mass - black hole mass relation  
  > "we find that $z \gtrsim 6$ quasar host galaxies fall above the locally derived correlation" (Summary and Concluding Remarks)

## Claim tuples

- H: Are z>~6 quasar host gas kinematics disk-like, merger-disturbed, or dispersion-dominated? | E: Visual classification of 27 [CII] velocity fields and 3D thin disk vs bulge model fits with qubefit | R: 10 galaxies with smooth velocity gradients, 8 with no gradient, 9 disturbed | F: Gas kinematics vary across the sample; no single precipitating event is implied, which the authors call very speculative | **partially**
- H: Do z>~6 quasar hosts fall on the local bulge mass - black hole mass relation? | E: Dynamical masses at 2 R_e for the undisturbed subsample compared with Mg II-based SMBH masses and the Kormendy2013 relation | R: Mean dynamical mass 5.0e10 Msun (+/-0.8 stat, +/-3.5 sys); mean SMBH mass 2.2e9 Msun; offset about a factor 7 at 2.4 sigma | F: Sample falls above the local relation, with the authors noting the dynamical-equals-bulge assumption as a caveat | **supported**
- H: Is the molecular gas fraction of z>~6 quasar hosts significant? | E: Molecular masses from dust continuum (constant dust-to-gas) and from [CII] luminosity (z~2 conversion) compared with dynamical masses | R: Dust-based molecular-to-dynamical ratio 0.3; [CII]-based median ratio 1.7; conservative lower limit >10 percent | F: Molecular gas is a non-negligible fraction of the baryonic mass; the z~2 [CII] conversion is judged invalid here | **supported**
- H: Is the high velocity dispersion intrinsic or due to redshift evolution? | E: Comparison of sample dispersions with an exponential extrapolation of lower-redshift dispersion measurements | R: Mean dispersion 129 +/- 10 km/s, consistent with the extrapolation | F: Attributed to higher redshift, but the authors caution that the extrapolation is challenging to interpret | **partially**
- H: Does the observed rise in rotation velocity with radius reflect a real rotation curve? | E: Radial profiles compared with a beam-convolved constant-velocity model cube | R: The constant-velocity model shows a similar rise in rotational velocity with radius | F: Rise is driven by beam smearing; resolution is insufficient to measure the rotation curve shape | **supported**

## Reasoning

- Why this data: Resolution of about 0.25 arcsec is needed to spatially resolve the [CII] emission for morphology, kinematics and dynamical mass  
  > "requires a resolution such that the" (Sample Selection)
- Why this method: Fit the full 3D cube with a forward model because moment-based 2D analyses give large uncertainties at low resolution and S/N  
  > "result in large uncertainties on the derived kinematics from low resolution, low signal-to-noise (S/N) observations" (Methods: Kinematic Modeling)
- Alternative: Dispersion-dominated bulge model gives poorer fits than the thin disk model, so the thin disk is used for the remainder of the paper  
  > "In general, the dispersion-dominated bulge model provides a poorer fit to the data than the thin disk model." (Results: Kinematic Modeling Results)
- Alternative: Moment (M1/M2) maps rejected in favour of per-spaxel Gaussian fits  
  > "we opt to use this method for estimating the velocity and velocity dispersion fields for all quasar host galaxies in our sample." (Two Methods for Deriving Mean Velocity and Velocity Dispersion Fields)
- How they decided it was enough: Two MCMC ensembles compared with each other for convergence; residual KS and reduced chi-squared checks of the model  
  > "To check for the convergence of the ensemble, we compare the ensemble both with itself and with the other ensemble." (Section 3.2 qubefit)
- Limitation (authors): Model uncertainties are not included in the Bayesian parameter uncertainties  
  > "Systematic uncertainties from the choice of the model are not included in these uncertainty estimates." (Fitting Caveats)
- Limitation (authors): Higher resolution and/or more sensitive observations could reveal more complex [CII] kinematics than these simple models  
  > "Higher resolution and/or more sensitive observations could" (Fitting Caveats)
- Limitation (authors): Dynamical mass estimates for disturbed galaxies are not very reliable due to non-gravitationally supported motions  
  > "we caution that the estimates for galaxies in the disturbed sample are not very reliable due to non-gravitationally supported motions" (Summary and Concluding Remarks)
- Caveat (inferred, ours): Gravitationally supported thin-disk or bulge assumption is applied even to merging systems, biasing their dynamical masses.
- Caveat (inferred, ours): Beam approximated as 2D Gaussian and the f_beam correction is an approximation to the covariance structure of the data.
- Caveat (inferred, ours): Ordered-rotation estimate depends on inclination, which is poorly constrained for barely resolved sources.
- Caveat (inferred, ours): Eta and disk-potential systematics are large; the quoted systematics are asymmetric and partly chosen by the authors.
- Caveat (inferred, ours): The 2.4 sigma tension depends on the dynamical mass being equal to the bulge mass and on the Kormendy2013 relation.
- Caveat (inferred, ours): Molecular gas lower limit depends on the dust opacity, T_d and the [CII] conversion, with the [CII] conversion judged invalid by the authors themselves.
- Caveat (inferred, ours): Only 13 undisturbed galaxies enter the radial profiles; the mean values depend on the sample split.
- Caveat (inferred, ours): Alpha_CII and dust-to-gas values are taken from other papers rather than fit here.
- Caveat (inferred, ours): Table 4 SMBH masses rely on a mix of Mg II, C IV and Eddington-based estimates.
- Caveat (inferred, ours): Project code 2015.1.00339.S printed in the Acknowledgments differs from the archive-linked code 2015.1.00399.S in the manifest.

## Reproducibility

- Data public (paper): Not stated whether the cubes are public; ALMA project codes are listed in the Acknowledgments  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA" (Acknowledgments)
- Products in archive: _not stated_
- Code: qubefit is publicly available as a Python code on GitHub  
  > "We have used our publicly available python-based fitting code, `qubefit`, to fit the kinematics" (Summary and Concluding Remarks); "https://github.com/mneeleman/qubefit" (qubefit section)
- Missing: Calibrated and cleaned cube products and the data reduction (defer to Venemans2020)
- Missing: Cleaning/imaging parameters and the continuum flux densities used for the dust masses
- Missing: Line-free channels, continuum subtraction and the velocity window per source
- Missing: Per-source prior bounds, walker numbers and step counts for emcee
- Missing: Beam fit parameters and fitting-region definitions used in qubefit
- Missing: Moment-map clipping thresholds used for comparison fields
- Missing: SMBH mass recipes and sources for all 27 objects (Schindler2020 and others)
- Data volume (inferred): not stated; inferred to be tens of GB for 27 cleaned [CII] cubes with 30 MHz channels (low confidence)
- Score (inferred): 5/5, Full kinematic recipe, models and most numeric results are described, but reduction and imaging settings are deferred to a companion paper, and several key inputs (continuum fluxes, priors, cube products) are missing.
- Rediscovery candidate: no, Public status of the data is not stated, the imaging and reduction recipe is incomplete, and the reduction is deferred to Venemans2020.

## Links

- Method: (cite: Venemans2020) (Observations and data reduction for the 27-quasar cubes)
- Method: (cite: ForemanMackey2013) (emcee MCMC sampler used for fitting)
- Method: (cite: Deblok2008) (Comparison of velocity field methods)
- Method: (cite: Burkert2010) (eta prescription for turbulent disk circular velocity)
- Method: (cite: Zanella2018) ([CII]-to-molecular gas conversion)
- Method: (cite: Venemans2016) (Dust-continuum molecular mass method)
- Companion: (cite: Venemans2020) (Observations, reduction and continuum-vs-[CII] comparison for the same sample)
- Companion: (cite: Novak2020) (Spatial and spectral extent of [CII] for the same sample)
- Companion: (cite: Neeleman2019) (Thin disk model summary and earlier kinematic analysis)
- Related: Three-paper series on the 27-quasar sample, with Venemans2020 and Novak2020 as companions

## Checks

```json
{
 "quotes": 132,
 "quotes_ok": 131,
 "quote_pass_rate": 0.992,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 10,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2015.1.00339.S"
 ],
 "obscore_codes_not_in_card": [
  "2015.1.00399.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 14,
 "numeric_problems": 0,
 "fill": {
  "facts": 124,
  "stated": 88,
  "rate": 0.71
 },
 "evidence_ok": false
}
```

## Figures

- **Figure 1** (moment_map, 18 panel(s), data): Flux density (channel at the [CII] line centre), mean velocity and velocity dispersion maps for the 18 undisturbed quasar host galaxies, with 0.5 arcsec scale bars and synthesized beams.
  - axes: colour (flux density): [CII] flux density in units of sigma (-3 to 9 sigma) [sigma]; colour (mean velocity): mean velocity [km s-1]; colour (velocity dispersion): velocity dispersion [km s-1]; contours: flux density contours [sigma]
  - supports step 3
  - read off the plot: approx. mean velocity colour scale spans -150 to +150 km s-1; approx. velocity dispersion colour scale spans 0 to 250 km s-1
  - reproduction target
- **Figure 2** (moment_map, 11 panel(s), data): Flux density, mean velocity and velocity dispersion maps for the quasars with complex [CII] structures indicative of mergers or close companions.
  - axes: colour (flux density): [CII] flux density in units of sigma [sigma]; colour (mean velocity): mean velocity [km s-1]; colour (velocity dispersion): velocity dispersion [km s-1]; contours: flux density contours [sigma]
  - supports step 3
  - read off the plot: approx. mean velocity colour scale spans -150 to +150 km s-1; approx. velocity dispersion colour scale spans 0 to 250 km s-1
- **Figure 3** (other, 16 panel(s), data, model): Velocity (rotational) and velocity dispersion profiles versus distance from the kinematic centre for eight galaxies with extended emission and clear velocity gradients, comparing data with the constant-velocity kinematic model.
  - axes: x: distance from kinematic centre [arcsec]; y: velocity [km s-1]; y: velocity dispersion [km s-1]
  - supports step 4
  - validation: Checks whether the constant rotational velocity and constant dispersion model agrees with the data radial profiles at the given beam resolution.
  - read off the plot: approx. J025-33 rotation plateau about 140 km s-1; approx. J025-33 central dispersion about 135 km s-1 in data; approx. J1048-0109 model velocity about 240 km s-1
- **Figure 4** (other, 13 panel(s), data, model): Same velocity and dispersion profile comparison as Figure 3 for five galaxies extended over more than two beams but without coherent rotation.
  - axes: x: distance from kinematic center [arcsec]; y: velocity [km s-1]; y: velocity dispersion [km s-1]
  - supports step 4
  - validation: Checks that without rotation the model and data both show a flat, constant dispersion profile consistent with beam smearing being negligible.
  - read off the plot: approx. J0100+2802 dispersion about 175 km s-1 model; approx. P231-20 dispersion about 115 km s-1 model
- **Figure 5** (scatter_or_relation, 2 panel(s), data, literature_comparison): Redshift evolution of the velocity dispersion (left) and of the ratio of rotation velocity to dispersion vrot/sigma (right) for the z>=6 quasar hosts compared with low-redshift star-forming galaxies.
  - axes: x: redshift [dimensionless]; y (left): log velocity dispersion [km s-1]; y (right): log vrot/sigma [dimensionless]
  - supports step 4
  - validation: Compares the z>=6 sample against low-redshift massive galaxies and an extrapolation of their trend.
  - read off the plot: approx. undisturbed average log dispersion about 2.1 at z approx. 6.3; approx. extrapolation intercept log sigma about 1.6 at z=0
  - reproduction target
- **Figure 6** (scatter_or_relation, 3 panel(s), data, model): Dynamical mass plotted against FWHM squared, FWHM squared times radius, and (FWHM/sin i) squared times radius, showing the correlation strength improving across the three observables.
  - axes: x: log FWHM^2, log FWHM^2 R, log (FWHM/sin i)^2 R [not labelled]; y: dynamical mass [log M_sun]; colour/marker: morphology class [not labelled]
  - supports step 6
  - validation: Tests which low-resolution observable best recovers the dynamical mass, with Pearson correlation coefficients 0.03, 0.40 and 0.64.
  - read off the plot: approx. R_cor 0.03 for log FWHM^2 panel; approx. R_cor 0.40 for FWHM^2 R panel; approx. R_cor 0.64 for (FWHM/sin i)^2 R panel; approx. best-fit dynamical mass log 10.5 to 11.0 for the undisturbed sample
  - reproduction target
- **Figure 7** (scatter_or_relation, 1 panel(s), data, literature_comparison): Black hole mass versus dynamical (galaxy) mass for the z>=6 quasars compared with local galaxies and the local black hole-bulge mass relation.
  - axes: x: galaxy mass [log M_sun]; y: SMBH mass [log M_sun]; marker: morphology class [not labelled]
  - supports step 8
  - validation: Compares the high-redshift black hole to host mass ratio with the locally derived correlation, showing the quasars lie above it.
  - read off the plot: approx. undisturbed SMBH masses about log 9.0 to 10.0 M_sun; approx. local relation spans log SMBH 6 to 10 over galaxy mass 9 to 12.5
  - reproduction target
- **Figure 8** (scatter_or_relation, 2 panel(s), data): Molecular gas mass estimates from dust continuum (left) and from the [CII] luminosity scaling of Zanella et al. 2018 (right), each compared with the dynamical mass.
  - axes: x: dynamical mass [log M_sun]; y (left): gas mass from continuum [log M_sun]; y (right): gas mass from [CII] [log M_sun]
  - supports step 7
  - validation: Checks the physical consistency of the molecular gas mass estimates against the dynamical mass upper bound.
  - read off the plot: approx. continuum gas masses about log 9.4 to 10.8 M_sun; approx. [CII]-based gas masses about log 10.4 to 11.5 M_sun
- **Figure 9** (channel_maps, 24 panel(s), data): Channel maps of the [CII] emission line of P183+05 across velocities from +403 to -406 km s-1 relative to the line redshift, centred on the quasar position.
  - axes: x: Delta R.A. [arcsec]; y: Delta Decl. [arcsec]; colour: flux density [mJy beam-1]; contours: flux density contours [sigma]
  - supports step 1
  - read off the plot: approx. peak flux density 3.5 mJy beam-1 in colour scale maximum; approx. emission visible between about +157 and -160 km s-1
- **Figure 10** (corner_plot, 49 panel(s), model, residual): Posterior corner plot of the thin disk kinematic model fit to P183+05, with parameter PDFs and the cumulative flux distribution of data and residual compared with Gaussian noise.
  - axes: parameters: RA, Dec, redshift, position angle, inclination, V_rot, sigma_v, I0, R_D [deg, arcsec, km s-1, mJy kpc-2, kpc]; inset x: flux RMS [sigma]; inset y: cumulative distribution [dimensionless]
  - supports step 1
  - validation: Checks that the residual flux distribution matches Gaussian noise (KS probability 0.741, reduced chi-square 1.175), indicating a good fit.
  - read off the plot: approx. position angle 260.2 deg; approx. sigma_v 140 km s-1; approx. disk scale radius 1.15 kpc; approx. inclination below 22 deg; approx. KS probability 0.741
- **Figure 11** (model_vs_data, 9 panel(s), data, model, residual): Comparison of the flux density, mean velocity and velocity dispersion for P183+05 between the data, the best-fit thin disk model and the residual.
  - axes: x: Delta R.A. [arcsec]; y: Delta Decl. [arcsec]; colour (flux density): flux density [mJy beam-1]; colour (mean velocity): mean velocity [km s-1]; colour (dispersion): velocity dispersion [km s-1]
  - supports step 2
  - validation: Compares data, model and residual maps for flux, velocity and dispersion to assess goodness of fit of the thin disk model.
  - read off the plot: approx. peak flux density 1.05 mJy beam-1 in data; approx. velocity range -175 to +175 km s-1 in data and model; approx. dispersion model about 140 km s-1
- **Figure 12** (residual_map, 24 panel(s), residual): Channel maps of the residual [CII] emission for P183+05 after subtracting the best-fit thin disk model convolved with the beam, using the same annotations and contours as Figure 9.
  - axes: x: Delta R.A. [arcsec]; y: Delta Decl. [arcsec]; colour: residual flux density [mJy beam-1]
  - supports step 2
  - validation: Checks that the residual channel maps contain no coherent emission left after the model is subtracted, i.e. only noise.
  - read off the plot: approx. residual colour range -0.6 to 3.5 mJy beam-1
- **Figure 13** (moment_map, 10 panel(s), data): Velocity and velocity dispersion fields of P183+05 for five clipping thresholds, from no clipping to 3-sigma clipping, showing how clipping affects the fields.
  - axes: x: Delta R.A. [kpc]; y: Delta Decl. [kpc]; colour (velocity): mean velocity [km s-1]; colour (dispersion): velocity dispersion [km s-1]; contours: total [CII] intensity [not labelled]
  - supports step 3
  - validation: Tests the sensitivity of the velocity dispersion field to the cube clipping threshold, showing artificial edge decrease at 2-sigma and above.
  - read off the plot: approx. spatial extent about 4 kpc radius
- **Figure 14** (moment_map, 4 panel(s), data): Comparison of velocity and dispersion fields of P183+05 from single-Gaussian fits per spaxel (top) and from the first and second moments of the clipped cube (bottom).
  - axes: x: Delta R.A. [kpc]; y: Delta Decl. [kpc]; colour (velocity): mean velocity [km s-1]; colour (dispersion): velocity dispersion [km s-1]
  - supports step 3
  - validation: Checks that the Gaussian-fit and moment-based velocity and dispersion fields agree, supporting the choice of Gaussian fitting.
  - read off the plot: approx. velocity range -175 to +175 km s-1; approx. dispersion typically 100 km s-1 at centre
