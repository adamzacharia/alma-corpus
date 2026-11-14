# The First ALMA Observation of a Solar Plasmoid Ejection from an X-Ray Bright Point

`2017ApJ...841L...5S` | The Astrophysical Journal Letters 2017 | first author: Shimojo, Masumi | arXiv: 1704.04881 | DOI: 10.3847/2041-8213/aa70e3

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: sun
- Question: What are the thermal structure and physical parameters (temperature, density, mass, energy) of a plasmoid ejected from an X-ray bright point, from combined 100 GHz ALMA, AIA EUV and XRT data?  
  > "This paper reports the physical parameters of the plasmoid obtained by combining the radio, EUV and X-ray data." (abstract)
- Target **SOL2015-12-17T19:44 plasmoid from X-ray bright point in NOAA12470**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00020.SV
- bands: central frequency 100 GHz  
  > "The central frequency of the solar observations is 100 GHz." (Observation)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 22 x 12m and 9 x 7m antennas  
  > "The telescope array included 22 $\times$ 12m antennas and 9 $\times$ 7m antennas during this observation." (Observation)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: synthesized beam 6.3" x 2.3"  
  > "The major and minor axes of the resulting synthesized beam are 6.3$^{\prime\prime}$ and 2.3$^{\prime\prime}$, respectively." (Observation)
- max recoverable scale: _not stated_
- sensitivity: ~11 K noise in 2-s images  
  > "found to be $\sim$11 K" (Observation)
- time on source: _not stated_
- observing dates: 2015 December 17  
  > "An ALMA observation of a solar active region at 100 GHz on 2015 December 17" (Introduction)
- pi or archival as stated: ALMA Science Verification data release (commissioning test observation)  
  > "The dataset has been provided by the ALMA observatory as a Science Verification (SV) data release." (Observation)
- Other facility **SDO/AIA**: EUV images (171, 193, 211, 304, 94 Å) and 1700 Å UV continuum  
  > "The time cadence of the EUV images is 12 seconds, and that of the UV continuum images (1700 Å) is 24 seconds." (Observation)
- Other facility **Hinode/XRT**: Al-thin filter soft X-ray images, 2" resolution, 30 s cadence  
  > "we use the XRT images observed with the Al-thin filter." (Observation)
- Other facility **Single-dish full-Sun observations**: absolute temperature scale/background  
  > "Single-dish observations of the full Sun were therefore taken to provide the absolute temperature scale (cite: White17)." (Observation)
- External data: Single-dish full-Sun data for absolute temperature scale  
  > "Single-dish observations of the full Sun were therefore taken to provide the absolute temperature scale (cite: White17)." (Observation) [from White et al. 2017 (cite: White17)]
- External data: AIA temperature response functions  
  > "The plotted values are estimated from the temperature responses of each band (cite: AIACal12)." (Thermal structure of the plasmoid) [from Boerner et al. 2012 (cite: AIACal12)]
- External data: XRT temperature response  
  > "Based on the temperature response of XRT (cite: XRTCal11)" (Plasmoid ejection observed with ALMA, AIA, and XRT) [from Narukage et al. 2011 (cite: XRTCal11)]

## Processing

### Calibration

- pipeline or manual: visibility calibration following Shimojo et al. 2017 method  
  > "We calibrated the visibility data following the method described in (cite: Shimojo17)" (Observation)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: self-calibration using image from entire observing period as reference to remove jitter  
  > "we carried out self-calibration using the image synthesized from the entire observing period as a reference" (Observation)

### Imaging

- task: images synthesized every 2 seconds  
  > "synthesized images every 2 seconds" (Observation)
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
- final beam: 6.3" x 2.3"  
  > "The major and minor axes of the resulting synthesized beam are 6.3$^{\prime\prime}$ and 2.3$^{\prime\prime}$, respectively." (Observation)
- final rms: ~11 K  
  > "found to be $\sim$11 K" (Observation)

### Inherited from earlier work

- Visibility calibration method  
  > "We calibrated the visibility data following the method described in (cite: Shimojo17)" (Observation) [from Shimojo et al. 2017 (cite: Shimojo17)]
- Noise level estimation method  
  > "The noise level of the synthesized 2-second 100 GHz images is estimated using the method in (cite: Shimojo17)" (Observation) [from Shimojo et al. 2017 (cite: Shimojo17)]

