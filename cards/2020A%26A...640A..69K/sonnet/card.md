# Event Horizon Telescope imaging of the archetypal blazar 3C 279 at an extreme 20 microarcsecond resolution

`2020A&A...640A..69K` | Astronomy and Astrophysics 2020 | first author: Kim, Jae-Young | arXiv: - | DOI: 10.1051/0004-6361/202037493

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: agn_and_quasars
- Question: What is the fine-scale morphology and kinematics of the 3C 279 inner jet at 1.3 mm with 20 microarcsecond resolution EHT VLBI?  
  > "We use an ultra-high angular resolution technique – global Very Long Baseline Interferometry (VLBI) at 1.3 mm (230 GHz) – to resolve the" (abstract)
- Target **3C 279 (1253-055)**: coordinates _not stated_; z/distance z = 0.536  
  > "at a redshift of _z_ = 0.536 this corresponds" (abstract); distance from Marziani et al. 1996  
  > "at a redshift of _z_ = 0.536 this corresponds" (abstract)

## Data provenance

- ALMA projects: 2016.1.01154.V, 2016.1.01176.V
- bands: 1.3 mm (230 GHz), two 2 GHz bands centered at 227 and 229 GHz  
  > "The signals were recorded at two 2 GHz bands (centered" (2.1 Observations and calibration)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: EHT with phased ALMA; eight stations at six sites (ALMA, APEX, LMT, PV, SMT, JCMT, SMA, SPT)  
  > "A total of eight stations at six geographic" (2.1 Observations and calibration)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~20 µas  
  > "at an angular resolution of ∼20 µas" (abstract)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2017 April 5, 6, 10, 11  
  > "3C 279 was observed by the EHT on 2017 April 5, 6, 10," (2.1 Observations and calibration)
- pi or archival as stated: _not stated_
- Other facility **EHT (APEX, LMT, IRAM 30m, SMT, JCMT, SMA, SPT)**: 1.3 mm VLBI visibilities with ALMA  
  > "Large Millimeter Telescope Alfonso" (2.1 Observations and calibration)
- Other facility **VLBA-BU-BLAZAR 43 GHz and GMVA 86 GHz**: quasi-simultaneous larger-scale jet images for illustration  
  > "quasi-simultaneous observations by the VLBA-BU-BLAZAR 43 GHz" (3.1 First 230 GHz images)
- External data: ALMA phased-array spectral index alpha = -(0.6 ± 0.06) at 230 GHz  
  > "steep spectral index of α = −(0.6 ± 0.06) at 230 GHz (see Goddi et al. 2019)" (4.4 Low brightness temperature at 230 GHz) [from Goddi et al. 2019]

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

- Observations, data acquisition, calibration, validation  
  > "We refer to Papers II and III, and references therein" (2.1 Observations and calibration) [from EHT Papers II and III]
- Imaging pipelines and image averaging  
  > "We refer to Paper IV for the details of the imaging pipelines and" (2.2 Imaging and model-fitting analysis) [from EHT Paper IV]

### Not stated but needed to reproduce (our reading)

- Imaging pipeline parameters (weights, regularizers, masks) for Difmap, eht-imaging, SMILI
- Themis priors and sampler settings (Broderick et al. in prep.)
- Image alignment and averaging procedure details

## Analysis recipe

1. **Image reconstruction**: Three pipelines (Difmap CLEAN, eht-imaging, SMILI) on frequency-averaged EHT-HOPS data; 12 images averaged per epoch  
  > "to generate a total of 12 images of 3C 279 (i.e., one" (2.2 Imaging and model-fitting analysis)
   - software: Difmap, eht-imaging, SMILI
   - fitting: _not stated_
   - validation: Compared self-cal antenna gains across methods  
  > "Consistent gain corrections across independent imaging methods and model-fitting" (2.2 Imaging and model-fitting analysis)
2. **Gaussian model fitting**: Difmap modelfit and Themis time-variable ten-component Gaussian model  
  > "a fully time-variable, ten-component" (2.2 Imaging and model-fitting analysis)
   - software: Difmap, Themis
   - parameter: ~1.5% systematic amplitude errors  
  > "with ∼1.5% systematic" (3.3 Model-fitting results)
   - fitting: parallel-tempered affine-invariant MCMC; priors limit time variability; min FWHM 10 µas  
  > "A minimum component FWHM of 10 µas was required" (Appendix A)
   - validation: reduced chi2 ~1.3; consistent with individual-day fits  
  > "reduced χ [2] of ∼1.3" (3.3 Model-fitting results)
