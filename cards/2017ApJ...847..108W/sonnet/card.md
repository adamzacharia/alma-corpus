# Discovery of Striking Difference of Molecular-emission-line Richness in the Potential Proto-binary System NGC 2264 CMM3

`2017ApJ...847..108W` | The Astrophysical Journal 2017 | first author: Watanabe, Yoshimasa | arXiv: 1708.07582 | DOI: 10.3847/1538-4357/aa88b6

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: Is NGC 2264 CMM3 a binary system, and do its components differ in molecular line richness (hot core, complex organic molecules)?  
  > "CMM3 is resolved into the two continuum peaks, CMM3A and CMM3B, at an angular separation of $0.9''$." (abstract)
- Target **NGC 2264 CMM3**: coordinates 6:41:12.3, +9:29:8.0 (J2000, phase center)  
  > "The phase-center coordinate is ($\alpha_{\rm J2000}$, $\delta_{\rm J2000}$) = (6:41:12.3, +9:29:8.0)." (2 Observation and Reduction); "corresponds to a linear scale of $\sim270$ au at the distance of 738 pc." (3.1); z/distance 738 pc  
  > "The phase-center coordinate is ($\alpha_{\rm J2000}$, $\delta_{\rm J2000}$) = (6:41:12.3, +9:29:8.0)." (2 Observation and Reduction); "corresponds to a linear scale of $\sim270$ au at the distance of 738 pc." (3.1); distance from not stated (NGC 2264 C cited to Kamezaki2014)  
  > "The phase-center coordinate is ($\alpha_{\rm J2000}$, $\delta_{\rm J2000}$) = (6:41:12.3, +9:29:8.0)." (2 Observation and Reduction); "corresponds to a linear scale of $\sim270$ au at the distance of 738 pc." (3.1)

## Data provenance

- ALMA projects: 2013.1.01192.S
- bands: 0.8 mm band  
  > "interferometric line survey in the 0.8 mm band" (abstract)
- frequencies and spectral setup: 12 spectral windows covering 336.0–347.3 and 348.0–359.3 GHz, 0.98 MHz resolution  
  > "Twelve spectral windows were employed to cover the frequency ranges of 336.0–347.3 GHz and 348.0–359.3 GHz at a frequency resolution of 0.98 MHz." (2 Observation and Reduction)
- continuum bandwidth: _not stated_
- arrays: 12 m antennas, 31 (2014) and 39 (2015)  
  > "the numbers of the 12 m antenna used in those observations were 31 and 39, respectively" (2 Observation and Reduction)
- configurations: _not stated_
- baselines: 14 m to 649 m  
  > "Minimum and maximum baseline lengths were 14 m and 649 m on the ground, respectively." (2 Observation and Reduction)
- angular resolution: 0.37 x 0.30 arcsec continuum; 0.28–0.49 arcsec spectral  
  > "The synthesized beam and the rms noise of spectral images range from 0.28$''$ to 0.49$''$" (2 Observation and Reduction)
- max recoverable scale: ~13 arcsec  
  > "any structure extended over $\sim 13''$ or larger is subject to the resolving-out effect" (2 Observation and Reduction)
- sensitivity: continuum rms 0.35 mJy/beam; spectral 4.2–7.0 mJy/beam  
  > "from 4.2 mJy beam$^{-1}$ to 7.0 mJy beam$^{-1}$ at the frequency resolution of 0.98 MHz" (2 Observation and Reduction)
- time on source: _not stated_
- observing dates: 19 July 2014 and 20 May 2015  
  > "The observations were carried out with ALMA on 19 July 2014 and 20 May 2015" (2 Observation and Reduction)
- pi or archival as stated: _not stated_
- Line: CH3OH 13_1-13_0 A-+ (not stated)
- Line: HCN, CO, CS, SO (outflow tracers) CO J=3-2, CS J=7-6, SO N_J=8_7-7_6 (not stated)
- Other facility **ASTE**: single-dish 0.8 mm spectrum for comparison  
  > "In the previous observation with the single-dish telescope ASTE in the 0.8 mm band" (3.2)
