# Water and interstellar complex organics associated with the HH 212 protostellar disc. On disc atmospheres, disc winds, and accretion shocks

`2018A&A...617A..10C` | Astronomy and Astrophysics 2018 | first author: Codella, C. | arXiv: 1806.07967 | DOI: 10.1051/0004-6361/201832765

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: What are the physical properties, kinematics and origin (disc atmosphere, accretion shock, disc wind) of HDO and CH3CHO emission within ~70 au of the HH 212 protostar?  
  > "We investigate the physical and chemical properties of the gas associated with water and interstellar complex organic molecules around a protostar on solar system scales." (abstract)
- Target **HH 212 mm (MM1)**: coordinates RA(J2000) 05h43m51.41s, Dec -01d02m53.17s  
  > "at a distance that has recently been estimated to be 405$\pm$15 pc (Kounkel et al. 2017; Kounkel, private communication)" (1 Introduction); "located at $\alpha({\rm J2000})$ = 05$^h$ 43$^m$ 51$s$41, $\delta({\rm J2000})$ = –01$\ensuremath{^\circ}$ 02$\ensuremath{'}$ 53$\ensuremath{''}$17" (2 Observations); z/distance 405±15 pc  
  > "at a distance that has recently been estimated to be 405$\pm$15 pc (Kounkel et al. 2017; Kounkel, private communication)" (1 Introduction); "located at $\alpha({\rm J2000})$ = 05$^h$ 43$^m$ 51$s$41, $\delta({\rm J2000})$ = –01$\ensuremath{^\circ}$ 02$\ensuremath{'}$ 53$\ensuremath{''}$17" (2 Observations); distance from Kounkel et al. 2017; Kounkel, private communication  
  > "at a distance that has recently been estimated to be 405$\pm$15 pc (Kounkel et al. 2017; Kounkel, private communication)" (1 Introduction); "located at $\alpha({\rm J2000})$ = 05$^h$ 43$^m$ 51$s$41, $\delta({\rm J2000})$ = –01$\ensuremath{^\circ}$ 02$\ensuremath{'}$ 53$\ensuremath{''}$17" (2 Observations)

## Data provenance

- ALMA projects: 2016.1.01475.S
- bands: Band 7 (Cycle 1 and Cycle 4)  
  > "HH 212 was also observed in Band 7 during Cycle 4 using 44 12m antennas" (2 Observations)
- frequencies and spectral setup: Cycle 1: SPWs 337.1–338.9 and 348.4–350.7 GHz, 488 kHz channels smoothed to 1 km/s; Cycle 4: single SPW 334.1–336.0 GHz, 0.42 km/s smoothed to 1 km/s  
  > "two spectral windows (337.1–338.9 GHz and 348.4–350.7 GHz) were simultaneously observed using spectral channels of 488 kHz" (2 Observations); "we used a single spectral window between 334.1–336.0 GHz with a 0.42 km s$^{-1}$ spectral resolution" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: 12m antennas: 34 (Cycle 1), 44 (Cycle 4)  
  > "using 34 12m antennas between 15 June and 19 July 2014" (2 Observations)
- configurations: _not stated_
- baselines: max 650 m (Cycle 1), 3 km (Cycle 4)  
  > "The maximum baselines were 650 m for Cycle 1 and 3 km for Cycle 4" (2 Observations)
- angular resolution: Cycle 1 ~0.4 arcsec; Cycle 4 0.15x0.12 arcsec  
  > "typical clean-beam FWHM of $0.15\ensuremath{''}\times0.12\ensuremath{''}$ (PA = -88$\ensuremath{^\circ}$)" (2 Observations)
- max recoverable scale: ~3 arcsec (1200 au)  
  > "the maximum unfiltered scale is $\sim$ 3$\ensuremath{''}$, that is, 1200 au" (2 Observations)
- sensitivity: rms ~2 mJy/beam (Cycle 1), ~1 mJy/beam (Cycle 4) per 1 km/s channel  
  > "an r.m.s. noise level of $\sim$ 1 mJy beam$^{-1}$ per channel" (2 Observations)
- time on source: _not stated_
- observing dates: Cycle 1: 15 June–19 July 2014; Cycle 4: 6 Oct–26 Nov 2016  
  > "between 6 October and 26 November 2016" (2 Observations)
