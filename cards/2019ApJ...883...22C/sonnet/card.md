# The Degree of Alignment between Circumbinary Disks and Their Binary Hosts

`2019ApJ...883...22C` | The Astrophysical Journal 2019 | first author: Czekala, Ian | arXiv: 1906.03269 | DOI: 10.3847/1538-4357/ab287b

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation, exoplanets
- Question: How well aligned are circumbinary disks with their host binaries, particularly for short-period double-lined spectroscopic binaries, and what does this imply for circumbinary planets?  
  > "We confirm this hypothesis using a hierarchical Bayesian analysis, showing that 68% of CB disks around short-period SB2s have $\theta < 3.0\ensuremath{^\circ}$." (abstract)
- Target **UZ Tau E (and UZ Tau W)**: coordinates _not stated_; z/distance 131.2 ± 1.7 pc  
  > "A *Gaia* DR2 parallax exists for UZ Tau E of $\pi=7.62\pm 0.10\,$mas (cite: lindegren18) or $131.2 \pm 1.7\,$pc (cite: gaia18; bailer-jones18)." (2.1 Background data on UZ Tau); distance from Gaia DR2 parallax (Lindegren et al. 2018; Bailer-Jones et al. 2018)  
  > "A *Gaia* DR2 parallax exists for UZ Tau E of $\pi=7.62\pm 0.10\,$mas (cite: lindegren18) or $131.2 \pm 1.7\,$pc (cite: gaia18; bailer-jones18)." (2.1 Background data on UZ Tau)

## Data provenance

- ALMA projects: 2015.1.00690.S
- bands: Band 6  
  > "Our band 6 observations targeted the dust continuum with a 1.875 GHz wide spectral window centered at 233.000 GHz" (2.2 New ALMA observations of UZ Tau)
- frequencies and spectral setup: continuum SPW 1.875 GHz wide at 233.000 GHz; 12CO, 13CO, C18O J=2-1 SPWs with 30.5, 30.5, 61.0 kHz channels  
  > "we placed three spectral windows on the ${}^{12}$CO, ${}^{13}$CO, and C${}^{18}$O $J$=2-1 molecular transitions with channel spacings of 30.5, 30.5, and 61.0 kHz, respectively." (2.2 New ALMA observations of UZ Tau)
- continuum bandwidth: 2.344 GHz  
  > "to create a measurement set with a total of 2.344 GHz continuum bandwidth." (2.2 New ALMA observations of UZ Tau)
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15 - 704 m, 36 antennas  
  > "The array was comprised of 36 antennas and the baselines ranged from 15 - 704 m." (2.2 New ALMA observations of UZ Tau)
- angular resolution: ~0.6" beam (continuum 0.66"x0.61")  
  > "233 GHz cont. | $0.66\ensuremath{''}\times0.61\ensuremath{''}$, -25$^\circ$  | 0.070" (Table 1)
- max recoverable scale: 10.7"  
  > "This configuration of the array yielded a maximum recoverable scale (MRS) of $10.7\ensuremath{''}$." (2.2 New ALMA observations of UZ Tau)
- sensitivity: _not stated_
- time on source: 22 minutes  
  > "The total on-source time was 22 minutes." (2.2 New ALMA observations of UZ Tau)
- observing dates: June 21, 2016  
  > "We observed the UZ Tau system with ALMA on June 21, 2016" (2.2 New ALMA observations of UZ Tau)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (not stated)
- Line: 13CO J=2-1 (not stated)
- Line: C18O J=2-1 (not stated)
- Other facility **FCRAO CO Mapping Survey of the Taurus Molecular Cloud**: 12CO and 13CO J=1-0 maps used to identify cloud-contaminated channels  
  > "we inspected the ${}^{12}$CO and ${}^{13}$CO $J$=1-0 maps of the Five College Radio Astronomy Observatory CO Mapping Survey of the Taurus Molecular Cloud" (2.2 New ALMA observations of UZ Tau)
