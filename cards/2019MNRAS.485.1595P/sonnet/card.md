# Multiphase circumgalactic medium probed with MUSE and ALMA

`2019MNRAS.485.1595P` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Péroux, Céline | arXiv: 1901.05217 | DOI: 10.1093/mnras/stz202

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, milky_way_ism
- Question: What galaxies (stellar and molecular gas) are associated with the strong HI absorber at z=0.313 toward Q1130-1449, and is the absorption linked to a single galaxy or a group/CGM structure?  
  > "Together, these findings challenge a picture where strong-$\sc N(\rm H~{\sc I})$ quasar absorbers are associated with a single bright galaxy" (abstract)
- Target **Q1130-1449 field (DLA at z_abs=0.313)**: coordinates J2000 113007.05–144927.38  
  > "The $z_{\rm QSO}=$1.189 (V=16.9 mag) quasar (J2000 coordinates: 113007.05–144927.38; alternative name: PKS B1127–145)" (2.1 Quasar Spectroscopy: Absorption Properties); "At the redshift of the absorber, 1 arcsec corresponds to 4.6  kpc." (1 Introduction); z/distance z_abs=0.313 (QSO z=1.189)  
  > "The $z_{\rm QSO}=$1.189 (V=16.9 mag) quasar (J2000 coordinates: 113007.05–144927.38; alternative name: PKS B1127–145)" (2.1 Quasar Spectroscopy: Absorption Properties); "At the redshift of the absorber, 1 arcsec corresponds to 4.6  kpc." (1 Introduction); distance from absorber redshift; cosmology H0=70, Om=0.3, OL=0.7  
  > "The $z_{\rm QSO}=$1.189 (V=16.9 mag) quasar (J2000 coordinates: 113007.05–144927.38; alternative name: PKS B1127–145)" (2.1 Quasar Spectroscopy: Absorption Properties); "At the redshift of the absorber, 1 arcsec corresponds to 4.6  kpc." (1 Introduction)

## Data provenance

- ALMA projects: 2016.1.01250.S
- bands: Band 3 (CO(1-0) at 87.8 GHz)  
  > "The field of Q1130$-$1449 was observed with ALMA in Band 3 to cover the CO(1-0) emission lines" (2.2 New ALMA Observations)
