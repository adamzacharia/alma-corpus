# The Distribution and Excitation of CH<SUB>3</SUB>CN in a Solar Nebula Analog

`2018ApJ...859..131L` | The Astrophysical Journal 2018 | first author: Loomis, Ryan A. | arXiv: 1805.01458 | DOI: 10.3847/1538-4357/aac169

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: What are the distribution, column density and excitation of CH3CN in the TW Hya disk, and do disk chemistry models imply in situ formation sufficient to explain it and cometary abundances?  
  > "connecting gas phase measurements to cometary abundances first requires constraints on formation chemistry and distributions of these species." (abstract)
- Target **TW Hya**: coordinates _not stated_; z/distance 59.5 pc  
  > "A distance of 59.5 pc, PA of 155$\degree$, and stellar mass of 0.8 M$_{\odot}$ (to determine line broadening) were assumed for the radiative transfer" (3.3 Comparison to chemical models); distance from Kastner_1997; Qi_2004; Andrews_2012; Andrews_2016 (cited together with other assumed parameters)  
  > "A distance of 59.5 pc, PA of 155$\degree$, and stellar mass of 0.8 M$_{\odot}$ (to determine line broadening) were assumed for the radiative transfer" (3.3 Comparison to chemical models)

## Data provenance

- ALMA projects: 2016.1.01046.S
- bands: Band 6  
  > "TW Hya was observed on 29-Dec-2016 and 09-Jan-2017 in Band 6" (2.1 Observational details)
- frequencies and spectral setup: TDM continuum window at 237 GHz (2 GHz BW); FDM windows at 219.560, 220.740, 239.112 GHz, 58.59 MHz BW, 61 kHz channels  
  > "These spectral windows had bandwidths of 58.59 MHz and channel spacings of 61 kHz ($\sim$0.08 km s$^{-1}$)" (2.1 Observational details)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15-460 m (first execution), 15-384 m (second)  
  > "The first execution block included 43 antennas with projected baseline lengths between 15 and 460 m (11–353 k$\lambda$)." (2.1 Observational details)
- angular resolution: 1.05" x 0.83" (beam ~50-60 AU)  
  > "to force the synthesized beam to match that of the J=12–11 transitions (1$\ensuremath{''}$05 $\times$ 0$\ensuremath{''}$83)" (Observations - Results)
- max recoverable scale: _not stated_
- sensitivity: ~3.2 mJy/beam per 0.2 km/s channel  
  > "The rms of the image cubes was $\sim$3.2 mJy beam$^{-1}$ in each channel" (2.2 Results)
- time on source: 63 minutes total (32 + 31 min)  
  > "The on-source integration times were 32 and 31 minutes, respectively, for a total on-source integration time of 63 minutes." (2.1 Observational details)
- observing dates: 29-Dec-2016 and 09-Jan-2017  
  > "TW Hya was observed on 29-Dec-2016 and 09-Jan-2017 in Band 6" (2.1 Observational details)
- pi or archival as stated: _not stated_
- Line: CH3CN J=12-11 (K=0,1,2) (220747.3, 220743.0, 220730.3 MHz)
- Line: CH3CN J=13-12 (K=0-3) (239137.9, 239133.3, 239119.5, 239096.5 MHz)
- Line: C18O J=2-1 (not stated)
- External data: TW Hya density and temperature structure constrained by SED and HD  
  > "The assumed density and temperature structures, constrained by the TW Hya SED and previous HD observations (cite: Bergin_2013) in (cite: Cleeves_2015)" (3.3 Comparison to chemical models) [from Cleeves_2015]
- External data: Inclination 7 deg and PA 155 deg for deprojection  
  > "using an inclination of 7$\degree$ and PA of 155$\degree$ (cite: Qi_2004; Andrews_2012; Andrews_2016)" (2.2 Results) [from Qi_2004; Andrews_2012; Andrews_2016]
- External data: Spectral line data and rotational constants from SLAIM  
  > "Values for these rotational constants and all other spectral line data were taken from the Spectral Line Atlas of Interstellar Molecules (SLAIM)" (3.1 Disk-averaged analysis) [from Remijan_2007]
- External data: Cometary CH3CN/H2O abundance 7e-5 to 3e-4  
  > "cometary CH$_3$CN abundances 7$\times$10$^{-5}$–3$\times$10$^{-4}$ (cite: Mumma_2011)" (4.2) [from Mumma_2011]