- External data: UZ Tau E disk inclination 56.15 ± 1.50 deg and Omega_disk 90.39 ± 1.50 deg from ALMA continuum; inclination fixed in the dynamical model  
  > "They also measured the disk inclination (relative to the sky plane) to be $i_\mathrm{disk} = 56.15 \ensuremath{^\circ} \pm 1.50\ensuremath{^\circ}$" (2.1 Background data on UZ Tau) [from (cite: long18)]
- External data: M_tot sin^3 i_star = 0.69 ± 0.13 Msun and mass ratio q = 0.30 ± 0.03 for UZ Tau E  
  > "For UZ Tau E, (cite: jensen07) find $M_\mathrm{tot} \sin^3 i_\star = 0.69 \pm 0.13\,M_\odot$" (2.3 UZ Tau E 13CO and C18O dynamical analysis) [from (cite: jensen07)]
- External data: Orbital and disk parameters of the circumbinary disk sample compiled in Tables 3-5  
  > "The first group contains the circumbinary systems that have precise measurements of the disk and stellar orientations (Table [3](#tab:disks-known))" (3.1 The circumbinary disk sample) [from literature references listed in Table 3-5 notes]
- External data: Gaia DR2 distance 131.2 ± 1.7 pc  
  > "$131.2 \pm 1.7\,$pc (cite: gaia18; bailer-jones18)" (2.1 Background data on UZ Tau) [from (cite: gaia18; bailer-jones18)]
- Simulation/model as data: Two mock samples of N=10 CB disks (isotropic and low-mutual-inclination, Gaussian mu=5 deg, sigma=2 deg times sin theta) used to test the hierarchical model  
  > "we apply it to two $N$=10 samples of fake circumbinary disk systems with drastically different mutual inclination distributions." (3.3 Testing the model with two mock CB disk samples)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: three rounds phase-only and one round amplitude+phase self-cal on continuum, applied to line SPWs; rms 450 to 70 uJy/beam  
  > "We used this CLEAN model to perform three rounds of phase-only self-calibration and one round of amplitude and phase self-calibration via the `gaincal` task." (2.2 New ALMA observations of UZ Tau)

### Imaging

- task: CASA clean for continuum; tclean for lines  
  > "We synthesized images of the CO isotopologue line emission using the CASA `tclean` task with Briggs `robust=0.5` weighting." (2.2 New ALMA observations of UZ Tau)
- deconvolver: multiscale-multifrequency clean (continuum)  
  > "using the multiscale-multifrequency `clean` algorithm and Briggs parameter `robust=0.5`" (2.2 New ALMA observations of UZ Tau)
- weighting robust: Briggs robust = 0.5  
  > "All images were synthesized with `robust=0.5`." (Table 1)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: auto-multithresh initial mask, edited by hand per channel  
  > "We used the `auto-multithresh` to generate an initial starting mask for each CO isotopologue, which was then edited by hand channel-by-channel" (2.2 New ALMA observations of UZ Tau)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub in visibility plane  
  > "The continuum was estimated in the visibility plane and subtracted from the dataset using the CASA task `uvcontsub`." (2.2 New ALMA observations of UZ Tau)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: lines binned to 334 m/s channels (mstransform, LSRK)  
  > "binned all line spectral windows into matching channels $334\,\rm m\thinspace s^{-1}$ wide." (2.2 New ALMA observations of UZ Tau)
- final beam: 12CO 0.65"x0.61"; 13CO 0.70"x0.68"; C18O 0.66"x0.63"  
  > "$^{13}$CO $J$=2$-$1 | $0.70\ensuremath{''}\times0.68\ensuremath{''}$, 35$^\circ$  | 8" (Table 1)
- final rms: continuum 0.070 mJy/beam; 12CO 7, 13CO 8, C18O 5 mJy/beam per 334 m/s channel  
  > "C$^{18}$O $J$=2$-$1 | $0.66\ensuremath{''}\times0.63\ensuremath{''}$, -19$^\circ$  | 5" (Table 1)

### Inherited from earlier work

