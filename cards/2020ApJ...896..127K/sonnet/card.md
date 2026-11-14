# Multiple Outflows in the High-mass Cluster-forming Region G25.82-0.17

`2020ApJ...896..127K` | The Astrophysical Journal 2020 | first author: Kim, Jungha | arXiv: 2005.05006 | DOI: 10.3847/1538-4357/ab9100

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism
- Question: What are the evolutionary stages, outflows, disk/rotation and mass of the YSOs in the high-mass cluster-forming region G25.82-0.17, and does it support turbulent core accretion?  
  > "To investigate the mechanism of high-mass star formation in the G25.82 region, we carried out 1.3 mm continuum and spectral line observations with ALMA and 22 GHz H$_2$O maser observations using KaVA and VERA." (Summary)
- Target **G25.82-0.17**: coordinates phase center (18h39m03.63s, -06d24m09.5s) J2000  
  > "The systemic velocity of G25.82–0.17 is 93.7 km s$^{-1}$ from ammonia (the NH$_3$ (1,1) line) observations using the Effelsberg 100 m telescope (cite: wienen12), with a corresponding kinematic distance of 5 $\pm$ 0.3 kpc (cite: green11)." (1 INTRODUCTION); z/distance 5 ± 0.3 kpc (kinematic); Vsys 93.7 km/s  
  > "The systemic velocity of G25.82–0.17 is 93.7 km s$^{-1}$ from ammonia (the NH$_3$ (1,1) line) observations using the Effelsberg 100 m telescope (cite: wienen12), with a corresponding kinematic distance of 5 $\pm$ 0.3 kpc (cite: green11)." (1 INTRODUCTION); distance from kinematic distance, Green & McClure-Griffiths 2011  
  > "The systemic velocity of G25.82–0.17 is 93.7 km s$^{-1}$ from ammonia (the NH$_3$ (1,1) line) observations using the Effelsberg 100 m telescope (cite: wienen12), with a corresponding kinematic distance of 5 $\pm$ 0.3 kpc (cite: green11)." (1 INTRODUCTION)

## Data provenance

- ALMA projects: 2015.1.01288.S
- bands: Band 6 (230 GHz)  
  > "ALMA observations of G25.82 in Band 6 (230 GHz) were performed as a part of the KaVA LP project" (2.1 ALMA Observations)
