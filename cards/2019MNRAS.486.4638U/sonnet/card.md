# A dust and gas cavity in the disc around CQ Tau revealed by ALMA

`2019MNRAS.486.4638U` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Ubeira Gabellini, M. Giulia | arXiv: 1905.00909 | DOI: 10.1093/mnras/stz1138

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Do the gas and dust in the CQ Tau disc share an inner cavity, what are the cavity properties, and can an embedded planet explain them?  
  > "The models show that a gas inner cavity with size between 15 and 25 au is needed to reproduce the data with a density depletion factor between $\sim 10^{-1}$ and $\sim 10^{-3}$." (abstract)
- Target **CQ Tau**: coordinates RA = 05h35m58.46712s; dec = +24d44m54.0864s  
  > "We present Band 6 ALMA data of CQ Tau (RA = 05$^{\rm h}$35$^{\rm m}$58.46712$^{\rm s}$; dec = +24$^{\circ}$44$^{\prime}$54.0864$^{\prime \prime}$)" (2.2.1 Observational Strategy and Data Reduction); "It is a young ($\sim$10 Myr), nearby (162 pc, (cite: Gaia2016)), intermediate mass (1.67 $M_{\odot}$) star" (2.1 Target properties); z/distance 162 pc  
  > "We present Band 6 ALMA data of CQ Tau (RA = 05$^{\rm h}$35$^{\rm m}$58.46712$^{\rm s}$; dec = +24$^{\circ}$44$^{\prime}$54.0864$^{\prime \prime}$)" (2.2.1 Observational Strategy and Data Reduction); "It is a young ($\sim$10 Myr), nearby (162 pc, (cite: Gaia2016)), intermediate mass (1.67 $M_{\odot}$) star" (2.1 Target properties); distance from Gaia (Gaia2016)  
  > "We present Band 6 ALMA data of CQ Tau (RA = 05$^{\rm h}$35$^{\rm m}$58.46712$^{\rm s}$; dec = +24$^{\circ}$44$^{\prime}$54.0864$^{\prime \prime}$)" (2.2.1 Observational Strategy and Data Reduction); "It is a young ($\sim$10 Myr), nearby (162 pc, (cite: Gaia2016)), intermediate mass (1.67 $M_{\odot}$) star" (2.1 Target properties)

## Data provenance

- ALMA projects: 2013.1.00498.S, 2016.A.00026.S, 2017.1.01404.S
- bands: Band 6 (1.3 mm)  
  > "We present Band 6 ALMA data of CQ Tau" (2.2.1 Observational Strategy and Data Reduction)