- Forward-modeling dynamical mass technique (RADMC-3D ray tracing, visibility-plane chi2, MCMC) follows earlier work  
  > "For more information on the implementation of these procedures see (cite: czekala15a) and the `DiskJockey` codebase." (2.3 UZ Tau E 13CO and C18O dynamical analysis) [from (cite: czekala15a)]
- Velocity-field maps made with quadratic-fit technique  
  > "Using the quadratic-fit technique implemented by (cite: teague18) we made maps of the velocity field" (2.2 New ALMA observations of UZ Tau) [from (cite: teague18)]

### Not stated but needed to reproduce (our reading)

- Line-free channels used for continuum and uvcontsub
- Self-calibration solution intervals and reference antenna
- Image size, cell size and clean thresholds
- MCMC walker number, burn-in and convergence criteria for the disk model
- Observed Omega_star treatment and numerical covariance matrices Sigma for the hierarchical model
- Random seed and NUTS settings (draws, tuning) for PyMC3
- Flux calibrator and calibration pipeline/CASA version
- Disk model priors ranges and vertical structure parameters

## Analysis recipe

1. **Continuum imaging and flux**: Self-calibrate on continuum, image with multiscale-multifrequency clean, fit elliptical Gaussian with uvmodelfit  
  > "We fit the dust emission of UZ Tau E with an elliptical Gaussian using the `uvmodelfit` task" (2.2 New ALMA observations of UZ Tau)
   - software: CASA
   - parameter: robust=0.5  
  > "Briggs parameter `robust=0.5`" (2.2 New ALMA observations of UZ Tau)
   - fitting: _not stated_
   - validation: _not stated_
2. **Line imaging, systemic velocity, cloud-contaminated channels**: tclean cubes, moment-0 maps, identify cloud contamination using FCRAO CO 1-0 maps; mask 4.0-7.5 km/s LSRK  
  > "Therefore, we choose to mask from our analysis all channels in the range $4.0 \leq v_\mathrm{LSRK} \leq 7.5\,{\rm km\thinspace s^{-1}}$." (2.2 New ALMA observations of UZ Tau)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared systemic velocity with Simon et al. 2000 and Guilloteau et al. 2013  
  > "The ${}^{12}$CO channel maps in (cite: simon00) appear consistent with our determination of the systemic velocity" (2.2 New ALMA observations of UZ Tau)
3. **Dynamical mass of UZ Tau E**: Forward-model 13CO and C18O emission to visibilities with a parametric disk (RADMC-3D), complex chi2 likelihood, MCMC  
  > "The channel maps are then Fourier transformed, sampled at the baselines corresponding to the array position during the observations, and compared to the visibilities with a complex-valued $\chi^2$ likelihood function." (2.3 UZ Tau E 13CO and C18O dynamical analysis)
   - software: DiskJockey, RADMC-3D
   - parameter: q fixed to 0.5; i_disk fixed to 56.15 deg; gamma=1; d=131.2 pc  
  > "| $q$ | 0.5$^{f}$ | 0.5$^{f}$ |" (Table 2)
   - assumption: Keplerian rotation, vertically isothermal, hydrostatic equilibrium, distance 131.2 pc  
  > "For a given radius, the disk is assumed to be vertically isothermal and the vertical density distribution set by hydrostatic equilibrium." (2.3 UZ Tau E 13CO and C18O dynamical analysis)
   - fitting: Julia affine-invariant ensemble MCMC, uniform priors on disk structure and geometric prior on inclination  
  > "the posterior distribution is sampled using our `Julia` implementation of the Markov Chain Monte Carlo (MCMC) affine-invariant ensemble sampler" (2.3 UZ Tau E 13CO and C18O dynamical analysis)
   - validation: Tried floating q, q=0.5, q=0.75; mass unchanged within uncertainties; compared to Simon et al. 2000  
  > "Throughout all of the choices of temperature power law (floating, and $q=0.50$, and $q=0.75$), the dynamical mass remained the same for each transition within statistical uncertainties." (2.3 UZ Tau E 13CO and C18O dynamical analysis)
