# Evidence of a Flat Outer Rotation Curve in a Star-bursting Disk Galaxy at z = 1.6

`2018ApJ...869...58D` | The Astrophysical Journal 2018 | first author: Drew, Patrick M. | arXiv: 1811.01958 | DOI: 10.3847/1538-4357/aaedbf

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies
- Question: Does a z=1.555 dusty star-forming disk galaxy have a flat or declining outer rotation curve, and what is its dark matter fraction?  
  > "We present an observational counterexample, a galaxy named DSFG850.95 at $z=1.555$ (4.1 Gyr after the big bang) that hosts a flat rotation curve between radii of $\sim$6–14 kpc" (abstract)
- Target **DSFG850.95**: coordinates _not stated_; z/distance z = 1.555  
  > "a galaxy named DSFG850.95 at $z=1.555$ (4.1 Gyr after the big bang)" (abstract); distance from _not stated_

## Data provenance

- ALMA projects: _none stated_
- bands: _not stated_
- frequencies and spectral setup: 870 μm dust continuum  
  > "ALMA 870 $\mu$m dust continuum contours of DSFG850.95" (Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **Keck/MOSFIRE**: H-band slit spectroscopy of Halpha and [NII], 1920 s, 0.7'' slit, used for rotation curve  
  > "The galaxy, DSFG850.95, was observed in the H band for a total integration time of 1920 s with the slit width set to $0.7\ensuremath{''}$." (Observations and Data Reduction)
- Other facility **UltraVISTA**: H-band imaging for GALFIT Sérsic fit  
  > "we fit a Sérsic profile (cite: Sersic63a) to H-band imaging of DSFG850.95 from the UltraVISTA survey (cite: McCracken12a)." (H-Band Light Profile Fitting)
- Other facility **HST**: F814W imaging for comparison  
  > "The right panel of [2](#fig:image) shows *Hubble* imaging in the F814W filter" (Observations and Data Reduction)
- External data: Stellar mass from MAGPHYS SED fitting, (3.8+0.4-1.0)e10 Msun  
  > "and finds a stellar mass of ${{\rm M}_{\star}}=(3.8^{+0.4}_{-1.0})\times10^{10}$ M$_{\odot}$." (Dynamical, Stellar, Gas, and Dark Matter Masses) [from (cite: Casey17a)]

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

- Gas mass from 870 μm continuum following Scoville prescription  
  > "Following the prescription of (cite: Scoville16a) we use our ALMA 870 $\mu$m dust continuum observations to estimate a molecular gas mass" (Dynamical, Stellar, Gas, and Dark Matter Masses) [from (cite: Scoville16a)]
- Stellar mass error derivation procedure  
  > "We follow the procedure of (cite: Hainline11a) for similarly-selected DSFGs at similar redshifts to derive a more conservative error" (Dynamical, Stellar, Gas, and Dark Matter Masses) [from (cite: Hainline11a)]

### Not stated but needed to reproduce (our reading)

- ALMA observing setup, calibration, imaging and continuum flux density are not given
- Scoville gas-mass assumptions (dust temperature, alpha_850) not given
- Prior choices and likelihood for pymc3 fits not given
- GALFIT setup (PSF, masking) not given

## Analysis recipe

1. **Extract rotation and dispersion curves**: Extract 1D spectra with apall, fit Halpha and [NII] simultaneously with splot; errors from 1000 Monte Carlo perturbations  
  > "We fit H$\alpha$, \[NII\]$\lambda 6548$, and \[NII\]$\lambda 6583$ simultaneously with fixed spacing between spectral features and tied but variable emission line full widths at half maximum (FWHM)." (Observations and Data Reduction)
   - software: iraf, MOSPY
   - parameter: Aperture radius equal to half the average seeing (0.85'')  
  > "Apertures of extraction were placed on each pixel across the galaxy with a radius equal to half the average seeing." (Observations and Data Reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit kinematic model**: Modified arctan rotation curve and Gaussian-plus-offset dispersion profile fitted with MCMC  
  > "We fit the position-velocity and position-dispersion data with the pymc3 python package for Markov Chain Monte Carlo" (Kinematic Model)
   - software: pymc3
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit H-band light profile and inclination**: GALFIT Sérsic fit; inclination from axis ratio with intrinsic edge-on axis ratio 0.25  
  > "assuming an intrinsic edge-on axis ratio of 0.25 (cite: Wuyts16a)" (H-Band Light Profile Fitting)
   - software: GALFIT
   - fitting: _not stated_
   - validation: A second Sérsic component for a bulge gave significantly worse fits  
  > "Adding a second Sérsic component to fit a bulge causes significantly worse fits." (H-Band Light Profile Fitting)
4. **Derive dynamical mass, gas mass and dark matter fraction**: Mdyn=Vc^2 r/G; ALMA 870 μm continuum gives gas mass; fDM=1-(M*(R1/2)+Mgas)/Mdyn  
  > "We calculate the dark matter fraction at the half light radius using the equation" (Dynamical, Stellar, Gas, and Dark Matter Masses)
   - assumption: Half of the total stellar mass lies within R1/2; all gas within R1/2; Chabrier IMF; Planck cosmology  
  > "where $M_{\star}(R_{1/2})$ is half of the total stellar mass" (Dynamical, Stellar, Gas, and Dark Matter Masses)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **iraf** : Spectral extraction (apall) and line fitting (splot)  
  > "We extracted 1D spectra from the MOSFIRE data using the iraf[^2] routine apall." (Observations and Data Reduction)
- **MOSPY** : MOSFIRE data reduction  
  > "The data were reduced with the MOSPY data reduction pipeline[^1]." (Observations and Data Reduction)
- **pymc3** : MCMC fits of rotation and dispersion curves  
  > "We fit the position-velocity and position-dispersion data with the pymc3 python package for Markov Chain Monte Carlo" (Kinematic Model)
- **GALFIT** : Sérsic fit to H-band image  
  > "Using the 2D image fitting code, GALFIT (cite: Peng02a), we fit a Sérsic profile" (H-Band Light Profile Fitting)
- **MAGPHYS** : SED fitting for stellar mass (by Casey17a)  
  > "(cite: Casey17a) uses MAGPHYS with the high-$z$ extension" (Dynamical, Stellar, Gas, and Dark Matter Masses)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| V_flat | 285 | 12 | km/s | 2 | is $V_{\rm flat}=285\raisebox{.2ex}{$\scriptstyle\pm$}12$ km s$^{-1}$. |
| sigma_0 | 48 | 4 | km/s | 2 | an ionized gas velocity dispersion of $\sigma_{0}=48\raisebox{.2ex}{$\scriptstyle\pm$}4$ km s$^{-1}$ |
| Sérsic index | 1.29 | 0.03 | dimensionless | 3 | The fit reveals a Sérsic index of $n=1.29\raisebox{.2ex}{$\scriptstyle\pm$}0.03$ |
| H-band half-light radius | 8.4 | 0.1 | kpc | 3 | The H-band half-light radius is $r_{1/2}=8.4\raisebox{.2ex}{$\scriptstyle\pm$}0.1$ kpc |
| Dynamical mass within 14 kpc | 2.7e11 | 0.3e11 | Msun | 4 | and within 14 kpc is $(2.7\raisebox{.2ex}{$\scriptstyle\pm$}0.3) \times 10^{11}$ M$_{\odot}$ |
| Molecular gas mass from ALMA 870 μm | 8.9e10 | 0.4e10 | Msun | 4 | to estimate a molecular gas mass of $(8.9\raisebox{.2ex}{$\scriptstyle\pm$}0.4)\times 10^{10}$ M$_{\odot}$ |
| Dark matter fraction at R1/2 | 0.44 | 0.08 | dimensionless | 4 | We find $f_{\rm DM}(R_{1/2})=0.44\raisebox{.2ex}{$\scriptstyle\pm$}0.08$. |

## Qualitative findings

- No evidence of a velocity turnover with declining rotation; the outer slope is consistent with flat  
  > "There is no evidence of a velocity turnover with declining rotation." (Kinematic Model)

## Claim tuples

- H: Do z>1 disk galaxies necessarily have declining outer rotation curves? | E: Keck/MOSFIRE Halpha rotation curve of DSFG850.95 fitted with modified arctan model | R: c = -0.5±1.0 km/s/arcsec, V_flat = 285±12 km/s over 6–14 kpc | F: The rotation curve is flat, a counterexample to declining curves | **supported**
- H: Is the dark matter fraction in the outer galaxy low as at some other z>1 galaxies? | E: Combine dynamical mass with stellar mass and ALMA-based gas mass | R: fDM(R1/2)=0.44±0.08 | F: Dark matter fraction is similar to the Milky Way and low-z disks | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Slit misaligned with the H-band major axis by 23±4 deg, which could underpredict the rotation velocity  
  > "Large misalignments would result in an underprediction of the maximum rotational velocity of a galaxy" (H-Band Light Profile Fitting)
- Caveat (inferred, ours): Single galaxy, so no statistical conclusion
- Caveat (inferred, ours): Large stellar mass uncertainty (3.8±3.0e10)
- Caveat (inferred, ours): Slit offset and seeing smearing
- Caveat (inferred, ours): Gas mass depends on Scoville dust-to-gas calibration

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA data processing details and flux
- Missing: MOSFIRE raw data access not stated
- Missing: MCMC priors
- Data volume (inferred): ~10 GB for the ALMA continuum; the MOSFIRE and UltraVISTA data are small
- Score (inferred): 3/5, ALMA is used only for a continuum gas mass, with no processing details; the kinematic methods are described fairly well.
- Rediscovery candidate: no, The main results come from Keck data, and the ALMA recipe is incomplete.

## Links

- Method: (cite: Scoville16a) (Gas mass from 870 μm continuum)
- Method: (cite: Weiner06a) (Kinematic model and slit misalignment)
- Companion: (cite: Casey17a) (Parent MOSFIRE DSFG sample and SED stellar mass)
- Related: UltraVISTA
- Related: COSMOS

## Checks

```json
{
 "quotes": 34,
 "quotes_ok": 34,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2015.1.00568.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 23,
  "rate": 0.329
 },
 "evidence_ok": true
}
```
