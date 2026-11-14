# Chasing the Break: Tracing the Full Evolution of a Black Hole X-Ray Binary Jet with Multiwavelength Spectral Modeling

`2024ApJ...962..116E` | The Astrophysical Journal 2024 | first author: Echiburú-Trujillo, Constanza | arXiv: 2311.11523 | DOI: 10.3847/1538-4357/ad1a10

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: stellar_physics, milky_way_ism
- Question: How does the jet spectral break of the black hole X-ray binary MAXI J1820+070 evolve through the full outburst, and how does it connect to the accretion flow?  
  > "This modeling allows us to track the evolution of the spectral break in the jet spectrum, a key observable that samples the jet launching region." (abstract)
- Target **MAXI J1820+070**: coordinates _not stated_; z/distance 2.96±0.33 kpc  
  > "a close distance ($2.96\pm0.33$ kpc, (cite: 2020MNRAS.493L..81A))" (2 MAXI J1820+070); distance from Atri et al. 2020 (cite: 2020MNRAS.493L..81A)  
  > "a close distance ($2.96\pm0.33$ kpc, (cite: 2020MNRAS.493L..81A))" (2 MAXI J1820+070)

## Data provenance

- ALMA projects: 2017.1.01103.T
- bands: Band 7 (central frequency 343.5 GHz)  
  > "observing in Band 7 (central frequency of 343.5 GHz)" (2.1.2 ALMA)
- frequencies and spectral setup: 4x2 GHz wide base-bands  
  > "The ALMA correlator was set up to yield 4$\times$2 GHz wide base-bands." (2.1.2 ALMA)
- continuum bandwidth: _not stated_
- arrays: 12-m array, Cycle 5 C3 configuration, 46 antennas  
  > "the 12-m array was in its Cycle 5 C3 configuration, with 46 antennas" (2.1.2 ALMA)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2018 April 12 to July 06  
  > "between 2018 April 12 and July 06 (observing up to 5 hrs on source per epoch)" (2.1.2 ALMA)
- pi or archival as stated: _not stated_
- Other facility **VLA, SMA, NOEMA, JCMT, AMI-LA**: radio/sub-mm flux densities  
  > "J1820 was observed with the National Radio Astronomy Observatory’s (NRAO) Karl G. Jansky Very Large Array" (2.1 Radio/(sub)-millimetre)
- Other facility **Swift XRT and UVOT**: X-ray and UV data  
  > "The UV/optical instrument UVOT onboard *Swift* observed J1820 simultaneously with the X-ray instrument XRT" (2.2.4 Swift/UVOT)
- Other facility **VLT VISIR, X-Shooter, LCO, REM, AAVSO**: IR/optical photometry and spectra  
  > "Mid-IR observations of the field of J1820 were made with the Very Large Telescope (VLT) on 14 dates" (2.2.1 VLT VISIR)
- External data: LOFAR, MeerKAT, eMERLIN, VLA 18A-277 and VLBA radio flux densities  
  > "We include additional long-wavelength data found in the literature from the Low Frequency ARray (LOFAR;" (2.1.7 Additional data from the literature) [from Broderick 2018; Bright 2020; Shaw 2021; Atri 2020]

## Processing

### Calibration

