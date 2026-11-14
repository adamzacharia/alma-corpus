# Resolving the molecular gas emission of the z ∼ 2.5─2.8 starburst galaxies SPT 0125-47 and SPT 2134-50

`2026A&A...705A..81K` | Astronomy and Astrophysics 2026 | first author: Kade, K. | arXiv: 2512.05093 | DOI: 10.1051/0004-6361/202451456

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: high_z_galaxies
- Question: What are the source-plane morphology and kinematics of the lensed DSFGs SPT 0125-47 and SPT 2134-50 from CO(3–2), and do they show clumps, companions or mergers?  
  > "We aim to resolve CO(3–2) emission toward two strongly lensed galaxies, SPT 0125-47 and SPT 2134-50, at $z \sim 2.5-2.8$ to determine their morphology and physical properties." (abstract)
- Target **SPT 0125-47**: coordinates SPT-S J012506-4723.7  
  > "SPT 0125-47 | 2.5148" (Table 2); "SPT-S J012506-4723.7 (hereafter, SPT 0125-47)" (Observations and data reduction); z/distance z = 2.5148  
  > "SPT 0125-47 | 2.5148" (Table 2); "SPT-S J012506-4723.7 (hereafter, SPT 0125-47)" (Observations and data reduction); distance from _not stated_
- Target **SPT 2134-50**: coordinates SPT-S J213403-5013.4  
  > "SPT 2134-50 | 2.7799" (Table 2); "SPT-S J213403-5013.4 (hereafter SPT 2134-50)" (Observations and data reduction); z/distance z = 2.7799  
  > "SPT 2134-50 | 2.7799" (Table 2); "SPT-S J213403-5013.4 (hereafter SPT 2134-50)" (Observations and data reduction); distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.01231.S
- bands: Band 3  
  > "were observed in band 3 as part of ALMA project ID 2016.1.01231.S (P.I. G. Drouart)." (Observations and data reduction)
- frequencies and spectral setup: spw central 98.476 GHz and 91.495 GHz; native channel width 3.9 MHz  
  > "SPT 2134-50 | CO(3–2) | 2017 09 25 | 91.495 | 3.9 | $0.15 \times 0.13, 76$ | 0.35" (Table 1)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.11x0.11'' (SPT 0125-47); 0.15x0.13'' (SPT 2134-50)  
  > "SPT 0125-47 | CO(3–2) | 2017 09 21 | 98.476 | 3.9 | $0.11 \times 0.11, 33$ | 0.4" (Table 1)
- max recoverable scale: ≈15.2'' (SPT 0125-47); ≈16.3'' (SPT 2134-50)  
  > "The maximum recoverable scale was $\approx 15.2''$ for SPT 0125-47 and $\approx 16.3''$ for SPT 2134-50." (Observations and data reduction)
- sensitivity: Cube 1σ = 0.5 mJy (SPT 0125-47), 0.36 mJy (SPT 2134-50) at ~70 km/s  
  > "where $1\sigma = 0.5$ mJy for SPT 0125-47 and $1\sigma = 0.36$ mJy for SPT 2134-50" (Observations and data reduction)
- time on source: _not stated_
- observing dates: SPT 0125-47: 2017 09 21; SPT 2134-50: 2017 09 25  
  > "SPT 0125-47 | CO(3–2) | 2017 09 21 | 98.476 | 3.9 | $0.11 \times 0.11, 33$ | 0.4" (Table 1); "SPT 2134-50 | CO(3–2) | 2017 09 25 | 91.495 | 3.9 | $0.15 \times 0.13, 76$ | 0.35" (Table 1)
- pi or archival as stated: Project of P.I. G. Drouart  
  > "were observed in band 3 as part of ALMA project ID 2016.1.01231.S (P.I. G. Drouart)." (Observations and data reduction)
- Line: CO J=3–2 (345.7959899 GHz)
- External data: Total molecular gas masses (CO(1–0)) and IR luminosities used for depletion times  
  > "using the total molecular gas mass and IR luminosity from (cite: Aravena16) and following the procedure within." (Implications) [from (cite: Aravena16)]
- External data: Lens Einstein radii used for prior upper limits and literature source morphology comparison  
  > "We set an upper limit on the Einstein radius for both sources as slightly larger than the Einstein radius reported for the sources in (cite: Spilker16)." (Parametric source modeling) [from (cite: Spilker16)]
- External data: Main-sequence depletion timescales for comparison  
  > "Both sources lie well below the expected depletion timescales for main sequence (MS) galaxies from (cite: Saintonge13)" (Implications) [from (cite: Saintonge13)]

## Processing

### Calibration

