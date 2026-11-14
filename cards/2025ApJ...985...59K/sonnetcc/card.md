# PKS 2131−021—Discovery of Strong Coherent Sinusoidal Variations from Radio to Optical Frequencies: Compelling Evidence for a Blazar Supermassive Black Hole Binary

`2025ApJ...985...59K` | The Astrophysical Journal 2025 | first author: Kiehlmann, S. | arXiv: 2407.09647 | DOI: 10.3847/1538-4357/adc567

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type multi_facility_alma_minor

## Science

- Fields: agn_and_quasars
- Question: Whether PKS 2131-021 is a supermassive black hole binary: do the coherent sinusoidal flux-density variations persist through 2023, are they statistically significant against red noise, and do they extend from radio to optical with a monotonic phase shift  
  > "In this paper, we present further evidence, which we find compelling, supporting the hypothesis of the SMBHB nature of PKS 2131$-$021." (Introduction); "We find the coherent sinusoidal intensity variations extend from below 2.7 GHz to optical frequencies" (abstract)
- Target **PKS 2131-021**: coordinates _not stated_; z/distance z = 1.283  
  > "The period for the weighted fit in the $z=1.283$ rest frame of the host galaxy is" (2.1 The OVRO+Haystack period fit); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00001.CAL
- bands: ALMA light curves at 91.5 GHz, 104 GHz and 345 GHz (continuum flux densities from the calibrator website)  
  > "and ALMA observations at 91.5 GHz, 104 GHz, and 345 GHz" (Introduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: ALMA linear polarization shown from 2019 to 2023.5 at 91.5 GHz and 103.5 GHz  
  > "The variation in the linear polarization at 91.5 GHz and 103.5 GHz from 2019 to 2023.5 seen by ALMA" (5 The Radio Spectrum, Structure, and Polarization of PKS 2131-021)
- pi or archival as stated: Data downloaded from the ALMA calibrator website (not a PI proposal)  
  > "We downloaded ALMA data from the ALMA calibrator website." (3 The Effects of Correlated Noise)
- Other facility **OVRO 40 m Telescope**: 15 GHz total flux-density monitoring light curve  
  > "The 40 m Telescope of the Owens Valley Radio Observatory (OVRO) has been dedicated to monitoring the total 15 GHz flux densities" (Introduction)
- Other facility **Haystack**: 1975-1983 multi-frequency light curves at 2.7, 7.9, 15.5 and 31.4 GHz  
  > "using Haystack observations from 1975–1983 (cite: 1986AJ.....92.1262O) at 2.7 GHz, 7.9 GHz, 15.5 GHz and 31.4 GHz" (Introduction)
- Other facility **WISE**: Infrared 2.8-3.8 and 4.1-5.2 micron light curves  
  > "We have extracted the Wide Field Infrared Explorer (WISE) data in the 2.8–3.8 micron and 4.1–5.2 micron bands." (6.1 The 2.8 um-5.2 um emission)
- Other facility **Zwicky Transient Facility (ZTF)**: Optical g, r, i light curves up to 2023 Sep 9  
  > "We have now added another two years of ZTF data up to 2023 Sep 9, so that, all told, the ZTF data now span a full period." (6.2 The Strong Optical Sinusoidal Emission)
- Other facility **Swift/XRT**: Stacked X-ray spectrum, 20.7 ks net exposure  
  > "We analyzed all available *Swift/XRT* obervations." (7 X-ray Observations and Future Prospects)
- Other facility **Fermi-LAT**: 30-day binned gamma-ray light curve, 0.1-100 GeV, from the Fermi light curve repository  
  > "to extract the 30-day binned $\gamma$-ray light curve in the 0.1–100 GeV band" (8 The gamma-ray Emission)
- External data: Haystack 1975-1983 multi-frequency light curves  
  > "we show the Haystack multifrequency light curves from (cite: 1986AJ.....92.1262O)" (3 The Effects of Correlated Noise) [from (cite: 1986AJ.....92.1262O)]
- External data: OVRO 40 m 15 GHz blazar monitoring light curve  
  > "The OVRO 40-m Telescope blazar program (cite: Richards2011) is currently the largest radio flux-density monitoring program." (Introduction) [from (cite: Richards2011)]
- External data: Planck radio spectrum of PKS 2131-021 at eight epochs  
  > "as measured from centimeter to sub-millimeter wavelengths by the Planck observatory at eight different epochs (cite: 2023A&A...669A..92R)" (5 The Radio Spectrum, Structure, and Polarization of PKS 2131-021) [from (cite: 2023A&A...669A..92R)]
- External data: Jet angle to line of sight theta = 3.8 deg from MOJAVE VLBI  
  > "the angle between the jet axis and the line of sight of $\theta=3.8^\circ$ (cite: 2021ApJ...923...67H)" (9.1 Consistency of the observed light curves with the Kinematic Orbital Model) [from (cite: 2021ApJ...923...67H)]
- Simulation/model as data: Kinematic Orbital (KO) model of aberration from the orbital motion of the jet-producing black hole, used to interpret the light curves  
  > "which ascribes the sinusoidal variations in PKS 2131$-$021 to aberration caused by the orbital motion in an SMBHB of the black hole producing the jet" (Introduction)
- Simulation/model as data: Simulated red-noise light curves used to build the noise covariance matrices  
  > "but we can use as a proxy the lightcurve simulations." (Fit of sinusoidal model using simulation-based likelihood)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: ALMA flux densities taken as downloaded from the ALMA calibrator website  
  > "We downloaded ALMA data from the ALMA calibrator website." (3 The Effects of Correlated Noise)
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

- Sine-wave fitting procedure applied to the multi-frequency light curves  
  > "derived by the procedure presented in Paper 1 and in Appendix" (3 The Effects of Correlated Noise) [from Paper 1 (cite: 2022ApJ...926L..35O)]
- GLS periodogram significance tests and red-noise simulations (PSD and PDF matching)  
  > "We refer to Appendix A in Paper 1 for details." (4 Statistical Significance) [from Paper 1 (cite: 2022ApJ...926L..35O)]
- WISE-OVRO cross-correlation method  
  > "The cross-correlation between the OVRO and WISE data was performed following (cite: 2014MNRAS.445..437M)." (6.1 The 2.8 um-5.2 um emission) [from (cite: 2014MNRAS.445..437M)]

### Not stated but needed to reproduce (our reading)

- Which ALMA calibrator-catalog entries and date ranges were used, and how the three band light curves were selected, averaged or cleaned
- How ALMA flux-density uncertainties were treated in the sinusoidal fits (white noise assumed, but no error floor given)
- The exact MJD windows for the two fixed-period phase fits (the printed inequalities are garbled in the text)
- Where the OVRO 15 GHz, ZTF, WISE and Haystack light-curve tables used in the fits can be retrieved in the versions used
- Full GLS test and red-noise simulation recipe (deferred to Paper 1)
- MCMC convergence diagnostics and how the noise covariance matrix was thresholded

## Analysis recipe

1. **assemble multi-frequency light curves**: ALMA flux densities downloaded from the ALMA calibrator website and combined with OVRO, Haystack, WISE and ZTF light curves  
  > "We downloaded ALMA data from the ALMA calibrator website." (3 The Effects of Correlated Noise); "and ALMA observations at 91.5 GHz, 104 GHz, and 345 GHz" (Introduction)
   - software: ALMA calibrator website
   - fitting: _not stated_
   - validation: _not stated_
2. **fit a sine wave to OVRO plus Haystack 15 GHz data**: Least-squares sine fit with separate amplitude and offset for OVRO and Haystack; Haystack points up-weighted so the sine aligns across the 19-year gap  
  > "We allow separate values for $A$ and $S_0$ for the OVRO and Haystack sections of the data." (2.1 The OVRO+Haystack period fit); "The weights of the OVRO data points are all 1." (2.2 White Noise Model Fit)
   - parameter: Haystack weight 850/154 = 5.5  
  > "we have assigned a weight of 850/154 = 5.5 to each of the Haystack observations" (2.2 White Noise Model Fit)
   - assumption: Independent Gaussian noise with intrinsic scatter sigma_0  
  > "First, we treated all noise terms as independent Gaussian noise" (2.2 White Noise Model Fit)
   - fitting: _not stated_
   - validation: Compared with equal-weight fit and with the period from Paper 1  
  > "This has brought the sine wave into alignment with the Haystack data, with no discernible difference in the fit to the OVRO data." (2.2 White Noise Model Fit)
3. **fit the period with a correlated-noise likelihood**: Simulation-based noise covariance matrices; likelihood marginalised over linear parameters; posterior in P and amplitude ratio sampled by MCMC  
  > "With this parameterization the only non-linear parameters are $P$ and $A^{HO}$." (Fit of sinusoidal model using simulation-based likelihood)
   - software: emcee
   - parameter: 4 walkers, burn-in 30 000 samples, 30 000 output samples  
  > "using *emcee* with 4 walkers, a burn-in of 30 000 samples and 30 000 output samples" (Full MCMC search)
   - parameter: Priors P in [1000,3000] and A^HO in [0.1,4]  
  > "We used $P\in [1000,3000]$ and $A^{HO}\in [0.1,4]$ in our fit." (Likelihood)
   - assumption: Gaussian noise with covariances N^O and N^H taken from lightcurve simulations  
  > "We approximate the noise as Gaussian, with covariances $N^O$ and $N^H$." (The noise covariance matrix)
   - fitting: Gaussian marginalised likelihood, log P = 1/2 a^T A^-1 a + log prior, sampled with emcee  
  > "using *emcee* with 4 walkers, a burn-in of 30 000 samples and 30 000 output samples" (Full MCMC search)
   - validation: Noted as sensitive to the noise covariance matrix; error bars likely overestimated  
  > "This fit is quite sensitive to the details of the noise covariance matrix." (Full MCMC search)
4. **test significance against red-noise simulations**: Generalized Lomb-Scargle periodogram tests (OVRO peak, Haystack peak and period, phase match) against simulated power-law red-noise light curves, joint probability as product  
  > "We model the PDF through the empirical cumulative distribution function of the original light curve." (4 Statistical Significance); "We estimate the probability of all three observations as defined in tests 1–3 under the null hypothesis by multiplying the probabilities of the three independent tests." (4 Statistical Significance)
   - software: GLS periodogram
   - parameter: PSD power-law index beta = 2.05  
  > "with index $\beta=2.05$" (4 Statistical Significance)
   - parameter: 10^6 simulations for the OVRO test, 10,000 for the Haystack test  
  > "Based on 10,000 simulations we estimate a probability of" (4 Statistical Significance)
   - assumption: Null hypothesis: light curves come from a power-law red noise process matching the observed PSD and PDF  
  > "The null hypothesis is that the light curves originate from a power-law red noise process that reproduces the power spectral density (PSD) and probability density function (PDF)." (4 Statistical Significance)
   - fitting: _not stated_
   - validation: _not stated_
5. **measure phase offsets versus frequency including ALMA bands**: Fit a sinusoid with period fixed from the OVRO 15 GHz fit over the overlap interval, then fit ALMA 91.5, 104 and 345 GHz phases relative to 15 GHz  
  > "We then held this period fixed and carried out the sinusoidal fits to the ALMA 91.5 GHz, 104 GHz, and 345 GHz" (3.1 The Correlated Noise Phase Shift with Frequency)
   - parameter: Fixed OVRO period P = 2002.9 days for the ALMA-era interval  
  > "we derived a period $P=2002.9$ days" (3.1 The Correlated Noise Phase Shift with Frequency)
   - assumption: White noise; non-sinusoidal variations treated as dominated by Type-A (correlated across frequency)  
  > "Fit a phase per light curve using a sinusoidal model with the period fixed at the value for the best fitting OVRO light curve during the period of the overlapping multi-frequency light curves, assuming white noise." (3.1 The Correlated Noise Phase Shift with Frequency)
   - fitting: _not stated_
   - validation: _not stated_
6. **fit sine waves to the ZTF optical data**: Joint g, r, i sine fit by maximising a log-likelihood with intrinsic scatter; model 1 shared period and phase, model 2 filter-dependent phases  
  > "The best-fit parameters were found by maximizing the log-likelihood function defined as" (Sine-wave fits to the optical data); "Subsequently, we relaxed this assumption and allowed the sine phases to depend on the filter (model 2)." (Sine-wave fits to the optical data)
   - fitting: Maximum likelihood  
  > "The best-fit parameters were found by maximizing the log-likelihood function defined as" (Sine-wave fits to the optical data)
   - validation: _not stated_
7. **fit phase shift as a function of frequency**: Linear-logarithmic fit of phase shift to 2.7-345 GHz, plus a quadratic fit to all data  
  > "A linear fit to the 2.7 GHz - 345 GHz data is given by" (6.4 Coherence of the Periodicity from the Radio to the Optical Emission)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **emcee** : MCMC sampling of the period and amplitude-ratio posterior  
  > "using *emcee* with 4 walkers, a burn-in of 30 000 samples and 30 000 output samples" (Full MCMC search)
- **Generalized Lomb-Scargle periodogram** : Significance tests of the periodicity against simulated red noise  
  > "We carried out the generalized Lomb–Scargle (GLS)" (4 Statistical Significance)
- **ALMA calibrator website** : Source of the ALMA flux-density light curves  
  > "We downloaded ALMA data from the ALMA calibrator website." (3 The Effects of Correlated Noise)
- **Fermi light curve repository** : Gamma-ray light curve extraction  
  > "to extract the 30-day binned $\gamma$-ray light curve in the 0.1–100 GeV band" (8 The gamma-ray Emission)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Period, weighted OVRO+Haystack white-noise fit | 1739.2 | 1.2 | days | 2 | The corresponding period is $P=(1739.2\pm1.2)$ days |
| Period, correlated-noise MCMC fit (15 GHz) | 1739.8 | 17.4 | days | 3 | Our final fit parameters are $P = 1739.8 \pm 17.4$ days |
| Joint probability and significance of rejecting the red-noise null hypothesis | 2.09e-7 (5.06 sigma) | not stated | dimensionless | 4 | The joint probability is $2.09 \times 10^{-7}$ ($5.06\sigma$). |
| Phase shift of ALMA 91.5 GHz relative to 15 GHz | -0.073 | 0.005 | fraction of a cycle | 5 | 91.5 GHz / $-0.073$ / 0.005 |
| Phase shift of ALMA 104 GHz relative to 15 GHz | -0.077 | 0.005 | fraction of a cycle | 5 | 104 GHz / $-0.077$ / 0.005 |
| Phase shift of ALMA 345 GHz relative to 15 GHz | -0.134 | 0.009 | fraction of a cycle | 5 | 345 GHz / $-0.134$ / 0.009 |
| Optical period from combined ZTF g, r, i sine fit | 1764 | 36 | days | 6 | yields a period of $P_\textrm{optical}=(1764  \pm 36)$ days |
| Optical phase shift relative to 15 GHz | -0.352 | 0.008 | fraction of a cycle | 6 | Optical / $-0.352$ / 0.008 |
| Linear-log fit of phase shift versus frequency, 2.7-345 GHz | delta phi = 0.020 - 0.116 log10(nu/15), nu in GHz | not stated | fraction of a cycle | 7 | \delta \phi = 0.020 -0.116 \log_{10}(\nu/15) |

## Qualitative findings

- The 15 GHz sinusoid continued through 2023 consistent with the Paper 1 prediction, giving 47.9 years of coherence with the Haystack data  
  > "The observed 47.9 year continuity, when combined with the Haystack data, is unprecedented in the light curves of blazars." (2 The Continuation of the 15 GHz Sine Wave Signal in PKS 2131-021)
- Phase lag increases monotonically with decreasing frequency from 2.7 GHz through ALMA bands to optical  
  > "The monotonic variation in phase lag with frequency from 2.7 GHz to optical frequencies demonstrates convincingly that the sinusoidal variation is caused by a physical process in the source." (6.4 Coherence of the Periodicity from the Radio to the Optical Emission)
- ALMA 91.5 and 103.5 GHz EVPA changes little through the sinusoidal cycle  
  > "where it is seen that the EVPA changes little throughout the sinusoidal cycle." (5 The Radio Spectrum, Structure, and Polarization of PKS 2131-021)

## Claim tuples

- H: The sinusoidal variations are a random fluctuation of red noise | E: GLS tests of OVRO and Haystack data against simulated red noise matching PSD and PDF | R: Joint p-value 2.09e-7 (5.06 sigma) | F: The red-noise null hypothesis is rejected; a physical periodic process is present | **supported**
- H: The sinusoidal variation persists in new 15 GHz data without changing the model | E: Extrapolation of the sine fit to pre-2021 data compared with new OVRO data through 2023 | R: New data returned to the extrapolated sine curve in 2023 | F: The constant long-term period prediction is fulfilled | **supported**
- H: The coherent sinusoid extends from radio to optical with a smooth phase shift | E: Fixed-period sine fits to Haystack, OVRO, ALMA and ZTF light curves with phase relative to 15 GHz | R: Phase shifts of -0.073 (91.5 GHz), -0.077 (104 GHz), -0.134 (345 GHz) and -0.352 (optical) of a cycle | F: Monotonic phase lag with frequency from 2.7 GHz to optical | **supported**
- H: The periodicity is caused by orbital motion in a supermassive black hole binary | E: Comparison of the multi-frequency phase shifts and amplitudes with the Kinematic Orbital model | R: Data are consistent with the KO model; precessing accretion disk cannot be ruled out | F: SMBHB orbital motion is a distinct possibility but not uniquely established | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Phases fitted per band with a fixed period assuming white noise because non-sinusoidal variations appear dominated by Type-A errors  
  > "We adopt alternative 2 in this paper." (3.1 The Correlated Noise Phase Shift with Frequency); "If the correlated non-sinusoidal variations are dominated by Type-A errors, as appears to be the case, then we can either:" (3.1 The Correlated Noise Phase Shift with Frequency)
- Alternative: Fitting each frequency light curve as a scaled and offset version of the OVRO light curve (not adopted)  
  > "Fit the lightcurve at each frequency as a scaled and offset version of the OVRO light curve" (3.1 The Correlated Noise Phase Shift with Frequency)
- Alternative: Optical shift of 612 or 1127 days; 612 days chosen as it continues the monotonic trend  
  > "The time shift between the observed maxima in the sine wave fits to the optical light curves and the 15 GHz curve is 612 or 1127 days, depending on the direction of the shift." (6.2 The Strong Optical Sinusoidal Emission)
- How they decided it was enough: _not stated_
- Limitation (authors): Type-A and Type-B variations cannot be reliably distinguished, so a full noise treatment of the phase offsets is not possible  
  > "we cannot reliably distinguish between Type-A and Type-B variations" (3.1 The Correlated Noise Phase Shift with Frequency)
- Limitation (authors): Correlated-noise period fit is sensitive to the noise covariance matrix, with error bars likely overestimated  
  > "This fit is quite sensitive to the details of the noise covariance matrix." (Full MCMC search)
- Caveat (inferred, ours): ALMA contributes only three calibrator light curves, with no stated calibration, flux scale uncertainty or sampling, so the ALMA phase offsets cannot be checked from the paper alone
- Caveat (inferred, ours): White-noise phase uncertainties (0.005 of a cycle) look small compared with the correlated-noise period uncertainty and may be underestimated
- Caveat (inferred, ours): ALMA fit window uses a different period (2002.9 d) than the global period (about 1740 d), which is justified only qualitatively
- Caveat (inferred, ours): The optical phase direction (612 vs 1127 days) is chosen to continue the monotonic trend, which assumes the conclusion

## Reproducibility

- Data public (paper): ALMA data taken from the public ALMA calibrator website  
  > "We downloaded ALMA data from the ALMA calibrator website." (3 The Effects of Correlated Noise)
- Products in archive: ALMA calibrator data identifier printed in acknowledgements  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00001.CAL." (Acknowledgements)
- Code: _not stated_
- Missing: ALMA calibrator light-curve selection and flux values used
- Missing: OVRO, Haystack and ZTF data tables in the exact versions used
- Missing: Noise covariance simulation and GLS test details from Paper 1
- Missing: Fit time windows for the ALMA-era phase fit
- Missing: Code for the fits
- Data volume (inferred): Negligible for ALMA (calibrator flux-density light curves, kilobytes); the full paper also needs OVRO, ZTF, WISE and Fermi light curves, all small tables
- Score (inferred): 2/5, ALMA data are public calibrator light curves, but selection, errors and time windows are not given, key analysis steps are deferred to Paper 1, and no code is released.
- Rediscovery candidate: no, ALMA plays a minor role and the recipe depends on Paper 1 and on non-ALMA light curves whose public availability is not stated.

## Links

- Method: Paper 1 (cite: 2022ApJ...926L..35O) (Sine-wave fitting procedure, GLS red-noise tests and simulations used here)
- Method: (cite: Richards2011) (OVRO 40 m 15 GHz monitoring program)
- Method: (cite: 2014MNRAS.445..437M) (Cross-correlation method for WISE versus OVRO)
- Companion: (cite: 2024arXiv240802645D) (Another strong SMBHB candidate (PKS J0805-0111) from the OVRO light curve)
- Related: OVRO 40 m blazar monitoring program
- Related: MOJAVE
- Related: Zwicky Transient Facility
- Related: Fermi light curve repository

## Checks

```json
{
 "quotes": 78,
 "quotes_ok": 78,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.0.00001.CAL"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 101,
  "stated": 56,
  "rate": 0.554
 },
 "evidence_ok": true
}
```
