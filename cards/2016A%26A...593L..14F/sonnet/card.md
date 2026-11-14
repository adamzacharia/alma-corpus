# Magnetically regulated fragmentation of a massive, dense, and turbulent clump

`2016A&A...593L..14F` | Astronomy and Astrophysics 2016 | first author: Fontani, F. | arXiv: 1608.08083 | DOI: 10.1051/0004-6361/201629442

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Is the fragmentation of a massive, dense, turbulent clump regulated by magnetic support? ALMA fragment populations are compared with 3D RMHD simulations with strong (mu=2) and weak (mu=200) magnetization.  
  > "we demonstrate that the fragmentation due to self-gravity is dominated by the magnetic support" (Discussion and conclusion)
- Target **IRAS16061–5048c1 (I16061c1)**: coordinates RA 16h10m06.61s, Dec -50d50m29s (J2000, phase centre)  
  > "located at 3.6 kpc (Fontani et al. (cite: fontani2005))" (Introduction); "The phase centre was at R.A. (J2000): 16$^h$10$^m$06.$^{\prime\prime}$61 and Dec (J2000): $-50^{\circ}50^{\prime}29$$''$" (Observations and data reduction); z/distance 3.6 kpc  
  > "located at 3.6 kpc (Fontani et al. (cite: fontani2005))" (Introduction); "The phase centre was at R.A. (J2000): 16$^h$10$^m$06.$^{\prime\prime}$61 and Dec (J2000): $-50^{\circ}50^{\prime}29$$''$" (Observations and data reduction); distance from Fontani et al. 2005  
  > "located at 3.6 kpc (Fontani et al. (cite: fontani2005))" (Introduction); "The phase centre was at R.A. (J2000): 16$^h$10$^m$06.$^{\prime\prime}$61 and Dec (J2000): $-50^{\circ}50^{\prime}29$$''$" (Observations and data reduction)

## Data provenance

- ALMA projects: 2012.1.00366.S
- bands: _not stated_
- frequencies and spectral setup: continuum ~278 GHz; N2H+(3-2) also used  
  > "dust thermal continuum emission at $\sim 278$ GHz" (Introduction)
- continuum bandwidth: ~1703 MHz  
  > "The total bandwidth used is $\sim 1703$ MHz." (Observations and data reduction)
- arrays: _not stated_
- configurations: C36-6, max baseline 1091 m  
  > "The array was in configuration C36-6, with maximum baseline of 1091 m." (Observations and data reduction)
