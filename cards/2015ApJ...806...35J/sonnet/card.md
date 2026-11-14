# The Physical Conditions in a Pre-super Star Cluster Molecular Cloud in the Antennae Galaxies

`2015ApJ...806...35J` | The Astrophysical Journal 2015 | first author: Johnson, K. E. | arXiv: 1503.06477 | DOI: 10.1088/0004-637X/806/1/35

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, nearby_galaxies
- Question: What are the physical conditions (size, mass, temperature, pressure) of a compact massive molecular cloud in the Antennae, and can it form a globular cluster / super star cluster?  
  > "The present paper characterizes this source, which we consider among the best candidates for a proto-SSC, and lays out the evidence for and against the source’s eventual evolution into a SSC or GC." (Introduction)
- Target **Compact cloud in SGMC2, Antennae overlap region**: coordinates RA 12:01:54.73, Dec -18:52:53.2 (J2000)  
  > "12:01:54.73 | -18:52:53.2 | 1524$\pm 3$" (Table 2); "adopting a distance of 21.5 Mpc" (Table 3 notes); z/distance 21.5 Mpc  
  > "12:01:54.73 | -18:52:53.2 | 1524$\pm 3$" (Table 2); "adopting a distance of 21.5 Mpc" (Table 3 notes); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00876.S
- bands: CO(3-2) and 870 um continuum (Cycle 0); SV CO(2-1)  
  > "We obtained ALMA observations of the Antennae system in CO(3-2) and 870$\;\mu$m continuum" (2 ALMA Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: 13-point mosaic, extended configuration  
  > "the observations consisted of a 13-point mosaic, and were carried out in the “extended” configuration" (2 ALMA Observations)
- baselines: max baseline ~400 m  
  > "with a maximum baseline of $\sim
400$ m and 5 km s$^{-1}$ spectral channels" (2 ALMA Observations)
- angular resolution: 0.56'' x 0.43'' (59 x 45 pc)  
  > "With an angular resolution FWHM of $0.''56 \times 0.''43$ ($59 \times
45$ pc)" (2 ALMA Observations)
- max recoverable scale: ~6''  
  > "The largest angular scale to which the CO(3-2) observations are sensitive is $\sim 6''$" (3.1 Cloud Temperature and Optical Depth)
