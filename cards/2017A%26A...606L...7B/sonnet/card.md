# Deuterated methanol on a solar system scale around the HH212 protostar

`2017A&A...606L...7B` | Astronomy and Astrophysics 2017 | first author: Bianchi, E. | arXiv: 1709.04726 | DOI: 10.1051/0004-6361/201731404

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: What is the methanol deuteration (CH2DOH/CH3OH) in the planet-forming region (~100 au) of the Class 0 protostar HH212-mm, and where does the emission originate?  
  > "we wish to measure methanol deuteration in the planet formation region around a Class 0 protostar and to understand its origin." (abstract)
- Target **HH212-mm**: coordinates RA(J2000) = 05h43m51.41s, Dec(J2000) = -01d02m53.17s  
  > "The HH212 star-forming region in Orion ($d$ = 450 pc) is an ideal laboratory to study the jet-disk system." (Introduction); "located at $\alpha({\rm J2000})$ = 05$^h$ 43$^m$ 51$s$41, $\delta({\rm J2000})$ = –01$\ensuremath{^\circ}$ 02$\ensuremath{'}$ 53$\ensuremath{''}$17 (Lee et al. 2014)" (Observations); z/distance d = 450 pc  
  > "The HH212 star-forming region in Orion ($d$ = 450 pc) is an ideal laboratory to study the jet-disk system." (Introduction); "located at $\alpha({\rm J2000})$ = 05$^h$ 43$^m$ 51$s$41, $\delta({\rm J2000})$ = –01$\ensuremath{^\circ}$ 02$\ensuremath{'}$ 53$\ensuremath{''}$17 (Lee et al. 2014)" (Observations); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00997.S, 2016.1.01475.S
- bands: Band 7 (Cycle 1 and Cycle 4)  
  > "HH212 was observed in Band 7 with ALMA using 34 12-m antennas between 15 June and 19 July 2014 during the Cycle 1 phase." (Observations)
- frequencies and spectral setup: Cycle 1: 337.1–338.9 and 348.4–350.7 GHz, 488 kHz channels smoothed to 1.0 km/s; Cycle 4: 334.1–336.0 GHz, 977 kHz channels (0.87 km/s)  
  > "In Cycle 1 the spectral windows between 337.1–338.9 GHz and 348.4–350.7 GHz were observed using spectral channels of 488 kHz (0.42–0.43 km s$^{-1}$), subsequently smoothed to 1.0 km s$^{-1}$." (Observations); "For Cycle 4 spectral units of 977 kHz (0.87 km s$^{-1}$) were used to observe the spectral windows between 334.1–336.0 GHz." (Observations)
- continuum bandwidth: _not stated_
- arrays: 34 12-m antennas (Cycle 1), 44 12-m antennas (Cycle 4)  
  > "Further observations of HH212 were performed in Band 7 with ALMA using 44 12-m antennas between 6 October and 26 November 2016 during the Cycle 4 phase." (Observations)
- configurations: _not stated_
- baselines: max baselines 650 m (Cycle 1), 3 km (Cycle 4)  
  > "The maximum baselines for Cycle 1 and 4 were 650 m and 3 km, respectively." (Observations)
- angular resolution: Cycle 1: 0.41"x0.33" to 0.52"x0.34"; Cycle 4: 0.15"x0.12"  
  > "The continuum-subtracted images have a typical clean-beam FWHM of $0.15\ensuremath{''}\times0.12\ensuremath{''}$ (PA = -88$\ensuremath{^\circ}$)" (Observations)
- max recoverable scale: _not stated_
- sensitivity: rms 5–6 mJy/beam in 1.0 km/s channels (Cycle 1); 1 mJy/beam in 0.87 km/s channels (Cycle 4)  
  > "and an rms noise level of 1 mJy beam$^{-1}$ in 0.87 km s$^{-1}$ channels" (Observations)
- time on source: _not stated_
- observing dates: 15 June–19 July 2014 (Cycle 1); 6 October–26 November 2016 (Cycle 4)  
  > "between 15 June and 19 July 2014 during the Cycle 1 phase" (Observations)
