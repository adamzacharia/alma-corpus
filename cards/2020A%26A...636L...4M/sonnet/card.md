# Spirals inside the millimeter cavity of transition disk SR 21

`2020A&A...636L...4M` | Astronomy and Astrophysics 2020 | first author: Muro-Arena, G. A. | arXiv: 2003.08189 | DOI: 10.1051/0004-6361/202037656

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: Do the scattered-light and mm-continuum structures of transition disk SR 21 match planet-disk interaction models, and what does this imply for a putative embedded planet in the cavity?  
  > "In this study we discuss recent observational results in the context of hydrodynamical simulations in order to infer the properties of a putative embedded planet in the cavity of a transition disk." (abstract)
- Target **SR 21 (EM* SR 21)**: coordinates _not stated_; z/distance 138.4±1.1 pc  
  > "EM\* SR 21 (hereafter, SR 21) is a nearby (138.4$\pm$1.1 pc, (cite: 2018yCat.1345....0G)) member of the Ophiuchus star forming region." (Introduction); distance from Gaia DR2 (Gaia Collaboration 2018)  
  > "EM\* SR 21 (hereafter, SR 21) is a nearby (138.4$\pm$1.1 pc, (cite: 2018yCat.1345....0G)) member of the Ophiuchus star forming region." (Introduction)

## Data provenance

- ALMA projects: 2017.1.00884.S
- bands: Band 3 (3 mm) new; Band 7 (343 GHz) and Band 9 (690 GHz) archival  
  > "We also use the data presented in Pinilla et al. 2015 in Band 9 (690 GHz) and Band 7 (343 GHz) from Cycle 0 and Cycle 1 ALMA observations" (2.2 Data reduction)
- frequencies and spectral setup: Two line spws (13CO and C18O J=1-0) plus two continuum spws centered at 108 GHz (TDM 1875 MHz; FDM 937.5 MHz)  
  > "and two spectral windows for the continuum, centered at 108 GHz." (2.1 Observations)
- continuum bandwidth: _not stated_
- arrays: 12 m array, 44 antennas  
  > "with the 12 m array in configuration C43-8 using 44 antennas" (2.1 Observations)
- configurations: C43-8  
  > "with the 12 m array in configuration C43-8 using 44 antennas" (2.1 Observations)
- baselines: max baseline 8.5 km; only long baselines  
  > "The total integration time was 41 min with a maximum baseline of 8.5km." (2.1 Observations)
- angular resolution: 0.10"×0.09"  
  > "The synthesized beam of the image is 0.10$''$$\times$0.09$''$" (2.2 Data reduction)
- max recoverable scale: 1.4 arcsec  
  > "we are missing shorter baselines, limiting the maximum recoverable scale to 1.4 arcsec" (2.1 Observations)
- sensitivity: rms 13.6 μJy/beam  
  > "with an rms of 13.6 $\mu$Jy/beam" (2.2 Data reduction)
- time on source: 41 min total integration  
  > "The total integration time was 41 min with a maximum baseline of 8.5km." (2.1 Observations)
- observing dates: November 9th 2017  
  > "on November 9th 2017" (2.1 Observations)
- pi or archival as stated: Cycle 5, PI: Pinilla; Band 7/9 from earlier cycles  
  > "Cycle 5 (2017.1.00884.S, PI: Pinilla)" (2.1 Observations)
- Line: 13CO J=1-0 (110.201354 GHz)
- Line: C18O J=1-0 (109.782176 GHz)
- Other facility **VLT/SPHERE IRDIS**: H- and J-band polarized scattered light images  
  > "We observed the system with the broad band H filter and the broad band J filter." (2.1 Observations)
- Other facility **Keck/NIRC2**: Archival L' band detection limits  
  > "SR 21 was observed (PI: N. van der Marel) with the NIRC2 camera" (Keck L-band detection limits)
