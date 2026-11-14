# A Detailed View of the Circumstellar Environment and Disk of the Forming O-star AFGL 4176

`2020ApJ...896...35J` | The Astrophysical Journal 2020 | first author: Johnston, Katharine G. | arXiv: 2004.13739 | DOI: 10.3847/1538-4357/ab8adc

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: What are the continuum source population, spectral/morphological line properties, and large-scale environment of the disk around the forming O-star AFGL 4176 mm1, using ALMA with ATCA and APEX data?  
  > "In this paper, we present a detailed analysis of the circumstellar environment and disk of AFGL 4176, combining continuum and line data from ALMA with complementary ATCA and APEX observations at 1.2-1.5 cm and 1.2 mm, respectively." (Introduction)
- Target **AFGL 4176 mm1**: coordinates 13:43:01.693 -62:08:51.25 (J2000)  
  > "situated at a distance of 4.2$\pm$0.9 kpc (cite: green11a)" (Introduction); "| mm1 | 13:43:01.693 -62:08:51.25 |" (Table 2); z/distance 4.2 kpc  
  > "situated at a distance of 4.2$\pm$0.9 kpc (cite: green11a)" (Introduction); "| mm1 | 13:43:01.693 -62:08:51.25 |" (Table 2); distance from green11a (Green & McClure-Griffiths 2011)  
  > "situated at a distance of 4.2$\pm$0.9 kpc (cite: green11a)" (Introduction); "| mm1 | 13:43:01.693 -62:08:51.25 |" (Table 2)

## Data provenance

