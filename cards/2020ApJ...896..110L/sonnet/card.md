# ALMA Observations of NGC 6334S. I. Forming Massive Stars and Clusters in Subsonic and Transonic Filamentary Clouds

`2020ApJ...896..110L` | The Astrophysical Journal 2020 | first author: Li, Shanghuo | arXiv: 2003.13534 | DOI: 10.3847/1538-4357/ab84f1

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism
- Question: Are non-thermal motions in the massive IRDC NGC 6334S subsonic/transonic at high resolution, and what is the dynamical state of its dense cores and velocity components?  
  > "In this paper, we investigate the dynamical motions of identified embedded dense cores and their parent cloud, as well as the dynamical stability of dense cores." (1 Introduction)
- Target **NGC 6334S (IRDC G350.56+0.44)**: coordinates _not stated_; z/distance not stated (trigonometric parallax distance, ~20% uncertainty)  
  > "The proximity of NGC 6334S (cite: 2014ApJ...784..114C) makes it an ideal laboratory to investigate the key physical processes related to massive star and cluster formation." (1 Introduction); "The uncertainty in distance from the trigonometric parallax measurement is about 20% (cite: 2014ApJ...784..114C)." (3.3 Dense Core Properties); distance from Chibueze et al. 2014 (cite: 2014ApJ...784..114C)  
  > "The proximity of NGC 6334S (cite: 2014ApJ...784..114C) makes it an ideal laboratory to investigate the key physical processes related to massive star and cluster formation." (1 Introduction); "The uncertainty in distance from the trigonometric parallax measurement is about 20% (cite: 2014ApJ...784..114C)." (3.3 Dense Core Properties)

## Data provenance

- ALMA projects: 2016.1.00951.S
- bands: 3 mm continuum; lines near 86 GHz  
  > "Our 3 mm continuum image resolves 49 dense cores" (abstract)
