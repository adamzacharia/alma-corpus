# ALMA observations of the narrow HR 4796A debris ring

`2018MNRAS.475.4924K` | Monthly Notices of the Royal Astronomical Society 2018 | first author: Kennedy, Grant M. | arXiv: 1801.05429 | DOI: 10.1093/mnras/sty135

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: debris_disks
- Question: What are the radial and vertical structure of the HR 4796A debris ring at 880 um, is CO gas present, and what do these imply for dynamics and an interior planet?  
  > "we obtained ALMA observations with the goals of i) imaging the population of larger grains that dominate the emission at millimeter wavelengths, and ii) detecting or setting limits on any primordial or secondary CO gas." (Introduction)
- Target **HR 4796A**: coordinates delta = -40 deg (full coordinates not stated)  
  > "HR 4796A (HD 109573, HIP 61498, TWA 11A), an A0V star at 72.8 parsecs." (Introduction); z/distance 72.8 pc  
  > "HR 4796A (HD 109573, HIP 61498, TWA 11A), an A0V star at 72.8 parsecs." (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00032.S
- bands: Band 7 (880 um)  
  > "HR 4796A was observed over two hours by ALMA in band 7 (880$\mu$m) during Cycle 3 using 41 antennas" (2 Observations)
- frequencies and spectral setup: 3 continuum SPWs at 333.76, 335.70, 347.76 GHz (2 GHz each, 15.625 MHz channels); 1 SPW near 12CO J=3-2 (345.76 GHz), 1.875 GHz, 0.85 km/s resolution  
  > "The correlator had 3 spectral windows centered at frequencies of 333.76, 335.70 and 347.76 GHz each covering a bandwidth of 2 GHz" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15 to 1124 m  
  > "with baselines ranging from 15 to 1124 m (2015.1.00032.S)" (2 Observations)
- angular resolution: 0.16x0.18 arcsec (11.6x13.1 au) continuum, robust 0.5  
  > "This yields a synthesized beam of size 0.16$\times$0.18$''$, corresponding to 11.6$\times$13.1 au at the 72.8 pc distance" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: 31 uJy/beam continuum; 2 mJy/beam per 0.42 km/s channel in cube  
  > "The standard deviation obtained near the disk is $\sigma = 31 \mu$Jy beam$^{-1}$" (2 Observations); "The standard deviation of the noise in the datacube is 2 mJy beam$^{-1}$ in a 0.42 km s$^{-1}$ channel." (2 Observations)
- time on source: 50 minutes  
  > "Observations of the science target HR 4796A (50 minutes total integration time)" (2 Observations)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO J=3-2 (345.76 GHz)
- Other facility **SCUBA-2 (SONS)**: Comparison total flux 14.4 +/- 1.9 mJy  
  > "consistent with $14.4 \pm 1.9$mJy measured with SCUBA-2 (cite: 2013MNRAS.430.2513H)" (2.1 Basic continuum analysis)
- Other facility **SPHERE scattered light (Milli et al.)**: Scattered-light width and geometry for comparison  
  > "we use the results of (cite: 2017A&A...599A.108M), who measure a FWHM$_r$ of 7au using a power-law model" (4.4 Radial width and comparison with scattered light)
- External data: Stellar mass 2.18 Msun  
  > "an estimated stellar mass of 2.18 M$_{\odot}$ (cite: 1999A&AS..137..273G)" (2.2 Spectral data and CO) [from (cite: 1999A&AS..137..273G)]
- External data: Scattered-light power-law indices and FWHM_r of 7 au  
  > "the latter authors found $p_{\rm in} = 23$, and $p_{\rm out} = 13$ to $18$" (3.3 Power-law torus) [from (cite: 2017A&A...599A.108M)]
- External data: 9650K PHOENIX stellar model atmosphere  
  > "The stellar emission is taken as that of a 9650K PHOENIX model atmosphere (cite: 2005ESASP.576..565B)" (4.2.1 CO mass upper limit) [from (cite: 2005ESASP.576..565B)]

## Processing

### Calibration

- pipeline or manual: standard ALMA pipeline  
  > "through the standard pipeline provided by the ALMA observatory" (2 Observations)
- casa version: CASA 4.5.2  
  > "CASA software version 4.5.2" (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1107-4449 (bandpass J1427-4206)  
  > "The sources J1427-4206 and J1107-4449 were used as bandpass and flux calibrators, respectively" (2 Observations)
- flux scale uncertainty: 10% absolute calibration  
  > "the uncertainty is dominated by the 10% absolute calibration uncertainty" (2.1 Basic continuum analysis)
- self calibration: one round of phase-only self-calibration using CLEAN model; peak S/N 28 to 37  
  > "we used the CLEAN model to carry out one round of phase-only self-calibration." (2 Observations)

### Imaging

- task: CLEAN  
  > "using the CLEAN algorithm and Briggs weighting with a robust parameter of 0.5" (2 Observations)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5 (continuum); natural weighting for CO cube  
  > "then imaged the visibilities with natural weighting to cover the spectral region" (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub in visibility space  
  > "We first subtracted continuum emission in visibility space using the `uvcontsub` task within CASA" (2 Observations)
- line free channels: _not stated_
- primary beam correction: correction <1% in central 2 arcsec  
  > "the primary beam correction in this region is $<$1%" (2 Observations)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.16x0.18 arcsec continuum; 0.19x0.22 arcsec CO cube  
  > "datacubes with a synthesized beam size of $0.19 \times 0.22$$''$" (2 Observations)
- final rms: _not stated_

### Inherited from earlier work

- Visibility-fitting modelling method (radmc-3d image, FT, chi2)  
  > "The modelling method is the same as used by (cite: 2016MNRAS.460.2933M; 2017MNRAS.465.2595M)." (3 Continuum image Models) [from (cite: 2016MNRAS.460.2933M; 2017MNRAS.465.2595M)]
- Velocity-shifting filtering method for CO search  
  > "we used the filtering method developed by (cite: 2015MNRAS.447.3936M) as implemented by (cite: 2017ApJ...842....9M)" (2.2 Spectral data and CO) [from (cite: 2015MNRAS.447.3936M; 2017ApJ...842....9M)]
- NLTE CO excitation analysis with fluorescence  
  > "using an improved version of the non-local thermodynamic equilibrium (NLTE) analysis of (cite: 2015MNRAS.447.3936M) that now includes the effect of fluorescence excitation" (4.2.1 CO mass upper limit) [from (cite: 2015MNRAS.447.3936M); Matra et al. submitted]
- Eccentric disk density prescription  
  > "we use the simplified model of (cite: 2016ApJ...832...81P) to prescribe the dust density around an elliptical annulus" (3.4 Eccentric Gaussian Torus) [from (cite: 2016ApJ...832...81P)]

### Not stated but needed to reproduce (our reading)

- Line-free channels used in uvcontsub
- Image size, cell size, and clean threshold/mask
- Self-calibration solution interval
- Priors and bounds on MCMC parameters
- Model grid/radmc-3d settings (photon number, image resolution)
- Details of CO NLTE code (not public; Matra et al. submitted)
- Mass-loss rate calculation inputs (stellar luminosity, f) not fully listed

## Analysis recipe

1. **Image continuum and measure flux**: CLEAN imaging, phase self-cal, elliptical mask photometry  
  > "Using an elliptical mask with a semi-major axis of 1.75$''$ and semi-minor axis 0.4$''$ (the ratio derived for the dust ring below), we measure a total disk flux of $14.8 \pm 1.5$ mJy" (2.1 Basic continuum analysis)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared with SCUBA-2 flux; 180-degree rotation subtraction consistent with noise  
  > "This agreement suggests that the ALMA observations have not resolved out significant flux on scales larger than seen in Figure" (2.1 Basic continuum analysis)
2. **Search for CO emission**: uvcontsub, natural-weight cube, velocity-shifted filtering over pixels >5 sigma in continuum  
  > "In this framework only pixels where the disk is detected at $>$5$\sigma$ in the continuum are used" (2.2 Spectral data and CO)
   - software: CASA
   - assumption: CO co-located with dust; stellar mass 2.18 Msun  
  > "This method assumes the best-fit dust disk geometry derived in section [3](#s:model) and an estimated stellar mass of 2.18 M$_{\odot}$ (cite: 1999A&AS..137..273G)." (Spectral data and CO)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit disk models to visibilities**: radmc-3d optically thin torus models, FT to uv points, chi2 minimisation with MCMC; Gaussian, box, power-law, eccentric variants  
  > "we use the ensemble Markov-Chain Monte-Carlo (MCMC) method proposed by (cite: gw2010), as implemented by the `emcee` package" (3 Continuum image Models)
   - software: radmc-3d, emcee, CASA
   - parameter: 40 walkers, 1000 steps, ~100 burn-in; data averaged to 10 s and four channels per SPW; weights recomputed with statwt; reweighting 1/2.5  
  > "For most fitting runs we use 40 walkers and chains with 1000 steps" (3 Continuum image Models)
   - assumption: Dust size 10 um to 1 cm, q=11/6; 880 um opacity 0.17 m2/kg  
  > "such that the 880$\mu$m opacity is 0.17 m$^2$ kg$^{-1}$ (45 au$^2$ $M_\oplus^{-1}$)" (3 Continuum image Models)
   - fitting: emcee ensemble sampler; chi2 likelihood; priors not stated  
  > "The difference between the model and the data is then quantified by computing the $\chi^2$ goodness-of-fit metric over all visibility samples." (3 Continuum image Models)
   - validation: Delta chi2 and BIC model comparison; residual images  
  > "$BIC = \chi^2 + N_{\rm param} \ln(N_{\rm vis})$" (3.5 Summary of modelling)
4. **Convert CO flux limit to CO mass and ice fraction**: NLTE statistical equilibrium over electron density and kinetic temperature, optically thin; photodissociation timescale; steady-state ratio to collisional mass loss rate  
  > "We find a CO mass upper limit ranging between (1.2 to 3.7) $\times$ 10$^{-6}$ M$_{\oplus}$" (4.2.1 CO mass upper limit)
   - parameter: electron density 1e-3 to 1e12 cm-3; T 10 to 250 K  
  > "which we varied between 10$^{-3}$ and 10$^{12}$ cm$^{-3}$) and kinetic temperature (which we varied between 10 and 250 K)" (4.2.1 CO mass upper limit)
   - assumption: Electrons main collider; CO optically thin  
  > "we assume the main collider species to be electrons" (4.2.1 CO mass upper limit)
   - fitting: _not stated_
   - validation: Optical depth check tau<=0.4  
  > "we set an upper limit to the optical thickness of the $^{12}$CO J=3-2 line along the line of sight to Earth of $\tau_{\rm 345 GHz}\leq 0.4$" (4.2.2 Primordial origin of undetected CO excluded)
5. **Constrain interior planet from secular perturbations**: Resonance overlap, secular precession and crossing-time criteria with Laplace coefficients  
  > "The resonance-overlap and precession criteria, plus an approximate planet detection limit of 2 Jupiter-masses" (4.3.2 Planet constraints)
   - parameter: r0 = 79 au, e_f = 0.06, M_star = 2.18 Msun  
  > "Values assumed are $r_0 = 79$au, $e_f = 0.06$, and $M_\star = 2.18 M_\odot$" (7 Planet constraints)
   - assumption: Initial disk width ~5 au  
  > "Based on a rough maximum initial width of 5au" (4.3.2 Planet constraints)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.5.2: calibration, imaging, uvcontsub, statwt  
  > "Calibration and imaging of the visibility dataset was carried out using the CASA software version 4.5.2" (2 Observations)
- **radmc-3d** : generate model disk images  
  > "a disk image is first generated using `radmc-3d`" (3 Continuum image Models)
- **emcee** : MCMC fitting  
  > "as implemented by the `emcee` package" (3 Continuum image Models)
- **corner** : posterior plots (listed among packages used)  
  > "corner (cite: 2016JOSS.2016...24F)" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total disk flux at 880 um | 14.8 | 1.5 | mJy | 1 | we measure a total disk flux of $14.8 \pm 1.5$ mJy |
| 12CO J=3-2 integrated flux upper limit (3 sigma) | 25 | not stated | mJy km/s | 2 | yields an integrated line flux upper limit (3$\sigma$) of 25 mJy km s$^{-1}$ |
| Gaussian torus FWHM_r | 10 | 1 | au | 3 | FWHM$_r$ (au)               / 10    / 1 |
| Gaussian torus FWHM_h | 7 | 1 | au | 3 | FWHM$_h$ (au)               / 7     / 1 |
| Dust mass | 0.35 | 0.04 | Earth masses | 3 | $M_{\rm dust}$ ($M_\oplus$) / 0.35  / 0.04 |
| Ring radius r0 (Gaussian) | 78.6 | 0.2 | au | 3 | $r_0$ (au)                  / 78.6  / 0.2 |
| Position angle | 26.7 | 0.1 | deg | 3 | $\Omega$ ($^\circ$)         / 26.7  / 0.1 |
| Inclination | 76.6 | 0.2 | deg | 3 | $I$ ($^\circ$)              / 76.6  / 0.2 |
| Power-law index p | 24 | 2 | dimensionless | 3 | is $p = 24 \pm 2$, which corresponds to a FWHM of only 5au |
| CO mass upper limit adopted | 3.7e-6 | not stated | Earth masses | 4 | we therefore adopt 3.7 $\times$ 10$^{-6}$ M$_{\oplus}$ as the strict upper limit on the CO mass |
| CO photodissociation timescale | 8 | not stated | years | 4 | we derive a photodissociation timescale of eight years at the radial location of the ring’s centre |
| CO+CO2 ice mass fraction upper limit | <1.8 | not stated | percent | 4 | upper limit of $<$1.8% on the CO+CO$_2$ ice mass fraction |
| Dust mass loss rate | 26 | not stated | Earth masses per Myr | 0 | The estimated mass loss rate is 26 $M_\oplus$ Myr$^{-1}$. |

## Qualitative findings

- Ring is radially resolved and probably vertically resolved, with no significant asymmetry; a pair of 3 sigma residual blobs lie east near the semi-minor axis.  
  > "The ring is clearly radially resolved, and models where the disk is also vertically resolved yield the lowest $\chi^2$ values." (3.5 Summary of modelling)
- Mid-IR pericenter glow and scattered light interpretations conflict on the pericenter direction.  
  > "we highlight a conflict between the interpretations of mid-IR and scattered light observations" (5 Summary and Conclusions)

## Claim tuples

- H: Is the HR 4796A ring resolved radially and vertically at 880 um? | E: Visibility modelling with Gaussian, box, power-law tori and thin/narrow/unresolved variants, with BIC comparison | R: Radial FWHM 10 au, vertical FWHM 7 au; thin model has Delta chi2 = 21.8, unresolved 114.2 | F: Ring resolved radially and probably vertically, though sub-beam and treated with caution | **partially**
- H: Is CO gas present, and could it be primordial? | E: Filtered spectral search plus NLTE mass limit and photodissociation timescale | R: No detection; CO mass < 3.7e-6 Mearth; CO lifetime 8 yr | F: Any CO is not primordial; CO+CO2 ice fraction of a few percent or less | **supported**
- H: What planet could cause the ring eccentricity? | E: Secular precession, resonance overlap and detection-limit criteria | R: Planet more massive than Neptune, beyond 40 au | F: Constraints on interior planet mass and location | **partially**
- H: Does the ALMA ring width match the scattered light width? | E: Power-law torus fit compared with SPHERE profile | R: Power-law fit FWHM 5 au consistent with scattered light, but resolution limits comparison | F: Large grains appear as radially concentrated as small grains | **partially**

## Reasoning

- Why this data: Thermal emission from the disk had not been imaged at high resolution; goals were large grain structure and CO limits.  
  > "Thermal emission from HR 4796A’s disk has not been imaged at high spatial resolution at any wavelength" (Introduction)
- Why this method: _not stated_
- Alternative: Outer shepherding planet judged unlikely given direct-imaging limits; high radial optical depth implausible (f r0/h ~0.1).  
  > "which, aside from uncertainties in the conversion between mass and brightness, are not favoured by more recent direct imaging" (4.4 Radial width and comparison with scattered light)
- How they decided it was enough: _not stated_
- Limitation (authors): Vertical extent is smaller than the beam, so the vertical resolution conclusion is cautious; tests not exhaustive.  
  > "We remain cautious about the claim of vertically resolved structure because it is smaller than the beam size" (5 Summary and Conclusions)
- Limitation (authors): Dust mass has large systematic uncertainty from arbitrary opacity.  
  > "the mass is given largely for comparative purposes (i.e. it has a considerable systematic uncertainty)" (3 Continuum image Models)
- Caveat (inferred, ours): Vertical width conclusion rests on sub-beam signal and chosen parametric profiles
- Caveat (inferred, ours): Residual blobs may indicate unmodelled structure
- Caveat (inferred, ours): Constant reweighting factor of 2.5 may mask correlated errors
- Caveat (inferred, ours): Mass loss rate and ice fraction depend on the vertical-extent assumption

## Reproducibility

- Data public (paper): ALMA data cited with project code; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00032.S." (Acknowledgments)
- Products in archive: _not stated_
- Code: _not stated_
- Missing: Fit priors and parameter bounds
- Missing: Imaging gridding and clean parameters
- Missing: Line-free channels
- Missing: Unreleased NLTE code with fluorescence
- Missing: Radmc-3d configuration
- Data volume (inferred): ~20-50 GB raw (two 25-min blocks, 41 antennas, 4 SPWs)
- Score (inferred): 3/5, Data and general recipe given and public archive, but fit priors, imaging parameters and CO code details are missing.
- Rediscovery candidate: yes, Archival data with a numeric result table (ring radius, widths, mass) and a defined fitting recipe.

## Links

- Method: (cite: 2016MNRAS.460.2933M) (visibility modelling method)
- Method: (cite: 2015MNRAS.447.3936M) (CO filtering and NLTE method)
- Companion: (cite: 2017A&A...599A.108M) (SPHERE scattered light of HR 4796A)
- Related: SONS SCUBA-2 legacy survey

## Checks

```json
{
 "quotes": 76,
 "quotes_ok": 76,
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
  "facts": 84,
  "stated": 55,
  "rate": 0.655
 },
 "evidence_ok": true
}
```
