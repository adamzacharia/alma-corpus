# Sulfur-bearing Species Tracing the Disk/Envelope System in the Class I Protostellar Source Elias 29

`2019ApJ...881..112O` | The Astrophysical Journal 2019 | first author: Oya, Yoko | arXiv: 1906.09724 | DOI: 10.3847/1538-4357/ab2b97

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: What are the physical and chemical structures (S-bearing species, organic molecules, rotation) of the disk/envelope system of the Class I protostar Elias 29 at subarcsecond resolution?  
  > "Here we report the physical and chemical structures of the disk/envelope system at" (1. Introduction); "subarcsecond resolution with the Atacama Large Millimeter/submillimeter Array (ALMA)." (1. Introduction)
- Target **Elias 29 (WL 15)**: coordinates field center (J2000) 16h27m09.44s, -24d37'19.99"  
  > "Elias 29 (WL 15) is a Class I protostar in the L1688 dark cloud in Ophiuchus (Elias" (1. Introduction); "whose distance is 137 pc (Ortiz-Le´on et al. 2017)." (1. Introduction); "The field center of the observations was" (2. Observations); z/distance 137 pc  
  > "Elias 29 (WL 15) is a Class I protostar in the L1688 dark cloud in Ophiuchus (Elias" (1. Introduction); "whose distance is 137 pc (Ortiz-Le´on et al. 2017)." (1. Introduction); "The field center of the observations was" (2. Observations); distance from Ortiz-León et al. 2017  
  > "Elias 29 (WL 15) is a Class I protostar in the L1688 dark cloud in Ophiuchus (Elias" (1. Introduction); "whose distance is 137 pc (Ortiz-Le´on et al. 2017)." (1. Introduction); "The field center of the observations was" (2. Observations)

## Data provenance

- ALMA projects: 2013.1.01102.S
- bands: Band 6  
  > "were observed with the Band 6 receiver, and the basic parameters of the observations are listed in Table" (2. Observations)
