# Solar ALMA Observations: Constraining the Chromosphere above Sunspots

`2017ApJ...850...35L` | The Astrophysical Journal 2017 | first author: Loukitcheva, Maria A. | arXiv: 1710.03812 | DOI: 10.3847/1538-4357/aa91cc

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: sun
- Question: What do ALMA 1.3 mm and 3 mm brightness temperatures of a sunspot umbra and penumbra imply for semi-empirical sunspot chromosphere models?  
  > "we extend their analysis by comparing ALMA observations of the same sunspot at two different millimeter wavelengths with the predictions of sunspot umbral and, for the first time, penumbral models." (Introduction)
- Target **Sunspot in active region AR12470**: coordinates N13E30 (Dec 16); N15E05 (Dec 18), heliographic  
  > "AR12470, which was located in the eastern hemisphere (N13E30) on December 16, and north of disc center (N15E05) on December 18." (2 ALMA observations and Data Analysis); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00020.SV
- bands: Band 3 (3 mm) on 2015 Dec 16; Band 6 (1.3 mm) on 2015 Dec 18  
  > "Band 3 (100 GHz, corresponding to a wavelength of 3 mm), and on 2015 December 18 in Band 6 (230 GHz, 1.3 mm)" (2 ALMA observations and Data Analysis)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: twenty-two 12m antennae and nine 7m ACA antennae, plus single-dish full-disk scanning  
  > "a compact array configuration which included twenty-two 12m antennae and nine 7m antennae of the Atacama Compact Array (ACA)." (2 ALMA observations and Data Analysis)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Synthesized beam 4.9"x2.2" (3 mm), 2.4"x0.9" (1.3 mm)  
  > "was 4.9$''$ $\times$2.2$''$ and 2.4$''$ $\times$0.9$''$ at 3 mm and 1.3 mm, respectively." (2 ALMA observations and Data Analysis)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2015 December 16 (Band 3) and 18 (Band 6)  
  > "The ALMA observations were carried out on 2015 December 16 in Band 3" (2 ALMA observations and Data Analysis)
- pi or archival as stated: ALMA Solar Science Verification data  
  > "Using ALMA Science Verification data (cite: 2017ApJ...841L..20I), hereafter Paper I" (Introduction)
- Other facility **SDO/HMI and AIA**: Continuum, magnetograms and UV/EUV images used to define umbra/penumbra boundaries and for comparison  
  > "The umbral and penumbral boundaries were derived from the HMI continuum image as, respectively, 0.65 and 0.90 of the surrounding photospheric white-light intensity" (2.1)
- External data: Earlier sunspot brightness measurements (BIMA 3.5 mm, JCMT, Nobeyama, NoRH) for comparison  
  > "the measurements from JCMT at 0.35, 0.85 and 1.2 mm (diamonds) made by (cite: 1995ApJ...453..517L) at a resolution of 14-17$''$" (3.3) [from (cite: 2014A&A...561A.133L); (cite: 1995ApJ...453..517L); (cite: 2015ApJ...804...48I); (cite: 2016ApJ...816...91I)]
- External data: 3 mm umbral/penumbral brightness from Paper I  
  > "and in Fig. 5 from Paper I." (2.3) [from (cite: 2017ApJ...841L..20I)]
- Simulation/model as data: Published semi-empirical umbral and penumbral atmosphere models (Avrett 1981, Maltby 1986, Severino 1994, Socas-Navarro 2007, Fontenla 2009, Avrett 2015, de la Cruz Rodriguez 2016; YBB, DF, FCHHT-R, S-N D; FALC for QS)  
  > "In this work we build on the same set of umbral models as in (cite: 2014A&A...561A.133L)." (3.1)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Interferometric and single-dish data combined via feathering, as in Paper I  
  > "The single dish and interferometric data were further combined in the UV plane via feathering to derive the absolute brightness temperature of the interferometric maps" (2 ALMA observations and Data Analysis)
- flux calibrator: _not stated_
- flux scale uncertainty: ~100 K absolute; relative 4 K (3 mm), 10 K (1.3 mm)  
  > "we adopt an uncertainty of order 100 K in the absolute temperatures." (2.1)
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
- array combination: Feathering of single-dish and interferometric maps  
  > "combined in the UV plane via feathering" (2 ALMA observations and Data Analysis)
- smoothing: _not stated_
- final beam: 4.9"x2.2" (3 mm); 2.4"x0.9" (1.3 mm)  
  > "The full-width at half-maximum (FWHM) of the synthesized beam was 4.9$''$ $\times$2.2$''$" (2 ALMA observations and Data Analysis)
- final rms: _not stated_

### Inherited from earlier work

- Observation details and image synthesis  
  > "Details of the observations and image synthesis can be found in Paper I." (2 ALMA observations and Data Analysis) [from Paper I (cite: 2017ApJ...841L..20I)]
- Umbra/penumbra boundaries at 0.65 and 0.90 of photospheric intensity  
  > "0.65 and 0.90 of the surrounding photospheric white-light intensity following (cite: 2007A&A...465..291M)" (2.1) [from (cite: 2007A&A...465..291M)]
- Millimeter brightness calculation from models  
  > "The details of the mm brightness calculations can be found in, e.g., (cite: 2004A&A...419..747L)." (3.3) [from (cite: 2004A&A...419..747L)]

### Not stated but needed to reproduce (our reading)

