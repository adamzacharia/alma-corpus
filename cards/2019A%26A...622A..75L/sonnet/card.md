# Ring structure in the MWC 480 disk revealed by ALMA

`2019A&A...622A..75L` | Astronomy and Astrophysics 2019 | first author: Liu, Yao | arXiv: 1811.04074 | DOI: 10.1051/0004-6361/201834157

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: What is the dust ring/gap structure of the MWC 480 disk at 1.3 mm, and can a planet–disk interaction explain it (planet mass)?  
  > "subsequently model the disk with hydrodynamic simulations to infer the mass of a possible planet within the disk." (Introduction)
- Target **MWC 480 (HD 31648)**: coordinates _not stated_; z/distance 161.8 pc  
  > "MWC 480 is a Herbig Ae star located at a Gaia DR2 distance[^1] of $161.8_{-2}^{+2}\,\rm{pc}$" (Introduction); distance from Gaia DR2  
  > "MWC 480 is a Herbig Ae star located at a Gaia DR2 distance[^1] of $161.8_{-2}^{+2}\,\rm{pc}$" (Introduction)

## Data provenance

- ALMA projects: 2016.1.01164.S
- bands: Band 6 (230 GHz)  
  > "We observed MWC 480 with ALMA in Band 6 (230 GHz)" (2 Observation, data reduction and analysis)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 21 to 3638 m, 47 12 m antennas  
  > "The observation was conducted using 47 12 m antennas with baselines ranging from 21 to 3638 m." (2 Observation, data reduction and analysis)
- angular resolution: 0.17" x 0.11" (27.5 x 17.8 au)  
  > "The resulting beam size is $0.17^{\prime\prime}\times0.11^{\prime\prime}$, corresponding to a physical scale of $27.5 \times 17.8$ au" (2 Observation, data reduction and analysis)
- max recoverable scale: _not stated_
- sensitivity: ~0.07 mJy/beam rms  
  > "The rms noise level of the image is ${\sim}\,0.07\,\rm{mJy/beam}$." (2 Observation, data reduction and analysis)
- time on source: 4 minutes, PWV 0.5 mm  
  > "The on-source time was 4 minutes and the precipitable water vapor (PWV) was 0.5 mm during the integration." (2 Observation, data reduction and analysis)
- observing dates: August 27, 2017  
  > "as part of the Cycle 4 program (ID: 2016.1.01164.S; PI: G. Herczeg) on August 27, 2017" (2 Observation, data reduction and analysis)
- pi or archival as stated: Cycle 4 program, PI G. Herczeg  
  > "Cycle 4 program (ID: 2016.1.01164.S; PI: G. Herczeg)" (2 Observation, data reduction and analysis)
- Other facility **Archival/multi-wavelength SED photometry**: Optical-to-millimeter SED used in radiative transfer fit  
  > "we incorporate a variety of archival data and multi-wavelength photometry" (3.3 Fit to the SED and brightness distribution)
- Other facility **Gaia DR2**: Distance 161.8 pc  
  > "located at a Gaia DR2 distance[^1] of $161.8_{-2}^{+2}\,\rm{pc}$" (Introduction)
- External data: Total 1.3 mm flux density 268 ± 0.3 mJy from visibility modeling  
  > "Modeling the visibility data yields a similar PA value and a total flux density at 1.3 mm of $268\,{\pm}\,0.3\,\rm{mJy}$ (cite: long2018)." (2 Observation, data reduction and analysis) [from (cite: long2018)]
- External data: Dust optical constants: silicate and carbon  
  > "we take the data from (cite: dorschner1995) for silicate and from (cite: jager1998) for carbon at a pyrolysis temperature of $800\,^{\rm o}\rm{C}$" (3 Radiative transfer modeling) [from (cite: dorschner1995); (cite: jager1998)]
- Simulation/model as data: 3D SPH gas+dust PHANTOM simulations of a disk with embedded migrating planet compared to RT-derived dust surface density  
  > "We perform a set of 3D Smoothed Particle Hydrodynamics (SPH) simulations of gas and dust disk with an embedded protoplanet using the PHANTOM code (cite: price17a)." (4 Modeling the dust gap)

## Processing

### Calibration

- pipeline or manual: ALMA-provided data reduction scripts  
  > "Following the data reduction scripts provided by ALMA, the atmospheric phase noise was first reduced using water vapor radiometer measurements." (2 Observation, data reduction and analysis)
- casa version: CASA 5.1.1  
  > "version 5.1.1" (2 Observation, data reduction and analysis)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0510+1800  
  > "J0510+1800 served as the flux calibrator" (2 Observation, data reduction and analysis)
