# On the Kennicutt-Schmidt scaling law of submillimetre galaxies

`2017A&A...602L...9M` | Astronomy and Astrophysics 2017 | first author: Miettinen, O. | arXiv: 1706.00589 | DOI: 10.1051/0004-6361/201731157

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What is the Kennicutt-Schmidt relation between SFR and gas surface density for a homogeneous sample of ALMA-detected SMGs, using 870 um dust-emitting sizes?  
  > "In this Letter, we report our results regarding the K-S law of SMGs, which were detected at 870 $\mu$m with the Atacama Large Millimetre/submillimetre Array (ALMA)." (Introduction)
- Target **AzTEC/C1-C27 SMGs in COSMOS**: coordinates _not stated_; z/distance z=1.1 to 5.3 (32 SMGs with SED and size)  
  > "The target SMGs, called AzTEC/C1–C27, were originally uncovered by the AzTEC $\lambda_{\rm obs}=1.1$ mm blank-field continuum survey of the inner 0.72 deg$^2$ of the COSMOS field" (2 Source sample and ALMA observations); "(40.6% are spectroscopically confirmed, while the remaining redshifts are photometric; (cite: brisbin2017))" (3 Data analysis); distance from spectroscopic and photometric redshifts from Brisbin et al. 2017  
  > "The target SMGs, called AzTEC/C1–C27, were originally uncovered by the AzTEC $\lambda_{\rm obs}=1.1$ mm blank-field continuum survey of the inner 0.72 deg$^2$ of the COSMOS field" (2 Source sample and ALMA observations); "(40.6% are spectroscopically confirmed, while the remaining redshifts are photometric; (cite: brisbin2017))" (3 Data analysis)

## Data provenance

- ALMA projects: 2016.1.00478.S
- bands: Band 7 (870 um), Cycle 4  
  > "in Cycle 4 using Band 7 continuum observations at $\lambda_{\rm obs}=870$ $\mu$m" (2 Source sample and ALMA observations)
- frequencies and spectral setup: 4 spectral windows at 336.5, 338.5, 348.5, 350.5 GHz, each 1.875 GHz in 128 channels  
  > "four spectral windows centred at 336.5 GHz and 338.5 GHz in the lower sideband, and at 348.5 GHz and 350.5 GHz in the upper sideband" (2 Source sample and ALMA observations)
- continuum bandwidth: 7.5 GHz  
  > "the total bandwidth available for continuum observations was 7.5 GHz." (2 Source sample and ALMA observations)
- arrays: 12 m array, 41 antennas  
  > "The observations were made using the 12 m array with 41 antennas" (2 Source sample and ALMA observations)
- configurations: _not stated_
- baselines: 18.6 m to 1.1 km  
  > "the baselines ranged from 18.6 m (21.3 k$\lambda$) to 1.1 km (1 260 k$\lambda$)" (2 Source sample and ALMA observations)
