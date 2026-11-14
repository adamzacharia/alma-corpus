# A Multifrequency ALMA Characterization of Substructures in the GM Aur Protoplanetary Disk

`2020ApJ...891...48H` | The Astrophysical Journal 2020 | first author: Huang, Jane | arXiv: 2001.11040 | DOI: 10.3847/1538-4357/ab711e

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: What are the dust substructures, spectral index variations, optical depths and gas cavity of the GM Aur disk at high resolution in Bands 4 and 6?  
  > "The continuum observations reveal new dust" (1. INTRODUCTION)
- Target **GM Aur**: coordinates ICRS 04h55m10.981s +30d21m59.376s  
  > "GM Aur (ICRS 04 h 55 m 10 s .981, 30 ◦ 21 ′ 59 ′′ . 376)" (1. INTRODUCTION); z/distance 159 ± 4 pc  
  > "GM Aur (ICRS 04 h 55 m 10 s .981, 30 ◦ 21 ′ 59 ′′ . 376)" (1. INTRODUCTION); distance from Gaia Collaboration et al. 2018  
  > "GM Aur (ICRS 04 h 55 m 10 s .981, 30 ◦ 21 ′ 59 ′′ . 376)" (1. INTRODUCTION)

## Data provenance

- ALMA projects: 2017.1.01151.S, 2018.1.01230.S
- bands: Band 4 (2.1 mm) and Band 6 (1.1 mm)  
  > "ALMA observations of GM Aur were taken at 2.1 mm (Band 4) and 1.1 mm (Band 6)" (2. OBSERVATIONS AND DATA REDUCTION)
- frequencies and spectral setup: Band 4 SPWs at 137.995, 139.932, 149.995, 151.995 GHz, 2 GHz bandwidth, 15.625 MHz channels; Band 6 extended SPWs at 252.505, 254.505, 267.655, 269.005 GHz  
  > "spectral windows (SPWs) centered at 137.995, 139.932, 149.995, and 151.995 GHz, each with a 2 GHz bandwidth and 15.625 MHz channel width." (2. OBSERVATIONS AND DATA REDUCTION)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: Extended and compact configurations in each band  
  > "the disk was observed with an extended configuration to achieve high angular resolution and with a more compact configuration to recover larger scale emission." (2. OBSERVATIONS AND DATA REDUCTION)
- baselines: 15 m to 14900 m  
  > "2017.1.01151.S 2017 October 27 [a] Extended 136 . 995 − 152 . 995 47 135 − 14900 64" (Table 1)
- angular resolution: 57x34 mas (2.1 mm), 45x25 mas (1.1 mm), 107x83 mas (HCO+)  
  > "2.1 mm continuum (B4) 144.988 0 57 × 34 ( − 13 . 2) 0.49 0.012" (Table 2)
- max recoverable scale: _not stated_
- sensitivity: rms 0.012 mJy/beam (2.1 mm), 0.01 mJy/beam (1.1 mm), 1.2 mJy/beam per 0.25 km/s channel (HCO+)  
  > "1.1 mm continuum (B6) 260.745 0.5 45 × 25 (2 . 2) 0.94 0.01 264 . 1 ± 0 . 8" (Table 2)
- time on source: Band 4: 64+32 min; Band 6: 47+47+28 min  
  > "2017.1.01151.S 2018 October 4 Compact 136 . 995 − 152 . 995 48 15 − 2517 32" (Table 1)
- observing dates: 2017 Oct 25-28, 2018 Oct 4 and 18  
  > "2018.1.01230.S 2018 October 18 Compact" (Table 1)
- pi or archival as stated: _not stated_
- Line: HCO+ J=3-2 (267.5576259 GHz)
- External data: Midplane dust temperature model from SED and resolved mm modeling, used for optical depths  
  > "midplane dust temperatures derived in Mac´ıas et al. (2018) through radiative transfer modeling of GM Aur’s SED and resolved millimeter continuum observations." (4.2.1. Constraints on optical depths) [from Macías et al. 2018]
- External data: Stellar mass 1.32 Msun  
  > "a stellar mass of 1.32 M ⊙ (Andrews et al. 2018a)" (4.2.2. Constraints on dust grain sizes) [from Andrews et al. 2018a]
