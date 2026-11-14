# Tidal Distortion of the Envelope of an AGB Star IRS 3 near Sgr A*

`2017ApJ...837...93Y` | The Astrophysical Journal 2017 | first author: Yusef-Zadeh, F. | arXiv: 1702.02196 | DOI: 10.3847/1538-4357/aa5ea2

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: milky_way_ism, stellar_physics, evolved_stars
- Question: Is the dusty envelope of the AGB star IRS 3 near Sgr A* tidally distorted, and what does this imply for IRS 3's line-of-sight distance and gas supply near Sgr A*?  
  > "show that the dusty outer shell of IRS 3 located $4.5''$ NW of Sgr A\* (projected distance $\sim$0.18 pc at the Galactic center distance 8 kpc) is being tidally stretched by Sgr A\*." (Introduction)
- Target **IRS 3 (near Sgr A*)**: coordinates RA 17h45m39.864s, Dec -29d00m24.257s (226 GHz, Table 1)  
  > "projected distance $\sim$0.18 pc at the Galactic center distance 8 kpc" (Introduction); z/distance 8 kpc (Galactic center)  
  > "projected distance $\sim$0.18 pc at the Galactic center distance 8 kpc" (Introduction); distance from adopted Galactic center distance  
  > "projected distance $\sim$0.18 pc at the Galactic center distance 8 kpc" (Introduction)

## Data provenance

