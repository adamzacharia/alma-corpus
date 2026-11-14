# Outflows, cores, and magnetic field orientations in W43-MM1 as seen by ALMA

`2020A&A...640A.111A` | Astronomy and Astrophysics 2020 | first author: Arce-Tord, C. | arXiv: 2005.12921 | DOI: 10.1051/0004-6361/202038024

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism
- Question: Is the core-scale magnetic field orientation correlated with the orientation of dense cores and protostellar outflows in W43-MM1?  
  > "We aim to reveal any correlation between the magnetic field orientation and the orientation of the cores and outflows in a sample of protostellar dense cores in the W43-MM1 high-mass star-forming region." (abstract)
- Target **W43-MM1**: coordinates Pointing 1: 18:47:47.00 -1:54:26.90 (five pointings in Table)  
  > "W43-MM1, which is at a distance of 5.5 kpc from the Sun (cite: zhangb+14)" (Introduction); "| 1 | 18:47:47.00 | -1:54:26.90 |" (Observations); z/distance 5.5 kpc  
  > "W43-MM1, which is at a distance of 5.5 kpc from the Sun (cite: zhangb+14)" (Introduction); "| 1 | 18:47:47.00 | -1:54:26.90 |" (Observations); distance from Zhang et al. 2014a (cite: zhangb+14)  
  > "W43-MM1, which is at a distance of 5.5 kpc from the Sun (cite: zhangb+14)" (Introduction); "| 1 | 18:47:47.00 | -1:54:26.90 |" (Observations)

## Data provenance

- ALMA projects: _none stated_
- bands: Band 6 (1.3 mm), full polarization  
  > "We used the Atacama Large Millimeter Array in Band 6 (1.3 mm) in full polarization mode" (abstract)
- frequencies and spectral setup: 4 SPWs at 224.984, 226.984, 239.015, 241.015 GHz; 64 channels of 31.25 MHz each  
  > "four spectral windows centered at 224.984, 226.984, 239.015, and 241.015 GHz" (Observations); "Each spectral window has 64 channels of 31.250 MHz each" (Observations)
- continuum bandwidth: 1.875 GHz per spectral window  
  > "corresponding to a total bandwidth of 1.875 GHz per spectral window" (Observations)
