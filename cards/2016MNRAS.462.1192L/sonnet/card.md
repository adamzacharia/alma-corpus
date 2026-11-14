# Estimating sizes of faint, distant galaxies in the submillimetre regime

`2016MNRAS.462.1192L` | Monthly Notices of the Royal Astronomical Society 2016 | first author: Lindroos, L. | arXiv: 1608.08853 | DOI: 10.1093/mnras/stw1628

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: high_z_galaxies
- Question: What are the typical sizes and flux densities of z~2 star-forming galaxies (DRG, ERO, sBzK, K20) measured by uv-stacking ALESS ALMA 344 GHz data with uv-domain model fitting?  
  > "We measure the sizes of redshift $\sim2$ star-forming galaxies by stacking data from the Atacama Large Millimeter/submillimeter Array (ALMA)." (abstract)
- Target **K20, sBzK, DRG, ERO samples in ECDFS (stacked) and 99 ALESS SMGs**: coordinates _not stated_; z/distance z~2 (photometric redshifts from MUSYC/EAZY)  
  > "The MUSYC catalogue is a $K$-band flux limited sample, covering a $30\ensuremath{'}\times{}30\ensuremath{'}$ area of the ECDFS" (3 PHOTOMETRIC GALAXY SELECTION); distance from photometric redshifts, Taylor et al. 2009 / EAZY  
  > "The MUSYC catalogue is a $K$-band flux limited sample, covering a $30\ensuremath{'}\times{}30\ensuremath{'}$ area of the ECDFS" (3 PHOTOMETRIC GALAXY SELECTION)

## Data provenance

- ALMA projects: 2011.1.00294.S
- bands: 344 GHz continuum  
  > "The observations are tuned to a frequency of 344 GHz and have a typical resolution around 1$.\!\!^{\prime\prime}$6 $\times$ 1$.\!\!^{\prime\prime}$2." (2 DATA)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 18-160 m  
  > "With the $uv$-coverage of our observations (18-160 m)" (abstract)
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: median central noise ~0.4 mJy/beam  
  > "The median value of the noise (standard deviation) in the centre of each pointing is $\sim0.4$mJy/beam." (2 DATA)
- time on source: _not stated_
- observing dates: Cycle 0, October-November 2011  
  > "observed during ALMA Cycle 0 between October and November 2011" (2 DATA)
- pi or archival as stated: ALESS survey data, same as Decarli et al. 2014; 88 good-quality pointings  
  > "As such our data consist of 88 “good quality” pointings" (2 DATA)
- Other facility **MUSYC / Spitzer IRAC / Taiwan ECDFS NIR survey**: Photometric catalogue, photometric redshifts, stellar masses  
  > "The selection is based on the photometric catalogue of the ECDFS assembled using the same procedure as (cite: simpson2014)" (3 PHOTOMETRIC GALAXY SELECTION)
- Other facility **HST (GOODS-S, GEMS)**: z-band images for stellar sizes and morphology model  
  > "The inner parts of the ECDFS are covered by the GOODS-S survey (cite: Giavalisco2004), with Hubble Space Telescope (*HST*) observations in $z$-band" (5.2 Following stellar morphology)
- Other facility **Herschel SPIRE (HerMES)**: Stacked SPIRE flux densities from Decarli et al. 2014 used for dust SED  
  > "(cite: decarli2014) stacked each of the four samples in the three *Herschel* SPIRE bands." (6.4 Star-formation rates)
- External data: Stacked Herschel SPIRE flux densities for the four samples  
  > "(cite: decarli2014) stacked each of the four samples in the three *Herschel* SPIRE bands." (6.4 Star-formation rates) [from (cite: decarli2014)]
- External data: ALESS SMG sub-mm positions (main catalogue, 99 sources)  
  > "We use the sub-mm positions from the main catalogue from (cite: hodge2013) (99 sources)." (6.2 Robustness of the stacked data) [from (cite: hodge2013)]
- Simulation/model as data: Simulated clumpy-morphology and HST z-band-based ALMA datasets (visibilities zeroed, model plus CASA sm noise added), incl. a Cycle 3 C36-5 configuration  
  > "We take the raw ALESS data set and set all visibilities to zero, then we add the model and noise to the data set." (5 SIMULATIONS AND MORPHOLOGY)

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

