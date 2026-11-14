# Resolving the Polarized Dust Emission of the Disk around the Massive Star Powering the HH 80-81 Radio Jet

`2018ApJ...856L..27G` | The Astrophysical Journal Letters 2018 | first author: Girart, J. M. | arXiv: 1803.06165 | DOI: 10.3847/2041-8213/aab76b

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, protoplanetary_disks
- Question: Is the disk around the massive protostar GGD27 MM1 (HH 80-81 jet) resolved, and what produces its dust polarization (self-scattering, aligned grains)?  
  > "The observations clearly resolve the disk oriented perpendicular to the radio jet, with a radius of $\simeq0.171\ensuremath{''}$ ($\sim$291 au at 1.7 kpc distance)." (abstract)
- Target **GGD27 MM1**: coordinates _not stated_; z/distance 1.7 kpc  
  > "($\sim$291 au at 1.7 kpc distance)" (abstract); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00480.S
- bands: Band 6 (1.14 mm, 263.0 GHz)  
  > "We used the Band 6 receiver with the correlator set in continuum mode (time division mode, TDM)" (2 Observations)
- frequencies and spectral setup: TDM continuum, 253.0–257.0 and 269.0–273.0 GHz  
  > "covering the 253.0–257.0 GHz and 269.0–273.0 GHz frequency ranges" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: 37 antennas, C36-7  
  > "The observations were performed with 37 antennas in the C36-7 configuration" (2 Observations)
- baselines: 15 m to 6.3 km (13 to 5400 kλ)  
  > "which provided baselines between 15 m and 6.3 km (or 13 to 5400 k$\lambda$)" (2 Observations)
- angular resolution: 45.0 mas x 38.3 mas, PA -62.4 deg  
  > "The resulting synthesized beam has a full width at half maximum (FWHM) of 45.0 mas$\times$38.3 mas with a position angle of $-62.4^\circ$." (2 Observations)
- max recoverable scale: image fidelity affected above ~0.7 arcsec  
  > "the image fidelity is severely affected for scales larger than $\ensuremath{\gtrsim} 0.7\ensuremath{''}$" (2 Observations)
- sensitivity: Stokes I rms 19 uJy/beam; Q/U rms 16 uJy/beam  
  > "The Stokes I rms noise is 19 $\mu$Jy beam$^{-1}$." (2 Observations)
- time on source: _not stated_
- observing dates: December 3, 2015  
  > "were taken on December 3, 2015" (2 Observations)
- pi or archival as stated: _not stated_
- External data: 7 mm flux density used for the spectral index (2.2)  
  > "Previous 7 mm observations marginally resolved the dust emission associated with this disk" (3.1 Dust emission) [from (cite: Carrasco12)]
- External data: Gas kinetic temperature ~120 K from SO2  
  > "indicates that the average kinetic temperature of the traced molecular gas is $\sim120$ K (cite: FernandezG11)" (4.1) [from (cite: FernandezG11)]
- External data: Self-scattering polarization model predictions  
  > "matches well the prediction of self-scattering from an optically thick disk where dust settling (into the mid-plane) has not yet occurred (cite: Yang17)" (4.2) [from (cite: Yang17)]

## Processing

### Calibration

