# SYMBA: An end-to-end VLBI synthetic data generation pipeline. Simulating Event Horizon Telescope observations of M 87

`2020A&A...636A...5R` | Astronomy and Astrophysics 2020 | first author: Roelofs, F. | arXiv: 2004.01161 | DOI: 10.1051/0004-6361/201936622

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type technical_calibration_or_instrument

## Science

- Fields: instrumentation, agn_and_quasars
- Question: How can realistic synthetic mm-VLBI (EHT) data with atmospheric, instrumental and calibration effects be generated and calibrated, and how well can GRMHD models of M87 be recovered with current and future EHT arrays?  
  > "Using synthetic data based on two example general relativistic magnetohydrodynamics (GRMHD) model images of M87, we performed case studies to assess the image quality that can be obtained with the current and future EHT array for different weather conditions." (abstract)
- Target **M87**: coordinates _not stated_; z/distance 16.4 ± 0.5 Mpc (16.7 Mpc assumed for the GRMHD models)  
  > "At a distance of $(16.4 \pm 0.5)$ Mpc (cite: Bird2010), the mass measurements correspond to an apparent diameter of the shadow between $\sim22$ $\mu$as and $42$ $\mu$as." (1 Introduction); distance from Bird2010  
  > "At a distance of $(16.4 \pm 0.5)$ Mpc (cite: Bird2010), the mass measurements correspond to an apparent diameter of the shadow between $\sim22$ $\mu$as and $42$ $\mu$as." (1 Introduction)

## Data provenance

- ALMA projects: 2017.1.00841.V
- bands: _not stated_
- frequencies and spectral setup: 64 channels spanning 2 GHz bandwidth centred at 228 GHz (synthetic)  
  > "the visibilities are split into 64 channels spanning a bandwidth of 2 GHz centred at 228 GHz, which is the central EHT observation frequency." (7.1 Point source study)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: EHT2017 schedule of 11 April adopted  
  > "The EHT2017 schedule for 11 April was adopted." (5.3 uv-coverage)
- pi or archival as stated: _not stated_
- Other facility **EHT stations (ALMA, APEX, JCMT, LMT, PV, SMA, SMT)**: Station parameters and observing schedule for the synthetic EHT2017 array; real ALMA data not analysed  
  > "Our primary array consists of the 2017 EHT stations, excluding the SPT station for which M87 is always below the horizon." (5.1 EHT2017 array)
- External data: GRMHD model images of M87 (thermal-jet and kappa-jet) used as input source models  
  > "We base our scientific studies primarily on a GRMHD simulation of the jet launching region of M87 from (cite: Davelaar2019)." (6.2.1 Fiducial models) [from (cite: Davelaar2019)]
- External data: Pre-EHT2017 GRMHD model images  
  > "we use `SYMBA` to simulate observations of GRMHD model images by (cite: Dexter2012) and (cite: Moscibrodzka2016)." (6.2.2 Pre-EHT2017 models) [from (cite: Dexter2012; Moscibrodzka2016)]
- External data: Median site weather (PWV, pressure, temperature) from the EHT2017 VLBI monitor  
  > "we used the median values measured during the EHT2017 campaign (5-11 April) at the individual primary sites, logged by the VLBI monitor (cite: eht-paperII)." (5.1 EHT2017 array) [from (cite: eht-paperII)]
- Simulation/model as data: Point source (4 Jy), geometric crescent (Kamruddin & Dexter 2013), and two GRMHD models (BHAC + RAPTOR) as synthetic inputs  
  > "We use a simple 4 Jy point source model to study signal corruption and calibration effects." (6.1.1 Point source model)

## Processing

### Calibration

- pipeline or manual: rPICARD CASA-based VLBI pipeline: fringe fit and a priori amplitude calibration, then network calibration with eht-imaging  
  > "the synthetic data are passed through the `rPICARD` calibration pipeline (cite: Janssen2019)." (3 Synthetic data calibration with rPICARD)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Amplitude then phase self-calibration to the reconstructed image within eht-imaging  
  > "The visibility phases are then self-calibrated and used for imaging as well, while maintaining the closure quantity fits." (7.2 Crescent and GRMHD image reconstructions)

### Imaging

- task: Regularized maximum likelihood imaging with eht-imaging (MEM, TV, TSV regularizers); starting model circular Gaussian FWHM 40 µas  
  > "The images are reconstructed with a regularized maximum likelihood (RML) method using the `eht-imaging` software." (7.2 Crescent and GRMHD image reconstructions)
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

- Fiducial eht-imaging parameters, regularizers and imaging script  
  > "The fiducial parameters and regularizers (Maximum Entropy, Total Variation, and Total Squared Variation) obtained from an extensive parameter survey by (cite: eht-paperIV) are adopted." (7.2 Crescent and GRMHD image reconstructions) [from (cite: eht-paperIV)]
- MeqSilhouette corruption details  
  > "We briefly describe the added tropospheric and instrumental corruptions below, referring to (cite: Blecher2017) and (cite: Natarajan2019) for more details." (2 Synthetic data generation with MeqSilhouette) [from (cite: Blecher2017; Natarajan2019)]

### Not stated but needed to reproduce (our reading)

- Exact eht-imaging regularizer weights and iteration schedule
- MeqSilhouette and rPICARD version numbers
- Random seeds for noise and pointing draws
- Exact GRMHD model image files

## Analysis recipe

1. **Generate corrupted synthetic visibilities**: MeqSilhouette predicts visibilities from the input model and adds tropospheric, noise, pointing, gain and leakage corruptions  
  > "`MeqSilhouette` predicts visibilities directly from the Fourier Transform of an input sky model." (2 Synthetic data generation with MeqSilhouette)
   - software: MeqSilhouette, ATM
   - fitting: _not stated_
   - validation: _not stated_
