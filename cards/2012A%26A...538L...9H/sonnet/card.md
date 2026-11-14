# ALMA CO and VLT/SINFONI H<SUB>2</SUB> observations of the Antennae overlap region: mass and energy dissipation

`2012A&A...538L...9H` | Astronomy and Astrophysics 2012 | first author: Herrera, C. N. | arXiv: 1201.2942 | DOI: 10.1051/0004-6361/201118317

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: nearby_galaxies, star_formation
- Question: How do the morphology, kinematics and line ratios of ALMA CO(3-2) and SINFONI H2 1-0 S(1) in the Antennae overlap region trace mass and energy dissipation in SGMCs, and is the compact H2 source a pre-cluster cloud?  
  > "We show that together the ALMA and VLT observations provide the complementary (mass and energetics) data needed to characterize the dynamical state of SGMCs and to search for pre-cluster clouds." (Introduction)
- Target **Antennae overlap region (NGC4038/4039)**: coordinates _not stated_; z/distance 22 Mpc  
  > "(66 pc$\times$115 pc, at a distance of 22 Mpc)" (Comparison of ALMA and SINFONI observations); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00003.SV
- bands: Band 7 (345 GHz)  
  > "obtained in 10 hr of observing time in band 7 (345 GHz) between May and June 2011" (Comparison of ALMA and SINFONI observations)
