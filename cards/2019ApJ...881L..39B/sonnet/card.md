# Sub-arcsecond (Sub)millimeter Imaging of the Massive Protocluster G358.93-0.03: Discovery of 14 New Methanol Maser Lines Associated with a Hot Core

`2019ApJ...881L..39B` | The Astrophysical Journal Letters 2019 | first author: Brogan, C. L. | arXiv: 1907.02470 | DOI: 10.3847/2041-8213/ab2f8a

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry, milky_way_ism
- Question: What are the (sub)millimeter continuum and line (maser and thermal) properties of the protocluster G358.93-0.03 after its 6.7 GHz methanol maser flare, and is there evidence of a protostellar accretion outburst?  
  > "Since the 6.7 GHz CH$_3$OH maser flare in G358.93$-$0.03 may be indicative of a massive protostellar outburst event, the M2O group has pursued multi-wavelength follow-up with telescopes worldwide" (Introduction)
- Target **G358.93-0.03**: coordinates MM1: 17:43:10.1014 -29:51:45.693 (J2000)  
  > "Lacking a maser parallax distance, we use the MM1 $v_{\rm LSR}$ to derive a near kinematic distance of 6.75 kpc (cite: Reid14)." (3.1 (Sub)millimeter Continuum and Thermal Line Emission); z/distance 6.75 kpc (near kinematic distance)  
  > "Lacking a maser parallax distance, we use the MM1 $v_{\rm LSR}$ to derive a near kinematic distance of 6.75 kpc (cite: Reid14)." (3.1 (Sub)millimeter Continuum and Thermal Line Emission); distance from Reid14 kinematic distance model, from MM1 v_LSR  
  > "Lacking a maser parallax distance, we use the MM1 $v_{\rm LSR}$ to derive a near kinematic distance of 6.75 kpc (cite: Reid14)." (3.1 (Sub)millimeter Continuum and Thermal Line Emission)

## Data provenance

- ALMA projects: 2018.A.00031.T
- bands: ALMA Bands 5, 6, 7; SMA 240/345 and 345/400 GHz receiver settings  
  > "Band 5 | 2019-04-16 | 55 | 0.9 | 9–494" (Table 1)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: SMA with 8 antennas; ALMA with 43 antennas  
  > "The SMA employed 8 antennas while ALMA employed 43" (Observations)
- configurations: _not stated_
- baselines: ALMA uv range 9–725 kilo-lambda; SMA 18–344 kilo-lambda  
  > "Band 6 | 2019-04-16 | 55 | 0.9 | 11–590" (Table 1)
- angular resolution: ~0.5 arcsec; common beam 0.46x0.42 arcsec for ALMA continuum  
  > "We present (sub)millimeter imaging at $0.5\ensuremath{''}$ resolution" (abstract)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: ALMA: 55, 55, 49 min (Bands 5, 6, 7); SMA: 187 and 134 min  
  > "Band 7 | 2019-04-12 | 49" (Table 1)
- observing dates: SMA 2019-03-14 and 2019-03-22; ALMA 2019-04-12 (Band 7) and 2019-04-16 (Bands 5, 6)  
  > "Band 7 | 2019-04-12 | 49 | 0.6 | 16–725" (Table 1)
- pi or archival as stated: _not stated_
- Line: CH3OH vt=2 11_3-12_4 A- (330.172526 GHz)
- Line: CH3CN J=11-10, K=0-6 (not stated)
- Other facility **SMA**: Epoch 1 (2019 March) continuum and maser line data  
  > "we report first results from 0.87 to 1.5 mm Submillimeter Array (SMA) and Atacama Large Millimeter/submillimeter Array (ALMA) observations" (Introduction)
- Other facility **ATLASGAL, BGPS, Herschel HiGAL, MIPSGAL**: Single-dish photometry for SED/luminosity  
  > "photometry extracted from 1.1 mm BGPS (cite: Rosolowsky10), 0.87 mm ATLASGAL (cite: Schuller09), and 70-500 $\mu$m *Herschel* HiGAL (cite: Molinari16)" (3.3 G358.93-0.03 Luminosity)
- External data: Methyl transition parameters from JPL Line Catalog  
  > "Transition parameters were extracted from the JPL Line Catalog (cite: Pickett98) compiled from (cite: Xu08)." (Table 3) [from Pickett98; Xu08]
