# The Architecture of the GW Ori Young Triple-star System and Its Disk: Dynamical Masses, Mutual Inclinations, and Recurrent Eclipses

`2017ApJ...851..132C` | The Astrophysical Journal 2017 | first author: Czekala, Ian | arXiv: 1710.03153 | DOI: 10.3847/1538-4357/aa9be7

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation, stellar_physics
- Question: What are the dynamical masses, orbital architecture and disk/orbit mutual inclinations of the GW Ori triple system, and what causes its recurrent eclipses?  
  > "In this paper, we combine information from each of these techniques to better understand the fundamental properties and underlying physical architecture of the GW Ori system." (Introduction)
- Target **GW Ori**: coordinates _not stated_; z/distance 388 pc  
  > "We adopt a fixed distance to the GW Ori system, $d = 388\,$pc (cite: kounkel17)" (Analysis and Results); distance from Kounkel et al. 2017 (cite: kounkel17)  
  > "We adopt a fixed distance to the GW Ori system, $d = 388\,$pc (cite: kounkel17)" (Analysis and Results)

## Data provenance

- ALMA projects: 2012.1.00496.S
- bands: Band 6 (1.3 mm)  
  > "The double sideband Band 6 receivers were employed in dual polarization mode" (2.1 Millimeter Interferometry)
- frequencies and spectral setup: 4 SPWs: 13CO and 12CO 2-1 (234 MHz, 61 kHz channels), C18O 2-1 (469 MHz, 122 kHz channels), continuum 1.875 GHz around 231.956 GHz  
  > "The last SPW sampled the continuum in a 1.875 GHz range around 231.956 GHz using 128 coarse channels" (2.1 Millimeter Interferometry)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: 37 12 m antennas, baselines 23-558 m  
  > "with 37 of the 12 m main array antennas configured to span baselines of 23–558 m" (2.1 Millimeter Interferometry)
- baselines: _not stated_
- angular resolution: ~0.9"x0.55" beam (226 GHz continuum 0.88"x0.54")  
  > "226 GHz continuum | $0.88\ensuremath{''}\times0.54\ensuremath{''}$, 126$^\circ$  | 0.055" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: continuum RMS 0.055 mJy/beam; line RMS 6, 8, 5 mJy/beam per 170 m/s channel (12CO, 13CO, C18O)  
  > "$^{13}$CO $J$=2$-$1 | $0.93\ensuremath{''}\times0.59\ensuremath{''}$, 126$^\circ$  | 8" (Table 1)
- time on source: 16 minutes  
  > "The total on-source integration time for GW Ori was 16 minutes." (2.1 Millimeter Interferometry)
- observing dates: 2015 May 14  
  > "GW Ori was observed with the ALMA interferometer on 2015 May 14" (2.1 Millimeter Interferometry)
- pi or archival as stated: _not stated_
- Line: 13CO J=2-1 (220.399 GHz)
- Line: C18O J=2-1 (219.560 GHz)
- Line: 12CO J=2-1 (230.538 GHz)
- Other facility **CfA DS echelle spectrographs and TRES**: 203 + 79 optical spectra for radial velocities over 35 years  
  > "A total of 203 usable spectra were gathered through 2009 April using three nearly identical echelle spectrographs" (2.2 Optical Spectroscopy)
- Other facility **Maidanak, KELT, ASAS, ASAS-SN**: V-band light curve spanning ~30 years  
  > "We have assembled a high cadence lightcurve of GW Ori covering a $\sim$30 year timespan" (2.3 Time-series Photometry)
- External data: Three epochs of astrometry and H-band flux ratios of the GW Ori triple  
  > "Combining the results from the ALMA data and the optical spectra with three epochs of astrometry in the literature" (Abstract) [from Berger et al. 2011 (cite: berger11)]
- External data: Distance 388 pc  
  > "We adopt a fixed distance to the GW Ori system, $d = 388\,$pc (cite: kounkel17)" (3.1) [from (cite: kounkel17)]
- External data: CO abundance ratios  
  > "\[$^{12}$CO/H\] = $7.5 \times 10^{-5}$, \[$^{12}$CO/$^{13}$CO\] = 69, and \[$^{12}$CO/C$^{18}$O\] = 557 (cite: henkel94; prantzos96)" (3.1) [from (cite: henkel94; prantzos96)]
