# PROJECT-J: JWST Observations of HH46 IRS and Its Outflow. Overview and First Results

`2024ApJ...967..168N` | The Astrophysical Journal 2024 | first author: Nisini, Brunella | arXiv: 2404.06878 | DOI: 10.3847/1538-4357/ad3d5a

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation
- Question: Disentangle the proposed mechanisms at the origin of the HH46 IRS outflow and cavity using JWST NIRSpec and MIRI spectroscopy; ALMA 12CO 2-1 is used only as a comparison with the warm H2 emission  
  > "The main aim of the project is to disentangle among the proposed mechanisms at the origin of the outflow and the associated cavity." (1 Introduction); "To better compare the morphology of the warm molecular emission with that of the cold CO gas" (4.2.4 Comparison between H2 and CO ALMA observations)
- Target **HH46 IRS**: coordinates 2MASSJ08254384-5100326 (source designation); coordinates of the ALMA pointing not stated  
  > "HH46 IRS (2MASSJ08254384-5100326) is a low mass Class I source" (1.1 HH46 IRS and its outflow); "located in a Bok globule at the edge of the Gum Nebula ($d$=450 pc)" (1.1 HH46 IRS and its outflow); z/distance d = 450 pc  
  > "HH46 IRS (2MASSJ08254384-5100326) is a low mass Class I source" (1.1 HH46 IRS and its outflow); "located in a Bok globule at the edge of the Gum Nebula ($d$=450 pc)" (1.1 HH46 IRS and its outflow); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00382.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO 2-1 (not stated)
- Other facility **JWST NIRSpec IFU and MIRI MRS (program 1706)**: Primary data: 1.66-28 micron IFU spectral maps of HH46 IRS and its outflow  
  > "as part of the JWST Cycle 1 program PROJECT-J (ID 1706, P.I. B. Nisini)" (2 Observations and Data reduction)
- Other facility **JWST NIRCam (DDT program 4441)**: F187N and F200W images used to resolve the binary  
  > "we used two images taken with NIRCam in the F187N and F200W filters (DDT program 4441)" (4.2.2 The binary at the origin of the two outflows ?)
- Other facility **HST**: Earlier image used to measure the change in binary position angle  
  > "the comparison between the NIRCam and HST images, the latter taken about 25 yrs earlier, in a similar filter" (4.2.2 The binary at the origin of the two outflows ?)
- Other facility **Spitzer IRS**: Spectrum used to check the global flux calibration of the JWST spectrum  
  > "shows also the Spitzer IRS spectrum of HH46 IRS from (cite: noriega2004), and other literature mid-IR photometric points for the source" (2.3 Spectra extraction and flux calibration)
- External data: Jet inclination of about 37 deg to the plane of the sky, used to convert radial to total jet velocity  
  > "it is inclined by about 37$^{\circ}$ with respect to the plane of the sky (cite: hartigan2005)" (1.1 HH46 IRS and its outflow) [from (cite: hartigan2005)]
- External data: Spitzer IRS spectrum of HH46 IRS used for flux calibration comparison  
  > "shows also the Spitzer IRS spectrum of HH46 IRS from (cite: noriega2004), and other literature mid-IR photometric points for the source" (2.3 Spectra extraction and flux calibration) [from (cite: noriega2004)]
