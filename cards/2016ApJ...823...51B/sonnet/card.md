# Toward Precision Black Hole Masses with ALMA: NGC 1332 as a Case Study in Molecular Disk Dynamics

`2016ApJ...823...51B` | The Astrophysical Journal 2016 | first author: Barth, Aaron J. | arXiv: 1603.04523 | DOI: 10.3847/0004-637X/823/1/51

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: Can ALMA CO(2-1) kinematics of the NGC 1332 circumnuclear disk, at 0.3'' resolution, constrain the central black hole mass, and what limits the measurement?  
  > "We constructed dynamical models for the rotating disk and fitted the modeled CO line profiles directly to the ALMA data cube." (abstract)
- Target **NGC 1332**: coordinates _not stated_; z/distance 22.3 Mpc; v = 1550±29 km/s  
  > "We adopt a distance of 22.3 Mpc for consistency with (cite: rusli2011)" (1 Introduction); "The recession velocity of NGC 1332 as measured from optical data is $1550\pm29$ km s$^{-1}$ (cite: dacosta1991)." (1 Introduction); distance from adopted for consistency with Rusli et al. 2011  
  > "We adopt a distance of 22.3 Mpc for consistency with (cite: rusli2011)" (1 Introduction); "The recession velocity of NGC 1332 as measured from optical data is $1550\pm29$ km s$^{-1}$ (cite: dacosta1991)." (1 Introduction)

## Data provenance

- ALMA projects: 2013.1.00229.S
- bands: Band 6, centered on redshifted 12CO(2-1) at 229.37 GHz  
  > "in a frequency band centered on the redshifted $^{12}$CO(2-1) 230.538 GHz line at $\nu_\mathrm{obs} = 229.37$ GHz (in ALMA Band 6)" (2 Observations)
- frequencies and spectral setup: 60 channels, 15.4 MHz spacing (20.1 km/s)  
  > "The data cube contains 60 frequency channels with spacing 15.4 MHz, or velocity spacing 20.1 km s$^{-1}$" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 33.7 m to 1.1 km  
  > "The minimum and maximum baselines of the array were 33.7 m and 1.1 km, respectively" (2 Observations)
- angular resolution: 0.319'' x 0.233'' beam, PA 78.4 deg; geometric mean 0.27'' (29.2 pc)  
  > "synthesized beam with major and minor axis FWHM sizes of $0.319\ensuremath{''}$ and $0.233\ensuremath{''}$ and major axis position angle 78.4$^\circ$" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: 0.4 mJy/beam per channel (20.1 km/s channels)  
  > "The RMS noise level as measured in line-free regions of the data cube is 0.4 mJy beam$^{-1}$ per channel." (2 Observations)
- time on source: 22.7 min  
  > "the on-source integration time was 22.7 min" (2 Observations)
- observing dates: 2014 September 1  
  > "ALMA observed NGC 1332 on 2014 September 1" (2 Observations)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (230.538 GHz)
- Other facility **HST WFPC2 F814W**: Archival I-band image of the dust disk; stellar luminosity profile consistency check  
  > "as seen in an archival *HST* WFPC2 F814W ($I$-band) image" (2 Observations)
- External data: Deprojected R+K-band stellar mass profile (Upsilon_R=7.35), provided by J. Thomas; used in final fits  
  > "We used this same mass profile (kindly provided by J. Thomas)" (4.2 Stellar Mass Profile) [from (cite: rusli2011)]
- External data: Stellar-dynamical BH mass (1.45±0.20)e9 Msun for comparison  
  > "found $\ensuremath{M_\mathrm{BH}}= (1.45\pm0.20)\times10^9$ ${M}_{\odot}$" (1 Introduction) [from (cite: rusli2011)]
- External data: X-ray hydrostatic BH mass 0.52 (+0.41/-0.28)e9 Msun for comparison  
  > "derived a smaller central mass of $\ensuremath{M_\mathrm{BH}}= 0.52_{-0.28}^{+0.41} \times10^9$ ${M}_{\odot}$" (1 Introduction) [from (cite: humphrey2009)]
- External data: Bulge stellar velocity dispersion 328 km/s  
  > "bulge stellar velocity dispersion of 328 km s$^{-1}$ (cite: kormendyho)" (1 Introduction) [from (cite: kormendyho)]
