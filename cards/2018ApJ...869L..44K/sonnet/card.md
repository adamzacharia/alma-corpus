# The Disk Substructures at High Angular Resolution Project (DSHARP). IV. Characterizing Substructures and Interactions in Disks around Multiple Star Systems

`2018ApJ...869L..44K` | The Astrophysical Journal Letters 2018 | first author: Kurtovic, Nicolás T. | arXiv: 1812.04536 | DOI: 10.3847/2041-8213/aaf746

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: protoplanetary_disks, star_formation
- Question: What substructures and interaction signatures appear in the dust continuum and 12CO emission of the multiple systems AS 205 and HT Lup at ~5 au resolution?  
  > "To characterize the substructures induced in protoplanetary disks by the interaction between stars in multiple systems, we study the $1.25\,$mm continuum and the $^{12}$CO$(J=2-1)$ spectral line emission" (abstract)
- Target **AS 205**: coordinates RA 16h11m31.352s, Dec -18d38m26.233s (J2000)  
  > "AS 205 is a multiple stellar system located at a distance of $127 \pm 2\,$pc (cite: Gaia2018)" (2.1 AS 205); "The final images are centered at (J2000) RA = 16h 11m 31.352s, Dec = $-18$d 38m 26.233s for AS 205" (Observations); z/distance 127 ± 2 pc  
  > "AS 205 is a multiple stellar system located at a distance of $127 \pm 2\,$pc (cite: Gaia2018)" (2.1 AS 205); "The final images are centered at (J2000) RA = 16h 11m 31.352s, Dec = $-18$d 38m 26.233s for AS 205" (Observations); distance from Gaia DR2  
  > "AS 205 is a multiple stellar system located at a distance of $127 \pm 2\,$pc (cite: Gaia2018)" (2.1 AS 205); "The final images are centered at (J2000) RA = 16h 11m 31.352s, Dec = $-18$d 38m 26.233s for AS 205" (Observations)
- Target **HT Lup**: coordinates RA 15h45m12.847s, Dec -34d17m31.01s (J2000)  
  > "HT Lup is a triple stellar system located at a distance of $154 \pm 2\,$pc (cite: Gaia2018)" (2.2 HT Lup); "for HT Lup the center is at RA = 15h 45m 12.847s, Dec = $-34$d 17m 31.01s" (Observations); z/distance 154 ± 2 pc  
  > "HT Lup is a triple stellar system located at a distance of $154 \pm 2\,$pc (cite: Gaia2018)" (2.2 HT Lup); "for HT Lup the center is at RA = 15h 45m 12.847s, Dec = $-34$d 17m 31.01s" (Observations); distance from Gaia DR2  
  > "HT Lup is a triple stellar system located at a distance of $154 \pm 2\,$pc (cite: Gaia2018)" (2.2 HT Lup); "for HT Lup the center is at RA = 15h 45m 12.847s, Dec = $-34$d 17m 31.01s" (Observations)

## Data provenance

