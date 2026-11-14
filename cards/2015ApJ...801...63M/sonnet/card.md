# ALMA Multi-line Imaging of the Nearby Starburst NGC 253

`2015ApJ...801...63M` | The Astrophysical Journal 2015 | first author: Meier, David S. | arXiv: 1501.05694 | DOI: 10.1088/0004-637X/801/1/63

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, astrochemistry
- Question: What are the spatially resolved molecular line properties, chemistry, opacities and dense gas conditions across the central starburst of NGC 253 in the 3 mm band?  
  > "The primary goal is to obtain spatially resolved views of the different molecular environments in and around the starburst center." (Discussion)
- Target **NGC 253**: coordinates Map centre 00 47 33.100 -25 17 17.50 (J2000)  
  > "Throughout the paper we adopt a distance to NGC 253 of 3.5 Mpc (Rekola et al. 2005), i.e., 1$"$ corresponds to 17 pc at that distance." (Introduction); z/distance 3.5 Mpc; systemic velocity ~250 km/s  
  > "Throughout the paper we adopt a distance to NGC 253 of 3.5 Mpc (Rekola et al. 2005), i.e., 1$"$ corresponds to 17 pc at that distance." (Introduction); distance from Rekola et al. 2005  
  > "Throughout the paper we adopt a distance to NGC 253 of 3.5 Mpc (Rekola et al. 2005), i.e., 1$"$ corresponds to 17 pc at that distance." (Introduction)

## Data provenance

- ALMA projects: 2011.0.00172.S
- bands: 3 mm band (Band 3)  
  > "A total of 50 molecular lines are detected over a 13 GHz bandwidth imaged in the 3 mm band." (abstract)
