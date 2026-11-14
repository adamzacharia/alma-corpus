# Reduction of the maximum mass-loss rate of OH/IR stars due to unnoticed binary interaction

`2019NatAs...3..408D` | Nature Astronomy 2019 | first author: Decin, L. | arXiv: 1902.09259 | DOI: 10.1038/s41550-019-0703-5

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type observational_alma_primary

## Science

- Fields: evolved_stars, stellar_physics
- Question: Why do extreme OH/IR stars appear to have a very short (~200-1000 yr) high mass-loss superwind phase, and what is the maximum AGB mass-loss rate?  
  > "A condundrum arises whereby the observationally determined duration of the superwind phase is too short for these stars to become white dwarfs" (abstract)
- Target **OH 26.5+0.6**: coordinates _not stated_; z/distance 1370 pc  
  > "For a distance of 1370 parsec and a wind velocity of 15 km/s" (Derived mass-loss rates for extreme OH/IR-stars); distance from _not stated_
- Target **OH 30.1-0.7**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00054.S, 2016.1.00005.S, 2016.2.00088.S
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
- Line: 12CO low-excitation rotational lines (J not specified) (not stated)
- Other facility **BIMA**: CO J=1-0 envelope size of OH 26.5+0.6 (from literature)  
  > "the CO J=1–0 line was imaged with BIMA and a CO envelope diameter of 8.5$^{\prime\prime}$$\times$5.5$^{\prime\prime}$ (FWHM) was derived" (Derived mass-loss rates for extreme OH/IR-stars)
- External data: Hydrodynamical wind patterns for binary AGB models (model M7, Fig. 15)  
  > "Of particular interest for this study is their model M7 which has a large binary period of 227 years, a binary separation of 24 stellar radii, and a wind velocity of 15 km/s" (Properties of the compact equatorial density enhancement (CEDE)) [from Mastrodemos & Morris (cite: Mastrodemos1999ApJ...523..357M)]
- External data: Stellar radii of ~900 and ~700 solar radii  
  > "For a stellar radius of $\sim$900 solar radii (OH 26.5+0.6) and $\sim$700 solar radii (OH 30.1$-$0.7)(cite: DeBeck2010A&A...523A..18D)" (Binary properties of OH 26.5+0.6 and OH 30.1$-$0.7) [from (cite: DeBeck2010A&A...523A..18D)]
- External data: Space density of type II OH/IR stars giving N~400  
  > "using the space densities derived by Ortiz et al.(cite: Ortiz1996A&A...313..180O). This yields $\sim$400 stars within a sphere of radius $\sim$4 000 parsec around the Sun" (The statistical probability) [from (cite: Ortiz1996A&A...313..180O)]

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

- Inclination estimated from radiative transfer calculations of spiral shells  
  > "one can use the outcome of radiative transfer calculations(cite: Kim2013ApJ...776...86K; Homan2015A&A...579A.118H) to estimate the inclination angle" (Binary properties of OH 26.5+0.6 and OH 30.1$-$0.7) [from (cite: Kim2013ApJ...776...86K; Homan2015A&A...579A.118H)]
- Orbital period from slope in angle-radius plot  
  > "the orbital period can be estimated from the slope of the observed emission in the angle-radius plot(cite: Kim2017NatAs...1E..60K)" (Binary properties of OH 26.5+0.6 and OH 30.1$-$0.7) [from (cite: Kim2017NatAs...1E..60K)]

### Not stated but needed to reproduce (our reading)

- ALMA bands, frequencies, array configurations, beams, sensitivity and dates (in Supplementary Information, not in text)
- CASA version and calibration/imaging parameters (robust, cell, channel width)
- How PV diagrams and angle-radius plots were extracted (cuts, PAs)
- Stellar and companion mass assumptions beyond range 5-9 Msun
- Details of ballistic simulation grid

## Analysis recipe

1. **Reduce ALMA CO data and inspect channel maps**: Data reduced with CASA; channel maps and zero-moment maps inspected for central emission and incomplete ring pattern  
  > "The data were reduced using the CASA software package(cite: CASA2007ASPC..376..127M)." (ALMA observations of OH 26.5+0.6 and OH 30.1$-$0.7)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive binary orbital period and separation**: Spiral-arm spacing and angle-radius slope give orbital period; Kepler's third law with total mass 5-9 Msun gives separation  
  > "Assuming a total mass for the binary system between 5 to 9 M$_{\odot}$ and using Kepler’s third law, the mean binary separation is 100$\pm$20 astronomical units for OH 26.5+0.6" (Binary properties of OH 26.5+0.6 and OH 30.1$-$0.7)
   - parameter: orbital speeds up to 5 km/s; arm spacing ~1" (OH 26.5+0.6), ~0.58" (OH 30.1-0.7)  
  > "assuming orbital speeds ranging up to 5 km/s" (Binary properties of OH 26.5+0.6 and OH 30.1$-$0.7)
   - assumption: Circular orbit  
  > "Assuming a circular orbit, the orbital period can be estimated from the slope of the observed emission in the angle-radius plot" (Binary properties of OH 26.5+0.6 and OH 30.1$-$0.7)
   - fitting: _not stated_
   - validation: Comparison with Mastrodemos & Morris model M7  
  > "The arm-spacing is around 400 stellar radii, which in the case of OH 26.5+0.6 would translate to $\sim1\mbox{$.\!\!^{\prime\prime}$}2$, comparable to the one derived from the ALMA data." (Properties of the compact equatorial density enhancement (CEDE))
