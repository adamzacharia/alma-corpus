# First Connection between Cold Gas in Emission and Absorption: CO Emission from a Galaxy-Quasar Pair

`2016ApJ...820L..39N` | The Astrophysical Journal Letters 2016 | first author: Neeleman, Marcel | arXiv: 1604.05720 | DOI: 10.3847/2041-8205/820/2/L39

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: Does the z = 0.101 galaxy toward PKS 0439-433 emit CO(1-0), and does the molecular absorption toward the quasar arise from its molecular disk or from its CGM?  
  > "By combining the results of emission and absorption studies, we find that the strongest molecular absorption component toward the quasar cannot arise from the molecular disk" (abstract)
- Target **z = 0.101 spiral galaxy toward PKS 0439-433**: coordinates _not stated_; z/distance z = 0.101  
  > "This supersolar metallicity absorber is associated with a spiral galaxy, at a projected distance of 7.3 kpc to the quasar" (1. INTRODUCTION); "corresponding to ≈ 3.7 kpc at z = 0.101" (3. ALMA OBSERVATIONS); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.01178.S
- bands: Band 3  
  > "We used ALMA band 3 receivers to carry out a deep search for redshifted CO(1−0) emission" (3. ALMA OBSERVATIONS)
- frequencies and spectral setup: four spectral windows; one at 104.7 GHz (CO(1-0)), three for continuum  
  > "One of the four spectral windows was centered at the redshifted CO(1−0) line frequency of 104.7 GHz, while the three other spectral windows were used for continuum observations of the field." (3. ALMA OBSERVATIONS)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: compact antenna configuration  
  > "A compact antenna configuration resulted in an angular resolution of ∼ 2′′" (3. ALMA OBSERVATIONS)
- baselines: _not stated_
- angular resolution: ~2 arcsec (≈3.7 kpc)  
  > "A compact antenna configuration resulted in an angular resolution of ∼ 2′′" (3. ALMA OBSERVATIONS)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: UT 2014 December 25  
  > "on UT 2014 December 25" (3. ALMA OBSERVATIONS)
- pi or archival as stated: _not stated_
- Line: CO J=1-0 (not stated (redshifted to 104.7 GHz))
- Other facility **B-band imaging (Chen et al. 2005)**: B-band image used as overlay for CO contours  
  > "overlaid on a B-band image of the field surrounding PKS 0439−433 taken by Chen et al. (2005)" (Figure 1)
- External data: Stellar mass log M*/Msun = 10.01 ± 0.02 and SFR ≈ 1.5 Msun/yr  
  > "the stellar mass of the spiral galaxy has been estimated to be log[M ⋆ /M ⊙ ] = 10.01 ± 0.02" (2. THE Z = 0.101 ABSORBER) [from Christensen et al. 2014]
- External data: HI 3-sigma upper limit on atomic gas mass of 3×10^9 Msun  
  > "yields a 3-σ upper limit of 3×10 [9] M ⊙ on its atomic gas mass" (2. THE Z = 0.101 ABSORBER) [from Kanekar et al. 2001]
- External data: H2 column density ≈ (4.1 ± 0.5)×10^16 cm^-2 from UV absorption  
  > "H 2 column density ≈ (4.1 ± 0.5) × 10 [16] cm [−][2]" (2. THE Z = 0.101 ABSORBER) [from Muzahid et al. 2015]

## Processing

### Calibration

- pipeline or manual: standard procedures in CASA  
  > "The data were analyzed following standard procedures in the Common Astronomy Software Applications package" (3. ALMA OBSERVATIONS)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Uranus (amplitude); QSO J0439-4522 (gain)  
  > "QSO J0439−4522 and Uranus were used as gain and amplitude calibrators, respectively." (3. ALMA OBSERVATIONS)
- flux scale uncertainty: _not stated_
- self calibration: one round phase-only and one round phase+amplitude on the quasar continuum  
  > "allowing for self-calibration of the visibility data by performing one round of phase only and one round of phase and amplitude calibration" (3. ALMA OBSERVATIONS)

### Imaging

