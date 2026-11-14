# WISDOM Project - III. Molecular gas measurement of the supermassive black hole mass in the barred lenticular galaxy NGC4429

`2018MNRAS.473.3818D` | Monthly Notices of the Royal Astronomical Society 2018 | first author: Davis, Timothy A. | arXiv: 1710.01488 | DOI: 10.1093/mnras/stx2600

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: What is the mass of the supermassive black hole in the barred lenticular galaxy NGC4429, measured from 12CO(3-2) molecular gas kinematics?  
  > "Our goal in this paper is to estimate the mass of the SMBH at the centre of NGC4429." (4 METHOD & RESULTS)
- Target **NGC4429**: coordinates RA 12h27m26.508s, Dec +11d06m27.76s (ALMA phase centre)  
  > "we assume a distance of 16.5$\pm$1.6 Mpc for NGC4429 (cite: 2011MNRAS.413..813C), as derived from the surface brightness fluctuation measurements of (cite: Tonry:2001ei)" (1 INTRODUCTION); z/distance 16.5±1.6 Mpc  
  > "we assume a distance of 16.5$\pm$1.6 Mpc for NGC4429 (cite: 2011MNRAS.413..813C), as derived from the surface brightness fluctuation measurements of (cite: Tonry:2001ei)" (1 INTRODUCTION); distance from surface brightness fluctuations (Tonry et al. 2001; via Cappellari et al. 2011)  
  > "we assume a distance of 16.5$\pm$1.6 Mpc for NGC4429 (cite: 2011MNRAS.413..813C), as derived from the surface brightness fluctuation measurements of (cite: Tonry:2001ei)" (1 INTRODUCTION)

## Data provenance

- ALMA projects: 2013.1.00493.S
- bands: _not stated_
- frequencies and spectral setup: 1850 MHz window on 12CO(3-2), ~1600 km/s coverage, raw 0.4 km/s resolution; three 2 GHz continuum windows  
  > "An 1850 MHz correlator window was placed over the $^{12}$CO(3–2) line, yielding a continuous velocity coverage of $\approx$1600 km s$^{-1}$" (3 ALMA DATA)
- continuum bandwidth: _not stated_
- arrays: 42 12m antennas  
  > "Forty-two of ALMA’s 12m antennas were used" (3 ALMA DATA)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.18 x 0.14 arcsec, PA 311 deg  
  > "yielding a synthesised beam of 0$.\!\!^{\prime\prime}$18 $\times$ 0$.\!\!^{\prime\prime}$14 at a position angle of 311$^{\circ}$" (3 ALMA DATA)
- max recoverable scale: 11.2 arcsec  
  > "the data are sensitive to emission on scales up to 11$.\!\!^{\prime\prime}$2" (3 ALMA DATA)
- sensitivity: continuum rms 36 uJy; 0.61 mJy/beam per 10 km/s channel; 1.34 mJy/beam per 2 km/s channel  
  > "RMS noise levels of 0.61 mJy beam$^{-1}$ in each 10 km s$^{-1}$ channel (and 1.34 mJy beam$^{-1}$ in 2 km s$^{-1}$ channels)" (3 ALMA DATA)
- time on source: 1.17 hours total, split equally between two tracks  
  > "The total integration time on source was 1.17 hours, split equally between the two tracks." (3 ALMA DATA)
- observing dates: 26 and 27 June 2015  
  > "observed with ALMA on both the 26th and 27th of June 2015" (3 ALMA DATA)
- pi or archival as stated: _not stated_
- Line: 12CO J=3-2 (not stated)
- Other facility **HST WFPC2 F606W**: image for MGE stellar mass model and dust disc inclination  
  > "This was constructed from an *HST* Wide-Field Planetary Camera 2 (WFPC2) F606W image, in combination with an $r'$-band image from SDSS." (4.1.2)
- Other facility **SDSS**: r'-band image for MGE  
  > "This was constructed from an *HST* Wide-Field Planetary Camera 2 (WFPC2) F606W image, in combination with an $r'$-band image from SDSS." (4.1.2)
- Other facility **CARMA**: 12CO(1-0) map from Alatalo et al. 2013 (literature)  
  > "we show the integrated intensity map of $^{12}$CO(1-0), from CARMA observations of NGC4429 by (cite: 2013MNRAS.432.1796A)" (5.2.1)
- External data: 12CO(1-0) CARMA flux/map for line ratio and gas mass  
  > "By comparing this measurement with that of $^{12}$CO(1–0) (cite: 2013MNRAS.432.1796A)" (3.1 Line emission) [from (cite: 2013MNRAS.432.1796A)]
