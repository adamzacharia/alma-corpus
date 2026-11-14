# The Surprisingly Low Carbon Mass in the Debris Disk around HD 32297

`2020ApJ...892...99C` | The Astrophysical Journal 2020 | first author: Cataldi, Gianni | arXiv: 1904.07215 | DOI: 10.3847/1538-4357/ab7cc7

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: debris_disks
- Question: What are the spatial distribution and mass of neutral carbon in the HD 32297 debris disk, and can a secondary gas production model explain the C0 and CO observations?  
  > "In this paper, we present ALMA observations of neutral carbon emission towards HD 32297. We attempt to explain the observations with a secondary gas production scenario." (Introduction)
- Target **HD 32297**: coordinates _not stated_; z/distance 132.3±1.0 pc  
  > "Located at a distance of $132.3\pm1.0$ pc (cite: BailerJones_etal_2018)" (Introduction); distance from Bailer-Jones et al. 2018  
  > "Located at a distance of $132.3\pm1.0$ pc (cite: BailerJones_etal_2018)" (Introduction)

## Data provenance

- ALMA projects: 2017.1.00201.S
- bands: Band 8  
  > "The HD 32297 disk was observed in a single pointing with ALMA Band 8 receivers on May 22, 2018" (2 Observations and data reduction)
- frequencies and spectral setup: three 2 GHz SPWs at 480, 482, 494 GHz (128 channels, continuum); one SPW on CI 492.16 GHz, 1920 channels, 488 kHz (0.30 km/s) spacing, 0.34 km/s effective resolution  
  > "The fourth spectral window was covering the C I $^3$P$_1$–$^3$P$_0$ line at 492.16 GHz, with 1920 channels, a channel spacing of 488 kHz (0.30 km s$^{-1}$)" (2 Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: 47 antennas, compact configuration  
  > "An array of 47 antennas arranged in a compact configuration was employed, with baselines ranging from 15 to 314 m." (2 Observations and data reduction)
- configurations: _not stated_
- baselines: 15 to 314 m  
  > "with baselines ranging from 15 to 314 m" (2 Observations and data reduction)
- angular resolution: 0.72" x 0.65" (96 x 86 au), PA 67 deg (line cube)  
  > "The synthesized beam is $0.72\ensuremath{''}\times0.65\ensuremath{''}$ (96 au $\times$ 86 au) with a position angle of $67\ensuremath{^\circ}$." (2 Observations and data reduction)
- max recoverable scale: ~5 arcsec  
  > "the maximum recoverable scale[^4] of our observations is $\sim$5$''$" (2 Observations and data reduction)
- sensitivity: line cube 21 mJy/beam; continuum 0.25 mJy/beam  
  > "The noise level (measured as above) is $2.0\times10^{-19}$ W m$^{-2}$ Hz$^{-1}$ sr$^{-1}$ (0.25 mJy beam$^{-1}$)." (2 Observations and data reduction)
- time on source: 45 min total, 18 min on source  
  > "The total integration time was 45 min (with 18 min on HD 32297)" (2 Observations and data reduction)
- observing dates: May 22, 2018  
  > "ALMA Band 8 receivers on May 22, 2018" (2 Observations and data reduction)
- pi or archival as stated: _not stated_
- Line: C I 3P1-3P0 (492.16 GHz)
- Other facility **Herschel/SPIRE**: 350 and 500 micron continuum for spectral index  
  > "Including previous continuum measurements from *Herschel*/SPIRE[^5] at 350 and 500 $\mu$m and ALMA at 1.3 mm (cite: MacGregor_etal_2018)" (3.1 Total C I and continuum emission)
- External data: C18O mass of the disk used as model constraint  
  > "We aim to reproduce two observables: the C$^0$ mass ($3.5\times 10^{-3}$ M$_\oplus$) and the mass of C$^{18}$O (cite: Moor_etal_2019)." (4.2 Applying to HD 32297) [from (cite: Moor_etal_2019)]
- External data: Stellar mass 1.7 Msun and inclination 83.6 deg for Keplerian curve; 1.3 mm continuum, dust mass 0.57 Mearth  
  > "assuming the same parameters as (cite: MacGregor_etal_2018): a stellar mass of 1.7 M$_\odot$ and an inclination of 83.6$^\circ$" (3.2 Position-velocity diagram) [from (cite: MacGregor_etal_2018)]
- External data: CII 158 um flux for consistency check  
  > "This compares well to the (cite: Donaldson_etal_2013) measurement of $2.68\pm0.72\times10^{-18}$ W m$^{-2}$." (Comparison to C II data) [from (cite: Donaldson_etal_2013)]
- External data: CO photodissociation cross sections (Heays, private communication, based on Visser et al. 2009)  
  > "The cross-sections for CO photo-dissociation were provided by A. Heays (private communication) and are based on (cite: Visser_etal_2009)" (4.1 Time Evolution Model) [from (cite: Visser_etal_2009); (cite: Heays_etal_2017)]

## Processing

### Calibration

- pipeline or manual: ALMA Science Pipeline  
  > "The data were calibrated by the ALMA Science Pipeline within the Common Astronomy Software Applications package (CASA) 5.1.1" (2 Observations and data reduction)
- casa version: CASA 5.1.1 for calibration; CASA 5.3.0 for further processing  
  > "For further processing of the calibrated visibilities, we used CASA 5.3.0." (2 Observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0522-3627 (bandpass, flux); J0505+0459 (phase)  
  > "J0522-3627 (bandpass, flux) and J0505+0459 (phase) were observed as calibration sources." (2 Observations and data reduction)
- flux scale uncertainty: 10%  
  > "An additional 10% flux calibration error (cite: Fomalont_etal_2014) is added in quadrature" (3.1 Total C I and continuum emission)
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "We produced an image cube by employing the CLEAN algorithm with the task `tclean` and natural weighting." (2 Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "We produced an image cube by employing the CLEAN algorithm with the task `tclean` and natural weighting." (2 Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub on CI spectral window, line masked  
  > "We used the task `uvcontsub` to subtract the continuum emission from the spectral window covering the C I line (the line was masked for the continuum fit)." (2 Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: not applied (disk much smaller than 12" primary beam)  
  > "so we do not apply a primary beam correction" (2 Observations and data reduction)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: continuum 0.73" x 0.66" (97 x 88 au), PA 66 deg  
  > "The synthesized beam is $0.73\ensuremath{''}\times0.66\ensuremath{''}$ (97 au $\times$ 88 au) with a position angle of $66\ensuremath{^\circ}$." (2 Observations and data reduction)
- final rms: 1.7e-17 W m-2 Hz-1 sr-1 (21 mJy/beam) cube; 0.25 mJy/beam continuum  
  > "is $1.7\times10^{-17}$ W m$^{-2}$ Hz$^{-1}$ sr$^{-1}$ (21 mJy beam$^{-1}$)" (2 Observations and data reduction)

### Inherited from earlier work

- Correlated noise in ALMA image-space fit handled as in Booth et al. 2017  
  > "The correlated noise in the ALMA data is handled as described by (cite: Booth_etal_2017)." (3.3 Modeling of the C I emission) [from (cite: Booth_etal_2017)]
- Ray-tracing of model cube  
  > "Then, the model is ray-traced as described in (cite: Cataldi_etal_2014) to account for optical depth." (3.3 Modeling of the C I emission) [from (cite: Cataldi_etal_2014)]
- Gaussian ring and double power-law surface density profiles  
  > "We follow (cite: Kral_etal_2019) and consider a Gaussian surface density profile for neutral C" (3.3 Modeling of the C I emission) [from (cite: Kral_etal_2019)]
- Stellar mass and inclination for Keplerian curve  
  > "assuming the same parameters as (cite: MacGregor_etal_2018)" (3.2 Position-velocity diagram) [from (cite: MacGregor_etal_2018)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and continuum fit order for uvcontsub
- Clean threshold, niter, mask, cell and image size, channel width of the cube
- Exact model grid size/resolution and the likelihood form
- Initial walker positions and convergence checks for emcee
- Photodissociation cross-section files (private communication)
- ISRF scaling used (Draine 1978 normalisation)
- Whether the line cube was Hanning-smoothed

## Analysis recipe

1. **Image line cube and continuum**: uvcontsub then tclean with natural weighting; moment 0 over 15.5–25.5 km/s; continuum from all SPWs with CI masked  
  > "produced by integrating the data cube over the (barycentric) velocities of 15.5–25.5 km s$^{-1}$" (2 Observations and data reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure total CI and continuum fluxes and spectral index**: Integrate emission above 3 sigma; error from flux samples in empty regions plus 10% calibration in quadrature  
  > "by integrating all emission above 3$\sigma$" (3.1 Total C I and continuum emission)
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure disk position angle**: Three methods (max flux in box, mirror residuals, spine fit) on continuum image, trial PAs 43–53 deg in 0.2 deg steps; Monte Carlo errors with correlated noise  
  > "We consider trial PAs between $43\ensuremath{^\circ}$ and $53\ensuremath{^\circ}$ with steps of $0.2\ensuremath{^\circ}$" (Position angle of the disk)
   - fitting: _not stated_
   - validation: Consistent with MacGregor et al. 2018 value  
  > "consistent with the value derived by (cite: MacGregor_etal_2018)" (Position angle of the disk)
4. **Position-velocity diagram**: Rotate cube by PA, integrate from -0.6 to 0.7 arcsec vertically, overplot Keplerian curve  
  > "The rotated data cube is then integrated from $-0.6\ensuremath{''}$ to $0.7\ensuremath{''}$ in the vertical direction $z$" (3.2 Position-velocity diagram)
   - assumption: Mstar 1.7 Msun, i = 83.6 deg  
  > "a stellar mass of 1.7 M$_\odot$ and an inclination of 83.6$^\circ$" (3.2 Position-velocity diagram)
   - fitting: _not stated_
   - validation: _not stated_
5. **Fit 3D LTE model to CI cube**: LTE level populations on 3D grid, ray-traced, convolved to data resolution, multiplied by primary beam; Gaussian ring or double power law surface density; fit in image space  
  > "we first calculate the level population and gas emission in each cell of a three-dimensional grid by assuming local thermodynamic equilibrium (LTE)." (3.3 Modeling of the C I emission)
   - software: emcee, LIME, pythonradex
   - parameter: Free: i, M*, v*, r0, sigma_r, M_C0, T100, dx, dz; PA fixed 48.5 deg  
  > "The position angle is fixed to 48.5$\ensuremath{^\circ}$ as determined in Appendix [7](#appendix:PA)." (3.3 Modeling of the C I emission)
   - parameter: 200 walkers, 1500 steps, first 200 discarded  
  > "The MCMC is run for 1500 steps with 200 walkers. We discarded the first 200 samples of each walker." (3.3 Modeling of the C I emission)
   - assumption: T(r)=T100 sqrt(100 au/r); mu=14; line broadening 1 km/s; Gaussian line profile  
  > "The line emission profile is assumed to be Gaussian with a broadening parameter of 1 km s$^{-1}$." (3.3 Modeling of the C I emission)
   - fitting: emcee MCMC; uninformative location- or scale-invariant priors over ranges in the parameter table; medians with 16th/84th percentile errors  
  > "we assume uninformative priors, either with a location invariant density ($\pi(\theta)=\mathrm{const}$) or a scale invariant density ($\pi(\theta)\propto\theta^{-1}$)" (3.3 Modeling of the C I emission)
   - validation: LTE flux only factor 1.3 above LIME non-LTE; fixed i=88 deg run gives unchanged parameters; no strong residuals  
  > "For that model, the total flux calculated in LTE was only a factor 1.3 higher than the flux from `LIME`." (3.3 Modeling of the C I emission)
6. **Model CO and carbon production/destruction history**: Time-evolution ODEs for CO and C mass with photon-counting CO destruction including CO self-shielding and C shielding, plus carbon removal timescale; steady-state solution and grid in event time and CO production rate; fit to C0 and C18O masses  
  > "In contrast to (cite: Kral_etal_2019), we obtain the photo-dissociation rate ($D_\mathrm{CO}$) using photon counting." (4.1 Time Evolution Model)
   - parameter: Gas ring r0=110 au, width 80 au fixed; ionisation fraction 0.2  
  > "a constant ionisation fraction of 0.2 is assumed" (4.1 Time Evolution Model)
   - assumption: ISM isotopologue ratios 13CO/12CO=1.4e-2, C18O/12CO=1.8e-3; constant CO production rate; well-mixed C and CO; ISRF of Draine 1978  
  > "$\mathrm{^{13}CO}/\mathrm{^{12}CO}=1.4\times10^{-2}$ and $\mathrm{C^{18}O}/\mathrm{^{12}CO}=1.8\times10^{-3}$" (4.2.1 Steady-state solution)
   - fitting: _not stated_
   - validation: Model run with C at disk surface changes results only by factor ~2; steady state consistent with full calculation  
  > "the derived CO production rates and C removal timescales only change by a factor of $\sim$2" (5.3 Other Uncertainties)

## Software

- **CASA** 5.1.1 (calibration), 5.3.0 (processing): Pipeline calibration, uvcontsub, tclean  
  > "We used the task `uvcontsub` to subtract the continuum emission" (2 Observations and data reduction)
- **emcee** : MCMC fit of CI models  
  > "We use a Markov chain Monte Carlo (MCMC) method implemented by the `emcee` package" (3.3 Modeling of the C I emission)
- **LIME** : Non-LTE check of the LTE approximation  
  > "calculating the full radiative transfer in non-LTE using the `LIME` code" (3.3 Modeling of the C I emission)
- **pythonradex** : Listed in the software section  
  > "pythonradex (<https://github.com/gica3618/pythonradex>)" (Software)
- **corner.py** : Posterior plots (listed in software section)  
  > "corner.py (cite: Foreman-Mackey_2016)" (Software)
- **astropy** : Listed in software section  
  > "astropy (cite: astropy_2018)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total CI 492 GHz flux | 4.0e-20 | 0.4e-20 | W m-2 | 2 | We find a total 492 GHz C I flux of $(4.0\pm0.4)\times10^{-20}$ W m$^{-2}$ |
| Total 487 GHz continuum flux | 22.0 | 2 | mJy | 2 | ($22.0\pm2$ mJy) |
| Sub-millimeter spectral index | 2.4 | not stated | dimensionless | 2 | we derive a sub-millimeter spectral index of 2.4 |
| Disk position angle | 48.5 | 0.6 | deg | 3 | yields a final estimate of $48.5\ensuremath{^\circ}\pm0.6\ensuremath{^\circ}$ |
| Neutral carbon mass (Gaussian ring) | 3.5 | +0.2/-0.2 | 1e-3 Mearth | 5 | $M_\mathrm{C^0}$ / $3.5^{+0.2}_{-0.2}$ |
| Ring radius r0 (Gaussian) | 109 | +3/-4 | au | 5 | $r_0$                / $109^{+3}_{-4}$ |
| Ring sigma_r (Gaussian) | 35.4 | +3.8/-3.5 | au | 5 | $\sigma_r$           / $35.4^{+3.8}_{-3.5}$ |
| Inclination | 77.9 | +1.7/-1.5 | deg | 5 | The derived inclination of $77.9\ensuremath{^\circ}^{+1.7}_{-1.5}$ |
| Stellar mass (fit) | 1.59 | +0.05/-0.05 | Msun | 5 | $M_*$                / $1.59^{+0.05}_{-0.05}$ |
| Steady-state CO production rate | ~15 | not stated | Mearth Myr-1 | 6 | the required CO production rate remains high at $\sim$15 M$_\oplus$ Myr$^{-1}$ |
| Carbon removal timescale | ~700 | not stated | yr | 6 | The corresponding steady state C removal timescale (equation [\[eq:C_mass_evolution\]](#eq:C_mass_evolution)) is short: $\tau_\mathrm{C}\approx 700$ yr. |
| Peak optical depth of CI along line of sight | 0.2 | not stated | dimensionless | 5 | This model has a peak optical depth of 0.2 along the line of sight. |

## Qualitative findings

- No evidence for sub-Keplerian rotation in the CI position-velocity diagram  
  > "Hence, there is no evidence for sub-Keplerian rotation, contrary to the conclusion by (cite: MacGregor_etal_2018)." (3.2 Position-velocity diagram)
- Gas is in a ring, inner region devoid of gas (rmin>60 au at 95% confidence)  
  > "We find that $r_\mathrm{min}>60$ au at the 95% confidence level" (Power law models)

## Claim tuples

- H: Is the neutral carbon in HD 32297 distributed in a ring and how massive is it? | E: MCMC fit of LTE ring models to the ALMA Band 8 CI cube | R: Gaussian ring at ~110 au, FWHM ~80 au, M_C0=(3.5±0.2)e-3 Mearth | F: The CI gas is a ring with a surprisingly low carbon mass | **supported**
- H: Can secondary CO production with shielding explain both the C0 and C18O masses without carbon removal? | E: Time-evolution model grid in event time and production rate | R: Without removal requires P_CO~100 Mearth/Myr and t0~1000 yr | F: Only a very recent catastrophic event could do it, hard to square with symmetric appearance | **partially**
- H: A steady state with rapid carbon removal explains the observations | E: Steady-state and full model with finite tau_C | R: tau_C~700 yr and P_CO~15 Mearth/Myr, above dust grind-down rate | F: Carbon must be removed rapidly; CO recycling via carbon capture on grains and CO re-formation is proposed | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: C18O used because 12CO is optically thick and 13CO may be too  
  > "We use the C$^{18}$O mass because the main component of the CO gas, $^{12}$CO, is optically thick and its mass cannot be determined accurately." (4.2 Applying to HD 32297)
- Alternative: Alternative carbon removal mechanisms (accretion, planets, viscous spreading, gas-phase chemistry, condensation) considered without satisfactory solution  
  > "We consider a number of alternative carbon removal mechanisms, but do not find a satisfactory solution to this problem at the moment." (5.2 Other C removal processes)
- How they decided it was enough: _not stated_
- Limitation (authors): Temperature poorly constrained by the data  
  > "We note that the temperature is not well constrained by our data." (3.3 Modeling of the C I emission)
- Limitation (authors): Calibration uncertainty not included in MCMC fit  
  > "We note that the calibration uncertainty, not included in the MCMC fit, might introduce some additional uncertainty in the fitted parameters." (3.3 Modeling of the C I emission)
- Caveat (inferred, ours): Low spatial resolution (~0.7") and a single SPW limit the ring structure constraints; the vertical structure is unresolved.
- Caveat (inferred, ours): Derived inclination differs from other studies, hinting at model mismatch.
- Caveat (inferred, ours): Carbon mass depends on temperature prior and LTE; low temperature could raise mass.
- Caveat (inferred, ours): Model conclusions rest on assumed ISRF, cross sections, and well-mixed gas.

## Reproducibility

- Data public (paper): Data cited by ALMA project ID; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00201.S." (Acknowledgments)
- Products in archive: _not stated_
- Code: _not stated_
- Missing: Cube imaging parameters (cell, size, threshold, mask)
- Missing: Private-communication CO cross sections
- Missing: Model code and likelihood details
- Missing: ISRF normalization details
- Data volume (inferred): ~10-50 GB raw; single short Band 8 execution
- Score (inferred): 3/5, Data and main fitting approach described, but imaging details, model code and cross-sections are not provided.
- Rediscovery candidate: no, Modeling code is custom and the recipe lacks details; cross-sections are privately supplied.

## Links

- Method: (cite: Booth_etal_2017) (Handling correlated noise in image-space fitting)
- Method: (cite: Cataldi_etal_2014) (Ray-tracing and synthetic correlated noise)
- Method: (cite: Kral_etal_2019) (Gaussian ring and double power-law CI models, shielding model)
- Companion: (cite: MacGregor_etal_2018) (Band 6 ALMA continuum and CO of HD 32297)
- Companion: (cite: Moor_etal_2019) (CO isotopologue masses of HD 32297)

## Checks

```json
{
 "quotes": 78,
 "quotes_ok": 78,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 88,
  "stated": 60,
  "rate": 0.682
 },
 "evidence_ok": true
}
```
