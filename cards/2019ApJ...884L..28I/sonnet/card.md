# Counter-rotation and High-velocity Outflow in the Parsec-scale Molecular Torus of NGC 1068

`2019ApJ...884L..28I` | The Astrophysical Journal Letters 2019 | first author: Impellizzeri, C. M. Violette | arXiv: 1908.07981 | DOI: 10.3847/2041-8213/ab3c64

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, nearby_galaxies
- Question: What are the geometry and kinematics of the parsec-scale molecular torus of NGC 1068, as traced by HCN (3-2) at 1.4 pc resolution?  
  > "In an effort to untangle the complicated geometry and kinematics of the molecular torus of NGC 1068, we obtained new ALMA observations of HCN ($J=3\to 2$) at 1.4 pc (20 mas) resolution." (1 Introduction)
- Target **NGC 1068**: coordinates _not stated_; z/distance scale 1" = 70 pc  
  > "We adopt the Ringberg Standards for NGC 1068 (cite: 1997Ap&SS.248....9B), which assigns the scale 1$''$ = 70 pc." (Footnote 1); distance from Ringberg Standards (Bland-Hawthorn et al. 1997)  
  > "We adopt the Ringberg Standards for NGC 1068 (cite: 1997Ap&SS.248....9B), which assigns the scale 1$''$ = 70 pc." (Footnote 1)

## Data provenance

- ALMA projects: 2017.1.01666.S
- bands: Band 6  
  > "We used ALMA to observe NGC 1068 in Band 6 during ALMA Cycle 5" (2 Observations and Data Reduction)
