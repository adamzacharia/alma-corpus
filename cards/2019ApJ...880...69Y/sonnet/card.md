# HL Tau Disk in HCO<SUP>+</SUP> (3-2) and (1-0) with ALMA: Gas Density, Temperature, Gap, and One-arm Spiral

`2019ApJ...880...69Y` | The Astrophysical Journal 2019 | first author: Yen, Hsi-Wei | arXiv: 1906.05535 | DOI: 10.3847/1538-4357/ab29f8

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: Does the HL Tau disk show HCO+ gas gaps coincident with the dust gaps, and what are the gas kinematics, density, temperature and surrounding spiral structure?  
  > "Therefore, the presence or absence of the HCO$^+$ gas gaps in the HL Tau disk is still uncertain." (1 Introduction)
- Target **HL Tau**: coordinates 04h31m38.428s +18d13m57.19s (2017 continuum peak)  
  > "The peak position of the 1.1 mm continuum emission is measured to be 04$^{\rm h}$31$^{\rm m}$38.428s +18$\ensuremath{^\circ}$13$\ensuremath{'}$57.19$''$ with our observations in 2017." (1.1 mm continuum); "located in the northern part of the L1551 region in the Taurus molecular cloud at a distance of $\sim$140 pc (cite: Hayashi09; Galli18)" (Introduction); z/distance ~140 pc  
  > "The peak position of the 1.1 mm continuum emission is measured to be 04$^{\rm h}$31$^{\rm m}$38.428s +18$\ensuremath{^\circ}$13$\ensuremath{'}$57.19$''$ with our observations in 2017." (1.1 mm continuum); "located in the northern part of the L1551 region in the Taurus molecular cloud at a distance of $\sim$140 pc (cite: Hayashi09; Galli18)" (Introduction); distance from Hayashi09; Galli18  
  > "The peak position of the 1.1 mm continuum emission is measured to be 04$^{\rm h}$31$^{\rm m}$38.428s +18$\ensuremath{^\circ}$13$\ensuremath{'}$57.19$''$ with our observations in 2017." (1.1 mm continuum); "located in the northern part of the L1551 region in the Taurus molecular cloud at a distance of $\sim$140 pc (cite: Hayashi09; Galli18)" (Introduction)

## Data provenance

- ALMA projects: 2011.0.00015.SV, 2016.1.00366.S
- bands: _not stated_
- frequencies and spectral setup: seven spectral windows; two 2 GHz continuum windows; 59 MHz HCO+ (3-2) window with 61 kHz native resolution  
  > "The spectral setup consists of seven spectral windows. Two spectral windows with a bandwidth of 2 GHz each were assigned to the continuum emission." (1.1 mm observation)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C40-7  
  > "The array configuration was C40-7." (1.1 mm observation)
- baselines: max projected baseline ~3.3 km  
  > "The maximum projected baseline length of the observations is $\sim$3.3 km." (1.1 mm observation)
- angular resolution: ~0.1"  
  > "at angular resolutions of 0.1$''$" (abstract)
- max recoverable scale: _not stated_
- sensitivity: 30 uJy/beam (1.1 mm continuum); 2.5 mJy/beam per channel (HCO+ 3-2)  
  > "The achieved noise level is 30 $\mu$Jy beam$^{-1}$ in the 1.1 mm continuum image, and 2.5 mJy beam$^{-1}$ per channel in the HCO$^+$ (3–2) images." (1.1 mm observation)
- time on source: _not stated_
- observing dates: 1.1 mm: 2017 August 22, 28 and September 1  
  > "The ALMA observations at 1.1 mm of HL Tau were executed on 2017 August 22 and 28 and September 1." (1.1 mm observation)
- pi or archival as stated: _not stated_
- Line: HCO+ 3-2 (267.557633 GHz)
- Line: HCO+ 1-0 (89.188526 GHz)
- External data: Dust temperature profile T_d = 310 (R/1 au)^-0.57 K  
  > "$T_{\rm d} = 310 \times (R/1\ {\rm au})^{-0.57}$ K" (4.2 HCO+ density and temperature profiles) [from Okuzumi16]
