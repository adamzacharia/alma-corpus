# PHANGS CO Kinematics: Disk Orientations and Rotation Curves at 150 pc Resolution

`2020ApJ...897..122L` | The Astrophysical Journal 2020 | first author: Lang, Philipp | arXiv: 2005.11709 | DOI: 10.3847/1538-4357/ab9953

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: nearby_galaxies
- Question: What are the kinematic disk orientations and ~150 pc resolution rotation curves of PHANGS-ALMA galaxies, and is CO a reliable dynamical mass tracer?  
  > "We use the inner slope as well as the amplitude of our fitted rotation curves to demonstrate that CO is a reliable global dynamical mass tracer." (abstract)
- Target **67 PHANGS-ALMA galaxies (e.g. NGC 4654 showcase)**: coordinates Table of photometric centers (RA, Dec in deg) given for all galaxies  
  > "We thus have 67 PHANGS galaxies with high resolution CO maps for analysis." (Observations and sample); "We use the stellar mass of a galaxy ($M_\star$), the global star formation rate (SFR), and distance measurements from the $z{=}0$ Multiwavelength Galaxy Survey (z0MGS) compilation of data" (Observations and sample); z/distance 4.4-26.1 Mpc (Table)  
  > "We thus have 67 PHANGS galaxies with high resolution CO maps for analysis." (Observations and sample); "We use the stellar mass of a galaxy ($M_\star$), the global star formation rate (SFR), and distance measurements from the $z{=}0$ Multiwavelength Galaxy Survey (z0MGS) compilation of data" (Observations and sample); distance from z0MGS compilation (Leroy2019)  
  > "We thus have 67 PHANGS galaxies with high resolution CO maps for analysis." (Observations and sample); "We use the stellar mass of a galaxy ($M_\star$), the global star formation rate (SFR), and distance measurements from the $z{=}0$ Multiwavelength Galaxy Survey (z0MGS) compilation of data" (Observations and sample)

## Data provenance

- ALMA projects: 2013.1.00650.S, 2013.1.00803.S, 2013.1.01161.S, 2017.1.00392.S, 2017.1.00886.L, 2018.1.01651.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12m, 7m (ACA) and total power (TP)  
  > "including data from the 12-m array (designated ‘12m’), the Morita Atacama Compact Array (designated ‘7m’) and the 12-m telescopes configured to observe as single-dish telescopes" (Observations and sample)
- configurations: 12m C43-1 or C43-2  
  > "The 12m data are obtained from array configurations C43-1 or C43-2." (Observations and sample)
- baselines: _not stated_
- angular resolution: ~1 arcsec (~150 pc median ~100 pc scale); 7m maps ~650 pc  
  > "PHANGS targets are chosen to be nearby (distance $< 17$ Mpc) such that the survey’s nominal resolution of $1''$ accesses linear scales of about $100$ pc." (Observations and sample)
- max recoverable scale: _not stated_
- sensitivity: 1σ ≈ 0.3 K in a 2.5 km/s channel  
  > "The $1\sigma$ noise level in the maps is approximately $0.3$ K in a $2.5$ $\mathrm{km~s^{-1}}$ channel." (Observations and sample)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (not stated)
- Other facility **Spitzer S4G (3.6 um)**: Photometric priors on center, PA, inclination, B/T  
  > "We adopt central coordinates, position angles and inclinations from the (cite: Salo2015) catalog based on isophotal analysis on Spitzer/3.6 $\mu$m images." (2.3.1 Photometric priors)
- Other facility **HyperLEDA**: R25, systemic velocity priors, orientations for non-S4G sources  
  > "Galaxy orientations for non-S4G sources are adopted from HyperLEDA." (2.3.1 Photometric priors)
- Other facility **2MASS/LGA**: Central positions/orientations for some non-S4G sources  
  > "we adopt the central positions from the 2MASS/LGA catalog (cite: Jarrett2003) based on $J$/$H$/$K$-band imaging if available" (2.3.1 Photometric priors)
- External data: Photometric centers, PA, inclinations, B/T from S4G  
  > "We adopt central coordinates, position angles and inclinations from the (cite: Salo2015) catalog" (2.3.1 Photometric priors) [from (cite: Salo2015)]
- External data: Stellar mass, SFR, distances  
  > "We use the stellar mass of a galaxy ($M_\star$), the global star formation rate (SFR), and distance measurements from the $z{=}0$ Multiwavelength Galaxy Survey (z0MGS) compilation of data (cite: Leroy2019)." (Observations and sample) [from (cite: Leroy2019)]
- External data: Bar lengths R_bar  
  > "$R_{{\rm bar}}$ measurements for the PHANGS-ALMA sample are compiled by M. Querejeta et al. (in prep.)" (2.3.2 Central bar and bulge properties) [from M. Querejeta et al. (in prep.); (cite: Herrera2015)]
