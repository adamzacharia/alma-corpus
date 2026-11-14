# Determining the mid-plane conditions of circumstellar discs using gas and dust modelling: a study of HD 163296

`2016MNRAS.461..385B` | Monthly Notices of the Royal Astronomical Society 2016 | first author: Boneberg, Dominika M. | arXiv: 1605.07938 | DOI: 10.1093/mnras/stw1325

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks
- Question: What are the gas mass and gas-to-dust ratio in the mid-plane of HD 163296 within the CO snowline, from combined C18O line modelling, CO snowline location and SED?  
  > "Here we present a novel approach to study the mid-plane gas by combining C$^{18}$O line modelling, CO snowline observations and the spectral energy distribution (SED)" (abstract)
- Target **HD 163296**: coordinates RA 17h56m21.281s, Dec -21d57m22.36s (J2000)  
  > "HD 163296 (RA$=17^h56^m21\mbox{\ensuremath{.\!\!^{s}}}281$, Dec.$=-21^\circ 57'22\mbox{\ensuremath{.\!\!^{\prime\prime}}}36$; J2000)" (2.1 Description of observations); "It is situated at a distance of about $d=122$ pc (cite: VanDenAnckerEtAl1998)" (1 Introduction); z/distance 122 pc  
  > "HD 163296 (RA$=17^h56^m21\mbox{\ensuremath{.\!\!^{s}}}281$, Dec.$=-21^\circ 57'22\mbox{\ensuremath{.\!\!^{\prime\prime}}}36$; J2000)" (2.1 Description of observations); "It is situated at a distance of about $d=122$ pc (cite: VanDenAnckerEtAl1998)" (1 Introduction); distance from VanDenAnckerEtAl1998  
  > "HD 163296 (RA$=17^h56^m21\mbox{\ensuremath{.\!\!^{s}}}281$, Dec.$=-21^\circ 57'22\mbox{\ensuremath{.\!\!^{\prime\prime}}}36$; J2000)" (2.1 Description of observations); "It is situated at a distance of about $d=122$ pc (cite: VanDenAnckerEtAl1998)" (1 Introduction)

## Data provenance

- ALMA projects: 2011.0.00010.SV
- bands: Band 6 (12CO, 13CO, C18O J=2-1) and Band 7 (12CO J=3-2)  
  > "Science verification data of HD 163296 were taken by ALMA in Band 6 and 7" (2.1 Description of observations)
