# A Complete ALMA Map of the Fomalhaut Debris Disk

`2017ApJ...842....8M` | The Astrophysical Journal 2017 | first author: MacGregor, Meredith A. | arXiv: 1705.05867 | DOI: 10.3847/1538-4357/aa71ae

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: debris_disks, stellar_physics
- Question: What is the complete millimeter structure of the Fomalhaut outer debris disk (geometry, eccentricity, width, azimuthal structure, apocenter glow), and what is the stellar flux at 1.3 mm?  
  > "These observations provide the first millimeter map of the continuum dust emission from the complete outer debris disk with uniform sensitivity, enabling the first conclusive detection of apocenter glow." (abstract)
- Target **Fomalhaut**: coordinates RA 22h57m39.449, Dec -29d37m22.687s (J2000), phase center corrected for proper motion  
  > "The phase center for the central pointing was $\alpha=22^\text{h}57^\text{m}39.449$, $\delta=-29\ensuremath{^\circ}37\ensuremath{'}22.687\ensuremath{''}$ (J2000)" (2 Observations); "where $D=7.66$ pc is the distance" (3.3 Results of Model Fits); z/distance 7.66 pc  
  > "The phase center for the central pointing was $\alpha=22^\text{h}57^\text{m}39.449$, $\delta=-29\ensuremath{^\circ}37\ensuremath{'}22.687\ensuremath{''}$ (J2000)" (2 Observations); "where $D=7.66$ pc is the distance" (3.3 Results of Model Fits); distance from not stated (the paper cites van Leeuwen 2007 for Fomalhaut's proximity but does not explicitly attribute the 7.66 pc distance)  
  > "The phase center for the central pointing was $\alpha=22^\text{h}57^\text{m}39.449$, $\delta=-29\ensuremath{^\circ}37\ensuremath{'}22.687\ensuremath{''}$ (J2000)" (2 Observations); "where $D=7.66$ pc is the distance" (3.3 Results of Model Fits)

## Data provenance

- ALMA projects: 2015.1.00966.S
- bands: Band 6 (1.3 mm, 223 GHz)  
  > "We observed the Fomalhaut system with ALMA in Band 6 (1.3 mm, 223 GHz)." (2 Observations)
- frequencies and spectral setup: Four basebands centered at 213.98, 215.98, 229.59, 231.48 GHz; the 12CO baseband has 3840 channels over 1.875 GHz (1.27 km/s); three continuum basebands have 128 channels and 2 GHz each  
  > "four basebands were centered at 213.98, 215.98, 229.59, and 231.48  GHz, in two polarizations." (2 Observations); "The remaining three continuum basebands included only 128 channels with a total bandwidth of 2 GHz each." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: 12-m antennas; 38 antennas (Dec 2015), 44-46 antennas (Jan 2016); seven-pointing mosaic  
  > "we constructed a seven pointing mosaic covering the star and the disk circumference." (2 Observations)
- configurations: _not stated_
- baselines: 15.1-331.0 m projected  
  > "$15.1-331.0$" (Table 1)
- angular resolution: 1.56'' x 1.15'' (12x9 AU), PA -87 deg, natural weighting  
  > "the synthesized beam size is $1.56\ensuremath{''}\times1.15\ensuremath{''}$ ($12\times9$ AU at 7.7 pc) with a position angle of $-87\ensuremath{^\circ}$" (3.1 Continuum Emission)
- max recoverable scale: _not stated_
- sensitivity: 14 uJy/beam rms  
  > "With natural weighting, the rms noise level is 14 $\mu$Jy/beam" (3.1 Continuum Emission)
- time on source: Seven executions of a 45 min SB (26.6-41.9 min on target each, per Table 1)  
  > "All of these seven pointings were observed within a single 45 minute scheduling block (SB), which was executed four times on 2015 December 29-30" (2 Observations)
- observing dates: 2015 Dec 29-30 (4 executions) and 2016 Jan 14 (3 executions)  
  > "An additional three executions were carried out on 14 January 2016 with $44-46$ antennas in the array and pwv $\sim2.4$ mm." (2 Observations)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (230.538 GHz)
- Other facility **HST/STIS**: Optical scattered-light image for overlay; background source position (GO-13726)  
  > "This region has been imaged with HST/STIS in the optical (GO-13726; PI Kalas)" (3.1 Continuum Emission)
- External data: ATCA 6.66 mm flux density used to derive mm spectral index  
  > "(cite: ric12) measured the flux density of Fomalhaut at 6.66 mm with ATCA." (4.1 Observational Evidence for Apocenter Glow) [from (cite: ric12)]
- External data: Dust opacity 2.3 cm^2/g at 1.3 mm  
  > "We assume a dust opacity at 1.3 mm of $\kappa_\nu = 2.3$ cm$^{2}$ g$^{-1}$ (cite: beck90)" (3.3 Results of Model Fits) [from (cite: beck90)]
- External data: Stellar Teff 8459+-44 K from CHARA and PHOENIX model prediction ~1.3 mJy at 1.3 mm  
  > "a PHOENIX stellar atmosphere model (cite: hus13) predicts a flux density of $\sim1.3$ mJy at 1.3 mm" (4.4 Stellar Emission at Millimeter Wavelengths) [from (cite: boy13); (cite: hus13)]
- External data: Apocenter/pericenter flux ratio simulation grid  
  > "A detailed description of the disk simulations is given by (cite: pan16)" (4.1 Observational Evidence for Apocenter Glow) [from (cite: pan16)]
- Simulation/model as data: Pan et al. grid of simulated Fomalhaut disks (3<=q<=4, 1<=beta<=3) for apocenter/pericenter flux ratios  
  > "We drew each model disk’s $q$ and $\beta$ values from a grid covering the ranges $3\leq q\leq 4$, $1\leq\beta\leq 3$." (4.1 Observational Evidence for Apocenter Glow)

## Processing

### Calibration

- pipeline or manual: Raw data processed by ALMA staff with CASA  
  > "The raw datasets were processed by ALMA staff using the `CASA` software package (version 4.5.2)." (2 Observations)
- casa version: CASA 4.5.2  
  > "The raw datasets were processed by ALMA staff using the `CASA` software package (version 4.5.2)." (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Pallas, J2357-5311, J2258-275; bandpass and gain from J2258-2758  
  > "The absolute flux calibration was determined from observations of Pallas, J2357-5311, and J2258-275, with a systematic uncertainty of $<10\%$." (2 Observations)
- flux scale uncertainty: <10%  
  > "with a systematic uncertainty of $<10\%$" (2 Observations)
- self calibration: _not stated_

### Imaging

- task: CASA CLEAN, multi-frequency synthesis, continuum  
  > "We generated continuum images using the multi-frequency synthesis `CLEAN` algorithm in `CASA`, and correct for the telescope primary beam." (2 Observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "With natural weighting, the rms noise level is 14 $\mu$Jy/beam" (3.1 Continuum Emission)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: Applied; FWHM ~26'' in Band 6  
  > "In Band 6, the primary beam of the ALMA 12-m antennas has FWHM$\sim26\ensuremath{''}$." (2 Observations)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.56'' x 1.15'', PA -87 deg  
  > "the synthesized beam size is $1.56\ensuremath{''}\times1.15\ensuremath{''}$" (3.1 Continuum Emission)
- final rms: 14 uJy/beam  
  > "the rms noise level is 14 $\mu$Jy/beam" (3.1 Continuum Emission)

### Inherited from earlier work

- Imaging of the 12CO data is described elsewhere  
  > "The imaging of the $^{12}$CO data is described in Matrà et al. (2017)." (2 Observations) [from Matrà et al. (2017)]
- Chi^2 visibility likelihood with statistical weights, as in earlier MacGregor work  
  > "Following our previous approach (cite: mac13; mac16b), we evaluate these model visibilities using a $\chi^2$ likelihood function" (3.2 Modeling Approach) [from (cite: mac13; mac16b)]
- Complex eccentricity plane populated following Wyatt et al.  
  > "We begin by populating the complex eccentricity plane defined by these four parameters following (cite: wya99)." (3.2 Modeling Approach) [from (cite: wya99)]
- Brightness temperature computed following Liseau et al.  
  > "To calculate the brightness temperature, we follow (cite: lis16)" (4.4 Stellar Emission at Millimeter Wavelengths) [from (cite: lis16)]

### Not stated but needed to reproduce (our reading)

- CLEAN parameters (cell size, image size, masks, threshold, niter)
- Mosaic pointing coordinates for the seven fields
- Prior ranges and walker/step numbers and burn-in for emcee
- Pixel scale, image size and the vertical/radial sampling of the model image and how the primary beam was handled in vissample
- Which executions were combined and any relative flux scaling between them
- Flux density used for the Pallas model/flux scale details
- Method for the Fomalhaut b 3-sigma upper limit and the apocenter/pericenter regions used for flux ratio

## Analysis recipe

1. **Image the continuum and characterize components**: Primary-beam-corrected multi-frequency synthesis CLEAN continuum image with natural weighting; identify ring, star and background source  
  > "Overall, the new ALMA image shows emission from three components: (1) a narrow, eccentric ring ($30\sigma$), (2) an unresolved central point source at the stellar position ($54 \sigma$)" (3.1 Continuum Emission)
   - software: CASA
   - parameter: natural weighting; rms 14 uJy/beam  
  > "With natural weighting, the rms noise level is 14 $\mu$Jy/beam" (3.1 Continuum Emission)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit background point source flux**: Point source model fit to visibilities  
  > "determined by fitting a point source model to the visibilities using the `uvmodelfit` task in `CASA`" (3.1 Continuum Emission)
   - software: CASA uvmodelfit
   - fitting: _not stated_
   - validation: Compared to source counts and to HST/STIS optical source position  
  > "it is likely the ALMA source is the same background object as observed in optical data." (3.1 Continuum Emission)
3. **Fit eccentric-ring particle model to visibilities**: 2D model of 10^4 particles with forced/proper eccentricity, random mean anomalies, solved Kepler's equation; binned to image; point-source star added; synthetic visibilities via vissample; chi^2 likelihood; emcee MCMC  
  > "To create our two-dimensional model, we complete this calculation for $10^4$ individual disk particles." (3.2 Modeling Approach)
   - software: ast2body newtonm, vissample, emcee
   - parameter: Free: R_belt, Δa, F_belt, F_star, i, PA, e_f, e_p, ω_f, Δα, Δδ  
  > "we fit for the geometry of the disk (inclination, $i$, and position angle, $PA$), as well as offsets of the stellar position from the pointing center" (3.2 Modeling Approach)
   - assumption: Negligible vertical thickness (opening angle ~1 deg); temperature T ∝ r^-0.5; ω_p random 0 to 2π  
  > "impose a radial temperature profile, $T\propto r^{-0.5}$" (3.2 Modeling Approach)
   - fitting: emcee affine-invariant ensemble sampler, chi^2 likelihood with visibility weights; priors not stated  
  > "This iterative process makes use of the `emcee` Markov Chain Monte Charlo (MCMC) package (cite: for13)." (3.2 Modeling Approach)
   - validation: Reduced chi^2 = 1.1; imaged residuals mostly noise  
  > "Table [2](#tab:diskpar) presents the best-fit model (reduced $\chi^2 = 1.1$) parameters" (3.3 Results of Model Fits)
4. **Derive dust mass**: Optically thin M_dust = F D^2/(kappa B(T))  
  > "$M_\text{dust} = F_\nu D^2/(\kappa_\nu B_\nu(T_\text{dust}))$" (3.3 Results of Model Fits)
   - assumption: kappa = 2.3 cm^2/g at 1.3 mm; T ~48 K radiative equilibrium; D = 7.66 pc  
  > "Given the best fit radial location of the disk, $136.3\pm0.9$ AU, the radiative equilibrium temperature is $\sim48$ K." (3.3 Results of Model Fits)
   - fitting: _not stated_
   - validation: Compared with previous flux measurements  
  > "consistent with previous flux measurements at slightly shorter wavelengths" (3.3 Results of Model Fits)
5. **Constrain grain size distribution and beta from apocenter/pericenter flux ratio**: alpha_mm from ALMA and ATCA fluxes gives q; compare observed flux ratios with Pan et al. simulation grid to bound beta  
  > "then $q = (\alpha_\text{mm} - \alpha_\text{Pl})/\beta_s + 3$ (cite: ric12; mac16a)" (4.1 Observational Evidence for Apocenter Glow)
   - assumption: alpha_Pl = 1.88+-0.02; beta_s = 1.8+-0.2; passively heated optically thin disks; T*=8590 K, R*=1.28e11 cm  
  > "Here, $\alpha_\text{Pl}=1.88\pm0.02$ (cite: mac16a), and $\beta_s = 1.8\pm0.2$" (4.1 Observational Evidence for Apocenter Glow)
   - fitting: _not stated_
   - validation: Consistent with White et al. 2016 q = 3.50+-0.14  
  > "This result is consistent with the determination of (cite: whi16) of $\alpha_\text{mm}=2.73\pm0.13$ and $q=3.50\pm0.14$." (4.1 Observational Evidence for Apocenter Glow)
6. **Search residuals and azimuthal profile for structure**: Subtract best-fit model, inspect imaged residuals; azimuthal mean brightness in 10 deg sectors with rms/sqrt(N beams) uncertainties  
  > "The mean brightness is calculated in small annular sections of $10\ensuremath{^\circ}$ around the ring" (4.2.1 Constraints on Azimuthal Belt Structure)
   - fitting: _not stated_
   - validation: _not stated_
7. **Limit Fomalhaut b dust mass and stellar brightness temperature**: 3-sigma point-source upper limit converted to dust mass (optically thin) or clump size (optically thick); stellar flux converted to brightness temperature  
  > "We can place a robust $3\sigma$ upper limit on the flux density of $0.042$ mJy, assuming a point source." (4.3 Implications for Fomalhaut b)
   - assumption: Fomalhaut b at ~125 AU, T_dust ~51 K; stellar photospheric radius 1.842 Rsun  
  > "this location implies a dust temperature of $\sim51$ K" (4.3 Implications for Fomalhaut b)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.5.2: Calibration by ALMA staff, CLEAN imaging, uvmodelfit  
  > "The raw datasets were processed by ALMA staff using the `CASA` software package (version 4.5.2)." (2 Observations)
- **vissample** : Compute synthetic model visibilities (python implementation of Miriad uvmodel)  
  > "we compute synthetic model visibilities using `vissample` [^1], a python implementation of the Miriad `uvmodel` task." (3.2 Modeling Approach)
- **emcee** : MCMC parameter exploration  
  > "This iterative process makes use of the `emcee` Markov Chain Monte Charlo (MCMC) package (cite: for13)." (3.2 Modeling Approach)
- **ast2body (newtonm)** : Solve for true anomaly  
  > "we iterate to find the true anomaly, $f$, using the `newtonm` code from `ast2body` (cite: val07)." (3.2 Modeling Approach)
- **corner.py** : Corner plots of MCMC output  
  > "Figures [6](#fig:ep) and [8](#fig:appendix) were generated using the `corner.py` code (cite: for16)." (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Rms noise | 14 | not stated | uJy/beam | 1 | the rms noise level is 14 $\mu$Jy/beam |
| Background source flux density | 0.150 | 0.014 | mJy | 2 | The total flux density for this source is $0.150\pm 0.014$ mJy |
| Belt total flux density | 24.7 | 0.1 (plus 10% calibration) | mJy | 3 | The total belt flux density determined for the best-fit model is $24.7\pm0.1$ mJy |
| Stellar flux density at 1.3 mm | 0.75 | 0.02 | mJy | 3 | $0.75\pm0.02$ |
| Belt semi-major axis (inner edge) R_belt | 136.3 | 0.9 | AU | 3 | $136.3\pm0.9$ |
| Belt FWHM width | 13.5 | 1.8 | AU | 3 | $13.5\pm1.8$ |
| Inclination | 65.6 | 0.3 | deg | 3 | $65.6\pm0.3$ |
| Position angle | 337.9 | 0.3 | deg | 3 | $337.9\pm0.3$ |
| Forced eccentricity | 0.12 | 0.01 | dimensionless | 3 | $0.12\pm0.01$ |
| Proper eccentricity | 0.06 | 0.04 | dimensionless | 3 | $\Delta a = 12.2\pm1.6$ AU and $e_p = 0.06\pm0.04$ |
| Argument of periastron | 22.5 | 4.3 | deg | 3 | $22.5\pm4.3$ |
| Range of semi-major axes Δa | 12.2 | 1.6 | AU | 3 | $12.2\pm1.6$ |
| Fractional width ΔR/R | 0.10 | 0.01 | dimensionless | 3 | $\Delta R/R = 0.10\pm0.01$ |
| Total dust mass | 0.015 | 0.010 | Earth masses | 4 | Thus, the total mass of the dust belt is $0.015\pm0.010$ $M_\oplus$. |
| Apocenter/pericenter flux ratio at 1.3 mm | 1.10 | 0.02 | dimensionless | 5 | including our new ALMA measurement at 1.3 mm of $1.10\pm0.02$ |
| Millimeter spectral index alpha_mm | 2.71 | 0.11 | dimensionless | 5 | we determine $\alpha_\text{mm} = 2.71\pm0.11$ and thus $q = 3.46\pm0.09$ |
| Size distribution index q | 3.46 | 0.09 | dimensionless | 5 | $\alpha_\text{mm} = 2.71\pm0.11$ and thus $q = 3.46\pm0.09$ |
| Dust absorptivity index beta | 0.9<beta<1.5 | 1 sigma range | dimensionless | 5 | The overlap between these indicates an allowed range of $0.9<\beta<1.5$ |
| Fomalhaut b 3-sigma flux upper limit | 0.042 | not stated | mJy | 7 | We can place a robust $3\sigma$ upper limit on the flux density of $0.042$ mJy, assuming a point source. |
| Fomalhaut b dust mass upper limit | <0.0019 M_Moon (<1.40e23 g) | not stated | Moon masses | 7 | The resulting upper limit on the dust mass is $<0.0019$ $M_\text{Moon}$ ($<1.40\times10^{23}$ g) |
| Stellar brightness temperature at 1.3 mm | <6200 | not stated | K | 7 | the brightness temperature dips to $<6600$ K and $<6200$ K at 870 $\mu$m and 1.3 mm, respectively. |

## Qualitative findings

- No azimuthal structure is seen in the residuals, including the HST 331 deg gap; structures <=10 AU cannot be excluded  
  > "the resulting residuals do not show any evidence for significant azimuthal structure." (Conclusions)
- An unresolved eastern source is attributed to a background galaxy  
  > "We attribute the unresolved point source in the southeast quadrant to a background galaxy." (3.1 Continuum Emission)

## Claim tuples

- H: Does the complete disk at 1.3 mm show apocenter glow? | E: Uniform-sensitivity mosaic and eccentric ring model; compare NW and SE flux | R: ~65 uJy (>5 sigma) NW-SE difference; flux ratio 1.10+-0.02 | F: First conclusive detection of apocenter glow | **supported**
- H: What are the belt geometry, width and eccentricity? | E: MCMC fit of eccentric particle model to visibilities | R: R_belt 136.3+-0.9 AU, width 13.5+-1.8 AU, e 0.12+-0.01, ω 22.5+-4.3 deg | F: Narrow, radially confined eccentric belt consistent with prior results | **supported**
- H: Are previously reported azimuthal features present? | E: Residual imaging and azimuthal profile | R: No significant peaks except the background galaxy | F: Previous HST, SCUBA, ALMA features not confirmed | **supported**
- H: Is the stellar 1.3 mm flux consistent with photospheric models? | E: Fit star as point source and compare with PHOENIX | R: 0.75+-0.02 mJy vs ~1.3 mJy predicted | F: Star is fainter than photospheric prediction | **supported**
- H: Can grain properties be constrained? | E: Combine alpha_mm with apocenter/pericenter ratios vs Pan et al. simulations | R: q = 3.46+-0.09, 0.9<beta<1.5 | F: beta constrained, consistent with Draine relation | **partially**

## Reasoning

- Why this data: Mosaic designed to cover the whole ring with equal sensitivity to examine azimuthal structure  
  > "The ALMA 1.3 mm mosaic map of the outer Fomalhaut debris disk was designed to cover the complete ring with equal sensitivity, allowing us to examine azimuthal structure along the belt." (4.2.1 Constraints on Azimuthal Belt Structure)
- Why this method: Mm observations trace large grains unperturbed by radiation forces; orbit-based model accounts for eccentric particle orbits  
  > "the large grains that emit predominantly at these wavelengths are not significantly perturbed by radiation forces and better trace the location of the larger planetesimals" (1 Introduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Resolution (~10 AU) prevents constraints on edge sharpness; Δa and e_p degenerate; large uncertainty on ω from inclination degeneracy  
  > "we are unable to place any strong constraints on the sharpness of the disk edges." (4.2.2 Determining the Belt Width)
- Limitation (authors): 2D model ignores vertical structure, which could loosen width constraints  
  > "Adding a vertical component to the model would likely loosen the constraints we are able to place on the width of the belt" (3.2 Modeling Approach)
- Caveat (inferred, ours): Dust mass depends on assumed opacity and temperature, giving a large systematic uncertainty
- Caveat (inferred, ours): beta upper bound set by grid range and assumed beta_s and q
- Caveat (inferred, ours): Quoted MCMC errors depend on unstated priors and the point-source/beam treatment of the star
- Caveat (inferred, ours): Different observing executions with different weather combined without stated relative scaling

## Reproducibility

- Data public (paper): ALMA project data acknowledged; vissample publicly available  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA #2015.1.00966.S." (Acknowledgments)
- Products in archive: _not stated_
- Code: vissample is public on GitHub; the eccentric-ring model code is not stated as released  
  > "`vissample` is publicly available at <https://github.com/AstroChem/vis_sample>" (footnote 1)
- Missing: Eccentric-ring model code and priors
- Missing: CLEAN parameters and mosaic field centers
- Missing: emcee configuration
- Data volume (inferred): ~10-50 GB raw for 7 executions with a mosaic (rough estimate)
- Score (inferred): 3/5, Data are archival and results numeric, but the custom model code, priors and imaging parameters are not given.
- Rediscovery candidate: no, The custom ring model code and MCMC priors are not provided, so the recipe is not complete enough for redoing.

## Links

- Method: (cite: wya99) (Complex eccentricity formalism for the model)
- Method: (cite: mac13; mac16b) (Visibility-based MCMC fitting approach)
- Method: (cite: pan16) (Apocenter glow simulations)
- Companion: Matrà et al. (2017) (12CO imaging of the same dataset)
- Companion: (cite: whi16) (Independent ALMA 233 GHz observation of Fomalhaut)
- Companion: (cite: su16) (ALMA Cycle 1 870 um observation)
- Related: HST GO-13726

## Checks

```json
{
 "quotes": 95,
 "quotes_ok": 95,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 21,
 "numeric_problems": 0,
 "fill": {
  "facts": 90,
  "stated": 62,
  "rate": 0.689
 },
 "evidence_ok": true
}
```
