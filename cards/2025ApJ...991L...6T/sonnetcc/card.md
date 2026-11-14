# A Radially Resolved Magnetic Field Threading the Disk of TW Hya

`2025ApJ...991L...6T` | The Astrophysical Journal Letters 2025 | first author: Teague, Richard | arXiv: 2509.09450 | DOI: 10.3847/2041-8213/adff4d

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: Can a radially resolved magnetic field in a protoplanetary disk (TW Hya) be detected and characterized from the differential Zeeman broadening of unpolarized CN N=1-0 hyperfine emission?  
  > "We present a new approach to detecting and characterizing a magnetic field in protoplanetary disks through the differential broadening of unpolarized molecular emission from CN." (abstract)
- Target **TW Hya**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2022.1.00840.S
- bands: _not stated_
- frequencies and spectral setup: Three spectral windows covering CN N=1-0 hyperfine transitions, 113.123 to 113.520 GHz, spectral resolution 80 m/s  
  > "Three spectral windows covered multiple CN" (2 Observations); "transitions from 113.123 to 113.520 GHz" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: 41 to 44 antennas per execution block (array type not stated)  
  > "using between 41 and 44 antennas" (2 Observations)
- configurations: short-baseline (SB) and long-baseline (LB) data, concatenated  
  > "These calibrated SB data were concatenated with the long-baseline (LB) observations" (2 Observations)
- baselines: 15.3 to 2516.8 m projected  
  > "Projected baselines ranged from 15.3 to 2516.8 m" (2 Observations)
- angular resolution: median beam 0.53'' x 0.42'', PA 105 deg  
  > "These parameters result in a median beam size of $0.53\ensuremath{''} \times 0.42\ensuremath{''}$ with a position angle of $105\ensuremath{^\circ}$" (2 Observations)
- max recoverable scale: 12.2''  
  > "the maximum recoverable scale (MRS) was 12.2" (2 Observations)
- sensitivity: 1.8 mJy/beam per channel (0.76 K)  
  > "and a per channel sensitivity of $1.8~{\rm mJy~beam^{-1}}$ (0.76 K)" (2 Observations)
- time on source: 670 minutes total on-source  
  > "for a total on-source integration time of 670 minutes" (2 Observations)
- observing dates: 7 January 2023 to 12 May 2023 (ten execution blocks)  
  > "comprise ten execution blocks (EBs) observed between 7 January 2023 and 12 May 2023" (2 Observations)
- pi or archival as stated: PI program (P.I. Teague); described as new ALMA observations  
  > "The data from project 2022.1.00840.S (P.I. Teague)" (2 Observations); "we apply it to new ALMA observations of the full complement of hyperfine components from the" (abstract)
- Line: CN N=1-0, nine hyperfine components (J, F levels as in Table 1) (113.123369 to 113.520420 GHz (Table 1))
- Other facility **CDMS**: Einstein A coefficients and upper-state level weights for the CN hyperfine components  
  > "were taken from CDMS (cite: Endres_ea_2016)" (Molecular Properties)
- External data: Zeeman-related line properties z, Delta Q and Q-bar for the CN hyperfine components  
  > "were taken from (cite: Lankhaar_Teague_2023)" (Molecular Properties) [from (cite: Lankhaar_Teague_2023)]
- External data: Einstein A coefficients and upper-state level weights g_u (CDMS)  
  > "were taken from CDMS (cite: Endres_ea_2016)" (Molecular Properties) [from (cite: Endres_ea_2016), which collates (cite: Dixon_Woods_1977) and (cite: Skatrud_ea_1983)]
- External data: CN-H2 collision rates used in the RADEX excitation model  
  > "with the collision rates from (cite: Kaligina_Lique_2015)" (3.1 Excitation Analysis) [from (cite: Kaligina_Lique_2015)]
- External data: Source inclination and position angle adopted for each annulus (+5.8 deg, 151.6 deg)  
  > "Following (cite: Teague_ea_2022), a source inclination and position angle of" (3.1 Excitation Analysis) [from (cite: Teague_ea_2022)]
- External data: Upper limits on non-thermal broadening used for the Gaussian prior on Delta V_nt  
  > "following the upper limits reported in (cite: Flaherty_ea_2018)" (3.1 Excitation Analysis) [from (cite: Flaherty_ea_2018)]
