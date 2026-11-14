# ALMA imaging of SDP.81 - I. A pixelated reconstruction of the far-infrared continuum emission.

`2015MNRAS.451L..40R` | Monthly Notices of the Royal Astronomical Society 2015 | first author: Rybak, M. | arXiv: 1503.02025 | DOI: 10.1093/mnrasl/slv058

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What is the pixelated source-plane structure, magnification and star-formation rate density of the lensed starburst SDP.81 from ALMA 1 and 1.3 mm continuum visibilities?  
  > "We determine the structure of the background source by applying a Bayesian pixellated visibility-fitting lens modelling technique (cite: rybak15)." (1 Introduction)
- Target **SDP.81 (H-ATLAS J090311.6+003906)**: coordinates H-ATLAS J090311.6+003906  
  > "SDP.81 (H-ATLAS J090311.6+003906; $z =$ 3.042 $\pm$ 0.001;" (1 Introduction); z/distance z = 3.042 ± 0.001  
  > "SDP.81 (H-ATLAS J090311.6+003906; $z =$ 3.042 $\pm$ 0.001;" (1 Introduction); distance from literature (Negrello2010; Frayer2011; Bussmann2013; Dye14; Negrello14)  
  > "SDP.81 (H-ATLAS J090311.6+003906; $z =$ 3.042 $\pm$ 0.001;" (1 Introduction)

## Data provenance

- ALMA projects: 2011.0.00016.SV
- bands: Bands 6 and 7 used (Bands 4, 6, 7 observed); 236 and 290 GHz  
  > "In this letter, we only consider the datasets taken in Bands 6 and 7 since they have the highest continuum signal-to-noise ratio." (2 ALMA continuum imaging)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: 2 spectral windows of 2 GHz each per band, 128 channels  
  > "The Band 6 and 7 continuum datasets were each taken using 2 spectral windows of 2 GHz total-bandwidth and with 128 channels in each of the linear polarisations" (2 ALMA continuum imaging)
- arrays: _not stated_
- configurations: _not stated_
- baselines: ~15 m to 15 km  
  > "baseline lengths from $\sim$15 m to 15 km, with 10 per cent of the baselines shorter than 200 m" (2 ALMA continuum imaging)
- angular resolution: 95 x 71 mas, PA 64.5 deg (<=2 Mλ, 236 GHz)  
  > "the synthesised beam-size of the $\le$ 2 M$\lambda$ dataset was 95 $\times$ 71 mas at a position angle of 64.5 deg east of north (at 236 GHz)" (2 ALMA continuum imaging)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 4.4 h (Band 6), 5.6 h (Band 7)  
  > "The total time on-source was 4.4 and 5.6 h for the Band 6 and 7 observations, respectively." (2 ALMA continuum imaging)
- observing dates: 2014 October and November  
  > "was taken over several observing blocks during 2014 October and November" (2 ALMA continuum imaging)
- pi or archival as stated: _not stated_
- External data: UV/optical-to-sub-mm broad-band SED fit used to derive intrinsic SFR, LFIR and dust mass  
  > "from a fit to the UV/optical-to-sub-mm broad-band spectrum that was carried out by (cite: Negrello14)" (4 The intrinsic source properties of SDP.81) [from (cite: Negrello14)]
