# Resolved images of a protostellar outflow driven by an extended disk wind

`2016Natur.540..406B` | Nature 2016 | first author: Bjerkeli, Per | arXiv: 1612.05148 | DOI: 10.1038/nature20600

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Where in the protostellar disk is the TMC1A CO outflow launched, and is it an extended disk wind or an X-wind/stellar wind?  
  > "This demonstrates that the outflowing gas is launched by an extended disk wind from a Keplerian disk." (abstract)
- Target **TMC1A**: coordinates phase centre RA(J2000)=04h39m35.2s, Dec=+25°41´44.27´´  
  > "TMC1A is located in the Taurus Molecular" (main text); "The phase centre of the observations was 𝛼 2000 = 04h39m35.2s" (2 ALMA observations and data processing); z/distance 140 pc  
  > "TMC1A is located in the Taurus Molecular" (main text); "The phase centre of the observations was 𝛼 2000 = 04h39m35.2s" (2 ALMA observations and data processing); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.01415.S
- bands: _not stated_
- frequencies and spectral setup: 12CO, 13CO, C18O J=2-1 at 230.5, 220.4, 219.6 GHz; 244 kHz (0.32 km/s) resolution, 117 MHz bandwidth; one continuum baseband 976 kHz, 1875 MHz  
  > "The CO observations were carried out at a spectral resolution of 244 kHz (≈0.32 km s [−1] ) and the total bandwidth is 117 MHz." (ALMA observations and data processing)
- continuum bandwidth: _not stated_
- arrays: 12-m array  
  > "49 antennas in the 12-m array were used during the observations" (ALMA observations and data processing)
- configurations: _not stated_
- baselines: 85–16196 m (65–12450 kλ), 49 12-m antennas  
  > "49 antennas in the 12-m array were used during the observations providing baselines in the range 85–16196 m (=65–12450 kλ)." (ALMA observations and data processing)
- angular resolution: 6 au spatial resolution  
  > "The observations (see Methods) were taken at a spatial resolution of 6 au for TMC1A" (main text)
- max recoverable scale: 0.4 arcsec (~60 au)  
  > "leads to a maximum recoverable scale of 0.4 arcseconds (~60 au at 140 pc distance)" (ALMA observations and data processing)
- sensitivity: sigma = 0.8 mJy/beam (12CO channel maps)  
  > "Contours are from 3𝜎 in steps of 1.5𝜎 (𝜎 = 0.8 mJy/beam)." (Figure 1 caption)
- time on source: _not stated_
- observing dates: 2015 October 23 and 30  
  > "TMC1A was observed with ALMA on 2015 October 23 and 30." (ALMA observations and data processing)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (230.5 GHz)
- Line: 13CO J=2-1 (220.4 GHz)
- Line: C18O J=2-1 (219.6 GHz)
- External data: Protostar mass ~0.5 Msun, disk mass 0.05 Msun, inclination 55°, disk radius 200 au  
  > "a disk-like structure of radius 200 au which is inclined 55° with respect to the plane of the sky [14]" (main text) [from Harsono et al. 2014 (ref 14)]
- External data: Systemic velocity 6.4 km/s and outflow position angle ~165°  
  > "with position angle ~165° east of north." (main text) [from ref 14, 16]
- Simulation/model as data: Power-law Keplerian disk model with RADMC3D and non-LTE excitation, run through CASA sm tool, to predict CO isotopologue emission  
  > "A simple power-law disk model is used to estimate the CO isotopologue emission arising from a Keplerian disk." (Origin of the emission)

## Processing

### Calibration

- pipeline or manual: standard procedure in CASA  
  > "The data calibration and imaging was carried out in CASA [31] (version 4.5.0) and followed standard procedure." (ALMA observations and data processing)
- casa version: CASA 4.5.0  
  > "CASA [31] (version 4.5.0)" (ALMA observations and data processing)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: <10%  
  > "The flux calibration uncertainty is estimated to be less than 10%." (ALMA observations and data processing)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: CLEAN (Högbom)  
  > "transformed into the image domain using the CLEAN algorithm [32]" (ALMA observations and data processing)
- weighting robust: continuum Briggs robust 0.5; lines natural weighting  
  > "with Briggs weighting and the robust parameter set to 0.5. For the line emission, natural weighting is used" (ALMA observations and data processing)
