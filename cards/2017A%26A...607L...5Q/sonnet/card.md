# Clues to NaCN formation

`2017A&A...607L...5Q` | Astronomy and Astrophysics 2017 | first author: Quintana-Lacaci, G. | arXiv: 1710.09628 | DOI: 10.1051/0004-6361/201732015

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars, astrochemistry
- Question: Where is NaCN distributed in the envelope of IRC +10216, what is its abundance profile, and is it formed from NaCl + CN?  
  > "High angular resolution maps allow us to model the abundance distribution of this molecule and check suggested formation paths." (abstract)
- Target **IRC +10216**: coordinates RA 09h47m57.446s, Dec +13d16m43.86s (J2000)  
  > "located at a distance of $\sim$ 123 pc from us (cite: IRC_distance)" (1 Introduction); "R.A.=09$^{\rm h}$47$^{\rm m}$57$^{\rm s}$446 and Dec.=13$^{\circ}$16$'$:43$''$86" (Observations); z/distance ~123 pc  
  > "located at a distance of $\sim$ 123 pc from us (cite: IRC_distance)" (1 Introduction); "R.A.=09$^{\rm h}$47$^{\rm m}$57$^{\rm s}$446 and Dec.=13$^{\circ}$16$'$:43$''$86" (Observations); distance from Groenewegen et al. 2012 (IRC_distance)  
  > "located at a distance of $\sim$ 123 pc from us (cite: IRC_distance)" (1 Introduction); "R.A.=09$^{\rm h}$47$^{\rm m}$57$^{\rm s}$446 and Dec.=13$^{\circ}$16$'$:43$''$86" (Observations)

## Data provenance

- ALMA projects: 2013.1.00432.S, 2016.1.01217.S
- bands: Band 3 (3 mm) Cycle 2 survey; 2 mm mosaic in Cycle 4  
  > "We carried out a $\lambda~3$ mm spectral survey of IRC +10216 with ALMA band 3 during Cycle 2, covering the frequency range 84.0-115.5 GHz." (2 Observations and NaCN distribution)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: compact and extended 12m configurations plus IRAM 30m short spacings; Cycle 4 seven-field mosaic  
  > "These observations consisted in a mosaic of seven fields covering a FOV of $\sim$214$''$." (Observations)
- baselines: compact ~12-300 m; extended ~30-2000 m; Cycle 4 ~12-408 m  
  > "with baselines in the range $\sim 12 - 300$ m and $\sim 30 - 2000$ m, respectively" (Observations); "The baselines of the interferometer were in the range $\sim 12 - 408$ m." (Observations)
- angular resolution: low-res ~4''x3''; high-res 0.8''x0.7''  
  > "one with a typical angular resolution of 4$''\times 3''$ , and another with a higher angular resolution of $0\mbox{\rlap{.}$''$}8\times0\mbox{\rlap{.}$''$}7$." (2 Observations and NaCN distribution)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: NaCN 6(1,6)-5(1,5) (90394.38 MHz)
- Line: NaCN 9(1,8)-8(1,7) and 10(2,8)-9(2,7) (2 mm) (145075.57 and 158616.77 MHz)
- Line: NaCl 7-6 (91169.88261 MHz)
- Line: CH3CN 6_3-5_3 (110364.35314 MHz)
- Other facility **IRAM 30m**: OTF single-dish maps for short-spacing merging  
  > "Additional observations were performed with the IRAM 30m telescope to recover the flux filtered out by the interferometer." (Observations)
- External data: NaCl abundance profile  
  > "we compared the abundance profile obtained here with that derived by (cite: NaCl_cycle0) for NaCl" (Results) [from (cite: NaCl_cycle0)]
- External data: Temperature law (T_K ~160 K at 3e15 cm)  
  > "At the regions where NaCN abundance rises ($3\times10^{15}$ cm) $T_{\mathrm{K}} \sim 160$ K (cite: Guelin2017)." (Results) [from (cite: Guelin2017)]

## Processing

### Calibration

