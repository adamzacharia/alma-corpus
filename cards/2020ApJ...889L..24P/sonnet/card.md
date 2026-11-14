# Long Baseline Observations of the HD 100546 Protoplanetary Disk with ALMA

`2020ApJ...889L..24P` | The Astrophysical Journal Letters 2020 | first author: Pérez, Sebastián | arXiv: 1906.06305 | DOI: 10.3847/2041-8213/ab6b2b

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: What fine substructure and gas kinematics (wiggles, Doppler flip) does the HD 100546 disk show at high resolution, and could a planet or stellar companion open its gap?  
  > "The high-resolution 1.3 mm continuum observation reveals fine radial and azimuthal substructures in the form of a complex maze of ridges and trenches sculpting a dust ring." (abstract)
- Target **HD 100546**: coordinates _not stated_; z/distance 110.0±0.6 pc  
  > "Throughout this Letter, we assume a distance of 110.0$\pm$0.6 pc to HD 100546 (cite: Gaia2018)." (Introduction); distance from Gaia (Gaia2018)  
  > "Throughout this Letter, we assume a distance of 110.0$\pm$0.6 pc to HD 100546 (cite: Gaia2018)." (Introduction)

## Data provenance

- ALMA projects: 2016.1.00344.S
- bands: 1.3 mm  
  > "We obtained 1.3 millimeter observations of HD 100546 with the Atacama Large Millimeter/submillimeter Array (ALMA)" (2.1 ALMA continuum and molecular line observations)
