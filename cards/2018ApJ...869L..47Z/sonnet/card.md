# The Disk Substructures at High Angular Resolution Project (DSHARP). VII. The Planet-Disk Interactions Interpretation

`2018ApJ...869L..47Z` | The Astrophysical Journal Letters 2018 | first author: Zhang, Shangjia | arXiv: 1812.04045 | DOI: 10.3847/2041-8213/aaf744

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: protoplanetary_disks
- Question: What planet masses and orbits could explain the gaps and rings in the DSHARP disks, and what young wide-orbit planet population results if the gaps are planet-induced?  
  > "To explore the properties of planets that may be responsible for these substructures, we systematically carry out a grid of 2-D hydrodynamical simulations including both gas and dust components." (abstract)
- Target **DSHARP disks (AS 209, Elias 24, Elias 27, GW Lup, HD 142666, HD 143006, HD 163296, SR 4, DoAr 25, Elias 20, IM Lup, RU Lup, Sz 114, Sz 129)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.00484.L
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
- External data: Observed azimuthally averaged radial intensity profiles of the DSHARP disks  
  > "We use the measured radial intensity profiles from Figure 2 in (cite: huang18b)." (Planet Properties) [from Huang et al. 2018a (cite: huang18b)]
- External data: Stellar luminosities and masses of DSHARP sources  
  > "We calculate $T_{d}(r)$ for each DSHARP source using the stellar properties ($L_*$) listed in (cite: andrews18b)." (Method) [from Andrews et al. 2018 (cite: andrews18b)]
- External data: DSHARP dust opacity table (0.43 cm2/g for smax=0.1 mm, 0.46 for 1 cm at 1.27 mm)  
  > "the absorption opacity for the $s_{max}=$0.1 mm case is 0.43 $\mathrm{cm^2\,g^{-1}}$, while for the $s_{max}=$1 cm case it is 0.46 $\mathrm{cm^2\,g^{-1}}$ based on (cite: birnstiel18)" (Method) [from Birnstiel et al. 2018 (cite: birnstiel18)]
- Simulation/model as data: Grid of 45 2-D Dusty FARGO-ADSG hydrodynamical simulations (h/r, alpha, q), scaled to 12 mm intensity maps each  
  > "we have 45 simulations with different $h/r$, $\alpha$, and $M_p$. For each simulation, we generate seven continuum maps for seven $\Sigma_{g,0}$" (Simulation Results)

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

- Radial intensity profile generation (deprojection and azimuthal averaging)  
  > "Details regarding generating the radial intensity profiles are given in (cite: huang18b)." (Planet Properties) [from (cite: huang18b)]
- Synthetic visibilities imaged as DSHARP sources  
  > "The resulting synthetic visibilities are imaged in the same manner as the DSHARP sources, as described in (cite: andrews18b)." (Discussion) [from (cite: andrews18b)]
- Gap width/depth fitting approach  
  > "Overall, our fitting follows (cite: kanagawa_width) and (cite: kanagawa_depth) but extend those relationships to dust particles with different sizes." (Simulation Results) [from (cite: kanagawa_width; kanagawa_depth)]

### Not stated but needed to reproduce (our reading)

- Exact Dusty FARGO-ADSG code version and setup files
- Random seeds for the super-particle initial conditions
- Details of the by-eye matching for narrow gaps
- Exact gap identification and edge measurements in the observed profiles

## Analysis recipe

1. **Run hydrodynamical grid**: 2-D gas plus Lagrangian dust particle simulations, no dust feedback, run 1000 orbits  
  > "We carry out 2-D hydrodynamical planet-disk simulations using the modified version of the grid-based code FARGO (cite: masset2000) called Dusty FARGO-ADSG" (Method)
   - software: Dusty FARGO-ADSG
   - parameter: h/r = 0.05, 0.07, 0.1; alpha = 1e-4, 1e-3, 1e-2; q = 3.3e-5 to 3.3e-3  
  > "Thus, we have 45 simulations in total." (Method)
   - assumption: Locally isothermal, Sc=1, dust-to-gas 1/100, rho_p = 1 g cm-3  
  > "We set $Sc=1$ which serves as a good first order approximation" (Method)
   - fitting: _not stated_
   - validation: _not stated_
