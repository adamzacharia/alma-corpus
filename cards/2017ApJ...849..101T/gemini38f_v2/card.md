# A Detached Protostellar Disk around a ∼0.2 M <SUB>☉</SUB> Protostar in a Possible Site of a Multiple Star Formation in a Dynamical Environment in Taurus

`2017ApJ...849..101T` | The Astrophysical Journal 2017 | first author: Tokuda, Kazuki | arXiv: 1709.07113 | DOI: 10.3847/1538-4357/aa8e9e | **HELD OUT (benchmark)**

Card schema 1.0 | model gemini-3.8-flash | depth full | type observational_alma_primary

## Science

- Fields: star_formation, protoplanetary_disks
- Question: What are the kinematic and physical properties of the disk and central protostar in the very low-luminosity object MMS-1 in MC27/L1521F?  
  > "In particular, the evolutionally status of the very low-luminosity protostar is still unclear, possibly due to insufficient spatial resolutions." (Introduction)
- Target **MC27/L1521F (MMS-1 / L1521F-IRS)**: coordinates 04h28m38.96s +26d51m35.0s  
  > "We carried out ALMA Cycle 3 Band 7 (0.87 mm) continuum and molecular line observations toward MC27/L1521F with a center position of (\alpha_{J2000.0}, \delta_{J2000.0}) = (4^h28^m38.96s, +26^\circ51''35.0'')" (Observations); "at a distance of Taurus (cite: Elias78)." (Observations); z/distance 140 pc  
  > "We carried out ALMA Cycle 3 Band 7 (0.87 mm) continuum and molecular line observations toward MC27/L1521F with a center position of (\alpha_{J2000.0}, \delta_{J2000.0}) = (4^h28^m38.96s, +26^\circ51''35.0'')" (Observations); "at a distance of Taurus (cite: Elias78)." (Observations); distance from (cite: Elias78)  
  > "We carried out ALMA Cycle 3 Band 7 (0.87 mm) continuum and molecular line observations toward MC27/L1521F with a center position of (\alpha_{J2000.0}, \delta_{J2000.0}) = (4^h28^m38.96s, +26^\circ51''35.0'')" (Observations); "at a distance of Taurus (cite: Elias78)." (Observations)

## Data provenance

- ALMA projects: 2015.1.00340.S
- bands: Band 7 (0.87 mm)  
  > "We carried out ALMA Cycle 3 Band 7 (0.87 mm) continuum and molecular line observations toward MC27/L1521F" (Observations)
- frequencies and spectral setup: Four spectral windows, each 1875 MHz wide (aggregate bandwidth 7.5 GHz): two in FDM (0.9765 MHz resolution, 1920 channels, velocity resolution ~0.85 km/s) and two in TDM (128 channels)  
  > "There were four spectral windows and the correlator was set to have a band width of 1875 MHz. Two of them have a frequency resolution of 0.9765 MHz (1920 channels), corresponding to the velocity resolution of ~0.85 km s^{-1} with the frequency domain mode (FDM). The rest was set to the time domain mode (TDM) with 128 channels. The aggregate bandwidth is thus 7.5 GHz." (Observations)
- continuum bandwidth: 7.5 GHz  
  > "The aggregate bandwidth is thus 7.5 GHz." (Observations)
- arrays: ALMA 12 m array  
  > "observations toward MC27/L1521F with a center position of (\alpha_{J2000.0}, \delta_{J2000.0}) = (4^h28^m38.96s, +26^\circ51''35.0'') with the ALMA 12 m array." (Observations)
- configurations: C40-6  
  > "and then we simulated the ALMA observations in ^{12}CO (J = 3–2) and 0.87 mm continuum with the C40-6 configuration, which is the same as in our present observations" (Physical quantities of disk of MMS-1)
- baselines: 15-2800 klambda  
  > "The UV range is 15-2800 k\lambda." (Observations)
- angular resolution: ~0.18" x 0.1"  
  > "The synthesized beam is ~0.18'' \times 0.1'' = 25 au \times 14 au at a distance of Taurus (cite: Elias78)." (Observations)
