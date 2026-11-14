# An Intensity Mapping Detection of Aggregate CO Line Emission at 3 mm

`2020ApJ...901..141K` | The Astrophysical Journal 2020 | first author: Keating, Garrett K. | arXiv: 2008.08087 | DOI: 10.3847/1538-4357/abb08e

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, cosmology
- Question: Can line intensity mapping of 3 mm ALMA and ACA visibility data detect aggregate CO line emission at z~1-5, and what does it imply for shot power and cosmic molecular gas density?  
  > "We present a detection of molecular gas emission at $z\sim1-5$ using the technique of line intensity mapping." (abstract)
- Target **ASPECS field in Hubble Ultra Deep Field**: coordinates 03h32m38.5s, -27d47m00s (J2000)  
  > "centered on the position $\alpha=03^{\rm h}32^{\rm m}38.5^{\rm s}$, $\delta=-27^{\circ}47^{\prime}00^{\prime\prime}$ (J2000)" (2.1 ASPECS Data); z/distance _not stated_; distance from _not stated_
- Target **COSMOS field ACA mosaic (AzTEC-3 centered)**: coordinates 10h00m20.7s, +02d35m17s (J2000)  
  > "centered on the position of a source known as AzTEC-3 ($\alpha=10^{\rm h}00^{\rm m}20.7^{\rm s}$, $\delta=+02^{\circ}35'17''$, J2000)" (2.2 ACA Data); z/distance AzTEC-3 at z=5.3  
  > "centered on the position of a source known as AzTEC-3 ($\alpha=10^{\rm h}00^{\rm m}20.7^{\rm s}$, $\delta=+02^{\circ}35'17''$, J2000)" (2.2 ACA Data); distance from Scott2008; Dwek2011  
  > "centered on the position of a source known as AzTEC-3 ($\alpha=10^{\rm h}00^{\rm m}20.7^{\rm s}$, $\delta=+02^{\circ}35'17''$, J2000)" (2.2 ACA Data)

## Data provenance

- ALMA projects: 2016.1.01149.S, 2018.1.01594.S, 2016.1.00324.L, 2013.1.00146.S
- bands: Band 3 (84-115 GHz)  
  > "Five separate tunings were used to cover the entirety of Band 3, which spans from 84-115 GHz" (2.1 ASPECS Data)
- frequencies and spectral setup: ASPECS 3.906 MHz resolution, 2x1.875 GHz SPWs per sideband; ACA 7.813 MHz resolution, three tunings; averaged to 15.625 MHz  
  > "All data were recorded at 3.906 MHz spectral resolution, with two spectral windows of 1.875 GHz apiece per sideband." (2.1 ASPECS Data); "we average down the data to 15.625 MHz resolution for both ACA and ASPECS data" (3.1 Data Reduction Pipeline)
- continuum bandwidth: _not stated_
- arrays: ALMA 12-m (ASPECS) and ACA 7-m  
  > "2016.1.01149.S | 7-m | $94-98$, $106-110$ | 9.7 | 40.2" (Table 1)
- configurations: ASPECS: C40-3 and C40-4; ACA fixed  
  > "Data were collected in the configurations C40-3 and C40-4, with baselines of between 15-460 m and 15-704 m respectively." (2.1 ASPECS Data)
- baselines: ACA 7-45 m  
  > "with baselines between 7 and 45 m in length" (2.2 ACA Data)
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: ASPECS 38.1 h; ACA 40.2 h + 80.6 h  
  > "2018.1.01594.S | 7-m | $86-94$, $98-106$ | 9.8 | 80.6" (Table 1)
- observing dates: ASPECS Dec 2016; ACA Oct-Nov 2016 and Oct-Dec 2018  
  > "between October 3 and December 11, 2018" (2.2 ACA Data)
- pi or archival as stated: _not stated_
- Line: CO J=2-1, 3-2, 4-3, 5-4 (aggregate, unresolved) (not stated)
- External data: CO line ratios r_J1 = 0.76, 0.42, 0.31, 0.23 for J=2-5  
  > "The derived line ratios for $J=2,3,4,5$ are $r_{J,1}=0.76{\pm}0.09,\,0.42{\pm}0.07,\,0.31{\pm}0.06,\,0.23{\pm}0.04$" (5.2 Power Spectrum Estimates of Individual Lines) [from Daddi2015]
- External data: L_IR-L'_CO 'full sample' relations  
  > "we instead adopt the “full sample” correlations from (cite: Kamenetzky2016)" (5.1 Modeling the multiple transitions of CO) [from Kamenetzky2016]
- External data: 3-mm source count model for continuum  
  > "Adopting the 3-mm source count model of (cite: Zavala2018)" (3.2.1 The Impact of Continuum Foregrounds) [from Zavala2018]
- External data: Sample variance simulations from TNG300  
  > "we use simulation results of Keenan et al. (2020; submitted), which utilizes the TNG300 simulations" (4.2 The Impact of Sample Variance) [from Keenan et al. 2020 (submitted); Nelson2019]
