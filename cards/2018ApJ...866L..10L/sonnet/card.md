# The ALMA Detection of Extraplanar <SUP>13</SUP>CO in a Ram-pressure-stripped Galaxy and Its Implication

`2018ApJ...866L..10L` | The Astrophysical Journal Letters 2018 | first author: Lee, Bumhyun | arXiv: 1810.04188 | DOI: 10.3847/2041-8213/aae4d9

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, milky_way_ism
- Question: Is molecular gas (12CO and 13CO) in the ram-pressure-stripped Virgo galaxy NGC 4522 stripped from the disk or formed in situ, and what does extraplanar 13CO imply for chemical enrichment of halo gas and the ICM?  
  > "Using the ALMA data, we probe the origin of the extraplanar molecular gas and discuss its impact on the surrounding medium of the host galaxy." (INTRODUCTION)
- Target **NGC 4522**: coordinates RA 12h33m39.71s, Dec +09d10m29.7s (J2000)  
  > "R.A. (J2000)$^{a}$ | $12^h33^m39^s.71$" (Table 1); "at the Virgo distance of 16 Mpc (cite: yasuda97)" (ALMA OBSERVATIONS); z/distance 16 Mpc (Virgo); v_HI = 2331 km/s  
  > "R.A. (J2000)$^{a}$ | $12^h33^m39^s.71$" (Table 1); "at the Virgo distance of 16 Mpc (cite: yasuda97)" (ALMA OBSERVATIONS); distance from Yasuda et al. 1997  
  > "R.A. (J2000)$^{a}$ | $12^h33^m39^s.71$" (Table 1); "at the Virgo distance of 16 Mpc (cite: yasuda97)" (ALMA OBSERVATIONS)

## Data provenance

- ALMA projects: 2015.1.01341.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12m array  
  > "were carried out during Cycle 3 (2016 January) using the 12m array." (ALMA OBSERVATIONS)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~2.3" to 3" (~200 pc)  
  > "This yields a synthesized beam of $\sim$2$\ensuremath{''}$.3 to 3$\ensuremath{''}$ in both lines" (ALMA OBSERVATIONS)
- max recoverable scale: ~21.5" (~1.7 kpc)  
  > "beyond the maximum recoverable scale ($\sim$21$\ensuremath{''}$.5$\approx$1.7 kpc)" (Main Disk)
- sensitivity: 1.44 mJy/beam (12CO) and 0.46 mJy/beam (13CO) per 5 km/s channel  
  > "yielding 1.44 mJy beam$^{-1}$ and 0.46 mJy beam$^{-1}$ over a 5 km s$^{-1}$ channel width" (ALMA OBSERVATIONS)
- time on source: 51 min (12CO), 273 min (13CO)  
  > "In total, 51 minutes and 273 minutes were integrated on the target for $^{12}$CO and $^{13}$CO with 46 and 43 antennas, respectively" (ALMA OBSERVATIONS)
- observing dates: Cycle 3, 2016 January  
  > "were carried out during Cycle 3 (2016 January) using the 12m array." (ALMA OBSERVATIONS)
- pi or archival as stated: PI: B. Lee  
  > "project ID: 2015.1.01341.S; PI: B. Lee" (ALMA OBSERVATIONS)
- Line: 12CO J=1-0 (115.271 GHz)
- Line: 13CO J=1-0 (110.201 GHz)
- External data: Single-dish 12CO and HI masses used for extraplanar fractions and flux comparison  
  > "using data from (cite: chung09) and (cite: vollmer08)." (Table 1) [from Chung et al. 2009 (cite: chung09); Vollmer et al. 2008 (cite: vollmer08)]
