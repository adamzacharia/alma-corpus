# An Inner Disk in the Large Gap of the Transition Disk SR 24S

`2019ApJ...878...16P` | The Astrophysical Journal 2019 | first author: Pinilla, Paola | arXiv: 1904.11517 | DOI: 10.3847/1538-4357/ab1cb8

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: Does the multiwavelength (0.45, 1.3, 2.75 mm) dust continuum structure of the SR 24S transition disk, including an inner disk, reveal the origin of its large cavity?  
  > "We use this multiwavelength comparison to better understand the potential origin of the cavity observed in SR 24S." (Introduction)
- Target **SR 24S**: coordinates 16:26:58.51 -24:45:37.24 (J2000)  
  > "assuming a distance of 114.4 pc $\pm$4.8 pc (cite: gaia2018)" (3.1 Dust morphology and comparison with previous ALMA observations); "The obtained center was $\alpha_{2000}$=16:26:58.51, $\delta_{2000}$=-24:45:37.24" (2 Observations); z/distance 114.4 pc ± 4.8 pc  
  > "assuming a distance of 114.4 pc $\pm$4.8 pc (cite: gaia2018)" (3.1 Dust morphology and comparison with previous ALMA observations); "The obtained center was $\alpha_{2000}$=16:26:58.51, $\delta_{2000}$=-24:45:37.24" (2 Observations); distance from Gaia (Gaia Collaboration 2018)  
  > "assuming a distance of 114.4 pc $\pm$4.8 pc (cite: gaia2018)" (3.1 Dust morphology and comparison with previous ALMA observations); "The obtained center was $\alpha_{2000}$=16:26:58.51, $\delta_{2000}$=-24:45:37.24" (2 Observations)

## Data provenance

- ALMA projects: 2017.1.00884.S
- bands: Band 3 (2.75 mm), plus earlier Band 6 and Band 9  
  > "for a mean frequency of $\sim$109 GHz or a wavelength of 2.75 mm" (2 Observations)
- frequencies and spectral setup: four spectral windows: two at 107.9 GHz, one at 110.2 GHz, one at 109.8 GHz  
  > "two of them centered at $107.9$ GHz, one at $110.2$ GHz, and the other one at $109.8$ GHz" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 138 m to 13894.4 m, 43 antennas  
  > "43 antennas were used, with a baseline range from 138 m to 13894.4 m" (2 Observations)
- angular resolution: 0.106'' x 0.088''  
  > "The final beam size was 0.106$''$$\times$0.088$''$" (2 Observations)
- max recoverable scale: 1.1 arcsec  
  > "In our observations, the maximum recoverable scale (MRS) is 1.1$''$." (3.2 Disk dust mass and spectral index)
- sensitivity: rms ~38 uJy/beam  
  > "achieving a rms of $\sim$38 $\mu$Jy beam$^{-1}$" (2 Observations)
- time on source: 22.5 min total, ~8 min on source  
  > "The total observing time was 22.5 mins, with a total on-source time of $\sim$8 min." (2 Observations)
- observing dates: November 9th, 2017 (Cycle 5)  
  > "during Cycle 5 on November 9th, 2017" (2 Observations)
- pi or archival as stated: _not stated_
- Line: 13CO 1-0 (110.20 GHz)
- Line: C18O 1-0 (109.78 GHz)
- Other facility **ALMA Cycle 0 Band 9 and Cycle 2 Band 6**: previous 0.45 mm and 1.3 mm observations  
  > "The details of the ALMA Cycle 0 and Cycle 2 observations (0.45 mm and 1.30 mm, respectively)" (2 Observations)
- Other facility **ATCA**: 3 mm flux of 26.6 mJy for comparison  
  > "Australia Telescope Compact Array (ATCA) observations at 3 mm of 26.6 mJy" (3.2 Disk dust mass and spectral index)
- Other facility **VLA**: 3.3 cm data from Zapata et al. used in the SED comparison  
  > "obtained 3.3 cm observations of 10 TDs with the Jansky Very Large Array (VLA), including SR 24S" (4.1 Origin of the emission from the inner disk)
