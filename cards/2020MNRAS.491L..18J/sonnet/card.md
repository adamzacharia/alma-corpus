# The ALPINE-ALMA [C II] survey: a triple merger at z ∼ 4.56

`2020MNRAS.491L..18J` | Monthly Notices of the Royal Astronomical Society 2020 | first author: Jones, G. C. | arXiv: 1908.07777 | DOI: 10.1093/mnrasl/slz154

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Is DC 818760 at z~4.56 a multiple-component merger system, and what are the [CII] kinematics, SFRs and merger state of its three sources?  
  > "we discuss new ALMA observations of \[C II\] and submm continuum emission from DC 818760 obtained as part of the ALMA large program ALPINE, and examine its triple merger nature." (Introduction)
- Target **DEIMOS_COSMOS_818760 (DC 818760)**: coordinates Source C: 10h01m54.865s, +2d32m31.53s  
  > "the $z_{\rm [CII]}=4.56$ dusty triple merger DEIMOS_COSMOS_818760 (hereafter DC 818760)" (Introduction); "| Right Ascension | 10h01m54.865s | 10h01m54.978s | 10h01m54.683s |" (Table 1); z/distance z_[CII]=4.56038 (source C)  
  > "the $z_{\rm [CII]}=4.56$ dusty triple merger DEIMOS_COSMOS_818760 (hereafter DC 818760)" (Introduction); "| Right Ascension | 10h01m54.865s | 10h01m54.978s | 10h01m54.683s |" (Table 1); distance from [CII] line centroid from this work  
  > "the $z_{\rm [CII]}=4.56$ dusty triple merger DEIMOS_COSMOS_818760 (hereafter DC 818760)" (Introduction); "| Right Ascension | 10h01m54.865s | 10h01m54.978s | 10h01m54.683s |" (Table 1)

## Data provenance

