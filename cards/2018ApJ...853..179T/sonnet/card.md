# PHIBSS: Unified Scaling Relations of Gas Depletion Time and Molecular Gas Fractions

`2018ApJ...853..179T` | The Astrophysical Journal 2018 | first author: Tacconi, L. J. | arXiv: 1702.01140 | DOI: 10.3847/1538-4357/aaa4b4

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies, nearby_galaxies
- Question: Do molecular gas masses from CO, Herschel dust SEDs and ~1mm dust photometry follow the same scaling relations of depletion time and gas fraction with redshift, offset from the main sequence and stellar mass, once zero-point offsets are minimized?  
  > "This paper provides an update of our previous scaling relations (Genzel et al. 2015) between galaxy integrated molecular gas masses, stellar masses and star formation rates" (abstract)
- Target **Compilation of 1444 star-forming galaxies (z=0-4.4)**: coordinates _not stated_; z/distance z=0 to 4.4  
  > "The data used in this work comprise a total of 1444 measurements of molecular mass, spanning a wide redshift range z=0 to 4.4" (3. Data Sets Entering this Analysis); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00092.S
- bands: _not stated_
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
- Line: CO 1-0, 2-1, 3-2 (4-3 in two cases) (not stated)
- Other facility **IRAM NOEMA/PdBI and 30m**: CO detections from PHIBSS1/2, xCOLD GASS and others  
  > "97 detections of CO 2-1 or 3-2 in main sequence SFGs between z=0.5 and 2.7, as part of the PHIBSS2 survey with the updated IRAM NOEMA interferometer" (3.1 CO observations)
- Other facility **Herschel**: FIR dust SED stacks (PACS/SPIRE)  
  > "stacks of z=0.1-1.9 SFGs with deep Herschel PACS/SPIRE spectro-photometry in the COSMOS and GOODS (N/S) fields" (3.2 Dust observations)
- External data: 1mm ALMA dust continuum fluxes/gas masses for 102 detections and 21 stacks  
  > "102 detections and 21 stacks of z=0.9-4.4 of 850-1300 μm continuum fluxes from recent ALMA observations" (3.2 Dust observations) [from Scoville et al. 2016, Dunlop et al. 2017, DeCarli et al. 2016, Barro et al. 2016, Tadaki et al. 2015, 2017]
- External data: Herschel FIR SED dust masses from stacks  
  > "In all cases we adopted dust masses from these references, and converted to gas mass as described in Sect 2.1." (3.2 Dust observations) [from Magnelli et al. 2014, Berta et al. 2016, G15, Santini et al. 2014, Béthermin et al. 2015]

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

- alpha_CO metallicity recipe, mass-metallicity relation and CO gas-mass calculation follow G15  
  > "Molecular gas masses are then computed from equation (4) in G15." (2.3 Determining Molecular Gas Masses) [from Genzel et al. 2015 (G15)]
- 1mm dust gas masses use Scoville et al. (2016) methodology with Tdust=25 K  
  > "using the methodology and calibration proposed by Scoville et al. (2016) with T dust =25K=const." (3.2 Dust observations) [from Scoville et al. 2016]
- Main-sequence prescription adopted from S14  
  > "We adopt in this study the prescription proposed by S14," (1. Gas and Galaxy Evolution) [from Speagle et al. 2014]

### Not stated but needed to reproduce (our reading)

- Full online table of 1444 measurements (only 14 rows printed)
- Exact fitting code and bootstrap/jackknife details
- ALMA data reduction for the 10 ALMA CO detections (Genzel et al. in prep)

## Analysis recipe

