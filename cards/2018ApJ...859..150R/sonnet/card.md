# Multiple Stellar Flybys Sculpting the Circumstellar Architecture in RW Aurigae

`2018ApJ...859..150R` | The Astrophysical Journal 2018 | first author: Rodriguez, Joseph E. | arXiv: 1804.09190 | DOI: 10.3847/1538-4357/aac08f

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: Do high-resolution ALMA maps of RW Aur reveal additional tidal streams and resolved disks, and do they imply multiple stellar fly-bys, given the system's dimming events?  
  > "The observed configuration of tidal streams surrounding RW Aur A and B is incompatible with a single star–disk tidal encounter, suggesting that the RW Aurigae system has undergone multiple fly-by interactions." (abstract)
- Target **RW Aurigae (A and B)**: coordinates RA 05:07:49.572, Dec +30:24:04.94 (A, J2000, Band 6 fit)  
  > "The RW Aur system is 140 pc away (cite: vanLeeuwen:2007)" (Introduction); "| RA (J2000) | 05:07:49.57220$\pm$0.00034s | 05:07:49.46089$\pm$0.00034s |" (Table 1); z/distance 140 pc  
  > "The RW Aur system is 140 pc away (cite: vanLeeuwen:2007)" (Introduction); "| RA (J2000) | 05:07:49.57220$\pm$0.00034s | 05:07:49.46089$\pm$0.00034s |" (Table 1); distance from van Leeuwen 2007  
  > "The RW Aur system is 140 pc away (cite: vanLeeuwen:2007)" (Introduction); "| RA (J2000) | 05:07:49.57220$\pm$0.00034s | 05:07:49.46089$\pm$0.00034s |" (Table 1)

## Data provenance

- ALMA projects: 2015.1.01506.S, 2016.1.00877.S
- bands: Band 6 (225 GHz) and Band 7 (338 GHz)  
  > "RW Aur was observed in Band 6 (225 GHz) with the 12m array" (2.1 ALMA)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12m array and 7m array (Band 6); Band 7 12m  
  > "Also, Band 6 observations were taken with the 7m array for a total additional integration time of 217.23 minutes." (2.1 ALMA)
- configurations: _not stated_
- baselines: Band 6 12m: 15–3248 m; 7m: 9–45 m; Band 7: 16–1110 m  
  > "The observations included 39 antennas with a baseline of 15 – 3248 m." (2.1 ALMA)
- angular resolution: Band 6 continuum 0.194"x0.077"; Band 7 continuum 0.271"x0.175"  
  > "yielding a synthesized beam of 0$\ensuremath{''}$194$\times$0$\ensuremath{''}$077" (2.1 ALMA)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: Band 6 12m 311.17 min; 7m 217.23 min; Band 7 22.8 min (total integration)  
  > "for a total integration time of 311.17 minutes" (2.1 ALMA)
- observing dates: Band 6: 2016 Sep 29/30 and Dec 07/08; Band 7: 2016 Jul 23  
  > "on UT 2016 September 29/30 and UT 2016 December 07/08" (2.1 ALMA)
- pi or archival as stated: _not stated_
- Line: 12CO 2-1 (not stated)
- Line: 12CO 3-2 (not stated)
- Line: 13CO 2-1 and 3-2 (not stated)
- Line: C18O, SO 2-1 (not stated)
- Other facility **AAVSO**: Photometry 1906–2018 (15,057 visual and V-band CCD observations)  
  > "totaling 15,057 visual and V-band CCD observations on RW Aur" (2.4 AAVSO)
- Other facility **ASAS-SN**: 591 V-band observations 2015–2018  
  > "obtaining 591 observations in the $V$-band" (2.3 ASAS-SN)
- Other facility **KELT and Wesleyan archive**: Archival photometry  
  > "We include and analyze the archival observations of RW Aur from the Kilodegree Extremely Little Telescope (KELT) survey" (2.2 Archival Observation: KELT & Wesleyan University)
- External data: PdBI 122.5 GHz flux densities and earlier A/B fluxes and separation  
  > "the PdBI 122.5 GHz continuum flux densities from (cite: Cabrit:2006) are consistent with an extrapolation along these slopes" (3.1.1 Spectral Index) [from (cite: Cabrit:2006)]
- External data: Stellar masses 1.4 and 0.9 Msun for A and B  
  > "Using a mass of 1.4$\,M_\Sun$ and 0.9$\,M_\Sun$ for RW Aur A and B (cite: Ghez:1997)" (5.2 Nature and Morphology of the Tidal Streams) [from (cite: Ghez:1997)]