- External data: DSHARP dust opacities  
  > "we adopt the default “DSHARP dust opacities” described in Birnstiel et al. (2018)" (4.2.2. Constraints on dust grain sizes) [from Birnstiel et al. 2018]
- External data: Gas temperature structure from McClure et al. 2016 for comparison with HCO+ brightness temperature  
  > "Using a linear interpolation of the two-dimensional temperature structures from McClure et al. (2016) and Mac´ıas et al. (2018)" (5.2. Constraints on the HCO + distribution and temperature) [from McClure et al. 2016]
- Simulation/model as data: RADMC-3D radiative transfer models (Flat, Thick, Warped ring models) of B84 at 1.1 mm  
  > "we use RADMC-3D (Dullemond 2012) to perform 3D Monte Carlo radiative transfer calculations and generate synthetic observations of three parametric ring models." (4.3. The geometry of B84)

## Processing

### Calibration

- pipeline or manual: ALMA pipeline, then additional CASA processing  
  > "The raw data were calibrated with the ALMA pipeline." (2. OBSERVATIONS AND DATA REDUCTION)
- casa version: CASA v.5.4.0  
  > "was used to perform additional data processing and imaging." (2. OBSERVATIONS AND DATA REDUCTION)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0510+1800 (bandpass and flux); J0438+3004 phase  
  > "the quasar J0510+1800 served as the bandpass and flux calibrator" (2. OBSERVATIONS AND DATA REDUCTION)
- flux scale uncertainty: ~10%  
  > "Uncertainties do not include the ∼ 10% flux calibration uncertainty" (Table 2)
- self calibration: Phase and amplitude self-cal on compact data alone, then combined phase-only self-cal; amplitude self-cal did not improve SNR  
  > "We found that amplitude self-calibration did not improve the SNR of the high-resolution image." (2. OBSERVATIONS AND DATA REDUCTION)

### Imaging

- task: tclean multi-scale multifrequency synthesis  
  > "using the multi-scale, multifrequency synthesis imaging algorithm implemented in the tclean task" (2. OBSERVATIONS AND DATA REDUCTION)
- deconvolver: _not stated_
- weighting robust: Band 4 robust = 0; Band 6 robust = 0.5; HCO+ robust 1.0  
  > "A lower Briggs parameter value (robust = 0) was chosen for Band 4 imaging compared to the Band 6 imaging (robust = 0 . 5)" (2. OBSERVATIONS AND DATA REDUCTION)
- uv taper: Gaussian outer taper for HCO+; 0.06 arcsec taper for low-res continuum  
  > "applying a Gaussian taper of 0 ′′ . 06" (3.2. Continuum spectral index)
- cell size: _not stated_
- image size: _not stated_
- masking: Elliptical CLEAN mask for continuum; manual per-channel masks for HCO+  
  > "CLEAN masks were manually generated for individual channels to encompass the observed emission." (2. OBSERVATIONS AND DATA REDUCTION)
- multiscale scales: Compact: [0,0.15,0.3,0.6,0.9] arcsec; combined: [0,0.075,0.15,0.3,0.525] arcsec; HCO+: [0,0.2,0.5,0.75,1.5] arcsec  
  > "The selected CLEAN scales were [0 ′′, 0 ′′ . 2, 0 ′′ . 5, 0 ′′ . 75, 1 ′′ . 5]." (2. OBSERVATIONS AND DATA REDUCTION)
- continuum subtraction: uvcontsub in uv plane for HCO+  
  > "The uvcontsub task was used to subtract the continuum from the line emission in the uv plane." (2. OBSERVATIONS AND DATA REDUCTION)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: imsmooth to common resolution (57x34 mas; or 110x90 mas)  
  > "smooth to a common resolution of 110 mas × 90 mas." (3.2. Continuum spectral index)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Aperture size selection method for integrated flux  
  > "The mask major axis is selected through a method similar to that used in Ansdell et al. (2016)" (2. OBSERVATIONS AND DATA REDUCTION) [from Ansdell et al. (2016)]
