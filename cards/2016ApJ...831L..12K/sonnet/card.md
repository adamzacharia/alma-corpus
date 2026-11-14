# Submillimeter Polarization Observation of the Protoplanetary Disk around HD 142527

`2016ApJ...831L..12K` | The Astrophysical Journal Letters 2016 | first author: Kataoka, Akimasa | arXiv: 1610.06318 | DOI: 10.3847/2041-8205/831/2/L12

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: Is the submillimeter polarization of the HD 142527 disk produced by grain alignment with magnetic fields or by dust self-scattering, and what does it imply for grain size?  
  > "In this section, we qualitatively discuss which mechanism is more likely to take place in the disk around HD 142527." (Discussions)
- Target **HD 142527**: coordinates _not stated_; z/distance not stated (beam 0.51x0.44 arcsec corresponds to ~71x62 au)  
  > "we set the inclination of the disk to be $27^\circ$ (cite: Fukagawa13) and the position angle to be $71^\circ$." (Discussions); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00425.S
- bands: 343 GHz (0.87 mm)  
  > "at the frequency of 343 GHz" (abstract)
- frequencies and spectral setup: four spectral windows at 336.5, 338.4, 348.5, 350.5 GHz, 1.875 GHz bandwidth each  
  > "The correlator processed four spectral windows centered at $336.5, 338.4, 348.5,$ and $350.5$ GHz with a bandwidth of 1.875 GHz each." (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C36-2/3, 38 antennas  
  > "The antenna configuration was C36-2/3 and 38 antennas were operated during the observation period." (Observations)
- baselines: _not stated_
- angular resolution: 0.51" x 0.44" (~71 x 62 au)  
  > "The beam size is $0.51\ensuremath{''} \times 0.44\ensuremath{''}$" (abstract)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2016 March 11, Cycle 3  
  > "HD142527 was observed by Atacama Large Millimeter / submillimeter Array (ALMA) on 2016 March 11, during its Cycle 3 operation." (Observations)
- pi or archival as stated: _not stated_
- External data: Dust density distribution for the RADMC-3D model based on previous continuum modeling at 0.87 mm  
  > "The density distribution is based on a previous modeling of the continuum at the same wavelength (cite: Muto15)." (Discussions) [from (cite: Muto15)]
- External data: Disk inclination of 27 deg  
  > "we set the inclination of the disk to be $27^\circ$ (cite: Fukagawa13)" (Discussions) [from (cite: Fukagawa13)]
- Simulation/model as data: RADMC-3D self-scattering model: power-law size distribution -3.5, amax 150 um, Gaussian lopsided ring, dust temperature 36 K  
  > "The dust temperature is set to 36 K." (Discussions)

## Processing

### Calibration

- pipeline or manual: Raw data reduced by EA-ARC staff; details in Nagai16  
  > "The raw data were reduced by EA-ARC staff. A detailed description of the data reduction is given in (cite: Nagai16)." (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: bandpass J1427-4206, gain J1604-4441, polarization J1512-0905  
  > "The bandpass and the complex gain were calibrated by observations of J1427-4206 and J1604-4441, respectively, and the polarization calibration was performed by observations of J1512-0905." (Observations)
- flux scale uncertainty: _not stated_
- self calibration: self-calibration applied with CASA imaging  
  > "We further perform the iterative CLEAN deconvolution imaging by using CASA with self-calibration to improve the image quality." (Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "We employ the Briggs weighting with a robust parameter of $0.5$" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: 0, 0.3, 0.9 arcsec  
  > "the multiscale option with scale parameters of 0, 0.3, and 0.9 arcsec" (Observations)
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.51" x 0.44"  
  > "The beam size of the final product is $0 \ensuremath{''}.51 \times 0 \ensuremath{''}.44$" (Observations)
- final rms: Stokes I 185, Q 29.1, U 29.5, V 25.2 uJy/beam  
  > "Stokes $Q$ | ... | 1.99, -5.13 | 29.1" (Table 1)

### Inherited from earlier work

- Data reduction (calibration) details  
  > "A detailed description of the data reduction is given in (cite: Nagai16)." (Observations) [from (cite: Nagai16)]
- Self-scattering polarization predictions/grain size range  
  > "The available size range to explain the observations is roughly $\sim 40-300 {\rm~\mu m}$ if we assume the compact spherical grains (cite: Kataoka15)." (Indication on Dust Coagulation and Dynamics) [from (cite: Kataoka15)]

### Not stated but needed to reproduce (our reading)

- CASA version
- number of self-calibration rounds and solution intervals
- clean mask, threshold and image size/cell size
- how Stokes Q/U/V imaging and polarization leakage calibration were done (deferred to Nagai16)
- distance to HD 142527
- opacity table and RADMC-3D settings (photon number, grid, stellar parameters)
- polarization debiasing method

## Analysis recipe

1. **Image Stokes I,Q,U,V**: Iterative CLEAN with self-calibration, multiscale, Briggs weighting  
  > "We further perform the iterative CLEAN deconvolution imaging by using CASA with self-calibration to improve the image quality." (Observations)
   - software: CASA
   - parameter: robust 0.5; scales 0, 0.3, 0.9 arcsec  
  > "multiscale option with scale parameters of 0, 0.3, and 0.9 arcsec" (Observations)
   - fitting: _not stated_
   - validation: Stokes V rms close to thermal noise  
  > "The rms for the Stokes $V$ image is 25.2 $\mu$Jy, close to the thermal noise level of the integration time." (Observations)
2. **Derive polarized intensity and fraction**: PI from integrated Q and U; polarization fraction = PI/I; restrict to >3 sigma_PI  
  > "The discussion in this Letter is concerning at the regions where the detection is larger than 3 $\sigma_{\rm PI}$" (Results)
   - fitting: _not stated_
   - validation: positive polarization bias argued not to affect >3 sigma regions  
  > "thus the positive polarization bias does not affect the results" (Results)
3. **Model self-scattering polarization**: RADMC-3D radiative transfer of lopsided ring with amax 150 um, compared qualitatively with observations  
  > "We model the intensity with a simple model and perform radiative transfer calculations with RADMC-3D" (Discussions)
   - software: RADMC-3D
   - parameter: Sigma0max 0.6, Sigma0min 0.008 g cm^-2; rc 170 au; rw 27 au; theta_d 30 deg; phi_d 60 deg; T 36 K; inclination 27 deg; PA 71 deg  
  > "$r_c = 170$ au, and $r_w=27$ au." (Discussions)
   - assumption: compact spherical grains, size slope -3.5  
  > "power-law size distribution with a power of $-3.5$ and the maximum grain size $150 {\rm~\mu m}$" (Discussions)
   - fitting: no fitting; not aimed at perfect model  
  > "Here, we do not aim to model the intensity and the polarization perfectly" (Discussions)
   - validation: qualitative comparison of vector flip and PI/continuum peak offset  
  > "The flip of the polarization vectors of the observations is naturally explained with the self-scattering model." (Comparison with the Observation)

## Software

- **CASA** : CLEAN imaging with self-calibration  
  > "iterative CLEAN deconvolution imaging by using CASA with self-calibration" (Observations)
- **RADMC-3D** : radiative transfer self-scattering model  
  > "perform radiative transfer calculations with RADMC-3D" (Discussions)
- **Astropy** : data analysis software  
  > "This work makes use of the Astropy (cite: AstropyCollaboration13) and Matplotlib (cite: Hunter07) software packages." (Acknowledgments)
- **Matplotlib** : plotting  
  > "This work makes use of the Astropy (cite: AstropyCollaboration13) and Matplotlib (cite: Hunter07) software packages." (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Polarization fraction at PI peak | 3.26 | 0.02 | % | 2 | The polarization fraction is $3.26 \pm0.02$ % at the peak of the polarized intensity |
| Polarization fraction at continuum peak | 0.220 | 0.010 | % | 2 | as low as $0.220 \pm 0.010$ % at the peak of the continuum |
| Peak polarization fraction (southwest) | 13.9 | 0.6 | % | 2 | a fraction of $13.9 \pm 0.6$ % |
| Total polarized intensity | 1.75 | not stated | mJy | 2 | to be $1.75$ mJy with an rms of $\sigma_{\rm PI}=42.8 {\rm~\mu Jy~beam^{-1}}$ |
| Total polarization fraction | 0.207 | not stated | % | 2 | we derive the total polarization fraction to be $0.207$ % |
| Maximum grain size | ~150 | range ~40-300 um | um | 3 | this puts a constraint on the maximum grain size to be approximately 150 ${\rm \mu m}$ |

## Qualitative findings

- Polarization vectors are radial on the main ring and azimuthal in two outer regions (NE, NW), a 90 deg flip  
  > "the polarization vectors are rotated by $90^\circ$ in two regions." (Results)

## Claim tuples

- H: Is the polarization from self-scattering rather than magnetic grain alignment? | E: Compared observed vector morphology with RADMC-3D self-scattering model and alignment expectations | R: Vector flip and PI/continuum peak offset are reproduced by self-scattering; alignment cannot rotate field by 90 deg | F: Self-scattering plays a major role | **supported**
- H: Can a simple self-scattering model explain all polarization features? | E: Compared model PI distribution and fractions with observed | R: Model misses PI peak at PA ~90 deg and the 13.9% fraction | F: Simple model is insufficient quantitatively | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Grain alignment with toroidal/poloidal magnetic fields rejected at least for outer regions  
  > "Therefore, at least at that position, the mechanism should be different from the grain alignment." (Grain alignment)
- How they decided it was enough: _not stated_
- Limitation (authors): High southwest polarization fraction may be due to interferometric filtering  
  > "could be due to interferometric filtering effects, where the Stokes $I$ and the Stokes $Q$, $U$ maps are resolved out differently." (Grain alignment)
- Caveat (inferred, ours): Self-scattering model is not fitted; single parameter set
- Caveat (inferred, ours): Grain size constraint assumes compact spherical grains
- Caveat (inferred, ours): Interferometric filtering not quantified

## Reproducibility

- Data public (paper): ALMA project data cited, public status not stated  
  > "This Letter makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00425.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version and self-cal details
- Missing: calibration details only in Nagai16
- Missing: RADMC-3D opacity and setup
- Data volume (inferred): ~50-100 GB
- Score (inferred): 3/5, Observation and imaging parameters are partly given, but calibration is deferred, self-cal and model setup details are missing.
- Rediscovery candidate: no, Calibration and self-cal details are incomplete and the model comparison is qualitative.

## Links

- Method: (cite: Nagai16) (Data reduction description)
- Method: (cite: Kataoka15) (Self-scattering polarization theory)

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
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 67,
  "stated": 37,
  "rate": 0.552
 },
 "evidence_ok": true
}
```