- External data: Stellar Tully-Fisher relation  
  > "the velocity implied by the Tully-Fisher relation measured by (cite: McGaugh2015)" (4.2 Overview) [from (cite: McGaugh2015)]
- Simulation/model as data: Mock galaxy velocity fields used to test the method  
  > "We have examined the impact of these properties on the results of our method by performing extensive tests on mock galaxy velocity fields." (2.2 Sample demographics)

## Processing

### Calibration

- pipeline or manual: Observatory pipeline for 12m and 7m; TP via Herrera et al. scripts  
  > "We calibrate the 12m and 7m data using the observatory-provided pipeline, and we calibrate and image the TP data using the scripts developed by (cite: herrera20)." (Observations and sample)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA v5.4 imaging with emission-mask cleaning; feather for combination  
  > "We imaged the 12m+7m data with CASA v5.4 using an emission-mask based cleaning scheme as described in A. K. Leroy et al. (in prep)." (Observations and sample)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: Corrected for primary beam power pattern  
  > "producing a well-sampled map that is then corrected for the primary beam power pattern." (Observations and sample)
- array combination: Feather with TP data  
  > "The interferometer data are merged with the single-dish data using the feather task within CASA" (Observations and sample)
- smoothing: Convolved to circular beams  
  > "We convolve the maps to have circular synthesized beams." (Observations and sample)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Sample selection, ALMA observations, data processing and imaging  
  > "Details of the sample selection, ALMA observations, and data processing are described in detail by A. K. Leroy et al. (in prep)." (Observations and sample) [from A. K. Leroy et al. (in prep)]
- Global galaxy parameters  
  > "We adopt global galaxy parameters for the galaxies as outlined in A. K. Leroy et al. (in prep)." (Observations and sample) [from A. K. Leroy et al. (in prep)]
- Rotation curve parametrization (arctan)  
  > "We adopt the empirical parametrization of rotation curves by the function (cite: Courteau1997)" (4.4.3 Smooth analytic fits) [from (cite: Courteau1997)]

### Not stated but needed to reproduce (our reading)

- CLEAN parameters (robust, threshold, masks) for the 12m+7m imaging, deferred to Leroy et al. in prep
- Precise noise-map smoothing and moment-map uncertainty computation
- emcee walker initialization for V_sys width and sigma_0^2
- Stellar M/L conversion and stellar-mass values per galaxy
- Which galaxies' measured velocity-field fits were truncated beyond the two named
- Bin-coverage threshold implementation details

## Analysis recipe

1. **Build masked moment maps**: Noise map from MAD, two-stage strict mask (3.5σ in 3 channels, dilated to 2σ in 2 channels) plus 500 pc mask → broad mask; moment-0 and moment-1 velocity maps  
  > "We first identify all regions with $T_{\rm B}>3.5\sigma$ in three consecutive channels. These regions are then dilated in three dimensional space to all connected regions that show $T_{\rm B}>2\sigma$ in two consecutive channels." (Observations and sample)
   - parameter: Remove pixels with I_CO,broad < 2x uncertainty or velocity differing >30 km/s from 500 pc field  
  > "the velocity field at high resolution differs from the velocity field measured at 500 pc resolution by more than $30~\mathrm{km~s^{-1}}$." (Observations and sample)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit global disk orientation with MCMC**: Fit circular-rotation model V_los = V_sys + V_rot cos(theta) sin i to all lines of sight; radial V_rot(c1) via linear least squares in beam-wide annuli nested in MCMC over phi, i, V_sys, sigma_0^2; cos(theta_PA) weighting  
  > "We sample a four-dimensional parameter space defined by $\phi$, $i$, $V_{{\rm sys}}$ and excess variance $\sigma^2_{0}$, leaving the center position $(X_{{\rm cen}},Y_{{\rm cen}})$ fixed for this analysis." (3.2.3 MCMC Implementation)
   - software: emcee
   - parameter: 1000 steps, 50 walkers, 350 burn-in steps  
  > "In total, the emcee sampler sampler is run for 1000 steps with 50 walkers." (3.2.3 MCMC Implementation)
   - parameter: Walkers initialized uniformly within 50 deg width centered on photometric phi and i  
  > "we initialize the walkers for $\phi$ and $i$ in the emcee sampler in a uniform distribution with a conservative width of 50 degrees" (3.2.3 MCMC Implementation)
   - assumption: Thin circular disk, constant phi and i with radius; q_min=0.25 for photometric inclination  
  > "which we fix to a value of $0.25$ (cite: vdW2014)" (2.3.1 Photometric priors)
   - fitting: emcee; flat priors on phi, i, V_sys; sigma_0^2 ~ InvGamma(N, 2.5); Gaussian log-likelihood with weights  
  > "We assume an inverse-Gamma distribution for the excess variance with a characteristic scale $2.5~\mathrm{km^2~s^{-2}}$" (3.2.3 MCMC Implementation)
   - validation: Tests on mock velocity fields; comparison with literature orientations and ROTCUR tilted rings  
  > "Our assessment of the quality of these results is motivated by extensive testing of the method on mock galaxy velocity fields." (4 Results)
