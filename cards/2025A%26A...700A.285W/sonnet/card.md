# Gravitational torques from lopsided young stellar component sustain high black hole accretion rates in NGC 4593

`2025A&A...700A.285W` | Astronomy and Astrophysics 2025 | first author: Winkel, N. | arXiv: 2506.19902 | DOI: 10.1051/0004-6361/202553991

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, nearby_galaxies
- Question: What secular mechanism drives high SMBH accretion rates in NGC 4593, from kpc-scale gas down to the SMBH sphere of influence?  
  > "The aim of this study is to identify the secular mechanism driving high SMBH accretion rates" (abstract)
- Target **NGC 4593**: coordinates _not stated_; z/distance z=0.0085 ± 0.0003; D_L = 36.6 Mpc  
  > "Based on NGC 4593’s spectroscopic redshift of $z=0.0085 \pm 0.0003$, as measured in Sect. [3.2](#subsec:Analysis_Spectral_Synthesis), we adopted a luminosity distance of 36.6 Mpc." (1 Introduction); distance from Ca II triplet fit to MUSE WFM spectrum; flat LCDM H0=70  
  > "Based on NGC 4593’s spectroscopic redshift of $z=0.0085 \pm 0.0003$, as measured in Sect. [3.2](#subsec:Analysis_Spectral_Synthesis), we adopted a luminosity distance of 36.6 Mpc." (1 Introduction)

## Data provenance

- ALMA projects: 2017.1.00236.S, 2018.1.00978.S
- bands: Band 6, CO(2-1)  
  > "With the superior resolution of the ALMA Band 6 data set" (3.1 The single-arm spiral)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.23'' (39 pc) lower-res program; 40 mas (6.7 pc) higher-res program  
  > "yielding a major axis of the synthesized beam $b_{\rm maj} = 0.23\ensuremath{''}$ (39 pc)" (2.1 ALMA imaging); "$b_{\rm maj} = 40\,{\rm mas}$ (6.7 pc, $\sim 4 \times R_{\rm SOI}$)" (2.1 ALMA imaging)
- max recoverable scale: _not stated_
- sensitivity: rms ~8e-4 Jy/beam per 30 km/s channel  
  > "The combined cube has an rms noise of $\sim 8 \times 10^{-4}$ Jy/beam per $30\,{\rm km\,s}^{-1}$ channel" (2.1 ALMA imaging)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Programs by Malkan (2017.1.00236.S) and Jahnke (2018.1.00978.S, own team)  
  > "Prog.ID 2017.1.00236.S (PI: Malkan)" (2.1 ALMA imaging)
- Line: CO J=2-1 (not stated)
- Other facility **HST/ACS HRC F330W**: Archival UV image used to find and model the diffuse young stellar component  
  > "NGC 4593 was observed with the High Resolution Camera (HRC) of the Advanced Camera for Surveys (ACS), using the F330W filter under Prop.ID 9379" (2.2 Hubble Space Telescope imaging)
- Other facility **VLT/MUSE WFM and NFM**: Ionised gas emission lines, stellar kinematics, SFR maps, SOI velocity dispersion  
  > "NGC 4593 was observed with MUSE in both the wide field mode (WFM) and narrow field mode (NFM)." (2.3 Optical 3D spectroscopy)
- External data: Black hole mass 4.47e6 Msun (dynamical BLR modelling)  
  > "Using the dynamically measured black hole mass of $M_{\rm BH} = 4.47^{+3.85}_{-1.30} \times 10^6 \,{\rm M}_{\odot}$ (cite: Williams:2018)" (3.2 Spectral synthesis modelling) [from (cite: Williams:2018)]
- External data: Eddington ratio and bolometric luminosity 4.4e43 erg/s  
  > "Adopting NGC 4593’s bolometric AGN luminosity $L_{\rm bol} = 4.4 \times 10^{43}\,{\rm erg/s}$ estimated from its H$\beta$ luminosity (cite: Husemann:2022)" (4.2 Inflow mass rate and BHAR) [from (cite: Husemann:2022)]
- External data: rKS relation at 100 pc (A=-9.96, alpha=1.06)  
  > "via the 100 pc rKS relation from (cite: Pessa:2021) ($A=-9.96$, $\alpha_{100\,{\rm pc}} = 1.06$)" (3.4 Star formation along the single-arm spiral) [from (cite: Pessa:2021)]
