# VALES - III. The calibration between the dust continuum and interstellar gas content of star-forming galaxies

`2017MNRAS.468L.103H` | Monthly Notices of the Royal Astronomical Society 2017 | first author: Hughes, T. M. | arXiv: 1702.07350 | DOI: 10.1093/mnrasl/slx033

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies
- Question: What is the calibration between the 850 um dust continuum luminosity and the molecular/ISM gas mass for 67 main-sequence star-forming galaxies at 0.02<z<0.35, and does it agree with Scoville et al. 2016?  
  > "We present the calibration between the dust continuum luminosity and interstellar gas content obtained from the Valparaíso ALMA Line Emission Survey (VALES) sample of 67 main-sequence star-forming galaxies at $0.02<z<0.35$." (abstract)
- Target **VALES sample of 67 H-ATLAS/GAMA galaxies**: coordinates _not stated_; z/distance 0.02<z<0.35 (median 0.05)  
  > "a redshift between 0.02 $<z<$ 0.35 (median of 0.05), beyond which the CO(1–0) line is redshifted out of ALMA Band 3." (2.1 Sample selection); distance from GAMA spectroscopic redshifts  
  > "a redshift between 0.02 $<z<$ 0.35 (median of 0.05), beyond which the CO(1–0) line is redshifted out of ALMA Band 3." (2.1 Sample selection)

## Data provenance

