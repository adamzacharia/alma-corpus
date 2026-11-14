# The Peculiar Distribution of CH3CN in IRC +10216 Seen by ALMA

`2015ApJ...814..143A` | The Astrophysical Journal 2015 | first author: Agúndez, M. | arXiv: 1506.06951 | DOI: 10.1088/0004-637X/814/2/143

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars, astrochemistry
- Question: Where is CH3CN distributed in the envelope of IRC +10216 at sub-arcsec resolution, and where is it formed?  
  > "The bulk of the emission is distributed as a hollow shell located at just $\sim$2$''$ from the star, with a void of emission in the central region up to a radius of $\sim$1$''$." (abstract)
- Target **IRC +10216**: coordinates _not stated_; z/distance 130 pc; Vsys = -26.5 km/s  
  > "The adopted mass loss rate and distance are $2\times10^{-5}$ M$_{\odot}$ yr$^{-1}$ and 130 pc" (2 Excitation and radiative transfer model); distance from adopted from Agundez et al. 2012 envelope model  
  > "The adopted mass loss rate and distance are $2\times10^{-5}$ M$_{\odot}$ yr$^{-1}$ and 130 pc" (2 Excitation and radiative transfer model)

## Data provenance

- ALMA projects: 2011.0.00229.S
- bands: Band 6  
  > "The ALMA Cycle 0 observations of IRC +10216 were carried out in April 2012 using receiver band 6." (Observations)
- frequencies and spectral setup: 255.3-260.2 GHz; spectral resolution 0.98 MHz, channel spacing 0.49 MHz  
  > "within the spectral setup covering the 255.3-260.2 GHz frequency range" (Observations); "The adopted spectral resolution is 0.98 MHz, with a channel spacing of 0.49 MHz." (Observations)
- continuum bandwidth: _not stated_
- arrays: 16 antennas of 12m array  
  > "An array of 16 antennas with baselines ranging from 15.7 m to 384.1 m was used" (Observations)
- configurations: _not stated_
- baselines: 15.7 m to 384.1 m  
  > "An array of 16 antennas with baselines ranging from 15.7 m to 384.1 m was used" (Observations)
- angular resolution: 0.76" x 0.61"  
  > "The resulting synthesized beam is $0\mbox{\rlap{.}$''$}76\times0\mbox{\rlap{.}$''$}61$" (Observations)
- max recoverable scale: _not stated_
- sensitivity: 3.6 mJy/beam per 0.49 MHz channel  
  > "the final rms per 0.49 MHz channel is 3.6 mJy beam$^{-1}$" (Observations)
- time on source: three tracks of 21 min on source  
  > "three observing tracks of 21 minutes of correlations on source" (Observations)
- observing dates: April 2012  
  > "were carried out in April 2012 using receiver band 6" (Observations)
- pi or archival as stated: _not stated_
- Line: CH3CN J=14-13 (K=0-3) (~257.5 GHz)
- Other facility **IRAM 30m**: On-the-fly map at 257.5 GHz to estimate flux filtered out by ALMA and for short-spacing combination  
  > "We carried out observations with the IRAM 30m telescope in June 2014 to estimate the degree of flux that could have been filtered out by ALMA." (Observations)
- External data: Envelope physical model with revised inner density  
  > "We adopted the model of the envelope of (cite: agu2012), with the downward revision of the density of particles derived by (cite: cer2013) for the innermost layers" (2 Excitation and radiative transfer model) [from (cite: agu2012); (cite: cer2013)]
- External data: H2-CH3CN rotational collisional rate coefficients up to 140 K  
  > "We adopted the rate coefficients of pure rotational excitation through inelastic collisions with H$_2$ from the calculations by (cite: gre1986)" (2 Excitation and radiative transfer model) [from (cite: gre1986)]
- External data: Dipole moment 3.92197 D  
  > "the dipole moment of $3.92197\pm0.00013$ D measured by (cite: gad1995)" (2 Excitation and radiative transfer model) [from (cite: gad1995)]

## Processing

### Calibration

