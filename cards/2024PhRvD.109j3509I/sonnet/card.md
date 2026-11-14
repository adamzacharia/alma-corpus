# Probing warm and mixed dark matter models using lensing shift power spectrum

`2024PhRvD.109j3509I` | Physical Review D 2024 | first author: Inoue, Kaiki Taro | arXiv: 2312.17536 | DOI: 10.1103/PhysRevD.109.103509

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: other, cosmology
- Question: Can the lensing shift power spectrum measured with ALMA toward MG J0414+0534 constrain warm dark matter mass and the WDM fraction in mixed dark matter models?  
  > "we place constraints on the mass of warm dark matter (WDM) particles $m_{\rm WDM}$ and their fraction in a mixed dark matter (MDM) model $r_{\rm WDM}$" (abstract)
- Target **MG J0414+0534**: coordinates _not stated_; z/distance z_S=2.639, z_L=0.9584  
  > "The redshifts of the source and the primary lens (early type galaxy) of MG J0414+0534 are $z_S=2.639$ (cite: lawrence1995) and $z_L=0.9584$ (cite: tonry1999), respectively." (Lensing shift power spectrum); distance from lawrence1995; tonry1999  
  > "The redshifts of the source and the primary lens (early type galaxy) of MG J0414+0534 are $z_S=2.639$ (cite: lawrence1995) and $z_L=0.9584$ (cite: tonry1999), respectively." (Lensing shift power spectrum)

## Data provenance

- ALMA projects: 2013.1.01110.S, 2016.1.00281.S
- bands: _not stated_
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
- External data: Measured lensing shift power Delta_alpha=0.0081 at l~1.3e6 (L=3.6 arcsec) with sigma_obs=0.0006, N_mode=7  
  > "Observed lensing power spectrum $\Delta_\alpha\,[\mathrm{arcsec}]$ at $l \sim 1.3 \times 10^6$ with $L=3^{''}\!\!.6$ (cite: Inoue:2021dkv)." (Table 1) [from Inoue et al. (cite: Inoue:2021dkv)]
- External data: Cosmological parameters from Planck (H0=67.36, Omega_m h^2=0.143, Omega_b h^2=0.02237, sigma8=0.811)  
  > "which are derived from the Planck data (cite: Planck:2018vyg)." (Lensing shift power spectrum) [from (cite: Planck:2018vyg)]
- Simulation/model as data: Non-linear WDM and MDM power spectra from N-body-based fitting formulae (inoue-etal2015; Kamada:2016vsc) on halofit CDM (Takahashi:2012em)  
  > "we adopt a fitting formula, constructed from N-body simulations to compute non-linear matter power spectra in WDM and MDM models" (Matter power spectra in warm dark matter and mixed dark matter models)

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

- ALMA data reduction and lensing shift power spectrum measurement taken from earlier paper  
  > "which was measured using ALMA (Atacama Large Milllimeter/submillimeter Array) observations of the quadruply lensed quasar MG J0414+0534 (cite: Inoue:2021dkv)" (Lensing shift power spectrum) [from (cite: Inoue:2021dkv)]
- kmax=1e5 h/Mpc chosen to match observed small-scale structures  
  > "which corresponds to the observed small scale structures in the quasar host galaxy (cite: Inoue:2021dkv)" (Lensing shift power spectrum) [from (cite: Inoue:2021dkv)]

### Not stated but needed to reproduce (our reading)

- Linear power spectrum/transfer function normalization and primordial spectral index details beyond the listed parameters
- Exact chi2 minimization/profiling procedure over kmin and the delta-chi2 thresholds
- Mock-data central values and bin definitions for future forecasts beyond stated range
- Numerical integration settings

## Analysis recipe

1. **Compute non-linear WDM/MDM matter power spectra**: Scale halofit CDM spectrum by WDM and MDM fitting-function suppression  
  > "Given a fitting function of matter power spectrum in the CDM model, which is denoted as $P_{\rm CDM} (k,z)$, the corresponding WDM non-linear power spectrum $P_\mathrm{WDM}(k,z)$ is given by (cite: inoue-etal2015)" (Matter power spectra in warm dark matter and mixed dark matter models)
   - assumption: Baryonic effects sufficiently small  
  > "assuming that baryonic effects are sufficiently small" (Matter power spectra in warm dark matter and mixed dark matter models)
   - fitting: _not stated_
   - validation: _not stated_
2. **Predict lensing shift power spectrum from line-of-sight halos**: Integrate matter power spectrum along line of sight with kernel Q/g and kmin cutoff treated as free parameter  
  > "we choose $k_\mathrm{min}$ such that the data gives a best fit when $k_\mathrm{min}$ is varied." (Lensing shift power spectrum)
   - parameter: kmax=1e5 h/Mpc; l~1.3e6 only  
  > "we use only the lensing shift power at the angular wave number of $l \sim 1.3 \times 10^6$ with $L=3^{''}\!\!.6$" (Lensing shift power spectrum)
   - assumption: Subhalo contribution neglected (expected subdominant); coupling effects neglected  
  > "we neglect contribution from subhalos that reside in the halo of the primary lens" (Lensing shift power spectrum)
   - fitting: _not stated_
   - validation: _not stated_