- pi or archival as stated: _not stated_
- Line: HDO 3(3,1)-4(2,2) (335.3955 GHz)
- Line: CH3CHO 18-17 series (14 lines) (335–351 GHz)
- External data: H2 column density ~1e24 cm-2 typical of hot corinos, used for abundance  
  > "assuming H$_2$ column densities around 10$^{24}$ cm$^{-2}$, which is a typical value for hot corinos in Perseus and in B335" (4 Physical properties) [from Taquet et al. 2015, Imai et al. 2016]
- External data: HDO-H2 collisional coefficients  
  > "assuming collisional coefficients for the system HDO-H$_2$ computed by Faure et al. (2012)" (4 Physical properties) [from Faure et al. 2012]
- External data: Spectroscopic parameters from JPL database  
  > "Frequencies and spectroscopic parameters have been extracted from the Jet Propulsion Laboratory molecular database (Pickett et al. 1998)" (Table 1) [from Pickett et al. 1998]
- External data: Systemic velocity +1.7 km/s  
  > "systemic velocity $v_{\rm sys}$ = +1.7 km s$^{-1}$ (Lee et al. 2014)" (3 Spectra and images) [from Lee et al. 2014]

## Processing

### Calibration

- pipeline or manual: Standard procedures  
  > "Standard procedures were used to calibrate the data, using quasars J0607-0834, J0541–0541, J0423–013, and Ganymede." (2 Observations)
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
- continuum subtraction: Continuum from line-free channels; continuum-subtracted images  
  > "The spectral windows were also used to derive continuum from the line-free channels." (2 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Smoothed to 1 km/s  
  > "and then smoothed to 1.0 km s$^{-1}$ to increase sensitivity" (2 Observations)
- final beam: Cycle 1 ~0.41x0.33 to 0.44x0.34 arcsec (PA -63); Cycle 4 0.15x0.12 arcsec (PA -88)  
  > "clean-beam FWHMs around $0.41\ensuremath{''}\times0.33\ensuremath{''}$ to $0.44\ensuremath{''}\times0.34\ensuremath{''}$" (2 Observations)
- final rms: ~2 mJy/beam (C1), ~1 mJy/beam (C4)  
  > "an r.m.s. noise level of $\sim$ 2 mJy beam$^{-1}$ in the 1 km s$^{-1}$ channels" (2 Observations)

### Inherited from earlier work

- Hot-corino LVG method and HDO/H2O assumptions  
  > "non-LTE Large Velocity Gradient (LVG) model (see Ceccarelli et al. 2003)" (4 Physical properties) [from Ceccarelli et al. 2003]
- Continuum cannot be used to derive N(H2) (optically thick)  
  > "As stressed in Codella et al. (2016), the continuum emission, being optically thick" (4 Physical properties) [from Codella et al. 2016]
- Protostar position reference  
  > "continuum peak located at $\alpha({\rm J2000})$ = 05$^h$ 43$^m$ 51$s$41" (2 Observations) [from Lee et al. 2014]

### Not stated but needed to reproduce (our reading)

- CASA version and tclean parameters (weighting, robust, cell, image size, masks, deconvolver)
- Line-free channels used for continuum subtraction
- Flux calibrator details and flux scale uncertainty; self-calibration
- Which Cycle 1 execution blocks/project code (Cycle 1 code not printed)
- Exact rotational-diagram fit procedure and beam-dilution correction details
- LVG code input parameters (linewidth, grid ranges)
- PV diagram cut widths and position angles

## Analysis recipe

1. **Extract spectra and fit lines**: Gaussian fits to spectra at protostar position  
  > "the profiles, fit using the GILDAS package (see Table 1; note that in two cases, 2 CH$_3$CHO lines are blended), are Gaussian-like" (3 Spectra and images)
   - software: GILDAS
   - parameter: 1 km/s resolution  
  > "Gaussian fit. Spectral resolution of 1 km s$^{-1}$." (Table 1)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure emitting region size**: 2D Gaussian fits of integrated maps after beam deconvolution  
  > "obtained with 2D Gaussian fits (after deconvolving the beam size): 161$\pm$17 mas (HDO), 205$\pm$25 mas (CH$_3$CHO-A), and 213$\pm$34 mas (CH$_3$CHO-E)" (3 Spectra and images)
   - fitting: _not stated_
   - validation: _not stated_
3. **CH3CHO temperature and column density**: Rotational diagram with Cycle 1 and 4 lines, intensities corrected for 0.18 arcsec source size  
  > "derived using the rotational diagram approach (Fig. 3), assuming local thermodynamic equilibrium (LTE) conditions and optically thin emission." (4 Physical properties)
   - parameter: source size 0.18 arcsec  
  > "corrected the observed intensities for a source size (of the total emitting region) of 0$\ensuremath{''}$18" (4 Physical properties)
   - assumption: LTE, optically thin, N(H2)=1e24 cm-2 for abundance  
  > "assuming H$_2$ column densities around 10$^{24}$ cm$^{-2}$" (4 Physical properties)
   - fitting: _not stated_
   - validation: Compared with Cycle 0 results and methanol temperatures  
  > "The temperature agrees reasonably well with the Cycle 0 results reported by Codella et al. (2016)" (4 Physical properties)
4. **HDO density and column density constraints**: Non-LTE LVG model in Tkin–N(HDO) plane for n = 1e8, 1e9, 1e10 cm-3  
  > "Figure 3 shows the LVG predictions in the $T_{\rm kin}$–$N$(HDO) plane for densities of 10$^8$ cm$^{-3}$ (blue)" (4 Physical properties)
   - parameter: source size 0.18 arcsec  
  > "we can now use the measured size of 0$\ensuremath{''}$18" (4 Physical properties)
   - assumption: N(HDO)/N(H2O) <= 0.1, X_H2O = 3e-5  
  > "When we assume $N$(HDO)/$N$(H$_2$O) $\leq$ 0.1, $X_{\rm H_2O}$ = 3 $\times$ 10$^{-5}$" (4 Physical properties)
   - fitting: _not stated_
   - validation: Tkin consistent with CH3CHO  
  > "The temperatures derived from CH$_3$CHO (grey region in Fig. 3) are consistent with the solutions found with HDO." (4 Physical properties)
5. **Kinematics: moment maps, uv-plane centroids, PV diagrams**: First moment maps; elliptical Gaussian fits in uv domain per channel for sizes and centroids; PV diagrams along equatorial plane and jet axis  
  > "The sizes and centroids of the emitting regions were obtained from elliptical Gaussian fits in the $uv$ domain" (5 Kinematics)
   - software: GILDAS
   - parameter: 0.42 km/s channels for centroids  
  > "also obtained from elliptical Gaussian fits in the $uv$ domain with the original 0.42 km s$^{-1}$" (5 Kinematics)
   - fitting: GILDAS uv-fit  
  > "We used the GILDAS $uv-fit$ task, which allows fitting models directly through the $uv$ visibilities." (5 Kinematics)
   - validation: Comparison with literature kinematics and continuum disc  
  > "Although comparisons between images taken at different angular resolutions have to be made with caution, Fig. 5 suggests that HDO and CH$_3$CHO originate from a radius consistent with that of the dusty disc" (Kinematics)

## Software

- **CASA** : Spectral line imaging  
  > "Spectral line imaging was achieved with the CASA[^2] package" (2 Observations)
- **GILDAS** : Data analysis, line fits, uv-fit  
  > "data analysis was performed using the GILDAS[^3] package" (2 Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CH3CHO excitation temperature | 78 | 14 | K | 3 | We derived an excitation temperature of 78$\pm$14 K and column density of 7.6$\pm$3.2 $\times$ 10$^{15}$ cm$^{-2}$. |
| CH3CHO column density | 7.6e15 | 3.2e15 | cm-2 | 3 | column density of 7.6$\pm$3.2 $\times$ 10$^{15}$ cm$^{-2}$ |
| CH3CHO abundance | 8e-9 | not stated | dimensionless | 3 | we can infer $X_{\rm CH_3CHO}$ $\simeq$ 8 $\times$ 10$^{-9}$ |
| HDO emission size | 161 | 17 | mas | 2 | 161$\pm$17 mas (HDO), 205$\pm$25 mas (CH$_3$CHO-A), and 213$\pm$34 mas (CH$_3$CHO-E) |
| HDO density lower limit | >=1e8 | not stated | cm-3 | 4 | only densities of at least 10$^8$ cm$^{-3}$ are possible, leading to $N$(HDO) $\leq$ 3 $\times$ 10$^{17}$ cm$^{-2}$ |
| HDO column density upper limit | <=3e17 | not stated | cm-2 | 4 | leading to $N$(HDO) $\leq$ 3 $\times$ 10$^{17}$ cm$^{-2}$ |
| HDO line opacity at n=1e8 | 0.3 | not stated | dimensionless | 4 | the opacity of the HDO line is 0.3 |
| Velocity gradient | ±2 | not stated | km/s | 5 | We detect a velocity gradient ($\pm$ 2 km s$^{-1}$ with respect to the systemic velocity) |

## Qualitative findings

- HDO and CH3CHO are more compact than C17O along the equatorial plane  
  > "HDO and CH$_3$CHO are more compact than C$^{17}$O, which is more elongated along the equatorial plane." (5 Kinematics)

## Claim tuples

- H: HDO and CH3CHO trace chemically enriched gas at the centrifugal barrier of the HH 212 disc | E: Cycle 4 imaging, PV diagrams and centroid fits | R: Linear PV gradient, emission radius ~60 au | F: Emission arises from an edge-on ring where envelope meets disc, probably through low-velocity accretion shocks | **supported**
- H: Physical conditions of HDO and CH3CHO gas | E: Rotational diagram and LVG analysis | R: T=78±14 K, N=7.6e15 cm-2, n>=1e8 cm-3 | F: Warm, dense gas with X(CH3CHO)~8e-9 | **supported**
- H: iCOMs and HDO are outflowing in a disc wind | E: Low-velocity channel maps offsets | R: Peaks offset from equatorial plane at ±1 km/s | F: Possibly outflowing, expanding, rotating rings tracing the base of a wind; needs verification | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Self-gravitating structure (M∝r^3) and infall motions rejected for the velocity pattern  
  > "Other interpretations in terms of a strongly self-gravitating structure with $M$ $\propto$ $r^{3}$ are unlikely" (6.1 Origin of the iCOM emission)
- How they decided it was enough: _not stated_
- Limitation (authors): Comparisons across different angular resolutions must be treated with caution; low-velocity offset needs higher-resolution verification  
  > "Although this result has to be verified using datasets with higher spatial resolution" (6.2 Low-velocity emission)
- Caveat (inferred, ours): Optically thin LTE assumption and assumed N(H2)=1e24 make abundance uncertain
- Caveat (inferred, ours): Cycle 1 maps are unresolved yet source size from Cycle 4 applied to all lines
- Caveat (inferred, ours): Sub-beam centroid offsets from uv-fits are interpreted with small errors
- Caveat (inferred, ours): Wind interpretation is speculative

## Reproducibility

- Data public (paper): Project code 2016.1.01475.S printed (PI Codella)  
  > "This paper makes use of the ADS/JAO.ALMA#2016.1.01475.S data (PI: C. Codella)." (Acknowledgements)
- Products in archive: _not stated_
- Missing: CASA/tclean imaging parameters
- Missing: Cycle 1 project code
- Missing: Rotational diagram fitting details and LVG inputs
- Data volume (inferred): ~100-300 GB (two cycles, Band 7)
- Score (inferred): 4/5, Data public and results numeric, but imaging and fitting settings are sparse.
- Rediscovery candidate: no, Imaging recipe incomplete and Cycle 1 project code not given, though main results are numeric.

## Links

- Method: Ceccarelli et al. 2003 (LVG model)
- Method: Martí-Vidal et al. 2014 (uv-fitting over-resolution power)
- Companion: Codella et al. 2016 (Cycle 0 HDO and CH3CHO detection)
- Companion: Lee et al. 2017b (Higher-resolution iCOM disc atmosphere)
- Companion: Bianchi et al. 2017 (13CH3OH from the same Cycle 4 dataset)

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
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 45,
  "rate": 0.592
 },
 "evidence_ok": true
}
```
