# The ALMA View of the OMC1 Explosion in Orion

`2017ApJ...837...60B` | The Astrophysical Journal 2017 | first author: Bally, John | arXiv: 1701.01906 | DOI: 10.3847/1538-4357/aa5c8b

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: What is the structure and kinematics of the OMC1 explosive outflow in 12CO J=2-1 and how does it relate to the ejection of BN, Source I and Source n?  
  > "We present new ALMA observations with $\sim$1$''$ angular resolution covering a 2$'$ by 3$'$ region containing the entire OMC1 outflow." (1.2 The OMC1 Outflow)
- Target **OMC1 outflow (Orion BN/KL)**: coordinates ejection center J2000 05h35m14.34s, -5d22'28.4"  
  > "point back to J2000 = 05$^h$35$^m$14.34$^s$, $-$5$^o$22’28.4"" (Results); "at a distance of $\sim$414 pc (cite: Menten2007; Goddi2011b)" (1.1 Ejection of Runaway Stars); z/distance ~414 pc  
  > "point back to J2000 = 05$^h$35$^m$14.34$^s$, $-$5$^o$22’28.4"" (Results); "at a distance of $\sim$414 pc (cite: Menten2007; Goddi2011b)" (1.1 Ejection of Runaway Stars); distance from Menten2007; Goddi2011b  
  > "point back to J2000 = 05$^h$35$^m$14.34$^s$, $-$5$^o$22’28.4"" (Results); "at a distance of $\sim$414 pc (cite: Menten2007; Goddi2011b)" (1.1 Ejection of Runaway Stars)

## Data provenance

- ALMA projects: 2013.1.00546.S
- bands: Band 6 (1.3 mm)  
  > "mapped with the Atacama Large Millimeter Array (ALMA) in the 1.3 mm atmospheric window (ALMA Band 6)" (Observations)
- frequencies and spectral setup: four 1.875 GHz bands centered at 216, 228, 231, 233 GHz; 0.488 MHz channels, 1.3 km/s resolution  
  > "using four 1.875 GHz-wide bands centered at 216, 228, 231, and 233 GHz." (Observations); "providing velocity resolution of 1.3 km s$^{-1}$" (Observations)