- pi or archival as stated: PI: C. Codella  
  > "(PI: C. Codella)" (Acknowledgements)
- Line: 13CH3OH 12(1,11)-12(0,12) A (Cycle 4); 5 Cycle 1 lines, Eup 17-303 K (335.56021 GHz)
- Line: CH2DOH 16(2,15)-16(1,15) o1 (Cycle 4); 12 Cycle 1 lines, Eup 38-438 K (334.68395 GHz)
- External data: 12C/13C = 70 at galactocentric distance ~8.3 kpc  
  > "Assuming a $^{12}$C/$^{13}$C ratio of 70 (Milam et al. 2005) at the galactocentric distance of HH212 ($\sim$ 8.3 kpc)" (2.2 Methanol deuteration) [from Milam et al. 2005 (cite: milam)]
- External data: Spectroscopic parameters from JPL and CDMS  
  > "Lines were identified using spectroscopic parameters extracted from the Jet Propulsor Laboratory" (Observations) [from Pickett et al. 1998; Müller et al. 2001, 2005]
- External data: Systemic velocity +1.7 km/s and continuum peak position  
  > "systemic velocity of +1.7 km s$^{-1}$ (Lee et al. 2014)" (2.1 Line spectra and maps) [from Lee et al. 2014]
- External data: Perseus D/H 0.4-0.6 from IRAM-30m  
  > "which indicate D/H $\simeq$ 40-60$\%$ (Parise et al. 2006)" (2.2 Methanol deuteration) [from Parise et al. 2006]

## Processing

### Calibration

