# The physical and chemical structure of Sagittarius B2. IV. Converging filaments in the high-mass cluster forming region Sgr B2(N)

`2019A&A...628A...6S` | Astronomy and Astrophysics 2019 | first author: Schwörer, A. | arXiv: 1906.10979 | DOI: 10.1051/0004-6361/201935200

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism, astrochemistry
- Question: What are the filamentary structure and kinematics of Sgr B2(N), and can the converging filaments feed a central hub that may form a super stellar cluster?  
  > "We aim to characterize the filamentary structure of Sgr B2(N) and its kinematic properties using multiple molecular dense gas tracers." (abstract)
- Target **Sgr B2(N)**: coordinates RA(J2000)=17h47m19.887s, Dec(J2000)=-28d22m15.76s (phase center)  
  > "Sgr B2(N), with phase center at $\alpha$(J2000)=17$^{h}$47$^{m}$19$^{s}$.887, $\delta$(J2000)=$-$28$^\circ$22$'$15.76$''$" (2 ALMA observations); "located at a distance[^1] of $8.127 \pm 0.031$ kpc (cite: GravityCollaboration2018)" (1 Introduction); "For consistency with previous findings in the literature, for our calculations we used the distance $8.34 \pm 0.16$ kpc (cite: Reid2014)" (Footnote 1); z/distance 8.34 ± 0.16 kpc used for calculations  
  > "Sgr B2(N), with phase center at $\alpha$(J2000)=17$^{h}$47$^{m}$19$^{s}$.887, $\delta$(J2000)=$-$28$^\circ$22$'$15.76$''$" (2 ALMA observations); "located at a distance[^1] of $8.127 \pm 0.031$ kpc (cite: GravityCollaboration2018)" (1 Introduction); "For consistency with previous findings in the literature, for our calculations we used the distance $8.34 \pm 0.16$ kpc (cite: Reid2014)" (Footnote 1); distance from Reid et al. 2014 (cite: Reid2014)  
  > "Sgr B2(N), with phase center at $\alpha$(J2000)=17$^{h}$47$^{m}$19$^{s}$.887, $\delta$(J2000)=$-$28$^\circ$22$'$15.76$''$" (2 ALMA observations); "located at a distance[^1] of $8.127 \pm 0.031$ kpc (cite: GravityCollaboration2018)" (1 Introduction); "For consistency with previous findings in the literature, for our calculations we used the distance $8.34 \pm 0.16$ kpc (cite: Reid2014)" (Footnote 1)

## Data provenance

- ALMA projects: 2013.1.00332.S
- bands: Band 6 (211 to 275 GHz), spectral scan with 10 tunings  
  > "The chosen spectral scan mode surveyed the whole ALMA band 6 (211 to 275 GHz) with 10 different spectral tunings" (2 ALMA observations)