- External data: Disk PA 138 deg and inclination 47 deg from 0.03" continuum  
  > "we fixed the position angle of the disk major axis and the disk inclination angle at 138$\ensuremath{^\circ}$ and 47$\ensuremath{^\circ}$, respectively" (4.1 Stellar mass and systemic velocity) [from ALMA15]
- External data: 2.9 mm continuum image and HCO+ (1-0) calibrated visibilities from the ALMA science verification archive  
  > "The 2.9 mm continuum image analyzed in this work was directly obtained from the archive." (2.9 mm observation) [from ALMA15]

## Processing

### Calibration

- pipeline or manual: CASA pipeline with archive script including additional manual flagging  
  > "The calibration script obtained from the archive includes additional manual flagging to remove the data of several antennas showing phase jumps." (1.1 mm observation)
- casa version: 4.7.0  
  > "of version 4.7.0" (1.1 mm observation)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0423-0120 (Aug 22); J0510+1800 (Aug 28, Sep 1)  
  > "J0237+2848, J0423$-$0120, and J0431+1731 were observed as bandpass, flux, and phase calibrators, respectively." (1.1 mm observation)
- flux scale uncertainty: 5-10%  
  > "uncertainty of an absolution flux calibration of 5–10%" (4.2 HCO+ density and temperature profiles)
- self calibration: phase self-cal on continuum, applied to line data  
  > "We further performed self-calibration on the phase with the continuum data, and applied the solution to the molecular-line data." (1.1 mm observation)

### Imaging

- task: tclean  
  > "and cleaned the images, using the CASA task *tclean*." (1.1 mm observation)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5 (1.1 mm); robust = 0 for HCO+ (1-0)  
  > "Briggs weighting with a robust parameter of 0.5" (1.1 mm observation); "The Briggs weighting with a robust parameter of 0 and without *uv* tapering was adopted" (2.9 mm observation)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub  
  > "The continuum subtraction was performed using the CASA task *uvcontsub*." (1.1 mm observation)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: 1.1 mm and 2.9 mm continuum and HCO+ (1-0) convolved to 0.1"x0.09", PA 19 deg  
  > "We convolved the 1.1 mm and 2.9 mm continuum images and the HCO$^+$ (1–0) image cube to a beam size of $0.1\ensuremath{''} \times 0.09\ensuremath{''}$" (4.2 HCO+ density and temperature profiles)
- final beam: 1.1 mm cont 0.09"x0.09" PA 19; HCO+ (3-2) 0.1"x0.09" PA 19  
  > "The sizes of the synthesized beams of the 1.1 mm continuum and HCO$^+$ (3–2) images are 0.09$''$ $\times$ 0.09$''$ and 0.1$''$ $\times$ 0.09$''$, respectively." (1.1 mm observation)
- final rms: 30 uJy/beam continuum; 2.5 mJy/beam per channel  
  > "The achieved noise level is 30 $\mu$Jy beam$^{-1}$ in the 1.1 mm continuum image" (1.1 mm observation)

### Inherited from earlier work

- Velocity-aligned stacking method for M_star and V_sys  
  > "we adopt the velocity-aligned stacking method introduced in (cite: Yen16b; Yen18) to measure $M_\star$ and $V_{\rm sys}$." (4.1 Stellar mass and systemic velocity) [from Yen16b; Yen18]
- Masking of absorption regions  
  > "we follow the procedure in (cite: Yen16a) to mask the regions showing negative intensity in the velocity channel maps." (4.1 Stellar mass and systemic velocity) [from Yen16a]
- 2.9 mm data reduction and imaging  
  > "The details of the observations and the data reduction are described in (cite: ALMA15)." (2.9 mm observation) [from ALMA15]
