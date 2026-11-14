# ALMA Band 6 high-resolution observations of the transitional disk around SY Chamaeleontis

`2023PASJ...75..424O` | Publications of the Astronomical Society of Japan 2023 | first author: Orihara, Ryuta | arXiv: 2302.05659 | DOI: 10.1093/pasj/psad009

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: What are the dust and gas structures of the transitional disk around SY Cha at high resolution, and what causes the velocity distortion inside the cavity?  
  > "Our high-resolution observations clearly revealed the inner cavity and the central point source for the first time." (abstract)
- Target **SY Cha**: coordinates _not stated_; z/distance 180.7 pc  
  > "distance to the star $d = 180.7$ pc ((cite: gaiaedr3))" (3.1.1 / Observations); "SY Cha is a T Tauri star with the mass of 0.78 $M_\odot$ ((cite: manara2017))." (Introduction); distance from Gaia EDR3  
  > "distance to the star $d = 180.7$ pc ((cite: gaiaedr3))" (3.1.1 / Observations); "SY Cha is a T Tauri star with the mass of 0.78 $M_\odot$ ((cite: manara2017))." (Introduction)

## Data provenance

- ALMA projects: 2018.1.00689.S
- bands: Band 6 (225 GHz continuum)  
  > "SY Cha was observed with ALMA in Band 6 during Cycle 6 (2018.1.00689S, PI: Muto)." (Observations and data reduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: two continuum SPWs of 2 GHz each, plus line-free data from three line SPWs  
  > "Two spectral windows for continuum observations with a bandwidth of 2 GHz, as well as three spectral windows for line observations" (Observations and data reduction)
- arrays: _not stated_
- configurations: Extended configuration (EC) 22 June 2019; compact configuration (CC) 19 August and 25 September 2019  
  > "The observations were conducted using an extended configuration (EC) on June 22, 2019, and by compact configuration (CC) on August 19 and September 25, 2019" (Observations and data reduction)
- baselines: _not stated_
- angular resolution: continuum beam 0.040"x0.022"; tapered 0.120"x0.083"; highest-resolution CO beam 0.128"x0.085"  
  > "we obtained a dust continuum image with a beam size of $0.040^{\prime\prime}\times0.022^{\prime\prime}$ and an RMS noise of $11.2\ \rm{\mu Jy/beam}$." (Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 11.2 uJy/beam (14.9 uJy/beam tapered)  
  > "we also prepared the tapered image with a beam size of $0.120^{\prime\prime}\times0.083^{\prime\prime}$ and an RMS noise of $14.9\ \rm{\mu Jy/beam}$." (Observations and data reduction)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Cycle 6, PI: Muto  
  > "SY Cha was observed with ALMA in Band 6 during Cycle 6 (2018.1.00689S, PI: Muto)." (Observations and data reduction)
- Line: 12CO J=2-1 (not stated)
- Line: 13CO J=2-1 (not stated)
- Line: C18O J=2-1 (not stated)
- External data: Stellar mass 0.78 Msun, accretion rate 3.89e-10 Msun/yr  
  > "SY Cha is a T Tauri star with the mass of 0.78 $M_\odot$ ((cite: manara2017))." (Introduction) [from (cite: manara2017)]
- External data: Distance 180.7 pc  
  > "distance to the star $d = 180.7$ pc ((cite: gaiaedr3))" (Observations and data reduction) [from (cite: gaiaedr3)]
- External data: 13CO and C18O abundance relative to H2  
  > "under the assumption of the abundance ratio of $\rm{}^{13}CO/H_2 = 1/67 \times 10^{-4}$ ((cite: Qi2011))" (3.3.2 Gas column density) [from (cite: Qi2011)]
- External data: Dust opacity kappa = 10 (nu/1e12 Hz)^beta cm2/g  
  > "((cite: beckwith1990)), we estimated the dust column density" (3.3.1 Dust Column Density) [from (cite: beckwith1990)]

## Processing

### Calibration

- pipeline or manual: CASA pipeline  
  > "We used the CASA pipeline (EC data: CASA 5.40-70 42254M, CC data: CASA 5.6.1-8 42866M) to calibrate the data" (Observations and data reduction)
- casa version: EC: CASA 5.40-70; CC: CASA 5.6.1-8; imaging CASA 6.4.4.31  
  > "The continuum image was reconstructed by multi-scale CLEAN ((cite: cornwell2008)) of CASA (version 6.4.4.31)" (Observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Phase-only self-cal on CC data; none on EC; final round combine spw,scan, solint inf on concatenated data  
  > "Since the EC observation did not detect the emission with sufficient sensitivity, no self-calibration was performed for it." (Observations and data reduction); "The final round of self-calibration in phase was then performed with `combine` “spw, scan” and `solint` “inf” for concatenated visibility." (Observations and data reduction)

### Imaging

- task: multi-scale CLEAN (CASA) for continuum; Hogbom CLEAN for line channel maps  
  > "Channel maps with a velocity width of 0.7 km/s were created by Hogbom CLEAN in a velocity range of $V_{\rm{LSRK}}= -4.3–12.5$ km/s." (Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: natural weighting for continuum; line maps density weight (file names indicate robust 0.5)  
  > "with natural weighting and `scales parameters` of \[0, ‘beam size’, ‘$2 \times$beam size’, ‘$3 \times$beam size’, ‘$4 \times$beam size’, ‘$5 \times$beam size’\]." (Observations and data reduction)
- uv taper: Gaussian taper 1.5 Mlambda on 12CO; 0.3 Mlambda on 13CO and C18O  
  > "we applied a Gaussian uvtaper of $1.5\ \rm{}M\lambda$ on the $\rm{}^{12}CO$, and $0.3\ \rm{}M\lambda$ on the $\rm{}^{13}CO$ and $\rm{}C^{18}O$." (Observations and data reduction)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: [0, 1,2,3,4,5 x beam size]  
  > "`scales parameters` of \[0, ‘beam size’, ‘$2 \times$beam size’, ‘$3 \times$beam size’, ‘$4 \times$beam size’, ‘$5 \times$beam size’\]" (Observations and data reduction)
- continuum subtraction: uvcontsub in visibility domain  
  > "Continuum components were subtracted from all line data in the visibility domain with the task `uvcontsub` in the CASA tools." (Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: EC and CC visibilities concatenated, phase centers aligned  
  > "Because $\rm{}^{12}CO$(2$-$1) emission was detected in the EC data, we performed imaging using the concatenated visibility." (Observations and data reduction)
- smoothing: _not stated_
- final beam: continuum 0.040"x0.022"; best CO 0.128"x0.085"  
  > "The beam size of the highest-resolution image is $0.128^{\prime\prime}\times0.085^{\prime\prime}$." (Observations and data reduction)
- final rms: 11.2 uJy/beam (continuum); 14.9 uJy/beam tapered  
  > "an RMS noise of $11.2\ \rm{\mu Jy/beam}$" (Observations and data reduction)

### Inherited from earlier work

- Phase-center alignment of execution blocks needed beyond proper-motion correction  
  > "It is known that only correcting for proper motion is sometimes inadequate and the alignment of ALMA data taken with different execution blocks is required ((cite: hashimoto2021))." (Observations and data reduction) [from (cite: hashimoto2021)]
- Disk assumed nearly axisymmetric for centering  
  > "taking advantage of the fact that the disk is nearly axisymmetric ((cite: kanagawa2021))" (Observations and data reduction) [from (cite: kanagawa2021)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and uvcontsub fit order
- Clean thresholds, masks, cell and image sizes
- Robust value for the line imaging text (only in file names)
- Self-calibration solint and number of iterations before the final round
- Priors and bounds for emcee fits
- Rest frequencies and spectral window setup details
- Stellar luminosity source details and dust beta justification

## Analysis recipe

1. **Calibrate, self-calibrate and align visibilities**: CASA pipeline; phase self-cal of CC; phase centers set by minimizing imaginary-part RMS over 300-1000 klambda  
  > "the phase centers of all observations were set at the position where the root mean square (RMS) of the imaginary part of the visibility was minimized" (Observations and data reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Image continuum and CO lines, make moment maps**: Multi-scale CLEAN continuum; Hogbom CLEAN cubes; bettermoments with Keplerian mask, 3 sigma clip  
  > "When creating moment 1 and 2 maps, the clipping levels were set to 3$\sigma$" (Observations and data reduction)
   - software: CASA, bettermoments, keplerian_mask
   - parameter: emitting surface height ratio 0.13  
  > "we assumed the height of the emitting surface relative to the radius to be 0.13" (Observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
3. **Determine ring center, PA and inclination**: Subtract 0.4 mJy point source, shift phase center to minimize imaginary-part RMS; minimize RMS of image minus its 90-degree rotation over PA and inclination  
  > "The minimum value of RMS was obtained for the deprojection with PA$=-15.4^\circ$ and Inc$=51.1^\circ$." (3.1.1)
   - software: CASA
   - fitting: grid search minimization  
  > "This was performed in the visibility domain by shifting the phase center and minimizing the imaginary part of the concatenated visibility; in this process, all visibilities with any spatial frequencies were used." (3.1.1 225GHz dust continuum)
   - validation: same result when rotating east or west  
  > "the same result was obtained when the image was rotated to the west" (3.1.1)
4. **Fit radial profiles and visibilities**: Three-Gaussian fits to major/minor axis profiles; visibility fit with two radially asymmetric Gaussians via Hankel transform  
  > "We determine eight parameters" (3.2)
   - software: emcee
   - fitting: emcee, 200 walkers, last 4000 steps shown  
  > "The plot shows the posterior sampling provided by the last 4000 steps of the 200 walkers chain." (Corner plots)
   - validation: _not stated_
5. **Derive dust and gas masses**: Optical depth from Planck function with T=415.8 (r/au)^-0.57 K from 12CO peak Tb; kappa=10(nu/1e12)^beta; LTE 13CO column density  
  > "T = 415.8\ \Big(\frac{r}{\rm{au}}\Big)^{-0.57}\ \rm{K}" (3.3.1)
   - assumption: beta = 1, kappa 2.25 cm2/g at 225 GHz; 13CO/H2 = 1/67e-4; CO/H2 = 1e-4  
  > "At 225 GHz, $\kappa_{\rm d}$ derived from equation (8) is 2.25 cm$^2$/g under the assumption that $\beta$ = 1." (3.3.1)
   - fitting: _not stated_
   - validation: C18O mass consistent with 13CO within factor 2  
  > "which is consistent with the gas mass estimated from $^{13}$CO emission within a factor of 2" (3.3.2)
6. **Test radial flow vs warp explanations**: Infall velocity v_los/sin i and infall rate; Blender shadow model of misaligned inner ring  
  > "Here, we investigate the shadow cast by the inner disk using a simplified model made with the 3D graphics software Blender." (5.2 Warp)
   - software: Blender
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.4.0-70 / 5.6.1-8 / 6.4.4.31: calibration, imaging, uvcontsub, phaseshift  
  > "The visibility data were reduced and calibrated using the Common Astronomy Software Applications (CASA) package" (Observations and data reduction)
- **emcee** : point-source Gaussian fit and visibility model fitting  
  > "The 2D Gaussian fitting of the point source on the image plane using `emcee`" (3.1.1)
- **bettermoments** : moment maps  
  > "We created the moment maps from each channel map using the `bettermoments` package" (Observations and data reduction)
- **keplerian_mask** : Keplerian masks for moment maps  
  > "generated with the `keplerian_mask` package" (Observations and data reduction)
- **Blender** : illumination model of misaligned rings  
  > "a simplified model made with the 3D graphics software Blender" (5.2 Warp)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum total flux density | 55.9 | not stated | mJy | 2 | The continuum emission has a total flux density of 55.9 mJy |
| Central point source flux | 0.4 | not stated | mJy | 2 | The emission consists of a ring and a central source of 0.4 mJy. |
| Disk position angle | -15.4 | not stated | deg | 3 | PA$=-15.4^\circ$ and Inc$=51.1^\circ$ |
| Disk inclination | 51.1 | not stated | deg | 3 | PA$=-15.4^\circ$ and Inc$=51.1^\circ$ |
| Total dust mass | ~1.0e-4 | lower limit | Msun | 5 | The total dust mass integrated over the entire disk was estimated to be $\sim 1.0 \times 10^{-4}~M_{\odot}$. |
| Total gas mass (13CO) | 2.2e-4 | not stated | Msun | 5 | The total gas mass is estimated to be $2.2\times 10^{-4}~M_{\odot}$. |
| Gas temperature fit | T = 415.8 (r/au)^-0.57 | not stated | K | 5 | T = 415.8\ \Big(\frac{r}{\rm{au}}\Big)^{-0.57}\ \rm{K} |
| Mass infall rate at ~30 au | ~1e-8 | not stated | Msun/yr | 6 | this gas surface density results in an estimate of the mass infall rate of $\sim 10^{-8}~M_{\odot}$/yr at $r\sim 30$ au |
| Central source size | 42 x 25 | ±0.96, ±0.37 | mas | 2 | this size is $42\pm 0.96$ mas $\times$ $25\pm 0.37$ mas |

## Qualitative findings

- Gas is present inside the dust cavity; velocity pattern distorted near star.  
  > "The observations showed that the gas is present inside the dust cavity." (abstract)

## Claim tuples

- H: Is there an inner disk in SY Cha? | E: High-resolution Band 6 continuum imaging | R: Unresolved 0.4 mJy central source | F: An inner dust disk/ring exists inside the cavity | **supported**
- H: Is the outer ring asymmetric? | E: Visibility-domain fit and residuals | R: Weak ~15% azimuthal asymmetry, east brighter | F: Weak asymmetry present | **supported**
- H: What causes the inner velocity distortion? | E: Moment/PV analysis, infall estimate, shadow model | R: Both radial flow and warp are possible; warp with inner inclination 70-90 deg fits | F: Origin inconclusive; warped inner disk plausible | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Foreground cloud absorption disfavored since all lines show similar spectra  
  > "since all the emission lines show similar spectra, this is most likely a result of the gas distribution in the disk rather than absorption by the foreground cloud." (3.1.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Dust scattering and beam dilution ignored; temperature is an upper limit so dust mass is a lower limit; CO depletion may raise gas mass by 10-100.  
  > "therefore the gas mass may be underestimated by a factor of 10$-$100." (3.3.2)
- Caveat (inferred, ours): Single-band dust mass with assumed beta=1 and upper-limit temperature
- Caveat (inferred, ours): Warp vs radial flow not discriminated; no radiative transfer modeling
- Caveat (inferred, ours): Central source unresolved; ring interpretation speculative

## Reproducibility

- Data public (paper): Project code given in acknowledgments; public status not explicitly stated  
  > "This study makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.00689.S." (Conclusions)
- Products in archive: _not stated_
- Missing: Self-cal solints
- Missing: Clean parameters and masks
- Missing: Line-free channels
- Missing: MCMC priors
- Data volume (inferred): ~100-300 GB raw
- Score (inferred): 3/5, Data identified and main steps described, but many imaging and fitting parameters are missing.
- Rediscovery candidate: no, Many parameters unstated and ALMA public availability not explicitly stated.

## Links

- Method: (cite: better2018) (moment maps)
- Method: (cite: teague2020) (Keplerian mask)
- Method: (cite: mangum2015) (column density equations)
- Companion: (cite: hashimoto2021) (execution block alignment)
- Companion: (cite: Kudo2018) (DM Tau inner ring analog)

## Checks

```json
{
 "quotes": 67,
 "quotes_ok": 67,
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
  "facts": 77,
  "stated": 47,
  "rate": 0.61
 },
 "evidence_ok": true
}
```