- uv visibility binning  
  > "we follow the example of Hezaveh et al. (2016) for modeling long-baseline ALMA data and bin the visibilities" (4.1. Surface brightness models) [from Hezaveh et al. (2016)]
- Median-stacking procedure for peak brightness temperature  
  > "the median-stacking procedure described in Huang et al. (2018a)" (5.2. Constraints on the HCO + distribution and temperature) [from Huang et al. (2018a)]
- Ring/gap naming nomenclature  
  > "In accordance with the nomenclature from Huang et al. (2018b)" (3.1. Continuum substructures) [from Huang et al. (2018b)]

### Not stated but needed to reproduce (our reading)

- Line-free channels flagged for Band 6 continuum
- Self-calibration solution intervals and number of iterations
- Gaussian taper parameters for the HCO+ cube
- CLEAN thresholds and image size/cell size
- Exact visibility binning and weight handling code for the MCMC fits
- Which data reduction scripts were used (not released)

## Analysis recipe

1. **Calibrate, align and self-calibrate, then image continuum**: ALMA pipeline, fixvis/fixplanets alignment, self-cal, tclean multiscale imaging in each band  
  > "the fixvis and fixplanets tasks were used to align them by applying phase shifts and assigning common labels to the phase centers" (2. OBSERVATIONS AND DATA REDUCTION)
   - software: CASA
   - parameter: Band 4 robust 0, Band 6 robust 0.5  
  > "A lower Briggs parameter value (robust = 0) was chosen for Band 4 imaging compared to the Band 6 imaging (robust = 0 . 5)" (2. OBSERVATIONS AND DATA REDUCTION)
   - fitting: _not stated_
   - validation: Visibility amplitudes consistent within 5% between dates  
  > "We checked that the visibility amplitudes from different dates were consistent within 5% at overlapping spatial frequencies" (2. OBSERVATIONS AND DATA REDUCTION)
2. **Radial profiles and spectral index**: Deproject images, azimuthally average, smooth 1.1 mm to 2.1 mm resolution, compute alpha = log(I1/I0)/log(nu1/nu0)  
  > "the CASA imsmooth task is used to smooth the 1.1 mm continuum image to the same resolution as the 2.1 mm image" (3.2. Continuum spectral index)
   - software: CASA
   - parameter: P.A. = 57.17 deg, i = 53.21 deg, 1 au bins  
  > "deprojecting the continuum images using P. A. = 57 ◦ . 17 and i = 53 ◦ . 21, then averaging the pixel intensities within annular bins one au wide." (3.1. Continuum substructures)
   - assumption: Distance 159 pc; ~10% flux calibration uncertainty per band  
  > "Accounting for the ∼ 10% systematic flux calibration uncertainty in each band and assuming that the probability distribution is Gaussian" (3.2. Continuum spectral index)
   - fitting: _not stated_
   - validation: Compared with Pinilla et al. 2014 disk-averaged index  
  > "This is similar to the disk-averaged spectral index (2 . 94 ± 0 . 44) that Pinilla et al. (2014) measured" (3.2. Continuum spectral index)
3. **Fit axisymmetric surface brightness models in uv plane**: Delta function + Gaussian rings parametrization, vis_sample synthetic visibilities, MCMC, 21 free parameters  
  > "for a total of 21 free parameters." (4.1. Surface brightness models)
   - software: vis_sample, emcee, CASA
   - parameter: 96 walkers, 20,000 steps, 10,000 burn-in; weights scaled down by 2.667  
  > "Each ensemble employs 96 walkers for 20,000 steps, with the first 10,000 steps discarded as burn-in." (4.1. Surface brightness models)
   - assumption: Axisymmetric, geometrically thin  
  > "An axisymmetric model is adopted, given that the azimuthal variations described in Section 3 are modest." (4.1. Surface brightness models)
   - fitting: emcee affine-invariant sampler; uniform priors on profile parameters, Gaussian priors on PA, i, offsets (Table 3); Gaussian likelihood in visibilities  
  > "Uniform priors are adopted for the parameters defining I ν ." (4.1. Surface brightness models)
   - validation: Compared model and residual images/profiles; residuals up to 8.4 sigma at 1.1 mm and 6.8 sigma at 2.1 mm  
  > "Some significant residuals remain, as large as 8.4 σ at 1.1 mm and 6.8 σ at 2.1 mm." (4.1. Surface brightness models)
