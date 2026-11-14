# The Properties of the Interstellar Medium of Galaxies across Time as Traced by the Neutral Atomic Carbon [C I]

`2020ApJ...890...24V` | The Astrophysical Journal 2020 | first author: Valentino, Francesco | arXiv: 2001.01734 | DOI: 10.3847/1538-4357/ab6603

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, nearby_galaxies, milky_way_ism
- Question: How do [C I] and mid/high-J CO line ratios, gas excitation temperature and PDR conditions vary across main sequence galaxies, local LIRGs and SMGs, and does a semi-analytical model reproduce the [C I] luminosities?  
  > "simultaneously studying multiple line transitions, allowing us to study the properties of the interstellar medium across redshift and galaxy types." (1 Introduction)
- Target **7 main sequence galaxies at z~1.2 in COSMOS (IDs 18538, 19021, 35349, 188090, 192337, 208273, 256703)**: coordinates _not stated_; z/distance z_spec 1.1-1.3 (Table 2)  
  > "we collected Band 7 observations for a set of 7 galaxies extracted from the sample in V18 (Project ID: 2018.1.00635.S, PI: F. Valentino)." (2.1.2 The [C I](3P2-3P1) transition); distance from spectroscopic redshifts from COSMOS master catalog / V18  
  > "we collected Band 7 observations for a set of 7 galaxies extracted from the sample in V18 (Project ID: 2018.1.00635.S, PI: F. Valentino)." (2.1.2 The [C I](3P2-3P1) transition)

## Data provenance

- ALMA projects: 2018.1.00635.S, 2016.1.01040.S, 2015.1.00260.S, 2016.1.00171.S
- bands: Band 7 (Cycle 6, new); Band 6 (Cycle 4, V18)  
  > "During ALMA Cycle 6, we collected Band 7 observations for a set of 7 galaxies" (2.1.2 The [C I](3P2-3P1) transition)
- frequencies and spectral setup: contiguous spectral windows of 1.875 GHz, 7.8 MHz resolution (~7 km/s)  
  > "within contiguous spectral windows of 1.875 GHz and with a spectral resolution of 7.8 MHz ($\sim7$ km s$^{-1}$)" (2.1.2 The [C I](3P2-3P1) transition)
- continuum bandwidth: 7.5 GHz at ~850 um  
  > "We concurrently measured the continuum emission at observed $\sim850$ $\mu$m over 7.5 GHz" (2.1.2 The [C I](3P2-3P1) transition)
- arrays: _not stated_
- configurations: C43-1  
  > "Data were collected in the C43-1 configuration for a final synthesized beam of $\sim0.9$”." (2.1.2 The [C I](3P2-3P1) transition)