3. **Constrain m_WDM and r_WDM via chi2**: chi2 comparing theory with observed power, errors from obs, cosmic variance (Delta/(2 sqrt(7))) and 10% mass-sheet degeneracy  
  > "we evaluate the $\chi^2$ defined as" (Constraints on WDM and MDM)
   - assumption: 10% error from mass-sheet degeneracy  
  > "We assume a conservative $10\,\%$ error due to the ambiguity in the mass profile of the primary lens of MG J0414+0534" (Lensing shift power spectrum)
   - fitting: chi2 minimization, 2 sigma bounds  
  > "we evaluate the $\chi^2$ defined as" (Constraints on WDM and MDM)
   - validation: _not stated_
4. **Forecast future constraints**: Mock 5 log-spaced bins in 3.1<=l/1e6<=8.0 with CDM fiducial; errors scaled by 1/sqrt(N_L), N_L=30 and 100  
  > "we assume a measurement of $\Delta_\alpha$ with five bins for the range of $3.1\leq l/10^6\leq8.0$, which are equally spaced on a logarithmic scale" (Future expected constraints)
   - assumption: Systematic errors negligible; no inter-bin correlations  
  > "We assume that the correlations between the errors in different bins are negligible." (Future expected constraints)
   - fitting: _not stated_
   - validation: _not stated_

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| WDM mass lower bound (current) | 0.19 | 95% C.L. | keV | 3 | m_{\rm WDM} \gtrsim 0.19~{\rm keV} \qquad (95~\%~{\rm C.L.}) |
| r_WDM upper bound at m_WDM=0.1 keV | 0.72 | not stated | dimensionless | 3 | in the case of $m_{\rm WDM} = 0.1~{\rm keV}$, as $r_{\rm WDM} \lesssim 0.72$ |
| Projected m_WDM bound, N_L=30 pure WDM | 6.3 | 2 sigma | keV | 4 | / $30$ / $\gtrsim$ 6.3 keV / $\gtrsim$ 4.8 keV / $\gtrsim$ 3.6 keV / |
| Projected m_WDM bound, N_L=100 pure WDM | 9.0 | 2 sigma | keV | 4 | / $100$ / $\gtrsim$ 9.0 keV / $\gtrsim$ 7.0 keV / $\gtrsim$ 5.3 keV / |

## Qualitative findings

- CDM preferred with LOS halos farther from the primary lens than in WDM/MDM models  
  > "our investigation of MG J0414+0534 indicates a preference for the CDM model with LOS halos residing farther from the primary lens compared to WDM and MDM models" (Conclusion and discussion)

## Claim tuples

- H: Does the single-lens shift power spectrum constrain WDM mass? | E: chi2 comparison of predicted and observed shift power at l~1.3e6 | R: m_WDM >~ 0.19 keV (95% C.L.) | F: Constraint is weaker than existing ones but demonstrates the method | **supported**
- H: Can more lens systems greatly tighten constraints? | E: Mock data with N_L=30,100 | R: m_WDM >~ 6.3 and 9.0 keV | F: Method is promising for WDM and MDM | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Convergence and potential power spectra not combined, to avoid systematics  
  > "We exclusively rely on the directly measurable astrometric shift power spectrum, which is less susceptible to systematic errors inherent in observations." (Conclusion and discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Subhalo contributions and coupling between primary and secondary deflections neglected  
  > "Additionally, we omitted contributions from subhalos within the halo of the primary lens in our analysis." (Conclusion and discussion)
- Caveat (inferred, ours): Single lens, single angular bin; kmin fitted as free parameter
- Caveat (inferred, ours): Ignoring subhalos could bias constraints
- Caveat (inferred, ours): Future forecasts assume negligible systematics and identical per-lens power

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Original measurement pipeline resides in Inoue et al. 2023
- Missing: No code released
- Data volume (inferred): none needed; uses published table value
- Score (inferred): 4/5, Theory analysis with explicit formulae and one tabulated data point; reproducible from the paper alone, ALMA reduction not required.
- Rediscovery candidate: no, The ALMA analysis is inherited from another paper; this paper's results come from a theory calculation on a tabulated value.

## Links

- Method: (cite: Inoue:2021dkv) (Measurement of the lensing shift power spectrum)
- Method: (cite: Takahashi:2012em) (Halofit nonlinear power spectrum)
- Companion: (cite: Inoue:2021dkv) (ALMA measurement of lensing power spectra toward MG J0414+0534)

## Checks

```json
{
 "quotes": 30,
 "quotes_ok": 30,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 21,
  "rate": 0.309
 },
 "evidence_ok": true
}
```
