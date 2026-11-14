# Confirming the Explosive Outflow in G5.89 with ALMA

`2020ApJ...902L..47Z` | The Astrophysical Journal Letters 2020 | first author: Zapata, Luis A. | arXiv: 2010.13835 | DOI: 10.3847/2041-8213/abbd3f

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Is the molecular outflow in G5.89-0.39 an explosive outflow (Hubble-like filaments pointing to a common origin), similar to Orion BN/KL and DR21?  
  > "Here, we confim a similar explosive outflow associated with the UCH$_{\rm II}$ region G5.89$-$0.39 that indicates that this phenomenon is not unique to Orion or DR21." (abstract)
- Target **G5.89-0.39 (W28A2)**: coordinates RA 18h00m30.388s, Dec -24d04'00.20" (J2000, pointing)  
  > "G5.89$-$0.39 or W28A2 is a massive star forming region located at a distance of 2.99$^{+0.19}_{-0.17}$ kpc (cite: sat2014)." (Introduction); "$\alpha_{J2000.0}$ = $18^{\rm h}00^{\rm m}30\mbox{$^{\rm s}\mskip-7.6mu.\,$}388$, and $\delta_{J2000.0}$ = $-24^{\circ}04'00\mbox{$''\mskip-7.6mu.\,$}20$" (Observations); z/distance 2.99 (+0.19/-0.17) kpc  
  > "G5.89$-$0.39 or W28A2 is a massive star forming region located at a distance of 2.99$^{+0.19}_{-0.17}$ kpc (cite: sat2014)." (Introduction); "$\alpha_{J2000.0}$ = $18^{\rm h}00^{\rm m}30\mbox{$^{\rm s}\mskip-7.6mu.\,$}388$, and $\delta_{J2000.0}$ = $-24^{\circ}04'00\mbox{$''\mskip-7.6mu.\,$}20$" (Observations); distance from Sato et al. 2014 (cite: sat2014)  
  > "G5.89$-$0.39 or W28A2 is a massive star forming region located at a distance of 2.99$^{+0.19}_{-0.17}$ kpc (cite: sat2014)." (Introduction); "$\alpha_{J2000.0}$ = $18^{\rm h}00^{\rm m}30\mbox{$^{\rm s}\mskip-7.6mu.\,$}388$, and $\delta_{J2000.0}$ = $-24^{\circ}04'00\mbox{$''\mskip-7.6mu.\,$}20$" (Observations)

## Data provenance

- ALMA projects: 2018.1.00513.S
- bands: Band 6 (1.3 mm)  
  > "As the primary beam at this frequency (Band 6) has a Full Width Half Maximum (FWHM) of about 25$''$" (Observations)
- frequencies and spectral setup: native channel 488.3 kHz (~0.61 km/s), smoothed to 2.44 km/s  
  > "we smoothed the spacing channel to 2.44 km s$^{-1}$" (Observations)
- continuum bandwidth: about 3.75 GHz from nine spectral windows  
  > "The total bandwidth for the continuum is about 3.75 GHz." (Observations)
- arrays: 12 m antennas, 49 and 45 antennas in two sessions  
  > "one with 49 antennas and the other with 45 antennas, both using antennas with diameters of 12 m" (Observations)
- configurations: _not stated_
- baselines: 38 to 3600 m (29-2769 kλ)  
  > "yielding baselines with projected lengths from 38 to 3600 m (29–2769 k$\lambda$)" (Observations)
- angular resolution: 0.12"x0.09" continuum; 0.13"x0.09" lines  
  > "The line image *rms*-noise is 0.75 mJy beam$^{-1}$ km s$^{-1}$ at an angular resolution of 0.13$''$ $\times$ 0.09$''$ with a PA of $-$73$^\circ$." (Observations)
- max recoverable scale: 2.5"  
  > "The maximum recoverable scale for these observations is 2.5$''$." (Observations)
- sensitivity: continuum rms 0.2 mJy/beam; line rms 0.75 mJy/beam km/s  
  > "We obtained an image *rms*-noise for the 1.3 mm continuum of 0.2 mJy Beam$^{-1}$" (Observations)
- time on source: 78 min  
  > "The total integration time on source that includes the two sessions is 78 min." (Observations)
- observing dates: 2019 September 5  
  > "carried out in 2019 September 5th as part of the Cycle 6 program" (Observations)