- Column density calculation of tau_g  
  > "The calculation of $\tau_{\rm g}$ is explained in detail in (cite: Mangum15)." (4.2 HCO+ density and temperature profiles) [from Mangum15]
- Planet mass from gap depth  
  > "using the formula in (cite: Kanagawa15)" (5.1 Gap opened by a planet?) [from Kanagawa15]

### Not stated but needed to reproduce (our reading)

- Self-calibration solution intervals and number of iterations
- Line-free channels for uvcontsub and fit order
- tclean cell size, image size, masks and clean threshold
- Exact radial bin centers and the numeric inputs for each bin
- Details of the absorption masks per radial bin
- Keplerian masking parameters for the HCO+ (1-0) moment map
- Spiral peak positions used in the fit
- Uncertainties on the fitted infall and rotation parameters

## Analysis recipe

1. **Calibrate and image 1.1 mm continuum and HCO+ (3-2)**: CASA pipeline plus manual flagging, phase self-cal, tclean with Briggs weighting, uvcontsub for continuum-subtracted cube  
  > "We generated images from the calibrated visibilities with the Briggs weighting with a robust parameter of 0.5" (1.1 mm observation)
   - software: CASA
   - parameter: channel width 0.1 km/s  
  > "The HCO$^+$ (3–2) images were generated with a channel width of 0.1 km s$^{-1}$" (1.1 mm observation)
   - fitting: _not stated_
   - validation: 1.1 mm flux compared with interpolated ALMA15 values, consistent within 10%  
  > "which is consistent with our observational measurement at 1.1 mm within 10%" (1.1 mm continuum)
2. **Measure stellar mass and systemic velocity**: Search for the Keplerian velocity pattern maximizing the S/N of the velocity-aligned stacked spectra, with absorption channels masked and only the blueshifted region (PA 48-228 deg) used  
  > "$M_\star$ and $V_{\rm sys}$ can be estimated by searching for a velocity pattern of Keplerian rotation that maximizes the S/N of the velocity-aligned stacked spectra" (Analysis, Stellar mass and systemic velocity)
   - parameter: free parameters M_star, V_sys; PA 138 deg, i 47 deg fixed  
  > "The free parameters in the analysis are $M_\star$ and $V_{\rm sys}$." (4.1 Stellar mass and systemic velocity)
   - assumption: geometrically thin disk  
  > "The velocity patterns of Keplerian rotation were computed with the assumption of a geometrically thin disk." (4.1 Stellar mass and systemic velocity)
   - fitting: S/N maximization of velocity-aligned stacked spectra; uncertainty from data noise only  
  > "These estimated uncertainties in $M_\star$ and $V_{\rm sys}$ only include the uncertainty due to the noise in the data." (4.1 Stellar mass and systemic velocity)
   - validation: Compared with previous 1.8 Msun from 13CO/C18O PV diagram; added a few percent for emitting height  
  > "we estimate $M_\star$ to be 2.1$\pm$0.2 $M_\odot$." (4.1 Stellar mass and systemic velocity)
3. **Radial profiles of HCO+ (3-2) and (3-2)/(1-0) intensity ratio**: Velocity-aligned stacked spectra in radial bins, Gaussian fits to (3-2), integrate both lines within 1 sigma line width, ratio in K km/s  
  > "we integrated the velocity-aligned stacked spectra of the HCO$^+$ (3–2) and (1–0) emission over the channels within the 1$\sigma$ Gaussian line width from the centroid velocity" (4.2 HCO+ density and temperature profiles)
   - parameter: radial bin width 0.05"; innermost radius = beam 0.1" (14 au)  
  > "The radius of the innermost bin is adopted to be the beam size of 0.1$''$ (14 au)" (4.2 HCO+ density and temperature profiles)
   - assumption: (3-2) and (1-0) trace the same volume; ratio constant within each bin  
  > "we assume that the HCO$^+$ (3–2) and (1–0) emission lines trace the same volume in the HL Tau disk" (4.2 HCO+ density and temperature profiles)
   - fitting: Gaussian fits  
  > "For each radial bin, we fitted a Gaussian line profile to the velocity-aligned stacked spectrum of the HCO$^+$ (3–2) emission." (Analysis, HCO$^+$ density and temperature profiles)
   - validation: _not stated_