- flux scale uncertainty: ~10%  
  > "we estimated an absolute flux calibration uncertainty of ${\sim}\,10$%" (2 Observation, data reduction and analysis)
- self calibration: Performed to improve S/N (details not given)  
  > "Self-calibration was performed to improve the signal-to-noise ratio." (2 Observation, data reduction and analysis)

### Imaging

- task: CASA tclean  
  > "The continuum image was finally created from the calibrated visibilities using the `CASA` `tclean` task" (2 Observation, data reduction and analysis)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "Briggs weighting with a robust parameter of 0.5" (2 Observation, data reduction and analysis)
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
- final beam: 0.17" x 0.11", PA ~23 deg  
  > "asymmetric beam ($\rm{PA}\,{\sim}\,23^{\circ}$)" (2 Observation, data reduction and analysis)
- final rms: ~0.07 mJy/beam  
  > "The rms noise level of the image is ${\sim}\,0.07\,\rm{mJy/beam}$." (2 Observation, data reduction and analysis)

### Inherited from earlier work

- Iterative procedure to build large-grain surface density from the brightness profile  
  > "following an iterative procedure introduced by (cite: pinte2016)" (3.2 The distribution of large grains) [from (cite: pinte2016)]
- Simulated annealing implementation details  
  > "Details about the implementation of simulated annealing can be found in (cite: madlener2012) and (cite: liu2017)." (3.3 Fit to the SED and brightness distribution) [from (cite: madlener2012); (cite: liu2017)]
- Gap width scaling with Hill radius, x = 4-8  
  > "the width $\Delta$ of dust gaps opened by planets is a few times the Hill radius $\Delta \approx x R_{\rm Hill}$ where $x=4\textrm{--}8$ (cite: rosotti2016)" (4.2 Analytical estimate of the planet properties) [from (cite: rosotti2016)]

### Not stated but needed to reproduce (our reading)

- Self-calibration solints, number of rounds and reference antenna
- tclean cell size, image size, mask, niter and threshold
- Phase center/coordinates of MWC 480
- Pipeline vs manual flagging details
- SED photometry table used in the fit
- Simulated annealing settings (priors ranges, cooling schedule, merit function)
- Stellar spectrum/photosphere model inputs for RADMC-3D beyond Table 1, number of photon packages
- PHANTOM setup files, sink parameters, resolution of dust
- Procedure to deproject radial profile and extract brightness along the major axis

## Analysis recipe

1. **Image continuum and measure gap/ring**: tclean image; Gaussian fit to radial brightness along the major axis  
  > "Fitting a Gaussian profile to the brightness distribution along the major axis in the vicinity of the gap using the `mpfit` routine within `IDL`" (2 Observation, data reduction and analysis)
   - software: CASA, IDL mpfit
   - parameter: PA = 148 deg from imfit; robust 0.5  
  > "assuming a position angle (PA) of $148^{\circ}$ obtained from the `CASA` `imfit` task" (2 Observation, data reduction and analysis)
   - fitting: _not stated_
   - validation: _not stated_
2. **Build large-grain surface density iteratively**: RADMC-3D synthetic images convolved with beam; surface density corrected at each radius by observed/model brightness ratio  
  > "the large grain population surface density at each radius is corrected by the ratio of the observed and the modeled brightness profile." (3.2 The distribution of large grains)
   - software: RADMC-3D
   - parameter: Initial H100=10 au, beta=1.1, Mdust=2e-3 Msun, Lambda=0.2, fLGP=0.85, i=36 deg; R_out,LGP=200 au  
  > "we initially fix $H_{100}\,{=}\,10\,\rm{au}$ and $\beta\,{=}\,1.1$" (3.2 The distribution of large grains)
   - assumption: 75% silicate + 25% carbon, Mie opacities, a^-3.5 size distribution, amin 0.01 um, amax 3 mm (LGP), 2 um (SGP); gas-to-dust 100 initially  
  > "The dust in the model is a mixture of 75% amorphous silicate and 25% carbon." (3 Radiative transfer modeling)
   - fitting: Iterations until change <5%  
  > "The iteration procedure converged after 30 iterations, when the change in model brightness profile was less than 5% at all radii." (3.2 The distribution of large grains)
   - validation: Visibility-plane comparison of the best-fit model  
  > "However, we confirm the quality of the fit in the UV space." (3 Radiative transfer modeling)