- frequencies and spectral setup: Continuum SPWs 1.875 GHz wide at 232.005 and 218.505 GHz; lines at 230.538, 220.399, 219.560 GHz; 122.070 kHz (0.2 km/s) resolution  
  > "Two spectral windows with 1.875 GHz bandwidth were set up for detecting the dust continuum, centered at 232.005 GHz and 218.505 GHz, respectively." (2.1 ALMA continuum and molecular line observations); "The spectral resolution for the line observations was 122.070 kHz (equivalent to 0.2 km s$^{-1}$ channels)." (2.1 ALMA continuum and molecular line observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: 12-m array extended (C40-9) and compact (C40-6)  
  > "by combining the 12-m array in extended (C40-9) and compact (C40-6) configurations" (2.1 ALMA continuum and molecular line observations)
- baselines: 19 m to 12.2 km, 39-42 antennas  
  > "The resulting baselines ranged from 19 meters to up to 12.2 kilometers with a total of 39-42 antennas." (2.1 ALMA continuum and molecular line observations)
- angular resolution: Natural beam 64x45 mas; uvmem beam 19.7x12.9 mas  
  > "The final $I_{1.3\mathrm{mm}}$ image has an angular resolution of $\Omega_b =
19.7\times12.9$ mas, or 2.1$\times$1.4 au." (2.1 ALMA continuum and molecular line observations)
- max recoverable scale: 1.5 arcsec  
  > "The combined observations are sensitive to spatial scales of up to 1.5$''$." (2.1 ALMA continuum and molecular line observations)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: September 19, 22, 23 (long baseline)  
  > "The long baseline observations were acquired on September 19, 22, and 23, in three different blocks of $\sim$90 min each (40 min on source)." (2.1 ALMA continuum and molecular line observations)
- pi or archival as stated: _not stated_
- Line: 12CO 2-1 (230.538 GHz)
- Line: 13CO 2-1 (220.399 GHz)
- Line: C18O 2-1 (219.560 GHz)
- Other facility **VLT/SPHERE (IRDIS, IFS) SAM**: K1K2 band sparse aperture masking, 1h on target plus 1h on calibrators  
  > "The observations were acquired in May 15-16 2018, in the K1K2 band, with 1h integration on HD 100546 plus 1h on calibrators." (2.2 SPHERE sparse aperture masking)
- External data: Disk orientation used for polar deprojection  
  > "adopting the disk orientation derived in (cite: Casassus2019)" (3.1 A structured continuum ring) [from (cite: Casassus2019)]
- External data: BT-Settl models for converting contrast to companion mass limits  
  > "we used the BT-Settl models by (cite: 2012RSPTA.370.2765A), adapted for SPHERE filters" (3.3 Could the gap be opened by a stellar object?) [from (cite: 2012RSPTA.370.2765A)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline by ALMA staff; short and long baselines calibrated independently  
  > "All data were calibrated by the ALMA staff using the ALMA Pipeline version 40896 in the CASA package (cite: McMullin2007)" (2.1 ALMA continuum and molecular line observations)
- casa version: CASA 5.4 (imaging)  
  > "Synthesis imaging was initially carried out using the CLEAN algorithm (CASA version 5.4, task `tclean`)." (2.1 ALMA continuum and molecular line observations)
- pipeline version: ALMA Pipeline version 40896  
  > "All data were calibrated by the ALMA staff using the ALMA Pipeline version 40896 in the CASA package (cite: McMullin2007)" (2.1 ALMA continuum and molecular line observations)
- archive products used as is: _not stated_
- flux calibrator: J1107-4449 (flux); J0635-7516 bandpass; J1147-6753 phase  
  > "Observations of atmospheric (J1147-6753), bandpass (J0635-7516), and flux (J1107-4449) calibrators were performed." (2.1 ALMA continuum and molecular line observations)
- flux scale uncertainty: _not stated_
- self calibration: One round of phase self-cal, solint 54 s, SNR improved by factor 1.6 (SNR ~80 before)  
  > "One round of phase self-calibration using a solution interval of 54s was applied to the data, which was found to improve the resulting SNR by a factor of 1.6." (2.1 ALMA continuum and molecular line observations)

### Imaging

- task: tclean; uvmem (GPUVMEM) for super-resolved continuum  
  > "we super-resolved the self-calibrated continuum data using non-parametric image modeling with the `uvmem` package (cite: Carcamo2018)." (2.1 ALMA continuum and molecular line observations)
- deconvolver: _not stated_
- weighting robust: Continuum natural; 12CO robust 1.0; 13CO and C18O robust 2.0  
  > "We used a Briggs weighting scheme with a robust parameter of 1.0 for $^{12}$CO" (2.1 ALMA continuum and molecular line observations); "a Briggs robust parameter of 2.0 was used given the low signal in those lines" (2.1 ALMA continuum and molecular line observations)
- uv taper: _not stated_
- cell size: 2.5 mas pixels (uvmem image)  
  > "We oversampled $\Omega_b$ with 2.5 mas pixels." (2.1 ALMA continuum and molecular line observations)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: CASA uvcontsub; cubes with and without subtraction made  
  > "Line emission cubes were produced with and without prior continuum-subtraction (performed with CASA task `uvcontsub`)." (2.1 ALMA continuum and molecular line observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Short and long baseline datasets concatenated after correcting positional offset  
  > "A positional offset between short and long baseline was corrected prior to combining the datasets." (2.1 ALMA continuum and molecular line observations)
- smoothing: _not stated_
- final beam: uvmem 19.7x12.9 mas; 12CO 76x57 mas; 13CO/C18O 82x61 mas  
  > "yielding maps with a beam resolution of 82$\times$61 mas and RMS noise of 1.8 and 1.2 mJy beam$^{-1}$, respectively." (2.1 ALMA continuum and molecular line observations)
- final rms: Continuum 16.6 uJy/beam (uvmem); 12CO 1.3 mJy/beam per channel  
  > "Each channel map has an RMS noise of 1.3 mJy beam$^{-1}$, for a CLEAN beam of 76$\times$57 mas." (2.1 ALMA continuum and molecular line observations)

### Inherited from earlier work

- Polar deprojection procedure  
  > "The polar deprojection was carried out following the procedure outlined in (cite: Perez2019)" (3.1 A structured continuum ring) [from (cite: Perez2019)]
- SAM data processing  
  > "The data processing follows the same procedure as in (cite: Cheetham2019)." (2.2 SPHERE sparse aperture masking) [from (cite: Cheetham2019)]
- Deviations from axisymmetric flow quantified in companion Letter  
  > "The deviations from the azimuthally symmetric flow are quantified and discussed in a companion Letter (cite: Casassus2019)." (Introduction) [from (cite: Casassus2019)]

### Not stated but needed to reproduce (our reading)

- tclean masks, clean thresholds and iterations
- line-free channels for uvcontsub and continuum order
- uvmem parameters (iterations, initial image, weights)
- self-calibration reference antenna and which datasets were self-calibrated
- SAM regularization weights and calibrator details
- moment-map clipping thresholds and Gaussian fit setup

## Analysis recipe

1. **Calibrate and self-calibrate continuum**: ALMA pipeline calibration, one phase self-cal round, offset correction, concatenation  
  > "A positional offset between short and long baseline was corrected prior to combining the datasets." (2.1 ALMA continuum and molecular line observations)
   - software: CASA
   - parameter: solint 54 s  
  > "One round of phase self-calibration using a solution interval of 54s was applied to the data" (2.1 ALMA continuum and molecular line observations)
   - fitting: _not stated_
   - validation: SNR improved by 1.6  
  > "which was found to improve the resulting SNR by a factor of 1.6" (2.1 ALMA continuum and molecular line observations)
2. **Super-resolved continuum image**: uvmem non-parametric modeling with positivity only, no entropy  
  > "Image positivity provided enough regularization (i.e. we did not add entropy to the objective function)." (2.1 ALMA continuum and molecular line observations)
   - software: GPUVMEM
   - fitting: _not stated_
   - validation: Effective beam measured from simulated point-source spike with same uv-coverage; noise estimated from natural-weight noise scaled by sqrt(Nb)  
  > "The input spike flux was 10 mJy, which is comparable with the emission at the location of the central star." (2.1 ALMA continuum and molecular line observations)
3. **CO channel cubes and moment maps**: tclean cubes at 0.5 km/s; moment 0 intensity-weighted sum; moments 1 and 2 from Gaussian fits per pixel  
  > "first and second moments were determined via Gaussian fits to the velocity profile along each pixel" (2.1 ALMA continuum and molecular line observations)
   - software: CASA
   - parameter: robust 1.0 (12CO), 2.0 (13CO, C18O)  
  > "Channel maps were produced with a spectral resolution of 0.5 km s$^{-1}$." (2.1 ALMA continuum and molecular line observations)
   - fitting: Gaussian fits per pixel, with polynomial baseline for non-subtracted cubes  
  > "the continuum emission is accounted by a polynomial baseline when producing moment maps from Gaussian fits" (2.1 ALMA continuum and molecular line observations)
   - validation: Channelization checked with 0.25 km/s channels shifted by 0.1 km/s  
  > "by producing a cube with smaller channels (0.25 km s$^{-1}$) shifted by 0.1 km s$^{-1}$ in velocity" (2.1 ALMA continuum and molecular line observations)
4. **Enhance and deproject continuum substructure**: Unsharp mask (subtract image convolved with circular Gaussian sigma=60 mas); polar deprojection and azimuthal average  
  > "after convolution with a circular Gaussian kernel ($\sigma=60$ mas)" (3.1 A structured continuum ring)
   - assumption: disk orientation from Casassus2019  
  > "adopting the disk orientation derived in (cite: Casassus2019)" (3.1 A structured continuum ring)
   - fitting: _not stated_
   - validation: _not stated_
5. **SAM companion limits**: MIRA image reconstruction from closure phases and visibilities; 5-sigma contrast converted to mass with BT-Settl models  
  > "IRDIS and IFS images are produced using the MIRA package (cite: Thibaut2008) applied to the closure phases and visibilities, with a hyperbolic regularization term." (2.2 SPHERE sparse aperture masking)
   - software: MIRA, SPHERE DRH pipeline
   - assumption: stellar age 4-12 Myr  
  > "if we assume the youngest age of 4 Myr for the star, or 71 M$_{\mathrm{Jup}}$ for the eldest of 12 Myr" (3.3 Could the gap be opened by a stellar object?)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.4 (tclean); pipeline 40896: Calibration, tclean imaging, uvcontsub  
  > "Synthesis imaging was initially carried out using the CLEAN algorithm (CASA version 5.4, task `tclean`)." (2.1 ALMA continuum and molecular line observations)
- **uvmem (GPUVMEM)** : Super-resolved continuum image  
  > "We adopted the `uvmem` image for our analysis." (2.1 ALMA continuum and molecular line observations)
- **MIRA** : SAM image reconstruction  
  > "IRDIS and IFS images are produced using the MIRA package (cite: Thibaut2008)" (2.2 SPHERE sparse aperture masking)
- **SPHERE DRH pipeline** : Cleaning SAM data  
  > "The data were cleaned using the SPHERE Data Reduction and Handling (DRH) pipeline (cite: Pavlov2008)" (2.2 SPHERE sparse aperture masking)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| uvmem continuum beam | 19.7x12.9 | not stated | mas | 2 | The final $I_{1.3\mathrm{mm}}$ image has an angular resolution of $\Omega_b =
19.7\times12.9$ mas |
| Continuum noise (uvmem) | 16.6 | not stated | uJy/beam | 2 | We estimate that the noise level in the $I_{1.3\mathrm{mm}}$ image is 16.6 $\mu$Jy beam$^{-1}$ |
| Central source flux density | 3.1 | 0.3 | mJy | 2 | The flux density of the central source is 3.1$\pm$0.3 mJy |
| Total flux density | 436 | 40 | mJy | 2 | while the total flux density over the entire image is 436$\pm$40 mJy |
| Inner disk radius | ~1.8 | not stated | au | 2 | The emission is resolved with a radius of $\sim$1.8 au (half the FWHM along its major axis) |
| SAM mass upper limit | 33 (4 Myr) to 71 (12 Myr) | not stated | MJup | 5 | This limit corresponds to a mass of 33 M$_{\mathrm{Jup}}$ if we assume the youngest age of 4 Myr for the star, or 71 M$_{\mathrm{Jup}}$ for the eldest of 12 Myr. |
| Diffuse CO emission in gap | 30 | scatter 6 | mJy/beam km/s | 3 | Within the gap, diffuse CO emission averages 30 mJy beam$^{-1}$ km s$^{-1}$ with a scatter of 6 mJy beam$^{-1}$ km s$^{-1}$. |

## Qualitative findings

- Continuum ring shows ridges and trenches; ring is eccentric and optically thick, 15-45 au  
  > "The continuum reveals an optically thick and rather wide ring, extending from 15 to 45 au in radius." (Summary and conclusions)

## Claim tuples

- H: Does the gas kinematics show planet-like wiggles? | E: 12CO(2-1) channel and moment maps at ~8 au resolution | R: Wiggles over ~90 deg azimuth at 0.2-0.3 arcsec NE with Doppler flip | F: Resembles imprint of embedded 5-10 MJup planet, yet coincides with bright continuum | **partially**
- H: Is the wiggle vertically extended? | E: Compare 13CO and C18O channel maps with 12CO | R: Wiggles much weaker in rarer isotopologues | F: Consistent with vertical flows in the disk surface | **partially**
- H: Could a stellar binary open the gap? | E: SPHERE SAM | R: No signal in gap; mass limit 33-71 MJup | F: Stellar companions excluded | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Robust 1.0 chosen for best SNR without compromising resolution  
  > "which yield the best results in terms of achieving good signal-to-noise without compromising on resolution" (2.1 ALMA continuum and molecular line observations)
- Alternative: Optically thick continuum blocking back-side CO emission can also produce wiggles (SW)  
  > "an optically thick continuum, such as the one in HD 100546, blocks the CO emission from the back side of the disk, inducing structure in the gas velocity map" (3.2.1 Kinematic signature over the continuum ring)
- How they decided it was enough: _not stated_
- Limitation (authors): Central emission shape may be affected by the PSF; brightest gap feature likely an artefact  
  > "However, the shape of this central emission could be affected by the PSF." (3.1 A structured continuum ring)
- Caveat (inferred, ours): No quantitative kinematic modelling here; relies on companion paper
- Caveat (inferred, ours): Super-resolved uvmem image fidelity and noise estimate are approximate
- Caveat (inferred, ours): Planet interpretation is qualitative and conflicts with bright dust ring

## Reproducibility

- Data public (paper): Project code given; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00344.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Clean masks and thresholds
- Missing: uvmem run parameters
- Missing: Moment-map clipping and fitting details
- Missing: Line-free channels
- Data volume (inferred): ~200-500 GB raw for long and short baseline blocks
- Score (inferred): 3/5, Data settings and main imaging choices stated, but many tclean/uvmem details missing and kinematics analysis is in a companion paper.
- Rediscovery candidate: no, Main results are largely qualitative; imaging recipe incomplete.

## Links

- Method: (cite: Carcamo2018) (uvmem super-resolution imaging)
- Method: (cite: Cheetham2019) (SAM data processing)
- Companion: (cite: Casassus2019) (Quantifies deviations from axisymmetric flow and Doppler flip)
- Companion: (cite: Perez2018) (Hydrodynamic predictions of wiggles for embedded planets)

## Checks

```json
{
 "quotes": 67,
 "quotes_ok": 67,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 50,
  "rate": 0.667
 },
 "evidence_ok": true
}
```