- continuum bandwidth: _not stated_
- arrays: 12-m array, ACA 7-m, and 12-m total-power antennas  
  > "re-observed with the twelve-element ALMA Compact Array (ACA) of 7-meter diameter antennas and the four 12-meter diameter total-power antennae" (Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.36" x 0.78" synthesized beam (~400 AU)  
  > "resulting in a synthesized beam with dimensions of 1.$''$ 36$\times$0.$''$ 78" (Observations)
- max recoverable scale: _not stated_
- sensitivity: 5 mJy per channel typical; continuum 0.5 mJy; up to 0.5 Jy in bright channels  
  > "The noise is 5 mJy in a typical spectral line channel" (Observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (~230 GHz)
- External data: Proper motions of BN, Source I and n  
  > "26.6 km s$^{-1}$ towards PA = 323$^\circ$ (cite: Dzib2016; Rodriguez2016)" (1.1) [from Dzib2016; Rodriguez2016; Gomez2008; Goddi2011]
- External data: CO SLED temperatures 200, 500, 2500 K  
  > "can be well fit with three components having temperatures of 200 K, 500 K and 2500 K" (Column densities and masses) [from Goicoechea2015]

## Processing

### Calibration

- pipeline or manual: ALMA QA2 reduction in CASA with standard flux, bandpass, gain calibration  
  > "The ALMA QA2 reduction included heavy flagging to remove strong spectral lines from the continuum, as well as the standard flux, bandpass, and gain calibrations." (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5  
  > "CLEAN-ed using a Briggs robust weighting parameter of 0.5" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12-m and 7-m visibilities combined in uv-plane  
  > "The *uv*-plane visibilities from the two data sets were combined using the CASA package" (Observations)
- smoothing: _not stated_
- final beam: 1.36" x 0.78"  
  > "synthesized beam with dimensions of 1.$''$ 36$\times$0.$''$ 78" (Observations)
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- CASA version
- Cell size, image size, clean threshold, masks
- Whether total-power data were combined
- Line-free channels and continuum subtraction
- Observing dates, configurations, calibrators
- Method for fitting streamer lines and determining intersection points

## Analysis recipe

1. **Image combined 12m+ACA CO cube**: Combine uv data, CLEAN with Briggs weighting in CASA  
  > "imaged, and CLEAN-ed using a Briggs robust weighting parameter of 0.5" (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Make maximum-brightness and moment maps, identify streamers**: Peak temperature per pixel over velocity ranges and moment 0  
  > "Figure 1 shows the maximum flux (brightness temperature) in each pixel from V$_{LSR}$ = $-$100 to +120 km s$^{-1}$" (Results)
   - fitting: _not stated_
   - validation: _not stated_
3. **Dynamical age of streamers**: t_dyn = R_max/V_max, with inclination correction from r_end/R_max  
  > "If the proper motions at 50$''$ projected distance were 159 km s$^{-1}$, the dynamic age would be $t_{dyn} = R_{max} / V_{max} \approx$ 620 years." (High radial-velocity structure)
   - assumption: spherical symmetry and simultaneous production of all streamers  
  > "Assuming spherical symmetry and that all streamers were produced at the same time" (High radial-velocity structure)
   - fitting: _not stated_
   - validation: Compared with SMA age and stellar ejection times  
  > "The ALMA data are consistent with an age of 470 to 700 years, similar to the age obtained by (cite: Zapata2009c) with the SMA" (High radial-velocity structure)
4. **Streamer density and excitation**: RADEX non-LTE modelling of CO 2-1 brightness  
  > "the radiative transfer and excitation code RADEX (cite: vanderTak2007) indicates that the CO excitation temperature in the J=2$-$1 line ranges from 25 K to 88 K" (Column densities and masses)
   - software: RADEX
   - assumption: X_CO = 1e-4 n(H2), 1.2" streamer depth, kinetic temperature 200 K, background 10 or 100 K  
  > "Assuming cylindrical geometry, a characteristic width or depth of 1.2$''$ (500 AU), and a $^{12}$CO abundance $X_{CO} = 10^{-4} n(H_2)$" (Column densities and masses)
   - fitting: _not stated_
   - validation: Opacities checked against C18O non-detection  
  > "These optical depths are consistent with the non-detection of C$^{18}$O at a brightness temperature above 0.2 K" (Column densities and masses)
5. **Mass of fast CO gas**: X-factor conversion of CO flux to H2 mass, summed over 86" circle  
  > "Integration of the CO data cube over an 86" diameter circle and summing the flux over the radial velocity ranges $-$100 to 0 km s$^{-1}$ and +20 to 120 km s$^{-1}$ implies a mass of 1.0 M$_{\odot}$" (Column densities and masses)
   - assumption: Bolatto2013 X-factor N(H2)=2.6e20 T*_A dV  
  > "which gives $N(H_2) \approx ~2.6 \times 10^{20} ~T^*_A \Delta V$" (Column densities and masses)
   - fitting: _not stated_
   - validation: Lower bound because of interferometric filtering  
  > "extended emission is filtered out and thus our mass estimates are lower bounds" (Column densities and masses)

## Software

- **CASA** : data reduction, combination, imaging  
  > "The raw data were reduced using the Common Astronomy Software Applications package, CASA (cite: casa)." (Observations)
- **RADEX** : CO excitation and density estimates  
  > "the radiative transfer and excitation code RADEX (cite: vanderTak2007)" (Column densities and masses)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Peak CO streamer brightness | 4.3 Jy/beam (~90 K) | not stated | Jy/beam | 1 | The peak CO flux in the streamers is about 4.3 Jy/beam in both the redshifted and blueshifted ranges |
| Dynamical age (R_max/V_max) | 620 | range 470-700 yr | years | 3 | The ALMA data are consistent with an age of 470 to 700 years |
| Mass of fast CO streamers | ~1 | lower bound | Msun | 5 | The total mass of the streamers traced by CO having a radial velocity that differs from the ambient cloud by more than 20 km s$^{-1}$ is $M_{fast} \sim$1 M$_{\odot}$. |
| Required energy of explosion | 1e48 | at least | erg | 0 | the energy source responsible for the ejection must supply at least $E_{tot}$ = $10^{48}$erg. |
| CO density required (kinetic T 100 K) | 1e6 to 1e7 | not stated | cm^-3 | 4 | the acceptable volume density ranges from $\sim 10^6$ to $\sim 10^7$ cm$^{-3}$ for a background radiation temperature of 10 K |

## Qualitative findings

- Over 100 CO streamers follow a Hubble flow, pointing to the ejection center and H2/[Fe II] fingertips; CO does not reach the fastest northern fingertips.  
  > "The streamers exhibit a roughly isotropic, spherically symmetric distribution exhibiting a ‘Hubble flow’" (Conclusions)

## Claim tuples

- H: The OMC1 CO outflow is an explosion linked to the stellar ejection | E: Map CO 2-1 streamers and trace back to origin | R: Over 80% of streamers trace back to a 3x5" region near the stellar ejection site | F: Explosion powered by the dynamical ejection event ~500 yr ago | **supported**
- H: Ejecta are spherically symmetric | E: Compare CO streamer extent with H2/[Fe II] fingers | R: To the north and northwest CO extent is about half that of the fingers | F: Deviations from symmetry exist | **supported**
- H: Energy source of the event | E: Energetics of stellar motions and outflow | R: ~1e48 erg required | F: Compact binary formation or protostellar merger plausible | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Gaps between CO ends and fingertips: CO destruction by shocks, atomic/ionized launch, or empty gap  
  > "Several models might explain the gaps between the ends of the CO streamers and the near-IR shocks in the fingertips." (The relationship of the CO streamers and the H2 fingers)
- How they decided it was enough: _not stated_
- Limitation (authors): Missing flux from interferometer filtering; masses are lower bounds  
  > "The spatial-filtering of the interferometer severely limits our ability to estimate masses within the inner $\pm$10 km s$^{-1}$" (Column densities and masses)
- Caveat (inferred, ours): Total-power combination not clearly described
- Caveat (inferred, ours): Streamer identification is by eye with no quantitative catalog
- Caveat (inferred, ours): Mass estimates depend on assumed temperatures and abundances

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Full imaging parameters
- Missing: Streamer catalog and fitting procedure
- Missing: CASA version
- Data volume (inferred): ~100-500 GB (large mosaic with 4 spws, 12m+ACA)
- Score (inferred): 4/5, Archive data code given but imaging details and analysis procedures sparse; mostly qualitative.
- Rediscovery candidate: no, Main results are largely qualitative and the recipe is incomplete.

## Links

- Companion: Zapata2009c (Earlier SMA CO map of streamers)
- Companion: BallyGinsburg2015 (H2 and [Fe II] fingers image)

## Checks

```json
{
 "quotes": 46,
 "quotes_ok": 46,
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
  "stated": 31,
  "rate": 0.456
 },
 "evidence_ok": true
}
```
