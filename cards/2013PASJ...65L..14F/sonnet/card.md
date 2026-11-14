# Local Enhancement of the Surface Density in the Protoplanetary Ring Surrounding HD 142527

`2013PASJ...65L..14F` | Publications of the Astronomical Society of Japan 2013 | first author: Fukagawa, Misato | arXiv: 1309.7400 | DOI: 10.1093/pasj/65.6.L14

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: What are the surface density and gravitational stability of the strongly asymmetric outer ring of HD 142527, using continuum and 13CO/C18O 3-2 data to constrain grain temperature?  
  > "To evaluate the surface density in this region, the grain temperature needs to be constrained and was estimated from the optically thick $^{13}$CO $J =$ 3–2 emission." (abstract)
- Target **HD 142527**: coordinates _not stated_; z/distance 140 pc  
  > "The distance is assumed to be 140 pc in this paper considering the association to Sco OB2." (1 Introduction); distance from assumed from association to Sco OB2  
  > "The distance is assumed to be 140 pc in this paper considering the association to Sco OB2." (1 Introduction)

## Data provenance

- ALMA projects: 2011.0.00318.S
- bands: Band 7  
  > "HD 142527 was observed with ALMA in Band 7 using 20–26 12-m antennas in the Extended array configuration in Cycle 0." (2 Observations and Data Reduction)
