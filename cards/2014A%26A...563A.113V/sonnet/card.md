# Warm formaldehyde in the Ophiuchus IRS 48 transitional disk

`2014A&A...563A.113V` | Astronomy and Astrophysics 2014 | first author: van der Marel, N. | arXiv: 1402.0392 | DOI: 10.1051/0004-6361/201322960

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Can complex molecules, especially H2CO, be detected in the transitional disk Oph IRS 48, and what are their abundances and formation routes?  
  > "to search for complex molecules in regions where planetesimals are forming" (abstract)
- Target **Oph IRS 48**: coordinates RA 16h27m37.18s, Dec -24d30m35.3s (J2000)  
  > "Oph IRS 48 ($\alpha_{\rm 2000}=$16$^{\rm h}$27$^{\rm m}$37.18s, $\delta_{\rm 2000}=$-24$^\circ$ 30$'$ 35.3$''$)" (2 Observations); "in the Ophiuchus molecular cloud (distance 125 pc)" (1 Introduction); z/distance 125 pc  
  > "Oph IRS 48 ($\alpha_{\rm 2000}=$16$^{\rm h}$27$^{\rm m}$37.18s, $\delta_{\rm 2000}=$-24$^\circ$ 30$'$ 35.3$''$)" (2 Observations); "in the Ophiuchus molecular cloud (distance 125 pc)" (1 Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00635.S
- bands: Band 9 (~680-690 GHz)  
  > "was observed using the Atacama Large Millimeter/submillimeter Array (ALMA) in Band 9 in the extended configuration in Early Science Cycle 0." (2 Observations)
- frequencies and spectral setup: 4 spectral windows centred at 674.00, 678.84, 691.47, 693.88 GHz; 3840 channels each, 488 kHz spacing, 1875 MHz bandwidth, 0.21 km/s resolution  
  > "The spectral setup contained four spectral windows, centered on 674.00 , 678.84, 691.47, and 693.88 GHz." (2 Observations); "Each spectral window consists of 3840 channels, a channel separation of 488 kHz, and thus a bandwidth of 1875 MHz" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: up to 390 m, 18-21 antennas  
  > "18 to 21 antennas with baselines of up to 390 meters were used." (2 Observations)
- angular resolution: 0.32" x 0.21" (38x25 AU), PA 96 deg  
  > "The resulting images have a synthesized beam of 0.32” $\times$ 0.21” or 38$\times$25 AU" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: rms 20-30 mJy/beam per 1 km/s channel  
  > "The final rms level was 20-30 mJy beam$^{-1}$ per 1 km s$^{-1}$ channel, depending on the exact frequency." (2 Observations)
- time on source: three execution blocks of 1.7 hours each  
  > "The observations were taken in three observation execution blocks of 1.7 hours each in June and July 2012." (2 Observations)
- observing dates: June and July 2012  
  > "in June and July 2012" (2 Observations)
- pi or archival as stated: _not stated_
- Line: H2CO 9(1,8)-8(1,7) (674.80978 GHz)
- Line: CH3OH 4(2,2)-3(1,3) (678.78546 GHz)
- Line: H13CO+ 8-7 (693.87633 GHz)
- Line: CN N=6 11/2-5 11/2 (678.84488 GHz)
- External data: Best-fitting DALI physical disk model (gas/dust structure, temperature, CO abundance) for IRS 48  
  > "We used the best-fitting model of the gas structure from (cite: BruderervdM) based on the $^{12}$CO and C$^{17}$O 6–5 lines" (4.1 Physical structure) [from (cite: BruderervdM)]
- External data: Molecular line parameters from CDMS  
  > "parameters taken from the Cologne Database for Molecular Spectroscopy (cite: Muller2001; Muller2005)" (Table 1) [from (cite: Muller2001; Muller2005)]
- External data: Collisional rate coefficients from LAMDA  
  > "Collisional rate coefficients were taken from the Leiden Atomic and Molecular Database (LAMDA) (cite: Schoier2005)" (4.1 Physical structure) [from (cite: Schoier2005)]
- External data: Dust optical depth ~0.43 averaged over continuum region  
  > "The optical depth $\tau_{\rm d}$ was calculated as $\tau_{\rm d}\sim 0.43$ (cite: vanderMarel2013) averaged over the continuum region." (4.2 Results) [from (cite: vanderMarel2013)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA v3.4  
  > "We reduced and calibrated the data using the Common Astronomy Software Application (CASA) v3.4." (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (model fit to shortest third of baselines); bandpass 3c279  
  > "The bandpass was calibrated using quasar 3c279, and fluxes were calibrated against Titan." (2 Observations)
- flux scale uncertainty: ~20%  
  > "The absolute flux calibration uncertainty in ALMA Band 9 is $\sim$20%." (2 Observations)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "after applying natural weighting and cleaning" (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: rectangular mask from 12CO emission, adapted per channel, applied to weaker lines  
  > "A rectangular cleaning mask centered on the detected emission peaks was used during the cleaning process of the $^{12}$CO line" (2 Observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.32" x 0.21", PA 96 deg  
  > "a synthesized beam of 0.32” $\times$ 0.21”" (2 Observations)
- final rms: 20-30 mJy/beam per 1 km/s channel  
  > "The final rms level was 20-30 mJy beam$^{-1}$ per 1 km s$^{-1}$ channel" (2 Observations)

### Inherited from earlier work

- Data reduction details  
  > "For more details on the data reduction see the supplementary online material of (cite: vanderMarel2013)." (2 Observations) [from (cite: vanderMarel2013)]
- Physical disk model  
  > "We used the best-fitting model of the gas structure from (cite: BruderervdM)" (4.1 Physical structure) [from (cite: BruderervdM)]

### Not stated but needed to reproduce (our reading)

- CASA tclean/clean parameters (cell, image size, niter, threshold)
- line-free channels and continuum subtraction method
- exact mask coordinates
- the DALI model parameter files
- LIME settings beyond grid points (e.g. dust opacities)
- how rms per channel was measured

## Analysis recipe

1. **Detect and integrate H2CO line**: Moment map and integrated flux over rectangle, v_LSR -0.5 to +9.5 km/s  
  > "Across this area, the integrated flux is found to be $\sim$3.1 $\pm$ 0.6 Jy km s$^{-1}$" (3 Results)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared with 12CO 6-5 at same velocity channels  
  > "The emission is, where detected, cospatial with the $^{12}$CO 6–5 emission at the same velocity channels" (3 Results)
2. **3 sigma upper limits on undetected lines**: F_upp = sqrt(dOmega/Omega_beam)*3*sigma*1.2*sqrt(N_chan)  
  > "F_{\rm upp} = \sqrt{d\Omega/\Omega_{\rm beam}} \cdot 3\sigma_{\rm rms} \cdot 1.2\sqrt{11\cdot1} = 0.79 \ {\rm Jy \ km \ s^{-1}}" (3 Results)
   - assumption: Other molecules cospatial with CO over -3 to +12 km/s  
  > "we expect the emission to be cospatial with the CO emission" (3 Results)
   - fitting: _not stated_
   - validation: _not stated_
3. **Model H2CO abundance with non-LTE radiative transfer**: LIME on DALI physical structure with three trial abundance profiles (constant, CO-scaled, ring 60-70 AU), compared to observed flux  
  > "The first step in the analysis is to empirically constrain the H$_2$CO abundance by using three different trial abundance profiles" (4.1 Physical structure)
   - software: LIME, DALI
   - parameter: 30 000 grid points, 12 000 surface points, outer radius 200 AU, 60 channels of 0.5 km/s, 5"x5" maps with 0.025" pixels  
  > "using 30 000 grid points and 12 000 surface grid points, using an outer radius of 200 AU" (4.1 Physical structure)
   - assumption: H2CO zero above photodissociation height N(H2)=4e20 cm-2 and where T<60 K (freeze-out)  
  > "H$_2$CO is expected to be frozen out on the grains at temperatures $<$60 K" (4.1 Physical structure)
   - fitting: Abundance grid scan, no formal fit  
  > "Figure [7](#fig:trends) presents the model fluxes as a function of H$_2$CO abundance for the three trial abundance structures." (Model, Results)
   - validation: Compared spectra and images convolved with ALMA beam; checked against simulated observations  
  > "the result of the model images convolved to the ALMA beam was compared with the result of simulated ALMA observations" (4.2 Results)
4. **Abundance limits for other molecules**: Same LIME modelling with CH3OH profiles as H2CO and others scaled to CO abundance; LTE for other species  
  > "For the other molecules the emission was only calculated in LTE" (4.1 Physical structure)
   - software: LIME
   - fitting: _not stated_
   - validation: Compared to DALI full chemical model predictions  
  > "The predicted integrated model intensity for H$^{13}$CO$^+$ is 0.02 Jy km s$^{-1}$" (5.2 Comparison with chemical models)
5. **Test continuum extinction on H2CO**: Attenuate model emission by exp(-tau_d) with 2D tau profile following continuum, max tau 0.86  
  > "The maximum $\tau_{\rm d}$ was taken as 0.86, recovering the averaged opacity over this area." (4.2 Results)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 3.4: data reduction and calibration  
  > "We reduced and calibrated the data using the Common Astronomy Software Application (CASA) v3.4." (2 Observations)
- **LIME** : non-LTE line radiative transfer of H2CO etc.  
  > "The H$_2$CO emission was modeled using the LIne Modeling Engine (LIME), a non-LTE excitation spectral line radiation transfer code" (4.1 Physical structure)
- **DALI** : thermo-chemical physical disk model  
  > "The DALI model (cite: Bruderer2012; Bruderer2013) uses a combination of a stellar photosphere with a disk density distribution as input." (4.1 Physical structure)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| H2CO 9(1,8)-8(1,7) integrated flux | 3.1 | 0.6 | Jy km/s | 1 | the integrated flux is found to be $\sim$3.1 $\pm$ 0.6 Jy km s$^{-1}$ |
| H2CO abundance w.r.t. H2 | ~1e-8 | 10^(±0.15) (constant model); within factors of a few | dimensionless | 3 | Model 1 with constant H$_2$CO abundance $\sim$10$^{-8 \pm 0.15}$ with respect to H$_2$ |
| CH3OH 3-sigma flux upper limit | 0.79 | not stated | Jy km/s | 2 | \sqrt{11\cdot1} = 0.79 \ {\rm Jy \ km \ s^{-1}} |
| Upper limit for CN, H13CO+ and other molecules | 1.8 | not stated | Jy km/s | 2 | \sqrt{15\cdot1} = 1.8 \ {\rm Jy \ km \ s^{-1}} |
| CH3OH abundance limit | <3e-8 | not stated | dimensionless | 4 | consistent with an abundance limit in model 1 of $<3\cdot10^{-8}$, thus H$_2$CO/CH$_3$OH $>$ 0.3 |
| H2CO/CH3OH ratio | >0.3 | not stated | dimensionless | 4 | thus H$_2$CO/CH$_3$OH $>$ 0.3 |
| H2CO column density at >60 AU | ~1e14 | not stated | cm^-2 | 3 | The column density of H$_2$CO for the best-fitting model with abundance 10$^{-8}$ is $\sim10^{14}$ cm$^{-2}$ for radii$>$60 AU |

## Qualitative findings

- H2CO emission forms a semi-ring at ~60 AU south of the star, offset from the dust continuum peak  
  > "which is spatially resolved as a semi-ring at $\sim60$ AU radius centered south from the star" (abstract)

## Claim tuples

- H: Warm H2CO can be detected in the IRS 48 transition disk | E: ALMA Band 9 line search | R: H2CO 9(1,8)-8(1,7) detected at 3-8 sigma per channel, resolved as southern semi-ring | F: H2CO is present where planetesimals form | **supported**
- H: The H2CO formation route can be constrained | E: Compare H2CO to CH3OH upper limit via LIME models | R: H2CO/CH3OH > 0.3 | F: Both ice and gas-phase routes plausible | **partially**
- H: H2CO distribution relates to the dust trap | E: Compare H2CO morphology with continuum and models | R: H2CO is south but offset from continuum peak | F: No firm claim possible due to low S/N | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Low S/N prevents distinguishing the radial abundance profiles  
  > "the current $S/N$ is too low to distinguish the different assumptions on the radial distribution of H$_2$CO" (4.2 Results)
- Caveat (inferred, ours): Upper limits rely on assumed spatial extent and ad hoc 1.2 factor
- Caveat (inferred, ours): Single physical model, no uncertainty propagation
- Caveat (inferred, ours): Continuum optical depth correction is an upper limit

## Reproducibility

- Data public (paper): Project code given; ALMA Cycle 0 data  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00635.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: DALI model files from Bruderer et al. 2014
- Missing: Detailed imaging parameters
- Missing: LIME input files
- Data volume (inferred): ~50-100 GB raw
- Score (inferred): 3/5, Data public and flux numeric, but physical model and reduction details come from companion papers.
- Rediscovery candidate: no, Needs the external DALI model and the imaging recipe is incomplete.

## Links

- Method: (cite: Brinch2010) (LIME code)
- Method: (cite: Bruderer2012) (DALI model)
- Companion: (cite: BruderervdM) (physical model of IRS 48 from same dataset)
- Companion: (cite: vanderMarel2013) (dust trap and data reduction details)

## Checks

```json
{
 "quotes": 60,
 "quotes_ok": 60,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 41,
  "rate": 0.569
 },
 "evidence_ok": true
}
```
