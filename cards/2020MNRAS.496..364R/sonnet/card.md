# A molecular absorption line survey towards the AGN of Hydra-A

`2020MNRAS.496..364R` | Monthly Notices of the Royal Astronomical Society 2020 | first author: Rose, Tom | arXiv: 2005.10252 | DOI: 10.1093/mnras/staa1474

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars, astrochemistry
- Question: What molecular species and cloud properties are revealed by multi-line molecular absorption against the Hydra-A AGN, and does the absorption vary over two years?  
  > "high spectral resolution observations of these absorption systems with a wider mix of molecular species are still lacking. This paper marks the beginning of a campaign to address this issue." (Introduction)
- Target **Hydra-A**: coordinates _not stated_; z/distance z = 0.0544±0.0001 (16294±30 km/s); 1.056 kpc/arcsec  
  > "At this redshift, there is a spatial scale of 1.056 kpc arcsec$^{-1}$, meaning that kpc and arcsec scales are approximately equivalent." (Introduction); "This redshift is calculated from MUSE observations of stellar absorption lines (ID: 094.A-0859) and corresponds to a recession velocity of 16294$\pm$30 km s$^{-1}$." (Introduction); distance from MUSE stellar absorption lines (ID 094.A-0859)  
  > "At this redshift, there is a spatial scale of 1.056 kpc arcsec$^{-1}$, meaning that kpc and arcsec scales are approximately equivalent." (Introduction); "This redshift is calculated from MUSE observations of stellar absorption lines (ID: 094.A-0859) and corresponds to a recession velocity of 16294$\pm$30 km s$^{-1}$." (Introduction)

## Data provenance

- ALMA projects: 2016.1.01214.S, 2018.1.01471.S, 2017.1.00629.S
- bands: Bands 3, 5, 6  
  > "| ALMA band | 3 | 5 | 6 | 3 | 5 |" (Table 1)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-1, C43-4, C43-5, C43-6, C43-5  
  > "| ALMA configuration | C43-1 | C43-4 | C43-5 | C43-6 | C43-5 |" (Table 1)
- baselines: max baseline 161, 784, 1400, 2500, 1400 m  
  > "| Maximum baseline (m) | 161 | 784 | 1400 | 2500 | 1400 |" (Table 1)
- angular resolution: beams 2.3x1.6, 0.60x0.46, 0.27x0.25, 0.47x0.29, 0.38x0.32 arcsec  
  > "| Beam dimensions (") | $2.3 \times 1.6$ | $0.60 \times 0.46$ | $0.27 \times 0.25$ | $0.47\times 0.29$ | $0.38 \times 0.32$ |" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: noise per channel 0.27-1.33 mJy/beam  
  > "| Noise/channel (mJy/beam) | 1.01 | 0.27/0.27/0.27 | 1.33/0.47/0.47 | 0.58/0.56/0.58 | 0.57/0.63 |" (Table 1)
- time on source: 44, 215, 95, 48, 85 min  
  > "| Integration time (mins) | 44 | 215 | 95 | 48 | 85 |" (Table 1)
- observing dates: 2018 Jul 18 to 2019 Sep 24 (per Table 1)  
  > "| Observation date | 2018 Jul 18 | 2018 Dec 12 | 2018 Oct 30 | 2019 Sep 24 | 2018 Nov 16 |" (Table 1)
- pi or archival as stated: _not stated_
- Line: CO 1-0 (115.271208 GHz)
- Line: CO 2-1 (230.538000 GHz)
- Line: HCO+ 1-0 (89.188525 GHz)
- Other facility **MUSE**: systemic redshift from stellar absorption lines  
  > "This redshift is calculated from MUSE observations of stellar absorption lines (ID: 094.A-0859)" (Introduction)
- External data: X-ray line-of-sight column density N_H = 3.5e22 cm^-2  
  > "(cite: Russell2013) find a line of sight column density of $N_{H} = 3.5 \times 10^{22} \textnormal{cm}^{-2}$ from X-ray observations." (6.3 continuum size) [from (cite: Russell2013)]
- External data: 2016 CO(2-1) absorption observation used for variability comparison  
  > "CO(2-1) absorption was first detected in Hydra-A in October 2016 (cite: Rose2019a)" (6.4 Absorption variability) [from (cite: Rose2019a)]

## Processing

### Calibration