- Calibration pipeline/CASA version and feathering parameters
- Exact ellipse parameters for inner/outer umbra and penumbra
- Code for the free-free brightness computation
- Image sizes and pixel scales
- Details of how model QS references were subtracted per model

## Analysis recipe

1. **Define sunspot regions**: Umbral and penumbral boundaries from HMI continuum; inner/outer regions chosen by eye with ellipses  
  > "red and green ellipses outlining inner and outer umbral boundaries (chosen by eye as described below)" (2.2)
   - parameter: 0.65 and 0.90 of surrounding white-light intensity  
  > "0.65 and 0.90 of the surrounding photospheric white-light intensity" (2.1)
   - fitting: _not stated_
   - validation: Compared with magnetogram histograms  
  > "The inner umbral ellipse, depicted in red, corresponds to the region of the strongest LOS magnetic field" (2.2)
2. **Measure brightness temperature statistics**: Mean and RMS of pixel brightness temperatures per region, with maps normalized to single-dish QS values  
  > "we determined typical brightness temperature values as the average of the corresponding set and its root-mean-square (RMS) variation" (2.1)
   - assumption: Disk-center QS ~6000 K (1.3 mm) and ~7400 K (3 mm)  
  > "around 6000 K and 7400 K, at 1.3 mm and 3 mm, respectively" (2.1)
   - fitting: _not stated_
   - validation: _not stated_
3. **Compute model mm brightness spectra**: Thermal free-free emission with H-zero and H-minus opacities at 32 wavelengths, 0.1-20 mm; effective formation heights from contribution function centroids  
  > "We have calculated the expected submm/mm brightness temperatures at 32 selected wavelengths in the range 0.1–20 mm for sunspot umbral models" (3.3)
   - assumption: Thermal free-free emission in LTE  
  > "assuming that the thermal free-free mechanism is responsible for the emission at mm wavelengths" (3.3)
   - fitting: _not stated_
   - validation: _not stated_
4. **Compare observations with models**: Compare model-minus-QS difference spectra with observed brightness minus disk-center QS, including earlier observations  
  > "we plot the difference spectra between the umbral brightness and the QS brightness from the corresponding reference atmospheric models" (3.3)
   - fitting: Qualitative comparison, no formal fit  
  > "None of the depicted model curves provides an outstanding fit to the observations at these longer wavelengths. However, the umbral model of (cite: 1994ASIC..433..169S), depicted in Fig. 12 by a red curve, shows the best agreement" (Millimeter-wavelength brightness spectra from umbral models)
   - validation: _not stated_

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Inner umbra mean Tb, 1.3 mm | 5330 | RMS 260 K | K | 2 | / inner umbra           / 5330       / 260                 / 7960       / 270                 / |
| Inner umbra mean Tb, 3 mm | 7960 | RMS 270 K | K | 2 | / inner umbra           / 5330       / 260                 / 7960       / 270                 / |
| Penumbra mean Tb, 1.3 mm | 6990 | RMS 440 K | K | 2 | / penumbra              / 6990       / 440                 / 7380       / 450                 / |
| Effective formation height, Severino 1994 model, 1.3 mm / 3 mm | 1090 / 1540 | not stated | km | 3 | / Severino et al. 1994             /     1090      /     1540      / |

## Qualitative findings

- Umbra looks very different at 1.3 and 3 mm, while penumbral structure is similar at both  
  > "We find that the sunspot umbra exhibits a radically different appearance at 1.3 mm and 3 mm, whereas the penumbral brightness structure is similar at the two wavelengths." (abstract)

## Claim tuples

- H: Do existing umbral models reproduce ALMA mm brightness of sunspot umbra? | E: Compared ALMA inner-umbra brightness differences to model-predicted spectra | R: Severino et al. (1994) model fits best | F: Best umbral model is Severino et al. (1994) | **supported**
- H: Do penumbral models reproduce ALMA data? | E: Compared penumbral brightness to four models | R: YBB and FCHHT R closest but not satisfactory | F: No penumbral model fits satisfactorily | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Side lobes may affect 1.3 mm umbral brightness, which should be treated as an upper limit  
  > "the derived umbral brightness depression in the single-dish map at 1.3 mm should be considered as an upper limit" (4 Discussion and Conclusions)
- Caveat (inferred, ours): Single sunspot on two different days
- Caveat (inferred, ours): Model comparison is qualitative
- Caveat (inferred, ours): Beam resolution comparable to umbral size, so region averages are partly smeared

## Reproducibility

- Data public (paper): Solar ALMA Science Verification data  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA$\sharp$2011.0.00020.SV." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Region ellipse definitions
- Missing: Model brightness code and model tables
- Missing: Feathering/processing details (in Paper I)
- Data volume (inferred): ~tens of GB (SV mosaics, 2 bands)
- Score (inferred): 3/5, Data public and results numeric, but processing relies on Paper I and region definitions are by eye.
- Rediscovery candidate: no, Region definitions by eye and model calculations not fully specified.

## Links

- Method: (cite: 2017SoPh..292...87S) (Solar ALMA SV data processing and feathering)
- Method: (cite: 2017SoPh..292...88W) (Single-dish calibration and QS temperature scaling)
- Companion: (cite: 2017ApJ...841L..20I) (Paper I: 3 mm sunspot umbral brightening)
- Related: ALMA Solar Science Verification campaign 2015

## Checks

```json
{
 "quotes": 38,
 "quotes_ok": 38,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.0.00020.SV"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 67,
  "stated": 30,
  "rate": 0.448
 },
 "evidence_ok": true
}
```
