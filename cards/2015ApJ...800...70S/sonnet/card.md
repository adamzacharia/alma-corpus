# ALMA Imaging of HCN, CS, and Dust in Arp 220 and NGC 6240

`2015ApJ...800...70S` | The Astrophysical Journal 2015 | first author: Scoville, Nick | arXiv: 1412.5183 | DOI: 10.1088/0004-637X/800/1/70

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, astrochemistry
- Question: What are the ISM masses, nuclear disk kinematics and dense-gas excitation conditions in the nuclei of Arp 220 and NGC 6240, from ALMA dust continuum and HCN/CS imaging?  
  > "This dynamical modeling yields total masses consistent with those derived from the dust continuum emission." (1.3. Probing the Nuclear Structure)
- Target **Arp 220**: coordinates West nucleus 698 GHz Gaussian peak: 15:34:57.217, +23:30:11.44 (J2000)  
  > "Arp 220 (L _IR_ = 2 _._ 5 _×_ 10 [12] L _⊙_, D _L_ = 77 Mpc, D _A_ = 74" (1. INTRODUCTION); "The adopted redshifts were _z_ = 0 _._ 01812 and" (2. ALMA OBSERVATIONS AND DATA REDUCTION); z/distance z = 0.01812; D_L = 77 Mpc, D_A = 74 Mpc  
  > "Arp 220 (L _IR_ = 2 _._ 5 _×_ 10 [12] L _⊙_, D _L_ = 77 Mpc, D _A_ = 74" (1. INTRODUCTION); "The adopted redshifts were _z_ = 0 _._ 01812 and" (2. ALMA OBSERVATIONS AND DATA REDUCTION); distance from _not stated_
- Target **NGC 6240**: coordinates 694 GHz Gaussian-fit peak: 16:52:58.898, +2:24:03.51 (J2000)  
  > "L _⊙_, D _L_ = 103 Mpc, D _A_ = 98 Mpc, 475 pc arcsec _[−]_ [1] ) are" (1. INTRODUCTION); z/distance z = 0.02448; D_L = 103 Mpc, D_A = 98 Mpc  
  > "L _⊙_, D _L_ = 103 Mpc, D _A_ = 98 Mpc, 475 pc arcsec _[−]_ [1] ) are" (1. INTRODUCTION); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00175.S
- bands: Band 7 (350 GHz) and Band 9 (696 GHz)  
  > "We report ALMA Band 7 (350 GHz) imaging at 0.4    - 0.6 _[′′]_ resolution and Band 9 (696 GHz) at" (abstract)
- frequencies and spectral setup: TDM, 4 spectral windows, 1875 MHz each, 31.25 MHz channels; Band 7 lines CS 7-6 and HCN 4-3 plus continuum window at 340.974 GHz; Band 9 HCN 8-7 and HCO+ 8-7 plus continuum windows at 707.3 and 711.0 GHz  
  > "Each window had a full bandwidth of 1875 MHz covered by 31.25 MHz resolution spectral channels." (2. ALMA OBSERVATIONS AND DATA REDUCTION)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: most extended Cycle 0 configuration; 16-21 antennas, one execution with 25  
  > "All observations were done in the most extended configuration available in Cycle 0." (2. ALMA OBSERVATIONS AND DATA REDUCTION); "Most of the data were taken with
configurations of 16 – 21 antennas, except one execution
block which had 25 antennas." (2. ALMA OBSERVATIONS AND DATA REDUCTION)
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: good flux recovery out to ~3 arcsec  
  > "good flux recovery is expected out to scales
of _∼_ 3 _[′′]_ and more extended emission will be partially
resolved out." (2. ALMA OBSERVATIONS AND DATA REDUCTION)
- sensitivity: Band 7 Arp 220: 1.1 (USB) and 1.7 (LSB) mJy/beam in 13 km/s channels; NGC 6240: 0.5 and 0.6 mJy/beam  
  > "For NGC 6240 we have a noise level of
_σ_ _≃_ 0 _._ 5 mJy beam _[−]_ [1] and 0 _._ 6 mJy beam _[−]_ [1] in the upper and lower sidebands in 13 km s _[−]_ [1] channels." (2. ALMA OBSERVATIONS AND DATA REDUCTION)
- time on source: Band 7: 140 min per source; Band 9: 32 min Arp 220, 75 min NGC 6240  
  > "whereas for the Band 9 observations, the total on-source
time was 32 minutes for Arp 220 and 75 minutes for NGC
6240." (2. ALMA OBSERVATIONS AND DATA REDUCTION)
- observing dates: 2012  
  > "The ALMA Cycle 0 observations for project