- External data: Modified black body dust model (TD = 34 K, beta = 1.5) for expected flux ratio  
  > "temperature $T_{\rm D} =$ 34 $\pm$ 1 K and emissivity $\beta =$ 1.5; (cite: Bussmann2012)" (4 The intrinsic source properties of SDP.81) [from (cite: Bussmann2012)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Refers to ALMA Partnership 2015 for observation and data processing; no re-calibration described  
  > "We refer to the ALMA partnership (2015) for more details about the observations and data processing." (2 ALMA continuum imaging)
- flux calibrator: _not stated_
- flux scale uncertainty: 10 per cent assumed  
  > "assuming a 10 percent uncertainty in the flux-density calibration" (2 ALMA continuum imaging)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0  
  > "With a Briggs weighting scheme (robust $= 0$)" (2 ALMA continuum imaging)
- uv taper: No taper; hard uv-cut at <=2 Mλ used for lens modelling  
  > "a cut was used instead of a *uv*-taper because this limited the number of visibilities needed" (2 ALMA continuum imaging)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Each spectral window averaged to one channel, 20 s time averaging  
  > "we therefore averaged each spectral window to a single channel and used a visibility averaging time of 20 s" (2 ALMA continuum imaging)
- final beam: 95 x 71 mas, PA 64.5 deg  
  > "95 $\times$ 71 mas at a position angle of 64.5 deg east of north" (2 ALMA continuum imaging)
- final rms: _not stated_

### Inherited from earlier work

- Bayesian pixelated visibility-fitting lens modelling method  
  > "we use the Bayesian visibility-fitting method of (cite: rybak15)" (3 Gravitational lens mass modelling) [from (cite: rybak15)]
- Observation details and data processing  
  > "We refer to the ALMA partnership (2015) for more details about the observations and data processing." (2 ALMA continuum imaging) [from ALMA Partnership; Vlahakis et al. 2015]
- Gravitational imaging technique with Delaunay source grid  
  > "This method extends the gravitational imaging technique introduced by (cite: Vegetti09) to interferometric data." (3 Gravitational lens mass modelling) [from (cite: Vegetti09)]

### Not stated but needed to reproduce (our reading)

- Regularisation strength / evidence optimisation details and priors on lens parameters
- Source-grid pixel number and resolution
- Which calibrated products/scripts were used and CASA version
- How the 28 per cent flux offset in Band 6 spw0 was corrected
- Conversion from far-IR luminosity to SFR (calibration) and how SFR density map was scaled
- Rybak et al. 2015 method paper was in preparation
- Image-plane imaging parameters (cell, size)
- Software implementation not named or released

## Analysis recipe

1. **Data selection and averaging**: Drop noisy final Band 6 block, correct 28% flux offset in spw0, average spws to single channel and 20 s, cut uv at <=2 Mλ  
  > "this observing block was removed from the dataset" (2 ALMA continuum imaging)
   - parameter: uv cut <=2 Mλ, ~1.1-1.5e5 visibilities per spw  
  > "about 1.1–1.5 $\times$ 10$^5$ visibilities per spectral window" (2 ALMA continuum imaging)
   - fitting: _not stated_
   - validation: _not stated_
2. **Lens mass model and pixelated source reconstruction**: Bayesian visibility-space fit with Delaunay-tessellated source grid, gradient regularisation, elliptical power-law mass plus external shear; each spw reconstructed separately then averaged  
  > "The modelling method optimises the Bayesian evidence by minimising a combination of the $\chi^2$ measured in the visibility space and a regularisation performed on the source plane grid." (3 Gravitational lens mass modelling)
   - parameter: Gradient regularisation  
  > "we adopt the gradient rather than the curvature regularisation to prevent the source from being overly smoothed" (3 Gravitational lens mass modelling)
   - fitting: Maximum a posteriori; noise per baseline from rms of visibilities within an observing block  
  > "We estimate the noise level for each baseline at a given time and frequency by calculating the rms of the visibilities measured within the same observing block" (3 Gravitational lens mass modelling)
   - validation: Visibility residuals consistent with Gaussian noise; consistency between spws and bands; error from rms scatter between spws  
  > "4.7 and 0.3 percent of the visibilities are out with the 2- and 3-$\sigma$ levels, respectively" (3 Gravitational lens mass modelling)
3. **Magnification and intrinsic properties**: Magnification as ratio of source-plane to image-plane emission; scale SED-derived properties of Negrello14 by it  
  > "We estimate the lensing magnification $\mu$ of the source by calculating the ratio of the reconstructed emission in the source-plane and image-plane." (4 The intrinsic source properties of SDP.81)
   - assumption: Only far-infrared part of the SED considered, where magnification is valid  
  > "we only consider the properties derived from the far-infrared part of the spectrum" (4 The intrinsic source properties of SDP.81)
   - fitting: _not stated_
   - validation: _not stated_
4. **SFR density map and spectral slope**: SFR density from reconstructed map assuming all dust heating is star formation; flux ratios 230/290 GHz per clump  
  > "under the assumption that all the heated dust emission is solely due to star formation" (4 The intrinsic source properties of SDP.81)
   - fitting: _not stated_
   - validation: Uncertainty from rms over all spectral channels  
  > "which was calculated from the rms over all spectral channels" (4 The intrinsic source properties of SDP.81)

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total magnification | 17.6 | 0.4 | dimensionless | 3 | The total magnification is found to be $\mu_{\rm tot} =$ 17.6 $\pm$ 0.4. |
| Star-forming disk magnification | 25.2 | 2.6 | dimensionless | 3 | $\mu_{\rm SF~disk} =$ 25.2 $\pm$ 2.6 |
| Intrinsic SFR | 315 | 60 | Msun/yr | 3 | giving an intrinsic total star-formation rate of 315 $\pm$ 60 M$_\odot$ yr$^{-1}$ |
| Dust mass | 6.4e8 | 1.5e8 | Msun | 3 | a dust mass of 6.4 $\pm$ 1.5 $\times$ 10$^{8}$ M$_{\odot}$ |
| Maximum SFR density | 190 | 20 | Msun/yr/kpc^2 | 4 | The maximum star-formation rate density in our reconstructed map is 190 $\pm$ 20 M$_{\odot}$ yr$^{-1}$ kpc$^{-2}$ |
| 230-290 GHz flux ratio, whole source | 0.56 | 0.08 | dimensionless | 4 | the flux-ratio of the entire source is 0.56 $\pm$ 0.08 |
| Total flux density Band 6 / Band 7 (<=0.5 Mλ) | 21.7 / 38.9 | 2.2 / 3.9 | mJy | 2 | 21.7 $\pm$ 2.2 and 38.9 $\pm$ 3.9 mJy, respectively |

## Qualitative findings

- Source is non-uniform with a ~1.9x0.7 kpc disk-like structure containing three compact regions  
  > "The highest surface brightness region is a $\sim$1.9$\,\times$ 0.7 kpc disk-like structure" (abstract)

## Claim tuples

- H: Is the dust emission structured and what is the magnification? | E: Pixelated visibility-space lens modelling of Band 6/7 | R: mu_tot = 17.6 ± 0.4; multiple clumps | F: Source compact and clumpy, consistent with size-bias | **supported**
- H: Is star formation Eddington-limited? | E: SFR density map | R: Max 190 ± 20 vs ~1000 Msun/yr/kpc^2 | F: Sub-Eddington starburst | **supported**
- H: Does the dust slope vary across the source? | E: Band 6/7 flux ratios per clump | R: 0.51, 0.41, 0.45 vs 0.56 whole | F: Tentative variation in temperature/opacity | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Parametric source profiles cannot represent complex dust structure  
  > "These are unlikely to represent well the complex surface brightness distribution of dusty star-forming galaxies on sub-kpc scales" (3 Gravitational lens mass modelling)
- Alternative: uv-taper rejected in favour of a uv-cut to limit visibilities  
  > "a cut was used instead of a *uv*-taper because this limited the number of visibilities" (2 ALMA continuum imaging)
- How they decided it was enough: _not stated_
- Limitation (authors): Results may not extrapolate to general SMG population due to size-bias  
  > "the results for this source should not necessarily be extrapolated to the general sub-mm galaxy population" (4 The intrinsic source properties of SDP.81)
- Caveat (inferred, ours): Intrinsic SFR and dust mass depend on external SED fit
- Caveat (inferred, ours): Only baselines <=2 Mλ used, so 'sub-50 pc' claim is not from the fitted data
- Caveat (inferred, ours): Code not named or public
- Caveat (inferred, ours): Spectral-slope variation is low significance

## Reproducibility

- Data public (paper): ALMA science verification data  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00016.SV." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Lens modelling code and settings (method paper in preparation)
- Missing: Regularisation and prior details
- Data volume (inferred): Large raw dataset (>1e8 visibilities per band); tens to hundreds of GB
- Score (inferred): 3/5, Public data but custom unreleased code and sparse settings.
- Rediscovery candidate: no, Requires non-public pixelated lens-modelling code and unstated settings.

## Links

- Method: (cite: rybak15) (Bayesian pixelated visibility-fitting lens modelling)
- Method: (cite: Vegetti09) (Gravitational imaging technique)
- Companion: Paper II (Rybak et al.) (Emission line reconstruction using this lens model)
- Companion: ALMA Partnership; Vlahakis et al. 2015 (SDP.81 observations and data processing)
- Related: H-ATLAS
- Related: SPT lens survey

## Checks

```json
{
 "quotes": 48,
 "quotes_ok": 48,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 36,
  "rate": 0.545
 },
 "evidence_ok": true
}
```
