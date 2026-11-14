# New Millimeter CO Observations of the Gas-rich Debris Disks 49 Cet and HD 32297

`2019ApJ...884..108M` | The Astrophysical Journal 2019 | first author: Moór, Attila | arXiv: 1908.09685 | DOI: 10.3847/1538-4357/ab4272

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: debris_disks, astrochemistry
- Question: How much CO gas do the debris disks of 49 Cet and HD 32297 contain, and can a shielded secondary gas model explain it without primordial gas?  
  > "Adapting a recent secondary gas disk model that considers both shielding by carbon atoms and self-shielding of CO, we can explain the observed CO level in both systems." (abstract)
- Target **49 Cet**: coordinates _not stated_; z/distance 57.0±0.3 pc  
  > "49 Cet is an A1V-type star located at a distance of 57.0$\pm$0.3 pc (cite: brown2018; lindegren2018; cb2018)." (2 Targets); distance from Gaia DR2  
  > "49 Cet is an A1V-type star located at a distance of 57.0$\pm$0.3 pc (cite: brown2018; lindegren2018; cb2018)." (2 Targets)
- Target **HD 32297**: coordinates _not stated_; z/distance 132.3±1.0 pc  
  > "Based on Gaia DR2 astrometry the star is located 132.3$\pm$1.0 pc away (cite: brown2018; lindegren2018; cb2018)." (2 Targets); distance from Gaia DR2  
  > "Based on Gaia DR2 astrometry the star is located 132.3$\pm$1.0 pc away (cite: brown2018; lindegren2018; cb2018)." (2 Targets)

## Data provenance

- ALMA projects: 2016.2.00200.S
- bands: Band 6 (1.3 mm)  
  > "We obtained Band 6 observations of the J = 2$-$1 rotational line of $^{12}$CO, $^{13}$CO, and C$^{18}$O, as well as the 1.3 mm continuum." (3 Observations)
- frequencies and spectral setup: 13CO+C18O baseband: 976.6 kHz resolution, 1875 MHz bandwidth; 12CO: 244.1 kHz, 468.8 MHz; two continuum windows at 217.0 and 233.5 GHz  
  > "The $^{13}$CO and C$^{18}$O lines were measured in a single baseband with a spectral resolution of 976.6 kHz and a bandwidth of 1875 MHz" (3 Observations)
- continuum bandwidth: _not stated_
- arrays: ALMA 7-m Array, stand-alone  
  > "49 Cet and HD 32297 were observed using the ALMA 7-m Array in stand-alone mode" (3 Observations)
- configurations: _not stated_
- baselines: 49 Cet: 9-45 m; HD 32297: 9-49 m  
  > "Nine antennas were involved providing projected baseline lengths from 9 to 49 m (6.7–37 k$\lambda$)." (3 Observations)
- angular resolution: beams ~4-8 arcsec (see Table 1)  
  > "| Beam size ($''$) | 6$\ensuremath{''}$6$\times$5$\ensuremath{''}$1 | 7$\ensuremath{''}$8$\times$4$\ensuremath{''}$6 |" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 49 Cet July 2017; HD 32297 18 and 19 August 2017  
  > "Observations of 49 Cet were carried out in July 2017 with nine antennas" (3 Observations)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (not stated)
- Line: 13CO J=2-1 (not stated)
- Line: C18O J=2-1 (not stated)
- External data: Disk geometry, radii and surface density profile of 49 Cet from ALMA 12m data  
  > "we used the double power-law surface density profile model proposed by (cite: hughes2017)" (5.2 Shielding) [from (cite: hughes2017)]
- External data: HD 32297 belt radius/width, inclination, and flux from ALMA  
  > "Based on (cite: macgregor2018) for the outer belt of HD 32297 we adopted a radius ($R$) and width ($\Delta R$) of 100 au and 40 au, respectively." (5.2 Shielding) [from (cite: macgregor2018)]