- External data: CH3CN excitation temperature model (Tex=172 K, Tbg=159 K)  
  > "$T_{ex}=172\pm 3$ K and a background temperature $T_{bg}=159\pm 3$ K (cite: McGuire18)" (3.1 (Sub)millimeter Continuum and Thermal Line Emission) [from McGuire18]
- External data: Pre-flare ATLASGAL flux density 1.09-1.4 Jy  
  > "Previous estimates of the ATLASGAL flux density for this source range from 1.09-1.4 Jy (cite: Csengeri14; Contreras13)" (4 Discussion) [from Csengeri14; Contreras13]
- Simulation/model as data: YSO model grid of Robitaille17 for SED fitting  
  > "to the model grid of young stellar objects of (cite: Robitaille17), using the method described in (cite: Towner19)" (3.3 G358.93-0.03 Luminosity)

## Processing

### Calibration

- pipeline or manual: SMA calibrated in MIR; ALMA with the ALMA CASA pipeline  
  > "The SMA data were calibrated in MIR, and the ALMA data were calibrated using the ALMA CASA pipeline." (Observations)
- casa version: CASA 5.4.0-70 (imaging)  
  > "All of the data were imaged in CASA 5.4.0-70" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1924-292 for ALMA; ALMA flux monitoring data used for absolute scale of all data  
  > "ALMA flux monitoring data was used to set the absolute flux scale for all the observations" (Observations)
- flux scale uncertainty: 5% ALMA, 10% SMA  
  > "We estimate that the absolute flux calibration uncertainty is $5\%$ and $10\%$ for the ALMA and SMA data, respectively." (Observations)
