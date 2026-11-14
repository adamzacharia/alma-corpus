# The Mass of Stirring Bodies in the AU Mic Debris Disk Inferred from Resolved Vertical Structure

`2019ApJ...875...87D` | The Astrophysical Journal 2019 | first author: Daley, Cail | arXiv: 1904.00027 | DOI: 10.3847/1538-4357/ab1074

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: debris_disks
- Question: Can the vertical thickness of the AU Mic debris disk be resolved at 1.3 mm, and what does it imply for the mass and size of the bodies stirring the disk?  
  > "The 3 au spatial resolution of the observations, combined with the favorable edge-on geometry of the system, allows us to measure the vertical thickness of the disk." (abstract)
- Target **AU Mic**: coordinates RA 20:45:09.84, Dec -31:20:32.4 (J2000; high proper motion, Table 1)  
  > "proximity (9.725 ± 0.005 pc; (cite: gaia16; gaia_DR2))" (Introduction); z/distance 9.725 ± 0.005 pc  
  > "proximity (9.725 ± 0.005 pc; (cite: gaia16; gaia_DR2))" (Introduction); distance from Gaia (gaia16; gaia_DR2)  
  > "proximity (9.725 ± 0.005 pc; (cite: gaia16; gaia_DR2))" (Introduction)

## Data provenance

- ALMA projects: 2012.1.00198.S
- bands: Band 6, 1.3 mm (mean wavelength 1.35 mm)  
  > "All observations employed ALMA’s 12m antennas and Band 6 receivers" (Observations); "The mean of the four central wavelengths is 1.35 mm." (Observations)
- frequencies and spectral setup: 4 spws of 1.875 GHz; CO 2-1 spw with 488 kHz channels; continuum spws at 228.5, 213.5, 216.0 GHz  
  > "The remaining three spectral windows were configured to detect continuum emission with central frequencies of 228.5, 213.5, and 216.0 GHz" (Observations)
- continuum bandwidth: _not stated_
- arrays: 12m antennas  
  > "All observations employed ALMA’s 12m antennas" (Observations)
- configurations: _not stated_
- baselines: 12–1320 m  
  > "The baseline lengths range between 12 m, & 1320 m" (Observations)
- angular resolution: combined natural-weighted beam 0.52" x 0.39", PA 77.9°  
  > "resulting in an rms noise of 15  Jy beam^−1^ and a $\ang{;;0.52} \times \ang{;;0.39}$ restoring beam with a position angle (PA) of 77.9°." (Observations)
- max recoverable scale: _not stated_
- sensitivity: combined rms 15 µJy/beam  
  > "resulting in an rms noise of 15  Jy beam^−1^" (Observations)
- time on source: 35, 35, 33 min for the three epochs  
  > "On-source time (min): | 35 | 35 | 33" (Table 1)
- observing dates: 2014 Mar 26, 2014 Aug 18, 2015 Jun 24  
  > "2014 Mar 26 | 2014 Aug 18 | 2015 Jun 24" (Table 1)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (230.538001 GHz)
- Other facility **Gaia**: stellar distance  
  > "a distance to the star of 9.725 ± 0.005 pc (cite: gaia_DR2)" (Analysis)
- External data: Stellar luminosity 0.09 Lsun  
  > "We adopt a stellar luminosity of 0.09 L~$\odot$~ (cite: plavchan09)" (Analysis) [from plavchan09]
- External data: Dust opacity 2.3 cm^2 g^-1  
  > "The dust opacity is set to 2.3 cm^2^ g^−1^ (cite: beckwith90)" (Analysis) [from beckwith90]

## Processing

### Calibration

