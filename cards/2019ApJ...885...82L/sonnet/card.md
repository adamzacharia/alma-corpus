# Sulfur-bearing Molecules in Orion KL

`2019ApJ...885...82L` | The Astrophysical Journal 2019 | first author: Luo, Gan | arXiv: 1910.01779 | DOI: 10.3847/1538-4357/ab45ef

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation, astrochemistry
- Question: How do S-bearing species (carbon-sulfur compounds vs carbon-free species) differ in line profiles, spatial distribution, abundances and temperature dependence in Orion KL, and what does this imply for sulfur chemistry?  
  > "we found a clear dichotomy between carbon-sulfur compounds and carbon-free S-bearing species in various characteristics, e.g., line profiles, spatial morphology, and molecular abundances with respect to $\rm H_2$." (abstract)
- Target **Orion KL**: coordinates RA 05h35m14.35s, Dec -05d22m35.0s (phase center)  
  > "It is the closest high-mass star-forming region (437 $\pm$ 19 pc; (cite: Hirota2007))" (Introduction); "The phase-tracking center was at R. A. = $05^h 35^m 14^s.35$ and Dec. = $-05^\circ 22'35''.0$." (2.1 ALMA observations); z/distance 437 ± 19 pc  
  > "It is the closest high-mass star-forming region (437 $\pm$ 19 pc; (cite: Hirota2007))" (Introduction); "The phase-tracking center was at R. A. = $05^h 35^m 14^s.35$ and Dec. = $-05^\circ 22'35''.0$." (2.1 ALMA observations); distance from Hirota et al. 2007  
  > "It is the closest high-mass star-forming region (437 $\pm$ 19 pc; (cite: Hirota2007))" (Introduction); "The phase-tracking center was at R. A. = $05^h 35^m 14^s.35$ and Dec. = $-05^\circ 22'35''.0$." (2.1 ALMA observations)

## Data provenance

- ALMA projects: 2011.0.00009.SV
- bands: Band 6 (1.3 mm)  
  > "The ALMA archive data were obtained from ALMA science verification[^1] (SV) data in band 6 (project ID 2011.0.00009.SV)." (2.1 ALMA observations)
