# ALMA Observations of the IRDC Clump G34.43+00.24 MM3: DNC/HNC Ratio

`2015ApJ...803...70S` | The Astrophysical Journal 2015 | first author: Sakai, Takeshi | arXiv: 1503.01827 | DOI: 10.1088/0004-637X/803/2/70

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: What is the DNC/HNC abundance ratio at high resolution in the IRDC clump G34.43+00.24 MM3, and why does it differ from the single-dish value?  
  > "We derive the DNC/HNC abundance ratio in the densest part of G34.43+00.24 MM3, and assess a relationship between star formation activity and the DNC/HNC abundance ratio." (Introduction)
- Target **G34.43+00.24 MM3**: coordinates RA 18h53m20.4s, Dec +1d28m23.0s (J2000, phase center)  
  > "The distance to this IRDC is estimated from VLBI parallax observations (1.56 kpc; Kurayama et al. 2011), and Sakai et al. (2013) used this distance." (Introduction); "The phase center was (R.A.(J2000), Dec.(J2000)) = (18$^{\rm h}$53$^{\rm m}$20.4$^{\rm s}$, 1$^{\circ}$28$^{\prime}$23.0$^{\prime\prime}$)." (2 OBSERVATIONS); z/distance 1.56 kpc (VLBI); kinematic/extinction distances 3-4 kpc discussed  
  > "The distance to this IRDC is estimated from VLBI parallax observations (1.56 kpc; Kurayama et al. 2011), and Sakai et al. (2013) used this distance." (Introduction); "The phase center was (R.A.(J2000), Dec.(J2000)) = (18$^{\rm h}$53$^{\rm m}$20.4$^{\rm s}$, 1$^{\circ}$28$^{\prime}$23.0$^{\prime\prime}$)." (2 OBSERVATIONS); distance from Kurayama et al. 2011 (VLBI parallax)  
  > "The distance to this IRDC is estimated from VLBI parallax observations (1.56 kpc; Kurayama et al. 2011), and Sakai et al. (2013) used this distance." (Introduction); "The phase center was (R.A.(J2000), Dec.(J2000)) = (18$^{\rm h}$53$^{\rm m}$20.4$^{\rm s}$, 1$^{\circ}$28$^{\prime}$23.0$^{\prime\prime}$)." (2 OBSERVATIONS)

## Data provenance

- ALMA projects: 2011.0.00656.S
- bands: Band 6 (211-275 GHz) and Band 7 (275-373 GHz)  
  > "We observed G34.43+00.24 MM3 with ALMA Band 6 (211-275 GHz) and Band 7 (275-373 GHz) on 2012 August 11, 15, and 26." (2 OBSERVATIONS)
- frequencies and spectral setup: 234 MHz mode, 61 kHz channels, averaged 8 channels to 488 kHz (0.64 km/s at 230 GHz)  
  > "Since we averaged 8 channels for all the data in order to reduce the noise, the channel width shown in this paper is 488 kHz, corresponding to the velocity width of 0.64 km s$^{-1}$ at 230 GHz." (2 OBSERVATIONS)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: Band 7 extended configuration, 23 antennas  
  > "The Band 7 observations were carried out in the extended configuration with 23 antennas" (2 OBSERVATIONS)
- baselines: 20.1 m to 384.1 m (Band 7)  
  > "providing baseline coverage from 20.1 m to 384.1 m" (2 OBSERVATIONS)
- angular resolution: DNC 0.85x0.64; HN13C 0.79x0.60; N2H+ 0.73x0.49 arcsec  
  > "0.85$\times$0.64" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2012 August 11, 15, and 26  
  > "on 2012 August 11, 15, and 26" (2 OBSERVATIONS)
- pi or archival as stated: _not stated_
- Line: DNC J=3-2 (228.91048 GHz)
- Line: HN13C J=3-2 (261.26351 GHz)
- Line: N2H+ J=3-2 (279.51173 GHz)
- Line: N2D+ J=3-2 (231.32 GHz)
- Other facility **NRO 45 m**: Single-dish DNC and HN13C J=1-0 data used for comparison  
  > "by using the Nobeyama Radio Observatory (NRO) 45 m telescope (beam size$\sim$20$^{\prime\prime}$)" (Introduction)
- External data: Single-dish DNC/HNC ratio 0.003±0.001 and spectra  
  > "(0.003$\pm$0.001: Sakai et al. 2012)" (4.2 DNC/HNC Ratio) [from Sakai et al. 2012 (cite: sak12)]
- External data: CS J=5-4 and CH3OH maps  
  > "we plot the CS $J$=5–4 (Paper I) and DNC contours" (4 RESULTS) [from Sakai et al. 2013 (Paper I)]
- External data: 12C/13C ratio of 62 used in earlier work  
  > "used the $^{12}$C/$^{13}$C ratio of 62, which is estimated from the CO and H$_2$CO data by Wilson & Rood (1994)" (4.2 DNC/HNC Ratio) [from Wilson & Rood 1994]
- Simulation/model as data: Gas-grain chemical model (three-phase, constant and temperature-rise cases) based on Furuya et al. network  
  > "We adopt a three-phase model, which consists of gas, chemically active ice mantle, and inert ice mantle (Hasegawa & Herbst 1993)" (4.4 Comparison with Chemical Model Calculations)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Neptune and J1751+096 (bandpass J1924-292)  
  > "The flux calibration was carried out by observing Neptune and J1751+096." (2 OBSERVATIONS)
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
- primary beam correction: None applied for averaged spectra  
  > "where no primary beam corrections are applied" (3.3 Spectra)
