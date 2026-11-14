# Resolved Images of the Protoplanetary Disk around HD 100546 with ALMA

`2014ApJ...788L..34P` | The Astrophysical Journal Letters 2014 | first author: Pineda, Jaime E. | arXiv: 1405.5773 | DOI: 10.1088/2041-8205/788/2/L34

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks
- Question: What are the resolved morphology, size and kinematics of the dust (870 um) and CO(3-2) gas in the HD 100546 disk, and what do they imply for planet-related processes?  
  > "We present the first resolved images of the disk around HD 100546 obtained in Band 7 with the ALMA observatory." (abstract)
- Target **HD 100546**: coordinates 11h33m25.440581s, -70d11'41.23633" (pointing phase center)  
  > "which is located at a distance of 97$\pm$4 pc (cite: vanLeeuwen_2007-Hipparcos_update)" (Introduction); "Position offset measured with respect to pointing phase center: (11h33m25.440581s, $-$70d11$\ensuremath{'}$41.23633$\ensuremath{''}$)" (Table 1); z/distance 97±4 pc  
  > "which is located at a distance of 97$\pm$4 pc (cite: vanLeeuwen_2007-Hipparcos_update)" (Introduction); "Position offset measured with respect to pointing phase center: (11h33m25.440581s, $-$70d11$\ensuremath{'}$41.23633$\ensuremath{''}$)" (Table 1); distance from van Leeuwen 2007 Hipparcos update  
  > "which is located at a distance of 97$\pm$4 pc (cite: vanLeeuwen_2007-Hipparcos_update)" (Introduction); "Position offset measured with respect to pointing phase center: (11h33m25.440581s, $-$70d11$\ensuremath{'}$41.23633$\ensuremath{''}$)" (Table 1)

## Data provenance