2. **Compute synthetic mm intensity maps**: Scale surface density and dust size distribution (DSD1, DSD2), assign DSHARP opacities, compute optical depth and brightness temperature, convolve with Gaussian beams  
  > "Finally, we convolve these intensity maps with two different Gaussian beams. The beam size is $\sigma=0.06 r_p$ and $\sigma=0.025 r_p$ respectively." (Method)
   - assumption: Rayleigh-Jeans for the scale-free maps; Td from L* with phi = 0.02  
  > "$\phi$ is a constant of 0.02 coming from an estimate from Figure 3 in (cite: dalessio01)" (Method)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit gap depth/width/secondary gap relations**: Least squares power-law fits of width vs K', depth-1 vs K, and secondary gap position, with degeneracy parameters optimized  
  > "Similarly, a least squares fitting was done to minimize the sum of the square difference of the vertical distance between the points and the linear-regression line log($\Delta$) vs. log(K’)." (Simulation Results)
   - fitting: Uncertainty from 15.9 and 84.1 percentiles of horizontal offsets  
  > "the left side error is estimated by the 15.9 percentile of the distribution and the right side error is 84.1 percentile of the distribution." (Simulation Results)
   - validation: _not stated_
4. **Infer planet masses for DSHARP gaps**: Measure observed gap widths, estimate gas surface density from outer-disk dust surface density, compute Stokes number, use width-K' relation, break degeneracy with h/r and alpha  
  > "Third, with known $\Sigma_{g,0}$ and the assumed dust size distribution, we can calculate $St_{max}$ and use the $\Delta$-$K'$ relationship" (Planet Properties)
   - assumption: GI limit with Toomre Q=1 caps gas surface density; preferred alpha=1e-3 and DSD1  
  > "we prefer $M_{p,am3}$ with DSD1 size distribution." (Planet Properties)
   - fitting: _not stated_
   - validation: Consistency check with assumed mass, kinematics, asymmetry, depth  
  > "We can also do a consistency check with the derived $M_p$." (Planet Properties)
5. **Synthetic observations of Solar System and HR 8799 analogs**: CASA simobserve with DSHARP-like configurations, imaged as DSHARP  
  > "Then, we use the `CASA` `simobserve` task to generate synthetic observations with sensitivities and angular resolutions comparable to those of the DSHARP observations" (Discussion)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **Dusty FARGO-ADSG** : hydrodynamical gas and dust simulations  
  > "`Dusty FARGO-ADSG` (cite: baruteau2008a; baruteau2008b; baruteau2016)" (Software)
- **CASA** : simobserve synthetic observations  
  > "we use the `CASA` `simobserve` task to generate synthetic observations" (Discussion)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Sub/super-Keplerian amplitude fit | Δδv_rot = 0.11 K_vr^0.80, K_vr = q (h/r)^-1.27 alpha^-0.41 | log10(K_vr) +0.103/-0.099 | dimensionless | 3 | $$\Delta\delta v_{rot} = 0.11 K_{v_r}^{0.80} \label{eq:Kvr}\,.$$ |
| Secondary gap position fit | 1 - r_IG2/r_p = 2.3 q^0.02 (h/r)^0.58 alpha^-0.01 | not stated | dimensionless | 3 | $$\label{eq:secondary_gap_fit} |
| Occurrence rate of >5 MJ planets beyond 5-10 au | 1/18 (6%) | not stated | percent | 4 | the occurrence rate for $>$5 $M_J$ planets beyond 5-10 au is 1/18 or 6%. |
| Occurrence rate of 0.2-5 MJ planets beyond 5-10 au | 8/18 (44%) | not stated | percent | 4 | The occurrence rate for 0.2 $M_J\lesssim M_p\lesssim$ 5 $M_J$ planets beyond 5-10 au is 8/18 or 44% |
| HD 143006 22 au gap planet mass (alpha=1e-3, DSD1) | 19.91 | not stated | M_Jup | 4 | HD 143006 / 1.78 / 22 / 0.62 |