- frequencies and spectral setup: spectral resolution 0.5-0.7 km/s  
  > "providing a spectral resolution of 0.5–0.7 km s$^{-1}$" (2 ALMA observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: extended configuration, 34-36 antennas, baselines 30 to 650 m  
  > "34–36 antennas were used in an extended configuration with baselines in the range from 30 to 650 m" (2 ALMA observations)
- baselines: _not stated_
- angular resolution: 0.3''-0.7''; common restored beam 0.4'' (3300 au)  
  > "All the images were restored with a common Gaussian beam of 0.4$''$." (2 ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: June 2014 and June 2015 (Cycle 2)  
  > "In June 2014 and June 2015, Sgr B2 was observed with ALMA (Atacama Large Millimeter/submillimeter Array) during its Cycle 2." (2 ALMA observations)
- pi or archival as stated: _not stated_
- External data: Dust continuum map at 242 GHz, dense core catalog (radii, masses) from Paper II  
  > "where $M$ is the mass of the dense core and $r$ its radius (values reported in Paper II)." (3.3 Dense core properties) [from Sánchez-Monge et al. 2017 (Paper II) (cite: Sanchez2017)]
- External data: Dust opacity 0.899 cm2/g  
  > "a dust opacity of 0.899 cm$^2$/g (cite: Ossenkopf1994)" (3.2 Mass accretion rates) [from (cite: Ossenkopf1994)]
- External data: Stellar mass-luminosity relation  
  > "The stellar luminosity ($L$) for a given star of mass $M$ follows the relation (see (cite: Eker2018))" (Appendix F) [from (cite: Eker2018)]
- Simulation/model as data: 10^5 simulated clusters with 1-50000 stars, Kroupa IMF, used to derive cluster mass-luminosity relation  
  > "we simulated 10$^5$ clusters with a random amount of stars. The number of stars varies between 1 and $50000$, with masses from $0.1$ and $100$ M$_\odot$." (Appendix F)

## Processing

### Calibration

- pipeline or manual: calibration in CASA 4.4.0, details in Paper II  
  > "The calibration and imaging processes were carried out with CASA[^3] version 4.4.0." (2 ALMA observations)
- casa version: CASA 4.4.0  
  > "The calibration and imaging processes were carried out with CASA[^3] version 4.4.0." (2 ALMA observations)
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
- final beam: common Gaussian beam 0.4''  
  > "All the images were restored with a common Gaussian beam of 0.4$''$." (2 ALMA observations)
- final rms: _not stated_

### Inherited from earlier work

- Observation details, calibration and imaging  
  > "Further details of the observations, calibration, and imaging are provided in Paper II." (2 ALMA observations) [from Paper II (cite: Sanchez2017)]
- 242 GHz continuum map and core catalog  
  > "The dust continuum emission at 242 GHz (see Paper II)" (3 Filamentary structure) [from Paper II (cite: Sanchez2017)]
- Filament mass accounting following cylindrical model  
  > "Following (cite: Kirk2013), we calculate the mass accretion rate implied by our velocity gradients assuming a cylindrical model for our filaments." (3.2 Mass accretion rates) [from (cite: Kirk2013)]

### Not stated but needed to reproduce (our reading)

- Calibrators, flux scale and self-calibration (deferred to Paper II)
- Continuum subtraction method and line-free channels
- Weighting/robust, cell and image size, deconvolver
- Dust-continuum filament masking/aperture definitions for filament masses
- XCLASS parameters for synthetic spectra and for core temperatures (Möller et al. in prep)
- Exact line lists used in stacking and the 10-sigma selection per species
- Core radii used for luminosities (from Paper II)
- Gaussian fitting details and filament spine paths

## Analysis recipe

1. **Line stacking per species**: Correct for LSR velocity (~64 km/s), model synthetic spectrum with XCLASS to find bright lines (>10 sigma), cut subspectra, convert to velocity, resample and average  
  > "First (step A in the figure), we correct our observed data by the source LSR velocity, corresponding to about 64 km s$^{-1}$ for Sgr B2(N)." (Appendix A)
   - software: XCLASS, python (signal, numpy)
   - parameter: 10 sigma threshold; 250 bright lines for one species in 211-275 GHz  
  > "we identified 250 bright lines above a 10 $\sigma$ threshold in the frequency range 211 to 275 GHz" (Appendix A)
   - fitting: _not stated_
   - validation: Synthetic C2H3CN test: velocities recovered to ~98%, linewidths 82% when injected into observed data  
  > "we recovered the velocities of the two components with a high accuracy (about 98%). The derived linewidths are slightly larger than the original ones, resulting in an accuracy of 82%." (Appendix A)
2. **Identify filaments**: Trace peak-intensity ridge by visual inspection on stacked-cube peak maps, excluding optically thick central region  
  > "The identification of the filaments has been done tracing their peak intensity, starting at a position close to the dense hub and following the intensity ridge outwards by visual inspection." (3.1 Filament identification)
   - fitting: _not stated_
   - validation: Confirmed in peak maps of individual transitions  
  > "The identified filaments were also confirmed in peak intensity maps created from individual molecular transitions." (3.1 Filament identification)
3. **Filament kinematics**: PV cuts along spines (width 0.4''), Gaussian fits to spectra along filaments, linear fits for velocity gradients  
  > "A more detailed study of the velocity structure is obtained by producing position-velocity (pv) cuts along the filaments and by fitting Gaussian functions to the spectra." (3.2 Filament kinematics)
   - software: pvextractor-like approach
   - parameter: local gradients from linear fits in 0.014 pc sections  
  > "We study the variation of the velocity gradient along the filament by performing linear fits in 0.014 pc size sections" (Appendix D)
   - fitting: _not stated_
   - validation: Consistency between species  
  > "The velocity structure of each filament is consistent between different molecular species" (3.2 Filament kinematics)
4. **Filament mass and accretion rate**: Mass from 242 GHz dust continuum; accretion rate = gradient x mass / tan(alpha) per Kirk et al. cylindrical model  
  > "For the calculation of the mass accretion rates, we assumed a projection angle $\alpha$ of 45$^\circ$." (3.2 Mass accretion rates)
   - parameter: kappa=0.899 cm2/g, dust-to-gas 100, Td 50-100 K, alpha=45 deg  
  > "a dust opacity of 0.899 cm$^2$/g (cite: Ossenkopf1994), a dust-to-gas mass ratio of 100, and dust temperatures between 50–100 K" (3.2 Mass accretion rates)
   - assumption: Median gradient across species; optically thin dust  
  > "For the velocity gradient, we used the median of the values determined for all the species" (3.2 Mass accretion rates)
   - fitting: _not stated_
   - validation: Inclination sensitivity: 25 deg doubles, 65 deg halves  
  > "An angle of 25$^\circ$ roughly doubles our results, while an angle of 65$^\circ$ halves them." (3.2 Mass accretion rates)
5. **Filament stability**: Compare M/L with turbulent critical value 2 sigma^2/G  
  > "This results in a value of $(M/L)_\mathrm{crit}$ about ($4$– $30)\times10^3$ $M_\odot$ pc$^{-1}$." (3.2 Mass accretion rates)
   - fitting: _not stated_
   - validation: _not stated_
6. **Core luminosity, stellar mass and timescales**: XCLASS core temperatures, Stefan-Boltzmann luminosity, stellar mass from simulated cluster relation, free-fall times  
  > "We determined the temperatures of the dense cores (from Paper II) located within the filaments by fitting the spectral lines of different molecular species with the software XCLASS" (3.3 Dense core properties)
   - software: XCLASS
   - parameter: clusters within ±10% of core luminosity; median stellar mass  
  > "we extract all the simulated clusters with luminosities corresponding to the core luminosity, within a range of $\pm$10%." (Appendix F)
   - assumption: cores are spherical blackbodies  
  > "Considering them as spherical black bodies, the stellar luminosity is given by the Stefan-Boltzmann equation" (3.3 Dense core properties)
   - fitting: Linear fit to log(M/L) vs log L of simulated clusters  
  > "We fit a linear function to the relation and find" (Appendix F)
   - validation: Blackbody deviation <6% for N_H2 above ~5e23 cm-2  
  > "with deviations of less than 6%" (Appendix E)

## Software

- **CASA** 4.4.0: calibration and imaging  
  > "The calibration and imaging processes were carried out with CASA[^3] version 4.4.0." (2 ALMA observations)
- **XCLASS** : line identification, synthetic spectra, core temperatures  
  > "The assignment of transitions to molecular species is done using the software XCLASS" (Footnote 4)
- **pvextractor** : approach followed for PV cuts  
  > "following a similar approach to what is implemented in the python tool `pvextractor`" (Appendix C)
- **scipy, numpy, pandas, matplotlib, astropy, aplpy, seaborn** : analysis and plots  
  > "we used the python packages `scipy`, `numpy`, `pandas`, `matplotlib`, `astropy`, `aplpy` and `seaborn`." (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of filaments | 8 | not stated | dimensionless | 2 | In total, we identify eight arms or filaments |
| Velocity gradients along filaments | 20-100 | not stated | km/s/pc | 3 | We derive velocity gradients along the filaments of about 20–100 km s$^{-1}$ pc$^{-1}$ |
| Total accretion rate onto hub | 0.16 | not stated | Msun/yr | 4 | which result in a total accretion rate of 0.16 $M_\odot$ yr$^{-1}$ |
| Hub mass | 2000 (T=250 K) | not stated | Msun | 4 | central hub (with a mass of 2000 $M_\odot$, assuming a temperature of 250 K) |
| Stellar mass fraction in cores | mean 50%, median 44% | not stated | % | 6 | with a mean (median) value of 50% (44%) |
| Cluster M/L vs L relation | log(M/L)=-0.6 log(L)+0.5 | not stated | dimensionless | 6 | \mathrm{log} \: \left( \frac{M/M_\odot}{L/L_\odot} \right) = -0.6 \times
\mathrm{log} \left( \frac{L}{L_\odot} \right) + 0.5. |
| Linewidths | 3-8 | not stated | km/s | 3 | Typical linewidths range from 3 to 8 km s$^{-1}$ |

## Qualitative findings

- Molecules split into filamentary tracers and spherical/bubble-like tracers  
  > "whereas other molecules like (ethylcyanid) or (carbonylsulfid) trace instead a spherical or bubble-like shape" (3 Filamentary structure)
- Filaments are stable against radial collapse  
  > "the filaments in Sgr B2(N) seem to be stable under gravitational collapse" (3.2 Mass accretion rates)

## Claim tuples

- H: Do filaments converge on a hub and carry large velocity gradients? | E: Stacked-line maps, PV cuts, Gaussian and linear fits | R: Eight filaments with gradients 20-100 km/s/pc | F: Gradients are 10-100x larger than at ~1 pc scales, consistent with accretion | **supported**
- H: Can filament flows be explained by outflows or explosions instead? | E: Compare linewidths, tracers and morphology | R: Linewidths ~10x smaller, complex-molecule tracers, curved structures | F: Accreting filaments most plausible | **supported**
- H: Will cores merge in the hub while still gas-rich? | E: Compare free-fall collapse and infall timescales, stellar fractions | R: Stellar fraction ~50%; timescales comparable | F: A 'damp' merger; Sgr B2(N) may become a super stellar cluster | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Line stacking overcomes blending in a line-rich source  
  > "Line stacking improves the signal-to-noise ratio, as well as averaging out line blendings." (3 Filamentary structure)
- Alternative: Outflows or explosive events rejected  
  > "Explosion events such as that in Orion KL are also a doubtful explanation since they produce clear and straightforward radial structures." (4.1 Converging filaments)
- How they decided it was enough: _not stated_
- Limitation (authors): Line stacking may artificially broaden lines near the center  
  > "We note that the increase of linewidth toward the center may be partially caused by the line stacking method." (Footnote 6)
- Limitation (authors): Small statistics  
  > "Although our statistics are small, we see the trend that dense cores located closer to the central hub can be more massive" (4.2 High-mass cluster formation)
- Caveat (inferred, ours): Inclination fixed at 45 deg for all filaments, though the paper argues they differ in orientation
- Caveat (inferred, ours): Mass accretion assumes the whole filament mass is infalling
- Caveat (inferred, ours): Dust temperature uncertain (50-100 K) drives masses
- Caveat (inferred, ours): Blackbody luminosity attributed entirely to stars
- Caveat (inferred, ours): Filament tracing by eye, with no uncertainties

## Reproducibility

- Data public (paper): ALMA project data cited in acknowledgements  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00332.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Calibration/imaging details in Paper II
- Missing: Stacking tool code not released
- Missing: Core catalog and continuum map from Paper II
- Missing: XCLASS fit results (Möller et al. in prep)
- Data volume (inferred): Large: full band 6 line survey, likely hundreds of GB raw
- Score (inferred): 4/5, Data are public but the recipe depends on Paper II, an unreleased stacking tool, and unpublished XCLASS fits.
- Rediscovery candidate: no, Key inputs and the stacking code are not provided and filament identification is manual.

## Links

- Method: Sánchez-Monge et al. 2017 (Paper II) (cite: Sanchez2017) (Observations, calibration, imaging, continuum and core catalog)
- Method: Kirk et al. 2013 (cite: Kirk2013) (Cylindrical accretion model)
- Method: Möller et al. 2017 (cite: Moeller2017) (XCLASS)
- Companion: Schmiedeke et al. 2016 (Paper I) (Series paper)
- Companion: Pols et al. 2018 (Paper III) (Series paper)
- Related: Sgr B2 series (Papers I-III)

## Checks

```json
{
 "quotes": 66,
 "quotes_ok": 66,
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
  "facts": 83,
  "stated": 48,
  "rate": 0.578
 },
 "evidence_ok": true
}
```