- Simulation/model as data: Li2016 CO model with Behroozi2013 SFR, 0.3 dex scatter  
  > "We adopt the fiducial model of (cite: Li2016), hereafter referred to as , with one significant modification" (5.1 Modeling the multiple transitions of CO)

## Processing

### Calibration

- pipeline or manual: ALMA pipeline in CASA, then custom MATLAB re-derivation of bandpass, SEFD and gains  
  > "we utilize the existing ALMA pipeline software (cite: Shinnaga2015) within the *Common Astronomy Software Applications* package" (3.1 Data Reduction Pipeline)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ~5%  
  > "The absolute flux uncertainty is estimated to be of order $\sim$5%" (3.1 Data Reduction Pipeline)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting for gridding  
  > "the data are naturally weighted and gridded using a simple, rectangular (i.e., Shah) gridding function" (3.1 Data Reduction Pipeline)
- uv taper: _not stated_
- cell size: uv cells 10% of antenna diameter  
  > "into cells of size $10\%$ of the antenna diameter" (3.1 Data Reduction Pipeline)
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

- Analysis pipeline follows COPSS II  
  > "Analysis of the data closely follows the prescription used for ." (3 Analysis) [from Keating2016; Keating2015]
- ASPECS description and imaging  
  > "A more through description of the ASPECS can be found in (cite: GonzalezLopez2019) and (cite: Decarli2019)" (2.1 ASPECS Data) [from GonzalezLopez2019; Decarli2019]

### Not stated but needed to reproduce (our reading)

- CASA and pipeline version
- MATLAB reduction code not released
- Exact flagging thresholds and SEFD fitting details
- Weights C_ij for the estimator
- Cosmology-based mapping details of k bins
- Keenan et al. simulation light cones for sample variance PDFs

## Analysis recipe

1. **Calibrate and clean visibilities**: ALMA pipeline in CASA, export to MATLAB, flag, refit bandpass, SEFD corrections from time-differenced noise, average to 15.625 MHz  
  > "we difference visibilities that are adjacent in time" (3.1 Data Reduction Pipeline)
   - software: CASA, MATLAB
   - parameter: Discard two tracks with 20-30% flagged (2% of data)  
  > "We discard all data from these two tracks, amounting to a loss of $2\%$ of the total data volume." (3.1 Data Reduction Pipeline)
   - fitting: _not stated_
   - validation: Noise agreement in image domain  
  > "The net impact of these corrections can be seen in the agreement between the estimated and measured noise in the image domain" (3.1 Data Reduction Pipeline)
2. **Grid delay-visibilities**: Fourier transform along frequency, grid in (u,v,eta,nu_c)  
  > "Each spectral window in each baseline is separately Fourier transformed along the frequency axis" (3.1 Data Reduction Pipeline)
   - fitting: _not stated_
   - validation: _not stated_
3. **Estimate spectral shot power**: Cross-multiplied delay-visibility estimator, inverse-variance averaged; exclude baselines >100 klambda, eta>=500 and eta=0  
  > "We exclude baselines of length $\gtrsim {\rm 100\ k\lambda}$" (3.2 Power Spectrum Analysis)
   - fitting: _not stated_
   - validation: 10^4 simulated trials agree to ~1%; six jackknife tests plus phase randomization  
  > "we find good agreement for both to within $\sim1\%$ percent of expectations" (3.2 Power Spectrum Analysis)
4. **Correct for sample variance**: TNG300 light-cone PDFs, maximum likelihood estimate of true shot power  
  > "We then run a maximum likelihood estimation (MLE) analysis to calculate the true spectral shot power" (4.2 The Impact of Sample Variance)
   - fitting: MLE on log intervals of shot power  
  > "we have evaluated the likelihoods in Figure [6](#fig:linepow_cv) on logarithmic intervals of $\tilde{I}^{2}_{s}(\nu)$" (Results, The Impact of Sample Variance)
   - validation: _not stated_
5. **Model line contributions and derive rho_H2**: Li2016-based model gives f_total per line; Daddi2015 line ratios to CO(1-0); halo-mass luminosity relation, Tinker mass functions, alpha_CO  
  > "Assuming a value $\alpha_{\rm CO}=3.6\ M_{\ensuremath{\odot}}\ (\textrm{K}\ \textrm{km}\ \textrm{s}^{-1}\ \textrm{pc}^{2})^{-1}$" (5.5 Constraints on Cosmic Molecular Gas Abundance)
   - assumption: alpha_CO=3.6; M0=1e12 Msun/h; h=0.7, Om=0.27  
  > "$h=0.7$, $\Omega_{\textrm{m}}=0.27$, $\Omega_{\Lambda}=0.73$" (Introduction)
   - fitting: fit A_CO to CO(1-0) estimates  
  > "we are able to fit for the value of $A_{\textrm{CO}}$ using the CO(1-0) estimates using the (cite: Daddi2015) estimates for the CO line ratios" (Discussion, Constraints on Cosmic Molecular Gas Abundance)
   - validation: _not stated_

## Software

- **CASA** : ALMA pipeline calibration and export  
  > "within the *Common Astronomy Software Applications* package (CASA; (cite: Jaeger2008))" (3.1 Data Reduction Pipeline)
