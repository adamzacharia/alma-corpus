# IRC + 10°216 mass loss properties through the study of λ3 mm emission. Large spatial scale distribution of SiO, SiS, and CS

`2019A&A...629A.146V` | Astronomy and Astrophysics 2019 | first author: Velilla-Prieto, L. | arXiv: 1908.05652 | DOI: 10.1051/0004-6361/201834717

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars, astrochemistry
- Question: What are the large-scale spatial distribution and radial abundance profiles of SiO, SiS and CS in the envelope of IRC+10216, and what do they say about its mass-loss history and photo-dissociation?  
  > "Here we provide new observational constraints to the molecular emission of IRC + 10$^{\circ}$216 impinging on the nature of its mass-loss history and photo-dissociation processes" (Introduction)
- Target **IRC +10216 (CW Leo)**: coordinates RA 09h47m57.446s, Dec +13d16m43.86s (J2000)  
  > "coordinates J2000.0 R.A.=9$^{\mathrm{h}}$47$^{\mathrm{m}}$57$^{\mathrm{s}}$446 and Dec.=13$^{\circ}$16$^{'}$43$''$86 according to the position of the $\lambda$ 1 mm continuum emission peak" (Observations); "It is located at $\sim$120 pc away from us (cite: gro12)" (Introduction); z/distance ~120 pc (123 pc adopted in modelling)  
  > "coordinates J2000.0 R.A.=9$^{\mathrm{h}}$47$^{\mathrm{m}}$57$^{\mathrm{s}}$446 and Dec.=13$^{\circ}$16$^{'}$43$''$86 according to the position of the $\lambda$ 1 mm continuum emission peak" (Observations); "It is located at $\sim$120 pc away from us (cite: gro12)" (Introduction); distance from Groenewegen et al. 2012 (cite: gro12)  
  > "coordinates J2000.0 R.A.=9$^{\mathrm{h}}$47$^{\mathrm{m}}$57$^{\mathrm{s}}$446 and Dec.=13$^{\circ}$16$^{'}$43$''$86 according to the position of the $\lambda$ 1 mm continuum emission peak" (Observations); "It is located at $\sim$120 pc away from us (cite: gro12)" (Introduction)

## Data provenance

- ALMA projects: 2013.1.00432.S
- bands: Band 3 (3 mm), Cycle 2  
  > "We carried out ALMA observations in band 3, corresponding to a $\lambda$ 3 mm spectral line survey" (Observations)