- pipeline or manual: standard procedures  
  > "Calibration was carried out following standard procedures, using quasars J0607-0834, J0541–0541, J0423–013, and Ganymede." (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Cycle 1: Ganymede (and quasars J0607-0834, J0541-0541, J0423-013); Cycle 4 quasars J0510+1800, J0552+0313, J0541-0211, J0552-3627  
  > "using quasars J0510+1800, J0552+0313, J0541–0211 and J0552–3627" (Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA for spectral line imaging  
  > "Spectral line imaging was achieved with the CASA package" (Observations)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: images are continuum-subtracted  
  > "The continuum-subtracted images have clean-beam FWHMs from $0.41\ensuremath{''}\times0.33\ensuremath{''}$" (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Cycle 1 smoothed to 1.0 km/s  
  > "subsequently smoothed to 1.0 km s$^{-1}$" (Observations)
- final beam: Cycle 1 0.41x0.33 to 0.52x0.34 arcsec; Cycle 4 0.15x0.12 arcsec  
  > "The continuum-subtracted images have a typical clean-beam FWHM of $0.15\ensuremath{''}\times0.12\ensuremath{''}$ (PA = -88$\ensuremath{^\circ}$)" (Observations)
- final rms: 5–6 mJy/beam (Cycle 1), 1 mJy/beam (Cycle 4)  
  > "an rms noise level of 5–6 mJy beam$^{-1}$ in 1.0 km s$^{-1}$ channels" (Observations)

### Inherited from earlier work

- Disk/system parameters (continuum peak position, systemic velocity)  
  > "Positions are given with respect to the MM1 protostar continuum peak" (Observations) [from Lee et al. 2014 (cite: lee14)]
- LVG analysis method  
  > "an LVG analysis (see Ceccarelli et al. 2003 for further details)" (2.2 Methanol deuteration) [from Ceccarelli et al. 2003]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration pipeline version
- weighting/robust, deconvolver, cell and image size, masks
- line-free channels for continuum subtraction
- how spectra were extracted (aperture/region)
- partition function used in the rotation diagram
- handling of A/E symmetry and beam-dilution details
- Population Diagram input parameters
- flux scale uncertainty

## Analysis recipe

1. **Detect lines and fit profiles**: Identify lines with JPL/CDMS; Gaussian fits with GILDAS  
  > "The profiles, fit using the GILDAS package, are Gaussian with typical Full Width at Half Maximum (FWHM) $\sim$ 5 km s$^{-1}$." (2.1 Line spectra and maps)
   - software: GILDAS, CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure source size**: Size from 13CH3OH Cycle 4 map integrated over emission range, used to correct Cycle 1 values  
  > "A source size of 0$\ensuremath{''}$19 $\pm$ 0$\ensuremath{''}$02 has been derived from the $^{13}$CH$_{3}$OH Cycle 4 map integrated over the whole emission range" (2.2 Methanol deuteration)
   - fitting: _not stated_
   - validation: Consistent with ~0.2 arcsec from CH3OH (Leurini et al. 2016)  
  > "This value is in good agreement with $\sim$ 0$\ensuremath{''}$2, as derived from CH$_{3}$OH (Leurini et al. 2016)." (2.2 Methanol deuteration)
3. **Rotation diagram for 13CH3OH and CH2DOH**: Rotation diagram of Cycle 1 13CH3OH lines; CH2DOH column density with same Trot and size, excluding two lines with Eup>300 K  
  > "In the lower panel of Fig. [4](#RD) we derive the column density of CH$_{2}$DOH, assuming the same rotational temperature and size derived for $^{13}$CH$_{3}$OH." (2.2 Methanol deuteration)
   - software: GILDAS
   - assumption: LTE and optically thin lines  
  > "assuming LTE conditions and optically thin lines" (2.2 Methanol deuteration)
   - fitting: Linear rotation diagram fit; only Cycle 1 data used  
  > "Conservatively, we used only Cycle 1 data to perform the fit" (2.2 Methanol deuteration)
   - validation: Population diagram (Goldsmith & Langer 1999) confirms CH2DOH optically thin; Cycle 4 lines consistent; LVG check  
  > "We also verified that the CH$_{2}$DOH transitions are indeed optically thin using a Population Diagram analysis" (2.2 Methanol deuteration)
4. **Derive D/H**: CH2DOH/CH3OH with CH3OH = 12C/13C x 13CH3OH  
  > "the D/H is consequently (2.4 $\pm$ 0.4) $\times$ 10$^{-2}$." (2.2 Methanol deuteration)
   - assumption: 12C/13C = 70  
  > "Assuming a $^{12}$C/$^{13}$C ratio of 70 (Milam et al. 2005)" (2.2 Methanol deuteration)
   - fitting: _not stated_
   - validation: Compared with Lee et al. 2017b upper limit and Parise et al. 2006  
  > "This value is in agreement with the upper limit of 0.27 derived by Lee et al. (2017b)" (2.2 Methanol deuteration)
5. **Characterise emitting region**: Image-plane fits of Cycle 4 maps at systemic and ±2 km/s; channel maps and velocity gradient  
  > "A fit in the image plane gives for $^{13}$CH$_{3}$OH a beam deconvolved FWHM size of 0$\ensuremath{''}$18(0$\ensuremath{''}$02)$\times$0$\ensuremath{''}$12(0$\ensuremath{''}$02) at PA = 33$\ensuremath{^\circ}$." (2.3 The emitting region of deuterated methanol)
   - software: CASA, GILDAS
   - assumption: d = 450 pc  
  > "The HH212 star-forming region in Orion ($d$ = 450 pc)" (Introduction)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : spectral line imaging  
  > "Spectral line imaging was achieved with the CASA package" (Observations)
- **GILDAS** : data analysis and line fitting  
  > "while data analysis was performed using the GILDAS[^1] package" (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Rotational temperature | 171 | 52 | K | 3 | $T_{\rm rot}$ = (171 $\pm$ 52) K |
| 13CH3OH column density | 6.5e16 | 2.1e16 | cm^-2 | 3 | $N_{\rm tot}$ = (6.5 $\pm$ 2.1) $\times$ 10$^{16}$ cm$^{-2}$ |
| CH2DOH column density | 1.1e17 | 0.2e17 | cm^-2 | 3 | $N_{\rm tot}$ = (1.1 $\pm$ 0.2) $\times$ 10$^{17}$ cm$^{-2}$ |
| Methanol D/H | 2.4e-2 | 0.4e-2 | dimensionless | 4 | the D/H is consequently (2.4 $\pm$ 0.4) $\times$ 10$^{-2}$ |
| Source size from 13CH3OH Cycle 4 | 0.19 | 0.02 | arcsec | 2 | A source size of 0$\ensuremath{''}$19 $\pm$ 0$\ensuremath{''}$02 |
| CH2DOH deconvolved size at Vsys | 0.20x0.10 (PA 19 deg) | 0.02 | arcsec | 5 | For CH$_{2}$DOH we derived 0$\ensuremath{''}$20(0$\ensuremath{''}$02)$\times$0$\ensuremath{''}$10(0$\ensuremath{''}$02) and PA = 19$\ensuremath{^\circ}$. |

## Qualitative findings

- Emission traces a rotating structure with velocity gradient parallel to the equatorial plane and elongated along the jet axis; origin tied to the accretion disk (disk wind, atmosphere or accretion shock)  
  > "The emission is tracing a rotating structure extending up to 45 au from the jet axis and elongated by 90 au along the jet axis." (abstract)

## Claim tuples

- H: Methanol deuteration at ~100 au in a Class 0 protostar is lower than single-dish values in Perseus | E: Rotation diagrams of 13CH3OH and CH2DOH from ALMA Cycle 1 and 4 data | R: D/H = (2.4±0.4)e-2, an order of magnitude below Perseus values | F: Lower deuteration consistent with higher dust temperature in Orion B | **supported**
- H: Origin of the emission | E: Cycle 4 channel maps and size fits | R: Rotating, elongated structure within ~45 au | F: Related to the accretion disk, but wind, atmosphere and accretion shock cannot be distinguished | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: 13CH3OH used to avoid opacity of main isotopologue; same dataset for same uv coverage  
  > "We used $^{13}$CH$_{3}$OH and CH$_{2}$DOH lines extracted from the same ALMA dataset in order to have the same $u-v$ coverage" (2.2 Methanol deuteration)
- How they decided it was enough: _not stated_
- Limitation (authors): Higher spatial resolution is needed to distinguish between scenarios; synthetic predictions needed for the disk wind  
  > "Higher spatial resolution maps will be necessary to distinguish between these possibilities." (Conclusions)
- Caveat (inferred, ours): D/H depends on assumed 12C/13C = 70 and the same Trot and size for both species
- Caveat (inferred, ours): Cycle 1 unresolved emission relies on a size correction from Cycle 4
- Caveat (inferred, ours): Only 5 13CH3OH lines used in the fit, large uncertainties
- Caveat (inferred, ours): Temperature explanation compared with Perseus is qualitative
- Caveat (inferred, ours): CH2DOH Cycle 4 line blended with SO2

## Reproducibility

- Data public (paper): ALMA data cited by project code (PI Codella)  
  > "This paper makes use of the ADS/JAO.ALMA#2012.1.00997.S and ADS/JAO.ALMA#2016.1.01475.S data (PI: C. Codella)." (Acknowledgements)
- Products in archive: _not stated_
- Missing: imaging parameters
- Missing: CASA version
- Missing: line extraction regions
- Missing: partition functions
- Data volume (inferred): ~50-150 GB raw for two Band 7 projects
- Score (inferred): 3/5, Data identified and results numeric, but calibration and imaging details are sparse.
- Rediscovery candidate: no, Imaging and spectral extraction details are not given, so a recipe is incomplete.

## Links

- Method: Goldsmith & Langer 1999 (cite: goldsmith) (Population diagram analysis)
- Method: Ceccarelli et al. 2003 (LVG analysis)
- Companion: Leurini et al. 2016 (cite: Leurini2016) (Cycle 0 CH3OH observations of HH212)
- Companion: Lee et al. 2017b (cite: Lee2017b) (CH2DOH D/H upper limit)

## Checks

```json
{
 "quotes": 58,
 "quotes_ok": 58,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 42,
  "rate": 0.592
 },
 "evidence_ok": true
}
```