- frequencies and spectral setup: CO(2-1), 13CO(2-1), C18O(2-1) and 1.3 mm continuum observed simultaneously  
  > "The ALMA correlator was configured to observe simultaneously CO(2–1), $^{13}$CO(2–1), and C$^{18}$O(2–1), as well as the nearby continuum at 1.3 mm." (2.2.1 Observational Strategy and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C34.6 (Cycle 2), C40.7 (Cycle 4), C43.8 (Cycle 5)  
  > "The array configurations used for Cycles 2, 4 and 5 are respectively C34.6, C40.7 and C43.8." (2.2.1 Observational Strategy and Data Reduction)
- baselines: _not stated_
- angular resolution: 0.15 arcsec Gaussian restoring beam (~24 au)  
  > "a Gaussian restoring beam of $0.\!\!^{\prime\prime}15$, corresponding to a spatial resolution of $\sim$24$\,$au" (2.2.1 Observational Strategy and Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: 30 uJy/beam continuum; 5 mJy/beam km/s in line integrated intensity maps  
  > "30 $\mu$Jy beam$^{-1}$ in the continuum, and 5 mJy beam$^{-1}$ km s$^{-1}$ in the line integrated intensity maps" (2.2.1 Observational Strategy and Data Reduction)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Three programs, Cycles 2, 4, 5 (PIs L. Pérez, L. Testi); data downloaded  
  > "After downloading the datasets, we reapplied the calibration tables and extracted the CQ Tau data from each of the four datasets" (2.2.1 Observational Strategy and Data Reduction)
- Line: 12CO J=2-1 (not stated)
- Line: 13CO J=2-1 (not stated)
- Line: C18O J=2-1 (not stated)
- External data: SED fluxes of CQ Tau from 0.36 um to 3.57 cm  
  > "Table [3](#tab:sed1) lists the fluxes of CQ Tau available in the literature between $360\,$nm and $3.57\,$cm." (Appendix SED) [from Table 3 refs: Creech2002, Mannings1997, Banzatti2011, Testi2003, Thi2001, Oja1987, Cutri2003, Mendigutia2012]
- External data: Stellar properties (luminosity from Lopez-2006 rescaled to Gaia distance; mass and age from Siess2000 tracks)  
  > "The luminosity L=6.6 L$_{\odot}$ from (cite: Lopez-2006) (d=130 pc) is re-scaled considering the new distance from GAIA" (Table 1) [from (cite: Lopez-2006); (cite: Siess2000); (cite: Gaia2016)]
- Simulation/model as data: DALI thermo-chemical disc models and 3D PHANTOM SPH planet-disc simulations (with RADMC3D post-processing) compared to ALMA radial profiles  
  > "We perform a set of 3D numerical simulations of a planet and a gas + dust accretion disc using the code PHANTOM (cite: Price2017)" (5.2 Numerical Simulations)

## Processing

### Calibration

- pipeline or manual: Calibration by ALMA with standard QA procedures; calibration tables reapplied  
  > "Data calibration was performed by ALMA following the standard Quality Assessment procedures for each of the three programmes." (2.2.1 Observational Strategy and Data Reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ~10%  
  > "We expect the intensity scale of these observations to be accurate within $\sim$ 10%, as described in the ALMA Technical Handbook" (2.2.1 Observational Strategy and Data Reduction)
- self calibration: One combined iteration of phase-only self-calibration, after proper motion correction  
  > "We corrected the data for the known proper motion of the star and performed one combined iteration of phase only self calibration." (2.2.1 Observational Strategy and Data Reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = +0.5  
  > "we imaged the data using a Briggs weighting with a robust parameter of +0.5" (2.2.1 Observational Strategy and Data Reduction)
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
- final beam: Gaussian restoring beam 0.15 arcsec  
  > "a Gaussian restoring beam of $0.\!\!^{\prime\prime}15$" (2.2.1 Observational Strategy and Data Reduction)
- final rms: 30 uJy/beam continuum; 5 mJy/beam km/s lines  
  > "30 $\mu$Jy beam$^{-1}$ in the continuum, and 5 mJy beam$^{-1}$ km s$^{-1}$ in the line integrated intensity maps" (2.2.1 Observational Strategy and Data Reduction)

### Inherited from earlier work

- Integrated intensity maps made by compensating for Keplerian rotation then integrating over optimized velocity range  
  > "The procedure we followed is very similar to the one presented in (cite: 2018arXiv180406272Y) and (cite: Ansdell2018)." (2.2.1 Observational Strategy and Data Reduction) [from (cite: 2018arXiv180406272Y); (cite: Ansdell2018)]
- Gas surface density parametrization: self-similar viscous disc profile  
  > "the density structure follows the simple parametric prescription proposed by (cite: Andrews2011)" (3.2 Gas and dust profiles) [from (cite: Andrews2011)]
- Dust opacities for standard ISM composition, optical constants for silicates and graphite  
  > "dust opacities considered follow (cite: 2001ApJ...548..296W) for a standard ISM dust composition." (3.2 Gas and dust profiles) [from (cite: 2001ApJ...548..296W); (cite: 2003ApJ...598.1017D)]
- Gaussian ring for large grains, inspired by earlier modelling of CQ Tau  
  > "Inspired by the work of (cite: 2018arXiv180407301P), we have employed a Gaussian functional profile" (4.2.1 A Gaussian ring for large grains) [from (cite: 2018arXiv180407301P)]
- One-fluid dust SPH algorithm  
  > "we adopt the one fluid algorithm developed in (cite: Laibe2014), (cite: Price2015) and (cite: ballabio2018)" (5.2 Numerical Simulations) [from (cite: Laibe2014); (cite: Price2015); (cite: ballabio2018)]

### Not stated but needed to reproduce (our reading)

- Velocity range used for integrating the line moment maps
- Continuum spectral windows and line-free channels
- Self-calibration solution interval and reference antenna/model
- Image size and cell size, clean threshold, masks
- Exact radial-cut bin widths for profiles
- DALI chemical network, CO abundance and isotope ratios, gas-to-dust prescriptions
- SPH initial disc mass, inner/outer radii, sink radii
- RADMC3D setup (opacities, inclination, wavelength)
- Definition of the dust-to-gas ratio and mass-integration radii

## Analysis recipe

1. **Image continuum and integrated CO maps**: Combine three datasets, phase-only self-cal, Briggs imaging with 0.15 arcsec beam; Keplerian-compensated moment-0 maps  
  > "we first compensate for the Keplerian velocity pattern, then we integrated the emission in each spatial pixel using an optimized range of velocities." (2.2.1 Observational Strategy and Data Reduction)
   - software: CASA
   - parameter: M*=1.67 Msun, d=162 pc, PA=55 deg, i=35 deg for Keplerian compensation  
  > "stellar mass M$_\star=1.67$ M$_\odot$, distance from the Sun d=162 pc, position angle of the disc major axis pa=55 deg, and inclination i=35 deg" (2.2.1 Observational Strategy and Data Reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract radial intensity profiles**: Radial cut along the major axis of continuum and moment-0 maps; error bars as dispersion in bins  
  > "The error bars shown in Figures [2](#fig:PROFILES) are computed as the dispersion of the measured points inside the bin." (2.3 Observational results)
   - fitting: _not stated_
   - validation: _not stated_
3. **Model SED and ALMA profiles with DALI**: Sparse grid of DALI models refined around best models; vary h_c, psi for SED; R_dust, sigma, Sigma_0,dust for continuum; R_cav, delta_gas, Sigma_0,gas, Sigma_0,small for CO; model images convolved with 0.15 arcsec beam  
  > "we explore the parameter space starting from a sparse grid of models, which is then refined around the values obtained for the best representative models." (3.3 Determining the best representative model)
   - software: DALI
   - parameter: inclination 33 deg in ray tracing; L*=10 Lsun, T*=6900 K blackbody; R_sub=0.2 au  
  > "spectral image cubes are created with a ray tracer fixing the inclination of the disc in the sky at 33$^{\circ}$" (3.1 DALI)
   - assumption: Two dust populations (small 0.005-1 um q=3.5; large 1 um-1 cm q=3), large grains settled with chi=0.2; Av=1.9, Rv=3.1 extinction  
  > "The small population has a scale height of $H$, whereas large grains have a scale height of $\chi H$, reduced by a factor $\chi =0.2$" (3.2 Gas and dust profiles)
   - fitting: No chi^2 minimisation; manual grid exploration by eye  
  > "We do not carry out any $\chi^2$ minimization analysis as the complexity of the DALI disc models does not allow us to cover a wide set of parameter values." (3.3 Determining the best representative model)
   - validation: Comparison of model profiles with data within error bars  
  > "The data are always matched by our model within the error bars" (4.2.1 A Gaussian ring for large grains)
4. **Derive masses and dust-to-gas ratio**: Integrate best-model mass components and cumulative radial mass  
  > "Fig. [8](#fig:cumfunct) shows the cumulative function of mass as a function of the radial distance from the star of both the gas (red) and the dust" (4.3 Dust-to-gas ratio)
   - software: DALI
   - fitting: _not stated_
   - validation: _not stated_
5. **Test planet-induced cavity analytically and with SPH simulations**: Gap-opening criterion (Crida), gap width, depletion; eight PHANTOM runs with planet 3-9 MJ at 20 au, grains 0.1 and 0.5 mm, 60 orbits; dust profiles post-processed with RADMC3D  
  > "Each simulation is evolved for $t=60\, t_{\rm orb}$, which corresponds to $\sim$ 4500 years." (5.2 Numerical Simulations)
   - software: PHANTOM, RADMC3D
   - parameter: alpha_AV=0.2 (alpha_SS~0.005-0.01); N_part=7.5e5 (convergence 1.5-2.2e6)  
  > "We choose the artificial viscosity parameter $\alpha_{\rm AV}=0.2$ in order to have an equivalent (cite: shakura73) turbulent parameter $\alpha_{\rm SS}\approx 0.005-0.01$" (5.2 Numerical Simulations)
   - assumption: Locally isothermal EOS; initial gas profile from DALI without depletion; no cavity initially  
  > "The planet is initially completely embedded in the disc, that is assumed to have an unperturbed density profile" (5.2.1 Initial conditions)
   - fitting: _not stated_
   - validation: Convergence tests with higher particle number  
  > "These high resolution runs are in good agreement with the lower resolution one throughout the entire disc both for gas and dust" (5.2.2 Results)

## Software

- **CASA** : _not stated_
- **DALI** : Thermo-chemical modelling of disc, SED and CO profiles  
  > "we use the physical-chemical code DALI (cite: Bruderer12; Bruderer13) that self-consistently computes the physical, thermal and chemical disc structure." (3.1 DALI)
- **PHANTOM** : 3D SPH planet-disc gas+dust simulations  
  > "using the code PHANTOM (cite: Price2017)" (5.2 Numerical Simulations)
- **RADMC3D** : Radiative transfer on hydrodynamical dust output  
  > "using a radiative transfer tool (RADMC3D, (cite: RADMC3D)) for the dust component" (5.2.3 Radiative transfer modelling)
- **miex** : Mie-theory dust mass extinction coefficients  
  > "the mass extinction coefficients were calculated using Mie theory with the $\rm miex$ code (cite: Wolf2004)" (3.2 Gas and dust profiles)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Gaussian ring peak radius of large dust R_dust | 53 | not stated | au | 3 | we find a center peak position of $R_{\rm dust}=53\,$au and a Gaussian width of $\sigma=13\,$au |
| Gaussian ring width sigma | 13 | not stated | au | 3 | we find a center peak position of $R_{\rm dust}=53\,$au and a Gaussian width of $\sigma=13\,$au |
| Gas cavity radius (best model) | 20 (range 15-25) | range 15-25 au | au | 3 | Our best representative model is shown with a red line in Fig. [7](#fig:fig7) and assumes $R_{\rm cav}=20$ au and $\delta_{\rm gas}=10^{-2}$. |
| Gas depletion factor inside cavity (best model) | 1e-2 (range 1e-3 to 1e-1) | range 1e-3 to 1e-1 | dimensionless | 3 | Observations agreed with a gas depletion factor of 10$^{-3}$ $< \delta_{\rm gas} <$ 10$^{-1}$. |
| Gas mass | 3.2e-3 | not stated | Msun | 4 | $M_{\rm gas} = 3,2 \cdot 10^{-3} M_{\odot}$; $M_{\rm small \, dust} = 4.9 \cdot 10^{-5} M_{\odot}$; $M_{\rm large \, dust} = 2.3 \cdot 10^{-4} M_{\odot}$ |
| Global dust-to-gas ratio | ~0.09 | not stated | dimensionless | 4 | The global dust-to-gas ratio for this model of CQ Tau is $\sim 0.09$. |
| Planet mass needed to open gap | 3-9 | not stated | M_Jup | 5 | $$M_{\rm p}\gtrsim 0.002\textrm{--}0.006 M_\star\approx 3\textrm{--}9\;M_{\rm J}$$ |
| Best-matching SPH planet | 6 MJup at 20 au with 0.1 mm grains | not stated | M_Jup | 5 | we found the best agreement with the data in the model with the planet at R$_{\rm p}$ = 20 au, M$_{\rm comp}$ = 6 M$_{\rm Jup}$ and the size of large grains of 0.1 mm |

## Qualitative findings

- Gas disc radial extent is about twice that of the mm dust disc  
  > "In the CQ Tau disc the gas radial extent is a factor of two broader than that one of the large dust grains;" (7 Conclusions)

## Claim tuples

- H: Is there a gas cavity inside the dust cavity of CQ Tau? | E: DALI modelling of 1.3 mm continuum, 12CO/13CO/C18O profiles and SED | R: Gas cavity radius 15-25 au with depletion 1e-3 to 1e-1; dust Gaussian ring at 53 au, sigma 13 au | F: Gas cavity is smaller than the dust cavity but depleted | **supported**
- H: Can an embedded planet at ~20 au explain the cavity? | E: PHANTOM SPH simulations with 3-9 MJ planets compared with DALI profiles | R: 6-9 MJ reproduces the ring at ~50 au but leaves inner dust disc and does not reach 1e-2 gas depletion | F: One-planet model only qualitatively reproduces observations | **partially**
- H: Is the dust-to-gas ratio standard? | E: Mass integration of best DALI model | R: Global dust-to-gas ~0.09 | F: Higher than ISM, likely carbon depletion | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: No chi2 minimisation because DALI models are too complex for a wide parameter grid  
  > "We do not carry out any $\chi^2$ minimization analysis as the complexity of the DALI disc models does not allow us to cover a wide set of parameter values." (3.3 Determining the best representative model)
- Alternative: Self-similar profile for large dust (gamma_dust=-0.7, Sigma0=0.85 g cm-2, cavity 28 au) also reproduces SED and continuum  
  > "The power law index of the surface density distribution is $\gamma_{\rm dust}=-0.7$ and the surface density normalization is $\Sigma_{\rm 0, dust}=0.85$ g cm$^{-2}$." (4.4 A further test for large dust grains)
- How they decided it was enough: _not stated_
- Limitation (authors): DALI models over-predict outer-disc emission; azimuthal asymmetries not analysed  
  > "The models always over-predict the emission in the outer disc ($^{13}$CO in particular)." (4.2.2 Gas radial profile)
- Caveat (inferred, ours): Parameter grid explored without formal fitting or uncertainties
- Caveat (inferred, ours): Axisymmetric models applied to a disc with azimuthal asymmetries
- Caveat (inferred, ours): Hydro simulations use single grain sizes and fixed alpha
- Caveat (inferred, ours): Inclination differs between Keplerian compensation (35 deg) and DALI (33 deg)
- Caveat (inferred, ours): Gas mass depends on assumed CO chemistry

## Reproducibility

- Data public (paper): Archival ALMA data from named programs; calibration tables reapplied after download  
  > "After downloading the datasets, we reapplied the calibration tables and extracted the CQ Tau data" (2.2.1 Observational Strategy and Data Reduction)
- Products in archive: _not stated_
- Missing: Velocity integration ranges
- Missing: Image/cell size, masks, clean parameters
- Missing: Full DALI input configuration and SPH setup files
- Missing: Self-calibration parameters
- Data volume (inferred): ~100-300 GB raw for three Band 6 programs
- Score (inferred): 3/5, Public data and key parameters given (robust, beam, model grid), but no code and manual grid modelling with missing imaging details.
- Rediscovery candidate: no, Main results come from manual DALI and SPH modelling that cannot be redone from the stated recipe alone.

## Links

- Method: (cite: Bruderer12; Bruderer13) (DALI code)
- Method: (cite: Price2017) (PHANTOM SPH code)
- Companion: (cite: 2018arXiv180407301P) (Earlier ALMA CQ Tau dust cavity modelling)
- Companion: (cite: Tripathi2017) (SMA detection of the continuum cavity)

## Checks

```json
{
 "quotes": 67,
 "quotes_ok": 67,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2016.A.000026.S"
 ],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 79,
  "stated": 46,
  "rate": 0.582
 },
 "evidence_ok": true
}
```
