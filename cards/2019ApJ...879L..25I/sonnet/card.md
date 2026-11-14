# Detection of Continuum Submillimeter Emission Associated with Candidate Protoplanets

`2019ApJ...879L..25I` | The Astrophysical Journal Letters 2019 | first author: Isella, Andrea | arXiv: 1906.06308 | DOI: 10.3847/2041-8213/ab2a12

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks, exoplanets
- Question: Is there sub-mm continuum emission associated with the PDS 70 planets b and c, and what dust mass would a circumplanetary disk need to explain it?  
  > "We present the discovery of a spatially unresolved source of sub-millimeter continuum emission ($\lambda=855$ $\mu$m) associated with a young planet, PDS 70 c" (abstract)
- Target **PDS 70**: coordinates _not stated_; z/distance 113.4 pc  
  > "a $\sim$5 Myr old low mass ($M_\star = 0.76 M_\odot$) T Tauri star at a distance of 113.4 pc (cite: Muller2018)" (Introduction); distance from Muller2018  
  > "a $\sim$5 Myr old low mass ($M_\star = 0.76 M_\odot$) T Tauri star at a distance of 113.4 pc (cite: Muller2018)" (Introduction)

## Data provenance

- ALMA projects: 2015.1.00888.S, 2017.A.00006.S
- bands: Band 7 (855 um)  
  > "the ALMA band 7 ($\lambda=855$ $\mu$m) observations of PDS 70" (Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15 m-1.5 km (2016); 15 m-6.9 km (2017)  
  > "baselines extending between 15 m and 1.5 km" (Observations); "baselines between 15 m and 6.9 km" (Observations)
- angular resolution: 0.093" x 0.074" (natural); 0.067" x 0.050" (robust 0.3)  
  > "achieves better angular resolution (FWHM=0.067$''$ $\times$ 0.050$''$)" (Observations)
- max recoverable scale: _not stated_
- sensitivity: rms 18 uJy/beam (natural), 19 uJy/beam (robust 0.3)  
  > "has an rms noise of 18 $\mu$Jy beam$^{-1}$" (Observations)
- time on source: _not stated_
- observing dates: August 2016; 2-6 December 2017  
  > "it was observed again between the 2$^{nd}$ and the 6$^{th}$ of December 2017" (Observations)
- pi or archival as stated: _not stated_
- Line: CO J=3-2 (not stated)
- Other facility **VLT/SPHERE**: NIR astrometry/images of planets (from Muller2018)  
  > "the VLT/SPHERE NIR image published in (cite: Muller2018)" (Complementary observations.)
- Other facility **VLT/MUSE**: Halpha detection of PDS 70 c (Haffert2019)  
  > "the VLT/MUSE H$\alpha$ image published in (cite: Haffert2019)" (Complementary observations.)
- External data: Planet masses, luminosities, orbital radii, accretion rates (Table 1)  
  > "Data from (cite: Wagner2018; Keppler2018; Haffert2019)" (Table 1) [from Wagner2018; Keppler2018; Haffert2019]
- External data: Stellar luminosity L*=0.36 Lsun  
  > "We assume a stellar luminosity $L_\star=0.36 L_\odot$ (cite: Muller2018)" (4.2) [from Muller2018]
- External data: Dust opacity 3.5 cm2/g  
  > "a dust opacity of 3.5 cm$^{2}$ g$^{-1}$ (cite: Keppler2019)" (Estimating the CPD dust mass) [from Keppler2019]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline, then self-calibration  
  > "Observations taken at the two different epochs were calibrated using the ALMA pipeline" (Observations)
- casa version: CASA 5.1.1  
  > "The self-calibration and imaging was performed in CASA 5.1.1" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: 2016 data had incorrect gain calibrator flux in pipeline, overestimating disk flux by ~25%  
  > "calibrated by the ALMA pipeline using an incorrect gain calibrator flux, which resulted in overestimating the flux density of the PDS 70 disk by about 25%" (Observations)
- flux scale uncertainty: _not stated_
- self calibration: Phase-only: SB solint inf then 120 s; combined 900, 120, 30 s; no amplitude self-cal  
  > "adopting solution intervals of 900 s, 120 s and 30 s" (Joint self-calibration); "amplitude self-calibration does not provide any improvement of the image quality" (Joint self-calibration)

### Imaging

- task: tclean  
  > "Using the task `tclean`, we generated an image of the continuum emission" (Self-calibration of 2015.1.00888.S data)
- deconvolver: multi-scale, scales 0,1,3,6 x beam FWHM  
  > "multi-scale cleaning with scales equal to 0 (point source), 1, 3, and 6 $\times$ the beam FWHM" (Self-calibration of 2015.1.00888.S data)
- weighting robust: Briggs, robust 2 to -0.3 explored; images at 2 and 0.3; self-cal images robust 0.5/0.6  
  > "Briggs weighting with *robust* parameters varying from 2 (which mimics natural weighting) to -0.3" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: elliptical mask 1.7" x 1.1", PA 160 deg (short baseline data)  
  > "an elliptical mask with a semi-major axis of 1.7$''$, a semi-minor axis of 1.1$''$, and a position angle of 160$^\circ$" (Self-calibration of 2015.1.00888.S data)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: 18 uJy/beam (natural), 19 uJy/beam (robust 0.3)  
  > "(rms=19 $\mu$Jy beam$^{-1}$)" (Observations)

### Inherited from earlier work

- Imaging and self-calibration procedure  
  > "imaged by us using the procedure described in (cite: Andrews2018)" (Observations) [from (cite: Andrews2018)]
- CPD temperature and flux model (Eq. 4)  
  > "Following (cite: Isella2014), we assume that CPDs are vertically isothermal" (Estimating the CPD dust mass) [from (cite: Isella2014)]
- Keplerian fitting of CO to find disk center  
  > "the fitting procedure is described in (cite: Teague2019)" (Astrometric measurements) [from (cite: Teague2019)]

### Not stated but needed to reproduce (our reading)

- Cleaning threshold, mask and scales for the robust 0.3 and 2 final images
- Spectral windows and line-free channels used for the continuum
- Flux calibrator and corrected flux value for the 2016 data
- Fit procedure and errors for the 2D Gaussian source fits
- Details of the CPD flux model grid (inner radius, inclination used numerically)

## Analysis recipe

1. **Self-calibrate and image continuum**: Phase self-cal of short-baseline data, then of combined data; tclean imaging at several robust values  
  > "we self-calibrated the combined data by averaging both on polarizations and spectral windows" (Joint self-calibration)
   - software: CASA, tclean, gaincal, applycal
   - parameter: clean threshold 8x rms; robust 0.5/0.6  
  > "a cleaning threshold of 0.15 mJy beam$^{-1}$, corresponding to 8$\times$ the rms noise" (Joint self-calibration)
   - fitting: _not stated_
   - validation: Sources found across robust weightings and in 2017 data alone  
  > "identified with the adopted range of weightings in both the combined and 2017 data alone" (Observations)
2. **Subtract symmetric ring to expose c_smm**: Visibility-space shift, deprojection, azimuthal average subtraction, re-imaging  
  > "The subtraction is performed in the Fourier space using the following procedure." (Subtraction of a symmetric ring emission)
   - parameter: inclination 49.9 deg, PA 159.9 deg  
  > "minimum for an inclination of 49.9$^\circ$  and a position angle of 159.9$^\circ$" (Subtraction of a symmetric ring emission)
   - fitting: chi2 minimization  
  > "We perform a $\chi^2$ minimization" (Subtraction of a symmetric ring emission)
   - validation: _not stated_
3. **Measure source astrometry and fluxes**: 2D Gaussian fits relative to disk center from continuum core and CO Keplerian rotation center  
  > "measured the center of the central component of the continuum emission (see Section 2) through a 2D Gaussian fit" (Astrometric measurements)
   - assumption: Star at disk center  
  > "we must therefore assume that the star is at the center of the disk" (4.1)
   - fitting: _not stated_
   - validation: Continuum and CO centers coincide within uncertainties  
  > "coincide within their uncertainties" (Astrometric measurements)
4. **Estimate CPD dust mass**: Grid of CPD models (Isella 2014) with temperature from viscous heating plus planet and stellar irradiation, matched to 106 uJy  
  > "We calculate continuum fluxes for a grid of models characterized by dust masses ($M_d$) between $10^{-3}$ M$_\Earth$ and $10^{-1}$ M$_\Earth$" (Estimating the CPD dust mass)
   - parameter: T_irr,* 20-80 K; mu=0.1; Sigma ∝ r^-1; Rout 0.3-3 au  
  > "where $\mu = 0.1$ is the assumed aspect ratio of the CPD" (Estimating the CPD dust mass)
   - assumption: kappa=3.5 cm2/g; gas-to-dust 100; CPD inclination equals circumstellar disk  
  > "a dust opacity of 3.5 cm$^{2}$ g$^{-1}$ (cite: Keppler2019)" (Estimating the CPD dust mass)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.1.1: self-calibration and imaging  
  > "The self-calibration and imaging was performed in CASA 5.1.1" (Observations)
- **tclean** : continuum imaging  
  > "Using the task `tclean`, we generated an image of the continuum emission" (Self-calibration of 2015.1.00888.S data)
- **gaincal** : phase gain solutions  
  > "Using the task `gaincal` we calculated phase gains" (Self-calibration of 2015.1.00888.S data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| PDS 70 c_smm peak intensity (robust image) | 106 | 19 | uJy/beam | 3 | PDS 70 c$_{smm}$ has a peak intensity of 106$\pm$19 $\mu$Jy beam$^{-1}$ (snr $\sim5.6$) |
| PDS 70 b_smm peak intensity (natural image) | 100 | 18 | uJy/beam | 3 | peak intensity of 100$\pm$18 $\mu$Jy beam$^{-1}$ (snr $\sim5.5$) |
| Offset of b_smm from PDS 70 b | 0.074 | 0.013 | arcsec | 3 | at an angular distance of 0.074$''$$\pm$0.013$''$ |
| CPD dust mass of PDS 70 c | 2e-3 to 4.2e-3 | not stated | Earth masses | 4 | dust mass between $2\times10^{-3}$ M$_\Earth$ and $4.2 \times 10^{-3}$ M$_\Earth$ |
| Ring flux density | 177 | not stated | mJy | 1 | and a flux density of 177 mJy |
| Disk inclination | 52 | not stated | deg | 1 | the measured aspect ratio implies a disk inclination of 52$^\circ$ |

## Qualitative findings

- Dust spur is a compact source at the position of PDS 70 c, separated from the ring  
  > "the dust spur identified by (cite: Keppler2019) is a compact source of emission spatially separated from the dust ring" (Introduction)

## Claim tuples

- H: Does sub-mm emission trace dust at PDS 70 c? | E: Re-calibrated ALMA Band 7 data with self-calibration; compared positions to NIR/optical | R: Unresolved 106 uJy source at the position of PDS 70 c | F: Likely a circumplanetary disk with Md 2-4.2e-3 Earth masses | **supported**
- H: Is there emission associated with PDS 70 b? | E: Astrometric comparison with SPHERE | R: Source 0.074" SW of b | F: Nature unclear (possibly L5 trapped dust) | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: b_smm may be dust trapped at L5 or jet emission rather than a CPD  
  > "PDS 70 b$_{smm}$ traces dust particles trapped at the Lagrangian point L5" (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Dust opacity uncertain; mass could be several times larger if grains <100 um  
  > "the dust mass might be a factor of several larger" (Discussion)
- Limitation (authors): ALMA reference position may not be the star  
  > "the ALMA reference position might not correspond to the position of the central star" (4.1)
- Caveat (inferred, ours): Detections are only ~4-6 sigma
- Caveat (inferred, ours): Mass depends on assumed temperature, opacity and unknown planet luminosity
- Caveat (inferred, ours): Star position assumed at disk center

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: Data are archival ALMA projects; self-cal script online  
  > "can be reproduced using the python script available at <http://obelix.rice.edu/~ai14/PDS70/>" (Self-calibration)
- Code: CASA 5.1.1 self-calibration script at obelix.rice.edu/~ai14/PDS70/  
  > "can be reproduced using the python script available at <http://obelix.rice.edu/~ai14/PDS70/>" (Self-calibration)
- Missing: Exact final-image clean parameters
- Missing: Corrected 2016 flux calibrator value
- Data volume (inferred): tens of GB
- Score (inferred): 4/5, Public data, script released and detailed self-cal; some final imaging and model details missing.
- Rediscovery candidate: yes, Public archival data, released script, numeric results.

## Links

- Method: Andrews2018 (imaging and self-calibration procedure)
- Method: Isella2014 (CPD flux model)
- Method: Teague2019 (Keplerian center fit)
- Companion: Keppler2019 (previous ALMA analysis of same data)
- Companion: Haffert2019 (MUSE detection of PDS 70 c)

## Checks

```json
{
 "quotes": 60,
 "quotes_ok": 60,
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
  "facts": 76,
  "stated": 46,
  "rate": 0.605
 },
 "evidence_ok": true
}
```
