# High-resolution observations of gas and dust around Mira using ALMA and SPHERE/ZIMPOL

`2018A&A...620A..75K` | Astronomy and Astrophysics 2018 | first author: Khouri, T. | arXiv: 1810.03886 | DOI: 10.1051/0004-6361/201833643

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars, astrochemistry
- Question: Constrain the distribution of gas and the composition and properties of dust grains forming in the inner circumstellar environment of Mira (o Cet)  
  > "Constrain the distribution of the gas and the composition and properties of the dust grains that form in the inner circumstellar environment of the archetypal Mira variable _o_ Cet." (abstract)
- Target **Mira (o Ceti) AB**: coordinates _not stated_; z/distance 102 pc  
  > "Throughout this paper we adopt a distance of 102 pc to the Mira system, which is the weighted average between the distance obtained by Hipparcos" (1. Introduction); distance from weighted average of Hipparcos (92 ± 10 pc) and period-luminosity relation (110 ± 9 pc)  
  > "Throughout this paper we adopt a distance of 102 pc to the Mira system, which is the weighted average between the distance obtained by Hipparcos" (1. Introduction)

## Data provenance

- ALMA projects: 2017.1.00191.S, 2012.1.00524.S
- bands: _not stated_
- frequencies and spectral setup: four spws of 1920 channels; 329.25–331.1, 331.1–333.0, 341.35–343.25, 343.2–345.1 GHz; ~0.85 km/s velocity resolution  
  > "The observations were performed using four spectral windows (spws) of 1920 channels each. The velocity resolution was ∼ 0.85 km s [−][1]" (3. ALMA observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: beam 32.7 × 19.1 mas, PA 53.2 deg  
  > "resulting in a beam with major and minor axes of 32.7 mas and 19.1 mas, respectively, and a position angle of 53.2 degrees" (3. ALMA observations)
- max recoverable scale: ~400 mas  
  > "which have a maximum recoverable scale of ∼ 400 mas" (Maximum recoverable scale)
- sensitivity: rms ~1.4 and ~2.0 mJy/beam (higher/lower frequency spws, 1.7 km/s); continuum 0.04 mJy/beam  
  > "In the continuum images, we find an rms noise of 0.04 mJy/beam." (3. ALMA observations)
- time on source: _not stated_
- observing dates: 9 November 2017  
  > "The ALMA observations were obtained on 9 November 2017" (3. ALMA observations)
- pi or archival as stated: PI Khouri (2017.1.00191.S); archival 13CO data from PI Ramstedt used for flux-loss estimate  
  > "We imaged the [13] CO _J_ = 3 − 2 line (PI: Ramstedt)" (Maximum recoverable scale)
- Line: CO v=1, J=3-2 (342.647 GHz)
- Line: 13CO v=0, J=3-2 (not stated)
- Line: SO N_J=8_8-7_7 (344.253 GHz)
- Line: AlO N=9-8 (not stated)
- Line: TiO2 nine unblended lines (Table 3) (331.2–342.7 GHz (Table 3))
- Other facility **VLT/SPHERE/ZIMPOL**: Quasi-simultaneous polarized-light images of dust (filters NR, cnt748, cnt820), 27 Nov 2017  
  > "Mira was observed using filters NR, cnt748, and cnt820 by SPHERE/ZIMPOL on 27 November 2017 (ESO programme ID 0100.D-0737, PI: Khouri)." (2. SPHERE observations)
- External data: Optical constants of Al2O3 solids (Suh amorphous used in models)  
  > "We used the complex refractive index obtained by Suh (2016) in our model calculations, since grains with these properties scatter less efficiently." (4.4.2 Model calculations and results) [from Suh 2016 (cite)]
- External data: 12C/13C ratio of 10 ± 3  
  > "assuming a [12] C-to- [13] C ratio of 10 ± 3 (Hinkle et al. 2016)" (4.3.2) [from Hinkle et al. 2016]
- External data: Solar Ti and Al abundances  
  > "for a gas with solar composition (Asplund et al. 2009)" (4.3.3) [from Asplund et al. 2009]
- External data: Archival 13CO J=3-2 observations used to estimate resolved-out flux  
  > "we compared the flux we measure from the compact molecular line emission region to the observations obtained by Ramstedt et al. (2014)." (Maximum recoverable scale) [from Ramstedt et al. 2014]
- External data: TiO2 line frequencies  
  > "based on measurements by Kania et al. 2011" (4.3.3) [from Kania et al. 2011]

## Processing

### Calibration

- pipeline or manual: standard ALMA procedures in CASA  
  > "The initial gain calibration (bandpass, amplitude, absolute flux-density scale, and phase) was performed following the standard ALMA procedures." (3. ALMA observations)
- casa version: CASA 5.1.1  
  > "The full calibration and imaging was performed in CASA 5.1.1." (3. ALMA observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0237+2848 (flux and bandpass); J0217+0144 (gain)  
  > "Observations of J0237+2848 were used for flux and bandpass calibrations and of J0217+0144 for gain calibration." (3. ALMA observations)
- flux scale uncertainty: _not stated_
- self calibration: phase self-cal on line-free stellar continuum, applied to full dataset  
  > "We then imaged the line free channels and performed a self-calibration step using the stellar continuum. These phase solutions were also applied to the full dataset." (3. ALMA observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "The final image products were created using Briggs robust weighting (with robust parameter equal to 0.5)" (3. ALMA observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: line images are stellar-continuum subtracted  
  > "All the images of spectral line emission presented by us are stellar-continuum subtracted." (3. ALMA observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 32.7 × 19.1 mas, PA 53.2 deg  
  > "a beam with major and minor axes of 32.7 mas and 19.1 mas, respectively, and a position angle of 53.2 degrees" (3. ALMA observations)
- final rms: ~1.4 and ~2.0 mJy/beam at ~1.7 km/s; continuum 0.04 mJy/beam  
  > "Root-mean squared (rms) noise levels of ∼ 1.4 mJy/beam and ∼ 2.0 mJy/beam were achieved" (3. ALMA observations)

### Inherited from earlier work

- CO v=1 J=3-2 modelling code and approach  
  > "We modelled the vibrationally-excited CO _J_ = 3 − 2 line with the same code and approach as used by Khouri et al. (2016b) and Vlemmings et al. (2017a)." (4.3.1 CO v=1, J=3-2) [from Khouri et al. 2016b; Vlemmings et al. 2017a]
- MCMax radiative-transfer approach  
  > "we calculated continuum radiative-transfer models using MCMax (Min et al. 2009) in its spherically-symmetric mode and with a similar approach to that of Khouri et al. (2016a)." (4.4) [from Min et al. 2009; Khouri et al. 2016a]
- ZIMPOL reduction basic procedures  
  > "The basic procedures are standard (bias frame subtraction, cosmic ray removal, and flat fielding; see e.g. Schmid et al. 2017)" (2. SPHERE observations) [from Schmid et al. 2017]

### Not stated but needed to reproduce (our reading)

- Spatial image size and cell size, clean threshold, masks and deconvolver
- Line-free channels used for continuum and self-calibration solution intervals
- Model code for CO v=1 not released/named; power-law radiative transfer details unspecified
- Sampling/grid steps for the model grid
- Continuum subtraction method for lines
- Aperture/integration velocity ranges for TiO2 fluxes
- SZ package version and polarimetric beam-shift correction details

## Analysis recipe

1. **Calibrate and image ALMA data**: Standard ALMA calibration, stellar-continuum self-calibration, Briggs weighting imaging in CASA  
  > "We then imaged the line free channels and performed a self-calibration step using the stellar continuum." (3. ALMA observations)
   - software: CASA
   - parameter: robust = 0.5  
  > "Briggs robust weighting (with robust parameter equal to 0.5)" (3. ALMA observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure stellar disc size at 338 GHz**: Uniform-disc fit to visibilities  
  > "By performing a fit of a uniform-disc source to the observed visibilities using the _uvmultifit_ code (Mart´ı-Vidal et al. 2014)" (3. ALMA observations)
   - software: uvmultifit
   - fitting: uniform disc fit; residuals max 1.9 and min 2.8 mJy  
  > "The residuals obtained after the subtraction of our uniform disc model have maximum and minimum values of 1.9 and 2.8 mJy, respectively." (3. ALMA observations)
   - validation: _not stated_
3. **Quantify flux loss from filtering**: Simulated uniform discs through the array configuration and compared to earlier lower-resolution 13CO data  
  > "we performed simulations of observations of uniform discs by the array configuration used to observe Mira." (Maximum recoverable scale)
   - assumption: resolved-out emission is smooth and spread evenly over the area  
  > "Assuming that the resolved-out emission is smooth and that, therefore, the remaining 28% flux density is spread evenly over the area of 0.24 arcsec [2]" (Maximum recoverable scale)
   - fitting: _not stated_
   - validation: _not stated_
4. **Model CO v=1 J=3-2 line (gas density, temperature, velocity)**: LTE radiative transfer in a spherical shell with power-law profiles; model images convolved with beam; spectra from 20, 50, 100 mas apertures; grid of ~2e4 models  
  > "We calculated close to 2 × 10 [4] models spanning the ranges given in Table 2." (4.3.1)
   - parameter: R338=2.15 au, T*=2100 K, Rout=8.6 au  
  > "The stellar radius and temperature were set to _R_ [338GHz] ⋆ = 2.15 au and _T_ ⋆ = 2100 K" (4.3.1)
   - assumption: CO abundance 4e-4 relative to H2; LTE; spherical symmetry; distance 102 pc  
  > "We assume a CO abundance of 4 × 10 [−][4] relative to H 2 ." (4.3.1)
   - fitting: Initial by-eye search then grids minimizing chi2; 54 DF; reduced chi2 ~4.0  
  > "Our best fit reached a reduced-χ [2] = χ [2] /DF ∼ 4.0." (4.3.1)
   - validation: Compared to 13CO J=3-2 line with 12C/13C=10±3  
  > "We calculated models considering the best-fit models, within the uncertainties given in Table 2, and assuming a [12] C-to- [13] C ratio of 10 ± 3" (4.3.2)
5. **Derive TiO2 and AlO column densities and depletion**: Rotational diagram of unblended TiO2 lines; LTE AlO column with TiO2 excitation temperature; divide by H2 column from CO model; compare to solar abundances  
  > "From the rotational diagram shown in Fig. 7, we derive an excitation temperature of 580 ± 65 K and a column density of (2.7 ± 0.7) × 10 [16] cm [−][2] ." (4.3.3)
   - assumption: LTE; solar composition with fully molecular hydrogen (Asplund et al. 2009)  
  > "for a gas with solar composition (Asplund et al. 2009) and in which hydrogen is fully molecular" (4.3.3)
   - fitting: _not stated_
   - validation: Compared with Kaminski et al. 2016, 2017  
  > "The column density we find is comparable to that reported by Kami´nski et al. (2016)" (4.3.3)
6. **Constrain Al2O3 grain sizes from scattered light**: Spherically-symmetric MCMax models with hollow-sphere opacities, Stokes images convolved with PSF star, compared to upper limit of 2% polarization degree in cnt820  
  > "MCMax calculates the scattering of radiation considering the full angle-dependent Mueller matrix and produces the images of the Stokes parameters _I_, _Q_, and _U_ ." (4.4.2)
   - software: MCMax
   - parameter: dust condensation radius 1.5 or 2.5 R*IR; Al abundance 2.8e-6 rel. to H; star blackbody 2500 K; free parameters f and grain size  
  > "The free parameters in our dust models are _f_ and the size of the dust grains." (4.4.2)
   - assumption: Suh (2016) amorphous Al2O3 optical constants; gas density from CO model  
  > "The values of _n_ ◦ and η are adopted from the gas model." (4.4.2)
   - fitting: _not stated_
   - validation: Result checked against all n values in Table 4  
  > "This result is valid for all the values of _n_ given in Table 4" (4.4.2)

## Software

- **CASA** 5.1.1: calibration and imaging  
  > "The full calibration and imaging was performed in CASA 5.1.1." (3. ALMA observations)
- **uvmultifit** : uniform-disc fit to visibilities  
  > "using the _uvmultifit_ code (Mart´ı-Vidal et al. 2014)" (3. ALMA observations)
- **MCMax** : scattered-light continuum radiative-transfer models  
  > "we calculated continuum radiative-transfer models using MCMax (Min et al. 2009)" (4.4)
- **SZ (SPHERE/ZIMPOL) package** : ZIMPOL data reduction  
  > "The data were reduced using the (SPHERE/ZIMPOL) SZ software package developed at the ETH" (2. SPHERE observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mira A uniform-disc size at 338 GHz | 41.9 × 42.5 | ±0.1 each | mas | 2 | (41.9 ± 0.1) × (42.5 ± 0.1) mas |
| Continuum flux density of Mira A | 250.6 | ±0.2 | mJy | 2 | We find a continuum flux density for Mira A of 250.6 ± 0.2 mJy. |
| Brightness temperature of Mira A | 2100 | not stated | K | 2 | with a brightness temperature of 2100 K |
| Gas mass between R338 and 4R338 | 3.8e-4 | ±1.3e-4 | Msun | 4 | We find a mass in the vibrationally-excited CO region of (3.8 ± 1.3) × 10 [−][4] _M_ ⊙ . |
| Preferred mass including 13CO | ~2.5e-4 | not stated | Msun | 4 | we conclude that the mass in the vibrationally-excited CO region is ∼ 2.5 × 10 [−][4] _M_ ⊙ . |
| vLSR | 47.7 | ±0.1 | km/s | 4 | We find υ LSR = 47.7 ± 0.1 km/s. |
| TiO2 excitation temperature | 580 | ±65 | K | 5 | we derive an excitation temperature of 580 ± 65 K |
| TiO2 column density | 2.7e16 | ±0.7e16 | cm-2 | 5 | a column density of (2.7 ± 0.7) × 10 [16] cm [−][2] |
| AlO column density | 7e15 | ±2e15 | cm-2 | 5 | an AlO column density of (7±2)×10 [15] cm [−][2] is needed |
| Fraction of Ti in TiO2 | ~4.5 | not stated | % | 5 | the TiO 2 molecules account for ∼ 4.5% of the expected titanium and the AlO molecules account for < 0.1% of the expected aluminium. |
| Max size of Al2O3 grains holding significant Al | ≲0.02 | not stated | micron | 6 | these must have relatively small sizes ≲ 0.02 µm. |

## Qualitative findings

- Dust polarized-light structures follow the edge of the compact high-gas-density region seen in ALMA molecular lines.  
  > "While Clump α and Structure β follow the edge of the compact molecular line emission region, Structure δ appears on top of the north-western lobe." (4.1)
- The ~12 R*IR radius of the density decline is too large for pulsation-induced shocks; scenarios of recent mass-loss increase or companion interaction cannot be distinguished.  
  > "We are not able to determine which of these scenarios is correct." (abstract)

## Claim tuples

- H: Do gas and large dust grains correlate spatially around Mira A? | E: Compare ALMA SO moment-zero maps with ZIMPOL polarization degree | R: Polarized dust structures lie at the edge of the compact molecular emission region | F: Dust is contained in a high-gas-density region with a steep outer density decline | **supported**
- H: What are gas density, temperature and velocity within a few stellar radii? | E: Model CO v=1 J=3-2 with 13CO check | R: Mass (3.8 ± 1.3)e-4 Msun within 4 R338 | F: Fairly cold (~1000 K) dense gas close to the star | **supported**
- H: Are Ti and Al largely in gas-phase TiO2 and AlO? | E: Column densities from rotational diagram and LTE, divided by H2 | R: TiO2 ~4.5% of Ti, AlO <0.1% of Al | F: Low AlO abundance allows efficient Al depletion into dust, but budget remains incomplete | **partially**
- H: Can Al2O3 grains of ~0.1 micron hold a significant fraction of Al? | E: MCMax scattered-light models vs <2% polarization limit | R: <1% of Al in 0.1 micron grains; ~100% only for 0.02 micron | F: Al2O3 grains must be ≲0.02 micron, smaller than model predictions | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Coordinated quasi-simultaneous ALMA and SPHERE observations to probe gas and large grains respectively  
  > "We obtained quasi-simultaneous observations using ALMA and SPHERE/ZIMPOL" (abstract)
- Alternative: Radiative excitation or temperature change as cause of compact emission rejected as unlikely because many lines with different Eu show the same region  
  > "We consider these possibilities very unlikely, because lines of different molecules" (4.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Spherical model gives reduced chi2 ~4.0; a non-spherical model is needed  
  > "This shows that a more complex model (non-spherically symmetric) is required" (4.3.1)
- Limitation (authors): Beam-shift effect in ZIMPOL data not corrected; Clump γ polarization likely overestimated  
  > "we do not attempt to improve the reduction." (Beam-shift effect)
- Caveat (inferred, ours): Fit uncertainties come from grid chi2 with reduced chi2 ~4, likely underestimated
- Caveat (inferred, ours): Single-epoch data; variability limits comparison with earlier studies
- Caveat (inferred, ours): Al2O3 limits rely on a 2% upper polarization limit affected by beam-shift
- Caveat (inferred, ours): LTE and spherical symmetry assumptions

## Reproducibility

- Data public (paper): ALMA project codes cited in acknowledgements  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00191.S and ADS/JAO.ALMA#2012.1.00524.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Radiative-transfer code for CO model not named or released
- Missing: Image size, cell, clean parameters
- Missing: ZIMPOL data not part of ALMA archive
- Missing: Details of line aperture integration
- Data volume (inferred): ~50-100 GB (four 1920-channel spws, long baselines)
- Score (inferred): 3/5, ALMA data public and key parameters given, but the custom CO model code and imaging details are missing.
- Rediscovery candidate: no, Main results depend on an unreleased custom radiative-transfer code and ZIMPOL data.

## Links

- Method: Khouri et al. 2016b (CO v=1 modelling code and approach)
- Method: Mart´ı-Vidal et al. 2014 (uvmultifit)
- Method: Min et al. 2009 (MCMax)
- Companion: Kami´nski et al. 2016, 2017 (AlO and TiO2 observations of Mira to compare)
- Companion: Wong et al. 2016 (earlier ALMA gas-density model of Mira)
- Related: ESO programme 0100.D-0737 (SPHERE/ZIMPOL)

## Checks

```json
{
 "quotes": 78,
 "quotes_ok": 78,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 86,
  "stated": 55,
  "rate": 0.64
 },
 "evidence_ok": true
}
```
