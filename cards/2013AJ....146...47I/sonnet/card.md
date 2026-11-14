# High-density Molecular Gas Properties of the Starburst Galaxy NGC 1614 Revealed with ALMA

`2013AJ....146...47I` | The Astronomical Journal 2013 | first author: Imanishi, Masatoshi | arXiv: 1307.3694 | DOI: 10.1088/0004-6256/146/3/47

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation, astrochemistry
- Question: What are the spatial distribution, dynamics and HCN/HCO+/HNC J=4-3 flux ratios of high-density molecular gas in the starburst LIRG NGC 1614?  
  > "We thus performed ALMA band 7 (275–373 GHz) observations of NGC 1614 to study the emission properties of HCN J = 4–3, HCO$^{+}$ J = 4–3, and HNC J = 4–3 lines." (1 Introduction)
- Target **NGC 1614**: coordinates continuum peak (04 34 00.01, -08 34 44.9) J2000  
  > "NGC 1614 (z = 0.016; L$_{\rm IR}$ = 10$^{11.6}$L$_{\odot}$) is a well-studied, nearby LIRG." (1 Introduction); "where 1$''$ corresponds to $\sim$320 pc at the distance of NGC 1614 (z = 0.016)" (1 Introduction); z/distance z = 0.016; 1'' ~ 320 pc  
  > "NGC 1614 (z = 0.016; L$_{\rm IR}$ = 10$^{11.6}$L$_{\odot}$) is a well-studied, nearby LIRG." (1 Introduction); "where 1$''$ corresponds to $\sim$320 pc at the distance of NGC 1614 (z = 0.016)" (1 Introduction); distance from redshift with H0=71, OmegaM=0.27, OmegaLambda=0.73 (Komatsu et al. 2009)  
  > "NGC 1614 (z = 0.016; L$_{\rm IR}$ = 10$^{11.6}$L$_{\odot}$) is a well-studied, nearby LIRG." (1 Introduction); "where 1$''$ corresponds to $\sim$320 pc at the distance of NGC 1614 (z = 0.016)" (1 Introduction)

## Data provenance

- ALMA projects: 2011.0.00020.S
- bands: Band 7 (275–373 GHz)  
  > "We thus performed ALMA band 7 (275–373 GHz) observations of NGC 1614" (1 Introduction)
- frequencies and spectral setup: 1.875 GHz mode, 3840 channels; HCN center 348.922 GHz, HCO+ 350.920 GHz, continuum 337.106 and 338.681 GHz; HNC 356.920 GHz, continuum 345.079 GHz  
  > "We adopted the widest 1.875 GHz band mode, and the total channel number was 3840." (2 Observations and Data Analysis); "The HNC line was covered with one spectral window ($\nu_{\rm center}$ = 356.920 GHz)" (2 Observations and Data Analysis)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.5'' x 1.3''  
  > "Our ALMA map has a resolution of 1.5$"$ $\times$ 1.3$"$." (3 Results)
- max recoverable scale: ~6'' at ~350 GHz  
  > "it is not sensitive to spatially extended structure beyond the maximum scale, which is $\sim$6$''$ at $\sim$350 GHz in ALMA Cycle 0" (1 Introduction)
- sensitivity: _not stated_
- time on source: ~26 min (HCN/HCO+), ~25 min (HNC)  
  > "The net on-source exposure time for the HCN/HCO$^{+}$ J = 4–3 line observation of NGC 1614 was $\sim$26 min." (2 Observations and Data Analysis)
- observing dates: 2011 November 15, 16 antennas  
  > "| HCN/HCO$^{+}$ J=4–3 | 2011 November 15 | 16      | 3C454.3  | Callisto | J0423$-$013 |" (Table 2)
- pi or archival as stated: PI M. Imanishi, Cycle 0  
  > "within the program 2011.0.00020.S (PI = M. Imanishi)" (2 Observations and Data Analysis)
- Line: HCN J=4-3 (354.505 GHz)
- Line: HCO+ J=4-3 (356.734 GHz)
- Line: HNC J=4-3 (362.630 GHz)
- Line: CS J=7-6 (342.883 GHz)
- External data: HCN J=1-0 flux of 7.2 Jy km/s from single dish  
  > "The HCN J = 1–0 flux of NGC 1614 was found to be 7.2 \[Jy km s$^{-1}$\] by (cite: gao04)" (4.3 Flux ratios of dense gas tracers) [from (cite: gao04)]
- External data: Inclination i = 51 deg  
  > "where the inclination angle i = 51$^{\circ}$ is adopted (cite: der88; alo01)" (4.2 Dynamics of dense molecular gas) [from (cite: der88; alo01)]

## Processing

### Calibration