4. **Binary inclination i_star**: Combine disk-based M_tot with RV M_tot sin^3 i_star from Jensen et al. 2007  
  > "Since the protoplanetary-disk based technique independently measures $M_\mathrm{tot}$, we can combine these two results to solve directly for $i_\star$." (2.3 UZ Tau E 13CO and C18O dynamical analysis)
   - fitting: _not stated_
   - validation: _not stated_
5. **Hierarchical Bayesian inference of mutual inclination distribution**: Logit-normal p(theta) with hyperparameters mu_v, tau_v; disk-frame rotation; sample full posterior of 4 SB2 disks (V4046 Sgr, DQ Tau, UZ Tau E, AK Sco) using cos i_disk and cos i_star  
  > "we choose to directly sample the full high dimensional posterior with a version of Hamiltonian Monte Carlo (HMC) algorithm called the No U-Turn Sampler (cite: hoffman14), implemented in `PyMC3` (cite: pymc3)." (3.3 Inferring the mutual inclinations of CB disks around SB2s with a hierarchical Bayesian model)
   - software: PyMC3, Theano
   - parameter: hyperpriors: mu_v ~ N(0,2); tau_v half-Gaussian (mu=0.5, sigma=4) with tau>0.5  
  > "we enforce a half-Gaussian prior $p(\tau_v) \propto {\cal N}_{1/2}(\tau_v |\, \mu_\tau = 0.5, \sigma_\tau = 4)$ where $\tau > 0.5$" (3.3 Inferring the mutual inclinations of CB disks around SB2s with a hierarchical Bayesian model)
   - assumption: AK Sco astrometric orbit ignored; Omega_star treated as unknown; uniform phi  
  > "For the purposes of the hierarchical model, we ignore the AK Sco astrometric orbit and treat $\Omega_\star$ and $\ensuremath{\theta}$ as unknown." (3.3 Inferring the mutual inclinations of the subsample of CB disks around SB2s)
   - fitting: NUTS HMC in PyMC3; multivariate normal likelihood  
  > "The likelihood is a multivariate normal" (3.2 Biased measurement of theta)
   - validation: Recovered true distributions for two mock N=10 samples (isotropic and low-inclination); also tried reparameterized Beta functions with unchanged results  
  > "We also experimented with different functional forms for $p(\theta |\,\boldsymbol{\alpha})$ including reparameterized Beta functions, and found our results to be unchanged." (3.3 Parameterizing the mutual inclination distribution)

## Software

- **CASA** : calibration/imaging: plotms, clean, tclean, gaincal, uvcontsub, mstransform, immoments, imstat, uvmodelfit  
  > "we used the CASA task `plotms` (cite: mcmullin07) to identify channels with strong line emission" (2.2 New ALMA observations of UZ Tau)
- **RADMC-3D** : ray-tracing channel maps in disk model  
  > "channel maps are ray-traced using the `RADMC-3D` software package (cite: dullemond12)" (2.3 UZ Tau E 13CO and C18O dynamical analysis)
- **DiskJockey** : forward-modeling disk dynamical mass with Julia MCMC  
  > "see (cite: czekala15a) and the `DiskJockey` codebase." (2.3 UZ Tau E 13CO and C18O dynamical analysis)
- **PyMC3** : NUTS sampling of hierarchical model  
  > "implemented in `PyMC3` (cite: pymc3)" (3.3 Testing the model with two mock CB disk samples)
- **Theano** : automatic differentiation for gradients  
  > "through the `Theano` framework (cite: theano)" (3.3 Testing the model with two mock CB disk samples)
- **emcee** : listed software; affine-invariant sampler reference  
  > "CASA (cite: mcmullin07), DiskJockey (cite: czekala15a; disk_jockey_zenodo), RADMC-3D (cite: dullemond12), emcee (cite: foreman-mackey13)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| UZ Tau E total stellar mass | 1.21 | 0.05 | Msun | 3 | These two uncertainties are added in quadrature to deliver a final mass determination of $M_\mathrm{tot} = 1.21\pm 0.05\,M_\odot$. |
