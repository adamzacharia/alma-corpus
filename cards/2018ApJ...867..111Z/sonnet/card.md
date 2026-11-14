# Spatially Resolved <SUP>12</SUP>CO(2-1)/<SUP>12</SUP>CO(1-0) in the Starburst Galaxy NGC 253: Assessing Optical Depth to Constrain the Molecular Mass Outflow Rate

`2018ApJ...867..111Z` | The Astrophysical Journal 2018 | first author: Zschaechner, Laura K. | arXiv: 1809.01160 | DOI: 10.3847/1538-4357/aadf32

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies
- Question: Is the CO emission in the NGC 253 molecular outflow optically thick, as probed by the CO(2-1)/CO(1-0) brightness temperature ratio r21, and what does this imply for the molecular mass outflow rate?  
  > "to determine whether or not the CO emission observed in the outflow of NGC 253 is optically-thick" (Introduction)
- Target **NGC 253**: coordinates _not stated_; z/distance 3.5 Mpc; systemic velocity 243 km/s  
  > "At a distance of 3.5 Mpc (cite: 2005MNRAS.361..330R), with a systemic velocity of 243 km s$^{-1}$, NGC 253 is the nearest nuclear starburst galaxy in the Southern sky" (Introduction); distance from Rekola et al. 2005  
  > "At a distance of 3.5 Mpc (cite: 2005MNRAS.361..330R), with a systemic velocity of 243 km s$^{-1}$, NGC 253 is the nearest nuclear starburst galaxy in the Southern sky" (Introduction)

## Data provenance

