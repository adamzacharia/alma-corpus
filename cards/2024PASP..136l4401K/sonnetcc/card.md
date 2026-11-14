# Radiative Transfer Modeling of Haumea's Dust Ring

`2024PASP..136l4401K` | Publications of the Astronomical Society of the Pacific 2024 | first author: Kalup, Csilla | arXiv: 2412.06544 | DOI: 10.1088/1538-3873/ad94a3

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: solar_system
- Question: Can the ring of Haumea be directly detected with ALMA and JWST, and what grain sizes and materials would its SED reveal, modeled with radiative transfer instead of a simple ring model  
  > "we highlight its sole detectability among Centaur/TNO rings using both the ALMA and the James Webb Space Telescope to provide direct constraints on the ring composition for the first time." (abstract); "providing a diagnostic tool to determine the dominant grain size and characteristic material of the ring" (abstract)
- Target **Haumea ring**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2022.1.01753.S
- bands: Band 7 (~870 um), ongoing measurements of Haumea; no ALMA data analysed in this paper  
  > "there are ongoing measurements on the Haumea system in band-7" (2.1 Direct Detectability of Centaur/TNO Rings)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: Cycle-9 antenna configuration; C-9 assumed for the sensitivity estimate  
  > "with the Cycle-9 antenna configuration (proposal ID 2022.1.01753.S)" (2.1 Direct Detectability of Centaur/TNO Rings); "with 8 h integration at the antenna configuration C-9, and assuming third quartile weather conditions" (4. Results)
- baselines: _not stated_
- angular resolution: <=30 mas required to resolve the rings  
  > "The required spatial resolution to resolve the rings is in the $\leq$30 mas range" (2.1 Direct Detectability of Centaur/TNO Rings)
- max recoverable scale: _not stated_
- sensitivity: 10 uJy/beam assumed (sensitivity calculator estimate, 8 h, band 7, C-9)  
  > "The black square represents the 10 $\mu$Jy beam$^{-1}$ sensitivity of ALMA observation in band-7 ($\sim$345 GHz, $\sim$870$\,\mu$m) with 8 h integration at the antenna configuration C-9" (5.1 Spectral Energy Distributions of the Ring Models)
- time on source: 8 h (assumed for the sensitivity estimate)  
  > "with 8 h integration at the antenna configuration C-9, and assuming third quartile weather conditions" (5.1 Spectral Energy Distributions of the Ring Models)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **JWST NIRCam F070W**: Predicted detectability of the ring in scattered light (5 sigma point source limit 0.07 uJy, 1 h); no data analysed  
  > "The black rectangle displays the wavelength range of the JWST NIRCAM F070W filter at a $5\sigma$ (point source) detection limit of 0.07 $\mu$Jy with 1 hour integration" (5.1 Spectral Energy Distributions of the Ring Models)
- Other facility **Herschel PACS and SPIRE**: Upper limits on the total thermal brightness of the Haumea system at 100 and 160 um, taken from Muller et al. 2019  
  > "The inverted triangles with the downward arrows represent the upper limits of the total brightness of the Haumea system at $100\,\mu$m and $160\,\mu$m (cite: Muller2019)." (5.1 Spectral Energy Distributions of the Ring Models)
- External data: Haumea ring radius and width from stellar occultation (r = 2287 km, w = 70 km), apparent opacity 0.555, and V-band ring contribution constraints (2.5% best fit, 5% upper limit)  
  > "Occultation chords define the radius of the ring, r = 2287$_{-45}^{+75}$ km, and using an apparent opacity of p’ = 0.555" (Introduction); "The empty circle shows the $2.5\%$ contribution, which was the best fit for the photometric data between 2005 and 2017." (5.1 Spectral Energy Distributions of the Ring Models) [from Ortiz et al. 2017 (cite: Ortiz2017)]
- External data: Upper limits on total thermal brightness of the Haumea system: 2.52e-3 Jy at 100 um and 2.66e-3 Jy at 160 um  
  > "derived upper limits on the total thermal brightness of $2.52\cdot 10^{-3}$ Jy and $2.66\cdot 10^{-3}$ Jy at 100 $\mu$m and 160 $\mu$m, respectively" (2. A Simple Ring Model) [from Muller et al. 2019 (cite: Muller2019)]
