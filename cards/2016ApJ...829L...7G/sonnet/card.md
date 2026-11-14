# High-velocity Bipolar Molecular Emission from an AGN Torus

`2016ApJ...829L...7G` | The Astrophysical Journal Letters 2016 | first author: Gallimore, Jack F. | arXiv: 1608.02210 | DOI: 10.3847/2041-8205/829/1/L7

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, nearby_galaxies
- Question: What is the kinematics of molecular gas in the NGC 1068 AGN torus, and does it support the disk-wind scenario?  
  > "although the torus’s compact dimensions are now firmly established, its kinematics and dynamic origin remain uncertain." (Introduction)
- Target **NGC 1068**: coordinates _not stated_; z/distance 14.4 Mpc; 1'' = 70 pc  
  > "We adopt a distance to the source of 14.4 Mpc (cite: Bland-Hawthorn97). The scale is $1\ensuremath{''} = 70$ pc." (Introduction); distance from Bland-Hawthorn et al. 1997  
  > "We adopt a distance to the source of 14.4 Mpc (cite: Bland-Hawthorn97). The scale is $1\ensuremath{''} = 70$ pc." (Introduction)

## Data provenance

- ALMA projects: 2013.1.00014.S
- bands: Band 9 (~450 micron)  
  > "We observed NGC 1068 in Band 9 ($\lambda \sim 450$$\mu$m) during ALMA Cycle 2" (2 Observations and Data Processing)
- frequencies and spectral setup: three continuum spws of 2 GHz each plus one CO(6-5) line window, ~0.21 km/s channels, ~±400 km/s  
  > "Spectral windows were tuned to observe three independent continuum bands, 2 GHz bandwidth each, and one line window for CO" (2 Observations and Data Processing)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15–1466 m  
  > "The baseline range was 15–1466 m" (2 Observations and Data Processing)
- angular resolution: 0.084'' x 0.064'', PA 75 deg (5.9 x 4.5 pc)  
  > "the synthetic restoring beam (angular resolution) is $0.084\ensuremath{''} \times 0.064\ensuremath{''}$, PA $75\hbox{$^\circ$}$" (2 Observations and Data Processing)
- max recoverable scale: ~270 pc (3.8'')  
  > "Resulting images are insensitive to structures larger than about 270 pc (3.8$''$)." (2 Observations and Data Processing)
- sensitivity: rms 0.49 mJy/beam continuum; 5.3 mJy/beam CO channel maps (10 km/s)  
  > "The background rms noise levels are 0.49 mJy beam$^{-1}$ and 5.3 mJy beam$^{-1}$ for Band 9 continuum and the CO channel maps, respectively." (2 Observations and Data Processing)
- time on source: 32.1 minutes  
  > "Total time on source was 32.1 minutes." (2 Observations and Data Processing)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=6-5 (691.47308 GHz)
- External data: H2O maser spots and S1 radio source position/disk  
  > "the nuclear radio source, S1, and its associated H$_2$O vapor maser disk (cite: Greenhill97; Gallimore04)" (Results) [from Greenhill97; Gallimore04]
- External data: Outflow axis inclined 5 deg out of the plane of sky  
  > "is inclined 5$^\circ$ out of the plane of the sky (cite: Crenshaw00)" (Results) [from Crenshaw00]
- External data: Keplerian central mass 1.5e7 Msun fit to maser disk  
  > "around a 1.5$\times$$10^{7}$ $M_{\odot}$ central mass that best fits the H$_2$O maser disk observations (cite: Lodato03)" (Results) [from Lodato03]

## Processing

### Calibration

- pipeline or manual: standard procedures in CASA  
  > "Calibration and data reduction followed standard procedures for ALMA observations in CASA (CASA v.4.3.1" (2 Observations and Data Processing)
- casa version: CASA 4.3.1  
  > "CASA v.4.3.1" (2 Observations and Data Processing)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: 3C454.3 and J2253+1608  
  > "limited by the photometric uncertainties of the flux calibrators (3C454.3 and J2253+1608)" (2 Observations and Data Processing)
