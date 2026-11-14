# ALMA Detection of Extended [C II] Emission in Himiko at z = 6.6

`2018ApJ...854L...7C` | The Astrophysical Journal Letters 2018 | first author: Carniani, S. | arXiv: 1712.01890 | DOI: 10.3847/2041-8213/aaab45

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: high_z_galaxies
- Question: Is [CII] 158um emission detected in the Lya emitter Himiko at z=6.595 when Cycle 0 and Cycle 1 ALMA data are combined, how does it compare with the local L[CII]-SFR relation, and how does it relate to the UV clumps?  
  > "In this paper we present an analysis of both Cycle 0 and Cycle 1 data." (Introduction)
- Target **Himiko**: coordinates Clump A: RA 2:17:57.61, Dec -5:08:44.96 (J2000)  
  > "Himiko is located in the Ultra Deep South field." (Introduction); "$z_{\rm Ly\alpha}$ | 6.595" (Table 2); z/distance z_Lya = 6.595; z_[CII] = 6.5913±0.0004  
  > "Himiko is located in the Ultra Deep South field." (Introduction); "$z_{\rm Ly\alpha}$ | 6.595" (Table 2); distance from Lya spectroscopy (Keck/DEIMOS, VLT/X-shooter) and [CII] from ALMA  
  > "Himiko is located in the Ultra Deep South field." (Introduction); "$z_{\rm Ly\alpha}$ | 6.595" (Table 2)

## Data provenance

- ALMA projects: 2011.0.00115.S, 2012.1.00033.S
- bands: Band 6  
  > "Himiko was observed with ALMA in band 6 in July 2012 and July 2015" (2 Observation and data reduction)
