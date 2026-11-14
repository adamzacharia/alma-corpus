# Scaling Relations Associated with Millimeter Continuum Sizes in Protoplanetary Disks

`2018ApJ...865..157A` | The Astrophysical Journal 2018 | first author: Andrews, Sean M. | arXiv: 1808.10510 | DOI: 10.3847/1538-4357/aadd9f

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks
- Question: How do mm continuum sizes and luminosities of protoplanetary disks scale with each other and with stellar host mass, luminosity and accretion rate, and what do these relations imply?  
  > "we aim to alleviate some potential sample biases and re-examine the mm continuum size–luminosity relationship for a large and well-defined collection of disks in the Lupus star-forming region" (Introduction)
- Target **Lupus disk sample (56 disks)**: coordinates _not stated_; z/distance ~136-175 pc (Table 4); Gaia DR2 parallax-based  
  > "Accounting for these exclusions, the final sample includes 56 disks." (Sample); "Trigonometric parallax ($\varpi$) measurements were collected from the *Gaia* DR2 catalog (cite: gaia_dr2) for all but 4 targets in the Lupus sample." (4.1 Modeling Surface Brightness Profiles); distance from Gaia DR2 parallaxes with zero-point correction, Astraatmadja & Bailer-Jones posteriors  
  > "Accounting for these exclusions, the final sample includes 56 disks." (Sample); "Trigonometric parallax ($\varpi$) measurements were collected from the *Gaia* DR2 catalog (cite: gaia_dr2) for all but 4 targets in the Lupus sample." (4.1 Modeling Surface Brightness Profiles)
- Target **SMA sample from Tripathi et al. 2017 (49 disks, IM Lup overlaps)**: coordinates _not stated_; z/distance ~60-309 pc (Table 5)  
  > "Noting the overlap of one target (IM Lup) between the Lupus and SMA samples, the joint sample has a total count of 105 unique disk targets." (Sample); distance from Gaia DR2  
  > "Noting the overlap of one target (IM Lup) between the Lupus and SMA samples, the joint sample has a total count of 105 unique disk targets." (Sample)

## Data provenance

