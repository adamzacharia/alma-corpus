# Confirmation of Enhanced Long-wavelength Dust Emission in OMC 2/3

`2020ApJ...893...13M` | The Astrophysical Journal 2020 | first author: Mason, Brian | arXiv: 1905.05221 | DOI: 10.3847/1538-4357/ab734a

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation, milky_way_ism
- Question: Do new MUSTANG-2 3.3 mm and GBT 31 GHz observations of OMC 2/3 confirm enhanced long-wavelength dust emission relative to a modified blackbody fit to shorter wavelengths, and what could explain it?  
  > "Here we present new observations of OMC 2/3 collected with the MUSTANG-2 camera on the GBT which confirm this elevated emission." (abstract)
- Target **OMC 2/3 (Integral Shaped Filament)**: coordinates _not stated_; z/distance within 500 pc  
  > "OMC 2/3 is the richest known star-forming filament within 500 pc" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00662.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: ALMA Compact Array (7-m), archival, used only for line contamination check  
  > "These data covered OMC-2 and OMC-3 over a narrow ($91.2$ - $91.7$ GHz) frequency range at a spectral resolution of $\sim 35 \, {\rm kHz}$ with the ALMA Compact Array (ACA)." (2.3 Archival Data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: <90 arcsec  
  > "the nature of interferometry limits the scales recovered to $<90 \ensuremath{''}$ for the given projected antenna spacing in the 7-m array" (2.3 Archival Data)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: PI: D. Mardones; data shared by the PI  
  > "We thank Diego Mardones, Di Li, and Jeremy Ren for sharing their ALMA data" (Acknowledgments)
- Line: CH3CN not stated (not stated)
- Other facility **GBT MUSTANG-2**: 3.3 mm continuum map  
  > "MUSTANG-2 is a 215 pixel feedhorn coupled Transition Edge Sensor (TES) bolometer array with a bandpass of $75-105 \, {\rm GHz}$." (2.1 MUSTANG-2)
- Other facility **GBT Ka band**: 31 GHz photometry of 24 regions  
  > "The observations used the Caltech Continuum Backend to perform sensitive, wide-band continuum beam switching" (2.2 GBT 31 GHz Observations)
- Other facility **Herschel, SCUBA-2, GISMO, MAMBO**: 160 um to 2 mm archival maps for SEDs  
  > "2mm data from GISMO in the IRAM 30m; $450 \, {\rm \mu m}$ and $850 \, {\rm \mu m}$ SCUBA-2 maps from the JCMT Gould Belt Survey" (2.3 Archival Data)
- External data: 1.2 mm MAMBO map and GISMO 2 mm data  
  > "we bring to bear the $1.2 \, {\rm mm}$ MAMBO map presented in S14 along with the multi-wavelength dataset presented by S16" (2.3 Archival Data) [from Schnee et al. 2014 (cite: schnee2014); Sadavoy et al. 2016 (cite: sadavoy2016)]
- External data: VLA 8.3 GHz source list for free-free correction  
  > "mapped this region at $8''$ resolution using the VLA at $8.3 \, {\rm GHz}$ and detected 14 sources." (2.2 GBT 31 GHz Observations) [from (cite: Reipurth1999)]
- Simulation/model as data: SPDUST2 spinning dust model spectra compared with residuals  
  > "We used the SPDUST2 code (cite: alihamoud2009; silsbee2011) to compute representative AME spectra." (4.3 Anomalous Microwave Emission)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: MUSTANG-2: 3C84 at 23.8 Jy (3.3 mm); GBT Ka: 3C138 at 0.86 Jy  
  > "We assume an interpolated flux density of $23.8 \, {\rm Jy}$ at $3.3 \, {\rm mm}$ based on the ALMA $91.5 \, {\rm GHz}$ measurements." (2.1 MUSTANG-2)
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

- GBT Ka-band calibration and reduction follow standard procedures  
  > "the data were calibrated and reduced using standard procedures described in (cite: mason2009)" (2.2 GBT 31 GHz Observations) [from (cite: mason2009)]
- Standard MBB fit as done for similar data  
  > "We first attempt a standard Modified Blackbody (MBB) fit, as done before for very similar data in S16." (3.2.1 Fitting) [from S16 (cite: sadavoy2016)]

### Not stated but needed to reproduce (our reading)

- ALMA ACA data calibration and imaging details (CASA version, line-free channels, continuum extraction)
- MBB fitting algorithm, priors, and parameter bounds
- Exact slice geometries
- Herschel/SCUBA-2 convolution and processing details

## Analysis recipe

1. **check line contamination in 3 mm continuum with ACA**: Used ACA spectral data to find lines and excise them, compare continuum fluxes with MUSTANG-2  
  > "While several spectral lines are evident (e.g. ${\rm CH_3 CN}$), their excision changes the integrated continuum fluxes by $<2\%$." (4.1 Spectral Line Contamination)
   - software: CASA
   - fitting: _not stated_
   - validation: ACA source fluxes agree with MUSTANG-2 within a few percent  
  > "Furthermore the ACA-observed source fluxes agree with the MUSTANG-2 source fluxes within a few percent." (4.1 Spectral Line Contamination)
2. **extract SEDs along slices**: Convolve to 25'' resolution, extract profiles along 24 slices, remove mean and slope, take peak as SED value; 10% calibration uncertainty per point  
  > "We take the peak value of the sky brightness across a slice to be the value of the Spectral Energy Distribution (SED) at that wavelength" (3.1 SED Extraction)
   - fitting: _not stated_
   - validation: _not stated_
3. **fit modified blackbody variants**: Fit MBB2mm, MBB2mm_ext, MBBall, MBBall_2beta (break at 120 GHz); F-test for extra parameter  
  > "MBBall_2beta: same as MBBall, but a spectral break is introduced at $120 \, {\rm GHz}$ with an independent emissivity index $\beta'$ to model long wavelength emission." (3.2 Modeling)
   - fitting: chi-squared minimisation evaluated at response-weighted frequencies  
  > "For purposes of fitting and evaluating $\chi^2$, the MBB is evaluated at each instrument’s response-weighted frequency $\nu_0$" (3.2 Modeling)
   - validation: Color-correction test shifts beta by median 0.3 sigma  
  > "The typical (median over regions) impact of the color correction on $\beta$ is $0.3 \sigma$ while for $\beta'$ it is $0.1 \sigma$" (3.2.3 Effect of Color Corrections)

## Software

- **CASA** : listed in software section; use not described  
  > "AplPy (cite: aplpy), Astropy (cite: astropy), CASA (cite: casa), ds9 (cite: ds9)" (Software)
- **SPDUST2** : spinning dust spectra  
  > "We used the SPDUST2 code (cite: alihamoud2009; silsbee2011) to compute representative AME spectra." (4.3 Anomalous Microwave Emission)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| median reduced chi2, MBB2mm | 1.65 | not stated | dimensionless | 3 | with a median over the 24 “slices” of $\chi_{n}^2 =
\chi^2/n = 1.65$ for $n = 4$ degrees of freedom |
| median reduced chi2, MBBall | 5.23 | not stated | dimensionless | 3 | with a median $\chi_{n}^2 = 5.23$ (minimum = $2.76$, maximum = $17.44$) for $n = 6$ |
| median reduced chi2, MBBall_2beta | 2.98 | not stated | dimensionless | 3 | with a median $\chi_{n}^2 = 2.98$ for $n = 5$ |
| 1 cm excess over extrapolated MBB | 5.19 | 1.03 | dimensionless | 3 | the 1 cm data points themselves are $5.19 \pm 1.03$ times as bright as the extrapolated MBB |
| 3.3 mm excess over extrapolated MBB | 2.01 | 0.15 | dimensionless | 3 | the $3.3 \, {\rm mm}$ data are $2.01 \pm 0.15$ times as bright as the model extrapolation |
| long-wavelength beta' (all regions) | 0.74 | 0.02 | dimensionless | 3 | All Regions (N=24)    / $1.65 \pm 0.02$ / $0.74 \pm  0.02$  / $16.5 \pm 0.3$ |
| beta' starless cores | 0.21 | 0.06 | dimensionless | 3 | though it is strikingly flatter for starless cores than in other regions ($\beta' = 0.21 \pm 0.06$) |
| change in continuum flux from line excision in ACA data | <2 | not stated | percent | 1 | their excision changes the integrated continuum fluxes by $<2\%$ |