- uv taper: 0.04 arcsec for continuum and 12CO; 0.10 arcsec for 13CO and C18O  
  > "we used a uv taper at 0.04 arcseconds for the continuum and [12] CO maps" (ALMA observations and data processing)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uv-domain constant fit to line-free channels  
  > "The continuum is subtracted in the uvdomain by fitting a constant to the line free channels." (ALMA observations and data processing)
- line free channels: _not stated_
- primary beam correction: not applied (<1% within 2 arcsec)  
  > "The presented data has not been corrected for the primary beam response." (Analysis of the continuum and spectral line maps)
- array combination: _not stated_
- smoothing: output spectral resolution 0.35 km/s  
  > "All spectral line output images have a spectral resolution of 0.35 km s [−1] ." (ALMA observations and data processing)
- final beam: _not stated_
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges
- Clean threshold, niter, masks, cell and image size
- Synthesized beam sizes
- Details of the non-LTE model and disk model parameters
- Choice of fitted pixel sets and weights in the footpoint fit
- Calibrator flux values and CASA calibration script
- Mean/definition of velocity-field (moment 1) clipping

## Analysis recipe

1. **Calibrate and image**: CASA calibration, uv continuum subtraction, CLEAN with tapers  
  > "The continuum is subtracted in the uvdomain by fitting a constant to the line free channels." (ALMA observations and data processing)
   - software: CASA
   - parameter: robust 0.5 continuum; natural for lines; taper 0.04''/0.10''  
  > "a uv taper at 0.10 arcseconds for the [13] CO and C [18] O maps" (ALMA observations and data processing)
   - fitting: _not stated_
   - validation: _not stated_
2. **Identify origin of 12CO emission and disk Keplerian rotation**: Compare isotopologues, estimate optical depths, simulate Keplerian disk, fit 2D Gaussians to 13CO/C18O channels for peak positions to derive central mass  
  > "we also fit 2D Gaussian distributions to all individual channel maps for [13] CO and C [18] O in order to find the peak positions." (Origin of the emission)
   - software: MATLAB, RADMC-3D, CASA
   - assumption: Kinetic temperature 100 K; isotopic ratios 60 (13CO) and 550 (C18O); i=55±10°  
  > "Assuming a kinetic temperature of 100 K and adopting isotopic ratios of 60 and 550 for [13] CO and C [18] O" (Origin of the emission)
   - fitting: _not stated_
   - validation: Disk models predict cospatial isotopologues, unlike observed  
  > "The models indicate that the observed spatial distribution of [12] CO, 13 CO and C 18 O should be cospatial in the case of a pure Keplerian disk." (Origin of the emission)
3. **Direct footpoint radius**: Flux-weighted first-order polynomial z=A(r−r0) fit to 12CO pixels above midplane per channel, eastern side only  
  > "first order polynomial fitting ( _z = A_ ( _r – r_ _0_ ) _; z_ is the distance above the disk midplane" (The launching radius)
   - software: MATLAB
   - parameter: S/N>3; velocities 2 to 5.5 km/s from systemic  
  > "Secondly, we exclude velocities > 5.5 km s [−1] with respect to the systemic velocity" (The launching radius)
   - assumption: Gas travels along straight lines  
  > "assuming the gas travels along straight lines" (main text)
   - fitting: linear least squares weighted by flux density  
  > "This linear least-squares fit provides a direct and straightforward estimate of the footpoint radius for each velocity channel" (main text)
   - validation: Tested with second-order polynomial and excluding data within 20 au of disk surface; results similar  
  > "The derived footpoint radii are similar and we conclude that the choice of exponent does not affect our scientific conclusions." (The launching radius)
4. **MHD-theory footpoint radius**: Eq. 4 of Anderson et al. 2003 applied per pixel using velocity field decomposed into rotation and outflow components, masking where escape velocity exceeds outflow velocity  
  > "using Eq. 4 of Anderson et al. (2003; ref 22)" (The launching radius)
   - assumption: vφ = vlos/sin(i)/2, vout = vlos/cos(i)/2; outflow perpendicular to disk, symmetric  
  > "_ν_ φ = _ν_ los /sin( _i_ )/2 and _ν_ out = _ν_ los /cos( _i_ )/2." (Origin of the emission)
   - fitting: _not stated_
   - validation: _not stated_