- External data: Binary companion detected at 0.26 arcsec separation in HST 2 micron image  
  > "the binary detected by (cite: reipurth2000) with a separation of 0.26$''$ remains unresolved within the PSF of these instruments" (2.3 Spectra extraction and flux calibration) [from (cite: reipurth2000)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
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
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- V_LSR of HH46 IRS taken equal to the cloud velocity of +5 km/s  
  > "The $V_{LSR}$ of HH46 IRS has been taken to be equal to the cloud velocity of $+5$ km s$^{-1}$ following (cite: arce2013)." (2.4 Maps of continuum-subtracted line emission) [from (cite: arce2013)]
- Description of the ALMA 12CO 2-1 outflow shells and cavity walls used to choose the comparison channel  
  > "As shown in (cite: zhang2019), the $^{12}$CO 2-1 outflow presents several emission shells travelling at different velocities" (4.2.4 Comparison between H2 and CO ALMA observations) [from (cite: zhang2019)]

### Not stated but needed to reproduce (our reading)

- Whether the ALMA 12CO 2-1 cube was newly reduced here or taken from Zhang et al. 2019; no calibration, CASA version or imaging parameters are given
- ALMA array configuration, spectral setup, beam, rms and channel width of the 12CO 2-1 data
- Velocity of the overlaid CO channel in terms of the cloud-corrected reference and how the CO map was registered to the JWST astrometry
- Exact continuum windows used for the linear and spline continuum fits for each JWST line
- Details of the aperture and scale-factor choices for the MIRI sub-band flux matching

## Analysis recipe

1. **Reduce JWST MIRI MRS and NIRSpec IFU data into cubes**: JWST pipeline stages 1-3 with custom background subtraction, astrometric correction, warm-pixel masking and column-noise correction  
  > "we created a master background using the background observation rate files for each detector." (2.1 MIRI); "We use the default parameters, carefully inspecting the intermediate products for each step." (2.2 NIRSpec)
   - software: JWST pipeline, LaCosmic
   - parameter: MIRI pointing adjustment of 0.133 arcsec in R.A. and 0.089 arcsec in DEC from HST + Gaia sources  
  > "we used HST + Gaia sources identified in the MIRI simultaneous imaging field, deriving a pointing adjustment of 0.133$''$ in R.A. and 0.089$''$ in DEC." (2.1 MIRI)
   - parameter: NIRSpec vertical noise corrected by subtracting the median of each column in each rate file  
  > "To correct for this vertical noise, we obtained the median of each column and subtracted them." (2.2 NIRSpec)
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract 1D spectra and set the flux calibration**: Aperture proportional to the diffraction-limited beam (4 times the beam size); MIRI sub-bands matched by ratio of median fluxes in overlaps; NIRSpec rescaled to MIRI  
  > "We considered an aperture of 4 times the beam-size in order to retrieve any flux extending beyond the diffraction-limited beam." (2.3 Spectra extraction and flux calibration); "We rescaled the NIRSpec spectrum to the MIRI one" (2.3 Spectra extraction and flux calibration)
   - fitting: _not stated_
   - validation: Compared with the Spitzer IRS spectrum and IRAC photometry  
  > "we also get a good agreement with the overall flux density with the Spitzer IRAC photometry at 3.6, 4.5 and 5.8 $\mu$m" (2.3 Spectra extraction and flux calibration)
3. **Make continuum-subtracted line maps**: Linear fit to the continuum on each side of the line, subtracted pixel by pixel in a sub-cube; spline fit tried for longer wavelengths  
  > "Then we perform a linear fit through the continuum, estimated by carefully selecting a wavelength range on each side of the line free from any other emission feature." (2.4 Maps of continuum-subtracted line emission); "This continuum is then subtracted, pixel by pixel, in each frame of the sub-cube." (2.4 Maps of continuum-subtracted line emission)
   - fitting: Linear (or spline) continuum fit  
  > "we also tried a fit with a spline function, that better traces the continuum undulation, when present." (2.4 Maps of continuum-subtracted line emission)
   - validation: _not stated_
4. **Build velocity channel maps and measure jet width**: Interpolate frames to 30 km/s channels; fit a Gaussian across the jet and correct for instrumental broadening  
  > "by interpolating the frames in order to have equally spaced interval of 30 km s$^{-1}$" (3.1 The atomic jet); "we measured the jet width at about 1$^{\prime\prime}$ from the source as the Full Width at Half Maximum (FWHM) of a Gaussian fit in the transversal direction, corrected for instrumental broadening" (3.1 The atomic jet)
   - assumption: Jet inclination of about 37 deg to the plane of the sky  
  > "Considering the jet inclination of $\sim$ 37$^{\circ}$" (3.1 The atomic jet)
   - fitting: Gaussian fit in the transverse direction  
  > "FWHM) of a Gaussian fit in the transversal direction" (3.1 The atomic jet)
   - validation: _not stated_
5. **Compare warm H2 with ALMA 12CO 2-1 cavity emission**: Overlay of a single low-velocity 12CO 2-1 channel (+/- 9 km/s, cloud-corrected) on the MIRI H2 S(7) and S(1) images  
  > "we overlay in Fig. [10](#fig:H2_CO) the ALMA $^{12}$CO 2-1 at velocity $\pm$ 9 km s$^{-1}$ (cloud-corrected)" (4.2.4 Comparison between H2 and CO ALMA observations); "We make here the comparison with a single CO low velocity channel as this roughly corresponds to the first observed structured shell" (4.2.4 Comparison between H2 and CO ALMA observations)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **JWST pipeline** 1.11.1: Reprocessing MIRI MRS and NIRSpec IFU data (calwebb stages 1-3)  
  > "The data were reprocessed using the JWST pipeline version 1.11.1 (cite: bushouse2023)" (2.1 MIRI)
- **CRDS** context jwst_1094.pmap: Calibration reference files for the pipeline  
  > "The data were processed using the JWST pipeline version 1.11.1 with the corresponding CRDS context file" (2.2 NIRSpec)
- **LaCosmic** : Identifying warm spurious pixels in MIRI exposures  
  > "using the LaCosmic algorithm developed to remove cosmic rays hits from CCD images (cite: vandokkum2001)" (2.1 MIRI)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Closest red-shifted jet detection to the source | ~90 au | not stated | au | 3 | the red-shifted jet is clearly detected for the first time down to $\sim$ 90 au from the source |
| Jet terminal radial velocity beyond ~3 arcsec | 180-200 | not stated | km/s | 4 | The jet terminal radial velocity at distances larger than $\sim$ 3$^{\prime\prime}$ is within 180-200 km s$^{-1}$. |
| Total jet velocity | ~380 | not stated | km/s | 4 | the observed maximum radial velocity translates into a total jet velocity of about 380 km s$^{-1}$ |
| Jet width at ~1 arcsec, -90 km/s channel to -300 km/s channel | ~0.7 arcsec (315 au) to 0.39 arcsec (175 au) | not stated | arcsec (au) | 4 | This width linearly decreases from $\sim$ 0.7$''$ (315 au) in the -90km s$^{-1}$ channel to 0.39$''$ (175 au) in the -300km s$^{-1}$ channel. |
| [Ne II] 12.8 um / [Ne III] 15.5 um ratio on knot B1 | ~20 | not stated | dimensionless | 3 | is about 20 on knot B1, which would be consistent with both scenarios |
| H2 2.12 um / 12.3 um intensity ratio on knot A1 | 3.7 | not stated | dimensionless | 3 | on knot A1 a 2.12 $\mu$m/12.3 $\mu$m intensity ratio equal to 3.7 is observed |
| Binary companion distance from main source in NIRCam | 0.23 arcsec | not stated | arcsec | 0 | the NIRCam images show a weaker emission peak at a distance of 0.23$''$ from the main source |
| Change in binary position angle over ~25 yr (HST to NIRCam) | ~13 degrees counter-clockwise | not stated | degrees | 0 | has changed its PA with respect to the primary A by about 13 degrees counter-clockwise |
| Absolute flux calibration uncertainty of the on-source spectrum | up to 40% | not stated | percent | 2 | The absolute calibration has however an uncertainty of up to 40% in the on-source extracted spectrum. |

## Qualitative findings

- Warm H2 emission along the cavity lies inside the ALMA CO cavity in both lobes  
  > "We see that the H$_2$ emission observed along the cavity is inside the CO emission in both lobes." (4.2.4 Comparison between H2 and CO ALMA observations)
- H2 and CO overlap spatially only in the northern part of the blue-shifted cavity  
  > "The H$_2$ and CO emissions are instead spatially overlapping only in the northern part of the blue-shifted cavity." (4.2.4 Comparison between H2 and CO ALMA observations)

## Claim tuples

- H: Can JWST trace the red-shifted counter-jet close to the source? | E: MIRI MRS continuum-subtracted line maps of the 5.3 um [Fe II] and 12.8 um [Ne II] lines | R: Red-shifted jet detected down to ~90 au from the source | F: Both lobes of the atomic jet are seen close to the source for the first time | **supported**
- H: What excites the highly ionised jet gas? | E: Detection of [Ne III] and other high-ionisation lines along the flow, and comparison of recombination and flow timescales | R: [Ne III] extends beyond 3000 au along the flow | F: High-velocity shocks are the likely source of ionisation, with direct stellar photoionisation not excluded near the source | **partially**
- H: How does the warm H2 emission relate to the cold CO cavity seen by ALMA? | E: Overlay of a single low-velocity ALMA 12CO 2-1 channel on MIRI H2 S(7) and S(1) images | R: H2 emission along the cavity lies inside the CO emission in both lobes | F: Warm emission from the cavity could be driven by shocks or photon-heating of the cavity walls | **supported**
- H: Is the asymmetric blue-shifted H2 emission driven by the companion of the binary? | E: NIRCam F187N and F200W images compared with NIRSpec and HST images, plus H2 arc and knot orientations | R: Companion detected at 0.23 arcsec; A1 arc orientation (PA ~65 deg) differs from jet PA (~43 deg) | F: The A1 shell and possibly the large H2 arcs may be driven by source B | **partially**

## Reasoning

- Why this data: JWST is best suited to Class I sources, whose envelopes can be penetrated at mid-IR wavelengths  
  > "JWST is best suited for the study of the intermediate age Class I objects" (1 Introduction)
- Why this method: A single low-velocity CO channel was chosen because it roughly matches the first structured shell and traces the cavity walls  
  > "We make here the comparison with a single CO low velocity channel as this roughly corresponds to the first observed structured shell" (4.2.4 Comparison between H2 and CO ALMA observations)
- Alternative: A spline continuum fit was tried in addition to a linear fit for lines above ~10 micron  
  > "we also tried a fit with a spline function, that better traces the continuum undulation, when present." (2.4 Maps of continuum-subtracted line emission)
- How they decided it was enough: _not stated_
- Limitation (authors): Continuum subtraction leaves residual noise close to the source at long wavelengths  
  > "the procedure leaves significant residual noise close to the source that compromises the identification of the line emission morphology" (2.4 Maps of continuum-subtracted line emission)
- Limitation (authors): MIRI fluxes may be overestimated by the non-optimal extraction  
  > "it might be that the MIRI fluxes are overestimated using our non-optimal extraction that does not take into consideration the complex PSF of the instrument." (2.3 Spectra extraction and flux calibration)
- Caveat (inferred, ours): The ALMA CO 2-1 data are shown in a single channel with no description of calibration, imaging, beam or rms, so the H2 versus CO comparison is qualitative and not reproducible from this paper alone
- Caveat (inferred, ours): The claim that source B drives the blue-shifted H2 shells rests on morphology and position angles, without proper motions or kinematics
- Caveat (inferred, ours): Large absolute flux calibration uncertainty (up to 40%) and unresolved discrepancy with Spitzer limit quantitative use of the spectra

## Reproducibility

- Data public (paper): JWST data available from MAST (program 1706); ALMA data cited by project code, with its public status not stated  
  > "The data were obtained from the Mikulski Archive for Space Telescopes at the Space Telescope Science Institute" (5 Conclusions); "This paper makes use of the following ALMA data: ADS/JAO.ALMA #2012.1.00382.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: ALMA 12CO 2-1 calibration, imaging and channel choice
- Missing: Exact continuum windows and spline settings for each JWST line map
- Missing: Custom scripts for warm-pixel masking, column-noise correction and MIRI sub-band scaling
- Missing: Kavanagh et al. in prep for the additional fringe correction
- Data volume (inferred): ALMA part: a single 12CO 2-1 cube (likely a few GB); JWST part: tens of GB of MIRI and NIRSpec uncalibrated and calibrated products from MAST
- Score (inferred): 2/5, JWST reduction is described with pipeline version and context but custom steps are only summarised; the ALMA CO comparison has no processing details, and the main results are mostly morphological
- Rediscovery candidate: no, ALMA plays a minor, qualitative role with no processing recipe, and the main results are largely morphological rather than numeric

## Links

- Method: (cite: bushouse2023) (JWST calibration pipeline used for reduction)
- Method: (cite: vandokkum2001) (LaCosmic algorithm used to flag warm pixels)
- Companion: (cite: zhang2019) (ALMA 12CO 2-1 observations of the HH46 IRS outflow shells used for comparison)
- Companion: (cite: arce2013) (ALMA CO 1-0 outflow observations and cloud velocity adopted for V_LSR)
- Companion: (cite: erkal2021) (HST [Fe II] images of the inner jet used for comparison)
- Related: JWST GO program 1706 (PROJECT-J)
- Related: JWST DDT program 4441

## Checks

```json
{
 "quotes": 61,
 "quotes_ok": 61,
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
  "facts": 78,
  "stated": 34,
  "rate": 0.436
 },
 "evidence_ok": true
}
```
