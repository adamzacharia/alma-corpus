# ALMA Observations of ρ-Oph 102: Grain Growth and Molecular Gas in the Disk around a Young Brown Dwarf

`2012ApJ...761L..20R` | The Astrophysical Journal Letters 2012 | first author: Ricci, L. | arXiv: 1211.6743 | DOI: 10.1088/2041-8205/761/2/L20

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: Do disks around young brown dwarfs contain mm-sized grains and gas, as measured from the mm spectral index and CO emission for rho-Oph 102?  
  > "In this Letter we report on our ALMA observations, which were designed to derive a solid estimate of the mm spectral index to constrain the dust properties." (1 Introduction)
- Target **rho-Oph 102**: coordinates _not stated_; z/distance 130 pc  
  > "a distance of 130 pc for the $\rho$-Oph SFR (cite: Wilking:2008; Lombardi:2008)" (2.2 Continuum maps); distance from rho-Oph SFR distance (Wilking:2008; Lombardi:2008)  
  > "a distance of 130 pc for the $\rho$-Oph SFR (cite: Wilking:2008; Lombardi:2008)" (2.2 Continuum maps)

## Data provenance

- ALMA projects: 2011.0.00259.S
- bands: Band 7 (~345 GHz) and Band 3 (~100 GHz), ALMA Cycle 0 Early Science  
  > "We observed $\rho$–Oph 102 using ALMA Early Science in Cycle 0 at Band 7 and 3 (about 345 and 100 GHz, respectively)." (2.1 Observations and data reduction)
