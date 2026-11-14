# The TW Hya Rosetta Stone Project. III. Resolving the Gaseous Thermal Profile of the Disk

`2021ApJ...908....8C` | The Astrophysical Journal 2021 | first author: Calahan, Jenny K. | arXiv: 2012.05927 | DOI: 10.3847/1538-4357/abd255

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: What is the 2D gas thermal structure and gas mass of the TW Hya disk, constrained by seven spatially resolved CO lines, the HD 1-0 flux and the SED?  
  > "we constrain the 2D thermal structure of the protoplanetary disk TW Hya structure utilizing images of seven CO lines." (abstract)
- Target **TW Hya**: coordinates _not stated_; z/distance nearby (no value stated)  
  > "towards the class II, nearby (cite: Gaia18; Bailer-Jones18), face-on TW Hya disk" (Introduction); distance from Gaia18; Bailer-Jones18  
  > "towards the class II, nearby (cite: Gaia18; Bailer-Jones18), face-on TW Hya disk" (Introduction)

## Data provenance

- ALMA projects: 2016.1.00311.S, 2015.1.00686.S, 2016.1.00629.S, 2012.1.00422.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-3 (compact) and C43-6 (extended)  
  > "obtained on December 16, 2016 in configuration C43-3" (2.1 CO Observations from TW Hya Rosetta Project)
- baselines: 15 m to 1124 m  
  > "The extended observations (baselines up to 1124 m)" (2.1 CO Observations from TW Hya Rosetta Project)
- angular resolution: C18O 2-1 0.40x0.30 arcsec; 12CO 2-1 0.37x0.28 arcsec  
  > "had FWHM dimensions of $0.''40 \times 0.''30$ and $^{12}\textrm{CO}$ had $0.''37 \times 0.''28$" (2.1 CO Observations from TW Hya Rosetta Project)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 81 min compact; 25 min extended  
  > "for a total on-source integration time of 81 minutes" (2.1 CO Observations from TW Hya Rosetta Project)
- observing dates: 16 Dec 2016 (compact); 5 and 7 May 2017 (extended)  
  > "carried out on May 5 and 7, 2017 in C43-6" (2.1 CO Observations from TW Hya Rosetta Project)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (230.538 GHz)
- Line: C18O J=2-1 (219.560 GHz)
- Line: 12CO J=3-2 (345.795 GHz)
- Line: 13CO J=3-2 (330.587 GHz)
- Line: 13CO J=6-5 (661.067 GHz)
- Line: C18O J=3-2 (329.331 GHz)
- Line: C18O J=6-5 (658.553 GHz)
- Other facility **Herschel**: HD J=1-0 integrated line flux  
  > "HD J=1-0 was observed using *Herschel*" (3.3 Spatially Unresolved Observations: HD Flux and SED)
- External data: HD 1-0 flux 6.3 (±0.7)e-18 W/m2  
  > "the observed total integrated flux was $6.3 (\pm0.7)\times 10^{-18}$ $\textrm{W/m}^{2}$ (cite: Bergin13)" (2.3 Spatially Unresolved Observations: HD Flux and SED) [from (cite: Bergin13)]
- External data: SED photometry compiled from literature  
  > "Data points for the SED were taken from (cite: Cleeves15)" (2.3 Spatially Unresolved Observations: HD Flux and SED) [from (cite: Cleeves15)]
- External data: Initial model parameters and CO depletion profile  
  > "Our initial parameters are taken from (cite: Zhang19)" (3.3 Initial Parameter Setup of TW Hya) [from (cite: Zhang19)]
- External data: Archival 12CO 3-2 images  
  > "We utilize their final data reduction and images." (2.2 Archival CO Data) [from (cite: Huang18)]
- External data: Archival 13CO 3-2, 6-5 and C18O 3-2, 6-5 images  
  > "and not repeated here. We utilize their final data reduction and images." (2.2 Archival CO Data) [from (cite: Schwarz16)]
- External data: ISM isotope ratios CO/13CO = 69, CO/C18O = 570  
  > "CO/$^{13}\textrm{CO}$ = 69 and CO/$\textrm{C}^{18}\textrm{O}$ = 570 (cite: Wilson99)" (3.2 Dust and Gas Temperatures) [from (cite: Wilson99)]

## Processing