- frequencies and spectral setup: 4 spectral windows of 1.875 GHz (7.5 GHz total), 0.488 kHz resolution; one window on [CII] at 250.24 GHz  
  > "One of the four spectral windows (each 1.875 GHz Wide) was set to the expected frequency of the [Cii] line at $z=6.595$ ($\nu_{\rm obs}$=250.24 GHz)." (2 Observation and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: Cycle 0: semi-compact, 25 antennae, max baseline 440 m; Cycle 1: extended, 44 antennae, baselines up to 1600 m  
  > "An extended-array configuration was instead used for Cycle-1 observations, with 44 12-m antennae and baseline lengths up to 1600 m." (2 Observation and data reduction)
- baselines: _not stated_
- angular resolution: Cycle 0 0.81x0.57 arcsec; Cycle 1 0.28x0.22; combined 0.39x0.31; combined+taper 0.48x0.40  
  > "combined and uv-tapered | 6.4 | 44 | 0.48$''$$\times$0.40$''$ | 11 | 101" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: Combined continuum 9 uJy/beam; line 88 uJy per 100 km/s channel  
  > "achieving a continuum sensitivity of 9 $\mu$Jy/beam and an angular resolution of $\sim$0.30$''$ at the observed frequency of [Cii]" (2 Observation and data reduction)
- time on source: 3.2 h per program (6.4 h combined)  
  > "The total on-source integration time was 3.2h for both programs." (2 Observation and data reduction)
- observing dates: July 2012 and July 2015  
  > "Himiko was observed with ALMA in band 6 in July 2012 and July 2015" (2 Observation and data reduction)
- pi or archival as stated: _not stated_
- Line: [CII] 2P3/2 -> 2P1/2 (157.74 um)
- Other facility **HST WFC3**: J125 and H160 rest-frame UV imaging showing clumps A, B, C  
  > "Hubble Space Telescope (HST) observations with WFC3 in bands J$_{125}$ and H$_{160}$" (Introduction)
- Other facility **VLT/X-shooter**: Lya spectrum and redshift  
  > "the optical spectrum of the Ly$\alpha$ line obtained from X-shooter observations (cite: Zabl:2015)" (3.2 [CII] line emission)
- Other facility **Gaia DR1**: astrometric registration of ALMA and HST  
  > "matching ALMA calibrator and foreground sources to the GAIA Data Release 1 catalogue" (2 Observation and data reduction)
- External data: Local L[CII]-SFR relation  
  > "our detection places Himiko along the local L$_{\rm[CII]}$-SFR given by (cite: De-Looze:2014)" (3.2 [CII] line emission) [from De-Looze:2014]
- External data: HST UV clump photometry and Lya data / SED metallicity  
  > "Clumps A and B are separated by a projected distance of 6.4 kpc, while the other two clumps have a separation of 2.5 kpc (cite: Zabl:2015)." (1 Introduction) [from Zabl:2015]
- External data: Cycle 0 [CII] upper limit L<5.4e7 Lsun  
  > "placing an upper limit for the [Cii] luminosity at L$_{\rm[CII]}$$<5.4\times10^{7}$ L$_{\odot}$" (Introduction) [from Ouchi:2013]

## Processing

### Calibration

- pipeline or manual: Standard ALMA reduction scripts delivered with the data release  
  > "The two datasets have been calibrated by using the standard scripts for ALMA reduction corresponding to the release data of the observations." (2 Observation and data reduction)
- casa version: CASA 3.4.0 (Cycle 0) and 4.7.2 (Cycle 1)  
  > "We used the software CASA (cite: McMullin:2007) version 3.4.0 and 4.7.2 respectively for the two datasets." (2 Observation and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Callisto, Neptune, Ceres, J0238+166  
  > "The absolute flux scale was established by observations of Callisto, Neptune, Ceres, and J0238+166." (2 Observation and data reduction)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean  
  > "by using the CASA task clean with a natural weighting" (2 Observation and data reduction)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "by using the CASA task clean with a natural weighting" (2 Observation and data reduction)
- uv taper: 0.2 arcsec  
  > "we have produced a spatially smoothed cube using a uv tapering of 0.2$''$" (2 Observation and data reduction)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum map from line-free channels; cubes with 5 km/s channels  
  > "we have generated the continuum map from the line-free channels and cubes with spectral channels of 5 km/s" (2 Observation and data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.39x0.31 arcsec combined; 0.48x0.40 arcsec tapered  
  > "combined | 6.4 | 44 | 0.39$''$$\times$0.31$''$ | 9 | 88" (Table 1)
- final rms: _not stated_

### Inherited from earlier work

- Continuum L_IR assumption: grey-body T=35 K, beta=1.5  
  > "if assuming grey-body emission with a dust temperature of 35 K and a spectral emissivity index of 1.5 (cite: Ota:2014; Schaerer:2015; Willott:2015)" (3.1 Continuum) [from Ota:2014; Schaerer:2015; Willott:2015]
- L_IR-SFR_IR conversion  
  > "If we assume the ${\rm L_{IR}-SFR_{IR}}$ relation presented in (cite: Kennicutt:2012)" (3.1 Continuum) [from Kennicutt:2012]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for continuum
- clean masks, threshold, iterations, cell and image size
- Which Cycle 0 calibration/flagging beyond standard scripts
- How the total flux and 9 sigma significance were computed
- Procedure for the Gaussian fits and size deconvolution
- SFR_UV conversion and the metallicity-relation details
- Method for the 100 km/s upper limits

## Analysis recipe

1. **Calibrate and image each dataset**: Standard ALMA scripts, then CASA clean with natural weighting for continuum and 5 km/s cubes  
  > "The two datasets have been calibrated by using the standard scripts for ALMA reduction corresponding to the release data of the observations." (2 Observation and data reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: Cycle-0 sensitivity and resolution agree with Ouchi et al. 2013  
  > "are in agreement with those presented by (cite: Ouchi:2013)" (2 Observation and data reduction)
2. **Combine datasets and taper**: Joint imaging of both programs, plus uv-tapered cube to recover extended emission  
  > "The imaging of the combined dataset has been performed by using CASA version 4.7.2 and natural weighting" (2 Observation and data reduction)
   - software: CASA
   - parameter: uv taper 0.2 arcsec  
  > "using a uv tapering of 0.2$''$ so to recover the spatially extended emission" (2 Observation and data reduction)
   - fitting: _not stated_
   - validation: Line marginally detected at same location in the two individual datasets  
  > "the line is marginally detected at the same location in the two individual datasets" (3.2 [CII] line emission)
3. **Extract [CII] map, spectrum and luminosity**: Moment map over 270 km/s centred at -185 km/s; spectrum extracted within the 2 sigma contours, rebinned to 40 km/s  
  > "we extract the [Cii] spectrum over a region within the $2\sigma$ [Cii] contours" (3.2 [CII] line emission)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
4. **Decompose into components**: Channel-map analysis of the non-smoothed combined cube; 2D elliptical Gaussian fit to channel map  
  > "By fitting a 2D elliptical Gaussian profile to the channel map" (3.3 Multi-component system)
   - fitting: 2D elliptical Gaussian  
  > "By fitting a 2D elliptical Gaussian profile to the channel map" (3.3 Multi-component system)
   - validation: _not stated_
5. **Continuum upper limit and SFR_IR**: 3 sigma limit converted to L_IR with grey-body, then to SFR_IR  
  > "We estimate a 3$\sigma$ upper limit on the continuum emission ${\rm S_{158\mu m}} <27 \ \mu$Jy" (3.1 Continuum)
   - assumption: T_d=35 K, beta=1.5  
  > "a dust temperature of 35 K and a spectral emissivity index of 1.5" (3.1 Continuum)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 3.4.0 and 4.7.2: Calibration, clean imaging of continuum and cubes  
  > "We used the software CASA (cite: McMullin:2007) version 3.4.0 and 4.7.2 respectively for the two datasets." (2 Observation and data reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| [CII] integrated flux | 108 | ±12 | mJy km/s | 3 | ${\rm S_{[CII]}\Delta v=108\pm12}$ mJy km/s |
| L[CII] | 1.2e8 | ±0.2e8 | Lsun | 3 | ${\rm L_{[CII]}=(1.2\pm0.2)}\times$10$^{8}$ L$_{\odot}$ |
| [CII] offset from Lya | -145 | ±15 | km/s | 3 | The line is offset by $-145\pm15$ km/s relative to the $z_{\rm Ly\alpha}$ |
| [CII] line width | 130 | ±30 | km/s | 3 | has a line width of $130\pm30$ km/s |
| Continuum upper limit | <27 | 3 sigma | uJy | 5 | ${\rm S_{158\mu m}} <27 \ \mu$Jy |
| L[CII] of A_[CII] | 0.85e8 | ±0.13e8 | Lsun | 4 | We measure L$_{\rm[CII]}$$=(0.85\pm0.13)\times10^{8}$ L$_{\odot}$ |
| L[CII] of B_[CII] | 0.50e8 | ±0.13e8 | Lsun | 4 | we infer a [Cii] luminosity L$_{\rm[CII]}$$=(0.50\pm0.13)\times10^{8}$ L$_{\odot}$ |
| Total [CII] size | (3.9±1.1) x (1.7±1.1) | ±1.1 | kpc | 3 | ${\rm (3.9\pm1.1) \ kpc \ \times(1.7\pm1.1) \ kpc}$ |

## Qualitative findings

- Cycle 1 extended-array data miss about 40% of the total [CII] emission as diffuse emission is resolved out  
  > "a fraction ($\sim40\%$) of the total [Cii] emission is missed" (3.2 [CII] line emission)

## Claim tuples

- H: Himiko is [CII]-deficient relative to the local L[CII]-SFR relation | E: Combined Cycle 0 and 1 data with uv taper | R: 9 sigma detection, L[CII]=1.2e8 Lsun | F: Himiko lies on the local relation; earlier upper limits were too low | **supported**
- H: [CII] morphology follows the UV clumps | E: Channel maps of the combined cube | R: Extended component (~4 kpc) at the Lya peak and an unresolved component at clump B | F: [CII] and UV trace different regions | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Putative emission at clump C (S/N=3.2) treated as non-detection; upper limits assume FWHM=100 km/s  
  > "Because of the low significance (S/N=3.2), the emission can be spurious due to noise fluctuation" (3.3 Multi-component system)
- Caveat (inferred, ours): Peak significance is only 5.5 sigma; 9 sigma depends on the extraction aperture
- Caveat (inferred, ours): Sub-component decomposition is based on a few channels at low S/N
- Caveat (inferred, ours): Cycle 0 and 1 data reduced with different CASA versions

## Reproducibility

- Data public (paper): Data retrievable from the ALMA archive  
  > "which can be retrieved from the ALMA data archive" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Clean masks and parameters
- Missing: Aperture definition for total flux
- Missing: Fit details
- Data volume (inferred): ~50-100 GB raw for two Band 6 programs
- Score (inferred): 3/5, Public data and a simple recipe, but many imaging and extraction details are missing.
- Rediscovery candidate: yes, Public data, a simple recipe and numeric results (flux, L[CII], offset).

## Links

- Companion: Carniani et al. in prep. (Multi-component [CII] in z>5 galaxies)
- Companion: Ouchi:2013 (Original Cycle 0 analysis)

## Checks

```json
{
 "quotes": 58,
 "quotes_ok": 58,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 41,
  "rate": 0.577
 },
 "evidence_ok": true
}
```
