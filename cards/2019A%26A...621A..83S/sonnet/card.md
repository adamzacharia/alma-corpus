# Outflows in the inner kiloparsec of NGC 1566 as revealed by molecular (ALMA) and ionized gas (Gemini-GMOS/IFU) kinematics

`2019A&A...621A..83S` | Astronomy and Astrophysics 2019 | first author: Slater, R. | arXiv: 1804.02054 | DOI: 10.1051/0004-6361/201730634

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: Do the molecular (ALMA CO J:2-1) and ionized (Gemini-GMOS/IFU) gas kinematics in the inner kpc of NGC 1566 show outflows and/or streaming inflows rather than only rotation and bar perturbations, and how large are the associated mass flow rates?  
  > "The morphology and kinematics of stellar, molecular (CO) and ionized (\[N II\]) emission lines are compared to the expectations from rotation, outflows, and streaming inflows." (abstract)
- Target **NGC 1566**: coordinates _not stated_; z/distance 10 Mpc (systemic velocity 1504 km/s from HI)  
  > "we use the mean distance of 10 Mpc from NED" (Introduction); "The systemic velocity of NGC 1566 is 1504  km s$^{-1}$ from H I observations (NED)" (Introduction); distance from mean distance from NED, in agreement with Combes et al. 2014  
  > "we use the mean distance of 10 Mpc from NED" (Introduction); "The systemic velocity of NGC 1566 is 1504  km s$^{-1}$ from H I observations (NED)" (Introduction)

## Data provenance

- ALMA projects: 2012.1.00474.S
- bands: Band 6  
  > "using the ALMA Band 6 receivers on thirty-two 12-meter antennas" (Observations, Data Processing, and Software)
- frequencies and spectral setup: 4 SPWs centered 229.415, 227.060, 241.554, 243.735 GHz; bandwidths 1.875, 2.0, 1.875, 1.875 GHz; channel spacing 1.27, 20.53, 1.22, 1.21 km/s  
  > "The SPWs were thus centered on 229.415 GHz, 227.060 GHz, 241.554 GHz and 243.735 GHz, with bandwidths of 1.875 GHz, 2.0 GHz, 1.875 GHz and 1.875 GHz, respectively" (Observations, Data Processing, and Software)
- continuum bandwidth: _not stated_
- arrays: thirty-two 12-m antennas  
  > "using the ALMA Band 6 receivers on thirty-two 12-meter antennas" (Observations, Data Processing, and Software)
- configurations: _not stated_
- baselines: 17 m to 650 m  
  > "Antenna baselines ranged from 17 m to 650 m" (Observations, Data Processing, and Software)
- angular resolution: 0.52" x 0.35" (robust=-2); 0.6" x 0.5" (robust=2)  
  > "have a synthesized beam of 0.52$''$ $\times$ 0.35$''$ (beam PA= 13$^\circ$)" (Observations, Data Processing, and Software)
- max recoverable scale: _not stated_
- sensitivity: ~1 mJy/beam per channel (robust=-2); 1.2 mJy/beam (robust=2)  
  > "The r.m.s. noise per channel in line free channels is $\sim$1 mJy/beam" (Observations, Data Processing, and Software)
- time on source: two observation blocks totalling 124 min  
  > "Observations were carried out in two continuous observation blocks, totalling 124 min." (Observations, Data Processing, and Software)
- observing dates: June 29, 2014  
  > "The observations of NGC 1566 were taken on June 29, 2014" (Observations, Data Processing, and Software)
- pi or archival as stated: PI Nagar, own project (Cycle 2)  
  > "project-ID 2012.1.00474.S (PI: Nagar)" (Observations, Data Processing, and Software)
- Line: CO J=2-1 (229.401922 GHz (nu_obs))
- Other facility **Gemini-GMOS/IFU**: Ionized gas ([N II]) and stellar kinematics, program GS-2011B-Q-23  
  > "(*program ID: GS-2011B-Q-23*; P.I. Nagar)" (Observations, Data Processing, and Software)
- Other facility **HST F606W**: image used for structure map  
  > "running the IDL routine ‘unsharp_mask.pro’ on a HST image taken through the F606W filter" (Results)
