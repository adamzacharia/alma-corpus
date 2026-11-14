# The ALMA-PILS survey: isotopic composition of oxygen-containing complex organic molecules toward IRAS 16293-2422B

`2018A&A...620A.170J` | Astronomy and Astrophysics 2018 | first author: Jørgensen, J. K. | arXiv: 1808.08753 | DOI: 10.1051/0004-6361/201731667

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation, astrochemistry
- Question: What are the deuteration and 13C content of oxygen-bearing complex organic molecules on Solar System scales toward IRAS 16293-2422B?  
  > "The aim of this paper is to systematically survey the deuteration and the $^{13}$C content of a variety of oxygen-bearing complex organic molecules on Solar System scales toward the “B component” of the protostellar binary IRAS 16293–2422." (abstract)
- Target **IRAS 16293-2422B**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00278.S, 2012.1.00712.S
- bands: Band 7 (329.1-362.9 GHz) main survey; Bands 3 and 6 targeted  
  > "covering the frequency range in ALMA’s Band 7 from 329.1 to 362.9 GHz with 0.2 km s$^{-1}$ spectral and $\approx$ 0.5$''$ angular resolution (60 AU diameter)" (2.1 The ALMA PILS survey)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ≈0.5'' (60 AU diameter)  
  > "0.2 km s$^{-1}$ spectral and $\approx$ 0.5$''$ angular resolution (60 AU diameter)" (2.1 The ALMA PILS survey)
- max recoverable scale: _not stated_
- sensitivity: ≈5 mJy beam^-1 km s^-1 across the Band 7 range  
  > "reaching a sensitivity of $\approx$5 mJy beam$^{-1}$ km s$^{-1}$ across the entire frequency range" (2.1 The ALMA PILS survey)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- External data: Laboratory spectroscopy and partition functions from CDMS and JPL catalogs  
  > "The spectroscopic data were taken from the Cologne Database of Molecular Spectroscopy, CDMS (cite: cdms1; cdms2) and the Jet Propulsion Laboratory (JPL) (cite: jpl) catalog." (2.2 Laboratory spectroscopic information) [from (cite: cdms1; cdms2; jpl)]
- External data: 16O/18O ratio of 560 to derive CH3OH from CH3(18)OH  
  > "Derived from the $^{18}$O-isotopologue assuming a $^{16}$O/$^{18}$O abundance ratio of 560 (cite: wilson94)." (Table isotopologuetable) [from (cite: wilson94)]
- External data: Standard local ISM 12C/13C ratio  
  > "about half that of the standard ratio for the local ISM (cite: milam05)" (3.2 Derived column densities) [from (cite: milam05)]
- Simulation/model as data: Taquet et al. 2014 model D/H predictions compared with observations  
  > "Fig. [5](#T14_comp) compares the measured D/H ratios to the predictions on interferometric scales at three separate times after collapse" (4.3.2 Comparison with models)

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

- Data reduction and overview of PILS data  
  > "An overview of the data and reduction as well as first results from the survey are presented in (cite: jorgensen16)" (2.1 The ALMA PILS survey) [from (cite: jorgensen16)]
- Species identification and modeling procedure  
  > "For the identification and modeling of individual species we adopted the same procedure as described in (cite: jorgensen16)" (2.3 Species identification, modeling and uncertainties) [from (cite: jorgensen16)]
- Source size 0.5'', FWHM 1.0 km/s, LSR velocity 2.5-2.7 km/s  
  > "As noted in previous PILS papers (cite: coutens16; jorgensen16; lykke17), all features toward IRAS16293B are well reproduced with a source size of 0.5$''$, a line width (FWHM) of 1.0 km s$^{-1}$ and a LSR velocity of 2.5–2.7 km s$^{-1}$." (2.3 Species identification, modeling and uncertainties) [from (cite: coutens16; jorgensen16; lykke17)]

### Not stated but needed to reproduce (our reading)

- Calibration, CASA version, and imaging parameters (all deferred to Jørgensen et al. 2016)
- Exact coordinates of the half-beam and full-beam offset positions
- Distance to IRAS 16293
- Synthetic spectrum code name and fitting procedure details
- Continuum subtraction method
- Lists of lines used per species and which were excluded

## Analysis recipe

