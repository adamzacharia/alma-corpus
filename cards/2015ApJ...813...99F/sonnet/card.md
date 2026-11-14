# Weak Turbulence in the HD 163296 Protoplanetary Disk Revealed by ALMA CO Observations

`2015ApJ...813...99F` | The Astrophysical Journal 2015 | first author: Flaherty, Kevin M. | arXiv: 1510.01375 | DOI: 10.1088/0004-637X/813/2/99

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: How strong is non-thermal (turbulent) gas motion in the HD 163296 disk, measured by forward-modeling visibilities of four CO lines?  
  > "We report a new constraint on the turbulence in the disk around HD 163296, a nearby young A star" (abstract)
- Target **HD 163296**: coordinates _not stated_; z/distance 122 pc  
  > "HD 163296 (=MWC 275) is a nearby (122 pc), 2.3 M$_{\odot}$, $\sim3$ Myr old A1 star (cite: mon09)" (Introduction); distance from Montesinos et al. 2009 (cite: mon09)  
  > "HD 163296 (=MWC 275) is a nearby (122 pc), 2.3 M$_{\odot}$, $\sim3$ Myr old A1 star (cite: mon09)" (Introduction)

## Data provenance

- ALMA projects: 2011.0.00010.SV
- bands: Band 6 and Band 7  
  > "Band 6 data were taken on 2012 June 9, 23, and July 7th when 24 12m antennas were available covering baselines of 20 to 400m." (The Data)