1. **Assemble and homogenize sample**: Compile CO, FIR-SED and 1mm gas masses; common ladder SFR/M*, S14 main sequence, alpha_CO and gas-to-dust metallicity corrections  
  > "Wherever necessary and possible, we adjusted the stellar masses and SFRs from the literature to the same assumptions." (3.4 Stellar Masses and Star Formation Rates)
   - assumption: Chabrier IMF, flat LCDM Om=0.3, H0=70  
  > "flat Λ CDM Universe with Ω m =0.3 and H 0 =70 km/s/Mpc used throughout this paper" (1. Gas and Galaxy Evolution)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit scaling relations**: Multi-parameter linear regression in log space, weighted by inverse square uncertainties, with per-method zero-point corrections  
  > "we employ multi-parameter linear regression fitting in 3-, 4- or 5-space of logarithmic variables" (4.2 New Results for Depletion Time Scaling Relations)
   - fitting: Error-weighted least squares  
  > "for quantitative fitting of the data, we employ multi-parameter linear regression fitting in 3-, 4- or 5-space of logarithmic variables (log( 1+z), log 2 (1+z), log δMS, log δM * , log δR e ) using all data points individually, weighted by the inverse square of their uncertainties" (4.2 New Results for Depletion Time Scaling Relations)
   - validation: Random half-splitting bootstrap, jackknife, Monte-Carlo mock tests (Appendix A)  
  > "We determined the uncertainties in Table 3a by splitting the sample randomly into two halves, fitting the parameters" (4.2 New Results for Depletion Time Scaling Relations)

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Slope of tdepl vs log(1+z) (Bt) | -0.62 | 0.13 | dimensionless | 2 | -0.620.13 |
| Slope of tdepl vs deltaMS (Ct) | -0.44 | 0.04 | dimensionless | 2 | t depl ~( sSFR/sSFR (MS)) [-0.44±0.03] |
| Slope of mu_gas vs deltaMS | 0.52 | 0.03 | dimensionless | 2 | +0.520.03 |
| Number of measurements in final fit | 1309 | not stated | galaxies/stacks | 1 | The final data set used in our global analysis of μ gas thus has 1309 measurements. |

## Qualitative findings

- CO, FIR-SED and 1mm dust methods give consistent scaling trends after modest zero-point adjustments (0-0.21 dex).  
  > "if modest (0-0.21 dex) adjustments are made to the zero points of each of the techniques and data sets" (5. Summary and Discussion)

## Claim tuples

- H: Different gas mass methods yield consistent scaling relations | E: Joint fits of CO, dust-FIR and dust-1mm samples with zero-point offsets | R: Common slopes Bt=-0.62, Ct=-0.44 with scatter ~0.07-0.1 dex | F: Methods converge on consistent relations | **supported**
- H: tdepl and mu_gas depend on optical size or surface density | E: Residual fits vs Re and direct fit vs SFR surface density | R: Et=0.11±0.1; weak residual dependence | F: No or weak size dependence, but optical sizes may be inadequate | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Optical sizes may not represent molecular/dust radii; low-mass results sensitive to alpha_CO metallicity dependence.  
  > "Optical sizes may not represent the true molecular/dust effective radii" (4.2.4 Size dependence)
- Caveat (inferred, ours): Compilation heterogeneity; zero-point offsets are fitted rather than independently calibrated
- Caveat (inferred, ours): ALMA is a minor data component

## Reproducibility

- Data public (paper): Full table available online at PHIBSS2 website  
  > "The full table will be available online at http://www.iram.fr/~phibss2/Home.html." (3. Data Sets Entering this Analysis)
- Products in archive: _not stated_
- Missing: Full data table not in text
- Missing: Fitting code not given
- Data volume (inferred): Negligible (literature table); ALMA raw data not reprocessed
- Score (inferred): 45/5, Compilation analysis from tabulated values with stated equations, but input table is external and ALMA is minor.
- Rediscovery candidate: no, ALMA data are a minor input; results rely on literature compilation.

## Links

- Method: Genzel et al. 2015 (Previous scaling relations and gas mass recipes)
- Method: Scoville et al. 2016 (1mm dust method)
- Companion: Freundlich et al. 2018 (PHIBSS2 CO data)
- Related: PHIBSS1
- Related: PHIBSS2
- Related: xCOLD GASS

## Checks

```json
{
 "quotes": 26,
 "quotes_ok": 26,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 1,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 59,
  "stated": 17,
  "rate": 0.288
 },
 "evidence_ok": true
}
```
