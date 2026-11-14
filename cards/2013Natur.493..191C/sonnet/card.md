# Flows of gas through a protoplanetary gap

`2013Natur.493..191C` | Nature 2013 | first author: Casassus, Simon | arXiv: 1305.6062 | DOI: 10.1038/nature11769

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: Is there gas inside the large dust gap of HD 142527, and does it flow across the gap along filaments that could feed stellar accretion?  
  > "so in order to sustain the observed accretion, matter must flow from the outer-disk into the cavity and cross the gap." (abstract)
- Target **HD 142527**: coordinates J2000 15:56:41.878 -42:19:23.568 (June 2012 epoch)  
  > "the young star HD 142527, at $\sim$140 pc" (abstract); "J2000 15:56:41.878 -42:19:23.568" (Registration of ALMA images); z/distance ~140 pc  
  > "the young star HD 142527, at $\sim$140 pc" (abstract); "J2000 15:56:41.878 -42:19:23.568" (Registration of ALMA images); distance from supported by a probable association to Sco OB2  
  > "the young star HD 142527, at $\sim$140 pc" (abstract); "J2000 15:56:41.878 -42:19:23.568" (Registration of ALMA images)

## Data provenance

- ALMA projects: 2011.0.00465.S
- bands: Band 7  
  > "ALMA Band 7 observations of HD142527 were carried out in the night of June 2 2012." (ALMA setup)
- frequencies and spectral setup: FDM, four spectral windows of 468.750 MHz, 122.07 kHz (0.1 km/s) channels, targeting CO(3-2), HCO+, CS(7-6), HCN(4-3)  
  > "configured in the Frequency Division Mode (FDM) to provide 468.750 MHz bandwidth in four different spectral windows at 122.07 kHz resolution ( 0.1 km/s) per channel." (ALMA setup)
- continuum bandwidth: _not stated_
- arrays: 12 m antennas, 19 available, two flagged  
  > "The number of 12 m antennas available at the time of the observation was 19" (ALMA setup)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: CO beam 0.55x0.33 arcsec  
  > "0.9 Jy beam$^{-1}$ in a $0.55\times0.33$ arcsec$^{2}$ beam" (Conditions along the filaments)
- max recoverable scale: _not stated_
- sensitivity: RMS 15 mJy in 0.1 km/s channels  
  > "yielding an RMS of 15 mJy in 0.1 km s$^{-1}$ channels." (ALMA setup)
- time on source: 52 minutes  
  > "a total time on source of 52 minutes was spent yielding an RMS of 15 mJy in 0.1 km s$^{-1}$ channels." (ALMA setup)
- observing dates: June 2 2012  
  > "carried out in the night of June 2 2012" (ALMA setup)
- pi or archival as stated: _not stated_
- Line: CO J=3-2 (345.7959 GHz)
- Line: HCO+ J=4-3 (not stated)
- Other facility **Gemini South NICI**: Near-IR ADI imaging and protoplanet search  
  > "HD 142527 was imaged by the Near-Infrared Coronagraphic Imager (NICI) at the Gemini South telescope" (Near-IR ADI processing)
- External data: Stellar accretion rate of 7e-8 Msun/yr  
  > "observed stellar accretion rate(cite: 2006A&A...459..837G) of $7 \times
10^{-8}$ M$_{\odot}$ yr $^{-1}$" (main text) [from (cite: 2006A&A...459..837G)]
- External data: Disk inclination ~20 deg from multi-wavelength data  
  > "Multi-wavelength data are consistent with an inclination of $\sim$20$^{\circ}$, so almost face-on" (main text) [from (cite: 2011A&A...528A..91V)]
- Simulation/model as data: LIME Keplerian disk model (20 deg, PA -20 deg, 140 pc, 2.7 Msun) as kinematic comparison  
  > "This model is inclined at 20 deg, with a PA of $-20$ deg east of north, and is placed at a distance of 140 pc with a 2.7 M$_\odot$ central star." (Comparison disk models)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (CASA Butler-JPL-Horizons 2010 model); 3c279 bandpass, J1604-446 phase  
  > "The primary flux calibrator was Titan, which provided a mean transferred flux of 14.2 Jy for 3c279, the bandpass calibrator" (ALMA setup)
