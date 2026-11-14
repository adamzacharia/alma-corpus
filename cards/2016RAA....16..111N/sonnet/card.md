# Morphology and kinematics of the gas envelope of the variable AGB star π<SUP>1</SUP> Gruis

`2016RAA....16..111N` | Research in Astronomy and Astrophysics 2016 | first author: Nhung, Pham Tuyet | arXiv: 1601.04834 | DOI: 10.1088/1674-4527/16/7/111

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: evolved_stars
- Question: What are the morphology and kinematics of the CO(3-2) gas envelope of pi1 Gru, and does a continuous equator-to-pole expansion model fit better than the flared disk plus bipolar outflow model of Chiu et al. (2006)?  
  > "The present work presents an analysis and modeling of these new data." (Introduction); "In a first step, we reproduce the results obtained by C2006 for CO(2-1)." (Flared disk model of the CSE)
- Target **pi1 Gruis (HIP 110478)**: coordinates _not stated_; z/distance 163 pc  
  > "It is close to the Sun, only 163 pc ((cite: VanLee2007)) and very bright, making it one the best known S stars." (Introduction); distance from van Leeuwen 2007 (cite: VanLee2007)  
  > "It is close to the Sun, only 163 pc ((cite: VanLee2007)) and very bright, making it one the best known S stars." (Introduction)

## Data provenance

- ALMA projects: 2012.1.00524.S
- bands: _not stated_
- frequencies and spectral setup: sixty velocity bins of 2 km/s between -60 and 60 km/s  
  > "The line Doppler velocity spectra are available in sixty bins of 2 kms$^{-1}$ between $-60$ kms$^{-1}$ and 60 kms$^{-1}$" (Observations, data reduction and data selection)
- continuum bandwidth: _not stated_
- arrays: ACA (seven 7-m antennae)  
  > "using the compact array (ACA, seven 7-m antennae) configuration" (Observations, data reduction and data selection)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 4.45'' x 2.48'', PA -84 deg  
  > "beam size and position angle of $4.45''\times2.48''$ and $-84^\circ$" (Observations, data reduction and data selection)
- max recoverable scale: _not stated_
- sensitivity: rms 6.2 mJy arcsec^-2  
  > "The peak associated with the effective noise has an rms value of 6.2 mJy arcsec$^{-2}$." (Observations, data reduction and data selection)
- time on source: six minutes on the line  
  > "for six minutes on the line" (Observations, data reduction and data selection)
- observing dates: 8 October 2013  
  > "The star was observed on October 8$^{\text{th}}$, 2013" (Observations, data reduction and data selection)
- pi or archival as stated: Public archival data retrieved from JVO portal  
  > "The data are retrieved from the JVO portal (http://jvo.nao.ac.jp/portal) operated by the NAOJ" (footnote)
- Line: CO J=3-2 (not stated)
- External data: Chiu et al. 2006 SMA CO(2-1) flared disk model parameters used for comparison  
  > "The values of the parameters giving the best fit are compared in Table 1 with the values found by Chiu et al. for CO(2-1)." (Flared disk model of the CSE) [from Chiu et al. (2006), C2006]
- External data: LSR velocity measurement of -11.7+-2.5 km/s  
  > "the measured value given by Mayer et al. (2014) is $-11.7\pm2.5$ kms$^{-1}$" (Observations, data reduction and data selection) [from Mayer et al. (2014)]
