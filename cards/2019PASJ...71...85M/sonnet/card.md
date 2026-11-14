# Complex distribution and velocity field of molecular gas in NGC 1316 as revealed by the Morita Array of ALMA

`2019PASJ...71...85M` | Publications of the Astronomical Society of Japan 2019 | first author: Morokuma-Matsui, Kana | arXiv: 1905.11085 | DOI: 10.1093/pasj/psz067

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: What are the distribution, total mass and velocity field of molecular gas in the cD/radio galaxy NGC 1316, what is its origin (inflow or outflow), and how does it interact with the nuclear jet?  
  > "We reveal the detailed distribution of the molecular gas in the central region for the first time: a shell structure in the northwest, a barely resolved blob in the southeast of the center and some clumps between them." (abstract)
- Target **NGC 1316 (Fornax A)**: coordinates CO box centre (ICRS) 03h22m41.448s, -37d12'16.2"  
  > "We adopt the distance to NGC 1316 of $20.8\pm0.5$ Mpc (cite: Cantiello:2013aa) throughout the paper" (1 Introduction); z/distance 20.8±0.5 Mpc  
  > "We adopt the distance to NGC 1316 of $20.8\pm0.5$ Mpc (cite: Cantiello:2013aa) throughout the paper" (1 Introduction); distance from Cantiello et al. 2013  
  > "We adopt the distance to NGC 1316 of $20.8\pm0.5$ Mpc (cite: Cantiello:2013aa) throughout the paper" (1 Introduction)

## Data provenance

- ALMA projects: 2017.1.00129.S
- bands: Band 3  
  > "The 7-m antennae (7M) and 12-m total power (TP) array observations in Band 3 were carried out during cycle 5" (2.1 ALMA 7-m and total-power array observations)
- frequencies and spectral setup: CO(1-0) SPW 1875 MHz wide, 1.128 MHz (2.952 km/s) resolution; other SPWs at 113.3962, 103.2712, 101.3962 GHz for continuum  
  > "whose bandwidth and resolution are 1875 MHz ($4902.5$ km s$^{-1}$) and 1.128 MHz ($2.952$ km s$^{-1}$), respectively." (2.1 ALMA 7-m and total-power array observations)
- continuum bandwidth: _not stated_
- arrays: ACA 7M (Morita Array) plus 12-m total power  
  > "The 7-m antennae (7M) and 12-m total power (TP) array observations in Band 3 were carried out during cycle 5" (2.1 ALMA 7-m and total-power array observations)
- configurations: _not stated_
- baselines: 8.9 m to 48.9 m; nine to eleven antennae  
  > "from nine to eleven antennae were employed with baselines ranging from 8.9 m to 48.9 m" (2.1 ALMA 7-m and total-power array observations)
- angular resolution: 15.2" x 7.7" (1.5 x 0.8 kpc), PA 89 deg  
  > "The achieved synthesized beam was $15''.2 \times 7''.7$ ($1.5~{\rm kpc} \times 0.8~{\rm kpc}$ at the distance of NGC 1316) with a P.A. of 89$^\circ$." (2.2 ALMA data analysis with CASA)
- max recoverable scale: _not stated_
- sensitivity: 12 mJy/beam rms at 9.9 km/s  
  > "with the final velocity resolution of 9.9 km s$^{-1}$ was 12 mJy beam$^{-1}$, after the primary beam correction." (2.2 ALMA data analysis with CASA)
- time on source: _not stated_
- observing dates: 7M: 16 Oct-21 Dec 2017; TP: 29-31 May 2018  
  > "The TP on-the-fly observations were carried out from May 29 to 31 in 2018 with three or four antennae." (2.1 ALMA 7-m and total-power array observations)
- pi or archival as stated: _not stated_
- Line: 12CO J=1-0 (115.271202 GHz)
- Other facility **Keck/LRIS**: Optical long-slit spectra of ionized gas for kinematics comparison  
  > "We also conducted optical spectroscopic observations with the Low-Resolution Imaging Spectrometer (LRIS) at the Keck Observatory" (1 Introduction)
- External data: Dust mass for GDR  
  > "given the literature data of dust mass (cite: Draine:2007aa) and the upper limit of H i mass (cite: Horellou:2001aa)" (4.2.1 Infalling galaxy (galaxies)) [from Draine et al. 2007 (cite: Draine:2007aa)]
- External data: HI mass upper limit  
  > "given the literature data of dust mass (cite: Draine:2007aa) and the upper limit of H i mass (cite: Horellou:2001aa)" (4.2.1 Infalling galaxy (galaxies)) [from Horellou et al. 2001 (cite: Horellou:2001aa)]