- self calibration: Self-calibrated using the strongest maser channel in each band  
  > "self-calibrated using the strongest maser channel in each respective band" (Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: SMA R=+0.5; ALMA R=-0.5, +0.1, +0.1 for Bands 5, 6, 7; extra Band 7 R=+1.0 image  
  > "The ALMA continuum images were made with $R=-0.5$, $+0.1$, and $+0.1$ for Bands 5, 6, and 7" (Observations)
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
- final beam: ALMA convolved to 0.46x0.42 arcsec pa=-30; SMA 0.66x0.46 (210.88 GHz), 1.1x0.7 (346 GHz)  
  > "convolved to a common beam of $0.46\ensuremath{''}\times 0.42\ensuremath{''}$ (pa$=-30\ensuremath{^\circ}$)" (Observations)
- final rms: ALMA continuum 0.14, 0.12, 0.35 mJy/beam (Bands 5, 6, 7)  
  > "0.14 / 2.8" (Table 1)

### Inherited from earlier work

- Luminosity/greybody fitting procedure  
  > "following the procedure of (cite: Towner19)" (3.3 G358.93-0.03 Luminosity) [from Towner19]
- Kinematic distance model  
  > "we use the MM1 $v_{\rm LSR}$ to derive a near kinematic distance of 6.75 kpc (cite: Reid14)" (3.1 (Sub)millimeter Continuum and Thermal Line Emission) [from Reid14]

### Not stated but needed to reproduce (our reading)

- Line-free channels and continuum subtraction method
- Image size, cell size, deconvolver, masking, tclean parameters
- Pipeline version
- SMA reduction details beyond MIR
- Fitting method/software for 2D Gaussian components
- Specific CASA tasks used for spot fitting

## Analysis recipe

1. **Fit continuum sources**: Fit eight 2D Gaussian components to ALMA three-band and SMA 210.88 GHz images  
  > "were fit with eight 2D Gaussian components" (3.1 (Sub)millimeter Continuum and Thermal Line Emission)
   - software: CASA
   - fitting: _not stated_
   - validation: Residual images checked after model subtraction  
  > "After subtracting the model components, two areas of residual emission are consistently present across all the images." (3.1 (Sub)millimeter Continuum and Thermal Line Emission)
2. **Maser spot spatio-kinematics**: Fit 2D Gaussian to each emission channel; S/N cutoff 12 (ALMA), 16 (SMA)  
  > "a two-dimensional Gaussian was fitted to each channel with emission." (3.2 (Sub)millimeter CH3OH Masers)
   - software: CASA
   - parameter: S/N<12 (ALMA), <16 (SMA) omitted for positions better than 20 mas  
  > "Channels with signal-to-noise ($S/N$) $< 12$ and $< 16$ for ALMA and SMA, respectively, are omitted" (3.2 (Sub)millimeter CH3OH Masers)
   - fitting: _not stated_
   - validation: _not stated_
3. **Luminosity and gas mass**: Single-temperature greybody fit to survey photometry plus YSO model grid SED fit  
  > "a single temperature greybody fit yields $T_{dust}=28.5\pm 1.5$ K" (3.3 G358.93-0.03 Luminosity)
   - assumption: beta=1.7, dust-to-gas 100, distance 6.75 kpc  
  > "assuming a grain opacity spectral index $\beta=1.7$ and dust-to-gas ratio of 100" (3.3 G358.93-0.03 Luminosity)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.4.0-70: ALMA pipeline calibration and imaging of all data  
  > "All of the data were imaged in CASA 5.4.0-70" (Observations)
- **MIR** : SMA calibration  
  > "The SMA data were calibrated in MIR" (Observations)
- **APLpy** : Plotting  
  > "APLpy (cite: aplpy2012)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of new CH3OH maser lines | 14 | not stated | dimensionless | 0 | we have discovered 14 new Class II CH$_3$OH maser lines |
| Total 0.89 mm ALMA flux density (R=+1.0) | 1.13 | 0.03 | Jy | 1 | $1.13\pm0.03$ Jy |
| MM1 spectral index | 3.06 | 0.13 | dimensionless | 1 | 3.06 (0.13) |
| Dust temperature | 28.5 | 1.5 | K | 3 | $T_{dust}=28.5\pm 1.5$ K |
| Total gas mass | 167 | 12 | Msun | 3 | total gas mass of $167\pm 12$ M$_{\odot}$ |
| MM1 vLSR | -16.5 | 0.3 | km/s | 0 | $v_{\rm LSR}$=$-16.5\pm0.3$ km s$^{-1}$ |

## Qualitative findings

- Masers trace a curvilinear pattern around MM1 inconsistent with simple disk rotation; no significant continuum change between epochs  
  > "The pattern is not consistent with simple rotation of an inclined circular disk" (4 Discussion)

## Claim tuples

- H: Are there new Class II methanol maser lines in the flare? | E: SMA and ALMA spectral imaging | R: 14 new lines, including one vt=2 | F: First evidence vt=2 levels involved in Class II maser pumping | **supported**
- H: Did the continuum brighten significantly because of an accretion outburst? | E: Compare epochs and prior ATLASGAL flux | R: No significant change in continuum flux | F: No conclusive evidence for dust heating | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Disk rotation interpretation of masers and thermal gas rejected in favor of ring/outflow cavity or spiral filament  
  > "Such a morphology could arise from the walls of an outflow cavity." (4 Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Kinematic distance has considerable uncertainty  
  > "This estimate has considerable uncertainty ($+0.37, -0.68$ kpc reported by the model)" (3.1 (Sub)millimeter Continuum and Thermal Line Emission)
- Caveat (inferred, ours): Pre-flare comparison relies on low-resolution single-dish data with spatial filtering differences
- Caveat (inferred, ours): Kinematic distance near Galactic center is poorly constrained

## Reproducibility

- Data public (paper): ALMA data project 2018.A.00031.T acknowledged; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2018.A.00031.T." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Detailed tclean parameters
- Missing: Line-free channel selection
- Missing: SMA data availability
- Data volume (inferred): ~100-300 GB (three ALMA bands, high spectral resolution)
- Score (inferred): 4/5, Observation setup and key imaging choices given, but many imaging and fitting details missing.
- Rediscovery candidate: no, Data may be proprietary/DDT at time; imaging recipe incomplete.

## Links

- Method: Towner19 (SED/luminosity fitting procedure)
- Companion: Breen19 (Centimeter-wavelength new maser lines)
- Companion: MacLeod19 (6.7 GHz maser light curves)
- Related: M2O (Maser Monitoring Organization)
- Related: ATLASGAL
- Related: BGPS
- Related: Hi-GAL

## Checks

```json
{
 "quotes": 51,
 "quotes_ok": 51,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 39,
  "rate": 0.574
 },
 "evidence_ok": true
}
```