- Simulation/model as data: Time-dependent disk chemical model (5970 reactions, 600 species) evolved 1 Myr, with RADMC-3D line radiative transfer and simulated ALMA observations  
  > "The chemical reaction network contains a total of 5970 reactions and 600 species." (3.3 Comparison to chemical models)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.3 (self-calibration)  
  > "one round of amplitude self-calibration in CASA version 4.3" (2.1 Observational details)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Callisto (first execution), Ganymede (second)  
  > "Callisto was used as the flux calibrator for the first execution, and Ganymede was used as the flux calibrator for the second execution." (2.1 Observational details)
- flux scale uncertainty: _not stated_
- self calibration: three rounds phase and one round amplitude self-cal on disk continuum, applied to lines  
  > "three rounds of phase self-calibration and one round of amplitude self-calibration in CASA version 4.3" (2.1 Observational details)

### Imaging

- task: CLEAN  
  > "The seven detected transitions were then individually imaged using `CLEAN` with natural weighting and a velocity resolution of 0.2 km s$^{-1}$" (2.2 Results)
- deconvolver: _not stated_
- weighting robust: Natural for CH3CN cubes; Briggs robust=0.5 for C18O filter cube  
  > "with Briggs weighting (robust=0.5), producing a high SNR image cube (peak SNR=32)" (2.2 Results)
- uv taper: outertaper 0.35" on J=13-12  
  > "(‘outertaper’ = 0$\ensuremath{''}$35)" (2.2 Results)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: ~3.2 mJy/beam per channel  
  > "The rms of the image cubes was $\sim$3.2 mJy beam$^{-1}$ in each channel" (2.2 Results)

### Inherited from earlier work

- Matched filtering line detection technique  
  > "matched filtering technique for identifying weak line emission, described in (cite: Loomis_2018)" (2.2 Results) [from Loomis_2018]
- Chemical model code and setup  
  > "time-dependent chemical model (cite: Fogel_2011; Cleeves_2014) evolved for 1 Myr" (3.3 Comparison to chemical models) [from Fogel_2011; Cleeves_2014; Cleeves_2015]

### Not stated but needed to reproduce (our reading)

- Line-free channels and continuum-subtraction details
- Image size, cell size, clean threshold and masks
- Self-calibration solution intervals
- Assumed linewidth Δv in rotational diagram
- Chemical model code and inputs not public; full network not given
- Whether pipeline calibration or manual scripts used

## Analysis recipe

1. **Detect lines by matched filtering**: C18O cube used as filter on CH3CN spectral windows with VISIBLE  
  > "This image cube was then used as a filter for the CH$_3$CN spectral windows using the `VISIBLE` code" (2.2 Results)
   - software: CLEAN, VISIBLE
   - fitting: _not stated_
   - validation: _not stated_
2. **Image transitions and extract fluxes**: Image each line, Keplerian mask convolved with beam (105 AU) to extract spectra, integrate 2.1-3.7 km/s, bootstrap uncertainty  
  > "Uncertainty on each flux measurement was determined through bootstrapping, repeating the extraction and integration 10,000 times" (2.2 Results)
   - software: CLEAN, CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Rotational diagram fit (disk-averaged and radial)**: LTE rotational diagram with optical depth correction, likelihood fit by MCMC  
  > "we use the affine-invariant Markov chain Monte Carlo (MCMC) code `emcee` (cite: Foreman-Mackey_2013) to fit the data" (3.1)
   - software: emcee
   - assumption: LTE excitation; solid angle of beam-convolved Keplerian mask  
  > "We initially assume local thermodynamic equilibrium (LTE) excitation" (3 CH3CN column density and excitation temperature)
   - fitting: emcee posteriors; 50th/16th/84th percentiles reported  
  > "parameters and uncertainties are listed as the 50th, 16th, and 84th percentiles from the marginalized posterior distributions" (3.1)
   - validation: Tau 0.002-0.012 confirms optically thin; both k-ladders fit consistently  
  > "Corresponding values of $\tau$ range between 0.002–0.012, confirming that these transitions of CH$_3$CN are optically thin." (3.1)
4. **Compare to chemical model**: Run model with/without grain-surface reactions, RADMC-3D radiative transfer, simulate ALMA with vis_sample, repeat rotational diagram analysis  
  > "Simulated ALMA observations were then calculated for each transition using the `vis`$\textunderscore$`sample` package" (3.3)
   - software: RADMC-3D, vis_sample
   - assumption: Distance 59.5 pc, PA 155 deg, inclination 8 deg, M*=0.8 Msun  
  > "An inclination of 8$\degree$ was assumed, which approximately accounts for the slight warp in the TW Hya disk" (3.3)
   - fitting: _not stated_
   - validation: Model-derived NT, Trot compared to observed within errors  
  > "both agree with the observed column density of N$_T$=1.45$^{+0.19}_{-0.15}\times$10$^{12}$ cm$^{-2}$" (3.3)

