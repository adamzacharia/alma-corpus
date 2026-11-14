# First M87 Event Horizon Telescope Results. I. The Shadow of the Supermassive Black Hole

`2019ApJ...875L...1E` | The Astrophysical Journal Letters 2019 | first author: Event Horizon Telescope Collaboration | arXiv: 1906.11238 | DOI: 10.3847/2041-8213/ab0ec7

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: agn_and_quasars, nearby_galaxies
- Question: Image the event-horizon-scale structure around the M87 supermassive black hole with the EHT at 1.3 mm, test whether it is a black hole shadow, and estimate the black hole mass.  
  > "To image and study this phenomenon, we have assembled the Event Horizon Telescope, a global very long baseline interferometry array observing at a wavelength of 1.3 mm." (abstract)
- Target **M87***: coordinates declination +12°  
  > "(+12° declination)" (Figure 1 caption); "Solid baselines represent mutual visibility on M87 [*] (+12° declination)." (Figure 1 caption); z/distance 16.8 ± 0.8 Mpc  
  > "adopt a distance to M87 of 16.8" (2. The Radio Core in M87); "Solid baselines represent mutual visibility on M87 [*] (+12° declination)." (Figure 1 caption); distance from Blakeslee et al. 2009; Bird et al. 2010; Cantiello et al. 2018 (see Paper VI)  
  > "Bird et al. 2010; Cantiello et al. 2018, see Paper VI)" (2. The Radio Core in M87); "Solid baselines represent mutual visibility on M87 [*] (+12° declination)." (Figure 1 caption)

## Data provenance

- ALMA projects: 2016.1.01154.V
- bands: 1.3 mm (230 GHz) VLBI, two 2 GHz bands centered at 227.1 and 229.1 GHz  
  > "two adjacent 2 GHz wide frequency bands centered at 227.1 and 229.1 GHz were converted to baseband" (4. Observations, Correlation, and Calibration)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: global VLBI array of eight stations over six locations (incl. ALMA, APEX, LMT, PV, SMT, JCMT, SMA, SPT)  
  > "the EHT collaboration fielded a global VLBI array of eight stations over six geographical locations." (3. The Event Horizon Telescope)
- configurations: _not stated_
- baselines: 160 m to 10,700 km  
  > "Baseline lengths ranged from 160 m to 10,700 km toward M87 [*]" (3. The Event Horizon Telescope)
- angular resolution: ~25 μas nominal  
  > "resulting in an array with a theoretical diffraction-limit resolution of ∼25 μas" (3. The Event Horizon Telescope)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2017 April 5, 6, 10, and 11  
  > "We observed M87 [*] on 2017 April 5, 6, 10, and 11 with the EHT." (4. Observations, Correlation, and Calibration)
- pi or archival as stated: _not stated_
- Other facility **EHT (APEX, LMT, IRAM 30m, SMT, JCMT, SMA, SPT)**: VLBI visibilities of M87* at 1.3 mm  
  > "The EHT (Paper II) is a VLBI experiment that directly measures “visibilities,” or Fourier components, of the radio brightness distribution on the sky." (3. The Event Horizon Telescope)
- External data: ALMA interferometric total flux density values used for amplitude calibration  
  > "By assuming total flux density values derived from ALMA interferometric data (Goddi et al. 2019)" (4. Observations, Correlation, and Calibration) [from Goddi et al. 2019]
- External data: Distance 16.8 ± 0.8 Mpc  
  > "adopt a distance to M87 of 16.8" (2. The Radio Core in M87) [from Blakeslee et al. 2009; Bird et al. 2010; Cantiello et al. 2018 (cite: Paper VI)]
- External data: Stellar-dynamics mass 6.2 +1.1/-0.6 ×10^9 Msun and gas-dynamics mass 3.5 +0.9/-0.3 ×10^9 Msun  
  > "M(gas) [e] 3.5 -+ 0.30.9 ´ 10 9 M e" (Table 1) [from Gebhardt et al. 2011; Walsh et al. 2013; Paper VI]
- Simulation/model as data: Library of 43 GRMHD simulations, >420 scenarios, >62,000 ray-traced images (Image Library)  
  > "we have used the Simulation Library to generate more than 420 different physical scenarios." (6. Theoretical Modeling)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: station sensitivities 5%–10% in amplitude; systematic ~1° phase, 2% amplitude  
  > "estimation of systematic baseline errors of around 1° in visibility phase and 2% for visibility amplitudes." (4. Observations, Correlation, and Calibration)
- self calibration: fitting station sensitivities and unknown station phases via self-calibration  
  > "remain after fitting station sensitivities and unknown station phases via self-calibration" (4. Observations, Correlation, and Calibration)

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
- array combination: _not stated_
- smoothing: each image blurred with circular Gaussian to common 20 μas resolution  
  > "we blurred each image with a circular Gaussian to a common, conservative angular resolution of 20 μas." (5. Images and Features)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Data reduction, correlation, calibration  
  > "is presented in Paper III and briefly summarized here." (4. Observations, Correlation, and Calibration) [from EHT Collaboration 2019b (Paper III)]
- Imaging details and Top-Set parameters  
  > "see Figure 4 in Paper IV" (5. Images and Features) [from EHT Collaboration 2019c (Paper IV)]
