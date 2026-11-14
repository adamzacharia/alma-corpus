# Unveiling the physical conditions of the youngest disks. A warm embedded disk in L1527

`2018A&A...615A..83V` | Astronomy and Astrophysics 2018 | first author: van 't Hoff, Merel L. R. | arXiv: 1803.04515 | DOI: 10.1051/0004-6361/201732313

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation, protoplanetary_disks, astrochemistry
- Question: Is the embedded Class 0/I disk around L1527 warm enough to keep CO in the gas phase throughout, or does it have a cold outer region where CO is frozen out like Class II disks?  
  > "we set out to determine whether there is an extended cold outer region where CO is frozen out, as is the case for Class II disks." (abstract)
- Target **L1527 IRS (IRAS 04368+2557)**: coordinates 04h39m53.91s +26d03m09.80s (phase center, J2000)  
  > "This protostar located in the Taurus molecular cloud ($d =$140 pc, (cite: Torres2007))" (Introduction); "The phase center was $\alpha$(J2000) = 04$^{\rm{h}}$39$^{\rm{m}}$53$s$91; $\delta$(J2000) = 26$\ensuremath{^\circ}$03$\ensuremath{'}$09$\ensuremath{''}$80." (Observations); z/distance 140 pc  
  > "This protostar located in the Taurus molecular cloud ($d =$140 pc, (cite: Torres2007))" (Introduction); "The phase center was $\alpha$(J2000) = 04$^{\rm{h}}$39$^{\rm{m}}$53$s$91; $\delta$(J2000) = 26$\ensuremath{^\circ}$03$\ensuremath{'}$09$\ensuremath{''}$80." (Observations); distance from Torres et al. 2007  
  > "This protostar located in the Taurus molecular cloud ($d =$140 pc, (cite: Torres2007))" (Introduction); "The phase center was $\alpha$(J2000) = 04$^{\rm{h}}$39$^{\rm{m}}$53$s$91; $\delta$(J2000) = 26$\ensuremath{^\circ}$03$\ensuremath{'}$09$\ensuremath{''}$80." (Observations)

## Data provenance

- ALMA projects: 2013.1.01086.S
- bands: Band 6 (1.3 mm continuum, lines near 220-231 GHz)  
  > "The correlator setup included a 2 GHz continuum band centered at 233.0 GHz" (Observations)
