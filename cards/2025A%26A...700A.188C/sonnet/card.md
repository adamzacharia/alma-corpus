# FAUST: XXVI. The dust opacity spectral indices of protostellar envelopes bridge the gap between interstellar medium and disks

`2025A&A...700A.188C` | Astronomy and Astrophysics 2025 | first author: Cacciapuoti, L. | arXiv: 2506.06865 | DOI: 10.1051/0004-6361/202554645

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: star_formation, protoplanetary_disks
- Question: What are the dust opacity spectral indices (beta) of protostellar envelopes, after removing the optically thick disk contribution, and do they bridge ISM-like and disk-like values?  
  > "we show how envelope spectral indices distribute between ISM-like and disk-like values, bridging the gap in the inferred dust evolution." (abstract)
- Target **13 FAUST Class 0/I protostars (IRAS 15398-3359, CB68, L483, Elias 29, VLA1623A, GSS30, RCra IRS7B, BHB07-11, IRS63, NGC1333 IRAS4A, IRAS4C, L1527 IRS, L1551-IRS5)**: coordinates _not stated_; z/distance 130-235 pc depending on region (e.g. Lupus 155 pc, Perseus 235 pc)  
  > "| IRAS 15398-3359 | 0.92$^{(a)}$ | 44$^{(a)}$ | 1.2$^{(a)}$ | 70$^{(s)}$ | N | 0 | Lupus (155 pc) |" (Table 1); distance from _not stated_

## Data provenance

- ALMA projects: 2018.1.01205.L, 2016.1.01203.S
- bands: Band 3 (3.1 mm, 95 GHz) and Band 6 (1.2 mm, 239 GHz)  
  > "two wavelength windows within the 1.2 mm (239 GHz) and 3.1 mm (95 GHz) atmospheric windows" (2 Observations and sample)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.3''-0.4'' (FAUST); common 1x1 arcsec restoring beam used here  
  > "ensure a resolution of 0.3$''$-0.4$''$ and a maximum recoverable scale of up to 14.4$''$" (2 Observations and sample)
- max recoverable scale: up to 14.4''  
  > "a maximum recoverable scale of up to 14.4$''$" (2 Observations and sample)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: FAUST Large Program, PI Yamamoto  
  > "project-ID 2018.1.01205.L, PI: Yamamoto, S." (2 Observations and sample)
- External data: Beta measurements for 9 CALYPSO sources (PdBI) for comparison and combined correlation analysis  
  > "Adding to previous 9 measurements in the literature (G19), we build a more statistically relevant sample." (Conclusions) [from (cite: Galametz2019)]
- External data: L1527 IRS envelope beta and compact-component results from pilot study  
  > "Note: (a) is from (cite: Cacciapuoti2023)." (Table 1) [from (cite: Cacciapuoti2023)]
- External data: Planck ISM beta distribution (1.51 +/- 0.13) and Lupus Class II disk spectral indices used in comparison figure  
  > "a representative distribution ($\beta = 1.51 \pm 0.13$) of the ones at galactic scales as measured by (cite: Planck2014)" (5.1) [from (cite: Planck2014), (cite: Tazzari2021)]

## Processing

### Calibration

- pipeline or manual: Modified ALMA pipeline, with correlator per-channel normalisation correction  
  > "The FAUST data were calibrated using a modified version of the ALMA pipeline" (2.1)
- casa version: CASA 5.6.1-8  
  > "version 5.6.1-8" (2.1)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: default calibrators  
  > "Within FAUST, the default calibrators were used for the flux calibration" (2.1)
- flux scale uncertainty: 2.5% Band 3, 5% Band 6; 0.1 systematic error on alpha  
  > "This flux calibration error corresponds to 2.5% and 5% for Band 3 and Band, 6 respectively" (4)
- self calibration: Per-configuration phase-only then amplitude+phase self-cal; per-integration phase, per-scan amplitude; configurations aligned via self-cal  
  > "For the amplitude self-calibration, the approach was “per-scan”." (2.1)