- frequencies and spectral setup: Band 6 SPWs at 217.105, 219.969, 230.969, 233.999 GHz (0.32-0.67 km/s); Band 7 SPWs at 360.169, 356.734, 345.796, 346.998 GHz (0.025-0.21 km/s)  
  > "The four spectral windows were centered on 217.105, 219.969, 230.969 and 233.999 GHz with bandwidths of 1.875, 0.937, 0.937, and 1.875 GHz" (The Data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 20 to 400 m, 24 12m antennas  
  > "when 24 12m antennas were available covering baselines of 20 to 400m" (The Data)
- angular resolution: Band 6 beam 0.81x0.65"; Band 7 beam 0.67x0.43"  
  > "The beam size is 0.81x0.65”, while the primary beam has a FWHM of 22”." (The Data); "The beam size is 0.67x0.43” with a primary beam size of 14”." (The Data)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: Band 6: 84 min; Band 7: 140 min  
  > "with a total on-source integration time of 84 minutes" (The Data); "The total on-source integration time was 140 minutes." (The Data)
- observing dates: Band 6: 2012 June 9, 23, July 7; Band 7: 2012 June 9, 11, 22, July 6  
  > "Band 7 data were taken on 2012 June 9, 11, 22, and July 6 with the same antenna configuration as the band 6 data." (The Data)
- pi or archival as stated: _not stated_
- Line: CO J=3-2 (not stated)
- Line: CO J=2-1 (not stated)
- Line: 13CO J=2-1 (not stated)
- Line: C18O J=2-1 (not stated)
- External data: Gas mass of 0.09 Msun from dust emission  
  > "Unless otherwise specified we assume $M_{\rm gas}$=0.09M$_{\odot}$ (cite: ise07)." (The Model) [from Isella et al. 2007 (cite: ise07)]
- External data: CO freeze-out temperature of 19 K  
  > "(cite: qi11) find a freeze out temperature of 19 K, which we take as the freeze-out boundary in our models." (The Model) [from Qi et al. 2011 (cite: qi11)]
- External data: ISM isotope ratios 12C/13C = 69 and 16O/18O = 557  
  > "we initially assume ISM values of $^{12}$C/$^{13}$C = 69 and $^{16}$O/$^{18}$O = 557 (cite: wil99)" (The Model) [from Wilson 1999 (cite: wil99)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Calibrated Science Verification data used  
  > "We use the calibrated Science Verification data; more details on the calibration procedure can be found on the NRAO website" (The Data)
- flux calibrator: Band 6: Juno, Neptune, Mars; Band 7: Juno, Neptune  
  > "Juno, Neptune, and Mars were used as amplitude calibrators" (The Data)
- flux scale uncertainty: 20% systematic assumed  
  > "which is within the expected 20% limit on the systematic uncertainty of the ALMA and SMA data" (Model Fitting)
- self calibration: None performed  
  > "We do not perform self-calibration" (The Data)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "we clean the central 14x14” with natural weighting and pixel sizes of 0.05”" (The Data)
- uv taper: _not stated_
- cell size: 0.05"  
  > "we clean the central 14x14” with natural weighting and pixel sizes of 0.05”" (The Data)
- image size: central 14x14"  
  > "we clean the central 14x14” with natural weighting and pixel sizes of 0.05”" (The Data)
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

- Disk model based on Rosenfeld et al. 2012/2013 and Dartois et al. 2003, including temperature functional form  
  > "This model is based on the work of (cite: ros12) and (cite: ros13), itself based on the structure laid out in (cite: dar03)" (The Model) [from (cite: ros12); (cite: ros13); (cite: dar03)]
- Photodissociation boundary definition  
  > "This is the same boundary used in (cite: qi11) with $\sigma_s$=0.79$\times$1.59$\times$10$^{21}$cm$^{-2}$." (The Model) [from (cite: qi11)]

### Not stated but needed to reproduce (our reading)

- Exact channel selection and line-free channels for the 2-1 lines
- Fixed offsets from phase center and velocity center values
- Which MIRIAD/CASA version and data export steps were used
- Fixed Zq0 for CO(2-1) etc. and prior ranges for parameters other than positivity
- Wide sky coordinates of the target
- Inclination/position angle sign conventions and temperature profile exponent for Zq
- Details of the cleaning routine (iterations, thresholds)

## Analysis recipe

1. **Prepare visibilities and uncertainties**: Use calibrated SV data; extract line channels; derive visibility weights from dispersion among 70 nearest uv points  
  > "We derive the uncertainties on the visibilities by calculating the the dispersion among the 70 visibility points with baselines closest to the particular uv point." (The Data)
   - parameter: CO(3-2) low-res binned to 0.3 km/s, central 15 channels; high-res 0.1 km/s, 101 channels  
  > "The low-resolution spectrum has been binned to a resolution of 0.3 km/s and includes only the central 15 channels." (The Data)
   - fitting: _not stated_
   - validation: Normalized residuals found Gaussian  
  > "we find that this method accurately estimates the errors and that these errors are Gaussian" (The Data)
2. **Forward model disk emission**: Parametric temperature and surface density structure, hydrostatic vertical structure, Keplerian plus pressure support velocity, LTE radiative transfer with thermal plus turbulent broadening; model visibilities by UVMODEL  
  > "We use the MIRIAD task UVMODEL to generate model visibilities sampled at the same spatial frequencies as the data." (Model Fitting)
   - software: MIRIAD
   - parameter: Fixed: d=122 pc, M*=2.3 Msun, PA=312 deg, Mgas=0.09 Msun, CO/H2=1e-4 (unless varied)  
  > "we keep the distance (d=122pc), stellar mass ($M_*$=2.3$M_{\odot}$) and position angle (PA=312$^{o}$) fixed" (The Model)
   - assumption: CO frozen out below 19 K and photodissociated above column threshold (abundance reduced by 8 orders of magnitude); LTE; mu=2.37  
  > "We simulate freeze-out by decreasing the CO abundance by eight orders of magnitude in regions where the gas temperature drops below 19 K." (The Model)
   - fitting: _not stated_
   - validation: _not stated_
3. **MCMC fit of each line and all four lines**: Chi-squared likelihood on visibilities, emcee affine-invariant sampler; flux scale factors s with 20% Gaussian prior in multiline fit  
  > "we employ the affine-invariant routine EMCEE (cite: for13) based on the algorithm originally presented in (cite: goo10)" (Model Fitting)
   - software: emcee
   - parameter: Typically 40 walkers, 3000 steps; CO(3-2) 1500 steps with 1000 burn-in; multiline 60 walkers, 1000 steps, 500 burn-in  
  > "For this MCMC trial we employ 60 walkers over 1000 steps, with the first 500 removed as burn-in." (Multi-line fit)
   - assumption: Mgas, Rc, vturb positive with uniform priors  
  > "We require that $M_{\rm gas}$, $R_c$, and $v_{\rm turb}$ are positive with uniform priors across the parameter space." (Model Fitting)
   - fitting: chi-squared likelihood; median and 3 sigma ranges reported  
  > "The goodness of fit between the model (V$_{\rm mod}$) and observed (V$_{\rm obs}$) visibilities is calculated using the chi-squared statistic" (Model Fitting)
   - validation: Reduced chi-squared, residual channel maps, tests with flux scale 0.8/1.2, distance 112/132 pc, vturb fixed at 0.1 km/s  
  > "we run an additional MCMC fit to the low-resolution CO(3-2) data with $v_{\rm turb}$ fixed at 0.1 km s$^{-1}$ while allowing the other model parameters to vary" (Turbulence)
4. **Convert turbulence limits to alpha**: alpha ~ (vturb/cs)^2  
  > "The form of this equation suggests that $\alpha\sim$($v_{\rm turb}$/c$_s$)$^2$" (Implications of weak turbulence)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **MIRIAD** : UVMODEL to sample model at data uv points  
  > "We use the MIRIAD task UVMODEL to generate model visibilities sampled at the same spatial frequencies as the data." (Model Fitting)
- **emcee** : MCMC posterior sampling  
  > "we employ the affine-invariant routine EMCEE (cite: for13)" (Model Fitting)
- **Astropy** : acknowledged as used in research  
  > "This research made use of Astropy, a community-developed core Python package for Astronomy (cite: ast13)." (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| vturb upper limit, CO(3-2) high-res | <0.031 cs | 3 sigma | cs | 3 | $<$0.031 |
| vturb upper limit, CO(3-2) low-res | <0.038 cs | 3 sigma | cs | 3 | $<$0.038 |
| vturb upper limit, multiline fit | <0.16 cs | 3 sigma | cs | 3 | We find a three-sigma upper limit of $<$0.16c$_s$ |
| vturb upper limits CO(2-1), 13CO, C18O | <0.31, <0.34, <0.40 | 3 sigma | cs | 3 | ($<31\%$c$_s$,$<34\%$c$_s$,$<40\%$c$_s$ respectively) |
| alpha upper limit from CO(3-2) | <9.6e-4 | not stated | dimensionless | 4 | our CO(3-2) observations correspond to an upper limit of $\alpha<9.6\times10^{-4}$ |
| CO depletion factor relative to ISM (multiline) | 4.9 | +0.6/-0.4 | dimensionless | 3 | We find that CO is depleted by a factor of 4.9$^{+0.6}_{-0.4}$ relative to the canonical ISM value. |
| Radial temperature index q (CO(3-2) high-res) | -0.278 | +0.003/-0.008 | dimensionless | 3 | -0.278$^{+0.003}_{-0.008}$ |

## Qualitative findings

- Turbulence in the outer disk upper layers is far below MRI simulation predictions and below the level implied by accretion rate  
  > "Our limits also fall below predictions from numerical simulations of the MRI, suggesting that MRI is less efficient in the outer disk than previously thought." (Conclusions)

## Claim tuples

- H: Is there strong non-thermal motion in the HD 163296 outer disk? | E: Forward-model CO(3-2) visibilities with MCMC | R: vturb<0.031 cs (3 sigma) | F: Turbulence is weak, below MRI predictions | **supported**
- H: Do other lines and a joint fit agree? | E: Fit CO(2-1), 13CO, C18O and all four lines together | R: Limits of 0.31-0.40 cs individually, <0.16 cs jointly | F: Consistent with low turbulence, weaker constraints from lower resolution and optically thin lines | **supported**
- H: Is weak turbulence compatible with the high accretion rate? | E: Compare alpha limit with accretion-implied alpha | R: alpha<9.6e-4 vs 0.06-0.3 implied | F: Incompatible; alpha radially dependent or angular momentum removed otherwise | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Fitting full 3D visibilities uses spatial information, giving stronger diagnostic power than line broadening alone  
  > "This behavior indicates that fitting a model to the full data set has a stronger diagnostic power than the broadening of the line in the spectral domain." (Turbulence)
- Alternative: Reported upper limit rather than detection because unmodeled features (asymmetry, eccentricity) may be absorbed by turbulence  
  > "For this reason we choose to report our turbulence results as an upper limit rather than a detection." (Turbulence)
- How they decided it was enough: _not stated_
- Limitation (authors): Parametric temperature structure cannot capture asymmetries; turbulence may be inflated; degeneracies between Tatm0 and Zq0, q and Rc  
  > "The end result is a high value of turbulence, and a worse fit to the peak-to-trough ratio, due to limitations of the assumed temperature structure" (CO(2-1))
- Caveat (inferred, ours): Gas temperature is parameterized, not computed, so limits depend on functional form
- Caveat (inferred, ours): Zq0 fixed at 70 AU for CO(3-2)
- Caveat (inferred, ours): Mgas fixed from dust, degenerate with CO/H2
- Caveat (inferred, ours): No self-calibration
- Caveat (inferred, ours): Turbulence assumed isotropic and scaling with cs

## Reproducibility

- Data public (paper): ALMA Science Verification data, calibrated products on NRAO website  
  > "We use the calibrated Science Verification data; more details on the calibration procedure can be found on the NRAO website" (The Data)
- Products in archive: _not stated_
- Missing: Model code not released
- Missing: Prior bounds and initial walker ranges
- Missing: Exact channel selection for J=2-1 lines
- Missing: Software versions
- Data volume (inferred): Tens of GB (SV measurement sets for Bands 6 and 7)
- Score (inferred): 3/5, Public SV data and clear model description with tables, but the custom model code is not released and several settings are missing.
- Rediscovery candidate: no, Requires reimplementing a custom disk radiative transfer model and MCMC; code not provided.

## Links

- Method: Rosenfeld et al. 2013 (cite: ros13) (Disk model with temperature structure used for HD 163296)
- Method: Foreman-Mackey et al. 2013 (cite: for13) (emcee sampler)
- Companion: Simon et al. 2015 in prep (cite: sim15) (MRI simulations and synthetic observations compared)
- Related: ALMA Science Verification

## Checks

```json
{
 "quotes": 59,
 "quotes_ok": 59,
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
  "facts": 71,
  "stated": 41,
  "rate": 0.577
 },
 "evidence_ok": true
}
```
