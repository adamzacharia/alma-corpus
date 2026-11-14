# Distributions of molecules in the circumnuclear disk and surrounding starburst ring in the Seyfert galaxy NGC 1068 observed with ALMA

`2014PASJ...66...75T` | Publications of the Astronomical Society of Japan 2014 | first author: Takano, Shuro | arXiv: 1406.0782 | DOI: 10.1093/pasj/psu052

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, astrochemistry, agn_and_quasars
- Question: How are molecules distributed between the circumnuclear disk and the starburst ring of NGC 1068, and what does this say about AGN and starburst effects on molecular abundances?  
  > "These observations were motivated to study the effects of an active galactic nucleus and its surrounding starburst ring on molecular abundances." (abstract)
- Target **NGC 1068**: coordinates _not stated_; z/distance 14.4 Mpc  
  > "Throughout the paper, we assume that the distance of NGC 1068 is 14.4 Mpc (cite: tully1988; bland1997); at this distance, $1''$ corresponds to 72 pc." (1 Introduction); distance from Tully 1988; Bland-Hawthorn et al. 1997  
  > "Throughout the paper, we assume that the distance of NGC 1068 is 14.4 Mpc (cite: tully1988; bland1997); at this distance, $1''$ corresponds to 72 pc." (1 Introduction)

## Data provenance

- ALMA projects: 2011.0.00061.S
- bands: Band 3 (100 GHz region)  
  > "The receivers in band 3 (100 GHz region) were used." (2 Observations and data reduction)
