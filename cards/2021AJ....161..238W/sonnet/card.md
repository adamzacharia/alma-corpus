# The Anatomy of an Unusual Edge-on Protoplanetary Disk. I. Dust Settling in a Cold Disk

`2021AJ....161..238W` | The Astronomical Journal 2021 | first author: Wolff, Schuyler G. | arXiv: 2103.02665 | DOI: 10.3847/1538-3881/abeb1d

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: What are the geometry, dust properties and degree of dust settling of the edge-on disk Oph163131, from joint radiative transfer modeling of HST scattered light and ALMA 1.3 mm continuum?  
  > "We model the 0.8 $\mu$m and 1.3 mm images in separate MCMC runs to investigate the geometry and dust properties of the disk using the MCFOST radiative transfer code." (abstract)
- Target **Oph163131 (2MASS J16313124-2426281)**: coordinates _not stated_; z/distance 147 pc  
  > "We adopt a distance of 147 pc for this source." (1 Introduction); "Oph163131 sits closest to the Eastern streamer of Ophiuchus (L1689) for which the authors provide a distance of $147.3 \pm 3.4 \, pc$." (1 Introduction); distance from Ortiz-Leon et al. 2017 VLBA parallax of L1689 (cite: 2017ApJ...834..141O)  
  > "We adopt a distance of 147 pc for this source." (1 Introduction); "Oph163131 sits closest to the Eastern streamer of Ophiuchus (L1689) for which the authors provide a distance of $147.3 \pm 3.4 \, pc$." (1 Introduction)

## Data provenance

- ALMA projects: 2016.1.00771.S
- bands: Band 6 (1.3 mm)  
  > "We obtained ALMA band 6 continuum data (1.3 mm)" (2.3 ALMA Continuum Map)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: beam 0.23'' x 0.13''  
  > "The ALMA continuum map (beam size of 0.23$''$ x 0.13$''$)" (2.3 ALMA Continuum Map)
- max recoverable scale: _not stated_
- sensitivity: rms 0.134 mJy  
  > "with a 3$\sigma$ cut (with an rms of 0.134 mJy)" (2.3 ALMA Continuum Map)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: PI Duchêne  
  > "(Project 2016.1.00771.S, PI: Duchêne)" (2.3 ALMA Continuum Map)
- Other facility **HST ACS/WFC3**: Scattered light images in F475W, F606W, F814W  
  > "Scattered light images of the Oph163131 disk were obtained using HST ACS in both the F814W and F606W broadband filters on March 4th, 2012" (2.1 HST Scattered Light Images)
- Other facility **Keck NIRC2**: 2.2 micron AO image (not modeled)  
  > "we obtained a $K'$ ($2.124 \, \mu m$) image of Oph163131 with the NIRC2 instrument" (2.2 Keck Image)
- Other facility **CARMA**: 2.6 mm continuum upper limit for SED  
  > "Oph163131 was observed in the 2.6 mm continuum with the Combined Array for Research in Millimeter Astronomy (CARMA) under project cf0024" (2.4 CARMA Detection)
- External data: Literature SED photometry (Table 3) incl. ALMA Band 7 flux 124.8 ± 2.4 mJy  
  > "They reported an integrated flux of 124.8 $\pm$ 2.4 mJy which is included in the SED shown in Appendix [7]" (2.3 ALMA Continuum Map) [from Cox et al. 2017 (cite: 2017ApJ...851...83C) and others in Table 3]
- External data: Ophiuchus K3.5-K5.5 star catalogue used for Teff 4500 K and L 0.96 Lsun  
  > "derive average values of 4500 K and 0.96 $L_{\odot}$ for the temperature and luminosity" (3.1 Stellar Properties) [from (cite: 2005AJ....130.1733W; 2011AJ....142..140E)]

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

- ALMA continuum data reduction and results  
  > "A full description of the ALMA continuum data reduction processes and results is presented in (cite: 2020arXiv200806518V)" (2.3 ALMA Continuum Map) [from Villenave et al. 2020 (cite: 2020arXiv200806518V)]
- Covariance-based likelihood framework for 2D disk images  
  > "In (cite: 2017ApJ...851...56W) we detail how to expand this to 2D disk observations" (3.3) [from Wolff et al. 2017 (cite: 2017ApJ...851...56W)]
- Dust settling prescription  
  > "We use the (cite: 2009A&A...496..597F) prescription for settling" (3.2 MCFOST Disk Model) [from Fromang & Nelson 2009]
