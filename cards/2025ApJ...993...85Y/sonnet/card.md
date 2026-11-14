# Peculiar Disk Substructures Associated with the Young Eruptive Star EX Lupi

`2025ApJ...993...85Y` | The Astrophysical Journal 2025 | first author: Yamaguchi, Masayuki | arXiv: 2508.14367 | DOI: 10.3847/1538-4357/adff50

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: Does the disk of the EXor EX Lupi host resolved substructures, and how do they relate to the disk surface/thermal structure and to episodic accretion?  
  > "However, those studies lacked the spatial resolution needed to directly image small-scale disk substructures that could link morphology to accretion behavior." (Introduction)
- Target **EX Lupi**: coordinates 16h03m5.476s, -40d18'25.764" (ICRS, Gaia-based, epoch of ALMA)  
  > "located at a distance of $154.7 \pm 0.4$ pc (cite: Gaia2023)" (Introduction); "The resulting ICRS coordinates for EX Lupi are ($16^{\rm h}03^{\rm m}5^{\rm s}.476$, $-40^{\circ} 18' 25.764\ensuremath{''}$)." (footnote 3); z/distance 154.7 ± 0.4 pc  
  > "located at a distance of $154.7 \pm 0.4$ pc (cite: Gaia2023)" (Introduction); "The resulting ICRS coordinates for EX Lupi are ($16^{\rm h}03^{\rm m}5^{\rm s}.476$, $-40^{\circ} 18' 25.764\ensuremath{''}$)." (footnote 3); distance from Gaia DR3 (Gaia2023)  
  > "located at a distance of $154.7 \pm 0.4$ pc (cite: Gaia2023)" (Introduction); "The resulting ICRS coordinates for EX Lupi are ($16^{\rm h}03^{\rm m}5^{\rm s}.476$, $-40^{\circ} 18' 25.764\ensuremath{''}$)." (footnote 3)

## Data provenance

- ALMA projects: 2017.1.00388.S
- bands: Band 3 (92.95 GHz, 3.2 mm) and Band 4 (152.95 GHz, 2.0 mm)  
  > "resulting in an average frequency of 92.95 GHz (3.2 mm) for Band 3 and 152.95 GHz (2.0 mm) for Band 4." (2.1 Data Reduction)
- frequencies and spectral setup: continuum, four 1.88 GHz-wide spectral windows  
  > "The correlators are configured for continuum observations to cover four 1.88 GHz-wide spectral windows." (2.1 Data Reduction)
- continuum bandwidth: _not stated_
- arrays: 12 m array, C40-9 configuration  
  > "The observations were performed with a 12 m array consisting of a C40-9 antenna configuration with the baseline length extending from 113 to 13,894 m." (2.1 Data Reduction)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: CLEAN beams 0.103"x0.068" (B3), 0.064"x0.042" (B4); PRIISM effective 47x39 mas (B3), 47x35 mas (B4)  
  > "The final restored CLEAN images provided a beam size of $0.103\ensuremath{''} \times 0.068\ensuremath{''} ~ (\rm PA = -77^{\circ})$ for Band 3" (2.2 Self-calibration and CLEAN Imaging)
- max recoverable scale: 1.18" (Band 3), 0.66" (Band 4)  
  > "The MRSs for Bands 3 and 4 provided $1.18\ensuremath{''}$ and $0.66\ensuremath{''}$, respectively." (2.1 Data Reduction)
- sensitivity: rms 36 uJy/beam (B3), 46 uJy/beam (B4) in CLEAN images  
  > "for Bands 3 and 4 were $36~\mu \rm Jy~beam^{-1}$ and $46~\mu \rm Jy~beam^{-1}$, respectively." (2.2 Self-calibration and CLEAN Imaging)
- time on source: _not stated_
- observing dates: 2017 Nov 6 (Band 4), 2017 Nov 7 (Band 3)  
  > "The observations were performed in 2017 November 6 (Band 4) and 2017 November 7 (Band 3)" (2.1 Data Reduction)