3. **Jackknife uncertainties**: Four radial bins, three jackknife realizations removing two bins, mean absolute difference times 1.25 as Gaussian 1σ  
  > "Finally, we convert the values of mean absolute difference to a representative Gaussian $1\sigma$ error by applying a multiplication with a factor of $1.25$." (3.3.1 Orientation Parameters)
   - fitting: _not stated_
   - validation: Median uncertainties 1.3 deg (phi), 5.6 deg (i)  
  > "The jackknife uncertainties overall yield median uncertainties of 1.3 and 5.6 degrees on $\phi_\mathrm{kin}$ and $i_\mathrm{kin}$, respectively." (3.3.1 Orientation Parameters)
4. **Reliability assessment of fits**: Flag unreliable i_kin via Tully-Fisher velocity consistency, |i_kin-i_phot|≳30 deg, and strong large bars (eps>0.4, R_bar/R_CO,max≳0.45); use i_phot for those  
  > "Galaxies with large strong bars (as quantified by $\epsilon>0.4$ and $R_{{\rm bar}} / R_{{\rm CO,max}}\gtrsim 0.45$) are also flagged as unreliable" (4.2 Overview)
   - fitting: _not stated_
   - validation: _not stated_
5. **Derive final rotation curves**: Least-squares fit with fixed orientation in 150 pc wide radial bins; 100 Monte Carlo realizations perturbing phi, i, V_sys by jackknife errors and center by 1 arcsec; drop bins with <10% detections or mean angle from major axis >55 deg  
  > "we adopt $\delta=55$ degrees and a 10% threshold for our sample." (3.3.2 Final Rotation Curves)
   - fitting: Least squares; 16th/84th percentile errors  
  > "The error on rotation velocity at a given radial bin is then computed based on the 16th and 84th percentile of the 100 realizations." (3.3.2 Final Rotation Curves)
   - validation: _not stated_
6. **Smooth arctan fits and dynamical masses**: Fit V_rot = V0 (2/pi) arctan(R/r_t) excluding R<2 kpc for 12 galaxies; M_dyn = V^2 R / G  
  > "we exclude radii $R<2$ kpc to prevent this region from dominating our analytic fits. In total, 12 galaxies are masked in this manner" (4.4.3 Smooth analytic fits)
   - assumption: Spherical geometry for M_dyn  
  > "assuming a spherical geometry" (5.2 Inner rotation curve shapes)
   - fitting: Fits repeated on all 100 MC curves; 16/84 percentiles  
  > "We derive uncertainties on $V_0$ and $r_{{\rm t}}$ by iterating our fits over all 100 Monte-Carlo realizations of rotation curves" (4.4.3 Smooth analytic fits)
   - validation: Compared to Tully-Fisher and S4G enclosed stellar mass  
  > "we show the inferred inner ($\le 500$ pc) dynamical mass versus the stellar mass within the same radius in Figure [11](#Mdyn.fig)." (5.2 Inner rotation curve shapes at high resolution as tracers of the central mass distributions of galaxies)

## Software

- **CASA** v5.4: Imaging of 12m+7m data and feathering with TP  
  > "We imaged the 12m+7m data with CASA v5.4" (Observations and sample)
- **emcee** : MCMC sampling of orientation parameters  
  > "Our regression process is performed using MCMC as implemented specifically in the python emcee package" (3.2.3 MCMC Implementation)
- **GIPSY (ROTCUR)** : Tilted-ring comparison for NGC 4654  
  > "as determined from a tilted-ring analysis with the ROTCUR routine in the Groningen Image Processing System" (4.1 Example NGC 4654)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Median R_CO,max/R25 | 0.72 | not stated | dimensionless | 1 | has a range of $0.26{-}1.2$, and median of $0.72$. |
