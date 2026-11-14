# The MBHBM<SUB>⋆</SUB> Project. I. Measurement of the Central Black Hole Mass in Spiral Galaxy NGC 3504 Using Molecular Gas Kinematics

`2020ApJ...892...68N` | The Astrophysical Journal 2020 | first author: Nguyen, Dieu D. | arXiv: 1902.03813 | DOI: 10.3847/1538-4357/ab77aa

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: What is the mass of the central supermassive black hole in NGC 3504, measured from 12CO(2-1) molecular gas kinematics, and is it consistent with BH-galaxy scaling relations?  
  > "We present the first measurement of the mass of a supermassive black hole (SMBH) in the nearby double-barred spiral galaxy NGC 3504" (abstract)
- Target **NGC 3504**: coordinates RA 11h03m11.210s, Dec +27d58m21.00s (J2000)  
  > "located at the distance of $D=13.6$ Mpc estimated from Tully-Fisher relation (cite: Russell02)" (2 The Galaxy NGC 3504); "has a systemic velocity of $1525.0\pm2.1$ km s$^{-1}$" (2 The Galaxy NGC 3504); z/distance D = 13.6 Mpc; systemic velocity 1525.0 km/s  
  > "located at the distance of $D=13.6$ Mpc estimated from Tully-Fisher relation (cite: Russell02)" (2 The Galaxy NGC 3504); "has a systemic velocity of $1525.0\pm2.1$ km s$^{-1}$" (2 The Galaxy NGC 3504); distance from Tully-Fisher relation (Russell02)  
  > "located at the distance of $D=13.6$ Mpc estimated from Tully-Fisher relation (cite: Russell02)" (2 The Galaxy NGC 3504); "has a systemic velocity of $1525.0\pm2.1$ km s$^{-1}$" (2 The Galaxy NGC 3504)

## Data provenance

- ALMA projects: 2017.1.00964.S
- bands: 12CO(2-1) at ~230 GHz (LSB 227.5-231.5 GHz, USB 442-446 GHz continuum mentioned)  
  > "The observations of the $^{12}{\rm CO(2-1)}$ line in the nucleus of NGC 3504 are carried out with ALMA" (3.2 ALMA Observations)