- baselines: _not stated_
- angular resolution: ~0.9 arcsec  
  > "Data were collected in the C43-1 configuration for a final synthesized beam of $\sim0.9$”." (2.1.2 The [C I](3P2-3P1) transition)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 5 of 7 targets full integration; 2 (#35349, #208273) at 75% of request  
  > "Five out of $7$ targets were observed for the full proposed integration, the remaining being imaged for 75% of the initial request" (2.1.2 The [C I](3P2-3P1) transition)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: [C I] 3P2-3P1 (809.344 GHz)
- Line: [C I] 3P1-3P0 (492.161 GHz)
- Other facility **Herschel (PACS/SPIRE/FTS)**: far-IR photometry for SEDs and local galaxy [C I]/CO lines  
  > "compilation of *Herschel*/Fourier Transform Spectrometer (FTS) observations in the Herschel Science Archive of local galaxies" (2.2 Local galaxies)
- Other facility **NOEMA / IRAM / APEX literature observations**: [C I] and CO for SMGs  
  > "recent detections with the NOEMA interferometer (Cortzen et al., submitted)" (2.3 High-redshift SMGs)
- External data: ALMA [C I](1-0), CO(4-3) of 10 main sequence galaxies  
  > "presented a set of 10 main sequence galaxies, selected from the Ultra Deep Survey (UDS) and in the COSMOS fields" (2.1.1) [from (cite: bourne_2019)]
- External data: Local IR-luminous galaxies [C I] and CO from Herschel FTS  
  > "We retrieve 32 (126) objects with a \[C I\]$(^3P_1\,-\,^{3}P_0)$ (\[C I\]$(^3P_2\, -\, ^{3}P_1)$) detection at $>3\sigma$." (2.2 Local galaxies) [from (cite: liu_2015; kamenetzky_2016)]
- External data: SMG/QSO [C I] and CO compilation  
  > "Altogether we collected information about 60 SMGs at $z\sim2-5$" (2.3 High-redshift SMGs) [from (cite: walter_2011; bothwell_2017; canameras_2018; yang_2017; dannerbauer_2019; jin_2019)]
- Simulation/model as data: Santa Cruz semi-analytical model predictions of [C I], CO luminosities, and PDR grids from Kaufman et al. 1999 via PDRT  
  > "we compared the \[C I\] and CO line luminosities from our compilation with the semi-analytical model from (cite: popping_2019)." (4.3)

## Processing

### Calibration

- pipeline or manual: standard pipeline with CASA plus customized GILDAS scripts, following V18 and Daddi et al. 2015  
  > "The data were reduced with a combination of the standard pipeline with CASA (cite: mcmullin_2007) and a series of customized scripts with GILDAS" (2.1.2)
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
- continuum subtraction: continuum measured excluding line channels, slope nu=3.7 (beta=1.7)  
  > "assuming an intrinsic slope of $\nu=3.7$ ($\beta = 1.7$), excluding the channels covered by the emission lines" (2.1.2)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA reduction and flux extraction procedure  
  > "following the procedure described in V18 and (cite: daddi_2015)" (2.1.2) [from (cite: valentino_2018); (cite: daddi_2015)]
- SED fitting prescriptions (Draine & Li models with AGN templates)  
  > "following the prescriptions of (cite: magdis_2012)" (2.1.1) [from (cite: magdis_2012)]
- Iterative uv-plane flux extraction with GILDAS/UVFIT  
  > "using the iterative procedure described in detail in our previous work" (Total recovered fluxes) [from (cite: daddi_2015; coogan_2018; valentino_2018; puglisi_2019)]
- Beam-matching of local line luminosities to L_IR  
  > "As described in V18, we beam-matched the line luminosities to $L_{\rm IR}$" (2.2) [from (cite: valentino_2018)]

### Not stated but needed to reproduce (our reading)

- CASA version and pipeline version
- imaging parameters (weighting, robust, cell, image size, cleaning)
- flux calibrators and calibration uncertainty
- line-free channels used for continuum
- exact channel ranges for line integration per source
- target coordinates
- exact initial Gaussian fit constraints in MPFIT
- PDR grid details (A_V treatment aside), fit weights and error handling for upper limits
- full homogenized literature tables (only released as FITS)

## Analysis recipe

1. **Extract line fluxes and continuum**: 1D spectra extracted at brightest peak position, integrated over channels maximizing S/N, increased by 10% for wings; GILDAS UVFIT point/Gaussian extraction; MPFIT single/double Gaussian fits with fixed z and widths from highest S/N line  
  > "These line fluxes were then increased by 10% to account for emission in extended wings as found by modeling the spectra with single or double Gaussian peaks." (2.1.2)
   - software: CASA, GILDAS, MPFIT
   - fitting: chi2 minimization MPFIT, single and double Gaussians with constant velocity widths  
  > "using the $\chi^2$-minimization algorithm MPFIT (cite: markwardt_2009) and using both single and double Gaussians with constant velocity widths" (2.1.2)
   - validation: flux losses for unresolved sources estimated by injecting Gaussians; corrections <5% not applied  
  > "Changes at $<5$% are not significant and therefore not applied." (Total recovered fluxes)
2. **SED modeling for L_IR, T_dust, dust mass**: Draine & Li 2007 models plus Mullaney AGN templates; MBB for T_dust; literature samples refit homogeneously  
  > "We adopted the expanded (cite: draine_2007) models and incorporated the AGN templates by (cite: mullaney_2011)" (2.1.1)
   - assumption: AGN flag if >=1/3 of L_IR from AGN with S/N>10  
  > "we flag as “AGN” objects with at least a 1/3 contribution to the total $L_{\rm IR}$ from an active nucleus" (2.1.1)
   - fitting: _not stated_
   - validation: AGN selection cross-checked against IRAC color criterion  
  > "We cross-checked this selection against the IRAC color criterion by (cite: donley_2012), retrieving consistent results." (2.1.1)
3. **Compare line-ratio distributions between samples**: Non-parametric two-sample tests with censored data (logrank, Gehan, Peto-Peto, Peto-Prentice) and Kaplan-Meier means  
  > "This suite of tests includes the logrank, the Gehan, Peto & Peto, and Peto & Prentice Generalized Wilcoxon tests." (3.1)
   - software: IRAF/STSDAS twosampt
   - assumption: CO(3-2)/(4-3)=0.57, CO(5-4)/(4-3)=1.36 (SMGs) and 0.92 (MS) used to correct to CO(4-3)  
  > "$L_{\rm CO(3-2)}$/$L_{\rm CO(4-3)}$$=0.57$ and $L_{\rm CO(5-4)}$/$L_{\rm CO(4-3)}$$=1.36$" (3.1)
   - fitting: _not stated_
   - validation: results unchanged with median corrections  
  > "The results do not change adopting median corrections." (3.1)
4. **Derive excitation temperature and correlations**: T_exc = 38.8/ln(2.11/R) assuming LTE and optically thin; correlation coefficients and generalized Kendall tau (bhkmethod) with limits  
  > "$T_{\rm exc} / \mathrm{K} = 38.8 /
\mathrm{ln}(2.11/R)$" (3.2)
   - software: IRAF bhkmethod
   - assumption: LTE and optically thin [C I] lines  
  > "which further requires the lines to be optically thin" (3.2)
   - fitting: _not stated_
   - validation: _not stated_
5. **PDR modeling of line ratios**: Kaufman et al. 1999 1D PDR models via PDR Toolbox; grid rebinned 5x finer; chi2 minimization on [CI]/CO/IR ratios; IR intensity = 2x1.3e-4 G0 erg/cm2/s/sr  
  > "We computed the IR intensity map as $2 \times 1.3\times10^{-4} G_0$ erg cm$^{-2}$ s$^{-1}$ sr$^{-1}$" (4.1)
   - software: PDR Toolbox
   - parameter: 90% interval from Delta chi2<2.71; bootstrap 1000 times within errors  
  > "fixing $\Delta \chi^{2} <
2.71$ corresponding to a 90% confidence interval" (4.1)
   - assumption: constant attenuation A_V=1.8 mag  
  > "given the assumption of a moderate constant attenuation $A_{\rm
  V}=1.8$ mag" (4.1.1)
   - fitting: chi2 minimization on grid with bootstrap  
  > "The best-fit model results from the $\chi^2$ minimization of the line and continuum emission ratios." (4.1)
   - validation: tested [C I](2-1) vs (1-0) and [C II] vs L_IR  
  > "Figure [\[fig:ci_test\]](#fig:ci_test) shows that, despite the large scatter, modeling \[C II\] or $L_{\rm IR}$ gives consistent results." (4.1.1)
