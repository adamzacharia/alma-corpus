# Anomalously Narrow Line Widths of Compact Massive Star-forming Galaxies at z ∼ 2.3: A Possible Inclination Bias in the Size-Mass Plane

`2019ApJ...886L..28M` | The Astrophysical Journal Letters 2019 | first author: Mowla, Lamiya A. | arXiv: 1910.10722 | DOI: 10.3847/2041-8213/ab54d1

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Are the narrow Halpha line widths of compact massive star-forming galaxies at z~2.3 due to dust obscuration of high-velocity central gas? Measured via CO(3-2) line widths.  
  > "We used the Atacama Large Millimeter/submillimeter Array (ALMA) to observe three galaxies at $z \sim 2.3$ from the vD15 sample that have very small H$\alpha$ line widths" (1 Introduction)
- Target **COSMOS-27289**: coordinates _not stated_; z/distance z = 2.23  
  > "| COSMOS-27289 | 2.23 | 400 | 11.0 | 2.3 | 0.81 | 127$\pm$28 | 460 | **167$\pm$7** | 2.39 |" (Table 1); distance from 3D-HST catalogs (EAZY redshifts), via vD15  
  > "| COSMOS-27289 | 2.23 | 400 | 11.0 | 2.3 | 0.81 | 127$\pm$28 | 460 | **167$\pm$7** | 2.39 |" (Table 1)
- Target **COSMOS-1014**: coordinates _not stated_; z/distance z = 2.10  
  > "| COSMOS-1014 | 2.10 | 150 | 10.7 | 0.7 | 0.79 | 400$\pm$30 | 674 | **181$\pm$22** | 0.56 |" (Table 1); distance from 3D-HST catalogs (EAZY redshifts), via vD15  
  > "| COSMOS-1014 | 2.10 | 150 | 10.7 | 0.7 | 0.79 | 400$\pm$30 | 674 | **181$\pm$22** | 0.56 |" (Table 1)
- Target **GOODSS-5981**: coordinates _not stated_; z/distance z = 2.25  
  > "| GOODSS-5981 | 2.25 | 210 | 10.8 | 0.8 | 0.85 | 260$\pm$38 | 650 | **177$\pm$26** | 0.84 |" (Table 1); distance from 3D-HST catalogs (EAZY redshifts), via vD15  
  > "| GOODSS-5981 | 2.25 | 210 | 10.8 | 0.8 | 0.85 | 260$\pm$38 | 650 | **177$\pm$26** | 0.84 |" (Table 1)

## Data provenance

- ALMA projects: 2018.1.01841.S
- bands: Band 3  
  > "The observations were carried out in Band-3 using four spectral windows covering the rest-frame frequency range of $304-349$ GHz." (3.1 Observations and processing)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-3  
  > "in array configuration C43-3 (shortest and longest baselines were 15 and 1240 m, respectively)" (3.1 Observations and processing)
- baselines: 15 m to 1240 m  
  > "shortest and longest baselines were 15 and 1240 m, respectively" (3.1 Observations and processing)
- angular resolution: ~1.2 arcsec beam  
  > "The synthesized beam sizes are $\sim 1.2\mu{''}\times1.2\mu{''}$" (3.1 Observations and processing)
- max recoverable scale: _not stated_
- sensitivity: rms 0.20-0.25 mJy/beam over 50 km/s  
  > "the rms levels are 0.20–0.25 mJy/beam over 50 km s$^{-1}$ in the channel maps" (3.1 Observations and processing)
- time on source: 30-42 minutes per object  
  > "The on-source integration times were $30-42$ minutes" (3.1 Observations and processing)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=3-2 (not stated)
- Other facility **Keck MOSFIRE/NIRSPEC**: K-band Halpha spectroscopy (line widths), via vD15  
  > "K-band spectroscopy of 25 of these galaxies was obtained using the MOSFIRE and NIRSPEC spectrographs on Keck." (2 Sample Selection)
