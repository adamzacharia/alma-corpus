# Constraints on a Putative Planet Sculpting the V4046 Sagittarii Circumbinary Disk

`2019AJ....157..237R` | The Astronomical Journal 2019 | first author: Ruíz-Rodríguez, Dary | arXiv: 1904.09866 | DOI: 10.3847/1538-3881/ab1c58

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: What are the dust ring/gap structures of the V4046 Sgr circumbinary disk in 870 um continuum and H-band scattered light, and what mass of a putative planet at 20 au could produce them?  
  > "Using synthetic 870 $\ensuremath{\mu}m$ and H-band images obtained from disk-planet interaction simulations, we attempt to constrain the mass of the putative planet orbiting at 20 au." (abstract)
- Target **V4046 Sgr**: coordinates RA 18h14m10.47s, Dec -32d47m34.50s (J2000, phase center)  
  > "The phase center of the observations is $\alpha$ (J2000) = 18$^{\rm h}$ 14$^{\rm
  m}$ 10.47$^{\rm s}$ ; $\delta$ (J2000) = -32$^{\rm o}$47$^{\rm '}$ 34.50$^{\rm ''}$." (ALMA Observations); "The V4046 Sgr system lies at a mere 72.47$\pm$0.34 pc (cite: Gaia2018)" (Introduction); z/distance 72.47±0.34 pc (72.4 pc adopted)  
  > "The phase center of the observations is $\alpha$ (J2000) = 18$^{\rm h}$ 14$^{\rm
  m}$ 10.47$^{\rm s}$ ; $\delta$ (J2000) = -32$^{\rm o}$47$^{\rm '}$ 34.50$^{\rm ''}$." (ALMA Observations); "The V4046 Sgr system lies at a mere 72.47$\pm$0.34 pc (cite: Gaia2018)" (Introduction); distance from Gaia DR2 (Gaia2018)  
  > "The phase center of the observations is $\alpha$ (J2000) = 18$^{\rm h}$ 14$^{\rm
  m}$ 10.47$^{\rm s}$ ; $\delta$ (J2000) = -32$^{\rm o}$47$^{\rm '}$ 34.50$^{\rm ''}$." (ALMA Observations); "The V4046 Sgr system lies at a mere 72.47$\pm$0.34 pc (cite: Gaia2018)" (Introduction)

## Data provenance

- ALMA projects: 2016.1.00315.S
- bands: Band 7 (345 GHz), 870 um  
  > "ALMA Band 7 (345 GHz) observations of V4046 Sgr were obtained on May 09, 2017" (ALMA Observations)
- frequencies and spectral setup: four SPWs centered at 330.616, 345.825, 344.031, 332.531 GHz; bandwidths 937.5, 468.8, 2000.0, 2000.0 MHz; continuum from the two 2 GHz SPWs  
  > "centered at 330.616 GHz, 345.825 GHz, 344.031 GHz, and 332.531GHz, and the bandwidths used were 937.5, 468.8, 2000.0 and 2000.0 MHz, respectively." (ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C40-5, longest baseline 1.1 km  
  > "The array configuration was C40-5 with a longest baseline of 1.1 km." (ALMA Observations)
- baselines: _not stated_
- angular resolution: 0.29"x0.17" (R=-0.5); 0.2"x0.1" (R=-2)  
  > "a synthesized beam of 0.29$^{''}$$\times$ 0.17$^{''}$ at P.A. -79.7$^{\rm o}$" (ALMA Observations)
- max recoverable scale: _not stated_
- sensitivity: rms 0.10 mJy/beam (R=-0.5); 0.18 mJy/beam (R=-2)  
  > "The resulting rms was 0.10 mJy beam$^{-1}$ within a bandwidth of 5.29 GHz" (ALMA Observations)
- time on source: 11.7 minutes  
  > "The total on-source integration time was 11.7 minutes." (ALMA Observations)
- observing dates: May 09, 2017  
  > "observations of V4046 Sgr were obtained on May 09, 2017" (ALMA Observations)
- pi or archival as stated: _not stated_
- Other facility **VLT SPHERE/IRDIS**: archival H-band polarimetric differential images (2016-03-13)  
  > "The archival H-band polarimetric images of V4046 Sgr presented in this work were obtained on March 13, 2016" (SPHERE Observations)
- External data: Library of fiducial hydrodynamic+MCRT planet-disk models used for synthetic images  
  > "we used the library of fiducial hydrodynamical models presented in (cite: Dong2015) to explore a range of ad hoc planet masses" (Constraints on Putative Planet Mass) [from Dong, Zhu & Whitney 2015 (cite: Dong2015)]
- External data: Stellar mass 1.75 Msun for central binary  
  > "the central source can be considered a single star of mass 1.75 M$_{\odot}$ (cite: Rosenfeld2012)" (Constraints on Putative Planet Mass) [from (cite: Rosenfeld2012)]
- External data: Dust opacity 0.02 cm2/g at 870 um, beta=1.5  
  > "we adopt 0.02 $\rm cm^{2} g^{-1}$ at 870 $\ensuremath{\mu}m$ with $\beta$ = 1.5; (cite: Beckwith1990)" (Disk Mass) [from (cite: Beckwith1990)]
- Simulation/model as data: Planet-disk models with 0.3 and 1.5 MJup planet at 20 au, inclination 32 deg, synthetic H-band and 870 um images  
  > "the radial location of the forming planet is fixed in a circular orbit at the location of the gap, i.e., 20 au." (Constraints on Putative Planet Mass)

## Processing

### Calibration

- pipeline or manual: ALMA pipeline r39732 in CASA 4.7.2  
  > "edited, calibrated and imaged using the pipeline version r39732 in CASA 4.7.2" (ALMA Observations)
- casa version: CASA 4.7.2  
  > "edited, calibrated and imaged using the pipeline version r39732 in CASA 4.7.2" (ALMA Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1823-3454 (flux); J1826-2924 phase; J1924-2914 bandpass  
  > "J1823-3454 was used as flux calibrator, while the quasar J1924-2914 was observed for bandpass calibration." (ALMA Observations)
- flux scale uncertainty: 10% assumed  
  > "83.0 $\pm$ 8.0 mJy (assuming a 10% flux calibration accuracy)" (An Inner Ring in the mm Continuum?)
- self calibration: three rounds of phase calibration  
  > "We applied self-calibration with three rounds of phase calibration" (ALMA Observations)

### Imaging

- task: tclean  
  > "used the TCLEAN algorithm to image the data using two different Briggs weighting values" (ALMA Observations)
- deconvolver: _not stated_
- weighting robust: robust -0.5 (main); -2 (uniform)  
  > "we set the Briggs weighting (robust) parameter $R$ to $-0.5$" (ALMA Observations)
- uv taper: _not stated_
- cell size: 20 mas  
  > "The images were constructed on a 256 $\times$ 256 pixel grid with 20 mas pixel size." (ALMA Observations)
- image size: 256 x 256 pixels  
  > "The images were constructed on a 256 $\times$ 256 pixel grid with 20 mas pixel size." (ALMA Observations)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.29"x0.17" PA -79.7 deg (R=-0.5)  
  > "a synthesized beam of 0.29$^{''}$$\times$ 0.17$^{''}$ at P.A. -79.7$^{\rm o}$" (ALMA Observations)
- final rms: 0.10 mJy/beam (R=-0.5); 0.18 mJy/beam (R=-2)  
  > "with rms of 0.18 mJy beam$^{-1}$" (ALMA Observations)

### Inherited from earlier work

- SPHERE polarimetric reduction following earlier procedure  
  > "Polarimetric images were then further reduced following the procedure described in (cite: Avenhaus2014; Avenhaus2018)." (SPHERE Observations) [from (cite: Avenhaus2014; Avenhaus2018)]
- Hydro + MCRT model setup and optical properties  
  > "More details of the disk setup and optical properties can be found in (cite: Dong2012) and (cite: Dong2015)." (Nominal Model) [from (cite: Dong2012; Dong2015)]

### Not stated but needed to reproduce (our reading)

- clean threshold, niter and masks
- self-calibration solution intervals and reference antenna
- uvmodelfit starting parameters and component type details
- how the three-Gaussian fits were initialized
- simobserve configuration, integration time and noise settings
- gas surface density, viscosity, scale height and mass of the Dong2015 models
- wedge and annulus definitions for the radial profiles
- continuum SPW selection details (5.29 GHz bandwidth vs 2 GHz SPWs)

## Analysis recipe

1. **Calibrate and image the continuum**: Pipeline calibration, three rounds of phase self-cal, tclean at robust -0.5 and -2  
  > "We applied self-calibration with three rounds of phase calibration, and used the TCLEAN algorithm to image the data using two different Briggs weighting values." (ALMA Observations)
   - software: CASA, tclean
   - parameter: 20 mas pixels, 256x256  
  > "The images were constructed on a 256 $\times$ 256 pixel grid with 20 mas pixel size." (ALMA Observations)
   - fitting: _not stated_
   - validation: The two robust values give comparable integrated flux densities  
  > "The two Briggs weighting values provide comparable integrated flux densities." (ALMA Observations)
2. **Fit inclination, PA and flux in visibility domain**: Elliptical Gaussian fit to visibilities with uvmodelfit  
  > "we estimated the inclination, position angle and continuum flux density by fitting an elliptical Gaussian directly to the visibility data." (Inclination and P.A.)
   - software: CASA uvmodelfit
   - fitting: single-component elliptical Gaussian  
  > "which fits a single component source model (i.e., point-source, Gaussian, or disk) to the ($u,v$) visibility data." (Inclination and P.A.)
   - validation: Inclination verified with short baselines 0-450 klambda  
  > "We verified the inclination by using only short baselines within the $u,v$ range 0–450 k$\lambda$" (Inclination and P.A.)
3. **Deproject and fit radial profiles**: Deproject ALMA and SPHERE images; azimuthally average ALMA, 20-deg major-axis wedges for SPHERE; fit superposition of three Gaussians  
  > "We achieved these fits with a superposition of an average of three Gaussians for every profile" (Radial Profiles)
   - parameter: wedge opening angle 20 deg  
  > "averages over wedges with opening angles of 20$^{\circ}$ oriented along the disk major axis" (Radial Profiles)
   - fitting: Gaussian fits  
  > "We then extracted radial profiles from the deprojected images and performed Gaussian fitting, so as to characterize the properties of the flux maxima." (3.1.2 Radial Profiles)
   - validation: _not stated_
4. **Estimate dust mass**: Optically thin M_dust = F d^2/(kappa B(T)) with T=15 K (brightness temperature)  
  > "To estimate $T_{dust}$, we adopt the brightness temperature calculated from the peak flux per beam, $T_B \sim 15$ K." (Disk Mass)
   - assumption: gas-to-dust ratio ~100, kappa=0.02 cm2/g at 870 um, isothermal  
  > "assuming isothermal emission and the canonical interstellar medium (ISM) gas-to-dust ratio of $\sim$100" (Disk Mass)
   - fitting: _not stated_
   - validation: Compared with T=30 K (factor 2 smaller); emission likely optically thick so value is lower limit  
  > "most likely represents a lower limit on the dust mass within the ring imaged by ALMA." (Disk Mass)
5. **Compare with planet-disk synthetic images**: Dong2015 FARGO two-fluid + HOCHUNK3D MCRT models for planets of different mass at 20 au; ALMA synthetic images via simobserve/simanalyze; H-band convolved to 0.04"; profiles compared with observations  
  > "the simulated ALMA images were produced by using *simobserve* and *simanalyze* tasks in CASA" (Constraints on Putative Planet Mass)
   - software: FARGO, HOCHUNK3D, CASA simobserve, CASA simanalyze
   - parameter: planet at 20 au, inclination 32 deg, central mass 1.75 Msun  
  > "We adopt the disk inclination of 32$^{\rm o}$ deduced from modeling the continuum emission" (Constraints on Putative Planet Mass)
   - assumption: viscosity and scale height fixed; only planet mass varied  
  > "only the mass of the planet is varied in our limited explorations" (Discussion)
   - fitting: No formal fit; qualitative comparison of ring radius and FWHM and gap depth  
  > "We emphasize that the models are not fine tuned to fit the observations; instead, they are generic models with parameterized profiles, and only the mass of the planet is varied in our limited explorations." (Discussion)
   - validation: _not stated_

## Software

- **CASA** 4.7.2: calibration, imaging, uvmodelfit, simobserve/simanalyze  
  > "using the pipeline version r39732 in CASA 4.7.2" (ALMA Observations)
- **uvmodelfit** : visibility-domain Gaussian fit  
  > "we used the CASA routine *uvmodelfit* (cite: Marti2014)" (Inclination and P.A.)
- **FARGO** : 2D two-fluid hydrodynamic simulations  
  > "2D (radial and azimuthal) two-fluid simulations were obtained using the FARGO code (cite: Masset2000)" (Nominal Model)
- **HOCHUNK3D** : Monte Carlo radiative transfer synthetic images  
  > "the radiative transfer package HOCHUNK3D is utlized (cite: Whitney2013)" (Nominal Model)
- **EsoReflex SPHERE IRDIS workflow** EsoReflex 2.8.5; workflow 0.31.0: SPHERE data reduction  
  > "reduced and analyzed using the EsoReflex pipeline (v. 2.8.5) and the SPHERE IRDIS workflow (v. 0.31.0)" (SPHERE Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Disk inclination | 32.42 | 0.07 | deg | 2 | This fit yields a disk inclination of 32.42$^{\circ}$ $\pm$ 0.07 and a P.A. of 74.33$^{\circ}$$\pm$ 0.14. |
| Position angle | 74.33 | 0.14 | deg | 2 | a P.A. of 74.33$^{\circ}$$\pm$ 0.14 |
| 870 um flux density (uvmodelfit) | 876.30 | 0.51 (formal) | mJy | 2 | we find an 870 $\ensuremath{\mu}m$ continuum flux density of 876.30 $\pm$ 0.51 mJy |
| Ring peak radius (870 um) | 32.30 | 0.14 | au | 3 | the 870 $\ensuremath{\mu}m$ continuum emission peaks at 32.30 $\pm$ 0.14 au, with a FWHM of 37.30 $\pm$ 2.74 au |
| Ring FWHM (870 um, R=-0.5) | 37.30 | 2.74 | au | 3 | with a FWHM of 37.30 $\pm$ 2.74 au and outer radius of $\sim$ 90 au |
| Dust mass (lower limit) | ~60 | not stated | Earth masses | 4 | we thereby obtain a dust mass of $M_{dust}
\sim 60$ $\rm M_{\oplus }$ for the dust ring imaged by ALMA |
| SPHERE ring 1 and ring 2 radii | 14.10 and 24.62 | 0.01 and 0.08 | au | 3 | ring 1 (inner ring) and 2 (gap outer edge) are located at 14.10 $\pm$ 0.01 and 24.62 $\pm$ 0.08 au |
| Inner-region flux (R=-2 image) | 83.0 | 8.0 | mJy | 3 | of 83.0 $\pm$ 8.0 mJy (assuming a 10% flux calibration accuracy) |
| Ring FWHM (R=-2) | 28.20 | 0.04 | au | 3 | the resulting FWHM of the dominant Gaussian, 28.20 $\pm$ 0.04 au |
| Putative planet mass range | 0.3-1.5 | not stated | MJup | 5 | the mass of the putative circumbinary planet orbiting V4046 Sgr at $\sim$20 au should lie within the range 0.3–1.5 M$_{\rm Jup}$ |

## Qualitative findings

- Dust ring, gas disk and binary orbit are coplanar; a tentative inner mm ring coincides with the 14 au scattered-light ring  
  > "demonstrating that the large-grain dust ring, larger-scale circumbinary gas disk, and central binary system are all in close alignment." (Summary)

## Claim tuples

- H: Is the dust ring inclined consistent with the gas disk and binary? | E: uvmodelfit elliptical Gaussian fit to visibilities | R: inclination 32.42±0.07 deg | F: dust disk, gas disk and binary are coplanar | **supported**
- H: Does a single planet at 20 au explain the gap and ring structures? | E: Compared SPHERE and ALMA radial profiles with 0.3 and 1.5 MJup synthetic images | R: 0.3 MJup fits the gap but underestimates the ALMA ring radius; 1.5 MJup fits ring radius but gives too wide and deep a gap | F: planet mass likely 0.3-1.5 MJup | **partially**
- H: Is there an inner mm ring? | E: R=-2 image radial profile | R: shoulder at 10-17 au matching the NIR inner ring | F: inner ring tentatively detected | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Simultaneous comparison of mm and NIR constrains planet mass since gap width and depth depend on planet mass  
  > "Since the width and depth of a gap that can be opened by a planet depend most sensitively on planet mass" (Constraints on Putative Planet Mass)
- How they decided it was enough: _not stated_
- Limitation (authors): Models are generic, not fine tuned; viscosity, scale height and gas surface density not varied; inner cavity not modeled  
  > "we have not explored the effects of varying these parameters in our modeling." (Discussion)
- Caveat (inferred, ours): Planet mass bracket rests on only two models and visual comparison without a goodness of fit
- Caveat (inferred, ours): Dust mass assumes optically thin emission and T=15 K, yet the emission is argued to be optically thick
- Caveat (inferred, ours): Inner ring detection is marginal at about beam resolution
- Caveat (inferred, ours): Short 11.7 min observation; only a 0.3 arcsec beam
- Caveat (inferred, ours): Summary flux 880±40 mJy differs from the 876.30 mJy uvmodelfit value

## Reproducibility

- Data public (paper): ALMA program 2016.1.00315.S and archival SPHERE data cited; public status not explicitly stated  
  > "The archival H-band polarimetric images of V4046 Sgr presented in this work were obtained on March 13, 2016" (SPHERE Observations)
- Products in archive: _not stated_
- Missing: Dong2015 model parameters and output images
- Missing: clean parameters and masks
- Missing: self-calibration details
- Data volume (inferred): ~5-20 GB for the ALMA MS; SPHERE data small
- Score (inferred): 3/5, The ALMA imaging and fits are fairly clear, but the hydrodynamic models are from earlier work and the planet-mass comparison is qualitative.
- Rediscovery candidate: no, The planet-mass constraint relies on external model libraries and qualitative comparison, though the ALMA measurements can be redone.

## Links

- Method: Dong, Zhu & Whitney 2015 (cite: Dong2015) (hydro+MCRT model library)
- Method: Avenhaus et al. 2018 (cite: Avenhaus2018) (SPHERE data and reduction)
- Method: Marti-Vidal et al. 2014 (cite: Marti2014) (uvmodelfit)
- Companion: Kastner et al. 2018 (cite: Kastner2018) (ALMA molecular line imaging of V4046 Sgr)
- Companion: Rosenfeld et al. 2013 (cite: Rosenfeld2013) (SMA continuum with 30 au hole)

## Checks

```json
{
 "quotes": 72,
 "quotes_ok": 72,
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
  "facts": 77,
  "stated": 54,
  "rate": 0.701
 },
 "evidence_ok": true
}
```
