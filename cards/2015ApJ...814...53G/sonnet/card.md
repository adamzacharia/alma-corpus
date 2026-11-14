# Cyanide Photochemistry and Nitrogen Fractionation in the MWC 480 Disk

`2015ApJ...814...53G` | The Astrophysical Journal 2015 | first author: Guzmán, V. V. | arXiv: 1511.03313 | DOI: 10.1088/0004-637X/814/1/53

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Do CN and HCN have different radial abundance profiles in Herbig Ae vs T Tauri disks (photochemistry), and what is the 14N/15N ratio in the MWC 480 disk?  
  > "To address the utility of HCN as a probe of disks, we present ALMA observations of CN, HCN, H$^{13}$CN and HC$^{15}$N toward the protoplanetary disk around Herbig Ae star MWC480" (abstract)
- Target **MWC 480**: coordinates _not stated_; z/distance 140 pc  
  > "Both stars are located in the Taurus star forming region at a distance of 140 pc" (Introduction); distance from _not stated_
- Target **DM Tau**: coordinates _not stated_; z/distance 140 pc  
  > "Both stars are located in the Taurus star forming region at a distance of 140 pc" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: _none stated_
- bands: Band 7 (CN, HCN); Band 6 (H13CN, HC15N)  
  > "The Band 7 observations were carried out in October 2012 with 23 antennas." (2.1 CN and HCN); "In brief, the Band 6 observations were carried out in June 2014 with 33 antennas" (2.2 H13CN and HC15N)
- frequencies and spectral setup: Band 7: two 468 MHz windows, 122 kHz resolution; Band 6: two 59 MHz windows, 61 kHz spacing  
  > "Two spectral windows of 468 MHz bandwidth and 122 kHz spectral resolution were centered on the CN and HCN lines." (2.1 CN and HCN); "Two spectral windows of 59 MHz bandwidth and 61 kHz channel spacing" (2.2 H13CN and HC15N)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 21-384 m (Band 7); 18-650 m (Band 6)  
  > "the baselines lengths ranged between 21 and 384 m" (2.1 CN and HCN); "baseline lengths spanning between 18 and 650 m" (2.2 H13CN and HC15N)
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 34 min (Band 7); 24 min (Band 6)  
  > "The total on-source observing time was 34 min" (2.1 CN and HCN); "The total on-source observing time was 24 min." (2.2 H13CN and HC15N)
- observing dates: October 2012 (Band 7); June 2014 (Band 6)  
  > "The Band 7 observations were carried out in October 2012 with 23 antennas." (2.1 CN and HCN)
- pi or archival as stated: Archival; Cycle 0 PI E. Chapillon, Cycle 2 PI K.I. Öberg  
  > "retrieved from the public archive" (2.1 CN and HCN)
- Line: CN N=3-2, J=7/2-5/2 (340.24777 GHz)
- Line: HCN J=4-3 (354.50548 GHz)
- Line: H13CN J=3-2 (259.0118 GHz)
- Line: HC15N J=3-2 (258.1571 GHz)
- External data: Disk scale height and gas surface density parameters for MWC 480 model  
  > "Scale height | $H_{100}$ | 16 AU" (Table 2) [from (cite: guilloteau2011)]
- External data: Temperature structure T100=23 K, q=0.5  
  > "Temperature | $T_{100}$ | 23 K" (Table 2) [from (cite: pietu2007)]
- External data: HCN collision rates  
  > "collision rates from (cite: dumouchel2010) for HCN and from (cite: lique2010) for CN" (3.1) [from (cite: dumouchel2010)]
- External data: CN collision rates  
  > "collision rates from (cite: dumouchel2010) for HCN and from (cite: lique2010) for CN" (3.1) [from (cite: lique2010)]

## Processing

### Calibration

- pipeline or manual: Calibrated by ALMA staff with standard procedures; further self-calibration in CASA  
  > "The data were calibrated by the ALMA staff using standard procedures, and retrieved from the public archive." (2.1 CN and HCN)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J01510-180 (Band 7); J0510+1800 (Band 6)  
  > "J01510-180 was used to derive the absolute flux scale." (2.1 CN and HCN); "The same quasar was used to derive the absolute flux scale, as no planet was available during the observations." (2.2 H13CN and HC15N)