6. **Compare with Santa Cruz semi-analytical model**: Overplot observed [C I], CO(4-3) luminosities vs L_IR with Popping et al. 2019 fiducial model, SFR converted to L_IR with Kennicutt 1998 (Chabrier IMF)  
  > "we converted the tracks originally expressed as a function of SFR into $L_{\rm IR}$ by applying the (cite: kennicutt_1998) conversion" (4.3)
   - fitting: _not stated_
   - validation: alternative Murphy 2011 conversion changes L_IR by 0.16 dex without changing conclusions  
  > "Using the latter results in 0.16 dex lower $L_{\rm IR}$ for a fixed SFR than adopting (cite: kennicutt_1998)" (4.3)

## Software

- **CASA** : standard pipeline reduction  
  > "standard pipeline with CASA (cite: mcmullin_2007)" (2.1.2)
- **GILDAS** : custom scripts and UVFIT flux extraction  
  > "The signal is extracted with GILDAS/UVFIT at fixed spatial position and extension" (Total recovered fluxes)
- **MPFIT** : Gaussian line fitting  
  > "using the $\chi^2$-minimization algorithm MPFIT" (2.1.2)
- **IRAF/STSDAS** : twosampt and bhkmethod censored statistics  
  > "the *twosampt* task in the IRAF/STSDAS package" (3.1)
