# Resolved gas temperatures and <SUP>12</SUP>C/<SUP>13</SUP>C ratios in SVS13A from ALMA Observations of CH<SUB>3</SUB>CN and CH<SUB>3</SUB><SUP>13</SUP>CN

`2025A&A...696A...1H` | Astronomy and Astrophysics 2025 | first author: Hsieh, T.-H. | arXiv: 2502.02873 | DOI: 10.1051/0004-6361/202453273

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: What are the kinematic structures, gas temperatures, physical conditions and 12C/13C ratios in the protobinary SVS13A (VLA4A and VLA4B), probed by resolved CH3CN and CH3 13CN J=12-11 K-ladder emission?  
  > "We aim to provide a snapshot of the forming protobinary system SVS13A, consisting of VLA4A and VLA4B. This includes clear pictures of its kinematic structures, physical conditions, and chemical properties." (abstract)
- Target **SVS13A (VLA4A, VLA4B)**: coordinates ICRS 03h29m03.74s, +31d16m03.8s (phase center)  
  > "SVS13A is a well studied protobinary system located in the NGC1333 cluster in the Perseus Molecular Cloud ($d=$293 pc, (cite: or18))." (Introduction); "ICRS $\alpha$ = 3$^{\rm h}$29$^{\rm m}$ 03$^{\rm s}$.74, $\delta$ = 31$^{\rm d}$16$^{\rm m}$03$^{\rm s}$.8" (Observations); z/distance d = 293 pc  
  > "SVS13A is a well studied protobinary system located in the NGC1333 cluster in the Perseus Molecular Cloud ($d=$293 pc, (cite: or18))." (Introduction); "ICRS $\alpha$ = 3$^{\rm h}$29$^{\rm m}$ 03$^{\rm s}$.74, $\delta$ = 31$^{\rm d}$16$^{\rm m}$03$^{\rm s}$.8" (Observations); distance from Ortiz-León et al. 2018 (cite: or18)  
  > "SVS13A is a well studied protobinary system located in the NGC1333 cluster in the Perseus Molecular Cloud ($d=$293 pc, (cite: or18))." (Introduction); "ICRS $\alpha$ = 3$^{\rm h}$29$^{\rm m}$ 03$^{\rm s}$.74, $\delta$ = 31$^{\rm d}$16$^{\rm m}$03$^{\rm s}$.8" (Observations)

## Data provenance

- ALMA projects: 2022.1.00479.S
- bands: Band 6  
  > "488 kHz (0.6 km s$^{-1}$) channel width (band 6, (cite: ed04))" (Observations)
