# The Radial Distribution of Dust Particles in the HL Tau Disk from ALMA and VLA Observations

`2019ApJ...883...71C` | The Astrophysical Journal 2019 | first author: Carrasco-González, Carlos | arXiv: 1908.07140 | DOI: 10.3847/1538-4357/ab3d33

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: What are the radial profiles of dust temperature, dust surface density and maximum grain size in the HL Tau disk when scattering is included and no optical depth is assumed?  
  > "This procedure allows us to obtain the dust temperature, the dust surface density and the maximum particle size at each radius." (abstract)
- Target **HL Tau**: coordinates _not stated_; z/distance 147 pc  
  > "equivalent to a physical size of 7.35 au at the distance of 147 pc (Galli et al. 2018)" (2.3 Final images and radial profiles); distance from Galli et al. 2018  
  > "equivalent to a physical size of 7.35 au at the distance of 147 pc (Galli et al. 2018)" (2.3 Final images and radial profiles)

## Data provenance

- ALMA projects: _none stated_
- bands: ALMA Bands 7, 6, 4 (0.9, 1.3, 2.1 mm); VLA Q, Ka, K  
  > "We used images obtained with ALMA at bands 7, 6, and 4, corresponding to central wavelengths of 0.9, 1.3 and 2.1 mm, respectively." (2.1 ALMA Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: VLA A configuration for Ka and K; Q is C+B+A  
  > "We obtained new observations at Ka and K bands during 7 observational sessions between October 1st and 18th, 2016, using the A configuration of the VLA." (2.2 VLA observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Band 7 ~30 mas, Band 6 ~35 mas, Band 4 ~49 mas; all convolved to 50 mas  
  > "These images have angular resolutions of $\sim$30 and $\sim$35 m.a.s., and rms noises of $\sim$20 and $\sim$12 $\mu$Jy beam$^{-1}$, respectively" (2.1 ALMA Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: Bands 7 and 6 in 2014; Band 4 in November 2015; VLA Ka and K in October 2016  
  > "The band 4 data was obtained in a more recent (November 2015) ALMA observation, also part of the Long Baselines Science Verification program" (2.1 ALMA Observations)
- pi or archival as stated: _not stated_
- Other facility **VLA**: Q, Ka, K band continuum at 7, 9, 13 mm  
  > "We used high sensitivity VLA observations at Q, Ka and K bands, corresponding to central wavelengths of 7.0, 9.0 and 13 mm, respectively." (2.2 VLA observations)
- External data: Band 7 and 6 reference images from the ALMA Long Baseline Science Verification campaign  
  > "We downloaded the reference images from the ALMA Science Verification webpage" (2.1 ALMA Observations) [from ALMA Partnership et al. (2015b)]
- External data: VLA Q band data previously presented  
  > "were already presented and discussed in Carrasco-González et al. (2016)" (2.2 VLA observations) [from Carrasco-González et al. 2016]
- External data: Disk inclination 46.72 deg and PA 138.02 deg  
  > "inclination[^3] i=46.72$^\circ$ and P.A.=138.02$^\circ$ of the HL Tau disk (ALMA Partnership et al 2015b)" (2.3 Final images and radial profiles) [from ALMA Partnership et al 2015b]
- External data: Snow line freezing temperature ranges  
  > "ranges of freezing temperatures for these molecules are taken from Zhang et al. 2015" (4 Results and Discussion) [from Zhang et al. 2015]

## Processing

### Calibration

- pipeline or manual: VLA calibrated with NRAO pipeline; Band 4 calibrated and self-calibrated following ALMA staff instructions  
  > "These data were calibrated using the NRAO pipeline for VLA continuum data." (2.2 VLA observations); "We downloaded the uv data and followed instructions from ALMA staff for applying the calibration, self-calibration and imaging." (2.1 ALMA Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Band 7 and 6 reference images used as downloaded, then convolved  
  > "The final ALMA images at bands 7 and 6 used in our analysis are simply the reference images downloaded from the ALMA archive and convolved to a circular beam of 50 m.a.s." (2.3 Final images and radial profiles)
- flux calibrator: VLA: 3C147 flux, 3C84 bandpass, J0431+1731 gain  
  > "flux, bandpass and complex gain calibrations were performed by observing 3C147, 3C84 and J0431+1731, respectively." (2.2 VLA observations)
- flux scale uncertainty: ~3, 1.5, 2.5, 3.5% at bands 7, 6, 4, Q+Ka  
  > "This results in flux uncertainties of $\sim$3, 1.5, 2.5, and 3.5% at bands 7, 6, 4, and Q+Ka, respectively." (Flux Calibration Uncertainties)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Robust 0 for initial images; for Band 4 and VLA, robust chosen for highest sensitivity with resolution just below 50 mas  
  > "we used images made with values of the parameter robust that gave us the highest sensitivity with an angular resolution just below 50 m.a.s." (2.3 Final images and radial profiles)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: CASA imsmooth  
  > "convolved them by using the task *imsmooth* from CASA" (2.3 Final images and radial profiles)
- final beam: circular 50 mas (7.35 au)  
  > "All images are convolved to a circular beam with a size of 50 m.a.s." (Table 2)
- final rms: B7 15, B6 20, B4 15, Ka+Q 3 uJy/beam  
  > "| ALMA | B7 | 0.9 | 15 | 33 |" (Table 2)

### Inherited from earlier work

- Band 7 and 6 images are the reference images from the Science Verification campaign  
  > "are the iconic images previously reported and discussed by ALMA Partnership et al. (2015b)" (2.1 ALMA Observations) [from ALMA Partnership et al. (2015b)]
- Dust opacities computed with the D'Alessio et al. code, Pollack et al. dust mixture  
  > "The dust opacity properties are computed using the D’Alessio et al. (2001) code for compact spherical grains" (3.3 Radial SED Fitting) [from D'Alessio et al. (2001); Pollack et al. 1994]
- Scattering source function solution for isothermal slab with inclination  
  > "the emergent specific intensity is obtained by (Sierra et al. 2019):" (3.2 Protoplanetary Disks: Scattering-dominated dust opacity) [from Miyake & Nakagawa (1993); Sierra et al. 2019]

### Not stated but needed to reproduce (our reading)

- Initial a_max guess and curve_fit bounds
- Exact robust values for each final image
- Band 4 self-calibration parameters and ALMA staff script
- Source function and Gaussian jet-model details for uv subtraction beyond text
- Asymmetry parameter g computation specifics
- Tabulated opacity grid of a_max vs chi0, beta, omega

## Analysis recipe

1. **Prepare images**: Download ALMA B7/B6 images, calibrate B4 and VLA data, subtract free-free jet in uv plane, convolve all to 50 mas  
  > "convolving all images to a circular beam with a size of 50 m.a.s., equivalent to a physical size of 7.35 au" (2.3 Final images and radial profiles)
   - software: CASA
   - parameter: Ka and Q combined into 8.0 mm image; K band excluded  
  > "We do not use the K band data for the analysis of the dust emission since the jet emission is likely to be affecting a larger part of the disk center at this band" (2.3 Final images and radial profiles)
   - fitting: _not stated_
   - validation: _not stated_
2. **Free-free jet subtraction**: MFS clean (nterms=2) of combined K, Ka, Q uniform-weighted image to model jet; subtract model components from uv data  
  > "we subtracted the model components obtained from the MFS cleaning process to the uv data of the three VLA bands." (Free-free substraction of VLA observations)
   - software: CASA
   - parameter: 175 uJy at 32.5 GHz, spectral index 0.7, size 22 mas  
  > "an elongated source at 32.5 GHz with a flux density of $\sim$175 $\mu$Jy, a spectral index of $\sim$0.7" (Free-free substraction of VLA observations)
   - fitting: _not stated_
   - validation: _not stated_
3. **Radial profiles**: Average intensity in elliptical rings 10 mas wide using inclination and PA; convert to brightness temperature with full Planck law; compute spectral indices  
  > "averaging emission in elliptical rings with a width of 10 m.a.s." (2.3 Final images and radial profiles)
   - parameter: error = rms/(Omega_ring/Omega_beam)^0.5  
  > "$\Delta \rm{I}_\nu = \rm{rms}_\nu / ( \Omega_{\rm ring} / \Omega_{\rm beam} )^{0.5}$" (2.3 Final images and radial profiles)
   - assumption: i=46.72 deg, PA=138.02 deg  
  > "i=46.72$^\circ$ and P.A.=138.02$^\circ$" (2.3 Final images and radial profiles)
   - fitting: _not stated_
   - validation: _not stated_
4. **Radial SED fit with scattering**: Fit each radius to I_nu with absorption+scattering slab solution for T_dust, tau_0, beta_chi; iterate a_max until converged; derive Sigma_dust=tau_0/chi_0  
  > "We repeat this until $a_{\rm max}$ converges (i.e., differences are lower than 5%) which typically occurs in 2 or 3 iterations" (3.3 Radial SED Fitting)
   - software: scipy curve_fit, python
   - parameter: reference frequency 230 GHz  
  > "we consider a reference frequency $\nu_0$=230 GHz, which corresponds to a wavelength of 1.3 mm" (3.3 Radial SED Fitting)
   - assumption: p=3.5, a_min=0.05 um, compact spherical grains; silicates/organics/ice 26/31/43%; vertically isothermal slab, isotropic scattering with effective sigma  
  > "with relative abundances of 26%, 31%, and 43% respectively (Pollack et al. 1994)" (3.3 Radial SED Fitting); "it is assumed to be 0.05 $\mu$m" (3 Methods: Estimating Particle Sizes from Dust Opacity)
   - fitting: Non-linear least squares; errors from 1000 Monte Carlo realizations with normal noise; mean and std dev  
  > "the nominal value of a parameter is defined as the mean and the error as the standard deviation of the 1000 fits." (3.3 Radial SED Fitting)
   - validation: Model compared to observed brightness temperatures and to independent 3.0 mm ALMA image convolved to ~80 mas  
  > "We convolved the prediction of our model at 3.0 mm to the angular resolution of this image, and compare the radial profiles of the brightness temperature." (3.3 Radial SED Fitting)
5. **Flux calibration uncertainty test**: Repeat fit 1000 times varying each profile by flux uncertainties; report 16th–84th percentiles  
  > "The lower limit is defined by the percentile 16 and the upper limit as the percentile 84 of our 1000 fits." (Flux Calibration Uncertainties)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Convolution (imsmooth), MFS clean, imaging  
  > "(parameter nterms=2 in the CASA task *clean*)" (Free-free substraction of VLA observations)
- **scipy curve_fit** : Non-linear least-squares SED fit  
  > "we use the function *curvefit*[^4] in *python*" (3.3 Radial SED Fitting)
- **D'Alessio et al. (2001) opacity code** : Dust opacity properties  
  > "The dust opacity properties are computed using the D’Alessio et al. (2001) code" (3.3 Radial SED Fitting)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Maximum particle size at disk center | ~1.5 | 1-2 mm with flux-scale uncertainty | mm | 4 | Maximum particle sizes are $\sim$1.5 mm at the center of the disk and decrease to $\sim$0.5 mm at the external disk |
| Dust temperature profile | T_dust=150 x [R/10 AU]^-0.5 | not stated | K | 4 | $T_{\rm dust}=150 \times [R/10 AU]^{-0.5}$ K |
| Total dust mass (absorption+scattering) | ~1.0e-3 | not stated | Msun | 4 | The total dust mass of the disk in this model is $\sim$1.0$\times$10$^{-3}$ M$_\odot$ |
| Total dust mass (absorption-only) | ~0.5e-3 | not stated | Msun | 4 | we obtain a total dust mass of $\sim$0.5$\times$10$^{-3}$ $M_\odot$ in the absorption-only approximation |
| a_max power law a0 at 40 au and index b | a0~0.9 mm, b=0.2 | not stated | mm; dimensionless | 4 | approximately follows a power-law with $a_0\sim$0.9 mm at 40 au, and $b$=0.2 |
| ALMA optical depth | tau~1-10 at all radii | not stated | dimensionless | 4 | emission at the ALMA wavelengths is optically thick $\tau\simeq1-10$ at all radii |

## Qualitative findings

- Dark rings have low dust density and small particles; inner features D13, B21, D33 coincide with snow lines, while D67-D77 is consistent with planet-disk interaction  
  > "Dark rings are always associated with low dust density and small particles." (Summary and Conclusions)

## Claim tuples

- H: Have particles in HL Tau grown to mm sizes when scattering is included? | E: Radial SED fit of 0.9–8 mm images with absorption+scattering model | R: a_max ~1.5 mm at center to ~0.5 mm outside | F: Millimeter-sized grains exist; inconsistent with ~100 um from polarization | **supported**
- H: Do rings have different origins? | E: Compare dust properties and temperature-derived snow line positions with rings | R: Inner rings coincide with snow lines; wide gap near 70 au has small particles and gas gap | F: Inner features likely snow-line related, outer planet-related | **partially**
- H: Does ignoring scattering bias results? | E: Repeat fit with absorption-only | R: a_max>>1 cm at R<50 au, lower dust mass and temperature | F: Scattering must be included | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Absorption-only, optically thin assumptions can overestimate sizes and underestimate mass  
  > "leading to overestimation of particle sizes and to underestimation of the disk’s mass" (abstract)
- Alternative: K band excluded due to jet contamination and poor S/N  
  > "adding it to the analysis does not help, but results in larger uncertainties" (2.3 Final images and radial profiles)
- How they decided it was enough: _not stated_
- Limitation (authors): Resolution comparable to ring separations smooths contrasts  
  > "The effect of this is to smooth differences in the obtained paramaters." (4.2 On the Nature of Bright and Dark Rings)
- Caveat (inferred, ours): Single grain composition and p=3.5 fixed; a_max and p are degenerate
- Caveat (inferred, ours): Isotropic scattering and vertically isothermal slab assumptions
- Caveat (inferred, ours): Flux-scale errors treated as sqrt(N epochs) reduction, which is optimistic
- Caveat (inferred, ours): Only 3 free parameters fit to 4 wavelengths

## Reproducibility

- Data public (paper): ALMA images/data from Science Verification webpage  
  > "We downloaded the reference images from the ALMA Science Verification webpage" (2.1 ALMA Observations)
- Products in archive: _not stated_
- Missing: Final VLA images/uv-subtracted data
- Missing: Band 4 calibration script
- Missing: Opacity tables
- Data volume (inferred): ~100s of GB (ALMA long-baseline SV uv data plus VLA)
- Score (inferred): 3/5, Public data and clear model equations, but several processing and fit details unstated and VLA data are not in the archive as given.
- Rediscovery candidate: no, Requires non-public VLA products and unstated opacity and fit settings.

## Links

- Method: Sierra et al. 2019 (Scattering radiative transfer equation used)
- Method: Miyake & Nakagawa (1993) (Analytical slab solution)
- Method: D'Alessio et al. (2001) (Opacity code)
- Companion: ALMA Partnership et al. (2015b) (Original HL Tau ALMA images)
- Companion: Carrasco-González et al. 2016 (VLA Q band data)
- Related: ALMA Long Baseline Science Verification

## Checks

```json
{
 "quotes": 56,
 "quotes_ok": 56,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00015.SV"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 44,
  "rate": 0.564
 },
 "evidence_ok": true
}
```