- pipeline or manual: Standard ALMA reduction scripts in CASA, plus visibility weights recalculated  
  > "Standard ALMA reduction scripts were applied to the datasets" (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (Mar, Jun), J2056-472 (Aug)  
  > "Flux calibrator: | Titan | J2056-472 | Titan" (Table 1)
- flux scale uncertainty: 10% systematic  
  > "the flux calibration is subject to a 10% systematic uncertainty" (Observations)
- self calibration: _not stated_

### Imaging

- task: CASA tclean; concat to combine epochs; fixvis to shift phase centers  
  > "Imaging was performed using standard Fourier inversion methods as implemented in the `CASA` task `tclean`." (Observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "A natural weighting scheme was used to trace small-scale disk structure" (Observations)
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
- final beam: 0.52" x 0.39", PA 77.9°  
  > "$\ang{;;0.52} \times \ang{;;0.39}$ restoring beam with a position angle (PA) of 77.9°" (Observations)
- final rms: 15 µJy/beam  
  > "resulting in an rms noise of 15  Jy beam^−1^" (Observations)

### Inherited from earlier work

- Visibility weights recalculated from variance around each baseline  
  > "the weights of the visibilities were recalculated using the variance around each baseline as in (cite: flaherty17)." (Observations) [from flaherty17]
- Parametric ray-tracing disk model code  
  > "We use the parametric structure and ray tracing disk code described in (cite: flaherty15), itself an adaptation of earlier work by (cite: rosenfeld13)." (Modeling Formalism) [from flaherty15; rosenfeld13]
- Steady-state size-dependent velocity model for stirring bodies  
  > "we refer to theoretical models of steady state size-dependent velocity distributions in the collisional cascade desribed in (cite: pan&schlichting12)." (Inferring the Mass of Stirring Bodies) [from pan&schlichting12]

### Not stated but needed to reproduce (our reading)

- tclean cell size, image size, niter, threshold and mask
- spectral windows/channels used and any line-free channel selection for the continuum
- CASA version
- MCMC prior bounds, walker initialization, burn-in and convergence criteria
- dirtol value used in concat
- Details of the disk model code (not publicly cited as released), e.g. radial grid and how stellar flux is added
- Slice widths for image-domain profiles
- Parameters of the eccentricity probability calculation (code not given)

## Analysis recipe

1. **Align and combine the three epochs and image**: Fit 2D Gaussian to star with imfit, phase-shift with fixvis, concat the three datasets, image with tclean natural weighting  
  > "Each dataset was then phase-shifted using the task `fixvis` so that the pointing center of the data was the same as the fitted star position." (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Image-domain profiles of the disk**: Extract surface brightness and fit 1D Gaussians to vertical slices along the major axis; subtract beam FWHM in quadrature  
  > "Broadening effects of the synthesized beam in the vertical direction have been removed by subtracting in quadrature the Gaussian beam FWHM" (Results)
   - software: MIRIAD
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit parametric disk model to visibilities**: Ray-traced axisymmetric optically thin disk with Gaussian vertical profile and H=hr, power-law surface density; model image Fourier transformed and sampled with uvmodel; MCMC fit  
  > "it is Fourier transformed into the visibility domain and sampled at the same spatial frequencies as the ALMA data with the `MIRIAD` task `uvmodel`." (Analysis)
   - software: emcee, MIRIAD
   - parameter: 50 walkers, 10^5 samples; 0.15 au per pixel  
  > "All runs used 50 walkers, and $10^5$ samples were drawn from each run" (Analysis)
   - assumption: opacity 2.3 cm^2/g; dust in blackbody equilibrium; L*=0.09 Lsun; d=9.725 pc; vertically isothermal  
  > "we assume that the dust grains are in blackbody equilibrium with the central star" (Modeling Formalism)
   - fitting: Affine-invariant emcee, lnL=-chi^2/2, uniform priors (log-uniform for dust mass); 10 free parameters  
  > "We assume uniform priors for all parameters." (Modeling Formalism)
   - validation: Skinny model with h=0.003 fit worse (3.7σ AICc, ΔBIC 5.8); inclination bound test; reduced chi2 1.032  
  > "The skinny model results in a significantly poorer fit to the data than the fiducial model" (4.3 Investigating Vertical Structure)
4. **Test inner ring/gap**: Add gap or ring component; compare via AICc and BIC  
  > "We use both the AICc, a form of the Aikake Information Criterion (AIC) corrected for finite datasets, and the Bayesian Information Criterion (BIC)" (4.2 Investigating Radial Structure)
   - software: emcee
   - parameter: ring width fixed to 0.1 au  
  > "the ring width was fixed to 0.1 au" (4.2 Investigating Radial Structure)
   - fitting: _not stated_
   - validation: Ring preferred at 3.7σ by AICc but fiducial preferred on BIC (ΔBIC=4.3)  
  > "the fiducial model is preferred to the ring model on the BIC with $\Delta \text{BIC} = 4.3$" (4.2 Investigating Radial Structure)
5. **Derive stirring body constraints**: Convert h to inclination dispersion and relative velocity; set lower limit on body size from escape velocity; steady-state Pan & Schlichting model gives sqrt(Np)*mp  
  > "we can use our estimate for $v_{rel}$ to place a lower limit on the escape velocity $v_{esc}$ and thus size $a_{big}$ of bodies stirring the disk." (5.5 Inferring the Mass of Stirring Bodies)
   - assumption: M*=0.5 Msun; r=40 au; density 2 g/cm^3; perturber eccentricity 0.03; HWHM 1.5 au  
  > "We assume an eccentricity of 0.03 (typical of the major planets of the Solar System)" (5.5 Inferring the Mass of Stirring Bodies)
   - fitting: _not stated_
   - validation: Consistent with Chiang & Fung 2017 progenitor size  
  > "The properties of the perturbers estimated in this work are consistent with those inferred independently by (cite: chiang&fung17)." (5.5 Inferring the Mass of Stirring Bodies)

## Software

- **CASA** : calibration, split, tclean, imfit, fixvis, concat  
  > "Calibration, reduction, and imaging were carried out using the `CASA` software package." (Observations)
- **MIRIAD** : flux measurement (cgcurs) and model sampling (uvmodel)  
  > "Using the `MIRIAD` task `cgcurs`, we measure an integrated flux density of 4.97 ± 0.08 mJy" (Results)
- **emcee** : MCMC fitting of disk model  
  > "implemented in Python as `emcee` (cite: foreman-mackey13)" (Modeling Formalism)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Aspect ratio h | 0.031 | +0.005/-0.004 | dimensionless | 3 | We report a scale height-to-radius aspect ratio of $h = 0.031_{-0.004}^{+0.005}$ |
| Disk flux density (model) | 4.81 | +0.04/-0.05 | mJy | 3 | our modeling yields a disk flux density of 4.81 \^{+0.04} \_{-0.05} mJy |
| Inner radius | 23.2 | +0.6/-0.8 | au | 3 | $r_{in}$ (au) / $23.2   _{-0.8}   ^{ +0.6}$ |
| Outer radius | 41.5 | +0.4/-0.5 | au | 3 | $r_{out}$(au) / $41.5   _{-0.5}   ^{ +0.4}$ |
| Inclination | 88.5 | +0.3/-0.2 | deg | 3 | $i$ (°) / $88.5   _{-0.2}   ^{ +0.3}$ |
| CO 2-1 flux upper limit | 0.07 | 3 sigma | Jy km/s | 0 | We set a $3 \sigma$ upper limit of 0.07 Jy km s^−1^ on the CO $\mathrm{J}=2-1$ integrated flux |
| Dust mass | 9.28e-3 | ±0.13e-3 | Earth masses | 3 | 9.28 ± 0.13 × 10^−3^ M~$\oplus$~ for an opacity of 2.3 cm^2^ g^−1^ |
| Scale height at 40 au | 1.24 | +0.20/-0.16 | au | 3 | vertical scale height of 1.24\^{+0.20}\_{-0.16} au |
| Relative velocity | 420 | +70/-50 | m/s | 5 | yields $v_{rel} = \SI[parse-numbers=false]{420^{+70}_{-50}}{m/s}$ |
| Minimum stirring body radius | 400 | +60/-50 | km | 5 | we find $a_{big} \sim \SI[parse-numbers=false]{400^{+60}_{-50}}{km}$ |
| sqrt(Np)*mp | 1.8 | not stated | Earth masses | 5 | $\sqrt{N_p} m_{p} \sim \SI{1.8}{M_\ensuremath{\oplus}}$ |

## Qualitative findings

- Disk vertical structure is resolved; AU Mic has the narrowest mm scale height of any known debris disk  
  > "to our knowledge, AU Mic exhibits the narrowest millimeter-wavelength scale height of any known debris disk." (5.4 Vertical Structure)
- Marginal evidence for an inner dust ring at ~10 au  
  > "the data are suggestive of an additional ring of dust at $\sim \SI{10}{au}$" (Conclusions)

## Claim tuples

- H: Is the mm vertical thickness of the AU Mic disk resolved rather than an upper limit? | E: MCMC visibility modeling and comparison with a thin h=0.003 model | R: h=0.031 (+0.005/-0.004), ~8σ; skinny model disfavored at 3.7σ AICc | F: Scale height is measured, not an upper limit | **supported**
- H: What bodies stir the disk? | E: Relate h to velocity dispersion and steady-state collisional model | R: Stirring bodies >~400 km; largest body <~1.8 Earth masses | F: Rules out gas giant or Neptune analog embedded in outer disk | **supported**
- H: Is there an additional inner ring? | E: Add ring/gap to model, compare AICc/BIC | R: AICc prefers ring (3.7σ), BIC prefers fiducial | F: Not conclusive | **partially**
- H: Does gas affect the dust kinematics? | E: CO 2-1 upper limit | R: gas-to-dust ratio upper limit ~1 | F: Gas does not influence mm grain scale height | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Parametric modeling to handle degeneracy between vertical structure, radial structure, and viewing geometry  
  > "we adopt a modeling approach that combines a simple ray-tracing code to properly project the radial and vertical flux distribution" (Analysis)
- Alternative: Gap model rejected: gap converged to regions with zero density  
  > "we take this as evidence that the data are not well characterized by a gap" (4.2 Investigating Radial Structure)
- Alternative: Single stellar flux across dates rejected (7.3σ AICc)  
  > "did not reproduce the data to the same degree of accuracy as the fiducial model" (4.2 Investigating Radial Structure)
- How they decided it was enough: _not stated_
- Limitation (authors): Phase noise could degrade true resolution so the h measurement may be an upper limit  
  > "if the phase noise is at the upper end of the range suggested by the quasar measurements, it may be an upper limit instead." (5.4 Vertical Structure)
- Limitation (authors): External perturbers not considered; limits on embedded perturbers are then upper limits  
  > "If external stirring is significant, then the above constraints on the properties of embedded (non-external) perturbers are all upper limits." (5.5 Inferring the Mass of Stirring Bodies)
- Caveat (inferred, ours): Strong h–inclination degeneracy; scale height below the beam size depends on model assumptions
- Caveat (inferred, ours): Constant aspect ratio and Gaussian vertical profile assumed
- Caveat (inferred, ours): Dust mass uncertainty excludes 10% flux and opacity uncertainty
- Caveat (inferred, ours): Stellar flare/variability and star-disk overlap complicate disk flux

## Reproducibility

- Data public (paper): ALMA data cited by project code 2012.1.00198.S  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00198.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Disk model code and priors bounds
- Missing: tclean parameters
- Missing: CASA version
- Missing: Eccentricity and Pan & Schlichting computation details
- Data volume (inferred): ~50-100 GB raw for three Band 6 epochs
- Score (inferred): 3/5, Data public and recipe described, but modeling code and imaging parameters are not fully specified.
- Rediscovery candidate: no, Custom modeling code and several unstated settings prevent a clean redo, though the data are public.

## Links

- Method: flaherty15 (disk ray-tracing model code)
- Method: pan&schlichting12 (steady-state collisional velocity model)
- Method: thebault09 (theory linking scale height to stirring)
- Companion: macgregor13 (earlier lower-resolution ALMA observations of AU Mic)
- Companion: chiang&fung17 (independent constraint on large planetesimals)

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
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 49,
  "rate": 0.636
 },
 "evidence_ok": true
}
```