- pipeline or manual: Started from calibrated data provided by JAO  
  > "We started data analysis from calibrated data provided by the Joint ALMA Observatory." (2 Observations and Data Analysis)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Calibrated data from JAO used  
  > "We started data analysis from calibrated data provided by the Joint ALMA Observatory." (2 Observations and Data Analysis)
- flux calibrator: Callisto (bandpass 3C454.3, phase J0423-013)  
  > "| HNC J=4–3           | 2011 November 15 | 16      | 3C454.3  | Callisto | J0423$-$013 |" (Table 2)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: clean  
  > "We subtracted this continuum level and performed the task “clean” for molecular emission lines." (2 Observations and Data Analysis)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 0.3'' per pixel  
  > "We employed 40-channel spectral binning ($\sim$17 km s$^{-1}$) and 0.3$''$ pixel$^{-1}$ spatial binning in this clean procedure." (2 Observations and Data Analysis)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum level estimated from line-free channels and subtracted  
  > "We then selected channels that were free from strong line emission to estimate the continuum flux level." (2 Observations and Data Analysis)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: 40-channel spectral binning (~17 km/s)  
  > "We employed 40-channel spectral binning ($\sim$17 km s$^{-1}$)" (2 Observations and Data Analysis)
- final beam: 1.5x1.3 (76 deg) lines HCN/HCO+; 1.3x1.3 HNC  
  > "| HCN J=4–3       | all       | 1.7 (12$\sigma$)               | 0.14                           | 1.5 $\times$ 1.3 (76$^{\circ}$)         |" (Table 4)
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- CASA version
- clean weighting/robust, deconvolver, threshold, masks
- line-free channel ranges
- image size
- flux calibrator model and flux scale uncertainty
- primary beam correction
- Gaussian fitting software and procedure
- how line luminosity was computed in detail

## Analysis recipe

1. **Image continuum and lines**: Subtract continuum from line-free channels; clean lines and continuum  
  > "We subtracted this continuum level and performed the task “clean” for molecular emission lines." (2 Observations and Data Analysis)
   - software: CASA clean
   - parameter: 40-channel binning, 0.3'' pixels  
  > "We employed 40-channel spectral binning ($\sim$17 km s$^{-1}$) and 0.3$''$ pixel$^{-1}$ spatial binning in this clean procedure." (2 Observations and Data Analysis)
   - fitting: _not stated_
   - validation: Continuum well subtracted in spectra  
  > "Continuum emission is found to be well subtracted in the spectra (Figure 2 right panels)" (3 Results)
2. **Moment maps and spectra, Gaussian fits, line luminosity**: Moment 0/1/2 maps; red (>4800) and blue (<4800 km/s) components; double Gaussian fits to spectra; luminosities from Solomon & Vanden Bout equations  
  > "We applied double Gaussian fits." (3 Results); "where we adopted equations (2) and (3) of (cite: sol05)" (3 Results)
   - parameter: nuclear v_opt = 4800 km/s  
  > "(v$_{\rm opt}$ = 4800 \[km s$^{-1}$\] for z = 0.016)" (3 Results)
   - fitting: Double Gaussian (triple for HCO+) fits  
  > "For HCO$^{+}$ J = 4–3 emission, a triple Gaussian fit was also applied because three emission peaks were seen." (3 Results)
   - validation: _not stated_
3. **Dynamical mass**: M_dyn = r v^2/G/sin(i)^2 from HCO+ moment 1, v~100 km/s at 1.5-2''  
  > "M$_{\rm dyn}$ = rv$^{2}$/G/sin(i)$^{2}$ = 1.5–2.5 $\times$ 10$^{9}$M$_{\odot}$" (4.2 Dynamics of dense molecular gas)
   - assumption: Rotating disk, inclination 51 deg  
  > "where the inclination angle i = 51$^{\circ}$ is adopted (cite: der88; alo01)" (4.2 Dynamics of dense molecular gas)
   - fitting: _not stated_
   - validation: Compared with previous estimates  
  > "This mass is comparable to the previously estimated values (cite: shi94; alo01; ols10)." (4.2 Dynamics of dense molecular gas)
