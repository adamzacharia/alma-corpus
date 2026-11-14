# Star Formation and Feedback: A Molecular Outflow-Prestellar Core Interaction in L1689N

`2016ApJ...827..133L` | The Astrophysical Journal 2016 | first author: Lis, D. C. | arXiv: 1605.01239 | DOI: 10.3847/0004-637X/827/2/133

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type multi_facility_alma_minor

## Science

- Fields: star_formation, astrochemistry
- Question: Is the L1689N prestellar core interacting with the molecular outflow from IRAS 16293-2422, and what are the core's dust continuum and deuterated-molecule properties?  
  > "which has been suggested to be interacting with a molecular outflow driven by the nearby solar type protostar IRAS 16293-2422." (abstract)
- Target **L1689N prestellar core (I16293E)**: coordinates _not stated_; z/distance 120 pc  
  > "L1689N, a nearby (120 pc; (cite: loinard08)) dark cloud located in the $\rho$ Ophiuchi complex" (Introduction); distance from Loinard et al. 2008  
  > "L1689N, a nearby (120 pc; (cite: loinard08)) dark cloud located in the $\rho$ Ophiuchi complex" (Introduction)

## Data provenance

- ALMA projects: 2012.1.00178.S
- bands: _not stated_
- frequencies and spectral setup: 310 GHz setting: four spectral windows near 309 GHz; N2D+ and ND3 in 0.0625 GHz windows; 340 GHz setting for continuum  
  > "Four spectral windows were observed centered near 309 GHz, with varying spectral resolution." (Observations)
- continuum bandwidth: two bands of 1.992 GHz width, near 308.053 and 309.873 GHz  
  > "by averaging channels within two bands of 1.992 GHz width, centered near 308.053 and 309.873 GHz" (Observations)
- arrays: ACA (Morita Array), eleven 7-m antennas  
  > "using eleven 7-m antennas of the Morita Array component of ALMA in Cycle 1" (Observations)
- configurations: _not stated_
- baselines: minimum 8.7 m; maximum 50 m  
  > "The minimum baseline of the ACA is 8.7 m, for a transiting source." (Discussion); "with a maximum baseline of 50 m" (Observations)
- angular resolution: 970 um beam 5.04x3.16 arcsec, PA 80 deg  
  > "the synthesized beam size is $5.04 \times 3.16$$^{\prime\prime}$, at a position angle of 80$^\circ$." (Observations)
- max recoverable scale: 13.8 arcsec  
  > "the ALMA Technical Handbook provides a value of 13.8$^{\prime\prime}$ for the largest angular scale recovered by the interferometer" (Discussion)
- sensitivity: _not stated_
- time on source: 15 min per pointing of a ten-pointing mosaic  
  > "At each point of the mosaic, 15 minutes of data was collected" (Observations)
- observing dates: 310 GHz: 2014 January–April (7 occasions); 340 GHz: 2014 April (6 occasions)  
  > "was observed on seven occasions during 2014 January–April" (Observations)
- pi or archival as stated: _not stated_
- Line: N2D+ 4-3 (308.42227 GHz)
- Line: ND3 1_0-0_0 (0a-0s) (309.90949 GHz)
- Line: CH3OH 5_1,4-5_0,5 A-+ (309.29040 GHz)
- Line: SO 2_2-2_1 (309.50244 GHz)
- Other facility **Herschel/HIFI**: NH2D, NH3, o-H2O, SO maps and spectra  
  > "using the Band 1 receivers of the Heterodyne Instrument for the Far-Infrared (HIFI; (cite: degraauw10))" (Observations)
- Other facility **CSO**: 1 mm maps of deuterated and hydrogenated tracers  
  > "using the 10.4 m Leighton Telescope of the Caltech Submillimeter Observatory (CSO)" (Observations)
- External data: Dust temperature 16 K from SED fit  
  > "isothermal dust temperature of 16 K derived from a SED fit by (cite: stark04)" (Results) [from (cite: stark04)]
- External data: Dust opacity kappa_1.3mm = 0.005 cm2/g  
  > "we scale the grain opacity coefficient $\kappa_{\rm 1.3 mm} = 0.005$ cm$^2$ g$^{-1}$ (cite: motte98)" (Discussion) [from (cite: motte98)]
- External data: Distance 120 pc  
  > "assuming a distance of 120 pc (cite: loinard08)" (Discussion) [from (cite: loinard08)]

## Processing

### Calibration

- pipeline or manual: ALMA/NAASC staff calibrated; bandpass J1733-1304 or J1427-4206, phase J1626-2951  
  > "ALMA/NAASC staff performed bandpass calibration with the quasar J1733-1304 or J1427-4206" (Observations)
- casa version: CASA 4.2  
  > "deconvolved and CLEANed with the CASA software package (version 4.2)" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan  
  > "the flux was calibrated with Titan" (Observations)
