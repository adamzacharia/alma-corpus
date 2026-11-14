# ALMA and RATIR observations of GRB 131030A

`2017PASJ...69...20H` | Publications of the Astronomical Society of Japan 2017 | first author: Huang, Kuiyun | arXiv: 1612.06481 | DOI: 10.1093/pasj/psw124

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type multi_facility_alma_minor

## Science

- Fields: transients, high_z_galaxies
- Question: Constrain the late-time 345 GHz afterglow/host emission of GRB131030A, model the forward shock with RATIR and Swift data, and assess the host galaxy and the nearby submm source  
  > "The ALMA observation constrained a deep limit at 17.1 d for the afterglow and host galaxy." (abstract)
- Target **GRB 131030A**: coordinates 23h00m16.14s, -05d22'05.2" (Swift/UVOT)  
  > "The redshift of GRB 131030A was measured at $z=1.293$ on the basis of the optical spectroscopic observation by using the Nordic Optical Telescope (cite: gcn15407)." (Introduction); z/distance z=1.293  
  > "The redshift of GRB 131030A was measured at $z=1.293$ on the basis of the optical spectroscopic observation by using the Nordic Optical Telescope (cite: gcn15407)." (Introduction); distance from Nordic Optical Telescope spectroscopy (cite: gcn15407)  
  > "The redshift of GRB 131030A was measured at $z=1.293$ on the basis of the optical spectroscopic observation by using the Nordic Optical Telescope (cite: gcn15407)." (Introduction)
- Target **ALMAJ2300-0522**: coordinates 23h00m16.326s, -05d22'07.50"  
  > "a source (ALMAJ2300-0522) with $0.716\pm0.045$ mJy was identified in the ALMA image" (2.1 ALMA Submillimeter Follow-up Observation); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00875.T
- bands: 345 GHz (default continuum setup)  
  > "We used ALMA to observe the afterglow at 345-GHz (default continuum setup) with the C32-5 configuration under the Cycle 1 open-use mode." (2.1 ALMA Submillimeter Follow-up Observation)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C32-5  
  > "with the C32-5 configuration under the Cycle 1 open-use mode" (2.1 ALMA Submillimeter Follow-up Observation)
- baselines: _not stated_
- angular resolution: 0.252"x0.207", PA 68.2 deg  
  > "The resulting synthesized beam sizes were $0.252\ensuremath{''}\times0.207\ensuremath{''}$ with a position angle of 68.2 deg." (2.1 ALMA Submillimeter Follow-up Observation)
- max recoverable scale: _not stated_
- sensitivity: 3-sigma limit 0.12 mJy at the afterglow position  
  > "No source was observed from the location of the optical afterglow to the 3$-\sigma$ limit of 0.12 mJy" (2.1 ALMA Submillimeter Follow-up Observation)
- time on source: 53 min on-source, 90 min total  
  > "The on-source time and total observing time were 53 min and 90 min, respectively." (2.1 ALMA Submillimeter Follow-up Observation)
- observing dates: 2013 November 16, 23:11 UT (17.12 d after the GRB)  
  > "the 345-GHz observation was initiated at 23:11 UT on 2013 November 16 (17.12 d after the GRB)." (2.1 ALMA Submillimeter Follow-up Observation)
- pi or archival as stated: _not stated_
- Other facility **RATIR (1.5 m Harold L. Johnson Telescope)**: r, i, Z, Y, J, H optical/NIR afterglow light curves  
  > "We used the Reionization and Transients InfraRed camera (RATIR) to monitor the afterglow in *r-*, *i-*, *Z-*, *Y-*, *J-* and *H-*bands" (2.2 Optical and Near Infrared Afterglow Follow-ups)
- Other facility **Swift (BAT, XRT, UVOT)**: Burst detection, X-ray light curve, UVOT data  
  > "The afterglow in X-ray and optical bands was also identified using the *Swift* X-ray Telescope (XRT) and Ultraviolet/Optical Telescope (UVOT)." (Introduction)
