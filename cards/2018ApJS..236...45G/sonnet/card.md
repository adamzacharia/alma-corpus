# Chemistry of the High-mass Protostellar Molecular Clump IRAS 16562-3959

`2018ApJS..236...45G` | The Astrophysical Journal Supplement Series 2018 | first author: Guzmán, Andrés E. | arXiv: 1804.06544 | DOI: 10.3847/1538-4365/aac01d

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: What is the chemistry, morphology and kinematics of molecular emission in the high-mass protostellar clump IRAS 16562-3959 at 0.014 pc resolution, including hot cores, extended gas and cold starless gas?  
  > "In this work, we study the chemistry and kinematics at small scales ($0.014$ pc) associated with the molecular emission from IRAS 16562$-$3959" (1 Introduction)
- Target **IRAS 16562-3959 (HMYSO G345.4938+01.4677)**: coordinates Source 10: R.A.=16h59m41.63s, decl.=-40d03m43.6s  
  > "This molecular clump is located at $\sim1.7$ kpc, it has a mass of $\approx900\mbox{$M_{\ensuremath{\odot}}$}$" (1 Introduction); z/distance ~1.7 kpc  
  > "This molecular clump is located at $\sim1.7$ kpc, it has a mass of $\approx900\mbox{$M_{\ensuremath{\odot}}$}$" (1 Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00351.S
- bands: 3 mm  
  > "taken at 3 mm using the Atacama Large Millimeter/submillimeter Array (ALMA)" (abstract)
- frequencies and spectral setup: four SpWs of 1.875 GHz, centered at 85.4, 87.2, 97.6, 99.3 GHz; channel width 488 kHz (~1.6 km/s), Hanning smoothed  
  > "The data covers four spectral windows (SpW) of 1.875 GHz wide each, centered at 85.4, 87.2, 97.6, and 99.3 GHz with a channel width of 488 kHz" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: 12m array only  
  > "the data were taken during 2012 using the 12m array" (2 Observations)
- configurations: _not stated_
- baselines: 21-453 m  
  > "with a configuration including baselines between 21 and 453 m" (2 Observations)
- angular resolution: 1.7 arcsec; typical beam 2.3x1.3 arcsec, PA=97 deg  
  > "Typical synthesized beam is approximately $2.3\ensuremath{''}\times1.3\ensuremath{''},\text{ P.A.}=97\ensuremath{^\circ}$" (2 Observations)
- max recoverable scale: ~19 arcsec  
  > "prevents the adequate recovery of structures larger than $\sim19\ensuremath{''}$" (2 Observations)
- sensitivity: 0.8-1.0 mJy/beam per channel  
  > "with a noise per channel of $0.8$–$1.0$ mJy beam$^{-1}$" (2 Observations)
- time on source: _not stated_
- observing dates: 2012  
  > "the data were taken during 2012 using the 12m array" (2 Observations)
- pi or archival as stated: _not stated_
- Line: CH3OH 2(1,1)-1(1,0) E1 and others (11 lines) (96.7604 GHz)
- Line: CH3CCH J=5-4, K=0-3 (85.4605 GHz)
- Line: SiO J=2-1 (86.8499 GHz)
- Line: NH2D 1(1,1),0s-1(0,1),0a (85.9223 GHz)
- Other facility **VVV survey (NIR)**: JHKs image compared with ALMA moment maps  
  > "Figure [15] shows a three color NIR image (JHK$_S$ filters) of IRAS 16562$-$3959 using data from the VVV survey" (6.1)
- Other facility **SEST**: single-dish CS 2-1 spectrum for short-spacing check  
  > "we compare the flux of the CS, $J=2\shortrightarrow1$ emission with that obtained by (cite: Bronfman1996AAS) using the *Swedish-ESO Submillimetre Telescope* (SEST)" (Appendix A)
- External data: Density profile n(r)=1.4e5 (0.1pc/r)^1.9 cm^-3 used for critical density check  
  > "Using the density profile $n(r)=1.4\times10^5(0.1\text{pc}/r)^{1.9}$ cm$^{-3}$ proposed for IRAS 16562$-$3959 by (cite: Guzman2010ApJ)" (4.1) [from (cite: Guzman2010ApJ)]
- External data: Solar and Galactic isotopic ratios for comparison  
  > "Solar abundances from (cite: Asplund2009ARAA)" (Table 2) [from (cite: Asplund2009ARAA); (cite: Wilson1999RPPh); (cite: Monson2017ApJ)]

## Processing

### Calibration

- pipeline or manual: calibration described in earlier paper  
  > "describes in more detail the observations and its calibration." (2 Observations)
- casa version: CASA v4.7.2  
  > "CASA v4.7.2 (cite: Petry2012ASPC)." (Software)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean in CASA, on continuum-subtracted data  
  > "We re-imaged the continuum subtracted data using the task `tclean` of the Common Astronomy Software Applications (CASA)" (2 Observations)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: no masks; clean to 2 sigma ~2.5 mJy; 5000 iteration limit in bright channels  
  > "we performed clean iterations with no masks until a threshold of $2\sigma\approx2.5$ mJy was reached in the residuals." (2 Observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Observations, calibration and continuum/imaging parameters taken from companion paper  
  > "using similar parameters as in ." (2 Observations) [from companion paper (citation stripped in text; likely Guzman2014/2016)]
- Moment-masking algorithm for zero-moment maps  
  > "we use the moment masking algorithm described in (cite: Dame2011arXiv) and the CASA task `immoments`." (3.2) [from (cite: Dame2011arXiv)]
- Line identification criteria  
  > "To identify the line we follow the criteria defined in (cite: Herbst2009ARA&A)." (3.1) [from (cite: Herbst2009ARA&A)]

### Not stated but needed to reproduce (our reading)

- Calibrators, flux scale and calibration pipeline version (deferred to earlier paper)
- Robust/weighting, cell and image size, line-free channels for continuum subtraction
- Exact spectral ranges for moment masking
- Initial parameters/priors for Minuit fits
- Which lines/regions used for each assumed Tex

## Analysis recipe

1. **Image line cubes**: tclean on continuum-subtracted data, no masks, threshold 2 sigma, max 5000 iterations  
  > "We determine that a limit of $5000$ iterations is sufficient to reach stability of the cleaned flux." (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: no improvement with more iterations  
  > "No further improvement in the quality of the images was detected by performing a larger number of iterations." (2 Observations)
2. **Identify lines**: CASSIS with JPL and CDMS; LTE model comparison; anti-coincidence rejects  
  > "To identify different molecular species we used CASSIS together with the Jet Propulsion Laboratory" (3.1)
   - software: CASSIS
   - parameter: VLSR between -6 and -17 km/s  
  > "have $V_{\rm LSR}$ between $-6$ and $-17$ km s$^{-1}$" (3.1)
   - fitting: _not stated_
   - validation: at least three lines of main isotopologue for COMs  
  > "For the COMs, we were able to identify at least three lines of the main isotopologue per species." (3.1)
3. **Moment maps and cross-correlation grouping**: zero-moment maps; pixel cross-correlation rho with inner 6 arcsec masked; maximum correlation partner grouping  
  > "we mask the pixels (that is, we set $w_{ij}=0$) inside an inner circle of 6$''$ radius centered at G345.49+1.47." (3.3)
   - software: CASA immoments
   - fitting: _not stated_
   - validation: noise simulations give rho uncertainty <0.01; same grouping using cubes  
  > "In all cases, the uncertainty due to random noise is $<0.01$, making no discernible effect in the classification." (3.3)
4. **Propyne temperature and column density per pixel**: Gaussian fits to K components, LTE optically thin rotation diagram, pixels >5 sigma  
  > "We calculate the temperature and column density of CH$_3$CCH by fitting Gaussians to the four $K$ components and modeling the rotation diagrams assuming LTE and optically thin conditions." (4.1)
   - software: Minuit, Perl Data Language
   - parameter: sigma=1.2 mJy/beam, 5 sigma threshold  
  > "where $\sigma=1.2$ mJy beam$^{-1}$ is the rms noise" (4.1)
   - assumption: LTE since density above critical density 1.5e4 cm^-3  
  > "we conclude that the critical density for the transitions is $\approx1.5\times10^4$ cm$^{-3}$." (4.1)
   - fitting: chi-square weighted by inverse variance; uncertainties per Lampton 1976  
  > "We obtain best fitting parameters (column density, temperature, central velocity and FWHM of the line) by minimizing the squared differences weighted by the inverse variances." (4.1)
   - validation: compared with single-dish Miettinen et al. 2006  
  > "Both the excitation temperature and column densities are consistent with previous single dish observations" (4.1)
5. **Column densities and Tex for sources**: single excitation temperature models for all molecules except methanol; Radex non-LTE for CH3OH; Gaussian line profiles; filling factor 1  
  > "We model the emission of all molecules except CH$_3$OH using a single excitation temperature (SET) model" (4.2)
   - software: Radex, Minuit
   - parameter: Tex assigned from SO, CH3OH or CH3CCH based on critical density and VLSR group  
  > "we assign the same temperature as SO to all molecules whose transitions have critical densities above or equal to that of SO" (4.2)
   - assumption: beam filling factor 1; equal E and A methanol abundances  
  > "We assume, unless explicitly stated, that the beam filling factor of the emission is 1." (4.2)
   - fitting: chi-square weighted by sigma^-2 on primary-beam-corrected spectra; Lampton prescription  
  > "We find optimal parameters by minimizing the squared difference between the data and the model, weighted by $\sigma^{-2}$" (4.2)
   - validation: _not stated_
6. **Isotopic and isomer ratios**: line ratios of moment maps and column density ratios  
  > "Table [2] shows a summary of the typical observed fractionations." (5)
   - assumption: same Tex for isotopologue pairs  
  > "assuming the same excitation temperature for both molecules" (5.3)
   - fitting: _not stated_
   - validation: _not stated_
7. **Mass of NH2D starless clouds**: NH2D column density with fractionation 0.02 and NH3 abundance 5-30e-8, size from 30% contour  
  > "Assuming a mean deuterated ammonia fractionation of 0.02 (cite: Lackington2016MNRAS) characteristic of IRDCs, an ammonia abundance respect to H$_2$ ranging between $5\text{--}30\times10^{-8}$" (6.2.3)
   - assumption: Tex = 15 K  
  > "assuming an excitation temperature of 15 K" (6.2.3)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.2: tclean imaging, immoments  
  > "CASA v4.7.2 (cite: Petry2012ASPC)." (Software)
- **CASSIS** : line identification  
  > "we used CASSIS together with the Jet Propulsion Laboratory" (3.1)
- **Radex** : non-LTE methanol modeling  
  > "we model its emission using Radex" (4.2)
- **Minuit (Perl Data Language)** : chi-square minimization and uncertainties  
  > "implemented by the package *Minuit* within the *Perl Data Language*" (4.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CH3OH Tkin, CC core | 107 | 10 | K | 5 | CC core           / $107\pm 10$ / $16.57\pm 0.06$ |
| CH3OH log N, CC core | 16.57 | 0.06 | log cm^-2 | 5 | CC core           / $107\pm 10$ / $16.57\pm 0.06$ |
| CH3CCH radial temperature profile | 80 K (r/0.01 pc)^-0.3 | not stated | K | 4 | decaying power law given by $80~\text{K}(r/0.01\text{ pc})^{-0.3}$ |
| [SiO]/[29SiO] median | 11.2 | IQR 9.2-13.6 | dimensionless | 6 | with a median value across the clump of $11.2$ |
| [34SO]/[33SO] | 5.4 | 0.6 | dimensionless | 6 | we obtain \[$^{34}$SO\]/\[$^{33}$SO\]$=5.4\pm0.6$ |
| [OCS]/[O13CS] | 25 | 2.4 | dimensionless | 6 | we obtain \[OCS\]/\[O$^{13}$CS\]$=25\pm2.4$ |
| [H13CN]/[HC15N] mean | 5.7 | 2 | dimensionless | 6 | The mean \[H$^{13}$CN\]/\[HC$^{15}$N\] is $5.7\pm2$ |
| NH2D cloud masses SE and NE | 0.25-1.5 and 0.4-2.3 | not stated | Msun | 7 | we derive mass ranges for the SE and NE clouds of 0.25–1.5 and 0.4–2.3 $M_{\ensuremath{\odot}}$, respectively. |
| [CH3OCH3]/[CH3OH] CC core | 1.7e-1 | 0.03 | dimensionless | 5 | Methoxymethane to methanol ratios of $1.7\pm0.03\times10^{-1}$ and $4\pm2\times10^{-2}$ are measured toward the CC core and C8 |

## Qualitative findings

- Extended molecules split into Shock and Continuum groups by morphology; NH2D is separate  
  > "Figure [8] shows that molecules gather in two groups by linking them together with their MCPs." (3.3)

## Claim tuples

- H: Do molecules in the clump separate into chemically distinct spatial groups? | E: Cross-correlation of zero-moment maps | R: Two groups (Shock, Continuum) plus NH2D | F: Shock group formed on grains/shocks; Continuum group via gas-phase ion-neutral chemistry | **supported**
- H: Are the CC core and C8 both hot molecular cores at different evolutionary stages? | E: Methanol-normalized abundances and Tex | R: Higher C2H3CN/C2H5CN and HC5N/HC3N in C8 | F: C8 is more evolved than the CC core | **partially**
- H: Does the clump contain starless gas remnants? | E: NH2D emission vs NIR dark clouds and mass estimate | R: ~1 Msun clouds | F: Remnants of the prestellar clump unlikely to form stars | **supported**

## Reasoning

- Why this data: Spectral setup chosen for recombination lines; molecular data obtained incidentally  
  > "The additional molecular line information was obtained gratuitously." (2 Observations)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Lack of short spacings filters extended emission; modest spectral resolution  
  > "The lack of shorter baselines or single dish complementary data prevents the adequate recovery of structures larger than $\sim19\ensuremath{''}$." (2 Observations)
- Caveat (inferred, ours): Many Tex values assumed rather than fitted
- Caveat (inferred, ours): Filling factor of 1 assumed
- Caveat (inferred, ours): Low ratios may reflect optical depth or short-spacing loss not fractionation
- Caveat (inferred, ours): Spectral resolution ~3 km/s limits kinematics

## Reproducibility

- Data public (paper): Reduced cubes and moment maps publicly available on Harvard Dataverse  
  > "Fully reduced spectral cubes and images are publicly available (cite: data_Guzman2017)." (2 Observations)
- Products in archive: _not stated_
- Missing: Calibration details (in earlier paper)
- Missing: Weighting, cell size, image size, continuum channels
- Missing: Fit initial conditions
- Data volume (inferred): ~10-50 GB raw Cycle 0 data
- Score (inferred): 3/5, Public data and detailed fitting description, but calibration/imaging parameters deferred to earlier paper and many Tex assumed.
- Rediscovery candidate: no, Imaging/calibration settings deferred to companion paper and analysis involves many judgment choices.

## Links

- Method: (cite: Lampton1976ApJ) (Uncertainty prescription for fitting)
- Method: (cite: vanderTak2007AA) (Radex)
- Method: (cite: Dame2011arXiv) (moment masking)
- Companion: (cite: Guzman2014ApJ) (HC HII region and earlier continuum/ALMA analysis of same data)
- Companion: (cite: Guzman2016ApJ) (ionized jet and NIR analysis)
- Companion: (cite: Cesaroni2017AA) (higher-resolution CH3CN and continuum of central source)
- Related: VVV survey

## Checks

```json
{
 "quotes": 68,
 "quotes_ok": 68,
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
  "facts": 84,
  "stated": 50,
  "rate": 0.595
 },
 "evidence_ok": true
}
```
