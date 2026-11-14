# ALMA Reveals a Misaligned Inner Gas Disk inside the Large Cavity of a Transitional Disk

`2018ApJ...868L...3M` | The Astrophysical Journal Letters 2018 | first author: Mayama, Satoshi | arXiv: 1810.06941 | DOI: 10.3847/2041-8213/aae88b

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: Are the two shadows seen in scattered light cast by an inner disk highly misaligned with the outer disk, as tested via mm surface brightness dips and a twisted butterfly pattern in gas moment 1 maps?  
  > "Our goal is to test the hypothesis that the two shadows seen in scattered light imaging are cast by an inner disk highly misaligned with the outer disk" (Introduction)
- Target **2MASS J16042165-2130284 (J1604-2130)**: coordinates _not stated_; z/distance 150 pc  
  > "Recent GAIA DR2 reported that J1604-2130 is located at a distance of 150 pc." (Introduction); distance from GAIA DR2  
  > "Recent GAIA DR2 reported that J1604-2130 is located at a distance of 150 pc." (Introduction)

## Data provenance

- ALMA projects: 2015.1.000888.S
- bands: Band 7  
  > "J1604-2130 was observed in ALMA cycle 3 program 2015.1.000888.S (PI: E. Akiyama) in Band 7." (Observations and Data Reduction)