4. **Derive continuum optical depths**: tau_d = -ln(1 - I/(B(Td)-B(Tbg))) using azimuthally averaged continuum profiles at 1.1 and 2.9 mm  
  > "Then we derived the radial profiles of the optical depths of the continuum emission ($\tau_{\rm d}$) with the radiative transfer equation" (4.2 HCO+ density and temperature profiles)
   - assumption: T_d from Okuzumi16; T_bg 2.73 K  
  > "cosmic microwave background temperature of 2.73 K" (4.2 HCO+ density and temperature profiles)
   - fitting: _not stated_
   - validation: _not stated_
5. **Solve for HCO+ column density and Tex per radial bin**: Three-layer radiative transfer model (dust midplane, HCO+ above and below) solved for (3-2) and (1-0) intensities  
  > "We adopt a simple three-layer model of the dust and HCO$^+$ gas distributions to correct the effect of the dust opacity on the line intensity" (4.2 HCO+ density and temperature profiles)
   - software: MPFIT
   - parameter: unknowns: column density and Tex; same Tex for both lines  
  > "For each radial bin, there are two unknowns, the column density and $T_{\rm ex}$ of HCO$^+$" (4.2 HCO+ density and temperature profiles)
   - assumption: Tex equal for both lines (RADEX thermalized for n_H2>1e8 cm-3, 20-60 K); geometrically thin  
  > "HCO$^+$ is thermalized when the H$_2$ number density is higher than 10$^8$ cm$^{-3}$ at a temperature of 20–60 K" (4.2 HCO+ density and temperature profiles)
   - fitting: MPFIT minimization; solutions exactly reproduce observed intensities  
  > "For all radial bins, the solutions, which exactly reproduce the observed intensities, were successfully obtained" (4.2 HCO+ density and temperature profiles)
   - validation: _not stated_
6. **Gap depth and profile fits**: Gap depth = column density in gap over power-law interpolation from 17 and 37 au; fit self-similar accretion disk profile; power-law Tex fit  
  > "the depth of this HCO$^+$ gas gap is estimated to be 4–8" (4.2 HCO+ density and temperature profiles)
   - assumption: constant HCO+ abundance between 17 and 37 au  
  > "Assuming that the HCO$^+$ abundance is constant at radii between 17 au and 37 au" (4.2 HCO+ density and temperature profiles)
   - fitting: self-similar solution; points between 20 and 35 au excluded  
  > "Excluding the data points at radii between 20 au and 35 au, which belong to the inner gap" (4.2 HCO+ density and temperature profiles)
   - validation: _not stated_
7. **Spiral morphology and kinematics**: Peak positions in moment 0 fit with piecewise polynomials; PV diagram along spiral fitted with infall plus rotation model with q = -1  
  > "We assume that the rotation of the spiral structure has a conserved angular momentum, meaning that $q = -1$." (4.3 kinematics of the one-arm spiral)
   - assumption: spiral lies in the disk mid-plane  
  > "we assume that the spiral structure is in the mid-plane of the disk" (4.3 kinematics of the one-arm spiral)
   - fitting: direct fit to local peaks in PV diagram  
  > "We fitted Eq. [\[vspiral\]](#vspiral) to the representative data points from the P–V diagram" (Analysis, kinematics of the one-arm spiral)
   - validation: _not stated_