## Processing

### Calibration

- pipeline or manual: ALMA Science Pipeline for 7M data  
  > "The absolute flux and gain fluctuations of the 7M data were calibrated with the ALMA Science Pipeline (version of r40896 of Pipeline-CASA51-P2-B) in the CASA 5.1.1 package." (2.2 ALMA data analysis with CASA)
- casa version: CASA 5.1.1 (calibration); CASA 5.4 (imaging)  
  > "The 7M $^{12}$CO($J$=1-0) mosaic data cube was generated with `TCLEAN` task in CASA version 5.4" (2.2 ALMA data analysis with CASA)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0522-3627 bandpass/flux; J0334-4008 phase  
  > "The objects J0334-4008 and J0522-3627 were observed as a phase calibrator and a bandpass/flux calibrator, respectively." (2.1 ALMA 7-m and total-power array observations)
- flux scale uncertainty: better than 5%  
  > "The flux accuracy of the ALMA 7M band-3 data is reported to be better than 5 % (ALMA proposer’s guide)." (2.2 ALMA data analysis with CASA)
- self calibration: _not stated_

### Imaging

- task: tclean (CASA 5.4) mosaic cube; 7M+TP combined with feather  
  > "The 7M and TP data are combined basically on the image plane with `FEATHER` task in CASA to account for zero spacing information." (2.2 ALMA data analysis with CASA)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "options of `Briggs` weighting with a `robust` parameter of 0.5" (2.2 ALMA data analysis with CASA)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: auto-multithresh: sidelobethreshold 1.25, noisethreshold 5.0, minbeamfrac 0.1, lownoisethreshold 2.0, negativethreshold 0.0; niter 10000  
  > "`sidelobethreshold` of 1.25, `noisethreshold` of 5.0, `minbeamfrac` of 0.1, `lownoisethreshold` of 2.0, and `negativethreshold` of 0.0), and `niter` of 10000." (2.2 ALMA data analysis with CASA)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 7M and TP feathered on image plane  
  > "The 7M and TP data are combined basically on the image plane with `FEATHER` task in CASA to account for zero spacing information." (2.2 ALMA data analysis with CASA)
- smoothing: _not stated_
- final beam: 15.2" x 7.7", PA 89 deg  
  > "The achieved synthesized beam was $15''.2 \times 7''.7$ ($1.5~{\rm kpc} \times 0.8~{\rm kpc}$ at the distance of NGC 1316) with a P.A. of 89$^\circ$." (2.2 ALMA data analysis with CASA)
- final rms: 12 mJy/beam at 9.9 km/s  
  > "with the final velocity resolution of 9.9 km s$^{-1}$ was 12 mJy beam$^{-1}$, after the primary beam correction." (2.2 ALMA data analysis with CASA)

### Inherited from earlier work

- Auto-masking parameter values taken from CASA Guides standard values for 7M data  
  > "`auto-multithresh` mask with standard values for 7M data provided in the CASA Guides for auto-masking" (2.2 ALMA data analysis with CASA) [from CASA Guides Automasking Guide]
- Details of full 64-galaxy sample to be given in the survey overview paper  
  > "Detailed information of the whole 64 galaxy samples will be presented in the forthcoming overview paper for the survey (Morokuma-Matsui et al. in prep.)." (2 Observations and data analysis) [from Morokuma-Matsui et al. in prep.]

### Not stated but needed to reproduce (our reading)

- Spatial cell size and image size of the cube
- Which channels were used for the final 9.9 km/s binning and the TP feathering scaling factor
- Line-free channels and continuum subtraction method
- Dust-mass and HI inputs and the exact GDR calculation
- Keck/LRIS PV extraction details and reduction software

## Analysis recipe

1. **Calibrate and image 7M data, combine with TP**: Pipeline calibration, tclean mosaic cube, feather with TP, primary beam correction  
  > "The 7M and TP data are combined basically on the image plane with `FEATHER` task in CASA to account for zero spacing information." (2.2 ALMA data analysis with CASA)
   - software: CASA, tclean, feather
   - parameter: Briggs robust 0.5, auto-multithresh, niter 10000  
  > "options of `Briggs` weighting with a `robust` parameter of 0.5" (2.2 ALMA data analysis with CASA)
   - fitting: _not stated_
   - validation: 7M+TP spectrum matched TP spectral profile  
  > "we verified that the 7M+TP data matched the spectral profile of the TP data" (2.2 ALMA data analysis with CASA)
