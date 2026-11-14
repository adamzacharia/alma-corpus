# A Subarcsecond ALMA Molecular Line Imaging Survey of the Circumbinary, Protoplanetary Disk Orbiting V4046 Sgr

`2018ApJ...863..106K` | The Astrophysical Journal 2018 | first author: Kastner, Joel H. | arXiv: 1806.10553 | DOI: 10.3847/1538-4357/aacff7

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: What is the molecular chemical structure (radial distribution of many molecules) of the circumbinary disk around V4046 Sgr, as seen in subarcsecond ALMA images?  
  > "Here, we bring together the results of these observations of the disk orbiting V4046 Sgr." (Introduction)
- Target **V4046 Sgr**: coordinates _not stated_; z/distance 72.47±0.34 pc  
  > "which lie at $D = 60.09\pm0.14$ pc and $72.47\pm0.34$ pc, respectively (cite: Gaia2018)" (Introduction); distance from Gaia (Gaia2018)  
  > "which lie at $D = 60.09\pm0.14$ pc and $72.47\pm0.34$ pc, respectively (cite: Gaia2018)" (Introduction)

## Data provenance

- ALMA projects: 2013.1.00226.S, 2015.1.00671.S, 2015.1.00678.S
- bands: Band 6 and Band 7 (1.1–1.4 mm)  
  > "The observations were undertaken in the 1.1–1.4 mm wavelength range (ALMA Bands 6 and 7)" (abstract)
