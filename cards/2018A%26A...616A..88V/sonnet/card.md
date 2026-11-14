# V1094 Scorpii: A rare giant multi-ringed disk around a T Tauri star

`2018A&A...616A..88V` | Astronomy and Astrophysics 2018 | first author: van Terwisga, S. E. | arXiv: 1805.03221 | DOI: 10.1051/0004-6361/201832862

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: What is the structure of the extended multi-ringed disk around V1094 Sco, and how common are such large disks in Lupus?  
  > "To characterize the structure of an extended, multi-ringed disk discovered serendipitously in the ALMA Lupus disk survey and put it in the context of the Lupus disk population." (abstract)
- Target **V1094 Sco**: coordinates 16h08m36.17s, -39d23m02.87s (J2000 phase center)  
  > "Throughout this article, we take a 150 pc distance to the source, consistent with the latest *Gaia* distance estimate of $153 \pm 1$ pc" (1 Introduction); "a J2000 phase center of 16h08m36.17s, -39$^{\circ}$23m02.87s." (3 Results and analysis); z/distance 150 pc (Gaia: 153 ± 1 pc)  
  > "Throughout this article, we take a 150 pc distance to the source, consistent with the latest *Gaia* distance estimate of $153 \pm 1$ pc" (1 Introduction); "a J2000 phase center of 16h08m36.17s, -39$^{\circ}$23m02.87s." (3 Results and analysis); distance from Gaia DR2 / Bailer-Jones et al. 2018  
  > "Throughout this article, we take a 150 pc distance to the source, consistent with the latest *Gaia* distance estimate of $153 \pm 1$ pc" (1 Introduction); "a J2000 phase center of 16h08m36.17s, -39$^{\circ}$23m02.87s." (3 Results and analysis)

## Data provenance

- ALMA projects: 2016.1.01239.S
- bands: Band 6 (234 GHz) and Band 7 (328 GHz)  
  > "ALMA observations in Band 6 at 234 GHz and Band 7 at 328 GHz at 0.3$''$ resolution" (abstract)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: Band 6: 2600-16700 m (44 antennae); Band 7: 1100-15100 m (41 antennae)  
  > "using 44 antennae and $2600 - 16700$ m baselines" (2 Observations and data reduction); "using 41 antennae and baselines between 1100 m and 15100 m" (2 Observations and data reduction)
