# Optical, Near-IR, and Sub-mm IFU Observations of the Nearby Dual Active Galactic Nuclei MRK 463

`2018ApJ...854...83T` | The Astrophysical Journal 2018 | first author: Treister, Ezequiel | arXiv: 1801.06190 | DOI: 10.3847/1538-4357/aaa963

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type multi_facility_alma_minor

## Science

- Fields: agn_and_quasars, nearby_galaxies
- Question: Study the morphology and kinematics of ionized, atomic and molecular gas in the dual AGN Mrk 463 to understand gas feeding the SMBHs and star formation during a major merger  
  > "The main goal is to study the morphology and kinematics of the gas in all its phases using atomic and molecular emission lines as tracers" (Introduction)
- Target **Mrk 463**: coordinates _not stated_; z/distance z=0.0504, d~210 Mpc  
  > "Mrk 463 is a nearby, $z$=0.0504 (cite: falco99) or $d$$\simeq$210Mpc" (Introduction); distance from Falco et al. 1999 redshift  
  > "Mrk 463 is a nearby, $z$=0.0504 (cite: falco99) or $d$$\simeq$210Mpc" (Introduction)

## Data provenance

- ALMA projects: 2013.1.00525.S
- bands: Band 6  
  > "in band 6 as part of program 2013.1.00525.S (PI: E. Treister)" (2.3 ALMA)
- frequencies and spectral setup: 4 spws: one 12CO(2-1) (10.7 km/s resolution, 2560 km/s bandwidth), three continuum at ~220-235 GHz  
  > "one covering the $^{12}$CO(2-1) molecular transition, providing a 10.7 km/s spectral resolution and a 2560 km/s bandwidth and the remaining three covering the mm continuum at $\sim$220-235 GHz" (2.3 ALMA)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 43 m to 1.57 km (Aug 16); 41 m to 4.5 km (Sep 16); 34 antennae  
  > "34 antennae were used with baselines ranging from 43 m to 1.57 km, while on September 16th the same number of antennae were used distributed between 41 m and 4.5 km baselines" (2.3 ALMA)
- angular resolution: 0.3'' x 0.17'' beam (natural weighting)  
  > "The resulting beam size is 0.3$''$$\times$0.17$''$." (2.3 ALMA)
- max recoverable scale: _not stated_
- sensitivity: ~0.6 mJy/beam (3-sigma) in CO(2-1) per ~10.7 km/s channel  
  > "we achieved a sensitivity of $\sim$0.6 mJy/beam at 3-$\sigma$ in the $^{12}$CO(2-1) line" (2.3 ALMA)
- time on source: 25.7 minutes per observation  
  > "The total on-target time in each observation was 25.7 minutes." (2.3 ALMA)
- observing dates: August 16, 2015 and September 16, 2015  
  > "The observations of Mrk 463 were taken on August 16, 2015 between 22:27 and 23:27 UT" (2.3 ALMA)
- pi or archival as stated: Own Cycle 2 program (PI Treister)  
  > "During ALMA Cycle 2, we were granted 5.1 hours of priority B time to observe a sample of four nearby dual AGN" (2.3 ALMA)
- Line: 12CO J=2-1 (not stated)
- Other facility **VLT/MUSE**: Optical IFU cube of full system (program 095.B-0482)  
  > "Mrk 463 was observed by the VLT/MUSE as part of program 095.B-0482 (PI: E. Treister)." (2.1 MUSE)
- Other facility **VLT/SINFONI**: K-band IFU of central 8''x8'' (program 093.B-0513)  
  > "as part of program 093.B-0513 (PI: S. Cales)" (2.2 SINFONI)
- Other facility **Chandra**: X-ray AGN positions, luminosities and NH from Bianchi et al. 2008  
  > "It was classified as a dual AGN based on *Chandra* X-ray observations reported by (cite: bianchi08)." (Introduction)
- External data: Chandra 2-10 keV luminosities, NH and accretion rate of both nuclei  
  > "relatively low X-ray luminosities of $L_{\rm X}$=1.5$\times$10$^{43}$ erg/s and 3.8$\times$10$^{42}$ erg/s in the 2-10 keV band" (Introduction) [from (cite: bianchi08)]
- External data: CO(1-0) fluxes 7.2 and 6.8 Jy km/s used to estimate resolved-out flux  
  > "yielded total unresolved fluxes of 7.2$\pm$0.8 Jy km/s (cite: alloin92) and 6.8$\pm$0.9 Jy km/s (cite: evans02) for the $^{12}$CO(1-0) transition" (3.3 CO and dust continuum) [from (cite: alloin92); (cite: evans02)]