4. **Optical depth and grain size constraints**: tau_nominal = -ln(1 - I/B(T)); beta from tau ratio; emergent intensity with scattering via analytic slab approximation  
  > "we can use the τ nominal values measured from the 1.1 and 2.1 mm surface brightness models to estimate β in optically thin parts of the disk." (4.2.2. Constraints on dust grain sizes)
   - software: dsharp_opac
   - parameter: p = 3.5, 2.5, 1.5; a_min = 0.1 um; Td = 30 K (B40), 18 K (B84)  
  > "fix the minimum grain size at 0.1 µ m" (4.2.2. Constraints on dust grain sizes)
   - assumption: Midplane temperature from Macías et al. 2018; DSHARP opacities; gas-to-dust ratio 100 for Toomre Q  
  > "assuming the standard gas-to-dust ratio of 100 and a stellar mass of 1.32 M ⊙" (4.2.2. Constraints on dust grain sizes)
   - fitting: _not stated_
   - validation: Alternative formulae from Birnstiel 2018 and Zhu 2019 give similar results; McClure temperature structure tested  
  > "Similar results are obtained using formulae based on the Eddington-Barbier approximation from Birnstiel et al. (2018) and Zhu et al. (2019)." (4.2.2. Constraints on dust grain sizes)
5. **Test B84 geometry with radiative transfer**: RADMC-3D models: flat, thick, warped rings, imaged with CASA and plotted in polar deprojection  
  > "we use RADMC-3D (Dullemond 2012) to perform 3D Monte Carlo radiative transfer calculations" (4.3. The geometry of B84)
   - software: RADMC-3D, vis_sample, CASA
   - parameter: 512 radial cells, 1024 poloidal cells, 64 azimuthal cells, 10^8 photon packages; parameters in Table 4  
  > "64 azimuthal cells spaced evenly between 0 and 2 π, and 10 8 photon packages." (4.3. The geometry of B84)
   - assumption: p = 3.5, a_max = 1 mm; vertically isothermal  
  > "We use a dust population with p = 3 . 5 and a max = 1 mm" (4.3. The geometry of B84)
   - fitting: Parameters adjusted manually until ring width and height match  
  > "The parameters to generate the disk surface density are adjusted manually" (4.3. The geometry of B84)
   - validation: Models illustrative, not best fit  
  > "Thus the models we present should be taken as illustrative, not as a “best fit” to GM Aur." (4.3. The geometry of B84)
6. **HCO+ emission height and kinematics**: Quadratic-fit velocity map with bettermoments, fit Keplerian flared-surface model with eddy  
  > "The lineof-sight velocity corresponding to the emission line peak at each pixel is computed using a quadratic fit" (5.1. The HCO + emitting height)
   - software: bettermoments, eddy, emcee
   - parameter: Fit radii 0.2-2 arcsec; 48 walkers, 3500 steps, 500 burn-in  
  > "sampled with 48 walkers for 3500 steps, with the first 500 steps discarded as burnin." (5.1. The HCO + emitting height)
   - assumption: Keplerian rotation; PA, inclination, offsets fixed to continuum values  
  > "The P. A., inclination, and phase offsets are fixed to the values derived from the continuum visibility modeling" (5.1. The HCO + emitting height)
   - fitting: emcee via eddy; uniform priors (Table 5)  
  > "Broad uniform priors are adopted for the four free parameters" (5.1. The HCO + emitting height)
   - validation: Isovelocity contours compared with channels  
  > "The best-fit model adequately reproduces the geometry of the HCO + emission" (5.1. The HCO + emitting height)
