# Mass constraint for a planet in a protoplanetary disk from the gap width

`2016PASJ...68...43K` | Publications of the Astronomical Society of Japan 2016 | first author: Kanagawa, Kazuhiro D. | arXiv: 1603.03853 | DOI: 10.1093/pasj/psw037

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: protoplanetary_disks
- Question: How can the mass of a planet embedded in a protoplanetary disk be constrained from the observed gap width, and what planet masses follow for the HL Tau gaps?  
  > "Further investigation have been required in order to constrain the planet mass from the width of the observed gaps." (Introduction)
- Target **HL Tau**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00015.SV
- bands: Band 6 and Band 7 brightness temperatures used  
  > "using the brightness temperatures in Band 6 and 7, we obtain the optical depth in Band 6 and the gas temperature" (4 Application to HL Tau disk)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- External data: HL Tau ALMA Long Baseline Campaign dust continuum observations (gaps)  
  > "clear axisymmetric gaps in HL Tau disk are discovered in the dust thermal emission by the Long Baseline Campaign of ALMA" (4 Application to HL Tau disk) [from ALMA Partnership, Brogan et al. 2015 (cite: ALMA_HLTau2015)]
- External data: Hydrodynamic simulation data from Dong et al. 2015, shared by the author  
  > "We thank Ruobing Dong for giving us his data." (Acknowledgments) [from (cite: Dong_Zhu_Whitney2015)]
- Simulation/model as data: 26 runs of 2D hydrodynamic simulation with FARGO, Mp 0.1-2 MJ, h/R 1/30-1/15, alpha 1e-2 to 1e-4  
  > "We perform $26$ runs of the hydrodynamic simulation for various planetary masses ($0.1 M_J$ – $2 M_J$, if $M_{\ast}=1M_{\odot}$)" (2 Numerical method)

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

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
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
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Optical depth and gas temperature derived from Band 6 and 7 brightness temperatures for assumed beta, as in Paper I  
  > "As done in Paper I, using the brightness temperatures in Band 6 and 7, we obtain the optical depth in Band 6 and the gas temperature" (4 Application to HL Tau disk) [from Paper I (cite: Kanagawa2015b)]
- Gap depth relation Sigma_min/Sigma_0 = 1/(1+0.04K)  
  > "the gap depth is related with the planetary mass, the disk aspect ratio (temperature), and the viscosity" (Introduction) [from Paper I (cite: Kanagawa2015b)]

### Not stated but needed to reproduce (our reading)

- The ALMA continuum images, radial profile extraction and beam/resolution used for HL Tau brightness temperatures are not described
- Method to convert brightness temperatures to optical depth and temperature is only referred to Paper I
- Opacity values and the exact fit procedure for tau_unp
- Distance to HL Tau
- Numerical details of FARGO runs (table of models not given in text)

## Analysis recipe

1. **Run hydrodynamic gap simulations**: 2D FARGO simulations of planet-disk interaction over a grid of Mp, h/R, alpha  
  > "using the two–dimensional hydrodynamic code FARGO (cite: Masset2000)" (2 Numerical method)
   - software: FARGO
   - parameter: Domain R/Rp 0.4-4.0 with 1024x2048 zones; smoothing length 0.6 hp; 1e4-1e5 orbits  
  > "The computational domain ranges from $R/R_p=0.4$ to $4.0$ with $1024 \times 2048$ radial and azimuthal zones." (2 Numerical method)
   - assumption: No gas accretion onto planet, fixed circular orbit, constant nu and h/R  
  > "we neglect the gas accretion onto the planet and the planets rotates on the fixed orbit with $R=R_p$" (2 Numerical method)
   - fitting: _not stated_
   - validation: Checked smoothing length does not significantly influence gap width  
  > "We have checked that the choice of the smoothing length does not significantly influence the gap width." (2 Numerical method)
2. **Derive empirical gap-width formula**: Gap defined where azimuthally averaged surface density is below half of initial; width R_out-R_in; scaling with K'  
  > "We define the gap region by the radial extent where the azimuthally averaged surface density is smaller than the half of the initial surface density." (3.1 Empirical formula for the gap width)
   - fitting: Power-law fit giving Delta_gap/Rp = 0.41 K'^(1/4)  
  > "= 0.41 K'^{1/4}" (3.1 Empirical formula for the gap width)
   - validation: Compared with Varniere et al. 2004 and Duffell & MacFadyen 2013  
  > "is reasonably consistent with that given by hydrodynamic simulations by (cite: Varniere_Quillen_Frank2004) and (cite: Duffell_MacFadyen2013)." (3.1 Empirical formula for the gap width)
