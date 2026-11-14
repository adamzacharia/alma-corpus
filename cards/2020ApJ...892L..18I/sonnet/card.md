# ALMA 50-parsec-resolution Imaging of Jet-ISM Interaction in the Lensed Quasar MG J0414+0534

`2020ApJ...892L..18I` | The Astrophysical Journal Letters 2020 | first author: Inoue, Kaiki Taro | arXiv: 2003.01650 | DOI: 10.3847/2041-8213/ab7b7e

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, high_z_galaxies
- Question: Is there jet-ISM interaction in the host of the lensed quasar MG J0414+0534 at z=2.639, as seen in resolved continuum and CO(11-10) at ~50 pc resolution?  
  > "In ALMA Cycle 4, we proposed carrying out long baseline observations of the CO(11-10) line to probe the distribution and kinematics of molecular gas surrounding quasar jets on small scales." (Introduction)
- Target **MG J0414+0534**: coordinates 04h14m37.7686s, +05d34m42.352s (J2000, phase center)  
  > "The phase center was $\alpha=$04$^\textrm{h}$14$^\textrm{m}$37$^\textrm{s}$.7686, $\delta=$+05$^\circ$34$'$42.352$''$ (J2000)." (Observation and Reduction); "a quadruply lensed radio-loud quasar at redshift $z_\textit{S}=2.639$ (cite: lawrence1995)" (Introduction); z/distance z = 2.639  
  > "The phase center was $\alpha=$04$^\textrm{h}$14$^\textrm{m}$37$^\textrm{s}$.7686, $\delta=$+05$^\circ$34$'$42.352$''$ (J2000)." (Observation and Reduction); "a quadruply lensed radio-loud quasar at redshift $z_\textit{S}=2.639$ (cite: lawrence1995)" (Introduction); distance from Lawrence et al. 1995  
  > "The phase center was $\alpha=$04$^\textrm{h}$14$^\textrm{m}$37$^\textrm{s}$.7686, $\delta=$+05$^\circ$34$'$42.352$''$ (J2000)." (Observation and Reduction); "a quadruply lensed radio-loud quasar at redshift $z_\textit{S}=2.639$ (cite: lawrence1995)" (Introduction)

## Data provenance

- ALMA projects: 2016.1.00281.S, 2013.1.01110.S
- bands: ~340 GHz (0.88 mm)  
  > "of the continuum emission and CO(11-10) line of MG J0414+0534 at 0.88 mm." (Introduction)
