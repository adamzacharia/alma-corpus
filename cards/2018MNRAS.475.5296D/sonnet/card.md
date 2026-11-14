# Rings and gaps in the disc around Elias 24 revealed by ALMA

`2018MNRAS.475.5296D` | Monthly Notices of the Royal Astronomical Society 2018 | first author: Dipierro, G. | arXiv: 1801.05812 | DOI: 10.1093/mnras/sty181

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: What are the gap and ring structures in the Elias 24 1.3 mm continuum, and can an embedded migrating, accreting planet in SPH gas/dust simulations reproduce them?  
  > "The main aim is to reproduce the gap and ring-like structures observed in Elias 24 and provide an estimate of the properties of the planet and the gas and dust disc." (Introduction)
- Target **Elias 24**: coordinates _not stated_; z/distance 139 ± 6 pc  
  > "located at a distance of $139\, \pm\, 6$ pc (cite: mamajek08a)" (Introduction); distance from Mamajek 2008 (rho-Ophiuchus distance)  
  > "located at a distance of $139\, \pm\, 6$ pc (cite: mamajek08a)" (Introduction)

## Data provenance

- ALMA projects: 2013.1.00498.S
- bands: Band 6 (1.3 mm)  
  > "ALMA Band 6 observations at a wavelength of 1.3 mm were obtained with 44 antennas" (2 Observations and Data Calibration)
- frequencies and spectral setup: two 1.875 GHz windows at 216.975 and 232.350 GHz plus 468.75 MHz windows including 12CO, 13CO, C18O J=2-1  
  > "two wide-bandwidth spectral windows with 1.875 GHz of bandwidth centered at 216.975 and 232.350 GHz" (2 Observations and Data Calibration)
- continuum bandwidth: 6.56 GHz aggregate, eight spectral windows  
  > "The correlator was configured to deliver 6.56 GHz of aggregate continuum bandwidth using eight spectral windows." (2 Observations and Data Calibration)
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15.1 m to 1.6 km, 44 antennas  
  > "with baselines between 15.1 m to 1.6 km and a total integration time of 12.5 min" (2 Observations and Data Calibration)
- angular resolution: 0.2'' x 0.17'' (P.A. 62 deg), 28 x 24 au  
  > "with angular resolution of $0.2'' \times 0.17''$ (P.A. = 62$^{\circ}$)" (2.1 Continuum emission)
- max recoverable scale: _not stated_
- sensitivity: rms 81.7 uJy/beam  
  > "resulting in a root mean square (rms) noise level of $81.7 \,\mathrm{\mu Jy \,beam^{-1}}$" (2 Observations and Data Calibration)
- time on source: 12.5 min total integration  
  > "with baselines between 15.1 m to 1.6 km and a total integration time of 12.5 min" (2 Observations and Data Calibration)
- observing dates: _not stated_
- pi or archival as stated: Program of P.I. L. Pérez  
  > "Elias 24 was observed with ALMA during program 2013.1.00498.S (P.I. L. Pérez)" (2 Observations and Data Calibration)
- External data: Disc dust model, stellar properties, dust mass 0.0017 Msun, rc=127 au, p=0.9, flaring index 1.03, geometry i=24, PA=50  
  > "where $M_{\mathrm{d}}=0.0017 M_{\odot}$ is the dust disc mass, $r_{\mathrm{c}}=127$ au is a characteristic scaling radius and $p=0.9$ is the gradient parameter." (3.2.1 Models for the disc surface density structure) [from (cite: andrews10a)]
- External data: Stellar properties: K5, 1 Msun, 4250 K  
  > "an effective fixed temperature of 4250 K (cite: wilking05a)" (3.1.2 Radiative transfer and synthetic ALMA observations) [from (cite: wilking05a)]
- External data: SMA 880 um flux used for spectral index  
  > "Comparing the measured total flux with $880\, \mu m$ SMA emission maps, we obtain a spectral index of $\sim 2.27\pm 0.01$" (2.1 Continuum emission) [from (cite: andrews07b; andrews10a)]