- flux scale uncertainty: ~10%  
  > "which gives an estimated systematic flux uncertainty of $\sim$10%" (ALMA setup)
- self calibration: Continuum: phase self-cal with 5 min solint, then amplitude+phase round; not applied to line channels  
  > "The solution interval chosen was 5 min, long enough to give over 30:1 signal to noise (2 deg accuracy) per antenna solution." (Self-calibration of continuum maps); "Hence, self-calibration correction to the line channels were not needed." (Self-calibration of continuum maps)

### Imaging

- task: Cotton-Schwab CLEAN in CASA; MEM deconvolved models with difmap residuals  
  > "we use Cotton-Schwab `CLEAN` in the `CASA` package." (Image synthesis)
- deconvolver: _not stated_
- weighting robust: Briggs, robustness 0  
  > "We use Briggs weighting with robustness parameter of zero." (Image synthesis)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: in the visibility domain  
  > "All the line data were processed with continuum subtraction in the visibility domain." (ALMA setup)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: Continuum 5.2e-4 Jy/beam, peak 0.38 Jy/beam  
  > "The final image has a peak of 0.38 Jy beam$^{-1}$ and an rms of $5.2~10^{-4}$ Jy beam$^{-1}$" (Self-calibration of continuum maps)

### Inherited from earlier work