1. **Extract spectra at offset positions**: Spectra taken at positions offset 0.5'' and 1'' from the continuum peak, mainly using the full-beam offset  
  > "In the following work we therefore predominantly focus on the full beam position, but note *(i)* that we check for consistency of the fits toward the half-beam position" (3.2 Emission morphology)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit LTE synthetic spectra for column densities and Tex**: Synthetic LTE spectra including optical depth and line overlap compared with observed spectrum; only tau<0.1 transitions used; Tex grouped as 125 K or 300 K  
  > "synthetic spectra are calculated assuming that the emission from the molecules are in Local Thermodynamic Equilibrium (LTE), taking into account optical depth and line overlaps." (2.3 Species identification, modeling and uncertainties)
   - parameter: source size 0.5'', FWHM 1.0 km/s, vLSR 2.5-2.7 km/s fixed  
  > "With those parameters fixed, the remaining quantities to be derived for each species are excitation temperatures and column densities for each species." (2.3 Species identification, modeling and uncertainties)
   - assumption: LTE justified by n_H2 ≳ 1e10 cm^-3  
  > "the LTE assumption for the complex organic molecules is justified by the high density, $n_{{\rm H}_2}\gtrsim 10^{10}$ cm$^{-3}$" (2.3 Species identification, modeling and uncertainties)
   - fitting: Visual comparison of models; no formal sampler  
  > "The uncertainties for the typical fits can be estimated comparing synthetic diagrams to the observed spectra." (2.3 Species identification, modeling and uncertainties)
   - validation: Rotation diagrams for CH3OD and a-CH3CHDOH as consistency check; ±20% variation in Tex and N visibly worsens fits  
  > "models with either excitation temperatures or column densities higher or lower by 20% start providing fits that are visibly worse" (2.3 Species identification, modeling and uncertainties)
3. **Derive isotopic ratios**: Ratios of column densities of isotopologues to main species, corrected for statistical H-atom/C-atom counts  
  > "Table [\[isotopologuetable\]] lists the derived column densities for each of the species and, for the rarer isotopologues, the abundances relative to the main isotopologue." (3.2 Derived column densities)
   - fitting: _not stated_
   - validation: _not stated_

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CH3OH column density (from 18O) | 1.0e19 | 20% | cm^-2 | 2 | CH$_3$OH$^{b}$ / $1.0\times 10^{19}$ |
| CH2DOH/CH3OH | 0.071 (0.024 corrected) | not stated | dimensionless | 3 | CH$_2$DOH                       / $7.1\times 10^{17}$     / 0.071                    / 0.024 |
| 12C/13C of dimethyl ether | 34 | not stated | dimensionless | 3 | implies a $^{12}$C/$^{13}$C ratio of 34, about half that of the canonical ISM value |
| Excitation temperatures | 125 K and 300 K groups | 25 K and 60 K | K | 2 | Within the uncertainties quoted above (25 K for an excitation temperature of 125 K and 60 K for a temperature of 300 K) |

## Qualitative findings

- First interstellar detections of deuterated/13C ketene, acetaldehyde, formic acid and deuterated ethanol  
  > "The deuterated and $^{13}$C-isotopic species of ketene, acetaldehyde and formic acid, as well as deuterated ethanol, are detected unambiguously for the first time in the interstellar medium." (abstract)

## Claim tuples

- H: Do complex organics show distinct D/H groups? | E: LTE fits of deuterated isotopologues | R: Simple species ≈2%, complex species 4-8% | F: Two groups possibly reflecting formation time in ices | **supported**
- H: Do excitation temperatures differ between species? | E: Fits of each species | R: 125 K vs 300 K groups | F: Reflects binding energies/sublimation | **supported**
- H: Are 12C/13C ratios lower than ISM? | E: 13C isotopologue fits | R: Dimethyl ether lower by up to factor 2; methyl formate and ethanol tentative | F: Possible late ice formation or FUV effects | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): 13C ethanol and methyl formate only tentative; ketene main isotopologue mostly optically thick  
  > "additional observations are needed to confirm and solidify the numbers for these two species" (3.2 Derived column densities)
- Caveat (inferred, ours): Single excitation temperature per species ignores temperature gradients
- Caveat (inferred, ours): Uncertainties of 20% are judged by eye, not from a formal fit
- Caveat (inferred, ours): Vibrational partition function corrections are uncertain for deuterated species

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Synthetic spectrum code
- Missing: Calibrated data/reduction details
- Missing: Line lists and exact positions
- Data volume (inferred): Hundreds of GB for the full PILS Band 7 dataset
- Score (inferred): 3/5, Recipe is described but code, positions and reduction are deferred to prior papers.
- Rediscovery candidate: no, Fitting code and details are not given, and results are derived by visual comparison.

## Links

- Method: (cite: jorgensen16) (PILS data reduction and fitting methodology)
- Companion: (cite: coutens16) (PILS N-bearing species)
- Companion: (cite: lykke17) (PILS ethylene oxide etc.)
- Related: PILS

## Checks

```json
{
 "quotes": 30,
 "quotes_ok": 30,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 63,
  "stated": 20,
  "rate": 0.317
 },
 "evidence_ok": true
}
```