- array combination: _not stated_
- smoothing: 8-channel averaging to 488 kHz  
  > "Since we averaged 8 channels for all the data in order to reduce the noise" (2 OBSERVATIONS)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Band 6 observation parameters  
  > "The parameters for the Band 6 observations are described in Paper I." (2 OBSERVATIONS) [from Sakai et al. (2013; Paper I)]
- Chemical reaction network  
  > "We adopt the chemical reaction network of Furuya et al. (2015, in prep.)" (4.4 Comparison with Chemical Model Calculations) [from Furuya et al. 2015, in prep.]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration/imaging parameters (task, weighting, robust, cell, size)
- Continuum subtraction and line-free channels
- Integration windows for moment maps and spectra
- Excitation/column density formulae and line parameters used
- Chemical model initial abundances and full parameters
- Band 6 details only in Paper I

## Analysis recipe

1. **Reduce data and make line maps**: Data reduced with CASA; channel-averaged; integrated intensity and channel maps made  
  > "The data were reduced by using the CASA software package." (2 OBSERVATIONS)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive DNC and HNC column densities and ratio**: Optically thin LTE column densities from spectra at DNC peak, HN13C peak, and 15x15 arcsec averaged region; HNC from HN13C  
  > "The column densities were derived by assuming optically thin emission under local thermodynamic equilibrium conditions." (4.2 DNC/HNC Ratio)
   - parameter: Tex 20-80 K at DNC peak, 20-130 K at HN13C peak  
  > "We calculate the column densities in the range previously defined: 20-80 K at the DNC peak and 20-130 K at the HN$^{13}$C peak position." (4.2 DNC/HNC Ratio)
   - assumption: Same Tex for DNC and HN13C; HN12C/HN13C = 60-80  
  > "Hence, we assume the HN$^{12}$C/HN$^{13}$C ratio to be 60-80." (4.2 DNC/HNC Ratio)
   - fitting: _not stated_
   - validation: Compared with single-dish ratio  
  > "This is much higher than that obtained from the single-dish observations" (4.2 DNC/HNC Ratio)
3. **Compare with chemical models**: Gas-grain model with constant temperature (10, 30, 100 K), density 1e4 or 1e6 cm-3, and temperature-rise cases; o/p H2 0.01 and 0.001  
  > "We thus calculate models with the initial o/p ratio of 0.01 and 0.001." (4.4 Comparison with Chemical Model Calculations)
   - parameter: Cosmic-ray ionization rate 2.6e-17 s-1; Av = 10 mag  
  > "The cosmic ray ionization rate is set to be 2.6$\times$10$^{-17}$ s$^{-1}$ (van der Tak & van Dishoeck 2000)." (4.4 Comparison with Chemical Model Calculations)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Data reduction  
  > "The data were reduced by using the CASA software package." (2 OBSERVATIONS)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| DNC/HNC ratio, averaged 15x15 arcsec | >0.06 | not stated | dimensionless | 2 | $>$0.06$^{b}$ |
| DNC/HNC ratio at DNC peak | 0.03-0.08 | not stated | dimensionless | 2 | 0.03-0.08$^{b}$ |
| DNC/HNC ratio at HN13C peak | 0.001-0.004 | not stated | dimensionless | 2 | 0.001–0.004$^{c}$ |
| Filling factor of DNC emitting region in 15x15 arcsec | ~0.1 | not stated | dimensionless | 2 | The filling factor of the DNC emitting region within the 15$^{\prime\prime}$$\times$15$^{\prime\prime}$ area is estimated to be about 0.1. |

## Qualitative findings

- N2H+ anti-correlated with CS, indicating outflow interacting with cold gas  
  > "This result indicates that a young outflow is interacting with cold ambient gas." (abstract)

## Claim tuples

- H: Why is the single-dish DNC/HNC ratio low? | E: ALMA DNC and HN13C J=3-2 versus NRO J=1-0 ratios plus chemical models | R: ALMA ratio >0.06 versus ~0.003 | F: Single-dish traces lower density envelopes with low filling factor of dense regions | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: HN13C resolved out by interferometer rejected as main cause  
  > "we do not think that the resolved-out problem is the main reason for the weak HN$^{13}$C $J$=3–2 emission" (4.3 Origin of the DNC/HNC Ratio)
- How they decided it was enough: _not stated_
- Limitation (authors): Higher resolution observations needed for the hot core  
  > "higher angular resolution observations would be necessary" (4.4 Comparison with Chemical Model Calculations)
- Caveat (inferred, ours): Optically thin LTE and common Tex assumptions are uncertain
- Caveat (inferred, ours): Model comparison is qualitative
- Caveat (inferred, ours): Distance ambiguity affects interpretation

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: CASA version and imaging parameters
- Missing: Integration ranges
- Missing: Chemical model code (in prep.)
- Data volume (inferred): ~20-50 GB
- Score (inferred): 3/5, Data are public and numeric results simple, but processing details are sparse.
- Rediscovery candidate: no, Imaging and spectral extraction details are not given.

## Links

- Companion: Sakai et al. 2013 (cite: sak13) (Paper I, Band 6 data)
- Companion: Sakai et al. 2012 (cite: sak12) (Single-dish DNC/HNC survey)

## Checks

```json
{
 "quotes": 45,
 "quotes_ok": 45,
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
  "facts": 66,
  "stated": 31,
  "rate": 0.47
 },
 "evidence_ok": true
}
```