### Not stated but needed to reproduce (our reading)

- CASA version and imaging parameters (weighting, deconvolver, cell/image size)
- Details of the Shimojo17 calibration and noise-estimation procedures
- Self-calibration solution interval
- Exact time windows for signal and background averaging
- Gaunt factor formula used
- Exact AIA response values and DEM/response tool used
- ALMA project/dataset identifier for retrieval beyond the SV acknowledgement

## Analysis recipe

1. **calibrate and image ALMA data**: Calibrate per Shimojo17, 2-s imaging, self-calibration against full-period image, scale with single-dish background  
  > "we carried out self-calibration using the image synthesized from the entire observing period as a reference, and this successfully removed the artificial motion." (Observation)
   - fitting: _not stated_
   - validation: jitter removal checked in 2-s movie  
  > "this successfully removed the artificial motion" (Observation)
2. **co-align ALMA, AIA and XRT**: convert ALMA RA/DEC to heliocentric; visual inspection for XRT  
  > "The co-alignment between the ALMA images and the other wavelengths is achieved by the conversion of the a priori coordinate system of the ALMA images from RA/DEC to heliocentric." (Observation)
   - fitting: _not stated_
   - validation: precision better than 2" ALMA vs AIA; up to 5" vs XRT  
  > "the precision of the co-alignment is better than 2$^{\prime\prime}$ for ALMA with respect to AIA" (Observation)
3. **measure plasmoid enhancements**: time-averaged intensities during a window minus background from another window, in 100 GHz and AIA 171/193/211  
  > "The intensity enhancement corresponding to the plasmoid is derived from the time-averaged intensities during the period indicated by the dotted lines" (Thermal structure of the plasmoid)
   - parameter: enhancements 145 K, 68.1, 49.8, 20.2 DN/s/pixel  
  > "The averaged enhancements that should be explained by the hypotheses are 145 K, 68.1 DN/sec/pixel, 49.8 DN/sec/pixel, and 20.2 DN/sec/pixel" (Thermal structure of the plasmoid)
   - assumption: line-of-sight depth 4" (~3000 km), filling factor unity  
  > "we assume that the line-of-sight depth of the plasmoid is 4$^{\prime\prime}$ ($\sim$3000 km)" (Thermal structure of the plasmoid)
   - fitting: _not stated_
   - validation: 304 Å excluded due to resonance scattering  
  > "we cannot obtain reliable quantitative results from 304 Å for the reasons given earlier" (Thermal structure of the plasmoid)
4. **test isothermal/multithermal hypotheses**: compute density required vs temperature for each band using AIA responses and free-free emission (Lang80); find where curves intersect  
  > "we use the standard formula for thermal free-free emission (cite: Lang80)" (Thermal structure of the plasmoid)
   - assumption: filling factor unity  
  > "we assume that the filling factor of the plasma is unity" (Thermal structure of the plasmoid)
   - fitting: _not stated_
   - validation: XRT non-detection constrains T<1 MK  
  > "we conclude that the plasmoid does not include significant coronal plasma at temperatures $>$1 MK" (Plasmoid ejection observed with ALMA, AIA, and XRT)
5. **derive mass and energies**: from optically thin parameters: T=1e5 K, volume 3e25 cm3, n=3e9 cm-3  
  > "the mass of the plasmoid is of order 2$\times$10$^{11}$ g and the thermal and kinetic energies are 5$\times$10$^{24}$ ergs and 2$\times$10$^{24}$ ergs" (Thermal structure of the plasmoid)
   - fitting: _not stated_
   - validation: compared with polar jets (Sako13) and active-region jets (Liu16)  
  > "These values are an order of magnitude smaller than, for example, the averaged thermal energy of polar X-ray jets" (Thermal structure of the plasmoid)

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| plasmoid projected velocity | 40 | not stated | km/s | 0 | The plasmoid moves at a projected velocity of about 40 km/s |
| 100 GHz enhancement | 145 | not stated | K | 3 | 145 K, 68.1 DN/sec/pixel, 49.8 DN/sec/pixel, and 20.2 DN/sec/pixel |
| isothermal optically thin temperature range | 8.0e4 to 1.4e5 | not stated | K | 4 | around a temperature of 8.0$\times10^{4}\sim$1.4$\times$10$^{5}$ K and density of 3.5$\sim$3.9$\times$10$^{9}$ cm$^{-3}$ |
| isothermal optically thin density | 3.5-3.9e9 | not stated | cm^-3 | 4 | density of 3.5$\sim$3.9$\times$10$^{9}$ cm$^{-3}$ |
| plasmoid mass | 2e11 | order of magnitude | g | 5 | the mass of the plasmoid is of order 2$\times$10$^{11}$ g |
| thermal energy | 5e24 | not stated | erg | 5 | the thermal and kinetic energies are 5$\times$10$^{24}$ ergs and 2$\times$10$^{24}$ ergs |
| kinetic energy | 2e24 | not stated | erg | 5 | the thermal and kinetic energies are 5$\times$10$^{24}$ ergs and 2$\times$10$^{24}$ ergs |