- pi or archival as stated: Cycle 6 program, PI Paul Ho  
  > "as part of the Cycle 6 program 2018.1.00513.S (PI: Paul Ho)" (Observations)
- Line: SiO 5-4 (217.105 GHz)
- Line: CO 2-1 (230.538 GHz)
- Other facility **SMA**: Earlier observations of six explosive filaments, used for comparison  
  > "using Submillimeter Array (SMA) observations, detected the presence of six explosive filaments pointing directly to the center of the UCH$_{\rm II}$ region" (Introduction)
- External data: Distance 2.99 kpc  
  > "located at a distance of 2.99$^{+0.19}_{-0.17}$ kpc (cite: sat2014)" (Introduction) [from (cite: sat2014)]
- External data: UCHII dynamical age 600 yr  
  > "with a dynamical age of 600$^{+250}_{-125}$ years, estimated from its expansion rate (cite: aco1998)" (Introduction) [from (cite: aco1998)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 5.6  
  > "the Common Astronomy Software Applications package, Version 5.6" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Phase self-calibration using continuum as model, applied to lines; ~factor 2 rms improvement  
  > "Phase self-calibration was done using the continuum emission as a model and then we applied the solutions to the line emission." (Observations)

### Imaging

- task: TCLEAN  
  > "We imaged the *uv*-data using the task TCLEAN." (Observations)
- deconvolver: _not stated_
- weighting robust: Robust = 0.5 for continuum and lines  
  > "We set the `Robust` parameter of TCLEAN equals to 0.5 for the continuum and line emissions." (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: channels smoothed to 2.44 km/s  
  > "we smoothed the spacing channel to 2.44 km s$^{-1}$" (Observations)
- final beam: 0.12"x0.09" PA -75 deg (continuum); 0.13"x0.09" PA -73 deg (lines)  
  > "0.12$''$ $\times$ 0.09$''$ with a PA of $-$75$^\circ$" (Observations)
- final rms: 0.2 mJy/beam continuum; 0.75 mJy/beam km/s line  
  > "We obtained an image *rms*-noise for the 1.3 mm continuum of 0.2 mJy Beam$^{-1}$" (Observations)

### Not stated but needed to reproduce (our reading)

- Line-free channels used for continuum
- Self-calibration solution intervals and number of iterations
- Image size, cell size, deconvolver, masks and clean threshold
- Filament identification criteria and fitting procedure for the Hubble law
- Which three outlier filaments were removed
- Statistical test details
- Calibrator roles per source and flux scale uncertainty

## Analysis recipe

1. **Image continuum and line cubes**: TCLEAN imaging, robust 0.5, channels smoothed to 2.44 km/s, after phase self-cal  
  > "We set the `Robust` parameter of TCLEAN equals to 0.5 for the continuum and line emissions." (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared rms to theoretical noise  
  > "The ALMA theoretical rms noise for this configuration, integration time, bandwidth (channel spacing), and frequency is about 0.7 mJy beam$^{-1}$" (Observations)
2. **Identify expanding CO filaments and map moments**: CO moment one map excluding -20 to +40 km/s; filaments traced as sequences of condensations across channels  
  > "Each filament marks the position of one sequence of molecular condensations mapped at different spectral channel velocities" (Results and Discussion)
   - software: CASA, KARMA
   - parameter: velocity range excluded -20 to +40 km/s  
  > "This thermal emission was especially selected from outside the velocity range from $-$20 to $+$40 km s$^{-1}$" (Results and Discussion)
   - fitting: _not stated_
   - validation: Comparison with earlier SMA filaments  
  > "These filaments coincide very well with some filamentary structures already traced by the moment one map and the six explosive filaments reported in (cite: zap2019)." (Results and Discussion)
3. **Test Hubble law and common origin**: Linear fits of radial velocity and distance per filament; mean intercepts with 95% CI and p-values after removing three outliers  
  > "Removing three outlier trajectories (or filaments), the mean of the projected distance intercepts is $\bar{x}=-0.01''$" (Results and Discussion)
   - fitting: Linear trajectories; test of mu=0 for intercepts  
  > "the hypothesis of $\mu=0$ cannot be rejected for both cases" (Results and Discussion)
   - validation: _not stated_
4. **Kinematic age and event rate**: Age from max projected distance/max velocity; rate from three events per 10,000 yr within 2.99 kpc  
  > "taking maximum radial velocity of about 160 km s$^{-1}$ and the maximum projected distance of 12$''$, we obtained a kinematic age of 1000 yrs" (Results and Discussion)
   - assumption: Distance 2.99 kpc  
  > "located at a distance of 2.99$^{+0.19}_{-0.17}$ kpc (cite: sat2014)" (Introduction)
   - fitting: _not stated_
   - validation: Age similar to fossil outflow of Klaassen et al. 2006 and Feldt star travel time  
  > "a similar value for the fossil outflow reported by (cite: kla2006) and the estimated time to reach the present position of the Feldt’s star" (Results and Discussion)

## Software

- **CASA** 5.6: Calibration, imaging, analysis  
  > "The data were calibrated, imaged, and analyzed using CASA (cite: mac2007), the Common Astronomy Software Applications package, Version 5.6." (Observations)
- **KARMA** : Listed in software section; use not described  
  > "CASA (cite: mac2007), KARMA (cite: goo1996)" (Software)
- **Astropy** : Python routines to image the data  
  > "We also used some routines in Python to image the data (cite: ast2013)." (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum rms | 0.2 | not stated | mJy/beam | 1 | 1.3 mm continuum of 0.2 mJy Beam$^{-1}$ |
| Number of expanding CO filaments | 34 (17 blueshifted, 17 redshifted) | not stated | dimensionless | 2 | We find 17 blueshifted, and 17 redshifted expanding filaments emerging from G5.89$-$0.39. |
| CO velocity extent | -170 to +130 | not stated | km/s | 2 | The CO(2$-$1) thermal emission is found from $-$170 up to $+$130 km s$^{-1}$. |
| Mean distance intercept | -0.01 | 95% CI (-0.75, 0.73) | arcsec | 3 | IC$_\mu$=($-$0.75$''$,0.73$''$) |
| Mean velocity intercept | +1.26 | 95% CI (-7.25, 9.77) | km/s | 3 | is $\bar{x}=$+$1.26$ km s$^{-1}$ |
| Kinematic age | 1000 | not stated | yr | 4 | we obtained a kinematic age of 1000 yrs |
| Explosion rate | one per ~130 | not stated | yr | 4 | we obtain a rate of about one explosion every 130 years |

## Qualitative findings

- SiO filaments are nearly isotropic and point back to the UCHII center; the previously reported NW bipolarity is lost  
  > "The northwest bipolarity reported for this SiO outflow (cite: aco1998; soll2004) is totally lost in these new ALMA images" (Results and Discussion)

## Claim tuples

- H: The G5.89 outflow is explosive | E: ALMA CO(2-1) and SiO(5-4) imaging, filament kinematics | R: 34 filaments with Hubble-law velocities converging on a common origin | F: Explosive outflow of age ~1000 yr | **supported**
- H: Explosive events are common enough to matter for massive star formation | E: Crude rate estimate from three known cases | R: One event per ~130 yr | F: Rate close to supernova rate | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Continuum rms is ten times the theoretical value, due to bright UCHII emission or missing short spacings  
  > "An alternative possibility is the lack of short spacing information on the continuum structure." (Observations)
- Caveat (inferred, ours): Rate estimate rests on three objects and an ad hoc volume
- Caveat (inferred, ours): Filament identification is subjective and uses a single epoch
- Caveat (inferred, ours): Energetics (1e46-49 erg) not derived in the text
- Caveat (inferred, ours): Abstract says ~100 yr, text says 130 yr

## Reproducibility

- Data public (paper): Archival project 2018.1.00513.S cited; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.00513.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Filament selection and fitting details
- Missing: Imaging parameters beyond robust
- Missing: Energy calculation method
- Data volume (inferred): ~50-100 GB
- Score (inferred): 3/5, Data identified and basic imaging given, but filament analysis and energetics are underspecified.
- Rediscovery candidate: no, Filament identification is subjective and the recipe is incomplete.

## Links

- Companion: Zapata et al. 2019 (cite: zap2019) (Earlier SMA detection of six explosive filaments)

## Checks

```json
{
 "quotes": 57,
 "quotes_ok": 57,
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
  "facts": 65,
  "stated": 41,
  "rate": 0.631
 },
 "evidence_ok": true
}
```
