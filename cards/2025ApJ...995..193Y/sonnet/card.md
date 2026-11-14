# The ALMA-QUARKS Survey: Evidence of a Candidate High-mass Prestellar Core Aside a Bright-rimmed Cloud IRAS 18290-0924

`2025ApJ...995..193Y` | The Astrophysical Journal 2025 | first author: Yang, Dongting | arXiv: 2511.15079 | DOI: 10.3847/1538-4357/ae2250

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation
- Question: Is the C2 core in the bright-rimmed cloud IRAS 18290-0924 a high-mass prestellar core candidate (unfragmented, no star-formation signatures, gravitationally bound)?  
  > "we utilize ALMA two-band observations (see Sect. [2](#sec:obs)) to perform a comprehensive analysis of the C2 core with the aim of assessing its evolutionary stage and evaluating its candidacy as a high-mass prestellar core." (Introduction)
- Target **IRAS 18290-0924 (C2 core)**: coordinates 18:31:42.68 -09:22:27.28 (ICRS, core, Band 3)  
  > "Located at a kinematic distance of $\sim5.34\pm0.5$ kpc" (Introduction); "Core | 18:31:42.68 | -09:22:27.28" (Table 1); z/distance ~5.34±0.5 kpc (kinematic)  
  > "Located at a kinematic distance of $\sim5.34\pm0.5$ kpc" (Introduction); "Core | 18:31:42.68 | -09:22:27.28" (Table 1); distance from (cite: 2018MNRAS.473.1059U; 2021A&A...646A..74M; 2014ApJ...790...84L)  
  > "Located at a kinematic distance of $\sim5.34\pm0.5$ kpc" (Introduction); "Core | 18:31:42.68 | -09:22:27.28" (Table 1)

## Data provenance

- ALMA projects: 2019.1.00685.S, 2021.1.00095.S
- bands: Band 3 (~3 mm, ATOMS) and Band 6 (~1.3 mm, QUARKS)  
  > "QUARKS observations were obtained with three different ALMA configurations at Band 6 ($\sim\rm1.3\,mm$)" (Observations)
- frequencies and spectral setup: ATOMS: 8 SPWs (six ~0.2-0.4 km/s, two wide ~1.8 GHz at ~1.6 km/s); QUARKS: 4 SPWs of ~1.8 GHz, ~1.3 km/s  
  > "Four SPWs were configured for the QUARKS survey, with a bandwidth of $\sim$1.8 GHz and a velocity resolution of $\sim\rm 1.3\,km\,s^{-1}$ for each SPW." (Observations)
