# Water and acetaldehyde in HH212: The first hot corino in Orion

`2016A&A...586L...3C` | Astronomy and Astrophysics 2016 | first author: Codella, C. | arXiv: 1601.00539 | DOI: 10.1051/0004-6361/201527424

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation, astrochemistry
- Question: Do hot corino, disk and ejected gas coexist in HH212-MM1, probed by high-excitation CH3CHO and HDO lines?  
  > "we aim to investigate whether and how hot corinos, circumstellar disks, and ejected gas are related in young solar-mass protostars." (abstract)
- Target **HH212-MM1**: coordinates RA(J2000) 05h43m51.41s, Dec -01d02m53.17s  
  > "HH212 is located in Orion (at 450 pc)" (Introduction: The HH212 laboratory); "Positions are given with respect to the MM1 protostar continuum peak located at $\alpha({\rm J2000})$ = 05$^h$ 43$^m$ 51$s$41" (Observations); z/distance 450 pc  
  > "HH212 is located in Orion (at 450 pc)" (Introduction: The HH212 laboratory); "Positions are given with respect to the MM1 protostar continuum peak located at $\alpha({\rm J2000})$ = 05$^h$ 43$^m$ 51$s$41" (Observations); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.000647.S
- bands: 850 um (Band 7), Cycle 0 Early Science  
  > "HH212 was observed at 850 $\mu$m with ALMA using 24 12 m antennas on 2012 December 1 (Early Science Cycle 0 phase; Codella et al. 2014)." (Observations)