### Imaging

- task: CASA tclean  
  > "using the `uvtaper` parameter of the CASA `tclean` routine" (2.1)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 1  
  > "using a Briggs weighting scheme with a robust parameter of 1" (2.1)
- uv taper: uv range 6-150 klambda; uvtaper in tclean to match beams for 2D alpha maps  
  > "restraining the utilized uv-distances in the range 6-150 k$\lambda$" (2.1)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: Line-free LSRK ranges by visual inspection, averaged per spw  
  > "Line-free Local Standard of Rest Kinematic (LSRK) frequency ranges were identified by visual inspection" (2.1)
- primary beam correction: images primary-beam corrected  
  > "We show the primary–beam–corrected images in Fig." (2.1)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: common 1 x 1 arcsec restoring beam (Table: 1.15x1.05x15 deg)  
  > "We applied a common restoring beam of 1 $\times$ 1 arcsec." (2.1)
- final rms: _not stated_

### Inherited from earlier work

- Full FAUST calibration and reduction details deferred to a companion paper  
  > "More details on the FAUST data calibration and reduction can be found in Chandler et al., (in prep.)." (2.1) [from Chandler et al., in prep.]
- uv-plane disk/envelope decomposition method  
  > "We utilise the methods of (cite: Cacciapuoti2023) to disentangle disk and envelope emission" (Conclusions) [from (cite: Cacciapuoti2023)]
- Temperature profile parametrisation for beta  
  > "Based on, e.g. (cite: Adams1985), (cite: Motte2001), we parametrised the dust temperature" (4) [from (cite: Adams1985), (cite: Motte2001)]

### Not stated but needed to reproduce (our reading)

- Exact ALMA configurations, execution blocks and on-source times per source
- Spectral window frequencies and continuum bandwidths
- Cell size, image size, masking, deconvolver and clean threshold
- Self-calibration solution intervals
- Burn-in and convergence diagnostics for emcee
- Which uv-bins and uncertainties were used for alpha and beta profiles
- How beta at 500 au was extrapolated and gradient fit
- Source coordinates and phase centers
- Model choice criteria per source beyond visual inspection
- Details of literature beta values and Menv used for combined correlation

## Analysis recipe

1. **Calibrate and self-calibrate continuum**: Modified ALMA pipeline, per-configuration self-calibration and cross-configuration alignment  
  > "initial continuum images were produced for each separate ALMA configuration" (2.1)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Image continuum for morphology**: Briggs robust 1, uv 6-150 klambda, common 1x1'' beam; used to choose uv models  
  > "visually determine which model to be fit in the uv-plane" (2.1)
   - software: CASA tclean
   - fitting: _not stated_
   - validation: _not stated_
3. **Remove secondary sources in field**: Model distant secondaries as Gaussians and subtract from visibilities; close secondaries fit jointly  
  > "We modeled the secondary sources as gaussians using `uvmodelfit` CASA routine" (Removal of secondaries)
   - software: CASA uvmodelfit, CASA ft, CASA uvsub
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit visibilities with compact (Gaussian) plus Plummer envelope models**: Sum of 2D Gaussians and Plummer envelope visibilities fit per band  
  > "we consider the total model to be the sum of the visibilities of the individual components" (3)
   - software: emcee, galario, CARTA
   - parameter: Uniform priors: sigma 0-0.7'', Ri 0-2.0'', Rout 2.0-15.0'', p+q in [1,3], inc/PA full range, offsets within few tenths of arcsec  
  > "Finally, the envelope power law exponent p+q was set free in the range \[1,3\]." (3)
   - parameter: 120 walkers, 25000 steps  
  > "We ran 120 walkers for 25000 steps to reach convergence" (3)
   - fitting: MCMC with emcee, galario chi2 on visibilities, uniform priors  
  > "The parameters were all set to vary within uniform prior distributions." (3)
   - validation: Reduced chi2 reported; compact flux saturation at 150-200 klambda consistent with Galametz2019  
  > "We thus confirm that their approach is robust" (3)
