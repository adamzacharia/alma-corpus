# Clumpy and Extended Starbursts in the Brightest Unlensed Submillimeter Galaxies

`2016ApJ...829L..10I` | The Astrophysical Journal Letters 2016 | first author: Iono, Daisuke | arXiv: 1609.02365 | DOI: 10.3847/2041-8205/829/1/L10

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What is the structure and star formation surface density of the central kpc (and extended regions) of three of the brightest unlensed z=3-4 SMGs (AzTEC1, 4, 8), and are they Eddington-limited starbursts?  
  > "Here we present $0.015\ensuremath{''} - 0.05\ensuremath{''}$ resolution ALMA images in three of the brightest unlensed $z=3 - 4$ SMGs in the COSMOS field – AzTEC1, AzTEC4 and AzTEC8." (Introduction)
- Target **AzTEC1**: coordinates 09:59:42.86 +02:29:38.2 (J2000)  
  > "| AzTEC1 | 4.342 | 6.7 | 9:59:42.86 | +2:29:38.2 |" (Table 1); z/distance z = 4.342  
  > "| AzTEC1 | 4.342 | 6.7 | 9:59:42.86 | +2:29:38.2 |" (Table 1); distance from spectroscopic redshift from Yun et al. 2015  
  > "| AzTEC1 | 4.342 | 6.7 | 9:59:42.86 | +2:29:38.2 |" (Table 1)
- Target **AzTEC4**: coordinates 09:59:31.72 +02:30:44.0 (J2000)  
  > "| AzTEC4 | $\sim 4$$^{c}$ | 7.1 | 9:59:31.72 | +2:30:44.0 |" (Table 1); z/distance z ~ 4 (photometric, adopted)  
  > "| AzTEC4 | $\sim 4$$^{c}$ | 7.1 | 9:59:31.72 | +2:30:44.0 |" (Table 1); distance from photometric redshifts from the literature  
  > "| AzTEC4 | $\sim 4$$^{c}$ | 7.1 | 9:59:31.72 | +2:30:44.0 |" (Table 1)
- Target **AzTEC8**: coordinates 09:59:59.34 +02:34:41.0 (J2000)  
  > "| AzTEC8 | 3.179 | 7.7 | 9:59:59.34 | +2:34:41.0 |" (Table 1); z/distance z = 3.179  
  > "| AzTEC8 | 3.179 | 7.7 | 9:59:59.34 | +2:34:41.0 |" (Table 1); distance from spectroscopic redshift from Smolčić et al. 2012  
  > "| AzTEC8 | 3.179 | 7.7 | 9:59:59.34 | +2:34:41.0 |" (Table 1)

## Data provenance

