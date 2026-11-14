# CO emission tracing a warp or radial flow within ≲100 au in the HD 100546 protoplanetary disk

`2017A&A...607A.114W` | Astronomy and Astrophysics 2017 | first author: Walsh, Catherine | arXiv: 1710.00703 | DOI: 10.1051/0004-6361/201731334

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks
- Question: Does the 12CO J=3-2 velocity field of the HD 100546 disk deviate from Keplerian rotation, indicating an inner-disk warp or radial flow?  
  > "The focus of this work is the search for evidence of a warp in the inner regions of the disk, as suggested by the single dish data presented in (cite: panic10)." (1 Introduction)
- Target **HD 100546**: coordinates _not stated_; z/distance not stated (revised Gaia distance adopted; value not given)  
  > "we adopt the revised distance to HD 100546 determined by Gaia (cite: gaia16a; gaia16b), and a stellar mass of $2.4 M_{\odot}$, (cite: vandenancker98)" (2 ALMA imaging of HD 100546); distance from Gaia (gaia16a; gaia16b)  
  > "we adopt the revised distance to HD 100546 determined by Gaia (cite: gaia16a; gaia16b), and a stellar mass of $2.4 M_{\odot}$, (cite: vandenancker98)" (2 ALMA imaging of HD 100546)

## Data provenance

- ALMA projects: 2011.0.00863.S
- bands: _not stated_
- frequencies and spectral setup: 12CO J=3-2 at 345.796 GHz; 0.15 km/s channels in Paper I imaging  
  > "at a spectral resolution of 0.15 km s$^{-1}$" (2 ALMA imaging of HD 100546)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 21 to 375 m, 24 antennas, compact configuration  
  > "HD 100546 was observed with ALMA on 2012 November 24 with 24 antennas in a compact configuration, with baselines ranging from 21 to 375 m." (2 ALMA imaging of HD 100546)
- angular resolution: 0.92'' x 0.38'' (37 deg) with uniform weighting  
  > "a synthesised beam of $0.92\ensuremath{''}\times0.38\ensuremath{''}~(37\degree)$" (2 ALMA imaging of HD 100546)
- max recoverable scale: _not stated_
- sensitivity: rms 26 mJy/beam/channel (uniform), S/N 106  
  > "The resulting channel maps have an rms noise of 26 mJy beam$^{-1}$ channel$^{-1}$, a S/N of 106" (2 ALMA imaging of HD 100546)
- time on source: _not stated_
- observing dates: 2012 November 24  
  > "HD 100546 was observed with ALMA on 2012 November 24 with 24 antennas in a compact configuration, with baselines ranging from 21 to 375 m." (2 ALMA imaging of HD 100546)
- pi or archival as stated: _not stated_
- Line: 12CO J=3-2 (345.796 GHz)
- Other facility **VLT/SPHERE, MagAO/GPI, VLTI/PIONIER**: Literature scattered-light and interferometric constraints on inner dust disk alignment, used for comparison  
  > "recent VLT/SPHERE, MagAO/GPI, and VLTI/PIONIER observations of HD 100546 that show no evidence of a severely misaligned inner *dust* disk" (abstract)
- External data: Stellar mass 2.4 Msun  
  > "a stellar mass of $2.4 M_{\odot}$, (cite: vandenancker98)" (2 ALMA imaging of HD 100546) [from (cite: vandenancker98)]
- External data: Outer disk P.A. 146+-4 deg and inclination 44+-3 deg from continuum  
  > "a P.A. of $146\degree \pm 4\degree$ and an inclination of $44\degree \pm 3\degree$ (cite: pineda14)" (3.1 A flat emitting surface) [from (cite: pineda14)]
