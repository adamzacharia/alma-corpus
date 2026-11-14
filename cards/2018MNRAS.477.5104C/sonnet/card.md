# An inner warp in the DoAr 44 T Tauri transition disc

`2018MNRAS.477.5104C` | Monthly Notices of the Royal Astronomical Society 2018 | first author: Casassus, Simon | arXiv: 1804.02360 | DOI: 10.1093/mnras/sty894

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks
- Question: Do the deep azimuthal dips in SPHERE H-band polarized imaging of DoAr 44 and their shallower 336 GHz counterparts arise from shadowing by a tilted inner disk, and what is the tilt?  
  > "We constrain the warp geometry by comparing radiative transfer predictions with the DPI data in $H$ band ($Q_\phi(H)$) and with a re-processing of archival 336 GHz ALMA observations." (abstract)
- Target **DoAr 44 (ROXs 44)**: coordinates J2000 16:31:33.4635, -24:27:37.222 (HSOY, epoch 2000)  
  > "DoAr 44 is located in the L1688 dark cloud of Ophiuchus" (1 Introduction); "so likely close to the distance of $+120.0_{-4.2}^{+4.5}$ pc derived for the Ophiuchus core by" (1 Introduction); "J2000 (16:31:33.4635, -24:27:37.222)" (2.2 Radio/IR alignment); z/distance ~120 pc (Ophiuchus core)  
  > "DoAr 44 is located in the L1688 dark cloud of Ophiuchus" (1 Introduction); "so likely close to the distance of $+120.0_{-4.2}^{+4.5}$ pc derived for the Ophiuchus core by" (1 Introduction); "J2000 (16:31:33.4635, -24:27:37.222)" (2.2 Radio/IR alignment); distance from Loinard et al. 2008 (cite: Loinard2008ApJ...675L..29L)  
  > "DoAr 44 is located in the L1688 dark cloud of Ophiuchus" (1 Introduction); "so likely close to the distance of $+120.0_{-4.2}^{+4.5}$ pc derived for the Ophiuchus core by" (1 Introduction); "J2000 (16:31:33.4635, -24:27:37.222)" (2.2 Radio/IR alignment)

## Data provenance

- ALMA projects: 2013.1.00100.S
- bands: _not stated_
- frequencies and spectral setup: 336 GHz continuum  
  > "re-processing of archival 336 GHz ALMA observations" (abstract)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: natural-weight beam 0.35'' x 0.24''; super-resolved effective 0.17'' x 0.13''  
  > "(with a beam of $0.35\ensuremath{''}\times 0.24\ensuremath{''}$)" (6 ALMA image synthesis); "we obtained an effective angular resolution of $(0.17\ensuremath{''} \times
0.13\ensuremath{''})$" (6 ALMA image synthesis)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2014-07-26  
  > "Since the date of the ALMA observations is 2014-07-26" (2.2 Radio/IR alignment)
- pi or archival as stated: archival; data from van der Marel et al. 2016  
  > "re-processing of archival 336 GHz ALMA observations" (abstract)
- Other facility **VLT SPHERE+IRDIS**: H-band differential polarized imaging (Q_phi), project 096.C-0523(A), 15 March 2016, ~2560 s  
  > "DoAr 44 was acquired using SPHERE+IRDIS as part of project ` 096.C-0523(A)`." (2.1 Instrumental setups); "on March 15 2016, with a total exposure time of $\sim$2560 s" (2.1 Instrumental setups)
- Other facility **HSOY catalogue**: stellar position and proper motion  
  > "provides astrometric data for DoAr 44 at epoch 2000" (2.2 Radio/IR alignment)
- External data: SED photometry (USNO, 2MASS, IRAC, WISE, MIPS, AKARI, ALMA 880um, JCMT 1300um)  
  > "Observed total flux densities in DoAr 44" (Table 2) [from Table 2 footnotes (Zacharias 2013, Cutri, Ishihara, Andrews 2007, van der Marel 2016)]
- External data: Disk inclination 20 deg and PA 60 deg from molecular line data  
  > "consistent with the molecular line data presented by (cite: vdm2016A&A...585A..58V)" (2.3.1) [from (cite: vdm2016A&A...585A..58V)]
- Simulation/model as data: RADMC3D parametric warped-disk RT model predictions at 1.6um (Q_phi) and 336 GHz  
  > "The stellar radiation was transferred through the synthetic disk model using the RADMC3D RT package" (3.1 Parametric model)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: full continuum dataset self-calibrated (by van der Marel et al. 2016)  
  > "After self-calibration of the full continuum dataset (cite: vdm2016A&A...585A..58V)" (6 ALMA image synthesis)

### Imaging

- task: uvmem (GPU) maximum-entropy-family super-resolution with Laplacian regularization  
  > "we attempted to super-resolve the continuum data using our `uvmem` package" (6 ALMA image synthesis)
