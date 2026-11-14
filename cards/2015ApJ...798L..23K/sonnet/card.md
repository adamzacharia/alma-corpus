# An ALMA Disk Mass for the Candidate Protoplanetary Companion to FW Tau

`2015ApJ...798L..23K` | The Astrophysical Journal Letters 2015 | first author: Kraus, Adam L. | arXiv: 1412.2175 | DOI: 10.1088/2041-8205/798/1/L23

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: Is the 1.3 mm continuum (disk) emission in FW Tau associated with the close binary FW Tau AB or the faint companion, and what is the dust mass?  
  > "designed to confirm and localize the putative long-wavelength continuum emission (to FW Tau AB or to FW Tau C) and to more accurately measure the mass of the dust responsible for it." (3 The FW Tau System)
- Target **FW Tau (AB + companion C/b)**: coordinates _not stated_; z/distance d ~ 140 pc  
  > "FW Tau is a member of the Taurus-Auriga association, a nearby ($d \sim 140$ pc), young ($\tau \sim 2$ Myr) region of ongoing star formation." (2 The FW Tau System); distance from Taurus-Auriga association distance (no specific citation)  
  > "FW Tau is a member of the Taurus-Auriga association, a nearby ($d \sim 140$ pc), young ($\tau \sim 2$ Myr) region of ongoing star formation." (2 The FW Tau System)

## Data provenance

- ALMA projects: 2012.1.00989.S
- bands: Band 6 (mean 224 GHz, 1.34 mm)  
  > "the Band 6 receivers under excellent conditions (0.6 mm of precipitable water vapor)" (ALMA Observations and Data Reduction)
