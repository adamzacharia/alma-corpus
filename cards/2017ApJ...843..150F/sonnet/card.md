# A Three-dimensional View of Turbulence: Constraints on Turbulent Motions in the HD 163296 Protoplanetary Disk Using DCO<SUP>+</SUP>

`2017ApJ...843..150F` | The Astrophysical Journal 2017 | first author: Flaherty, Kevin M. | arXiv: 1706.04504 | DOI: 10.3847/1538-4357/aa79f9

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: How strong is turbulence (non-thermal motion) at different vertical layers of the HD 163296 disk, probed with DCO+, C18O and CO, and what is the radial distribution of DCO+?  
  > "Radio observations of resolved molecular line emission can directly measure this non-thermal motion and, taking advantage of the layered chemical structure of disks, different molecular lines can be combined to map the turbulence" (abstract)
- Target **HD 163296**: coordinates _not stated_; z/distance 122 pc  
  > "We also assume a distance ($d$=122 pc), stellar mass (cite: mon09), and disk mass ($M_{\rm gas}$=0.09$M_{\odot}$)." (Disk Structure Model); distance from van Leeuwen 2007 (~10% uncertainty)  
  > "We also assume a distance ($d$=122 pc), stellar mass (cite: mon09), and disk mass ($M_{\rm gas}$=0.09$M_{\odot}$)." (Disk Structure Model)

## Data provenance

- ALMA projects: 2013.1.00366.S, 2011.0.00010.SV
- bands: _not stated_
- frequencies and spectral setup: 4 SPWs: CO(2-1), DCO+(3-2), C18O(2-1) with 3840 channels of 20 m/s; continuum SPW at 232.71 GHz, 128 channels  
  > "The spectral windows centered on line emission had 3840 channels, each 0.015 MHz (20 m s$^{-1}$) wide." (2 Data)
- continuum bandwidth: 2 GHz  
  > "The continuum spectral window had a total bandwidth of 2 GHz covered by 128 channels." (2 Data)
- arrays: _not stated_
- configurations: _not stated_
- baselines: 10 to 480 kλ  
  > "Baselines ranged from 10k$\lambda$ to 480k$\lambda$, corresponding to a spatial resolution of $\sim0.5\ensuremath{''}$." (2 Data)
- angular resolution: ~0.5'' lines (0.58x0.47 CO), ~0.4'' continuum  
  > "resulting in beam sizes of $\sim0.5\ensuremath{''}$ and $\sim0.4\ensuremath{''}$ respectively" (2 Data)
- max recoverable scale: _not stated_
- sensitivity: rms 6.5 (CO), 1.4 (C18O), 1.1 (DCO+) mJy/beam per 0.2 km/s channel  
  > "| DCO$^+$(3-2) | 0.21 km s$^{-1}$$^{a}$ | 0$\ensuremath{''}$59x0$\ensuremath{''}$50$^{b}$ | 89.6$^{\circ}$ | 1.1 |" (Table 1)
- time on source: 52 minutes per night  
  > "During each night the on-source integration time was 52 minutes" (2 Data)
- observing dates: 2014 June 4, 14, 16, 17 and 29  
  > "taken over the course of five nights (2014 June 4, 14, 16, 17 and 29)" (2 Data)
- pi or archival as stated: _not stated_
- Line: DCO+ 3-2 (not stated)
- Line: C18O 2-1 (not stated)
- Line: CO 2-1 (not stated)
- Other facility **ALMA Science Verification (2011.0.00010.SV)**: DCO+(5-4) and Band 7 continuum data  
  > "we extracted DCO$^+$(5-4) and Band 7 continuum data from the ALMA Science Verification observations of HD 163296" (2 Data)
- External data: Temperature structure from CO(3-2): q=-0.216, Rc=194 au, Tatm0=94 K, gamma=1, Tmid0=17.5 K  
  > "We use the temperature parameters derived in (cite: fla15) from the CO(3-2) emission" (Disk Structure Model) [from (cite: fla15)]
- External data: Disk gas mass 0.09 Msun from dust continuum with gas-to-dust 100  
  > "The disk mass was taken from (cite: ise07), who used continuum observations of sub-mm dust emission to derive a dust mass" (Disk Structure Model) [from (cite: ise07)]
