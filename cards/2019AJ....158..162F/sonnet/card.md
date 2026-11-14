# From Scattered-light to Millimeter Emission: A Comprehensive View of the Gigayear-old System of HD 202628 and its Eccentric Debris Ring

`2019AJ....158..162F` | The Astronomical Journal 2019 | first author: Faramaz, Virginie | arXiv: 1909.04162 | DOI: 10.3847/1538-3881/ab3ec1

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: debris_disks
- Question: What are the geometry, eccentricity, dust size distribution and gas content of the HD 202628 debris ring, and what do they imply for its belt-shaping perturber?  
  > "The offset of the ring centre of symmetry from the star allows us to quantify its eccentricity to be $e=0.09_{-0.01}^{+0.02}$." (abstract)
- Target **HD 202628**: coordinates 21h18m27.653s, -43d20m04.267s (ALMA fitted stellar position)  
  > "HD 202628 (HIP 105184) is a G2V star, located at 23.8 pc (cite: Collaboration2016; Collaboration2018; Bailer-Jones2018)" (Introduction); z/distance 23.8 pc  
  > "HD 202628 (HIP 105184) is a G2V star, located at 23.8 pc (cite: Collaboration2016; Collaboration2018; Bailer-Jones2018)" (Introduction); distance from Gaia (Gaia Collaboration 2018; Bailer-Jones 2018)  
  > "HD 202628 (HIP 105184) is a G2V star, located at 23.8 pc (cite: Collaboration2016; Collaboration2018; Bailer-Jones2018)" (Introduction)

## Data provenance

- ALMA projects: 2016.1.00515.S
- bands: Band 6 (230 GHz, 1.3 mm)  
  > "ALMA observations of HD 202628 in Band 6 (230 GHz, 1.3mm)" (2.1 ALMA Band 6 Observations)
- frequencies and spectral setup: Four 2 GHz SPWs; three at 232.5, 245.5, 247.5 GHz (128 channels, 15.625 MHz); fourth at 230.5 GHz for CO, 0.5 MHz (~0.6 km/s) resolution  
  > "Three were centred on 232.5, 245.5, and 247.5 GHz, and divided into 128 channels of width 15.625 MHz" (2.1 ALMA Band 6 Observations)
- continuum bandwidth: _not stated_
- arrays: 12m array and ACA  
  > "They comprise 12m-array observations carried out from 2017 April 15 to 2017 April 29, and observations carried out with the Atacama Compact Array (ACA)" (2.1 ALMA Band 6 Observations)
- configurations: _not stated_
- baselines: ACA 8.9-48.0 m; 12m 15.1-460.0 m  
  > "12m-array data were taken using baselines ranging from 15.1 to 460.0 m" (2.1 ALMA Band 6 Observations)
- angular resolution: 0.92" x 0.75", PA 83 deg  
  > "The resulting synthesized beam has dimensions $0\ensuremath{''}.92 \times 0\ensuremath{''}.75$, with position angle (PA) $83^{\circ}$." (3.1 ALMA Band 6 Observations)
- max recoverable scale: _not stated_
- sensitivity: 5.2 uJy/beam continuum rms  
  > "was found to be $\sigma=5.2\,\mu\mathrm{Jy.beam}^{-1}$" (3.1 ALMA Band 6 Observations)
- time on source: 9.8 h ACA, 5.3 h 12m array  
  > "The total time on source was 9.8 hours with the ACA and 5.3 hours with the 12m array." (2.1 ALMA Band 6 Observations)
- observing dates: ACA 2016 Oct 19 - Nov 2; 12m 2017 Apr 15-29  
  > "observations carried out with the Atacama Compact Array (ACA) from 2016 October 19 to 2016 November 2" (2.1 ALMA Band 6 Observations)
- pi or archival as stated: Own program, PI V. Faramaz  
  > "under the project 2016.1.00515.S (PI: V. Faramaz)" (2.1 ALMA Band 6 Observations)
- Line: CO J=2-1 (230.538 GHz)
- Other facility **Herschel PACS/SPIRE**: 70-500 um photometry and images  
  > "*Herschel*/PACS observations using the mini scan map AOT (Astronomical Observing Template) took place on 2012 March 28." (2.2 Herschel)
