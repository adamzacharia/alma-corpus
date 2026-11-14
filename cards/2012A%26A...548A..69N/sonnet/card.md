# Outflow structure and velocity field of Orion source. I. ALMA imaging of SiO isotopologue maser and thermal emission

`2012A&A...548A..69N` | Astronomy and Astrophysics 2012 | first author: Niederhofer, F. | arXiv: 1210.2526 | DOI: 10.1051/0004-6361/201220292

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: What are the large-scale structure and velocity field of the Source I outflow in Orion BN/KL as traced by SiO isotopologues, and is the J=5-4 v=1 emission maser?  
  > "Our main goal was to study in detail the large-scale structure and velocity field of the Source I outflow." (1 Introduction)
- Target **Orion BN/KL Source I**: coordinates _not stated_; z/distance 418±6 pc (420 pc adopted)  
  > "Radio Source I in the Becklin-Neugebauer/Kleinmann-Low (BN/KL) region (d=418$\pm$6 pc; (cite: Kim08))" (1 Introduction); distance from Kim08 (cite: Kim08)  
  > "Radio Source I in the Becklin-Neugebauer/Kleinmann-Low (BN/KL) region (d=418$\pm$6 pc; (cite: Kim08))" (1 Introduction)

## Data provenance

- ALMA projects: 2011.0.99001.CSV
- bands: Band 6, 214-246 GHz  
  > "covered the frequency range 214-246 GHz which corresponds to the lower 2/3 of the total frequency range in ALMA Band 6" (2 Observations and Imaging)
- frequencies and spectral setup: 20 spectral windows of 1.875 GHz, 3840 channels of 488.281 kHz, ~0.7 km/s Hanning-smoothed  
  > "Each spectral window consists of 3840 channels that are 488.281 kHz wide." (2 Observations and Imaging)
- continuum bandwidth: _not stated_
- arrays: 16 12-m antennas, compact Cycle 0 ES configuration  
  > "16 antennas (each 12 meters in diameter) were included in the compact Early Science (ES) Cycle 0 configuration." (2 Observations and Imaging)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~1.7"x1.2"  
  > "This provided a synthesized beam of $\sim$1$\ensuremath{''}$7 $\times$ 1$\ensuremath{''}$2 at a P.A. of $\sim$1$^{\rm o}$." (2 Observations and Imaging)
- max recoverable scale: _not stated_
- sensitivity: theoretical 0.01 Jy/beam in 0.7 km/s  
  > "is 0.01 Jy beam$^{-1}$ in 0.7 km s$^{-1}$" (2 Observations and Imaging)
- time on source: _not stated_
- observing dates: 2012 January 20  
  > "was conducted on 2012 January 20" (2 Observations and Imaging)
- pi or archival as stated: _not stated_
- Line: 29SiO v=0 5-4 (214.38574 GHz)
- Line: 28SiO v=2 5-4 (214.08854 GHz)
- Line: 28SiO v=1 5-4 (215.59595 GHz)
- Line: 28SiO v=0 5-4 (217.10498 GHz)
- Line: 28Si18O v=0 6-5 (242.09493 GHz)
- External data: CARMA SiO v=0 J=2-1 total intensity contours  
  > "overlaid with the contours of the total intensity of the $^{28}$SiO v=0 J=2-1 emission as observed by (cite: Plambeck09) using CARMA" (4.1.1) [from (cite: Plambeck09)]