- frequencies and spectral setup: CO(3-2) window 234.375 MHz at 345.8 GHz; HCO+(4-3) window 468.750 MHz at 356.7 GHz; continuum 2 GHz windows at 344.0 and 355.5 GHz  
  > "The other windows with bandwidth of 2.00 GHz were configured to obtain the continuum emission centered at 344.0 GHz and 355.5 GHz (channel widths of 15.625 MHz)." (Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: extended and compact  
  > "The observations were conducted with the extended and compact configurations." (Observations and Data Reduction)
- baselines: extended 15.1 m-1.1 km; compact 15.3 m-460.0 m  
  > "The extended configuration array provided a maximum and minimum baseline length of 1.1 km and 15.1 m, respectively." (Observations and Data Reduction)
- angular resolution: ~0.2 arcsec  
  > "using ALMA observations with $\sim0$$''$2 angular resolution" (abstract)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 62.8 min extended, 31.4 min compact  
  > "The total integration time on source for target J1604-2130 was 62.8 minutes with extended configuration and 31.4 minutes with compact configuration." (Observations and Data Reduction)
- observing dates: 2016 March 10 (compact); August 2 and 15-16 (extended)  
  > "The observation with the compact configuration was performed on March 10, 2016 with 37 operative antennas" (Observations and Data Reduction)
- pi or archival as stated: PI: E. Akiyama  
  > "J1604-2130 was observed in ALMA cycle 3 program 2015.1.000888.S (PI: E. Akiyama) in Band 7." (Observations and Data Reduction)
- Line: CO 3-2 (345.8 GHz (window center))
- Line: HCO+ 4-3 (356.7 GHz (window center))
- Other facility **Gaia DR2**: distance and stellar position  
  > "For the stellar position, we used the GAIA DR2." (Observations and Data Reduction)
- External data: Subaru H-band scattered light dips at PA 85 and 255 deg  
  > "In NIR, similar dips are detected around a P.A. 85 and 255$^{\circ}$ at H-band" (Discussion) [from (cite: 2012ApJ...760L..26M)]
- External data: dust opacity 3 cm2/g at 0.87 mm  
  > "using an opacity for mm-sized particles, observed at a wavelength of 0.87mm = 3cm$^2$/g (cite: 2006ApJ...636.1114D)" (Discussion) [from (cite: 2006ApJ...636.1114D)]
- Simulation/model as data: Toy ring model (radius 0.58 arcsec, width 0.1 arcsec) with dips at PA 45 and 225 deg convolved with the beam  
  > "we simulate observations using a toy model of a ring disk(=0.$''$58 in radius). 0.$''$1 ring radial width is adopted as a fixed value." (Discussion)

## Processing

### Calibration

- pipeline or manual: Pipeline calibration by East Asian ARC as provided on archive  
  > "We followed the pipeline calibration provided by East Asian ALMA Regional Center and as provided for this data set on the ALMA archive." (Observations and Data Reduction)
- casa version: CASA 4.7 (extended), 4.5 (compact)  
  > "version 4.7 of the Common Astronomy Software Applications package (CASA) for extended configuration data and version 4.5 for compact configuration data" (Observations and Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1517-2422 or Titan  
  > "Absolute flux density was scaled using J1517-2422 or Titan." (Observations and Data Reduction)
- flux scale uncertainty: _not stated_
- self calibration: Continuum image as model, gain calibration repeated until rms converged; tables applied to CO and HCO+  
  > "gain calibration was repeated until the rms converged to a minimum" (Observations and Data Reduction)

### Imaging

- task: clean in CASA, all observations concatenated  
  > "We used the clean algorithm in CASA for imaging." (Observations and Data Reduction)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5  
  > "The Briggs weighting with robust of 0.5 was applied in both continuum and line imaging" (Observations and Data Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: compact and extended concatenated  
  > "we concatenate all the observations together for maximum uv-coverage" (Observations and Data Reduction)
- smoothing: _not stated_
- final beam: continuum 0.216x0.187 (PA 76.7); CO 0.229x0.194 (PA 77.8); HCO+ 0.218x0.188 (PA 72.1)  
  > "0.$''$216 $\times$ 0.$''$187 (PA=76.7 $^{\circ}$), 0.$''$229 $\times$ 0.$''$194 (PA=77.8 $^{\circ}$)" (Observations and Data Reduction)
- final rms: continuum 39 uJy/beam; CO channel 3.813 mJy/beam; HCO+ channel 3.385 mJy/beam  
  > "The achieved rms in the individual channel maps with approximately native channel width was 3.813 mJy beam$^{-1}$ for CO (3-2), and 3.385 mJy beam$^{-1}$ for HCO$^{+}$ (4-3)." (Observations and Data Reduction)

### Inherited from earlier work

- Method of using central velocity (4.6 km/s) to determine PA  
  > "This method to use the central velocity(4.6 km/s) for determination of the PA is described by (cite: 2018A&A...615L..10M)." (Results) [from (cite: 2018A&A...615L..10M)]
- Inner disk inclination from shadow geometry  
  > "If we adopt their method, we can address the different position angle between the inner disk and the line connecting the shadows." (Discussion) [from (cite: 2017A&A...604L..10M)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and continuum subtraction method
- clean mask, threshold, image size and cell size
- self-calibration solution intervals and number of iterations
- Moment map clipping thresholds
- Dust mass formula details and flux uncertainty
- Beam convolution details of toy model

## Analysis recipe

1. **Image continuum and lines**: Concatenate, self-calibrate on continuum, clean with Briggs weighting  
  > "The Briggs weighting with robust of 0.5 was applied in both continuum and line imaging" (Observations and Data Reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive disk PAs from moment 1**: Zero-velocity line along minor axis in CO moment 1; PA outer 80, inner 45 deg  
  > "we estimated the P.A. of J1604-2130 outer and inner disk to be 80 and 45$^{\circ}$, respectively." (Results)
   - fitting: _not stated_
   - validation: Compared with overlaid channel maps  
  > "we confirmed that the PAs of both inner and outer disks derived from CO (3-2) moment 1 map are perfectly consistent" (Results)
3. **Fit ring peak radii**: Ellipse fit to brightest peak coordinates in 10 deg PA increments, PA fixed  
  > "We first measured disk radial profiles in 10$^{\circ}$ position angle increments, and then extracted coordinates of the brightest peak area." (Elliptical fitting)
   - fitting: Trust Region Reflective algorithm  
  > "The Trust Region Reflective algorithm was performed." (Elliptical fitting)
   - validation: _not stated_
4. **Locate azimuthal dips**: Gaussian fit to local minima of azimuthal normalized profiles  
  > "By fitting the gaussian profile to the azimuthal profile, the best-fit parameter is found for the location of the local minimum to identify dip PA." (inner disk geometry and origins of dips)
   - fitting: Gaussian  
  > "By fitting the gaussian profile to the azimuthal profile, the best-fit parameter is found for the location of the local minimum to identify dip PA." (inner disk geometry and origins of dips)
   - validation: Toy ring model simulations for beam effect on dip depth and shift  
  > "beam elongation at the time of our observation (0.$''$216 $\times$ 0.187$''$ (PA=76.7 $^{\circ}$)) can produce ${\sim}$10${\%}$ of local decrements" (inner disk geometry and origins of dips)
5. **Dust mass lower limit**: Optically thin emission from 0.276 Jy  
  > "Assuming optically thin dust emission and using an opacity for mm-sized particles, observed at a wavelength of 0.87mm = 3cm$^2$/g" (Discussion)
   - assumption: minimum disk temperature 20 K, kappa 3 cm2/g, d=150 pc  
  > "we assume a minimum disk temperature of 20K" (Discussion)
   - fitting: _not stated_
   - validation: Compared with SMA dust mass 0.1 MJup  
  > "derived that J1604-2130 has a dust mass of 0.1 $M$$_\mathrm{Jup}$ by their SMA observation" (Discussion)

## Software

- **CASA** 4.7 / 4.5: calibration, clean imaging, self-calibration  
  > "We used the clean algorithm in CASA for imaging." (Observations and Data Reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum peak radius major/minor | 583 / 576 | ±3 | mas | 3 | for the continuum, peak radii of major and minor axis are $583 \pm 3$ and $576 \pm 3$ \[mas\], respectively |
| CO(3-2) peak radius major/minor | 385 / 375 | ±3 | mas | 3 | For CO (3-2), peak radii of major and minor axis are $385 \pm 3$ and $375\pm 3$\[mas\], respectively. |
| Outer / inner disk PA | 80 / 45 | not stated | deg | 2 | we estimated the P.A. of J1604-2130 outer and inner disk to be 80 and 45$^{\circ}$, respectively. |
| Integrated continuum flux | 0.276 | not stated | Jy | 5 | giving an integrated emission of 0.276 Jy |
| Dust mass lower limit | 0.21 | not stated | M_Jup | 5 | resulting in a derived dust mass lower limit of M$_{dust}$=0.21 M$_\mathrm{Jup}$ |

## Qualitative findings

- Twisted butterfly moment 1 pattern in CO(3-2) indicates misaligned inner and outer disks; dips seen in continuum and gas.  
  > "A twisted butterfly pattern is found in the moment 1 map of CO (3-2) emission line towards the center" (abstract)

## Claim tuples

- H: Shadows are cast by a misaligned inner disk | E: Search for dips and twisted moment 1 in ALMA Band 7 data | R: Inner gas component, twisted moment 1 and two dips found | F: Supports misaligned-inner-disk origin | **supported**
- H: Inner disk inclination sign | E: Compare NIR shadow line with Min et al. models | R: Close to -45 deg | F: Inclination near -45 rather than 45 deg | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Infall as alternative origin of twist: no significant evidence of inflow in cavity  
  > "our new ALMA data detected no significant evidence of inflow penetrating the cavity" (Comparisons with previous observations)
- How they decided it was enough: _not stated_
- Limitation (authors): Single epoch and resolution insufficient to resolve obscuring structures causing variability  
  > "our new observation is at one epoch and did not have good enough resolution to resolve any obscuring structures on inner disk" (Comparisons with previous observations)
- Caveat (inferred, ours): Dip positions affected by beam; real vs. beam-induced dips indistinguishable
- Caveat (inferred, ours): Inner disk only marginally resolved; PA of 45 deg is uncertain
- Caveat (inferred, ours): No uncertainties on PAs or dust mass

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: Pipeline calibration as provided on ALMA archive  
  > "as provided for this data set on the ALMA archive" (Observations and Data Reduction)
- Missing: Clean parameters, masks, self-cal intervals
- Missing: Moment map clipping
- Missing: Dip-fitting details
- Data volume (inferred): ~50-100 GB raw for several execution blocks
- Score (inferred): 3/5, Public data and standard steps but many imaging and fitting details missing.
- Rediscovery candidate: no, Key results (inner disk twist, dips) are largely qualitative and the recipe lacks key parameters.

## Links

- Method: (cite: 2017A&A...604L..10M) (Inner disk inclination from shadow geometry)
- Method: (cite: 2018A&A...615L..10M) (PA from central velocity)
- Companion: (cite: 2017ApJ...836..201D) (Cycle 2 ALMA observation of the same disk)
- Companion: (cite: 2012ApJ...760L..26M) (Subaru scattered light shadows)
- Related: HD 142527 shadows
- Related: Subaru NIR imaging

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
 "codes_not_in_obscore": [
  "2015.1.000888.S"
 ],
 "obscore_codes_not_in_card": [
  "2015.1.00888.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 42,
  "rate": 0.609
 },
 "evidence_ok": true
}
```
