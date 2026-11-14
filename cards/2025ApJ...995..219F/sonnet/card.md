# PASSAGES: The Discovery of a Strongly Lensed Protocluster Core Candidate at Cosmic Noon

`2025ApJ...995..219F` | The Astrophysical Journal 2025 | first author: Foo, Nicholas | arXiv: 2504.05617 | DOI: 10.3847/1538-4357/adf4d5

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, star_formation
- Question: Is the Planck-selected lensed source PJ0846+15 a single DSFG or a strongly lensed protocluster core at z~2.67, and what are its lens model, SFR, gas/dust masses, dynamical mass and kinematics?  
  > "Here we present the discovery that J0846 does not consist of just one source, but instead at least $11$ CO(3–2) emitting galaxies all at $z = 2.67$ uncovered by Atacama Large Millimeter Array (ALMA) observations." (Introduction)
- Target **PJ0846+15 (J0846.BG at z=2.67, lensed by J0846.FG at z=0.77)**: coordinates RA=131.70877, Dec=15.09936 (deg, J2000 center)  
  > "One of these PASSAGES sources, PJ0846+15 (J0846), is found to be lensed by a foreground galaxy cluster determined to be at $z=0.77$." (Introduction); "Center position: RA=131.70877, DEC=15.09936" (5.1 Star Formation Activity); z/distance z=2.6655±0.0008 (background); z=0.766±0.002 (foreground cluster)  
  > "One of these PASSAGES sources, PJ0846+15 (J0846), is found to be lensed by a foreground galaxy cluster determined to be at $z=0.77$." (Introduction); "Center position: RA=131.70877, DEC=15.09936" (5.1 Star Formation Activity); distance from ALMA CO(3-2) redshifts; optical spectroscopy (MUSE, FORS2, GMOS) for cluster  
  > "One of these PASSAGES sources, PJ0846+15 (J0846), is found to be lensed by a foreground galaxy cluster determined to be at $z=0.77$." (Introduction); "Center position: RA=131.70877, DEC=15.09936" (5.1 Star Formation Activity)

## Data provenance

- ALMA projects: 2017.1.01214.S
- bands: Band 3, Cycle 5  
  > "ALMA observations were acquired in a Band 3 Cycle 5 program (2017.1.01214.S, PI: Min Yun)." (2.1 ALMA)
- frequencies and spectral setup: 91.53-107.151 GHz; 31.25 MHz continuum resolution; one sub-band at 3.9043 MHz (12.279 km/s) for CO(3-2); two overlapping pointings  
  > "The total frequency bandwidth spans $91.53-107.151$ GHz with a resolution of 31.25 MHz for the continuum, while one sub-band was set up to resolve the CO(3–2) line emission with a resolution of 3.9043 MHz" (2.1 ALMA)
- continuum bandwidth: _not stated_
- arrays: 12 m array  
  > "These observations were taken using the 12 m antennae array in configuration 3 with baselines ranging from $15-2517$ m" (2.1 ALMA)
- configurations: _not stated_
- baselines: 15-2517 m  
  > "These observations were taken using the 12 m antennae array in configuration 3 with baselines ranging from $15-2517$ m" (2.1 ALMA)
- angular resolution: 0.56" x 0.46", PA -63.18 deg  
  > "This resulted in a synthesized beam size of $0.56^{\prime\prime}\times0.46^{\prime\prime}$, a position angle of $-63.18 ^\circ$." (2.1 ALMA)
- max recoverable scale: _not stated_
- sensitivity: line rms ~0.1 mJy/beam per 50 km/s channel; continuum rms ~6 uJy/beam  
  > "The final root mean square (rms) achieved for the continuum-subtracted line map was $\sim0.1$ mJy beam$^{-1}$ per 50 km s$^{-1}$ channel." (2.1 ALMA); "The final rms achieved for the continuum imaging was $\sim6$ $\mu$Jy beam$^{-1}$." (2.1 ALMA)
- time on source: average 4596.480 s  
  > "an average on-source integration time of 4596.480 seconds" (2.1 ALMA)
- observing dates: _not stated_
- pi or archival as stated: PI: Min Yun  
  > "ALMA observations were acquired in a Band 3 Cycle 5 program (2017.1.01214.S, PI: Min Yun)." (2.1 ALMA)
- Line: CO J=3-2 (not stated)
- Other facility **VLA 6 GHz**: Radio continuum; counterparts and cluster WAT  
  > "We use the VLA data to provide an initial morphological characterization of J0846.FG and determine radio counterparts to the J0846.BG members." (2.2 VLA 6 GHz Continuum)