- ALMA projects: 2011.1.00172.S, 2012.1.00108.S, 2013.1.00191.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12m, ACA, TP (plus Mopra for CO(1-0) short spacings)  
  > "include a 14-pointing mosaic with the 12-meter array using Nyquist sampling, ACA, and Total Power (TP) data" (2 Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: original CO(2-1) 1.7''x1.0'', smoothed 1.9''x1.4''  
  > "The synthesized beam size of the original CO(2–1) cube is 1.7$''$$\times$1.0$''$ with PA=80.9$^{\circ}$" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: 2.0 mJy/beam per 5 km/s channel (original); 2.2 mJy/beam smoothed  
  > "the rms noise is 2.0 mJy beam$^{-1}$ over a 5 km s$^{-1}$ channel" (2 Observations)
- time on source: CO(2-1): ACA 0.5 hr, 12m 0.35 hr, TP 6.75 hr  
  > "Total Integration Time – 12m Array | 0.35 hrs" (Table 1)
- observing dates: CO(2-1): ACA 2014 Jun 28; 12m 2014 Dec 28; TP 2015 May-Aug  
  > "Observation Dates$-$12m Array | 2014 Dec 28" (Table 1)
- pi or archival as stated: _not stated_
- Other facility **Mopra**: short-spacing data for CO(1-0)  
  > "combined with Mopra observations to account for the short-spacings (PI: J. Ott)" (2 Observations)
- External data: CO(1-0) cube and its calibration  
  > "We use the same cube in this analysis and thus refer the reader to that paper for a full description" (2 Observations) [from (cite: 2015ApJ...801...25L)]
- External data: Single-dish CO fluxes for flux-recovery comparison  
  > "compare the integrated fluxes with those provided in (cite: 1999MNRAS.303..157H) over the same region" (3.4 Flux Recovery) [from (cite: 1999MNRAS.303..157H); (cite: 1996A&A...305..421M)]
- External data: Optically thin outflow mass 6.6e6 Msun, 9 Msun/yr, alpha_CO=0.34  
  > "to compute lower limits to the molecular mass and the mass loss rate due to the outflow in NGC 253 of $6.6\times10^6$ M$_\odot$ and 9 M$_\odot$ yr$^{-1}$ respectively" (4.2) [from (cite: 2013Natur.499..450B)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline for 12m; staff scripts for ACA  
  > "Initial calibration used scripts provided by ALMA staff for the ACA data and the ALMA pipeline for the 12-meter data." (2 Observations)
- casa version: CASA 4.2.2 (pipeline, initial imaging); 4.7.2 (feathering)  
  > "CASA version 4.2.2 was used for the pipeline and initial imaging." (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Uranus  
  > "Calibrators 12m & ACA - Flux | Uranus" (Table 1)
- flux scale uncertainty: _not stated_
- self calibration: one phase-only iteration then phase+amplitude for 12m; ACA same with 12m as model  
  > "A single iteration of phase-only self-calibration using line-free channels, followed by another iteration of phase and amplitude calibration of the 12-meter data improved image quality." (2 Observations)

### Imaging

- task: CLEAN; CONCAT; FEATHER  
  > "The 12-meter and ACA data were combined using `CONCAT` followed by continuum subtraction using `UVCONTSUB`." (2 Observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "Image cubes were created using Briggs weighting with a robust parameter of 0.5" (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: interactive CLEAN mask, then non-interactive CLEAN  
  > "a mask was created using the interactive mode of `CLEAN`." (2 Observations)
- multiscale scales: _not stated_
- continuum subtraction: UVCONTSUB  
  > "followed by continuum subtraction using `UVCONTSUB`" (2 Observations)
- line free channels: _not stated_
- primary beam correction: applied before combining with TP  
  > "A primary beam correction was applied to the cubes prior to combining them with TP data." (2 Observations)
- array combination: FEATHER with SD factor 1  
  > "combined with the TP data using `FEATHER` with a SD factor of 1 to recover missing flux" (2 Observations)
- smoothing: smoothed to 1.9''x1.4'', PA 78 deg to match CO(1-0)  
  > "the final cubes are smoothed to 1.9$''$$\times$1.4$''$, with a PA of 78$^{\circ}$ in order to match the CO(1–0) cube" (2 Observations)
- final beam: 1.9''x1.4''  
  > "Beam Size (smoothed cubes) | 1.9$''$$\times$1.4$''$" (Table 1)
- final rms: 2.2 mJy/beam (CO 2-1), 2.5 (CO 1-0)  
  > "(CO (2–1) smoothed cube) | 2.2 mJy beam$^{-1}$" (Table 1)

### Inherited from earlier work

- CO(1-0) calibration, processing and cube  
  > "Calibration and processing of the CO(1–0) is described in (cite: 2015ApJ...801...25L)." (2 Observations) [from (cite: 2015ApJ...801...25L)]
- Regions 1-10 positions  
  > "We make this measurement in the regions marked 1–10 from (cite: 2015ApJ...811...15L)." (3.3) [from (cite: 2015ApJ...811...15L)]
- Outflow mass/rate calculation method  
  > "following the calculations of (cite: 2013Natur.499..450B) the implied molecular mass outflow rate increases by factors of $3-6$" (5 Summary) [from (cite: 2013Natur.499..450B)]

### Not stated but needed to reproduce (our reading)

- Self-calibration solution intervals and line-free channels used
- CLEAN threshold, cell and image size, deconvolver details
- Exact velocity ranges of the 30 km/s windows per region
- Mask for outflow-mass apportioning and geometry used to get the outflow rate
- TP baseline/reduction details beyond the first-order polynomial
- Brightness-temperature conversion details

## Analysis recipe

1. **Calibrate, image and combine CO(2-1)**: Pipeline/scripts calibration, self-cal, CONCAT, UVCONTSUB, CLEAN, FEATHER with TP, smooth to CO(1-0) beam  
  > "The cubes were then combined with the TP data using `FEATHER` with a SD factor of 1 to recover missing flux" (2 Observations)
   - software: CASA
   - parameter: robust 0.5; SD factor 1; 5 km/s channels  
  > "Briggs weighting with a robust parameter of 0.5" (2 Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Build the r21 ratio cube**: Convert to Rayleigh-Jeans K with CMB correction, divide CO(2-1) by CO(1-0), mask edges using smoothed mask at 70% of peak  
  > "Emission that falls within 70$\%$ of the peak of the smoothed mask is then included in the final ratio cube." (3.1)
   - software: CASA IMSMOOTH
   - parameter: 20 mJy/beam threshold in CO(1-0); smoothing to 2.0''x1.5''  
  > "the thresholds are initially set at 20 mJy beam$^{-1}$ in the CO(1–0) cube" (3.1)
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure r21 in regions**: Average ratio in 1.9''x1.4'' apertures over custom 30 km/s ranges around emission peaks  
  > "we measure the ratio of CO(1–0) and CO(2–1) brightness temperatures over custom 30 km s$^{-1}$ velocity ranges" (3.3)
   - assumption: LTE, warm gas: r21~1 thick, up to ~4 thin  
  > "implying that in warm gas, $r_{21}$ can be as high as $4$." (3.2)
   - fitting: _not stated_
   - validation: Compared with and without short-spacing correction  
  > "The absence of short-spacing corrections typically affect the ratios by $<$10%" (3.4)
4. **Check flux recovery**: Smooth to 23'' and compare integrated fluxes to single-dish  
  > "We smooth the cubes using `IMSMOOTH` to a 23$''$ FWHM beam size" (3.4)
   - software: CASA IMSMOOTH
   - fitting: _not stated_
   - validation: Fluxes 72% (CO 1-0) and 79% (CO 2-1) of single-dish  
  > "which is 79$\%$ of the flux listed in (cite: 1999MNRAS.303..157H)" (3.4)
5. **Revise outflow mass and rate**: Scale Bolatto 2013 optically-thin results by alpha_CO 1-2 vs 0.34  
  > "If we adopt this range of conversion factors for all the molecular gas in the outflow, the implied molecular masses and mass loss rates would accordingly increase" (4.2)
   - assumption: alpha_CO = 1-2 Msun (K km/s pc^2)^-1 applies to outflow  
  > "constrain the CO-to-H$_2$ conversion factor there to be $\alpha_{\rm CO}=1-2$" (4.2)
   - fitting: _not stated_
   - validation: _not stated_
6. **Characterize extended CO(2-1) component**: Masked moment map (6-15 mJy/beam km/s per channel, dispersion >50 km/s), luminosity and mass estimate  
  > "the included emission must also have a velocity dispersion higher than 50 km s$^{-1}$" (4.3)
   - software: CASA IMMOMENTS
   - assumption: optically thin, alpha_CO=0.34, r21~3-4  
  > "applying a CO(1–0) optically-thin conversion factor of ${\alpha_{\rm CO}}=$0.34" (4.3)
   - fitting: _not stated_
   - validation: TP flagging (~20%) and first-order baseline removal tested  
  > "We started by flagging $\sim$20% of the total-power data showing possible baseline problems" (3.5)

## Software

- **CASA** 4.2.2 and 4.7.2: calibration, imaging, combination, moments, smoothing  
  > "Calibration of the CO(2–1) data was done using the Common Astronomy Software Application (CASA)." (2 Observations)
- **APLpy** : plotting  
  > "This research made use of APLpy, an open-source plotting package for Python" (Acknowledgments)
- **Matplotlib** : plotting  
  > "and Matplotlib (cite: Hunter:2007)" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| r21 range | 0.5 to 1.0 | not stated | dimensionless | 3 | we find that the $r_{21}$ ratio takes values between 0.5 and 1.0 |
| Total CO(1-0) flux in 23'' aperture | 650 | not stated | K km/s | 4 | Our total CO(1–0) flux is 650 K km s$^{-1}$. |
| Total CO(2-1) flux in 23'' aperture | 840 | not stated | K km/s | 4 | The flux we measure for CO(2–1) is 840 K km s$^{-1}$ |
| Molecular mass outflow rate | 25-50 | not stated | Msun/yr | 5 | ${\rm \dot{M}_{H2}}\sim25-50$ M$_\odot$ yr$^{-1}$ respectively |
| Mass-loading factor eta | 9-19 | not stated | dimensionless | 5 | would be in the range of 9 to 19 |
| Diffuse high-dispersion fraction of emission | ~15% | not stated | percent | 6 | accounts for $\sim$15$\%$ of the total emission in the central region and outflow |
| Extended component height above midplane | 100-340 | not stated | pc | 6 | the true height of the emission above the midplane is somewhere between 100 and 340 pc |

## Qualitative findings

- r21 under unity throughout, attributed to temperature gradients in optically thick gas  
  > "We attribute this to temperature gradients in the optically thick emitting gas." (5 Summary)

## Claim tuples

- H: CO in the NGC 253 outflow is optically thick | E: Measured r21 in disk, SW streamer and outflow features | R: r21 between 0.5 and 1.0, no optically thin values | F: CO emission is mostly optically thick in the outflow as in the starburst | **supported**
- H: Optically thin assumption underestimates outflow mass | E: Rescaled Bolatto 2013 estimates with starburst alpha_CO | R: Mass 2-4e7 Msun, rate 25-50 Msun/yr, eta 9-19 | F: Outflow rate 3-6 times the lower limit | **supported**
- H: The extended CO(2-1) component is real | E: TP flagging, baseline fitting, and comparison | R: Component persists | F: Tentatively real, biconical like ionized wind | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: 13CO too faint in outflow, so use r21 for optical depth  
  > "However, $^{13}$CO is difficult to detect in relatively faint outflow features." (Introduction)
- Alternative: Subthermal excitation or cold gas rejected as cause of low r21  
  > "This departure is not due to subthermal excitation, or exceedingly cold gas temperatures." (4.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Regions near the map edge may have artificially low r21 from poor flux recovery  
  > "In these cases $r_{21}$ could be artificially low." (3.4)
- Limitation (authors): Large uncertainties in alpha_CO, geometry and apportioning of CO to outflow  
  > "there are considerable uncertainties associated with these values beyond the adoption of a conversion factor" (4.2)
- Caveat (inferred, ours): Mass rate relies on applying central-starburst alpha_CO to the outflow without independent check
- Caveat (inferred, ours): Thresholds (70% mask, 30 km/s windows) are arbitrary and no uncertainty propagation on r21 beyond 2 sigma
- Caveat (inferred, ours): Extended component may be a TP combination artifact

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: CO(1-0) combined cube from Leroy et al. 2015
- Missing: Region masks and velocity windows
- Missing: Outflow mass map from Bolatto 2013 for rate rescaling
- Data volume (inferred): ~50-100 GB raw for three projects
- Score (inferred): 3/5, Data identifiable and processing described, but key imaging parameters and CO(1-0) cube come from earlier work.
- Rediscovery candidate: no, Needs the previously published CO(1-0) cube and several unstated settings; the outflow rate is a rescaling of external numbers.

## Links

- Method: (cite: 2015ApJ...801...25L) (CO(1-0) calibration and cube)
- Method: (cite: 2013Natur.499..450B) (Outflow mass and rate calculation)
- Companion: (cite: 2017ApJ...835..265W) (Dense gas tracers in the outflow)

## Checks

```json
{
 "quotes": 64,
 "quotes_ok": 64,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.1.00172.S"
 ],
 "obscore_codes_not_in_card": [
  "2011.0.00172.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 50,
  "rate": 0.625
 },
 "evidence_ok": true
}
```
