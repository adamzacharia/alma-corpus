# Protoplanetary disk masses in NGC 2024: Evidence for two populations

`2020A&A...640A..27V` | Astronomy and Astrophysics 2020 | first author: van Terwisga, S. E. | arXiv: 2004.13551 | DOI: 10.1051/0004-6361/201937403

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: How does external photoevaporation and environment affect the dust masses of disks across the young NGC 2024 cluster, compared with other star-forming regions?  
  > "By studying how the disk mass varies within the cluster, and comparing these disks to those in other regions, we aim to determine how external photoevaporation influences disk properties over time." (abstract)
- Target **NGC 2024 (mosaic centered on FIR 3)**: coordinates 05h41m40.5s, -01d54m16.25s (J2000)  
  > "The full mosaic consists of 149 pointings, centered on $05^\mathrm{h}41^\mathrm{m}40.5^\mathrm{s}$, $-01^\circ54{}^\prime16.25{}^{\prime\prime}$ (J2000)." (2 ALMA observations and data reduction); "we take the distance $d$ to NGC 2024 to be 414 pc (cite: menten07; bailerjones18)" (3.2 Dust masses of NGC 2024 disks); z/distance 414 pc  
  > "The full mosaic consists of 149 pointings, centered on $05^\mathrm{h}41^\mathrm{m}40.5^\mathrm{s}$, $-01^\circ54{}^\prime16.25{}^{\prime\prime}$ (J2000)." (2 ALMA observations and data reduction); "we take the distance $d$ to NGC 2024 to be 414 pc (cite: menten07; bailerjones18)" (3.2 Dust masses of NGC 2024 disks); distance from Menten et al. 2007; Bailer-Jones et al. 2018  
  > "The full mosaic consists of 149 pointings, centered on $05^\mathrm{h}41^\mathrm{m}40.5^\mathrm{s}$, $-01^\circ54{}^\prime16.25{}^{\prime\prime}$ (J2000)." (2 ALMA observations and data reduction); "we take the distance $d$ to NGC 2024 to be 414 pc (cite: menten07; bailerjones18)" (3.2 Dust masses of NGC 2024 disks)

## Data provenance

- ALMA projects: 2017.1.01102.S
- bands: Band 6, mosaic of 149 pointings, 2.9' x 2.9'  
  > "consist of a Band 6 mosaic of a $2.9' \times 2.9'$ square region." (2 ALMA observations and data reduction)
