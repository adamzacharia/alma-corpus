# Suppression of star formation in the galaxy NGC 253 by a starburst-driven molecular wind

`2013Natur.499..450B` | Nature 2013 | first author: Bolatto, Alberto D. | arXiv: 1307.6259 | DOI: 10.1038/nature12351

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies
- Question: How much molecular gas is carried out by the starburst-driven wind of NGC 253, and what is the mass loading relative to the star formation rate?  
  > "These observations allow us to directly measure the molecular outflow rate to be" (abstract)
- Target **NGC 253**: coordinates reference position RA 00h47m33.15s, Dec -25°17'17.5" (J2000), as given in the Figure 1 caption  
  > "centered on the reference position" (Figure 1 caption); "a nearby [15] starburst galaxy (D~3.4 Mpc)" (abstract); z/distance D~3.4 Mpc  
  > "centered on the reference position" (Figure 1 caption); "a nearby [15] starburst galaxy (D~3.4 Mpc)" (abstract); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00172.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: Cycle 0, ~16 antennas, 7-pointing mosaic, combined with Mopra single-dish  
  > "our cycle 0 observations use ~16 antennas" (Supplementary Information); "(our cycle 0 observations use ~16 antennas, offering limited sampling of the Fourier plane)" (Supplementary Information 1)
- configurations: _not stated_
- baselines: shortest projected baseline ~20.2 m  
  > "(shortest projected baseline ~20.2 m)" (Supplementary Information)
