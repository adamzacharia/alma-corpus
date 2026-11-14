# Disk-driven rotating bipolar outflow in Orion Source I

`2017NatAs...1E.146H` | Nature Astronomy 2017 | first author: Hirota, Tomoya | arXiv: 1712.04606 | DOI: 10.1038/s41550-017-0146

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Does the bipolar outflow from Orion Source I rotate, and does it trace a magneto-centrifugal disk wind launched from the disk?  
  > "Thus, present results provide a convincing evidence of a rotating outflow directly driven by the magneto-centrifugal disk wind launched by a high-mass YSO candidate" (abstract)
- Target **Orion Source I (Orion KL)**: coordinates RA(J2000)=05h35m14.512s, Decl(J2000)=-05d22'30.57" (tracking center)  
  > "the tracking center position was RA(J2000)=05h35m14.512s, Decl(J2000)=$-$05d22’30.57"" (Methods); "As one of the nearest high-mass star-forming regions (418 pc from the Sun(cite: Kim2008))" (main text); z/distance 418 pc  
  > "the tracking center position was RA(J2000)=05h35m14.512s, Decl(J2000)=$-$05d22’30.57"" (Methods); "As one of the nearest high-mass star-forming regions (418 pc from the Sun(cite: Kim2008))" (main text); distance from Kim2008 (VERA)  
  > "the tracking center position was RA(J2000)=05h35m14.512s, Decl(J2000)=$-$05d22’30.57"" (Methods); "As one of the nearest high-mass star-forming regions (418 pc from the Sun(cite: Kim2008))" (main text)

## Data provenance

- ALMA projects: 2013.1.00048.S
- bands: Band 8 (490 GHz and 460 GHz tunings)  
  > "in the ALMA band 8 were selected for the present paper." (Methods)
- frequencies and spectral setup: 4 spectral windows; 1875 MHz (484 GHz) and 937.5 MHz (463 GHz) total bandwidth; 0.6 and 0.3 km/s channels  
  > "The ALMA correlator provided the four spectral windows with the total bandwidth of 1875 MHz and 937.5 MHz" (Methods)
- continuum bandwidth: _not stated_
- arrays: 12 m antennas, 41 and 40 antennas  
  > "The array consisted of 41 and 40 antennas with a diameter of 12 m each" (Methods)
- configurations: _not stated_
- baselines: max baseline 1466.2 m (484 GHz), 1574.4 m (463 GHz)  
  > "the maximum baseline length of 1466.2 m and 1574.4 m for the 484 GHz and 463 GHz, respectively." (Methods)
- angular resolution: 124x97 mas (484 GHz); 121x104 mas (463 GHz)  
  > "The resultant synthesized beam size were 124 mas$\times$97 mas with the position angle of 73.3 degrees at 484 GHz" (Methods)
- max recoverable scale: _not stated_
- sensitivity: rms 0.048 Jy/beam (Si18O channel), 0.033 Jy/beam (H2O channel)  
  > "The rms noise levels are 0.048 Jy beam$^{-1}$ and 0.033 Jy beam$^{-1}$ for the 484 GHz Si$^{18}$O and 463 GHz H$_{2}$O lines, respectively." (Supplementary Figure 5)
- time on source: 410 s (463 GHz), 315 s (484 GHz)  
  > "was 410 seconds and 315 seconds for 463 GHz and 484 GHz, respectively." (Methods)
- observing dates: July 27 (490 GHz) and August 27 (460 GHz), 2015  
  > "were carried out on July 27 (490 GHz) and August 27 (460 GHz), 2015" (Methods)
- pi or archival as stated: PI observations (cycle 2)  
  > "T.H. led the project as a principal investigator of ALMA observations and performed data analysis." (Author Contributions)
- Line: Si18O J=12-11 (484.056 GHz)
- Line: H2O v2=1, 4(2,2)-3(3,1) (463.171 GHz)
- External data: Distance 418 pc  
  > "418 pc from the Sun(cite: Kim2008)" (main text) [from Kim2008]
- External data: Maser proper-motion 3D outflow velocity of 18 km/s  
  > "which is measured by proper motions of H$_{2}$O masers(cite: Greenhill2013)" (main text) [from Greenhill2013]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Used calibrated data delivered by EA-ARC, then self-calibrated  
  > "We employed the calibrated data delivered by the East-Asia ALMA Regional Center (EA-ARC)." (Methods)
- flux calibrator: J0423-013 (primary flux); bandpass J0522-3627; gain J0607-0834  
  > "A primary flux calibrator, band-pass calibrator, and secondary gain calibrator were J0423$-$013, J0522$-$3627, and J0607$-$0834, respectively." (Methods)