- Other facility **2MASS**: near-infrared images  
  > "This publication makes use of data products from the Two Micron All Sky Survey" (Acknowledgments)
- External data: Dust mass absorption coefficient kappa = 0.0182 cm2/g  
  > "we adopt the mass absorption coefficient of the dust of $\kappa_{\nu}=0.0182$ cm$^2$g$^{-1}$ derived by (cite: Jorgensen2016)" (3.2) [from (cite: Jorgensen2016)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.5.3  
  > "Common Astronomy Software Applications package (CASA; Version 4.5.3)" (2 Observation and Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0750+125  
  > "The absolute flux was calibrated by using the quasar J0750+125." (2 Observation and Reduction)
- flux scale uncertainty: 10 %  
  > "The uncertainty of the absolute flux calibration is 10 %" (2 Observation and Reduction)
- self calibration: Performed on continuum, solutions applied to continuum and line data; S/N 190 to 723  
  > "Self-calibration was performed by using the continuum data, and then the solutions were applied to both the continuum and spectral line data." (2 Observation and Reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "the data were imaged and CLEANed by using the Briggs weighting with the robustness parameter of 0.5" (2 Observation and Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: continuum from averaging line-free channels of all spectral windows (channels not listed)  
  > "A continuum image was obtained by averaging line-free channels of all the spectral windows." (2 Observation and Reduction)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.37'' x 0.30'' (PA -30.7 deg)  
  > "$0.37'' \times 0.30''$ (P.A.$=-30.7^{\circ}$)" (2 Observation and Reduction)
- final rms: 0.35 mJy/beam (continuum)  
  > "0.35 mJy beam$^{-1}$, respectively" (2 Observation and Reduction)

### Inherited from earlier work

- H2 column density formula  
  > "by using the formula used by (cite: Imai2016)" (3.2) [from (cite: Imai2016)]
- Envelope mass formula  
  > "The envelope mass is derived based on the formula given by (cite: Ward-Thompson2000)." (5 Discussion) [from (cite: Ward-Thompson2000)]

### Not stated but needed to reproduce (our reading)

- Line-free channel selection
- Self-calibration solution intervals and number of iterations
- CLEAN threshold, masks, image size and cell size
- Software and spectroscopic catalog used for line identification and rotation diagram
- Transitions used for column densities
- Source-finding and 2D Gaussian fitting details
- Line widths/velocity ranges for moment maps
- Pipeline vs manual calibration

## Analysis recipe

1. **Image continuum and identify peaks**: Self-calibrated continuum imaged with Briggs weighting; local peaks >10 sigma identified, 2D Gaussian fits  
  > "we have identified local intensity peaks detected with more than $10\sigma$ as the continuum peaks" (3.1)
   - software: CASA
   - parameter: robust = 0.5  
  > "Briggs weighting with the robustness parameter of 0.5" (2 Observation and Reduction)
   - fitting: 2D Gaussian fitting  
  > "the FWHM evaluated by the 2D-Gaussian fitting is similar to the synthesized beam" (3.1)
   - validation: _not stated_
2. **Rotation temperature of CH3OH**: Rotation diagram, optically thin LTE  
  > "rotation temperature ($385 \pm 58$ K) of CH$_3$OH estimated by using the rotation diagram method under the assumption of optically thin conditions and local thermodynamic equilibrium" (3.2)
   - assumption: optically thin, LTE  
  > "under the assumption of optically thin conditions and local thermodynamic equilibrium (LTE)" (3.2)
   - fitting: _not stated_
   - validation: _not stated_
3. **Column densities and abundances**: LTE column densities at Trot=100 and 300 K averaged over uncontaminated transitions; N(H2) from continuum peak flux  
  > "The column densities are derived under the LTE approximation with the rotation temperatures of 100 K and 300 K." (3.2)
   - assumption: kappa=0.0182 cm2/g, gas-to-dust ratio 100, dust T 100 and 300 K  
  > "The gas-to-dust mass ratio is assumed to be 100." (3.2)
   - fitting: _not stated_
   - validation: _not stated_
4. **Outflow mapping**: Moment 0/1 and channel maps of HCN, CO, CS, SO, CH3OH  
  > "Figures [5](#fig05)a and c show the 0th and the 1st moment maps of HCN, respectively." (3.3 Outflows)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.5.3: data reduction, self-calibration, imaging  
  > "Data reduction was carried out with the Common Astronomy Software Applications package (CASA; Version 4.5.3)." (2 Observation and Reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CMM3A flux density | 431.8 | 2.2 | mJy | 1 | $431.8 (2.2)$ |
| CMM3B flux density | 313.0 | 3.4 | mJy | 1 | $313.0 (3.4)$ |
| CMM3A-CMM3B separation | ~0.9 (~660 au) | not stated | arcsec | 1 | The angular separation between the two peaks is $\sim 0.9''$, which corresponds to $\sim660$ au. |
| CH3OH rotation temperature in CMM3A | 385 | 58 | K | 2 | rotation temperature ($385 \pm 58$ K) |
| CMM3A envelope mass (100 K / 300 K) | 18 / 5.7 | 2 / 0.6 | Msun | 3 | 18 (2) - 5.7 (0.6) |
| CMM3B envelope mass (100 K / 300 K) | 13 / 4.1 | 1 / 0.4 | Msun | 3 | 13 (1) - 4.1 (0.4) |
| N(CH3OH) CMM3A at 100 K | 4.0e16 | 0.2e16 | cm^-2 | 3 | $4.0 (0.2) \times 10^{16}$ |

## Qualitative findings

- CMM3A is rich in complex organic molecules in a compact (<300 au) hot core, whereas CMM3B is line-deficient.  
  > "they are concentrated in a compact region ($<300$ au) around the continuum peak" (3.2)
- Two bipolar outflows, from CMM3A and CMM3B respectively.  
  > "This collimated outflow system seems to be launched from CMM3B" (3.3 Outflows)

## Claim tuples

- H: CMM3 is a binary | E: 0.8 mm continuum imaging at 0.3 arcsec | R: Two peaks separated by 0.9 arcsec with similar velocities | F: CMM3 is a potential proto-binary | **supported**
- H: Both components have hot cores | E: Line survey spectra, moment maps, rotation diagram | R: COMs only toward CMM3A, Trot 385 K | F: CMM3A harbors a hot core, CMM3B does not | **supported**
- H: Origin of the difference | E: Qualitative discussion | R: Three interrelated possibilities (evolutionary stage, dust opacity, mass) | F: Cannot be disentangled with present data | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Rotation temperature uncertain due to non-LTE, optical depth, blending, resolving-out  
  > "The uncertainty of the derived rotation temperature is relatively large because of the non-LTE effects" (3.2)
- Caveat (inferred, ours): Dust opacity at 0.8 mm may bias N(H2) and abundances
- Caveat (inferred, ours): Only two temperatures assumed for column densities
- Caveat (inferred, ours): Hot core absence in CMM3B partly inferred from upper limits

## Reproducibility

- Data public (paper): ALMA project 2013.1.01192.S cited; public status not stated  
  > "This paper makes use of the ALMA data set ADS/JAO.ALMA#2013.1.01192.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Self-cal parameters
- Missing: Line-free channels
- Missing: Line catalog and transitions used
- Missing: Imaging parameters
- Data volume (inferred): ~100-300 GB raw for two line-survey sessions
- Score (inferred): 3/5, Public data and key imaging parameters given, but many processing and line-analysis details missing.
- Rediscovery candidate: no, Recipe incomplete for line analysis; some results are qualitative.

## Links

- Method: Imai et al. 2016 (cite: Imai2016) (H2 column density formula)
- Companion: Watanabe et al. 2015 (cite: Watanabe2015) (single-dish line survey of CMM3)
- Companion: Saruwatari et al. 2011 (cite: Saruwatari2011) (SMA outflow observations)

## Checks

```json
{
 "quotes": 55,
 "quotes_ok": 55,
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
  "facts": 67,
  "stated": 38,
  "rate": 0.567
 },
 "evidence_ok": true
}
```
