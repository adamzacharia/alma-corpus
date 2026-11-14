# Observations of spiral and streamer on a candidate proto-brown dwarf

`2024MNRAS.529.3601R` | Monthly Notices of the Royal Astronomical Society 2024 | first author: Riaz, B. | arXiv: 2403.07367 | DOI: 10.1093/mnras/stae724

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: Do the earliest-stage brown dwarf candidate Ser-emb 16 and its surroundings show spirals and streamers like those around young stars, and what do they imply about accretion and magnetic fields?  
  > "We present the first observations of a large-scale spiral and a streamer towards a very young brown dwarf candidate in its early formation stages." (abstract)
- Target **Ser-emb 16**: coordinates RA 18h28m44.78s, Dec +00d51m25.79s (J2000)  
  > "RA (J2000) = 18h28m44.78s, Dec (J2000) = 00d51m25.79s" (Target and ALMA Observations); "It is located in the Serpens star-forming region \[$d$=440$\pm$9 pc; (Ortiz-Leon et al. 2017)\]." (Target and ALMA Observations); z/distance 440±9 pc  
  > "RA (J2000) = 18h28m44.78s, Dec (J2000) = 00d51m25.79s" (Target and ALMA Observations); "It is located in the Serpens star-forming region \[$d$=440$\pm$9 pc; (Ortiz-Leon et al. 2017)\]." (Target and ALMA Observations); distance from Ortiz-Leon et al. 2017  
  > "RA (J2000) = 18h28m44.78s, Dec (J2000) = 00d51m25.79s" (Target and ALMA Observations); "It is located in the Serpens star-forming region \[$d$=440$\pm$9 pc; (Ortiz-Leon et al. 2017)\]." (Target and ALMA Observations)

## Data provenance

- ALMA projects: 2021.1.00134.S
- bands: Band 6  
  > "We observed Ser-emb 16 with ALMA in the HCO$^{+}$ (3-2) line at 267.567 GHz in Band 6." (Target and ALMA Observations)
- frequencies and spectral setup: Line window bandwidth 117.18 MHz, resolution 244.14 kHz (smoothed ~0.3-0.4 km/s); continuum baseband 1875 MHz with 976 kHz channels  
  > "The bandwidth was set to 117.18 MHz, which provides a resolution of 244.14 kHz, or a smoothed resolution of $\sim$0.3-0.4 km s$^{-1}$ at 267.5 GHz." (Target and ALMA Observations)
- continuum bandwidth: 1875 MHz  
  > "One baseband was used for continuum observations where the spectral resolution was set to 976 kHz and the total bandwidth was 1875 MHz." (Target and ALMA Observations)
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.4 arcsec; beam 0.47"x0.38"  
  > "The synthetic beam size of the observations is 0.47$^{\prime\prime}\times$0.38$^{\prime\prime}$ or about 221$\times$179 au at the distance to Serpens." (Target and ALMA Observations)
- max recoverable scale: ~4 arcsec  
  > "Our chosen configuration was a maximum recoverable scale of $\sim$4 arcsec, and an angular resolution of $\sim$0.4 arcsec." (Target and ALMA Observations)
- sensitivity: 1-sigma rms ~0.15 mJy/beam continuum, ~10 mJy/beam HCO+, ~7 mJy/beam c-HCCCH  
  > "The 1-$\sigma$ rms is $\sim$0.15 mJy beam$^{-1}$ for the continuum image, $\sim$10 mJy beam$^{-1}$ in the HCO$^{+}$ line and $\sim$7 mJy beam$^{-1}$ in the c-HCCCH line." (Target and ALMA Observations)
- time on source: _not stated_
- observing dates: September 2022 (Cycle 8)  
  > "The observations were obtained in Cycle 8 (PID: 2021.1.00134.S) in September, 2022." (Target and ALMA Observations)
- pi or archival as stated: _not stated_
- Line: HCO+ 3-2 (267.567 GHz)
- Line: ortho c-HCCCH 5(2,3)-4(3,2) (not stated)
- Line: CO 2-1 (not stated)
- External data: Systemic velocity Vlsr = 8.0±0.2 km/s  
  > "V$_{lsr}$ = 8.0$\pm$0.2 km s$^{-1}$ (Riaz et al. 2019a)" (Data Analysis and interpretation) [from Riaz et al. 2019a]
- External data: Distance 440±9 pc  
  > "\[$d$=440$\pm$9 pc; (Ortiz-Leon et al. 2017)\]" (Target and ALMA Observations) [from Ortiz-Leon et al. 2017]
