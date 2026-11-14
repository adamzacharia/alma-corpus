# The ALMA Spectroscopic Survey in the HUDF: CO Luminosity Functions and the Molecular Gas Content of Galaxies through Cosmic History

`2019ApJ...882..138D` | The Astrophysical Journal 2019 | first author: Decarli, Roberto | arXiv: 1903.09164 | DOI: 10.3847/1538-4357/ab30fe

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: high_z_galaxies, cosmology
- Question: How do the CO luminosity functions and the cosmic molecular gas density rho(H2) evolve with redshift, from the ASPECS LP 3 mm blind line scan?  
  > "we constrain the evolution of the cosmic molecular gas density $\rho$(H$_2$): this cosmic gas density peaks at $z\sim1.5$" (abstract)
- Target **Hubble Ultra Deep Field / XDF mosaic (17 pointings)**: coordinates central pointing RA 03:32:38.5, Dec -27:47:00 (J2000)  
  > "the central pointing is centered at Right Ascension = 03:32:38.5 and Declination = -27:47:00 (J2000.0)" (2.1 Survey design and observations); z/distance CO lines at z=0.003-4.475  
  > "the central pointing is centered at Right Ascension = 03:32:38.5 and Declination = -27:47:00 (J2000.0)" (2.1 Survey design and observations); distance from CO-based redshifts, cross-checked with catalog redshifts (MUSE etc.)  
  > "the central pointing is centered at Right Ascension = 03:32:38.5 and Declination = -27:47:00 (J2000.0)" (2.1 Survey design and observations)

## Data provenance

