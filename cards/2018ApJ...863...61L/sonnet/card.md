# An ALMA Survey of Faint Disks in the Chamaeleon I Star-forming Region: Why Are Some Class II Disks so Faint?

`2018ApJ...863...61L` | The Astrophysical Journal 2018 | first author: Long, Feng | arXiv: 1806.04826 | DOI: 10.3847/1538-4357/aacce9

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: Why are some Class II disks in Chamaeleon I so faint at mm wavelengths, and does the stellar-disk mass scaling relation hold with deeper data?  
  > "The stellar-disk mass scaling relation reported in (cite: pascucci2016) is confirmed with these updated measurements." (abstract)
- Target **14 faintest Class II disks of the Hot sample in Chamaeleon I (e.g. CHXR71, CHXR30A, T54, CHXR20, ISO91, T51)**: coordinates 2MASS names listed in Table 2 (e.g. J11023265-7729129 for CHXR71)  
  > "located at an average distance of 190 pc" (1 Introduction); "The name and spectral type for each of these sources are listed in Table [2](#tab:continuum)." (Observations and data reduction); z/distance ~190 pc  
  > "located at an average distance of 190 pc" (1 Introduction); "The name and spectral type for each of these sources are listed in Table [2](#tab:continuum)." (Observations and data reduction); distance from Gaia DR2 parallaxes (cite: gaia2018)  
  > "located at an average distance of 190 pc" (1 Introduction); "The name and spectral type for each of these sources are listed in Table [2](#tab:continuum)." (Observations and data reduction)

## Data provenance

- ALMA projects: 2015.1.00333.S
- bands: Band 7 (887 um / 882 um)  
  > "The ALMA Band 7 observational setup in Cycle 3 was similar to that in Cycle 2" (Observations and data reduction)
- frequencies and spectral setup: Continuum basebands at 333.8, 335.7, 347.5 GHz; weighted mean 340 GHz; line window on 12CO J=3-2  
  > "The three continuum basebands were centered at 333.8, 335.7, and 347.5 GHz with an aggregated bandwidth of 5.9 GHz" (Observations and data reduction)
- continuum bandwidth: 5.9 GHz aggregated  
  > "The three continuum basebands were centered at 333.8, 335.7, and 347.5 GHz with an aggregated bandwidth of 5.9 GHz" (Observations and data reduction)
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15-331 m (Jan 25), 15-460 m (Mar 30)  
  > "| 2016 Mar 30 | 44      | 15-460         | 0.75   |" (Table 1)