- Simulation/model as data: MHD simulations of Machida et al. 2020 adapted (misalignment 30 deg best), and SPH SEREN core-collision simulations, used as input to MOLLIE radiative transfer  
  > "We find a model with an initial misalignment angle of 30$^{\circ}$ best matches the observed structure in the moment 0 map" (Theoretical interpretations)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Calibrated data delivered by EU-ARC used  
  > "We employed the calibrated data delivered by the EU-ARC." (Target and ALMA Observations)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: uniform weighting  
  > "Data analysis was performed on the uniform-weighted synthesized images using the CASA software." (Target and ALMA Observations)
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
- final beam: 0.47"x0.38"  
  > "The synthetic beam size of the observations is 0.47$^{\prime\prime}\times$0.38$^{\prime\prime}$ or about 221$\times$179 au at the distance to Serpens." (Target and ALMA Observations)
- final rms: _not stated_

### Inherited from earlier work

- HCO+ column density, H2 gas mass and number density derived following earlier method  
  > "the HCO$^{+}$ column density, H$_{2}$ gas mass and H$_{2}$ number density were derived following the method described in Riaz et al. (2018)." (Data Analysis and interpretation) [from Riaz et al. (2018)]
- Dust continuum mass method  
  > "Following the method described in Riaz et al. (2019b), the dust continuum mass for Ser-emb 16 is 0.11$\pm$0.02 M$_{Jup}$" (Data Analysis and interpretation) [from Riaz et al. (2019b)]
- MHD simulation setup  
  > "The numerical settings used in the present paper are almost the same as in Machida et al. (2020)" (Twisted spiral model) [from Machida et al. (2020)]

### Not stated but needed to reproduce (our reading)

- CASA version and tclean parameters (cell, image size, masks, deconvolver)
- Continuum subtraction and line-free channels
- Imaging for CO and c-HCCCH, including rest frequency
- Column density equations, excitation temperature and abundance assumptions from Riaz et al. 2018
- Moment map thresholds and velocity ranges for the spiral and streamer
- Regions used for imfit of the clumps
- MOLLIE abundance and line-width grids; how the simulation was scaled to the observation

## Analysis recipe

1. **Make moment maps**: Moment 0, 8 and 9 maps over blue-shifted (<8.0 km/s) and red-shifted (>8.0 km/s) velocities  
  > "We create moment 0 (integrated value of the spectrum) and moment 8 (maximum value of the spectrum) maps separately over the blue-shifted ($<$8.0 km s$^{-1}$) and red-shifted ($>$8.0 km s$^{-1}$) velocities." (Data Analysis and interpretation)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure sizes and fluxes**: Fit elliptical Gaussians to continuum and HCO+ images  
  > "We have used the CASA tasks *uvmodelfit* and *imfit* to measure the source size, continuum and line fluxes by fitting one or more elliptical Gaussian components" (Data Analysis and interpretation)
   - software: CASA uvmodelfit, CASA imfit
   - fitting: elliptical Gaussians  
  > "by fitting one or more elliptical Gaussian components on the continuum and HCO$^{+}$ (3-2) line images" (Data Analysis and interpretation)
   - validation: _not stated_
3. **Derive masses and densities**: Dust mass from continuum; gas mass and density from HCO+ flux and size  
  > "assuming a dust temperature of 10 K, and dust opacity at 1.16 mm of 0.02582 cm$^{2}$ g$^{-1}$ for $\beta$ = 1.0 or for optically thin emission." (Data Analysis and interpretation)
   - assumption: Td = 10 K; kappa(1.16 mm)=0.02582 cm2/g; optically thin  
  > "assuming a dust temperature of 10 K, and dust opacity at 1.16 mm of 0.02582 cm$^{2}$ g$^{-1}$ for $\beta$ = 1.0 or for optically thin emission" (Data Analysis and interpretation)
   - fitting: _not stated_
   - validation: _not stated_
4. **Compare with models via radiative transfer**: MOLLIE non-LTE modelling of the simulations; reduced chi2 against the observed blue-shifted spiral spectrum  
  > "For each synthetic spectrum, a reduced-$\chi^{2}$ value is computed to determine the goodness of fit." (Radiative transfer modelling)
   - software: MOLLIE
   - fitting: Vary abundance profile and line width; lowest reduced chi2  
  > "A reasonable fit to the strength and width of the observed line profile is reached from varying the abundance profile and the line width." (Radiative transfer modelling)
   - validation: Model moment 0 maps compared with observed  
  > "From the best line model fit, we produced a moment 0 map to compare with the observed map." (Radiative transfer modelling)