- task: CASA 4.4 imaging and cleaning of each pointing, only for bright source model  
  > "The data is imaged and cleaned using Common Astronomy Software Applications package[^2] (CASA) version 4.4." (4.1 Removing bright sources)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 0.2 arcsec  
  > "Each pointing is imaged separately with a cell size of 0$.\!\!^{\prime\prime}$2 and cleaned down to a depth 1.8 mJy/beam." (4.1 Removing bright sources)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: CASA 4.4 Airy model, FWHM ~17.5 arcsec; stacking weights = A_N^2  
  > "an Airy pattern with a full width at half maximum (FWHM) of 1.17$\frac{\lambda}{D} \approx 17\mbox{\ensuremath{.\!\!^{\prime\prime}}}{}5$" (4.2 Weights and primary-beam effects)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Data selection (88 good-quality pointings, exclusion criteria)  
  > "All pointings with central noise $>0.6$ mJy/beam or beam axis ratio $>2$ are excluded from the analysis, see (cite: hodge2013) for more details." (2 DATA) [from (cite: hodge2013)]
- Sample selection same as Decarli et al.  
  > "In this paper we extend the analysis of (cite: decarli2014), using the same sample selection." (3 PHOTOMETRIC GALAXY SELECTION) [from (cite: decarli2014)]
- uv-stacking algorithm  
  > "The samples are stacked using the $uv$-stacking algorithm described in (cite: lindroos2015)." (4 STACKING ROUTINE) [from (cite: lindroos2015)]

### Not stated but needed to reproduce (our reading)

- Calibration details of ALESS data (pipeline/manual, CASA version of calibration, flux scale)
- Exact catalogue source positions and sample membership lists
- Source code of the uv-stacking implementation
- Details of visibility weight recalculation bin sizes
- Minimizer starting values
- Herschel SPIRE flux values for SED fits

## Analysis recipe

1. **Select samples and estimate stellar mass**: Colour/photo-z selection (K20, sBzK, DRG, ERO) with K_Vega<20, z>1; PEGASE 2 SED fitting with four templates, lowest chi2  
  > "We limit all samples with $\ensuremath{K_\mathrm{Vega}}< 20$, $z>1$, and further limit the samples as follows:" (3 PHOTOMETRIC GALAXY SELECTION)
   - software: PEGASE 2, EAZY
   - assumption: Kroupa IMF  
  > "all assuming Kroupa IMF, we fit for stellar mass" (3 PHOTOMETRIC GALAXY SELECTION)
   - fitting: _not stated_
   - validation: _not stated_
2. **Subtract bright unrelated sources**: Clean model from each pointing, excluding sources within 1 arcsec of stacking positions, subtracted from uv data; weights recalculated from scatter  
  > "A model for the bright sources is built from the clean model, excluding all sources within 1$''$ of a stacking position." (4.1 Removing bright sources)
   - software: CASA 4.4
   - parameter: clean depth 1.8 mJy/beam, cell 0.2 arcsec  
  > "cleaned down to a depth 1.8 mJy/beam" (4.1 Removing bright sources)
   - fitting: _not stated_
   - validation: Bias test with inserted point sources  
  > "By inserting and stacking point sources in the ALESS data, using the method described in section [4.4](#sec:uncertainties), we evaluate biases in the stacking result." (Robustness of the stacked data)
3. **uv-stack samples**: Weighted average of visibilities phase-shifted to source positions, weights = primary beam attenuation squared; astrometry shifted by 0.3 arcsec in dec  
  > "all stacked datasets were phase rotated with 0$.\!\!^{\prime\prime}$3 in declination." (6.1 Astrometry)
   - parameter: flag baselines <18.2 m (sBzK, DRG) and <21 m (K20, ERO)  
  > "we flag all baseline shorter than $18.2\,\mathrm{m}$ for the sBzK and DRG samples" (6.2 Robustness of the stacked data)
   - fitting: _not stated_
   - validation: Stacked all SMGs: Gaussian fit gives 4.2±0.14 mJy and 0.4±0.06 arcsec, consistent with Simpson et al. 2015  
  > "This agrees well with (cite: simpson2015), which found typical sizes (FWHM) of SMGs between 0$.\!\!^{\prime\prime}$3 and 0$.\!\!^{\prime\prime}$4." (6.2 Robustness of the stacked data)
