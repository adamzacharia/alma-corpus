# First Detection of Gas-phase Methanol in a Protoplanetary Disk

`2016ApJ...823L..10W` | The Astrophysical Journal Letters 2016 | first author: Walsh, Catherine | arXiv: 1606.06492 | DOI: 10.3847/2041-8205/823/1/L10

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Is gas-phase methanol present in the TW Hya protoplanetary disk, and what are its abundance and radial location?  
  > "The first detection of gas-phase methanol in a protoplanetary disk (TW Hya) is presented." (abstract)
- Target **TW Hya**: coordinates _not stated_; z/distance 54 pc  
  > "the first detection of gas-phase methanol in a nearby protoplanetary disk (TW Hya, $54$ pc)" (INTRODUCTION); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00902.S, 2013.1.00114.S
- bands: Band 7 and Band 6  
  > "The Band 7 (B7) methanol transitions listed in Table [1](#table1) were targeted" (OBSERVATIONS)
- frequencies and spectral setup: B7: 122 kHz channels (0.12 km/s), plus 317 GHz continuum window; B6: 122 kHz (0.15 km/s), 58.6 MHz per window  
  > "using a channel width of 122 kHz (corresponding to 0.12 km s$^{-1}$)" (OBSERVATIONS); "with a total bandwidth of 58.6 MHz per spectral window" (OBSERVATIONS)
- continuum bandwidth: 2 GHz at 317 GHz (B7)  
  > "A continuum-only spectral window at 317 GHz (with a total bandwidth of 2 GHz) was also covered." (OBSERVATIONS)
- arrays: _not stated_
- configurations: _not stated_
- baselines: B7: 15-350 m (39 antennas); B6: 30-650 m (31 antennas)  
  > "observed on 2015 January 02 with 39 antennas and baselines from 15 to 350 m" (OBSERVATIONS); "observed on 2014 July 19 with 31 antennas and baselines from 30 to 650 m" (OBSERVATIONS)
- angular resolution: Stacked B7 beam 1.4"x0.73"; B6 0.5"x0.5"  
  > "This resulted in a synthesised beam of 1.4$''$$\times$0.73$''$ ($-84\degree$)" (OBSERVATIONS)
- max recoverable scale: _not stated_
- sensitivity: Stacked B7 rms 2.0 mJy/beam; per-channel ~4 mJy (B7), ~5 mJy (B6)  
  > "an rms noise of 2.0 mJy/beam, which is a factor of $\approx 2$ increase in sensitivity" (OBSERVATIONS)
- time on source: B7: 43 min; B6: 41 min  
  > "The total on-source observation time was 43 minutes." (OBSERVATIONS); "The total on-source observation time was 41 minutes." (OBSERVATIONS)
- observing dates: B7: 2015 Jan 02; B6: 2014 Jul 19  
  > "TW Hya was also observed on 2014 July 19" (OBSERVATIONS)
- pi or archival as stated: _not stated_
- Line: CH3OH 2_11-2_02 A (304.208 GHz)
- Line: CH3OH 3_12-3_03 A (305.473 GHz)
- Line: CH3OH 4_13-4_04 A (307.166 GHz)
- External data: TW Hya disk physical structure (density, temperature, UV) reproducing dust SED and CO lines  
  > "We adopt the TW Hya disk physical structure from (cite: kama16) that reproduces the dust SED as well CO rotational line emission" (Constraining the methanol abundance) [from (cite: kama16)]
- External data: TW Hya inclination and position angle  
  > "a disk inclination and position angle appropriate for TW Hya (cite: hughes11)" (Constraining the methanol abundance) [from (cite: hughes11)]
- External data: Methanol molecular data (A and E type) from LAMDA  
  > "the molecular data files for A- and E-type methanol from the Leiden Atomic and Molecular Database (LAMDA" (Constraining the methanol abundance) [from LAMDA]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.3  
  > "using CASA version 4.3 and the continuum band at 317 GHz" (OBSERVATIONS)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: B7: Titan; B6: Pallas  
  > "Titan was used for amplitude calibration" (OBSERVATIONS); "Pallas was used for flux calibration" (OBSERVATIONS)
- flux scale uncertainty: _not stated_
- self calibration: B7: 20 s on 317 GHz continuum; B6: 30 s on continuum in each spectral window  
  > "using a timescale of 20 seconds ($\approx$ 3 times the integration step)" (OBSERVATIONS); "a timescale of 30 seconds" (OBSERVATIONS)

### Imaging

- task: _not stated_
- deconvolver: Line cubes imaged dirty (no CLEAN); stacked data one round of CLEAN  
  > "A single round only of additional CLEANing was performed." (OBSERVATIONS)
- weighting robust: Continuum: Briggs robust = 0.5; lines: natural  
  > "CLEAN (Briggs weighting, robust = 0.5)" (OBSERVATIONS); "(using natural weighting)" (OBSERVATIONS)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Applied to line data after self calibration  
  > "following self calibration and continuum subtraction" (OBSERVATIONS)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Three B7 datasets concatenated and stacked in uv domain after velocity regridding  
  > "concatenated into a single measurement set following velocity regridding" (OBSERVATIONS)
- smoothing: _not stated_
- final beam: 1.4"x0.73" (-84 deg)  
  > "a synthesised beam of 1.4$''$$\times$0.73$''$ ($-84\degree$)" (OBSERVATIONS)
- final rms: 2.0 mJy/beam  
  > "an rms noise of 2.0 mJy/beam" (OBSERVATIONS)

### Inherited from earlier work