- **PDR Toolbox** : PDR model grids  
  > "updated version released with the PHOTODISSOCIATION REGION TOOLBOX" (4.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| mean T_exc from [C I] ratio | 25.6 | ±1.0 | K | 4 | we find a mean temperature of $\langle T_{\rm exc} \rangle = 25.6 \pm 1.0$ K for the whole compilation |
| median T_exc | 25.1 | IQR 8.0 K | K | 4 | an interquartile range of $\Delta T_{\rm exc} =
8.0$ K centered on a median value of $T_{\rm exc} = 25.1$ K |
| mean L'[CI](2-1)/L'[CI](1-0), MS z~1 | 0.465 | ±0.057 | dimensionless | 3 | Main sequence $z\sim1$ / $0.465 \pm  0.057$ |
| mean L'[CI](2-1)/L'[CI](1-0), SMGs | 0.476 | ±0.057 | dimensionless | 3 | SMGs $z\sim2-4$        / $0.476 \pm  0.057$ |
| log L[CI](1-0)/L_IR, SMGs | -5.336 | ±0.060 | dimensionless | 3 | SMGs $z\sim2-4$        / $-5.336 \pm  0.060^\dagger$ |
| log L[CI](1-0)/L_IR, MS z~1 | -4.908 | ±0.044 | dimensionless | 3 | Main sequence $z\sim1$ / $-4.908 \pm  0.044^\dagger$ |
| T_exc-T_dust correlation (local, Kendall/Spearman/Pearson) | 0.47, 0.62, 0.63 | not stated | dimensionless | 4 | ($\rho=0.47$, $0.62$, and $0.63$ Kendall, Spearman, and Pearson’s correlation coefficients, respectively) |
| [C I](2-1) vs (1-0) PDR offset in n and G0 | ~0.5 and ~0.3 | not stated | dex | 5 | results in $\sim0.5$ and $\sim0.3$ dex larger $n$ and $G_0$ than when adopting |

## Qualitative findings

- [C I]/IR and [C I]/CO(7-6) ratios of local LIRGs and z~1 main sequence galaxies are similar and higher than in SMGs  
  > "in local LIRGs and main sequence galaxies at $z\sim1$ are consistent, but systematically and significantly higher than the values measured in SMGs at $z=2-4$" (5 Conclusions)
- Observed [C I] luminosities exceed Santa Cruz model predictions at fixed L_IR while CO(4-3) is reproduced  
  > "the observed \[C I\] luminosities appear brighter than the predictions of the fiducial model at fixed $L_{\rm IR}$" (4.3)

## Claim tuples

- H: Dense gas fractions and SFE differ between SMGs and normal galaxies | E: Compared [C I]/IR and [C I]/CO(7-6) ratios across samples with censored two-sample tests | R: SMGs have lower ratios, p<0.0001 for [C I](1-0)/IR vs MS | F: Higher dense gas fractions and SFEs in SMGs | **supported**
- H: [C I]-traced gas temperature varies across populations | E: [C I](2-1)/(1-0) ratio converted to T_exc | R: ratios consistent across samples; mean T_exc 25.6 K | F: similar T_exc and T_exc ≲ T_dust | **supported**
- H: Simple PDR models can describe ISM conditions | E: Fit [C I]/CO/IR ratios with Kaufman 1999 models | R: larger n and G0 in SMGs; different line combos give different n,G0 | F: useful relatively but limited by multiphase ISM | **partially**
- H: Santa Cruz SAM reproduces [C I] emission | E: Compare luminosities vs L_IR to fiducial model | R: observed [C I] systematically brighter | F: emission recipes for [C I] need revision | **refuted**

## Reasoning

- Why this data: Select 7 targets with secure [C I](1-0) detection, simultaneous observability of [C I](2-1) and CO(7-6), and well-constrained SED  
  > "We selected the targets based on a secure \[C I\]$(^3P_1\,-\,^{3}P_0)$ detection, the simultaneous observability of \[C I\]$(^3P_2\, -\, ^{3}P_1)$ and CO $(7-6)$" (2.1.2)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Only a handful of MS galaxies with [C I](2-1) and CO(7-6); literature inhomogeneity; PDR modeling only order-of-magnitude  
  > "We stress that only a handful of main sequence galaxies with \[C I\]$(^3P_2\, -\, ^{3}P_1)$ and CO $(7-6)$ measurements are currently available" (3.1)
- Caveat (inferred, ours): Heterogeneous literature compilation (single dish vs interferometry, lensing) may bias ratio comparisons
- Caveat (inferred, ours): T_dust depends on SED parametrization; optically thin assumption questionable for SMGs
- Caveat (inferred, ours): Kaplan-Meier means biased when lowest value is a limit
- Caveat (inferred, ours): No uncertainty propagation described for PDR fits to unresolved multi-phase ISM

## Reproducibility

- Data public (paper): Compilation released in FITS; ALMA data from listed projects acknowledged  
  > "The whole data compilation we assembled for this work is made publicly available in an electronic format in the online version" (1 Introduction)
- Products in archive: _not stated_
- Missing: CASA version, imaging parameters
- Missing: per-source channel ranges
- Missing: literature photometry used for SED refits
- Missing: Cortzen et al. submitted data
- Data volume (inferred): ~tens of GB for the 7 Band 7 datasets plus V18 Band 6 data
- Score (inferred): 3/5, ALMA data public and key results tabulated, but reduction/imaging details are inherited from earlier papers and much of the analysis uses a literature compilation.
- Rediscovery candidate: no, Main results depend on a large literature compilation and inherited reduction recipes with missing imaging details.

## Links

- Method: (cite: valentino_2018) (Reduction procedure and previous sample)
- Method: (cite: daddi_2015) (Reduction and flux extraction procedure)
- Method: (cite: magdis_2012) (SED fitting prescriptions)
- Method: (cite: kaufman_1999) (PDR models)
- Companion: (cite: popping_2019) (Santa Cruz SAM sub-mm line modeling compared here)
- Companion: (cite: bourne_2019) (Main sequence sample included)
- Related: COSMOS
- Related: Herschel PEP
- Related: SCUBA2 Cosmology Legacy Survey

## Checks

```json
{
 "quotes": 68,
 "quotes_ok": 68,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2015.1.00228.S",
  "2015.1.01379.S",
  "2016.1.01184.S",
  "2017.1.00373.S",
  "2017.A.00013.S"
 ],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 84,
  "stated": 49,
  "rate": 0.583
 },
 "evidence_ok": true
}
```
