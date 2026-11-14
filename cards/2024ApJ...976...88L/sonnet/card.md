# Disk Turbulence and Star Formation Regulation in High-z Main-sequence Analog Galaxies

`2024ApJ...976...88L` | The Astrophysical Journal 2024 | first author: Lenkić, Laura | arXiv: 2408.02730 | DOI: 10.3847/1538-4357/ad758c

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: nearby_galaxies, high_z_galaxies
- Question: What sets the molecular gas velocity dispersion (turbulence) and star formation regulation on kpc scales in z~0.1 analogues of z~1-2 main-sequence galaxies, and do star formation theories reproduce the sigma_mol-Sigma_SFR/Sigma_mol relations?  
  > "We measure beam smearing corrected molecular gas velocity dispersions and relate them to the molecular gas and star formation rate surface densities." (abstract)
- Target **DYNAMO sample: C13-1, D13-5, D15-3, G04-1, G08-5, G14-1, G20-2**: coordinates _not stated_; z/distance z = 0.067-0.141 (e.g. C13-1 z=0.07876, G20-2 z=0.14113)  
  > "| G04-1 | 0.12981 | 6.47 | $21.32 \pm 1$ | $0.33\pm0.04$ | 30 | 13 | 16 | -0.65 $\pm$ 0.03 | 0.98 (0.42) |" (Table 1); distance from _not stated_

## Data provenance

- ALMA projects: 2017.1.00239.S, 2019.1.00447.S
- bands: CO(3-2) where available, CO(4-3) otherwise (D15-3 only CO(4-3))  
  > "in all cases but DYNAMO D15-3, for which no CO(3$-$2) was available. In that case, we use the CO(4$-$3) integrated intensity map." (3.2 Molecular Gas Surface Density)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: CO beam FWHM 0.40-1.23 arcsec (0.95-3.08 kpc)  
  > "| G08-5 | 0.13217 | 1.73 | $10.04 \pm 1$ | $0.30\pm0.05$ | 36 | 15 | 20 | -0.63 $\pm$ 0.04 | 0.95 (0.40) |" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Programs 2017.1.00239.S (PI Fisher) and 2019.1.00447.S (PI Herrera-Camus)  
  > "project codes 2017.1.00239.S (PI: D. B. Fisher) and 2019.1.00447.S (PI: R. Herrera-Camus)" (2.2 ALMA and HST Observations)
- Line: CO J=3-2 (not stated)
- Line: CO J=4-3 (not stated)
- Other facility **HST (H-alpha, PID 12977)**: H-alpha as SFR tracer  
  > "HST observations of H$\alpha$ as a tracer of the star formation rate (PID 12977; P.I.: I. Damjanov)" (2.2 ALMA and HST Observations)
- Other facility **HST WFC3/IR F125W (PID 15069)**: Stellar mass tracer  
  > "HST WFC3/IR F125W observations ($\sim J$ band) as a tracer of the stellar mass (PID 15069; P.I.: D. B. Fisher)" (2.2 ALMA and HST Observations)
- Other facility **HST WFC3/UVIS F336W and ACS FR647M**: F336W-F125W color for M/L; FR647M for C13-1 mass  
  > "we use HST ACS/WFC FR647M instead and derive the masses from:" (3.1 Stellar Mass Surface Density)
- External data: Global sigma_mol, rotation curve (arctan) parameters, inclination from GalPak3D modelling  
  > "$^b$   Values from (cite: girard21)." (Table 1) [from (cite: girard21)]
- External data: R31 and R41 CO line ratios  
  > "we adopt the $R_{31}$ and $R_{41}$ values in Table 3 of (cite: lenkic23)" (3.2 Molecular Gas Surface Density) [from (cite: lenkic23)]
- External data: PHANGS-ALMA kpc-smoothed Sigma_mol, Sigma_SFR, sigma_mol, Sigma_* measurements  
  > "black squares correspond to measurements from the PHANGS-ALMA survey (cite: sun20; leroy21), which have been smoothed to kpc-scale resolution" (4.2 Sigma_mol-Sigma_* Relation) [from (cite: sun20; leroy21; Sun2023)]
- External data: Global galaxy properties (M*, SFR, fgas, Sigma_SFR)  
  > "$^a$   Values from (cite: fisher17a), (cite: White2017) and (cite: fisher19)." (Table 1) [from (cite: fisher17a; White2017; fisher19)]