- Other facility **HST WFC3-IR F160W**: Lens imaging, cluster member luminosities, counterparts  
  > "A single orbit was taken with the F160W wide-band filter, composed of a five-point dithering pattern, of 500 s each" (2.3 HST Observations)
- Other facility **Gemini/GMOS**: r' and z' imaging and spectroscopy  
  > "Gemini/GMOS r$^{\prime}$ and z$^{\prime}$ imaging and slit spectroscopy was acquired as part of the Gemini South programs" (2.4 Gemini Observations)
- Other facility **VLT MUSE and FORS2**: Redshifts of foreground cluster members  
  > "we were unable to make detections of any lensed background sources, only managing to secure redshifts of foreground objects." (2.5 VLT Observations)
- External data: Dust SED unresolved photometry (Planck/Herschel etc.) used in modified blackbody fit  
  > "we opt to fit a modified blackbody to the observed dust SED using the sum of all unresolved dust continuum data points (cite: Harrington2021; Berman2022)." (5.1 Star Formation Activity) [from (cite: Harrington2021; Berman2022)]
- External data: Fiducial Tdust = 44.7 K (20% error) and alpha_CO(3-2) ~1  
  > "we adopt a fiducial value for the dust temperature of $T_{\text{dust}}= 44.7$ K (with a 20% error) from (cite: Harrington2021)" (5.2 Estimates of molecular gas and dust masses) [from (cite: Harrington2021)]
- External data: Kappa_850um = 0.077 kg^-1 m^2 for SED fit  
  > "We adopt a value of $\kappa_0 = \kappa_{850\mu\text{m}} = 0.077\, \text{kg}^{-1}\text{m}^2$ where $\nu_0 = 352.7\, \text{GHz}$" (10 Global Modified Blackbody Fitting) [from (cite: Dunne_2000)]

## Processing

### Calibration

- pipeline or manual: CASA with ALMA pipeline heuristics  
  > "We reduced the dataset with the Common Astronomy Software Application (cite: McMullin2007; CASA_2022) version 6.5.4.9 with the ALMA pipeline heuristics (cite: Hunter_2023)" (2.1 ALMA)
- casa version: 6.5.4.9  
  > "version 6.5.4.9 with the ALMA pipeline heuristics" (2.1 ALMA)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "using the `tclean` routine to produce both spectral line data cubes and continuum images." (2.1 ALMA)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 1.0  
  > "cleaned using Briggs weighting with a robust parameter of 1.0." (2.1 ALMA)
- uv taper: _not stated_
- cell size: 0.09"  
  > "generated with a pixel size of $0.09^{\prime\prime}$" (2.1 ALMA)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub in CASA, line-free channels  
  > "We utilized the `uvcontsub` routine in CASA to subtract the observed 3mm continuum, ensuring that only line-free channels were included for relevant analyses." (2.1 ALMA)
- line free channels: _not stated_
- primary beam correction: Detection search before PB correction; fluxes measured on PB-corrected cubes  
  > "we searched for individual detections in the generated ALMA image-cubes prior to primary-beam corrections." (3 The CO Detections)
- array combination: _not stated_
- smoothing: 15.625 MHz (~50 km/s) channels; also 25 km/s cubes  
  > "we opt for a channel width of 15.625MHz ($\sim$50 km s$^{-1}$), a factor of four greater than the native resolution" (2.1 ALMA)
- final beam: 0.56"x0.46"  
  > "This resulted in a synthesized beam size of $0.56^{\prime\prime}\times0.46^{\prime\prime}$" (2.1 ALMA)
- final rms: ~0.1 mJy/beam per 50 km/s (line); ~6 uJy/beam (continuum)  
  > "The final rms achieved for the continuum imaging was $\sim6$ $\mu$Jy beam$^{-1}$." (2.1 ALMA)

### Inherited from earlier work

- VLA 6 GHz observations and full reduction  
  > "The observational details are presented in (cite: Kamieneski_2024_PASSAGES) along with the full data reduction procedure." (2.2 VLA 6 GHz Continuum) [from (cite: Kamieneski_2024_PASSAGES)]
- CO luminosity calculation procedure  
  > "Following the procedure described in, e.g., (cite: Solomon2005), we calculate the CO(3–2) line luminosities." (3 The CO Detections) [from (cite: Solomon2005)]
