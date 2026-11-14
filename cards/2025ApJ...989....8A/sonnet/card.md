# The ALMA Survey of Gas Evolution of PROtoplanetary Disks (AGE-PRO). VIII. The Impact of External Photoevaporation on Disk Masses and Radii in Upper Scorpius

`2025ApJ...989....8A` | The Astrophysical Journal 2025 | first author: Anania, Rossella | arXiv: 2506.10743 | DOI: 10.3847/1538-4357/adb587

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: protoplanetary_disks
- Question: Can 1D viscous disk evolution models including external photoevaporation by FUV from OB stars explain the gas and dust masses and radii of the ten AGE-PRO Upper Sco disks?  
  > "The aim of this work is to test if 1D viscous evolution models with the inclusion of external photoevaporation are able to explain disk masses and radii observed by the AGE-PRO survey in the Upper Sco region." (1 Introduction)
- Target **Ten AGE-PRO Upper Sco disks (UppSco 1-10)**: coordinates 2MASS ids given in Table (e.g. J16120668-3010270 for UppSco 1)  
  > "Upper Sco, located at $\sim$142 pc from the Sun (cite: Fang_pascucci_2023)" (1 Introduction); z/distance 131.9-158.4 pc per source; region ~142 pc  
  > "Upper Sco, located at $\sim$142 pc from the Sun (cite: Fang_pascucci_2023)" (1 Introduction); distance from region distance from Fang et al. 2023; per-source distances from AGE-PRO tables  
  > "Upper Sco, located at $\sim$142 pc from the Sun (cite: Fang_pascucci_2023)" (1 Introduction)

## Data provenance

- ALMA projects: 2021.1.00128.L
- bands: Band 6 (1.3 mm) continuum  
  > "all the dust properties are estimated at wavelength $1.3$ mm, which corresponds to the continuum Band 6 observations of AGE-PRO (cite: AGEPRO_IV_UpperSco)" (4.4 Evaluation of Disk Radius and Mass)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~30 AU  
  > "Given that the spatial resolution of AGE-PRO is $\sim$30 AU (cite: AGEPRO_IV_UpperSco)" (6.2 Dust Results)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO not stated (not stated)
- Other facility **Gaia DR3 / Hipparcos**: Parallaxes and stellar parameters of OB stars used for FUV flux  
  > "The stellar parameters are taken from Gaia DR3" (3.1 Field Stars Selection)
- Other facility **SIMBAD / ALS II**: Spectral types and luminosity classes of OB stars  
  > "We retrieve the spectral type and luminosity class of the stars from the SIMBAD database" (3.1 Field Stars Selection)
- External data: Disk gas masses, 12CO R90 radii, dust radii, mm fluxes, stellar masses and ages of the ten sources  
  > "A more detailed description of the source sample, along with the method used for measuring disk masses and sizes can be found in (cite: AGEPRO_IV_UpperSco)" (2 Disk sample) [from (cite: AGEPRO_IV_UpperSco), (cite: AGEPRO_V_gas_masses), (cite: AGEPRO_XI_gas_disk_sizes), (cite: AGEPRO_X_dust_disks)]
- External data: FRIEDv2 grid of external photoevaporation mass-loss rates  
  > "we perform a bi-linear interpolation of a sub-set of the FRIEDv2 grid (cite: FRIEDv2)" (4.1 Gas Evolution) [from (cite: FRIEDv2)]
- External data: Critical 12CO column density relation fitted to DALI models  
  > "The above expression is retrieved from fitting the results of DALI thermochemical models and depends on the initial carbon abundance and the disk temperature." (4.4 Evaluation of Disk Radius and Mass) [from (cite: Trapman_2023)]
- Simulation/model as data: DustPy 1D gas+dust evolution with external photoevaporation; grid alpha=1e-2,1e-3,1e-4, Rc,0=10,40,100 AU, Mdisk,0=0.01,0.1 Mstar  
  > "Values for the $\alpha$ viscosity parameter, initial characteristic radius ${R_{\rm{c},0}}$, and disk mass $\mathrm{M_{disk,0}}$ explored in our simulations." (Table 2)

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
- weighting robust: _not stated_
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
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Gas masses, gas/dust radii and fluxes taken from AGE-PRO papers  
  > "In this work we compare the results of numerical simulations with the disk properties listed in Table [\[tab:source_params\]]" (2 Disk sample) [from (cite: AGEPRO_IV_UpperSco), (cite: AGEPRO_V_gas_masses), (cite: AGEPRO_XI_gas_disk_sizes), (cite: AGEPRO_X_dust_disks)]
- Numerical implementation of external photoevaporation outside-in depletion  
  > "Following the numerical approach of (cite: sellek_fried), we implement the outside-in depletion of gas and dust at $R > R_{\mathrm{t}}$" (4.1 Gas Evolution) [from (cite: sellek_fried)]