- External data: Galaxy-scale CO(1-0) and GALEX UV Sigma_mol and Sigma_SFR within 3.6 kpc  
  > "$\Sigma_{\rm mol}^{<3.6\,{\rm kpc}} = 38.10 \pm 1.42 \,{\rm M}_\odot/{\rm pc}^2$" (3.3 Star formation rates) [from (cite: Diaz-Garcia:2021)]
- Simulation/model as data: GALAXEV/CB09 stellar population models for M_star bounds of young component  
  > "Specifically, we used the stellar population models generated with the `GALAXEV` code (cite: Bruzual:2003)." (3.6.2 Mass of the young stellar component)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5  
  > "using a Briggs robust parameter of 0.5, which provides an optimal balance between spatial resolution and sensitivity" (2.1 ALMA imaging)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: performed for 2017.1.00236.S data in CASA v5.4.0-70  
  > "Using CASA v5.4.0-70, we continuum-subtracted and reconstructed the cube at 10 km s${^{-1}}$ resolution" (2.1 ALMA imaging)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: two datasets jointly imaged; 30 km/s channels  
  > "We created a data cube where we jointly image the two data sets" (2.1 ALMA imaging)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: ~8e-4 Jy/beam per 30 km/s  
  > "The combined cube has an rms noise of $\sim 8 \times 10^{-4}$ Jy/beam per $30\,{\rm km\,s}^{-1}$ channel" (2.1 ALMA imaging)

### Inherited from earlier work

- MUSE spectral synthesis and PSF deblending procedure  
  > "We followed the procedure outlined in (cite: Winkel:2022)." (3.2 Spectral synthesis modelling) [from (cite: Winkel:2022)]
- Gravity torque method  
  > "we followed the method of (cite: Garcia-Burillo:2005)" (3.7.1 Torques: Methodology) [from (cite: Garcia-Burillo:2005)]

### Not stated but needed to reproduce (our reading)

- CASA tclean parameters (cell, image size, mask, niter, threshold), line-free channels, and rest frequency
- ALMA calibration/pipeline version and flux calibrator details for both programs
- Whether CASA was used for the joint imaging of the combined cube
- KinMS_fitter prior ranges, number of walkers and burn-in; skySampler settings
- Aperture and masks used to measure total CO flux and M_mol
- Spiral-fit procedure and exact apertures for SFR and depletion time
- How the 2% AGN-fuelled fraction was chosen beyond being consistent with the present state

## Analysis recipe

1. **Make CO(2-1) cube**: Continuum-subtract and jointly image the two ALMA datasets into a 30 km/s cube  
  > "We created a data cube where we jointly image the two data sets using a Briggs robust parameter of 0.5" (2.1 ALMA imaging)
   - software: CASA
   - parameter: robust = 0.5, 30 km/s channels  
  > "The cube was constructed with a frequency resolution equivalent to 30 km s${^{-1}}$." (2.1 ALMA imaging)
   - assumption: alpha_CO = 1/10 of MW value 4.35 (conservative); 1/2 as optimistic  
  > "we assume a constant $\alpha_{\rm CO} = 1/10 \, \alpha_{\rm CO}^{\rm MW}$ for NGC 4593’s nuclear single-arm spiral" (2.1 ALMA imaging)
   - fitting: _not stated_
   - validation: _not stated_
2. **MUSE spectral synthesis, deblending, SOI**: QDeblend3D PSF subtraction, PyParadise fitting of binned stellar continuum and Gaussian emission lines; Ca II triplet for sigma_star and redshift; R_SOI = GM/sigma^2  
  > "For an estimation of the SOI size of NGC 4593’s SMBH we used $R_{\rm SOI} = G M_{\rm BH} /\sigma_\star^2$." (3.2 Spectral synthesis modelling)
   - software: PyParadise, QDeblend3D, Voronoi binning, ESO Reflex/EsoRex
   - parameter: Voronoi min S/N 20 in 5080–5260 Å; CB09 templates; [NII], [OIII] ratio fixed to 2.96  
  > "to achieve a minimum S/N of 20 in the stellar continuum between 5080–5260 Å" (3.2 Spectral synthesis modelling)
   - fitting: _not stated_
   - validation: _not stated_
