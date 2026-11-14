# Disk Wind Feedback from High-mass Protostars. III. Synthetic CO Line Emission

`2024ApJ...966..117X` | The Astrophysical Journal 2024 | first author: Xu, Duo | arXiv: 2309.03868 | DOI: 10.3847/1538-4357/ad3211

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type theory_or_simulation_compared_to_alma

## Science

- Fields: star_formation
- Question: How well can outflow mass, momentum, energy and outflow rates be recovered from CO line emission of simulated disk-wind outflows from massive protostars, and how do synthetic spectra compare with ALMA-observed outflows?  
  > "We compare the mass, momentum and kinetic energy estimates obtained from molecular lines to the true values, finding that the mass and momentum estimates can have uncertainties of up to a factor of four." (abstract)
- Target **G35.20-0.74N (G35.20)**: coordinates _not stated_; z/distance 2.2 kpc  
  > "The distances to G35.20, G45.47, and G339.88 are 2.2 kpc, 8.4 kpc, and 2.1 kpc, respectively." (4.1 Overview of CO Morphologies of G35.30, G45.47 and G338.88); distance from _not stated_
- Target **G45.47+0.05 (G45.47)**: coordinates _not stated_; z/distance 8.4 kpc  
  > "The distances to G35.20, G45.47, and G339.88 are 2.2 kpc, 8.4 kpc, and 2.1 kpc, respectively." (4.1 Overview of CO Morphologies of G35.30, G45.47 and G338.88); distance from _not stated_
- Target **G339.88-1.26 (G339.88)**: coordinates _not stated_; z/distance 2.1 kpc  
  > "The distances to G35.20, G45.47, and G339.88 are 2.2 kpc, 8.4 kpc, and 2.1 kpc, respectively." (4.1 Overview of CO Morphologies of G35.30, G45.47 and G338.88); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.01454.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12-m array, C36-3 configuration  
  > "The presented $^{12}$CO (2-1) data were obtained with ALMA in the C36-3 configurations" (4.1 Overview of CO Morphologies of G35.30, G45.47 and G338.88)
- configurations: _not stated_
- baselines: 15 m to 463 m  
  > "with baselines ranging from 15 m to 463 m" (4.1 Overview of CO Morphologies of G35.30, G45.47 and G338.88)
- angular resolution: Synthesized beams 0.87x0.83, 0.90x0.84, 0.93x0.74 arcsec; images use 0.25 arcsec Gaussian beams  
  > "The major axis sizes of the synthesized beams for G35.20, G45.47, and G339.88 are 0.87$''$, 0.90$''$, and 0.93$''$, respectively." (4.1 Overview of CO Morphologies of G35.30, G45.47 and G338.88)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 3.5 min per source  
  > "The integration time for each source was 3.5 min." (4.1 Overview of CO Morphologies of G35.30, G45.47 and G338.88)
- observing dates: 2016 Sep 8 (G35.20), Apr 24 (G45.47), Apr 4 (G339.88)  
  > "on September 8 (G35.20), April 24 (G45.47), and April 4 (G339.88) of 2016" (4.1 Overview of CO Morphologies of G35.30, G45.47 and G338.88)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (not stated)
- External data: Protostellar mass, L_bol, inclination from SED fitting for the three sources  
  > "The protostellar mass $m_{*}$ and bolometric luminosity $L_{\rm bol}$ are determined from SED fitting as reported in (cite: 2023ApJ...942....7F)." (4.3 Estimating the Mass Outflow Rate and Momentum Outflow Rate in Observations) [from (cite: 2023ApJ...942....7F)]
- External data: Protostellar evolutionary tracks (radius, luminosity) used as radiative transfer input  
  > "adopted from (cite: 2014ApJ...788..166Z)" (Table 1) [from (cite: 2014ApJ...788..166Z)]
- External data: Observed outflow dynamical timescale around 12 kyr  
  > "the calculated observed outflow dynamical timescale is around 12 kyr (cite: 2019ApJ...873...73Z)" (4.3 Estimating the Mass Outflow Rate and Momentum Outflow Rate in Observations) [from (cite: 2019ApJ...873...73Z)]