3. **Joint SED and image fit**: Simulated annealing over {Mdust,tot, H100, beta, Lambda, fLGP, i}  
  > "we explore the parameter space {$M_{\rm dust,tot}$, $H_{100}$, $\beta$, $\Lambda$, $f_{\rm LGP}$, $i$} using the simulated annealing algorithm (cite: kirkpatrick1983)" (3.3 Fit to the SED and brightness distribution)
   - software: RADMC-3D
   - assumption: Passively heated disk; fixed Rin=0.15 au, gamma=1, M*=2.0 Msun  
  > "The disk is considered to be passively heated by stellar irradiation." (3 Radiative transfer modeling)
   - fitting: Simulated annealing (Metropolis-Hastings-based MCMC random walk)  
  > "Based on the Metropolis-Hastings algorithm, simulated annealing creates a Markov Chain Monte Carlo random walk through the parameter space" (3.3 Fit to the SED and brightness distribution)
   - validation: Best-fit model compared with ALMA image, SED and visibilities  
  > "The best-fit model well reproduces the ALMA image and the SED." (3.3 Fit to the SED and brightness distribution)
4. **Estimate planet mass analytically**: Gap width ~ x R_Hill, with Rp=73.4 au, Delta=23 au, plus gap-opening criteria  
  > "assuming $R_{\rm p}=73.4 \,{\rm au}$ and $\Delta=23 \,{\rm au}$." (4.2 Analytical estimate of the planet properties)
   - parameter: Mp range 0.4-3 MJ; simulated 0.4-2 MJ  
  > "our numerical simulations adopt planet masses spanning $M_{\rm p}=[0.4,2] \, \rm{M_{J}}$." (4.2 Analytical estimate of the planet properties)
   - fitting: _not stated_
   - validation: _not stated_
5. **SPH gas/dust simulations to match dust profile**: PHANTOM 3D SPH one-fluid dust, varying dust-to-gas ratio, planet mass and initial radius; 5e5 particles  
  > "modeled as a set of $5\,{\times}\,10^{5}$ SPH gas/dust particles" (4.1 Initial conditions)
   - software: PHANTOM
   - parameter: Dust/gas 0.01-0.2; Rp = 85-120 au; alpha_AV ~0.15 (alpha_SS ~5e-3)  
  > "We set the SPH $\alpha_{\rm AV}$ viscosity parameter to $\sim$0.15, resulting in an effective (cite: shakura73a) viscosity $\alpha_{\rm{SS}} \approx 5 \times 10^{-3}$." (4.1 Initial conditions)
   - assumption: Locally isothermal; uniform dust properties; temperature and opacity effects negligible  
  > "we assume that these two contributions have a negligible effect on the disk emission with respect to the effects of dust density." (4 Modeling the dust gap)
   - fitting: Fit by eye, no statistical test  
  > "the fitting procedure is done by eye without performing any statistical test to quantify the goodness of the fit." (4 Modeling the dust gap)
   - validation: Compared azimuthally averaged dust surface density with RT-derived profile; dust settling check H_d/H_g ~0.28 vs Lambda 0.25  
  > "This value is quite close to the value of $\Lambda\,{=}\,0.25$" (4.2 Dust-to-gas mass ratio)

## Software

- **CASA** 5.1.1: Calibration, tclean imaging, imfit  
  > "The data were calibrated using the Common Astronomy Software Applications (CASA, (cite: mcmullin07a)) package, version 5.1.1." (2 Observation, data reduction and analysis)
- **IDL mpfit** : Gaussian fit to gap and ring profiles  
  > "using the `mpfit` routine within `IDL`" (2 Observation, data reduction and analysis)
- **RADMC-3D** : Radiative transfer modeling of SED and image  
  > "using the radiative transfer code `RADMC-3D`[^2] (cite: radmc3d2012)" (3 Radiative transfer modeling)
- **PHANTOM** : 3D SPH gas+dust planet-disk simulations  
  > "using the PHANTOM code (cite: price17a)" (4 Modeling the dust gap)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Gap location | 74.3 | not stated | au | 1 | yields a gap location of $74.3\,\rm{au}$ ($0.46^{\prime\prime}$) |
