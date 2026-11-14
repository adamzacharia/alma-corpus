# Polarization Properties and Magnetic Field Structures in the High-mass Star-forming Region W51 Observed with ALMA

`2018ApJ...855...39K` | The Astrophysical Journal 2018 | first author: Koch, Patrick M. | arXiv: 1801.08264 | DOI: 10.3847/1538-4357/aaa4c1

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism
- Question: What are the dust polarization properties and B-field morphologies in W51 e2, e8 and North at ~5 mpc, and how effectively can the B-field oppose gravity (sin omega)?  
  > "The focus of the present paper is to study the role of the magnetic (B) field with the Atacama Large Millimeter/submillimeter Array (ALMA) at a physical scale around 5 mpc in W51 e2, e8, and North." (Introduction)
- Target **W51 e2**: coordinates 19:23:43.95 +14:30:34.00 (J2000)  
  > "W51 e2 together with e8 is located along a molecular ridge at a parallax distance around 5.41 kpc (cite: sato10)." (Introduction); "(19:23:43.95, 14:30:34.00), (19:23:43.90, 14:30:27.00) and (19:23:39.95, 14:31:05.50), respectively." (2 Observations); z/distance 5.41 kpc  
  > "W51 e2 together with e8 is located along a molecular ridge at a parallax distance around 5.41 kpc (cite: sato10)." (Introduction); "(19:23:43.95, 14:30:34.00), (19:23:43.90, 14:30:27.00) and (19:23:39.95, 14:31:05.50), respectively." (2 Observations); distance from parallax, Sato et al. 2010  
  > "W51 e2 together with e8 is located along a molecular ridge at a parallax distance around 5.41 kpc (cite: sato10)." (Introduction); "(19:23:43.95, 14:30:34.00), (19:23:43.90, 14:30:27.00) and (19:23:39.95, 14:31:05.50), respectively." (2 Observations)
- Target **W51 e8**: coordinates 19:23:43.90 +14:30:27.00 (J2000)  
  > "W51 e2 together with e8 is located along a molecular ridge at a parallax distance around 5.41 kpc (cite: sato10)." (Introduction); z/distance 5.41 kpc  
  > "W51 e2 together with e8 is located along a molecular ridge at a parallax distance around 5.41 kpc (cite: sato10)." (Introduction); distance from parallax, Sato et al. 2010  
  > "W51 e2 together with e8 is located along a molecular ridge at a parallax distance around 5.41 kpc (cite: sato10)." (Introduction)
- Target **W51 North**: coordinates 19:23:39.95 +14:31:05.50 (J2000)  
  > "Parallax measurements towards W51 North yield about 5.1 kpc (cite: xu09)." (Introduction); z/distance 5.1 kpc  
  > "Parallax measurements towards W51 North yield about 5.1 kpc (cite: xu09)." (Introduction); distance from parallax, Xu et al. 2009  
  > "Parallax measurements towards W51 North yield about 5.1 kpc (cite: xu09)." (Introduction)

## Data provenance

- ALMA projects: 2013.1.00994.S
- bands: Band 6 (230 GHz)  
  > "in Band 6 (230 GHz) with a resolution around 0$\ensuremath{''}$26" (abstract)
- frequencies and spectral setup: four basebands, FDM mode, 3840 channels over 1.875 GHz, 488 kHz resolution  
  > "The four basebands were set in FDM mode (3840 channels for 1.875 GHz with a resolution of 488 kHz)." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: 12-m array (implied by baselines 13-1492 m, 38 antennas)  
  > "The array included 38 antennas" (2 Observations)
- configurations: _not stated_
- baselines: 38 antennas, 13 m to 1492 m  
  > "The array included 38 antennas with (projected) baselines ranging from 13 m to 1492 m." (2 Observations)