- flux scale uncertainty: _not stated_
- self calibration: Phase and amplitude self-cal on continuum, applied to each spectral window; Band 6 described in Öberg et al. 2015  
  > "We further self-calibrated the data in phase and amplitude in CASA, taking advantage of the bright continuum emission in both sources." (2.1 CN and HCN)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs robust 0.5 (CN, HCN); robust 1.0 (H13CN, HC15N)  
  > "with Briggs weighting and a robust parameter of 0.5" (2.1 CN and HCN); "cleaned in CASA using a robust parameter of 1.0" (2.2 H13CN and HC15N)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Clean mask per channel on line emission  
  > "A clean mask was created for each channel to select only regions with line emission during the cleaning process." (2.1 CN and HCN)
- multiscale scales: _not stated_
- continuum subtraction: Subtracted from visibilities using line-free channels  
  > "The continuum was then subtracted from the visibilities using channels free of line emission to produce the spectral line cubes." (2.1 CN and HCN)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: ~0.6 arcsec; see Table 1  
  > "resulting in an angular resolution of $0.6''$" (2.1 CN and HCN)
- final rms: _not stated_

### Inherited from earlier work

- Band 6 phase/amplitude calibration and self-calibration  
  > "A description of the phase and amplitude calibration, as well as the self-calibration, can be found in (cite: oberg2015)." (2.2 H13CN and HC15N) [from (cite: oberg2015)]
