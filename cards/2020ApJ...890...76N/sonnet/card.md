# ALMA Observations of Two Massive and Dense MALT90 Clumps

`2020ApJ...890...76N` | The Astrophysical Journal 2020 | first author: Neupane, Sudeep | arXiv: 2001.02227 | DOI: 10.3847/1538-4357/ab67c9

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism
- Question: How do massive and dense clumps in prestellar and protostellar phases fragment into cores, and what are the cores' physical and kinematic properties?  
  > "made with the goal of investigating their fragmentation characteristics at angular scales of $\sim$1$\ensuremath{''}$." (abstract)
- Target **AGAL333.014-0.521 (prestellar)**: coordinates _not stated_; z/distance 3.72 kpc  
  > "| Distance (kpc) | 3.72 | 3.46 | \(2\) |" (Table 1); distance from reference (2) in Table 1, not identified in the text  
  > "| Distance (kpc) | 3.72 | 3.46 | \(2\) |" (Table 1)
- Target **AGAL329.184-0.314 (protostellar)**: coordinates _not stated_; z/distance 3.46 kpc  
  > "| Distance (kpc) | 3.72 | 3.46 | \(2\) |" (Table 1); distance from reference (2) in Table 1, not identified in the text  
  > "| Distance (kpc) | 3.72 | 3.46 | \(2\) |" (Table 1)

## Data provenance

- ALMA projects: 2016.1.00645.S
- bands: Band 3 (86-116 GHz)  
  > "We made ALMA Band 3 (86-116 GHz) dust continuum and molecular line observations towards the MDCs AGAL333 and AGAL329." (3 Observations)
- frequencies and spectral setup: Two setups: N2H+, CH3CN and 3 continuum SPWs; HCO+, H13CO+ and 2 continuum SPWs. Line SPWs 117.19 MHz wide; continuum SPWs 1875 MHz wide  
  > "In the first one, five separate spectral windows (SPW) were used, three for continuum observations and two for observations of the N$_{2}$H$^{+}$J=1$\rightarrow$0 and CH$_{3}$CN J=5$\rightarrow$4 lines." (3 Observations)
