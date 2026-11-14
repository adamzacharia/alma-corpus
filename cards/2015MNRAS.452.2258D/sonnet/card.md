# Revealing the complex nature of the strong gravitationally lensed system H-ATLAS J090311.6+003906 using ALMA

`2015MNRAS.452.2258D` | Monthly Notices of the Royal Astronomical Society 2015 | first author: Dye, S. | arXiv: 1503.08720 | DOI: 10.1093/mnras/stv1442

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: high_z_galaxies
- Question: What are the physical properties (dust, gas, kinematics, star formation) of the lensed SMG SDP.81, and how does the ALMA-reconstructed submm emission relate to the HST near-IR emission?  
  > "The purpose of this paper is to exploit the high resolution ALMA imaging of the highly magnified lensed source to determine its physical properties." (1 INTRODUCTION)
- Target **H-ATLAS J090311.6+003906 (SDP.81)**: coordinates _not stated_; z/distance z = 3.042  
  > "reconstructed the distribution of band 6 and 7 continuum emission in the z = 3.042 source" (abstract); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00016.SV
- bands: Bands 4, 6, 7  
  > "using between 22 and 36 12 m-diameter antennas and ALMA's band 4, 6 & 7 receivers." (2.1 ALMA data)
- frequencies and spectral setup: Four 1.875 GHz spectral windows per band, 7.5 GHz total; one or two cover a line, rest continuum  
  > "Four 1.875 GHz bandwidth spectral windows were used, over a total bandwidth of 7.5 GHz." (2.1 ALMA data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: CO uv-tapered to ~170 mas (1000 kλ); beams 155×121 mas (CO(5-4)), 169×117 mas (CO(8-7))  
  > "155×121 mas and 169×117 mas for CO(5-4) and CO(8-7), respectively." (2.1 ALMA data)
- max recoverable scale: _not stated_
- sensitivity: RMS 0.20 mJy (CO(5-4)) and 0.15 mJy (CO(8-7)) per 21 km/s channel  
  > "The resulting RMS noise levels are 0.20 mJy and 0.15 mJy per 21 kms −1 channel for CO(5-4) and CO(8-7) respectively." (2.1 ALMA data)
- time on source: _not stated_
- observing dates: October 2014, Long Baseline Campaign  
  > "SDP.81 was observed in October 2014 as part of ALMA's Long Baseline Campaign" (2.1 ALMA data)
- pi or archival as stated: _not stated_
- Line: CO 5-4 (576.267 GHz)
- Line: CO 8-7 (921.799 GHz)
- Line: CO 10-9 (1151.985 GHz)
- Other facility **HST/WFC3 F160W**: Near-IR imaging, 4418 s, reanalysed  
  > "deeper F160W image which has a total exposure time of 4418 s" (2.2 Near-IR data)
- External data: Continuum photometry of the lensed source (table 2 of N14) used in SED fit  
  > "to the fluxes from table 2 in N14 (but de-magnified using our derived continuum source magnification factor)" (Figure 6 caption) [from Negrello et al. 2014]
- External data: CO(1-0) spectroscopic data  
  > "using the CO(1-0) spectroscopic data acquired by Valtchanov et al. (2011)" (4.4.2 CO(1-0) gas) [from Valtchanov et al. (2011)]

## Processing

### Calibration

- pipeline or manual: Calibration and imaging per ASP scripts, using CASA  
  > "The calibration and imaging of the data is described in the scripts provided on the ASP." (2.1 ALMA data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: ASP calibrated data/cubes used; own imaging found ASP data already optimal  
  > "We attempted a variety of different tapers and cleaning parameters but found the ASP data to be already optimal for our purposes." (2.1 ALMA data)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: robust=1  
  > "A robust=1 weighting of the visibilities was used." (2.1 ALMA data)
- uv taper: CO to ~170 mas (1000 kλ); H2O 200 kλ  
  > "were uv-tapered to a resolution of ∼170 mas (1000 kλ)" (2.1 ALMA data)
- cell size: Continuum binned from 0.005" to 0.01" pixels  
  > "we binned the band 6 and band 7 continuum images from a pixel scale of 0.005 ′′ to a pixel scale of 0.01 ′′ ." (2.1 ALMA data)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Line-free channels used for CO  
  > "Line-free channels were used to subtract the continuum emission from the CO data." (2.1 ALMA data)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Calibration and imaging from ASP scripts / ALMA Partnership paper  
  > "more details can be found in ALMA Partnership, Vlahakis et al. (2015)." (2.1 ALMA data) [from ALMA Partnership, Vlahakis et al. (2015)]
- Semi-linear inversion lens modelling with adaptive source grid  
  > "We used the latest implementation of the semi-linear inversion method (Warren & Dye 2003) as described by Nightingale & Dye (2015)." (3.1 Lens modelling procedure) [from Warren & Dye 2003; Nightingale & Dye (2015)]
- MCMC dynamical fitting code  
  > "fitted the two dimensional dynamics using an MCMC code (see Swinbank et al. 2012, for further details)" (4.3.1 Dynamical modelling) [from Swinbank et al. 2012]
- Dust opacity kappa_850=0.077 m2/kg for consistency  
  > "to be consistent with the fitting in N14" (4.4.1 Dust mass) [from N14]

### Not stated but needed to reproduce (our reading)

- MCMC priors, sampler and chain settings for kinematic fit
- Lens model mask definitions and priors/evidence sampler details
- Line-free channel ranges and CASA version used by ASP scripts
- Two-component SED model functional form and fitting priors
- Magnification-velocity mapping details for CO(1-0)

## Analysis recipe

1. **Lens model from continuum**: Image-plane semi-linear inversion with dual reconstruction of band 6 and 7 continuum; power-law elliptical mass plus external shear  
  > "using a dual reconstruction of the ALMA band 6 and band 7 continuum image data" (3.1 Lens modelling procedure)
   - software: Nightingale & Dye semi-linear code
   - parameter: 2×2 binned continuum to 0.01" pixels  
  > "our use of the 2 × 2 pixel binned version of the band 6 and band 7 science verification continuum image data" (3 LENS MODELLING)
   - assumption: Single smooth power-law profile, scale-invariant slope  
  > "we adopted a single smooth powerlaw profile with a volume mass density of the form ρ ∝ r −α" (3.1 Lens modelling procedure)
   - fitting: Most probable parameters from marginalising over Bayesian evidence  
  > "most probable lens model parameters identified by marginalising over the Bayesian evidence" (4.1 Lens model)
   - validation: Image-plane best fit checked in uv plane via MIRIAD uvmodel chi2; offset within uncertainties  
  > "although there is a slight offset in parameter space between the image plane minimum-χ 2 and the uv plane minimum-χ 2, this is within the parameter uncertainties" (3 LENS MODELLING)
2. **Reconstruct CO cubes and moment maps**: Apply best lens model to each channel of CO cubes; moment maps with immoments  
  > "We used our best fit lens model to reconstruct the distribution of flux in the source plane for each slice of the image data cubes" (4.3 CO emission and source kinematics)
   - software: CASA
   - parameter: CO(5-4) channels 31-61; CO(8-7) channels 30-60  
  > "stacking over channels 31 to 61 inclusive" (4.3 CO emission and source kinematics)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit disk dynamics**: 2D velocity-field model of Freeman disk plus Burkert halo, MCMC  
  > "we fitted a two dimensional model whose velocity field is described by a combination of stars and gas" (4.3.1 Dynamical modelling)
   - software: MCMC code (Swinbank et al. 2012)
   - parameter: Dynamical centre within 0.5 kpc of band 7 continuum centroid  
  > "We constrained the [x / y] dynamical centre to be within 0.5 kpc of the band 7 continuum centroid" (4.3.1 Dynamical modelling)
   - assumption: Disk rotation; no asymmetric drift correction  
  > "a correction for asymmetric drift need not be applied to the inferred dynamical mass" (4.3.1 Dynamical modelling)
   - fitting: MCMC; priors not stated  
  > "then fitted the two dimensional dynamics using an MCMC code (see Swinbank et al. 2012, for further details)" (4.3.1 Dynamical modelling)
   - validation: Residual velocity maps and rotation curves compared  
  > "The best-fit kinematic maps and velocity residuals are shown in Figure 4." (4.3.1 Dynamical modelling)
4. **Dust mass, FIR luminosity, gas mass**: Two-component modified blackbody SED fit to de-magnified fluxes; gas mass via gas-to-dust ratio  
  > "fitting a two-component spectral energy distribution (SED) model to a combination of our measured band 6 and band 7 continuum fluxes" (4.4.1 Dust mass)
   - parameter: kappa_850 = 0.077 m2/kg  
  > "κ 850µm = 0.077 m 2 kg −1" (4.4.1 Dust mass)
   - assumption: gas to dust ratio 150  
  > "Assuming a typical gas to dust ratio of 150" (4.4.1 Dust mass)
   - fitting: _not stated_
   - validation: Tested fixed beta=2 and with/without 160 µm flux; dust mass 1.8-2.1e8  
  > "returned a dust mass in the range (1.8 − 2.1) × 10 8 M ⊙" (4.4.1 Dust mass)
5. **CO(1-0) gas mass**: De-magnify Valtchanov CO(1-0) spectrum using velocity-dependent magnification from CO(5-4) lens reconstruction; alpha_CO=1  
  > "we used the CO luminosity to molecular gas mass conversion factor from Bothwell et al. (2013) of α CO = 1" (4.4.2 CO(1-0) gas)
   - parameter: Fixed magnification of 3 at extreme velocities  
  > "we assumed a fixed magnification of 3 in these extremes" (4.4.2 CO(1-0) gas)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibration/imaging (ASP scripts) and immoments moment maps  
  > "These were made using CASA immoments" (4.3 CO emission and source kinematics)
- **MIRIAD** : uvmodel to simulate visibilities for uv-plane check  
  > "using MIRIAD uvmodel to produce a simulated visibility dataset" (3 LENS MODELLING)
- **GALFIT** : Lens galaxy light removal in HST data  
  > "using the GALFIT software (Peng et al. 2002)" (2.2 Near-IR data)
- **TinyTim** : HST PSF  
  > "a point spread function created by the TinyTim software package (Krist 1993)" (2.2 Near-IR data)
- **IRAF MultiDrizzle** : HST image reduction  
  > "The image was reduced using the IRAF MultiDrizzle package" (2.2 Near-IR data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Disk inclination | 40 | ±5 | deg | 3 | The best fit disk inclination is (40 ± 5) ◦ |
| Intrinsic asymptotic rotation velocity | 320 | not stated | km/s | 3 | corresponds to an intrinsic asymptotic velocity of 320 kms −1 |
| Dynamical mass within 1.5 kpc | 3.5e10 | 0.5e10 | Msun | 3 | Dynamical mass within 1.5 kpc (3.5 ± 0.5) × 10 10 M ⊙ |
| Toomre Q | 0.3 | not stated | dimensionless | 3 | the resulting Toomre stability value is Q ≃ 0.3 |
| Continuum magnification | 15.9 | 0.7 | dimensionless | 1 | Total continuum magnification 15.9 ± 0.7 |
| CO(5-4) magnification | 13.7 | 0.6 | dimensionless | 2 | 13.7 ± 0.6 for the CO(5-4) flux and 13.1 ± 0.6 for the CO(8-7) flux |
| Dust mass | 1.8e8 | 0.3e8 | Msun | 4 | yielding a dust mass of (1.8 ± 0.3) × 10 8 M ⊙ |
| Gas mass from dust | 2.7e10 | 0.5e10 | Msun | 4 | total molecular gas mass of (2.7±0.5)×10 10 M ⊙ |
| Intrinsic FIR luminosity | 3.1e12 | 0.5e12 | Lsun | 4 | intrinsic far-infrared luminosity is (3.1 ± 0.5) × 10 12 L ⊙ |
| CO(1-0) luminosity | 3.5e10 | 0.6e10 | K km/s pc^2 | 5 | L ′ CO = (3.5 ± 0.6) × 10 10 K kms −1 pc 2 |
| Gas mass from CO | 3.5e10 | 0.6e10 | Msun | 5 | total molecular gas mass in the source of (3.5 ± 0.6) × 10 10 M ⊙ |
| Star formation rate | 470 | 80 | Msun/yr | 4 | the star-formation rate in this object is ∼ 470 ± 80 M ⊙ /yr |

## Qualitative findings

- Dust continuum is clumpy on ~200 pc scales while CO shows smooth disk-like velocity field  
  > "The continuum imaging reveals a highly non-uniform distribution of dust with clumps on scales of ∼ 200 pc." (abstract)
- ALMA disk is offset from the HST near-IR emission  
  > "there is a very distinct offset between the submm emission and the near-IR (rest frame blue) emission" (4.2 Source morphology)

## Claim tuples

- H: Is the SDP.81 source a rotating disk? | E: Fit disk+halo model to reconstructed CO velocity fields | R: Inclination 40±5 deg, v=320 km/s, Mdyn=3.5e10 Msun | F: Smooth disk-like rotation | **supported**
- H: Is the disk gravitationally unstable? | E: Toomre Q from surface density and dispersion | R: Q≈0.3 | F: Disk is collapsing, consistent with merger-induced starburst | **partially**
- H: Does submm emission align with the near-IR emission? | E: Reconstruct ALMA and HST sources with same lens model | R: ~1.5 kpc offset | F: Offset; scenarios include merger | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Image-plane modelling is more sensitive for the figure of merit and far more efficient than uv-plane  
  > "modelling in the image plane is vastly more efficient than working directly with the extremely large visibility dataset" (3 LENS MODELLING)
- Alternative: Pure SIE model fit the ring but had lower evidence  
  > "the model has a lower evidence (with ∆χ 2 ≃ 20) than the most probable model" (4.1 Lens model)
- How they decided it was enough: _not stated_
- Limitation (authors): Differential magnification neglected; large uncertainties in gas conversion factors  
  > "we have of course neglected any effects of differential magnification" (4.4.1 Dust mass)
- Limitation (authors): Image-plane pixel covariance ignored  
  > "image pixels are correlated by the beam which biases image plane modelling" (3 LENS MODELLING)
- Caveat (inferred, ours): Image-plane fit ignores pixel covariance so evidences are not strictly comparable
- Caveat (inferred, ours): Single power-law lens without substructure
- Caveat (inferred, ours): Gas masses depend strongly on assumed gas-to-dust ratio and alpha_CO
- Caveat (inferred, ours): Dynamical mass assumes disk geometry from a lensed, tapered cube

## Reproducibility

- Data public (paper): Science verification data on ALMA Science Portal  
  > "ALMA Science Verification data on SDP.81 were taken from the ALMA Science Portal [1] (ASP)." (2.1 ALMA data)
- Products in archive: _not stated_
- Missing: Lens-modelling code and MCMC priors
- Missing: Exact SED model setup
- Missing: CASA version and ASP script details
- Data volume (inferred): tens of GB (long-baseline Bands 4, 6, 7; ASP image cubes sufficient)
- Score (inferred): 5/5, Public data and processed cubes, but custom lens and kinematic codes with unstated priors.
- Rediscovery candidate: no, Key results depend on unreleased lens-modelling code and unspecified fit settings.

## Links

- Method: Nightingale & Dye (2015) (Adaptive semi-linear lens inversion)
- Method: Swinbank et al. 2012 (MCMC kinematic modelling)
- Companion: ALMA Partnership, Vlahakis et al. (2015) (Data overview)
- Companion: Rybak et al. (2015) (uv-plane lens modelling of same data)
- Related: H-ATLAS
- Related: ALMA Long Baseline Campaign

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
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 83,
  "stated": 50,
  "rate": 0.602
 },
 "evidence_ok": true
}
```