- External data: CO emitting layer opening angle ~11 deg from thermo-chemical modelling  
  > "suggest an opening angle $\alpha \approx 11\degree$ (cite: bruderer12)" (3.2 A flared emitting surface) [from (cite: bruderer12)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Self-calibrated, phase-corrected measurement set from Paper I  
  > "The self-calibrated and phase-corrected measurement set, produced as described in Paper I, is used in these analyses." (2 ALMA imaging of HD 100546)

### Imaging

- task: CASA clean (Paper I); re-imaged here  
  > "The data cube from which those maps were produced was itself produced using the CASA task `clean` with Briggs weighting (robust=0.5)" (2 ALMA imaging of HD 100546)
- deconvolver: _not stated_
- weighting robust: Uniform weighting in this work (Briggs robust=0.5 in Paper I)  
  > "the imaging is redone here using uniform weighting which results in a smaller beam" (2 ALMA imaging of HD 100546)
- uv taper: _not stated_
- cell size: 0.12''  
  > "The maps were created using a pixel size of 0.12$''$ to ensure that the beam is well sampled." (2 ALMA imaging of HD 100546)
- image size: _not stated_
- masking: Moment 0 with 3 sigma clip; moments 1, 2, 8 with 6 sigma clip  
  > "The zeroth moment map (integrated intensity) was produced using a $3\sigma$ rms noise clip." (2 ALMA imaging of HD 100546)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.92'' x 0.38'' (37 deg)  
  > "a synthesised beam of $0.92\ensuremath{''}\times0.38\ensuremath{''}~(37\degree)$" (2 ALMA imaging of HD 100546)
- final rms: 26 mJy/beam/channel  
  > "The resulting channel maps have an rms noise of 26 mJy beam$^{-1}$ channel$^{-1}$" (2 ALMA imaging of HD 100546)

### Inherited from earlier work

- Self-calibration and phase correction of the measurement set  
  > "The self-calibrated and phase-corrected measurement set, produced as described in Paper I, is used in these analyses." (2 ALMA imaging of HD 100546) [from Paper I = (cite: walsh14)]
- Source velocity 5.7 km/s  
  > "the central channel is centred at the source velocity of 5.7 km s$^{-1}$ as constrained previously by these data (see Paper I)" (2 ALMA imaging of HD 100546) [from Paper I = (cite: walsh14)]
- Toy-model approach for warp and radial flow  
  > "We adopt the same approach as the toy models presented in (cite: rosenfeld14) and assume that the radial velocity component is a fixed fraction of the local Keplerian velocity" (3.4 A radial flow) [from (cite: rosenfeld14)]

### Not stated but needed to reproduce (our reading)

- Gaia distance value used for converting angular to au
- Source coordinates / phase centre
- Spectral setup details and calibrators (only in Paper I)
- Exact clean parameters (niter, threshold, mask) for the uniform-weighted cube
- Pixel masking criterion yielding the 2562 unmasked first-moment pixels
- Moment-map generation code and model code are not given
- Velocity resolution relation between 0.15 km/s channels and delta v = 0.21 km/s

## Analysis recipe

1. **Re-image 12CO cube and make moment maps**: Re-clean with uniform weighting; zeroth moment 3 sigma clip, first/second/eighth 6 sigma clip  
  > "the imaging is redone here using uniform weighting which results in a smaller beam" (2 ALMA imaging of HD 100546)
   - software: CASA
   - parameter: pixel 0.12'', rms 26 mJy/beam/channel  
  > "The maps were created using a pixel size of 0.12$''$ to ensure that the beam is well sampled." (2 ALMA imaging of HD 100546)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit flat and flared Keplerian surface to first-moment map**: Analytic line-of-sight velocity model convolved with the beam; grid search over inclination, P.A. and opening angle (coarse 5 deg then 1 deg)  
  > "First, a coarse grid with a resolution of 5 is run over the full parameter space, followed by a zoomed in region with a resolution of 1." (3.1 A flat emitting surface)
   - parameter: Inclination 20-60 deg, P.A. 120-170 deg, opening angle 0-20 deg  
  > "The range of surface opening angles ($[0\degree,20\degree]$)" (3.2 A flared emitting surface)
   - assumption: Stellar mass 2.4 Msun; Keplerian rotation; emission from flat or double-cone surface  
  > "a stellar mass of $2.4 M_{\odot}$" (2 ALMA imaging of HD 100546)
   - fitting: Grid based, all combinations explored; best fit by three metrics: pixels within one delta v, sum of squared residuals per pixel, peak residual  
  > "the modelling approach is grid based, i.e. all possible grid combinations are explored." (3 Modelling the kinematics)
   - validation: Residual histograms and maps compared by eye and by metrics  
  > "The histogram of residuals shows small dispersion about 0 with 96.0% of pixels matching the data within $\pm0.315$ km s$^{-1}$." (3.1 A flat emitting surface)
3. **Fit misaligned inner-disk warp model**: Outer disk fixed to best upper-cone model; inner flat disk with own inclination, P.A. and transition radius; coarse grid 10 deg/10 au then 2 deg/2 au  
  > "A coarse grid with a resolution of 10 and 10 au is first run to identify the parameter space containing the global best-fit" (3.3 A warped disk)
   - parameter: inner inclination 40-90 deg, inner P.A. 40-100 deg, transition radius 40-120 au  
  > "the inner disk inclination (\[40, 90\]), the inner disk P.A. (\[40, 100\]), and a transition radius marking the boundary between the inner and outer disks (\[40, 120\] au)" (3.3 A warped disk)
   - assumption: Inner disk planar and flat Keplerian  
  > "we assume that the inner disk velocity structure is described using the flat disk prescription" (3.3 A warped disk)
   - fitting: Grid search with the three metrics  
  > "Given the relatively small number of parameters for each model considered, the modelling approach is grid based, i.e. all possible grid combinations are explored." (Modelling the kinematics)
   - validation: Peak residual compared with flat/flared models  
  > "The magnitude of the peak residual of this model is significantly smaller than the previous models selected using metric (i), $4 \delta v$ versus $7 \delta v$." (3.3 A warped disk)
4. **Fit radial-flow model**: Radial velocity v_r = chi v_K inside a transition radius, flat disk inside; coarse grid 10 au/0.1 then 1 au/0.01  
  > "we first run a coarse grid at a resolution of 10 au and 0.1, followed by a finer grid with a resolution of 1 au and 0.01" (3.4 A radial flow)
   - parameter: transition radius 10-120 au; chi 0 to sqrt(2)  
  > "the transition radius (\[10,120\] au) and the scaling factor $\chi$ (\[0:$\sqrt{2}$\])" (3.4 A radial flow)
   - assumption: Outer disk fixed to best upper-cone model  
  > "The disk velocity structure is fixed to that of the best-fit upper cone model for the outer disk" (3.4 A radial flow)
   - fitting: Grid search with the three metrics  
  > "Given the relatively small number of parameters for each model considered, the modelling approach is grid based, i.e. all possible grid combinations are explored." (Modelling the kinematics)
   - validation: Compared with warp model via peak residual  
  > "using metric (iii) the peak residual for the former model is 3.7$\delta v$ versus 2.4$\delta v$ for the latter." (3.4 A radial flow)
5. **Estimate warp precession period**: Scaling relation from Lai 2014 / Debes 2017 for assumed companions  
  > "The precession period of a warp induced by a perturbing companion can be estimated using equation (2) in (cite: debes17)" (4.1 Is the inner disk warped?)
   - parameter: mu_c = 0.006, r_disk = 40 au, a_c = 50 au, i_c = 80 deg  
  > "setting $\mu_c = 0.006$, $r_\mathrm{disk} =$40 au, and $a_c=50$ au results in a precession period of 1940 yr" (4.1 Is the inner disk warped?)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Imaging with task clean  
  > "using the CASA task `clean` with Briggs weighting (robust=0.5)" (2 ALMA imaging of HD 100546)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Best-fit flat disk inclination / P.A. (metric i) | 36 deg / 145 deg | not stated | deg | 2 | / Flat / \(i\) / 36 / 145 / 0 / 1590 / 62.1% / 0.737 / 7.23 / |
| Best upper-cone flared model inclination / P.A. / opening angle | 36 / 145 / 9 deg | not stated | deg | 2 | The best-fit inclination, P.A., and opening angle are 36, 145, and 9, respectively |
| Best warp model (metric i): inner inclination, P.A., transition radius | 80 deg, 60 deg, 90 au | not stated | deg, deg, au | 3 | / Warped / \(i\) / 80 / 60 / 90 / 1722 / 67.2% / 0.387 / 4.06 / |
| Best warp model (metrics ii & iii) | 84 deg, 64 deg, 100 au; peak residual 2.44 dv | not stated | deg, deg, au | 3 | / / \(ii\) & (iii) / 84 / 64 / 100 / 1710 / 66.4% / 0.350 / 2.44 / |
| Radial flow best fit (metric i): transition radius, chi | 54 au, 1.23 | not stated | au, dimensionless | 4 | Metric (i) favours a radial component to the flow within a radius of 54 au and a velocity scaling factor of $\chi = 1.23$ which is close to the free-fall velocity. |
| Warp precession period for companion at 50 au | 1940 | not stated | yr | 5 | results in a precession period of 1940 yr |
| Warp precession period for companion at 10 au | 111 | not stated | yr | 5 | leads to a precession period of 111 yr |

## Qualitative findings

- Emission is detected down to ~16 au radius (8 au for inclination 30 deg); the CO emitting surface is relatively flat.  
  > "emission is detected down to a radius of 16 au from the central star." (2 ALMA imaging of HD 100546)

## Claim tuples

- H: Is the CO velocity field Keplerian with a single inclination and P.A.? | E: Fit flat and flared Keplerian models to the first-moment map | R: Residuals reach ~7 dv in the inner disk | F: A purely Keplerian model with universal geometry does not describe the gas | **supported**
- H: A misaligned inner gas disk explains the residuals | E: Warp model grid fit | R: Peak residual reduced to <3 dv with nearly edge-on inner disk almost orthogonal in P.A. | F: A twisted warp within ~100 au fits best but conflicts with dust observations | **partially**
- H: Fast radial flows explain the kinematics | E: Radial flow grid fit | R: Residuals of ~4 dv with near free-fall inflow inside ~50 au | F: Fits worse than warp model | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Simple toy models because residuals are about the beam size  
  > "Because the residuals are of the order of the size of the synthesised beam, a simple toy prescription for the warp is used." (3.3 A warped disk)
- Alternative: Radial flow considered as alternative to warp; fits worse  
  > "However, the radial flow model does not reproduce the velocity structure as well as the warped disk" (3.4 A radial flow)
- How they decided it was enough: _not stated_
- Limitation (authors): Resolution insufficient; higher resolution (~10 au) data needed  
  > "Molecular emission data at a higher spatial resolution (of order 10 au) are required to further constrain the kinematics within $\lesssim 100$ au." (abstract)
- Limitation (authors): Brightness asymmetries not modelled  
  > "Note that this analysis will not address the asymmetry in CO brightness across the disk seen in the channel maps and zeroth and eighth moment maps." (3 Modelling the kinematics)
- Caveat (inferred, ours): No uncertainties on best-fit parameters; grid metrics only
- Caveat (inferred, ours): First-moment-only fitting is degenerate between warp and radial flow
- Caveat (inferred, ours): Model optimization relies on pixel thresholds tied to delta v, not statistical likelihood
- Caveat (inferred, ours): Extreme warp parameters conflict with scattered light

## Reproducibility

- Data public (paper): Project code given in acknowledgements; Cycle 0 data  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00863.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Gaia distance value
- Missing: Model code not released
- Missing: Exact clean parameters and moment-map masks
- Missing: Calibration details only in Paper I
- Data volume (inferred): ~10-30 GB raw for one Cycle 0 band 7 execution
- Score (inferred): 3/5, Public data and simple grid models with full parameter ranges, but the code, distance and several imaging details are missing, and calibration is deferred to Paper I.
- Rediscovery candidate: yes, Public Cycle 0 data, analytic grid models with stated ranges and numeric best fits in tables.

## Links

- Method: (cite: rosenfeld13) (Flat and flared disk velocity model)
- Method: (cite: rosenfeld14) (Warp and radial flow toy models)
- Companion: (cite: walsh14) (Paper I: data calibration and continuum)
- Companion: (cite: pineda14) (Earlier analysis of the same CO dataset)

## Checks

```json
{
 "quotes": 62,
 "quotes_ok": 62,
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
  "facts": 78,
  "stated": 48,
  "rate": 0.615
 },
 "evidence_ok": true
}
```
