# The ALMA Frontier Fields Survey. I. 1.1 mm continuum detections in Abell 2744, MACS J0416.1-2403 and MACS J1149.5+2223

`2017A&A...597A..41G` | Astronomy and Astrophysics 2017 | first author: González-López, J. | arXiv: 1607.03808 | DOI: 10.1051/0004-6361/201628806

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Can ALMA 1.1 mm mosaics of three Frontier Fields lensing clusters detect sub-mJy dusty star-forming galaxies, and what are their fluxes, sizes and NIR counterpart offsets?  
  > "In this first paper of our series, we describe our methods for finding high redshift faint dusty galaxies using millimeter observations with ALMA." (abstract)
- Target **Abell 2744**: coordinates 00:14:21.2 -30:23:50.1 (J2000)  
  > "| Abell 2744 | 0.308 | 00:14:21.2 | $-$30:23:50.1 |" (Table 1); z/distance z=0.308  
  > "| Abell 2744 | 0.308 | 00:14:21.2 | $-$30:23:50.1 |" (Table 1); distance from _not stated_
- Target **MACSJ0416.1-2403**: coordinates 04:16:08.9 -24:04:28.7 (J2000)  
  > "| MACSJ0416.1$-$2403 | 0.396 | 04:16:08.9 | $-$24:04:28.7 |" (Table 1); z/distance z=0.396  
  > "| MACSJ0416.1$-$2403 | 0.396 | 04:16:08.9 | $-$24:04:28.7 |" (Table 1); distance from _not stated_
- Target **MACSJ1149.5+2223**: coordinates 11:49:36.3 +22:23:58.1 (J2000)  
  > "| MACSJ1149.5$+$2223 | 0.543 | 11:49:36.3 | $+$22:23:58.1 |" (Table 1); z/distance z=0.543  
  > "| MACSJ1149.5$+$2223 | 0.543 | 11:49:36.3 | $+$22:23:58.1 |" (Table 1); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00999.S
- bands: 1.1 mm, LO 263.14 GHz  
  > "The Local Oscillator frequency was set to 263.14 GHz ($\approx$1.1 mm), with two spectral windows placed in each sideband." (2.1 Observations)
- frequencies and spectral setup: FDM, 1875 MHz bandwidth per SPW, 7.45 GHz total, averaged to 7.813 MHz channels (~9 km/s)  
  > "resulting in a final spectral resolution of 7.813 MHz ($\sim9{{\rm \thinspace km\thinspace s}^{-1}}$)" (2.1 Observations)
- continuum bandwidth: _not stated_
- arrays: 12 m array  
  > "using the array of 12 m antennas" (2.1 Observations)
- configurations: C36-2 for MACSJ0416, MACSJ1149 and last two A2744 executions; first four A2744 executions more extended  
  > "The first four executions on A2744 were carried out in a more extended configuration." (2.1 Observations)
- baselines: 15.1-783.5 m (A2744), 15.1-348.5 m (others)  
  > "| Abell 2744 | 0.308 | 00:14:21.2 | $-$30:23:50.1 | 29-Jun-2014/31-Dec-2014 | 15.1 | 783.5 | $170.0\,|\,115.6$ |" (Table 1)
- angular resolution: natural beams 0.63x0.49'', 1.52x0.85'', 1.22x1.08''  
  > "| Abell 2744 | Natural | 0.63 | 0.49 | 86.14 | 55 |" (Table 2)
- max recoverable scale: _not stated_
- sensitivity: rms 55, 59, 71 uJy/beam  
  > "we reach observed rms sensitivities of 55, 59 and 71 ${\rm \mu Jy}\,{\rm beam}^{-1}$ respectively" (abstract)
- time on source: _not stated_
- observing dates: Jun 2014 - May 2015  
  > "| MACSJ0416.1$-$2403 | 0.396 | 04:16:08.9 | $-$24:04:28.7 | 04-Jan-2015/02-May-2015 |" (Table 1)
- pi or archival as stated: _not stated_
- Other facility **HST WFC3/IR F160W (Frontier Fields)**: NIR counterparts and positions  
  > "Based on the deep *HST* $F160W$ imaging, a counterpart search was performed" (3.2 High-significance continuum detections)
- Other facility **GLASS**: spectroscopic redshifts for MACSJ0416-ID01 and ID02  
  > "obtained from the Grism Lens-Amplified Survey from Space (cite: Treu2015)" (4.3 Source sizes)
- External data: Lens models for magnification from FF archive teams  
  > "We estimate the magnification values as in (cite: Coe2015), by taking the 16th, 50th and 84th percentiles of the magnification values given by the full range from all the models" (4.3 Source sizes) [from (cite: Coe2015)]
