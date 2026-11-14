# Chasing discs around O-type (proto)stars. ALMA evidence for an SiO disc and disc wind from G17.64+0.16

`2018A&A...620A..31M` | Astronomy and Astrophysics 2018 | first author: Maud, L. T. | arXiv: 1810.03920 | DOI: 10.1051/0004-6361/201833908

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Does the O-type YSO G17.64+0.16 host a disc, and what do the SiO kinematics say about a disc and disc wind?  
  > "The main parameter we aim to characterise is the stellar mass, as this is key to understanding whether G17.64 is truly an O-type YSO." (Analysis and Discussion)
- Target **G17.64+0.16 (AFGL 2136)**: coordinates J2000 18h22m26.385s -13d30'11.97"  
  > "G17.64 is located at 2.2 kpc and has a bolometric luminosity of 1$\times$10$^5$ L$_{\odot}$." (Introduction); "J2000 18$^{\rm h}$22$^{\rm m}$26.385$^{\rm s}$ $-$13$^{\circ}$30$'$11.97$''$" (Continuum emission); z/distance 2.2 kpc  
  > "G17.64 is located at 2.2 kpc and has a bolometric luminosity of 1$\times$10$^5$ L$_{\odot}$." (Introduction); "J2000 18$^{\rm h}$22$^{\rm m}$26.385$^{\rm s}$ $-$13$^{\circ}$30$'$11.97$''$" (Continuum emission); distance from kinematic distance from RMS survey (Urquhart2012; Urquhart2014)  
  > "G17.64 is located at 2.2 kpc and has a bolometric luminosity of 1$\times$10$^5$ L$_{\odot}$." (Introduction); "J2000 18$^{\rm h}$22$^{\rm m}$26.385$^{\rm s}$ $-$13$^{\circ}$30$'$11.97$''$" (Continuum emission)

## Data provenance

- ALMA projects: 2013.1.00489.S, 2016.1.00288.S
- bands: Band 6 (220-230 GHz)  
  > "for the molecular line emission in Band 6 (220$-$230 GHz)" (Observations)