- Other facility **ALMA archive (C14 CO J:3-2)**: CO J:3-2 data to compare fluxes  
  > "we downloaded the CO J:3-2 data of C14 from the *ALMA Science Archive*" (Molecular mass in the inner kiloparsec)
- External data: 2-10 keV nuclear luminosity (7±3)e33 W  
  > "The nuclear 2–10 keV luminosity as measured by *XMM* and scaled to our adopted distance (10 Mpc) is $\rm L_{X}=(7\pm3)\times10^{33}~[W]$" (Bolometric luminosity and accretion, inflow, and outflow rates) [from (cite: levenson2009)]
- External data: Nuclear [O III] flux  
  > "The nuclear \[O III\] flux (cite: moustakas2010) at our adopted distance" (Bolometric luminosity and accretion, inflow, and outflow rates) [from (cite: moustakas2010)]
- External data: alpha_CO = 4.3 Msun/(K km/s pc^2)  
  > "we use the value $\rm \alpha_{CO}$$\rm =4.3~[M_{\odot}~(K~km~s^{-1}~pc^{2})^{-1}]$ as suggested by (cite: bolatto2013)" (Molecular mass in the inner kiloparsec) [from (cite: bolatto2013)]
- External data: M-sigma relation  
  > "we use that of (cite: gultekin2009) for their entire sample" (Mass of the SMBH in NGC 1566) [from (cite: gultekin2009)]