- frequencies and spectral setup: 2015.1.00671.S: 262.9 GHz (2474 MHz, 231.9 kHz) and 265.9 GHz (618.6 MHz, 116 kHz); 2015.1.00678.S: seven Band 7 windows incl. continuum  
  > "The central frequency, bandwidth, and channel widths were 262.9 GHz, 2474 MHz, and 231.9 kHz, respectively, for the C$_2$H $N=3 \rightarrow 2$ transition" (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15–704 m (2015.1.00671.S); 20–640 m (2015.1.00678.S)  
  > "in a configuration with baselines in the range 15–704 m, on 20 June 2016" (Observations); "The configuration consisted of 41 antennae with baselines in the range 20–640 m." (Observations)
- angular resolution: beamwidths of 0.5–0.6'' chosen via robust  
  > "with values chosen to obtain beamwidths of 0.5–0.6$''$" (Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 613 s (2015.1.00671.S); 1200 s (2015.1.00678.S)  
  > "These observations were carried out during a 613 s integration with 41 antennas" (Observations); "Data for program 2015.1.00678.S were collected in a 1200 s integration on 2016 April 30." (Observations)
- observing dates: 20 June 2016 (2015.1.00671.S); 2016 April 30 (2015.1.00678.S)  
  > "Data for program 2015.1.00678.S were collected in a 1200 s integration on 2016 April 30." (Observations)
- pi or archival as stated: Programs with PIs Öberg, Kastner, Qi  
  > "2013.1.00226.S (Cycle 2; PI: K. Öberg), 2015.1.00671.S (Cycle 3; PI: J. Kastner), and 2015.1.00678.S (Cycle 3; PI: C. Qi)" (Observations)
- Line: C2H N=3→2 (262.00423 GHz)
- Line: HCN J=3→2 (265.88618 GHz)
- Line: N2H+ J=3→2 (279.5117 GHz)
- Line: 12CO J=2→1 (230.538 GHz)
- External data: Disk inclination 33.5 deg and position angle 67 deg  
  > "assuming a disk inclination $i=33.5^\circ$ and position angle of 67$^\circ$ (cite: Rosenfeld2013)" (3.2 Radial Profiles) [from (cite: Rosenfeld2013)]
- External data: Disk geometric parameters from SED fitting  
  > "with the disk geometric (i.e., scale height and surface density profile) parameters fixed to values previously determined via SED fitting for V4046 Sgr (cite: Rosenfeld2013)" (5.4 C2H ring) [from (cite: Rosenfeld2013)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.7.0  
  > "using standard tools available in CASA 4.7.0" (Observations)
- pipeline version: _not stated_
- archive products used as is: Initially calibrated by ALMA/NAASC staff, then additional calibration  
  > "Data for all three programs were initially calibrated by ALMA/NAASC staff." (Observations)
- flux calibrator: _not stated_
- flux scale uncertainty: minimum ~10% line flux uncertainties including systematic calibration  
  > "the minimum uncertainties are $\sim$10%, after accounting for typical systematic ALMA calibration errors" (Observations)
- self calibration: Phase and amplitude self-calibration on continuum; solutions applied to line channels  
  > "We then performed phase and amplitude self-calibration on the continuum visibilities." (Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs robust 0.0 (C2H, HCN); 0.5 (DCO+, 13CO, C18O, HC3N, CH3CN, HC15N, H13CN, H13CO+); 1.0 (12CO); 2.0 (DCN, H2CO, N2H+)  
  > "Briggs `robust` parameter set to 0.0 for C$_2$H and HCN; 0.5 for DCO$^+$, $^{13}$CO C$^{18}$O, HC$_3$N, CH$_3$CN, HC$^{15}$N, H$^{13}$CN, and H$^{13}$CO$^+$" (Table 1)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Uniform elliptical clean mask over all channels; cleaned per channel  
  > "The line data were cleaned per channel using a uniform elliptical clean mask encompassing the emission over all channels." (Observations)
- multiscale scales: _not stated_
- continuum subtraction: Average continuum from line-free channels subtracted  
  > "after subtracting the average continuum obtained from line-free channels" (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Self-calibration and imaging strategy  
  > "This basic self-calibration and imaging strategy is described in detail in (cite: Huang2017)" (Observations) [from (cite: Huang2017)]
- C2H modeling methodology  
  > "we have modeled the ring-like C$_2$H line emission following the methodology described in detail in (cite: Qi2013) and (cite: Kastner2015)" (5.4 C2H ring) [from (cite: Qi2013); (cite: Kastner2015)]
- Line flux uncertainty estimation  
  > "accounting for the radial extent of the emission in the moment 0 image as well as the linewidths (cite: Kastner2010)" (Observations) [from (cite: Kastner2010)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges per spectral window
- Self-calibration solution intervals and number of iterations
- Clean thresholds, cell and image sizes
- Channel ranges for moment maps
- Starting abundance/temperature and grid ranges for C2H model, and fit statistic
- Coordinates of V4046 Sgr
- Primary beam correction details

## Analysis recipe

1. **Self-calibrate and image continuum and line cubes**: Extract continuum from line-free channels, phase+amplitude self-cal, apply to lines, Briggs imaging, per-channel cleaning with elliptical mask  
  > "To summarize, the continuum visibilities were extracted by averaging the line-free channels in each spectral window." (Observations)
   - software: CASA
   - parameter: robust 0.0 to 2.0  
  > "using Briggs `robust` parameters ranging from 0.0 to 2.0" (Observations)
   - fitting: _not stated_
   - validation: Compared continuum, 12CO and 13CO fluxes with previous SMA imaging  
  > "Our integrated continuum and $^{12}$CO and $^{13}$CO line flux measurements are consistent with those obtained in previous SMA imaging of V4046 Sgr" (Observations)
2. **Make moment maps and radial profiles**: Moment 0 and 1 images; deprojected radial profiles of unclipped moment 0 with statistical errors  
  > "$\sigma_r = \sigma_{xy} \, (\sqrt{\Delta V / \delta v}) \, (1/\sqrt{N})$" (3.2 Radial Profiles)
   - parameter: i = 33.5 deg, PA = 67 deg  
  > "assuming a disk inclination $i=33.5^\circ$ and position angle of 67$^\circ$" (3.2 Radial Profiles)
   - assumption: Inclination 33.5 deg, PA 67 deg  
  > "assuming a disk inclination $i=33.5^\circ$ and position angle of 67$^\circ$" (3.2 Radial Profiles)
   - fitting: _not stated_
   - validation: _not stated_
3. **CO isotopologue ratio and optical depth**: Radial profiles of intensity ratios R_{1,2}(r) related to tau via isotopologue abundance ratio  
  > "given an assumed (constant) isotopologue abundance ratio $X_{1,2}$ within the disk" (5.1)
   - assumption: X12,13 ~40–70, X12,18 ~480  
  > "$X_{12,13}$ from $\sim$40 to $\sim$70, and $X_{12,18} \sim 480$" (5.1)
   - fitting: _not stated_
   - validation: Qualitative only  
  > "we restrict the present discussion to a qualitative analysis" (5.1)
4. **Empirical model of C2H ring**: Disk model with constant-abundance emitting layer bounded by column densities, radial power laws, RATRAN radiative transfer, visibility-space grid search  
  > "fitting to the interferometric molecular emission line data is performed in visibility space via a grid search approach" (5.4 C2H ring)
   - software: RATRAN
   - parameter: Free: Rin, Rout, p1, p2, R1 for given Z1, Z2; R0 = 10 AU  
  > "in this case, $R_{in}, R_{out}, p_1, p_2, R_1$, for a given $Z_1, Z_2$" (5.4 C2H ring)
   - assumption: D'Alessio accretion disk model matching SED  
  > "we adopt a physically self-consistent accretion disk model (cite: DAlessio2006) that matches the spectral energy distribution (SED)" (5.4 C2H ring)
   - fitting: Grid search in visibility space  
  > "fitting to the interferometric molecular emission line data is performed in visibility space via a grid search approach" (5.4 C2H ring)
   - validation: Compared model and ALMA moment 0 and line profile; uniqueness not assessed  
  > "as we have not employed a rigorous parameter space study, the robustness and uniqueness of this particular model fit" (5.4 C2H ring)

## Software

- **CASA** 4.7.0: Calibration, self-calibration and imaging  
  > "using standard tools available in CASA 4.7.0" (Observations)
- **RATRAN** : Radiative transfer for C2H model  
  > "radiative transfer calculations are carried out via the `RATRAN` code" (5.4 C2H ring)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| R12,13 (12CO:13CO ratio) | ~2.5 | not stated | dimensionless | 3 | with a value $R_{12,13} \sim 2.5$ |
| C2H best-fit inner radius | 30 | ~5 | AU | 4 | $R_{in} = 30$ AU and $R_{out}=130$ AU |
| C2H best-fit outer radius | 130 | ~5 | AU | 4 | $R_{in} = 30$ AU and $R_{out}=130$ AU |
| C2H emitting layer Z1, Z2 | 0.5, 1.5 | ~0.5 | dimensionless | 4 | The parameters of the best-fit model are $Z_1 = 0.5$, $Z_2 = 1.5$ |
| C2H power-law slopes p1, p2 and break R1 | p1=+0.6, p2=+1.8, R1=100 AU | not stated | dimensionless; AU | 4 | with a radial power-law slope of $p_1 = +0.6$ between 30 AU and 100 AU and a (much steeper) slope of $p_2 = +1.8$ |
| C2H 262.004/262.064 GHz intensity ratio | 1.37 | 0.1 | dimensionless | 4 | 1.37$\pm$0.1, is in good agreement with the theoretical ratio of 1.41 |
| 264 GHz continuum flux | 327 | 33 | mJy | 1 | 264  / $0.69''$$\times$$0.49''$ ($-$77$^\circ$) / 327$\pm$33 |

## Qualitative findings

- CO and HCN isotopologues centrally peaked; HC3N, CH3CN, DCN, DCO+, N2H+, C2H, H2CO form rings of increasing radius  
  > "appears as a sequence of sharp and diffuse rings" (abstract)

## Claim tuples

- H: Do HC3N and CH3CN trace dust rings? | E: Compared nitrile images with continuum and scattered light | R: Ring dimensions similar to continuum ring | F: Suggests photodesorption of organic ices from grains | **partially**
- H: Is the C2H ring in surface or deep layers? | E: Empirical column-density layer model fit in visibility space | R: Layer at z/r ~0.1–0.3, 30–130 AU | F: Favors gas-phase production, irradiation not ruled out | **partially**
- H: Are CO isotopologues optically thick? | E: Radial ratios of 12CO, 13CO, C18O | R: R12,13 ~2.5 constant | F: 12CO and 13CO optically thick, C18O thin | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): C2H model not a rigorous parameter study; uniqueness uncertain  
  > "the robustness and uniqueness of this particular model fit, as well as the precise uncertainties in the various model parameters, are difficult to assess" (5.4 C2H ring)
- Caveat (inferred, ours): Single-model grid search without error analysis
- Caveat (inferred, ours): Different beams across lines complicate comparisons
- Caveat (inferred, ours): Optical depth ratio analysis assumes constant abundance ratios

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Self-calibration parameters
- Missing: Moment channel ranges
- Missing: C2H model grid details and code setup
- Data volume (inferred): ~100–300 GB raw across three programs
- Score (inferred): 3/5, Data archival, imaging steps partly specified (robust values), but model setup and self-cal are deferred to other papers.
- Rediscovery candidate: no, Imaging recipe incomplete and C2H model details deferred to cited work.

## Links

- Method: (cite: Huang2017) (Self-calibration and imaging strategy)
- Method: (cite: Qi2013); (cite: Kastner2015) (C2H ring modeling methodology)
- Companion: Bergner et al. (2018) (HC3N and CH3CN from program 2013.1.00226.S)
- Companion: (cite: Guzman2017) (N isotopologues of HCN)

## Checks

```json
{
 "quotes": 60,
 "quotes_ok": 60,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2015.1.00226.S"
 ],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 40,
  "rate": 0.571
 },
 "evidence_ok": true
}
```
