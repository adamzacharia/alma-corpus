# ALMA Observations of SMM11 Reveal an Extremely Young Protostar in Serpens Main Cluster

`2017ApJ...850L...2A` | The Astrophysical Journal Letters 2017 | first author: Aso, Yusuke | arXiv: 1710.10787 | DOI: 10.3847/2041-8213/aa9701

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Is SMM11 in Serpens Main a first hydrostatic core or an extremely young Class 0 protostar just after the second collapse?  
  > "The low $L_{\rm int}$, $T_{\rm bol}$, $X$(C$^{18}$O) values and spherical envelope of SMM11 are consistent with theoretical predictions of the FHSC phase." (Is SMM11 a FHSC?)
- Target **SMM11**: coordinates 18h30m00.38s, 1d11m44.55s (J2000, observing coordinate center)  
  > "Coordinate center (J2000)" (Table 1); "Detection limits in various wavelengths are affected by the long distance, 429 pc, of SMM11." (Is SMM11 a FHSC?); z/distance 429 pc  
  > "Coordinate center (J2000)" (Table 1); "Detection limits in various wavelengths are affected by the long distance, 429 pc, of SMM11." (Is SMM11 a FHSC?); distance from _not stated_

## Data provenance

- ALMA projects: _none stated_
- bands: 1.3 mm, Cycle 3  
  > "during its Cycle 3 at 1.3 mm" (abstract)
- frequencies and spectral setup: 12CO: 3840 channels, 117 MHz, 30.5 kHz; C18O: 1920 channels, 59 MHz; two continuum windows at 216-218 and 232-234 GHz  
  > "Two other spectral windows cover 216-218 GHz and 232-234 GHz, and used to measure the continuum emission." (2 ALMA OBSERVATIONS)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15 - 613 m (11 - 460 klambda)  
  > "Projected baseline length" (Table 1)
- angular resolution: ~0.5'' (~210 AU); continuum beam 0.58''x0.47''  
  > "an angular resolution of $\sim 0.5\ensuremath{''}\sim 210$ AU" (abstract)
- max recoverable scale: emission beyond 8.0'' (~3400 AU) resolved out by >~50%  
  > "Any emission beyond $8.0\ensuremath{''}\sim 3400$ AU was resolved out by $\gtrsim 50\%$ with the antenna configuration" (2 ALMA OBSERVATIONS)
- sensitivity: rms 0.074 mJy/beam continuum; 5.0 (12CO), 11 (C18O) mJy/beam  
  > "rms noise level (${\rm mJy~beam^{-1}}$)" (Table 1)
- time on source: 4.5 and 9.0 min on the two days  
  > "On-source observing time for SMM11 is 4.5 and 9.0 min in the first and the second days, respectively." (2 ALMA OBSERVATIONS)
- observing dates: 2016 May 19 and 21  
  > "using ALMA at its Cycle 3 stage on 2016 May 19 and 21." (2 ALMA OBSERVATIONS)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (230.538000 GHz)
- Line: C18O J=2-1 (219.560358 GHz)
- Other facility **Spitzer and Herschel**: Near/mid-IR flux densities for the SED, Tbol, Lbol  
  > "we measured the flux density at near and mid-infrared wavelengths using $Spitzer$ and $Herschel$." (3 RESULTS)
- External data: Additional SED wavelengths from the literature  
  > "with other wavelengths in the literature, using $3\sigma$ upper limits for the integration where necessary." (3 RESULTS) [from not stated]
