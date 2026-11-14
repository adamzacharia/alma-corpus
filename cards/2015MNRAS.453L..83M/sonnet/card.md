# ALMA and Herschel reveal that X-ray-selected AGN and main-sequence galaxies have different star formation rate distributions

`2015MNRAS.453L..83M` | Monthly Notices of the Royal Astronomical Society 2015 | first author: Mullaney, J. R. | arXiv: 1506.05459 | DOI: 10.1093/mnrasl/slv110

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars, high_z_galaxies
- Question: Do X-ray selected AGN hosts have the same SFR distribution relative to the main sequence as normal star-forming galaxies?  
  > "we test this by combining deep *Herschel* and ALMA observations to instead constrain the *distribution* of host galaxy SFRs of a sample of X-ray selected AGNs" (Introduction)
- Target **X-ray AGN in 4 Ms CDF-S (high-z, 24 ALMA targets)**: coordinates _not stated_; z/distance 1.5<=z<4 (high-z); 0.5<=z<1.5 (low-z sample)  
  > "The high-*z* sample were all selected from the 4 Ms *Chandra* Deep Field South (hereafter, CDF-S) survey catalogue described in (cite: Xue11) with updated redshifts from (cite: Hsu14)" (2 Sample selection); distance from spec-z or phot-z from Xue11 with updates from Hsu14  
  > "The high-*z* sample were all selected from the 4 Ms *Chandra* Deep Field South (hereafter, CDF-S) survey catalogue described in (cite: Xue11) with updated redshifts from (cite: Hsu14)" (2 Sample selection)

## Data provenance

- ALMA projects: 2012.1.00869.S
- bands: Band 7 (~850 um observed)  
  > "All 24 of our ALMA targets were observed with ALMA Band-7 (i.e., observed-frame $\sim850$ ${\rm \mu m}$)" (3 ALMA observations and data analysis)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: longest baseline 1.3 km  
  > "during November, 2013, with a longest baseline of 1.3 km" (3 ALMA observations and data analysis)
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: RMS limits of 200, 125 and 90 uJy for three target groups  
  > "This corresponds to RMS flux limits of 200 ${\rm \mu Jy}$, 125 ${\rm \mu Jy}$ and 90 ${\rm \mu Jy}$ for the three groups." (3 ALMA observations and data analysis)
- time on source: _not stated_
- observing dates: November 2013  
  > "during November, 2013, with a longest baseline of 1.3 km" (3 ALMA observations and data analysis)
- pi or archival as stated: _not stated_
- Other facility **Herschel (PEP + GOODS-Herschel 160 um)**: 160 um fluxes and 3 sigma upper limits for SFRs  
  > "All other *Herschel* fluxes and $3\sigma$ upper limits (including for the twelve *Herschel*-undetected AGNs not targeted by ALMA) are also taken from the combined PEP$+$GOODS-*Herschel* dataset." (2 Sample selection)
- Other facility **Chandra Deep Fields**: X-ray AGN selection and positions  
  > "The high-*z* sample were all selected from the 4 Ms *Chandra* Deep Field South (hereafter, CDF-S) survey catalogue" (2 Sample selection)
- External data: CDF-S X-ray catalogue  
  > "4 Ms *Chandra* Deep Field South (hereafter, CDF-S) survey catalogue described in (cite: Xue11)" (2 Sample selection) [from (cite: Xue11)]
- External data: Updated redshifts for CDF-S  
  > "with updated redshifts from (cite: Hsu14)" (2 Sample selection) [from (cite: Hsu14)]
- External data: MS log-normal parameters and MS SFR relation (Eqn 9)  
  > "${\rm SFR_{MS}}$ is computed using Eqn. 9 of (cite: Schreiber15)" (3 ALMA observations and data analysis) [from (cite: Schreiber15)]
- External data: Average MS infrared SEDs  
  > "the average infrared SEDs of MS galaxies described in (cite: Bethermin15)" (3 ALMA observations and data analysis) [from (cite: Bethermin15)]
- External data: CDF-N low-z sample redshifts and stellar masses  
  > "adopting the same redshifts and $M_{\ast}$ as (cite: Mullaney12)" (2 Sample selection) [from (cite: Alexander03; Mullaney12)]

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

- Stellar masses derived following Santini12  
  > "which we derive following (cite: Santini12)" (2 Sample selection) [from (cite: Santini12)]
- SFR from L_IR using Kennicutt98 Eqn 4 with Chabrier IMF  
  > "SFRs are derived from $L_{\rm IR}$ using Eqn. 4 from (cite: Kennicutt98), but adopting a Chabrier IMF." (3 ALMA observations and data analysis) [from (cite: Kennicutt98)]