- External data: Geometric albedo p_V = 0.75 and q = 0.44 used for the Haumea body SED  
  > "the latest geometric albedo and phase angle values, $p_V$ = 0.75 and q = 0.44, derived by (cite: V22)" (5.1 Spectral Energy Distributions of the Ring Models) [from Verbiscer et al. 2022 (cite: V22)]
- External data: Volume-equivalent diameter of Haumea D_eq = 1595 km  
  > "assuming a volume-equivalent diameter of $D_{eq}$ = 1595 km (cite: Ortiz2012; Muller2019)" (5.1 Spectral Energy Distributions of the Ring Models) [from Ortiz et al. 2012; Muller et al. 2019 (cite: Ortiz2012; Muller2019)]
- External data: Ring opening angle B = 13.8 deg at the 2017 discovery  
  > "During the discovery of the ring in 2017, its opening angle was $B=13.8^{\circ}$ (cite: Ortiz2017)." (5.2 Comparison with Observational Constraints) [from Ortiz et al. 2017 (cite: Ortiz2017)]
- Simulation/model as data: RADMC-3D ring-element radiative transfer models for graphite, carbon, water ice, olivine and pyroxene grains, 0.1 to 1000 micron, 2017 geometry  
  > "We calculated carbon, graphite and water ice models, as well as olivine and pyroxene with varying magnesium content, and covered grain sizes from 0.1 to 1000 micron for each material." (3. Comparison with Planetary Rings and Comets)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
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

- Simple ring thermal model (ring particle temperature and brightness temperature equations)  
  > "A detailed description of this simple model and the related references can be found in (cite: Lellouch2017), where it was used to estimate the brightness of Chariklo in infrared and submillimeter wavelengths; we just recite the main equations here." (2. A Simple Ring Model) [from Lellouch et al. 2017 (cite: Lellouch2017)]
- Updated reflectivity, opacity and phase integral values for the ALMA band-7 simple-model flux prediction  
  > "partly revisited the thermal model flux prediction and provided flux density estimates for the ring in ALMA band-7 measurements using various reflectivities and updated opacity and phase integral values" (2. A Simple Ring Model) [from Kalup & Kiss 2023 (cite: Kalup2023)]

### Not stated but needed to reproduce (our reading)

- Ring optical depth and width values adopted in the RADMC-3D ring element
- Grain bulk density and the specific optool material (optical constant) entries used for each material
- Wavelength grid and photon packet count for RADMC-3D
- Heliocentric distance and solar geometry for 2017 and 2025
- Bond albedo, phase integral and reflectivity adopted for the simple model flux numbers
- Details of ALMA Cycle 9 observations (integration, uv coverage) and whether the data are analysed (they are not)

## Analysis recipe

1. **Predict ring flux with simple ring model**: Thermal ring model with particle temperature from absorbed sunlight, applied to ALMA band 7 at ~870 um for 2017 and 2025  
  > "derive $F_{\mathrm{ALMA}}$ flux densities at $\sim870\,\mu$m for 2017 January 21 and at the beginning of 2025 for comparison with the radiative transfer approach" (2. A Simple Ring Model)
   - parameter: rotation rate factor f = 2  
  > "$f$ is the rotation rate factor (assumed to be f = 2 here)" (2. A Simple Ring Model)
   - assumption: spectral and bolometric emissivity both equal 1  
  > "it is assumed that $\epsilon_{r,\lambda}$ = $\epsilon_{r,b}$ = 1" (2. A Simple Ring Model)
   - fitting: _not stated_
   - validation: _not stated_