- frequencies and spectral setup: one ~1.875 GHz wide SPW for continuum plus narrower ~234 MHz SPWs for lines  
  > "one wide-band spectral window (SPW) with $\sim$1.875 GHz bandwidth" (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 40 m to ~1500 m (12 m array); ACA 8.9 to 45.0 m  
  > "baselines ranging from 40 m out to $\sim$1500 m" (Observations); "the array had baselines ranging from 8.9 to 45.0 m" (Observations)
- angular resolution: _not stated_
- max recoverable scale: ~7 arcsec (12 m)  
  > "our observations are sensitive to scales up to $\sim$7$''$" (Larger scales and the 13CO molecular outflow)
- sensitivity: _not stated_
- time on source: ACA ~3 min; TP ~19 min  
  > "The total time on source was about three minutes for the ACA." (Observations)
- observing dates: July and September 2015 (Cycle 2); ACA 27 November 2016  
  > "during Cycle 2 in July and September 2015" (Observations)
- pi or archival as stated: PI Cesaroni  
  > "(2013.1.00489.S - PI: Cesaroni)" (Observations)
- Line: SiO 5-4 (217.10498 GHz)
- Line: CH3CN 12-11 K=3 (220.70902 GHz)
- Line: 13CO 2-1 (220.39868 GHz)
- Line: CH3OH 4(2,2)-3(1,2) E (218.44005 GHz)
- Line: H30alpha recombination line (231.90093 GHz)
- Other facility **UKIDSS**: near-IR JHK background image  
  > "These near-IR images were obtained by the UKIDSS" (Larger scales and the 13CO molecular outflow)
- External data: Free-free spectral index 1.2 and radio fluxes  
  > "using the free-free spectral index of 1.2 estimated by (cite: Menten2004)" (Continuum emission) [from Menten2004]
- External data: Inclination 70 deg from IR models  
  > "We used a source inclination of 70$^{\circ}$" (SiO) [from dewit2011]
- External data: Tex = 21.2 K and tau13CO = 6.34 for outflow  
  > "estimates for the excitation temperature (T$_{ex}$ = 21.2 K) and correct optical depth using a bulk average ($\tau_{13_{CO}}$ = 6.34)" (ACA 13CO outflow) [from Maud2015]

## Processing

### Calibration

- pipeline or manual: ACA data pipeline reduced then manually imaged; TP delivered products  
  > "The data were pipeline reduced and then the ACA data were manually imaged" (Observations)
- casa version: CASA 4.5.3 (12 m); 4.7.2 (ACA)  
  > "The data reduction was undertaken using casa version 4.5.3" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: iterative self-cal on line-free continuum, solints 180, 60, 30 s then 6 s; S/N improved ~180 to ~860  
  > "subsequent iterations using 180, 60 and 30 seconds, then finally down to the integration time of 6 s" (Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs robust 0.5 for all; robust 1.5 also for continuum  
  > "A Briggs robust weighting of 0.5 (cite: Briggs1995) was used for all images" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: standard continuum subtraction using line-free channels, remade after self-cal  
  > "the continuum subtraction was remade" (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: ACA not merged with 12 m data  
  > "the ACA data are unsuitable for merging with the aforementioned 12 m data" (Observations)
- smoothing: _not stated_
- final beam: continuum 0.17x0.14 arcsec PA -88.2; SiO 0.20x0.15  
  > "Continuum | 226.700 | ... | ... | 0.17$\times$0.14, $-$88.2 | 0.07" (Table 1)
- final rms: continuum 0.07 mJy/beam; SiO 1.21 mJy/beam per channel  
  > "SiO | 217.10498 | 5$-$4 | 31.26 | 0.20$\times$0.15, $-$88.3 | 1.21 | 2.70" (Table 1)

### Inherited from earlier work

- Spectral setup details  
  > "We refer the reader to (cite: Cesaroni2017) for more details on the setup." (Observations) [from Cesaroni2017]
- Outflow mass analysis adapted for ACA 13CO  
  > "We use the analysis presented in (cite: Maud2015) adapted to the $^{13}$CO (2$-$1) transition observed with the ACA." (ACA 13CO outflow) [from Maud2015]
- Line broadening analysis for H30alpha  
  > "Following the analysis outlined in (cite: GalvanMadrid2012) pressure broadening can at most explain" (H30alpha) [from GalvanMadrid2012]

### Not stated but needed to reproduce (our reading)

- Cell and image size, clean thresholds and masks
- Line-free channels and continuum bandwidth used
- Calibrators and flux scale
- Which self-cal solution intervals/gain types in detail
- Model code and exact by-eye selection criteria
- Pixel-level model convolution beam

## Analysis recipe

1. **Self-calibrate and image**: Self-calibration on line-free continuum, applied to all data; continuum subtraction remade; imaged with robust 0.5/1.5  
  > "The self-calibration solutions were applied to the entire G17.64 data" (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: S/N improved from ~180 to ~860; compared with statcont  
  > "improving from $\sim$180 to over $\sim$860" (Observations)
2. **Continuum size and dust mass**: 2D Gaussian fit in image plane; optically thin dust mass with free-free subtracted  
  > "A two-dimensional gaussian fit to the central continuum emission" (Continuum emission)
   - assumption: kappa0 = 1.0 cm2/g, gas-to-dust 100, T = 50-100 K  
  > "a gas-to-dust ratio of 100, and temperatures between 50 and 100 K" (Continuum emission)
   - fitting: Gaussian fit  
  > "A two-dimensional gaussian fit to the central continuum emission associated with G17.64 in the image plane results in deconvolved source dimensions" (Continuum emission)
   - validation: mass uncertain by factor 2-3  
  > "uncertainties in dust mass by a factor of 2-3 are not unreasonable" (Continuum emission)
3. **SiO morphology, centroids and PV diagram**: Moment maps, channel-by-channel Gaussian centroids, PV cut at PA 30 deg with beam width  
  > "we show the centroid positions after fitting Gaussians to each channel in the SiO image cube" (SiO)
   - assumption: Inclination 70 deg  
  > "We used a source inclination of 70$^{\circ}$" (SiO)
   - fitting: _not stated_
   - validation: _not stated_
4. **Parametric kinematic model**: 3D optically thin emissivity/velocity model (Keplerian, radial, disc surface) compared to PV diagram on a coarse grid  
  > "We make a qualitative by-eye assessment for suitable matches with the data." (Modelling)
   - parameter: M 5-50 Msun, Rinner 10-50 au, Router 100-600 au, p+q -2.6 to -1.8  
  > "Stellar Mass | $M$ | 5$-$50" (Table 3)
   - assumption: turbulent width 0.5 km/s, surface layer scale height 10 au  
  > "typical turbulent line width of 0.5 km s$^{-1}$" (Modelling)
   - fitting: by-eye grid comparison, no sampler  
  > "We make a qualitative by-eye assessment for suitable matches with the data." (Modelling the kinematics of the compact disc emission)
   - validation: qualitative match in all four PV quadrants  
  > "all models provide a qualitative match to the entire observed PV plot in all quadrents, depending on the parameter combination." (Disc and Disc Surface)

## Software

- **CASA** 4.5.3 (12 m), 4.7.2 (ACA): data reduction and imaging  
  > "The data reduction was undertaken using casa version 4.5.3" (Observations)
- **statcont** : comparison continuum subtraction  
  > "Comparisons were made for G17.64 using statcont which did produce comparable products" (footnote 5)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum flux density at 1.3 mm | 81.3 | not stated | mJy | 2 | peak = 74.2 mJy beam$^{-1}$, flux density = 81.3 mJy |
| Dust mass | 0.85-2.69 | factor 2-3 | Msun | 2 | 3.57$-$29.5 / 0.85$-$2.69 |
| Deconvolved continuum size | 53 x 39 mas, PA 25 | PA ±5 deg | mas | 2 | deconvolved source dimensions (FWHM - full-width-half-maximum) of 53 $\times$ 39 milliarcsecond |
| H30alpha FWHM | 81.9 | 1.7 | km/s | 0 | FWHM$\sim$81.9$\pm$1.7 km s$^{-1}$ |
| SiO integrated PA | 47 | 7 | deg | 3 | indicates a PA of $\sim$47$\pm$7$^{\circ}$ and a major axis of $\sim$0.28$''$ |
| ACA 13CO outflow lobe masses (blue, red) | 1.64, 8.40 | not stated | Msun | 0 | are 1.64 and 8.40 M$_{\odot}$ respectively |

## Qualitative findings

- SiO is compact and perpendicular to the large-scale outflow, inconsistent with a jet  
  > "inconsistent with a typical jet origin" (Conclusions)
- CH3CN does not trace a disc  
  > "we find no evidence for a rotating disc in this molecular tracer" (CH3CN and CH3OH)

## Claim tuples

- H: Is there a rotating disc around G17.64? | E: SiO moment, centroid and PV analysis plus parametric models | R: Keplerian rotation of a compact disc (<200 au) around 10-30 Msun matches high-velocity SiO | F: A compact disc with a radially expanding component (disc wind) is required | **supported**
- H: Is G17.64 a late-stage O-type YSO? | E: H30alpha and luminosity compared with model masses | R: Broad compact H30alpha, upper model mass ~20 Msun | F: G17.64 is contracting from a bloated star | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Pure rotation and rotation+radial disc-only models fail to match all four PV quadrants  
  > "Again, none of the models are entirely consistent with the observed PV diagram." (Disc only - rotation with radial motion)
- How they decided it was enough: _not stated_
- Limitation (authors): Disc only marginally resolved so Keplerian fitting not reliable  
  > "thus ‘fitting’ Keplerian rotation lines is not reliable" (SiO)
- Caveat (inferred, ours): Mass is degenerate with inclination and inner radius; inclination is fixed from literature
- Caveat (inferred, ours): By-eye model matching without uncertainties
- Caveat (inferred, ours): Dust mass includes unquantified optical depth and temperature

## Reproducibility

- Data public (paper): ALMA project codes cited; data in archive  
  > "ADS/JAO.ALMA#2013.1.00489.S and ADS/JAO.ALMA#2016.1.00288.S" (Acknowledgements)
- Products in archive: _not stated_
- Missing: Model code
- Missing: Imaging parameters and masks
- Missing: Self-cal details
- Data volume (inferred): ~50-100 GB
- Score (inferred): 3/5, Public data and clear processing summary but model code and imaging details missing; modelling is by-eye.
- Rediscovery candidate: no, Main kinematic conclusions rely on unreleased by-eye modelling.

## Links

- Method: Richer1991 (parametric PV model approach)
- Companion: Cesaroni2017 (original sample paper presenting the same data)
- Related: Red MSX Source survey

## Checks

```json
{
 "quotes": 66,
 "quotes_ok": 66,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 46,
  "rate": 0.639
 },
 "evidence_ok": true
}
```
