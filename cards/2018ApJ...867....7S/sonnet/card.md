# Molecular Clouds Associated with the Type Ia SNR N103B in the Large Magellanic Cloud

`2018ApJ...867....7S` | The Astrophysical Journal 2018 | first author: Sano, H. | arXiv: 1806.10299 | DOI: 10.3847/1538-4357/aae07c

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism
- Question: Are there molecular clouds associated with the Type Ia SNR N103B in the LMC, and does their gas motion constrain the progenitor (single-degenerate) scenario?  
  > "We present a possible scenario that N103B exploded in the wind-bubble formed by the accretion winds from the progenitor system, and is now interacting with the dense gas wall." (abstract)
- Target **N103B (SNR 0509-68.7)**: coordinates ~(05h08m59s, -68d43m36s) (map center)  
  > "The angular size of N103B is $27'' \times 29''$ corresponding the diameter $\sim$6.8 pc at the LMC distance of 50 kpc" (1 Introduction); z/distance LMC distance of 50 kpc  
  > "The angular size of N103B is $27'' \times 29''$ corresponding the diameter $\sim$6.8 pc at the LMC distance of 50 kpc" (1 Introduction); distance from (cite: 2016A&A...585A.162M; 2017ApJS..230....2B)  
  > "The angular size of N103B is $27'' \times 29''$ corresponding the diameter $\sim$6.8 pc at the LMC distance of 50 kpc" (1 Introduction)

## Data provenance

- ALMA projects: 2015.1.01130.S
- bands: Band 3 (84–119 GHz)  
  > "using ALMA Band 3 (84–119 GHz) as a Cycle 3 filler project" (2.1 CO)
- frequencies and spectral setup: correlator bandwidth 58.59 MHz, velocity coverage 152.5 km/s  
  > "The correlator was set to have a bandwidth of 58.59 MHz, representing the velocity coverage of 152.5 km s$^{-1}$." (2.1 CO)
- continuum bandwidth: _not stated_
- arrays: 12 m array, 38 antennas, mosaic of 100'' x 100''  
  > "The observations were carried out using 38 antennas for 12 m array." (2.1 CO)
- configurations: _not stated_
- baselines: 13.7 to 1551.1 m (4.6 to 596.0 kλ)  
  > "The baseline ranges are from 13.7 to 1551.1 m, corresponding to the *u-v* coverage form 4.6 to 596.0 $k\lambda$." (2.1 CO)
- angular resolution: 1.92'' x 1.73'', PA 66.7 deg (~0.44 pc)  
  > "The final beam size is $1.92'' \times 1.73''$ with a position angle of $66.7\ensuremath{^\circ}$" (2.1 CO)
- max recoverable scale: _not stated_
- sensitivity: ~0.95 K at 0.4 km/s  
  > "Typical noise fluctuation is $\sim$0.95 K at 0.4 km s$^{-1}$ velocity resolution." (2.1 CO)
- time on source: _not stated_
- observing dates: 31 January and 27 August 2016  
  > "were conducted at 31th January and 27th August 2016 using ALMA Band 3" (2.1 CO)
- pi or archival as stated: Cycle 3 filler project, PI Kosuke Fujii  
  > "as a Cycle 3 filler project $\#$2015.1.01130.S (PI: Kosuke Fujii)" (2.1 CO)
- Line: 12CO J=1-0 (not stated)
- Other facility **ASTE**: 12CO(J=3-2) map, 25'' beam  
  > "Observations of $^{12}$CO($J$ = 3–2) line emission at 0.87 mm wavelength were carried out in 16–24 November 2015 using ASTE" (2.1 CO)
- Other facility **Chandra**: 14 archival ACIS-S observations, 459.5 ks combined  
  > "The total effective exposure time and pixel size are 459.5 ks and $0.49\ensuremath{''}$, respectively." (2.3 X-rays)
- Other facility **ATCA + Parkes**: archival HI 21 cm data, 60'' resolution  
  > "The angular resolution of the Hi data is $60''$, corresponding to the spatial resolution of $\sim$15 pc at the distance of the LMC." (2.2 Hi)
- Other facility **Mopra**: single-dish CO(1-0) for missing-flux check  
  > "we compared the integrated intensity of the Mopra single-dish data" (2.1 CO)
- Other facility **HST WFC3**: Halpha image  
  > "Figure [1](#fig1)b shows an H$\alpha$ image obtained using *Hubble Space Telescope* (HST) with WFC3." (3.1 Large-Scale Distribution)
- External data: HI 21 cm cube (ATCA + Parkes)  
  > "We also used archival Hi 21 cm line data published by (cite: 2003ApJS..148..473K)." (2.2 Hi) [from (cite: 2003ApJS..148..473K)]