- pipeline or manual: calibrated data produced by ALMA observatory; self-calibration done as part of pipeline  
  > "The calibrated data were produced by the ALMA observatory and following their delivery, we made channel maps at maximal spectral resolution." (3 Data Processing)
- casa version: CASA 5.6.0  
  > "The data presented throughout this paper were handled using CASA version 5.6.0" (3 Data Processing)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: channel maps at maximal spectral resolution; spectra extracted from region equal to synthesized beam FWHM centred on continuum  
  > "All are extracted from a region centered on the continuum source with a size equal to the synthesized beam’s FHWM." (2 Observations and target lines)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Emission subtraction and 2016 CO(2-1) absorption spectrum, and flux shift handling  
  > "the degree to which the emission compensates for the absorption cannot be known precisely (cite: Rose2019a)" (Footnote 3) [from (cite: Rose2019a)]
- Optical depth correction factor for column densities  
  > "We therefore apply an optical depth correction factor from (cite: Magnum2015)" (5 Column Density Estimates) [from (cite: Magnum2015)]

### Not stated but needed to reproduce (our reading)

- tclean/imaging parameters (weighting, robust, cell, image size, continuum subtraction, line-free channels)
- Continuum RMS used and how continuum level extracted
- Flux calibrators and flux scale uncertainty
- Partition functions, Einstein A values and spectroscopic database used
- How the 2016 and 2018 data were matched in resolution for variability test
- Exact fitting algorithm/software for Gaussian fits

## Analysis recipe

1. **Extract absorption spectra**: Channel maps at maximal spectral resolution; spectra extracted from a beam-sized region at the continuum source  
  > "All are extracted from a region centered on the continuum source with a size equal to the synthesized beam’s FHWM." (2 Observations and target lines)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Remove CO emission**: Gaussian fit to broad emission with absorption velocities (-50 to +10 km/s) masked  
  > "First, a Gaussian fit is made to the emission. During the fitting process, the spectral bins in which absorption can be seen are masked, approximately $-50$ to $+10$ km s$^{-1}$." (3 Data Processing)
   - fitting: _not stated_
   - validation: Mask limits chosen by lowest reduced chi2 of flat-line fit to non-masked residual  
  > "The chosen range produces a spectrum with the lowest $\chi^{2}_{\nu}$ value when the non-masked, emission-subtracted region is fitted to a flat line." (3 Data Processing)
3. **Multi-Gaussian line fit**: Common 12-Gaussian fit with fixed sigma and vcen across spectra, free non-positive amplitudes  
  > "Each has a fixed $\sigma$ and $v_{\textnormal{cen}}$ across all of the spectra, but a freely varying amplitude." (3.1 Line fitting procedure)
   - parameter: initial 10 Gaussians from CO(2-1), HCO+(2-1), HCN(2-1); two added after >5 sigma residuals  
  > "The initial 10 Gaussian fit is found to be insufficient, with $> 5 \sigma$ absorption remaining in the residuals across several neighbouring channels." (3.1 Line fitting procedure)
   - fitting: Monte Carlo: 10000 simulated spectra with Gaussian noise at continuum RMS; 1sigma from 15.865 per cent percentiles  
  > "Following this, 10 000 simulated spectra are created based upon the observed spectrum." (3.1 Line fitting procedure)
   - validation: vcen freed per line gave values consistent with fixed ones  
  > "The v$_\textnormal{cen}$ values resulting from this process were consistent with the fixed values" (3.1 Line fitting procedure)
4. **Optical depths**: tau = -ln(1 - Iobs/(fc Icont))  
  > "The apparent optical depth of an absorption line, $\tau$, can be derived according to the equation" (3.2 Optical depth calculations)
   - assumption: covering factor 0.7 for G2, 1 for others  
  > "We assume a covering factor of 0.7 for the G2 absorption feature at $-43.1$ km s$^{-1}$." (3.2 Optical depth calculations)
   - fitting: _not stated_
   - validation: _not stated_
5. **Excitation and kinetic temperatures**: Tex from HCO+ (1-0)/(2-1) integrated tau ratio; Tkin = 10 x I(HCN)/I(HNC)  
  > "the HCO$^{+}$(1-0) and HCO$^{+}$(2-1) velocity integrated optical depths are related by" (4.1 Excitation temperature estimates)
   - assumption: optically thin and LTE  
  > "This requires that the gas is optically thin and in local thermodynamic equilibrium" (4.1 Excitation temperature estimates)
   - fitting: _not stated_
   - validation: HCN and HCO+ average Tex compare well  
  > "which compares well with the value of 5.8$^{+ 0.7 }_{- 0.7}$ K" (4.1 Excitation temperature estimates)