- pipeline or manual: Calibration with CASA; further processing with GILDAS  
  > "Calibration was done with the software CASA[^2] and further data processing was done using the package GILDAS[^3]." (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0854+201 (bandpass and amplitude); J0909+013 phase  
  > "the amplitude and phase were calibrated by observing J0854+201 and J0909+013 every 10 and 20 minutes, respectively." (Observations)
- flux scale uncertainty: 8 %  
  > "The uncertainty in the flux calibration is estimated to be 8 %." (Observations)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: Högbom clean, no support  
  > "Image deconvolution was carried out using the Högbom clean algorithm with no support" (Observations)
- weighting robust: _not stated_
- uv taper: Taper to simulate 5.9" x 3.0" beam (SMA comparison)  
  > "we have applied a tapering procedure to the ALMA data to suppress long baselines and simulate what would be seen with a synthesized beam of 5$''$9 $\times$ 3$''$0" (Results)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Line-free spectral windows near the CH3CN lines  
  > "The continuum was subtracted by carefully selecting spectral windows free of line emission located in spectral regions near the CH$_3$CN $J=14-13$ lines." (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: ALMA combined with IRAM 30m short spacings  
  > "we have combined the ALMA data with the IRAM 30m short-spacing data to include visibilities at shorter baselines" (Results)
- smoothing: _not stated_
- final beam: 0.76" x 0.61"  
  > "The resulting synthesized beam is $0\mbox{\rlap{.}$''$}76\times0\mbox{\rlap{.}$''$}61$" (Observations)
- final rms: 3.6 mJy/beam per 0.49 MHz channel  
  > "the final rms per 0.49 MHz channel is 3.6 mJy beam$^{-1}$" (Observations)

### Inherited from earlier work

- Part of the ALMA data previously presented  
  > "Part of these observations has been previously presented by (cite: cer2013) and by (cite: vel2015)." (Observations) [from (cite: cer2013); (cite: vel2015)]
- Envelope model parameters other than mass loss and distance  
  > "(see Table 9 of (cite: agu2012) for other parameters)" (2 Excitation and radiative transfer model) [from (cite: agu2012)]
- Initial abundances of chemical model  
  > "The initial abundances injected into the expanding envelope are taken from (cite: agu2012)" (3 Chemical model) [from (cite: agu2012)]
- Clumpiness parametrization  
  > "adopting the same parametric treatment of clumpiness of (cite: dec2010)" (3 Chemical model) [from (cite: dec2010)]

### Not stated but needed to reproduce (our reading)

- Channel ranges used for continuum subtraction
- Clean mask/iteration count, weighting, cell and image size
- How 30m and ALMA data were merged in GILDAS
- CASA version
- Description of the LVG code and fitting procedure for the abundance profile (no goodness-of-fit)
- Phase center coordinates

## Analysis recipe

1. **Calibrate and image CH3CN J=14-13**: CASA calibration, GILDAS continuum subtraction and Högbom clean  
  > "Calibration was done with the software CASA[^2] and further data processing was done using the package GILDAS[^3]." (Observations)
   - software: CASA, GILDAS
   - fitting: _not stated_
   - validation: Dirty beam sidelobes <10 % of main beam  
  > "The associated dirty beam has minor contributions from sidelobes (less than 10 % of the main beam" (Observations)
2. **Estimate flux filtered out by ALMA**: Compare IRAM 30m spectrum with ALMA spectrum integrated over 9.4" x 9.4"; combine with 30m short spacings  
  > "compared in Fig. [2](#fig:spectrum) with the ALMA spectrum integrated over a region $9\mbox{\rlap{.}$''$}4\times9\mbox{\rlap{.}$''$}4$" (Observations)
   - fitting: _not stated_
   - validation: Flux loss negligible at line edges, up to 30-40 % in central channels  
  > "it can be as high as 30-40 % in some channels located around the center of the $K$ lines" (Observations)
3. **Excitation and radiative transfer modelling of radial brightness**: Multi-shell LVG model with Gaussian-in-log-radius abundance profile, fit to observed J=14-13 radial brightness  
  > "we have carried out excitation and radiative transfer calculations based on a multi-shell LVG formalism." (2 Excitation and radiative transfer model)
   - parameter: Levels up to J=30 in ground and nu6=1 states; A:E ratio 1:1  
  > "We considered rotational levels within the ground and $\nu_6=1$ vibrational states up to $J=30$." (2 Excitation and radiative transfer model)
   - assumption: Distance 130 pc; mass loss 2e-5 Msun/yr; collisional rates scale as sqrt(T) above 140 K  
  > "extrapolated at higher temperatures assuming that the rate coefficients scale with the square root of temperature" (2 Excitation and radiative transfer model)
   - fitting: Best-reproducing profile chosen (method not stated)  
  > "The radial abundance profile which best reproduces the $J=14-13$ transition observed with ALMA" (2 Excitation and radiative transfer model)
   - validation: Compared azimuthally averaged radial brightness for each K component  
  > "The radial brightness distributions calculated for the various $K$ components of the $J=14-13$ transition are confronted with the observed ones" (2 Excitation and radiative transfer model)
4. **Compare with standard gas-phase chemical model**: Gas-phase network from UMIST and KIDA; initial radius 2e14 cm; N2 abundance 4e-5; cosmic-ray ionization rate 1.2e-17 s-1; clumpy variant  
  > "Here we have constructed a standard chemical model using a gas phase reaction network built up from the databases UMIST and KIDA" (3 Chemical model)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibration  
  > "Calibration was done with the software CASA" (Observations)
- **GILDAS** : Further data processing, imaging  
  > "further data processing was done using the package GILDAS" (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Synthesized beam | 0.76 x 0.61 | not stated | arcsec | 1 | The resulting synthesized beam is $0\mbox{\rlap{.}$''$}76\times0\mbox{\rlap{.}$''$}61$ |
| Peak abundance profile radius r0 | 1.2e16 | not stated | cm | 3 | $r_0=1.2\times10^{16}$ cm, $f(r_0)=5\times10^{-8}$ |
| Peak fractional abundance f(r0) relative to H2 | 5e-8 | not stated | dimensionless | 3 | reaches a maximum value of $5\times10^{-8}$ at 6$''$ |
| Delta log r | 0.45 (r<r0), 0.3 (r>r0) | not stated | dimensionless | 3 | $\Delta \log r=0.45$ for $r<r_0$ and 0.3 for $r>r_0$ |
| Maximum CH3CN volume density | ~0.02 at 2" | not stated | molecules cm-3 | 3 | reaching a maximum abundance of $\sim0.02$ molecules cm$^{-3}$ at 2$''$ from the star |
| Ring radius / inner hole | ~2 / ~1 | not stated | arcsec | 1 | the maximum of the emission appears as a ring with a radius of $\sim2''$ and that there is a hole within $\sim1''$ |
| Flux filtered out by ALMA in central channels | up to 30-40 | not stated | percent | 2 | it can be as high as 30-40 % in some channels |
| Chemical model underestimate of CH3CN abundance | > two orders of magnitude | not stated | dimensionless | 4 | Our chemical model underestimates the abundance of CH$_3$CN by more than two orders of magnitude |

## Qualitative findings

- Hollow shell at ~2" with a double-humped, non-uniform structure; the SMA compact distribution is explained by limited resolution  
  > "the compact emission distribution observed is probably a consequence of the limited angular resolution" (Results)

## Claim tuples

- H: CH3CN is concentrated near the star or in the ~15" shell like other molecules | E: ALMA band 6 J=14-13 imaging with 30m short-spacing check | R: Hollow shell at ~2" with hole within ~1" | F: CH3CN distribution differs from all other molecules seen in this source | **supported**
- H: Standard chemical models can reproduce the CH3CN distribution | E: Built gas-phase chemical model and compared to the LVG-derived abundance | R: Model puts bulk at ~15" and underestimates abundance by >2 orders of magnitude | F: Standard models fail; non-uniform envelope or grain-surface processes proposed | **supported**
- H: Earlier compact SMA CH3CN emission conflicts with the ALMA hollow shell | E: Tapered ALMA data to the SMA beam | R: Inner hole not resolved at that resolution | F: No conflict | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Högbom clean without support, since sidelobes are low and CH3CN structure is not simple  
  > "This choice is adequate because the sidelobes of the dirty beam are not important" (Observations)
- Alternative: Clumpy envelope scenario gives a compact distribution rather than a hollow shell; higher CR ionization rate is constrained by HCO+  
  > "although the distribution of molecules would appear compact around the star rather than as a hollow shell" (3 Chemical model)
- How they decided it was enough: _not stated_
- Limitation (authors): Smooth spherical shell model does not reproduce fine structure; infrared pumping only partly included  
  > "Our model of a smooth hollow spherical shell does not aim at reproducing these fine details" (2 Excitation and radiative transfer model)
- Caveat (inferred, ours): Abundance profile fit has no quantitative goodness of fit or uncertainties
- Caveat (inferred, ours): Spherical symmetry assumed despite arcs and spirals
- Caveat (inferred, ours): 30m data are low sensitivity, so flux recovery is only partial

## Reproducibility

- Data public (paper): ALMA project code printed in footnote; archive data  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00229.S." (footnote 1)
- Products in archive: _not stated_
- Missing: IRAM 30m data not stated as public
- Missing: LVG code not named
- Missing: Imaging parameters
- Data volume (inferred): ~10-30 GB for the Cycle 0 raw data
- Score (inferred): 4/5, Imaging recipe and model details are incomplete; the LVG fit is unspecified and requires 30m data.
- Rediscovery candidate: no, Modeling code is not named, the 30m data are not public, and the results rely on a custom fit.

## Links

- Method: (cite: agu2012) (Envelope model and chemical initial abundances)
- Companion: (cite: cer2013) (Earlier presentation of the same ALMA Cycle 0 data)
- Companion: (cite: vel2015) (Earlier presentation of part of the same ALMA data)

## Checks

```json
{
 "quotes": 60,
 "quotes_ok": 60,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 45,
  "rate": 0.643
 },
 "evidence_ok": true
}
```