### Not stated but needed to reproduce (our reading)

- AGE-PRO derived values come from companion papers not fully reproduced here
- Full list of OB stars truncated in appendix table
- Number of Monte Carlo iterations for flux and Spearman tests
- Details of interpolation of Trapman 2023 Fig. 2 for FUV dependence
- Stellar luminosity fixed at 0.3 Lsun, so not source-specific
- Dust grain material density and Ricci 2010 volume fractions not given
- Time step and DustPy version

## Analysis recipe

1. **Compute FUV flux at each disk**: Sum FUV luminosity of 174 OB stars (blackbody Teff from spectral type, mass from evolution models, L_FUV from empirical relation) with 3D distances from inverted Gaia parallaxes; Monte Carlo over parallax errors  
  > "Finally, the FUV flux experienced by each disk is determined by the contribution of the overall field stars" (3.2 FUV Flux Experienced by the Sources)
   - software: Astropy
   - parameter: median flux with 16th/84th percentiles  
  > "The error bars reach down to the 16$^{\mathrm{th}}$ percentile and up to the 84$^{\mathrm{th}}$ percentile of the flux distribution." (3.2 FUV Flux Experienced by the Sources)
   - assumption: Blackbody emission for stars; extinction from residual gas neglected  
  > "For simplicity we are assuming a blackbody emission for the stars." (3.2 FUV Flux Experienced by the Sources)
   - fitting: _not stated_
   - validation: Parallax inversion compared with Bailer-Jones distances; RUWE<1.4; 2D upper-limit flux  
  > "we show in Figure [19](#fig:ruwe) that the ours and Bailer-Jones (cite: Bailer-Jones) method for distance evaluation yield the same outcome" (8.3 Uncertainty on the FUV flux calculation)
2. **Run viscous + external photoevaporation disk evolution**: DustPy with Garate 2023 module and FRIEDv2 interpolation; Lynden-Bell & Pringle initial profile; 250 cells from 5 to 500 AU  
  > "Our numerical simulations are performed using `DustPy` (cite: dustpy) along with an integrated module that incorporates the effects of external photoevaporation (cite: Garate_2023)" (4.3 Simulation Setup)
   - software: DustPy
   - parameter: alpha 1e-2/1e-3/1e-4; Rc,0 10/40/100 AU; Mdisk,0 0.01/0.1 Mstar; vfrag 10 m/s; dust-to-gas 0.01; psi=0.05; L*=0.3 Lsun  
  > "the initial dust-to-gas ratio for the distribution of particles is 0.01 and the fragmentation velocity is set to $v_{\mathrm{frag}} = 10$ $\mathrm{m\ s^{-1}}$" (4.3 Simulation Setup)
   - assumption: Constant alpha; no internal photoevaporation; constant FUV flux  
  > "In our model we neglect the effects of internal photoevaporation" (4.1 Gas Evolution)
   - fitting: No fitting; grid comparison at 2 and 6 Myr  
  > "Therefore, we compare the resulting disk masses and sizes at 2 and 6 Myr with the AGE-PRO observed values." (Simulation Setup)
   - validation: Test runs with FUV=0-1000 G0  
  > "The FUV flux experienced varies from 0 to 1000 G$_{0}$." (Test the Effect of External Photoevaporation on Disk Properties)
3. **Derive model observables and compare with AGE-PRO**: Gas radius from critical column density (Trapman 2023); 1.3 mm flux and R90 dust from optically thin emission with DSHARP opacities, T_dust=20 K, d=142 pc; Spearman correlations by Monte Carlo  
  > "The dust radius is determined as the position in the disk that encompasses 90% of the continuum flux" (4.4 Evaluation of Disk Radius and Mass)
   - software: DSHARP opacity library
   - parameter: mu_gas = 2.3 mu_H  
  > "which we set to the standard value $\mu_{\mathrm{gas}} \sim 2.3 \ \mu_{\mathrm{H}} = 1.15 \ \mu_{\mathrm{H}_{2}}$" (4.4 Evaluation of Disk Radius and Mass)
   - assumption: Face-on, no scattering, isothermal  
  > "If we neglect scattering and assume a face-on[^4] and vertical isothermal disk" (4.4 Evaluation of Disk Radius and Mass)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **DustPy** : Gas and dust evolution simulations  
  > "Astropy ((cite: astropy:2013) (cite: astropy:2013), (cite: astropy:2018)), `Dustpy` (cite: dustpy), Matplotlib (cite: Matplotlib_2007), Numpy (cite: Numpy_2020)" (Software)
