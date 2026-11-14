# Exploring molecular complexity with ALMA (EMoCA): complex isocyanides in Sgr B2(N)

`2020A&A...636A..29W` | Astronomy and Astrophysics 2020 | first author: Willis, E. R. | arXiv: 2003.07423 | DOI: 10.1051/0004-6361/201936489

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: astrochemistry, star_formation, milky_way_ism
- Question: What are the column densities and excitation temperatures of cyanides and isocyanides in Sgr B2(N2), and can updated chemical models with a single-stage collapse/warm-up and extinction-dependent cosmic-ray ionization reproduce the NC:CN ratios?  
  > "We investigate the column densities and excitation temperatures of cyanide and isocyanide species in Sgr B2(N2). We then use state-of-the-art chemical models to interpret these observed quantities." (abstract)
- Target **Sgr B2(N2)**: coordinates RA 17h47m19.86s, Dec -28°22'13.4'' (J2000)  
  > "We analyze here the spectrum of the secondary hot core Sgr B2(N2) at the position ($\alpha, \delta$)$_{\rm J2000}$= ($17^{\rm h}47^{\rm m}19.86^{\rm s}, -28^\circ22'13.4''$)" (Observational results); "This scale translates into $\sim$0.8 pc at the adopted distance of 8.3 kpc (cite: Reid14)." (Observations); z/distance 8.3 kpc  
  > "We analyze here the spectrum of the secondary hot core Sgr B2(N2) at the position ($\alpha, \delta$)$_{\rm J2000}$= ($17^{\rm h}47^{\rm m}19.86^{\rm s}, -28^\circ22'13.4''$)" (Observational results); "This scale translates into $\sim$0.8 pc at the adopted distance of 8.3 kpc (cite: Reid14)." (Observations); distance from Reid et al. 2014  
  > "We analyze here the spectrum of the secondary hot core Sgr B2(N2) at the position ($\alpha, \delta$)$_{\rm J2000}$= ($17^{\rm h}47^{\rm m}19.86^{\rm s}, -28^\circ22'13.4''$)" (Observational results); "This scale translates into $\sim$0.8 pc at the adopted distance of 8.3 kpc (cite: Reid14)." (Observations)

## Data provenance

- ALMA projects: 2011.0.00017.S, 2012.1.00012.S
- bands: _not stated_
- frequencies and spectral setup: 84.1-114.4 GHz in five setups; spectral resolution 488.3 kHz (1.7 to 1.3 km/s)  
  > "The survey covers the frequency range between 84.1 and 114.4 GHz in five setups. It has a spectral resolution of 488.3 kHz (1.7 to 1.3 km s$^{-1}$)" (Observations)
- continuum bandwidth: _not stated_
- arrays: ALMA main array, cycles 0 and 1  
  > "in its cycles 0 and 1" (Observations)
- configurations: _not stated_
- baselines: ~17 m to ~400 m  
  > "We used the main array with baselines ranging from $\sim$17 m to $\sim$400 m" (Observations)
- angular resolution: median 1.6'' (~0.06 pc)  
  > "a median angular resolution of 1.6$\ensuremath{''}$ ($\sim$0.06 pc or $\sim$13000 au)" (Observations)
- max recoverable scale: ~20''  
  > "which imply a maximum recoverable scale of $\sim 20\ensuremath{''}$" (Observations)