- flux scale uncertainty: _not stated_
- self calibration: Phase and amplitude self-cal on Source I continuum, three of four spectral windows, applied to all channels  
  > "both phase and amplitude self-calibration was done with the continuum emission of Source I by integrating over all the channels using CASA tasks `clean` and `gaincal`." (Methods)

### Imaging

- task: CASA clean  
  > "by using the CASA task `clean` providing velocity channel maps" (Methods)
- deconvolver: _not stated_
- weighting robust: uniform weighting  
  > "The uniform-weighted synthesized images were made for both 484 GHz Si$^{18}$O and 463 GHz H$_{2}$O lines" (Methods)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub with line-free channels  
  > "by setting the line free channels with the CASA task `uvcontsub`." (Methods)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 124x97 mas PA 73.3 deg (484 GHz); 121x104 mas PA 85.2 deg (463 GHz)  
  > "121 mas$\times$104 mas with the position angle of 85.2 degrees at 463 GHz" (Methods)
- final rms: continuum 5 mJy/beam; moment 0 481 (Si18O) and 56 (H2O) mJy/beam km/s  
  > "the rms noise levels are 5 mJy beam$^{-1}$, 481 mJy beam$^{-1}$ km s$^{-1}$, and 56 mJy beam$^{-1}$ km s$^{-1}$" (Figure 1 caption)

### Inherited from earlier work

- 490 GHz continuum image and registration of line maps with continuum  
  > "we used only three spectral windows among four ALMA basebands to make a continuum image at 490 GHz(cite: Hirota2016b)" (Methods) [from Hirota2016b]

### Not stated but needed to reproduce (our reading)

- line-free channel ranges for uvcontsub
- self-calibration solution intervals
- clean parameters (cell, image size, masks, threshold, niter)
- which spectral windows were used for the continuum
- AIPS PV-slice parameters and fitting code
- CASA version
- spectral resolution and velocity frame of cubes

## Analysis recipe

1. **Self-calibrate and image lines**: Continuum split, phase and amplitude self-cal, solutions applied to line data, uniform-weighted clean cubes, moment maps  
  > "The phase and amplitude solutions of self-calibration were applied to all the spectral channels including the target lines by the CASA task `applycal`." (Methods)
   - software: CASA, AIPS
   - fitting: _not stated_
   - validation: _not stated_
2. **Make PV diagrams**: PV slices parallel to the disk midplane at 25 au offsets, 60 mas width  
  > "The width of each slice is 60 mas." (Figure 1 caption)
   - software: AIPS
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit PV diagrams for radii and velocities**: Gaussian fits per velocity channel, then linear (|z|<=50 au) or elliptical (|z|>=50 au) function fits  
  > "we fitted the linear function or elliptical function to the PV diagrams" (Methods)
   - parameter: linear fits use 6 channels (3 km/s) of highest-velocity or outermost FWHM data  
  > "we carried out fitting to use the highest velocity components with the width of 6 channels (3 km s$^{-1}$)" (Methods)
   - fitting: Gaussian, double Gaussian, linear and ellipse fits; 1-sigma errors from fitting, propagated  
  > "All the uncertainties for outflow parameters are estimated by those of the fitting of PV diagrams." (Methods)
   - validation: Both fits applied at z=±50 au for comparison; authors note the fitting is simplified  
  > "For comparison, we applied both fitting procedure at $z$=$\pm$50 au." (Methods)
4. **Derive enclosed mass, centrifugal and launching radii, dynamical time**: Keplerian mass from max rotation velocity at R_in; centrifugal radii from specific angular momentum; launching radii from the Anderson2003 disk-wind model; t_dyn=R_out/v_r  
  > "we can also derive the launching radii of the outflow by using the magneto-centrifugal disk wind model(cite: Anderson2003) (see their equation (4))." (main text)
   - assumption: Keplerian rotation; distance 418 pc  
  > "Assuming Keplerian rotation, the enclosed mass is estimated to be 8.7$\pm$0.6$M_{\odot}$" (main text)
   - fitting: _not stated_
   - validation: Compared with maser-based mass and 3D velocity  
  > "The result is consistent with the mass estimated from SiO maser observations(cite: Matthews2010)." (main text)

## Software

- **CASA** : uvcontsub, clean, gaincal, applycal, immoments  
  > "The synthesis imaging and self-calibration were done with the CASA software package." (Methods)
- **AIPS** : PV diagrams and some analysis/plotting  
  > "We made position-velocity (PV) diagrams by using AIPS in a standard manner." (Methods)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Inner radius R_in(z=0) | 24 | ±8 | au | 3 | $R_{in}$($z$=0)=24$\pm$8 au |