#2011.0.00175.S were obtained in 2012." (2. ALMA OBSERVATIONS AND DATA REDUCTION)
- pi or archival as stated: _not stated_
- Line: CS 7-6 (342.882 GHz)
- Line: HCN 4-3 (354.505 GHz)
- External data: Empirical calibration of ISM mass vs. RJ dust luminosity (alpha_850um) and RJ mass formula (Eqs. 2-4)  
  > "The use of the dust continuum is fully developed along with empirical calibration
of the flux to mass ratio in Scoville et al. (2014) and is
summarized briefly below." (4. LONG WAVELENGTH DUST CONTINUUM AS A MASS TRACER) [from Scoville et al. 2014]
- External data: Dust temperature and optical depth models for Arp 220 nuclei  
  > "Modeling the IR SED of Arp 220, Wilson et al. (2014) found
that the dust optical depth was _τ_ _∼_ 1 _._ 7 and 5.3 at 678
GHz" (4. LONG WAVELENGTH DUST CONTINUUM AS A MASS TRACER) [from Wilson et al. 2014]
- External data: HCN-He collision rate coefficients  
  > "The collision rate coefficients for HCN J=4 were taken
from the He-HCN rate coefficients calculated by Dumouchel et al. (2010)" (6.2. HCN (4 - 3) Excitation in Arp 220) [from Dumouchel et al. 2010]
- External data: CS and HCN summed collision rates  
  > "(using the tables given in Sch¨oier et al. (2005))" (6.2. HCN (4 - 3) Excitation in Arp 220) [from Schöier et al. 2005]
- External data: CO(2-1) fluxes of Arp 220 nuclei  
  > "CO (2   - 1) fluxes for the nuclei are
from Sakamoto et al. (1999)." (Table 6) [from Sakamoto et al. 1999]

## Processing

### Calibration

- pipeline or manual: Data re-reduced in CASA after delivery; original passband calibrator used  
  > "Following the delivery of data products, the data were
re-reduced and imaged using the Common Astronomy
Software Applications package (CASA)." (2. ALMA OBSERVATIONS AND DATA REDUCTION)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10% flux calibration uncertainty  
  > "Uncertainties on the line fluxes are taken to be the the larger of the
10% uncertainty in flux calibration or the measured rms noise." (Table 1)
- self calibration: Modest self-calibration to improve dynamic range  
  > "Modest selfcalibration was done to improve the dynamic range." (2. ALMA OBSERVATIONS AND DATA REDUCTION)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Image-plane subtraction in IDL: polynomial fit to line-free planes per pixel, endpoints linearly interpolated across line planes  
  > "This was done in IDL using our own software which fit a polynomial to line-free frequency planes for each spatial pixel," (2. ALMA OBSERVATIONS AND DATA REDUCTION)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: Arp 220 Band 7 ~0.60-0.52 x 0.42-0.39 arcsec; Band 9 0.32x0.28; NGC 6240 Band 7 0.54x0.45, Band 9 0.27x0.24  
  > "Arp 220
Band 7: 0 _._ 60 _−_ 0 _._ 52 _×_ 0 _._ 42 _−_ 0 _._ 39 _[′′]_ and Band 9: 0 _._ 32 _×_ 0 _._ 28 _[′′]_" (Figure 1 caption)
- final rms: Arp 220 342 GHz 1.26 and NGC 6240 340 GHz 0.248 mJy/beam; Band 9 11 and 1 mJy/beam  
  > "where _σ_ = 1 _._ 26 and 0 _._ 248
mJy beam _[−]_ [1],respectively for Arp 220 at 342 GHz and NGC 6240 at 340 GHz." (Figure 1 caption)

### Inherited from earlier work

- Dust-continuum ISM mass method and empirical alpha_850um calibration  
  > "The use of the dust continuum is fully developed along with empirical calibration
of the flux to mass ratio in Scoville et al. (2014)" (4. LONG WAVELENGTH DUST CONTINUUM AS A MASS TRACER) [from Scoville et al. 2014]
- Kinematic deconvolution maximum-likelihood algorithm  
  > "We used the same algorithm described in Scoville et al. (1983), with the addition of an external computation
loop" (A. KINEMATIC MODELING AND DECONVOLUTION) [from Scoville et al. 1983]
- Two-level excitation with photon trapping  
  > "Here, we extend the 2-level analytic