8. **Planet mass from gap depth**: Kanagawa15 formula with depth 4-8, M_star 2.1 Msun, T 60 K, alpha 1e-3  
  > "a gas temperature of 60 K, and a viscosity $\alpha$ of 10$^{-3}$" (5.1 Gap opened by a planet?)
   - assumption: vertically isothermal disk  
  > "We note that the formula of planet mass and gap depth in (cite: Kanagawa15) is derived for vertically isothermal disks." (Discussion, Gap opened by a planet?)
   - fitting: _not stated_
   - validation: compared with planet masses in simulations rescaled by stellar mass  
  > "we linearly scaled the mass of planets in these simulations by the ratio of their adopted and our measured stellar masses." (Footnote 3)

## Software

- **CASA** 4.7.0: calibration, tclean imaging, uvcontsub  
  > "The data were calibrated with the pipeline of the software Common Astronomy Software Applications (cite: McMullin07) of version 4.7.0." (1.1 observation)
- **MPFIT** : minimization for column density and Tex  
  > "we used the IDL routine *MPFIT* (cite: Markwardt09) for the minimization" (4.2 HCO+ density and temperature profiles)
- **RADEX** : check that HCO+ is thermalized  
  > "non-LTE radiative calculations using RADEX (cite: radex07)" (4.2 HCO+ density and temperature profiles)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Stellar mass | 2.1 | 0.2 | Msun | 2 | the stellar mass is estimated to be 2.1$\pm$0.2 $M_\ensuremath{\odot}$ with a disk inclination angle of 47$\ensuremath{^\circ}$ |
| Systemic velocity V_LSR | 7.14 | 0.03 | km/s | 2 | $V_{\rm LSR}$ of 7.14$\pm$0.03 km s$^{-1}$ |
| HCO+ column density at 30 au | 1.7e14 | 0.4e14 | cm^-2 | 5 | The estimated column density at a radius of 30 au is $(1.7\pm0.4) \times 10^{14}$ cm$^{-2}$. |
| HCO+ gap depth at 30 au | 4-8 | not stated | dimensionless | 6 | the depth of this HCO$^+$ gas gap is estimated to be 4–8 |
| Tex power-law profile | 256 (R/1 au)^-0.48 for 15<R<140 au | not stated | K | 6 | $256\cdot(R/{\rm 1\ au})^{-0.48}$ K for $15 < R < 140$ au |
| Gas mass times X(HCO+) | 4.4e-12 | not stated | Msun / X(HCO+) | 6 | the gas mass of the HL Tau disk is estimated to be $4.4 \times 10^{-12}/X({\rm HCO^+})$ $M_\ensuremath{\odot}$ |
| Planet mass opening the 30 au gap | 0.5-0.8 | not stated | MJ | 8 | the planet mass is estimated to be 0.5–0.8 $M_{\rm J}$ from the gap depth of 4–8 |
| 1.1 mm disk flux | 894.4 | 0.4 | mJy | 1 | The 1.1 mm flux of the disk is measured to be 894.4$\pm$0.4 mJy. |
| Spiral fit parameters | V_in,0 = -2.2, p = -0.16, V_rot,0 = 3.6 | not stated | km/s | 7 | we obtained $V_{\rm in,0}$ of $-2.2$ km s$^{-1}$, $p$ of $-0.16$, and $V_{\rm rot,0}$ of 3.6 km s$^{-1}$ |

## Qualitative findings

- HCO+ (3-2) is optically thick (tau 2.5 to >10) except in the inner gap where tau is near 1  
  > "the HCO$^+$ (3–2) line is optically thick with $\tau_{\rm g}$ ranging from 2.5 to $>$10 at the peak velocity" (4.2 HCO+ density and temperature profiles)

## Claim tuples