- ALMA projects: 2012.1.01080.S, 2013.1.00530.S
- bands: Band 3  
  > "We exploit our VALES observations targeting the CO(1–0)  line in Band 3 for 67 galaxies obtained during cycle-1 and -2." (2.2 ALMA CO(1–0) line observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=1-0 (not stated)
- Other facility **GAMA / H-ATLAS (Herschel)**: FUV to FIR/submm photometry used for MAGPHYS SED fitting  
  > "photometry in 21 bands extending from the far-ultraviolet to far-infrared from numerous facilities" (2.3 GAMA multiwavelength photometry)
- External data: Scoville et al. 2016 sample of 70 galaxies used for the combined fit and L850/MH2 comparison  
  > "we consider the calibrations we obtain from combining the 70 galaxies of (cite: scoville2016) with the 43 CO-detected star-forming galaxies in our VALES sample." (3.3 The calibration) [from (cite: scoville2016)]
- External data: HI mass from the HI–colour scaling relation (Eqn. 4)  
  > "we use the Hi–colour scaling relation given by Eqn. 4 of (cite: zhang2009)" (3.2 Measurement of the interstellar gas content) [from (cite: zhang2009)]

## Processing

### Calibration

- pipeline or manual: common CASA pipeline developed from standard pipelines, applied homogeneously  
  > "using a common pipeline, developed from standard pipelines, for calibration, concatenation and imaging, with standard bandpass, flux and phase calibrators." (2.2 ALMA CO(1–0) line observations)
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
- primary beam correction: cleaned, primary-beam-corrected cubes  
  > "by collapsing the cleaned, primary-beam-corrected data cubes between $\nu_{\mathrm{obs}}-\nu_{\mathrm{FWHM}}$ and $\nu_{\mathrm{obs}}+\nu_{\mathrm{FWHM}}$" (2.2 ALMA CO(1–0) line observations)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA observations, data reduction and characterisation  
  > "(cite: villanuevaprep) present the observations, data reduction and a detailed characterisation for the complete sample." (2.2 ALMA CO(1–0) line observations) [from (cite: villanuevaprep)]
- MAGPHYS modelling of GAMA SEDs  
  > "we refer the reader to (cite: driverprep) for details of the complete analysis of the MAGPHYS modelling of all the GAMA SEDs" (3.1 Estimating the dust continuum luminosity) [from (cite: driverprep)]
- K-correction following Dunne et al. 2011 exact methodology  
  > "$K$ is the $K$-correction given by Eqn. 2 in (cite: dunne2011), following their exact methodology" (3.1 Estimating the dust continuum luminosity) [from (cite: dunne2011)]

### Not stated but needed to reproduce (our reading)

- CASA version and imaging parameters (weighting, cell size, deconvolver, masks)
- Flux calibrators and flux scale uncertainty
- Fitting method for the linear relations (regression type, error treatment)
- Galaxy-by-galaxy CO fluxes and the list of merger exclusions
- MAGPHYS priors/library version and the GAMA SED outputs
- Gaussian fitting details of collapsed cubes

## Analysis recipe

1. **CO(1-0) flux measurement**: Collapse cleaned primary-beam-corrected cubes over ±250 km/s FWHM about line centre and fit a Gaussian; upper limits 5x rms  
  > "We estimate upper limits as 5$\times$ the measured RMS from the collapsed cubes set at 100 km s$^{-1}$ spectral resolution and adopting $\nu_{\mathrm{FWHM}}$ = 250 km s$^{-1}$." (2.2 ALMA CO(1–0) line observations)
   - software: CASA
   - fitting: Gaussian fit  
  > "collapsing the cleaned, primary-beam-corrected data cubes between $\nu_{\mathrm{obs}}-\nu_{\mathrm{FWHM}}$ and $\nu_{\mathrm{obs}}+\nu_{\mathrm{FWHM}}$, and fitting these cubes with a Gaussian" (ALMA CO(1–0) line observations)
   - validation: _not stated_
2. **Estimate L850 from SED**: MAGPHYS best-fit SED median flux 800-900 um converted to rest-frame luminosity with K-correction; uncertainty from std of MAGPHYS and two modified blackbody fits  
  > "we calculate the median model flux between 800 and 900 $\mu$m, $S_{\nu_{850}}$, and convert this flux – that ranges from 1 to 15 mJy – into a monochromatic rest-frame luminosity" (3.1 Estimating the dust continuum luminosity)
   - software: MAGPHYS
   - assumption: Modified blackbody with beta free or fixed at 1.8; LCDM H0=70, OmegaM=0.27  
  > "either keeping the spectral index $\beta$ as a free parameter or fixing the value at 1.8" (3.1 Estimating the dust continuum luminosity)
   - fitting: Bayesian SED fitting (MAGPHYS)  
  > "modelled with the Bayesian SED fitting code, MAGPHYS" (Estimating the dust continuum luminosity)
   - validation: Modified blackbody fits give consistent fluxes  
  > "In both cases, our best-fit model fluxes are consistent and produce results that support the conclusions reached with the MAGPHYS SED fitting results." (3.1 Estimating the dust continuum luminosity)
3. **Derive gas masses**: L'CO from Solomon et al. formula; MH2 via alpha_CO; MHI from Zhang et al. colour relation; MISM=MHI+MH2  
  > "We then calculate the ISM gas mass as $M_{\rm ISM} = M_{\mathrm{H {\textsc{i}}}} + M_{\rm H_{2}}$ using standard error propagation." (3.2 Measurement of the interstellar gas content)
   - assumption: alpha_CO = 6.5 (primary), 4.6 Galactic alternative; mergers excluded  
  > "we primarily adopt $\alpha_{\rm CO}$ = 6.5 (K km s$^{-1}$ pc$^{2}$)$^{-1}$ for the bulge- and disk-dominated galaxies with normal star formation." (3.2 Measurement of the interstellar gas content)
   - fitting: _not stated_
   - validation: _not stated_
4. **Calibration relations**: Mean ratios and linear fits in log space of MH2 and MISM vs L850, for VALES and combined with Scoville+2016  
  > "a linear fit (in logarithmic space) may be more appropriate for the galaxies." (3.3 The calibration)
   - fitting: _not stated_
   - validation: Compared with Scoville et al. 2016 mean values  
  > "also in excellent agreement with the mean values found by (cite: scoville2016) and with near-matching scatter." (The $L_{\nu_{850}}$/$M_{\mathrm{ISM}}$ calibration)

## Software

- **CASA** : reduction, concatenation and imaging of ALMA data  
  > "All observations were reduced homogeneously within the *Common Astronomy Software Applications*[^1] (CASA; (cite: mcmullin2007))" (2.2 ALMA CO(1–0) line observations)
- **MAGPHYS** : SED fitting to estimate L850  
  > "modelled with the Bayesian SED fitting code, MAGPHYS (cite: dacunha2008)" (3.1 Estimating the dust continuum luminosity)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| L850/MH2 (alpha_CO=6.5) | 6.4e19 | 1.4e19 | erg s^-1 Hz^-1 Msun^-1 | 4 | the average ratio of $L_{\nu_{850}}$/$M_{\mathrm{H}_{2}}$ $=$ (6.4$\pm$1.4)$\times$10$^{19}$ erg s$^{-1}$ Hz$^{-1}$ M$_{\odot}^{-1}$ |
| VALES fit slope and intercept, log MH2 vs log L850 | 0.92, -17.31 | 0.02, 0.59 | dimensionless | 4 | \log_{10} {M}_{\mathrm{H}_{2}}& =\,  (0.92\pm0.02) \log_{10} L_{\nu_{850}}-(17.31\pm0.59) |
| VALES fit log MISM vs log L850 | 0.86, -15.38 | 0.02, 0.55 | dimensionless | 4 | \log_{10} {M}_{\mathrm{ISM}}& =\,  (0.86\pm0.02) \log_{10} L_{\nu_{850}}-(15.38\pm0.55) |
| Combined sample (113) fit log MH2 | 0.93, -17.74 | 0.01, 0.05 | dimensionless | 4 | (0.93\pm0.01) \log_{10} L_{\nu_{850}}-(17.74\pm0.05) |
| mean L'CO/L850 | 2.91e-21 | 0.66e-21 | dimensionless | 4 | (2.91$\pm$0.66)$\times$10$^{-21}$ in units of the luminosity ratio dimensions |

## Qualitative findings

- The average ratio agrees with Scoville et al. 2016; a slight trend with luminosity favours a linear log fit.  
  > "there is a very minor trend that galaxies with $L_{\nu_{850}}>10^{30}$ erg s$^{-1}$ Hz$^{-1}$ tend to lie on or above the average ratio" (3.3 The calibration)

## Claim tuples

- H: Does the dust-continuum to gas calibration of Scoville et al. hold for VALES main-sequence galaxies? | E: Compare L850/MH2 from MAGPHYS L850 and ALMA CO(1-0) with literature | R: L850/MH2 = (6.4±1.4)e19 | F: Average ratio in excellent agreement with literature | **supported**
- H: Is a constant ratio adequate across luminosity? | E: Linear fits in log space | R: slope 0.92±0.02 | F: A linear fit is recommended over constant ratio | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Dust continuum is faster than line observations for ISM mass at high z  
  > "being much faster ($\sim$ 20$\times$) at estimating the ISM mass than molecular line observations" (1 Introduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Largest uncertainty is alpha_CO; few resolved galaxies  
  > "we stress that the largest uncertainty in this work remains in the $\alpha_{\rm CO}$ factor." (4 Discussion)
- Caveat (inferred, ours): L850 is extrapolated from SED fits, not measured
- Caveat (inferred, ours): Narrow metallicity range limits applicability
- Caveat (inferred, ours): Fit errors exclude alpha_CO uncertainty

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Per-galaxy CO fluxes (in Villanueva et al. in prep)
- Missing: MAGPHYS outputs from Driver et al. in prep
- Data volume (inferred): ~50-200 GB raw for 67 Band 3 datasets
- Score (inferred): 3/5, Analysis is simple but depends on companion papers in prep for fluxes and SED fits.
- Rediscovery candidate: no, Relies on unpublished companion products; data reduction details not given.

## Links

- Method: (cite: dacunha2008) (MAGPHYS SED fitting)
- Method: (cite: dunne2011) (K-correction)
- Companion: (cite: villanuevaprep) (VALES observations and reduction)
- Companion: (cite: scoville2016) (Comparison calibration)
- Related: VALES
- Related: H-ATLAS
- Related: GAMA

## Checks

```json
{
 "quotes": 38,
 "quotes_ok": 38,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 67,
  "stated": 27,
  "rate": 0.403
 },
 "evidence_ok": true
}
```