- frequencies and spectral setup: three continuum windows of 1.875 GHz each plus one HCN(3-2) window; ~1.0 km/s channels, ~1000 km/s bandwidth  
  > "The HCN line observation has channel-width $\sim$1.0 km s$^{-1}$ and spans $\sim$1000 km s$^{-1}$ total bandwidth." (2 Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-10  
  > "We used the longest baseline configuration available for Band 6 during Cycle 5, C43-10" (2 Observations and Data Reduction)
- baselines: 41.4 m to 16.2 km  
  > "with baselines ranging from 41.4 m to 16.2 km" (2 Observations and Data Reduction)
- angular resolution: 19.9x19.1 mas line beam (~1.4 pc)  
  > "The common restoring beam is $19.9\times19.1$ mas, PA 79.8$^\circ$" (2 Observations and Data Reduction)
- max recoverable scale: about 0.32 arcsec (22 pc)  
  > "The largest recoverable structure is about 0.32$''$, or 22 pc at the distance of NGC 1068." (2 Observations and Data Reduction)
- sensitivity: 1.6 mJy/beam per ~10 km/s channel (median); continuum rms 6.2 uJy/beam  
  > "the median line channel sensitivity is 1.6 mJy beam$^{-1}$." (2 Observations and Data Reduction)
- time on source: 14.5 hours total, nine execution blocks  
  > "the total integration time on source was 14.5 hours" (2 Observations and Data Reduction)
- observing dates: 10-24 October 2017  
  > "The source was observed in nine execution blocks between 10 October 2017 and 24 October 2017." (2 Observations and Data Reduction)
- pi or archival as stated: _not stated_
- Line: HCN J=3-2 (265.88618 GHz)
- Other facility **VLBA**: Continuum and H2O megamaser disk data from earlier work, used for comparison  
  > "the H$_2$O megamaser disk mapped by the VLBA" (4 Conclusions)
- External data: Keplerian rotation curve best fitting H2O megamaser kinematics, and maser radial velocities (central mass 1.66e7 Msun)  
  > "the Keplerian rotation curve that best fits the H$_2$O megamaser kinematics (cite: newmaserpaper)" (3 Results) [from (cite: newmaserpaper)]
- External data: CO(6-5) outflow velocities up to 400 km/s for comparison  
  > "maximum outflow velocities observed in CO ($J=6\rightarrow 5$) line emission (cite: 2016ApJ...829L...7G)" (3 Results) [from (cite: 2016ApJ...829L...7G)]

## Processing

### Calibration

- pipeline or manual: CASA pipeline  
  > "The data were calibrated using CASA pipeline version 40896 (Pipeline-CASA51-P2-B)" (2 Observations and Data Reduction)
- casa version: CASA 5.1.1 (imaging)  
  > "imaged using CASA 5.1.1" (2 Observations and Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0432-0120, 0.97±0.04 Jy  
  > "the flux calibrator was J0432$-$0120, with flux density $S_{\nu} = 0.97\pm0.04$ Jy" (2 Observations and Data Reduction)
- flux scale uncertainty: _not stated_
- self calibration: four cycles of phase-only self-cal on continuum, applied to line data  
  > "We performed four cycles of phase-only self-calibration on the continuum data" (2 Observations and Data Reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs weighting (robust value not given)  
  > "The visibility data were Briggs-weighted during Fourier inversion" (2 Observations and Data Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uv-plane, average of channels with |RV|>600 km/s from systemic  
  > "Continuum subtraction of the line data was performed in the $(u,v)$ plane using an average of channels with radial velocities $| \mbox{RV}| > 600$ km s$^{-1}$ relative to systemic." (2 Observations and Data Reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: averaged to ~10 km/s channels  
  > "The spectral line data were averaged in frequency to provide approximately 10 km s$^{-1}$ wide channels." (2 Observations and Data Reduction)
- final beam: line 19.9x19.1 mas PA 79.8 deg; continuum 20.2x19.6 mas PA 78.3 deg  
  > "The restoring beam of the continuum image is $20.2\times19.6$ mas, PA 78.3$^\circ$" (2 Observations and Data Reduction)
- final rms: continuum 6.2 uJy/beam; line 1.6 mJy/beam per channel  
  > "the rms sensitivity is $6.2\,\mu\mbox{Jy\ beam}^{-1}$." (2 Observations and Data Reduction)

### Inherited from earlier work

- Gauss-Hermite fitting technique for velocity field  
  > "see (cite: 1993ApJ...407..525V) for a description of this technique" (3 Results) [from (cite: 1993ApJ...407..525V)]
- Tangential velocity technique for rotation curve  
  > "using the conventional tangential velocity technique (cite: 1965gast.book..167K)" (3 Results) [from (cite: 1965gast.book..167K)]

### Not stated but needed to reproduce (our reading)

- Briggs robust value, cell size, image size, deconvolver and clean threshold
- Self-calibration solution intervals and reference antenna
- Gauss-Hermite order and initial guesses
- Exact criterion for 'nearest velocity where spectrum falls below noise' in tangential velocity method
- Inclination used to deproject rotation speeds
- Megamaser Keplerian curve parameters (paper submitted/unpublished)
- Position of S1 used for spectrum extraction

## Analysis recipe

1. **Calibrate, self-calibrate and image continuum and HCN cube**: CASA pipeline calibration, 4 phase-only self-cal cycles on continuum applied to lines, Briggs imaging, uv continuum subtraction, ~10 km/s channels  
  > "We performed four cycles of phase-only self-calibration on the continuum data (cite: 1989ASPC....6..185C), and the solutions were applied to the spectral line data." (2 Observations and Data Reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Radial velocity field**: Gauss-Hermite polynomial fit to each spectrum in the cube  
  > "We measured the radial velocity field using Gauss-Hermite polynomial fits to each spectrum in the HCN data cube" (3 Results)
   - fitting: Gauss-Hermite polynomial  
  > "A Gauss-Hermite polynomial was fitted to each extracted HCN spectrum, and Monte Carlo realizations of the spectrum were generated by adding a randomly generated noise spectrum scaled to the observed rms." (Results)
   - validation: _not stated_
3. **Nuclear absorption profile and outflow**: Extract spectrum at S1; subtract mean of spectra 1.4 pc NE and SW to correct for emission  
  > "we averaged the spectra from positions 1.4 pc (one beam) northeast and southwest of the nucleus and subtracted the result from the nuclear spectrum." (3 Results)
   - fitting: _not stated_
   - validation: Blue wing present in both raw and corrected spectra  
  > "The blue wing appears on both the raw and corrected spectra, and so it is likely not an artifact of the emission correction." (3 Results)
4. **Rotation curve via tangential velocity**: Spectra at each pixel (0.2 pc) along major axis for r>=1.2 pc; two spectra along maser PA 131 deg for r<1.2 pc; Gauss-Hermite fit with Monte Carlo noise realizations  
  > "Monte Carlo realizations of the spectrum were generated by adding a randomly generated noise spectrum scaled to the observed rms." (3 Results)
   - parameter: 10^4 Monte Carlo trials  
  > "The average and standard deviation of $10^4$ trials respectively provide an estimate of the tangential velocity and its uncertainty." (3 Results)
   - assumption: Intrinsic dispersion up to 90 km/s gives corrections smaller than uncertainties  
  > "intrinsic velocity dispersions as high as $\sigma_r = 90$ km s$^{-1}$, comparable to the inferred rotation speeds, introduce corrections smaller than the measurement uncertainties." (3 Results)
   - fitting: _not stated_
   - validation: Compared with Keplerian curve from H2O masers  
  > "The $r > 1.2$ pc rotation curve is consistent with an extrapolation of the Keplerian rotation curve." (3 Results)

## Software

- **CASA** 5.1.1 (pipeline 40896): calibration and imaging  
  > "imaged using CASA 5.1.1" (2 Observations and Data Reduction)
- **astropy** : _not stated_

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Blue wing absorption extent | -450 | not stated | km/s | 3 | there is a pronounced blue wing on the absorption profile that extends to roughly $-450$ km s$^{-1}$ relative to systemic |
| Inner disk max rotation speed | 380 | 30 | km/s | 4 | The inferred rotation speeds of the inner HCN disk reach $380\pm 30$ km s$^{-1}$ |
| Largest deviation from Keplerian (3.4 pc NW) | 70 | 40 | km/s | 4 | the measured rotational speed deviates from the predicted Keplerian rotation curve by $70\pm 40$ km s$^{-1}$ |
| Median rotation speed uncertainty | 30 | not stated | km/s | 4 | The median uncertainty is 30 km s$^{-1}$. |
| HCN major axis PA | ~114 | not stated | deg | 0 | The orientation of the HCN major axis is PA $\sim 114\ensuremath{^\circ}$ |
| Central mass (from maser Keplerian fit) | 1.66e7 | not stated | Msun | 0 | Keplerian rotation around a central mass of $1.66\times 10^7\,\mbox{M}_\odot$ |

## Qualitative findings

- Outer disk (1.2-7 pc) counter-rotates relative to the inner disk, with rotation consistent with Keplerian about same central mass  
  > "The outer disk, which extends to $\sim 7$ pc radius, counter-rotates relative to the inner disk." (abstract)
- HCN velocity field is complex along the CO outflow axis  
  > "the HCN radial velocity field is more complex along the molecular outflow axis" (4 Conclusions)

## Claim tuples

- H: Is there a high-velocity molecular outflow in the nuclear region? | E: Extract the HCN absorption spectrum toward S1, correct for emission | R: Blue wing extends to about -450 km/s | F: Outflow speeds approach 450 km/s, exceeding CO(6-5) maxima of 400 km/s | **supported**
- H: Does the torus consist of kinematically distinct disks? | E: Tangential velocity rotation curve along the major axis | R: Inside 1.2 pc rotation follows the masers; 1.2-7 pc runs opposite | F: Counter-rotating, misaligned inner and outer disks | **supported**
- H: Origin of the outer counter-rotating disk | E: Argument from angular momentum and literature | R: Disk warping cannot induce counter-rotation | F: Outer disk likely formed from recently introduced gas (infall or captured dwarf); speculative | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Method does not correct for unknown intrinsic velocity dispersion; outflow and disk emission blended in the beam along the minor axis  
  > "Note that this method does not correct for the unknown, intrinsic velocity dispersion of the gas." (3 Results)
- Caveat (inferred, ours): Blue absorption wing could partly reflect beam-blended emission or continuum structure
- Caveat (inferred, ours): Rotation curve uncertainties are large; Keplerian consistency is weakly constrained
- Caveat (inferred, ours): Inclination and deprojection not described
- Caveat (inferred, ours): Origin of counter-rotation is speculation

## Reproducibility

- Data public (paper): Project code stated; ALMA data acknowledged via ADS/JAO  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.01666.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters (robust, cell, size, clean settings)
- Missing: Self-cal parameters
- Missing: Maser Keplerian curve parameters (submitted paper)
- Missing: Fitting details for Gauss-Hermite
- Data volume (inferred): Large: nine execution blocks in C43-10, likely several hundred GB raw
- Score (inferred): 5/5, Data identified and main steps described, but imaging and fitting parameters are missing and the maser comparison relies on an unpublished paper.
- Rediscovery candidate: no, Recipe lacks key imaging/fitting details and depends on an unpublished maser model.

## Links

- Method: (cite: 1993ApJ...407..525V) (Gauss-Hermite line profile fitting)
- Method: (cite: 1965gast.book..167K) (Tangential velocity technique)
- Companion: (cite: newmaserpaper) (H2O megamaser Keplerian disk fit)
- Companion: (cite: 2018ApJ...853L..25I) (Earlier HCN(3-2) ALMA observations at ~3 pc)
- Companion: (cite: 2016ApJ...829L...7G) (CO(6-5) outflow)

## Checks

```json
{
 "quotes": 52,
 "quotes_ok": 52,
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
  "facts": 67,
  "stated": 40,
  "rate": 0.597
 },
 "evidence_ok": true
}
```