- sensitivity: rms 3.3 mJy/beam (CO 3-2, 5 km/s channels); SV CO(2-1) 6.5 mJy/beam  
  > "The resulting rms was determined using line-free channels and found to be 3.3 mJy/beam." (2 ALMA Observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO 3-2 (not stated)
- Line: 12CO 2-1 (SV) (not stated)
- Other facility **VLA 3.6 cm archival**: Radio maps constraining free-free emission / ionizing flux  
  > "We created two radio maps from archival 3.6 cm VLA observations (proposal codes AN079, AP478, AS796, AA301)" (3.3)
- Other facility **HST Paα**: Paα emission to search for ionizing sources  
  > "We also register the astrometry of archival Hubble Space Telescope observations" (2.2)
- External data: Dust emissivity kappa=0.9 cm2/g and dust temperature 20 K  
  > "Assuming a dust emissivity of $\kappa = 0.9
\pm 0.13$ cm$^{2}$ g$^{-1}$ (cite: wilson08)" (3.2 Cloud Mass) [from (cite: wilson08)]
- External data: Starburst XCO = 0.5e20  
  > "Here we adopt a “starburst” CO-to-H$_2$ conversion factor X$_{CO}
  = 0.5\times 10^{20}$ cm$^{-2}$(K km s$^{-1}$)$^{-1}$ (cite: bolatto13)." (3.2 Cloud Mass) [from (cite: bolatto13)]
- External data: SGMC2 mass ~4e8 Msun  
  > "The SGMC2 region has an estimated total mass of $\sim 4\times 10^8$ M$_{\odot}$ (cite: wilson00)" (5.1) [from (cite: wilson00)]

## Processing

### Calibration

- pipeline or manual: Calibration described in overview paper; SV data recalibrated and reimaged  
  > "data calibration is discussed in detail in the overview paper (cite: whitmore14)" (2 ALMA Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
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
- smoothing: CO(3-2) convolved to CO(2-1) beam  
  > "The CO(3-2) observations were convolved to the synthesized beam of the CO(2-1) observations" (3.1)
- final beam: 0.56'' x 0.43''  
  > "With an angular resolution FWHM of $0.''56 \times 0.''43$" (2 ALMA Observations)
- final rms: 3.3 mJy/beam  
  > "found to be 3.3 mJy/beam" (2 ALMA Observations)

### Inherited from earlier work

- Data calibration  
  > "data calibration is discussed in detail in the overview paper (cite: whitmore14)" (2 ALMA Observations) [from (cite: whitmore14)]

### Not stated but needed to reproduce (our reading)

- CASA version and imaging parameters (weighting, robust, cleaning, masks)
- Continuum spectral windows and line-free channels
- Flux calibrator and flux uncertainty
- Exact sub-cube extraction and moment procedures
- RADEX grid ranges and priors
- How the SV data were recalibrated
- Spectral setup frequencies

## Analysis recipe

1. **Extract cloud and measure size/line width**: Sub-cube ~1''x1''x300 km/s, Gaussian fits and deconvolution of beam; cross-checked with CPROPS  
  > "We extract the primary cloud from the velocity cube for further analysis by creating a sub-cube around the cloud with dimensions of $\sim 1''\times 1'' \times 300$ km s$^{-1}$." (2.1 Cloud Analysis)
   - software: CPROPS
   - fitting: _not stated_
   - validation: CPROPS on whole cube agrees within uncertainties  
  > "the resulting parameters agree to within the uncertainties" (2.1 Cloud Analysis)
2. **Temperature and optical depth**: RADEX grid of CO(3-2) and CO(2-1) intensities, chi-squared minimization  
  > "The best-fit values result from a chi-squared minimization." (3.1)
   - software: RADEX
   - parameter: CO(3-2) filling fraction 1; CO(2-1) set to dilution factor  
  > "for CO(3-2) we set the beam filling fraction to 1, and for CO(2-1) we set it to the dilution factor" (3.1)
   - fitting: chi-squared grid  
  > "The line intensities and their ratio were compared to a grid of RADEX models covering a range of values for kinetic temperature, CO column density, and H$_2$ volume density." (Results, Cloud Temperature and Optical Depth)
   - validation: _not stated_
3. **Cloud mass from four methods**: Virial (isothermal sphere), RADEX column density, XCO, 870um dust continuum  
  > "The mass of the cloud is estimated using four different methods, each subject to different caveats." (3.2)
   - assumption: n_H2/n_CO = 2e4; XCO = 0.5e20; kappa 0.9 cm2/g; gas-to-dust 120; Td 20 K; distance 21.5 Mpc  
  > "gas-to-dust ratio of 120$\pm 28$, and dust temperature of 20 K" (3.2)
   - fitting: _not stated_
   - validation: Compared methods; virial treated as upper limit, RADEX as lower limit  
  > "we treat the estimated virial mass as an *upper* limit." (3.2)
4. **Ionizing flux limits**: VLA 3.6 cm maps at two resolutions; 5 sigma limit converted to N_Lyc  
  > "the 5$\sigma$ detection threshold of the radio emission corresponds to an ionizing flux of N$_{Lyc} \approx 6\times
10^{50}$ s$^{-1}$" (3.3)
   - fitting: Gaussian fit and subtraction of nearby sources in low-res map  
  > "we first fit and subtract Gaussian profiles to the other dominate sources in SGMC2." (Constraining the Ionizing Flux Associated with the Cloud)
   - validation: _not stated_
5. **Pressure and timescales**: Virial pressure relation with Pi=0.5; crossing and free-fall times  
  > "where $\Pi$ is defined by $n_e = \Pi \langle n_e \rangle$, and here we adopt $\Pi = 0.5$." (3.5)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CPROPS** : Cloud property measurement on cube  
  > "Properties of the clouds were measured both with the CPROPS program (cite: rosolowsky06)" (Table 2 notes)
- **RADEX** : Non-LTE modeling of CO lines  
  > "RADEX non-LTE modeling (cite: vandertak07) was used to analyze the CO(3-2) and CO(2-1) emission." (3.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Half-light radius | <=24 | ±3 | pc | 1 | half-light radius for the cloud of $\lesssim 24\pm 3$ pc |
| Velocity dispersion | 49 | ±3 (Table 2); ±6 (text) | km/s | 1 | 49$\pm 3$ |
| CO(3-2) flux | 52 | ±5 | Jy km/s | 1 | 52$\pm 5$ |
| Kinetic temperature | 25 | +10/-2 | K | 2 | kinetic temperature of 25$^{+10}_{-2}$ K |
| Optical depth | 3.5 | ±0.5 | dimensionless | 2 | the best fitting depth is $\tau\sim 3.5 \pm 0.5$ |
| Continuum peak | 9.8e-4 | ±3.4e-4 | Jy/beam | 3 | with a peak brightness of $9.8\pm3.4 \times
10^{-4}$ Jy beam$^{-1}$ |
| Adopted cloud mass | 0.3-1.5e7 | not stated | Msun | 3 | we adopt a cloud mass of M$= 0.3 - 1.5
\times 10^7$ M$_{\odot}$ |
| XCO mass | 3.3-15e6 | not stated | Msun | 3 | M$_{X_{CO}} =
3.3-15\times 10^6$ M$_{\odot}$ |
| Ionizing flux limit (high-res) | 6e50 | not stated | s^-1 | 4 | N$_{Lyc} \approx 6\times
10^{50}$ s$^{-1}$ |
| Free-fall time | 8e5 | not stated | yr | 5 | $t_{ff}=(3\pi/32~G~\rho)^{1/2} \approx 8 \times 10^5$ years |

## Qualitative findings

- No thermal radio or Paα source is associated with the cloud, so star formation has not yet altered it.  
  > "the lack of associated thermal radio emission indicates that star formation has not yet altered the environment" (abstract)

## Claim tuples

- H: Is the cloud a pre-SSC capable of forming a globular cluster? | E: CO(3-2) size/mass, continuum mass, radio/Paα limits | R: Radius <=24 pc, mass ~0.3-1.5e7 Msun, no ionizing source | F: Cloud is a proto-SSC candidate | **supported**
- H: Does confinement require high external pressure? | E: Size-linewidth and pressure analysis | R: P/kB >~1e8 K cm^-3 | F: Supports high-pressure SSC formation theories | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Cloud only marginally resolved; temperature-density degeneracy; mass methods have different caveats.  
  > "there is a degeneracy between the inferred temperature and density of the cloud" (3.1)
- Caveat (inferred, ours): Single marginally resolved cloud; size is an upper limit
- Caveat (inferred, ours): Large mass spread between methods; virial mass 5-10x too high
- Caveat (inferred, ours): Pressure inferred assuming confinement

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters and CASA version
- Missing: Details in Whitmore et al. 2014 calibration
- Missing: RADEX grid details
- Data volume (inferred): ~50-100 GB raw for Cycle 0 plus SV
- Score (inferred): 3/5, Public ALMA data and clear derived numbers, but calibration/imaging inherited and unspecified.
- Rediscovery candidate: no, Processing details are deferred to another paper and the measurement is a single marginal source.

## Links

- Method: (cite: whitmore14) (Calibration and overview of the ALMA Antennae data)
- Method: (cite: rosolowsky06) (CPROPS)
- Companion: (cite: herrera12) (Earlier SV analysis of the same source)
- Related: ALMA Science Verification Antennae (2011.0.00003.SV)

## Checks

```json
{
 "quotes": 52,
 "quotes_ok": 52,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00003.SV"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 34,
  "rate": 0.486
 },
 "evidence_ok": true
}
```