- frequencies and spectral setup: 16 spectral windows, 61.035 kHz resolution (0.073 km/s at 250 GHz), 58.5938 MHz per window  
  > "Sixteen spectral windows were observed with a backend correlator tuned" (2. Observations); "and the bandwidth of each window" (2. Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15.1 m to 519.8 m  
  > "The baselines ranged from 15.1 m to 519.8 m." (2. Observations)
- angular resolution: continuum beam 0.856" x 0.470" (P.A. 95.17 deg)  
  > "0 _[′′]_ _._ 856 _×_ 0 _[′′]_ _._ 470 (P.A. 95. _[◦]_ 17)" (3.1 1.2 mm Continuum Emission)
- max recoverable scale: ~6"  
  > "whose maximum recoverable size is _∼_ 6 _[′′]_ ." (4.1 Deficiency in Organic Molecules)
- sensitivity: rms 0.3 mJy/beam continuum; 7, 7, 4, 6, 4 mJy/beam for CS, SO, 34SO, SO2, SiO  
  > "The root-mean-square (rms) noise level was 0.3 mJy beam _[−]_ [1] for the" (2. Observations)
- time on source: 22.27 minutes  
  > "The total on-source time was 22.27 minutes." (2. Observations)
- observing dates: 2015 May 18, Cycle 2  
  > "The ALMA observations of Elias 29 were carried out on 2015 May 18 with 37 antennas" (2. Observations)
- pi or archival as stated: _not stated_
- Line: CS, SO, 34SO, SO2, SiO SO 6_7-5_6; SO2 10_3,7-10_2,8; SiO J=6-5; others in Table 1 (not stated)
- External data: Dust temperature distribution model (~70 K at 40 au, ~25 K at 500 au) used to assume gas temperature  
  > "dust temperature is about 70 K at a distance of 40 au from the protostar." (3.1 1.2 mm Continuum Emission) [from Rocha & Pilling 2018]
- External data: Dust mass opacity kappa = 1.3 cm2/g at 1.2 mm  
  > "is estimated" (3.1 1.2 mm Continuum Emission) [from Ossenkopf & Henning (1994)]
- External data: Abundance ratios for comparison (L1157 B1, NGC1333 IRAS 2, IRAS 16293 B)  
  > "Table 4 also shows previously reported results for comparison: the shocked outflow" (3.3 Abundance Ratios of the S-bearing Species) [from Bachiller & Pérez Gutiérrez 1997; Wakelam et al. 2005; Drozdovskaya et al. 2018]
- External data: NGC1333 IRAS 4A organic-molecule abundances for comparison  
  > "fractional abundances or their upper limits reported for NGC1333 IRAS 4A1 and A2 by" (4.1 Deficiency in Organic Molecules) [from López-Sepulcre et al. 2017]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (bandpass J1517-2422, phase J1625-2527)  
  > "An absolute flux density scale was derived" (2. Observations)
- flux scale uncertainty: 10% for Band 6  
  > "The absolute accuracy of the flux calibration was 10% for Band 6 (Lundgren" (2. Observations)
- self calibration: not applied  
  > "Self-calibration was not applied, for simplicity." (2. Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust 0.5  
  > "Images were obtained with the CLEAN algorithm using Briggs weighting with a robust" (2. Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum subtracted in visibility data; 1.2 mm continuum from line-free channels  
  > "A 1.2 mm continuum image was obtained by averaging line-free channels." (2. Observations)
- line free channels: _not stated_
- primary beam correction: applied to continuum and line maps  
  > "A primary beam correction was applied for the" (2. Observations)
- array combination: _not stated_
- smoothing: channel width 0.5 km/s for 34SO and SiO, 0.1 km/s for others  
  > "The line maps were obtained after subtracting the continuum component directly from the visibility data by resampling to make the channel width 0.5 km s _[−]_ [1] for [34] SO and SiO or 0.1" (2. Observations)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Disk-envelope kinematic model approach (simplified PV model without radiative transfer)  
  > "this simplified model is useful, as found for other sources (e.g. Oya et al. 2017; Okoda et al. 2018)" (5.2 Analysis of Rotation) [from Oya et al. 2017; Okoda et al. 2018]
- H2 column density equation  
  > "is obtained from the following equation (Ward-Thompson et" (3.1 1.2 mm Continuum Emission) [from Ward-Thompson et al. 2000]

### Not stated but needed to reproduce (our reading)

- Number of channels/line-free channel ranges for continuum
- Image size and cell size
- CASA version and calibration pipeline
- Clean threshold/mask and number of iterations
- Partition functions / molecular data source and line parameters used for LTE column densities
- Details of the PV model beyond mass, inclination, PA, radius 100 au (velocity broadening, grid)
- Spectral window to line assignment (Table 1 not in text)

## Analysis recipe

1. **Image continuum and lines**: CLEAN imaging with Briggs weighting, continuum subtraction in uv, primary beam correction  
  > "Images were obtained with the CLEAN algorithm using Briggs weighting with a robust" (2. Observations)
   - parameter: robust 0.5; channel widths 0.5 or 0.1 km/s  
  > "parameter of 0.5." (2. Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Continuum fit and H2 column density/mass**: 2D Gaussian fit of continuum; N(H2) from optically thin dust emission equation  
  > "The peak position of the continuum emission was determined" (3.1 1.2 mm Continuum Emission)
   - parameter: kappa_nu = 1.3 cm2/g at 1.2 mm; dust-to-gas 0.01  
  > "dust-to-gas mass ratio (0.01)" (3.1 1.2 mm Continuum Emission)
   - assumption: Ossenkopf & Henning dense-region MRN opacity; beta=1.0 alternative gives factor 2 smaller  
  > "we chose" (3.1 1.2 mm Continuum Emission)
   - fitting: 2D Gaussian fit; errors 3 sigma  
  > "where the errors represent three standard deviations (3 _σ_ ) of the fit." (3.1 1.2 mm Continuum Emission)
   - validation: _not stated_
3. **Molecular column densities and abundance ratios**: LTE, optically thin 34SO; SO from 34SO with 32S/34S = 22.6; Gaussian fit of integrated intensity maps  
  > "determine the column density and fractional abundance of [34] SO by assuming optically thin" (3.2.1 SO, SO2, and SiO)
   - parameter: Tgas 50-150 K at the continuum peak; 100 K adopted for ratios; 20 K in ridge  
  > "We hereafter assume a gas temperature of 100 K for the continuum peak" (3.3 Abundance Ratios of the S-bearing Species)
   - assumption: Gas temperature equals dust temperature  
  > "The gas and dust temperatures are assumed to be equal." (Table 3)
   - fitting: _not stated_
   - validation: _not stated_
4. **Upper limits for organic molecules**: Upper limits from rms of integrated intensity maps compared with IRAS 4A  
  > "are determined from the rms noise levels of their integrated intensity maps in Figure" (4.1 Deficiency in Organic Molecules)
   - fitting: _not stated_
   - validation: _not stated_
5. **Rotation and protostellar mass**: Moment 1 and PV diagrams of SO; compare with Keplerian disk model PV  
  > "Figure 9 shows the PV diagrams simulated by using the Keplerian disk model" (5.2 Analysis of Rotation)
   - parameter: M=1.0 Msun, i=65 deg, PA 0 deg, radius 100 au, emissivity r^-2.0  
  > "the protostellar mass is 1.0 _M_ _⊙_, the inclination angle of the disk/envelope system is 65 _[◦]_ (0 _[◦]_ for" (5.2 Analysis of Rotation)
   - assumption: Keplerian rotation, no radiative transfer; M = 0.82 Msun / sin^2 i  
  > "we hereafter assume that the observed rotation is Keplerian, for simplicity." (5.2 Analysis of Rotation)
   - fitting: _not stated_
   - validation: Appendix B: infalling-rotating envelope would give half the mass  
  > "the protostellar mass would be half of that estimated above via the pure Keplerian model" (5.2 Analysis of Rotation)

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum peak intensity (1.2 mm) | 17.2 | 0.3 (3σ) | mJy/beam | 2 | (17 _\. |
| Continuum integrated flux | 21.4 | 0.7 (3σ) | mJy | 2 | (21 _._ 4 _±_ 0 _._ 7) mJy |
| 32SO/34SO intensity ratio | 13 | 4 | dimensionless | 3 | The intensity ratio [32] SO/ [34] SO is found to be 13 _±_ 4 |
| Optical depth of 32SO | 2.33 | not stated | dimensionless | 3 | The optical depth of [32] SO is indeed estimated to be 2.33 |
| Dust continuum optical depth | 0.07 | not stated | dimensionless | 2 | beam-averaged optical depth of the dust continuum is estimated to be 0.07. |
| N(SO)/N(CS) at protostar | 3 x 10^2 | +13/-2 x10^2 | dimensionless | 3 | The abundance ratio SO/CS is as high as 3 |
| Protostellar mass | 0.82-1.0 | not stated | Msun | 5 | protostellar mass between 0.82 and 1.0 _M_ _⊙_ by assuming an inclination angle of 90 _[◦]_ to |
| Inclination (lower limit) | 65 | not stated | deg | 5 | If we assume a flat disk with no thickness, _i_ is estimated to be 65 _[◦]_ . |
| SO2 red/blue peak asymmetry | blue 329±10, red 225±9; ratio 0.68 | 10, 9 | mJy/beam | 0 | and red-shifted peaks of 329 _±_ 10 and 225 _±_ 9 mJy beam _[−]_ [1] |

## Qualitative findings

- SO and SO2 compact near protostar, CS deficient but present in southern ridge; COMs and CCH, c-C3H2 not detected  
  > "The former component is found to be abundant in SO and SO 2 but deficient in CS." (abstract)

## Claim tuples

- H: Is the chemistry near Elias 29 rich in SO/SO2 and poor in CS and organics? | E: Line maps and LTE abundances compared with other sources | R: SO/CS ~3e2, higher than L1157 B1 by ~200; COMs undetected | F: Elias 29 is S-oxide rich and COM deficient | **supported**
- H: What causes the COM deficiency? | E: Discussion of evolved nature vs warm prestellar dust | R: Both consistent; not discriminated | F: Evolutionary or high parent-cloud temperature | **partially**
- H: Does SO/SO2 trace rotation and what is the protostellar mass? | E: Moment 1, PV diagrams, Keplerian model | R: N-S velocity gradient; M 0.82-1.0 Msun for i 90-65 deg | F: Rotation around protostar with mass lower than earlier estimates | **partially**
- H: Why is SO2 blue-shifted emission weaker? | E: Estimate dust optical depth attenuation and consider expansion | R: Averaged tau 0.07 gives factor 0.93, insufficient; tau 0.4 in thin disk could explain | F: Several possible causes, undecided | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: beta=1.0 opacity (kappa=2.5 cm2/g) would halve N(H2) and mass; not adopted  
  > "In the following discussion, we use the former results with _κ_ _ν_ = 1.3" (3.1 1.2 mm Continuum Emission)
- How they decided it was enough: _not stated_
- Limitation (authors): Rotation marginally resolved; Keplerian vs infall-rotation indistinguishable; mass depends on inclination  
  > "it is difficult to distinguish between Keplerian motion and infall-rotation." (5.2 Analysis of Rotation)
- Limitation (authors): Column densities beam-averaged and may be affected by beam dilution  
  > "Thus, the calculated column densities may be underestimates and could be affected by" (3.3 Abundance Ratios of the S-bearing Species)
- Caveat (inferred, ours): Mass estimate from by-eye PV comparison with no formal fit or error
- Caveat (inferred, ours): Large uncertainties on SO/CS ratio from marginal CS detection
- Caveat (inferred, ours): Single-epoch data with extended emission resolved out

## Reproducibility

- Data public (paper): ALMA data set 2013.1.01102.S used  
  > "This study used the ALMA data set ADS/JAO.ALMA#2013.1.01102.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Table 1 line parameters
- Missing: CASA version
- Missing: Imaging parameters (size, cell, masks)
- Missing: Details of PV model code
- Data volume (inferred): ~10-30 GB
- Score (inferred): 3/5, Public data and a clear outline, but software, version and imaging details missing.
- Rediscovery candidate: yes, Public archive data, numeric results (continuum fluxes, column densities, mass) reproducible with standard imaging, though some settings are missing.

## Links

- Method: Oya et al. 2017 (Keplerian PV model approach)
- Companion: López-Sepulcre et al. 2017 (NGC1333 IRAS 4A comparison, same survey)
- Companion: Sakai et al. 2016; Imai et al. 2016 (Comparative study sources)
- Related: Comparative study of five low-mass protostars (TMC-1A, B335, NGC1333 IRAS 4A, L483, Elias 29)

## Checks

```json
{
 "quotes": 68,
 "quotes_ok": 68,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 44,
  "rate": 0.587
 },
 "evidence_ok": true
}
```