- Non-parametric least-squares MEM modeling technique  
  > "we use a non-parametric least-squares modeling technique(cite: 2006ApJ...639..951C) with a regularizing entropy term" (Image synthesis) [from (cite: 2006ApJ...639..951C)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration procedure (pipeline vs manual)
- Cell size, image size, masks, clean threshold
- Line-free channels used for continuum
- Spectral aperture definitions and velocity ranges for the filaments
- MEM regularization parameters
- Dust opacity and gas-to-dust ratio used for the continuum filament mass

## Analysis recipe

1. **Calibrate, self-calibrate continuum and image**: Nominal calibration; continuum phase then amp+phase self-cal; CLEAN with Briggs robust 0; MEM deconvolution  
  > "We use Briggs weighting with robustness parameter of zero." (Image synthesis)
   - software: CASA, difmap
   - parameter: self-cal solint 5 min  
  > "The solution interval chosen was 5 min" (Self-calibration of continuum maps)
   - fitting: _not stated_
   - validation: Astrometry checked against centroid of Keplerian velocity field and near-IR image; error <0.05 arcsec  
  > "Overall, we estimate that any astrometric error is less than $\sim$0.05 arcsec." (Registration of ALMA images)
2. **Compare with Keplerian model**: LIME disk model filtered to uv-coverage and reconstructed like the data, to rule out beam elongation  
  > "We filtered the LIME predictions to match the $uv$-coverage of the data, and we reconstructed the resulting visibility in the same way as the observations." (Comparison disk models)
   - software: LIME
   - parameter: CO abundance 1e-4, HCO+ 1e-7, T=50(r/50AU)^-1/2 K, gap well-depth 1/10, total mass 0.1 Msun  
  > "$\zeta = 1/10$ is a fiducial well-depth. The total mass in this disk model is 0.1 M$_\odot$." (Comparison disk models)
   - fitting: _not stated_
   - validation: Beam elongation cannot mimic the HCO+ filaments  
  > "We conclude that beam elongation effects cannot mimick the HCO$^+$ filaments." (Comparison disk models)
3. **Estimate mass inflow rates**: Lower bound from HCO+ critical density, inflow velocity and filament section; upper bound from continuum mass and dynamical age  
  > "With an inflow velocity of 5 km s$^{-1}$, and a filament section of $\sim 0.25\times0.25$ arcsec$^2$, we obtain a mass inflow rate of $dM_i/dt > 7~10^{-9}~$M$_\odot$ yr$^{-1}$." (Estimates of mass inflow rates)
   - assumption: n_H2 ~1e6 cm-3; uniform standard dust-to-gas ratio; radial velocity <1 km/s; length 100 AU  
  > "so the filaments carry $\sim
10^{-4}$M$_\odot$ for a uniform and standard dust to gas ratio." (Estimates of mass inflow rates)
   - fitting: _not stated_
   - validation: Compared with observed stellar accretion rate 7e-8 Msun/yr  
  > "is bracketed within one order of magnitude by the above limits on the filament mass inflow rate" (Estimates of mass inflow rates)

## Software

- **CASA** : calibration and CLEAN imaging  
  > "Cotton-Schwab `CLEAN` in the `CASA` package" (Image synthesis)
- **difmap** : residuals added to MEM images  
  > "adding the residuals calculated using the `difmap` package" (Image synthesis)
- **LIME** : Keplerian comparison disk model  
  > "we have calculated a disk model using the LIME(cite: 2010A&A...523A..25B) package" (Comparison disk models)
- **MCFOST** : radiative transfer for SAM test of binary model  
  > "radiative transfer prediction obtained with the MCFOST(cite: 2006A&A...459..797P) package" (Physical considerations on close stellar companions)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mass inflow rate lower bound | 7e-9 | not stated | Msun/yr | 3 | $dM_i/dt > 7~10^{-9}~$M$_\odot$ yr$^{-1}$ |
| Mass inflow rate upper bound | 2e-7 | not stated | Msun/yr | 3 | $dM_i/dt <
2~10^{-7}~$M$_\odot$ yr$^{-1}$ |
| North-south continuum intensity ratio | 28 | 0.5 | dimensionless | 0 | observed north-south contrast of $28\pm0.5$ |
| Opening angle of filaments at star | 140 | 10 | deg | 0 | Both filaments subtend an angle of $\sim 140\pm10$ deg with the star at its vertex. |
| Peak continuum | 0.38 | not stated | Jy/beam | 1 | The final image has a peak of 0.38 Jy beam$^{-1}$ |

## Qualitative findings

- CO(3-2) emission peaks inside the cavity; HCO+ traces gap-crossing filaments; continuum is horseshoe-shaped  
  > "We find that the CO(3-2)-emitting gas peaks inside the cavity." (main text)

## Claim tuples

- H: Gas remains inside the dust gap | E: ALMA Band 7 CO(3-2) imaging | R: CO emission peaks inside the cavity with no counterpart to the continuum arc | F: Diffuse gas is present in the gap | **supported**
- H: Filaments are planet-induced accretion flows rather than outflows or an orthogonal disk | E: HCO+(4-3) kinematics, compared with outflow and orthogonal-disk arguments | R: Non-Keplerian, low-velocity filaments at systemic velocity | F: Interpreted as gap-crossing bridges | **partially**
- H: Filament flow can sustain stellar accretion | E: Mass inflow estimates from HCO+ and continuum | R: 7e-9 to 2e-7 Msun/yr vs 7e-8 observed | F: Sufficient to maintain accretion | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Central outflow, slow disk wind, and orthogonal inner disk rejected on kinematic grounds  
  > "The non-Keplerian HCO$^+$ is probably not consistent with a central outflow." (main text)
- Alternative: Differential stellar heating cannot explain the N-S contrast  
  > "Differential stellar heating, on its own, cannot account for the observed north-south contrast of $28\pm0.5$." (North-south asymmetry in the continuum)
- How they decided it was enough: _not stated_
- Limitation (authors): CO(3-2) is likely optically thick, so it does not trace density; embedded protoplanets would be obscured  
  > "CO(3-2) is likely optically thick, as reflected by its diffuse morphology" (main text)
- Caveat (inferred, ours): Inflow rates rest on order-of-magnitude assumptions (density, velocity, dust-to-gas)
- Caveat (inferred, ours): Inflow velocity not measured directly; radial velocity of filaments undetected
- Caveat (inferred, ours): Low-resolution Cycle 0 single-configuration data limit filament interpretation

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Full CASA scripts and imaging parameters
- Missing: MEM code details
- Data volume (inferred): ~10-50 GB (single Cycle 0 Band 7 execution)
- Score (inferred): 3/5, Single public dataset with partly described reduction, but imaging parameters and inflow assumptions are loosely specified.
- Rediscovery candidate: no, Key results are order-of-magnitude estimates with incomplete recipe.

## Links

- Method: (cite: 2006ApJ...639..951C) (MEM modeling technique)
- Companion: (cite: Casassus2012ApJ...754L..31C) (Near-IR images and hydrodynamical simulations of HD 142527)

## Checks

```json
{
 "quotes": 56,
 "quotes_ok": 56,
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
  "facts": 68,
  "stated": 40,
  "rate": 0.588
 },
 "evidence_ok": true
}
```