- frequencies and spectral setup: 213.719-246.619 GHz; 0.488 MHz resolution (~0.7 km/s at 230 GHz)  
  > "The ALMA spectral coverage is from 213.719 GHz to 246.619 GHz, with a spectral resolution of 0.488 MHz (corresponding to $\sim$ 0.7 $\mathrm{km\, s^{-1}\, }$at 230 GHz)." (2.1 ALMA observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 17 to 265 m  
  > "with baselines ranging from 17 to 265 m." (2.1 ALMA observations)
- angular resolution: ALMA-only 1.64'' x 1.20''; combined 1.86'' x 1.53'' (USB), 2.03'' x 1.76'' (LSB)  
  > "The combined datacube has a synthesized beam of $1.86'' \times 1.53''$ (P.A.= $-19^\circ$) in the upper sideband and $2.03'' \times 1.76''$ (P.A.= $-12.6^\circ$) in the lower sideband." (2.2 Single-dish observation with IRAM)
- max recoverable scale: _not stated_
- sensitivity: ALMA-only: continuum ~10 mJy/beam, lines 30 mJy/beam per channel; combined ~60 mJy/beam per km/s  
  > "The 1$\sigma$ root mean square (RMS) noise level of the continuum and lines are $\sim$10 m$\mathrm{Jy\, beam^{-1}\, }$and 30 m$\mathrm{Jy\, beam^{-1}\, }$per channel, respectively." (2.1 ALMA observations)
- time on source: _not stated_
- observing dates: Jan. 20, 2012  
  > "The observations were performed on Jan. 20, 2012" (2.1 ALMA observations)
- pi or archival as stated: Archival ALMA science verification data  
  > "The ALMA archive data were obtained from ALMA science verification[^1] (SV) data" (2.1 ALMA observations)
- Line: SO2 (and isotopologues) many, e.g. 4(2,2)-3(1,3) (235151.7 MHz)
- Line: 13CS 5-4 (231220.7 MHz)
- Line: H2CS 7(1,7)-6(1,6) (236727.0 MHz)
- Other facility **IRAM-30 m**: Single-dish 1.3 mm line data used to recover extended emission lost by ALMA  
  > "The ALMA-only observations filtered out $\sim$30-50% of the extended emission in general compared to the 1.3 mm line emission detected with the IRAM-30 m single-dish observations" (2.2 Single-dish observation with IRAM)
- External data: IRAM-30 m 1.3 mm Orion KL data (observational details)  
  > "(see the observational details in (cite: Feng2015))" (2.2 Single-dish observation with IRAM) [from (cite: Feng2015)]
- External data: [C18O/H2] ~ 2e-7 towards Orion KL used to derive H2 column density  
  > "\[C$^{18}$O/H$_2$\] $\sim 2 \times 10^{-7}$ towards Orion KL (cite: Frerking1982; Plume2012; Crockett2014; Giannetti2014)" (4.2 Chemical segregation) [from (cite: Frerking1982; Plume2012; Crockett2014; Giannetti2014)]
- External data: Molecular line catalogs CDMS and JPL  
  > "based on molecular databases such as the Cologne Database for Molecular Spectroscopy (CDMS, (cite: Muller2005)) or the database from from the Jet Propulsion Laboratory (JPL, (cite: Pickett1998))" (3.1 Line identification) [from (cite: Muller2005); (cite: Pickett1998)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Callisto (bandpass and flux); J0607-085 phase  
  > "Bandpass and flux calibration were performed with Callisto. Quasar J0607-085 was observed for phase calibration." (2.1 ALMA observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: MIRIAD reduction; UVMODEL used to generate model visibilities from IRAM data  
  > "First, with the task UVMODEL, model visibility data from the single-dish spectral line are generated in the UV plane." (2.2 Single-dish observation with IRAM)
- deconvolver: Clean, natural weighting  
  > "The images were deconvolved with natural weighting using the Clean algorithm." (2.1 ALMA observations)
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: performed (method not given)  
  > "Continuum subtraction was performed, and the images were reduced with the MIRIAD (cite: miriad) software." (2.1 ALMA observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: ALMA and IRAM-30m visibilities combined and jointly cleaned, natural weighting  
  > "Then, using the Clean algorithm with natural weighting, the ALMA and IRAM-30 m visibilities are combined into deconvolved images containing large-scale emission" (2.2 Single-dish observation with IRAM)
- smoothing: _not stated_
- final beam: 1.86''x1.53'' (USB), 2.03''x1.76'' (LSB)  
  > "The combined datacube has a synthesized beam of $1.86'' \times 1.53''$ (P.A.= $-19^\circ$) in the upper sideband" (2.2 Single-dish observation with IRAM)
- final rms: ~60 mJy/beam per km/s  
  > "The RMS noise level of spectral lines is $\sim$60 m$\mathrm{Jy\, beam^{-1}\, }$per $\mathrm{km\, s^{-1}\, }$." (2.2 Single-dish observation with IRAM)

### Inherited from earlier work

- Source nomenclature (hot core, mm2-mm7)  
  > "Adopting the same nomenclature as that given by (cite: Wu2012), we label the brightest condensation as the hot core and the resolved condensations as mm2-mm7." (2.1 ALMA observations) [from (cite: Wu2012)]
- IRAM-30m observation details  
  > "(see the observational details in (cite: Feng2015))" (2.2 Single-dish observation with IRAM) [from (cite: Feng2015)]

### Not stated but needed to reproduce (our reading)

- IRAM-30m data details (receiver, calibration, how obtained) only by reference to Feng2015
- Continuum-subtraction method and line-free channels
- Clean parameters (cell size, image size, masks, threshold, iterations)
- Flux scaling between IRAM and ALMA and uv range overlap treatment
- MAGIX/XCLASS initial guesses, parameter bounds, source sizes
- How species other than SO2 are fitted with fixed Trot and which lines used
- Regions/apertures defining mm2-mm7 positions for spectral extraction
- Pixel selection and S/N cutoffs for XCLASSMapfit maps

## Analysis recipe

1. **Combine ALMA and IRAM-30m data**: Convert IRAM data to MIRIAD format, create model visibilities with UVMODEL, jointly clean with natural weighting  
  > "Then, using the Clean algorithm with natural weighting, the ALMA and IRAM-30 m visibilities are combined into deconvolved images containing large-scale emission" (2.2 Single-dish observation with IRAM)
   - software: MIRIAD
   - fitting: _not stated_
   - validation: Compared amplitude vs uv-distance and recovered missing flux  
  > "see Figure [3](#fig:alma_com) for an example of the complementation of missing flux" (2.2 Single-dish observation with IRAM)
2. **Identify S-bearing lines**: XCLASS line identification against CDMS and JPL towards each substructure  
  > "using XCLASS, we identified 74 lines from 20 S-bearing isotopologues towards the hot core" (3.1 Line identification)
   - software: XCLASS
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit synthetic LTE spectra for Trot, N, linewidth, vlsr**: Isothermal 1D LTE model with optical depth, blending, source size; chi2 minimisation; low-J optically thick SO2 lines excluded  
  > "a synthetic spectrum is modeled from an isothermal object in one dimension by taking the optical depth, line blending, source size, velocity, and linewidth into account." (3.2 Synthetic spectrum fitting)
   - software: MAGIX, XCLASS
   - parameter: Algorithms: genetic, Levenberg-Marquardt, errorestim-ins  
  > "An optimal fit is obtained by using three fitting algorithms, genetic, Levenberg-Marquardt, and errorestim-ins." (3.2 Synthetic spectrum fitting)
   - assumption: LTE; other species' Trot fixed to that of SO2; same centroid velocity for isotopologues  
  > "we assume that their excitation temperatures towards individual substructures are the same as those of $\mathrm{SO_2}$." (3.2 Synthetic spectrum fitting)
   - fitting: chi2 minimisation in MAGIX  
  > "By minimizing ${\chi}^2$ in the given parameter space, MAGIX yields optimized the results as output." (3.2 Synthetic spectrum fitting)
   - validation: Isotopologue ratios compared with canonical values  
  > "to test if these assumptions are reasonable, we derive the relative abundance ratios between the $\rm{^{32}S}$-/$\rm {^{34}S}$-/$\rm {^{33}S}$- isotopologues as well as the $\rm{^{12}C}$-/$\rm{ ^{13}C}$- isotopologues" (4.1 Error budget)
4. **Pixel-by-pixel Trot and column density maps**: XCLASSMapfit with same assumptions/algorithms as MAGIX  
  > "Using XCLASSMapfit (with the same assumptions and algorithms as MAGIX), we fit the $\mathrm{T_{rot}}$ and column density maps by modeling the synthetic spectra towards all pixels." (3.3 Line spatial distribution)
   - software: XCLASS
   - fitting: _not stated_
   - validation: _not stated_
5. **Derive H2 column and relative abundances**: H2 column from C18O column using [C18O/H2] ~2e-7; abundances = N(species)/N(H2); correlate with Trot pixel by pixel  
  > "we use $\mathrm{C^{18}O}$ to estimate the $\mathrm{H_2}$ column density" (4.2 Chemical segregation)
   - assumption: [C18O/H2] ~ 2e-7; C18O optically thin (tau<=0.2); distance ~400 pc  
  > "our MAGIX fitting results indicate that this line is optically thin ($\tau \leq 0.2$)" (4.2 Chemical segregation)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **MIRIAD** : Data reduction, imaging, ALMA+IRAM combination  
  > "the images were reduced with the MIRIAD (cite: miriad) software" (2.1 ALMA observations)
- **XCLASS** : Line identification and Mapfit  
  > "Adopting the eXtended CASA Line Analysis Software Suite (XCLASS, (cite: xclass))" (3.1 Line identification)
- **MAGIX** : LTE synthetic spectrum fitting  
  > "we can use the Modeling and Analysis Generic Interface for eXternal numerical codes (MAGIX; (cite: magix)) package to perform the fitting process" (3.2 Synthetic spectrum fitting)
- **GILDAS/CLASS** : Listed in software section; use not described  
  > "MIRIAD (cite: miriad), GILDAS/CLASS (cite: Pety2005; Gildas2013), XCLASS (cite: xclass), MAGIX (cite: magix)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of S-bearing lines identified | 79 | not stated | lines | 2 | we have identified 79 molecular lines from 6 S-bearing species |
| SO2 Trot hot core | 176 | 9 | K | 3 | $\mathrm{SO_2}$       / $176 \pm 9$ |
| SO2 Trot mm7 | 68 | 11 | K | 3 | OCS                   / $68 \pm 11$ |
| 32SO2/34SO2 average | 20 | 4 | dimensionless | 3 | the average relative abundance ratio of $\mathrm{^{32}SO_2/^{34}SO_2}$ towards Orion KL is $20 \pm 4$ |
| 34S/33S from SO average | 6 | 1 | dimensionless | 3 | The average abundance ratio of $\mathrm{^{34}S/^{33}S}$ derived from $\mathrm{^{32}SO/^{34}SO}$ is 6 $\pm$ 1 |
| 12C/13C from OCS | 38 | 9 | dimensionless | 3 | the derived average $\mathrm{^{12}C/^{13}C}$ ratio (38 $\pm$ 9 from $\mathrm{O^{12}CS/O^{13}CS}$) |
| 34SO/34SO2 decrease with Trot 60-180 K | 1.5 to 0.7 | not stated | dimensionless | 5 | The $\mathrm{^{34}SO/^{34}SO_2}$ ratio decreases from 1.5 to 0.7 as the temperature increases from 60$\sim$180 K |
| OCS/SO2 ratio 40-100 K | 1.0 to 0.3 | not stated | dimensionless | 5 | The $\mathrm{OCS/SO_2}$ ratio decreases from 1.0 to 0.3 when the temperature increases from 40 K to 100 K |
| H2S/SO2 ratio | ~0.3 | not stated | dimensionless | 5 | The $\mathrm{H_2S/SO_2}$ ratio is $\rm\sim$0.3 |

## Qualitative findings

- Ring-like structure (radius ~5'') in carbon-free S species channel maps at 10-15 km/s, possibly shock-related  
  > "This ring, centered at R. A. = $05^h 35^m 14^s.235$ and Dec. = $-05^\circ 22'32''.7$, has a radius of $\sim$5$''$ in the plane of the sky." (3.3 Line spatial distribution)

## Claim tuples

- H: Carbon-sulfur compounds and carbon-free S-bearing species trace different chemistry/gas | E: Compared line profiles, maps and linewidths across substructures | R: Carbon-free species broader (12-26 km/s) and extended NE of mm4; C-S compounds narrower (2-11 km/s), concentrated on continuum peaks and south | F: Clear dichotomy between the two groups | **supported**
- H: S-species abundances depend on gas temperature | E: Pixel-by-pixel abundance vs Trot | R: Carbon-free species abundances rise by ~an order of magnitude from 40-90 K; OCS and 13CS decrease from 40 to 180 K | F: Temperature-dependent chemistry differs between groups | **supported**
- H: LTE and SO2 Trot assumptions are reasonable | E: Compared derived isotopic ratios with literature | R: Ratios consistent with canonical values | F: Assumptions reasonable | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: C18O used for H2 because continuum is hard to define and missing flux uncertain  
  > "it is difficult to define the “line-free" part for the continuum." (4.2 Chemical segregation)
- Alternative: Using dust continuum with gas-to-dust ratio for H2 rejected  
  > "Instead of using continuum emission and the gas-to-dust ratio, we use $\mathrm{C^{18}O}$ to estimate the $\mathrm{H_2}$ column density" (4.2 Chemical segregation)
- How they decided it was enough: _not stated_
- Limitation (authors): H2C34S column density may be underestimated due to narrow linewidth (2 channels)  
  > "which means that the column density of $\mathrm{H_2C^{34}S}$ may be underestimated." (4.1 Error budget)
- Caveat (inferred, ours): Single-Trot LTE assumption from SO2 applied to all species despite multiple temperature components
- Caveat (inferred, ours): C18O-based H2 with fixed abundance and ~1.6-2'' beam may be uncertain
- Caveat (inferred, ours): Mixed beam/source-size dilution and non-uniform line uncertainties; some fitted values lack errors
- Caveat (inferred, ours): Combination procedure of ALMA+IRAM not quantitatively validated

## Reproducibility

- Data public (paper): ALMA science verification archive data; IRAM data from Feng2015  
  > "The ALMA archive data were obtained from ALMA science verification[^1] (SV) data" (2.1 ALMA observations)
- Products in archive: _not stated_
- Missing: IRAM-30m dataset
- Missing: Clean parameters
- Missing: MAGIX/XCLASS setups and priors
- Missing: Region definitions
- Data volume (inferred): ~10-50 GB (SV band 6 spectral scan, plus IRAM cubes)
- Score (inferred): 3/5, ALMA SV data are public and the method is outlined, but IRAM data and fitting configurations are not fully specified.
- Rediscovery candidate: no, IRAM data and detailed fit setups are unavailable in the text, so the recipe is incomplete.

## Links

- Method: (cite: xclass) (XCLASS software)
- Method: (cite: magix) (MAGIX fitting package)
- Companion: (cite: Feng2015) (IRAM-30m observations and previous Orion KL line analysis)
- Companion: (cite: Wu2012) (continuum source nomenclature)
- Related: ALMA Science Verification Orion KL

## Checks

```json
{
 "quotes": 64,
 "quotes_ok": 64,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 44,
  "rate": 0.595
 },
 "evidence_ok": true
}
```
