# ALMA Observations of the Molecular Gas in the Debris Disk of the 30 Myr Old Star HD 21997

`2013ApJ...776...77K` | The Astrophysical Journal 2013 | first author: Kóspál, Á. | arXiv: 1310.5068 | DOI: 10.1088/0004-637X/776/2/77

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: debris_disks, protoplanetary_disks
- Question: What are the physical state, origin and evolutionary status of the molecular gas in the 30 Myr old HD 21997 debris disk, and is it co-located with the dust?  
  > "With the goal of understanding the physical state, origin, and evolution of the gas in young debris disks, we obtained CO line observations" (abstract)
- Target **HD 21997**: coordinates _not stated_; z/distance 72 pc  
  > "an A3-type star at a distance of 72 pc (based on Hipparcos parallax; (cite: vanleeuwen2007))" (1 Introduction); distance from Hipparcos parallax (van Leeuwen 2007)  
  > "an A3-type star at a distance of 72 pc (based on Hipparcos parallax; (cite: vanleeuwen2007))" (1 Introduction)

## Data provenance

- ALMA projects: 2011.0.00780.S
- bands: Band 6 (CO 2-1) and Band 7 (CO 3-2, CS 7-6)  
  > "In Band 6, we targeted the (2–1) transitions of $^{12}$CO, $^{13}$CO, and C$^{18}$O." (2 Observations and data reduction)
