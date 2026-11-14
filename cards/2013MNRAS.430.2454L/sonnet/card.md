# Variations in the fundamental constants in the QSO host J1148+5251 at z = 6.4 and the BR1202-0725 system at z = 4.7

`2013MNRAS.430.2454L` | Monthly Notices of the Royal Astronomical Society 2013 | first author: Lentati, L. | arXiv: 1211.3316 | DOI: 10.1093/mnras/stt070

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies, agn_and_quasars, cosmology
- Question: Do the CO and [C II] redshifts of high-z quasar hosts and an SMG differ (Delta z), and can this constrain variation of F = alpha^2/mu, given possible spatial and velocity offsets between the gas species?  
  > "We use these observations to place constraints on the quantity $\Delta z = z_{CO} - z_{C_{II}}$ for each source" (abstract)
- Target **J1148+5251**: coordinates _not stated_; z/distance z = 6.4  
  > "The observations of the [C II] line for J1148+5251 were made with the Plateau de Bure Interferometer (PdB) in 2011" (Observations); distance from _not stated_
- Target **BR1202-0725 QSO and SMG**: coordinates _not stated_; z/distance z = 4.7  
  > "its sub-millimeter companion (SMG) galaxy at $z=4.7$" (abstract); distance from _not stated_

## Data provenance

- ALMA projects: _none stated_
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: ALMA channels ~16 MHz (QSO), 32 MHz (SMG); noise 0.65 and 0.8 mJy/beam per channel  
  > "with noise levels per channel of 0.65 and 0.8 mJy beam$^{-1}$ per channel respectively." (Observations)
- time on source: BR1202 [C II] ALMA: 25 minutes; J1148 [C II] PdBI: 17.5 hours  
  > "The observations lasted 25 minutes and produced signal to noise ratios of $\sim$ 80 for both lines" (Observations)
- observing dates: ALMA [C II] of BR1202 during 2012  
  > "observations of the two lines were made with the Atacama Large Millimeter Array (ALMA) during 2012." (Observations)
- pi or archival as stated: _not stated_
- Line: C+ 2P3/2 -> 2P1/2 (not stated)
- Line: CO J=5-4 and J=2-1 (not stated)
- Other facility **PdBI**: J1148 [C II]; BR1202 CO(5-4)  
  > "The CO (J = $5\to4$) observations were made with the PdB in February 2007" (Observations)
- Other facility **JVLA**: J1148 CO(2-1)  
  > "The CO (J = $2\to1$) line was observed with the Jansky Very Large Array (JVLA) in 2011." (Observations)
- External data: Detailed description of the BR1202 [C II] ALMA observations  
  > "For a detailed description of the [C II] observations made of the two BR1202$-$0725 sources see (cite: 2012ApJ...752L..30W)." (Observations) [from (cite: 2012ApJ...752L..30W)]
- External data: BR1202 CO(5-4) PdBI data  
  > "for a detailed description refer to (cite: 2012arXiv1207.6722S)" (Observations) [from (cite: 2012arXiv1207.6722S)]
- External data: J1148 [C II] PdBI data  
  > "made with the Plateau de Bure Interferometer (PdB) in 2011(cite: 2012MNRAS.425L..66M)" (Observations) [from (cite: 2012MNRAS.425L..66M)]

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
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA BR1202 data reduction and observation details  
  > "For a detailed description of the [C II] observations made of the two BR1202$-$0725 sources see (cite: 2012ApJ...752L..30W)." (Observations) [from (cite: 2012ApJ...752L..30W)]

### Not stated but needed to reproduce (our reading)

- Spectra extraction details for BR1202 (aperture)
- MultiNest settings and priors
- ALMA project code and calibration
- Rest frequencies adopted
- Exact velocity frame conversions per line

## Analysis recipe

