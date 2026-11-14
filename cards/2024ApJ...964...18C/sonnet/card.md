# Resolved Measurements of the CO-to-H<SUB>2</SUB> Conversion Factor in 37 Nearby Galaxies

`2024ApJ...964...18C` | The Astrophysical Journal 2024 | first author: Chiang, I-Da | arXiv: 2311.00407 | DOI: 10.3847/1538-4357/ad23ed

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, milky_way_ism
- Question: How does the CO-to-H2 conversion factor (alpha_CO) vary at 2 kpc resolution across 37 nearby galaxies, and how does it scale with local and galaxy-integrated quantities, especially stellar mass surface density?  
  > "We measure the CO-to-H$_2$ conversion factor ($\alpha_\mathrm{CO}$) in 37 galaxies at 2 kpc resolution, using dust surface density inferred from far-infrared emission as a tracer of the gas surface density" (abstract)
- Target **37 nearby galaxies (e.g. NGC0628, NGC3627, NGC4321, NGC5055)**: coordinates _not stated_; z/distance 0.9 to 19.0 Mpc (Table 1)  
  > "We measure $\alpha_{\rm CO}$ in 37 nearby galaxies in this study." (3 Data); distance from Tully et al. 2009 (EDD) per Table 1 notes  
  > "We measure $\alpha_{\rm CO}$ in 37 nearby galaxies in this study." (3 Data)

## Data provenance

- ALMA projects: 2012.1.00650.S, 2015.1.00782.S, 2018.1.01321.S, 2018.1.01651.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: all data convolved to common 2 kpc FWHM Gaussian PSF  
  > "The analyses in this work are done at a common resolution of 2 kpc for all data." (3.2 Uniform Data Processing)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (~230 GHz)
- Line: CO J=1-0 (~115 GHz)
- Other facility **Herschel**: 70-250 micron dust emission for SED fitting  
  > "the 70, 100, 160 and 250 $\mu$m bands with the *Herschel Space Observatory*" (3.1 Physical Quantities and Data Sets)
- Other facility **WISE**: 3.4-22 micron maps for dust SED, stellar mass and SFR  
  > "the 3.4, 4.6, 12 and 22 $\mu$m bands with the Wide-field Infrared Survey Explorer" (3.1 Physical Quantities and Data Sets)
- Other facility **VLA**: new HI 21 cm data (EveryTHINGS, PHANGS-VLA)  
  > "Both surveys have their data observed with the C- and D-configurations of *Karl G. Jansky Very Large Array (VLA)*" (3.1 Physical Quantities and Data Sets)
- Other facility **IRAM 30m / HERACLES**: CO(2-1) maps  
  > "CO $(2{\ensuremath{-}}1)$ data from HERACLES (cite: LEROY09), the PHANGS-ALMA survey (cite: Leroy21_PHANGS-ALMA_CO)" (3.1 Physical Quantities and Data Sets)
- Other facility **Nobeyama (CO Atlas, COMING)**: CO(1-0) maps  
  > "CO $(1{\ensuremath{-}}0)$ data from the COMING survey (cite: Sorai19_COMING) and the CO Atlas (cite: Kuno07_NRO_CO)." (3.1 Physical Quantities and Data Sets)
- External data: PHANGS-ALMA CO(2-1) maps (ALMA data used as published compilation)  
  > "We use the compilation of CO mapping assembled by (cite: Leroy21_CO_Line_Ratios; Leroy23_JWST-CO) from several publicly available CO $(1{\ensuremath{-}}0)$ and CO $(2{\ensuremath{-}}1)$ data:" (3.1 Physical Quantities and Data Sets) [from (cite: Leroy21_PHANGS-ALMA_CO)]
- External data: Dust SED fitting products (Sigma_dust, Umin, gamma, qPAH)  
  > "The details of the IR data processing and dust SED fitting are reported in (cite: Chastenet21_M101) and J. Chastenet et al. (in preparation)." (3.1 Physical Quantities and Data Sets) [from (cite: Chastenet21_M101)]
- External data: Stellar mass and SFR surface density conversions from z0MGS  
  > "using the data and conversion formulae presented in the $z$0MGS survey (cite: LEROY19)" (3.1 Physical Quantities and Data Sets) [from (cite: LEROY19)]
