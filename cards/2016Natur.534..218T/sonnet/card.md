# Cold, clumpy accretion onto an active supermassive black hole

`2016Natur.534..218T` | Nature 2016 | first author: Tremblay, Grant R. | arXiv: 1606.02304 | DOI: 10.1038/nature17969

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: galaxy_clusters_and_sz, agn_and_quasars
- Question: Is cold molecular gas falling in clumps toward the active supermassive black hole in the Abell 2597 BCG, as predicted by cold-accretion models?  
  > "Recent theory(cite: 5; 6; 7) and simulations(cite: 8; 9; 10) instead predict that accretion can be dominated by a stochastic, clumpy distribution of very cold molecular clouds" (abstract)
- Target **Abell 2597 BCG**: coordinates _not stated_; z/distance z = 0.0821; D_L = 373.3 Mpc  
  > "a nearby (redshift $\bm{z=0.0821}$) giant elliptical galaxy surrounded by a dense halo of hot plasma" (abstract); "$D_L$ its luminosity distance (373.3 Mpc), for which we assume a flat $\Lambda$CDM model wherein $H_0 =  70$ km s$^{-1}$ Mpc$^{-1}$, $\Omega_M =  0.3$, and $\Omega_{\Lambda} =  0.7$" (Mass Estimates.); distance from derived from z assuming flat LCDM, H0=70, Omega_M=0.3  
  > "a nearby (redshift $\bm{z=0.0821}$) giant elliptical galaxy surrounded by a dense halo of hot plasma" (abstract); "$D_L$ its luminosity distance (373.3 Mpc), for which we assume a flat $\Lambda$CDM model wherein $H_0 =  70$ km s$^{-1}$ Mpc$^{-1}$, $\Omega_M =  0.3$, and $\Omega_{\Lambda} =  0.7$" (Mass Estimates.)

## Data provenance

- ALMA projects: 2012.1.00988.S
- bands: Band 6, tuned to 213 GHz  
  > "ALMA’s Band 6 heterodyne receivers were tuned to a frequency of 213 GHz" (Observations, Data Reduction, and Analysis.)
- frequencies and spectral setup: FDM, 1875 MHz per baseband, 0.488 MHz channels (~2 km/s); one baseband on CO(2-1), three on continuum  
  > "delivered a bandwidth of 1875 MHz (per baseband) with a 0.488 MHz channel spacing, for a maximum spectral resolution of $\sim2$ km s$^{-1}$." (Observations, Data Reduction, and Analysis.); "One baseband was centered on the CO(2-1) line, while the other three sampled the local continuum." (Observations, Data Reduction, and Analysis.)
- continuum bandwidth: _not stated_
- arrays: 12m Array, 29 antennae, Cycle 1  
  > "obtained in Cycle 1 with the use of 29 operational antennae in the 12m Array" (Observations, Data Reduction, and Analysis.)
- configurations: _not stated_
- baselines: max ~1 km  
  > "Maximum antenna baselines extended to $\sim1$ km" (Observations, Data Reduction, and Analysis.)
- angular resolution: ~0.7 arcsec at 213 GHz; beam 0.715x0.533 arcsec  
  > "delivering an angular resolution at 213 GHz of $\sim 0\mbox{$.\!\!^{\prime\prime}$}7$ within a $\sim 28\mbox{$^{\prime\prime}$}$ primary beam (field of view)" (Observations, Data Reduction, and Analysis.)
- max recoverable scale: _not stated_
- sensitivity: 0.16 mJy per beam per 40 km/s channel  
  > "a final value of $0.16$ mJy per $0\mbox{$.\!\!^{\prime\prime}$}715\times0\mbox{$.\!\!^{\prime\prime}$}533$ beam per 40 km s$^{-1}$ channel" (Observations, Data Reduction, and Analysis.)
- time on source: ~3 hours over three scheduling blocks  
  > "ALMA observed the Abell 2597 BCG for a total of $\sim 3$ hours over three separate scheduling blocks" (Observations, Data Reduction, and Analysis.)
- observing dates: 17-19 November 2013  
  > "executed between 17-19 November 2013" (Observations, Data Reduction, and Analysis.)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (230.538001 GHz)
