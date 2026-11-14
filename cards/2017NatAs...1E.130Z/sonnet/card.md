# Mass inventory of the giant-planet formation zone in a solar nebula analogue

`2017NatAs...1E.130Z` | Nature Astronomy 2017 | first author: Zhang, Ke | arXiv: 1705.04746 | DOI: 10.1038/s41550-017-0130

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: What is the gas mass distribution, mid-plane temperature and gas-to-dust ratio in the giant-planet formation zone (5-21 AU) of the TW Hya disk, and how does it compare with the MMSN?  
  > "we directly constrain the mid-plane temperature and optical depths of gas and dust emission." (abstract)
- Target **TW Hya**: coordinates _not stated_; z/distance ~55 pc  
  > "TW Hya, at a distance of only$\sim$55 pc(cite: vanLeeuwen07)" (Main text); distance from van Leeuwen 2007  
  > "TW Hya, at a distance of only$\sim$55 pc(cite: vanLeeuwen07)" (Main text)

## Data provenance

- ALMA projects: 2015.1.00308.S
- bands: _not stated_
- frequencies and spectral setup: 3 line SPWs 117.2 MHz wide starting at 314.171, 329.319, 329.264 GHz; 0.23 km/s resolution; SPW 0 continuum  
  > "The three line SPWs are all 117.2 MHz wide and start at 314.171, 329.319 and 329.264 GHz, respectively." (ALMA observations.)
- continuum bandwidth: 1.875 GHz  
  > "The SPW 0 was used for continuum observations with a total bandwidth of 1.875 GHz." (ALMA observations.)
- arrays: 40 antennas  
  > "Observations were carried out on 2015 March 8, with 40 antennas and baselines of 15-460 m (16-492 k$\lambda$)." (ALMA observations.)
- configurations: _not stated_
- baselines: 15-460 m (16-492 kλ)  
  > "with 40 antennas and baselines of 15-460 m (16-492 k$\lambda$)" (ALMA observations.)
- angular resolution: 0.54" x 0.47", PA -87 deg (321 GHz continuum)  
  > "the synthesized beam is 0.54$^{\prime\prime}\times0.47^{\prime\prime}$, with a position angle of -87 degrees" (ALMA observations.)
- max recoverable scale: _not stated_
- sensitivity: C18O 6.5 mJy/beam per 0.23 km/s; 13C18O 4 mJy/beam  
  > "The C$^{18}$O line image cube has a noise level of 6.5 mJy beam$^{-1}$ in each 0.23 km s$^{-1}$ wide velocity bin" (ALMA observations.)
- time on source: 67.5 min  
  > "The total on-source integration time was 67.5 min." (ALMA observations.)
- observing dates: 2015 March 8  
  > "Observations were carried out on 2015 March 8" (ALMA observations.)
- pi or archival as stated: Cycle 3 proposal, PI Bergin  
  > "as a part of the Cycle 3 proposal 2015.1.00308.S (P.I. Bergin)" (ALMA observations.)
- Line: 13C18O J=3-2 (not stated)
- Line: C18O J=3-2 (not stated)
- Other facility **Herschel (HD 1-0)**: Previously detected HD 1-0 line flux used to scale abundance  
  > "The HD (1-0) line flux is (6.3$\pm$0.7)$\times$10$^{-18}$ W m$^{-2}$ at 112 $\mu$m(cite: Bergin13)." (Gas column density.)
- External data: HD (1-0) line flux (6.3±0.7)e-18 W m-2  
  > "The HD (1-0) line flux is (6.3$\pm$0.7)$\times$10$^{-18}$ W m$^{-2}$ at 112 $\mu$m(cite: Bergin13)." (Gas column density.) [from Bergin et al. 2013 (cite: Bergin13)]
- External data: 345 GHz continuum radial surface brightness profile  
  > "we employ the radial profile of surface brightness derived from the high spatial resolution dust continuum observations by Andrews et al. (2016)(cite: Andrews16)" (Parameterized disk model.) [from Andrews et al. 2016 (cite: Andrews16)]
- External data: 145 and 233 GHz radial brightness temperature profiles  
  > "We thank Takashi Tsukagoshi for sharing radial brightness temperature profiles of ALMA 145 and 233 GHz continuum observations of the TW Hya disk." (Acknowledgements) [from Tsukagoshi et al. 2016 (cite: Tsukagoshi16)]
