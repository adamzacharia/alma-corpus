# The nascent wind of AGB star R doradus: evidence for a recent episode of enhanced mass loss

`2019MNRAS.490.3329N` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Nhung, P. T. | arXiv: 1908.03311 | DOI: 10.1093/mnras/stz2675

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: evolved_stars
- Question: What are the morpho-kinematics of the nascent slow wind of AGB star R Dor (20-100 au) from SO(6_5-5_4) emission: roles of rotation, expansion and mass-loss history?  
  > "we explore the morpho-kinematics of the circumstellar envelope using ALMA observations of the SO($J_K=6_5-5_4$) emission" (Introduction)
- Target **R Dor**: coordinates _not stated_; z/distance ~59 pc  
  > "it is close to the Sun, at a distance of only $\sim$59 pc (cite: Knapp2003)" (Introduction); distance from Knapp et al. 2003  
  > "it is close to the Sun, at a distance of only $\sim$59 pc (cite: Knapp2003)" (Introduction)

## Data provenance

- ALMA projects: 2017.1.00824.S, 2013.1.00166.S
- bands: Band 6 (SO); Band 7 (comparison lines)  
  > "observed in December 2017 for $\sim$2.7 hours on source in band 6 with an average of 45 antennas" (Observations and data reduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.15 arcsec (9 au) circular beam  
  > "The beam is circular with a FWHM of 0.15 arcsec (9 au)" (Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: 1.1 mJy/beam per channel (SO); continuum 0.6 mJy/beam  
  > "giving evidence for a Gaussian noise of 1.1 mJy/beam (1$\sigma$)" (Observations and data reduction)
- time on source: ~2.7 hours  
  > "observed in December 2017 for $\sim$2.7 hours on source in band 6" (Observations and data reduction)
- observing dates: December 2017 (SO); summer 2015 (band 7)  
  > "observed in December 2017" (Observations and data reduction)
- pi or archival as stated: _not stated_
- Line: SO J_K=6_5-5_4 (251.826 GHz)
- External data: Rotating disc parameters (outer radius ~25 au, axis ~25 deg E of N, inclination ~20 deg)  
  > "evidence has been obtained for a rotating gas disc surrounding the star, with an outer radius of $\sim$25 au" (Introduction) [from Homan et al. 2018 (cite: Homan2018)]

## Processing

### Calibration

- pipeline or manual: Reduced by ALMA staff  
  > "The data, retrieved from ALMA archives and reduced by the ALMA staff" (Observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Archive-reduced data used; continuum subtracted in uv plane  
  > "The continuum contribution has been subtracted in the $uv$ plane." (Observations and data reduction)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 28 mas pixels, 0.29 km/s channels  
  > "with elements of 28$\times$28 mas$^2$ and 0.29 km s$^{-1}$" (Observations and data reduction)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: in the uv plane  
  > "The continuum contribution has been subtracted in the $uv$ plane." (Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.15 arcsec circular  
  > "The beam is circular with a FWHM of 0.15 arcsec (9 au)" (Observations and data reduction)
- final rms: 1.1 mJy/beam  
  > "giving evidence for a Gaussian noise of 1.1 mJy/beam (1$\sigma$)" (Observations and data reduction)

### Inherited from earlier work

- Interpretation of rotation/expansion anisotropy via sine-wave asymmetry method  
  > "Rotation about an axis projecting at position angle $\theta$ on the plane of the sky (cite: Diep2016; Nhung2018)" (3 Overview) [from (cite: Diep2016; Nhung2018)]

### Not stated but needed to reproduce (our reading)

- Imaging task, weighting and robust of the archived cube
- Exact velocity binning and masks for octant integrals
- How core positions and uncertainties in Table 1 were determined
- Procedure for cavity centre R_cent(omega) determination
- Position of phase centre and ALMA array configuration

## Analysis recipe

1. **Characterise anisotropy of the data cube**: Integrate intensity in eight octants (sign of Vz and N,E,S,W sectors) in two radial regions; fit asymmetry A(x*Vz) vs angle with a sine wave  
  > "we split the data-cube in eight octants depending on the sign of $V_z$ and on the position angle" (3 Overview)
   - fitting: _not stated_
   - validation: _not stated_
2. **Identify outflows in Vz vs position-angle PV maps**: Inspect PV maps at 0.6<R<0.8 arcsec and tabulate blobs  
  > "We therefore choose tentatively the interval of projected distances from the star $0.6<R<0.8$ arcsec as best compromise." (4.1)
   - fitting: _not stated_
   - validation: Compared with other molecular lines  
  > "The P-V maps of the CO, SO$_2$ and HCN lines display patterns similar to that observed for the SO line." (Comparison with other molecular lines)
3. **Map cavities and mass-loss history**: PV maps of R*f; analyse product Rf vs rho=sqrt(R^2+Vz^2/V0^2) with V0 = 4 and 5 km/s  
  > "Figure [12](#fig12) (right panel) displays the dependence of product $Rf$ on $\rho$ for both values of $V_0$, 4 and 5 km s$^{-1}$" (4.3)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **GILDAS** : Reduction of an alternative SiO data set as a check  
  > "reduced using ALMA pipeline standard script, GILDAS and natural weighting" (4.4)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Global anisotropy k, inner region | 20 | not stated | % | 1 | the global anisotropies, $k$=20% and 23%, respectively, are similar |
| Global anisotropy k, outer region | 23 | not stated | % | 1 | the global anisotropies, $k$=20% and 23%, respectively, are similar |
| Rotation axis PA east of north (inner region) | 17 | not stated | deg | 1 | $A(x^*V_z)=0.21\cos(\theta-17$$^\circ$) |
| Outflow symmetry axis position angle | ~140 | 5 | deg | 2 | about a position angle of $\sim140$$^\circ$$\pm$5$^\circ$ |

## Qualitative findings

- Slow wind hosts radial outflows with multiple cores and an enhanced mass-loss episode about a century ago  
  > "an episode of enhanced mass loss having occurred a century or so ago" (abstract)

## Claim tuples

- H: Is the nascent wind only a rotating disc or pure expansion? | E: Octant and PV analysis of SO cube | R: Inhomogeneous cores inconsistent with pure rotation or pure expansion | F: Wind has a rotating disc plus inhomogeneous radial outflows | **supported**
- H: Was there a recent episode of enhanced mass loss? | E: PV maps of Rf and rho distribution | R: Emission excess near rho~0.9 and cavity K1 | F: Enhanced mass loss ~a century ago | **partially**

## Reasoning

- Why this data: Large time on source gives better description of rotation and expansion  
  > "taking advantage of the large time on source, more than six times longer than for line emissions studied earlier" (Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Continuum emission complicates line study at R<0.2 arcsec  
  > "The importance of continuum emission from the star at projected distances $R<0.2$ arcsec complicates the study of the line emission in this region." (3 Overview)
- Caveat (inferred, ours): Mostly qualitative inspection; no formal fitting or uncertainties
- Caveat (inferred, ours): Outflow cores identified by eye
- Caveat (inferred, ours): No radiative transfer or deprojection model

## Reproducibility

- Data public (paper): Retrieved from ALMA archive via JVO/NAOJ  
  > "The data are retrieved from the JVO/NAOJ portal." (ACKNOWLEDGEMENTS)
- Products in archive: _not stated_
- Missing: Analysis code
- Missing: Exact selection/binning for P-V maps and cores
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Public data and clear descriptive analysis, but qualitative methods without code or detailed parameters.
- Rediscovery candidate: no, Results are mostly qualitative and the recipe is incomplete.

## Links

- Method: Diep et al. 2016; Nhung et al. 2018 (Rotation/expansion asymmetry method)
- Companion: Hoai et al. 2019 (High Doppler velocity components in the same data)
- Related: ATOMIUM

## Checks

```json
{
 "quotes": 35,
 "quotes_ok": 35,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 57,
  "stated": 25,
  "rate": 0.439
 },
 "evidence_ok": true
}
```