## Qualitative findings

- Gap shapes depend mainly on the maximum Stokes number of the dust, so the relations transfer to other surface densities and size distributions  
  > "different disks with different surface densities and different dust size distributions have the same gap shape as long as their Stokes numbers for the maximum-size particles" (Conclusion)
- Uranus and Neptune analogs are not detectable with DSHARP-like observations  
  > "Thus, Uranus and Neptune in our Solar System analogs are not detectable with DSHARP." (Discussion)

## Claim tuples

- H: A single planet can explain the multiple gaps in AS 209 | E: Simulations with q=1e-4 at 99 au, alpha=1e-5 or radially varying alpha | R: Reproduces gaps at 24, 35, 62, 90 and 105 au | F: AS 209 is the most plausible case of a planet in a gap | **supported**
- H: Wide-orbit giant planet occurrence from DSHARP gaps agrees with direct imaging | E: Count inferred planets over 18 single-star disks | R: 1/18 for >5 MJ | F: Consistent with direct imaging constraints | **supported**
- H: DSHARP can detect young Solar System and HR 8799 analogs | E: simobserve synthetic observations | R: Jupiter/Saturn gap and HR 8799 gap detectable; Uranus/Neptune barely | F: Partial detectability | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Other gap mechanisms (ice lines, dead zone edges, zonal flows, SGI, disk winds) not excluded  
  > "there are many other possible mechanisms to produce gaps and rings, such as ice lines" (Caveats)
- How they decided it was enough: _not stated_
- Limitation (authors): Gap profiles fitted at fixed 1000 orbits; dust feedback ignored  
  > "Another major caveat in this work is that we fit the gap profiles at 1000 planetary orbits." (Caveats)
- Limitation (authors): Occurrence rates are upper limits since gaps may not be planetary  
  > "our derived planet occurrence rates should be considered as the upper limits." (Young Planet Population)
- Caveat (inferred, ours): Planet masses depend strongly on assumed alpha, dust size and gas density, uncertain by about 10x
- Caveat (inferred, ours): Single-time snapshot and passive dust
- Caveat (inferred, ours): Small sample statistics (18 disks)

## Reproducibility

- Data public (paper): Uses DSHARP intensity profiles from Huang et al. 2018; ALMA project cited  
  > "This paper makes use of ALMA data ADS/JAO.ALMA #2016.1.00484.L." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Simulation code configuration and outputs
- Missing: Observed profile values (in Huang et al. 2018)
- Data volume (inferred): Simulations only; ALMA profiles taken from a companion paper (small).
- Score (inferred): 3/5, Methods and fits are detailed, but the simulation code setup is not released and ALMA data enter only via published profiles.
- Rediscovery candidate: no, Main results come from a custom hydrodynamics grid, not from reprocessing public ALMA data.

## Links

- Method: Kanagawa et al. 2015, 2016 (gap depth/width fitting framework)
- Method: Birnstiel et al. 2018 (DSHARP opacities)
- Companion: Andrews et al. 2018 (DSHARP I) (sample and imaging)
- Companion: Huang et al. 2018a (radial intensity profiles)
- Companion: Guzman et al. 2018 (AS 209 gaps)
- Companion: Dullemond et al. 2018 (ring widths and alpha/St)
- Related: DSHARP

## Checks

```json
{
 "quotes": 38,
 "quotes_ok": 38,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 27,
  "rate": 0.355
 },
 "evidence_ok": true
}
```