- frequencies and spectral setup: One high-resolution spw at 87.8 GHz (3840 channels of 0.488 MHz); three low-resolution continuum spws  
  > "The other three spectral windows were set to low spectral resolution mode and were used for continuum observations of the field." (2.2 New ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C40-3, angular resolution 1.2x1.8 arcsec  
  > "A compact antenna configuration (C40-3) resulted in an angular resolution 1.2$\times$1.8$"$." (2.2 New ALMA Observations)
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 3.6 hr  
  > "the total on-source observing time was $T_{\rm exp}=3.6$ hrs" (2.2 New ALMA Observations)
- observing dates: 4, 8, 15 Dec 2016  
  > "on 4, 8, and 15 Dec 2016" (2.2 New ALMA Observations)
- pi or archival as stated: Own program, PI C. Peroux  
  > "(under programme 2016.1.01250.S, PI: C. Peroux)" (2.2 New ALMA Observations)
- Line: CO J=1-0 (87.8 GHz observed (z=0.313))
- Other facility **VLT/MUSE**: 5-hr IFU spectroscopy: galaxy redshifts, fluxes, SFR, metallicities, kinematics  
  > "We report new MUSE medium-deep (5-hours on source) observations of this field." (2.2 New MUSE Observations)
- Other facility **HST/WFPC2**: F814W image used as prior for spectral extraction  
  > "We retrieved HST/WFPC2 F814W image of the field from the HST archive" (2.2 New MUSE Observations)
- Other facility **VLT/UVES**: Archival quasar spectrum for metal absorption  
  > "We obtained the VLT/UVES reduced quasar spectra from the ESO advanced data products archives" (5 Gas Absorption Profiles)
- External data: HI column density log N(HI)=21.71±0.07 from HST/FOS  
  > "log $[N(H I)/cm^{-2}]$=21.71$\pm$0.07 (cite: lane98)" (2.1 Quasar Spectroscopy: Absorption Properties) [from (cite: lane98)]
- External data: Zinc metallicity [Zn/H]=-0.80±0.16 from HST/STIS  
  > "(cite: kanekar14) computed the zinc metallicity to be \[Zn/H\]$=-0.80\pm0.16$ relative to solar" (2.1 Quasar Spectroscopy: Absorption Properties) [from (cite: kanekar14)]
- External data: Mean CO/H2 column density ratio of 3e-6  
  > "Using the mean CO/H$_2$ column density ratio of 3$\times$10$^{-6}$ from (cite: burgh07)" (2.2 New ALMA Observations) [from (cite: burgh07)]
- Simulation/model as data: Dedicated RAMSES AMR zoom-in cosmological simulation of a z=0.3 halo (SFR=1 Msun/yr, Mstar=1e11, MDM=1e12) post-processed for Halpha surface brightness  
  > "we picked a typical z=0.3 halo in the zoom-in simulations which best mimics the properties of H i absorbers" (3.1.2 Cosmological zoom-in Simulations)

## Processing

### Calibration

- pipeline or manual: Started from ALMA pipeline-calibrated data; minor manual flags; two self-calibration cycles  
  > "We started the data reduction with the pipeline-calibrated uv-data sets, as delivered by ALMA." (2.2 New ALMA Observations); "Minor manual flags were added to remove some uv-data points with strongly outlying amplitudes." (2.2 New ALMA Observations)
- casa version: CASA 4.7.0  
  > "Common Astronomy Software Applications (CASA) software package version 4.7.0" (2.2 New ALMA Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1058+0133 amplitude calibrator; J1139-1350 phase calibrator  
  > "The quasars J1058$+$0133 and J1139$-$1350 were used as amplitude and phase calibrators, respectively." (2.2 New ALMA Observations)
- flux scale uncertainty: _not stated_
- self calibration: One round phase, one round amplitude+phase, using gaincal and applycal  
  > "We applied one round of phase self-calibration and one round of amplitude and phase self-calibration." (2.2 New ALMA Observations)

### Imaging

- task: tclean; uvsub; uvcontsub; pbcor  
  > "The next step was to subtract the bright continuum source from the field using the task *uvsub*." (2.2 New ALMA Observations)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5  
  > "using a ’robust’ weighting scheme with a Briggs parameter of 0.5" (2.2 New ALMA Observations)
- uv taper: _not stated_
- cell size: 0.2 arcsec  
  > "setting the pixel size to 0.2"" (2.2 New ALMA Observations)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvsub of bright quasar, then uvcontsub for residuals  
  > "We removed remaining continuum signatures around the imperfectly subtracted quasar with the *uvcontsub* task." (2.2 New ALMA Observations)
- line free channels: _not stated_
- primary beam correction: pbcor task  
  > "Lastly, we produced a cube corrected for the primary beam using the *pbcor* task." (2.2 New ALMA Observations)
- array combination: _not stated_
- smoothing: Spectral binning of seven channels to 53 km/s  
  > "We applied a spectral binning of seven channels to achieve a velocity resolution of 53 km s$^{-1}$." (2.2 New ALMA Observations)
- final beam: 1.4" x 1.3"  
  > "the angular resolution is $1.4"\times 1.3"$, corresponding to 6 kpc" (2.2 New ALMA Observations)
- final rms: 0.11 mJy/beam per 53 km/s channel  
  > "The final rms noise level of the cube is 0.11 mJy/beam per 53 km s$^{-1}$ channel" (2.2 New ALMA Observations)

### Inherited from earlier work

- Morpho-kinematic analysis method with GalPak3D  
  > "using the method described in (cite: peroux17)" (3.3 Morphological and Kinematical Properties) [from (cite: peroux17)]
- Metallicity measurement from strong-line indices  
  > "Following the methodology of (cite: peroux17), the HII region metallicities were measured" (3.2 Physical Properties of the Galaxy Group) [from (cite: peroux17)]
- Simulation details  
  > "Details of the simulation are presented in an upcoming paper (Augustin et al. submitted)." (3.1.2 Cosmological zoom-in Simulations) [from Augustin et al. submitted]

### Not stated but needed to reproduce (our reading)

- Self-calibration solution intervals and imaging parameters for the continuum model
- Line-free channels for uvcontsub and the fit order
- Cleaning threshold, masks and niter in tclean
- Duchamp parameters other than the 5-sigma threshold
- GalPak3D priors, model choice and initial conditions
- Simulation parameters and post-processing details (in a separate paper)
- ALMA flux scale uncertainty

## Analysis recipe

1. **Reduce and image ALMA CO(1-0) cube**: Self-calibrate on bright quasar, subtract it with uvsub, tclean cube, uvcontsub, pbcor  
  > "We then built a cube with the *tclean* task, setting the pixel size to 0.2"" (2.2 New ALMA Observations)
   - software: CASA
   - parameter: robust 0.5, 53 km/s channels, 0.2" pixels  
  > "using a ’robust’ weighting scheme with a Briggs parameter of 0.5" (2.2 New ALMA Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Detect CO emitters in cube**: Duchamp 3D wavelet source finder at 5 sigma on cube before pb correction, plus visual inspection  
  > "running the *Duchamp* source finder (version v1.6.2) which performs a three-dimensional search via wavelet reconstruction with a detection threshold of 5-$\sigma$" (3.1.1 Galaxies at z_abs=0.313)
   - software: Duchamp
   - fitting: _not stated_
   - validation: Visual inspection of cube; MUSE counterparts  
  > "In addition, we performed a visual inspection of the cube at the redshifted frequency of the CO(1–0) line." (3.1.1 Galaxies at z_abs=0.313)
3. **Derive CO luminosity, molecular mass and depletion time**: Integrate CO spectra; L_CO from Solomon formula; Mmol as function of alpha_CO; tau_depl = M_H2/SFR with alpha_CO=4.6  
  > "We calculated the molecular depletion times for the three objects detected with ALMA following: $\tau_{\rm depl}$=M$_{H2}$/SFR=1/SFE" (3.2 Physical Properties of the Galaxy Group)
   - software: CASA
   - assumption: Galactic alpha_CO=4.6 Msun (K km/s pc^2)^-1 for depletion times  
  > "we assumed a Galactic CO-H$_2$ conversion factor of $\alpha_{\rm CO}$=4.6 M$_{\odot}$ (K km/s pc$^2$)$^{-1}$" (3.2 Physical Properties of the Galaxy Group)
   - fitting: _not stated_
   - validation: _not stated_
4. **MUSE line fluxes, SFR and metallicity**: Gaussian fits to nebular lines, Balmer-decrement dust correction, Kennicutt98 SFR, strong-line metallicities  
  > "We measured the emission fluxes from a Gaussian fit to the nebular lines." (3.2 Physical Properties of the Galaxy Group)
   - software: MPDAF, Sextractor
   - fitting: Gaussian line fits  
  > "We measured the emission fluxes from a Gaussian fit to the nebular lines." (Physical Properties of the Galaxy Group)
   - validation: Agrees with earlier G2 and G6 metallicities  
  > "Our estimates agreed within the errors with earlier measurements of G2 and G6 metallicities by (cite: kacprzak10b)." (3.2 Physical Properties of the Galaxy Group)
5. **3D morpho-kinematics and dynamical masses**: GalPak3D MCMC fit of [OIII]/Halpha and CO cubes; Mdyn=Vmax^2 r1/2/G; halo mass from spherical collapse  
  > "we used the GalPak$^{\rm 3D}$ algorithm (cite: bouche15) which compares directly the data cube with a parametric model" (3.3 Morphological and Kinematical Properties)
   - software: GalPak3D, Sextractor
   - fitting: MCMC  
  > "The algorithm uses a Markov Chain Monte Carlo (MCMC) approach with a proposed distribution of the parameters" (3.3 Morphological and Kinematical Properties)
   - validation: chi2 minimisation and residual map inspection  
  > "We assessed the quality of the fit from a $\chi^2$ minimisation as well as the inspection of the residual maps." (3.3 Morphological and Kinematical Properties)

## Software

- **CASA** 4.7.0: ALMA reduction, self-cal, imaging, spectra extraction  
  > "Common Astronomy Software Applications (CASA) software package version 4.7.0" (2.2 New ALMA Observations)
- **Duchamp** v1.6.2: 3D source finding in the ALMA cube  
  > "running the *Duchamp* source finder (version v1.6.2)" (3.1.1 Galaxies at z_abs=0.313)
- **GalPak3D** : 3D morpho-kinematic fitting  
  > "we used the GalPak$^{\rm 3D}$ algorithm (cite: bouche15)" (3.3 Morphological and Kinematical Properties)
- **MUSE pipeline** v1.6: MUSE data reduction  
  > "The ESO MUSE pipeline (cite: weilbacher15) version v1.6 was used to reduced the data" (2.2 New MUSE Observations)
- **MPDAF** : Extracting MUSE spectra  
  > "Using the MPDAF[^4] routine (cite: piqueras17), we extract the pixels at these coordinates" (3.1.1 Galaxies at z_abs=0.313)
- **Sextractor** : Source identification in HST image; inclination/PA fallback  
  > "we used *Sextractor* to identify and deblend faint objects in the broad band WFPC2 image" (3.1.1 Galaxies at z_abs=0.313)
- **VPFIT** v10.0: Voigt profile fits of UVES absorption  
  > "We modelled the absorption lines with Voigt profiles using VPFIT[^7] v10.0." (5 Gas Absorption Profiles)
- **RAMSES** : Zoom-in cosmological simulation  
  > "dedicated RAMSES Adaptive Mesh Refinement (AMR) simulations" (3.1.2 Cosmological zoom-in Simulations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(1-0) integrated flux G2 | 0.63 | ±0.01 | Jy km/s | 3 | / G2 / 11 30 07.66 / $-$14 49 23.41 / 9.7 / 44.8 / 0.63$\pm$0.01 / 250$\pm$50 / |
| CO(1-0) integrated flux G4 | 0.42 | ±0.03 | Jy km/s | 3 | / G4 / 11 30 07.62 / $-$14 49 11.44 / 18.0 / 83.2 / 0.42$\pm$0.03 / 535$\pm$50 / |
| CO(1-0) integrated flux G6 | 0.20 | ±0.01 | Jy km/s | 3 | / G6 / 11 30 08.53 / $-$14 49 28.54 / 21.5 / 99.4 / 0.20$\pm$0.01 / 205$\pm$50 / |
| Molecular mass range | 1.00 to 3.16 x alpha_CO x 1e9 | ±0.05 to ±0.07 | Msun | 3 | $M_{\rm mol}$ = (1.00$\pm$0.05) to (3.16$\pm$0.07) $\times$ ($\alpha_{\rm CO}$/1 K km/s pc$^2$) $\times$ 10$^9$ M$_{\odot}$ |
| Depletion time G2 | 13 | ±5 | Gyr | 3 | 3.16$\pm$0.07 / 13$\pm$5 |
| Continuum 5-sigma limit | 30 | rms 6 uJy | uJy | 1 | None of the objects are detected in the map with rms=6 $\mu$Jy, corresponding to a 5-$\sigma$ continuum flux limit of 30 $\mu$Jy. |
| N(CO) limit | <2e13 | not stated | cm^-2 | 0 | we derive a stringent limit on the CO column density of N(CO)$<$2$\times$10$^{13}$ cm$^{-2}$ |
| N(H2) limit | <7e18 | not stated | cm^-2 | 0 | this results in a limit of N(H$_2$)$<$7$\times$10$^{18}$ cm$^{-2}$ |
| Group velocity dispersion | ~170 | not stated | km/s | 0 | The velocity dispersion of the system is $\sim$170 km s$^{-1}$ |
| Group virial mass | 2.9e12 | not stated | Msun | 0 | The virial mass for such system will be 2.9$\times$10$^{12} M_{\odot}$. |
| Vmax G2 (CO) | 134 | ±14 | km/s | 5 | / **G2** / 2$\pm$1 / 76$\pm$3 / 117$\pm$2 / 134$\pm$14 / |
| ALMA cube rms | 0.11 | not stated | mJy/beam per 53 km/s | 1 | The final rms noise level of the cube is 0.11 mJy/beam per 53 km s$^{-1}$ channel |

## Qualitative findings

- Fourth emission line 26.4 arcsec south of quasar is CO(2-1) at z=1.614 or CO(3-2) at z=2.921; a continuum-spw line at 101.4 GHz is CO(2-1) at z=1.274  
  > "identified as CO(2–1) at z=1.274 thanks to the detection of the \[O ii\] doublet in the corresponding MUSE spectrum" (3.1.1 Galaxies at z_abs=0.313)

## Claim tuples

- H: Is the z=0.313 DLA associated with a single galaxy? | E: MUSE+ALMA survey of the field and comparison to zoom-in simulations | R: 11 galaxies at the absorber redshift (7 new), 3 detected in CO | F: The absorber arises from a galaxy group environment with complex structure, not a single galaxy | **supported**
- H: Do absorption-selected galaxies hold large molecular reservoirs? | E: CO(1-0) detection and depletion time computation | R: Mmol 1.0–3.2 x alpha_CO x 1e9 Msun; long depletion times | F: HI-selected galaxies have large molecular gas reservoirs inefficiently converted to stars | **supported**
- H: Does emitting galaxy gas explain all the absorption? | E: Compare metallicities and velocities to absorption, and simulations | R: Overlap in velocity is limited; absorber metallicity matches the lowest galaxy values | F: Neutral gas only partly related to the galaxies; the rest is likely faint low-surface-brightness tidal gas | **partially**

## Reasoning

- Why this data: Band 3 chosen to cover CO(1-0) at the absorber redshift; primary beam matches MUSE field of view  
  > "We note that the resulting FWHM of the primary beam of ALMA in band 3 is about $60"$, conveniently matching the MUSE field-of-view." (2.2 New ALMA Observations)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): CO-to-H2 conversion factor is uncertain, so masses are expressed as functions of alpha_CO  
  > "Estimates of the corresponding H$_2$ molecular masses however rely on the rather uncertain CO-H$_2$ conversion factor" (3.2 Physical Properties of the Galaxy Group)
- Limitation (authors): Analysis of G0 hampered by the bright quasar; GalPak3D did not converge for several galaxies  
  > "The analysis of galaxy G0 is hampered by the proximity to the bright quasar (2.3 arcsec)." (3.3 Morphological and Kinematical Properties)
- Caveat (inferred, ours): Group interpretation rests on one simulated halo qualitatively compared, with no quantitative match
- Caveat (inferred, ours): Resolution of 1.4 arcsec limits CO kinematics
- Caveat (inferred, ours): Depletion times depend on assumed alpha_CO=4.6 and a 25% MUSE flux error
- Caveat (inferred, ours): Four orders of magnitude fainter gas claim is only simulation-based

## Reproducibility

- Data public (paper): ALMA programme code given; MUSE and UVES from ESO archive  
  > "We obtained the VLT/UVES reduced quasar spectra from the ESO advanced data products archives" (5 Gas Absorption Profiles)
- Products in archive: _not stated_
- Missing: Simulation outputs (separate paper)
- Missing: GalPak3D configuration
- Missing: tclean cleaning details and self-cal solints
- Missing: MUSE sky-removal PCA code is purpose-developed
- Data volume (inferred): ALMA ~ tens of GB raw; MUSE cube ~ few GB
- Score (inferred): 3/5, ALMA data public and main steps described, but several key parameters and the simulation are missing.
- Rediscovery candidate: no, Results depend on MUSE data, GalPak3D settings and unreleased simulations; ALMA recipe incomplete.

## Links

- Method: (cite: bouche15) (GalPak3D algorithm)
- Method: (cite: peroux17) (Morpho-kinematic and metallicity methodology)
- Companion: Hamanowicz et al. (in prep) (Other two absorption systems in the field)
- Companion: Augustin et al. submitted (Simulation details)
- Related: MUSE Analysis of Gas around Galaxies (MAGG)
- Related: ESO programme 096.A-0303

## Checks

```json
{
 "quotes": 79,
 "quotes_ok": 79,
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
  "facts": 81,
  "stated": 57,
  "rate": 0.704
 },
 "evidence_ok": true
}
```