- angular resolution: 3.4"x3" (θ~3.2")  
  > "The interferometer configuration provided an angular resolution of 3.4”×3” oriented approximately N-­‐S" (Supplementary Information 1)
- max recoverable scale: _not stated_
- sensitivity: ~6 mJy/beam in 2.5 km/s channels (thermal); effective 8-16 mJy/beam given dynamic range ~250  
  > "We attain an rms of ~6 mJy beam [-­‐1] in 2.5 km s [-­‐1] channels in thermal noise." (Supplementary Information 1)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO J=1-0 (not stated)
- Other facility **Mopra**: single-dish CO map used to fill in missing short spacings  
  > "to partially fill in the long spatial frequencies missing in the interferometric ALMA observations" (Supplementary Information 1)
- Other facility **HST**: archival WFC3 H-band and Paschen beta images, used for stellar surface density and shell counterparts  
  > "We estimate the surface density in the central region using the HST archival H-­‐band (F160W) image from WFC3." (Supplementary Information 2)
- External data: SFR ~2.8 Msun/yr from radio continuum and far-infrared  
  > "determined from radio continuum and far-­‐infrared measurements [28]" (main text) [from Ott et al. 2005 (ref 28)]
- External data: _not stated_ [from Westmoquette et al. 2011 (ref 18)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: iterative self-calibration on the source continuum after phase calibrator solution  
  > "we further iteratively self-­‐calibrated the source on its continuum, which substantially reduced the phase noise." (Supplementary Information 1)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5  
  > "using robust weighing with Briggs parameter 0.5" (Supplementary Information)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: channel maps not corrected for illumination; Fig. 3 corrected  
  > "The panels are not corrected by field-­‐of-­‐view illumination" (Figure 2 caption)
- array combination: CLEANed ALMA feathered with Mopra; combined cube used as prior for a new CLEAN deconvolution  
  > "We then used the combined cube as the prior for a deconvolution of the ALMA observations using CLEAN." (Supplementary Information)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- CASA version and calibrators
- Mopra map details and feathering parameters
- cell size, image size, masks, CLEAN thresholds
- self-cal solution intervals
- continuum subtraction and line-free channels
- method for defining outflow components and measuring LCO, vw, rw
- shell radii and velocity measurement procedure

## Analysis recipe

1. **Reduce and image CO(1-0) cube**: Calibrate, self-calibrate, CLEAN, feather with Mopra, re-CLEAN  
  > "We reduced the data using the CASA and Miriad software packages." (Supplementary Information)
   - software: CASA, Miriad
   - parameter: Briggs robust 0.5  
  > "using robust weighing with Briggs parameter 0.5" (Supplementary Information)
   - fitting: _not stated_
   - validation: _not stated_
2. **Convert CO luminosity to molecular mass**: Optically thin alpha_CO for wind; alpha_CO≈1 for shells  
  > "For the galactic wind we adopt an optically thin conversion factor [31]" (Supplementary Information)
   - parameter: _not stated_
   - assumption: Tex≈30 K, CO/H2≈1e-4, optically thin  
  > "an excitation temperature T ex ≈30 K and an abundance CO/H 2 ≈10 [-­‐4]" (Supplementary Information 2)
   - fitting: _not stated_
   - validation: shell alpha_CO checked against 13CO/12CO modeling and stellar surface density  
  > "This value also agrees well with a correction to the Galactic X CO values based on the measured stellar surface density" (Supplementary Information)
3. **Compute mass outflow rate and loading**: Mdot = 2 alpha_CO L_CO v_w tan i / r_w with median tan i ~3  
  > "has a median value of tan i ~3., which we adopt in our calculation (equivalent to i ~72°)." (Supplementary Information)
   - assumption: outflow inclination from cone of 60° opening angle centered on i=78°  
  > "The distribution of the de-­‐projection factor for a cone centered on this inclination and with the observed opening angle" (Supplementary Information 2)
   - fitting: _not stated_
   - validation: alternative parameters (Tex, abundance, inclination) tested to see when Mdot≈SFR  
  > "Obtaining an outflow rate similar to the SFR would require decreasing the CO excitation to T ex ~10 K" (main text)

## Software

- **CASA** : data reduction  
  > "We reduced the data using the CASA and Miriad software packages." (Supplementary Information)
- **Miriad** : data reduction  
  > "We reduced the data using the CASA and Miriad software packages." (Supplementary Information)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| outflowing molecular mass | 6.6e6 | not stated | Msun | 2 | This results in a total outflowing molecular mass M mol ~6.6×10 [6] M |
| CO luminosity of wind | 2.0e7 | not stated | K km/s pc2 | 2 | adds up to _L_ _CO_ ≈ 2.0×10 [7] K km s [-­‐1] pc [2] |
| mass loading | η≥1, likely ~3 | not stated | dimensionless | 3 | the mass loading of the wind is certainly η≥1 from our lower limit, and likely η~3. |

## Qualitative findings

- Extraplanar molecular gas follows Halpha filaments and connects to expanding shells in the starburst region  
  > "the extraplanar molecular gas closely tracks the Hα filaments" (abstract)

## Claim tuples

- H: The molecular wind removes gas at a rate comparable to or above the SFR | E: ALMA+Mopra CO(1-0) mapping with conservative alpha_CO and geometric corrections | R: Mdot~9 Msun/yr (lower bound ~3) versus SFR~2.8 | F: Starburst wind limits star formation, η≥1 | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Outflow rate is uncertain due to alpha_CO and geometry  
  > "with considerable uncertainty due to α CO and the geometrical corrections." (main text)
- Caveat (inferred, ours): alpha_CO for the wind is unmeasured
- Caveat (inferred, ours): Outflow geometry assumed from Halpha
- Caveat (inferred, ours): Separating wind from disk emission is subjective

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Reduction scripts and parameters
- Missing: Mopra data
- Missing: component masks
- Data volume (inferred): ~50-100 GB
- Score (inferred): 3/5, Data are archival-style Cycle 0 but processing details are sparse.
- Rediscovery candidate: no, Recipe incomplete; Mopra data and component definitions not given.

## Links

- Method: Bolatto, Wolfire & Leroy 2013 (ref 31) (CO-to-H2 conversion factor)

## Checks

```json
{
 "quotes": 36,
 "quotes_ok": 36,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 64,
  "stated": 26,
  "rate": 0.406
 },
 "evidence_ok": true
}
```