- Simulation/model as data: 3D ideal MHD ZEUS-MP disk wind simulations of a 60 Msun core, Sigma_cl=1 g cm^-2, protostar mass 1 to >24 Msun  
  > "We analyze the 3D ideal MHD simulations by (cite: 2023ApJ...947...40S), which utilized the ZEUS-MP (cite: 2000RMxAC...9...66N) code" (2.1 Magnetohydrodynamics Simulations)

## Processing

### Calibration

- pipeline or manual: CASA pipeline calibration, then self-calibration using continuum applied to CO line data  
  > "After pipeline calibration, self-calibration using the continuum data was performed and applied to the CO line data." (4.1 Overview of CO Morphologies of G35.30, G45.47 and G338.88)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA tclean  
  > "The CASA *tclean* task was used to image the data" (4.1 Overview of CO Morphologies of G35.30, G45.47 and G338.88)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "using Briggs weighting with the robust parameter set to 0.5" (4.1 Overview of CO Morphologies of G35.30, G45.47 and G338.88)
- uv taper: _not stated_
- cell size: 0.1 arcsec (synthetic images)  
  > "We retain the resolution of $0.1^{\prime\prime}$ as the cell size for the tclean image." (3.2 Synthetic ALMA Observations)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: Gaussian 0.25 arcsec  
  > "the synthetic beams of the $^{12}$CO images are Gaussian with a size of 0.$''$ 25" (4.1 Overview of CO Morphologies of G35.30, G45.47 and G338.88)
- final rms: _not stated_

### Inherited from earlier work

- MHD simulation setup  
  > "Further details on the setup of MHD simulations are described by (cite: 2023ApJ...947...40S)." (2.1 Magnetohydrodynamics Simulations) [from (cite: 2023ApJ...947...40S)]
- Observational details of the ALMA data  
  > "We refer the reader to these papers for more details of the observations." (4.1 Overview of CO Morphologies of G35.30, G45.47 and G338.88) [from (cite: 2022ApJ...936...68Z; 2019ApJ...873...73Z; 2019ApJ...886L...4Z)]
- Outflow rate estimation approach  
  > "we adopt a similar observational approach as in (cite: 2019ApJ...873...73Z)" (3.4 Estimating the Mass Outflow Rate and Momentum Outflow Rate) [from (cite: 2019ApJ...873...73Z)]
- Inclination grid of 20 cos(i) values  
  > "This choice is the same as that used in the continuum radiative transfer model grid of (cite: 2018ApJ...853...18Z)." (3.1 Synthetic CO Maps) [from (cite: 2018ApJ...853...18Z)]

### Not stated but needed to reproduce (our reading)

- Rest frequencies, channel widths and spectral setup of the observed data
- simalma parameters beyond 12m config, 210 s, PWV 0.5 mm, 2 kpc
- Noise levels (rms) of observed cubes
- Line-free channels and continuum subtraction for CO
- Exact velocity-integration masks and central velocity for observed sources
- Excitation-temperature grid and chi-squared noise treatment details
- Access to the MHD simulation snapshots and radmc-3d inputs
- Which MHD snapshots correspond to each protostellar mass

## Analysis recipe

1. **Dust temperature**: radmc-3d dust radiative transfer on MHD grid, gas temperature set equal to dust temperature  
  > "We use radmc-3d (cite: 2012ascl.soft02015D) to calculate the dust temperature structures of the simulations." (2.2.1 Continuum Radiative Transfer and Dust Temperature)
   - software: radmc-3d
   - parameter: 10^8 photon packages, modified random walk  
  > "we employ a large number of photon packages, $10^8$, and the modified random walk algorithm" (2.2.1 Continuum Radiative Transfer and Dust Temperature)
   - assumption: gas-to-dust ratio 100, isotropic scattering, dusty outflow cavity fiducial  
  > "A gas-to-dust mass ratio of 100 is adopted." (2.2.1 Continuum Radiative Transfer and Dust Temperature)
   - fitting: _not stated_
   - validation: _not stated_
