# [C II] emission in z ∼ 6 strongly lensed, star-forming galaxies

`2016MNRAS.462L...6K` | Monthly Notices of the Royal Astronomical Society 2016 | first author: Knudsen, Kirsten K. | arXiv: 1603.02277 | DOI: 10.1093/mnrasl/slw114

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Is [C II] 158 um emission detectable in strongly lensed, sub-L* star-forming galaxies at z>6, and does it follow local SFR-L[CII] relations?  
  > "In this letter we present ALMA observations of [C ii] for two sub-$L^\ast$ galaxies at $z>6$." (Introduction)
- Target **A383-5.1**: coordinates _not stated_; z/distance z = 6.029 (Lya); z_[CII] = 6.0274  
  > "estimated magnification factors of $\mu = 11.4\pm1.9$ and $100\pm20$, respectively (cite: richard11; stark15)" (Introduction); distance from optical/UV redshift from richard11; [CII] redshift measured here  
  > "estimated magnification factors of $\mu = 11.4\pm1.9$ and $100\pm20$, respectively (cite: richard11; stark15)" (Introduction)
- Target **MS0451-H**: coordinates _not stated_; z/distance z = 6.703  
  > "MS0451-H | $6.703\pm0.001$" (Table 2); distance from Lya redshift; reference not clearly stated  
  > "MS0451-H | $6.703\pm0.001$" (Table 2)

## Data provenance

- ALMA projects: 2013.1.01241.S
- bands: Cycle-2; tuned to redshifted [CII] at 270.462 GHz (A383-5.1) and 246.727 GHz (MS0451-H)  
  > "for A383 at $z = 6.027$ [^2] the central frequency was 270.462 GHz and for MS0451-H at $z = 6.703$ it was 246.727 GHz." (2 Observations)
- frequencies and spectral setup: one spw of 1.875 GHz on the line; three continuum spws of 2 GHz each with 128 channels  
  > "one spectral window (spw) having a bandwidth of 1.875 GHz centered on the aforementioned frequencies, and the three other available spw’s used a continuum setup with a bandwidth of 2 GHz each" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15-350 m (MS0451-H); 15-540 m (A383-5.1)  
  > "baselines extending between 15 and 350 m for MS0451-H and 15 to 540 m for A383-5.1" (2 Observations)
- angular resolution: 0.86'' x 0.67'' (A383-5.1); 1.6'' x 0.9'' (MS0451-H)  
  > "The obtained resolution is $0.86'' \times 0.67''$ PA = 94$^\circ$ for A383-5.1 and $1.6'' \times 0.9''$ PA = 84$^\circ$" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 11 uJy/beam; 15.6 MHz channel rms 0.125 mJy/beam (A383-5.1), 0.163 mJy/beam (MS0451-H)  
  > "The rms in a 15.6 MHz channel near the redshifted line is 0.125 mJy beam$^{-1}$ and 0.163 mJy beam$^{-1}$ for A383-5.1 and MS0451-H, respectively." (2 Observations)
- time on source: 1.9 h (MS0451-H); 4.6 h (A383-5.1)  
  > "The integration time was 1.9 hours for MS0451-H and 4.6 hours for A383-5.1." (2 Observations)
- observing dates: December 2014, January and May 2015  
  > "The observations were carried out in December 2014, January and May 2015." (2 Observations)
- pi or archival as stated: _not stated_
- Line: [C II] 2P3/2 -> 2P1/2 (1900.537 GHz)
- Other facility **HST (CLASH)**: near-infrared F140W image for overlay  
  > "overlaid on a near-infrared *HST* F140W image from the CLASH survey" (3 Results)
- External data: magnifications and optical/UV redshift  
  > "estimated magnification factors of $\mu = 11.4\pm1.9$ and $100\pm20$, respectively (cite: richard11; stark15)" (Introduction) [from (cite: richard11; stark15)]
- External data: A383-5.1 metallicity log(Z/Zsun) = -1.33  
  > "finds that the metallicity is $\log(Z/Z_\odot) = -1.33$ for A383-5.1" (Discussion) [from (cite: stark15)]