- Simulation/model as data: PHOENIX synthetic templates, NextGen atmospheres and MIST evolutionary tracks  
  > "we adopted synthetic templates from the PHOENIX library of (cite: husser13)" (2.2 Optical Spectroscopy)

## Processing

### Calibration

- pipeline or manual: standard CASA procedures  
  > "The visibility data were calibrated with standard procedures using the CASA software package (v4.4)." (2.1 Millimeter Interferometry)
- casa version: CASA v4.4  
  > "using the CASA software package (v4.4)" (2.1 Millimeter Interferometry)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ganymede (bandpass J0423-0120, gain J0510+1800)  
  > "The absolute amplitude scale was determined based on the observations of Ganymede." (2.1 Millimeter Interferometry)
- flux scale uncertainty: _not stated_
- self calibration: two rounds phase-only (30 s, 6 s) then one amplitude+phase round (7 min); continuum RMS reduced ~40x  
  > "two rounds of phase-only self-calibration (on 30 s, then 6 s intervals) and one additional round that included the amplitudes (on a 7 minute scan interval)" (2.1 Millimeter Interferometry)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs robust=0.5  
  > "assuming a Briggs (robust=0.5) weighting scheme and deconvolution with the standard `CLEAN` algorithm" (2.1 Millimeter Interferometry)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: line cubes continuum-subtracted, regridded to 170 m/s channels in LSRK over ~10 km/s  
  > "were continuum-subtracted and regridded into 170 m s$^{-1}$-wide channels in the LSRK restframe over a $\sim$10 km s$^{-1}$ range around the line centers" (2.1 Millimeter Interferometry)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.88"x0.54" at 126 deg (continuum)  
  > "226 GHz continuum | $0.88\ensuremath{''}\times0.54\ensuremath{''}$, 126$^\circ$  | 0.055" (Table 1)
- final rms: _not stated_

### Inherited from earlier work

- Disk forward-modeling procedure with DiskJockey  
  > "We follow the forward modeling procedures described by (cite: czekala15a; czekala16) using the associated open-source software package `DiskJockey`." (3.1) [from (cite: czekala15a; czekala16)]
- Geometric prior on disk inclination  
  > "where instead we adopt a simple geometric prior (cite: czekala16)" (3.1) [from (cite: czekala16)]
- Disk velocity field with emitting layer  
  > "with a velocity field that appropriately accounts for the two-dimensional distribution of the emitting layer (cite: rosenfeld13a)" (3.1) [from (cite: rosenfeld13a)]

### Not stated but needed to reproduce (our reading)

- Image size and cell size of the ALMA cubes
- Line-free channels used for continuum and subtraction
- Starting priors/bounds and MCMC walker count and steps for the disk fit
- Grid and radiative-transfer settings for RADMC-3D (inner radius, outer radius, resolution)
- Spatial/velocity masks for the CLEAN images
- Exact flux scale uncertainty for Ganymede

## Analysis recipe

1. **Calibrate, self-calibrate and image ALMA data**: CASA calibration, phase and amplitude self-calibration on continuum, line cubes imaged with Briggs robust 0.5 CLEAN  
  > "These fully reduced visibility sets were then imaged by Fourier inversion assuming a Briggs (robust=0.5) weighting scheme" (2.1 Millimeter Interferometry)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Forward-model 13CO and C18O disk velocity field for total mass and inclination**: Parametric Keplerian disk, LTE radiative transfer with RADMC-3D, Fourier-transformed and compared to visibilities with chi^2 likelihood  
  > "The model quality with respect to the observed visibilities is evaluated with a $\chi^2$ likelihood function that incorporates the nominal visibility weights." (3.1)
   - software: DiskJockey, RADMC-3D, emcee
   - parameter: data averaged to 25 channels of 0.4 km/s; fixed d = 388 pc  
  > "we only model the data averaged to 25 channels of $0.4\,{\rm km\thinspace s^{-1}}$ width" (3.1)
   - assumption: vertically isothermal; abundance ratios H2/gas=0.8, H/H2=2, 12CO/H=7.5e-5, 12CO/13CO=69, 12CO/C18O=557; LTE  
  > "we assume a vertically isothermal model with a radial profile $T(r) = T_{10} (r/10$ AU$)^{-q}$" (3.1)
   - fitting: Affine-invariant ensemble MCMC (emcee, Julia port); flat priors except geometric prior on inclination  
  > "We assume flat priors on all parameters except for $i_\mathrm{disk}$, where instead we adopt a simple geometric prior (cite: czekala16)." (3.1)
   - validation: Compared more complex disk models via visual inspection and AIC; found similar M_tot  
  > "Encouragingly, however, they still yielded similar estimates of $M_\mathrm{tot}$ as the standard model" (3.1)
