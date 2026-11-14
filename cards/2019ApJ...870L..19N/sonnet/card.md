# [C II] 158 μm Emission from z ∼ 4 H I Absorption-selected Galaxies

`2019ApJ...870L..19N` | The Astrophysical Journal Letters 2019 | first author: Neeleman, Marcel | arXiv: 1812.06113 | DOI: 10.3847/2041-8213/aaf871

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Can [C II] 158 um emission identify the galaxies associated with high-metallicity DLAs at z~4, and does the emission kinematics match the DLA absorption?  
  > "The primary aim of the ALMA observations was to use [C II] 158 $\mu$m emission to identify the galaxies associated with DLAs at $z \sim 4$." (Discussion and Summary)
- Target **QSO J0834+2140 (DLA z=4.3900)**: coordinates 08:34:29.44 +21:40:24.7 (J2000)  
  > "Right Ascension (J2000)                                      | 08:34:29.44" (Table 1); z/distance DLA z = 4.3900  
  > "Right Ascension (J2000)                                      | 08:34:29.44" (Table 1); distance from DLA absorption redshift  
  > "Right Ascension (J2000)                                      | 08:34:29.44" (Table 1)
- Target **QSO J1101+0531 (DLA z=4.3446)**: coordinates 11:01:34.36 +05:31:33.8 (J2000)  
  > "Right Ascension (J2000)                                      | 08:34:29.44            | 11:01:34.36" (Table 1); z/distance DLA z = 4.3446  
  > "Right Ascension (J2000)                                      | 08:34:29.44            | 11:01:34.36" (Table 1); distance from DLA absorption redshift  
  > "Right Ascension (J2000)                                      | 08:34:29.44            | 11:01:34.36" (Table 1)
- Target **QSO J1253+1046 (DLA z=4.6001)**: coordinates 12:53:53.35 +10:46:03.1 (J2000)  
  > "The $z=4.6001$ DLA towards QSO J1253$+$1046 is both our highest-redshift and our lowest-metallicity target" (Results); z/distance DLA z = 4.6001; QSO z = 4.908  
  > "The $z=4.6001$ DLA towards QSO J1253$+$1046 is both our highest-redshift and our lowest-metallicity target" (Results); distance from DLA absorption redshift  
  > "The $z=4.6001$ DLA towards QSO J1253$+$1046 is both our highest-redshift and our lowest-metallicity target" (Results)
- Target **QSO PSS1443+2724 (DLA z=4.2241)**: coordinates 14:43:31.17 +27:24:36.7 (J2000)  
  > "The $z=4.2241$ DLA towards PSS1443$+$2724 has" (Results); z/distance DLA z = 4.2241  
  > "The $z=4.2241$ DLA towards PSS1443$+$2724 has" (Results); distance from DLA absorption redshift  
  > "The $z=4.2241$ DLA towards PSS1443$+$2724 has" (Results)

## Data provenance

- ALMA projects: 2015.1.01564.S, 2016.1.00569.S
- bands: Band 7  
  > "We used the ALMA Band-7 receivers to search for [C II] 158 $\mu$m emission in the fields of four DLAs" (Sample Selection, Observations and Reduction)