- frequencies and spectral setup: four spectral windows of 1.875 GHz, 0.488 MHz channels; Band 7 centered 331.103, 332.998, 343.103, 344.998 GHz; Band 3 86.1021, 87.9976, 98.103, 99.999 GHz  
  > "Spectral windows were centered at 331.103, 332.998, 343.103, 344.998 GHz for Band 7 observations and 86.1021, 87.9976, 98.103, 99.999 GHz for Band 3." (2.1 Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: Band 7: Compact (15 antennas, 2011 Nov 3) and Extended (16 antennas, 2012 May 23); Band 3: Extended (16 antennas, 2012 May 8)  
  > "Observations in Band 7 were performed using 15 antennas in the Compact array configuration on November 3, 2011, and 16 antennas in the Extended array configuration on May 23, 2012" (2.1 Observations and data reduction)
- baselines: Band 7: shadowing limit to ~400 m; Band 3: ~35 to ~402 m  
  > "Observations in Band 3 were conducted with 16 antennas in the Extended configuration on May 8, 2012 (projected baseline lengths from $\sim$35 to $\sim$402 m)." (2.1 Observations and data reduction)
- angular resolution: ~0.6'' at 0.89 mm  
  > "Considering our angular resolution of $\sim 0.6''$ at 0.89 mm" (2.2 Continuum maps)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: ~15 min Band 7, ~30 min Band 3  
  > "The total integration times on $\rho$–Oph 102 were approximately 15 and 30 minutes in Band 7 and 3, respectively." (2.1 Observations and data reduction)
- observing dates: 2011-11-03, 2012-05-23 (Band 7); 2012-05-08 (Band 3)  
  > "Observations in Band 7 were performed using 15 antennas in the Compact array configuration on November 3, 2011" (2.1 Observations and data reduction)
- pi or archival as stated: _not stated_
- Line: CO J=3-2 (not stated)
- Other facility **SMA**: Earlier 1.3 mm flux and CO(2-1) map (Phan-Bao 2008) used for comparison  
  > "Using observations with the Submillimeter array (cite: Ho:2004) (cite: Phan-Bao:2008) reported a low signal-to-noise flux density of $7 \pm 3$ mJy at about 1.3 mm." (2.2 Continuum maps)
- External data: SMA 1.3 mm flux density 7±3 mJy and CO(2-1) map  
  > "reported a low signal-to-noise flux density of $7 \pm 3$ mJy at about 1.3 mm." (2.2 Continuum maps) [from (cite: Phan-Bao:2008)]
- External data: Dust opacity kappa(0.89 mm) for beta 0.4-0.6  
  > "correspond to dust opacities values of $\kappa^{\rm{dust}}_{\nu,\lambda=0.89\rm{mm}}= 1.5 - 4.5$ cm$^2/$g (cite: Ricci:2010a)" (3.1 Disk mass and size) [from (cite: Ricci:2010a)]
- External data: Visual extinction A_V ~ 3  
  > "the visual extinction of the $\rho$-Oph 102 photosphere, i.e. $A_{V} \approx 3$ (cite: Natta:2002)" (3 Discussion) [from (cite: Natta:2002)]

## Processing

### Calibration

- pipeline or manual: CASA used for reduction; details not stated  
  > "The interferometric visibility data were reduced using the CASA package (cite: McMullin:2007)." (2.1 Observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Neptune and Titan; Butler-JPL-Horizons 2010 models  
  > "The flux scale was tied to the Butler-JPL-Horizons 2010 models of Neptune and Titan, resulting in an accuracy of $\sim10\%$." (2.1 Observations and data reduction)
- flux scale uncertainty: ~10%  
  > "resulting in an accuracy of $\sim10\%$" (2.1 Observations and data reduction)
- self calibration: _not stated_

### Imaging

- task: CASA imaging; continuum with natural weighting using all line-free channels  
  > "For each band, a continuum map was produced using natural weighting and combining all the channels without line emission." (2.1 Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: CO: natural weighting plus Gaussian taper (all data); robust weighting for baselines >~60 kλ (robust value not stated)  
  > "we also imaged the data from baselines exceeding $\sim60$ k$\lambda$" (2.1 Observations and data reduction)
- uv taper: Gaussian taper for extended CO map (value not stated)  
  > "we first used all the data, natural weighting and a gaussian taper of the visibilities" (2.1 Observations and data reduction)
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

- Unresolved-disk photometry modeling procedure, adapted for BDs  
  > "Our analysis of the unresolved disk photometry follows the procedure outlined in (cite: Testi:2001), adapted for the case of young BDs." (3 Discussion) [from (cite: Testi:2001)]
- Two-layer flared disk model  
  > "we model the mm continuum emission using a two-layer (surface$+$midplane) model of a flared disk heated by the radiation of the central BD (cite: Chiang:1997; Dullemond:2001)." (3 Discussion) [from (cite: Chiang:1997; Dullemond:2001)]
- Sub-stellar photospheric properties and dust model described in Figure 4 caption (not in text)  
  > "The adopted sub-stellar photospheric properties of $\rho$-Oph 102 and the dust model are described in the caption of Figure [4](#fig:models)." (3 Discussion) [from Figure 4 caption]

### Not stated but needed to reproduce (our reading)

- CASA version and pipeline/manual calibration details
- robust value, taper size, cell size, image size, clean threshold and masks
- channel ranges used for CO moment maps and line-free channels
- dust model (composition, grain size distribution) and stellar parameters from the Fig. 4 caption
- gas-to-dust and disk model grid details (radius range, temperature, outer radius sampling)
- how flux densities were measured (fit or aperture)

## Analysis recipe

1. **image continuum and measure flux densities and spectral index**: Natural-weighted continuum maps in each band; flux densities measured; spectral index from the two fluxes  
  > "We measured flux densities of $4.10 \pm 0.22$ mJy at 0.89 mm and of $0.22 \pm 0.03$ mJy at 3.2 mm." (2.2 Continuum maps)
   - software: CASA
   - fitting: _not stated_
   - validation: rms noise consistent with theoretical expectations  
  > "The obtained rms-noise levels are consistent with the theoretical expectations given the on-source integration times." (2.2 Continuum maps)
2. **test whether the continuum is resolved**: Inspect visibility amplitude vs projected baseline; no decrease implies unresolved, size upper limit ~40 AU  
  > "We conclude that our observations did not spatially resolve the disk continuum emission." (2.2 Continuum maps)
   - assumption: distance 130 pc  
  > "a distance of 130 pc for the $\rho$-Oph SFR" (2.2 Continuum maps)
   - fitting: _not stated_
   - validation: _not stated_
3. **image CO(3-2) and measure compact emission**: Imaged with >~60 kλ baselines to filter extended emission; integrated flux and velocity field  
  > "The disk is detected at a $> 10\sigma$ level, with a velocity-integrated total flux of about $530 \pm 45$ mJy$\cdot$km/s." (2.3 CO molecular gas map)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
4. **model dust emission to get disk mass, radius and beta**: Two-layer flared disk model compared to the fluxes for varying radius and beta  
  > "Disk models with radii larger than $\mathbin{\lower 3pt\hbox
     {$\rlap{\raise 5pt\hbox{$\char'076$}}\mathchar"7218$}}~5$ AU can reproduce the data only if the spectral index of the dust opacity $\beta$" (3.1 Disk mass and size)
   - assumption: Sigma ∝ r^-1; inclination 70 deg; gas-to-dust ratio 100  
  > "We assume in the following an inclination of 70 degrees; however, our results do not depend critically on this choice." (3 Discussion)
   - fitting: not stated (models compared to data, no formal fit)  
  > "The main results of our modeling can be derived from Figure [4](#fig:models), which shows the ALMA data overlaid with the predictions from the disk models presented above." (Disk mass and size)
   - validation: CO brightness temperature argument gives lower limit ~15 AU on radius  
  > "this argument sets a lower-limit of about 15 AU for the disk radius." (3.1 Disk mass and size)

## Software

- **CASA** : Data reduction and imaging  
  > "Imaging of the calibrated visibilities was done in CASA." (2.1 Observations and data reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Flux density 0.89 mm | 4.10 | 0.22 | mJy | 1 | We measured flux densities of $4.10 \pm 0.22$ mJy at 0.89 mm |
| Flux density 3.2 mm | 0.22 | 0.03 | mJy | 1 | of $0.22 \pm 0.03$ mJy at 3.2 mm |
| Spectral index alpha(0.89-3.2mm) | 2.29 | 0.16 | dimensionless | 1 | $\alpha_{\rm{0.89-3.2mm}} = 2.29 \pm 0.16$ |
| CO(3-2) velocity-integrated flux | 530 | 45 | mJy km/s | 3 | velocity-integrated total flux of about $530 \pm 45$ mJy$\cdot$km/s |
| Dust disk radius upper limit | ~40 | not stated | AU | 2 | derive an upper limit on the radius of the dusty disk of $\sim 40$ AU |
| Dust mass | 2-6e-6 | not stated | Msun | 4 | we derive estimates for the dust mass of $\sim 2 - 6\cdot 10^{-6}~M_{\odot}$ |
| beta | 0.4-0.6 | not stated | dimensionless | 4 | i.e. $\beta \approx 0.4 - 0.6$ |
| Disk mass fraction of BD+disk | 0.3-1 | not stated | % | 4 | These values correspond to a disk which contains $\sim$0.3–1% of the mass of the BD$+$disk system |

## Qualitative findings

- CO emission detected from the disk, tentative velocity gradient ~1 km/s consistent with Keplerian rotation  
  > "We tentatively find the presence of a velocity gradient along the disk spanning a range of radial velocities of $\approx 1$ km/s." (2.3 CO molecular gas map)

## Claim tuples

- H: Do BD disks contain mm-sized grains? | E: Two-band continuum spectral index plus disk modeling | R: alpha=2.29±0.16; beta~0.4-0.6 for disks >5 AU | F: mm-sized grains exist in the BD disk outer regions, challenging dust evolution models | **supported**
- H: Is the BD disk gas-rich with similar relative mass as T Tauri disks? | E: CO(3-2) mapping and dust mass with gas-to-dust 100 | R: CO detected >10σ; disk mass 0.3-1% of BD | F: Gas-rich disk with typical relative mass | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Small (<5 AU) optically thick disk rejected since it would need gas temperature >400 K  
  > "This would correspond to a gas temperature $>$ 400 K, which is much higher than expected for a BD disk." (3.1 Disk mass and size)
- How they decided it was enough: _not stated_
- Limitation (authors): Disk unresolved so radius and inclination poorly constrained; CO extended emission affected by missing flux  
  > "Since our observations did not allow us to spatially resolve the dust emission of the disk, we could not strongly constrain the disk radius and inclination." (3 Discussion)
- Caveat (inferred, ours): Only two continuum points; beta depends on assumed disk model and opacity
- Caveat (inferred, ours): Assumed gas-to-dust 100 and CO optically thick/temperature argument are uncertain
- Caveat (inferred, ours): Single object

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Disk model code and parameters (Fig. 4 caption)
- Missing: CASA version and imaging parameters
- Data volume (inferred): ~10-30 GB raw
- Score (inferred): 4/5, Flux measurements are simple to redo from archive data, but the disk modeling and imaging parameters are not fully specified.
- Rediscovery candidate: no, Imaging details and model setup are incomplete, so the modeling results cannot be redone from the text alone.

## Links

- Method: (cite: Testi:2001) (unresolved disk photometry modeling procedure)
- Companion: (cite: Phan-Bao:2008) (previous SMA CO(2-1) and 1.3 mm observations)

## Checks

```json
{
 "quotes": 49,
 "quotes_ok": 49,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 36,
  "rate": 0.529
 },
 "evidence_ok": true
}
```