- Other facility **SUBARU Suprime-Cam**: Archival Rc-band image for host and ALMA source counterpart  
  > "We reduced the SUBARU Suprime-Cam images obtained from the SMOKA archive system (cite: smoka)." (2.5 SUBARU Archive Image and Host Galaxy)
- Other facility **Mt. Lemmon 1-m telescope (KASI)**: B and R band follow-up  
  > "We also conducted the *B-* and *R-*band follow-up observations by using the robotic 1-m telescope at the Mt. Lemmon observatory" (2.2 Optical and Near Infrared Afterglow Follow-ups)
- External data: X-ray light curve from online repository  
  > "The X-ray data were obtained from the online data repository prepared by (cite: butler07)." (2.3 Afterglow Lightcurve) [from (cite: butler07)]
- External data: Template infrared SED library  
  > "a template infrared SED, which we obtained from the library provided by (cite: ce01)." (4.2 Host Galaxy and ALMAJ2300-0522) [from (cite: ce01)]

## Processing

### Calibration

- pipeline or manual: Standard CASA procedure  
  > "The raw data were calibrated using the Common Astronomy Software Applications 4.1 (CASA, (cite: casa)) with the standard procedure" (2.1 ALMA Submillimeter Follow-up Observation)
- casa version: CASA 4.1  
  > "The raw data were calibrated using the Common Astronomy Software Applications 4.1" (2.1 ALMA Submillimeter Follow-up Observation)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J2232+117 (flux), J2148+0657 (bandpass), J2301-0158 (phase)  
  > "Three calibrators (J2232+117, J2148+0657, and J2301$-$0158) for flux, bandpass, and phase calibrations, respectively, were also observed." (2.1 ALMA Submillimeter Follow-up Observation)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean  
  > "final CLEANed images were made using the “clean” task" (2.1 ALMA Submillimeter Follow-up Observation)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "a robust briggs weighting (robust parameter of 0.5)" (2.1 ALMA Submillimeter Follow-up Observation)
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
- final beam: 0.252"x0.207", PA 68.2 deg  
  > "The resulting synthesized beam sizes were $0.252\ensuremath{''}\times0.207\ensuremath{''}$ with a position angle of 68.2 deg." (2.1 ALMA Submillimeter Follow-up Observation)
- final rms: _not stated_

### Inherited from earlier work

- IR SED redshifting method for L_IR upper limit  
  > "Following (cite: wang12), we applied a redshifting to a template infrared SED" (4.2 Host Galaxy and ALMAJ2300-0522) [from (cite: wang12)]
- SFR conversion SFR=1.7e-10 L_IR/Lsun  
  > "SFR($M\solar$ yr$^{-1})=1.7\times10^{-10} L_{IR}/L\solar$ (cite: kennicutt98) used in (cite: wang12)" (4.2 Host Galaxy and ALMAJ2300-0522) [from (cite: kennicutt98)]
- RATIR photometric calibration agreement details  
  > "agree to within $\lesssim$3 per cent (Butler et al. 2016 in prep.)" (2.2 Optical and Near Infrared Afterglow Follow-ups) [from Butler et al. 2016 in prep.]

### Not stated but needed to reproduce (our reading)

- Image size, cell size, masking and clean threshold
- Flux calibrator flux scale and its uncertainty
- Which frequency/spectral windows were used for continuum imaging
- How the template SED was selected and normalized to 345 GHz
- Boxfit fitting settings (priors, optimization, fixed parameters)
- Light-curve fitting method and extinction treatment details
- Whether primary beam correction was applied

## Analysis recipe

1. **Calibrate and image ALMA data**: Standard CASA calibration then clean with Briggs weighting  
  > "final CLEANed images were made using the “clean” task with a robust briggs weighting (robust parameter of 0.5)" (2.1 ALMA Submillimeter Follow-up Observation)
   - software: CASA
   - parameter: robust = 0.5  
  > "robust parameter of 0.5" (2.1 ALMA Submillimeter Follow-up Observation)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit afterglow light curves and SEDs**: Single and broken power-law fits to light curves; power-law fits to SEDs  
  > "To describe the light curves, we employed a single power-law function by dividing light curve data into earlier" (2.3 Afterglow Lightcurve)
   - fitting: chi-square fits, no sampler stated  
  > "We successfully fitted the single power-law function to the earlier light curves." (Afterglow Lightcurve)
   - validation: chi2/nu reported  
  > "$\beta=-0.57\pm0.09$ ($\chi^{2}/\nu=1.9$ with $\nu=8$)" (2.4 Afterglow Spectrum)
