# The multiphase gas structure and kinematics in the circumnuclear region of NGC 5728

`2019MNRAS.490.5860S` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Shimizu, T. Taro | arXiv: 1907.03801 | DOI: 10.1093/mnras/stz2802

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: How do the multiphase gas (molecular, ionized) and stars in the circumnuclear region of NGC 5728 trace AGN feeding (inflow) and feedback (outflow)?  
  > "to investigate in detail the feeding and feedback of the AGN." (abstract)
- Target **NGC 5728**: coordinates RA = 14:42:23.872, DEC = 17:15:11.016 (VLBI, Megamaser Cosmology Project)  
  > "NGC 5728 is a nearby SAB(r)a galaxy ($D = 39$ Mpc, 1$''$ = 190 pc), with a Compton thick, Seyfert 2 nucleus" (1.1 NGC 5728); "The coordinates of the AGN are RA = 14:42:23.872 and DEC = 17:15:11.016 with an accuracy of a few tens mas." (2.5 Astrometric Alignment and AGN Position); z/distance D = 39 Mpc  
  > "NGC 5728 is a nearby SAB(r)a galaxy ($D = 39$ Mpc, 1$''$ = 190 pc), with a Compton thick, Seyfert 2 nucleus" (1.1 NGC 5728); "The coordinates of the AGN are RA = 14:42:23.872 and DEC = 17:15:11.016 with an accuracy of a few tens mas." (2.5 Astrometric Alignment and AGN Position); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00086.S
