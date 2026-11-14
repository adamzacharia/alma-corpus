# Resolving CO (2-1) in z ∼ 1.6 Gas-rich Cluster Galaxies with ALMA: Rotating Molecular Gas Disks with Possible Signatures of Gas Stripping

`2019ApJ...870...56N` | The Astrophysical Journal 2019 | first author: Noble, A. G. | arXiv: 1809.03514 | DOI: 10.3847/1538-4357/aaf1c6

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, high_z_galaxies
- Question: Are molecular gas disks in z~1.6 cluster galaxies rotating, how large are they compared to stellar disks and the field, and is there evidence for gas stripping?  
  > "We compare the extent of the molecular gas component to that of the optical stellar component, measured with rest-frame optical *HST* imaging." (abstract)
- Target **SpARCS J022546-035517 (J0225) cluster, 8 CO-detected members**: coordinates _not stated_; z/distance z=1.60  
  > "The cluster redshift of $z=1.60$ is determined via $>20$ spectroscopically-identified cluster members." (2.1 A $z\sim1.6$ SpARCS Cluster); distance from spectroscopic cluster members  
  > "The cluster redshift of $z=1.60$ is determined via $>20$ spectroscopically-identified cluster members." (2.1 A $z\sim1.6$ SpARCS Cluster)

## Data provenance

- ALMA projects: 2017.1.01228.S, 2015.1.01151.S
- bands: Band 3, single pointing at 88 GHz  
  > "The data presented here thus consists of a single Band 3 pointing at 88 GHz, totaling 4 hours (2.7 hours on-source), with $\sim0.4$$^{\prime\prime}$ angular resolution." (2.2 ALMA Observations and Maps)
- frequencies and spectral setup: 1.875 GHz baseband, frequency division correlator mode  
  > "We used the 1.875 GHz baseband in the frequency division correlator mode to detect CO (2–1) at $z\sim1.6$." (2.2 ALMA Observations and Maps)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.4 arcsec; beam 0.50"x0.41"  
  > "a synthesized beam of 0.50$^{\prime\prime}$$\times$0.41$^{\prime\prime}$" (2.2 ALMA Observations and Maps)
- max recoverable scale: _not stated_
- sensitivity: ~0.1 mJy/beam per 50 km/s channel (central rms)  
  > "central rms of $\sim 0.1$ mJy beam$^{-1}$ per 50 ${\rm km}\,{\rm s}^{-1}$ channel" (2.2 ALMA Observations and Maps)
- time on source: 2.7 hours on-source (4 hours total)  
  > "totaling 4 hours (2.7 hours on-source)" (2.2 ALMA Observations and Maps)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (230.54 GHz)
- Other facility **HST WFC3 F160W**: Stellar half-light radii (rest-frame r-band)  
  > "namely the F160W filter on WFC3 aboard *HST*, corresponding to rest-frame $r$-band." (2.4 HST Sizes)
- External data: Field CO and optical sizes, high-z (PHIBSS)  
  > "The PHIBSS survey contains six star-forming galaxies with sub-arcsecond resolution CO (3–2) imaging" (2.5 Size Comparisons in the Literature) [from (cite: Tacconi13)]
- External data: Low-z field CO and optical sizes (BIMA)  
  > "The BIMA Survey provides 13 galaxies with measured optical disks from $R/J/K/I$ and gas disks from CO (1–0)" (2.5 Size Comparisons in the Literature) [from (cite: Regan01)]
- External data: Virgo CO sizes  
  > "The largest compilation of CO sizes of Virgo cluster galaxies is from (cite: Kenney88)." (2.5 Size Comparisons in the Literature) [from (cite: Kenney88)]
- External data: Stellar masses  
  > "$^{e}$ Described in detail in (cite: Nantais16)." (Table 1) [from (cite: Nantais16)]
- External data: Infrared SFRs  
  > "$^{f}$ Described in detail in (cite: Noble17)." (Table 1) [from (cite: Noble17)]

## Processing

### Calibration

- pipeline or manual: Standard ALMA Science Pipeline within CASA  
  > "We calibrated the data using the standard ALMA Science Pipeline within CASA (cite: McMullin07)" (2.2 ALMA Observations and Maps)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "we used an inverse-variance weighting function (i.e. natural) when imaging the visibilities" (2.2 ALMA Observations and Maps)
- uv taper: _not stated_
- cell size: 0.04 arcsec pixels  
  > "imaged the data cube with 0.04$^{\prime\prime}$ pixels and spectral resolutions of 50 and 100 ${\rm km}\,{\rm s}^{-1}$" (2.2 ALMA Observations and Maps)
- image size: _not stated_
- masking: minimal cleaning on bright sources, down to ~3 sigma  
  > "performed minimal cleaning on bright sources, down to a threshold of $\sim3\sigma$" (2.2 ALMA Observations and Maps)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied to final continuum-subtracted map  
  > "The final continuum-subtracted and primary-beam-corrected map" (2.2 ALMA Observations and Maps)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.50"x0.41"  
  > "a synthesized beam of 0.50$^{\prime\prime}$$\times$0.41$^{\prime\prime}$" (2.2 ALMA Observations and Maps)
- final rms: ~0.1 mJy/beam per 50 km/s  
  > "central rms of $\sim 0.1$ mJy beam$^{-1}$ per 50 ${\rm km}\,{\rm s}^{-1}$ channel" (2.2 ALMA Observations and Maps)

### Inherited from earlier work

- CO flux measurement approach  
  > "We adopt the same approach as in (cite: Noble17) to measure the CO flux." (2.3 CO (2–1) Sizes and Gas Masses) [from (cite: Noble17)]