- External data: 5 GHz nuclear flux density 0.40±0.02 mJy  
  > "the 5 GHz flux density (0.40 $\pm$ 0.02 mJy) reported by (cite: 2016MNRAS.458.2221N)" (5.3 Continuum emission) [from (cite: 2016MNRAS.458.2221N)]
- External data: Stellar mass-to-light ratio used for circular velocity estimate  
  > "calculated by multiplying the luminous mass model of (cite: 2013MNRAS.432.1894S) with the mass-to-light ratio of (cite: 2013MNRAS.432.1709C)" (4 METHOD & RESULTS) [from (cite: 2013MNRAS.432.1894S; 2013MNRAS.432.1709C)]

## Processing

### Calibration

- pipeline or manual: standard ALMA pipeline by regional centre, plus extra flagging  
  > "The raw ALMA data were calibrated using the standard ALMA pipeline, as provided by the ALMA regional centre staff." (3 ALMA DATA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: 3C273 (amplitude), J1229+0203 (bandpass and phase)  
  > "Amplitude and bandpass calibration were performed using the quasars 3C273 and J1229+0203, respectively." (3 ALMA DATA)
- flux scale uncertainty: ≈10%  
  > "accounts for the $\approx$10% flux calibration uncertainty of the ALMA data" (3.1 Line emission)
- self calibration: _not stated_

### Imaging

- task: CASA used to combine and image the two tracks; uvcontsub for continuum subtraction  
  > "subtracted from the data in the $uv$ plane using the `CASA` task `uvcontsub`" (3 ALMA DATA)
- deconvolver: _not stated_
- weighting robust: Briggs, robust 0.5  
  > "produced using Briggs weighting with a robust parameter of 0.5" (3 ALMA DATA)
- uv taper: _not stated_
- cell size: 0.05 arcsec  
  > "pixels of 0$.\!\!^{\prime\prime}$05 were chosen as a compromise" (3 ALMA DATA)
- image size: _not stated_
- masking: interactive cleaning mask in source regions, threshold = dirty channel RMS  
  > "The continuum-subtracted dirty cubes were cleaned in regions of source emission (identified interactively) to a threshold equal to the RMS noise of the dirty channels." (3 ALMA DATA)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: clean components restored with Gaussian equal to dirty beam, 0.18 x 0.14 arcsec  
  > "re-convolved using a Gaussian beam of full-width-at-half-maximum (FWHM) equal to that of the dirty beam" (3 ALMA DATA)
- final rms: 0.61 mJy/beam (10 km/s), 1.34 mJy/beam (2 km/s)  
  > "RMS noise levels of 0.61 mJy beam$^{-1}$ in each 10 km s$^{-1}$ channel" (3 ALMA DATA)

### Inherited from earlier work

- Forward-modelling fitting procedure, covariance-matrix likelihood  
  > "Full details of the fitting procedure are described in WISDOM paper II (cite: 2017arXiv170305248D), but we highlight the important aspects below." (4.1) [from (cite: 2017arXiv170305248D)]
- Masked moment technique  
  > "As in our previous works, a copy of the clean data cube was Gaussian-smoothed spatially" (3.1 Line emission) [from previous WISDOM works]
- M/L gradient treatment  
  > "To include this $M$/$L$ gradient in our model we follow (cite: 2016arXiv160903559D)" (4.1.2) [from (cite: 2016arXiv160903559D)]

### Not stated but needed to reproduce (our reading)

- Line-free channels used for uvcontsub
- Clean niter/mask details and CASA version
- MCMC code KinMS_MCMC not yet published (Davis et al. in prep.)
- Exact MGE fitting masks and PSF details for HST/SDSS
- Rest frequency adopted

## Analysis recipe

1. **Image calibrated visibilities and make moment maps**: CASA imaging of two tracks, uvcontsub, masked moments (smoothed cube, 1.5 sigma mask)  
  > "A three-dimensional mask was then defined by selecting all pixels above a fixed flux threshold of 1.5 times the RMS noise" (3.1 Line emission)
   - software: CASA
   - parameter: 10 km/s and 2 km/s channels; robust 0.5; 0.05 arcsec pixels  
  > "In this work we primarily use data with a channel width of 10 km s$^{-1}$" (3 ALMA DATA)
   - fitting: _not stated_
   - validation: _not stated_
2. **Build stellar mass model**: MGE fit to HST F606W + SDSS r' with dust masked; central unresolved Gaussian removed; piecewise linear M/L  
  > "we found that assuming a $M$/$L$ (referred to here as $\Psi$ for brevity) that is piecewise linear as a function of radius provides the best fit to the data" (4.1.2)
   - software: MGE_FIT_SECTORS
   - assumption: Solar absolute magnitude 4.67 in F606W; axisymmetry; inclination tied to gas disc  
  > "assuming the absolute magnitude of the Sun in this band to be 4.67" (4.1.2)
   - fitting: _not stated_
   - validation: Independent 10-bin M/L fit agrees with piecewise linear model  
  > "The black points with error bars in Figure [11](#ml_grad) show these estimates, that agree well with our simple piecewise linear approximation." (4.3.2)
3. **Fit gas kinematics for SMBH mass**: KinMS forward model + MCMC, circular rotation, exponential disc with truncations and plateau; two-step fit (160x160 px then central 64x64 px with covariance)  
  > "we adopt a two-step fitting process. We initially fit a 160 $\times$ 160 pixel$^2$ area that roughly covers the entire molecular gas disc" (4.2.1 Fitting process)
   - software: KinMS, KinMS_MCMC
   - parameter: gas velocity dispersion fixed at 2.2 km/s; flat priors, log-flat for MBH 4.8-9.8  
  > "The prior on the SMBH mass was flat in log-space, with the mass allowed to vary between log$_{10}(\frac{M_{\rm BH}}{\mathrm{M}_{\odot}})$ = 4.8 and 9.8." (4.2.1 Fitting process)
   - assumption: circular motion; distance 16.5 Mpc  
  > "In this work we always assume that the gas is in circular motion" (4.1.2)
   - fitting: MCMC with Gibbs sampling and adaptive stepping; chi2 log-likelihood with analytic covariance matrix; 100,000 steps, 10% burn-in; median and 68/99% CL  
  > "We utilise a MCMC method with Gibbs sampling and adaptive stepping to explore the parameter space." (4.2)
   - validation: Cross-checks with emcee; refit within 1 arcsec; flat priors in sin i and cos PA; residuals check  
  > "We recovered the same best-fit SMBH mass and $M$/$L$, with increased uncertainties as expected (by a factor of $\approx$1.5 in this case)." (4.3.3)
4. **Estimate gas velocity dispersion**: Refit 2 km/s channel cube with sigma_gas free  
  > "We repeated the kinematic fitting described above on this higher velocity resolution data cube, allowing $\sigma_{\rm gas}$ to vary." (4.3.5)
   - software: KinMS_MCMC
   - fitting: _not stated_
   - validation: Increasing sigma by 10x has negligible effect on MBH  
  > "Arbitrarily increasing the assumed gas velocity dispersion by an order of magnitude has a negligible effect on our best-fit SMBH mass" (4.3.5)
5. **Fit continuum source**: Gaussian fitting with IMFIT  
  > "We constrain the position and size of this source using Gaussian fitting with the `CASA` task `IMFIT`." (3.2 Continuum emission)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : calibration/imaging, uvcontsub, IMFIT  
  > "We then used the `Common Astronomy Software Applications` (`CASA)` package to combine and image the visibility files of the two tracks" (3 ALMA DATA)
- **KinMS** : forward-modelling mm-wave data cubes  
  > "we utilise the publicly available KINematic Molecular Simulation (KINMS[^2]) mm-wave observation simulation tool" (4.1)
- **KinMS_MCMC** : MCMC fitting  
  > "coupled to the Markov Chain Monte Carlo (MCMC) code KINMS_MCMC (Davis et al. in prep.)" (4.1)
- **MGE_FIT_SECTORS** : multi-Gaussian expansion of stellar light  
  > "constructed using the MGE_FIT_SECTORS package of (cite: 2002MNRAS.333..400C)" (4.1.2)
- **emcee** : cross-check of MCMC code  
  > "details of cross checks with the well tested MCMC code EMCEE (cite: 2013PASP..125..306F)" (4.2)
- **JAM** : new mass-follows-light fit to SAURON data, M/L_r=8.8  
  > "We performed a new mass-follows-light JAM fit on the SAURON data using the MGE given in Table 1 and find $M$/$L_{r}$=8.8" (4.2.1 Fitting process)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| SMBH mass | 1.5e8 | ±0.1 (random, 99% CL), +0.15/-0.35 (systematic) e8 | Msun | 3 | a mass of (1.5$\pm0.1^{+0.15}_{-0.35}$) $\times$10$^8$ M$_{\odot}$ for the SMBH in NGC4429 |
| Gas velocity dispersion | 2.2 | +0.68/-0.65 (99% CL) | km/s | 4 | yielding a value of 2.2$^{+0.68}_{-0.65}$ km s$^{-1}$(at the 99% CL) |
| Total CO(3-2) flux | 75.45 | ±0.09 ±7.5 | Jy km/s | 1 | The total flux is 75.45 $\pm$ 0.09 $\pm$7.5 Jy km s$^{-1}$ |
| CO(3-2)/CO(1-0) intensity ratio | 1.06 | 0.15 | dimensionless | 1 | we find a $^{12}$CO(3-2)/$^{12}$CO(1-0) intensity ratio of 1.06 $\pm$ 0.15 |
| Continuum integrated flux (340 GHz) | 1.38 | ±0.07 ±0.14 | mJy | 5 | a total integrated intensity of 1.38 $\pm$ 0.07 $\pm$0.14 mJy |
| Inclination | 66.80 | ±0.04 (68%) | deg | 3 | Inclination ($i$; $^\circ$) / 66.5 / $\rightarrow$ / 89.0 / 66.80 |
| Central V-band M/L | 6.59 | ±0.05 (68%) | Msun/Lsun,V | 3 | Inner stellar $M$/$L$ ($\Psi_{\rm cent}$; M$_{\odot}$/L$_{\odot,V}$) / 1.0 / $\rightarrow$ / 10.0 / 6.59 |
| Outer V-band M/L (400 pc) | 8.25 | -0.03/+0.02 | Msun/Lsun,V | 3 | Outer Stellar $M$/$L$ ($\Psi_{\rm outer}$; M$_{\odot}$/L$_{\odot,V}$)$^*$ / 1.0 / $\rightarrow$ / 10.0 / 8.25 |
| Kinematic position angle | 93.20 | ±0.03 (68%) | deg | 3 | Kinematic position angle ($\phi_{\rm kin}$; $^\circ$) / 0.0 / $\rightarrow$ / 359.0 / 93.20 |

## Qualitative findings

- Gas disc is flocculent, relaxed, truncated at small radii with ~40 pc central hole  
  > "We clearly detect a flocculent disc of molecular gas in NGC4429, with a radius of $\approx$400 pc. This disc has a central hole of $\approx$40 pc in radius." (3.1 Line emission)

## Claim tuples

- H: Can the SMBH mass in NGC4429 be measured despite the central gas hole? | E: KinMS forward modelling of the ALMA CO(3-2) cube with M/L gradient | R: MBH = (1.5±0.1) x10^8 Msun (99% CL) | F: A massive dark object is clearly detected; consistent with previous upper limit and the MBH-sigma relation | **supported**
- H: Does the stellar M/L vary in the inner region? | E: Fit piecewise linear M/L profile | R: M/L rises from 6.6 to 8.25 at 400 pc | F: ~30% M/L change within the inner 400 pc | **supported**
- H: What explains the gas disc truncation? | E: Resonance, Toomre Q and Roche-limit analyses | R: Q rises at the outer truncation; resonance origin requires extreme pattern speed; tides alone insufficient | F: Stability plus tidal shear likely responsible; resonance disfavoured | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Resonance origin of gas morphology disfavoured; morphological quenching disfavoured due to normal SFE  
  > "We thus consider a resonance origin for the gas morphology to be disfavoured, although we cannot rule it out entirely." (5.2.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Central gas hole makes SMBH mass sensitive to stellar mass modelling  
  > "due to the central hole in the gas distribution, any SMBH mass estimate will be sensitive to errors in our stellar mass modelling" (4 METHOD & RESULTS)
- Caveat (inferred, ours): M/L gradient degenerate with SMBH mass given central hole
- Caveat (inferred, ours): Dust masking and AGN point source affect MGE
- Caveat (inferred, ours): MCMC code unpublished
- Caveat (inferred, ours): Systematic asymmetry from AGN treatment (-0.2 dex)

## Reproducibility

- Data public (paper): ALMA data acknowledged by project code; HST from Hubble Legacy Archive  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00493.S." (Acknowledgments)
- Products in archive: _not stated_
- Code: KinMS public on GitHub; KinMS_MCMC not yet released  
  > "we utilise the publicly available KINematic Molecular Simulation (KINMS[^2]) mm-wave observation simulation tool" (4.1)
- Missing: KinMS_MCMC code
- Missing: CASA version and clean parameters
- Missing: line-free channel ranges
- Data volume (inferred): ~10-50 GB (two Band 7 tracks, 42 antennas)
- Score (inferred): 3/5, Public ALMA data and clear model description, but fitting code unpublished and imaging details incomplete.
- Rediscovery candidate: no, Key fitting code (KinMS_MCMC) was unreleased and imaging details are incomplete.

## Links

- Method: (cite: 2017arXiv170305248D) (Full fitting procedure including covariance likelihood)
- Method: (cite: 2013MNRAS.429..534D) (KinMS tool)
- Method: (cite: 2016arXiv160903559D) (M/L gradient formalism)
- Companion: (cite: 2017arXiv170305247O) (WISDOM paper I, NGC3665)
- Companion: (cite: 2017arXiv170305248D) (WISDOM paper II, NGC4697)
- Related: WISDOM
- Related: ATLAS3D

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
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 81,
  "stated": 53,
  "rate": 0.654
 },
 "evidence_ok": true
}
```