- External data: CI 492 GHz line flux of 49 Cet (25.8±2.3 Jy km/s)  
  > "(cite: higuchi2017) derived 25.8$\pm$2.3 Jykms$^{-1}$ for the integrated line flux" (5.3.2 Modelling results) [from (cite: higuchi2017)]
- External data: Isotope ratios [12C]/[13C]=77, [16O]/[18O]=560  
  > "Taking isotope ratios of \[$^{12}$C\]/\[$^{13}$C\]=77 and \[$^{16}$O\]/\[$^{18}$O\]=560, typical in the local interstellar matter (cite: wilson1994)" (4.2 CO Line Emission) [from (cite: wilson1994)]
- Simulation/model as data: Shielded secondary gas disk 1-D model (upgraded Kral et al. 2018), grid of 100 models in Mdot_CO and alpha  
  > "we run a large grid of 100 models to explore the parameter space in $\dot{M}_{\rm CO}$ and $\alpha$." (5.3.2 Modelling results)

## Processing

### Calibration

- pipeline or manual: ALMA pipeline script delivered with the data, in CASA  
  > "using the pipeline script delivered with the data" (3 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Uranus (49 Cet; HD 32297 first block); J0510+1800 (HD 32297 second block)  
  > "quasar J0522-3627 and Uranus were targeted as bandpass and flux calibrators, respectively" (3 Observations)
- flux scale uncertainty: 10%  
  > "the typical ALMA calibration error (10% of the signal)" (4.1 Continuum Emission)
- self calibration: _not stated_

### Imaging

- task: tclean on continuum-subtracted visibilities  
  > "Then the `tclean` task was used to create spectral cubes of the three CO lines from the continuum subtracted calibrated visibilities adopting natural weighting." (3 Observations)
- deconvolver: _not stated_
- weighting robust: natural  
  > "The continuum maps were also cleaned using natural weighting." (3 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub, first-order polynomial on line-free channels  
  > "We used the CASA task `uvcontsub` to fit a first order polynomial to line-free channels in the *uv* space" (3 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: channel width 0.7 km/s for 12CO, 1.4 km/s for 13CO and C18O  
  > "The channel width was set to 0.7 km s$^{-1}$ for $^{12}$CO and to 1.4 km s$^{-1}$ for $^{13}$CO and C$^{18}$O lines." (3 Observations)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Secondary gas disk model with C0 and CO self-shielding  
  > "The model we use in this paper is based on the (cite: kral2018) model described above but it has been improved." (5.3.1) [from (cite: kral2018)]
- Mass loss rate formula for steady-state collisional cascade  
  > "we estimated the mass loss rate using the formula proposed by (cite: matra2017b)" (5.2 Shielding) [from (cite: matra2017b)]
- Dust opacity 2.3 cm2/g  
  > "Following (cite: beckwith1990), we adopted a value of 2.3 cm$^2$ g$^{-1}$ for the dust opacity." (4.1 Continuum Emission) [from (cite: beckwith1990)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for uvcontsub
- Clean thresholds, masks, image size and cell size
- Aperture sizes and velocity ranges for line flux extraction
- uvmodelfit starting parameters
- Details of the new 1-D shielded gas model code (to be presented in a forthcoming paper)
- Stellar masses used in the mass-loss formula
- LIME setup parameters

## Analysis recipe

1. **Calibrate and image**: Pipeline calibration, uvcontsub, tclean natural weighting cubes and continuum  
  > "Both data sets were calibrated and flagged with the ALMA reduction tool *Common Astronomy Software Applications* (cite: mcmullin2007) using the pipeline script delivered with the data." (3 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure continuum flux density**: uvmodelfit in the uv plane (elliptical Gaussian for 49 Cet, point source for HD 32297); CO channels flagged, weights via statwt  
  > "we applied the `uvmodelfit` task in CASA that allows to fit a single component source model to the *uv* data." (4.1 Continuum Emission)
   - software: CASA
   - fitting: single component model fit  
  > "we applied the `uvmodelfit` task in CASA that allows to fit a single component source model to the *uv* data." (4.1 Continuum Emission)
   - validation: Compared with previous millimeter photometry and ALMA high-resolution results  
  > "Our measurement is consistent with this prediction." (4.1 Continuum Emission)
3. **Derive dust masses**: Isothermal optically thin emission, M=F d^2/(B(T) kappa)  
  > "Assuming isothermal, optically thin dust emission and using our obtained millimeter flux densities, we estimated the dust mass of the disks" (4.1 Continuum Emission)
   - assumption: T_dust 56 K (49 Cet, blackbody at 100 au), 47 K (HD 32297); kappa=2.3 cm2/g at 1.33 mm  
  > "obtained a $T_{\rm dust}$ of 56 K." (4.1 Continuum Emission)
   - fitting: _not stated_
   - validation: _not stated_
4. **Measure integrated CO line fluxes**: Elliptical apertures matching the beam; sum channels with peak SNR>3; minimum aperture enclosing all emission; error from line-free spectrum plus 10% calibration  
  > "determine the integrated line flux by summing all consecutive channels that show significant line emission, i.e. where the peak SNR is higher than 3 (within the aperture)." (4.2 CO Line Emission)
   - fitting: _not stated_
   - validation: Compared with SMA, JCMT and ALMA literature fluxes  
  > "the derived integrated line flux of 1.02 Jy km s$^{-1}$ are consistent with our results" (4.2 CO Line Emission)
5. **Derive CO gas masses**: LTE mass from optically thin 13CO (49 Cet) or C18O (HD 32297) flux, scaled by isotope ratios to 12CO  
  > "We assumed that local thermodynamical equilibrium (LTE) holds and utilized the Boltzmann equation to compute the fractional populations." (4.2 CO Line Emission)
   - assumption: Excitation temperature 20 K; ISM isotope ratios  
  > "for the excitation temperature we adopted 20 K for both our disks." (4.2 CO Line Emission)
   - fitting: _not stated_
   - validation: Mass within factor of 2 for 7-74 K in LTE  
  > "for gas temperatures between 7 and 74 K the gas mass estimates would not exceed our derived CO masses by more than a factor of two" (4.2 CO Line Emission)
6. **Estimate required shielding factor**: Steady-state M_CO = Mdot_loss gamma t_ph eps_CO with t_ph~120 yr, gamma=0.27  
  > "we set a dissociation timescale of $\sim$120 yrs for unshielded CO molecules." (5.2 Shielding)
   - fitting: _not stated_
   - validation: _not stated_
7. **Fit shielded secondary gas disk model**: Grid of 100 models, 10x10 log in Mdot_CO (1e-3 to 1e-1 Mearth/Myr) and alpha (1e-5 to 1e-2); compare 13CO/C18O mass, inner CO radius, CI flux, 12CO flux  
  > "The grid is logarithmic for both parameters and comprised of 10 elements going from $10^{-3}$ to $10^{-1}$ M$_\oplus$/Myr for $\dot{M}_{\rm CO}$ and from $10^{-5}$ to $10^{-2}$ for $\alpha$." (5.3.2 Modelling results)
   - software: LIME
   - assumption: Gas temperature 20 K; pre-stirred disk; collisions start 5 Myr; run 40 Myr (49 Cet) and 25 Myr (HD 32297)  
  > "then our simulations are run for 40 Myr and 25 Myr for 49 Cet and HD 32297, respectively." (5.3.2 Modelling results)
   - fitting: Grid search with contours at 3 sigma  
  > "while the black dashed contours mark the 3$\sigma$ uncertainties" (5.3.2 Modelling results)
   - validation: Consistency with inner radius and CI flux  
  > "all three observational constraints, represented by the blue (inner CO disk radius), green (CI emission), and black ($^{13}$CO mass) lines, are simultaneously satisfied within their 3$\sigma$ uncertainties" (5.3.2 Modelling results)
8. **Assess gas-dust coupling**: Stokes number from Richert et al. formula using highest model gas surface density, beta=0.5  
  > "Then Eq. [\[eq:stokes\]](#eq:stokes) yields $St\sim$20 and $\sim$1 for the smallest bound grains in 49 Cet and HD 32297, respectively." (5.4 Gas-dust interaction)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibration, uvcontsub, tclean, uvmodelfit, statwt  
  > "CASA (cite: mcmullin2007), LIME (cite: brinch2010)" (Software)
- **LIME** : Model CI and 12CO line fluxes under LTE  
  > "In the computation of CI model fluxes we used the LIME radiation transfer code (cite: brinch2010) assuming LTE conditions." (5.3.2 Modelling results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 1.33 mm flux density 49 Cet | 5.3 | 0.7 | mJy | 2 | / $F_\nu$ at 1.33 mm (mJy) / 5.3$\pm$0.7(0.4) / 3.4$\pm$0.4(0.1) / |
| 1.33 mm flux density HD 32297 | 3.4 | 0.4 | mJy | 2 | / $F_\nu$ at 1.33 mm (mJy) / 5.3$\pm$0.7(0.4) / 3.4$\pm$0.4(0.1) / |
| Dust mass 49 Cet | 0.15 | 0.02 | Earth masses | 3 | we obtained dust masses of 0.15$\pm$0.02 M$_\oplus$ and 0.64$\pm$0.07 M$_\oplus$ for 49 Cet and HD 32297, respectively. |
| Dust mass HD 32297 | 0.64 | 0.07 | Earth masses | 3 | we obtained dust masses of 0.15$\pm$0.02 M$_\oplus$ and 0.64$\pm$0.07 M$_\oplus$ for 49 Cet and HD 32297, respectively. |
| 12CO(2-1) flux 49 Cet | 3.87 | 0.41 | Jy km/s | 4 | / $S_{\rm ^{12}CO}$ (Jy km s$^{-1}$) / 3.87$\pm$0.41(0.14) / 1.05$\pm$0.12(0.05) / |
| 13CO(2-1) flux HD 32297 | 0.50 | 0.07 | Jy km/s | 4 | / $S_{\rm ^{13}CO}$ (Jy km s$^{-1}$) / 1.68$\pm$0.19(0.09) / 0.50$\pm$0.07(0.04) / |
| C18O flux HD 32297 | 0.27 | 0.05 | Jy km/s | 4 | / $S_{\rm C^{18}O}$ (Jy km s$^{-1}$) / $<$0.26 / 0.27$\pm$0.05(0.04) / |
| 12CO mass 49 Cet | 1.11e-2 | 0.13e-2 | Earth masses | 5 | $M_{\rm ^{12}C^{16}O}$ = (1.11$\pm$0.13)$\times$10$^{-2}$ M$_\oplus$ and (7.4$\pm$1.3)$\times$10$^{-2}$ M$_\oplus$ for 49 Cet and HD 32297 |
| 12CO mass HD 32297 | 7.4e-2 | 1.3e-2 | Earth masses | 5 | $M_{\rm ^{12}C^{16}O}$ = (1.11$\pm$0.13)$\times$10$^{-2}$ M$_\oplus$ and (7.4$\pm$1.3)$\times$10$^{-2}$ M$_\oplus$ for 49 Cet and HD 32297 |
| 12CO/13CO flux ratio 49 Cet | 2.3 | 0.2 | dimensionless | 4 | $S_{\rm ^{12}CO} / S_{\rm ^{13}CO} = 2.3\pm0.2$ |
| Required shielding factor eps_CO | ~3600 (49 Cet), ~400 (HD 32297) | lower limits | dimensionless | 6 | yielded shielding factors of $\epsilon_{\rm CO}\sim$3600 and $\sim$400 for 49 Cet and HD 32297, respectively. |
| Best-fit CO production rate | ~0.005 (49 Cet), ~0.035 (HD 32297) | not stated | Earth masses/Myr | 7 | Our best fitting secondary gas models predict CO production rates of $\sim$0.005 M$_\oplus$/Myr and $\sim$0.035 M$_\oplus$/Myr for 49 Cet and HD 32297, respectively. |
| Stokes number for beta=0.5 grains | ~20 (49 Cet), ~1 (HD 32297) | upper limits | dimensionless | 8 | yields $St\sim$20 and $\sim$1 for the smallest bound grains in 49 Cet and HD 32297, respectively. |

## Qualitative findings

- 12CO is highly optically thick in both disks; 13CO likely thick in HD 32297 and thin in 49 Cet  
  > "Thus the measured values imply highly optically thick $^{12}$CO emission in both disks, while the $^{13}$CO line is probably optically thick in HD 32297 and optically thin in 49 Cet." (4.2 CO Line Emission)

## Claim tuples

- H: 49 Cet and HD 32297 have protoplanetary-level CO content | E: ALMA ACA 13CO and C18O observations, LTE mass | R: M_CO >0.01 Earth masses in both | F: Both are CO-rich debris disks similar to four known ones | **supported**
- H: A shielded secondary gas model can explain the CO without primordial gas | E: Grid of 1-D models matched to 13CO/C18O masses, inner radii and CI flux | R: Solutions exist with alpha<1e-4 and Mdot_CO ~0.005-0.03 Mearth/Myr | F: Secondary origin viable; primordial gas not excluded | **supported**
- H: Gas and small dust are coupled | E: Stokes number from model gas surface density | R: St ~1 for HD 32297, ~20 for 49 Cet (upper limits) | F: Coupling likely in HD 32297; undecided for 49 Cet | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Hybrid disk with primordial H2 shielding cannot be ruled out  
  > "we cannot rule out their presence based on our current results" (5.3.4)
- How they decided it was enough: _not stated_
- Limitation (authors): Gas temperature not constrained; LTE assumed; isotope ratios uncertain; dust opacity uncertain by factor 2-3  
  > "Our observations do not allow to derive reliable gas temperatures for the targeted disks." (4.2 CO Line Emission)
- Caveat (inferred, ours): Low-resolution data (~5-8 arcsec) leave disks mostly unresolved
- Caveat (inferred, ours): Model fits constrained mainly by one mass per target; degeneracy in alpha
- Caveat (inferred, ours): C18O in 49 Cet is an offset upper limit
- Caveat (inferred, ours): 12CO mass from ISM isotope ratios may be biased

## Reproducibility

- Data public (paper): ALMA project 2016.2.00200.S cited; archive data  
  > "in the framework of our Cycle 4 project (2016.2.00200.S, PI: Á. Kóspál)" (3 Observations)
- Products in archive: _not stated_
- Missing: Shielded gas model code (forthcoming paper)
- Missing: Exact aperture sizes and velocity ranges
- Missing: Imaging parameters
- Data volume (inferred): ~ few GB (small 7-m array datasets)
- Score (inferred): 5/5, Observational part reproducible from archive with pipeline; modelling relies on unreleased code.
- Rediscovery candidate: yes, Public data, simple imaging and flux/mass numerics are redoable; the modelling part is not.

## Links

- Method: (cite: kral2018) (Shielded secondary gas disk model)
- Method: (cite: matra2017b) (Mass loss rate formula)
- Companion: (cite: hughes2017) (ALMA 12m data of 49 Cet)
- Companion: (cite: macgregor2018) (ALMA data of HD 32297)

## Checks

```json
{
 "quotes": 70,
 "quotes_ok": 70,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2017.2.00200.S"
 ],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 86,
  "stated": 49,
  "rate": 0.57
 },
 "evidence_ok": true
}
```
