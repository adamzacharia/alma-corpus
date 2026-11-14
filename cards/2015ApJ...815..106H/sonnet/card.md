# Sgr B2(N): A Bipolar Outflow and Rotating Hot Core Revealed by ALMA

`2015ApJ...815..106H` | The Astrophysical Journal 2015 | first author: Higuchi, Aya E. | arXiv: 1511.02955 | DOI: 10.1088/0004-637X/815/2/106

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation, astrochemistry, milky_way_ism
- Question: What is the kinematic structure of the Sgr B2(N) core (bipolar outflow vs rotating disk), and what are the outflow's physical parameters and molecular abundances?  
  > "The goal is to establish a clearer kinematic picture of the Sgr B2(N) core, and to enable further explorations of the processes associated with the on-going high-mass stars formation." (INTRODUCTION)
- Target **Sgr B2(N) (K2)**: coordinates K2: RA 17h47m19.88s, Dec -28d22m18.4s (J2000)  
  > "($\alpha_{J2000}$, $\delta_{J2000}$)=\[17$^{\mbox h}$47$^{\mbox m}$19$^{\mbox s}.$88,  $-$ $\!\!$28$^{\circ}$22$\ensuremath{'}$18$\ensuremath{''}.$4\] (cite: gau95)" (3.1 Line profiles); "At the adopted distance of 7.8 kpc (cite: rei09), 2$\ensuremath{''}$ corresponds to 0.076 pc." (INTRODUCTION); z/distance 7.8 kpc  
  > "($\alpha_{J2000}$, $\delta_{J2000}$)=\[17$^{\mbox h}$47$^{\mbox m}$19$^{\mbox s}.$88,  $-$ $\!\!$28$^{\circ}$22$\ensuremath{'}$18$\ensuremath{''}.$4\] (cite: gau95)" (3.1 Line profiles); "At the adopted distance of 7.8 kpc (cite: rei09), 2$\ensuremath{''}$ corresponds to 0.076 pc." (INTRODUCTION); distance from Reid et al. 2009 (cite: rei09)  
  > "($\alpha_{J2000}$, $\delta_{J2000}$)=\[17$^{\mbox h}$47$^{\mbox m}$19$^{\mbox s}.$88,  $-$ $\!\!$28$^{\circ}$22$\ensuremath{'}$18$\ensuremath{''}.$4\] (cite: gau95)" (3.1 Line profiles); "At the adopted distance of 7.8 kpc (cite: rei09), 2$\ensuremath{''}$ corresponds to 0.076 pc." (INTRODUCTION)

## Data provenance

- ALMA projects: 2011.0.0017.S
- bands: _not stated_
- frequencies and spectral setup: Spectral scan 84-111 GHz, four overlapping basebands; channel spacing 244 kHz, smoothed to 488 kHz (~1.6 km/s)  
  > "The full frequency range between 84 and 111 GHz was covered in the spectral scan mode with four overlapping basebands." (OBSERVATIONS); "The channel spacing was 244 kHz, and smoothed spectra were 488 kHz ($\sim$1.6 km s$^{-1}$)." (OBSERVATIONS)
- continuum bandwidth: _not stated_
- arrays: 12-m antennas; 1 execution with 21 antennas and 3 with 26 antennas (Cycle 0)  
  > "The observations were done in 1 execution with 21 12-m antennas and 3 executions with 26 12-m antennas at an angular resolution of $\sim$2$\ensuremath{''}$." (OBSERVATIONS)
- configurations: _not stated_
- baselines: Maximum baseline 440 m  
  > "The maximum baseline length achieved during the observations was 440 m." (OBSERVATIONS)
- angular resolution: ~2"; beams 1.9"x1.4" to 2.5"x1.8" depending on line  
  > "SiO | $v$=0, $J$=2–1 | 86.847 | 2.5$''$$\times$1.8$''$" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: 3 to 7 mJy/beam per 1.6 km/s channel  
  > "The sensitivity obtained ranges from 3 to 7 mJy beam$^{-1}$ per channel of 1.6 km s$^{-1}$" (OBSERVATIONS)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archival Cycle 0 Early Science data  
  > "We have analyzed the archival data of the ALMA observations of Sgr B2(N) in SO$_{2}$($12_{4,8} - 13_{3,11}$) and SiO ($2 - 1$) lines" (SUMMARY)
- Line: SO2 12(4,8)-13(3,11) (107.843 GHz)
- Line: SiO v=0, J=2-1 (86.847 GHz)
- Line: SiO v=2, J=2-1 (possible maser) (85.640 GHz)
- Line: SO2 29(4,26)-28(5,23) (99.393 GHz)
- External data: Partition functions Q(T) for SO2 and SiO  
  > "we use $Q$(150 K) = 2091, $Q$(100 K) = 1140, $Q$(50 K) = 404 from (cite: pic98)" (4.1) [from (cite: pic98)]
- External data: SO2 Eu=110.6 K and Smu^2=8.27 D^2  
  > "$E_{u}$=110.6 K and $S\mu^{2}$=8.27 D$^{2}$ (cite: bel13)" (4.1) [from (cite: bel13)]
