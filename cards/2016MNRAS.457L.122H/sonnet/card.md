# ALMA resolves extended star formation in high-z AGN host galaxies

`2016MNRAS.457L.122H` | Monthly Notices of the Royal Astronomical Society 2016 | first author: Harrison, C. M. | arXiv: 1510.06740 | DOI: 10.1093/mnrasl/slw001

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: Is the rest-frame FIR (star-formation) emission in high-z X-ray AGN hosts extended, and are its sizes and SFR surface densities similar to those of SMGs?  
  > "Here, we place constraints on the sizes of the rest-frame FIR emission in high-$z$ X-ray AGN host galaxies and hence measure the spatial distribution and surface density of star formation in these sources" (Introduction)
- Target **Chandra Deep Field South X-ray AGN (IDs 156, 276, 301, 310, 344) plus serendipitous source 305(S)**: coordinates _not stated_; z/distance z≈1.5–4.5 (photometric; spectroscopic for ID 344, z=1.617)  
  > "Thirty AGN were targeted that were selected from the *Chandra*-Deep Field South (CDF-S; (cite: Xue11))" (2 Target selection, observations and analysis); "For the AGN we adopt the photometric redshifts and 1$\sigma$ uncertainties provided in (cite: Hsu14)." (2.3 Multi-wavelength properties); distance from Hsu et al. 2014 photometric redshifts; Szokoly04 spectroscopic for 344; 3D-HST (Skelton14) for 305(S)  
  > "Thirty AGN were targeted that were selected from the *Chandra*-Deep Field South (CDF-S; (cite: Xue11))" (2 Target selection, observations and analysis); "For the AGN we adopt the photometric redshifts and 1$\sigma$ uncertainties provided in (cite: Hsu14)." (2.3 Multi-wavelength properties)

## Data provenance

- ALMA projects: 2012.1.00869.S
- bands: Band 7 (870 μm), Cycle 1  
  > "The data presented in this letter are from a Cycle 1 Band 7 ALMA programme" (2 Target selection, observations and analysis)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: 7.5 GHz centred on 351 GHz  
  > "Each target was observed using 7.5 GHz of bandwidth, centred on 351 GHz (i.e., $\approx$870 $\mu$m)" (2.1 ALMA observations)
- arrays: 26 antennae  
  > "The array configuration contained 26 ALMA antennae, with a maximum baseline of 1300 m and median baselines of $\approx$200 m." (2.1 ALMA observations)
- configurations: _not stated_
- baselines: max 1300 m, median ≈200 m  
  > "with a maximum baseline of 1300 m and median baselines of $\approx$200 m" (2.1 ALMA observations)
- angular resolution: ≈0.3 arcsec (high-res), ≈0.8 arcsec (detection)  
  > "“detection images” (FWHM$\approx$0.8$^{\prime\prime}$) and (2) “high-resolution images” (FWHM$\approx$0.3$^{\prime\prime}$)" (2.2 Data reduction and source detection)
- max recoverable scale: 4–6 arcsec  
  > "The observations are sensitive to a maximum angular scale of 4–6$^{\prime\prime}$" (2.1 ALMA observations)
- sensitivity: σ870=0.07–0.18 mJy/beam (high-res); 0.10–0.25 (detection)  
  > "These final cleaned images have a noise of $\sigma_{870}$=0.07–0.18 mJy beam$^{-1}$." (2.2 Data reduction and source detection)
- time on source: 2.5–7 min per target  
  > "with on-source exposure times of 2.5–7 min" (2.1 ALMA observations)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **Herschel PACS/SPIRE, Spitzer**: Infrared photometry for SED fitting  
  > "fitting SEDs to the available *Spitzer*, deblended *Herschel*-PACS; deblended *Herschel*-SPIRE and ALMA photometry" (2.3 Multi-wavelength properties)
- Other facility **HST**: I, J, H imaging for positions  
  > "we collated the $I$-band, and where possible, $J$ and $H$ band *HST* observations of our targets" (2.3 Multi-wavelength properties)
- Other facility **VLA 1.4 GHz**: Radio synchrotron check  
  > "Only three of our sources (156, 344 and 305\[S\]) are detected in the deep 1.4 GHz radio imaging of (cite: Miller13)" (2.3 Multi-wavelength properties)
- External data: Photometric redshifts of the AGN  
  > "For the AGN we adopt the photometric redshifts and 1$\sigma$ uncertainties provided in (cite: Hsu14)." (2.3 Multi-wavelength properties) [from (cite: Hsu14)]
- External data: 2–8 keV X-ray fluxes  
  > "We use these redshifts and the 2–8 keV X-ray fluxes from (cite: Xue11) to calculate X-ray luminosities" (2.3 Multi-wavelength properties) [from (cite: Xue11)]