- continuum bandwidth: _not stated_
- arrays: 12 m array and 7 m ACA, single pointing  
  > "single pointing observations were carried out, as part of Cycle 4, during Dec 2016 and Jan 2017 using both the 12 m array and 7m Atacama Compact Array (ACA)." (3 Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.46"x1.34" (PA 155°) for AGAL329; 1.46"x1.33" (PA 138°) for AGAL333 in continuum  
  > "The angular resolution achieved in the continuum observations are 1.46$\ensuremath{''}\times1.34\ensuremath{''}$ (P.A. 155$\ensuremath{^\circ}$)" (3 Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 23 and 32 min per setup (the paper's assignment of the two times to arrays is internally inconsistent)  
  > "The integration time on source in each of the setups was 23 and 32 minutes for the 7m and 12m array observations, respectively." (3 Observations)
- observing dates: Dec 2016 and Jan 2017 (Cycle 4)  
  > "during Dec 2016 and Jan 2017" (3 Observations)
- pi or archival as stated: _not stated_
- Line: N2H+ J=1-0 (93173.402 MHz (SPW center))
- Line: CH3CN J=5-4 (91985.284 MHz (SPW center))
- Line: HCO+ J=1-0 (89188.526 MHz)
- Line: H13CO+ J=1-0 (86754.288 MHz)
- Other facility **Herschel Hi-GAL**: 70-500 um fluxes for the clump SEDs  
  > "The data points at infrared wavelengths (70 to 500 $\mu$m; red circles) were obtained from the Hi-Gal images ((cite: hershel)) available in the Herschel Science Archive" (2 The targets)
- Other facility **ATLASGAL**: 850 um flux, used for clump size, mass and density  
  > "the data point at 850 $\mu$m (black square) was obtained from ATLASGAL images ((cite: Schuller))." (2 The targets)
- Other facility **MOPRA / MALT90**: Clump classification, Vlsr and line widths from N2H+ hyperfine fits  
  > "The velocities and line widths correspond to those determined from the hyperfine fitting of the N$_{2}$H$^{+}$ emission as observed with the MOPRA telescope in the MALT90 survey." (2 The targets)
- Other facility **ATCA**: 18 and 22 GHz flux densities used to subtract free-free emission from the central AGAL329 core  
  > "The latter was determined from an extrapolation of the observed flux densities at 18 GHz and 22 GHz ((cite: sanchez-monge2013))." (4.3.3 Masses)
- External data: 1.2 mm flux density of the protostellar clump  
  > "for the protostellar clump the 1.2 mm flux density reported by (cite: Beltran2006) (open square)" (2 The targets) [from (cite: Beltran2006)]
- External data: Cores in the AGAL305 prestellar clump, added to the CMF sample  
  > "including, in addition, the cores detected by (cite: Servajean2019) towards the prestellar clump (AGAL305)" (4.4 Mass distribution) [from (cite: Servajean2019)]
- External data: Dust opacity 0.21 cm2/g at 100 GHz (ice mantles, 10^6 cm^-3)  
  > "$k_{100 GHz}$ = 0.21 cm$^{2}$ g$^{-1}$ corresponding to the dust grains with ice mantles at gas densities of 10$^{6}$ cm$^{-3}$ ((cite: Ossenkopf1994))" (4.1.3 Masses) [from (cite: Ossenkopf1994)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.7  
  > "Data calibration and reduction were made using the Common Astronomy Software Application (CASA: (cite: casa2007)) version 4.7 package." (3 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Mars and Callisto, plus multiple quasars for bandpass and flux  
  > "The bandpass and flux calibrations were carried out using multiple quasars" (3 Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA tclean, 12m and 7m concatenated and cleaned together  
  > "Independently calibrated 12m and 7m dataset were concatenated and cleaned together using the CASA *tclean* task with a Briggs weighting of 0.5." (3 Observations)
- deconvolver: multi-scale  
  > "We used a *multi-scale* clean deconvolver ((cite: cornwell2008))" (3 Observations)
- weighting robust: Briggs 0.5  
  > "with a Briggs weighting of 0.5" (3 Observations)
- uv taper: _not stated_
- cell size: 0.3"  
  > "image pixel size (0.3$\ensuremath{''}$)" (3 Observations)
- image size: _not stated_
- masking: Interactive for continuum; auto-multithresh with noisethreshold 2 sigma for cubes  
  > "We used interactive mode for continuum imaging while spectral cubes were made using continuum subtracted spectra with automated masking procedure *auto-multithresh* using noise threshold parameter *noisethreshold* of 2 sigma." (Observations)
- multiscale scales: 0, 6, 10, 30 times the pixel size  
  > "with scale values of 0, 6, 10 and 30 times the image pixel size" (3 Observations)
- continuum subtraction: Cubes made from continuum-subtracted spectra; method not stated  
  > "spectral cubes were made using continuum subtracted spectra" (3 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12m and 7m concatenated  
  > "Independently calibrated 12m and 7m dataset were concatenated" (3 Observations)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: Continuum 0.085 mJy/beam (AGAL329), 0.047 mJy/beam (AGAL333); lines 3.7-4.0 mJy/beam  
  > "Continuum        |   | 8.5$\times 10^{-2}$ | 1.5 x 1.3" (Table 3)

### Inherited from earlier work

- Single-temperature modified blackbody SED model  
  > "using a single temperature modified blackbody model (c.f., (cite: Guzman2015; konig2017))" (2 The targets) [from (cite: Guzman2015; konig2017)]
- Uncertainty in core mass (~40%) estimated following earlier work  
  > "The uncertainties in the mass are estimated to be $\sim$40%, considering errors in the flux density, temperature, distance and dust mass absorption coefficient (c.f., (cite: Sanhueza2017))." (4.1.3 Masses) [from (cite: Sanhueza2017)]

### Not stated but needed to reproduce (our reading)

- Line-free channels used for continuum subtraction
- Cleaning thresholds and number of iterations
- Continuum subtraction method for the cubes
- Primary-beam correction details
- Exact assignment of the 23 and 32 min between 12m and 7m
- Flux scale uncertainty
- Which quasar calibrates which dataset
- Astrodendro and Clumpfind implementation details beyond the thresholds
- Fit ranges for the rotational diagrams and for the CMF
- Parameters of the Hill5 fit
- How the SED flux apertures and backgrounds were handled

## Analysis recipe

1. **Fit clump SEDs for dust temperature and beta**: Aperture photometry on Herschel and ATLASGAL images; least-squares fit of a modified blackbody to the SED  
  > "A least squares fit to the SED, using the SciPy optimize module in Python ((cite: scipy2019)), gave values of T$_d$ and $\beta$ of 22 K and 2.1 for the prestellar clump" (2 The targets)
   - software: SciPy
   - parameter: Apertures of 27" (prestellar) and 20" (protostellar) radius  
  > "circular region with radii of 27$\ensuremath{''}$ and 20$\ensuremath{''}$ for the prestellar and protostellar clumps, respectively" (2 The targets)
   - assumption: Gas-to-dust ratio 100; kappa 1.85 cm2/g  
  > "a dust absorption coefficient of 1.85 cm$^{2}$ gr$^{-1}$ ((cite: Ossenkopf1994)), and a gas to dust ratio of 100" (2 The targets)
   - fitting: Least squares; no priors  
  > "A least squares fit to the SED, using the SciPy optimize module in Python ((cite: scipy2019)), gave values of T$_d$ and $\beta$ of 22 K and 2.1 for the prestellar clump" (The targets)
   - validation: _not stated_
2. **Identify cores in the 3 mm continuum**: Astrodendro and Clumpfind; Clumpfind parameters adopted  
  > "Given the similarities, in the remaining of this paper we will use the parameters of the cores determined from the Clumpfind method" (4.2 Continuum emission)
   - software: Astrodendro, Clumpfind
   - parameter: Astrodendro: Fmin=3 sigma, delta=1 sigma, Amin=1 beam  
  > "we adopted F$_{min}$=3$\sigma$, $\delta$=1$\sigma$ and A$_{min}$ = 1 beam." (Continuum emission)
   - parameter: Clumpfind: Tlow=3 sigma, dT=2 sigma, Smin=1 beam  
  > "we adopted T$_{low}$=3$\sigma$, $\Delta$T=2$\sigma$ and S$_{min}$ = 1 beam." (Continuum emission)
   - fitting: _not stated_
   - validation: Compared the two algorithms; fluxes and sizes similar  
  > "We find that the flux densities and angular sizes of the structures (cores) obtained from both methods are similar." (Continuum emission)
3. **Fit core line spectra for velocity, width and optical depth**: Hyperfine fit of N2H+ with pyspeckit; Gaussian fit to H13CO+; Gaussian or two components for complex cores  
  > "The red line shows the result of a simultaneous fit to the emission from the whole hyperfine structure for a single velocity component, made using the task *pyspeckit.models* in *PySpecKit*" (Line emission from cores)
   - software: PySpecKit
   - fitting: Least-squares line fits  
  > "From a least squares fit to the data we derived the rotational temperatures given in column 8 of Table [\[tab:Trot\]]" (Analysis and discussion, Temperatures)
   - validation: N2H+ and H13CO+ velocities and widths agree  
  > "the velocities and line widths of the cores derived from both lines are in good agreement" (Line emission from cores)
4. **Derive CH3CN rotational temperatures and column densities**: Rotational diagram, least-squares fit to K=0-4 lines of J=5-4  
  > "We use the standard rotational diagram analysis ( (cite: Turner1991; Sutton1995)) which assumes that the lines are optically thin and that the population levels are characterized by a single excitation temperature (LTE assumption)." (4.1.2 Temperatures)
   - parameter: Cores with at least three K lines above 3 sigma  
  > "for which at least three lines in the 5$_K$ - 4$_K$ K-ladder were detected above the 3$\sigma$ level" (4.1.2 Temperatures)
   - assumption: LTE, optically thin; Q(T) from Araya2005  
  > "Q(T_{rot}) = 3.89 ~ \frac{T_{rot}^{1.5}}{(1-e^{-524.8/T_{rot}} )^2}" (4.1.2 Temperatures)
   - fitting: _not stated_
   - validation: Optical-depth-corrected diagram gives differences within errors  
  > "the differences in the derived temperatures and column densities are well within the errors determined from the “traditional" approach" (4.1.2 Temperatures)
5. **Compute core masses, column densities, virial parameters**: Optically thin dust mass from 3 mm flux with Trot (clump T otherwise); alpha_vir=Mvir/M with Mvir=5 sigma^2 R/G  
  > "For cores in which no rotational temperature is available we adopted the temperature of the clump." (4.1.3 Masses)
   - parameter: Core radius from geometric mean of Clumpfind semi-axes  
  > "The radius of the cores were computed from the geometric mean of the semi-major and minor axis determined from Clumpfind" (4.1.1 Sizes)
   - assumption: Rgd=100; k100GHz=0.21 cm2/g; mu_H2=2.8; virial equilibrium for 0.71<alpha<1.4  
  > "We assume $R_{gd}$=100 and $k_{100 GHz}$ = 0.21 cm$^{2}$ g$^{-1}$" (4.1.3 Masses)
   - fitting: _not stated_
   - validation: Mass uncertainty ~40%, column density ~35%  
  > "The uncertainties in the mass are estimated to be $\sim$40%" (4.1.3 Masses)
6. **Fit the core mass function**: Maximum likelihood power-law fit to the eCDF of the combined core sample (AGAL329, AGAL333, AGAL305)  
  > "the value of the $\alpha$ index that best reproduces the eCDF, using the maximum likelihood estimator (MLE) method, is $-1.33\pm$0.15" (4.2 Mass distribution)
   - parameter: Mass limits 0.9, 0.7, 1.4 Msun (3 sigma flux at clump temperature)  
  > "The mass sensitivity limits are 0.9, 0.7 and 1.4 M$_{\odot}$ for AGAL329, AGAL333 and AGAL305, respectively." (4.2 Mass distribution)
   - fitting: MLE of a power law dN/dM ∝ M^alpha  
  > "Assuming that the core mass function (CMF) can be described by a power-law $dN/dM$ $\propto$ $M^{\alpha}$, the value of the $\alpha$ index that best reproduces the eCDF, using the maximum likelihood estimator (MLE) method" (Mass distribution)
   - validation: 90% confidence interval -1.58 to -1.08  
  > "the 90% confidence interval is $-1.58$ to $-1.08$" (4.2 Mass distribution)
7. **Infall model fit for the central AGAL329 core**: Fit HCO+ spectrum with Hill5 infall model of De Vries & Myers; mass infall rate from 4 pi R^2 n mu mH v_in  
  > "To estimate the infall velocity we fitted the observed HCO$^{+}$ core spectrum with analytical infall models presented by (cite: Devries2005)." (4.5 The massive core)
   - fitting: _not stated_
   - validation: None of the simple models reproduces the deep absorption  
  > "We note that none of the simple models is able to reproduce the observed deep absorption feature (reaching zero intensity)." (4.5 The massive core)

## Software

- **CASA** 4.7: Calibration, tclean imaging, immoments  
  > "Data calibration and reduction were made using the Common Astronomy Software Application (CASA: (cite: casa2007)) version 4.7 package." (3 Observations)
- **Astrodendro** : Core identification  
  > "we used two commonly employed methods: *Astrodendro[^3]* and *Clumpfind*" (Continuum emission)
- **Clumpfind** : Core identification and parameters  
  > "we used two commonly employed methods: *Astrodendro[^3]* and *Clumpfind*" (Continuum emission)
- **PySpecKit** : N2H+ hyperfine fits  
  > "made using the task *pyspeckit.models* in *PySpecKit*" (Line emission from cores)
- **SciPy** : Least-squares SED fit  
  > "using the SciPy optimize module in Python ((cite: scipy2019))" (2 The targets)
- **GILDAS/CLASS** : Named in the software list; use not specified  
  > "GILDAS/CLASS ((cite: pety2005gildas; Gildas2013))" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of cores in AGAL333 (Clumpfind) | 10 | not stated | dimensionless | 2 | / Number of cores / 10 / 10 / |
| Mass of central core mm-6 in AGAL329 | 119 | ~40% | Msun | 5 | we detected a massive (119 M$_\odot$) central core |
| Core-to-clump mass fraction, prestellar | 0.06 | not stated | dimensionless | 5 | / $f$($\Sigma$M$_{cores}$/M$_{clump}$) / 0.06 / 0.23 / |
| Core-to-clump mass fraction, protostellar | 0.23 | not stated | dimensionless | 5 | / $f$($\Sigma$M$_{cores}$/M$_{clump}$) / 0.06 / 0.23 / |
| CMF power-law index | -1.33 | 0.15 | dimensionless | 6 | is $-1.33\pm$0.15, and the 90% confidence interval is $-1.58$ to $-1.08$ |
| Infall velocity of core mm-6 (Hill5) | 1.6 | not stated | km/s | 7 | indicating an infall velocity, $v_{in}$, of 1.6 km s$^{-1}$ |
| Mass infall rate of core mm-6 | 1.9e-2 | not stated | Msun/yr | 7 | of 1.9$\times$10$^{-2}$ M$_{\odot}$/yr |
| CH3CN Trot at the AGAL329 mm-6 peak (inner 1") | 131 | 24 | K | 4 | The rotational temperature decreases from 131$\pm$24 K at the peak position to 30$\pm$3 K |
| Power-law index of Trot profile | -0.8 | 0.2 | dimensionless | 4 | give power law indices of $-0.8\pm0.2$ and $-2.0\pm0.4$, respectively |
| Plummer index p of mm-6 radial profile | 2.2 | 0.1 | dimensionless | 0 | indicates a power law index $p$ of 2.2$\pm$0.1 and R$_0$ of 0.95$\pm$0.05$''$ |
| Mean N2H+ line width of cores, AGAL333 vs AGAL329 | 1.2 vs 2.0 | not stated | km/s | 3 | The average line width of the cores within AGAL333 and AGAL329 are 1.2 km s$^{-1}$ and 2.0 km s$^{-1}$, respectively. |
| Clump dust temperature and beta, prestellar | 22 K, 2.1 | not stated | K, dimensionless | 1 | gave values of T$_d$ and $\beta$ of 22 K and 2.1 for the prestellar clump and 28 K and 1.6 for the protostellar clump |

## Qualitative findings

- Fragmentation is inefficient: about 10 cores per clump versus about 160 Jeans masses  
  > "showing that fragmentation is not efficient during the early stages of evolution" (4.2 Mass distribution)
- Protostellar-clump cores are warmer, with larger linewidths, than prestellar-clump cores  
  > "Cores within the prestellar clump have smaller linewidths and lower temperatures than cores within the protostellar clump." (abstract)

## Claim tuples

- H: Prestellar-clump cores are individually collapsing | E: HCO+ profiles and virial parameters of the cores | R: Five of ten cores show inverse P Cygni profiles; five are sub-virial | F: Cores in the prestellar clump are undergoing collapse | **supported**
- H: The central protostellar-clump core is accreting from global collapse | E: Hill5 fit to HCO+, Plummer profile fit, virial analysis | R: Infall 1.6 km/s, infall rate 1.9e-2 Msun/yr, alpha_vir 0.71 | F: Large-scale collapse feeds the massive core | **supported**
- H: Core mass fraction increases with evolution | E: Sum of core masses over clump mass | R: ~6% vs ~23% | F: The protostellar clump has gathered more gas into cores, consistent with accretion | **supported**
- H: The CMF in early clump fragmentation is top-heavy | E: MLE fit to the eCDF of 3 clumps | R: alpha = -1.33 ± 0.15 | F: High-mass cores form more efficiently than low-mass cores | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: eCDF preferred over the differential CMF to avoid binning bias  
  > "We prefer to use the eCDF over the differential form of the core mass function because the later approach contains the numerical bias introduced by binning." (4.2 Mass distribution)
- How they decided it was enough: _not stated_
- Limitation (authors): Simple infall models fail to reproduce the deep HCO+ absorption  
  > "To reproduce it requires a more sophisticated modeling, which is beyond the scope of this work." (4.5 The massive core)
- Caveat (inferred, ours): Only two clumps, so the evolutionary-sequence conclusion rests on a sample of two
- Caveat (inferred, ours): Core temperatures often fall back on the clump temperature, which feeds into masses
- Caveat (inferred, ours): Core extraction depends on the algorithm and on a 3 sigma threshold
- Caveat (inferred, ours): Interferometric filtering of extended emission is not discussed
- Caveat (inferred, ours): CMF sample includes AGAL305 from different observations

## Reproducibility

- Data public (paper): ALMA project 2016.1.00645.S cited; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00645.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Clean thresholds and iteration counts
- Missing: Line-free channels
- Missing: Rotational diagram fit details
- Missing: Hill5 fit settings
- Missing: Exact SED photometry procedure
- Data volume (inferred): ~10-50 GB raw 12m+ACA Band 3 data for two fields
- Score (inferred): 3/5, Data are tied to a project code and the imaging settings are fairly detailed, but line-free channels, clean thresholds and fit settings are missing.
- Rediscovery candidate: no, Public status is not stated and several steps (core definitions, fits, SED photometry) are under-specified.

## Links

- Method: (cite: Devries2005) (Hill5 infall model)
- Method: (cite: Rosolowsky2008) (Dendrogram algorithm)
- Method: (cite: clumpfind) (Clumpfind algorithm)
- Companion: (cite: Servajean2019) (AGAL305 cores added to the CMF sample)
- Companion: (cite: Csengeri2017) (Comparison sample of infrared-quiet MDCs)
- Related: MALT90
- Related: ATLASGAL
- Related: Hi-GAL

## Checks

```json
{
 "quotes": 89,
 "quotes_ok": 89,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 94,
  "stated": 67,
  "rate": 0.713
 },
 "evidence_ok": true
}
```