- External data: Dust temperature law T_d(r)=217 K (r/AU)^-0.57  
  > "T$_d$(r) = 217 K (r / AU)$^{$-$0.57}$ (cite: Osterloh:1995)" (3.1.1 Spectral Index) [from (cite: Osterloh:1995)]

## Processing

### Calibration

- pipeline or manual: Initially calibrated by NAASC; then two rounds of phase-only self-calibration  
  > "The data were initially calibrated by the NAASC. Two rounds of phase-only self-calibration were then applied to each set of observations in CASA 4.3.1" (2.1 ALMA)
- casa version: CASA 4.3.1  
  > "The Band 6 observations were concatenated and imaged in CASA 4.3.1 using the CLEAN task." (2.1 ALMA)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0510+1800 (12m Band 6, Band 7); J0522-3627 (7m)  
  > "the quasar J0522-3627 was used for the flux calibrator" (2.1 ALMA)
- flux scale uncertainty: _not stated_
- self calibration: Two rounds phase-only, continuum model  
  > "using the RW Aurigae continuum emission as the self-calibration model" (2.1 ALMA)

### Imaging

- task: CLEAN in CASA 4.3.1; Band 6 data concatenated  
  > "The Band 6 observations were concatenated and imaged in CASA 4.3.1 using the CLEAN task." (2.1 ALMA)
- deconvolver: _not stated_
- weighting robust: Continuum Briggs robust 0; lines robust 0.5  
  > "The continuum data were imaged using Briggs weighting with a robust value of 0" (2.1 ALMA)
- uv taper: 0.06"x0.25" for lines  
  > "with a uv-taper of 0$\ensuremath{''}$06$\times$0$\ensuremath{''}$25 to force a more circular beam" (2.1 ALMA)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 12CO 2-1: 0.30"x0.25", PA -30  
  > "resulting in a synthesized beam of 0$\ensuremath{''}$30$\times$0$\ensuremath{''}$25, a beam position angle of -30$^{\circ}$" (2.1 ALMA)
- final rms: Band 6 continuum 38 uJy/beam; Band 7 560 uJy/beam; 12CO 2-1 1.5 mJy/beam  
  > "and an rms of 38 $\mu$Jy bm$^{-1}$" (2.1 ALMA)

### Inherited from earlier work

- Occultation model for dimming events  
  > "(following §5.1 in (cite: Rodriguez:2013))" (4 Photometric Results) [from (cite: Rodriguez:2013)]
