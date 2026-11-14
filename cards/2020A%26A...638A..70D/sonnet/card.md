# The Massive and Distant Clusters of WISE Survey. SZ effect of Verification with the Atacama Compact Array - Localization and Cluster Analysis

`2020A&A...638A..70D` | Astronomy and Astrophysics 2020 | first author: Di Mascolo, Luca | arXiv: 2004.06728 | DOI: 10.1051/0004-6361/202037818

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: galaxy_clusters_and_sz
- Question: Can ACA Band 3 observations robustly validate MaDCoWS cluster candidates through the thermal SZ effect, and what cluster masses do they give?  
  > "to provide robust validation of cluster detections via the thermal Sunyaev–Zeldovich (SZ) effect" (abstract)
- Target **ten MaDCoWS clusters (VACA LoCA pilot sample; individual IDs not preserved in the text), e.g. MOO J0129-1641, MOO J0917-0700, MOO J2146-0320**: coordinates _not stated_; z/distance photometric z about 1.01-1.31  
  > "1 arcsecond corresponds to $8.01~\mathrm{kpc}$ at the average redshift $z\simeq1$ of the VACA LoCA clusters" (1 Introduction); distance from Spitzer photometric constraints (Gonzalez2019)  
  > "1 arcsecond corresponds to $8.01~\mathrm{kpc}$ at the average redshift $z\simeq1$ of the VACA LoCA clusters" (1 Introduction)

## Data provenance