3. **Combine masses and inclinations from the two lines**: Weighted combination of 13CO and C18O M_tot, plus 1.3% distance uncertainty; weighted-mean inclination with large systematic uncertainty  
  > "we convolve an additional 1.3% mass uncertainty with this posterior to arrive at $M_\mathrm{tot} = 5.29 \pm 0.09\,M_\odot$" (3.1)
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit hierarchical triple orbit to RVs, RV+astrometry, and RV+disk mass**: Hierarchical triple model with 3D orbit; RV from TODCOR/PSOAP; joint chi^2 likelihood; mutual inclination from angular momentum vectors  
  > "We use the ensemble sampler MCMC (cite: goodman10; foreman-mackey13) with 20 walkers to explore the posterior for 50,000 iterations, burn 25,000 iterations" (3.3)
   - software: TODCOR, PSOAP, emcee, IRAF
   - fitting: emcee, 20 walkers, 50,000 iterations, 25,000 burn-in, Gelman-Rubin <1.1; flat mass priors, geometric inclination priors  
  > "assess convergence by ensuring the Gelman-Rubin statistic (cite: gelman14) is $\hat{R} < 1.1$ for all parameters" (3.3)
   - validation: Consistency between RV+astrometry M_tot and disk M_tot  
  > "Both measurements are consistent with the $M_\mathrm{tot}$ independently measured with the disk-based analysis" (3.2)

## Software

- **CASA** 4.4: calibration, self-calibration and imaging  
  > "using the CASA software package (v4.4)" (2.1 Millimeter Interferometry)
- **DiskJockey** : forward modeling of disk line emission  
  > "using the associated open-source software package `DiskJockey`" (3.1)
- **RADMC-3D** : ray-tracing molecular line emission  
  > "ray-trace the associated emission into a set of high resolution channel maps using the radiative transfer package `RADMC-3D`" (3.1)
- **emcee** : MCMC sampling  
  > "as implemented in the `emcee` code (cite: foreman-mackey13)" (3.1)
- **PSOAP** : spectroscopic disentangling  
  > "We embarked on a search for such a signature using the then-under-development `PSOAP` spectroscopic disentangling package" (2.2 Optical Spectroscopy)
- **TODCOR** : two-dimensional cross-correlation RVs  
  > "a targeted `TODCOR` analysis, which is a two-dimensional cross-correlation algorithm" (2.2 Optical Spectroscopy)
- **IRAF XCSAO** : 1D cross-correlations  
  > "computed using the IRAF[^1] task `XCSAO`" (2.2 Optical Spectroscopy)
- **VARTOOLS** : Lomb-Scargle period search  
  > "we used the Lomb-Scargle (LS) periodicity search algorithm" (3.4)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total stellar mass (disk-based) | 5.29 | 0.09 | Msun | 3 | $M_\mathrm{tot} = 5.29 \pm 0.09\,M_\odot$, which we report as the total mass estimate |