- Stellar spectral type and dynamical mass from Paper II  
  > "In Paper II, we report mid-resolution optical and IR spectroscopy for Oph163131 and compare to template spectral libraries to arrive at a spectral type of K4-5" (3.1 Stellar Properties) [from Flores et al. in prep (Paper II)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration details, CASA version, robust weighting and imaging parameters (deferred to Villenave et al. 2020)
- Aperture used for photometry
- Stellar parameters fixed in MCFOST beyond Teff/L (mass, spectral inputs)
- Gas-to-dust ratio
- Dust-to-model flux normalisation details and mask definitions
- Amplitude of global covariance and exact analytic autocorrelation function form
- Downsampling procedure for ALMA to HST resolution
- Fixed minimum/maximum grain parameters beyond stated

## Analysis recipe

1. **Measure ALMA continuum flux and geometry**: Aperture photometry in CASA with 3 sigma cut; imfit for comparison; profiles along major/minor axes  
  > "we perform aperture photometry in the CASA software package with a 3$\sigma$ cut (with an rms of 0.134 mJy)" (2.3 ALMA Continuum Map)
   - software: CASA
   - assumption: 10% flux error  
  > "where we have assumed a conservative flux error of 10%" (2.3 ALMA Continuum Map)
   - fitting: _not stated_
   - validation: Compared with imfit integrated flux of ~47 mJy  
  > "this is consistent with the integrated flux value of $\sim 47$ mJy provided by the CASA imfit package" (2.3 ALMA Continuum Map)
2. **Individual MCMC fits to F814W and ALMA images**: MCFOST models convolved with Tiny Tim PSF or ALMA Gaussian beam, normalised to observed flux, recentred, chi-square log-likelihood on pixels >3 sigma  
  > "we first generate a synthetic image with MCFOST at the specified wavelength, convolve this model with an instrumental PSF, normalize the model to the sum of the observed disk signal" (3.3)
   - software: MCFOST, emcee, mcfost-python, Tiny Tim
   - parameter: parallel-tempered, 2 temperatures, 50 walkers; 2000 iterations (F814W), 1000 (ALMA); burn-in 100  
  > "For both initial runs we use a parallel-tempered sampler with 2 temperatures and 50 walkers." (3.3)
   - parameter: Free: i, H0, dust mass, gamma, beta, p, alpha, Rc; fixed distance 147 pc, Rin 1 au, Rout 191 au  
  > "The disk is assumed to be at a distance of 147 pc with an inner radius fixed at 1 au and an outer radius of 191 au." (3.2 MCFOST Disk Model)
   - assumption: Single species amorphous olivine, non-porous grains, a = 0.03-1000 micron, 70 log bins  
  > "with a particle size distribution described by a power law extending from $a$ = 0.03 - 1000 $\mu$m in size" (3.2 MCFOST Disk Model)
   - fitting: Uniform priors except uniform in cos i and log-uniform for dust mass and alpha; ranges in Table 2  
  > "We use uniform priors for all parameters except for the inclination (uniform in $\cos{i}$), and the dust mass and viscosity parameter where log-uniform priors are used." (3.3)
   - validation: Effective sample size from integrated autocorrelation time  
  > "We compute an effective sample size (ESS) for each parameter to test the convergence of the chain." (4.1 Scattered Light Image)
3. **Joint covariance-based MCMC**: Gaussian likelihood with covariance C = diag noise + global covariance from residual autocorrelation of 1000 models from individual runs; ALMA downsampled to HST resolution; p fixed at 3.5  
  > "We generate an autocorrelation map by selecting 1000 models drawn from the MCMC chain, computing the observation - model residuals, and autocorrelating those residuals." (3.3)
   - software: emcee, MCFOST, mcfost-python
   - parameter: 2 temperatures, 50 walkers, 2000 iterations, burn-in 250; covariance cutoff at 8 pixels  
  > "with a cutoff outside of 8 pixels to make computations of $C_{i,j}$ tractable" (3.3)
   - fitting: Same priors as individual fits with p fixed  
  > "For the combined MCMC run we keep this value fixed at 3.5 to further limit parameter degeneracies." (3.3)
   - validation: ESS test; only inclination and gamma unconstrained (ESS 8 and 20)  
  > "only the inclination and surface density exponent remain unconstrained with ESS values of 8 and 20, respectively" (4.3)
4. **Compare models with SED and Keck image; derive scale heights and Stokes numbers**: Compare representative models A, B, C to SED and 2.2 micron profiles; compute temperature-derived scale height and Stokes numbers  
  > "we compute the Stokes numbers for Models A, B and C following (cite: 2016SSRv..205...41B)" (5.3 Vertical Structure)
   - software: MCFOST
   - assumption: mu = 2.3; material density 1.8 g/cm3  
  > "we assume a reduced mass, $\mu$ of 2.3" (5.3 Vertical Structure)
   - fitting: _not stated_
   - validation: Cross-check with CO-derived temperature in Paper II  
  > "We find that the vertical extent of the gas matches the HST scattered light observations" (5.3 Vertical Structure)

## Software

- **MCFOST** : Radiative transfer disk models  
  > "The MCFOST radiative transfer code (cite: 2006A&A...459..797P; 2009A&A...498..967P) was used to construct synthetic SEDs" (3.2 MCFOST Disk Model)
- **emcee** : Parallel-tempered affine-invariant MCMC  
  > "we employ a parallel-tempered Monte Carlo Markov Chain approach using the `emcee` package" (3.3)
- **mcfost-python** : Interface to MCFOST, data parsing, goodness-of-fit  
  > "We couple this with the `mcfost-python` package developed by our team to interface with MCFOST" (3.3)
- **CASA** : Aperture photometry and imfit  
  > "we perform aperture photometry in the CASA software package" (2.3 ALMA Continuum Map)
- **Tiny Tim** : Simulated HST PSF  
  > "we use a simulated Tiny Tim PSF" (3.3)
- **DrizzlePac** : Re-drizzle ACS exposures  
  > "the MAST data products were re-drizzled using the DrizzlePac python package" (2.1 HST Scattered Light Images)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA 1.3 mm flux density | 44.8 | 4.5 | mJy | 1 | we find a flux density of 44.8 $\pm$ 4.5 mJy |
| Deconvolved major axis FWHM | 1.22 | 0.01 | arcsec | 1 | deconvolved disk major axis FWHM of 1.22 $\pm$ 0.01 arcsec |
| Inclination (ALMA-only posterior) | 87.31 | +0.31/-0.30 | deg | 2 | $87.31^{+0.31}_{-0.30}$ |
| Inclination (adopted) | ~87 | 1 | deg | 3 | we find an inclination of $\sim 87 \pm 1^{\circ}$ is most probable |
| Dust mass log M (ALMA-only) | -3.8 | +0.1/-0.1 | log Msun | 2 | $-3.8^{+0.1}_{-0.1}$ |
| mm scale heights at 100 au, Models A,B,C | 3.3, 4.2, 0.3 | not stated | au | 4 | $h_{1mm}$ = 3.3, 4.2, 0.3 au, respectively |
| Disk outer radius (HST) | 191 | 8 | au | 0 | arrive at a value of $191 \pm 8$ au |

## Qualitative findings

- Disk is flared but vertically thin; some dust settling is required to reconcile scattered light and mm datasets; midplane colder than expected.  
  > "some degree of dust settling is required to reproduce the vertically thin profile and lack of apparent flaring" (abstract)

## Claim tuples

- H: Can a single smooth tapered disk model fit both scattered light and ALMA continuum? | E: Separate chi-square and joint covariance MCMC runs with MCFOST | R: Individual fits good; joint fit gives worse fit and bimodal dust mass posterior | F: Model lacks complexity; more complex radial structure likely | **supported**
- H: Is dust settled in Oph163131? | E: Compare apparent vertical extent in scattered light and mm; alpha posterior | R: Low alpha values ruled out; mm scale heights smaller than 0.8 micron | F: Some degree of settling required | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Covariance likelihood to combine datasets with different noise and sensitivities without biasing the fit  
  > "to leverage the information inherent in both datasets without preferentially biasing the fit towards one image or the other" (3.3)
- Alternative: Keck image and other HST filters excluded from fitting  
  > "We chose not to include the Keck image in the modeling because of the image artifacts" (3.2 MCFOST Disk Model)
- How they decided it was enough: _not stated_
- Limitation (authors): Midplane thermal emission not vertically resolved; smooth tapered density model too simple  
  > "since the vertical height of the disk in the ALMA data is not resolved" (5.3)
- Caveat (inferred, ours): Model fits are degenerate; posteriors often hit prior edges
- Caveat (inferred, ours): Fitting image-plane CLEAN map rather than visibilities
- Caveat (inferred, ours): Joint fit has ESS of 8 for inclination
- Caveat (inferred, ours): Flux normalisation marginalised so absolute mass poorly constrained

## Reproducibility

- Data public (paper): mcfost-python code public on GitHub; ALMA project cited  
  > "The code is publicly available on Github." (3.3)
- Products in archive: _not stated_
- Code: mcfost-python at github.com/swolff9/mcfost-python  
  > "mcfost-python (https://github.com/swolff9/mcfost-python)" (Software)
- Missing: ALMA calibration/imaging details (in Villenave et al. 2020)
- Missing: MCFOST version and parameter files
- Missing: Covariance function analytic form
- Data volume (inferred): ~10-50 GB raw ALMA (single Band 6 continuum project) plus HST/Keck images
- Score (inferred): 3/5, Methods are described and code public, but ALMA reduction is deferred and MCFOST setup is only partly specified; compute-heavy (~4 months CPU).
- Rediscovery candidate: no, ALMA reduction is not given here and the modeling is very expensive and requires non-ALMA data.

## Links

- Method: Wolff et al. 2017 (cite: 2017ApJ...851...56W) (Covariance-based MCMC framework)
- Method: Pinte et al. 2006 (cite: 2006A&A...459..797P) (MCFOST)
- Companion: Villenave et al. 2020 (cite: 2020arXiv200806518V) (ALMA continuum reduction of edge-on disk sample)
- Companion: Flores et al. in prep (Paper II) (CO gas and temperature structure)
- Related: HST edge-on disk program GO 12514 and GO 13643

## Checks

```json
{
 "quotes": 57,
 "quotes_ok": 57,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 44,
  "rate": 0.55
 },
 "evidence_ok": true
}
```