- frequencies and spectral setup: 4 spws centered at 335.370, 337.120, 347.182, 348.995 GHz, 1.875 GHz bandwidth each, 0.976563 MHz channels, 1920 channels  
  > "four spectral windows centered at 335.370, 337.120, 347.182, and 348.995 GHz, with a bandwidth 1.875 GHz (frequency domain mode)" (Observation and Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 113 m to 13.8944 km (Cycle 4)  
  > "The maximum and minimum baselines were 13.8944 km and 113 m, respectively." (Observation and Reduction)
- angular resolution: 0.03-0.04'' continuum; ~0.07'' CO  
  > "The achieved angular resolutions are $0.03\ensuremath{''}-0.04\ensuremath{''}$ and $\sim 0.07\ensuremath{''}$, respectively." (Results)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 38.72, 39.00, 40.65, 38.88 min (Cycle 4 executions)  
  > "the total on-source integrating times were 38.72, 39.00, 40.65, and 38.88 minutes, respectively." (Observation and Reduction)
- observing dates: 2017 Nov 1, 8, 10, 11 (Cycle 4)  
  > "Our ALMA Cycle 4 observations were carried out on 2017 November 1, 8, 10, and 11." (Observation and Reduction)
- pi or archival as stated: Cycle 4 PI S. Matsushita; Cycle 2 data from authors' earlier paper  
  > "(Project ID: 2016.1.00281.S, PI: S. Matsushita) combined with our Cycle 2 low angular resolution ($0.1\ensuremath{''}-0.3\ensuremath{''}$) observations" (Introduction)
- Line: CO J=11-10 (1267.014486 GHz (348.176556 GHz at z=2.639))
- Other facility **HST (CASTLES archive)**: WFPC/WFPC2 image positions and lens galaxy centroids for lens model  
  > "we used the measured *Hubble Space Telescope*(HST) Wide Field and Planetary Camera/Wide Field and Planetary Camera 2 (WFPC/WFPC2) positions" (Lens modeling and de-lensing)
- Other facility **VLBI**: 5 GHz positions of core/jet components used in lens model (from literature)  
  > "The Very Long Baseline Interferometry (VLBI) positions of the lensed possible core components at $5\,$GHz (cite: trotter2000)" (Lens modeling and de-lensing)
- External data: MIR flux ratios A2/A1 and B/A1  
  > "we used the mid-infrared (MIR) flux ratios of A2/A1 and B/A1 (cite: minezaki2009; macleod2013)" (Lens modeling and de-lensing) [from (cite: minezaki2009; macleod2013)]
- External data: CO(3-2) FWHM = 580 km/s  
  > "lower transition CO(3-2) line with FWHM $= 580\,$$\textrm{km}\,\textrm{s}^{-1}$ (cite: barvainis1998)" (Discussion) [from (cite: barvainis1998)]
- External data: CO(3-2)/(1-0) line luminosity ratio lower limit 2.56  
  > "the lower limit of the CO(3-2)/(1-0) line luminosity ratio is estimated as $2.56$ (cite: sharon2016)" (Discussion) [from (cite: sharon2016)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 5.1  
  > "(CASA; (cite: mcmullin2007)) version 5.1" (Observation and Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: Cycle 2 vs 4 amplitude difference below ~10% in uv range 140-1400 m  
  > "It turned out that the difference is below $\sim 10\%$, which is comparable to the typical error value in ALMA observations." (Observation and Reduction)
- self calibration: Phase-only, Cycle 2 and 4 separately, spws combined, S/N>=3.0 (S/N>2.0 for Cycle 4 three-antenna solutions)  
  > "we carried out phase-only self-calibration for our previous Cycle 2 (cite: inoue2017) and new Cycle 4 data, separately." (Observation and Reduction); "by reducing the condition for rejecting solutions for a group of three antennas to S/N $>2.0$" (Observation and Reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs robust=0.5 for continuum; natural for CO  
  > "The continuum and CO images were obtained with a Briggs ($robust=0.5$) and a natural weightings, respectively." (Results)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uv-plane subtraction for Cycles 2 and 4, then combined with inverse-variance weights  
  > "We also subtracted the continuum emission from the line channels for both the Cycles 2 and 4 data in the $uv$ plane" (Observation and Reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Cycle 2 and 4 combined with weights inversely proportional to error variance  
  > "we combined the continuum data with weights inversely proportional to the variance of errors." (Observation and Reduction)
- smoothing: Channel maps 146 MHz (125.6 km/s); gaussian uv taper to ~2''x1'' for spectrum  
  > "The channel maps of the lensed CO(11-10) emission were generated with a width of 146 MHz (125.6 $\textrm{km}\,\textrm{s}^{-1}$) per channel." (Observation and Reduction)
- final beam: 0.03-0.04'' continuum, ~0.07'' CO; source-plane ~0.007'' (~50 pc)  
  > "The achieved angular resolution near intensity peak in the source plane was found to be $\sim 0.007\ensuremath{''}$[^4], which corresponds to $\sim 50$ pc" (Continuum)
- final rms: _not stated_

### Inherited from earlier work

- Cycle 2 data reduction and observations  
  > "phase-only self-calibration for our previous Cycle 2 (cite: inoue2017)" (Observation and Reduction) [from (cite: inoue2017)]
- Substructure lens modeling method  
  > "constrained to fit the optical/near-infrared (NIR) and MIR data (cite: inoue2016; inoue2020)" (Lens modeling and de-lensing) [from (cite: inoue2016; inoue2020)]

### Not stated but needed to reproduce (our reading)

- Calibrator names and pipeline vs manual calibration
- Cycle 2 array configuration and dates
- Line-free channels used for continuum
- Self-cal solution intervals
- Image size, cell size, clean threshold/masks
- Lens model parameters and code (inoue2020 in preparation)
- Gaussian PSF subtraction amplitudes
- RADEX input details and line width/size assumptions

## Analysis recipe

1. **Self-calibrate and combine Cycle 2 and 4 data**: Phase-only self-cal each dataset, continuum subtraction in uv, inverse-variance weighted combination  
  > "we combined the continuum data with weights inversely proportional to the variance of errors." (Observation and Reduction)
   - software: CASA
   - parameter: S/N >= 3.0 (>2.0 for Cycle 4 three-antenna)  
  > "sufficient signal-to-noise ratio (S/N $\geq 3.0$) for each gain solution" (Observation and Reduction)
   - fitting: _not stated_
   - validation: Dynamic range rose ~120 to ~250 (Cycle 2); 140 (Cycle 4); amplitude comparison <~10%  
  > "The ’dynamic range,’ defined as peak intensity per root-mean-square (rms) error, increased from $\sim 120$ to $\sim 250$." (Observation and Reduction)
2. **Lens modeling and de-lensing**: SIE+cored isothermal sphere+shear background model fit to HST/VLBI/MIR constraints; subhalo perturbations fit with ALMA continuum; de-lensed images from linear combination of A1, A2, B  
  > "Using the best-fit lensing model, we reconstructed de-lensed images of the continuum and CO(11-10) line from a linear combination of three de-lensed images of A1, A2 and B." (Lens modeling and de-lensing)
   - fitting: Minimizing differences between de-lensed images with astrometric/magnification constraints  
  > "We obtained a best-fit model by minimizing the differences between the de-lensed images" (Lens modeling and de-lensing)
   - validation: Residual position errors <0.003'' below HST errors  
  > "The residual errors in the relative positions are $<0.003\ensuremath{''}$" (Lens modeling and de-lensing)
3. **Subtract bright core PSFs in continuum**: Subtract best-fit Gaussians at lensed p and q images with flux ratios fixed to VLBI; amplitudes chosen by visual smoothness  
  > "The absolute amplitudes were determined appropriately through visual inspection of the smoothness of the image in which the fitted Gaussian PSFs are subtracted off." (Continuum)
   - fitting: _not stated_
   - validation: _not stated_
4. **CO moment maps and PV diagram**: Pixels with S/N>2 in -700<V<800 km/s; velocity zero at core q (z_CO=2.6381); PV along line through s,p,r,q fitted by chi2 minimization  
  > "we only picked up pixels with S/N $>2$ within the velocity range of $-700<V<800\,\textrm{km}/\textrm{s}$ and combined them." (CO(11-10))
   - fitting: chi2 minimization for PV section  
  > "using $\chi^2$ minimization (Fig. [3](#f3)d)" (CO(11-10))
   - validation: _not stated_
5. **CO excitation constraints**: RADEX modelling of CO(11-10)/(3-2) brightness ratio 0.14 and CO(3-2)/(1-0) limit 0.475  
  > "Using RADEX (cite: vandertak2007), we found that a kinetic temperature of $\sim 2 \times 10^{2}$ K and a $\textrm{H}_2$ number density of $\sim5\times10^{4}$ cm$^{-3}$ are consistent" (Discussion)
   - software: RADEX
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.1: calibration and imaging  
  > "The calibration and imaging of the data were carried out using the Common Astronomy Software Application package" (Observation and Reduction)
- **RADEX** : constrain kinetic temperature and density from CO ratios  
  > "Using RADEX (cite: vandertak2007)" (Discussion)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(11-10) integrated flux | 6.3 | 0.6 | Jy km/s | 1 | The integrated flux and luminosity of the CO(11-10) line are $6.3\pm 0.6\,\textrm{Jy}\cdot \textrm{km}/\textrm{s}$ |
| CO(11-10) FWHM | 1170 | 180 | km/s | 1 | FWHM $=1170\pm 180\,$$\textrm{km}\,\textrm{s}^{-1}$ obtained from a Gaussian fit |
| Magnification, continuum | 37 | 4 | dimensionless | 2 | the total magnification factors for the continuum and CO(11-10) are $37\pm4$ and $28\pm 3$, respectively. |
| Magnification, CO(11-10) | 28 | 3 | dimensionless | 2 | the total magnification factors for the continuum and CO(11-10) are $37\pm4$ and $28\pm 3$, respectively. |
| CO(11-10)/(3-2) brightness temperature ratio | 0.14 | not stated | dimensionless | 5 | the CO(11-10)/(3-2) brightness temperature ratio is found to be 0.14 |
| Kinetic temperature / H2 density | ~2e2 K; ~5e4 cm^-3 | not stated | K; cm^-3 | 5 | a kinetic temperature of $\sim 2 \times 10^{2}$ K and a $\textrm{H}_2$ number density of $\sim5\times10^{4}$ cm$^{-3}$ |

## Qualitative findings

- Continuum and CO(11-10) show bimodal structure aligned with VLBI jet components; CO moves up to ±600 km/s at ~80 pc from core.  
  > "The CO gas in the vicinity of both the eastern and western jet components at the location of $\sim 80\,$pc from the quasar core are moving at high velocities" (abstract)

## Claim tuples

- H: Jets interact with ISM in the host of MG J0414+0534 | E: De-lensed continuum and CO(11-10) maps and PV diagram along jets | R: Bimodal structure aligned with jets; velocities up to ±600 km/s near jet components | F: Clear jet-ISM interaction | **supported**
- H: Molecular gas is hot and dense | E: RADEX modelling of CO line ratios | R: T~200 K, n~5e4 cm^-3 | F: High temperature, high density conditions | **supported**
- H: Source is a young radio source | E: Compare jet scale, interaction and GPS SED | R: Compact ≲1 kpc, SED turnover 0.4-0.5 GHz | F: Possibly early stage of quasar radio activity | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Asymmetric velocity gradient not explained by a simple circular rotating disk or spheroid.  
  > "Such an asymmetric feature cannot be explained by a simple circular rotating disk or a spheroid." (CO(11-10))
- How they decided it was enough: _not stated_
- Limitation (authors): Core component interpretation not conclusive.  
  > "Though not conclusive, our result suggests that *q* corresponds to quasar circumnuclear dust emission or synchrotron radiation" (Continuum)
- Caveat (inferred, ours): Lens model uncertainty propagates to de-lensed kinematics
- Caveat (inferred, ours): PSF subtraction amplitudes chosen visually
- Caveat (inferred, ours): Cycle 4 self-cal marginal
- Caveat (inferred, ours): Line ratio modelling is crude and with single-zone assumptions

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Lens model code and parameters (in preparation paper)
- Missing: Imaging parameters
- Missing: Calibrator and flagging details
- Data volume (inferred): ~100-300 GB raw for two projects
- Score (inferred): 3/5, Data are archival ALMA projects, but the lens modeling and imaging details are sparse.
- Rediscovery candidate: no, Lens modeling is unreleased and the recipe is incomplete.

## Links

- Method: Inoue et al. 2016 (cite: inoue2016) (Lens substructure modeling method)
- Companion: Inoue et al. 2017 (cite: inoue2017) (Cycle 2 data)
- Companion: Inoue et al. 2020 in preparation (cite: inoue2020) (Lens model details)
- Related: CASTLES

## Checks

```json
{
 "quotes": 58,
 "quotes_ok": 58,
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
  "facts": 71,
  "stated": 41,
  "rate": 0.577
 },
 "evidence_ok": true
}
```