- frequencies and spectral setup: 2 GHz continuum band at 233.0 GHz; 58.6 MHz line windows; 30.5 kHz resolution for C18O, 61.0 kHz for the other two lines  
  > "The spectral resolution was 30.5 kHz for C$^{18}$O and 61.0 kHz for the two other lines, which corresponds to a velocity resolution of 0.04 and 0.08 km s$^{-1}$, respectively." (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: Two Cycle 2 executions: compact (34 antennas, 21-539 m) and extended (35 antennas, 41-2269 m)  
  > "using 34 antennas sampling baselines between 21 and 539 m, and on 20 September 2015, using 35 antennas sampling baselines between 41 and 2269 m." (Observations)
- baselines: _not stated_
- angular resolution: 13CO 0.32x0.18'', C18O 0.32x0.19'', N2D+ 0.93x0.71''  
  > "0.32$\times$0.18 (PA = 39.0$^{\circ}$)" (Table 1)
- max recoverable scale: 4.2'' (compact) and 1.3'' (extended)  
  > "This corresponds to a maximum angular scale of 4.2$\ensuremath{''}$ and 1.3$\ensuremath{''}$, respectively." (Observations)
- sensitivity: rms per channel: 10.2 mJy/beam (13CO, 0.08 km/s), 8.7 (C18O, 0.04 km/s), 10.4 (N2D+)  
  > "0.08$^{e}$ | 10.2$^{f}$ | 4.4$^{f}$" (Table 1)
- time on source: 25 minutes in each observation  
  > "During both observations, L1527 was observed with a total on-source integration time of 25 minutes." (Observations)
- observing dates: 24 May 2015 and 20 September 2015  
  > "Observations were carried out during Cycle 2 on 24 May 2015" (Observations)
- pi or archival as stated: Archival, PI S. Koyamatsu  
  > "retrieved from the ALMA archive (project code: 2013.1.01086.S, PI: S. Koyamatsu)" (Observations)
- Line: 13CO J=2-1 (220.39868 GHz)
- Line: C18O J=2-1 (219.56035 GHz)
- Line: N2D+ J=3-2 (231.32183 GHz)
- External data: Best-fit 3D radiative transfer physical model of disk+envelope (density, dust temperature, disk radius 125 AU) used as input for optical depth and LIME models  
  > "We adopt the physical structure (dust density and temperature) from T13, who modeled the disk continuum emission" (Analysis) [from Tobin et al. 2013 (T13) (cite: Tobin2013)]
- External data: Collisional rate coefficients for RADEX  
  > "with collisional rate coefficients from (cite: Yang2010)" (4.1) [from (cite: Yang2010)]
- External data: Isotope ratios [12C]/[13C]=77, [16O]/[18O]=560  
  > "The isotope ratios are taken to be \[$^{12}$C\]/\[$^{13}$C\] = 77 and \[$^{16}$O\]/\[$^{18}$O\] = 560 (cite: Wilson1994)" (4.1) [from (cite: Wilson1994)]
- External data: Stellar mass ~0.45 Msun and disk radius ~74 AU from C18O modelling (A17); 0.19 Msun from Tobin2012  
  > "(cite: Tobin2012) derived a dynamical mass of $\sim$0.19 $M_{\ensuremath{\odot}}$, while recently A17 find a slightly larger value of $\sim$0.45 $M_{\ensuremath{\odot}}$." (4.3) [from Aso et al. 2017 (A17) (cite: Aso2017); (cite: Tobin2012)]
- Simulation/model as data: LIME synthetic 13CO/C18O/N2D+ cubes for warm, intermediate (snowline 71 AU) and cold (23 AU) models, observed via symobserve with the real uv coverage  
  > "resulting in a CO snowline at 71 AU and 23 AU, respectively" (5.1)

## Processing

### Calibration

- pipeline or manual: Compact configuration: ALMA Pipeline; extended: manual by East Asia ARC staff  
  > "while the observations in the more extended configuration were reduced manually by the East Asia ALMA Regional Center staff using CASA version 4.5." (Observations)
- casa version: CASA 4.2.2 (compact), CASA 4.5 (extended)  
  > "using the ALMA Pipeline and version 4.2.2 of Common Astronomy Software Applications (CASA)" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0423-0120 and J0510+1800 (bandpass and flux); J0510+1800 and J0429+2724 (phase)  
  > "Calibrators for the respective observations were J0510+1800 and J0429+2724 (phase), J0423-0120 and J0510+1800 (bandpass and flux)." (Observations)
- flux scale uncertainty: _not stated_
- self calibration: Self-calibration on continuum; phase and amplitude solutions applied to line bands  
  > "We performed self-calibration on the continuum data and applied the phase and amplitude solutions also to the spectral line bands." (Observations)

### Imaging

- task: CASA CLEAN  
  > "The data were imaged using the CASA task `CLEAN` with natural weighting." (Observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "The data were imaged using the CASA task `CLEAN` with natural weighting." (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum subtracted before line imaging  
  > "For the line images, the continuum was subtracted before imaging." (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 13CO and C18O use only extended configuration; N2D+ limits from compact configuration  
  > "For $^{13}$CO and C$^{18}$O, only the observations in the extended configuration are used, while the N$_2$D$^+$ upper limits are derived from the data obtained in the more compact configuration." (Observations)
- smoothing: _not stated_
- final beam: Continuum 0.30''x0.18''; 13CO 0.32''x0.18''  
  > "(for a $0.30\ensuremath{''} \times 0.18\ensuremath{''}$ beam)" (Observations)
- final rms: _not stated_

### Inherited from earlier work

- Physical structure (density, temperature, velocity field, disk radius 125 AU) adopted from the T13 best-fit model  
  > "we adopt for the physical structure the best fit model from T13." (Appendix: Physical model) [from Tobin et al. 2013 (T13)]
- Dust opacity kappa = 3.1 cm2/g at 220 GHz  
  > "Adopting the dust opacity from T13, that is, $\kappa = 3.1$ cm$^2$ g$^{-1}$ at 220 GHz" (4.3) [from T13]
- Envelope infall-rotation velocity profile (UCM)  
  > "the material in the envelope has a infalling rotating velocity profile (cite: Ulrich1976; Cassen1981)" (4.3) [from (cite: Ulrich1976; Cassen1981)]

### Not stated but needed to reproduce (our reading)

- Number of CLEAN iterations, threshold, masks and cell/image size
- Line-free channels used for continuum subtraction
- Self-calibration solution intervals and number of rounds
- Exact method/pixel selection for extracting the maximum midplane brightness temperature and its uncertainty
- Fit details of the 'by eye' model comparison; LIME settings (grid points, photons, resolution)
- Concatenated-data imaging parameters for the beam-dilution test
- symobs_custom script (not public in paper)

## Analysis recipe

1. **Image lines and continuum**: Self-calibrate continuum, apply to lines, continuum-subtract, CLEAN with natural weighting; moment-0 maps from channels above 3 sigma  
  > "The data were imaged using the CASA task `CLEAN` with natural weighting." (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Continuum flux 184.2 mJy consistent with A17  
  > "consistent with the 1.3 mm flux density reported by A17" (Observations)
2. **Establish optical depth from 13CO/C18O ratio**: Pixel-wise line ratio compared with RADEX grid over T=20-100 K and N(C18O)=1e13-1e18 cm-2  
  > "we calculate line ratios for a range of temperatures (20–100 K) and column densities (C$^{18}$O column densities ranging from $10^{13}$ cm$^{-2}$ to $10^{18}$ cm$^{-2}$) using RADEX" (4.1)
   - software: RADEX
   - parameter: [12C]/[13C]=77, [16O]/[18O]=560  
  > "\[$^{12}$C\]/\[$^{13}$C\] = 77 and \[$^{16}$O\]/\[$^{18}$O\] = 560" (4.1)
   - fitting: _not stated_
   - validation: Tested [12C]/[13C]=70, no change  
  > "Taking \[$^{12}$C\]/\[$^{13}$C\] = 70, that is, \[$^{13}$CO\]/\[C$^{18}$O\] = 8, does not change these results." (4.1)
3. **Derive midplane radial temperature profile**: Take maximum brightness temperature in highest-velocity disk-only channels and extrapolate with power law T=Tobs(R/Robs)^-q, q=0.5 and 0.35  
  > "determining the maximum temperature in the highest velocity channels and extrapolating this assuming a radial power law dependence" (4.2)
   - parameter: q=0.5 and q=0.35 (0.35 matches T13 profile between 40 and 125 AU)  
  > "adopting $q=0.35$ results in a better match to the T13 model between 40 and 125 AU" (4.2)
   - assumption: Optically thick lines, brightness temperature traces kinetic temperature (lower limit); thermalized emission  
  > "their brightness temperatures can be used as a measure for the kinetic temperature of the gas" (4.2)
   - fitting: _not stated_
   - validation: Same procedure applied to synthetic images of the warm model  
  > "computing a power law temperature profile from the synthetic images for the warm disk model (25 minutes integration) in the same way as done for the observations" (5.1)
4. **Separate disk and envelope emission kinematically**: Compute line-of-sight midplane velocities and tau=1 surfaces per 0.16 km/s bin using T13 structure  
  > "for each 0.16 km s$^{-1}$ velocity bin of the observations, we select the material moving at that velocity range and calculate the molecular column density along the line of sight" (4.3)
   - parameter: Mstar=0.45 Msun fiducial (0.19 also tested), disk radius 125 AU  
  > "Here we adopt the higher value so our estimate of the channels containing only disk emission is conservative" (4.3)
   - assumption: gas-to-dust 100, CO/H = 1e-4 where T>20 K, Tgas=Tdust  
  > "we assume a gas-to-dust ratio of 100 and a constant canonical CO/H abundance of $10^{-4}$ in the region with temperatures larger than 20 K." (4.3)
   - fitting: _not stated_
   - validation: Free-fall and modified free-fall envelope velocity alternatives  
  > "Assuming free-fall velocity for the envelope material gives similar results" (4.3)
5. **Radiative transfer modelling of CO freeze-out and abundance**: LIME models (warm, intermediate, cold; T13 temperature scaled down by 40% / 60%), synthetic visibilities with symobserve, imaged like data; compared by eye with observations; also CO abundance 1e-5 test  
  > "For the intermediate model the temperature is lowered by 40% and for the cold model by 60%, resulting in a CO snowline at 71 AU and 23 AU, respectively" (5.1)
   - software: LIME, CASA symobserve (symobs_custom)
   - parameter: inclination 85 deg; Mstar 0.4 Msun best; comparison for |dv|>1.1 km/s  
  > "We will therefore restrict the comparison between observations and models to velocities $\Delta v > 1.1$ km s$^{-1}$." (5.1)
   - assumption: CO abundance 1e-4 for T>=20 K, zero below  
  > "for $T \geq 20$ K CO is present in the gas phase at a constant abundance of $10^{-4}$ (w.r.t. H), while for $T < 20$ K CO is frozen out" (5.1)
   - fitting: No formal fit; by-eye best match  
  > "The by eye best matching model and lowest residuals are reached for a stellar mass of 0.4 $M_{\ensuremath{\odot}}$" (5.1)
   - validation: Residual maps; 5 hr integration simulations  
  > "In addition, emission was simulated for a five hour integration" (5.1)
6. **Constrain N2D+ column density and sensitivity**: 3 sigma upper limit from compact-config data, LTE with Tex 10-50 K; synthetic N2D+ images for intermediate/cold models  
  > "corresponds to an upper level for the beam-averaged N$_2$D$^+$ column density of $\sim 2-4 \times 10^{12}$ cm$^{-2}$" (3 Results)
   - software: LIME
   - assumption: LTE, Tex 10-50 K  
  > "assuming LTE and excitation temperatures between 10 and 50 K" (3 Results)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.2.2 (compact), 4.5 (extended): Calibration, CLEAN imaging, symobserve simulations  
  > "version 4.2.2 of Common Astronomy Software Applications (CASA)" (Observations)
- **RADEX** : 13CO/C18O line ratios vs temperature and column density  
  > "using RADEX[^1] (cite: vanderTak2007; vanderTak2011)" (4.1)
- **LIME** : 3D radiative transfer line modelling  
  > "simulated with the 3D radiative transfer code LIME (cite: Brinch2010)" (5.1)
- **symobs_custom** : Modified symobserve to compute visibilities for observed uv-coverage  
  > "modified version of the task `symobserve` that calculates visibilities for the observed $uv$-coverage" (5.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total 1.3 mm continuum flux density | 184.2 | 0.15 | mJy | 1 | is 184.2 $\pm$ 0.15 mJy |
| Peak continuum flux density | 66.0 | 0.16 | mJy/beam | 1 | peak flux density of 66.0 $\pm$ 0.16 mJy beam$^{-1}$ |
| N2D+ column density upper limit | 2-4e12 | not stated | cm-2 | 6 | $\sim 2-4 \times 10^{12}$ cm$^{-2}$ |
| 13CO max midplane Tb, blueshifted channel (-2.54 km/s) at 42 AU | 34 | rms 4 K per channel | K | 3 | maximum temperature of 34 K along the midplane at 42 AU |
| 13CO max midplane Tb, redshifted channel at 39 AU | 33 | rms 4 K per channel | K | 3 | in the redshifted channel this is 33 K at 39 AU |
| 13CO/C18O ratio | <3.0 everywhere, <2.0 along midplane | not stated | dimensionless | 2 | The $^{13}$CO/C$^{18}$O ratio is below 3.0 in all regions, and below 2.0 in the pixels with the highest signal-to-noise |
| CO snowline radius, intermediate / cold models | 71 / 23 | not stated | AU | 5 | resulting in a CO snowline at 71 AU and 23 AU, respectively |
| Simulated 13CO peak for CO abundance 1e-5 vs observed | 67 vs 125 (6 sigma vs 15 sigma) | not stated | mJy/beam km/s | 5 | only a $6\sigma$ detection of $^{13}$CO (peak flux of 67 mJy beam$^{-1}$ km s$^{-1}$), while the observed signal-to-noise ratio is $15\sigma$ |
| Simulated C18O peak for CO abundance 1e-5 vs observed | 20 vs 101 (2 sigma vs 14 sigma) | not stated | mJy/beam km/s | 5 | C$^{18}$O would only be detected at the $2\sigma$ level (peak flux of 20 mJy beam$^{-1}$ km s$^{-1}$), while it is observed at $14\sigma$ |
| Minimum detectable N2D+ abundance | ≳1e-11 | not stated | w.r.t. H | 6 | only abundances $\gtrsim10^{-11}$ could have been detected with the observations presented here |

## Qualitative findings

- Optically thick 13CO and C18O emission seen throughout disk and inner envelope with brightness temperatures >~25 K along the midplane; N2D+ not detected  
  > "Both CO isotopologues have brightness temperatures $\gtrsim$ 25 K along the midplane." (abstract)
- Observation-derived temperatures underestimate the true temperature (synthetic images give colder profiles); disk could be warmer than 35 K  
  > "These results suggest that the L1527 disk could be warmer than 35 K." (5.1)

## Claim tuples

- H: The L1527 disk has a cold outer region with frozen-out CO | E: Brightness temperatures of optically thick 13CO/C18O in disk-only velocity channels extrapolated with a power law | R: T>20 K out to at least 75 AU and possibly throughout 125 AU disk | F: Disk is warm enough for gas-phase CO over most or all of the disk | **supported**
- H: Models with CO snowline reproduce the data as well as a fully warm disk | E: LIME warm/intermediate/cold models compared to observations | R: Warm model best matches C18O; intermediate (71 AU) is worse; cold clearly worst | F: No CO freeze-out in the disk | **supported**
- H: CO is strongly depleted in the L1527 disk | E: Model with CO abundance 1e-5 vs canonical 1e-4 | R: Reduced abundance gives much weaker emission than observed | F: No evidence for order-of-magnitude CO depletion | **supported**
- H: N2D+ traces a cold CO-frozen region | E: Upper limit and synthetic N2D+ images | R: Not detected, but observations not sensitive enough to rule out low abundances | F: N2D+ non-detection is consistent with, but not conclusive proof of, a warm disk | **partially**

## Reasoning

- Why this data: Edge-on orientation allows direct view of the disk midplane  
  > "enabling direct probes of the midplane as shown for the Flying Saucer protoplanetary disk" (Introduction)
- Why this method: _not stated_
- Alternative: Free-fall and modified free-fall envelope velocity, stellar masses 0.19/0.45 Msun, q=0.5 vs 0.35 tested  
  > "Assuming free-fall velocity for the envelope material gives similar results" (4.3)
- How they decided it was enough: _not stated_
- Limitation (authors): Derived brightness temperatures underestimate kinetic temperature; emission resolved out near systemic velocity; optically thick so angular offset does not map to radius  
  > "the angular offset at which emission is observed no longer correlates to the physical radius at which the radiation is emitted" (4.3)
- Caveat (inferred, ours): Model comparison is by eye with no quantitative fit statistic
- Caveat (inferred, ours): Results depend on T13 physical structure, which has degenerate density and opacity
- Caveat (inferred, ours): Temperature scaling for models changes only freeze-out region not excitation
- Caveat (inferred, ours): Single source, so generalisation to young disks is untested

## Reproducibility

- Data public (paper): Data retrieved from the ALMA archive  
  > "The L1527 data analyzed here were retrieved from the ALMA archive" (Observations)
- Products in archive: _not stated_
- Missing: CLEAN parameters and masks
- Missing: LIME model setup details and symobs_custom script
- Missing: T13 model files (must be obtained from original paper)
- Data volume (inferred): ~50-200 GB raw for two executions
- Score (inferred): 3/5, Public data and clear analysis logic, but imaging and LIME details are missing and the model comparison is qualitative.
- Rediscovery candidate: no, Main results rely on by-eye model comparison and an external model (T13) not fully specified.

## Links

- Method: Brinch & Hogerheijde 2010 (cite: Brinch2010) (LIME code)
- Method: van der Tak et al. 2007 (cite: vanderTak2007) (RADEX)
- Companion: Tobin et al. 2013 (T13) (Physical model of L1527 adopted)
- Companion: Aso et al. 2017 (A17) (ALMA C18O modelling of the same data; stellar mass and disk radius)

## Checks

```json
{
 "quotes": 82,
 "quotes_ok": 82,
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
  "facts": 85,
  "stated": 60,
  "rate": 0.706
 },
 "evidence_ok": true
}
```