| Median CO covering fraction | 30 | not stated | % | 1 | The median CO covering fraction in the sample is about 30 %. |
| Galaxies with reliable kinematic orientation | 52 of 67 (78%) | not stated | galaxies | 4 | we obtain reliable results for the majority (78 %) of our kinematic sample. |
| Median jackknife uncertainty on phi_kin | 1.3 | not stated | deg | 3 | median uncertainties of 1.3 and 5.6 degrees on $\phi_\mathrm{kin}$ and $i_\mathrm{kin}$ |
| Median uncertainty on i_kin | 5.6 | not stated | deg | 3 | median uncertainties of 1.3 and 5.6 degrees on $\phi_\mathrm{kin}$ and $i_\mathrm{kin}$ |
| Median i_kin - i_phot (all) | -0.5 | +10.0/-7.2 | deg | 2 | All / $-1.3^{+7.4}_{-9.9}$ / $-0.5^{+10.0}_{-7.2}$ |
| Median phi_kin - phi_phot (all) | -1.3 | +7.4/-9.9 | deg | 2 | All / $-1.3^{+7.4}_{-9.9}$ / $-0.5^{+10.0}_{-7.2}$ |
| Inner slope vs stellar mass Spearman coefficient | 0.63 | not stated | dimensionless | 6 | with a Spearman’s rank correlation coefficient of $0.63$ |
| Median log Mdyn - log Mstar within 500 pc | 0.1 | +0.3/-0.4 | dex | 6 | $0.1^{+0.3}_{-0.4}$ |
| Scatter of V_rot,25 at fixed stellar mass | ~0.07 | not stated | dex | 6 | The scatter in our reconstructions of $V_{{\rm rot,25}}$ at fixed stellar mass is $\sim 0.07$ dex. |

## Qualitative findings

- Kinematic and photometric orientations agree equally well for barred and unbarred galaxies  
  > "orientations agree equally well for unbarred and barred galaxies" (4.3.1)

## Claim tuples

- H: Global-orientation fitting of CO velocity fields yields robust disk orientations despite bars and spirals | E: Fit 67 PHANGS velocity fields and compare with photometric and 7m results | R: Median offsets ~ -0.5 deg in i and -1.3 deg in phi; 52 reliable fits | F: Method robust except for prominently barred or poorly sampled cases | **supported**
- H: CO rotation curves trace inner and global dynamical mass | E: Inner slope vs M*, M_dyn vs M*(<500 pc), and Tully-Fisher | R: Correlations 0.63, 0.73; TF scatter ~0.07 dex | F: CO is a reliable dynamical tracer once systematics are accounted for | **supported**
- H: Stellar disks are circular with uniform thickness | E: Compare kinematic and photometric orientations | R: No trend of offsets with galaxy properties | F: Disks very close to circular and of uniform thickness | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Global orientation fit chosen to reduce impact of non-axisymmetric features and sparse CO coverage  
  > "Our approach identifies an optimal global orientation as a way to reduce the impact of non-axisymmetric (bar and spiral) features and the uneven spatial sampling characteristic of CO emission" (abstract)
- Alternative: Tilted-ring fits in independent radial bins can be biased by sparse coverage and non-circular motions  
  > "fitting orientation parameters in independent radial bins following the tilted ring model can be biased by the sparse coverage of the mapped area" (3.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Inclination unreliable for strong bars and solid-body-only velocity fields; bin covariance not accounted for  
  > "Note that we do not account for bin covariance in our assignment of an uncertainty to each individual radial bin." (4.4.1)
- Caveat (inferred, ours): Pure circular-motion model ignores non-circular flows
- Caveat (inferred, ours): Jackknife errors partly ad hoc (1.25 factor)
- Caveat (inferred, ours): Reliability thresholds somewhat subjective

## Reproducibility

- Data public (paper): ALMA programs listed; public availability not explicitly stated  
  > "The PHANGS-ALMA sample comprises observations from several ALMA programs: 2013.1.00650.S, P.I. E. Schinnerer; 2013.1.00803.S, P.I. D. Espada;" (2.1 ALMA CO (2-1) observations and sample selection)
- Products in archive: _not stated_
- Missing: Leroy et al. in prep imaging recipe and moment maps
- Missing: Querejeta et al. bar lengths
- Missing: Public moment maps/code not stated
- Data volume (inferred): Large raw data (tens of TB for full survey); derived moment maps are small
- Score (inferred): 3/5, Fitting method fully described but data processing deferred to in-prep paper and no code stated.
- Rediscovery candidate: no, Relies on unpublished processed maps and in-prep catalogs.

## Links

- Method: A. K. Leroy et al. (in prep) (PHANGS-ALMA data processing and masks)
- Method: (cite: herrera20) (TP calibration and imaging)
- Related: PHANGS-ALMA
- Related: S4G
- Related: z0MGS

## Checks

```json
{
 "quotes": 73,
 "quotes_ok": 73,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 6,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2013.1.00650.S"
 ],
 "obscore_codes_not_in_card": [
  "2012.1.00650.S",
  "2015.1.00925.S",
  "2015.1.00956.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 83,
  "stated": 49,
  "rate": 0.59
 },
 "evidence_ok": true
}
```
