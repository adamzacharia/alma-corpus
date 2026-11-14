# Radio Emission from the Magnetically Active M Dwarf UV Ceti from 1 to 105 GHz

`2024ApJ...970...56P` | The Astrophysical Journal 2024 | first author: Plant, Kathryn | arXiv: 2406.17280 | DOI: 10.3847/1538-4357/ad4356

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: stellar_physics
- Question: What are the radio emission components (flares, auroral ECME, persistent) of UV Ceti across 1–105 GHz, and which emission mechanisms explain them given its strong large-scale field?  
  > "Here we present multi-epoch characterization of the radio spectrum of UV Ceti spanning 1–105 GHz, exhibiting flared emission similar to coronal activity, auroral-like emission analogous to planetary magnetospheres, and slowly-varying persistent emission." (abstract)
- Target **UV Ceti (with companion BL Ceti)**: coordinates _not stated_; z/distance 2.7 pc  
  > "BL and UV Ceti are a nearby (2.7 pc) binary system" (abstract); "We used the coordinates and proper motions of UV and BL Ceti in the GAIA DR3 catalog to determine the position of the system barycenter at each epoch." (2.5 Astrometry); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00993.S
- bands: VLA L, S, C, Ku, K, Ka; ALMA band 3  
  > "ALMA band 3 | ALMA | 90–94 & 101–105 | Stokes I" (Table 1)
- frequencies and spectral setup: ALMA 90–94 & 101–105 GHz, four spectral windows  
  > "ALMA band 3 | ALMA | 90–94 & 101–105 | Stokes I" (Table 1); "imaging each of the four spectral windows in the ALMA observation" (3.1 Spectrum)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: VLA in B-North-C configuration for both observations  
  > "The VLA was in B-North-C configuration for both observations." (2.1 Observations)
- baselines: _not stated_
- angular resolution: ALMA beam 1.3x0.5 arcsec  
  > "ALMA band 3 | ALMA | 90–94 & 101–105 | Stokes I | – | – | 37 | 1.3$\times$0.5" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 37 minutes on UV Ceti with ALMA  
  > "ALMA band 3 | ALMA | 90–94 & 101–105 | Stokes I | – | – | 37 | 1.3$\times$0.5" (Table 1)
- observing dates: ALMA 23 July 2014; VLA 8 and 28 Jan 2011  
  > "UV Ceti was observed by ALMA on July 23 2014 in band 3, from 90 to 105 GHz" (2.1 Observations)
- pi or archival as stated: Archival observations  
  > "We present an analysis of archival observations of UV Ceti" (Introduction)
- Other facility **VLA**: 1–40 GHz observations (project 10C-210) in January 2011  
  > "UV Ceti was observed by the VLA on January 8 2011 in three bands between 1 and 25 GHz, and on January 28 2011 in five bands between 2 and 40 GHz (Project code 10C-210)." (2.1 Observations)
- Other facility **OVRO 40m**: Monitoring of J0132-1654 used to check flux density  
  > "our flux density measurement at Ku band agrees with the OVRO measurement from the following day" (2.2 Calibration)
- Other facility **Gaia DR3**: Coordinates and proper motions for astrometry  
  > "We used the coordinates and proper motions of UV and BL Ceti in the GAIA DR3 catalog" (2.5 Astrometry)
- External data: Orbital parameters and masses of the binary; stellar radius 0.159±0.006 Rsun  
  > "using masses and orbital parameters from (cite: Kervella2016) as input to the ephemeris calculator tool" (2.5 Astrometry) [from (cite: Kervella2016)]
- External data: Eight earlier VLA spectra for comparison  
  > "Figure [3](#fig:flux) also shows eight other VLA observations, from (cite: gudelbenz1996radiospectra) and (cite: Gudel1989)." (3.1 Spectrum) [from (cite: gudelbenz1996radiospectra); (cite: Gudel1989)]
- External data: Rotation period 5.45 hours  
  > "Since UV Ceti rotates with a period of 5.45 hours (cite: Barnes2016)" (3.1 Spectrum) [from (cite: Barnes2016)]

## Processing

### Calibration