- Tidal truncation Monte Carlo approach  
  > "we follow (cite: Torres:1999), (cite: Harris2012) and use a Monte Carlo approach to construct a probability distribution for $R_t$" (5.4 Tidal Truncation of the Disks) [from (cite: Torres:1999), (cite: Harris2012)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and continuum subtraction method
- Image sizes, cell sizes, clean masks and thresholds
- Exact rest frequencies and velocity ranges for moment maps
- Starting parameter priors and MCMC settings for the uv fit
- Flux scale uncertainty applied
- Stellar mass and orbital priors used in the truncation Monte Carlo
- How disk gas radii were defined (threshold)

## Analysis recipe

1. **Fit continuum visibilities**: Two elliptical Gaussian disks fit directly to visibilities with emcee and vis_sample  
  > "we fit a simple model consisting of two Gaussian disks directly to the measured visibilities." (3.1 Continuum Modeling)
   - software: emcee, vis_sample
   - parameter: 12 parameters; PA, inclination, flux, offset, Gaussian width per disk  
  > "This model used a total of 12 parameters" (3.1 Continuum Modeling)
   - fitting: MCMC with emcee; priors not stated  
  > "fit to the observed visibilities using the MCMC routine `emcee`" (3.1 Continuum Modeling)
   - validation: Reduced chi2 of 1.02  
  > "The best fit model resulted in a reduced $\chi^{2}$ of 1.02" (3.1 Continuum Modeling)
2. **Spectral index and optical depth**: Compare Band 6 and 7 flux densities; compare to blackbody brightness temperature  
  > "we find a spectral index ($\alpha = \Delta \log F_{\nu}$$/$$\Delta \log \nu$) of 2.11$\pm$0.01 in RW Aur A and 2.39$\pm$0.07 in RW Aur B" (3.1.1 Spectral Index)
   - assumption: Disk radius 20 AU, inclination 55 deg  
  > "for a disk of radius 20 AU viewed at a 55 degrees of inclination" (3.1.1 Spectral Index)
   - fitting: _not stated_
   - validation: Compared with PdBI 122.5 GHz extrapolation  
  > "the PdBI 122.5 GHz continuum flux densities from (cite: Cabrit:2006) are consistent with an extrapolation along these slopes, indicating a constant spectral index across this wavelength range for both disks." (Spectral Index)
3. **Gas disk kinematics and sizes**: PV diagrams for Keplerian masses; disk radii measured with CASA measurement tool; spectra extracted with elliptical mask  
  > "Using CASA’s built-in measurement tool (cite: McMullin:2007), we estimate the radius of the gas disk around RW Aur A from the $^{12}$CO(2-1) to be $\sim$58 AU" (3.2.1 RW Aur A)
   - software: CASA
   - assumption: PA 41 deg and inclination 55 deg for A  
  > "assuming a PA of 41$^{\circ}$ and a dust disk inclination of 55$^{\circ}$" (3.2.1 RW Aur A)
   - fitting: _not stated_
   - validation: Masses compared to pre-main-sequence estimates  
  > "This mass range is consistent with the inferred mass of 1.3-1.4$\,M_\Sun$ determined from pre-main sequence models of near-IR observations (cite: Ghez:1997; Woitas:2001)." (RW Aur A)
4. **Gas temperature and column density in arm**: Compare 12CO(3-2)/(2-1) ratio and surface brightness to RADEX LVG isothermal slab models  
  > "compare to simple predictions for an isothermal slab in the Large Velocity Gradient (LVG) approximation, calculated with the on-line RADEX modeling tool" (5.3 Gas Properties)
   - software: RADEX
   - assumption: LTE densities; CO/H <=1e-4; solar isotopic ratio 89  
  > "Assuming similar excitation in the two isotopologues and a solar isotopic abundance ratio of 89, we infer a $^{12}$CO(2-1) optical depth at the peak $< 7$." (Discussion, Gas Properties in the Tidal Arm and Disks)
   - fitting: _not stated_
   - validation: Critical densities checked a posteriori  
  > "This confirms *a posteriori* that LTE should be valid (the critical densities of the CO(2-1) and (3-2) lines at $\simeq 20$K are $2\times 10^3$ and $\simeq 7 \times 10^4$ cm$^{-3}$, respectively)." (Discussion, Gas Properties in the Tidal Arm and Disks)
5. **Tidal truncation radii**: Monte Carlo of orbital parameters, 10 million samples, 1000 radius bins  
  > "We then perform 10 million random samplings of the unknown orbital parameters" (5.4 Tidal Truncation of the Disks)
   - parameter: Separation 1.468", 140 pc, masses 1.3-1.4 and 0.3-1.0 Msun, e max 1 or 0.7  
  > "For the current observed separation of $1.468\pm0.056\ensuremath{''}$, distance of 140 pc, and possible stellar masses of 1.3-1.4 and 0.3-1.0 M$_\odot$ for the primary and secondary respectively" (Tidal Truncation of the Disks)
   - fitting: _not stated_
   - validation: Peak consistent with observed gas radii for e=0.7  
  > "Both the 58 and 38 AU observed gas radii of the primary and secondary disks (Table [\[tbl:Results\]](#tbl:Results)) are consistent with the most probable tidal truncation radii in Figure [11](#fig:Truncation) for an eccentricity of 0.7" (Tidal Truncation of the Disks)
6. **Photometric dimming analysis**: Opaque-screen occultation model with sharp leading edge to estimate transverse velocity and width  
  > "We model each event separately as an occultation of RW Aur A by large opaque screen with a leading edge perpendicular to its direction of motion" (4 Photometric Results)
   - assumption: Stellar radius 1.6 Rsun  
  > "adopting a stellar radius of 1.6$\pm$0.32 $\,R_\Sun$(cite: Rodriguez:2013)" (Historical Dimming: 1937-1938 "A", 1987 "B")
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.3.1: Self-calibration, CLEAN imaging, measurement tool  
  > "in CASA 4.3.1 using the CLEAN task" (2.1 ALMA)
- **emcee** : MCMC visibility fit  
  > "MCMC routine `emcee` (cite: ForemanMackey:2013)" (3.1 Continuum Modeling)
- **vis_sample** : Visibility sampling of models  
  > "visibility sampling routine `vis_sample` (cite: Loomis:2018)" (3.1 Continuum Modeling)
- **RADEX** : LVG line ratio modeling  
  > "calculated with the on-line RADEX modeling tool (cite: radex)" (5.3 Gas Properties)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Band 6 flux density RW Aur A | 36.31 | 0.02 | mJy | 1 | / Disk Flux Density (mJy) / 36.31 $\pm$ 0.02 / 4.61$\pm$0.02 / |
| Band 6 Gaussian radius A / B | 21.28 / 15.51 | 0.03 / 0.20 | AU | 1 | / Disk Gaussian radius (AU) / 21.28 $\pm$ 0.03 / 15.51 $\pm$ 0.20 / |
| Spectral index A | 2.11 | 0.01 | dimensionless | 2 | 2.11$\pm$0.01 in RW Aur A and 2.39$\pm$0.07 in RW Aur B |
| Spectral index B | 2.39 | 0.07 | dimensionless | 2 | 2.11$\pm$0.01 in RW Aur A and 2.39$\pm$0.07 in RW Aur B |
| CO gas disk radius A / B | 58 / 38 | not stated | AU | 3 | with CO radii of 58 au and 38 au consistent with tidal truncation |
| A–B separation Band 6 | 1.497 | 0.001 | arcsec | 1 | / A–B Separation / 1.497$\pm$0.001$\ensuremath{''}$ / — / |
| Inclination difference A vs B (Band 6) | 12 | 6 sigma | deg | 1 | the disk inclinations differ by 12$^\circ$ (6 sigma) in Band 6 |
| 12CO(2-1) integrated flux A / B | 3.42 / 0.86 | 0.03 / 0.03 | Jy km/s | 3 | 2-1 = 0.86$\pm$0.03 Jy  km s$^{-1}$ |
| Tidal arm length | 740 | not stated | AU | 3 | we estimate the arm to be $\sim$740 AU along the spine of the arm |
| Gas temperature in A disk | ~70 | not stated | K | 4 | we find $T_k \simeq 70$ K |
| Dimming velocity range | 0.4 to 4.6 | not stated | km/s | 6 | we derive a transverse velocity in the range of 0.4 to 4.6  km s$^{-1}$ |

## Qualitative findings

- Additional tidal streams gamma and delta beyond the apparent circumbinary ring  
  > "we identify the presence of two additional tidal streams extending out past the extent of the apparent circumbinary ring" (3.2.3 Tidal Streams)

## Claim tuples

- H: Is the stream pattern consistent with a single fly-by? | E: 12CO maps and escape velocity comparison | R: Multiple streams, partially unbound | F: At least two fly-bys of RW Aur B | **supported**
- H: Are disks truncated and misaligned? | E: uv fits and CO radii vs truncation Monte Carlo | R: Gas radii 58 and 38 AU; dust 2.5 times smaller; inclinations differ | F: Consistent with tidal truncation; misaligned by 12 or 57 deg | **supported**
- H: Can the dimming origin be located? | E: Occultation modelling of seven events | R: Velocities 0.4–4.6 km/s | F: Cannot distinguish between interpretations | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Gamma stream may be a slow outflow from RW Aur B  
  > "This coincidence raises the alternative possibility that $\gamma$ might trace a slow molecular outflow from RW Aur B." (3.2.3 Tidal Streams)
- How they decided it was enough: _not stated_
- Limitation (authors): Lack of uv coverage at intermediate baselines  
  > "our observations are not sensitive enough to constrain this due to a lack of (u,v) coverage at intermediate baselines" (3.2.3 Tidal Streams)
- Caveat (inferred, ours): Gas disk radii are measured with an undefined threshold and a marginally resolved beam for B
- Caveat (inferred, ours): Gas mass and ejected fraction rely on very restrictive assumptions
- Caveat (inferred, ours): Truncation test does not constrain eccentricity

## Reproducibility

- Data public (paper): Final calibrated ALMA data made public with paper; project codes listed  
  > "Our final calibrated ALMA observations are available publicly with this paper." (2.1 ALMA)
- Products in archive: _not stated_
- Code: vis_sample publicly available on GitHub  
  > "vis_sample is publicly available at https://github.com/AstroChem/vis_sample" (Footnote 3)
- Missing: Clean parameters and masks
- Missing: MCMC priors
- Missing: Line-free channels and moment map thresholds
- Data volume (inferred): ~50-150 GB raw for three configurations
- Score (inferred): 3/5, Data public and the imaging recipe is mostly given, but several imaging and fit details are missing.
- Rediscovery candidate: yes, Public data, numeric continuum-fit and flux results with a stated recipe.

## Links

- Method: (cite: Loomis:2018) (vis_sample visibility sampling)
- Method: (cite: Rodriguez:2013) (occultation model)
- Companion: (cite: Cabrit:2006) (earlier PdBI observations)
- Companion: (cite: Dai:2015) (SPH fly-by simulations)
- Related: AAVSO
- Related: ASAS-SN
- Related: KELT

## Checks

```json
{
 "quotes": 78,
 "quotes_ok": 78,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 83,
  "stated": 54,
  "rate": 0.651
 },
 "evidence_ok": true
}
```