- ALMA projects: 2016.1.00324.L
- bands: Band 3 (3 mm), 84-115 GHz  
  > "The observations were performed in 5 different frequency settings, covering the frequency range 84–115 GHz." (2.1 Survey design and observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C40-3  
  > "The survey was executed with the array in a relatively compact (C40-3) configuration." (2.1 Survey design and observations)
- baselines: 15-700 m  
  > "Baselines ranged between 15 and 700 m." (2.1 Survey design and observations)
- angular resolution: ~1.75'' x 1.49'' (PA=91.5 deg) natural; ~3.5'' tapered  
  > "The resulting synthesized beam is $\approx 1.75''\times1.49''$ (PA=$91.5^\circ$) at the center of the observed frequency range." (2.2 Data reduction, calibration, and imaging)
- max recoverable scale: _not stated_
- sensitivity: ~0.2 mJy/beam per 7.813 MHz channel  
  > "We reach a sensitivity of $\sim 0.2$ mJy beam$^{-1}$ per 7.813 MHz channel throughout the scanned frequency range." (2.2 Data reduction, calibration, and imaging)
- time on source: 68 hr of telescope time including calibration and overheads  
  > "The 3 mm survey presented here took 68 hr of telescope time (including calibrations and overheads)" (2.1 Survey design and observations)
- observing dates: December 2-21, 2016  
  > "was executed between December 2–21, 2016 (ALMA Cycle 4)." (2.1 Survey design and observations)
- pi or archival as stated: _not stated_
- Line: CO J=1-0 to 4-3 (blind scan, 2-1, 3-2, 4-3 mainly) (not stated)
- Other facility **HST (CANDELS, 3D-HST grism) and Spitzer**: Optical/NIR photometry and grism spectroscopy, IRAC/MIPS photometry  
  > "The bulk of optical and NIR photometry comes from the *Hubble* Space Telescope (*HST*) Cosmic Assembly Near-infrared Deep Extragalactic Legacy Survey" (3 Ancillary data)
- Other facility **VLT/MUSE (MUSE HUDS)**: Spectroscopic redshifts for line identification  
  > "The main optical spectroscopy sample in the ASPECS LP footprint comes from the MUSE *Hubble* Ultra Deep Survey" (3 Ancillary data)
- External data: CO excitation ratios r_J1 = {1.00, 0.76±0.09, 0.42±0.07, 0.31±0.07}  
  > "with $r_{J1}=\{1.00$, $0.76\pm0.09$, $0.42\pm0.07$, $0.31\pm0.07\}$, for $J_{\rm up}$=$\{$1, 2, 3, 4$\}$" (4.3 Line luminosities and corresponding H2 mass) [from (cite: daddi15)]
- External data: Line search catalog (findclumps), fidelity and completeness  
  > "Among the compilations presented in GL19, here we refer to the results obtained with findclumps." (4.1 Line search) [from (cite: gonzalezlopez19)]
- External data: Local CO(1-0) luminosity functions and rho(H2)  
  > "compared to the local universe (cite: keres03; boselli14; saintonge17)" (5 Discussion) [from (cite: keres03; boselli14; saintonge17)]

## Processing

### Calibration

- pipeline or manual: CASA pipeline plus own procedures following the pipeline scheme; own-reduced cube used  
  > "We processed the data using both the CASA pipeline for ALMA data (cite: mcmullin07) and our own procedures (cite: aravena16a), which follow the general scheme of the official ALMA pipeline." (2.2 Data reduction, calibration, and imaging)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0334-4008 (flux, bandpass, pointing); J0342-3007 phase  
  > "The quasar J0334-4008 was observed as a flux, bandpass, and pointing calibrator, while the quasar J0342-3007 served as phase calibrator." (2.1 Survey design and observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "We imaged the 3 mm cube with natural weighting using the task tclean." (2.2 Data reduction, calibration, and imaging)
- deconvolver: dirty cube used for line search and most analysis  
  > "The lack of very bright sources in our cubes allows us to perform our analysis on the ‘dirty’ cube" (2.2 Data reduction, calibration, and imaging)
- weighting robust: natural weighting  
  > "We imaged the 3 mm cube with natural weighting using the task tclean." (2.2 Data reduction, calibration, and imaging)
- uv taper: 3'' taper, cleaned to 2-sigma, beam ~3.5'' (spectral extraction only)  
  > "we image the dataset after applying a u,v taper of $3''$ (using the uvtaper parameter in tclean) cleaned to 2-$\sigma$." (2.2 Data reduction, calibration, and imaging)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: channels rebinned to 7.813 MHz (2x native), ~23.5 km/s at 99.5 GHz, nearest interpolation  
  > "We rebin the frequency dimension in channels of 7.813 MHz, i.e., $2\times$ the native spectral resolution of the observations." (2.2 Data reduction, calibration, and imaging)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Line search, fidelity and completeness derived in companion paper  
  > "We extensively discuss the line search approach in GL19, and summarize the main steps here for completeness." (4.1 Line search) [from (cite: gonzalezlopez19)]
- CO LF construction method  
  > "The CO luminosity functions are constructed in a similar way as in (cite: decarli16a) via a Monte Carlo approach" (4.4 CO luminosity functions) [from (cite: decarli16a)]
- Own reduction procedures  
  > "our own procedures (cite: aravena16a), which follow the general scheme of the official ALMA pipeline" (2.2 Data reduction, calibration, and imaging) [from (cite: aravena16a)]
- Line luminosity formula  
  > "The line fluxes are transformed into luminosities following (cite: carilli13)" (4.3 Line luminosities and corresponding H2 mass) [from (cite: carilli13)]

### Not stated but needed to reproduce (our reading)

- CASA version used
- Exact tclean parameters (cell, image size, niter, mask)
- Pipeline version and flagging details of the independent reduction
- Final rms per channel versus frequency across mosaic
- Details of findclumps settings (in GL19)
- Completeness and fidelity tables as a function of S/N and width
- Random seed and prior details for the Monte Carlo realizations; fitting sampler not named

## Analysis recipe

1. **Search for line candidates**: Matched-filter line search in cube without priors (findclumps); candidates S/N>5  
  > "This catalog of line candidates consists of 613 entries at S/N$>$5.0, 70 at S/N$>$5.5, 21 at S/N$>$6.0, and 15 at S/N$>$6.5." (4.1 Line search)
   - software: findclumps
   - fitting: _not stated_
   - validation: Negative-candidate statistics for fidelity; mock-line injection for completeness  
  > "The statistics of negative line candidates is used to model the noise properties of the cube" (4.1 Line search)
2. **Fidelity and completeness cuts**: Fidelity=1-P; keep fidelity>20% and completeness>20%; completeness from injected Gaussian mock lines  
  > "We limit our analysis to line candidates with fidelity $>$20%." (4.1 Line search)
   - fitting: _not stated_
   - validation: _not stated_
3. **Identify CO transition and redshift**: Use optical/NIR counterpart redshift to assign transition (z<0.8 CO(1-0), 0.8-1.9 CO(2-1), 1.9-3.2 CO(3-2)); otherwise bootstrap with probability proportional to volume; up to CO(4-3)  
  > "the line identification is performed through a bootstrap, where the probability of a line candidate to be CO(1-0), CO(2-1), CO(3-2), and CO(4-3) is proportional to the volume of universe sampled" (4.2 Line identification and redshifts)
   - fitting: _not stated_
   - validation: Compared CO and catalog redshifts; MUSE confirmation of overlaps  
  > "Our detailed analysis of the MUSE data confirms that these cases are examples of overlapping galaxies at different redshifts" (4.2 Line identification and redshifts)
4. **Convert fluxes to luminosities and H2 masses**: L' from Carilli & Walter formula; CO(1-0) via r_J1; M_H2 = alpha_CO/r_J1 * L'  
  > "Here we adopt $\alpha_{\rm CO}=3.6$ M$_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$ (cite: daddi10a)." (4.3 Line luminosities and corresponding H2 mass)
   - assumption: alpha_CO=3.6; no CMB correction (<~15%); intermediate excitation from Daddi15  
  > "we do not correct our measurements for the cosmic microwave background impact." (4.3 Line luminosities and corresponding H2 mass)
   - fitting: _not stated_
   - validation: _not stated_
5. **Build CO luminosity functions and rho(H2)**: 1000 Monte Carlo realizations; 0.5 dex bins shifted by 0.1 dex (5 times); completeness-corrected counts divided by comoving volume; rho(H2) from summed masses  
  > "The CO luminosity functions are created 1000 times" (4.4 CO luminosity functions)
   - fitting: _not stated_
   - validation: Robustness tests with secure sources and different CO excitation  
  > "Here we test the robustness of the CO LFs constraints from ASPECS LP 3 mm by creating different realizations of the CO LFs" (8 Robustness of the CO Luminosity Functions)
6. **Schechter fits to LFs**: Schechter fit in log form, alpha fixed to -0.2, lognormal priors (sigma 0.5 dex) on Phi* (1e-3) and L'* (10^9.5); all bins and five independent subsets  
  > "we assume broad ($\sigma$=$0.5$ dex) log normal distributions as priors in $\Phi_*$ and $L'_*$" (4.5 Analytical fits to the CO LFs)
   - fitting: Posterior medians and 14/86 percentiles; sampler not stated  
  > "The best fit value and the 1-$\sigma$ confidence levels of the fitted parameters are derived from the 50%, 14%, and 86% quartiles of the marginalized posterior distributions" (4.5 Analytical fits to the CO LFs)
   - validation: Consistency across binning choices  
  > "The fitted parameters do not show strong dependency on the choice of binning" (4.5 Analytical fits to the CO LFs)

## Software

- **CASA** : Pipeline calibration and tclean imaging  
  > "We imaged the 3 mm cube with natural weighting using the task tclean." (2.2 Data reduction, calibration, and imaging)
- **findclumps** : Line candidate search  
  > "here we refer to the results obtained with findclumps." (4.1 Line search)
- **MAGPHYS** : SED fitting of photometry  
  > "The photometric dataset is modeled with the high–$z$ extension of the Spectral Energy Distribution (SED) fitting code MAGPHYS" (3 Ancillary data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Drop in rho(H2) from z~1 to local | 6.5 | +1.8/-1.4 | dimensionless | 5 | drops by factor of $6.5_{-1.4}^{+1.8}$ to the value measured locally |
| Schechter log L'* CO(2-1), all bins | 10.09 | +0.10/-0.09 | log K km/s pc^2 | 6 | CO(2-1) / $-2.79_{-0.09}^{+0.09}$   / $10.09_{-0.09}^{+0.10}$ |
| Schechter log L'* CO(3-2), all bins | 10.60 | +0.20/-0.15 | log K km/s pc^2 | 6 | CO(3-2)   / $-3.83_{-0.12}^{+0.13}$   / $10.60_{-0.15}^{+0.20}$ |
| Fraction of total CO luminosity recovered at <z>=1.43, 2.61, 3.80 | 83%, 91%, 71% | not stated | percent | 6 | recover 83%, 91%, and 71% of the total CO luminosity at $\langle z\rangle$ = 1.43, 2.61, and at 3.80 |
| rho(H2) at z~1 | 7.1e7 | not stated | Msun Mpc^-3 | 5 | $z\sim 1$ \[$\rho$(H$_2$)$\approx$7.1$\times$10$^7$ Mpc$^{-3}$\] |

## Qualitative findings

- CO LFs at z>1 show an excess at the bright end relative to semi-analytic models  
  > "The CO LFs show an excess at the bright end compared with the predictions by semi–analytical models" (5 Discussion)

## Claim tuples

- H: Do CO luminosity functions evolve with redshift? | E: Schechter fits to ASPECS LP CO LFs at z=1-4 compared with local LFs | R: Knee higher by about an order of magnitude at z~2 than locally | F: Strong evolution of CO LF | **supported**
- H: How does cosmic molecular gas density evolve? | E: Sum of completeness-corrected H2 masses per redshift bin | R: Peak at z~1.5, drop of 6.5 to local | F: rho(H2) mirrors rho_SFR | **supported**
- H: Has star formation efficiency evolved? | E: Compare rho(H2) and rho_SFR evolution | R: Similar evolution | F: Little room for SFE evolution since z~3 (population average) | **supported**
- H: Are results robust to source inclusion and CO excitation? | E: Repeat with secure sources only and thermalized/Milky Way excitation | R: Strong evolution z=0 to z>1 persists | F: Robust | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: alpha_CO=2 would give a milder evolution (factor ~3)  
  > "the factor would be $\sim$3 if we adopt $\alpha_{\rm CO}$=2 M$_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$ for galaxies at $z>1$." (6 Conclusions)
- How they decided it was enough: _not stated_
- Limitation (authors): Local bin affected by cosmic variance and tiny volume  
  > "although this last measure is strongly affected by cosmic variance due to the small volume probed by ASPECS LP 3 mm" (4.5 Analytical fits to the CO LFs)
- Caveat (inferred, ours): Faint-end slope fixed at alpha=-0.2, not fitted
- Caveat (inferred, ours): Alpha_CO assumed constant; conclusions on SFE depend on it
- Caveat (inferred, ours): Line identification for ~25% of candidates is probabilistic
- Caveat (inferred, ours): Fiducial excitation from only 4 main-sequence galaxies
- Caveat (inferred, ours): Small volume and cosmic variance

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: Data from program 2016.1.00324.L  
  > "ALMA data: 2016.1.00324.L." (Acknowledgments)
- Missing: findclumps catalog and completeness/fidelity functions from GL19
- Missing: Own reduction scripts
- Missing: CASA version and tclean parameters
- Missing: Fitting sampler
- Data volume (inferred): ~100-300 GB raw for 17-pointing Band 3 mosaic; cubes tens of GB
- Score (inferred): 3/5, Clear high-level recipe and tables of LFs and line candidates, but line search and completeness depend on companion paper and custom code.
- Rediscovery candidate: no, Results rely on custom reduction and line-search/completeness products from GL19 that are not fully specified.

## Links

- Method: (cite: gonzalezlopez19) (Line search, fidelity and completeness)
- Method: (cite: decarli16a) (CO LF construction method)
- Companion: (cite: aravena19) (Main sequence context, alpha_CO from dust)
- Companion: (cite: boogaard19) (MUSE counterparts and galaxy properties)
- Companion: (cite: popping19) (Comparison with models)
- Related: ASPECS Pilot
- Related: COLDz
- Related: HUDF/XDF
- Related: MUSE HUDS

## Checks

```json
{
 "quotes": 58,
 "quotes_ok": 58,
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
  "facts": 77,
  "stated": 46,
  "rate": 0.597
 },
 "evidence_ok": true
}
```