3. **Forward shock modeling**: boxfit 2D relativistic hydrodynamic jet model fit to six OIR bands and ALMA limit, ISM only  
  > "we performed forward shock synchrotron radiation modeling with the optical light curves and ALMA upper limit by using the boxfit code (cite: boxfit)." (3.1 Forward Shock Radiation and X-Ray Excess)
   - software: boxfit
   - parameter: on-axis case, theta_obs=0  
  > "We determined the optimal modeling parameters with the on-axis case (observing angle, $\theta_{obs}=0$)" (3.1 Forward Shock Radiation and X-Ray Excess)
   - assumption: homogeneous circumburst medium (ISM)  
  > "Because the code involved a two-dimensional relativistic hydrodynamical jet simulation with a homogeneous circumburst medium" (3.1 Forward Shock Radiation and X-Ray Excess)
   - fitting: _not stated_
   - validation: Compared SSC analytic prediction with X-ray data  
  > "On the basis of the analytic solution described by (cite: fan08), we calculated the expected flux density of synchrotron self-inverse-Compton radiation" (3.1 Forward Shock Radiation and X-Ray Excess)
4. **Host IR luminosity and SFR limits**: Redshift Chary & Elbaz template SED to z=1.293 and scale to ALMA 3-sigma limit; convert L_IR to SFR  
  > "We constrained the 3-$\sigma$ upper limits of IR luminosity as $L_{IR} <1.11\times10^{11} L\solar$." (4.2 Host Galaxy and ALMAJ2300-0522)
   - assumption: ALMAJ2300-0522 at same redshift as GRB  
  > "By assuming the same redshift with GRB131030A, we also obtained $L_{IR}=8.65\times10^{11} L\solar$" (4.2 Host Galaxy and ALMAJ2300-0522)
   - fitting: _not stated_
   - validation: Compared with TOUGH sample SFR  
  > "The upper limit of SFR was consistent with those of the TOUGH samples" (4.2 Host Galaxy and ALMAJ2300-0522)

## Software

- **CASA** 4.1: ALMA calibration and imaging  
  > "calibrated using the Common Astronomy Software Applications 4.1" (2.1 ALMA Submillimeter Follow-up Observation)
- **boxfit** : Forward shock modeling  
  > "by using the boxfit code (cite: boxfit)" (3.1 Forward Shock Radiation and X-Ray Excess)
- **SExtractor** : RATIR photometry  
  > "We performed photometry for individual science frames and mosaic using sextractor" (2.2 Optical and Near Infrared Afterglow Follow-ups)
- **SWarp** : image co-addition  
  > "image co-addition was achieved using swarp" (2.2 Optical and Near Infrared Afterglow Follow-ups)
- **astrometry.net** : image alignment  
  > "image alignment was conducted by astrometry.net" (2.2 Optical and Near Infrared Afterglow Follow-ups)
- **IRAF** : Mt. Lemmon reduction and Subaru centroid  
  > "A standard routine including bias subtraction and flat-fielding corrections was employed to process the data using the IRAF package." (2.2 Optical and Near Infrared Afterglow Follow-ups)
- **DAOPHOT** : aperture photometry of Mt. Lemmon images  
  > "The DAOPHOT package was used to perform aperture photometry of the GRB images." (2.2 Optical and Near Infrared Afterglow Follow-ups)
- **SDFRED** : Suprime-Cam reduction  
  > "The basic reduction of the Suprime-Cam data was performed using the SDFRED (cite: sdfred)." (2.5 SUBARU Archive Image and Host Galaxy)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA 345 GHz 3-sigma limit at afterglow position | 0.12 | not stated | mJy | 1 | to the 3$-\sigma$ limit of 0.12 mJy |
