# The relationship between dust and [C I] at z = 1 and beyond

`2019MNRAS.482.3135B` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Bourne, N. | arXiv: 1810.01640 | DOI: 10.1093/mnras/sty2773

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Is [CI] 492 GHz emission correlated with dust continuum in typical z=1 star-forming galaxies, and what does this imply for gas mass calibrations (dust vs [CI])?  
  > "In this paper we study the [Ci]/dust correlation to determine whether the two tracers are sensitive to the same gas phase" (1 Introduction)
- Target **10 SCUBA-2 450um selected galaxies at 0.84<z<1.29 in UDS-CANDELS and COSMOS-CANDELS**: coordinates Table of sample, e.g. ID 1 02:17:17.50 -5:10:03.39; ID 2 10:00:13.58 +2:22:25.47  
  > "We selected 10 galaxies with grism redshifts in the range $0.84<z<1.29$, so that [Ci] falls within ALMA Band 6" (2.1 Selection); z/distance z=0.84-1.29 (grism redshifts)  
  > "We selected 10 galaxies with grism redshifts in the range $0.84<z<1.29$, so that [Ci] falls within ALMA Band 6" (2.1 Selection); distance from 3DHST grism redshifts (Momcheva2015)  
  > "We selected 10 galaxies with grism redshifts in the range $0.84<z<1.29$, so that [Ci] falls within ALMA Band 6" (2.1 Selection)

## Data provenance

- ALMA projects: 2016.1.01184.S, 2017.A.00013.S
- bands: Band 6  
  > "so that [Ci] falls within ALMA Band 6" (2.1 Selection)
