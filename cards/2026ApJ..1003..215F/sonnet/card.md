# Reading between the Rings: Observed Dust Ring Properties as Probes of Planet Masses

`2026ApJ..1003..215F` | The Astrophysical Journal 2026 | first author: Faruqi, Amena | arXiv: 2605.27627 | DOI: 10.3847/1538-4357/ae6272

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: protoplanetary_disks
- Question: How do dust ring properties (mass, peak location, width) produced by an embedded planet depend on planet mass relative to the pebble-isolation mass, and can they constrain planet masses in observed discs?  
  > "We hypothesise that dust rings in protoplanetary discs formed by an embedded planet should have properties that reflect the planet’s mass." (abstract)
- Target **PDS 70**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2018.A.00030.S
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
- External data: PDS 70 outer ring peak (74.5 AU) and inner shoulder (54.5 AU) locations from ALMA Band 6/7  
  > "We first consider the location of the inner “shoulder” of PDS 70’s ring at 54.5 AU (cite: Fasano2025)" (4.6 Application of results to the PDS 70 system) [from (cite: Fasano2025)]
- External data: PDS 70 stellar mass and PDS 70c orbital radius  
  > "By combining the location of the ring, measured by (cite: Fasano2025), with the estimates provided by (cite: Hammond2025) for the mass of PDS 70 and the orbital radius of PDS 70c" (4.6 Application of results to the PDS 70 system) [from (cite: Hammond2025)]
- External data: exoALMA gas pressure gradients and dust gap/ring locations for 9 discs  
  > "We use the pressure gradients presented in Figures 7, E7, and E8 in (cite: Stadler2025)" (4.7 Application of results to exoALMA sample) [from (cite: Stadler2025)]
- External data: stellar masses for exoALMA systems  
  > "along with the stellar masses in (cite: izquierdo2025), to estimate the masses of the presumed planets forming the rings" (4.7 Application of results to exoALMA sample) [from (cite: izquierdo2025)]
- Simulation/model as data: 18 FARGO3D 2D (r,phi) gas + 5 dust species models, 1500 orbits, three aspect ratios  
  > "In total, 18 models are run (see Table [1](#tab:masses)) to 1500 planet orbits" (3.2 Simulation setup)

## Processing

### Calibration

- pipeline or manual: ALMA pipeline image used for display  
  > "overlaid on the ALMA pipeline image of the disk in Band 7 from program 2018.A.00030.S" (4.6 Application of results to the PDS 70 system)
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

- Pebble-isolation mass prescription  
  > "In this work, we follow the prescription given by (cite: bitsch2018), since it takes into account a broad range of parameters" (2 Pebble-Isolation Theory) [from (cite: bitsch2018)]
- MRN dust size distribution for weighting dust species  
  > "specified by the dust size distribution given in (cite: Mathis1977)" (3.4 Dust mass calibration) [from (cite: Mathis1977)]
- Planetesimal collapse probability formula  
  > "using the following expression (equations 10 and 11 in (cite: lau2024))" (4.4 Dust-to-Gas Ratios and Planetesimal Formation in Rings) [from (cite: lau2024)]

### Not stated but needed to reproduce (our reading)

- FARGO3D version and numerical parameters (flaring index only implied, viscosity prescription details, planet smoothing length, damping zones)
- Exact pressure-gradient extraction and interpolation from Stadler et al. digitized curves
- Uncertainty derivation method for planet masses
- Stellar masses and gap/ring locations used per exoALMA disc
- Details of how the PDS 70 ring locations/uncertainties were propagated

## Analysis recipe