- External data: Galaxy properties from HyperLeda  
  > "(a) HyperLeda (cite: makarov14)" (Table 1) [from Makarov et al. 2014 (cite: makarov14)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline in CASA  
  > "The data were calibrated using the ALMA pipeline in Common Astronomy Software Applications (CASA)-4.5.3" (ALMA OBSERVATIONS)
- casa version: CASA 4.5.3  
  > "The data were calibrated using the ALMA pipeline in Common Astronomy Software Applications (CASA)-4.5.3" (ALMA OBSERVATIONS)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "the data were naturally weighted to obtain the highest signal-to-noise ratio (S/N) possible to recover diffuse molecular emissions." (ALMA OBSERVATIONS)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied  
  > "and corrected for primary beam attenuation." (ALMA OBSERVATIONS)
- array combination: _not stated_
- smoothing: 10 km/s resolution cube with smoothing mask in AIPS for intensity map  
  > "The intensity map was generated using the cube of 10 km s$^{-1}$ resolution with the smoothing mask in the Astronomical Image Processing System (AIPS)" (ALMA OBSERVATIONS)
- final beam: _not stated_
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- Mask/threshold criteria for the AIPS smoothing mask and clump definitions
- Cell size, image size, deconvolution and clean threshold
- Continuum subtraction and line-free channels
- Whether the two pointings were mosaicked and how
- Flux calibrator and flux scale uncertainty
- How region apertures for clumps were defined
- Procedure for line ratio map (convolution to common beam, cutoff)
- Observed frequency/redshift used in the L'CO equation

## Analysis recipe

1. **Calibrate and image the data**: ALMA pipeline calibration in CASA, natural weighting, primary beam correction; intensity maps from 10 km/s cube with AIPS smoothing mask  
  > "The data were calibrated using the ALMA pipeline in Common Astronomy Software Applications (CASA)-4.5.3" (ALMA OBSERVATIONS)
   - software: CASA, AIPS
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure clump velocity, width and flux**: Fit single 1D Gaussian to each clump spectrum; 2D Gaussian for orientation  
  > "have been measured by fitting a single 1D Gaussian function to each spectrum shown in the bottom panels" (Clumps)
   - fitting: _not stated_
   - validation: Compared main-disk ALMA flux with single-dish flux (87%)  
  > "This corresponds to 87% of the single-dish flux within the comparable area" (Main Disk)
3. **Derive H2 masses**: L'CO from Solomon et al. 1997 equation, then multiply by alpha_CO  
  > "To estimate the H$_{2}$ mass ($M_{\rm H_{2}}$), we adopt $\alpha_{\rm CO}$ = 3.2 $M_{\odot}$ pc$^{-2}$ (K km s$^{-1}$)$^{-1}$ (cite: strong96)." (RESULTS)
   - assumption: alpha_CO = 3.2 Msun pc-2 (K km/s)-1, no helium; distance 16 Mpc; 12CO(2-1)/(1-0) ~0.8 for single-dish comparison  
  > "assuming a $^{12}$CO (2–1)/(1–0) ratio of $\sim$0.8, as in nearby galaxies (cite: leroy09)" (Main Disk)
   - fitting: _not stated_
   - validation: _not stated_
4. **Measure 12CO/13CO line ratio**: Line ratio map, mean ratio per structure, for clumps detected at 5 sigma in both lines  
  > "We measured $R_{12/13}$ for the clumps detected in 5$\sigma$ or above in both lines." (Clumps)
   - fitting: _not stated_
   - validation: Compared with ratios in nearby spirals  
  > "which is consistent with the range observed in nearby spiral galaxies (cite: paglione01; vila15)" (Main Disk)
5. **Compare timescales for origin of clumps**: Compare stripping timescale (~100 Myr upper limit) with H2 and cloud formation timescales  
  > "we have compared various timescales involved with molecular gas stripping and formation processes." (Origin of Extraplanar Clumps)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.5.3: ALMA pipeline calibration  
  > "The data were calibrated using the ALMA pipeline in Common Astronomy Software Applications (CASA)-4.5.3" (ALMA OBSERVATIONS)
- **AIPS** : Intensity map generation with smoothing mask  
  > "with the smoothing mask in the Astronomical Image Processing System (AIPS)" (ALMA OBSERVATIONS)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Main disk 12CO flux | 64.725 | 0.417 | Jy km/s | 2 | MAIN / 3.99 / 2333.1$\pm$3.0 / 137.8$\pm$7.0 / 64.725$\pm$0.417 |
| Main disk H2 mass | 1289.0e5 | 8.3e5 | Msun | 3 | 1289.0$\pm$8.3 |
| Main disk R12/13 | 10.80 | 3.52 | dimensionless | 4 | $R_{12/13}$ across the main disk is 10.80 $\pm$ 3.52 |
| H2 mass within stellar disk | ~1.3e8 | not stated | Msun | 3 | we measure $\sim$$1.3 \times 10^{8}$ $M_{\odot}$ of $M_{\rm H_{2}}$ |
| Fraction of CO flux in clumps | ~8% | not stated | percent | 2 | about 8% of the total CO flux has been detected in clumps |
| Clump F 13CO flux | 0.159 | 0.011 | Jy km/s | 2 | 0.159$\pm$0.011 |
| Clump H2 mass range | 1e5 to 3e6 | not stated | Msun | 3 | The H$_{2}$ mass of clumps ranges from $10^{5}$ $M_{\odot}$ to $3 \times 10^{6}$ $M_{\odot}$ |
| Mean extraplanar clump velocity | 2388 | not stated | km/s | 2 | with a mean of 2388 km s$^{-1}$ |

## Qualitative findings

- Extraplanar clumps elongated along the projected ICM wind direction and offset to lower velocity toward the cluster mean  
  > "Most clumps are not randomly oriented but elongated along the east-west direction." (Characteristics of Extraplanar Clumps)

## Claim tuples

- H: Is 13CO present in the extraplanar gas of a ram-pressure-stripped galaxy? | E: ALMA 12CO and 13CO(1-0) imaging of two pointings | R: 13CO detected in extraplanar clumps C, D, E, G | F: First extraplanar 13CO detection in a ram-pressure-stripped galaxy | **supported**
- H: Does the 13CO imply heavy elements were stripped from the disk? | E: Argument based on 13C origin in AGB stars versus Halpha/no FUV in the halo | R: Newly formed stars in the halo are too young to donate 13C | F: 13C likely originated in the disk, evidence for stripping of heavy elements | **supported**
- H: Are extraplanar molecular clumps stripped molecules or formed in situ? | E: Compare stripping and formation timescales | R: Timescales not significantly distinct | F: Origin cannot be uniquely constrained | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Natural weighting chosen for highest S/N to recover diffuse emission  
  > "the data were naturally weighted to obtain the highest signal-to-noise ratio (S/N) possible to recover diffuse molecular emissions." (ALMA OBSERVATIONS)
- How they decided it was enough: _not stated_
- Limitation (authors): Diffuse extended CO emission likely missing beyond maximum recoverable scale  
  > "Some diffuse extended CO emission is likely missing from our ALMA data" (Main Disk)
- Limitation (authors): H2 mass excludes helium  
  > "Note that our estimation for H$_{2}$ mass ($M_{\rm H_{2}}$) does not include helium abundance." (RESULTS)
- Caveat (inferred, ours): Single alpha_CO applied to disk and clumps
- Caveat (inferred, ours): R12/13 gradient interpretation relies on assumed uniform conditions
- Caveat (inferred, ours): No 13CO-based optical depth or abundance modeling
- Caveat (inferred, ours): Origin argument is qualitative

## Reproducibility

- Data public (paper): Project code and acknowledgement of ADS/JAO.ALMA data given; public status not explicitly stated  
  > "This Letter makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.01341.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters (cell, size, mask, clean threshold)
- Missing: Clump region definitions
- Missing: Line ratio map construction details
- Data volume (inferred): ~20-50 GB raw for the two-pointing 12m dataset
- Score (inferred): 5/5, Data are identifiable and calibration and weighting are given, but imaging and region-definition details are missing.
- Rediscovery candidate: yes, The project code is given and main results are tabulated numbers, but recipe details are thin.

## Links

- Method: Solomon et al. 1997 (cite: solomon97) (L'CO equation)
- Companion: Lee et al. 2017 (cite: lee17) (Earlier ALMA CO study of Virgo ram-pressure-stripped spirals)
- Companion: Vollmer et al. 2008 (cite: vollmer08) (Single-dish CO of NGC 4522)

## Checks

```json
{
 "quotes": 51,
 "quotes_ok": 51,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 33,
  "rate": 0.5
 },
 "evidence_ok": true
}
```