- flux scale uncertainty: ~10%  
  > "The photometric accuracy, $\sim$10%, is limited by" (2 Observations and Data Processing)
- self calibration: two rounds of phase-only self-calibration over scan intervals  
  > "Two rounds of phase-only self-calibration reduced sidelobe artifacts and improved the background rms." (2 Observations and Data Processing)

### Imaging

- task: _not stated_
- deconvolver: multiscale CLEAN  
  > "multiscale CLEAN deconvolution" (2 Observations and Data Processing)
- weighting robust: Briggs weighting (robust not stated)  
  > "Images and data cubes were produced using Briggs weighting" (2 Observations and Data Processing)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: CO cube binned to 10 km/s channels  
  > "The CO spectral line cube was binned to 10 km s$^{-1}$ channel-widths during imaging and deconvolution." (2 Observations and Data Processing)
- final beam: _not stated_
- final rms: 0.49 mJy/beam continuum; 5.3 mJy/beam CO channel  
  > "0.49 mJy beam$^{-1}$ and 5.3 mJy beam$^{-1}$" (2 Observations and Data Processing)

### Inherited from earlier work

- Astrometric correction aligning Band 9 continuum peak to AGN position  
  > "We therefore adopted an astrometric correction by aligning the Band 9 continuum peak to the position of the active nucleus (cf. GB16)." (2 Observations and Data Processing) [from GB16 (cite: García-Burillo16)]

### Not stated but needed to reproduce (our reading)

- Briggs robust value
- multiscale scales, cell and image size, clean masks and thresholds
- continuum subtraction method and line-free channels
- self-calibration solint and reference antenna
- position of AGN used for astrometric alignment
- simulation random seeds and clump parameters beyond those listed
- phase center coordinates

## Analysis recipe

1. **Calibrate, self-calibrate and image**: Standard CASA calibration, two rounds phase-only self-cal, Briggs multiscale CLEAN to 10 km/s channels  
  > "Images and data cubes were produced using Briggs weighting (cite: Briggs1995) and multiscale CLEAN deconvolution" (2 Observations and Data Processing)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Blue/systemic/red moment maps and displacement**: Integrate CO in v<-70, |v|<=70, v>+70 km/s bins and compare blue and red peak positions  
  > "blueshifted, $v < -70$ km s$^{-1}$(blue contours); systemic, $-70 \leq v \leq
+70$ km s$^{-1}$(greyscale)" (Results)
   - fitting: _not stated_
   - validation: _not stated_
3. **Spectroastrometry of channel peaks**: Find peaks >3 sigma per channel and refine with local 2-D Gaussian fit  
  > "Peaks $> 3.0\sigma$ on individual channel maps were recorded, and their positions were refined using a local 2-D Gaussian fit." (Results)
   - software: photutils find_peaks (Astropy)
   - fitting: 2-D Gaussian  
  > "Peaks $> 3.0\sigma$ on individual channel maps were recorded, and their positions were refined using a local 2-D Gaussian fit." (Results)
   - validation: Compared to bicone simulation  
  > "To test this possibility we conducted a numerical simulation of a bipolar outflow." (Results)
4. **Simulate bipolar outflow**: 10^4 clumps in truncated cone, accelerated 30 to 800 km/s, inclined 5 deg, 0.5 pc position errors  
  > "We employ a truncated cone geometry with a disk base diameter of 1 pc (comparable to the H$_2$O maser disk), 4.4 pc total bicone height" (Results)
   - assumption: Outflow axis inclined 5 deg, as in ionized gas  
  > "we assume the same for the CO outflow" (Results)
   - fitting: Interactive trials, not a fit  
  > "these values were selected from interactive trials to give a reasonable match to the observations." (Results)
   - validation: Qualitative comparison of red-blue asymmetry  
  > "broadly reproduce a parsec-scale asymmetry of redshifted and blueshifted peaks similar to that observed (left panel)." (Results)