3. **Measure HL Tau gap widths and estimate planet masses**: Fit tau outside gaps as unperturbed profile, edges at intersections with tau_unp/2, Rp=(Rin+Rout)/2, then apply mass formula  
  > "The locations of the inner and outer gap edges, $R_{\rm in}$ and $R_{\rm out}$, are determined by intersection points with $\tau^{\rm unp}/2$" (4 Application to HL Tau disk)
   - parameter: tau_unp = 9.5 (R/1AU)^-0.4  
  > "The optical depth outside the gaps can be fitted by $\tau^{\rm unp} = 9.5(R/1\mbox{AU})^{-0.4}$" (4 Application to HL Tau disk)
   - assumption: alpha=1e-3, beta=1.5, M*=1 Msun; constant opacity; gas and dust gap widths similar (weak dust filtration)  
  > "We assume that the gap widths of the gas and dust disks are similar." (4 Application to HL Tau disk)
   - fitting: _not stated_
   - validation: 30 AU result consistent with gap-depth estimate of Paper I; compared with Dong et al. and Jin et al.  
  > "The estimated mass of the planet at $30$AU gap is consistent with that estimated from the gap depth in Paper I." (4 Application to HL Tau disk)

## Software

- **FARGO** : 2D hydrodynamic simulations of disk-planet interaction  
  > "using the two–dimensional hydrodynamic code FARGO (cite: Masset2000)" (2 Numerical method)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Gap width coefficient | 0.41 | not stated | dimensionless | 2 | = 0.41 K'^{1/4} |
| Planet mass, 10 AU gap (beta=1.5, alpha=1e-3) | 1.4 | not stated | M_J | 3 | The planet masses for the gaps at $10$AU, $30$AU and $80$AU are estimated to be $1.4 M_J$, $0.2 M_J$ and $0.5 M_J$ from the gap widths |
| Planet mass, 30 AU gap | 0.2 | not stated | M_J | 3 | The planet masses for the gaps at $10$AU, $30$AU and $80$AU are estimated to be $1.4 M_J$, $0.2 M_J$ and $0.5 M_J$ from the gap widths |
| Planet mass, 80 AU gap | 0.5 | not stated | M_J | 3 | The planet masses for the gaps at $10$AU, $30$AU and $80$AU are estimated to be $1.4 M_J$, $0.2 M_J$ and $0.5 M_J$ from the gap widths |
| Innermost gap mass for beta=1 (beta=2) | 3.3 (1.3) | not stated | M_J | 3 | the planet mass is estimated to be $3.3M_J$ ($1.3M_J$) if $\beta=1$ ($2$) from the gap width |

## Qualitative findings

- Gap width scales as Mp^(1/2), (h/R)^(-3/4), alpha^(-1/4)  
  > "The gap width is proportional to the square root of the planet mass, $-3/4$ power of the disk aspect ratio and $-1/4$ power of the viscosity." (abstract)
- Mass estimate from gap width is less affected by resolution and dust filtration than from gap depth  
  > "The estimate of planet masses from the gap widths is less affected by the observational resolution and dust filtration than that from the gap depth." (abstract)

## Claim tuples

- H: Gap width can be scaled with planet mass, aspect ratio and viscosity to constrain planet mass | E: 26 FARGO runs; width measured at half initial surface density | R: Delta_gap/Rp = 0.41 K'^(1/4) | F: Planet mass can be estimated from observed gap width | **supported**
- H: HL Tau gaps can be explained by planets of constrained mass | E: Apply formula to ALMA-derived optical-depth gaps at 10, 30, 80 AU | R: 1.4, 0.2, 0.5 MJ | F: Masses depend on beta, Rp and M*, but are estimated by gap width | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Gap width is easier to measure than depth  
  > "In contrast, the gap width can be more easily measured than the gap depth." (Introduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Estimates depend on beta (dust particle size) and dust filtration model  
  > "Our estimate depends on the particle size of dusts (i.e., the dust opacity index of $\beta$) and the disk model for the dust filtration." (Summary)
- Caveat (inferred, ours): Gaps assumed planet-induced and single planet each
- Caveat (inferred, ours): Dust gap width assumed equal to gas gap width
- Caveat (inferred, ours): No uncertainties on planet masses
- Caveat (inferred, ours): Constant stellar mass of 1 Msun and alpha=1e-3 assumed

## Reproducibility

- Data public (paper): ALMA science verification data cited  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00015.SV." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Table of model parameters and measured widths not included in text
- Missing: HL Tau radial profiles and temperature/optical depth derivation details
- Missing: Distance to HL Tau
- Data volume (inferred): Small if using published HL Tau images; simulations require significant compute
- Score (inferred): 3/5, Simulation setup and formulas are well specified, but the ALMA data processing is only inherited from Paper I and numerical tables are missing.
- Rediscovery candidate: no, ALMA role is minor and the ALMA-derived profiles are not specified well enough to redo the full recipe.

## Links

- Method: Masset 2000 (cite: Masset2000) (FARGO code)
- Companion: Kanagawa et al. 2015 ApJL 806 L15 (cite: Kanagawa2015b) (Paper I: gap depth relation and HL Tau mass estimate)
- Related: ALMA HL Tau Long Baseline Campaign

## Checks

```json
{
 "quotes": 34,
 "quotes_ok": 34,
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
  "facts": 65,
  "stated": 24,
  "rate": 0.369
 },
 "evidence_ok": true
}
```