- sensitivity: rms ~3 mJy/beam; 0.1-0.2 K depending on setup  
  > "The achieved rms sensitivity is on the order of 3 mJy beam$^{-1}$, which translates into an rms sensitivity of 0.1-0.2 K" (Observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CH3NC 5_2-4_2 and 5_1-4_1 (100517.433 and 100524.249 MHz)
- Line: HCCNC J=10-9 and 11-10 (99354.250 and 109289.095 MHz)
- External data: CH3CN, C2H5CN, C2H3CN, HC3N column densities and LTE parameters toward Sgr B2(N2)  
  > "The parameters reported for CH$_3$CN, C$_2$H$_5$CN, C$_2$H$_3$CN, and HC$_3$N are taken from (cite: Belloche16)." (Table notes) [from (cite: Belloche16)]
- External data: Hot-core physical parameters (T0, n0, r0) from EMoCA  
  > "$T_0$, $n_0$, and $r_0$ are determined from observations of Sgr B2(N2) taken as part of the EMoCA survey (cite: bonfand17; bonfand19)" (5.2 Physical model) [from (cite: bonfand17; bonfand19)]
- External data: Binding energies of CH3CN and CH3NC on water ice (6150 K, 5686 K)  
  > "The values are 6150 K for and 5686 K for ." (5.1 Chemical network) [from (cite: bertin17)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

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

- Observations, data reduction, line identification and column density derivation  
  > "A detailed description of the observations, the data reduction process, and the method used to identify the detected lines and derive column densities was presented in (cite: Belloche16)." (Observations) [from (cite: Belloche16)]
- Chemical network basis and MAGICKAL code  
  > "The basis of the chemical network is taken from (cite: garrod17), with the above-mentioned inclusion of chemistry first presented by (cite: calcutt18)." (5 Chemical modeling) [from (cite: garrod17); (cite: calcutt18)]
- Radiative transfer model details  
  > "Details of the radiative transfer model used here are given in (cite: garrod13)" (6.4) [from (cite: garrod13)]

### Not stated but needed to reproduce (our reading)

- Calibration and imaging details (CASA version, robust, masks, continuum subtraction) are all deferred to Belloche et al. 2016
- Reduced EMoCA spectral cubes are not described as released
- Full chemical network files and MAGICKAL input not provided
- Formal uncertainties on column densities (fit by eye)
- Initial abundances and other chemical model parameters not listed
- Radiative transfer beam size not stated

## Analysis recipe

1. **LTE modeling of observed spectrum toward N2**: Synthetic LTE spectra with Weeds; CH3NC and HCCNC use same parameters as CH3CN and HC3N with only column density free; upper limits likewise  
  > "For each investigated molecule, a synthetic spectrum is produced using the software Weeds (cite: Maret11)" (Observational results); "The LTE model assumes the same parameters as for CH$_3$CN, with only the column density left as a free parameter." (Detection of CH3NC and HCCNC)
   - software: Weeds
   - parameter: five free parameters: size, column density, temperature, line width, velocity offset  
  > "The spectrum of each molecule is modeled with five free parameters: the size of the emission assumed to be Gaussian, the column density, the temperature, the line width, and the velocity offset" (Observational results)
   - assumption: LTE valid given high densities  
  > "under the assumption of local thermodynamic equilibrium (LTE), which is valid here given the high densities (cite: bonfand19)" (Observational results)
   - fitting: Parameters adjusted until good fit by visual inspection  
  > "These parameters are adjusted until a good fit to the observed spectrum is achieved, as evaluated by visual inspection." (Observational results)
   - validation: Detection requires uncontaminated lines reproduced by model  
  > "Two of them are detected (at 100518 MHz and 100524 MHz) without contamination from other species and well reproduced by our LTE model" (Detection of CH3NC and HCCNC)
2. **Build single-stage physical model of N2**: Power-law density and temperature profiles with free-fall collapse; density floor 1e4 cm-3; stop at 400 K  
  > "We have chosen to give the density profile a minimum gas-phase density of $10^{4}$ cm$^{-3}$." (5.2 Physical model); "The collapse is stopped once a temperature of 400 K is reached" (5.2 Physical model)
   - software: MAGICKAL
   - parameter: r0=6010 au, n0=1.54e7 cm-3, T0=135.5 K, alpha=1.5, q=0.38, nf=2.74e9 cm-3  
  > "| $r_{0}$   | 6010 au                          |" (Table 1)
   - assumption: alpha from Shu 1977, q from Terebey 1993; COM rotational temperature equals dust temperature  
  > "we assume the rotational temperature measured for COMs at $r_0$ to be equal to the dust temperature at that radius" (5.2 Physical model)
   - fitting: _not stated_
   - validation: Column density from profile within a factor of two of observed value  
  > "a value of $\sim$2.5 × 10^24^ cm$^{-2}$ is obtained, which is within a factor of two of the observational value of 1.4 × 10^24^ cm$^{-2}$" (7.3)
3. **Run chemical models varying barrier and cosmic-ray ionization rate**: Seven models: constant zeta 1.3e-17, 1e-16, 3e-14, and Av-dependent zeta = 3.9e-16 Av^-0.6 + 1e-17 with multipliers 3.9e-16/-15/-14; H+CH3NC barrier 1200 vs 3000 K  
  > "$\zeta = 3.9 \times 10^{-16}(A_{v})^{-0.6} + 10^{-17} s^{-1}$" (5.3 Cosmic-ray ionization)
   - software: MAGICKAL
   - parameter: H+CH3NC barrier 1200 K (standard) vs 3000 K (Model 2)  
  > "The standard models presented in this paper use a barrier of 1200 K" (5.1)
   - assumption: New isocyanide reactions and binding energies analogous to cyanides  
  > "Grain-surface binding energies for and related radicals were chosen to mimic those of the corresponding cyanides" (5.1)
   - fitting: _not stated_
   - validation: _not stated_
4. **Radiative transfer of model abundances and rotational diagrams**: LTE radiative transfer through spherical model, convolution with Gaussian beam, rotation diagrams with optical depth correction, integration to ~8e4 au  
  > "We integrate the emission of each molecule only for a radius of $\sim$8 × 10^4^ au, which is the maximum recoverable scale of ALMA in the EMoCA survey." (6.4)
   - software: MAGICKAL
   - assumption: LTE  
  > "we then use the LTE approximation to calculate radiative transfer along lines of sight" (6.4)
   - fitting: Gaussian fit to line wings for optical depth correction  
  > "We correct for the optical depth of lines by fitting the wings of each spectral line to a Gaussian." (6.4)
   - validation: _not stated_

## Software

- **Weeds** : Synthetic LTE spectra  
  > "a synthetic spectrum is produced using the software Weeds (cite: Maret11)" (Observational results)
- **MAGICKAL** : Three-phase chemical kinetics modeling  
  > "we use the chemical kinetics code MAGICKAL (cite: garrod13)" (5 Chemical modeling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CH3NC column density | 1.0e16 | not stated | cm^-2 | 1 | / CH$_3$NC, $\varv=0$ / t / 2 / 1.4 / 170 / 1.0 $\times$ 10$^{16}$ / 1.45 |
| CH3NC/CH3CN ratio | 4.7e-3 | not stated | dimensionless | 1 | / 1.0 $\times$ 10$^{16}$ / 1.45 / 5.4 / -0.5 / 0.0047 / |
| HCCNC column density | 5.1e14 | not stated | cm^-2 | 1 | / HCCNC, $\varv=0$ / t / 2 / 1.3 / 170 / 5.1 $\times$ 10$^{14}$ / 1.55 |
| HCCNC/HC3N ratio | 1.5e-3 | not stated | dimensionless | 1 | $\sim$ 1.5 × 10^−3^ |
| C2H5NC column density upper limit | <1.5e15 | not stated | cm^-2 | 1 | $<$ 1.5 $\times$ 10$^{15}$ |
| Model 1 radiative transfer CH3NC/CH3CN | 5.2e-2 | not stated | dimensionless | 4 | / CH$_3$NC/CH$_3$CN / 4.7 × 10^−3^ / 5.2 × 10^−2^ |
| Model 4 CH3NC/CH3CN (radiative transfer) | 4.5e-3 | not stated | dimensionless | 4 | 4.2 × 10^−3^ / 4.5 × 10^−3^ |

## Qualitative findings

- Single-stage model yields very different abundances (e.g. strongly reduced HCCNC-related species) than two-stage model owing to time spent in key temperature ranges.  
  > "These significant chemical differences are directly related to the physical differences between the two modeling approaches." (6.2)
- HCCNC:HC3N is systematically overproduced by all models.  
  > "This appears to be due to a systematic overproduction of" (Conclusion)

## Claim tuples

- H: Isocyanides CH3NC and HCCNC are present in Sgr B2(N2) | E: LTE modeling of EMoCA spectra | R: Two uncontaminated/associated lines each matched | F: Tentative detections of CH3NC and HCCNC | **supported**
- H: Enhanced extinction-dependent zeta improves agreement with observations | E: Seven chemical models plus radiative transfer | R: Model 4 reproduces CH3NC:CH3CN almost exactly; high constant zeta poor | F: Enhanced Av-dependent zeta preferred | **supported**
- H: Models reproduce observed column densities | E: Radiative transfer of model abundances | R: Column densities much lower than observed | F: Models underproduce complex molecules or physical profile inaccurate | **refuted**

## Reasoning

- Why this data: EMoCA data are used since N2 has narrow lines reducing confusion.  
  > "narrow line widths ameliorate the line confusion problem" (abstract)
- Why this method: _not stated_
- Alternative: Two-stage hot-core model compared and found less appropriate.  
  > "The new physical model used throughout this paper is more directly relevant to the source structure of Sgr B2(N2)" (6.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Physical profile, spherical symmetry, LTE and network inaccuracies may cause column density mismatch.  
  > "It is possible that the physical profiles (density and temperature) that are being used in the spectroscopic model are not physically representative of the actual source." (7.3)
- Caveat (inferred, ours): Detections rest on only two lines each and are tentative
- Caveat (inferred, ours): LTE fits by eye without uncertainties
- Caveat (inferred, ours): Observed column density comparisons vs radiative-transfer limited by ALMA spatial filtering
- Caveat (inferred, ours): Few models, no parameter sweep or statistical comparison

## Reproducibility

- Data public (paper): Interferometric data available in the ALMA archive  
  > "The interferometric data are available in the ALMA archive at https://almascience.eso.org/aq/." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Calibration/imaging recipe (in Belloche et al. 2016)
- Missing: MAGICKAL network and inputs
- Missing: Initial chemical abundances
- Data volume (inferred): Large (hundreds of GB for full EMoCA survey); a single-position spectrum is much smaller
- Score (inferred): 3/5, Data public and LTE approach clear, but processing is inherited and chemical code/network not released.
- Rediscovery candidate: no, Main results depend on inherited reduction and unreleased chemical code with by-eye fits.

## Links

- Method: Belloche et al. 2016 (cite: Belloche16) (EMoCA observations, reduction and LTE analysis method)
- Method: Garrod 2013 (cite: garrod13) (MAGICKAL and radiative transfer)
- Companion: Bonfand et al. 2019 (cite: bonfand19) (Physical profiles and cosmic-ray modeling of Sgr B2(N) hot cores)
- Companion: Calcutt et al. 2018 (cite: calcutt18) (Earlier CH3NC chemistry in network)
- Related: EMoCA

## Checks

```json
{
 "quotes": 59,
 "quotes_ok": 59,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 39,
  "rate": 0.527
 },
 "evidence_ok": true
}
```
