# The Sun at millimeter wavelengths. II. Small-scale dynamic events in ALMA Band 3

`2020A&A...644A.152E` | Astronomy and Astrophysics 2020 | first author: Eklund, Henrik | arXiv: 2010.06400 | DOI: 10.1051/0004-6361/202038250

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: sun
- Question: How often do small-scale dynamic brightness-temperature events occur in the quiet Sun in ALMA Band 3, what are their properties, and are they consistent with propagating shock waves?  
  > "An important question in this regard is if the detected signatures are caused by propagating shock waves in the solar chromosphere." (1 Introduction)
- Target **Quiet Sun region near disc centre**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.00423.S
- bands: Band 3 (~3 mm / 100 GHz)  
  > "ALMA Band 3 data ($\sim 3$ mm / $100$ GHz)" (abstract)
- frequencies and spectral setup: four sub-bands: SB1 92-94, SB2 94-96, SB3 104-106, SB4 106-108 GHz  
  > "ALMA receiver band 3 is currently set up with four spectral sub-bands as indicated in Table" (2.1 Observational data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: clean beam mean ~1.4'' x 2.1'', PA 68 deg  
  > "has a mean value of about $1.4\ensuremath{''}$ and $2.1\ensuremath{''}$ along the minor and major axis respectively, with a beam position angle of $68^\circ$." (2.1 Observational data)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 22 Dec 2016, 14:19-15:07 UT, four 10-min scans with ~2.5 min gaps  
  > "The observations took place between $14$:$19 \text{UT} - 15$:$07 \text{UT}$ parted in four time scans in blocks of $10$ min each, separated by calibration gaps of $\sim2.5$ min." (2.1 Observational data)
- pi or archival as stated: _not stated_
- Other facility **SDO/HMI**: photospheric LOS magnetograms, 36 s cadence, co-aligned to ALMA  
  > "The magnetograms, measuring the Fe I line (6173 Å) at photospheric heights, have a cadence of $36$ seconds and are co-aligned with the ALMA observations." (2.1 Observational data)
- Other facility **SDO/AIA**: 170 nm and 30.4 nm channels used for spatial co-alignment  
  > "the ALMA images were cross-correlated with a combination of the $170$ nm and $30.4$ nm channels of the SDO’s Atmospheric Imaging Assembly" (2.1 Observational data)
- External data: Network/internetwork mask  
  > "The network/inter-network mask by (cite: 2020A&A...635A..71W) is overplotted in Fig." (3.2 Magnetic field strength) [from (cite: 2020A&A...635A..71W)]
- External data: Bifrost 3D simulation brightness temperature rms reduction factors with beam (0.70 NW, 0.53 IN)  
  > "reduces the brightness temperature standard deviation $T_\text{b}^\mathrm{rms}$ from $1794$ K to $1254$ K for network pixels" (4.2 Shock wave propagation in a 3D environment) [from (cite: 2020A&A...635A..71W)]
- Simulation/model as data: RADYN 1D piston-driven acoustic wave simulations, RH 1.5D radiative transfer, 1500 s, 1 s cadence  
  > "The duration of the simulations is $1500$ seconds" (4.1 1D numerical simulations)
- Simulation/model as data: Bifrost 3D MHD simulation with ART code brightness temperature maps, degraded with clean beam  
  > "the maps are degraded to the resolution of the ALMA band 3 observations by convolution with the clean beam" (4.2 Shock wave propagation in a 3D environment)

## Processing

### Calibration

- pipeline or manual: Solar Alma Pipeline (SoAP); calibration with script delivered with the data from the ALMA Science Archive  
  > "The data set is processed using the Solar Alma Pipeline (SoAP)." (2.1 Observational data); "data set is calibrated (with a script delivered together with the data from the ALMA Science Archive)" (2.1 Observational data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: Multiscale CLEAN  
  > "followed by deconvolution using the Multiscale CLEAN algorithm" (2.1 Observational data)
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 0.32''  
  > "The pixel size of the final images is $0.32\ensuremath{''}$." (2.1 Observational data)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied; output cut at radius 32.8'' (0.3 main beam power response)  
  > "The cut-off point corresponds to 0.3 times the main beam power response." (2.1 Observational data)
- array combination: interferometric maps feathered with single-dish total power  
  > "These are combined (‘feathered’) with single dish total power measurements." (2.1 Observational data)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- SoAP processing and data details  
  > "The specifics of SoAP will be explained in detail in a forthcoming paper (cite: 2020A&A...635A..71W)." (2.1 Observational data) [from (cite: 2020A&A...635A..71W)]

### Not stated but needed to reproduce (our reading)

- SoAP software and version (not public per text), CLEAN parameters, scales, thresholds
- Number of clusters k chosen and clustering settings
- Definition of 'significant local minima' for peak detection
- Co-alignment procedure details
- ART code is in prep. and RADYN/RH run details (grids) incomplete
- Time-averaged noise/uncertainty of Tb

## Analysis recipe

1. **Produce Tb time series**: SoAP imaging of all sub-bands combined, feathering, Rayleigh-Jeans conversion to Tb, 2 s cadence, 1200 steps  
  > "The final dataset has a cadence of 2 s, with a total of 1200 time steps." (2.1 Observational data)
   - software: SoAP
   - assumption: Rayleigh-Jeans law and LTE  
  > "under the assumption of the Rayleigh-Jeans law and formation in local thermodynamic equilibrium" (2.1 Observational data)
   - fitting: _not stated_
   - validation: _not stated_
2. **Detect Tb peaks per pixel**: Box-car smoothing over 7 time steps (14 s); find rise-then-fall peaks with amplitude >= 400 K relative to nearest significant local minimum; lifetime = FWHM  
  > "the data is box-car averaged in time with a size of $7$ time steps $(14\,s)$." (2.2 Event definition and selection)
   - parameter: amplitude threshold 400 K  
  > "with an amplitude of at least $400$ K" (2.2 Event definition and selection)
   - fitting: _not stated_
   - validation: conservative criteria to minimize false detections  
  > "the criteria are defined more conservatively for this initial study in order to minimize the number of false detection." (2.2 Event definition and selection)
3. **Group pixels into events**: k-means clustering in space and time within 15'' radius; events fully in one time scan; number of clusters via elbow and silhouette methods  
  > "The pixels showing such a temporary rise in brightness temperature are grouped together using the k-means clustering method" (2.2 Event definition and selection)
   - parameter: radius 15''  
  > "the k-means clustering is only applied to the innermost parts within a radius of $15\ensuremath{''}$." (2.2 Event definition and selection)
   - fitting: _not stated_
   - validation: elbow and silhouette methods  
  > "This method is commonly referred to as the "silhouette method"." (2.2 Event definition and selection)
4. **Event statistics and magnetic field comparison**: Size, lifetime, amplitude, base Tb, apparent motion, repetitiveness, HMI LOS field at event location; NW/IN mask  
  > "the apparent motion is estimated for each event." (3.3 Statistical study)
   - fitting: _not stated_
   - validation: _not stated_
5. **Compare with shock simulations**: RADYN 1D piston-driven waves + RH 1.5D, Band 3 mean of four sub-bands; Bifrost+ART degraded with clean beam to derive reduction factor  
  > "The limited spatial resolution of the ALMA band 3 observations thus results in an observable signature of this shock wave example, $\sim 0.18$ times the original $\Delta T_\text{b}$ magnitude." (4.2 Shock wave propagation in a 3D environment)
   - software: RADYN, RH 1.5D, Bifrost, ART
   - parameter: initial amplitude 0.005-0.05 v0, period 90-210 s  
  > "Distinct shock waves are excited with an initial amplitude between $0.005 v_0 - 0.05 v_0$ and wave periodicity between $P \approx 90 - 210$ s." (4.1 1D numerical simulations)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **SoAP** : calibration/imaging pipeline for solar ALMA data  
  > "The data set is processed using the Solar Alma Pipeline (SoAP)." (2.1 Observational data)
- **RADYN** : 1D radiation-hydrodynamic shock simulations  
  > "The hydrodynamic code RADYN" (4.1 1D numerical simulations)
- **RH 1.5D** : radiative transfer through RADYN atmospheres  
  > "calculated using the RH 1.5D code" (4.1 1D numerical simulations)
- **Bifrost** : 3D MHD simulation  
  > "numerical simulations with the Bifrost code" (4.2 Shock wave propagation in a 3D environment)
- **ART** : Tb maps from Bifrost at Band 3 wavelengths  
  > "calculated with the Advanced Radiative Transfer (ART) code" (4.2 Shock wave propagation in a 3D environment)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of events | 552 | not stated | dimensionless | 3 | A total number of $552$ events are found within the inner parts of the FOV with a radius of $15$$''$ |
| Typical Tb excess (50% of events) | ~450-750 | not stated | K | 4 | with values between $\sim450$ – $750$ K and $\sim 55$ – $125$ s for $50~\%$ of the distribution. |
| Event lifetime range (FWHM) | ~43-360 | not stated | s | 4 | The lifetimes ranging between $\sim43$ – $360$ s |
| Resolution reduction factor of Tb excess (Bifrost example) | ~0.18 | not stated | dimensionless | 5 | $\sim 0.18$ times the original $\Delta T_\text{b}$ magnitude |
| 1D simulated Tb excess for P=90-210 s | ~2000-4450 | not stated | K | 5 | values of the brightness temperature excess between $\sim 2000$ K to $4450$ K are seen |
| Mean Tb of area | 7402 | not stated | K | 4 | $<T_\text{b}>_{x,y,t} = 7402$ K and $7336$ K |

## Qualitative findings

- Few events in areas with strong photospheric magnetic field; none at |B| > ~250 G  
  > "there are no $T_\mathrm{b}$ peaks at locations with absolute LOS magnetic field strength larger than $\sim 250$ G" (3.2 Magnetic field strength)

## Claim tuples

- H: Small-scale dynamic events in Band 3 are consistent with propagating shock waves | E: Detect events, compare amplitude, lifetime, apparent motion and magnetic field to 1D RADYN and 3D Bifrost predictions | R: 552 events, 450-750 K typical, apparent speeds mostly <10 km/s, low B; 1D amplitudes ~3-4x larger but reduced by beam degradation | F: Many events plausibly originate in shock waves | **partially**
- H: Limited resolution reduces observed Tb excess | E: Degrade Bifrost maps to clean beam | R: 3600 K to 640 K | F: Observed amplitudes are lower limits | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Resolution limits detection; 552 events is a lower limit  
  > "the $552$ detected dynamical events in this dataset (within $15"$ radius) must therefore be considered to be a lower limit only." (4.3 Detection of events)
- Caveat (inferred, ours): Shock identification relies on loose criteria and 1D models
- Caveat (inferred, ours): Event detection thresholds are arbitrary and no false-detection rate is quantified
- Caveat (inferred, ours): Single 40-min dataset

## Reproducibility

- Data public (paper): Data from ALMA Science Archive project 2016.1.00423.S  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00423.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: SoAP pipeline and settings
- Missing: k-means cluster number
- Missing: ART code (in prep.)
- Data volume (inferred): tens to hundreds of GB raw; processed cube small
- Score (inferred): 4/5, Data public, event detection described, but processing relies on unreleased SoAP and details are missing.
- Rediscovery candidate: no, Pipeline and clustering parameters are not fully specified.

## Links

- Method: (cite: 2020A&A...635A..71W) (SoAP and dataset description)
- Companion: (cite: 2020arXiv200805324E) (3D shock wave analysis)
- Related: SolarALMA
- Related: SSALMON

## Checks

```json
{
 "quotes": 47,
 "quotes_ok": 47,
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
  "facts": 76,
  "stated": 36,
  "rate": 0.474
 },
 "evidence_ok": true
}
```