- Simulation/model as data: PHANTOM 3D SPH gas+1 mm dust disc with embedded migrating accreting planet (10^6 particles), post-processed with RADMC-3D  
  > "We perform a set of 3D SPH simulations of gas and dust disc with an embedded protoplanet using the PHANTOM code (cite: price17a)." (3.1.1 Dust/gas numerical simulations)

## Processing

### Calibration

- pipeline or manual: ALMA pipeline inside CASA  
  > "Standard calibration was carried out using the ALMA pipeline (<https://almascience.nrao.edu/processing/science-pipeline>) inside the Common Astronomy Software Application (CASA)" (2 Observations and Data Calibration)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (flux); J1517-2422 bandpass; J1627-2426 gain  
  > "J1517-2422 for bandpass calibration, Titan for absolute surface brightness calibration, and J1627-2426 for gain calibration" (2 Observations and Data Calibration)
- flux scale uncertainty: _not stated_
- self calibration: phase then amplitude; SNR ~350 to ~710  
  > "self calibration (first in phase, then in amplitude) was also carried out, improving the dynamic range of the image from an initial SNR value of $\sim$ 350 to an SNR of $\sim$ 710" (2 Observations and Data Calibration)

### Imaging

- task: CASA clean  
  > "Imaging of the interferometric observations was carried out with the CASA task *clean*" (2 Observations and Data Calibration)
- deconvolver: multiscale  
  > "multiscale deconvolution (cite: rau11a)" (2 Observations and Data Calibration)
- weighting robust: Briggs, robust = 0  
  > "using Briggs weighting of the visibilities with a robust parameter of 0" (2 Observations and Data Calibration)
- uv taper: _not stated_
- cell size: 0.02''  
  > "with a pixel size of $0.02''$" (2 Observations and Data Calibration)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: 0, 10, 30 pixels  
  > "we selected scales of 0 (point source), 10 and 30 pixels for deconvolution, with a pixel size of $0.02''$" (2 Observations and Data Calibration)
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.2'' x 0.17'', PA 62 deg  
  > "with angular resolution of $0.2'' \times 0.17''$ (P.A. = 62$^{\circ}$)" (2.1 Continuum emission)
- final rms: 81.7 uJy/beam  
  > "resulting in a root mean square (rms) noise level of $81.7 \,\mathrm{\mu Jy \,beam^{-1}}$" (2 Observations and Data Calibration)

### Inherited from earlier work

- Disc dust mass, vertical geometry, dust opacity model and stellar parameters  
  > "Our reference model for the total dust mass (see Sect. [3.2.1](#sect:refmodel)) and the disc vertical geometry are taken from (cite: andrews10a)" (3.2 Initial conditions) [from (cite: andrews10a)]