- task: clean  
  > "using Briggs weighting with a robust factor of 0.5 and the clean routine" (3. ALMA OBSERVATIONS)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "using Briggs weighting with a robust factor of 0.5" (3. ALMA OBSERVATIONS)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: cube velocity resolution 20 km/s  
  > "the final spectral cube covering the CO(1 0) line was made with a velocity resolution of 20 km s [−][1]" (3. ALMA OBSERVATIONS)
- final beam: 4.28" × 1.96", PA 73.85°  
  > "The synthesized beam size of the cube was 4.28 [′′] × 1.96 [′′], at a position angle of 73.85°." (3. ALMA OBSERVATIONS)
- final rms: 0.76 mJy/beam per 20 km/s channel; continuum 61 µJy  
  > "The final RMS noise of the data cube is 0.76 mJy beam [−][1] per 20 km s [−][1] channel." (3. ALMA OBSERVATIONS)

### Not stated but needed to reproduce (our reading)

- CASA version
- cell size and image size
- clean threshold, masks and iterations
- continuum subtraction and line-free channels
- self-calibration solution intervals
- MCMC priors, chain length, step sizes and likelihood
- on-source time, number of antennas, baselines
- how R_D and the 10 kpc disk radius were derived
- exact CO line luminosity conversion details
- how the SFR of 1.5 was adopted vs 0.53

## Analysis recipe

1. **Image continuum and self-calibrate**: Combine three continuum spws, detect quasar, self-calibrate (phase, then phase+amplitude)  
  > "The continuum image was made by combining the three continuum spectral windows, resulting in a root mean square (RMS) noise of 61 µJy." (3. ALMA OBSERVATIONS)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Make CO(1-0) cube and moment maps**: clean cube with Briggs robust 0.5, 20 km/s channels; first moment with immoments for >3σ emission  
  > "the first velocity moment of the CO(1−0) emission obtained by using the immoments function in CASA, and by only including emission detected at greater than 3σ significance" (4. RESULTS)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit disk kinematic model**: Infinitely thin exponential disk with flat rotation curve, convolved with beam and compared with data cube  
  > "We model the CO(1−0) emission from the z = 0.101 galaxy by an infinitely thin, exponential disk." (4.1)
   - software: custom MCMC code
   - parameter: free parameters: I0, R_D, inclination, PA, center (3 coords), v_max  
  > "The disk’s orientation is determined by its inclination (i) and the position angle of the major axis with respect to north (α)." (4.1)
   - assumption: zero intrinsic velocity dispersion, flat rotation curve  
  > "We note that the intrinsic velocity dispersion for this model is zero" (4.1)
   - fitting: Metropolis-Hastings MCMC; first 40% of chain discarded as burn-in  
  > "we remove the ‘burnin’ phase by discarding the first 40 % of the chain." (4.1)
   - validation: Five different starting points/runs for convergence; residuals inspected  
  > "We check for convergence by choosing five different starting points and running five different iterations." (4.1)
4. **Derive gas and dynamical masses**: M_mol = alpha_CO L'CO with helium correction; M_dyn ~ V^2 R/G  
  > "the dynamical mass can be roughly estimated as M dyn ∼ V [2] R/G" (4.3)
   - assumption: alpha_CO = 4.3 Msun (K km/s pc^2)^-1 (Bolatto et al. 2013); R ≈ 10 kpc  
  > "we will assume α CO = 4.3 M ⊙ (K km s [−][1] pc [2] ) [−][1], as recommended by Bolatto et al. (2013)" (4.3)
   - fitting: _not stated_
   - validation: _not stated_
5. **Compare emission with absorption**: Compare absorption component velocities to disk rotation curve and extrapolate surface density to sightline  
  > "we can calculate the rotational velocity needed to produce the velocity shifts seen in the absorption components." (4.2)
   - assumption: covering fraction <10%, representative H2 column, gas within 20 kpc sphere  
  > "(iii) only gas within a sphere of 20 kpc of the galaxy is considered." (4.4)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : data reduction, self-calibration, clean imaging, immoments  
  > "The data were analyzed following standard procedures in the Common Astronomy Software Applications package (CASA; McMullin et al. 2007)." (3. ALMA OBSERVATIONS)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(1-0) integrated flux | 1.46 | 0.07 | Jy km/s | 2 | We obtain an integrated CO(1−0) flux density of 1.46 ± 0.07 Jy km s [−][1] |