- External data: Dust opacity (kappa850=0.035 cm2/g, beta=1)  
  > "dust opacity, $(\kappa_{850 \mu {\rm m}},\beta)=(0.035\ {\rm cm}^{2}\,{\rm g}^{-1},1)$ (cite: an.wi2005)" (3 RESULTS) [from (cite: an.wi2005)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan  
  > "Flux calibrator" (Table 1)
- flux scale uncertainty: _not stated_
- self calibration: Self-calibration of continuum with clean, gaincal, applycal; rms improved ~2x; tables applied to line data  
  > "This improved the rms noise level of the continuum maps by a factor of $\sim 2$." (2 ALMA OBSERVATIONS)

### Imaging

- task: CASA CLEAN  
  > "All the imaging processes were performed with the Common Astronomical Software Applications (CASA)." (2 ALMA OBSERVATIONS)
- deconvolver: _not stated_
- weighting robust: Briggs, robust 0.0  
  > "CLEANed with Briggs weighting, a robust parameter of 0.0, and a threshold of 3$\sigma$." (2 ALMA OBSERVATIONS)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: Multi-scale CLEAN for line maps; point sources or ~1.5'' Gaussians  
  > "where CLEAN components were point sources or $\sim 1.5\ensuremath{''}$ Gaussian sources." (2 ALMA OBSERVATIONS)
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Channels binned: 16 (12CO, 0.63 km/s), 2 (C18O, 0.083 km/s)  
  > "16 and 2 channels are binned for $^{12}$CO and C$^{18}$O lines" (2 ALMA OBSERVATIONS)
- final beam: 0.58x0.47 (-86), 0.62x0.51 (-83), 0.65x0.52 (-85) arcsec (P.A. deg) for continuum, 12CO, C18O  
  > "Beam (P.A.)" (Table 1)
- final rms: _not stated_

### Inherited from earlier work

- Wind-driven-shell fitting procedure to 12CO map and PV diagrams  
  > "as described in Appendix A of (cite: ye2017)" (4.1 12CO outflows) [from (cite: ye2017)]
- Dust temperature range 20-50 K  
  > "assuming a dust temperature, $T_{\rm dust}=$20-50 K (cite: ha2015)" (3 RESULTS) [from (cite: ha2015)]

### Not stated but needed to reproduce (our reading)

- CASA version
- Clean mask, image size and cell size
- Line-free channels and continuum subtraction details
- Self-calibration solution intervals
- Flux density scale uncertainty
- Spitzer/Herschel data products, aperture sizes and literature SED points
- Fit method/priors for wind-driven-shell and visibility fits
- Source of 429 pc distance

## Analysis recipe

1. **Image continuum and lines**: CASA CLEAN with Briggs weighting, self-calibration on continuum applied to lines  
  > "CLEANed with Briggs weighting, a robust parameter of 0.0, and a threshold of 3$\sigma$." (2 ALMA OBSERVATIONS)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Continuum flux and mass**: 2D Gaussian fit; mass from flux density  
  > "Two-dimensional Gaussian fitting to the 1.3 mm image provides an approximately circular deconvolved size" (3 RESULTS)
   - assumption: Tdust 20-50 K, kappa850=0.035, beta=1, gas-to-dust 100  
  > "a gas-to-dust mass ratio of 100" (3 RESULTS)
   - fitting: _not stated_
   - validation: _not stated_
3. **SED, Tbol and Lbol**: Aperture photometry on Spitzer/Herschel, trapezoidal integration of SED  
  > "calculated by trapezoidal integration directly from the SED" (3 RESULTS)
   - fitting: _not stated_
   - validation: _not stated_
4. **Outflow inclination**: Fit wind-driven-shell model to 12CO integrated intensity map and PV diagrams within 10''  
  > "We only used pixels within $10\ensuremath{''}$ in radius" (4.1 12CO outflows)
   - fitting: _not stated_
   - validation: Best-fit parabolas overlaid on the map  
  > "The best-fit parabolas are overlaid on Figure [1](#ch4:fig:11c)b" (4.1 12CO outflows)
5. **C18O abundance**: LTE optical depth from continuum and C18O peak intensities  
  > "under the LTE condition" (4.2 C18O abundance)
   - assumption: Tgas = Tdust = 20-50 K  
  > "when both gas and dust temperatures are 20-50 K" (4.2 C18O abundance)
   - fitting: _not stated_
   - validation: _not stated_
6. **Visibility amplitude fitting**: Fit Gaussian, power-law and combination to continuum visibility amplitudes  
  > "we fitted it with three different functions: Gaussian, power-law, and a combination of the two." (4.3 Continuum visibility)
   - software: MIRIAD
   - assumption: Tdust=30 K, kappa850=0.035, beta=1  
  > "if $T_{\rm dust}=30$ K" (4.3 Continuum visibility)
   - fitting: _not stated_
   - validation: Combination fits better than single functions  
  > "fits the visibility profile better than the other functions" (4.3 Continuum visibility)

## Software

- **CASA** : imaging and self-calibration  
  > "All the imaging processes were performed with the Common Astronomical Software Applications (CASA)." (2 ALMA OBSERVATIONS)
- **MIRIAD** : listed in Software section; use not stated  
  > "CASA, MIRIAD" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total 1.3 mm flux density | 164 | 1 | mJy | 2 | The derived total flux density, $164\pm 1\ {\rm mJy}$ |
| Total mass | 0.09-0.27 | not stated | Msun | 2 | corresponds to a total mass of 0.09-0.27 $M_{\ensuremath{\odot}}$ |
| Tbol | 26 | not stated | K | 3 | $T_{\rm bol}=$26 K |
| Lbol | <=0.9 | not stated | Lsun | 3 | $L_{\rm bol}\lesssim 0.9L_{\ensuremath{\odot}}$ |
| Lint | <=0.043 | not stated | Lsun | 3 | $L_{\rm int}\lesssim 0.043\ L_{\ensuremath{\odot}}$ |
| C18O systemic velocity | 9.1 | not stated | km/s | 0 | $9.1\ {\rm km~s^{-1}}$ and $0.8\ {\rm km~s^{-1}}$ |
| Outflow inclination (east lobe) | 77-79 | not stated | deg | 4 | $i=77\ensuremath{^\circ}$-$79\ensuremath{^\circ}$ |
| X(C18O) | (1.5-3.0)e-10 | not stated | dimensionless | 5 | $X({\rm C}^{18}{\rm O})$ is $\sim (1.5$-$3.0)\times 10^{-10}$ |
| Power-law index p+q | ~2.7 | not stated | dimensionless | 6 | The derived power-law index, $p+q\sim 2.7$ |

## Qualitative findings

- SMM11 has no 70 um or shorter-wavelength counterpart and drives a collimated outflow  
  > "SMM11 is a Class 0 protostar without any counterpart at 70 $\mu$m or shorter wavelengths." (abstract)

## Claim tuples

- H: SMM11 is an extremely young protostar | E: ALMA 1.3 mm, 12CO, C18O plus Spitzer/Herschel SED | R: Tbol 26 K, Lint<=0.043 Lsun, low C18O abundance, spherical envelope | F: Properties are FHSC-like | **supported**
- H: Outflow velocity matches FHSC predictions | E: Wind-driven-shell fit | R: v0~4 km/s/arcsec, few 10 km/s at few 1000 AU | F: Too fast for FHSC; SMM11 is a transitional object after second collapse | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Low luminosity could instead be from episodic accretion with low accretion rate  
  > "the low luminosity may be due to a low mass accretion rate during episodic accretion" (Is SMM11 a FHSC?)
- How they decided it was enough: _not stated_
- Limitation (authors): Long distance limits detection; 24 and 70 um contaminated by neighboring Class I source  
  > "Detection limits in various wavelengths are affected by the long distance, 429 pc, of SMM11." (Is SMM11 a FHSC?)
- Caveat (inferred, ours): Very short on-source time and one source
- Caveat (inferred, ours): Fit uncertainties not formally defined
- Caveat (inferred, ours): Inclination from simple model with sparse parameter ranges

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: CASA version and clean parameters
- Missing: SED photometry values
- Missing: Fit procedures
- Data volume (inferred): ~10-50 GB
- Score (inferred): 4/5, Data are an ALMA project with moderate imaging detail, but many analysis details are missing.
- Rediscovery candidate: no, Recipe is incomplete (imaging parameters, SED data, fit details) and partly relies on literature and other facilities.

## Links

- Method: (cite: ye2017) (Wind-driven-shell fitting procedure)
- Companion: (cite: aso2017) (Similar visibility analysis for L1527 IRS)

## Checks

```json
{
 "quotes": 55,
 "quotes_ok": 55,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2015.1.01478.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 39,
  "rate": 0.527
 },
 "evidence_ok": true
}
```
