# η Carinae Baby Homunculus Uncovered by ALMA

`2014ApJ...791...95A` | The Astrophysical Journal 2014 | first author: Abraham, Zulema | arXiv: 1406.6297 | DOI: 10.1088/0004-637X/791/2/95

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: stellar_physics, milky_way_ism
- Question: What are the nature and physical parameters of the compact ionized region around eta Carinae, as probed by mm/submm continuum and H and He recombination lines?  
  > "Combined with fittings to the continuum, we were able to constrain the shell size, radius, density, temperature and velocity." (abstract)
- Target **eta Carinae**: coordinates _not stated_; z/distance 2.3 kpc  
  > "assuming a distance to $\eta$ Carinae of 2.3 kpc" (1 Introduction); distance from assumed  
  > "assuming a distance to $\eta$ Carinae of 2.3 kpc" (1 Introduction)

## Data provenance

- ALMA projects: 2011.0.00497.S
- bands: 92 GHz (3.3 mm), 225 GHz (1.3 mm), 291 GHz (1.0 mm), 672 GHz (447 um)  
  > "in four bands, centered at 92 GHz (3.3 mm), 225 GHz (1.3 mm), 291 GHz (1.0 mm) and 672 GHz (447 $\ensuremath{\mu}m$)" (2 Observations)
- frequencies and spectral setup: 7.5 GHz correlator bandwidth in four spectral windows, 488 kHz resolution (1.5, 0.65, 0.5, 0.22 km/s)  
  > "The 7.5 GHz bandwidth of the correlator was divided in four spectral windows, with resolution of 488 kHz" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: 23 antennas, Cycle 0 Early Science  
  > "Twenty three antennas were used in the observations, with a maximum baseline of 375 m." (2 Observations)
- configurations: _not stated_
- baselines: maximum 375 m  
  > "Twenty three antennas were used in the observations, with a maximum baseline of 375 m." (2 Observations)
- angular resolution: 2.88'' to 0.45''  
  > "with a resolution that varied from $2.88\ensuremath{''}$ to $0.45\ensuremath{''}$ for the lower and higher frequencies respectively" (abstract)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2012 November 4 and 5  
  > "on 2012 November 4 and 5" (2 Observations)
- pi or archival as stated: _not stated_
- Line: H H42alpha (85.7 GHz)
- Line: H H40alpha (99.0 GHz)
- Line: H H28alpha (284.3 GHz)
- Line: H H21alpha (662.4 GHz)
- Other facility **Itapetinga radiotelescope**: 43 GHz flux density 8.7±1 Jy, 2012 Oct 30  
  > "a 43 GHz (7 mm) observation obtained at the same epoch with the Itapetinga radiotelescope ($2.4\ensuremath{'}$ resolution), which gave a flux density of $8.7\pm 1$ Jy." (3.1 The continuum spectrum)
- External data: Historical optical light curve used to date the ejection to ~1941  
  > "looking at the historical light curve at optical wavelengths compiled by (cite: fer09), shown in fig. 9" (4.3 The Baby Homunculus) [from (cite: fer09)]
