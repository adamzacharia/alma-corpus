# Comprehensive Analysis of HD 105, A Young Solar System Analog

`2018ApJ...869...10M` | The Astrophysical Journal 2018 | first author: Marshall, J. P. | arXiv: 1811.06440 | DOI: 10.3847/1538-4357/aaec6a

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: debris_disks
- Question: What are the stellar parameters, disc architecture, scattered-light albedo and dust properties of the young Solar analogue HD 105 and its debris disc?  
  > "Simultaneous modelling of the available photometry, disc architecture, and detection in scattered light allow better determination of the disc’s architecture, and dust grain minimum size, composition, and albedo." (abstract)
- Target **HD 105**: coordinates RA 00 05 52.54, Dec -41 45 11.0  
  > "Distance (pc) | 38.85 $\pm$ 0.08  | 2" (Table 2); "Right Ascension (*hms*)   | 00 05 52.54       | 1" (Table 2); z/distance 38.85 ± 0.08 pc  
  > "Distance (pc) | 38.85 $\pm$ 0.08  | 2" (Table 2); "Right Ascension (*hms*)   | 00 05 52.54       | 1" (Table 2); distance from Gaia DR2 parallax  
  > "Distance (pc) | 38.85 $\pm$ 0.08  | 2" (Table 2); "Right Ascension (*hms*)   | 00 05 52.54       | 1" (Table 2)

## Data provenance

- ALMA projects: 2012.1.00437.S
- bands: Band 6 (1.3 mm)  
  > "An ALMA band 6 (1.3 mm) observation for HD 105 was downloaded from the ESO ALMA Science Archive" (3.2 ALMA millimetre imaging data)