2. **Detect CO emission and make moment maps**: SoFiA source finding with noise normalisation, smoothing kernels, 4 sigma threshold, friends-of-friends merging, reliability cuts; moment 1/2 blanked below 0.9 Jy/beam km/s  
  > "build a detection mask which includes voxels outside the 4 $\sigma$ range in at least one of the convolved cubes" (2.3 Moment maps: CO emission search with SoFiA)
   - software: SoFiA
   - parameter: merging radius 2 pixels, 3 channels; min size 3 pixels/channels; integrated S/N>3; dilation 2 pixels, 1 channel  
  > "remove from the detection mask all objects with an integrated S/N below 3;" (2.3 Moment maps: CO emission search with SoFiA)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive total molecular gas mass**: Sum moment-0 flux in a box, convert Jy/beam to K via Rayleigh-Jeans, apply X_CO and helium factor 1.36; error from noise map  
  > "The error for the molecular mass is calculated with a noise map as $\sigma_{rms} \sqrt{npts} ({\rm pixel\ scale})^2$" (3.1 Total molecular gas mass)
   - parameter: Box 120"x160", 114.497-114.73 GHz (1406.8-2013.55 km/s)  
  > "enclosed with a box centered on (R.A., Dec.)$_{\rm ICRS}=(03^{h}22^{m}41^{s}.448, -37^{\circ}12'16''.2)$ with a width of 120 arcsec and a height of 160 arcsec" (3.1 Total molecular gas mass)
   - assumption: Milky-Way X_CO = 2.0e20 cm^-2 (K km/s)^-1; distance 20.8 Mpc  
  > "standard CO-to-H$_2$ conversion factor of the Milky-Way of $X_{\rm CO}=2.0\times 10^{20}$ cm$^{-2}$ (K km s$^{-1}$)$^{-1}$" (3.1 Total molecular gas mass)
   - fitting: _not stated_
   - validation: Compared with previous single-dish masses  
  > "The obtained molecular gas mass is comparable to the previous single-dish observations" (3.1 Total molecular gas mass)