3. **Star formation rates**: Extinction-correct Halpha with Balmer decrement, separate AGN/SF via BPT mixing with Rainbow, convert with Calzetti 2007 SFR calibration  
  > "we employed the Baldwin, Phillips, and Terlevich (BPT) diagram and modelled the mixing sequence using `Rainbow`" (3.3 Star formation rates)
   - software: Rainbow
   - parameter: intrinsic Halpha/Hbeta = 2.86; Te=1e4 K; ne=100 cm^-3; R_V=3.1  
  > "using an intrinsic Balmer decrement of H$\alpha$/H$\beta$ = 2.86, an electron temperature of $T_e = 10^4 \,{\rm K}$, and density $n_e = 100\,{\rm cm}^{-3}$" (3.3 Star formation rates)
   - fitting: Rainbow likelihood maximisation giving posterior for f_SF  
  > "`Rainbow` maximises a likelihood function over the line ratio parameter space, returning posterior probability distributions for $f_{\rm SF}$" (3.3 Star formation rates)
   - validation: Compared Sigma_mol and Sigma_SFR within 3.6 kpc with Diaz-Garcia et al. 2021  
  > "To assess the consistency of SF estimates, we compared our results to those of (cite: Diaz-Garcia:2021)" (3.3 Star formation rates)
4. **Depletion time along spiral**: Parametrize spiral with polynomial, extract Sigma_mol and Sigma_SFR in 200 pc apertures on 100 pc grid, compute t_dep  
  > "Along this spiral path, we extract $\Sigma_{\rm mol}$ and $\Sigma_{\rm SFR}$ in 200 pc-wide apertures" (3.4 Star formation along the single-arm spiral)
   - parameter: a=0.04, b=-0.93, theta in [0,3pi]  
  > "$a=0.04$, $b=-0.93$ are best-fitting parameters over the range $\theta = [0,3\pi]$" (3.4 Star formation along the single-arm spiral)
   - fitting: _not stated_
   - validation: Trends robust to resolution 100–300 pc and aperture 100–400 pc  
  > "across aperture widths ranging from 100 to 400 pc" (3.4 Star formation along the single-arm spiral)
5. **Fit molecular gas kinematics**: KinMS forward modelling with arctan rotation curve, black hole mass, and radial motions in 20 bins; outer and inner cubes fitted separately; inflow rate from v_rad  
  > "we employ the Kinematic Molecular Simulation (KinMS) routines from (cite: Davis:2013), specifically the `KinMS_fitter`" (3.5 Molecular gas kinematic modelling)
   - software: KinMS, KinMS_fitter, skySampler
   - parameter: outer: 0.23'' cube; inner: 1.1''x1.1'' cutout at 40 mas; M_BH fixed log 6.65  
  > "the ‘inner’ region is modelled using a $1.1\ensuremath{''} \times 1.1\ensuremath{''}$ cutout cube at a resolution of $b_{\rm maj} = 40\,{\rm mas}$" (3.5 Molecular gas kinematic modelling)
   - fitting: MCMC, uniform priors, 30,000 samples  
  > "we assumed uniform priors with sensible boundaries, and ran 30,000 samples" (3.5 Molecular gas kinematic modelling)
   - validation: Inner and outer best-fit parameters consistent  
  > "the best-fitting kinematic parameters, listed in Table [1](#tbl:KinMS_results), are consistent with each other" (3.5 Molecular gas kinematic modelling)
6. **Decompose HST UV image**: PSF subtraction using stacked standard-star PSFs and single-Sérsic fit of diffuse component with galight  
  > "we employed the open-source software `galight` [^4] (cite: Ding:2020), which uses the two-dimensional image modelling provided by `lenstronomy`" (3.6.1 Photometric decomposition)
   - software: galight, lenstronomy, L.A.Cosmic
   - parameter: uniform priors 0.01''<Reff<4.0'', 0.3<n<9; innermost 0.2'' masked  
  > "Uniform priors were applied to the effective radius $0.01\ensuremath{''} < R_{\rm eff} <  4.0\ensuremath{''}$" (3.6.1 Photometric decomposition)
   - fitting: galight MCMC  
  > "derived from `galight`’s Markov chain Monte Carlo decomposition" (3.6.1 Photometric decomposition)
   - validation: Feature persists with different PSF subsets and 90° rotation  
  > "the extended feature near the centre persists." (3.6.1 Photometric decomposition)
7. **Stellar mass of young component**: GALAXEV composite models predicting F330W magnitude over grid of metallicity, optical depth, SFR decay time  
  > "we employed `pygalaxev`[^5] to create composite stellar population models and predict the F330W broadband magnitudes" (3.6.2 Mass of the young stellar component)
   - software: pygalaxev, GALAXEV
   - parameter: 0.01<Z/Zsun<5; 0.1<tau_V<3; 0.1<tau<2 Gyr  
  > "we assume a metallicity range of 0.01 \< Z/Z$_\odot < 5$" (3.6.2 Mass of the young stellar component)
   - fitting: _not stated_
   - validation: _not stated_
