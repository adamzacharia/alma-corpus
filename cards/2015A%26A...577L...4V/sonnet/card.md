# Resolving the stellar activity of the Mira AB binary with ALMA

`2015A&A...577L...4V` | Astronomy and Astrophysics 2015 | first author: Vlemmings, W. H. T. | arXiv: 1503.07647 | DOI: 10.1051/0004-6361/201526186

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars, stellar_physics
- Question: What are the size, shape, flux densities and spectral indices of Mira A and Mira B at mm wavelengths, and what do they imply about the extended atmosphere, stellar activity and the wind around Mira B?  
  > "We present the size, shape and flux densities at millimeter continuum wavelengths, based on ALMA science verification observations" (abstract)
- Target **Mira AB (Mira A, Mira B)**: coordinates _not stated_; z/distance 92 pc  
  > "Mira is the closest symbiotic binary star (at 92 pc, (cite: vanLeeuwen07))" (Introduction); distance from van Leeuwen 2007  
  > "Mira is the closest symbiotic binary star (at 92 pc, (cite: vanLeeuwen07))" (Introduction)

## Data provenance

- ALMA projects: 2011.0.00014.SV
- bands: Band 3 (~94.6 GHz) and Band 6 (~228.7 GHz)  
  > "Band 3 ($\sim94.6$ GHz) and Band 6 ($\sim228.7$ GHz)" (abstract)
- frequencies and spectral setup: Band 3: three 2 GHz continuum SPWs (128 channels) at 89.176, 91.234, 99.192 GHz; Band 6: one 2 GHz SPW centered at 228.558 GHz  
  > "In Band 3, three continuum spectral windows were observed with 128 channels over 2 GHz bandwidth centered on 89.176 GHz, 91.234 GHz and 99.192 GHz." (Observations and analysis)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Band 3: 72x64 mas and 68x57 mas; Band 6: 34x24 mas  
  > "This resulted in a beam of $72\times64$ mas and a position angle of $78.8^\circ$ on October 17" (Observations and analysis)
- max recoverable scale: _not stated_
- sensitivity: rms ~40 uJy/beam (Band 3), ~130 uJy/beam (Band 6)  
  > "The rms sensitivity was $\sim40~\mu$Jy beam$^{-1}$ in both epochs of the Band 3 and $\sim130~\mu$Jy beam$^{-1}$ in both epochs of the Band 6 observations." (Observations and analysis)
- time on source: _not stated_
- observing dates: 17 and 25 Oct 2014 (Band 3); 29 Oct and 1 Nov 2014 (Band 6)  
  > "Mira was observed on 17 and 25 October 2014 (Band 3) and 29 October and 1 November 2014 (Band 6)." (Observations and analysis)
- pi or archival as stated: _not stated_
- External data: Flux density at 345 GHz and CO/continuum Cycle 1 ALMA data of Mira  
  > "the flux density at 345 GHz (cite: ramsetal14) are presented in Fig. [3](#fig:sed)" (Discussion) [from (cite: ramsetal14)]
- External data: VLA flux densities and 43 GHz measurements used in SED  
  > "The VLA values, the ALMA values from this work and the flux density at 345 GHz (cite: ramsetal14) are presented in Fig. [3](#fig:sed)." (Discussion) [from (cite: mattkaro06); (cite: reidment07)]
- External data: Calibrator flux densities and spectral indices from the ALMA calibrator catalog  
  > "we present the calibrators, and their adopted flux densities and spectral indices from the ALMA calibrator catalog." (Flux density calibrators) [from ALMA calibrator catalog]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: ALMA observatory data products used, but epochs treated separately  
  > "We used the data products provided by the ALMA observatory except that the two epochs for each observing band were treated separately" (Observations and analysis)
- flux calibrator: Quasars J0334-4008, J2258-2758, J0238+1636 depending on epoch  
  > "| 25 Oct 2014 | J2258-2758 |      86.23      |     1.21     |     -0.73      |" (Flux density calibrators)
- flux scale uncertainty: ~5% absolute in both bands  
  > "we conservatively estimate an *absolute* flux density calibration uncertainty of $\sim5\%$ in both observing bands." (Observations and analysis)
- self calibration: Self-calibration on continuum SPWs averaged from 128 to 8 channels  
  > "Self-calibration was performed on the continuum spectral windows that were averaged from 128 to 8 channels across the 2 GHz bandwidth." (Observations and analysis)

### Imaging

- task: CASA clean  
  > "images were also created using the CASA task *clean* with Briggs $0.5$ weighing of the visibilities." (Observations and analysis)
