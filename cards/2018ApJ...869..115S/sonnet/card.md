# Dust Polarization toward Embedded Protostars in Ophiuchus with ALMA. II. IRAS 16293-2422

`2018ApJ...869..115S` | The Astrophysical Journal 2018 | first author: Sadavoy, Sarah I. | arXiv: 1811.03104 | DOI: 10.3847/1538-4357/aaef81

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: What is the dust polarization and inferred magnetic field structure across IRAS 16293A, IRAS 16293B and the bridge between them, and what does it imply for the bridge and for grain growth in IRAS 16293B?  
  > "These observations spatially resolve the dust polarization across the two protostellar sources and toward the filamentary structures between them." (abstract)
- Target **IRAS 16293-2422 (IRAS 16293A and B)**: coordinates IRAS 16293A 16:32:22.873 -24:28:36.63; IRAS 16293B 16:32:22.613 -24:28:32.61 (J2000)  
  > "IRAS 16293A | 16:32:22.873 | -24:28:36.63" (Table 1); "scaled to our assumed distance of 140 pc (cite: Jacobsen18)" (5.1.4 Toy Model); z/distance 140 pc  
  > "IRAS 16293A | 16:32:22.873 | -24:28:36.63" (Table 1); "scaled to our assumed distance of 140 pc (cite: Jacobsen18)" (5.1.4 Toy Model); distance from Jacobsen18 (assumed)  
  > "IRAS 16293A | 16:32:22.873 | -24:28:36.63" (Table 1); "scaled to our assumed distance of 140 pc (cite: Jacobsen18)" (5.1.4 Toy Model)

## Data provenance

