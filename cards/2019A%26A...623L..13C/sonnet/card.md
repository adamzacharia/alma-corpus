# The ALMA-PILS survey: First detection of nitrous acid (HONO) in the interstellar medium

`2019A&A...623L..13C` | Astronomy and Astrophysics 2019 | first author: Coutens, A. | arXiv: 1903.03378 | DOI: 10.1051/0004-6361/201935040

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: astrochemistry, star_formation
- Question: Is nitrous acid (HONO) present in the ISM towards IRAS16293 B, what are its abundance and excitation, and can a gas-grain chemical model reproduce it along with other nitrogen oxides?  
  > "In this letter, we present the first interstellar detection of HONO." (Introduction)
- Target **IRAS 16293-2422 B**: coordinates one-beam offset SW of continuum peak of source B: RA 16h32m22.58s, Dec -24d28m32.8s (J2000)  
  > "located at a distance of $\sim$140 pc in the $\rho$ Ophiuchus cloud complex (cite: Dzib2018)" (Introduction); "($\alpha_{\rm J2000}$=16$^{\rm h}$32$^{\rm m}$22$s$58, $\delta_{\rm J2000}$=-24$\ensuremath{^\circ}$28$\ensuremath{'}$32.8$\ensuremath{''}$)" (Observations and analysis); z/distance ~140 pc  
  > "located at a distance of $\sim$140 pc in the $\rho$ Ophiuchus cloud complex (cite: Dzib2018)" (Introduction); "($\alpha_{\rm J2000}$=16$^{\rm h}$32$^{\rm m}$22$s$58, $\delta_{\rm J2000}$=-24$\ensuremath{^\circ}$28$\ensuremath{'}$32.8$\ensuremath{''}$)" (Observations and analysis); distance from Dzib et al. 2018  
  > "located at a distance of $\sim$140 pc in the $\rho$ Ophiuchus cloud complex (cite: Dzib2018)" (Introduction); "($\alpha_{\rm J2000}$=16$^{\rm h}$32$^{\rm m}$22$s$58, $\delta_{\rm J2000}$=-24$\ensuremath{^\circ}$28$\ensuremath{'}$32.8$\ensuremath{''}$)" (Observations and analysis)

## Data provenance

- ALMA projects: 2013.1.00278.S
- bands: Band 7 (PILS); band 3 and band 6 PILS data also searched  
  > "The survey covers part of Band 7 in the spectral range 329.147–362.896 GHz" (Observations and analysis)
- frequencies and spectral setup: 329.147–362.896 GHz, 0.2 km/s resolution  
  > "The survey covers part of Band 7 in the spectral range 329.147–362.896 GHz, at a spectral resolution of 0.2 km s$^{-1}$" (Observations and analysis)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: circular restoring beam of 0.5"  
  > "A circular restoring beam of 0$\ensuremath{''}$5 was used to produce the final dataset." (Observations and analysis)
- max recoverable scale: _not stated_
- sensitivity: 6–10 mJy/beam/channel (4–5 mJy/beam km/s)  
  > "with a sensitivity of 6–10 mJy beam$^{-1}$ channel$^{-1}$ (i.e., 4–5 mJy beam$^{-1}$ km s$^{-1}$)" (Observations and analysis)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: trans-HONO 12 unblended lines, e.g. 14 3 12 – 13 3 11 (329519.5–362397.6 MHz (Table of lines))
- Line: HNO 4_{1,3} – 3_{1,2} (332106.6 MHz)
- External data: Column densities of NO, N2O, NH2OH towards IRAS16293 B  
  > "$^{\ddagger}$Results from (cite: ligterink2018)." (Table 1) [from (cite: ligterink2018)]
- External data: trans/cis HONO energy difference 130.2 cm-1  
  > "The trans/cis energy difference (130.2 cm$^{-1}$) is from (cite: Varma1976)." (Observations and analysis) [from (cite: Varma1976)]
- External data: 1D radiative hydrodynamical collapse physical structure  
  > "we have used the physical structure derived from a 1D radiative hydrodynamical model (cite: 2008ApJ...674..984A)" (Chemical modeling of HONO) [from (cite: 2008ApJ...674..984A)]

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
- final beam: 0.5" circular  
  > "A circular restoring beam of 0$\ensuremath{''}$5 was used to produce the final dataset." (Observations and analysis)