- deconvolver: _not stated_
- weighting robust: natural weights for dirty map/noise  
  > "$\sigma_D$ is the thermal noise in the natural-weights dirty map" (6 ALMA image synthesis)
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
- final beam: effective resolution 0.17'' x 0.13''  
  > "we obtained an effective angular resolution of $(0.17\ensuremath{''} \times
0.13\ensuremath{''})$" (6 ALMA image synthesis)
- final rms: _not stated_

### Inherited from earlier work

- SPHERE data reduction to Q_phi  
  > "The data were reduced following as in (cite: Avenhaus2017AJ....154...33A)" (2.1 Instrumental setups) [from (cite: Avenhaus2017AJ....154...33A)]
- RT model parametrization  
  > "The RT model follows from (cite: vdm2016A&A...585A..58V)." (3.1 Parametric model) [from (cite: vdm2016A&A...585A..58V)]
- Warp geometry formulae  
  > "The formulae in (cite: Min2017A&A...604L..10M) relate the inner disk orientation" (3.2.2) [from (cite: Min2017A&A...604L..10M)]

### Not stated but needed to reproduce (our reading)

- uvmem pixel size, image size and convergence settings
- Self-calibration solints and calibration details (deferred to van der Marel 2016)
- Exact MS/spectral windows used for continuum
- RT model photon numbers and grid
- Inclusion of the full SPHERE dataset reduction parameters

## Analysis recipe

1. **Super-resolve 336 GHz continuum**: uvmem maximum-entropy-type image synthesis with Laplacian regularization, lambda=0.01  
  > "We chose $\lambda = 0.01$, which is the highest value that preserved thermal residuals." (6 ALMA image synthesis)
   - software: uvmem
   - parameter: lambda = 0.01  
  > "We chose $\lambda = 0.01$, which is the highest value that preserved thermal residuals." (6 ALMA image synthesis)
   - fitting: _not stated_
   - validation: Monte Carlo simulations of RT model with same uv coverage, 100 noise realisations  
  > "The result of these Monte Carlo simulations, with 100 different realisation of noise" (2.3.6)
2. **Align and locate decrements and ring centroids**: Deproject (i=20, PA=60), search origin minimizing ring-radius dispersion, extract azimuthal profiles, find minima  
  > "We therefore optimized the origin so that the shape of the ring is the closest match to a perfect circle" (2.3.1)
   - parameter: origin search radius 50 mas  
  > "with a radius of 50 mas" (2.3.1)
   - assumption: i=20 deg, PA=60 deg  
  > "assuming an inclination $i=20~$deg and a disk position angle PA=60 deg" (2.3.1)
   - fitting: _not stated_
   - validation: uncertainties from plateau rms and noise realisations  
  > "For the DPI decrements, we used the rms scatter observed in the plateau around PA$\sim$60 deg, which is at $\sim$2% of the peak." (2.3.4 Depth of the decrements)
3. **Radiative transfer modelling of warped disk**: RADMC3D parametric two-dust-population model with tilted inner disk, compared with Q_phi(H) and 336 GHz and SED  
  > "We calculate equilibrium grain temperatures and emergent specific intensity maps." (3.1 Parametric model)
   - software: RADMC3D
   - parameter: Teff 4750 K, R*=1.5 Rsun, xi=30 deg  
  > "with $T_\mathrm{eff} = 4750$ K, $\log(g)=-4.0$, and with a stellar radius of $1.5~R_\odot$" (3.1 Parametric model)
   - assumption: 70% astro-silicates, 30% amorphous carbon, density 2.9 g cm-3, gas-to-dust 100  
  > "Grain optical properties were calculated using 70% astro-silicates, and 30% amorphous carbon" (7 Parametric RT model)
   - fitting: No parameter-space exploration; tilt chosen from arc-length ratio  
  > "Hence we do not explore parameter space to place uncertainties on each parameter." (7 Parametric RT model)
   - validation: Consistency with SED  
  > "which we required to be consistent with the SED" (3.1 Parametric model)
4. **Constrain geometry with MCMC**: Sample inner disk orientation and scale height from shadow positions using Min et al. formulae  
  > "We sampled the posterior distributions in inner disk orientation and outer disk scale aspect ratio $h$ using the `emcee` package" (3.2.2)
   - software: emcee
   - fitting: emcee; h posterior truncated to <0.5  
  > "the posterior distribution in $h$ was arbitrarily truncated to $<0.5$" (Footnote 5)
   - validation: _not stated_

## Software

- **uvmem** : super-resolution image synthesis of ALMA visibilities  
  > "we attempted to super-resolve the continuum data using our `uvmem` package" (6 ALMA image synthesis)