## Software

- **CASA** 4.3: self-calibration, CLEAN imaging  
  > "one round of amplitude self-calibration in CASA version 4.3" (2.1 Observational details)
- **VISIBLE** v0.1.0: matched filter line detection  
  > "using the `VISIBLE` code" (2.2 Results)
- **emcee** : MCMC fit of rotational diagrams  
  > "we use the affine-invariant Markov chain Monte Carlo (MCMC) code `emcee`" (3.1)
- **RADMC-3D** : simulated emission from chemical model  
  > "using the radiative transfer code RADMC-3D" (3.3)
- **vis_sample** : simulated ALMA observations  
  > "Simulated ALMA observations were then calculated for each transition using the `vis`$\textunderscore$`sample` package" (3.3)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Disk-averaged CH3CN column density | 1.45e12 | +0.19/-0.15 e12 | cm^-2 | 3 | disk-averaged column density of N$_T$=1.45$^{+0.19}_{-0.15}\times10^{12}$ cm$^{-2}$ |
| Disk-averaged rotational temperature | 32.7 | +3.9/-3.4 | K | 3 | T$_{rot}$=32.7$^{+3.9}_{-3.4}$ K |
| Radial NT profile range | 5 to 0.9e12 | not stated | cm^-2 | 3 | The observed N$_T$ profile decreases with radius from 5 to 0.9$\times10^{12}$ cm$^{-2}$. |
| Model disk-averaged NT and Trot | 1.49e12 cm^-2; 36.6 K | not stated | cm^-2; K | 4 | N$_T$=1.49$\times$10$^{12}$ cm$^{-2}$ and rotational temperature of T$_{rot}$=36.6 K |

## Qualitative findings

- Trot is flat (30-34 K) across the disk, implying emission from z/r~0.3  
  > "T$_{rot}$ shows a flat radial profile, ranging between 30–34 K" (3.2)

## Claim tuples

- H: Grain-surface chemistry dominates CH3CN formation | E: Compared models with and without grain-surface reactions to observations | R: Gas-phase-only model underpredicts fluxes by over an order of magnitude; full model within factor 2 | F: Grain-surface reactions likely dominate; in situ chemistry suffices for disk column density | **supported**
- H: In situ chemistry reproduces cometary CH3CN/H2O in the midplane | E: Computed CH3CN(gr)/H2O(gr) in the model | R: Cometary values reached only at z/r>0.04, not at midplane | F: Vertical mixing or inheritance needed | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Limited spatial resolution prevents robust quantitative comparison of gas-phase vs grain-surface contributions  
  > "The limited spatial resolution of our observations and the caveats of our chemical model presented in §4.1.3, however, prevent a more robust quantitative analysis" (4.1.2)
- Caveat (inferred, ours): Summary section quotes NT=1.82e12 and Trot=29.3 K, inconsistent with abstract/results
- Caveat (inferred, ours): Single-source, model not fit to data
- Caveat (inferred, ours): LTE assumption and a single Trot
- Caveat (inferred, ours): Photodesorption and C/O assumptions affect conclusions

## Reproducibility

- Data public (paper): ALMA project data cited; VISIBLE is public  
  > "VISIBLE is publicly available at https://github.com/AstroChem/VISIBLE" (Software)
- Products in archive: _not stated_
- Code: VISIBLE public on GitHub  
  > "VISIBLE is publicly available at " (footnote)
- Missing: Chemical model code and exact setup
- Missing: Imaging parameters, line-free channels
- Missing: Assumed linewidth
- Data volume (inferred): ~10-30 GB
- Score (inferred): 3/5, Data and recipe mostly described and public tools used, but chemical model and several imaging details are missing.
- Rediscovery candidate: yes, Public data, rotational diagram analysis numeric and well specified, though model comparison is hard to redo.

## Links

- Method: Loomis_2018 (Matched filter line detection and vis_sample)
- Companion: Bergner_2018 (CH3CN detection in other disks)

## Checks

```json
{
 "quotes": 53,
 "quotes_ok": 53,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 42,
  "rate": 0.583
 },
 "evidence_ok": true
}
```