- final rms: _not stated_

### Inherited from earlier work

- Observations, data reduction and overview of PILS survey  
  > "This survey, taken with the Atacama Large Millimeter/submillimeter Array (ALMA), is fully described in (cite: jorgensen2016)." (Observations and analysis) [from (cite: jorgensen2016)]
- LTE fitting approach and background temperature correction  
  > "Similar to previous PILS studies (e.g., (cite: ligterink2018)), the observed spectra were fitted with a synthetic spectrum, assuming Local Thermodynamic Equilibrium (LTE) conditions" (Observations and analysis) [from (cite: calcutt2018; ligterink2018)]
- Two-step (cold core then collapse) chemical modeling  
  > "The chemical modeling was done in two steps as in similar previous studies of IRAS16293 (cite: Andron2018)" (Chemical modeling of HONO) [from (cite: Andron2018)]
- Chemical network updated from earlier network  
  > "we have updated the gas and grain chemical network used in (cite: Loison2019)" (Chemical modeling of HONO) [from (cite: Loison2019)]

### Not stated but needed to reproduce (our reading)

- Exact spectral line-free/continuum handling and continuum subtraction (in PILS paper)
- Exact pixel/beam extraction method of spectra
- Full chemical network (only HONO reactions in Table C.1)
- Initial elemental abundances and grain parameters for Nautilus
- Fit weighting/noise values used in chi2
- Line widths fit details for HONO beyond FWHM 1 km/s

## Analysis recipe

1. **Identify HONO lines and check blending**: Compare candidate lines with template of previously detected species in PILS spectra, using JPL and CDMS spectroscopy  
  > "we compared all lines tentatively identified as HONO with a template containing the lines of the molecules previously detected in this source" (Observations and analysis)
   - software: CASSIS
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive HONO column density and Tex**: LTE synthetic spectrum chi2 grid fit  
  > "A $\chi^{2}$ minimisation routine was employed to find the best-fit model to the observed data and derive the column density ($N$) and excitation temperature" (Observations and analysis)
   - software: CASSIS
   - parameter: Tex grid 50–300 K step 25 K; N grid 5e14–3e15 cm-2 step 1e14  
  > "The grid covers excitation temperatures between 50 and 300 K with steps of 25 K." (Observations and analysis)
   - assumption: source size 0.5", VLSR 2.5 km/s, background temperature 21 K  
  > "using a source size of 0$\ensuremath{''}$5 and a $V_{\rm LSR}$ velocity of 2.5 km s$^{-1}$" (Observations and analysis)
   - fitting: chi2 minimisation including three undetected transitions to avoid bias  
  > "we included some undetected transitions (333925.02, 348264.91, and 358979.13 MHz) that are predicted to be above the noise limit for certain models in the grid" (Observations and analysis)
   - validation: _not stated_
3. **Upper limits for HNO, NO+, NO2, HNO3**: 3sigma upper limits at Tex=100 K from line-free regions/brightest predicted lines  
  > "3$\sigma$ upper limit column densities were determined for $T_{\rm ex}$ = 100 K." (Upper limit determination of HNO, NO+, NO2, and HNO3)
   - fitting: _not stated_
   - validation: _not stated_
4. **Model HONO formation chemistry**: Nautilus gas-grain model: cold core phase 1e6 yr then collapse from 1D radiative hydro model, parcel arriving at 62.4 au; compare abundance ratios  
  > "For these simulations, we have used these parcels arriving at 62.4 au at the end of the simulations" (Chemical modeling of HONO)
   - software: Nautilus
   - parameter: cold phase: T=10 K, nH=1e4 cm-3, Av=15, zeta=1.3e-17 s-1  
  > "a gas and dust temperature of 10 K, an atomic H density of $10^4$ cm$^{-3}$, a visual extinction ($A_{\rm V}$) of 15" (Chemical modeling of HONO)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASSIS** : line analysis and LTE spectral fitting  
  > "the CASSIS line analysis software[^1], as well as the Jet Propulsion Laboratory" (Observations and analysis)