treatment in Scoville & Solomon (1974)" (6. HIGH EXCITATION GAS TRACED IN HCN AND CS) [from Scoville & Solomon 1974]

### Not stated but needed to reproduce (our reading)

- Imaging parameters (tclean/clean weighting, robust, cell, image size, masks, deconvolver)
- CASA version and self-calibration solution intervals/reference antennas
- Flux calibrator and bandpass/phase calibrators
- Line-free channel ranges and polynomial order for continuum subtraction
- Chi-square minimization algorithm details and uncertainties on disk model parameters (Table 5)
- Radial binning/aperture and how velocity profiles were compared in the fit
- IDL continuum-subtraction code not provided

## Analysis recipe

1. **Reduce and image data**: Re-reduction in CASA, modest self-calibration, image-plane continuum subtraction  
  > "we chose to use the original passband calibrator and then
did continuum subtraction in the image plane." (2. ALMA OBSERVATIONS AND DATA REDUCTION)
   - software: CASA, IDL
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure continuum and line fluxes and source sizes**: Circular aperture photometry and simultaneous 2D elongated Gaussian fits; moment integrals over ±500 km/s; beam analytically deconvolved  
  > "We also computed least squares fits of elongated Gaussians to the observed brightness distributions and the fit
parameters are given in Tables 2 and 3." (3.3. Measurements and Source Components)
   - parameter: moments over V = ±500 km/s without S/N clipping  
  > "calculated as simple moment integrals over
_V_ = _±_ 500km s _[−]_ [1] (without a signal-to-noise clipping
threshold for the 3d pixels)" (3.2. Lines)
   - fitting: least squares Gaussian fits  
  > "We also computed least squares fits of elongated Gaussians to the observed brightness distributions and the fit parameters are given in Tables 2 and 3." (3.3. Measurements and Source Components)
   - validation: Compared with single-dish SCUBA fluxes and peak positions of earlier studies  
  > "The peak positions all agree to within 0.2 _[′′]_ ." (3.1. Continuum)
3. **Derive ISM masses from RJ dust continuum**: Eq. 4 RJ-correction and empirical alpha_850um mass-flux relation using 347.6 GHz fluxes for Arp 220 and 693.5 GHz for NGC 6240  
  > "ISM masses derived from the RJ continuum flux using Equation 4 with distances of 74 and 103
Mpc for Arp 220 and NGC 6240." (Table 4)
   - parameter: Td = 100 K (Arp 220), 25 K (NGC 6240); beta = 1.8  
  > "For the Arp 220 nuclei we therefore use the
350 GHz fluxes and adopt T _d_ = 100 K." (4. LONG WAVELENGTH DUST CONTINUUM AS A MASS TRACER)
   - assumption: Optically thin dust, empirical dust-opacity/gas-to-dust absorbed in alpha_850um, uniform spherical/disk distribution for column density  
  > "assuming a
uniform, spherical distribution of ISM (see Table 4)." (4. LONG WAVELENGTH DUST CONTINUUM AS A MASS TRACER)
   - fitting: _not stated_
   - validation: Compared with CO-based masses; uncertain by factor of at most 2  
  > "we expect these estimates to
be uncertain by a factor of at most 2 for the nuclear" (4. LONG WAVELENGTH DUST CONTINUUM AS A MASS TRACER)
4. **Model nuclear disk kinematics and HCN emissivity**: Maximum-likelihood kinematic deconvolution fit of a disk model with 3-part rotation curve and 30 radial emissivity bins to HCN(4-3) line profiles  
  > "The radial emissivity function was taken to be
a step function in radius (R) with 30 equal width bins
in R with no imposed continuity between adjacent radial
bins." (5. NUCLEAR DISK MODELS)
   - parameter: free: V0, R0, sigma_v, inclination, PA, emissivity per bin  
  > "The parameters to be solved for are: the velocity dispersion _σ_ _v_ of the gas; the inclination i of the disk; the
PA of the major axis of the disk and the radial emissivity
function." (5. NUCLEAR DISK MODELS)
   - assumption: Axisymmetry, no radiative transfer  
  > "acceptable given the simplified assumptions
of the model – axisymmetry and no radiative transfer
considerations." (5. NUCLEAR DISK MODELS)
   - fitting: Chi-square minimization of model vs observed line profiles with external loop over rotation curve parameters  
  > "varying rotation curve parameters to minimize the overall _χ_ [2] of the observed line profiles" (A. KINEMATIC MODELING AND DECONVOLUTION)
   - validation: Visual agreement with spectra; dynamical masses compared with dust masses  
  > "the general agreement between the model and observed