- angular resolution: median beam 0.192'' x 0.176''  
  > "typical (median) synthesised beam of $0.192\ensuremath{''} \times 0.176\ensuremath{''}$" (2 Source sample and ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: 1 sigma rms 0.155 mJy/beam (typical)  
  > "typical $1\sigma$ rms noise of the final images is 0.155 mJy beam$^{-1}$" (2 Source sample and ALMA observations)
- time on source: about 1.3 min per pointing, 34 pointings  
  > "with a total on-source integration time of about 1.3 min per pointing" (2 Source sample and ALMA observations)
- observing dates: 28 October 2016  
  > "The observations were carried out on 28 October 2016." (2 Source sample and ALMA observations)
- pi or archival as stated: PI: O. Miettinen  
  > "under project `2016.1.00478.S` (PI: O. Miettinen)" (2 Source sample and ALMA observations)
- Other facility **AzTEC (1.1 mm)**: Original single-dish source selection  
  > "originally uncovered by the AzTEC $\lambda_{\rm obs}=1.1$ mm blank-field continuum survey" (2 Source sample and ALMA observations)
- Other facility **ALMA Cycle 2 1.3 mm survey**: 1.3 mm source positions and flux densities (used for gas masses)  
  > "observed as part of our ALMA follow-up survey in Cycle 2 at $\lambda_{\rm obs}=1.3$ mm" (2 Source sample and ALMA observations)
- External data: SFR and gas mass from MAGPHYS SED fitting  
  > "Both the SFR and gas mass ($M_{\rm gas}$) values were adopted from Miettinen et al. (2017b, hereafter M17b)" (3 Data analysis) [from Miettinen et al. 2017b (M17b)]
- External data: Redshifts (spectroscopic and photometric)  
  > "(40.6% are spectroscopically confirmed, while the remaining redshifts are photometric; (cite: brisbin2017))" (3 Data analysis) [from (cite: brisbin2017)]
- External data: 3 GHz radio sizes  
  > "we also derived the $\Sigma_{\rm gas}$ values using the radio sizes from M17a" (3 Data analysis) [from (cite: miettinen2017a)]

## Processing

### Calibration

- pipeline or manual: standard ALMA pipeline  
  > "The visibility data were edited, calibrated, and imaged using the standard ALMA pipeline" (2 Source sample and ALMA observations)
- casa version: CASA 4.7.0  
  > "(CASA; (cite: mcmullin2007)) version 4.7.0" (2 Source sample and ALMA observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "The final images were created using the `tclean` task" (2 Source sample and ALMA observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "adopting Briggs weighting with a `robust` parameter of 0.5" (2 Source sample and ALMA observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied before noise estimate  
  > "estimated from emission-free regions after correction for the primary beam (PB) response" (2 Source sample and ALMA observations)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.192'' x 0.176'' median  
  > "typical (median) synthesised beam of $0.192\ensuremath{''} \times 0.176\ensuremath{''}$" (2 Source sample and ALMA observations)
- final rms: 0.155 mJy/beam  
  > "typical $1\sigma$ rms noise of the final images is 0.155 mJy beam$^{-1}$" (2 Source sample and ALMA observations)

### Inherited from earlier work

- SFR and gas mass derivation details (MAGPHYS, Scoville calibration)  
  > "These dust-based $M_{\rm gas}$ values refer to the molecular (H$_2$) gas mass (see M17b for further details)." (3 Data analysis) [from Miettinen et al. (2017b) (M17b)]
- MS/starburst split defined as offset >3 from MS mid-line  
  > "defined to be offset from the MS mid-line by a factor of $>3$; see M17b" (3 Data analysis) [from Miettinen et al. (2017b)]
- Kaplan-Meier treatment of unresolved 3 GHz sources  
  > "using a right-censored Kaplan-Meier (K-M) survival analysis (see M17a for details)" (Appendix B) [from (cite: miettinen2017a)]

### Not stated but needed to reproduce (our reading)

- Line-by-line SFR and Mgas values per source (in M17b, not given here)
- Details of ALMA Cycle 2 1.3 mm flux densities (Aravena et al. in prep.)
- Binning scheme (number of sources per bin, bin edges)
- Exact MAGPHYS settings and Scoville calibration parameters
- Whether 1.3 mm positions were used as JMFIT starting points

## Analysis recipe

1. **Image 870 um continuum**: Standard ALMA pipeline calibration and tclean imaging, Briggs weighting  
  > "The final images were created using the `tclean` task by adopting Briggs weighting with a `robust` parameter of 0.5." (2 Source sample and ALMA observations)
   - software: CASA
   - parameter: robust = 0.5  
  > "Briggs weighting with a `robust` parameter of 0.5" (2 Source sample and ALMA observations)
   - fitting: _not stated_
   - validation: Non-detections tested by convolving with Gaussian kernels  
  > "we convolved the images with a Gaussian smoothing kernel of different radii" (2 Source sample and ALMA observations)
2. **Measure source sizes**: 2D elliptical Gaussian fits to image plane, deconvolved major axis FWHM as diameter  
  > "the beam-deconvolved (intrinsic) sizes were derived through two-dimensional elliptical Gaussian fits to the image plane data using the AIPS task `JMFIT`." (3 Data analysis)
   - software: AIPS JMFIT, CASA imfit
   - parameter: fit restricted to pixels >= 2.5 sigma  
  > "the fit was restricted to the pixel values of $\geq 2.5\sigma$" (3 Data analysis)
   - fitting: Gaussian fit in rectangular box  
  > "The Gaussian fitting was performed inside a rectangular box enclosing the source" (3 Data analysis)
   - validation: Compared with CASA imfit; mean ratio 1.06, median 1.02  
  > "the mean (median) ratio between the two being $\langle {\rm Size(AIPS)}/{\rm Size(CASA)}\rangle=1.06$ (1.02)" (3 Data analysis)
3. **Compute surface densities**: Sigma = X/(2 pi R^2), R = 0.5 FWHM_maj, with SFR and Mgas from M17b  
  > "the surface densities were calculated as $\Sigma_{\rm SFR}={\rm SFR}/(2\pi R^2)$ and $\Sigma_{\rm gas}=M_{\rm gas}/(2\pi R^2)$" (3 Data analysis)
   - software: MAGPHYS
   - assumption: Galactic alpha_CO = 6.5 Msun (K km/s pc^2)^-1 inherent in Scoville et al. 2016 calibration  
  > "calibrated using a comparable, single Galactic $\alpha_{\rm CO}$ of 6.5 M$_{\ensuremath{\odot}}$ (K km s$^{-1}$ pc$^2$)$^{-1}$" (3 Data analysis)
   - fitting: _not stated_
   - validation: Two sources with CO-based Mgas agree within factor of two  
  > "they agree within a factor of two with our dust-based values" (3 Data analysis)
4. **Fit K-S relation and SFE**: Linear least squares fits to binned data (MS and starburst), also with slope fixed to unity for SFE  
  > "The linear least squares fits ($\log \Sigma_{\rm SFR}= a\times \log \Sigma_{\rm gas}+b$) through the binned data points" (3 Data analysis)
   - fitting: Least squares, errors derived from Sigma_SFR uncertainties  
  > "they were derived from the $\Sigma_{\rm SFR}$ uncertainties" (3 Data analysis)
   - validation: Alternative alpha_CO and 3 GHz sizes tested  
  > "we show two alternative K-S diagrams" (3 Data analysis)

## Software

- **CASA** 4.7.0: Pipeline calibration, tclean imaging, imfit  
  > "The visibility data were edited, calibrated, and imaged using the standard ALMA pipeline of the Common Astronomy Software Applications" (2 Source sample and ALMA observations)
- **AIPS (JMFIT)** : Gaussian size fitting  
  > "we used the NRAO Astronomical Image Processing System (AIPS) software package" (3 Data analysis)
- **MAGPHYS** latest version: SED fits for SFR and Mgas (in M17b)  
  > "who used the latest version of `MAGPHYS` ((cite: dacunha2015)) to fit the panchromatic spectral energy distributions" (3 Data analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Median deconvolved FWHM_maj | 0.31 | +0.15/-0.10 | arcsec | 2 | The median value of ${\rm FWHM_{\rm maj}}$ is $0.31\ensuremath{''}^{+0.15}_{-0.10}$ ($2.4^{+1.1}_{-0.8}$ kpc) |
| K-S slope, MS SMGs | 0.81 | 0.01 | dimensionless | 4 | $(a=0.81\pm0.01,\,b=-1.89\pm0.05)$ for the MS SMGs |
| K-S slope, starburst SMGs | 0.84 | 0.39 | dimensionless | 4 | $(a=0.84\pm0.39,\,b=-1.81\pm1.84)$ for the starburst SMGs |
| SFE, MS SMGs | 21 | +2/-1 | % per 100 Myr | 4 | constant global SFE of $21^{+2}_{-1}\%$ per 100 Myr |
| SFE, starburst SMGs | 27 | +6/-6 | % per 100 Myr | 4 | that for our starburst SMGs is $27^{+6}_{-6}\%$ per 100 Myr |
| Gas depletion time, MS / starburst | 480 / 370 | +20/-45 / +106/-67 | Myr | 4 | $\tau_{\rm dep}={\rm SFE}^{-1}\simeq 480^{+20}_{-45}$ Myr and $\simeq370^{+106}_{-67}$ Myr |

## Qualitative findings

- SMG K-S relations are flatter with higher zero points than K98/D10; gas surface densities exceed Eddington-limit threshold  
  > "our SMG $\Sigma_{\rm SFR}-\Sigma_{\rm gas}$ relations have flatter slopes and higher zero points than the K98 relation" (3 Data analysis)

## Claim tuples

- H: Do SMGs follow the K98/D10 K-S slope of ~1.4? | E: Fit binned Sigma_SFR vs Sigma_gas using ALMA 870 um sizes | R: Slopes 0.81±0.01 (MS) and 0.84±0.39 (starburst) | F: Sub-linear/quasi-linear, consistent with Eddington-limited disk expectation of unity | **supported**
- H: Does the choice of size scale affect the K-S law? | E: Used 3 GHz radio sizes instead of dust sizes | R: Slopes 0.40 and -0.16 | F: Source size is a major bottleneck | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: ULIRG alpha_CO=0.8 and 3 GHz radio sizes considered as alternatives  
  > "a lower value of $\alpha_{\rm CO}=0.8$ M$_{\ensuremath{\odot}}$ (K km s$^{-1}$ pc$^2$)$^{-1}$" (3 Data analysis)
- How they decided it was enough: _not stated_
- Limitation (authors): Dust-based Mgas rests on uniform Galactic alpha_CO; dust sizes may be more compact than gas  
  > "based on the critical assumption of a uniform Galactic CO-to-H$_2$ conversion factor" (Summary and conclusions)
- Caveat (inferred, ours): Binned fits with 4 points per group give fragile uncertainties
- Caveat (inferred, ours): Photometric redshifts large uncertainty
- Caveat (inferred, ours): Dust size used for gas surface density is not gas extent

## Reproducibility

- Data public (paper): ALMA data cited by project code; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00478.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: SFR and Mgas tables from M17b (submitted)
- Missing: Binning details
- Missing: Cycle 2 1.3 mm fluxes
- Data volume (inferred): ~10-30 GB (34 short pointings, 4 spws)
- Score (inferred): 3/5, Imaging and size fitting are clear, but SFR/Mgas inputs come from unpublished companion paper and binning is unspecified.
- Rediscovery candidate: no, Key inputs (SFR, Mgas) come from a companion paper not given here.

## Links

- Method: Scoville et al. 2016 (Dust-continuum gas mass calibration)
- Method: da Cunha et al. 2015 (MAGPHYS SED fitting)
- Companion: Miettinen et al. 2017a (3 GHz radio sizes)
- Companion: Miettinen et al. 2017b (SFR and gas masses)
- Companion: Brisbin et al. 2017 (Redshifts and counterparts)
- Related: AzTEC COSMOS survey
- Related: ALMA Cycle 2 1.3 mm follow-up (Aravena et al., in prep.)

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
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 48,
  "rate": 0.667
 },
 "evidence_ok": true
}
```