- **MATLAB** 2019a: custom reduction and power spectrum software  
  > "exported from CASA into our MATLAB[^1]-based reduction software package" (3.1 Data Reduction Pipeline)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Spectral shot power, ASPECS | 730 | 240 | uK^2 Hz sr | 3 | We measure $\tilde{I}^{2}_{s}(\nu)=730\pm240\ \mu\textrm{K}^2\ \textrm{Hz}\ \textrm{sr}$ for the ASPECS data. |
| Spectral shot power, ACA | 890 | 440 | uK^2 Hz sr | 3 | For the ACA data, we measure $\tilde{I}^{2}_{s}(\nu)=890\pm440\ \mu\textrm{K}^2\ \textrm{Hz}\ \textrm{sr}$. |
| Spectral shot power, joint | 770 | 210 | uK^2 Hz sr | 3 | finding $\tilde{I}^{2}_{s}(\nu)=770\pm210\ \mu\textrm{K}^2\ \textrm{Hz}\ \textrm{sr}$ |
| Spectral shot power after sample variance (MLE) | 1010 | +550/-390 | uK^2 Hz sr | 4 | the estimated spectral shot power is $\tilde{I}^{2}_{s}(\nu)=1010_{-390}^{+550}\ \mu\textrm{K}^2\ \textrm{Hz}\ \textrm{sr}$ |
| CO(3-2) shot power at z=2.5 | 200 | +120/-70 | uK^2 h^-3 Mpc^3 | 5 | $200^{+120}_{-70}\ \mu\textrm{K}^2\ h^{-3}\,\textrm{Mpc}^{3}$ |
| rho_H2 at z=2.5 | 9.7e7 | +3.2/-2.5 e7 | Msun Mpc^-3 | 5 | 2.5 / $2.0{-}3.1$ / $\phn9.7_{-2.5}^{+3.2}$ |
| COPSS CO(1-0) shot power z=2.6 | 2000 | +1100/-1200 | uK^2 h^-3 Mpc^3 | 0 | $P_{\rm shot}(z)=2000_{-1200}^{+1100}\ \mu\textrm{K}^2\ h^{-3}\,\textrm{Mpc}^{3}$ |

## Qualitative findings

- Intensity mapping estimates lie above direct-detection ones at z~2-3, possibly capturing sub-threshold galaxies  
  > "suggest that such measurements may be capturing emission from galaxies below direct detection threshold" (5.5 Constraints on Cosmic Molecular Gas Abundance)

## Claim tuples

- H: Is there non-zero aggregate line power at 100 GHz? | E: Visibility-domain power spectrum of ASPECS and ACA data | R: 770±210 uK^2 Hz sr joint | F: Zero power rejected at 99.99% | **supported**
- H: Is the signal free of systematics? | E: Six jackknife tests | R: Consistent with null, band-averaged <2 sigma | F: Data sufficiently free of systematics | **supported**
- H: Does the result agree with models and COPSS? | E: Modified Li2016 model and line ratios | R: Model within 20% (0.4 sigma); COPSS consistent | F: Good agreement | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Spectral shot power avoids assuming a single line/redshift or cosmology  
  > "it requires no assumptions about the underlying cosmology, nor division of the signal into separate redshift bins" (3.2 Power Spectrum Analysis)
- Alternative: Subtracting continuum sources rejected in favor of excluding eta=0 modes  
  > "Rather than attempting to subtract out individual sources, which may introduce its own set of artifacts and systematics" (3.2.1 The Impact of Continuum Foregrounds)
- How they decided it was enough: _not stated_
- Limitation (authors): Uncertainties significant; sample variance dominates; follow-up needed  
  > "the results presented here will likely require further observational follow-up, particularly as the uncertainties on our measurement are significant" (6 Conclusion)
- Caveat (inferred, ours): Line attribution depends on a model
- Caveat (inferred, ours): Tension with Uzgil2019 on same ASPECS data
- Caveat (inferred, ours): No linewidth correction applied
- Caveat (inferred, ours): Sample variance relies on unpublished simulations

## Reproducibility

- Data public (paper): ALMA project codes listed; archive data  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA #2013.1.00146.S" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Custom MATLAB pipeline not released
- Missing: Sample-variance simulations from unpublished paper
- Data volume (inferred): Several hundred GB to ~1 TB raw visibilities (~120 tracks)
- Score (inferred): 3/5, Data public and method described in detail, but custom code and unpublished simulations are required.
- Rediscovery candidate: no, Requires unreleased custom visibility power spectrum code and external simulations.

## Links

- Method: Keating2015 (Original visibility-domain power spectrum pipeline (COPSS I))
- Companion: Keating2016 (COPSS II, CO(1-0) power spectrum)
- Companion: Uzgil2019 (Image-domain power spectrum of ASPECS)
- Related: ASPECS
- Related: COPSS
- Related: COLDz
- Related: PHIBSS2
- Related: mmIME

## Checks

```json
{
 "quotes": 58,
 "quotes_ok": 58,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 41,
  "rate": 0.547
 },
 "evidence_ok": true
}
```
