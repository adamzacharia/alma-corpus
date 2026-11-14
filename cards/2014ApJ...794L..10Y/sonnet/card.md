# ALMA Observations of the IRDC Clump G34.43+00.24 MM3: 278 GHz Class I Methanol Masers

`2014ApJ...794L..10Y` | The Astrophysical Journal Letters 2014 | first author: Yanagida, Takahiro | arXiv: 1409.7143 | DOI: 10.1088/2041-8205/794/1/L10

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry, milky_way_ism
- Question: Is the CH3OH 9(-1)-8(0) E emission in G34.43+00.24 MM3 masing, and how do the maser positions relate to outflows and ambient dense gas?  
  > "we have studied the relationship between class I methanol maser emission and dense molecular gas toward G34.43+00.24 MM3 at sub-arcsecond resolution" (Introduction)
- Target **G34.43+00.24 MM3**: coordinates _not stated_; z/distance 1.56 kpc (VLBI parallax); 3-4 kpc from other methods  
  > "The distance to this object is derived to be 1.56 kpc from VLBI parallax observations (Kurayama et al. 2011)" (Introduction); distance from Kurayama et al. 2011 (VLBI parallax)  
  > "The distance to this object is derived to be 1.56 kpc from VLBI parallax observations (Kurayama et al. 2011)" (Introduction)

## Data provenance