- frequencies and spectral setup: Two 234.4 MHz windows for H13CO+ 1-0 and NH2D 1_11-1_01 (61 kHz resolution); three 1.875 GHz continuum windows at 88.5, 98.5, 100.3 GHz  
  > "We employed two 234.4 MHz wide spectral windows to cover the H$^{13}$CO$^{+}$ 1-0 (86.754 GHz) and NH$_{2}$D $1_{11}$-$1_{01}$ (85.926 GHz) lines, respectively" (2.1 ALMA Observations); "we centered three 1.875 GHz wide spectral windows at 88.5 GHz, 98.5 GHz, and 100.3 GHz to obtain broad band continuum data" (2.1 ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: 12-m main array, 55-pointing mosaic  
  > "We carried out a 55-pointings mosaic of the massive infrared dark cloud (IRDC), NGC 6334S" (2.1 ALMA Observations)
- configurations: _not stated_
- baselines: 15 to 155 m (~4.9-51 kλ)  
  > "The projected baseline lengths range from 15 to 155 meters" (2.1 ALMA Observations)
- angular resolution: Continuum 3.6"x2.4"; lines ~4.1"x2.8"  
  > "This yields a synthesized beam of 3$^{\prime\prime}$.6 $\times$ 2$^{\prime\prime}$.4" (2.1 ALMA Observations)
- max recoverable scale: _not stated_
- sensitivity: Continuum 0.03 mJy/beam; lines ~6 mJy/beam per 0.21 km/s channel  
  > "The 1$\sigma$ rms noise level is about 6 mJy beam$^{-1}$ per 0.21 km s$^{-1}$ channel" (2.1 ALMA Observations)
- time on source: 7.3 h total, 4.4 h on source  
  > "The overall observing time and the on-source integration time are 7.3 hours and 4.4 hours, respectively." (2.1 ALMA Observations)
- observing dates: 2017 March 13 to 21  
  > "between 2017 March 13 and 2017 March 21" (2.1 ALMA Observations)
- pi or archival as stated: PI Shaye Strom (other team's program)  
  > "ID: 2016.1.00951.S, PI: Shaye Strom" (2.1 ALMA Observations)
- Line: H13CO+ 1-0 (86.754 GHz)
- Line: NH2D 1_11-1_01 (85.926 GHz)
- Other facility **JVLA**: NH3 (1,1)-(5,5) mosaic for gas temperature  
  > "These observations simultaneously covered the NH$_{3}$ (1,1) through (5,5) metastable inversion transitions." (2.2 JVLA Observations)
- Other facility **Herschel/Planck/ATLASGAL**: Far-IR/submm data for SED fitting of column density and dust temperature  
  > "PACS 160 $\mu \rm m$, SPIRE 250 $\mu \rm m$ and the combined 870 $\mu \rm m$ data are used to fit the column density" (Appendix: Column density and dust temperature)
- External data: Distance by trigonometric parallax  
  > "The uncertainty in distance from the trigonometric parallax measurement is about 20% (cite: 2014ApJ...784..114C)." (3.3 Dense Core Properties) [from (cite: 2014ApJ...784..114C)]

## Processing

### Calibration

- pipeline or manual: Calibrated by ARC staff using CASA  
  > "The data calibrations were performed by the supporting staff at the ALMA Regional Center (ARC), using the CASA software package" (2.1 ALMA Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1733-1304 (absolute flux); J1617-5858 passband; J1713-3418 gain  
  > "We observed the quasars J1617-5858, J1713-3418, and J1733-1304, for passband, complex gain, and absolute flux calibrations, respectively." (2.1 ALMA Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5 (continuum and lines)  
  > "with a Briggs’s robust weighting of 0.5 to the visibilities" (2.1 ALMA Observations)
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
- final beam: 3.6"x2.4" PA 81 deg (continuum)  
  > "with a position angle (P.A.) of 81$^{\circ}$" (2.1 ALMA Observations)
- final rms: 0.03 mJy/beam continuum  
  > "1$\sigma$ root mean square (rms) noise level of 0.03 mJy beam$^{-1}$" (2.1 ALMA Observations)

### Inherited from earlier work

- Hyperfine fitting of NH3 (1,1),(2,2) follows earlier procedure  
  > "Details of the procedure have been provided in (cite: 2017ApJ...843...63F)." (2.3 Fitting molecular line spectra) [from (cite: 2017ApJ...843...63F)]
- SED fitting / image combination procedure  
  > "We adopted the image combination and SED fitting procedure presented in (cite: 2016ApJ...828...32L; 2017ApJ...840...22L)." (Appendix: Column density and dust temperature) [from (cite: 2016ApJ...828...32L; 2017ApJ...840...22L)]
- NH2D 36 hyperfine components  
  > "including its 36 hyperfine components (cite: 2016A&A...586L...4D)" (2.3 Fitting molecular line spectra) [from (cite: 2016A&A...586L...4D)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and continuum subtraction method for the line cubes
- CASA version and tclean parameters (cell, image size, masking, deconvolver, threshold)
- Primary beam correction details
- PySpecKit fitting initial guesses
- Mapping of dendrogram/imfit to final core table (imfit regions)
- Spatial smoothing used for the line-width vs beam size test
- How the NH3 temperature maps were regridded to cores
- Core line component assignment procedure and areas A_i
- Distance value adopted

## Analysis recipe

1. **identify dense cores in 3 mm continuum**: astrodendro leaves, properties measured with CASA imfit; extra >5 sigma sources added  
  > "We employed the `astrodendro`[^1] algorithm to pre-select dense cores (i.e., the leaves in the terminology of `astrodendro`) from the 3 mm continuum image" (3.1 Dense core identification)
   - software: astrodendro, CASA
   - parameter: min_value = 3 sigma, min_delta = 1 sigma, min_npix = 40  
  > "$\mathbf{min_{-}npix}$ = 40, which is approximately the synthesized beam area." (3.1 Dense core identification)
   - fitting: _not stated_
   - validation: _not stated_
2. **fit line profiles and velocity components**: Pixel-by-pixel Gaussian fits to H13CO+ and NH2D (hyperfine) cubes; NH3 (1,1),(2,2) jointly fit for temperature  
  > "We fit Gaussian line profiles to the H$^{13}$CO$^{+}$ image cube pixel by pixel, using the `PySpecKit` package" (2.3 Fitting molecular line spectra)
   - software: PySpecKit
   - parameter: peaks >5 sigma separated by >2 channels are independent components; keep sigma_obs>3 err, -8<=vlsr<=0 km/s, I>3 err  
  > "we regarded spectral peaks that are separated by more than 2 spectral channels and brighter than 5 times the rms noise level as independent velocity components" (2.3 Fitting molecular line spectra)
   - assumption: Uniform T = 15 K where NH3 unavailable  
  > "We use a uniform temperature of $\langle T_{\rm NH_{3}} \rangle$ = 15 K" (2.3 Fitting molecular line spectra)
   - fitting: Simultaneous multi-Gaussian least-squares (PySpecKit)  
  > "We then simultaneously fit Gaussian profiles to all of the independent velocity components." (2.3 Fitting molecular line spectra)
   - validation: Synthetic spectra smoothed to 0.21 km/s with noise, 1000 iterations, recovered input widths  
  > "The fitted line width agrees with the input line width, indicating that the measured line widths are not significantly affected by the current spectral resolution in this study." (Appendix: Simulation)
3. **non-thermal dispersion and Mach number**: sigma_nt from sigma_obs minus channel and thermal terms; Mach = sqrt3 sigma_nt / c_s  
  > "we also derived the Mach number, $\mathcal{M} = \sqrt{3} \sigma_{\rm nt}/c_{\rm s}$" (3.3 Line width and Mach number)
   - assumption: Mean gas mass 2.37 m_H; T from NH3 or 15 K  
  > "assuming a mean mass of gas of 2.37$\, m_{\rm H}$ (cite: 2008A&A...487..993K)" (3.3 Line width and Mach number)
   - fitting: _not stated_
   - validation: Tested T from 8 to 25 K  
  > "found that 56% to up to 99% of Mach numbers are smaller than 2" (4.1 sonic-to-transonic motion)
4. **core gas masses and densities**: Optically thin dust emission at 3 mm with Hildebrand opacity law; spherical density  
  > "assuming optically thin modified black body emission in the Rayleigh-Jeans limit" (3.3 Dense Core Properties)
   - parameter: kappa_98.5GHz = 0.235 cm2/g, beta = 1.5  
  > "We adopt $\kappa_{\rm 98.5\; GHz}$ = 0.235 cm$^{2}$g$^{-1}$" (3.3 Dense Core Properties)
   - assumption: Gas-to-dust ratio 100  
  > "where $\eta$ = 100 is the assumed gas-to-dust mass ratio" (3.3 Dense Core Properties)
   - fitting: _not stated_
   - validation: Error propagation gives 57% mass uncertainty  
  > "we estimate an uncertainty of 57% for the gas mass" (3.3 Dense Core Properties)
5. **virial parameters of decomposed structures**: Bertoldi & McKee virial mass with density power law and ellipsoidal geometry; component mass split by line intensity  
  > "The virial ratio is evaluated for each decomposed structure using (cite: 1992ApJ...395..140B)" (3.3 Dense Core Properties)
   - parameter: density profile index b = 1.6  
  > "we assume a typical density profile of $b$ = 1.6 for all decomposed structures" (3.3 Dense Core Properties)
   - assumption: Prolate cores; intrinsic axis ratio from observed via Appell function  
  > "the dense cores are likely prolate ellipsoids" (3.3 Dense Core Properties)
   - fitting: _not stated_
   - validation: Virial ratio uncertainty ~46%  
  > "the typical uncertainty is about 46% for the virial ratios" (3.3 Dense Core Properties)
6. **external pressure and energy budget**: P_cl = pi G Sigma_bar Sigma_r beta_cl with SED column density; compare Omega_P, Omega_G, Omega_K  
  > "$$P_{\rm cl} = \pi G \bar{\Sigma}\Sigma_{r}  \beta_{\rm cl},$$" (3.4 Pressure)
   - parameter: Mean cloud column density 0.15 g/cm2; Sigma_r = Sigma_obs/2  
  > "the mean column density of the cloud is about $\bar{\Sigma}$ = 0.15 g cm$^{-2}$ estimated from the SED fitting" (3.4 Pressure)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibration, imaging, imfit  
  > "obtained using the CASA-`imfit` task" (3.1 Dense core identification)
- **PySpecKit** : Gaussian/hyperfine line fitting  
  > "using the `PySpecKit` package" (2.3 Fitting molecular line spectra)
- **astrodendro** : Dense core identification  
  > "We employed the `astrodendro`[^1] algorithm to pre-select dense cores" (3.1 Dense core identification)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of dense cores | 49 | not stated | dimensionless | 1 | We identified 49 dense cores |
| Core gas mass range | 0.17 to 14 | 57% | Msun | 4 | The derived gas masses are between 0.17 and 14 $M_{\odot}$ |
| Mean Mach number (H13CO+) | 1.5 | not stated | dimensionless | 3 | The derived Mach numbers range from 0.02 to 6.3, with a mean value of 1.5. |
| Virial ratio, H13CO+ structures (67) | 0.1-9.7; mean 1.8, median 1.4 | ~46% | dimensionless | 5 | the virial ratios range from 0.1 to 9.7, with the mean and median value of 1.8 and 1.4, respectively |
| Mean external pressure P_cl/k_B (H13CO+) | 3.8e7 | not stated | K cm^-3 | 6 | $\langle P_{\rm cl}/k_{\rm B} \rangle =  3.8\times 10^{7} \, \rm K\, cm^{-3}$ |

## Qualitative findings

- Line widths increase with increasing beam size, suggesting poor resolution biases supersonic reports  
  > "It is clear that the line widths increase with increasing beam sizes." (4.1 sonic-to-transonic motion)

## Claim tuples

- H: Non-thermal motions in a massive IRDC are subsonic/transonic at ~0.02 pc | E: Gaussian fits of H13CO+ and NH2D cubes, Mach numbers with NH3 temperatures | R: ~77% of regions have M<=2; mean M 1.5 | F: Motions are predominantly subsonic and transonic, like low-mass clouds | **supported**
- H: Virial parameter depends on mass | E: Virial analysis of 67 H13CO+ and 45 NH2D structures | R: Inverse alpha_vir - M_gas relation | F: More massive structures are more gravitationally unstable | **supported**
- H: External pressure helps confine dense structures | E: Energy budget with cloud pressure | R: 79% bound with pressure vs 64% without; 14 remain unbound | F: External pressure plays a role in confinement | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: H13CO+ heavier than NH2D, better probe of non-thermal motions  
  > "and therefore is a better probe of the non-thermal gas motions" (3 Results and Analysis)
- How they decided it was enough: _not stated_
- Limitation (authors): Cannot discriminate causes of broad line widths in cores with the data at hand; filament pressure not computed  
  > "Unfortunately, we can not discriminate between these possibilities with the data at hand." (4.1 sonic-to-transonic motion); "We are not able to accurately compute the filament pressure" (4.2.1 H13CO+ decomposed structures)
- Caveat (inferred, ours): Mass assigned to velocity components by line intensity fraction is crude
- Caveat (inferred, ours): Fixed density slope and 15 K for much of the area
- Caveat (inferred, ours): Spatially unresolved motions only partly addressed
- Caveat (inferred, ours): Chemical segregation may bias virial masses
- Caveat (inferred, ours): Uniform single-component NH3 temperatures

## Reproducibility

- Data public (paper): ALMA data identified by project code; public status not stated  
  > "ID: 2016.1.00951.S, PI: Shaye Strom" (2.1 ALMA Observations)
- Products in archive: _not stated_
- Missing: Exact CASA imaging parameters and version
- Missing: Line-free channels
- Missing: Fitting initial conditions
- Missing: Adopted distance
- Missing: JVLA data details
- Data volume (inferred): ~50-200 GB for ALMA mosaic MS; JVLA additional
- Score (inferred): 3/5, Main steps are described with numbers, but imaging and fitting details are partly missing and the archive data must be reprocessed.
- Rediscovery candidate: yes, ALMA data are archival with a project code, dendrogram parameters and mass recipe are given, and results are numeric.

## Links

- Method: (cite: 2017ApJ...843...63F) (NH3 fitting procedure)
- Method: (cite: 1992ApJ...395..140B) (Virial analysis formalism)
- Related: JVLA 14A-241

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
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 81,
  "stated": 50,
  "rate": 0.617
 },
 "evidence_ok": true
}
```
