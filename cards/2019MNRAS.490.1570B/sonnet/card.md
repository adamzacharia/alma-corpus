# The peculiar chemistry of the inner ejecta of Eta Carina

`2019MNRAS.490.1570B` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Bordiu, Cristobal | arXiv: 1904.00256 | DOI: 10.1093/mnras/stz2621

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: evolved_stars, astrochemistry, stellar_physics
- Question: What are the spatial distribution, kinematics and chemistry of molecular gas and continuum in the inner ejecta of eta Car, and how do they relate to the 19th-century eruptions?  
  > "We analyse the spatial distribution and kinematics of the emission in the innermost region of the Homunculus, also providing hints on its chemistry" (1 Introduction)
- Target **eta Carinae**: coordinates RA 10h45m03.5362s, Dec -59d41m04.0534s (J2000)  
  > "$\eta$ Car is located at 2350$\pm$50 pc in the Carina arm (cite: 2006ApJ...644.1151S)" (1 Introduction); "$\alpha =10^\mathrm{h}45^\mathrm{m}03^\mathrm{s}.5362, \,\delta=-59^\circ 41\ensuremath{'} 04\ensuremath{''}.0534$ (J2000)" (footnote 2); z/distance 2350±50 pc; V_LSR -19.7 km/s  
  > "$\eta$ Car is located at 2350$\pm$50 pc in the Carina arm (cite: 2006ApJ...644.1151S)" (1 Introduction); "$\alpha =10^\mathrm{h}45^\mathrm{m}03^\mathrm{s}.5362, \,\delta=-59^\circ 41\ensuremath{'} 04\ensuremath{''}.0534$ (J2000)" (footnote 2); distance from Smith 2006 (2006ApJ...644.1151S)  
  > "$\eta$ Car is located at 2350$\pm$50 pc in the Carina arm (cite: 2006ApJ...644.1151S)" (1 Introduction); "$\alpha =10^\mathrm{h}45^\mathrm{m}03^\mathrm{s}.5362, \,\delta=-59^\circ 41\ensuremath{'} 04\ensuremath{''}.0534$ (J2000)" (footnote 2)

## Data provenance

- ALMA projects: 2016.1.00585.S
- bands: Band 7 (0.8 mm)  
  > "We make use of ALMA band 7 archival observations from project 2016.1.00585.S" (2 Data and overall results)
- frequencies and spectral setup: four 1 GHz spectral windows targeting CO 3-2, H13CN 4-3, HCN 4-3, HCO+ 4-3  
  > "The correlator was set to observe four simultaneous spectral windows of 1 GHz each" (2 Data and overall results)
- continuum bandwidth: _not stated_
- arrays: 41 12-m antennas  
  > "A total of 41 12-m antennas were used, providing a maximum baseline of 1.8 km." (2 Data and overall results)
- configurations: _not stated_
- baselines: maximum baseline 1.8 km  
  > "A total of 41 12-m antennas were used, providing a maximum baseline of 1.8 km." (2 Data and overall results)
- angular resolution: 0.17x0.13 arcsec, PA -60 deg  
  > "with a characteristic beam of 0.17$\times$0.13 arcsec (P.A. -60$^\circ$)" (2 Data and overall results)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 668 s integration  
  > "with an integration time of 668 s" (2 Data and overall results)
- observing dates: 2016 October 24  
  > "The source was observed on 2016 October 24 under excellent weather conditions" (2 Data and overall results)
- pi or archival as stated: Archival, PI G. Pech-Castillo  
  > "archival observations from project 2016.1.00585.S (P.I: G. Pech-Castillo)" (2 Data and overall results)
- Line: CO J=3-2 (345.795989 GHz)
- Line: H13CN J=4-3 (345.339769 GHz)
- Line: HCN J=4-3 (354.505475 GHz)
- Line: HCO+ J=4-3 (356.734223 GHz)
- External data: Dust temperature relation T_dust ≈ 13100 D(au)^-1/2  
  > "We took the equation by (cite: 2003AJ....125.1458S):" (5.1 Column densities) [from (cite: 2003AJ....125.1458S)]
- External data: Homunculus polar axis tilt of 49 deg used for inclination correction  
  > "the polar axis of the Homunculus is tilted by 49$^\circ$" (5.1 Column densities) [from (cite: 2006ApJ...644.1151S)]
- External data: Average H2 column density of ~1e22 cm-2 through Homunculus walls  
  > "provided an average H$_2$ column density through the walls of the Homunculus of around 10$^{22}$ cm$^{-2}$" (5.4 Mass estimates) [from (cite: 2005ASPC..332..294F; 2006ApJ...645L..41S)]

## Processing

### Calibration

- pipeline or manual: standard ALMA pipeline  
  > "Visibilities were reduced following the standard ALMA pipeline with CASA v.4.7.0 r38335." (2 Data and overall results)
- casa version: CASA 4.7.0 r38335  
  > "Visibilities were reduced following the standard ALMA pipeline with CASA v.4.7.0 r38335." (2 Data and overall results)