- frequencies and spectral setup: five spws; 1953.04 kHz (~2.6 km/s) resolution, 937.5 MHz bandwidth  
  > "The spectral resolution and bandwidth were 1953.04 kHz ($\sim$2.6 km s$^{-1}$) and 937.5 MHz ($\sim$1300 km s$^{-1}$), respectively." (2.1 ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: 36 12 m antennas  
  > "The number of 12 m antennas was 36 and baseline lengths ranged from 15 to 1462 m." (2.1 ALMA Observations)
- configurations: _not stated_
- baselines: 15 to 1462 m  
  > "baseline lengths ranged from 15 to 1462 m" (2.1 ALMA Observations)
- angular resolution: continuum 0.27" x 0.24", PA -83.6  
  > "the synthesized beam size of the continuum data was $0.27\ensuremath{''}\ \times 0.24\ensuremath{''}$ with a position angle of -83.6" (2.1 ALMA Observations)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 0.40 mJy/beam; lines 1.24-1.45 mJy/beam  
  > "| Continuum |  |  |  | 0.40 | ... | ALMA |" (Table 1)
- time on source: 33 minutes  
  > "The on-source time was 33 minutes." (2.1 ALMA Observations)
- observing dates: August 19 and 22, 2016  
  > "on August 19, and 22, 2016" (2.1 ALMA Observations)
- pi or archival as stated: _not stated_
- Line: SiO 5–4 (217.104980 GHz)
- Line: CH3OH 8-1–70 E (229.758811 GHz)
- Line: CH3OH 224–215 E (230.368199 GHz)
- Line: H2O 616–523 (22.235080 GHz)
- Other facility **KaVA**: 22 GHz H2O maser VLBI imaging  
  > "We carried out VLBI observations on November 17, 2016, with KaVA toward G25.82 at K-band (22 GHz)." (2.2 KaVA Observations)
- Other facility **VERA**: phase-referenced absolute positions of H2O masers  
  > "This method is used to derive accurate absolute positions of the H$_2$O maser spots." (2.3 VERA Observations)
- External data: Systemic velocity 93.7 km/s from NH3(1,1)  
  > "The systemic velocity of G25.82–0.17 is 93.7 km s$^{-1}$ from ammonia (the NH$_3$ (1,1) line) observations using the Effelsberg 100 m telescope (cite: wienen12)" (1 INTRODUCTION) [from (cite: wienen12)]
- External data: VLA radio continuum and 6.7 GHz masers  
  > "In addition, a radio continuum source was also detected in this region using the VLA (cite: hu16)." (4.2) [from (cite: hu16)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline for initial calibration  
  > "Initial data calibration was carried out using the ALMA pipeline from the CASA[^1] package version 4.7" (2.1 ALMA Observations)
- casa version: CASA 4.7  
  > "Initial data calibration was carried out using the ALMA pipeline from the CASA[^1] package version 4.7" (2.1 ALMA Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: robust = 0.5 (line images)  
  > "using a robust weighting of 0.5" (2.1 ALMA Observations)
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
- final beam: continuum 0.27"x0.24"; lines 0.25"x0.26" to 0.30"x0.26"  
  > "Synthesized beams for the line images range from $0.25\ensuremath{''}\ \times 0.26\ensuremath{''}$ to $0.30\ensuremath{''}\ \times 0.26\ensuremath{''}$" (2.1 ALMA Observations)
- final rms: continuum 0.4 mJy/beam  
  > "1$\sigma=0.4$ mJy beam$^{-1}$" (3.1 Continuum Emission)

### Not stated but needed to reproduce (our reading)

- Self-calibration, if any
- Line-free channels and continuum-subtraction method
- Imaging task, cell size, image size, masking, and deconvolver
- Continuum weighting and spw selection for the continuum
- Flux calibrator and flux scale uncertainty
- Details of the robust Gaussian line fits
- Moment map clipping thresholds
- Uncertainty derivation for the total mass range

## Analysis recipe

1. **Identify continuum sources**: 2D Gaussian fits to emission >10 sigma in 1.3 mm continuum  
  > "Three components were identified by two-dimensional Gaussian fits to emission at intensities larger than 10$\sigma$ of the noise level" (3.1 Continuum Emission)
   - software: Miriad
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure line parameters and outflow maps**: Robust Gaussian fits to line profiles; integrated intensity maps over blue/red velocity ranges for SiO  
  > "Using a Gaussian profile, robust fitting was done to derive line parameters such as the peak flux density, central velocity, and full width half maximum (FWHM) of the Gaussian." (3.2 Molecular Line Emission)
   - software: Miriad
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive total mass from dust continuum**: Optically thin graybody M = S D^2/(kappa B(Tdust))  
  > "Assuming the emission is optically thin graybody radiation, we can derive the total enclosed mass (gas+dust)" (4.1 Mass Estimation)
   - assumption: Tdust = 150 K (75-300 K); D = 5.0 kpc; kappa=0.1(250um/lambda)^beta cm2/g, beta=1.85; gas-to-dust 100; starless cores at 15 K  
  > "dust temperature ($T_{\textrm{dust}}$) is assumed to be 150 K with an uncertainty by a factor of 2 (75 K - 300 K)." (4.1 Mass Estimation)
   - fitting: _not stated_
   - validation: _not stated_
4. **Dynamical mass**: Keplerian M=Rv^2/G for edge-on rotation using CH3OH 22_4-21_5 ring  
  > "Dynamical mass of the central protostar can be estimated assuming that the 230 GHz CH$_3$OH line emission arises from an edge-on rotating structure with the Keplerian rotation" (4.1 Mass Estimation)
   - parameter: R = 2500 au (0.5"), v = 3 km/s  
  > "is the radius of the 230 GHz CH$_3$OH 22$_{4}$–21$_{5}$ E line emission of 2500 au (0.5$''$) and $v$ is the velocity difference within $R$ of 3 km s$^{-1}$" (4.1 Mass Estimation)
   - assumption: edge-on geometry, so mass is a lower limit  
  > "Our mass estimate is a lower limit because the inclination of the disk is unknown." (4.1 Mass Estimation)
   - fitting: _not stated_
   - validation: _not stated_
5. **Maser spot positions**: AIPS calibration, IMAGR imaging, SAD Gaussian fits to channel maps at >5 sigma  
  > "The peak positions of maser spots were derived by Gaussian fitting to the individual channel images using the AIPS task SAD." (2.2 KaVA Observations)
   - software: AIPS
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7: ALMA pipeline calibration  
  > "Initial data calibration was carried out using the ALMA pipeline from the CASA[^1] package version 4.7" (2.1 ALMA Observations)
- **Miriad** : plotting and analysis of ALMA data  
  > "Plotting and analysis were done with the *Miriad*[^2] software package" (2.1 ALMA Observations)
- **AIPS** : KaVA/VERA calibration, imaging, spot fitting  
  > "KaVA data calibration was carried out using the Astronomical Image Processing System (AIPS)" (2.2 KaVA Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| G25.82-W1 integrated 1.3 mm flux | 377 | 0.8 | mJy | 1 | / G25.82–W1 / 18:39:03.62 / -6:24:11.31 / 143 (0.2) / 377 (0.8) / |
| G25.82-W1 total mass | 20-84 | from Tdust 75-300 K | Msun | 3 | The total mass is estimated to be 20 M$_\odot$-84 M$_\odot$ assuming the gas to dust mass ratio of 100. |
| G25.82-W1 dynamical mass | 25 | 11 | Msun | 4 | The derived mass is 25 $\pm$ 11 M$_\odot$ in the case of the edge-on geometry. |
| G25.82-W1 luminosity | ~1.3e4 | not stated | Lsun | 3 | the luminosity of G25.82–W1 is estimated to be $\sim1.3\times10^{4}$ L$_{\odot}$ |
| Masses of W2 and W3 | 361 and 99 | not stated | Msun | 3 | The derived masses of these cores are 361 M$_{\odot}$ and 99 M$_{\odot}$, respectively |
| SiO 5-4 FWHM | 11.7 | not stated | km/s | 2 | The SiO 5–4 line has a broader FWHM ($\Delta v \sim$ 11.7 km s$^{-1}$) |

## Qualitative findings

- Two SiO outflows (N–S and SE–NW); N–S driven by G25.82-W1, SE–NW driver uncertain  
  > "The driving source of the N–S SiO outflow is G25.82–W1 while that of the SE–NW SiO outflow is uncertain." (Summary)

## Claim tuples

- H: Is G25.82-W1 a high-mass YSO with a rotating structure? | E: Continuum mass and Keplerian estimate from CH3OH 22_4-21_5 velocity gradient | R: Total mass 20-84 Msun; dynamical mass 25±11 Msun lower limit | F: G25.82-W1 is a HM-YSO with rotating disk or envelope | **supported**
- H: Does G25.82 contain multiple outflows? | E: SiO 5-4 integrated maps and H2O masers | R: Two SiO outflows plus an H2O maser outflow with inconsistent velocity structure | F: Multiple outflows from a cluster-forming region | **supported**
- H: Do high-mass stars form in individual high-mass cores (turbulent core accretion)? | E: Search for low-mass cores in 1.3 mm continuum | R: No low-mass cores detected at 5 sigma ~2 mJy/beam (~0.5 Msun) | F: Consistent with scaled-up low-mass formation, unresolved cores not excluded | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: H2O maser outflow could be a separate small-scale outflow or the inner part of the N–S SiO outflow  
  > "However, we cannot rule out the possibility that the H$_2$O maser outflow is tracing the inner part of the large scale outflow (N–S SiO outflow)." (4.3)
- How they decided it was enough: _not stated_
- Limitation (authors): Dynamical mass is a lower limit because inclination is unknown  
  > "Our mass estimate is a lower limit because the inclination of the disk is unknown." (4.1 Mass Estimation)
- Caveat (inferred, ours): Dynamical mass from a crude R v^2/G with a 3 km/s velocity difference at ~2.6 km/s channels is poorly constrained
- Caveat (inferred, ours): Assumed Tdust of 150 K drives the mass range
- Caveat (inferred, ours): The non-detection of low-mass cores at 0.25" resolution does not rule out unresolved cores
- Caveat (inferred, ours): Class I maser vs thermal CH3OH interpretation is qualitative

## Reproducibility

- Data public (paper): ALMA project code given; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA$\#$2015.1.01288.S." (Summary)
- Products in archive: _not stated_
- Missing: Imaging parameters (cell, size, masks, continuum channels)
- Missing: Line-free channels
- Missing: Moment map thresholds
- Missing: Manifest links 2015.1.01571.S, which the paper does not mention
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Data are identifiable and the analysis is simple, but imaging details are sparse.
- Rediscovery candidate: no, Imaging recipe is incomplete and the key results rely on assumed parameters and qualitative maps.

## Links

- Companion: Kim, J., Hirota, T., Kim, K.-T., et al. 2018 (cite: kimj18) (KaVA large program overview)
- Related: KaVA Large Program on high-mass star formation

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
 "codes_not_in_obscore": [
  "2015.1.01288.S"
 ],
 "obscore_codes_not_in_card": [
  "2015.1.01571.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 36,
  "rate": 0.507
 },
 "evidence_ok": true
}
```