- Mass fitting and model comparison  
  > "In Paper VI, the black hole mass is derived from fitting to the visibility data of geometric and GRMHD models" (7. Model Comparison and Parameter Estimation) [from EHT Collaboration 2019e (Paper VI)]

### Not stated but needed to reproduce (our reading)

- Data release location and file names for EHT visibilities
- Priors, samplers and likelihoods of crescent and GRMHD fits (in Paper VI)
- Imaging parameters of the three pipelines (in Paper IV)
- ALMA phased-array calibration details (Goddi et al. 2019)

## Analysis recipe

1. **Correlate and calibrate VLBI data**: Software correlation, fringe fitting with three pipelines, network calibration with ALMA flux densities  
  > "Fringe fitting was performed with three independent automated pipelines" (4. Observations, Correlation, and Calibration)
   - software: DiFX, AIPS, CASA
   - fitting: _not stated_
   - validation: Comparison of pipelines, polarizations and bands  
  > "Comparisons between the three independent pipelines, the two polarizations, and the two frequency bands" (4. Observations, Correlation, and Calibration)
2. **Reconstruct images**: CLEAN and RML imaging with parameter surveys, Top-Set selection using synthetic data  
  > "We determined a “TopSet” of parameter combinations that both produced images of M87 [*] that were consistent with the observed data" (5. Images and Features)
   - fitting: _not stated_
   - validation: Synthetic data from ring, crescent, filled disk, asymmetric double source  
  > "reconstructed accurate images from synthetic data sets corresponding to four known geometric models" (5. Images and Features)
3. **Fit crescent and GRMHD models, derive mass**: Bayesian fits of crescent models to visibilities, calibrate α with Image Library, combine with distance  
  > "We used two distinct Bayesian-inference algorithms" (7. Model Comparison and Parameter Estimation)
   - assumption: Distance 16.8 ± 0.8 Mpc  
  > "distance of 16.8" (7. Model Comparison and Parameter Estimation)
   - fitting: Details in Paper VI  
  > "In Paper VI, the black hole mass is derived from fitting to the" (7. Model Comparison and Parameter Estimation)
   - validation: Consistency across methods and days  
  > "Our measurements remain consistent across methodologies, algorithms, data representations, and observed data sets." (7. Model Comparison and Parameter Estimation)

## Software

- **CASA** : standard radio-interferometric data processing in pipelines  
  > "(Greisen 2003; Whitney et al. 2004; McMullin et al. 2007, I. M. van Bemmel et al. 2019, in preparation)." (4. Observations, Correlation, and Calibration)
- **DiFX** : software correlator  
  > "Correlation of the data was carried out using a software correlator (Deller et al. 2007)" (4. Observations, Correlation, and Calibration)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Ring diameter | 42 | ±3 | μas | 3 | ring with a diameter of 42 |
| Central depression contrast | >10:1 | not stated | dimensionless | 3 | Crescent contrast [b] >10:1 |

## Qualitative findings

- Ring is brighter in the south, consistent with a clockwise-rotating flow and spin pointing away from Earth.  
  > "the spin of the black hole points away from us" (9. Conclusion and Outlook)

## Claim tuples

- H: M87* shows a black hole shadow ring | E: EHT 1.3 mm VLBI imaging on four days | R: Asymmetric ring of 42 ± 3 μas with >10:1 contrast | F: Consistent with the shadow of a Kerr black hole | **supported**
- H: The mass of M87* from the shadow size | E: Fit crescent, GRMHD and image-domain ring | R: M = (6.5 ± 0.7)×10^9 Msun | F: Favors stellar-dynamics mass | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Jet feature, random blobs and Einstein ring alternatives disfavored  
  > "the image is unlikely to be produced by a jet-feature" (8. Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Sparse (u,v) coverage makes imaging under-constrained  
  > "Because the (u, v) plane is only sparsely sampled (Figure 2), the inverse problem is under-constrained." (5. Images and Features)
- Caveat (inferred, ours): ALMA is only one station of a VLBI array; the ALMA archive entry is a VLBI project
- Caveat (inferred, ours): Mass depends on GRMHD calibration and adopted distance

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Public data release details
- Missing: Companion Papers III-VI for methods
- Data volume (inferred): Petabyte-scale raw VLBI recordings; calibrated data products much smaller
- Score (inferred): 2/5, Summary Letter; all methods deferred to companion papers; ALMA data are VLBI.
- Rediscovery candidate: no, Recipe is not given here and ALMA is only a VLBI station.

## Links

- Method: EHT Collaboration 2019b (Paper III) (data reduction and calibration)
- Method: EHT Collaboration 2019c (Paper IV) (imaging)
- Method: EHT Collaboration 2019e (Paper VI) (mass estimation)
- Companion: EHT Collaboration 2019a (Paper II) (instrument)
- Companion: EHT Collaboration 2019d (Paper V) (theoretical models)
- Related: Event Horizon Telescope

## Checks

```json
{
 "quotes": 43,
 "quotes_ok": 43,
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
  "facts": 66,
  "stated": 33,
  "rate": 0.5
 },
 "evidence_ok": true
}
```