- External data: NLTE departure coefficients b_n  
  > "calculated by (cite: sto95) for several values of $n$, $N_e$ and $T_e$" (Appendix B) [from (cite: sto95)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan  
  > "J1038-5311 and Titan for phase calibration and the latter also for flux calibration" (2 Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CLEAN in CASA  
  > "We used the CLEAN algorithm present in CASA (Common Astronomy Software Applications) to construct the images." (2 Observations)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 0.45'', 0.17'', 0.13'', 0.05'' for 92, 225, 291, 672 GHz  
  > "The cell sizes used were $0.45\ensuremath{''}$, $0.17\ensuremath{''}$, $0.13\ensuremath{''}$ and $0.05\ensuremath{''}$" (2 Observations)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum maps from line-free channels; continuum subtracted from UV data for line cubes  
  > "after subtracting the continuum contribution from the UV data" (2 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Receiver and observing mode of Itapetinga 43 GHz data  
  > "The characteristics of the receiver and the observing mode are described in (cite: abr05)." (2 Observations) [from (cite: abr05)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration procedure
- weighting/robust, deconvolver, masks, iterations, thresholds
- line-free channel ranges
- flux scale accuracy/Titan model
- fitting procedure and goodness-of-fit criterion for the shell model
- code for radiative transfer model
- quantitative uncertainties on model parameters

## Analysis recipe

1. **Image continuum and line cubes**: CLEAN in CASA; continuum from line-free channels, UV continuum subtraction, cubes at 2 km/s (10 km/s for H21alpha)  
  > "Line map cubes were obtained with velocity resolution of 2 km s$^{-1}$ for all lines, except for H21$\alpha$ and He21$\alpha$" (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit continuum spectrum with shell model**: Spherical shell radiative transfer with free-free emission in cells; fit Ne and R for given Te and DeltaR/R  
  > "determined the electron density and radius necessary to fit the observed spectrum" (3.1 The continuum spectrum)
   - parameter: Te = 1e4, 1.5e4, 2e4 K; DeltaR/R from 0.05 to 1  
  > "for three values of $T_e$: $10^4$, $1.5\times 10^4$ and $2\times 10^4$ K" (3.1 The continuum spectrum)
   - assumption: Spherical symmetry; constant density and temperature; H fully ionized, He as He+ (Ni=Ne); distance 2.3 kpc  
  > "We assumed that H is completely ionized and He is in the form of He$^+$, implying that $N_i = N_e$." (3.1 The continuum spectrum)
   - fitting: _not stated_
   - validation: Good fits for all Te and DeltaR/R combinations; Fig. 5 examples  
  > "Good fits were obtained for all combinations of electron temperature and shell width" (3.1 The continuum spectrum)
3. **Model recombination line profiles in NLTE**: Solve line+continuum transfer with expansion velocity gradient, Doppler broadening with TD=Te; compare model/observed peak flux ratios  
  > "we assumed $T_D = T_e$ in equation (B6) and introduced an expansion velocity, with a linear gradient across the shell" (3.2 Recombination line emission)
   - parameter: Te 1.4e4-2e4 K; DeltaR/R = 0.05, 0.1, 0.2  
  > "for values of $T_e$ ranging from $1.4\times 10^4$ K to $2\times 10^4$ K and for three values of $\Delta R/R$: 0.05, 0.1 and 0.2" (3.2 Recombination line emission)
   - assumption: Pressure broadening neglected  
  > "for that reason presure broadening was not included in the calculations" (Appendix B)
   - fitting: Best model chosen where model/observed peak ratios approach unity for all lines  
  > "the ratio becomes close to unity for all lines for $T_e \sim 1.7\times 10^4$ and $\Delta R/R \sim 0.1$" (3.2 Recombination line emission)
   - validation: Compared with LTE models and He lines; poorer fit for H40alpha and H42alpha  
  > "The fitting is not so good for the H40$\alpha$ and H42$\alpha$ lines" (3.2 Recombination line emission)
4. **Wind-blown shell dynamics**: Weaver et al. wind-driven shell then snow-plow expansion; derive mass-loss rate and wind velocity vs. ambient density  
  > "The dynamical evolution of an expanding shell driven by a continuous stellar wind is well described by the classical work of (cite: weaver77)." (3.4 Dynamical evolution)
   - parameter: t2 = 71 yr; ambient density 1e5 and 1e6 cm^-3  
  > "it was taken as 71 yr, linking the beginning of the ejection to the luminosity increase observed in 1941" (3.4 Dynamical evolution)
   - fitting: _not stated_
   - validation: Predicted v2=19 km/s agrees with model expansion velocity  
  > "we immediately obtain $v_2(t_2)= 19$ km s$^{-1}$ in excellent agreement with the expansion velocity derived for the shell" (3.4 Dynamical evolution)

## Software

- **CASA** : CLEAN imaging  
  > "We used the CLEAN algorithm present in CASA (Common Astronomy Software Applications) to construct the images." (2 Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum flux density 92.5 GHz | 28.4 | 0.03 | Jy | 1 | / 92.5  / $2.88\times 1.83$ /  54  /  20.9   / $28.4 \pm 0.03$ / |
| Continuum flux density 671.7 GHz | 40.2 | 0.09 | Jy | 1 | / 671.7 / $0.45\times 0.32$ /  42  /  22.1   / $40.2 \pm 0.09$ / |
| Shell electron temperature | 1.68e4 | not stated | K | 3 | $T=1.68\times 10^4$ K and a relative shell width $\Delta R/R = 0.1$ |
| Shell electron density | 1.25e7 | not stated | cm^-3 | 3 | $N_e = 1.25 \times 10^7$ cm$^{-3}$ and $R= 2.2 \times 10^{-3}$ pc |
| Shell radius | 2.2e-3 | not stated | pc | 3 | $N_e = 1.25 \times 10^7$ cm$^{-3}$ and $R= 2.2 \times 10^{-3}$ pc |
| Bulk velocity of shell (LSR) | -52 | not stated | km/s | 3 | In all cases the bulk velocity of the model is $-52$ km s$^{-1}$. |
| Expansion velocity inner/outer shell | 60 / 20 | not stated | km/s | 3 | expansion velocity of 60 km s$^{-1}$ in the internal part of the shell and of 20 km s$^{-1}$ in the external part |
| Line width H42alpha to H21alpha | 29 to 40 | not stated | km/s | 1 | The line width varies between 29 km s$^{-1}$ for the H42$\alpha$ line to 40 km s$^{-1}$ for the H21$\alpha$ line |

## Qualitative findings

- Continuum is unresolved at all frequencies and turns over between 100 and 230 GHz, indicating a compact HII region rather than an optically thin wind  
  > "indicating that it arises in a compact H II region instead of an ionized wind" (1 Introduction)

## Claim tuples

- H: Is the mm/submm emission from a compact ionized shell rather than an ionized wind? | E: Fit continuum spectrum from 43 to 672 GHz with a spherical shell model | R: Shell R~0.0022 pc, Ne~1.25e7 cm^-3, Te~1.7e4 K reproduces spectrum | F: Emission arises in a compact shell | **supported**
- H: Can the line profiles be explained by the shell? | E: NLTE line transfer with expansion velocity gradient | R: Profiles fit only with expansion of 60 to 20 km/s | F: Expanding shell with slow shock | **supported**
- H: Is the shell a new ejection (Baby Homunculus) related to the Weigelt blobs? | E: Compare shell parameters with blobs and light curve; wind-blown shell dynamics | R: Matching velocity, density, temperature; ejection ~1941 | F: Shell ejected ~1941 and includes Weigelt blobs | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Turbulence added to thermal velocity could not reproduce line profiles  
  > "We were not able to reproduce the line profiles adding only turbulence to the thermal velocity" (3.2 Recombination line emission)
- How they decided it was enough: _not stated_
- Limitation (authors): Departure from spherical symmetry would make the solution degenerate; finer resolution needed  
  > "the velocity distribution necessary to fit the line profiles will depend on the density and temperature distributions and the solution will be degenerate." (3.2 Recombination line emission)
- Limitation (authors): Wind parameters during eruption cannot be strictly constrained  
  > "we cannot strictly constrain the wind parameters during the eruption" (3.4 Dynamical evolution)
- Caveat (inferred, ours): No formal fit or uncertainties; parameters chosen by eye
- Caveat (inferred, ours): Degenerate model parameters with unresolved source
- Caveat (inferred, ours): Ejection date of 1941 is inferred from light curve, not independent
- Caveat (inferred, ours): Source unresolved so shell geometry untested

## Reproducibility

- Data public (paper): ALMA project 2011.0.00497.S cited; public status not stated  
  > "This paper makes use of the following ALMA data: 2011.0.00497.S." (footnote 1)
- Products in archive: _not stated_
- Missing: Model code for the shell radiative transfer
- Missing: CASA version and imaging parameters
- Missing: Fit criteria
- Data volume (inferred): ~10-50 GB (Cycle 0, four bands)
- Score (inferred): 4/5, Data identified and equations given, but imaging and fitting details lack, and model code is not released.
- Rediscovery candidate: no, Imaging recipe incomplete and the model fit is not specified enough to redo precisely.

## Links

- Method: (cite: bro72) (free-free and line absorption coefficients)
- Method: (cite: sto95) (NLTE departure coefficients)
- Method: (cite: weaver77) (wind-blown shell dynamics)
- Companion: (cite: cox95b) (earlier mm recombination lines with NLTE evidence)
- Companion: (cite: meh10) (Weigelt blob photoionization models)

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
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 36,
  "rate": 0.522
 },
 "evidence_ok": true
}
```