- frequencies and spectral setup: CH3CN J=12-11 window 220.52-220.75 GHz, 61 kHz (0.08 km/s) channels; continuum window at 234.5 GHz, 1.875 GHz bandwidth  
  > "which covers a wavelength ranging from 220.52 GHz to 220.75 GHz with a channel width of 61 kHz (0.08 km s$^{-1}$)" (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C-7  
  > "With the ALMA C-7 configuration, the baselines were $91-8282$ m" (Observations)
- baselines: 91-8282 m (~65-6000 kλ) at 220 GHz  
  > "the baselines were $91-8282$ m ($\sim$$65-6000$ k$\lambda$) at 220 GHz" (Observations)
- angular resolution: 0.11'' x 0.08'' (~30 au)  
  > "resulting in a beam size of $0.11\ensuremath{''}\times0.08\ensuremath{''}$ ($\sim$30 au) for the cube" (Observations)
- max recoverable scale: 0.1 to 1.2 arcsec (~30-360 au)  
  > "recovering scales from 0.1 to 1.2 arcsec ($\sim$30$-$360 au)" (Observations)
- sensitivity: 1.7 mJy/beam (4.7 K) per 0.08 km/s channel  
  > "This image cube has an rms noise level of 1.7 mJy beam$^{-1}$ (4.7 K) at the spectral resolution of 0.08 km s$^{-1}$." (Observations)
- time on source: 144 min  
  > "The total on-source (SVS13A) time was 144 min" (Observations)
- observing dates: June 2023, three executions  
  > "We conducted ALMA observations in June 2023 with three executions" (Observations)
- pi or archival as stated: _not stated_
- Line: CH3CN J=12-11 K=0-7 (not stated)
- Line: CH3 13CN J=12-11 K=0-5 (not stated)
- Other facility **NOEMA (PRODIGE)**: Broad-band line identification via LTE modeling in earlier papers  
  > "Using the broad wavelength coverage provided by the large program PROtostars & DIsks: Global Evolution (PRODIGE) using NOEMA, (cite: hs23; hs24) thoroughly identify the molecular lines" (Results)
- External data: Protostellar masses, inclination and disk parameters for VLA4A/VLA4B  
  > "given the star masses and inclination angle from (cite: di22)" (Toomre Q analysis) [from (cite: di22)]
- External data: Dust opacity 0.899 cm2/g at 1.3 mm  
  > "assuming the dust opacity $\kappa=0.899$ cm$^{2}$ g$^{-1}$ at 1.3 mm (cite: os94; to18)" (Toomre Q analysis) [from (cite: os94; to18)]
- External data: Spectroscopic line data from CDMS and JPL  
  > "The line data are taken from CDMS (cite: mu05; en16) and JPL (cite: pi98)" (LTE model setup) [from (cite: mu05; en16; pi98)]
- External data: Canonical ISM 12C/13C ratio of 68  
  > "the canonical ratio in the local ISM /$\simeq$68 (cite: mi05)" (12C/13C spatial distribution) [from (cite: mi05)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline calibrated data  
  > "We use the pipeline calibrated data restored using CASA 6.4.12 (cite: casa)." (Observations)
- casa version: CASA 6.4.12  
  > "We use the pipeline calibrated data restored using CASA 6.4.12 (cite: casa)." (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0423-0120 (also bandpass)  
  > "The three executions shared the same bandpass and flux calibrator as J0423-0120" (Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "Imaging was done using the `tclean` package with a robust weighting of 0.5" (Observations)
- deconvolver: _not stated_
- weighting robust: robust = 0.5  
  > "Imaging was done using the `tclean` package with a robust weighting of 0.5" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: STATCONT, image-domain pixel by pixel, default sigma-clipping  
  > "STATCONT performs continuum subtraction in image domain pixel by pixel" (STATCONT for continuum subtraction); "We used the default sigma-clipping algorithm" (STATCONT for continuum subtraction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.11'' x 0.08''  
  > "resulting in a beam size of $0.11\ensuremath{''}\times0.08\ensuremath{''}$ ($\sim$30 au) for the cube" (Observations)
- final rms: 1.7 mJy/beam (4.7 K) at 0.08 km/s  
  > "This image cube has an rms noise level of 1.7 mJy beam$^{-1}$ (4.7 K)" (Observations)

### Inherited from earlier work

- LTE model constructed following CASSIS and XCLASS manuals  
  > "The LTE model is constructed based on CASSIS and XCLASS manuals (cite: va15; mo17)." (LTE model setup) [from (cite: va15; mo17)]
- Two-layer model is a variation of the infall two-layer model  
  > "This equation can be considered as a variation from the two-layer model in (cite: my96)" (Two-layer model) [from (cite: my96)]
- CH3CN partition function error estimate from earlier work  
  > "This causes at most $0.06\%$ error at $T<500$ K ((cite: hs23))." (Boltzmann distribution and optical depth) [from (cite: hs23)]

### Not stated but needed to reproduce (our reading)

- MCMC sampler/package, priors ranges, walkers, steps and likelihood noise treatment
- Exact tclean parameters (cell, image size, niter, threshold, mask, spectral gridding)
- Line-free channels chosen by STATCONT and STATCONT settings
- Rest frequencies/catalog entries used per transition and which lines were masked per pixel
- Clustering inputs scaling for DBSCAN in PPV space
- Details of initial-guess interpolation and per-pixel fitting code (not released)
- Thin-disk model parameters used for Toomre Q

## Analysis recipe

1. **Image cube and subtract continuum**: tclean imaging of pipeline-calibrated data; STATCONT continuum subtraction  
  > "we obtained the continuum image from the continuum window and the line image cube from the window." (STATCONT for continuum subtraction)
   - software: CASA, STATCONT
   - parameter: robust = 0.5  
  > "Imaging was done using the `tclean` package with a robust weighting of 0.5" (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **One-layer LTE fit per pixel with dust absorption**: Pixel-by-pixel LTE fit with Tex, N, tau_dust, Vlsr, FWHM and 12C/13C ratio free; mask S/N>12 on K=3 moment map; fit boundary 800 K  
  > "A spatial mask is taken using a threshold of S/N\>12 from the K=3 integrated intensity map" (LTE model setup); "the boundary of the fitting is set to 800 K" (One-layer model)
   - assumption: Dust and gas co-located with same temperature Tex; Tbg = 2.7 K  
  > "and that the dust and gas temperature are the same, $T_{\rm ex}$." (One-layer model)
   - fitting: _not stated_
   - validation: A model without dust absorption failed to fit the line ratios  
  > "We note that an LTE model without considering dust absorption was also tried but failed to interpret the line spectrum" (One-layer model)
3. **Two-layer LTE fit with MCMC initial guesses**: 12-parameter two-layer model; MCMC on 41 grid positions, tuned priors, interpolated to initial-guess maps for per-pixel fitting  
  > "We first perform Markov Chain Monte Carlo (MCMC) sampling of a grid of positions in the emitting regions (in total 41 positions with gaps around emission of roughly beam size)." (Two-layer model)
   - fitting: MCMC; priors tuned so neighboring positions do not differ dramatically; isotopologue ratio upper prior bound 80  
  > "the sample reaches its upper boundary of 80 in the prior" (Degeneracy and model selection)
   - validation: Compared reduced chi2, AIC and Bayesian evidence (Dynesty) for one vs two layers  
  > "we have also calculated Bayesian evidence with nested sampling algorithm (cite: sk04) using Dynesty (cite: sp20; ko22) toward the 41 grid positions" (Degeneracy and model selection)
4. **Select model per pixel and cluster kinematic components**: Two-layer used where |V1-V2| exceeds both velocity dispersions; DBSCAN in PPV space  
  > "We use the clustering algorithm DBSCAN (cite: es96; va23; gi24) with `eps=0.3` and `min_samples=10`, clustering these points into six groups." (Clustering into kinematic components)
   - software: DBSCAN
   - parameter: eps=0.3, min_samples=10  
  > "with `eps=0.3` and `min_samples=10`" (Clustering into kinematic components)
   - fitting: _not stated_
   - validation: _not stated_
5. **Toomre Q maps**: Sigma from tau_dust map, sound speed from Tex, Omega from Keplerian thin-disk models  
  > "By assuming Keplerian rotation, we obtain $Q$ maps for VLA4A and VLA4B (Figure [9](#fig:Q))." (Toomre Q analysis)
   - assumption: kappa = 0.899 cm2/g at 1.3 mm, gas-to-dust 100, inclination from Diaz-Rodriguez et al. 2022  
  > "a gas to dust mass ratio of 100, with inclination correction from (cite: di22)" (Toomre Q analysis)
   - assumption: Quiescent T ∝ L^0.2 with luminosity 100 times lower  
  > "If we assume $T\propto L^{0.2}$ (cite: go74) and the luminosity was 100 times less during the quiescent phase" (Toomre Q analysis)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 6.4.12: Pipeline-restored data and tclean imaging  
  > "We use the pipeline calibrated data restored using CASA 6.4.12 (cite: casa)." (Observations)
- **STATCONT** : Continuum level, line-free channels and continuum subtraction  
  > "We use STATCONT (cite: sa18) to determine the continuum level and find the line-free channels." (STATCONT for continuum subtraction)
- **DBSCAN** : Clustering PPV points into kinematic components  
  > "We use the clustering algorithm DBSCAN (cite: es96; va23; gi24)" (Clustering into kinematic components)
- **Dynesty** : Bayesian evidence for model selection  
  > "using Dynesty (cite: sp20; ko22) toward the 41 grid positions" (Degeneracy and model selection)
- **CDMS/JPL catalogs** : Line data for LTE models  
  > "The line data are taken from CDMS (cite: mu05; en16) and JPL (cite: pi98)" (LTE model setup)
- **Astropy, NumPy, SciPy, Matplotlib, APLpy** : Listed software for analysis and plotting  
  > "*Software:* Numpy ((cite: numpy)), Scipy ((cite: scipy)), APLpy ((cite: aplpy)), Matplotlib ((cite: matplotlib)), Astropy ((cite: astropy)) CASA ((cite: casa))" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Rms noise of cube | 1.7 | not stated | mJy/beam | 1 | This image cube has an rms noise level of 1.7 mJy beam$^{-1}$ (4.7 K) |
| Component I Tex | 205.5 | +79.1/-43.1 | K | 3 | / I / 27660 / 205.5$^{+79.1}_{-43.1}$ / |
| Component II Tex | 178.9 | +73.7/-47.0 | K | 3 | / II / 7282 / 178.9$^{+73.7}_{-47.0}$ / |
| Component II Vin | -2.1 | +0.3/-0.3 | km/s | 4 | -2.1$^{+0.3}_{-0.3}$ |
| Component I 12C/13C | 19.5 | +8.6/-5.6 | dimensionless | 3 | 19.5$^{+8.6}_{-5.6}$ |
| Component II 12C/13C | 38.6 | +34.0/-11.9 | dimensionless | 3 | 38.6$^{+34.0}_{-11.9}$ |
| Peak continuum brightness temperature VLA4A / VLA4B | 70 / 90 | not stated | K | 1 | VLA4A peak brightness is lower (70 K) than the primary VLA4B (90K). |
| Toomre Q reduction factor in quiescent phase | ~0.6 | not stated | dimensionless | 5 | the $c_s$ as well as the $Q$ parameter should be a factor of $\sim$0.6 of the current values |

## Qualitative findings

- CH3CN peaks toward VLA4A while CH3 13CN peaks between the protostars; ring-like emission around VLA4B attributed to dust absorption  
  > "the is the brightest towards the secondary protostar VLA4A while its isotopologue is the brightest in between the two protostars." (Summary)

## Claim tuples

- H: Is there an infalling signature toward VLA4A and does the gas thermal structure require more than protostellar heating? | E: Two-layer LTE fits per pixel and clustering into components | R: Component II shows blue excess/negative Vin around VLA4A; high temperatures along spiral | F: Possible infall toward VLA4A and shock/mechanical heating | **partially**
- H: Is the 12C/13C ratio below ISM and spatially variable? | E: LTE fit with free isotopologue ratio | R: Ratios ~20-40 in most components, lower toward VLA4B | F: Ratio lower than 68 and differs between VLA4A and VLA4B | **supported**
- H: Was the disk gravitationally unstable before the outburst? | E: Toomre Q maps with cooler quiescent temperature | R: Q>1 currently; lower Q in quiescence | F: Disk may have fragmented before outburst | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Dust absorption needed; LTE model without it gave inconsistent line ratios; two-layer model needed for double-peaked profiles  
  > "the double peak spectral profiles are still present in particular regions, indicating two components along the line of sight." (Two-layer model)
- Alternative: LTE model without dust absorption tried but failed  
  > "an LTE model without considering dust absorption was also tried but failed to interpret the line spectrum" (One-layer model)
- How they decided it was enough: _not stated_
- Limitation (authors): Infall vs expansion is degenerate in two-layer fits; tau_dust,1 and tau_dust,2 degenerate  
  > "However, there is a caveat to determine this given the degeneracy of the model." (Clustering into kinematic components)
- Caveat (inferred, ours): Infall interpretation depends on initial-guess convention (blue excess = infall)
- Caveat (inferred, ours): Single-band data cannot constrain dust opacity; Toomre Q uncertain by dust kappa
- Caveat (inferred, ours): LTE assumption and gas-dust same temperature
- Caveat (inferred, ours): Model selection thresholds are ad hoc

## Reproducibility

- Data public (paper): Project ID given; ALMA archive linked  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2022.1.00479.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Fitting code and MCMC configuration
- Missing: Full tclean parameters
- Missing: STATCONT line-free channel selection
- Missing: Manual velocity masks per pixel
- Data volume (inferred): ~50-200 GB raw for three executions of Band 6 C-7 data
- Score (inferred): 3/5, Public data and good model equations, but fitting code, sampler settings and imaging details are missing.
- Rediscovery candidate: no, Recipe lacks sampler/priors and manual masks, so numbers cannot be exactly recovered.

## Links

- Method: (cite: sa18) (STATCONT continuum subtraction)
- Method: (cite: my96) (Two-layer infall model)
- Method: (cite: mo17) (XCLASS LTE modeling)
- Companion: (cite: hs23) (NOEMA PRODIGE line modeling of SVS13A, streamer candidate)
- Companion: (cite: hs24) (O-bearing COM multi-component LTE fitting toward SVS13A)
- Companion: (cite: di22) (Prior ALMA study with binary masses and disk parameters)
- Related: PRODIGE

## Checks

```json
{
 "quotes": 73,
 "quotes_ok": 70,
 "quote_pass_rate": 0.959,
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
  "facts": 80,
  "stated": 53,
  "rate": 0.662
 },
 "evidence_ok": false
}
```