- External data: CO J:2-1/J:1-0 intensity ratio of 1 in temperature units  
  > "The nuclear CO J:2-1 / CO J:1-0 intensity ratio found by (cite: bajaja95) is 1 in temperature units" (Molecular mass in the inner kiloparsec) [from (cite: bajaja95)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.2.1  
  > "Data were calibrated and imaged using CASA 4.2.1 (cite: casa)." (Observations, Data Processing, and Software)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0519-4546 (Pictor A), also phase and bandpass  
  > "The nearby radiogalaxy J0519-4546 (PICTOR A) was used as a phase, bandpass and flux-calibrator." (Observations, Data Processing, and Software)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA; moment maps with immoment  
  > "The task *immoment* of CASA was used to create moment (integrated flux, velocity, and dispersion and skewness) maps" (Observations, Data Processing, and Software)
- deconvolver: _not stated_
- weighting robust: Briggs robust=-2 (highest resolution) and robust=2 (natural)  
  > "made with Brigg’s weighting with the *robust* parameter set to $-$2" (Observations, Data Processing, and Software)
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
- final beam: 0.52" x 0.35" PA 13 deg (robust -2); 0.6" x 0.5" PA 15.6 deg (robust 2)  
  > "have a resolution of 0.6$''$ $\times$ 0.5$''$ (beam PA= 15.6$^\circ$)" (Observations, Data Processing, and Software)
- final rms: ~1 mJy/beam (robust -2), 1.2 mJy/beam (robust 2) per channel  
  > "an r.m.s. noise per channel of 1.2 mJy/beam in line free channels" (Observations, Data Processing, and Software)

### Inherited from earlier work

- Assumed thermalized optically-thick CO (L'CO 2-1/1-0 = 1)  
  > "We thus, as in C14, assume thermalized optically-thick gas" (Molecular mass in the inner kiloparsec) [from C14 (Combes et al. 2014)]
- Pattern speed 120 km/s/kpc used as reference  
  > "it uses a pattern speed argued for in C14 (based on corotation placed at the bar end)" (Modelling Observed Velocities: Bar perturbations) [from C14]
- Linear bar perturbation analysis  
  > "based on the the linear perturbation analysis described in (cite: wong2004; fathiphd2004)" (Modelling Observed Velocities: Bar perturbations) [from (cite: wong2004; fathiphd2004)]
- Modified Kinemetry with improved optimization  
  > "This modified version uses an improved global optimization thereby yielding results that are less affected by the starting values" (Observations, Data Processing, and Software) [from (cite: venki2017)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges and continuum subtraction method for the CO cube
- Cell size, image size, deconvolution settings, masks/clean threshold
- Flux scale uncertainty and any self-calibration
- Calibrator flux density for Pictor A
- Exact apertures and Gaussian fit details for nuclear spectrum decomposition
- Details of the Kinemetry global optimization (modified code unreleased)
- Finlez PhD bar perturbation code is not public
- Coordinates of the nucleus and rest frequency adopted for velocity zero point
- Pipeline vs manual calibration

## Analysis recipe

1. **Make CO J:2-1 cubes and moment maps**: Imaged in CASA with Briggs weighting; moment maps with immoment  
  > "The task *immoment* of CASA was used to create moment (integrated flux, velocity, and dispersion and skewness) maps from the above data cubes." (Observations, Data Processing, and Software)
   - software: CASA
   - parameter: robust=-2 and robust=2; 1.3 km/s channels  
  > "we were able to map the CO line at the observed channel spacing of 1.3 km s$^{-1}$" (Observations, Data Processing, and Software)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit rotation with Kinemetry and build rotation models**: Kinemetry two-pass fit (PA, inclination free then fixed to median) with six odd Fourier terms; also solid-body and ModC2014 models; Bertola model fit to stellar field  
  > "In the first run both the PA and inclination were allowed to vary with radius, and in the second run we fixed both to their median values from the first run." (Modeling the Observed Velocities: Rotation)
   - software: Kinemetry
   - parameter: PA=45 deg, i=33 deg; Bertola A=200 km/s, p=1.5  
  > "The best fit parameters obtained were *A*=200 km s$^{-1}$, *p*=1.5, PA=45$^\circ$" (Modeling the Observed Velocities: Rotation)
   - assumption: m=2 modes  
  > "We assumed m=2 modes and thus use six (odd) Fourier decomposition terms." (Modeling the Observed Velocities: Rotation)
   - fitting: _not stated_
   - validation: Residual maps compared across three rotation models  
  > "The *Kinemetry* model results in the best and most symmetrical residual velocity map for CO J:2-1" (Modeling the Observed Velocities: Rotation)
3. **Extract ionized gas and stellar kinematics from GMOS**: Gauss-Hermite and double Gaussian fits to [N II] with profit; pPXF on Voronoi-binned cube for stars  
  > "Ionized gas kinematics were obtained by fitting Gauss-Hermite polynomials and double Gaussians to the \[N II\] 6583Å emission line using a modified version of the *profit* routine" (Observations, Data Processing, and Software)
   - software: profit, pPXF, IRAF
   - parameter: Voronoi bins with minimum S/N 25  
  > "to achieve a minimum signal to noise of 25 in the continuum near the \[O III\] line" (Observed Moment Maps: ALMA and Gemini-GMOS/IFU)
   - fitting: _not stated_
   - validation: _not stated_
4. **Build pv diagrams and empirical outflow model**: pv diagrams with 0.2" slit; outflow velocities measured along the minor axis from brightest CO emission, interpolated and deprojected assuming in-disk outflow  
  > "The final outflow model starts with outflow velocities in the disk of 157 km s$^{-1}$ at the (unresolved) nucleus and decreases monotonically to zero velocity 2$''$ from the nucleus." (Observed Position-Velocity (pv) Diagrams: ALMA)
   - parameter: slit width 0.2"  
  > "These pv diagrams were extracted from the ALMA datacubes using a slitwidth of 0.2$''$" (Observed Position-Velocity (pv) Diagrams: ALMA)
   - assumption: outflow in the plane of the disk  
  > "deprojected (assuming that the outflow is in the disk)" (Observed Position-Velocity (pv) Diagrams: ALMA)
   - fitting: _not stated_
   - validation: Rotation+outflow model overlaid on pv diagrams at several PAs  
  > "provides a much better fit (as compared to a pure rotational model) to the inner 2$''$ in the pv diagrams at all PAs" (Modeling Observed Velocities: Molecular Outflows?)
5. **Test bar perturbations**: Diskfit m=2 fit to CO velocity field and linearized epicyclic bar perturbation code on exponential disk rotation curves, varying pattern speed and damping  
  > "The bar pattern speed ($\Omega$) and the damping factor ($\lambda$) were allowed to vary." (Modelling Observed Velocities: Bar perturbations)
   - software: Diskfit
   - parameter: bar PA 0 deg, bar ellipticity 0.42; reference Omega=120 km/s/kpc, lambda=0.2  
  > "the bar ellipticity ($\epsilon=0.42$), the latter derived from our *Diskfit* decomposition" (Modelling Observed Velocities: Bar perturbations)
   - assumption: constant M/L for bulge, disk, bar; disk mass adjusted to 6e9 Msun (gas) or ~2e9 (stellar)  
  > "We further assume a constant mass to light (M/L) ratio for all three components." (Modelling Observed Velocities: Bar perturbations)
   - fitting: Disk mass adjusted by eye  
  > "in order to better fit (by eye) the model rotation curve of the CO in the inner disk" (Modelling Observed Velocities: Bar perturbations)
   - validation: Compared model to residual map and pv diagrams  
  > "it fails to predict (by a factor $\sim$2) the large peak velocities seen along the minor axis" (Modelling Observed Velocities: Bar perturbations)
6. **Test streaming inflow with toy model**: Constant radial inflow of 50 km/s projected and added to rotation, compared to aperture spectra and skewness maps  
  > "constant radial inflow velocity (which we fix to 50 km s$^{-1}$ after initial inspection of the results)" (Modeling Observed Velocities: CO J:2-1 Streaming?)
   - parameter: skewness computed to 10% of peak flux  
  > "the skewness was calculated using the spectral profile down to 10% of the peak flux" (Modeling Observed Velocities: CO J:2-1 Streaming?)
   - fitting: _not stated_
   - validation: _not stated_
7. **Derive molecular gas masses and flow rates**: L'CO from integrated flux, M=alpha_CO L'CO; nuclear 0.2" spectrum decomposed into Gaussians; rate = mass/crossing time  
  > "Molecular gas mass is typically estimated from the CO luminosity (cite: solbout2005) using M$_{\rm mol}~[M_{\odot}] = \alpha_{CO} \times$$\rm L^{\prime}_{CO}$" (Molecular mass in the inner kiloparsec)
   - parameter: alpha_CO=4.3, D_L=10 Mpc, nuclear aperture r=0.2", v_outflow~180 km/s  
  > "the velocity of the outflows in the nucleus is $\sim180$ km s$^{-1}$ in the plane of the disk, which gives a crossing time of around $5.42\times10^{4}~[yr]$" (Bolometric luminosity and accretion, inflow, and outflow rates)
   - assumption: thermalized optically thick CO, L'(2-1)/L'(1-0)=1  
  > "i.e. $L^{\prime}_{\rm CO J:2-1}$/$L^{\prime}_{\rm CO J:1-0}$ = 1" (Molecular mass in the inner kiloparsec)
   - fitting: _not stated_
   - validation: CO J:3-2 vs 2-1 flux ratio check  
  > "the integrated CO J:2-1 flux density ($\rm 251\pm25~[Jy~km~s^{-1}]$) is 1/2.3 times that of CO J:3-2" (Molecular mass in the inner kiloparsec)
8. **Estimate SMBH mass, Lbol and accretion rate**: pPXF sigma_* into Gultekin 2009 M-sigma; Lbol from X-ray and [O III], mean adopted; mdot = Lbol/(c^2 eta)  
  > "$$\begin{equation}
\label{accrateeq}
 \dot{m}=\frac{L_{Bol}}{c^{2}\eta}
\end{equation}$$" (Bolometric luminosity and accretion, inflow, and outflow rates)
   - software: pPXF
   - parameter: eta=0.1; Lbol=6.7 LX(2-10keV); Lbol=90 L[OIII]  
  > "($\rm L_{Bol}=6.7\times L_{X(2-10keV)}$)" (Bolometric luminosity and accretion, inflow, and outflow rates)
   - assumption: accretion efficiency 0.1  
  > "is typically taken to be 0.1" (Bolometric luminosity and accretion, inflow, and outflow rates)
   - fitting: _not stated_
   - validation: Two Lbol methods agree  
  > "These two methods thus give relatively consistent values for $\rm L_{Bol}$" (Bolometric luminosity and accretion, inflow, and outflow rates)

## Software

- **CASA** 4.2.1: calibration, imaging, immoment moment maps  
  > "Data were calibrated and imaged using CASA 4.2.1 (cite: casa)." (Observations, Data Processing, and Software)
- **Kinemetry** : fit PA, inclination and circular velocity field of CO and [N II]  
  > "We used a modified version of the *Kinemetry* package (cite: kraj2006) to constrain the major axis and inclination of NGC 1566" (Observations, Data Processing, and Software)
- **profit** : Gauss-Hermite and double-Gaussian fits to [N II]  
  > "using a modified version of the *profit* routine (cite: riffel2010)" (Observations, Data Processing, and Software)
- **pPXF** : stellar velocity and dispersion  
  > "determined by using the *Penalized Pixel Fitting (*pPXF*)* code (cite: capandems2004)" (Observations, Data Processing, and Software)
- **Diskfit** : velocity-field bar perturbation fit and IRAC image decomposition  
  > "We used *Diskfit* to decompose an IRAC 3.6$\mu$ image of NGC 1566" (Modelling Observed Velocities: Bar perturbations)
- **IRAF gemini.gmos** : GMOS data reduction  
  > "The data was processed using specific tasks developed for GMOS data in the *gemini.gmos IRAF* package." (Observations, Data Processing, and Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Inclination from CO Kinemetry | 33 | not stated | deg | 2 | a galaxy disk inclination of i=33$^\circ$, as derived from our CO data |
| Integrated CO J:2-1 systemic velocity | 1485 | not stated | km/s | 1 | the galaxy’s integrated CO J:2-1 profile is centered on a systemic velocity of $1485$ km s$^{-1}$ |
| Nuclear CO FWZI | 200 | not stated | km/s | 4 | double peaked profile with Full Width at Zero Intensity (FWZI) $\sim$200 km s$^{-1}$ |
| Molecular gas mass in inner spiral arms | 6.6e7 | 0.7e7 | Msun | 7 | the molecular gas mass in the inner spiral arms is $(6.6\pm0.7)\times 10^{7} [M_{\odot}]$ |
| Total molecular gas mass in central 12"x12" | 1.1e8 | 0.1e8 | Msun | 7 | $(1.1\pm0.1)\times 10^{8} [M_{\odot}]$ |
| Stellar velocity dispersion | 116 | 9 | km/s | 8 | $\sigma_{\star}=116\pm9$  km s$^{-1}$ |
| SMBH mass | 1.3e7 | 0.6e7 | Msun | 8 | $M_{BH}=1.3\pm0.6\times10^{7}~[M_{\odot}]$ |
| Adopted Lbol | 2.7e34 | 1.3e34 | W | 8 | $\rm L_{Bol} = (2.7\pm1.3)\times10^{34}~[W]$ |
| SMBH accretion rate | 4.8e-5 | 2.3e-5 | Msun/yr | 8 | $\dot{m}=(4.8\pm2.3)\times10^{-5}~[M_{\odot}yr^{-1}]$ |
| Nuclear outflow rate (blue) | 3.7 | not stated | Msun/yr | 7 | $\rm 3.7~[M_{\odot}yr^{-1}]$ for the blueshifted component |
| Nuclear outflow rate (red) | 1.9 | not stated | Msun/yr | 7 | $1.9~[M_{\odot}yr^{-1}]$ for the redshifted component |
| Molecular streaming inflow rate | 0.1 | not stated | Msun/yr | 7 | a mass inflow rate of $\rm 0.1~[M_{\odot}yr^{-1}]$ along this spiral arm |
| Outflow kinetic power | 7.62e33 | not stated | W | 7 | $\rm \dot{E}_{out}=7.62\times10^{33}~[W]$ |
| Total mass in nuclear outflow out to ~72 pc | 2.1e7 | not stated | Msun | 7 | we find a mass of $2.1\times10^{7}~[M_{\odot}]$ |

## Qualitative findings

- Ionized gas [N II] shows a narrow rotating component and a broad blueshifted component interpreted as a spherical outflow in the inner ~100 pc  
  > "We postulate that the broad component of ionized gas is part of a nuclear spherical outflow." (Summary and Conclusions)

## Claim tuples

- H: Nuclear CO non-circular motions are due to an in-disk molecular outflow rather than only bar perturbations | E: Residual velocity maps, pv diagrams, Diskfit and linear bar perturbation models | R: Bar models fail to reproduce minor-axis velocities and morphology; rotation+outflow fits pv diagrams in inner 2" | F: Favour a decelerating molecular outflow in the disk (~180 km/s), without excluding bar effects | **supported**
- H: Ionized gas shows an outflow | E: Two-component Gaussian fits to [N II] | R: Broad blueshifted component of sigma ~140-160 km/s not following rotation | F: Spherical ionized outflow in inner ~100 pc | **supported**
- H: Streaming inflows feed the nucleus | E: Toy 50 km/s inflow model compared to aperture spectra and skewness | R: Only some aperture spectra along the E arm are consistent; W arm inconsistent | F: Some evidence only; inflow rate ~0.1 Msun/yr exceeds SMBH accretion | **partially**
- H: Outflow energetics relative to AGN power | E: Outflow mass, rate and kinetic power vs Lbol | R: Edot_out/Lbol ~0.28 | F: Larger than ionized-gas outflow ratios, suggesting ionized gas is a minor fraction | **supported**

## Reasoning

- Why this data: New CO J:2-1 data have higher spectral resolution, sensitivity and uv coverage than the earlier Cycle 0 CO J:3-2  
  > "These new CO J:2-1 observations are more sensitive allowing us to create datacubes at the intrinsic channel spacing of the observations" (Introduction)
- Why this method: _not stated_
- Alternative: Polar and spherical molecular outflow rejected; starburst-driven outflow disfavoured  
  > "A spherical outflow scenario can be rejected as this would produce a large velocity dispersion centered on zero velocity" (Modeling Observed Velocities: Molecular Outflows?)
- How they decided it was enough: _not stated_
- Limitation (authors): Distance uncertain; warped or non-coplanar disks cannot be constrained; outer CO velocity field sparse  
  > "cannot be constrained by us due to the limited resolution, the sparse velocity field, and the lack of a reliable circular rotation model for the galaxy" (Modeling Observed Velocities: Molecular Outflows?)
- Caveat (inferred, ours): Outflow interpretation rests on assumed in-disk geometry and deprojection; bar models are not exhaustively explored
- Caveat (inferred, ours): Rotation model is empirical (ModC2014) and choice affects residuals
- Caveat (inferred, ours): Distance and alpha_CO assumptions drive masses and rates by factors of several
- Caveat (inferred, ours): Pattern-speed tension may reflect distance error or a missing inner bar
- Caveat (inferred, ours): No formal uncertainties or fitting statistics for outflow velocity model

## Reproducibility

- Data public (paper): ALMA data acknowledged by project code; CO J:3-2 data obtained from ALMA archive  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00474.S ." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging parameters (cell, size, masks, clean threshold)
- Missing: Modified Kinemetry and Finlez bar-perturbation code
- Missing: GMOS reduction details
- Missing: Exact apertures and Gaussian decomposition of nuclear spectrum
- Data volume (inferred): ~10-50 GB (one ALMA Band 6 EB set, 4 SPWs) plus small Gemini cube
- Score (inferred): 3/5, ALMA data public and key numbers given, but imaging settings, custom codes and many by-eye choices are missing.
- Rediscovery candidate: no, Recipe incomplete (imaging settings, unreleased codes, by-eye model choices), though data are public.

## Links

- Method: (cite: kraj2006) (Kinemetry method)
- Method: (cite: diskfit2007) (Diskfit)
- Method: (cite: wong2004) (Linear bar perturbation theory)
- Method: (cite: capandems2004) (pPXF)
- Companion: C14 (cite: combes2014) (ALMA Cycle 0 CO J:3-2 study of NGC 1566)
- Companion: (cite: smajic2015) (SINFONI + ALMA study of NGC 1566 kinematics)
- Companion: (cite: dasilva2017) (IFU study of [O III] outflow in NGC 1566)
- Related: ALMA survey of five nearby Seyfert galaxies (2012.1.00474.S)

## Checks

```json
{
 "quotes": 91,
 "quotes_ok": 91,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 14,
 "numeric_problems": 0,
 "fill": {
  "facts": 101,
  "stated": 68,
  "rate": 0.673
 },
 "evidence_ok": true
}
```
