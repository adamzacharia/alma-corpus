# The Sizes and Depletions of the Dust and Gas Cavities in the Transitional Disk J160421.7-213028

`2017ApJ...836..201D` | The Astrophysical Journal 2017 | first author: Dong, Ruobing | arXiv: 1701.05189 | DOI: 10.3847/1538-4357/aa5abf

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: What are the sizes, depletions and edge sharpnesses of the cavities in small dust, big dust and gas in the transitional disk J1604?  
  > "What are the sizes of the cavities seen in various disk components" (1 Introduction); "How depleted are the cavities in the various disk components?" (1 Introduction)
- Target **J160421.7-213028 (J1604)**: coordinates RA 16h04m21.638s, Dec -21d30'28.98"  
  > "system is located at $\sim$145 pc in the $\sim$5–10 Myr old Upper Scorpius star forming region" (1 Introduction); "the stellar position derived from the first-moment map is RA 16$^h$04$^m$21.638$^s$, Dec -21$^{\circ}$30’28.98"" (2 ALMA Observations and Data Reduction); z/distance ~145 pc  
  > "system is located at $\sim$145 pc in the $\sim$5–10 Myr old Upper Scorpius star forming region" (1 Introduction); "the stellar position derived from the first-moment map is RA 16$^h$04$^m$21.638$^s$, Dec -21$^{\circ}$30’28.98"" (2 ALMA Observations and Data Reduction); distance from cited (de Zeeuw 1999; Pecaut 2012)  
  > "system is located at $\sim$145 pc in the $\sim$5–10 Myr old Upper Scorpius star forming region" (1 Introduction); "the stellar position derived from the first-moment map is RA 16$^h$04$^m$21.638$^s$, Dec -21$^{\circ}$30’28.98"" (2 ALMA Observations and Data Reduction)

## Data provenance

- ALMA projects: 2013.1.01020.S
- bands: Band 6 (230 GHz, 1.3 mm), Cycle 2  
  > "observed with the Atacama Large Millimeter/submillimeter Array (ALMA) in Band 6 (230 GHz) during ALMA Cycle 2 observations" (2 ALMA Observations and Data Reduction)
- frequencies and spectral setup: 4 spws: 12CO and 13CO 117.19 MHz BW (61.035 kHz channels); C18O 468.75 MHz BW (0.244 MHz channels); continuum 1875 MHz BW  
  > "two with bandwidths of 117.19 MHz (and channel widths of 61.035 kHz; equivalent to a velocity resolution of $\sim$0.08 km s$^{-1}$) centered on $^{12}$CO (2–1) and $^{13}$CO (2–1)" (2 ALMA Observations and Data Reduction)
- continuum bandwidth: ~2.6 GHz  
  > "The continuum data were concatenated from four spectral windows providing $\sim$2.6 GHz of continuum bandwidth." (2 ALMA Observations and Data Reduction)
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.25" (35 AU)  
  > "with an angular resolution of $\sim$$0\ensuremath{''}.25$ (35 AU)" (abstract)
- max recoverable scale: _not stated_
- sensitivity: continuum sigma=0.11 mJy/beam; line rms 10-11 mJy/beam in 0.25 km/s bins  
  > "Continuum | 234.00000 | 0.24$\times$0.21 | 61 | 0.11 | 4.0" (Table 1)
- time on source: 316 s  
  > "The total on-source integration time was 316 seconds." (2 ALMA Observations and Data Reduction)
- observing dates: July 2015  
  > "(program ID: 2013.1.01020.S, PI: T. Tsukagoshi) in July 2015" (2 ALMA Observations and Data Reduction)
- pi or archival as stated: PI T. Tsukagoshi  
  > "program ID: 2013.1.01020.S, PI: T. Tsukagoshi" (2 ALMA Observations and Data Reduction)