- Other facility **VLBA**: Archival high-resolution 1.3 and 5 GHz radio continuum and HI absorption showing pc-scale jet  
  > "These data resolve the 1.3 and 5 GHz radio continuum source down to scales of 25 parsecs" (main text)
- Other facility **IRAM 30m**: Previous CO(2-1) mass for comparison  
  > "based on an IRAM 30m CO(2-1) observation, of $\left(1.8\pm0.3\right) \times 10^9$ $M_{\odot}$" (Mass Estimates.)
- External data: Stellar velocity dispersion 220 ± 19 km/s  
  > "The stellar velocity dispersion of the BCG(cite: 24) is $\sigma_v = 220 \pm
19$ km s$^{-1}$." (Estimating physical properties of the redshifted absorbing gas.) [from Smith, Heckman & Illingworth 1990 (cite: 24)]
- External data: VLBA radio continuum and HI absorption data  
  > "given existing Very Long Baseline Array (VLBA) radio observations at extremely high spatial resolution(cite: 15)" (main text) [from (cite: 15) Tremblay et al. 2012]
- External data: Size-linewidth relation sigma_v = 1.0 S^0.5 km/s  
  > "$\sigma_v = \left(1.0 \pm 0.1 \right) S^{0.5\pm0.05}~\mathrm{km~s}^{-1}$" (Estimating physical properties of the redshifted absorbing gas.) [from Solomon et al. 1987 (cite: 26)]

## Processing

### Calibration

- pipeline or manual: CASA calibration scripts provided by the ARCs in Garching and Manchester  
  > "The data were reduced using casa version 4.2 with calibration and imaging scripts kindly provided by the ALMA Regional Centres (ARCs) in both Garching, Germany, and Manchester, UK." (Observations, Data Reduction, and Analysis.)
- casa version: CASA 4.2  
  > "The data were reduced using casa version 4.2" (Observations, Data Reduction, and Analysis.)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Neptune (flux); quasars J2258-2758 and J2331-1556 for amplitude/phase  
  > "The planet Neptune and quasars J2258-2758 and J2331-1556 were used for amplitude, flux, and phase calibration." (Observations, Data Reduction, and Analysis.)
- flux scale uncertainty: _not stated_
- self calibration: Iterative self-calibration on galaxy continuum; ~14% RMS decrease  
  > "we iteratively performed self-calibration of the data using the galaxy’s own continuum, yielding a $\sim 14\%$ decrease in RMS noise" (Observations, Data Reduction, and Analysis.)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "Measurement sets were imaged using ‘natural’ visibility weighting" (Observations, Data Reduction, and Analysis.)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Figures show continuum-subtracted CO(2-1) line emission  
  > "The figures presented in this paper show only continuum-subtracted, pure CO(2-1) line emission." (Observations, Data Reduction, and Analysis.)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Spectral binning to 5, 10 or 40 km/s  
  > "binning to either 5 km s$^{-1}$, 10 km s$^{-1}$ or 40 km s$^{-1}$, as indicated in the figure captions" (Observations, Data Reduction, and Analysis.)
- final beam: 0.715 x 0.533 arcsec  
  > "per $0\mbox{$.\!\!^{\prime\prime}$}715\times0\mbox{$.\!\!^{\prime\prime}$}533$ beam" (Observations, Data Reduction, and Analysis.)
- final rms: 0.16 mJy/beam per 40 km/s channel  
  > "a final value of $0.16$ mJy per $0\mbox{$.\!\!^{\prime\prime}$}715\times0\mbox{$.\!\!^{\prime\prime}$}533$ beam per 40 km s$^{-1}$ channel" (Observations, Data Reduction, and Analysis.)

### Inherited from earlier work

- CO-to-H2 conversion and mass relation  
  > "All molecular gas masses estimated in this letter adopt the following relation(cite: 32):" (Mass Estimates.) [from Bolatto, Wolfire & Leroy 2013 (cite: 32)]

### Not stated but needed to reproduce (our reading)

- Continuum-subtraction channel ranges and method
- Image size, cell size, deconvolution/clean threshold and masks
- Aperture used for total CO(2-1) flux
- Self-calibration solution intervals and iterations
- Gaussian fitting details for absorption lines (errors, continuum level)
- Pixel/region for central-beam spectrum extraction
- Sky coordinates of target