- frequencies and spectral setup: four spectral windows at 215, 217, 230.5, 233 GHz; 128 channels of 15.625 MHz each  
  > "centered at 215, 217, 230.5, and 233 GHz (a mean frequency of 224 GHz, or $\lambda = 1.34$ mm), each with 128 coarse channels (15.625 MHz resolution)" (ALMA Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: 27 12 m antennas  
  > "using 27 available 12 m antennas in an intermediate configuration (baseline lengths of 17–460 m)" (ALMA Observations and Data Reduction)
- configurations: _not stated_
- baselines: 17–460 m  
  > "baseline lengths of 17–460 m" (ALMA Observations and Data Reduction)
- angular resolution: 1.45" x 0.75" (PA 131 deg)  
  > "restored with a $1.45\ensuremath{''}\times0.75\ensuremath{''}$ (P.A. = 131$^\circ$) synthesized beam" (ALMA Observations and Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: 28 uJy/beam RMS  
  > "The RMS noise level in the resulting image is 28 $\mu$Jy beam$^{-1}$." (ALMA Observations and Data Reduction)
- time on source: 22 minutes  
  > "The total on-source time for the FW Tau field was 22 minutes." (ALMA Observations and Data Reduction)
- observing dates: 2013 December 2 (Cycle 1)  
  > "FW Tau was briefly observed with ALMA in Cycle 1 on 2013 December 2" (ALMA Observations and Data Reduction)
- pi or archival as stated: _not stated_
- Line: CO J=3-2 (not stated)
- Other facility **Keck/NIRC2**: K' image of FW Tau components for overlay  
  > "overlaid on the Keck/NIRC2 $K^{\prime}$ image of the FW Tau components (cite: Kraus:2014lr)" (Results)
- External data: 850 um flux 4.5 ± 1.1 mJy of FW Tau system  
  > "noted a 4$\sigma$ detection of the system at 850 $\mu$m ($F_{\nu}=4.5 \pm 1.1$ mJy)" (2 The FW Tau System) [from Andrews & Williams 2005 (cite: Andrews:2005qf)]
- External data: Herschel fluxes 30, 33, 70 mJy at 70, 100, 160 um  
  > "$F_{\nu} = 30 \pm 4$, $33\pm4$, and $70\pm40$ mJy at 70, 100, and 160 $\mu$m, respectively" (2 The FW Tau System) [from Howard et al. 2013 (cite: Howard:2013qy)]
- External data: Companion position 2.28" separation, PA 296 deg, and 3.6 um magnitude  
  > "from the FW Tau AB photocenter (cite: Kraus:2014lr)" (Results) [from Kraus et al. 2014 (cite: Kraus:2014lr)]

## Processing

### Calibration

- pipeline or manual: CASA calibration: WVR phase correction, Tsys, flagging, bandpass (J0522-3627), flux (Ganymede), gain (J051002+180041)  
  > "The absolute flux scaling was bootstrapped from observations of Ganymede." (ALMA Observations and Data Reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ganymede  
  > "The absolute flux scaling was bootstrapped from observations of Ganymede." (ALMA Observations and Data Reduction)
- flux scale uncertainty: ~10% systematic  
  > "with an additional $\sim$10% systematic uncertainty in the flux scale" (Results)
- self calibration: single iteration of phase-only self-calibration  
  > "after a single iteration of phase-only self-calibration" (ALMA Observations and Data Reduction)

### Imaging

- task: _not stated_
- deconvolver: CLEAN  
  > "deconvolved with the `CLEAN` algorithm" (ALMA Observations and Data Reduction)
- weighting robust: natural weighting  
  > "(assuming natural weighting)" (ALMA Observations and Data Reduction)
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
- final beam: 1.45" x 0.75", PA 131 deg  
  > "restored with a $1.45\ensuremath{''}\times0.75\ensuremath{''}$ (P.A. = 131$^\circ$) synthesized beam" (ALMA Observations and Data Reduction)
- final rms: 28 uJy/beam  
  > "The RMS noise level in the resulting image is 28 $\mu$Jy beam$^{-1}$." (ALMA Observations and Data Reduction)

### Inherited from earlier work

- Standard dust opacity/optically thin assumption  
  > "entirely optically thin for any reasonable dust opacity (cite: Beckwith:1990uq)" (Results) [from (cite: Beckwith:1990uq)]

### Not stated but needed to reproduce (our reading)

- CASA version
- Image size and cell size, CLEAN threshold/mask and iterations
- Self-calibration solution interval and reference
- Gaussian visibility fit procedure/software
- Dust mass equation details, gas-to-dust ratio, distance used
- Derivation of the 3 sigma AB upper limit of 90 uJy and 0.1 Earth mass
- Source coordinates

## Analysis recipe

1. **Calibrate and image continuum**: CASA calibration, natural-weighted CLEAN with one phase-only self-cal iteration  
  > "The spectrally-averaged calibrated visibilities were Fourier inverted (assuming natural weighting), deconvolved with the `CLEAN` algorithm" (ALMA Observations and Data Reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure continuum flux of companion**: Gaussian fit to emission, model of visibilities; unresolved  
  > "A Gaussian fit to the emission indicates that it is unresolved in the $\sim$200$\times$100 AU beam" (Results)
   - fitting: Gaussian model of the visibilities  
  > "as estimated from a Gaussian model of the visibilities" (Results)
   - validation: _not stated_
3. **Convert flux to dust mass**: Optically thin conversion  
  > "so the flux measurement can be simply converted into a dust mass estimate." (Results)
   - assumption: Dust temperature ~10–20 K; opacity 2.3 cm^2/g at 1.3 mm  
  > "Assuming a characteristic dust temperature of $\sim$10–20 K and a standard opacity of 2.3 cm$^{2}$ g$^{-1}$ at 1.3 mm" (Results)
   - fitting: _not stated_
   - validation: Compared with 850 um flux, spectral index 2.2±0.6  
  > "the corresponding spectrum scales like $F_{\nu} \propto \nu^{2.2\pm0.6}$" (Results)

## Software

- **CASA** : calibration and imaging  
  > "The raw ALMA visibilities were calibrated and imaged with the `CASA` software package." (ALMA Observations and Data Reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 1.3 mm integrated flux of FW Tau C | 1.78 | 0.03 (+~10% systematic) | mJy | 2 | has an integrated $F_{\nu} = 1.78\pm0.03$ mJy |
| Dust mass of FW Tau C | 1–2 | not stated | Earth masses | 3 | we infer $M_{\rm dust} \approx 1$–2 M$_{\oplus}$ |
| FW Tau AB flux upper limit | ≤90 | 3 sigma | uJy | 2 | $F_{\nu} \le 90$ $\mu$Jy ($3\sigma$) |
| FW Tau AB dust mass limit | ≲0.1 | not stated | Earth masses | 3 | corresponds to a dust mass limit of $\lesssim$0.1 $M_{\oplus}$ |
| CO 3-2 peak flux upper limit | ~3 | 3 sigma | mJy/beam per 20 km/s channel | 0 | The 3$\sigma$ upper limit on the peak flux is $\sim$3 mJy beam$^{-1}$ in a single 20 km s$^{-1}$-wide channel. |

## Qualitative findings

- All disk material in the system is associated with FW Tau C, not AB  
  > "all of the disk material in the system is associated solely with the faint companion, FW Tau C" (Discussion)

## Claim tuples

- H: Is the mm emission from AB or C? | E: 1.3 mm ALMA imaging | R: Detection centered on C at S/N~60; AB undetected | F: Disk is around FW Tau C | **supported**
- H: Disk mass can form giant planets? | E: Dust mass from flux | R: 1–2 Earth masses | F: Insufficient for giant planet; sufficient for Kepler-42-like system or Galilean satellites | **supported**
- H: Is C a planetary-mass companion or a brown dwarf? | E: Compare fluxes to Taurus relations | R: Ambiguous | F: Nature remains unclear | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Veiling prevents accurate spectral type/mass determination of the companion  
  > "substantial veiling prevents a more accurate determination of the effective temperature (and hence mass)" (abstract)
- Caveat (inferred, ours): Dust mass depends on assumed opacity and temperature; no uncertainty given
- Caveat (inferred, ours): Single short observation, unresolved source; no disk geometry constraint

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: CASA version and imaging parameters
- Missing: Self-cal details
- Data volume (inferred): ~5-10 GB
- Score (inferred): 3/5, Short observation and simple analysis, but imaging parameters and CASA version are missing.
- Rediscovery candidate: yes, Data are from a Cycle 1 project and the simple flux measurement is numeric, though public status is not stated by the paper.

## Links

- Companion: Kraus et al. 2014 (cite: Kraus:2014lr) (Companion discovery and characterization, AO imaging)
- Companion: Bowler et al. 2014 (cite: Bowler:2014lr) (Near-infrared spectrum of FW Tau C)

## Checks

```json
{
 "quotes": 44,
 "quotes_ok": 44,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 61,
  "stated": 33,
  "rate": 0.541
 },
 "evidence_ok": true
}
```