- External data: Mopra CO data used for missing-flux comparison  
  > "we compared the integrated intensity of the Mopra single-dish data (cite: 2011ApJS..197...16W; 2017ApJ...850..139W; 2017AIPC.1792d0038S; sano2018)" (2.1 CO) [from (cite: 2011ApJS..197...16W; 2017ApJ...850..139W; 2017AIPC.1792d0038S; sano2018)]
- External data: Balmer-dominant shock velocities ~2100 and ~1200 km/s  
  > "the velocity for Balmer-dominant shocks is $\sim$2100 km s$^{-1}$ in the northern edge of the shell" (4.1 Inhomogeneous Distribution) [from (cite: 2017ApJ...847..122G)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 5.1.0  
  > "package version 5.1.0" (2.1 CO)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0519-4546 (flux); J0635-7516 (gain); J0529-7245 (phase)  
  > "J0635$-$7516 for the complex gain calibrator, J0519$-$4546 for the flux calibrator, and J0529$-$7245 for the phase calibrator" (2.1 CO)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: multiscale CLEAN  
  > "We used the natural weighting and the multiscale CLEAN algorithm (cite: 2008ISTSP...2..793C) implemented in the CASA package." (2.1 CO)
- weighting robust: natural weighting  
  > "We used the natural weighting and the multiscale CLEAN algorithm" (2.1 CO)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: ALMA 12 m only; missing flux checked vs Mopra, ~10% smaller, deemed negligible  
  > "Since the total integrated intensity of ALMA data is $\sim$10$\%$ smaller than that of the single-dish data, the missing flux is considered to be negligible." (2.1 CO)
- smoothing: _not stated_
- final beam: 1.92'' x 1.73'', PA 66.7 deg  
  > "The final beam size is $1.92'' \times 1.73''$ with a position angle of $66.7\ensuremath{^\circ}$" (2.1 CO)
- final rms: ~0.95 K at 0.4 km/s  
  > "Typical noise fluctuation is $\sim$0.95 K at 0.4 km s$^{-1}$ velocity resolution." (2.1 CO)

### Inherited from earlier work

- X(CO) conversion factor and mean molecular weight mu=2.38  
  > "We use the conversion factor $X = 7.0 \times 10^{20}$ cm$^{-2}$ (K km s$^{-1}$)$^{-1}$ (cite: 2008ApJS..178...56F)." (3.2 Detailed CO Distribution with ALMA) [from (cite: 2008ApJS..178...56F)]
- Accretion wind mass-loss rate and velocity  
  > "the accretion wind of Type Ia SD progenitor system has a wind mass of $\sim$ $10^{-4}$ $M_\ensuremath{\odot}$ yr$^{-1}$" (4.2 Implications for the progenitor system) [from (cite: 1999ApJ...522..487H; 1999ApJ...519..314H)]

### Not stated but needed to reproduce (our reading)

- Line-free channels / continuum handling for the CO cube
- Cell size, image size, CLEAN threshold, mask and multiscale scales
- Which execution blocks/MOUS were used and whether pipeline or manual calibration
- Velocity range and region used for mass of the expanding shell (~5e3 Msun)
- How PV cavity/expansion velocity was determined (fit vs by eye)
- Wind duration assumption basis (3e5 yr)
- Mosaic pointing count and primary beam correction details

## Analysis recipe

1. **Calibrate and image ALMA CO(1-0)**: CASA calibration and multiscale CLEAN with natural weighting  
  > "We used the natural weighting and the multiscale CLEAN algorithm (cite: 2008ISTSP...2..793C) implemented in the CASA package." (2.1 CO)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared with Mopra single-dish flux, ALMA ~10% lower  
  > "Since the total integrated intensity of ALMA data is $\sim$10$\%$ smaller than that of the single-dish data, the missing flux is considered to be negligible." (2.1 CO)
2. **Identify cloud-SNR association and expansion**: Channel maps and position-velocity diagram; cavity-like structure gives expansion velocity ~5 km/s  
  > "We find a cavity-like structure in the position-velocity diagram, indicating an evidence for the expanding gas motion with an expansion velocity of $\sim$5 km s$^{-1}$" (3.2 Detailed CO Distribution with ALMA)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive molecular cloud masses**: M = mu m_p D^2 Omega sum N(H2), N(H2)=X W(CO), regions >=3 sigma  
  > "The physical properties of molecular clouds are estimated for the regions that are significantly detected by CO line emission with a 3-sigma or higher." (3.2 Detailed CO Distribution with ALMA)
   - assumption: X = 7.0e20 cm-2 (K km/s)-1; mu = 2.38; D = 50 kpc; beam-filling factor ~1 for clumps  
  > "we assumed a beam-filling factor of $\sim$1" (3.3 Tiny Molecular Clumps)
   - fitting: _not stated_
   - validation: Total mass consistent with previous Mopra CO study  
  > "which is roughly consistent with previous CO studies" (3.2 Detailed CO Distribution with ALMA)
4. **Test accretion-wind momentum budget**: Compare expanding shell momentum (M x 5 km/s) with wind momentum (1e-4 Msun/yr x 2000 km/s x 3e5 yr)  
  > "It is therefore that $\sim$40% of the wind momentum had transferred to the expanding gas motion." (4.2 Implications for the progenitor system)
   - assumption: wind duration ~3e5 yr  
  > "Assuming the wind duration of $\sim$ $3 \times 10^5$ yr" (4.2 Implications for the progenitor system)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.1.0: ALMA calibration, data reduction and multiscale CLEAN imaging  
  > "These calibrations and data reduction were made by the Common Astronomy Software Application (cite: 2007ASPC..376..127M) package version 5.1.0." (2.1 CO)
- **CIAO** 4.10: Chandra data reprocessing and imaging  
  > "We used *Chandra* Interactive Analysis of Observations (cite: 2006SPIE.6270E..1VF) software version 4.10 and CALDB 4.7.8" (2.3 X-rays)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total molecular cloud mass (ALMA) | 8e5 | not stated | Msun | 3 | We finally derive the total mass of the molecular cloud of $\sim$$8 \times 10^5$ $M_\ensuremath{\odot}$ |
| Expansion velocity | ~5 | not stated | km/s | 2 | with an expansion velocity of $\sim$5 km s$^{-1}$ |
| Expanding shell mass | 5e3 | not stated | Msun | 3 | the mass of expanding shell is estimated to be $\sim$$5 \times 10^3$ $M_\ensuremath{\odot}$ |
| Momentum of expanding shell | 2.5e4 | not stated | Msun km/s | 4 | the momentum is calculated to be $\sim$$2.5 \times 10^4$ $M_\ensuremath{\odot}$ km s$^{-1}$ |
| Clump A mass | 110 | not stated | Msun | 3 | $\sim$110 $M_\ensuremath{\odot}$, $\sim$1.2 pc, and $\sim$2000 cm$^{-3}$ for clump A |
| Clump B mass | 90 | not stated | Msun | 3 | $\sim$90 $M_\ensuremath{\odot}$, $\sim$1.3 pc, and $\sim$1400 cm$^{-3}$ for clump B |
| HI cloud mass | 2e4 | not stated | Msun | 0 | We finally obtain the mass of the Hi cloud is $\sim$$2 \times 10^4$ $M_\ensuremath{\odot}$ |

## Qualitative findings

- CO clouds trace the SNR boundary from south to northeast; none toward the northwestern shell  
  > "while the northwestern shell has no CO clouds" (4.1 Inhomogeneous Distribution)

## Claim tuples

- H: Molecular gas around N103B shows expansion consistent with accretion winds | E: ALMA CO(1-0) PV diagram and momentum comparison | R: Expansion ~5 km/s; ~40% of wind momentum transferred | F: N103B exploded in a wind bubble, consistent with SD scenario | **partially**
- H: Asymmetric X-ray shell reflects inhomogeneous ISM | E: Compared CO maps with Chandra image and shock velocities | R: CO along southeastern shell, none in northwest | F: Density contrast shapes shell morphology | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): HI resolution limits density estimate; companion star identification still needed  
  > "To verify the interpretation, further Hi observations with high spatial resolution with a few pc scales are needed." (4.1 Inhomogeneous Distribution)
- Caveat (inferred, ours): Expansion velocity from a by-eye PV cavity; no fit or uncertainty
- Caveat (inferred, ours): Wind duration and efficiency assumed; momentum comparison is order-of-magnitude
- Caveat (inferred, ours): Association with SNR based on projected morphology
- Caveat (inferred, ours): Single X factor used for LMC

## Reproducibility

- Data public (paper): ALMA data cited by project code; Chandra and HI archival  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA$\#$2015.1.01130.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters (cell, size, threshold, masks)
- Missing: PV extraction and expansion-velocity fitting details
- Missing: Mass-integration regions
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Public ALMA data and clear mass equations, but imaging and PV analysis details are missing.
- Rediscovery candidate: yes, Public data, with numeric results (masses, expansion velocity) that can be redone.

## Links

- Method: (cite: 2008ISTSP...2..793C) (multiscale CLEAN)
- Method: (cite: 2008ApJS..178...56F) (X factor and mu)
- Companion: (cite: 2017AIPC.1792d0038S; sano2018) (previous Mopra CO study of N103B)

## Checks

```json
{
 "quotes": 54,
 "quotes_ok": 54,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 42,
  "rate": 0.592
 },
 "evidence_ok": true
}
```