4. **Flux ratios and excitation**: Compare HCN/HCO+ and HCN/HNC ratios; compare HCN 4-3 with thermal expectation from single-dish J=1-0  
  > "Under thermal excitation, the HCN J = 4–3 flux is expected to be 16 times higher than J = 1–0, and so $\sim$115 \[Jy km s$^{-1}$\]." (4.3 Flux ratios of dense gas tracers)
   - assumption: Missing flux factor ~2  
  > "Even assuming a missing flux of a factor of $\sim$2, the HCN J = 4–3 flux of NGC 1614 is 5.6 \[Jy km s$^{-1}$\]" (4.3 Flux ratios of dense gas tracers)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA clean** : Imaging of lines and continuum  
  > "The “clean” procedure was applied also to the continuum data." (2 Observations and Data Analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Dynamical mass within 1.5–2'' radius | 1.5–2.5e9 | not stated | Msun | 3 | M$_{\rm dyn}$ = rv$^{2}$/G/sin(i)$^{2}$ = 1.5–2.5 $\times$ 10$^{9}$M$_{\odot}$ |
| HCN J=4-3 total flux | 2.8 | 0.8 | Jy km/s | 2 | / HCN J=4–3       / all       / 4733$\pm$25 + 4857$\pm$14            / 11$\pm$2 + 12$\pm$4            / 171$\pm$52 + 73$\pm$30           / 2.8$\pm$0.8        / |
| HCO+ J=4-3 total flux (double Gaussian) | 16.0 | 1.4 | Jy km/s | 2 | 16.0$\pm$1.4$^{a}$ |
| HNC J=4-3 total flux | 1.7 | 0.5 | Jy km/s | 2 | / HNC J=4–3       / all       / 4718$\pm$11 + 4859$\pm$16            / 10$\pm$2 + 7.8$\pm$2.7         / 125$\pm$27 + 50$\pm$45           / 1.7$\pm$0.5        / |
| Continuum a peak flux at 344 GHz | 14.6 | rms 0.32 | mJy/beam | 1 | / a / 344 / 14.6 (45$\sigma$) $^{a}$ / (04 34 00.01, $-$08 34 44.9) / 0.32 / 1.5 $\times$ 1.3 (81$^{\circ}$) / |
| HCN J=4-3 luminosity | 4.8e3 | 1.4e3 | Lsun | 2 | / HCN J=4–3 / (4.8$\pm$1.4)$\times$10$^{3}$ / (3.4$\pm$1.0)$\times$10$^{6}$ / |
| Peak velocity dispersion in nucleus | ~80 | not stated | km/s | 2 | The observed velocity dispersion is highest in the nuclear region with $\sim$80 km s$^{-1}$ (Figure 4) |

## Qualitative findings

- Northern gas redshifted, southern blueshifted; red/blue peaks 0.6'' N/S of nucleus, coinciding with dusty starburst ring regions  
  > "the northern (southern) side of the nucleus is redshifted (blueshifted) with respect to the nuclear velocity of this galaxy." (abstract)

## Claim tuples

- H: Dense gas traces active dusty starbursts | E: Mapped HCN/HCO+/HNC 4-3 kinematics and compared with IR/radio | R: Red/blue peaks ~0.6'' N/S coincide with strong 3.3um PAH regions | F: Starbursts occur in dense gas | **supported**
- H: Dense-gas dynamics give a mass consistent with earlier estimates | E: Rotation from HCO+ moment 1 | R: 1.5–2.5e9 Msun within 1.5–2'' | F: Consistent with previous estimates | **supported**
- H: Starburst line ratios at J=4-3 resemble J=1-0 | E: Compared line fluxes | R: HCN<HCO+ and HCN>HNC in all regions | F: Similar trend to J=1-0 starbursts | **supported**

## Reasoning

- Why this data: Compact (~2'') starburst-dominated nucleus suits ALMA Cycle 0 limited maximum scale  
  > "make NGC 1614 an ideal target to investigate the spatial distribution and dynamics of dense molecular gas in merging LIRG nuclei" (1 Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Missing flux for emission >6''; HCN 4-3 sub-thermal conclusion depends on it  
  > "The smaller flux of our ALMA data could partly be caused by missing flux" (4.3 Flux ratios of dense gas tracers)
- Caveat (inferred, ours): Low resolution (1.5'') and beam smearing affect dynamical mass
- Caveat (inferred, ours): Single inclination adopted; no kinematic modelling
- Caveat (inferred, ours): Missing-flux factor of 2 is assumed
- Caveat (inferred, ours): Low S/N for HNC and HCN

## Reproducibility

- Data public (paper): Cycle 0 program ID given; public status not explicit  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00020.S ." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version and clean parameters
- Missing: line-free channel selection
- Missing: Gaussian fit details
- Data volume (inferred): ~ a few GB
- Score (inferred): 3/5, Data identified and simple analysis, but imaging parameters and versions unstated.
- Rediscovery candidate: yes, Archive data, simple moment/Gaussian analysis with numeric results, though settings need guessing.

## Links

- Companion: Imanishi et al., in preparation (Other ALMA targets with AGN HCN/HCO+ 4-3 ratios)

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
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 64,
  "stated": 37,
  "rate": 0.578
 },
 "evidence_ok": true
}
```
