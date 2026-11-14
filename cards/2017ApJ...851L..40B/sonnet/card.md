# Spatially Resolved Kinematics in the Central 1 kpc of a Compact Star-forming Galaxy at z ∼2.3 from ALMA CO Observations

`2017ApJ...851L..40B` | The Astrophysical Journal Letters 2017 | first author: Barro, G. | arXiv: 1712.01283 | DOI: 10.3847/2041-8213/aa9f0d

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What are the resolved kinematics, dynamical mass and gas content in the central 1 kpc of a compact star-forming galaxy at z~2.3, and are they consistent with its baryonic mass?  
  > "The spatially resolved velocity map of the inner $r\lesssim1$ kpc reveals a continous velocity gradient consistent with the kinematics of a rotating disk" (abstract)
- Target **GDS-14876**: coordinates _not stated_; z/distance z = 2.309  
  > "assuming the redshift derived from optical lines ($z = 2.309$)" (Target selection and Observations); distance from optical emission lines  
  > "assuming the redshift derived from optical lines ($z = 2.309$)" (Target selection and Observations)

## Data provenance

- ALMA projects: 2015.1.00907.S
- bands: Band 7  
  > "The observations were conducted on 2016-09-17 in band 7 using four spectral windows in the largest bandwidth mode." (Target selection and Observations)