## Analysis recipe

1. **Calibrate, self-calibrate and image the cube**: ARC-provided CASA scripts, self-calibration on continuum, natural-weight imaging, continuum subtraction  
  > "The data were reduced using casa version 4.2 with calibration and imaging scripts kindly provided by the ALMA Regional Centres (ARCs)" (Observations, Data Reduction, and Analysis.)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared self-calibrated and non-self-calibrated cubes  
  > "There is effectively no difference in CO(2-1) morphology between the self- calibrated and non-self-calibrated cubes." (Observations, Data Reduction, and Analysis.)
2. **Derive total molecular gas mass**: Single Gaussian fit to integrated CO(2-1) spectrum, convert to H2 mass  
  > "A single gaussian fit to the CO(2-1) spectrum extracted from an aperture containing all detected emission yields an emission integral of $S_{\mathrm{CO}}\Delta v = 4.2\pm0.4$ Jy km s$^{-1}$" (Mass Estimates.)
   - software: CASA
   - assumption: X_CO = 2e20 cm^-2 (K km/s)^-1; CO(2-1)/CO(1-0) flux ratio 3.2; D_L=373.3 Mpc  
  > "we assume the average Milky Way value of $X_{\mathrm{CO}} = 2 \times 10^{20}$ cm$^{-2}$ $\left(\mathrm{K~km~s}^{-1}\right)^{-1}$ and a CO(2-1) to CO(1-0) flux density ratio of $3.2$" (Mass Estimates.)
   - fitting: Gaussian fit  
  > "A single gaussian fit to the CO(2-1) spectrum extracted from an aperture containing all detected emission yields an emission integral of $S_{\mathrm{CO}}\Delta v = 4.2\pm0.4$ Jy km s$^{-1}$" (Mass Estimates.)
   - validation: Compared with IRAM 30m mass  
  > "This is very close to the previously reported(cite: 13) mass, based on an IRAM 30m CO(2-1) observation" (Mass Estimates.)
3. **Detect and characterise absorption against the nuclear continuum**: Extract CO(2-1) spectrum from central beam; Gaussian fits to absorption lines; tau from I_total = I_cont exp(-tau)  
  > "found by extracting the CO(2-1) spectrum from this central beam" (main text); "$$I_{\mathrm{total}} = I_{\mathrm{continuum}}\mathrm{e}^{-\tau_{\mathrm{CO(2-1)}}}$$" (Estimating physical properties of the redshifted absorbing gas.)
   - software: CASA
   - fitting: Gaussian fits to absorption features  
  > "Gaussian fits to the spectral absorption features reveal narrow linewidths of $\sigma_v \mathrel{<\kern-1.0em\lower 0.9ex\hbox{$\sim$}}6$ km s$^{-1}$" (main text)
   - validation: Line shapes unchanged under different spectral binning  
  > "The shapes of the absorption lines remain roughly the same regardless of how finely the spectra are binned" (main text)
4. **Estimate cloud size and mass**: Solomon et al. size-linewidth relation for size; virial relation for mass  
  > "A measured absorber linewidth of $\sigma_v \sim 6$ km s$^{-1}$ would then correspond to a size of $\sim 36$ pc." (Estimating physical properties of the redshifted absorbing gas.)
   - assumption: Milky Way size-linewidth relation applies (upper limit); virial equilibrium  
  > "If the absorbers are in virial equilibrium, their masses $M_{\mathrm{cloud}}$ can be roughly estimated by applying the virial relation" (Estimating physical properties of the redshifted absorbing gas.)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.2: Data reduction, imaging and Gaussian line fitting  
  > "Reduction of the data as well as some simple modeling (e.g., fitting of Gaussians to lines) was performed using routines included in CASA version 4.2" (Code, software, and data availability.)
- **Astropy** : General analysis  
  > "This research made use of Astropy (<http://www.astropy.org>)" (Code, software, and data availability.)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total H2 gas mass | 1.80e9 | 0.19e9 | Msun | 2 | $M_{\mathrm{H}_2}  = \left(1.80 \pm 0.19\right) \times 10^9$ $M_{\odot}$ |