- frequencies and spectral setup: intrinsic 0.85 km/s resolution, binned to 10 km/s channels  
  > "The data have an intrinsic spectral resolution of 0.85 km s$^{-1}$ and were binned into channels of 10 km s$^{-1}$." (Comparison of ALMA and SINFONI observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 25 to 200 m, 10 to 13 antennae  
  > "with 10 to 13 antennae and baselines from 25 to 200 m" (Comparison of ALMA and SINFONI observations)
- angular resolution: 0.6"x1.1" (66 pc x 115 pc)  
  > "This gives an angular resolution of 0.6$''$$\times$1.1$''$" (Comparison of ALMA and SINFONI observations)
- max recoverable scale: extended structures >4" lost  
  > "cause a loss of extended structures $>$4$''$" (Comparison of ALMA and SINFONI observations)
- sensitivity: 2sigma = 6 mJy/beam  
  > "all pixel values $<$2$\sigma$ (6 mJy beam$^{-1}$) were set to zero" (Comparison of ALMA and SINFONI observations)
- time on source: 10 hr of observing time (mosaic)  
  > "obtained in 10 hr of observing time in band 7" (Comparison of ALMA and SINFONI observations)
- observing dates: May-June 2011  
  > "between May and June 2011" (Comparison of ALMA and SINFONI observations)
- pi or archival as stated: ALMA Science Verification data  
  > "CO(3$-$2) line emission was obtained during ALMA science verification." (Comparison of ALMA and SINFONI observations)
- Line: CO J=3-2 (not stated)
- Line: H2 1-0 S(1) (not stated)
- Other facility **VLT/SINFONI**: K-band imaging spectroscopy of H2 lines, R=3000, four 8"x8" regions, 40 min per pointing  
  > "in four regions each 8$''$$\times$8$''$ in size" (Comparison of ALMA and SINFONI observations)
- Other facility **OVRO**: CO(1-0) cube used for R3-2/1-0 ratios  
  > "by comparing the ALMA and OVRO data, after smoothing to a common resolution" (Comparison of ALMA and SINFONI observations)
- Other facility **VLT/CRIRES**: high-resolution H2 1-0 S(1) spectrum of PCC  
  > "CRIRES high-resolution (6 km s$^{-1}$) H$_2$ 1$-$0 S(1) spectra of PCC (H11)" (The compact H$_2$ source)
- External data: Single-dish CO(3-2) (JCMT, HHT) for missing flux comparison  
  > "single-dish JCMT and HHT CO(3$-$2) observations of (cite: zhu03) and (cite: schulz07)" (Comparison of ALMA and SINFONI observations) [from (cite: zhu03), (cite: schulz07)]
- External data: R3-2/1-0 = 0.59 scaling  
  > "adopted the scaling R$_{3-2/1-0}$$=$0.59 of (cite: schulz07)" (Comparison of ALMA and SINFONI observations) [from (cite: schulz07)]
- External data: Embedded stellar mass of PCC 4e4 Msun and H2/Brgamma>15  
  > "The small embedded stellar mass of $M_{*}$$=$$4\times 10^4
\, M_\odot$ (H11)" (The compact H$_2$ source) [from (cite: herrera11)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Publicly available reduced SV data cubes, corrected for primary beam attenuation  
  > "We used the reduced data cubes publicly available on the ALMA website" (Comparison of ALMA and SINFONI observations)
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
- primary beam correction: applied to reduced cubes  
  > "which we corrected for the primary beam attenuation" (Comparison of ALMA and SINFONI observations)
- array combination: _not stated_
- smoothing: ALMA smoothed to resolution of OVRO CO(1-0) and single-dish beams for ratios  
  > "after smoothing to a common resolution" (Comparison of ALMA and SINFONI observations)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- SINFONI reduction of the additional fields done similarly to SGMC 2 in earlier work  
  > "We obtained and reduced the data of the three additional fields in a similar way." (Comparison of ALMA and SINFONI observations) [from H11 (cite: herrera11)]
- Xco = 3e20 same as previous study  
  > "we used the same $X_{\rm CO}$ factor for CO(1$-$0) as (cite: wilson00)" (Comparison of ALMA and SINFONI observations) [from (cite: wilson00)]

### Not stated but needed to reproduce (our reading)

- SINFONI data reduction details
- Exact moment-map and Gaussian-fit initial guesses and channel ranges
- Box definitions for SGMC spectra (only in figure)
- Procedure for annulus background subtraction of PCC CO
- Conversion from CO flux to mass formula details
- Beam/rms of the final ALMA cubes
- Whether SV calibrated cubes version/date

## Analysis recipe

1. **Prepare ALMA cube and measure missing flux**: Primary beam corrected SV cubes clipped at 2 sigma; compared spectra at single-dish resolution  
  > "To measure fluxes we used a clipped cube where all pixel values $<$2$\sigma$ (6 mJy beam$^{-1}$) were set to zero." (Comparison of ALMA and SINFONI observations)
   - fitting: _not stated_
   - validation: About half the single-dish flux recovered; SGMC total flux agrees with SMA  
  > "We found about half the total flux of the single-dish data." (Comparison of ALMA and SINFONI observations)
2. **Intensity and velocity maps and spectra**: Gaussian fits per pixel (1 component SINFONI, up to 3 ALMA); first moment for CO velocity; integrated spectra over boxes fitted with Gaussians for flux, velocity, width  
  > "by fitting Gaussian profiles to the spectra in each spatial pixel, using one component for SINFONI and up to three components for the higher spectral resolution ALMA data." (Comparison of ALMA and SINFONI observations)
   - fitting: Gaussian fits; errors are fit uncertainties only  
  > "Error bars include only fit uncertainties, not the systematic errors owing to the missing short spacings." (Comparison of ALMA and SINFONI observations)
   - validation: _not stated_
3. **Derive gas masses**: CO flux to mass with Xco and R3-2/1-0  
  > "We estimated gas masses from the CO fluxes, where the $X_{\rm
CO}$ factor is the main source of uncertainty." (Comparison of ALMA and SINFONI observations)
   - assumption: Xco = 3e20 H2 cm-2 (K km/s)-1; R3-2/1-0 = 0.59; distance 22 Mpc  
  > "$X_{\rm CO}$$=$$3\times
10^{20}$ H$_2$ cm$^{-2}$ (K km s$^{-1})^{-1}$" (Comparison of ALMA and SINFONI observations)
   - fitting: _not stated_
   - validation: Comparable to Wilson et al. 2000 masses  
  > "Our mass estimates (Tab. [\[tab:comp\]](#tab:comp)) are comparable to those of (cite: wilson00)." (Comparison of ALMA and SINFONI observations)