- frequencies and spectral setup: Continuum spws at 230 and 219 GHz (effective 225 GHz); three line spws with 122 kHz channels for 12CO, 13CO, C18O J=2-1  
  > "The spectral setup of the observations covers the millimeter-continuum with two spectral windows centered at 230 GHz and 219 GHz." (2 ALMA observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 10-1700 kλ  
  > "The data span baselines from $10 - 1700$ k$\lambda$." (2 ALMA observations and data reduction)
- angular resolution: 0.26" x 0.18" (full baseline); 0.22" x 0.15" (>150 kλ)  
  > "The effective beam shape is $0.26^{\prime\prime} \times 0.18^{\prime\prime}$ (full width at half maximum) for the full baseline image." (2 ALMA observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: rms 0.052 mJy/beam (full); 0.058 mJy/beam (>150 kλ)  
  > "In the most sensitive part of the image, the rms noise is 0.052 mJy beam$^{-1}$." (2 ALMA observations and data reduction)
- time on source: _not stated_
- observing dates: Eight visits, starting 23 December 2017 to January 2018  
  > "Flux over time for J054141.3-015332, starting December 23, 2017." (Table 3)
- pi or archival as stated: PI R. Mann program  
  > "ALMA program 2017.1.01102.S (PI: R. Mann)" (2 ALMA observations and data reduction)
- Line: 12CO J=2-1 (not stated)
- Other facility **Herschel PACS 160 um**: Contours used to define the east/west division and show the ridge  
  > "detections and nondetections are shown against both the ALMA data and Herschel PACS 160 $\mu$m contours (cite: stutz13)" (4.1 Two disk populations across the NGC 2024 core region)
- External data: Catalog of infrared-excess objects (JHK) defining the 179-disk sample  
  > "we used the catalog of infrared-excess objects from (cite: meyer96), which were identified by their JHK colors." (3.1 A 1.3 mm catalog of disks in NGC 2024) [from (cite: meyer96)]
- External data: HOPS protostar catalog used to reject Class 0 sources  
  > "we cross-referenced the (cite: meyer96) catalog with the Herschel Orion Protostars Survey (HOPS) catalog of protostars in Orion (cite: furlan16)." (3.1 A 1.3 mm catalog of disks in NGC 2024) [from (cite: furlan16)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Amplitude and bandpass: J0432-0120; phase: J0541-0211  
  > "amplitude and bandpass calibration were carried out on J0432-0120 and phase calibration was performed on J0541-0211." (2 ALMA observations and data reduction)
- flux scale uncertainty: 10% absolute flux calibration  
  > "These errors do not include the standard (absolute) flux calibration accuracy of $10\%$." (3.1 A 1.3 mm catalog of disks in NGC 2024)
- self calibration: Phase-only self-cal on each integration of the mosaic separately  
  > "Each integration of the mosaic was separately self-calibrated for phase only." (2 ALMA observations and data reduction)

### Imaging

- task: CASA 5.4.0 tclean  
  > "Images of the data were made in `CASA` 5.4.0, using the *tclean* task." (2 ALMA observations and data reduction)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 1.0  
  > "we used Briggs weighting, with a robust parameter of $1.0$" (2 ALMA observations and data reduction)
- uv taper: Second image with only baselines >150 kλ  
  > "another image was generated where only baselines $>150$ k$\lambda$ were included." (2 ALMA observations and data reduction)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Channels with strong line emission flagged  
  > "The images presented here have been made after flagging the channels with strong line emission." (2 ALMA observations and data reduction)
- line free channels: _not stated_
- primary beam correction: Noise weighted by primary-beam coverage computed by tclean  
  > "weighting the noise estimated in an empty part of the image with the primary-beam coverage, as calculated by *tclean*." (2 ALMA observations and data reduction)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.26"x0.18" (full), 0.22"x0.15" (long baseline)  
  > "For the long-baseline image, the effective beam shape is $0.22^{\prime\prime} \times 0.15^{\prime\prime}$." (2 ALMA observations and data reduction)
- final rms: 0.052 mJy/beam (full), 0.058 mJy/beam (long baseline)  
  > "After restricting the baseline coverage to baselines $>150$ k$\lambda$, the noise increased to 0.058 mJy beam$^{-1}$." (2 ALMA observations and data reduction)

### Inherited from earlier work

- Dust mass assumptions (T=20 K, kappa, beta=1) for comparison with other surveys  
  > "$T_{\text{eff}} = 20$ K (cite: andrews05), and $\kappa_{\nu} = \kappa_0 \left( \nu / \nu_0 \right)^{\beta}$ with $\beta = 1$" (3.2 Dust masses of NGC 2024 disks) [from Andrews & Williams 2005 (cite: andrews05); Beckwith 1990 (cite: beckwith90)]

### Not stated but needed to reproduce (our reading)

- tclean cell size, image size, deconvolver, threshold and masks
- Line-free channels flagged
- Self-calibration solution intervals and reference antenna
- Details of aperture photometry (aperture size, background)
- Which Kaplan-Meier implementation was used
- How spectral indices of IRS 2 and IRC 101 were computed
- CASA calibration pipeline version and manual vs pipeline calibration

## Analysis recipe

1. **Image continuum**: tclean Briggs imaging of full and >150 kλ baselines after phase-only self-calibration  
  > "another image was generated where only baselines $>150$ k$\lambda$ were included." (2 ALMA observations and data reduction)
   - software: CASA
   - parameter: robust = 1.0; first visit excluded from images used for masses  
  > "the data from this first integration were not used for creating the images from which we derive the dust masses of disks." (2 ALMA observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure fluxes of catalog sources**: Aperture photometry on brightest >3σ point source within 1" of catalog position in long-baseline image; else flux in 0.25" beam at catalog position  
  > "If no source was found, the flux was measured in a $0.25''$ beam on the catalog position." (3.1 A 1.3 mm catalog of disks in NGC 2024)
   - fitting: _not stated_
   - validation: Catalog checked manually and tested for extended emission in full-baseline image  
  > "The resulting millimeter catalog was checked manually, and tested for the presence of extended emission in the full-baseline image." (3.1 A 1.3 mm catalog of disks in NGC 2024)
3. **Convert flux to dust mass and derive mass distribution**: Optically thin relation M = d^2 F/(kappa B(T)); Kaplan-Meier estimator including nondetections  
  > "the Kaplan-Meier estimator is used to infer the disk mass distribution for the full sample, including nondetections." (3.2 Dust masses of NGC 2024 disks)
   - parameter: d = 414 pc, T = 20 K, kappa(1000 GHz) = 10 cm2/g, beta = 1  
  > "$\kappa_{1000\,\text{GHz}} = 10$ cm$^{2}$ g$^{-1}$ (cite: beckwith90)" (3.2 Dust masses of NGC 2024 disks)
   - assumption: Optically thin emission, no free-free contamination, 20 K midplane (40 K tested)  
  > "The size of this effect is shown in Fig. [2](#fig:mdisk_v1) for a 40 K effective midplane temperature" (3.2.2 Impact of midplane temperature variations)
   - fitting: _not stated_
   - validation: Free-free contribution estimated negligible using spectral indices 2.3 and -0.1  
  > "assuming spectral indices of $2.3$ for the dust and $-0.1$ for the free-free emission" (3.2.1 Impact of free-free emission)
4. **Search for new sources and stack nondetections**: Blind search for >4.8σ peaks checked in both images; weighted stack of 122 nondetections with detections masked  
  > "These sources were first identified by performing a blind search for $>4.8\,\sigma$ peaks in the data" (3.2.3 Point sources without near infrared counterparts)
   - fitting: _not stated_
   - validation: 4.8σ chosen to give <1 expected false positive (0.6)  
  > "we expect less than one false positive given the number of independent beams in the full image (0.6 on average)." (3.2.3 Point sources without near infrared counterparts)
5. **Compare east and west subsamples**: Log-rank test on Kaplan-Meier distributions of two subsamples split by a line; comparison with other regions  
  > "Using a log-rank test, we then tested if it is possible to reject the null hypothesis that there is no difference in disk masses between the samples." (4.1 Two disk populations across the NGC 2024 core region)
   - parameter: Dividing line between 5:41:44.189 -1:55:39.94 and 5:41:38.665 -1:53:00.27  
  > "The subsamples are divided by a line between 5:41:44.189 -1$^{\circ}$55’39.94” and 5:41:38.665 -1$^{\circ}$53’00.27” (J2000)." (4.1 Two disk populations across the NGC 2024 core region)
   - fitting: _not stated_
   - validation: Results robust to dividing line within 10 deg and 0.5' west  
  > "they hold so long as the dividing line lies within $10^{\circ}$ of its presently defined angle, and less than $0.5'$ to the west of its current position." (4.1 Two disk populations across the NGC 2024 core region)

## Software

- **CASA** 5.4.0: Imaging with tclean and Gaussian fits with imfit  
  > "Images of the data were made in `CASA` 5.4.0, using the *tclean* task." (2 ALMA observations and data reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Overall disk detection rate | 32 | 4% | percent | 2 | Of the 179 objects in the sample, 57 are detected, with an overall detection rate of $32 \pm 4\%$. |
| Detection rate East | 45 | 7% | percent | 5 | a detection rate of $45 \pm 7\%$ |
| Detection rate West | 15 | 4% | percent | 5 | only $15 \pm 4\%$ of disks in the western part of the image are detected. |
| Log-rank p-value East vs West | 2.0e-6 | not stated | dimensionless | 5 | ($p = 2.0 \times 10^{-6}$) |
| Stacked nondetection 3σ limit | 20 uJy (<0.96 M_Mars) | not stated | uJy | 4 | The resulting $3\sigma$ mass limit for the stacked sources is $20\,\mu$Jy, or $< 0.96\,M_{\text{Mars}}$. |
| IRC 101 flux | 204 ± 1.1 | 1.1 mJy | mJy | 2 | The brightest source in the field, IRC 101, has a flux of $204 \pm 1.1$ mJy. |
| Flare peak flux of U10 (J054141.3-015332) | 176.9 | 0.5 | mJy | 2 | / 12/23 / 04:56:01 / $176.9 \pm 0.5$       / |

## Qualitative findings

- IRC 101 is a giant (~300 AU radius) transition-disk-like ring with an asymmetric ring  
  > "the ring’s peak intensity is at a radius of $\sim 300$ AU, making it the largest such object identified so far." (3.3.1 IRC 101: A 300 AU-radius dust ring around a YSO)
- Millimeter flare from an X-ray bright YSO fading by factor 26 within 24 hours  
  > "It then fades by a factor of 26 to $6.8 \pm 0.36$ mJy within 24 hours" (3.3.5 Bright flaring object at 225 GHz)

## Claim tuples

- H: Are there distinct disk populations in NGC 2024? | E: Split sample east/west and compare mass distributions with log-rank test | R: p = 2e-6; detection rates 45% vs 15% | F: Two disk populations: young shielded east, older and more exposed west | **supported**
- H: Do NGC 2024 East disk masses resemble those in other regions? | E: Log-rank comparison with Lupus, OMC-2 and others | R: Cannot be distinguished from Lupus or OMC-2 | F: East masses similar to isolated 1-3 Myr regions | **supported**
- H: Is the west population low in mass due to external photoevaporation? | E: Compare to Upper Sco, Corona Australis, Trapezium | R: Resembles Upper Sco and CrA; indistinguishable from Trapezium | F: Age plus photoevaporation likely, but initial low masses possible | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Briggs robust 1.0 chosen for best SNR and compact beam  
  > "for the best image signal-to-noise ratio (SNR) and a compact beam shape" (2 ALMA observations and data reduction)
- Alternative: Disk masses might be overestimated or disks optically thick; flux axis shown free of opacity assumptions  
  > "we therefore also show a flux axis in the disk mass distribution plots shown here, which is free from assumptions on opacities and optical depth." (3.2 Dust masses of NGC 2024 disks)
- How they decided it was enough: _not stated_
- Limitation (authors): Stellar mass differences and binarity cannot be accounted for in the comparison  
  > "we cannot take into account possible differences in stellar masses, even though these may be significant" (4.2 Comparison to other star-forming regions)
- Limitation (authors): Kaplan-Meier assumption of nondetection independence not met at low masses  
  > "The third requirement is not met" (3.2 Dust masses of NGC 2024 disks)
- Caveat (inferred, ours): East/west split is somewhat arbitrary and drawn by eye along a 160 um contour
- Caveat (inferred, ours): Age and extinction differences are confounded with external photoevaporation
- Caveat (inferred, ours): Catalog incompleteness differs east to west due to extinction
- Caveat (inferred, ours): Short-baseline emission from cloud may affect photometry

## Reproducibility

- Data public (paper): ALMA program 2017.1.01102.S (PI Mann); public status not stated  
  > "ALMA program 2017.1.01102.S (PI: R. Mann)" (2 ALMA observations and data reduction)
- Products in archive: _not stated_
- Missing: Imaging parameters (cell, image size, masks, deconvolver)
- Missing: Self-calibration solints
- Missing: Photometry aperture details
- Missing: Meyer 1996 catalog is a thesis, hard to obtain
- Data volume (inferred): Large: 149-pointing Band 6 mosaic, eight executions; hundreds of GB raw
- Score (inferred): 3/5, Data identified and key settings (robust, CASA version, mass assumptions) given, but many imaging and self-cal details missing and sample catalog is a thesis.
- Rediscovery candidate: no, Recipe incomplete for imaging/photometry and the source catalog is not readily available, though results are numeric.

## Links

- Method: Ansdell et al. 2016 (cite: ansdell16); van Terwisga et al. 2019 (cite: vanterwisga19) (Comparable ALMA disk survey methodology and mass assumptions)
- Companion: Mann et al. 2015 (cite: mann15) (Earlier SMA observations of NGC 2024 disks)
- Related: HOPS
- Related: MYSTiX
- Related: ALMA surveys of Lupus, Upper Sco, Corona Australis, OMC-2, sigma Orionis, ONC

## Checks

```json
{
 "quotes": 62,
 "quotes_ok": 62,
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
  "facts": 72,
  "stated": 46,
  "rate": 0.639
 },
 "evidence_ok": true
}
```
