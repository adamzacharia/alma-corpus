# Submillimeter H<SUB>2</SUB>O Megamasers in NGC 4945 and the Circinus Galaxy

`2016ApJ...827...68P` | The Astrophysical Journal 2016 | first author: Pesce, D. W. | arXiv: 1604.03789 | DOI: 10.3847/0004-637X/827/1/68

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: agn_and_quasars, nearby_galaxies, astrochemistry
- Question: Do the AGN host 321 GHz H2O megamasers, and how do the submillimeter masers and continuum compare with 22 GHz masers and galactic disks?  
  > "Submillimeter maser emission is detected for the first time towards NGC 4945, and we present a new analysis of the submillimeter maser system in Circinus." (abstract)
- Target **NGC 4945**: coordinates 13:05:27.279 -49:28:04.44 (tracking center)  
  > "Adopting a distance to NGC 4945 of 3.7 Mpc (cite: 2013AJ....146...86T)" (Discussion); z/distance 3.7 Mpc  
  > "Adopting a distance to NGC 4945 of 3.7 Mpc (cite: 2013AJ....146...86T)" (Discussion); distance from Tully et al. 2013  
  > "Adopting a distance to NGC 4945 of 3.7 Mpc (cite: 2013AJ....146...86T)" (Discussion)
- Target **Circinus**: coordinates 14:13:09.906 -65:20:20.468 (tracking center)  
  > "At a distance to the galaxy of 4.2 Mpc (measured by (cite: 2013AJ....145..101K) using the Tully-Fisher relation)" (Discussion); z/distance 4.2 Mpc  
  > "At a distance to the galaxy of 4.2 Mpc (measured by (cite: 2013AJ....145..101K) using the Tully-Fisher relation)" (Discussion); distance from Karachentsev et al. 2013 (Tully-Fisher)  
  > "At a distance to the galaxy of 4.2 Mpc (measured by (cite: 2013AJ....145..101K) using the Tully-Fisher relation)" (Discussion)
- Target **NGC 5793**: coordinates 14:59:24.807 -16:41:36.55 (tracking center)  
  > "Listed coordinates (rows “R.A." and “Dec." for right ascension and declination, respectively) correspond to the tracking center entered for the observations" (Table 1); z/distance v_rec 3491 km/s  
  > "The “$v_{\text{rec}}$" row lists the galaxy recession velocity in km s$^{-1}$ (taken from NED)" (Table 1); distance from NED  
  > "The “$v_{\text{rec}}$" row lists the galaxy recession velocity in km s$^{-1}$ (taken from NED)" (Table 1)
- Target **NGC 1068**: coordinates 02:42:40.770 -00:00:47.84 (tracking center)  
  > "Listed coordinates (rows “R.A." and “Dec." for right ascension and declination, respectively) correspond to the tracking center entered for the observations" (Table 1); z/distance v_rec 1137 km/s  
  > "The “$v_{\text{rec}}$" row lists the galaxy recession velocity in km s$^{-1}$ (taken from NED)" (Table 1); distance from NED  
  > "The “$v_{\text{rec}}$" row lists the galaxy recession velocity in km s$^{-1}$ (taken from NED)" (Table 1)
- Target **NGC 1386**: coordinates 03:36:46.237 -35:59:57.39 (tracking center)  
  > "Listed coordinates (rows “R.A." and “Dec." for right ascension and declination, respectively) correspond to the tracking center entered for the observations" (Table 1); z/distance v_rec 868 km/s  
  > "The “$v_{\text{rec}}$" row lists the galaxy recession velocity in km s$^{-1}$ (taken from NED)" (Table 1); distance from NED  
  > "The “$v_{\text{rec}}$" row lists the galaxy recession velocity in km s$^{-1}$ (taken from NED)" (Table 1)

## Data provenance

- ALMA projects: 2011.0.00121.S
- bands: Band 7, 321.226 GHz (NGC 5793 also 325.153 GHz)  
  > "All targets were observed at a rest-frame frequency of 321.226 GHz (ALMA Band 7)" (2 Observations)
- frequencies and spectral setup: 1.875 GHz bandwidth, 3840 channels of 0.488 MHz (~0.5 km/s)  
  > "which was split into 3840 channels spaced contiguously every 0.488 MHz" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: longest ~360 m  
  > "The longest baselines for these observations were $\sim$360 meters" (2 Observations)
- angular resolution: ~0.5''  
  > "corresponding to a typical resolution of $\sim$$0.5''$" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2012 Jun 01 to 2012 Aug 24  
  > "Observing date (UTC)" (Table 1)
- pi or archival as stated: Archival Cycle 0 data  
  > "We have analyzed archival Cycle 0 ALMA observations of five galaxies" (2 Observations)
- Line: ortho-H2O 10(2,9)-9(3,6) (321.226 GHz)
- Line: para-H2O 5(1,5)-4(2,2) (325.153 GHz)
- External data: Distance to NGC 4945 of 3.7 Mpc  
  > "Adopting a distance to NGC 4945 of 3.7 Mpc (cite: 2013AJ....146...86T)" (Discussion) [from (cite: 2013AJ....146...86T)]
- External data: Distance to Circinus 4.2 Mpc  
  > "At a distance to the galaxy of 4.2 Mpc" (Discussion) [from (cite: 2013AJ....145..101K)]
- External data: 22 GHz spectra of NGC 4945 and Circinus  
  > "top panel of Figure [3](#fig:NGC4945_321GHz_spectra) has been reproduced from (cite: 2003ApJS..146..249B)" (Discussion) [from (cite: 2003ApJS..146..249B)]

## Processing

### Calibration

