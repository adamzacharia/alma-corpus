# Dust Properties of C II Detected z ∼ 5.5 Galaxies: New HST/WFC3 Near-IR Observations

`2017ApJ...845...41B` | The Astrophysical Journal 2017 | first author: Barisic, I. | arXiv: 1707.02980 | DOI: 10.3847/1538-4357/aa7eda

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies
- Question: What are the rest-UV slopes and luminosities of [C II]-detected z~5.5 galaxies from new HST imaging, and where do they fall on the IRX-beta diagram?  
  > "We examine the rest-frame ultra-violet (UV) properties of 10 \[C II\]$\lambda158\,{\rm \mu m}$$-$detected galaxies at $z\sim5.5$ in COSMOS using new HST/WFC3 near-infrared imaging." (abstract)
- Target **HZ1-HZ10 LBG sample in COSMOS (plus HZ5a, HZ8W, HZ6 and HZ10 sub-components)**: coordinates _not stated_; z/distance z = 5.148-5.690 (Table 1)  
  > "observed at $5 < z < 6$ in the 2 square-degree field of the *Cosmic Evolution Survey*" (2.1 Sample selection and auxiliary data); distance from Keck/DEIMOS spectroscopic redshifts  
  > "observed at $5 < z < 6$ in the 2 square-degree field of the *Cosmic Evolution Survey*" (2.1 Sample selection and auxiliary data)

## Data provenance

- ALMA projects: 2012.1.00523.S, 2011.0.00064.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.5" ALMA beam  
  > "fitted by Gaussians with the size of the ALMA beam ($\sim 0.5\ensuremath{''}$)" (3.1 Flux extraction and measurement of beta)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: ALMA Cycle 1, PI: P. L. Capak (pre-existing data, Capak et al. 2015)  
  > "ALMA Cycle 1, ADS/JAO.ALMA#2012.1.00523.S, PI: P. L. Capak." (footnote 2)
- Line: [C II] 158 um fine-structure (not stated)
- Other facility **HST/WFC3**: New F105W, F125W, F160W imaging (programs 13641, 13384) for beta and L1600  
  > "HST Cycle 22, ID 13641, PI: P. L. Capak) in F105W, F125W, and F160W" (2.2 New HST/WFC3 observations)
- Other facility **Keck/DEIMOS**: Optical spectra for redshifts and stacking  
  > "The $R=3000-4500$ Keck/DEIMOS optical spectra that are available for all 9 main galaxies" (4 Results & Discussion)
- External data: ALMA FIR and [C II] luminosities and 158 um continuum measurements  
  > "$^{a}$ Measurements by unless noted differently." (Table 1) [from Capak et al. 2015 (cite: CAPAK15)]
- External data: Updated HZ10 [C II] luminosity  
  > "$^{f}$ Updated value from (cite: PAVESI16)." (Table 1) [from (cite: PAVESI16)]

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