- External data: alpha_CO=3.1 and R21=0.7  
  > "Following (cite: sandstrom2013), we assume an intensity ratio $R_{21} \equiv L^{\prime}_\mathrm{CO(2-1)}/L^{\prime}_\mathrm{CO(1-0)} = 0.7$." (3 CO emission properties and disk kinematics) [from (cite: sandstrom2013)]

## Processing

### Calibration

- pipeline or manual: standard ALMA pipeline version 31266  
  > "version 31266 of the standard ALMA pipeline" (2 Observations)
- casa version: CASA 4.2.2, r30721  
  > "version 4.2.2, r30721 of the Common Astronomy Software Application" (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0334-4008, 0.76 Jy at 234.2 GHz  
  > "The overall flux scale for the data was set by an observation of the quasar J0334$-$4008" (2 Observations)
- flux scale uncertainty: 10%  
  > "for which we adopt a 10% uncertainty (cite: alma2015)" (2 Observations)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robustness 0.5  
  > "Use of Briggs weighting with robustness parameter 0.5" (2 Observations)
- uv taper: _not stated_
- cell size: 0.07''  
  > "with 0.07$''$ spatial pixels" (2 Observations)
- image size: 21'' x 21'' field of view  
  > "spanning a field of view of 21$''$$\times$21$''$" (2 Observations)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: 0.4 mJy/beam per channel  
  > "0.4 mJy beam$^{-1}$ per channel" (2 Observations)

### Inherited from earlier work

- Disk model follows approach used for HST ionized gas disks  
  > "We modeled the kinematics of a flat circular disk following the same approach used for ionized gas disks observed with *HST*" (4.1 Method) [from (cite: macchetto1997; barth2001; walsh2010)]
- Stellar mass profile adopted from Rusli et al. for comparison  
  > "We used this same mass profile (kindly provided by J. Thomas)" (4.2 Stellar Mass Profile) [from (cite: rusli2011)]
- Kinemetry method  
  > "we used the kinemetry method of (cite: krajnovic2006)" (3 CO emission properties and disk kinematics) [from (cite: krajnovic2006)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and continuum subtraction method
- Clean threshold, masking and deconvolver for tclean
- Actual coordinates of NGC 1332
- Starting parameters and bounds for the amoeba fits
- Initial values of the amoeba fits
- The elliptical fitting region definition in detail
- HST dataset ID
- Kinemetry code settings

## Analysis recipe

1. **Image and characterize CO emission**: CASA/pipeline imaging; summed CO image; continuum and total flux measured  
  > "Figure [1](#hstalmafig) shows the ALMA CO image of NGC 1332, summed over all frequency channels of the data cube." (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Map kinematics (Gauss-Hermite, kinemetry, PVD)**: Sixth-order Gauss-Hermite fit per pixel; kinemetry on v_LOS; PVD from 4-pixel-wide swath after rotation by 27 deg  
  > "we fit the line profile at each spatial pixel using a sixth-order Gauss-Hermite function (cite: vandermarel1994)" (3 CO emission properties and disk kinematics)
   - software: kinemetry
   - fitting: _not stated_
   - validation: _not stated_
3. **Estimate molecular gas mass**: Flux to L'CO(2-1), R21=0.7, alpha_CO=3.1 with He correction  
  > "a standard value of $\ensuremath{\alpha_\mathrm{CO}}= 3.1$ ${M}_{\odot}$ pc$^{-2}$ (K km s$^{-1}$)$^{-1}$" (3 CO emission properties and disk kinematics)
   - assumption: R21=0.7, alpha_CO=3.1 including 1.36 He factor  
  > "including a factor of 1.36 correction for helium (cite: sandstrom2013)" (3 CO emission properties and disk kinematics)
   - fitting: _not stated_
   - validation: _not stated_
4. **Build forward-model data cubes**: Flat circular disk with BH plus stars, Gaussian local profile with sigma_turb, oversampling s=10, scaled by Richardson-Lucy deconvolved CO map (5 iterations), convolved with beam  
  > "We deconvolved the CO image shown in Figure [1](#hstalmafig) using five iterations of the Richardson-Lucy algorithm" (4.1 Method)
   - software: IRAF
   - parameter: sigma_turb prescriptions: flat, exponential, Gaussian; min 1 km/s  
  > "we enforced a minimum value of $\ensuremath{\sigma_\mathrm{turb}}=1$ km s$^{-1}$" (4.3 Turbulent Velocity Dispersion Profile)
   - assumption: No dark matter or gas mass; thin, dynamically cold disk; distance 22.3 Mpc  
  > "We neglect the possible contribution of dark matter" (4.1 Method)
   - fitting: _not stated_
   - validation: Oversampling tests s=1-50  
  > "The models converged on consistent results for $\ensuremath{\chi^2}$ and for the free parameters when the oversampling factor was greater than $s=4$." (5.1 Initial tests)
5. **Fit models to data cube**: chi^2 minimization with amoeba on 4x4 block-averaged cube; 49 pixels x 52 channels = 2548 data points; grids over fixed M_BH  
  > "We fit models using the `amoeba` downhill simplex method implemented in IDL." (4.4 Model Optimization)
   - software: IDL amoeba
   - parameter: Free: M_BH, Upsilon, x, y, v_sys, i, Gamma, f0, sigma_turb params  
  > "Free parameters in the model include $M_\mathrm{BH}$ and $\Upsilon$, the $x$ and $y$ centroid positions of the BH, the systemic velocity $v_\mathrm{sys}$" (4.1 Method)
   - fitting: chi^2 with noise from block-averaged blank regions (0.3 mJy/beam); covariance matrix attempt failed  
  > "The RMS noise level in the $4\times4$ block-averaged data is 0.3 mJy beam$^{-1}$" (4.4 Model Optimization)
   - validation: Compared full-resolution chi^2, PVD fits, HST mass profile  
  > "the results for the best-fitting parameters were virtually identical to the block-averaged fits" (5.1 Initial tests)

## Software

- **CASA** 4.2.2, r30721: Data processing and imaging  
  > "version 4.2.2, r30721 of the Common Astronomy Software Application" (2 Observations)
- **IRAF** : Richardson-Lucy deconvolution; STSDAS crrej  
  > "implemented in IRAF" (4.1 Method)
- **MGE_FIT_SECTORS** : MGE fit of HST F814W surface brightness  
  > "using the `MGE_FIT_SECTORS` package (cite: cappellari2002)" (4.2 Stellar Mass Profile)
- **Tiny Tim** : Synthetic WFPC2 PSF  
  > "synthetic PSF generated using Tiny Tim (cite: krist2011)" (4.2 Stellar Mass Profile)
- **amoeba (IDL)** : Downhill simplex chi^2 minimization  
  > "We fit models using the `amoeba` downhill simplex method implemented in IDL." (4.4 Model Optimization)
- **kinemetry** : Harmonic expansion of v_LOS  
  > "we used the kinemetry method of (cite: krajnovic2006)" (3 CO emission properties and disk kinematics)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum flux density | 8.75 | ±0.04 (plus 10% flux scale) | mJy | 1 | flux density $8.75 \pm 0.04$ mJy |
| Total CO(2-1) flux | 37.7 | ±0.3 (plus 10% flux scale) | Jy km/s | 1 | The total CO(2-1) flux of the disk is $37.7\pm0.3$ Jy km s$^{-1}$ |
| Molecular gas mass | 5.0e7 | ±0.5e7 | Msun | 3 | $M_\mathrm{gas} = \ensuremath{\alpha_\mathrm{CO}}L^{\prime}_\mathrm{CO(1-0)} =
(5.0\pm0.5)\times10^7$ |
| Best flat-sigma M_BH | 6.02e8 | not meaningful (chi2_nu=4.40) | Msun | 5 | The best-fitting model with flat $\sigma_\mathrm{turb}$ is found at $\ensuremath{M_\mathrm{BH}}=
6.02\times10^8$ ${M}_{\odot}$. |
| Best-fit flat sigma_turb | 24.7 | not stated | km/s | 5 | $\Upsilon_R = 7.25$ and $\ensuremath{\sigma_\mathrm{turb}}= 24.7$ km s$^{-1}$ |
| Disk inclination | 83-84 | not stated | deg | 5 | inclination $i = 83\ensuremath{^\circ}-84\ensuremath{^\circ}$ |
| Systemic velocity | 1559 | ±1 | km/s | 5 | $\ensuremath{v_\mathrm{sys}}= 1559\pm1$ km s$^{-1}$ |
| Provisional BH mass range | ~(4-8)e8 | not rigorous | Msun | 5 | point to a BH mass that is likely to be in the range $\sim(4-8)\times10^8$ ${M}_{\odot}$ |
| BH mass with sigma_turb=10 km/s | 8.0e8 | not stated | Msun | 5 | For $\ensuremath{\sigma_\mathrm{turb}}=10$ km s$^{-1}$, the best-fitting BH mass is $8.0\times10^8$ ${M}_{\odot}$. |
| Gaussian sigma_turb model chi2 (M_BH=0) | 7499.7 for 2538 dof | not stated | dimensionless | 5 | the best-fitting $\chi^2$ value in this case is 7499.7 for 2538 degrees of freedom |
| Radius of influence | 24 | not stated | pc | 0 | the kinematic definition of the radius of influence gives $r_g = 24$ pc |

## Qualitative findings

- CO disk is in orderly rotation with a mild kinematic twist and a central upturn in maximum velocity  
  > "We find evidence for a disk in orderly rotation with evidence for a mild kinematic twist" (7 Conclusions)

## Claim tuples

- H: Can the ALMA Cycle 2 data tightly constrain M_BH? | E: Fit forward models to the cube with flat, exponential and Gaussian sigma_turb | R: Flat gives 6.0e8; radial profiles drive M_BH to 0 with unphysical sigma; limited sigma<50 km/s gives (4-8)e8 | F: M_BH is degenerate with the turbulent dispersion profile; only a provisional (4-8)e8 Msun | **supported**
- H: Is M_BH consistent with the stellar-dynamical value of 1.45e9? | E: Compare chi2 for models with M_BH fixed near 1.45e9 | R: chi2 rises steeply above 1e9 | F: Rusli et al. value disfavored; agrees with X-ray value | **supported**
- H: What resolution criterion is needed for gas-dynamical BH measurement in inclined disks? | E: Beam-smearing analysis of kinemetry vs model v_circ | R: r_g cos i = 0.027'' vs 0.27'' beam | F: r_g should be resolved along the minor axis | **supported**

## Reasoning

- Why this data: Cycle 2 CO(2-1) at ~0.3'' to test for rapid rotation within the BH sphere of influence in a dust-disk ETG  
  > "The first stage of this program involves observations of the CO(2–1) line at $\sim0.3\ensuremath{''}$ resolution to search for evidence of rapid rotation within the BH sphere of influence." (1 Introduction)
- Why this method: _not stated_
- Alternative: Covariance-matrix chi2 attempted but numerically unstable, so used 4x4 block averaging  
  > "We found that numerical errors in constructing and inverting the covariance matrix rendered the $\chi^2$ calculation highly unstable." (4.4 Model Optimization)
- Alternative: HST I-band mass profile rejected due to dust extinction  
  > "We therefore choose to use the (cite: rusli2011) profile for our final model fits." (4.2 Stellar Mass Profile)
- How they decided it was enough: _not stated_
- Limitation (authors): Models are poor fits (chi2_nu 4.4); warp, sigma_turb and surface brightness models inadequate; no meaningful confidence intervals  
  > "We are unable to derive meaningful confidence limits on $M_\mathrm{BH}$" (5.5 Final Results)
- Caveat (inferred, ours): The result depends on the chosen sigma_turb parametrization and the ad hoc 50 km/s cap
- Caveat (inferred, ours): Richardson-Lucy deconvolved flux map with 5 iterations is arbitrary
- Caveat (inferred, ours): Noise correlation handled by block averaging, not rigorous
- Caveat (inferred, ours): Stellar profile taken from the literature, not varied in shape

## Reproducibility

- Data public (paper): ALMA program 2013.1.00229.S named; HST archival image  
  > "This paper makes use of data from ALMA program 2013.1.00229.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Custom IDL modeling code not released
- Missing: Rusli et al. mass profile provided privately
- Missing: Line-free channel and clean settings
- Missing: Exact fit-region definition
- Data volume (inferred): ~1-3 GB (one EB, 60-channel cube)
- Score (inferred): 5/5, Data identifiable and recipe described in detail, but the custom code and the mass profile are not public and the result is not rigorous.
- Rediscovery candidate: no, Needs custom forward-modeling code and a privately provided mass profile; the main result is a loose range.

## Links

- Method: (cite: krajnovic2006) (Kinemetry method)
- Method: (cite: cappellari2002) (MGE fitting)
- Companion: (cite: rusli2011) (Stellar-dynamical M_BH and mass profile)
- Companion: (cite: humphrey2009) (X-ray M_BH)
- Related: ALMA Cycle 2 ETG black hole program
- Related: ALMA Cycle 3 0.04'' follow-up of NGC 1332

## Checks

```json
{
 "quotes": 70,
 "quotes_ok": 70,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2013.1.0229.S"
 ],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 81,
  "stated": 51,
  "rate": 0.63
 },
 "evidence_ok": true
}
```