### Calibration

- pipeline or manual: CASA pipeline  
  > "The data were calibrated by the CASA pipeline (cite: McMullin07)." (2.1 CO Observations from TW Hya Rosetta Project)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1107-4449 (extended); J1037-2934 (compact)  
  > "J1107-4449 as the flux calibration, and J1037-2934 as the phase calibrator." (2.1 CO Observations from TW Hya Rosetta Project)
- flux scale uncertainty: 10-15%  
  > "The error in the observed flux ranges from 10-15% based on the ALMA technical handbook." (Table 1)
- self calibration: one round phase self-cal each on extended and compact data, 30 s solint, polarizations averaged, CASA 4.5.0  
  > "For the self calibration we adopted a solution interval of 30 seconds and averaged both polarizations." (2.1 CO Observations from TW Hya Rosetta Project)

### Imaging

- task: tclean in CASA 4.6.12  
  > "The images were produced in CASA version 4.6.12 using *tclean*" (2.1 CO Observations from TW Hya Rosetta Project)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "with Briggs weighting and a robust parameter of 0.5" (2.1 CO Observations from TW Hya Rosetta Project)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub in uv plane  
  > "the continuum was subtracted from the line observations in the uv plane using the CASA routine *uvcontsub*" (2.1 CO Observations from TW Hya Rosetta Project)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: concat of continuum-subtracted long and short baselines  
  > "The continuum subtracted long and short baselines were then combined using the method *concat*" (2.1 CO Observations from TW Hya Rosetta Project)
- smoothing: _not stated_
- final beam: C18O 0.40x0.30 arcsec; 12CO 0.37x0.28 arcsec  
  > "The $\textrm{C}^{18}\textrm{O}$ restoring beam had FWHM dimensions of $0.''40 \times 0.''30$" (2.1 CO Observations from TW Hya Rosetta Project)
- final rms: _not stated_

### Inherited from earlier work

- 12CO 3-2 analysis and imaging procedures  
  > "The $^{12}\textrm{CO}$ $J$ = 3-2 analysis and imaging procedures are reported in (cite: Huang18)" (2.2 Archival CO Data) [from (cite: Huang18)]
- 13CO and C18O 3-2, 6-5 observations described elsewhere  
  > "observations are described in (cite: Schwarz16), and not repeated here" (2.2 Archival CO Data) [from (cite: Schwarz16)]
- RAC2D code details  
  > "a higher-level detailed description of the code can be found in the aforementioned paper." (3 Modeling: RAC2D) [from (cite: Du14)]
- Initial chemical abundances  
  > "motivated by (cite: Du14) and (cite: Zhang19)" (3.3 Initial Parameter Setup of TW Hya) [from (cite: Du14); (cite: Zhang19)]

### Not stated but needed to reproduce (our reading)

- Exact line-free channels and spectral windows used for uvcontsub and concat
- Velocity range and moment-zero settings (clipping, masks) in bettermoments
- Image size, cell size, cleaning threshold, and masks for tclean
- Flux scaling for archival data if any
- Procedure for computing beam-convolved simulated profiles and azimuthal averaging details (center, PA, inclination deprojection)
- Quantitative goodness-of-fit metric; best fit was judged by eye
- RAC2D source code, grid resolution, and dust opacity/composition details
- Stellar luminosity/UV and cosmic-ray ionization inputs

## Analysis recipe

1. **Make moment-zero maps and radial profiles**: Moment zero maps with bettermoments, azimuthally averaged to radial emission profiles  
  > "Each moment zero map was then azimuthally averaged producing the radial emission profiles." (2 Observations)
   - software: bettermoments
   - assumption: disk inclination 6 deg  
  > "The disk inclination used is 6$^{\circ}$" (3.3 Initial Parameter Setup of TW Hya)
   - fitting: _not stated_
   - validation: _not stated_
