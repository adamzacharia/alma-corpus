# ALMA Observations of the T Tauri Binary System AS 205: Evidence for Molecular Winds and/or Binary Interactions

`2014ApJ...792...68S` | The Astrophysical Journal 2014 | first author: Salyk, Colette | arXiv: 1407.2652 | DOI: 10.1088/0004-637X/792/1/68

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: Does the gas disk of AS 205 N show non-Keplerian motion and extended emission on ALMA scales, and is it due to disk winds, binary tidal interaction, or other causes?  
  > "also displays significant deviations from Keplerian disk emission in the observations presented here." (abstract); "Two possible explanations for these observations hold up best to close scrutiny — tidal interaction with AS 205 S or disk winds (or a combination of the two)" (abstract)
- Target **AS 205 (N and S binary)**: coordinates _not stated_; z/distance ~125 pc  
  > "AS 205 is located at the northern edge of the Ophiuchus star forming region, at a distance of $\sim$125 pc (cite: Mamajek08; Loinard08)." (INTRODUCTION); distance from Mamajek08; Loinard08  
  > "AS 205 is located at the northern edge of the Ophiuchus star forming region, at a distance of $\sim$125 pc (cite: Mamajek08; Loinard08)." (INTRODUCTION)

## Data provenance

- ALMA projects: 2011.0.00531.S
- bands: 1.3 mm (Cycle 0)  
  > "Detections near both AS 205 N and S are obtained in 1.3$\,$mm continuum" (abstract)
- frequencies and spectral setup: Four 117 MHz spectral windows, 30.5 kHz channels (0.04 km/s), resolution 61 kHz (0.08 km/s); windows at 13CO, 12CO, C18O and CH3OH (continuum)  
  > "Observations were obtained in four spectral windows of width 117 MHz, with a channel width of 30.5 kHz (0.04 km s$^{-1}$)" (OBSERVATIONS AND REDUCTION)
- continuum bandwidth: _not stated_
- arrays: Fifteen 12-m antennas  
  > "Fifteen 12-meter antennas were available for both sets of observations" (OBSERVATIONS AND REDUCTION)
- configurations: Cycle 0 extended configuration  
  > "with the Cycle 0 extended configuration" (OBSERVATIONS AND REDUCTION)
- baselines: 27 Mar: 43-402 m; 04 May: 21-402 m  
  > "On 27 Mar, the minimum and maximum baselines were 43 and 402 meters" (OBSERVATIONS AND REDUCTION)
- angular resolution: ~0.7'' x 0.5'', PA ~90-100 deg  
  > "the synthesized beam is approximately $\sim 0.7'' \times 0.5''$ with a position angle of $\sim 90^\circ-100^\circ$ degrees" (Basic results)
- max recoverable scale: ~8'' (1000 AU)  
  > "with a maximum spatial scale of $\sim8'' = 1000$ AU" (OBSERVATIONS AND REDUCTION)
- sensitivity: _not stated_
- time on source: 15.8 min per date, 31.6 min total  
  > "The total on-source integration time for each set of observations was 15.8 minutes, for a total integration time of 31.6 minutes." (OBSERVATIONS AND REDUCTION)
- observing dates: 27 Mar 2012 and 04 May 2012  
  > "Observations of AS 205 N and S were obtained on UT 27 Mar 2012 and 04 May 2012" (OBSERVATIONS AND REDUCTION)
- pi or archival as stated: _not stated_
- Line: 13CO 2-1 (220.399 GHz)
- Line: 12CO 2-1 (230.538 GHz)
- Line: C18O 2-1 (219.56 GHz)
- External data: Stellar and disk parameters for AS 205 N (R*, M*, T*, Rin, Mdisk, H) from SED + mm visibility fit  
  > "uses most of the same stellar and disk parameters derived by (cite: Andrews10) from a combined fit to the spectral energy distribution and millimeter visibilities" (Disk Models) [from (cite: Andrews10)]
- External data: AS 205 S stellar parameters R*, M*, T*  
  > "we assume $R_\star=4.2\,R_\odot$, $M_\star=0.6\, M_\odot$ and $T_\star=3450\,K$, values derived by (cite: Prato03)" (Disk Models) [from (cite: Prato03); (cite: Eisner05)]
- External data: Single-dish 1.3 mm flux density 450±90 mJy/beam  
  > "the total 1.3$\,$mm single dish flux density of 450$\pm90$ mJy/beam (assuming a 20% flux uncertainty; (cite: Andre94))" (Envelope) [from (cite: Andre94)]
