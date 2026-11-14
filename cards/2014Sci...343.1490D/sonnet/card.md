# Molecular Gas Clumps from the Destruction of Icy Bodies in the β Pictoris Debris Disk

`2014Sci...343.1490D` | Science 2014 | first author: Dent, W. R. F. | arXiv: 1404.1380 | DOI: 10.1126/science.1248726

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: debris_disks
- Question: Is gas also released in collisions of icy bodies in the beta Pic debris disk, and how is it distributed?  
  > "But is gas also released in such events?" (abstract)
- Target **beta Pictoris**: coordinates _not stated_; z/distance 19.44 pc  
  > "At a distance of 19.44 parsec" (Main Text); distance from van Leeuwen 2007 (ref 1)  
  > "At a distance of 19.44 parsec" (Main Text)

## Data provenance

- ALMA projects: 2011.0.00087.S
- bands: _not stated_
- frequencies and spectral setup: four 2 GHz-wide spectral windows; CO J=3-2 in one window, 0.488 MHz channels, 0.85 km/s resolution after Hanning smoothing  
  > "with a channel spacing of 0.488MHz, and a spectral resolution of 0.85km/s (after Hanning smoothing)" (Supplementary Materials, Methods)
- continuum bandwidth: 7.4 GHz total, centred at 340 GHz  
  > "with a total bandwidth of 7.4GHz centred at 340GHz" (Supplementary Materials, Methods)
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15 to 380 m, 27 antennas  
  > "using ALMA with 27 antennas with projected baseline lengths from 15 to 380m" (Supplementary Materials, Methods)
- angular resolution: 0.56x0.71 arcsec at PA=62 deg  
  > "This resulted in a synthesized beam of 0.56x0.71arcsec (FWHM) at PA=62deg." (Supplementary Materials, Methods)
- max recoverable scale: sensitive to scales 10 to 240 AU  
  > "were sensitive to emission on scales from 10 to 240AU" (Supplementary Materials, Methods)
- sensitivity: continuum rms 61 µJy/beam; cube rms 0.004 Jy/channel/beam  
  > "The resultant datacube had an rms of 0.004Jy/channel/beam" (Supplementary Materials, Methods)
- time on source: 2.7 hr total, 1 hr on source  
  > "the total observing time was 2.7hrs, with 1hr integration on the source" (Supplementary Materials, Methods)
- observing dates: Nov 16, 2012  
  > "were performed on Nov 16, 2012" (Supplementary Materials, Methods)
- pi or archival as stated: _not stated_
- Line: 12CO J=3-2 (345.796 GHz)
- External data: CO column from UV absorption lines, 0.6-2.1x10^15 cm^-2, and 20 K excitation temperature  
  > "results from UV absorption line measurements range between 0.6-­‐2.1x10 [15 ] cm [-­‐2] ( _13_ )" (Main Text) [from Roberge et al. 2000 (ref 13)]
- External data: Projected separation of beta Pic b, 8.7 AU  
  > "with a projected separation of 8.7AU ( _11_ )" (Main Text) [from Chauvin et al. 2012 (ref 11)]

## Processing

### Calibration

- pipeline or manual: reduced using CASA (details not given)  
  > "The data were reduced using CASA" (Supplementary Materials, Methods)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Callisto amplitude; J0522-364 bandpass; J0519-4546 phase  
  > "Callisto was used as an amplitude calibrator, with J0522-­‐364 to calibrate the bandpass" (Supplementary Materials, Methods)
- flux scale uncertainty: 10%  
  > "is estimated to be 10%" (Supplementary Materials, Methods)
- self calibration: _not stated_

### Imaging

- task: clean algorithm in CASA  
  > "imaged using the clean algorithm" (Supplementary Materials, Methods)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "with natural weighting of the antenna uv response" (Supplementary Materials, Methods)
- uv taper: _not stated_
- cell size: 0.1 arcsec  
  > "produced with a 0.1 arcsec pixel spacing" (Supplementary Materials, Methods)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied to Fig. 1 images  
  > "The images in Fig.1 have been corrected for the response of the primary beam." (Supplementary Materials, Methods)
- array combination: _not stated_
- smoothing: Hanning smoothing  
  > "0.85km/s (after Hanning smoothing)" (Supplementary Materials, Methods)
- final beam: _not stated_
- final rms: 61 µJy/beam continuum  
  > "The rms sensitivity of the continuum map was 61µJy/beam" (Supplementary Materials, Methods)

### Inherited from earlier work

- Dust radial distribution annulus method  
  > "for stellar luminosity 8.7L sun ( _12_ )" (Supplementary Materials, Methods) [from Telesco et al. 2005 (ref 12)]