- External data: Gas surface density model from scattered light (Model 2)  
  > "Model 2 is the gas surface density distribution derived by van boekel et al. (2016)(cite: vanBoekel16)" (CO snowline or jump in gas surface density.) [from van Boekel et al. 2016 (cite: vanBoekel16)]

## Processing

### Calibration

- pipeline or manual: ALMA staff pipeline calibration  
  > "The visibility data were calibrated by ALMA staff following standard procedures with the pipeline." (ALMA observations.)
- casa version: CASA 4.6.12  
  > "We further performed self-calibration on the calibrated data in phase and amplitude in CASA 4.6.12" (ALMA observations.)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1037-2934 (flux and phase); J1058+0133 bandpass  
  > "The nearby quasar J1058+0133 was used for bandpass calibration, and J1037-2934 for both flux and phase calibration." (ALMA observations.)
- flux scale uncertainty: _not stated_
- self calibration: Phase and amplitude self-cal on SPW 0 continuum, applied to line SPWs  
  > "The self-calibrated phase and gain solutions were then applied to the three line SPWs." (ALMA observations.)

### Imaging

- task: CLEAN  
  > "We generated synthesized images using a CLEAN deconvolution with a manual mask" (ALMA observations.)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "Briggs weighting with a robust parameter of 0.5" (ALMA observations.)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: manual mask  
  > "We generated synthesized images using a CLEAN deconvolution with a manual mask" (ALMA observations.)
- multiscale scales: _not stated_
- continuum subtraction: using line free channels  
  > "The data were subsequently continuum subtracted using line free channels." (ALMA observations.)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.54" x 0.47" at PA -87 deg (321 GHz continuum)  
  > "the synthesized beam is 0.54$^{\prime\prime}\times0.47^{\prime\prime}$, with a position angle of -87 degrees" (ALMA observations.)
- final rms: C18O 6.5 mJy/beam; 13C18O 4 mJy/beam  
  > "the $^{13}$C$^{18}$O line image cube has a noise level of 4 mJy beam $^{-1}$" (ALMA observations.)

### Inherited from earlier work

- Stellar mass, inclination, PA, V_LSR, inner radius, distance taken from literature  
  > "adopt stellar properties and disk inclination/position angle from the literature" (Parameterized disk model.) [from Table 2 refs: van Leeuwen 2007, Rosenfeld 2012, Qi 2004, Hughes 2011]
- HD-based abundance scaling follows Bergin et al. approach (LTE)  
  > "Following the approach in Bergin et al. (2013)(cite: Bergin13), we assume the HD (1-0) line is in LTE" (Gas column density.) [from Bergin et al. 2013 (cite: Bergin13)]
