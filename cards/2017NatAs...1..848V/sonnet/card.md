# The shock-heated atmosphere of an asymptotic giant branch star resolved by ALMA

`2017NatAs...1..848V` | Nature Astronomy 2017 | first author: Vlemmings, Wouter | arXiv: 1711.01153 | DOI: 10.1038/s41550-017-0288-9

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars, stellar_physics
- Question: Does the extended atmosphere of the AGB star W Hya contain hot, shock-heated chromospheric gas, and what are its temperature, mass and kinematic structure?  
  > "We show that hot gas with chromospheric characteristics exists around the star. Its filling factor is shown to be small." (abstract)
- Target **W Hya**: coordinates RA(J2000) = 13h49m01.939s, Dec(J2000) = -28d22m04.484s  
  > "The image is centered at RA(J2000) = 13 h 49 m 01.939 s and Dec(J2000) = -28 d 22 m 04.484 s" (Figure 1 caption); "The image is centered at RA(J2000) = 13 h 49 m 01.939 s and Dec(J2000) = -28 d 22 m 04.484 s" (Figure 1 caption); z/distance 98 pc  
  > "The image is centered at RA(J2000) = 13 h 49 m 01.939 s and Dec(J2000) = -28 d 22 m 04.484 s" (Figure 1 caption); "(2 au, for an adopted distance of 98 parsec _(21)_ )" (Main text, introduction of W Hya); distance from Vlemmings et al. 2003 (ref 21), VLBI OH maser parallax  
  > "The image is centered at RA(J2000) = 13 h 49 m 01.939 s and Dec(J2000) = -28 d 22 m 04.484 s" (Figure 1 caption); "VLBI astrometry of circumstellar OH masers: Proper motions and parallaxes of four AGB stars" (References and Notes)

## Data provenance

- ALMA projects: 2015.1.01446.S
- bands: _not stated_
- frequencies and spectral setup: spw0 937.5 MHz/960 ch at 330.87 GHz; spw1 937.5 MHz/960 ch at 342.87 GHz; spw2 1.875 GHz/3840 ch at 344.97 GHz  
  > "Two spectral windows of 937.5 MHz and 960 channels were centered on 330.87 (spw0) and 342.87 GHz (spw1), and a window of 1.875 GHz and 3840 channels was centered on 344.97 GHz (spw2)." (Methods 1)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 18 to 8283 m, 47 antennas, extended configuration  
  > "The observations were done using 47 antennas in an extended configuration, with baseline lengths between 18 and 8283 m." (Methods 1)
- angular resolution: 17x24 mas uniform-weighting dirty beam; 0.031x0.038" with Briggs  
  > "Using uniform weighting, we obtained a beam of 0.017x0.024” at a similar position angle at the expense of dynamic range." (Methods 1)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: about 2.3 hours on source (4.25 hours total)  
  > "The observations spanned a total time of 4.25 hours, of which approximately 2.3 hours were spent on source." (Methods 1)
- observing dates: Nov 30, Dec 3 and Dec 5 2015 (three observing blocks)  
  > "The first observation was taken Nov 30 th 2015, the second on Dec 3 rd 2015, and the third on Dec 5 th 2015." (Methods 1)
- pi or archival as stated: _not stated_
- Line: CO v=1, J=3-2 (342.647 GHz)
- Line: SO2 (tentative) v2=2, 27(3,25)-28(0,28) (345.01713 GHz)
- External data: Photospheric radius ~20 mas and stellar parameters from near-IR observations  
  > "It is estimated to have a photospheric radius R ★ ~20 mas" (main text) [from Woodruff et al. 2009 (cite: 19); Zhao-Geisler et al. 2011 (cite: 20)]
- External data: SO2 line list: ExoMol Einstein coefficients and energies; SLAIM frequencies  
  > "We use the ExoMol database for the Einstein coefficients and energy level energy." (Methods 5) [from Underwood et al. 2016 (cite: 41); SLAIM Splatalogue (cite: 40)]