- frequencies and spectral setup: 4 spectral windows, 469 MHz each, 3840 channels, 0.122 MHz (0.11 km/s) spacing; centers 330.588, 329.331, 342.883, 342.400 GHz  
  > "The central frequencies for these windows are 330.588, 329.331, 342.883, and 342.400 GHz, respectively" (2 Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: 20–26 12-m antennas, Extended configuration, Cycle 0  
  > "using 20–26 12-m antennas in the Extended array configuration in Cycle 0" (2 Observations and Data Reduction)
- configurations: _not stated_
- baselines: 20 m to 380 m  
  > "The maximum and minimum baselines were 380 m and 20 m, respectively" (2 Observations and Data Reduction)
- angular resolution: continuum 0.39"x0.34" PA 57; lines 0.43"x0.37" PA 50  
  > "The synthesized beam size for the continuum is $0.39\ensuremath{''} \times 0.34\ensuremath{''}$ with a position angle (PA) of 57$\ensuremath{^\circ}$ for the major axis" (2 Observations and Data Reduction)
- max recoverable scale: 10 arcsec  
  > "the latter corresponded to the largest angular scale of the detectable component of $10\ensuremath{''}$." (2 Observations and Data Reduction)
- sensitivity: continuum rms 0.19 mJy/beam; 13CO 12 and C18O 15 mJy/beam per 0.11 km/s channel  
  > "The rms noise is 0.19 mJy beam$^{-1}$ for the continuum whereas it is 12 and 15 mJy beam$^{-1}$ in the 0.11 km s$^{-1}$ wide channels" (2 Observations and Data Reduction)
- time on source: _not stated_
- observing dates: June to August 2012, four scheduling blocks  
  > "The observations reported in this letter consisted of four scheduling blocks over the period from June to August 2012." (2 Observations and Data Reduction)
- pi or archival as stated: _not stated_
- Line: 13CO J=3-2 (not stated)
- Line: C18O J=3-2 (not stated)
- External data: Stellar mass 2.2±0.3 Msun  
  > "whereas the stellar mass is fixed in the range of $2.2 \pm 0.3$ $M_{\ensuremath{\odot}}$ (V11)." (3.2.1 Integrated Intensity and Gas Kinematics) [from Verhoeff et al. 2011 (cite: ver11)]
- External data: Abundance ratio X(C13O)/X(C18O) ~ 7  
  > "an abundance ratio of X(C$^{13}$O)/X(C$^{18}$O) $\sim$ 7 (cite: qi11)" (3.2.2 Temperature Estimate) [from Qi et al. 2011 (cite: qi11)]

## Processing

### Calibration

- pipeline or manual: CASA flagging then bandpass, gain, flux scaling calibration; manual/pipeline not specified  
  > "After flagging aberrant data and applying calibrations for the bandpass, gain, and flux scaling, the corrected visibilities were imaged" (2 Observations and Data Reduction)
- casa version: CASA 3.4  
  > "Common Astronomy Software Applications (CASA) package, version 3.4." (2 Observations and Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan and Neptune  
  > "The absolute flux density was determined from observations of Titan and Neptune." (2 Observations and Data Reduction)
- flux scale uncertainty: 10%  
  > "The uncertainty associated with the absolute flux density is 10%." (2 Observations and Data Reduction)
- self calibration: Continuum self-cal: phase-only with six iterations, then one phase+amplitude; applied to 13CO and C18O  
  > "The phase alone was corrected first via six iterative model refinements, then the calibration was obtained for phase-plus-amplitude with no iteration." (2 Observations and Data Reduction)

### Imaging

- task: CLEAN  
  > "the corrected visibilities were imaged and deconvolved using the CLEAN algorithm with Briggs weighting with a robust parameter of 0.5." (2 Observations and Data Reduction)
- deconvolver: _not stated_
- weighting robust: Briggs robust 0.5 initially; final CLEAN with Uniform weighting for continuum and lines  
  > "The final CLEANing was performed with Uniform weighting both for the continuum and emission lines." (2 Observations and Data Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: underlying continuum subtracted from line data  
  > "The line results above were obtained after subtracting the underlying continuum, which is the typical method adopted in earlier studies." (3.2.2 Temperature Estimate)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.39"x0.34" PA 57 (continuum); 0.43"x0.37" PA 50 (lines)  
  > "those for $^{13}$CO and C$^{18}$O are $0.43\ensuremath{''} \times 0.37\ensuremath{''}$ with PA = $50\ensuremath{^\circ}$." (2 Observations and Data Reduction)
- final rms: 0.19 mJy/beam continuum  
  > "The rms noise is 0.19 mJy beam$^{-1}$ for the continuum" (2 Observations and Data Reduction)

### Inherited from earlier work

- Dust opacity relation kappa=0.1(nu/1e12 Hz)^beta, beta=1  
  > "on the basis of the conventional relation $\kappa_{\nu}=0.1(\nu / 10^{12}$ Hz)$^{\beta}$ with $\beta = 1.0$ ((cite: bec90); V11)" (3.1.2 Inner Disk and Radial Gap) [from (cite: bec90); V11]
- 1+1D vertical radiative transfer modeling  
  > "The 1+1D modeling (cite: nom09) was performed assuming the surface density estimated as above" (4.1 Constraint on Surface Density) [from (cite: nom09)]

### Not stated but needed to reproduce (our reading)

- CLEAN masks, threshold, iteration counts and cell/image sizes
- Self-calibration solution intervals and reference antenna
- Line-free channels and continuum subtraction method
- Which calibrator was used for bandpass vs each scheduling block
- Details of the 1+1D radiative transfer inputs (opacity, stellar parameters)
- Inclination/position angle used for deprojection beyond i=27
- Rest frequencies used

## Analysis recipe

1. **Calibrate, self-calibrate and image continuum and lines**: CASA calibration, CLEAN imaging, continuum self-cal applied to lines  
  > "The solution for the continuum was applied to $^{13}$CO and C$^{18}$O data." (2 Observations and Data Reduction)
   - software: CASA
   - parameter: Briggs robust 0.5; final Uniform weighting  
  > "The final CLEANing was performed with Uniform weighting both for the continuum and emission lines." (2 Observations and Data Reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit Keplerian rotation to 13CO to get inclination and systemic velocity**: Gaussian peak velocity along major axis every 0.03", then S/N-weighted least-squares Keplerian fit  
  > "S/N-weighted least-squares fitting of an analytic Keplerian equation was performed to the measured peak velocity as a function of radius." (3.2.1 Integrated Intensity and Gas Kinematics)
   - parameter: free: systemic velocity, center, inclination; stellar mass fixed at 2.2±0.3 Msun  
  > "the systemic velocity, position of the center of mass (the star), and inclination relative to an observer are set as free parameters" (3.2.1 Integrated Intensity and Gas Kinematics)
   - fitting: weighted least squares  
  > "Then, S/N-weighted least-squares fitting of an analytic Keplerian equation was performed to the measured peak velocity as a function of radius." (Results, Integrated Intensity and Gas Kinematics)
   - validation: _not stated_
3. **Estimate grain temperature from optically thick 13CO brightness temperature**: Add continuum Tb to line peak Tb after beam matching; take 13CO Tb at continuum peak (36 K) as upper bound on dust temperature  
  > "we conservatively regard 36 K, which is the $T_b$($^{13}$CO) at the radius of continuum peak, as an upper bound of the grain temperature" (4.1 Constraint on Surface Density)
   - assumption: LTE; 13CO optically thick; C13O/C18O abundance ~7  
  > "we assume the same excitation temperature ($T_{\rm ex}$) for both lines and an abundance ratio of X(C$^{13}$O)/X(C$^{18}$O) $\sim$ 7" (3.2.2 Temperature Estimate)
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive dust optical depth and surface density lower limit**: Compare Tdust with continuum Tb to get tau, convert with kappa_336=0.034 cm2/g for g/d=100  
  > "using $\tau = 0.9$ along with $\kappa_{336} = 0.034$ cm$^2$ g$^{-1}$ for a g/d of 100" (4.1 Constraint on Surface Density)
   - assumption: gas-to-dust 100; T=36 K; distance 140 pc  
  > "Assuming a g/d of 100 and a temperature of 36 K, the fitted Gaussian to the azimuthally-averaged one has a peak surface density" (Discussion, Spatial Structure)
   - fitting: _not stated_
   - validation: 1+1D vertical radiative transfer reproduced observed Tb  
  > "The observed $T_b$ was reproduced when using a grain opacity plausible for protoplanetary disks (cite: nom05)." (4.1 Constraint on Surface Density)
5. **Radial Gaussian fit and Toomre Q**: Gaussian fit to deprojected radial profile per PA and azimuthal average; compute Toomre Q with isothermal sound speed at 36 K, M*=2.2 Msun  
  > "resulting in $Q(R = 161~{\rm{AU}}) = 2.2$ using $\Sigma_{\rm{average}} = 11$ g cm$^{-2}$, the isothermal sound speed for 36 K, and a stellar mass of $2.2~M_{\ensuremath{\odot}}$." (4.3 Stability against Self-Gravity)
   - assumption: g/d = 100  
  > "the Toomre’s $Q$ parameter (cite: too64) was computed under the assumption of a g/d of 100." (Discussion, Stability against Self-Gravity)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 3.4: calibration, CLEAN imaging, self-calibration  
  > "The data were calibrated and analyzed using the Common Astronomy Software Applications (CASA) package, version 3.4." (2 Observations and Data Reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum contrast north peak/SW minimum | 30 | not stated | dimensionless | 1 | The contrast in flux density thus reaches to 30 between the northern peak and the SW minimum. |
| Outer disk total flux density at 336 GHz | 2.7 | not stated | Jy | 1 | the total flux density ($>5\sigma$) was measured as 2.7 Jy |
| Peak brightness temperature | 24 | not stated | K | 1 | The peak flux density is expressed by a brightness temperature ($T_b$) of 24 K |
| Inner disk flux density | 2.3 | 0.2 | mJy | 1 | The integrated flux density over the Gaussian was 2.3$\pm$0.2 mJy |
| Inclination | 26.9 | +2.2/-1.8 | degrees | 2 | the inclination was estimated as $i = 26.9^{+2.2}_{-1.8}$ degrees |
| Systemic velocity | 3.70 | 0.02 | km/s | 2 | The systemic velocity was determined as $3.70 \pm 0.02$ km s$^{-1}$. |
| Peak surface density (lower limit) | 28.1 | not stated | g cm-2 | 4 | the surface density was calculated as $\Sigma_{\rm peak}=$ 28.1 g cm$^{-2}$ |
| Outer disk mass | 0.09 | not stated | Msun | 4 | Integrating the surface density yielded a mass for the entire outer disk of 0.09 $M_{\odot}$ |
| Toomre Q at horseshoe peak | 0.9 | not stated | dimensionless | 5 | Locally estimated at the horseshoe peak at $R = 156$ AU, $Q$ was obtained as 0.9 for $\Sigma_{\rm peak} = 28$ g cm$^{-2}$. |
| Inner disk mass | 4.3e-5 | 0.4e-5 | Msun | 4 | the total (gas and dust) disk mass was then calculated as $(4.3 \pm 0.4) \times 10^{-5}~M_{\ensuremath{\odot}}$ |

## Qualitative findings

- Gas velocity field is consistent with simple circular Keplerian rotation; dust streamers reported earlier were not confirmed.  
  > "Dust streamers from the outer disk reported in the previous study (cite: cas13) were not confirmed." (3.1.2 Inner Disk and Radial Gap)

## Claim tuples

- H: Is the northern horseshoe locally very dense? | E: Estimate Tdust from 13CO Tb, derive tau and Sigma | R: Sigma_peak >= 28 g/cm2 for g/d 100 | F: Region is locally massive and may be gravitationally unstable (Q<~1-2) | **supported**
- H: Can the asymmetry be due to eccentric dust orbits? | E: Gaussian fits to radial profile at each PA | R: Anticorrelation between peak intensity and deprojected distance | F: Eccentric orbits excluded | **supported**
- H: Could the ring be stable if gas is depleted? | E: Consider lower g/d with C18O optical depth | R: g/d lower by >=10 gives Q>>1 | F: Alternatively dust accumulation, possible rocky core formation | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Eccentric dust orbits rejected as cause of asymmetry  
  > "The anti-correlation excludes the possible explanation that the azimuthal asymmetry is due to eccentric orbits of the dust particles." (4.2 Spatial Structure)
- How they decided it was enough: _not stated_
- Limitation (authors): Q is an upper limit and g/d assumption is a caveat; optical thickness of C18O uncertain, so derived g/d is a limit  
  > "The caveat in the above discussion is the assumption of the g/d" (4.3 Stability against Self-Gravity)
- Caveat (inferred, ours): Dust temperature set to upper bound from 13CO surface Tb; midplane could be colder or warmer
- Caveat (inferred, ours): Single opacity law assumed; grain growth would change Sigma
- Caveat (inferred, ours): Low inclination makes kinematic constraints weak
- Caveat (inferred, ours): No formal fitting uncertainties on surface density

## Reproducibility

- Data public (paper): ALMA Cycle 0 project cited; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00318.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging masks/thresholds, image sizes and cell sizes
- Missing: Self-cal intervals
- Missing: 1+1D model inputs
- Missing: Continuum subtraction channels
- Data volume (inferred): ~50-100 GB raw (4 SBs, Band 7, 4 spws x 3840 channels)
- Score (inferred): 3/5, Data and main recipe are clear and the numbers are simple, but imaging and self-cal details are missing.
- Rediscovery candidate: yes, Cycle 0 data are likely public, the recipe is short and results are numeric, though some settings must be guessed.

## Links

- Method: Nomura et al. 2009 (cite: nom09) (1+1D vertical radiative transfer modeling)
- Companion: Casassus et al. 2013 (cite: cas13) (earlier ALMA observations of HD 142527 reporting streamers)
- Companion: Verhoeff et al. 2011 (cite: ver11) (stellar parameters and SED model of the disk)

## Checks

```json
{
 "quotes": 59,
 "quotes_ok": 59,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 42,
  "rate": 0.592
 },
 "evidence_ok": true
}
```