| M_tot from 13CO | 1.19 | 0.01 (stat) | Msun | 3 | / $M_\mathrm{tot}\quad [M_\odot]$ / $1.19 \pm 0.01$ / $1.23 \pm 0.01$ / |
| M_tot from C18O | 1.23 | 0.01 (stat) | Msun | 3 | / $M_\mathrm{tot}\quad [M_\odot]$ / $1.19 \pm 0.01$ / $1.23 \pm 0.01$ / |
| UZ Tau E binary inclination i_star | 56.1 | 5.7 | deg | 4 | we infer the binary inclination relative to the sky-plane to be $i_\star = 56.1 \pm 5.7\ensuremath{^\circ}$ |
| M_Ea | 0.93 | 0.04 | Msun | 4 | $M_\mathrm{Ea} = 0.93 \pm 0.04 \,M_\odot$ and $M_\mathrm{Eb} = 0.28 \pm 0.02 \,M_\odot$ |
| M_Eb | 0.28 | 0.02 | Msun | 4 | $M_\mathrm{Ea} = 0.93 \pm 0.04 \,M_\odot$ and $M_\mathrm{Eb} = 0.28 \pm 0.02 \,M_\odot$ |
| UZ Tau E systemic velocity | 5.5 (LSRK) | 0.1 | km/s | 2 | $v_\mathrm{LSRK} = 5.5 \pm 0.1\,{\rm km\thinspace s^{-1}}$ |
| UZ Tau E 233 GHz continuum flux density | 145.72 | 0.04 (stat) | mJy | 1 | find a flux density of $145.72 \pm 0.04$ mJy |
| UZ Tau E 12CO line flux | 6.01 | 0.02 | Jy km/s | 2 | the ${}^{12}$CO, ${}^{13}$CO, and C${}^{18}$O line fluxes are $6.01\pm0.02\,\mathrm{Jy}\thinspace\mathrm{km}\thinspace \mathrm{s}^{-1}$ |
| 68% upper bound on mutual inclination for CB disks around short-period SB2s | 3.0 | not stated | deg | 5 | with 68% of the probability contained within $\ensuremath{\theta}< 3.0\ensuremath{^\circ}$ (95.4% and 99.7% within $\ensuremath{\theta}< 9.5\ensuremath{^\circ}$ and $\ensuremath{\theta}< 11.9\ensuremath{^\circ}$, respectively) |
| 95.4% upper bound on theta | 9.5 | not stated | deg | 5 | 95.4% and 99.7% within $\ensuremath{\theta}< 9.5\ensuremath{^\circ}$ |

## Qualitative findings

- CB disks around binaries with P<40 d are nearly co-planar, whereas longer-period, eccentric binaries host disks with a wide range of mutual inclinations up to polar  
  > "For the ten CB disks orbiting binaries with periods longer than 40 days, the distribution of mutual inclinations differs dramatically, with most systems having values of $\ensuremath{\theta}> 20\ensuremath{^\circ}$." (3.4 Mutual inclination as a function of orbital period)
- UZ Tau W emits faint CO in all isotopologues; line emission in the E system is contaminated by foreground cloud  
  > "We detect faint line emission from UZ Tau W in all CO isotopologues" (2.2 New ALMA observations of UZ Tau)

## Claim tuples

- H: Circumbinary disks around short-period SB2s are nearly co-planar with their binaries | E: Hierarchical Bayesian model applied to i_disk and i_star of four disks (V4046 Sgr, DQ Tau, UZ Tau E, AK Sco), validated on mock samples | R: 68% of probability within theta<3.0 deg | F: CB disks around short-period SB2s are nearly co-planar | **supported**
- H: UZ Tau E's binary and disk inclinations match | E: Forward-modeling ALMA 13CO and C18O to get M_tot, combine with RV M_tot sin^3 i | R: M_tot=1.21±0.05 Msun, i_star=56.1±5.7 deg vs i_disk=56.15±1.5 deg | F: i_disk ≈ i_star for UZ Tau E | **supported**
- H: Mutual inclination depends on binary period and eccentricity | E: Compiled 19 systems with measured mutual inclinations and plotted against P, a, e | R: Disks around P<30 d and/or e<0.2 binaries consistent with co-planar; longer-period/eccentric ones misaligned to polar | F: Strong trends of theta with P and e | **supported**
- H: Kepler CB planets are co-planar and occurrence rate is similar to single stars | E: Infer from disk co-planarity and prior literature | R: theta<3 deg for disks | F: Adds evidence for low mutual inclinations of Kepler CB planets | **partially**