- frequencies and spectral setup: TDM, 2 GHz per baseband; one spw on [CI] 492 GHz rest, second on CO(4-3) 461 GHz  
  > "The spectral setup was designed with one spectral window centred on the [Ci] line at rest-frame 492 GHz, and a second spectral window was centred on the CO(4–3) line at 461 GHz." (3.1 Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C40-3 (15-460m), C40-4 (15-704m) in Cycle 4; C43-6 (15-2400m) in Cycle 5  
  > "We used configurations C40-3 (15-460m baselines) and C40-4 (15-704m) in Cycle 4, and C43-6 (15-2400m) in Cycle 5." (3.1 Observations and data reduction)
- baselines: _not stated_
- angular resolution: ~0.8x0.6 arcsec natural; 1.1x1.1 tapered; 0.3x0.2 arcsec Cycle 5 (IDs 2, 9)  
  > "Most of the data were imaged with natural weighting of the visibilities, which resulted in beam sizes of approximately $0.8\times0.6$ arcsec FWHM." (3.1 Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: Designed for [CI] SNR>5 in 40 km/s channels over 250 km/s line width  
  > "calculated to reach a sensitivity level sufficient to detect the [Ci] line at SNR $>5$ in 40km s$^{-1}$ channels across an assumed line width of 250km s$^{-1}$" (3.1 Observations and data reduction)
- time on source: _not stated_
- observing dates: 2016 Nov 28 - Dec 14 (Cycle 4); 2017 Dec 24 (Cycle 5)  
  > "Observations were conducted between 2016 November 28 and December 14 in Cycle 4, and 2017 December 24 in Cycle 5." (3.1 Observations and data reduction)
- pi or archival as stated: _not stated_
- Line: [CI] 3P1-3P0 (492 GHz)
- Line: CO 4-3 (461 GHz)
- Other facility **JCMT/SCUBA-2 (S2CLS)**: 450 and 850 um photometry  
  > "JCMT/SCUBA-2 450 & 850 $\mu$m from S2CLS" (2.3 Far-infrared spectral energy distributions)
- Other facility **Herschel PACS/SPIRE**: 100, 160, 250 um photometry  
  > "*Herschel*/PACS 100 & 160 $\mu$m from PEP (cite: Lutz2011); *Herschel*/SPIRE 250 $\mu$m from HerMES (cite: Oliver2012)" (2.3 Far-infrared spectral energy distributions)
- Other facility **HST/3DHST/CANDELS**: imaging, grism redshifts, multiwavelength catalogue  
  > "grism redshifts for a large subset of galaxies from 3DHST (cite: Momcheva2015)" (2.1 Selection)
- External data: 3DHST catalogue photometry, stellar masses, L_UV, 24um fluxes  
  > "The sample is based upon the 3DHST galaxy catalogue described by (cite: Skelton2014)." (2.2 Multi-wavelength data and derived properties) [from (cite: Skelton2014)]
- External data: Deblended SCUBA-2/Herschel photometry catalogue used for selection  
  > "We selected our sample from the catalogue of prior-based submm photometry for stellar-mass selected galaxies that we used for the analysis in (cite: Bourne2017)." (2.1 Selection) [from (cite: Bourne2017)]
- External data: Literature SMG and lensed [CI] and continuum samples for Fig. 12  
  > "These are the $z\sim2.5$ SMG sample from (cite: Alaghband-Zadeh2013), which also includes SMGs from (cite: Cox2011), (cite: Danielson2011) and (cite: Walter2011b)" (5.2 Comparing independent gas mass estimates) [from (cite: Alaghband-Zadeh2013; Bothwell2017; Weiss2013)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline in CASA 4.7.2, using packaged calibration scripts; then own imaging scripts  
  > "All data were reduced using the ALMA pipeline in CASA version 4.7.2." (3.1 Observations and data reduction)
- casa version: CASA 4.7.2  
  > "All data were reduced using the ALMA pipeline in CASA version 4.7.2." (3.1 Observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: TCLEAN for continuum and lines  
  > "We imaged the continuum-subtracted spectral lines using TCLEAN, again masking any line emission for cleaning." (3.1 Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: Natural weighting for most; u-v taper to 1.1x1.1 arcsec for IDs 1, 5, 8, 9  
  > "In cases where this led to higher flux measurements, we used the tapered images, which have beam sizes of $1.1\times1.1$ arcsec FWHM (IDs 1, 5, 8, 9)." (3.1 Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Emission from target or other galaxies masked during cleaning  
  > "During cleaning, we masked any emission associated with either the target or other galaxies in the field." (3.1 Observations and data reduction)
- multiscale scales: _not stated_
- continuum subtraction: UVCONTSUB using line-free channels  
  > "then used the task UVCONTSUB to fit and subtract the continuum using channels containing no line emission" (3.1 Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: ID 9: Cycle 4 and 5 continuum images made separately, combined with inverse-variance weighted mean  
  > "then combined the two continuum images with an inverse-variance weighted mean" (3.1 Observations and data reduction)
- smoothing: _not stated_
- final beam: 0.8x0.6 arcsec natural; 1.1x1.1 tapered; 0.3x0.2 Cycle 5  
  > "The natural-weighted images have beam sizes of $0.3\times0.2$ arcsec FWHM." (3.1 Observations and data reduction)
- final rms: _not stated_

### Inherited from earlier work

- FIR deblended photometry method with T-PHOT  
  > "The methodology used here is very similar to that described in (cite: Bourne2017), and we refer the reader to that publication for full details." (2.3 Far-infrared spectral energy distributions) [from (cite: Bourne2017)]
- SFR determination from UV+IR  
  > "We determine SFRs as in (cite: Bourne2017), from the sum of the SFR derived from the raw UV luminosity" (2.2 Multi-wavelength data and derived properties) [from (cite: Bourne2017)]
- Gas mass from continuum calibration  
  > "(cite: Scoville2016) provide the following calibration for molecular gas mass as a function of observed 850-$\mu$m flux density" (5.1 Gas mass calibrations) [from (cite: Scoville2016; Scoville2016err)]
- [CI] gas mass formula and Q10=0.35  
  > "We adopt a moderate value of $Q_{10}=0.35$, following (cite: Papadopoulos2012a)." (5.1 Gas mass calibrations) [from (cite: Papadopoulos2004; Papadopoulos2012a)]

### Not stated but needed to reproduce (our reading)

- tclean parameters: robust, cell size, image size, niter/threshold, channel width of cubes
- line-free channel ranges and continuum-subtraction polynomial order
- aperture definitions (ellipse positions/sizes) for each source
- SED fit priors and ODR error handling
- exact velocity integration ranges beyond table values
- pipeline-produced vs manual flagging details; flux calibrator and flux uncertainty

## Analysis recipe

1. **Calibrate and image ALMA data**: Pipeline calibration then own scripts: continuum via TCLEAN over line-free channels; line cubes via UVCONTSUB and TCLEAN; moment-0 maps  
  > "We created separate data cubes for the [Ci], CO(4–3) and continuum imaging." (3.1 Observations and data reduction)
   - software: CASA, TCLEAN, UVCONTSUB
   - parameter: Natural weighting; optional taper giving 1.1 arcsec beam  
  > "We also tried imaging with a *u-v* taper to down-weight the contributions from long baselines and increase sensitivity to extended flux." (3.1 Observations and data reduction)
   - fitting: _not stated_
   - validation: Iterated line masking, continuum subtraction and clean masks after inspecting moment maps and aperture spectra  
  > "The process was iterative since it was necessary to revise the line masking, continuum subtraction and cleaning masks after inspecting the moment maps and aperture spectra." (3.1 Observations and data reduction)
2. **Measure aperture line and continuum fluxes**: Integrate emission in matched apertures; uncertainties from randomising aperture position 150 times in the field; background subtraction judged unnecessary  
  > "To estimate uncertainties on aperture fluxes, we took the source aperture and randomised its position 150 times within the field of view" (3.2 Line and continuum measurements)
   - parameter: Sky level estimated in annulus of 2-4 times aperture semimajor axis  
  > "measuring the median pixel value (in Jy beam$^{-1}$) in an annulus enclosing radii 2 to 4 times the semimajor axis of the aperture ellipse" (3.2 Line and continuum measurements)
   - fitting: _not stated_
   - validation: Alternative apertures for ID 1 and velocity ranges for ID 2 compared  
  > "Source ID 1 has two alternative sets of apertures defined as discussed in Section" (4.1 The [CI]–continuum correlation)
3. **Fit FIR SEDs for L_IR, T_d, dust mass**: Modified blackbody plus power law (Casey 2012), beta=1.8, optically thick with lambda0; dust mass from 850um flux with kappa850  
  > "We modeled the SEDs with a modified blackbody function combined with a power law, as in (cite: Casey2012)." (2.3 Far-infrared spectral energy distributions)
   - software: emcee
   - parameter: 100 walkers, 500 steps, 100-step burn-in  
  > "with 100 walkers over 500 steps, with 100-step burnin" (2.3 Far-infrared spectral energy distributions)
   - assumption: beta=1.8; kappa_850=0.077 m^2/kg  
  > "where we assumed the widely-adopted value of $\kappa_{850}=0.077$ m$^2$ kg$^{-1}$ (cite: James2002)." (2.3 Far-infrared spectral energy distributions)
   - fitting: MCMC with emcee; posterior medians and 16/84 percentiles  
  > "The posterior median $\pm1\sigma$ estimates of the temperature ($T_d$), optically-thick limit ($\lambda_0$) and power-law index ($\alpha$) are given" (2.3 Far-infrared spectral energy distributions)
   - validation: Checked optically thin or free beta give similar L_IR  
  > "the constraints on $\ensuremath{L_\text{IR}}$ are almost identical if we substitute the model for an optically-thin SED or allow $\beta$ to vary" (2.3 Far-infrared spectral energy distributions)
4. **Quantify correlations**: Spearman rank with 100 Monte Carlo realisations for uncertainty; orthogonal distance regression for linear and power-law fits when p<0.01  
  > "For this purpose we use the orthogonal distance regression method implemented in SCIPY.ODR." (4 Results and discussion)
   - software: scipy.odr
   - fitting: Total least squares (ODR); linear y=a0 x and power-law y=a1 x^a2  
  > "we also attempt to fit the relationship using total-least-squares minimisation (which takes into account the large error bars in both $x$ and $y$ data). For this purpose we use the orthogonal distance regression method implemented in SCIPY.ODR." (4 Results and discussion)
   - validation: Residual variance reported  
  > "The quality of these fits is parameterised by the residual variance $\sigma^2_r$, quantifying deviations between the data and the best-fitting model." (4 Results and discussion)
5. **Derive gas masses and compare [CI] vs dust calibrations**: M_mol[CI] via Papadopoulos 2004 formula; M_mol,cont via Scoville 2016 850um calibration; compare, infer X_CI  
  > "We adopt an intermediate value of $3\times10^{-5}$." (5.1 Gas mass calibrations)
   - parameter: Q10=0.35, X_CI=3e-5, mu=1.36, A10=7.93e-8 s^-1  
  > "We adopt a moderate value of $Q_{10}=0.35$" (5.1 Gas mass calibrations)
   - assumption: [CI] optically thin; Scoville calibration assumes Td=25 K, beta=1.8, Galactic X_CO  
  > "assuming $T_d=25$ K and $\beta=1.8$ (cite: Scoville2016err)" (5.1 Gas mass calibrations)
   - fitting: _not stated_
   - validation: Compared with literature SMG and lensed samples  
  > "we also show two samples of high-redshift dusty star-forming galaxies from the literature." (5.2 Comparing independent gas mass estimates)

## Software

- **CASA** 4.7.2: ALMA pipeline calibration, tclean, uvcontsub  
  > "All data were reduced using the ALMA pipeline in CASA version 4.7.2." (3.1 Observations and data reduction)
- **emcee** : MCMC SED fitting  
  > "We used the PYTHON package EMCEE (cite: Foreman-Mackey2013) to conduct Monte Carlo Markov Chain (MCMC) sampling" (2.3 Far-infrared spectral energy distributions)
- **T-PHOT** : Deblended FIR/submm photometry  
  > "to measure deblended photometry with T-PHOT (cite: Merlin2015; Merlin2016)" (2.3 Far-infrared spectral energy distributions)
- **scipy.odr** : Orthogonal distance regression fits  
  > "For this purpose we use the orthogonal distance regression method implemented in SCIPY.ODR." (4 Results and discussion)
- **Le Phare** : Photometric redshift check for ID 2  
  > "our own photometric redshift fitting using Le Phare (cite: Ilbert2006)" (3.3.2 ID 2)
- **Astropy** : Analysis (acknowledged)  
  > "This research made use of ASTROPY, a community-developed core Python package for Astronomy (cite: Astropy2018)" (Acknowledgements)
- **APLpy** : Plotting  
  > "and APLPY, an open-source plotting package for Python (cite: Robitaille2012)" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Best-fit linear [CI]/continuum ratio a0 (excl. IDs 1,2) | 2.67 | 0.28 | Jy km/s per mJy | 4 | which yields $a_0=2.67\pm0.28$ Jy km s$^{-1}$ mJy$^{-1}$ |
| Spearman r_s [CI]-continuum (9 points) | 0.95 | 0.12 | dimensionless | 4 | 0.95 $\pm$ 0.12 / 0.000088 |
| Power-law index [CI]-continuum (all) | 0.746 | 0.096 | dimensionless | 4 | $a_1=1.90\pm0.22$ and $a_2=0.746\pm0.096$ |
| Spearman r_s CO(4-3)-continuum (7 points) | 0.68 | 0.23 | dimensionless | 4 | the Spearman rank coefficient and significance level respectively are 0.68, 0.094 |
| Average offset M[CI]/Mcont across samples | 0.56 (-0.25 dex) | scatter 0.21 dex | dimensionless | 5 | The average offset is $-0.25$ dex (i.e. $\langle M_\textrm{mol}^\textrm{[CI]}/M_\textrm{mol}^\textrm{cont} \rangle=0.56$) |
| Mean dust/gas ratio from [CI] gas masses | 70-130 | not stated | dimensionless | 5 | we measure the mean dust/gas ratio in our sample to be between 70 and 130 |
| Predicted X_CI | 1.9e-5 | 0.1e-5 | dimensionless | 5 | this implies $\ensuremath{X_\mathrm{CI}}=(1.9\pm0.1)\times10^{-5}$ |

## Qualitative findings

- [CI] and dust continuum are strongly correlated, more so than CO(4-3) and continuum, suggesting they trace the same gas phase  
  > "CO(4–3) emission traces a warmer, denser phase of the ISM, while [Ci] and dust continuum emission both appear to trace the same phase." (6 Conclusions)

## Claim tuples

- H: Dust continuum and [CI] trace the same molecular gas phase at z=1 | E: ALMA Band 6 [CI], CO(4-3), continuum aperture fluxes for 9 detected galaxies; Spearman and ODR fits | R: Spearman r_s=0.93-0.95 for [CI] vs continuum; CO(4-3) vs continuum r_s~0.6-0.7 | F: [CI] correlates strongly with dust, more than CO(4-3) | **supported**
- H: The [CI]-continuum correlation persists across luminosity and redshift | E: Added literature SMG and lensed samples | R: Common relation with 0.2 dex scatter up to z~4 | F: Same relation over all samples | **supported**
- H: [CI] and dust calibrations give consistent gas masses | E: Compared M_mol[CI] (X_CI=3e-5) with Scoville continuum masses | R: [CI] masses 1-4 times smaller | F: Offset probably due to unknown X_CI; X_CI~1.9e-5 would reconcile | **partially**

## Reasoning

- Why this data: 450um-selected galaxies on the main sequence at z~1 so that [CI] falls in Band 6 and dust SEDs are well measured  
  > "In order to identify star-forming galaxies at $z=1$ with good measurements of the dust spectral energy distribution (SED), we selected sources detected by SCUBA-2 at 450 $\mu$m." (2.1 Selection)
- Why this method: _not stated_
- Alternative: Optically thin vs thick SED or free beta gave similar L_IR; high [CI] optical depth rejected as explanation of offset  
  > "This is inconsistent with the fact that most of the sample have dust obscuration factors consistent with the average for their stellar mass" (5.2 Comparing independent gas mass estimates)
- How they decided it was enough: _not stated_
- Limitation (authors): Small sample and ambiguous total fluxes of IDs 1 and 2; modest dynamic range  
  > "although the sample is small and ambiguities in the total fluxes of IDs 1 and 2 add some complication to the interpretation" (4.3 Discussion of scatter and outliers)
- Caveat (inferred, ours): Only 9 detections; correlations sensitive to aperture choices for IDs 1 and 2
- Caveat (inferred, ours): Gas-mass comparison depends on assumed X_CI, Q10, Scoville alpha850, and fixed Td
- Caveat (inferred, ours): Literature continuum extrapolated with assumed Td=35 K

## Reproducibility

- Data public (paper): ALMA data identified by project codes; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.01184.S and ADS/JAO.ALMA#2017.A.00013.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Aperture definitions
- Missing: tclean parameters
- Missing: SED fit priors
- Missing: Photometry catalogue values from Bourne2017
- Data volume (inferred): ~100 GB raw for two programs
- Score (inferred): 3/5, Data and general recipe are given with a results table, but imaging parameters and apertures are unspecified.
- Rediscovery candidate: no, Imaging and aperture details are not specified enough, and SED inputs come from prior work.

## Links

- Method: (cite: Bourne2017) (FIR deblended photometry and SFR methods)
- Method: (cite: Scoville2016) (Dust continuum gas mass calibration)
- Method: (cite: Papadopoulos2004) ([CI] gas mass calibration)
- Related: S2CLS
- Related: 3DHST
- Related: CANDELS

## Checks

```json
{
 "quotes": 73,
 "quotes_ok": 73,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 84,
  "stated": 58,
  "rate": 0.69
 },
 "evidence_ok": true
}
```