1. **Run hydrodynamic simulations**: FARGO3D 2D gas plus 5 pressureless dust fluids, no dust feedback, fixed planet orbit  
  > "We run a series of 2D ($r + \phi$) simulations of gas and 5 dust species using FARGO3D" (3.2 Simulation setup)
   - software: FARGO3D
   - parameter: alpha=1e-4; Stokes 0.002-0.2; dust-to-gas 0.01; grid 504x1170; planets 0.5-2 M_iso; h/r 0.05, 0.06, 0.07  
  > "This corresponds to cylindrical grid dimensions of 504 radial cells against 1170 azimuthal cells" (3.2 Simulation setup)
   - assumption: Stellar mass 1 Msun; scale-free; fixed planet orbit  
  > "The stellar mass across all models is $1 M_\odot$." (Table 1)
   - fitting: _not stated_
   - validation: Checked steady state of rings over last 600 orbits  
  > "We find that the ring surface mass density is unchanging and the dust rings have reached an approximately steady height and width by 1500 orbits" (4 Results)
2. **Measure ring peak, edges, width and mass**: Peak = local maximum within 3-20 Hill radii; edges where density falls to 10% of peak or gradient below 0.5; mass integrated and weighted by MRN weights  
  > "either the value of the surface density drops to 10% of its peak value, or the magnitude of the surface density gradient drops below an arbitrarily small value, which was chosen here to be $0.5$" (3.3 Ring identification)
   - assumption: MRN distribution, total dust-to-gas 0.01  
  > "These masses are computed assuming the grains follow the MRN size distribution with a total dust-to-gas mass ratio of 0.01" (4.3 Ring masses)
   - fitting: Linear fit of ring peak and edge vs Hill radius  
  > "We apply a linear fit to our data and find that for all aspect ratios, the ring peak is located at approximately" (4.2 Ring peak locations)
   - validation: Varying thresholds changes widths but scaling holds  
  > "Changing these threshold values does yield different values for the measured ring widths but the scaling with planet mass we find in Section [4](#sec:results) still holds." (3.3 Ring identification)
3. **Apply ring peak relation to PDS 70c**: Invert r_peak relation for planet mass using literature ring location, star mass and planet radius  
  > "we can use Equation [\[eq:rpeak\]](#eq:rpeak) to estimate the mass of PDS 70c, assuming that PDS 70c is solely responsible for the formation of the ring." (4.6 Application of results to the PDS 70 system)
   - assumption: PDS 70c solely forms the ring; circular orbit  
  > "Equation [\[eq:rpeak\]](#eq:rpeak) is based on models in which the planets are on perfectly circular orbits" (4.6 Application of results to the PDS 70 system)
   - fitting: _not stated_
   - validation: Compared with Hammond2025 and Ruzza2025 masses  
  > "This aligns very well with the masses estimated by (cite: Hammond2025) ($5.4 \pm 3.1 M_{\rm Jup}$)" (4.6 Application of results to the PDS 70 system)
4. **Apply to exoALMA discs: planet mass and aspect-ratio bounds**: Find pressure maxima, compare max dP/dr within 5 AU on each side (difference >=0.001), pair with dust rings, estimate mass via ring-peak relation, combine with M_iso inequality  
  > "we then compute the maximum value of $\partial P/ \partial r$ within 5 AU of the pressure maximum in either direction and compare these values" (Application of results to exoALMA sample)
   - parameter: alpha=1e-4, Stokes 0.01, surface density slope 1, flaring index 0.25, stellar mass ±3%  
  > "assume a fixed Stokes number (here, we use 0.01)" (4.7 Application of results to the exoALMA sample)
   - fitting: _not stated_
   - validation: DM Tau compared with Ruzza2025  
  > "which aligns closely with our result for that system" (4.7 Application of results to exoALMA sample)

## Software

- **FARGO3D** : 2D hydrodynamic gas and dust simulations  
  > "using FARGO3D (cite: masset2000fargo; llambay2016fargo)" (3.2 Simulation setup)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Ring inner edge relation | r_edge = (1.0 ± 0.02) r_p + (5.4 ± 0.5) R_H | as stated | dimensionless coefficients | 2 | $$r_{edge} = (1.0 \pm 0.02)r_{p} + (5.4 \pm 0.5) R_{H}$$ |