2. **Synthetic CO PPV cubes**: radmc-3d LVG non-LTE line transfer for 12CO, 13CO, C18O at 20 inclinations  
  > "radmc-3d employs an approximate Large Velocity Gradient (LVG) method (cite: 1997NewA....2..365O) to solve the statistical equilibrium equation at each position." (2.2.2 12CO, 13CO and C18O Emission)
   - software: radmc-3d
   - parameter: microturbulence 1 km/s; 12CO/H = 1e-4; 13CO and C18O ratios 62 and 500  
  > "set the abundance ratios of $^{12}$CO/H nuclei to a fiducial value of $10^{-4}$, and the ratio of the isotopologues $^{13}$CO and C$^{18}$O to $^{12}$CO to fiducial values of 62 and 500" (2.2.2 12CO, 13CO and C18O Emission)
   - assumption: constant CO abundance, H2 dominant collision partner  
  > "the abundance of CO and its isotopologues is spatially constant" (2.2.2 12CO, 13CO and C18O Emission)
   - fitting: _not stated_
   - validation: _not stated_
3. **Synthetic ALMA observations**: CASA simalma with C36-3 12m array, 210 s, source at 2 kpc, PWV 0.5 mm, tclean imaging; also 12m+ACA test  
  > "we utilized CASA/`simalma` to post-process the synthetic molecular line data of $^{12}$CO (2-1)" (3.2 Synthetic ALMA Observations)
   - software: CASA, simalma, tclean
   - parameter: PWV 0.5 mm; synthetic beam 0.63x0.55 arcsec  
  > "The synthetic beam dimensions are $0.63^{\prime\prime}\times 0.55^{\prime\prime}$." (3.2 Synthetic ALMA Observations)
   - assumption: distance 2 kpc  
  > "We assumed that the source was located at a distance of 2 kpc" (3.2 Synthetic ALMA Observations)
   - fitting: _not stated_
   - validation: Compared 12m only vs 12m+ACA; distance dependence of spectra tested  
  > "the assumption of source distance affects the spectral shape, especially near the central velocity, but has minimal impact on the spectral wings." (3.2 Synthetic ALMA Observations)
4. **Estimate outflow mass, momentum, energy from CO spectra**: Optically thin column density from integrated Tb with LTE level correction, assumed Tex 10-50 K, LOS velocity cut 3-50 km/s; compared to true simulation values  
  > "We consider multiple excitation temperatures for the outflow gas, ranging from 10 K to 50 K." (3.3 Impact I+Impact II: Radiative Transfer)
   - parameter: mu=1.4, Tbg=2.7 K, 1 sigma threshold for synthetic ALMA  
  > "where $T_{\rm bg}$ is the background temperature, assumed to be 2.7K." (3.3 Impact I+Impact II: Radiative Transfer)
   - assumption: optically thin, LTE  
  > "It is worth noting that Equation [\[equ-Nu\]](#equ-Nu) assumes the molecular line is optically thin to derive the column density." (3.3 Impact I+Impact II: Radiative Transfer)
   - fitting: _not stated_
   - validation: Ratios to true values from simulation  
  > "In this section, we evaluate the estimation of outflow mass, momentum, and energy derived from synthetic molecular line emission and compare it with the true values acquired from simulations." (Estimating the Mass, Momentum and Energy of Synthetic Outflows)
5. **Mass and momentum outflow rates**: Outflow half-length from 3 sigma integrated intensity box; tau_dyn = length / mass-weighted mean LOS velocity; rate = quantity/tau_dyn; compare to true flux at 25,000 au  
  > "we estimate the dynamical timescale $\tau_{\rm dyn}$ of the outflow by calculating the ratio between the half length of the outflow and the mass-weighted mean LOS velocity." (3.4 Estimating the Mass Outflow Rate and Momentum Outflow Rate)
   - fitting: _not stated_
   - validation: _not stated_
