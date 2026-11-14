# ALMA suggests outflows in z ∼ 5.5 galaxies

`2018MNRAS.473.1909G` | Monthly Notices of the Royal Astronomical Society 2018 | first author: Gallerani, S. | arXiv: 1604.05714 | DOI: 10.1093/mnras/stx2458

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: high_z_galaxies
- Question: Do the [CII] 158um lines of z~5.5 star-forming galaxies show broad wings indicating starburst-driven outflows?  
  > "We present the first attempt to detect outflows from galaxies approaching the Epoch of Reionization (EoR) using a sample of 9 star-forming" (abstract)
- Target **9 z~5.5 star-forming galaxies from Capak et al. 2015 (HZ1, HZ2, HZ3, HZ4, HZ6, HZ7, HZ8, HZ8W, HZ9)**: coordinates _not stated_; z/distance 5.2 ≲ z ≲ 5.7  
  > "We consider HZ8 and its “companion” galaxy HZ8W as two distinct sources." (ALMA observations); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00523.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.6 arcsec (~3.7 kpc)  
  > "obtained with ALMA at an angular resolution of[^1] $\sim$0.6” by (cite: Capak15)" (ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Data from Capak et al. 2015  
  > "We have analyzed the \[CII\] emission lines obtained with ALMA (cite: Capak15)" (Conclusions)
- Line: [CII] 158 um (not stated)
- External data: [CII] ALMA spectra and sample of galaxies (SFR, stellar masses)  
  > "spectra of the \[CII\]158$\mu$m line have been obtained with ALMA at an angular resolution of[^1] $\sim$0.6” by (cite: Capak15)" (ALMA observations) [from Capak P. L. et al., 2015, Nature, 522, 455]
- External data: Zoom-in RAMSES simulation of the galaxy Dahlia  
  > "These simulations are fully described in (cite: pallottini:2017)" (Numerical simulations) [from (cite: pallottini:2017)]
- Simulation/model as data: RAMSES zoom-in simulation of z~6 galaxy Dahlia (halo ~1e11 Msun, SFR~100 Msun/yr) used to compute outflow rate and radial velocity PDF  
  > "we carry out a zoom-in simulation of a $z\sim 6$ dark matter (DM) halo of mass $\sim10^{11} \rm M_\odot$" (Numerical simulations)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ganymede, Pallas, Callisto (~5% accuracy); bandpass J0538-4405, J0522-3627, J1037-2934; phase J1058+0133, J1008+0621  
  > "Ganymede, Pallas, and Callisto were used for the flux calibration (providing an accuracy of $\sim$5%)" (footnote 3)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs Robust = 1 (natural, Robust = 2, for HZ6)  
  > "A Briggs flexible weighting scheme (Robust = 1) was adopted" (ALMA observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum image from three line-free ~2 GHz base-bands, model subtracted in uv plane, 0th order polynomial  
  > "The continuum subtraction was done by creating a continuum image from the three line-free $\sim$2 GHz base-bands, and then subtracting a model thereof in the visibility plane." (ALMA observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Data reduction and observations from Capak et al. 2015  
  > "have been obtained with ALMA at an angular resolution of[^1] $\sim$0.6” by (cite: Capak15)" (ALMA observations) [from (cite: Capak15)]
- Outflow gas mass from [CII] luminosity obtained as in Maiolino et al. 2012  
  > "is the total mass of the outflowing gas, obtained as in (cite: Maiolino12)" (Conclusions) [from (cite: Maiolino12)]

### Not stated but needed to reproduce (our reading)

- CASA version
- Spectral channel width and spectral extraction aperture per galaxy
- Exact conversion from [CII] luminosity to outflow mass
- Random seeds and ranges used for the Monte Carlo realization selection
- Sample SFRs per galaxy
- Gaussian fitting algorithm

## Analysis recipe

1. **Fit Gaussians and compute normalized residuals**: Fit each [CII] line with a Gaussian (FWHM, peak, v0); noise from std at |v|>700 km/s; R=(Fobs-Fmod)/sigma_n  
  > "we compute the residuals by subtracting the best fitting model from the observed spectrum, and normalize them to the noise" (Method)
   - parameter: v_cont = 700 km/s  
  > "where[^4] $v_{\rm cont}=700~\rm km s^{-1}$" (Method)
   - fitting: _not stated_
   - validation: Standard normal deviates G processed identically as a sanity check  
  > "As a sanity check of the method, for each galaxy, we also compute a *standard normal deviate*" (Method)
2. **Stack residuals and test against Gaussian noise**: Average residuals of 9 galaxies; compare CDF with erf via KS and Anderson-Darling tests  
  > "we apply the Kolmogorov-Smirnov (KS) test to our data" (Method)
   - fitting: _not stated_
   - validation: 500 standard normal deviate realizations  
  > "the gray-shaded region is the result of the CDFs computed for 500 *standard normal deviates*" (Method)
3. **Compare outflow, satellite and rotating-disk scenarios**: 500 Monte Carlo synthetic spectra per scenario in sub-samples of 9, same fit/stack procedure, KS test against observed CDF  
  > "we produce 3 sets of 500 Monte Carlo simulations of \[CII\] emission lines with different profiles" (Interpreting the flux excess)
   - parameter: Parameter ranges in Table 2  
  > "Parameter ranges for Monte Carlo simulations of synthetic profiles" (Table 2)
   - assumption: One satellite per beam; halo occupation model  
  > "we assume that, for each of the galaxies, the ALMA beam encloses a number of satellites $N_{\rm sat}=1$" (Satellites)
   - fitting: _not stated_
   - validation: Compared with simulated Gaussian peak/sigma distributions  
  > "The nice agreement between the observed values and the synthetic ones shows that the simulated lines have properties consistent with data." (Results)
4. **Estimate outflow rate and loading factor**: Mdot = v_outfl M_outfl / R_outfl  
  > "$$\begin{equation}
\dot{M}=v_{\rm outfl} \frac{M_{\rm outfl}}{R_{\rm outfl}},
\end{equation}$$" (Conclusions)
   - parameter: v_outfl ~500 km/s; R_outfl ~1.9 kpc  
  > "we assume that the spatial extent of the outflow is of the order of the radius of the deconvolved \[CII\] emission sizes, i.e. $\sim$ 1.9 kpc" (Conclusions)
   - fitting: _not stated_
   - validation: Compared with local starbursts and RAMSES Dahlia simulation  
  > "The simulation outcomes support our interpretation of the ALMA data" (Conclusions)

## Software

- **CASA** : Data reduction and analysis  
  > "The Common Astronomy Software Application (CASA) was used for data reduction and analysis." (ALMA observations)
- **RAMSES** : Zoom-in hydrodynamic simulation of Dahlia  
  > "Adaptive Mesh Refinement (AMR) code RAMSES (cite: teyssier:2002)" (Numerical simulations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Stacked flux excess | ~0.5 mJy over ~1000 km/s | not stated | mJy | 2 | We find a flux excess of $\sim 0.5$ mJy extended over $\sim 1000$ km s$^{-1}$. |
| Mean broad component peak flux | 0.4 | 0.1 | mJy | 3 | $\langle F_{\rm peak}^{\rm broad}\rangle=0.4\pm 0.1 \rm ~mJy$ |
| Mean broad component sigma | 360 | 140 | km/s | 3 | $\langle\sigma^{\rm broad}\rangle=360\pm 140 \rm ~km~s^{-1}$ |
| Outflow rate | 54 | 23 | Msun/yr | 4 | we infer an outflow rate of $\rm \dot{M}=54\pm23~ M_{\odot}~yr^{-1}$ |
| Mass loading factor | 1.7 | 1.3 | dimensionless | 4 | $\eta=\dot{M}/SFR=1.7\pm1.3$ |
| KS distance, outflow scenario | 0.05 (P_KS=1.0) | not stated | dimensionless | 3 | We find that the distance from the observed CDF is minimized by the *Outflow* scenario ($D_{\rm KS}=0.05$). |

## Qualitative findings

- Satellite emission cannot be excluded as a partial contribution; rotating disk disfavoured  
  > "we cannot exclude that part of the flux excess we detect is due to emission from satellite galaxies" (Results)

## Claim tuples

- H: [CII] lines of the sample are purely Gaussian | E: Gaussian fits, stacked residuals, KS and AD tests | R: Flux excess ~0.5 mJy over ~1000 km/s; R_tot CDF differs from the normal deviate | F: Null hypothesis rejected | **supported**
- H: Excess is due to starburst-driven outflows | E: Monte Carlo of outflow, satellite and disk profiles | R: Outflow gives D_KS=0.05, satellites 0.10, disk 0.13 | F: Outflow broad wings most probable explanation | **partially**
- H: Inferred outflow is consistent with simulations and local starbursts | E: Mdot estimate and comparison with Dahlia | R: Mdot=54±23 Msun/yr; eta=1.7±1.3; Dahlia ~30 Msun/yr | F: Consistent | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Satellite galaxies and rotating disk considered as alternative explanations  
  > "a multi-peaked profile might result from the collective emission of satellite galaxies" (Interpreting the flux excess)
- How they decided it was enough: _not stated_
- Limitation (authors): ALMA data quality insufficient for individual line profile analysis  
  > "The quality of the ALMA data is not sufficient for a detailed analysis of the \[CII\] line profile in individual galaxies." (abstract)
- Limitation (authors): Stack of 9 galaxies compared with a single simulated galaxy  
  > "we are comparing an observed signal stacked from 9 galaxies with a single synthetic galaxy" (Conclusions)
- Caveat (inferred, ours): Broad wings may result from continuum residuals or bandpass systematics
- Caveat (inferred, ours): Stacking only 9 sources with an ad hoc mean outflow geometry; Mdot uncertainty is rough
- Caveat (inferred, ours): Outflow velocity and radius choices are assumed

## Reproducibility

- Data public (paper): ALMA data cited with project code  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00523.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: CASA version and exact reduction scripts
- Missing: Monte Carlo seeds
- Missing: Per-galaxy spectral extraction details
- Data volume (inferred): ~tens of GB raw for the 2012.1.00523.S dataset
- Score (inferred): 3/5, Public data and a clear statistical method, but several processing and fitting details are missing.
- Rediscovery candidate: yes, Public archival data, a simple residual-stacking recipe, and numeric results.

## Links

- Method: (cite: Maiolino12) (Outflow mass from line luminosity)
- Method: (cite: deblok:2014) (Double-horned profile model)
- Companion: (cite: Capak15) (Source of the ALMA [CII] data)
- Companion: (cite: pallottini:2017) (Simulation of Dahlia)

## Checks

```json
{
 "quotes": 43,
 "quotes_ok": 43,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 31,
  "rate": 0.443
 },
 "evidence_ok": true
}
```
