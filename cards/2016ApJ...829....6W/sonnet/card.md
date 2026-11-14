# ALMA Observations of HD 141569’s Circumstellar Disk

`2016ApJ...829....6W` | The Astrophysical Journal 2016 | first author: White, J. A. | arXiv: 1606.00442 | DOI: 10.3847/0004-637X/829/1/6

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: debris_disks, protoplanetary_disks
- Question: What are the dust and CO gas structure, kinematics and masses of the HD141569 disk, and is the gas primordial or second-generation (debris-related)?  
  > "We discuss whether the gas in HD141569’s disk may be second generation." (abstract)
- Target **HD141569**: coordinates RA 15h49m57.73s, Dec -03d55m16.62s (J2000)  
  > "Observations were centered on HD141569 using J2000 coordinates RA = 15 hr 49 min 57.73 sec and $\delta = -3^{\circ} 55' 16.62''$." (2 Observations); "HD141569 is a B9.5 Ve star at a distance[^1] of $116\pm8$ pc (cite: van)." (1 Introduction); z/distance 116 ± 8 pc  
  > "Observations were centered on HD141569 using J2000 coordinates RA = 15 hr 49 min 57.73 sec and $\delta = -3^{\circ} 55' 16.62''$." (2 Observations); "HD141569 is a B9.5 Ve star at a distance[^1] of $116\pm8$ pc (cite: van)." (1 Introduction); distance from re-analysed Hipparcos (van Leeuwen 2007)  
  > "Observations were centered on HD141569 using J2000 coordinates RA = 15 hr 49 min 57.73 sec and $\delta = -3^{\circ} 55' 16.62''$." (2 Observations); "HD141569 is a B9.5 Ve star at a distance[^1] of $116\pm8$ pc (cite: van)." (1 Introduction)

## Data provenance

- ALMA projects: 2012.1.00698.S
- bands: Band 7 (~345 GHz)  
  > "observations were taken in band 7 (at $\sim345$ GHz)" (2 Observations)
- frequencies and spectral setup: 4 spectral windows, 1875 MHz wide, centers 335, 337, 345, 347 GHz; FDM, 3840 channels of 488 kHz (0.85 km/s resolution)  
  > "Four different spectral windows were used with 1875 MHz bandpasses at rest frequency centers of 335, 337, 345, and 347 GHz." (2 Observations); "The correlator in FDM gives 3840 channels of width 488 kHz, which corresponds to a velocity resolution of $0.85$ km s$^{-1}$." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: compact configuration, 32 antennas (31 after flagging)  
  > "A compact configuration was used with 32 antennas; the longest baseline was 650.3 m." (2 Observations)
- baselines: longest baseline 650.3 m  
  > "the longest baseline was 650.3 m" (2 Observations)
- angular resolution: 0.38" (continuum)  
  > "with $0."38$ resolution and $0.07 ~ \rm mJy~beam^{-1}$ sensitivity" (abstract)
- max recoverable scale: _not stated_
- sensitivity: 0.070 mJy/beam continuum; 0.028 Jy/beam CO  
  > "$0.070$ mJy beam$^{-1}$" (Table 2)
- time on source: 1.43 hr total, 0.79 hr on target (one EB)  
  > "The total integration time for the successful EB was 1.43 hr (0.79 hr on target)." (2 Observations)
- observing dates: 21 May 2014  
  > "The data were acquired on 21 May 2014" (2 Observations)
- pi or archival as stated: _not stated_
- Line: 12CO J=3-2 (345.79 GHz)
- External data: Previous continuum/total-system flux densities (Keck, IRAS, HST, APEX, JCMT) in Table 1  
  > "Summary of select previous HD 141569 debris disk observations." (Table 1) [from Fisher 2000; Walker 1988; Marsh 2002; Mouillet 2001; Augereau 1999; Nilsson 2010; Sylvester 2001]
- External data: CARMA CO(1-0) flux 1.6 ± 0.2 Jy km/s and gas mass 13 (+50/-9) Earth masses, SMA 870um flux 8.2 ± 2.4 mJy  
  > "The (cite: flaherty) CARMA observations found an integrated line flux for CO(1-0) of $1.6\pm 0.2\rm~Jy~km~s^{-1}$" (5.4) [from Flaherty et al. 2016 (cite: flaherty)]
