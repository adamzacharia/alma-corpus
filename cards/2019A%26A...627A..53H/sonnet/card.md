# The Close AGN Reference Survey (CARS). A massive multi-phase outflow impacting the edge-on galaxy HE 1353-1917

`2019A&A...627A..53H` | Astronomy and Astrophysics 2019 | first author: Husemann, B. | arXiv: 1905.10385 | DOI: 10.1051/0004-6361/201935283

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: How do an AGN-driven outflow and radio jet affect the multi-phase gas and star formation of the edge-on host galaxy HE 1353-1917?  
  > "It is therefore a unique test case to study the process of AGN feedback in detail and to highlight the power of our multi-wavelength approach in constraining the AGN outflow energetics" (1 Introduction)
- Target **HE 1353-1917**: coordinates 13h56m36.7s -19d31m45s  
  > "at redshift $z=0.035$" (1 Introduction); "1$''$ corresponds to 0.697 kpc at the redshift of HE 1353$-$1917 ($z=0.035$), where the associated luminosity distance is 153.9 Mpc." (1 Introduction); z/distance z=0.035; D_L = 153.9 Mpc  
  > "at redshift $z=0.035$" (1 Introduction); "1$''$ corresponds to 0.697 kpc at the redshift of HE 1353$-$1917 ($z=0.035$), where the associated luminosity distance is 153.9 Mpc." (1 Introduction); distance from redshift with H0=70, Om=0.3, OL=0.7  
  > "at redshift $z=0.035$" (1 Introduction); "1$''$ corresponds to 0.697 kpc at the redshift of HE 1353$-$1917 ($z=0.035$), where the associated luminosity distance is 153.9 Mpc." (1 Introduction)

## Data provenance

- ALMA projects: 2016.1.00952.S
- bands: 12CO(1-0) line (Band 3 not named)  
  > "The $^{12}$CO(1–0) line in HE 1353$-$1917 was observed with ALMA" (6.4 ALMA observations)