- Dust assumptions (beta=1.8, opacity)  
  > "Here we adopt the same assumptions as (cite: Harrington2021) following (cite: Draine_Lee_1984), and fix the dust emissivity index, $\beta=1.8$." (5.2 Estimates of molecular gas and dust masses) [from (cite: Harrington2021); (cite: Draine_Lee_1984)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges and continuum-subtraction fit order
- Clean threshold, niter, masking and deconvolver for tclean
- Self-calibration and flux calibrator details; ALMA flux scale uncertainty
- Exact line-extraction aperture masks and multi-Gaussian fit initial conditions
- Lens model GLAFIC constraints, priors, parameter ranges, and MCMC settings (walkers, steps)
- Mass absorption coefficient used for 3mm dust masses and how magnification de-lensing is applied per image
- Photometry points used in the global SED fit
- Rest frequency adopted for CO(3-2)

## Analysis recipe

1. **Image CO(3-2) cube and 3 mm continuum**: tclean on pipeline-calibrated data, Briggs weighting, continuum subtraction with uvcontsub  
  > "using the `tclean` routine to produce both spectral line data cubes and continuum images." (2.1 ALMA)
   - software: CASA, tclean, uvcontsub
   - parameter: robust 1.0; pixel 0.09"; 50 km/s channels  
  > "cleaned using Briggs weighting with a robust parameter of 1.0." (2.1 ALMA)
   - fitting: _not stated_
   - validation: Individual execution blocks imaged independently to verify line fidelity  
  > "Individual execution blocks (EB) were imaged and inspected independently to verify the fidelity of line features." (3 The CO Detections)
2. **Blind search for CO(3-2) detections**: FindClumps blind search after by-eye inspection  
  > "utilizing the `FindClumps` algorithm (cite: Walter_2016) built into the `Interferopy` python package (cite: interferopy)." (3 The CO Detections)
   - software: Interferopy
   - parameter: S/N>2.5 per channel across >=3 continuous channels  
  > "we impose a criterion of S/N$>2.5$ per channel, across $\geq3$ continuous channels." (3 The CO Detections)
   - fitting: _not stated_
   - validation: Counterparts sought in F160W, r', z'  
  > "We search for any counterparts in F160W, r$^{\prime}$ and z$^{\prime}$ to further corroborate secure detections." (3 The CO Detections)
3. **Extract spectra and line fluxes/luminosities**: Manual apertures at >3 sigma in moment-0; multi-Gaussian line fits integrated for flux; L'CO following Solomon & Vanden Bout  
  > "We model the spectral line profile utilizing multi-Gaussian functions and integrate them to obtain their line fluxes, measuring from the primary beam corrected image cubes" (3 The CO Detections)
   - fitting: multi-Gaussian line profile  
  > "We model the spectral line profile utilizing multi-Gaussian functions and integrate them to obtain their line fluxes, measuring from the primary beam corrected image cubes" (The CO Detections at $z=2.67$)
   - validation: _not stated_
4. **Build strong lens model of foreground cluster**: Parametric GLAFIC model with pseudo-Jaffe cluster members, NFW halo, second NFW for z=0.357 perturber; constrained by image positions, penalty for singly-imaged sources  
  > "To construct the lens model we used `GLAFIC` (cite: Oguri2010; Oguri2021), employing a parametric approach" (4 The Lens Model)
   - software: GLAFIC, emcee, GALFIT
   - parameter: rms image-position separation 0.14"  
  > "The best fit model reproduces the angular positions of identified multiply imaged systems to an rms separation of $0.14^{\prime\prime}$." (4.4 The J0846 Model Results)
   - fitting: emcee MCMC; likelihood from reproduced image positions plus penalty for extra images  
  > "We construct the likelihood function based on the ability of the model to reproduce the positions of the observed multiply imaged systems." (4.4 The J0846 Model Results)
   - validation: 1000 posterior resamples for magnification uncertainty; systematics acknowledged not included  
  > "we randomly resampled 1000 model iteration from the MCMC posterior distribution." (4.4 The J0846 Model Results)
5. **Global SFR via modified blackbody SED**: MBB fit to unresolved dust photometry, integrate 8-1000 um, SFR=LIR/9.4e9  
  > "We determine the total apparent IR luminosity by integrating the SED fit from $8-1000\mu$m" (5.1 Star Formation Activity)
   - software: emcee
   - assumption: kappa_850 = 0.077 kg^-1 m^2; free A, Td, Md, beta  
  > "setting $A$, $T_d$, $M_d$, and $\beta$ as free parameters." (10 Global Modified Blackbody Fitting)
   - fitting: emcee MCMC  
  > "We use a MCMC approach with the `emcee` (cite: Foreman-Mackey_2013) Python package to sample the posterior distribution, setting $A$, $T_d$, $M_d$, and $\beta$ as free parameters." (Global Modified Blackbody Fitting to the Dust SED)
   - validation: _not stated_
6. **Intrinsic gas and dust masses**: Gas mass from de-magnified L'CO with alpha_CO~1; dust mass from 3 mm flux with optically thin MBB (Hildebrand)  
  > "We then directly translate the measured, de-magnified $\text{L}_{\text{CO(3-2)}}^{\prime}$ to a total molecular ISM gas mass estimate" (5.2 Estimates of molecular gas and dust masses)
   - assumption: alpha_CO(3-2)~1 Msun/(K km/s pc^2); Tdust=44.7 K (20%); beta=1.8; optically thin; helium factor 1.36  
  > "we assume all systems are in the optically thin regime" (5.2 Estimates of molecular gas and dust masses)
   - fitting: _not stated_
   - validation: _not stated_
7. **Velocity dispersion and dynamical mass**: Biweight mean and sigma of 11 members; virial M=3R sigma^2/G with R=280 kpc  
  > "we employ the virial theorem assuming a spherical mass distribution" (5.3 Dynamical Mass Estimate)
   - assumption: spherical, virialized  
  > "we employ the virial theorem assuming a spherical mass distribution" (Dynamical Mass Estimate)
   - fitting: _not stated_
   - validation: _not stated_
8. **Classify kinematics**: Inspect moment-1 maps for smooth monotonic gradients (disks) vs disturbed (mergers)  
  > "we search for smooth, monotonic velocity gradients, indicative of ordered rotation within gas disks" (5.4 A Diverse Population of Galaxies)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 6.5.4.9: Calibration, tclean imaging, uvcontsub  
  > "version 6.5.4.9 with the ALMA pipeline heuristics" (2.1 ALMA)
- **Interferopy (FindClumps)** : Blind CO line search  
  > "utilizing the `FindClumps` algorithm (cite: Walter_2016) built into the `Interferopy` python package" (3 The CO Detections)
- **GLAFIC** : Parametric lens model  
  > "To construct the lens model we used `GLAFIC` (cite: Oguri2010; Oguri2021)" (4 The Lens Model)
- **emcee** : MCMC for lens model and SED fit  
  > "We use the Python package `emcee` (cite: Foreman-Mackey_2013)" (4.4 The J0846 Model Results)
- **GALFIT** : Subtract foreground galaxy near Einstein cross  
  > "utilizing the `GALFIT` (cite: Peng_2002) software" (4.1 The Image Systems)
- **BLOBCAT** : 6 GHz photometry  
  > "Photometry for the 6 GHz imaging is performed using source extraction software BLOBCAT (cite: Hales_2012)" (8.1 VLA: 6 GHz Continuum Imaging)
- **SExtractor** : Optical/IR photometry  
  > "Photometry was obtained from the F160W, r$^{\prime}$ and z$^{\prime}$ band imaging utilizing `SExtractor`, applying nominal settings." (8.2 Optical-Infrared Imaging)
- **ESO pipelines/EsoReflex, ZAP** 2.8.5: FORS2 and MUSE reduction; sky residual removal  
  > "We used the Zurich Atmosphere Purge (ZAP) tool software (cite: Soto2016)" (2.5.2 MUSE)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of CO(3-2) detections | 18 (11 sources) | not stated | dimensionless | 2 | In total we report 18 CO(3–2) detections |
| Apparent SFR (muSFR) | 39900 | +23000/-12900 | Msun/yr | 5 | $\mu\mathrm{SFR}=39900^{+23000}_{-12900}~\mathrm{M}_{\odot}~\mathrm{yr}^{-1}$ |
| Intrinsic SFR | 5200 | +3200/-2000 | Msun/yr | 5 | SFR $= 5200^{+3200}_{-2000}~\textup{ M}_{\odot}$ yr$^{-1}$ |
| Dust temperature (global SED) | 47.1 | +8.8/-6.4 | K | 5 | a dust temperature of $T_d=47.1^{+8.8}_{-6.4}$ K |
| Apparent IR luminosity | 3.75e14 | +2.16/-1.21 e14 | Lsun | 5 | $\mu\mathrm{L}_{\mathrm{IR}} = 3.75^{+2.16}_{-1.21} \times 10^{14}~\textup{L}_{\odot}$ |
| Global magnification (CO-weighted) | 7.7 | 1.5 | dimensionless | 4 | of $\mu=7.7\pm1.5$ |
| Total molecular gas mass | 2.0e11 | 0.3e11 | Msun | 6 | M$_{ISM}= (2.0\pm0.3)\times10^{11}\textup{ M}_\odot$ |
| Velocity dispersion | 246 | 72 | km/s | 7 | yielding $\sigma_{v}=246\pm72$ km s$^{-1}$ |
| Dynamical mass | 1.2e13 | 0.6e13 | Msun | 7 | M$_{dyn}=1.2\pm0.6\times10^{13} \textup{ M}_\odot$ |
| Mean redshift of members | 2.6655 | 0.0008 | dimensionless | 7 | calculating a value of $z=2.6655\pm0.0008$ |
| Foreground cluster redshift | 0.766 | 0.002 | dimensionless | 0 | or $z=0.766\pm0.002$ utilizing the biweight estimator |
| Lens model image-position rms | 0.14 | not stated | arcsec | 4 | rms separation of $0.14^{\prime\prime}$ |

## Qualitative findings

- 6/11 members show disk-like kinematics, 2/11 merger signatures, 3 undetermined  
  > "we are still find that 6/11 members exhibit kinematic features consistent with ordered-disk rotation (while only two may be mergers and three remain undetermined)" (6.2 How may this DSFG-rich Core Candidate evolve?)

## Claim tuples

- H: J0846 is a single lensed DSFG rather than a multi-galaxy system | E: ALMA Band 3 CO(3-2) cube search plus lens model | R: 18 CO detections from 11 sources at z=2.660-2.669 within 280x150 kpc | F: J0846.BG is a strongly lensed protocluster core candidate | **supported**
- H: J0846.BG is among the most star-forming protocluster cores | E: MBB SED fit and CO-based demagnification | R: Intrinsic SFR 5200 Msun/yr | F: Among most starbursting protocluster core candidates | **supported**
- H: Members have diverse kinematics | E: Moment-1 map inspection | R: 6 disks, 2 mergers, 3 undetermined | F: Diverse population | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Single-galaxy SED template deemed inappropriate for multiple sources, so MBB to summed photometry  
  > "therefore a single galaxy template fit is likely inappropriate and is considered a lower limit." (5.1 Star Formation Activity)
- Alternative: Serendipitous line at 92.737 GHz excluded as unlikely protocluster member  
  > "For this work, we have not included this detection in our analyses as it unlikely to be a protocluster member." (3 The CO Detections)
- How they decided it was enough: _not stated_
- Limitation (authors): Lens model systematics not included; mass-sheet degeneracy possibly unbroken  
  > "We acknowledge that this does not account for the systematics that arise from cluster lens modeling, that likely dominate the overall uncertainties." (4.4 The J0846 Model Results)
- Limitation (authors): Gas mass is a lower limit given alpha_CO  
  > "thereby sets a lower limit for the molecular gas masses" (5.2 Estimates of molecular gas and dust masses)
- Caveat (inferred, ours): Virial mass assumes all 11 galaxies bound and virialized; membership as protocluster not demonstrated
- Caveat (inferred, ours): Global SFR from unresolved Planck-scale photometry with single MBB
- Caveat (inferred, ours): Magnification-weighted values depend on a lens model with few spectroscopic constraints at one redshift
- Caveat (inferred, ours): Kinematic classification is qualitative by-eye in lensed image plane

## Reproducibility

- Data public (paper): ALMA data cited by project code; acknowledgments use ADS/JAO data  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA 2017.1.01214.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Lens model files and GLAFIC input
- Missing: Aperture definitions and Gaussian fit parameters
- Missing: Photometry table used for global SED
- Data volume (inferred): ~50-100 GB raw for Band 3 12 m project
- Score (inferred): 3/5, Imaging settings largely stated and data public, but lens model, aperture and fitting details are incomplete.
- Rediscovery candidate: no, Cube search is repeatable, but key results rely on a bespoke lens model and external photometry not fully specified.

## Links

- Method: (cite: Kamieneski_2024_PASSAGES) (VLA/HST/Gemini data and reduction details)
- Method: (cite: Oguri2010) (GLAFIC lens modeling)
- Companion: (cite: Berman2022) (LMT/RSR detections and Planck-WISE selection)
- Companion: (cite: Harrington2021) (PASSAGES gas excitation, alpha_CO, Tdust)
- Related: PASSAGES
- Related: Planck All-Sky Survey

## Checks

```json
{
 "quotes": 88,
 "quotes_ok": 88,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2021.2.00088.S",
  "2022.1.01282.S",
  "2022.1.01311.S",
  "2023.1.00299.S"
 ],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 95,
  "stated": 66,
  "rate": 0.695
 },
 "evidence_ok": true
}
```