- External data: Previous 12CO 2-1 flux 20.06±0.13 Jy km/s  
  > "consistent with the flux of $20.06\pm0.13$ Jy km s$^{-1}$ found by (cite: Oberg11a)" (Basic results) [from (cite: Oberg11a)]
- Simulation/model as data: RADMC/RADLite disk and disk+wind models, observed with simobserve/simanalyze using 04 May 2012 configuration and 30 min exposure  
  > "All simulated observations use the antenna configuration from the observations on 04 May 2012, and an exposure time of 30 minutes." (Disk Models)

## Processing

### Calibration

- pipeline or manual: standard procedure in CASA: passband, atmospheric/phase correction, absolute flux  
  > "Reduction steps included passband calibration, correction for atmospheric variations, and absolute flux calibration." (OBSERVATIONS AND REDUCTION)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan  
  > "Absolute flux was calibrated using observations and models of Titan." (OBSERVATIONS AND REDUCTION)
- flux scale uncertainty: 15% allowed  
  > "if we allow for a 15% error in absolute flux calibration" (Basic results)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: Clark CLEAN  
  > "CLEANED using the Clark algorithm and Briggs weighting with a robustness parameter of 0.5" (OBSERVATIONS AND REDUCTION)
- weighting robust: Briggs, robust = 0.5  
  > "CLEANED using the Clark algorithm and Briggs weighting with a robustness parameter of 0.5" (OBSERVATIONS AND REDUCTION)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub using 232 and 219 GHz windows; constant model for 12CO, linear for 13CO and C18O  
  > "Continuum subtraction was performed with the CASA routine *uvcontsub* using a fit to the 232 and 219 GHz windows and either a constant model (for $^{12}$CO) or a linear model" (OBSERVATIONS AND REDUCTION)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: two dates' measurement sets combined  
  > "The calibrated measurement sets were then combined for the two dates." (OBSERVATIONS AND REDUCTION)
- smoothing: line cubes binned to 0.08 km/s channels  
  > "then binned to a channel spacing equal to the spectral resolution (0.08 km s$^{-1}$)" (OBSERVATIONS AND REDUCTION)
- final beam: ~0.7'' x 0.5'', PA ~90-100 deg  
  > "the synthesized beam is approximately $\sim 0.7'' \times 0.5''$ with a position angle of $\sim 90^\circ-100^\circ$ degrees" (Basic results)
- final rms: ~2 mJy/beam (continuum noise in large box)  
  > "which has an RMS value of $\sim2$ mJy beam$^{-1}$" (Gas/dust ratio)

### Inherited from earlier work

- Gas temperature parameterization above tau=1 surface  
  > "used a parameterized gas temperature increase in the disk atmosphere, following the procedure described in (cite: Zhang13)" (Disk Models) [from (cite: Zhang13)]
- Wind model parameters similar to earlier work  
  > "Parameters used in our nominal model are similar to those used by (cite: Pontoppidan11)" (RADLite implementation of wind model) [from (cite: Pontoppidan11); (cite: Kurosawa06)]

### Not stated but needed to reproduce (our reading)

- CASA version
- Image size and cell size
- Line-free channels used for uvcontsub
- Clean masks and thresholds
- Calibrator names other than the phase calibrator and bandpass calibrator
- Exact moment-map thresholds
- Model fitting details (by-eye only; no objective fit)
- Coordinates and phase centers
- Extraction box positions

## Analysis recipe

1. **Reduce and image data**: Standard CASA calibration; combine dates; Clark CLEAN with Briggs weighting; uvcontsub  
  > "The data were reduced according to a standard procedure, using the Common Astronomy Software Applications package" (OBSERVATIONS AND REDUCTION)
   - software: CASA
   - parameter: robust = 0.5; 0.08 km/s channels  
  > "Briggs weighting with a robustness parameter of 0.5" (OBSERVATIONS AND REDUCTION)
   - fitting: _not stated_
   - validation: Line-free channel inspection: continuum residuals in 12CO up to ~10%  
  > "continuum-subtraction residuals in the $^{12}$CO maps of up to $\sim$10% near the centers of AS 205 N and S" (OBSERVATIONS AND REDUCTION)
