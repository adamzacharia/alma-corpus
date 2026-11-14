# Exploring the CO/CN line ratio in nearby galaxies with the ALMA archive

`2018MNRAS.477.2926W` | Monthly Notices of the Royal Astronomical Society 2018 | first author: Wilson, Christine D. | arXiv: 1803.11225 | DOI: 10.1093/mnras/sty845

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: nearby_galaxies, astrochemistry
- Question: How does the CO J=1-0/CN N=1-0 line ratio vary within and between nearby galaxies, and does it depend on AGN presence, abundance or excitation?  
  > "These line ratio changes are likely due to changes in the \[CN\]/\[H$_2$\] abundance ratio and/or the CN excitation." (abstract)
- Target **NGC 253**: coordinates _not stated_; z/distance 3.5 Mpc  
  > "NGC 253 distance from (cite: radburn-smith2011)" (Table 3); distance from radburn-smith2011  
  > "NGC 253 distance from (cite: radburn-smith2011)" (Table 3)
- Target **M83**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **NGC 3256**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **VV 114**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **NGC 1377**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **AM 2055-425, AM 2246-490, AM 1300-233**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.1.00099.S, 2011.1.00172.S, 2011.1.00467.S, 2011.1.00525.S, 2011.1.00645.S, 2011.1.00772.S
- bands: 3 mm window (CO J=1-0 and CN N=1-0), Cycle 0  
  > "CN was one of the $\sim 50$ molecular lines in the 3 mm window" (1 Introduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: VV 114 observed in compact and extended configurations; only compact used  
  > "For VV 114, which was imaged in both the compact and extended configurations, we use only the compact data" (2.2 Initial data processing)
- baselines: _not stated_
- angular resolution: beams from 1.45x1.30 to 5.5x3.1 arcsec (Table 2)  
  > "| VV 114 | 5.5x3.1, -80 | 2.1x1.2 | 30 | 1.1 | 1.3 | 3 | 30 |" (Table 2)
- max recoverable scale: _not stated_
- sensitivity: CN rms 1.0-4.7 mJy/beam in 5-40 km/s channels  
  > "| NGC 3256 | 3.2x2.1, 5 | 0.67x0.44 | 20 | 1.0 | 1.3 | 3 | 20 |" (Table 2)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archival Cycle 0 data  
  > "For this archival ALMA project, we focused on Cycle 0 data" (2.1 The ALMA Cycle 0 CN galaxy sample)
- Line: CO J=1-0 (not stated)
- Line: CN N=1-0, J=3/2-1/2 (113.4910 GHz)
- External data: Infrared luminosities, adjusted to adopted distances  
  > "Infrared luminosities from (cite: sanders2003) adjusted to luminosity distance given here." (Table 3) [from (cite: sanders2003)]
- External data: NGC 253 and M83 distances  
  > "NGC 253 distance from (cite: radburn-smith2011); M83 distance averaged from (cite: radburn-smith2011) and (cite: saha2006)" (Table 3) [from (cite: radburn-smith2011); (cite: saha2006)]
- External data: CO cubes for NGC 253 and VV 114 provided by collaborators  
  > "CO and CN data cubes for NGC 253 were kindly provided by A. Bolatto, while a cleaned CO data cube for VV 114 was kindly provided by K. Sliwa." (2.2 Initial data processing) [from (cite: bolatto2013a)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Calibrated uv data and initial cubes downloaded from ALMA archive (March 2014)  
  > "Calibrated uv data and initial image cubes were downloaded from the ALMA Science Archive in March 2014." (2.1 The ALMA Cycle 0 CN galaxy sample)
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
- masking: Clean box defined by inspecting emission channel by channel  
  > "The clean box was defined by inspecting emission channel by channel for each line." (2.2 Initial data processing)
- multiscale scales: _not stated_
- continuum subtraction: Performed for all galaxies except NGC 1377  
  > "Continuum subtraction was performed for all the galaxies in the ALMA Cycle 0 CN sample except NGC 1377." (2.2 Initial data processing)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Small spatial smoothing to match CO and CN beams  
  > "a small spatial smoothing was applied to each of the CO and CN data cubes to match the beam size and shape" (2.2 Initial data processing)
- final beam: _not stated_
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- Software used for imaging, smoothing and moment maps (not named)
- Weighting/robust, cell and image size, deconvolver
- Line-free channels for continuum subtraction and velocity ranges per galaxy (except VV 114)
- Exact aperture definitions for flux measurement
- Flux calibration uncertainty
- Rest frequency of CO assumed
- Cubes provided privately for NGC 253 and VV 114 CO

## Analysis recipe

1. **Select sample**: Inspect Cycle 0 projects for nearby galaxies observing CO 1-0; check cubes for CN S/N>3 over more than one channel  
  > "8 galaxies showed significant CN emission across more than one velocity channel." (2.1 The ALMA Cycle 0 CN galaxy sample)
   - fitting: _not stated_
   - validation: _not stated_
2. **Make matched moment 0 maps**: Integrated intensity maps with 2-3 sigma cutoff, only emission channels, after beam matching  
  > "An integrated intensity map was made for each line using a $2-3\sigma$ cutoff and including only those velocity channels in which sufficiently strong emission was seen" (2.3 Measuring the CO/CN ratio)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive S/N-matched CO/CN ratio**: Iterate CO moment cutoff at R_i x (2,3)sigma_CN, using CN channels and CN-clipped mask, until R converges (2-3 iterations); ratio of fluxes  
  > "a second CO integrated intensity map was made, but this time using a cutoff equal to $R_1 \times (2,3)\sigma_{CN}$" (2.3 Measuring the CO/CN ratio)
   - fitting: _not stated_
   - validation: Convergence of R_i; tapered NGC 1377 test agreed with Table values  
  > "The global and S/N-matched CO/CN line ratios measured from this lower resolution map agreed extremely well" (3.1 Observed variations in the CO/CN line ratio)

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| S/N-matched CO/CN range | 7 to 65 | not stated | dimensionless | 3 | Signal-to-noise matched CO/CN ratios range from as low as 7 to as high as 65 |
| Global CO/CN ratio range | 20 to 140 | not stated | dimensionless | 2 | while ratios using the total detected flux range from 20 to 140 |
| AM 2246-490 S/N-matched ratio | 7 | 1 | dimensionless | 3 | / AM 2246-490 / $7 \pm 1$ / $20 \pm 3$ / 34 / |
| NGC 1377 S/N-matched ratio | 40 | 10 | dimensionless | 3 | / NGC 1377 / $40\pm 10$ / $140\pm 40$ / |

## Qualitative findings

- CO/CN varies by more than a factor of 3 spatially in several galaxies; opacity and conversion factor unlikely to explain it  
  > "We argue that the variations are unlikely to be due to differences in the opacity of either CO or CN" (Conclusions)

## Claim tuples

- H: Does the CO/CN ratio vary strongly between and within galaxies? | E: S/N-matched and global ratios in 8 Cycle 0 galaxies | R: Ratios 7-65 (matched), 20-140 (global) | F: Large variations, likely abundance and/or excitation | **supported**
- H: Is CO/CN higher near AGN? | E: Compare ratios in 4 AGN nuclei with starburst regions | R: 3 of 4 AGN show ratios 2-3 times larger | F: CN may be suppressed near AGN, in tension with XDR models | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: CN optical depth, CO optical depth, and CO-to-H2 conversion factor variations rejected as main cause  
  > "or to changes in the CO-to-H$_2$ conversion factor in these infrared-luminous systems" (Conclusions)
- How they decided it was enough: Iterated until R_i close to R_i+1  
  > "at which point the process was deemed to have converged" (2.3 Measuring the CO/CN ratio)
- Limitation (authors): Agreement between flux-weighted and moment-map ratios not always good; VV 114 multiplier could not match global ratio  
  > "We note that the agreement between the flux-weighted CO/CN ratio and the value measured from the ratio of the moment 0 maps is not always as good as for AM 2246-490." (2.3 Measuring the CO/CN ratio)
- Caveat (inferred, ours): Iterative S/N matching is subjective and uncertainties are loosely estimated
- Caveat (inferred, ours): Small sample, heterogeneous resolution
- Caveat (inferred, ours): No excitation modelling to separate abundance from excitation

## Reproducibility

- Data public (paper): Calibrated Cycle 0 data from ALMA Science Archive  
  > "calibrated uv data sets are available through the ALMA archive" (2.1 The ALMA Cycle 0 CN galaxy sample)
- Products in archive: _not stated_
- Missing: Software and imaging parameters
- Missing: Privately provided cubes
- Missing: Per-galaxy velocity ranges and apertures
- Data volume (inferred): tens of GB
- Score (inferred): 3/5, Public data and clear ratio method, but imaging details and software are unstated.
- Rediscovery candidate: no, Imaging recipe incomplete and some cubes were privately supplied.

## Links

- Companion: (cite: ueda2014) (Source of 20-galaxy CO survey)
- Companion: (cite: meier2015) (NGC 253 CN analysis)
- Related: ALMA Cycle 0 projects 2011.1.00099.S etc.

## Checks

```json
{
 "quotes": 39,
 "quotes_ok": 39,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 6,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.1.00099.S",
  "2011.1.00172.S",
  "2011.1.00467.S",
  "2011.1.00525.S",
  "2011.1.00645.S",
  "2011.1.00772.S"
 ],
 "obscore_codes_not_in_card": [
  "2011.0.00099.S",
  "2011.0.00172.S",
  "2011.0.00467.S",
  "2011.0.00525.S",
  "2011.0.00645.S",
  "2011.0.00772.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 24,
  "rate": 0.329
 },
 "evidence_ok": true
}
```