## Processing

### Calibration

- pipeline or manual: Observatory-provided scripts with extra flagging of one antenna  
  > "We adopted the calibration approach of the observatory provided scripts." (Methods 1)
- casa version: CASA 4.7.0  
  > "The data were reduced using CASA 4.7.0." (Methods 1)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1337-1257, 1.437 Jy at 339.57 GHz, spectral index -0.77  
  > "Flux and bandpass calibration were done on the quasar J1337-1257, for which a flux of 1.437 Jy at 339.57 GHz, and a spectral index of -0.77, were adopted." (Methods 1)
- flux scale uncertainty: maximum 10%  
  > "we conclude that the maximum absolute flux uncertainty is 10%." (Methods 1)
- self calibration: two rounds of phase and one of phase+amplitude self-cal on stellar continuum; dynamic range ~380 to ~2860  
  > "we performed two rounds of phase self-calibration and one round of phase and amplitude self-calibration on the stellar continuum." (Methods 1)

### Imaging

- task: CASA tclean  
  > "Using robust Briggs weighting in the CASA task tclean, we obtained a synthesized beam of 0.031x0.038” at position angle -84.3 deg." (Methods 1)
- deconvolver: _not stated_
- weighting robust: Final images uniform weighting (Briggs trial, robust value not given)  
  > "we produced our final images using uniform weighting and a 17 mas restoring beam." (Methods 1)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: ~1 km/s spectral resolution for line imaging  
  > "For the line imaging, we used a ~1 km s -1 spectral resolution." (Methods 1)
- final beam: 17 mas circular restoring beam  
  > "we produced our final images using uniform weighting and a 17 mas restoring beam." (Methods 1)
- final rms: 18 K (continuum, brightness temperature); 0.45 mJy/beam  
  > "The rms noise in the image is 18 K and the peak is 3560 K." (Figure 1 caption)

### Inherited from earlier work

- CO v=1 J=3-2 radiative transfer model based on earlier model, modified for three layers  
  > "The model is based on the one presented in (27), but was modified to include three different layers" (Methods 3) [from Khouri et al. 2016 (cite: 27)]
- Turbulence FWHM of 3 km/s  
  > "The full-width at half maximum of the turbulence broadening term was considered to be 3 km s -1 (38)" (Methods 3) [from Tsuji 1986 (cite: 38)]

### Not stated but needed to reproduce (our reading)

- Robust value for Briggs weighting
- Line-free channels and continuum subtraction method for the line cubes
- Self-calibration solution intervals and which spectral windows were used for the continuum
- Image size and cell size
- Specific radiative transfer code and chi2 grid ranges and step sizes
- Which components, starting parameters and UVMULTIFIT settings were used
- Spectrum extraction regions (hemisphere and annulus definitions)

## Analysis recipe

1. **Calibrate and self-calibrate**: Observatory script calibration, extra flagging, phase and amplitude self-calibration on stellar continuum  
  > "After the script calibration, we performed two rounds of phase self-calibration and one round of phase and amplitude self-calibration on the stellar continuum." (Methods 1)
   - software: CASA
   - fitting: _not stated_
   - validation: Each observing block imaged separately; structure consistent  
  > "Although the beam is different for the three epochs, the structure is fully consistent." (Methods 1)
2. **Image continuum and convert to brightness temperature**: tclean uniform weighting with 17 mas restoring beam; Tb from elliptical Gaussian formula  
  > "The brightness temperature image was created from the total intensity image using the formula for the brightness temperature of an elliptical Gaussian" (Methods 1)
   - software: CASA tclean
   - assumption: Optically thick free-free emission so brightness temperature equals gas temperature  
  > "Assuming optically thick free free emission, the brightness temperature is equal to the gas temperature." (main text)
   - fitting: _not stated_
   - validation: Beam choice does not affect flux density in spectra and residuals  
  > "We have confirmed that the beam selection does not affect the flux density in our spectra and the measured residuals." (Methods 1)