- pipeline or manual: ALMA: pipeline-calibrated data from archive; VLA calibrated manually in CASA  
  > "We used CASA (cite: McMullin2007-CASA) to flag, calibrate, and image the VLA data, and to image the pipeline-calibrated data obtained from the ALMA archive." (2.2 Calibration)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: ALMA pipeline-calibrated data  
  > "to image the pipeline-calibrated data obtained from the ALMA archive" (2.2 Calibration)
- flux calibrator: ALMA: Uranus flux, J0132-1654 phase, J0137-2430 bandpass  
  > "For the ALMA observations, Uranus served as the flux density calibrator, J0132-1654 as the phase calibrator, and J0137-2430 as the bandpass calibrator." (2.2 Calibration)
- flux scale uncertainty: _not stated_
- self calibration: Phase-only self-cal at VLA L band using a model of a bright off-axis source  
  > "We used this first iteration image to create a model of the bright source, via the CLEAN algorithm, and then solved for a new phase-only calibration using that model." (2.4 Imaging)

### Imaging

- task: CASA tclean  
  > "We imaged the visibility data using the CASA tclean routine." (2.3 Imaging)
- deconvolver: _not stated_
- weighting robust: Briggs 0 (L band -0.5)  
  > "We used Briggs 0 weighting, except with L band for which we used Briggs -0.5" (2.3 Imaging)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: ALMA 1.3x0.5 arcsec  
  > "ALMA band 3 | ALMA | 90–94 & 101–105 | Stokes I | – | – | 37 | 1.3$\times$0.5" (Table 1)
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- CASA version used
- tclean cell size, image size, niter, thresholds and masks
- ALMA field and spectral-window selection and any channel averaging
- Method for flux density at each ALMA scan, and Monte Carlo details for the spectral index
- Stellar disk size and distance used for the brightness temperatures

## Analysis recipe

1. **Image and measure flux densities**: tclean images; Gaussian fit and peak pixel flux with off-source RMS  
  > "first by fitting a Gaussian source to the cleaned image via the CASA Gaussian fit tool" (2.3 Imaging)
   - software: CASA
   - parameter: Briggs 0 weighting  
  > "We used Briggs 0 weighting" (2.3 Imaging)
   - fitting: _not stated_
   - validation: Two methods gave similar results  
  > "These two methods provided similar results." (2.3 Imaging)
2. **Build light curves**: Shift phase center with fixvis, subtract other sources' model, average visibilities over channels, spws and baselines; ALMA light curve from five per-scan images  
  > "We used the CASA task fixvis to move the phase center to the position of UV Ceti" (2.4 Light Curves); "made by imaging each of the five correlator scans separately" (3.3 Temporal Variability: ALMA)
   - software: CASA fixvis
   - fitting: _not stated_
   - validation: Phase-calibrator flux constant; aperture flux checks of phase errors  
  > "we confirmed that the flux density of the phase calibrator varies by only a few percent during this time" (3.3 Temporal Variability: ALMA)
3. **Astrometric identification of the emitting binary component**: Gaussian position fits compared to Gaia-based predicted positions of UV and BL Ceti  
  > "We measured the positions of the source(s) in all images by fitting a Gaussian source to the cleaned images" (2.5 Astrometry)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared predictions with K band image where both detected  
  > "We estimate the uncertainty in predicted positions by comparing the predictions to the observed positions in the image in which both components are detected." (2.5 Astrometry)
4. **Spectral indices and polarization**: Image sidebands separately; power law fit; uncertainties by Monte Carlo propagation  
  > "these uncertainties are propagated by Monte Carlo process to constrain the uncertainty on the spectral index" (3.2 Temporal Variability: VLA)
   - fitting: Power law F ∝ ν^α  
  > "fitting a power law to the measured flux density vs frequency" (3.1 Spectrum)
   - validation: _not stated_