- bands: Band 6 (1.3 mm)  
  > "resulting in an angular resolution of 0.56$''$$\times$0.49$''$ (PA = -79.4$^\circ$) in Band 6." (2.3 ALMA Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C36-3  
  > "for a total on-source time of 29 minutes in the C36-3 configuration" (2.3 ALMA Observations)
- baselines: _not stated_
- angular resolution: 0.56'' x 0.49'' (PA = -79.4 deg)  
  > "resulting in an angular resolution of 0.56$''$$\times$0.49$''$ (PA = -79.4$^\circ$) in Band 6." (2.3 ALMA Observations)
- max recoverable scale: 5.34''  
  > "given the largest angular scale of the ALMA observation was 5.34$''$" (3.2.2 Molecular Gas Mass)
- sensitivity: _not stated_
- time on source: 29 minutes  
  > "for a total on-source time of 29 minutes in the C36-3 configuration" (2.3 ALMA Observations)
- observing dates: May 15, 2016  
  > "ALMA observed NGC 5728 on May 15, 2016" (2.3 ALMA Observations)
- pi or archival as stated: PI N. Nagar program (project 2015.1.00086.S)  
  > "as part of project 2015.1.00086.S (PI N. Nagar)" (2.3 ALMA Observations)
- Line: CO J=2-1 (230.538 GHz)
- Other facility **VLT/SINFONI (LLAMA)**: H+K IFU cube, 0.15'' PSF; H2, [FeII], [SiVI], Brgamma  
  > "With AO, we achieved a point spread function (PSF) full width at half maximum (FWHM) of 0.15$''$" (2.1 SINFONI Observations)
- Other facility **VLT/MUSE**: Archival optical IFU cube, 0.62'' PSF  
  > "Gaussian fitting of a foreground star within the FOV show a PSF FWHM of 0.62$''$." (2.2 MUSE Observations)
- Other facility **HST/WFC3**: Archival F336W, F438W, F814W, F160W imaging  
  > "HST observed NGC 5728 in the F336W, F438W, F814W and F160W bands with the *Wide Field Camera 3* instrument as part of program 13755 (PI J. Greene)." (2.4 HST Observations)
- Other facility **VLT/X-Shooter**: IFU spectrum for trans-auroral electron density  
  > "as part of the LLAMA program, we obtained X-Shooter IFU spectra for all of the targets." (6 Electron Densities)
- External data: alpha_CO = 1.1 and R12 = 1.4 for CO conversion  
  > "In this work we use $R_{12} = 1.4$, the value found for nearby star forming galaxies (cite: Sandstrom:2013en)." (3.2.2 Molecular Gas Mass) [from (cite: Sandstrom:2013en)]
- External data: VLBI AGN position  
  > "we used VLBI observations from The Megamaser Cosmology Project (C. Y. Kuo 2018, private communication)" (2.5 Astrometric Alignment and AGN Position) [from C. Y. Kuo 2018, private communication]
- External data: Swift/BAT 14-195 keV luminosity converted to L_Bol  
  > "$L_{X} = 2.15\times10^{43}$ ergs s$^{-1}$ (cite: Ricci:2017aa), into $L_{\rm Bol}$ using the relation from (cite: Winter:2012yq)" (1.1 NGC 5728) [from (cite: Ricci:2017aa); (cite: Winter:2012yq)]
- External data: Global SFR of 2.1 Msun/yr  
  > "(cite: Shimizu:2017aa) estimated a global SFR of 2.1 M$_{\ensuremath{\odot}}$ yr$^{-1}$." (3.6 AGN Feedback in NGC 5728) [from (cite: Shimizu:2017aa)]
- External data: Literature outflow rates for 15 AGN and BN19 sample for comparison  
  > "We found data for 15 AGN: NGC 1068, NGC 2992, NGC 3783, NGC 6814, NGC 7469 (cite: Muller-Sanchez:2011aa)" (3.5 Outflow Energetics) [from (cite: Fiore:2017aa); (cite: Baron:2019aa) and others]
- Simulation/model as data: MILES v11.0 SSP models (Padova 2000, Chabrier IMF) for stellar fitting; CLOUDY grid from Rose et al. 2018 for trans-auroral densities  
  > "latest (v11.0) single stellar population (SSP) models based on the extended MILES stellar library (cite: Vazdekis:2016aa)" (2.6.1 Continuum Fitting and Subtraction)

## Processing

### Calibration

- pipeline or manual: CASA used to process the data; details not given  
  > "We used the Common Astronomy Software Applications package (cite: McMullin:2007aa) to process the data." (2.3 ALMA Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: TCLEAN  
  > "Within the TCLEAN routine, we applied Briggs weighting with *robust* = 0.5" (2.3 ALMA Observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "we applied Briggs weighting with *robust* = 0.5" (2.3 ALMA Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: already included in ALMA cube reduction; 1.3 mm continuum from remaining three spws without CO  
  > "The data reduction for the ALMA cube includes already a continuum subtraction" (2.6.1 Continuum Fitting and Subtraction)
- line free channels: _not stated_
- primary beam correction: applied to all cubes  
  > "All resulting data cubes were primary beam corrected" (2.3 ALMA Observations)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: clean threshold 2.5 mJy, channels 2.54 km/s  
  > "at 2.54 km s$^{-1}$ velocity resolution and a peak residual (parameter *threshold*) of 2.5 mJy" (2.3 ALMA Observations)

### Inherited from earlier work

- ALMA program/data from the 7-AGN CO(2-1) survey; disk fit results consistent with that paper  
  > "This observation was part of an ALMA program to map CO (2–1) in the nuclear regions of 7 local AGN (cite: Ramakrishnan:2019aa)." (2.3 ALMA Observations) [from (cite: Ramakrishnan:2019aa)]
- Multi-component line fitting via MultiNest  
  > "we used the method described in (cite: Fischer:2017aa) that employs the Bayesian MultiNest algorithm" (3.3 The Inner Warped Disk) [from (cite: Fischer:2017aa)]
- Bicone flux profile F(r)=A exp(-tau r/r_end)  
  > "As in (cite: Bae:2016aa), we assume the flux is exponentially decreasing with radius" (3.4.3 Outflow Modeling) [from (cite: Bae:2016aa)]
- Brgamma-to-ionized-gas-mass formula  
  > "using the formula given in (cite: Storchi-Bergmann:2009aa)" (3.5 Outflow Energetics) [from (cite: Storchi-Bergmann:2009aa)]
- CO luminosity relation  
  > "The CO luminosity is calculated following (cite: Solomon:2005df)" (3.2.2 Molecular Gas Mass) [from (cite: Solomon:2005df)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and continuum-subtraction method for the ALMA cube
- Number of iterations, mask and image size/cell size for tclean
- CASA version and calibration (flux calibrator, pipeline) details
- Initial guesses, priors and bounds for DYSMALPY fits
- MultiNest settings and evidence threshold for adding components
- Masking/velocity-error thresholds used for the residual velocity field and mass-rate aperture sizes
- Which CO(2-1) flux extraction and signal threshold for maps

## Analysis recipe

1. **Image ALMA CO(2-1) cube**: CASA tclean with Briggs weighting, primary-beam correction, 2.54 km/s channels  
  > "we applied Briggs weighting with *robust* = 0.5 to reproduce the data cube at 2.54 km s$^{-1}$ velocity resolution" (2.3 ALMA Observations)
   - software: CASA
   - parameter: robust = 0.5; threshold 2.5 mJy  
  > "a peak residual (parameter *threshold*) of 2.5 mJy" (2.3 ALMA Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit single-Gaussian emission lines per spaxel**: Single Gaussians to CO(2-1) and optical/NIR lines; errors from 100 Monte Carlo perturbed spectra using line-free RMS  
  > "we produced 100 simulated spectra for every emission line by randomly perturbing the original spectra assuming a Gaussian distribution with a standard deviation equal to the RMS" (2.6.2 Emission Line Fitting)
   - software: PPXF
   - fitting: Single Gaussian least squares; doublet ratios fixed to 3  
  > "fixed the intensity ratio to the expected theoretical value of 3 for the \[OIII\] and \[NII\] doublets" (2.6.2 Emission Line Fitting)
   - validation: _not stated_
3. **Derive molecular gas mass**: Integrate CO(2-1) within 6.5'' aperture over +/-375 km/s, convert to L'CO and mass  
  > "we simply integrated the spectrum between rest-frame velocities of $\pm375$ km s$^{-1}$ to obtain a total CO (2–1) intensity ($S_{\rm C O}$) of 93.6 Jy km s$^{-1}$" (3.2.2 Molecular Gas Mass)
   - assumption: R12 = 1.4; alpha_CO = 1.1 Msun pc^-2/(K km/s)  
  > "we use $\alpha_{\scriptscriptstyle \rm CO} = 1.1$ M$_{\ensuremath{\odot}}$ pc$^{-2}$/(K km s$^{-2}$)" (3.2.2 Molecular Gas Mass)
   - fitting: _not stated_
   - validation: Compared with JCMT-based mass of Rosario et al. 2018; convolution test to JCMT beam  
  > "We tested whether convolving the ALMA cube to the JCMT beam and integrating over a larger aperture increased the measured molecular mass but did not find any change" (3.2.2 Molecular Gas Mass)
4. **Model disk rotation of CO and stars**: DYSMALPY thin exponential disk fit to CO velocity field (inner 2.5'' masked) and stellar velocity field, convolved with PSF and LSF  
  > "For the CO (2–1) model we fixed the centre by eye because we also masked out the inner 2.5$''$" (3.2.3 Disk Modelling)
   - software: DYSMALPY, emcee
   - parameter: free: Mdyn, r_eff, inclination, PA; 100 walkers, 100 burn-in, 400 sampling steps  
  > "We ran MCMC with 100 walkers for 100 burn-in steps and 400 sampling steps" (3.2.3 Disk Modelling)
   - assumption: thin exponential disk  
  > "We assumed a thin exponential disk mass distribution parameterised by the total dynamical mass" (3.2.3 Disk Modelling)
   - fitting: emcee MCMC; median and 16th/84th percentiles  
  > "to determine the best fit parameters and uncertainties from the sampled posterior distribution using the median and the 16th and 84th percentiles" (3.2.3 Disk Modelling)
   - validation: Consistent with Ramakrishnan et al. 2019 using same data  
  > "These results are also consistent with those found using the same data in (cite: Ramakrishnan:2019aa)." (3.2.3 Disk Modelling)
5. **Estimate molecular inflow/outflow from residuals**: Circular apertures spaced 0.56'' along disk minor axis on residual velocity field; mass via L'CO; rate = M v/delta r  
  > "The mass rate through each aperture is then $Mv/\delta r$ where $\delta r$ is the diameter of the apertures." (3.2.4 Molecular gas outflow and inflow?)
   - assumption: near side is west of kinematic major axis  
  > "We know based on the large scale dust maps and H$\alpha$ and \[OIII\] flux maps as well as the excitation of the ionized gas that the near-side is West of the kinematic major axis." (3.2.4 Molecular gas outflow and inflow?)
   - fitting: _not stated_
   - validation: _not stated_
6. **Decompose nuclear CO kinematic components**: MultiNest Bayesian fit of 1-3 Gaussians per spaxel in central 4''x4'', components assigned to five velocity groups from integrated 2'' spectrum  
  > "in this work we allow for a maximum of three components based on visual inspection of the ALMA cube" (3.3 The Inner Warped Disk)
   - software: MultiNest
   - fitting: MultiNest evidence comparison between N components  
  > "by comparing the evidence from a single component fit to a double component fit, we can determine whether the second component is statistically necessary" (3.3 The Inner Warped Disk)
   - validation: _not stated_
7. **Model ionized outflow and energetics**: DYSMALPY biconical outflow fit to [SiVI] velocity map; Brgamma-based ionized mass with ne = 1550 cm^-3; Mdot, Edot, pdot in annuli  
  > "As with modelling the rotating disk, we determined the best fit parameters using MCMC with 800 walkers, 100 burn steps, and 100 sampling steps." (3.4.3 Outflow Modeling)
   - software: DYSMALPY, emcee
   - parameter: tau fixed to 5; annular width 0.075''  
  > "we fixed $\tau$ to be 5 which is the value found for many nearby AGN" (3.4.3 Outflow Modeling)
   - assumption: Case B recombination; constant ne within SINFONI FOV  
  > "we assume a constant electron density within the SINFONI FOV" (3.5 Outflow Energetics)
   - fitting: MCMC; median and standard deviation of posteriors  
  > "based on the median and standard deviations of the resulting posterior distributions" (3.4.3 Outflow Modeling)
   - validation: Compared with Fiore et al. 2017 scaling relations and literature compilation  
  > "NGC 5728 lies very close to the correlations and the low values of $\dot{M}_{\rm{out}}$ and $\dot{E}_{\rm{out}}$ seem to be simply due to the relatively modest AGN luminosity." (3.5 Outflow Energetics)

## Software

- **CASA** : ALMA data processing and tclean imaging  
  > "We used the Common Astronomy Software Applications package (cite: McMullin:2007aa) to process the data." (2.3 ALMA Observations)
- **DYSMALPY** : disk and outflow kinematic modelling  
  > "an updated Python version of DYSMAL (cite: Davies:2011aa), now called DYSMALPY" (3.2.3 Disk Modelling)
- **emcee** : MCMC sampling  
  > "a Monte Carlo Markov Chain (MCMC) algorithm with EMCEE (cite: Foreman-Mackey:2013lr)" (3.2.3 Disk Modelling)
- **MultiNest** : multi-component line profile fitting  
  > "employs the Bayesian MultiNest algorithm (cite: Feroz:2009aa; Buchner:2014aa)" (3.3 The Inner Warped Disk)
- **PPXF** : stellar continuum and kinematics fitting of MUSE/SINFONI  
  > "we use the *Penalized Pixel-Fitting*[^3] (PPXF) routine" (2.6.1 Continuum Fitting and Subtraction)
- **VORONOI_2D_BINNING** : Voronoi binning of MUSE cube to S/N 20  
  > "bin the MUSE cube such that each bin contains a minimum S/N in the continuum of 20" (2.6.1 Continuum Fitting and Subtraction)
- **PyNeb** : [SII] doublet density  
  > "Using the PYNEB[^7] software package and assuming an electron temperature of 10$^{4}$ K" (6 Electron Densities)
- **CLOUDY** : photoionization grid for trans-auroral ratios (from Rose et al. 2018)  
  > "were produced using the CLOUDY photoionization code under the assumptions of solar metallicity gas" (6 Electron Densities)
- **Astropy** : general analysis  
  > "This research made use of Astropy,[^6] a community-developed core Python package for Astronomy" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total CO(2-1) intensity within 6.5'' aperture | 93.6 | not stated | Jy km/s | 3 | to obtain a total CO (2–1) intensity ($S_{\rm C O}$) of 93.6 Jy km s$^{-1}$ |
| Molecular gas mass within central ~1 kpc | 1.3e8 | not stated | Msun | 3 | we find a total molecular gas mass within the central $\sim$1 kpc of NGC 5728 to be 1.3$\times10^{8}$ M$_{\ensuremath{\odot}}$ |
| CO disk log Mdyn | 10.372 | +0.002/-0.001 | log Msun | 4 | we find a best fitting $\log M_{\rm dyn} = 10.372^{+0.002}_{-0.001}$ M$_{\ensuremath{\odot}}$ |
| CO disk r_eff | 537 | +2/-2 | pc | 4 | $r_{\rm eff} = 537^{+2}_{-2}$ pc |
| CO disk inclination | 43.3 | +0.1/-0.1 | deg | 4 | $i_{\rm disk} = 43.3\ensuremath{^\circ}^{+0.1}_{-0.1}$ |
| CO disk PA | 14.01 | +0.04/-0.03 | deg | 4 | P.A.$_{\rm disk} = 14.01\ensuremath{^\circ}^{+0.04}_{-0.03}$ |
| Molecular outflow velocity and rate within 1 kpc (residuals) | ~80 km/s; ~0.5 Msun/yr | not stated | km/s; Msun/yr | 5 | the residuals suggest an outflow velocity of $\sim$80 km s$^{-1}$ and mass outflow rate of $\sim0.5$ $M_{\ensuremath{\odot}}$ yr$^{-1}$ within 1 kpc |
| Nuclear molecular gas masses Comp1, Comp2, Comp3 within 2'' | 1.6e7, 1.6e7, 7.7e6 | not stated | Msun | 6 | $1.6\times10^{7}$, $1.6\times10^{7}$, and $7.7\times10^{6}$ M$_{\ensuremath{\odot}}$ respectively |
| Outflow bicone i, PA, v_max, r_end | i=49, PA=43, vmax=737, r_end=540 | 2 deg, 2 deg, 25 km/s, 20 pc | deg, deg, km/s, pc | 7 | $i_{\rm bicone} = 49\pm2\ensuremath{^\circ}$, P.A.$_{\rm bicone} = 43\pm2\ensuremath{^\circ}$, $r_{\rm end} = 540\pm20$ pc, and $v_{\rm max} = 737\pm25$ km s$^{-1}$ |
| Peak ionized mass outflow rate | 0.08 | not stated | Msun/yr | 7 | peak values of 0.08 M$_{\ensuremath{\odot}}$ yr$^{-1}$, $4\times10^{39}$ erg s$^{-1}$, and $2\times10^{32}$ Dyne |
| Electron density (trans-auroral) log ne | 3.19 | 0.12 | log cm^-3 | 0 | we estimate a flux-weighted $\log n_{\rm e}=3.19\pm0.12$ (1550 cm$^{-3}$) |

## Qualitative findings

- CO(2-1) holes along the NLR bicone coexist with strong ionized gas; interpreted as either lack of molecular gas or CO suppression by X-rays  
  > "A plausible explanation for these holes is instead that CO (2–1) is not accurately tracing the presence molecular gas in the NLR." (3.7 Missing molecular gas?)

## Claim tuples

- H: Is the circumnuclear ring a rotating star-forming disk? | E: DYSMALPY disk fits to CO and stellar velocity fields | R: CO i=43.3 deg, stars i=42.1 deg; residuals <40 km/s in stars | F: The ring is a rotating disk with young stars born from the molecular gas | **supported**
- H: Is there molecular gas structure inside the ring that feeds the AGN? | E: MultiNest multi-component fits to CO(2-1) in the central 4'' | R: Three kinematic components (~40%, 40%, 20% of nuclear gas) | F: Ring-like rotation, a warped inner disk, and gas along the nuclear bar | **supported**
- H: Is the AGN driving a strong ionized outflow that disrupts the circumnuclear region? | E: Bicone modelling of [SiVI] and Brgamma-based energetics | R: Peak Mdot 0.08 Msun/yr, 0.003% of L_Bol, momentum ratio 0.043 | F: Weak, momentum-driven outflow, consistent with Fiore scaling relations; not disrupting the region | **supported**
- H: Do CO holes mean the AGN removed molecular gas? | E: Compare CO holes with ionized and H2 emission | R: Holes are filled with ionized gas | F: Holes may reflect CO suppression/missing gas rather than clear evacuation; unresolved without higher-J CO | **partially**

## Reasoning

- Why this data: Multiwavelength IFU and ALMA data probe stars, ionized and molecular gas at matched spatial scales  
  > "it is now possible to study simultaneously the distribution and kinematics of both ionized and molecular gas at the same spatial scales in an efficient manner" (1 Introduction)
- Why this method: _not stated_
- Alternative: Spike in excitation diagram explained by A_M/I or by ionization parameter; they chose the simpler increase in U  
  > "we choose the simpler increase in $U$ model as our explanation" (3.2.1 Gas Excitation)
- How they decided it was enough: _not stated_
- Limitation (authors): ALMA lacks short spacings; diffuse flux resolved out, so mass is a lower limit  
  > "an indication that diffuse flux was resolved out due to the lack of short spacings during the ALMA observation" (3.2.2 Molecular Gas Mass)
- Limitation (authors): Disk model errors are statistical only  
  > "the very small errors on the model parameters only incorporate the statistical uncertainties" (3.2.3 Disk Modelling)
- Caveat (inferred, ours): Single ALMA pointing with limited resolution (0.5'') and no short spacings; CO-to-H2 factor assumed
- Caveat (inferred, ours): Molecular inflow/outflow from velocity residuals is sensitive to the disk model and non-circular orbits
- Caveat (inferred, ours): Ionized outflow mass depends on assumed constant ne (1550 cm^-3) and projection corrections
- Caveat (inferred, ours): Five-to-three component grouping of CO components is subjective

## Reproducibility

- Data public (paper): Archival ALMA, MUSE-DEEP (ESO Phase 3), and HST (MAST) data downloaded; SINFONI from program 093.B-0057  
  > "We downloaded archival MUSE data of NGC 5728 from the MUSE-DEEP collection, an ESO Phase 3 data release" (2.2 MUSE Observations)
- Products in archive: _not stated_
- Code: _not stated_
- Missing: Reduced SINFONI and X-Shooter cubes (LLAMA) not clearly public
- Missing: Fischer et al. MultiNest decomposition code and DYSMALPY priors/initial settings
- Missing: Exact CASA calibration and imaging parameters
- Data volume (inferred): ~10-50 GB for ALMA raw data; MUSE and HST cubes several GB
- Score (inferred): 5/5, ALMA imaging and disk fitting are fairly specified, but multi-instrument data, unreleased code and missing parameters limit full reproduction.
- Rediscovery candidate: no, Key results depend on non-ALMA datasets and unreleased fitting tools, and many settings are unstated.

## Links

- Method: (cite: Fischer:2017aa) (multi-component MultiNest line fitting method)
- Method: (cite: Davies:2011aa) (DYSMAL basis of DYSMALPY)
- Method: (cite: Baron:2019aa) (ionization parameter and density method)
- Companion: (cite: Ramakrishnan:2019aa) (Analysis of same ALMA CO(2-1) data for 7 local AGN)
- Companion: (cite: Durre:2018aa) (Prior MUSE/SINFONI study of NGC 5728 with differing outflow rates)
- Related: LLAMA
- Related: MUSE-DEEP
- Related: Megamaser Cosmology Project

## Checks

```json
{
 "quotes": 87,
 "quotes_ok": 87,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 100,
  "stated": 67,
  "rate": 0.67
 },
 "evidence_ok": true
}
```
