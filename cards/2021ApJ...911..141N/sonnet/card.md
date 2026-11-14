# The Kinematics of z ≳ 6 Quasar Host Galaxies

`2021ApJ...911..141N` | The Astrophysical Journal 2021 | first author: Neeleman, Marcel | arXiv: 2102.05679 | DOI: 10.3847/1538-4357/abe70f | **HELD OUT (benchmark)**

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: What are the [C II] kinematics, dynamical masses and gas mass fractions of z ≳ 6 quasar host galaxies, and how do they compare with the local bulge mass–black hole mass relation?  
  > "Comparison between the dynamical mass and the mass of the supermassive black hole reveals that the sample falls above the locally derived bulge mass–black hole mass relation at 2.4$\sigma$ significance." (abstract)
- Target **27 z ≳ 6 quasar host galaxies (e.g. P183+05, J1342+0928)**: coordinates Per-source kinematic centres in Table 1, e.g. P183+05 12:12:26.9754 +05:05:33.566 (ICRS)  
  > "P183+05 | 12:12:26.9754(4) | $+$05:05:33.566(5) | 6.43855(10)" (Table 1); z/distance z_kin 5.78 to 7.54 (Table 1)  
  > "P183+05 | 12:12:26.9754(4) | $+$05:05:33.566(5) | 6.43855(10)" (Table 1); distance from [C II] redshift from kinematic modelling; agrees with Venemans2020  
  > "P183+05 | 12:12:26.9754(4) | $+$05:05:33.566(5) | 6.43855(10)" (Table 1)

## Data provenance

- ALMA projects: 2017.1.01301.S, 2018.1.00908.S, 2012.1.00240.S, 2012.1.00882.S, 2013.1.00273.S, 2015.1.00339.S, 2015.1.00692.S, 2016.A.00018.S, 2016.1.00544.S, 2017.1.00396.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.10'' to 0.25''  
  > "The observations range in resolution between $0.10\ensuremath{''}$ and $0.25\ensuremath{''}$" (2 Sample Selection)
- max recoverable scale: _not stated_
- sensitivity: 0.13–0.54 mJy/beam per 30 MHz channel, mean 0.27  
  > "have root mean square (RMS) sensitivities between 0.13 and 0.54 mJy beam$^{-1}$, with an average of 0.27 mJy beam$^{-1}$, per 30 MHz channel" (2 Sample Selection)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Own team programs plus archival data at the same resolution  
  > "We supplement this data with previous data obtained by our team, as well as archival data at the same resolution." (2 Sample Selection)
- Line: [C II] 158 μm fine-structure (not stated)
- External data: [C II] FWHM, line redshifts and continuum fluxes for the sample  
  > "The second column lists the FWHM of the total \[C II\] emission as reported in (cite: Venemans2020)." (4.4.1) [from (cite: Venemans2020)]
- External data: SMBH masses from NIR spectra (Mg II, C IV, Eddington)  
  > "Nearly all of the SMBH mass estimates are taken from a recent study analyzing NIR spectra from a large sample of $z \gtrsim 6$ quasars (cite: Schindler2020)" (5.4) [from (cite: Schindler2020); (cite: Mazzucchelli2017); (cite: Onoue2020)]
- External data: Local bulge mass–black hole mass relation  
  > "we compare these measurements with the relationship between bulge mass and black hole mass for local galaxies (cite: Kormendy2013; DeNicola2019)" (5.4) [from (cite: Kormendy2013; DeNicola2019)]
- External data: Lower-redshift velocity dispersions and v_rot/sigma  
  > "velocity dispersion measurements for both individual galaxies (cite: Livermore2015; Turner2017; FoersterSchreiber2018) and sample averages (cite: Turner2017)" (5.1) [from (cite: Livermore2015; Turner2017; FoersterSchreiber2018)]

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
- smoothing: 30 MHz channel width, cleaned cubes  
  > "the channel spacing of 30 MHz is much larger than the line-spread function of ALMA, which is 1 MHz" (3.2 qubefit)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Observations and data reduction (calibration, imaging, cubes)  
  > "Details of the observations and data reduction procedure for the data used in this paper are given in (cite: Venemans2020)" (1 Introduction) [from (cite: Venemans2020)]