- H: Is there an HCO+ gas gap coincident with the dust gap at 30 au? | E: LTE analysis of HCO+ (3-2) and (1-0) with continuum opacity correction | R: Column density drops by 4-8 at 30 au; no other clear gap | F: HCO+ gas gap coincident with the dust gap at 30 au | **supported**
- H: What is the stellar mass from the resolved Keplerian rotation? | E: Velocity-aligned stacking in the blueshifted region | R: M_star 2.1+-0.2 Msun at i=47 deg | F: Disk in Keplerian rotation around a 2.1 Msun star | **supported**
- H: Could a planet open the 30 au HCO+ gap? | E: Kanagawa15 formula using gap depth, Tex and alpha | R: 0.5-0.8 MJ, comparable to simulation masses | F: Planet-opened gap is plausible, but chemical effects such as UV excess are not excluded | **partially**
- H: Is the one-arm spiral infalling? | E: PV along the spiral compared with Keplerian rotation and infall plus rotation model | R: Spiral more redshifted than Keplerian beyond 0.3" | F: Infalling and rotating gas stream toward inner disk | **supported**

## Reasoning

- Why this data: HCO+ (3-2) is brighter than (1-0) and adding it allows Tex and column density to be derived  
  > "Thus, observations in the HCO$^+$ (3–2) line can have better S/N." (1 Introduction)
- Why this method: Asymmetric emission prevents a kinematic model fit, so stacking was used  
  > "it is not straightforward to construct a kinematical model to fit the observed velocity channel maps." (4.1 Stellar mass and systemic velocity)
- Alternative: CO depletion, ionization rate enhancement and free-fall of a clump rejected for the gap and spiral  
  > "Thus, the presence of the HCO$^+$ gas gap at a radius of 30 au in the HL Tau disk is not caused by the CO depletion." (5.1 Gap formed by chemical effects?)
- How they decided it was enough: _not stated_
- Limitation (authors): Spiral velocities depend on the assumed mid-plane location and conserved angular momentum  
  > "If the spiral structure is not in the disk mid-plane or the angular momentum is not conserved, the derived profiles of the infalling and rotational velocities are not valid." (4.3 kinematics of the one-arm spiral)
- Limitation (authors): Inner-radius line width overestimated, so column density, Tex and tau at the inner radius may be underestimated  
  > "the column density, $T_{\rm ex}$, and $\tau_{\rm g}$ at the inner radius can be underestimated." (4.2 HCO+ density and temperature profiles)
- Caveat (inferred, ours): Gap depth depends on the assumed constant HCO+ abundance and the three-layer geometry
- Caveat (inferred, ours): Planet mass relies on a vertically isothermal formula and an assumed alpha
- Caveat (inferred, ours): Uncertainties on stellar mass are only noise-based plus an ad hoc few percent
- Caveat (inferred, ours): Stacked HCO+ (1-0) S/N is low and its profile is derived from the ratio

## Reproducibility

- Data public (paper): 2.9 mm data from the public ALMA SV archive; 1.1 mm project 2016.1.00366.S listed in acknowledgements  
  > "ADS/JAO.ALMA#2016.1.00366.S and ADS/JAO.ALMA#2011.0.00015.SV" (Acknowledgements)
- Products in archive: _not stated_
- Missing: Self-calibration parameters
- Missing: Imaging cell and image size, masks and thresholds
- Missing: Line-free channels
- Missing: Stacking and bin implementation details
- Data volume (inferred): ~100-300 GB (three Band 6 executions plus SV Band 3 data)
- Score (inferred): 3/5, Data are public and methods largely described, but imaging and stacking details are not fully given and no code is released.
- Rediscovery candidate: no, Recipe lacks key imaging and self-calibration parameters and relies on custom stacking code from earlier papers.

## Links

- Method: Yen16b; Yen18 (velocity-aligned stacking method)
- Method: Mangum15 (column density and optical depth formalism)
- Method: Kanagawa15 (planet mass from gap depth)
- Companion: Yen16a (earlier HCO+ (1-0) analysis of HL Tau gas gaps)
- Companion: ALMA15 (2.9 mm SV data and continuum rings and gaps)
- Related: ALMA science verification 2011.0.00015.SV

## Checks

```json
{
 "quotes": 88,
 "quotes_ok": 88,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 93,
  "stated": 66,
  "rate": 0.71
 },
 "evidence_ok": true
}
```