4. **Characterise velocity field with PV cuts and compare with Keck ionized gas**: Moment-1/2 maps and position-velocity cuts of CO; Keck/LRIS long-slit spectra PV maps compared at same PA  
  > "In Figure [5](#fig:pv_maps), the position-velocity (PV) maps are presented." (3.3.1 CO velocity field)
   - parameter: LRIS slit PA 158.56 deg, 1.0" slit, velocity accuracy ~100 km/s  
  > "The slit is set to cross the galaxy center with P.A. of 158.56 deg." (2.4 Keck/LRIS observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
5. **Estimate relaxation timescale and GDR/H2-HI ratios**: t_relax = t_dyn/epsilon with literature t_dyn and epsilon; GDR and H2/HI from literature dust and HI limit  
  > "For NGC 1316, $t_{\rm relax}$ is estimated to be $8\times10^8$ yr with $t_{\rm dyn}$ of $3\times10^8$ yr" (4.2.2 Timescales)
   - assumption: Potential eccentricity equals stellar eccentricity (0.4)  
  > "Here, we assume that the eccentricity of the potential is the same as that of stellar component." (4.2.2 Timescales)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.1.1 (calibration), 5.4 (imaging): Calibration, tclean, feather  
  > "Data calibration and imaging were conducted with the standard ALMA data analysis package, the Common Astronomy Software Applications" (2.2 ALMA data analysis with CASA)
- **ALMA Science Pipeline** r40896 of Pipeline-CASA51-P2-B: 7M calibration  
  > "calibrated with the ALMA Science Pipeline (version of r40896 of Pipeline-CASA51-P2-B)" (2.2 ALMA data analysis with CASA)
- **SoFiA** : Source finding and masks for moment maps  
  > "We searched for CO emission using the Source Finding Application (cite: Serra:2015aa)." (2.3 Moment maps: CO emission search with SoFiA)
- **Analysis Utilities (getALMAFluxForMS)** : Checking calibrator flux against other ALMA measurements  
  > "We utilized `getALMAFluxForMS` of the “Analysis Utilities”" (footnote 3)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total molecular gas mass (Galactic X_CO) | 5.62e8 | 0.53e8 | Msun | 3 | The total molecular gas mass is estimated to be $(5.62 \pm 0.53)\times 10^8$ M$_\odot$ |
| Central CO peak intensity | 26.8 mK at ~1720 km/s (4.2 sigma) | not stated | mK | 2 | a weak and narrow CO emission is detected with a peak intensity of $26.8$ mK at $\sim 1720$ km s$^{-1}$ |
| Velocity difference NW Shell-SE Blob | ~400 | not stated | km/s | 4 | The velocity difference between the NW Shell and the SE Blob ($\sim 400$ km s$^{-1}$ |
| Gas-to-dust ratio | ~28 | not stated | dimensionless | 5 | the obtained GDR and H$_2$/H i ratio of the dust patches are respectively $\sim 28$ and $\gtrsim 5.6$ |
| t_relax | 8e8 | not stated | yr | 5 | $t_{\rm relax}$ is estimated to be $8\times10^8$ yr |
| Molecular gas velocity dispersion | 20-50 | not stated | km/s | 4 | The velocity dispersion of the molecular gas is roughly in the range of $20-50$ km s$^{-1}$ at kpc-resolution. |

## Qualitative findings

- CO traces dust patches; shell in NW, blob in SE, clumps between  
  > "the spatial distribution of molecular gas traced with $^{12}$CO($J$=1-0) excellently matches the dust patches visible in the optical" (3.2 Spatial distribution)
- Halpha emission very weak in Keck/LRIS data  
  > "Keck/LRIS observation confirms that H$\alpha$ emission is very weak in NGC 1316" (6 Summary)

## Claim tuples

- H: Does ALMA recover the single-dish molecular gas mass? | E: Sum 7M+TP moment-0 with Galactic X_CO | R: (5.62±0.53)e8 Msun | F: Consistent with single-dish values | **supported**
- H: Is the molecular gas a simple rotating disk? | E: Moment and PV maps of CO and Keck ionized gas | R: Multiple velocity components, monotonic trend along shell, crossing systemic velocity | F: Disturbed velocity field, gas not settled | **supported**
- H: Is the gas of external origin and how recent? | E: Timescale estimate and GDR, H2/HI ratios from literature | R: t_relax ~8e8 yr; GDR~28, H2/HI>~5.6 | F: If external, injected within ~1 Gyr; unusual ratios need dust formation and HI-to-H2 conversion | **partially**
- H: Does the jet bend because of interaction with molecular gas? | E: Compare jet with CO distribution | R: Jet bends at dense regions toward sparser regions | F: Supports buoyancy and/or ram pressure | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Ram-pressure stripping alone judged unlikely to explain low GDR/high H2/HI  
  > "Therefore, the ram pressure stripping alone may not be able to explain the observed low GDR and high H$_2$/H i ratio of NGC 1316." (4.2.1 Infalling galaxy (galaxies))
- How they decided it was enough: _not stated_
- Limitation (authors): Keck velocity accuracy only ~100 km/s; IFU data needed  
  > "Uncertainty in absolute wavelength calibration of the data is $\lesssim2$ Å, roughly corresponding to an absolute value of velocities of $\sim100$ km s$^{-1}$." (2.4 Keck/LRIS observations and data reduction)
- Limitation (authors): Line-of-sight ordering and jet inclination hard to determine  
  > "it is difficult to estimate it with our current data set." (4.1 Relative line-of-sight location of each component)
- Caveat (inferred, ours): Coarse 15x8 arcsec beam limits kinematic interpretation
- Caveat (inferred, ours): Mass uses Galactic X_CO with no uncertainty from alpha_CO
- Caveat (inferred, ours): Timescale and GDR rely on literature inputs and assumptions
- Caveat (inferred, ours): Keck data uncalibrated in flux with ad hoc velocity offset

## Reproducibility

- Data public (paper): Project code given; ALMA archive data  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00129.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Cell size, image size, channel binning details
- Missing: Feather scaling and TP processing details
- Missing: Keck data reduction code and PV cut definitions
- Data volume (inferred): ~50-100 GB raw (7M+TP, 64-galaxy SB with 33 EBs)
- Score (inferred): 3/5, Imaging and mass recipe largely given with public data, but several imaging parameters and the extended discussion inputs are missing.
- Rediscovery candidate: yes, Public 7M/TP data, tclean and mass recipe stated, numeric mass result.

## Links

- Method: Serra et al. 2015 (cite: Serra:2015aa) (SoFiA source finding)
- Companion: Morokuma-Matsui et al. in prep. (Overview of ALMA Fornax 64-galaxy survey)
- Related: ALMA 12CO(1-0) survey of 64 Fornax galaxies

## Checks

```json
{
 "quotes": 62,
 "quotes_ok": 62,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 49,
  "rate": 0.628
 },
 "evidence_ok": true
}
```