3. **Fit uniform elliptical disk and compact hotspots in visibilities**: Visibility fitting of disk plus Gaussian/point components; size limit from sigma_s = 2/SNR x beam  
  > "Our fit to the stellar disk was performed using the visibility fitting code UVMULTIFIT (32)." (Methods 2)
   - software: UVMULTIFIT, CASA, AIPS
   - parameter: Strongest hotspot SNR=59; 5 sigma size limit <2x3 mas  
  > "With 5 σ confidence we can thus determine the size to be <2x3 mas, providing a temperature of > 5.3x10 4 K." (Methods 2)
   - fitting: Disk fixed at 51.0x56.5 mas PA 65.7 deg for component fits  
  > "We fit a disk with a fixed size of 51.0x56.5 mas (position angle 65.7 degrees)" (Methods 2)
   - validation: Imaging with CASA and AIPS both give point-source component  
  > "Both using CASA and AIPS, the deconvolved component size is found to be indistinguishable from a point source." (Methods 1)
4. **Model CO v=1 J=3-2 spectra**: LTE radiative transfer through spherical shell with outflow, infall and warm layers, linear velocity law; chi2 fit to hemisphere and annulus spectra  
  > "The populations of the rotational levels were calculated using the Boltzmann distribution under the assumption of local thermodynamical equilibrium (LTE)." (Methods 3)
   - parameter: Rout = 2.4 R★ (4.8 au); spectra binned to 3 km/s for chi2  
  > "We used spectra binned to 3 km/s resolution for these calculations to further improve the signal-to-noise." (Methods 3)
   - assumption: CO/H2 abundance 4x10^-4; constant density and excitation temperature per layer  
  > "The gas mass is calculated using a abundance ratio of CO with respect to H 2 of 4x10 -4 ." (Methods 3)
   - fitting: chi2 minimization, formal 1-sigma uncertainties; no sampler  
  > "We determined the best fits and estimated the uncertainties within the assumptions of our described model on the derived parameters by calculating the 𝛘 2 of the fit of the models to the observed spectra." (Methods 3)
   - validation: Compared with and without warm layer by reduced chi2; alternative equal-temperature approach changes results by ~10% and ~5%  
  > "We find that the derived temperatures and densities are different by only ~10% and ~5% with respect to the previous models." (Methods 3)

## Software

- **CASA** 4.7.0: Data reduction, tclean imaging, image fitting  
  > "The data were reduced using CASA 4.7.0." (Methods 1)
- **UVMULTIFIT** : Visibility fitting of stellar disk and hotspots  
  > "Our fit to the stellar disk was performed using the visibility fitting code UVMULTIFIT (32)." (Methods 2)