3. **Estimate density enhancement of CEDE**: Ballistic trajectory calculations (lower limit) and comparison of Kim & Taam simulations  
  > "A lower limit for the density enhancement of the compact equatorial density enhancement (CEDE) can be obtained using ballistic trajectory calculations" (Properties of the compact equatorial density enhancement (CEDE))
   - software: ballistic trajectory code (El Mellah & Casse)
   - parameter: mass ratio 5, donor filling factor 10%, beta = 2 or 3  
  > "where the binary mass ratio has been set to 5 and the filling factor of the donor star to 10%" (Properties of the compact equatorial density enhancement (CEDE))
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Data reduction and making Figs. 1-3  
  > "Figs. 1–3, and Supplementary Figs. 1–2 are made using CASA(cite: CASA2007ASPC..376..127M)." (Methods)
- **python script** : Angle-radius plot (Supplementary Fig. 3)  
  > "Supplementary Fig. 3 is made using a simple python script that can be distributed upon request." (Methods)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Orbital period OH 26.5+0.6 | ~430 | not stated | yr | 2 | We deduce an orbital period of $\sim$430 ($\sim$590) years |
| Orbital period OH 30.1-0.7 | ~590 | not stated | yr | 2 | We deduce an orbital period of $\sim$430 ($\sim$590) years |
| Binary separation OH 26.5+0.6 | 100 | 20 | au | 2 | the mean binary separation is 100$\pm$20 astronomical units for OH 26.5+0.6 and 123$\pm$22 astronomical units for OH 30.1$-$0.7 |
| Binary separation OH 30.1-0.7 | 123 | 22 | au | 2 | the mean binary separation is 100$\pm$20 astronomical units for OH 26.5+0.6 and 123$\pm$22 astronomical units for OH 30.1$-$0.7 |
| Inclination OH 26.5+0.6 | ~60-75 | not stated | deg | 2 | between $\sim$60$^\circ$ – 75$^\circ$ for OH 26.5+0.6, and between $\sim$50$^\circ$ – 70$^\circ$ for OH 30.1$-$0.7 |
| CEDE density contrast | ~10 | factor of a few up to ~100 possible | dimensionless | 3 | the CEDE has a density contrast of a factor $\sim$10 with respect to the background wind density |

## Qualitative findings

- Incomplete ring-like patterns and PV diagrams reveal binary-induced shell-like spirals in both stars  
  > "The PV diagrams prove that the circumstellar envelope of both targets is shaped by a *binary-induced shell-like spiral*" (ALMA observations of OH 26.5+0.6 and OH 30.1$-$0.7)

## Claim tuples

- H: Are extreme OH/IR stars binaries whose companions mimic a short superwind? | E: ALMA 12CO channel maps and PV diagrams compared with binary hydrodynamic models | R: Spiral/ring patterns detected; CEDE with ~10x density contrast | F: Short superwind duration is an artefact of a binary-induced CEDE | **supported**
- H: What is the maximum AGB mass-loss rate? | E: Argue that CO-based rates are reliable and dust-based rates overestimated | R: CO rates ~(0.1-3)e-5 Msun/yr | F: Maximum rate is near the single-scattering limit | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): ALMA data cannot give the companion mass  
  > "The current ALMA data do not allow an accurate estimate of the companion’s mass." (Binary properties of OH 26.5+0.6 and OH 30.1$-$0.7)
- Caveat (inferred, ours): Simulations used were not tuned to these stars (primary 1.5 Msun)
- Caveat (inferred, ours): Only two stars observed; generalisation to all extreme OH/IR stars is statistical
- Caveat (inferred, ours): Binomial argument assumes independence and a 10,000 yr lifetime

## Reproducibility

- Data public (paper): ALMA data retrievable from the archive  
  > "The ALMA data from proposals 2015.1.00054.S, 2016.1.00005.S, and 2016.2.00088.S can be retrieved from the ALMA data archive" (Methods)
- Products in archive: _not stated_
- Code: Python script and ballistic code only on request  
  > "The code is available for collaboration with I.E.M. upon reasonable request." (Methods)
- Missing: Observational setup and imaging parameters
- Missing: PV cut definitions
- Missing: Radiative transfer details for inclination
- Data volume (inferred): ~50-200 GB
- Score (inferred): 3/5, Public data, but processing details are in supplementary material and the analysis is largely qualitative.
- Rediscovery candidate: no, Recipe is incomplete and main results are mostly qualitative/model-comparison.

## Links

- Method: Kim & Taam 2012 (cite: Kim2012ApJ...759...59K) (Spiral-shell hydrodynamics and density contrast)
- Method: Homan et al. 2015 (cite: Homan2015A&A...579A.118H) (PV diagrams of spiral shells)

## Checks

```json
{
 "quotes": 34,
 "quotes_ok": 34,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 21,
  "rate": 0.304
 },
 "evidence_ok": true
}
```