- ALMA projects: 2015.A.00021.S
- bands: _not stated_
- frequencies and spectral setup: two spectral windows centered on 218.3 and 238.0 GHz, each 1.87 GHz wide  
  > "The ALMA 230 GHz data consisted of two spectral windows centered on 218.3 and 238.0 GHz, each 1.87 GHz wide." (Observation and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.36'' x 0.25'' (July 12)  
  > "The July 12 data with a spatial resolution of $0.36''\times0.25''$ are presented here." (Observation and Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2016 July 12 and July 18 (July 12 used)  
  > "Observations were obtained on 2016, July 12 and July 18." (Observation and Data Reduction)
- pi or archival as stated: ALMA project 2015.A.00021.S, PI Gunther Witzel  
  > "2015.A.00021.S (Principal Investigator Gunther Witzel)" (Acknowledgments)
- Other facility **VLA**: 44 GHz and 15 GHz continuum images (A configuration)  
  > "We also present radio data at 44 GHz and 15 GHz data taken with the VLA in its A configuration." (Observation and Data Reduction)
- External data: 350 GHz peak flux density of IRS 3 and CS (5-4)/SiO (6-4) emission distribution and velocities  
  > "Using the peak flux density of IRS 3 at 350 GHz given by Moser et al. (2016)" (Results) [from Moser et al. 2016 (cite: 2016arXiv160300801M)]
- External data: IRS 3 position and proper motion relative to Sgr A*  
  > "$\Delta RA = -2\dasec341 \pm 0\dasec009$, $\Delta Dec = 3\dasec848 +- 0\dasec016$" (Discussion) [from Schödel et al. 2009 (cite: 2009A&A...502...91S)]
- External data: Mass-loss rate of IRS 3 from photospheric modeling  
  > "Based on photospheric modeling, Pott et al. (2008) estimate $\dot{M}\sim 6\times10^{-5}$  yr$^{-1}$." (Discussion) [from Pott et al. 2008 (cite: 2008A&A...487..413P)]
- External data: Near-IR extinction map and 3.8 micron image  
  > "(Schödel et al. 2010), coincident with the CS (5-4) emission." (Results) [from Schödel et al. 2010 (cite: 2010A&A...511A..18S)]

## Processing

### Calibration

- pipeline or manual: Manual calibration and editing in OBIT with phase self-cal then amp+phase  
  > "The editing and calibration of the data was carried out using OBIT (Cotton 2008)" (Observation and Data Reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: 1744-3116 with assumed 0.26 Jy at 234 GHz; bandpass J1924-2914  
  > "Initial amplitude and phase calibration was based on 1744-3116 with an assumed flux density of 0.26 Jy at 234 GHz." (Observation and Data Reduction)
- flux scale uncertainty: _not stated_
- self calibration: Phase self-cal followed by amplitude and phase calibration  
  > "Phase self calibration followed by amplitude and phase calibration were applied." (Observation and Data Reduction)

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
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- 44 GHz VLA observation details  
  > "Details of these narrow band observations are given in Yusef-Zadeh et al. (2013)." (Observation and Data Reduction) [from Yusef-Zadeh et al. (2013) (cite: 2013ApJ...767L..32Y)]
- 15 GHz data reduction and setup  
  > "Data reduction and observing setup were identical to that described at 8 GHz in Table 1 of Yusef-Zadeh et al. (2016)." (Observation and Data Reduction) [from Yusef-Zadeh et al. (2016) (cite: 2016ApJ...819...60Y)]

### Not stated but needed to reproduce (our reading)

- Imaging task, weighting/robust, cell and image size, masking, deconvolver
- Software/version used to image the OBIT-calibrated data
- Gaussian fit method details and background subtraction
- Why July 18 data not used and how epochs compared
- Exact RADEX inputs beyond those stated (line width, background)
- Clump model details yielding 16 clumps
- Ballistic orbit integration code and initial conditions

## Analysis recipe

1. **Measure IRS 3 radio-mm flux and spectral index**: Background-subtracted 2D Gaussian fits to IRS 3 at each frequency; spectral index from flux densities  
  > "The intensities are estimated from background subtracted 2D Gaussian fits to IRS 3." (Results)
   - fitting: _not stated_
   - validation: _not stated_
2. **Estimate envelope gas mass from CS (5-4)**: RADEX non-LTE estimate of n_H N_CS, then density and mass with a clumpy envelope  
  > "We used the online version of RADEX (Van der Tak et al. 2007) to estimate the density and column of the emitting molecular gas." (Discussion)
   - software: RADEX
   - parameter: kinetic temperature 300 K; FWHM 40 km/s; L = 0.2 pc  
  > "Adopting a kinetic temperature of 300 K, consistent with the proximity to hot stars in the central parsec, and a 40 km s$^{-1}$  FHWM" (Discussion)
   - assumption: CS abundance relative to H x_CS = 5e-7  
  > "We assume that the CS abundance relative to H to be $x_\mathrm{CS}= 5\times10^{-7}$" (Discussion)
   - fitting: _not stated_
   - validation: Predicted ~90 uJy per beam at 226 GHz with dust at 100 K compared with the observed mm enhancement  
  > "Adopting a dust temperature of 100 K in the envelope implies an average thermal continuum $\sim90\, \mu$Jy per $0.39''\times0.38''$ beam at 226 GHz" (Discussion)
3. **Model tidal distortion by ballistic fluid elements**: Fluid elements launched radially from IRS 3 follow Keplerian orbits around Sgr A*; vary line-of-sight z and compare shell shape  
  > "we model it as a set of fluid elements that are launched radially outwards from IRS 3 as it orbits Sgr A\* and subsequently follow their ballistic trajectories" (Discussion)
   - parameter: v_z = +50 km/s; wind 20 km/s; ejection 2500, 5000, 7500 yr ago  
  > "We adopt $+50$  km s$^{-1}$  as the line-of-sight velocity, representative of the mean velocity of the CS emission" (Discussion)
   - assumption: Sgr A* mass 4e6 Msun, distance 8 kpc  
  > "We adopt $4\times10^6\msol$ and 8 kpc as the mass and distance of Sgr A\*" (Discussion)
   - fitting: _not stated_
   - validation: Qualitative comparison of the 5000 yr shell with the CS envelope extent across z values  
  > "The blue shell should correspond to the extent of the CS envelope, which has an estimated flow time $\sim5\,000$  yrs." (Discussion)

## Software

- **OBIT** : editing and calibration of ALMA data  
  > "The editing and calibration of the data was carried out using OBIT (Cotton 2008)" (Observation and Data Reduction)
- **RADEX** online version: density and column of CS emitting gas  
  > "We used the online version of RADEX (Van der Tak et al. 2007)" (Discussion)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Spectral index 44-226 GHz | 1.85 | 1.13 | dimensionless | 1 | between 44 and 226 GHz as well as between 34 and 44 GHz give values 1.85$\pm1.13$ and 1.32$\pm0.32$ |
| Spectral index 34-44 GHz | 1.32 | 0.32 | dimensionless | 1 | between 44 and 226 GHz as well as between 34 and 44 GHz give values 1.85$\pm1.13$ and 1.32$\pm0.32$ |
| Spectral index 226-350 GHz | 1.17 | 0.33 | dimensionless | 1 | we find the spectral index is $\alpha=1.17\pm0.33$ between 226 and 350 GHz |
| Envelope mass (smooth) | 1.4 | not stated | Msun | 2 | This implies an uncomfortably large envelope mass $M_\mathrm{env}\approx 1.4\msol$ |
| Envelope mass (clumpy, 5% filling) | 0.3 | not stated | Msun | 2 | giving $M_\mathrm{env}=0.3 \msol$ with most mass residing in clumps with 5% filling factor |
| IRS 3 line-of-sight position | ~0.7 pc in front of or ~0.5 pc behind Sgr A* | not stated | pc | 3 | constrains the distance of IRS 3 to $\sim$0.7 pc in front of or $\sim$0.5 pc behind Sgr A\* |

## Qualitative findings

- Two semicircular mm dust shells facing Sgr A*, outer shell breaking into fingers coincident with CS (5-4) emission and an extinction cloud  
  > "consists of two semi-circular dust shells facing the direction of Sgr A\*." (abstract)

## Claim tuples

- H: IRS 3 is an AGB star rather than a young mass-losing star | E: Radio-to-mm spectral index of IRS 3 | R: alpha 1.85±1.13 (44-226 GHz) and 1.17±0.33 (226-350 GHz) | F: Optically thick, more consistent with an evolved star photosphere, but a young star cannot be ruled out | **partially**
- H: The IRS 3 envelope is tidally distorted by Sgr A* | E: Ballistic model of ejected fluid elements for various line-of-sight distances | R: Shell shape matches only for z ~ -0.7 pc or +0.5 pc | F: IRS 3 lies ~0.7 pc in front of or ~0.5 pc behind Sgr A* | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Asymmetric outflow as in post-AGB stars; external winds (bow shock) judged unlikely  
  > "Thus, it seems unlikely that the the NE-SW structure of IRS 3 at 3.8$\mu$m is produced by external winds." (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Orbit not determined a priori; line-of-sight velocity and position unknown  
  > "The orbit of IRS 3 is not completely determined a-priori because its line-of-sight velocity and location within the inner parsec along the line of sight are unknown" (Discussion)
- Caveat (inferred, ours): Tidal model is qualitative, with shell-shape matching by eye and no fit
- Caveat (inferred, ours): Large spectral index uncertainty
- Caveat (inferred, ours): Amplitude self-calibration may bias faint extended structure
- Caveat (inferred, ours): Dark features may be interferometric artifacts
- Caveat (inferred, ours): Only one ALMA epoch used for imaging

## Reproducibility

- Data public (paper): ALMA project 2015.A.00021.S cited; public status not stated  
  > "This paper makes use of the following ALMA data: 2015.A.00021.S (Principal Investigator Gunther Witzel)" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: OBIT scripts
- Missing: Orbit integration code
- Missing: Exact fit regions and fluxes for substructures
- Data volume (inferred): tens of GB
- Score (inferred): 3/5, Data identified but imaging and modeling details are sparse.
- Rediscovery candidate: no, Imaging recipe incomplete and the main result relies on a qualitative model.

## Links

- Method: Cotton 2008, PASP 120, 439 (OBIT calibration software)
- Companion: Yusef-Zadeh et al. 2016 (cite: 2016ApJ...819...60Y) (VLA data setup and 34/44 GHz measurements)
- Companion: Moser et al. 2016 (cite: 2016arXiv160300801M) (CS and SiO ALMA line data and 350 GHz flux)

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
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 33,
  "rate": 0.485
 },
 "evidence_ok": true
}
```