- External data: CO dissociation radius ~6700 AU (~41'')  
  > "From Mamon et al. (1988) we estimate the effective radius of dissociation of CO molecules by the interstellar UV radiation to be $\sim6700$ AU" (Observations, data reduction and data selection) [from Mamon et al. (1988)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Data reduced by ALMA staff  
  > "The data have been reduced by the ALMA staff." (Observations, data reduction and data selection)
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

- Flared disk model parametrization and 2 km/s Gaussian smearing  
  > "A Gaussian smearing of $\pm2$ kms$^{-1}$ is included as in C2006." (Flared disk model of the CSE) [from Chiu et al. (2006), C2006]

### Not stated but needed to reproduce (our reading)

- CASA version and pipeline details of the ALMA staff reduction
- Line rest frequency and spectral setup
- Fit algorithm and minimizer used for chi2, and how chi2 weights are defined
- Exact pixel/velocity range used for chi2
- Treatment of the primary beam and flux scale uncertainty
- Target coordinates and whether the data cube was the archive product

## Analysis recipe

1. **Select and prepare data cube**: Center on peak emission, restrict to velocity range -36 to 40 km/s, R<7'' and apply 3 sigma cut  
  > "we limit the analysis to $R<7''$ in order to keep the effects of noise and side lobes at a low level and apply a 3$\sigma$ cut" (Observations, data reduction and data selection)
   - parameter: 3 sigma cut = 0.02 Jy arcsec^-2  
  > "apply a 3$\sigma$ cut to the measured flux densities (0.02 Jy arcsec$^{-2}$)" (Observations, data reduction and data selection)
   - fitting: _not stated_
   - validation: _not stated_
2. **Characterize morphology and kinematics**: Channel maps, mean Doppler velocity map and sine-wave fits versus position angle  
  > "well described by simple sine wave fits of the form $35.6+13.0\sin(2\varphi+101^\circ)$" (Morphology and kinematics of the observed CSE)
   - fitting: _not stated_
   - validation: _not stated_
3. **Reproduce C2006 flared disk model**: Flared disk with effective density r^-n and radial wind, integrated along the line of sight to r=41'' with 2'' pixels, no beam convolution  
  > "We use a pixel size of $2''\times2''$ without convolving the model by the beam and integrate along the line of sight up to $r=41''$" (Flared disk model of the CSE)
   - assumption: Effective density proportional to r^-n and constant radial wind velocity  
  > "We take the effective density proportional to $r^{-n}$ and the wind velocity radial with constant intensity $v_{rad}$ ." (Flared disk model of the CSE)
   - fitting: _not stated_
   - validation: Compared parameters with C2006 CO(2-1) values and the model with the data (Figure 5)  
  > "The measured spectral map is compared with the model result in Figure 5." (Flared disk model of the CSE)
4. **Fit new continuous equator-to-pole model**: Radial expansion velocity V_pole exp(-0.5 cos^2 alpha/sigma_pole^2), effective density rho0 r^-n (cos alpha)^p [1-exp(-0.5 r^2/sigma_cut^2)]; nine free parameters  
  > "$\rho=\rho_0 r^{-n}(\cos\alpha)^p[1-\exp(-0.5r^2/\sigma_{cut}^2)]$ namely five parameters to be adjusted" (A new model of the CSE)
   - parameter: Additional parameters: theta, psi, smearing sigma_v, velocity origin shift delta v  
  > "the direction of the star axis, measured by $\theta$ and $\psi$ as before, the smearing parameter $\sigma_v$ and a small shift $\delta v$" (A new model of the CSE)
   - assumption: Rotation about the star axis not included, since it gave no significant improvement  
  > "adding rotation about the star axis does not bring significant improvement" (A new model of the CSE)
   - fitting: chi2 minimization; uncertainties are the parameter changes raising chi2 by 5%, ignoring correlations  
  > "proportional to the quantity by which they must be changed to increase the value of $\chi^2$ by $\sim5\%$" (A new model of the CSE)
   - validation: chi2 divided by 2.9 relative to C2006 model; fit compared to spectral map  
  > "The best fit value of $\chi^2$ is divided by 2.9 with respect to the C2006 model fit" (A new model of the CSE)

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Disk model inclination theta (CO(3-2)) | 140 | not stated | deg | 3 | /    $\theta$     /  $145^\circ$  /   $140^\circ$   / |
| Disk model radial velocity V_rad (CO(3-2)) | 12.5 | not stated | km/s | 3 | /    $V_{rad}$    / 11 kms$^{-1}$ / 12.5 kms$^{-1}$ / |
| Disk model density index n | 2.03 | not stated | dimensionless | 3 | /       $n$       /      \-       /      2.03       / |
| New model normalization rho0 | 144 | not stated | Jy arcsec^-3 km/s | 4 | The value of $\rho_0$, obtained from the normalization between data and model, is 144 Jy arcsec$^{-3}$kms$^{-1}$. |
| Chi2 improvement factor of new model | 2.9 | not stated | dimensionless | 4 | The best fit value of $\chi^2$ is divided by 2.9 with respect to the C2006 model fit |
| Upper limit on polar effective density | 13 | not stated | Jy arcsec^-3 km/s | 4 | its largest possible value making $\chi^2$ increase by at most $5\%$ is only 13 Jy arcsec$^{-3}$kms$^{-1}$ compared with 144 at the equator |
| Line profile wing extent | -36 to 40 | not stated | km/s | 1 | wings extending to $-36$ kms$^{-1}$ and 40 kms$^{-1}$ |

## Qualitative findings

- Continuity between low and high Doppler velocities suggests a smooth variation of expansion velocity from equator to poles rather than a confined bipolar jet  
  > "This suggests a smooth variation of the expansion velocity from the star equator, where the disk stands, to the star poles" (A new model of the CSE)
- The new model underestimates the double horn structure and no simple modification was found  
  > "We failed to find a simple modification of the new model that would account for this feature." (A new model of the CSE)

## Claim tuples

- H: A model with continuous equator-to-pole variation describes the CSE better than the flared disk plus jet model | E: Fit both the C2006-type flared disk and a new nine-parameter model to the CO(3-2) cube | R: chi2 divided by 2.9; high velocity wings reproduced | F: No need for expansion confined to a flared disk with sharp boundaries | **supported**
- H: The effective density is strongly oblate | E: Allowed a polar density in the fit | R: Polar density at most 13 versus 144 at equator | F: Effective density drops by at least a factor 10 between equator and poles | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Detailed analysis like C2006 would only repeat earlier work, so they model morphology and kinematics with effective density  
  > "We limit instead our discussion of the present data to the modelling of the morphology and kinematics of the CSE using the concept of effective density" (Morphology and kinematics of the observed CSE)
- Alternative: Adding rotation about the star axis and a velocity gradient gave no significant improvement  
  > "We checked that accounting for a velocity gradient does not significantly improve the quality of the best fit." (A new model of the CSE)
- How they decided it was enough: _not stated_
- Limitation (authors): Model is crude; uncertainties are not reliable quantitatively  
  > "The relative crudeness of the present model does not allow for a reliable quantitative evaluation of the uncertainties attached to the model parameters." (A new model of the CSE)
- Limitation (authors): Data cannot separate gas density and temperature  
  > "The present data do not allow for telling apart the respective roles of actual gas density and temperature in such a strong latitudinal dependence." (Discussion and conclusion)
- Caveat (inferred, ours): Single-line, short ACA observation with ~4'' beam limits constraints on the model
- Caveat (inferred, ours): Pseudo-uncertainties from 5% chi2 change are not statistical
- Caveat (inferred, ours): Effective density conflates density, temperature and excitation
- Caveat (inferred, ours): Model degeneracies and the fitting algorithm are not documented

## Reproducibility

- Data public (paper): Public ALMA data after one-year exclusive period, retrieved from JVO  
  > "who are making their data available to the public after a one year period of exclusive property" (ACKNOWLEDGEMENTS)
- Products in archive: _not stated_
- Missing: Fitting code and minimizer
- Missing: Chi2 definition and weights
- Missing: Rest frequency and cube specifics
- Missing: Exact model integration grid for the new model
- Data volume (inferred): <1 GB (single ACA CO(3-2) cube)
- Score (inferred): 3/5, Public data and explicit model equations with a parameter table, but the fitting procedure and code are not described.
- Rediscovery candidate: no, Model fit details are incomplete and uncertainties are non-standard.

## Links

- Method: Chiu et al. 2006, ApJ, 645, 605 (Source of the flared disk model reproduced here)
- Companion: Nhung et al. 2015a,b; Hoai et al. 2014 (Similar effective density model applied to RS Cnc and EP Aqr)

## Checks

```json
{
 "quotes": 47,
 "quotes_ok": 47,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 33,
  "rate": 0.485
 },
 "evidence_ok": true
}
```