- Initial disc geometry (i=24, PA=50) used as starting ellipse  
  > "We start our analysis by considering an ellipse with geometry parameters found by (cite: andrews10a)" (2.1 Continuum emission) [from (cite: andrews10a)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and continuum spectral window selection for imaging
- Self-calibration solution intervals and number of iterations
- clean threshold, masks, image size
- Dust opacity table details beyond reference to Andrews et al. 2010
- SPH initial planet/disc parameter grid explored and selection of best snapshot (fit by eye)
- Number of azimuthal/vertical RADMC-3D grid cells and CASA simulator noise settings

## Analysis recipe

1. **Image continuum and measure flux**: CASA clean after self-calibration; total flux summed over emission above 2 rms  
  > "We measure the total flux by summing the disc emission with values of the surface brightness within two times the rms noise." (2.1 Continuum emission)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive disc geometry**: Elliptical apertures; minimise intensity dispersion  
  > "We therefore evaluate the best fitting ellipse by computing the elliptical aperture where the spread of the intensity values inside the apertures reaches the minimum value." (2.1 Continuum emission)
   - fitting: _not stated_
   - validation: Compared with Andrews et al. 2010 geometry  
  > "Both values are consistent with the geometry parameters found by (cite: andrews10a)." (2.1 Continuum emission)
3. **Radial profile and ring locations**: Azimuthal elliptical annulus photometry; fit sum of three Gaussians  
  > "we fix a combination of three Gaussian functions $f \left(\theta \right)=\sum_{i=1}^3 a_i \exp \left[-\left(\theta-\theta_i \right)^2/2 \sigma_i^2 \right]$, where we assume $\theta_1=0$." (2.1 Continuum emission)
   - parameter: annuli width a quarter of linear resolution  
  > "elliptical annuli with an extent of a quarter of the linear resolution of the observation" (2.1 Continuum emission)
   - assumption: distance 139 pc  
  > "assuming a source distance of $139$ pc" (2.1 Continuum emission)
   - fitting: Levenberg-Marquardt nonlinear least squares weighted by flux uncertainties  
  > "We carry out a nonlinear least-squares Levenberg-Marquardt minimization (cite: levenberg44a) taking into account the uncertainties on the flux measurements" (2.1 Continuum emission)
   - validation: _not stated_
4. **SPH gas/dust simulations with embedded planet**: PHANTOM one-fluid dust, 1 mm grains, sink-particle planet free to migrate and accrete; 10^6 particles; snapshot chosen by eye  
  > "In all our simulations we set the dust grain size to be $s_{\rm grain}=1\, {\rm mm}$" (3.1.1 Dust/gas numerical simulations)
   - software: PHANTOM
   - parameter: alpha_AV=0.1 (alpha_SS~0.003); dust-to-gas 0.1; H_in=0.075 au; r 1-180 au  
  > "We set the SPH $\alpha_{\rm AV}$ viscosity parameter to 0.1, resulting in an effective (cite: shakura73a) viscosity $\alpha_{\mathrm{SS}} \approx 0.003$" (3.2 Initial conditions)
   - assumption: vertically isothermal; initial dust-to-gas ratio 0.1 for mm grains  
  > "In our modelling, we therefore adopt a total initial dust-to-gas ratio for millimetre grains of 0.1." (3.2.2 Dust-to-gas mass ratio)
   - fitting: by eye, no statistical test  
  > "the fitting procedure is done by eye without performing any statistical test to quantify the goodness of the fit." (3 Modelling the continuum dust emission)
   - validation: Compare with Elias 24 radial profile  
  > "In Fig. [6](#fig:cfrphotom) we show the data vs model comparison in terms of the azimuthally averaged surface brightness at different angular separations from the disc center." (Comparison with ALMA observations)
5. **Radiative transfer and synthetic observations**: RADMC-3D dust temperature then ray tracing with 10^8 photons; Fourier transform, sample at ALMA uv, image like data with CASA simulator  
  > "We then calculated the predicted visibilities from our models by Fourier transforming the model images and sampling the visibility function on the same $\left(u,v\right)$ points as probed by our ALMA observations." (3.1.2 Radiative transfer and synthetic ALMA observations)
   - software: RADMC-3D, CASA
   - parameter: grain size 0.005 um-1 mm, m=3.5; star R=4.2 Rsun, T=4250 K  
  > "between $0.005\, \mathrm{\mu m}$ and $1$ mm, with $m=3.5$" (3.1.2 Radiative transfer and synthetic ALMA observations)
   - assumption: star only heating source; inclination/PA from observations  
  > "assuming that the star is the only source of luminosity" (3.1.2 Radiative transfer and synthetic ALMA observations)
   - fitting: _not stated_
   - validation: Residuals of model vs data in radial profile and visibility-based residual map  
  > "The residuals map was obtained by first deriving the residuals for the real and imaginary parts of the visibility function" (3.4 Comparison with ALMA observations)

## Software

- **CASA** 4.7.1 (simulator): Calibration, clean imaging, ALMA simulator, fixvis  
  > "together with the CASA ALMA simulator (version 4.7.1)" (3.1.2 Radiative transfer and synthetic ALMA observations)
- **PHANTOM** : 3D SPH gas/dust simulations  
  > "using the PHANTOM code (cite: price17a)" (3.1.1 Dust/gas numerical simulations)
- **RADMC-3D** : Monte Carlo radiative transfer  
  > "using the RADMC-3D Monte Carlo radiative transfer code (cite: dullemond12a)" (3.1.2 Radiative transfer and synthetic ALMA observations)
- **SPLASH** : visualisation of SPH output  
  > "We used SPLASH (cite: price07a)." (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total 1.3 mm flux | 368.1 | 0.9 | mJy | 1 | The measured total flux is $368.1 \pm0.9$ mJy |
| Spectral index 0.88-1.3 mm | 2.27 | 0.01 | dimensionless | 1 | we obtain a spectral index of $\sim 2.27\pm 0.01$ |
| Inclination | 28.5 | 3.8 | deg | 2 | $i=28.5^{\circ} \pm 3.8^{\circ}$ and $\mathrm{P.A.}=46.7^{\circ}\pm 6.5^{\circ}$ |
| Position angle | 46.7 | 6.5 | deg | 2 | $i=28.5^{\circ} \pm 3.8^{\circ}$ and $\mathrm{P.A.}=46.7^{\circ}\pm 6.5^{\circ}$ |
| Dark ring radii | 0.47 and 0.71 (65.3 and 98.7 au) | not stated | arcsec | 3 | the dark rings are located at $0.47''$ and $0.71''$ while the bright rings have a semi-major axis of $0.58''$ and $0.87''$ |
| Planet mass and location in best model | 0.7 MJ at 61.7 au | not stated | MJ, au | 4 | At this stage of the simulation, the planet is at 61.7 au from the central star and its mass is $0.7\, \mathrm{M_{\mathrm{J}}}$. |
| Mean residual in gap/outer edge (0.4-1'') | 5.1 | 0.4 | % of observed flux | 5 | the mean value of the absolute values of the residuals is $\left(5.1\pm 0.4\right)$% of the observed fluxes |
| Model total flux | 309.2 | 1.1 | mJy | 5 | The measured total flux of the disc from the simulated model map is $309.2 \pm1.1$ mJy |

## Qualitative findings

- Double-hump dust structure in outer disc arises from inward drift of large grains toward pressure maximum at gap outer edge  
  > "Our model suggests that the two inflection points in the radial intensity profile are due to the inward radial motion of large dust grains from the outer disc." (abstract)

## Claim tuples

- H: An embedded migrating, accreting low-mass planet can produce the observed gap and ring | E: PHANTOM SPH + RADMC-3D + CASA simulated observations compared with ALMA profile | R: ~5% average discrepancy around gap region | F: Planet of ~0.7 MJ at ~60 au is consistent with the data | **supported**
- H: Outer-disc inflection points have a dynamical origin | E: Dust drift in simulation | R: Model reproduces concavity change at ~0.8'' | F: Due to radial inward motion of large grains | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: CO snow line, dead zone as alternative gap origins; not ruled out  
  > "Further modelling of the evolution of dust particles in the presence of the CO snow line applied to the physical conditions of the Elias 24 disc is necessary" (4.5 The origin of the gap structure)
- How they decided it was enough: _not stated_
- Limitation (authors): Fit done by eye; degeneracy cannot be quantified  
  > "Given the large range of parameters involved in the fitting procedure, we cannot reasonably quantify this degeneracy" (3.3 Results)
- Caveat (inferred, ours): No quantitative fit or uncertainty on planet mass
- Caveat (inferred, ours): Single grain size and fixed dust-to-gas ratio assumed
- Caveat (inferred, ours): Central core poorly reproduced (~40% residual)

## Reproducibility

- Data public (paper): Project code given and acknowledged  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00498.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Simulation input files and parameter grid
- Missing: Self-calibration details
- Missing: Selected snapshot and RT setup details
- Data volume (inferred): ~10-20 GB raw
- Score (inferred): 4/5, Imaging and profile measurement reproducible from archival data; the hydrodynamic modelling is hard to reproduce exactly.
- Rediscovery candidate: yes, Public data, stated imaging recipe, numeric ring locations and fluxes.

## Links

- Method: (cite: price17a) (PHANTOM code)
- Method: (cite: andrews10a) (disc model and geometry)
- Companion: (cite: cieza17a) (independent ALMA 1.3 mm observations of Elias 24)
- Companion: (cite: cox17a) (independent ALMA 870 um observations)
- Related: Disks@EVLA

## Checks

```json
{
 "quotes": 63,
 "quotes_ok": 63,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 51,
  "rate": 0.662
 },
 "evidence_ok": true
}
```
