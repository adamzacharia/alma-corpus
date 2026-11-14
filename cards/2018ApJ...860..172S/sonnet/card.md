# Cloud-scale Molecular Gas Properties in 15 Nearby Galaxies

`2018ApJ...860..172S` | The Astrophysical Journal 2018 | first author: Sun, Jiayi | arXiv: 1805.00937 | DOI: 10.3847/1538-4357/aac326

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: nearby_galaxies, milky_way_ism, star_formation
- Question: How do cloud-scale (45-120 pc) molecular gas velocity dispersion, surface density, virial parameter and turbulent pressure vary within and among 15 nearby galaxies?  
  > "We measure the velocity dispersion, $\sigma$, and surface density, $\Sigma$, of the molecular gas in nearby galaxies from CO spectral line cubes with spatial resolution $45$-$120$ pc" (abstract)
- Target **11 PHANGS-ALMA galaxies (NGC 628, 1672, 2835, 3351, 3627, 4254, 4303, 4321, 4535, 5068, 6744)**: coordinates _not stated_; z/distance 8.28-17.6 Mpc  
  > "NGC 628 | Sc-A | 9.0 | 6.5 | 2.1 | ALMA | CO(2-1) | 1.0 / 44 | 2.5 | 0.13" (Table 1); distance from Extragalactic Distance Database (Tully et al. 2009)  
  > "NGC 628 | Sc-A | 9.0 | 6.5 | 2.1 | ALMA | CO(2-1) | 1.0 / 44 | 2.5 | 0.13" (Table 1)
- Target **M51, M31, M33, Antennae (literature data)**: coordinates _not stated_; z/distance M51 8.39, M31 0.79, M33 0.92, Antennae 22.0 Mpc  
  > "M51 | Sbc-A | 8.39 | 21.0 | 7.7 | PdBI | CO(1-0) | 1.2 / 49 | 5.0 | 0.31" (Table 1); distance from Extragalactic Distance Database (Tully et al. 2009)  
  > "M51 | Sbc-A | 8.39 | 21.0 | 7.7 | PdBI | CO(1-0) | 1.2 / 49 | 5.0 | 0.31" (Table 1)

## Data provenance

- ALMA projects: 2011.0.00876.S, 2012.1.00650.S, 2015.1.00956.S
- bands: _not stated_
- frequencies and spectral setup: Channel width 2.5 km/s (5.0 km/s for M51 and Antennae; 2.6 for M33)  
  > "The channel width for most of these observations is $2.5$-$2.6$ km s$^{-1}$." (2 Data)