- Disk physical structure model  
  > "We adopt the TW Hya disk physical structure from (cite: kama16)" (Constraining the methanol abundance) [from (cite: kama16)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and continuum subtraction method
- Image size and cell size
- Which B7 transitions are stacked beyond approximate frequencies; velocity regridding details
- Aperture/mask for spectrum extraction beyond the 3 sigma continuum contour
- LIME settings (photons, grid) and methanol temperature/excitation assumptions
- Exact fit criterion (by eye)

## Analysis recipe

1. **Self-calibrate and image data**: Self calibration on continuum, continuum subtraction, dirty channel maps  
  > "The line data were imaged without CLEANing (using natural weighting)" (OBSERVATIONS)
   - software: CASA
   - fitting: _not stated_
   - validation: Self-cal on continuum near lines gave almost indistinguishable results  
  > "gave almost indistinguishable results" (OBSERVATIONS)
2. **Stack three B7 methanol lines in uv domain**: Concatenate after velocity regridding and image with natural weighting  
  > "imaged using CLEAN with natural weighting (i.e., “stacked” in the uv domain)" (OBSERVATIONS)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Model abundance and location**: Grid of LIME LTE models varying inner/outer radius (10 AU steps), abundance and vertical layer; compare stacked line profile and channel maps  
  > "A small grid of models were run in which the inner and outer radius of the emission were varied (in steps of 10 AU)" (Constraining the methanol abundance)
   - software: LIME
   - parameter: layers z/r<=0.1, 0.1-0.2, 0.2-0.3  
  > "$z/r \le 0.1$, $0.1 \le z/r \le 0.2$, and $0.2 \le z/r \le 0.3$" (Constraining the methanol abundance)
   - assumption: LTE; Kama et al. disk structure  
  > "assuming LTE" (Constraining the methanol abundance)
   - fitting: Best by-eye fit  
  > "The results for the best “by-eye” fit to the data" (Constraining the methanol abundance)
   - validation: Models reproduce B6 non-detection  
  > "reproduce the non-detection in the B6 data" (Constraining the methanol abundance)

## Software

- **CASA** 4.3: Self calibration, CLEAN imaging  
  > "self calibration of the B6 data with CASA version 4.3" (OBSERVATIONS)
- **LIME** : Ray-tracing of model channel maps  
  > "Ray-tracing calculations were performed using LIME (cite: brinch10)" (Constraining the methanol abundance)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Peak S/N of stacked B7 emission | 5.5 | not stated | sigma | 2 | reaching a peak S/N of $5.5\sigma$ |
| Fiducial midplane CH3OH abundance (30-100 AU ring) | 2.8e-12 | ~20% | relative to H2 | 3 | with a fractional abundance of $2.8\times10^{-12}$ relative to |
| Abundance in 0.1<z/r<0.2 and 0.2<z/r<0.3 | 8.0e-12; 4.4e-11 | not stated | relative to H2 | 3 | fractional abundances of $8.0\times10^{-12}$ and $4.4\times10^{-11}$ |
| Peak column density at 30 AU | 3-6e12 | not stated | cm^-2 | 3 | peak column density of $\approx 3 - 6 \times 10^{12}$ cm$^{-2}$ at 30 AU |
| Stacked line peak flux density | 33 | rms 6.5 | mJy | 2 | The peak flux density for the stacked line profile is 33 mJy and the rms noise is 6.5 mJy |
| CH3OH/H2O gas ratio (midplane) | ~0.7 | not stated | % | 0 | ratio is $\approx 0.7$% if both species are located in the midplane |

## Qualitative findings

- Methanol emission is offset from the star, suggesting a ring peaking near the CO snowline; emission is compact relative to the continuum  
  > "methanol is located in a ring, with a peak column density coincident with the location of the CO snow line" (DISCUSSION)

## Claim tuples

- H: Gas-phase methanol is detectable in a protoplanetary disk | E: Stacked three B7 methanol lines in uv domain | R: Emission in six channels, peak 5.5 sigma, with expected kinematics | F: First detection of gas-phase methanol in a disk | **supported**
- H: Methanol abundance and location in TW Hya | E: LIME grid models compared to stacked data | R: Abundance 3e-12 to 4e-11; ring peaking near 30 AU | F: Abundance is up to two orders lower than chemical models predict; ice hosted on larger inner grains | **partially**

## Reasoning

- Why this data: Chemical models identified methanol as good ALMA target  
  > "determined that gas-phase was a good ALMA target for the indirect detection of the complex organic ice reservoir" (INTRODUCTION)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Low S/N precludes detailed modeling; vertical location unconstrained  
  > "The low S/N of the B7 detection precludes more detailed modeling." (Constraining the methanol abundance)
- Caveat (inferred, ours): By-eye fitting without formal uncertainties or degeneracy exploration
- Caveat (inferred, ours): Detection is only 5 sigma and depends on stacking choices and extraction aperture
- Caveat (inferred, ours): Ring morphology inferred from low-resolution data

## Reproducibility

- Data public (paper): Project codes given in acknowledgments  
  > "ADS/JAO.ALMA#2013.1.00902.S and\ ADS/JAO.ALMA#2013.1.00114.S" (Acknowledgments)
- Products in archive: _not stated_
- Missing: LIME configuration
- Missing: Kama et al. 2016 model files
- Missing: Imaging sizes and line-free channels
- Data volume (inferred): ~20-50 GB
- Score (inferred): 3/5, Public data and clear stacking recipe, but modeling details and disk model are external and fit is by eye.
- Rediscovery candidate: yes, Public data; stacked detection with numeric S/N and abundances is redoable, though modeling needs external disk structure.

## Links

- Method: (cite: brinch10) (LIME code)
- Method: (cite: kama16) (TW Hya disk physical structure)
- Companion: (cite: walsh14b) (Predicted methanol as ALMA target)

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
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 62,
  "stated": 37,
  "rate": 0.597
 },
 "evidence_ok": true
}
```