| Gap FWHM | 23 | ±3 | au | 1 | a full-width half-maximum (FWHM) of $23\pm3\,\rm{au}$ |
| Bright ring center | 97.5 | not stated | au | 1 | The same procedure yields a center for the bright ring of $97.5\,\rm{au}$ ($0.6^{\prime\prime}$). |
| Disk radial extent (3 sigma) | ~175 | not stated | au | 1 | The radial extent of the disk is ${\sim}\,175$ au |
| Total dust mass | 1.6 | +0.5/-0.4 | 1e-3 Msun | 3 | $M_{\rm dust,tot}\, [10^{-3}\,M_{\odot}]$ / $1.6^{+0.5}_{-0.4}$ |
| Flaring index beta | 1.08 | ±0.02 | dimensionless | 3 | $\beta$ / $1.08^{+0.02}_{-0.02}$ |
| Scale height H100 | 12 | +2.1/-0.7 | au | 3 | $H_{100}\,[\rm{au}]$ / $12^{+2.1}_{-0.7}$ |
| Settling parameter Lambda | 0.25 | ±0.04 | dimensionless | 3 | $\Lambda$ / $0.25^{+0.04}_{-0.04}$ |
| Large-grain mass fraction | 0.95 | +0.04/-0.08 | dimensionless | 3 | $f_{\rm LGP}$ / $0.95^{+0.04}_{-0.08}$ |
| Inclination | 37 | +0.3/-0.8 | deg | 3 | $i\,[^{\circ}]$ / $37^{+0.3}_{-0.8}$ |
| Ring dust mass | 2e-4 (~67 Earth masses) | not stated | Msun | 3 | The ring has a dust mass of $2\times10^{-4}\,M_{\odot}$ (${\sim}\,67\,M_{\oplus}$) |
| Best-model planet mass after 50 orbits | ~2.3 (initial 1.25 at 85 au) | not stated | MJ | 5 | the planet reaches the distance of 78.4 au from the central star and its mass is ${\sim}\,2.3\,\mathrm{M_{\mathrm{J}}}$ |
| Analytic planet mass estimate | 0.4-3 | not stated | MJ | 4 | \sim 0.4 \textrm{--}3\, {\rm M_J} |
| Missing dust mass in gap | ~5 | not stated | MJ | 5 | The difference between these two integrated masses is ${\sim}5\,\rm{M_{J}}$ |

## Qualitative findings

- SED shows no gap signature because 1.3 mm traces mm grains and the gap is at large radius  
  > "Second, the gap is too far from the central star to have a significant impact on the IR SED." (5.1 Why the SED does not show evidence of the gap)

## Claim tuples

- H: Does MWC 480 host a gap and ring at 1.3 mm? | E: High-resolution Band 6 continuum imaging and Gaussian fits | R: Gap at 74.3 au, FWHM 23 au, ring at 97.5 au | F: A gap and ring are identified for the first time | **supported**
- H: Can a planet–disk interaction explain the gap? | E: PHANTOM SPH simulations compared by eye to RT-derived dust profile | R: Planet of ~2.3 MJ at ~78 au reproduces the dust profile with dust/gas 0.1 | F: Data consistent with an embedded planet; disk had enough material | **partially**
- H: Why does the SED not reveal the gap? | E: Compare SED of central blob with full model | R: Central blob shapes SED up to ~50 um | F: Gap too far out and mm-only | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Modeling done in image plane because most of the disk is optically thin at 1.3 mm  
  > "our modeling of the ALMA data is carried out in the image plane." (3 Radiative transfer modeling)
- Alternative: Condensation fronts (CO snow line) and dead zones considered as alternatives; not ruled out  
  > "The center of the ring marked with the vertical dotted line appears associated with the CO snow line." (5.2 On the origin of the gap/ring structure)
- How they decided it was enough: _not stated_
- Limitation (authors): Degeneracy among simulation parameters cannot be quantified; fit by eye  
  > "we cannot reasonably quantify this degeneracy" (4 Modeling the dust gap)
- Limitation (authors): Planet not confirmed; high-contrast searches needed  
  > "deep high-contrast searches for planets in the gap are required to confirm the presence of a planet" (5.2 On the origin of the gap/ring structure)
- Caveat (inferred, ours): Planet mass relies on by-eye fits with no uncertainty or uniqueness test
- Caveat (inferred, ours): Dust-to-gas ratio of 0.1 is assumed from a simple argument
- Caveat (inferred, ours): Short 4-min observation; assumed temperature structure from passive heating

## Reproducibility

- Data public (paper): Data cited by ALMA project code in acknowledgments; public status not explicit  
  > "This paper makes use of the following ALMA data: 2016.1.01164.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Self-calibration and tclean parameters
- Missing: SED photometry and annealing configuration
- Missing: PHANTOM input setups
- Data volume (inferred): ~10-50 GB raw for one short Band 6 execution
- Score (inferred): 3/5, ALMA project code and imaging basics given, but self-cal, SED and simulation inputs are underspecified.
- Rediscovery candidate: no, Imaging measurements are reproducible but modeling results depend on unstated settings and expensive simulations.

## Links

- Method: (cite: pinte2016) (Iterative surface-density construction procedure)
- Method: (cite: liu2017) (Radiative transfer model setup and simulated annealing)
- Companion: (cite: long2018) (Total flux density from visibility modeling in the same ALMA survey of Taurus disks)
- Related: ALMA survey of 32 disks in Taurus (PI G. Herczeg)

## Checks

```json
{
 "quotes": 74,
 "quotes_ok": 74,
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
  "facts": 81,
  "stated": 55,
  "rate": 0.679
 },
 "evidence_ok": true
}
```
