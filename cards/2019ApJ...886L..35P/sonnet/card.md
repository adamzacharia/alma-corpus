# ALMA C II 158 μm Imaging of an H I-selected Major Merger at z ∼ 4

`2019ApJ...886L..35P` | The Astrophysical Journal Letters 2019 | first author: Prochaska, J. Xavier | arXiv: 2005.10279 | DOI: 10.3847/2041-8213/ab55eb

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, milky_way_ism
- Question: Is the HI-selected (DLA) galaxy at z=3.7978 a major merger, and can DLA velocity widths (Delta v90) trace major mergers and the merger fraction at high z?  
  > "We propose that DLAs with high $\Delta v_{\rm 90}$ values are a signpost of major mergers in normal galaxies at high redshifts" (abstract)
- Target **DLA1201+2117_3.80 (J120110.31+211758.5)**: coordinates J120110.26+211756.2 (galaxy position from lower-resolution data); quasar J120110.31+211758.5  
  > "The $z = 3.7975$ DLA towards J120110.31+211758.5 (hereafter DLA1201+2117_3.80), with an HI column density of $N_{\rm HI}= 10^{21.35}~{\rm cm}^{-2}$" (2 Observations and Data Analysis); z/distance z = 3.7978  
  > "The $z = 3.7975$ DLA towards J120110.31+211758.5 (hereafter DLA1201+2117_3.80), with an HI column density of $N_{\rm HI}= 10^{21.35}~{\rm cm}^{-2}$" (2 Observations and Data Analysis); distance from [CII] redshift from earlier ALMA observations (Neeleman+17)  
  > "The $z = 3.7975$ DLA towards J120110.31+211758.5 (hereafter DLA1201+2117_3.80), with an HI column density of $N_{\rm HI}= 10^{21.35}~{\rm cm}^{-2}$" (2 Observations and Data Analysis)

## Data provenance

- ALMA projects: 2017.1.01052.S
- bands: Band 7  
  > "we used the ALMA Band-7 receivers to observe the $z = 3.7978$ galaxy in configuration C43-4" (2 Observations and Data Analysis)
- frequencies and spectral setup: four 1.875 GHz IF bands; one on [CII] at 396.127 GHz with 3840 channels, three others with 128 channels each for continuum  
  > "We used four 1.875 GHz IF bands for the observations, one centered on the redshifted \[CII\] 158 $\mu$m line frequency (at 396.127 GHz), with 3840 channels" (2 Observations and Data Analysis)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-4, Cycle 5  
  > "in configuration C43-4, with a higher angular resolution ($0.33\ensuremath{''}$, i.e. $\approx 2.3$ kpc at $z=3.7978$), in Cycle 5" (2 Observations and Data Analysis)
- baselines: _not stated_
- angular resolution: 0.36'' x 0.31'' (continuum); 0.37'' x 0.31'' (cube)  
  > "The spectral cube has an RMS noise of $250$ $\mu$Jy/Bm per 50 km/s channel, and an angular resolution of $0.37\ensuremath{''} \times 0.31\ensuremath{''}$." (2 Observations and Data Analysis)
- max recoverable scale: _not stated_
- sensitivity: continuum rms ≈ 30 uJy/beam; cube rms 250 uJy/beam per 50 km/s channel  
  > "The final naturally-weighted continuum image has a root-mean-square (RMS) noise value of $\approx 30 \mu$Jy/Bm" (2 Observations and Data Analysis)
- time on source: 2.25 h  
  > "for a total on-source time of 2.25 h" (2 Observations and Data Analysis)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: [CII] 158 um (not stated (observed at 396.127 GHz))
- Other facility **Keck/ESI**: metallicity and low-ionization metal-line velocity width Delta v90 of the DLA  
  > "Follow-up Keck/ESI observations yielded a high gas-phase metallicity (\[M/H\] $\approx -0.75$) and a large velocity width $\Delta v_{\rm 90}$" (2 Observations and Data Analysis)