- max recoverable scale: _not stated_
- sensitivity: 1.6 mJy/beam at ~0.85 km/s resolution (12CO 3-2); ~35 muJy/beam (0.87 mm continuum)  
  > "The (1\sigma) rms of molecular line emission, ^{12}CO (J = 3–2) and the 0.87 mm continuum are ~1.6 mJy beam^{-1} at a velocity resolution of ~0.85 km s^{-1} and ~35 \mu Jy beam^{-1}, respectively." (Observations)
- time on source: _not stated_
- observing dates: September 2016  
  > "The observations were carried out in September 2016." (Observations)
- pi or archival as stated: _not stated_
- Line: 12CO J = 3-2 (not stated)
- Line: H13CO+ J = 4-3 (not stated)
- Line: C17O J = 3-2 (not stated)
- Other facility **Spitzer Space Telescope**: Mid-IR scattered light nebula imaging, giving disk inclination (70 deg) and bolometric luminosity constraint (<0.07 L_sun)  
  > "We also adopted the inclination angle = 70^\circ derived from the scattered light seen in the Spitzer (cite: Terebey09)" (Physical quantities of disk of MMS-1); "it contains a VeLLO (L1521F-IRS) at the center of the core with the luminosity of <0.07 L_{\odot} (cite: Bourke06; Terebey09)" (Introduction)
- External data: Distance to Taurus (~140 pc assumed implicitly from ~0.18'' x 0.1'' = 25 au x 14 au)  
  > "at a distance of Taurus (cite: Elias78)." (Observations) [from (cite: Elias78)]
- External data: Spitzer luminosity <0.07 L_sun and disk inclination angle i = 70 deg  
  > "it contains a VeLLO (L1521F-IRS) at the center of the core with the luminosity of <0.07 L_{\odot} (cite: Bourke06; Terebey09)" (Introduction); "We also adopted the inclination angle = 70^\circ derived from the scattered light seen in the Spitzer (cite: Terebey09)" (Physical quantities of disk of MMS-1) [from (cite: Bourke06; Terebey09)]