- angular resolution: 0.28"x0.26", PA 33 deg  
  > "synthesized beam resolution $\theta\sim0\ensuremath{''}$28$\times$0$\ensuremath{''}$26 with an orientation of 33$\ensuremath{^\circ}$" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: Stokes I 1σ 6 mJy/beam (e2, e8), 1.4 mJy/beam (North); Q 0.15 (e2,e8), 0.08; U 0.19 (e2,e8), 0.10 mJy/beam  
  > "The sensitivities (1$\sigma$) are 6 mJy/beam (e2, e8) and 1.4 mJy/beam (North) for Stokes $I$" (2 Observations)
- time on source: _not stated_
- observing dates: July 18, 2015, three execution blocks  
  > "Observations were done in three execution blocks (EBs) on July 18, 2015." (2 Observations)
- pi or archival as stated: _not stated_
- Other facility **SMA**: 345 GHz polarization maps (Tang et al. 2009) and new combined subcompact+compact envelope-scale maps, theta~2.13x1.88 arcsec  
  > "we also present new larger-scale SMA maps combining data from the subcompact array configuration" (2 Observations)
- External data: SMA 345 GHz polarization maps of e2, e8, North reproduced for comparison  
  > "here reproduced from (cite: tang09b) in panel (b), (c), and (g) in Figure [1](#figure_composite_pol)" (3.2 Polarization) [from (cite: tang09b)]
- External data: SMA 1.3 mm flux densities of e2 sub-cores  
  > "Their reported flux densities are 2.15$\pm$0.12, 0.62$\pm$0.12 and 0.73$\pm$0.08 Jy for W51 e2-E, e2-NW and w2-N, respectively." (3.1 230 GHz Dust Continuum) [from (cite: shi10a)]
- External data: SMA compact array data for e2, e8, North  
  > "compact array configuration (described originally in (cite: zhang14) for W51 e2, e8, and W51 North)" (2 Observations) [from (cite: zhang14)]

## Processing

### Calibration

- pipeline or manual: Separate EB calibration, then polarization calibration after merging, standard ALMA procedure  
  > "Polarization calibration was performed after merging the three calibrated EBs following the standard polarization calibration for ALMA" (2 Observations)