- frequencies and spectral setup: Four windows: three continuum (128 channels, 2 GHz each), one covering 12CO(2-1) with 3840 channels; 6.9 GHz total continuum bandwidth  
  > "Three windows were set up to measure the continuum, each with 128 channels over 2 GHz bandwidth." (3.2 ALMA millimetre imaging data); "In combination, the four channels provide 6.9 GHz bandwidth to study the continuum emission." (3.2 ALMA millimetre imaging data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.95″ × 0.67″ at PA 88° (34 × 26 au)  
  > "The dirty beam has an ellipsoidal FWHM $0.95\ensuremath{''}~\times~0.67\ensuremath{''}$ at a position angle of 88$\ensuremath{^\circ}$" (3.2 ALMA millimetre imaging data)
- max recoverable scale: _not stated_
- sensitivity: 26.8 μJy/beam continuum rms (natural weighting)  
  > "With natural weighting the continuum image r.m.s. noise is 26.8 $\mu$Jy beam$^{-1}$." (3.2 ALMA millimetre imaging data)
- time on source: 2238 s  
  > "The on-source integration time for HD 105 was 2238 s." (3.2 ALMA millimetre imaging data)
- observing dates: _not stated_
- pi or archival as stated: Archival, PI D. Rodriguez, Cycle 1  
  > "The observation was originally carried out as part of project 2012.1.00437.S (PI: D. Rodriguez) during Cycle 1." (3.2 ALMA millimetre imaging data)
- Line: CO 2-1 (230.538 GHz)
- Other facility **HST/NICMOS**: Coronagraphic F110W and F160W images; scattered-light detection (ALICE reprocessing)  
  > "We reprocessed both datasets as part of the *Archival Legacy Investigations for Circumstellar Environments* (ALICE) program" (3.3.1 HST/NICMOS)
- Other facility **VLT/SPHERE**: H-band coronagraphic images (SHARDDS) for scattered light  
  > "in the broad-band H filter (centred at 1.625 $\mu$m, width 291 nm) with the apodized Lyot coronagraph of diameter 185mas." (3.3.2 VLT/SPHERE)
- Other facility **Herschel PACS/SPIRE**: Re-reduced far-IR/sub-mm photometry  
  > "Here we re-reduced these data to obtain revised values for the source fluxes" (2 Observations)
- Other facility **FEROS/HARPS**: High-resolution spectra for stellar parameters  
  > "high resolution FEROS and HARPS spectra were also used to obtain the stellar effective temperature" (3.1 Stellar parameters)
- External data: ATCA 9 mm flux  
  > "an ATCA measurement at 9 mm taken from (cite: 2017Marshall)" (2 Observations) [from (cite: 2017Marshall)]
- External data: APEX/LABOCA 880 μm flux  
  > "an APEX/LABOCA measurement at 880 $\mu$m (cite: 2010Nilsson)" (2 Observations) [from (cite: 2010Nilsson)]
- External data: Gaia DR2 position, parallax, proper motion, G mag  
  > "are taken from the Gaia DR 2 catalogue (cite: 2016Prusti; 2016Lindegren; 2018Brown)" (3.1 Stellar parameters) [from (cite: 2018Brown)]

## Processing

### Calibration

- pipeline or manual: Provided scripts used  
  > "Calibration and reduction of the ALMA observation were carried out in CASA 4.1 using the provided scripts." (3.2 ALMA millimetre imaging data)
- casa version: CASA 4.1  
  > "Calibration and reduction of the ALMA observation were carried out in CASA 4.1 using the provided scripts." (3.2 ALMA millimetre imaging data)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Neptune (bandpass J0006-0623, phase J0012-3954)  
  > "Neptune was used as the flux calibrator, J0006-0623 was the bandpass calibrator, and J0012-3954 was the phase calibrator." (3.2 ALMA millimetre imaging data)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: clean, all four spectral windows combined  
  > "Image reconstruction was carried out using the *clean* task combining all four spectral windows for the greatest signal-to-noise." (3.2 ALMA millimetre imaging data)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "We reconstruct the image using natural weighting." (3.2 ALMA millimetre imaging data)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub for the CO cube  
  > "To begin we produced a continuum subtracted measurement set from the HD 105 data using *uvcontsub*." (3.2.2 Non-detection of cold CO emission)
- line free channels: _not stated_
- primary beam correction: impbcor on CO cube  
  > "The cube is corrected for the effect of the primary beam using the *impbcor* task before further analysis." (3.2.2 Non-detection of cold CO emission)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- CO spectro-spatial filtering technique  
  > "We then proceed by implementing the spectro-spatial filtering technique presented in (cite: 2017Matra)." (3.2.2 Non-detection of cold CO emission) [from (cite: 2017Matra)]
- CO mass upper limit via non-LTE code  
  > "We use a non-Local Thermodynamic Equilibrium CO excitation code to calculate a CO mass upper limit, following (cite: 2018aMatra)." (3.2.2 Non-detection of cold CO emission) [from (cite: 2018aMatra)]
- Bayesian stellar parameter method  
  > "using the Bayesian approach applied in (cite: 2016delBurgo; 2018delBurgo)" (3.1 Stellar parameters) [from (cite: 2016delBurgo; 2018delBurgo)]
- Single-size single-composition grain assumption for albedo  
  > "Following (cite: 2018Choquet), we assume that the debris disc to be composed entirely of dust grains with a single size and of a single composition." (3.4 Constraints on the dust composition) [from (cite: 2018Choquet)]

### Not stated but needed to reproduce (our reading)

- Cell size and image size of the ALMA clean image
- clean threshold, mask and iterations
- Exact model-fit residual metric and error estimation for disc architecture
- Line-free channels for uvcontsub
- Dust temperature adopted for the mass calculation
- Details of the CO non-LTE excitation conditions
- SED fitting method, likelihood and how parameter errors were derived

## Analysis recipe

1. **Image ALMA continuum**: clean of all four spectral windows with natural weighting  
  > "We reconstruct the image using natural weighting." (3.2 ALMA millimetre imaging data)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit disc architecture**: Grid of single-annulus models convolved with dirty beam, subtracted from image, residuals minimised  
  > "we subtract each disc model, convolved with the dirty ALMA beam (FWHM $\sim~0.9\ensuremath{''}\times0.7\ensuremath{''}$), from the observed image and seek to minimise the residuals" (3.2.1 Disc architecture)
   - parameter: Grid over inclination, PA, semi-major axis, width, flux  
  > "Semi-major axis (au) | 50 – 150 | 41 | Linear | 85 $\pm$ 5 |" (Table 3)
   - assumption: Vertical opening angle 10°, constant surface brightness exponent alpha=0  
  > "a vertical opening angle of 10$\ensuremath{^\circ}$, similar to the Solar system, was assumed" (3.2.1 Disc architecture)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive dust mass**: Optically thin M = F d^2 / (kappa B)  
  > "assuming that the disc is fully optically thin at 1.3 mm" (3.2.1 Disc architecture)
   - assumption: kappa = 1.7 g cm^-2  
  > "Assuming the dust opacity $\kappa$ is 1.7 gcm$^{-2}$" (3.2.1 Disc architecture)
   - fitting: _not stated_
   - validation: _not stated_
4. **Search for CO(2-1) emission**: Continuum-subtracted cube, Keplerian spectro-spatial filtering over disc region, non-LTE mass limit  
  > "The spectro-spatial filtering yields a 3-$\sigma$ upper limit of 8.5 mJy kms$^{-1}$ to CO emission." (3.2.2 Non-detection of cold CO emission)
   - software: CASA
   - parameter: Cube -25 to 25 km/s, 0.5 km/s step; star 1.114 Msun  
  > "The cube spans barycentric velocities between -25 and 25 kms$^{-1}$, with a step size of 0.5 kms$^{-1}$." (3.2.2 Non-detection of cold CO emission)
   - assumption: CO co-located with dust, vertically flat, Keplerian  
  > "The CO is further assumed to be situated in a vertically flat disc, orbiting with Keplerian velocity around a star of 1.114 $M_{\odot}$." (3.2.2 Non-detection of cold CO emission)
   - fitting: _not stated_
   - validation: _not stated_
5. **Measure scattered-light radial profile and albedo**: PSF subtraction (KLIP/PCA-RDI), elliptical-aperture averaging using ALMA geometry, throughput correction, albedo from Weinberger approximation  
  > "we obtain an albedo of 0.15 based on the NICMOS surface brightness (15 $\mu$Jy/arcsec$^{2}$), or 0.06 based on the SPHERE measurement" (3.3.3 Combined modelling)
   - parameter: NICMOS F160W: 69 modes, 125 reference images; SPHERE: 100 PCA modes, 610 images from 22 stars  
  > "We then selected 610 images from 22 stars most correlated with the ones from HD 105" (3.3.2 VLT/SPHERE)
   - assumption: Optically thin dust  
  > "Assuming optically thin dust, and using the approximation from (cite: 1999Weinberger)" (3.3.3 Combined modelling)
   - fitting: _not stated_
   - validation: Algorithm throughput by analytical forward modelling (NICMOS)  
  > "We corrected our average profiles and uncertainties by estimating the algorithm throughput with analytical forward modeling." (3.3.1 HST/NICMOS)
6. **Constrain grain size and composition from albedo**: Hyperion radiative transfer for grain sizes 0.1-500 μm and silicate/ice mixtures  
  > "We test grain sizes from 0.1 to 500 $\mu$m, and dust compositions of pure astronomical silicate, and water ice:astronomical silicate mixtures" (3.4 Constraints on the dust composition)
   - software: Hyperion
   - assumption: Dust mass fixed from ALMA flux; Ldust/L* = 2.6e-4  
  > "For consistency, we keep the dust mass of the disc fixed to that calculated for HD 105 based on its ALMA mm flux." (3.4 Constraints on the dust composition)
   - fitting: _not stated_
   - validation: _not stated_
7. **Fit SED with disc model**: Grid of radiative transfer models with power-law size distribution, annulus 70-100 au  
  > "We model the disc as being an annulus lying 70 to 100 au from the star with uniform radial surface brightness, as per the ALMA image." (3.5 Revised SED model)
   - software: Hyperion
   - parameter: amin 0.5-20.5 μm (41 values), q 2.5-4.5 (11 values), amax fixed 10 mm  
  > "$q$                    | 2.50 – 4.50 |   11   | Linear  | 3.55$^{+0.30}_{-0.15}$ |" (Table 4)
   - assumption: Pure astronomical silicate  
  > "The dust composition is assumed to be pure astronomical silicate (cite: 2003Draine)." (3.5 Revised SED model)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.1: ALMA calibration, clean, uvcontsub, impbcor  
  > "Calibration and reduction of the ALMA observation were carried out in CASA 4.1 using the provided scripts." (3.2 ALMA millimetre imaging data)
- **Hyperion** : 3-D radiative transfer for scattered light and SED  
  > "The scattered light modelling is carried out using the 3-D radiative transfer code Hyperion (cite: 2011Robitaille)." (3.4 Constraints on the dust composition)
- **HIPE** 15: Herschel PACS and SPIRE reduction  
  > "using the standard pipeline processing scripts (hipe version 15, PACS calibration 78)" (2 Observations)
- **KLIP** : PCA PSF subtraction of NICMOS data  
  > "using the PCA-based KLIP algorithm for PSF subtraction (cite: 2012Soummer)" (3.3.1 HST/NICMOS)
- **SPHERE DRH pipeline** : Sky subtraction, flat-fielding, bad pixel correction of SPHERE data  
  > "using the official SPHERE Data Reduction and Handling pipeline (cite: 2008Pavlov)" (3.3.2 VLT/SPHERE)
- **PARSEC isochrones** : Stellar evolution grid for Bayesian parameters  
  > "we downloaded and arranged a grid of PARSEC isochrones" (3.1 Stellar parameters)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Disc semi-major axis | 85 | ± 5 | au | 2 | Semi-major axis (au) / 50 – 150 / 41 / Linear / 85 $\pm$ 5 / |
| Disc inclination | 50 | ± 5 | deg | 2 | with an inclination of 50 $\pm$ 5 $^\circ$ with respect to the line of sight at a position angle of 15 $\pm$ 5$^\circ$ |
| Disc position angle | 15 | ± 5 | deg | 2 | with an inclination of 50 $\pm$ 5 $^\circ$ with respect to the line of sight at a position angle of 15 $\pm$ 5$^\circ$ |
| Belt width | 30 | ± 10 | au | 2 | Belt width (au) / 10 – 50 / 21 / Linear / 30 $\pm$ 10 / |
| Total disc flux at 1.3 mm | 1.45 | ± 0.28 | mJy | 2 | The total flux of the disc in the sub-millimetre, 1.45 $\pm$ 0.28 mJy |
| Dust mass | 0.035 | +0.013/-0.009 | Earth masses | 3 | we calculate a mass of $0.035^{+0.013}_{-0.009}~$M$_{\oplus}$ for the dust |
| CO(2-1) 3-sigma upper limit | 8.5 | not stated | mJy km/s | 4 | The spectro-spatial filtering yields a 3-$\sigma$ upper limit of 8.5 mJy kms$^{-1}$ to CO emission. |
| CO mass upper limit | 2.5e-7 to 2.5e-6 | not stated | Earth masses | 4 | we determine a CO mass upper limit ranging from 2.5$\times10^{-7}$ to 2.5$\times10^{-6}$ $M_{\oplus}$ |
| Stellar age | 50 | ± 16 | Myr | 0 | We derived an age of 50 $\pm$ 16 Myr |
| Dust albedo (NICMOS) | 0.15 | not stated | dimensionless | 5 | we obtain an albedo of 0.15 based on the NICMOS surface brightness (15 $\mu$Jy/arcsec$^{2}$) |
| Dust albedo (SPHERE) | 0.06 | not stated | dimensionless | 5 | or 0.06 based on the SPHERE measurement (5.9 $\mu$Jy/arcsec$^{2}$) |
| Minimum grain size | 3.25 | +3.00/-1.00 | μm | 7 | $a_{\rm min}$ ($\mu$m) / 0.5 – 20.5  /   41   / Linear  / 3.25$^{+3.00}_{-1.00}$ / |
| Size distribution exponent q | 3.55 | +0.30/-0.15 | dimensionless | 7 | $q$                    / 2.50 – 4.50 /   11   / Linear  / 3.55$^{+0.30}_{-0.15}$ / |
| Gamma = Rdisc/Rbb | 2.43 | ± 0.42 | dimensionless | 0 | We find $\Gamma = 2.43~\pm~0.42$ |

## Qualitative findings

- No evidence of gas lines in stellar spectra and no CO emission detected in ALMA  
  > "No evidence of significant CO 2-1 line emission was found from the area of the disc" (5 Conclusions)
- Disc detected in scattered light for the first time via annular averaging, but NICMOS and SPHERE brightness differ by ~4x  
  > "This is a factor of $\sim$4 fainter than the disc detected by *HST*/NICMOS" (3.3.2 VLT/SPHERE)

## Claim tuples

- H: The disc geometry can be constrained from the archival ALMA 1.3 mm image | E: Annulus model grid fit to image | R: a=85±5 au, i=50±5°, PA=15±5°, width 30±10 au | F: The disc is a single annulus, marginally resolved, with no detected offset or asymmetry | **supported**
- H: Scattered light from the disc can be recovered using the ALMA geometry as a prior | E: Elliptical annular averaging of NICMOS and SPHERE PSF-subtracted images | R: Peaks of 15 μJy/arcsec² (NICMOS) and 5.9 μJy/arcsec² (SPHERE) | F: Disc detected in scattered light, albedo 0.06-0.15 | **supported**
- H: The disc hosts detectable CO gas | E: Spectro-spatial filtering of the CO(2-1) cube | R: 3σ limit 8.5 mJy km/s; CO mass < 2.5e-7 to 2.5e-6 Mearth | F: No CO detected | **supported**
- H: Dust grain composition and size can be constrained | E: Radiative transfer models compared with albedo and SED | R: amin=3.25 μm, q=3.55; grains of few microns, silicate or moderately icy | F: Consistent with pure silicate or moderately icy dust | **partially**

## Reasoning

- Why this data: Archival ALMA image gives resolved disc geometry as a prior for scattered light and SED modelling  
  > "a spatially resolved archival image of the disc at millimetre wavelengths from ALMA" (1 Introduction)
- Why this method: _not stated_
- Alternative: Classical ADI for SPHERE rejected as insensitive due to self-subtraction; RDI used instead  
  > "we are therefore unable to confirm the *HST*/NICMOS detection with this data reduction technique." (3.3.2 VLT/SPHERE)
- How they decided it was enough: _not stated_
- Limitation (authors): Low S/N ALMA data; belt width not conclusively resolved  
  > "The belt is perhaps marginally resolved in the ALMA image, but the quality of the data does not allow us to conclude that" (3.2.1 Disc architecture)
- Limitation (authors): Dust opacity uncertainty gives factor 3-5 in mass  
  > "which leads to an uncertainty in $M_{\rm dust}$ of a factor 3 to 5." (3.2.1 Disc architecture)
- Limitation (authors): NICMOS/SPHERE discrepancy possibly from non-Gaussian noise  
  > "it can be seen in the reduced image that the noise is non-Gaussian." (3.3.2 VLT/SPHERE)
- Caveat (inferred, ours): Disc fit has no formal uncertainty method; errors look like grid spacing
- Caveat (inferred, ours): Scattered-light detection is low S/N and NICMOS/SPHERE disagree by 4x
- Caveat (inferred, ours): Albedo analysis uses a crude optically thin approximation
- Caveat (inferred, ours): SED fit gives poor match at mm wavelengths

## Reproducibility

- Data public (paper): ALMA data downloaded from ESO ALMA Science Archive; ALICE database public  
  > "An ALMA band 6 (1.3 mm) observation for HD 105 was downloaded from the ESO ALMA Science Archive" (3.2 ALMA millimetre imaging data)
- Products in archive: _not stated_
- Missing: Imaging parameters (cell, size, masks)
- Missing: Unpublished ALICE F160W reduction
- Missing: SPHERE custom PCA code
- Missing: SED fitting details
- Data volume (inferred): ~5-20 GB for the ALMA MS; HST/SPHERE data additional
- Score (inferred): 3/5, ALMA data public and the main numeric results are specified, but imaging and fitting details are sparse and several datasets are unpublished or custom.
- Rediscovery candidate: yes, Public ALMA data; disc geometry, dust mass and CO limit are numeric and the recipe is fairly simple, though imaging details are missing.

## Links

- Method: (cite: 2017Matra) (CO spectro-spatial filtering method)
- Method: (cite: 2018aMatra) (non-LTE CO mass limit code)
- Method: (cite: 2018Choquet) (grain size and composition albedo approach)
- Companion: (cite: 2012Donaldson) (Original Herschel observations and disc discovery)
- Companion: (cite: 2018Milli) (SHARDDS survey)
- Related: SHARDDS
- Related: ALICE
- Related: Tucana-Horologium association

## Checks

```json
{
 "quotes": 85,
 "quotes_ok": 85,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 14,
 "numeric_problems": 0,
 "fill": {
  "facts": 97,
  "stated": 60,
  "rate": 0.619
 },
 "evidence_ok": true
}
```