5. **Compute alpha profiles of total and envelope-only emission**: Alpha from fluxes in azimuthally averaged uv bins common to both bands, with compact component subtracted for envelope  
  > "we compute $\alpha$ across azimuthally averaged baseline bins common between 1.2 and 3.1 mm" (2.1)
   - parameter: nu1 = 95 GHz, nu2 = 233 GHz; 0.1 systematic error from flux calibration  
  > "$\nu_1 = 95$ GHz and $\nu_2 = 233$ GHz" (4)
   - fitting: _not stated_
   - validation: Compared to image-plane alpha maps and Galametz2019  
  > "these image plane spectral indices are consistent with the ones computed in the uv-plane analysis." (4.2)
6. **Derive beta and its gradient**: beta = alpha - 2 (RJ, optically thin) and full form with temperature profile; linear fit in log R  
  > "we computed the dust opacity spectral index $\beta$ in the optically thin and Rayleigh-Jeans approximation, $\beta = \alpha - 2$" (4)
   - assumption: T(R) = 38 (L/Lsun)^0.2 (R/100au)^-0.4 K  
  > "T(R) = 38 \times \Bigg(\frac{\textrm{L}}{\textrm{L$_{\odot}$}}\Bigg)^{0.2}" (4)
   - fitting: _not stated_
   - validation: Varying T by 10 K or index in [-0.3,-0.6] changes beta within 10%  
  > "the derived $\beta$ values remain well within a 10% uncertainty" (4)
7. **Correlate beta with protostellar properties and compare with CALYPSO**: Pearson correlation (scipy pearsonr) and KS test on combined sample  
  > "we used the `pearsonr` routine of `scipy`" (5.3)
   - software: scipy
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.6.1-8: calibration, tclean imaging, uvmodelfit/uvsub  
  > "version 5.6.1-8" (2.1)
- **emcee** : MCMC sampling of model parameters  
  > "we used `emcee` (cite: Foreman-Mackey2013) and `galario` (cite: Tazzari2018)" (3)
- **galario** : Fourier transform of models and chi2 against visibilities  
  > "Then it Fourier-transforms the model into synthetic visibilities" (3)
- **CARTA** : inspect data to set component offset priors  
  > "Cube Analysis and Rendering Tool for Astronomy (CARTA, (cite: Comrie2021))" (3)
- **scipy** : pearsonr correlation tests  
  > "we used the `pearsonr` routine of `scipy`" (5.3)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| beta_env at 500 au, IRAS15398-3359 | 1.41 | 0.09 | dimensionless | 6 | / IRAS15398-3359 / -0.17 $\pm$ 0.20 / 1.41 $\pm$ 0.09 / |
| beta_env at 500 au, IRAS4A | 1.10 | 0.03 | dimensionless | 6 | / IRAS4A / 0.76 $\pm$ 0.11 / 1.10 $\pm$ 0.03 / |
| beta_env at 500 au, L1551-IRS5 | 0.94 | 0.04 | dimensionless | 6 | / L1551-IRS5 / -0.04 $\pm$ 0.11 / 0.94 $\pm$ 0.04 / |
| beta_env at 500 au, VLA1623A | 1.43 | 0.05 | dimensionless | 6 | / VLA1623A / 0.45 $\pm$ 0.25 / 1.43 $\pm$ 0.05 / |
| Mean beta FAUST vs CALYPSO | 1.42 vs 0.78 | 0.06 and 0.09 | dimensionless | 7 | the mean $\beta$ is 1.42 $\pm$ 0.06, whereas the average $\beta$ of the latter is 0.78 $\pm$ 0.09 |
| KS test statistic and p-value | 0.4, p=0.003 | not stated | dimensionless | 7 | results 0.4 and relative p-value is 0.003 |
| p-value beta vs Menv; gradient vs Menv | 0.01; 0.001 | not stated | dimensionless | 7 | the p-values decrease to 0.01 for $\beta$ vs M$_{env}$ and to 0.001 for $\beta^{env}_{grad}$ vs M$_{env}$ |
| alpha of compact component, IRAS15398-3359 | 2.2 | 0.2 | dimensionless | 4 | / IRAS15398-3359 / 1.28 / 8.09 / 9 / 2.2 $\pm$ 0.2 / |