## Qualitative findings

- Optically thin free-free, synchrotron and standard spinning-dust models do not explain the 3 mm and 1 cm excess; flatter intrinsic dust emissivity is favoured, possibly with AME.  
  > "The 3 mm and 1 cm data could be explained by a flatter dust emissivity at wavelengths shorter than 2 mm, potentially in concert with AME in some regions." (abstract)

## Claim tuples

- H: Is the elevated 3 mm emission seen by MUSTANG real? | E: Compare new MUSTANG-2 map with the MUSTANG-1 map pixel by pixel | R: median old/new ratio 0.95, slope 1.03 | F: The maps robustly agree | **supported**
- H: Can a single MBB describe the whole SED? | E: Fit MBB variants to 24 regional SEDs | R: 3 mm and 1 cm lie well above extrapolation; broken-beta model fits better | F: Long-wavelength excess is real | **supported**
- H: Does line contamination explain the 3 mm excess? | E: ACA spectra from 2013.1.00662.S | R: Line excision changes continuum by <2% | F: Unlikely | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Free-free, synchrotron and canonical AME rejected as main explanation  
  > "The spectrum of the long wavelength excess is inconsistent with both free-free emission and standard “Spinning Dust” models" (abstract)
- How they decided it was enough: _not stated_
- Limitation (authors): Limited spectral coverage does not support more parameters; broken power law residuals still show trends  
  > "The limited limited spectral coverage of our dataset in this regime however would not support introducing more parameters into the analysis" (3.2.2 Fitting all the data)