## Qualitative findings

- Plasmoid seen at 100 GHz and AIA EUV but not in XRT, so it lacks significant >1 MK plasma and is not chromospheric.  
  > "This confirms that the event is not predominantly chromospheric." (Plasmoid ejection observed with ALMA, AIA, and XRT)

## Claim tuples

- H: Is the plasmoid an optically thick isothermal 10^4 K source at 100 GHz? | E: Compare required densities from AIA and ALMA enhancements | R: AIA would require ~1e12 cm^-3, which would produce EUV absorption | F: Rejected | **refuted**
- H: Is the plasmoid isothermal and optically thin at 100 GHz? | E: Find intersection of density-temperature curves | R: Curves cluster near ~1e5 K, ~4e9 cm^-3 | F: Reasonable | **supported**
- H: Can a multi-thermal cool core plus hot sheath explain the data? | E: Constrain sheath temperature with XRT and AIA | R: Sheath 5e5-1 MK; core 1e4 K | F: Viable alternative | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Combine ALMA with EUV and X-ray because He II 304 Å is hard to use quantitatively  
  > "it is difficult to use the He II line data for quantitative analysis because the intensity of the line depends strongly on resonance scattering" (Introduction)
- Alternative: Optically thick isothermal 10^4 K plasmoid rejected  
  > "it cannot be an optically-thick 10$^{4}$ K isothermal source at 100 GHz." (Hypothesis 1): Isothermal plasma that is optically thick at 100 GHz)
- How they decided it was enough: _not stated_
- Limitation (authors): ALMA-XRT alignment uncertain by up to 5"  
  > "the positional uncertainty between ALMA and XRT might be as poor as 5$^{\prime\prime}$" (Observation)
- Limitation (authors): Three-dimensional path unknown  
  > "although we have no way of determining the exact path in three dimensions" (Plasmoid ejection observed with ALMA, AIA, and XRT)
- Caveat (inferred, ours): No uncertainties on derived densities, temperatures, mass, energies
- Caveat (inferred, ours): Line-of-sight depth assumed equal to width
- Caveat (inferred, ours): Plasmoid size comparable to ALMA beam, so unresolved
- Caveat (inferred, ours): Intersection of curves is qualitative, not a formal fit
- Caveat (inferred, ours): Only 100 GHz single frequency so optical depth is not measured

## Reproducibility

- Data public (paper): ALMA Science Verification data release  
  > "The dataset has been provided by the ALMA observatory as a Science Verification (SV) data release." (Observation)
- Products in archive: _not stated_
- Missing: Calibration details (in Shimojo17)
- Missing: Single-dish data (White17)
- Missing: Averaging time windows
- Missing: AIA response functions and Gaunt factor specifics
- Data volume (inferred): tens of GB (solar SV visibilities, 2-s cadence) plus small AIA/XRT cutouts
- Score (inferred): 4/5, Public SV data and simple analysis, but calibration is deferred to another paper, there is no software or version information, and key time windows and settings are only given in figures.
- Rediscovery candidate: no, Data are public, but the calibration recipe is deferred to Shimojo17 and the analysis is a qualitative curve-intersection rather than a fully specified numeric pipeline.

## Links

- Method: Shimojo et al. 2017, Sol. Phys. (cite: Shimojo17) (ALMA solar calibration and noise estimation method)
- Method: White et al. 2017, Sol. Phys. (cite: White17) (single-dish full-Sun data for absolute temperature scale)
- Related: ALMA solar commissioning campaign
- Related: ALMA Science Verification data release

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
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 39,
  "rate": 0.534
 },
 "evidence_ok": true
}
```