1. **Fit line profiles with shapelets**: Bayesian fit of shapelet basis, evidence compared for independent vs joint models  
  > "Using the MULTINEST algorithm (cite: 2009MNRAS.398.1601F), we are able to analyse efficiently spectral data containing individual, or multiple emission lines" (3.1 Model Selection)
   - software: MultiNest
   - parameter: O_thresh = 2%  
  > "For the following work we therefore set $O_{\mathrm{thresh}}$=2$\%$." (3 Shapelets)
   - assumption: Diagonal covariance with per-channel noise; shapelet line shapes positive  
  > "which in all the following work we take to be diagonal, with elements $N_{ii} = \sigma_i^2$" (Marginalizing)
   - fitting: MultiNest nested sampling; priors not stated  
  > "Using the MULTINEST algorithm (cite: 2009MNRAS.398.1601F), we are able to analyse efficiently spectral data containing individual, or multiple emission lines" (Model Selection)
   - validation: _not stated_
2. **Marginalise over models for Delta z**: Integrate posterior over all shapelet parameters and n_max to get P(Delta z)  
  > "where we have integrated over all model parameters $\theta$." (Marginalizing)
   - software: MultiNest
   - assumption: Delta z entirely due to Delta F/F: Delta z/(1+z_avg) = Delta F/F  
  > "\frac{\Delta z}{1+z_{avg}} = \frac{\Delta F}{F}," (Introduction)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **MultiNest** : Bayesian evidence and model selection for shapelet fits  
  > "Using the MULTINEST algorithm (cite: 2009MNRAS.398.1601F)" (3.1 Model Selection)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| J1148+5251 Delta z (joint fit) | -2.7e-3 | 0.6e-3 | dimensionless | 1 | We find $\Delta z = (-2.7 \pm 0.6 \times 10^{-3})$ |
| J1148+5251 marginalised Delta z (99% CI) | -2.4e-3 | 1.7e-3 | dimensionless | 2 | 99$\%$ confidence interval for the value $\Delta z$ of $(-2.4 \pm 1.7 ) \times 10^{-3}$ |
| BR1202 QSO Delta z (joint fit) | -3e-4 | 3e-4 | dimensionless | 1 | $\Delta z = (-3 \pm 3) \times 10^{-4}$ |
| BR1202 SMG Delta F/F (joint fit) | -3.5e-4 | 2.0e-4 | dimensionless | 1 | $\Delta F/F = (-3.5 \pm 2.0) \times 10^{-4}$ |

## Qualitative findings

- CO(5-4) lines are ~30% wider than [C II] in BR1202 QSO and SMG, indicating spatial separation of the gas  
  > "in both cases the CO (J = $5\to4$) was approximately 30$\%$ wider than the [C II]." (5.3)

## Claim tuples

- H: Delta z between CO and [C II] reflects variation of F | E: Shapelet joint fits and marginalisation | R: Delta z nonzero for J1148 but line profiles differ for BR1202 sources | F: Delta z cannot be attributed solely to constants variation; spatial/velocity offsets contribute | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Unknown relative distribution and velocities of the two gas species limit constraints  
  > "with our results being fundamentally limited by this unknown factor that represents the relative distributions and velocities of the gas within the host galaxy." (Conclusions)
- Caveat (inferred, ours): Delta z values are inconsistent between joint fit and marginalised results (e.g. SMG table entries)
- Caveat (inferred, ours): Frame conversions to LSR add velocity uncertainty comparable to Delta z
- Caveat (inferred, ours): Spectra taken from unresolved apertures

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Project codes and calibrated spectra
- Missing: Shapelet fitting code and priors
- Data volume (inferred): small (spectra only if reduced products obtained); raw ALMA SV data tens of GB
- Score (inferred): 2/5, ALMA is a minor part, spectra are inherited from earlier papers, and priors and code are not given.
- Rediscovery candidate: no, Reduced spectra are from earlier papers and the fitting settings are incomplete.

## Links

- Method: (cite: 2003MNRAS.338...35R) (Shapelet formalism)
- Method: (cite: 2008A&A...479..719L) (CO vs fine-structure line method for Delta F/F)
- Companion: (cite: 2012ApJ...752L..30W) (BR1202 ALMA [C II] observations)

## Checks

```json
{
 "quotes": 29,
 "quotes_ok": 29,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00006.SV"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 64,
  "stated": 21,
  "rate": 0.328
 },
 "evidence_ok": true
}
```