2. **Measure fluxes, line widths, centers**: Moment maps, extraction boxes, Gaussian fits to line profiles; separate N and S by subtracting Gaussian fit  
  > "we perform a Gaussian fit to the full $^{12}$CO emission profile to determine the AS 205 N statistics." (Table 1)
   - software: CASA
   - fitting: Gaussian line fit  
  > "For these calculations, we perform a Gaussian fit to the full $^{12}$CO emission profile to determine the AS 205 N statistics." (Table 1 notes)
   - validation: 12CO flux compared to Oberg11a within 15% flux calibration  
  > "consistent with the flux of $20.06\pm0.13$ Jy km s$^{-1}$ found by (cite: Oberg11a)" (Basic results)
3. **Build disk models and simulate ALMA observations**: RADMC dust and RADLite line radiative transfer; simobserve/simanalyze; compare to channel and moment maps  
  > "Dust radiative transfer was performed with RADMC (cite: Dullemond04), and line radiative transfer with RADLite (cite: Pontoppidan09)." (Disk Models)
   - software: RADMC, RADLite, CASA simobserve, CASA simanalyze
   - parameter: Sigma ~ R^-0.9 to Rout=80 AU, R^-12 beyond; Rout(S)=35 AU; LTE  
  > "we use a broken power-law $\Sigma$, $\propto (R/\mathrm{AU})^{-0.9}$ out to $R_\mathrm{out}=80$ AU, and $\propto (R/\mathrm{AU})^{-12}$ beyond." (Disk Models)
   - assumption: gas/dust 100; H2/CO 5000; CO freeze-out 17 K; 12CO/13CO=60; 12CO/C18O=500  
  > "For isotopologue abundances, we assumed $^{12}$CO/$^{13}$CO$=60$ and $^{12}$CO/C$^{18}$O$=500$." (Disk Models)
   - fitting: By-eye comparison; model fluxes scaled  
  > "These inclinations and error bars are determined via by-eye examination of the channel maps and residuals" (Disk Models)
   - validation: Compare model and observed maps and spatial profiles  
  > "We show that the observed $^{13}$CO spatial profile is well reproduced by our nominal disk model." (Truncation of disk around AS 205 S)
4. **Estimate mass, optical depth, gas/dust of extended emission**: Residual flux in box after model subtraction; optically thin mass at Tex=30 K or 1000 K; dust limit with kappa=2 cm2/g  
  > "Assuming the emission is optically thin and has a low excitation temperature of 30 K, we find a total mass of $^{12}$CO of $2\times10^{-9}\, M_\odot$" (Mass and optical depth)
   - assumption: Tex 30 K; H2/CO 5000; kappa 2 cm2/g  
  > "a grain opacity of $2\,\mathrm{cm^2\, g^{-1}}$ (cite: Beckwith90)" (Gas/dust ratio)
   - fitting: _not stated_
   - validation: _not stated_
5. **Test origin scenarios and wind model**: Compare observations with cloud, envelope, circumbinary, tidal and RADLite wind models; estimate mass-loss rate  
  > "We find that the nominal wind model does not produce any appreciable extended emission, beyond that expected for a disk" (Comparison with model predictions)
   - software: RADLite
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Data reduction, imaging, uvcontsub, simobserve/simanalyze  
  > "using the Common Astronomy Software Applications package (CASA; (cite: McMullin07))" (OBSERVATIONS AND REDUCTION)
- **RADMC** : Dust radiative transfer  
  > "Dust radiative transfer was performed with RADMC (cite: Dullemond04)" (Disk Models)
- **RADLite** : Line radiative transfer including wind models  
  > "line radiative transfer with RADLite (cite: Pontoppidan09)" (Disk Models)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Binary separation (continuum) | 1.3 | not stated | arcsec | 2 | the separation of the two disks is $1.3''$, and the position angle of the binary is 214$^\circ$ |