7. **HCO+ integrated flux and brightness temperature**: Keplerian-mask integrated intensity; peak brightness temperature map without continuum subtraction; power-law fit  
  > "The full Planck equation is used to convert peak intensities to brightness temperatures." (5.2. Constraints on the HCO + distribution and temperature)
   - software: CASA, scipy
   - parameter: Integration range -1.25 to 12.75 km/s; fit over R = 30-350 au  
  > "The integration range, − 1 . 25 to 12 . 75 km s − 1, is selected to encompass channels with disk emission above the 3 σ level." (5.2. Constraints on the HCO + distribution and temperature)
   - fitting: Levenberg-Marquardt power law T = T100 (r/100 au)^-q  
  > "Using Levenberg-Marquardt minimization to fit a power law" (5.2. Constraints on the HCO + distribution and temperature)
   - validation: Flux error from 50 noise-only cubes; compared with Macías and McClure temperature models  
  > "The flux uncertainty is estimated by generating 50 image cubes consisting only of noise" (5.2. Constraints on the HCO + distribution and temperature)

## Software

- **CASA** 5.4.0: Calibration follow-up, self-cal, imaging, imsmooth, uvcontsub  
  > "CASA v.5.4.0 (McMullin et al. 2007) was used to perform additional data processing and imaging." (2. OBSERVATIONS AND DATA REDUCTION)
- **emcee** : MCMC sampling of continuum and HCO+ height models  
  > "sampled with the emcee implementation of the affine invariant MCMC sampler" (4.1. Surface brightness models)
- **vis_sample** : Synthetic visibilities from model images  
  > "Using the Python package vis sample (Loomis et al. 2018), synthetic visibilities V m are produced" (4.1. Surface brightness models)
- **RADMC-3D** : 3D radiative transfer ring models  
  > "we use RADMC-3D (Dullemond 2012)" (4.3. The geometry of B84)
- **eddy** : Fit HCO+ emission surface  
  > "We use the Python packages bettermoments and eddy" (5.1. The HCO + emitting height)
- **bettermoments** : Line-of-sight velocity map  
  > "We use the Python packages bettermoments and eddy" (5.1. The HCO + emitting height)
- **dsharp_opac** v1.1.0: Dust opacities and beta  
  > "use the companion Python package dsharp opac (Birnstiel 2018)" (4.2.2. Constraints on dust grain sizes)
- **scipy.optimize.curve_fit** : Gaussian fits to B84 profile  
  > "using the Levenberg-Marquardt minimization implementation in scipy.optimize.curve f it" (3.1. Continuum substructures)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 1.1 mm continuum flux | 264.1 | ±0.8 (excl. ~10% calibration) | mJy | 1 | 264 . 1 ± 0 . 8 |
| 2.1 mm continuum flux | 54.8 | ±0.7 (excl. ~10% calibration) | mJy | 1 | 54 . 8 ± 0 . 7 |
| Disk-averaged spectral index 1.1-2.1 mm | 2.7 | ±0.2 | dimensionless | 2 | the disk-averaged spectral index between 1.1 and 2.1 mm is α = 2 . 7 ± 0 . 2 |
| Peak nominal optical depth B40 and B84 at 1.1 mm | 0.94 and 0.70 | not stated | dimensionless | 4 | ( τ nominal = 0 . 94 and 0 . 70, respectively) |
| Inclination from 1.1 mm fit | 53.20 | ±0.01 | degree | 3 | 53 . 20 ± 0 . 01 |
| HCO+ emission height z0 | 0.127 | ±0.002 | arcsec | 6 | 0 . 127 ± 0 . 002 |
| HCO+ flaring index psi | 0.81 | ±0.03 | dimensionless | 6 | 0 . 81 ± 0 . 03 |
| Stellar mass from HCO+ kinematics | 1.206 | ±0.004 | Msun | 6 | 1 . 206 ± 0 . 004 |
| HCO+ brightness temperature T100 | 26.9 | ±3 (+10% flux calibration) | K | 7 | T 100 = 26 . 9 ± 3 and q = 0 . 43 ± 0 . 01 |
| HCO+ temperature power-law index q | 0.43 | ±0.01 | dimensionless | 7 | T 100 = 26 . 9 ± 3 and q = 0 . 43 ± 0 . 01 |
| Central unresolved flux within 100 mas | 0.28 (1.1 mm), 0.09 (2.1 mm) | ±0.02 each | mJy | 2 | 0 . 28 ± 0 . 02 mJy at 1.1 mm and 0 . 09 ± 0 . 02 mJy at 2.1 mm |
| HCO+ integrated flux | 6960 | ±60 | mJy km/s | 7 | 6960 ± 60 |