- GALFIT wrapper for HST Sérsic fits  
  > "We use a GALFIT (cite: Peng02) wrapper, detailed in Matharu et al. (submitted)" (2.4 HST Sizes) [from Matharu et al. (submitted)]

### Not stated but needed to reproduce (our reading)

- Software versions (CASA, pipeline)
- Continuum-subtraction channel ranges
- Clean mask details and niter
- Flux/bandpass/phase calibrators
- Exact channel ranges for moment maps
- Fitting code for 2D Gaussians and spectra
- Matharu et al. GALFIT wrapper settings
- Gas fraction scaling-relation calculation details

## Analysis recipe

1. **Image cubes and moment maps**: Natural-weighted cubes at 50 and 100 km/s; moment 0 over channels with >~2 sigma emission; moment 1 from pixels >3 sigma  
  > "Integrated-intensity (i.e., moment 0) maps of the CO emission are created by collapsing the cube over frequency channels that encompass significant emission ($\gtrsim2\sigma$) for each source." (2.2 ALMA Observations and Maps)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure CO sizes**: 2D elliptical Gaussian fit within 3 sigma region of moment 0; R1/2 = geometric mean of HWHM axes, deconvolved  
  > "Within a $3\sigma$ region around each source, we model the flux using a two-dimensional Gaussian profile with an elliptical cross-section" (2.3 CO (2–1) Sizes and Gas Masses)
   - fitting: _not stated_
   - validation: Residuals within 0.6 of local pixel rms  
  > "Subtracting the model fit from the integrated-intensity image produces low residuals (all within 0.6 of the local pixel-to-pixel rms) in each case." (2.3 CO (2–1) Sizes and Gas Masses)
3. **CO flux and line width**: Extract spectrum within 4 sigma elliptical region, fit Gaussian (double Gaussian for J0225-303); errors from line-free channel rms  
  > "we extract spectral profiles defined over a 4$\sigma$ ($\sigma=\rm FWHM/2.355$) region on the full image cube." (2.3 CO (2–1) Sizes and Gas Masses)
   - fitting: _not stated_
   - validation: Fluxes of four earlier detections within 1.5 sigma of previous data  
  > "are all within 1.5$\sigma$ of the previous shallower data" (2.3 CO (2–1) Sizes and Gas Masses)
4. **Gas masses**: L'CO from Solomon05 formula; Mgas = alphaCO L'(2-1)/0.77  
  > "we assume sub-thermalized emission with brightness temperature ratio of 0.77 (cite: Daddi15; Genzel15) between $J=2$ to $J=1$, and an ${\alpha_{\rm CO}}$ conversion factor of 4.36" (2.3 CO (2–1) Sizes and Gas Masses)
   - assumption: _not stated_
   - fitting: _not stated_
   - validation: _not stated_
5. **Stellar sizes and size ratios**: GALFIT single-Sérsic fits to HST F160W; compare stellar-to-gas ratios with PHIBSS, BIMA, Virgo; KS test  
  > "to fit a single-component Sérsic profile and measure a half-light radius, $r_{e}$, for each galaxy." (2.4 HST Sizes)
   - software: GALFIT
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibration with ALMA pipeline and imaging  
  > "We calibrated the data using the standard ALMA Science Pipeline within CASA (cite: McMullin07)" (2.2 ALMA Observations and Maps)
- **GALFIT** : Sérsic fits to HST imaging  
  > "We use a GALFIT (cite: Peng02) wrapper" (2.4 HST Sizes)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mean stellar-to-gas size ratio, cluster | 1.3 | 0.2 | dimensionless | 5 | with a mean ratio of $1.3\pm0.2$ (using the standard error on the mean) |
| Mean ratio, PHIBSS field | 1.1 | 0.1 | dimensionless | 5 | with a mean ratio of $1.1\pm0.1$ |
| Mean ratio, Virgo | 1.8 | 0.2 | dimensionless | 5 | The mean ratio in Virgo ($1.8\pm0.2$) |
| Gas masses | ~1-25e10 | not stated | Msun | 4 | Our final sample consists of galaxies with gas masses $\sim 1-25\times10^{10}$ ${\rm M_{\ensuremath{\odot}}}$. |
| J0225-371 CO flux | 1.26 | 0.10 | Jy km/s | 3 | 1.26$\pm$0.10 |

## Qualitative findings

- Velocity gradients in six of eight galaxies; at least three likely rotating disks  
  > "we see evidence for velocity gradients in six of the eight cluster galaxies (75%)" (3.1)

## Claim tuples


## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Lower alphaCO in compressed or merging gas could explain high gas fractions  
  > "a lower ${\alpha_{\rm CO}}$ conversion may be appropriate for increased gas temperatures and velocity dispersions" (3.3)
- How they decided it was enough: _not stated_
- Limitation (authors): Small samples and inhomogeneous comparison data  
  > "inhomogeneity between molecular gas transitions, resolution scales, optical bands, and imaging depths precludes a direct comparison" (3.2)
- Caveat (inferred, ours): Size ratios rely on small samples and mixed methods
- Caveat (inferred, ours): Tails at only 2-3 sigma
- Caveat (inferred, ours): Fixed alphaCO assumed

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Calibrator and pipeline details
- Missing: Exact fitting code and channel selections
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Public data and simple methods, but many processing details are missing.
- Rediscovery candidate: yes, Data are public, the recipe is simple, and the results are numeric.

## Links

- Method: (cite: Noble17) (CO flux and SFR methods)
- Method: (cite: Nantais16) (Stellar masses and imaging)
- Companion: (cite: Noble17) (Cycle 3 integrated CO)
- Related: PHIBSS
- Related: SpARCS

## Checks

```json
{
 "quotes": 44,
 "quotes_ok": 44,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 35,
  "rate": 0.486
 },
 "evidence_ok": true
}
```