- ALMA projects: 2013.1.00220.S, 2013.1.00694.S, 2012.1.00761.S, 2013.1.00374.S
- bands: Band 7 (mean 335 GHz, 895 um) for the Lupus survey  
  > "this program employed the ALMA Band 7 receivers to observe the dust continuum emission at a mean frequency of 335 GHz (895 $\mu$m)" (2 Data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: ~5 GHz in 3 spectral windows averaged to 256 MHz pseudo-channels  
  > "The total continuum bandwidth in those windows is $\sim$5 GHz." (2 Data)
- arrays: _not stated_
- configurations: _not stated_
- baselines: 21 to 784 m (Lupus survey)  
  > "with 41 and 37 of the 12 m antennas arranged to span baselines of 21 to 784 m" (2 Data)
- angular resolution: ~0.13 arcsec naturally weighted  
  > "a width ($\sigma = 0.13\ensuremath{''}$) corresponding to the (naturally weighted) data resolution" (4.2 Modifications for Special Cases)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 48-120 s per target (Lupus snapshots)  
  > "The observations were “snapshots", with total integration times of 48–120 s per target." (2 Data)
- observing dates: 2015 June 14 and 15 (Lupus survey)  
  > "The vast majority of the ALMA data used here were obtained on 2015 June 14 and 15" (2 Data)
- pi or archival as stated: archival ALMA data  
  > "We have used archival ALMA and SMA observations to measure the sizes ($R_{\rm eff}$) and luminosities ($L_{\rm mm}$)" (6 Discussion)
- Other facility **SMA**: Archival 340 GHz continuum survey of 49 disks (Tripathi et al. 2017)  
  > "Building on the previous SMA survey, we infer surface brightness profiles using a simple model of the observed visibilities" (abstract)
- Other facility **Gaia DR2**: Parallaxes for distances  
  > "Trigonometric parallax ($\varpi$) measurements were collected from the *Gaia* DR2 catalog (cite: gaia_dr2)" (4.1 Modeling Surface Brightness Profiles)
- Other facility **VLT X-shooter**: Stellar and accretion parameters (via Alcala et al. 2017)  
  > "We primarily use the parameters compiled by (cite: alcala17) as a base set of values" (4.3 Stellar and Accretion Parameter Estimation)
- External data: SMA sample surface-brightness model parameters  
  > "For the SMA sample, we adopted the parameters inferred by (cite: tripathi17)" (4.1 Modeling Surface Brightness Profiles) [from (cite: tripathi17)]
- External data: Teff, L*, Lacc for Lupus targets  
  > "In their Table A.2, (cite: alcala17) list effective temperatures ($T_{\rm eff}$) and stellar luminosities ($L_\ast$)" (4.3 Stellar and Accretion Parameter Estimation) [from (cite: alcala17)]
- External data: Gaia DR2 parallaxes and 30 uas zero-point shift  
  > "we corrected the catalog parallaxes for the known 30 $\mu$as systematic shift with respect to the quasar reference frame" (4.1 Modeling Surface Brightness Profiles) [from (cite: gaia_dr2; lindegren18)]
- Simulation/model as data: MIST pre-main sequence evolutionary models used for masses and ages  
  > "We prefer here the MIST evolutionary models (cite: choi16) as the basis for that inference" (4.3 Stellar and Accretion Parameter Estimation)

## Processing

### Calibration

- pipeline or manual: Pipeline-calibrated by NRAO staff  
  > "The raw data were pipeline-calibrated by NRAO staff." (2 Data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: Normal factor s with mean 1, sd 0.1 applied to L_mm  
  > "$s$ values are drawn from a normal distribution with a mean of unity and a standard deviation of 0.1" (4.1 Modeling Surface Brightness Profiles)
- self calibration: Single phase-only self-cal (30 s) for brighter targets, ~20% peak S/N gain  
  > "For brighter targets, a single iteration of phase-only self-calibration (on a 30 s interval) was employed, which enhanced the peak S/N in the resulting emission maps by $\sim$20%." (2 Data)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs robust=0 image for HK Lup illustration  
  > "A close examination of a continuum image made to enhance the resolution (with Briggs robust=0)" (4.2 Modifications for Special Cases)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Narrowband line windows removed; spectral lines excised before averaging  
  > "We then removed two narrowband spectral windows (containing spectral lines at high velocity resolution)" (2 Data)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Lupus observations and calibration details  
  > "The observations and calibration procedure were described in detail by (cite: ansdell16)." (2 Data) [from (cite: ansdell16)]
- Calibration of IM Lup, Sz 91, GQ Lup data  
  > "These data and their calibration were already presented by (cite: cleeves16), (cite: tsukagoshi17), and (cite: macgregor17), respectively." (2 Data) [from (cite: cleeves16), (cite: tsukagoshi17), (cite: macgregor17)]
- Visibility modeling procedure with Nuker profiles and priors  
  > "To measure luminosities and sizes for the continuum emission, we follow the procedure described in detail by (cite: tripathi17)." (4.1 Modeling Surface Brightness Profiles); "Adopting the same practical and conservative priors advocated by (cite: tripathi17)" (4.1 Modeling Surface Brightness Profiles) [from (cite: tripathi17)]
- Accretion rates computed following Alcala et al. 2017  
  > "Accretion rates were calculated following (cite: alcala17), based on their estimates of the accretion luminosities" (4.3 Stellar and Accretion Parameter Estimation) [from (cite: alcala17)]
- Regression via Kelly 2007 mixture model  
  > "following the general mixture model formulation described in detail by (cite: kelly07)" (5.3 Inferred Scaling Relations) [from (cite: kelly07)]

### Not stated but needed to reproduce (our reading)

- Exact prior ranges for the Nuker parameters (deferred to Tripathi et al. 2017)
- Visibility weighting/binning and any uv-range cuts used in the MCMC
- emcee walkers, steps, burn-in and convergence criteria
- Line-free channels used for continuum visibilities
- Exact CASA version
- Treatment of ALMA flux scale beyond the 10% factor
- Details of the manual tuning of the thick/thin population models
- Visibility data set preparation for multiple-pointing targets beyond CLEAN-component subtraction

## Analysis recipe

1. **Assemble and prepare ALMA continuum visibilities**: Use archival pipeline-calibrated Band 7 data, drop line windows, average to pseudo-channels, phase-only self-cal for bright targets  
  > "We then removed two narrowband spectral windows (containing spectral lines at high velocity resolution) and then spectrally averaged the data in 3 other spectral windows to 256 MHz-wide pseudo-channels." (2 Data)
   - software: CASA
   - parameter: 256 MHz pseudo-channels, 30 s self-cal interval  
  > "spectrally averaged the data in 3 other spectral windows to 256 MHz-wide pseudo-channels" (2 Data)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit visibility models to derive F_nu, R_eff, L_mm**: Gaussian likelihood comparing observed visibilities with Hankel transforms of Nuker profiles with 9 parameters; effective radius encloses 68% of flux  
  > "We adopt a Gaussian likelihood that compares the observed complex visibilities and Hankel transforms of “Nuker" surface brightness profiles (cite: lauer95)" (4.1 Modeling Surface Brightness Profiles)
   - software: emcee
   - parameter: x = 0.68 encircled luminosity fraction  
  > "such that $f_\nu(\varrho_{\rm eff}) = x F_\nu$; we adopt $x = 0.68$" (4.1 Modeling Surface Brightness Profiles)
   - parameter: L_mm = F_nu (d/140)^2 s  
  > "$L_{\rm mm} = F_\nu \times (d/140)^2 \times s$" (4.1 Modeling Surface Brightness Profiles)
   - assumption: Distances from Gaia DR2 with uniform d prior  
  > "Posterior draws for the distance were made following (cite: astraatmadja16), conditioned on parallax measurements and assuming an uniform $d$ prior." (4.1 Modeling Surface Brightness Profiles)
   - fitting: Affine-invariant ensemble MCMC (emcee) with Tripathi et al. priors; special-case modified priors for 10 faint targets, Sz 91, and a depression model for HK Lup  
  > "we modified the $\varrho_t$ prior for these systems, employing a Gaussian prior with a mean of zero and a width ($\sigma = 0.13\ensuremath{''}$)" (4.2 Modifications for Special Cases)
   - validation: Observed visibility profiles compared with synthetic data from posterior draws  
  > "Figure [\[fig:visgallery\]](#fig:visgallery) compares the observed visibilities with synthetic data generated from random draws from the parameter posterior distributions." (5.1 Surface Brightness Modeling Results)
3. **Derive stellar masses, ages, accretion rates**: Convert Teff and L* to log posteriors rescaled to adopted d; sample M*, age from MIST tracks; Lacc log-normal with 0.25 dex  
  > "adopt the approach advocated by (cite: jorgensen05), and implemented in the `ScottiePippen` software package (cite: czekala16), to sample the joint posterior distribution of {$M_\ast$, $\tau_\ast$}" (4.3 Stellar and Accretion Parameter Estimation)
   - software: ScottiePippen
   - assumption: Teff and L* independent  
  > "we assume that $T_{\rm eff}$ and $L_\ast$ are independent" (4.3 Stellar and Accretion Parameter Estimation)
   - fitting: _not stated_
   - validation: Other evolutionary models gave no significant differences  
  > "The same analysis was performed for various other evolutionary models (cite: siess00; dotter08; tognelli11; baraffe15) and no significant differences were identified." (4.3 Stellar and Accretion Parameter Estimation)
4. **Regress scaling relations**: Linear regression in log space with intrinsic scatter, errors and censoring, via linmix  
  > "The (cite: kelly07) methodology infers posterior samples on {$\mathcal{A}$, $\mathcal{B}$, $\sigma$} conditioned on {$\mathsf{x}$, $\mathsf{y}$}, their covariance matrices, and any associated censoring (limits)." (5.3 Inferred Scaling Relations)
   - software: linmix
   - assumption: 2D posteriors approximated as symmetric elliptical Gaussians  
  > "approximating the two-dimensional posteriors for any {$\mathsf{x}$, $\mathsf{y}$} as (symmetric, elliptical) Gaussian distributions" (5.3 Inferred Scaling Relations)
   - fitting: _not stated_
   - validation: Slope insensitive to enclosed fraction definition (50-95%)  
  > "we find that the slope of this relationship is identical regardless of how $R_{\rm eff}$ is defined." (5.3.1 Size–Luminosity Relation)
5. **Interpret with optically thick and thin population models**: Analytic power-law Td and tau profiles with outer radius R_o, manually tuned population models  
  > "This host population model was manually designed and tuned as described in Appendix [9]" (6 Discussion)
   - parameter: T0 = 30 K at r0 = 10 au for L*=Lsun  
  > "with a fiducial normalization of $T_0 = 30$ K at $r_0 = 10$ au for $L_\ast = L_\odot$" (6 Discussion)
   - assumption: Distinct outer boundary R_o; Td ∝ L*^0.25 r^-q  
  > "The first is that the continuum emission distribution has a distinct outer boundary, $R_o$." (6 Discussion)
   - fitting: _not stated_
   - validation: Compared model populations with observed multi-dimensional relationships  
  > "The mean behavior in this multi-dimensional parameter-space can be explained well with three key assumptions" (6.1 Optically Thick Scenario)

## Software

- **CASA** : Listed in software; data handling  
  > "`CASA` (cite: mcmullin07)" (Software)
- **emcee** : MCMC sampling of visibility models  
  > "we sample the posterior distribution of the model parameters conditioned on the data using `emcee` (cite: foreman-mackey13)" (4.1 Modeling Surface Brightness Profiles)
- **ScottiePippen** : Sample mass and age posteriors from H-R diagram  
  > "implemented in the `ScottiePippen` software package (cite: czekala16)" (4.3 Stellar and Accretion Parameter Estimation)
- **linmix** : Linear regression with scatter and censoring  
  > "We use the same algorithms, but in software modified for `python` by J. Meyers" (5.3 Inferred Scaling Relations)
- **corner** : Listed in software  
  > "`corner` (cite: corner)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Size-luminosity slope B (joint) | 0.49 | +0.05/-0.03 | dimensionless | 4 | / $\log{L_{\rm mm}/{\rm Jy}}$ / $\log{R_{\rm eff}/{\rm au}}$ / joint / $^{+0.06}_{-0.03}$ / 0.49 $^{+0.05}_{-0.03}$ / 0.20 $^{+0.02}_{-0.01}$ / 0.86 (0.76, 0.92) / |
| L_mm vs M* slope (joint) | 1.51 | +0.11/-0.16 | dimensionless | 4 | / $\log{M_\ast/M_\odot}$ / $\log{L_{\rm mm}/{\rm Jy}}$ / joint / -0.69 $^{+0.08}_{-0.05}$ / 1.51 $^{+0.11}_{-0.16}$ / 0.46 $^{+0.04}_{-0.03}$ / 0.75 (0.61, 0.86) / |
| R_eff vs M* slope (joint) | 0.58 | +/-0.10 | dimensionless | 4 | / $\log{M_\ast/M_\odot}$ / $\log{R_{\rm eff}/{\rm au}}$ / joint / $^{+0.05}_{-0.04}$ / 0.58 $^{+0.10}_{-0.10}$ / 0.30 $^{+0.03}_{-0.03}$ / 0.58 (0.35, 0.74) / |
| Mdot vs M* slope (joint) | 1.95 | +0.25/-0.32 | dimensionless | 4 | / $\log{M_\ast/M_\odot}$ / $\log{\dot{M}_\ast/M_\odot {\rm yr}^{-1}}$ / joint / $^{+0.1}_{-0.1}$ / 1.95 $^{+0.25}_{-0.32}$ / 0.84 $^{+0.11}_{-0.07}$ / 0.63 (0.40, 0.79) / |
| Optically thick filling factor | ~0.3 | permissible ~0.1-0.5 | dimensionless | 5 | The permissible range of $\mathcal{F}$ is $\sim$0.1–0.5 before the model scatter becomes considerably broader than is observed. |
| Temperature index q required | 0.57 | 0.08 | dimensionless | 5 | are reproduced when $q = 0.57\pm0.08$ |
| Transition disk L_mm-M* slope | 0.86 | 0.18 | dimensionless | 4 | the transition disks alone have a much lower scaling index ($\mathcal{B} = 0.86\pm0.18$; a difference at the 3 $\sigma$ level) |
| Median Tb at 40 au | ~5 | factor of two sd | K | 2 | The median $T_b$ at 40 au is $\sim$5 K, with a standard deviation of only a factor of two |

## Qualitative findings

- About 25% of the joint sample are transition disks with central depressions, similar to infrared surveys.  
  > "the total fraction of transition disks in the joint sample, $\sim$25%, is similar to what is found in infrared surveys" (5.1 Surface Brightness Modeling Results)

## Claim tuples

- H: Does the SMA size-luminosity relation hold for a larger, lower-luminosity Lupus sample? | E: Visibility modeling of Lupus ALMA data and regression on Lupus, SMA and joint samples | R: Slopes ~0.5 for all samples | F: L_mm scales linearly with emitting surface area | **supported**
- H: Do disk sizes correlate with host and accretion properties? | E: Regression of R_eff against M*, L*, Mdot | R: R_eff ∝ M*^0.6, L*^0.3, weaker correlations (rho~0.5-0.6) | F: New but weaker relations exist; larger disks around more massive, faster-accreting hosts | **supported**
- H: Can simple optically thick or thin models explain the multi-dimensional relations? | E: Population models with power-law Td, tau and R_o | R: Thick needs F~0.3 and R_o ∝ M*^0.7; thin needs uniform tau profile | F: Both can work, requiring sub-linear size-mass relation with ~0.2 dex scatter | **partially**

## Reasoning

- Why this data: Wanted a large, well-defined Lupus sample to reduce heterogeneity of the SMA sample  
  > "One challenge in linking the sizes with the other relevant parameters has been that the (cite: tripathi17) sample has a comparatively heterogeneous construction" (Introduction)
- Why this method: _not stated_
- Alternative: Colder disks (T0 ~10 K) to cure excess emission rejected as unrealistic; filling factor preferred  
  > "The first option alone is difficult to achieve for realistic radiation transfer calculations, so we prefer the second." (6.1 Optically Thick Scenario)
- How they decided it was enough: _not stated_
- Limitation (authors): Resolution insufficient to constrain depression in HK Lup; tentative values  
  > "These should be considered tentative values, since the data resolution is not really sufficient to do a proper evaluation of the depression properties" (4.2 Modifications for Special Cases)
- Limitation (authors): Lupus multiplicity not thoroughly vetted  
  > "The Lupus population has not been thoroughly vetted for multiplicity, particularly at sub-arcsecond separations." (Sample)
- Caveat (inferred, ours): Population models were manually tuned, not formally fit
- Caveat (inferred, ours): Joint sample combines clusters with different selection biases (SMA biased to massive hosts/transition disks)
- Caveat (inferred, ours): Unresolved structure limits optical depth interpretation
- Caveat (inferred, ours): Stellar parameters inherited from heterogeneous literature

## Reproducibility

- Data public (paper): Archival ALMA data used  
  > "We have used archival ALMA and SMA observations to measure the sizes ($R_{\rm eff}$) and luminosities ($L_{\rm mm}$)" (6 Discussion)
- Products in archive: _not stated_
- Missing: Tripathi et al. 2017 prior definitions and code
- Missing: MCMC settings
- Missing: Final population model tuning code
- Data volume (inferred): ~50-100 GB for ~100 Lupus snapshot measurement sets plus 3 other programs
- Score (inferred): 3/5, Data public and method clearly described but relies on Tripathi 2017 for priors and details; no code released.
- Rediscovery candidate: yes, Public data, numeric regression results, but recipe depends on cited earlier paper.

## Links

- Method: (cite: tripathi17) (Visibility modeling procedure, priors, effective size definition)
- Method: (cite: kelly07) (Regression method)
- Method: (cite: alcala17) (Stellar and accretion parameters)
- Companion: (cite: ansdell16) (Original Lupus ALMA survey)
- Related: ALMA Lupus snapshot survey
- Related: SMA disk survey of Tripathi et al. 2017

## Checks

```json
{
 "quotes": 77,
 "quotes_ok": 77,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 90,
  "stated": 58,
  "rate": 0.644
 },
 "evidence_ok": true
}
```