- Caveat (inferred, ours): ALMA is used only as a cross-check; details of ACA reduction are absent
- Caveat (inferred, ours): Fixed 10% calibration uncertainty and peak-along-slice extraction may bias SEDs
- Caveat (inferred, ours): Fits are chi-squared without stated priors or sampler

## Reproducibility

- Data public (paper): MUSTANG-2 map on Harvard Dataverse  
  > "The MUSTANG-2 map of OMC-2/3 is publicly available on the Harvard Dataverse (`doi:10.7910/DVN/EWN4RK`)." (2.1 MUSTANG-2)
- Products in archive: _not stated_
- Missing: Reduction pipeline for MUSTANG-2 (IDL, instrument team)
- Missing: Slice definitions beyond figure
- Missing: Fit code and settings
- Data volume (inferred): ACA part: a few GB; full analysis uses processed maps
- Score (inferred): 3/5, Processed maps and tables are available and the recipe is simple, but the ALMA processing and fit details are missing.
- Rediscovery candidate: no, Main results depend on non-ALMA single-dish data and unreleased reduction; ALMA part is a minor check.

## Links

- Method: Romero et al. 2019 (cite: romero2019) (Transfer function of the MUSTANG-2 IDL pipeline)
- Companion: Schnee et al. 2014 (cite: schnee2014) (Original MUSTANG 3.3 mm result)
- Companion: Sadavoy et al. 2016 (cite: sadavoy2016) (Herschel and GISMO SEDs of OMC 2/3)
- Related: JCMT Gould Belt Survey

## Checks

```json
{
 "quotes": 40,
 "quotes_ok": 40,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2013.0.00662.S"
 ],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 65,
  "stated": 26,
  "rate": 0.4
 },
 "evidence_ok": true
}
```