- frequencies and spectral setup: Setup 1: 85.6–89.6 GHz LSB and 97.4–101.4 GHz USB; Setup 2: 99.8–103.7 GHz LSB and 111.8–115.7 GHz USB  
  > "The second setup covers 99.8–103.7 GHz (LSB) and 111.8–115.7 GHz (USB) and is a 7–point mosaic of NGC 253’s center in the compact configuration." (2 Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: Cycle 0, 16 antenna array  
  > "We have mapped NGC 253 with ALMA in cycle 0 (16 antenna array) in two different frequency setups and configurations." (2 Observations and Data Reduction)
- configurations: Extended (3-pointing mosaic) and compact (7-pointing mosaic)  
  > "is a central 3–point mosaic along the major axis in the extended configuration" (2 Observations and Data Reduction)
- baselines: _not stated_
- angular resolution: ~2" (~35 pc) extended; ~4" (~70 pc) compact  
  > "This yields an average beam size of $\sim$4$"$ ($\sim$70 pc)" (2 Observations and Data Reduction)
- max recoverable scale: uv range 12–47 kλ compact (4.4"–18"); 23–100 kλ extended (2"–9") at 90th percentile  
  > "In the compact (extended) configuration spatial scales of 12 – 47 k$\lambda$ (23 – 100 k$\lambda$) \[90th percentile\] were sampled, corresponding to 4.4$''$ – 18$''$ (2$''$ – 9$''$)." (2 Observations and Data Reduction)
- sensitivity: RMS ~2.0 mJy/beam at 20 km/s (ext LSB 1.9, ext USB 2.1, comp LSB 2.0, comp USB 3.3 mJy)  
  > "Our final cube has 20 km s$^{-1}$ velocity resolution and a typical RMS of $\sim$2.0 mJy beam$^{-1}$" (2 Observations and Data Reduction)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: HCN 1-0 (88.63160 GHz)
- Line: HCO+ 1-0 (89.18852 GHz)
- Line: C17O 1-0 (112.35928 GHz)
- Line: 12CO 1-0 (115.27120 GHz)
- External data: Single-dish fluxes used to estimate recovered flux fractions (e.g. HCN, HCO+, SiO, CN, C2H, HNCO)  
  > "HCN(1–0) — 100 % (Paglione et al 1995), HCO$^+$(1–0) — 55 % (Martin et al. 2009)" (2 Observations and Data Reduction) [from Paglione et al 1995; Martin et al. 2009; Henkel et al. 2014; Nakajima et al. 2011; Nguyen-Q-Rieu et al. 1991]
- External data: Distance 3.5 Mpc  
  > "we adopt a distance to NGC 253 of 3.5 Mpc (Rekola et al. 2005)" (Introduction) [from Rekola et al. 2005]
- External data: Collisional rate coefficients from Leiden LAMDA database for LVG  
  > "collisional coefficients adapted from the Leiden LAMDA database (van der Tak et al. 2007; see Table 4 for references to the individual molecular rate coefficients)" (4.2 Dense Gas Tracers) [from van der Tak et al. 2007]

## Processing

### Calibration

- pipeline or manual: Calibration and imaging in CASA, details in B13 and L14  
  > "All of the calibration and imaging of the data cubes was completed within CASA, including self–calibration to remove residual phase and flux calibration errors." (2 Observations and Data Reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Self-calibration applied for residual phase and flux errors  
  > "including self–calibration to remove residual phase and flux calibration errors" (2 Observations and Data Reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Line cubes blanked with a mask derived from CO(1-0); integrated intensity by summing without flux cutoff  
  > "We created line cubes for each line, and then blanked those with a mask derived from the CO(1-0) line" (2 Observations and Data Reduction)
- multiscale scales: _not stated_
- continuum subtraction: Continuum defined in spectral regions with no evident line emission; continuum-subtracted cube used  
  > "where the continuum was defined in those spectral regions where no line emission was evident" (2 Observations and Data Reduction)
- line free channels: _not stated_
- primary beam correction: Integrated line maps corrected for primary beam attenuation  
  > "Integrated line maps are corrected for primary beam attenuation and are shown in Fig. [3](#Fmap)." (2 Observations and Data Reduction)
- array combination: _not stated_
- smoothing: Maps convolved to a common resolution per configuration for measurements  
  > "all the compact and extended configuration data have been convolved to a common resolution, respectively" (3.1 The Nucleus of NGC 253)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Observation and data reduction details  
  > "Details regarding the observations and data reduction can be found in B13 and L14" (2 Observations and Data Reduction) [from Bolatto et al. 2013 (B13); Leroy et al. 2014 (L14)]
- CO(1-0) data, zero-spacing corrected  
  > "has been zero-spacing corrected and therefore detects all flux (see discussion in B13)" (2 Observations and Data Reduction) [from B13]

### Not stated but needed to reproduce (our reading)

- CASA version and calibrators
- Imaging weighting/robust, cell and image size, deconvolver, clean thresholds
- Line-free channels for continuum
- Exact beam-matching common resolution per line and mask details
- LVG code availability and grid ranges
- Exact line widths/velocity ranges used for integrated intensities

## Analysis recipe

1. **Build line cubes and integrated intensity maps**: Continuum-subtract, make per-line cubes, mask with CO(1-0), sum all data, primary-beam correct  
  > "The integrated intensity map for a given line was then derived by simply adding all data in the respective data cube (without any further flux cutoff)." (2 Observations and Data Reduction)
   - software: CASA, IDL, Miriad, Matlab
   - fitting: _not stated_
   - validation: Compared recovered flux with single-dish values (>=50%)  
  > "it appears that the data consistently detect at least 50 % of their respective single dish fluxes" (2 Observations and Data Reduction)
2. **Measure line intensities at 10 regions and assign uncertainties**: Peak integrated intensity from beam-matched maps; 10% error for S/N>10, 30% for 5<S/N<10, ignore S/N<5  
  > "We thus adopt a conservative 10% error for pixels that have been detected at high $S$/$N$ ($>10$)" (2 Observations and Data Reduction)
   - software: IDL
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive excitation temperature, column densities and abundances**: Optically thin LTE column densities; Tex from SO(32-21)/SO(22-11) ratio; N(H2) from CO(1-0) with XCO  
  > "Molecular column densities $N_{mol}$ are determined assuming optically thin LTE emission" (3.4 Excitation and Abundances)
   - parameter: Abundances reported for Tex 10–75 K  
  > "abundances are reported for T$_{ex}$ ranging from 10 K (first number in each entry) to 75 K (second number)" (3.4 Excitation and Abundances)
   - assumption: XCO = 0.5e20 cm-2 (K km/s)-1, uncertain at ±2x  
  > "We adopt a CO-to-H$_{2}$ conversion factor of X$_{CO} = 0.5\times 10^{20}$ cm$^{-2}$ (K km s$^{-1}$)$^{-1}$." (3.4 Excitation and Abundances)
   - fitting: _not stated_
   - validation: C17O/H2 compared with expected value from [CO/C17O]=1000 and [CO/H2]=1e-4  
  > "The level of agreement between the two methods of constraining N(H$_{2}$) is reasonable, being less than the uncertainties in each method." (4.1 CO Isotopologues)
4. **Estimate optical depths from isotopologue line ratios**: Compare CO/C17O, HCN/H13CN, HCO+/H13CO+ ratios with adopted abundance ratios  
  > "For $A= ^{12}$C/$^{13}$C abundance ratios of 80 above and LTE assumptions, both HCN and HCO$^+$ have $\tau \simeq 5-8$." (4.2 Dense Gas Tracers)
   - assumption: [CO/C17O]=1000 nominal; 12C/13C = 80  
  > "so we adopt \[CO/C$^{17}$O\] = 1000" (4.1 CO Isotopologues)
   - fitting: _not stated_
   - validation: _not stated_
5. **LVG modelling of dense gas isotopologue ratios**: Independent LVG radiative transfer modelling of line ratios, patterned after Meier et al. 2008, Jmax=20  
  > "The model used is patterned after the models of Meier et al. (2008), with J$_{max}$ extended to 20" (4.2 Dense Gas Tracers)
   - software: LVG code (Meier et al. 2008)
   - parameter: Abundance per velocity gradient 10^-11.33 to 10^-7.67 km-1 s pc explored  
  > "Models with a wide range of abundance per velocity gradient ($10^{-11.33}-10^{-7.67}$ km$^{-1}$ s pc) were calculated." (4.2 Dense Gas Tracers)
   - fitting: Grid comparison of five isotopic ratios averaged over positions 5 and 7; no formal sampler  
  > "Figure [2](#Flvg) displays the acceptable parameter space for the ratios observed toward the inner nuclear disk (average of the ratios toward positions 5 and 7)" (4.2 Dense Gas Tracers)
   - validation: Compared with Knudsen et al. 2007 results  
  > "The favored densities and kinetic temperatures of the dense gas isotopologues match well those previously found in Knudsen et al. (2007)" (4.2 Dense Gas Tracers)

## Software

- **CASA** : Calibration, self-calibration and imaging  
  > "All of the calibration and imaging of the data cubes was completed within CASA" (2 Observations and Data Reduction)
- **IDL** : Post-imaging analysis scripts  
  > "much of the remaining analysis was performed with IDL scripts with some use of the Miriad and Matlab software packages" (2 Observations and Data Reduction)
- **Miriad** : Some analysis  
  > "with some use of the Miriad and Matlab software packages" (2 Observations and Data Reduction)
- **Matlab** : Some analysis  
  > "with some use of the Miriad and Matlab software packages" (2 Observations and Data Reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Lines detected | 50 (27 unambiguous) | not stated | lines | 1 | We detect at least 50 emission lines in total of which 27 have unambiguous identifications. |
| SO-derived Tex inner disk | 74 | not stated | K | 3 | we estimate the inner disk to have an excitation temperature of 74 K in SO |
| CO(1-0) opacity | ~2.5 (for 16O/17O=1000); ~5.5 for 2000 | not stated | dimensionless | 4 | the measured ratio nominally implies a $^{12}$CO opacity of $\sim$2.5, a moderate value for the main CO line. |
| HCN and HCO+ opacity (LTE) | 5-8 | not stated | dimensionless | 4 | both HCN and HCO$^+$ have $\tau \simeq 5-8$ |
| LVG best-fit density and Tkin | n_H2 = 10^4.75 cm-3, Tkin = 80 K | n 10^4.5-5.0, T 60-120 K | cm-3; K | 5 | good agreement to all five ratios is obtained for $n_{H_{2}} = 10^{4.5 - 5.0}$ cm$^{-3}$ and T$_{kin} = 60 - 120$ K. |
| HNCO/SiO ratio inner disk | ~0.17 | not stated | dimensionless | 2 | Towards the inner disk the ratio drops dramatically to a value of $\sim$0.17. |
| H40α/H50β ratio | ~3.5 | not stated | dimensionless | 2 | the global H40$\alpha$/H50$\beta$ ratio is around 3.5 |

## Qualitative findings

- HNCO is dominated by the outer nuclear disk, unlike SiO which is enhanced across the nucleus  
  > "HNCO has the most distinctive morphology of all the bright lines, being completely dominated by the outer locations of the disk." (4.4 Shock Tracers)

## Claim tuples

- H: Are the CO(1-0) lines highly optically thick in NGC 253? | E: Compared CO/C17O line ratio with assumed abundance ratio | R: CO/C17O ≳350; opacity ~2.5–5.5 | F: 12CO(1-0) has only moderate optical depth | **supported**
- H: Are HCN(1-0) and HCO+(1-0) optically thick? | E: Compared with 13C isotopologues and LVG modelling | R: HCN/H13CN and HCO+/H13CO+ are 10–15, below 12C/13C | F: Opacities at least comparable to CO(1-0) | **supported**
- H: Does HNCO/SiO variation reflect shock strength? | E: Compared HNCO and SiO maps with PDR tracers | R: HNCO/SiO drops to ~0.17 in inner disk while SiO stays high | F: Shock signatures of HNCO erased by radiation fields in the centre | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Error maps too optimistic; negative bowl from missing short spacings; region 6 fluxes highly uncertain due to absorption  
  > "Because of this the fluxes toward this location should be considered highly uncertain." (2 Observations and Data Reduction)
- Caveat (inferred, ours): Abundances depend on assumed Tex and XCO with factor-of-few uncertainty
- Caveat (inferred, ours): Missing flux varies by line and is not corrected
- Caveat (inferred, ours): LVG uses uniform conditions and a fixed 12C/13C

## Reproducibility

- Data public (paper): ALMA project 2011.0.00172.S cited  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA #2011.0.00172.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters and CASA version
- Missing: LVG code
- Missing: Precise integration windows
- Data volume (inferred): ~50-200 GB raw for Cycle 0 Band 3 mosaics
- Score (inferred): 3/5, Data public and measurements tabulated, but reduction details deferred to other papers and imaging parameters missing.
- Rediscovery candidate: no, Processing details are inherited from B13/L14 and not stated, though the data are public.

## Links

- Method: Bolatto et al. 2013 (B13) (Observations and data reduction)
- Method: Leroy et al. 2014 (L14) (Observations and data reduction)
- Method: Meier et al. 2008 (LVG model basis)
- Companion: Bolatto et al. 2013, Nature, 499, 450 (Molecular outflow in CO from same dataset)
- Companion: Leroy et al. 2014 (Molecular clump properties from same dataset)

## Checks

```json
{
 "quotes": 58,
 "quotes_ok": 58,
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
  "facts": 73,
  "stated": 42,
  "rate": 0.575
 },
 "evidence_ok": true
}
```
