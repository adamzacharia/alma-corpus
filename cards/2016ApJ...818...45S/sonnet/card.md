# The Inner Debris Structure in the Fomalhaut Planetary System

`2016ApJ...818...45S` | The Astrophysical Journal 2016 | first author: Su, Kate Y. L. | arXiv: 1512.03535 | DOI: 10.3847/0004-637X/818/1/45

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: debris_disks
- Question: What is the nature of the warm (ice-line) excess in the inner Fomalhaut system, and what does ALMA 870 um imaging constrain about an inner asteroid-belt analog?  
  > "The high angular resolution and sensitivity of the ALMA data enable us to place strong constraints on the nature of the warm excess revealed by *Spitzer* and *Herschel* observations." (abstract)
- Target **Fomalhaut**: coordinates RA=22:57:39.409, Dec=-29:37:22.423 (proper-motion corrected)  
  > "Due to its proximity (7.7 pc) and luminosity (17.4 L$_{\ensuremath{\odot}}$)" (Introduction); "The phase center is located at the star position (RA=22:57:39.409, Dec=$-$29:37:22.423) corrected for proper motion at the epoch of the observation." (2 Observations and Data Reduction); z/distance 7.7 pc  
  > "Due to its proximity (7.7 pc) and luminosity (17.4 L$_{\ensuremath{\odot}}$)" (Introduction); "The phase center is located at the star position (RA=22:57:39.409, Dec=$-$29:37:22.423) corrected for proper motion at the epoch of the observation." (2 Observations and Data Reduction); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00238.S
- bands: Band 7 (870 um, 345 GHz)  
  > "in five execution blocks at band 7" (2 Observations and Data Reduction)
- frequencies and spectral setup: Four 2-GHz wide spectral windows centered at 337.987, 339.924, 350.002, 352.002 GHz  
  > "Four 2-GHz wide spectral windows centered at 337.987 GHz, 339.924 GHz, 350.002 GHz and 352.002 GHz were used to measure the continuum emission" (2 Observations and Data Reduction)
- continuum bandwidth: effective 8 GHz centered at 345 GHz  
  > "A final image with effective bandwidth of 8 GHz centered at 345 GHz was generated." (2 Observations and Data Reduction)
- arrays: ALMA 12-m array  
  > "Fomalhaut was observed with the ALMA 12-m array in Cycle 1" (2 Observations and Data Reduction)
- configurations: _not stated_
- baselines: uv-coverage 23.0 to 737.7 kilolambda  
  > "The overall $uv$-coverage ranges from 23.0 k$\lambda$ to 737.7 k$\lambda$." (2 Observations and Data Reduction)
- angular resolution: 0.45" x 0.37", PA 82.3 deg  
  > "The synthesized beam is 0.45$''$$\times$0.37$''$ with position angle (P.A.) of 82.3$^\circ$." (2 Observations and Data Reduction)
- max recoverable scale: ~9"  
  > "Thus, our data are not sensitive to smooth emission structures larger than $\sim$9$''$." (2 Observations and Data Reduction)
- sensitivity: rms 26 uJy/beam  
  > "The rms noise in the final mfs image is 26 $\mu$Jy beam$^{-1}$." (2 Observations and Data Reduction)
- time on source: 172 minutes  
  > "A total on-source time of 172 minutes was achieved." (2 Observations and Data Reduction)
- observing dates: 2014 Apr 29, May 21, May 26  
  > "X4a7  | 2014 Apr 29" (Table 1)
- pi or archival as stated: _not stated_
- Other facility **Spitzer/Herschel/VLTI/Keck Nuller (literature data)**: Excess measurements at 2, 8-13, 24, 70 um and IRS spectrum used to constrain SED models  
  > "we review all the available measurements that can be used to constrain the excess properties of the inner 20 AU region in Fomalhaut." (4.1 Properties of Inner 20 AU Excess in Fomalhaut)
- External data: Photospheric output 2.96 Jy at MIPS 24 um  
  > "determined the stellar photospheric output to be 2.96 Jy in the MIPS 24 ${\rm \mu m}$ band." (3.2) [from (cite: su13)]
- External data: alpha Cen A ALMA flux 26.1+/-0.2 mJy  
  > "The measurement of 26.1$\pm$0.2 mJy for $\alpha$ Cen A from (cite: liseau15)" (3.2) [from (cite: liseau15)]
