# GA-NIFS: Multiphase analysis of a star-forming galaxy at z ∼ 5.5

`2025A&A...695A...6P` | Astronomy and Astrophysics 2025 | first author: Parlanti, Eleonora | arXiv: 2407.19008 | DOI: 10.1051/0004-6361/202451692

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies
- Question: What are the kinematics, ISM conditions, stellar populations and outflow properties of HZ4 (z~5.5) from JWST/NIRSpec IFS, and how do ionized and neutral ([CII]) outflow phases compare?  
  > "we present a detailed multiphase analysis of HZ4, a main-sequence star-forming galaxy at $z \sim 5.5$" (abstract)
- Target **HZ4 (DEIMOS_COSMOS_494057)**: coordinates RA = 09h58m28.5s, Dec = +02d03m06.7s  
  > "we focus on HZ4 (RA = 09h58m28.5s, Dec= +02d03m06.7s)" (1 Introduction); "we estimated a redshift of $5.54455 \pm 0.00002$ for the galaxy" (3.1 Spectral fitting of the R2700 cube); z/distance z = 5.54455 ± 0.00002  
  > "we focus on HZ4 (RA = 09h58m28.5s, Dec= +02d03m06.7s)" (1 Introduction); "we estimated a redshift of $5.54455 \pm 0.00002$ for the galaxy" (3.1 Spectral fitting of the R2700 cube); distance from narrow-component lines in NIRSpec R2700 spectrum  
  > "we focus on HZ4 (RA = 09h58m28.5s, Dec= +02d03m06.7s)" (1 Introduction); "we estimated a redshift of $5.54455 \pm 0.00002$ for the galaxy" (3.1 Spectral fitting of the R2700 cube)

## Data provenance