- frequencies and spectral setup: 1850 MHz correlator window on CO(1-0), ~3000 km/s coverage, ~1 km/s raw resolution; three 2 GHz low-res windows for continuum  
  > "An 1850 MHz correlator window was placed over the $^{12}$CO(1–0) line, yielding a continuous velocity coverage of $\approx$3000 km s$^{-1}$" (6.4 ALMA observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C40-5 and C40-2  
  > "for 70.56 and 34.23 minutes in configurations C40-5 and C40-2, respectively" (6.4 ALMA observations)
- baselines: _not stated_
- angular resolution: 0.64" x 0.55" at PA 71 deg  
  > "yielding a synthesized beam of 0$.\!\!^{\prime\prime}$64 $\times$ 0$.\!\!^{\prime\prime}$55 at a position angle of 71$^{\circ}$" (6.4 ALMA observations)
- max recoverable scale: up to 22.6 arcsec (text elsewhere says 20 arcsec)  
  > "Combining these observations gives us sensitivity to emission on scales up to 22$.\!\!^{\prime\prime}$6." (6.4 ALMA observations)
- sensitivity: 0.21 mJy/beam per 50 km/s channel; continuum rms 9.3 uJy  
  > "with RMS noise levels of 0.21 mJy beam$^{-1}$ in each 50 km s$^{-1}$ channel" (6.4 ALMA observations)
- time on source: 70.56 and 34.23 min  
  > "for 70.56 and 34.23 minutes in configurations C40-5 and C40-2" (6.4 ALMA observations)
- observing dates: 3 November and 24 December 2016  
  > "on both the 3rd November and the 24th of December 2016" (6.4 ALMA observations)
- pi or archival as stated: _not stated_
- Line: 12CO J=1-0 (not stated)
- Other facility **VLT/MUSE**: optical IFU spectroscopy for ionized gas  
  > "we obtained optical integral-field spectroscopy with the Multi Unit Spectroscopic Explorer" (2 The CARS multi-wavelength data set)
- Other facility **Gemini-N/NIFS**: near-IR IFU, warm H2  
  > "near-IR (NIR) integral-field spectroscopy with the Near-Infrared Integral Field Spectrometer" (2 The CARS multi-wavelength data set)
- Other facility **VLA**: 10 GHz and 1.4 GHz continuum, HI  
  > "Radio observations were taken with the Karl G. Jansky Very Large Array (VLA) at $X$-band (10 GHz) in A configuration" (2 The CARS multi-wavelength data set)
- Other facility **XMM-Newton and Chandra**: X-ray spectrum and image  
  > "a deep X-ray spectrum with 62 ksec integration time was taken with *XMM-Newton*" (2 The CARS multi-wavelength data set)
- External data: IRAM-30m single-dish CO(1-0) molecular gas mass 2.7e9 Msun for comparison  
  > "single-dish measurements from the IRAM-30m telescope of $M_\mathrm{H2}=(2.7\pm0.2)\times10^9\mathrm{M}_\odot$ reported by" (3.3 Cold molecular and atomic gas phase) [from (cite: Bertram:2007)]

## Processing

### Calibration

- pipeline or manual: standard ALMA pipeline by regional centre, plus additional flagging  
  > "The raw ALMA data were calibrated using the standard ALMA pipeline, as provided by the ALMA regional centre staff." (6.4 ALMA observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ganymede (amplitude) and J1337-1257 (bandpass); J1400-1858 phase  
  > "Amplitude and bandpass calibration were performed using Ganymede and the quasar J1337-1257." (6.4 ALMA observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA, tracks combined and imaged into cube  
  > "to combine and image the visibility files of the two tracks, producing a three-dimensional RA-Dec-velocity data cube" (6.4 ALMA observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "imaged using Briggs weighting with a robust parameter of 0.5" (6.4 ALMA observations)
- uv taper: _not stated_
- cell size: 0.2 arcsec; 50 km/s channels  
  > "a channel width of 50  km s$^{-1}$, and pixels of 0$.\!\!^{\prime\prime}$2" (6.4 ALMA observations)
- image size: _not stated_
- masking: interactive clean regions, threshold = rms of dirty channels  
  > "cleaned in regions of source emission (identified interactively) to a threshold equal to the RMS noise of the dirty channels" (6.4 ALMA observations)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub over full line-free bandwidth  
  > "subtracted from the data in the $uv$ plane using the `CASA` task `uvcontsub`" (6.4 ALMA observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.64" x 0.55" (476 x 409 pc)  
  > "a physical resolution of 476 $\times$ 409 pc$^2$" (6.4 ALMA observations)
- final rms: _not stated_

### Inherited from earlier work

- Masked moment technique for CO moment maps  
  > "using a masked moment technique (cite: Dame:2011)" (3.3 Cold molecular and atomic gas phase) [from (cite: Dame:2011)]
- Cold gas mass from CO luminosity prescription  
  > "We estimate the cold molecular gas from the CO luminosity following the prescription of (cite: Davis:2015)" (3.6 Outflow energetics) [from (cite: Davis:2015)]

### Not stated but needed to reproduce (our reading)

- CASA version used for ALMA imaging
- Line-free channels for continuum subtraction
- Which pipeline version/CASA version for calibration
- Clean deconvolver and image size
- Exact spatial/velocity regions used for the extracted spectra and CO flux integration
- Primary beam correction details
- Flux scale uncertainty

## Analysis recipe

1. **Produce CO(1-0) cube**: Pipeline calibration, combine two tracks, Briggs robust 0.5 imaging, uvcontsub, interactive clean  
  > "The data presented here were imaged using Briggs weighting with a robust parameter of 0.5" (6.4 ALMA observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Moment maps and cold gas mass**: Masked moments: smoothed cube mask at 3 sigma, moments from unsmoothed cube; integrate CO for M_H2  
  > "A three-dimensional mask was then defined by selecting all pixels above a fixed flux threshold of 3 times the RMS noise in this new cube." (3.3 Cold molecular and atomic gas phase)
   - assumption: Galactic alpha_CO = 4.35 Msun (K km/s pc^2)^-1  
  > "adopting a Galactic conversion factor of $\alpha_\mathrm{CO}=4.35\,\mathrm{M}_\odot(\mathrm{K\,km\,s}^{-1}\,\mathrm{pc}^{-2})^{-1}$" (3.3 Cold molecular and atomic gas phase)
   - fitting: _not stated_
   - validation: compared with IRAM-30m single-dish mass  
  > "Our estimate is slightly higher than the single-dish measurements from the IRAM-30m telescope" (3.3 Cold molecular and atomic gas phase)
3. **Kinematic model of CO disc and dynamical mass**: KinMS forward model of CO cube with MGE mass model from Ks image; truncated exponential disc; M_dyn from Lequeux formula  
  > "we model the ALMA CO observation directly with the KINematic Molecular Simulation (cite: Davis:2013; Davis:2013b) software tool" (3.5.1 CO(1-0) kinematic modelling)
   - software: KinMS
   - parameter: free: r_exp, r_trunc, PA, inclination, sigma, v_sys, kinematic centre, M/L gradient  
  > "with the scale radius ($r_\mathrm{exp}$) and the inner truncation radius ($r_\mathrm{trunc}$) as free parameters" (3.5.1 CO(1-0) kinematic modelling)
   - assumption: linear M/L gradient; AGN MGE component neglected  
  > "We neglect the unresolved MGE component at the galaxy centre, which arises from the AGN." (3.5.1 CO(1-0) kinematic modelling)
   - fitting: _not stated_
   - validation: residual maps compared to data  
  > "Our model is indeed a very good description of the data" (3.5.1 CO(1-0) kinematic modelling)
4. **Outflow components and energetics**: Two-Gaussian fits to co-added spectra (0.8 arcsec radius) in all phases; mass, mass outflow rates for cone and shell geometries  
  > "We extract a co-added spectrum within an aperture of 0.8$''$ radius for both high dispersion regions." (3.5.2 Multi-phase kinematics of the bipolar outflow)
   - parameter: shell thickness 200 pc (20-500 pc range); X_CO = 2e20  
  > "we adopt a thickness of $\Delta R=200$ pc" (3.6 Outflow energetics)
   - assumption: X_CO = 2e20 cm^-2 (K km/s pc^2)^-1 for outflowing gas; lower limit 1.6e19  
  > "we choose a conversion factor of $X_{\rm CO}=2\times10^{20}\,\mathrm{cm}^{-2}(\mathrm{K\,km\,s}^{-1}\mathrm{pc}^2)^{-1}$" (3.6 Outflow energetics)
   - fitting: _not stated_
   - validation: compared with literature outflow trends  
  > "We find that the mass outflow rates and kinetic power of the outflow measured for HE 1353$-$1917 is fully consistent with the clear trends" (4.3)

## Software

- **CASA** : ALMA/VLA calibration combination imaging, uvcontsub  
  > "We then used the `Common Astronomy Software Applications` (cite: McMullin:2007) package to combine and image" (6.4 ALMA observations)
- **KinMS** : CO kinematic modelling  
  > "KINematic Molecular Simulation (cite: Davis:2013; Davis:2013b) software tool" (3.5.1 CO(1-0) kinematic modelling)
- **AGNFITTER** : SED fitting for stellar mass and SFR  
  > "A Bayesian approach is used byAGNFITTER (cite: CalistroRivera:2016) to decompose the total SED" (3.1 Broad-band SED fitting)
- **PyParadise** : stellar continuum and emission line fitting of MUSE  
  > "is implemented in PYPARADISE" (3.3.1 Ionized gas phase)
- **QDeblend3D** : AGN-host deblending of IFU data  
  > "using our own software QDEBLEND${}^{\mathrm{3D}}$" (3.2.1 IFU spectroscopy)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Cold molecular gas mass | 3.6e9 | 0.3e9 | Msun | 2 | $M_\mathrm{H2}=(3.6\pm0.3)\times10^9\mathrm{M}_\odot$ |
| Dynamical mass (R<12.65 kpc) | 1.0e11 | 0.3e11 | Msun | 3 | $(1.0\pm0.3)\times10^{11}M_\ensuremath{\odot}$ |
| CO disc inclination | 85.4 | +0.1/-0.4 | deg | 3 | $85.4\ensuremath{^\circ}\ _{-0.4}^{+0.1}$ |
| Truncation radius | 3.1 | 0.1 | arcsec | 3 | $r_\mathrm{trunc}=3.1\ensuremath{''}\pm0.1\ensuremath{''}$ |
| Stellar mass | 2.5e10 | 0.5e10 | Msun | 0 | $M_* = (2.5\pm0.5)\times10^{10}M_\ensuremath{\odot}$ |
| Molecular outflow mass SW wing | 0.84e8 | 0.25e8 | Msun | 4 | $M_\mathrm{mol,winge}=(0.84\pm0.25)\times10^8M_\odot$ |
| Total mass-loading factor | ~1-30 | not stated | dimensionless | 4 | ranges between $\sim$1–30, if the molecular gas is indeed outflowing |

## Qualitative findings

- CO velocity dispersion shows hot spots on both sides of the nucleus coincident with ionized and warm H2 features  
  > "apart from two hot spots in the south-west and north-east of the nucleus of the galaxy" (3.3)

## Claim tuples

- H: Is there a multi-phase AGN-driven outflow in the disc? | E: Compared CO, H2 and ionized gas kinematics with a CO rotation model | R: High dispersion hot spots 1.5-2.0" from centre deviate from the model in all phases | F: Fast bipolar multi-phase outflow, ~1 kpc scale | **supported**
- H: What powers the outflow? | E: Compared energetics with L_bol and jet power | R: Jet power log 43.3 ~0.1 L_bol; ~1% of L_bol needed | F: Jet alone can drive it; both possible | **partially**
- H: Does the outflow suppress star formation? | E: Compared sSFR and depletion time to main sequence | R: Galaxy near main sequence; H-alpha SFR a factor 2 lower | F: Mild impact on SFR | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Gravitational explanations (point mass, bar) or pre-existing nuclear ring considered for molecular dispersion  
  > "It might be possible to explain the elevated velocity dispersion in the molecular gas by adding an additional point-like mass in the centre or a circum-nuclear bar." (3.5.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Outflow energetics uncertain by orders of magnitude (X_CO, geometry, velocity definition)  
  > "the definition of outflow velocity, geometry and $X_\mathrm{CO}$ still leads to order of magnitude uncertainties" (3.6)
- Caveat (inferred, ours): Molecular outflow may be a nuclear ring, not an outflow
- Caveat (inferred, ours): Single-object study; X_CO unconstrained
- Caveat (inferred, ours): Shell thickness unmeasured

## Reproducibility

- Data public (paper): ALMA project code and PI stated; public status not stated  
  > "as part of programme 2016.1.00952.S (PI: G. Tremblay)" (2)
- Products in archive: _not stated_
- Missing: CASA version
- Missing: line-free channels
- Missing: KinMS fitting setup and priors
- Missing: extraction apertures for CO flux
- Data volume (inferred): ~10-50 GB (two tracks, 1850 MHz line window plus continuum)
- Score (inferred): 4/5, CO imaging steps and KinMS setup mostly described, but versions, fitting details and multi-wavelength data (MUSE, NIFS) are needed for full reproduction.
- Rediscovery candidate: no, Main results depend on non-ALMA data (MUSE, NIFS, VLA) and incomplete fitting details.

## Links

- Method: (cite: Davis:2013) (KinMS modelling)
- Method: (cite: Dame:2011) (masked moment technique)
- Companion: (cite: Husemann:2017b) (CARS survey presentation)
- Related: Close AGN Reference Survey (CARS)

## Checks

```json
{
 "quotes": 64,
 "quotes_ok": 64,
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
  "facts": 75,
  "stated": 48,
  "rate": 0.64
 },
 "evidence_ok": true
}
```