- **AIPS** : Image fitting of hotspot size  
  > "Both using CASA and AIPS, the deconvolved component size is found to be indistinguishable from a point source." (Methods 1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Stellar flux density | 470 | 48 | mJy | 3 | which has a flux density of 470 ± 48 mJy |
| Average disk brightness temperature | 2495 | 255 | K | 3 | The disk has an average brightness temperature of 2495 ± 255 K. |
| Disk major axis | 56.5 | 0.1 | mas | 3 | It has a major axis of 56.5 ± 0.1 mas |
| Disk minor axis | 51.0 | 0.1 | mas | 3 | a minor axis of 51.0 ± 0.1 mas |
| Hotspot brightness temperature limit | >5.3x10^4 | lower limit | K | 3 | With 5 σ confidence we can thus determine the size to be <2x3 mas, providing a temperature of > 5.3x10 4 K. |
| Hotspot area filling factor | <0.2 | upper limit | percent | 3 | corresponding to an area filling factor <0.2% |
| Stellar velocity V*,lsr | 39.2 | 0.2 | km/s | 4 | we find that it peaks around V = 39.2 ± 0.2 km s -1 |
| Mass in visible warm layer | ~2x10^-5 | factor of two | Msun | 4 | The total mass in the visible warm layer, not hidden behind the optically thick continuum surface, is ~ 2x10 -5 M ¤, with an uncertainty of a factor of two. |
| Cool gas mass between 2.6 and 5 au | 1.4x10^-4 | 0.4x10^-4 | Msun | 4 | is (1.4 ± 0.4)x10 -4 M ¤ . |
| Warm layer volume-filling factor | <4 | upper limit | percent | 4 | the volume-filling factor of the warm gas is <4% |
| Warm layer temperature | 2900 | +400/-500 | K | 4 | 2900+400 -500 |

## Qualitative findings

- Disk is non-uniform with regions hotter and cooler than photosphere; kinematics differ between hemispheres  
  > "It is immediately apparent that the stellar disk is far from uniform." (main text)

## Claim tuples

- H: Does hot chromospheric gas with small filling factor exist around W Hya? | E: Resolved 338 GHz continuum, visibility fitting of disk and hotspots | R: Unresolved hotspot with Tb >5.3x10^4 K, area filling factor <0.2% | F: Shock-heated hot gas with small filling factor exists | **supported**
- H: Is there a warm molecular layer plus infall/outflow in the atmosphere? | E: Radiative transfer modelling of CO v=1 J=3-2 spectra | R: Warm layer ~2900 K, cool layers 850-900 K, infall/outflow ~±20 km/s | F: Warm molecular layer and fast infall/outflow, in conflict with models | **partially**
- H: Do shocks cool instantaneously? | E: Compare measured temperatures with models | R: High temperatures persist | F: Post-shock cooling time cannot be instantaneous | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Models with equal gas temperature in the two hemispheres tested; derived values differ ~10% and ~5%  
  > "We find that the derived temperatures and densities are different by only ~10% and ~5% with respect to the previous models." (Methods 3)
- How they decided it was enough: _not stated_
- Limitation (authors): SO2 identification of the emission line is tentative  
  > "we also cannot rule out that the emission originates from a different, unidentified, molecular or atomic transition." (Methods 5)
- Limitation (authors): Choice of one component per quadrant is arbitrary; degeneracies prevent constraining surface structure  
  > "the choice of a single component per quadrant is arbitrary and only serves to highlight that more than a single component is needed to describe the data." (Methods 2)
- Caveat (inferred, ours): Warm layer detection is marginal (4.2 sigma in a few channels; chi2 statistically indistinguishable)
- Caveat (inferred, ours): Spherical LTE model with constant layers is a strong simplification
- Caveat (inferred, ours): Brightness temperature depends on the 10% flux scale and on a uniform-disk assumption
- Caveat (inferred, ours): Hotspot temperature is only a lower limit

## Reproducibility

- Data public (paper): Data available via ALMA archive  
  > "The data that support the findings of this study are available though the ALMA archive" (Data availability)
- Products in archive: _not stated_
- Missing: Radiative transfer code not released
- Missing: Briggs robust value, imaging parameters and self-cal intervals
- Missing: Extraction regions for spectra
- Data volume (inferred): ~100-300 GB (three extended-configuration execution blocks, high spectral resolution)
- Score (inferred): 3/5, Public data and clear recipe for continuum and disk fit, but custom radiative transfer code and several imaging settings are unspecified.
- Rediscovery candidate: no, The disk fit is reproducible, but the CO modelling uses unreleased code and unspecified settings.

## Links

- Method: Martí-Vidal et al. 2014 (cite: 32) (UVMULTIFIT visibility fitting)
- Method: Khouri et al. 2016 (cite: 27) (Basis of CO v=1 radiative transfer model)

## Checks

```json
{
 "quotes": 66,
 "quotes_ok": 66,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 45,
  "rate": 0.643
 },
 "evidence_ok": true
}
```
