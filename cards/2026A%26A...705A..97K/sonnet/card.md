# MINDS: Young binary systems with JWST/MIRI: Variable water-rich primaries and extended emission

`2026A&A...705A..97K` | Astronomy and Astrophysics 2026 | first author: Kurtovic, Nicolás T. | arXiv: 2508.02576 | DOI: 10.1051/0004-6361/202554927

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: protoplanetary_disks, star_formation
- Question: How does stellar multiplicity affect the inner-disk chemistry and physics of the primary and secondary disks in binaries, as seen with JWST/MIRI-MRS and compared to Spitzer, CRIRES+ and ALMA?  
  > "to investigate the impact of stellar multiplicity on the chemistry and physics of their inner disk." (abstract)
- Target **VW Cha**: coordinates _not stated_; z/distance 185 pc  
  > "VW Cha is a quadruple stellar system located at 185 pc (cite: gaia2021edr3)" (2.1 VW Cha); distance from Gaia EDR3  
  > "VW Cha is a quadruple stellar system located at 185 pc (cite: gaia2021edr3)" (2.1 VW Cha)
- Target **WX Cha**: coordinates _not stated_; z/distance 191 pc  
  > "WX Cha is a binary system located at 191 pc (cite: gaia2021edr3)." (2.2 WX Cha); distance from Gaia EDR3  
  > "WX Cha is a binary system located at 191 pc (cite: gaia2021edr3)." (2.2 WX Cha)
- Target **RW Aur**: coordinates _not stated_; z/distance 154 pc  
  > "located at 154 pc (cite: gaia2021edr3)" (2.3 RW Aur); distance from Gaia EDR3  
  > "located at 154 pc (cite: gaia2021edr3)" (2.3 RW Aur)
- Target **DF Tau**: coordinates _not stated_; z/distance 140 pc  
  > "($14$ au when considering a distance of 140 pc)" (2.4 DF Tau); distance from assumed in text, not stated  
  > "($14$ au when considering a distance of 140 pc)" (2.4 DF Tau)

## Data provenance

- ALMA projects: 2015.1.01506.S, 2016.1.00877.S, 2016.1.01164.S, 2017.1.01631.S, 2018.1.00973.S, 2019.1.01739.S, 2021.1.00854.S
- bands: Band 6 for DF Tau 12CO J=2-1 (ALMA part)  
  > "When observed with ALMA in Band 6, DF Tau shows emission in the $^{12}$CO $\nu$=0 J=2-1 emission" (5.1 Extended Ionized Neon)
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
- Line: 12CO J=2-1 (230.538 GHz)
- Other facility **JWST/MIRI-MRS**: Mid-IR spectra and extended emission of VW Cha, WX Cha, RW Aur (program 1282, MINDS)  
  > "These observations are part of the MINDS (cite: kamp2023; henning2024)." (3.1 Observations and data reduction)
- Other facility **Spitzer/IRS**: Earlier mid-IR spectra for variability comparison  
  > "RW Aur, VW Cha, and WX Cha were previously observed with Spitzer/IRS" (4.4 Continuum and H2O variability)
- Other facility **VLT/CRIRES+**: M-band CO line profiles  
  > "we use the high-spectral resolution observations in the M-band from VLT/CRIRES" (4.6 Inner gas disk with VLT/CRIRES+)
- External data: ALMA dust continuum and CO analysis of RW Aur (disk sizes, 4 au cavity in B, inclination 55 deg, stellar masses)  
  > "with dust disk sizes of 19 au and 14 au for A and B, respectively" (2.3 RW Aur) [from (cite: kurtovic2025a)]
- External data: DF Tau ALMA observations and MIRI-MRS data  
  > "we also include the observation of the binary DF Tau, which was previously analyzed in (cite: grant2024)." (2 Multiple Stellar Systems) [from (cite: grant2024)]

## Processing

### Calibration

- pipeline or manual: JWST data: hybrid pipeline combining standard JWST pipeline and VIP; ALMA calibration not described  
  > "The MIRI-MRS data[^1] was reduced using a hybrid pipeline[^2] (cite: minds_notebook)" (3.1 Observations and data reduction)
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

- ALMA imaging and processing of RW Aur and DF Tau  
  > "where high angular resolution observations at millimeter wavelengths are available (cite: grant2024; kurtovic2025a)" (5 Extended emission) [from (cite: kurtovic2025a), (cite: grant2024)]