- Modeling procedure and disk density/temperature structure  
  > "using the procedure and disk density and temperature structure described in (cite: oberg2015)" (3.1) [from (cite: oberg2015)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for continuum subtraction
- Self-calibration solution intervals and reference antenna
- CASA version
- Cell size, image size, clean threshold
- Grid step sizes, LIME settings (photons, grid points)
- Vertical abundance structure assumed in the models
- Flux calibrator flux values
- Definition of the Keplerian mask

## Analysis recipe

1. **Self-calibrate, subtract continuum and image line cubes**: Self-cal on continuum in CASA, continuum subtraction, CLEAN with Briggs weighting  
  > "The images were obtained by deconvolution of the visibilities using the CLEAN algorithm in CASA" (2.1 CN and HCN)
   - software: CASA
   - parameter: robust 0.5 (CN, HCN), 1.0 (H13CN, HC15N)  
  > "cleaned in CASA using a robust parameter of 1.0" (2.2 H13CN and HC15N)
   - fitting: _not stated_
   - validation: _not stated_
2. **Radial profiles and half-light radii**: Azimuthally averaged radial profiles of velocity-integrated maps  
  > "azimuthally averaged radial profiles of the CN and HCN lines towards MWC 480 and DM Tau" (3.1)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit abundance profiles with radiative transfer model**: Power-law abundance X=X0(r/R0)^alpha with outer cut-off Rout, non-LTE LIME models, chi2 fit to visibilities on a grid  
  > "The model fitting was done in the $u-v$ plane by computing $\chi^2$, the weighted difference between model and observations" (3.1)
   - software: LIME
   - parameter: 50<Rout/AU<500, -2<alpha<2, 1e-14<X100<1e-9, R0=100 AU  
  > "outer radius $50<\ensuremath{R_\ensuremath{\mathrm{out}}}/\mathrm{AU}<500$, power-law indexes $-2<\alpha<2$" (3.1)
   - assumption: Disk structure from Table 2 (Guilloteau 2011, Pietu 2007); HCN collision rates used for isotopologues  
  > "For the HCN isotopologues, we use the collisional rates of HCN." (3.1)
   - fitting: chi2 minimization on grid; errors are 7 sigma  
  > "The best-fit models were obtained by minimizing $\chi^2$." (3.1)
   - validation: Residual maps and disk-integrated spectra with Keplerian mask  
  > "Except for the low-velocity CN channels there are no significant residuals" (3.1)
4. **Derive 14N/15N ratio**: H13CN/HC15N abundance ratio times 12C/13C=70, H13CN as proxy since HCN partially optically thick  
  > "Assuming an isotopic ratio of $^{12}$C/$^{13}$C$=70$, we derive a disk HCN isotopologue ratio HC$^{14}$N/$\ensuremath{\mathrm{HC^{15}N}}=200\pm110$." (3.2)
   - assumption: Isotopologues co-spatial, optically thin; 30% uncertainty on 12C/13C  
  > "we included a 30% uncertainty in the C isotopic ratio" (3.2)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Self-calibration, continuum subtraction, CLEAN imaging  
  > "We further self-calibrated the data in phase and amplitude in CASA" (2.1 CN and HCN)
- **LIME** : Non-LTE radiative transfer for line emission  
  > "The line emission was calculated using the radiative transfer code LIME (cite: brinch2010) assuming non-LTE excitation" (3.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HCN outer cut-off radius, MWC 480 | 110 | ±10 | AU | 3 | $R_\ensuremath{\mathrm{out}}$ \[AU\] / $>300$ / $110\pm 10$ |
| CN outer cut-off radius, MWC 480 | >300 | not stated | AU | 3 | while the outer-radius of the CN emission is constrained to $>300$ AU |
| Half-light radius HCN / CN, MWC 480 | 66 / 102 | not stated | AU | 2 | The best-fit half-light radius for the HCN and CN emission toward MWC 480 are 66 and 102 AU, respectively. |
| Half-light radius HCN / CN, DM Tau | 151 / 158 | not stated | AU | 2 | toward DM Tau the best-fit half-radius for HCN and CN are similar, 151 and 158 AU, respectively |
| H13CN/HC15N abundance ratio | 2.8 | ±1.4 | dimensionless | 3 | This abundance ratio is 2.8$\pm$1.4 |
| 14N/15N ratio, MWC 480 | 200 | ±100 (±110 in text) | dimensionless | 4 | We find a low disk averaged $\mathrm{^{14}N/^{15}N}$ ratio of 200$\pm$100 |
| X0 CN / HCN | 8.5e-11 / 5.2e-12 | ±1.5e-11 / ±0.7e-12 | wrt total H at 100 AU | 3 | $(8.5\pm 1.5)\times 10^{-11}$ / $(5.2\pm 0.7)\times 10^{-12}$ |

## Qualitative findings

- First detection of HC15N in a disk; CN extends >1 arcsec beyond HCN cut-off in MWC 480 but not in DM Tau.  
  > "including the first detection of HC$^{15}$N in a disk" (abstract)

## Claim tuples

- H: CN is more radially extended than HCN in Herbig Ae disk due to HCN photodissociation | E: Radial profiles and visibility-plane abundance modeling of MWC 480 | R: Rout HCN 110±10 AU vs CN >300 AU | F: Consistent with efficient HCN photodissociation in outer disk | **supported**
- H: T Tauri disk shows the same CN/HCN difference | E: Compare DM Tau profiles | R: Half-light radii 151 vs 158 AU | F: Different photochemical structure in T Tauri disks | **supported**
- H: Nitrogen fractionation in MWC 480 disk is high | E: H13CN and HC15N modeling | R: 14N/15N = 200±100 | F: Comparable to comets and cold cores; inheritance and/or efficient fractionation | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Robust 1.0 chosen to improve SNR of weak isotopologue lines while keeping resolution  
  > "This selection of robustness parameter allowed us to improve the signal-to-noise ratio of the weak $\mathrm{H^{13}CN}$ and $\mathrm{HC^{15}N}$ lines" (2.2 H13CN and HC15N)
- How they decided it was enough: _not stated_
- Limitation (authors): Absolute abundances highly model dependent owing to unknown vertical abundance profile  
  > "they are highly model dependent, i.e. they depend strongly on the assumed vertical abundance profile" (3.1)
- Caveat (inferred, ours): Error bars are 7 sigma-based and ad hoc, not a posterior
- Caveat (inferred, ours): Single 12C/13C value assumed
- Caveat (inferred, ours): Second CN hyperfine component not modeled
- Caveat (inferred, ours): Optically thin assumption for H13CN/HC15N untested
- Caveat (inferred, ours): Fixed disk structure from literature

## Reproducibility

- Data public (paper): Band 7 data retrieved from public archive  
  > "retrieved from the public archive" (2.1 CN and HCN)
- Products in archive: _not stated_
- Missing: Self-calibration parameters
- Missing: Line-free channels
- Missing: Imaging pixel/size/threshold
- Missing: LIME run settings
- Missing: Full model details in Öberg et al. 2015
- Data volume (inferred): ~20-50 GB
- Score (inferred): 5/5, Public data and key settings (robust, model grid) given, but self-cal, channel selection and model details are deferred to another paper or omitted.
- Rediscovery candidate: no, Recipe relies on unstated self-calibration and the Öberg et al. 2015 modeling procedure.

## Links

- Method: (cite: oberg2015) (Calibration, self-calibration and disk model procedure)
- Companion: (cite: oberg2015) (Same MWC 480 Band 6 survey data)

## Checks

```json
{
 "quotes": 59,
 "quotes_ok": 59,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00629.S",
  "2013.1.00226.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 38,
  "rate": 0.528
 },
 "evidence_ok": true
}
```