- frequencies and spectral setup: 333.7-337.4 GHz and 345.6-349.3 GHz, 488 kHz units (0.42-0.44 km/s)  
  > "The spectral windows 333.7–337.4 GHz and 345.6–349.3 GHz were observed using spectral units of 488 kHz (0.42–0.44 km s$^{-1}$)." (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 20 m to 360 m  
  > "The baselines were between 20 m and 360 m with a maximum unfiltered scale of 3$\ensuremath{''}$." (Observations)
- angular resolution: 0.65"x0.47" (PA=35 deg)  
  > "The continuum-subtracted images have a typical clean-beam FWHM of $0.65\ensuremath{''}\times0.47\ensuremath{''}$ (PA = 35$\ensuremath{^\circ}$)" (Observations)
- max recoverable scale: 3 arcsec  
  > "The baselines were between 20 m and 360 m with a maximum unfiltered scale of 3$\ensuremath{''}$." (Observations)
- sensitivity: rms 3-4 mJy/beam in 0.44 km/s channels  
  > "an rms noise level of 3–4 mJy beam$^{-1}$ in 0.44 km s$^{-1}$ channels" (Observations)
- time on source: _not stated_
- observing dates: 2012 December 1  
  > "using 24 12 m antennas on 2012 December 1" (Observations)
- pi or archival as stated: PI C. Codella; dataset of Codella et al. (2014)  
  > "This paper makes use of the ADS/JAO.ALMA#2011.0.000647.S data (PI: C. Codella)." (Acknowledgements)
- Line: CH3CHO twelve lines, Eu 150-200 K (e.g. 18_0,18-17_0,17 A) (335358.7 MHz (example))
- Line: HDO 3_3,1-4_2,2 (335395.5 MHz)
- External data: N(H2) ~1e24-1e25 cm-2 in IRAS2A and IRAS4A hot corinos, used to derive CH3CHO abundance  
  > "Taquet et al. (2015) measured N(H$_2$) $\simeq$ 10$^{24}$–10$^{25}$ cm$^{-2}$ towards the NGC1333-IRAS2A and IRAS4A hot corinos" (CH3CHO emission) [from Taquet et al. 2015 (ref: taquet15)]
- External data: HDO-H2 collisional coefficients  
  > "the collisional coefficients for the system HDO-H$_2$ computed by Faure et al. (2012)" (HDO emission) [from Faure et al. 2012 (ref: faure)]
- External data: Line spectroscopic parameters from JPL database  
  > "The lines were identified using the Jet Propulsion Laboratory (JPL) molecular database (Pickett et al. 1998)." (Results and discussion) [from Pickett et al. 1998 (ref: pickett)]

## Processing

### Calibration

- pipeline or manual: standard procedures  
  > "Calibration was carried out following standard procedures, using quasars J0538–440, J0607–085, Callisto, and Ganymede." (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
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
- continuum subtraction: images are continuum-subtracted (method not given)  
  > "The continuum-subtracted images have a typical clean-beam FWHM" (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Dataset, calibration and V_sys choice from earlier ALMA paper  
  > "(Early Science Cycle 0 phase; Codella et al. 2014)" (Observations) [from Codella et al. 2014 (ref: codella14)]
- V_sys = +1.7 km/s and continuum peak position  
  > "we adopt here +1.7 km s$^{-1}$ (Lee et al. 2014)" (footnote 2) [from Lee et al. 2014 (ref: lee14)]

### Not stated but needed to reproduce (our reading)

- CASA version and clean parameters (weighting, robust, masks, cell/image size)
- line-free channels for continuum subtraction
- flux calibrator adopted fluxes and flux scale uncertainty
- spectrum extraction aperture
- line blending corrections
- LVG code details and grid

## Analysis recipe

1. **Identify lines and measure intensities**: Identify lines with JPL database; integrate unblended lines at MM1 position  
  > "The lines were identified using the Jet Propulsion Laboratory (JPL) molecular database (Pickett et al. 1998)." (Results and discussion)
   - software: GILDAS, CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **CH3CHO LTE rotational diagram**: Optically thin LTE analysis with lines less than 30% blended  
  > "An LTE (Local Thermodynamic Equilibrium) optically thin analysis of CH$_3$CHO (using only lines with less than 30% contamination from blended lines" (CH3CHO emission)
   - assumption: Source size 0.3" (half a beam)  
  > "we assume a source size equal to half a beam, namely 0$\ensuremath{''}$3" (CH3CHO emission)
   - fitting: rotational diagram  
  > "Table 1 lists the emission lines observed towards HH212–MM1 and used for the standard analysis of the rotational diagram (Fig. A.1), which allows us to derive $T_{\rm rot}$ = 87$\pm$47 K" (The CH$_3$CHO rotational diagram)
   - validation: opacity <0.4 checked  
  > "With these values the opacity is less than 0.4." (CH3CHO emission)
3. **HDO non-LTE LVG modelling**: LVG grid in T vs N(HDO) for densities 1e7-1e10 cm-3, optically thin and tau=1 cases, source sizes 0.3" and 0.06"  
  > "we compare the observed emission with that predicted by a non-LTE LVG (Large Velocity Gradient) model using the code by Ceccarelli et al. (2003), a plane parallel geometry" (HDO emission)
   - software: LVG code of Ceccarelli et al. 2003
   - parameter: HDO abundance <10% of D/H, N(HDO)/N(H2) <= 3.2e-6  
  > "namely $N$(HDO)/$N$(H$_2$) $\leq 3.2 \times 10^{-6}$" (HDO emission)
   - assumption: Initial H2O abundance 3e-5; Boltzmann ortho/para H2  
  > "assuming an initial H$_2$O abundance of 3 $\times$ 10$^{-5}$" (HDO emission)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : spectral line imaging  
  > "Spectral line imaging was achieved with the CASA package" (Observations)
- **GILDAS** : data analysis  
  > "data analysis was performed using the GILDAS[^1] package" (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CH3CHO rotational temperature | 87 | ±47 | K | 2 | indicates temperature of 87$\pm$47 K and a column density of 2$\pm$1 $\times$ 10$^{15}$ cm$^{-2}$ |
| CH3CHO column density | 2e15 | ±1e15 | cm-2 | 2 | column density of 2$\pm$1 $\times$ 10$^{15}$ cm$^{-2}$ |
| CH3CHO abundance | 0.2-2e-9 | not stated | dimensionless | 2 | $X_{\rm CH_3CHO}$ $\sim$ 0.2–2 $\times$ 10$^{-9}$ |
| HDO column density (optically thick, T~100 K, 0.06") | ~7e17 | not stated | cm-2 | 3 | for a temperature around 100 K, $N$(HDO)$\sim 7 \times 10^{17}$ cm$^{-2}$ |
| HDO emitting size if thick | 18-37 | not stated | AU | 3 | the emitting size must be very small (18–37 AU) |

## Qualitative findings

- HDO profile asymmetric at low velocity, indicating slow outflowing gas, possibly a disk wind  
  > "The asymmetric HDO profile at low velocities indicates that at least some of the deuterated water is associated with slow outflowing gas" (Conclusions)

## Claim tuples

- H: HH212-MM1 hosts a hot corino | E: Detect and model high-excitation CH3CHO and HDO lines | R: T ~ 87 K, N(CH3CHO)=2e15 cm-2, density >=1e7 cm-3 | F: First hot corino detected in Orion | **supported**
- H: Low-velocity HDO traces outflowing gas | E: Compare HDO profile with CH3CHO and with disk/envelope/outflow scenarios | R: Redshifted HDO brighter than blueshifted | F: HDO traces slow outflow, possibly a disk wind | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Disk and infalling envelope origins of HDO rejected based on asymmetry and resolved extent  
  > "We can also rule out an origin from the rotating infalling envelope" (Optically thin case)
- How they decided it was enough: _not stated_
- Limitation (authors): Continuum optically thick so H2 column cannot be derived; sizes unresolved  
  > "we cannot use the continuum emission to estimate the H$_2$ column density" (CH3CHO emission)
- Caveat (inferred, ours): Unresolved emission so source size assumed
- Caveat (inferred, ours): CH3CHO abundance relies on N(H2) borrowed from other sources
- Caveat (inferred, ours): Optically thin vs thick HDO not distinguished

## Reproducibility

- Data public (paper): ALMA Cycle 0 project cited in acknowledgements  
  > "This paper makes use of the ADS/JAO.ALMA#2011.0.000647.S data (PI: C. Codella)." (Acknowledgements)
- Products in archive: _not stated_
- Missing: CASA version and imaging parameters
- Missing: spectrum extraction details
- Missing: LVG code inputs
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Public data and simple analysis but imaging and LVG details missing.
- Rediscovery candidate: no, Imaging and LVG modelling details are insufficient for exact redo.

## Links

- Method: Ceccarelli et al. 2003 (ref: cecilia03) (LVG code)
- Companion: Codella et al. 2014 (ref: codella14) (Same ALMA dataset)
- Companion: Podio et al. 2015 (ref: podio15) (SiO and SO from same dataset)

## Checks

```json
{
 "quotes": 46,
 "quotes_ok": 46,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.0.000647.S"
 ],
 "obscore_codes_not_in_card": [
  "2011.0.00647.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 65,
  "stated": 33,
  "rate": 0.508
 },
 "evidence_ok": true
}
```