6. **Fit observed spectra with synthetic spectra**: chi-squared fit for each protostellar mass and inclination, |v|>6 km/s, emission above 5 sigma, free v_offset (within ±6 km/s) and f_scale  
  > "we only have two free parameters in the $\chi^{2}$ fitting process for each protostellar mass and inclination angle." (4.2 Comparison of Observational and Synthetic Outflow 12CO (2-1) Spectra)
   - assumption: fixed 60 Msun initial core  
  > "the initial core mass in the simulation is fixed at 60 $M_{\mathord\odot}$" (4.2 Comparison of Observational and Synthetic Outflow 12CO (2-1) Spectra)
   - fitting: minimum chi-squared over grid  
  > "We obtain the minimum $\chi^{2}$ for each protostellar mass and inclination angle and subsequently arrange the $\chi^{2}$ values to identify the best-fitting parameters." (Comparison of Observational and Synthetic Outflow $^{12}$CO (2-1) Spectra)
   - validation: Compared with SED fitting results  
  > "provides a general constraint on the inclination angles of the outflows, aligning with the results constrained by SED fitting" (4.2 Comparison of Observational and Synthetic Outflow 12CO (2-1) Spectra)
7. **Observed outflow rates for three sources and correction**: Same method with fixed 15 arcsec half-length; apply correction factors 10 (mass rate) and 200 (momentum rate); compare with evolutionary tracks  
  > "After correcting the observed momentum outflow rate by a factor of 200, the final momentum outflow rate agrees with the theoretical protostellar evolutionary tracks." (4.3 Estimating the Mass Outflow Rate and Momentum Outflow Rate in Observations)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **radmc-3d** : Dust temperature and non-LTE LVG line radiative transfer  
  > "we employ the publicly available radiation transfer code radmc-3d" (2.2.2 12CO, 13CO and C18O Emission)
- **CASA** : simalma synthetic observations, calibration and tclean imaging  
  > "we utilized CASA/`simalma` to post-process" (3.2 Synthetic ALMA Observations)