- frequencies and spectral setup: Four 1.875 GHz bands, 128 channels each; one centered on redshifted [C II], three for continuum  
  > "The ALMA observations used four 1.875 GHz bands, each sub-divided into 128 channels." (Sample Selection, Observations and Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: cube beams ~0.67x0.47 to 0.97x0.89 arcsec  
  > "Cube Resolution ($'' \times ''$)$^{\rm a}$                   | ($0.69 \times 0.56$)   | ($0.97 \times 0.89$)" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: Continuum RMS 16.4-26.2 uJy/beam; per-channel RMS 0.17-0.29 mJy/beam  
  > "RMS per channel (mJy beam$^{-1}$)                            | 0.17                   | 0.27                   | 0.19                   | 0.29" (Table 1)
- time on source: 1.2-2.8 hours  
  > "The on-source times were $1.2 - 2.8$ hours." (Sample Selection, Observations and Reduction)
- observing dates: UT 2016 March 16 to UT 2017 January 29  
  > "between UT 2016 March 16 and UT 2017 January 29" (Sample Selection, Observations and Reduction)
- pi or archival as stated: PI Neeleman  
  > "PI: Neeleman" (Sample Selection, Observations and Reduction)
- Line: C+ [C II] 2P3/2-2P1/2 (158 um) (not stated)
- External data: DLA H I column densities, metallicities and Delta V90 from high-resolution optical spectra  
  > "high-resolution ($R > 10\,000$) optical spectra are available, allowing an accurate determination of the gas metallicity" (Sample Selection, Observations and Reduction) [from (cite: Rafelski2012; Rafelski2014)]
- External data: SFR from 160 um continuum conversion  
  > "Using the conversion rate between SFR and 160 $\mu$m continuum emission (cite: Calzetti2010)" (DLA J0834+2140) [from (cite: Calzetti2010)]
- External data: Previous results for DLA J1201+2117 and other z~4 DLA [C II] detections  
  > "Together with the results of (cite: Neeleman2017), the success rate of this program has been remarkable, with 5 detections out of 6 targets." (Discussion and Summary) [from (cite: Neeleman2017)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline in CASA, plus additional data editing  
  > "All of the data were calibrated using the ALMA pipeline, in the Common Astronomy Software Applications (cite: McMullin2007) package." (Sample Selection, Observations and Reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Done for J1101+0531 and J1253+1046 in AIPS  
  > "Two of the targets, QSO J1101$+$0531 and QSO J1253$+$1046, were sufficiently bright to perform self-calibration" (Sample Selection, Observations and Reduction)

### Imaging

- task: tclean in CASA  
  > "using the task `tclean` in CASA" (Sample Selection, Observations and Reduction)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "were obtained using natural weighting, to maximize sensitivity" (Sample Selection, Observations and Reduction)
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

- Systematic 0.5 dex uncertainty and single-wavelength modified black-body L_TIR estimate  
  > "there is an additional systematic uncertainty of $\approx 0.5$ dex when estimating $L_{\rm TIR}$ from a measurement at a single wavelength (cite: Neeleman2017)" (DLA J0834+2140) [from (cite: Neeleman2017)]

### Not stated but needed to reproduce (our reading)

- CASA and pipeline versions
- Array configurations and baselines
- Modified black-body parameters (T_dust, beta, CMB correction) for L_TIR
- Line-free channels and continuum subtraction
- Cell size, image size, clean threshold and masks
- Line extraction aperture / moment-0 procedure and S/N definition
- Rest frequency and L[CII] conversion formula details
- Flux calibrators and flux scale uncertainty
- Self-calibration solution intervals

## Analysis recipe

1. **Calibrate and image**: ALMA pipeline calibration, extra editing in CASA, self-cal in AIPS for two fields, natural-weighted tclean cubes and continuum  
  > "The final spectral cubes and continuum images were obtained using natural weighting, to maximize sensitivity, using the task `tclean` in CASA." (Sample Selection, Observations and Reduction)
   - software: CASA, AIPS
   - fitting: _not stated_
   - validation: _not stated_
2. **Detect [C II] emitters and measure line fluxes and luminosities**: Identify emission lines near DLA redshift, integrate flux, convert to L[CII]  
  > "implying a [C II] 158 $\mu$m line luminosity, $L_{\rm [C{\scriptscriptstyle II}]}$, of $(1.02 \pm 0.12) \times 10^8$ L$_\odot$ (cite: Solomon1992)" (DLA J0834+2140)
   - assumption: Flat LCDM, Omega_lambda=0.7, H0=70 km/s/Mpc  
  > "We assume a standard, flat, $\Lambda$-CDM cosmology with $\Omega_\lambda = 0.7$ and $H_0 = 70~\text{km}~\text{s}^{-1}~\text{Mpc}^{-1}$." (Introduction)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive L_TIR and SFR from continuum**: Modified black-body fit to continuum flux; SFR from Calzetti2010 160 um conversion; 3 sigma upper limits for non-detections  
  > "The total infrared luminosity, $L_{\rm TIR}$, as determined from a modified black-body fit to the continuum measurement is $(6.6 \pm 2.1) \times 10^{10}$ L$_\odot$." (DLA J0834+2140)
   - assumption: 0.5 dex systematic uncertainty on L_TIR  
  > "Systematic uncertainties are 0.5 dex." (Table 1)
   - fitting: _not stated_
   - validation: _not stated_
4. **Compare emission and absorption kinematics**: Compare [C II] line profiles/centroids to low-ionization metal absorption profile  
  > "In all of the 5 detected [C II] 158 $\mu$m emitters, the velocity difference between the emission and absorption line centroids is $< 100$ km s$^{-1}$." (Kinematics of Emission and Absorption Lines)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Pipeline calibration, editing, tclean imaging  
  > "Additional data editing was performed in CASA after the initial calibration." (Sample Selection, Observations and Reduction)
- **AIPS** : Self-calibration  
  > "which was done in the Astronomical Image Processing System (cite: Greisen2003) package" (Sample Selection, Observations and Reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| J0834+2140 [C II] integrated flux | 0.173 | 0.020 | Jy km/s | 2 | The total velocity-integrated line flux density is $0.173 \pm 0.020$ Jy km s$^{-1}$ |
| J0834+2140 L[CII] | 1.02e8 | 0.12e8 | Lsun | 2 | $1.02 \pm 0.12$ |
| J0834+2140 L_TIR | 6.6e10 | 2.1e10 | Lsun | 3 | is $(6.6 \pm 2.1) \times 10^{10}$ L$_\odot$ |
| J1101+0531 L[CII] | 7.0e7 | 2.3e7 | Lsun | 2 | $L_{\rm [C{\scriptscriptstyle II}]}$ = $(7.0 \pm 2.3) \times 10^7$ L$_\odot$ |
| PSS1443+2724 main emitter integrated flux | 0.846 | 0.063 | Jy km/s | 2 | $(0.846 \pm 0.063)$ Jy km s$^{-1}$ |
| PSS1443+2724 main emitter L[CII] | 4.7e8 | 0.4e8 | Lsun | 2 | $(4.7 \pm 0.4) \times 10^8$ L$_\odot$ |
| PSS1443+2724 second emitter L[CII] | 1.5e8 | 0.2e8 | Lsun | 2 | $(1.5 \pm 0.2) \times 10^8$ L$_\odot$ |
| PSS1443+2724 SFR | 15 | 4 | Msun/yr | 3 | SFR = $(15 \pm 4)$ M$_\odot$ yr$^{-1}$ |
| J1253+1046 SMG continuum flux density | 9.9 | 0.6 | mJy | 3 | the measured continuum flux density of $(9.9 \pm 0.6)$ mJy |

## Qualitative findings

- Five of six targeted high-metallicity z~4 DLAs have detected [C II] emitters, with impact parameters ~16-45 kpc  
  > "we now have detected [C II] 158 $\mu$m emission from five of six galaxies associated with targeted high-metallicity DLAs at $z \sim 4$." (abstract)

## Claim tuples

- H: High-metallicity z~4 DLAs can be associated with [C II]-emitting galaxies | E: ALMA Band 7 search in four DLA fields | R: [C II] emitters in three of four fields (five of six with earlier work) | F: [C II] is an efficient way to identify DLA galaxies | **supported**
- H: DLA galaxies resemble luminous LBGs in FIR properties | E: Compare L_FIR vs L[CII] to other populations | R: Similar to luminous LBGs and CSGs | F: Absorption-selected galaxies are similar to luminous LBGs | **supported**
- H: The DLA arises in a companion galaxy rather than the [C II] emitter | E: Compare emission and absorption line centroids | R: Offsets <100 km/s for all five emitters | F: Disfavors the companion scenario | **supported**

## Reasoning

- Why this data: High-metallicity DLAs are best candidates for [C II] detection given the [C II]-SFR correlation  
  > "further indicates that such high-metallicity DLAs are the best candidates for detections of [C II] 158 $\mu$m emission." (Sample Selection, Observations and Reduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): L_TIR from a single-wavelength continuum measurement has ~0.5 dex systematic uncertainty; some continuum associations are tentative  
  > "Therefore, we tentatively take this as the continuum flux measurement of the [C II] 158 $\mu$m emitter." (DLA J0834+2140)
- Caveat (inferred, ours): Small sample of four fields
- Caveat (inferred, ours): Low-significance detections (5.2 sigma) and 3.7-3.8 sigma continuum assignment
- Caveat (inferred, ours): SMG in J1253 assumed at quasar redshift without line confirmation

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Dust SED parameters
- Missing: Imaging parameters
- Missing: Line extraction and flux measurement details
- Missing: CASA version
- Data volume (inferred): ~50-100 GB raw for four fields
- Score (inferred): 3/5, Short Letter with brief processing description; key imaging and SED parameters missing, though numbers are tabulated.
- Rediscovery candidate: no, Recipe lacks details on line extraction, SED fitting and imaging parameters.

## Links

- Companion: Neeleman et al. 2017, Science (cite: Neeleman2017) (Earlier [C II] detections in z~4 DLAs; methods for L_TIR)
- Related: Cycle 6 DLA [C II] program

## Checks

```json
{
 "quotes": 55,
 "quotes_ok": 55,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2015.0.01564.S",
  "2016.0.00569.S"
 ],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 39,
  "rate": 0.527
 },
 "evidence_ok": true
}
```
