# Constraining the Planetary System of Fomalhaut Using High-resolution ALMA Observations

`2012ApJ...750L..21B` | The Astrophysical Journal Letters 2012 | first author: Boley, A. C. | arXiv: 1204.0007 | DOI: 10.1088/2041-8205/750/1/L21

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: debris_disks
- Question: What is the width and morphology of the Fomalhaut parent-body ring at 850 um, and what origin (planet sculpting, collision remnant, shepherd planets) best explains it?  
  > "These observations demonstrate that the parent body population is 13-19 AU wide with a sharp inner and outer boundary." (abstract)
- Target **Fomalhaut debris ring**: coordinates RA 22h57m38.65s, Dec -29d37m12.6s (J2000)  
  > "centered on the expected position of Fom b at RA = 22h:57m:38.65s and $\delta$ = -29d:37’:12.6” (J2000, proper motion included)." (2 Observations and Reduction); "The synthesized beam effective area is $\sim 2~{\rm AU}^2$ at 7.69 pc." (Results); z/distance 7.69 pc  
  > "centered on the expected position of Fom b at RA = 22h:57m:38.65s and $\delta$ = -29d:37’:12.6” (J2000, proper motion included)." (2 Observations and Reduction); "The synthesized beam effective area is $\sim 2~{\rm AU}^2$ at 7.69 pc." (Results); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00191.S
- bands: 350 GHz (850 um), upper and lower sidebands at 357 and 345 GHz  
  > "The observations were taken at 357 and 345 GHz (in the upper and lower sidebands)" (2 Observations and Reduction)
- frequencies and spectral setup: Frequency Domain Mode, dual polarization, 4x1875 MHz bandpasses (2 per sideband)  
  > "using the Frequency Domain Mode in dual polarization with $4\times$1875 MHz bandpasses (2 in each of the sidebands)" (2 Observations and Reduction)
- continuum bandwidth: _not stated_
- arrays: ALMA Cycle 0, compact configuration, 13-15 antennas  
  > "Fomalhaut’s ring was observed using ALMA cycle 0 in the compact configuration" (2 Observations and Reduction)
- configurations: _not stated_
- baselines: 14 to 175 m  
  > "measuring projected baselines from 14 to 175m" (2 Observations and Reduction)
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: RMS ~60 uJy/beam  
  > "the RMS is $\sim60\ \mu \rm Jy~\rm beam^{-1}$ (0.32 mK)" (Results)
- time on source: 140 min  
  > "The total on-source integration time was 140 min." (2 Observations and Reduction)
- observing dates: 22-23 Sep 2011 and 18 Oct 2011  
  > "| 22/09/2011 | 23:45:00.0 |    25     |    13    | 0.63 |" (Table 1)
- pi or archival as stated: _not stated_
- External data: Ellipse fits to optical images (center offset, a=18.31 arcsec, PA=336 deg, i=66 deg)  
  > "The ellipses have a $a=18.31$” and a position angle (${\rm PA}=336^{\circ}$)." (Results) [from K05 (cite: kalas_etal_2005_nature_435)]
- External data: Stellar temperature and radius (8750 K, 1.82 Rsun)  
  > "$T_{\rm star}=8750$ K and $R_{\rm star}=1.82 R_{\odot}$ are the stellar temperature and radius" (Results) [from (cite: difolco_2004_AnA_426)]

## Processing

### Calibration

- pipeline or manual: Manual CASA reduction: WVR, Tsys, bandpass and gain calibration  
  > "calibration involved removing the effects of rapid atmospheric variations at each antenna using the WVR data" (2 Observations and Reduction)