- Outer-disk gas temperature of 21 K  
  > "We use a constant temperature of 21 K for the CO isotopologues emission, as previously measured" (Parameterized disk model.) [from Schwarz et al. 2016 (cite: Schwarz16)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges used for continuum subtraction
- Self-calibration solution intervals and number of iterations
- Cell size, image size, CLEAN threshold and mask definition
- Exact mapping from CLEAN images to the visibilities fit (binning, weights)
- Burn-in and convergence criteria for MCMC
- Dust opacity law details beyond kappa(0.93 mm)=3.1 cm2/g
- Rest frequencies adopted
- Calibrator flux value and flux scale uncertainty

## Analysis recipe

1. **Calibrate and image**: Pipeline calibration, self-calibration on continuum, continuum subtraction, CLEAN imaging  
  > "We generated synthesized images using a CLEAN deconvolution with a manual mask (Briggs weighting with a robust parameter of 0.5)." (ALMA observations.)
   - software: CASA
   - parameter: robust 0.5  
  > "Briggs weighting with a robust parameter of 0.5" (ALMA observations.)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit parameterized 1D disk model to visibilities**: Isothermal slab model of 13C18O, C18O and dust inside the snowline, with Keplerian field; model cubes sampled at observed uv points and compared in visibility space  
  > "we carry out Fourier transforms on the model image cubes and retrieve the complex visibilities at the ($u,v$)-plane locations sampled by the ALMA observations" (Parameterized disk model.)
   - software: VIS_SAMPLE, emcee
   - parameter: v_turb fixed at 0.01 km/s; outer-disk T = 21 K; fixed stellar mass 0.6 Msun, i=7 deg, PA=155 deg  
  > "We fix $v_{\rm turb}$ at 0.01 km s$^{-1}$" (Parameterized disk model.)
   - assumption: Emission arises from mid-plane or adjacent regions characterized by one temperature; C18O/13C18O constant  
  > "The abundance ratio of C$^{18}$O/$^{13}$C$^{18}$O is assumed to be constant throughout the disk and modeled as a free parameter(cite: Miotello14)." (Parameterized disk model.)
   - fitting: emcee affine-invariant MCMC, uniform priors, 100 walkers, 1000 steps  
  > "Our chains consist of 100 walkers and 1000 steps." (Parameterized disk model.)
   - validation: Channel maps compared with best model; v_turb and fixed 12C/13C=69 tests  
  > "we also run models with a fixed $^{12}$C/$^{13}$C ratio of 69." (Comparison with previous models.)
3. **Derive gas surface density**: 13C18O column density in LTE scaled to HD 1-0 flux to get abundance, then gas mass  
  > "we assume the HD (1-0) line is in LTE and scale the $^{13}$C$^{18}$O column density to match the measured HD line flux." (Gas column density.)
   - parameter: D/H = 1.5e-5  
  > "the D/H ratio is well calibrated as 1.5$\times$10$^{-5}$" (Gas column density.)
   - assumption: HD and 13C18O abundance constant in warm region (T>20 K)  
  > "given $x_{\rm ^{13}C^{18}O}$ is a constant in the warm region throughout the disk" (Gas column density.)
   - fitting: Uncertainties propagated from model parameters and HD flux  
  > "Propagating uncertainties in our best-fitting parameters and in the HD (1-0) line flux" (Gas column density.)
   - validation: _not stated_
4. **Derive mm-dust mass and gas-to-dust ratio**: Dust optical depth converted to surface density with constant opacity  
  > "here we adopt a constant $\kappa$(0.93 mm) = 3.1 cm$^2$g$^{-1}$ to estimate the dust mass of grains no larger than millimeter." (Main text)
   - assumption: kappa consistent with a_max of 1 mm  
  > "We use a $\kappa$ consistent with a dust population with an a$_{\rm max}$ of 1 mm" (The gas-to-dust mass ratio and its uncertainty sources.)
   - fitting: _not stated_
   - validation: Compared with alternate gas models and sanity check on temperature assumption  
  > "Therefore the best-fit model is self-consistent in the treatment of the temperature." (Sanity check.)

## Software

- **CASA** 4.6.12: self-calibration, continuum subtraction, imaging  
  > "in CASA 4.6.12" (ALMA observations.)
- **VIS_SAMPLE** : sampling model visibilities at observed uv points  
  > "using the Python package VIS_SAMPLE" (Parameterized disk model.)
- **emcee** : MCMC posterior sampling  
  > "carried out by the affine-invariant routine EMCEE(cite: Foreman13)" (Parameterized disk model.)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mid-plane CO snowline radius | 20.5 | ±1.3 | AU | 2 | 20.5$\pm1.3$ |
| Temperature at snowline | 27 | +3/-2 | K | 2 | 27$^{+3}_{-2}$ |
| 12C/13C ratio | 40 | +9/-6 | dimensionless | 2 | We measure a $^{12}$C/$^{13}$C ratio of 40$^{+9}_{-6}$ |
| 13C18O abundance | 1.7e-10 | +1.3/-0.8 e-10 | relative to H2 | 3 | 1.7$^{+1.3}_{-0.8}\times$10$^{-10}$ |
| Gas surface density at 20.5 AU | 13 | +8/-5 | g cm-2 | 3 | $\Sigma_g$ = 13$^{+8}_{-5}\times$(R/20.5 AU)$^{-0.87^{+0.38}_{-0.26}}$ g cm$^{-2}$ |
| Surface density power-law index | -0.87 | +0.38/-0.26 | dimensionless | 3 | (R/20.5 AU)$^{-0.87^{+0.38}_{-0.26}}$ |
| Gas-to-mm-dust ratio (5-20.5 AU) | 140 | +43/-31 | dimensionless | 4 | we derive a total gas-to- dust ratio of 140$^{+43}_{-31}$ for the 5-20.5 AU region |
| Missing solid mass | 2.4 | +3.2/-2.0 | Earth masses | 4 | 2.4$^{+3.2}_{-2.0}$ M$_{\oplus}$ solid masses are missing |
| alpha radial index | 0.16 | ±0.39 | dimensionless | 4 | we find an $\alpha\propto r^{0.16\pm0.39}$ between 5-21 AU |

## Qualitative findings

- Gas mass distribution in TW Hya is much flatter than MMSN/MMEN  
  > "the mass distribution in TW Hya is much flatter in this region" (Main text)
- Gas jump is a CO snowline, not a gas surface density jump  
  > "the jump in CO gas column density is most likely caused by a mid-plane CO snowline" (CO snowline or jump in gas surface density.)

## Claim tuples

- H: 13C18O and C18O 3-2 constrain mid-plane temperature and CO snowline | E: Visibility-space MCMC fit of 1D disk model | R: Snowline 20.5±1.3 AU, T=27 K | F: First direct mid-plane CO snowline measurement in TW Hya | **supported**
- H: Gas-to-dust ratio in 5-21 AU is standard | E: Compared gas mass from 13C18O+HD to mm dust mass | R: Ratio 140 | F: At least 2.4 Earth masses of dust grown beyond cm size | **partially**
- H: MMSN is a suitable template for initial mass distribution | E: Compared measured profile to MMSN/MMEN | R: TW Hya profile much flatter | F: MMSN/MMEN should not be used as quantitative templates | **supported**

## Reasoning

- Why this data: 13C18O and C18O are far less abundant, so probe the mid-plane deeper  
  > "Their optical depths are correspondingly much smaller than the $^{12}$CO and $^{13}$CO lines, and thus can probe much deeper regions in protoplanetary disks." (ALMA observations.)
- Why this method: _not stated_
- Alternative: Gas surface density jump from dust-based models (Models 2 and 3) rejected  
  > "We find that neither models based on dust observations (Model 2 and 3) could reproduce the observed C$^{18}$O emissions." (CO snowline or jump in gas surface density.)
- How they decided it was enough: _not stated_
- Limitation (authors): 12C/13C ratio constrained by weak 13C18O emission; needs confirmation  
  > "The ratio is mostly constrained by the weak $^{13}$C$^{18}$O emission on the west side of the disk" (Comparison with previous models.)
- Limitation (authors): Dust opacity uncertainty from grain growth not included  
  > "we have not included the uncertainty of dust opacity due to dust growth" (The gas-to-dust mass ratio and its uncertainty sources.)
- Caveat (inferred, ours): Gas mass depends on single HD flux and assumed constant abundance
- Caveat (inferred, ours): 1D model with single temperature may bias results
- Caveat (inferred, ours): Single disk

## Reproducibility

- Data public (paper): Data available from corresponding author on request; ALMA project cited  
  > "are available from the corresponding author upon reasonable request." (Data Availability Statement)
- Products in archive: _not stated_
- Code: Only VIS_SAMPLE is linked; the disk model/fitting code is not stated as released  
  > "Available at <https://github.com/AstroChem/vis_sample>" (footnote)
- Missing: Model code
- Missing: Line-free channels and self-cal parameters
- Missing: Continuum profile from Andrews et al. 2016 and HD flux inputs
- Data volume (inferred): ~10-30 GB raw single-track Band 7 dataset
- Score (inferred): 3/5, Data identified and fit described, but the model code and several imaging parameters are not provided.
- Rediscovery candidate: no, Custom model code and external inputs are required.

## Links

- Method: Foreman-Mackey et al. 2013 (cite: Foreman13) (emcee sampler)
- Companion: Andrews et al. 2016 (cite: Andrews16) (high-resolution continuum profile used)
- Companion: Bergin et al. 2013 (cite: Bergin13) (HD 1-0 flux)

## Checks

```json
{
 "quotes": 71,
 "quotes_ok": 71,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 55,
  "rate": 0.705
 },
 "evidence_ok": true
}
```