2. **Compute grain opacities**: Complex opacities, scattering opacity and g anisotropy parameter from optool material library for given grain sizes  
  > "We use the *optool* package (cite: optool) to obtain the complex opacities of the grains, using materials from *optool*’s material library, assuming specific grain sizes." (4.1 General Setup)
   - software: optool
   - parameter: grain sizes 0.1 to 1000 micron; amorphous options used  
  > "covered grain sizes from 0.1 to 1000 micron for each material" (3. Comparison with Planetary Rings and Comets); "Therefore, we decided to use the amorphous options in our analysis." (5.1 Spectral Energy Distributions of the Ring Models)
   - assumption: porosity ignored  
  > "As a first approximation, we ignored porosity in our models." (4.1 General Setup)
   - assumption: simulation volume homogeneous in material  
  > "we assume that the whole simulation volume is homogeneous material-wise" (4.1 General Setup)
   - fitting: _not stated_
   - validation: _not stated_
3. **Radiative transfer of a ring element**: RADMC-3D calculation in a small ring element, flux scaled by ratio of ring area to simulated area; mean of pixels where tau is maximal  
  > "We approximate the ring by modeling the radiative transfer in a small element of the ring, and then multiplying the flux densities by the ratio of the ring area ($A_r$) to the area of the simulated region ($A_s$)." (4.2 Ring Element Model); "The mean values of these selected pixels provide the flux density at a specific wavelength." (4.2 Ring Element Model)
   - software: RADMC-3D
   - parameter: 128x128x8 cell simulation volume  
  > "we used a 128$\times$128$\times$8 cell simulation volume" (4.2 Ring Element Model)
   - parameter: Henyey-Greenstein anisotropic scattering  
  > "treated by applying the Henyey-Greenstein function" (4.1 General Setup)
   - assumption: Sun is a black body, T_eff = 5780 K, R = 6.96e5 km  
  > "The Sun is considered as a black body with $T_{\rm eff} = 5780$ K temperature and $R_\odot = 6.96\times10^5$ km radius." (4.1 General Setup)
   - assumption: ring homogeneous and thin, edge effects ignored  
  > "This model implicitly assumes that the ring is homogeneous, thin" (4.2 Ring Element Model)
   - fitting: _not stated_
   - validation: Compared with the simple ring model flux (181 uJy for ALMA in 2017)  
  > "This example clearly shows the versatile capabilities of the radiative transfer approach over the simple ring model" (5.2 Comparison with Observational Constraints)
4. **Build model SEDs and compare to Haumea body**: Ring SEDs for each material and grain size compared with a Near-Earth Asteroid Thermal Model SED of Haumea  
  > "We marked the approximate SED of Haumea as a black curve, which was calculated using a Near-Earth Asteroid Thermal Model" (5.1 Spectral Energy Distributions of the Ring Models)
   - parameter: beaming parameter eta = 2.5  
  > "We used a beaming parameter of $\eta$ = 2.5 to match the observed far-infrared flux densities presented in (cite: Muller2019)." (5.1 Spectral Energy Distributions of the Ring Models)
   - assumption: D_eq = 1595 km, p_V = 0.75, q = 0.44  
  > "assuming a volume-equivalent diameter of $D_{eq}$ = 1595 km (cite: Ortiz2012; Muller2019)" (5.1 Spectral Energy Distributions of the Ring Models)
   - fitting: _not stated_
   - validation: Checked against Muller et al. 2019 far-infrared upper limits  
  > "Our sum of the contribution of the main body and its ring aligns well with these constraints at the far-infrared." (5.2 Comparison with Observational Constraints)
5. **Extract V-band, ALMA and JWST flux densities**: V-band flux via filter-weighted integral of model SEDs; flux densities at ~870 micron for ALMA and F070W profile convolution for JWST  
  > "We extracted the flux densities at $\sim$ 870 micron for every grain size of the carbon, water and silicate models." (5.2 Comparison with Observational Constraints); "we obtained the flux densities for JWST by convolving the NIRCAM F070W filter profile in a similar way as we performed for the Johnson $V$ filter" (5.2 Comparison with Observational Constraints)
   - software: JWST Exposure Time Calculator, ALMA Sensitivity Calculator
   - fitting: _not stated_
   - validation: V-band ring contribution compared with the 2.5% best-fit of Ortiz et al. 2017  
  > "all the models are below the $2.5\%$ best fit model of (cite: Ortiz2017)" (5.2 Comparison with Observational Constraints)