- frequencies and spectral setup: 4 spws of 1.875 GHz, 128 channels; centered 278.57 (CO 8-7), 276.91, 288.91, 290.91 GHz  
  > "The other spectral windows were centered at 276.91, 288.91, and 290.91 GHz." (Target selection and Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C39-7, extended  
  > "in an extended array configuration, C39-7" (Target selection and Observations)
- baselines: 15.1 m to 3.1 km  
  > "shortest and longest baselines were 15.1 m and 3.1 km, respectively" (Target selection and Observations)
- angular resolution: 0.14" x 0.12" (1.15 x 0.98 kpc), PA 70 deg  
  > "FWHM $=0.14\ensuremath{''}\times0.12\ensuremath{''}$ ($1.15\times0.98$ kpc)" (Target selection and Observations)
- max recoverable scale: _not stated_
- sensitivity: 0.19 mJy/beam per 20 km/s channel (CO); 28 uJy/beam continuum  
  > "The r.m.s. noise of the observations is 0.19 mJy/beam for the CO(8-7) line, measured in 20 km $s^{-1}$ channel bins" (Target selection and Observations)
- time on source: 51 min on source (~2 hr total)  
  > "The on-source integration time was $51$ min" (Target selection and Observations)
- observing dates: 2016-09-17  
  > "The observations were conducted on 2016-09-17" (Target selection and Observations)
- pi or archival as stated: _not stated_
- Line: CO J=8-7 (not stated)
- Other facility **HST ACS/WFC3**: imaging for stellar structure and SED (F160W)  
  > "We measure the structural properties of GDS-14876 in the F160W image" (Structural Properties)
- Other facility **Keck MOSFIRE**: [OIII] 5007 spectrum and sigma  
  > "The \[OIII\] profile is relatively narrow with a $\sigma=55\pm5$ km s$^{-1}$." (4.1 [OIII] kinematics)
- Other facility **Herschel, Spitzer, VLA**: far-IR and radio photometry for SED  
  > "we include far-IR data from *Spitzer* MIPS (cite: pg08b), *Herschel* PACS and SPIRE from the GOODS-Herschel survey" (Target selection and Observations)
- External data: Multiband U-8um photometry  
  > "extensive multi-band data ranging from U to 8$\mu$m (cite: guo13)" (Target selection and Observations) [from (cite: guo13)]
- External data: SFR log(SFR)=2.7  
  > "The SFR was determined in (cite: barro16b)" (Target selection and Observations) [from (cite: barro16b)]

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

- task: CASA tclean  
  > "We use the `tclean` task with natural weighting" (Target selection and Observations)
- deconvolver: _not stated_
- weighting robust: natural  
  > "We use the `tclean` task with natural weighting for the ` u-v` visibility plane." (Target selection and Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: CASA uvsubcont  
  > "we subtract the continuum flux from the image using CASA’s `uvsubcont` task" (Structural Properties)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.14" x 0.12"  
  > "average angular resolution of FWHM $=0.14\ensuremath{''}\times0.12\ensuremath{''}$" (Target selection and Observations)
- final rms: _not stated_

### Inherited from earlier work

- Continuum size fitting with GALFIT and synthetic ALMA beam PSF  
  > "Following (cite: barro16b), we use `GALFIT` and the synthetic PSF of the ALMA beam" (Structural Properties) [from (cite: barro16b)]
- MOSFIRE observations and reduction  
  > "A full description of the observations and data reduction in presented in (cite: barro14b)." (4.1 [OIII] kinematics) [from (cite: barro14b)]
- Inclination from axis ratio  
  > "following the method of (cite: dokkum15)" (4.2 CO kinematics) [from (cite: dokkum15)]

### Not stated but needed to reproduce (our reading)

- Flux, bandpass and phase calibrator names and calibration pipeline/CASA version
- Clean parameters: cell size, image size, mask, threshold, niter
- Line-free channels for continuum and how the CO line flux was measured
- Fitting priors, sampler setup and likelihood for the dynamical model
- Continuum frequency/wavelength used and its flux density
- Collapsed-cube mask and aperture for L'CO

## Analysis recipe

1. **Image continuum and CO cube**: CASA tclean, natural weighting  
  > "We use the `tclean` task with natural weighting for the ` u-v` visibility plane." (Target selection and Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure sizes**: GALFIT single Sérsic fits to F160W, continuum and collapsed CO image  
  > "Lastly, we run `GALFIT` on the resulting image, obtaining values of $r_{e}=0.67\pm0.05$ kpc and $n=0.9$." (Structural Properties)
   - software: GALFIT, CASA
   - parameter: CO collapsed over ±250 km/s  
  > "collapse the resulting data-cube in velocity space using a $\pm250$ km/s bin" (Structural Properties)
   - fitting: _not stated_
   - validation: _not stated_
3. **Dust-based gas mass**: Fit DL07 and modified blackbody models to FIR SED, apply gas-to-dust ratio  
  > "The best-fit models and the corresponding confidence intervals are computed by exploring the parameter space using the Python Markov-Chain Monte Carlo package ` emcee`" (4.1 Continuum-based measurement)
   - software: emcee
   - assumption: kappa=1 cm2/g at 850 um, beta=1.5-2.5, GDR~100  
  > "Here we assume the typical value for solar metallicity, $\delta_{\rm GDR}\sim100$." (4.1 Continuum-based measurement)
   - fitting: emcee MCMC; priors not stated  
  > "The best-fit models and the corresponding confidence intervals are computed by exploring the parameter space using the Python Markov-Chain Monte Carlo package ` emcee`" (Dust and gas masses, Continuum-based measurement)
   - validation: _not stated_
4. **CO-based gas mass**: L'CO from line flux, then M_gas = alpha_CO L'CO / R_81  
  > "We obtain $\log~L'_{\rm CO,
  8-7}=9.65\pm0.17$ dex." (4.2 CO-based measurement)
   - assumption: R_81=0.30±0.20; alpha_CO=0.8 (SMG) or 4.3 (MW)  
  > "Here we adopt a conservative value of $R_{8,1}=0.30\pm0.20$" (4.2 CO-based measurement)
   - fitting: _not stated_
   - validation: _not stated_
5. **Dynamical modeling of velocity field**: Per-spaxel single Gaussian fit for velocity/dispersion; forward model of thin Freeman disk with beam smearing and pressure support, spectra extracted along major axis  
  > "The dynamical model assumes that the ionized gas is rotating in a thin disk, and that the disk density profile can be described by a Freeman model" (4.2 CO kinematics)
   - parameter: Free parameters: M_dyn, r_e^dyn, sigma_0  
  > "The free parameters of the dynamical fit are three" (4.2 CO kinematics)
   - assumption: inclination 62 (+8/-15) deg from axis ratio q=0.82  
  > "we obtain $i=62^{\circ+8}_{-15}$" (4.2 CO kinematics)
   - fitting: _not stated_
   - validation: Compared to [OIII] and CO linewidth along MOSFIRE slit after convolving to 0.7"  
  > "after convolving the ALMA cube to a FWHM=0.7$''$ resolution still yields a much larger $\sigma\gtrsim100$km s$^{-1}$" (4.2 CO kinematics)

## Software

- **CASA** : processing, tclean, uvsubcont  
  > "We use the CASA software (cite: mcmullin07) to process and clean the data." (Target selection and Observations)
- **GALFIT** : Sérsic size fits  
  > "using `GALFIT` (cite: galfit) assuming a single two-dimensional Sérsic profile" (Structural Properties)
- **FAST** : SED fitting for stellar mass  
  > "fitting the optical & NIR SED using FAST (cite: fast)" (Target selection and Observations)
- **emcee** : MCMC fits of dust SED  
  > "Python Markov-Chain Monte Carlo package ` emcee` (cite: mcmc)" (4.1 Continuum-based measurement)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(8-7) luminosity log L'CO | 9.65 | 0.17 | dex (K km/s pc^2) | 4 | We obtain $\log~L'_{\rm CO,
  8-7}=9.65\pm0.17$ dex. |
| CO effective radius | 0.67 | 0.05 | kpc | 2 | obtaining values of $r_{e}=0.67\pm0.05$ kpc and $n=0.9$ |
| v_rot sin i at 1 kpc | 163 | 5 | km/s | 5 | a rotation velocity at $r=1$ kpc of $v_{\rm rot}\sin~i=163\pm5$ km s$^{-1}$ |
| log M_dyn | 10.58 | +0.52/-0.20 | log Msun | 5 | log(M$_{\rm dyn}$/M$_{\odot}$)=$10.58^{+0.52}_{-0.20}$ |
| Intrinsic dispersion sigma_0 | 73 | 8 | km/s | 5 | $\sigma_{0}=73\pm8$ km s$^{-1}$ |
| Integrated CO sigma | 153 | 7 | km/s | 5 | The integrated $\sigma=153\pm7$km s$^{-1}$ |
| Depletion time | 27 | 12 | Myr | 4 | =27\pm12$ Myr |
| log M_gas (SMG alpha_CO) | 10.08 | +0.30/-0.18 | log Msun | 4 | $\log(M^{\rm SMG}_{\rm
  gas}/M_{\odot})=10.08^{+0.30}_{-0.18}$ dex |

## Qualitative findings

- CO and continuum sizes are ~3x smaller than rest-frame optical size  
  > "Both the continuum and emission line sizes are $\sim3\times$ smaller than the rest-frame optical size" (Structural Properties)

## Claim tuples

- H: Is the CO velocity field consistent with a rotating disk? | E: Gaussian fits per spaxel and forward disk modeling | R: v_rot=163±5 km/s, v/sigma~2.5 | F: Rotation-dominated disk in the central kpc | **supported**
- H: Is M_dyn consistent with baryonic mass? | E: Compare modeled M_dyn with M_star plus CO gas | R: M_dyn=10.58 vs M_bar=11.0 for lowest gas fraction | F: Consistent only for the lowest CO gas fraction; strongly baryon dominated | **partially**
- H: Is the center gas-rich and rapidly forming a bulge? | E: Gas fraction within 1 kpc and depletion time | R: f_gas~85%, t_depl~27 Myr | F: Nuclear starburst building a compact quiescent descendant | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): R_81 and alpha_CO poorly constrained; turnover radius loosely constrained; central stellar mass uncertain  
  > "the turnover radius is only loosely constrained because the CO tracer (magenta), probes a smaller region" (4.2 CO kinematics)
- Caveat (inferred, ours): Single galaxy
- Caveat (inferred, ours): Gas mass uncertain by ~1 dex from CO excitation and alpha_CO
- Caveat (inferred, ours): Forward model has few constraints; inclination from optical axis ratio

## Reproducibility

- Data public (paper): Project ID given, public status not stated  
  > "ADS/JAO.ALMA#2015.1.00907.S" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Calibration details and imaging parameters
- Missing: Dynamical model code and priors
- Missing: SED data tables and flux measurements
- Data volume (inferred): ~10-30 GB
- Score (inferred): 3/5, Single dataset with identified project code, but missing imaging parameters and custom dynamical model details.
- Rediscovery candidate: no, Dynamical modeling and SED data are not fully specified.

## Links

- Method: (cite: wuyts16) (pressure support correction)
- Method: (cite: dokkum15) (inclination method)
- Companion: (cite: barro16b) (SFR and continuum size of sample)
- Related: CANDELS
- Related: GOODS-Herschel

## Checks

```json
{
 "quotes": 56,
 "quotes_ok": 56,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 42,
  "rate": 0.545
 },
 "evidence_ok": true
}
```