- pi or archival as stated: PI Hauyu Baobab Liu (project 2017.1.00388.S)  
  > "project code: 2017.1.00388.S, PI: Hauyu Baobab Liu" (2.1 Data Reduction)
- Other facility **VLT/SPHERE**: H-band polarimetric Q_phi scattered-light image from Rigliaco et al. 2020, used for disk-surface geometry  
  > "obtained with SPHERE at the VLT from (cite: rigliaco_circumstellar_2020)" (4.1 Scattered-light Asymmetry of Disk Surface)
- Other facility **Gaia DR3**: parallax distance and stellar position  
  > "central stellar position determined using Gaia DR 3 parallax measurements (cite: Gaia2023)" (3.1.1 Detailed Geometry)
- External data: Stellar luminosity 0.43 Lsun (quiescent)  
  > "has a quiescent stellar luminosity of $0.43~L_{\odot}$ (cite: Wang2023ApJ)" (Introduction) [from (cite: Wang2023ApJ)]
- External data: Dynamical stellar mass 0.5 Msun  
  > "a dynamical stellar mass of $0.5~M_{\odot}$ (cite: hales_circumstellar_2018)" (Introduction) [from (cite: hales_circumstellar_2018)]
- External data: Flaring index beta = 1.09 from SED fit  
  > "flaring index $\beta (= 1.09)$ determined from a SED fit using a flared disk model (cite: sipos_ex_2009)" (4.2 Shape of Disk Surface) [from (cite: sipos_ex_2009)]
- External data: SPHERE H-band Q_phi image  
  > "obtained with SPHERE at the VLT from (cite: rigliaco_circumstellar_2020)" (4.1 Scattered-light Asymmetry of Disk Surface) [from (cite: rigliaco_circumstellar_2020)]

## Processing

### Calibration

- pipeline or manual: CASA pipeline scripts provided by ALMA Regional Centers  
  > "The data were initially calibrated with the $\tt CASA$ pipeline reduction scripts provided by the ALMA Regional Centers." (2.1 Data Reduction)
- casa version: CASA 6.5.0 (for self-cal CLEAN)  
  > "on $\tt CASA$ version 6.5.0" (2.2 Self-calibration and CLEAN Imaging)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: B3: J1427-4206; B4: J1617-5848  
  > "For the Band 3 dataset, the absolute flux scale and bandpass shape were corrected with J1427-4206" (2.1 Data Reduction)
- flux scale uncertainty: _not stated_
- self calibration: phase-only, solint=inf, CLEAN model, robust 0.5, CASA 6.5.0  
  > "we apply a phase-only self-calibration ($\tt calmode = p$) with a CLEAN model as a reference calibrator for each dataset." (2.2 Self-calibration and CLEAN Imaging)

### Imaging

- task: tclean (CLEAN) for self-cal and comparison; PRIISM for science images  
  > "local peak of the inner arc emission around the center of the $\tt tclean$ image (hereafter CLEAN image)" (2.1 Data Reduction)
- deconvolver: multi-frequency synthesis with multi-scale, scales [0,1,3] x theta_cl  
  > "with scale parameters of $[0, 1, 3] \times \theta_{\rm cl}$ (where $\theta_{\rm cl}$ is the CLEAN beam size)" (2.2 Self-calibration and CLEAN Imaging)
- weighting robust: Briggs robust = 0.5  
  > "we employed a Briggs robustness parameter of 0.5 for the imaging" (2.2 Self-calibration and CLEAN Imaging)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Band 4 restored image smoothed to Band 3 resolution for spectral index  
  > "the restored Band 4 image is smoothed to match the spatial resolution of the Band 3 image." (3.2.2 Spectral Index)