- External data: Band 6 and Band 9 visibilities and calibration  
  > "are explained in (cite: marel2015) and (cite: pinilla2017)" (2 Observations) [from (cite: marel2015); (cite: pinilla2017)]
- External data: Total flux at 1.3 mm of 220 mJy  
  > "Using the total flux at 1.3 mm of 220 mJy (cite: pinilla2017)" (3.2 Disk dust mass and spectral index) [from (cite: pinilla2017)]
- External data: Accretion rate ~3e-8 Msun/yr  
  > "the accretion rate of $\sim3\times10^{-8}$ $M_{\odot}$  year$^{-1}$ (cite: natta2006)" (4.2 Origin of the large gap and ring-like structure) [from (cite: natta2006)]
- Simulation/model as data: Dust evolution models of 1 MJup planet at 20 au vs dead zone to 20 au, after 1 Myr, compared qualitatively  
  > "the case of an 1 $M_{\rm{Jup}}$ planet embedded a 20 au distance from the star as compared to the case of a dead zone extended up to 20 au" (4.2 Origin of the large gap and ring-like structure)

## Processing

### Calibration

- pipeline or manual: CASA calibration; self-calibration performed  
  > "The data were calibrated using the Common Astronomy Software Package (cite: mcmullin2007)." (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: QSO J1427-4206 (bandpass and flux)  
  > "The quasar QSO J1427-4206 was observed for bandpass and flux calibration" (2 Observations)
- flux scale uncertainty: 10%  
  > "10% of uncertainty from absolute flux calibration" (3.2 Disk dust mass and spectral index)
- self calibration: performed, slightly improved S/N  
  > "We performed self-calibration, which slightly improved the signal-to-noise ratio of the data compared to the delivered data." (2 Observations)

### Imaging

- task: clean  
  > "Continuum imaging was performed using the `clean` algorithm." (2 Observations)
- deconvolver: _not stated_
- weighting robust: natural  
  > "We used the natural weighting scheme to obtain the best sensitivity possible." (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Band 3 and Band 6 imaged with common circular 0.19'' beam for comparison  
  > "we imaged with the same circular beam of 0.19$''$and deprojected the two data sets for comparison" (3.1 Dust morphology and comparison with previous ALMA observations)
- final beam: 0.106'' x 0.088''  
  > "The final beam size was 0.106$''$$\times$0.088$''$" (2 Observations)
- final rms: ~38 uJy/beam  
  > "achieving a rms of $\sim$38 $\mu$Jy beam$^{-1}$" (2 Observations)

### Inherited from earlier work

- Band 6/Band 9 observations and calibration  
  > "are explained in (cite: marel2015) and (cite: pinilla2017)" (2 Observations) [from (cite: marel2015); (cite: pinilla2017)]
- MCMC fitting procedure  
  > "We follow the same procedure as in (cite: pinilla2017)." (3.3 Fit of the dust morphology in the visibility plane) [from (cite: pinilla2017)]
- Dust evolution/hydrodynamic model details  
  > "The details of these simulations are presented in (cite: pinilla2012; pinilla2015; pinilla2016a)." (4.2 Origin of the large gap and ring-like structure) [from (cite: pinilla2012; pinilla2015; pinilla2016a)]

### Not stated but needed to reproduce (our reading)

- clean parameters: cell size, image size, mask, niter, threshold
- self-calibration solution intervals and number of rounds
- whether lines were flagged before the continuum was made, and how
- binning of visibilities in the fit
- likelihood form for MCMC and burn-in
- details of the Band 6/9 data reprocessing
- planet/dead-zone model parameters other than mass and radius

## Analysis recipe

1. **Centre data and get geometry**: Gaussian fit with uvmodelfit; phase centre corrected with fixvis  
  > "the data were correctly centered by fitting a simple Gaussian to the data, using `uvmodelfit`" (2 Observations)
   - software: CASA
   - parameter: PA 26.8±1.3 deg, inclination 47.6±2.4 deg  
  > "the position angle (PA) and inclination were $26.8^{\circ}\pm{1.3}^{\circ}$ and $47.6^{\circ}\pm{2.4}^{\circ}$" (2 Observations)
   - fitting: _not stated_
   - validation: agreement with previous observations  
  > "in agreement with previous observations (cite: marel2015; fernandez2017; pinilla2017)" (2 Observations)
2. **Image continuum and radial profiles**: clean with natural weighting; deprojected azimuthally averaged radial profiles  
  > "azimuthally averaged radial profiles from the deprojected images and assuming a distance of 114.4 pc" (3.1 Dust morphology and comparison with previous ALMA observations)
   - software: CASA
   - assumption: distance 114.4 pc  
  > "assuming a distance of 114.4 pc $\pm$4.8 pc (cite: gaia2018)" (3.1 Dust morphology and comparison with previous ALMA observations)
   - fitting: _not stated_
   - validation: _not stated_
3. **Optical depth, dust mass and spectral index**: optically thin dust mass from flux; tau from brightness temperature; spectral index from 1.3 and 2.75 mm fluxes  
  > "the dust disk mass can be calculated as $M_{\mathrm{dust}}\simeq\frac{{d^2 F_\nu}}{\kappa_\nu B_\nu (T(r))}$" (3.2 Disk dust mass and spectral index)
   - assumption: kappa=2.3 cm2/g (nu/230GHz)^0.4, T=20 K  
  > "$\kappa_\nu=2.3\,$cm$^{2}$ g$^{-1}\times(\nu/230\,\rm{GHz})^{0.4}$ (cite: andrews2013), and a dust temperature of 20 K" (3.2 Disk dust mass and spectral index)
   - fitting: _not stated_
   - validation: flux compared with ATCA 3 mm  
  > "the 2.75 mm flux from our observations is in good agreement with the flux obtained from the Australia Telescope Compact Array (ATCA)" (3.2 Disk dust mass and spectral index)
4. **Fit visibility-plane ring models**: fit the real part of the visibilities with 3 models (asymmetric Gaussian ring; plus point source; plus central Gaussian) at each of three bands  
  > "We focused on fitting the real part of the visibilities because the emission is mainly axisymmetric." (3.3 Fit of the dust morphology in the visibility plane)
   - software: emcee
   - parameter: 200 walkers, 2000 steps, uniform priors (r_peak 10-80 au, sigma 1-50 au, A 0-1, sigma_inner 0.1-10 au, F_total 0-3 Jy)  
  > "We explored the free parameters with 200 walkers and 2000 steps in each case." (3.3 Fit of the dust morphology in the visibility plane)
   - fitting: MCMC with emcee, uniform priors  
  > "we used the Markov chain Monte Carlo (MCMC) method, and we used *emcee* (cite: foreman2013)" (3.3 Fit of the dust morphology in the visibility plane)
   - validation: BIC model comparison  
  > "we obtain the Bayesian Information Criterion (BIC)" (3.3 Fit of the dust morphology in the visibility plane)
5. **Compare with cavity-formation models**: qualitative comparison of normalized intensity profiles with planet and dead-zone dust evolution models convolved with an 11 au beam  
  > "We convolved these intensity profiles with a Gaussian beam of 11 au" (4.2 Origin of the large gap and ring-like structure)
   - assumption: Mie opacities with Ricci et al. 2010 optical constants; temperature power law index -1/2  
  > "we took a simple power-law for the radial dependence of the midplane temperature (power-law index of $-1/2$)" (4.2 Origin of the large gap and ring-like structure)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : calibration and imaging (clean, uvmodelfit, fixvis)  
  > "The data were calibrated using the Common Astronomy Software Package (cite: mcmullin2007)." (2 Observations)
- **emcee** : MCMC visibility fits  
  > "we used the Markov chain Monte Carlo (MCMC) method, and we used *emcee* (cite: foreman2013)" (3.3 Fit of the dust morphology in the visibility plane)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Band 3 total flux density from image | 28.9 | not stated | mJy | 2 | The total flux density and the peak brightness from the image is 28.9 mJy |
| Band 3 ring peak radius | 37.10 | +0.45/-0.44 | au | 4 | 37.10$^{+0.45}_{-0.44}$ |
| Dust mass from image flux | 55.3 | 7.3 | Earth masses | 3 | 55.3 $M_{\oplus}\pm$7.3 $M_{\oplus}$ |
| Dust mass from fitted flux | 58.3 | 7.7 | Earth masses | 4 | which gives a dust disk mass of 58.3$\pm$7.7 $M_{\oplus}$ |
| Spatially integrated spectral index | 2.7 | 0.03 | dimensionless | 3 | the spatially integrated spectral index is 2.7$\pm$0.03 |
| Inner disk spectral index (within 20 au) | ~2.2 | not stated | dimensionless | 4 | The spectral index derived from these fluxes is $\sim$2.2 |
| Band 3 inner disk flux in 75 mas aperture | ~0.46 | not stated | mJy | 2 | The total flux density inside a circular aperture of 75 mas radius is $\sim$0.46 mJy |
| Band 3 optical depth peak | 0.37 | not stated | dimensionless | 3 | with a maximum value of $\tau$ at the peak of emission of 0.37 |

## Qualitative findings

- Ring is radially asymmetric with outer width larger than inner width at all three bands, and total width decreases at longer wavelength  
  > "the total width ($\sigma_{\rm{int}}+\sigma_{\rm{ext}}$) decreases at longer wavelength" (3.3 Fit of the dust morphology in the visibility plane)

## Claim tuples

- H: Is the 2.75 mm inner disk thermal dust emission rather than free-free? | E: Spectral index inside 20 au from best-fit models at 1.3 and 2.75 mm, plus resolved size | R: Spectral index ~2.2, inner disk resolved (3-5 au) | F: Inner disk emission likely dominated by dust thermal emission | **partially**
- H: Which mechanism opens the SR 24S cavity? | E: Compare multiwavelength ring morphology with photoevaporation, dead zone and planet models | R: Photoevaporation excluded by cavity size and accretion rate; dead zone predicts inward peak shift not seen | F: Planet(s) scenario favoured | **supported**
- H: Does the inner disk constrain planet mass and turbulence? | E: Interpret the inner disk with published dust evolution models | R: Inner disk requires dust passage across gap | F: Single planet upper limit ~5 MJup and alpha ~1e-4 to 1e-3 | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Photoevaporation rejected from cavity size ~35 au and accretion rate ~3e-8 Msun/yr  
  > "exclude the possibility of photoevaporation" (4.2 Origin of the large gap and ring-like structure)
- How they decided it was enough: _not stated_
- Limitation (authors): Dust opacity uncertainty not included in mass errors; possible flux loss from missing short baselines  
  > "The potentially large uncertainty in the dust opacity is not taken into account." (3.2 Disk dust mass and spectral index)
- Caveat (inferred, ours): Comparison with models is only qualitative
- Caveat (inferred, ours): Band 9 resolution is poor, so ring shift is poorly constrained
- Caveat (inferred, ours): Single-dish-like flux agreement with ATCA does not prove no flux loss
- Caveat (inferred, ours): Model-dependent mass and alpha limits

## Reproducibility

- Data public (paper): Project code given and acknowledged as ADS/JAO.ALMA#2017.1.00884.S  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00884.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: clean parameters
- Missing: self-calibration details
- Missing: Band 6 and 9 data processing
- Missing: hydrodynamic and dust evolution model inputs
- Data volume (inferred): tens of GB for the Band 3 data, more with Band 6 and Band 9
- Score (inferred): 3/5, Data public and fitting approach clear with priors, but imaging and self-calibration parameters missing and model comparison relies on earlier papers.
- Rediscovery candidate: yes, Public data and numeric visibility fit results, with the recipe largely stated.

## Links

- Method: (cite: pinilla2017) (MCMC fitting procedure and Band 6/9 data)
- Companion: (cite: marel2015) (Band 9 observations)

## Checks

```json
{
 "quotes": 69,
 "quotes_ok": 69,
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
  "facts": 78,
  "stated": 51,
  "rate": 0.654
 },
 "evidence_ok": true
}
```