## Software

- **RADMC-3D** : Radiative transfer of dust grains in the ring element, producing images and spectra  
  > "The radiative transfer modeling of the dust grains in the ring is performed using the RADMC-3D (cite: radmc)" (4. Radiative Transfer Modeling)
- **optool** : Complex opacities, scattering opacity and g anisotropy of the grains  
  > "using the scattering opacity and $g$ anisotropy parameters obtained for the specific material with *optool*" (4.1 General Setup)
- **Near-Earth Asteroid Thermal Model** : Approximate thermal SED of Haumea's body  
  > "which was calculated using a Near-Earth Asteroid Thermal Model (cite: Harris1998)" (5.1 Spectral Energy Distributions of the Ring Models)
- **JWST Exposure Time Calculator** : JWST NIRCam F070W 5 sigma detection limit for 1 h  
  > "as obtained with the JWST Exposure Time Calculator" (5.1 Spectral Energy Distributions of the Ring Models)
- **ALMA Sensitivity Calculator** : ALMA band 7 C-9 sensitivity estimate (8 h)  
  > "see the ALMA Sensitivity Calculator" (Footnotes)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Simple-model ALMA flux density of the ring at ~870 um, 2017 January 21 | 181 | not stated | uJy | 1 | We found that $F_{\mathrm{ALMA}}^{2017}=181\,\mu$Jy and $F_{\mathrm{ALMA}}^{2025}=287\,\mu$Jy, assuming this simple ring model. |
| Simple-model ALMA flux density of the ring at ~870 um, beginning of 2025 | 287 | not stated | uJy | 1 | We found that $F_{\mathrm{ALMA}}^{2017}=181\,\mu$Jy and $F_{\mathrm{ALMA}}^{2025}=287\,\mu$Jy, assuming this simple ring model. |
| Largest V-band ring contribution among radiative transfer models (100 nm water ice and 100 nm pyroxene) | 1.6 | not stated | percent of total system brightness | 5 | The models closest to this estimation are the $100\,$nm water ice and the $100\,$nm pyroxene models with a contribution of $1.6\%$. |
| Typical V-band brightness ratio of ring models | 0.1-0.2 | not stated | percent of total system brightness | 5 | However, most of the models show a brightness ratio of around 0.1–0.2%. |
| Ring opening angle range 2025 to 2040 | 20.9 to 35.2 | not stated | deg | 0 | it will rapidly change between 2025 and 2040 from $B=20.9^{\circ}$ to $B=35.2^{\circ}$ |

## Qualitative findings

- Carbon-rich models are observable with ALMA from about 10 um grains, silicates from about 100 um, and pure water ice rings only at millimeter sizes  
  > "carbon-rich models can be observed from $\gtrsim$ 10 $\mu$m with ALMA, while silicate models at around $\gtrsim$ 100 $\mu$m, and pure water ice rings only in the millimeter regime" (5.2 Comparison with Observational Constraints)
- Mid-infrared excess at 10-30 micron for carbon-rich or low-magnesium silicate models can exceed Haumea's own thermal emission, tracing 0.1-10 micron grains  
  > "we report a possibly observable mid-infrared excesses around 10–30 micron, where carbon-rich or silicate models, consisting of a lower amount of magnesium can be brighter than the thermal emission of Haumea itself" (6. Summary and conclusions)

## Claim tuples