- frequencies and spectral setup: 4 spectral windows: 2 LSB (~96–100 GHz), 2 USB (~108–111 GHz); each 1875 MHz, 3840 channels, 488 kHz resolution  
  > "Each spectral window covered 1875 MHz with 3840 channels resulting in a frequency resolution of 488 kHz." (2 Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: 16 12m antennas  
  > "The 16 antennas available were in the compact configuration." (2 Observations and data reduction)
- configurations: compact  
  > "The 16 antennas available were in the compact configuration." (2 Observations and data reduction)
- baselines: _not stated_
- angular resolution: ~4''x2'' (290 pc x 140 pc)  
  > "with an angular resolution of $\sim4''\times2''$ (290 pc$\times$140 pc)" (abstract)
- max recoverable scale: _not stated_
- sensitivity: rms ~1.1–1.7 mJy/beam  
  > "The achieved noise level (rms) was $\sim$1.1–1.7 mJy beam$^{-1}$ depending on the spectral window and image region." (2 Observations and data reduction)
- time on source: about 110 minutes total including calibration and overheads  
  > "The total observational time was about 110 minutes including calibration and overheads." (2 Observations and data reduction)
- observing dates: January 9 and 10, 2012  
  > "Date | January 9 and 10, 2012" (Table 1)
- pi or archival as stated: _not stated_
- Line: 13CO J=1-0 (110201.353 MHz)
- Line: C18O J=1-0 (109782.160 MHz)
- Line: CS J=2-1 (97980.968 MHz)
- Line: CH3OH JK=2K-1K (96741.42 MHz)
- Line: HC3N J=11-10, 12-11 (100076.389, 109173.634 MHz)
- Other facility **NRO 45m and IRAM 30m**: Single-dish 13CO and CS fluxes for flux recovery comparison  
  > "We compared the flux obtained from ALMA with those from single dish telescopes (NRO 45m and IRAM 30m) to estimate the recovery of the flux with the interferometer." (3.4 Comparison of flux with single dish telescopes)
- External data: Star formation rates of regions in the starburst ring  
  > "we studied the relation of methanol intensity to the star-formation rate (cite: tsai2012) in those regions with relatively strong methanol emission" (4.2 CH3OH) [from Tsai et al. 2012 (cite: tsai2012)]
- External data: IRAM 30m 13CO flux (12.8 K km/s) and C18O/13CO ratio 0.28  
  > "The corresponding value obtained with the 30m telescope is $\sim$12.8 K km s$^{-1}$ (cite: aladro2013)" (3.4 Comparison of flux with single dish telescopes) [from Aladro et al. 2013 (cite: aladro2013)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Continuum-subtracted calibrated data and cubes provided by the ARC  
  > "We used continuum subtracted calibrated data (measurement set) and image cubes provided by the ALMA Regional Center." (2 Observations and data reduction)
- flux calibrator: Callisto (bandpass J0423-013, phase J0339-017)  
  > "Flux calibrator | Callisto" (Table 1)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA (mainly ver. 3.4); images made from the measurement set for 13CN, HNCO, CH3CN  
  > "For molecular lines with no provided image cubes ($^{13}$CN, HNCO, and CH$_3$CN), we obtained images from the measurement set above." (2 Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Provided continuum-subtracted data  
  > "We used continuum subtracted calibrated data (measurement set)" (2 Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: Applied before spectral extraction and flux comparison  
  > "attenuation due to the primary beam pattern of the ALMA 12m antennas was corrected." (3.2 Spectra at the circumnuclear disk and the starburst ring (southwest))
- array combination: _not stated_
- smoothing: Velocity resolution ~19 km/s (13 channel binning); USB images convolved to lowest-frequency LSB beam  
  > "$\sim$19.0 at 100 GHz (13 channel binning)" (Table 1)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Phase center and systemic velocity (1150 km/s)  
  > "The position and the velocity were taken from (cite: schinn2000)." (2 Observations and data reduction) [from (cite: schinn2000)]

### Not stated but needed to reproduce (our reading)

- Imaging weighting/robust, cell and image size, deconvolver and clean thresholds
- Exact CASA version for cubes made by ARC and the ARC pipeline version
- Line-free channels and mask or velocity range used for moment 0 maps
- Phase center coordinates and the SW ring position (blank in text)
- Aperture centering details and the single-dish beam sizes (blank in text)
- Gaussian fit procedure details

## Analysis recipe

1. **Make integrated intensity maps**: Moment 0 maps from cubes using all pixel flux values  
  > "The images of integrated intensity (moment 0 maps) were made using pixels with all flux values in the image cubes." (2 Observations and data reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract spectra at AGN and SW ring and fit lines**: Spectra from cleaned images (beam-matched, PB-corrected) at the continuum peak and 13CO 3-2 peak; Gaussian fits  
  > "The detected lines were Gaussian fitted, and the line parameters obtained are summarized in Table [2]" (3.2 Spectra at the circumnuclear disk and the starburst ring (southwest))
   - software: CASA
   - fitting: Gaussian line fits  
  > "The detected lines were Gaussian fitted, and the line parameters obtained are summarized in Table [2](#tab:param)." (3.2 Spectra at the circumnuclear disk and the starburst ring (southwest))
   - validation: _not stated_
3. **Measure CND and total flux and ratio**: Flux in 10'' circle (CND) and 55'' circle (total) centered on the continuum peak; ratio CND/Total used for classification  
  > "Flux within the circle with the diameter of 55"." (Table 3)
   - fitting: _not stated_
   - validation: Errors from pixel standard deviation; systematics not included  
  > "The error for each flux is obtained from the standard deviation of the pixel values of the image, but the systematic deviation is not included." (3.3 Total flux and the flux at the circumnuclear disk)
4. **Check flux recovery against single dishes**: Convolve ALMA PB-corrected data to the 45m and 30m beams and compare K km/s  
  > "Therefore, the recovered flux is about 92 %." (3.4 Comparison of flux with single dish telescopes)
   - fitting: _not stated_
   - validation: Comparison with NRO 45m and IRAM 30m  
  > "We compared the flux obtained from ALMA with those from single dish telescopes (NRO 45m and IRAM 30m) to estimate the recovery of the flux with the interferometer." (3.4 Comparison of flux with single dish telescopes)

## Software

- **CASA** mainly 3.4: Data reduction and imaging  
  > "The data were reduced with the reduction software CASA (mainly with ver. 3.4)." (2 Observations and data reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| C18O/13CO total flux ratio | ~0.34 | not stated | dimensionless | 3 | the obtained value is $\sim$0.34 |
| CND/Total flux ratio, 13CO | 0.0217 | 0.0005 | dimensionless | 3 | 0.0217$\pm$0.0005 |
| CND/Total flux ratio, CS | 0.37 | 0.01 | dimensionless | 3 | 0.37$\pm$0.01 |
| CND/Total flux ratio, HC3N 12-11 | 0.73 | 0.06 | dimensionless | 3 | 0.73$\pm$0.06 |
| Recovered 13CO flux vs NRO 45m | ~92 | not stated | % | 4 | Therefore, the recovered flux is about 92 %. |
| Recovered CS flux vs NRO 45m | ~74 | not stated | % | 4 | Therefore, the recovered flux is about 74 %. |

## Qualitative findings

- HC3N, SO, CH3CN concentrated in CND despite easy dissociation, implying shielding from X-rays/UV  
  > "our results indicate that these molecules must be effectively shielded." (abstract)

## Claim tuples

- H: Molecular distributions differ between CND and starburst ring | E: Band 3 imaging of 10 lines and CND/Total flux ratios | R: Ratios 0.7–1.0 (CND), 0.1–0.4 (both), 0.0–0.02 (ring) | F: Three categories of distributions | **supported**
- H: CH3OH in the ring tracks star formation | E: Compare strong methanol regions with SFR from Tsai et al. | R: SFR 1.40±0.54 vs 1.26±0.46 for all regions | F: No strong correlation between methanol and SFR | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Low S/N and limited resolution hinder precise classification  
  > "Higher spatial resolution and better signal-to-noise ratio are desirable for this more precise classification" (4.1 Classification of molecular distributions)
- Caveat (inferred, ours): Qualitative classification with no abundance or excitation modelling
- Caveat (inferred, ours): Interferometric flux loss not corrected
- Caveat (inferred, ours): Cycle 0 resolution blends CND structure

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: Calibrated data and cubes provided by the ARC  
  > "We used continuum subtracted calibrated data (measurement set) and image cubes provided by the ALMA Regional Center." (2 Observations and data reduction)
- Missing: Imaging parameters
- Missing: Moment map velocity ranges
- Missing: Phase center and aperture centers
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Public data and simple flux measurements, but imaging and moment settings are unstated.
- Rediscovery candidate: yes, Data are archival ALMA Cycle 0, and the flux ratios and line parameters are numeric tables that can be redone.

## Links

- Companion: Nakajima et al. in preparation (ALMA band 7 data and abundances)
- Companion: Tosaki et al. in preparation (Giant molecular associations and SFR relation)

## Checks

```json
{
 "quotes": 47,
 "quotes_ok": 47,
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
  "facts": 62,
  "stated": 32,
  "rate": 0.516
 },
 "evidence_ok": true
}
```