- External data: KIN 8-13 um excess 0.35%+/-0.10% and VLTI K-band excess 0.88%+/-0.12%  
  > "$K$-band excess of 0.88%$\pm$0.12% ((cite: absil09), hereafter the VLTI measurement) and 8–13 ${\rm \mu m}$ excess of 0.35%$\pm$0.10%" (4.1) [from (cite: absil09); (cite: mennesson13)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.2.1  
  > "All the data reduction and imaging processes were carried out with CASA 4.2.1" (2 Observations and Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J2258-279 in all execution blocks  
  > "The quasar J2258$-$279 was used as the amplitude calibrator in all execution blocks." (2 Observations and Data Reduction)
- flux scale uncertainty: 10%  
  > "The flux uncertainty is estimated to be 10%." (2 Observations and Data Reduction)
- self calibration: _not stated_

### Imaging

- task: multi-frequency synthesis imaging in CASA  
  > "The final continuum image was obtained by performing multi-frequency-synthesis (mfs) imaging." (2 Observations and Data Reduction)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Clean boxes on expected cold belt (from HST image) and central 5"  
  > "Clean boxes of the expected cold belt location (generated with reference to the *HST* image) and the central 5$''$ for the warm belt, were used" (2 Observations and Data Reduction)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.45" x 0.37", PA 82.3 deg  
  > "The synthesized beam is 0.45$''$$\times$0.37$''$ with position angle (P.A.) of 82.3$^\circ$." (2 Observations and Data Reduction)
- final rms: 26 uJy/beam  
  > "The rms noise in the final mfs image is 26 $\mu$Jy beam$^{-1}$." (2 Observations and Data Reduction)

### Inherited from earlier work

- Photospheric flux at 24 um (2.96 Jy) and PSF-subtraction excess methods  
  > "determined the stellar photospheric output to be 2.96 Jy in the MIPS 24 ${\rm \mu m}$ band." (3.2) [from (cite: su13)]
- Hot nano-grain ring model and magnetic trapping  
  > "a hot ($\sim$1500 K) ring produced by the magnetically trapped nano grains proposed by Rieke et al. (2015, accepted)" (4.3.1) [from (cite: rieke15)]
- Low/high collision P-R disk formalism (k=1/7 scaling)  
  > "one can simply scale the $\eta_0$ value by a multiplicative factor $k$ where $k=$ 1/7" (4.3.1) [from (cite: kennedy15); (cite: vanlieshout14); (cite: wyatt05)]

### Not stated but needed to reproduce (our reading)

- Weighting/robust, cell size, image size, clean threshold and niter not given
- Initial data reduction route (pipeline vs manual script) and calibrator flux values not given
- uvmodelfit starting parameters
- Exact SED fitting procedure/goodness of fit for the SED and KIN null comparison
- simobserve configuration and integration settings

## Analysis recipe

1. **Image continuum and fit stellar point source**: MFS imaging; fit single point source in uv plane with uvmodelfit, subtract, make residual map  
  > "we fitted a single point source model to the data and subtracted it from the original data in the $uv$ plane, then generated the residual map." (3.1)
   - software: CASA, uvmodelfit
   - fitting: _not stated_
   - validation: Flux compared with Rayleigh-Jeans photosphere and solar-analog calibration via alpha Cen A  
  > "To verify the calibration, we used the solar analog method" (3.2)
2. **SED model of warm asteroid belt and ALMA upper limit**: Optically thin narrow-ring SED model fit to data beyond 10 um; flux limit from number of beams around ring times 3 sigma rms  
  > "a narrow ring of 9 (13) AU would cover $\sim$13 (17) beams in its circumference in our cycle 1 map." (4.2)
   - parameter: Astronomical silicates, blowout size ~2.5-5 um, max grain 1 mm, ring width 2 AU, Gaussian profile, slope -3.5 to -3.7  
  > "We further assume the warm dust belt is confined in a narrow ring (NR) with a fixed width of 2 AU." (4.2)
   - assumption: Inner belt inclined 66 deg like outer belt  
  > "Assuming the inner belt is inclined by 66$^\circ$ from face-on like the outer cold belt" (4.2)
   - fitting: _not stated_
   - validation: Simulated 13 AU belt observation with simobserve, noise tuned to 26 uJy/beam  
  > "We then added the random thermal noise by adjusting the PWV parameters in $simobserve$ until the measured noise level reaches 26 $\mu$Jy beam$^{-1}$" (4.2)
3. **Model inner debris (asteroid belt + P-R disk + pile-up + hot ring) against SED and KIN nulls**: Construct SED for each component, adjust scalings, simulate 7-14 um images and compute KIN null levels vs observed  
  > "Using these model images, we then compute the expected null levels on the given dates and baselines of the KIN observations" (4.3.1)
   - parameter: Table 2 component parameters  
  > "Asteroid Belt | Silicates | 5 | 1000 | $-$3.65 | Gaussian Ring | 13 | 2" (Table 2)
   - assumption: Inner structures share cold belt i=66 deg, PA=156 deg  
  > "Assuming that the inner dust structures have the same inclination and position angles as the cold belt ($i$=66$^\circ$ and P.A.=156$^\circ$)" (4.3.1)
   - fitting: _not stated_
   - validation: Comparison of model optical depth with low and high collision theory and Lebreton model  
  > "Figure [5](#complex_model_optdepth) shows the model optical depth distribution for two of the fits in comparison with the theoretical values" (4.3.1)

## Software

- **CASA** 4.2.1: Data reduction, imaging, uvmodelfit, simobserve  
  > "All the data reduction and imaging processes were carried out with CASA 4.2.1" (2 Observations and Data Reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Point-source flux at star position | 1.789 | 0.037 (fit only) | mJy | 1 | a total flux of 1.789$\pm$0.037 mJy |
| Image rms | 26 | not stated | uJy/beam | 1 | The rms noise in the final mfs image is 26 $\mu$Jy beam$^{-1}$. |
| 3 sigma upper limit of inner belt flux | 1 (9 AU ring) and 1.3 (13 AU ring) | not stated | mJy at 870 um | 2 | the corresponding 3$\sigma$ upper limit for the whole inner belt is 1 mJy and 1.3 mJy at 870 ${\rm \mu m}$ for such rings. |
| Unresolved 24 um excess | 0.64 | 0.13 | Jy | 0 | We find the unresolved excess at 24 ${\rm \mu m}$ is 0.64$\pm$0.13 Jy |
| Dominant excess blackbody temperature | ~170 | not stated | K | 0 | the inner warm emission is best described by a blackbody emission of $\sim$170 K |
| ALMA vs solar-analog calibration offset | 10.7 | 7 | % | 0 | the solar analog calibration is brighter than the ALMA measurement by 10.7$\pm$7% |
| Asteroid belt radial location | ~8-15 | not stated | AU | 2 | indicates a radial location in the range $\sim$8–15 AU |

## Qualitative findings

- ALMA detects a point source at the star consistent with the stellar photosphere and no >3 sigma structure in the central 15x15 AU  
  > "No structures that are brighter than 3$\sigma$ are detected in the central 15 AU$\times$15 AU region." (abstract)

## Claim tuples

- H: Warm excess arises from compact free-free stellar wind emission | E: Compare ALMA 870 um stellar flux with photospheric extrapolation | R: Point source flux 1.789 mJy is below the 2.2 mJy Rayleigh-Jeans prediction | F: Compact free-free emission ruled out | **supported**
- H: Warm excess is an ice-line asteroid belt analog | E: Optically thin SED modeling and ALMA upper limit | R: Belt at ~8-15 AU, 3 sigma flux <1.3 mJy | F: Consistent with an asteroid-belt analog at the ice line | **supported**
- H: Inner hot excesses are linked to the belt via P-R drag, sublimation and trapped nano grains | E: Four-component SED and KIN null modeling | R: Good fits to SED and KIN | F: Coherent model proposed | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Stellar wind free-free origin (Acke et al.) and Lebreton et al. models compared and disfavored  
  > "rules out any compact free-free emission originating from the star" (3.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Putative 13-AU belt needs deeper data; SED models degenerate due to lack of Rayleigh-Jeans constraints  
  > "Nevertheless, a deeper map is needed to confirm this putative 13-AU belt." (4.2)
- Caveat (inferred, ours): Many model parameters fixed by assumption; no formal fit statistics or uncertainties
- Caveat (inferred, ours): ALMA calibration 10% uncertainty comparable to photosphere discrepancy
- Caveat (inferred, ours): Inner belt orientation assumed equal to outer belt

## Reproducibility

- Data public (paper): Archive data cited with ALMA project code 2012.1.00238.S (ADS/JAO.ALMA)  
  > "This paper made use of the following ALMA data: ADS/JAO.ALMA 2012.0.00238.S (PI: S.P.L.)." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters (weighting, cell, threshold)
- Missing: SED model code and fitting details
- Missing: KIN null computation details
- Data volume (inferred): ~10-50 GB (five 12-m EBs, 4 continuum spws)
- Score (inferred): 3/5, Simple imaging and point-source fit reproducible, but imaging parameters and modeling code are missing.
- Rediscovery candidate: no, Key ALMA numbers (flux, rms) are reproducible but imaging settings are incomplete and main conclusions rely on unspecified SED modeling.

## Links

- Method: (cite: wyatt05) (P-R drag analytic optical depth formulae)
- Method: (cite: vanlieshout14) (Numerical P-R drag with collisional size distribution)
- Method: (cite: kennedy15) (Optical depth scaling for P-R disks)
- Companion: (cite: su13) (Previous Fomalhaut inner-disk SED analysis)
- Companion: (cite: rieke15) (Magnetically trapped nano grain hot ring)
- Companion: (cite: boley12) (ALMA cycle 0 Fomalhaut image)

## Checks

```json
{
 "quotes": 56,
 "quotes_ok": 56,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2012.0.00238.S"
 ],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 67,
  "stated": 42,
  "rate": 0.627
 },
 "evidence_ok": true
}
```