spectra is acceptable given the simplified assumptions" (5. NUCLEAR DISK MODELS)
5. **Derive dynamical mass, disk thickness, mean density**: Eq. 5 for M(R) from Vrot and sigma_v; hydrostatic thickness Eq. 6 or self-gravitating Eq. 7; density from mass and thickness  
  > "For the combination of circular orbital motions and uniform random motions, an approximate dynamical mass is obtained from" (5. NUCLEAR DISK MODELS)
   - assumption: Mass surface density divided by 1.36 to remove He  
  > "The mass surface density was divided by a factor 1.36 to remove the He mass
contribution." (Figure 9 caption)
   - fitting: _not stated_
   - validation: Consistency with dust-based masses  
  > "This dynamical modeling yields total masses consistent with those derived from the dust continuum emission." (1.3. Probing the Nuclear Structure)
6. **Constrain gas density from HCN and CS excitation**: Analytic two-level excitation with photon trapping, matching observed Tx/Tk (0.4 for HCN, 0.1 for CS)  
  > "For the adopted molecular abundances the
required densities are _n_ _H_ 2 = 2 _._ 0 and 3 _._ 0 _×_ 10 [5] cm _[−]_ [3] for
HCN and CS." (6.4. Densities required for the Observed Emission)
   - software: RADEX
   - parameter: Tk = 100 K; dv/dr ~ 4 km/s/pc; X_HCN ~ 2e-8; X_CS ~ 5e-9  
  > "we adopt a gas kinetic temperature T _k_ = 100
K, based on the dust blackbody-limit temperature" (6.2. HCN (4 - 3) Excitation in Arp 220)
   - assumption: Optically thick lines, single excitation temperature, Galactic abundances  
  > "Assuming the line is optically thick (as in Galactic sources), these brightness temperatures imply excitation temperatures" (6.2. HCN (4 - 3) Excitation in Arp 220)
   - fitting: _not stated_
   - validation: Densities within 10% of full multilevel code such as RADEX  
  > "The densities derived from this analytic
2-level treatment are within 10% of those derived using
a full multilevel code such as RADEX." (6.4. Densities required for the Observed Emission)

## Software

- **CASA** : Re-reduction and imaging  
  > "the data were
re-reduced and imaged using the Common Astronomy
Software Applications package (CASA)." (2. ALMA OBSERVATIONS AND DATA REDUCTION)
- **IDL** : Custom image-plane continuum subtraction  
  > "This was done in IDL using our own software" (2. ALMA OBSERVATIONS AND DATA REDUCTION)
- **RADEX** : Cited comparison for multilevel excitation  
  > "within 10% of those derived using
a full multilevel code such as RADEX." (6.4. Densities required for the Observed Emission)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ISM mass Arp 220 East | 1.9e9 | factor of at most 2 | Msun | 3 | Arp 220 East 347.6 161 100 0.917 1.9 |
| ISM mass Arp 220 West | 4.2e9 | factor of at most 2 | Msun | 3 | Arp 220 West 347.6 342 100 0.917 4.2 |
| ISM mass NGC 6240 | 1.6e9 | factor of at most 2 | Msun | 3 | 1.6 _×_ 10 [9] M _⊙_ within radii of 69, 65 and 190 pc. |
| Total flux Arp 220 at 345 GHz / 698 GHz | 490 mJy / 4.51 Jy | not stated | mJy, Jy | 2 | The
total fluxes measured for Arp 220 and NGC 6240 are 490
and 20 mJy at 345 GHz and 4.51 and 0.126 Jy at 698 GHz |
| HCN(4-3) flux Arp 220 West | 231 | 23 | Jy km/s | 2 | Arp 220 West 1.2 HCN(4 - 3) 231 _±_ 23 |
| Disk model Arp 220 East (V0, R0, incl, PA, sigma_v) | 350 km/s, 30 pc, 71 deg, 47 deg, 90 km/s | not stated | mixed | 4 | Arp 220 East 350 30 71 47 90 |
| Disk model Arp 220 West (V0, R0, incl, PA, sigma_v) | 360 km/s, 40 pc, 64 deg, -15 deg, 90 km/s | not stated | mixed | 4 | Arp 220 West 360 40 64 -15 90 |
| Required gas density from HCN and CS | 2.0e5 and 3.0e5 | not stated | cm^-3 | 6 | the
required densities are _n_ _H_ 2 = 2 _._ 0 and 3 _._ 0 _×_ 10 [5] cm _[−]_ [3] for
HCN and CS. |
| Dynamical mass Arp 220 nuclei | ~7e8 at R=20 pc; ~3e9 at R=100 pc | not stated | Msun | 5 | the dynamical
masses are _∼_ 7 _×_ 10 [8] M _⊙_ at R = 20 pc and _∼_ 3 _×_ 10 [9] |
| Line optical depths HCN(4-3) and CS(7-6) | ~130 and 3 | not stated | dimensionless | 6 | The optical depths corresponding to the solution densities are _∼_ 130 and 3 for the HCN (4 -3) and CS (7
- 6) lines |