- pipeline or manual: ALMA data reduced and imaged within CASA; details in Tetarenko et al. 2021  
  > "These ALMA data were reduced and imaged within CASA." (2.1.2 ALMA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: point-source fit in image plane with imfit  
  > "Flux densities of the source were measured by fitting a point source in the image plane (using the `imfit` task)" (2.1.2 ALMA)
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

- ALMA observation and calibration details  
  > "Details on the observations and calibration process of these data can be found in (cite: atet21)." (2.1.2 ALMA) [from (cite: atet21)]

### Not stated but needed to reproduce (our reading)

- CASA version for ALMA
- ALMA calibrators and flux scale uncertainty
- imaging weighting, cell size, beam, rms for ALMA
- per-epoch ALMA integration times

## Analysis recipe

1. **measure radio/sub-mm flux densities**: point-source fit in image plane  
  > "Flux densities of the source were measured by fitting a point source in the image plane (using the `imfit` task)" (2.1.2 ALMA)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **fit broad-band SED per epoch**: XSPEC model redden*tbabs(highecut*bknpower+bbodyrad+diskir)  
  > "`redden*tbabs(highecut*bknpower+bbodyrad+diskir)`" (3.1 Spectral Modeling)
   - software: XSPEC
   - parameter: 14 walkers per free parameter, 10^6 steps, 30% burn-in  
  > "we standarized the number of walkers to 14 per free parameter and run the chains for $10^6$ steps, with a burn-in corresponding to 30% of the chain length" (3.1 Spectral Modeling)
   - assumption: E(B-V)=0.18, NH=1.5e21 cm^-2 fixed  
  > "$E(B-V)=0.18$ (cite: 2018ApJ...867L...9T) and $N_{\mathrm{H}}=1.5 \times 10^{21}$ $\mathrm{cm}^{-2}$" (3.1 Spectral Modeling)
   - fitting: Goodman-Weare MCMC in XSPEC, uniform priors  
  > "XSPEC uses the Goodman-Weare algorithm" (3.1 Spectral Modeling)
   - validation: Geweke convergence criterion and visual chain inspection  
  > "The convergence of the parameters is assessed with the Geweke convergence criteria" (3.1 Spectral Modeling)

## Software

- **CASA** v5.4 (VLA): reduction and imaging of radio/mm data  
  > "calibrated and imaged within the Common Astronomy Software Application package (CASA v5.4" (2.1.1 VLA)
- **XSPEC** v12.10.1: broad-band spectral fitting and MCMC  
  > "We use XSPEC to model the broad-band spectrum across multiple epochs." (3.1 Spectral Modeling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Jet break frequency, April 12 | 7.98e12 | ±0.06e12 | Hz | 2 | / April 12 / $7.98^{+0.06}_{-0.06} \times 10^{12}$ / $284.96_{-1.80}^{+1.84}$ / |
| Jet break frequency, May 17 | 1.16e12 | ±0.03e12 | Hz | 2 | / May 17 / $1.16^{+0.03}_{-0.03} \times 10^{12}$ / |

## Qualitative findings

- Break moves from IR to below 1e8 Hz in the soft state and returns to IR in the decline  
  > "we observe the jet spectral break shift to lower frequencies as the jet emission fades in the soft state, and move back to IR frequencies" (5 Conclusions)

## Claim tuples

- H: The jet quenches and recovers over the full outburst | E: SED fits at 19 epochs | R: Break shifts over at least 3 orders of magnitude | F: Jet quenching and recovery tied to accretion state | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): X-ray coverage limited to 1-10 keV  
  > "our *Swift*/XRT data is limited to 1–10 keV" (4.1 Source evolution)
- Caveat (inferred, ours): Phenomenological model with many fixed parameters
- Caveat (inferred, ours): Epochs quasi-simultaneous only within ±2 days
- Caveat (inferred, ours): Break often only a limit

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA calibration details deferred to Tetarenko et al. 2021
- Missing: MCMC initial guesses
- Data volume (inferred): ALMA ~ tens of GB; whole campaign larger
- Score (inferred): 3/5, ALMA is minor and deferred to another paper; the model is stated but many data are non-public.
- Rediscovery candidate: no, Multi-facility data, ALMA processing not described.

## Links

- Method: Tetarenko et al. 2021 (cite: atet21) (ALMA and VLA observation and calibration details)

## Checks

```json
{
 "quotes": 29,
 "quotes_ok": 29,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 2,
 "numeric_problems": 0,
 "fill": {
  "facts": 60,
  "stated": 24,
  "rate": 0.4
 },
 "evidence_ok": true
}
```