4. **Fit point-source and Gaussian models in uv-domain**: Least-squares fit of point source and circular Gaussian to all non-flagged visibilities with weights, flux positive  
  > "The models are fitted in the $uv$-domain to our stacked sources using the least square minimizer package Ceres ." (4.3 Model fitting)
   - software: Ceres
   - parameter: Levenberg-Marquardt, Cholesky solver, max 50 iterations  
  > "The fit is terminated at the first to occur within 50 iterations" (footnote 3)
   - fitting: Levenberg-Marquardt chi2 minimization, 2 free parameters (flux, FWHM)  
  > "In the plot is shown the fit from the Gaussian model, with two free parameters: the total flux density and the FWHM size." (Flux densities and sizes of the stacked sources)
   - validation: Compared to Vidal et al. size-limit formula; beta 0.4-0.5  
  > "Using this formula we find our size error to be consistent with a $\beta$ between 0.4 and 0.5." (7.2 Robustness of the measured sizes)
5. **Estimate uncertainties**: Monte Carlo insertion of random sources (100 runs) and bootstrap resampling of galaxies (1000 runs; errors from CDF at 0.159/0.841)  
  > "This procedure is repeated a 100 times for each sample and model" (4.4)
   - fitting: _not stated_
   - validation: _not stated_
6. **Deconvolve optical-submm positional offsets**: Offsets from 11 galaxies with peak SNR>5; offset modelled as circular Gaussian FWHM 0.36 arcsec, deconvolved from sizes  
  > "the offset between the submm and measured optical position can be modelled as a circular Gaussian with a FWHM of $0.36^{+0.06}_{-0.09}$" (6.1 Astrometry)
   - fitting: _not stated_
   - validation: _not stated_
7. **Fit dust SED and derive SFR**: Modified blackbody with beta fixed 1.6, free T and L_IR, chi2 fit using stacked ALMA and Herschel SPIRE; SFR=1.3e-10 L_IR  
  > "The value of $\beta$ is fixed to 1.6." (6.4 Star-formation rates)
   - assumption: Chabrier IMF; L_IR 8-1000 micron  
  > "The total IR luminosity ($L_\mathrm{IR}$) is calculated between 8 $\mu$m and 1000 $\mu$m" (6.4 Star-formation rates)
   - fitting: chi2 minimization, weights sigma^-2  
  > "The dust emission is fitted using a $\chi^2$ minimization, with two free parameters, $T$ and $L_\mathrm{IR}$. The value of $\beta$ is fixed to 1.6. Each data point is weighted by $\sigma^{-2}$." (Star-formation rates)
   - validation: Compared to Tacconi et al. 2013 main sequence  
  > "The measured values fall close to the best-fit “main sequence” for star-forming galaxies at similar redshifts, (e.g. the (cite: tacconi2013) parametrization for comparison)." (Star-formation rates)
8. **Simulate morphologies**: Simulated clumpy model (3 clumps, 0.7 mJy each) and HST z-band-based model on ALESS and Cycle 3 C36-5 uv-coverage; stack identically  
  > "For each source in the sample we generate 3 clumps, i.e., 3 point sources." (5.1 Clumpy morphology)
   - software: CASA sm
   - fitting: _not stated_
   - validation: Recovered flux 2.3±0.2 mJy vs input 2.1 mJy  
  > "The Gaussian model recovers an average flux density for the stacked sources of $2.3\pm0.2$ mJy, compared to the input flux density for the simulation of 2.1 mJy per source." (Simulations)

## Software

- **CASA** 4.4: imaging, clean models, primary beam model, simulator (sm)  
  > "Common Astronomy Software Applications package[^2] (CASA) version 4.4" (4.1 Removing bright sources)
- **Ceres Solver** : uv-domain model fitting  
  > "using the least square minimizer package Ceres ." (4.3 Model fitting)
- **PEGASE 2** : stellar mass fitting  
  > "The stellar-mass estimates are done using PEGASE 2" (3 PHOTOMETRIC GALAXY SELECTION)
- **EAZY** : MUSYC photometric redshifts  
  > "estimated using EAZY (cite: brammer2008)" (3 PHOTOMETRIC GALAXY SELECTION)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| K20 stacked Gaussian flux density | 1.85 | 0.30 | mJy | 4 | K20& 52 & $1.85\pm0.30$ |