- Line: 12CO J=2-1 (230.538 GHz)
- Line: 13CO J=2-1 (220.398677 GHz)
- Line: C18O J=2-1 (219.56036 GHz)
- Other facility **Subaru/HiCIAO**: H-band polarized scattered light image (Mayama 2012)  
  > "we use the Subaru/HiCIAO image by (cite: mayama12)" (3 Modeling)
- External data: SED photometry and Spitzer IRS spectrum (Table 3)  
  > "Archival SED data for J160421.7-213028" (Table 3) [from Table 3 refs (preibisch99, cutri03, cutri12, carpenter06, moshir89, mathews12)]
- External data: H-band polarized intensity image from Subaru/HiCIAO  
  > "we use the Subaru/HiCIAO image by (cite: mayama12)" (3 Modeling) [from (cite: mayama12)]

## Processing

### Calibration

- pipeline or manual: CASA following EA-ARC calibration scripts  
  > "The data were calibrated with CASA (cite: mcmullin07) following the calibration scripts provided by EA-ARC" (2 ALMA Observations and Data Reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: quasar J1517-243 (also bandpass); gain J1559-2442  
  > "The flux and bandpass were calibrated with the quasar J1517-243, which was used as a bandpass calibrator as well." (2 ALMA Observations and Data Reduction)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA CLEAN  
  > "then imaged in CASA using the CLEAN algorithm (cite: rau11)" (2 ALMA Observations and Data Reduction)
- deconvolver: _not stated_
- weighting robust: continuum Briggs robust 0.5; lines natural  
  > "The continuum data were cleaned using Briggs weighting with a robust factor of 0.5, and the line data were cleaned using natural weighting" (2 ALMA Observations and Data Reduction)
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
- final beam: ~0.25"; continuum 0.24x0.21 PA 61  
  > "Continuum | 234.00000 | 0.24$\times$0.21 | 61 | 0.11 | 4.0" (Table 1)
- final rms: continuum 0.11 mJy/beam; sigma_line ~11 mJy km/s  
  > "$\sigma_{\rm line}\approx$11 mJy km s$^{-1}$ for the integrated emission" (2 ALMA Observations and Data Reduction)

### Inherited from earlier work

- Modeling procedures for scattered light  
  > "largely follow the procedures described by (cite: dong12pds70) for scattered light" (3 Modeling) [from (cite: dong12pds70)]
- Modeling procedures for mm continuum and line emission  
  > "(cite: vandermarel16) for mm continuum and line emission" (3 Modeling) [from (cite: vandermarel16)]
- Full DALI model details  
  > "The full details on the DALI model are discussed in these papers as well." (3 Modeling) [from (cite: bruderer14; vandermarel15; vandermarel16)]

### Not stated but needed to reproduce (our reading)

- Line-free channels / continuum subtraction for line cubes
- CASA version and clean parameters (image size, cell, masks, threshold)
- Moment map creation details (clipping)
- DALI parameters beyond Table 2 (scale heights, gas temperature, CO abundance, UV field, flaring)
- Gas-to-dust ratio and vertical scale heights of big dust
- Procedure for visibility profiles (deprojection, bins)
- Model code inputs for MCRT scattered light (e.g. grain settings, PSF)

## Analysis recipe

1. **Image continuum and CO lines**: CASA CLEAN; Briggs robust 0.5 for continuum, natural weighting for lines; moment maps  
  > "The continuum data were cleaned using Briggs weighting with a robust factor of 0.5, and the line data were cleaned using natural weighting" (2 ALMA Observations and Data Reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive radial profiles and visibility profiles**: Azimuthally averaged radial cuts and deprojected visibility profiles of continuum and integrated CO; nulls identified  
  > "all profiles show clear nulls, at $\sim$130 k$\lambda$ (continuum), $\sim$170 k$\lambda$ ($^{12}$CO), $\sim$110 k$\lambda$ ($^{13}$CO) and $\sim$110 k$\lambda$ (C$^{18}$O)" (2 ALMA Observations and Data Reduction)
   - fitting: _not stated_
   - validation: _not stated_
3. **Build parametrized axisymmetric disk models with radiative transfer**: MCRT for H-band scattered light; DALI for dust continuum and CO isotopologue lines; synthetic images convolved with observed resolution and compared with data  
  > "For scattered light, we use the (cite: whitney13) Monte Carlo radiative transfer (MCRT) code; for dust continuum and CO line emission, we use the physical-chemical DALI code" (3 Modeling)
   - software: Whitney MCRT, DALI
   - parameter: 23 parameters; star K2, 1.4 Rsun, 1.0 Msun, 4500 K; CO isotope ratios 12CO/13CO=77, 12CO/C18O=560  
  > "The assumed abundance ratios of the CO isotopologues in DALI are $^{12}$CO/$^{13}$CO=77 and $^{12}$CO/C$^{18}$O=560." (3 Modeling)
   - assumption: Small dust: Kim et al. 1994 ISM model; big dust: Andrews 2011 model, 0.005 um-1 mm, n(s)∝s^-3.5; Mie scattering  
  > "which has a minimum size of 0.005 $\ensuremath{\mu}m$ and a maximum size of 1 mm with a power law differential size ($s$) distribution $n(s)\propto s^{-3.5}$" (3 Modeling)
   - fitting: Fitting by eye, not chi^2  
  > "We do not aim at formally fitting the observations in a $\chi^2$ manner, as this is impractical given the large number of degrees of freedom; fitting is done by eye instead." (3 Modeling)
   - validation: Compared with SED, H-band profile, visibilities, CO spectrum; consistent with Cycle 0 345 GHz data  
  > "The fiducial model is also consistent with ALMA Cycle 0 345 GHz continuum and $^{12}$CO $J$=3-2 data (not shown)." (4.1 The Fiducial Model)
4. **Vary cavity size, depth and edge sharpness**: Grid of models varying R_cav (e.g. 50/60/70 AU small dust, 60/70/80 big dust, 5/15/25 gas), delta_cav, and edge shape; compared by eye with visibility nulls and profiles  
  > "we show models with 3 cavity sizes for each disk component — 50, 60, and 70 AU for $R_{\rm cav,small-dust}$" (4.2 How Big are the Cavities?)
   - software: Whitney MCRT, DALI
   - fitting: By eye  
  > "We do not aim at formally fitting the observations in a $\chi^2$ manner, as this is impractical given the large number of degrees of freedom; fitting is done by eye instead." (Modeling)
   - validation: Rejected sharp gas edge at 30 AU and double-drop models since CO isotopologue visibilities deviate near nulls  
  > "a double-drop model (two sharp $\Sigma_{\rm gas}$ drops, one at $R_{\rm cav,big-dust}$, the other at $R_{\rm cav,gas}$), such as proposed by (cite: vandermarel16), is not able to reproduce the visibility profiles of the CO isotope lines." (4.4 How Sharp are the Cavity Edges?)

## Software

- **CASA** : calibration and CLEAN imaging  
  > "The data were calibrated with CASA (cite: mcmullin07)" (2 ALMA Observations and Data Reduction)
- **DALI** : physical-chemical modeling of dust continuum and CO line emission  
  > "for dust continuum and CO line emission, we use the physical-chemical DALI code (cite: bruderer12; bruderer13)" (3 Modeling)
- **Whitney et al. 2013 MCRT code** : scattered light modeling  
  > "For scattered light, we use the (cite: whitney13) Monte Carlo radiative transfer (MCRT) code" (3 Modeling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum peak S/N | 36 | not stated | dimensionless | 1 | The continuum is detected with a peak signal-to-noise ratio of 36 ($\sigma$=0.11 mJy beam$^{-1}$) |
| Position angle / inclination | 80 / 6 | not stated | deg | 1 | We derive a position angle of 80$^\circ$ and an inclination of 6$^{\circ}$ |
| Small dust cavity radius | 60 | ±5 | AU | 4 | Small Dust /       60$\pm$5        /  $\lesssim10^{-3}$ |
| Big dust cavity radius | 70 | ±10 | AU | 4 | Big Dust   /       70$\pm$10       /  $\lesssim10^{-3}$ |
| Gas cavity radius | 15 | ±10 | AU | 4 | Gas        /       15$\pm$10       / $10^{-6}\sim10^{-4}$ |
| Model total gas mass | 2.5 | not stated | M_J | 3 | the total gas mass is 2.5 $M_{\rm J}$, resulting in a global gas-to-dust-mass ratio of $\sim$38:1 |
| Gas cavity depletion delta_cav,gas | 1e-5 (surface density at 15 AU ~1e-3 of that at 70 AU) | within factor 10 | dimensionless | 4 | Inside $R_{\rm cav,gas}$, $\delta_{\rm cav,gas}=10^{-5}$ |

## Qualitative findings

- Gas cavity much smaller than dust cavity; gas density grades smoothly between 15 and 70 AU; mm dust edge sharp  
  > "the CO line data demand a smooth transition in gas density between 15 and 70 AU." (4.4 How Sharp are the Cavity Edges?)

## Claim tuples

- H: Gas and dust cavities have different sizes | E: Model comparison to scattered light, continuum and CO visibilities | R: R_cav gas 15±10 AU vs dust 60-70 AU | F: Gas cavity substantially smaller than dust cavities | **supported**
- H: Cavities are depleted in all components | E: Varied delta_cav | R: dust depletion at least 1000; gas 1e2-1e4 at 15 AU vs 70 AU | F: Gas cavity shallower than dust cavities | **supported**
- H: Gas edge is sharp (30 AU or double drop) | E: Fit CO isotopologue visibilities | R: Models deviate around nulls | F: Sharp drop at 30 AU and double-drop rejected | **refuted**

## Reasoning

- Why this data: _not stated_
- Why this method: CO is not a direct gas density tracer, so DALI is needed  
  > "is thus not a direct gas density tracer" (3 Modeling)
- Alternative: Smooth big-dust edge rejected; sharp gas edge at 30 AU and double-drop rejected  
  > "Thus a smooth cavity edge in big dust appears inconsistent with the data." (4.4 How Sharp are the Cavity Edges?)
- How they decided it was enough: _not stated_
- Limitation (authors): Fiducial model not unique; fitting by eye; overproduces 13CO and C18O outer emission  
  > "We emphasize that the fiducial model does not provide a unique fit to the data." (4.1 The Fiducial Model)
- Caveat (inferred, ours): No formal fitting or uncertainty estimation; errors are judged by eye
- Caveat (inferred, ours): Single short observation; nearly face-on so kinematics weak
- Caveat (inferred, ours): Model degeneracies with many fixed parameters

## Reproducibility

- Data public (paper): ALMA program 2013.1.01020.S cited; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.01020S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Full DALI/MCRT input files and unlisted parameters
- Missing: CASA version and clean settings
- Missing: Exact by-eye criteria
- Data volume (inferred): ~10-30 GB raw
- Score (inferred): 4/5, Data is archival and the fiducial model parameters are tabulated, but modeling is by eye with several unspecified inputs.
- Rediscovery candidate: no, Results rely on by-eye radiative transfer modeling with incomplete inputs.

## Links

- Method: (cite: vandermarel16) (DALI modeling of mm continuum and CO lines)
- Method: (cite: dong12pds70) (scattered light modeling procedure)
- Companion: (cite: vandermarel15) (Cycle 0 CO 3-2 modeling of J1604)
- Companion: (cite: mathews12) (SMA observations of J1604)
- Related: SEEDS

## Checks

```json
{
 "quotes": 61,
 "quotes_ok": 61,
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
  "facts": 69,
  "stated": 42,
  "rate": 0.609
 },
 "evidence_ok": true
}
```