- External data: X(C18O) = 1e-7 for Sgr B2  
  > "the adopted $X$(C$^{18}$O) of $1\times10^{-7}$ for Sgr B2 (cite: lis89)" (4.1) [from (cite: lis89)]
- External data: C18O column density per velocity  
  > "$^c$Hasegawa *et al.*, in preparation." (Table 2) [from Hasegawa et al., in prep.]
- External data: H2O maser positions  
  > "the position of the H$_2$O maser spots reported by (cite: mcg04)" (3.3) [from (cite: mcg04)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Neptune (amplitude); B1730-130 bandpass; J1700-261 gain  
  > "Amplitude calibration was done using Neptune. The quasars B1730-130 and J1700-261 were used to calibrate the bandpass and the complex gain fluctuations, respectively." (OBSERVATIONS)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA; natural weighting  
  > "Natural Weighting was used for imaging." (OBSERVATIONS)
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
- final beam: 1.9"x1.4" (SO2 12_4,8), 2.5"x1.8" (SiO)  
  > "SO$_{2}$ | 12$_{4,8}$–13$_{3,11}$ | 107.843 | 1.9$''$$\times$1.4$''$" (Table 1)
- final rms: 6 mJy/beam for SO2 12_4,8-13_3,11 at 1.6 km/s  
  > "SO$_{2}$ | 12$_{4,8}$–13$_{3,11}$ | 107.843 | 1.9$''$$\times$1.4$''$ | 1.6 | 6" (Table 1)

### Inherited from earlier work

- Observations/data description follow Belloche et al. 2014 Cycle 0 spectral scan  
  > "Sgr B2(N) was observed with ALMA (cite: hil10) during Early Science Cycle 0 (cite: bel14)." (OBSERVATIONS) [from (cite: bel14)]
- Column density formula  
  > "Molecular column densities can be calculated (cite: liu98) from" (4.1) [from (cite: liu98)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration procedure (pipeline vs manual)
- Continuum subtraction method and line-free channels
- Image size, cell size, cleaning parameters and masks
- Primary beam correction details
- How C18O column densities were derived (Hasegawa et al. in prep.)
- Method for fitting velocity gradients and extracting P-V diagrams
- Flux calibration uncertainty

## Analysis recipe

1. **Image line cubes and spectra**: Natural-weighted CASA imaging of SO2 and SiO; spectra integrated over 20"x20" box at K2  
  > "spectra of the SO$_{2}$ and SiO lines integrated within a 20$\ensuremath{''}$$\times$20$\ensuremath{''}$ region centered on the K2 position" (3.1 Line profiles)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Map kinematics**: Channel maps, moment-1 maps, peak-position shifts and P-V diagrams at PA=120 and 30 deg  
  > "Figure [6](#pv)(a) shows the observed position-velocity (P-V) diagram of the SO$_{2}$ emission along the major axis of the bipolar outflow (P.A.=120$^\circ$)." (3.3)
   - assumption: Vsys = 63 km/s  
  > "which we adopt for the systemic velocity ($V$$_{\rm{SYS}}$) of Sgr B2(N)" (3.1 Line profiles)
   - fitting: _not stated_
   - validation: Compared higher-Eu SO2 line P-V diagram to test Keplerian rotation  
  > "This situation is quite different from the case of a disk in Keplerian rotation around a massive star" (3.3)
3. **Fractional abundances of SO2 and SiO**: Optically thin LTE column densities in a 6"x6" box at 46.6 km/s compared to C18O  
  > "we assume that SO$_{2}$, SiO and C$^{18}$O lines are optically thin and in a local thermodynamical equilibrium" (4.1)
   - parameter: Tex = 50, 100, 150 K  
  > "we have adopted a range of possible temperatures (50, 100, and 150 K) to compare the results" (4.1)
   - assumption: X(C18O)=1e-7; uniform relative abundances over position-velocity space  
  > "we assume that their relative abundances are uniform in the position-velocity space defined by the outflow" (4.1)
   - fitting: _not stated_
   - validation: Compared with abundances in other high-mass regions  
  > "These values are consistent with the previous estimates for other high-mass hot cores." (4.1)
4. **Outflow mass, momentum, energy, dynamical time**: Per-channel masses for |dV|>7 km/s; momentum = sum M|dV|, energy = 1/2 sum M dV^2; t_dyn = l1/V_outflow; no inclination correction  
  > "The momentum is given by $\Sigma$$M_{i}$$|\Delta{V_{i}}|$ and the energy by (1/2)$\Sigma$$M_{i}$${|\Delta{V_{i}}|}^{2}$" (4.2)
   - fitting: _not stated_
   - validation: Compared with other outflows  
  > "In comparison with their physical parameters, the Sgr B2(N) outflow has a comparable mass" (4.2)

## Software

- **CASA** : Data reduction and imaging  
  > "Data reduction was performed using the Common Astronomy Software Applications package (CASA; http://casa.nrao.edu)." (OBSERVATIONS)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| X(SO2) in outflow (Tex=100 K) | 2.3e-8 | +2.6/-0.4 e-8 | dimensionless | 3 | $X$(SO$_{2}$) = ${2.3^{+2.6}}_{-0.4}$$\times$10$^{-8}$ |
| X(SiO) in outflow | 1.2e-9 | +/-0.1e-9 | dimensionless | 3 | $X$(SiO) = ${1.2^{+0.1}}_{-0.1}$$\times$10$^{-9}$ |
| Total outflow mass | 2.0e3 | not stated | Msun | 4 | Total / 2.0$\times$10$^{3}$ |
| Total momentum | 3.0e4 | not stated | Msun km/s | 4 | Total / 3.0$\times$10$^{4}$ |
| Total kinetic energy | 5.5e48 | not stated | erg | 4 | Total / 5.5$\times$10$^{48}$ |
| Average dynamical time | 4.7e3 | not stated | yr | 4 | Average / 4.7$\times$10$^{3}$ |
| Core rotation velocity gradient | 88 | not stated | km/s/pc | 2 | we determine a velocity gradient of 88 km s$^{-1}$ pc$^{-1}$ |
| Dynamical mass of rotating core | 42/(sin i)^2 | not stated | Msun | 2 | a dynamical mass of 42 $M_\odot/ (\sin i)^2$ is needed within this radius |
| SiO v=2 J=2-1 FWHM | 3.8 | 0.3 | km/s | 0 | The emission has a linewidth of FWHM=3.8$\pm$0.3 km s$^{-1}$ |
| Mass spectrum power index | ~-1 | not stated | dimensionless | 4 | with a power index $\gamma$$\sim$-1 |

## Qualitative findings

- SO2 line core shows N-S gradient perpendicular to the E-W outflow, interpreted as a rotating ring-like toroid of ~6000 AU radius without Keplerian signature  
  > "arises from a rotating ring-like structure with a radius $\sim$6000 AU" (3.3)

## Claim tuples

- H: Is the Sgr B2(N) core an E-W bipolar outflow plus N-S rotating core, or a large E-W rotating disk? | E: Channel maps, moment maps and P-V diagrams of SO2 and SiO | R: E-W wing emission symmetric about K2; N-S gradient in line core | F: Bipolar outflow driven from K2 plus rotating hot core, supporting Lis et al. 1993 | **supported**
- H: What are the outflow properties? | E: LTE abundances vs C18O and channel mass sums | R: Mass ~2000 Msun, t_dyn ~5e3 yr, collimation ~60 deg | F: Young, massive, moderately collimated outflow | **supported**
- H: Is SiO v=2 J=2-1 maser emission present at K2? | E: Checked vibrationally excited SiO lines | R: Point-like narrow 2 Jy line at K2 | F: Possible maser, needs confirmation | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: SO2 12_4,8-13_3,11 chosen for high Eu and less contamination  
  > "its upper state energy is high ($E_{\rm u} = 110.6$ K), and it traces the hotter and denser region" (OBSERVATIONS)
- Alternative: CH3OCHO assignment of the 72 km/s feature judged unlikely; gravitationally bound circular motion for the wings rejected  
  > "but this assignment is unlikely because the emission in other transitions of this molecule have larger linewidth" (3.5)
- How they decided it was enough: _not stated_
- Limitation (authors): Uniform excitation and chemistry assumed over space and velocity; C18O contaminated; resolution too low to resolve outflow or inner structure  
  > "it is obviously a bold simplification" (4.1)
- Caveat (inferred, ours): LTE with a single Tex and optically thin assumption in a hot, dense, absorbed region is questionable
- Caveat (inferred, ours): C18O comparison at a single channel/box drives abundances and mass
- Caveat (inferred, ours): No inclination correction for outflow parameters
- Caveat (inferred, ours): Maser identification from one line is tentative
- Caveat (inferred, ours): Line blending in a line-rich source

## Reproducibility

- Data public (paper): Archival ALMA Cycle 0 data  
  > "we analyze the ALMA archival data taken at $\sim$2$\ensuremath{''}$ resolution" (INTRODUCTION)
- Products in archive: _not stated_
- Missing: CASA version, imaging parameters
- Missing: C18O column density maps (Hasegawa et al. in prep.)
- Missing: Details of velocity gradient and P-V extraction
- Data volume (inferred): ~100-300 GB raw (Cycle 0 spectral scan, 4 executions)
- Score (inferred): 3/5, Public data and simple formulas, but processing and imaging details are sparse and C18O inputs are unpublished.
- Rediscovery candidate: no, Imaging recipe and C18O column densities are incomplete.

## Links

- Method: (cite: liu98) (column density formula)
- Method: (cite: bel14) (Cycle 0 spectral scan data)
- Companion: Hasegawa et al., in prep. (C18O analysis)
- Related: Belloche et al. ALMA Cycle 0 spectral scan of Sgr B2(N)

## Checks

```json
{
 "quotes": 60,
 "quotes_ok": 60,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.0.0017.S"
 ],
 "obscore_codes_not_in_card": [
  "2011.0.00017.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 37,
  "rate": 0.536
 },
 "evidence_ok": true
}
```