| sBzK Gaussian flux density | 2.34 | 0.32 | mJy | 4 | sBzK & 22 & $2.34\pm0.32$ |
| DRG Gaussian flux density | 2.44 | 0.28 | mJy | 4 | DRG & 19 & $2.44\pm0.28$ |
| ERO Gaussian flux density | 1.51 | 0.22 | mJy | 4 | ERO & 25 & $1.51\pm0.22$ |
| Stacked sizes range (FWHM) | 0.65-0.73 | 0.14-0.17 | arcsec | 4 | with stacked sizes between $0\mbox{\ensuremath{.\!\!^{\prime\prime}}}65$ and $0\mbox{\ensuremath{.\!\!^{\prime\prime}}}73$ |
| Deconvolved sizes range | 0.54-0.64 | 0.16-0.19 | arcsec | 6 | we find deconvolved sizes for our samples between $0\mbox{\ensuremath{.\!\!^{\prime\prime}}}54$ and $0\mbox{\ensuremath{.\!\!^{\prime\prime}}}64$ |
| SMG stack flux density | 4.2 | 0.14 | mJy | 4 | with a flux density $4.2\pm0.14$ mJy |
| sBzK SFR | 86 | 14 | Msun/yr | 7 | sBzK & $6.7\pm1.1$ & $27\pm2$ & $86\pm14$ |
| DRG SFR | 102 | 20 | Msun/yr | 7 | DRG & $7.8\pm1.6$ & $28\pm2$ & $102\pm20$ |
| Simulated clumpy flux with ALESS baselines | 2.3 | 0.2 | mJy | 8 | The Gaussian model recovers an average flux density for the stacked sources of $2.3\pm0.2$ mJy |

## Qualitative findings

- Stacked sources are extended; sub-mm sizes agree with HST z-band sizes; short baselines are essential to recover total stacked flux density.  
  > "This highlights the importance of short baselines to recover the full flux density of high-redshift galaxies." (abstract)

## Claim tuples

- H: z~2 star-forming galaxies are extended at 344 GHz | E: uv-stacking and Gaussian uv-model fit for four samples | R: FWHM ~0.65-0.73 arcsec, deconvolved 0.54-0.64 arcsec, >3 sigma | F: Typical sizes ~5-6 kpc, matching z-band sizes | **supported**
- H: Point-source assumption underestimates stacked flux | E: Compare uv model fitting to point-source and image stacking | R: Gaussian fluxes 20-40% higher than Decarli et al. | F: Model fitting recovers full flux if short baselines are available | **supported**
- H: Intermediate baselines suffice | E: Simulated Cycle 3 C36-5 configuration | R: Only 90 uJy recovered vs 2.3 mJy | F: Short baselines are crucial | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: uv-stacking avoids combining differently restored images, allowing deconvolution of source size  
  > "Using $uv$-stacking, we combine the data in the $uv$-domain, and the beam can be directly calculated from the new $uv$-coverage." (INTRODUCTION)
- How they decided it was enough: _not stated_
- Limitation (authors): GEMS z-band less deep, possibly underestimating stellar sizes; bright source subtraction incomplete on shortest baselines  
  > "As such is possible that we are missing low flux surface density emission, and underestimating the size of these galaxies." (7.3)
- Caveat (inferred, ours): Optical-submm offset modelled from only 11 galaxies
- Caveat (inferred, ours): Bright source subtraction based on clean models leaves residuals, handled by flagging short baselines
- Caveat (inferred, ours): Fixed beta and few SED points

## Reproducibility

- Data public (paper): ALESS data 2011.1.00294.S cited; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.1.00294.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: uv-stacking code
- Missing: sample source lists
- Missing: Herschel stacked fluxes
- Data volume (inferred): ~50-100 GB for Cycle 0 ALESS data
- Score (inferred): 3/5, Data archival and method described in detail, but stacking code and catalogs not provided.
- Rediscovery candidate: no, Requires external catalogs and unreleased stacking code.

## Links

- Method: (cite: lindroos2015) (uv-stacking algorithm)
- Method: (cite: vidal2012) (minimum measurable size in interferometric model fitting)
- Companion: (cite: decarli2014) (same data and samples, image stacking)
- Companion: (cite: hodge2013) (ALESS survey)
- Related: ALESS
- Related: LESS
- Related: MUSYC
- Related: GOODS-S
- Related: GEMS
- Related: HerMES

## Checks

```json
{
 "quotes": 63,
 "quotes_ok": 63,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.1.00294.S"
 ],
 "obscore_codes_not_in_card": [
  "2011.0.00294.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 87,
  "stated": 48,
  "rate": 0.552
 },
 "evidence_ok": true
}
```