- final beam: PRIISM restored: 92x66 mas PA -84 (B3); 60x38 mas PA 87 (B4)  
  > "with a beam size of $92 \times 66 ~ \rm mas ~ (\rm PA = -84^{\circ})$ for Band 3 and $60 \times 38 ~ \rm mas ~ (\rm PA = 87^{\circ})$ for Band 4." (9.3 Restored Image)
- final rms: 37 uJy/beam (B3), 48 uJy/beam (B4) restored PRIISM  
  > "derived as $37~\mu \rm Jy~\rm beam^{-1}$ and $48~\mu \rm Jy~\rm beam^{-1}$, respectively." (9.3 Restored Image)

### Inherited from earlier work

- PRIISM l1+TSV with 10-fold cross-validation scheme  
  > "cross-validation (CV) scheme as illustrated in (cite: yamaguchi_super-resolution_2020)" (2.3 PRIISM Imaging) [from (cite: yamaguchi_super-resolution_2020)]
- Ellipse fit of ring done as in earlier work  
  > "by performing an ellipse fit in the same manner as in (cite: yamaguchi_alma_2021)" (3.1.1 Detailed Geometry) [from (cite: yamaguchi_alma_2021)]
- Curve-of-growth disk radius method  
  > "using the curve-of-growth method, following the approach of (cite: yamaguchi_alma_2024)" (5.2 Radial Extent of the Dust Disk) [from (cite: yamaguchi_alma_2024)]
- Point-source injection for effective resolution  
  > "using the point-source injection method outlined in (cite: yamaguchi_alma_2021)" (9.2 Effective Spatial Resolution) [from (cite: yamaguchi_alma_2021)]

### Not stated but needed to reproduce (our reading)

- PRIISM pixel size, image size and PRIISM version
- Exact CLEAN cell size, image size, masks, threshold and iterations
- Self-calibration spectral/time details and number of rounds
- Flux calibration scale uncertainty
- Whether the SPHERE image reduction products are public/how to obtain them
- Radial bin width and aperture settings for curve of growth
- Exact pixel region and weighting for the inner-arc spectral index

## Analysis recipe

1. **Calibrate, align and self-calibrate**: CASA pipeline calibration, phase-center shifting with fixvis/fixplanets, phase-only self-cal with CLEAN model  
  > "we apply a phase-only self-calibration ($\tt calmode = p$) with a CLEAN model as a reference calibrator for each dataset." (2.2 Self-calibration and CLEAN Imaging)
   - software: CASA
   - parameter: solint=inf, robust 0.5  
  > "CASA task $\tt gaincal$ to average whole scans ($\tt solint = inf$)" (2.2 Self-calibration and CLEAN Imaging)
   - fitting: _not stated_
   - validation: SNR improvement of 1.2 over non-self-calibrated image  
  > "which reached slight improvements of 1.2 in SNR compared with a non-self-calibrated CLEAN image" (2.2 Self-calibration and CLEAN Imaging)
2. **Super-resolution imaging with PRIISM**: l1+TSV regularized maximum likelihood with 10-fold CV over a grid of (Lambda_l, Lambda_tsv); restored image via beam convolution plus residuals  
  > "To select a pair of $(\Lambda_{l}, \Lambda_{tsv})$ for the optimal image, we employ a 10-fold CV approach." (2.3 PRIISM Imaging)
   - software: PRIISM
   - parameter: B3 (1e5, 3e12); B4 (7e4, 3e12)  
  > "($10^{5}$, $3\times10^{12}$) for Band 3 and ($7\times10^{4}$, $3\times10^{12}$) for Band 4" (2.3 PRIISM Imaging)
   - fitting: minimum cross-validation error selects optimum  
  > "The model with minimum cross-validation error (CVE) is set to the optimal one" (2.3 PRIISM Imaging)
   - validation: reduced chi-square near unity in visibility domain; point-source injection for effective resolution  
  > "the PRIISM model images yield $\tilde{\chi}^{2}$ values around unity, similar to the CLEAN models" (9.1 Goodness of Fit to Observations)