- angular resolution: 1.1" x 0.7" typical beam  
  > "The typical continuum beam size is 1.$\ensuremath{''}$1$\times$0.$\ensuremath{''}$7, when all baselines are included." (Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: 1 sigma rms 0.2 mJy/beam  
  > "reaching a 1$\sigma$ rms of 0.2 mJy beam$^{-1}$" (Observations and data reduction)
- time on source: 3.6 min per source  
  > "two sets of observations were executed for a total integration time of 3.6 min" (Observations and data reduction)
- observing dates: 2016 Jan 25 and 2016 Mar 30  
  > "| 2016 Jan 25 | 42      | 15-331         | 1.13   |" (Table 1)
- pi or archival as stated: Cycle 3 program PI I. Pascucci  
  > "in our Cycle 3 program 2015.1.00333 (PI: I. Pascucci)" (Observations and data reduction)
- Line: 12CO J=3-2 (not stated)
- External data: Stellar masses  
  > "stellar masses are adopted from (cite: pascucci2016)" (Table 2) [from (cite: pascucci2016)]
- External data: Spectral types and accretion rates  
  > "Spectral types are adopted from (cite: manara2016; manara2017)" (Table 2) [from (cite: manara2016; manara2017)]
- External data: Stellar multiplicity and separations  
  > "References for stellar multiplicity are (cite: lafrenire2008) and (cite: daemgen2013)." (Table 2) [from (cite: lafrenire2008; daemgen2013)]
- External data: Cycle 2 887um fluxes  
  > "Column 6 and 7 are 887$\mu$m fluxes in (cite: pascucci2016) and this work." (Table 2) [from (cite: pascucci2016)]
- Simulation/model as data: RADMC-3D SED model of CHXR30A with a circumsecondary disk  
  > "we use the radiative transfer code RADMC-3D (cite: dullemond2012) to model the SED of the binary system CHXR30A." (6.3 Disks around the secondary star)

## Processing

### Calibration

- pipeline or manual: NRAO-provided scripts  
  > "following the scripts provided by NRAO, including flux, phase, bandpass, and gain calibrations." (Observations and data reduction)
- casa version: CASA 4.6.0  
  > "The data calibration was performed using CASA 4.6.0" (Observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1107-4449  
  > "| 2016 Jan 25 | 42      | 15-331         | 1.13   | J1107-4449 | J1427-4206 | J1058-8003 |" (Table 1)
- flux scale uncertainty: ~10%  
  > "We estimated the systematic flux uncertainty of $\sim$10$\%$ based on the amplitude and phase variations of the calibrators over time." (Observations and data reduction)
- self calibration: not applied  
  > "Self-calibration was not applied on these weak sources." (Observations and data reduction)

### Imaging

- task: clean in CASA  
  > "with natural weighting in *clean*" (Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "with natural weighting in *clean*" (Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.1" x 0.7"  
  > "The typical continuum beam size is 1.$\ensuremath{''}$1$\times$0.$\ensuremath{''}$7, when all baselines are included." (Observations and data reduction)
- final rms: _not stated_

### Inherited from earlier work

- Continuum flux measurement by uvmodelfit visibility fitting  
  > "we fit the visibility data using the CASA task *uvmodelfit*, following the description in (cite: barenfeld2016)." (Results) [from (cite: barenfeld2016)]
- Dust mass calculation assumptions  
  > "Dust masses in column 11 are calculated based on the same assumption as in (cite: pascucci2016) and for a constant temperature of 20 K." (Table 2) [from (cite: pascucci2016)]
- Bayesian linear regression method for Fmm-M* relation  
  > "using a Bayesian linear regression method, following (cite: pascucci2016)" (Results) [from (cite: pascucci2016)]
- Elliptical models applied to detected sources with S/N>5  
  > "As in our Cycle 2 survey, elliptical models are also applied in *uvmodelfit* to all detected sources with a signal-to-noise larger than 5" (Results) [from Cycle 2 survey (cite: pascucci2016)]

### Not stated but needed to reproduce (our reading)

- Dust opacity and gas-to-dust ratio values used for dust masses (deferred to Pascucci 2016)
- Clean mask, threshold and image size/cell size
- Line-free channel selection for continuum
- Linmix priors and settings
- How the random 7% of Cool-sample upper limits was drawn
- RADMC-3D disk and stellar parameters (inner radius, scale height, grain sizes)
- Cycle 3 data reduction details beyond NRAO scripts
- Detail of the 12CO imaging

## Analysis recipe

1. **Image continuum**: Average continuum channels of calibrated visibilities, natural weighting in clean  
  > "Continuum images were created using the calibrated visibilities by averaging all the continuum channels, with natural weighting in *clean*" (Observations and data reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure continuum flux densities**: uvmodelfit point-source or elliptical Gaussian fits to visibilities; uncertainties scaled by sqrt reduced chi2; non-detections refit with fixed offsets  
  > "The uncertainties of the fitted parameters are scaled by the square root of the reduced $\chi^{2}$ of the fit." (Results); "the continuum emission is re-calculated by fitting a point-source model with fixed phase center offsets" (Results)
   - software: CASA uvmodelfit
   - parameter: Detection if flux >3 sigma near expected position  
  > "Flux densities that are brighter than three times the uncertainty and located near the expected source position are considered detections." (Results)
   - fitting: Least squares in uv plane; 3 free parameters for point source (F, dRA, dDec)  
  > "This model has three free parameters: the integrated flux density ($F_\nu$), the phase center offsets in right ascension ($\Delta\alpha$) and in declination ($\Delta\delta$)." (Results)
   - validation: Compared with Cycle 2 fluxes; flux ratios 0.8-1.5  
  > "The flux ratios of the sources detected in both observations range from 0.8–1.5, with an average value of 1.2." (Results)
3. **Derive dust masses**: Same assumptions as Pascucci 2016, constant T=20 K, distance 190 pc  
  > "Dust masses in column 11 are calculated based on the same assumption as in (cite: pascucci2016) and for a constant temperature of 20 K." (Table 2)
   - assumption: T = 20 K; distance 190 pc  
  > "for a constant temperature of 20 K" (Table 2)
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit Fmm-M* scaling relation**: Linmix Bayesian linear regression in log-log plane including upper limits, with and without outliers  
  > "here we use the python equivalent *Linmix*" (Footnote 4)
   - software: Linmix
   - assumption: Linear relation in log-log plane with Gaussian scatter  
  > "assuming a linear scaling relation in the log-log plane" (Results)
   - fitting: Linmix (Kelly 2007 method)  
  > "(cite: pascucci2016) used the (cite: kelly2007) $IDL$ routine, while here we use the python equivalent *Linmix*" (Footnote 4)
   - validation: Compared to Pascucci 2016 slope 1.9±0.2 and intercept 1.6±0.1  
  > "The fitted parameters are consistent with the best-fit values from (cite: pascucci2016), with a slope of $1.9\pm0.2$ and an intercept of $1.6\pm0.1$" (Results)
5. **Model SED of CHXR30A with circumsecondary disk**: RADMC-3D SED model; two stars 80 AU apart; secondary disk truncated at ~30 AU; disk-to-star mass ratio set to match mm upper limit  
  > "The ratio of disk mass [^12] to stellar mass is adjusted to satisfy the millimeter flux upper limit." (6.3 Disks around the secondary star)
   - software: RADMC-3D
   - parameter: Secondary mass 0.28 Msun from Ks contrast 0.85  
  > "The $K_s$-band contrast of 0.85 from (cite: lafrenire2008) leads to an estimated stellar mass of 0.28 $M_\odot$" (Disks around the secondary star)
   - assumption: Dust: 25% carbon, 75% silicate amorphous grains  
  > "we include two populations of amorphous dust grains with 25% carbon and 75% silicate" (Footnote 12)
   - fitting: No best-fit; illustrative  
  > "While identifying the best-fit model for these systems is beyond the scope of this paper" (6.3 Disks around the secondary star)
   - validation: Compared with observed SED  
  > "The modeled SED reproduces well the observed SED structure" (6.3 Disks around the secondary star)

## Software

- **CASA** 4.6.0: Calibration, clean imaging, uvmodelfit  
  > "The data calibration was performed using CASA 4.6.0" (Observations and data reduction)
- **Linmix** : Bayesian linear regression of Fmm vs M*  
  > "here we use the python equivalent *Linmix*" (Footnote 4)
- **RADMC-3D** : SED modelling of CHXR30A  
  > "we use the radiative transfer code RADMC-3D (cite: dullemond2012) to model the SED" (6.3 Disks around the secondary star)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Detection rate of Hot sample | 94% (51/54) | not stated | percent | 2 | the detection rate for the *Hot* Sample is now 94% (51/54) |
| Fmm-M* slope | 1.89 | 0.24 | dimensionless | 4 | $\log(F_{mm}/{\rm mJy})=1.89 (\pm0.24)\times \log(M_\star/M_\odot)+1.57(\pm 0.14)$ |
| Fmm-M* intercept | 1.57 | 0.14 | log mJy | 4 | $\log(F_{mm}/{\rm mJy})=1.89 (\pm0.24)\times \log(M_\star/M_\odot)+1.57(\pm 0.14)$ |
| Slope excluding outliers | 2.07 | 0.21 | dimensionless | 4 | $\log(F_{mm}/{\rm mJy})=2.07 (\pm0.21)\times \log(M_\star/M_\odot)+1.81(\pm 0.13)$ |
| Intercept excluding outliers | 1.81 | 0.13 | log mJy | 4 | $\log(F_{mm}/{\rm mJy})=2.07 (\pm0.21)\times \log(M_\star/M_\odot)+1.81(\pm 0.13)$ |
| Gaussian scatter of residuals | mean 0.12, sigma 0.26 | not stated | dex | 4 | a Gaussian fit with a mean value of 0.12 and 1$\sigma$ spread of 0.26 |
| Dust mass upper limits of non-detections | ~0.2 | not stated | Earth masses | 3 | The dust mass upper limits are only $\sim$0.2 $M_\ensuremath{\oplus}$ |
| T24 flux | 6.57 | 0.25 | mJy | 2 | / J11071206-7632232 / T24 /  / M0 / -0.23 / 4.23$\pm$0.81 / 6.57$\pm$0.25 |

## Qualitative findings

- Of 14 targets, 11 detected at >3 sigma; six previously undetected sources now detected.  
  > "Of the 14 observed sources in our Cycle 3 program, 11 are detected with a signal-to-noise ratio of $>$3." (Results)

## Claim tuples

- H: Does the stellar-disk mass relation survive deeper data? | E: Refit Fmm-M* with Cycle 3 fluxes using Linmix | R: Slope 1.89±0.24, intercept 1.57±0.14, consistent with Pascucci 2016 | F: Relation is robust | **supported**
- H: Why are three disks undetected? | E: Compare SEDs, accretion and multiplicity | R: All three have close companions <=100 AU, weak accretion and weak IR excess | F: Tidal interaction plus internal photoevaporation may hasten evolution | **partially**
- H: Could a disk only around the secondary explain faint binary SEDs? | E: RADMC-3D SED model of CHXR30A | R: Model matches observed SED and mm upper limit | F: Circumsecondary-only disk is plausible | **partially**

## Reasoning

- Why this data: Faintest Hot-sample disks targeted for deeper observation  
  > "we were able to request deeper observations of the faintest *Hot* stars in our Cycle 3 program" (Observations and data reduction)
- Why this method: _not stated_
- Alternative: Fast grain growth proposed for CHXR20 and other faint disks  
  > "Fast grain growth is capable of explaining the observed SED morphologies in these four disks" (Individual disk evolution)
- How they decided it was enough: _not stated_
- Limitation (authors): Binaries at <~100 AU unresolved at the beam size  
  > "We note that systems with projected separations $\lesssim$ 100 AU should remain unresolved at our spatial resolution." (Discussion)
- Caveat (inferred, ours): Cycle 2 vs Cycle 3 flux differences (ratio ~1.2) attributed to Pallas calibrator without quantitative test
- Caveat (inferred, ours): Outlier exclusion and random 7% of upper limits is ad hoc
- Caveat (inferred, ours): SED model is illustrative and not fitted

## Reproducibility

- Data public (paper): Data acknowledged as ADS/JAO.ALMA#2015.1.00333.S  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00333.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Dust opacity and gas-to-dust values (in Pascucci 2016)
- Missing: Clean parameters
- Missing: RADMC-3D inputs
- Data volume (inferred): ~10-50 GB (14 short Band 7 observations)
- Score (inferred): 3/5, Simple measurements and public data, but dust-mass assumptions and several settings are deferred to earlier work.
- Rediscovery candidate: yes, Public data, a simple uvmodelfit recipe, and numeric results (fluxes, scaling relation).

## Links

- Method: (cite: pascucci2016) (Cycle 2 survey, dust mass method, regression)
- Method: (cite: barenfeld2016) (uvmodelfit flux measurement)
- Companion: (cite: manara2016; manara2017) (Accretion rates and spectral types)
- Related: ALMA Cycle 2 Chamaeleon I survey 2013.1.00437.S

## Checks

```json
{
 "quotes": 72,
 "quotes_ok": 72,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2013.1.00437.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 54,
  "rate": 0.692
 },
 "evidence_ok": true
}
```