- ALMA projects: 2017.1.00428.L
- bands: _not stated_
- frequencies and spectral setup: Two sidebands, each two 1.875 GHz SPWs with 15.625 MHz channels; lower sideband on [CII], upper continuum only  
  > "The spectral setup consisted of two sidebands, each constructed of two spectral windows (SPWs) of width 1.875 GHz." (2 Observations & Data Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-2, 45 antennas  
  > "using configuration C43-2 (baselines $\sim15-320$ m), 45 antennas" (2 Observations & Data Reduction)
- baselines: ~15-320 m  
  > "configuration C43-2 (baselines $\sim15-320$ m)" (2 Observations & Data Reduction)
- angular resolution: 1.07'' x 0.84'' at -81 deg  
  > "a synthesized beam of $1.07''\times0.84''\,$at$\,-81^{\circ}$" (2 Observations & Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: 0.6 mJy/beam per 15.625 MHz channel (cube); 0.05 mJy/beam continuum  
  > "channel of 0.6 mJy beam$^{-1}$" (2 Observations & Data Reduction); "a continuum image with an RMS noise level of 0.05 mJy beam$^{-1}$" (2 Observations & Data Reduction)
- time on source: 17 minutes  
  > "an on-source time of 17 minutes" (2 Observations & Data Reduction)
- observing dates: 25 May 2018 (cycle 5)  
  > "observed with ALMA on 25 May, 2018 in cycle 5" (2 Observations & Data Reduction)
- pi or archival as stated: Large Program, PI O. Le Fèvre  
  > "project 2017.1.00428.L, PI O. Le Fèvre" (2 Observations & Data Reduction)
- Line: [CII] 158 micron (not stated)
- Other facility **HST/ACS, UltraVISTA, Subaru, Spitzer**: Ancillary optical/NIR imaging (i-band, Ks-band) and SED photometry  
  > "The HST/ACS F814W (i-band) image of this source reveals emission from only source C." (Imaging Results)
- External data: Stellar mass log(M*)=10.6±0.1 and SFR_SED from LePHARE SED fit  
  > "Faisst et al. (in prep) find a stellar mass of log(M$_{*}\,[M_{\odot}])=10.6\pm0.1$" (Introduction) [from Faisst et al. (in prep)]
- External data: Empirical L[CII]-SFR calibration for star-forming galaxies  
  > "The empirical L$_{\rm [CII]}$ to SFR calibration of (cite: delo14) for their full sample of star-forming galaxies" (4.1 Star Formation Rate) [from (cite: delo14)]
- Simulation/model as data: Zoom-in simulation 'Althaea' spectra (Kohandel+19) and Dahlia (Pallottini+17) compared with observed spectra  
  > "The recent zoom-in cosmological simulations of (cite: koha19) detail the evolution of a disk galaxy (“Althæa”)" (4.2 Comparison to Simulations)

## Processing

### Calibration

- pipeline or manual: CASA automatic pipeline with reduced band-edge flagging  
  > "Calibration was performed using the heuristic-based CASA 5.4.1 automatic pipeline, with reduced automatic band-edge channel flagging" (2 Observations & Data Reduction)
- casa version: CASA 5.4.1  
  > "heuristic-based CASA 5.4.1 automatic pipeline" (2 Observations & Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0158+0133 (bandpass and flux); J0948+0022 phase  
  > "J0158+0133 was used as a bandpass and flux calibrator, while J0948+0022 was used as a phase calibrator." (2 Observations & Data Reduction)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: TCLEAN (cube and MFS continuum)  
  > "The lower sideband was made into a data cube using the CASA task TCLEAN" (2 Observations & Data Reduction)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "To maximise sensitivity, we adopted natural weighting." (2 Observations & Data Reduction)
- uv taper: _not stated_
- cell size: 0.16 arcsec per pixel  
  > "1 pixel=$0.16''$" (3 Imaging Results)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: CASA UVCONTSUB  
  > "Continuum and line emission were separated using the CASA task UVCONTSUB." (2 Observations & Data Reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.07'' x 0.84'' at -81 deg  
  > "a synthesized beam of $1.07''\times0.84''\,$at$\,-81^{\circ}$" (2 Observations & Data Reduction)
- final rms: 0.6 mJy/beam per channel; 0.05 mJy/beam continuum  
  > "RMS noise level of 0.05 mJy beam$^{-1}$" (2 Observations & Data Reduction)

### Inherited from earlier work

- Pipeline calibration with reduced band-edge flagging  
  > "with reduced automatic band-edge channel flagging (Béthermin et al. in prep)" (2 Observations & Data Reduction) [from Béthermin et al. in prep]
- SED fitting for stellar mass and SFR  
  > "Faisst et al. (in prep) find a stellar mass of log(M$_{*}\,[M_{\odot}])=10.6\pm0.1$" (Introduction) [from Faisst et al. (in prep)]

### Not stated but needed to reproduce (our reading)

- Cleaning threshold, niter, masking, image size
- Line-free channels for UVCONTSUB and continuum
- Channel range used for moment maps
- Exact L[CII] formula and SFR calibration coefficients
- Uncertainty propagation for SFR
- Pipeline version and flux-scale uncertainty

## Analysis recipe

1. **Image cube and continuum**: UVCONTSUB, then TCLEAN natural weighting cube; MFS continuum from line-free data  
  > "one continuum image was created using all line-free data in both sidebands using TCLEAN in multi-frequency synthesis mode" (2 Observations & Data Reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Moment maps and source fluxes**: Moment 0/1/2 from channels with >2 sigma emission; fit three 2D Gaussians to moment 0 with IMFIT  
  > "Using the CASA task IMFIT, we simultaneously fit three two-dimensional Gaussians to the moment zero map." (3 Imaging Results)
   - software: CASA IMMOMENTS, CASA IMFIT
   - parameter: channel threshold >2 sigma_LINE, sigma_LINE=0.6 mJy/beam  
  > "channels show emission with $>2\sigma_{\rm LINE}$ ($\sigma_{\rm LINE}$=0.6 mJy beam$^{-1}$)" (3 Imaging Results)
   - fitting: three 2D Gaussians  
  > "Using the CASA task IMFIT, we simultaneously fit three two-dimensional Gaussians to the moment zero map." (Imaging Results)
   - validation: _not stated_
3. **Per-source spectra and redshifts**: Assign spaxels in 2 sigma contour to sources by Gaussian component weights, integrate, fit 1D Gaussians  
  > "we first assign each spaxel within the $2\sigma$ moment zero contour to one of the three sources, based on the relative contributions of each of the three Gaussian components" (3 Imaging Results)
   - software: CASA
   - fitting: 1D Gaussian per spectrum  
  > "For clarity, each spectrum is fit with a one-dimensional Gaussian, and displayed in Figure [2](#globspec), along with its centroid velocity." (Imaging Results)
   - validation: _not stated_
4. **Position-velocity diagram**: IMPV slice 5 pixel thick, 8'' long along RA, averaged in declination  
  > "extracting a 5 pixel thick (1 pixel=$0.16''$), $8''$ long slice across the right ascension axis of the data cube" (3 Imaging Results)
   - software: CASA IMPV
   - fitting: _not stated_
   - validation: _not stated_
5. **Derive SFR from L[CII]**: Apply De Looze+14 L[CII]-SFR calibration per source and sum  
  > "The empirical L$_{\rm [CII]}$ to SFR calibration of (cite: delo14) for their full sample of star-forming galaxies may be used to estimate the SFR of each source individually." (4.1 Star Formation Rate)
   - assumption: flat LCDM, Om=0.3, OL=0.7, H0=70  
  > "We assume a flat $\Lambda$-CDM cosmology ($\Omega_{\Lambda}=0.7$, $\Omega_{m}=0.3$, H$_{o}=70$ km s$^{-1}$) throughout." (Introduction)
   - fitting: _not stated_
   - validation: Compared with SED-based SFR for source C  
  > "is in agreement with our value for the source C of log$_{10}\rm (SFR_{[CII],C}\,[M_{\odot}year^{-1}])=2.59\pm0.24$" (4.1 Star Formation Rate)
6. **Compare spectra with simulations**: Qualitative comparison of global spectrum to Kohandel+19 simulated merger spectra  
  > "This feature is also seen in the face-on merger spectrum of Althæa (figure 6 of (cite: koha19))." (4.2 Comparison to Simulations)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.4.1: Pipeline calibration, UVCONTSUB, TCLEAN, IMMOMENTS, IMFIT, IMPV  
  > "heuristic-based CASA 5.4.1 automatic pipeline" (2 Observations & Data Reduction)
- **LePHARE** : SED modelling for stellar mass and SFR  
  > "the SED modelling code LePHARE" (Introduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Source C [CII] integrated flux | 4.9 | 0.3 | Jy km/s | 2 | / $4.9\pm0.3$ / $2.6\pm0.2$ / $0.8\pm0.2$ / |
| Source E [CII] integrated flux | 2.6 | 0.2 | Jy km/s | 2 | / $4.9\pm0.3$ / $2.6\pm0.2$ / $0.8\pm0.2$ / |
| Source W [CII] integrated flux | 0.8 | 0.2 | Jy km/s | 2 | / $4.9\pm0.3$ / $2.6\pm0.2$ / $0.8\pm0.2$ / |
| Redshift of source C | 4.56038 | 0.00004 | dimensionless | 3 | The redshift of the dominant source C, which will be used as the redshift of this field, is $4.56038\pm0.00004$. |
| Total log SFR[CII] | 2.82 | 0.23 | log Msun/yr | 5 | sum to log$_{10}\rm (SFR_{[CII]}\,[M_{\odot}year^{-1}])=2.82\pm0.23$ |
| log SFR[CII] source C | 2.59 | 0.24 | log Msun/yr | 5 | / log(SFR$_{\rm [CII]}$ \[M$_{\odot}$ year$^{-1}$\]) / $2.59\pm0.24$ / $2.31\pm0.23$ / $1.80\pm0.25$ / |
| Continuum integrated flux of C+E | 1.22 | 0.18 | mJy | 2 | an integrated flux density of $1.22\pm0.18$ mJy |
| Continuum integrated flux of W | 0.26 | 0.11 | mJy | 2 | integrated flux density of $0.26\pm0.11$ mJy |
| L[CII] ratio C/E | 1.86 | not stated | dimensionless | 5 | L$_{\rm [CII],C}/$L$_{\rm [CII],E}=1.86<4$ |

## Qualitative findings

- Source E shows a velocity gradient; C and W nearly constant velocity; dispersion peaks coincide with [CII] sources  
  > "All three show velocity dispersion peaks coincident with the peak of [CII] emission." (Conclusions)

## Claim tuples

- H: Are C and E undergoing a major merger? | E: Compared separation, velocity offset and L[CII] ratio, plus simulation spectra | R: 1.6'' (~11 kpc), ~100 km/s, L ratio 1.86 | F: Ongoing major merger, merging within <0.5 Gyr | **supported**
- H: Is W a separate galaxy that will minor-merge later? | E: Kinematic and luminosity comparison with C | R: ~18 kpc, ~300 km/s, L ratio 6.03 | F: Upcoming minor merger | **partially**
- H: Is [CII] a good SFR tracer here? | E: Compared L[CII] SFR with SED SFR for C | R: 2.59±0.24 vs 2.7 | F: Agreement | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Velocity gradient of E may indicate a rotating or tidally disrupted galaxy  
  > "which may either suggest a rotating galaxy or a tidally disrupted galaxy" (Conclusions)
- How they decided it was enough: _not stated_
- Limitation (authors): Velocity dispersion peaks may be enhanced by beam smearing; SFR uncertainties likely underestimated  
  > "These $\sigma_v$ peaks may be artificially enhanced by beam smearing" (3 Imaging Results)
- Caveat (inferred, ours): Low resolution (~1'') and short 17-min observation limit kinematic inference
- Caveat (inferred, ours): Merger classification is qualitative, based on a single simulation comparison
- Caveat (inferred, ours): Single-component SFR calibration with no dust or AGN considerations

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Clean parameters and masks
- Missing: Line-free channel selection
- Missing: SFR calibration coefficients
- Missing: Faisst et al. SED values unpublished
- Data volume (inferred): ~5-10 GB raw
- Score (inferred): 3/5, Single short observation with standard CASA steps, but imaging parameters are missing.
- Rediscovery candidate: no, Public ALPINE data, but key imaging and SFR calibration details are unstated.

## Links

- Method: Béthermin et al. in prep (ALPINE pipeline calibration)
- Method: (cite: delo14) (L[CII]-SFR calibration)
- Companion: (cite: fais19) (ALPINE survey)
- Companion: Faisst et al. (in prep) (SED fitting results)
- Related: ALPINE
- Related: COSMOS

## Checks

```json
{
 "quotes": 62,
 "quotes_ok": 62,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 43,
  "rate": 0.581
 },
 "evidence_ok": true
}
```