- External data: 3.1 mm continuum optical depth estimate used to justify ignoring continuum opacity  
  > "estimates the 3.1 mm continuum optical depth to be" (3.2 Zeeman Splitting) [from (cite: Macias_ea_2021)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Per-EB alignment to common disk center, then SB data: 3 rounds phase-only (solint inf, 360 s, 90 s) + 1 amplitude (inf); concatenated with LB, then 2 rounds phase-only (inf, 360 s) + 1 amplitude (inf); ~4x peak continuum SNR gain; tables applied to line visibilities  
  > "followed by one round of amplitude self-calibration with" (2 Observations); "These calibrated SB data were concatenated with the long-baseline (LB) observations, after which two rounds of phase-only self-calibration (" (2 Observations); "This calibration yielded an improvement of approximately 4" (2 Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: robust = 1  
  > "value of 1 for the final imaging run, CLEANing down to a threshold of" (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: median 0.53'' x 0.42'', PA 105 deg  
  > "These parameters result in a median beam size of $0.53\ensuremath{''} \times 0.42\ensuremath{''}$ with a position angle of $105\ensuremath{^\circ}$" (2 Observations)
- final rms: 1.8 mJy/beam per channel (0.76 K); CLEAN threshold 3 sigma  
  > "and a per channel sensitivity of $1.8~{\rm mJy~beam^{-1}}$ (0.76 K)" (2 Observations); "CLEANing down to a threshold of $3\sigma$" (2 Observations)

### Inherited from earlier work

- Zeeman splitting line-profile model (sum over magnetic substate transitions, weighted by relative line strength)  
  > "we implement the Zeeman splitting model presented in (cite: Lankhaar_Teague_2023)" (3.2 Zeeman Splitting) [from (cite: Lankhaar_Teague_2023)]
- Excitation analysis framework that the Zeeman splitting is added to  
  > "This builds on excitation analyses described in many previous works, such as (cite: Teague_ea_2016) and (cite: Teague_ea_2018c)" (3 Methodology) [from (cite: Teague_ea_2016); (cite: Teague_ea_2018c)]
- Convolution of the model spectrum with a Gaussian kernel of free FWHM to absorb systematic broadening  
  > "Following (cite: Cataldi_ea_2021), we account for any systematic broadening" (3.1 Excitation Analysis) [from (cite: Cataldi_ea_2021)]
- Shift-and-stack approach (used by earlier works; here replaced by shifting model spectra; also used for integrated intensities)  
  > "approach described in (cite: Yen_ea_2016)" (3.1 Excitation Analysis) [from (cite: Yen_ea_2016)]
- Source inclination and position angle  
  > "Following (cite: Teague_ea_2022), a source inclination and position angle of" (3.1 Excitation Analysis) [from (cite: Teague_ea_2022)]
- Definition of the Zeeman sensitivity weight w = Z x Q-bar  
  > "as defined in (cite: Lankhaar_Teague_2023)" (2 Observations) [from (cite: Lankhaar_Teague_2023)]

### Not stated but needed to reproduce (our reading)

- ALMA band and array (12 m vs 7 m) of the observations; antenna configurations per EB
- CASA version and whether the pipeline or manual calibration was used; flux, bandpass and phase calibrators and flux scale uncertainty
- Imaging task, deconvolver, cell size, image size, masks and primary-beam correction
- Continuum subtraction method and line-free channels
- Self-calibration details: reference antenna, SB/LB boundary, spw combination, solution SNR cuts
- Which pixels per annulus count as independent samples and how spectra were extracted and weighted
- Prior ranges for every free parameter and the likelihood function (noise estimate per channel)
- Walker initialization, convergence checks beyond the ~200 autocorrelation time, and handling of the isothermal-slab geometry
- How radius-dependent systemic velocity and Keplerian stellar mass (0.82 vs 0.84 Msun used in different places) were fixed for fitting
- Source distance and coordinates
- Mapping from posterior to the 'significant detection' radii beyond the stated median-separation rule, and the exact plotted lower limit procedure for plasma beta

## Analysis recipe

1. **Align and self-calibrate the execution blocks**: Re-align EBs to a common disk center (Gaussian fit to continuum) with phaseshift and fixplanets; phase-only and amplitude self-calibration on SB data, concatenate with LB, further self-calibration; apply tables to line visibilities  
  > "All individual EBs were first re-aligned to a common disk center, determined based on a Gaussian fit to the continuum emission, using the" (2 Observations); "The final calibration tables were then applied to the aligned line visibilities." (2 Observations)
   - software: CASA
   - parameter: SB: phase-only solint inf, 360 s, 90 s; amplitude solint inf. SB+LB: phase-only solint inf, 360 s; amplitude solint inf  
  > "followed by one round of amplitude self-calibration with" (2 Observations); "These calibrated SB data were concatenated with the long-baseline (LB) observations, after which two rounds of phase-only self-calibration (" (2 Observations)
   - fitting: _not stated_
   - validation: Peak continuum SNR improved by approximately 4x  
  > "This calibration yielded an improvement of approximately 4" (2 Observations)
2. **Image the CN line cubes**: Final imaging at 80 m/s channel spacing (the FWHM spectral resolution), robust = 1, CLEAN down to 3 sigma  
  > "value of 1 for the final imaging run, CLEANing down to a threshold of" (2 Observations); "CLEANing down to a threshold of $3\sigma$" (2 Observations)
   - software: CASA
   - parameter: robust = 1; channel spacing 80 m/s; median beam 0.53'' x 0.42''; 1.8 mJy/beam per channel  
  > "These parameters result in a median beam size of $0.53\ensuremath{''} \times 0.42\ensuremath{''}$ with a position angle of $105\ensuremath{^\circ}$" (2 Observations); "and a per channel sensitivity of $1.8~{\rm mJy~beam^{-1}}$ (0.76 K)" (2 Observations)
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure hyperfine flux densities and integrated intensities**: Spatially integrate a 4'' (240 au) radius circular aperture per channel; integrated intensities via shift-and-stack, integrated spatially to 4'' and spectrally over +/-300 kHz  
  > "which were calculated by spatially integrating a circulate aperture with a radius of 4" (2 Observations); "The data were spatially integrated out to" (Molecular Properties)
   - software: GoFish
   - parameter: Shift-and-stack with dynamical stellar mass 0.84 Msun and inclination 5.8 deg  
  > "where a dynamical stellar mass of" (Molecular Properties)
   - fitting: _not stated_
   - validation: _not stated_
4. **Extract annular spectra**: Annuli of spatially independent pixels (separated by at least a beam FWHM) fitted simultaneously; annuli every 0.1'' with one-pixel (0.05'') width between 0.4'' and 4''  
  > "we simultaneously fit annuli of spatially independent pixels (i.e., pixels that are separated by at least a beam FWHM)" (3.1 Excitation Analysis); "To create the radial profiles, annuli were extracted every $0.1\ensuremath{''}$, roughly a fifth of the beam major axis, with a width of one pixel, $0.05\ensuremath{''}$," (3.3 MCMC Sampling)
   - assumption: Disk is azimuthally symmetric so line profiles vary only in their centers through projected disk velocity  
  > "The assumption here is that the disk is azimuthally symmetric such that the line profiles vary only in their centers due to the projection of the disk velocity structure." (3.1 Excitation Analysis)
   - fitting: _not stated_
   - validation: Narrow annuli limit Keplerian shear broadening to ~100 m/s at 1'' down to ~10 m/s at 3''  
  > "The narrow annuli are necessary to reduce the impact of Keplerian shear across the annulus width" (3.3 MCMC Sampling)
5. **Fit excitation plus Zeeman model with MCMC**: Model all hyperfine components with RADEX (SpectralRadex) optical depths plus the Zeeman splitting profile, shifted by projected velocity field; two field scenarios (disk-centric B_phi, B_r, B_z with mixing angle; constant-theta environmental field); 9 or 10 free parameters  
  > "(cite: vanderTak_ea_2007) with the collision rates from (cite: Kaligina_Lique_2015) to calculate the optical depth of each hyperfine component" (3.1 Excitation Analysis); "we explore two scenarios:" (3.2 Zeeman Splitting); "In total, the model contains either nine or ten free parameters" (3.2 Zeeman Splitting)
   - software: SpectralRadex, RADEX, emcee
   - parameter: emcee with 128 walkers, 20,000 steps, default StretchMove; autocorrelation time ~200, 20 tau discarded as burn-in  
  > "utilizing 128 walkers which took 20,000 steps using the default" (3.3 MCMC Sampling)
   - assumption: Emitting region is a geometrically thin, isothermal slab  
  > "This model makes the implicit assumption that the emitting region can be well represented by a geometrically thin, isothermal slab." (3.1 Excitation Analysis)
   - assumption: Continuum opacity ignored  
  > "With this model, we implicitly ignore the impact of continuum opacity" (3.2 Zeeman Splitting)
   - fitting: emcee; uniform priors over broad ranges, except Gaussian prior on non-thermal broadening centered on zero with width 0.08 c_s; likelihood not stated  
  > "All parameters assumed uniform priors over some broad range of possible values, except the non-thermal broadening contribution which was chosen to have a Gaussian prior centered on zero with a width of" (3.3 MCMC Sampling)
   - validation: Posterior covariances inspected for one annulus; slight FWHM_conv vs |B| covariance noted  
  > "No significant correlations are found, however a slight covariance is observed between" (9.1 Excitation Analysis)
6. **Test Zeeman origin with randomized sensitivities**: Rerun fits for both field scenarios with the Zeeman properties of the most sensitive hyperfine transitions swapped with the least sensitive ones (two swap pairs); real vs mixed |B| posteriors compared  
  > "To verify that the broadening we detect can be uniquely associated with magnetic-field induced Zeeman splitting, we run two additional" (3.4 Randomized Zeeman Sensitivities)
   - software: emcee
   - parameter: Posteriors counted as statistically different if medians differ by more than the quadrature sum of their standard deviations (16th to 84th percentile widths in the appendix)  
  > "To classify the posterior distributions as statistically different, we require that their medians are separated by more than the quadrature sum of their standard deviations." (3.4 Randomized Zeeman Sensitivities)
   - fitting: _not stated_
   - validation: Colored points mark radii where correct sensitivities give significantly higher |B| than mixed ones  
  > "The colored points show radii where the magnetic field strength posteriors of the" (4.1 Field Strength)
7. **Derive plasma beta lower limits**: Thermal pressure from ideal gas with inferred T_kin and n(H2) lower limit; magnetic pressure |B|^2/8pi; median of beta distribution plotted as lower limit  
  > "The thermal pressure was calculated assuming an ideal gas with a temperature set to the inferred" (4.3 Plasma beta); "the median of the parameter distribution was chosen as the plotted lower limit" (4.3 Plasma beta)
   - assumption: CN data favor LTE at all radii, so only lower limits on density and beta  
  > "the data favored an LTE solution at all radii, which results only in lower limits of the gas density" (4.3 Plasma beta)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibration and imaging (phaseshift, fixplanets tasks named; listed in Software)  
  > "All individual EBs were first re-aligned to a common disk center, determined based on a Gaussian fit to the continuum emission, using the" (2 Observations); "(cite: CASA)" (Software)
- **GoFish** : Spatially integrated flux densities of the hyperfine components  
  > "which were calculated by spatially integrating a circulate aperture with a radius of 4" (2 Observations); "(cite: GoFish)" (Software)
- **SpectralRadex** : Python implementation of RADEX used to model the observed spectrum  
  > "(cite: SpectralRadex)" (Software); "(cite: vanderTak_ea_2007) with the collision rates from (cite: Kaligina_Lique_2015) to calculate the optical depth of each hyperfine component" (3.1 Excitation Analysis)
- **RADEX** : Non-LTE excitation and optical depth of each CN hyperfine component  
  > "(cite: vanderTak_ea_2007) with the collision rates from (cite: Kaligina_Lique_2015) to calculate the optical depth of each hyperfine component" (3.1 Excitation Analysis)
- **emcee** : MCMC sampling of the model posteriors  
  > "An exploration of the parameter posterior distributions was performed with the MCMC package" (3.3 MCMC Sampling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total integrated CN N=1-0 flux | 4.38 | 0.04 | Jy km/s | 3 | The total integrated flux for the $N=1-0$ transition is $4.38 \pm 0.04~{\rm Jy~km\,s^{-1}}$ |
| Median beam size | 0.53 x 0.42 arcsec, PA 105 deg | not stated | arcsec, deg | 2 | These parameters result in a median beam size of $0.53\ensuremath{''} \times 0.42\ensuremath{''}$ with a position angle of $105\ensuremath{^\circ}$ |
| Per-channel sensitivity | 1.8 mJy/beam (0.76 K) | not stated | mJy/beam | 2 | and a per channel sensitivity of $1.8~{\rm mJy~beam^{-1}}$ (0.76 K) |
| Radially averaged magnetic field strength, disk-centric model | 9 | 2 | mG | 5 | Both field morphologies yield a similar radially averaged magnetic field strength of $9 \pm 2$ mG and $8 \pm 2$ mG for the disk-centric model and for the environmental field, respectively. |
| Radially averaged magnetic field strength, environmental model | 8 | 2 | mG | 5 | Both field morphologies yield a similar radially averaged magnetic field strength of $9 \pm 2$ mG and $8 \pm 2$ mG for the disk-centric model and for the environmental field, respectively. |
| Magnetic field strength between 60 and 120 au | ~10 | not stated | mG | 5 | we recover a radially resolved magnetic field with a strength of ${\sim}10~{\rm mG}$ between 60 and 120 au |
| Magnetic field strength at 3.2'' (190 au), disk-centric model only | ~12 | not stated | mG | 5 | a magnetic field is also detected at $3.2\ensuremath{''}$ (190 au) with a ${\sim}~12$ mG field strength |
| Plasma beta lower limit range | between 0.1 and 0.01 | not stated | dimensionless | 7 | correspond to a lower limit between 0.1 and 0.01 for the plasma |
| Local gas density lower limit | >~1e8 | not stated | cm^-3 | 5 | Lower limits on the local gas density ($n({\rm H_2}) \gtrsim 10^8~{\rm cm^{-3}}$) |
| Kinetic temperature profile | above 30 K in the inner disk, ~10 K outside 2.5'' (plateau) | not stated | K | 5 | starting from above 30 K in the inner disk and dropping to around 10 K outside |
| Field inclination angle theta_B transition | theta_B <~30 deg at 1.2'' to >~60 deg at 1.6'' | not stated | deg | 5 | a steady transition from $\theta_B \lesssim 30\ensuremath{^\circ}$ at $1.2\ensuremath{''}$ to $\theta_B \gtrsim 60\ensuremath{^\circ}$ at $1.6\ensuremath{''}$ |

## Qualitative findings

- Field is poloidal inside the gap at 1.37'' and in the disk plane at larger radii; field strength appears to peak at the gap  
  > "revealing a predominantly poloidal field at 60 au, sharply transitioning to one within the disk plane outside of the gap at 82 au." (abstract)
- Both field morphologies fit the data equally well, so neither is favored  
  > "neither is clearly favored." (5.1 Global Magnetic Field Morphology)
- Planar component could not be split into toroidal and radial parts; phi_B unconstrained at every radius  
  > "The signal-to-noise ratio of the data meant that the planar component was unable to be decomposed into toroidal and radial components." (abstract)

## Claim tuples

- H: Zeeman broadening of unpolarized CN hyperfine lines can reveal a magnetic field in the TW Hya disk | E: Fit a RADEX plus Zeeman model with emcee to annular spectra of all nine CN N=1-0 hyperfine components | R: ~10 mG field detected between 60 and 120 au, with |B|/delta|B| >~ 5 between 1'' and 2.5'' | F: A radially resolved magnetic field threads the disk | **supported**
- H: The detected broadening is uniquely attributable to Zeeman splitting | E: Randomized models swapping Zeeman properties of the most and least sensitive hyperfine transitions | R: Correct-sensitivity posteriors peak at larger |B| over most of the disk, but outer-disk posteriors are too wide to differentiate | F: Zeeman origin holds over the inner/mid disk; not demonstrated beyond ~2.5'' | **partially**
- H: The field morphology (poloidal vs in-plane; toroidal vs radial) can be constrained from azimuthal broadening | E: Compared disk-centric and constant-theta environmental models; fitted theta_B and phi_B per annulus | R: Poloidal inside the gap and in-plane outside; phi_B unconstrained everywhere | F: Morphology only weakly constrained; toroidal/radial decomposition not possible with these data | **partially**
- H: The excitation analysis can bound the plasma beta in the CN emitting layer | E: Combined T_kin and n(H2) lower limits from the LTE solution with the derived |B| | R: Beta lower limits between 0.1 and 0.01 | F: Field is dynamically important in the CN layer (strict lower limits only) | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Avoids needing polarized emission; low frequency lines are easier to schedule; single pixels lack signal, so annuli are fitted jointly  
  > "bypasses the need for polarized emission and benefits from the improved schedulability of low frequency programs" (1 Introduction); "A single pixel does not contain sufficient signal to robustly identify the influence of a magnetic fields on the line profile." (3.1 Excitation Analysis)
- Alternative: Two field scenarios (azimuthally symmetric disk-centric field vs large-scale environmental field with constant theta) were both fitted; neither rejected  
  > "we explore two scenarios:" (3.2 Zeeman Splitting)
- Alternative: Instead of shift-and-stack before fitting, model spectra are shifted to the reference frame to propagate uncertainties  
  > "we opt to instead shift our model spectra to the appropriate reference frame through" (3.1 Excitation Analysis)
- How they decided it was enough: _not stated_
- Limitation (authors): Beam smearing biases results inside ~1'' (60 au)  
  > "In general, beam smearing will impact the shape of the spectrum in regions inwards of approximately twice the beam FWHM." (4 Results)
- Limitation (authors): Isothermal thin-slab excitation model  
  > "This model makes the implicit assumption that the emitting region can be well represented by a geometrically thin, isothermal slab." (3.1 Excitation Analysis)
- Limitation (authors): LTE solution gives only lower limits on density and plasma beta  
  > "the data favored an LTE solution at all radii, which results only in lower limits of the gas density" (4.3 Plasma beta)
- Limitation (authors): Limited spectral resolution prevents robust line-width inference in the outer disk where lines are very narrow  
  > "With such narrow lines, the limited spectral resolution of the data will prohibit robust inferences about the line width" (9.1 Excitation Analysis)
- Caveat (inferred, ours): Detection rests on small differential line-width ratios at 80 m/s resolution; unmodeled broadening (e.g. vertical structure, back-side emission) is argued against in simulations only
- Caveat (inferred, ours): Both morphology models fit equally well and phi_B is unconstrained, so the field orientation claims are weak
- Caveat (inferred, ours): Plasma beta is a lower limit from an LTE density bound and refers to the CN layer, not the midplane
- Caveat (inferred, ours): Prior ranges and likelihood details are not given, so posterior widths cannot be audited

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Fitting code with priors and likelihood is not released or linked in the paper text
- Missing: CASA version, calibrators, imaging masks and cell/image size not stated
- Missing: Per-annulus pixel selection and noise model not specified
- Data volume (inferred): Ten execution blocks with three spectral windows at 80 m/s resolution; likely on the order of 100 GB to a few hundred GB raw (rough estimate)
- Score (inferred): 3/5, Project code, spectral setup, self-calibration solints, imaging robust and MCMC settings are given, and numeric results are listed, but there is no code release and several key settings (priors, likelihood, CASA version, masks, calibrators) are missing.
- Rediscovery candidate: no, Public availability of the data is not stated in the paper and the custom Zeeman fitting code and priors are not provided, so a faithful redo is not guaranteed.

## Links

- Method: (cite: Lankhaar_Teague_2023) (Zeeman splitting line-profile model, sensitivity parameters z, Delta Q, Q-bar)
- Method: (cite: Yen_ea_2016) (shift-and-stack technique)
- Method: (cite: Teague_Loomis_2020) (non-LTE excitation analysis with non-thermal broadening and Keplerian shear estimates)
- Method: (cite: Teague_ea_2016); (cite: Teague_ea_2018c) (excitation analyses the model builds on)
- Companion: (cite: Teague_ea_2022) (source inclination and position angle, spiral arm and gap structure of TW Hya)
- Companion: (cite: Vlemmings_ea_2019) (earlier circular polarization upper limits for CN in TW Hya)
- Companion: (cite: Yoshida_ea_2024) (independent non-LTE CN analysis with consistent excitation conditions)
- Related: 2022.1.00840.S

## Checks

```json
{
 "quotes": 101,
 "quotes_ok": 101,
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
  "facts": 100,
  "stated": 64,
  "rate": 0.64
 },
 "evidence_ok": true
}
```