- Thin disk model description  
  > "has been previously summarized in Appendix C of (cite: Neeleman2019)" (3.3.1) [from (cite: Neeleman2019)]
- Dust-mass-based gas mass method  
  > "we convert the dust continuum flux measurement into a dust mass assuming the method described in detail in (cite: Venemans2016)" (5.5) [from (cite: Venemans2016)]
- [C II]-to-molecular mass conversion alpha_[CII]=31 Lsun/Msun  
  > "assuming the conversion given in (cite: Zanella2018) with $\alpha_{\rm [CII]} = 31~L_\odot/M_\odot$" (5.5) [from (cite: Zanella2018)]

### Not stated but needed to reproduce (our reading)

- Imaging details (robust, tclean parameters, CASA version, continuum subtraction) deferred to Venemans2020
- Exact cube cutout size and mask per source
- MCMC chain length, walker numbers and convergence criteria besides P183+05 example
- Initial parameter values for first chain
- Flux calibration uncertainty
- Continuum flux values used for dust mass

## Analysis recipe

1. **Fit 3D kinematic models to [C II] cubes**: qubefit forward-models thin disk (9 params) and dispersion-dominated bulge (6 params) cubes, convolved with beam, compared with cleaned cube in 3σ-based mask  
  > "calculate the best-fit parameters and associated uncertainties for these models using a Markov Chain Monte Carlo (MCMC) approach" (3.2 qubefit)
   - software: qubefit, emcee
   - parameter: Modified chi2: ln L = -0.5 f_beam sum (M-D)^2/R^2, f_beam = pi/(A_beam ln2)  
  > "the adjustment factor is $f_{\rm beam} =  \pi / (A_{\rm beam}\ln2)$" (3.2 qubefit)
   - parameter: Mask: pixels ≥3σ plus buffer of one independent measurement  
  > "generated from all pixels with at least a 3$\sigma$-significant signal, which is then expanded to contain a buffer of at least one independent measurement" (3.2 qubefit)
   - assumption: Exponential emission profile, constant v_rot and sigma_v, gas gravitationally supported  
  > "The emission of the disk is assumed to be axisymmetric and exponentially decreasing with distance from the center." (3.3.1)
   - fitting: emcee affine-invariant sampler, flat priors, two independent ensembles, 30% burn-in removed, medians and 16–84th percentiles  
  > "We assume flat, uninformed priors on all of the parameters, and run two independent ensembles using different initial values." (3.2 qubefit)
   - validation: Reduced chi2 and one-sample KS probability on independent pixels (one per beam)  
  > "we calculate two goodness-of-fit statistics: a simple reduced-$\chi^2$ statistic and a one-sample Kolmogorov-Smirnov (KS) probability." (3.4 Goodness of Fit)
2. **Build velocity and dispersion fields and radial profiles**: Single Gaussian fit per spaxel (astropy) for velocity/dispersion maps; invert line-of-sight equation for v_rot; compare with beam-convolved constant-velocity model  
  > "we use the fitting routines in `astropy` (cite: Astropy2013; Astropy2018) to fit a single Gaussian to the spectrum of each individual spaxel." (9 Two Methods)
   - software: astropy, qubefit
   - parameter: Measurements within 30 deg of minor axis removed  
  > "We remove measurements within 30$\ensuremath{^\circ}$ of the minor axis" (4.3)
   - fitting: _not stated_
   - validation: Beam smearing tested with constant-velocity model  
  > "we apply the same method to the model cube with constant velocity which has been convolved with the beam." (4.3)