- **RADMC3D** 0.39: radiative transfer predictions  
  > "using the RADMC3D RT package (cite: RADMC3D0.39)" (3.1 Parametric model)
- **emcee** : posterior of inner disk orientation  
  > "using the `emcee` package" (3.2.2)
- **CASA statwt** : visibility weight/scatter estimate  
  > "using the scatter estimated with CASA task `statwt`" (2.3.6)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Q_phi(H) decrement depth | 88 | 1 | % | 2 | dropping by $100\%-f_s \sim
88\pm1$% |
| 336 GHz decrement depth | 24 | 6 | % | 2 | the radio decrements are rather shallow, with an average drop of only $\sim 24\pm 6$% |
| Radio/IR shadow PA shift eta_S | -2.8 | 0.9 | deg | 2 | $\eta_S = a_{336} - a_{H} = -2.8\pm0.9$ deg |
| Relative inner disk inclination | 30 | 5 | deg | 3 | We conclude that the relative disk inclination is likely $\xi=30\pm5~$deg. |
| 336 GHz ring radius | 0.309 | not stated | arcsec | 2 | The deconvolved 336 GHz continuum ring has a radius $\langle \rho
\rangle_{336} = 0.309$$''$ |
| Inner disk inclination from circle-geometry MCMC | 55.6 | +21/-11 | deg | 4 | $i_1 =55.6^{+21}_{-11}~$deg |

## Qualitative findings

- Radio dips coincide with the IR shadows but are much shallower; a tilted inner disk explains them.  
  > "The location of the optical and radio decrements are coincident, within fairly narrow uncertainties" (5 Conclusions)
- Inner disk tilt should be detectable with ALMA 12CO(6-5).  
  > "the proposed inner disk tilt in DoAr 44 should be detectable with ALMA in $^{12}$CO(6–5)" (4 Discussion)

## Claim tuples

- H: Are the DPI dips due to inclination effects alone? | E: RT models without inner disk at various inclinations | R: At 20 deg only very shallow decrements | F: A tilted inner disk is needed | **supported**
- H: Do radio and IR shadows coincide? | E: Compare decrement PA in deconvolved ALMA and Q_phi(H) | R: eta_S = -2.8±0.9 deg | F: Coincident, with deeper IR dips | **supported**
- H: What is the inner disk tilt? | E: RT arc-length comparison; MCMC geometry | R: xi=30±5 deg from arcs; geometry method loosely constrained (56.8 deg) | F: Tilt ~30 deg | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Beam comparable to ring radius smooths the profile, so super-resolution was used  
  > "the beam is comparable to the ring radius, and strongly smooths out the intensity profile along the ring" (6 ALMA image synthesis)
- Alternative: Warp-free models at higher inclination (~40 deg) or 60 deg warp rejected  
  > "these deeper decrements are quite different from the observations: they are much broader, aligned with the star" (3.1 Parametric model)
- How they decided it was enough: _not stated_
- Limitation (authors): Observed IR depths are lower limits due to PSF tails near coronagraph  
  > "the observed values should be considered as lower limits" (2.3.4)
- Limitation (authors): RT model parameters not explored for uncertainties  
  > "Hence we do not explore parameter space to place uncertainties on each parameter." (7 Parametric RT model)
- Caveat (inferred, ours): Tilt based on one hand-tuned RT model
- Caveat (inferred, ours): Super-resolved image biases depend on regularization
- Caveat (inferred, ours): Coronagraph and PSF systematics in the IR
- Caveat (inferred, ours): Astrometric uncertainty of ALMA ~25 mas

## Reproducibility

- Data public (paper): archival ALMA project 2013.1.00100.S  
  > "This work makes use of archival ALMA data from project 2013.1.00100.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: SPHERE reduced data and DARTTS-S reduction details
- Missing: uvmem settings
- Missing: full RT setup details
- Data volume (inferred): ~5-20 GB
- Score (inferred): 3/5, ALMA data are public and the model parameters are tabulated, but the imaging details, SPHERE data and code settings are incomplete.
- Rediscovery candidate: no, The central result relies on SPHERE data and a custom RT model with non-public settings.

## Links

- Method: (cite: Carcamo2018A&C....22...16C) (GPU uvmem)
- Method: (cite: Avenhaus2017AJ....154...33A) (SPHERE Q_phi reduction)
- Method: (cite: Min2017A&A...604L..10M) (shadow geometry formulae)
- Companion: (cite: vdm2016A&A...585A..58V) (original ALMA data analysis)
- Companion: (cite: Avenhaus2018arXiv180310882A) (DARTTS-S dataset)
- Related: DARTTS-S

## Checks

```json
{
 "quotes": 65,
 "quotes_ok": 65,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 45,
  "rate": 0.584
 },
 "evidence_ok": true
}
```