- angular resolution: 0.25'' x 0.22'' (B6), 0.19'' x 0.18'' (B7)  
  > "the beam shapes become $0.25'' \times 0.22''$ and $0.19'' \times 0.18''$ in Band 6 and Band 7" (2 Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: rms 0.11 (Band 6) and 0.3 (Band 7) mJy/beam  
  > "rms noise values of 0.11 and 0.3 mJy beam$^{-1}$ respectively for V1094 Sco" (2 Observations and data reduction)
- time on source: 3 min (Band 6), 4.5 min (Band 7)  
  > "On-source integration times were 3 and 4.5 min in Band 6 and 7, respectively." (2 Observations and data reduction)
- observing dates: Band 6: 7 July 2017; Band 7: 21 May 2017  
  > "The Band 6 observations were performed on 7 July 2017" (2 Observations and data reduction)
- pi or archival as stated: Lupus completion survey, PI S.E. van Terwisga  
  > "(ALMA proposal 2016.1.01239.S, P.I.: S.E. van Terwisga)" (2 Observations and data reduction)
- Line: 12CO 2-1 (not stated)
- Other facility **VLT/X-Shooter**: stellar types and accretion properties  
  > "also have VLT/X-Shooter spectroscopy data available resulting in accurate stellar types and accretion properties" (1 Introduction)
- External data: Stellar luminosity and accretion rate of V1094 Sco  
  > "V1094 is a K6 star with a luminosity of 1.7 (1.95) L$_{\odot}$" (1 Introduction) [from (cite: alcala17)]
- External data: GQ Lup Band 7 fluxes used to recalibrate Band 7 flux scale  
  > "it is safe to compare these data with the (cite: macgregor17) results to re-calibrate the Band 7 fluxes" (2 Observations and data reduction) [from (cite: macgregor17)]
- External data: Temperature profile T(R)=99.3 K (R/1AU)^-0.68 from SED fit  
  > "$T(R) = 99.3\,\rm{K} \left( \frac{R}{1\,\rm{AU}} \right)^{-0.68}$" (3.2.1) [from (cite: tsukagoshi11)]
- External data: Lupus disk continuum radii and fractions (large disks, transition disks)  
  > "$8 \pm 3.0 \%$ of the full population (cite: vandermarel18)" (4.2) [from (cite: vandermarel18)]
- Simulation/model as data: DALI grid of 45 parametric disk models for dust temperature and raytraced images  
  > "used to perform dust radiative transfer calculations for a set of 45 disk models to obtain their dust temperatures" (3.2.1)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Band 6: J1427-4206; Band 7: J1517-2422  
  > "The Band 6 data were flux-calibrated using J1427-4206" (2 Observations and data reduction); "The Band 7 data used J1517-2422 as flux- and bandpass calibrator" (2 Observations and data reduction)
- flux scale uncertainty: Band 6 ~10%; Band 7 very uncertain, rescaled with GQ Lup by factor 1.3 ± 0.009  
  > "This gives a flux ratio of $F_{\rm{MacGregor\,et\,al.}} / F_{\rm{this\,work}} = 1.3 \pm 0.009$" (2 Observations and data reduction)
- self calibration: Phase-only; Band 6 down to 6 s, Band 7 down to 15 s  
  > "Phase-only self-calibration was used to maximize the $S/N$ of the observations in both bands." (2 Observations and data reduction); "for Band 7 we found useable solutions down to a $15$ s interval" (2 Observations and data reduction)

### Imaging

- task: CASA tclean  
  > "Imaging the continuum data using the `CASA` `tclean` task" (2 Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "Briggs weighting with a robust parameter of 0.5" (2 Observations and data reduction)
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
- final beam: 0.25'' x 0.22'' (B6), 0.19'' x 0.18'' (B7); circular 0.25'' for spectral index  
  > "the data were re-imaged with a circular, $0.25''$-radius beam, using only baselines with lengths between $17 - 1260$ k$\lambda$" (3.2)
- final rms: 0.11 mJy/beam (B6), 0.3 mJy/beam (B7)  
  > "rms noise values of 0.11 and 0.3 mJy beam$^{-1}$ respectively for V1094 Sco" (2 Observations and data reduction)

### Inherited from earlier work

- Aperture photometry with curve-of-growth method  
  > "identical to the method used in (cite: ansdell16; ansdell18)" (3 Results and analysis) [from (cite: ansdell16; ansdell18)]
- Intensity-profile model of Gaussians times cosine fit in the uv-plane  
  > "we model the intensity profile using an approach similar to that of (cite: zhang16)" (3.1) [from (cite: zhang16)]
- Parametric disk density structure for DALI models  
  > "The disk models themselves are based on the parametric disk density structure introduced in (cite: andrews11)" (Appendix B) [from (cite: andrews11)]

### Not stated but needed to reproduce (our reading)

- MCMC priors, number of steps and burn-in for the pymc uv fit
- CASA version
- Self-calibration solution intervals beyond the minimum and the reference models
- Line-free channels and spectral windows used for continuum
- Mask used in tclean and cleaning threshold
- Initial pymc ranges of rho_i
- Exact DALI grid parameters besides Table 1 (inner radius, dust opacities, stellar spectrum)
- Whether the Band 7 1.3 flux rescaling was applied to the spectral index maps and how the ratio of 1.3 was sourced in detail

## Analysis recipe

1. **Measure integrated continuum flux and disk geometry**: Curve-of-growth aperture photometry; imfit 2D Gaussian for PA, inclination, center  
  > "fluxes and errors here were derived using aperture photometry with a curve-of-growth method to set the aperture radius" (3 Results and analysis)
   - software: CASA
   - parameter: aperture radius 2.16''  
  > "inside of a $2.16''$ radius aperture, beyond which the image is entirely dominated by noise" (3 Results and analysis)
   - assumption: disk purely radially symmetric  
  > "Assuming the disk is indeed purely radially symmetric" (3 Results and analysis)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit radial intensity profile in uv-plane to locate rings and gaps**: Gaussian times cosine model Fourier transformed and fit to deprojected visibilities binned in 10 klambda; baselines < 700 klambda  
  > "fit to the derotated, deprojected data in the $u,v$-plane, after binning the data to $10$ k$\lambda$ bins" (3.1)
   - software: pymc
   - parameter: up to n=4 terms, 13 free parameters; rho ranges at least 100 klambda wide  
  > "we use up to $n=4$ terms, for a total of 13 free parameters" (3.1)
   - fitting: MCMC with pymc; inclination, PA, center initialised from imfit  
  > "A Monte Carlo Markov Chain (MCMC) fitting procedure was used to infer the best fit parameters, using the `pymc` package." (3.1)
   - validation: Checked burn-in, single posterior maximum, and re-ran with different initial inclination, PA and center  
  > "We confirmed their impact on the resulting fit was minimal by re-running the fitting code with different initial choices" (3.1)
3. **Derive radial spectral index profile**: Re-image both bands with common 0.25'' circular beam and uv range 17-1260 klambda; compute alpha per pixel after deprojection, radially average  
  > "calculating the value of $\alpha_{\rm{mm}}$ and its standard error in each pixel, and radially averaging these values" (3.2)
   - software: CASA
   - parameter: pixels with S/N < 2.5 masked  
  > "Pixels in both Band 6 and Band 7 with $S/N < 2.5$ were masked." (Appendix A)
   - assumption: 10% flux calibration error in both bands gives 0.42 error on alpha  
  > "assuming a $10\%$ flux calibration error is appropriate in both bands" (3.2)
   - fitting: _not stated_
   - validation: _not stated_
4. **Test cold optically thick inner disk with brightness temperature and models**: Brightness temperature of peak assuming optically thick; compared to Tsukagoshi SED model and DALI grid of 45 models imaged with 0.25'' beam  
  > "corresponds to a brightness temperature of only 12.9 K if we assume the emission is optically thick" (3.2.1)
   - software: DALI
   - parameter: Rc=250 AU, gamma=0.6, Mdisk fixed 0.1 Msun, h_c, psi, f_ls, chi grid  
  > "$R_c$ was set to 250 AU based on the Band 6 continuum image, and we fix $\gamma$ to $0.6$." (Appendix B)
   - assumption: gas-to-dust ratio 100; smooth disks without rings or gaps  
  > "reproducing the Band 6 continuum flux assuming a gas to dust ratio of 100" (Appendix B)
   - fitting: _not stated_
   - validation: Model peak brightness temperatures (median 12.7 K) compared to the observed value  
  > "The resulting raytraced images of the disk show peak brightness temperatures between 17 and 10 K and a median temperature of $12.7$ K" (3.2.1)
5. **Estimate occurrence rate of giant disks in Lupus**: Count disks with continuum radii up to ~300 AU among 95 Class II Lupus sources  
  > "In total, there are $95$ Class-II sources in the Lupus clouds." (4.2)
   - assumption: uniform 150 pc distance  
  > "All radial distances of the Lupus disks have been calculated assuming a uniform 150 pc distance" (4.1)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : tclean imaging and imfit  
  > "with the `imfit` task in CASA" (3 Results and analysis)
- **pymc** : MCMC fit of uv-plane intensity model  
  > "using the `pymc` package" (3.1)
- **DALI** : dust radiative transfer and midplane temperatures for model grid  
  > "physical-chemical disk modeling code `DALI` (cite: dali1; dali2)" (3.2.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Band 6 integrated flux | 180 | 14 | mJy | 1 | in Band 6 is $180 \pm 14$ mJy, while in Band 7 it is $390 \pm 19$ mJy |
| Band 7 integrated flux | 390 | 19 | mJy | 1 | in Band 6 is $180 \pm 14$ mJy, while in Band 7 it is $390 \pm 19$ mJy |
| Disk position angle | 109 | 1.9 | deg | 1 | PA$= 109 \pm 1.9 ^{\circ}$ and $i = 53 \pm 1.3 ^{\circ}$ |
| Disk inclination | 53 | 1.3 | deg | 1 | PA$= 109 \pm 1.9 ^{\circ}$ and $i = 53 \pm 1.3 ^{\circ}$ |
| Gap 1 and Gap 2 radii | 100 and 170 | 6 and 13 | AU | 2 | while the gaps are found at $100 \pm 6$ AU and $170 \pm 13$ AU |
| Ring 1 and Ring 2 radii | 130 and 220 | 9 and 16 | AU | 2 | the locations of the bright rings become $130 \pm 9$ AU and $220 \pm 16$ AU |
| Core characteristic radius | 35 | 2 | AU | 2 | having a characteristic radius of $35 \pm 2$ AU |
| Spectral index in inner disk | 2.09 | 0.03 (statistical; 0.42 absolute flux calibration) | dimensionless | 3 | consistent with $\alpha_{\rm{mm}} = 2.09 \pm 0.03$, increasing outward |
| Spectral index in first gap (100 AU) | 3.0 | 0.2 | dimensionless | 3 | towards $3.0 \pm 0.2$ in the first gap at $100$ AU |
| Spectral index in first ring (130 AU) | 2.3 | 0.3 | dimensionless | 3 | to $2.3 \pm 0.3$ in the first ring at $130$ AU |
| Central brightness temperature | 12.9 | not stated | K | 4 | corresponds to a brightness temperature of only 12.9 K if we assume the emission is optically thick |
| DALI midplane temperature at 20 AU | 20 | 4 | K | 4 | we find midplane temperatures of $20 \pm 4$ K at this radius |
| Occurrence rate of giant disks in Lupus | 2.1 | 1.5 | % | 5 | This implies an occurrence rate of $2.1 \pm 1.5 \%$ for these largest disks. |

## Qualitative findings

- Snow lines are excluded as drivers of the rings and gaps; dead zone gives at most one ring; GI or planets remain possible  
  > "the midplane dust temperature at the ring locations is too low for snow lines to be a valid explanation" (5 Conclusions)

## Claim tuples

- H: V1094 Sco hosts a giant multi-ringed disk | E: Band 6/7 continuum imaging and uv-plane fit | R: Rings at 130 and 220 AU, gaps at 100 and 170 AU, emission to 300 AU | F: Giant multi-ringed disk, similar in size to IM Lup | **supported**
- H: The inner disk is cold and optically thick | E: Spectral index profile, brightness temperature, comparison with SED and DALI models | R: alpha=2.09, Tb=12.9 K, models give median 12.7 K | F: Consistent with cold optically thick core | **supported**
- H: Snow lines drive the rings and gaps | E: Compare ring locations with midplane temperatures | R: Rings far outside the ~20 AU CO snowline | F: Snow lines excluded | **supported**
- H: Such large disks are rare in Lupus | E: Count disks with radius >200 AU among 95 Class II sources | R: 2.1 ± 1.5% | F: Giant disks are rare | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: uv-plane fit uses few parameters and no temperature or dust model assumptions  
  > "it does not rely on a model-dependent temperature profile or assumptions about the dust properties" (3.1)
- Alternative: Band 7 data not used as basis for structure analysis because of higher phase noise  
  > "Therefore we choose the Band 6 data as the basis for the subsequent analysis." (3 Results and analysis)
- How they decided it was enough: _not stated_
- Limitation (authors): Band 7 absolute flux very uncertain, giving 0.42 systematic error on alpha  
  > "its flux — and therefore the flux calibration of all Band 7 data — is very uncertain" (2 Observations and data reduction)
- Limitation (authors): Gap and ring widths hard to constrain with the fit  
  > "It is difficult to constrain the width of the gaps and rings from this fit" (3.1)
- Caveat (inferred, ours): Flux scale of Band 7 rests on a single GQ Lup comparison, so alpha profile is uncertain
- Caveat (inferred, ours): Optically thick inference rests on a 0.25'' beam and smooth model temperatures
- Caveat (inferred, ours): Occurrence rate from 2 of 95 objects has small-number statistics and distance assumption
- Caveat (inferred, ours): Only 3-4.5 min of data, with a ripple in Band 6 from uv coverage

## Reproducibility

- Data public (paper): ALMA project 2016.1.01239.S cited; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.01239.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: pymc priors and sampler settings
- Missing: CASA version and self-calibration details
- Missing: DALI full setup
- Data volume (inferred): ~10-50 GB for two short EBs including line spectral windows
- Score (inferred): 5/5, Data and main steps stated, but MCMC priors, CASA version and several imaging details are missing.
- Rediscovery candidate: yes, Data are from a standard ALMA project, the recipe is mostly specified and the results are numeric (ring/gap radii, alpha).

## Links

- Method: (cite: zhang16) (uv-plane intensity profile model)
- Method: (cite: ansdell16; ansdell18) (Lupus survey flux measurement method)
- Companion: (cite: ansdell18) (Lupus survey data including CO line fluxes)
- Companion: (cite: vandermarel18) (Lupus disk sizes and transition disk statistics)
- Related: ALMA Lupus disk survey
- Related: Lupus completion survey

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
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 52,
  "rate": 0.634
 },
 "evidence_ok": true
}
```