## Qualitative findings

- Dust disk has at least three rings (B40, B84, B168) atop faint extended emission and a central unresolved source; the 2.1 mm image shows a shoulder on B40  
  > "The dust continuum shows at least three rings atop faint, extended emission." (abstract)
- HCO+ gas cavity is smaller than the dust cavity  
  > "the HCO + emission indicates that the gas cavity is more compact than the dust cavity traced by the millimeter continuum" (abstract)

## Claim tuples

- H: Do spectral index variations trace grain trapping or optical depth in the rings? | E: uv-plane surface brightness fits, tau_nominal, scattering calculations | R: Gaps and outer disk (R>100 au) optically thin; B40 and B84 tau_nominal up to 0.94 and 0.70 | F: Ring dust properties are ambiguous, but the dust population is not radially uniform | **partially**
- H: Is B84's inner edge at different inclination than the outer edge, and why? | E: Polar deprojection and RADMC-3D flat/thick/warped models | R: Thick and warped models reproduce the undulating inner contour | F: Vertical structure or mild warp are plausible | **partially**
- H: What produces the central compact emission? | E: Flux comparison at 1.1 and 2.1 mm, free-free extrapolation, SED comparison | R: Spectral index 1.9; free-free ~55-58 uJy | F: Large dust grains plus free-free emission | **partially**
- H: Is the gas cavity smaller than the dust cavity? | E: HCO+ J=3-2 imaging and integrated intensity | R: HCO+ peaks at ~20 au, interior to B40 | F: Gas cavity smaller than mm dust cavity | **supported**

## Reasoning

- Why this data: HCO+ chosen to test kinematic disturbance without cloud contamination  
  > "HCO + was targeted to investigate previous claims of a significant kinematic disturbance in the GM Aur disk with a line that is not afflicted by cloud contamination." (1. INTRODUCTION)
- Why this method: _not stated_
- Alternative: Optically thick free-free emission rejected as origin of inner disk mm emission  
  > "it is unlikely that the inner disk millimeter emission of GM Aur originates from optically thick freefree emission." (6.2. Origin of the central compact emission)
- How they decided it was enough: _not stated_
- Limitation (authors): Temperature, flux calibration and degeneracies prevent precise grain size measurements  
  > "the aim of this section is to comment on which regions of parameter space are consistent with the observations rather than to provide precise measurements." (4.2.2. Constraints on dust grain sizes)
- Caveat (inferred, ours): Results depend on Macías et al. 2018 temperature model, which disagrees with HCO+ temperatures by 30-40%
- Caveat (inferred, ours): RT models are illustrative and manually tuned
- Caveat (inferred, ours): Only two continuum bands, so grain size, density and temperature are degenerate

## Reproducibility

- Data public (paper): Project codes given in acknowledgments  
  > "This paper makes use of ALMA data" (7. SUMMARY)
- Products in archive: _not stated_
- Missing: Self-cal solution intervals
- Missing: Taper values for HCO+
- Missing: Image size and cell size
- Missing: Scripts for modeling not released
- Data volume (inferred): ~200-500 GB raw for five execution blocks
- Score (inferred): 3/5, Data public and the modeling approach is well described with priors and MCMC settings, but several imaging and self-cal parameters and the thermal model inputs are missing.
- Rediscovery candidate: yes, Public data and a described recipe with numeric results (fluxes, spectral index, table of fit parameters), though some settings are unstated.

## Links

- Method: Birnstiel et al. 2018 (DSHARP dust opacities)
- Method: Sierra et al. 2019; Carrasco-González et al. 2019 (Analytic emergent intensity with scattering)
- Method: Teague & Foreman-Mackey 2019 (bettermoments)
- Companion: Macías et al. 2018 (Previous GM Aur multiwavelength modeling and temperature structure)
- Companion: Qi et al. 2019 (N2H+ in GM Aur)
- Related: DSHARP

## Checks

```json
{
 "quotes": 97,
 "quotes_ok": 97,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 1,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 97,
  "stated": 77,
  "rate": 0.794
 },
 "evidence_ok": true
}
```
