# Radiation-pressure-driven sub-Keplerian rotation of the disc around the AGB star L<SUB>2</SUB> Pup

`2018MNRAS.473..317H` | Monthly Notices of the Royal Astronomical Society 2018 | first author: Haworth, Thomas J. | arXiv: 1709.02815 | DOI: 10.1093/mnras/stx2416

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: evolved_stars
- Question: Can radiation pressure on dust explain the observed sub-Keplerian rotation of the disc around L2 Pup, and what dust populations are compatible with the rotation curve and SED?  
  > "we aim to further extend our understanding of the structure of discs surrounding evolved stars by investigating whether the sub-Keplerian motion observed in the disc around L$_{\rm 2}$ Pup could be induced by radiation pressure on the dust." (Introduction)
- Target **L2 Pup (HD 56096)**: coordinates _not stated_; z/distance 64 pc  
  > "It is the second nearest asymptotic giant branch (AGB) star, located at a distance of only 64 pc" (Introduction); distance from (cite: 2007A&A...474..653V)  
  > "It is the second nearest asymptotic giant branch (AGB) star, located at a distance of only 64 pc" (Introduction)

## Data provenance

- ALMA projects: 2011.0.00277.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **NACO/VLT, VLTI/MIDI and other SED data**: Observed SED used to constrain the models  
  > "which we compare with the observed NACO/VLT, VLTI/MIDI, and other data, summarised in (cite: 2014A&A...564A..88K)." (4.4 SED modelling)
- External data: Observed azimuthal velocity profile v_phi = 40.7 (R/AU)^-0.853 km/s from ALMA kinematics  
  > "v_{\phi} = 40.7\left(\frac{R}{\textrm{AU}}\right)^{-0.853}\,\textrm{km\,s}^{-1}." (2.1 Basic concept) [from (cite: 2016A&A...596A..92K)]
- External data: Disc density and temperature structure from CO radiative transfer modelling  
  > "We base our disc on the best-fit models of (cite: 2017A&A...601A...5H)." (3.3 Disc construction) [from (cite: 2017A&A...601A...5H)]
- External data: Observed SED data  
  > "summarised in (cite: 2014A&A...564A..88K)" (4.4 SED modelling) [from (cite: 2014A&A...564A..88K)]

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

- Disc density, scale height, temperature structure and outer radius  
  > "We base our disc on the best-fit models of (cite: 2017A&A...601A...5H)." (3.3 Disc construction) [from (cite: 2017A&A...601A...5H)]
- Stellar parameters (Teff, L, R, mass)  
  > "We assume an effective temperature of 3500 K, a luminosity of 2000L$_{\odot}$, a radius of 121 R$_{\odot}$ and a mass of 0.659 M$_{\odot}$ (cite: 2016A&A...596A..92K)." (3.2 Stellar model) [from (cite: 2016A&A...596A..92K)]

### Not stated but needed to reproduce (our reading)

- Number of photon packets and TORUS grid resolution
- Exact SED data points and uncertainties used in the chi-square
- Convergence criteria for manual search of a_max profiles

## Analysis recipe

1. **Test thermal pressure gradient alone**: Evaluate mid-plane rotation with f_rad=0 and power-law temperature profiles  
  > "we consider equation [\[vphi_wpgrad\]](#vphi_wpgrad) with $f_{\textrm{rad}}=0$." (4.1 Can a thermal pressure gradient explain the rotation curve?)
   - fitting: _not stated_
   - validation: _not stated_
2. **Find dust populations reproducing rotation curve**: TORUS Monte Carlo radiation pressure, manual adjustment of a_max or dust-to-gas ratio per radial bin  
  > "In this paper we locate solutions to the rotation profile manually." (3.1 Model parameters)
   - software: TORUS
   - parameter: 10 radial dust types, q=3.3, a_min=1 nm  
  > "we use 10 different dust types that apply over discrete radial ranges" (3.1 Model parameters)
   - assumption: Dust and gas dynamically coupled; Draine silicates; grain density 3 g cm^-3 for Stokes number  
  > "The grain mass $m_d$ is computed assuming a density of $3$ g cm$^{-3}$." (4.3 Dust-gas dynamics)
   - fitting: _not stated_
   - validation: Stokes number and coupled dust-gas velocity solution  
  > "We have confirmed this by directly solving for the dust and gas velocity at each radius" (4.3 Dust-gas dynamics)
3. **Compare synthetic SEDs with observations**: Chi-square on wavelengths at a given flux for points longward of 10 micron  
  > "We evaluate the goodness of fit of each model using a chi-square measure for the $N$ points of the observed SED longward of $10\,\mu$m" (4.4 SED modelling)
   - software: TORUS
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **TORUS** : Monte Carlo radiative transfer, radiation pressure force and SEDs  
  > "TORUS computes the radiation pressure force using the algorithm presented by (cite: 2015MNRAS.448.3156H)." (3.1 Model parameters)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Best-match dust-to-gas mass ratio | 2.5e-3 | not stated | dimensionless | 3 | the model with $\delta=2.5\times10^{-3}$ is the only one that is consistent with all observed points longward of $10\,\mu$m within uncertainties |
| Dust replenishment rate | 3.3e-9 | not stated | Msun/yr | 2 | which yields a required replenishment rate of $3.3\times10^{-9}$ M$_\odot$ yr$^{-1}$ |
| Dust depletion timescale | ~20 | not stated | yr | 2 | the disc will be depleted of dust within $\sim 20\,{\rm yr}$ |

## Qualitative findings

- Thermal pressure gradient alone cannot explain sub-Keplerian rotation  
  > "We find that the thermal pressure gradient alone cannot explain the observed rotation profile." (abstract)

## Claim tuples

- H: Radiation pressure on dust drives the sub-Keplerian rotation | E: TORUS radiation pressure models compared to the observed rotation curve and SED | R: A family of dust populations reproduces the rotation; SED favours delta ~1-4e-3 with decreasing a_max | F: Radiation pressure is a capable and necessary mechanism | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Thermal pressure gradient with hot power-law temperature; wind-like interpretation rejected  
  > "We therefore conclude that the disc interpretation is the more applicable" (5.2 On the possibility that the circumstellar matter is more wind-like than disc-like)
- How they decided it was enough: _not stated_
- Limitation (authors): Models simple: vertically constant dust, no full radiation hydrodynamics  
  > "Our models in this paper are dynamically and geometrically quite simple" (5.1 On dust replenishment)
- Caveat (inferred, ours): Manual solution search with degenerate parameters
- Caveat (inferred, ours): Fixed disc structure inherited from CO modelling

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: TORUS settings and photon counts
- Missing: SED data table
- Data volume (inferred): No ALMA data processed directly
- Score (inferred): 3/5, Theory paper with detailed model description but manual fitting and unreleased inputs.
- Rediscovery candidate: no, Models rely on TORUS and inherited literature inputs; ALMA data not reprocessed.

## Links

- Method: (cite: 2015MNRAS.448.3156H) (TORUS radiation pressure algorithm)
- Companion: (cite: 2016A&A...596A..92K) (ALMA kinematics of the disc)
- Companion: (cite: 2017A&A...601A...5H) (CO radiative transfer disc model)

## Checks

```json
{
 "quotes": 26,
 "quotes_ok": 26,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 64,
  "stated": 19,
  "rate": 0.297
 },
 "evidence_ok": true
}
```
