# The complex chemistry of hot cores in Sgr B2(N): influence of cosmic-ray ionization and thermal history

`2019A&A...628A..27B` | Astronomy and Astrophysics 2019 | first author: Bonfand, M. | arXiv: 1906.04695 | DOI: 10.1051/0004-6361/201935523

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: astrochemistry, star_formation, milky_way_ism
- Question: What physical history and environmental conditions (cosmic-ray ionization rate, minimum prestellar dust temperature) explain the chemical differences among the Sgr B2(N2-N5) hot cores?  
  > "Our main goal is to characterize the physico-chemical evolution of Sgr B2(N)’s sources in order to explain their chemical differences and constrain their environmental conditions." (abstract)
- Target **Sgr B2(N2-N5) hot cores**: coordinates phase center alpha_J2000 = 17h47m19.87s, delta_J2000 = -28d22'16.0"  
  > "The phase center is located half way between the two main hot molecular cores Sgr B2(N1) and N2" (2.1 The EMoCA survey); "with $D$ = 8.34 kpc the distance to Sgr B2(N) from the Sun (cite: reid2014)" (2.1 Column densities and masses); z/distance D = 8.34 kpc  
  > "The phase center is located half way between the two main hot molecular cores Sgr B2(N1) and N2" (2.1 The EMoCA survey); "with $D$ = 8.34 kpc the distance to Sgr B2(N) from the Sun (cite: reid2014)" (2.1 Column densities and masses); distance from Reid et al. 2014  
  > "The phase center is located half way between the two main hot molecular cores Sgr B2(N1) and N2" (2.1 The EMoCA survey); "with $D$ = 8.34 kpc the distance to Sgr B2(N) from the Sun (cite: reid2014)" (2.1 Column densities and masses)

## Data provenance

- ALMA projects: 2011.0.00017.S, 2012.1.00012.S
- bands: _not stated_
- frequencies and spectral setup: 84.1-114.4 GHz, five spectral setups  
  > "The survey is divided into five spectral setups covering the frequency range between 84.1 GHz and 114.4 GHz" (2.1 The EMoCA survey)
- continuum bandwidth: _not stated_
- arrays: 12 m antennas, ALMA cycles 0 and 1  
  > "The EMoCA imaging spectral line survey was conducted with ALMA in its cycles 0 and 1" (2.1 The EMoCA survey)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~1.6 arcsec  
  > "at high angular resolution ($\sim$1.6$\ensuremath{''}$) with a sensitivity of $\sim$3 mJy/beam per 488 kHz" (2.1 The EMoCA survey)
- max recoverable scale: _not stated_
- sensitivity: ~3 mJy/beam per 488 kHz channel  
  > "with a sensitivity of $\sim$3 mJy/beam per 488 kHz (1.7 to 1.3 km s$^{-1}$) wide channel" (2.1 The EMoCA survey)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **SMA**: 343 GHz dust continuum map used (in earlier work) to derive beta  
  > "dust continuum emission map obtained with the submillimeter array (SMA) at 343 GHz (cite: qin2011)" (2.1 Column densities and masses)