## Qualitative findings

- Dust and gas in Arp 220 are concentrated at R < 50 pc in both counter-rotating nuclear disks; in NGC 6240 gas lies along a ridge between the nuclei.  
  > "In Arp 220, the major dust and
gas concentrations are at radii less than 50 pc in both counter-rotating nuclear disks." (abstract)
- Effective CO-to-H2 conversion factor in Arp 220 nuclei is about a factor 2 below the Galactic value.  
  > "we conclude that the effective CO-to-H2 conversion factor in the Arp 220 nuclei is approximately a factor
2 reduced from the standard Galactic value." (7.1. CO-to-H2 conversion factor)

## Claim tuples

- H: Do dust-based ISM masses agree with dynamical masses in the nuclei? | E: RJ dust masses vs maximum-likelihood HCN disk modeling | R: Masses ~2e9 Msun dust vs consistent dynamical masses | F: Dust and dynamical masses are consistent. | **supported**
- H: Is the dense gas in Arp 220 clumpy? | E: Compare excitation densities with mean density from mass and size | R: nH2 ~2e5 vs mean ~1e5 cm^-3 | F: Volume is essentially filled with dense gas. | **supported**
- H: Does the Galactic CO conversion factor hold in Arp 220 nuclei? | E: Compare CO(1-0)-based masses with dust masses | R: CO masses 2-3 times higher | F: alpha_CO reduced by ~2. | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Long-wavelength dust is a linear ISM mass probe avoiding CO uncertainties.  
  > "Thus the long wavelength dust continuum can be used as a linear probe of the ISM mass" (4. LONG WAVELENGTH DUST CONTINUUM AS A MASS TRACER)
- Alternative: Using the weaker phase calibrator for passband calibration was attempted and abandoned.  
  > "After attempting to use the
much weaker phase calibrator for passband calibration,
we chose to use the original passband calibrator" (2. ALMA OBSERVATIONS AND DATA REDUCTION)
- How they decided it was enough: _not stated_
- Limitation (authors): Single dust temperature adopted; dust temperature not derivable from the data; masses uncertain by factor of 2.  
  > "A
good derivation of the dust temperature from the observations would require multiple spectral bands" (4. LONG WAVELENGTH DUST CONTINUUM AS A MASS TRACER)
- Limitation (authors): Only ~15% of single-dish flux recovered in NGC 6240.  
  > "Here, the detected
percentages are only _∼_ 15%." (3.1. Continuum)
- Caveat (inferred, ours): Dust masses depend on assumed Td and alpha_850; optical depth in Band 7 for Arp 220 not fully excluded
- Caveat (inferred, ours): Kinematic fit gives no uncertainties and ignores radiative transfer
- Caveat (inferred, ours): Disk sizes smaller than the beam are poorly constrained
- Caveat (inferred, ours): Two-level excitation assumes single Tx and Galactic abundances

## Reproducibility

- Data public (paper): Cycle 0 ALMA project data cited in acknowledgments  
  > "This paper makes use of the following ALMA data:
ADS/JAO.ALMA# 2011.0.00175.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: Continuum-subtraction code/channels
- Missing: Fit code and uncertainties
- Missing: Calibrator details
- Data volume (inferred): ~50-200 GB raw Cycle 0 data
- Score (inferred): 3/5, Public data and clear dust-mass formulas, but imaging and fitting details missing and fit code custom.
- Rediscovery candidate: no, Imaging and kinematic modeling details are not complete enough to redo without custom code.

## Links

- Method: Scoville et al. 2014 (dust continuum ISM mass calibration)
- Method: Scoville et al. 1983 (kinematic deconvolution algorithm)
- Companion: Wilson et al. 2014 (ALMA 691 GHz continuum of Arp 220 compared)

## Checks

```json
{
 "quotes": 77,
 "quotes_ok": 77,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 88,
  "stated": 57,
  "rate": 0.648
 },
 "evidence_ok": true
}
```
