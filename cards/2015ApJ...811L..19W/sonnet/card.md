# Gemini Planet Imager Observations of the AU Microscopii Debris Disk: Asymmetries within One Arcsecond

`2015ApJ...811L..19W` | The Astrophysical Journal Letters 2015 | first author: Wang, Jason J. | arXiv: 1508.04765 | DOI: 10.1088/2041-8205/811/2/L19

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: debris_disks
- Question: What is the morphology of the AU Mic debris disk within 1 arcsec, and are there planets or compact clumps, as seen with GPI?  
  > "We use GPI in both spectral and polarimetry modes to study the morphology of the debris disk and search for planets close in to the star." (Introduction)
- Target **AU Microscopii**: coordinates _not stated_; z/distance 9.9 pc  
  > "At a distance of 9.9 pc, we are able to probe closer to the star than most systems." (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: _none stated_
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **Gemini South GPI**: K1-band spectral mode and H-band polarimetry mode observations (primary data)  
  > "On 2014 May 12, twenty-seven 60 s spectral mode frames were taken in the K1 spectral band (1.90–2.19 $\mu$m)" (Observations and Data Reduction)
- Other facility **HST/STIS**: Optical scattered-light images for comparison  
  > "optical imaging using the using the Space Telescope Imaging Spectrograph (STIS) on the Hubble Space Telescope (cite: schneider14)" (Discussion)
- Other facility **NICI**: Planet detection limits at large separations  
  > "we also included the limits from the Near-Infrared Coronagraphic Imager (cite: wahhaj13) in Figure" (Sensitivity to Planets)
- External data: ALMA 1.3-mm continuum reduced data of AU Mic, used for comparison and disk position angle  
  > "we compare our observations with 1.3-mm continuum data from ALMA (cite: macgregor13)" (Discussion) [from MacGregor et al. 2013 (cite: macgregor13)]
- External data: Disk PA of 128.41 deg derived from ALMA  
  > "using a disk position angle (PA) of $128.41\ensuremath{^\circ}$ (cite: macgregor13) derived from observations with Atacama Large Millimeter/submillimeter Array (ALMA)" (Observations and Data Reduction) [from MacGregor et al. 2013 (cite: macgregor13)]
- External data: HST/STIS reduced data for comparison  
  > "We thank M. MacGregor and G. Schneider for making available to us the reduced ALMA and STIS data respectively." (Acknowledgments) [from Schneider et al. 2014 (cite: schneider14)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
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

- Polarimetry mode data reduction steps  
  > "The reduction of the polarimetry mode data follows the steps described in (cite: perrin15_pol)." (Observations and Data Reduction) [from (cite: perrin15_pol)]
- Disk model parameters from porous water-ice model  
  > "We adopted values from the porous water-ice model from (cite: graham07)" (Analysis of the Debris Disk) [from (cite: graham07)]

### Not stated but needed to reproduce (our reading)

- ALMA data were not reprocessed; the reduced ALMA images came from MacGregor via private communication
- GPI data availability not given

## Analysis recipe

1. **PSF subtraction**: KLIP with ADI (and SDI for spectral mode), annuli and azimuthal sectors  
  > "we used `pyKLIP` (cite: wang15), a Python implementation of the Karhunen-Loève Image Projection (KLIP) algorithm" (Observations and Data Reduction)
   - software: pyKLIP
   - parameter: H-band: 3 KL modes with 10-pixel exclusion (left side), 4 KL modes with 6-pixel exclusion (right side)  
  > "we used three KL modes and a ten-pixel exclusion for the diffuse left side of the disk" (Observations and Data Reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit disk vertical profiles**: Gaussian vertical profile fits between 0.4 and 1.25 arcsec to measure mid-plane offset, FWHM, peak and integrated flux  
  > "fit Gaussian vertical profiles to the disk at various separations. We fit between 0.4$''$ and 1.25$''$." (Analysis of the Debris Disk)
   - fitting: _not stated_
   - validation: Injected model disks at five positions to correct self-subtraction bias; scatter gives the uncertainties  
  > "The scatter of all four quantities in the model disks were used as the uncertainties in our measurements." (Analysis of the Debris Disk)
3. **Planet sensitivity**: Contrast curve via Mawet et al. 2014, planet injection, Monte-Carlo completeness with COND models  
  > "we ran a Monte-Carlo analysis as described by (cite: nielsen) to determine the completeness of our data." (Sensitivity to Planets)
   - assumption: COND evolutionary models; 23 Myr age  
  > "assuming COND models (cite: baraffe03)" (Sensitivity to Planets)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **pyKLIP** : PSF subtraction  
  > "we used `pyKLIP` (cite: wang15)" (Observations and Data Reduction)
- **GPI Data Reduction Pipeline** : Creating datacubes and measuring satellite spots  
  > "a datacube created by the GPI Data Reduction Pipeline (cite: perrin14_drp)" (Observations and Data Reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| SE vertical mid-plane offset at 1 arcsec | 69 | 30 | mas | 2 | an offset from the average ALMA mid-plane of 69$\pm$30 mas to the northeast at 1$''$ separation |
| NW mid-plane offset at 1 arcsec | 47 | 8 | mas | 2 | with an offset of 47$\pm$8 mas to the southwest at 1$''$ |
| SE peak FWHM | 570 | 56 | mas | 2 | triples on the SE side past 0.8$''$ to a peak FWHM of 570$\pm$56 mas |
| K1 candidate separation | 544 | 4 | mas | 3 | at a separation of 544$\pm$4 mas, a PA of $130.2\ensuremath{^\circ}$$\pm$$0.9\ensuremath{^\circ}$ |
| K1 candidate contrast | 1.1e-5 | 0.3e-5 | dimensionless | 3 | a *K1* contrast of 1.1$\pm$0.3 $\times 10^{-5}$ |

## Qualitative findings

- No polarized signal detected; disk detected only in total intensity  
  > "We did not detect any polarized signal (5% upper limit on the polarization fraction at 0.5$''$)" (Observations and Data Reduction)

## Claim tuples

- H: Is the inner AU Mic disk asymmetric? | E: Gaussian vertical profile fits to KLIP-reduced H-band images | R: SE side has a bump at 1 arcsec, three times more extended and fainter in peak brightness, offset 69 mas | F: Stark SE/NW asymmetries, possibly a warp or the disk backside, agreeing with STIS and ALMA | **supported**
- H: Are planets present in the inner disk? | E: K1 spectral-mode contrast and completeness analysis | R: 50% complete for 4 MJup at 4 AU; one compact candidate at 544 mas | F: The candidate is either a planet or a disk clump, since it is resolved along the disk | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Disk brightness vs separation unreliable owing to residual PSF features; sliver at only 3.1 sigma and may arise from KLIP self-subtraction  
  > "We cannot rule out that the apparent morphology is influenced by KLIP self-subtraction." (Analysis of the Debris Disk)
- Caveat (inferred, ours): Single-epoch GPI data; the candidate is not confirmed by common proper motion
- Caveat (inferred, ours): ALMA is used only as comparison, with no reanalysis

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: GPI data access
- Missing: Exact pyKLIP settings beyond KL modes and exclusion
- Missing: Reduced ALMA images from MacGregor 2013
- Data volume (inferred): not applicable for ALMA; GPI data are a few GB
- Score (inferred): 2/5, ALMA plays only a comparison role and the main analysis uses GPI data
- Rediscovery candidate: no, The main data are GPI, not ALMA, and the ALMA data are only a supporting comparison

## Links

- Method: Wang et al. 2015 pyKLIP (cite: wang15) (PSF subtraction code)
- Method: Perrin et al. 2015 (cite: perrin15_pol) (GPI polarimetry reduction)
- Companion: MacGregor et al. 2013 (cite: macgregor13) (ALMA 1.3 mm AU Mic observations)

## Checks

```json
{
 "quotes": 28,
 "quotes_ok": 28,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00142.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 20,
  "rate": 0.303
 },
 "evidence_ok": true
}
```