- ALMA projects: 2011.0.00863.S
- bands: Band 7 (870 um continuum, CO 3-2)  
  > "HD 100546 was observed on November 18, 2012 with ALMA using Band 7 receivers under project 2011.0.00863.S." (Data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 21 to 375 m, 24 antennas  
  > "The array configuration included 24 antennas, with baselines between 21 and 375–m." (Data)
- angular resolution: 0.93" x 0.37" (PA=39 deg) continuum; 0.92" x 0.38" (PA=38 deg) CO  
  > "uniform weighting to achieve an angular resolution of 0.93$\ensuremath{''} \times$0.37$\ensuremath{''}$ (PA=39$\ensuremath{^\circ}$)" (Data)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 5.7 mJy/beam; CO rms 27 mJy/beam per channel  
  > "The rms noise is 5.7 mJy beam$^{-1}$, as estimated from emission free regions." (Data); "is 27 mJy beam$^{-1}$ per channel, with a channel width of 0.1058 km s$^{-1}$" (Data)
- time on source: _not stated_
- observing dates: November 18, 2012  
  > "HD 100546 was observed on November 18, 2012 with ALMA using Band 7 receivers" (Data)
- pi or archival as stated: archival Cycle 0  
  > "Here we present an analysis of archival ALMA Cycle 0 observations" (Introduction)
- Line: CO 3-2 (not stated)
- External data: Inner radius fixed at 14 au  
  > "it is not possible to constrain $R_{\rm in}$, and therefore it is fixed at 14 au (cite: quanz2011)" (Results) [from Quanz et al. 2011 (cite: quanz2011)]
- External data: Stellar mass 2.4±0.1 Msun  
  > "M$_*$=2.4$\pm$0.1 M$_\odot$ (cite: vandenAncker_1997-HAeBe_Parameters)" (Results) [from van den Ancker et al. 1997]
- External data: Gas surface density Sigma_gas(r)=18 (r/au) g cm-2  
  > "Using $\Sigma_{gas}(r)$$=$18 $(r/\textrm{au})$ g cm$^{-2}$ (cite: Mulders_2013-HD100546_Companion_Mass)" (Discussion) [from Mulders et al. 2013]
- Simulation/model as data: Modified Mulders et al. 2011 MCMax SED-based radiative transfer model with truncated mm-grain component  
  > "We use a modified version of the model presented in (cite: Mulders_2011-HD100546_Model), using the radiative transfer and disk modeling code MCMax" (Results)

## Processing

### Calibration

- pipeline or manual: standard flagging and calibration in CASA  
  > "The standard flagging and calibration was done using CASA 3.4" (Data)
- casa version: CASA 3.4 calibration; CASA 4.2 imaging  
  > "while imaging was done using CASA 4.2" (Data)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (flux); 3C 279 bandpass; J1147-6753 gain  
  > "The bright quasar 3C 279 is used as bandpass calibrator, while Titan is used to set the flux amplitude." (Data)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: multiscale clean (CO)  
  > "The imaging was done using multiscale clean with uniform weighting" (Data)
- weighting robust: uniform weighting  
  > "imaged using uniform weighting to achieve an angular resolution" (Data)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub; continuum from line-free channels  
  > "The CO (3–2) data cube is obtained from the continuum subtracted visibilities obtained using the task `uvcontsub`." (Data)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.93x0.37 arcsec continuum; 0.92x0.38 arcsec CO  
  > "which produced a beam size of 0.92$\ensuremath{''} \times$0.38$\ensuremath{''}$ (PA=38$\ensuremath{^\circ}$)" (Data)
- final rms: 5.7 mJy/beam continuum; 27 mJy/beam/channel CO  
  > "The rms noise is 5.7 mJy beam$^{-1}$, as estimated from emission free regions." (Data)

### Inherited from earlier work

- Disk model for radiative transfer taken from earlier work and modified  
  > "We use a modified version of the model presented in (cite: Mulders_2011-HD100546_Model)" (Results) [from Mulders et al. 2011 (cite: Mulders_2011-HD100546_Model)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for continuum and uvcontsub
- Clean masks, thresholds, cell and image size
- Self-calibration status
- Rest frequency/spectral windows used
- Details of the truncated-disk visibility fit (binning, weights, fitting method)
- Exact modifications to the Mulders et al. 2011 model and goodness-of-fit criterion
- Phase-center and de-projection details for the visibility plots

## Analysis recipe

1. **Image continuum and CO cube**: Uniform weighting imaging in CASA; uvcontsub and multiscale clean for CO  
  > "The imaging was done using multiscale clean with uniform weighting" (Data)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit continuum geometry**: Elliptical Gaussian fit to visibilities; inclination from axis ratio  
  > "We determine the center, major and minor axes, and disk orientation by fitting an elliptical Gaussian to the visibility data in CASA using the `uvmodelfit` task." (Results)
   - software: CASA uvmodelfit
   - fitting: _not stated_
   - validation: Compared with PA and i of Ardila et al. 2007  
  > "are in agreement with those obtained by (cite: ardila2007), who find PA=145$\ensuremath{^\circ}$$\pm$5$\ensuremath{^\circ}$ and i=42$\ensuremath{^\circ}$$\pm$5$\ensuremath{^\circ}$." (Results)
3. **Fit truncated uniform disk to visibilities**: Truncated disk of uniform surface brightness fit to de-projected visibilities; free F0 and Rout  
  > "we fit the visibilities with a truncated disk of uniform surface brightness." (Results)
   - parameter: R_in fixed at 14 au  
  > "it is fixed at 14 au (cite: quanz2011)" (Results)
   - fitting: _not stated_
   - validation: Authors note Rout uncertainties are underestimated  
  > "therefore the uncertainties for $R_{\textrm{out}}$ are underestimated" (Results)
4. **Compare with radiative transfer models**: MCMax model with 1-3 mm grain component truncated at Rout in a grid 40-100 au in 10 au steps  
  > "Using a grid of models with $R_{\textrm{out}}$ from 40 au up to 100 au and spaced by 10 au the best model is found for 40 au$<$$R_{\textrm{out}}$$<$60 au" (Results)
   - software: MCMax
   - parameter: mm dust mass 5e-4 Msun, 0.1x hydrostatic scale height  
  > "with a dust mass of $5\times 10^{-4}$ M$_\odot$, and 0.1$\times$ the hydrostatic scale height, mimicking dust settling" (Results)
   - fitting: _not stated_
   - validation: _not stated_
5. **CO moments and PV diagram kinematics**: Moment maps and major-axis PV diagram compared with Keplerian curves for M*=2.4 Msun at 40 and 30 deg  
  > "For separations $<$2$\ensuremath{''}$ the velocities are better reproduced with an inclination angle of 30$\ensuremath{^\circ}$" (Results)
   - parameter: moment 0 over -2.1 to 14.0 km/s; moment 1 voxels >3 rms, pixels with integrated intensity >0.4 Jy/beam km/s  
  > "calculated using voxels (volume element) with brightness $>3\times$rms and in pixels with integrated intensity $>0.4$ Jy beam$^{-1}$ km s$^{-1}$" (Results)
   - fitting: _not stated_
   - validation: _not stated_
6. **Stokes number estimate**: St = sqrt(2 pi) rho_s a / Sigma_gas at 50 au  
  > "the Stokes number at 50 au is approximately unity, suggesting that millimeter-sized particles are only marginally coupled to the gas." (Discussion)
   - assumption: rho_s = 1 g cm-3, a = 1 mm  
  > "which we assume to be 1 g cm$^{-3}$ for silicates, $a$$=$1 mm is the particle size" (Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 3.4 (calibration), 4.2 (imaging): calibration, imaging, uvcontsub, uvmodelfit  
  > "The standard flagging and calibration was done using CASA 3.4" (Data)
- **MCMax** : radiative transfer disk modelling  
  > "using the radiative transfer and disk modeling code MCMax" (Results)
- **Astropy** : acknowledged research tool  
  > "This research made use of Astropy, a community-developed core Python package for Astronomy" (Acknowledgments)
- **APLpy** : plotting  
  > "and APLpy, an open-source plotting package for Python" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum total flux | 1.09 | not stated | Jy | 1 | The total and peak flux are 1.09 Jy and 0.500 Jy beam$^{-1}$, respectively. |
| Continuum position angle | 145.14 | 0.04 | deg | 2 | The PA of the major axis (145.14$\ensuremath{^\circ}$$\pm$0.04$\ensuremath{^\circ}$) and inclination angle (41.94$\ensuremath{^\circ}$$\pm$0.03$\ensuremath{^\circ}$), are in agreement |
| Inclination from continuum | 41.94 | 0.03 | deg | 2 | i / 41.94$\ensuremath{^\circ}$$\pm$0.03$\ensuremath{^\circ}$ |
| Gaussian major axis FWHM | 613.2 | 0.1 | mas | 2 | Major axis (FWHM) / (613.2$\pm$0.1)  mas |
| Gaussian integrated flux | 1.2015 | 0.0002 | Jy | 2 | Integrated Flux / (1.2015$\pm$0.0002) Jy |
| Truncated disk outer radius | 45.8 | 0.7 (underestimated) | au | 3 | the total flux is 1.07$\pm$0.02 Jy and the outer radius is 45.8$\pm$0.7 au |
| Truncated disk total flux | 1.07 | 0.02 | Jy | 3 | the total flux is 1.07$\pm$0.02 Jy |
| Visibility null location | 250 | not stated | kλ | 3 | shows a null at $R_{null}$$\approx$250 k$\lambda$ |
| CO disk extent at 3 sigma | 3.5 arcsec (340 au) | not stated | arcsec | 5 | The CO (3–2) emission extends out to 3.5$\ensuremath{''}$ (340 au), where the 3-$\sigma$ level is reached |
| Inner-disk inclination from PV diagram | 30 | not stated | deg | 5 | For separations $<$2$\ensuremath{''}$ the velocities are better reproduced with an inclination angle of 30$\ensuremath{^\circ}$ |

## Qualitative findings

- Dust continuum is asymmetric, with the southeastern side brighter (6-sigma residuals)  
  > "The asymmetric model residuals at the 6-$\sigma$ level (bottom panels in Fig. [1](#fig-cont-data)), with the southeastern side being brighter than the northwestern side" (Discussion)
- CO first-moment map twisted, resembling a warped disk  
  > "a likely explanation is the presence of a warp" (Discussion)

## Claim tuples

- H: Is the mm dust emission as extended as the gas? | E: Visibility fit and radiative transfer comparison of the 870 um continuum versus CO moment maps | R: Dust compact (Rout ~46 au, <60 au) while CO extends to ~350 au | F: mm-sized grains are confined to a truncated disk, consistent with radial drift | **supported**
- H: Is the mm dust azimuthally symmetric? | E: Residuals of the symmetric model | R: 6-sigma asymmetric residuals, SE brighter | F: Underlying dust distribution is asymmetric | **partially**
- H: Does the gas kinematics show non-Keplerian structure or a warp? | E: PV diagram and first moment map | R: Inclination 40 deg outside 2 arcsec, ~30 deg inside; twisted velocity field | F: Possible warp, though unresolved substructure could mimic it | **partially**

## Reasoning

- Why this data: First resolved mm dust and gas images of the disk are not otherwise published  
  > "so far no spatially resolved images of the dust and gas content at (sub)-mm wavelengths have been published" (Introduction)
- Why this method: _not stated_
- Alternative: Infall versus warp for twisted velocity field; warp preferred since twist is seen outside the gap  
  > "since the twist in the first moment map of HD 100546 is also observed outside the annular gap, where infall signatures are not expected, a likely explanation is the presence of a warp" (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Simple model and short baselines; R_in unconstrained; Rout errors underestimated  
  > "Because of the relatively short baselines probed by these ALMA data it is not possible to constrain $R_{\textrm{in}}$" (Results)
- Caveat (inferred, ours): Rout from a uniform-disk fit with fixed inner radius is model dependent
- Caveat (inferred, ours): Resolution of ~0.4-0.9 arcsec barely resolves a ~50 au disk
- Caveat (inferred, ours): Asymmetry and warp claims are tentative
- Caveat (inferred, ours): Stokes number depends on an assumed Sigma_gas and grain size

## Reproducibility

- Data public (paper): Archival ALMA Cycle 0 data, project 2011.0.00863.S  
  > "Here we present an analysis of archival ALMA Cycle 0 observations" (Introduction)
- Products in archive: _not stated_
- Missing: Clean parameters, masks, line-free channels
- Missing: Fitting procedure details for the truncated disk
- Missing: Modified MCMax model parameters
- Data volume (inferred): ~10-30 GB for Cycle 0 Band 7 single execution
- Score (inferred): 6/5, Public data and standard CASA steps with many numeric results, but imaging and model-fit details are sparse.
- Rediscovery candidate: yes, Public data; uvmodelfit and visibility results are numeric and redoable, though imaging details are missing.

## Links

- Method: Mulders et al. 2011 (cite: Mulders_2011-HD100546_Model) (base radiative transfer model)
- Method: Min et al. 2009 (cite: Min_2009-MCMax) (MCMax code)
- Companion: Walsh et al. (in prep) (detailed disk chemistry analysis of same data)

## Checks

```json
{
 "quotes": 65,
 "quotes_ok": 65,
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
  "facts": 78,
  "stated": 45,
  "rate": 0.577
 },
 "evidence_ok": true
}
```