- Other facility **HST/STIS**: Coronagraphic scattered-light images (GO-12291, 13455, 13786)  
  > "HD 202628 has been observed with the *HST*/STIS coronagraph $(0."05\,\mathrm{pixel}^{-1})$ in three separate Guest Observer (GO) programs" (2.3 HST/STIS)
- External data: Gaia astrometry and stellar parameters (Teff, mass etc.)  
  > "| Mass(tracks) | 1.050 $\pm$ 0.006 M$_{\odot}$ | (cite: Spina2018) |" (Table 7) [from (cite: Collaboration2018; Spina2018)]
- External data: Optical/IR photometry (2MASS, WISE, Spitzer/MIPS)  
  > "| 23.8 | 0.059 | 0.0024 | *Spitzer*/MIPS; (cite: Sierchio2014) |" (Table 6) [from (cite: Cutri2003; Cutri2012; Sierchio2014)]

## Processing

### Calibration

- pipeline or manual: ALMA-provided pipeline  
  > "Calibrations were applied using the pipeline provided by ALMA." (3.1 ALMA Band 6 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10% absolute flux uncertainty  
  > "(including a 10% absolute flux uncertainty)" (3.1.3 The ring)
- self calibration: _not stated_

### Imaging

- task: tclean in CASA 5.1.1, four SPWs combined  
  > "We used the *TCLEAN* algorithm in CASA (Common Astronomy Software Applications) version 5.1.1" (3.1 ALMA Band 6 Observations)
- deconvolver: _not stated_
- weighting robust: natural  
  > "We used a natural weighting scheme, a cell size of $0\ensuremath{''}.08$" (3.1 ALMA Band 6 Observations)
- uv taper: _not stated_
- cell size: 0.08"  
  > "a cell size of $0\ensuremath{''}.08$, and an image size of $800\times 800$ pixels" (3.1 ALMA Band 6 Observations)
- image size: 800x800 pixels  
  > "an image size of $800\times 800$ pixels in order to cover the primary beam" (3.1 ALMA Band 6 Observations)
- masking: mask from best-fit disk model  
  > "a mask generated with our disk best fit model" (3.1 ALMA Band 6 Observations)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub in CASA 5.1.0 (CO cube)  
  > "We subtracted continuum emission from the visibilities using the *uvcontsub* task in CASA v5.1.0." (2.1 ALMA Band 6 Observations)
- line free channels: _not stated_
- primary beam correction: applied  
  > "We further corrected the image for the primary beam" (3.1 ALMA Band 6 Observations)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.92" x 0.75", PA 83 deg  
  > "The resulting synthesized beam has dimensions $0\ensuremath{''}.92 \times 0\ensuremath{''}.75$" (3.1 ALMA Band 6 Observations)
- final rms: 5.2 uJy/beam  
  > "was found to be $\sigma=5.2\,\mu\mathrm{Jy.beam}^{-1}$" (3.1 ALMA Band 6 Observations)

### Inherited from earlier work

- Ray-tracing disk model code adapted to debris disks  
  > "The model disk emission is computed thanks to the ray-tracing disk code first developed by (cite: Rosenfeld2013) and (cite: Flaherty2015)" (3.1.3 The ring) [from (cite: Rosenfeld2013; Flaherty2015; Daley2019)]
- Spectro-spatial filtering for CO  
  > "we use the spectro-spatial filtering technique of (cite: Matra2015; Matra2017a)" (3.1.4 Gas content) [from (cite: Matra2015; Matra2017a)]
- Dynamical framework for perturber constraints  
  > "we nevertheless adopt the theoretical framework of (cite: Pearce2014)" (4.1 Theoretical constraints) [from (cite: Pearce2014)]
- ADI algorithm and SED modeling approach  
  > "the same iterative ADI algorithm used here was described in that paper" (2.3 HST/STIS) [from (cite: Krist2010)]
- Grain size index derivation from spectral index  
  > "Using their Equation (1), and adopting their values for the dust opacity and Planck function spectral indices" (3.2.2 Photometry and SED modeling) [from (cite: Ricci2012)]

### Not stated but needed to reproduce (our reading)

- MCMC walkers, steps, burn-in and priors for the 23-parameter fit
- Initial guesses/bounds for model parameters
- Stellar luminosity/temperature used in dust temperature
- Flux-calibration and pipeline CASA version used for calibration
- Details of source Gaussian model priors
- CO imaging channel/velocity range and ring mask exact definition
- Scattered-light ADI code not released

## Analysis recipe

1. **Image continuum**: tclean of combined 12m+ACA continuum, natural weighting, model-based mask, primary-beam corrected  
  > "We combined the four spectral windows in order to recover the maximum signal-to-noise ratio (SNR)" (3.1 ALMA Band 6 Observations)
   - software: CASA
   - parameter: cell 0.08", 800x800 pixels  
  > "a cell size of $0\ensuremath{''}.08$, and an image size of $800\times 800$ pixels" (3.1 ALMA Band 6 Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit ring geometry in visibility space**: MCMC fit of circular constant-surface-density ring model plus Gaussian sources, Fourier transformed to visibilities  
  > "we used the Python `emcee` procedure (cite: Foreman-Mackey2013), which allows us to perform an MCMC (Markov Chain Monte Carlo) fit of a debris disk model emission to our observations." (3.1.3 The ring)
   - software: emcee, disk_model ray-tracing code
   - parameter: 23 free parameters (7 ring incl. centre offset, plus Gaussian sources)  
  > "The total number of free parameters in our model is therefore 23." (3.1.3 The ring)
   - assumption: Blackbody grains, opacity 2.3 cm^2/g, constant surface density  
  > "its opacity is set to $2.3\mathrm{cm^2/g}$" (3.1.3 The ring)
   - fitting: emcee; errors are 16-84 percentiles  
  > "Error bars correspond to the 16-84 percentiles values." (Table 5)
   - validation: Residual map after model subtraction; consistency with HST  
  > "In Figure [3](#fig:model), we show our best fit model, along with the residuals once the model is subtracted from our observations." (3.1.3 The ring)
3. **Derive eccentricity from star-ring offset**: Eccentricity = projected offset / projected inner-edge semimajor axis, using ALMA-detected stellar position  
  > "the ring’s true eccentricity is thus also equal to the ratio between the projected offset and the projected semimajor axis." (3.1.3 The ring)
   - fitting: _not stated_
   - validation: Compared with independent visual HST ellipse fits (e=0.14)  
  > "Similar, independent visual fits to the new, combined *HST* yields an eccentricity of $0.14 \pm 0.02$" (3.1.3 The ring)
4. **Measure bright sources**: Elliptical Gaussian fits in CASA viewer on disk-model-subtracted image  
  > "within the CASA viewer, we performed an elliptical Gaussian fit over a rectangular region encompassing the source." (3.1.2 Bright sources)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
5. **Search for CO gas and derive upper limits**: Keplerian-shifted spectro-spatial filtering within ring mask; non-LTE excitation with UV/IR fluorescence for mass limit  
  > "We begin by shifting the spectra in each of the cube’s pixels by the negative of the Keplerian velocity expected at that belt location." (3.1.4 Gas content)
   - software: CASA
   - parameter: Tkin 10-250 K; stellar mass 1 Msun  
  > "kinetic temperatures between 10 and 250 K" (3.1.4 Gas content)
   - assumption: Gas co-located with belt, Keplerian, optically thin  
  > "any gas present is co-located with the belt’s continuum emission and moving at Keplerian velocity around the central star" (3.1.4 Gas content)
   - fitting: _not stated_
   - validation: _not stated_
6. **Grain size distribution from spectral index**: Spectral index from ALMA 1.3 mm and SPIRE fluxes converted to q via Ricci et al. 2012 Eq. 1  
  > "we find that the index $-q$ of the grain size distribution power-law in the debris disk of HD 202628 is $-3.39\pm0.15$" (3.2.2 Photometry and SED modeling)
   - parameter: beta_s=1.8±0.2, alpha_Pl=1.84±0.02  
  > "($\beta_s=1.8\pm 0.2$ and $\alpha_\mathrm{Pl}=1.84\pm 0.02$)" (3.2.2 Photometry and SED modeling)
   - fitting: _not stated_
   - validation: Compared with Dohnanyi -3.5  
  > "in accordance not only with the theoretical Dohnanyi value of -3.5" (3.2.2 Photometry and SED modeling)
7. **Constrain perturber**: Secular theory (forced eccentricity, chaotic zone, timescales) of Pearce & Wyatt 2014 with updated ring geometry; S1 extent as Hill-radius constraint  
  > "2 a_p \left( \frac{m_p}{3M_\star} \right)^{1/3} = 13.8 \mathrm{AU}" (4.2)
   - assumption: Single inner perturber; circumplanetary material fills Hill radius  
  > "assuming that circumplanetary material fills the perturber’s Hill radius" (4.2)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.1.1 (imaging); 5.1.0 (uvcontsub): Imaging, continuum subtraction, source fitting  
  > "version 5.1.1 (cite: McMullin2007)" (3.1 ALMA Band 6 Observations)
- **emcee** : MCMC fit of ring model  
  > "we used the Python `emcee` procedure (cite: Foreman-Mackey2013)" (3.1.3 The ring)
- **HIPE** 10: Herschel/PACS mosaics  
  > "customized routines in Version 10 of the *Herschel* Interactive Processing Environment (HIPE) software package" (2.2 Herschel)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Ring inner radius | 143.1 | 1.7 | AU | 2 | Inner radius (AU) / $143.1\pm 1.7$ |
| Ring outer radius | 165.5 | 1.4 | AU | 2 | Outer radius (AU) / $165.5 \pm 1.4$ |
| Inclination | 57.4 | 0.4 | deg | 2 | Inclination $(^\circ)$ / $57.4\pm 0.4$ |
| Eccentricity | 0.09 | +0.02/-0.01 | dimensionless | 3 | Eccentricity / $0.09_{-0.01}^{+0.02}$ |
| Dust disk mass (mm grains) | 1.36e-2 | 0.06e-2 | Earth masses | 2 | $(1.36\pm0.06)\times10^{-2}$ |
| Total ring flux 1.3 mm | 959 | 96 | uJy | 2 | is found to be $959\pm 96\,\mu\mathrm{Jy}$ |
| Stellar peak flux at 1.3 mm | 29.3 | 5.2 | uJy/beam | 1 | $29.3\pm 5.2\mu\mathrm{Jy.beam}^{-1}$ |
| S1 integrated flux | 285 | 18 | uJy | 4 | $285\pm18$ |
| Grain size index -q | -3.39 | 0.15 | dimensionless | 6 | $-3.39\pm0.15$ |
| Mean spectral index | 2.54 | 0.15 | dimensionless | 6 | it is thus equal to $2.54 \pm 0.15$ |
| CO J=2-1 3sigma flux upper limit | 12 | not stated | mJy km/s | 5 | 3\sigma$ upper limit on the integrated CO J=2-1 line flux within the HD202628 belt of 12 mJy km/s |
| CO mass 3sigma upper limits | 1.4-26e-7 | not stated | Earth masses | 5 | $3\sigma$ CO mass upper limits between $1.4-26\times10^{-7}$ M$_{\oplus}$ |
| Minimum grain size a_min | 3.2 | not stated | um | 0 | a$_{min}$ is found to be 3.2 $\mu$m |
| Perturber if S1 is circumplanetary | m=0.8 MJup, a=107.5 AU, e=0.1 | not stated | MJup, AU | 7 | $m_{\mathrm{p}}=0.8\,\mathrm{M_{Jup}}$, $a_{\mathrm{p}}=107.5\,\mathrm{AU}$, and $e_{\mathrm{p}}=0.1$ |

## Qualitative findings

- Ring inner edge consistent between ALMA and HST; ring broader in scattered light due to radiation pressure  
  > "The ring inner edge is found to be consistent between ALMA and *HST* data." (abstract)
- Pericenter glow detected at 70 um with Herschel  
  > "The surface brightness in this region is roughly 30% brighter than at a comparable distance East of the star." (3.2.1)

## Claim tuples

- H: Is the ring intrinsically eccentric, and how much? | E: Visibility-space MCMC ring fit plus ALMA star position | R: e=0.09 (+0.02/-0.01), smaller than HST value | F: Ring is eccentric with e~0.1 | **supported**
- H: Is in-situ formation of the perturber possible (steep grain size distribution)? | E: Spectral index ALMA+SPIRE to grain size index | R: q = 3.39±0.15 | F: Excludes in-situ formation requiring q~4.5-5.5 | **supported**
- H: Is there CO gas affecting ring dynamics? | E: Spectro-spatial filtering of CO J=2-1 | R: No detection; mass limits 1.4-26e-7 Mearth | F: Gas does not shape the ring | **supported**
- H: Is source S1 circumplanetary material of the perturber? | E: Compared with background-source counts, HST non-detection and Hill-radius constraint | R: Cannot be excluded; implies 0.8 MJup at 107.5 AU | F: Possible but unconfirmed; needs second epoch | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Star detection needed to measure offset because ALMA beam cannot distinguish circular ring from e=0.2 ring shape  
  > "with ALMA observations of the ring only, one would not be able to disentangle a projected circular ring from a ring of eccentricity 0.2." (3.1.3 The ring)
- Alternative: S1 as background galaxy (2.4 expected brighter than S3 in ACA primary beam)  
  > "we would expect 2.4 background sources brighter than S3 (the faintest of the sources)" (4.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Apocenter-glow detection remains qualitative; lacks sensitivity  
  > "our observations lack the sensitivity for us to be formally conclusive." (3.1.3 The ring)
- Limitation (authors): Perturber constraints are degenerate without extra constraint; S1 comoving unknown  
  > "Whether the source S1 is co-moving or not cannot be ascertained without second epoch observations." (4.2)
- Caveat (inferred, ours): Constant surface density circular ring model with only barely resolved width
- Caveat (inferred, ours): Opacity 2.3 cm^2/g uncertain by factor ~5, affecting mass
- Caveat (inferred, ours): Observed 1.3 mm flux lower than predicted; star flux above photosphere
- Caveat (inferred, ours): Hill-radius argument for S1 relies on strong assumptions
- Caveat (inferred, ours): Single inner perturber assumed, no N-body

## Reproducibility

- Data public (paper): Project code given; code for disk model public on GitHub  
  > "This code is publicly available and can be found here: <https://github.com/kevin-flaherty/disk_model>" (footnote 2)
- Products in archive: _not stated_
- Code: Disk model code public at github.com/kevin-flaherty/disk_model  
  > "This code is publicly available and can be found here: <https://github.com/kevin-flaherty/disk_model>" (footnote 2)
- Missing: MCMC settings and priors
- Missing: Pipeline version
- Missing: Exact CO analysis masks
- Missing: HST ADI code
- Data volume (inferred): ~50-100 GB raw (20 ACA+12m execution blocks)
- Score (inferred): 3/5, Data and project code stated, main recipe clear, but MCMC details and priors missing.
- Rediscovery candidate: yes, Public ALMA data (2016.1.00515.S), numeric ring geometry results in a table; fit settings partly missing.

## Links

- Method: (cite: Pearce2014) (Perturber dynamical framework)
- Method: (cite: Matra2015; Matra2017a) (CO spectro-spatial filtering and excitation)
- Method: (cite: Ricci2012) (Grain size index from spectral index)
- Companion: (cite: Krist2012) (Original HST discovery of eccentric ring)
- Companion: (cite: Schneider2016) (HST RDI of 2015 data)
- Related: ALMA 2018.1.00455.S (second epoch, PI Faramaz)
- Related: HST GO-12291, GO-13455, GO-13786

## Checks

```json
{
 "quotes": 83,
 "quotes_ok": 83,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2018.1.00455.S"
 ],
 "numeric_results": 14,
 "numeric_problems": 0,
 "fill": {
  "facts": 89,
  "stated": 62,
  "rate": 0.697
 },
 "evidence_ok": true
}
```