| Disk inclination | 137.6 | 2.0 | deg | 3 | resulting in a final estimate of $i_\mathrm{disk} = 137.6 \pm 2.0^\circ$ |
| Inner orbit period | 241.50 | 0.05 | days | 4 | $241.50\pm0.05$ day period |
| Outer orbit period | 4218 | 60 | days | 4 | $P_\mathrm{out} = 4218 \pm 60$ days |
| Inner binary mass ratio q=MB/MA | 0.60 | 0.02 | dimensionless | 4 | a mass ratio of $q \equiv M_\mathrm{B} / M_\mathrm{A} = 0.60 \pm 0.02$ |
| Disk-inner orbit mutual inclination | 44 | 5 | deg | 4 | $\Phi_\mathrm{in} = 44\pm5^\circ$ |
| Disk-outer orbit mutual inclination | 54 | 7 | deg | 4 | $\Phi_\mathrm{out} = 54 \pm 7^\circ$ |
| Continuum flux density at 226 GHz | 202 | 20 | mJy | 1 | flux density = $202\pm20$ mJy |
| M_A (RV + disk) | 2.74 | +0.15/-0.52 | Msun | 4 | $M_\mathrm{A}$ \[$M_\odot$\] / $2.80_{-0.31}^{+0.36}$ / $2.74_{-0.52}^{+0.15}$ |

## Qualitative findings

- Eclipses are not strictly periodic with the inner orbit; 0.2 mag oscillation phased with outer orbit, minimum near apoastron  
  > "The 11.5 yr variability reaches a minimum flux level near apoastron (phase = 0.5) of the outer orbit." (3.4)

## Claim tuples

- H: Disk-based dynamics can give the total stellar mass of GW Ori | E: Forward-model 13CO and C18O ALMA visibilities | R: M_tot = 5.29 ± 0.09 Msun, consistent between lines | F: Robust dynamical total mass | **supported**
- H: Stellar orbits are coplanar with the disk | E: Compare disk inclination with RV+astrometry orbits | R: Mutual inclinations ~44 and ~54 deg | F: Orbits misaligned with disk | **supported**
- H: Eclipses arise from Algol-like edge-on inner orbit | E: Orbit fit and 30-yr light curve | R: Inner orbit not edge-on; eclipses not strictly periodic | F: Algol mechanism disfavored; AB partly obscured by inner-disk material | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Models with vertical temperature gradient and CO depletion, and flexible temperature model, did not fit better  
  > "we found that neither of these models resulted in a more satisfactory fit to the data as measured by visual inspection and the Akaike information criterion" (3.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Only three astrometric epochs; possible unaccounted systematics; 12CO contaminated by cloud  
  > "Since these results only rest upon three astrometric epochs, however, there is a possibility that the large inferred mutual inclinations may be the result of unaccounted for systematic effects." (3.2)
- Caveat (inferred, ours): 13CO and C18O inclinations disagree; systematic uncertainty is ad hoc
- Caveat (inferred, ours): Distance fixed at 388 pc; a different distance would shift mass linearly
- Caveat (inferred, ours): RVs from heavily blended lines are template-sensitive
- Caveat (inferred, ours): No joint fit to both lines, no 12CO use

## Reproducibility

- Data public (paper): ALMA project 2012.1.00496.S is cited; DiskJockey is open source; RV and photometry tables machine-readable  
  > "Available under an MIT license at <https://github.com/iancze/DiskJockey>." (Software footnote)
- Products in archive: _not stated_
- Code: DiskJockey released under MIT license  
  > "Available under an MIT license at <https://github.com/iancze/DiskJockey>." (Software footnote)
- Missing: Imaging grid parameters
- Missing: MCMC setup for disk fit
- Missing: Compute cost ~10,000 CPU hours per line
- Data volume (inferred): ~ a few GB (single ALMA execution block)
- Score (inferred): 3/5, Public single-EB ALMA data and open code, but disk fits are very expensive and some settings are unstated.
- Rediscovery candidate: no, Disk-fit cost is very high and the full result also needs optical RVs and astrometry.

## Links

- Method: Czekala et al. 2015a, 2016 (cite: czekala15a; czekala16) (disk forward-modeling method)
- Method: Czekala et al. 2017 (cite: czekala17) (PSOAP disentangling)
- Companion: Fang et al. 2017 (cite: fang17) (SMA study of the GW Ori disk)
- Companion: Berger et al. 2011 (cite: berger11) (interferometric astrometry of the triple)
- Related: KELT
- Related: ASAS
- Related: ASAS-SN

## Checks

```json
{
 "quotes": 66,
 "quotes_ok": 66,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 49,
  "rate": 0.628
 },
 "evidence_ok": true
}
```