4. **Virial mass of PCC**: M_vir = 5 R sigma^2/G with CO(3-2) sigma and 50 pc SINFONI size  
  > "Since ALMA does not spatially resolve the PCC, we instead used the 50 pc size measured with SINFONI." (The compact H$_2$ source)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CLUMPFIND** : mentioned as an algorithm that would have difficulty isolating PCC; not used  
  > "Isolating the PCC CO counterpart from the surrounding extended emission is difficult with an algorithm like CLUMPFIND" (The compact H$_2$ source)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| PCC CO(3-2) flux | 7.6 | 0.4 | Jy km/s | 2 | 7.6 $\pm$0.4 |
| PCC molecular mass | 1.0e7 | 0.1e7 | Msun | 3 | 1.0$\pm0.1 \times 10^7$ |
| PCC virial mass | 4.6e7 (sigma=40 km/s) | not stated | Msun | 4 | $M_{\rm vir}=5 R \sigma^2/G=4.6\times
10^{7}\times (\sigma_{v}/40~{\rm km~s}^{-1})^2~M_{\odot}$ |
| R3-2/1-0 range | 0.3-0.8, mean 0.5 | not stated | dimensionless | 2 | This ratio varies from source to source between 0.3$-$0.8, with a mean value of 0.5 |
| PCC H2/CO ratio | 8.7 | not stated | dimensionless | 2 | 8.7 |
| PCC CO velocity gradient | ~1 | not stated | km/s/pc | 2 | ($\sim$1 km s$^{-1}$ pc$^{-1}$ in the position-velocity diagram |

## Qualitative findings

- H2 and CO kinematics are well matched in all SGMCs; H2/CO varies by up to 10x  
  > "H$_2$ line emission is found in all SGMCs and the kinematics of H$_2$ and CO are well matched." (abstract)

## Claim tuples

- H: The compact H2 source is a pre-cluster cloud | E: Identify CO counterpart in ALMA, fit spectrum, compute virial mass, compare energetics | R: Highest H2/CO, steepest velocity gradient, Mvir ~5e7 Msun, size 50 pc | F: PCC is likely a pre-cluster cloud in a short ~1 Myr phase | **partially**
- H: H2 and CO trace same gas kinematics in SGMCs | E: Compare velocity fields and spectra | R: Kinematics match well | F: Warm and cold gas closely associated | **supported**

## Reasoning

- Why this data: SINFONI lacked CO at similar resolution; ALMA SV provides it  
  > "but lacked CO observations at similar resolution, which are required to probe the bulk of the gas on the relevant scales of $\le$100 pc" (Introduction)
- Why this method: _not stated_
- Alternative: PDR heating and protostellar winds rejected as H2 energy sources  
  > "makes protostellar winds an implausible energy source" (The compact H$_2$ source)
- How they decided it was enough: _not stated_
- Limitation (authors): Missing short spacings lose about half of single-dish flux; errors exclude this  
  > "We found about half the total flux of the single-dish data." (Comparison of ALMA and SINFONI observations)
- Caveat (inferred, ours): Masses depend on Xco and R3-2/1-0 assumptions and missing flux
- Caveat (inferred, ours): PCC size taken from SINFONI, not resolved by ALMA
- Caveat (inferred, ours): Shock interpretation relies on line ratios and literature

## Reproducibility

- Data public (paper): Reduced SV cubes publicly available  
  > "We used the reduced data cubes publicly available on the ALMA website" (Comparison of ALMA and SINFONI observations)
- Products in archive: _not stated_
- Missing: SINFONI cubes and reduction
- Missing: OVRO CO(1-0) cube (provided privately)
- Missing: Box regions and fit details
- Data volume (inferred): ~10-50 GB (reduced SV cubes) plus SINFONI cubes
- Score (inferred): 3/5, ALMA data public and recipe simple, but SINFONI and OVRO data are not public and details are sparse.
- Rediscovery candidate: no, Requires non-public SINFONI and OVRO data and under-specified fitting.

## Links

- Companion: (cite: herrera11) (Earlier SINFONI/CRIRES study of the PCC (H11))
- Companion: (cite: ueda11) (SMA CO(3-2) observations of the Antennae)
- Related: ALMA Science Verification Antennae

## Checks

```json
{
 "quotes": 48,
 "quotes_ok": 48,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 36,
  "rate": 0.529
 },
 "evidence_ok": true
}
```
