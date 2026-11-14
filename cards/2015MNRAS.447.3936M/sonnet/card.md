# CO mass upper limits in the Fomalhaut ring - the importance of NLTE excitation in debris discs and future prospects with ALMA

`2015MNRAS.447.3936M` | Monthly Notices of the Royal Astronomical Society 2015 | first author: Matrà, L. | arXiv: 1412.2757 | DOI: 10.1093/mnras/stu2619

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: debris_disks, astrochemistry
- Question: Is CO J=3-2 emission detectable in the Fomalhaut ring, and how does non-LTE CO excitation affect the derived CO mass upper limit and planetesimal CO/H2O ice ratio?  
  > "we analyse CO molecular excitation in optically thin debris discs, and search ALMA Cycle-0 data for CO J=3-2 emission in the Fomalhaut ring." (abstract)
- Target **Fomalhaut ring**: coordinates pointing centre RA 22h57m38.65s, Dec -29d37m12.6s  
  > "The star harbours a debris ring which has been imaged in scattered light at a semi-major axis of $\sim$140 AU (cite: Kalas2005)." (1 Introduction); "with pointing centred on the position of Fomalhaut b, RA: $22^h57^m38^s.65$, Dec: $-29^d37\ensuremath{'}12.6\ensuremath{''}$" (2 Observations and Results); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00191.S
- bands: Band 7  
  > "for 140 minutes (Band 7)" (2 Observations and Results)
- frequencies and spectral setup: upper/lower sidebands 357 and 345 GHz; channel width 488.28 kHz (0.424 km/s)  
  > "with upper and lower sidebands at frequencies of 357 and 345 GHz, respectively." (2 Observations and Results); "we retained the channel width of the calibrated data (488.28 kHz, i.e. 0.424 km/s)" (2 Observations and Results)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.5" x 1.2" beam  
  > "for a beam of size 1$\ensuremath{''}$5 $\times$ 1$\ensuremath{''}$2" (2 Observations and Results)
- max recoverable scale: _not stated_
- sensitivity: ~60 uJy/beam continuum  
  > "A continuum sensitivity of $\sim$60 $\mu$Jy beam$^{-1}$ was achieved" (2 Observations and Results)
- time on source: 140 minutes  
  > "for 140 minutes (Band 7)" (2 Observations and Results)
- observing dates: 2011  
  > "The Fomalhaut ring was observed in 2011 by ALMA" (2 Observations and Results)
- pi or archival as stated: _not stated_
- Line: CO J=3-2 (345.789 GHz)
- External data: Dust model: Gaussian radial profile FWHM 16 AU centred at 143 AU, exponential vertical profile with 1 deg opening angle; dust temperature 48 K; ALMA continuum flux  
  > "This consists of a Gaussian radial profile with FWHM of 16 AU and centred at a radius of 143 AU, and an exponential vertical profile with an opening angle of 1$^{\circ}$." (4.1 The radiation environment) [from (cite: Boley2012)]
- External data: Ring orbital parameters used for velocity assignment  
  > "using orbital parameters from (cite: Kalas2005)" (2 Observations and Results) [from (cite: Kalas2005)]
- External data: CO-H2 collisional rate coefficients  
  > "Coefficients for H$_2$-CO collisions are obtained from the LAMDA database (cite: Schoier2005)." (4.2 Collisional excitation) [from (cite: Schoier2005)]