- ALMA data reduction and FIR/[C II] measurements taken from earlier work  
  > "See for a detailed description of this data." (footnote 2) [from Capak et al. 2015 (cite: CAPAK15)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration and imaging details
- FIR SED assumptions used for L_FIR
- Source Extractor parameter values tuned per pointing
- Stacking details for the spectra

## Analysis recipe

1. **Measure HST photometry**: Source Extractor AUTO apertures (Kron factor 2.5, min radius 3.5 px); GALFIT for HZ6 sub-components  
  > "We choose the Kron-factor (2.5) and the minimum radius (3.5px) to be the same for all pointings and wavelengths." (3.1 Flux extraction and measurement of beta)
   - software: Source Extractor, GALFIT
   - fitting: _not stated_
   - validation: Simulations show AUTO magnitudes recovered to <0.05 mag down to 25 AB  
  > "we find that we can recover the `AUTO` magnitudes better than 0.05 mag down to 25AB magnitude" (3.1 Flux extraction and measurement of beta)
2. **Measure UV slope beta**: Forward-modeling power-law SEDs convolved with filters, chi2 minimization; errors from Monte Carlo flux variation plus 0.007 mag systematic  
  > "The best $\beta_{in}$ is then found via $\chi^2~-$ minimization from the comparison of the previously obtained model fluxes and the measured fluxes of the galaxies." (3.1 Flux extraction and measurement of beta)
   - fitting: chi2 minimization on grid of beta and intercept  
  > "The best $\beta_{in}$ is then found via $\chi^2~-$ minimization from the comparison of the previously obtained model fluxes and the measured fluxes of the galaxies." (3.1 Flux extraction and measurement of $\beta$)
   - validation: 1000 simulated galaxies injected into HST pointings; offsets <0.05 in beta  
  > "we find systematic offsets in our $\beta$ measurements of less than $\Delta\beta=0.05$ at the observed magnitudes of our galaxies" (3.2 Simulations)
3. **Place on IRX-beta and stack spectra**: Compare IRX vs beta with attenuation curves; median-stack DEIMOS spectra, errors from 500 repeats  
  > "the $1\sigma$ uncertainties are derived by repeating the stacking analysis 500 times including Gaussian measurement uncertainties" (4 Results & Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **Source Extractor** : HST photometry  
  > "We use *Source Extractor* (cite: BERTIN96) to measure the fluxes of the galaxies" (3.1 Flux extraction and measurement of beta)
- **GALFIT** : HZ6 sub-component photometry  
  > "extracted using `GALFIT` (cite: CHIEN10)" (3.1 Flux extraction and measurement of beta)
- **AstroDrizzle** : combining HST exposures  
  > "the exposures are joined using the Pyraf/STSDAS `AstroDrizzle` task" (2.2 New HST/WFC3 observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HZ1 beta | -1.92 | +0.14/-0.11 | dimensionless | 2 | -1.92$_{-0.11}^{+0.14}$ |
| HZ6 (total) beta | -1.14 | +0.12/-0.14 | dimensionless | 2 | -1.14$_{-0.14}^{+0.12}$ |
| HST 5 sigma depth F105W/F125W/F160W | 26.2, 26.4, 25.9 | not stated | AB mag | 0 | reaching $26.2$, $26.4$, and $25.9\,{\rm AB}$ ($5\sigma$ in $1\ensuremath{''}$ aperture) |

## Qualitative findings

- Roughly 2/3 of galaxies are consistent with local starburst or SMC dust; 1/3 lie below the SMC curve with low IRX  
  > "We find that roughly $2/3$ of the galaxies are consistent with the dust attenuation models of local starbursts or the SMC extinction law." (4 Results & Discussion)

## Claim tuples

- H: Earlier ground-based beta measurements were biased red | E: New HST/WFC3 photometry with simulations | R: HST beta consistent within errors but systematically bluer than ground-based values | F: Some tension with dust models is relieved | **supported**
- H: The galaxies follow standard dust attenuation relations | E: IRX-beta diagram using HST beta and ALMA L_FIR | R: About 1/3 lie below the SMC curve with a large range in beta | F: Dust properties or geometry must differ from uniform mixed models | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): HZ6a and HZ6b are blended in ALMA; flux extraction uncertain by up to a factor of three  
  > "therefore the relative flux extraction is uncertain by up to a factor of three depending on the weighting" (3.1 Flux extraction and measurement of beta)
- Caveat (inferred, ours): FIR luminosities depend on single-band 158 um continuum and assumed SED
- Caveat (inferred, ours): Stacking sample is very small (3 vs few galaxies)
- Caveat (inferred, ours): Metallicity and age claims are qualitative

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA-derived L_FIR/L_CII come from earlier papers
- Missing: Source Extractor settings per pointing not given
- Data volume (inferred): small (<1 GB HST, ALMA reuse optional)
- Score (inferred): 3/5, HST recipe partly described, ALMA measurements inherited from earlier work.
- Rediscovery candidate: no, ALMA role is minor and key inputs are inherited.

## Links

- Method: Capak et al. 2015 (cite: CAPAK15) (ALMA data and FIR/[C II] measurements)
- Companion: Faisst et al., in prep (dust temperatures and FIR properties)
- Related: COSMOS
- Related: HST programs 13641 and 13384

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
 "codes_not_in_obscore": [
  "2011.0.00064.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 62,
  "stated": 21,
  "rate": 0.339
 },
 "evidence_ok": true
}
```