- ALMA projects: 2012.1.00469.S
- bands: _not stated_
- frequencies and spectral setup: 4 spws: 238.8376–239.3064, 239.6035–241.4785, 253.1055–254.9805, 256.1146–256.5834 GHz; channel widths 0.33–1.4 km/s  
  > "| spw0 | 238.8376 – 239.3064 | 0.354 | 0.30 $\times$ 0.28$''$ PA: $38.0^{\circ}$ | 3.8 |" (Table 1)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.26 to 0.30'' (1100 to 1300 au)  
  > "The angular resolutions for each spw range from 0.26 to 0.30$\ensuremath{''}$, corresponding to 1100 to 1300 au." (2.1 ALMA Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 1.37 hr  
  > "the total time on-source across the observations was 1.37 hr" (2.1 ALMA Observations)
- observing dates: August 2014, Cycle 1 Transfer project during Cycle 2  
  > "The ALMA observations of AFGL 4176 were taken in August 2014 as a Cycle 1 Transfer project during ALMA Cycle 2." (2.1 ALMA Observations)
- pi or archival as stated: _not stated_
- Line: CH3CN J=13-12 K ladder (238.84–239.14 GHz)
- Line: C34S J=5-4 (241.016194 GHz)
- Line: H29alpha recombination line (not stated)
- Other facility **ATCA**: 1.2–1.5 cm continuum, NH3 and recombination lines (project C2646)  
  > "We observed AFGL 4176 with the Australia Telescope Compact Array (ATCA) under project C2646 in the 15-mm band during 2012" (2.2 ATCA Observations)
- Other facility **APEX**: C34S(5-4) map to combine with ALMA  
  > "We used the Swedish Heterodyne Facility Instrument (SHeFI) APEX-1 receiver to observe C$^{34}$S(J=5-4) at 241.016 GHz in the lower sideband" (2.3 APEX Observations)
- External data: CH3CN-derived disk temperature 190 K, excitation map, inclination ~30 deg, disk PA, 1.21 mm Gaussian flux 50 mJy  
  > "we use a temperature of 190 K, which was the average temperature of the disk derived from modeling CH$_3$CN line emission using CASSIS[^5] (J15)" (3.1.1) [from Johnston et al. 2015 (cite: johnston15a)]
- External data: Dust opacity 0.24 cm2/g at 1.21 mm (Milky Way dust model R_V=5.5)  
  > "the dust opacity at 1.21 mm was assumed to be 0.24 cm$^2$ g$^{-1}$, which was determined from the (cite: draine03a; draine03b) Milky Way dust model with $R_V=5.5$." (3.1.1) [from (cite: draine03a; draine03b)]
- External data: Gas-to-dust ratio 154  
  > "We assume a gas-to-dust ratio measured for the solar neighborhood of 154 (cite: draine11)" (3.1.1) [from (cite: draine11)]
- External data: 8.59 GHz flux density of 363 mJy for the extended HII region  
  > "(cite: ellingsen05) measured an integrated flux density of 363 mJy at 8.59 GHz for the extended HII region with the 6A array." (4.1 Centimeter Continuum) [from (cite: ellingsen05)]
- External data: ATLASGAL 870 um integrated flux 17.32 Jy  
  > "The integrated ATLASGAL flux density at 870 $\mu$m is 17.32 Jy (cite: urquhart14a)." (4.2 Ammonia Emission) [from (cite: urquhart14a)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: absolute flux calibration error of 10-20% expected  
  > "whereas an absolute flux calibration error of 10-20% is also expected." (3.1.1)
- self calibration: Phase-only self-cal derived from continuum applied to spw1 and spw2 for spectral index  
  > "We applied the phase self-calibration (i.e. no amplitude self-calibration) derived from the continuum data to the wide spectral windows spw1 and spw2" (3.1.1)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5; natural weighting for H29alpha and C34S  
  > "Each of the four observed spectral windows were imaged using Briggs weighting and a robust parameter of 0.5" (2.1 ALMA Observations); "When imaging H29$\alpha$ and C$^{34}$S, we instead used natural weighting to recover extended emission" (2.1 ALMA Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: imcontsub in CASA  
  > "the continuum was subtracted using `imcontsub` in CASA to avoid over-subtraction" (2.1 ALMA Observations)
- line free channels: _not stated_
- primary beam correction: All figures except Fig. 1 are primary-beam-corrected  
  > "Except for Fig.[1](#contfig), all figures in this paper show primary-beam-corrected images." (2.1 ALMA Observations)
- array combination: ALMA and APEX C34S combined with CASA feather  
  > "The ALMA and APEX C$^{34}$S images were combined using the CASA task `feather`." (2.1 ALMA Observations)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: 2.0–3.8 mJy/beam per spw (H29alpha 1.3 mJy/beam at 2.0 km/s; C34S 4 mJy/beam at 1.4 km/s)  
  > "| spw3 | 256.1146 – 256.5834 | 0.330 | 0.26 $\times$ 0.26$''$ PA: $-171^{\circ}$ | 3.4 |" (Table 1)

### Inherited from earlier work

- ALMA observations described in earlier paper  
  > "The observations are described in J15." (2.1 ALMA Observations) [from J15 = Johnston et al. 2015 (cite: johnston15a)]
- Assumed distance 4.2 kpc  
  > "As in J15, we assume a distance of 4.2 kpc." (3.1.1) [from J15 (cite: johnston15a)]
- Dust opacity at 1.21 mm kept consistent with J15  
  > "To be consistent with J15, the dust opacity at 1.21 mm was assumed to be 0.24 cm$^2$ g$^{-1}$" (3.1.1) [from J15 (cite: johnston15a)]
- Gas mass/assumption set for Fig. 23 comparison (gas-to-dust 100, kappa 1 cm2/g at 1.4 mm, beta 2)  
  > "have been recalculated to be consistent with the set of assumptions stated in (cite: beltran16a), namely that the gas-to-dust ratio is 100" (6.1) [from (cite: beltran16a)]

### Not stated but needed to reproduce (our reading)

- ALMA CASA version and calibration/pipeline details (in J15)
- Image size and cell size, clean threshold, masking and deconvolver
- Line-free channels used for continuum and the sigma-clipping thresholds
- astrodendro min_delta/min_npix beyond the stated sigma criteria
- Exact flux calibrator and calibration scheme for ALMA
- ALMA-APEX feather parameters (scaling)

## Analysis recipe

1. **Identify continuum sources and measure fluxes**: astrodendro on non-PB-corrected image with 5 sigma peak threshold; properties extracted from PB-corrected image  
  > "we used the non-primary-beam-corrected image and set the peak flux required for a detection to be 5$\sigma$" (3.1.1)
   - software: astrodendro
   - parameter: 2 sigma flux limit; 1 sigma required difference between embedded structures  
  > "the required flux difference between embedded structures to be assigned as a separate source is 1$\sigma$" (3.1.1)
   - fitting: _not stated_
   - validation: Compared with Gaussian-fit fluxes of J15  
  > "The peak and integrated flux densities measured for mm1 are slightly larger than that quoted in J15, which was determined using a Gaussian fit." (3.1.1)
2. **Derive masses and column densities**: Optically thin dust formulae with T=100 K (190 K for mm1)  
  > "We assume a gas-to-dust ratio measured for the solar neighborhood of 154 (cite: draine11) and a temperature of 100 K, except for mm1, where we use a temperature of 190 K" (3.1.1)
   - assumption: kappa(1.21 mm)=0.24 cm2/g; g=154; d=4.2 kpc; OH94 opacity would lower masses by ~4  
  > "which if used instead would reduce the masses and column densities by a factor of $\sim$4" (3.1.1)
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure mm1 spectral index and dust fraction**: Power-law fit to line-free channel fluxes in 1'' aperture across spw1 and spw2; cross-check with clean nterms=2; dust fraction from f=(alpha_obs-alpha_ff)/(alpha_d-alpha_ff)  
  > "We then found the integrated flux in each line-free channel within a 1$''$  diameter aperture around the mm1 peak, and subsequently fitted these continuum channel fluxes by a power law" (3.1.1)
   - software: CASA
   - parameter: alpha_d upper limit 3.6, alpha_ff upper limit 2  
  > "Assuming an upper limit for the spectral index of dust emission of 3.6 (derived from the dust model used in J15)" (3.1.2)
   - fitting: Power-law fit; uncertainty from scatter plus calibrator-based systematic  
  > "The resulting spectral index is 3.36$\pm$0.14, where the uncertainty is determined from the scatter in the data." (3.1.1)
   - validation: nterms=2 clean gives 3.35  
  > "obtained a similar average spectral index of 3.35 over pixels within 0.15$''$ of the continuum peak" (3.1.1)
4. **Line census and identification**: Mean spectra in 0.5'' radius aperture; >5 sigma lines; LTE models in CASSIS with CDMS/JPL; simultaneous Gaussian fits with astropy.modeling SLSQP  
  > "all line properties were determined via a simultaneous spectral fit with Gaussians to all of the detected lines using `astropy.modeling` with the Sequential Least Squares Programming (SLSQP) fitter" (3.2.1)
   - software: CASSIS, astropy
   - parameter: CH3OH LTE reference: N_H2=4e25 cm-2, vLSR=-52, FWHM 5 km/s, T=160 K, size 0.5'', abundance 1e-8  
  > "N$_{H_2}$ = 4$\times$10$^{25}$ cm$^{-2}$, v$_{_{\rm LSR}}$=-52 km s$^{-1}$, $\Delta v _{\rm_{FWHM}}$=5 km s$^{-1}$, T=160 K, and a size of 0.5$''$" (3.2.1)
   - fitting: SLSQP bounded Gaussians; errors estimated by Monte Carlo on synthetic data  
  > "the errors were instead estimated by testing the fitting algorithm used with Monte Carlo simulations of synthetic data" (3.2.2)
   - validation: Compared with Bøgelund et al. 2019 line list  
  > "The line identifications are generally in good agreement with (cite: bogelund19a)" (3.2.1)
5. **Classify line morphologies**: Inspect channel maps; pairwise reduced chi2 on three channels (-2, 0, +2 km/s) in 2''x2'' field after adding noise to S/N 15  
  > "we added noise to each of the three channels, so that all channels had a peak signal-to-noise of 15" (3.2.2)
   - fitting: _not stated_
   - validation: Self-comparison chi2 close to 1, cross-type chi2 higher  
  > "the average reduced $\chi^2$ is statistically significantly higher when the $\chi^2$ is calculated from comparison between line types" (3.2.2)
6. **ATCA NH3 temperature and mass**: Per-pixel Gaussian fits to NH3(1,1) and (2,2), Trot then Tk with Maret correction; mass from Rosolowsky eqs; ATLASGAL dust mass comparison  
  > "We fit Gaussians to the main component, and hyperfine components in the case of NH$_3$(1,1), for each pixel in the NH$_3$(1,1) and NH$_3$(2,2) cubes" (4.2 Ammonia Emission)
   - software: MIRIAD
   - parameter: >7 sigma pixels, tau held at zero, NH3 abundance 10^-7.5  
  > "Only pixels where the peak flux density in the main line was $>7\sigma$ in both transitions were fit." (4.2 Ammonia Emission)
   - assumption: Optically thin NH3  
  > "assuming therefore that the NH$_{3}$ clump is optically thin" (4.2 Ammonia Emission)
   - fitting: Gaussian fits per pixel  
  > "We fit Gaussians to the main component, and hyperfine components in the case of NH$_3$(1,1), for each pixel in the NH$_3$(1,1) and NH$_3$(2,2) cubes" (4.2 Ammonia Emission)
   - validation: NH3 mass within factor two of ATLASGAL dust mass  
  > "The mass of the clump determined from the Draine opacities is within a factor of two of the mass determined from NH$_3$" (4.2 Ammonia Emission)
7. **Electron density from recombination lines**: Monte Carlo electron density distribution for H29alpha paired with H64/65/67/68alpha following Keto et al. 2008  
  > "using Monte Carlo statistics and the method outlined in (cite: keto08)" (5.2)
   - fitting: Product of pairwise distributions; 99.7th percentile upper limit  
  > "We then multiplied these distributions to find the combined probability distribution for $n_e$ and found the 99.7th percentile provided an upper limit of $n_e < 6.6 \times 10^5$ cm$^{-3}$" (5.2 Hydrogen Recombination Line Emission)
   - validation: _not stated_

## Software

- **CASA** : imaging, imcontsub, feather, clean  
  > "The ALMA and APEX C$^{34}$S images were combined using the CASA task `feather`." (2.1 ALMA Observations)
- **astrodendro** : continuum source identification and photometry  
  > "We measured the positions and flux densities of these sources using the `astrodendro` software" (3.1.1)
- **CASSIS** : LTE line modelling and identification  
  > "Using the spectral analysis package CASSIS,[^7] we first fit an LTE model to the CH$_3$OH and $^{13}$CH$_3$OH lines in spw2" (3.2.1)
- **astropy.modeling** : SLSQP Gaussian line fitting  
  > "using `astropy.modeling` with the Sequential Least Squares Programming (SLSQP) fitter" (3.2.1)
- **MIRIAD** 20120419 ATNF version: ATCA calibration and imaging  
  > "Calibration and imaging was carried out in the 20120419 ATNF version of MIRIAD." (2.2 ATCA Observations)
- **GILDAS/CLASS** : APEX data reduction  
  > "Data reduction was performed within GILDAS/CLASS" (2.3 APEX Observations)
- **spectral-cube** v0.4.0: listed software  
  > "spectral-cube (cite: spectralcube)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of 1.2 mm continuum sources within 5'' | 17 | not stated | dimensionless | 1 | We detect 17 sources in the field. |
| mm1 integrated flux density | 61.22 | 0.04 | mJy | 1 | / mm1 / 13:43:01.693 -62:08:51.25 / 38.49 $\pm$ 0.08 / 61.22 $\pm$ 0.04 / 9.4 $^{b}$ / |
| mm1 spectral index (spw1-spw2) | 3.4 | 0.2 | dimensionless | 3 | The measured spectral index of 3.4$\pm$0.2 can be explained by dust emission |
| Dust opacity index beta | 1.4 | 0.2 | dimensionless | 3 | In this case, we would infer $\beta=1.4\pm0.2$. |
| Dust fraction of 1.2 mm emission (lower limit) | 87 | 13 | % | 3 | we find a lower limit to the dust emission fraction $f$ of 87$\pm$13% |
| Spectral index 1.23 cm to 1.21 mm | 1.56 | 0.15 | dimensionless | 0 | The spectral index between 1.23 cm and 1.21 mm is therefore 1.56$\pm$0.15. |
| Number of molecules / lines detected | 25 molecules, 203 lines | not stated | dimensionless | 4 | we detect a total of 25 different molecules, which are listed in Table [\[moldetect\]](#moldetect), from a total of 203 lines |
| mm1 mass | 9.4 | not stated | Msun | 2 | / mm1 / 13:43:01.693 -62:08:51.25 / 38.49 $\pm$ 0.08 / 61.22 $\pm$ 0.04 / 9.4 $^{b}$ / |
| Mean velocity of blue-dominant lines | -53.27 | 0.10 | km/s | 4 | -51.64$\pm$0.21, -52.44$\pm$0.15, -52.88$\pm$0.11, and -53.27$\pm$0.10 km s$^{-1}$ for red-dominant, disk-tracing, outflow-tracing, and blue-dominant lines |
| Toroid H2 mass from NH3 | 9200 | not stated | Msun | 6 | find the total H$_2$ mass to be 9200 M$_{\odot}$ |
| Outflow half-opening angle at 1.5e5 au | ~19 | not stated | deg | 0 | we could determine that the half-opening angle of the outflow or cavity wall at 1.5$\times 10^{5}$ au is $\sim$19$^{\circ}$ |
| Electron density upper limit | 6.6e5 | not stated | cm-3 | 7 | $n_e < 6.6 \times 10^5$ cm$^{-3}$ |

## Qualitative findings

- All N-bearing molecules bright enough trace the disk; O-bearing lines are mostly blue-dominant, coincident with methanol masers  
  > "the presence of nitrogen in the molecules of these observations appears to indicate that it is a good disk tracer." (3.2.3)

## Claim tuples

- H: mm1 continuum at 1.2 mm is dominated by dust | E: Spectral index across ALMA band and combination with 1.23 cm flux | R: alpha=3.4±0.2; dust fraction >87% | F: Dust dominates at 1.2 mm; free-free <13% | **supported**
- H: Different molecules trace different parts of the disk environment | E: Channel maps and chi2 comparison of lines | R: Four morphology types; N-bearing disk-tracing, O-bearing blue-dominant | F: Chemical segregation; blue-dominant lines may trace accretion shock | **supported**
- H: mm2 is a companion or jet knot | E: Spectra and kinematics at mm2 | R: Rich in S-bearing lines, blueshifted, on disk axis | F: Likely a jet/outflow knot but companion not excluded | **partially**
- H: mm1 lies in a large-scale rotating toroid | E: ATCA NH3(1,1),(2,2) moment maps | R: Velocity gradient over r~0.5 pc, mass 9200 Msun | F: mm1 at blueshifted NW end of a rotating toroid | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Spectral index method chosen because Gaussian-fit continuum misses diffuse background; astrodendro used  
  > "the Gaussian source lies on a background of more diffuse emission, which was not included in the Gaussian fit" (3.1.1)
- Alternative: OH94 dust opacity not used because no scattering properties for HYPERION  
  > "We could not use this opacity for the radiative-transfer dust-continuum modeling presented in J15" (3.1.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Free-free contribution at 1.2 mm not removed; relative astrometry insufficient  
  > "we do not attempt to remove the free-free contribution from the ALMA continuum data" (3.1.2)
- Caveat (inferred, ours): Line identification and morphology classification are by-eye and subjective
- Caveat (inferred, ours): Morphology classes sensitive to interferometric filtering
- Caveat (inferred, ours): Single 1.37 hr observation; distance uncertainty of ~20% propagates to masses
- Caveat (inferred, ours): Dust opacity choice changes masses by factor ~4

## Reproducibility

- Data public (paper): Reduced data products released on Zenodo  
  > "We have made these data available online[^1]." (Introduction)
- Products in archive: _not stated_
- Missing: Calibration details (in J15)
- Missing: Imaging sizes, masks, line-free channels
- Missing: Manual CASSIS Gaussian fits for busy regions
- Missing: Morphological classification by eye
- Data volume (inferred): ~50-100 GB raw for ALMA single execution; ATCA and APEX smaller
- Score (inferred): 3/5, Data public and many numbers stated, but calibration is inherited from J15 and line classification is subjective.
- Rediscovery candidate: no, Key steps are partly manual/by-eye and calibration/imaging details are missing.

## Links

- Method: Johnston et al. 2015 (cite: johnston15a) (Original ALMA data description, CH3CN disk modeling, temperature and inclination)
- Companion: Bøgelund et al. 2019 (cite: bogelund19a) (Independent chemistry analysis of same ALMA data)
- Related: ATLASGAL

## Checks

```json
{
 "quotes": 85,
 "quotes_ok": 85,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 91,
  "stated": 60,
  "rate": 0.659
 },
 "evidence_ok": true
}
```