- flux scale uncertainty: ~10%  
  > "The uncertainty in the absolute flux is ∼10%." (Observations)
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
- continuum subtraction: 850 um continuum by averaging line-free channels; CH3OH and H3O+ lines flagged for 970 um  
  > "CH$_3$OH and H$_3$O$^+$ lines in the bands were flagged before averaging to avoid possible contamination." (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 970 um: 5.04x3.16 arcsec PA 80 deg; 850 um: 4.4x2.9 arcsec PA 94 deg  
  > "the synthesized beam size is $4.4 \times 2.9$$^{\prime\prime}$, at a position angle of 94$^\circ$." (Observations)
- final rms: 1.1 mJy/beam at 970 um; 3.3 mJy at 850 um  
  > "The rms in the image is 1.1 mJy/beam" (Observations)

### Inherited from earlier work

- Dust temperature 16 K adopted  
  > "For a 16 K dust temperature (cite: stark04)" (Discussion) [from (cite: stark04)]

### Not stated but needed to reproduce (our reading)

- tclean/clean weighting, robust, cell and image size
- deconvolver and masking
- Line-free channels used for continuum
- Gas-to-dust ratio used for mass
- Exact coordinates and phase center
- Which execution blocks were used
- Primary-beam correction details

## Analysis recipe

1. **Image ACA continuum and lines**: CASA deconvolution/CLEAN of calibrated visibilities; continuum from averaged channels  
  > "The calibrated visibilities were deconvolved and CLEANed with the CASA software package (version 4.2)." (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Hyperfine fits of NH2D, ND3, N2D+**: HFS fits giving v0, width, Tex, tau  
  > "The HFS fit parameters (the line center velocity and width, the excitation temperature, and the line center optical depth) are given in Table [1](#tab:hfs)." (Results)
   - software: GILDAS CLASS
   - fitting: CLASS HFS fit, single velocity component  
  > "with single velocity component HFS fits overlaid in red" (Results)
   - validation: _not stated_
3. **Source size from continuum**: 2D Gaussian fit, deconvolved from beam  
  > "A two-dimensional Gaussian fit gives a FWHM source size of $13.2 \times 8.6$$^{\prime\prime}$ at a position ange of 2$^\circ$." (Discussion)
   - assumption: distance 120 pc  
  > "assuming a distance of 120 pc (cite: loinard08)" (Discussion)
   - fitting: _not stated_
   - validation: _not stated_
4. **Column density, density and mass**: Optically thin dust emission with scaled opacity, Td 16 K or 11 K  
  > "This leads to $\kappa_{\rm 970 \mu m} = 0.009$ cm$^2$ g$^{-1}$." (Discussion)
   - parameter: line-of-sight size 9.5 arcsec (1140 au)  
  > "Assuming a line-of-sight source size of 9.5$^{\prime\prime}$ or 1140 au" (Discussion)
   - assumption: nu^2 opacity dependence; Td 16 K or 11 K  
  > "appropriate for prestellar dense, clumps with a $\nu^2$ frequency dependence" (Discussion)
   - fitting: _not stated_
   - validation: Compared with Bacmann 2016 and Pattle 2015 values  
  > "consistent with the best-model value of $1.4 \times 10^7$ cm$^{-2}$ in the recent study of (cite: bacmann16)" (Discussion)

## Software

- **CASA** 4.2: ACA imaging  
  > "CASA software package (version 4.2)" (Observations)
- **HIPE** 10.0: HIFI data reduction  
  > "using HIPE version 10.0" (Observations)
- **GILDAS CLASS** : spectra reduction and HFS fits  
  > "subsequently reduced using the GILDAS CLASS[^3] software package" (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 970 um peak flux | 76 | rms 1.1 mJy/beam | mJy/beam | 1 | the peak flux is 76 mJy/beam and the integrated flux is 840 mJy |
| Intrinsic source size | 12.9 x 7.0 arcsec (1540 x 840 au) | not stated | arcsec | 3 | the intrinsic source size is $12.9 \times 7.0$$^{\prime\prime}$, or $1540 \times 840$ au |
| H2 column density | 1.8e23 (16 K); 3.3e23 (11 K) | not stated | cm^-2 | 4 | we derive an H$_2$ column density of $1.8 \times 10^{23}$ cm$^{-2}$ |
| H2 volume density | (1.1-1.9)e7 | not stated | cm^-3 | 4 | we derive an H$_2$ volume density of $(1.1-1.9)\times 10^7$ cm$^{-3}$ |
| Mass of compact source | 0.22 (16 K); 0.42 (11 K) | not stated | Msun | 4 | The total mass of the compact continuum source seen in the ACA image is 0.22 M$_{\odot}$ |
| ND3 HFS line width | 0.40 | ~0.002 | km/s | 2 | ND$_3$      /     3.45      /     0.40      /   6.5    /   0.43   / |

## Qualitative findings

- NH2D line velocity and width change across the core, indicating interaction with the outflow  
  > "The change in the NH$_2$D line velocity and width across the core provides clear evidence of an interaction with the outflow" (abstract)

## Claim tuples

- H: The core interacts with the IRAS 16293 outflow | E: HIFI NH2D line velocity/width maps and water maps | R: Velocity and width increase from NE to W/SW; water avoids core | F: Physical interaction with the blue outflow lobe | **supported**
- H: Dust peak coincides with deuterated tracers | E: ACA continuum vs N2D+/ND3 | R: Dust peak offset ~5 arcsec south | F: Northern extended emission is resolved out | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Low dynamic range and resolved-out extended emission; 850 um SNR too low for temperature gradient  
  > "the SNR in our 850 $\mu$m continuum image is too low to draw definitive conclusions" (Discussion)
- Caveat (inferred, ours): No total-power data, so masses are lower limits for extended gas
- Caveat (inferred, ours): Mass depends on assumed opacity and dust temperature

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: Gas-to-dust ratio
- Data volume (inferred): ~20-50 GB
- Score (inferred): 3/5, Public ACA data and simple recipe, but imaging parameters are missing.
- Rediscovery candidate: no, Imaging recipe is incomplete.

## Links

- Companion: (cite: pagani16) (Complementary H2D+ and dust temperature study)

## Checks

```json
{
 "quotes": 53,
 "quotes_ok": 53,
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
  "stated": 38,
  "rate": 0.551
 },
 "evidence_ok": true
}
```