- pipeline or manual: Archive datasets and initial calibration scripts used; post-processing in CASA  
  > "We obtained datasets and initial calibration scripts from the ALMA archive" (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan or Uranus  
  > "Flux calibrator" (Table 1)
- flux scale uncertainty: _not stated_
- self calibration: Circinus: phase-only on line, 1 min solint; NGC 4945: phase-only on continuum, baselines >150 m, 30 s solint  
  > "We found that a solution interval of 1 minute (averaging both polarizations) was optimal" (2.1 Circinus); "We used a solution interval of 30 seconds, averaging both polarizations." (2.2 NGC 4945)

### Imaging

- task: CASA clean  
  > "Initial imaging was performed using CASA task `clean` with natural UV weighting" (2.1 Circinus)
- deconvolver: _not stated_
- weighting robust: natural  
  > "natural UV weighting" (2.1 Circinus)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub with line-free channels  
  > "after using `uvcontsub` (specifying line-free channels) to remove the continuum contribution" (2.1 Circinus)
- line free channels: _not stated_
- primary beam correction: impbcor for NGC 4945  
  > "we used `impbcor` to apply a primary beam correction prior to extracting a spectrum from the data cube" (2.2 NGC 4945)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- CASA version
- line-free channel ranges
- image size and cell size
- clean threshold, masks and iterations
- spectral channel averaging details
- maser flux integration velocity limits
- number of self-cal iterations
- flux scale uncertainty

## Analysis recipe

1. **self-calibrate and image**: Phase-only self-cal using line (Circinus) or long-baseline continuum (NGC 4945), then clean imaging of line and continuum  
  > "we stopped iterating self-calibration once there was no noticeable increase in signal-to-noise ratio (SNR)" (2.1 Circinus)
   - software: CASA
   - fitting: _not stated_
   - validation: SNR improvement  
  > "The new calibration improves the SNR by a factor of $\sim$2 compared the initial analysis." (321 GHz H$_2$O masers in Circinus)
2. **derive ISM mass from continuum**: Aperture flux density converted with Scoville et al. relation  
  > "we use the results from (cite: 2011A&A...536A..21P) to fix $\beta = 1.8$, and we adopt a dust temperature of $T_d = 25$ K" (3.1)
   - assumption: beta=1.8, Td=25 K  
  > "we adopt a dust temperature of $T_d = 25$ K" (3.1)
   - fitting: _not stated_
   - validation: uncertainty from 15 off-source apertures  
  > "15 non-overlapping, identical apertures that are offset from the continuum emission" (3.1)
3. **maser isotropic luminosity**: L_iso = 0.335 D^2 integral S dv  
  > "\left( \frac{L_{\text{iso}}}{L_{\odot}} \right) = 0.335" (3.2)
   - fitting: _not stated_
   - validation: compared with 22 GHz  
  > "Insofar as we are able to discern spectral structure, we see that it appears to match reasonably well with previous observations of NGC 4945 at 22 GHz" (321 GHz H$_2$O masers in NGC 4945)

## Software

- **CASA** : all reduction, imaging, spectral analysis  
  > "all post-processing reduction, imaging, and spectral analysis was done using the Common Astronomy Software Applications package (CASA)" (2 Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| NGC 4945 maser integrated flux | 0.88 | not stated | Jy km/s | 3 | the observed flux of $0.88$ Jy km s$^{-1}$ corresponds to an isotropic luminosity of $L_{\text{iso}} = 4$ L$_{\odot}$ |
| NGC 4945 L_iso | 4 | not stated | Lsun | 3 | $L_{\text{iso}} = 4$ L$_{\odot}$ |
| Circinus maser flux | 17.5 | not stated | Jy km/s | 3 | the observed flux of $17.5$ Jy km s$^{-1}$ |
| NGC 4945 continuum flux density | 90.8 | 5.6 | mJy | 2 | $S_{\nu}$ (mJy) |

## Qualitative findings


## Claim tuples

- H: NGC 4945 hosts 321 GHz masers | E: Imaged archival Band 7 data | R: Features at 4-5 sigma, complex at ~9 sigma, 650-750 km/s | F: First submillimeter maser detection in NGC 4945 | **supported**
- H: 321 GHz masers trace the same sites as 22 GHz in Circinus | E: Compared spectra | R: Similar structure with excess at 650-750 km/s | F: 321 GHz masers may trace the disk at smaller radii | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Low SNR and ~0.5'' resolution preclude detailed characterization  
  > "The low signal-to-noise in the current observations precludes any detailed characterization of this system" (3.2)
- Caveat (inferred, ours): Single-epoch data
- Caveat (inferred, ours): maser positions unresolved
- Caveat (inferred, ours): gas mass depends on assumed Td and beta

## Reproducibility

- Data public (paper): Archival data obtained from ALMA archive  
  > "We obtained datasets and initial calibration scripts from the ALMA archive" (2 Observations)
- Products in archive: _not stated_
- Missing: CASA version
- Missing: imaging parameters
- Missing: line-free channels
- Data volume (inferred): tens of GB
- Score (inferred): 3/5, Public data and simple method, but many imaging parameters unstated.
- Rediscovery candidate: yes, Public data; numeric fluxes and masses can be rechecked.

## Links

- Companion: (cite: 2016arXiv160407937H) (Parallel analysis of NGC 4945 data)
- Companion: (cite: 2013ApJ...768L..38H) (Original Circinus 321 GHz detection)

## Checks

```json
{
 "quotes": 53,
 "quotes_ok": 53,
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
  "facts": 70,
  "stated": 42,
  "rate": 0.6
 },
 "evidence_ok": true
}
```
