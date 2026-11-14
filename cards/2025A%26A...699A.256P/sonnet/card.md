# The ALMA-CRISTAL survey: Extended [CII] emission in an interacting galaxy system at z ∼ 5.5

`2025A&A...699A.256P` | Astronomy and Astrophysics 2025 | first author: Posses, A. | arXiv: 2403.03379 | DOI: 10.1051/0004-6361/202449843

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What are the morphology and kinematics of the cold gas, star-forming and stellar components of CRISTAL-05/HZ3 at z=5.54, and what is the origin of its extended [CII] emission?  
  > "we explore the morphology and kinematics of the cold gas, star-forming, and stellar components in the star-forming main-sequence galaxy CRISTAL-05/HZ3, at z = 5.54." (abstract)
- Target **CRISTAL-05 (HZ3)**: coordinates +10:00:29.86, +02:13:02.19  
  > "Center | +10:00:29.86, +02:13:02.19" (Table 2); "$z_{\mathrm{[CII]}}$$^{a}$                   |    5.5420 $\pm$ 0.0005" (Table 2); z/distance z_[CII] = 5.5420 ± 0.0005 (5.961 kpc/" at the source)  
  > "Center | +10:00:29.86, +02:13:02.19" (Table 2); "$z_{\mathrm{[CII]}}$$^{a}$                   |    5.5420 $\pm$ 0.0005" (Table 2); distance from [CII] redshift from these data; flat ΛCDM H0=70, Ωm=0.3  
  > "Center | +10:00:29.86, +02:13:02.19" (Table 2); "$z_{\mathrm{[CII]}}$$^{a}$                   |    5.5420 $\pm$ 0.0005" (Table 2)

## Data provenance

- ALMA projects: 2017.1.00428.L, 2018.1.01359.S, 2021.1.00280.L
- bands: Band 7  
  > "We combined the available Band 7 ALMA observations of CRISTAL-05" (2.2 ALMA observations)
- frequencies and spectral setup: four spectral windows, 1875 MHz usable bandwidth each; [CII] at 290.6 GHz observed  
  > "In all cases, four spectral windows were used with an individual usable bandwidth of 1875 MHz." (2.2 ALMA observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-2 and C43-5  
  > "CRISTAL observations in the configurations C43-2 and C43-5" (2.2 ALMA observations)
- baselines: _not stated_
- angular resolution: 0.33x0.27" (robust 2); 0.21x0.18" (robust 0.5)  
  > "\[C\]map           |  0.5   |         45          | 0.21$''$ $\times$ 0.18$''$" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 8.8 uJy/beam  
  > "Continuum          |   2    |         8.8         | 0.33$''$ $\times$ 0.27$''$" (Table 1)
- time on source: 22, 136, 92, and 24 minutes  
  > "The observations have total on-source times of 22, 136, 92, and 24 minutes respectively." (2.2 ALMA observations)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: [CII] 2P3/2 -> 2P1/2 (158 um) (290.541 GHz (observed frame reference))
- Other facility **HST/WFC3 (CANDELS)**: Rest-UV imaging F105W, F125W, F140W, F160W  
  > "Observations were performed in 2015 in 1 orbit per filter for the F105W (1.05 $\mu$m), F125W (1.25 $\mu$m), F140W (1.4 $\mu$m), and F160w (1.54 $\mu$m) filters." (2.3 HST observations)
- Other facility **JWST MIRI (PRIMER)**: F770W imaging, rest-frame 1.2 um  
  > "The filter used was F770W, corresponding to the rest-frame near-infrared emission at 1.2 $\mu$m." (2.4 JWST observations)
- External data: Dust continuum flux density S158um = 0.118 ± 0.021 mJy; dust effective radius 1.4 ± 0.6 kpc; HST/F160W circularized radius 0.36 ± 0.02 kpc  
  > "The dust emission was measured by (cite: 2023Mitsuhashi), yielding a flux density of S$_{158\mu m}$ = 0.118 $\pm$ 0.021 mJy." (4.1 [CII] line and dust emission) [from (cite: 2023Mitsuhashi)]
- External data: Stellar mass log M*=10.27  
  > "the stellar mass log M$_{*}$/M$_{\odot}$ = 10.27 obtained by (cite: 2015capak)" (4.3 Kinematic modeling of C05-NW) [from (cite: 2015capak)]
- External data: FIR conversion factor nuLnu(158um)/L_FIR = 0.185 and SED scaling for Td=45 K, beta=1.5  
  > "the conversion factor is $\nu$L$_{\nu}$(158 $\mu$m)/L$\rm_{FIR}$ = 0.185 (cite: 2024solimano)" (5.3 Shock heating) [from (cite: 2020bethermin); (cite: 2024solimano)]

## Processing

### Calibration

- pipeline or manual: Observatory pipelines, no extra manual flagging  
  > "No extra manual flagging was needed beyond what was already identified by the observatory and automatically flagged by each pipeline." (3.1 Data reduction and JvM correction)
- casa version: CASA 6.5.2 for concat/imaging  
  > "This task and the following procedure are performed using version 6.5.2 of CASA software." (3.1 Data reduction and JvM correction)
- pipeline version: 5.6.1 (ALPINE), 5.6.1 (pilot), 6.5.2 (CRISTAL)  
  > "5.6.1 for the ALPINE program, 5.6.1 for the CRISTAL pilot program, and finally, version 6.5.2 for the CRISTAL program." (3.1 Data reduction and JvM correction)
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: TCLEAN with auto-multithresh, concat to combine  
  > "We created the final product using task TCLEAN and the auto-multithresh algorithm." (3.1 Data reduction and JvM correction)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 2 mainly; robust = 0.5 for auxiliary  
  > "We mainly worked on the products created using a Briggs weighting scheme (cite: 1995briggs) with robust = 2" (3.1 Data reduction and JvM correction)
- uv taper: _not stated_
- cell size: 0.0245 arcsec/pix  
  > "All the products have a pixel size of 0.0245$''$ pix$^{-1}$" (3.1 Data reduction and JvM correction)
- image size: _not stated_
- masking: auto-multithresh: sidelobethreshold=2, noisethreshold=4.5, lownoisethreshold=2, minbeamfrac=0.0; nsigma=1  
  > "Sidelobethreshold = 2, Noisethreshold = 4.5, Lownoisethreshold = 2 and Minbeamfrac = 0.0." (3.1 Data reduction and JvM correction)
- multiscale scales: _not stated_
- continuum subtraction: UVCONTSUB with fitorder = 0  
  > "subtract the continuum emission using UVCONTSUB with fitorder = 0." (3.1 Data reduction and JvM correction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: concat of all programs into a single ms  
  > "We combined the calibrated datasets into a single measurement set (ms) used to create the images and data cubes, using the task concat." (3.1 Data reduction and JvM correction)
- smoothing: _not stated_
- final beam: 0.33x0.27" (robust 2), 0.21x0.18" (robust 0.5)  
  > "\[C\]map           |   2    |         42          | 0.33$''$ $\times$ 0.27$''$" (Table 1)
- final rms: [CII] map 42 uJy/beam (robust 2)  
  > "\[C\]map           |   2    |         42          | 0.33$''$ $\times$ 0.27$''$" (Table 1)

### Inherited from earlier work

- JvM correction following Czekala et al. 2021  
  > "we applied in all the products the correction suggested by (cite: Czekala2021)" (3.1 Data reduction and JvM correction) [from (cite: Czekala2021)]
- Detailed data reduction and JvM correction described elsewhere  
  > "A more detailed description of the data reduction and JvM correction is covered in Gonzalez-Lopez et al, in prep." (3.1 Data reduction and JvM correction) [from Gonzalez-Lopez et al, in prep.]
- Sersic n=1 visibility modeling for [CII] size  
  > "Based on visibility modeling, a Sérsic profile with an index of $n=1$ (Ikeda et al. in prep) results in a circularized effective radius" (4.1 Radial profiles) [from Ikeda et al. in prep]
- Rest frequency of [CII] as in ALPINE catalog  
  > "the reference frequency of the \[C\]emission is the same as defined to the source in the ALPINE catalog" (3.1 Data reduction and JvM correction) [from (cite: 2020lefevre)]
- Disk criteria from Förster Schreiber & Wuyts; single-system radial profile approach following Fujimoto  
  > "following (cite: 2020fujimoto) analysis, we evaluate how the emission is distributed along the system considering it as a single source." (4.1 Radial profiles) [from (cite: 2020fujimoto); (cite: 2020forster)]

### Not stated but needed to reproduce (our reading)

- Line-free channels used for continuum subtraction and uv-range of continuum
- Exact JvM epsilon per product and the channel used
- Fellwalker NOISE and MINDIP-specific values for final clump definitions beyond ranges; MINDIP/MAXJUMP baseline
- DYSMALpy settings: PA, kinematic centre values, spectral/instrumental line broadening, PSF
- Moment map 0 integration limits (FW tenth max channels)
- Task cube velocity grid and phase centre
- Flux calibrators and flux scale uncertainty
- Exact aperture positions for the 11 regions and conversion for upper limits

## Analysis recipe

1. **Calibrate, combine and image ALMA data**: Pipeline calibration per program, concat, uvcontsub, tclean with auto-multithresh down to nsigma=1, JvM correction  
  > "We created the final product using task TCLEAN and the auto-multithresh algorithm." (3.1 Data reduction and JvM correction)
   - software: CASA
   - parameter: robust = 2 and 0.5; pixel 0.0245"; nsigma=1  
  > "All the products have a pixel size of 0.0245$''$ pix$^{-1}$" (3.1 Data reduction and JvM correction)
   - fitting: _not stated_
   - validation: Non-JvM-corrected flux is ~2.5x larger than corrected within 1.5" aperture  
  > "the total flux density of CRISTAL-05 is approximately 2.5 $\times$ larger in the non-JvM-corrected cube compared to the corrected one" (3.1 Data reduction and JvM correction)
2. **Measure integrated [CII] line**: Spectrum in 1.5" aperture, single-Gaussian fit (also two-Gaussian)  
  > "We measured the spatially integrated \[C\]line profile using a 1.5$''$-aperture centered at the emission centroid" (4.1 [CII] line and dust emission)
   - fitting: Gaussian fit; chi2 = 6.5 single, 5.2 double  
  > "The moderate goodness of the fit ($\rm\chi^{2}$ = 6.5)" (4.1 [CII] line and dust emission)
   - validation: Consistent with ALPINE total flux  
  > "This is consistent with the total flux measured by the ALPINE survey (cite: 2020lefevre)" (4.1 [CII] line and dust emission)
3. **Moment maps and position-velocity diagram**: Moment-0/1/2 from natural-weighted cube over [-280,+280] km/s with 3 rms clip; PV slit along major axis 10 pixels wide  
  > "The averaging only includes pixels in a given channel with an intensity greater than 3 $\times$ the rms of the channel." (3.2 Gas motion)
   - fitting: _not stated_
   - validation: _not stated_
4. **Compare sizes and radial profiles across wavelengths**: Degrade HST/JWST PSF to ALMA beam; elliptical annuli 0.3" wide with q=0.6; Sersic n=1 visibility-fit radius  
  > "We calculate the flux in elliptical annuli, with 0.3$''$ widths and the axial ratio of q = 0.6" (4.1 Radial profiles)
   - fitting: Visibility modeling (Ikeda et al. in prep)  
  > "Based on visibility modeling, a Sérsic profile with an index of $n=1$ (Ikeda et al. in prep) results in a circularized effective radius of $r_{{{\rm [C}{\rm \scriptstyle II}]}}^{\rm cir} = 1.6 \pm 0.3$ kpc." (Analysis, Radial profiles)
   - validation: _not stated_
5. **Decompose system into clumps**: Fellwalker on non-JvM cubes; MINPIX=16, FLATSLOPE=2 rms, MINDIP in [1,2,3] sigma, MAXJUMP in [4,6,8] pixels  
  > "we performed several runs while varying the parameters: \[1, 2, 3\]-$\sigma_{rms}$ and \[4, 6, 8\] pixels, respectively." (4.2 Clumpiness)
   - software: Fellwalker
   - fitting: _not stated_
   - validation: Two components found in all runs  
  > "For all runs, the algorithm found a total number of 2 components" (4.2 Clumpiness)
6. **Kinematic model of C05-NW**: 1D DYSMALpy with disk (n=1)+bulge (n=4, B/T=30%)+NFW halo (c=3) fit to symmetrized rotation and dispersion curves  
  > "We choose the 1-d approach to simultaneously model the radial and dispersion velocity curves along the major axis of the galaxy" (4.3 Kinematic modeling of C05-NW)
   - software: DYSMALpy
   - parameter: 1000 walkers, 50 burn-in steps, 200 run steps; inclination 60 deg; free: fdm, disk r_eff, sigma0  
  > "We ran the algorithm using 1000 walkers, a burning phase of 50 steps, a running phase of 200 steps" (4.3 Kinematic modeling of C05-NW)
   - assumption: gas-mass ratio log Mgas/M* = 0.75; isotropic constant dispersion; no adiabatic contraction  
  > "the assume a gas-mass ratio of log M$\rm_{gas}$/M$_{*}$ = 0.75 (cite: 2020dessauges)" (4.3 Kinematic modeling of C05-NW)
   - fitting: MCMC; flat prior for fdm, truncated Gaussian priors on Mbar (centre 10.5, sd 0.5) and disk r_eff (centre 1.32 kpc, sd 1 kpc), sigma0 flat [5,100] km/s; MAP estimates  
  > "We choose a truncated Gaussian prior, centered at log M$\rm_{bar}$/M$_{\odot}$ = 10.5, with a standard deviation of 0.5" (4.3 Kinematic modeling of C05-NW)
   - validation: chi2 = 0.63 velocity, 2.6 dispersion  
  > "This is a good fit for the velocity curve ($\chi^{2}$ = 0.63) but moderate for the dispersion velocity curve ($\chi^{2}$ = 2.6)." (4.3 Kinematic modeling of C05-NW)
7. **Dynamical masses**: Mdyn = gamma R v^2 / G using circularized Gaussian radii  
  > "M$_{\rm dyn}$ = $\rm\gamma$Rv$^{2}$/G" (5.1 On the nature of CRISTAL-05)
   - assumption: gamma = 5 and v~sigma for C05-SE; v=120 km/s at R=1.5 kpc for NW  
  > "so we assume $\gamma$ = 5 (cite: 2022spilker) and v $\sim \sigma$ of the system" (5.1 On the nature of CRISTAL-05)
   - fitting: _not stated_
   - validation: Consistent with DYSMALpy estimate  
  > "which are consistent with the value estimated for C05-NW in section [4.3](#sec:kinematical) and the dynamical mass of typical galaxies at z = 5.5" (Discussion, On the nature of CRISTAL-05)
8. **Resolved [CII]/FIR ratios**: Beam-sized apertures (0.33"), dust flux converted to L_FIR with factor 0.185 for Td=45 K, beta=1.5; compare with local and ALPINE galaxies  
  > "We define apertures with the same width of the beam size (${\rm d}\sim0.33$$''$ $\sim$ 2 kpc)" (5.3 Shock heating)
   - assumption: Td = 45 K, beta=1.5, uncertainty from Td 40-60 K  
  > "assuming a dust temperature of T$_{d} = 45$ K and an emissivity index of $\rm\beta_{dust} = 1.5$" (5.3 Shock heating)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 6.5.2 (pipelines 5.6.1, 6.5.2): calibration, concat, uvcontsub, tclean  
  > "Data calibration and a combination of the different observations were performed using the CASA software (cite: 2022casa)." (3.1 Data reduction and JvM correction)
- **Fellwalker** : 3D clump finding  
  > "We used the Fellwalker algorithm (cite: 2005berry) to search for structures" (4.2 Clumpiness)
- **DYSMALpy** : MCMC kinematic modeling  
  > "We kinematically model the C05-NW emission using the parametric 3D software DYSMALpy" (4.3 Kinematic modeling of C05-NW)
- **grizli** : HST image recalibration  
  > "Raw images were re-calibrated using the latest versions of the grizli pipeline" (2.3 HST observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| [CII] line flux | 1.00 | 0.07 | Jy km/s | 2 | line flux of 1.00 $\pm$ 0.07 Jy km s$^{-1}$ |
| [CII] FWHM | 238 | 25 | km/s | 2 | FWHM = 238 $\pm$ 25 km s$^{-1}$ |
| [CII] circularized effective radius | 1.6 | 0.3 | kpc | 4 | $r_{{{\rm [C}{\rm \scriptstyle II}]}}^{\rm cir} = 1.6 \pm 0.3$ kpc |
| Flux fraction C05-NW / C05-SE / extended | 46% / 13% / 41% | extended is upper limit | percent | 5 | 46%, 13%, and 41% of the total emission of the system, respectively |
| dark matter fraction within r_eff | 0.06 | +0.27/-0.06 | dimensionless | 6 | fdm = 0.06$^{+0.27}_{-0.06}$ |
| log baryonic mass | 9.83 | +0.11/-0.17 | log Msun | 6 | log M$_{bar} = 9.83^{+0.11}_{-0.17}$ M$_{\odot}$ |
| intrinsic dispersion sigma0 | 35 | +6/-7 | km/s | 6 | $\sigma_{0} =$ 35$_{-7}^{+6}$ kms$^{-1}$ |
| dynamical mass C05-NW / C05-SE | 5e9 / 9.1e8 | not stated | Msun | 7 | M$_{\rm dyn}^{\rm NW} = 5 \times 10^{9}$ M$_{\odot}$, M$_{\rm dyn}^{\rm SE} = 9.1 \times 10^{8}$ M$_{\odot}$ |
| mean velocity dispersion (moment-2) | 79 | 21 | km/s | 3 | notably high average value of $79\pm 21$ kms$^{-1}$ |

## Qualitative findings

- The system is a close interacting pair (C05-NW, C05-SE) separated by ~2.4 kpc and ~100 km/s, with compact UV and NIR emission.  
  > "our observations reveal that the system is a close interacting pair surrounded by an extended component of carbon-enriched gas." (abstract)

## Claim tuples

- H: Is CRISTAL-05 a single galaxy or a multicomponent system? | E: Moment maps, PV diagram and Fellwalker clump finding at 0.2-0.3" resolution | R: Two components found in all runs; PV shows separation of ~100 km/s | F: CRISTAL-05 is a close interacting pair | **supported**
- H: Is [CII] more extended than UV and stellar emission? | E: Radial profiles and visibility modeling comparison with HST and JWST | R: r_[CII]=1.6±0.3 kpc, ~4x UV; extended to 10 kpc | F: [CII] extended emission with compact UV/NIR | **supported**
- H: Does C05-NW host a rotating disk with little dark matter? | E: DYSMALpy MCMC fit to rotation and dispersion curves | R: fdm = 0.06 (+0.27/-0.06), V/sigma ~3 | F: Baryon-dominated rotating disk, though a compact merger cannot be ruled out | **partially**
- H: Is the extended [CII] caused by merger shock heating? | E: Resolved [CII]/FIR and Sigma_[CII]-Sigma_SFR in beam-sized apertures | R: Regions around the components have ratios consistent with shocked regions of SQ and Taffy | F: Mergers likely main driver, other mechanisms not excluded | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Natural weighting used to mitigate surface brightness dimming and nsigma=1 cleaning to minimize the JvM effect  
  > "To mitigate this possibility, we employ data products generated through natural weighting in the next analyses." (3.2 Gas motion)
- Alternative: Clumpy single galaxy scenario disfavoured: clump sizes exceed expectations and it struggles with PV velocity distributions  
  > "the clumpy scenario struggles to account for the distinct velocity distributions observed in the position-velocity (pv) diagram." (5.1 On the nature of CRISTAL-05)
- How they decided it was enough: _not stated_
- Limitation (authors): Extended fraction is an upper limit dependent on noise and segmentation thresholds  
  > "we define the fraction of \[C\]emission in the extended emission as an upper limit, meaning that it contributes no greater than 41%" (4.2 Clumpiness)
- Limitation (authors): Dust emission is low S/N so no radial dust profile  
  > "Due to the moderate spatial S/N, we can not perform a direct comparison of the radial profile of the dust distribution." (4.1 Radial profiles)
- Caveat (inferred, ours): Disk modeling relies on 1D curves of a source resolved over ~3 beams with many priors and fixed parameters
- Caveat (inferred, ours): Shock interpretation rests on assumed dust temperature and low dust S/N
- Caveat (inferred, ours): Fellwalker segmentation depends on thresholds; extended fraction uncertain
- Caveat (inferred, ours): JvM correction changes fluxes by 2.5x, affecting extended emission

## Reproducibility

- Data public (paper): ALMA programs listed with IDs; data from public ALMA programs  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00428.L, ADS/JAO.ALMA#2021.1.00280.L, ADS/JAO.ALMA#2018.1.01359.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Gonzalez-Lopez et al. in prep reduction details
- Missing: Ikeda et al. in prep visibility fits
- Missing: Line-free channels, Fellwalker baseline parameters, aperture definitions
- Data volume (inferred): ~100-300 GB raw across three programs; cubes tens of GB
- Score (inferred): 3/5, Imaging recipe and modeling priors are well specified, but several key methods rely on in-prep papers and some parameters are unstated.
- Rediscovery candidate: yes, Data are public, imaging and modeling are largely specified, and results are numeric (fluxes, sizes, fractions, DM fraction).

## Links

- Method: (cite: Czekala2021) (JvM correction)
- Method: (cite: 2005berry) (Fellwalker clump finder)
- Method: (cite: 2021price) (DYSMALpy modeling)
- Companion: (cite: 2023Mitsuhashi) (CRISTAL dust continuum measurements)
- Companion: (cite: 2024solimano) (CRISTAL series; FIR conversion factor)
- Companion: (cite: 2020fujimoto) (previous [CII] halo identification of CRISTAL-05)
- Related: CRISTAL
- Related: ALPINE
- Related: CANDELS
- Related: PRIMER
- Related: COSMOS

## Checks

```json
{
 "quotes": 83,
 "quotes_ok": 83,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 90,
  "stated": 62,
  "rate": 0.689
 },
 "evidence_ok": true
}
```