- External data: Metallicity gradients from PHANGS-MUSE  
  > "we adopt radial $12+\log({\rm O/H})$ gradients presented in (cite: Santoro22), which are calculated with the PG16S calibration." (3.1 Physical Quantities and Data Sets) [from (cite: Santoro22)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
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
- smoothing: convolved to circular Gaussian PSF of 2 kpc FWHM; reprojected to pixel size of FWHM/3  
  > "The images are then reprojected onto a grid with a pixel size of one third of the FWHM" (3.2 Uniform Data Processing)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- CO line ratio R21 = 0.65 constant  
  > "For the third method, we adopt the constant $R_{21}=0.65$ from (cite: Leroy21_CO_Line_Ratios)." (2.1 CO cases) [from (cite: Leroy21_CO_Line_Ratios)]
- MIR-dependent R21 formula capped at 1  
  > "we adopt the MIR-dependent formula suggested by (cite: Leroy23_JWST-CO)" (2.1 CO cases) [from (cite: Leroy23_JWST-CO)]
- IR processing and dust SED fitting  
  > "We briefly summarize the process below." (3.1 Physical Quantities and Data Sets) [from (cite: Chastenet21_M101); J. Chastenet et al. (in preparation)]

### Not stated but needed to reproduce (our reading)

- Exact PHANGS-ALMA CO(2-1) product version, moment-map masking and noise maps
- Dust SED fit outputs (J. Chastenet et al. in prep.) and uncertainty maps
- Binning details for plots and regression method for linear fits
- HI processing for EveryTHINGS and PHANGS-VLA (in preparation)

## Analysis recipe

1. **Homogenize data to 2 kpc**: Convolve HI, CO, Sigma_star, Sigma_SFR to 2 kpc Gaussian PSF and reproject to FWHM/3 pixels; inclination-correct  
  > "we convolve them to a circular Gaussian PSF with a FWHM corresponding to 2 kpc, using the `astropy.convolution` package" (3.2 Uniform Data Processing)
   - software: astropy, reproject
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive alpha_CO per pixel**: alpha_CO = (Sigma_dust/(Z x D/M) - Sigma_atom)/W_CO, with errors propagated  
  > "$$\begin{equation} \label{eq:aco_final} \ensuremath{\alpha_{\rm CO}}= \ensuremath{\Sigma_\mathrm{mol}}~W_\mathrm{CO}^{-1}" (2 Calculating alpha_CO)
   - parameter: S/N<1 pixels in W_CO and Sigma_mol blanked  
  > "we blank pixels with $\mathrm{S/N} < 1$ in $W_\mathrm{CO}$ and $\Sigma_\mathrm{mol}$." (3.3 S/N Mask and Completeness)
   - assumption: constant D/M = 0.55 (mean of 0.4-0.7)  
  > "we will take a constant $\mathrm{D/M}=0.55$ (mean of 0.4–0.7) as the fiducial case for deriving $\alpha_{\rm CO}$." (2 Calculating alpha_CO)
   - fitting: _not stated_
   - validation: Compared with Sandstrom et al. 2013 and COMING  
  > "The $\alpha_{\rm CO}$ measured in the three works are in general consistent with each other within uncertainties." (6.3 Comparing to previous alpha_CO surveys)
3. **Regress alpha_CO on local and galaxy-averaged quantities**: Spearman-type correlation and linear regression log alpha_CO = m x + b in completeness >50% zone  
  > "we perform linear regression with the functional form: $$\begin{equation} \log\ensuremath{\alpha_{\rm CO}}=mx+b," (4.1 Correlations with Local Conditions)
   - fitting: Errorbars from 1000 bootstraps  
  > "We first bootstrap the measurements by 1000 times with uncertainties" (4.1 Correlations with Local Conditions)
   - validation: _not stated_
4. **Fit alpha_CO vs Sigma_star power law**: Fit log(alpha/alpha_gal,T) = a log(Sigma_star/100) + b above 100 Msun/pc2; vary D/M and threshold  
  > "We use a power law to characterize this scaling relation" (5 Power-law dependence)
   - parameter: Sigma_star,T = 100 Msun/pc2; D/M 0.1-1  
  > "i.e. $0.1 \leq \text{D/M} \leq 1$." (5.1 Dependence of the power-law index)
   - fitting: Uncertainties from 1000 bootstrap resamplings of galaxies  
  > "The uncertainties of $a$ and $b$ are estimated from 1000 rounds of bootstrap resampling." (5 Power-law dependence)
   - validation: Robustness to D/M, threshold and toy D/M-variation model  
  > "The constant D/M case and the toy model case should sandwich the actual indices." (8 Internal variation of D/M)

## Software

- **astropy** : convolution and interpolation  
  > "using the `astropy.convolution` package" (3.2 Uniform Data Processing)
- **reproject** : reprojecting to common grid  
  > "with the `astropy` affiliated package `reproject`" (3.2 Uniform Data Processing)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mean alpha_CO(2-1) | 9.3 | +4.6/-5.4 | Msun pc-2 (K km/s)-1 | 2 | $9.3^{+4.6}_{-5.4}$ and $4.2^{+1.9}_{-2.0}~M_\odot~pc^{-2}~(K~km~s^{-1})^{-1}$ |
| Mean alpha_CO(1-0) | 4.2 | +1.9/-2.0 | Msun pc-2 (K km/s)-1 | 2 | $9.3^{+4.6}_{-5.4}$ and $4.2^{+1.9}_{-2.0}~M_\odot~pc^{-2}~(K~km~s^{-1})^{-1}$ |
| W_CO-weighted mean alpha_CO(2-1) | 5.69 | not stated | Msun pc-2 (K km/s)-1 | 2 | The $W_{\rm CO}$-weighted mean for $\ensuremath{\alpha_{\textup{CO}\,\ensuremath{(2{\ensuremath{-}}1)}}}$ and $\ensuremath{\alpha_{\textup{CO}\,\ensuremath{(1{\ensuremath{-}}0)}}}$ are 5.69 and 3.33, respectively. |
| Power-law index a, CO(2-1), fiducial | -0.50 | +0.07/-0.06 | dimensionless | 4 | the fitting yields $a=-0.50^{+0.07}_{-0.06}$ and $b=0.03^{+0.01}_{-0.01}$ with $\ensuremath{\Delta_\mathrm{rms}}=0.15~\mathrm{dex}$ for CO $(2{\ensuremath{-}}1)$ |
| Power-law index a, CO(1-0), fiducial | -0.22 | +/-0.06 | dimensionless | 4 | $a=-0.22^{+0.06}_{-0.06}$ and $b=0.003^{+0.01}_{-0.01}$ with $\ensuremath{\Delta_\mathrm{rms}}=0.13~\mathrm{dex}$ for CO $(1{\ensuremath{-}}0)$ |

## Qualitative findings

- alpha_CO anti-correlates most strongly with Ubar, Sigma_SFR and W_CO  
  > "Among them, $\overline{U}$, $\Sigma_{\rm SFR}$, and integrated CO intensity ($W_\mathrm{CO}$) have the strongest anti-correlation with spatially resolved $\alpha_\mathrm{CO}$." (abstract)

## Claim tuples

- H: alpha_CO decreases with stellar mass surface density at high Sigma_star | E: Fit normalized alpha_CO vs Sigma_star above 100 Msun/pc2 for 29/25 galaxies | R: a = -0.50 (CO 2-1), -0.22 (CO 1-0) | F: alpha_CO follows a negative power law in Sigma_star, insensitive to D/M | **supported**
- H: alpha_CO depends on local conditions beyond metallicity | E: Pixel-by-pixel correlations and linear regressions | R: Ubar, Sigma_SFR, W_CO strongest; metallicity correlation moderate to weak | F: Starburst-like conditions drive alpha_CO variation at 2 kpc | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Varying D/M toy model gives steeper indices (a = -0.74 and -0.47), so the relation is not caused by D/M variation  
  > "these indices are steeper than our fiducial case" (8 Internal variation of D/M)
- How they decided it was enough: _not stated_
- Limitation (authors): Data concentrated in narrow metallicity range 8.4-8.6, limiting metallicity analysis  
  > "$>80\%$ of our data is concentrated in a small dynamic range of $8.4 \leq \ensuremath{12+\log({\rm O/H})}\leq 8.6$." (4.1 Correlations with Local Conditions)
- Caveat (inferred, ours): Constant D/M assumption and PG16S metallicity bias propagate directly into alpha_CO
- Caveat (inferred, ours): Dust opacity assumed fixed, degenerate with alpha_CO
- Caveat (inferred, ours): Abstract and summary quote different mean values (9.3 vs 9.7)

## Reproducibility

- Data public (paper): CO data are described as publicly available; new VLA HI data are in preparation  
  > "from several publicly available CO $(1{\ensuremath{-}}0)$ and CO $(2{\ensuremath{-}}1)$ data:" (3.1 Physical Quantities and Data Sets)
- Products in archive: _not stated_
- Missing: Dust SED fit products (in preparation)
- Missing: New EveryTHINGS and PHANGS-VLA HI maps (in preparation)
- Data volume (inferred): Mostly derived maps; tens of GB if PHANGS-ALMA products and IR/HI maps are fetched
- Score (inferred): 3/5, Equations and fiducial assumptions are clear, but key inputs (dust maps, new HI) come from unpublished work and ALMA is only used via a compilation.
- Rediscovery candidate: no, Key dust and HI inputs are unpublished, and ALMA data are used only as published products.

## Links

- Method: (cite: Chastenet21_M101) (dust SED fitting and opacity calibration)
- Method: (cite: LEROY19) (z0MGS stellar mass and SFR prescriptions)
- Companion: (cite: Teng24_alphaCO_dv) (cloud-scale alpha_CO vs velocity dispersion using these measurements)
- Related: PHANGS-ALMA
- Related: HERACLES
- Related: COMING
- Related: z0MGS
- Related: EveryTHINGS
- Related: PHANGS-VLA
- Related: PHANGS-MUSE

## Checks

```json
{
 "quotes": 48,
 "quotes_ok": 48,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 34,
  "rate": 0.453
 },
 "evidence_ok": true
}
```
