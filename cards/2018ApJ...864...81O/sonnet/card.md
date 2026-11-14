# Two Different Grain Size Distributions within the Protoplanetary Disk around HD 142527 Revealed by ALMA Polarization Observation

`2018ApJ...864...81O` | The Astrophysical Journal 2018 | first author: Ohashi, Satoshi | arXiv: 1807.10776 | DOI: 10.3847/1538-4357/aad632

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: Which polarization mechanism (magnetic grain alignment, radiative grain alignment, or self-scattering) produces the 0.87 mm polarized emission in different regions of the HD 142527 disk, and what does that imply for grain sizes  
  > "Aiming to observationally identify the polarization mechanisms, we present ALMA polarization observations of the 0.87 mm dust continuum emission toward the circumstellar disk around HD 142527 with high spatial resolution." (abstract)
- Target **HD 142527**: coordinates _not stated_; z/distance 156 ± 7.5 pc  
  > "Here, we adopt the distance measured by *Gaia*, $156\pm7.5$ pc (cite: gai16a; gai16b)." (Introduction); distance from Gaia  
  > "Here, we adopt the distance measured by *Gaia*, $156\pm7.5$ pc (cite: gai16a; gai16b)." (Introduction)

## Data provenance

- ALMA projects: 2015.1.01025.S
- bands: Band 7 (0.87 mm)  
  > "The 0.87 mm ($=870$ $\mu$m) ALMA dust polarization observations were carried out on 2016 March 11 during its Cycle 3 operation and on 2017 May 21 during its Cycle 4 operation." (2 Observations)
- frequencies and spectral setup: 4 spws, 64 channels each, 31.25 MHz channels; centers 336.5, 338.5, 348.5, 350.5 GHz  
  > "The central frequencies in the spws were 336.5, 338.5, 348.5, and 350.5 GHz, respectively." (2 Observations)
- continuum bandwidth: ~7.5 GHz in total  
  > "providing a bandwidth of $\sim7.5$ GHz in total" (2 Observations)
- arrays: _not stated_
- configurations: C36-2/3 (38 antennas) in Cycle 3; C40-5 (45 antennas) in Cycle 4  
  > "The antenna configurations were C36-2/3 with 38 antennas and C40-5 with 45 antennas, respectively." (2 Observations)