- Log-normal form for R_MS distribution  
  > "we instead *assume* the same log-normal form for the AGN $R_{\rm MS}$ distribution as found for MS galaxies" (4.2 Parameterising an X-ray AGN SFR distribution) [from (cite: Rodighiero11; Sargent12; Schreiber15)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration/imaging procedure (pipeline vs manual, weighting, cell, beam)
- Archive reduced products or how visibilities were calibrated for GILDAS uv_fit
- Source positions/priors used in uv_fit and which sources were point vs Gaussian
- Prior forms and widths, chain length and convergence criteria for the hierarchical MCMC
- How upper limits and L_IR uncertainties enter the likelihood
- Herschel stacking procedure and flux values
- Per-source table of redshifts, masses, fluxes

## Analysis recipe

1. **select AGN samples**: X-ray AGN with LX>1e42, reliable z, M*>2e10 Msun, within 6' of aim point (high-z)  
  > "we only consider those sources with $L_{\rm X}$$>10^{42}$ ${\rm ergs~s^{-1}}$ and reliable redshifts" (2 Sample selection)
   - fitting: _not stated_
   - validation: _not stated_
2. **measure ALMA 850um continuum fluxes**: uv-plane fitting with point or circular Gaussian profiles  
  > "ALMA continuum fluxes were measured using `uv_fit` of GILDAS v.apr14c, adopting point source profiles for two unresolved sources and circular Gaussian profiles for the other five detected targets." (3 ALMA observations and data analysis)
   - software: GILDAS
   - fitting: _not stated_
   - validation: _not stated_
3. **convert fluxes to L_IR and SFR**: MS-galaxy average IR SEDs (Bethermin15, Draine07 templates), then Kennicutt98 relation; R_MS=SFR/SFR_MS  
  > "converted to 8-1000 ${\rm \mu m}$ infrared luminosities (hereafter, $L_{\rm IR}$) using our adopted redshifts (see §2)" (3 ALMA observations and data analysis)
   - assumption: L_IR accurate to ±0.3 dex from SED template range, included in analysis; Chabrier IMF  
  > "we estimate that the corresponding $L_{\rm IR}$ are accurate to within $\pm0.3$ dex, which we factor into our analyses" (3 ALMA observations and data analysis)
   - fitting: _not stated_
   - validation: Conclusions unchanged with Chary01 or Arp220 SEDs; ALMA and Herschel SFRs consistent for four sources detected by both  
  > "our conclusions do not change if we instead use either the (cite: Chary01) SEDs or a starburst SED (i.e., Arp220)" (3 ALMA observations and data analysis)
4. **infer log-normal R_MS distribution parameters**: Hierarchical Bayesian model with upper limits and uncertainties, assuming log-normal  
  > "We adopt a hierarchical Bayesian framework to determine the best-fit parameters (i.e., $\mu$ and $\sigma$) for our assumed log-normal distributions" (4.2 Parameterising an X-ray AGN SFR distribution)
   - fitting: Gibbs sampling and Metropolis-Hastings MCMC; weak priors  
  > "using Gibbs sampling and the Metropolis-Hastings MCMC algorithm to randomly sample their posterior probability distributions" (4.2 Parameterising an X-ray AGN SFR distribution)
   - validation: Prior centring has no significant effect  
  > "noting that the centring of these priors (within reasonable limits) has no significant effect on our results" (4.2 Parameterising an X-ray AGN SFR distribution)
5. **compute linear-mean R_MS and compare with stacking**: Monte-Carlo sampling of mu and sigma posteriors to compute linear mean  
  > "calculating the linear mean of our log-normal distributions, taking a Monte-Carlo approach to sample the $\mu$ and $\sigma$ PDs" (5 Interpretation)
   - fitting: _not stated_
   - validation: Compared to mean-stacked Herschel 160 um results  
  > "broadly consistent with the linear means calculated by mean-stacking *Herschel* 160 ${\rm \mu m}$ maps at the positions of our AGN" (5 Interpretation)

## Software

- **GILDAS** apr14c: uv_fit continuum flux measurements  
  > "ALMA continuum fluxes were measured using `uv_fit` of GILDAS v.apr14c" (3 ALMA observations and data analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA detections among high-z targets | 7 of 24 | not stated | sources | 2 | only seven (i.e., $\approx29$ per cent) of the 24 ALMA-targeted AGNs in our high-*z* sample are detected at $>3\sigma$ at 850 ${\rm \mu m}$ |
| Combined AGN log-normal mu | -0.369 | +0.065/-0.080 | dex | 4 | Combined AGN sample / $-0.369^{+0.065}_{-0.080}$ / $0.560^{+0.087}_{-0.065}$ |
| Combined AGN log-normal sigma | 0.560 | +0.087/-0.065 | dex | 4 | Combined AGN sample / $-0.369^{+0.065}_{-0.080}$ / $0.560^{+0.087}_{-0.065}$ |
| Low-z AGN mu, sigma | mu=-0.378, sigma=0.568 | mu +0.068/-0.079; sigma +0.082/-0.062 | dex | 4 | Low-$z$ AGN sample / $-0.378^{+0.068}_{-0.079}$ / $0.568^{+0.082}_{-0.062}$ |
| High-z AGN mu, sigma | mu=-0.38, sigma=0.59 | mu +0.12/-0.16; sigma +0.15/-0.10 | dex | 4 | High-$z$ AGN sample / $-0.38^{+0.12}_{-0.16}$ / $0.59^{+0.15}_{-0.10}$ |
| Fraction of combined AGN with R_MS<0.5 | 34 to 55 per cent (54-88 of 159) | range from upper limits | per cent | 3 | We find that 54 to 88 (range due to upper limits) of the 159 AGNs (i.e., $\approx$34 to $\approx$55 per cent) in our combined |
| Linear-mean <R_MS> low-z | 0.99 | +0.23/-0.16 | dimensionless | 5 | $0.99^{+0.23}_{-0.16}$ and $1.09^{+0.47}_{-0.25}$ for our low-*z* and high-*z* samples, respectively |
| Linear-mean <R_MS> high-z | 1.09 | +0.47/-0.25 | dimensionless | 5 | $0.99^{+0.23}_{-0.16}$ and $1.09^{+0.47}_{-0.25}$ for our low-*z* and high-*z* samples, respectively |

## Qualitative findings

- AGN SFR distribution shows no evolution with redshift within 1 sigma  
  > "with the modes and variances of the log-normal distributions describing our low-*z* and high-*z* samples being consistent to within 1$\sigma$" (4.2 Parameterising an X-ray AGN SFR distribution)

## Claim tuples

- H: X-ray AGN hosts follow the MS R_MS distribution | E: Compare R_MS fractions and fitted log-normals of ALMA+Herschel AGN sample to MS galaxies | R: AGN distribution about twice as broad and peaks ~0.4 dex lower | F: AGN and MS SFR distributions differ significantly | **supported**
- H: Stacking results (AGN SFR consistent with MS) conflict with the distribution result | E: Compute linear mean of fitted log-normals | R: Linear means ~1, consistent with stacking | F: Linear mean is biased by bright outliers and not a reliable typical SFR | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Small samples and many non-detections prevent direct determination of the distribution, so a log-normal form is assumed for comparison  
  > "Our relatively small sample sizes, combined with the large fraction of non-detections prevents us from determining the AGN $R_{\rm MS}$ distribution directly." (4.2 Parameterising an X-ray AGN SFR distribution)
- How they decided it was enough: _not stated_
- Limitation (authors): Log-normal is not a literal description of the true AGN distribution  
  > "is not to be taken as a literal description of the true AGN $R_{\rm MS}$ distribution" (4.2 Parameterising an X-ray AGN SFR distribution)
- Caveat (inferred, ours): Single-template SED assumption with ±0.3 dex uncertainty; no full SED fitting
- Caveat (inferred, ours): Results depend on assumed log-normal form
- Caveat (inferred, ours): Only 7/24 ALMA detections, so heavily upper-limit driven
- Caveat (inferred, ours): Possible AGN contribution to sub-mm not discussed

## Reproducibility

- Data public (paper): ALMA data acknowledged by project code  
  > "This paper makes use of ALMA data: ADS/JAO.ALMA#2012.1.00869.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Per-source flux and mass tables
- Missing: MCMC prior and implementation details
- Missing: Herschel maps processing and stacking details
- Data volume (inferred): ~10-50 GB raw for 24 Band 7 targets
- Score (inferred): 3/5, Public data and clear overall approach, but calibration, uv_fit details, and MCMC priors are missing.
- Rediscovery candidate: no, Recipe incomplete (priors, per-source inputs, Herschel data) though data are public.

## Links

- Method: (cite: Schreiber15) (MS SFR relation and log-normal distribution)
- Method: (cite: Bethermin15) (MS SED templates)
- Companion: (cite: Mullaney12) (low-z sample redshifts and masses)
- Related: 4 Ms Chandra Deep Field South
- Related: GOODS-Herschel
- Related: PEP
- Related: ALMA Cycle 2 follow-up (PI: Alexander)

## Checks

```json
{
 "quotes": 44,
 "quotes_ok": 44,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 32,
  "rate": 0.444
 },
 "evidence_ok": true
}
```