| CO line luminosity L'CO | 7.0e8 | 0.3e8 | K km/s pc^2 | 2 | L ′ CO = 7.0 ± 0.3 × 10 8 K km s −1 pc 2 |
| inclination | 67 | +6/-5 | degrees | 3 | we find an inclination angle of 67 [+6] −5 [degrees,] |
| position angle | 56 | ±5 | degrees | 3 | with a position angle of 56°± 5° |
| rotational velocity | 134 | +8/-11 | km/s | 3 | a rotational velocity of 134 [+8] −11 [km s] [−][1] |
| molecular gas mass | 4.2e9 | 0.2e9 | Msun | 4 | M mol = 4.2 ± 0.2 × 10 [9] M ⊙ |
| dynamical mass | ≳4e10 | not stated | Msun | 4 | yielding M dyn ≳ 4 × 10 [10] M ⊙ |
| gas consumption timescale | ≈2.8 | not stated | Gyr | 4 | yields a gas consumption timescale of ≈ 2.8 Gyr |
| molecular gas in absorbing component | ≲1e5 | not stated | Msun | 5 | the absorbing molecular component contains ≲ 10 [5] M ⊙ of gas |

## Qualitative findings

- CO emission coincides with the stellar disk and shows a rotating-disk velocity field  
  > "It is clear that the CO(1−0) emission arises from the disk of the z = 0.101 spiral galaxy." (Figure 1)

## Claim tuples

- H: Is CO(1-0) emitted by the galaxy associated with the absorber? | E: ALMA Band 3 cube | R: 12σ detection, flux 1.46 Jy km/s, aligned with optical disk | F: First CO emission detection from a quasar-selected galaxy; M_mol≈4.2e9 Msun | **supported**
- H: Does the strongest H2 absorption component arise from the molecular disk? | E: Compare absorption velocities and surface densities with disk model | R: Component 2 velocity inconsistent with the disk; extrapolated density far above that observed | F: Component 2 likely arises in the CGM | **supported**
- H: Is the molecular gas in dense clouds? | E: Gas consumption timescale from M_mol and SFR | R: ≈2.8 Gyr vs ≈1 Gyr typical | F: Molecular gas likely diffuse | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Component 2 could be CGM, outflow, or a faint dwarf; outflow speeds are very modest so it blurs with CGM  
  > "must instead be probing molecular gas in either the CGM, a strong metal-rich outflow, or a nearby faint dwarf galaxy" (4.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Higher-resolution data would be needed to confirm absence of substructure; dynamical mass is a lower limit  
  > "although higher- resolution data would be required to confirm this" (4.1)
- Caveat (inferred, ours): Galactic alpha_CO adopted despite high metallicity; mass uncertain
- Caveat (inferred, ours): Simple flat thin-disk model with zero dispersion and 2" resolution
- Caveat (inferred, ours): Beam-smearing and inclination degeneracy; MCMC details unspecified
- Caveat (inferred, ours): SFR is uncorrected for extinction and varies between estimates

## Reproducibility

- Data public (paper): ALMA project cited in acknowledgments  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.01178.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version and exact imaging parameters
- Missing: MCMC code and priors
- Missing: line-free channels and moment settings
- Data volume (inferred): ~10-20 GB raw
- Score (inferred): 3/5, Single compact-array dataset and simple recipe, but key imaging and MCMC details missing and custom code unreleased.
- Rediscovery candidate: yes, Data are public, the recipe is short, and the results (flux, M_mol, v_rot) are numeric, though the MCMC model needs reimplementation.

## Links

- Companion: Dutta et al. 2015 (Absorber metallicity, SFR and photoionization modeling)
- Related: ALMA program on molecular gas in high-metallicity absorption-selected galaxies

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
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 35,
  "rate": 0.5
 },
 "evidence_ok": true
}
```