- H: Which known Centaur/TNO rings can be directly detected with ALMA and JWST | E: Simple ring model flux and surface brightness estimates for Chariklo, Quaoar and Haumea rings compared with instrument resolution and sensitivity | R: Only the Haumea ring is bright enough for both ALMA/Band-7/C9 and JWST/NIRCam/F070W | F: Haumea is the sole detectable ring among Centaur/TNO rings with both facilities | **supported**
- H: Can the ring's V-band contribution of 2.5% from occultation-era photometry be matched by small-grain models | E: RADMC-3D V-band fluxes for several materials and 0.1-1000 micron grains | R: None of the models reach 2.5%; the best match is 1.6% for 100-200 nm water ice and pyroxene grains | F: No tested model reproduces the best-fit 2.5% contribution | **partially**
- H: Does the ring produce a detectable mid-infrared excess even if unresolved | E: Compare ring model SEDs with the thermal SED of Haumea's body | R: Between 10 and 30 micron the ring SED can exceed Haumea's thermal emission for carbon-rich and low-magnesium silicate models | F: Mid-infrared excess can trace small grains around the dwarf planet | **supported**
- H: Does the radiative transfer approach differ from the simple ring model | E: Compare ALMA flux density at ~870 micron across materials and grain sizes with the single simple model value | R: Radiative transfer fluxes vary with composition and grain size, versus one value (181 uJy) for 2017 in the simple model | F: The radiative transfer approach is more versatile since it includes thermal emission and reflected sunlight | **supported**

## Reasoning

- Why this data: 1 mm chosen as upper grain size because the SED wavelength dependence is diagnostic below that radius  
  > "We choose 1 mm as the upper limit of the grain sizes, because below this radius the observed wavelength dependence of the ring’s SED can give indications on the possible constitution of the ring’s dust particles" (3. Comparison with Planetary Rings and Comets)
- Why this method: Simple ring models cannot treat grain properties, so radiative transfer was introduced  
  > "which enables a more detailed treatment of the dust grain properties of a ring" (Introduction)
- Alternative: Porosity and crystalline versus amorphous options were tested and found not to matter significantly at the relevant wavelengths, so ignored or set to amorphous  
  > "we did not find significant differences at wavelengths of past and possible future observational facilities" (5.1 Spectral Energy Distributions of the Ring Models)
- How they decided it was enough: _not stated_
- Limitation (authors): Models assume single-material, single-size grains and ignore porosity; a size distribution or mixture is left for future work  
  > "in this analysis we focus on identifying the potentially dominant component and particle radius for the Haumea ring" (3. Comparison with Planetary Rings and Comets); "Our analysis also provides a first step for further investigations on rings with a mixture of large boulders and small grains" (6. Summary and conclusions)
- Caveat (inferred, ours): No ALMA data are analysed; the Cycle 9 observations are only mentioned as ongoing, so the paper cannot be checked against measurements.
- Caveat (inferred, ours): The ring element approach assumes a homogeneous thin ring and ignores edge effects, with optical depth choices not fully listed.
- Caveat (inferred, ours): Grain density, optool material entries and wavelength grid are not given.

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Optical depth and ring parameters adopted in the RADMC-3D runs
- Missing: Exact optool material names and bulk densities
- Missing: RADMC-3D settings (photon packages, wavelength grid, image setup)
- Missing: Tabulated model SEDs or flux densities (only the V-band table is given)
- Data volume (inferred): none (no ALMA data processed)
- Score (inferred): 2/5, Public codes (RADMC-3D, optool) and a clear method outline, but ring optical depth, grain densities, material entries and code settings are not given, and no model output beyond a V-band table is published.
- Rediscovery candidate: no, The paper analyses no ALMA data, and the recipe lacks key parameters.

## Links

- Method: Lellouch et al. 2017 (cite: Lellouch2017) (Simple ring thermal model used for the baseline fluxes)
- Method: Dullemond et al. 2012 (cite: radmc) (RADMC-3D code)
- Method: Dominik et al. 2021 (cite: optool) (optool opacity code)
- Companion: Ortiz et al. 2017 (cite: Ortiz2017) (Discovery of the Haumea ring by stellar occultation and V-band constraints)
- Companion: Muller et al. 2019 (cite: Muller2019) (Thermal emission and Herschel limits of the Haumea system)
- Companion: Kalup & Kiss 2023 (cite: Kalup2023) (Earlier ALMA band 7 flux predictions with the simple model)
- Related: ALMA Cycle 9 project 2022.1.01753.S (Haumea band 7)

## Checks

```json
{
 "quotes": 65,
 "quotes_ok": 65,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 88,
  "stated": 46,
  "rate": 0.523
 },
 "evidence_ok": true
}
```