- External data: Systemic redshift 0.050355  
  > "systemic heliocentric velocity of 15096 km/s corresponding to the redshift of 0.050355 reported by (cite: falco99)" (4.1 Optical Emission Lines) [from (cite: falco99)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.5.0  
  > "Data reduction and analysis were carried out using the Common Astronomy Software Applications (CASA) version 4.5.0." (2.3 ALMA)
- pipeline version: _not stated_
- archive products used as is: No; data re-processed with natural weighting instead of NAASC early processing  
  > "we decided to re-process the ALMA data using a natural weighting scheme" (2.3 ALMA)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Natural weighting (NAASC early processing used Briggs robust 0.5)  
  > "This value was obtained using a Brigg Robust image weighting (cite: briggs95) with a robust parameter of 0.5" (2.3 ALMA)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: CO map is continuum-subtracted (method not given)  
  > "Fig. [10](#img_co21_mom0) shows the velocity-integrated continuum-subtracted $^{12}$CO(2-1) emission map" (3.3 CO and dust continuum)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.3'' x 0.17''  
  > "The resulting beam size is 0.3$''$$\times$0.17$''$." (2.3 ALMA)
- final rms: _not stated_

### Inherited from earlier work

- CO luminosity prescription (eq. 3)  
  > "Following the prescription described in Sections 2.1 and 2.2 of (cite: solomon05), and in particular their equation 3" (3.3 CO and dust continuum) [from (cite: solomon05)]
- CO-to-H2 conversion alpha=4.3  
  > "$\alpha$=4.3M$_\ensuremath{\odot}$(K km s$^{-1}$pc$^2$)$^{-1}$ (cite: bolatto13)" (3.3 CO and dust continuum) [from (cite: bolatto13)]

### Not stated but needed to reproduce (our reading)

- Image size, cell size, mask, cleaning threshold and iterations for the natural-weighted CO cube
- Line-free channels and order for continuum subtraction
- Moment map construction and clipping thresholds
- Exact region definitions for flux extraction and nuclear-beam gas mass
- Flux calibrator and ALMA flux scale uncertainty
- Whether the pipeline or manual scripts were used for calibration
- CO(2-1)/(1-0) assumption and rest frequency used

## Analysis recipe

1. **Re-image ALMA data**: Re-process with natural weighting for higher sensitivity  
  > "we decided to re-process the ALMA data using a natural weighting scheme, which delivers a higher sensitivity at the expense of a slightly worse spatial resolution" (2.3 ALMA)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure CO(2-1) flux and gas mass**: Integrate flux in ~4''x3'' region, compute L'CO and M_gas = alpha L'CO  
  > "Defining a $\sim$4$''$$\times$3$''$ region centered on the Mrk 463E nucleus that encloses the majority of the flux, we obtain a total flux density of 11.4$\pm$0.12 Jy km/s." (3.3 CO and dust continuum)
   - assumption: alpha=4.3 Msun (K km/s pc^2)^-1; thermalized optically thick CO  
  > "we assume that the CO emission is thermalized and optically thick so that the intrinsic line luminosity is independent of $J$" (3.3 CO and dust continuum)
   - fitting: _not stated_
   - validation: Compared with CO(1-0) single-dish fluxes: ~50% resolved out  
  > "our high-resolution ALMA observations resolve out $\sim$50% of the CO emission for the Mrk 463E nucleus" (3.3 CO and dust continuum)
3. **Molecular gas kinematics and infall rate**: Velocity map; infall rate from nuclear-beam CO mass, 200 km/s infall velocity at 75 pc  
  > "assuming that this gas is falling at $\sim$200 km/s based on the CO(2-1) velocity measured on the nuclear ALMA beam and that it is at an average distance of 75 pc" (4.3 CO and dust continuum)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.5.0: ALMA data reduction and analysis  
  > "Data reduction and analysis were carried out using the Common Astronomy Software Applications (CASA) version 4.5.0." (2.3 ALMA)
- **ESO MUSE pipeline** 1.6.2: MUSE reduction  
  > "Data reduction was carried out using the ESO MUSE pipeline version 1.6.2" (2.1 MUSE)
- **Fluxer** 2.7: Gaussian emission line fitting  
  > "carried out using IDL *Fluxer*[^4] tool version 2.7" (2.1 MUSE)
- **pPXF** : Stellar kinematics fitting  
  > "fitted the optical continuum and absorption lines using the Penalized Pixel-Fitting (pPXF) method" (4.2 Stellar kinematics)
- **CLOUDY** 13.04: Photoionization modeling of southern cloud  
  > "plasma ionization code CLOUDY version 13.04" (5.2 Energetics of the Emission Line Region)
- **Pyspeckit** : Multi-component line fits  
  > "were carried out using the Pyspeckit Python package (cite: ginsburg11)" (2.1 MUSE)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(2-1) flux, Mrk 463E region | 11.4 | 0.12 | Jy km/s | 2 | we obtain a total flux density of 11.4$\pm$0.12 Jy km/s |
| CO(2-1) flux, Mrk 463W region | 4.5 | 0.12 | Jy km/s | 2 | we derive a line flux density of 4.5$\pm$0.12 Jy km/s |
| Molecular gas mass, Mrk 463E | 1.36e9 | not stated | Msun | 2 | we obtain a total gas mass in this region of 1.36$\times$10$^9$M$_\ensuremath{\odot}$ |
| Molecular gas mass, Mrk 463W | 5.39e8 | not stated | Msun | 2 | $M_{gas}$=5.39$\times$10$^8$M$_\ensuremath{\odot}$ |
| Molecular gas infall rate onto Mrk 463E | ~104 | not stated | Msun/yr | 3 | this yields an influx rate of $\sim$104 M$_\ensuremath{\odot}$/yr |
| Ionized outflow rate | 512 (f/0.001) | not stated | Msun/yr | 0 | $\dot{M}_{\textnormal{out}}$=512($f$/0.001) $M_\odot$/yr |

## Qualitative findings

- Molecular gas shows ring-like/infalling structures around each nucleus with little CO directly on the AGN  
  > "The eastern emission region presents an incomplete ring-like or infalling spiral structure, possibly centered on the AGN" (4.3 CO and dust continuum)

## Claim tuples

- H: Is molecular gas infall balanced by ionized outflow while SMBH accretion is small? | E: CO(2-1) infall estimate versus [OIII]-based outflow rate and X-ray accretion rate | R: Infall ~104 Msun/yr, outflow ~512 Msun/yr, accretion ~0.017 Msun/yr | F: Rough balance between infall and outflow; accretion is a tiny fraction | **supported**
- H: Has the Mrk 463E AGN luminosity dropped recently? | E: CLOUDY modelling of southern emission line region | R: Required luminosity 2.7e45-1.8e46 erg/s versus current ~1e45 | F: Luminosity drop by factor 3-20 over ~40,000 years | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Natural weighting chosen to approach requested sensitivity  
  > "which delivers a higher sensitivity at the expense of a slightly worse spatial resolution" (2.3 ALMA)
- How they decided it was enough: _not stated_
- Limitation (authors): High-resolution ALMA data resolve out ~50% of CO emission  
  > "our high-resolution ALMA observations resolve out $\sim$50% of the CO emission" (3.3 CO and dust continuum)
- Caveat (inferred, ours): Gas masses depend strongly on alpha=4.3 versus ULIRG-appropriate values
- Caveat (inferred, ours): Outflow rate depends on assumed filling factor and density
- Caveat (inferred, ours): Infall rate is a crude estimate with assumed velocity and radius
- Caveat (inferred, ours): CO(2-1)/(1-0) ratio of 4 in flux units assumed

## Reproducibility

- Data public (paper): Program code given; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00525.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: Continuum subtraction channels
- Missing: Region definitions
- Data volume (inferred): ~10-50 GB for the two ALMA EBs
- Score (inferred): 3/5, ALMA part is simple with stated sensitivity and beam, but imaging details are missing.
- Rediscovery candidate: no, ALMA recipe is incomplete and the main results rely on multi-instrument data.

## Links

- Method: (cite: solomon05) (CO luminosity formula)
- Method: (cite: bolatto13) (alpha_CO)
- Companion: (cite: bianchi08) (Chandra X-ray properties of the nuclei)
- Related: MODA (Multiwavelength Observations of Dual AGN)

## Checks

```json
{
 "quotes": 50,
 "quotes_ok": 50,
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
  "facts": 69,
  "stated": 39,
  "rate": 0.565
 },
 "evidence_ok": true
}
```