2. **Build thermo-chemical disk model**: RAC2D with gas, small dust and large dust populations, Lynden-Bell & Pringle surface density with exponential tapers; compute gas/dust temperature and chemistry over 1 Myr; ray-trace lines  
  > "We use the time-dependent thermo-chemical code RAC2D (cite: Du14)." (3 Modeling: RAC2D)
   - software: RAC2D
   - parameter: Initial parameters from Zhang19; CO depletion imposed at start; 13CO and C18O from CO/13CO=69, CO/C18O=570  
  > "we compute $^{13}\textrm{CO}$ and $\textrm{C}^{18}\textrm{O}$ abundances based on ISM ratios" (3.2 Dust and Gas Temperatures)
   - assumption: MRN grain size distribution n(a) ∝ a^-3.5  
  > "Each dust population follows an MRN grain size distribution $n(a) \propto a^{-3.5}$" (3.1 Physical Structure)
   - assumption: no isotopologue fractionation chemistry  
  > "We do not model isotopologue fractionation in this chemical network" (3.2 Dust and Gas Temperatures)
   - fitting: Manual grid exploration of gas mass, small dust mass, Psi, gamma, radii and heights; no sampler  
  > "As a first step we set up a grid of models to explore the full parameter space." (3.4 Parameter Exploration)
   - validation: Compared radial integrated intensity profiles, HD flux and SED  
  > "the quality of model was assessed by a comparison of the radial integrated intensity profiles" (3.4 Parameter Exploration)
3. **Iterate CO depletion and parameters to best fit**: Adjust CO depletion profile, chemical time reduced to 0.01 Myr, and give gas and small dust different Psi (1.1, 1.2) to match CO profiles and HD flux  
  > "We find that in order to match both CO and HD observations the $\Psi$ values of the gas and small dust need to be slightly different (1.1 and 1.2, respectively)." (4.1 Description of Best-Fit Model)
   - software: RAC2D
   - fitting: _not stated_
   - validation: Model HD flux 5.9e-18 W/m2 within observed uncertainty  
  > "This model predicts an HD flux of $5.9 \times 10^{-18}$ $\textrm{W m}^{-2}$, which is well within the uncertainty of the observed flux." (4.1 Description of Best-Fit Model)
4. **Compute and compare SED**: Feed RAC2D temperatures, stellar spectrum and dust opacities into RADMC3D  
  > "we feed in those results including the stellar spectrum and dust opacities into RADMC3D." (4.2 Best-fit SED)
   - software: RADMC-3D
   - fitting: _not stated_
   - validation: Model SED agrees reasonably with observed SED  
  > "our model SED agrees reasonably well with the observed SED" (4.2 Best-fit SED)
5. **Test CO abundance and gas mass degeneracy**: Low-mass model with gas mass reduced 10x and CO abundance increased 10x; compare CO profiles and HD flux  
  > "we decrease the total gas mass by one order of magnitude while subsequently increasing in the CO abundance by the same factor." (4.4 CO Mass/Abundance Degeneracy)
   - software: RAC2D
   - fitting: _not stated_
   - validation: Radial CO profiles indistinguishable, HD flux drops by more than a factor of five  
  > "the line flux of HD (1-0) transition of the lower mass model goes down by more than a factor of five" (4.4 CO Mass/Abundance Degeneracy)

## Software

- **RAC2D** : thermo-chemical modeling and line ray-tracing  
  > "We use the time-dependent thermo-chemical code RAC2D (cite: Du14)." (3 Modeling: RAC2D)
- **CASA** 4.5.0 (self-cal); 4.6.12 (imaging): calibration, self-calibration, uvcontsub, concat, tclean  
  > "The images were produced in CASA version 4.6.12 using *tclean*" (2.1 CO Observations from TW Hya Rosetta Project)
- **bettermoments** : moment zero maps  
  > "Using BETTERMOMENTS[^1] (cite: Teague18), moment zero maps were calculated" (2 Observations)
- **RADMC-3D** : model SED  
  > "The simulated SED as derived by our final TW Hya model was calculated using RADMC3D (cite: Dullemond12)." (4.2 Best-fit SED)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| best-fit gas mass | 0.025 | not stated | Msun | 3 | The resulting thermal profile finds a disk mass of 0.025 $\textrm{M}_{\odot}$ |
