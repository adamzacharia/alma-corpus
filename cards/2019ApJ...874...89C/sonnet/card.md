# The Central 1000 au of a Pre-stellar Core Revealed with ALMA. I. 1.3 mm Continuum Observations

`2019ApJ...874...89C` | The Astrophysical Journal 2019 | first author: Caselli, Paola | arXiv: 1902.05299 | DOI: 10.3847/1538-4357/ab0700

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: What is the structure of the central ~1000 au of the pre-stellar core L1544 in 1.3 mm dust continuum, and is there real fragmentation or are substructures interferometric artefacts?  
  > "The region within $R_{\rm ker}$ appears to have fragmented, but detailed analysis shows that similar substructure can be reproduced by synthetic interferometric observations" (abstract)
- Target **L1544**: coordinates _not stated_; z/distance 135 pc  
  > "the 8 M$_{\odot}$ pre-stellar core L1544 in Taurus at a distance of 135 pc (cite: SGF14)" (Introduction); distance from Schlafly et al. 2014 (cite: SGF14)  
  > "the 8 M$_{\odot}$ pre-stellar core L1544 in Taurus at a distance of 135 pc (cite: SGF14)" (Introduction)

## Data provenance

- ALMA projects: 2013.1.01195.S
- bands: Band 6 (1.3 mm)  
  > "We present ALMA Band 6 observations (ACA and 12m array)" (abstract)
- frequencies and spectral setup: continuum spw centred at 228.973 GHz, 2 GHz bandwidth; other 3 spws for N2D+, DCO+, D13CO+  
  > "1 of the 4 correlator spectral windows was used for continuum centred at 228.973 GHz and a 2 GHz bandwidth" (Observations)