- ALMA projects: 2015.1.01112.S
- bands: Band 6 (1.3 mm, 233 GHz), full polarization  
  > "IRAS 16293 was observed in full polarization in Band 6 (1.3 mm, 233 GHz)" (2 Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.28'' x 0.23'' (≈35 au)  
  > "The map resolution is $0.28\ensuremath{''} \times 0.23\ensuremath{''}$ ($\approx 35$ au)" (2 Observations)
- max recoverable scale: 2.6'' (360 au)  
  > "the maximum recoverable scale is $2.6$$''$ (360 au)" (2 Observations)
- sensitivity: 280 μJy/beam Stokes I; 25 μJy/beam Stokes Q, U, V  
  > "The final map sensitivities are 280 $\mu$Jy beam$^{-1}$ for Stokes I and 25 $\mu$Jy beam$^{-1}$ for Stokes Q, U, and V" (2 Observations)
- time on source: ≈7 minutes per pointing, two pointings  
  > "The total time on each pointing was $\approx 7$ minutes." (2 Observations)
- observing dates: 2017 May 20, July 11, and July 13  
  > "on 2017 May 20, July 11, and July 13" (2 Observations)
- pi or archival as stated: Part of Cycle 3 survey; details in Sadavoy18  
  > "Details of these observations are discussed in (cite: Sadavoy18)." (2 Observations)
- Other facility **VLA 6.9 mm polarization**: 6.9 mm polarization of IRAS 16293B from Liu18, compared with ALMA  
  > "(cite: Liu18) presented 6.9 mm polarization observations of IRAS 16293B from the Karl G. Jansky Very Large Array (VLA)" (5.2 Polarization of IRAS 16293B)
- Other facility **SMA 878 μm polarization**: Earlier lower-resolution polarization maps (Rao09, Rao14)  
  > "(cite: Rao14) observed IRAS 16293 in 878 $\mu$m dust polarization with the SMA" (5.2 Polarization of IRAS 16293B)
- External data: Velocity dispersion 0.75 km/s from C17O (3-2), used for DCF  
  > "we adopt $\sigma_v = 0.75$ km s$^{-1}$ from C$^{17}$O (3-2) line emission (M. van der Wiel 2018, private communication)" (4.3 Field Strength) [from van der Wiel 2018 (private communication)]
- External data: Dust temperature 30 K  
  > "We assume a temperature of 30 K (cite: Jacobsen18)" (4.3 Field Strength) [from (cite: Jacobsen18)]
- External data: Dust opacity 0.01112 cm2/g at 233 GHz  
  > "a dust opacity at 233 GHz of 0.01112 cm$^2$ g$^{-1}$ at 1.3 mm following the theoretical measurements from (cite: Ossenkopf94)" (4.3 Field Strength) [from (cite: Ossenkopf94)]
- External data: 6.9 mm VLA polarization vectors of IRAS 16293B  
  > "with the 6.9 mm VLA e-vectors (green) form (cite: Liu18)" (5.2 Polarization of IRAS 16293B) [from (cite: Liu18)]
- Simulation/model as data: Monte Carlo sample of 100,000 random 3-D vectors projected to 2-D to give expected angle-difference profiles  
  > "we generate a large Monte Carlo sample of 100,000 randomly defined 3-D vectors to represent the field orientation." (4.2 Field Orientation)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10%  
  > "with an absolute flux calibration uncertainty of 10%" (2 Observations)
- self calibration: Two rounds of phase-only self-cal (solint inf to 30 s), then one phase+amplitude round with infinite solint  
  > "we first applied two rounds of phase-only self-calibration with decreasing solution intervals from infinity (full schedule block) to 30 seconds" (2 Observations)

### Imaging

- task: CASA clean; interactive for Stokes I, noninteractive for Q, U, V; two fields mosaicked  
  > "For the Stokes I observations, we ran `clean` in interactive mode with `multiscale` and user-defined masks, whereas for the Stokes Q, U, and V observations, we used noninteractive `clean`." (2 Observations)
- deconvolver: _not stated_
- weighting robust: robust = 0.5  
  > "we use a robust weighting of 0.5, a taper of 0.1$''$" (2 Observations)
- uv taper: 0.1''  
  > "a taper of 0.1$''$" (2 Observations)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: 1, 2.5, and 5 beams  
  > "the `multiscale` option with 1, 2.5, and 5 beams" (2 Observations)
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.28'' x 0.23''  
  > "$0.28\ensuremath{''} \times 0.23\ensuremath{''}$" (2 Observations)
- final rms: 280 μJy/beam (I); 25 μJy/beam (Q,U,V)  
  > "280 $\mu$Jy beam$^{-1}$ for Stokes I and 25 $\mu$Jy beam$^{-1}$ for Stokes Q, U, and V" (2 Observations)

### Inherited from earlier work

- Cleaning and self-calibration approach  
  > "Following the same approach as outlined in (cite: Sadavoy18), each field was cleaned interactively" (2 Observations) [from (cite: Sadavoy18)]
- Observation details  
  > "Details of these observations are discussed in (cite: Sadavoy18)." (2 Observations) [from (cite: Sadavoy18)]
- Polarization debiasing method  
  > "We use a basic maximum likelihood characterization to debias the polarized intensities (cite: SimmonsStewart85; Vaillancourt06)" (3.2 Polarization Results) [from (cite: SimmonsStewart85; Vaillancourt06)]
- Angle uncertainty formula  
  > "for the position angles (cite: Hull14)" (3.2 Polarization Results) [from (cite: Hull14)]
- DCF scaling Q = 0.5  
  > "We adopt $Q = 0.5$ (cite: Ostriker01)." (4.3 Field Strength) [from (cite: Ostriker01)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and spectral windows used for continuum
- CASA version
- Flux, bandpass, and polarization calibrators
- Number of clean iterations and thresholds, mask definitions, cell and image size
- Exact FilFinder2D parameters
- How the 85 slices and the angle dispersion were computed in detail
- Exact Gaussian fit procedure for sigma_theta

## Analysis recipe

1. **Self-calibrate and image Stokes I, Q, U, V mosaic**: Self-calibration then CASA clean of both fields mosaicked, multiscale  
  > "For the final map, we performed a deep clean with both fields mosaicked together." (2 Observations)
   - software: CASA
   - parameter: robust 0.5, taper 0.1'', multiscale 1, 2.5, 5 beams  
  > "we use a robust weighting of 0.5, a taper of 0.1$''$" (2 Observations)
   - fitting: _not stated_
   - validation: Checked self-cal solutions and amplitudes consistency; individual fields compared with mosaic  
  > "We note that the individual Stokes I, Q, and U maps from each field are identical to the the final mosaic observations" (2 Observations)
2. **Derive debiased polarization intensity, angle, and fraction**: P = sqrt(Q²+U²−σ²); theta = 0.5 atan(U/Q); P_F = P/I; b-vectors by 90° rotation  
  > "The polarization intensity is determined from $\mbox{$\mathcal{P}_I$}= \sqrt{Q^2 + U^2}$." (3.2 Polarization Results)
   - parameter: vectors shown for I>3σ and P>4σ; black for >5σ  
  > "We show the e-vectors and b-vectors for regions with $I > 3\ \sigma_I$ and $\mbox{$\mathcal{P}_I$}> 4\ \mbox{$\sigma_{\mathcal{P}I}$}$" (3.2 Polarization Results)
   - assumption: σ_PI ≈ σ_Q ≈ σ_U; 0.1% instrumental polarization uncertainty  
  > "We adopt a polarization fraction uncertainty of 0.1% for the instrument polarization." (3.2 Polarization Results)
   - fitting: _not stated_
   - validation: Stokes V not used because two fields gave inconsistent values  
  > "we do not use the Stokes V data in this study." (3.2 Polarization Results)
3. **Identify filaments and measure field-filament angle**: FilFinder2D skeleton with user-defined mask; angle difference between skeleton slope and b-vectors; Bridge fitted with y=sqrt(x)  
  > "We use the filament-finding algorithm FilFinder2D (cite: KochRosolowsky15) to produce a skeleton diagram of all filamentary structures in IRAS 16293." (4.1 Filamentary Structure Properties)
   - software: FilFinder2D
   - parameter: mask I>5σ, cuts I<9σ and I<12σ in places  
  > "The user-defined mask is constructed using a mask of $I > 5\ \sigma_I$" (4.1 Filamentary Structure Properties)
   - fitting: y = sqrt(x) curve fitted to southern Bridge skeleton  
  > "we fit a simple $y = \sqrt{x}$ curve to the skeleton." (4.1 Filamentary Structure Properties)
   - validation: Skeleton compared by eye with Stokes I; thresholds chosen so skeleton traces curvature  
  > "By eye, the skeleton outline has good agreement with the Stokes I emission." (4.1 Filamentary Structure Properties)
4. **Compare angle distributions to Monte Carlo field models**: Cumulative angle difference compared with projected random 3-D vectors in 0-20° to 0-90° subsamples; KS and AD tests  
  > "we conduct the two-sample Kolmogorov-Smirnov (KS) test (cite: Kolmogorov33; Smirnov48; Massey51) and the Anderson-Darling (AD) test" (4.2 Field Orientation)
   - parameter: 100,000 Monte Carlo vectors  
  > "we generate a large Monte Carlo sample of 100,000 randomly defined 3-D vectors" (4.2 Field Orientation)
   - assumption: Filaments lie in the plane of the sky  
  > "we assume that the filamentary structures are all in the plane-of-the-sky" (4.2 Field Orientation)
   - fitting: _not stated_
   - validation: Also tested one data point per beam  
  > "even if we undersample the observations by taking only one data point per beam" (4.2 Field Orientation)
5. **Estimate Bridge mass, density, and field strength**: Modified blackbody mass from average of 85 slices; DCF B = Q sqrt(4πρ) σv/σθ  
  > "We convert this thermal dust emission to mass and column density following a modified blackbody function" (4.3 Field Strength)
   - parameter: σv = 0.75 km/s; σθ = 5-17°; length 3'' (420 au); FWHM 0.96'' (134 au); median flux density 3.4 mJy/beam  
  > "The average slice has a median flux density of 3.4 mJy beam$^{-1}$ and a FWHM of $0.96$$''$ (134 au)." (4.3 Field Strength)
   - assumption: T = 30 K, kappa = 0.01112 cm2/g, gas-to-dust 100, mu = 2.8, cylinder geometry, Q=0.5  
  > "a gas to dust ratio of 100" (4.3 Field Strength)
   - fitting: Gaussian fit to peak of angle distribution for σθ ≈ 5°; standard deviation of full distribution for 17°  
  > "If we exclude these twisted vectors and fit a Gaussian to the peak distribution, we find $\sigma_{\theta} \approx 5$." (4.3 Field Strength)
   - validation: _not stated_
6. **Toy gravitational-flow model of the Bridge**: Straight negligible-mass cylinder of length 2L=740 au with equal-mass stars at the ends; compute flow velocity, Alfvén speed, and flow time  
  > "We model the Bridge by a straight cylinder of length $2L = 740$ au and negligible mass." (5.1.4 Toy Model)
   - parameter: star masses 0.1-1.0 Msun  
  > "we can expect flow rates of $v_{flow} = 0.5-1.5$ km s$^{-1}$ for star masses between 0.1 and 1.0 M$_{\odot}$." (5.1.4 Toy Model)
   - assumption: Stars have equal mass; Bridge in the plane of the sky; distance 140 pc  
  > "we assume that the stars have the same mass, $M$ and the Bridge is in the plane of the sky." (5.1.4 Toy Model)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Cleaning, self-calibration, Gaussian position fitting  
  > "from fitting Gaussian functions to each object in CASA" (3.1 Continuum Results)
- **FilFinder2D** : Filament skeleton identification  
  > "We use the filament-finding algorithm FilFinder2D (cite: KochRosolowsky15)" (4.1 Filamentary Structure Properties)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Stokes I rms sensitivity | 280 | not stated | μJy/beam | 1 | 280 $\mu$Jy beam$^{-1}$ for Stokes I |
| Stokes Q/U/V rms sensitivity | 25 | not stated | μJy/beam | 1 | 25 $\mu$Jy beam$^{-1}$ for Stokes Q, U, and V |
| Bridge total flux | 0.13 | not stated | Jy | 5 | we estimate a total flux of 0.13 Jy |
| Bridge mass | 0.026 | not stated | Msun | 5 | we find a total mass of 0.026 M$_{\odot}$ for the Bridge |
| Bridge column density | 1.1e24 | not stated | cm^-2 | 5 | a typical column density of $1.1 \times 10^{24}$ cm$^{-2}$ |
| Bridge density | 5.6e8 | not stated | cm^-3 | 5 | a typical density of $5.6 \times 10^{8}$ cm$^{-3}$ |
| Bridge magnetic field strength (DCF) | 23-78 | range from σθ = 5-17° | mG | 5 | we find a magnetic field strength of $B = 23-78$ mG |
| Alfvén speed | 1.2-4 | not stated | km/s | 6 | we find $v_A = 1.2-4$ km s$^{-1}$ |
| Toy-model flow speed | 0.5-1.5 | not stated | km/s | 6 | $v_{flow} = 0.5-1.5$ km s$^{-1}$ for star masses between 0.1 and 1.0 M$_{\odot}$ |
| Bridge flow time scale | ~1e3 | not stated | yr | 6 | For our toy cylinder, $\tau_{flow} \sim 10^3$ yr. |
| Bridge angular dispersion σθ | 5 (Gaussian peak) to 17 (full distribution) | not stated | deg | 5 | we find $\sigma_{\theta} = 17$ |

## Qualitative findings

- The inferred field is parallel to the Bridge, A-Streamer and B-Streamer, mostly within 30° of the filaments  
  > "the magnetic field morphology is primarily oriented within 30 of the filamentary structures in IRAS 16293" (4.2 Field Orientation)
- Depolarization zone passes through the Bridge near the midpoint  
  > "This depolarization zone spans roughly one beam and passes through the Bridge near the center point between the two stars." (3.3 Inferred Magnetic Field Morphology)
- IRAS 16293B polarization morphology resembles dust self-scattering in a face-on disk, matching 6.9 mm  
  > "Qualitatively, the polarization signature toward IRAS 16293B is reminiscent of dust self-scattering in a face-on disk" (5.2 Polarization of IRAS 16293B)

## Claim tuples

- H: Is the field in the filamentary structures parallel or perpendicular to them? | E: FilFinder2D skeletons compared with b-vector angles; Monte Carlo, KS and AD tests | R: B-Streamer consistent with <30° distribution (p≈0.4-0.5); random and perpendicular rejected (p≪1e-10); A-Streamer and Bridge more complex | F: Field is mainly parallel to the Bridge and streamers | **supported**
- H: How strong is the field in the Bridge? | E: DCF method with measured density, σv and σθ | R: B = 23-78 mG | F: Field strength estimated, but density is highly uncertain | **partially**
- H: Can the magnetic field regulate gas flow in the Bridge, and is the Bridge long-lived? | E: Toy model with stars dominating potential | R: Flow ~1 km/s comparable to Alfvén speed; depletion time ~1e3 yr | F: Field may regulate flow; Bridge either accretes new material or is transient | **partially**
- H: What produces the polarization toward IRAS 16293B? | E: Compare 1.3 mm ALMA with 6.9 mm VLA and 878 μm SMA polarization | R: Consistent patterns across wavelengths, azimuthal at periphery and uniform at center | F: Qualitatively consistent with dust self-scattering, implying grains of ~200-2000 μm; models still needed | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Mosaicking two fields is safe because the emission lies within the inner third of the primary beams  
  > "it is safe to mosaic these data (ALMA Helpdesk #12418, private communication)" (2 Observations)
- Alternative: Depolarization attributed to grain property changes was disfavored; alternatives are disordered field or unresolved structure  
  > "Therefore, we see no evidence that the depolarization zones are due to changes in the dust grains themselves." (5.1.3 Depolarization)
- How they decided it was enough: _not stated_
- Limitation (authors): Lack of short baselines limits recovery of extended field structure, especially around IRAS 16293B  
  > "First, we lack observations on shorter baselines to trace fully the magnetic field morphology at large angular extents." (3.3 Inferred Magnetic Field Morphology)
- Limitation (authors): Stokes V unusable; Stokes I maps are dynamic range limited  
  > "Both the individual and mosaicked Stokes I maps are dynamic range limited because IRAS 16293 is so bright" (2 Observations)
- Caveat (inferred, ours): Bridge density and mass depend strongly on assumed T and opacity, and propagate into B and v_A
- Caveat (inferred, ours): Toy model assumes equal stellar masses, plane-of-sky geometry and a straight massless cylinder
- Caveat (inferred, ours): Self-scattering interpretation is qualitative; no scattering model was fit
- Caveat (inferred, ours): DCF sigma_v comes from a private communication and the velocity dispersion is not measured here
- Caveat (inferred, ours): Nyquist-sampled angles are not independent, which affects the KS/AD p-values

## Reproducibility

- Data public (paper): Data cited as ADS/JAO.ALMA#2015.1.01112.S  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.01112.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Calibrator, CASA version and flagging details
- Missing: Clean masks, thresholds and image size
- Missing: FilFinder2D parameter settings
- Missing: C17O velocity dispersion (private communication)
- Data volume (inferred): ~50-100 GB raw for three execution blocks (estimate)
- Score (inferred): 5/5, Imaging parameters and analysis are largely described, but calibration, software versions, masks, FilFinder parameters and the C17O input are missing.
- Rediscovery candidate: no, Data are likely public, but key inputs such as sigma_v are private communication and several processing details are unspecified.

## Links

- Method: (cite: Sadavoy18) (Observation details and the cleaning/self-calibration approach)
- Method: (cite: KochRosolowsky15) (FilFinder algorithm)
- Method: (cite: Vaillancourt06) (Polarization debiasing)
- Companion: (cite: Sadavoy18) (Paper I in the series (VLA 1623))
- Companion: (cite: Jacobsen18) (Radiative transfer model of the bridge)
- Companion: (cite: Liu18) (VLA 6.9 mm polarization of IRAS 16293B)
- Related: Cycle 3 ALMA polarization survey of embedded protostars in Ophiuchus (2015.1.01112.S)

## Checks

```json
{
 "quotes": 83,
 "quotes_ok": 83,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 91,
  "stated": 63,
  "rate": 0.692
 },
 "evidence_ok": true
}
```