- External data: Isotope ratios 18O/16O=557, 13C/12C=69  
  > "We assume isotope abundances of $^{18}$O/$^{16}$O=557 and $^{13}$C/$^{12}$C=69 (cite: wil99)." (Disk Structure Model) [from (cite: wil99)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 20% assumed amplitude calibration uncertainty  
  > "Throughout our analysis we assume a 20% uncertainty on the amplitude calibration of our data." (2 Data)
- self calibration: Self-calibrated using the continuum spectral window; SV data per Band 7 CASA guide  
  > "Data were self-calibrated using the continuum spectral window." (2 Data)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: robust weighting (robust=0.5) lines; uniform for continuum  
  > "$^{b}$ Derived with robust=0.5 $^{c}$ Derived with uniform weighting" (Table 1)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Keplerian-disk-based clean mask for CO(2-1)  
  > "A clean mask based on the emission pattern of a Keplerian disk was applied to the CO(2-1) data." (2 Data)
- multiscale scales: _not stated_
- continuum subtraction: Spectral line data continuum-subtracted and binned by factor of 10 to 0.2 km/s  
  > "The spectral line data were continuum-subtracted and binned by a factor of 10, to 0.2 km s$^{-1}$ wide channels" (2 Data)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Modeling code and disk structure model  
  > "The modeling code comes from (cite: fla15), which is based on earlier work by (cite: ros13) and (cite: dar03)." (Disk Structure Model) [from (cite: fla15)]
- SV DCO+(5-4) self-calibration  
  > "with self-calibration applied based on the HD 163296 Band 7 Science Verification CASA guide" (2 Data) [from HD 163296 Band 7 Science Verification CASA guide]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration pipeline/manual details
- Self-calibration solution intervals
- Line-free channels and continuum-subtraction order
- Cell and image size, clean thresholds
- Model grid resolution and visibility weighting/ UV range in fits
- Stellar mass value used
- Initial walker positions and prior ranges
- Source coordinates

## Analysis recipe

1. **Deconvolve radial DCO+ structure**: Richardson-Lucy-like deconvolution with Keplerian rings across the PPV cube  
  > "we employ an image deconvolution routine modeled after (cite: luc74) and (cite: sco83)" (3 Initial DCO+ Morphology Estimate)
   - fitting: _not stated_
   - validation: _not stated_
2. **Estimate DCO+ excitation temperature**: Line ratios of DCO+(3-2) vs (5-4) and (4-3)  
  > "we find a temperature of 16$\pm$4 K and 11$\pm$4 K when comparing DCO$^+$(3-2) to DCO$^+$(5-4) and DCO$^+$(4-3) respectively" (3 Initial DCO+ Morphology Estimate)
   - assumption: LTE; 20% amplitude calibration uncertainty  
  > "This calculation assumes LTE, which is likely applicable for DCO$^+$." (3 Initial DCO+ Morphology Estimate)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit parametric disk model to visibilities with MCMC**: Ray-traced models converted to visibilities, chi-squared comparison, MCMC for posteriors  
  > "model images are generated and converted to visibilities using the MIRIAD task UVMODEL. The model visibilities are then directly compared to the data" (Disk Structure Model)
   - software: MIRIAD, emcee
   - parameter: 80 walkers, 1000 steps, first 500 burn-in  
  > "Our chains typically consist of 80 walkers and 1000 steps, with the first 500 removed as burn-in." (Disk Structure Model)
   - assumption: d=122 pc, PA=312 deg, Mgas=0.09 Msun, XCO=1e-4 for CO, LTE, ring sigma=0.1 R, v_turb proportional to sound speed  
  > "The position angle is fixed (PA=312$^{\circ}$) but inclination is allowed to vary between the three molecules" (Disk Structure Model)
   - fitting: emcee affine-invariant sampler; simple physical priors (vturb>0); linear spacing except log Rc  
  > "Simple, physical, priors are employed (e.g. $v_{\rm turb}>0$) and we employ linear spacing in all parameters except $R_c$, where we fit $\log(R_c)$." (Disk Structure Model)
   - validation: Residual moment maps; chi-squared; AIC comparison  
  > "a moment 0 (total-intensity) map of the residuals (subtracted in the visibility domain and imaged using the clean algorithm) only shows small 3$\sigma$ features" (5.1 DCO+)
4. **Test systematics for DCO+ turbulence limit**: Reruns with narrow rings, variable ring width, free Tmid0 (with DCO+(5-4)), and sys scale factor 0.8-1.2  
  > "we introduce an additional parameter, $sys$, that is a multiplicative scale factor on the amplitude of the model emission." (5.1 DCO+)
   - software: emcee
   - fitting: _not stated_
   - validation: Akaike Information Criterion rejects narrow rings at >10 sigma  
  > "We find that the fit is significantly worse, a $>10\sigma$ difference according to the Akaike Information Criterion" (5.1 DCO+)
5. **Fit C18O(2-1) and CO(2-1) with double power-law temperature**: Same MCMC modeling with Rbreak and q_in added to capture inner excess; C18O fixed Rc, Tatm0, Tmid0; CO(2-1) free temperature  
  > "To accommodate this behavior we explore models with a double power law temperature structure." (5.2 C18O(2-1))
   - software: emcee, MIRIAD
   - parameter: CO freeze-out below 19 K; depletion factor 5 for C18O, 8 orders for CO  
  > "Freeze-out occurs below a temperature of 19 K" (Disk Structure Model)
   - fitting: _not stated_
   - validation: Residual maps; test with 25 K snow line; test with dust included in uncontinuum-subtracted C18O  
  > "We run an MCMC trial with with the CO snow line occurring at 25 K, instead of 19 K in the fiducial model" (5.2 C18O(2-1))
6. **Convert limits to alpha and map emission heights**: alpha ~ (vturb/cs)^2; heights containing 5% and 95% of emission along each line of sight in best-fit model  
  > "along each line of sight through the disk we calculate the heights above which 5% and 95% of the emission arises" (6 Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **MIRIAD** : UVMODEL to convert model images to visibilities  
  > "model images are generated and converted to visibilities using the MIRIAD task UVMODEL" (Disk Structure Model)
- **emcee** : MCMC posterior sampling  
  > "we employ the MCMC routine EMCEE (cite: for13)" (Disk Structure Model)
- **corner** triangle.py v0.1.1: Posterior distribution plots  
  > "generated using the python module corner (cite: for14)" (5.1 DCO+)
- **CASA** : Self-calibration of SV data following CASA guide  
  > "based on the HD 163296 Band 7 Science Verification CASA guide" (2 Data)
- **Astropy** : Python analysis  
  > "The research made use of Astropy, a community-developed core Python package for Astronomy" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| DCO+ ring radii (inner) | 65.7 | ±0.9 | au | 3 | / Fiducial / $<0.04$ / 48.8$^{+0.2}_{-0.1}$ / 65.7$\pm$0.9 / 149.9$^{+0.5}_{-0.7}$ / 259$\pm$1 / |
| DCO+ ring radii (middle) | 149.9 | +0.5/-0.7 | au | 3 | 65.7$\pm$0.9 au, 149.9$^{+0.5}_{-0.7}$ au and 259$\pm$1 au |
| DCO+ ring radius (outer) | 259 | ±1 | au | 3 | 65.7$\pm$0.9 au, 149.9$^{+0.5}_{-0.7}$ au and 259$\pm$1 au |
| vturb upper limit DCO+(3-2) | <0.04 | not stated | cs | 3 | with any non-thermal velocity dispersion limited to $<$0.04c$_s$ |
| vturb upper limit C18O(2-1) | <0.05 | not stated | cs | 5 | /    $v_{\rm turb}$    /      $<$0.05 c$_s$      / |
| vturb upper limit CO(2-1) | <0.06 | not stated | cs | 5 | /    v$_{\rm turb}$    /      $<$0.06 c$_s$      / |
| vturb limit with free Tmid0 | <0.12 | not stated | cs | 4 | an increase in the turbulence limit to $v_{\rm turb}<$0.12c$_s$ |
| DCO+ Tmid0 free fit | 12.2 | +0.4/-0.5 | K | 4 | $T_{\rm mid0}$ is constrained to 12.2$^{+0.4}_{-0.5}$ K |
| DCO+ excitation temperature (3-2 vs 5-4) | 16 | ±4 | K | 2 | we find a temperature of 16$\pm$4 K and 11$\pm$4 K |
| alpha upper limit (DCO+) | <1.5e-3 | not stated | dimensionless | 6 | our velocity limits imply $\alpha<$1.5$\times$10$^{-3}$, $<$2.4$\times$10$^{-3}$, and $<$3.2$\times$10$^{-3}$ |
| C18O inner hole radius | 35.6 | +1.7/-2.0 | au | 5 | 35.6$^{+1.7}_{-2.0}$ au |
| log XCO from C18O | -4.610 | ±0.003 | dimensionless | 5 | -4.610$\pm$0.003 |
| DCO+ ring peak abundance log (inner) | -10.83 | ±0.03 | dimensionless | 3 | log(\[DCO$^+$/H$_2$\])= -10.83$\pm$0.03, -10.79$\pm$0.01 and -10.99$\pm$0.01 |

## Qualitative findings

- DCO+ emission is confined to three rings, not co-located with dust rings, indicating chemical origin  
  > "Bright rings of dust (cite: zha16; ise16) are not colocated with the DCO$^+$ rings" (Conclusions)
- CO and C18O show an inner excess explained by a steeper inner temperature profile  
  > "we find an inner excess that can be explained by a change in the temperature structure towards the inner disk" (Conclusions)

## Claim tuples

- H: Is turbulence weak throughout the vertical extent of the HD 163296 disk? | E: Modeled DCO+(3-2), C18O(2-1), CO(2-1) visibilities with parametric model and MCMC | R: vturb<0.04, 0.05, 0.06 cs; alpha<~3e-3 | F: Little turbulence from near midplane to surface, below MRI and gravito-turbulence predictions | **supported**
- H: Is the DCO+ turbulence limit robust against systematics? | E: Varied ring width, Tmid0, amplitude scale sys | R: Limit rises at most to <0.12 cs | F: Limit robust, modest degeneracy with temperature | **supported**
- H: What is the radial distribution of DCO+? | E: Deconvolution and ring model fit | R: Three rings at 65.7, 149.9, 259 au | F: Complex chemical environment | **supported**

## Reasoning

- Why this data: DCO+ traces cold gas near the midplane, complementing CO  
  > "is predicted to arise from close to the cold midplane" (Introduction)
- Why this method: _not stated_
- Alternative: Narrow (1%) rings rejected by AIC at >10 sigma  
  > "We find that the fit is significantly worse, a $>10\sigma$ difference according to the Akaike Information Criterion" (5.1 DCO+)
- How they decided it was enough: _not stated_
- Limitation (authors): Parametric temperature/density structure, degeneracies with abundance, dust-to-gas ratio and 18O abundance; turbulence is a disk-averaged intensity-weighted value  
  > "In the end we are constraining a disk-averaged, intensity-weighted value of the non-thermal non-Keplerian motion" (4.1 Influence of Model Assumptions)
- Caveat (inferred, ours): Turbulence parameterized as constant fraction of sound speed; no vertical profile
- Caveat (inferred, ours): Tmid0 discrepancy (12 vs 17.5 K) unresolved
- Caveat (inferred, ours): Fixed ring widths and temperature structure
- Caveat (inferred, ours): Amplitude calibration handled via simple scale factor

## Reproducibility

- Data public (paper): ALMA data cited by project code  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00366.S and ADS/JAO.ALMA#2011.0.00010.SV." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Custom ray-tracing code not released
- Missing: Calibration and imaging parameters
- Missing: Prior ranges and stellar mass
- Data volume (inferred): ~100-300 GB raw for five-night Cycle 2 execution blocks
- Score (inferred): 3/5, Data public and results numeric, but custom modeling code is from earlier work and not released; many setup details missing.
- Rediscovery candidate: no, Requires unreleased ray-tracing code and unspecified imaging details.

## Links

- Method: (cite: fla15) (Modeling code and CO(3-2) structure)
- Method: (cite: ros13) (Velocity field and model basis)
- Method: (cite: sim15) (MRI turbulence predictions for line diagnostics)
- Companion: (cite: fla15) (Previous turbulence constraints from SV data)
- Related: ALMA Science Verification HD 163296

## Checks

```json
{
 "quotes": 68,
 "quotes_ok": 68,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 46,
  "rate": 0.575
 },
 "evidence_ok": true
}
```