- External data: ALMA Band 9 and Band 7 continuum data  
  > "We also use the data presented in Pinilla et al. 2015 in Band 9 (690 GHz) and Band 7 (343 GHz)" (2.2 Data reduction) [from Pinilla et al. 2015; (cite: 2014ApJ...783L..13P; 2016A&A...585A..58V)]
- External data: ATCA 3.3 mm total flux of 4.2 mJy  
  > "Previous observations at 3.3 mm using ATCA (Ricci et al., 2010) found a total flux of 4.2 mJy" (2.2 Data reduction) [from Ricci et al., 2010]
- External data: Hydrodynamical two-planet model of gas surface density  
  > "in the hydrodynamical models from (cite: pinilla2015), one of which is shown in the bottom panel of Fig." (3.1 Scattered light images) [from (cite: pinilla2015)]
- Simulation/model as data: Pinilla et al. 2015a hydrodynamical models (two planets, alpha_turb=1e-3, mass ratios 1e-4 and 1e-3) compared qualitatively  
  > "This model shows the resulting gas surface density from the interaction of two planets in the disk with $\alpha_{\mathrm{turb}}$= 10$^{-3}$" (3.1 Scattered light images)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA v. 5.1.1  
  > "Self-calibration was performed on band 3 using `CASA v. 5.1.1`" (2.2 Data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Performed on Band 3; S/N improved by a factor of two  
  > "improving the signal-to-noise of the data by a factor of two compared to the product" (2.2 Data reduction)

### Imaging

- task: tclean  
  > "We used `tclean` to produce the images of Band 3 data" (2.2 Data reduction)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.0  
  > "with Briggs weighting and a robust parameter of 0.0 for the best compromise between resolution and sensitivity" (2.2 Data reduction)
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
- final beam: 0.10"×0.09"  
  > "The synthesized beam of the image is 0.10$''$$\times$0.09$''$" (2.2 Data reduction)
- final rms: 13.6 μJy/beam  
  > "with an rms of 13.6 $\mu$Jy/beam" (2.2 Data reduction)

### Inherited from earlier work

- SPHERE reduction follows polarimetric reduction of earlier work  
  > "The pipeline follows largely the polarimetric data reduction as outlined in (cite: 2016A&A...595A.112G) and (cite: 2017SPIE10400E..15V)." (2.2 Data reduction) [from (cite: 2016A&A...595A.112G; 2017SPIE10400E..15V)]
- Keck data reduced following NACO description  
  > "following the description for NACO data presented in (cite: 2020MNRAS.492..431B)" (Keck L-band detection limits) [from (cite: 2020MNRAS.492..431B)]

### Not stated but needed to reproduce (our reading)

- Self-calibration solution intervals, number of rounds, and reference antenna/spw
- Flux, bandpass and phase calibrators and flux scale uncertainty for Band 3
- Whether the ALMA pipeline or manual calibration was used
- Cell size, image size, masks, number of clean iterations/threshold, and deconvolver
- Details of Band 7 and Band 9 data processing and project codes
- Procedure for the Gaussian ring fit and optical depth calculation (opacity law, dust properties)
- Method to determine planet location/PA from the spiral kink and ring radius ratio to planet mass
- Disk inclination and position angle used for deprojection/polar maps
- Whether molecular line data were used

## Analysis recipe

1. **Self-calibrate and image Band 3 continuum**: Self-calibration in CASA, imaging with tclean using Briggs weighting  
  > "We used `tclean` to produce the images of Band 3 data, with Briggs weighting and a robust parameter of 0.0" (2.2 Data reduction)
   - software: CASA, tclean
   - parameter: robust = 0.0  
  > "with Briggs weighting and a robust parameter of 0.0 for the best compromise between resolution and sensitivity" (2.2 Data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Characterize the ring in Band 3**: Gaussian fit to azimuthally-averaged radial profile between 0.33" and 0.66"  
  > "determined from a Gaussian fit to the azimuthally-averaged radial profile between 0.33$''$and 0.66$''$" (4.2 Band 3 dust continuum)
   - fitting: _not stated_
   - validation: _not stated_
3. **Estimate optical depths in Bands 3, 7, 9**: Peak optical depth assuming 20 K physical temperature  
  > "In Band 3, where the disk is optically thin (peak optical depth of $\tau$= 0.17 assuming a physical temperature of 20K)" (5.2 Indications of planetary companions)
   - assumption: Dust temperature 20 K  
  > "peak optical depth of $\tau\sim$2.0, assuming a physical temperature of 20K" (5.2 Indications of planetary companions)
   - fitting: _not stated_
   - validation: _not stated_
4. **Compare to hydrodynamic models and infer planet location and mass**: Qualitative comparison of spiral/ring morphology with Pinilla et al. 2015 models; planet position from kink in the faint spiral; mass from ring radial offset (~1.2 planetary radii) and Keck limit  
  > "Given the radial location of the ring in H-band and Band 3, at $\sim$1.2 planetary radii in both datasets, we can rule out a planet of the order of $>$5 M$_\mathrm{Jup}$" (6 Conclusions)
   - software: PynPoint
   - assumption: System age 10 Myr; stellar L' = 6.8 mag for Keck mass conversion  
  > "For this conversion we assumed a stellar L’ magnitude of 6.8 mag based on WISE measurements." (Keck L-band detection limits)
   - fitting: _not stated_
   - validation: Keck upper limit consistent with small planet mass  
  > "A small planet mass is also consistent with archival observational data obtained with the Keck telescope and the NIRC2 instrument in the L-band." (5.3 Mass constraints)

## Software

- **CASA** 5.1.1: Self-calibration and imaging of Band 3  
  > "Self-calibration was performed on band 3 using `CASA v. 5.1.1`" (2.2 Data reduction)
- **IRDAP** : SPHERE/IRDIS polarimetric data reduction  
  > "The SPHERE observations were reduced with the IRDAP (IRDIS Data reduction for Accurate Polarimetry) pipeline" (2.2 Data reduction)
- **PynPoint** 0.8.1: Keck NIRC2 L' reduction, ADI+PCA, contrast curves  
  > "The data were reduced with PynPoint (v. 0.8.1;" (Keck L-band detection limits)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Band 3 beam | 0.10 x 0.09 | not stated | arcsec | 1 | The synthesized beam of the image is 0.10$''$$\times$0.09$''$ |
| Band 3 image rms | 13.6 | not stated | μJy/beam | 1 | with an rms of 13.6 $\mu$Jy/beam |
| Band 3 total flux | 8.2 | not stated | mJy | 1 | a total flux of 8.2 mJy, with a peak value of 0.35 mJy/beam |
| Band 3 ring radius | 0.387 | not stated | arcsec | 2 | The image shows a narrow ($\sim$0.18$''$FWHM) ring centered at 0.387$''$ |
| Band 3 ring FWHM | ~0.18 | not stated | arcsec | 2 | The image shows a narrow ($\sim$0.18$''$FWHM) ring |
| Inner Band 3 ring radius | ~0.23 | not stated | arcsec | 2 | is seen inside it at a radius of $\sim$0.23$''$ |
| Band 3 peak optical depth | 0.17 | not stated | dimensionless | 3 | peak optical depth of $\tau$= 0.17 assuming a physical temperature of 20K |
| Band 7 peak optical depth | 0.5 | not stated | dimensionless | 3 | Band 7, with an intermediate estimated peak optical depth of $\tau$= 0.5 |
| Band 9 peak optical depth | ~2.0 | not stated | dimensionless | 3 | peak optical depth of $\tau\sim$2.0, assuming a physical temperature of 20K |
| Putative planet radius | ~44 | not stated | au | 4 | constrain the location of the suspected planet to a radius of $\sim$44 au and PA of $\sim$11$^{\circ}$ |
| Keck mass upper limit at gap | ~13 | not stated | MJup | 4 | The Keck observation rules out companions more massive than $\sim$13 M$_{\mathrm{Jup}}$ at the location of the scattered light gap in SR21. |

## Qualitative findings

- Bright spirals in scattered light lie inside the mm cavity, with a faint kinked spiral bridging the gap to the outer ring  
  > "in addition to a set of bright spirals inside the mm cavity and a fainter spiral bridging the gap to the outer ring" (abstract)

## Claim tuples

- H: Does SR 21 show evidence of dust trapping and a dust over-density in its outer ring? | E: ALMA Band 3 imaging compared with Bands 7 and 9 and SPHERE H-band | R: Narrow ring at 0.387" with north-west brightening; Band 3 optically thin (tau=0.17) | F: North-west bright region is a dust over-density in a dust-trapping ring | **supported**
- H: Are the SR 21 spirals and ring consistent with planet-disk interaction models? | E: Qualitative comparison of SPHERE morphology with Pinilla et al. 2015 hydrodynamical models | R: Spiral azimuth and pitch angle and Arc 2 match model features | F: A planet at ~44 au, PA ~11 deg is inferred from the kink in the faint spiral | **supported**
- H: How massive is the putative planet? | E: Ring location in H-band vs Band 3 plus Keck L' detection limits | R: Rings coincide within ~13 mas; Keck excludes >~13 MJup | F: Planet mass ~1 MJup favored; >5 MJup ruled out | **partially**
- H: Does a second companion exist in the inner disk? | E: Examination of spiral pitch angle behavior | R: Irregular pitch angles of inner spirals | F: Might hint at a second companion but not concluded | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Outer ring asymmetry in scattered light could instead be shadowing by inner spirals  
  > "or if they are the product of shadowing by the inner spiral arms." (5.2 Indications of planetary companions)
- How they decided it was enough: _not stated_
- Limitation (authors): Only long-baseline ALMA data; shorter baselines missing, limiting recoverable scale to 1.4 arcsec  
  > "We note that only these long baseline observations were carried out and we are missing shorter baselines" (2.1 Observations)
- Limitation (authors): Kinked spiral has low S/N (~3.5 falling to ~2.3) computed pixel by pixel  
  > "we find that this feature has a signal-to-noise ratio of $\sim$3.5 close to the launching point at the inner ring." (3.1 Scattered light images)
- Caveat (inferred, ours): Planet position and mass rest on qualitative comparison with a non-tailored model and a low-S/N kinked spiral
- Caveat (inferred, ours): No dedicated hydrodynamic or radiative transfer simulation for SR 21
- Caveat (inferred, ours): Optical depths depend on an unstated opacity prescription and assumed 20 K
- Caveat (inferred, ours): Band 3 flux is twice the ATCA value without a test of flux calibration

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Calibration details and self-cal parameters
- Missing: Imaging parameters beyond robust
- Missing: Band 7/9 data project codes and processing
- Missing: Method for deriving planet mass from ring offset
- Data volume (inferred): ~50-100 GB for the Band 3 execution (raw), plus SPHERE data
- Score (inferred): 3/5, ALMA Band 3 imaging is reproducible from archival data with CASA, but the planet inference is qualitative and many settings are unstated.
- Rediscovery candidate: no, Main conclusions are mostly morphological and qualitative; the recipe lacks details and the planet inference is not numeric.

## Links

- Method: (cite: vanHolstein2020) (IRDAP polarimetric reduction pipeline)
- Companion: (cite: 2015A&A...584A..16P) (Earlier ALMA Band 9/7 data and two-planet models for SR 21)
- Companion: (cite: 2016A&A...585A..58V) (ALMA Band 7 data)
- Related: SPHERE program 1100.C-0481(Q)

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
 "obscore_codes_not_in_card": [
  "2011.0.00724.S",
  "2012.1.00158.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 43,
  "rate": 0.589
 },
 "evidence_ok": true
}
```