- arrays: array with 35 antennas  
  > "The ALMA observations were obtained between April and May 2016 using an array with 35 antennas." (Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.55" x 0.49" (~2700 au)  
  > "with an angular resolution of 0.55$^{''}$ $\times$ 0.49$^{''}$" (Observations)
- max recoverable scale: ~10.6"  
  > "The maximum recoverable scale is $\sim$10.6$^{''}$." (Observations)
- sensitivity: Stokes Q/U rms 0.04-0.12 (units per Table, not stated in text); I rms 0.47-3.42  
  > "| 1 | 18:47:47.00 | -1:54:26.90 | 3.42 | 0.12 | 0.11 | 0.12 |" (Observations)
- time on source: _not stated_
- observing dates: April-May 2016  
  > "The ALMA observations were obtained between April and May 2016" (Observations)
- pi or archival as stated: _not stated_
- Other facility **ALMA+ACA CO(2-1), SiO(5-4) (Nony et al. 2020)**: Outflow orientations  
  > "archival data that provide the orientation of the outflows driven by the cores (cite: nony20)" (Results and analysis)
- External data: Core catalog and major-axis PAs (GETSOURCES) of 131 cores  
  > "The PAs (major axis) come from the GETSOURCES catalog and complete Table 1 of (cite: mottenat18)." (Table notes) [from Motte et al. 2018 (cite: mottenat18)]
- External data: Outflow lobe orientations  
  > "archival data that provide the orientation of the outflows driven by the cores (cite: nony20)" (Results and analysis) [from Nony et al. 2020 (cite: nony20)]
- Simulation/model as data: Monte Carlo synthetic populations of 100,000 random 3D vector pairs projected on the sky, in five angle ranges  
  > "These simulations select 100,000 pairs of random 3D vectors with an angle difference within a given range." (Results and analysis)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 5.1.2  
  > "The calibration, the imaging, and the analysis were done using version 5.1.2. of the Common Astronomical Software Applications" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: four rounds of phase-only self-cal using Stokes I model, per pointing; mosaic not self-calibrated  
  > "The images were improved iteratively through four rounds of phase-only self-calibration using the Stokes *I* image as a model." (Observations); "The mosaic was produced with data that were not self-calibrated." (Observations)

### Imaging

- task: tclean, each pointing separately for I, Q, U  
  > "The Stokes *U* and *Q* maps were imaged individually for each of the five fields with the *tclean* task using the same parameters as above." (Observations)
- deconvolver: Hogbom  
  > "using a Hogbom deconvolver and a Briggs weighting scheme with a robust parameter of 0.5" (Observations)
- weighting robust: Briggs, robust = 0.5  
  > "a Briggs weighting scheme with a robust parameter of 0.5" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied after cleaning to each map  
  > "After the cleaning, a primary beam correction was applied to each map." (Observations)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Core positions, sizes and PAs from earlier catalog  
  > "We measured the position angle (PA) of the magnetic field at the location of the cores identified by (cite: mottenat18)." (Results and analysis) [from Motte et al. 2018 (cite: mottenat18)]
- Polarization debiasing method  
  > "we applied the debiasing method proposed by (cite: vaillan06)" (Observations) [from Vaillancourt 2006 (cite: vaillan06)]

### Not stated but needed to reproduce (our reading)

- ALMA project code and archive MOUS
- Pointing-by-pointing flux/polarization calibrators
- Image size, cell size, masks, clean thresholds
- Flux units for rms table
- Pipeline vs manual calibration
- Exact implementation of the core-averaging and KS test code
- Outflow table angles source details

## Analysis recipe

1. **Image Stokes I, Q, U**: Phase self-calibration then tclean per pointing  
  > "The final imaging was performed with the *tclean* task from CASA using a Hogbom deconvolver and a Briggs weighting scheme with a robust parameter of 0.5." (Observations)
   - software: CASA
   - parameter: robust 0.5, Hogbom  
  > "a robust parameter of 0.5" (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive debiased polarized intensity and B-field angles**: P=sqrt(Q^2+U^2), Vaillancourt debiasing, 3 sigma_P threshold, chi=0.5 arctan(U/Q), rotate 90 deg  
  > "We wielded the 3$\sigma_{\mathrm{P}}$ debiased intensity value as a threshold to select the pixels used to derive the polarization angle maps" (Observations)
   - software: CASA
   - assumption: Grain alignment by radiative alignment torques; polarization perpendicular to B  
  > "we assumed alignment of the grains with respect to the magnetic field due to the "radiative alignment torques" mechanism (RATs)" (Observations)
   - fitting: _not stated_
   - validation: _not stated_
3. **Mean B-field PA per core**: Average Q and U within each core area (2D Gaussian of Stokes I), only within one-third of primary beam; error propagation  
  > "where *Q* and *U* are the mean Stokes $Q$ and $U$ intensities averaged within each core, whose area is defined by a 2D Gaussian fit of its Stokes $I$ emission." (Results and analysis)
   - parameter: within one-third of primary beam; 52 cores, 29 with polarization  
  > "Of these 52 cores, 29 display polarized thermal dust emission." (Results and analysis)
   - fitting: _not stated_
   - validation: _not stated_
4. **Compare angle distributions with synthetic populations**: CDFs of angle differences vs Monte Carlo populations in 5 ranges; KS tests, reject at p<0.05  
  > "Following a conservative rule of thumb, we rejected the hypothesis that the two populations are drawn from the same distribution when $p$ $<$ 0.05." (Results and analysis)
   - parameter: 100,000 vector pairs; ranges 0-20, 20-50, 50-70, 70-90, 0-90 deg  
  > "We considered the following five ranges of 3D angle differences" (Results and analysis)
   - fitting: _not stated_
   - validation: Footnote: treating bipolar outflows as single points gives similar results  
  > "We also performed the analysis treating bipolar outflows as single data points and obtained similar results" (Footnote 2)

## Software

- **CASA** 5.1.2: calibration, imaging, analysis  
  > "The calibration, the imaging, and the analysis were done using version 5.1.2. of the Common Astronomical Software Applications" (Observations)
- **GETSOURCES** : core catalog (from Motte et al. 2018)  
  > "The PAs (major axis) come from the GETSOURCES catalog" (Table notes)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| KS p-value B-field vs core PA, 20-50 deg | 0.76 | not stated | dimensionless | 4 | / 20-50$^\circ$ / 0.76 / |
| KS p-value B-field vs outflows, 50-70 deg | 0.51 | not stated | dimensionless | 4 | / B-field vs. Outflows / 50-70$^\circ$ / 0.51 / 28 / |
| KS p-value B-field vs outflows, random | 0.16 | not stated | dimensionless | 4 | /  / Random / 0.16 /  / |
| Cores with polarization | 29 of 52 | not stated | cores | 3 | Of these 52 cores, 29 display polarized thermal dust emission. |

## Qualitative findings

- Core orientation is not random with respect to B; compatible with 20-50 deg  
  > "the dense cores are compatible with being oriented 20-50$^\circ$ with respect to the magnetic field." (abstract)

## Claim tuples

- H: Cores are randomly oriented relative to B | E: KS tests of core PA minus B-field PA vs synthetic populations | R: Only the 20-50 deg population is not rejected (p=0.76) | F: Cores are nonrandomly oriented, 20-50 deg to B, contradicting magnetically controlled collapse models | **supported**
- H: Outflows are aligned with B | E: KS tests on outflow minus B-field angles | R: Parallel and perpendicular rejected; random or 50-70 deg allowed | F: Outflows are either random or 50-70 deg to B; cannot discriminate | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: KS test chosen over chi-squared because preferable for nonequally sampled data  
  > "We chose the KS test over the chi-squared test as the former is preferable to compare nonequally sampled data." (Results and analysis)
- How they decided it was enough: _not stated_
- Limitation (authors): Sample size does not allow discriminating 50-70 deg, random, or bimodal populations  
  > "it is not statistically possible to discriminate between the 50-70$^\circ$ orientation, a random orientation, or an 85% random population plus a 15% orthogonal population." (Discussion)
- Caveat (inferred, ours): Small samples; KS p-values depend on projection assumptions
- Caveat (inferred, ours): Core elongation as disk proxy is assumed
- Caveat (inferred, ours): Core PA errors treat only measurement error
- Caveat (inferred, ours): Spatial correlation of cores not accounted for

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA project code not printed in paper
- Missing: Tabulated Q/U flux values per pixel
- Missing: Pointing calibration details
- Data volume (inferred): ~100-300 GB raw for five pointings full-pol Band 6
- Score (inferred): 3/5, Imaging parameters partly given and catalogs are external, but project code, calibration and masking details are missing.
- Rediscovery candidate: no, The paper does not state public data or project code, and key inputs (core catalog, outflow table) come from other papers.

## Links

- Method: Vaillancourt 2006 (cite: vaillan06) (polarization debiasing)
- Method: Motte et al. 2018 (cite: mottenat18) (core catalog)
- Companion: Nony et al. 2020 (cite: nony20) (outflow orientations)
- Companion: Cortes et al. 2016 (cite: cortes+16) (earlier ALMA polarization of W43-MM1)
- Related: ALMA-IMF-related W43-MM1 studies

## Checks

```json
{
 "quotes": 50,
 "quotes_ok": 50,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2015.1.01020.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 38,
  "rate": 0.551
 },
 "evidence_ok": true
}
```