2. **Calibrate synthetic data**: rPICARD fringe fit (S/N>5.5) and a priori amplitude calibration, then 10 s averaging and network calibration  
  > "the smallest timescale which yields fringe detections with S/N\>5.5 on all baselines for which the source can be detected, is chosen" (3 Synthetic data calibration with rPICARD)
   - software: rPICARD, CASA, eht-imaging
   - fitting: _not stated_
   - validation: _not stated_
3. **Reconstruct images and quantify fidelity**: RML imaging and normalized cross-correlation with the input model convolved with varying beams  
  > "We compute the normalized cross-correlation (cite: eht-paperIV) between the reconstructed image $X$ and the input model image $Y$" (7.2 Crescent and GRMHD image reconstructions)
   - software: eht-imaging
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **MeqSilhouette** : synthetic data generation  
  > "We generate raw synthetic data with `MeqSilhouette`" (1 Introduction)
- **rPICARD** : CASA-based calibration of synthetic data  
  > "We then calibrate the raw data using the new `CASA` (cite: McMullin2007) VLBI data calibration pipeline `rPICARD`" (1 Introduction)
- **eht-imaging** : network calibration and RML imaging  
  > "a ‘network calibration’ (cite: Fish2011; Johnson2015; Blackburn2019; eht-paperIII) is performed with the `eht-imaging` software." (3 Synthetic data calibration with rPICARD)
- **ATM** : atmospheric attenuation and delay  
  > "`MeqSilhouette` calculates the attenuation and time delays using the Atmospheric Transmission at Microwaves (`ATM`) software" (2.1.1 Mean troposphere)
- **am** : radiative transfer for PWV and opacity conversion  
  > "we then perform radiative transfer at 225 GHz with the `am` atmospheric model software (cite: Paine2019)" (5.1 EHT2017 array)
- **BHAC** : GRMHD simulation of input model  
  > "This GRMHD simulation is performed with the code `BHAC` (cite: Porth2017)" (6.2.1 Fiducial models)
- **RAPTOR** : ray tracing of GRMHD models  
  > "The GRMHD simulation is post-processed with the general relativistic ray tracing code `RAPTOR` (cite: bronzwaer2018)." (6.2.1 Fiducial models)

## Numeric results


## Qualitative findings

- Atmospheric and instrumental corruptions significantly affect visibilities; EHT2017 can recover the GRMHD ring structure after calibration and self-calibration.  
  > "Our synthetic observations show that the effects of atmospheric and instrumental corruptions on the measured visibilities are significant." (abstract)
- Adding GLT, KP and PDB allows visual distinction of thermal-jet and kappa-jet models; AMT gives only minor improvement for M87.  
  > "The M87 reconstruction shows only minor improvement when the AMT is added to the EHT2020 array." (8.1 κ-jet versus thermal-jet model)

## Claim tuples

- H: Including all corruption and calibration effects matters versus thermal noise only | E: Reconstructed crescent and kappa-jet images from thermal-noise-only and full-effects synthetic data | R: Full-effects reconstructions show more artefacts and irregularity | F: Full simulation is important for assessing image reconstruction | **supported**
- H: Future EHT stations improve discrimination of GRMHD models | E: Synthetic observations with EHT2017, EHT2020, EHT2020+AMT of both models | R: Reconstructions improve and model-specific features appear with added stations | F: Models can be visually distinguished with EHT2020 | **supported**
- H: Poor weather degrades EHT imaging | E: PWV 5 mm, tc 3 s, pointing rms 1-4 arcsec | R: Decent image at 2 arcsec, much reduced at 3, failed at 4 | F: Image quality degrades strongly with pointing offsets in poor weather | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Only one GRMHD snapshot and two electron models used; results may not generalize.  
  > "We note that we have only used one GRMHD snapshot with two specific electron temperature models." (8.1 κ-jet versus thermal-jet model)
- Caveat (inferred, ours): No quantitative validation of simulated corruptions against real EHT data
- Caveat (inferred, ours): Visual model distinction is qualitative
- Caveat (inferred, ours): Weather and pointing parameters are rough estimates

## Reproducibility

- Data public (paper): Pipeline is open source on Bitbucket and dockerized; no real ALMA data are analysed  
  > "The pipeline is fully dockerized." (4 Computing workflow)
- Products in archive: _not stated_
- Code: SYMBA released at bitbucket.org/M_Janssen/symba  
  > "In this paper, we present the SYnthetic Measurement creator for long Baseline Arrays (`SYMBA`) – a new synthetic VLBI data generation and calibration pipeline." (1 Introduction)
- Missing: Exact GRMHD model images
- Missing: eht-imaging script parameters
- Data volume (inferred): Small; synthetic data only, tens of GB at most
- Score (inferred): 3/5, Open pipeline and many parameters in tables, but key imaging settings are inherited and model inputs are external.
- Rediscovery candidate: no, The work is a simulation pipeline with no real ALMA data and mostly qualitative, image-based results.

## Links

- Method: (cite: Blecher2017) (MeqSilhouette)
- Method: (cite: Janssen2019) (rPICARD)
- Method: (cite: eht-paperIV) (eht-imaging parameters)
- Companion: (cite: Davelaar2019) (GRMHD models used)
- Related: Event Horizon Telescope

## Checks

```json
{
 "quotes": 35,
 "quotes_ok": 35,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 0,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 30,
  "rate": 0.429
 },
 "evidence_ok": true
}
```