## Reasoning

- Why this data: New high-resolution ALMA observations to derive new dynamical mass and remove uncertainty from earlier low-resolution 12CO  
  > "in order to derive new dynamical mass measurements of UZ Tau E and remove the lingering uncertainties." (2.1 Background data on UZ Tau)
- Why this method: Hierarchical model used because individual systems lack Omega_star, so single-system theta posteriors are biased broad  
  > "we use a standard Bayesian analysis to demonstrate why this supposition is incorrect when each system is considered individually." (3.2 Direct and indirect measurements of mutual inclination)
- Alternative: Floating temperature profile gave flat cold profiles; q=0.75 tried; q=0.5 chosen as most reasonable. 12CO not modeled because of cloud contamination.  
  > "The choice of $q=0.50$ yielded the most reasonable temperature normalization ($T_{10} \approx 50$ K)" (2.3 UZ Tau E 13CO and C18O dynamical analysis)
- How they decided it was enough: _not stated_
- Limitation (authors): 13CO and C18O masses are statistically inconsistent, implying at least 0.02 Msun systematic error from missing model complexity  
  > "this indicates that there is at least a $0.02\,M_\odot$ systematic error affecting these results" (2.3 UZ Tau E 13CO and C18O dynamical analysis)
- Limitation (authors): Line fluxes are lower limits because of cloud contamination  
  > "We note that because of the foreground cloud contamination, these line fluxes are lower limits only." (2.2 New ALMA observations of UZ Tau)
- Caveat (inferred, ours): Hierarchical result rests on only four systems, one (AK Sco) with questioned orbit
- Caveat (inferred, ours): Sample inclusion of literature values heterogeneous; selection effects asserted not tested
- Caveat (inferred, ours): Inclination fixed from continuum rather than fit, so M_tot error budget approximated
- Caveat (inferred, ours): Logit-normal form and hyperpriors may influence the tight 3 deg bound

## Reproducibility

- Data public (paper): ALMA project code printed and acknowledged; public availability not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00690.S." (Acknowledgments)
- Products in archive: _not stated_
- Code: DiskJockey available on GitHub  
  > "<https://github.com/iancze/DiskJockey>" (footnote 3)
- Missing: CASA version and calibration details
- Missing: Line-free channel ranges and clean parameters
- Missing: MCMC run settings for disk model and PyMC3 sampler
- Missing: Exact input table values/covariances for the hierarchical model beyond Table 3
- Data volume (inferred): ~10-30 GB raw single-EB Band 6 dataset (22 min on source, 36 antennas)
- Score (inferred): 6/5, Public single ALMA dataset with fairly clear model description and released code, but imaging/calibration parameters and sampler settings are missing.
- Rediscovery candidate: yes, Public ALMA data, numeric results (M_tot, i_star, theta<3 deg), and hierarchical model fully specified with tabulated inputs.

## Links

- Method: (cite: czekala15a) (DiskJockey visibility-plane forward-modeling of disk dynamics)
- Method: (cite: teague18) (quadratic-fit velocity-field maps)
- Method: (cite: hogg10b) (hierarchical inference background)
- Companion: (cite: long18) (ALMA continuum of UZ Tau E giving i_disk used here)
- Companion: (cite: jensen07) (UZ Tau E spectroscopic orbit)
- Related: Kepler circumbinary planets
- Related: FCRAO Taurus CO Mapping Survey

## Checks

```json
{
 "quotes": 79,
 "quotes_ok": 79,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 83,
  "stated": 58,
  "rate": 0.699
 },
 "evidence_ok": true
}
```