## Software

- **CASA** : Imaging, moment maps and Gaussian fitting  
  > "Data analysis was performed on the uniform-weighted synthesized images using the CASA software." (Target and ALMA Observations)
- **MOLLIE** : 3D non-LTE line radiative transfer  
  > "is used as an input to the 3D non-LTE radiative transfer code MOLLIE (Keto et al. 2004)" (Radiative transfer modelling)
- **SEREN** : SPH core-collision simulations  
  > "We used the SPH code SEREN (Hubber et al. 2011) to simulate the collision of two cores" (Core collision model)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum flux of Ser-emb 16 | 3.22 | 0.63 | mJy | 2 | integrated continuum flux of 3.22$\pm$0.63 mJy |
| Projected continuum size | 588 | 97 | au | 2 | Projected  = 588$\pm$97 au |
| Dust mass | 0.11 | 0.02 | M_Jup | 3 | the dust continuum mass for Ser-emb 16 is 0.11$\pm$0.02 M$_{Jup}$ |
| H2 gas mass of Ser-emb 16 | 17.6 | 3.2 | M_Jup | 3 | 17.6$\pm$3.2 M$_{Jup}$ |
| Spiral gas mass | 0.094 | 0.01 | Msun | 3 | 0.094$\pm$0.01 M$_{\odot}$ |
| Streamer gas mass | 0.045 | 0.01 | Msun | 3 | 0.045$\pm$0.01 M$_{\odot}$ |
| HCO+ abundance in spiral from models | (0.8-2)e-8 | 20-30% | relative to H2 | 4 | The HCO$^{+}$ molecular abundance relative to H$_{2}$ derived from both models is (0.8-2)$\times$10$^{-8}$ for the spiral. |

## Qualitative findings

- No CO (2-1) outflow detected within 10 arcsec  
  > "There is no CO detection at a $>$2-$\sigma$ level within 10$^{\prime\prime}$ of Ser-emb 16." (Non-detection of a CO outflow)

## Claim tuples

- H: Ser-emb 16 is a proto-brown dwarf with spiral and streamer accretion structures | E: HCO+ (3-2) moment maps of ALMA Band 6 data | R: Blue-shifted spiral (~2000 au) and red-shifted streamer (~2900 au) around the source | F: Large-scale asymmetric accretion exists around a candidate proto-brown dwarf | **supported**
- H: The streamer triggers warm carbon-chain chemistry | E: c-HCCCH moment map compared with streamer | R: Emission peaks near the source, nowhere else along the structures | F: Streamer impact may produce warm carbon-chain emission | **partially**
- H: The origin of the spiral can be explained by simulations | E: Twisted pseudo-disk MHD model and core collision SPH model fed into MOLLIE | R: Both reproduce the curved structure and clumps | F: Both are viable; they imply opposite magnetic field strengths | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Streamer as outflow rejected given no CO outflow detection; attributed to infall viewed from a different orientation  
  > "However, there is no detection of a molecular outflow in the CO (2-1) line" (Data Analysis and interpretation)
- How they decided it was enough: _not stated_
- Limitation (authors): Velocity resolution inadequate to constrain kinematics  
  > "This makes it difficult to constrain the kinematics of these structures." (Data Analysis and interpretation)
- Caveat (inferred, ours): Only one HCO+ line, so no independent kinematic test
- Caveat (inferred, ours): Models are tuned by eye to fit and not unique
- Caveat (inferred, ours): Mass estimates depend on assumed excitation and abundances
- Caveat (inferred, ours): Lbol disagreement with Herschel-based values

## Reproducibility

- Data public (paper): Public after the proprietary period via the ALMA archive  
  > "This data will become publicly available at the end of the proprietary period. It can then be accessed through the ALMA archives." (Data Availability)
- Products in archive: _not stated_
- Missing: CASA version and imaging parameters
- Missing: Mass derivation details from Riaz et al. 2018
- Missing: Simulation outputs and MOLLIE setup
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Data are public and the main numbers are reproducible, but the imaging and mass derivation details are deferred to earlier papers.
- Rediscovery candidate: no, Imaging recipe incomplete and key methods are inherited from earlier papers.

## Links

- Method: Riaz et al. 2018 (Method for column density and mass)
- Method: Machida et al. 2020 (MHD simulations)
- Companion: Riaz & Thi 2022a (Classification of Ser-emb 16)

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
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 35,
  "rate": 0.515
 },
 "evidence_ok": true
}
```