- baselines: _not stated_
- angular resolution: ~0.25 arcsec (~900 AU)  
  > "The angular resolution of the final image is $\sim 0.25$ $^{\prime\prime}$ (i.e.$\sim 900$ AU at the source distance)." (Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: point-like fragments of 0.06 Msun  
  > "We were sensitive to point-like fragments of 0.06 M$_\odot$." (Observations and data reduction)
- time on source: ~18 minutes  
  > "The total integration time on source was $\sim 18$ minutes." (Observations and data reduction)
- observing dates: southern winter 2015  
  > "Observations of I16061c1 with the ALMA array were performed during southern winter, 2015." (Observations and data reduction)
- pi or archival as stated: _not stated_
- Line: N2H+ 3-2 (not stated)
- Other facility **SEST**: 1.2 mm low-resolution single-dish flux and clump mass (Beltrán et al. 2006)  
  > "The clump was detected at 1.2 mm at low angular resolution with the Swedish-ESO Submillimeter Telescope (SEST" (Introduction)
- External data: Single-dish flux ~2.3 Jy within 24'' used to estimate recovered flux  
  > "the total flux measured with the single-dish in an area corresponding to the ALMA primary beam at the observing frequency (24$^{\prime\prime}$) is $\sim 2.3$ Jy" (Observations and data reduction) [from Beltrán et al. (cite: beltran2006)]
- External data: Gas temperature 25 K used as dust temperature  
  > "We adopted $T_{\rm d}=25$ K, corresponding to the gas temperature derived by Giannetti et al. ((cite: giannetti))" (Appendix A) [from Giannetti et al. (cite: giannetti)]
- External data: Turbulent Mach number 6.44 from C18O(3-2) line width  
  > "The amplitude of the velocity dispersion is scaled to match a turbulent Mach number of 6.44, in agreement with C$^{18}$O observations" (Appendix B) [from Fontani et al. (cite: fontani2012)]
- External data: Dust opacity kappa=0.899 at 230 GHz, beta=2  
  > "We assumed $\beta=2$ and $\kappa_{\nu_0}=0.899$ cm$^{-2}$ gr$^{-1}$ at $\nu_0 = 230$ GHz, according to Ossenkopf & Henning ((cite: oeh))." (Appendix A) [from Ossenkopf & Henning (cite: oeh)]
- Simulation/model as data: RAMSES RMHD simulations of 300 Msun, 0.25 pc core, mu=2 and mu=200, post-processed with RADMC-3D at 278 GHz and run through CASA simobserve/simanalyze  
  > "We consider an isolated spherical core of mass $300$ M$_\odot$, radius  0.25 pc and temperature 20 K." (Appendix B)

## Processing

### Calibration

- pipeline or manual: Calibration with CASA; reduction help from Italian ARC node  
  > "Calibration and imaging was performed with the CASA[^1] software (McMullin et al. 2007)" (Observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan and Ceres  
  > "The absolute flux scale was set through observations of Titan and Ceres." (Observations and data reduction)
- flux scale uncertainty: about 10%  
  > "within an uncertainty of about 10$\%$ (the calibration uncertainty on the flux density" (Discussion and conclusion)
- self calibration: _not stated_

### Imaging

- task: CASA imaging; analysis with GILDAS MAPPING  
  > "the final images were analysed following standard procedures with the software MAPPING of the GILDAS[^2] package." (Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum from averaging line-free channels  
  > "Continuum was extracted by averaging in frequency the line-free channels." (Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: ~0.25 arcsec  
  > "The angular resolution of the final image is $\sim 0.25$ $^{\prime\prime}$" (Observations and data reduction)
- final rms: _not stated_

### Inherited from earlier work

- Simulation setup follows Commerçon et al. 2011 and Hennebelle et al. 2011  
  > "The initial conditions are similar to those used in Hennebelle et al. ((cite: hennebelle)) and Commerçon et al. ((cite: commercon2011))" (Appendix B) [from Commerçon et al. (cite: commercon2011); Hennebelle et al. (cite: hennebelle)]
- Spectral fitting via PyMC and CLASS WEEDS  
  > "using a procedure based on the integration of the python module PyMC and the CLASS extension WEEDS (Maret et al. (cite: maret))" (Appendix A) [from Maret et al. (cite: maret)]

### Not stated but needed to reproduce (our reading)

- Weighting/robust, cell size, image size, clean threshold and masks
- Line-free channels and spectral setup details
- Rms noise of the final continuum image
- Self-calibration usage
- CASA version
- Exact simobserve/simanalyze parameters (e.g. pointing, mosaic, antenna list, thermal noise)
- Distance and viewing set for the synthetic fluxes, and RADMC-3D opacity settings
- Fragment identification is by eye, so not exactly reproducible
- Line-fit details for N2H+ spectra

## Analysis recipe

1. **Identify fragments in continuum map**: By eye: peak >5 sigma; overlapping fragments separate if separated at half peak level  
  > "(1) peak intensity greater than 5 times the noise level; (2) two partially overlapping fragments are considered separately if they are separate at their half peak intensity level." (Results)
   - software: GILDAS MAPPING
   - fitting: _not stated_
   - validation: Avoided Clumpfind because of sensitivity to input parameters  
  > "because small changes in their input parameters could lead to big changes in the number of identified clumps" (Results)
2. **Measure flux, size and gas mass**: Integrate within 3 sigma contour; size is equivalent-area circle diameter; mass from M = g S d^2/(kappa B(Td))  
  > "The integrated flux densities of the fragments, $S_{\nu}$, have been obtained from the 3$\sigma$ rms contour in the continuum image." (Appendix A)
   - software: GILDAS MAPPING
   - assumption: Td=25 K, gas-to-dust ratio 100, beta=2, kappa=0.899 at 230 GHz, d=3.6 kpc  
  > "$g$ is the gas-to-dust ratio (assumed to be 100)" (Appendix A)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive virial masses**: Fit N2H+(3-2) spectra averaged over each core; Mvir = 210 r dv^2  
  > "M_{\rm vir} = 210 r \Delta v^{2} \mbox{M$_\odot$}" (Appendix A)
   - software: PyMC, CLASS/WEEDS
   - fitting: Automatic fit with PyMC and WEEDS  
  > "All the spectra are fitted in an automatic way" (Appendix A)
   - validation: _not stated_
4. **Run simulations and make synthetic ALMA images**: RAMSES RMHD for mu=2 and 200; RADMC-3D 278 GHz maps; simobserve and simanalyze with the same observing parameters; snapshot chosen to match observed total flux within ~10% for mu=2  
  > "synthetic visibilities have been created with the task *simobserve*, which have then been imaged with the task *simanalyze*." (Appendix B)
   - software: RAMSES, RADMC-3D, CASA
   - parameter: 18 min, PWV 1.8 mm, C36-6, start HA 2.4 h  
  > "integration time on source of 18 minutes, precipitable water vapour of about 1.8 mm, array configuration C36-6, start hour angle of 2.4 hours" (Appendix B)
   - fitting: _not stated_
   - validation: _not stated_
5. **Compare observed and synthetic fragment populations**: Same fragment identification, cumulative peak-flux distributions, Anderson-Darling test  
  > "non-parametric statistical test (Anderson-Darling test) implies that all the $\mu$=200 cases can be excluded" (Discussion and conclusion)
   - fitting: _not stated_
   - validation: Three projections tested  
  > "we have imaged the outcome of the simulations projected on three planes: (x,y), (x,z) and (y,z)" (Discussion and conclusion)

## Software

- **CASA** : Calibration, imaging, and simobserve/simanalyze synthetic observations  
  > "Calibration and imaging was performed with the CASA[^1] software" (Observations and data reduction)
- **GILDAS MAPPING** : Analysis of final images  
  > "the final images were analysed following standard procedures with the software MAPPING of the GILDAS[^2] package." (Observations and data reduction)
- **RAMSES** : Radiation-MHD simulations  
  > "We use the RAMSES code with the grey flux-limited-diffusion approximation for radiative transfer" (Appendix B)
- **RADMC-3D** : Dust emission maps at 278 GHz  
  > "We first postprocessed the RAMSES calculations results using the radiative transfer code RADMC-3D" (Appendix B)
- **PyMC / CLASS WEEDS** : Fitting N2H+ spectra  
  > "a procedure based on the integration of the python module PyMC and the CLASS extension WEEDS" (Appendix A)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of fragments | 12 | not stated | dimensionless | 1 | This structure has been decomposed into twelve fragments |
| Mean fragment mass | 4.4 | not stated | Msun | 2 | The mean mass of the fragments turns out to be 4.4 M$_\odot$ |
| Fraction of single-dish flux recovered | ~30% | not stated | percent | 0 | Thus, we recover $\sim 30\%$ of the total flux. |
| Mean Mvir/M | ~0.4 | factor 2-3 from opacity | dimensionless | 3 | The average ratio between $M_{\rm vir}$ and $M$ computed from the continuum emission is about 0.4 |
| Number of fragments in synthetic maps mu=2 (x,y), (x,z), (y,z) | 12, 12, 8 | not stated | dimensionless | 4 | / $\mu=2$ (y,z) / 0.46 / 42 / 8 / 0.018 / 0.050 / 5.2 / |
| Number of fragments in synthetic maps mu=200 | 13, 15, 16 | not stated | dimensionless | 4 | / $\mu=200$ (y,z) / 0.28 / 24 / 16 / 0.016 / 0.021 / 2.19 / |
| Sink particles formed | 38 (mu=2), 119 (mu=200) | not stated | dimensionless | 4 | model $\mu$=2 has formed 38 sink particles (for a total mass of 60 M$_\odot$) while model $\mu$=200 has formed 119 sink particles |

## Qualitative findings

- ALMA continuum shows a filamentary east-west chain of condensations, matching mu=2 morphology; mu=200 is chaotic and never filamentary  
  > "we have detected several dense condensations distributed in a filamentary-like structure extended east-west" (Results)

## Claim tuples

- H: Fragmentation of I16061c1 is regulated by magnetic support | E: Compare ALMA fragment population with RMHD synthetic ALMA images for mu=2 and mu=200 | R: mu=200 excluded at >99.8% by Anderson-Darling; mu=2 not excluded in the (y,z) projection; mu=2 is filamentary like the data | F: Strong magnetic support (mu=2) best reproduces the data | **supported**
- H: Fragments are gravitationally unstable | E: Virial masses from N2H+ line widths versus continuum masses | R: Mvir/M ~0.4 without magnetic support; ~1 with 0.27 mG | F: Gravity appears to dominate but the fragments are marginally stable if magnetic support is included; inconclusive | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Fragments identified by eye rather than with algorithms to avoid sensitivity to input parameters  
  > "We decided to use these criteria and decompose the map into cores by eye instead of using decomposition algorithms" (Results)
- Alternative: Clumpfind-type decomposition rejected  
  > "instead of using decomposition algorithms (such as Clumpfind)" (Results)
- How they decided it was enough: _not stated_
- Limitation (authors): Only one turbulence realisation explored; simulations not fine-tuned; deficit of very weak and strong peaks in the data may reflect density profile or temperature assumptions  
  > "only one realisation is explored" (Appendix B)
- Limitation (authors): Mass uncertainty from dust opacity of factor 2-3  
  > "the uncertainties due to the dust mass opacity coefficient (see Eq. [\[mass_dust\]](#mass_dust)) can be of a factor 2-3" (Results)
- Caveat (inferred, ours): Single turbulence seed and only two mu values
- Caveat (inferred, ours): Only ~30% of flux recovered, and a resolved-out envelope affects the comparison
- Caveat (inferred, ours): Snapshot time for mu=2 chosen by matching flux
- Caveat (inferred, ours): By-eye identification and a single observed region
- Caveat (inferred, ours): Small samples with an Anderson-Darling test
- Caveat (inferred, ours): Uniform 25 K dust temperature versus 20 K in the simulations

## Reproducibility

- Data public (paper): Project 2012.1.00366.S cited in acknowledgements  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA.2012.1.00366.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: RAMSES model snapshots and setup files
- Missing: Details of the by-eye fragment selection
- Data volume (inferred): ~10-50 GB for one Band 7 continuum+line project
- Score (inferred): 3/5, Data are public and the analysis is simple, but imaging parameters and simulation outputs are missing.
- Rediscovery candidate: no, The key comparison needs simulations that are not provided and the imaging recipe is incomplete; the observed fragment table is reproducible only partly.

## Links

- Method: Commerçon et al. 2011 (cite: commercon2011) (Simulation approach and the mu parameter)
- Method: Maret et al. 2011 (cite: maret) (WEEDS spectral fitting)
- Companion: forthcoming paper on the line data (Will present the other detected lines)

## Checks

```json
{
 "quotes": 61,
 "quotes_ok": 61,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 46,
  "rate": 0.597
 },
 "evidence_ok": true
}
```