- External data: Dust opacity kappa_345GHz = 1.2 x 10^-2 cm^2 g^-1  
  > "the dust opacity per unit (gas + dust) mass column density, \kappa_{345 GHz} = 1.2 \times 10^{-2} cm^2 g^{-1} ((cite: Hildebrand83; Oss94; Kauffmann08); Paper I)" (Gas/dust distributions toward MMS-1) [from (cite: Hildebrand83; Oss94; Kauffmann08)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: 4.7.2  
  > "The data were processed with the CASA (Common Astronomy Software Application) package (cite: McMullin07) version 4.7.2." (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0510+1800  
  > "The calibrations of the complex gains and the flux were carried out through observations of a quasar, J0510+1800, and the phase calibrations were performed using J0433+2905." (Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "We used the briggs weighting with the robust parameter of 0.5." (Observations)
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
- final beam: ~0.18" x 0.1"  
  > "The synthesized beam is ~0.18'' \times 0.1'' = 25 au \times 14 au at a distance of Taurus (cite: Elias78)." (Observations)
- final rms: 1.6 mJy/beam for 12CO (J = 3-2) at 0.85 km/s; 35 muJy/beam for 0.87 mm continuum  
  > "The (1\sigma) rms of molecular line emission, ^{12}CO (J = 3–2) and the 0.87 mm continuum are ~1.6 mJy beam^{-1} at a velocity resolution of ~0.85 km s^{-1} and ~35 \mu Jy beam^{-1}, respectively." (Observations)

### Inherited from earlier work

- Fitting model parameters to velocity-versus-projected-distance peak position curves  
  > "Based on the plots of the relative velocities to the systemic velocity with respect to the projected distances from the 0.87 mm continuum peak in MMS-1, the parameters of the model were adjusted to match the observations (Figure 3). Similar data analysis was carried out in (cite: Tobin12)." (Physical quantities of disk of MMS-1) [from (cite: Tobin12)]
- LTE radiative transfer calculation method for rotating disk models  
  > "Expected line emissions along lines of sight were calculated with radiative transfer equations, assuming the local thermal equilibrium (cite: Ohashi14)" (Physical quantities of disk of MMS-1) [from (cite: Ohashi14)]
- Numerical stellar evolution code for cold accretion  
  > "We calculated the evolution of the stellar luminosity with the cold accretion by using the numerical code described by (cite: Hosokawa09) and (cite: Hosokawa10; Hosokawa11)." (A very low-luminosity object as a candidate evolved by cold accretion) [from (cite: Hosokawa09; Hosokawa10; Hosokawa11)]

### Not stated but needed to reproduce (our reading)

- CASA clean/tclean parameter values (cell size, imsize, niter, threshold, multiscale)
- Continuum subtraction procedure / line-free channels
- Total on-source integration time

## Analysis recipe

1. **Deconvolve continuum source MMS-1 and derive mass and column density**: Image plane deconvolution using synthesized beam PSF  
  > "We deconvolved the source in the image plane by using the point spread function (PSF) of the synthesized beam." (Gas/dust distributions toward MMS-1)
   - parameter: Peak flux = 2.8 mJy/beam, total flux = 3.6 mJy  
  > "The peak flux and the total flux are 2.8 mJy beam^{-1} and 3.6 mJy, respectively" (Gas/dust distributions toward MMS-1)
   - assumption: Optically thin emission, uniform dust temperature T_dust = 100 K, kappa_345GHz = 1.2 x 10^-2 cm^2 g^-1, gas-to-dust ratio = 100  
  > "with the assumptions of the optically thin emission, the uniform dust temperature of 100 K, and the dust opacity per unit (gas + dust) mass column density, \kappa_{345 GHz} = 1.2 \times 10^{-2} cm^2 g^{-1}" (Gas/dust distributions toward MMS-1); "gas-to-dust ratio is assumed to be 100." (Gas/dust distributions toward MMS-1)
   - fitting: Image plane 2D Gaussian deconvolution with synthesized beam PSF  
  > "We deconvolved the source in the image plane by using the point spread function (PSF) of the synthesized beam." (Gas/dust distributions toward MMS-1)
   - validation: _not stated_
2. **Model rotating disk and derive stellar dynamical mass and disk parameters**: Radiative transfer modeling under LTE followed by synthetic ALMA observations using simobserve and simanalyze  
  > "Expected line emissions along lines of sight were calculated with radiative transfer equations, assuming the local thermal equilibrium (cite: Ohashi14), and then we simulated the ALMA observations in ^{12}CO (J = 3–2) and 0.87 mm continuum with the C40-6 configuration" (Physical quantities of disk of MMS-1)
   - software: CASA
   - parameter: M_* = 0.18 M_sun, R_disk = 9 au, M_disk = 8 x 10^-5 M_sun, T_1au = 180 K  
  > "The derived optimum values of the Keplerian disk model are M_{*} = 0.18 M_{\odot}, R_{disk} = 9 AU, M_{disk} = 8 \times 10^{-5} M_{\odot} and T_{1au} = 180 K." (Physical quantities of disk of MMS-1)
   - assumption: Keplerian rotation disk, temperature profile proportional to r^-0.5, density profile proportional to r^-1, LTE, V_sys = 6.75 km/s, inclination = 70 deg, position angle = -17 deg  
  > "In the present study, we assume a Keplerian rotation, as the simplest modeling approach, to estimate the mass of the protostar and the disk properties. The temperature and density profiles of the simulated models are assumed to be \propto r^{-0.5} and \propto r^{-1}." (Physical quantities of disk of MMS-1); "We adopted the V_{sys} = 6.75 km s^{-1}" (Physical quantities of disk of MMS-1); "We also adopted the inclination angle = 70^\circ derived from the scattered light seen in the Spitzer (cite: Terebey09), and the position angle = -17^\circ" (Physical quantities of disk of MMS-1)
   - fitting: Three-step iterative tuning: 2D Gaussian fitting in velocity channels matched against synthetic observations, fitting T_1au to high-velocity spectral intensity, and adjusting M_disk to continuum flux  
  > "We derived the optimum values with the following three steps. (1) The peak positions of the ^{12}CO (J = 3–2) in each channel (Figure 2) with both the ALMA observations and the synthetic observations of Keplerian models are derived by 2D Gaussian fitting." (Physical quantities of disk of MMS-1); "(2) We then fitted the T_{1au} to reproduce the intensity of the spectrum at high-velocity parts." (Physical quantities of disk of MMS-1); "(3) The remaining parameter, M_{disk}, was calculated to reproduce the observed 0.87 mm continuum flux by assuming the temperature distribution derived in step (2)." (Physical quantities of disk of MMS-1)
   - validation: Comparison with observed channel maps, position-velocity diagram, and mirrored spectrum  
  > "Our observation and model agree reasonably well (see also the channel maps in Figure 2 and the P-V diagram in Figure 4)." (Physical quantities of disk of MMS-1)
3. **Model pre-main-sequence luminosity evolution under cold accretion**: Stellar evolution simulation code with cold accretion  
  > "We calculated the evolution of the stellar luminosity with the cold accretion by using the numerical code described by (cite: Hosokawa09) and (cite: Hosokawa10; Hosokawa11)." (A very low-luminosity object as a candidate evolved by cold accretion)
   - parameter: Initial radius ~0.65 R_sun  
  > "initial radius of the protostar (~0.65 R_\odot)" (A very low-luminosity object as a candidate evolved by cold accretion)
   - assumption: Cold accretion with fixed accretion rate 10^-5 M_sun/yr up to 0.2 M_sun, initial mass 0.01 M_sun, initial radius 0.65 R_sun  
  > "We used a fixed accretion rate of 10^{-5} M_{\odot} yr^{-1} until the star has reached the mass of 0.2 M_{\odot}, and then we stopped the accretion and tracked the evolution of pre-main-sequence star." (A very low-luminosity object as a candidate evolved by cold accretion); "Our calculation starting with a 0.01 M_{\odot} star with the initial radius of 0.65 R_{\odot} reproduces the observed luminosity (~0.07 L_{\odot}) in <10^5 years after we stop the mass accretion." (A very low-luminosity object as a candidate evolved by cold accretion)
   - fitting: _not stated_
   - validation: Comparison to observed luminosity ~0.07 L_sun  
  > "reproduces the observed luminosity (~0.07 M_{\odot}) in <10^5 years after we stop the mass accretion." (A very low-luminosity object as a candidate evolved by cold accretion)

## Software

- **CASA** 4.7.2: Data calibration, imaging, and simulation of synthetic ALMA observations with simobserve and simanalyze  
  > "The data were processed with the CASA (Common Astronomy Software Application) package (cite: McMullin07) version 4.7.2." (Observations); "using tasks ``simobserve'' and ``simanalyze'' in CASA." (Physical quantities of disk of MMS-1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Deconvolved major axis size of MMS-1 | 91.1 | 10.1 | mas | 1 | The deconvolved size of MMS-1 is (91.1\pm10.1 mas)\times(55.8\pm4.2 mas), corresponding to (12.9\pm1.4 au)\times(7.8\pm0.6 au). |
| Deconvolved minor axis size of MMS-1 | 55.8 | 4.2 | mas | 1 | The deconvolved size of MMS-1 is (91.1\pm10.1 mas)\times(55.8\pm4.2 mas), corresponding to (12.9\pm1.4 au)\times(7.8\pm0.6 au). |
| 0.87 mm continuum peak flux density of MMS-1 | 2.8 | not stated | mJy beam^-1 | 1 | The peak flux and the total flux are 2.8 mJy beam^{-1} and 3.6 mJy, respectively |
| 0.87 mm continuum total flux density of MMS-1 | 3.6 | not stated | mJy | 1 | The peak flux and the total flux are 2.8 mJy beam^{-1} and 3.6 mJy, respectively |
| Peak H2 column density of MMS-1 | 3.1 x 10^23 | not stated | cm^-2 | 1 | corresponding to the peak H_2 column density and the total mass of 3.1 \times 10^{23} cm^{-2} and 8.3 \times 10^{-5} M_{\odot} |
| Total mass of MMS-1 from continuum | 8.3 x 10^-5 | not stated | M_\odot | 1 | corresponding to the peak H_2 column density and the total mass of 3.1 \times 10^{23} cm^{-2} and 8.3 \times 10^{-5} M_{\odot} |
| Position angle of the disk | -17 | not stated | deg | 2 | A position angle of the line passing through the emission peaks in each velocity channel is -17^\circ |
| Central stellar dynamical mass M_* | 0.18 | +/-0.05 | M_\odot | 2 | The derived optimum values of the Keplerian disk model are M_{*} = 0.18 M_{\odot}, R_{disk} = 9 AU, M_{disk} = 8 \times 10^{-5} M_{\odot} and T_{1au} = 180 K. |
| Keplerian disk radius R_disk | 9 | not stated | AU | 2 | The derived optimum values of the Keplerian disk model are M_{*} = 0.18 M_{\odot}, R_{disk} = 9 AU, M_{disk} = 8 \times 10^{-5} M_{\odot} and T_{1au} = 180 K. |
| Keplerian disk mass M_disk | 8 x 10^-5 | not stated | M_\odot | 2 | The derived optimum values of the Keplerian disk model are M_{*} = 0.18 M_{\odot}, R_{disk} = 9 AU, M_{disk} = 8 \times 10^{-5} M_{\odot} and T_{1au} = 180 K. |
| Kinematic temperature at 1 au T_1au | 180 | not stated | K | 2 | The derived optimum values of the Keplerian disk model are M_{*} = 0.18 M_{\odot}, R_{disk} = 9 AU, M_{disk} = 8 \times 10^{-5} M_{\odot} and T_{1au} = 180 K. |
| Mass accretion rate upper limit | < 2 x 10^-8 | not stated | M_\odot yr^-1 | 0 | the mass accretion rate is estimated to be quite low as < 2 \times 10^{-8} M_{\odot} yr^{-1} with the assumption of a stellar radius of 1.5 R_{\odot}. |

## Qualitative findings

- Clear detection of blueshifted and redshifted 12CO (J = 3-2) emission associated with MMS-1  
  > "We have clearly detected the blueshifted and redshifted emission of the ^{12}CO (J = 3–2) at MMS-1 (Figure 1 (a,b)) for the first time at the present high-angular resolution." (Gas/dust distributions toward MMS-1)
- Non-detection of dense gas tracers H13CO+ and C17O toward MMS-1, indicating absence of connecting high-density envelope  
  > "It is to be noted that we cannot detect high-density tracers, H^{13}CO^{+} (J = 3–2) and C^{17}O (J = 3–2), toward MMS-1 even with the higher angular resolution compared with Paper II." (Gas/dust distributions toward MMS-1)
- The compact and detached disk suggests mass accretion onto the protostar/disk may have halted recently  
  > "The observed disk in MMS-1 is very small, indicating that further significant mass accretion through the disk does not occur anymore. Thus, we may be witnessing a stage close to the moment when the accretion activity has been halting." (A detached disk at the center of an isolated protostellar core)

## Claim tuples

- H: Does the very low-luminosity protostar in MC27/L1521F have a rotating circumstellar disk and what is the mass of the central object? | E: High-angular resolution (~0.18" x 0.10") ALMA Band 7 continuum and 12CO (J = 3-2) observations of MMS-1 in MC27/L1521F compared with synthetic Keplerian disk models | R: Detected compact 12CO velocity gradient with highest velocity ~7 km/s at ~2 au, fitted by Keplerian disk model with M_* = 0.18 +/- 0.05 M_sun, R_disk = 9 au, and M_disk = 8 x 10^-5 M_sun | F: The VeLLO MMS-1 hosts a compact rotating Keplerian disk with a central protostellar mass of ~0.2 M_sun and disk mass of ~10^-4 M_sun | **supported**
- H: Is the protostellar disk actively fed by an extended connecting dense envelope? | E: High-resolution imaging of high-density molecular tracers H13CO+ (J=4-3) and C17O (J=3-2) and dust continuum around MMS-1 | R: No high-density line emission detected toward MMS-1, and no extended high-density envelope connecting to the disk in 0.87 mm continuum | F: The disk appears detached from the surrounding envelope, potentially truncated by turbulent dynamical interactions in the core | **supported**
- H: Can the extremely low luminosity (<0.1 L_sun) of a ~0.2 M_sun protostar be reconciled with stellar evolution models? | E: Pre-main-sequence evolutionary calculation with cold accretion starting from a 0.01 M_sun core | R: Standard pre-main-sequence tracks require >1 Myr to reach <0.1 L_sun, whereas cold accretion models reproduce ~0.07 L_sun within <10^5 yr with R_init ~ 0.65 R_sun | F: The low luminosity of ~0.07 L_sun for a ~0.2 M_sun protostar can be matched within <10^5 yr if accretion occurred via cold accretion with an unusually small initial stellar radius (~0.65 R_sun) | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Synthetic ALMA observations of Keplerian disk models with CASA simobserve and simanalyze were needed to deconvolve beam dilution effects on unresolved/marginally resolved disk kinematics  
  > "since the present ALMA observations do not have a sufficient resolution to spatially resolve the disk structure, the comparisons with the simulation of rotating disks are needed to remove the effect of the beam dilution." (Physical quantities of disk of MMS-1)
- Alternative: Standard pre-main-sequence evolutionary tracks cannot explain the observed low luminosity (<0.1 L_sun) for a ~0.2 M_sun protostar within dense core timescales  
  > "According to the classical evolutionary tracks of pre-main-sequence stars (cite: Baraffe98), it takes >1 Myr for a ~0.2 M_{\odot} protostar to reach a luminosity of <0.1 L_{\odot}." (A very low-luminosity object as a candidate evolved by cold accretion)
- How they decided it was enough: _not stated_
- Limitation (authors): Disk structure is not fully spatially resolved at ~20 au resolution, requiring simulation comparisons to correct for beam dilution  
  > "since the present ALMA observations do not have a sufficient resolution to spatially resolve the disk structure, the comparisons with the simulation of rotating disks are needed to remove the effect of the beam dilution." (Physical quantities of disk of MMS-1)
- Limitation (authors): Models include only the disk and not the surrounding dense core envelope or absorption  
  > "We note that we simulated only the disk component, although the source is heavily embedded in a dense core. This difference is seen in the spectrum mainly around the systemic velocity (4.45–9.55 km s^{-1}); the dense core is observed in this velocity range." (Physical quantities of disk of MMS-1)
- Caveat (inferred, ours): The disk is only marginally resolved, so derived stellar mass and radius depend heavily on the adopted Keplerian thin disk geometry and fixed inclination.
- Caveat (inferred, ours): Forefront core absorption obscures the line profile near systemic velocity, limiting constraints to the high-velocity wings.

## Reproducibility

- Data public (paper): ADS/JAO.ALMA#2015.1.00340.S  
  > "This paper makes use of the following ALMA data: ADS/ JAO.ALMA#2015.1.00340.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Specific CASA cleaning parameters (niter, threshold, cell size, image size, mask details)
- Missing: Continuum subtraction method details
- Missing: Exact command lines or script for simobserve / simanalyze parameter exploration
- Data volume (inferred): 10 - 30 GB
- Score (inferred): 8/5, High quality ALMA paper with explicit project code, calibrators, beam, noise levels, and modeled parameter values. Forward modeling with CASA simobserve is detailed, though some fine clean parameters and script details are omitted.
- Rediscovery candidate: yes, ALMA Cycle 3 Band 7 dataset is public under project 2015.1.00340.S; the continuum measurement, 2D deconvolution, and forward-modeling procedure with CASA simobserve are fully described with clear target numeric values.

## Links

- Method: (cite: McMullin07) (CASA software package reference)
- Method: (cite: Ohashi14) (Radiative transfer modeling method for rotating circumstellar disk under LTE)
- Method: (cite: Hosokawa09) (Numerical code for stellar evolution under accretion)
- Companion: (cite: Tokuda14) (Paper I: ALMA Cycle 0 observations of MC27/L1521F)
- Companion: (cite: Tokuda16) (Paper II: ALMA Cycle 1 observations of MC27/L1521F)

## Checks

```json
{
 "quotes": 79,
 "quotes_ok": 78,
 "quote_pass_rate": 0.987,
 "quotes_too_long": 6,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 47,
  "rate": 0.653
 },
 "evidence_ok": false
}
```
