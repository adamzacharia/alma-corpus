# The Dragonfly Galaxy. II. ALMA unveils a triple merger and gas exchange in a hyper-luminous radio galaxy at z = 2

`2015A&A...584A..99E` | Astronomy and Astrophysics 2015 | first author: Emonts, B. H. C. | arXiv: 1510.02381 | DOI: 10.1051/0004-6361/201526090

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: What triggered the hyper-luminous starburst and radio-AGN in the Dragonfly Galaxy (MRC 0152-209), and how is its molecular gas distributed and moving?  
  > "What triggered its activity? We present ALMA Cycle 2 observations of cold molecular CO(6-5) gas and dust" (abstract)
- Target **Dragonfly Galaxy (MRC 0152-209)**: coordinates _not stated_; z/distance z = 1.9212 (8.3 kpc/arcsec)  
  > "the Dragonfly Galaxy (MRC 0152-209) at $z$ = 1.92" (1 Introduction); "They are presented in optical velocity definition with respect to $z$ = 1.9212 (EM11)." (2 ALMA observations); distance from CO(1-0) redshift from EM11  
  > "the Dragonfly Galaxy (MRC 0152-209) at $z$ = 1.92" (1 Introduction); "They are presented in optical velocity definition with respect to $z$ = 1.9212 (EM11)." (2 ALMA observations)

## Data provenance

- ALMA projects: 2013.1.00521.S
- bands: Band 6  
  > "The ALMA Cycle 2 observations in Band 6 were performed in July and Aug 2014" (2 ALMA observations)