- casa version: CASA 3.4  
  > "Data were reduced using CASA 3.4" (2 Observations and Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Neptune (Butler-JPL-Horizons 2010 model)  
  > "Neptune was used as an absolute flux calibrator, and J1924-292 for bandpass calibration." (2 Observations and Reduction)
- flux scale uncertainty: ±10%  
  > "which gives an estimated systematic flux uncertainty of $\pm$10%" (2 Observations and Reduction)
- self calibration: _not stated_

### Imaging

- task: CLEAN, Cotton-Schwab, all channels combined to continuum  
  > "CLEANed using the Cotton-Schwab algorithm, combining all channels to give the final continuum image" (2 Observations and Reduction)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: Airy voltage pattern, effective dish 10.7 m, blockage 0.75 m  
  > "voltage pattern for an Airy function in with an effective dish diameter of 10.7 m, a blockage diameter of 0.75 m" (2 Observations and Reduction)
- array combination: _not stated_
- smoothing: spectrally binned to 49 MHz channels  
  > "The calibrated measurement set was spectrally binned to a channel spacing of 49MHz" (2 Observations and Reduction)
- final beam: _not stated_
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- Weighting/robust, cell and image size, clean threshold and masks
- Synthesized beam size and PA
- Sky-model fitting method, parameter priors and likelihood
- Details of surface-brightness model (visibility vs image fitting)
- Phase calibrator flux and self-calibration status
- Dust opacity used for mass estimate
- N-body initial planet parameters for each run

## Analysis recipe

1. **Image continuum**: CLEAN of calibrated, binned data; primary beam correction  
  > "CLEANed using the Cotton-Schwab algorithm, combining all channels to give the final continuum image" (2 Observations and Reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure ring radial profile**: Deprojected slices through ansa, Gaussian fits; 7 slices with bilinear interpolation  
  > "Surface brightness profiles of the ring (Fig. 2) are taken along the 7 slices shown in Figure 1 using bilinear interpolation." (Results)
   - assumption: Ellipses are sky-projected circles  
  > "Assuming the ellipses represent sky-projected circles" (Results)
   - fitting: Single/double Gaussian fits  
  > "Each slice can be fit by a single Gaussian except slice 4, which requires a double Gaussian" (Results)
   - validation: _not stated_
3. **Fit sky models of ring**: Gaussian and power-law surface density models compared to data with residual image  
  > "The best-fit models with a Gaussian distribution have a scale height corresponding to an opening angle of $1.0^{\circ}\pm 0.25$" (Results)
   - fitting: _not stated_
   - validation: Residual image inspection  
  > "The NE is not subtracted in the residual image (Fig. 1, bottom-right)" (Results)
4. **Estimate mm grain mass and mass loss**: Optically thin emission with s~1 mm, rho~2.5 g/cc, Tg~48 K; collisional timescale  
  > "We estimate the mm grain mass by assuming the ring is optically thin and comprised of grains with $s\sim 1$ mm and $\rho_s\sim2.5$ g/cc." (Results)
   - assumption: Collisions are the main removal mechanism  
  > "If collisions are the main removal mechanism of mm grains" (Results)
   - fitting: _not stated_
   - validation: _not stated_
5. **N-body shepherd planet simulations**: Two planets, 1e5 massless particles, 1e8 yr integration  
  > "For each run, $10^5$ massless particles are placed between $r_{inner}$ and $r_{outer}$ with a surface density profile $\propto r^{-1}$" (Discussion)
   - software: Mercury
   - parameter: Bulirsch-Stoer; planet eccentricities set so planetesimals at ~143 AU have e~0.11  
  > "using the Bulirsch-Stoer algorithm in Mercury" (Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 3.4: Calibration and imaging  
  > "Data were reduced using CASA 3.4" (2 Observations and Reduction)
- **Mercury** : N-body simulations of shepherd planets  
  > "using the Bulirsch-Stoer algorithm in Mercury" (Discussion)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Ring FWHM (Gaussian model) | 16 | ±3 | AU | 3 | a ${\rm FWHM} =16 \pm 3$ AU |
| Opening angle | 1.0 | ±0.25 | deg | 3 | an opening angle of $1.0^{\circ}\pm 0.25$ |
| Total flux density (full ring) | ~85 | ~10% | mJy | 1 | we find a total flux density of $\sim 85$ mJy |
| Deprojected FWHM at ansa (corrected) | 1.87 | ±0.03 | arcsec | 2 | The ${\rm FWHM}= 1.87\pm0.03''$ and $1.85 \pm 0.03''$ for the corrected and uncorrected profiles |
| mm grain mass | 0.017 | not stated | Earth masses | 4 | $M_{\rm mm}\sim 0.017~{\rm M}_{\oplus}$ |
| Preferred inclination | 66.75 | not stated | deg | 3 | Models with $i=66.75^{\circ}$ and a total flux density of 80 mJy are preferred. |

## Qualitative findings

- Mm grains are much more tightly confined than micron grains, consistent with radiation pressure.  
  > "but the mm grains are much more tightly confined, consistent with radiation pressure effects." (Results)

## Claim tuples

- H: What is the width of the parent body ring? | E: Gaussian profile and sky-model fits to ALMA 850 um image | R: FWHM 16±3 AU, sharp edges | F: Parent bodies form a narrow ring 13-19 AU wide | **supported**
- H: Which origin best explains the ring? | E: Compare single planet, collision remnant, and shepherd planet N-body models | R: Shepherd planets reproduce narrow ring; ring too cold for flyby truncation | F: Shepherd planets favored | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Collision remnant of two planets and single-planet plus stellar flyby considered; ring seems too cold for flyby.  
  > "Fomalhaut’s parent body population may be too cold to be explained by this mechanism." (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Only half of the ring is observed so the ellipse cannot be reliably determined.  
  > "Without the second *ansa*, we cannot reliably determine the ellipse." (Results)
- Caveat (inferred, ours): Model fitting is unspecified (no likelihood/priors, no visibility-domain fitting)
- Caveat (inferred, ours): Mass estimate depends on assumed grain size and no opacity
- Caveat (inferred, ours): Shepherd planet conclusion is not unique

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: Model-fitting procedure and priors
- Missing: Full N-body setup
- Data volume (inferred): ~10-20 GB raw Cycle 0 data
- Score (inferred): 3/5, Data are Cycle 0 and identifiable, but imaging and model-fitting details are missing.
- Rediscovery candidate: no, Model-fitting recipe is incomplete, so numeric results cannot be reliably redone.

## Links

- Companion: (cite: ricci_etal_2012_arxiv) (Related ALMA Fomalhaut/grain modeling work)

## Checks

```json
{
 "quotes": 46,
 "quotes_ok": 46,
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
  "stated": 34,
  "rate": 0.5
 },
 "evidence_ok": true
}
```