- casa version: CASA v4.5.0  
  > "was performed using CASA[^2] v4.5.0." (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1922+1530 (0.175 Jy at 232.9 GHz) with Titan as reference  
  > "With a flux of 0.175 Jy at 232.9 GHz, J1922+1530 also provided the flux scale with the reference flux calibrator Titan." (2 Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "The images presented here are with natural weighting" (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.28"x0.26", PA 33 deg  
  > "synthesized beam resolution $\theta\sim0\ensuremath{''}$28$\times$0$\ensuremath{''}$26 with an orientation of 33$\ensuremath{^\circ}$" (2 Observations)
- final rms: _not stated_

### Inherited from earlier work

- Local gravity direction calculation and MHD force equation  
  > "Calculating the local direction of gravity is introduced in (cite: koch12a)." (Footnote 4) [from (cite: koch12a)]
- SMA subcompact data for W51 North  
  > "subcompact array configuration (described originally in (cite: tang13) for W51 North)" (2 Observations) [from (cite: tang13)]
- Instrumental polarization in Band 6  
  > "A detailed analysis of the instrumental polarization in Band 6 is given in (cite: nagai16)" (2 Observations) [from (cite: nagai16)]

### Not stated but needed to reproduce (our reading)

- Spectral windows/channels used for continuum and total bandwidth
- Image size, cell size, and whether clean was used with masks/threshold
- Self-calibration performed or not
- Polarization calibration details (leakage calibrator, Stokes solutions)
- Pixel sampling used for B-field segments and the annulus for dispersion S
- Procedure for the power-law fits of p vs I
- Details of SMA combination and unpublished SMA data
- Primary beam correction treatment for mosaics/pointings

## Analysis recipe

1. **Calibrate and image Stokes I, Q, U**: Separate EB calibration in CASA, merged for polarization calibration; natural weighting imaging  
  > "The three EBs were calibrated separately in flux, bandpass and gain." (2 Observations)
   - software: CASA
   - parameter: polarization calibrator J1924-2914, p=2.56%, PA=45.6 deg  
  > "measured to have a polarization fraction of 2.56% and a polarization position angle of 45.6$\ensuremath{^\circ}$" (2 Observations)
   - fitting: _not stated_
   - validation: Calibrator polarization consistent with other ALMA measurements  
  > "in agreement with other ALMA measurements" (2 Observations)
2. **Derive debiased polarized intensity and fraction**: Debias Ip=sqrt(Q²+U²-σ²) for Ip≥3σp; require I≥3σ and Ip≥3σp  
  > "For all results displayed in this paper we impose the two simultaneous conditions of having Stokes $I\geq$3$\sigma$ and $I_p\geq$3$\sigma_p$." (2 Observations)
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure core flux densities**: two-dimensional Gaussian fits to continuum cores  
  > "The flux densities of these dense cores are determined by two-dimensional Gaussian fits" (3.1 230 GHz Dust Continuum)
   - fitting: 2D Gaussian  
  > "The flux densities of these dense cores are determined by two-dimensional Gaussian fits to be 2.54, 1.04, 0.22 and 0.10 Jy for W51 e2-E, e2-W, e2-NW and e2-N, respectively" (Results: 230 GHz Dust Continuum)
   - validation: Compared with SMA fluxes of Shi et al. 2010a  
  > "Our newly reported flux densities are within the 3$\sigma$ uncertainty levels of the ones in (cite: shi10a)." (3.1 230 GHz Dust Continuum)
4. **Fit p vs I anti-correlation and compute B-field dispersion S**: Power-law fit of p vs I; S computed with r_disp=0.2" over neighbouring segments; B-field = polarization PA rotated 90 deg  
  > "Figure [6](#figure_field_dispersion) shows $\mathcal{S}$-maps, evaluated for $r_{disp}=0.2\ensuremath{''}$" (4.1 Polarization Structures)
   - parameter: r_disp = 0.2 arcsec  
  > "evaluated for $r_{disp}=0.2\ensuremath{''}$" (4.1 Polarization Structures)
   - fitting: power-law fit (method not stated)  
  > "The anti-correlation can be fit with power-laws with indices -1.02 (e2), -0.84 (e8), and -0.84 (North)." (Results: Polarization)
   - validation: Compared with Planck and BLASTPol results  
  > "Our findings are in line with recent BLASTPol results for the Vela C molecular cloud" (4.1 Polarization Structures)
5. **Compute sin omega maps**: Local gravity direction from summing pixelized dust emission weighted 1/r² as point masses; omega is angle between gravity direction and B-field orientation (0-90 deg)  
  > "derived by summing up all the surrounding pixelized dust emission weighted by $1/r^2$ along the direction to each pixel" (Footnote 4)
   - assumption: Dust emission distribution represents total mass distribution  
  > "The observed dust emission *distribution* is assumed to represent the total mass *distribution* that generates the gravitational potential $\phi$." (Footnote 4)
   - fitting: _not stated_
   - validation: Initial comparison shows close structural resemblance to Sigma_B maps  
  > "An initial comparison is showing a close structural resemblance between $\sin\omega$- and $\Sigma_B$-maps." (4.2 Gravity vs Magnetic Field)

## Software

- **CASA** 4.5.0: Calibration (bandpass, phase, amplitude, flux, polarization)  
  > "The calibration (bandpass, phase, amplitude, flux) was performed using CASA[^2] v4.5.0." (2 Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total 230 GHz continuum flux e2 | 4.0 | not stated | Jy | 3 | is 4.0, 3.7 and 6.8 Jy for W51 e2, e8 and North, respectively. |
| Flux densities e2-E, e2-W, e2-NW, e2-N | 2.54, 1.04, 0.22, 0.10 | not stated | Jy | 3 | to be 2.54, 1.04, 0.22 and 0.10 Jy for W51 e2-E, e2-W, e2-NW and e2-N, respectively |
| p vs I power-law index (e2, e8, North) | -1.02, -0.84, -0.84 | not stated | dimensionless | 4 | The anti-correlation can be fit with power-laws with indices -1.02 (e2), -0.84 (e8), and -0.84 (North). |
| Mean sin omega e2 | 0.40 | std 0.27 | dimensionless | 5 | $\sin\omega$ averaged over the entire W51 e2 map is small with 0.40 and a standard deviation of 0.27. |
| Mean sin omega e8 | 0.41 | std 0.29 | dimensionless | 5 | average $\sin\omega$ value of 0.41 and a standard deviation of 0.29 |
| Mean sin omega North | 0.47 | std 0.30 | dimensionless | 5 | with an overall average of 0.47 and a standard deviation of 0.30 |
| Polarization percentage range | 0.1% to 10% | not stated | % | 2 | Measured relative polarization levels are between 0.1% and 10%. |

## Qualitative findings

- New B-field features resolved: cometary morphologies in satellite cores, convergence zones, possible streamlined fields  
  > "revealing new features such as cometary-shaped B-field morphologies in satellite cores, symmetrically converging B-field zones, and possibly streamlined morphologies" (abstract)

## Claim tuples

- H: Does relative polarization anti-correlate with Stokes I at mpc scales? | E: Power-law fits of p vs I for each source | R: Indices about -1 with scatter of almost an order of magnitude | F: Typical anti-correlation present with large scatter, implying additional physics | **supported**
- H: Is polarization related to local B-field dispersion? | E: Compare S and p maps | R: Lowest p coincides with largest S in convergence zones | F: Anti-correlation of p and S continues to mpc scales; likely unresolved field structure | **supported**
- H: Can sin omega map where the B-field can oppose gravity? | E: Compute sin omega maps from B-field and gravity direction | R: Organized structures; mean values 0.40-0.47; narrow sin omega~0 channels | F: B-field role varies locally, with possible magnetic channels, speculative at resolution limit | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Lower grain alignment efficiency could also explain p anti-correlations with S and I  
  > "Alternatively, an intrinsic lower grain alignment efficiency, due to varying densities and temperatures, might also explain these two anti-correlations." (4.1 Polarization Structures)
- How they decided it was enough: _not stated_
- Limitation (authors): sin omega only captures gravity-dominated zones; large values need field strength  
  > "Its shortcoming is that it can only capture the zones where gravity is clearly dominating over the B-field" (4.2 Gravity vs Magnetic Field)
- Caveat (inferred, ours): No continuum/line-free or imaging parameters given, hindering reproduction
- Caveat (inferred, ours): Qualitative interpretation of B-field morphologies is subjective
- Caveat (inferred, ours): Gravity direction assumes dust emission traces mass and ignores filtered large scales
- Caveat (inferred, ours): No uncertainties on sin omega or fits

## Reproducibility

- Data public (paper): ALMA project code given; public status not explicitly stated  
  > "ADS/JAO.ALMA#2013.1.00994.S" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters (cell, size, masking, cleaning)
- Missing: Spectral windows used for continuum
- Missing: Leakage calibration details
- Missing: Fit procedure for power laws
- Missing: Unpublished SMA data
- Data volume (inferred): ~100-300 GB raw for three execution blocks
- Score (inferred): 3/5, Data identified and calibration outline given, but imaging details missing; analysis is mostly maps with few numbers.
- Rediscovery candidate: no, Imaging and fitting recipes are incomplete and key results are morphological.

## Links

- Method: (cite: koch12a) (MHD force equation and gravity direction method)
- Method: (cite: nagai16) (ALMA Band 6 instrumental polarization)
- Companion: (cite: tang09b) (SMA polarization of e2/e8)
- Companion: (cite: tang13) (SMA polarization of W51 North)
- Related: SMA W51 polarization
- Related: Planck
- Related: BLASTPol

## Checks

```json
{
 "quotes": 63,
 "quotes_ok": 63,
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