- ALMA projects: 2012.1.00523.S, 2017.1.00428.L, 2018.1.01605.S
- bands: Band 7  
  > "The source was observed for $\sim 20$ min, $\sim 30$ min, and 4.7 h, respectively, in Band 7." (2.2 ALMA data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.33''x0.29'' (robust 0.5), 0.45''x0.41'' (robust 2); continuum 0.46''x0.41''  
  > "The resulting datacubes have a beam size of $0.33\ensuremath{''} \times0.29\ensuremath{''}$, and $0.45\ensuremath{''} \times0.41\ensuremath{''}$, respectively." (2.2 ALMA data)
- max recoverable scale: _not stated_
- sensitivity: continuum 6 µJy/beam  
  > "a sensitivity of 6 $\mu$Jy/beam" (2.2 ALMA data)
- time on source: ~20 min, ~30 min, 4.7 h for the three projects  
  > "The source was observed for $\sim 20$ min, $\sim 30$ min, and 4.7 h, respectively, in Band 7." (2.2 ALMA data)
- observing dates: _not stated_
- pi or archival as stated: Archival; PIs Capak, Le Fevre, Herrera-Camus  
  > "The \[C\] raw data were retrieved from the ALMA archive" (2.2 ALMA data)
- Line: [CII] 158 µm (not stated)
- Other facility **JWST/NIRSpec IFS (GA-NIFS, program 1217)**: G395H R2700 and PRISM R100 cubes; optical/UV lines and continuum  
  > "The galaxy was observed in the Integral field spectroscopy (IFS) mode" (2.1 JWST data)
- Other facility **HST/WFC3 F160W**: Image used for astrometric registration  
  > "we retrieved the F160W images of HST/WFC3 (PID: 13641) from the MAST archive" (2.3 Astrometric registration)
- External data: SFR_UV = 29±4 Msun/yr, FIR band 6 and 8 fluxes, T_D=57.3 K  
  > "(cite: Faisst:2020_dusttemp) report $\rm SFR_{UV} = 29\pm4$ M${_\odot}$ yr$^{-1}$ exploiting the UV HST observations" (6.2 Dust continuum emission) [from (cite: Faisst:2020_dusttemp)]
- External data: k_[CII]=4.88 Msun/Lsun for maximal excitation  
  > "the case for maximal excitation gives $k_{[CII]}=4.88 ~M_\odot/L_\odot$ (cite: Herrera-Camus:2021)" (8.2 Neutral outflow properties) [from (cite: Herrera-Camus:2021)]
- External data: alpha_[CII]=31 Msun/Lsun  
  > "We adopt $\alpha_{\rm [CII]} = 31 ~M_\odot/L_\odot$ (cite: Zanella:2018)" (8.3 Outflow strength) [from (cite: Zanella:2018)]
- Simulation/model as data: MAPPINGS III shock models (n=100, 1000 cm^-3, 200-1000 km/s) overplotted on BPT  
  > "we over plot the MAPPINGS III shock-ionization models (cite: Allen:2008) with densities of $n=100$ and 1000 cm$^{-3}$" (4.2 Spaxel-by-spaxel R2700 results)

## Processing

### Calibration

- pipeline or manual: Dataset calibration script, then CRISTAL reduction pipeline  
  > "calibrate the *uv* visibilities by using the script included in the dataset" (2.2 ALMA data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "the task `tclean` is run with a Briggs weighting (robust parameter = 0.5 and 2), `hogbom` deconvolver" (2.2 ALMA data)
- deconvolver: hogbom  
  > "the task `tclean` is run with a Briggs weighting (robust parameter = 0.5 and 2), `hogbom` deconvolver" (2.2 ALMA data)
- weighting robust: Briggs robust = 0.5 and 2  
  > "Briggs weighting (robust parameter = 0.5 and 2)" (2.2 ALMA data)
- uv taper: _not stated_
- cell size: 0.0445''  
  > "a spaxel scale of 0.0445$''$" (2.2 ALMA data)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub in visibility space  
  > "the continuum emission is subtracted in the visibility space using the task `uvcontsub`" (2.2 ALMA data)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.33''x0.29'' and 0.45''x0.41''  
  > "The resulting datacubes have a beam size of $0.33\ensuremath{''} \times0.29\ensuremath{''}$, and $0.45\ensuremath{''} \times0.41\ensuremath{''}$, respectively." (2.2 ALMA data)
- final rms: _not stated_

### Inherited from earlier work

- ALMA reduction via CRISTAL pipeline  
  > "The measurement sets were then processed with CRISTAL’s reduction pipeline" (2.2 ALMA data) [from (cite: posses:2024; Solimano:2024_ALMA; Villanueva:2024); Herrera-Camus et al. in prep.]
- Broad/narrow two-Gaussian constraints  
  > "and we imposed the amplitude of the broad component to be lower than 50% of the narrow one, following (cite: Carniani:2023)." (3.1 Spectral fitting of the R2700 cube) [from (cite: Carniani:2023)]
- JWST pipeline customised code  
  > "we used some customized code to improve the quality of the final data (cite: Perna:2023)" (2.1 JWST data) [from (cite: Perna:2023)]
- Escape velocity approach  
  > "We followed the same approach as in (cite: Carniani:2023)." (8.3 Outflow strength) [from (cite: Carniani:2023)]

### Not stated but needed to reproduce (our reading)

- CASA version used for ALMA calibration/imaging
- line-free channels and uvcontsub fit order
- clean threshold, masks and iterations
- primary-beam correction and flux-scale uncertainty
- how [CII] outflow luminosity was integrated (apertures)
- inclination/line-of-sight details of the ALMA continuum SED fit
- exact aperture definitions for northern/central/southern components

## Analysis recipe

1. **Fit integrated NIRSpec R2700 spectrum**: Power-law continuum plus narrow and broad Gaussian per line; BIC test for 2 vs 1 components  
  > "We fitted the integrated spectrum by modeling it with the sum of a power-law continuum and two Gaussian components for each line, one narrow and one broad." (3.1 Spectral fitting of the R2700 cube)
   - parameter: narrow sigma 0-250 km/s; broad width at least 20% larger; broad amplitude <50% of narrow  
  > "the broader component was constrained to have a line width larger by at least 20% than the narrow one" (3.1 Spectral fitting of the R2700 cube)
   - assumption: [OIII]5007/4959=2.98, [NII]6584/6548=2.94  
  > "\[O\]$\lambda$5007/\[O\]$\lambda4959 = 2.98$ and \[N\]$\lambda$6584/\[N\]$\lambda6548 = 2.94$" (3.1 Spectral fitting of the R2700 cube)
   - fitting: _not stated_
   - validation: ΔBIC>10 favours two components  
  > "highly favors the two components model with $\Delta \rm BIC = \rm BIC_1 - BIC_2  > 10$" (3.1 Spectral fitting of the R2700 cube)
2. **Dust attenuation, SFR, density, metallicity**: Balmer decrement with Calzetti law; Kennicutt&Evans Halpha SFR; [SII] ratio density; Curti strong-line calibrations  
  > "Assuming the (cite: Calzetti:2000) attenuation law ($R_V$ = 4.05), we estimated the dust attenuation of the source from the measured Balmer decrement." (3.1 Spectral fitting of the R2700 cube)
   - assumption: Case B Halpha/Hbeta=2.86  
  > "the theoretical ratio between the H$\alpha$ and H$\beta$ fluxes is $\rm F_{H\alpha}/F_{H\beta}= 2.86$" (3.1 Spectral fitting of the R2700 cube)
   - fitting: _not stated_
   - validation: R100 fluxes compared with R2700  
  > "This demonstrates that the flux calibration largely agrees between the two cubes." (3.2 Spectral fitting of the R100 cube)
3. **Spaxel-by-spaxel JWST fitting, BPT diagnostics**: One vs two Gaussians per spaxel selected by BIC; S/N>3; BPT/VO87 with shock models  
  > "selecting the model with two components for each line only when $\rm BIC_1 - BIC_2 > 10$" (4.2 Spaxel-by-spaxel R2700 results)
   - software: MAPPINGS III
   - fitting: _not stated_
   - validation: _not stated_
4. **SED fitting of PRISM spectra**: Bagpipes with BC03, Cloudy nebular, Calzetti, nonparametric continuity SFH with 10 bins  
  > "we adopt a so-called nonparametric SFH, with continuity priors (cite: Leja:2019) with 10 bins logarithmically spaced" (5 SED fitting)
   - software: Bagpipes, Cloudy
   - parameter: -3<logU<0; A_V 0-4; Z 0.1-1 Zsun  
  > "with $A_V$ free to vary between 0 and 4" (5 SED fitting)
   - fitting: Bagpipes (sampler not stated)  
  > "We used the SED fitting code `Bagpipes` (cite: Carnall:2018)." (SED fitting)
   - validation: _not stated_
5. **Spaxel-wise [CII] fit and dust continuum**: One or two Gaussians plus constant per spaxel on natural-weighted cube; two components if ΔBIC>5 and S/N>3 each  
  > "we selected the 2-component model only when $\rm BIC_1 - BIC_2 > 5$ and the S/N of both the narrow and the broad component were greater than 3" (6 ALMA analysis)
   - software: CASA
   - fitting: _not stated_
   - validation: Residuals vanish with 2 components in example spaxel; ΔBIC=14  
  > "The 2-component model is favored by the BIC test, with a $\rm \Delta BIC = 14$." (6.1 [CII] spaxel-by-spaxel results)
6. **Outflow masses, rates, energetics**: Halpha and [OIII] mass formulae; v_out=|Δv|+2σ; Mdot=vM/R; [CII] mass with k_[CII]; eta=Mdot/SFR  
  > "$$\begin{equation}
\label{eq:outflowrate}
    \Dot{M}_{\rm out} = \frac{v_{{\rm out}}M_{{\rm out}}}{R_{\rm out}},
\end{equation}$$" (8.1 Ionized outflow properties)
   - parameter: n_e=200 cm^-3, Z=0.5 Zsun, R_out~2 kpc (ionized), 1.3 kpc (neutral)  
  > "We assume $n_e$ = 200 cm$^{-3}$" (8.1 Ionized outflow properties)
   - assumption: [CII] k at T=1e4 K, n_H=1e4 cm^-3 (lower limit)  
  > "assuming $T = 10^4$ K and $n_H=10^4$ cm$^{-3}$, which correspond to the maximal excitation case" (8.2 Neutral outflow properties)
   - fitting: _not stated_
   - validation: _not stated_
7. **FIR SED fit for dust temperature and mass**: Single-temperature gray-body, beta=2, with L_IR fixed from obscured Halpha SFR  
  > "a dust emissivity index of $\beta = 2$, and we performed a fit assuming a gray-body curve with a single temperature" (6.2 Dust continuum emission)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Combine and calibrate ALMA data, uvcontsub, tclean  
  > "We used `CASA` (cite: Mcmullin:2007) to combine these three observations" (2.2 ALMA data)
- **JWST pipeline** 1.11.1: Reduce NIRSpec data (CRDS jwst_1097.pmap)  
  > "we processed them with the JWST pipeline version 1.11.1" (2.1 JWST data)
- **Bagpipes** : SED fitting  
  > "We used the SED fitting code `Bagpipes` (cite: Carnall:2018)." (5 SED fitting)
- **Cloudy** : Nebular emission models  
  > "we used `Cloudy` (cite: Cloudy:2023) to obtain the models for the nebular emission" (5 SED fitting)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Redshift | 5.54455 | 0.00002 | dimensionless | 1 | we estimated a redshift of $5.54455 \pm 0.00002$ for the galaxy |
| Broad component FWHM | 430 | 10 | km/s | 1 | Broad / 430 $\pm$ 10 |
| Integrated Halpha SFR | 77 | +19/-16 | Msun/yr | 2 | $\rm SFR = 77_{-16}^{+19}$ M${_\odot}$ yr$^{-1}$ |
| Electron density | 270 | +260/-200 | cm^-3 | 2 | $n_e = 270_{-200}^{+260}$ cm$^{-3}$ |
| 12+log(O/H) whole galaxy | 8.34 | 0.08 | dex | 2 | $\rm 12 + \log(O/H) = 8.34 \pm 0.08$ for the entire galaxy |
| Stellar mass of system | 9.75 | +0.05/-0.10 | log Msun | 4 | $\log(M_\star/M_\odot) = 9.75_{-0.10}^{+0.05}$ |
| S160um continuum flux | 134 | 33 | µJy | 5 | $S_{\rm 160\,\mu m} = 134 \pm 33~ \mu$Jy |
| Dust temperature | 70 | 12 | K | 7 | $T_D = 70\pm12$ K |
| Ionized outflow velocity | 389 | 12 | km/s | 6 | = 389 \pm 12 {\rm~ km ~s^{-1}} |
| Ionized mass outflow rate (Halpha) | 2.3 | +2.7/-0.6 | Msun/yr | 6 | $\Dot{M}_{\rm out, H\alpha} = 2.3 ^{+2.7}_{-0.6}$ M${_\odot}$ yr$^{-1}$ |
| Neutral mass outflow rate lower limit | ~121 | not stated | Msun/yr | 6 | we compute a lower limit on the mass outflow rate of $\Dot{M}_{\rm H, out} \sim 121$ M${_\odot}$ yr$^{-1}$ |
| Escape velocity | ~800 | not stated | km/s | 6 | $v_{\rm esc} \sim 800$ ${\rm km~s^{-1}}$ |

## Qualitative findings

- JWST shows HZ4 is composed of three components (North, Central, South) with different SFHs, not a regular rotating disk  
  > "it is formed by three different components" (9 Conclusions)

## Claim tuples

- H: Is HZ4 a rotating disk? | E: Spatially resolved NIRSpec kinematics and continuum | R: Clumpy morphology, abrupt velocity gradient in south, different SFHs | F: HZ4 is a merger of multiple components | **supported**
- H: Do broad components trace a multiphase outflow? | E: Two-component fits to [OIII]/Halpha and [CII]; outflow energetics | R: Broad ionized is blueshifted, [CII] broad redshifted but co-spatial; eta_ion~3%, eta_neutral~150% | F: If outflows, mass is dominated by the neutral phase | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Fountain, inflow, and merger shocks considered; shocks disfavoured by BPT/VO87  
  > "we do not find line ratios consistent with the presence of shocks" (7 Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Origin of the broad components remains uncertain  
  > "it remains challenging to fully understand its geometry and pinpoint the origin of the broad components" (9 Conclusions)
- Caveat (inferred, ours): Outflow interpretation of broad components is speculative
- Caveat (inferred, ours): Neutral outflow mass is a lower limit with assumed k_[CII]
- Caveat (inferred, ours): Spaxel S/N threshold affects broad-component detection
- Caveat (inferred, ours): Redshifted [CII] vs blueshifted [OIII] difficult to reconcile

## Reproducibility

- Data public (paper): ALMA from archive; JWST from MAST  
  > "We retrieved the raw data from the Mikulski Archive for Space Telescopes (MAST) archive" (2.1 JWST data)
- Products in archive: _not stated_
- Missing: CASA version
- Missing: [CII] line-free channels and clean settings
- Missing: fitting code for spaxel fits
- Missing: Herrera-Camus et al. in prep. details
- Data volume (inferred): ~50-100 GB ALMA raw plus ~10 GB JWST
- Score (inferred): 3/5, Public data and fitting recipe described, but ALMA reduction details and fit code are deferred or unstated.
- Rediscovery candidate: no, ALMA is secondary to JWST, and reduction details are incomplete.

## Links

- Method: (cite: Carniani:2023) (Broad-component fitting and outflow methodology)
- Method: (cite: Perna:2023) (Custom JWST IFS pipeline steps)
- Companion: (cite: Herrera-Camus:2021) (Previous [CII] outflow analysis of HZ4)
- Related: GA-NIFS
- Related: CRISTAL
- Related: ALPINE

## Checks

```json
{
 "quotes": 74,
 "quotes_ok": 74,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 87,
  "stated": 51,
  "rate": 0.586
 },
 "evidence_ok": true
}
```
