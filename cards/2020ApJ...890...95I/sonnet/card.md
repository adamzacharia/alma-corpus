# <SUP>14</SUP>N/<SUP>15</SUP>N Isotopic Ratio in CH<SUB>3</SUB>CN of Titan's Atmosphere Measured with ALMA

`2020ApJ...890...95I` | The Astrophysical Journal 2020 | first author: Iino, Takahiro | arXiv: 2001.01484 | DOI: 10.3847/1538-4357/ab66b0

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: solar_system
- Question: What is the 14N/15N isotopic ratio in CH3CN in Titan's atmosphere, and does it differ from HCN/HC3N values as predicted by photochemical models?  
  > "By comparing those observations with the simultaneously observed lines at the GHz band, we then derived in as ." (abstract)
- Target **Titan**: coordinates _not stated_; z/distance apparent disk diameter 0.78 arcsec  
  > "The apparent disk diameter (2575 km) of Titan was 0.78$\ensuremath{''}$ at the observed time, and the sub-Earth latitude was 24.7$^{\circ}$N." (2.1 Extracting Titan data from the ALMA archive); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00033.S
- bands: _not stated_
- frequencies and spectral setup: CH3C15N J=19-18 at 338.88-338.92 GHz; CH3CN lines at 349.21-349.45 GHz; 1874.956 MHz bandwidth, 3840 channels, 488.270 kHz resolution  
  > "Since the total bandwidth and number of channels were 1874.956 MHz and 3840 channels, respectively, the spectral resolution was 488.270 kHz." (2.1 Extracting Titan data from the ALMA archive)
- continuum bandwidth: _not stated_
- arrays: 39 12-m antennas  
  > "The number of 12-m antennas used for the observation was 39." (2.1 Extracting Titan data from the ALMA archive)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.19" x 0.62" (PA -70.3 deg)  
  > "The synthesis beam size was 1.19$\ensuremath{''} \times$0.62$\ensuremath{''}$ (position angle = $-$70.3$^{\circ}$)." (2.1 Extracting Titan data from the ALMA archive)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 157 seconds, seven scans  
  > "The observation time was 157 seconds with seven observation scans taken at 6.05 second intervals." (2.1 Extracting Titan data from the ALMA archive)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CH3C15N J=19-18 (338.88-338.92 GHz)
- External data: Disk-averaged and hemispheric temperature profiles of Titan retrieved from ALMA data of June 27, 2015  
  > "a disk-averaged temperature profile was retrieved from ALMA archived data observed on June 27, 2015" (2.2 Radiative transfer analysis) [from Thelen et al. 2018 (cite: Thelen2018)]
- External data: A priori CH3CN vertical profile  
  > "An a priori profile for was taken from (cite: Marten2002)." (2.2 Radiative transfer analysis) [from (cite: Marten2002)]

## Processing

### Calibration

- pipeline or manual: QA-2 pipeline script used to reduce raw visibilities  
  > "The calibration was done using the QA-2 pipeline script ." (2.1 Extracting Titan data from the ALMA archive)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CLEAN with csclean mode  
  > "Imaging was performed with the CLEAN method with $csclean$ mode" (2.1 Extracting Titan data from the ALMA archive)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 0.025 arcsec  
  > "to produce a 320$\times$320 pixel image with a 0.025$\ensuremath{''}$ spacing" (2.1 Extracting Titan data from the ALMA archive)
- image size: 320x320 pixels  
  > "to produce a 320$\times$320 pixel image with a 0.025$\ensuremath{''}$ spacing" (2.1 Extracting Titan data from the ALMA archive)
- masking: 1.5 arcsec diameter circle at disk center  
  > "A CLEAN mask with 1.5$\ensuremath{''}$ diameter circle was placed at the Titan’s disk center." (2.1 Extracting Titan data from the ALMA archive)
- multiscale scales: _not stated_
- continuum subtraction: continuum and line separated in uv plane  
  > "The continuum and line emissions were separated in the $uv$ plane." (2.1 Extracting Titan data from the ALMA archive)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- CASA version
- weighting/robust and deconvolver settings
- line-free channels for continuum
- threshold/niter for CLEAN
- Titan ephemeris used for Doppler correction
- flux calibration scale and uncertainty
- radiative transfer code, line list and spectroscopic parameters
- numerical isotopic ratio and uncertainty (missing in the text)
- noise estimate used in chi-square

## Analysis recipe