3. **Compute dynamical masses**: M_dyn = v_circ^2 R / G at 2R_e, with v_circ = sqrt(v_rot^2 + eta sigma_v^2), eta=3.4, R_e=1.678 R_D  
  > "resulting in $\eta = 3.4$. We will take this value as our fiducial value" (4.4.1)
   - parameter: Radius 2R_e  
  > "Lower redshift studies often use $2R_{\rm e}$ as the radius to calculate the dynamical mass" (4.4.2)
   - assumption: Spherical mass distribution; systematic uncertainties added: 20% disk geometry, 40% eta, 40% double-exponential R_e, 50% lower-bound for [C II] tracer  
  > "we therefore conservatively increase the dynamical mass uncertainty by 20 % toward lower masses" (4.4)
   - fitting: _not stated_
   - validation: Compared with FWHM-based estimators  
  > "This circular velocity estimate in most cases is bracketed by the other two methods" (4.4.1)
4. **Derive gas masses and compare to SMBH mass**: Dust-continuum gas mass and [C II]-based gas mass; dynamical mass vs SMBH mass compared with Kormendy2013 relation  
  > "we assume a dust temperature of T$_{\rm d}$ = 47 K, an emissivity index of $\beta$ = 1.6" (5.5)
   - parameter: Dust-to-gas 100, molecular fraction 0.75, Td 30–60 K, beta 1.4–1.8 for uncertainties, 0.3 dex on alpha_[CII]  
  > "Dust masses are converted into molecular masses assuming a dust-to-gas ratio of 100 and a molecular-to-total gas mass fraction of 0.75." (5.5)
   - assumption: kappa = 0.77 (850um/lambda)^beta cm2/g; flat LCDM H0=70, Omega_lambda=0.7  
  > "a dust mass opacity coefficient of $\kappa_\lambda = 0.77 (850 \mu{\rm m}/\lambda)^\beta$ cm$^2$ g$^{-1}$ (cite: Dunne2000)" (5.5)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **qubefit** : 3D kinematic fitting and velocity-field routines  
  > "The kinematic modeling was performed with the custom python code, `qubefit`." (3 Methods)
- **emcee** : MCMC sampling  
  > "we use the affine-invariant MCMC ensemble sampler, `emcee`, to sample the multidimensional parameter space" (3.2 qubefit)
- **astropy** : Gaussian fits for velocity fields  
  > "we use the fitting routines in `astropy`" (9 Two Methods)
- **scipy** : KS statistic  
  > "using standard recipes within `scipy`" (3.4 Goodness of Fit)
- **CASA** : Listed in software section; data reduction  
  > "CASA (cite: McMullin2007)" (Software)
- **corner** : Corner plots of PDFs  
  > "Corner (cite: ForemanMackey2016)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mean velocity dispersion (undisturbed sample) | 129 | 10 | km/s | 1 | The mean velocity dispersion for the undisturbed sample is $129 \pm 10$ km s$^{-1}$. |
| Mean dynamical mass within 2R_e (undisturbed) | 5.0 | ±0.8 (±3.5 systematic) | 1e10 Msun | 3 | with a mean mass of $5.0 \pm 0.8\,(\pm 3.5) \times 10^{10} M_\odot$ |
| Mean effective radius (undisturbed) | 1.11 | 0.11 | kpc | 3 | The mean effective radius for the undisturbed sample is $1.11 \pm 0.11$ kpc. |
| Mean inclination (undisturbed) | 33 | 5 | deg | 1 | This inclination is on average $33 \pm 5 \ensuremath{^\circ}$ for those quasars in the undisturbed subsample. |
| Mean SMBH mass | 2.2 | 0.5 | 1e9 Msun | 0 | The sample has a mean SMBH mass of $2.2 \pm 0.5$ $\times 10^{9} M_\odot$. |
| Deviation from local Mbulge-MBH relation | 2.4 | not stated | sigma | 4 | smaller by about a factor of seven, which is a 2.4$\sigma$ deviation from the local correlation |
| Dispersion for no-gradient vs gradient galaxies | 153 vs 95 | 32 and 25 | km/s | 1 | $153 \pm 32$ compared to $95 \pm 25$ km s$^{-1}$ |
| Median molecular-to-dynamical mass ratio (dust continuum) | 0.3 | not stated | dimensionless | 4 | we find a molecular-to-dynamical mass ratio of 0.3 |