- Simulation/model as data: Vallini et al. metallicity-dependent L[CII]-SFR relation compared with results  
  > "We show the Vallini et al. model results in Fig. [2]" (Discussion)

## Processing

### Calibration

- pipeline or manual: Observatory pipeline-reduced data used; no extra flagging or calibration  
  > "The pipeline reduced data delivered from the observatory was of sufficient quality, no additional flagging and further calibration was necessary." (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: pipeline products used as delivered  
  > "The pipeline reduced data delivered from the observatory was of sufficient quality" (2 Observations)
- flux calibrator: Uranus, J0423-013, J0238+166  
  > "| 14-01-2015 | 38 | Uranus | J0423$-$013 | J0239$-$0234 |" (Table 1)
- flux scale uncertainty: 10% (conservative)  
  > "A conservative estimate of the absolute flux calibration is $10\%$." (2 Observations)
- self calibration: attempted on a 2 mJy source; no significant sensitivity improvement  
  > "We attempted to self-calibrate using this relatively bright source, however, this did not significantly improve the sensitivity." (2 Observations)

### Imaging

- task: CASA  
  > "Reduction, calibration, and imaging was done using casa" (2 Observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "The data was imaged both as continuum and spectral cube using natural weighting." (2 Observations)
- uv taper: 2D Gaussian taper with 1'' width for spectral extraction cubes  
  > "imaged using natural weighting and tapering with 2D Gaussian with a corresponding $1''$ width" (3 Results)
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
- final rms: 11 uJy/beam continuum  
  > "in both cases the r.m.s. is 11 $\mu$Jy beam$^{-1}$" (2 Observations)

### Inherited from earlier work

- dust modified blackbody T = 35 K, beta = 1.6  
  > "assuming a modified blackbody spectrum with a temperature $T
= 35$ K and $\beta = 1.6$ (cite: remyruyer13)" (3 Results) [from (cite: remyruyer13)]
- L[CII] formula  
  > "$L_{\rm [CII]} = 1.04\times 10^{-3} S
\Delta V D_{\rm L}^2 \nu_{\rm obs}$ (cite: solomon05; carilliwalter13)" (3 Results) [from (cite: solomon05; carilliwalter13)]
- CMB effect on continuum  
  > "Following the analysis of (cite: dacunha13), we estimate that the CMB heating would increase the temperature by less than a per cent" (3 Results) [from (cite: dacunha13)]

### Not stated but needed to reproduce (our reading)

- CASA version
- Pipeline version
- Channel width and image size/cell size for cubes
- Exact aperture for spectrum extraction
- Continuum-collapsed channel range for size estimate
- Conversion from L_IR and L[CII] to SFR details (delooze14 relation coefficients)
- Integration range for upper limits

## Analysis recipe

1. **Image continuum and line cubes**: Natural-weighted continuum from all spws and cube of line spw; tapered cube (1'' Gaussian) for spectra  
  > "A continuum image was produced combining all spectral windows, while a spectral cube was constructed for the spectral window tuned to the redshifted [C ii] line." (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit [CII] line profile in A383-5.1**: Gaussian fit to extracted spectrum  
  > "We fit a Gaussian line profile to the extracted spectrum and use this to derive the line properties." (3 Results)
   - fitting: Gaussian profile; sampler/priors not stated  
  > "We fit a Gaussian line profile to the extracted spectrum and use this to derive the line properties." (Results)
   - validation: redshift compared with optical/UV and CIII] redshifts  
  > "which is in agreement with the optical/UV redshift of $6.029\pm 0.002$ (cite: richard11)" (3 Results)
3. **Upper limit for MS0451-H**: 5 sigma limit assuming line FWHM = 100 km/s channel rms 0.05 mJy/beam  
  > "Assuming this corresponds to the FWHM width of the line, we estimate a $5\sigma$ upper limit of 0.026 Jy km s$^{-1}$." (3 Results)
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive luminosities and SFRs**: L[CII] from formula; SFR from de Looze low-metallicity relation; L_IR from modified blackbody limit; correct for magnification  
  > "We use the relation for low-metallicity galaxies to estimate the SFR from $L_{\rm [CII]}$ under the assumption that the [C ii] line traces star formation in the galaxies." (3 Results)
   - assumption: T = 35 K, beta = 1.6, Chabrier IMF, CMB correction 14-20% missed continuum  
  > "about 14-20% of the intrinsic continuum flux density would be missed due to the CMB background emission" (3 Results)
   - fitting: _not stated_
   - validation: compared with local relations and models  
  > "The model results are consistent with our detection of A383-5.1, which suggests that metallicity plays an important role." (Discussion)

## Software

- **CASA** : reduction, calibration, imaging  
  > "Reduction, calibration, and imaging was done using casa" (2 Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| A383-5.1 [CII] central frequency | 270.4448 | 0.0061 | GHz | 2 | $\nu =  
270.4448\pm0.0061$ GHz |
| A383-5.1 FWHM | 100 | 23 | km/s | 2 | FWHM line width of $\Delta V = 100\pm 23$ km s$^{-1}$ |
| A383-5.1 integrated line intensity | 0.102 | 0.032 | Jy km/s | 2 | $I_{\rm [CII]} = 0.102 \pm 0.032$ Jy km s$^{-1}$ |
| A383-5.1 z_[CII] | 6.0274 | 0.0002 | dimensionless | 2 | $z_{\rm [CII]} = 6.0274\pm0.0002$ |
| A383-5.1 L[CII] | 8.9e6 | 3.1e6 | Lsun | 4 | $(8.9\pm3.1)\times10^{6}$ $^a$ |
| MS0451-H L[CII] upper limit | <3.0e5 | not stated | Lsun | 4 | $<3.0\times10^{5}$ $^b$ |
| A383-5.1 SFR_[CII] | 0.68 | 0.24 | Msun/yr | 4 | $0.68\pm0.24$ |
| Continuum 5 sigma upper limit | 55 | not stated | uJy | 1 | we place a $5\sigma$ upper level 55 $\mu$Jy |

## Qualitative findings

- A383-5.1 is the lowest L[CII] detection at z>6; MS0451-H limit lies ~1 dex below local SFR-L[CII] relations  
  > "making it the lowest $L_{\rm [CII]}$ detection at $z>6$." (abstract)

## Claim tuples

- H: [C II] is detectable in faint lensed z>6 galaxies | E: ALMA Cycle-2 observations of A383-5.1 and MS0451-H | R: A383-5.1 detected with L=8.9e6 Lsun; MS0451-H not detected | F: Detections possible but much fainter than predicted | **supported**
- H: Low metallicity explains the [CII] deficit | E: Compare with Vallini et al. models and dwarf galaxies | R: Results consistent with low-Z predictions | F: Metallicity may play a role but cannot be confirmed | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Self-calibration on bright continuum source did not help  
  > "this did not significantly improve the sensitivity" (2 Observations)
- How they decided it was enough: _not stated_
- Limitation (authors): Modest S/N makes source size hard to measure  
  > "due to the modest signal-to-noise ratio it is difficult to accurately measure its extent" (3 Results)
- Caveat (inferred, ours): Only one detection and one non-detection; small sample
- Caveat (inferred, ours): SFR from [CII] relies on a local low-Z relation
- Caveat (inferred, ours): Non-detection limit assumes line width of 100 km/s
- Caveat (inferred, ours): Magnification uncertainty for MS0451-H is large

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: CASA version
- Missing: imaging parameters (cell, size, channel width)
- Missing: spectrum extraction apertures
- Data volume (inferred): ~50-150 GB raw for two Cycle-2 projects
- Score (inferred): 3/5, Single archive project and simple analysis, but imaging and extraction details missing.
- Rediscovery candidate: no, Recipe lacks key imaging and extraction details, and the paper does not state public data availability.

## Links

- Companion: (cite: stark15) (counter-image spectroscopy and metallicity of A383-5.2)
- Related: CLASH

## Checks

```json
{
 "quotes": 53,
 "quotes_ok": 53,
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
  "facts": 70,
  "stated": 40,
  "rate": 0.571
 },
 "evidence_ok": true
}
```