- Dust mass opacity and 85 K temperature  
  > "(0.15m [2] kg [-­‐1] at 850µm) and temperature of 85K ( _10_ )" (Main Text) [from Dent et al. 2000 (ref 10)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration details
- clean threshold, masks, iterations
- line-free channels used for continuum
- CO line flux integration method and aperture
- CO mass calculation details and excitation assumptions
- deprojection implementation details

## Analysis recipe

1. **image continuum and CO cube**: CASA reduction, clean with natural weighting, 0.1 arcsec pixels  
  > "imaged using the clean algorithm, with natural weighting of the antenna uv response" (Supplementary Materials, Methods)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **derive dust mass**: flux to mass with standard opacity and temperature  
  > "if we assume a standard dust mass opacity (0.15m [2] kg [-­‐1] at 850µm) and temperature of 85K" (Main Text)
   - assumption: opacity 0.15 m2/kg at 850 µm; T=85 K  
  > "temperature of 85K ( _10_ )" (Main Text)
   - fitting: _not stated_
   - validation: _not stated_
3. **derive CO mass**: CO J=3-2 flux with excitation temperature 20-85 K  
  > "Assuming a range of possible excitation temperatures from 20K" (Main Text)
   - assumption: Tex 20-85 K  
  > "to 85K (the dust equilibrium temperature ( _10_ ))" (Main Text)
   - fitting: _not stated_
   - validation: _not stated_
4. **PV diagram and deprojection**: PV cut along major axis integrated ±1 arcsec; deprojected assuming circular Keplerian orbits  
  > "a cut was taken along the disk major axis and the emission was integrated over ±1 arcsec orthogonal to the disk plane" (Supplementary Materials)
   - assumption: stellar mass 1.75 Msun, circular orbits  
  > "Keplerian velocity of a 1.75M sun star" (Supplementary Materials)
   - fitting: _not stated_
   - validation: emission in empty quadrants indicates noise level  
  > "the emission in the mostly empty quadrants in Fig. 3 indicate the level of noise in the deprojected images" (Supplementary Materials)
5. **dust radial distribution**: 11 annuli fitted iteratively from outermost inward, separately for SW and NE  
  > "modelled with 11 consecutive annuli, each of which characterized by its surface density" (Supplementary Materials)
   - assumption: black-body emissivities, L*=8.7 Lsun  
  > "assuming black-­‐body emissivities and temperatures for stellar luminosity 8.7L sun" (Supplementary Materials)
   - fitting: iterative annulus-by-annulus brightness matching until convergence  
  > "the process is repeated a few times until the distribution converges" (Supplementary Materials)
   - validation: _not stated_

## Software

- **CASA** : data reduction and clean imaging  
  > "The data were reduced using CASA" (Supplementary Materials, Methods)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| continuum total flux | 60 | 6 | mJy | 1 | The total flux of 60±6mJy |
| dust mass | 4.7e23 kg (6.4 M_Moon) | 0.5e23 kg | kg | 2 | dust mass of 4.7±0.5x10 [23] kg |
| CO J=3-2 total flux | 7.6e-20 | 0.8e-20 | W/m^2 | 1 | The CO J=3-­‐2 emission totals 7.6±0.8x10 [-­‐20] W/m [2] |
| CO mass | 1.7e20 kg (0.0023 M_Moon) | factor of 2 | kg | 3 | CO mass of 1.7x10 [20] kg (0.0023M Moon ) within a factor of 2 |
| clump CO flux fraction at 85 AU | ~30 | not stated | percent | 4 | which contains ~30% of the flux |
| CO production rate | ~1.4e18 | not stated | kg/yr | 3 | production rate of ~1.4x10 [18] kg/yr |

## Qualitative findings

- CO gas belt spans 50-160 AU, is brighter to the SW and offset ~5 AU above the main plane  
  > "the CO clump is offset by ~5AU above the main disk plane" (Main Text)

## Claim tuples

- H: CO is continuously replenished from icy bodies | E: Compare CO photodissociation timescale with orbital period | R: ~120 yr lifetime vs 600 yr orbit | F: CO must be replenished at ~1.4e18 kg/yr | **supported**
- H: The CO clump marks enhanced collisions | E: Deprojected PV diagram under circular Keplerian orbits | R: compact clump at 85 AU with ~30% of the flux | F: Resonance with a giant planet or a Mars-mass collision | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Photodesorption of mm-sized ice grains gives CO ~10 times lower than observed  
  > "would produce CO at a rate that is ~10 times lower than our observations show" (Main Text)
- How they decided it was enough: _not stated_
- Limitation (authors): Deprojection has near/far ambiguity; clump motion not confirmed  
  > "there are two solutions for the gas location, on the near and far side of the disk" (Supplementary Materials)
- Caveat (inferred, ours): Few methods details and no uncertainties for the deprojection
- Caveat (inferred, ours): Two interpretations are not discriminated
- Caveat (inferred, ours): Mass depends on assumed temperature and opacity

## Reproducibility

- Data public (paper): ALMA project data cited in acknowledgements  
  > "ADS/JAO.ALMA#2011.0.00087.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: CASA version and cleaning parameters
- Missing: Deprojection code
- Missing: Flux integration regions
- Data volume (inferred): ~5-20 GB
- Score (inferred): 3/5, Short report with sparse processing details but public data and simple numeric results.
- Rediscovery candidate: yes, Public single-execution data; numeric flux, dust and CO masses are checkable.

## Links

- Companion: Telesco et al. 2005 (ref 12) (Mid-IR asymmetry and dust annulus method)

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
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 40,
  "rate": 0.571
 },
 "evidence_ok": true
}
```