- pipeline or manual: Standard and polarization calibration by ALMA staff  
  > "The standard aperture synthesis calibration and the specific polarization calibration were performed by the ALMA staff (cite: Nagai2016)." (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ~10%  
  > "The ALMA flux accuracy in Band 6 is $\sim$10%" (2 Observations)
- self calibration: Iterative phase-only, Stokes I model, baselines >300 kλ, solutions applied to Q and U  
  > "iterative phase-only selfcalibration was performed using the Stokes I image as a model for the visibilities with baselines larger than 300 k$\lambda$." (2 Observations)

### Imaging

- task: CASA clean  
  > "all obtained with the CASA task *clean*" (2 Observations)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5  
  > "generated with a value of 0.5 for the robust Briggs weighting parameter" (2 Observations)
- uv taper: only baselines >300 kλ used  
  > "only using visibilities with baselines larger than 300 k$\lambda$" (2 Observations)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 45.0 x 38.3 mas, PA -62.4 deg  
  > "The resulting synthesized beam has a full width at half maximum (FWHM) of 45.0 mas$\times$38.3 mas" (2 Observations)
- final rms: I 19 uJy/beam; Q,U 16 uJy/beam  
  > "The rms noise level in the Stokes Q and U dust maps is $\sigma_{\rm pol}=$16  $\mu$Jy beam$^{-1}$." (2 Observations)

### Not stated but needed to reproduce (our reading)

- Cell size, image size, clean masks, iteration threshold
- Number of self-calibration iterations and solution intervals
- How the unresolved compact source was removed from visibilities (model, uv range)
- Fitting method, likelihood and priors for the two power-law disk model
- Source coordinates and phase center
- CASA version
- Polarization debiasing details beyond the formula, and uv range for compact-source detection

## Analysis recipe

1. **Self-calibrate and image Stokes I, Q, U**: Phase-only self-cal with Stokes I model, applied to Q, U; clean with robust 0.5, baselines >300 kλ  
  > "The selfcalibration solutions were transfer to the Stokes Q and U visibilities." (2 Observations)
   - software: CASA
   - parameter: robust 0.5, uv > 300 kλ  
  > "generated with a value of 0.5 for the robust Briggs weighting parameter" (2 Observations)
   - fitting: _not stated_
   - validation: Noise improved by a factor of ~2 for Stokes I  
  > "The selfcalibration allowed to improve the rms noise in Stokes map (by a factor of $\sim$2 for the Stokes I)." (2 Observations)
2. **Remove unresolved compact source**: Compact source seen at >4000 kλ removed from visibilities; maps redone with same parameters  
  > "the compact source was removed from the visibilities and the maps were redone with the same parameters" (3.1)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit disk intensity profile**: Two power-law model (inner/outer) convolved with the beam; free Rinn, Rturn, Rdisk, PA, i  
  > "we assumed that the disk intensity can be modeled with two different power laws ($I_{\nu} \propto r^{-q}$)" (3.1)
   - fitting: best fit; sampler not stated  
  > "The best fit was obtained for a disk with a radius of 171$\pm$6 mas (291$\pm$10 au), $PA=112.9$$\pm$1.0$^\circ$, $i=48.8$$\pm$0.5$^\circ$" (Results, Dust emission)
   - validation: A simple power law fit is significantly worse  
  > "A fit using a simple power law generates a significantly worse solution." (3.1 footnote)
4. **Polarization maps and angle statistics**: P = sqrt(Q^2+U^2-sigma^2), PA=0.5 arctan(U/Q), 3-sigma cutoff; compare PAs with azimuthal tangent in outer disk  
  > "The polarization position angles ($PA_{\rm pol} = 0.5 \arctan{\rm (U/Q)}$) were obtained using a cutoff of 3-$\sigma$" (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
5. **Estimate maximum grain size**: Compare mean inner-disk polarization fraction with Figure 3 of Kataoka et al. 2016  
  > "From Figure 3 of (cite: Kataoka2016) and taking into account the average polarization fraction in GGD27 MM1, we estimate that the maximum grain size should be in the 50 and 500 $\mu$m range." (4.2)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Imaging (clean) and self-calibration  
  > "all obtained with the CASA task *clean*" (2 Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Disk radius | 171 mas (291 au) | ±6 mas (±10 au) | mas | 3 | a disk with a radius of 171$\pm$6 mas (291$\pm$10 au) |
| Disk inclination | 48.8 | ±0.5 | deg | 3 | $i=48.8$$\pm$0.5$^\circ$ |
| Total 1.14 mm flux density | 350 | ±1 | mJy | 3 | a total 1.14 mm flux density of 350$\pm$1 mJy |
| Power-law indices q_out / q_inn | 4.5 / 0.7 | ±0.1 each | dimensionless | 3 | q_{\rm out}$=4.5$\pm$0.1) to a relative flat index in the inner disk ($q_{\rm inn}$=0.7$\pm$0.1) |
| Mean polarization fraction, inner disk | 0.56 | std 0.33% | % | 4 | the polarization degree has a mean value of 0.56% and a standard deviation of 0.33% |
| Mean polarization fraction, outer disk | 4.0 | std 2.3% | % | 4 | with an average value of 4.0% and standard deviation of 2.3% |
| Maximum grain size | 50–500 | not stated | micron | 5 | the maximum grain size should be in the 50 and 500 $\mu$m range |

## Qualitative findings

- Inner disk (R<~170 au) is optically thick and its polarization is consistent with self-scattering without dust settling; outer disk has an azimuthal pattern with higher polarization.  
  > "The polarization characteristics of the inner disk suggest that dust settling has not occurred yet" (abstract)

## Claim tuples

- H: The inner disk is optically thick | E: Brightness temperature, intensity profile and polarization transition | R: Tb ~400 K peak, drops below 10 K outside; Rturn at Tb ~120 K | F: Disk optically thick inside ~170 au | **supported**
- H: Inner disk polarization arises from self-scattering | E: Compare polarization pattern with Yang et al. 2017 model | R: Offset along the minor axis, bifurcation of angles; NE side deviates | F: Broadly consistent with self-scattering, no settling, grains 50–500 μm | **partially**
- H: Outer disk polarization is explained by existing scattering models | E: Azimuthal pattern and polarization fraction analysis | R: Mean angle difference 11 deg; fractions 5–7% exceed predictions | F: Broadly consistent with scattering of radially beamed radiation; aligned non-spherical grains not excluded | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Single power law fit rejected as significantly worse  
  > "A fit using a simple power law generates a significantly worse solution." (3.1 footnote)
- How they decided it was enough: _not stated_
- Limitation (authors): Image fidelity is poor for scales larger than 0.7 arcsec because of lack of visibilities at 150–300 kλ  
  > "That means that the image fidelity is severely affected for scales larger than $\ensuremath{\gtrsim} 0.7\ensuremath{''}$." (2 Observations)
- Caveat (inferred, ours): Grain size estimate is read off a published figure for low-mass disks, with no dedicated modeling
- Caveat (inferred, ours): Removal of the compact source may bias inner disk polarization
- Caveat (inferred, ours): Excluding baselines <300 kλ discards extended emission
- Caveat (inferred, ours): Optical depth is inferred using an assumed 120 K gas temperature

## Reproducibility

- Data public (paper): Project code given in the acknowledgments; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00480.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging cell and image size, masks
- Missing: Compact source removal procedure
- Missing: Disk model fitting code and priors
- Missing: Self-calibration parameters
- Data volume (inferred): ~50-100 GB raw (single-track Band 6 C36-7 polarization data)
- Score (inferred): 3/5, Single dataset with key imaging parameters given (robust, uv cut, beam), but self-calibration, compact-source removal and model fitting are underspecified.
- Rediscovery candidate: no, Recipe is incomplete (source removal and fitting details) even though results are numeric.

## Links

- Method: (cite: Nagai2016) (ALMA polarization calibration)
- Method: (cite: Kataoka2016) (Grain size from polarization fraction)
- Method: (cite: Yang17) (Self-scattering model predictions)
- Companion: (cite: Girart17) (Earlier observations of the GGD27 MM1 disk)
- Companion: Añez et al., in preparation (Analysis of the compact ionized source)

## Checks

```json
{
 "quotes": 47,
 "quotes_ok": 47,
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
  "facts": 66,
  "stated": 35,
  "rate": 0.53
 },
 "evidence_ok": true
}
```