- External data: Delta v90 distributions f(Δv90) of DLAs at z~2 and z~4 from high-resolution absorption studies  
  > "Figure [6](#fig:fdv) shows the $f(\Delta v_{\rm 90})$ distributions measured from high-resolution absorption studies of DLAs" (3.2 On the origin of high Δv90 DLAs) [from (cite: marcel13; rafelski+12)]
- External data: Directly observed major merger fractions from MUSE for comparison  
  > "They are compared with estimates of $f_{MM}^{\rm g}$ from the incidence of spectroscopically-confirmed galaxies with $\delta R< 25$ kpc" (3.3 Inferring the Major Merger Fraction) [from (cite: ventou+2017; ventou+2019)]
- External data: Earlier low-resolution ALMA [CII] detection and galaxy position  
  > "centered on the galaxy position as determined from the lower resolution data (J120110.26+211756.2)" (2 Observations and Data Analysis) [from (cite: neeleman+17)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline in CASA, then custom self-calibration on continuum  
  > "The initial data analysis was carried out with the ALMA pipeline in the Common Astronomy Software Application (casa) package" (2 Observations and Data Analysis)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 15% systematic  
  > "fluxes and quantities derived from them (e.g. SFR) have a systematic error of 15%" (Table 1)
- self calibration: a few rounds of phase-only, then a couple of amplitude-and-phase rounds until convergence; robust scheme with custom CASA routines; applied to line data; peak S/N 100 to 330  
  > "The self-calibration procedure involved a few rounds of imaging and phase-only self-calibration, followed by a couple of rounds of amplitude-and-phase self-calibration and imaging" (2 Observations and Data Analysis); "The peak signal-to-noise ratio on the image improved from $\approx 100$ before self-calibration to $\approx 330$ after self-calibration" (2 Observations and Data Analysis)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting for continuum image and cube  
  > "a spectral cube was made using the visibilities from the band centered on the redshifted \[CII\] 158 $\mu$m frequency, using natural weighting" (2 Observations and Data Analysis)
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
- final beam: 0.36'' x 0.31'' continuum; 0.37'' x 0.31'' cube  
  > "an angular resolution of $0.36\ensuremath{''} \times 0.31\ensuremath{''}$" (2 Observations and Data Analysis)
- final rms: 30 uJy/beam continuum; 250 uJy/beam per 50 km/s channel  
  > "The spectral cube has an RMS noise of $250$ $\mu$Jy/Bm per 50 km/s channel" (2 Observations and Data Analysis)

### Inherited from earlier work

- Rotating-disk cube-fitting code (MCMC) used to test single-disk model  
  > "using the fitting code described in (cite: neeleman+20)" (2 Observations and Data Analysis) [from (cite: neeleman+20)]
- Uncertainties of dust SED assumptions (T=35 K, beta=1.6)  
  > "For a discussion of the uncertainties of these assumptions for this galaxy see (cite: neeleman+17)." (3.1 The nature of a z ~ 4 merger) [from (cite: neeleman+17)]
- Cosmology  
  > "we adopt a $\Lambda$-Cold Dark Matter cosmology with cosmological parameters as defined in (cite: Planck2015)" (1 Introduction) [from (cite: Planck2015)]

### Not stated but needed to reproduce (our reading)

- Self-calibration solution intervals, number of rounds and the custom robust routines (not released)
- Line-free channels, continuum subtraction and image size/cell size
- Primary beam correction and CASA version
- Box-car integration velocity limits and aperture for each component
- Flux calibrators
- How Delta v90 f(Δv90) integrals were computed and data digitised
- Conversion from L_IR to SFR (calibration not given)

## Analysis recipe

1. **Calibrate and self-calibrate**: ALMA pipeline calibration, then iterative phase and amplitude+phase self-calibration on continuum; gains applied to line data  
  > "The antenna-based gains derived from the above procedure were then applied to the line data." (2 Observations and Data Analysis)
   - software: CASA
   - fitting: _not stated_
   - validation: peak S/N improved ~100 to ~330 and rms improved by ~1.7  
  > "the image RMS noise improved by a factor of $\approx 1.7$" (2 Observations and Data Analysis)
2. **Image continuum and [CII] cube; define components**: Naturally weighted continuum image and cube; moment maps and channel maps; regions A, B, C defined by lines in kpc offsets  
  > "A: Emission below the line $\Delta Y = -1.0\,\Delta X \rm +1.0\,kpc$" (2 Observations and Data Analysis)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Test single rotating-disk model**: Fit cube with single-disk model convolved with the beam; MCMC; residuals compared to rms  
  > "The best-fit parameters and uncertainties are then estimated through a Markov Chain Monte Carlo analysis of the parameter space." (2 Observations and Data Analysis)
   - fitting: _not stated_
   - validation: residuals significantly higher than RMS, so no single-disk model fits  
  > "we find that no single-disk model can reliable reproduce the observed \[CII\] 158 $\mu$m line-emission" (2 Observations and Data Analysis)
4. **Measure fluxes and derive luminosities and SFR per component**: Box-car integration on cube for [CII] fluxes; continuum flux converted to L_IR (8-1000 um) with modified blackbody; L_CII/L_IR ratios  
  > "we have analyzed our naturally-weighted data cube, using simple box-car integrations to estimate the integrated flux densities." (3.1 The nature of a z ~ 4 merger)
   - assumption: modified blackbody with T = 35 K and beta = 1.6  
  > "assuming the dust emits as a modified blackbody with $T = 35$ K and a Raleigh-Jeans slope of $\beta = 1.6$" (3.1 The nature of a z ~ 4 merger)
   - fitting: _not stated_
   - validation: compared to L_CII/L_IR of z>2 galaxies with modest SFR and SFR-L_CII local relations  
  > "These values are consistent with the local correlation between SFR and \[CII\] 158 $\mu$m line luminosity" (3.1 The nature of a z ~ 4 merger)
5. **Infer major merger fraction from DLA Delta v90 distribution**: Fraction of DLAs with Δv90 above threshold 150 km/s, corrected for cross-section weighting (A_merger = 2 to 4 A_DLA)  
  > "We make the ansatz that every DLA with $\Delta v_{\rm 90}> \Delta v_{\rm 90}^{\rm max}$ tags an ongoing major merger." (3.3 Inferring the Major Merger Fraction)
   - parameter: Δv90max = 150 km/s, varied 125-200 km/s  
  > "we allow $\Delta v_{\rm 90}^{\rm max}$ to range from $125$ to $200 \, \rm km \, s^{-1}$" (3.3 Inferring the Major Merger Fraction)
   - fitting: _not stated_
   - validation: compared with MUSE merger fractions  
  > "It is clear that our results are consistent with the directly observed merger fraction" (3.3 Inferring the Major Merger Fraction)

## Software

- **CASA** : pipeline calibration, self-calibration, imaging  
  > "The initial data analysis was carried out with the ALMA pipeline in the Common Astronomy Software Application (casa) package" (2 Observations and Data Analysis)
- **Neeleman+20 disk fitting code** : single rotating-disk fit with MCMC  
  > "using the fitting code described in (cite: neeleman+20)" (2 Observations and Data Analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total [CII] flux | 1.36 | 0.010 | Jy km/s | 4 | / 0.51 / 0.007 / 0.51 / 0.006 / 0.34 / 0.005 / 1.36 / 0.010 / |
| L_CII/L_IR component A / B / C / total | 2.5 / 3.4 / 5.8 / 3.3 (x1e-3) | 0.1 / 0.1 / 0.3 / 0.1 | dimensionless | 4 | / $L_{\rm C^+}$/ $L_{\rm IR}$ / $10^{-3}$ / 2.5 / 0.1 / 3.4 / 0.1 / 5.8 / 0.3 / 3.3 / 0.1 / |
| SFR of A and B | 10.8 and 7.8 | ±1.5 and ±1 | Msun/yr | 4 | (A) $\approx 10.8 \pm 1.5 M_{\odot}\, \, \rm yr^{-1}$ and (B) $\approx 7.8 \pm 1 M_{\odot}\, \rm yr^{-1}$ |
| Projected separation of A and B | ≈6 kpc, velocity separation ≈200 km/s | not stated | kpc; km/s | 2 | projected separation $\delta R\approx 6$ kpc and a line-of-sight velocity separation of $\delta v \approx 200 \, \rm km \, s^{-1}$ |
| DLA merger fraction f_m^DLA at z~2 and z~4 | 0.14 and 0.18 | systematic from Δv90max 125-200 km/s | dimensionless | 5 | we estimate $f_m^{\rm DLA}= 0.14$ and $0.18$ for $z \sim 2$ and 4, respectively |
| Galaxy major merger fraction f_MM^g | ≈0.1 at z≈2.5 and z≈4 | large systematic | dimensionless | 5 | obtaining $f_{MM}^{\rm g}\approx 0.1$ at $z\approx 2.5$ and $z \approx 4$ |

## Qualitative findings

- Component C has about 2x higher L_CII/L_IR, likely stripped gas; velocity spread of [CII] matches the DLA metal-line profile.  
  > "Between these galaxies is a third emission component with highly elevated ($2\times$) \[CII\] 158 $\mu$m emission relative to the dust continuum" (abstract)

## Claim tuples

- H: The [CII] emission arises from merging galaxies rather than a single disk | E: Moment/channel maps and single-disk MCMC fit | R: No single disk fits; two dust peaks separated by ≈6 kpc, ≈200 km/s | F: A and B are a major merger | **supported**
- H: The merger enhances star formation | E: Derive SFR and L_CII/L_IR of A and B | R: Modest SFRs, consistent with local relations | F: No evidence of enhanced SFR | **supported**
- H: High Δv90 DLAs trace major mergers and give a merger fraction | E: Compare [CII] velocity profiles to metal absorption; apply Δv90 threshold to DLA distributions | R: f_MM^g ≈ 0.1 at z≈2.5 and 4 | F: Consistent with MUSE estimates but with large systematics; one example only | **partially**

## Reasoning

- Why this data: Kinematic complexity and high flux density in the low-resolution data motivated a more extended configuration  
  > "Owing to the kinematic complexity of the \[CII\] 158 $\mu$m line-emission already present in the low resolution observations and its relatively high flux density" (2 Observations and Data Analysis)
- Why this method: _not stated_
- Alternative: Chance projection cannot be strictly ruled out; probability true separation >30 kpc is <1%  
  > "Thus, the probability that the true separation is $> 30$ kpc is $< 1$%." (2 Observations and Data Analysis)
- How they decided it was enough: _not stated_
- Limitation (authors): Merger fraction is coarse with large systematic uncertainty; quantitative comparison with merger models beyond scope  
  > "We proceed with our nominal approach and emphasize that this yields only a coarse estimate of the major merger fraction." (3.3 Inferring the Major Merger Fraction)
- Caveat (inferred, ours): Single system underpins the Δv90–merger link
- Caveat (inferred, ours): Merger fraction ansatz relies on a sharp Δv90 threshold and assumed cross-section
- Caveat (inferred, ours): L_IR from a single-band continuum with assumed T and beta
- Caveat (inferred, ours): Table error bars on L_C+ appear as 0.0

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Custom robust self-calibration routines
- Missing: Imaging parameters (cell, size, masks)
- Missing: Aperture and velocity limits for fluxes
- Missing: Digitised Δv90 distributions
- Data volume (inferred): ~100-200 GB raw for a 2.25 h Band 7 observation with 3840-channel line window
- Score (inferred): 3/5, Data identified by project code and the main flux numbers are tabulated, but self-calibration, imaging parameters and aperture definitions are not detailed.
- Rediscovery candidate: no, The recipe is incomplete (imaging parameters and custom routines not stated) and the merger-fraction part depends on external distributions.

## Links

- Method: (cite: neeleman+20) (disk-fitting code used)
- Companion: (cite: neeleman+17) (original low-resolution ALMA detection of this DLA galaxy)
- Companion: (cite: neeleman+19) (another [CII] DLA emitter with companions at z≈4.224)
- Related: ALMA [CII] survey of 19 HI-selected DLA galaxies at z>~4
- Related: VLT/MUSE merger fraction surveys (Ventou+2017, 2019)

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
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 40,
  "rate": 0.556
 },
 "evidence_ok": true
}
```