| CO(2-1) emission integral | 4.2 | 0.4 | Jy km/s | 2 | $S_{\mathrm{CO}}\Delta v = 4.2\pm0.4$ Jy km s$^{-1}$ with a line FWHM of $252 \pm 14$ km s$^{-1}$ |
| CO(2-1) line FWHM | 252 | 14 | km/s | 2 | with a line FWHM of $252 \pm 14$ km s$^{-1}$ |
| Absorption line centres | +240, +275, +335 | not stated | km/s | 3 | redshifted line centres at $+240$, $+275$, and $+335$ km s$^{-1}$ relative to the systemic (stellar) velocity |
| Nuclear continuum flux | 13.6 | not stated | mJy | 3 | 13.6 mJy at rest-frame 230 GHz |
| Absorber linewidth | <~6 | not stated | km/s | 3 | narrow linewidths of $\sigma_v \mathrel{<\kern-1.0em\lower 0.9ex\hbox{$\sim$}}6$ km s$^{-1}$ |
| Absorber optical depth | 0.1-0.3 | not stated | dimensionless | 3 | $0.1 \mathrel{<\kern-1.0em\lower 0.9ex\hbox{$\sim$}}\tau_{\mathrm{CO(2-1)}} \mathrel{<\kern-1.0em\lower 0.9ex\hbox{$\sim$}}0.3$ |
| Virial cloud mass | 1.7e5 | not stated | Msun | 4 | \approx 1.7\times10^5~M_\odot, |

## Qualitative findings

- Redshifted narrow CO(2-1) absorption against the nuclear continuum shows cold clouds infalling at ~300 km/s, likely within ~100 pc of the black hole  
  > "revealing ‘shadows’ cast by the molecular clouds as they move inward at about $\bm{300}$ kilometres per second towards the active supermassive black hole" (abstract)

## Claim tuples

- H: Cold molecular clouds fall toward the AGN in a clumpy accretion flow | E: ALMA CO(2-1) spectrum extracted from beam on the continuum core | R: Three narrow redshifted absorption lines at +240, +275, +335 km/s with sigma<~6 km/s | F: Cold clumpy clouds are infalling toward the black hole | **supported**
- H: Absorbers lie close to the black hole | E: Compare with VLBA HI absorption and geometric/probability arguments | R: HI infall velocity matches; gas confined to innermost 2 kpc in emission | F: Clouds are within tens to ~100 pc | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Clouds could be in non-circular bound orbits rather than radial infall; transverse velocity unknown  
  > "If most of the clouds are instead locked in non-circular orbits around the black hole, the fuelling rate would depend on the gas angular momentum" (main text)
- How they decided it was enough: _not stated_
- Limitation (authors): Optical depth/covering factor uncertain due to beam contamination by emission  
  > "the covering factor cannot be known with certainty" (main text)
- Caveat (inferred, ours): Absorber distance from the black hole is inferred indirectly, not measured
- Caveat (inferred, ours): Mass and size estimates rely on Milky Way X_CO and size-linewidth relations
- Caveat (inferred, ours): Systemic velocity chosen from CO emission peak

## Reproducibility

- Data public (paper): Raw ALMA data public; analysis code on GitHub  
  > "The raw ALMA data used in this Letter are publicly available at the ALMA Science Archive" (Code, software, and data availability.)
- Products in archive: _not stated_
- Code: https://github.com/granttremblay/Tremblay_Nature_ALMA_Abell2597  
  > "Codes that we have written to both reduce and analyse the ALMA data have been made publicly available here" (Code, software, and data availability.)
- Missing: Details of line-fitting apertures and continuum channel selection (may be in released code)
- Data volume (inferred): ~10-50 GB raw
- Score (inferred): 4/5, Public data, released code, simple analysis, few settings missing from the text.
- Rediscovery candidate: yes, Public data, code released, numeric results (mass, line centres, tau) reproducible.

## Links

- Method: Bolatto, Wolfire & Leroy 2013 (cite: 32) (CO-to-H2 mass relation)
- Companion: Tremblay et al. 2012 (cite: 15) (VLBA and prior observations of Abell 2597)

## Checks

```json
{
 "quotes": 61,
 "quotes_ok": 61,
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
  "facts": 69,
  "stated": 44,
  "rate": 0.638
 },
 "evidence_ok": true
}
```