- **Astropy** : general analysis  
  > "Astropy ((cite: astropy:2013) (cite: astropy:2013), (cite: astropy:2018))" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Median FUV flux range at the ten sources | 2.5 to 12.0 | 16th-84th percentiles in Table 1 | G0 | 1 | / UppSco 2 / 12.049 / 5.898 / 34.335 / |
| Spearman rho, R12CO vs FUV | -0.41 | -0.63 to -0.18 (16-84%) | dimensionless | 3 | / $R_{^{12}\rm{CO}}$ / -0.41 / -0.63 / -0.18 / 0.12 / 0.02 / 0.31 / |
| Spearman rho, Rdust vs FUV | -0.52 | -0.69 to -0.28 (16-84%) | dimensionless | 3 | / $R_{\rm{dust}}$ / -0.52 / -0.69 / -0.28 / 0.064 / 0.01 / 0.21 / |
| Disks with gas size reproduced within factor <2 | 7 of 10 | not stated | count | 3 | we can successfully reproduce gas disk sizes for 7 out of 10 sources within a factor $<$2, when the initial disk mass is 1-10% of the stellar mass |

## Qualitative findings

- Even moderate FUV (1-10 G0) suppresses viscous spreading and shrinks gas disks; disk mass changes only later  
  > "even moderate levels of irradiation can suppress disk spreading" (5.1 Test the Effect of External Photoevaporation on Disk Properties)
- Dust radii and mm fluxes not reproduced; substructures needed  
  > "In general, the models are not able to reproduce consistently both dust radii and mm fluxes." (5.4 AGE-PRO Dust Results)

## Claim tuples

- H: Pure viscous evolution explains Upper Sco disk properties | E: Compare viscous DustPy models with AGE-PRO masses and radii | R: Observed gas radii inconsistent with viscous models | F: Pure viscous framework fails | **supported**
- H: External photoevaporation reconciles models with gas sizes | E: Add FRIEDv2-based mass loss with computed FUV fluxes | R: 7/10 gas sizes within factor <2 for initial mass 1-10% Mstar | F: External photoevaporation matters even at moderate FUV | **supported**
- H: Initial disk extent can be constrained | E: Vary Rc,0 for UppSco 6 and 8 | R: Disks converge to similar size | F: Not constrainable | **refuted**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: MHD wind-driven accretion not tested; its role is not excluded  
  > "since we did not test alternative models in which accretion is driven by winds" (6.1 Gas Results)
- How they decided it was enough: _not stated_
- Limitation (authors): Sample too small for robust correlations  
  > "our disk sample is too small to offer robust statistical evidence for the presence of correlations" (5.7 Correlations: FUV Flux and Disk Properties)
- Limitation (authors): FUV flux uncertain, especially UppSco 2, from parallax inversion  
  > "the inferred median FUV flux may tend to be underestimated." (8.3 Uncertainty on the FUV flux calculation)
- Caveat (inferred, ours): Single fixed stellar luminosity (0.3 Lsun) for all sources
- Caveat (inferred, ours): Constant present-day FUV flux assumed
- Caveat (inferred, ours): No quantitative goodness-of-fit; comparison by eye in figures
- Caveat (inferred, ours): Smooth dust disks only

## Reproducibility

- Data public (paper): AGE-PRO ALMA data cited as ADS/JAO.ALMA#2021.1.00128.L; derived values from companion papers  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA$\#$2021.1.00128.L." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Simulation input files and scripts
- Missing: Full OB star list
- Missing: Companion-paper measurements
- Data volume (inferred): Negligible; uses tabulated results, no ALMA data reduction
- Score (inferred): 3/5, Models and public tools (DustPy, FRIEDv2) are named, but many settings and scripts are unstated, and observables come from companion papers.
- Rediscovery candidate: no, Main work is simulation with unreleased setup rather than ALMA data analysis.

## Links

- Method: (cite: dustpy) (Simulation code)
- Method: (cite: Garate_2023) (External photoevaporation module in DustPy)
- Method: (cite: FRIEDv2) (Mass-loss grid)
- Method: (cite: Trapman_2023) (Critical column density for 12CO radius)
- Companion: (cite: AGEPRO_I_overview) (AGE-PRO overview)
- Companion: (cite: AGEPRO_IV_UpperSco) (Upper Sco sample)
- Companion: (cite: AGEPRO_V_gas_masses) (Gas masses)
- Companion: (cite: AGEPRO_XI_gas_disk_sizes) (Gas disk sizes)
- Companion: (cite: AGEPRO_X_dust_disks) (Dust disk radii)
- Related: AGE-PRO
- Related: FRIED

## Checks

```json
{
 "quotes": 44,
 "quotes_ok": 44,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 34,
  "rate": 0.466
 },
 "evidence_ok": true
}
```
