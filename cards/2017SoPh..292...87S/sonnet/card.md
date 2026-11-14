# Observing the Sun with the Atacama Large Millimeter/submillimeter Array (ALMA): High-Resolution Interferometric Imaging

`2017SoPh..292...87S` | Solar Physics 2017 | first author: Shimojo, M. | arXiv: 1704.03236 | DOI: 10.1007/s11207-017-1095-2

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type technical_calibration_or_instrument

## Science

- Fields: sun, instrumentation
- Question: How can ALMA be commissioned and calibrated for continuum interferometric imaging of the Sun in Bands 3 and 6, and what do the resulting science-verification images show?  
  > "Examples of high-resolution synthesized images obtained using the newly commissioned modes during the solar commissioning campaign held in December 2015 are presented." (abstract)
- Target **AR 12470 (leading sunspot)**: coordinates ICRS reference 17h35m32.218s -23d16m23.843s (Band 3, 16 Dec 2015); 17h44m10.112s -23d19m30.632s (Band 6, 18 Dec 2015)  
  > "AR 12470 | 18:01 – 18:48UT" (Table 4); z/distance _not stated_; distance from _not stated_
- Target **Solar limb near South Pole**: coordinates 17h51m46.086s -23d41m33.229s (20 Dec 2015)  
  > "South Pole | 13:31 – 14:32UT" (Table 4); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00020.SV
- bands: Band 3 (3 mm) and Band 6 (1.25 mm) continuum  
  > "two frequency bands, the 3 mm band (Band 3) and the 1.25 mm band (Band 6)" (abstract)
- frequencies and spectral setup: Four 2 GHz SPWs; Band 3: 92–96, 104–108 GHz; Band 6: 229–233, 245–249 GHz; images at 100 GHz and 239 GHz  
  > "Band 6 | 229 – 231 GHz | 231 – 233 GHz | 245 – 247 GHz | 247 – 249 GHz" (Table 2); "the observing frequency of the solar images shown in this article is the same as the frequency of the first LO: 100 GHz for Band 3, 239 GHz for Band 6." (4.1 Data and Image Synthesis)
- continuum bandwidth: _not stated_
- arrays: ~30 antennas incl. 9 x 7 m; 21 x 12 m; 7 m and 12 m correlated together, plus TP  
  > "The commissioning observation is carried out using 9 $\times$ 7 m antennas and 21 $\times$ 12 m antennas." (4.3 Imaging Artifacts Above the Solar Limb)
- configurations: most compact 12-m configurations (C40-1 to C40-3)  
  > "In Cycle 4, only the three most compact antenna configurations are available for solar observing: C40-1, C40-2, and C40-3." (3.5 Additional Considerations)
- baselines: _not stated_
- angular resolution: Band 3 4.9"x2.2"; Band 6 2.4"x0.9" (sunspot), 1.7"x1.0" (South Pole)  
  > "The synthesized beams are $2.4\hbox{$^{\prime\prime}$}\times 0.9\hbox{$^{\prime\prime}$}$ for the sunspot image" (4.1 Data and Image Synthesis)
- max recoverable scale: 12-m only 20.1" at 239 GHz; heterogeneous array 34.3" at 239 GHz  
  > "the largest angular scale measured is 20.1$^{\prime\prime}$ at 239 GHz" (4.3 Imaging Artifacts Above the Solar Limb)
- sensitivity: noise 3.7 K (Band 3), 9.8 K (Band 6) for 6 s integration, 8 GHz bandwidth  
  > "the noise level of the Band 3 synthesized image of the sunspot (Figure 7b) is 3.7 K when the integration time is six seconds" (4.2 Estimating the Noise Level)
- time on source: _not stated_
- observing dates: Commissioning 14–21 Dec 2015; data sets 16, 18, 20 Dec 2015  
  > "was held from 14 – 21 December 2015." (4 ALMA Solar Imaging Examples)
- pi or archival as stated: _not stated_
- Other facility **SDO/AIA**: EUV and UV continuum images for co-alignment  
  > "UV continuum, and EUV images obtained with Solar Dynamics Observatory/Atmospheric Imaging Assembly" (4.4 Co-alignment between ALMA and other instruments)
- Other facility **IRIS**: Mg II k2v image for co-alignment  
  > "a Mg ii k$_{\rm 2v}$ image obtained with the Interface Region Imaging Spectrograph" (4.4 Co-alignment between ALMA and other instruments)
- External data: Correction factor for CASA-made full-Sun TP maps  
  > "(cite: White17) pointed out that a correction factor has to be applied to any map created with CASA." (4.1 Data and Image Synthesis) [from (cite: White17)]