- Other facility **3D-HST / CANDELS**: redshifts, structural parameters, photometry  
  > "structural parameters were measured from CANDELS imaging" (2 Sample Selection)
- External data: Halpha line widths, sizes, masses, axis ratios of the sample  
  > "We describe three galaxies objectively selected from a sample of compact star-forming galaxies with H$\alpha$ measurements presented in vD15." (2 Sample Selection) [from van Dokkum et al. 2015 (cite: VanDokkum2015)]
- External data: CO(1-0) FWHM of only 60 km/s in COSMOS-27289  
  > "(cite: Spilker2016) find that the CO(1-0) line has a FWHM of only 60 km s in this galaxy" (5 Discussion) [from (cite: Spilker2016)]
- External data: ALMA 870um continuum effective radius 1.14 kpc and Sersic n 0.7 for G5  
  > "They find an effective radius of 1.14 kpc and a Sèrsic index of 0.7." (3.4 Spatially-resolved kinematics) [from (cite: Barro2016)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "We use the `tclean` task with natural weighting to make channel maps and dirty continuum maps excluding the frequency range of the CO line." (3.1 Observations and processing)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "We use the `tclean` task with natural weighting" (3.1 Observations and processing)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: binned to 50 km/s channels  
  > "to search for lines and the continuum the data were binned to a velocity width of 50 km s$^{-1}$." (3.1 Observations and processing)
- final beam: _not stated_
- final rms: 0.20-0.25 mJy/beam per 50 km/s  
  > "the rms levels are 0.20–0.25 mJy/beam over 50 km s$^{-1}$ in the channel maps" (3.1 Observations and processing)

### Inherited from earlier work

- Sample selection, Halpha data, and expected velocity dispersion formula  
  > "(see vD15)" (2 Sample Selection) [from van Dokkum et al. 2015 (cite: VanDokkum2015)]

### Not stated but needed to reproduce (our reading)

- Pixel/image size and cell size
- Line-free channels used for continuum
- Pipeline vs manual calibration and CASA version
- Flux calibrator and flux scale uncertainty
- Target coordinates and phase centers
- Fit procedure details for Gaussian line fits and errors
- Data for axis ratio vs size analysis (catalog selection, Fig 4)

## Analysis recipe

1. **Image cubes and continuum**: tclean with natural weighting; channels binned to 50 km/s; continuum excluding CO  
  > "We use the `tclean` task with natural weighting to make channel maps and dirty continuum maps excluding the frequency range of the CO line." (3.1 Observations and processing)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure CO(3-2) flux and luminosity**: moment-0 maps with immoment over -200 to 200 km/s; apertures 2" (C1, G5) or 3" (C2); L'CO from standard formula  
  > "We measure the total flux densities of the three galaxies from moment zero maps created using CASA task `immoment` within the velocity range of -200 to 200 km s$^{-1}$ centered on the CO line." (3.2 CO(3-2) Line Detection)
   - software: CASA immoment
   - fitting: _not stated_
   - validation: results unchanged when velocity range increased  
  > "we verified that our results do not change if we increase the velocity range" (3.2 CO(3-2) Line Detection)
3. **Measure CO line widths**: single Gaussian fit to spectra from circular aperture  
  > "We measure the integrated line widths of the galaxies by fitting a single Gaussian to the spectra, extracted with a 1.5 diameter circular aperture" (3.3 CO(3-2) linewidth)
   - fitting: _not stated_
   - validation: results not sensitive to aperture size  
  > "the results are not sensitive to the size of the aperture" (3.3 CO(3-2) linewidth)
4. **Spatially resolved kinematics and size**: per-spaxel single Gaussian fit for velocity field; uvmodelfit circular Gaussian on 200 km/s averaged cube for C2 size  
  > "We do a visibility fit of the emission in an averaged cube of width 200 km s$^{-1}$ and find a half-light radius of 2.5$\pm$0.5 kpc by fitting a circular Gaussian disk." (3.4 Spatially-resolved kinematics)
   - software: CASA uvmodelfit
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : data processing, tclean imaging, immoment, uvmodelfit  
  > "The data were processed through the Common Astronomy Software Application package (cite: Mcmullin2007)." (3.1 Observations and processing)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(3-2) FWHM COSMOS-27289 | 167 | 7 | km/s | 3 | **167$\pm$7** |
| CO(3-2) FWHM COSMOS-1014 | 181 | 22 | km/s | 3 | **181$\pm$22** |
| CO(3-2) FWHM GOODSS-5981 | 177 | 26 | km/s | 3 | **177$\pm$26** |
| CO half-light radius of COSMOS-27289 | 2.5 | 0.5 | kpc | 4 | find a half-light radius of 2.5$\pm$0.5 kpc by fitting a circular Gaussian disk |
| L'CO(3-2) COSMOS-27289 | 2.39 | not stated | 10^10 K km/s pc^2 | 2 | 2.39 |
| Significance of size-axis ratio correlation | 4 | not stated | sigma | 0 | There is indeed a correlation, with a significance of 4$\sigma$ |

## Qualitative findings

- CO line widths are similar to or narrower than Halpha, ~3x smaller than virial expectation; dust obscuration hypothesis rejected; face-on disks and inclination bias in the size-mass plane proposed  
  > "These results show that the narrow H$\alpha$ linewidths of many compact massive star-forming galaxies are not due to preferential obscuration of the highest velocity gas." (abstract)

## Claim tuples

- H: Narrow Halpha widths result from dust obscuration of high-velocity central gas | E: ALMA CO(3-2) observations of three compact massive SFGs | R: FWHM(CO)~165 km/s vs 450-700 km/s expected | F: Obscuration hypothesis rejected | **supported**
- H: There is an inclination bias in the size-mass plane | E: Compare size and axis ratio for massive SFGs | R: Anti-correlation between size and axis ratio | F: Face-on galaxies may appear more compact; not conclusive | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Different CO transition tracing different gas; central regions devoid of gas (quenched centers) - second judged hard to reconcile with UV-optical morphology and SEDs  
  > "However, it is difficult to reconcile with the rest-frame UV–optical morphology and spectral energy distributions of the galaxies." (5 Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Beam (~1.2") large compared to galaxy sizes, so spatially resolved kinematics inconclusive for two galaxies  
  > "Nothing conclusive can be said about either C1 or G5 and extent of the gas." (3.4 Spatially-resolved kinematics)
- Caveat (inferred, ours): Only three galaxies; small sample
- Caveat (inferred, ours): Single-Gaussian widths with low S/N may be biased
- Caveat (inferred, ours): Inclination bias argument rests on correlations that may reflect morphology differences
- Caveat (inferred, ours): Table CO widths for G5 (177) disagree with text (179), and C1/C2 labeling inconsistent

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Calibration/CASA version
- Missing: Imaging cell/image size
- Missing: Exact Gaussian fitting setup
- Missing: Axis-ratio catalog analysis details
- Data volume (inferred): ~10-50 GB raw for three Band 3 execution blocks
- Score (inferred): 3/5, Simple, short analysis on a single program, but several processing details are missing.
- Rediscovery candidate: no, Public status not stated in paper and processing details are sparse.

## Links

- Companion: van Dokkum et al. 2015 (cite: VanDokkum2015) (Parent sample and Halpha line widths)
- Companion: Mowla et al. 2019 (cite: Mowla2019) (Size-mass plane context)
- Related: 3D-HST
- Related: CANDELS
- Related: PHIBBS
- Related: ASPECS

## Checks

```json
{
 "quotes": 44,
 "quotes_ok": 44,
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
  "facts": 71,
  "stated": 33,
  "rate": 0.465
 },
 "evidence_ok": true
}
```