- pipeline version: _not stated_
- archive products used as is: QA2 products (four cubes and a continuum map)  
  > "The resulting QA2 products included four spectral cubes and a continuum map" (2 Data and overall results)
- flux calibrator: J1107-4449 (flux), J1047-6217 (phase), J0538-4405 (bandpass)  
  > "Quasars J1107-4449, J1047-6217 and J0538-4405 were used for flux, phase and bandpass calibration respectively." (2 Data and overall results)
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
- final beam: 0.17x0.13 arcsec (PA -60 deg)  
  > "with a characteristic beam of 0.17$\times$0.13 arcsec (P.A. -60$^\circ$)" (2 Data and overall results)
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- Imaging parameters of the QA2 products (weighting, robust, cell and image size, channel width)
- Continuum-free channels and continuum subtraction method
- Noise rms of the cubes and continuum map
- Exact regions and pixel positions used for column density extraction
- Excitation/radiative transfer code and partition functions used for column densities
- Velocity ranges and abundance ratios assumed for Peanut mass formula
- Method used to separate point source and extended component beyond single 2D Gaussian

## Analysis recipe

1. **Make peak-intensity and channel maps**: Use QA2 cubes, convert to brightness temperature, make peak maps and 20 km/s velocity-binned HCO+ maps  
  > "Fig. [4](#fig:fig5) presents intensity maps of HCO$^+$ integrated in velocity bins of 20 km s$^{-1}$ over the range (–80,+80) km s$^{-1}$." (3.1 Kinematics)
   - software: CASA
   - parameter: Tb = 1.22e6 S/(nu^2 theta_maj theta_min)  
  > "T_\mathrm{b} = 1.22\times10^6 \frac{S_\nu}{\nu^2\theta_\mathrm{maj}\theta_\mathrm{min}}" (2 Data and overall results)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure continuum point source and extended component**: Fit single 2D Gaussian to the point source and isolate the extended component  
  > "We attempted to isolate the point source emission by fitting it to a single 2D Gaussian." (2 Data and overall results)
   - fitting: single 2D Gaussian  
  > "We attempted to isolate the point source emission by fitting it to a single 2D Gaussian." (2 Data and overall results)
   - validation: Compared 1 arcsec2 aperture flux with previous literature  
  > "integrating a circular area of this size yields a flux of $38.9 \pm 0.6$ Jy, which is in very good agreement with previous results" (2 Data and overall results)
3. **Derive column densities and abundance ratios**: LTE, optically thin emission with radiative excitation; temperature from dust equilibrium; for the absorbing bullet full radiative transfer with LTE  
  > "For the emission lines we assumed that the gas is in local thermodynamic equilibrium (LTE), the emission is optically thin and that radiative excitation dominates over collisions" (5.1 Column densities)
   - parameter: Non-detections: 3 sigma level as intensity upper limit  
  > "we constrained the column densities of CO, HCN and H$^{13}$CN taking the 3$\sigma$ level as the line intensity upper limit" (5.3 Hints of chemical differentiation)
   - assumption: Gas temperature equals dust temperature, T_dust = 13100 D^-1/2 K  
  > "If gas and dust are thermally coupled, gas temperature may be approximated by the dust temperature." (5.1 Column densities)
   - assumption: Peanut distance approximated by projected distance, giving upper limit T ~500 K  
  > "This allows us to approximate the real distance by the projected distance." (5.1 Column densities)
   - fitting: _not stated_
   - validation: Compared with APEX column densities (factor 3-5 lower) and Mangum 2017 Herschel-based values  
  > "our column densities are consistently lower than those reported by (cite: 2012ApJ...749L...4L) by a factor of 3–5" (5.1 Column densities)
4. **Estimate masses**: Convert CO column to H2 with [CO]/[H2]=1e-4 for torus; express Peanut mass as function of HCO+ abundance  
  > "For the torus, a standard \[CO\]/\[H$_2$\] abundance of 10$^{-4}$ yields a mass of 0.07$\pm$0.02 $\mathrm{M}_{\ensuremath{\odot}}$." (5.4 Mass estimates)
   - assumption: HCO+ reference abundance 1e-8  
  > "by taking a reference value of 10$^{-8}$" (5.4 Mass estimates)
   - fitting: _not stated_
   - validation: Compared with torus mass 0.2-1 Msun from Smith 2018  
  > "constrained the mass of the torus to 0.2–1 $\mathrm{M}_{\ensuremath{\odot}}$" (5.4 Mass estimates)

## Software