- frequencies and spectral setup: C18O J=2-1: 150 channels, 0.33 km/s resolution (~0.24 MHz), rest frequency 219.56 GHz  
  > "the spectral resolution is $0.33$ km s$^{-1}$ ($\sim0.24$ MHz) with 150 channels" (2.1 Description of observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 20-400 m, 24 12-m antennas  
  > "were taken with 24 ALMA antennas (12 m) in 2012, on June 9 and 23 and July 7 with baselines spanning 20–400 m" (2.1 Description of observations)
- angular resolution: C18O beam 0.73 x 0.58 arcsec (~0.7 arcsec, ~85 au)  
  > "The beam size of the reduced and cleaned C$^{18}$O data is $0.73'' \times 0.58''$" (2.1 Description of observations)
- max recoverable scale: _not stated_
- sensitivity: C18O rms 2e-2 Jy/beam  
  > "C$^{18}$O J=2–1 (SV) | $0.73 \times 0.58$ | $2\times10^{-2}$" (Table 2)
- time on source: 84 min  
  > "a total on-source time of 84 min (cite: RosenfeldEtAl2013)" (2.1 Description of observations)
- observing dates: 2012 June 9, June 23, July 7  
  > "in 2012, on June 9 and 23 and July 7" (2.1 Description of observations)
- pi or archival as stated: _not stated_
- Line: C18O J=2-1 (219.56 GHz)
- External data: Observed SED and 0.85 mm flux density S≈2.1 Jy  
  > "we find a flux density of $S \approx 2.1$ Jy (cite: GuidiEtAl2016)" (4.1 Results of the SED modelling) [from GuidiEtAl2016]
- External data: CO snowline radius 90 au  
  > "CO snowline radius$^{7}$ $R_\text{sl}$ | $90$ au" (Table 1) [from QiEtAl2015]
- External data: Stellar Teff 9250 K and L 37.7 Lsun  
  > "with a luminosity of $L=37.7\,\text{L}_\odot$ and an effective temperature of $T_{\text{eff}}=9250$ K (cite: TillingEtAl2012)" (1 Introduction) [from TillingEtAl2012]
- External data: Dust opacity, kappa~4 cm2/g at 1 mm for 1 mm grains  
  > "$\kappa_\lambda \approx 4$ cm$^2$ g$_\text{dust}^{-1}$" (4.1 Results of the SED modelling) [from Draine2006]
- External data: [16O]/[18O]=557±30  
  > "\[$^{16}$O\]/\[$^{18}$O\]=$557\pm30$, (cite: Wilson1999)" (1 Introduction) [from Wilson1999]
- External data: Mass accretion rate (0.8-4.5)e-7 Msun/yr  
  > "within the range (0.8-4.5) $\times 10^{-7}$ M$_\odot$yr$^{-1}$ (cite: GarciaLopezEtAl2015)" (3.1.1 MCMAX) [from GarciaLopezEtAl2015]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.4.0  
  > "CASA software package version 4.4.0" (2.1 Description of observations)
- pipeline version: _not stated_
- archive products used as is: Used self-calibrated and cleaned SV data from ALMA Portal  
  > "We employ the already self-calibrated and cleaned Science Verification data provided on the ALMA Portal." (2.1 Description of observations)
- flux calibrator: _not stated_
- flux scale uncertainty: ~10% flux calibration uncertainty  
  > "given by the $\sim 10\%$ flux calibration uncertainty of the ALMA observations" (4.4 The inner disc regions)
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

- Spectral windows and calibration details  
  > "For a detailed summary of the spectral windows and calibrations, see (cite: RosenfeldEtAl2013)." (2.1 Description of observations) [from RosenfeldEtAl2013]
- Photodissociation criterion qualitatively similar  
  > "we implement a simple criterion, qualitatively similar to that of (cite: WilliamsBest2014)" (3.1.2 Modelling of the C18O line emission) [from WilliamsBest2014]
- Turbulent broadening 0.01-0.1 cs  
  > "Following (cite: SimonEtAl2015), we employ a value of $0.01 - 0.1 c_{\textrm{s}}$" (3.1.2) [from SimonEtAl2015]

### Not stated but needed to reproduce (our reading)

- Moment-map/integration velocity ranges and masks for the 6.2 Jy km/s and line profiles
- Exact CASA tasks and settings for 2D Gaussian fits and synthetic observation (simobserve/uv sampling) of TORUS cubes
- Dust composition and full opacity table used in MCMAX
- Criterion for an 'acceptable' SED fit and SED data sources
- TORUS grid and ray-tracing setup, image size and pixel scale
- Vertical temperature/CO ice surface treatment details
- Whether dust-gas models use inner radius and scale-height inputs

## Analysis recipe

1. **Measure disc geometry and C18O flux from ALMA cubes**: Moment maps and 2D Gaussian fits in CASA to get PA and inclination; integrated intensity  
  > "Fitting a 2D Gaussian to the spatial profile of the emission with CASA allows us to determine the inclination of the disc" (2.2 Spatial structure of the emission)
   - software: CASA
   - parameter: adopted PA=132 deg, i=48 deg  
  > "For our models, we will adapt a PA=132 $^{\circ}$ and an inclination of $i$=48 $^{\circ}$" (2.2 Spatial structure of the emission)
   - fitting: _not stated_
   - validation: Compared with literature PA and inclination  
  > "This is in agreement with what other studies have found from CO and continuum observations" (2.2 Spatial structure of the emission)
2. **Model disc temperature/density and SED**: MCMAX Monte Carlo radiative transfer with hydrostatic equilibrium and dust settling; vary Mdust, amin, amax, g/d, alpha_turb; fit SED and require mid-plane T consistent with 90 au snowline  
  > "we first model the 2D temperature and density structure of the disc using the radiative transfer code MCMAX (cite: MinEtAl2009), ensuring that our models match the observed SED and CO snowline radius." (3.1 Physical models)
   - software: MCMAX
   - parameter: 5e7 photon packages, 350 azimuthal and 400 radial cells; Rout=540 au; Sigma ∝ r^-p, p=1-1.2; alpha_turb 1e-4 to 1e-2  
  > "We perform the above iterations using $5\times10^{7}$ photon packages and 350 grid cells in the azimuthal direction and 400 in radial direction." (3.1.1 MCMAX)
   - assumption: Gas and dust temperatures equal; grain size distribution n(a)∝a^-3.5; Kurucz stellar model; Mgas×alpha_turb constant gives identical SED  
  > "We assume in every case that the grains follow a power-law size distribution of $n(a) \propto a^{-k}$" (3.1.1 Modelling the SED)
   - fitting: Manual exploration of >100 models, no formal fit; 15 acceptable  
  > "We have explored in total over 100 models varying $M_\text{dust}$, $a_\text{min}$, $a_\text{max}$ and $g/d$ (alone, and in combination with $\alpha_\text{turb}$) and have found 15 models that fit the observed SED" (4.1 Results of the SED modelling)
   - validation: Mid-plane T at 90 au between 20 and 25 K, consistent with CO freeze-out  
  > "We find that all of them have mid-plane temperatures between $\sim 20$ and $25\,$K at the observed snowline radius" (4.3 Models matching the CO snowline location)
3. **Synthesize C18O J=2-1 emission and compare with observed profile**: TORUS LTE line radiative transfer on mapped MCMAX structures, freeze-out below T(90 au), photodissociation threshold, CASA processing to synthetic observations; compare spectra from elliptical region R<90 au  
  > "We implement a model for freeze-out, whereby the C$^{18}$O abundance drops to a negligible value if the temperature is below the freeze-out temperature" (3.1.2)
   - software: TORUS, CASA
   - parameter: C18O abundance 1.4e-7 to 1.7e-6; N_CO photodissociation 1e18,1e19,1e20 cm-2; vturb 0.01-0.1 cs  
  > "$$1.4 \times 10^{-7} < \frac{[\text{C}^{18}\text{O}]}{[\text{H}_2]} < 1.7 \times 10^{-6}$$" (3.1.2)
   - assumption: LTE; [C18O]/[CO]=[18O]/[16O]; CO/H2~1e-4; gas and dust thermally coupled  
  > "We assume that the gas and dust are thermally coupled" (3.1.2)
   - fitting: _not stated_
   - validation: Match within ~10% flux calibration uncertainty; line optically thin  
  > "All of them match the observations well within the error bars (given by the $\sim 10\%$ flux calibration uncertainty of the ALMA observations" (4.4 The inner disc regions)
4. **Derive C18O mass, gas mass, g/d, alpha_visc and Toomre Q within 90 au**: Convert C18O mass to H2 using abundance and mass ratio ~14; extremes from abundance range; alpha_visc from Mgas/Mdot flow time; Toomre Q  
  > "by taking into account the abundance of C$^{18}$O given in Table [\[tab:90au\]](#tab:90au) and the mass ratio of these molecules ${m_{\text{C}^{18}\text{O}}}/{m_{\text{H}_2}} \approx 14$" (Results and discussion, Gas mass within the snowline radius)
   - parameter: H/r~0.1, tau_dyn(90 au)~100 yr  
  > "The scale-height of our models is $H/r \sim 0.1$." (4.5 Viscosity)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.4.0: Analysing ALMA cubes, PA/inclination fits, synthetic observations  
  > "We use the *Common Astronomy Software Applications* CASA software package version 4.4.0" (2.1 Description of observations)
- **MCMAX** : 2D temperature and density structure and SED  
  > "We use the 3D radiative transfer code MCMAX, which self-consistently calculates a 2D temperature and density structure" (3.1.1 MCMAX)
- **TORUS** : Molecular line radiative transfer and synthetic C18O cubes  
  > "We use the radiation transport and hydrodynamics code TORUS to perform molecular line transfer calculations in this paper" (3.1.2)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| C18O J=2-1 integrated intensity | 6.2 | ±0.4 | Jy km/s | 1 | We find an integrated intensity of C$^{18}$O J=2-1 of $6.2\pm0.4$ Jy km s$^{-1}$ |
| Disc position angle (C18O) | 132.8 | ±3.4 | deg | 1 | PA=(132.8$\pm$3.4) $^\circ$ |
| Disc inclination (C18O) | 47.9 | ±1.6 | deg | 1 | inclination of $i=$(47.9$\pm$1.6) $^\circ$ |
| C18O mass within 90 au | 2-3e-8 | not stated | Msun | 3 | ${M}_{\text{C}^{18}\text{O}}(R<90\,\text{au}) \approx 2-3 \times 10^{-8} \text{M}_\odot |
| Gas mass within 90 au (fiducial models) | (1.3-5.0)e-3 | not stated | Msun | 4 | ${M}_{\text{gas}}(R<90\,\text{au}) \approx (1.3 - 5.0) \times 10^{-3}\,\text{M}_\odot$ |
| Gas mass within 90 au incl. abundance uncertainty | 6.6e-4 to 1.1e-2 | not stated | Msun | 4 | $6.6 \times 10^{-4}\,\text{M}_\odot \lesssim {M}_{\text{gas}}(R<90\,\text{au}) \lesssim 1.1 \times 10^{-2}\,\text{M}_\odot$ |
| Gas-to-dust ratio, fiducial models | 9-20 | not stated | dimensionless | 4 | all models (excluding the extreme cases) have very low $g/d$ values ($9 \lesssim g/d \lesssim 20$) |
| Maximum g/d (B_max, C_max) | 82, 71 | not stated | dimensionless | 4 | The highest possible values of $g/d$ for models that match the observed C$^{18}$O line profiles are 82 and 71 |
| alpha_visc fiducial models | 0.2-0.7 | not stated | dimensionless | 4 | We obtain a high $\alpha_\text{visc} \sim 0.2 - 0.7$ for our models of the inner disc regions |
| Minimum dust mass estimate | 8e-4 | not stated | Msun | 2 | We thus estimate a minimum dust mass of $M_\text{dust,min} \sim 8 \times 10^{-4}\,\text{M}_\odot$. |

## Qualitative findings

- All models have Toomre Q well above 1 at R<90 au; disc not gravitationally unstable  
  > "We find that all of our models are well above the threshold value of $Q=1$." (4.5 Gravitational instability)

## Claim tuples

- H: Combining C18O, snowline and SED constrains inner-disc gas mass and g/d | E: MCMAX+TORUS models compared to SED, 90 au snowline and ALMA C18O profile | R: M_C18O(<90au)~2-3e-8 Msun; Mgas(<90au) 0.7-11e-3 Msun | F: Combination breaks degeneracies that SED+snowline alone cannot | **supported**
- H: The inner disc has ISM-like g/d=100 | E: Model grid with C18O abundance range | R: Most models g/d 10-20; only models with low C18O abundance and depleted sub-micron grains reach ~70-80 | F: Gas depletion or small-grain depletion needed | **refuted**
- H: Angular momentum transport is turbulent | E: Compare alpha_visc with alpha_turb | R: alpha_visc ~2 orders above alpha_turb | F: Evidence against turbulent viscosity model | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: C18O is optically thin and traces the mid-plane; restricting to R<90 au avoids freeze-out  
  > "selectively study the inner tens of au where freeze-out is not relevant" (abstract)
- Alternative: Puffed-up inner rim not included; would only affect NIR  
  > "For simplicity, we therefore do not include a model for a puffed up inner rim at this stage." (4.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Not a single best-fit model; outer disc emission over-predicted; SED modelling degenerate  
  > "We do not aim to provide one best-fitting model for the disc around HD 163296" (1 Introduction)
- Caveat (inferred, ours): No formal fit or likelihood; model selection by eye
- Caveat (inferred, ours): Results depend on assumed C18O abundance and isotopic ratio
- Caveat (inferred, ours): LTE and equal gas/dust temperature assumed
- Caveat (inferred, ours): Low-resolution data; no spatially resolved fitting

## Reproducibility

- Data public (paper): SV data available on ALMA Portal  
  > "The ALMA observations are provided as 3D fits cubes with two spatial and one spectral axis (velocity/frequency) on the ALMA Portal" (2.1 Description of observations)
- Products in archive: _not stated_
- Missing: MCMAX and TORUS input files and dust composition
- Missing: Exact SED data and acceptance criteria
- Missing: CASA steps for synthetic observations
- Data volume (inferred): Few GB (calibrated SV cubes)
- Score (inferred): 3/5, Public SV data and clear model grid with tables, but codes' inputs and fit criteria are not given.
- Rediscovery candidate: no, Requires MCMAX/TORUS modelling with incomplete setup details.

## Links

- Method: MinEtAl2009 (MCMAX code)
- Method: RundleEtAl2010 (TORUS molecular line transfer)
- Companion: RosenfeldEtAl2013 (SV data description and calibration)
- Companion: QiEtAl2015 (CO snowline at 90 au and C18O data)
- Related: ALMA Science Verification

## Checks

```json
{
 "quotes": 64,
 "quotes_ok": 64,
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
  "facts": 76,
  "stated": 45,
  "rate": 0.592
 },
 "evidence_ok": true
}
```