- External data: Distance 116 ± 8 pc  
  > "The re-analyzed *Hipparcos* Catalog distance with 1-$\sigma$ uncertainty is $116\pm8$ pc (cite: van)." (5.2 MCMC Modeling) [from van Leeuwen 2007]
- External data: CO spectroscopic data (A32, Be) from Splatalogue  
  > "The spectral information for the CO molecule was obtained from the Splatalogue database" (footnote 4) [from Remijan 2010 (cite: splat)]

## Processing

### Calibration

- pipeline or manual: CASA reduction: WVR, Tsys, bandpass, flux, phase calibration  
  > "The data reduction in CASA included WVR calibration; system temperature corrections; and bandpass, flux, and phase calibrations with Titan and quasar J1550+0527." (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (flux), J1550+0527 (bandpass)  
  > "Titan and quasar J1550+0527 were used for absolute flux and bandpass calibration, respectively." (2 Observations)
- flux scale uncertainty: ~10%  
  > "an absolute flux calibration uncertainty of $\sim10\%$ added in quadrature" (3 Results)
- self calibration: _not stated_

### Imaging

- task: CASA CLEAN  
  > "The continuum (with the CO channels removed) is deconvolved and imaged using CASA’s CLEAN algorithm." (3.1 Continuum)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "A threshold of $\frac{1}{2} \times \sigma_{RMS}$ and a natural weighting are used" (3.1 Continuum)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: CASA uvcontsub for CO  
  > "The CO is continuum subtracted using the CASA task *uvcontsub*." (3.2 Gas Disk)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: continuum 0.42x0.34" PA -61.1 deg; CO 0.34x0.31" PA -77.1 deg  
  > "Beam Position Angle (PA) | $-61.1^{\circ}$ | $-77.1^{\circ}$" (Table 2)
- final rms: 0.070 mJy/beam continuum; 0.028 Jy/beam CO moment 0  
  > "$0.070$ mJy beam$^{-1}$" (Table 2)

### Inherited from earlier work

- MCMC Metropolis-Hastings algorithm  
  > "Parameter space is explored through a random walk directed by Metropolis-Hastings MCMC (cite: ford)." (5.2 MCMC Modeling) [from Ford 2005 (cite: ford)]
- Gas mass formalism for optically thin LTE CO  
  > "The mass of an optically thin gas disk near LTE can be calculated from the integrated line intensity (cite: perez)." (5.3 Gas Mass) [from Perez et al. 2015 (cite: perez)]
- Grain temperature and Q_nu emission treatment  
  > "The grain temperature (cite: wyatt) is" (5.1 Debris/Dust Mass) [from Wyatt & Dent 2002 (cite: wyatt)]
- Collisional cascade size distribution  
  > "we use a collisional cascade such that the mass per size increment $M_s\propto s^{-0.5}$ (cite: dohnayi)" (5.1 Debris/Dust Mass) [from Dohnanyi 1969 (cite: dohnayi)]
- H2/CO abundance ratio of 1e4  
  > "If we assume the $10^4$ ISM number density abundance ratio for H$_{2}$ to CO (as in Flaherty et al.)" (5.3 Gas Mass) [from Flaherty et al. 2016]

### Not stated but needed to reproduce (our reading)

- CASA version
- Number of clean iterations and mask used for CLEAN; image size and cell size
- Which channels were treated as CO-free for the continuum and uvcontsub fit order
- Velocity-axis reference/ rest frequency used for moment maps; moment-map clipping thresholds
- uvmodelfit starting parameters
- How the first moment map was sampled (pixels, masking) for chi^2 and how the model was projected
- Details on how the 1/32 flagged channels were chosen
- Phase calibrator and gain solution intervals
- Treatment of correlated noise between moment-map pixels in chi^2

## Analysis recipe

1. **Calibrate and flag ALMA data**: CASA calibration with WVR, Tsys, bandpass, flux, phase; flag antenna 14 and 120 bad channels in SPW 1 and 3; split  
  > "Antenna 14 was flagged during quality assurance (QA), leaving 31 antennas for the final data product." (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Image continuum and fit uniform disk to visibilities**: CLEAN image of line-free data; uvmodelfit uniform disk with chi^2 minimization  
  > "We run this task to fit a uniform disk model to the continuum data (the CO channels are *split* out)" (3.1 Continuum)
   - software: CASA
   - parameter: natural weighting; threshold 1/2 sigma_RMS  
  > "A threshold of $\frac{1}{2} \times \sigma_{RMS}$ and a natural weighting are used" (3.1 Continuum)
   - assumption: Flux uncertainty dominated by 10% absolute flux scale  
  > "The uncertainty in the flux is dominated by the uncertainty in the absolute flux scale, which is taken to be $10\%$." (3.1 Continuum)
   - fitting: uvmodelfit chi^2 minimization, single uniform disk  
  > "which fits single component models directly to the visibility data and selects the best fit through $\chi^{2}$ minimization" (3.1 Continuum)
   - validation: Compared with sum of cleaned flux to 3 sigma: within 15%  
  > "This is within $15\%$ of the flux density found by summing the total flux from the cleaned image down to the $3\sigma$ contour." (3.1 Continuum)
3. **Make CO moment and channel maps and measure line flux**: uvcontsub, zeroth/first moments; flux from summing zeroth moment above 3 sigma times number of beams  
  > "The total flux density of the CO given in Table [2](#data) is determined by summing the flux in the zeroth moment map down to $3 \times \sigma_{RMS}$ and multiplying by the number of beams." (3.2 Gas Disk)
   - software: CASA
   - parameter: channel spacing 0.5 km/s for channel maps  
  > "velocity channel spacing is chosen to be $0.50~\rm km~s^{-1}$ to include a slight oversampling" (3.2 Gas Disk)
   - fitting: _not stated_
   - validation: Consistent with integrating all channels within 10%  
  > "This value is consistent with integrating over all channels of the CO map to within $10\%$." (3.2 Gas Disk)
4. **Fit Keplerian disk model to CO velocity field**: Uniform Keplerian disk projected, convolved with beam, compared to first moment map in image domain  
  > "Model comparison is conducted in the image domain due to the high velocity resolution and signal-to-noise." (5.2 MCMC Modeling)
   - software: custom MCMC code
   - parameter: 3 chains, 100 thousand links each, ~1000 burn-in; sigma = 0.5 km/s  
  > "Each chain contains 100 thousand links of which about 1000 are needed for burn-in." (5.2 MCMC Modeling)
   - assumption: No inner cavity, temperature profile or line broadening in model  
  > "For simplicity, the inner cavity, temperature profile, and line broadening of CO (which is expected to be small) are not factored in to the model." (5.2 MCMC Modeling)
   - fitting: Metropolis-Hastings with Gibbs sampling; flat priors (Table 4); chi^2 likelihood; two parameters updated per trial  
  > "We assume flat prior distributions over the ranges given in Table [4](#mcmc_pri)." (5.2 MCMC Modeling)
   - validation: 3 chains converge to similar parameters; model agrees with data to ~10%  
  > "The most probable model typically shows agreement with the data to about 10%" (5.2 MCMC Modeling)
5. **Estimate mm dust and debris masses**: Optically thin single-size grain ring estimate; then 100-ring collisional cascade model 10-50 au, r^-1 surface density, s<50 km, matched to 3.8 mJy  
  > "In practice, the debris disk is divided into a series of rings (here 100), placed evenly between 10 and 50 au." (5.1 Debris/Dust Mass)
   - parameter: grain density 2.5 g/cm3, size 1 mm, T_star 10500 K, size distribution M_s ∝ s^-0.5  
  > "to have an internal density $\rho_i = 2.5~\rm g~cm^{-3}$ and size $s=1~\rm mm$" (5.1 Debris/Dust Mass)
   - assumption: Black-body grains, albedo 0, emissivity 1 (Q_nu=2s/lambda for large wavelengths); kappa=3 cm2/g equivalent  
  > "We note that this mass estimate is equivalent to $M  = \frac{d^2 F_\nu(\text Obs)}{\kappa_\nu B_\nu {(R)}}$ with $\kappa_\nu =3~\rm cm^2~g^{-1}$" (5.1 Debris/Dust Mass)
   - fitting: Total mass scaled to match observed flux  
  > "The total mass is then determined by requiring the model continuum flux density to match our observations." (5.1 Debris/Dust Mass)
   - validation: _not stated_
6. **Derive CO gas mass**: Optically thin LTE CO(3-2) mass from integrated flux with partition function  
  > "Taking a gas temperature of T $= 33$K, the minimum excitation temperature of the $J= 3$-2 line" (5.3 Gas Mass)
   - parameter: T = 33 K; A32 = 2.497e-6 Hz; Be = 57.635; distance 116 pc  
  > "$A_{32} = 2.497 \times 10^{-6}$ Hz is the Einstein absorption coefficient[^4] for the transition." (5.3 Gas Mass)
   - assumption: Optically thin, LTE; H2/CO = 1e4 for total gas  
  > "as we assumed the gas to be thin for the mass calculation" (5.3 Gas Mass)
   - fitting: _not stated_
   - validation: Predicted LTE CO(1-0) flux ~0.8 Jy km/s vs CARMA 1.6 ± 0.2, factor two  
  > "making the estimate good to about a factor of two" (5.4)

## Software

- **CASA** : Data reduction, split, CLEAN imaging, uvmodelfit, uvcontsub  
  > "Data were reduced using the Common Astronomy Software Applications (CASA) package (cite: casa_reference)." (2 Observations)
- **uvmodelfit** : Fit uniform disk to continuum visibilities  
  > "The dust distribution is constrained using CASA’s *uvmodelfit*" (3.1 Continuum)
- **Splatalogue** : CO spectroscopic constants  
  > "The spectral information for the CO molecule was obtained from the Splatalogue database" (footnote 4)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum flux density (870 um) | 3.8 | 0.4 | mJy | 2 | $3.8 \pm 0.4$ mJy |
| Continuum peak intensity | 1.74 | 0.24 | mJy/beam | 2 | $1.74 \pm 0.24$ mJy beam$^{-1}$ |
| CO(3-2) integrated flux | 15.7 | 1.6 | Jy km/s | 3 | $15.7 \pm 1.6$ Jy km s$^{-1}$ |
| Stellar mass (MCMC) | 2.39 | 95% interval [2.34, 2.43] | Msun | 4 | Mass \[M$_{\odot}$\]            / $2.39$        / $[2.34,2.43]$ |
| Inclination (MCMC) | 53.4 | 95% interval [52.5, 54.6] | deg | 4 | Inclination \[$^{\circ}$\]      / $53.4$        / $[52.5, 54.6]$ |
| Position angle (MCMC) | -3.36 | 95% interval [-3.78, -2.71] | deg | 4 | Position Angle \[$^{\circ}$\]   / \-$3.36$      / $[-3.78,-2.71]$ |
| System velocity (LSRK) | 6.04 | 95% interval [6.01, 6.06] | km/s | 4 | System Velocity \[km s$^{-1}$\] / $6.04$        / $[6.01, 6.06]$ |
| M sin(i) | 1.92 | 95% interval [1.89, 1.95] | Msun | 4 | Mass \[M$_{\odot}$sin(i)\]      / $1.92$        / $[1.89,1.95]$ |
| mm grain mass lower limit (R=10 au) | 0.04 | not stated | Earth masses | 5 | which yields a mm grain mass[^3] of $0.04~\rm M_{\oplus}$ |
| Debris mass s<50 km (10-50 au) | ~160 | not stated | Earth masses | 5 | we find that $M(s<{\rm 50~km})\sim 160~M_{\oplus}\frac{\rho_i}{\rm 2.5~g~cm^{-3}}$ |
| CO gas mass | 1.9e-3 | 0.2e-3 | Earth masses | 6 | gives M$_{\rm{CO}} =1.9 \pm 0.2 \times 10^{-3}~\rm M_{\bigoplus}$ |
| CO column density | 1.2e16 | 0.1e16 | cm^-2 | 6 | is $1.2 \pm 0.1 \times 10^{16} ~\rm cm^{-2}$ |
| Uniform-disk fit flux (uvmodelfit) | 3.78 | 0.23 | mJy | 2 | $3.78 \pm 0.23 ~\rm mJy$ |

## Qualitative findings

- CO emission shows a ~40% brighter western wing in channel maps, an asymmetry of unknown origin  
  > "the western wing is brighter than the eastern wing by $\sim 40\%$ in each channel" (6.1 Disk Asymmetry)
- ALMA continuum flux is a factor of ~3 below single-dish values, suggesting extended or low-surface-brightness dust  
  > "The continuum flux density found here is about a factor of three lower than that derived by single dish observations" (Summary)

## Claim tuples

- H: Is the CO velocity field consistent with Keplerian rotation around a ~2-3 Msun star? | E: MCMC fit of Keplerian model to first-moment map | R: M=2.39 Msun, i=53.4 deg, vsys=6.04 km/s | F: Gas is Keplerian around the star; mass scales with distance | **supported**
- H: Does the inner mm dust disk contain significant debris mass? | E: Collisional-cascade model matched to 3.8 mJy | R: ~160 Earth masses in s<50 km objects | F: Significant debris may lie between 10 and 50 au | **partially**
- H: Could the CO gas be second-generation? | E: Compare CO mass, photodissociation timescale (~120 yr) and required comet destruction rate | R: CO production ~17 Earth masses/Myr, ~170 Earth masses comet material per Myr | F: Second-generation gas is plausible but not demonstrated | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: High spatial and velocity resolution yields a well-constrained velocity field to compare with a Keplerian model  
  > "the high spatial and velocity resolution capabilities of ALMA yield a well-constrained velocity field" (5.2 MCMC Modeling)
- How they decided it was enough: _not stated_
- Limitation (authors): CO mass assumes optically thin LTE and could be larger by a factor of a few or more  
  > "the actual CO gas mass could be larger by a factor of a few" (5.3 Gas Mass)
- Limitation (authors): Debris mass depends strongly on assumed size distribution, density, albedo  
  > "A steeper (shallower) solid size distribution can lead to significantly larger (smaller) masses." (5.1 Debris/Dust Mass)
- Caveat (inferred, ours): Only one EB calibrated; short on-source time
- Caveat (inferred, ours): Keplerian model fit to first-moment map ignores cavity and beam smearing; chi^2 uses arbitrary sigma of 0.5 km/s and uncorrelated pixels
- Caveat (inferred, ours): Uniform-disk uvmodelfit is a crude dust model with no uncertainties on shape parameters
- Caveat (inferred, ours): Distance ambiguity (99 vs 116 pc) affects all linear scales and masses

## Reproducibility

- Data public (paper): ALMA cycle 1 data project cited; archive data  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA\[2012.1.00698.S\] ." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version and scripts
- Missing: CLEAN parameters and masks
- Missing: MCMC code
- Missing: moment-map thresholds and flagged channel ranges
- Data volume (inferred): ~10-30 GB raw for one cycle 1 band 7 EB
- Score (inferred): 3/5, Data public and recipe fairly simple with numeric results, but imaging and MCMC details and code are missing.
- Rediscovery candidate: yes, Public archival data, simple analysis with numeric tabulated results (flux, CO flux, Keplerian parameters).

## Links

- Method: Ford 2005 (cite: ford) (Metropolis-Hastings MCMC)
- Method: Perez et al. 2015 (cite: perez) (LTE optically thin CO mass)
- Method: Wyatt & Dent 2002 (cite: wyatt) (Grain temperature/emission model)
- Companion: Flaherty et al. 2016 (cite: flaherty) (CARMA and SMA observations of the same disk used for comparison)

## Checks

```json
{
 "quotes": 83,
 "quotes_ok": 83,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 86,
  "stated": 60,
  "rate": 0.698
 },
 "evidence_ok": true
}
```