5. **Continuum ring and angular momentum**: Gaussian fit of deprojected radial continuum profile, excluding 12–33 au; specific angular momentum = rotational velocity × distance to axis  
  > "specific angular momentum is calculated as the product of the rotational velocity, and the distance to the central axis of the blue-shifted outflow" (Angular momentum of the outflowing gas)
   - software: MATLAB
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.5.0: calibration and imaging  
  > "The data calibration and imaging was carried out in CASA [31] (version 4.5.0)" (ALMA observations and data processing)
- **MATLAB** : channel-by-channel analysis  
  > "Each velocity channel is analysed individually using MATLAB." (Analysis of the continuum and spectral line maps)
- **RADMC-3D** : Keplerian disk modelling  
  > "The code RADMC-3D, used for the Keplerian disk modelling, is available at" (Code availability)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Footpoint radii (polynomial fit) | ~6 to ~22 | not stated | au | 3 | reveal a range of footpoint radii between ~6 and ~22 au |
| Footpoint radii (MHD theory) | ~2 to ~19 | not stated | au | 4 | revealing footpoint radii between ~2 and ~19 au (Fig. 3) |
| Central mass | 0.4 | ±0.1 | Msun | 2 | The central mass is estimated at 0.4±0.1 _M_ sun |
| Optical depths C18O, 13CO, 12CO | 0.04, 0.2, 25 | not stated | dimensionless | 2 | we calculate the optical depths (𝜏) to be 0.04, 0.2 and 25 for C [18] O, [13] CO and [12] CO |
| Specific angular momentum of outflow | <200 | not stated | au km/s | 5 | to be less than 200 au km s [−1] in the outflow |
| Continuum excess radius | ~20 | not stated | au | 5 | is located at a relatively constant radius of ~20 au |

## Qualitative findings

- 12CO emission is spatially shifted from 13CO, C18O and dust, indicating a non-disk (outflow) origin  
  > "A non-disk origin for [12] CO is suggested by the significant spatial shift" (main text)
- Outflow likely rotating, as two cavity walls are undetected  
  > "suggests that the outflow is rotating" (main text)

## Claim tuples

- H: Is the outflow launched from an extended disk region rather than near the protostar (X-wind/stellar wind)? | E: Fit footpoint radii from 12CO channel maps and MHD wind theory | R: Footpoint radii ~6–22 au and ~2–19 au | F: Extended disk wind; X-wind and stellar wind ruled out on observed scales | **supported**
- H: Does the outflow remove angular momentum from an extended disk region? | E: Specific angular momentum from 12CO velocity field | R: <200 au km/s increasing with distance | F: Angular momentum removed from extended disk region | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Fit with zero intercept (z=Ar^2) gives worse fit than free r0  
  > "the goodness of fit decreases because the observed geometry stands significantly more steeply" (The launching radius)
- How they decided it was enough: _not stated_
- Limitation (authors): 6 au resolution cannot exclude an unresolved confined high-velocity component  
  > "we cannot exclude the possibility of an additional, confined and high-velocity component" (main text)
- Caveat (inferred, ours): Rotation and outflow velocity decomposition assumes symmetric flow and perpendicular axis
- Caveat (inferred, ours): Missing emission at low velocities from spatial filtering limits footpoint inference
- Caveat (inferred, ours): Only eastern cavity wall fit

## Reproducibility

- Data public (paper): ALMA archive from 10 December 2016  
  > "will be available in the ALMA archive, https://almascience.nrao.edu/alma-data/archive, 10 December 2016" (Data availability)
- Products in archive: _not stated_
- Code: RADMC-3D public; non-LTE excitation code not released  
  > "We have opted not to make the non-LTE molecular excitation code available" (Code availability)
- Missing: Imaging parameters (cell, size, masks, thresholds)
- Missing: Analysis MATLAB code
- Missing: Disk model parameters
- Data volume (inferred): ~50-150 GB raw
- Score (inferred): 3/5, Data public and method clear, but imaging details and analysis code missing.
- Rediscovery candidate: yes, Public data, numeric footpoint radii, simple fitting recipe.

## Links

- Method: Anderson et al. 2003 (ref 22) (MHD footpoint radius formula)
- Companion: Aso et al. 2015 (ref 18) (Earlier ALMA observations of TMC1A)
- Companion: Harsono et al. 2014 (ref 14) (Disk properties of TMC1A)

## Checks

```json
{
 "quotes": 59,
 "quotes_ok": 59,
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
  "facts": 74,
  "stated": 44,
  "rate": 0.595
 },
 "evidence_ok": true
}
```