- **ZEUS-MP** : The underlying MHD simulations (from Paper II)  
  > "which utilized the ZEUS-MP (cite: 2000RMxAC...9...66N) code" (2.1 Magnetohydrodynamics Simulations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total 3D momentum underestimation from LOS 3-50 km/s (ratio mean) | 7.892 | std 7.265 | dimensionless | 4 | / $p_{\rm w,out,3D, 0-\infty}/p_{\rm w,out,LOS, 3-50}$ / 7.892 / 5.055 / 2.763 / 43.29 / 7.265 / |
| Total mass/mass in 3-50 km/s (mean) | 23.68 | std 24.33 | dimensionless | 4 | / $m_{\rm w,out,LOS, 0-\infty}/m_{\rm w,out,LOS, 3-50}$ / 23.68 / 14.71 / 5.207 / 150.5 / 24.33 / |
| True/observed mass outflow rate from synthetic ALMA 12CO(2-1) | about 7 (about 10 at 60-70 deg) | wide variation | dimensionless | 5 | the true mass outflow rate is about 7 times larger |
| True/observed momentum outflow rate | about 200 (about 100 at ~60 deg) | wide variation | dimensionless | 5 | the true momentum outflow rate is about 200 times larger |
| G35.20 mass outflow rate (uncorrected) | 2.53 | 0.39 | 1e-5 Msun/yr | 7 | / G35.20 / 0.37$\pm$0.06 / 3.97$\pm$0.61 / 1.27$\pm$0.20 / 10.72 / 3.30 / 1.46 / 2.53$\pm$0.39 / 2.72$\pm$0.42 / |
| G45.47 mass outflow rate (uncorrected) | 5.01 | 0.77 | 1e-5 Msun/yr | 7 | / G45.47 / 2.53$\pm$0.39 / 29.95$\pm$4.63 / 11.94$\pm$1.84 / 11.85 / 12.60 / 5.04 / 5.01$\pm$0.77 / 5.94$\pm$0.92 / |
| G339.88 mass outflow rate (uncorrected) | 1.76 | 0.27 | 1e-5 Msun/yr | 7 | / G339.88 / 0.26$\pm$0.04 / 2.64$\pm$0.41 / 0.92$\pm$0.14 / 10.05 / 3.15 / 1.49 / 1.76$\pm$0.27 / 1.77$\pm$0.27 / |
| G45.47 fitted protostellar mass | about 24 | not stated | Msun | 6 | the protostellar mass of G45.47 is estimated to be around 24 $M_{\mathord\odot}$ |
| G35.20 fitted protostellar mass range | 8 to 16 | not stated | Msun | 6 | the protostellar mass of G35.20 likely falls within the range of 8 $M_{\mathord\odot}$ to 16 $M_{\mathord\odot}$ |

## Qualitative findings

- Mass near rest velocity (<3 km/s) is missed by about a factor of 10 or more; >50 km/s gas has negligible mass but significant momentum and energy.  
  > "a significant amount of mass, about ten times or more, is missed if excluding velocities near the rest frame velocity" (5 Conclusions)
- 13CO is a more reliable, optically thin tracer than 12CO.  
  > "which implies that $^{13}$CO (1-0) is more optically thin compared to $^{12}$CO (2-1)" (3.3)

## Claim tuples

- H: Can CO line emission recover true outflow mass, momentum, energy? | E: Compared estimates from raw and synthetic ALMA spectra with simulation truth | R: Scatter within factor 4 (12CO raw), 2 (13CO), 8 (ALMA mass); energy strongly underestimated | F: Mass and momentum uncertain by up to a factor of four; kinetic energy more strongly underestimated | **supported**
- H: Observed outflow rates from 12CO can be corrected to true rates | E: Derived conversion factors from synthetic ALMA data and applied to three sources | R: Factors ~10 (mass) and ~200 (momentum) | F: Corrected rates agree with theoretical evolutionary tracks | **supported**
- H: CO spectra constrain protostellar mass and inclination | E: chi-squared fit of synthetic to observed spectra | R: Inclinations consistent with SED fitting; masses poorly constrained except G45.47 | F: Broad constraint on inclination only | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Dust-free outflow cavity and 100 km/s outflow cutoff rejected in favor of dusty and 1 km/s cutoff  
  > "we consider that a model with standard dust in the outflow is the more realistic scenario" (2.2.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Single 60 Msun core evolutionary sequence; PDR effects ignored; fitted masses not reliable  
  > "caution is required when interpreting the fitted protostellar mass results" (4.2)
- Caveat (inferred, ours): Constant CO abundance and Tgas=Tdust ignore PDR/photodissociation
- Caveat (inferred, ours): Correction factors derived from one simulation track applied to sources with different core masses
- Caveat (inferred, ours): Observed outflow length fixed at 15 arcsec is a lower limit
- Caveat (inferred, ours): Synthetic observations at 2 kpc used for a source at 8.4 kpc

## Reproducibility

- Data public (paper): ALMA project 2015.1.01454.S named; public status not stated  
  > "(ALMA project ID: 2015.1.01454.S)" (4.1)
- Products in archive: _not stated_
- Missing: MHD simulation snapshots
- Missing: radmc-3d setup files
- Missing: simalma exact inputs
- Missing: fitting code
- Data volume (inferred): Tens of GB for ALMA data; simulation cubes additional
- Score (inferred): 3/5, Recipe is described but depends on unreleased MHD simulation outputs and simulation-specific processing.
- Rediscovery candidate: no, Main results rely on non-public MHD simulations.

## Links

- Method: (cite: 2023ApJ...947...40S) (MHD simulations analyzed)
- Method: (cite: 2019ApJ...873...73Z) (Outflow rate approach and G339.88 data)
- Companion: (cite: 2023ApJ...942....7F) (SED fitting of the three sources)
- Companion: (cite: 2022ApJ...936...68Z) (Previous presentation of G35.20 CO data)
- Related: SOMA survey

## Checks

```json
{
 "quotes": 66,
 "quotes_ok": 66,
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
  "facts": 94,
  "stated": 50,
  "rate": 0.532
 },
 "evidence_ok": true
}
```