- frequencies and spectral setup: FDM; Band 6: 3840 channels of 122 kHz, 469 MHz per window, 0.33 km/s; Band 7: 3840 channels of 244 kHz, 938 MHz, 0.44 km/s  
  > "Each of the four simultaneously observed spectral windows offered 3840 channels with a channel separation of 122 kHz, resulting in a bandwidth of 469 MHz per window." (2 Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: Cycle 0 compact configuration  
  > "We observed HD 21997 with ALMA in Cycle 0 using a compact configuration (PI: Á. Kóspál)." (2 Observations and data reduction)
- baselines: 9.6-196 kλ (Band 6); 14-154 kλ (Band 7)  
  > "using 16 antennas, with baselines between 9.6 and 196 k$\lambda$" (2 Observations and data reduction)
- angular resolution: beams ~1.1-1.9 arcsec (Table)  
  > "| $^{12}$CO(2–1) | 230.538 | A2 | 1.14$\times$1.21 | 16.4 | 8.6 |" (Table 1 (results))
- max recoverable scale: _not stated_
- sensitivity: 5.7-9.0 mJy/beam/channel  
  > "| $^{13}$CO(3–2) | 330.588 | B1, B2 | 1.20$\times$1.38 | $-$49.9 | 5.7 |" (Table 1 (results))
- time on source: 49.4 min per setup  
  > "Each of these two setups had an on-source time of 49.4 minutes." (2 Observations and data reduction)
- observing dates: 2011 Nov 3, 4, 29; Dec 31  
  > "it was executed on 2011 November 29 using 14 antennas" (2 Observations and data reduction)
- pi or archival as stated: _not stated_
- Line: 12CO 2-1 (230.538 GHz)
- Line: 12CO 3-2 (345.796 GHz)
- Line: 13CO 2-1 (220.399 GHz)
- Line: 13CO 3-2 (330.588 GHz)
- Line: C18O 2-1 (219.560 GHz)
- Other facility **APEX**: earlier CO(3-2) and CO(2-1) detections for comparison  
  > "we detected molecular gas in the $J$=3–2 and $J$=2–1 transitions (CO(3–2) and CO(2–1)) with the APEX telescope" (1 Introduction)
- Other facility **Spitzer/IRS**: spectrum used to check H2 lines  
  > "We checked the *Spitzer*/Infrared Spectrograph spectrum of HD 21997 (Paper I) for the $S$(0), $S$(1), and $S$(2) lines" (3.3 Temperature and Mass of the CO Gas)
- External data: Dust continuum results: dust disk inner radius ~55 AU, dust mass 0.09 Earth masses within ~150 AU  
  > "In Paper I, we found that the dust disk starts at a radius of $\approx$55 AU." (4 Discussion) [from Moór et al. 2013 (Paper I) (cite: moor2013)]
- External data: ISM isotopic abundance ratios (tau12=560 tau18, tau13=7.4 tau18)  
  > "then $\tau_{12} = 560
\tau_{18}$, and $\tau_{13} = 7.4 \tau_{18}$" (3.3 Temperature and Mass of the CO Gas) [from Wilson & Rood 1994 (cite: wilson1994)]
- External data: Dust temperature 64 K from SED fitting  
  > "the dust temperature (64 K, based on spectral energy distribution fitting done by (cite: moor2011b))" (4.2 Primordial Gas in a Hybrid Disk) [from Moór et al. 2011 (cite: moor2011b)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Callisto, CASA Butler-JPL-Horizons 2010 model; J0403-360 bandpass and gain  
  > "Callisto was used to set the absolute amplitude scale using the CASA Butler-JPL-Horizons 2010 model." (2 Observations and data reduction)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean, per line region  
  > "individually cleaned the spectral region around each molecular line using the CASA task `clean` with robust weighting." (2 Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: CASA uvcontsub  
  > "We subtracted the continuum emission in the spectral cubes using the CASA task `uvcontsub`" (2 Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Continuum observations and dust model presented separately  
  > "while the continuum measurements are presented in Paper I." (2 Observations and data reduction) [from Paper I (cite: moor2013)]
- CO lifetime UV treatment done the same way as earlier  
  > "We took into account both stellar UV flux and the interstellar radiation field, the same way as in (cite: moor2011b)." (4.1 Debris Disk with Pure Secondary Gas) [from (cite: moor2011b)]

### Not stated but needed to reproduce (our reading)

- robust value, cell size, image size, clean mask and threshold
- CASA version and whether calibration used the archive scripts
- line-free channels used for uvcontsub
- number of flagged data/antennas
- aperture/moment-map thresholds
- CO excitation/radiative transfer code used for mass
- model code for the disk grid not released

## Analysis recipe

1. **Extract integrated line profiles and fluxes**: Sum flux within 2.8 arcsec radius of star per channel; integrate -4 to 6.6 km/s  
  > "we added all the flux within a radius of 2$\ensuremath{''}$8 of the stellar position" (3.1 Integrated Line Profiles)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared with APEX fluxes; no significant flux loss  
  > "indicating that there is no significant flux loss due to the interferometer filtering out large-scale structures" (3.1 Integrated Line Profiles)
2. **Moment maps and PV diagram**: Zeroth and first moment maps; P.A. from v=vsys line; PV along major axis  
  > "We calculated zeroth and first moment maps for each data cube" (3.2 Spatially Resolved CO Emission)
   - fitting: _not stated_
   - validation: _not stated_
3. **Optical depth, temperature and CO mass**: Isotopologue line ratios give optical depth; 12CO brightness and 3-2/2-1 ratio via Planck function give temperature; C18O gives mass for T 5.6-100 K  
  > "Indeed, using the Planck function, it turns out that these line ratios correspond to 5.6 K." (3.3 Temperature and Mass of the CO Gas)
   - assumption: ISM isotope ratios; CO/H2 = 1e-4 for total gas mass  
  > "Taking a canonical CO/H$_2$ abundance ratio of 10$^{-4}$" (3.3 Temperature and Mass of the CO Gas)
   - fitting: _not stated_
   - validation: Isotopic ratio uncertainty gives factor 2 lower to 5 higher mass  
  > "the total CO mass may actually be a factor of two smaller or a factor of five higher than this value" (3.3 Temperature and Mass of the CO Gas)
4. **Fit Keplerian disk model to 12CO(2-1) cube**: Grid of 104,448 models with 5 parameters, Keplerian, convolved with beam; chi2 max over channels; Bayesian probability exp(-chi2/2) marginalized  
  > "In total, we calculated 104,448 models." (3.4 Distribution of the CO Gas)
   - parameter: M* 0.9-3.0 Msun step 0.3; rin 5-60 AU; rout 95-175 AU; i 25-39 deg step 2; p 0 to -1.75 step 0.25  
  > "$r_{\rm in}$ between 5 AU and 60 AU in steps of 5 AU, $r_{\rm out}$ between 95 AU and 175 AU in steps of 5 AU" (3.4 Distribution of the CO Gas)
   - parameter: Intrinsic line width 0.1 km/s; 2-channel Hanning smoothing; 6x spatial oversampling  
  > "We used an intrinsic line width of 0.1 km s$^{-1}$" (3.4 Distribution of the CO Gas)
   - assumption: Keplerian rotation, power-law brightness I(r)~r^p, models normalized to observed total intensity  
  > "we normalized the models so that the total intensity equaled the observed total intensity" (3.4 Distribution of the CO Gas)
   - fitting: Uniform grid, flat priors implied; 1D marginal maximum with 68% integrals; inclination from best-fit stellar mass due to degeneracy  
  > "The inclination and the stellar mass are degenerate, thus we did not determine the inclination from the Bayesian probabilities" (3.4 Distribution of the CO Gas)
   - validation: Model reproduces all five lines; outer radius, inclination, stellar mass consistent with independent estimates  
  > "This fact demonstrates that a single disk model with one set of parameters reproduces all five CO lines." (3.4 Distribution of the CO Gas)
5. **CO lifetime and gas production rate**: CO distributed 20-138 AU with power-law density, shielding from Visser 2009; lifetime into production rate  
  > "we distributed the measured CO mass between 20 AU and 138 AU, adopted a power-law radial density distribution" (4.1 Debris Disk with Pure Secondary Gas)
   - assumption: alpha 1.5-2.5, H/r 0.05-0.2  
  > "with $\alpha$ = 1.5, 2.0, and 2.5), and assumed three different vertical scale heights ($H/r$ = 0.05, 0.1, and 0.2)" (4.1 Debris Disk with Pure Secondary Gas)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : uvcontsub, clean, flux model  
  > "We subtracted the continuum emission in the spectral cubes using the CASA task `uvcontsub`" (2 Observations and data reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Disk outer radius | 138 | ±20 | AU | 4 | /     Disk outer radius     /     $r_{\rm out}$ (AU)      /     $138\pm20$      / |
| Stellar mass | 1.8 | +0.5/-0.2 | Msun | 4 | /       Stellar mass       /     $M_*$ ($M_{\odot}$)     / $1.8^{+0.5}_{-0.2}$ / |
| Inclination | 32.6 | ±3.1 | deg | 4 | /     Disk inclination     /      $i$ ($^{\circ}$)       /   $32.6 \pm 3.1$    / |
| Inner radius | <26 | 1 sigma upper limit | AU | 4 | /    Disk inner radius     /      $r_{\rm in}$ (AU)      /       $< 26$        / |
| Major axis P.A. | 22.6 | ±0.5 | deg | 2 | /     Disk orientation     /     $P.A.$ ($^{\circ}$)     /   $22.6 \pm 0.5$    / |
| Systemic velocity | 1.29 | ±0.05 | km/s | 1 | The intensity-weighted average velocity for all lines is the same (1.29 $\pm$ 0.05 km s$^{-1}$) as well. |
| 12CO(3-2) total flux | 2.52 | 0.27 | Jy km/s | 1 | / $^{12}$CO(3–2) / 345.796 / B1 / 1.19$\times$1.47 / 117.5 / 7.9 / 0.615 / 2.52$\,\pm\,$0.27 / |
| C18O(2-1) total flux | 0.36 | 0.06 | Jy km/s | 1 | / C$^{18}$O(2–1) / 219.560 / A1 / 1.21$\times$1.92 / 18.6 / 9.0 / 0.129 / 0.36$\,\pm\,$0.06 / |
| Radiation temperature from 12CO 3-2/2-1 ratio | 5.6 | not stated | K | 3 | Indeed, using the Planck function, it turns out that these line ratios correspond to 5.6 K. |
| Total CO mass | (4-8)e-2 | not stated | Earth masses | 3 | The resulting value, (4–8)$\times$10$^{-2}\,M_{\oplus}$ |
| CO-to-dust mass ratio | 0.4-0.9 | not stated | dimensionless | 0 | resulting in a CO-to-dust ratio of 0.4–0.9 |
| Lower limit gas production rate | 1e19 | not stated | kg/yr | 5 | we obtained a lower limit for the gas production rate of about 10$^{19}$ kg yr$^{-1}$ |

## Qualitative findings

- Gas is in Keplerian rotation; gas extends inside the dust ring, so gas and dust are not co-located  
  > "the gas and dust in the HD 21997 system are not co-located, indicating a dust-free inner gas disk within 55 AU of the star." (abstract)

## Claim tuples

- H: Is the CO disk in Keplerian rotation and described by a simple star+disk model? | E: Grid model fit to 12CO(2-1) cube | R: rout=138 AU, M*=1.8 Msun, i=32.6 deg | F: Simple Keplerian disk reproduces all five CO lines | **supported**
- H: How much CO is present and how is it excited? | E: Isotopologue ratios and C18O mass | R: CO mass (4-8)e-2 Earth masses, T about 6-9 K | F: Gas-rich disk with cold CO, comparable CO and dust mass | **supported**
- H: Is the gas of secondary origin? | E: CO lifetime and production rate estimate | R: Required production rate implies 1e10-1e11 comets | F: Pure secondary origin disfavored | **supported**
- H: Is HD 21997 a hybrid system? | E: Compare gas and dust distributions and disk properties | R: Dust-free inner gas disk; dust debris-like | F: Proposed hybrid disk with primordial gas and secondary dust | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: 12CO(2-1) chosen for modelling for brightness and smallest, most circular beam  
  > "We decided to model the $^{12}$CO (2–1) line, which is one of the brightest we observed and has the smallest and most circular beam." (3.4 Distribution of the CO Gas)
- Alternative: Secondary-gas scenario rejected due to high production rate and non co-location  
  > "the short CO lifetimes and the necessary high CO production rates exclude this scenario" (5 Summary and Conclusions)
- How they decided it was enough: _not stated_
- Limitation (authors): Inner radius only an upper limit; brightness exponent ill-determined; full radiative transfer model postponed  
  > "A more detailed physical model, taking into account the vertical disk structure and full radiative transfer, is postponed to our forthcoming paper." (3.4 Distribution of the CO Gas)
- Caveat (inferred, ours): Chi2 defined as max over channels is nonstandard; uncertainties are formal
- Caveat (inferred, ours): Grid is coarse and inclination degenerate with mass
- Caveat (inferred, ours): Mass depends on assumed isotope ratios and temperature
- Caveat (inferred, ours): Resolution about 1.2 arcsec limits inner radius constraint

## Reproducibility

- Data public (paper): ALMA Cycle 0 project cited  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00780.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: clean parameters (robust, cell, mask)
- Missing: model code
- Missing: aperture and moment thresholds
- Missing: CO excitation calculation details
- Data volume (inferred): ~10-30 GB raw (Cycle 0, 5 short executions)
- Score (inferred): 3/5, Data public and model grid described in detail, but imaging parameters and code absent.
- Rediscovery candidate: yes, Public Cycle 0 data, clear grid fit recipe and numeric results (rout, M*, i, fluxes), though imaging details are missing.

## Links

- Companion: Moór et al. 2013 (cite: moor2013) (ALMA continuum analysis (Paper I))
- Companion: Moór et al. 2011 (cite: moor2011b) (APEX detection of CO)

## Checks

```json
{
 "quotes": 64,
 "quotes_ok": 64,
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
  "facts": 74,
  "stated": 41,
  "rate": 0.554
 },
 "evidence_ok": true
}
```