- External data: Comparison samples of sizes/fluxes (SMA, SDP.81, UDS, HerMES)  
  > "objects from the UKIDSS ultra deep survey (UDS) part of the SCUBA-2 cosmology legacy survey and the un-lensed objects from the *Herschel* Multi-tiered Extragalactic Survey (HerMES)" (4.3 Source sizes) [from (cite: Simpson2015; Bussmann2015)]
- External data: Source number density >0.084 mJy used for confusion estimate  
  > "We should expect a number density of $\approx10^{4.8}\,\,{\rm deg}^{-2}$ sources with flux densities $>0.084$ mJy (cite: Fujimoto2016)." (4.2.1 Image fit) [from (cite: Fujimoto2016)]
- Simulation/model as data: CASA simobserve simulations (30 per configuration) for purity  
  > "We performed 30 simulations per antenna configuration and recorded the number of detections with $S/N\geq5$ recovered by our code." (4.1 Purity)

## Processing

### Calibration

- pipeline or manual: MACSJ0416 via ALMA pipeline; A2744 and MACSJ1149 manual script reduction  
  > "The manual ("script") reduction of A2744 and MACSJ1149, as well as all imaging and analysis of the clusters, were performed using casa version 4.3.1." (2.2 Reduction)
- casa version: CASA 4.2.2 (pipeline), 4.3.1 (manual reduction and imaging)  
  > "reduced using the ALMA pipeline included in casa version 4.2.2" (2.2 Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Uranus, Ganymede, Titan, Callisto, J2258-279, J0334-401, 3C273  
  > "For MACSJ0416, the amplitude calibrators were J0334$-$401, Ganymede and Uranus" (2.2 Reduction)
- flux scale uncertainty: ~8%  
  > "We estimate that the flux calibration for each field is accurate to $\sim$8% based on a comparison of the amplitudes for the different flux calibrators." (2.2 Reduction)
- self calibration: _not stated_

### Imaging

- task: CLEAN, mfs, clark psfmode, mosaic imagermode  
  > "adopting the `clark` psfmode, the `mosaic` imagermode, and a 0.1$''$ pixel size" (2.3 Imaging)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "Mosaicked images were created using natural weighting" (2.3 Imaging)
- uv taper: outertaper 1.5'' for check images  
  > "includes a uvtaper with an outertaper equal to 1.5$''$" (4.2.2 uv-plane fit)
- cell size: 0.1''  
  > "a 0.1$''$ pixel size" (2.3 Imaging)
- image size: _not stated_
- masking: no masking; niter=1000, threshold 4x dirty rms  
  > "The cleaned images were generated using `niter`=1000 and a threshold of four times the rms measured in the dirty images, with no masking applied during cleaning." (2.3 Imaging)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: detection on PB-uncorrected images; PB>=0.5 region  
  > "We limited the region used for source detection to that where the PB sensitivity is higher than 0.5 of the peak sensitivity (PB$\geq0.5$)." (3.1 Source extraction)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Reduction follows JAO delivered scripts and most JAO manual flags  
  > "Our reduction procedure closely followed the reduction scripts delivered by joint ALMA observatory (JAO) together with the datasets." (2.2 Reduction) [from JAO reduction scripts]
- Magnification estimation method  
  > "We estimate the magnification values as in (cite: Coe2015)" (4.3 Source sizes) [from (cite: Coe2015)]
- Full size-reliability characterization deferred to earlier work  
  > "we refer interested readers to (cite: Bussmann2013; Bussmann2015) for such details." (4.3 Source sizes) [from (cite: Bussmann2013; Bussmann2015)]

### Not stated but needed to reproduce (our reading)

- DBSCAN parameters (eps, min_samples)
- Priors and initial parameter ranges for uvmcmcfit
- Number of walkers
- Exact simobserve settings (PWV, integration time)
- Which lens models and versions exactly were used per cluster
- Cosmology parameters
- Details of fake point-source injection (flux grid, number)

## Analysis recipe

1. **calibrate and image mosaics**: JAO-based reduction, edge channels reinstated, natural-weighted mfs mosaic CLEAN  
  > "The data were imaged using the multi-frequency synthesis algorithm in `CLEAN`" (2.3 Imaging)
   - software: CASA
   - parameter: niter=1000, threshold 4x rms, 0.1'' pixels  
  > "The cleaned images were generated using `niter`=1000 and a threshold of four times the rms measured in the dirty images" (2.3 Imaging)
   - fitting: _not stated_
   - validation: _not stated_
2. **detect sources and assess purity**: sigma-clip rms in PB>=0.5, S/N>=5 pixels grouped with DBSCAN, 2D Gaussian fits; purity from simobserve simulations and NIR counterparts  
  > "used the clustering algorithm `DBSCAN` in `Python:scikit-learn` (cite: Pedregosa2011) to group the pixels that corresponded to unique sources." (3.1 Source extraction)
   - software: scikit-learn, CASA simobserve
   - parameter: S/N>=5 cut  
  > "We adopted a traditional $S/N$ cut of $\geq$ 5 to select "secure" detections" (3.2 High-significance continuum detections)
   - fitting: six-parameter and three-parameter 2D Gaussians  
  > "we also fit a 2d-Gaussian function with only three free parameters, fixing the shape to that of the synthesized beam" (3.2 High-significance continuum detections)
   - validation: N<<1 false detections at S/N>=5 in simulations  
  > "we obtain $N\ll1$ simulated-noise detections for $S/N\geq5$" (4.1 Purity)
3. **measure flux densities and sizes in uv-plane**: uvmcmcfit elliptical Gaussian in uv-plane after PB-weighting pointings within 19''  
  > "We estimate an initial source position based on the continuum images and select all pointings which lie within 19$''$ (PB$\geq$0.1) of the initial position." (4.2.2 uv-plane fit)
   - software: uvmcmcfit, emcee
   - parameter: 10,000-240,000 iterations, 5,000 burn-in  
  > "Between 10,000–240,000 iterations were required, depending on the speed of convergence." (4.2.2 uv-plane fit)
   - assumption: no magnification modeled in the fit (lensed image plane)  
  > "We chose to first model the observed sources as if no magnification were present." (4.2.2 uv-plane fit)
   - fitting: emcee sampling of likelihood in visibilities; 1 sigma range of posterior  
  > "`uvmcmcfit` uses `EMCEE` (cite: Foreman-mackey2013) to sample the posterior probability density function (PDF) of the model parameters." (4.2.2 uv-plane fit)
   - validation: compared with fluxes from 1.5'' tapered images; injected fake sources  
  > "We see that the two estimates agree within the errors" (4.2.2 uv-plane fit)
4. **demagnify sizes and fluxes**: magnification from 16/50/84th percentiles of FF lens models; r/sqrt(mu), F/mu  
  > "We correct the effective radius as $r_{s}/\sqrt{\mu}$ and the flux density as $F_{\rm uv-fit}/\mu$." (4.3 Source sizes)
   - assumption: z=2 (range 1-3) for sources without spectroscopic redshift  
  > "we will assume that they lie at $z$$=$2 and use the range $z$$=$1–3 as an estimate of the error" (4.3 Source sizes)
   - fitting: linear regression log r_s vs log F with HerMES comparison  
  > "we fit a linear regression between flux density and effective radius as $\log{r_{\rm s}} = m\times\log{F_{\nu}} + b$" (4.3 Source sizes)
   - validation: _not stated_
5. **measure ALMA-HST positional offsets**: 2D Gaussian centroid of F160W counterpart vs ALMA; source plane offsets via Zitrin-NFWv3 and LTMv1  
  > "we tracked the positions of the centroids in ALMA and *HST* to the source plane using the lensing models of Zitrin-NFWv3 and Zitrin-LTMv1" (4.4 Positional Offsets)
   - fitting: _not stated_
   - validation: phase calibrator positions compared to literature  
  > "By comparing the observed positions of the phase calibrators used in the ALMA observations to those in the literature" (4.4 Positional Offsets)

## Software

- **CASA** 4.2.2 (pipeline), 4.3.1: reduction, imaging, simobserve  
  > "were performed using casa version 4.3.1" (2.2 Reduction)
- **scikit-learn DBSCAN** : grouping pixels into sources  
  > "used the clustering algorithm `DBSCAN` in `Python:scikit-learn`" (3.1 Source extraction)
- **uvmcmcfit** : uv-plane model fitting  
  > "To measure the flux in the $uv$-plane we used `uvmcmcfit`" (4.2.2 uv-plane fit)
- **emcee** : posterior sampling  
  > "`uvmcmcfit` uses `EMCEE`" (4.2.2 uv-plane fit)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| rms A2744 | 55 | not stated | uJy/beam | 1 | / Abell 2744 / Natural / 0.63 / 0.49 / 86.14 / 55 / |
| rms MACSJ0416 | 59 | not stated | uJy/beam | 1 | / MACSJ0416 / Natural / 1.52 / 0.85 / -85.13 / 59 / |
| rms MACSJ1149 | 71 | not stated | uJy/beam | 1 | / MACSJ1149 / Natural / 1.22 / 1.08 / -43.46 / 71 / |
| number of detections S/N>=5 | 12 | not stated | sources | 2 | We detect 12 dusty star-forming galaxies at $S/N\geq5.0$ across the three clusters |
| A2744-ID01 uv-fit flux | 1.570 | 0.073 | mJy | 3 | / A2744-ID01 / $1.495 \pm 0.081$ / $1.545 \pm 0.081$ / 1.7 / 1.6 / $1.570\pm0.073$ / |
| A2744-ID02 uv-fit flux | 2.816 | 0.229 | mJy | 3 | / A2744-ID02 / $1.656 \pm 0.131$ / $3.262 \pm 0.213$ / 10.3 / 2.2 / $2.816\pm0.229$ / |
| size-flux regression slope m | -0.08 | 0.10 | dimensionless | 4 | The best-fit regression values are $m=-0.08\pm0.10$ and $b=-0.95\pm0.05$ |
| size-flux regression intercept b | -0.95 | 0.05 | dimensionless | 4 | The best-fit regression values are $m=-0.08\pm0.10$ and $b=-0.95\pm0.05$ |
| median offset Delta DEC (NIR-mm) | -0.13 | 0.02 | arcsec | 5 | $\Delta{\rm DEC}$$=$$-$0.13$''$$\pm$0.02$''$ |
| A2744-ID02 source-plane offset | 0.48 | 0.04 | arcsec | 5 | is $0.48\ensuremath{''}\pm0.04\ensuremath{''}$ including only the uncertainties |

## Qualitative findings

- None of the detected sources lie near caustics; magnifications mu~1.5-4.2  
  > "None of the sources fall close to the lensing caustics, thus they are not strongly lensed." (abstract)

## Claim tuples

- H: ALMA can detect sub-mJy DSFGs behind FF clusters with high purity | E: S/N>=5 detection in PB-uncorrected maps, simulations and counterpart matching | R: 12 detections, N<<1 false detections, all but one with NIR counterparts | F: Detections are reliable (purity ~1) | **supported**
- H: Sub-mJy DSFGs are more extended than brighter ones | E: Demagnified uv-plane sizes compared to brighter samples, regression | R: ~2/3 have r_s,demag >~0.16'' vs ~0.1'' average, but large dispersion; slope consistent with 0 | F: Sizes similar in range, possibly larger dispersion; larger samples needed | **partially**
- H: ALMA and HST emission are co-spatial | E: Centroid offsets between ALMA and F160W | R: scatter ~0.1'', A2744-ID02 offset ~4 kpc | F: Mostly co-spatial; ID02 is a notable offset case | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: uv-plane fitting recovers extended flux for marginally resolved sources  
  > "The code allows one to extract the maximum amount of information from the observations, particularly if the sources appear marginally resolved." (4.2.2 uv-plane fit)
- Alternative: Image-plane point-source and extended fits were measured but uv-fit adopted  
  > "Given these findings, we adopt the F$_{uv-fit}$ flux estimates for all sources." (4.2.2 uv-plane fit)
- How they decided it was enough: _not stated_
- Limitation (authors): Possible unaccounted systematics at 5-10% level; non-uniform sensitivity in two mosaics  
  > "we only caution that there may be unaccounted for systematic errors at the 5–10% level." (3.2 High-significance continuum detections)
- Caveat (inferred, ours): Redshift z=2 assumption for most sources affects magnification and demagnified sizes
- Caveat (inferred, ours): Small sample (12) limits size-distribution conclusions
- Caveat (inferred, ours): Lens model systematics not propagated in offsets

## Reproducibility

- Data public (paper): Continuum images, sensitivity maps and visibilities available on author website; ALMA archive project  
  > "The continuum images used in this paper, as well as the sensitivity maps and visibilities are available for download at this web address" (5 Summary)
- Products in archive: _not stated_
- Code: uvmcmcfit public on GitHub (third party); analysis scripts not stated  
  > "<https://github.com/sbussmann/uvmcmcfit>" (footnote)
- Missing: DBSCAN settings
- Missing: uvmcmcfit priors/walkers
- Missing: simobserve parameters
- Missing: exact lens model versions
- Data volume (inferred): ~100-300 GB raw for 18 executions of 126-pointing mosaics
- Score (inferred): 3/5, Public data and a fairly clear recipe, but several analysis parameters are unstated and manual reduction is needed.
- Rediscovery candidate: yes, Data are public, the recipe is mostly complete, and results are numeric (rms, fluxes, sizes).

## Links

- Method: Bussmann et al. 2013, 2015 (uvmcmcfit method and size reliability)
- Method: Coe et al. 2015 (magnification estimation)
- Companion: N. Laporte et al. 2016, in prep. (counterpart identification)
- Companion: J. González-López et al. 2016, in prep. (source-plane SED and morphology)
- Companion: A. Muñoz Arancibia et al. 2016, in prep. (number counts)
- Companion: R. Carvajal et al. 2016, in prep. (stacking analyses)
- Related: Frontier Fields
- Related: GLASS

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
  "facts": 86,
  "stated": 60,
  "rate": 0.698
 },
 "evidence_ok": true
}
```