- continuum bandwidth: _not stated_
- arrays: 12-m (Main) array and 7-m (ACA)  
  > "Both the 12-m (Main array) and the 7-m (ACA) arrays were employed." (Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 2.05"x1.61" (277 au x 217 au), PA 59.5 deg  
  > "which results in a beam with major and minor axes of 2.05$^{\prime\prime}\times1.61^{\prime\prime}$ (277 au $\times$ 217 au at the distance of Taurus)" (Observations)
- max recoverable scale: _not stated_
- sensitivity: 36 uJy/beam rms  
  > "found to be 36 $\mu$Jy beam$^{-1}$" (Observations)
- time on source: _not stated_
- observing dates: 12-m: 2014 Dec 27 and 29; 7-m: 2014 June 15, July 20, 29, Aug 6, 11  
  > "The 12-m array observations were carried out on 2014 Dec 27 and 29" (Observations)
- pi or archival as stated: Cycle 2, PI Caselli  
  > "ESO Project ID 2013.1.01195.S, PI Caselli" (Observations)
- Other facility **LMT AzTEC and GBT MUSTANG-2**: single-dish 1.1 mm and 3.3 mm dust continuum used for density profile (from Chacon-Tanarro et al. 2019)  
  > "with the AzTEC camera at the Large Millimeter Telescope (LMT), and at 3.3 mm, with the MUSTANG-2 camera at the Green Bank Telescope (GBT)" (4.3 Structure derived from single dish observations)
- External data: L1544 density profile n0=1.6e6 cm-3, Rflat=17.3", alpha=2.6  
  > "$n_0$ = 1.6$\times$10$^6$ cm$^{-3}$, $R_{\rm flat}$ = 17.3$^{\prime\prime}$ ($\equiv$2336 au), and $\alpha$ = 2.6" (4.3 Structure derived from single dish observations) [from Chacon-Tanarro et al. 2019 (cite: CPC19)]
- External data: Bonnor-Ebert sphere model of L1544 with temperature gradient  
  > "The model is generated using the physical parameters found by (cite: KC10) and refined by (cite: KRC14)" (4.1 The centrally concentrated Bonnor-Ebert sphere) [from Keto & Caselli 2010 (cite: KC10); Keto et al. 2014 (cite: KRC14)]
- External data: dust temperature 6.5 K  
  > "Assuming a dust temperature $T_d$ = 6.5 K (cite: CCW07; KC10)" (3 Results) [from Crapsi et al. 2007 (cite: CCW07); Keto & Caselli 2010]
- External data: dust opacity 0.009 cm2/g at 1.3 mm  
  > "a dust opacity at 1.3 mm $\kappa_{\rm 1.3mm}$ = 0.009 cm$^2$ g$^{-1}$ (cite: OH94)" (3 Results) [from Ossenkopf & Henning 1994 (cite: OH94)]
- Simulation/model as data: 3D non-ideal MHD and HD simulations of an 8.1 Msun core with ZeusTW, radiative transfer with RADMC-3D, used for simulated ALMA observations  
  > "we carry out 3D non-ideal magneto-hydrodynamic (MHD) turbulent simulations using ZeusTW code (cite: Krasnopolsky+2010) to model the evolution of the pre-stellar core L1544" (5 Hydro- and Magneto-hydro simulations)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: 12-m data CASA 4.2.2; 7-m data CASA 4.2.1  
  > "version 4.2.2, while the 7-m array data were calibrated using CASA version 4.2.1" (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: 12-m: Uranus; 7-m: J0510+1800, Ganymede, Uranus  
  > "while flux calibration was done using Uranus" (2 Observations)
- flux scale uncertainty: 5% calibration error  
  > "(42$\pm$2 mJy, taking into account a 5% calibration error)" (3 Results)
- self calibration: _not stated_

### Imaging

- task: joint deconvolution of ACA and 12-m in CASA 4.4.0, mfs; statwt for relative weights  
  > "We perform a joint de-convolution of both datasets (ACA and 12-m array) in CASA (version 4.4.0) using multifrequency synthesis (*mfs*)" (2 Observations)
- deconvolver: multi-scale clean  
  > "we use the multi-scale clean technique" (2 Observations)
- weighting robust: robust 0.5  
  > "a robust weighting of 0.5, and a taper of 1.5$^{\prime\prime}$" (2 Observations)
- uv taper: 1.5"  
  > "a robust weighting of 0.5, and a taper of 1.5$^{\prime\prime}$" (2 Observations)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: [0, 2, 6, 18] arcsec  
  > "with the multi-scale parameter of \[0, 2, 6, 18\] arcsec" (2 Observations)
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: maps shown without PB correction; flux measured PB-corrected within 50% response  
  > "all without primary-beam correction to maintain a roughly constant noise across the image" (3 Results)
- array combination: joint deconvolution of ACA+12m visibilities  
  > "Before combining the data from both arrays we calculated the relative weights using the *statwt()* command." (2 Observations)
- smoothing: _not stated_
- final beam: 2.05"x1.61", PA 59.5 deg  
  > "a beam with major and minor axes of 2.05$^{\prime\prime}\times1.61^{\prime\prime}$" (2 Observations)
- final rms: 36 uJy/beam  
  > "found to be 36 $\mu$Jy beam$^{-1}$" (2 Observations)

### Inherited from earlier work

- Temperature structure and Bonnor-Ebert model parameters taken from earlier work  
  > "with a temperature gradient which reproduces the one observed by (cite: CCW07)" (4.1 The centrally concentrated Bonnor-Ebert sphere) [from Crapsi et al. 2007 (cite: CCW07); KC10; KRC14]
- Chemical network for ambipolar diffusion diffusivity  
  > "We adopt the same chemical network as in (cite: ZCL16) for obtaining the magnetic diffusivity of ambipolar diffusion (AD)." (5 Hydro- and Magneto-hydro simulations) [from Zhao et al. 2016 (cite: ZCL16)]
- Line data (N2D+, DCO+, D13CO+) deferred to Paper II  
  > "These data will be presented in a follow-up paper dedicated to the kinematics (Paper II)." (2 Observations) [from Paper II]

### Not stated but needed to reproduce (our reading)

- Image size and cell size
- Clean threshold, masks and iteration count
- Whether continuum channels were selected/line-free; no continuum subtraction details
- Pointing/phase centre coordinates
- Simulation inputs: simobserve integration times, precipitable water vapour, thermal noise settings
- How the 5-sigma contour area was converted to a radius (elliptical vs circular)
- Details of the MHD/HD simulation resolution and RADMC-3D dust/opacity setup
- Which of the 7-m and 12-m executions were used and their flux scale values

## Analysis recipe

1. **Calibrate and jointly image ACA+12m continuum**: Calibrate in CASA, reweight with statwt, joint multi-scale mfs clean  
  > "We perform a joint de-convolution of both datasets (ACA and 12-m array) in CASA (version 4.4.0) using multifrequency synthesis (*mfs*)" (2 Observations)
   - software: CASA
   - parameter: robust 0.5, taper 1.5", scales [0,2,6,18]"  
  > "a robust weighting of 0.5, and a taper of 1.5$^{\prime\prime}$" (2 Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive kernel radius, mass and density**: Kernel radius from 5 sigma contour; mass from optically thin dust emission formula; mean H2 density from sphere  
  > "The kernel radius ($R_{\rm ker}$), derived from the area within the 5 $\sigma$ contour of the combined map is 10.3$''$  (1446 au)." (3 Results)
   - parameter: flux integrated within 5 sigma contour and 50% primary beam response: 42±2 mJy  
  > "integrated within the 5 $\sigma$ contour and within the 50% primary beam response in the right panel of Figure [1](#fig:maps_array) (42$\pm$2 mJy" (3 Results)
   - assumption: Td = 6.5 K, kappa1.3mm = 0.009 cm2/g, D = 135 pc  
  > "Assuming a dust temperature $T_d$ = 6.5 K (cite: CCW07; KC10) and a dust opacity at 1.3 mm $\kappa_{\rm 1.3mm}$ = 0.009 cm$^2$ g$^{-1}$ (cite: OH94)" (3 Results)
   - fitting: _not stated_
   - validation: Mass error ~50% when distance and opacity uncertainties included  
  > "uncertainties on the source distance and on the dust opacity effectively increase this error to about 50 $\%$ of the measured value." (Footnote 1)
3. **Characterise fragments and Jeans stability**: Mass within 11 sigma contour in 12m map; Jeans length for isothermal cloud  
  > "the mass enclosed within the fragments (the 11 $\sigma$ contour in the central panel of Fig. [1](#fig:maps_array)) is 0.003 M$_{\odot}$ (3 M$_{\rm J}$)" (3 Results)
   - assumption: T = 6.5 K, uniform spherical kernel density 4.5e-18 g/cm3  
  > "Assuming a temperature of 6.5 K and the mass density of the kernel of 4.5$\times$10$^{-18}$ g cm$^{-3}$" (3 Results)
   - fitting: _not stated_
   - validation: _not stated_
4. **Simulated observations of Bonnor-Ebert model**: simobserve of model image for ACA and 12m, imaged with same parameters  
  > "The high-resolution continuum image is then processed using the task *simobserve* in CASA 4.6.0" (4.1 The centrally concentrated Bonnor-Ebert sphere)
   - software: CASA simobserve
   - fitting: _not stated_
   - validation: Compared peak flux with observed  
  > "with a peak flux about two times larger than that observed" (4.1 The centrally concentrated Bonnor-Ebert sphere)
5. **Fit smooth elongated model and test substructure**: Fit F(r)=F0/(1+(r/Rflat)^alpha) with elliptical radius by chi2 minimisation over 50% PB region; simulate observations, residuals; 100 simulations with different hour angles using baselines >13 klambda, natural weighting  
  > "The best-fit model is calculated by minimising the $\chi^2$ of the flux difference between the model (after applying the primary beam correction) and the combined ACA+Main Array data" (4.2 The smooth elongated structure derived from ALMA observations)
   - software: CASA simobserve
   - parameter: 100 models, Cycle 1 configuration 2, baselines >13 klambda  
  > "We run 100 models with different starting hour-angles to generate different $uv$-coverage." (4.2.1)
   - fitting: chi2 minimisation; peak flux fixed  
  > "The peak value is fixed and the minimisation is carried out over the region with primary beam response higher than 50%." (4.2 The smooth elongated structure derived from ALMA observations)
   - validation: Residuals show no significant fragments; simulated images reproduce similar substructure  
  > "small substructures similar to those identified in the ALMA data of L1544 can be produced when a radial emission profile with a flat central section is used as input image" (4.2.1)
6. **Simulated observations of single-dish-derived model**: Simulated ALMA observations of spherical profile from Chacon-Tanarro et al.  
  > "Figure [6](#fig:Chacon) shows the ALMA simulated observations of the pre-stellar core with the spherically-symmetric physical structure derived by (cite: CPC19)." (4.3)
   - software: CASA simobserve
   - fitting: _not stated_
   - validation: Compared fluxes with ACA+12m and 12m-only images  
  > "including the flux in the ACA + 12m and 12m-only images" (4.3)
7. **MHD/HD simulations and synthetic ALMA observations**: ZeusTW non-ideal MHD and HD turbulent simulations; RADMC-3D temperature; simulated ALMA 12m observations at peak densities 2e6, 5e6, 1e7 cm-3  
  > "We first apply radiative transfer to the simulation models using RADMC-3D (cite: DJP12)." (5.1 Simulated ALMA observations)
   - software: ZeusTW, RADMC-3D, CASA simobserve
   - parameter: Mc=8.1 Msun, Rc=5e4 au, B0≈14.8 uG, Mach 5 turbulence, tilt 45 deg  
  > "total mass $M_{\rm c}=8.1~M_{\ensuremath{\odot}}$ (cite: TMM98) and radius $R_c=5\times 10^{4}$ au" (5 Hydro- and Magneto-hydro simulations)
   - fitting: _not stated_
   - validation: Compared simulated peak fluxes with observed  
  > "the 10$^7$ cm$^{-3}$ MHD core has a peak flux about 1.5 times lower than the observed core" (5.1)

## Software

- **CASA** 4.2.2 / 4.2.1 (calibration), 4.4.0 (imaging), 4.6.0 (simobserve): calibration, imaging and simulated observations  
  > "The 12-m array data were calibrated using the Common Astronomy Software Applications package (cite: MWS07) version 4.2.2" (2 Observations)
- **ZeusTW** : 3D non-ideal MHD simulations  
  > "using ZeusTW code (cite: Krasnopolsky+2010)" (5 Hydro- and Magneto-hydro simulations)
- **RADMC-3D** : radiative transfer for dust temperature and continuum images  
  > "We first apply radiative transfer to the simulation models using RADMC-3D (cite: DJP12)." (5.1 Simulated ALMA observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Kernel radius | 10.3 (1446 au) | not stated | arcsec (au) | 2 | derived from the area within the 5 $\sigma$ contour of the combined map is 10.3$''$  (1446 au) |
| Kernel flux | 42 | 2 | mJy | 2 | (42$\pm$2 mJy, taking into account a 5% calibration error) |
| Kernel mass | 0.100 | 0.005 (about 50% with distance and opacity) | Msun | 2 | we find $M_{\rm ker}$ = 0.100$\pm$0.005 M$_{\odot}$ |
| Average H2 number density in kernel | 1.00e6 | 0.05e6 | cm-3 | 2 | (1.00$\pm$0.05)$\times$10$^{6}$ cm$^{-3}$ |
| Fragment total mass (11 sigma contour) | 0.003 | not stated | Msun | 3 | is 0.003 M$_{\odot}$ (3 M$_{\rm J}$), i.e. each fragment is about 1 M$_{\rm J}$ |
| Jeans length of kernel | 3200 | not stated | au | 3 | the Jeans length of the kernel is about 3200 au |
| Best-fit smooth model Rflat | 10.84 (1463 au) | not stated | arcsec (au) | 5 | $R_{\rm flat}$=10.84$^{\prime\prime}$ (equivalent to 1463 au), $\alpha$=2.32, $AR$=1.83 |
| Best-fit smooth model alpha | 2.32 | not stated | dimensionless | 5 | $\alpha$=2.32, $AR$=1.83, position angle PA=166$^{\circ}$ |
| Best-fit model F0 | 0.772 | not stated | mJy/beam | 5 | $F_0$=0.772 mJy beam$^{-1}$ |
| Kernel original orientation angle phi | ≈45 | not stated | deg | 7 | which yields $\phi\approx45^{\circ}$ for the kernel of L1544 |

## Qualitative findings

- Dense cores with peak densities below ~5e6 cm-3 are completely filtered out in simulated 12m observations  
  > "are completely filtered out by the Main Array because of their smooth structure" (5.1)

## Claim tuples

- H: Is the substructure in the kernel real fragmentation? | E: Simulated ALMA observations of smooth models, including baselines >13 klambda | R: Smooth models with a flat central zone reproduce similar substructure; residuals show no significant fragments | F: Substructure may be interferometric artefacts; no claim of fragmentation | **supported**
- H: Does the best Bonnor-Ebert model of L1544 reproduce the ALMA map? | E: Simulated observations of KC10/KRC14 model | R: Model is more centrally concentrated with peak flux ~2x higher | F: L1544 has a larger flat radius, i.e. is earlier or evolves differently | **supported**
- H: Which cores can be detected by interferometers? | E: Simulated 12m observations of MHD and HD cores at different peak densities | R: Only cores with peak density 1e7 cm-3 detected | F: Only dynamically evolved cores are detectable, explaining earlier non-detections | **supported**
- H: Can continuum distinguish MHD from HD? | E: Compared simulated peak fluxes to observed | R: MHD peak 1.5x lower, HD 1.5x higher than observed | F: Not possible to distinguish; MHD reproduces kernel-core misalignment | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Simulated observations used to test whether fragments are artefacts  
  > "the fragments may also be imaging artefacts due to extended emission viewed with an interferometer" (3 Results)
- Alternative: Bonnor-Ebert sphere model rejected as too centrally concentrated  
  > "shows a core that is clearly more centrally concentrated than deduced by the observations" (4.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Mass uncertainty ~50% due to distance and opacity  
  > "effectively increase this error to about 50 $\%$ of the measured value" (Footnote 1)
- Limitation (authors): Smooth model underestimates peak flux because extended structure is filtered  
  > "the peak flux of the simulated combined image was underestimated because the model was constructed from the ALMA data" (4.3)
- Caveat (inferred, ours): Fixed single dust temperature and opacity for mass
- Caveat (inferred, ours): Parametric model fit to filtered data, peak fixed
- Caveat (inferred, ours): No statistical test of fragment significance beyond 2-3 sigma
- Caveat (inferred, ours): Only one simulation setup per density; sensitivity to simobserve noise settings unclear

## Reproducibility

- Data public (paper): Project code given (ALMA Cycle 2)  
  > "ESO Project ID 2013.1.01195.S, PI Caselli" (2 Observations)
- Products in archive: _not stated_
- Missing: Cell/image size, clean threshold, masks
- Missing: simobserve noise and integration settings
- Missing: Simulation snapshots and MHD setup details
- Missing: Model input maps
- Data volume (inferred): ~50-150 GB raw (12m + ACA, several executions)
- Score (inferred): 6/5, Data public and imaging parameters mostly given with numeric results, but several imaging and simulation settings are missing.
- Rediscovery candidate: yes, Public data, stated imaging recipe, numeric kernel mass/radius/density results.

## Links

- Method: McMullin et al. 2007 (cite: MWS07) (CASA)
- Companion: Chacon-Tanarro et al. 2019 (cite: CPC19) (single-dish density profile)
- Companion: Paper II (Pineda et al., in prep.) (kinematics from molecular lines)

## Checks

```json
{
 "quotes": 75,
 "quotes_ok": 75,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 86,
  "stated": 59,
  "rate": 0.686
 },
 "evidence_ok": true
}
```