5. **Position-velocity diagram and Keplerian disk model**: Slice cube along systemic extension axis (3-pixel width), Savitzky-Golay smoothing for display; simulate edge-on Keplerian disk for 1.5e7 Msun, emissivity r^-2  
  > "The data were smoothed using a Savitzky-Golay filter (7 channels, polynomial order 3; (cite: SavitzkyGolay)) along the velocity axis for display purposes." (Results)
   - fitting: not fit; illustrative  
  > "This simulation is not intended to fit the CO data but to illustrate the appearance of a rotating disk on the $p$–$v$ diagram." (Results)
   - validation: _not stated_

## Software

- **CASA** 4.3.1: calibration, imaging  
  > "CASA v.4.3.1" (2 Observations and Data Processing)
- **Astropy photutils** : find_peaks for spectroastrometry  
  > "find_peaks from the photutils package of Astropy" (Results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO low-velocity structure size | 12 x 7 | not stated | pc | 1 | resolves into a 12$\times$7 pc structure |
| Blue-red peak displacement | 1.2 | not stated | pc | 2 | displaced 1.2 pc northeast (PA$\simeq 33\hbox{$^\circ$}$) of the redshifted peak |
| Angle between displacement axis and maser line | 78 | 2 | deg | 2 | roughly orthogonal ($78\hbox{$^\circ$}\pm2\hbox{$^\circ$}$) to the line of masers |
| Peak CO 6-5 brightness temperature | 31.1 | not stated | K | 0 | brightness temperature, which peaks at 31.1 K |
| Astrometric shift | 9.5 mas west, 11 mas south (1.0 pc) | not stated | mas | 1 | the shift moves the Band 9 continuum peak 9.5 mas west and 11 mas south |

## Qualitative findings

- High-velocity CO (up to ±400 km/s) is consistent with a bipolar outflow nearly perpendicular to the nuclear disk, with possible rotation in the p-v diagram.  
  > "Higher-velocity emission (up to $\pm 400$ km s$^{-1}$) is consistent with a bipolar outflow" (abstract)

## Claim tuples

- H: CO emission traces a bipolar outflow from the torus | E: Velocity-binned maps and spectroastrometry with a 5-degree-tilt bicone simulation | R: Blue and red peaks are displaced 1.2 pc along an axis ~78 deg to the maser line | F: The high-velocity CO is consistent with a bipolar outflow along the AGN axis | **supported**
- H: The CO velocity field also contains rotation | E: p-v diagram compared with an illustrative Keplerian disk model | R: Elongated components match the maser chain and a shallower slope | F: Kinematics are consistent with rotation plus outflow, i.e. a disk wind | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: A collimated jet explanation of the p-v elongated features was judged unlikely.  
  > "The existence of two such features with different slopes and the overlap of one of them with the maser line make a jet-based explanation unlikely" (Results)
- How they decided it was enough: _not stated_
- Limitation (authors): Single CO transition makes it hard to constrain cloud physical parameters.  
  > "Having detected a single CO transition, it is difficult to derive strong constraints on the physical parameters of emitting clouds." (Discussion)
- Caveat (inferred, ours): Qualitative simulations without fitting or error analysis
- Caveat (inferred, ours): Astrometric alignment assumption affects red-blue displacement
- Caveat (inferred, ours): 1.2 pc displacement is below the beam size and comparable to astrometric uncertainty
- Caveat (inferred, ours): Outflow inclination borrowed from optical NLR

## Reproducibility

- Data public (paper): Project code given and ALMA data acknowledged; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00014.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Briggs robust, clean parameters and masks
- Missing: simulation code
- Missing: phase center and AGN reference position
- Data volume (inferred): tens to hundreds of GB raw
- Score (inferred): 3/5, Data identified, but imaging parameters and simulation details are sparse and results are mostly qualitative.
- Rediscovery candidate: no, Key results are mainly qualitative, and the imaging recipe is incomplete.

## Links

- Companion: García-Burillo et al. 2016 (cite: García-Burillo16) (Independent ALMA observations of the NGC 1068 torus)

## Checks

```json
{
 "quotes": 50,
 "quotes_ok": 50,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 40,
  "rate": 0.588
 },
 "evidence_ok": true
}
```