- External data: SMG ALMA sizes and FIR luminosities for comparison  
  > "we compare our FIR size measurements with the $z$$\approx$1–5 SMGs from the UDS field that were observed with ALMA by (cite: Simpson15)" (4 Discussion) [from (cite: Simpson15)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline, rerun with additional flagging after visual inspection  
  > "However, the calibrated data were then visually inspected and, where appropriate, we repeated the pipeline calibration including additional data flagging." (2.2 Data reduction and source detection)
- casa version: CASA 4.4.0  
  > "Application (casa; version 4.4.0; (cite: McMullin07))" (2.2 Data reduction and source detection)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean  
  > "imaged using the clean routine provided by casa" (2.2 Data reduction and source detection)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5 (high-res); natural weighting plus Gaussian taper (detection)  
  > "To create the high-resolution images we used Briggs weighting (robust parameter = 0.5)" (2.2 Data reduction and source detection)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: tight clean mask around sources detected at SNR≥5 in dirty images; clean to 1.5σ, repeat for SNR≥4  
  > "We then place a tight clean mask around the emission from the source and iteratively clean down to 1.5$\sigma$ within these regions." (2.2 Data reduction and source detection)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: (0.3–0.4)x0.2 arcsec high-res; (0.8–0.9)x0.7 arcsec detection  
  > "to obtain synthesised beams of (0.3$^{\prime\prime}$–0.4$^{\prime\prime}$)$\times$0.2$^{\prime\prime}$" (2.2 Data reduction and source detection)
- final rms: 0.07–0.18 mJy/beam (high-res)  
  > "These final cleaned images have a noise of $\sigma_{870}$=0.07–0.18 mJy beam$^{-1}$." (2.2 Data reduction and source detection)

### Inherited from earlier work

- Imaging methods  
  > "To image the data, we largely follow the methods described in detail in (cite: Simpson15) and so we only provide brief details here." (2.2 Data reduction and source detection) [from (cite: Simpson15)]
- Size measurement with imfit  
  > "To measure the intrinsic far-infrared sizes of our targets we follow the same methods as those presented in (cite: Simpson15)." (3 Extended far-infrared emission) [from (cite: Simpson15)]
- SED fitting routine and photometry compilation  
  > "The details of the SED fitting routine and the compilation of the non-ALMA photometry are detailed in (cite: Stanley15)." (2.3 Multi-wavelength properties) [from (cite: Stanley15)]
- SFR surface density derivation  
  > "To derive SFR surface densities we follow (cite: Simpson15)." (4 Discussion) [from (cite: Simpson15)]
- Full observations and data reduction details  
  > "Full details of the observations and data reduction will be presented in Stanley et al. (in prep)." (2.1 ALMA observations) [from Stanley et al. (in prep)]

### Not stated but needed to reproduce (our reading)

- Taper parameters for detection images
- Calibrator names and flux scale
- Observing dates and exact configurations
- Cell and image size
- Pipeline version
- SED templates and fitting details (in Stanley15)
- uv-binned amplitude fit initial settings
- Source positions

## Analysis recipe

1. **Calibrate and image**: ALMA pipeline calibration with extra flagging; clean to make detection and high-resolution images  
  > "We created two sets of images: (1) “detection images” (FWHM$\approx$0.8$^{\prime\prime}$) and (2) “high-resolution images” (FWHM$\approx$0.3$^{\prime\prime}$)." (2.2 Data reduction and source detection)
   - software: CASA
   - parameter: robust 0.5 for high-res  
  > "Briggs weighting (robust parameter = 0.5)" (2.2 Data reduction and source detection)
   - fitting: _not stated_
   - validation: _not stated_
2. **Detect sources and measure fluxes**: Peak SNR≳9 detections; total flux in 1 arcsec diameter apertures; errors from random apertures  
  > "Uncertainties are calculated by taking the 1$\sigma$ distribution from placing hundreds of random apertures across the images." (2.2 Data reduction and source detection)
   - software: CASA
   - fitting: _not stated_
   - validation: Detection-image fluxes agree within 20%  
  > "agreement within 20% in all cases and a median ratio between measurements of 1.0" (2.2 Data reduction and source detection)
3. **Derive L_IR from SED fitting**: Fit empirical SF templates plus AGN template to Spitzer, Herschel and ALMA photometry; subtract AGN contribution  
  > "Using the best-fit SEDs we derived total infrared luminosities, $L_{{\rm IR,SF}}$, due to star formation only" (2.3 Multi-wavelength properties)
   - assumption: X-ray luminosities assume Gamma=1.4  
  > "assuming a power-law index of $\Gamma$=1.4" (2.3 Multi-wavelength properties)
   - fitting: best-fit combination of templates accounting for uncertainties and upper limits  
  > "taking into account photometric data points, uncertainties, and upper limits" (2.3 Multi-wavelength properties)
   - validation: Radio synchrotron negligible  
  > "We conclude that the ALMA photometry has negligible contribution from synchrotron emission." (2.3 Multi-wavelength properties)
4. **Test for extended emission in uv-amplitudes**: Bin visibility amplitudes in 100 kλ steps; fit constant vs Gaussian; compare with BIC  
  > "binning across the $uv$ distance in steps of 100k$\lambda$, and calculating the error on the mean in each bin" (3 Extended far-infrared emission)
   - fitting: constant and Gaussian models, BIC comparison  
  > "Using the Bayesian Information Criterion ((cite: Schwarz78))" (3 Extended far-infrared emission)
   - validation: Δχ² 19–255 favouring Gaussian  
  > "The $\Delta\chi^{2}$ values between the two fits range from 19–255." (3 Extended far-infrared emission)
5. **Measure intrinsic sizes**: imfit elliptical Gaussian convolved with beam fit to high-res images  
  > "we use the imfit routine in casa to fit an elliptical Gaussian model (convolved with the synthesised beam) to the 870 $\mu$m emission" (3 Extended far-infrared emission)
   - software: CASA
   - fitting: _not stated_
   - validation: uv sizes agree within 1–3σ, median ratio 0.9; peak/integrated flux ratios 0.49–0.74  
  > "with a median ratio of FWHM$^{uv}$/FWHM$^{{\rm image}}$=0.9" (3 Extended far-infrared emission)
6. **SFR surface densities and comparison with SMGs**: Convert L_IR to SFR (Kennicutt98, Chabrier IMF), uniform surface density within radius FWHM/2  
  > "we convert infrared luminosities to SFRs, following (cite: Kennicutt98) (converting to a Chabrier IMF), and assume a uniform surface density with a radius of FWHM/2" (4 Discussion)
   - assumption: H0=70, OmegaM=0.30, OmegaL=0.70  
  > "we adopt $H_0 = 70$ km s$^{-1}$ Mpc$^{-1}$, $\Omega_{\rm{M}} = 0.30$ and $\Omega_{\Lambda}= 0.70$" (1 Introduction)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.4.0: calibration, clean imaging, imfit size fitting  
  > "The data were processed using the Common Astronomy Software Application (casa; version 4.4.0; (cite: McMullin07))" (2.2 Data reduction and source detection)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Median physical FIR size of AGN | 1.8 | not stated | kpc | 5 | physical sizes of 1–3 kpc (median value of 1.8 kpc) |
| Deconvolved FWHM range | 0.2–0.5 | not stated | arcsec | 5 | The measured intrinsic (i.e., deconvolved) sizes are FWHM=0.2$^{\prime\prime}$–0.5$^{\prime\prime}$ |
| SFR surface density | 20–200 | not stated | Msun/yr/kpc^2 | 6 | We obtain SFR surface densities of $\approx$20–200 $M_{\ensuremath{\odot}}$ yr$^{-1}$ kpc$^{-2}$ |
| Peak-to-integrated flux ratio | 0.49–0.74 | not stated | dimensionless | 5 | We find $S^{0.3}_{\rm pk}$/$S^{0.3}_{\rm
  int}$=0.49–0.74. |

## Qualitative findings

- All six detected sources are spatially resolved at 0.3 arcsec  
  > "In all cases imfit returns spatially-resolved fits" (3 Extended far-infrared emission)

## Claim tuples

- H: FIR emission in high-z X-ray AGN hosts is extended | E: uv-amplitude fits and imfit on 0.3 arcsec images | R: All sources resolved with FWHM 0.2–0.5 arcsec (1–3 kpc) | F: Star-forming dust emission extended on kpc scales | **supported**
- H: AGN host sizes and SFR surface densities differ from SMGs | E: Compare with Simpson15 SMGs measured identically | R: Sizes and surface densities similar at comparable L_IR | F: Star formation distribution independent of X-ray AGN presence (small sample) | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: AGN-heated dust or radio synchrotron as source of the emission rejected  
  > "the observed spatial extent of the FIR emission on $>$1 kpc scales is challenging to explain with dust that is heated directly by AGN without any contribution from star formation" (4 Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Small sample, all with high FIR luminosities  
  > "Although limited by a small sample of AGN, which all have high FIR luminosities" (abstract)
- Caveat (inferred, ours): Only 3 of 30 primary targets detected; selection biased
- Caveat (inferred, ours): Photometric redshifts uncertain for several sources
- Caveat (inferred, ours): Sizes from short snapshot observations with modest SNR

## Reproducibility

- Data public (paper): Project code given; public status not stated  
  > "This paper makes use of ALMA data: ADS/JAO.ALMA-2012.1.00869.S." (footnote 1)
- Products in archive: _not stated_
- Missing: Full reduction details deferred to Stanley et al. in prep
- Missing: SED fitting inputs
- Missing: Taper parameters
- Data volume (inferred): ~10-50 GB raw for Cycle 1 project
- Score (inferred): 3/5, Recipe largely given and follows Simpson15, but several settings are deferred or unstated.
- Rediscovery candidate: no, Key details deferred to in-prep paper and SED analyses.

## Links

- Method: (cite: Simpson15) (Imaging and size measurement methods)
- Method: (cite: Stanley15) (SED fitting routine)
- Companion: (cite: Mullaney15) (Source programme and sample)
- Related: CDF-S
- Related: UDS ALMA SMG survey

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
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 79,
  "stated": 49,
  "rate": 0.62
 },
 "evidence_ok": true
}
```