## Processing

### Calibration

- pipeline or manual: Standard ALMA calibration in CASA except amplitude calibration using Tant/Tsys  
  > "ALMA standard calibrating method is used for solar data, except for the amplitude calibration steps described in Section 3.2." (4.1 Data and Image Synthesis)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: SV data released by JAO 18 Jan 2017 were calibrated and imaged by the authors in CASA  
  > "was used to calibrate and image the SV data." (4.1 Data and Image Synthesis)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean with mosaic imagemode, even for single pointings  
  > "the mosaic option for the imagemode parameter has to be used even for the data of single-pointing observations" (4.1 Data and Image Synthesis)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 1.0 (default 0 gave stripes)  
  > "Hence, in this article, we always set the robust parameter to 1.0." (4.1 Data and Image Synthesis)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: CASA feather with default parameters, combining with full-Sun TP map  
  > "For the combination, we use the default parameters of the feather task in CASA." (4.1 Data and Image Synthesis)
- smoothing: _not stated_
- final beam: 4.9"x2.2" (Band 3 sunspot)  
  > "is 4.9$^{\prime\prime}$$\times$2.2$^{\prime\prime}$" (4.1 Data and Image Synthesis)
- final rms: 3.7 K (Band 3), 9.8 K (Band 6)  
  > "estimate the noise level to be 9.8 K" (4.2 Estimating the Noise Level)

### Inherited from earlier work

- Tant/Tsys measurement procedure and full-Sun TP mapping  
  > "The procedure for measuring $T_{\rm ant}$ and $T_{\rm sys}$ is described in detail by (cite: White17)" (3.2 Flux Calibration) [from (cite: White17)]

### Not stated but needed to reproduce (our reading)

- Cell size, image size, niter, threshold and deconvolver for clean
- Mask and cleaning details
- CASA version
- Exact feather parameters and how TP map and the correction factor were applied
- Procedure for RA/Dec to heliocentric conversion
- Which SV execution blocks and scripts map to each dataset beyond EB IDs

## Analysis recipe

1. **Calibrate solar visibilities**: Standard ALMA calibration with solar-specific amplitude calibration using Tant from hot/cold/sky/off/sun/zero power measurements and Tsys  
  > "when observing the Sun $T_{\rm ant}>T_{\rm sys}$, and it is therefore necessary to measure both $T_{\rm sys}$ and $T_{\rm ant}$ in order to correctly scale the visibility measurements." (3.2 Flux Calibration)
   - software: CASA
   - fitting: _not stated_
   - validation: Phase variation from attenuator changes checked with 3C279; std 0.3 deg (IF Switch), 0.6 deg (IF Proc)  
  > "its standard deviation across the spectral window is 0.3 degrees for the attenuator in the IF Switch, and 0.6 degrees in the IF Processor." (3.1 Gain Calibration)
2. **Synthesize mosaic images**: clean mosaic with all four SPWs, 149 pointings, robust 1.0  
  > "we include the data from all four SPWs for synthesizing one solar image in this article." (4.1 Data and Image Synthesis)
   - software: CASA
   - parameter: robust = 1.0  
  > "Hence, in this article, we always set the robust parameter to 1.0." (4.1 Data and Image Synthesis)
   - fitting: _not stated_
   - validation: Stripe artifacts disappear with robust 1.0  
  > "When this is done, the artificial stripes disappear in the image" (4.1 Data and Image Synthesis)
3. **Combine with single-dish map**: feather with full-Sun TP map  
  > "Figure 7e is the result of combining the synthesized image and the full-Sun map constructed from the simultaneous single-dish mapping data." (4.1 Data and Image Synthesis)
   - software: CASA
   - fitting: _not stated_
   - validation: Combined Tb 5-10% above single-dish map at same position  
  > "the averaged brightness temperature of the combined image is always larger (5$\ --\ $10%) than the temperature brightness at the same position in the single-dish map" (4.1 Data and Image Synthesis)
4. **Estimate noise**: Difference of XX and YY images; Gaussian fit width of difference distribution  
  > "the difference between the two polarizations can therefore be used as a proxy for the noise level in the final images" (4.2 Estimating the Noise Level)
   - software: CASA
   - assumption: Linear polarization negligible; XX and YY should be equal  
  > "the difference between the solar images synthesized from XX- and YY- data should be zero in principle" (4.2 Estimating the Noise Level)
   - fitting: Gaussian fit to difference distribution  
  > "From the width of the Gaussian function fitted to the distribution of the differential (Figure 9e), the noise level of the Band 3 synthesized image of the sunspot (Figure 7b) is 3.7 K" (4.2 Estimating the Noise Level of Solar Synthesized images)
   - validation: _not stated_