- External data: Collisional rates dust mass-loss rate 6.0e17 kg/yr  
  > "has been estimated as $6.0\times10^{17}$ kg/yr (cite: Wyatt2002)" (5.1 Production and destruction) [from (cite: Wyatt2002)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ~10%  
  > "The flux calibration uncertainty was estimated to be $\sim$10%." (2 Observations and Results)
- self calibration: _not stated_

### Imaging

- task: CASA v.4.1.0 imaging repeated at native channel width  
  > "Here we repeated the imaging section of the data reduction using the CASA software v.4.1.0 (cite: McMullin2007)" (2 Observations and Results)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: pixels with continuum >=4 sigma, star pixels discarded; each pixel assigned Keplerian velocity channel  
  > "We used this to select pixels where continuum emission observed is $\ge$ 4$\sigma$, and subsequently discarded pixels associated with the star" (2 Observations and Results)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: non-primary-beam-corrected continuum image used for pixel selection  
  > "We also recovered the non-primary-beam-corrected continuum image from (cite: Boley2012)." (2 Observations and Results)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Observation details and data reduction (calibration)  
  > "A more detailed description of the observations and data reduction can be found in (cite: Boley2012)." (2 Observations and Results) [from (cite: Boley2012)]
- Gas T_k, dust model and C/CO, C+/C ratios assumed as in beta Pic  
  > "we assume C/CO and C$^+$/C ratios similar to those inferred for the $\beta$ Pictoris disc (cite: Roberge2000; Cataldi2014)" (4.2 Collisional excitation) [from (cite: Roberge2000; Cataldi2014)]

### Not stated but needed to reproduce (our reading)

- Imaging parameters (weighting/robust, cell size, image size, deconvolver, cleaning threshold)
- Calibration details are only in Boley2012 (calibrators, pipeline)
- Velocity assigned per pixel: stellar radial velocity value and ring inclination/PA not given
- Code for the non-LTE statistical equilibrium and radiative transfer model not named or released
- Exact mapping from 3-sigma flux to mass over grid and grid resolution
- Sensitivity calculator settings (PWV, configuration) for prospects

## Analysis recipe

1. **Re-image line cube**: Repeat imaging of calibrated data at native channel resolution, 200-channel window around CO 3-2  
  > "We selected a 200-channels wide (85 km/s) spectral window around the CO line" (2 Observations and Results)
   - software: CASA
   - parameter: channel width 0.424 km/s  
  > "(488.28 kHz, i.e. 0.424 km/s)" (2 Observations and Results)
   - fitting: _not stated_
   - validation: _not stated_
2. **Search for CO emission with velocity-matched extraction**: Select ring pixels from 4 sigma continuum, assign Keplerian velocity channel per pixel, sum flux in expected channels; also moment-0 map and unshifted integrated spectrum  
  > "for the selected pixels, we only sum fluxes in the spectral channels identified for the velocity of the ring at that location." (2 Observations and Results)
   - software: CASA
   - parameter: 1-sigma single-channel error 30 mJy; 3-sigma 90 mJy  
  > "where 30 mJy represents the 1-$\sigma$ error on the spatially integrated flux in a single frequency channel" (2 Observations and Results)
   - assumption: CO co-located with dust, Keplerian, axisymmetric ring  
  > "under the assumption that the CO and sub-mm dust emission are co-located and axisymmetric" (2 Observations and Results)
   - fitting: _not stated_
   - validation: Continuum level of spectrum (23 mJy) compared with ALMA and single-dish fluxes  
  > "the mean continuum level of the spectrum (23 mJy) is in line with both the ALMA continuum flux estimate in the observed region" (2 Observations and Results)
3. **Compute flux upper limit**: 3-sigma plus 10% calibration error, converted to Jy km/s, rescaled by whole-ring/partial-ring continuum ratio  
  > "rescale our result using the ratio of continuum flux of the whole ring (cite: Boley2012) over that of the partial ring (85 mJy/23 mJy)" (2 Observations and Results)
   - fitting: _not stated_
   - validation: _not stated_
4. **Non-LTE CO excitation and mass upper limit**: Solve statistical equilibrium for levels up to jmax=24 over grid of f_cp, T_k (10-150 K) and CO/H2O ice ratio, with radiation field from CMB, star and dust model; convert flux limit to mass with Eq. 2  
  > "is solved to obtain fractional populations $x_j$ for all levels up to $j_{max}$=24" (4.2 Collisional excitation)
   - parameter: T_k 10 to 150 K  
  > "we select a range of temperatures from as low as 10 K, to as high as 150 K" (4.2 Collisional excitation)
   - assumption: Dust, colliders and CO co-located, axisymmetric; uniform T_k; colliders H2 (primordial) or e- and H2O (secondary)  
  > "dust, collisional partners and CO are assumed to be co-located and to follow the same density distribution within the ring" (4 Application to the Fomalhaut ring)
   - fitting: _not stated_
   - validation: _not stated_
5. **Constrain planetesimal CO/H2O ice ratio**: Compare CO destruction rate upper limit (mass / photodissociation lifetime ~120 yr) to production rate from collisional cascade assuming steady state  
  > "If we assume steady state, the production rate (grey dashed line, Fig. 5, right) should balance the destruction rate (coloured lines)" (5.2 Constraints on the planetesimal composition)
   - assumption: Comet-like composition, ice/rock about 1  
  > "Assuming the planetesimal composition to be similar to that observed in Solar System comets (ice/rock ratio of about 1" (5.1 Production and destruction)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.1.0: Re-imaging ALMA data to produce line cube  
  > "using the CASA software v.4.1.0 (cite: McMullin2007)" (2 Observations and Results)
- **ALMA Sensitivity Calculator** : Comparison of predicted flux limits with ALMA sensitivity for future observations  
  > "Fig. 6 shows a comparison between these flux upper limits and the output of the ALMA Sensitivity Calculator." (5.4 Prospects for detection)
- **LAMDA database** : CO-H2 collisional coefficients  
  > "Coefficients for H$_2$-CO collisions are obtained from the LAMDA database (cite: Schoier2005)." (4.2 Collisional excitation)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 3-sigma upper limit on integrated CO J=3-2 line flux | 0.16 | not stated | Jy km/s | 3 | This yields a final 3-$\sigma$ CO J=3-2 line flux upper limit of 0.16 Jy km s$^{-1}$ |
| Strict 3-sigma CO mass upper limit (radiation-dominated) | 4.9e-4 | not stated | Earth masses | 4 | the 3$\sigma$ upper limit on the mass of CO in the Fomalhaut ring is thus 4.9 $\times$ $10^{-4}$ M$_{\oplus}$ |
| CO mass upper limit, secondary scenario | 2.5e-6 | not stated | Earth masses | 4 | lead to upper limits on the CO and H$_2$O gas mass in the Fomalhaut ring of 2.5 $\times$ $10^{-6}$ M$_{\oplus}$ |
| Upper limit on CO/H2O ice ratio in planetesimals (steady state) | ~55% (~3% if LTE) | not stated | percent | 5 | allows us to set an upper limit of $\sim$55% on the CO/H$_2$O ice ratio in the parent planetesimals. This could drop to $\sim$3% if LTE applies |
| CO photodissociation timescale | ~120 | not stated | yr | 0 | hence assume the photodissociation timescale of CO to be $\tau_{phd}\sim120$ years |

## Qualitative findings

- No CO detected in the Fomalhaut ring; LTE analysis would underestimate the mass limit by ~3-4 orders of magnitude; primordial CO origin disfavoured  
  > "a simple LTE analysis underestimates this by $\sim$3-4 orders magnitude." (Summary and Conclusions)

## Claim tuples

- H: Is CO gas present in the Fomalhaut ring at detectable levels? | E: Velocity-matched extraction of CO 3-2 in Cycle-0 data | R: 22±30 and 2±30 mJy per channel vs 90 mJy threshold | F: No CO detected; 3-sigma flux limit 0.16 Jy km/s | **supported**
- H: Does non-LTE excitation matter for CO mass limits in debris discs? | E: Statistical equilibrium models over n, T_k, J | R: Mass limit 4.9e-4 Mearth in radiation-dominated regime vs 3-4 orders lower in LTE | F: LTE assumptions can strongly underestimate CO mass limits | **supported**
- H: Can the limits constrain planetesimal composition? | E: Steady-state balance of CO production and photodissociation | R: CO/H2O ice <~55% (~3% if LTE) | F: Comet-like composition remains consistent with non-detection | **partially**

## Reasoning

- Why this data: High-resolution ALMA Cycle-0 image showed planetesimals in a sharp-edged belt, so data retrieved to search for CO  
  > "In this work, we retrieve these data to search for CO J=3-2 line emission within the belt." (1 Introduction)
- Why this method: _not stated_
- Alternative: Primordial H2-dominated origin considered but disfavoured due to short CO photodissociation timescale  
  > "As such, primordial origin gas is not favoured in this system" (5.1 Production and destruction)
- How they decided it was enough: _not stated_
- Limitation (authors): Detailed chemical modelling beyond scope; T_k assumed uniform; vibrational/electronic states neglected  
  > "Detailed chemical modelling is beyond the scope of this paper" (4.2 Collisional excitation)
- Caveat (inferred, ours): Assumes CO co-located and axisymmetric with dust; partial-ring rescaling is crude
- Caveat (inferred, ours): Adding 10% calibration error to 3-sigma is ad hoc
- Caveat (inferred, ours): Model code and grid details not given
- Caveat (inferred, ours): Result depends on assumed collider species and C/CO, C+/C ratios borrowed from beta Pic

## Reproducibility

- Data public (paper): Archival ALMA Cycle-0 data, project 2011.0.00191.S  
  > "using archival ALMA Cycle-0 data" (Summary and Conclusions)
- Products in archive: _not stated_
- Missing: Non-LTE excitation code
- Missing: Imaging parameters
- Missing: Stellar velocity and ring geometry values
- Missing: Calibration scripts (in Boley2012)
- Data volume (inferred): ~5-20 GB
- Score (inferred): 3/5, Public data and clear flux-limit procedure, but imaging parameters and the excitation code are unstated.
- Rediscovery candidate: yes, Public archival data, stated procedure and numeric flux/mass limits; some imaging details need inference.

## Links

- Method: (cite: Boley2012) (Data reduction and continuum image used)
- Method: (cite: McMullin2007) (CASA)
- Companion: (cite: Boley2012) (Original ALMA Cycle-0 Fomalhaut continuum observations)
- Related: LAMDA database

## Checks

```json
{
 "quotes": 51,
 "quotes_ok": 51,
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
  "facts": 76,
  "stated": 38,
  "rate": 0.5
 },
 "evidence_ok": true
}
```