- **CASA** 4.7.0 r38335: ALMA pipeline reduction of visibilities  
  > "Visibilities were reduced following the standard ALMA pipeline with CASA v.4.7.0 r38335." (2 Data and overall results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HCO+ peak intensity of the Peanut | 77.5 | ±6.8 | K | 1 | with a peak intensity of $77.5\pm6.8$ K |
| Point source peak intensity | 6.41 | ±0.02 | Jy/beam | 2 | The peak intensity of the point source is $6.41 \pm 0.02$ Jy beam$^{-1}$ |
| Integrated flux of point-like source | 13.1 | ±0.5 | Jy | 2 | the integrated fluxes of the point-like and extended sources are $13.1\pm 0.5$ and $17.4\pm 1.1$ Jy, respectively |
| Integrated flux of extended source | 17.4 | ±1.1 | Jy | 2 | the integrated fluxes of the point-like and extended sources are $13.1\pm 0.5$ and $17.4\pm 1.1$ Jy, respectively |
| Flux in 1 arcsec2 circular aperture | 38.9 | ±0.6 | Jy | 2 | integrating a circular area of this size yields a flux of $38.9 \pm 0.6$ Jy |
| Deconvolved size of point source | 0.11 x 0.11 | not stated | arcsec | 2 | with a deconvolved size of $0.11 \times 0.11$ arcsec (i.e. 260 au) |
| N(HCO+) in the Peanut | 141.6e14 | ±4.4e14 | cm-2 | 3 | Peanut / 500 / (–66, +81) / $<0.56$ / $<0.81$ / $<0.87$ / $141.6\pm4.4$ |
| Torus mass for [CO]/[H2]=1e-4 | 0.07 | ±0.02 | Msun | 4 | a standard \[CO\]/\[H$_2$\] abundance of 10$^{-4}$ yields a mass of 0.07$\pm$0.02 |
| Peanut mass | (0.8±0.3) x X_HCO+/1e-8 | ±0.3 | Msun | 4 | M = (0.8\pm0.3) \times \frac{X_\mathrm{HCO^+}}{10^{-8}} \, \mathrm{M}_{\ensuremath{\odot}} |
| Excitation temperature of absorbing bullet | 500 | not stated | K | 3 | The continuum and excitation temperatures result to be 3390 and 500 K, respectively. |

## Qualitative findings

- Peanut is traced only by continuum and HCO+, with no CO, HCN or H13CN detected  
  > "The structure is only traced by continuum and HCO$^+$, and not detected in the other lines." (abstract)
- HCN/H13CN ratios are close to unity everywhere, implying very low 12C/13C  
  > "In every position, we measure \[HCN\]/\[H$^{13}$CN\] ratios close to unity." (5.2 Abundances in the torus)

## Claim tuples

- H: Is the Peanut ejecta from the 1890s eruption? | E: HCO+ velocity channel maps compared with Weigelt blobs and Fe structures | R: Blue and red arcs plus bar form a roughly conical structure of 0.6x0.4 arcsec | F: HCO+ gas likely arises from 1890s ejecta expanding within the wind-blown cavity | **supported**
- H: Is the Peanut chemically different from the torus? | E: LTE column densities at several positions | R: HCO+ enhanced to ~1e16 cm-2; CO, HCN, H13CN not detected | F: Peanut chemistry differs from Great Eruption ejecta | **supported**
- H: What is the HCN/H13CN absorption near the star? | E: Absorption and vibrationally excited lines analysis with full radiative transfer | R: Compact absorption at -60 km/s, v2=1 lines detected | F: Hot N-enriched bullet expelled at projected 40 km/s | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Absorbing gas as foreground cloud (obscuring debris) rejected because high excitation requires proximity to photosphere  
  > "prove that the absorbing gas is close to the photosphere rather than part of a foreground cloud" (6 Concluding remarks)
- How they decided it was enough: _not stated_
- Limitation (authors): Work at scales comparable to beam size; higher resolution needed  
  > "here we are working at scales comparable to the beam size" (3.1 Kinematics)
- Limitation (authors): Mass estimates must be regarded with caution  
  > "all these estimates must be regarded with caution" (5.4 Mass estimates)
- Caveat (inferred, ours): Single epoch, 668 s observation; no orbital phase coverage
- Caveat (inferred, ours): LTE and optically thin assumptions with dust temperature as gas temperature are weakly justified
- Caveat (inferred, ours): Kinematic cone model is qualitative, not fitted
- Caveat (inferred, ours): Peanut mass depends on unknown HCO+ abundance
- Caveat (inferred, ours): No uncertainty from systematic flux calibration

## Reproducibility

- Data public (paper): Archival ALMA data, project 2016.1.00585.S  
  > "We make use of ALMA band 7 archival observations from project 2016.1.00585.S" (2 Data and overall results)
- Products in archive: QA2 products used  
  > "The resulting QA2 products included four spectral cubes and a continuum map" (2 Data and overall results)
- Missing: Imaging parameters and rms
- Missing: Radiative transfer code details for column densities
- Missing: Extraction regions
- Data volume (inferred): ~5-20 GB (single short Band 7 execution, four 1 GHz windows)
- Score (inferred): 5/5, Public data and simple analysis, but column density and imaging details are sparse.
- Rediscovery candidate: yes, Public single-EB data and mostly numeric flux and column density results, though some settings need to be inferred.

## Links

- Companion: (cite: 2018MNRAS.474.4988S) (Earlier ALMA CO 2-1 torus detection)
- Companion: (cite: 2016MNRAS.462.3196G) (Fe structures and Weigelt blobs used for comparison)

## Checks

```json
{
 "quotes": 63,
 "quotes_ok": 63,
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
  "facts": 69,
  "stated": 41,
  "rate": 0.594
 },
 "evidence_ok": true
}
```