5. **Brightness temperatures and emission mechanism**: Brightness temperature assuming source size equal to stellar disk; compare cyclotron harmonic field strengths with dipole field  
  > "The brightness temperatures presented are calculated for a source size equal to the size of the stellar disk." (4.4 Brightness Temperature as a function of frequency)
   - assumption: Emitting region equals stellar disk; dipole field 2 kG at pole; radius 0.159 Rsun  
  > "the field at radial distance $r$ can be approximated as $B(r)=2\,kG(r/r_*)^{-3}$ above the pole" (4.2 Auroral emission)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Flagging, calibration, imaging, Gaussian fitting, fixvis, imstat  
  > "We used CASA (cite: McMullin2007-CASA) to flag, calibrate, and image the VLA data" (2.2 Calibration)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA millimeter spectral index | -0.81 | 0.36 | dimensionless | 4 | The millimeter emission has a spectral index $-0.81\pm0.36$ |
| Ka band spectral index | 0.63 | 0.27 | dimensionless | 4 | with a spectral index of $0.63 \pm 0.27$ |
| ALMA brightening during observation | 36% | not stated | percent | 2 | UV Ceti gradually brightened by 36% during the ALMA observation |
| ALMA position offset from UV Ceti | 0.09 | 0.41 | arcsec | 3 | $0.09\pm0.41$ arcseconds from the expected position of UV Ceti |
| Millimeter brightness temperature (disk-size source) | 6.5e5 | not stated | K | 5 | the flux density implies a brightness temperature of $6.5\times 10^5$ K |
| K band spectral index Jan 8 flare | 0.56 | 0.17 | dimensionless | 4 | the K band emission from UV Ceti has a spectral index $0.56\pm0.17$ |

## Qualitative findings

- No fast millimeter flares found in the ALMA data.  
  > "we searched for fast flares similar to the one-second millimeter flare from the M dwarf Proxima Centauri (cite: macgregor2021) and found none." (3.3 Temporal Variability: ALMA)

## Claim tuples

- H: Is the persistent emission consistent with optically thick or isotropic optically thin gyrosynchrotron? | E: Compared persistent flux across 1–105 GHz from non-simultaneous VLA and ALMA data | R: Flux density is nearly flat across 1–105 GHz | F: Isotropic optically thick or thin gyrosynchrotron unlikely; radiation-belt-like anisotropic electrons possible | **partially**
- H: Does the ALMA millimeter emission vary? | E: Per-scan imaging of ALMA data | R: 36% brightening over ~30 minutes | F: Variability likely intrinsic, rotational modulation or slow flare | **supported**
- H: Do C and S band bursts reflect ECME? | E: Polarization of VLA bursts | R: Intensely circularly polarized bursts, same sense as earlier ECME | F: Consistent with auroral ECME | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Thermal gyroresonance ruled out for flares because brightness temperatures exceed coronal temperatures.  
  > "Thus, thermal gyroresonance emission can be ruled out." (4.1 Flares)
- How they decided it was enough: _not stated_
- Limitation (authors): VLA bands observed sequentially, not simultaneously, so no instantaneous spectrum.  
  > "it is important to emphasize that the VLA observations in each band were conducted sequentially, not simultaneously" (3.1 Spectrum)
- Caveat (inferred, ours): Non-simultaneous multi-epoch data across three years limit spectral conclusions
- Caveat (inferred, ours): Single 37-minute ALMA epoch
- Caveat (inferred, ours): Brightness temperatures depend on assumed disk-size source
- Caveat (inferred, ours): Rotational modulation claim rests on few overlapping low S/N observations

## Reproducibility

- Data public (paper): Archival VLA and ALMA data  
  > "We present an analysis of archival observations of UV Ceti" (Introduction)
- Products in archive: _not stated_
- Missing: CASA version
- Missing: tclean parameters beyond weighting
- Missing: Flux extraction details for ALMA per-scan images
- Data volume (inferred): Tens of GB (VLA multi-band plus one ALMA band 3 EB)
- Score (inferred): 5/5, Public archival data and simple workflow, but imaging parameters and CASA version are missing.
- Rediscovery candidate: yes, Public data, stated calibrators and weighting, numeric results such as the ALMA spectral index and 36% brightening.

## Links

- Companion: (cite: Villadsen2019) (Earlier radio study of UV Ceti ECME)
- Related: VLA project 10C-210

## Checks

```json
{
 "quotes": 52,
 "quotes_ok": 52,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 38,
  "rate": 0.543
 },
 "evidence_ok": true
}
```