8. **Gravitational torques and inflow rate**: Garcia-Burillo 2005 method: deproject, compute potential and torque from Sérsic young-star mass map, weight by Sigma_mol, derive dL/L and inflow rate  
  > "We estimate the time derivative of the angular momentum surface density $dL_s(x,y)/dt$ by weighting $t(x,y)$ with the molecular gas column density" (3.7.1 Torques: Methodology)
   - parameter: PA=5°, i=38°, M_young=1e8.5 for illustration  
  > "using an affine transformation with a position angle ${\rm PA} = 5^\circ$ and inclination $i=38^\circ$" (3.7.1 Torques: Methodology)
   - assumption: thin gas disc on near-circular orbits; young stars isothermal plane with scale height ~1/12 radial scale length; old stars negligible  
  > "The young stellar component is modelled as an isothermal plane with a vertical scale height of approximately one-twelfth of the radial scale length." (3.7.1 Torques: Methodology)
   - fitting: _not stated_
   - validation: Compared with kinematic inflow rate; torque method noted as unvalidated by simulations  
  > "the torque method remains unvalidated by simulations" (3.7.2 Torques from the young stellar component)

## Software

- **CASA** v5.4.0-70: continuum subtraction and cube reconstruction  
  > "Using CASA v5.4.0-70, we continuum-subtracted and reconstructed the cube" (2.1 ALMA imaging)
- **KinMS / KinMS_fitter** : forward modelling of CO kinematics  
  > "specifically the `KinMS_fitter`" (3.5 Molecular gas kinematic modelling)
- **PyParadise** : spectral synthesis of MUSE spectra  
  > "we used the publicly available spectral synthesis modelling code `PyParadise`" (3.2 Spectral synthesis modelling)
- **Rainbow** : BPT mixing sequence, star-forming fraction  
  > "modelled the mixing sequence using `Rainbow`" (3.3 Star formation rates)
- **galight** : UV photometric decomposition  
  > "we employed the open-source software `galight`" (3.6.1 Photometric decomposition)
- **QDeblend3D** : AGN/host deblending of MUSE cubes  
  > "using `QDeblend`$^{\rm 3D}$ (cite: Husemann:2013)" (2.4 Deblending AGN and host emission)
- **pygalaxev** : stellar population models for F330W magnitudes  
  > "we employed `pygalaxev`[^5] to create composite stellar population models" (3.6.2 Mass of the young stellar component)
- **ESO Reflex / EsoRex** Reflex v2.11.0; MUSE pipeline v2.8.3: MUSE NFM reduction  
  > "we have used the MUSE pipeline v2.8.3 together with the graphical user interface `ESO Reflex` v2.11.0" (2.3 Optical 3D spectroscopy)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Molecular gas mass of spiral | 8.1 | 0.3 | log Msun | 1 | ${\rm log}\,M_{\rm mol}/{\rm M}_\odot=8.1\pm0.3$ |
| Black hole sphere of influence radius | 1.7 | +0.5/-0.2 | pc | 2 | we calculate a SOI radius of $R_{\rm SOI} = 1.7 ^{+0.5}_{-0.2}\,{\rm pc}$ |
| Stellar velocity dispersion at AGN | 105 | 12 | km/s | 2 | we derive a stellar velocity dispersion of $\sigma_\star = 105 \pm 12 \,{\rm km\,s^{-1}}$ |
| Total SFR | 4.9e-2 | 0.3e-2 | Msun/yr | 3 | ${\rm SFR}=(4.9 \pm 0.3) \times 10^{-2} \,{\rm M_\odot/yr}$ |
| Median molecular gas depletion time along spiral | 3.9 | 0.6 | Gyr | 4 | $\langle t^{\rm mol}_{\rm dep} \rangle =  3.9 \pm 0.6\,$ Gyr |
| Young stellar component stellar mass | 10^7.4 – 10^9.3 | range | Msun | 7 | the stellar mass of the young component is constrained to $10^{7.4} < M_\star/ {\rm M}_\odot < 10^{9.3}$ |
| Offset of young stellar component from AGN | 258 | 14 | pc | 6 | offset from the AGN by $258 \pm 14 \,{\rm pc}$ |
| Average torque-derived inflow rate | -4.2 | not stated | Msun/yr | 8 | average $-4.2 \, {\rm M}_\odot \,\mathrm{yr}^{-1}$ |
| BHAR | 0.10 | 0.03 | Msun/yr | 0 | translates to a BHAR of $0.10 \pm 0.03 \,{\rm M}_\odot/{\rm yr}$ |
| Gas supply lifetime for BHAR | 35 | not stated | Myr | 0 | the nuclear single-arm spiral hosts sufficient gas to maintain the BHAR for 35 Myr |