- ALMA projects: 2011.0.00656.S
- bands: Band 7 (CH3OH 9-1-80 E); Band 6 (CH3OH 5-4 E lines)  
  > "Band 7), $J_K$=$5_0$–$4_0$ $E$ (241.70022 GHz; $E_u$$\sim$48 K; Band 6)" (Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.74"x0.50" (PA 101.4 deg) for 9-1-80 E; 0.79"x0.60" (PA 101.1 deg) for the 5-4 E lines  
  > "The synthesized beam for the $J_K$=$9_{-1}$–$8_0$ $E$ transition is 0$^{\prime\prime}$.74$\times$0$^{\prime\prime}$.50 with a P.A. of 101.4$^{\circ}$" (Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: August 2012  
  > "Our ALMA observations were carried out in August 2012." (Observations)
- pi or archival as stated: _not stated_
- Line: CH3OH 9(-1)-8(0) E (278.30451 GHz)
- Line: CH3OH 5(0)-4(0) E (241.70022 GHz)
- Line: CH3OH 5(-1)-4(-1) E (241.76722 GHz)
- Other facility **Keck**: 2.2 um K-band image (from Paper I)  
  > "Figure 1f shows the color image of 2.2 $\mu$m $K$-band from Keck telescope (Paper I)" (Results)
- External data: Transition rest frequencies from CDMS catalog  
  > "Transition rest frequencies are taken from the CDMS catalog" (Observations) [from CDMS catalog]
- External data: N2H+ J=3-2 data  
  > "where the N$_2$H$^+$ data is presented in T. Sakai et al. (2014; in preparation)" (Velocity Structures) [from T. Sakai et al. 2014 (cite: sak14)]

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
- continuum subtraction: Continuum subtracted directly from the visibilities; line images by CLEAN  
  > "The line images were obtained by CLEANing the dirty images after subtracting the continuum directly from the visibilities." (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.74"x0.50" (9-8) ; 0.79"x0.60" (5-4)  
  > "The velocity resolution of the data used in this Letter is 0.60 km s$^{-1}$." (Observations)
- final rms: _not stated_

### Inherited from earlier work

- Observation and calibration details  
  > "The details of the observations are described in Sakai et al. (2013) and T. Sakai et al. (2014, in preparation)." (Observations) [from Sakai et al. (2013) (cite: sak13); T. Sakai et al. 2014 in prep.]

### Not stated but needed to reproduce (our reading)

- CASA version
- Calibrators and flux scale
- Weighting/robust, cell and image size
- Line-free channels for continuum subtraction
- Array configuration, baselines, and integration time
- Integration velocity ranges for moment maps
- Exact line ratio to Tex formulation and column density/partition function assumptions
- Source of the CS, SiO and 1.3 mm continuum data processing

## Analysis recipe

1. **Identify maser peaks and fit line profiles**: Integrated intensity maps, identify peaks >100 mJy/beam, double Gaussian fits to the 9-8 E line  
  > "We identify 6 peaks (M1-M6) with intensity $>$ 100 mJy beam$^{-1}$." (Results)
   - software: CASA
   - parameter: Narrow widths corrected for 0.60 km/s velocity resolution  
  > "Corrected by the velocity resolution of 0.60 km s$^{-1}$ with the following equation" (Table 1)
   - fitting: Double Gaussian  
  > "Results of the double Gaussian fitting of the 9$_{-1}$–8$_0$ $E$ line." (Table 1)
   - validation: _not stated_
2. **Excitation temperature from line ratios to test inversion**: Tex from intensity ratios at 9-8 E peak velocity; negative Tex indicates population inversion  
  > "Assuming optically thin emission and local thermodynamic equilibrium excitation, we calculate the excitation temperature from the intensity ratios" (Results)
   - assumption: Optically thin, LTE  
  > "Assuming optically thin emission and local thermodynamic equilibrium excitation" (Results)
   - fitting: _not stated_
   - validation: Compared with thermal 5-4 E lines and hot core Tex of 79 K  
  > "At this position, the excitation temperature derived from the ($9_{-1}$–$8_0$ $E$)/($5_0$-$4_0$ $E$) ratio is 79 K. Thus, maser emission is either absent or very weak toward the hot core." (Results, Integrated Intensity Images and Spectra)
3. **Compare maser positions with outflow and dense gas tracers**: Overlays with 1.3 mm continuum, CS, K band; channel maps with N2H+ and CS; position-velocity cuts with SiO  
  > "we present velocity channel maps of CH$_3$OH $J_K$=$9_{-1}$–$8_0$ $E$, CS $J$=5–4 and N$_2$H$^+$ $J$=3–2 (Figure 3)" (Velocity Structures)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Data reduction  
  > "The data were reduced by using the CASA software package." (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Tex from (5-1-4-1)/(5-4) ratio | 19 to 40 | not stated | K | 2 | range from 19 K to 40 K |
| M5 peak intensity of 9-8 E | 1063 | 18 | mJy/beam | 1 | 1063 $\pm$18 |
| Hot core Tex from 9-8/5-4 ratio | 79 | +17/-11 | K | 2 | the excitation temperature derived from the ($9_{-1}$–$8_0$ $E$)/($5_0$-$4_0$ $E$) ratio is 79 K |
| Narrow component velocity width | <1 | not stated | km/s | 1 | The velocity width of the narrow component is less than 1 km s$^{-1}$. |

## Qualitative findings

- No continuum or infrared point sources toward the maser peaks  
  > "it is clear that there are no continuum peaks toward M1-M6" (Results)

## Claim tuples

- H: The 9-1-80 E line is masing | E: Compared with 5-4 E lines assuming LTE | R: Negative Tex at 6 peaks, narrow and compact | F: 9-8 E emission is maser | **supported**
- H: Masers arise from outflow-ambient gas interaction | E: Channel maps and PV diagrams with CS, SiO, N2H+ | R: Peaks on edges of N2H+ and coincident with CS/SiO | F: Masers come from post-shocked gas at interaction regions | **supported**
- H: Origin of strongest maser M5 | E: Compare SiO and CH3OH | R: SiO very weak | F: Traces relatively old or weak shocks | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Radiative heating by embedded protostars rejected for M5 due to no continuum sources  
  > "Thus, the CH$_3$OH molecule in M5 cannot originate from radiative heating by embedded protostars." (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Unclear whether maser can persist after shock ended; driving source unclear  
  > "However, it is unclear whether the maser emission can be maintained for a relatively long timescale after the shock ended." (Discussion)
- Caveat (inferred, ours): Tex from LTE optically thin ratios is not valid for masers; only a sign test
- Caveat (inferred, ours): Beam sizes differ between Band 6 and 7 lines, yet ratios are taken without stated matching
- Caveat (inferred, ours): Old vs weak shock interpretation is speculative

## Reproducibility

- Data public (paper): ALMA project 2011.0.00656.S cited; public status not stated  
  > "ADS/JAO.ALMA#2011.0.00656.S" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Calibration and imaging parameters
- Missing: Velocity ranges for integration
- Missing: Peak-position measurement method
- Data volume (inferred): ~50-100 GB
- Score (inferred): 3/5, Public data and simple analysis, but processing details deferred to other papers.
- Rediscovery candidate: no, Imaging recipe is not given and results depend on in-preparation companion data.

## Links

- Companion: Sakai et al. (2013; Paper I) (cite: sak13) (Earlier ALMA observations of MM3, with CS, SiO and Keck data)
- Companion: T. Sakai et al. 2014 in preparation (cite: sak14) (N2H+ data and details of observations)

## Checks

```json
{
 "quotes": 36,
 "quotes_ok": 36,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 62,
  "stated": 24,
  "rate": 0.387
 },
 "evidence_ok": true
}
```