- pipeline or manual: ALMA calibration pipeline with additional manual flagging  
  > "additional flagging was added where necessary to ensure the calibration was satisfactory" (Observations and data reduction)
- casa version: CASA 4.7.2 (pipeline); CASA 5.6.2-3 (imaging)  
  > "The data for both sources were processed with the ALMA calibration pipeline in CASA 4.7.2" (Observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J2357-5311 (SPT 0125-47); J2056-4714 (SPT 2134-50)  
  > "J2357-5311 was used as the bandpass and flux calibrator" (Observations and data reduction)
- flux scale uncertainty: ~10%  
  > "We conservatively report the uncertainty in the absolute flux calibration to be $\sim 10\%$" (Observations and data reduction)
- self calibration: _not stated_

### Imaging

- task: CASA tclean  
  > "The pipeline-reduced measurement sets were used to create images using the CASA task TCLEAN with a Hogbom deconvolution" (Observations and data reduction)
- deconvolver: Hogbom  
  > "The pipeline-reduced measurement sets were used to create images using the CASA task TCLEAN with a Hogbom deconvolution" (Observations and data reduction)
- weighting robust: natural weighting  
  > "imaged using a natural weighting scheme with a spectral resolution of $\sim$70 km s$^{-1}$" (Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: cleaning in region of expected emission; cubes cleaned to 1σ  
  > "where cleaning was performed in the region of expected emission" (Observations and data reduction)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub, polynomial order 1  
  > "The continuum was subtracted using the CASA task UVCONTSUB with a polynomial fit of order 1" (Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.11x0.11'' PA 33 (SPT 0125-47); 0.15x0.13'' PA 76 (SPT 2134-50)  
  > "SPT 0125-47 | CO(3–2) | 2017 09 21 | 98.476 | 3.9 | $0.11 \times 0.11, 33$ | 0.4" (Table 1)
- final rms: 0.4 and 0.35 mJy/beam  
  > "SPT 2134-50 | CO(3–2) | 2017 09 25 | 91.495 | 3.9 | $0.15 \times 0.13, 76$ | 0.35" (Table 1)

### Inherited from earlier work

- Luminosity equations for line and line-prime luminosities  
  > "Integrated flux densities and line luminosities were calculated using the following equations from (cite: Solomon97):" (3.2 Line emission) [from (cite: Solomon97)]
- Nonparametric lens modeling methodology  
  > "We used a similar methodology to what has been employed for other studies that perform nonparametric lensing using PyAutoLens" (Nonparametric source modeling) [from (cite: Maresca22; Giulietti23; Perrotta23; Amvrosiadis25)]
- Depletion time procedure  
  > "using the total molecular gas mass and IR luminosity from (cite: Aravena16) and following the procedure within." (Implications) [from (cite: Aravena16)]

### Not stated but needed to reproduce (our reading)

- Line-free channels used for uvcontsub
- Annular aperture radii for spectrum/continuum extraction
- Cell size, image size and clean thresholds/masks
- Regularization coefficient values (file names hint at coefficients, not explained), mesh resolution, sampler and priors for PyAutoLens
- Channel ranges of red and blue bins and channels used in lens modeling
- Gaussian fitting details
- Private tclean scripts
- Gas-to-CO conversion/SFR values from Aravena16 for depletion times

## Analysis recipe

1. **Calibrate and image ALMA data**: ALMA pipeline calibration, extra flagging, tclean cubes and continuum, uvcontsub  
  > "The continuum was subtracted using the CASA task UVCONTSUB with a polynomial fit of order 1 for both SPT 0125-47 and SPT 2134-50." (Observations and data reduction)
   - software: CASA, tclean, uvcontsub
   - parameter: natural weighting, ~70 km/s channels  
  > "imaged using a natural weighting scheme with a spectral resolution of $\sim$70 km s$^{-1}$" (Observations and data reduction)
   - fitting: _not stated_
   - validation: Residual images checked for emission  
  > "The residual images were checked for emission to ensure that the cleaning was adequate." (Observations and data reduction)
2. **Extract continuum and line spectra, fit line, derive luminosities**: Annular aperture extraction without sigma cut, two-Gaussian fit, moment maps, Solomon97 luminosity equations  
  > "we fit the CO(3–2) emission with two Gaussian profiles (a single Gaussian does not provide a good fit to the data)" (3.2 Line emission)
   - software: CASA
   - parameter: per-channel rms from multiple emission-free regions matching extraction size  
  > "This involved sampling multiple emission-free regions of the cube in each channel, with the sampled regions matching the size of those used for spectrum extraction." (3.2 Line emission)
   - assumption: flat ΛCDM H0 = 70, Ωm = 0.3  
  > "we adopt a flat $\Lambda$ cold dark matter ($\Lambda$CDM) cosmology with ${H_{0}}$ = 70 km $\mathrm{s^{-1}\,Mpc^{-1}}$ and $\mathrm{\Omega_{m}}$ = 0.3" (Introduction)
   - fitting: Two Gaussian profiles  
  > "we fit the CO(3–2) emission with two Gaussian profiles" (3.2 Line emission)
   - validation: _not stated_
3. **Parametric uv-plane lens modeling**: PyAutoLens on uvcontsub visibilities, SIE lens, Sérsic source with linear light profiles, line channels only  
  > "we model the lens as a single isothermal ellipsoid (SIE) mass distribution assumed to not have light distributions" (Parametric source modeling)
   - software: PyAutoLens, CASA
   - parameter: lens centers fixed at Einstein ring centers with uniform priors; Einstein radius upper limit slightly above Spilker16  
  > "We fixed the centers of the mass distributions to be in the center of the observed Einstein rings using uniform priors." (Parametric source modeling)
   - fitting: Formal errors from sampling algorithms; sampler not named  
  > "are formal statistical errors from the sampling algorithms in the lens model fitting" (Nonparametric source modeling)
   - validation: Residuals checked at >3σ; compared with literature magnifications  
  > "We found a good parametric lens mass model for the CO(3–2) emission with no residuals at $>3\sigma$ levels." (SPT 0125-47)
4. **Nonparametric source reconstruction and error maps**: Adaptive Voronoi mesh with constant regularization using the optimized parametric lens model; error maps from visibility errors via statwt  
  > "This methodology employs an adaptive Voronoi mesh, maintaining regions of higher magnification and, thus, higher angular resolution, around the caustic lines in the source plane." (Nonparametric source modeling)
   - software: PyAutoLens, CASA statwt
   - parameter: constant regularization scheme with one coefficient  
  > "Here, we used a constant regularization scheme, which was parameterized by a regularization coefficient that regulated the smoothness of the emission." (Nonparametric source modeling)
   - fitting: _not stated_
   - validation: Source-plane S/N maps  
  > "making it straightforward to produce a S/N map in the source plane" (Nonparametric source modeling)
5. **Differential lensing and red/blue bin reconstructions**: Split line into red and blue bins, parametric lens modeling of each, then nonparametric source models  
  > "We investigated whether this is caused by differential lensing across the line profile by dividing each emission line into red and blue spectral bins." (Differential lensing)
   - software: PyAutoLens
   - fitting: _not stated_
   - validation: _not stated_
6. **Depletion times**: t_dep = SFR/M_gas using Aravena16 values  
  > "We calculated the depletion time ($\rm t_{dep} = SFR/M_{gas}$) for both sources" (Implications)
   - fitting: _not stated_
   - validation: Compared to other SPT sources  
  > "These values are in good agreement with the depletion times found for other SPT sources (cite: Aravena16)." (Implications)

## Software

- **CASA** 4.7.2 (pipeline), 5.6.2-3 (imaging): Calibration, tclean imaging, uvcontsub, statwt  
  > "The calibration and image processing steps were all performed in the Common Astronomy Software Application package (cite: CASA)." (Observations and data reduction)
- **PyAutoLens** : Parametric and nonparametric uv-plane lens modeling  
  > "The lens modeling for both sources was performed using the sophisticated publicly available lens modeling code PyAutoLens (cite: Autolens)." (Lens modeling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Magnification SPT 0125-47 (CO(3-2)) | 10.7 | 0.002 | dimensionless | 3 | we found a magnification factor of $\mu_{\rm CO(3-2)} = 10.7 \pm 0.002$ |
| Magnification SPT 2134-50 (CO(3-2)) | 7.6 | 0.002 | dimensionless | 3 | we find a magnification factor of $\mu_{\rm CO(3-2)} = 7.6 \pm 0.002$ |
| Differential magnification SPT 0125-47 | mu_blue ~14, mu_red ~9 | not stated | dimensionless | 5 | For SPT 0125-47, we found $\mu_{\rm blue} \sim 14$ and $\mu_{\rm red} \sim 9$. |
| Differential magnification SPT 2134-50 | mu_blue ~14, mu_red ~4.4 | not stated | dimensionless | 5 | For SPT 2134-50, we found $\mu_{\rm blue} \sim 14$ and $\mu_{\rm red} \sim 4.4$. |
| Continuum flux SPT 0125-47 | 1.9 | 1.4 | mJy | 2 | toward SPT 0125-47 at $1.9 \pm 1.4$ mJy (not corrected for lensing) |
| Continuum flux SPT 2134-50 | 1.1 | 0.7 | mJy | 2 | toward SPT 2134-50 at $1.1 \pm 0.7$ mJy (not corrected for lensing) |
| CO(3-2) integrated flux SPT 0125-47 | 2.1 | 1.0 | Jy km/s | 2 | SPT 0125-47 / 2.5148 / $5.0 \pm 2.5$ / $206 \pm 73$ / $2.1 \pm 1.0$ / $0.96 \pm 0.50$ / $0.73 \pm 0.35$ |
| CO(3-2) integrated flux SPT 2134-50 | 1.2 | 0.4 | Jy km/s | 2 | SPT 2134-50 / 2.7799 / $2.0 \pm 0.3$ / $394 \pm 128$ / $1.2 \pm 0.4$ / $0.62 \pm 0.22$ / $0.47 \pm 0.17$ |
| Depletion time SPT 0125-47 | 0.051 | not stated | Gyr | 6 | We found a depletion time of 0.051 Gyr for SPT 0125-47 and 0.037 Gyr for SPT 2134-50. |
| Depletion time SPT 2134-50 | 0.037 | not stated | Gyr | 6 | We found a depletion time of 0.051 Gyr for SPT 0125-47 and 0.037 Gyr for SPT 2134-50. |

## Qualitative findings

- Both sources are described by a single Sérsic profile; no clumps, companions or mergers seen; tentative velocity gradient.  
  > "We found tentative evidence of a velocity gradient across both sources and no evidence of any clumpy structure, companions, or ongoing mergers." (abstract)

## Claim tuples

- H: Does SPT 0125-47 require multiple source components as previously reported? | E: Parametric and nonparametric uv-plane lens modeling of CO(3–2) | R: Single Sérsic source gives a good fit with no residuals >3σ | F: Both sources are consistent with a single background source | **supported**
- H: Is there differential lensing across the line profile? | E: Parametric lens modeling of red and blue spectral bins | R: Blue bins magnified more strongly than red | F: Skewed profiles arise at least partly from differential lensing | **supported**
- H: Do the sources show ordered kinematics? | E: Nonparametric reconstructions of red and blue bins | R: Low S/N; tentative velocity gradient | F: Cannot be confirmed with current data | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: uv-plane modeling avoids bias from correlated image pixels; nonparametric avoids assumed morphology  
  > "pixels in interferometric images are not independent of one another; therefore, performing lens modeling directly on the images can bias the results of the lens model." (Lens modeling)
- Alternative: Continuum lens modeling rejected due to poor S/N; per-channel delensing attempts with ~10 and 3 channels failed  
  > "found that the signal-to-noise (S/N) of the data was too poor to obtain reasonable results." (Lens modeling)
- How they decided it was enough: _not stated_
- Limitation (authors): Low per-channel S/N prevents full delensed cubes; source plane resolution insufficient to resolve clumps; results preliminary.  
  > "these results should be considered as preliminary and require confirmation through deeper observations or observations of brighter emission lines" (Implications)
- Caveat (inferred, ours): Quoted lens parameter uncertainties are formal and very small (e.g. mu ±0.002)
- Caveat (inferred, ours): Lens model parameters poorly constrained (large asymmetric errors)
- Caveat (inferred, ours): Merger/settling interpretation is speculative given low S/N
- Caveat (inferred, ours): Magnification uncertainty not propagated into luminosities

## Reproducibility

- Data public (paper): Data are from ALMA project 2016.1.01231.S; public status implied by archive use  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.01231.S." (Acknowledgements)
- Products in archive: _not stated_
- Code: _not stated_
- Missing: Private tclean scripts and line-free channels
- Missing: PyAutoLens version, sampler, priors, regularization and mesh settings
- Missing: Aperture definitions
- Missing: Channel ranges of red/blue bins
- Data volume (inferred): ~20-50 GB raw for two Band 3 tracks
- Score (inferred): 5/5, Public data and named software, but key lens-modeling settings and scripts are missing.
- Rediscovery candidate: no, Lens modeling details are insufficiently specified to redo and the main results are partly qualitative.

## Links

- Method: (cite: Autolens) (PyAutoLens lens modeling code)
- Method: (cite: Solomon97) (Line luminosity equations)
- Companion: (cite: Spilker16) (Previous lens models of the same sources)
- Companion: (cite: Aravena16) (CO(1-0) gas masses and IR luminosities)
- Related: South Pole Telescope survey

## Checks

```json
{
 "quotes": 75,
 "quotes_ok": 75,
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
  "facts": 81,
  "stated": 53,
  "rate": 0.654
 },
 "evidence_ok": true
}
```