## Qualitative findings

- Prominent single-arm (m=1) CO spiral extends from 1.3 kpc to near the SOI, with 2.5 windings and consistently negative radial velocities  
  > "This single-arm spiral extends inward over 2.5 windings" (3.1 The single-arm spiral)

## Claim tuples

- H: Does star formation consume the gas flowing along the spiral? | E: Sigma_mol and Sigma_SFR along spiral | R: median t_dep 3.9 ± 0.6 Gyr; SFR below rKS expectation | F: star formation is inefficient so gas can reach the AGN | **supported**
- H: Can torques from a lopsided young stellar component drive the inflow? | E: UV decomposition and gravity torque computation compared with KinMS inflow | R: torque-derived inflow broadly consistent with kinematic inflow, but sensitive to configuration | F: young stars likely drive inflow, as snapshot | **partially**
- H: Is the inflow sufficient to sustain the SMBH accretion? | E: Compare BHAR with spiral gas reservoir and inflow | R: fuel for 35 Myr, ~9% SMBH growth | F: m=1 mode can sustain high BHAR | **supported**

## Reasoning

- Why this data: Combined ALMA cube covers molecular gas inside the bar at highest resolution near the AGN  
  > "We used this combined cube, since it covers the molecular gas structure embedded within the bar at the highest spatial resolution close to the AGN." (2.1 ALMA imaging)
- Why this method: _not stated_
- Alternative: AGN scattered light and [Ne V] emission as source of diffuse UV rejected in favour of young stars  
  > "We therefore favour a third scenario: the diffuse UV emission in NGC 4593’s centre originates from an unresolved young stellar population." (3.6.1 Photometric decomposition)
- How they decided it was enough: _not stated_
- Limitation (authors): Torque method unvalidated by simulations, configuration likely unstable  
  > "First, the configuration is likely unstable over time." (3.7.2 Torques from the young stellar component)
- Limitation (authors): Mass of young component is poorly constrained from single UV band; closed-box and alpha_CO assumptions  
  > "Thus, we were limited to a flux measurement in the F330W filter." (3.6.2 Mass of the young stellar component)
- Caveat (inferred, ours): Young stellar mass spans two dex, so torque amplitude is arbitrary (fixed at 10^8.5)
- Caveat (inferred, ours): Single-band UV decomposition with non-physical Sérsic model near AGN residuals
- Caveat (inferred, ours): alpha_CO choice scales gas mass and lifetime
- Caveat (inferred, ours): Radial velocity inflow could be due to non-circular orbits
- Caveat (inferred, ours): ~2% AGN-fuelled fraction is assumed

## Reproducibility

- Data public (paper): ALMA, HST and ESO archival data; codes public  
  > "We retrieved the data from the HST archive, processed through the standard calibration pipeline." (2.2 Hubble Space Telescope imaging)
- Products in archive: _not stated_
- Missing: tclean imaging details
- Missing: KinMS priors and fit setup
- Missing: apertures and masks for fluxes
- Missing: torque code details
- Data volume (inferred): Tens to ~100 GB (two ALMA MSs plus MUSE and HST)
- Score (inferred): 3/5, Data public and software named, but imaging, fitting priors and aperture details are missing; the torque and mass results depend on assumptions.
- Rediscovery candidate: no, Key results depend on unstated settings and multi-instrument data, and the mass and torque numbers rest on assumptions.

## Links

- Method: (cite: Garcia-Burillo:2005) (torque method)
- Method: (cite: Winkel:2022) (MUSE spectral synthesis and deblending)
- Method: (cite: Davis:2013) (KinMS)
- Companion: (cite: Kianfar:2024) (Earlier ALMA study of NGC 4593 spiral non-axisymmetric motions)
- Related: Hopkins & Quataert 2010 m=1 mode simulations

## Checks

```json
{
 "quotes": 78,
 "quotes_ok": 78,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 98,
  "stated": 60,
  "rate": 0.612
 },
 "evidence_ok": true
}
```