- deconvolver: Band 3: multi-frequency synthesis with two Taylor coefficients  
  > "were made using a the multi-frequency synthesis option in *clean* with two Taylor coefficients to model the frequency dependence." (Observations and analysis)
- weighting robust: Briggs 0.5  
  > "images were also created using the CASA task *clean* with Briggs $0.5$ weighing of the visibilities." (Observations and analysis)
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

- Data products and observations from the ALMA long-baseline science verification campaign  
  > "taken as part of the ALMA long-baseline science verification campaign (ALMA partnership, 2015)" (Introduction) [from ALMA partnership, Fomalont et al. 2015 (cite: alma15)]
- uv-fitting method  
  > "To analyze the $uv$-data directly, we used the UVMULTIFIT code (cite: Marti14)." (Observations and analysis) [from (cite: Marti14)]

### Not stated but needed to reproduce (our reading)

- CASA version
- Image size and cell size
- Initial models/starting parameters for UVMULTIFIT fits and fit-selection criteria
- Details of self-calibration (solints, reference antennas, number of iterations)
- How brightness temperatures were computed (uniform disc assumptions, exact formula)
- How spectral indices and uncertainties were derived in uv-fits
- Baseline range / configuration details

## Analysis recipe

1. **Self-calibrate continuum data and image**: Self-calibration on averaged continuum SPWs; images made with clean, Briggs 0.5, MFS with 2 Taylor terms in Band 3  
  > "Self-calibration was performed on the continuum spectral windows that were averaged from 128 to 8 channels across the 2 GHz bandwidth." (Observations and analysis)
   - software: CASA
   - parameter: Briggs 0.5  
  > "with Briggs $0.5$ weighing of the visibilities." (Observations and analysis)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit source size and shape in uv-plane**: uv-fitting of delta function, elliptical/circular Gaussian and disc models for Mira A and B per epoch  
  > "For both sources we attempted fits to unresolved delta functions, elliptical and circular Gaussians and elliptical and circular discs." (Results)
   - software: UVMULTIFIT
   - fitting: _not stated_
   - validation: Residual image after subtracting disc; Band 3 25 Oct epoch excluded due to resolved calibrator  
  > "We find that the observations of October 25 in Band 3 are likely affected by a marginally resolved quasar flux calibrator" (Observations and analysis)
3. **Derive spectral indices and brightness temperatures**: Spectral index within Band 3 from MFS/uv-fits and between bands from flux densities; Tb for uniform disc  
  > "For a uniform disc we find $T_b\sim5300$ K at Band 3 ($\sim1.3$ R$_*$) and $T_b\sim2500$ K at Band 6" (Discussion)
   - assumption: Distance 92 pc  
  > "corresponds to $43.4$ AU at a distance of $92$ pc." (Relative astrometry)
   - fitting: _not stated_
   - validation: _not stated_