- External data: Ammonia column density map of the hot core  
  > "overlaid with contours of the ammonia column density map (cite: Goddi11b) tracing dense gas in the hot core region" (4.1.2) [from (cite: Goddi11b)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: SV data calibrated prior to public release  
  > "The ALMA SV data were calibrated prior to public release." (2 Observations and Imaging)
- flux calibrator: Callisto absolute flux; J0607-085 (1.4 Jy) bandpass and phase  
  > "Callisto served as the absolute flux calibrator and the quasar J0607-085, with a flux of 1.4 Jy, was used as both bandpass and phase calibrator." (2 Observations and Imaging)
- flux scale uncertainty: _not stated_
- self calibration: single step phase-only on strongest emission feature in each cube; more steps did not help  
  > "In each data cube, we used the strongest emission feature to perform a single step, phase-only self-calibration." (2 Observations and Imaging)

### Imaging

- task: CASA; uvcontsub for continuum subtraction  
  > "used the *uvcontsub* task which fits a model to the continuum and subtracts it afterwards" (2 Observations and Imaging)
- deconvolver: _not stated_
- weighting robust: Briggs, robustness 1  
  > "a Briggs weighting with a robustness parameter of 1" (2 Observations and Imaging)
- uv taper: _not stated_
- cell size: 0.3"  
  > "we used a pixel size of 0$\ensuremath{''}$3" (2 Observations and Imaging)
- image size: 30"x30"  
  > "an imagesize of 30$\ensuremath{''}$ $\times$ 30$\ensuremath{''}$" (2 Observations and Imaging)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: identified per spectral window but ranges not given  
  > "We identified all channels with no line emission in each spectral window containing an SiO line" (2 Observations and Imaging)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: ~0.01 Jy/beam line-free; up to 0.3 Jy/beam in strongest channels  
  > "The rms noise in the line-free channels was about 0.01 Jy beam$^{-1}$ while it was up to 0.3 Jy beam$^{-1}$ in the channels with the strongest emission." (2 Observations and Imaging)

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for uvcontsub and fit order
- Deconvolver, clean threshold, masks and iterations
- Self-calibration solint
- CASA version
- Which SV datasets/execution blocks and any reprocessing
- Region/angular size used for brightness temperature
- Exact velocity-channel rebinning procedure

## Analysis recipe

1. **Continuum subtraction and cleaning of SiO cubes**: uvcontsub on line-free channels, clean with Briggs weighting, one phase-only self-cal  
  > "The first step of the SiO line imaging process was the continuum subtraction." (2 Observations and Imaging)
   - software: CASA
   - parameter: robust=1, 0.3" pixels, 30" image  
  > "a pixel size of 0$\ensuremath{''}$3, an imagesize of 30$\ensuremath{''}$ $\times$ 30$\ensuremath{''}$ and a Briggs weighting with a robustness parameter of 1" (2 Observations and Imaging)
   - fitting: _not stated_
   - validation: further self-cal steps tested, no significant improvement  
  > "Tests with further steps of self-calibration did not improve the image quality significantly." (2 Observations and Imaging)
2. **Gaussian fits to v=1 emission per channel**: 2-D elliptical Gaussian fit in each channel above 4 sigma in at least six connected pixels; errors 0.5*beam/SNR  
  > "Relative positional errors are given by $\delta \theta=0.5\theta_B/SNR$, where $\theta_B$ is the FWHM of the synthesized beam." (3.1)
   - fitting: 2-D elliptical Gaussian per channel  
  > "we fitted a two-dimensional elliptical Gaussian model to the unresolved emission, in every velocity channel" (3.1)
   - validation: compared with J=1-0 maser structure of Matthews10  
  > "The velocity structure obtained from our Gaussian fits is consistent with the one found for the masing $^{28}$SiO v=1 and v=2 J=1-0 transitions by (cite: Matthews10)" (3.1)
3. **Moment maps of v=0 28SiO and 29SiO**: moment 0 over -20 to 40 km/s; moment 1 with 4 sigma threshold  
  > "The moment 0 map is obtained integrating the emission at each pixel in the velocity range from -20 to 40 km s$^{-1}$" (3.3)
   - fitting: _not stated_
   - validation: compared with CARMA J=2-1 and J=8-7 SiO features to exclude contaminants  
  > "we exclude contamination from other molecular species, i.e. they must be associated with SiO emission." (4.1.1)
4. **Brightness temperature**: Tb=(S lambda^2)/(2 k_B dOmega); lower limit for unresolved v=1, integrated over source size for v=0  
  > "$T_b=(S\lambda^2)/(2k_Bd\Omega)$, where $S$ is the flux, $\lambda$ the wavelength and $d\Omega$ the solid angle of the source." (4.2)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : imaging, uvcontsub, cleaning, self-calibration  
  > "For imaging we used the Common Astronomy Software Applications (CASA)." (2 Observations and Imaging)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 28SiO v=1 peak flux | 44.97 | not stated | Jy | 1 | SiO v=1 / 215.59595 / 5-4 / 1.75$\times$1.18; 0.98 / 44.97 / 28 / $\geq$580 |
| 28SiO v=1 brightness temperature | >=580 | lower limit | K | 4 | we derive a brightness temperature $T_b\sim$580 K |
| 28SiO v=0 peak flux | 72.96 | not stated | Jy | 1 | SiO v=0 / 217.10498 / 5-4 / 1.72$\times$1.17; 1.29 / 72.96 / 55 / $\geq$50 |
| 28SiO v=0 and 29SiO v=0 brightness temperatures | ~50 K and ~100 K | not stated | K | 4 | We obtained brightness temperatures of $\sim$50 K and $\sim$100 K for the $^{28}$SiO and the $^{29}$SiO isotopologue, respectively. |
| v=1 position errors | 10 to 50 | not stated | mas | 2 | Errors range from 10 mas for the brightest channels to 50 mas in the channels with weakest emission. |

## Qualitative findings

- Ground-state SiO traces a bipolar NE-SW outflow with complex large-scale velocity structure (blue arc, red arm, high-velocity wing) likely due to environment interaction  
  > "the large scales (500-5000 AU) probed by thermal SiO with ALMA reveal a complex structure and velocity field" (abstract)

## Claim tuples

- H: Does the large-scale outflow show rotation? | E: Moment maps of 28SiO and 29SiO J=5-4 compared with IR sources and ammonia | R: Blue-red asymmetry attributable to environment and contaminants | F: No evidence for rotation on thousands-of-AU scales | **supported**
- H: Is v=1 J=5-4 emission masing? | E: Line widths and per-channel Gaussian positions | R: Narrow peaks (~3.5 km/s), distribution like J=1-0 maser, Tb>=580 K | F: First evidence of >200 GHz SiO maser at Source I | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Two bipolar outflows, rotation, and precession rejected to explain velocity structure  
  > "but it is inconsistent with the strong evidence that Source I is a hard binary" (4.1.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Vibrationally excited emission unresolved at ~1.7"x1.2"; maser nature needs confirmation  
  > "If confirmed, this would be the first detection of high-frequency SiO maser emission" (4.2)
- Caveat (inferred, ours): Brightness temperatures depend on unspecified source sizes
- Caveat (inferred, ours): Line contamination identification is qualitative
- Caveat (inferred, ours): Maser claim rests on indirect arguments
- Caveat (inferred, ours): No flux uncertainty given

## Reproducibility

- Data public (paper): ALMA Science Verification data, publicly released  
  > "The ALMA SV data were calibrated prior to public release." (2 Observations and Imaging)
- Products in archive: _not stated_
- Missing: CASA version
- Missing: line-free channels
- Missing: clean parameters
- Data volume (inferred): ~100 GB
- Score (inferred): 3/5, Public SV data, partial imaging recipe, qualitative main results.
- Rediscovery candidate: no, Main results largely qualitative and several imaging parameters unstated.

## Links

- Companion: (cite: Zapata12) (Subset of same ALMA data (J=5-4 v=0) suggesting rotation)
- Companion: (cite: Matthews10) (VLBI SiO maser J=1-0 comparison)
- Related: ALMA Science Verification Orion KL spectral survey

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
 "codes_not_in_obscore": [
  "2011.0.99001.CSV"
 ],
 "obscore_codes_not_in_card": [
  "2011.0.00009.SV"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 62,
  "stated": 34,
  "rate": 0.548
 },
 "evidence_ok": true
}
```