- ALMA projects: 2016.2.00014.S
- bands: Band 3, four continuum spectral windows covering 89.5-105.5 GHz (center about 97.5 GHz)  
  > "using four Band 3 spectral windows in continuum mode with centers at approximately $90.5$, $92.5$, $102.5$, and $104.5~\mathrm{GHz}$" (2 ACA observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: ACA (Morita Array), 7-m  
  > "the 7-meter Atacama Compact Array (cite: Iguchi2009), or Morita Array" (1 Introduction)
- configurations: _not stated_
- baselines: uv range average 2.64-17.23 kλ  
  > "span, on average, between $2.64$ and $17.23~\mathrm{k\lambda}$" (2 ACA observations)
- angular resolution: _not stated_
- max recoverable scale: MRS 1.36-2.23 arcmin across fields (Table 1)  
  > "2017-09-07 | $2.14$ | $0.081$ | $2.52-17.22$ | $19.9\times  9.6$ | $1.36$" (Table 1)
- sensitivity: _not stated_
- time on source: average 2.6 hours per pointing, target sensitivity about 80 uJy  
  > "the integration time on source for each of the pointings amounts to an average of $2.6~\mathrm{hours}$" (2 ACA observations)
- observing dates: May-October 2017, Cycle 4  
  > "carried out between May and October 2017 as part of ALMA Cycle 4 operations" (2 ACA observations)
- pi or archival as stated: PI M. Brodwin  
  > "project ID: 2016.2.00014.S, PI: M. Brodwin" (2 ACA observations)
- Other facility **Spitzer/IRAC**: cluster richness, photometric redshifts, galaxy overdensity maps  
  > "infrared richness estimates from observations with the Infrared Array Camera" (2 ACA observations)
- Other facility **CARMA**: SZ masses for the MaDCoWS mass-richness relation  
  > "masses derived from the SZ signal measured by the Combined Array for Research in Millimeter-wave Astronomy" (2 ACA observations)
- Other facility **VLASS, FIRST, NVSS**: checks for radio contamination  
  > "we first checked the NRAO VLA Sky Survey (cite: Condon1998) for possible radio components." (4.3 Unresolved sources)
- External data: gNFW pressure profile parameters (universal, cool core, disturbed)  
  > "we set the above gNFW parameters alternatively to the best-fit values reported in (cite: Arnaud2010)" (3.1 Estimating cluster masses) [from (cite: Arnaud2010)]
- External data: Planck and high-z Chandra gNFW parameters  
  > "we additionally consider gNFW parameters derived in (cite: Planck2013V)" (3.1 Estimating cluster masses) [from (cite: Planck2013V); (cite: McDonald2014)]
- External data: MaDCoWS richness, photometric redshifts, mass-richness relation, centroid offsets  
  > "deviate by $\sigma_{\mathrm{RA}}=14.3~\mathrm{arcsec}$ in right ascension" (3.3 Parameter priors) [from (cite: Gonzalez2019)]

## Processing

### Calibration

- pipeline or manual: standard calibration pipelines provided at data delivery  
  > "using the standard calibration pipelines provided at data delivery" (2 ACA observations)
- casa version: CASA 4.7.2 (calibration); 5.6.1 (imaging)  
  > "package version 4.7.2" (2 ACA observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 5%  
  > "We hence adopt the nominal value of $5\%$ for the fiducial uncertainty on the ACA absolute calibration" (2 ACA observations)
- self calibration: _not stated_

### Imaging

- task: tclean in CASA 5.6.1, display only  
  > "generated using the `tclean` task in `CASA` version 5.6.1" (2 ACA observations)
- deconvolver: none; dirty maps  
  > "No deconvolution is performed to reduce the effects of sidelobes on the reconstructed “dirty” maps." (2 ACA observations)
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: not corrected; cut at 0.2 gain level  
  > "The fields are cut off at the standard 0.2 gain level of the ACA antenna pattern." (2 ACA observations)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Bayesian forward-modeling in visibility space, flux normalization hyperparameter, data-free tests  
  > "An extensive discussion of the modeling methodology and the implementation is provided in (cite: DiMascolo2019a; DiMascolo2019b)." (3 Analysis technique) [from (cite: DiMascolo2019a; DiMascolo2019b)]
- P500 definition and 5 r500 line-of-sight integration limit  
  > "Following (cite: Arnaud2010), the scaling parameter $P_{500}$ is defined as" (3.1 Estimating cluster masses) [from (cite: Arnaud2010)]

### Not stated but needed to reproduce (our reading)

- Sampler name and settings (the evidence is computed, but the nested-sampling code is not named)
- Cluster IDs are missing from the converted tables, so rows cannot be matched to clusters
- Spectral-window averaging and uv-data weighting or flagging applied before fitting
- Redshift split-normal prior widths per cluster beyond the table values
- Exact mass-richness fit procedure and likelihood
- Code used for the visibility modeling is not named or released

## Analysis recipe

1. **calibrate ACA visibilities**: standard pipeline calibration; check for issues  
  > "A direct inspection of the reduced data sets did not highlight any significant issue with the calibration." (2 ACA observations)
   - software: CASA
   - parameter: 5% flux uncertainty  
  > "nominal value of $5\%$ for the fiducial uncertainty on the ACA absolute calibration" (2 ACA observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **fit SZ + point-source model to visibilities**: Bayesian forward modeling of raw visibilities with gNFW pressure model (fixed shape parameters) plus Dirac-delta point sources with flat spectrum  
  > "we perform a Bayesian forward-modeling analysis directly on the visibilities of the ACA MaDCoWS sample" (3 Analysis technique)
   - parameter: free: M500, z, centroid, point source positions and fluxes, flux normalization  
  > "The position $\bm{x}_{\textsc{ps}}$ and the source flux $i_{\textsc{ps}}$ are left free to vary." (3.3 Parameter priors)
   - assumption: non-relativistic tSZ, kSZ neglected, flat ΛCDM Ωm=0.30 H0=70  
  > "we neglect any temperature-dependent corrections arising from the fully relativistic treatment of the thermal SZ effect" (3.1 Estimating cluster masses)
   - fitting: Normal priors on centroid (sigma 14.3, 15 arcsec); split-normal priors on z; normal prior on flux scaling; wide uninformative priors on point source flux  
  > "we adopt split-normal priors (cite: Wallis2014) on the redshifts $z$" (3.3 Parameter priors)
   - validation: data-free runs show no prior-induced biases  
  > "have shown no biases in the parameter inference related to choice in the prior distributions" (3.3 Parameter priors)
3. **assess detection significance**: Bayes factor between SZ+point-source and point-source-only models, converted to sigma_eff  
  > "$\sigma_{\mathrm{eff}}\simeq\sqrt{2\Delta\log{\mathcal{Z}}}$" (4 Results and discussion)
   - parameter: sigma_eff >~ 3 indicates robust detection  
  > "a value of $\sigma_{\mathrm{eff}}\gtrsim3$ is indicative of a robust detection" (4 Results and discussion)
   - fitting: _not stated_
   - validation: Compared with dirty-image significance for most significant cluster  
  > "corresponding to a statistical significance of $4.06\sigma$" (4 Results and discussion)
4. **compare to mass-richness relation and test pressure models**: Fit normalization with slope fixed to Gonzalez2019; refit with M500 fixed to relation and free P0; repeat with five gNFW models  
  > "with the slope constrained to that of the mass–richness scaling in (cite: Gonzalez2019) but with a free normalization parameter" (4.1 Mass–richness relation)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.2 (calibration), 5.6.1 (imaging): calibration and tclean dirty images  
  > "All the interferometric images presented in this work are generated using the `tclean` task in `CASA` version 5.6.1." (2 ACA observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| clusters with significant SZ detection | 7 of 10 | not stated | clusters | 3 | we obtain a significant detection of the SZ effect for seven out of the ten VACA LoCA clusters |
| highest sigma_eff (universal profile) | 7.77 | not stated | dimensionless | 3 | $\sigma_{\mathrm{eff}}=7.77$ |
| M500 of most significant cluster (universal) | 2.57 | +0.30/-0.30 | 1e14 Msun | 2 | $2.57\substack{+0.30\\-0.30}$ |
| mass scaling factor vs CARMA mass-richness, all clusters | 0.56 | +0.13/-0.05 | dimensionless | 4 | downscaled by a factor of $0.56\substack{+0.13\\-0.05}$ |
| scaling factor excluding non-detections | 0.61 | +0.15/-0.06 | dimensionless | 4 | ($0.61\substack{+0.15\\-0.06}$) |
| point source flux in radio-lobe cluster field | 0.20 | +0.06/-0.04 | mJy | 2 | $i_{\textsc{ps}}=0.20\substack{+0.06\\-0.04}~\mathrm{mJy}$ |

## Qualitative findings

- Detection significance is independent of the assumed pressure profile, while masses depend strongly on it.  
  > "the detection significance is not affected by the specific choice of pressure distribution model" (5 Conclusions)

## Claim tuples

- H: Can ACA confirm the ICM in MaDCoWS clusters? | E: uv-space Bayesian fit of ten ACA fields | R: 7 of 10 significant (sigma_eff>=3) | F: ACA robustly validates clusters in under ~3 h per target | **supported**
- H: Do ACA masses agree with the CARMA-calibrated mass-richness relation? | E: Fit normalization with fixed slope | R: masses downscaled by 0.56 | F: Systematically low, likely from filtering, profile choice, and radio contamination | **partially**
- H: Does interferometric filtering bias masses low? | E: Fix M500 to the relation and fit P0 | R: no evident common systematic | F: Filtering is unlikely to be the main bias | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Visibility-space forward modeling avoids missing-flux and correlated-noise issues of image analysis  
  > "accounting for the exact sampling function of the visibility plane" (3 Analysis technique)
- Alternative: Free gNFW slopes rejected: unconstrained and degenerate  
  > "all three parameters $a$, $b$, and $c$ would remain entirely unconstrained" (3.1 Estimating cluster masses)
- How they decided it was enough: _not stated_
- Limitation (authors): Limited angular dynamic range, short integrations and unresolved-source contamination limit mass inference  
  > "the limited angular dynamic range of the ACA in Band 3 alone, short observational integration times, and possible contamination from unresolved sources" (abstract)
- Caveat (inferred, ours): sigma_eff is heuristic and ignores prior volumes
- Caveat (inferred, ours): Masses are extrapolated from the cluster core using fixed pressure profiles
- Caveat (inferred, ours): Only 10 clusters, so the mass-richness offset is poorly constrained

## Reproducibility

- Data public (paper): ALMA data cited by project ID; acknowledgement uses ADS/JAO.ALMA#2016.2.00014.S  
  > "ADS/JAO.ALMA#2016.2.00014.S" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Modeling code and sampler settings
- Missing: Per-cluster IDs in tables
- Missing: Details of visibility preprocessing
- Data volume (inferred): about 10 ACA fields, tens of GB raw
- Score (inferred): 3/5, Data are archival and the method is described, but the inference code and sampler details are in earlier papers.
- Rediscovery candidate: no, Requires a custom visibility-space Bayesian code that is not specified or released.

## Links

- Method: (cite: DiMascolo2019a) (Visibility-space modeling method)
- Method: (cite: DiMascolo2019b) (Implementation of the modeling)
- Companion: (cite: Gonzalez2019) (MaDCoWS catalog and mass-richness relation)
- Companion: (cite: Decker2019) (CARMA SZ follow-up)
- Related: MaDCoWS
- Related: VACA LoCA
- Related: CARMA SZ follow-up

## Checks

```json
{
 "quotes": 52,
 "quotes_ok": 52,
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
  "stated": 41,
  "rate": 0.577
 },
 "evidence_ok": true
}
```