- frequencies and spectral setup: two 4 GHz bands, 235.8-239.6 and 250.1-254.9 GHz  
  > "We used two 4 GHz bands, covering 235.8 $-$239.6 and 250.1$-$254.9 GHz." (2 ALMA observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 17-783 m, 32 antennas  
  > "with 32 antennas (baselines $17 - 783$m)" (2 ALMA observations)
- angular resolution: 0.32" x 0.28" beam, pa 78.9 deg (robust +0.5)  
  > "$0.32^{\prime\prime}$ $\times$ 0.28$^{\prime\prime}$ beam; pa = 78.9$^{\circ}$" (2 ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: 0.13 mJy/beam continuum; 0.54 mJy/beam line (Hanning smoothed)  
  > "0.13 mJy beam$^{-1}$ for the continuum and 0.54 mJy beam$^{-1}$ for the Hanning smoothed line data" (2 ALMA observations)
- time on source: 6.3 min  
  > "for a total of 6.3 min on source with 32 antennas" (2 ALMA observations)
- observing dates: July and Aug 2014  
  > "performed in July and Aug 2014" (2 ALMA observations)
- pi or archival as stated: _not stated_
- Line: CO 6-5 (not stated (observed 236.7 GHz))
- Other facility **ATCA**: CO(1-0) data (EM15)  
  > "we recently used the Australia Telescope Compact Array (ATCA) to image this CO(1-0)" (1 Introduction)
- Other facility **HST NICMOS/WFPC2**: stellar/UV counterparts  
  > "Components NW, SE and C all have a counterpart in *HST*/NICMOS imaging" (3.1 Morphology)
- External data: SFR ~3000 Msun/yr and L_IR from Spitzer/Herschel SED modelling  
  > "with a star formation rate determined with *Spitzer* and *Herschel* (3 – 500 $\mu$m) of $\sim$ 3000 M$_{\odot}$ yr$^{-1}$ (cite: dro14)" (1 Introduction) [from (cite: dro14)]
- External data: Stellar mass of the system  
  > "$\sim$10$^{11.76}$ M$_{\odot}$ stellar mass that was found in the system by (cite: bre10)" (3.1 Morphology) [from (cite: bre10)]
- External data: ATCA CO(1-0) data and redshifts  
  > "compare our ALMA data with lower resolution CO(1-0) data from EM15" (3.3 Excitation) [from (cite: emo15)]

## Processing

### Calibration

- pipeline or manual: calibration script supplied by ALMA observatory, in CASA  
  > "The data were calibrated in CASA (cite: mcm07) with the calibration script that was supplied by the ALMA observatory." (2 ALMA observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: conservative 10%  
  > "Errors reflect a conservative 10$\%$ uncertainty in flux calibration" (Table 1)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: robust = +0.5 (uniform also used for PV slits)  
  > "we used data with robustness weighting parameter of +0.5" (2 ALMA observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: total intensity map made through low-resolution mask  
  > "A total intensity CO(6-5) map was created by filtering the data through a low-resolution mask." (2 ALMA observations)
- multiscale scales: _not stated_
- continuum subtraction: straight-line fit to line-free channels in uv domain  
  > "we subtracted the continuum in the UV-domain by fitting a straight line to the line-free channels" (2 ALMA observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: binned to 30 km/s, Hanning smoothed to 60 km/s  
  > "binned to 30 km s$^{-1}$ channels and Hanning smoothed to a velocity resolution of 60 km s$^{-1}$" (2 ALMA observations)
- final beam: 0.32" x 0.28"  
  > "$0.32^{\prime\prime}$ $\times$ 0.28$^{\prime\prime}$ beam" (2 ALMA observations)
- final rms: 0.13 mJy/beam continuum; 0.54 mJy/beam line  
  > "The root mean square (rms) noise level is 0.13 mJy beam$^{-1}$ for the continuum" (2 ALMA observations)

### Inherited from earlier work

- CO(1-0) data, redshift, and gas depletion time  
  > "consistent with $z_{\rm CO(1-0)}$ = 1.9212 $\pm$ 0.0002 (EM11)" (3.2 Kinematics) [from EM11, EM15]
- Dust mass method  
  > "Dust masses can be derived following (cite: gil14), assuming an optically thin case" (4.2 Gas and dust masses) [from (cite: gil14)]
- Outflow rate formula  
  > "following (cite: arr14)" (4.3) [from (cite: arr14)]

### Not stated but needed to reproduce (our reading)

- CASA version
- tclean parameters (cell, image size, niter, threshold, scales)
- line-free channel ranges
- flux/bandpass/phase calibrators
- Gaussian fitting software and priors
- exact aperture/region definitions for fluxes
- mask details and moment map settings
- ALMA coordinates of the field

## Analysis recipe

1. **Image continuum and CO(6-5) cube**: CASA calibration script, continuum from line-free channels of both bands, uv continuum subtraction, robust +0.5 imaging  
  > "We combined both bands to image the 1.2 mm dust continuum, excluding channels with CO(6-5) emission" (2 ALMA observations)
   - software: CASA
   - fitting: _not stated_
   - validation: features present in both July and Aug data  
  > "All features discussed in this paper were present in both the July and Aug data." (2 ALMA observations)
2. **Kinematics: PV diagrams and Gaussian line fits**: Four pseudo-slits; Gaussian components fitted to spectra (2 for NW, 3 for SE)  
  > "The best-fit models are derived when using two Gaussian components for NW and three for SE." (3.2 Kinematics)
   - fitting: Gaussian models; fit method not stated  
  > "Fig. [3](#fig:kinematics) (right) also shows Gaussian model fits that approximate the complex gas kinematics seen in the PV plots." (Kinematics)
   - validation: alternative 3-component NW model leaves noise-consistent residuals  
  > "An alternative 3-component model in NW, in which the main Gaussian is similar to that of SE, only leaves residuals that are consistent with the noise" (3.2 Kinematics)
3. **Derive excitation ratio and high-excitation gas**: Compare CO(6-5) (smoothed to ATCA resolution) with CO(1-0); subtract scaled CO(1-0) model to get residuals  
  > "If we subtract the model of the scaled CO(1-0) spectrum from the CO(6-5) spectrum of the central region, the CO(6-5) residuals reveal this ‘high-excitation’ gas" (3.3 Excitation)
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive gas and dust masses**: H2 mass from CO(6-5) via r6-5 and X_CO; dust mass from 1.2 mm flux  
  > "These estimates are based on a conversion factor $X_{\rm CO}$ = M$_{\rm H_2}$/$L'_{\rm CO}$ = 0.8 M$_{\odot}$ (K km s$^{-1}$ pc$^{2}$)$^{-1}$" (4.2 Gas and dust masses)
   - assumption: r6-5 = 13 (17-36 for wings), X_CO = 0.8, optically thin dust, kappa = 4.0 (nu/1.2 THz)^-2.0 cm2/g, T_dust = 45 K  
  > "$\kappa_{\nu} = 4.0(\nu_{\rm rest}/1.2\,{\rm THz})^{-2.0}$ cm$^{2}$ g$^{-1}$ and $T_{\rm dust} = 45$ K" (4.2 Gas and dust masses)
   - fitting: _not stated_
   - validation: _not stated_
5. **Energetics and gas redistribution rate**: Order-of-magnitude kinetic energy and Mdot = M v / R  
  > "molecular gas is being redistributed at a minimum rate of Ṁ =M$_{\rm H2}$ $\times$ v$_{\rm ejecta}$ $\times$ R$^{-1}$" (4.3)
   - assumption: i_outfl = 90 deg, v ~250 km/s, FWHM ~300 km/s, R ~1 kpc  
  > "assuming *i*$_{\rm outfl}$ = 90$^{\circ}$, M$_{\rm H_2}$ $\sim$ 10$^{10}$ M$_{\odot}$, v $\sim$ 250 km s$^{-1}$ and FWHM $\sim$ 300 km s$^{-1}$" (4.3)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : calibration and imaging  
  > "The data were calibrated in CASA (cite: mcm07)" (2 ALMA observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| S_1.2mm NW | 0.8 | 0.2 | mJy | 1 | / $S_{\rm 1.2\,mm}$ (mJy) / 0.8 $\pm$ 0.2 / 1.5 $\pm$ 0.2 / $<$0.3 / |
| S_1.2mm SE | 1.5 | 0.2 | mJy | 1 | / $S_{\rm 1.2\,mm}$ (mJy) / 0.8 $\pm$ 0.2 / 1.5 $\pm$ 0.2 / $<$0.3 / |
| I_CO(6-5) NW | 2.0 | 0.2 | Jy/beam km/s | 1 | 2.0 $\pm$ 0.2 / 1.4 $\pm$ 0.2 / 0.20$\pm$0.05 |
| I_CO(6-5) SE | 1.4 | 0.2 | Jy/beam km/s | 1 | 2.0 $\pm$ 0.2 / 1.4 $\pm$ 0.2 / 0.20$\pm$0.05 |
| Main-component velocity NW | -30 | 10 | km/s | 2 | central velocity of $-$30 $\pm$ 10 km s$^{-1}$ for NW and $-$15$\pm$30 km s$^{-1}$ for SE |
| FWHM main component NW | 360 | 20 | km/s | 2 | larger FWHM in NW (360 $\pm$ 20 km s$^{-1}$) |
| r6-5 | ~13 | not stated | dimensionless | 3 | average intensity ratio r$_{\rm 6-5}$ = $I_{\rm CO(6-5)}$/$I_{\rm CO(1-0)}$ $\sim$ 13 |
| M_H2 SE (main) | 9 | 2 | 1e9 Msun | 4 | / 14$-$21 / 9 $\pm$ 2 / 2.2 $\pm$ 0.5 / |
| Minimum gas redistribution rate | 1200 | 500 | Msun/yr | 5 | $\sim$ 1200 $\pm$ 500 M$_{\odot}$ yr$^{-1}$ |
| Upper-limit redistribution rate | 2900 | 1600 | Msun/yr | 5 | $\sim$ 2900 $\pm$ 1600 M$_{\odot}$ yr$^{-1}$ |
| NW-SE separation | ~4 | not stated | kpc | 0 | the NW and SE components have a projected separation of $\sim$4 kpc |

## Qualitative findings

- Dragonfly is a precoalescent triple merger with activity triggered before the nuclei fully merged  
  > "our current ALMA results indicate that the triggering of this activity has happened before the parent nuclei fully merged" (4.1 Precoalescent merger)
- Highest-velocity gas is also the most highly excited  
  > "*This thus shows that the highest velocity gas is also the most highly excited.*" (3.3 Excitation)

## Claim tuples

- H: The Dragonfly is a gas-rich merger | E: ALMA CO(6-5) and 1.2 mm continuum compared with HST | R: Double nucleus (~4 kpc) plus companion C at ~10 kpc, all with NICMOS counterparts | F: Precoalescent triple merger | **supported**
- H: Gas at highest velocities is redistributed within the merger | E: CO(6-5) vs CO(1-0) residuals and kinematics | R: ~1e10 Msun with enhanced excitation; rate >= 1200 Msun/yr | F: Gas redistribution comparable to depletion timescale; gas stays bound | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Interacting discs versus starburst/AGN-driven outflow; driver undetermined  
  > "it remains unclear as to what is the total mass currently involved and what is the main driving mechanism" (4.3)
- How they decided it was enough: _not stated_
- Limitation (authors): Resolution insufficient to determine disc rotation axes and properties  
  > "The resolution of our CO(6-5) data is insufficient to securely determine the rotation axis and detailed properties of these putative discs" (3.2 Kinematics)
- Caveat (inferred, ours): Only 6.3 min on source; Gaussian decomposition degenerate
- Caveat (inferred, ours): Gas masses depend on assumed r6-5 and X_CO
- Caveat (inferred, ours): Outflow energetics are order-of-magnitude with assumed geometry

## Reproducibility

- Data public (paper): project code given  
  > "We used the following ALMA data: 2013.1.00521.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: CASA version and clean parameters
- Missing: line-free channels
- Missing: fit procedure details
- Missing: region definitions
- Data volume (inferred): ~10-30 GB
- Score (inferred): 3/5, Single short archival dataset with simple methods, but imaging and fitting details are sparse.
- Rediscovery candidate: no, Imaging and fitting details missing; results depend on external CO(1-0) data.

## Links

- Method: (cite: gil14) (dust mass method)
- Method: (cite: arr14) (outflow rate formula)
- Companion: (cite: emo15) (Dragonfly paper I, ATCA CO(1-0))
- Companion: (cite: dro14) (SED/SFR modelling)

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
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 42,
  "rate": 0.575
 },
 "evidence_ok": true
}
```