| Outer radius R_out(z=0) | 76 | ±4 | au | 3 | $R_{out}$($z$=0)=76$\pm$4 au |
| Rotation velocity at R_in | 17.9 | ±0.6 | km/s | 3 | $v_{\phi}$($z$=0,$r$=$R_{in}$)=17.9$\pm$0.6 km s$^{-1}$ |
| Rotation velocity at R_out | 7.0 | ±0.4 | km/s | 3 | $v_{\phi}$($z$=0,$r$=$R_{out}$)=7.0$\pm$0.4 km s$^{-1}$ |
| Enclosed mass (Keplerian) | 8.7 | ±0.6 | Msun | 4 | the enclosed mass is estimated to be 8.7$\pm$0.6$M_{\odot}$ (1$\sigma$) |
| Dynamical timescale at z=±150 au | 70 | ±4 | yr | 4 | $t_{dyn}$=$R_{out}/v_{r}$=70$\pm$4 yr (1$\sigma$) at $z$=$\pm$150 au |
| Centrifugal radii | 21-47 | not stated | au | 4 | corresponds to centrifugal radii of 21-47 au |
| Disk-wind launching radii | 5-25 | not stated | au | 4 | The calculated values, 5-25 au, are comparable with or slightly smaller than the centrifugal radii |
| Outward velocity v_z | 10 | not stated | km/s | 4 | the outward velocity along the outflow axis, $v_{z}$, is estimated to be 10 km s$^{-1}$ |
| Maximum opening angle | 70 | not stated | degrees | 3 | has a maximum value of 70 degrees close to the midplane |

## Qualitative findings

- Si18O shows velocity gradients across the outflow axis in both lobes, consistent with the H2O-traced disk rotation  
  > "reveals a velocity gradient perpendicular to the outflow axis which is consistent with that of the circumstellar disk traced by a high-excitation water (H$_{2}$O) line." (abstract)

## Claim tuples

- H: Is the Source I bipolar outflow rotating? | E: Si18O and H2O PV diagrams at offsets from the midplane | R: Velocity gradients perpendicular to the outflow axis in both lobes, similar to the disk | F: The outflow rotates | **supported**
- H: Is the outflow a magneto-centrifugal disk wind rather than entrained jet, stellar wind or X-wind? | E: Derived launching and centrifugal radii and outflow velocity | R: Launching radii >10 au (5-25 au model), v ~10 km/s | F: Disk wind favoured | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: High-excitation thermal lines at high resolution give continuous spatial sampling unlike masers  
  > "These findings are facilitated by utilizing high excitation thermal emission from the H$_{2}$O and Si$^{18}$O lines." (main text)
- Alternative: Precession, warped disk or two unresolved jets for the gradients; rejected for lack of wiggles or velocity mismatches  
  > "Alternative scenarios have also been suggested to explain the observed gradients, such as precessing motion, interaction with a warped disk, or two unresolved jets." (main text)
- How they decided it was enough: _not stated_
- Limitation (authors): Fitting too simplified; radiative transfer modelling needed  
  > "We note that the fitting procedures discussed above are too simplified" (Methods)
- Limitation (authors): Keplerian vs angular-momentum-conserving rotation not distinguished; inner radius and mass may be overestimated  
  > "the PV diagrams could not distinguish Keplerian rotation, $v_{\phi} \propto r^{-0.5}$ due to insufficient resolution." (main text)
- Caveat (inferred, ours): Beam (~50 au) comparable to the slice spacing, so midplane contamination
- Caveat (inferred, ours): Mass depends on assumed Keplerian rotation and inclination (edge-on)
- Caveat (inferred, ours): Fit errors only; no systematic uncertainty or model comparison

## Reproducibility

- Data public (paper): Data available from corresponding author on request; project code given  
  > "are available from the corresponding author upon reasonable request." (Data availability)
- Products in archive: _not stated_
- Missing: self-cal and clean parameters
- Missing: line-free channels
- Missing: PV fitting code and AIPS settings
- Data volume (inferred): ~50-100 GB
- Score (inferred): 3/5, Data code given and fitting approach described, but many imaging and fitting parameters are missing.
- Rediscovery candidate: no, Recipe lacks key imaging and fitting details.

## Links

- Method: Hirota2016b (Band 8 continuum image and self-calibration approach)
- Companion: Hirota2014 (Earlier ALMA hot disk observations of Source I)

## Checks

```json
{
 "quotes": 60,
 "quotes_ok": 60,
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
  "facts": 66,
  "stated": 41,
  "rate": 0.621
 },
 "evidence_ok": true
}
```