| 12CO 2-1 flux AS 205 N | 19.23 | 0.27 | Jy km/s | 2 | $19.23\pm  0.27$, $3.02\pm  0.22$ |
| Continuum flux density N | 377 | 2 | mJy | 2 | $377\pm     2$ , $64\pm     1$ |
| Inclination AS 205 N | 15 | 5 | deg | 3 | an inclination of $\sim$15$^\circ\pm5^\circ$ is required to fit the observed $^{13}$CO velocity field for AS 205 N |
| Inclination AS 205 S | 25 | 10 | deg | 3 | we find a disk inclination of 25$^\circ\pm10^\circ$ for AS 205 S |
| AS 205 S disk outer radius | 35 | not stated | AU | 3 | set $R_\mathrm{out}=35$ AU |
| Extended 12CO flux | 1.0 | 0.2 (systematic factor of a few) | Jy km/s | 4 | we find a total flux $1.0\pm0.2$ Jy km s$^{-1}$ |
| Extended 12CO mass (30 K) | 2e-9 | not stated | Msun | 4 | we find a total mass of $^{12}$CO of $2\times10^{-9}\, M_\odot$ |
| Circumbinary disk mass upper limit | 1e-4 | 3 sigma | Msun | 5 | we derive an upper limit to the mass of a circumbinary disk around AS 205 of $10^{-4}\,M_\odot$ |
| Mass-loss rate | 1e-8 to 1e-7 | not stated | Msun/yr | 5 | we find $\dot{M}_\mathrm{loss}\sim 10^{-8} - 10^{-7} M_\odot \mathrm{yr}^{-1}$ |
| vLSR AS 205 N | 4.29 | 0.18 | km/s | 2 | we estimate $v_{LSR}$ of AS 205 N to be $4.29 \pm 0.18$ |

## Qualitative findings

- 12CO emission extends to ~2'' from AS 205 N with non-axisymmetric excess to the northeast and an S-shaped non-Keplerian velocity field deviating by ~1 km/s  
  > "The observations deviate from expectation by as much as $\sim$1 km s$^{-1}$." (Non-Keplerian velocity field)
- Cloud emission, envelope and circumbinary accretion are disfavored  
  > "we believe it’s unlikely that we are observing accretion streams from a circumbinary disk" (Accretion from a circumbinary disk)

## Claim tuples

- H: Is the gas around AS 205 N purely Keplerian? | E: Compare 12CO and 13CO moment maps with a disk model | R: Extended asymmetric emission and ~1 km/s velocity deviations | F: AS 205 N is not solely a Keplerian disk | **supported**
- H: Is extended emission from a circumbinary disk accretion stream? | E: Derive CO mass upper limit for a ring at 2''-6'' and compare to GG Tau and UY Aur | R: Upper limit 1e-4 Msun | F: Unlikely | **supported**
- H: Can a disk wind or tidal stripping explain the features? | E: Compare with RADLite wind models and tidal resonance arguments | R: Wind models give a curved velocity field but no extended emission unless modified; tidal resonance problematic | F: Neither fully explains; a combination remains possible | **partially**

## Reasoning

- Why this data: Low-J 12CO 2-1 may trace wind on larger scales; target had IR evidence for a disk wind  
  > "a low-critical-density, low-excitation tracer like $^{12}$CO $J=2-1$ may be a good choice for detecting a wind on larger scales" (INTRODUCTION)
- Why this method: _not stated_
- Alternative: Molecular cloud emission, envelope remnant, circumbinary accretion, and flyby encounters considered and disfavored  
  > "Therefore, we do not believe that molecular cloud emission can be the cause of the observed spatially extended emission." (Molecular cloud emission)
- How they decided it was enough: _not stated_
- Limitation (authors): Model degeneracies; fluxes scaled by hand; mass of AS 205 S uncertain  
  > "Since our limited information would result in strong model degeneracies were we to try to exactly match the observed data" (Disk Models)
- Caveat (inferred, ours): Models compared by eye with no quantitative fit
- Caveat (inferred, ours): Short 30-min Cycle 0 dataset limits sensitivity
- Caveat (inferred, ours): Residuals depend on disk model scaling
- Caveat (inferred, ours): Mass estimates depend on assumed excitation temperature

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: CASA version
- Missing: Imaging parameters such as cell and image size
- Missing: Full model grid and wind parameters beyond the Table
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Imaging recipe is outlined and project code given, but the model comparison is by eye and many parameters are missing.
- Rediscovery candidate: no, Main conclusions are qualitative and rely on by-eye model comparison.

## Links

- Method: (cite: Pontoppidan09); (cite: Kurosawa06) (RADLite and wind parameterization used)
- Companion: (cite: Pontoppidan11) (IR evidence for disk wind motivating the observations)

## Checks

```json
{
 "quotes": 71,
 "quotes_ok": 71,
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
  "facts": 76,
  "stated": 51,
  "rate": 0.671
 },
 "evidence_ok": true
}
```