- frequencies and spectral setup: one 1875 MHz FDM window on CO(2-1) plus three 2 GHz TDM continuum windows  
  > "one 1875 MHz FDM spectral window covers over the $^{12}{\rm CO(2-1)}$ line and three 2 GHz TDM spectral windows added simultaneously to detect continuum emission" (3.2 ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: 46 12m antennas  
  > "The observations use 46 ALMA’s 12m antennas with the C43-9 and C43-6 configurations" (3.2 ALMA Observations)
- configurations: C43-9 (high res.) and C43-6 (low res.)  
  > "Configurations | C43-9 | C43-6" (Table 1)
- baselines: _not stated_
- angular resolution: 0.042"x0.030" (C43-9); 0.221"x0.164" (C43-6)  
  > "Beamsize | $0.042\ensuremath{''}\times0.030\ensuremath{''}$ | $0.221\ensuremath{''}\times0.164\ensuremath{''}$" (Table 1)
- max recoverable scale: 10 arcsec  
  > "so that the data has a maximum recoverable scale (MRS) of 10$\ensuremath{''}$ in diameter" (3.2 ALMA Observations)
- sensitivity: _not stated_
- time on source: 46.6 min (C43-9), 25.7 min (C43-6)  
  > "Exposure time | 46.6 min. | 25.7 min." (Table 1)
- observing dates: 2017 Oct 24 (C43-9); 2018 Jan 01 (C43-6)  
  > "Obs. Date | 2017 Oct. 24 | 2018 Jan. 01" (Table 1)
- pi or archival as stated: PI program of first author  
  > "“Weighing Black Hole Masses in Low-Mass Galaxies” project (Program 2017.1.00964.S, PI: Nguyen, Dieu)" (3.2 ALMA Observations)
- Line: 12CO J=2-1 (not stated)
- Line: CS J=5-4 (not stated)
- Other facility **HST WFC3 F160W/F110W**: imaging used for MGE stellar mass model  
  > "We use *HST* observations in wide field camera 3 (WFC3) IR band F160W to create a mass model" (3.1 HST Imaging)
- External data: Tully-Fisher distance 13.6 Mpc  
  > "located at the distance of $D=13.6$ Mpc estimated from Tully-Fisher relation (cite: Russell02)" (2 The Galaxy NGC 3504) [from (cite: Russell02)]
- External data: bulge stellar velocity dispersion 119.3±10.3 km/s  
  > "measures the stellar velocity dispersion of the bulge is $\sigma=119.3\pm10.3$ km s$^{-1}$ (cite: Ho09)" (2 The Galaxy NGC 3504) [from (cite: Ho09)]
- External data: dust mass (5.1±0.7)e5 Msun  
  > "The dust mass of $(5.1\pm0.7)\times10^5$$M_{\odot}$ is calculated in D. Nguyen et al. in preparation." (5.3 Fitting Process) [from D. Nguyen et al. in preparation]
- External data: bulge effective radius from bulge-disk-bar decomposition  
  > "adapt the bulge effective radius from the bugle-disk-bar decomposition model (cite: Laurikainen04)" (7.2 MBH Scaling Relations) [from (cite: Laurikainen04)]

## Processing

### Calibration

- pipeline or manual: standard ALMA pipeline by ARC staff  
  > "The raw ALMA data are calibrated by the ALMA regional center staff using the standard ALMA pipeline." (3.2 ALMA Observations)
- casa version: CASA 5.1.1 (for uvcontsub)  
  > "using the task `uvcontsub` of the `Common Astronomy Software Applications` (`CASA`) package version 5.1.1" (3.2 ALMA Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1058+0133 (flux and bandpass); phase calibrator J1102+2757  
  > "Flux and bandpass calibration are conducted using the quasar J1058+0133" (3.2 ALMA Observations)
- flux scale uncertainty: ~10% ALMA flux calibration uncertainty  
  > "with 10% of the error budget comes from the flux calibration uncertainty of ALMA data" (4 Detection of Dense Gas CS(5-4))
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: moments masking technique  
  > "We enhance the quality of these maps using the moments masking technique" (3.2.2 CO line emission)
- multiscale scales: _not stated_
- continuum subtraction: continuum fitted by a power law over the line-free bandwidth, subtracted in uv-plane with uvcontsub  
  > "measured over the full line-free bandwidth, fitted by a power law function, and then subtracted from the data in the $uv$-plane using the task `uvcontsub`" (3.2 ALMA Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: C43-9 and C43-6 data combined into a 'combined' high-resolution cube; low-res cube from C43-6  
  > "from the combined cube directly" (3.2.2 CO line emission)
- smoothing: _not stated_
- final beam: 0.042"x0.030" (combined), 0.221"x0.164" (low res)  
  > "Beamsize | $0.042\ensuremath{''}\times0.030\ensuremath{''}$ | $0.221\ensuremath{''}\times0.164\ensuremath{''}$" (Table 1)
- final rms: _not stated_

### Inherited from earlier work

- moments masking technique for moment maps  
  > "details of this technique were described in (cite: Davis17; Onishi17; Davis18)" (3.2.2 CO line emission) [from (cite: Davis17; Onishi17; Davis18)]
- covariance handling by inflating RMS by (2NxM)^1/4  
  > "we increase the RMS by a factor $(2N\times M)^{1/4}$, where $N$ and $M$ are the numbers of spaxels and velocity channels included in the fit (cite: Mitzkus17)" (5.3 Fitting Process) [from (cite: Mitzkus17)]
- tilted-ring modelling approach  
  > "in a similar approach as for the H$_2$1-0 S(1) transition kinematics in (cite: Seth10a; denbrok15); N17" (6.1 The Tilted-Ring Models) [from (cite: Seth10a; denbrok15); N17]
- CO line ratio 0.8 and X_CO  
  > "assuming the line ratio $^{12}{\rm CO(2-1)}$/$^{12}{\rm CO(1-0)}=0.8$ (cite: Bigiel08)" (5.3 Fitting Process) [from (cite: Bigiel08); (cite: Kuno00; Kuno07; Bolatto13)]

### Not stated but needed to reproduce (our reading)

- Imaging parameters (tclean weighting/robust, cell size, image size, deconvolver, channel width of cubes)
- How the two configurations were combined (concat, weights) and any self-calibration
- Line-free channels used for continuum fitting and power-law order
- Exact CASA version used for imaging and whether pipeline was re-run
- Dust mass and nuclear structure analysis come from unpublished paper
- Rest frequencies and moment-map clipping thresholds
- KinMS walker count, and details of tilted-ring code and sampler
- Rest frequency used for velocity axis and CS(5-4) extraction method

## Analysis recipe

1. **Continuum measurement**: Gaussian fit to continuum peak with CASA imfit giving centre, size, flux  
  > "we fit this continuum profile with a Gaussian using the `CASA` task `imfit`" (3.2.1 Continuum Emission)
   - software: CASA
   - fitting: _not stated_
   - validation: compared with SDSS DR14 optical centre  
  > "The SDSS data release 14 (cite: Abolfathi18) also report an optical center" (3.2.1 Continuum Emission)
2. **Stellar mass model**: MGE fit to HST F160W image with PSF deconvolution, masking dust lanes; PA fixed at -28 deg; q range 0.65-1.0  
  > "We use the `mge_fit_sectors IDL` version 4.14 (cite: Cappellari02) to fit the F160W image and deconvolve the effects of a PSF." (5 Creating a Mass Model); "we set the axis ratio in the range of $q=0.65-1.0$" (5 Creating a Mass Model)
   - software: mge_fit_sectors, IDL, Tiny Tim
   - assumption: constant M/L, justified by uniform J-H colour  
  > "suggests we can use a constant *M/L* to create the mass model for NGC 3504" (5 Creating a Mass Model)
   - fitting: _not stated_
   - validation: model-data difference <15% across FOV  
  > "The difference between the best-fit model and the data are $<$15% across the FOV" (5 Creating a Mass Model)
3. **Gas mass for self-gravity**: H2 mass from CO flux using CO(2-1)/(1-0)=0.8 and X_CO=0.5x MW=1e20; gas+dust added via KinMS gasGrav  
  > "We add these masses in the KinMS `gasGrav` mechanism, assuming the dust and gas is co-spatial distribution." (5.3 Fitting Process)
   - software: KinMS
   - assumption: X_CO = 1e20 cm^-2 (K km/s)^-1 for starburst  
  > "$X_{\rm CO}=0.5\times X_{\rm CO}^{\rm Milky Way}=1\times10^{20}$" (5.3 Fitting Process)
   - fitting: _not stated_
   - validation: _not stated_
4. **KinMS dynamical modelling for M_BH**: 13-parameter MCMC fit of simulated cube to data, circular velocity from MGE + point-mass BH; first fit on 4"x4" with 1e5 iterations, then 1"x1" fit with 3e6 iterations, 20% burn-in, velocity channels -200 to 200 km/s  
  > "The total number of iterations are set to be $3\times10^6$ and the first 20% of iterations are considered as the burn-in phases" (5.3 Fitting Process)
   - software: KinMSpy_MCMC, emcee, JAM mge_vcirc
   - parameter: flat priors, M_BH flat in log space; inclination free over MGE-allowed range  
  > "the prior on the $M_{\rm BH}$ was flat in log-space" (5.3 Fitting Process)
   - assumption: thin axisymmetric disk, circular orbits, constant velocity dispersion  
  > "we assume the gas in NGC 3504 is in purely circular motion" (5.4 Uncertainty Sources)
   - fitting: emcee affine-invariant ensemble sampler; chi^2 likelihood; medians of posteriors with 16/84% (1 sigma) and 0.2/99.8% (3 sigma)  
  > "We choose the best-fit parameters that are the medians of the parameter posterior PDFs." (5.4 Model Results)
   - validation: reduced chi2 1.16; PVD compared with no-BH and overly large BH models; systematics tests on mass model, AGN, distance, non-circular motions, dispersion profile, resolution  
  > "The reduced chi-square ($\chi^2_{\rm red}$) for the best fit is 1.16, indicating a good fit." (5.4 Model Results)
5. **Independent tilted-ring check**: three thin-disk tilted-ring models fitted in same area, using rotational velocity chi2; gas and dust ignored  
  > "We ignore gas and dust distribution during the fit in this work" (6.1 The Tilted-Ring Models)
   - software: Kinemetry
   - fitting: _not stated_
   - validation: compare with KinMS result  
  > "The purpose of this test is to examine the robustness of the measured $M_{\rm BH}$ in various assumptions and dynamical models." (6 Thin Disk Tilted-Ring Dynamical Model)

## Software

- **CASA** 5.1.1: uvcontsub and imfit  
  > "using the task `uvcontsub` of the `Common Astronomy Software Applications` (`CASA`) package version 5.1.1" (3.2 ALMA Observations)
- **KinMSpy_MCMC** : dynamical modelling of gas to find M_BH  
  > "we use the Python code `KINMSpy_MCMC`" (5 KinMS Dynamical Modeling)
- **emcee** : MCMC sampling  
  > "using the `emcee` algorithm (cite: Foreman-Mackey13)" (5 KinMS Dynamical Modeling)
- **mge_fit_sectors** 4.14 (IDL): MGE fitting of HST image  
  > "We use the `mge_fit_sectors IDL` version 4.14" (5 Creating a Mass Model)
- **JAM (mge_vcirc)** : circular velocity profile  
  > "We calculate this circular velocity profile using the `mge_vcirc` procedure" (5.2 Velocity Model)
- **Kinemetry** : kinematic misalignment and velocity model  
  > "`Kinemetry`[^1] (cite: Krajnovic06) examination reveals these two disks are clearly misalignment" (3.2.2 CO line emission)
- **drizzlepac/Astrodrizzle** : combining HST flt images to check sky level  
  > "combined these images in the same filter using `drizzlepac/Astrodrizzle`" (3.1 HST Imaging)
- **Tiny Tim** : HST PSFs  
  > "We used `Tiny Tim` point spread functions" (3.1 HST Imaging)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| M_BH (KinMS, combined cube) | 1.02e7 | +0.18/-0.15 (3 sigma) | Msun | 4 | $M_{\rm BH}=1.02^{+0.18}_{-0.15}\times10^7$$M_{\odot}$ |
| H-band M/L | 0.66 | +1.44/-0.65 | Msun/Lsun | 4 | $M/L_{\rm H}=0.66^{+1.44}_{-0.65}$ |
| reduced chi2 of best fit | 1.16 | not stated | dimensionless | 4 | is 1.16, indicating a good fit |
| M_BH (tilted-ring) | 7.7e6 | +1.5/-1.2 (3 sigma) | Msun | 5 | $M_{\rm BH}=7.7_{-1.2}^{+1.5}\times10^6$$M_{\odot}$ |
| continuum integrated intensity | 4.70 | ±0.16 (sys) ±0.24 (flux cal) | mJy | 1 | the total integrated intensity of $4.70\pm0.16\pm0.24$ mJy |
| CS(5-4) total flux | 1.76 | 0.42 | Jy km/s | 0 | We estimate the total flux is $1.76\pm0.42$ Jy km s$^{-1}$ |
| H2 gas mass in fit region | 4.2e7 | 0.5e7 | Msun | 3 | $M_{\rm H_2}=(4.2\pm0.5)\times10^7$$M_{\odot}$ |
| bulge mass | 2.3e9 | 0.4e9 | Msun | 0 | $M_{\rm Bulge}=(2.3\pm0.4)\times10^9$$M_{\odot}$ |
| sphere of influence radius | 4.6 | not stated | pc | 0 | $R_{\rm SOI}=G M_{\rm BH}/\sigma^2=4.6$ pc |

## Qualitative findings

- CS(5-4) fills the central CO(2-1) hole and shares kinematics with CO within the CND  
  > "The ${\rm CS(5-4)}$ line has the same kinematics with the ${\rm ^{12}CO(2-1)}$ line within the CND" (abstract)

## Claim tuples

- H: NGC 3504 hosts a central SMBH measurable with CO(2-1) kinematics | E: KinMS MCMC modelling of ALMA CO(2-1) cube with HST MGE mass model | R: M_BH=1.02e7 Msun, M/L_H=0.66 | F: An SMBH of ~1e7 Msun is detected | **supported**
- H: Result is robust to modelling assumptions | E: Alternative mass models, AGN component, kinemetry velocity, dispersion profiles, tilted-ring models | R: M_BH varies from ~8.7e6 to 1.3e7; tilted-ring 7.7e6 | F: Estimate robust within 3 sigma | **supported**
- H: BH is consistent with scaling relations | E: Compare with M_BH-sigma and M_BH-M_bulge | R: consistent with empirical relations, outside +1 sigma of Pacucci18 | F: Consistent with scaling relations | **supported**
- H: CS(5-4) is a better tracer in the CO hole | E: Compare CS and CO moment maps and PVD | R: CS centrally concentrated, but velocity resolution ~40 km/s | F: CS(5-4) could constrain M_BH better with higher velocity resolution | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Tilted-ring model used as independent check of robustness  
  > "We also constrain the *M/L*, $i$, and $M_{\rm BH}$ of the central SMBH in NGC 3504 independently using a different dynamical model" (6 Thin Disk Tilted-Ring Dynamical Model)
- Alternative: Central CO hole interpreted as torus/CO deficiency rather than missing gas  
  > "the $^{12}{\rm CO(2-1)}$ emission is sometimes deficient in the nuclear regions, and therefore may not be the best tracer for the torus" (3.2.2 CO line emission)
- How they decided it was enough: _not stated_
- Limitation (authors): Tilted-ring uncertainties likely underestimated; distance systematics large  
  > "we assume uniform errors for the velocities, the confidence intervals are therefore likely underestimated" (6.2 Results)
- Caveat (inferred, ours): Quoted M_BH errors are far smaller than the systematics (distance 10%, alternative models 8.7e6-1.3e7)
- Caveat (inferred, ours): Gas and dust mass inputs depend on an unpublished paper and assumed X_CO
- Caveat (inferred, ours): Non-circular motions and the nuclear structure are only tested crudely
- Caveat (inferred, ours): Large M/L degeneracy; narrow 3-sigma quoted error on log M_BH seems small

## Reproducibility

- Data public (paper): ALMA program cited by code; no explicit public statement  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA #2017.1.00964.S." (Acknowledgements)
- Products in archive: _not stated_
- Code: KinMSpy_MCMC public on GitHub (third-party code); no new code released  
  > "<https://github.com/TimothyADavis/KinMSpy_MCMC>" (5 KinMS Dynamical Modeling)
- Missing: tclean imaging parameters
- Missing: combined-cube construction details
- Missing: KinMS configuration details (walkers, files)
- Missing: dust mass from unpublished paper
- Missing: tilted-ring code
- Data volume (inferred): ~50-100 GB raw for two executions
- Score (inferred): 5/5, Public ALMA data and named tools, but imaging and fitting setup details are missing and some inputs come from unpublished work.
- Rediscovery candidate: no, Imaging recipe incomplete and key inputs (dust mass, mass model) rely on unpublished work, although the main result is numeric.

## Links

- Method: Davis14 (KinMS method)
- Method: Cappellari02 (MGE fitting)
- Method: Krajnovic06 (Kinemetry)
- Companion: D. Nguyen et al. in preparation (dust mass, nuclear structure, SFR)
- Related: MBHBM* Project
- Related: Barth16a
- Related: Davis17
- Related: Onishi17

## Checks

```json
{
 "quotes": 79,
 "quotes_ok": 79,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 83,
  "stated": 58,
  "rate": 0.699
 },
 "evidence_ok": true
}
```