- continuum bandwidth: _not stated_
- arrays: ALMA 12-m, 7-m and total power for PHANGS targets  
  > "These targets were observed by ALMA in CO (2-1) using the 12-meter and 7-meter interferometric arrays as well as the total-power antennas." (2 Data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Native 0.6-1.7 arcsec (34-130 pc); convolved to 45-120 pc  
  > "NGC 4254 | Sc-A | 16.8 | 27.0 | 6.5 | ALMA | CO(2-1) | 1.6 / 130 | 2.5 | 0.06" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: 1 sigma channel rms 0.06-0.27 K at native resolution; ~0.5 K km/s integrated for PHANGS  
  > "the sensitivity of velocity-integrated intensity maps are typically ${\sim}0.5$ K km s$^{-1}$" (2 Data)
- time on source: _not stated_
- observing dates: First 11 PHANGS targets observed in 2016, ALMA Cycle 3  
  > "the first $11$ targets analyzed here were already observed in 2016 during ALMA’s Cycle 3" (2 Data)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (PHANGS, M33), 1-0 (M51, M31), 3-2 (Antennae) (not stated)
- Other facility **PdBI + IRAM 30m (PAWS)**: M51 CO(1-0) map  
  > "we include the PdBI Arcsecond Whirlpool Survey (PAWS) CO (1-0) map of M51" (2 Data)
- Other facility **CARMA + IRAM 30m**: M31 CO(1-0) survey  
  > "we use the CARMA CO (1-0) survey by A. Schruba et al. (in prep.)" (2 Data)
- Other facility **IRAM 30m**: M33 CO(2-1) survey  
  > "For M33, we use the IRAM 30-m CO (2-1) survey by (cite: Gratier_etal_2010) and (cite: Druard_etal_2014)." (2 Data)
- External data: Antennae ALMA CO(3-2) map  
  > "we include the ALMA CO (3-2) map of the interacting region of the Antennae galaxies presented by (cite: Whitmore_etal_2014)" (2 Data) [from (cite: Whitmore_etal_2014)]
- External data: Distances from Extragalactic Distance Database  
  > "Distance values are taken from the Extragalactic Distance Database (cite: Tully_etal_2009)." (Table 1) [from (cite: Tully_etal_2009)]
- External data: Galaxy stellar masses from S4G  
  > "*all other galaxies* - S$^4$G global stellar masses (cite: Sheth_etal_2010; Querejeta_etal_2015)." (Table 1) [from (cite: Sheth_etal_2010; Querejeta_etal_2015)]
- External data: Milky Way cloud catalog used for beam-dilution test  
  > "we take the molecular cloud catalog published by (cite: MivilleDeschenes_etal_2017) as a reference sample" (5.2.4) [from (cite: MivilleDeschenes_etal_2017)]

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
- masking: Seed: >=2 consecutive channels S/N>=5; expand to adjacent pixels with >=2 channels S/N>=2; extend in velocity to +-3 sigma Gaussian equivalent  
  > "we first identify all 3D regions in the data cube where $\geq 2$ consecutive channels show emission with signal-to-noise ratio ${\rm (S/N)} \geq 5$." (3.2 Measurement Procedure)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: PHANGS cubes include 12m, 7m and total power; Antennae lacks short spacing  
  > "This is the only target in our sample that lacks short- and zero-spacing data." (2 Data)
- smoothing: Convolved to round Gaussian beams of 45, 60, 80, 100, 120 pc FWHM; resampled to Nyquist-sampled grids  
  > "we pre-process all data sets by convolving them to a set of round Gaussian-shaped beams with fixed linear sizes: $45$, $60$, $80$, $100$, and $120$ pc (at FWHM)." (3.2 Measurement Procedure)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- PHANGS-ALMA observing strategy and data reduction described elsewhere  
  > "A detailed description of the PHANGS-ALMA sample, observing strategy and data reduction is presented in A. K. Leroy et al. (2018, in prep.)." (2 Data) [from A. K. Leroy et al. 2018, in prep.]
- Fixed-scale approach and spectral response correction  
  > "This approach has been advocated by (cite: Leroy_etal_2016)" (3.1) [from (cite: Leroy_etal_2016)]
- Effective width definition  
  > "Following (cite: Heyer_etal_2001), we define the effective width as" (3.4 Line Width) [from (cite: Heyer_etal_2001)]

### Not stated but needed to reproduce (our reading)

- Calibration/imaging details (CASA version, robust, tclean settings) for the PHANGS cubes are deferred to Leroy et al. 2018 in prep.
- Noise model used to generate Monte Carlo cube realizations is not specified
- MCMC walker count, steps, burn-in not given
- M31 CARMA cubes are unpublished (Schruba et al. in prep.)
- Which ALMA project code corresponds to which galaxy is not given (2015.1.00925.S printed only as '.00925.S')
- Center-region definition coordinates/nucleus positions not given

## Analysis recipe

1. **Convolve cubes to fixed linear resolutions**: Convolve to round Gaussian beams and resample to Nyquist grids  
  > "we resample the data sets onto regular square grids so that the pixels Nyquist-sample the new beam" (3.2 Measurement Procedure)
   - parameter: 45, 60, 80, 100, 120 pc; 10% tolerance on native resolution  
  > "When the native angular resolution of a data set is coarser than the target beam size, we exclude that galaxy from the analysis at that spatial scale" (3.2 Measurement Procedure)
   - fitting: _not stated_
   - validation: _not stated_
2. **Identify significant CO sightlines and measure I_CO, T_peak**: Two-stage S/N mask (5 sigma seed, 2 sigma expansion), velocity growth to +-3 sigma; compute integrated and peak intensity per sightline  
  > "we calculate the line-integrated intensity $\mbox{$I_\mathrm{CO}$}$ and peak intensity $\mbox{$T_\mathrm{peak}$}$ of the emission within the expanded mask." (3.2 Measurement Procedure)
   - fitting: _not stated_
   - validation: 1,000 Monte Carlo noise realizations with fixed mask give statistical errors  
  > "We generate $1,000$ realizations of the data cube by artificially adding random noise to the original cube" (3.2 Measurement Procedure)
3. **Convert to surface density**: Sigma = alpha_CO * I_CO with fixed conversion factors  
  > "We adopt the following conversion factors $\mbox{$\alpha_\mathrm{CO}$}\equiv \mbox{$\Sigma$}/\mbox{$I_\mathrm{CO}$}$" (3.3 Surface Density)
   - parameter: alpha_CO(1-0)=4.35, (2-1)=6.25, (3-2)=17.4 Msun pc^-2 (K km/s)^-1  
  > "\alpha_{\rm CO(2-1)} &= 6.25\;\mbox{$\mathrm{M}_{\odot}$}\,{\rm pc}^{-2}\,(\mbox{K\,km\,s$^{-1}$})^{-1}" (3.3 Surface Density)
   - assumption: Galactic alpha_CO; CO(2-1)/(1-0)=0.7, CO(3-2)/(1-0)=0.25; no inclination or filling-factor correction  
  > "we do not apply any correction to $\Sigma$ to account for beam filling factors or the effect of galaxy disk inclination." (3.3 Surface Density)
   - fitting: _not stated_
   - validation: _not stated_
4. **Measure velocity dispersion**: Effective width sigma = I_CO/(sqrt(2pi) T_peak), corrected in quadrature for spectral response  
  > "we subtract the effective width of the spectral response from the measured effective width" (3.4 Line Width)
   - parameter: sigma_response from channel width and channel-to-channel correlation r, measured from empty channels  
  > "we measure $r$ from the correlation between noise in successive empty spectral channels in the data cube" (Quantifying the Spectral Response Curve Width of the CO Maps)
   - assumption: No beam-smearing correction  
  > "we do not correct for unresolved rotational motions or contributions from multiple clouds along the line of sight." (3.4 Line Width)
   - fitting: _not stated_
   - validation: r at 60 pc compared with Leroy et al. 2016 k values  
  > "which are consistent with those reported by (cite: Leroy_etal_2016) (see Table 3 therein)." (Quantifying the Spectral Response Curve Width of the CO Maps)
5. **Derive virial parameter and turbulent pressure**: alpha_vir = 5 sigma^2 r_beam/(fGM) with R=r_beam; P_turb ~ Sigma sigma^2/(2R)  
  > "we take the beam size as the relevant size scale (i.e. $R = \mbox{$r_\mathrm{beam}$}$, thus $R = 40$ pc at $80$ pc resolution), adopt $f=10/9$" (5.3 The Virial Parameter)
   - assumption: Line-of-sight depth ~2 r_beam; density profile rho ~ r^-1 (f=10/9)  
  > "In this paper, we take $l \sim 2\mbox{$r_\mathrm{beam}$}$" (4.2)
   - fitting: _not stated_
   - validation: _not stated_
6. **Fit sigma-Sigma power law**: log sigma = beta log(Sigma/100) + A with intrinsic scatter, truncated likelihood, only sightlines above 5-sigma criterion  
  > "We include only the data points above our 2-consecutive-5-sigma selection criterion" (5.2.1)
   - software: emcee
   - fitting: emcee affine-invariant ensemble MCMC, uninformative priors, Gaussian likelihood with statistical covariance in both axes and intrinsic scatter, truncation normalization  
  > "We adopt a Bayesian approach with an uninformative prior, and find the best fit model parameters, as well as their estimated uncertainties, by sampling the posterior distribution" (Power-law Fitting Strategy and Results)
   - validation: Mock distributions recover input parameters; other fitting methods differ by ~0.05  
  > "We find that the input parameters can be accurately recovered as long as the truncation does not severely affect the whole distribution." (Power-law Fitting Strategy and Results)
7. **Test sensitivity effect on M33**: Add noise to M33 cube to match NGC 2835 noise and repeat analysis  
  > "We add random noise into the M33 data cube to artificially degrade it, so that its noise level matches that in the data cube for NGC 2835" (5.2.4)
   - fitting: _not stated_
   - validation: Compared with beam-diluted Milky Way cloud catalog  
  > "we calculate their “beam-averaged” surface density as $\mbox{$\Sigma$}' = \mbox{$\Sigma$}\;R^2 / r_{\rm beam}^2$" (5.2.4)

## Software

- **emcee** : MCMC fitting of sigma-Sigma relation  
  > "Our implementation is based on the Python package `emcee` (cite: Foreman-Mackey_etal_2013)" (Power-law Fitting Strategy and Results)
- **CASA** : listed in software section; specific use not stated  
  > "`CASA` (cite: McMullin_etal_2007)." (Software)
- **Astropy** : listed in software section  
  > "`Astropy` (cite: Astropy)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Combined main-sample sigma-Sigma slope (80 pc) | 0.47 | ~0.05 | dimensionless | 6 | \log_{10} \left( \frac{\mbox{$\sigma$}}{\mbox{km\,s$^{-1}$}} \right) = 0.47\,\log_{10} \left( \frac{\mbox{$\Sigma$}}{10^2\;\mbox{$\mathrm{M}_{\odot}$}\,\rm pc^{-2}} \right) + 0.85 |
| Combined main-sample normalization A (80 pc) | 0.85 | ~0.05 dex | dex | 6 | with (systematic-dominated) uncertainties of $\sim 0.05$ in the slope and $\sim 0.05$ dex in the intercept. |
| Per-galaxy slopes beta at 80 pc | 0.34-0.63 | not stated | dimensionless | 6 | At 80 pc resolution, we find best fit power-law slopes of $\beta = 0.34$-$0.63$ in individual galaxy disks. |
| Intrinsic scatter in sigma at fixed Sigma | <0.10 | not stated | dex | 6 | We find the intrinsic scatter in $\sigma$ at fixed $\Sigma$ to be less than $0.10$ dex for all galaxies at all resolutions. |
| Typical median alpha_vir | 1.5-3.0 | not stated | dimensionless | 5 | Most galaxies (excluding M31 and M33) have distributions centered near $\mbox{$\alpha_\mathrm{vir}$}\approx 1.5$-$3.0$ |
| Median alpha_vir M31 / M33 at 120 pc | 10.7 / 9.3 | not stated | dimensionless | 5 | M31 / 7.6 / 0.62 / – / 10.2 / 0.67 / – / 10.7 / 0.68 / – |
| Independent sightlines at 120 pc | ~30,000 | not stated | count | 2 | this sample corresponds to nearly $30,000$ independent beams across our sample |
| M33 recovered mass fraction after noise degradation | 63% to 8% | not stated | percent | 7 | the recovered molecular gas mass faction in M33 drastically drops from 63% to 8% |
| Center vs disk median Sigma offset in strongly barred galaxies | 0.8-1.7 | not stated | dex | 0 | the median $\Sigma$ value in the central region can be $0.8$-$1.7$ dex higher than in the disk. |
| Median P_turb range across sample | varies by >4 orders of magnitude (disk 10^3-10^5 low mass, 10^5-10^7 high mass K cm^-3) | not stated | K cm^-3 | 5 | The mass weighted median $P_\mathrm{turb}$ varies by more than $4$ orders of magnitude across our sample. |

## Qualitative findings

- The sigma-Sigma relation is approximately constant-alpha_vir across disks, while P_turb varies enormously with environment  
  > "This indicates only weak variation in the virial parameter $\alpha_\mathrm{vir}\propto\sigma^2/\Sigma$" (abstract)
- Central regions of strongly barred galaxies show elevated sigma at given Sigma  
  > "The same quantities appear enhanced in the central kpc of strongly barred galaxies relative to their disks." (abstract)

## Claim tuples

- H: Molecular gas at cloud scales has a common dynamical state across galaxies | E: Fixed-scale sigma and Sigma measurements and power-law fits for 15 galaxies | R: slope 0.34-0.63 per galaxy, combined 0.47; median alpha_vir 1.5-3.0 | F: Gas is near energy equipartition with weak alpha_vir variation | **supported**
- H: Turbulent pressure varies strongly with environment | E: Compute P_turb distributions | R: Median P_turb varies by >4 dex; centers up to 2-3 dex higher | F: Internal pressure depends strongly on environment and galaxy mass | **supported**
- H: The sigma-Sigma relation flattens at low Sigma | E: M31/M33 high-sensitivity maps; degrade M33 noise; beam-diluted MW clouds | R: M31/M33 show high sigma at low Sigma; degraded M33 follows alpha_vir~2 | F: Flattening is genuine in low-density environments, from beam dilution, missing gas and external pressure | **partially**
- H: The sigma-Sigma correlation is not an artifact of the effective-width definition | E: Compare sigma with T_peak | R: Correlation consistent with sigma ∝ T_peak | F: Relation conveys physical information | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Fixed-scale approach avoids segmentation criteria that find beam-sized objects and is simple to apply to simulations  
  > "Based on all these, we believe that the fixed-scale approach is at least as appropriate in this context as cloud identification." (3.1)
- Alternative: Cloud-identification (Clumpfind, cprops) rejected in favor of fixed-scale approach  
  > "Our fixed-scale approach differs from the cloud identification approaches commonly used in previous studies" (3.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Single alpha_CO adopted; absolute alpha_vir uncertain; beam smearing not corrected in centers  
  > "We adopt a single $\alpha_{\rm CO}$ and then discuss possible variations when they become relevant." (3.3 Surface Density)
- Caveat (inferred, ours): Beam size taken as cloud size; alpha_vir absolute values depend on assumed geometry
- Caveat (inferred, ours): Heterogeneous data sets (different lines, line ratios, sensitivities, missing short spacings in Antennae)
- Caveat (inferred, ours): Selection effects at low Sigma bias medians in NGC 2835 and NGC 5068
- Caveat (inferred, ours): Sigma and effective width correlated by construction (partly addressed)

## Reproducibility

- Data public (paper): ALMA programs listed; full measurement table available machine-readable  
  > "A machine-readable version of the full table is available." (Table 3)
- Products in archive: _not stated_
- Missing: PHANGS cube reduction recipe (in prep. paper)
- Missing: M31 CARMA cubes unpublished
- Missing: MCMC settings
- Missing: Per-galaxy ALMA project mapping
- Data volume (inferred): Hundreds of GB raw for 11 ALMA CO(2-1) mosaics plus Antennae; processed cubes tens of GB
- Score (inferred): 3/5, Measurement and fitting recipe is clear and results numeric, but PHANGS reduction and some data sets deferred to unpublished work.
- Rediscovery candidate: no, Calibrated PHANGS cubes and unpublished M31 data are needed; reduction details are deferred to in-prep papers.

## Links

- Method: (cite: Leroy_etal_2016) (Fixed-scale approach and spectral response correction)
- Method: (cite: Heyer_etal_2001) (Effective width definition)
- Method: (cite: Foreman-Mackey_etal_2013) (emcee sampler)
- Companion: A. K. Leroy et al. 2018, in prep. (PHANGS-ALMA survey and data reduction)
- Companion: (cite: Schruba_etal_2018) (Pressure in M31 and M33 using same data)
- Companion: (cite: Whitmore_etal_2014) (Antennae ALMA CO(3-2) data)
- Related: PHANGS-ALMA
- Related: PAWS
- Related: CARMA M31 survey
- Related: IRAM M33 large program

## Checks

```json
{
 "quotes": 69,
 "quotes_ok": 69,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2015.1.00925.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 90,
  "stated": 50,
  "rate": 0.556
 },
 "evidence_ok": true
}
```