- Simulation/model as data: Model predictions from Krumholz+18, Ostriker & Kim 2022 (TIGRESS), Rathjen+23 (SILCC), Brucy+20, Ginzburg+22, Faucher-Giguere+13 compared with data  
  > "we first compare the DYNAMO and PHANGS-ALMA results to the predictions of (cite: krumholz18)." (5.1.1 Gravitational and Stellar Feedback-Driven Turbulence)

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

- task: tclean in CASA  
  > "These observations were imaged using `tclean` with the Common Astronomy Software Application (cite: mcmullin07)" (2.2 ALMA and HST Observations)
- deconvolver: _not stated_
- weighting robust: briggs, robust=0.5  
  > "with `weighting=‘‘briggs’’` and `robust=0.5`." (2.2 ALMA and HST Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: HST images convolved with Gaussian of FWHM equal to circularized ALMA beam, then reprojected to CO WCS/pixel scale  
  > "we convolve the HST observations with a two-dimensional Gaussian function whose FWHM is equal to the circularized beam of the corresponding ALMA observation." (2.2 ALMA and HST Observations)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA data processing and data products  
  > "Detailed information on the data processing and data products can be found in (cite: lenkic23)." (2.2 ALMA and HST Observations) [from (cite: lenkic23)]
- HST H-alpha and F125W reduction and analysis  
  > "For details on the reduction and analysis of these observations, see (cite: fisher17a) and (cite: ambachew22), respectively." (2.2 ALMA and HST Observations) [from (cite: fisher17a); (cite: ambachew22)]
- Beam smearing correction procedure  
  > "We follow the procedure outlined in (cite: levy18), which we summarize here for completeness." (3.4 Velocity Dispersion) [from (cite: levy18)]
- H-alpha extinction correction  
  > "apply a correction for extinction (cite: lenkic23)" (3.3 Star Formation Rate Surface Density) [from (cite: lenkic23)]

### Not stated but needed to reproduce (our reading)

- Line-free channels, continuum subtraction and moment-map/integrated intensity masking details
- Image size, cell size, channel width, cleaning threshold, final rms of cubes
- Aperture radius definition and exact beam-sized aperture grid placement
- S/N cuts for spectral fits and initial guesses for curve_fit
- Metallicity values used for variable alpha_CO
- Extinction values per aperture
- Whether ALMA archive products or reprocessed data were used
- Details of the ODR fitting (weights, error treatment)

## Analysis recipe

1. **Match HST images to CO resolution**: Convolve HST images with Gaussian of circularized ALMA beam, reproject to CO WCS, scale by pixel-scale ratio squared  
  > "we scale the reprojected images by the squared ratio of the new pixel scale and old pixel scale to conserve flux." (2.2 ALMA and HST Observations)
   - software: reproject, astropy
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure Sigma_*, Sigma_SFR and Sigma_mol in beam-sized apertures**: Two offset grids of beam-sized circular apertures; stellar mass from F125W with color-based M/L; SFR from Halpha (Hao+11); Sigma_mol = alpha_CO R_J,J-1 I_CO  
  > "we define a “grid” of circular, beam-sized apertures centered on the galaxy, and a second that is offset from the center by $0.5 \times$ the beam FWHM" (3 Methods)
   - software: CASA, astropy
   - parameter: log Upsilon = 0.195 (F336W-F125W) - 1.187, floor -1  
  > "and we impose a floor of $\mathrm{log} \, \Upsilon_{*,\mathrm{F125W}} = -1$." (3.1 Stellar Mass Surface Density)
   - parameter: SFR = 5.53e-42 L_Halpha  
  > "SFR\;[M_{\odot}\,yr^{-1}]} = 5.53 \times 10^{-42} \times L_{\mathrm{H}\alpha}" (3.3 Star Formation Rate Surface Density)
   - assumption: Constant alpha_CO = 4.35 Msun (K km/s pc^2)^-1, or variable alpha_CO from Bolatto+13 eq. 31 iterated until change <0.1%  
  > "repeating this process until $\alpha_{\mathrm{CO}}$ changes by less than 0.1%." (3.2 Molecular Gas Surface Density)
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure beam-smearing-corrected velocity dispersion**: Gaussian fit of central-pixel CO spectrum per aperture; subtract in quadrature model beam-smearing dispersion from arctan rotation-curve model cube smoothed to beam  
  > "We perform our fitting using the Python SciPy function `curve_fit`." (3.4 Velocity Dispersion)
   - software: SciPy curve_fit, spectral-cube
   - assumption: Arctan rotation curve with parameters and inclination from Girard+21  
  > "we adopt the arctan model and rotation curve parameters from (cite: girard21)" (3.4 Velocity Dispersion)
   - fitting: Gaussian line fit with scipy curve_fit  
  > "We perform our fitting using the Python SciPy function `curve_fit`." (Methods, Velocity Dispersion)
   - validation: Compared with Girard+21 GalPak3D dispersions (within a channel width beyond central beam); tested uncorrected and central-excluded fits  
  > "they are all within a channel width or less of each other." (Beam Smearing Correction Discussion)
4. **Fit scaling relations and compare to theory**: ODR power-law fits of Sigma_mol-Sigma_*, KS, sigma_mol-Sigma_mol, -Sigma_SFR, -t_dep, with PHANGS; compare to Krumholz+18, TIGRESS, SILCC, Brucy+20 curves  
  > "with a power law of the form $\mathrm{log}$ $\Sigma_{\mathrm{SFR}}$ $= N\, \times\, \mathrm{log}$ $\Sigma_{\mathrm{mol}}$ $+\,C$ using ODR." (4.3 Resolved Molecular KS Relation at High Sigma_SFR)
   - software: scipy ODR
   - assumption: Krumholz+18 fiducial parameters; P*/m* = 3000 km/s for Faucher-Giguere model  
  > "If we assume $P_{*}/m_{*} = 3,000$ km s$^{-1}$" (4.4 Resolved Correlations)
   - fitting: ODR; priors not applicable  
  > "with a power law of the form $\mathrm{log}$ $\Sigma_{\mathrm{SFR}}$ $= N\, \times\, \mathrm{log}$ $\Sigma_{\mathrm{mol}}$ $+\,C$ using ODR." (Results, Resolved Molecular KS Relation at High $\Sigma_{\mathrm{SFR}}$)
   - validation: _not stated_

## Software

- **CASA** : tclean imaging of ALMA data  
  > "imaged using `tclean` with the Common Astronomy Software Application (cite: mcmullin07)" (2.2 ALMA and HST Observations)
- **reproject** : Reprojecting HST images to CO grid  
  > "using the Python astropy package `reproject`" (2.2 ALMA and HST Observations)
- **SciPy** : curve_fit Gaussian fitting of CO spectra  
  > "We perform our fitting using the Python SciPy function `curve_fit`." (3.4 Velocity Dispersion)
- **spectral-cube** v0.4.4: listed in Software; cube handling  
  > "spectral-cube (cite: 2019SpectralCube)" (Software)
- **GalPak3D** : Global sigma_mol in Girard+21, used for comparison  
  > "The authors model the ALMA CO data cubes with GalPak$^{3D}$ (cite: bouche15)." (3.4 Velocity Dispersion)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Resolved Sigma_mol-Sigma_* slope | 0.78 | 0.03 | dimensionless | 4 | \log \Sigma_{\mathrm{mol}} = (0.78\pm0.03) \times  \log \Sigma_{*} + (0.05\pm0.07). |
| KS slope, constant alpha_CO, DYNAMO only | 0.90 | 0.04 | dimensionless | 4 | (0.90 \pm 0.04) \, \times \, \mathrm{log} \; \Sigma_{\mathrm{mol}} - (2.70 \pm 0.08) |
| KS slope, variable alpha_CO, DYNAMO | 1.23 | 0.03 | dimensionless | 4 | (1.23 \pm 0.03) \, \times \, \mathrm{log} \; \Sigma_{\mathrm{mol}} - (3.08 \pm 0.06) |
| Median depletion time, constant alpha_CO | 0.8 | not stated | Gyr | 4 | more than half of the DYNAMO line-of-sight measurements (297/490) have $t_{\mathrm{dep}}$ $<1$ Gyr. |
| sigma_mol-Sigma_mol slope (DYNAMO+PHANGS) | 0.48 | 0.02 | dimensionless | 4 | \mathrm{log}\;\sigma_{\mathrm{mol}} = (0.48 \pm 0.02) \, \times \, \mathrm{log\;}\Sigma_{\mathrm{mol}} + (0.47 \pm 0.03) |
| sigma_mol-Sigma_SFR slope (DYNAMO+PHANGS) | 0.27 | 0.02 | dimensionless | 4 | $N = 0.27 \pm 0.02$ |
| sigma_mol-t_dep slope | -0.80 | 0.07 | dimensionless | 4 | \mathrm{log}\;\sigma_{\mathrm{mol}} = (-0.80 \pm 0.07) \, \times \, \mathrm{log\;}t_{\mathrm{dep}} + (1.00 \pm 0.03). |
| Fraction of measurements in powered-breakout region | ~38 | not stated | percent | 4 | We find that ${\sim} 38$% of our measurements lie within the region where powered breakouts |

## Qualitative findings

- DYNAMO galaxies are more gas-rich than local spirals at all disk positions and not analogous to local spiral centers  
  > "DYNAMO galaxies are more gas-rich than local spirals (see Figure [3](#fig:ssd_gsd)) and are not analogous to the centers of local star-forming galaxies." (6 Summary and Conclusions)

## Claim tuples

- H: Are DYNAMO galaxies more gas-rich than local spirals on kpc scales? | E: Compare resolved Sigma_mol-Sigma_* with PHANGS | R: Sub-linear relation offset ~order of magnitude higher in Sigma_mol/Sigma_* | F: DYNAMO are globally more gas rich at all disk positions | **supported**
- H: Does gravity+feedback transport theory reproduce sigma_mol? | E: Compare data to Krumholz+18 for fiducial and varied t_orb | R: Models overpredict observed sigma_mol | F: Transport+feedback overestimates dispersions | **supported**
- H: Is stellar feedback alone sufficient? | E: Compare to TIGRESS, SILCC and feedback-only Krumholz+18 | R: Slopes ~0.2 vs observed 0.27; reasonable agreement | F: Feedback-regulated models reproduce observations without transport | **supported**

## Reasoning

- Why this data: DYNAMO galaxies resemble z~1-2 main-sequence systems but are nearby, allowing kpc-scale resolved study  
  > "Their resemblance to high-redshift systems and proximity to us allows us to probe the turbulence powering mechanisms in gas-rich galaxies on kpc scales." (Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Literature comparison sample is heterogeneous and of differing data quality  
  > "We offer the strong caveat that the sample is not homogeneously selected and there is a difference in data quality" (4.1 Galaxy Averaged Relationship)
- Caveat (inferred, ours): Only seven galaxies; beam smearing correction depends on assumed arctan models
- Caveat (inferred, ours): Gaussian fit of central pixel spectrum may be affected by non-Gaussian profiles and S/N
- Caveat (inferred, ours): Overlapping apertures make measurements non-independent for ODR errors
- Caveat (inferred, ours): alpha_CO and extinction assumptions drive KS results

## Reproducibility

- Data public (paper): ALMA project codes given; HST data from MAST  
  > "Some of the data presented in this article were obtained from the Mikulski Archive for Space Telescopes (MAST) at the Space Telescope Science Institute." (Acknowledgments)
- Products in archive: _not stated_
- Code: _not stated_
- Missing: Imaging details deferred to Lenkić+23
- Missing: Exact aperture size, masks, S/N thresholds
- Missing: Extinction and metallicity inputs
- Missing: Girard+21 rotation curve parameters
- Data volume (inferred): tens of GB for ALMA CO cubes of 7 targets plus small HST images
- Score (inferred): 3/5, Public data and a clear recipe for derived quantities, but key processing and per-aperture inputs are deferred to other papers.
- Rediscovery candidate: no, Recipe depends on inherited imaging, extinction and rotation-curve parameters not given here.

## Links

- Method: (cite: lenkic23) (ALMA data processing, R31/R41 ratios, extinction)
- Method: (cite: levy18) (Beam smearing correction procedure)
- Method: (cite: girard21) (Rotation curve parameters and global sigma_mol)
- Companion: (cite: lenkic23) (Companion ALMA CO study of the same galaxies)
- Companion: (cite: girard21) (Global molecular velocity dispersions for DYNAMO)
- Related: DYNAMO
- Related: PHANGS-ALMA
- Related: ALMaQUEST
- Related: EDGE-CALIFA
- Related: HERACLES

## Checks

```json
{
 "quotes": 58,
 "quotes_ok": 58,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 41,
  "rate": 0.512
 },
 "evidence_ok": true
}
```