## Qualitative findings

- Nine of 27 hosts are disturbed, ten show smooth velocity gradients, eight show no gradient  
  > "We find that nine of the galaxies show disturbed \[C II\] emission, either due to a close companion galaxy or recent merger." (abstract)
- Resolution is insufficient to measure rotation curve shape; beam smearing explains rising profiles  
  > "The resolution of these observations is therefore insufficient to measure the shape of the rotation curve" (4.3)

## Claim tuples

- H: Do z≳6 quasar hosts show a single kinematic class? | E: Thin disk fits and velocity fields for 27 hosts | R: 9 disturbed, 10 with gradients, 8 without | F: Varied kinematics suggest no single trigger for quasar phase | **partially**
- H: Quasar hosts are less massive than implied by local Mbulge-MBH | E: Compare M_dyn with MBH against Kormendy2013 | R: Offset factor ~7, 2.4σ | F: Hosts fall above local relation, robust to systematics | **supported**
- H: Gas makes up a large fraction of the mass | E: Compare dust- and [C II]-based molecular masses with M_dyn | R: Ratio 0.3 (dust), 1.7 ([C II]) | F: Molecular gas >10% of dynamical mass | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Full 3D forward-modelling accounts for finite resolution and allows non-disk models  
  > "to allow for maximum flexibility in emission models, we have designed the Python-based code `qubefit`" (3.2 qubefit)
- Alternative: Moment maps rejected in favour of Gaussian fits because of clipping dependence  
  > "We show that the latter method is more robust for the moderate resolution and S/N observations discussed here." (4.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Models are simplified; systematic model uncertainties not in errors  
  > "Systematic uncertainties from the choice of the model are not included in these uncertainty estimates." (3.5 Fitting Caveats)
- Caveat (inferred, ours): Dynamical mass vs bulge mass equivalence is assumed; stellar mass could differ by ~0.4 dex
- Caveat (inferred, ours): Many hosts barely resolved so inclination poorly constrained
- Caveat (inferred, ours): Single-exponential profile may underestimate R_e
- Caveat (inferred, ours): Gas-mass estimates depend on assumed Td, beta, dust-to-gas ratio

## Reproducibility

- Data public (paper): Programs listed in acknowledgments; qubefit is public on GitHub  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA $\#$2012.1.00240.S" (Acknowledgments)
- Products in archive: _not stated_
- Code: qubefit at github.com/mneeleman/qubefit  
  > "https://github.com/mneeleman/qubefit" (Footnote 1)
- Missing: Calibrated/imaged cubes (from Venemans2020 processing)
- Missing: Per-source cutout and mask settings
- Missing: SMBH masses from Schindler2020 (submitted)
- Data volume (inferred): Large: ~10 ALMA projects, 27 sources, tens to hundreds of GB raw
- Score (inferred): 3/5, Fitting method, equations and tables are detailed and code is public, but imaging is deferred to companion paper and data span many projects.
- Rediscovery candidate: no, Requires imaging recipe from Venemans2020 and many archival datasets; recipe incomplete here.

## Links

- Method: (cite: Venemans2020) (Observations and data reduction)
- Method: (cite: Neeleman2019) (Thin disk model)
- Companion: (cite: Novak2020) ([C II] spatial and spectral extent of the same sample)

## Checks

```json
{
 "quotes": 68,
 "quotes_ok": 68,
 "quote_pass_rate": 1.0,
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
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 45,
  "rate": 0.549
 },
 "evidence_ok": true
}
```