## Qualitative findings

- Most envelopes show flat, ISM-like beta (~1.4-1.8), implying maximum grain sizes below ~100 micron; IRAS4A, L1527 and L1551-IRS5 show lower beta or gradients.  
  > "which indicate a dust size distribution with maximum grain sizes less than 100 $\mu$m, for eight sources." (Conclusions)
- No correlation of beta with Tbol, Lbol or inclination.  
  > "We find no correlation of $\beta$ with source evolutionary stage" (Conclusions)

## Claim tuples

- H: Do envelope beta values lie between ISM and disk values? | E: Measure uncontaminated envelope beta for FAUST sources and combine with CALYPSO | R: Envelope beta spans ISM-like to disk-like values | F: Dust optical properties vary smoothly from ISM through envelopes to disks | **supported**
- H: Does beta correlate with envelope mass? | E: Pearson test on combined FAUST+CALYPSO sample | R: p = 0.01 (beta) and 0.001 (gradient) | F: Significant correlation confirmed | **supported**
- H: Are young disks optically thick and small? | E: Fit compact Gaussian components and compute alpha | R: alpha~2 for most; sizes down to <9 au | F: Young disks are compact and optically thick | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: uv-plane modelling avoids image-plane weighting issues and disentangles compact and extended emission  
  > "it is hard to spatially disentangle the contribution of compact and extended structures in the image plane" (3)
- Alternative: Image-plane alpha maps attempted for four-five sources only, limited by disk-envelope contamination  
  > "computing 2D spectral index maps is a challenging task and their interpretation is limited by the mutual contamination of disk and envelope" (4.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Azimuthal averaging in the uv-plane loses 2D morphology information  
  > "the main one being the loss of information about the 2D source morphology" (3)
- Limitation (authors): High chi2 for asymmetric envelopes and unsubtracted FOV sources  
  > "in some cases, the $\chi^2$ results significantly higher than unity" (3)
- Caveat (inferred, ours): Spherical Plummer model poorly describes asymmetric envelopes
- Caveat (inferred, ours): Temperature profile assumed, not constrained
- Caveat (inferred, ours): Dust optical depth and scattering may bias beta
- Caveat (inferred, ours): Heterogeneous sample comparison with CALYPSO
- Caveat (inferred, ours): Elias 29 emission may include free-free

## Reproducibility

- Data public (paper): ALMA data acknowledged by project code  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.01205.L, ADS/JAO.ALMA#2016.1.01203.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Chandler et al. FAUST calibration details (in prep.)
- Missing: Self-calibration parameters
- Missing: Imaging cell/image size
- Missing: Per-source model choices and bins
- Data volume (inferred): Large; several hundred GB to ~1 TB raw for 13 sources in two bands
- Score (inferred): 3/5, Methods and priors given and software named, but calibration/self-cal details deferred and the data are a large program requiring custom reduction.
- Rediscovery candidate: no, Needs the custom FAUST self-calibrated products and many unstated choices.

## Links

- Method: (cite: Cacciapuoti2023) (pilot uv-plane disk-envelope decomposition for L1527)
- Method: (cite: Galametz2019) (CALYPSO beta method and comparison sample)
- Companion: Chandler et al., in prep. (FAUST data calibration and reduction)
- Companion: (cite: Sabatini2025) (L1551-IRS5 cavity wall dust analysis)
- Related: FAUST
- Related: CALYPSO
- Related: eDisk

## Checks

```json
{
 "quotes": 64,
 "quotes_ok": 64,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 84,
  "stated": 50,
  "rate": 0.595
 },
 "evidence_ok": true
}
```