5. **Co-align with SDO/AIA and IRIS**: Coordinate conversion only for AIA; visual inspection for IRIS  
  > "the co-alignment is done only by the visual inspection." (4.4 Co-alignment between ALMA and other instruments)
   - fitting: _not stated_
   - validation: Co-alignment better than synthesized beam by comparing umbra edge  
  > "the precision of the co-alignment appears to be better than the size of the synthesized beam" (4.4 Co-alignment between ALMA and other instruments)

## Software

- **CASA** : Calibration, clean mosaic imaging, feather combination, TP map reduction  
  > "was used to calibrate and image the SV data." (4.1 Data and Image Synthesis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Noise level Band 3 sunspot image | 3.7 | not stated | K | 4 | is 3.7 K when the integration time is six seconds and the integration bandwidth is 8 GHz |
| Noise level Band 6 sunspot image | 9.8 | not stated | K | 4 | estimate the noise level to be 9.8 K |
| Synthesized beam Band 3 | 4.9 x 2.2 | not stated | arcsec | 2 | 4.9$^{\prime\prime}$$\times$2.2$^{\prime\prime}$ |
| Shortest baseline heterogeneous array | 7.6 m (34.3" at 239 GHz) | not stated | m | 0 | the shortest baseline measured is 7.6 m, corresponding to an angular scale of 34.3$^{\prime\prime}$ at 239 GHz |

## Qualitative findings

- MD modes preferable to solar filters for non-flaring Sun  
  > "the use of MD modes is preferable over the use of SFs for the non-flaring Sun" (2.2 Receiver Gain Reduction)

## Claim tuples

- H: Can ALMA image the Sun interferometrically with standard calibration plus Tant correction? | E: Commissioning Dec 2015, MD2 mode mosaics of sunspot and limb in Bands 3 and 6 | R: Images with beams of a few arcsec and noise 3.7–9.8 K | F: Solar interferometric imaging works and reveals new features | **supported**
- H: Do stepped attenuators require extra phase calibration? | E: 3C279 observed with varied attenuator states | R: Phase variation std 0.3–0.6 deg | F: No additional calibration needed | **supported**
- H: Does combining interferometer and TP maps yield consistent brightness temperature? | E: feather with default parameters | R: Combined 5–10% brighter than single dish | F: Feather parameters need tuning | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Robust 1.0 reduces weight of long 7m–12m baselines causing stripes  
  > "We attribute this to undue weight being given to longer interferometric baselines." (4.1 Data and Image Synthesis)
- Alternative: Solar filters rejected for non-flaring Sun due to calibration drawbacks  
  > "their use introduces enough disadvantages to consider whether an alternative approach may be more attractive" (2.2 Receiver Gain Reduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Robust value not fully optimized  
  > "The value is not fully optimized, and the most suitable value might depends on the target and array configuration." (4.1 Data and Image Synthesis)
- Limitation (authors): Limb artifacts from incomplete uv sampling; only ~30 antennas  
  > "The stripes are non-physical artifacts due to incomplete sampling" (4.3 Imaging Artifacts Above the Solar Limb)
- Caveat (inferred, ours): Noise via XX–YY difference assumes no polarization and equal noise
- Caveat (inferred, ours): Only three datasets, no quantitative absolute Tb validation
- Caveat (inferred, ours): Co-alignment precision judged qualitatively

## Reproducibility

- Data public (paper): SV data released by JAO and downloadable from ALMA Science Portal  
  > "The solar SV data can be downloaded from the ALMA Science Portal web site hosted by each ARC." (4 ALMA Solar Imaging Examples)
- Products in archive: _not stated_
- Missing: Clean parameters (cell, size, niter, masks)
- Missing: CASA version
- Missing: Feather and TP correction factor details
- Data volume (inferred): tens of GB (three mosaic execution blocks plus TP data)
- Score (inferred): 5/5, Public SV data and key settings (robust, mosaic) given, but many imaging parameters and CASA version missing.
- Rediscovery candidate: no, Mostly instrument/technical description; few numeric results and incomplete recipe.

## Links

- Method: (cite: White17) (TP fast-scan mapping and Tant/Tsys procedure)
- Companion: (cite: White17) (Companion article on single-dish solar mapping)
- Related: ALMA solar commissioning campaigns
- Related: ALMA Cycle 4 Scientific Verification data

## Checks

```json
{
 "quotes": 51,
 "quotes_ok": 51,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.0.00020.SV"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2011.0.00001.CAL"
 ],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 41,
  "rate": 0.569
 },
 "evidence_ok": true
}
```