| ALMAJ2300-0522 flux density | 0.716 | 0.045 | mJy | 1 | a source (ALMAJ2300-0522) with $0.716\pm0.045$ mJy |
| Host L_IR 3-sigma upper limit | <1.11e11 | not stated | Lsun | 4 | $L_{IR}<1.11\times10^{11} L\solar$ |
| Host SFR 3-sigma upper limit | <18.7 | not stated | Msun/yr | 4 | SFR$<18.7$ ($M\solar$ yr$^{-1}$) |
| ALMAJ2300-0522 L_IR if at z=1.293 | 8.65e11 | not stated | Lsun | 4 | we also obtained $L_{IR}=8.65\times10^{11} L\solar$ and the corresponding SFR of 147 $M\solar$ yr$^{-1}$ |
| Jet break time (r-band) | 2.51e5 | 0.48e5 | s | 2 | $(2.51\pm0.48)\times10^{5}$ |
| Boxfit jet opening angle | 8.8 | not stated | deg | 3 | $\theta_{jet}=8^{\circ}.8$, $E=1.05\times10^{52}$ erg |

## Qualitative findings

- X-ray excess is inconsistent with SSC from the forward shock  
  > "The excess was inconsistent with the synchrotron self-inverse Compton radiation from the forward shock." (abstract)

## Claim tuples

- H: Is any afterglow or host emission detected at 345 GHz at the GRB position? | E: ALMA Cycle 1 observation at 17.1 d | R: 3-sigma limit 0.12 mJy; L_IR<1.11e11 Lsun, SFR<18.7 Msun/yr | F: Host is not a luminous submm galaxy; deep limit benchmarks ALMA afterglow follow-up | **supported**
- H: Can SSC explain the X-ray excess? | E: Boxfit forward shock model plus analytic SSC estimate | R: SSC does not reproduce late temporal evolution or spectrum | F: SSC is unlikely; another component such as late prompt emission is needed | **supported**
- H: Is ALMAJ2300-0522 part of the host galaxy? | E: Compare offset 3.5" with host companions in the literature | R: Offset 30.2 kpc; Rc=24.48 counterpart | F: May be a host component; redshift needed | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: SSC rejected for X-ray excess; late prompt emission and magnetar spin-down proposed  
  > "A spinning-down magnetar as the central engine is one of the explanations for the X-ray excess" (3.1 Forward Shock Radiation and X-Ray Excess)
- How they decided it was enough: _not stated_
- Limitation (authors): ALMA astrometry bugs reported; large offset not explained  
  > "Although several astrometry-related bugs (e.g. phase calibrator coordinate inconsistency) were reported from the ALMA ARC after data delivery" (2.1 ALMA Submillimeter Follow-up Observation)
- Caveat (inferred, ours): Astrometry bugs raise doubt on the ALMA source position and association
- Caveat (inferred, ours): Association of ALMAJ2300-0522 with the host rests on analogy without a redshift
- Caveat (inferred, ours): Host L_IR limit depends on a single template SED
- Caveat (inferred, ours): Boxfit fit has no stated uncertainties

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters beyond robust
- Missing: Template SED selection and scaling
- Missing: Boxfit fit configuration
- Missing: RATIR calibration paper in prep.
- Data volume (inferred): ~10-30 GB raw ALMA for one execution block, plus small optical data
- Score (inferred): 3/5, ALMA part is simple and archival but several settings are missing, and the modeling is under-described.
- Rediscovery candidate: no, Public ALMA data likely, but the recipe is incomplete and main results rely on external optical data and models.

## Links

- Method: (cite: wang12) (IR SED redshifting and SFR method)
- Method: (cite: boxfit) (forward shock modeling code)
- Companion: (cite: xrf) (earlier modeling parameters updated here)
- Related: RATIR
- Related: TOUGH

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
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 49,
  "rate": 0.598
 },
 "evidence_ok": true
}
```