3. **Derive brightness temperatures and jet kinematics**: T_B from flux and sizes; bent-jet beta_app/Doppler/Lorentz factor analysis relative to C0-0  
  > "T_B = 1.22 × 10 [12] F/(ν [2] d_maj d_min ) K" (3.3 Model-fitting results)
   - assumption: H0 = 67.7, Om = 0.307; M_BH = 8e8 Msun; theta ~2 deg; alpha = -0.7  
  > "H0 = 67.7 km s [−][1] Mpc [−][1], Ω _m_ = 0.307" (1. Introduction)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **polconvert** : convert ALMA linear to circular polarization  
  > "software (Martí-Vidal et al. 2016) was applied to" (2.1 Observations and calibration)
- **Difmap** : CLEAN imaging, beams, modelfit  
  > "The beam sizes were obtained using `Difmap` and uniform" (Table 1)
- **eht-imaging** : regularized maximum likelihood imaging  
  > "(Chael et al. 2016, 2018), and `SMILI`" (2.2 Imaging and model-fitting analysis)
- **SMILI** : regularized maximum likelihood imaging  
  > "(Chael et al. 2016, 2018), and `SMILI`" (2.2 Imaging and model-fitting analysis)
- **Themis** : MCMC time-variable model fitting  
  > "parallel-tempered, affine invariant Markov" (2.2 Imaging and model-fitting analysis)
- **EHT-HOPS** : calibration pipeline supplying data  
  > "visibility data from" (2.2 Imaging and model-fitting analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Apparent speed C0-1 | 16 | +3/-2 | c | 3 | C0-1 16 |
| Apparent speed C0-2 | 20 | ±1 | c | 3 | C0-2 20 ± 1 |
| Reduced chi2 of Themis fit | ~1.3 | not stated | dimensionless | 2 | reduced χ [2] of ∼1.3 |
| Apparent brightness temperature | 10^10-11 | not stated | K | 3 | T B ∼ 10 [10][−][11] K |
| Minimum Lorentz factor | 20 | not stated | dimensionless | 3 | we constrain Γ ≥ 20 for both C0-1 and C0-2 |

## Qualitative findings

- Northern core elongated perpendicular to jet; consistent across days and methods  
  > "The elongated nuclear structure is consistent on all four" (abstract)

## Claim tuples

- H: Is the 1.3 mm structure of 3C 279 robust across days and methods? | E: Imaging with three pipelines and two model-fitting methods | R: Elongated multicomponent nuclear structure seen in all | F: Structure is robust | **supported**
- H: Do inner jet components indicate a bent jet? | E: Kinematics of components relative to C0-0 | R: Non-radial motions of ~15c and ~20c | F: Supports traveling shocks in a bent jet | **supported**
- H: Is the core optically thin at 1.3 mm? | E: Brightness temperature estimates | R: Intrinsic T_B ≲10^10 K | F: Core likely optically thin, or magnetically dominated | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Jet precession with ~22 yr period excluded by similar 2011 and 2017 structure  
  > "The mismatching periods would exclude this possibility." (4.3 Physical implications)
- How they decided it was enough: _not stated_
- Limitation (authors): Lack of short baselines limits recovery of extended emission  
  > "the 2017" (2.2 Imaging and model-fitting analysis)
- Caveat (inferred, ours): Few epochs and sparse uv coverage
- Caveat (inferred, ours): Kinematic reference choice affects inferred motions
- Caveat (inferred, ours): Doppler factor analysis assumes equal intrinsic fluxes

## Reproducibility

- Data public (paper): Data available at CDS and EHT website  
  > "https://eventhorizontelescope.org/for-astronomers/data" (abstract)
- Products in archive: _not stated_
- Missing: Pipeline settings in Paper IV
- Missing: Themis code and priors
- Missing: VLBI calibration details in Paper III
- Data volume (inferred): large (VLBI visibilities; released reduced data small)
- Score (inferred): 3/5, Data public but recipe depends on companion papers and non-public Themis code.
- Rediscovery candidate: no, Recipe incomplete and relies on EHT-specific pipelines.

## Links

- Method: Event Horizon Telescope Collaboration 2019d (Paper IV) (imaging pipelines)
- Method: Event Horizon Telescope Collaboration 2019c (Paper III) (calibration)
- Companion: Goddi et al. 2019 (ALMA phased-array data and spectral index)
- Related: VLBA-BU-BLAZAR
- Related: GMVA blazar monitoring

## Checks

```json
{
 "quotes": 41,
 "quotes_ok": 41,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 30,
  "rate": 0.441
 },
 "evidence_ok": true
}
```