- pipeline or manual: calibrated with CASA (details not given)  
  > "The data were calibrated using the CASA[^2] software package" (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: GILDAS imaging, SDI cleaning  
  > "imaged and cleaned with GILDAS[^3] software package. We used the SDI cleaning algorithm" (Observations)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: done before merging with 30m data  
  > "were merged, after continuum subtraction, with the short-spacing data obtained with the IRAM 30m telescope." (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: compact+30m (low-res) or compact+extended+30m (high-res)  
  > "obtained when merging both ALMA configurations plus the short-spacing data" (Observations)
- smoothing: spectral resolution smoothed to 5 km/s for high-res maps  
  > "We therefore smoothed the spectral resolution to 5km s$^{-1}$to increase the S/N." (2 Observations and NaCN distribution)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Density and temperature profiles  
  > "we assumed the density and temperature profiles adopted by (cite: NaCl_cycle0), slightly modified to follow the temperature law deduced by (cite: Guelin2017)." (3 NaCN modeling) [from (cite: NaCl_cycle0); (cite: Guelin2017)]
- Starting abundance profiles  
  > "the abundance profile was adjusted to the observation using as starting point the abundance profiles derived by (cite: innerlayer)." (3 NaCN modeling) [from (cite: innerlayer)]
- Cycle 4 observation details  
  > "For a detailed description of these ALMA-Cycle 4 observations see Velilla Prieto et al. (in prep)." (Observations) [from Velilla Prieto et al. (in prep)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibrators
- GILDAS clean parameters (weights, cell, image size, mask)
- Exact stacking procedure and weights
- Line-free channels for continuum subtraction
- Fitting method and goodness criterion for abundance profile
- Full density/temperature profiles and mass-loss rate
- Abundance profile values
- IRAM 30m merging details

## Analysis recipe

1. **Merge interferometric and 30m data and make maps**: Merge ALMA visibilities with IRAM 30m OTF data after continuum subtraction; clean with SDI  
  > "data from the ALMA compact and extended configurations were merged, after continuum subtraction, with the short-spacing data obtained with the IRAM 30m telescope." (Observations)
   - software: CASA, GILDAS
   - fitting: _not stated_
   - validation: _not stated_
2. **Stack NaCN lines**: Stack NaCN 3 mm lines; smooth high-res maps to 5 km/s  
  > "we stacked the emission from the NaCN lines presented in Table." (2 Observations and NaCN distribution)
   - software: GILDAS
   - fitting: _not stated_
   - validation: 2 mm maps show the same hollow shell  
  > "show the very same structure, confirming the presence of the hollow shell mentioned above" (2 Observations and NaCN distribution)
3. **Fit abundance profile**: LTE multi-shell model with ray tracing and beam convolution, fit to azimuthally averaged stacked intensity profiles (low and high resolution simultaneously)  
  > "we used a local thermodynamical equilibrium (LTE) multi-shell approach carried out with the MADEX code (cite: MADEX) to reproduce the observations." (3 NaCN modeling)
   - software: MADEX
   - assumption: LTE (Tex=TK); spherical emission; no IR pumping  
  > "we assumed that the emission distribution is mainly spherical." (3 NaCN modeling)
   - fitting: Abundance profile adjusted by hand/iteratively; high-S/N profile fit mandatory, low-S/N reasonable  
  > "A good fitting of the high S/N emission profile was mandatory, while a reasonable fit of the low S/N profile was enough." (3 NaCN modeling)
   - validation: _not stated_

## Software

- **CASA** : calibration  
  > "The data were calibrated using the CASA[^2] software package" (Observations)
- **GILDAS** : imaging and cleaning  
  > "imaged and cleaned with GILDAS[^3] software package." (Observations)
- **MADEX** : LTE multi-shell excitation and radiative transfer  
  > "LTE) multi-shell approach carried out with the MADEX code (cite: MADEX)" (3 NaCN modeling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Radius where NaCN abundance rises | 3e15 | not stated | cm | 3 | we found that NaCN arises at a radius of $3\times10^{15}$ cm. |
| Inner hole radius in NaCN brightness | ~1.5 | not stated | arcsec | 2 | reveal a small inner hole with a radius $\sim$ 1.5$''$ in the brightness distribution of NaCN |

## Qualitative findings

- NaCN emission forms a hollow shell, complementary to NaCl emission  
  > "its brightness distribution is complementary to that of NaCN, that is, when NaCl emission fades, NaCN emission rises." (Discussion)

## Claim tuples

- H: NaCN forms in chemical-equilibrium conditions near the photosphere | E: High-resolution ALMA+30m maps | R: Inner hole of radius ~1.5'' in NaCN | F: NaCN forms where gas has left chemical equilibrium | **supported**
- H: NaCl + CN -> NaCN + Cl is the main path | E: Compare NaCN and NaCl profiles and abundances | R: Anti-correlated emission but NaCN abundance higher than NaCl (LTE) | F: Plausible but unconfirmed; LTE likely overestimates NaCN | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: LTE used since no NaCN collisional rates exist  
  > "Since there are no available collisional rates for NaCN, we used a local thermodynamical equilibrium (LTE) multi-shell approach" (3 NaCN modeling)
- How they decided it was enough: _not stated_
- Limitation (authors): LTE assumption may overestimate NaCN abundance; IR pumping not considered  
  > "we might expect non-LTE modeling to derive lower values of $T_\mathrm{ex}$ and therefore higher level populations, higher intensities, and lower abundances" (Results)
- Caveat (inferred, ours): No uncertainties on abundances or fits
- Caveat (inferred, ours): Fitting is not statistically defined
- Caveat (inferred, ours): LTE conclusion on NaCl/NaCN ratio is weak

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: Fit procedure
- Missing: Short-spacing 30m data
- Missing: Physical model profiles from unpublished Guelin et al.
- Data volume (inferred): hundreds of GB (Band 3 survey, two configurations plus Cycle 4 mosaic)
- Score (inferred): 2/5, Recipe sparse; key details deferred to in-prep papers and 30m data are needed.
- Rediscovery candidate: no, Recipe incomplete and results few numbers.

## Links

- Method: (cite: MADEX) (Excitation and radiative transfer code)
- Companion: (cite: NaCl_cycle0) (NaCl from same ALMA Cycle 2 project)
- Companion: (cite: CH3CN) (CH3CN hollow shell)
- Related: ALMA Cycle 2 band 3 spectral survey of IRC +10216

## Checks

```json
{
 "quotes": 46,
 "quotes_ok": 46,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 2,
 "numeric_problems": 0,
 "fill": {
  "facts": 64,
  "stated": 31,
  "rate": 0.484
 },
 "evidence_ok": true
}
```