- **Nautilus** : gas-grain chemical modeling  
  > "This network was then used with the Nautilus gas-grain model" (Chemical modeling of HONO)
- **Gaussian 2009** 2009: reaction exothermicities at M06-2X/AVTZ  
  > "calculated at M06-2X/AVTZ level using Gaussian 2009 software" (Chemical reactions for HONO)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HONO column density | 9e14 | ±5e14 (3σ) | cm-2 | 2 | (9$\pm$5) $\times$ 10$^{14}$ |
| HONO excitation temperature | 100 | not stated | K | 2 | The best-fit model is obtained for an excitation temperature of 100 K and a column density of 9 $\times$ 10$^{14}$ cm$^{-2}$. |
| HONO column density at fixed Tex=300 K | 1.4e15 | not stated | cm-2 | 2 | the best-fit column density is 1.4 $\times$ 10$^{15}$ cm$^{-2}$ |
| HNO upper limit | ≤3e14 | 3σ | cm-2 | 3 | $\leq$ 3 $\times$ 10$^{14}$ |
| NO2 upper limit | ≤2e16 | 3σ | cm-2 | 3 | 3 $\times$ 10$^{14}$, 2 $\times$ 10$^{14}$, 2 $\times$ 10$^{16}$, and 5 $\times$ 10$^{14}$ cm$^{-2}$ for HNO, NO$^{+}$, NO$_{2}$, and HNO$_{3}$ |
| Observed HONO/NO | 4.5e-2 | not stated | dimensionless | 2 | 4.5 $\times$ 10$^{-2}$ |
| Observed HONO/CH3OH | 9e-5 | not stated | dimensionless | 2 | 9 $\times$ 10$^{-5}$ |

## Qualitative findings

- HONO emission is compact around IRAS16293 B, like COMs and NO  
  > "show that the emission is quite compact around IRAS16293 B" (Observational results)

## Claim tuples

- H: HONO is present in the ISM towards IRAS16293 B | E: Line search in ALMA-PILS Band 7 with LTE fitting and blending check | R: 12 unblended lines, Tex ~100 K, N ~9e14 cm-2 | F: First interstellar detection of HONO | **supported**
- H: A gas-grain model can reproduce observed nitrogen oxide abundances | E: Nautilus with updated network, compared ratios | R: HONO, N2O, NO2 reproduced; NO, HNO, NH2OH not | F: Partial agreement; possible destructive thermal desorption, UV photodestruction or missing reactions | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Tex=300 K model rejected: overproduces undetected lines  
  > "the model at 300 K overproduces some undetected lines at 333925.02, 348264.91, and 358979.13 MHz" (Observational results)
- How they decided it was enough: _not stated_
- Limitation (authors): Three lines underproduced, possibly blends or non-LTE infrared pumping  
  > "Three lines (329519.48, 329685.92, and 355001.15 GHz) have their fluxes underproduced by the best-fit model and could be blended with unknown species" (Observational results)
- Caveat (inferred, ours): Single-position LTE fit with assumed 0.5" source size
- Caveat (inferred, ours): Chemical model compared at one radius with few free choices explored
- Caveat (inferred, ours): Uncertainties on column density large (~50%)

## Reproducibility

- Data public (paper): PILS data from ALMA project 2013.1.00278.S  
  > "This paper makes use of the ALMA data ADS/JAO.ALMA#2013.1.00278.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Full chemical network and Nautilus inputs
- Missing: PILS calibrated cubes processing details (in Jørgensen 2016)
- Data volume (inferred): ~100s of GB raw; calibrated PILS cubes tens of GB
- Score (inferred): 3/5, Public data and clear LTE grid, but the chemical model network is not fully given and imaging is inherited from PILS.
- Rediscovery candidate: yes, Public data, explicit LTE grid, numeric results (N, Tex).

## Links

- Method: (cite: jorgensen2016) (PILS survey description and data reduction)
- Method: (cite: ligterink2018) (LTE fitting approach and NO/N2O results)
- Companion: (cite: Loison2019) (chemical network basis)
- Related: ALMA-PILS

## Checks

```json
{
 "quotes": 47,
 "quotes_ok": 47,
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
  "facts": 71,
  "stated": 31,
  "rate": 0.437
 },
 "evidence_ok": true
}
```