3. **Fit outer ring geometry and width**: ellipse fit for PA/inclination; Gaussian fit to deprojected radial profile with emcee; deconvolve beam  
  > "we employed a Markov Chain Monte Carlo (MCMC) fitting procedure using the `emcee` sampler" (3.1.1 Detailed Geometry)
   - software: emcee
   - parameter: 100 walkers, 500 steps, 250 burn-in  
  > "ran 100 walkers for 500 steps, discarding the initial 250 steps as burn-in" (3.1.1 Detailed Geometry)
   - assumption: deprojected outer ring is circular; Gaussian ring and beam  
  > "Assuming that the deprojected outer ring is circular" (3.1.1 Detailed Geometry)
   - fitting: emcee, uniform priors, median and 16/84 percentiles  
  > "We adopted uniform (flat) priors" (3.1.1 Detailed Geometry)
   - validation: inclination compared with CO kinematic value of Hales et al.  
  > "in reasonable agreement with the $38^{\circ} \pm 4^{\circ}$ derived from a Keplerian model rotation" (3.1.1 Detailed Geometry)
4. **Inner arc elongation and spectral index**: PA profile of deprojected arc gives arc length/width; spectral index averaged over pixels >3 sigma in both bands  
  > "we calculate the average spectral index using the following equation" (3.2.2 Spectral Index)
   - parameter: PA sampling 10 deg; 3 sigma threshold  
  > "we sample the $k$th data point at intervals of $\Delta \theta = 10^{\circ}$" (3.2.1 Elongation)
   - assumption: arc coplanar with outer ring (same inclination and PA)  
  > "under the assumption that the inner arc and the outer ring are aligned on the disk midplane" (3.2.1 Elongation)
   - fitting: _not stated_
   - validation: arc offset significance via positional accuracy relation  
  > "This calculation yields positional uncertainties of $5-10$ mas in both Band 3 and Band 4 images" (3.2 Inner Arc)
5. **Disk-surface height from SPHERE ellipse**: Sobel edge detection on smoothed Q_phi image, ellipse fit with emcee, height from center offset H=Oc/sin(i)  
  > "transformed into an edge-enhanced image using the Sobel operator implemented in $\tt scikit-image$" (10 Elliptical Fitting Procedure)
   - software: scikit-image, scipy, emcee
   - parameter: 500 walkers, 2000 steps, 500 burn-in; PA fixed 51.7 deg; Gaussian smoothing FWHM 0.2"  
  > "utilizing 500 walkers with 2000 steps each, discarding the first 500 steps as burn-in" (10 Elliptical Fitting Procedure)
   - assumption: circular, azimuthally symmetric disk; beta=1.09  
  > "under the assumption that the disk is circular and azimuthally symmetric" (4.2 Shape of Disk Surface)
   - fitting: Gaussian log-likelihood with local scatter, uniform priors  
  > "a uniform prior is applied with the following ranges" (10 Elliptical Fitting Procedure)
   - validation: compared with Dullemond & Dominik flared models and Avenhaus et al. relation  
  > "consistent with that expected from a theoretical flaring disk model for T Tauri stars" (4.2 Shape of Disk Surface)
6. **Temperature profile, scale height, trapping ratio**: passively irradiated flared disk energy balance gives T_d(r); h_p=c_s/Omega; ratio of deconvolved width to h_p  
  > "The temperature at each radius $r$ is determined by balancing the stellar irradiation" (5.1 Thermal Structure of the Disk)
   - assumption: mu=2.3, M*=0.5 Msun, L*=0.43 Lsun, stellar heating dominant  
  > "The mean molecular weight is assumed to be $\mu = 2.3$ in atomic units" (3.1.2 Dust Trapping)
   - fitting: _not stated_
   - validation: disk-averaged T compared with T Tauri scaling (~20 K)  
  > "consistent with the disk$-$averaged temperature ($\langle T_{\mathrm{d}} \rangle  \approx 20$ K)" (5.1 Thermal Structure of the Disk)
