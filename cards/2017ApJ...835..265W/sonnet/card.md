# Dense Molecular Gas Tracers in the Outflow of the Starburst Galaxy NGC 253

`2017ApJ...835..265W` | The Astrophysical Journal 2017 | first author: Walter, Fabian | arXiv: 1701.05040 | DOI: 10.3847/1538-4357/835/2/265

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies
- Question: What are the kinematics, origin and dense-gas content of the south-west molecular outflow streamer in NGC 253, and what drives it?  
  > "Strikingly, bright tracers of dense molecular gas (HCN, CN, HCO$^+$, CS) are also detected in the molecular outflow" (abstract)
- Target **NGC 253 (SW streamer)**: coordinates _not stated_; z/distance D = 3.5 Mpc  
  > "We assume a distance to NGC 253 of $D=3.5$ Mpc (Rekola et al. 2005), leading to a linear (projected) scale of 1$''$ = 17 pc." (1 Introduction); distance from Rekola et al. 2005  
  > "We assume a distance to NGC 253 of $D=3.5$ Mpc (Rekola et al. 2005), leading to a linear (projected) scale of 1$''$ = 17 pc." (1 Introduction)

## Data provenance

- ALMA projects: 2011.0.00172.S, 2012.1.00108.S
- bands: Band 3, two setups (high-frequency: CO(1-0), CN; low-frequency: HCN, HNC, HCO+, CS)  
  > "Two frequency setups were observed in ALMA band 3, one high–frequency setup (LSB: 99.8–103.7 GHz; USB: 111.8–115.7 GHz)" (2.1 ALMA Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12m array plus ACA (high-frequency setup); 12m (low-frequency)  
  > "These observations were complemented by a 2.6 h, 7-pointing mosaic with the ALMA compact array (ACA)" (2.1 ALMA Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: CO rms 1.6 mJy/beam per 5 km/s (practical floor 6.5); HCN, CN, CS, HCO+ rms 1 mJy/beam  
  > "For the HCN, CN, CS, and HCO$^+$ lines, the rms is 1 mJy beam$^{-1}$ for a 1.9$''\times$1.9$''$ beam." (2.1 ALMA Observations)
- time on source: High-freq 12m 2.5 h; ACA 2.6 h; low-freq 27.5 min  
  > "The total on–source integration time was 2.5 h, using typically 36 antennas." (2.1 ALMA Observations); "with a total of 27.5 minutes on–source using 32 antennas." (2.1 ALMA Observations)
- observing dates: Cycle 1: Oct 2013 to Dec 2013 (high-freq), 31-Aug-2014 (low-freq); cycle 0 from earlier papers  
  > "Observations were done on 31-Aug-2014" (2.1 ALMA Observations)
- pi or archival as stated: _not stated_
- Line: CO 1-0 (not stated)
- Line: CN 1,3/2,5/2 -> 0,1/2,3/2 (113490.9 MHz)
- Line: HCN, HCO+, CS 1-0, 1-0, 2-1 (not stated)
- Other facility **IRAM 30m**: Zero-spacing data for dense-gas tracers  
  > "We use new IRAM 30 m telescope measurements to correct the high–density tracer molecules (low–frequency setup)." (2.2 Single Dish Observations)
- Other facility **Mopra**: Zero-spacing data for CO(1-0)  
  > "We use measurements obtained by the Mopra telescope to correct the ALMA CO(1–0) observations" (2.2 Single Dish Observations)
- Other facility **HST**: Halpha and Pa-beta imaging of ionized outflow  
  > "We compare our ALMA observations to the ionized gas outflow, traced by *Hubble Space Telescope* imaging of hydrogen recombination lines." (2.3 Hubble Space Telescope Observations)
- External data: Galaxy inclination 78 deg and ionized outflow cone geometry  
  > "The inclination of the galaxy is 78$^\circ$ (Westmoquette et al. 2011)" (3.3 Is the Molecular Outflow Accelerating?) [from Westmoquette et al. 2011]
- External data: Circular velocity used for escape velocity  
  > "the circular velocity by Hlavacek-Larrondo et al. 2011" (3.3 Is the Molecular Outflow Accelerating?) [from Hlavacek-Larrondo et al. 2011]
- External data: Total IR luminosity 1.4e44 erg/s  
  > "NGC 253 has a total infrared luminosity of L$_{\rm TIR}=1.4\times10^{44}$ erg s$^{-1}$" (3.7 The driving of the SW Streamer) [from Leroy et al. 2015]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Uranus (12m high-freq), Neptune (ACA and low-freq)  
  > "J0038-2459 (phase), J2357-5311 (bandpass) and Uranus (amplitude)" (2.1 ALMA Observations)
- flux scale uncertainty: _not stated_
- self calibration: Phase then amplitude self-calibration on the continuum  
  > "Phase information using the continuum were self-calibrated first followed by amplitude self-calibration." (2.1 ALMA Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Natural and Briggs robust cubes (robust value not stated)  
  > "Natural and Briggs robust–weighted, continuum–subtracted, cubes were created at 5 km s$^{-1}$ velocity resolution." (2.1 ALMA Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: Applied for all quantitative analysis  
  > "All values were primary beam corrected for all quantitative analysis." (2.1 ALMA Observations)
- array combination: Mopra via Miriad immerge (16.2 Jy/K); IRAM via CASA feather (6.15 Jy/K); feathered cubes used as clean models via setjy  
  > "we combined the ALMA cube with the Mopra single dish data using the feathering Miriad task `immerge` with a gain of 16.2 Jy/K." (2.2 Single Dish Observations)
- smoothing: Convolved to common 1.9 arcsec (32 pc) beam  
  > "for all comparisons we convolve the low– and high–frequency setups to a common beam size of 1.9$''$ (32 pc)" (2.1 ALMA Observations)
- final beam: CO: 1.6" x 1.2", PA 71.5 deg; others 1.9" x 1.9"  
  > "a beam size of 1.6$"\times$1.2$"$ with PA of 71.5$^\circ$" (2.1 ALMA Observations)
- final rms: CO 1.6 mJy/beam (5 km/s); HCN etc. 1 mJy/beam  
  > "The final robust-weighed CO(1–0) cube has an rms of 1.6 mJy beam$^{-1}$ in 5 km s$^{-1}$ channels" (2.1 ALMA Observations)

### Inherited from earlier work

- ALMA observation and reduction details  
  > "Additional details about the ALMA observations and reduction can be found in Bolatto et al. (2013), Leroy et al. (2015b), and Meier et al. (2015)." (2.1 ALMA Observations) [from Bolatto et al. (2013); Leroy et al. (2015b); Meier et al. (2015)]
- CO-to-H2 conversion alpha_CO=0.34 and projection correction factor ~3  
  > "Bolatto et al. (2013) argue that a correction factor of $\sim3$ is more likely, and we adopt that value here." (3.3 Is the Molecular Outflow Accelerating?) [from Bolatto et al. (2013)]

### Not stated but needed to reproduce (our reading)

- Briggs robust value and uv-taper
- clean masks, thresholds, cell and image size
- line-free channels for continuum subtraction
- self-calibration solution intervals
- CASA version
- how CO luminosity and streamer area were measured
- exact velocity range and region for peak flux extraction

## Analysis recipe

1. **Build combined cubes**: Self-calibrate, image, feather with Mopra/IRAM, re-clean using feathered model, convolve to 1.9 arcsec  
  > "the final cubes were created using the feathered cubes as models for the inversion of the ALMA data." (2.2 Single Dish Observations)
   - software: CASA, Miriad
   - fitting: _not stated_
   - validation: Zero-spacing correction improved negative bowls  
  > "this zero spacing correction significantly improved the negative bowls in the original (ALMA 12m–only) data cubes." (2.2 Single Dish Observations)
2. **Streamer kinematics**: Gaussian fits to spectra along pv cut; first-order polynomial to central velocity vs position; deconvolved width  
  > "A first order polynomial fit to the central velocity as a function of position is overplotted as a red line." (3.2 Spectra Along the SW Streamer)
   - assumption: Projection correction factor ~3  
  > "Adopting the aforementioned projection correction factor of 3" (3.3 Is the Molecular Outflow Accelerating?)
   - fitting: Gaussian line fits; linear fit  
  > "A first order polynomial fit to the central velocity as a function of position is overplotted as a red line." (Spectra Along the SW Streamer)
   - validation: OLS bisector gives 25% higher gradient  
  > "the symmetric ordinary-least-squares bisector yields a 25% higher value" (3.3 Is the Molecular Outflow Accelerating?)
3. **Line ratios**: Compare peak flux densities of CO, HCN, HCO+, CS, CN at common resolution in center, streamer and disk  
  > "At an offset of $-6.5\ensuremath{''}$, significantly off the central starburst region" (3.5 Dense Gas in the Outflow)
   - fitting: _not stated_
   - validation: _not stated_
4. **Mass, density and radiation pressure estimates**: Minimum mass from optically thin alphaCO; volume density with clumping; extinction from Halpha/Pabeta; radiation pressure force calculation  
  > "Bolatto et al. (2013) used a CO-to-H$_2$ conversion factor $\alpha_{\rm CO}=0.34$" (3.6 Mass and Density of the SW Streamer)
   - assumption: Cylindrical geometry, T_b~100 K, Cardelli et al. extinction curve  
  > "Assuming an intrinsic brightness of T$_{\rm b}\sim100$ K" (3.6.1 Inferred volume densities)
   - fitting: _not stated_
   - validation: Extinction-based N(H2) compared with CO-based  
  > "These numbers are consistent with the “lower limit” mass estimate from CO inferred above." (3.6.3 Constraints to mass and surface density from extinction)

## Software

- **CASA** : clean, feather, setjy  
  > "using the CASA task `feather`" (2.2 Single Dish Observations)
- **Miriad** : immerge feathering with Mopra  
  > "feathering Miriad task `immerge`" (2.2 Single Dish Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Velocity gradient (observed) | 6.1 | not stated | km/s per arcsec | 2 | We measure a gradient of d$v$/d$r=6.1$ km s$^{-1}$/\[$''$\] |
| Deprojected velocity gradient | ~1 | not stated | km/s/pc | 2 | we derive an actual velocity gradient of $\sim$ 100 km s$^{-1}$/\[100 pc\], or $\sim$1 km s$^{-1}$/\[pc\] |
| CO/HCN peak flux ratio: center, streamer, disk | 13.8, ~12, ~35 | not stated | dimensionless | 3 | These values yield a CO/HCN peak flux density ratio $\sim 12$.; These yield a CO/HCN peak flux density ratio $\sim35$ |
| Streamer CO(1-0) luminosity | 2.8e6 | not stated | K km/s pc^2 | 4 | $L_{\rm CO}\sim2.8\times10^6$ K km s$^{-1}$ pc$^2$ |
| Average volume density | 40 | not stated | cm^-3 | 4 | this results in an average volume density of 40 cm$^{-3}$ |
| Radiation-pressure velocity range | 15-120 | not stated | km/s | 4 | which would result in $15\leq v_{cloud}\leq 120$ km s$^{-1}$ |

## Qualitative findings

- Streamer aligns with edge of ionized Halpha/Pabeta outflow  
  > "The *SW streamer* aligns closely with the edge of the outflow as seen in both H$\alpha$ and the more extinction–robust Pa$\beta$ imaging" (3.4 Deep Imaging of the Ionized Gas)

## Claim tuples

- H: Does the streamer contain dense gas with starburst-like properties? | E: Compare CO and dense tracer peak flux ratios in center, streamer and disk | R: CO/HCN ~12 in streamer vs ~35 in disk | F: Gas originates in the starburst and retains its dense state | **supported**
- H: Is the outflow accelerating toward escape velocity? | E: Linear fit of velocity along pv cut with projection correction | R: ~1 km/s/pc, 360 km/s vs ~500 km/s escape | F: Consistent with acceleration but not unique | **partially**
- H: Is radiation pressure the main driver? | E: Simple force estimate | R: Velocity 15-120 km/s | F: Not the dominant mechanism | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Velocity gradient could come from short ejection with velocity distribution or inclination gradient; latter judged less likely  
  > "This interpretation of the data is, however, not unique." (3.3 Is the Molecular Outflow Accelerating?)
- How they decided it was enough: _not stated_
- Limitation (authors): Projection correction highly uncertain, factor from ~1 to infinity  
  > "the actual factor can range from $\sim1$ to $\infty$ so the projection correction has large uncertainties." (3.3 Is the Molecular Outflow Accelerating?)
- Caveat (inferred, ours): Many estimates are order-of-magnitude with no uncertainties
- Caveat (inferred, ours): Line ratios from peak flux at single positions, not integrated
- Caveat (inferred, ours): Mass is only a minimum, optically-thin alphaCO
- Caveat (inferred, ours): Imaging parameters mostly deferred to earlier papers

## Reproducibility

- Data public (paper): ALMA projects cited; IRAM project 209-14  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA #2011.0.00172.S, #2012.1.00108.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters (robust, masks, cell size)
- Missing: IRAM 30m and Mopra data access
- Missing: Region definitions for fluxes and mass
- Data volume (inferred): ~100-300 GB raw for cycle 0+1 band 3 mosaics
- Score (inferred): 3/5, Data public and analysis simple, but processing is deferred to earlier papers and single-dish data are needed.
- Rediscovery candidate: no, Recipe incomplete and requires inherited processing plus non-ALMA single-dish data.

## Links

- Method: Bolatto et al. 2013 (ALMA observations, reduction, alphaCO and projection correction)
- Method: Meier et al. 2015 (Data description and line optical depths)
- Method: Leroy et al. 2015b (Combined cycle 0+1 data analysis)

## Checks

```json
{
 "quotes": 57,
 "quotes_ok": 57,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
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