- ALMA projects: 2011.0.00531.S
- bands: Band 6 (1.3 mm)  
  > "observed in band 6 (1.3mm) as part of DSHARP" (Conclusions)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~5 au (continuum beams 37x24 mas AS 205, 37x32 mas HT Lup)  
  > "with a beam size of $37\times 24\,$mas ($4.7\times 3.0\,$au)" (Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: DSHARP large program plus Cycle 0 archival data for AS 205  
  > "For AS 205, we also include band 6 archival data from ALMA Cycle 0" (Observations)
- Line: 12CO J=2-1 (not stated)
- Other facility **Gaia DR2**: Distances and parallaxes, proper motion  
  > "The distances to each source in the AS 205 system used here were calculated from Gaia DR2" (2.1 AS 205)
- External data: Stellar masses of AS 205 S components (0.74 and 0.54 Msun)  
  > "masses of $0.74$ and $0.54\,M_\odot$ (cite: Eisner2005)" (2.1 AS 205) [from (cite: Eisner2005)]
- External data: Earlier HT Lup A-B separations (0.107 arcsec in 1997, 0.126 arcsec in 2004)  
  > "(cite: Ghez1997) find that the angular separation between HT Lup A and B is $0\ensuremath{''}{107} \pm 0\ensuremath{''}{007}$ in 1997" (6.1 Ruling out chance alignment) [from (cite: Ghez1997); (cite: Correia2006)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean in CASA 5.1  
  > "we generated continuum images using the `tclean` task in CASA 5.1 (cite: mcmullin07)" (Observations)
- deconvolver: _not stated_
- weighting robust: AS 205 continuum robust 0.5 (and -0.5 for compact AS 205 S); AS 205 CO robust 1.0; HT Lup continuum 0.5; HT Lup CO 1.5  
  > "For AS 205 we chose a robust parameter of $0.5$" (Observations); "The CO images used a robust parameter of 1.5" (Observations)
- uv taper: AS 205 continuum 40x0 mas PA=90 deg (AS 205 N); HT Lup CO 20x5 mas PA=150 deg  
  > "we also created an image with uvtaper of $40\times0\,$mas and PA=$90^\circ$" (Observations)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: HT Lup CO excluded baselines shorter than 150 m  
  > "we excluded baselines smaller than $150\,$m" (Observations)
- smoothing: _not stated_
- final beam: AS 205 CO 90x67 mas; HT Lup CO 53x50 mas  
  > "resulting in a beam of $53\times50\,$mas ($\approx 8\,$au)" (Observations)
- final rms: AS 205 continuum 16 uJy/beam; HT Lup continuum 14.1 uJy/beam; CO 1.42 and 1.2 mJy/beam per channel  
  > "The first continuum image has an SNR of 390 with an rms of $16\,\mu$Jy/beam" (Observations)

### Inherited from earlier work

- Data acquisition and calibration  
  > "A detailed description of the data acquisition and calibration can be found in (cite: Andrews2018)." (Observations) [from (cite: Andrews2018)]
- Astrometric alignment and CO map procedure  
  > "following the procedure in (cite: Andrews2018)" (Observations) [from (cite: Andrews2018)]
- HT Lup CO map produced following DSHARP procedure  
  > "A map of the CO emission was obtained following the DSHARP procedure (cite: Andrews2018)." (6 Gas emission in the HT Lup system) [from (cite: Andrews2018)]

### Not stated but needed to reproduce (our reading)

- Self-calibration solints and number of rounds (in Andrews2018)
- Line-free channels and continuum subtraction method for CO
- Image size, cell size, masks, clean threshold
- Which DSHARP execution blocks and configurations were used
- Spectral resolution of CO cubes
- Moment map parameters beyond 3 sigma clipping

## Analysis recipe

1. **Fit disk geometry**: 2D Gaussian fit to each disk to get inclination and PA  
  > "we fitted a 2D Gaussian model to each disk using the CASA task `imfit`" (4.1 Continuum AS 205)
   - software: CASA imfit
   - parameter: AS 205 N fit used image excluding longest baselines, beam 270x227 mas  
  > "we used the continuum image generated while excluding the longest baseline dataset, with a beamsize of $270\times227\,$mas" (4.1 Continuum AS 205)
   - fitting: _not stated_
   - validation: Ring fit geometry agrees with Gaussian values  
  > "the ring inclination and position angle are also in good agreement with the values obtained with the 2D Gaussian fit to the image" (4.1.2 A ring in AS 205 South)
2. **Fit spiral arms**: Subtract azimuthally averaged radial profile (AS 205 N) or unsharp mask (HT Lup A), trace arm maxima, fit logarithmic and Archimedean spirals  
  > "After subtracting this radial profile from the continuum image, a clear spiral structure is revealed" (4.1.1 Spirals in AS 205 North)
   - software: emcee
   - parameter: 250 walkers, burn-in 1000 and 500 steps, 1500 sampling steps; 6 free parameters  
  > "we use 250 walkers with two consecutive burning stages of 1000 and 500 steps, and then 1500 steps to sample the parameter space" (4.1.1 Spirals in AS 205 North)
   - parameter: HT Lup A unsharp mask: 66 mas FWHM Gaussian, weight 0.95  
  > "We first convolve the image with a Gaussian of $66\,$mas FWHM and then subtract it from the original continuum image, multiplying by a weighting factor of 0.95." (4.4.1 Spirals in HT Lup A)
   - assumption: Both spirals share same center and geometry  
  > "The NW and SW spirals are assumed to share the same center (located at the peak of emission)" (4.1.1 Spirals in AS 205 North)
   - fitting: emcee MCMC with flat priors  
  > "A flat prior probability was used for all parameters." (4.1.1 Spirals in AS 205 North)
   - validation: Reduced chi2 comparison; Archimedean 1.5x better; offset-center test gives similar chi2  
  > "We note that the reduced $\chi^2$ in the Archimedean spiral model is factor of $1.5$ better than in the logarithmic model." (4.1.1 Spirals in AS 205 North)
3. **Fit AS 205 S ring**: Ring maxima every 18 deg fitted with ellipse via MCMC  
  > "The points were then fitted with an ellipse using a MCMC routine based on `emcee`" (4.1.2 A ring in AS 205 South)
   - software: emcee
   - fitting: emcee, center, axes and PA free  
  > "letting the center, major axis, minor axis, and position angle free to vary" (4.1.2 A ring in AS 205 South)
   - validation: _not stated_
4. **Analyze CO kinematics**: Moment 0 and 1 maps clipped at 3 sigma; channel maps inspected for tidal features and rotation sense  
  > "intensity-weighted velocity field (moment 1) computed from the CO datacube, clipping at $3\sigma$" (4.2 Gas emission in the AS 205 system)
   - software: CASA
   - assumption: Trailing spirals imply counter-clockwise rotation of HT Lup A  
  > "assume that the spiral arms in HT Lup A are trailing (i.e. the disk rotation is counter-clockwise)" (6.4 Disk misalignment)
   - fitting: _not stated_
   - validation: Compared with hydrodynamic fly-by simulations in literature  
  > "For example, the 3D hydrodynamic fly-by simulations from (cite: Dai2015) exhibit several of the non-Keplerian features present in the AS205 system, such as the gas bridge between the disks" (A fly-by in AS 205 system?)

## Software

- **CASA** 5.1: tclean imaging and imfit Gaussian fitting  
  > "we generated continuum images using the `tclean` task in CASA 5.1" (Observations)
- **emcee** : MCMC fits of spirals and ring  
  > "we use an MCMC routine based on `emcee` (cite: emcee2013)" (4.1.1 Spirals in AS 205 North)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| AS 205 N spiral pitch angle (log) | 13.9 (NW), 13.7 (SE) | ±0.3 | deg | 2 | ${13.9^\circ}_{-0.3}^{+0.3}$ |
| AS 205 S ring radius | 33.8 | +0.3/-0.4 | au | 3 | ${33.8}_{-0.4}^{+0.3}$ |
| HT Lup A spiral pitch angle (log) | 4.15 (N), 3.69 (S) | +1.4/-1.7 | deg | 2 | ${4.15^\circ}_{-1.7}^{+1.4}$ |
| AS 205 N-S projected separation | 168 | not stated | au | 0 | or $168\,$au in projected separation |
| HT Lup A-B disk misalignment | 91 or 164 | not stated | deg | 1 | either $91^\circ$ or $164^\circ$ for HT Lup A and B |
| HT Lup A-B separation (2017) | 0.161 | 0.003 | arcsec | 0 | we constrain a separation of $0\ensuremath{''}{161} \pm 0\ensuremath{''}{003}$ with data from 2017 |
| HT Lup B deconvolved size | 31 | 2 | mas | 1 | deconvolved FWHM size of $31\pm2\,$mas |

## Qualitative findings

- AS 205 CO shows tidal-interaction features consistent with a fly-by.  
  > "possible evidence of a recent close encounter between the disks in the AS 205 system" (abstract)

## Claim tuples

- H: Do dust spirals exist in the primaries of AS 205 and HT Lup? | E: Radial-profile subtraction or unsharp masking and spiral model fits | R: Two-armed spirals with pitch angles ~14 deg (AS 205 N) and ~4 deg (HT Lup A) | F: Symmetric spirals detected; Archimedean preferred for AS 205 N | **supported**
- H: Was AS 205 shaped by a recent fly-by? | E: CO moment and channel maps compared to simulations | R: Bridge, arcs, non-Keplerian motions | F: Features consistent with prograde fly-by, constrained by the unperturbed ring | **partially**
- H: Are HT Lup A and B misaligned? | E: Gaussian-fit geometry and CO kinematics | R: Apparent counter-rotation | F: Degenerate: near perpendicular or near parallel counter-rotating | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Chance alignment rejected using the measured separation change over 20 years.  
  > "We therefore conclude that most likely, the HT Lup A and B stars as well as the AS 205 N and S components are not aligned by chance." (6.1 Ruling out chance alignment)
- How they decided it was enough: _not stated_
- Limitation (authors): HT Lup CO heavily contaminated by cloud emission.  
  > "the CO was found to be highly contaminated by extended cloud emission and foreground absorption" (4.5)
- Caveat (inferred, ours): Spiral tracing and unsharp-mask parameters are subjective
- Caveat (inferred, ours): Pitch-angle errors depend on the assumed geometry
- Caveat (inferred, ours): Misalignment degeneracy is unresolved
- Caveat (inferred, ours): AS 205 S distance assumed equal to N

## Reproducibility

- Data public (paper): Cycle 0 archival data cited; DSHARP is a large program  
  > "we also include band 6 archival data from ALMA Cycle 0" (Observations)
- Products in archive: _not stated_
- Missing: DSHARP self-calibration details
- Missing: Image and cell sizes, masks
- Missing: Spiral point extraction code
- Data volume (inferred): ~100-300 GB raw for the DSHARP execution blocks
- Score (inferred): 3/5, Imaging parameters are partly given, but calibration and self-calibration are deferred to Andrews2018.
- Rediscovery candidate: no, Calibration is deferred to another paper and spiral tracing is not fully specified.

## Links

- Method: (cite: Andrews2018) (DSHARP data acquisition, calibration, and CO procedure)
- Method: (cite: Huang2018b) (Spirals in other DSHARP targets)
- Companion: (cite: Salyk2014) (Earlier Cycle 0 AS 205 data)
- Related: DSHARP (2016.1.00484.L)

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
 "obscore_codes_not_in_card": [
  "2016.1.00484.L"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 42,
  "rate": 0.568
 },
 "evidence_ok": true
}
```