6. **Column densities, sizes, masses**: Optically thin N with optical-depth correction tau/(1-exp(-tau)); Larson sigma-D relation; virial mass M=D sigma^2/2G  
  > "By further assuming the absorption regions are in virial equilibrium, their total masses, $M_{\textnormal{tot}}$, can be estimated using the virial theorem" (6.2 Cloud size and mass estimates)
   - assumption: Milky Way sigma=D^0.5 relation holds; virial equilibrium  
  > "so the relation should still hold true." (6.2 Cloud size and mass estimates)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.6.0: data handling and channel maps  
  > "The data presented throughout this paper were handled using CASA version 5.6.0" (3 Data Processing)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of absorbing Gaussian components | 12 | not stated | dimensionless | 3 | The minimum number of Gaussians required to provide a good fit for all of the lines is found to be 12. |
| Average Tex from HCN | 5.5 | +2.0/-1.6 | K | 5 | This gives an excitation temperature of 5.5$^{+ 2.0 }_{- 1.6 }$ K |
| Average Tex from HCO+ | 5.8 | +0.7/-0.7 | K | 5 | 5.8$^{+ 0.7 }_{- 0.7}$ K when the same method is applied |
| Average kinetic temperature | 33 | +9/-8 | K | 5 | which we find to be $33^{+9}_{-8}$K |
| Total virial mass of absorbers | 4e4 | not stated | Msun | 6 | The total mass inferred from the molecular absorption seen in Hydra-A is $4\times 10 ^{4} M_{\odot}$ |
| Continuum source diameter | 7 (4 after correction) | not stated | pc | 6 | Hydra-A’s central continuum source has an apparent diameter of 7 pc |
| Significance of absorption variability | 3.4 | not stated | sigma | 0 | has a combined significance of $3.4 \sigma$ |

## Qualitative findings

- HCO+ and HCN are stronger, more ubiquitous tracers than CO for absorption searches  
  > "which we find to be stronger, more ubiquitous and more consistent tracers than CO" (Conclusions)

## Claim tuples

- H: Do the absorption profiles trace individual cold clouds similar to Milky Way clouds? | E: 12-Gaussian fit, Tex, column densities, sigma compared to Milky Way | R: sigma ~1 km/s, Tex 5-10 K, diameters 1-10 pc, masses tens to thousands Msun | F: clumpy ISM of clouds similar to Milky Way; environment pressure negligible vs self-gravity | **supported**
- H: Does absorption vary between 2016 and 2018? | E: Compare CO(2-1) absorption profiles from Cycle 4 and Cycle 6 | R: decrease between -20 and -5 km/s at 3.4 sigma | F: possible variability, likely from changing background illumination | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Cloud transverse motion, jet precession and chemistry changes considered less likely explanations for variability  
  > "so this can ruled out with a fair degree of confidence." (6.4 Absorption variability)
- How they decided it was enough: _not stated_
- Limitation (authors): Tex assumes optically thin LTE, which the results contradict; covering factors give lower limits on tau  
  > "the values should only be treated as approximations" (4.1 Excitation temperature estimates)
- Caveat (inferred, ours): Variability only 3.4 sigma with ad hoc 0.1 mJy shift
- Caveat (inferred, ours): Covering factor and Larson relation assumptions drive masses
- Caveat (inferred, ours): Tex from LTE method inconsistent with sub-thermal finding

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: Fitting code
- Missing: Spectroscopic constants source
- Data volume (inferred): ~100-300 GB raw across three projects
- Score (inferred): 3/5, Public ALMA data and clear spectral analysis, but imaging settings and fitting details missing.
- Rediscovery candidate: yes, Data public, spectra analysis recipe largely given with numeric tables of tau and N.

## Links

- Method: (cite: Magnum2015) (column density and optical depth correction)
- Method: (cite: Hacar2019) (HCN/HNC kinetic temperature relation)
- Companion: (cite: Rose2019a) (earlier Hydra-A CO absorption)
- Companion: (cite: Rose2019b) (BCG absorption sample)

## Checks

```json
{
 "quotes": 54,
 "quotes_ok": 54,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 36,
  "rate": 0.486
 },
 "evidence_ok": true
}
```
