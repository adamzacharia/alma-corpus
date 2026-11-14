# First detection of the 448 GHz ortho-H<SUB>2</SUB>O line at high redshift: probing the structure of a starburst nucleus at z = 3.63

`2020A&A...634L...3Y` | Astronomy and Astrophysics 2020 | first author: Yang, C. | arXiv: 2001.06589 | DOI: 10.1051/0004-6361/201937319

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Can the first high-z detection of the 448 GHz ortho-H2O line, with other H2O lines and dust continuum, constrain the structure of the dusty ISM in the lensed SMG G09v1.97-R?  
  > "In combination with three other previously detected H~2~O lines, we build a model that “resolves” the dusty ISM structure of the SMG" (abstract)
- Target **G09v1.97 (R component)**: coordinates _not stated_; z/distance z = 3.63; D_L = 32.7 Gpc  
  > "in a strongly lensed SMG at $z=3.63$ in the SMG merging pair G09v1.97" (Introduction); "$D_L=32.7$ Gpc is the luminosity distance" (Analysis and Discussion); distance from _not stated_

## Data provenance

- ALMA projects: 2018.1.00797.S
- bands: Band 3, spectral window covering H2O(4_23-3_30) at 96.137 GHz observed  
  > "we only present data from the Band-3 spectral window covering the ortho-H~2~O($4_{23}\text{--}3_{30}$) line centered at 96.137 GHz (observed frequency)." (2 Observations and data reduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12-m array, 43 antennas  
  > "Forty-three antennas of the 12-m array were used." (2 Observations and data reduction)
- configurations: C43-2  
  > "with the C43-2 configuration, which provides baselines ranging from 15 to 200 m" (2 Observations and data reduction)
- baselines: 15 to 200 m  
  > "with the C43-2 configuration, which provides baselines ranging from 15 to 200 m" (2 Observations and data reduction)
- angular resolution: 2.46" x 2.03", PA 78.2 deg  
  > "synthesis beamsize of 2.46$''$$\times$2.03$''$ and $PA$ = 78.2$^{\circ}$" (2 Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: ~0.12 mJy/beam in 50 km/s bins  
  > "resulting in a sensitivity of $\sim$ 0.12 mJy/beam in 50 km s$^{-1}$ velocity bins" (2 Observations and data reduction)
- time on source: 118.4 min on source (plus 47.7 min overhead)  
  > "The total on-source time was 118.4 min, with an additional overhead time of 47.7 min" (2 Observations and data reduction)
- observing dates: December 2018 to January 2019  
  > "The observations were carried out between December 2018 and January 2019." (2 Observations and data reduction)
- pi or archival as stated: _not stated_
- Line: ortho-H2O 4_23-3_30 (448.001 GHz)
- Other facility **NOEMA**: H2O(3_21-3_12) and H2O(4_22-4_13) line fluxes  
  > "which were obtained with NOEMA with similar spatial resolution of $\gtrsim$ 2$''$ (unresolved)" (4 Analysis and Discussion)
- External data: H2O(2_11-2_02) flux, linewidth and magnification, plus CO(6-5) high-resolution data  
  > "para-H~2~O($2_{11}\text{--}2_{02}$) | 137 | 752.033 | $4.2\pm0.6$" (Table 1) [from (cite: 2016A&A...595A..80Y); (cite: 2019A&A...624A.138Y)]
- External data: H2O(4_22-4_13) line flux  
  > "ortho-H~2~O($4_{22}\text{--}4_{13}$) | 454 | 1207.639 | $1.8\pm0.6$" (Table 1) [from (cite: 2017PhDT........21Y)]
- External data: Einstein A coefficients of the H2O lines  
  > "$5.4\times10^{-5}$ and $2.8\times10^{-2}$ s$^{-1}$, respectively" (4 Analysis and Discussion) [from (cite: 1998JQSRT..60..883P)]

## Processing

### Calibration

- pipeline or manual: ALMA calibration pipelines with minor flagging  
  > "The data were calibrated using the ALMA calibration pipelines with minor flagging." (2 Observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0750+1231 (also bandpass)  
  > "J0750+1231 as the bandpass and flux calibrator" (2 Observations and data reduction)
- flux scale uncertainty: 5%  
  > "A typical ALMA Band-3 calibration uncertainty of 5% is adopted." (2 Observations and data reduction)
- self calibration: _not stated_

### Imaging

- task: tclean in CASA 5.4.0  
  > "using `tclean` procedure of the `CASA` software (cite: 2007ASPC..376..127M) version 5.4.0" (2 Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "with a natural weighting (synthesis beamsize of 2.46$''$$\times$2.03$''$ and $PA$ = 78.2$^{\circ}$) to maximize the signal to noise ratio" (2 Observations and data reduction)
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
- final beam: 2.46" x 2.03", PA = 78.2 deg  
  > "synthesis beamsize of 2.46$''$$\times$2.03$''$ and $PA$ = 78.2$^{\circ}$" (2 Observations and data reduction)
- final rms: _not stated_

### Inherited from earlier work

- Radiative-transfer model component library following earlier method; details in prep.  
  > "a library of model components has been developed following the method described in (cite: 2014A&A...567A..91G)" (4 Analysis and Discussion) [from (cite: 2014A&A...567A..91G)]
- Magnification of R (~20) and B (~5) taken from earlier high-resolution lens modelling  
  > "the magnifications R and B are $\mu_{\mathrm{R}}$ $\approx$ 20 and $\mu_{\mathrm{B}}$ $\approx$ 5, respectively" (4 Analysis and Discussion) [from (cite: 2019A&A...624A.138Y)]
- Gas temperature of 150 K from CO excitation  
  > "$T_{\mathrm{gas}}$ = 150 K (consistent with the results from CO excitation, (cite: 2017A&A...608A.144Y))" (4 Analysis and Discussion) [from (cite: 2017A&A...608A.144Y)]

### Not stated but needed to reproduce (our reading)

- Model code and grid ranges not public (González-Alfonso et al., in prep.)
- Line-free channels, continuum subtraction and image size/cell size
- Method to extract line flux and fit for 448 GHz line (aperture, velocity range)
- Continuum flux densities used in the fit and their sources
- Priors/grid spacing for Tdust, tau100, NH2O, nH2
- Lens model for magnification as a function of velocity

## Analysis recipe

1. **Image and extract spectrum**: tclean natural-weighted cube; spectrum from spatially integrated emission over entire source  
  > "The spectrum was then extracted from the spatially integrated emission over the entire source" (2 Observations and data reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Isolate R component and correct magnification**: Associate detection (>=5 sigma) only with red component; correct line fluxes with mu_R=20; scale continuum down by 25 with 20% uncertainty  
  > "Therefore, here we scale down the measured continuum fluxes by a factor of 25 and include an uncertainty of 20% associated with the flux scaling." (4 Analysis and Discussion)
   - assumption: Similar H2O(4_23-3_30)/H2O(2_11-2_02) flux ratio in R and B  
  > "Assuming a similar flux ratio of H~2~O($4_{23}\text{--}3_{30}$)/H~2~O($2_{11}\text{--}2_{02}$) in R and B" (4 Analysis and Discussion)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit H2O excitation and dust continuum with multi-component models**: Grid of spherical uniform components; up to 2 per group, all combinations; chi2 minimization for radius; likelihood distributions of parameters  
  > "a $\chi^2$ minimization procedure is used to determine the source radius $R$ of each component for all combinations of model components" (4 Analysis and Discussion)
   - parameter: Fixed Delta V = 100 km/s, Tgas = 150 K  
  > "we keep fixed $\Delta V$ = 100 km s$^{-1}$ and $T_{\mathrm{gas}}$ = 150 K" (4 Analysis and Discussion)
   - assumption: GDR = 100; X_H2O = N_H2O/(1.3e24 tau100 (GDR/100))  
  > "With the assumption of a $\mathit{GDR}$ = 100, we obtain $X_{\mathrm{H_{2}O}}$ $\sim$ $(0.3\text{--}5)\times10^{-5}$" (4 Analysis and Discussion)
   - fitting: chi2 minimization over component combinations, likelihood distribution following Ward et al. 2003  
  > "enable us to calculate the likelihood distribution of the free physical parameters (cite: 2003ApJ...587..171W)" (4 Analysis and Discussion)
   - validation: Single component gives chi2_red≈4; two components give ≈0.9; CMB excitation checked negligible; fit without the 448 line compared  
  > "A better fit was found with $N_\mathrm{C}$ = 2 components (Fig. [3](#fig:model)), with $\chi_\mathrm{red}^2$ $\approx$ 0.9." (4 Analysis and Discussion)

## Software

- **CASA** 5.4.0: calibration pipeline, tclean imaging  
  > "using `tclean` procedure of the `CASA` software (cite: 2007ASPC..376..127M) version 5.4.0" (2 Observations and data reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| H2O(4_23-3_30) line flux (magnification-uncorrected, R) | 0.16 | 0.03 | Jy km/s | 1 | para-H~2~O($4_{23}\text{--}3_{30}$) / 433 / 448.001 / $0.16\pm0.03$ |
| 448 GHz line luminosity in G09v1.97-R | 8.5e5 | not stated | Lsun | 2 | the 448 GHz ortho-H~2~O($4_{23}\text{--}3_{30}$) line has a luminosity of $8.5 \times 10^{5}$ $L_\odot$ |
| Core Tdust, size, Sigma_IR | ~100 K, ~100 pc, 8e12 | not stated | K, pc, Lsun/kpc^2 | 3 | resulting in an extreme IR luminosity surface density $\Sigma_\mathrm{IR}$ = $8\times10^{12}$ $L_\odot$ kpc$^{-2}$ |
| Disk component Tdust, L_IR, Sigma_IR | ~50 K, 5e12 Lsun, 4e11 Lsun/kpc^2 | not stated | K, Lsun, Lsun/kpc^2 | 3 | $L_{\mathrm{IR}}$ $\sim$ $5\times10^{12}$ $L_{\odot}$ and $\Sigma_\mathrm{IR}=4\times10^{11}$ $L_\odot$ kpc$^{-2}$ |
| Core water abundance X_H2O | (0.3-5)e-5 | 90% confidence interval | dimensionless | 3 | $X_{\mathrm{H_{2}O}}$ $\sim$ $(0.3\text{--}5)\times10^{-5}$ (90% confidence interval |
| Observed flux ratio F(1208)/F(448) | ≈11 | not stated | dimensionless | 2 | The observed flux ratio in G09v1.97-R is only $\approx$ 11 |
| Core surface SFR | 1.1e3 | not stated | Msun/yr/kpc^2 | 3 | surface star formation rate of $\sim$ $1.1\times10^{3}$ $M_\odot$ yr$^{-1}$ kpc$^{-2}$ |

## Qualitative findings

- 448 GHz line detected only in the red component (G09v1.97-R) at >=5 sigma  
  > "The 448 GHz H~2~O line is detected with $\gtrsim$ 5-$\sigma$ significance, but only in the red-shifted component" (4 Analysis and Discussion)

## Claim tuples

- H: Is the 448 GHz H2O line detectable at high z and does it trace a buried nucleus? | E: ALMA Band 3 observation of lensed SMG G09v1.97 | R: Line detected at >=5 sigma in R component | F: First high-z detection of the line | **supported**
- H: Does the ISM of G09v1.97-R need multiple components? | E: Joint fit of four H2O lines and continuum with 1 vs 2 components | R: chi2_red ≈4 for one, ≈0.9 for two | F: Extended optically thin disk plus compact warm optically thick core | **supported**
- H: Is the core an Eddington-limited starburst? | E: Compare core Sigma_IR and Tdust with models | R: Sigma_IR ~8e12 and 100 K vs ~1e13 and ~90 K | F: Radiation pressure on dust supports ISM in the nucleus | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Single-component model rejected (chi2_red ≈ 4)  
  > "results were unreliable with a best reduced chi-square value $\chi_\mathrm{red}^2$ $\approx$ 4" (4 Analysis and Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Models neglect spatially varying Tdust, which could lower inferred N_H2O; AGN contribution cannot be ruled out  
  > "our models do not include the effects of spatially varying $T_{\mathrm{dust}}$" (4 Analysis and Discussion)
- Caveat (inferred, ours): Continuum split between R and B relies on a CO(6-5)-based scaling
- Caveat (inferred, ours): Beam unresolved so structure is purely model-inferred
- Caveat (inferred, ours): Only four H2O lines constrain many parameters
- Caveat (inferred, ours): Gas-to-dust ratio fixed at 100

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Model library code and grids (in prep.)
- Missing: Continuum photometry values
- Missing: Lens model magnification curve
- Data volume (inferred): ~5-20 GB
- Score (inferred): 3/5, ALMA imaging recipe is brief but the main result depends on an unreleased model code and external data.
- Rediscovery candidate: no, Modelling code is unavailable and key inputs come from other works.

## Links

- Method: (cite: 2014A&A...567A..91G) (H2O excitation and dust model method)
- Companion: (cite: 2019A&A...624A.138Y) (High-resolution CO(6-5) and H2O(2_11-2_02) of G09v1.97)
- Companion: (cite: 2016A&A...595A..80Y) (NOEMA H2O lines)
- Related: Dense gas line survey ADS/JAO.ALMA#2018.1.00797.S

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
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 35,
  "rate": 0.53
 },
 "evidence_ok": true
}
```