- continuum bandwidth: _not stated_
- arrays: ATOMS: ACA 7-m + 12-m; QUARKS: ACA, 12-m C-2 (TM2), C-5 (TM1)  
  > "which were performed using the ACA 7-m array, the ALMA 12-m compact array C-2 (TM2) and extended C-5 (TM1) configurations, respectively." (Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~2'' (3 mm continuum); ~0.3'' (1.3 mm combined)  
  > "Combining three configuration observations from the QUARKS survey for both continuum and line data yielded a synthesized beam size of $\sim0.3$ $''$." (Observations)
- max recoverable scale: _not stated_
- sensitivity: rms ~0.1 mJy/beam (3 mm); ~0.14 mJy/beam (1.3 mm)  
  > "The combined QUARKS continuum data of the I18290 region have a typical sensitivity of rms ($\sigma_{\rm 1.3\,mm}$) $\sim0.14\,\rm mJy~beam^{-1}$." (Observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: H13CO+ 1-0 (not stated)
- Line: N2D+ 3-2 (not stated)
- Line: CO 2-1 (not stated)
- External data: Clump-average dust temperature 22 K from SED (upper limit temperature)  
  > "the average dust temperature of the natal clump (22 K, derived from the spectral energy distribution, (cite: 2018MNRAS.473.1059U))" (Results) [from (cite: 2018MNRAS.473.1059U)]
- External data: Dust opacity 0.18 and 0.9 cm2/g at 3 mm and 1.3 mm  
  > "The dust opacity, $\kappa_{\nu}$, is taken as 0.18 $\rm cm^2~g^{-1}$ and 0.9 $\rm cm^2~g^{-1}$ for the 3 mm and 1.3 mm continuum emission, respectively" (Results) [from (cite: 1994A&A...291..943O)]

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
- array combination: ACA and 12-m data combined (ATOMS); three QUARKS configurations combined  
  > "ACA and 12-m array data from the ATOMS survey were combined to produce continuum and images and line cubes" (Observations)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ATOMS survey observing and data processing details  
  > "Further details regarding the ATOMS survey are available in (cite: 2020MNRAS.496.2790L)." (Observations) [from (cite: 2020MNRAS.496.2790L)]
- QUARKS survey details  
  > "More details regarding the QUARKS survey are available in (cite: 2024RAA....24b5009L), (cite: 2024RAA....24f5011X), and (cite: 2025ApJS..280...33Y)." (Observations) [from (cite: 2024RAA....24b5009L; 2024RAA....24f5011X; 2025ApJS..280...33Y)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration/imaging pipeline details (inherited from survey papers)
- Weighting/robust, cell size, deconvolver, masks for the continuum and cubes
- imfit region/fit box and how errors were set
- Line-free channels and continuum subtraction
- How line widths were fitted and uncertainties on sigma_obs
- Details of the magnetic-field virial calculation (Pillai Eq. 5)

## Analysis recipe

1. **Fit core and condensation sizes and fluxes**: 2D Gaussian fit with CASA imfit to ATOMS 3 mm and QUARKS 1.3 mm continuum  
  > "The *imfit* task involves a two-dimensional Gaussian fit to the continuum emission of structures." (Results)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive mass and density**: Optically thin dust mass with Planck function, T=10-22 K; spherical density  
  > "If we assume that the 3 mm and 1.3 mm continuum emission is optically thin and mainly arises from thermal dust radiation" (Results)
   - assumption: Gas-to-dust ratio 100; kappa 0.18/0.9 cm2/g; mu=2.8; D=5.34 kpc  
  > "$R_{\rm gd}$ is the ratio of gas to dust (assumed to be 100)" (Results)
   - fitting: _not stated_
   - validation: _not stated_
3. **Search for star-formation activity**: Inspect averaged spectra and CO (2-1) high-velocity emission for outflows; compare with literature  
  > "No CO outflow is detected towards the massive core C2 in the I18290 region." (Results)
   - fitting: _not stated_
   - validation: Consistency with earlier SiO/HCO+ non-detection of outflows  
  > "The absence of the outflow signature in the line transitions investigated is consistent with the findings of (cite: 2023MNRAS.520..322Z)." (Results)
4. **Virial analysis**: alpha_vir = 5 sigma^2 R/(G M) using H13CO+ (core) and N2D+ (condensation) line widths with thermal subtraction  
  > "The nonthermal velocity dispersion is $\sigma_{\rm nt}=(\sigma_{\rm line}^2-\frac{k_BT}{m_{\rm line}})^{1/2}$" (Results)
   - assumption: Uniform spherical structure; mu_p=2.33  
  > "where $\mu_{p}=2.33$ is the mean molecular weight per free particle" (Results)
   - fitting: Gaussian fits to averaged spectra  
  > "Gaussian fitting of the average spectra of $\rm H^{13}CO^+$ molecular emission from the C2 core using the ATOMS data" (Figure 4 caption)
   - validation: _not stated_

## Software

- **CASA** : imfit Gaussian fits to continuum maps  
  > "the *imfit* task in *CASA* (cite: 2022PASP..134k4501C) was used to extract structures" (Results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| C2 core mass (3 mm) | 26.9-68.2 (T=22-10 K) | ±5.2 / ±13.4 | Msun | 2 | / Core / 2800$\pm$500 / 0.62$\pm$0.37 / 10 / 68.2$\pm$13.4 / |
| Condensation mass (1.3 mm) | 6.1-19.1 | ±1.2 / ±3.6 | Msun | 2 | the estimated masses of the C2 core and condensation are 26.9-68.2 $M_{\odot}$ and 6.1-19.1 $M_{\odot}$ at 3 mm and 1.3 mm |
| Core radius | 2800 | ±500 | au | 2 | / Core / 2800$\pm$500 / |
| Core virial parameter | 0.10 (10 K), 0.27 (22 K) | ±0.03 / ±0.09 | dimensionless | 4 | / 22 / 26.9$\pm$5.2 / 0.4$\pm$0.2 / 0.27$\pm$0.09 / |
| Observed H13CO+ velocity dispersion of core | 0.62 | ±0.37 | km/s | 4 | 0.62$\pm$0.37 |

## Qualitative findings

- C2 core is unfragmented at ~0.3'' with a single compact condensation, no outflows, and only cold-gas lines detected.  
  > "Only a single compact condensation is observed in the core C2" (Results)

## Claim tuples

- H: C2 is a high-mass prestellar core candidate | E: Two-band continuum masses, line survey for outflows/warm-gas tracers, virial analysis | R: 27-68 Msun within ~2800 au, no fragmentation, no outflows, alpha_vir ~0.1-0.3 | F: C2 is a candidate high-mass prestellar core | **supported**
- H: C2 is gravitationally bound and may collapse | E: Virial parameter from H13CO+ and N2D+ widths | R: alpha_vir ~0.1-0.3 | F: Bound, requires ~mG fields to be stable | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Conclusive classification requires chemical evolution analysis; N2D+ only marginally detected.  
  > "a conclusive classification also hinges on the chemical evolution analysis" (Discussion and conclusions)
- Caveat (inferred, ours): Dust temperature is unconstrained (10-22 K) so masses uncertain by factor ~2.5
- Caveat (inferred, ours): N2D+ marginal detection drives the condensation virial parameter
- Caveat (inferred, ours): Single-core study; low alpha_vir requires unmeasured strong B field
- Caveat (inferred, ours): Free-free or line contamination of continuum not discussed

## Reproducibility

- Data public (paper): Project IDs given; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2019.1.00685.S and ADS/JAO.ALMA#2021.1.00095.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging parameters and CASA version
- Missing: imfit regions
- Missing: Line fit procedure and velocity-integration details
- Data volume (inferred): ~50-200 GB for ATOMS + QUARKS (multi-config) raw data
- Score (inferred): 3/5, Simple analysis with stated equations and parameters, but imaging and fitting details are inherited from survey papers.
- Rediscovery candidate: no, Imaging recipe incomplete; relies on survey products and ambiguous choices.

## Links

- Method: (cite: 2020MNRAS.496.2790L) (ATOMS survey description)
- Method: (cite: 2024RAA....24b5009L) (QUARKS survey description)
- Companion: (cite: 2023MNRAS.520..322Z) (Earlier ATOMS study proposing C2 as prestellar candidate)
- Related: ATOMS
- Related: QUARKS
- Related: ALMA-IMF

## Checks

```json
{
 "quotes": 42,
 "quotes_ok": 42,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 64,
  "stated": 26,
  "rate": 0.406
 },
 "evidence_ok": true
}
```