7. **Dust disk radius**: curve of growth on deprojected Band 4 PRIISM model, radius at 95% of total flux  
  > "The dust disk radius $r_{\rm dust}$ is then defined as the radius where $0.95 \times F_{\nu} = F_{\nu}(r)$." (5.2 Radial Extent of the Dust Disk)
   - fitting: _not stated_
   - validation: compared with other EXor and compact M/K star disks  
  > "The measured radius also aligns well with compact dust radii observed in other EXor systems" (5.2 Radial Extent of the Dust Disk)

## Software

- **CASA** 6.5.0: calibration, self-calibration, tclean, fixvis/fixplanets  
  > "on $\tt CASA$ version 6.5.0" (2.2 Self-calibration and CLEAN Imaging)
- **PRIISM** : sparse-modeling super-resolution imaging  
  > "we employ $\tt PRIISM$[^1]" (2.3 PRIISM Imaging)
- **emcee** : MCMC fits of ring profile and scattered-light ellipse  
  > "using the `emcee` sampler" (3.1.1 Detailed Geometry)
- **scikit-image** : Sobel edge enhancement  
  > "using the Sobel operator implemented in $\tt scikit-image$" (10 Elliptical Fitting Procedure)
- **SciPy** : Nelder-Mead minimization for ellipse distance  
  > "the optimization was performed using the `scipy.optimize.minimize` routine with the Nelder-Mead method" (10 Elliptical Fitting Procedure)
- **AnalysisUtilities** 2.6: listed in software section  
  > "AnalysisUtilities (cite: hunter_2023)" (Software)
- **Astropy** : listed in software section  
  > "Astropy (cite: astropy2022)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Outer ring inclination | 42.6 | 2.4 | deg | 3 | an inclination of $42^{\circ}.6 \pm 2^{\circ}.4$ |
| Outer ring position angle | 51.7 | 2.2 | deg | 3 | yielding a PA of $51^{\circ}.7 \pm 2^{\circ}.2$ |
| Ring radius | 28.59 | 0.04 | au | 3 | $r_{\rm ring} = 28.59\pm 0.04 ~\rm au$ |
| Deconvolved ring width | 1.62 | 0.04 | au | 3 | deconvolved ring width of $\hat{w}_{d} = 1.62\pm 0.04$ au |
| Ring width / pressure scale height | 0.95 | 0.04 | dimensionless | 6 | $\hat{w}_{\rm d}/h_{\rm p}(r_{\rm ring}) = 0.95 \pm 0.04$ |
| Ring integrated flux Band 3 | 1.0 | 0.2 | mJy | 2 | are $1.0\pm0.2$ mJy in Band 3 and $2.1\pm0.4$ mJy in Band 4 |
| Ring integrated flux Band 4 | 2.1 | 0.4 | mJy | 2 | are $1.0\pm0.2$ mJy in Band 3 and $2.1\pm0.4$ mJy in Band 4 |
| Inner arc elongation | >7 | lower limit | dimensionless | 4 | These calculations yield a lower limit of $\varepsilon > 7$ for the elongation |
| Inner arc spectral index | 2.0 | 0.5 | dimensionless | 4 | This calculation yields $\bar{\alpha}_{\rm mm}=2.0\pm0.5$. |
| Disk surface height at 77 au | 8.2 | 2.3 | au | 5 | $H_{s}(r_{\rm ridge}) = 8.2 \pm 2.3$ au at $r_{\rm ridge} = 77 \pm 3$ au |
| Disk-averaged temperature | 18 | 1 | K | 6 | The resulting average disk temperatures yields $18\pm1$ K |
| Dust disk radius | 34 | 3 | au | 7 | $r_{\rm dust} = 0.22\ensuremath{''}\pm 0.02\ensuremath{''}$ ($34\pm3$ au) |
| Ring-star center offset | ~5 | not stated | au | 3 | The center of the ellipse has an offset of $\sim 5$ au |