- frequencies and spectral setup: ~84.0-115.5 GHz with five spectral setups; effective resolution 0.488 MHz (channel spacing 0.244 MHz)  
  > "The total frequency coverage was achieved by using five different spectral setups with an effective spectral resolution of 0.488 MHz (channel spacing 0.244 MHz)." (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C34-7 (extended) and C34-2 (compact)  
  > "We used the C34-7 and C34-2 configurations (extended and compact, respectively)." (Observations)
- baselines: Extended up to ~1600 m; compact 13 m to 390 m  
  > "The compact configuration provided baselines as low as 13 m and up to 390 m" (Observations)
- angular resolution: beams as small as ~0.6 arcsec  
  > "resulting in synthesised beam sizes as small as $\sim$0$''$6" (Observations)
- max recoverable scale: ~23 to ~32 arcsec (compact configuration)  
  > "resulting into maximum recoverable scales in the range of $\sim$23$''$ up to $\sim$32$''$ depending on the frequency" (Observations)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 4 Dec 2014; 29 Jun, 4, 5, 19 Jul 2015  
  > "The observations were taken during several runs on December 4, 2014, and on June 29, July 4, 5, and 19, 2015." (Observations)
- pi or archival as stated: _not stated_
- Line: SiO J=2-1 (86846.986 MHz)
- Line: SiS J=5-4 (90771.566 MHz)
- Line: SiS J=6-5 (108924.303 MHz)
- Line: CS J=2-1 (97980.953 MHz)
- Other facility **IRAM-30 m**: OTF maps 96x96 arcsec at ~80-116 GHz to recover flux filtered out by ALMA, merged with ALMA  
  > "IRAM-30 m on-the-fly (OTF) observations were carried out on June 7–11, 2015, in order to recover the flux filtered out by ALMA." (Observations)
- External data: Kinetic temperature profile and mass-loss rate 2.7e-5 Msun/yr  
  > "The updated parameters are the kinetic temperature radial profile and the mass-loss rate, which have been recently estimated in (cite: gue18)." (Radiative transfer modelling) [from (cite: gue18)]
- External data: Collisional rate coefficients for SiO, SiS, CS with H2  
  > "for SiO we used the values from (cite: day06) and (cite: bal17)" (Radiative transfer modelling) [from (cite: day06; bal17; klo08; tob08; den18)]
- External data: Parent-species abundances for chemical model  
  > "which are the values used in (cite: agu17) after updating the abundances of CS, SiO, and SiS according to our results from the radiative transfer analysis" (Chemistry) [from (cite: agu17)]

## Processing

### Calibration

- pipeline or manual: Initial calibration in CASA with ALMA-provided scripts; self-calibration in GILDAS  
  > "We did an initial calibration of the ALMA data with the Common Astronomy Software Applications (cite: mcm07) by using the scripts provided by the ALMA team." (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ganymede or Callisto in half of tracks; archive fluxes of J0854+201, J1058+015, J0854+2006 otherwise  
  > "In half of the tracks, observations of Ganymede or Callisto were performed to calibrate absolute amplitudes" (Observations)
- flux scale uncertainty: better than 15%  
  > "we estimate an accuracy in the flux calibration better than 15%" (Observations)
- self calibration: Self-calibration on compact continuum emission with GILDAS, per track  
  > "for every track the standard phase calibration was improved by self-calibrating with the very compact source continuum emission, by using the Grenoble Image and Line Data Analysis System (GILDAS) software package." (Observations)

### Imaging

- task: _not stated_
- deconvolver: Steer-Dewdney-Ito algorithm (not Hogbom)  
  > "the Steer-Dewdney-Ito algorithm (cite: ste84) was used during the cleaning process" (Observations)
- weighting robust: Natural weighting cube and robust = 0.5 cube  
  > "A second data cube was obtained by using a robustness factor of 0.5 during the deconvolution process" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: ALMA + IRAM-30m merged with UVSHORT (pseudo-visibilities) after continuum subtraction  
  > "Final data cubes were produced by merging the ALMA and IRAM-30 m data after continuum subtraction." (Observations)
- smoothing: _not stated_
- final beam: Beams ~0.56x0.49 to 1.14x0.88 arcsec depending on line (e.g. SiO 0.60x0.53)  
  > "SiO $J$=2–1 | 86846.986 | 0.60$\times$0.53" (Table 1)
- final rms: 1-2 mJy/beam depending on line  
  > "SiS $J$=5–4 | 90771.566 | 0.79$\times$0.60 | 39 | 2" (Table 1)

### Inherited from earlier work

- Radiative transfer code and physical model  
  > "We carried out radiative transfer models using the code that is described in detail in (cite: agu12)." (Radiative transfer modelling) [from (cite: agu12)]
- Complete description of ALMA observations deferred  
  > "A complete description of these ALMA observations will be presented elsewhere (Cernicharo, in prep.)." (Observations) [from Cernicharo, in prep.]
- Chemical model setup (NH/Av factor, UV field)  
  > "This assumption has been made on the basis of reproducing the interferometer observations of the region where photochemistry occurs (cite: agu17)." (Chemistry) [from (cite: agu17)]

### Not stated but needed to reproduce (our reading)

- Continuum-free/line-free channels and continuum subtraction method
- Cell size, image size, clean masks and iteration thresholds
- Exact azimuthal-average procedure and fit goodness criterion for abundance profiles
- Abundance profile values as a function of radius (only in figure)
- Details of the UVSHORT merging scaling
- Spectral window assignments per track and time on source
- Radiative transfer code is not named or released

## Analysis recipe

1. **Merge ALMA and IRAM-30m and image cubes**: UVSHORT pseudo-visibility merging, then SDI cleaning, natural and robust 0.5 weights  
  > "This was done by using the UVSHORT task in the GILDAS software package that uses the pseudo-visibility technique" (Observations)
   - software: GILDAS, CASA
   - fitting: _not stated_
   - validation: Relative amplitude calibration checked in uv-plane; cleaning methods compared  
  > "In all the cases a comparison was made between the different cleaning methods to ensure the consistency and quality of our results." (Observations)
2. **Extract azimuthal averages at systemic velocity channel and PV diagrams**: Azimuthal average of brightness in the v* channel of merged cubes; moment 0, PV diagrams  
  > "Azimuthal averages of the brightness distribution of the ALMA-30 m merged data of the channel corresponding to the systemic velocity of IRC + 10$^{\circ}$216 are presented" (Results)
   - fitting: _not stated_
   - validation: _not stated_
3. **Radiative transfer modelling of radial abundance profiles**: LVG statistical equilibrium plus ray-tracing in spherical CSE of 100 log-spaced shells; abundance profiles adjusted to reproduce azimuthal averages  
  > "It is divided according to a spherical shell gridding of 100 shells evenly spaced on a logarithmic scale for the radius." (Radiative transfer modelling)
   - software: code of Agundez et al. 2012
   - parameter: d = 123 pc; R* = 4e13 cm; T* = 2330 K; Mdot = 2.7e-5 Msun/yr; vexp 5/11/14.5 km/s; microturbulence 1 km/s; gas-to-dust 300  
  > "Mass-loss rate ($\dot{M}$) | 2.7$\times$10$^{-5}$ $M_{\odot}$ yr$^{-1}$" (Radiative transfer modelling)
   - assumption: Spherical envelope, constant expansion velocity, collisions with H2 only  
  > "The collisional rates taken into account to solve the statistical equilibrium equations consider only collisions with H$_2$." (Radiative transfer modelling)
   - fitting: Manual adjustment of abundance profiles to match azimuthal averages on average; no formal fit stated  
  > "Our purpose is to derive the radial abundance profiles that reproduce the azimuthal averages observed, at least up to a level where model predictions are on average compatible with the observations." (Radiative transfer modelling)
   - validation: Synthetic spectra compared with IRAM-30m spectra; IR pumping test  
  > "we tested the accuracy of the model to predict the observed spectrum of the emission lines towards IRC + 10$^{\circ}$216 as observed with the IRAM-30 m antenna" (Radiative transfer modelling)
4. **Chemical model of photo-dissociation**: Gas-phase photo-induced chemistry network (~8000 reactions) with parent abundances updated from step 3  
  > "The chemical network encompasses about 8 000 gas-phase, photo-induced, and cosmic-ray reactions" (Chemistry)
   - parameter: cosmic-ray ionisation rate 1.2e-17 s-1; NH/Av 1.5 times lower than classical; initial radius 2e14 cm  
  > "The adopted cosmic-ray ionisation rate of H$_2$ is 1.2$\times$10$^{-17}$ s$^{-1}$ (cite: agu06)." (Chemistry)
   - assumption: SiS photo-dissociation rate assumed equal to SiO  
  > "In the case of SiS, there are no estimates of its photo-dissociation rate, thus as an educated guess, we assumed the same value than that of SiO." (Chemistry)
   - fitting: _not stated_
   - validation: Compared fall-off radii with observations and RT results  
  > "these predictions are on average below a factor of 1.5, being the fall-off distances of the chemical models larger than the observational measurements" (Chemistry)

## Software

- **CASA** : Initial calibration with ALMA scripts  
  > "We did an initial calibration of the ALMA data with the Common Astronomy Software Applications (cite: mcm07)" (Observations)
- **GILDAS** : Self-calibration, UVSHORT merging, imaging  
  > "This work has made use of GILDAS[^3] and CASA[^4] softwares to reduce and analyse data." (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Fractional abundance of SiO | ~1e-7 | not stated | relative to H2 | 3 | For SiO, we derive a fractional abundance of $\sim$10$^{-7}$ |
| Fractional abundance of CS in innermost CSE | ~1e-6, decreasing to ~5e-7 between ~100-300 R* | not stated | relative to H2 | 3 | we derive an average fractional abundance of $\sim$10$^{-6}$ in the innermost CSE, decreasing down to $\sim$5$\times$10$^{-7}$ between $\sim$100 and 300 $R_{*}$ |
| SiS abundance | ~1-2e-6 up to ~70-100 R* | not stated | relative to H2 | 3 | For SiS, we find an average abundance of $\sim$1–2$\times$10$^{-6}$ in the region up to $\sim$70–100 $R_{*}$ |
| Disappearance radii | SiS ~600 R*, SiO ~700-800 R*, CS ~1000 R* | not stated | R* | 3 | the first molecule to disappear from the gas phase is SiS (at $\sim$600 $R_{*}$), then SiO (at $\sim$700–800 $R_{*}$), and significantly farther, CS (at $\sim$1000 $R_{*}$) |
| Kinematical age of shell at ~420 R* | ~365 | not stated | years | 0 | the kinematical age for a shell located at $\sim$420 $R_{*}$ would be $\sim$365 years |

## Qualitative findings

- Emission shows arcs and shells; SiS J=5-4 shows horn emission suggested to be maser from IR line overlap  
  > "The most plausible explanation for this scenario is maser emission of the $J$=5–4 line, probably as a consequence of an IR line overlap as we discuss below." (Radiative transfer modelling)

## Claim tuples

- H: Is the mass loss of IRC+10216 episodic? | E: Mapped SiO, SiS, CS at 3 mm, computed azimuthal averages, compared with dust shells | R: Common shells at ~150, 315, 420, 560 R* in all lines coincident with dust shells | F: Over-dense shells point to variable mass loss on timescales of hundreds of years | **supported**
- H: Can a standard gas-phase chemical model reproduce the observed sizes? | E: Chemical model with RT-derived parent abundances | R: Right sequence of dissociation radii, but fall-off ~1.5 times farther than observed; no shells | F: Model qualitatively consistent but too simple | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Single-dish data needed for large-scale flux missed by interferometer  
  > "Large-scale flux is provided by short-space observations, thus, single-dish observations must be considered if the aim is to study the complete molecular emission of an extended object." (Introduction)
- Alternative: Hogbom CLEAN rejected as it can introduce artificial clumpiness in extended emission  
  > "given that (cite: hog74) can introduce artificial clumpiness when generating images of objects that have extended emission" (Observations)
- How they decided it was enough: _not stated_
- Limitation (authors): Model based on single line for SiO and CS, two for SiS; degeneracy between density and abundance  
  > "our study is based solely on the analysis of just a single line in the cases of SiO and CS, and two lines in the case of SiS" (Radiative transfer modelling)
- Caveat (inferred, ours): Abundance profiles fitted by eye with no uncertainties
- Caveat (inferred, ours): Density and abundance enhancements degenerate in shell interpretation
- Caveat (inferred, ours): Chemical model omits gas-dust interaction
- Caveat (inferred, ours): Maser claim for SiS J=5-4 not tested quantitatively

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: Reduced cubes available at CDS  
  > "Reduced data cubes are available in FITS format at the CDS via anonymous ftp to cdsarc.u-strasbg.fr" (Footnote 1)
- Missing: Radiative transfer code and final abundance profile tables
- Missing: IRAM-30m data processing details
- Missing: Imaging parameters and masks
- Data volume (inferred): Several hundred GB raw ALMA data across five setups and multiple tracks, plus IRAM-30m OTF maps
- Score (inferred): 3/5, ALMA data are archival-linked and cubes are at CDS, but imaging details are sparse and RT code and profiles are not given numerically.
- Rediscovery candidate: no, Key results derive from a non-public RT code and fitted-by-eye profiles with incomplete recipe.

## Links

- Method: Agúndez et al. 2012 (cite: agu12) (Radiative transfer code and CSE model)
- Method: Pety & Rodríguez-Fernández 2010 (cite: pet10) (UVSHORT merging technique)
- Companion: Cernicharo, in prep. (Full description of the ALMA observations)
- Companion: Guélin et al. 2018 (cite: gue18) (CO mass-loss rate and temperature profile)
- Related: ALMA Band 3 line survey of IRC+10216

## Checks

```json
{
 "quotes": 62,
 "quotes_ok": 62,
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
  "facts": 71,
  "stated": 46,
  "rate": 0.648
 },
 "evidence_ok": true
}
```