1. **Reduce and image Titan data**: QA-2 calibration, split SPWs, Doppler correction, uv continuum/line separation, CLEAN imaging  
  > "Calibrated datasets for Titan were split into each spectral windows (SPW), and their line-of-sight Doppler-shift velocity values were corrected." (2.1 Extracting Titan data from the ALMA archive)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract disk-averaged spectra**: Average spectra within region up to 1200 km altitude (~1.15" diameter)  
  > "we averaged the spectra within a region that included the Titan atmosphere up to an altitude of 1200 km" (2.1 Extracting Titan data from the ALMA archive)
   - fitting: _not stated_
   - validation: _not stated_
3. **Retrieve CH3CN vertical profile**: Line-by-line radiative transfer with spherically uniform layers; pencil-beam spectra convolved with the beam; flux calibrated against forward-model continuum  
  > "Our radiative transfer model consists of a line-by-line calculation using spherically uniform atmospheric layers." (2.2 Radiative transfer analysis)
   - assumption: Temperature profile from Thelen et al. 2018  
  > "For the temperature profile, we referred to a recent work by (cite: Thelen2018)" (2.2 Radiative transfer analysis)
   - fitting: Retrieval from CH3CN lines at 349.21-349.45 GHz  
  > "A vertical profile of was retrieved from the transitions at 349.21–349.45 GHz." (2.2 Radiative transfer analysis)
   - validation: Compared with Thelen et al. 2019 profile  
  > "we briefly compared it with the work by (cite: Thelen2019)" (2.2 Radiative transfer analysis)
4. **Fit CH3C15N abundance scaling**: Chi-square vs scaling factor of the retrieved profile, vertically constant isotopic ratio; fit within ±16 MHz of the 338.882 GHz line; uncertainty from Δχ2≤1  
  > "The fitting uncertainty was estimated from the range of $\Delta \chi^{2} \leq 1.0$" (2.2 Radiative transfer analysis)
   - assumption: Vertically constant isotopic ratio  
  > "A vertically constant isotopic ratio is assumed in this study." (2.2 Radiative transfer analysis)
   - fitting: Reduced chi-square minimization  
  > "The reduced $\chi^{2}$ values were calculated as a function of the scaling factor of with respect to the volume mixing ratio." (2.2 Radiative transfer analysis)
   - validation: Best fit also reproduces the other two lines not used in fitting; tested northern-hemisphere temperature profile  
  > "this isotopic ratio also reproduces the other two lines that are not used in the fitting analysis" (2.2 Radiative transfer analysis)

## Software

- **CLEAN (csclean)** : Imaging Titan visibilities  
  > "Imaging was performed with the CLEAN method with $csclean$ mode" (2.1 Extracting Titan data from the ALMA archive)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Disk apparent diameter of Titan | 0.78 | not stated | arcsec | 0 | The apparent disk diameter (2575 km) of Titan was 0.78$\ensuremath{''}$ at the observed time |

## Qualitative findings

- CH3CN intensity peaks in the northern mid-latitudes, consistent with seasonal behavior  
  > "the intensity peak is located in the northern mid-latitude region, which is consistent with past observations of the seasonal behavior of this species" (2.1 Extracting Titan data from the ALMA archive)

## Claim tuples

- H: CH3CN has a higher 14N/15N than HCN and HC3N because of GCR-driven production | E: Fit CH3C15N J=19-18 against CH3CN in archival ALMA Titan data | R: Best-fit ratio (numbers not in text) lies within the model range of 70-170 at 200 km | F: Best fit is higher than HCN and HC3N, supporting different dissociation sources, but accuracy is insufficient | **partially**

## Reasoning

- Why this data: Simultaneous observation of both isotopologues avoids seasonal and spatial mismatch  
  > "researchers must always be careful when interpreting an isotopic ratio if the values were derived from the data of two isotopologues taken at different observation dates" (2.1 Extracting Titan data from the ALMA archive)
- Why this method: _not stated_
- Alternative: Northern-hemisphere temperature profile tested as alternative to the disk-averaged one  
  > "We tested different temperature profiles for the derivation." (3.2 Impact of the assumed temperature profile)
- How they decided it was enough: _not stated_
- Limitation (authors): Data quality limits accuracy; cannot distinguish UV vs GCR scenarios  
  > "due to the data quality limitation, the value derived in this study is not sufficiently accurate to clearly differentiate between these two possible scenarios" (3.3 Comparisons with the model and future perspectives)
- Caveat (inferred, ours): Short 157 s calibration data give low SNR
- Caveat (inferred, ours): Single dataset, vertically constant ratio assumed
- Caveat (inferred, ours): Temperature profile from a different date
- Caveat (inferred, ours): Flux calibration depends on model continuum

## Reproducibility

- Data public (paper): Public ALMA archive data  
  > "we searched the publicly released ALMA archive" (2.1 Extracting Titan data from the ALMA archive)
- Products in archive: _not stated_
- Missing: Radiative transfer code and spectroscopy
- Missing: CASA version and clean parameters
- Missing: Final ratio values (absent from the supplied text)
- Data volume (inferred): ~10-50 GB raw
- Score (inferred): 3/5, Public data, but radiative transfer code and key settings are not given and key numbers are missing from the text.
- Rediscovery candidate: no, The radiative transfer recipe is incomplete and the numeric results are missing from the text.

## Links

- Companion: Thelen et al. 2018 (cite: Thelen2018) (Temperature profile from ALMA Titan data)
- Companion: Thelen et al. 2019 (cite: Thelen2019) (CH3CN profile comparison)
- Companion: Dobrijevic & Loison 2018 (cite: Dobrijevic2018) (Photochemical model predictions)

## Checks

```json
{
 "quotes": 35,
 "quotes_ok": 35,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 1,
 "numeric_problems": 0,
 "fill": {
  "facts": 63,
  "stated": 30,
  "rate": 0.476
 },
 "evidence_ok": true
}
```