- baselines: _not stated_
- angular resolution: 0.27" x 0.24" (~38 x 34 au) for combined data  
  > "The beam size of the final product was $0.27\ensuremath{''}\times0.24\ensuremath{''}$, corresponding to a spatial resolution of $\sim38\times34$ au at the assumed distance of 156 pc." (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: Stokes I rms ~43 uJy/beam; sigma_PI = 2.9e-5 Jy/beam  
  > "a rms of $\sim43$ $\mu$Jy beam$^{-1}$" (3.1 New High Spatial Resolution Data); "The rms noise of the polarized intensity is derived to be $\sigma_{\rm PI}=2.9\times10^{-5}$ Jy beam$^{-1}$." (2 Observations)
- time on source: 73 min (Cycle 3), 80 min (Cycle 4)  
  > "The total integration times for the target were 73 min in Cycle 3 operation and 80 min in Cycle 4 operation." (2 Observations)
- observing dates: 2016 March 11 and 2017 May 21  
  > "carried out on 2016 March 11 during its Cycle 3 operation and on 2017 May 21 during its Cycle 4 operation" (2 Observations)
- pi or archival as stated: _not stated_
- Other facility **ALMA archival CO J=3-2 data**: peak intensity map of CO 3-2 overlaid on continuum, used in appendix for the spiral arm  
  > "Figure [18](#fig8) shows the peak intensity map for the CO $J=3-2$ line overlaid with the continuum emission." (High Spatial Resolution Image and Spiral Arms)
- External data: Disk inclination 27 deg and major-axis position angle 341 deg used to project radial directions  
  > "assuming an inclination of $27^\circ$ and a position angle (the major axis of the disk) of $341^\circ$ (cite: fuk13)" (4.1 Morphology of Polarization Vectors) [from (cite: fuk13)]
- External data: Previous Cycle 3 data (2016 March 11) combined with the new data  
  > "The data taken on 2016 March 11 were previously reported by (cite: kat16)." (2 Observations) [from (cite: kat16)]
- Simulation/model as data: Self-built model of polarization vectors for radiative grain alignment from continuum intensity gradients  
  > "we construct a simple model to discuss the polarization vectors due to grain alignment with radiation gradients." (4.1 Morphology of Polarization Vectors)

## Processing

### Calibration

- pipeline or manual: CASA reduction in a standard manner  
  > "The reduction and calibration of the data were done with CASA version 4.5.3 (cite: mcm07) in a standard manner." (2 Observations)
- casa version: CASA 4.5.3  
  > "CASA version 4.5.3" (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: bandpass J1427-4206, gain J1604-4441, polarization J1512-0905 and J1427-4206  
  > "The bandpass and gain calibrations were performed using observations of J1427-4206 and J1604-4441, respectively, and the polarization calibration was performed using observations of J1512-0905 and J1427-4206." (2 Observations)
- flux scale uncertainty: _not stated_
- self calibration: phase and amplitude self-calibration  
  > "self-calibration for both phase and amplitude was performed." (2 Observations)

### Imaging

- task: tclean  
  > "All images were reconstructed using the CASA task tCLEAN" (2 Observations)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5 (robust = -2 for high-resolution image)  
  > "with Briggs weighting with a robust parameter of 0.5 by combining these data." (2 Observations); "using Briggs weighting with a robust parameter of $-2$" (High Spatial Resolution Image and Spiral Arms)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Cycle 3 and Cycle 4 data combined in uv plane during tclean  
  > "The previous and new data were combined in the uv plane in the tCLEAN process." (2 Observations)
- smoothing: _not stated_
- final beam: 0.27" x 0.24"; 0.15" x 0.13" for robust=-2  
  > "The beam size is $0.15\ensuremath{''}\times0.13\ensuremath{''}$" (High Spatial Resolution Image and Spiral Arms)
- final rms: ~43 uJy/beam (Stokes I); sigma_I = 1.143e-4 for robust=-2 image  
  > "a rms of $\sim43$ $\mu$Jy beam$^{-1}$" (3.1 New High Spatial Resolution Data)

### Inherited from earlier work

- Detailed data reduction description  
  > "A detailed description of the data reduction is given by (cite: nag16)." (2 Observations) [from (cite: nag16)]
- Polarized intensity debiasing method  
  > "We thus debiased the polarized intensity map as described by (cite: vai06) and (cite: hul15)." (2 Observations) [from (cite: vai06), (cite: hul15)]
- Gradient analysis approach for radiative alignment model  
  > "This analysis is similar to that done by (cite: koc12)." (4.1 Morphology of Polarization Vectors) [from (cite: koc12)]

### Not stated but needed to reproduce (our reading)

- Number of tclean iterations, cleaning threshold, masks, cell and image size
- Self-calibration solution intervals and number of rounds
- Continuum channel selection (line-free channels)
- Flux calibrator and flux-scale uncertainty
- How polarization calibration was applied in detail
- Smoothing kernel details for resolution comparison
- Debiasing formula details and the inner-disk Gaussian fitting setup

## Analysis recipe

1. **Calibrate and image Stokes I, Q, U**: CASA calibration, phase+amp self-cal, tclean of combined Cycle 3+4 data  
  > "All images were reconstructed using the CASA task tCLEAN, with Briggs weighting with a robust parameter of 0.5 by combining these data." (2 Observations)
   - software: CASA, tclean
   - parameter: robust = 0.5  
  > "Briggs weighting with a robust parameter of 0.5" (2 Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive polarized intensity, angle and fraction**: PI=sqrt(Q^2+U^2), debiased; polarization angle errors from CASA guide; fraction only above 3 sigma_PI  
  > "The polarization fraction ($P_{\rm frac}=PI/I$) is derived only where the detection is above the threshold 3$\sigma_{\rm PI}$." (2 Observations)
   - software: CASA
   - parameter: sigma_PI = 2.9e-5 Jy/beam  
  > "$\sigma_{\rm PI}=2.9\times10^{-5}$ Jy beam$^{-1}$" (2 Observations)
   - assumption: Stokes V ignored  
  > "we ignore the Stokes *V* component in this study because it has not been well characterized for ALMA" (2 Observations)
   - fitting: _not stated_
   - validation: _not stated_
3. **Compare with previous lower-resolution data**: Smooth Q, U, I of new data to the previous beam and compare polarization-fraction ratios  
  > "Then, we calculate the ratio of the polarization fraction for our high resolution data to that for the previous data." (3.2 Dependence on Spatial Resolution)
   - fitting: _not stated_
   - validation: Ratio ~1 outside the flip region indicates no depolarization  
  > "In the whole region excepting for the part where the flip is found, the ratio is almost unity" (3.2 Dependence on Spatial Resolution)
4. **Test polarization vector morphology against the mechanisms**: Offset between polarization angle and projected radial direction versus PA; model of radiative alignment from continuum intensity gradient rotated by 90 deg  
  > "we calculate the offset angle between the polarization angle and the position angle measured from the central star." (4.1 Morphology of Polarization Vectors)
   - parameter: Pixels above 10 sigma; gradients from the pixel with maximum F_nu r^-2  
  > "First, we find the pixel where $F_{\nu}\times r^{-2}$ is a maximum within the image." (4.1 Morphology of Polarization Vectors)
   - assumption: 0.87 mm radiation field used as proxy for 140 um field; inclination 27 deg, PA 341 deg  
  > "we regard the radiation field of 0.87 mm as the radiation field of $140$ $\mu$m for simplicity." (4.1 Morphology of Polarization Vectors)
   - fitting: _not stated_
   - validation: Model compared with observed vectors  
  > "the model does not match the observed polarization vectors." (4.1 Morphology of Polarization Vectors)
5. **Compare radial profile widths of I and PI**: Gaussian fits to radial profiles at PA = 32, 230, 319 deg  
  > "we perform Gaussian fittings to the radial profiles (Figure [3](#plot1)$-$[5](#plot3)) of the total intensity and polarized intensity" (4.2 Polarization Fraction)
   - fitting: Gaussian fits; northern PI fit excludes r<~120 au or r>~230 au peaks  
  > "we only fit the data outside the local peaks where the radius is $r\lesssim120$ au or $r\gtrsim230$ au" (4.2 Polarization Fraction)
   - validation: _not stated_

## Software

- **CASA** 4.5.3: Data reduction, calibration, tclean imaging  
  > "The reduction and calibration of the data were done with CASA version 4.5.3 (cite: mcm07) in a standard manner." (2 Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total continuum flux | 3.0 | not stated | Jy | 1 | The total flux is derived to be 3.0 Jy |
| Polarization fraction in southern minimum-intensity region | ~15 | not stated | % | 2 | A high polarization fraction of $\sim15$% is found in the minimum intensity region |
| Upper limit on polarization fraction at stellar position | ~2.0 | not stated | % | 2 | We calculate the upper limit of the polarization fraction to be $\sim2.0$% |
| Inner disk peak intensity | 4.4 | not stated | mJy/beam | 1 | with a peak intensity of 4.4 mJy beam$^{-1}$ |
| FWHM of I and PI at PA 32 deg | 73 and 64 | ±1 and ±2 | au | 5 | are $73\pm1$ au and $64\pm2$ au in Figure [3](#plot1) |
| FWHM of I and PI at PA 319 deg | 76 and 68 | ±1 and ±2 | au | 5 | $76\pm1$ au and $68\pm2$ au in Figure [4](#plot2) |
| FWHM of I and PI at PA 230 deg | 76 and 74 | ±1 and ±1 | au | 5 | $76\pm1$ au and $74\pm1$ au in Figure [5](#plot3) |
| Mean polarization angle error | ~2.5 | not stated | deg | 2 | The 1$\sigma$ error of the polarization angle is derived to be $\sim2.5^\circ$ on average. |
| Northeast to southwest intensity contrast (robust=-2 image) | 22:1 | not stated | dimensionless | 1 | The contrast in the intensity reaches a ratio of $22:1$ between the northeast peak and the southwest minimum |

## Qualitative findings

- Polarization vectors flip from radial to azimuthal only in the northern region  
  > "We note that the flip of the polarization vectors appears only in the northern region of the horseshoe structure." (3.1 New High Spatial Resolution Data)
- No compact source found in the cavity, in contrast to Boehler et al. 2017  
  > "However, we find no such source in the cavity." (3.1 New High Spatial Resolution Data)

## Claim tuples

- H: Northern polarization is from self-scattering | E: Compared vector morphology and fraction with theory | R: Sharp 90 deg flip outside the northern ring; fraction depends on resolution at the inner edge | F: Self-scattering is likely in the north | **supported**
- H: Southern polarization is from magnetic grain alignment | E: Offset angle analysis and polarization fraction comparison | R: Radial vectors with ~15% fraction and no flip | F: Toroidal magnetic alignment likely in the south; self-scattering not fully excluded | **partially**
- H: Radiative grain alignment explains the polarization | E: Built a gradient-based model | R: Model does not match the observed vectors in either region | F: Radiative alignment unlikely | **refuted**
- H: Grain size differs between north and south | E: Interpretation of mechanisms with dust trap and vertical structure | R: Small grains (<~100 um) in the south; ~100 um grains in the northern upper layer | F: Two different grain size distributions | **partially**

## Reasoning

- Why this data: Higher resolution than previous data to clarify polarization mechanisms in the whole disk  
  > "Therefore, we aim to clarify the polarization mechanisms in the entire disk with the new higher spatial resolution data." (Introduction)
- Why this method: _not stated_
- Alternative: Radiative grain alignment rejected after model comparison  
  > "Radiative grain alignment is unlikely either in the northern or southern region" (4.4 Polarization in HD 142527)
- Alternative: Mechanical grain alignment not investigated  
  > "In this paper, we do not investigate this mechanism because no polarization model for mechanical grain alignment has been studied in protoplanetary disks." (4.5 Future Prospects)
- How they decided it was enough: _not stated_
- Limitation (authors): Northern peaks optically thick, so midplane grain size is unmeasurable  
  > "The grain size near the middle plane in the northern region cannot be measured because the emission at 0.87 mm is optically thick." (abstract)
- Limitation (authors): Single wavelength cannot separate scattering from alignment  
  > "In the future, we distinguish the polarization caused by scattering from that caused by grain alignment by observing multiple millimeter wavelengths" (4.5 Future Prospects)
- Caveat (inferred, ours): Mechanism assignment is qualitative, with no radiative transfer model fit to the data
- Caveat (inferred, ours): Radiative alignment model uses 0.87 mm as proxy for 140 um
- Caveat (inferred, ours): Grain size conclusions rest on literature theory, not on fits
- Caveat (inferred, ours): Beam smoothing and depolarization may affect the flip location

## Reproducibility

- Data public (paper): ALMA data cited by project code  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.01025.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Self-calibration and tclean parameters
- Missing: Exact smoothing and debiasing implementation
- Missing: Radiative alignment model code
- Missing: Details of the Nagai et al. 2016 reduction
- Data volume (inferred): Tens to ~100 GB for two Band 7 polarization execution blocks
- Score (inferred): 3/5, Data are public and the imaging basics are stated, but self-calibration, masks and the model implementation are missing, and the results are largely qualitative.
- Rediscovery candidate: no, Main conclusions are qualitative interpretations of vector patterns rather than numeric results, and the recipe lacks key settings.

## Links

- Method: (cite: nag16) (Detailed description of the data reduction)
- Method: (cite: vai06) (Polarized intensity debiasing)
- Companion: (cite: kat16) (Earlier lower-resolution polarization data of the same disk, combined here)
- Companion: (cite: cas15) (Multifrequency optical depth study of HD 142527)

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
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 49,
  "rate": 0.636
 },
 "evidence_ok": true
}
```