## Qualitative findings

- Inner arc casts shadow seen in SPHERE scattered light, anti-aligned with the arc  
  > "The anticorrelation between the submillimeter continuum and the scattered light suggests that the inner arc casts a shadow onto the outer disk surface" (4.1 Scattered-light Asymmetry of Disk Surface)

## Claim tuples

- H: EX Lupi's dust disk has resolved substructure | E: PRIISM imaging of Band 3 and 4 continuum | R: Narrow ring at 28.6 au and crescent inner arc within 10 au | F: First detection of both substructures | **supported**
- H: The outer ring is a dust trap | E: Compare deconvolved width to pressure scale height | R: w/h_p = 0.95 ± 0.04 | F: Moderately effective dust trapping | **partially**
- H: Inner arc shadows the outer disk surface | E: Compare ALMA arc location with SPHERE asymmetry | R: Scattered light concentrated NW, arc at SE | F: Arc casts a shadow | **partially**
- H: Disk thermal structure resembles T Tauri disks | E: Flaring angle from SPHERE+ALMA geometry, energy balance | R: Mean T = 18±1 K | F: Structurally mature disk with T Tauri-like temperature | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Sparse modeling gives higher effective resolution and suppresses patchy CLEAN artifacts  
  > "achieves improved effective spatial resolution compared to CLEAN" (2.3 PRIISM Imaging)
- Alternative: Multi-scale CLEAN images gave patchy structure; PRIISM preferred  
  > "The CLEAN model image exhibits a patchy pattern" (9.1 Goodness of Fit to Observations)
- How they decided it was enough: _not stated_
- Limitation (authors): Ring clumps only 3-5 sigma; higher SNR needed to confirm the SW clump  
  > "observations with higher SNR are required to confirm or reject the presence of this clump" (3 Peculiar Disk Structures)
- Limitation (authors): Low spectral index evidence tentative  
  > "though the evidence remains tentative" (6.1 Origin of the Inner Arc)
- Caveat (inferred, ours): Ring is only marginally resolved; width depends on Gaussian deconvolution
- Caveat (inferred, ours): Super-resolution features may be affected by regularization choices
- Caveat (inferred, ours): Temperature depends on assumed beta and passive heating, with uncertainty not fully propagated
- Caveat (inferred, ours): Quiescent single-epoch data; no independent confirmation of companions

## Reproducibility

- Data public (paper): PRIISM public; ALMA data from project 2017.1.00388.S (archival)  
  > "is a public ALMA imaging tool based on sparse modeling, available at <https://github.com/tnakazato/priism>" (footnote 1)
- Products in archive: _not stated_
- Code: PRIISM is public on GitHub; no analysis code released  
  > "available at <https://github.com/tnakazato/priism>" (footnote 1)
- Missing: PRIISM pixel/image settings
- Missing: SPHERE image reduction file
- Missing: CLEAN cell/mask settings
- Data volume (inferred): ~20-50 GB for two long-baseline execution blocks
- Score (inferred): 3/5, Public data and main numeric steps are stated, but PRIISM and imaging configuration details are partly missing.
- Rediscovery candidate: yes, Data are archival, and the PRIISM procedure plus ring-fit and numeric results are fairly well specified.

## Links

- Method: (cite: Nakazato2020; Nakazato_priism_2020) (PRIISM software)
- Method: (cite: yamaguchi_super-resolution_2020) (l1+TSV with CV imaging scheme)
- Method: (cite: yamaguchi_alma_2024) (curve of growth and chi-square evaluation)
- Companion: (cite: hales_circumstellar_2018) (earlier ALMA CO and continuum observations of EX Lupi)
- Companion: (cite: rigliaco_circumstellar_2020) (SPHERE data source)

## Checks

```json
{
 "quotes": 94,
 "quotes_ok": 94,
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
  "facts": 95,
  "stated": 72,
  "rate": 0.758
 },
 "evidence_ok": true
}
```