4. **Compare with radio photosphere and wind models**: Compare SED/spectral index and Tb with Reid & Menten model and expected Mira B wind emission  
  > "Both spectral indexes are not quite in agreement with the model prediction by (cite: reidment97)" (Discussion)
   - assumption: Ionized cavity gas temperature T=10^4 K  
  > "assuming a gas temperatures of $T=10^4\,$K" (Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : clean imaging  
  > "images were also created using the CASA task *clean*" (Observations and analysis)
- **UVMULTIFIT** : direct uv-plane model fitting  
  > "we used the UVMULTIFIT code (cite: Marti14)." (Observations and analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mira A spectral index within Band 3 | 1.71 | 0.05 | dimensionless | 3 | from 1.71$\pm$0.05 within Band 3 to $1.54\pm0.04$ between Band 3 and 6 |
| Mira A spectral index Band 3 to 6 | 1.54 | 0.04 | dimensionless | 3 | from 1.71$\pm$0.05 within Band 3 to $1.54\pm0.04$ between Band 3 and 6 |
| Mira B spectral index in Band 3 | 1.3 | 0.2 | dimensionless | 3 | The spectral index of Mira B is 1.3$\pm$0.2 in Band 3 |
| Mira B spectral index Band 3 to 6 | 1.72 | 0.11 | dimensionless | 3 | it rises to $1.72\pm0.11$ between the bands |
| Mira A Band 3 brightness temperature | ~5300 | not stated | K | 3 | (with brightness temperature $T_b\sim5300$ K) |
| Mira A Band 6 brightness temperature | ~2500 | not stated | K | 3 | $\sim4.0\times3.6$ AU in Band 6 ($T_b\sim2500$ K) |
| Mira A hotspot brightness temperature | ~10000 | not stated | K | 3 | With a size of $\sim4.7$ mas, we find $T_b\sim10000$ K |
| Mira B FWHM size | ~26 mas (~2.4 AU) | not stated | mas | 2 | with a full-width half-maximum (fwhm) of $\approx26$ mas, which corresponds to $\sim2.4$ AU. |
| Mira A Band 3 disc major axis (17 Oct) | 41.8 | 0.4 | mas | 2 | Oct 2014 & 94.2 & Disc & 35.03$\pm$0.04 & 41.8$\pm$0.4 & 1.20$\pm$0.01 & 54$\pm$2 & 1.73$\pm$0.09 |
| Mira A Band 6 hotspot flux density (29 Oct) | 10.13 | 0.07 | mJy | 2 | & 228.67 & Gaussian & 10.13$\pm$0.07 & 4.6$\pm$0.5 & 1.0 & …& … |
| Mira AB average separation | 0.472 | not stated | arcsec | 2 | The average separation of 0.472$''$ corresponds to $43.4$ AU at a distance of $92$ pc. |

## Qualitative findings

- Mira A disc is elongated and larger at Band 6 than Band 3, implying opacity changes and possible non-radial pulsations  
  > "The elongation and wavelength dependent size of Mira A point to strong changes of opacity source throughout the extended envelope and possible non-radial pulsations." (Conclusions)

## Claim tuples

- H: Is the Mira B emission from an ionized cavity or from Mira B's wind? | E: uv-fit sizes and spectral index of Mira B compared with ionized cavity and wind expectations | R: Size ~2.4 AU, alpha=1.3±0.2 with no turnover to 89 GHz | F: Emission from partially ionized gravitationally bound material from Mira A's wind, density at least an order of magnitude higher than the wind | **supported**
- H: Does Mira A's atmosphere match radio photosphere model predictions? | E: Measured spectral indices and Tb compared to Reid & Menten model | R: Tb at 3 mm ~5300 K, alpha shallower between bands | F: Tb in Band 3 significantly higher than predicted, possibly shock heating | **supported**
- H: Is there a hotspot on Mira A's disc? | E: Residual analysis and added Gaussian component in Band 6 uv-fits | R: Compact component ~10 mJy, ~4.7 mas, Tb ~10000 K | F: Hotspot likely due to magnetic activity, possibly related to X-ray outburst | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Analysis done on uv-data to avoid deconvolution artifacts  
  > "Most of the data analysis was performed directly on the $uv$-data in order to avoid image deconvolution artifacts" (Observations and analysis)
- Alternative: Mira B wind contribution ruled out as too faint by 4 orders of magnitude  
  > "We therefore rule out any significant contribution from Mira B’s wind at ALMA frequencies." (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Band 3 resolution too poor to confirm the hotspot there; 25 Oct Band 3 epoch affected by resolved calibrator  
  > "the worse angular resolution did not allow us to confidently distinguish between a fit of a stellar disc plus compact component or a stellar disc alone." (Discussion)
- Caveat (inferred, ours): Hotspot interpretation depends on model choice (Gaussian vs cluster of points) and single-band detection
- Caveat (inferred, ours): Self-calibration on the strong source could bias small-scale structure
- Caveat (inferred, ours): Absolute calibration depends on variable quasars; Band 6 epoch uses a different calibrator spectral index
- Caveat (inferred, ours): Uniform-disc Tb assumptions not detailed

## Reproducibility

- Data public (paper): ALMA science verification data, acknowledged by project code  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00014.SV" (Acknowledgements)
- Products in archive: _not stated_
- Missing: CASA version
- Missing: UVMULTIFIT starting parameters and fit setup
- Missing: self-cal parameters
- Missing: image size/cell size
- Data volume (inferred): tens of GB (long-baseline SV continuum, 4 epochs)
- Score (inferred): 3/5, Public data and a clear modelling approach with tabulated results, but many processing and fitting details are missing.
- Rediscovery candidate: yes, Data are public, uv-fitting with UVMULTIFIT is straightforward, and results are numeric in Table 1.

## Links

- Method: Martí-Vidal et al. 2014 (cite: Marti14) (UVMULTIFIT uv-plane fitting)
- Companion: Ramstedt et al. 2014 (cite: ramsetal14) (Earlier ALMA Cycle 1 Band 7 observations of Mira)
- Companion: ALMA partnership, Fomalont et al. 2015 (cite: alma15) (Long-baseline science verification campaign)
- Related: ALMA long-baseline science verification campaign

## Checks

```json
{
 "quotes": 51,
 "quotes_ok": 51,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 35,
  "rate": 0.515
 },
 "evidence_ok": true
}
```