| thickness of dust-depleted gas layer | ~1.2 | not stated | % of radius | 3 | a thin upper layer of gas depleted of small dust with a thickness of $\sim$1.2% of the corresponding radius |
| model HD 1-0 flux | 5.9e-18 | not stated | W m-2 | 3 | This model predicts an HD flux of $5.9 \times 10^{-18}$ $\textrm{W m}^{-2}$ |
| initial (Zhang19) model HD flux | 4.6e-18 | not stated | W m-2 | 2 | The initial model HD line flux is $4.6 \times 10^{-18}$ $\textrm{W m}^{-2}$ |
| CO depletion relative to Zhang19 beyond 20 AU | 2.5 times less (average) | not stated | factor | 3 | Beyond 20AU the final CO depletion profile is on average 2.5 times less than what was derived in (cite: Zhang19) |
| Psi gas / small dust | 1.1 / 1.2 | not stated | dimensionless | 3 | $\Psi$                      / 1.1   / 1.2                                          / 1.2 |

## Qualitative findings

- CO alone is not a viable mass tracer because abundance is degenerate with H2 surface density; HD breaks the degeneracy  
  > "CO alone is not a viable mass tracer as its abundance is degenerate with the total $\textrm{H}_{2}$ surface density." (abstract)
- 12CO 2-1, 3-2 and 13CO 3-2 trace layers where HD emits; C18O and 13CO 6-5 become optically thin beyond 20-40 AU  
  > "The $\textrm{C}^{18}\textrm{O}$ and $^{13}\textrm{CO}$ 6-5 become optically thin beyond radii of 20-40AU" (5.1 CO Emitting Regions)

## Claim tuples

- H: A single thermo-chemical model can reproduce multiple spatially resolved CO lines, HD flux and SED | E: Forward modeling with RAC2D and parameter grid exploration | R: Best-fit model matches seven CO radial profiles, HD flux (5.9e-18 W/m2) and SED | F: A thermal structure and gas mass of ~0.025 Msun is derived | **supported**
- H: CO line profiles can determine gas mass | E: Low-mass model with 10x lower mass and 10x higher CO abundance | R: CO profiles indistinguishable; HD drops by more than 5x | F: CO is degenerate with gas mass; HD needed | **supported**
- H: Gas and small dust need identical flaring | E: Vary Psi for gas and small dust | R: Psi 1.1 vs 1.2 needed to match inner CO and HD | F: Thin dust-depleted gas layer at the surface | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Forward modeling with multiple spatially resolved lines gives finer constraints on radial and vertical temperature  
  > "Spatially resolved observations allow for measurements of column densities and temperature information at different disk radii" (1 Introduction)
- Alternative: Modeling continuum and scattered light was not attempted  
  > "It is worth noting that we do not seek to reproduce scattered light nor continuum observations." (1 Introduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Gas mass is valid within the model framework; CO fractionation not included; inclination not explored  
  > "we constrain the total gas mass of the TW Hya disk to be $\approx$ 0.025 $\textrm{M}_{\odot}$ within our model framework." (6 Conclusions)
- Caveat (inferred, ours): Best fit chosen by eye with no formal statistical fit or uncertainties; parameter degeneracies not quantified
- Caveat (inferred, ours): Gas mass depends on assumed HD/H2 and the 1 Myr chemical time plus imposed depletion
- Caveat (inferred, ours): Results are model-dependent and rely on single-disk tuning of Psi

## Reproducibility

- Data public (paper): Archival ALMA programs listed in acknowledgments  
  > "This paper makes use of data from ALMA programs 2015.1.00686.S, 2016.1.00629.S, 2012.1.00422.s, and 2016.1.00311.S." (Acknowledgments)
- Products in archive: _not stated_
- Code: _not stated_
- Missing: RAC2D code and grid setup
- Missing: Moment/mask settings and line-free channels
- Missing: Quantitative fit criteria
- Data volume (inferred): ~100-300 GB raw for five ALMA programs
- Score (inferred): 3/5, Data public and parameters tabulated, but RAC2D is a specialized code and best-fit selection was by eye.
- Rediscovery candidate: no, Main result depends on a specialized thermo-chemical code and manual fitting.

## Links

- Method: (cite: Du14) (RAC2D code)
- Method: (cite: Zhang19) (initial model and CO depletion)
- Companion: (cite: Huang18) (12CO 3-2 data and imaging)
- Companion: (cite: Schwarz16) (archival isotopologue data)
- Related: TW Hya Rosetta Stone Project

## Checks

```json
{
 "quotes": 73,
 "quotes_ok": 73,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 52,
  "rate": 0.634
 },
 "evidence_ok": true
}
```