- ALMA projects: 2012.1.00978.S, 2015.1.01345.S
- bands: 860 μm continuum (Band 7), center 350.739 GHz  
  > "The center frequency of the four correlator basebands was 350.739 GHz (855.337 $\mu$m)." (ALMA Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 100 m to 14 km projected  
  > "projected baselines that ranged from 100 m to 14 km" (ALMA Observations)
- angular resolution: 0.015''–0.05''  
  > "$0.015\ensuremath{''}$ – $0.05\ensuremath{''}$ (120 – 360 pc) 860$\ensuremath{\mu}m$ continuum images" (abstract)
- max recoverable scale: _not stated_
- sensitivity: RMS 31–61 μJy/beam depending on source and taper  
  > "| AzTEC8 | 3.179 | 7.7 | 9:59:59.34 | +2:34:41.0 | 34 | $0.017\ensuremath{''} \times 0.014\ensuremath{''}$ (87$^\circ$) | 0.5 |" (Table 1)
- time on source: _not stated_
- observing dates: November 6–8, 2015  
  > "Observations were carried out on November 6 – 8, 2015 using 46 - 47 antennas" (ALMA Observations)
- pi or archival as stated: _not stated_
- Line: [CII] and [NII] not stated (not stated)
- Other facility **SMA**: 880 μm fluxes (0.5''-0.9'' beam) used to estimate total and extended flux  
  > "The SMA 880 micron fluxes (beam sizes) are $13.8 \pm 2.3$ ($0.86\ensuremath{''} \times 0.55\ensuremath{''}$)" (Table 1)
- Other facility **ALMA Archive**: 0.3'' resolution AzTEC1 data (2012.1.00978.S) combined with new data  
  > "we obtained the $0.3\ensuremath{''}$ resolution data from the ALMA Archive (2012.1.00978.S) and combined it with our high resolution data." (ALMA Observations)
- External data: SMA 880 μm total fluxes of AzTEC1, 4, 8  
  > "for AzTEC1, AzTEC4, and AzTEC8, respectively (cite: 2008ApJ...688...59Y; 2010MNRAS.407.1268Y)" (Table 1) [from (cite: 2008ApJ...688...59Y; 2010MNRAS.407.1268Y)]
- External data: AzTEC4 and AzTEC8 IR luminosity, SFR from SED fit  
  > "The IR luminosity and SFR are obtained from (cite: 2014ApJ...782...68T)." (Table 2) [from (cite: 2014ApJ...782...68T)]
- External data: AzTEC1 total IR luminosity and SFR  
  > "The IR luminosity and SFR are obtained from (cite: 2015MNRAS.454.3485Y)." (Table 2) [from (cite: 2015MNRAS.454.3485Y)]

## Processing

### Calibration

- pipeline or manual: delivered manually calibrated data product, with additional flagging of problematic antennas  
  > "The delivered manually calibrated data product were inspected in the visibilities and in the dirty image, and we flagged problematic antennas that were causing ripples in the image." (ALMA Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA v4.5.1 clean  
  > "We used CASA v4.5.1 for imaging." (ALMA Observations)
- deconvolver: _not stated_
- weighting robust: robust 2 (AzTEC1, AzTEC4), 0.5 (AzTEC8)  
  > "| AzTEC8 | 3.179 | 7.7 | 9:59:59.34 | +2:34:41.0 | 34 | $0.017\ensuremath{''} \times 0.014\ensuremath{''}$ (87$^\circ$) | 0.5 |" (Table 1)
- uv taper: AzTEC4 0.05''; AzTEC1 outertaper 0.03''–0.05''  
  > "We tapered the AzTEC4 data to $0.05\ensuremath{''}$ since the emission is only marginally detected with the native resolution." (ALMA Observations)
- cell size: _not stated_
- image size: _not stated_
- masking: CLEAN boxes on ≥3σ emission; cleaned down to 1.5σ  
  > "We placed CLEAN boxes to the regions where clear ($\geq 3\sigma$) emission features are seen, and CLEANed down to 1.5$\sigma$" (ALMA Observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: AzTEC1 continuum excludes redshifted [CII] frequency range  
  > "The continuum image was generated by using all of the bands except for AzTEC1 in which the frequency range of the redshifted \[C II\] emission was excluded." (ALMA Observations)
- primary beam correction: _not stated_
- array combination: AzTEC1: 0.3'' data combined with high-resolution data, down-weighted by 1/10; multiscale CLEAN  
  > "Data combination was performed after down-weighting the $0.3\ensuremath{''}$ resolution data by 1/10" (ALMA Observations)
- smoothing: _not stated_
- final beam: AzTEC1 0.026''x0.018'' (and tapered 0.048'', 0.070''); AzTEC4 0.064''x0.057''; AzTEC8 0.017''x0.014''  
  > "| AzTEC4 | $\sim 4$$^{c}$ | 7.1 | 9:59:31.72 | +2:30:44.0 | 61 | $0.064\ensuremath{''} \times 0.057\ensuremath{''}$ (40$^\circ$) | 2 ($0.05\ensuremath{''}$) |" (Table 1)
- final rms: _not stated_

### Inherited from earlier work

- AzTEC4/AzTEC8 SED-derived SFRs, IR luminosities and stellar masses  
  > "A fit to the SED yields a SFR of $1778$ M$_{\odot}$ yr$^{-1}$, dust mass of $4.0 \times 10^{9}$ M$_{\odot}$" (Introduction) [from (cite: 2014ApJ...782...68T)]

### Not stated but needed to reproduce (our reading)

- How the Gaussian fits were done (task, region)
- Conversion from FIR luminosity to SFR (calibration, IMF) is not given
- Pipeline/CASA version used for the delivered calibration
- Channel selection for continuum and the exact taper/robust choices tried
- Method and criteria for manual clump identification
- Flux calibrator and flux scale uncertainty

## Analysis recipe

1. **image continuum**: CASA clean with CLEAN boxes, robust and taper variations, multiscale for AzTEC1 combined data  
  > "We searched for the optimal beam size by varying the Robust weighting." (ALMA Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: astrometry check source J0930+0034 peak within 0.0015''–0.0045'' of phase center  
  > "The emission peak of J0930+0034 in all datasets were found within $0.0015\ensuremath{''} - 0.0045\ensuremath{''}$ of the phase center" (ALMA Observations)
2. **measure sizes and fluxes**: Two-dimensional Gaussian fits to peaks; flux integrated above 3σ; manual clump identification at 3σ and 4σ  
  > "In the $>$ 0.5 kpc region, we have manually identified $\sim40$ compact clumps which are detected at $3\sigma$ or above." (Characteristics of the Individual Sources)
   - fitting: 2D Gaussian  
  > "the peak emission of Figure [2](#fig2) (c) was modeled with a two dimensional Gaussian." (Characteristics of the Individual Sources)
   - validation: Residuals after subtracting the two AzTEC4 sources are noise dominated; negative clumps counted for false detections  
  > "The number of negative $3\sigma$ and $4\sigma$ clumps in the same region are two and one, respectively." (Characteristics of the Individual Sources)
3. **derive SFR and surface densities; compare with SMA**: Scale total SFR by ratio of component flux to total SMA flux; divide by measured size; compare ALMA and SMA flux for extended fraction  
  > "We derive the SFR of each component by scaling the total SFR with the ratio between the derived flux densities and the total SMA flux." (Characteristics of the Individual Sources)
   - assumption: z=4 for AzTEC4; WMAP-type ΛCDM, H0=69.6, ΩM=0.286  
  > "We adopt the WMAP concordance $\Lambda$CDM cosmology parameters with H$_0 = 69.6$ km s$^{-1}$ Mpc$^{-1}$ and $\Omega_M = 0.286$" (Introduction)
   - fitting: _not stated_
   - validation: AzTEC1 ALMA 14.16 mJy consistent with SMA 13.8 mJy  
  > "The excellent consistency between the total flux in the $0.070\ensuremath{''} \times 0.063\ensuremath{''}$ image" (Characteristics of the Individual Sources)

## Software

- **CASA** 4.5.1: imaging (clean, multiscale, outertaper)  
  > "We used CASA v4.5.1 for imaging." (ALMA Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| AzTEC1 total ALMA flux (0.070'' image) | 14.16 | 1.42 | mJy | 2 | / 56 / $0.070\ensuremath{''} \times 0.063\ensuremath{''}$ (41$^\circ$) / 2 ($0.05\ensuremath{''}$) / $14.16 \pm 1.42$ / |
| AzTEC1 extended flux fraction | 68% (9.64 mJy) | 1.44 mJy | percent | 2 | This suggests that the extended structure contains 68% ($9.64 \pm 1.44$ mJy) of the total flux. |
| AzTEC1 half light radius | 1.1 | 0.1 | kpc | 2 | The half light radius is $1.1 \pm 0.1$ kpc. |
| AzTEC4 north+south flux | 3.26 | 0.40 | mJy | 2 | yielding a total of $3.26 \pm 0.40$ mJy |
| AzTEC8 central flux | 1.63 | 0.16 | mJy | 2 | is $1.63\pm0.16$ mJy |
| AzTEC8 western peak Sigma_SFR | 2950 | 520 | Msun/yr/kpc^2 | 3 | / Western Peak / $0.30 \pm 0.03$ / \- / $(4.7 \pm 0.6) \times 10^{11}$ / $(2.9 \pm 0.4) \times 10^{13}$ / $47 \pm 8$ / $2950 \pm 520$ / |
| AzTEC1 clumps at ≥4σ total flux | 2.69 | 0.27 | mJy | 2 | total flux from all of the $\geq 4\sigma$ clumps is $2.69 \pm 0.27$ mJy |

## Qualitative findings

- AzTEC1 and AzTEC8 centers consist of multiple ~200 pc clumps; AzTEC4 is a ~1.5 kpc double (mid-stage merger).  
  > "AzTEC4 consists of two sources that are separated by $\sim 1.5$ kpc, indicating a mid-stage merger." (abstract)

## Claim tuples

- H: Are the central regions of the brightest SMGs compact and clumpy? | E: 0.015''–0.05'' ALMA 860 μm imaging of three SMGs | R: Multiple ~200 pc clumps in AzTEC1 and AzTEC8; double source in AzTEC4 | F: Central structures are complex and clumpy | **supported**
- H: Is most emission extended? | E: Compare ALMA flux with SMA total flux | R: 68–90% of flux extended (≳1 kpc) in AzTEC 4 and 8, 68% in AzTEC1 | F: Extended clumpy starbursts surround the compact centers | **supported**
- H: Are the central clumps Eddington-limited starbursts? | E: Derive Sigma_SFR and compare with radiation pressure models | R: Peak Sigma_SFR ~300–3000 | F: AzTEC8 may be near or above Eddington limit | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Cold mode accretion model not ruled out; isolated clumpy disk too large  
  > "However, the cold mode accretion model is not ruled out." (abstract)
- How they decided it was enough: _not stated_
- Limitation (authors): Lack kinematic data to constrain Eddington model parameters  
  > "We lack sufficient data, such as gas kinematics, to constrain these parameters properly" (Eddington Limited Starbursts?)
- Limitation (authors): Unknown cause of ~0.05''–0.4'' offset from SMA phase center  
  > "The cause of this offset is unknown at present." (ALMA Observations)
- Caveat (inferred, ours): SFR scaling from SMA flux assumes uniform dust temperature
- Caveat (inferred, ours): Extended fraction relies on SMA total flux with different frequency and resolution
- Caveat (inferred, ours): Manual clump identification, not objective
- Caveat (inferred, ours): Small sample of three

## Reproducibility

- Data public (paper): Archive data cited for AzTEC1 (2012.1.00978.S); ALMA data acknowledged  
  > "we obtained the $0.3\ensuremath{''}$ resolution data from the ALMA Archive (2012.1.00978.S)" (ALMA Observations)
- Products in archive: _not stated_
- Missing: Calibrated measurement sets/pipeline details
- Missing: Clump identification list procedure
- Missing: FIR luminosity to SFR conversion
- Data volume (inferred): ~100–300 GB raw for the long-baseline data
- Score (inferred): 3/5, Data public and imaging parameters partly given, but clump identification manual and several settings missing.
- Rediscovery candidate: no, Manual clump finding and unstated settings; proprietary period data may have been public later but recipe incomplete.

## Links

- Companion: (cite: 2015MNRAS.454.3485Y) (AzTEC1 SED and redshift)
- Companion: (cite: 2014ApJ...782...68T) (SED fits for AzTEC4 and AzTEC8)
- Related: COSMOS

## Checks

```json
{
 "quotes": 57,
 "quotes_ok": 57,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 43,
  "rate": 0.614
 },
 "evidence_ok": true
}
```