| Ring peak relation | r_peak = (1.07 ± 0.01) r_p + (5.3 ± 0.3) R_H | as stated | dimensionless coefficients | 2 | r_{peak} = (1.07 \pm 0.01)r_{p} + (5.3 \pm 0.3) R_{H} |
| PDS 70c mass from inner shoulder (54.5 AU) | 3.3 | +7.1/-2.4 | M_Jup | 3 | we calculate the mass of PDS 70c to be $3.3^{+7.1}_{-2.4} M_{\rm Jup}$ |
| PDS 70c mass from 74.5 AU ring peak | 29.3 | +42.5/-17.5 | M_Jup | 3 | we estimate the mass of PDS 70c to be $29.3^{+42.5}_{-17.5} M_{\rm Jup}$ |
| Probability of gravitational collapse | at least 98% | not stated | percent | 0 | all scenarios predict a high probability of inducing gravitational collapse (at least 98% for all aspect ratios) |
| Dust mass in ring for highest-mass planets (scaled to disc 0.01 Msun) | ~20 (~7% of dust mass) | not stated | M_earth | 2 | the mass of solid material trapped in the dust rings is on the order of 20 Earth masses ($\sim 7$% of the total dust mass in the disc) |

## Qualitative findings

- Ring width and mass change with planet mass up to M_iso then plateau; ring peak location is independent of Stokes number  
  > "The dust ring width and mass change with planet mass for planet masses up to the pebble-isolation mass, beyond which they become constant." (abstract)

## Claim tuples

- H: Ring peak location scales linearly with planet Hill radius and can give planet mass | E: Linear fits to simulated ring peaks; application to PDS 70 | R: r_peak=(1.07±0.01)r_p+(5.3±0.3)R_H; PDS 70c 3.3 M_Jup from inner shoulder | F: Ring peak can estimate planet mass | **supported**
- H: Ring width and mass depend on planet mass relative to M_iso | E: 18 simulations over 0.5-2 M_iso | R: Both change below M_iso and plateau above | F: Rings can distinguish sub- vs super-M_iso planets | **supported**
- H: Pebble-isolation mass can be defined by pressure gradient asymmetry | E: Compared max interior/exterior pressure gradients vs planet mass | R: Interior gradient exceeds exterior above M_iso | F: New definition of M_iso usable with gas observations | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Gaussian/Lorentzian ring edge fits rejected due to asymmetric profiles  
  > "Instead, we define our own criteria for identifying the ring edges." (3.3 Ring identification)
- How they decided it was enough: _not stated_
- Limitation (authors): No migration, dust feedback, dust growth, or 3D; single alpha; circular orbits  
  > "The primary simplification in our models is that all planets are on fixed orbits, unable to migrate." (4.8 Caveats)
- Caveat (inferred, ours): Planet mass scales as cube of ring location offset, giving very large uncertainties
- Caveat (inferred, ours): Single alpha=1e-4 and fixed St assumed for aspect-ratio bounds
- Caveat (inferred, ours): Scale-free 2D models without growth may not match real rings

## Reproducibility

- Data public (paper): PDS 70 ALMA data cited as program 2018.A.00030.S; simulations use public FARGO3D  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2018.A.00030.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: FARGO3D parameter files
- Missing: Digitized exoALMA pressure profiles
- Data volume (inferred): small (<1 GB; ALMA data only for a figure)
- Score (inferred): 3/5, Simulation setup largely specified and equations given, but FARGO3D settings and exoALMA inputs incomplete; ALMA data minor.
- Rediscovery candidate: no, Main results come from simulations, not ALMA data reduction.

## Links

- Method: (cite: bitsch2018) (Pebble-isolation mass prescription)
- Method: (cite: lau2024) (Planetesimal collapse probability)
- Companion: (cite: Stadler2025) (exoALMA pressure gradients and ring/gap locations)
- Companion: (cite: Fasano2025) (PDS 70 ring locations)
- Related: exoALMA
- Related: DSHARP

## Checks

```json
{
 "quotes": 40,
 "quotes_ok": 40,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 29,
  "rate": 0.403
 },
 "evidence_ok": true
}
```