- External data: Peak flux density of Sgr B2(N3) at 242 GHz (0.4" resolution)  
  > "we use the peak flux density measured by (cite: sanchezmonge2017) at 242 GHz in ALMA data obtained at 0.4$\ensuremath{''}$ resolution" (2.1 Column densities and masses) [from Sánchez-Monge et al. 2017 (cite: sanchezmonge2017)]
- External data: Dust opacities, beta=1.3, kappa0=0.0199 cm2/g at 230 GHz  
  > "which corresponds to a dust emissivity exponent of $\beta$ = 1.3, with $\kappa_0 = 0.0199$ cm$^2$ g$^{-1}$ (of gas) at $\nu_0$ = 230 GHz" (2.1 Column densities and masses) [from Ossenkopf & Henning 1994 (cite: ossenkopf1994)]
- External data: Mass-luminosity relation for accreting protostars  
  > "we use the mass-luminosity relation derived by (cite: hosokawa2009) for spherically accreting protostars" (2.4 Protostellar evolution) [from Hosokawa & Omukai 2009 (cite: hosokawa2009)]
- Simulation/model as data: Published RMHD simulation (run E) of Peters et al. 2011 used for accretion-rate evolution  
  > "we use published results from theoretical simulations of high-mass star formation" (2.4 Protostellar evolution)

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
- continuum subtraction: first-order baseline fitted to line-free channels of spectra at source peak positions, using CLASS  
  > "In each spectral window of each setup, a first-order baseline is subtracted to the channels that are free of strong line emission to separate the spectral lines from the continuum." (Data reduction)
- line free channels: _not stated_
- primary beam correction: applied to spectra and continuum  
  > "that we compare to the observed continuum-subtracted spectra, after correction for the primary beam attenuation" (Radiative transfer modeling of the line survey)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Observations, calibration and imaging procedures  
  > "A detailed description of the observations, the calibration, and the imaging procedures is presented in (cite: belloche2016)." (2.1 The EMoCA survey) [from (cite: belloche2016)]
- Details of LTE line-modeling methods  
  > "More details about the methods of analysis can be found in (cite: bonfand2017)." (Radiative transfer modeling of the line survey) [from (cite: bonfand2017)]
- Chemical network and binding energies  
  > "The chemical network is based on that of (cite: belloche2017)." (3.1 A three-phase astrochemical code) [from (cite: belloche2017)]
- Initial abundances  
  > "Initial abundances are taken from (cite: garrod2013)." (3.1 A three-phase astrochemical code) [from (cite: garrod2013)]

### Not stated but needed to reproduce (our reading)

- CASA/pipeline version and calibration details (deferred to Belloche et al. 2016)
- line-free channels used for baseline subtraction
- continuum flux densities of N2, N4, N5 and free-free correction values
- exact fitted Weeds parameters for N2 and fit procedure details
- MAGICKAL code access and exact fitted accretion-rate relation Mdot(t)

## Analysis recipe

1. **separate continuum and lines**: First-order baseline subtraction on spectra at source peak positions  
  > "In each spectral window of each setup, a first-order baseline is subtracted to the channels that are free of strong line emission" (Data reduction)
   - software: CLASS
   - fitting: _not stated_
   - validation: _not stated_
2. **derive COM column densities by LTE modeling**: Weeds synthetic spectra; population diagrams for Trot, 2D Gaussians for size, 1D Gaussians for linewidth/offset, column density adjusted manually  
  > "The column density is adjusted manually until a good fit to the data is obtained." (Radiative transfer modeling of the line survey)
   - software: Weeds, CLASS
   - assumption: LTE valid at high densities  
  > "collisions in the gas phase are frequent enough for the local thermodynamic equilibrium (LTE) approximation to be valid" (Radiative transfer modeling of the line survey)
   - fitting: manual adjustment, no sampler  
  > "The column density is adjusted manually until a good fit to the data is obtained." (Observations and methods of analysis, Radiative transfer modeling of the line survey)
   - validation: Uncertainty tested by varying size and Trot; column densities vary at most by factor four  
  > "we find that column densities vary at most by a factor four" (Appendix: Uncertainties on column densities)
3. **H2 column density and mass from dust continuum**: Optically thin-corrected dust emission formula with power-law opacity; mass within beam  
  > "We derive column densities from the dust thermal emission measured in the ALMA continuum emission maps toward each source" (2.1 Column densities and masses)
   - parameter: Td = 150 K, mu_H2 = 2.8, D = 8.34 kpc  
  > "$B_{\nu}(T_{\rm d}$) the Planck function at the dust temperature $T_{\rm d}$ = 150 K" (2.1 Column densities and masses)
   - assumption: gas-to-dust ratio 100; Ossenkopf & Henning opacity without ice mantles, n=1e6  
  > "Assuming the following gas-to-dust mass ratio, $M_{\rm d} = M_{\rm g} / \chi_{\rm d}$ with $\chi_{\rm d}$ = 100" (2.3 Luminosity and temperature profile)
   - fitting: _not stated_
   - validation: Compared with Sanchez-Monge et al. 2017 for N3  
  > "This gives $N_{\rm H_2}$ = 3.7$\times$10$^{24}$ cm$^{-2}$, a factor $\sim$ 4 higher than the value we derived in this paper." (Discussion, Physical properties of Sgr B2(N)'s hot cores)
4. **estimate current luminosities**: RADMC-3D 1D spherical envelope with rho ~ r^-1.5; luminosity adjusted until Td(r0)=T0=150 K  
  > "for each source the luminosity of its central protostar is adjusted until the calculated dust temperature in the envelope matches the observational constraint" (2.3 Luminosity and temperature profile)
   - software: RADMC-3D
   - parameter: envelope radius 1e6 au, 5e4 cells, Modified Random Walk  
  > "with a radius of 10$^6$ au (that is 4.8 pc), divided into 5$\times$10$^4$ cells" (2.3 Luminosity and temperature profile)
   - assumption: point-source blackbody protostar, no scattering  
  > "The protostar is defined as a point-source (that is its radius is not taken into account) and we assume simple black body radiation by setting its effective temperature." (Physical properties of Sgr B2(N)'s hot cores, Luminosity and temperature profile)
   - fitting: manual luminosity adjustment  
  > "for each source the luminosity of its central protostar is adjusted until the calculated dust temperature in the envelope matches the observational constraint, $T_{\rm d}(r_0)$ = $T_0$." (Physical properties of Sgr B2(N)'s hot cores, Luminosity and temperature profile)
   - validation: _not stated_
5. **time evolution and ages**: Mdot(t) from Peters et al. 2011 with floor of 1e-4 Msun/yr; M(t); L(t) via Hosokawa & Omukai; age from current L  
  > "we simply assume that the accretion rate does not drop below 10$^{-4} \Msol$ yr$^{-1}$" (2.4 Protostellar evolution)
   - assumption: same accretion history for all sources  
  > "our analysis assumes that the evolution of the accretion rate, $\dot{M}(t)$, is the same for all sources" (Discussion, Limitations on the physical models of Sgr B2(N2-N5))
   - fitting: _not stated_
   - validation: _not stated_
6. **build physical model (quasi-static contraction + free-fall)**: 1 Myr contraction from n=3e3 cm-3, Av=2, then free-fall trajectory with density, Av and temperature profiles to 400 K  
  > "from $t_{\rm start}$ = -1$\times$10$^6$ yr to $t_0$ = 0" (2.5.1 Quasi-static contraction)
   - parameter: Tmin = 10, 15, 20 K (plus 25, 28 K for N2)  
  > "we run additional simulations with $T_{\rm min}$ = 25 K and 28 K for N2, with $\zeta^{\rm H_2}$ = 50$\times \zeta^{\rm H_2}_0$" (Discussion, Constraining the physical parameters)
   - fitting: _not stated_
   - validation: _not stated_
7. **run chemical model grid**: MAGICKAL, 18 models per source (6 CRIR x 3 Tmin), 1333 species, 13374 reactions  
  > "For each hot core we run a grid of 18 models, one for each set of physical parameters (CRIR and $T_{\rm min}$" (3.2 The chemical models)
   - software: MAGICKAL
   - parameter: CRIR 1.3e-17 to 1.3e-14 s-1; ISRF 1 G0  
  > "We run chemical simulations using CRIRs ranging from the standard value $\zeta^{\rm H_2}_0$ = 1.3$\times$10$^{-17}$ s$^{-1}$ to 1000$\times \zeta^{\rm H_2}_0$ = 1.3$\times$10$^{-14}$ s$^{-1}$." (Chemical modeling, The chemical models)
   - assumption: no CR attenuation  
  > "we assume for simplicity that no attenuation occurs in the envelope of the sources" (Chemical modeling, The chemical models)
   - fitting: _not stated_
   - validation: _not stated_
8. **compare models with observations**: Confidence level kappa = erfc(|log Rmodel - log Robs|/(sqrt2 sigma)), sigma=1 dex, averaged over molecules  
  > "For each model we take the mean of the confidence levels obtained for the molecules in the sample to define the overall confidence level" (Appendix: Confidence level)
   - fitting: grid comparison, no sampler  
  > "For each model, we compute a level of confidence, $\kappa_{\rm i}$, in the agreement between calculated and observed abundances" (Appendix, Confidence level of the models with respect to the observations)
   - validation: _not stated_

## Software

- **CLASS** : continuum/line separation of spectra  
  > "using the CLASS[^1] software" (Data reduction)
- **Weeds** : LTE synthetic spectra  
  > "We use *Weeds* (cite: maret2011), which is part of the CLASS software, to produce LTE synthetic spectra" (Radiative transfer modeling of the line survey)
- **RADMC-3D** 0.41: dust temperature profiles and luminosities  
  > "We use the radiative transfer code RADMC-3D (version 0.41), to compute dust temperature profiles" (2.3 Luminosity and temperature profile)
- **MAGICKAL** : time-dependent gas-grain chemistry  
  > "we use the astrochemical code MAGICKAL (cite: garrod2013) to calculate chemical abundances" (3.1 A three-phase astrochemical code)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Current luminosity N2 | 2.63e5 | +3.13/-1.58 e5 | Lsun | 4 | We estimate the current luminosities of N2, N3, N4, and N5 to be 2.6$\times$10$^5$ $\ensuremath{L_{\odot}}$ |
| Current luminosity N3 | 4.5e4 | +1.6/-2.0 e4 | Lsun | 4 | 4.5$\times$10$^{4}$ $\Lsol$ |
| Current luminosity N4 | 3.9e5 | +4.17/-2.62 e5 | Lsun | 4 | 3.9$\times$10$^{5}$ $\Lsol$ |
| Current luminosity N5 | 2.8e5 | +1.77/-1.52 e5 | Lsun | 4 | 2.8$\times$10$^{5}$ $\Lsol$ |
| Best-fit CRIR | 7e-16 | not stated | s-1 | 8 | The best match between chemical models and observations is obtained for $\zeta^{\rm H_2}$ = 7$\times$10$^{-16}$ s$^{-1}$ |
| N2 density at 6010 au | 1.4e7 | not stated | cm-3 | 3 | We derived gas densities of 1.4$\times$10$^7$ cm$^{-3}$ toward Sgr B2(N2) at a radius of 6010 au |
| Gas mass N2 within beam | 151 | 42 | Msun | 3 | / N2 / 8.01(0.50) / 1.42(0.39) / 151(42) |

## Qualitative findings

- N3 and N5 share similar composition relative to methanol; N2 differs significantly.  
  > "N3 and N5 share a similar chemical composition while N2 differs significantly from the other sources." (abstract)

## Claim tuples

- H: Can a CRIR be constrained from COM abundances in Sgr B2(N2-N5)? | E: Grid of MAGICKAL models compared via confidence levels | R: Best match for CRIR 50x standard | F: CRIR ~7e-16 s-1, lower than diffuse-medium GC values | **supported**
- H: What minimum prestellar dust temperature is allowed? | E: Models with Tmin 10-28 K | R: 15 K works, >=25 K gives low confidence | F: Tmin>=25 K excluded | **supported**
- H: Same accretion history for all sources explains their chemistry | E: Models with common Mdot(t) | R: N3 gets much shorter age and worse agreement | F: Tailored RMHD simulations needed | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Stronger ISRF (100-1000 G0) tested; no improvement for abundances relative to methanol  
  > "The confidence levels drop significantly for models with higher $\chi_{\rm UV}$." (Appendix: Influence of the external radiation field)
- How they decided it was enough: _not stated_
- Limitation (authors): Ages unreliable because the same accretion history is assumed for all sources; no CR attenuation.  
  > "The estimated $t_{\rm source}$ values are unlikely to be accurate" (5.5 Limitations)
- Caveat (inferred, ours): Model confidence differences are modest and no formal model uncertainty is propagated
- Caveat (inferred, ours): Luminosity relies on assumption that COM emission traces radiatively heated gas
- Caveat (inferred, ours): Manual LTE fits with no formal posterior

## Reproducibility

- Data public (paper): Interferometric data available in the ALMA archive  
  > "The interferometric data are available in the ALMA archive at https://almascience.eso.org/aq/." (Acknowledgements)
- Products in archive: _not stated_
- Missing: MAGICKAL code and network files
- Missing: Belloche et al. 2016 calibration/imaging parameters
- Missing: Fitted Mdot(t) function
- Data volume (inferred): ~100s GB to ~1 TB (5 setups, cycles 0/1, 12 m array)
- Score (inferred): 3/5, Data public and analysis described, but heavy dependence on earlier papers and unreleased chemical code with manual fits.
- Rediscovery candidate: no, Main results depend on a specialized chemical code and inherited calibration choices; many steps are manual.

## Links

- Method: Belloche et al. 2016 (cite: belloche2016) (EMoCA observations, calibration and imaging)
- Method: Bonfand et al. 2017 (cite: bonfand2017) (Source analysis and LTE methods)
- Method: Garrod 2013 (cite: garrod2013) (MAGICKAL chemical code)
- Companion: Belloche et al. 2017 (cite: belloche2017) (N2 chemical network and abundances)
- Related: EMoCA
- Related: ReMoCA

## Checks

```json
{
 "quotes": 65,
 "quotes_ok": 65,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 92,
  "stated": 49,
  "rate": 0.533
 },
 "evidence_ok": true
}
```