- Continuum estimation with Savitzky-Golay filter  
  > "We estimate the continuum emission in the 1D spectra as in (cite: temmink2024)" (3.1 Observations and data reduction) [from (cite: temmink2024)]
- Slab model calculation with line overlap  
  > "Our slab calculation is the same as described in (cite: tabone2023)" (3.2 Modeling spectra with 0D slabs) [from (cite: tabone2023)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration, imaging parameters, and beams are not given; all ALMA details are deferred to the cited papers
- Which ALMA projects correspond to which target
- Details of the adapted bettermoments code
- Exact MIRI aperture sizes and PSF model settings

## Analysis recipe

1. **separate primary and secondary spectra**: Forward model theoretical PSF per channel image plus aperture photometry on residuals  
  > "we apply a combination of forward modeling with a theoretical PSF and aperture photometry to disentangle the emission of each binary component." (3.1 Observations and data reduction)
   - software: VIP
   - fitting: MCMC maximum likelihood for PSF centers  
  > "we calculated the center with the maximum likelihood with a Markov Chain Monte Carlo (MCMC) approach" (3.1 Observations and data reduction)
   - validation: _not stated_
2. **fit molecular slab models**: LTE 0D slab models fitted with MCMC in 13.4-25.4 um  
  > "We fit the continuum-subtracted spectra with Local Thermodynamical Equilibrium (LTE) slab models in the range 13.4-25.4 $\mu$m" (3.2 Modeling spectra with 0D slabs)
   - software: emcee, spectres, HITRAN
   - parameter: Uniform priors; minimum T 140 K; maximum radius 10 au; N upper limit 1e20 cm-2  
  > "The minimum allowed temperature was 140 K, while the maximum allowed radius was $10$ au." (3.2 Modeling spectra with 0D slabs)
   - assumption: linewidth 4.71 km/s; distance from Gaia DR3 parallax inverse  
  > "As linewidth, we use a $\Delta\text{V}=4.71\,\text{km}\,\text{s}^{-1}$" (3.2 Modeling spectra with 0D slabs)
   - fitting: emcee, chi2 likelihood, walkers x8 number of parameters, converged after ~4e3 steps  
  > "We optimize the minimum $\chi^2$ of the residuals as the likelihood distribution for our MCMC." (3.2 Modeling spectra with 0D slabs)
   - validation: _not stated_
3. **extended emission maps**: Subtract scaled median empirical PSF, make moment 0 and quasi-moment 8 maps; compare with ALMA  
  > "This median PSF was rescaled to match the peak flux of each channel image, thus removing all the emission coming from a point source." (3.3 Extracting extended emission)
   - software: bettermoments
   - fitting: _not stated_
   - validation: _not stated_
4. **per-pixel H2 slab fitting**: Slab fit of H2 S(5)-S(8) per 0.2 arcsec pixel with MCMC, filtered by T and N  
  > "We run an MCMC for every pixel, with 80 walkers and 500 steps, using an uniform prior for each parameter." (13 Fitting the extended H2 emission)
   - software: emcee
   - fitting: uniform priors, emitting area fixed to pixel area  
  > "The temperature of the slab ($T_{\text{H}_2}$) and the column density ($N_{\text{H}_2}$) are left as free parameters, and the emitting area ($A_{\text{H}_2}$) is fixed to the pixel area." (Fitting the extended H$_2$ emission)
   - validation: Resampled flux within 1% of original  
  > "we confirm the resampled image has less than 1% of difference in total flux compared to the original image." (13 Fitting the extended H2 emission)

## Software

- **emcee** : MCMC slab fits  
  > "We fit the slab models to the spectrum of each disk using an MCMC approach with `emcee`" (3.2 Modeling spectra with 0D slabs)
- **bettermoments** adapted: moment maps  
  > "using an adapted version of `bettermoments`" (3.3 Extracting extended emission)
- **VIP** : part of hybrid MIRI reduction pipeline  
  > "and from the VIP package (cite: GomezGonzalez2017; Christiaens2023)" (3.1 Observations and data reduction)
- **JWST pipeline** 1.13.4: standard reduction, CRDS context 1224  
  > "using CRDS context 1224" (3.1 Observations and data reduction)
- **pybaselines** : baseline determination  
  > "determined using PyBaselines (cite: erb2022)" (3.1 Observations and data reduction)
- **spectres** : binning to MIRI sampling  
  > "binned to the frequency sampling of the MIRI-MRS using `spectres`" (3.2 Modeling spectra with 0D slabs)
- **lmfit** 1.3.2: Gaussian fits to CRIRES+ CO profiles  
  > "These Gaussians were fitted using the python-package `lmfit`" (12 CO emission from VLT/CRIRES+)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| [Ne III]/[Ne II] ratio, VW Cha BC | 0.65 | 0.02 | dimensionless | 0 | we find ratios of 0.65$\pm$0.02 and 0.14$\pm$0.02 |
| [Ne III]/[Ne II] ratio, RW Aur B | 0.14 | 0.02 | dimensionless | 0 | we find ratios of 0.65$\pm$0.02 and 0.14$\pm$0.02 |
| median H2 temperature RW Aur / VW Cha | 1300 / 800 | not stated | K | 4 | with a median temperature of 1300 K in RW Aur, and 800 K in VW Cha |
| hot H2 mass RW Aur / VW Cha | 9.2e-8 / 8.3e-8 | not stated | Msun | 4 | is $9.2\cdot10^{-8}\,$M$_\odot$ in the RW Aur system, and $8.3\cdot10^{-8}\,$M$_\odot$ in VW Cha |
| RW Aur A hottest H2O slab T | 1299 | 3 | K | 2 | / H$_2$O $\#1$ / $T$ / $825 \pm 6$ / $877 \pm 16$ / $1299 \pm 3$ / 450 / K / |

## Qualitative findings

- Primary disks are H2O-rich; secondary disks mostly line-poor  
  > "primary disks showing H$_2$O-rich spectra, and secondary disks being mostly line poor to the sensitivity of our spectra." (abstract)

## Claim tuples

- H: Do primary and secondary disks differ in mid-IR emission? | E: Separated spectra with PSF forward modeling and fitted slabs | R: Primaries are H2O-rich; secondaries line-poor except RW Aur B | F: Dramatic primary/secondary differences, not explained by truncation alone | **supported**
- H: Is there variability between Spitzer and JWST? | E: Compared IRS to MIRI-MRS | R: VW Cha A line variability, RW Aur A continuum variability | F: Physical variability | **supported**
- H: Does the RW Aur B cavity explain its weak lines? | E: Compared MIRI spectrum with ALMA continuum | R: 4 au cavity consistent qualitatively | F: Cavity may explain spectrum | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Sensitivity for secondaries limited by fringing and PSF undersampling; line detections limited to >3 mJy  
  > "the line detections in our spectra are limited to features brighter than 3mJy." (3.4 Limitations)
- Caveat (inferred, ours): ALMA comparison is qualitative and relies on earlier papers
- Caveat (inferred, ours): Slab uncertainties are underestimated, as the paper admits

## Reproducibility

- Data public (paper): JWST data from MAST; pipeline on GitHub  
  > "The original data can be downloaded from the Mikulski Archive for Space Telescopes (MAST)." (3.1 footnote)
- Products in archive: _not stated_
- Code: Hybrid pipeline at github.com/VChristiaens/MINDS  
  > "The pipeline and associated documentation are available at <https://github.com/VChristiaens/MINDS>" (footnote 2)
- Missing: ALMA data reduction details
- Missing: PSF-fit and aperture settings
- Missing: Slab fit initial values
- Data volume (inferred): JWST MIRI-MRS cubes plus ALMA datasets: tens of GB
- Score (inferred): 3/5, JWST part is well described, but the ALMA part is minor and delegated to other papers.
- Rediscovery candidate: no, The main results come from JWST, and the ALMA recipe is not given.

## Links

- Method: (cite: tabone2023) (Slab model calculation)
- Method: (cite: temmink2024) (Continuum estimation and line stacking)
- Companion: (cite: kurtovic2025a) (ALMA analysis of RW Aur)
- Companion: (cite: grant2024) (DF Tau MIRI and ALMA)
- Related: MINDS

## Checks

```json
{
 "quotes": 57,
 "quotes_ok": 57,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 7,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 84,
  "stated": 40,
  "rate": 0.476
 },
 "evidence_ok": true
}
```
