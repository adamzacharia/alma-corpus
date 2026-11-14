# An ALMA [C II] Survey of 27 Quasars at z &gt; 5.94

`2018ApJ...854...97D` | The Astrophysical Journal 2018 | first author: Decarli, Roberto | arXiv: 1801.02641 | DOI: 10.3847/1538-4357/aaa5aa

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: What are the [C II] line and FIR dust continuum properties (luminosity, width, size, dynamical mass) of a homogeneous sample of z>5.94 quasar host galaxies?  
  > "The size of the sample and the homogeneous data quality, together with the consistent analysis, allow us for the first time to study quasar host galaxies at the end of the reionization as a population." (Introduction)
- Target **27 quasars at z>5.94 (e.g. PJ167-13, J1306+0356, PJ009-10, J0142-3327)**: coordinates Listed per source in sample table (RA/Dec J2000)  
  > "PSO J007.0273+04.9571 | P007+04 | 00:28:06.560 | +04:57:25.68 | $6.00\pm   0.05$ | Template | 1 | -26.64" (Table 1); z/distance z=5.95-6.66 (pre-ALMA); [CII] redshifts in table  
  > "PSO J007.0273+04.9571 | P007+04 | 00:28:06.560 | +04:57:25.68 | $6.00\pm   0.05$ | Template | 1 | -26.64" (Table 1); distance from Pre-ALMA redshifts from Template/Lya/MgII/DLA; [CII] redshifts from ALMA spectral fits  
  > "PSO J007.0273+04.9571 | P007+04 | 00:28:06.560 | +04:57:25.68 | $6.00\pm   0.05$ | Template | 1 | -26.64" (Table 1)

## Data provenance

- ALMA projects: 2015.1.01115.S
- bands: Band 6 (~1.2 mm)  
  > "so that the [C ii] line falls in ALMA band 6 ($\sim 1.2$mm)" (2.1 The main sample)
- frequencies and spectral setup: SPWs 0 and 1 cover expected [C II] (~3.6 GHz total); SPWs 2 and 3 around rest 1790 GHz  
  > "The other two SPWs (2 and 3) covered rest-frame frequencies around 1790 GHz." (3 Observations); "This results in a frequency coverage of $\sim 3.6$ GHz around the expected observed frequency of the [C ii] line" (3 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: compact configuration, 38-49 12 m antennas  
  > "with the array in compact configuration with 38-49 12 m antennas" (3 Observations)
- baselines: _not stated_
- angular resolution: ~1.1'' x 0.8'' synthesized beam  
  > "The synthesized beam size is typically $\sim 1.1''\times 0.8''$." (3 Observations)
- max recoverable scale: _not stated_
- sensitivity: 0.5 mJy/beam per 30 km/s channel  
  > "The typical rms noise is 0.5 mJy beam$^{-1}$ per 30 km s$^{-1}$ channel." (3 Observations)
- time on source: ~8 min per target  
  > "short ($\sim8$ min on source) pointings" (3 Observations)
- observing dates: 2016 January to July  
  > "Observations were carried out between 2016 January and July" (3 Observations)
- pi or archival as stated: _not stated_
- Line: [C II] 2P3/2-2P1/2 158 um (1900.548 GHz)
- External data: [CII] luminosities, widths and continuum flux densities of 21 literature z>5.94 quasars (comparison sample)  
  > "For these sources, we will use the line luminosity and width, and the dust continuum flux density derived in the papers quoted above." (2.2 The sample from the literature) [from maiolino05; walter09; banados15; venemans12/16/17a/17c; willott13/15/17; wang13/16; mazzucchelli17]
- External data: Dust temperature 47 K and beta=1.6  
  > "The values of $T_{\rm dust}$ and $\beta$ assumed here are taken from (cite: beelen06)" (5.1) [from (cite: beelen06)]
- External data: Bolometric correction from 1450 A luminosity  
  > "following the conversion derived by (cite: runnoe12) and recomputed in (cite: venemans16)" (5.5) [from (cite: runnoe12); (cite: venemans16)]

## Processing

### Calibration

- pipeline or manual: CASA ALMA pipeline, default calibration procedure  
  > "We processed the data using the CASA (cite: mcmullin07) pipeline for ALMA (version 4.7.1), using the default calibration procedure." (3 Observations)
- casa version: CASA 4.7.1  
  > "pipeline for ALMA (version 4.7.1)" (3 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean, Briggs weighting  
  > "The cubes were imaged using Briggs cleaning (via the CASA task tclean) with robustness parameter = 2" (3 Observations)
- deconvolver: _not stated_
- weighting robust: robust = 2 (natural); re-imaged with robust = 0.5 for four resolved sources  
  > "robustness parameter = 2 (i.e., natural visibility weights) to maximize the signal-to-noise ratio" (3 Observations); "These are created after re-imaging the cubes using robustness parameter = 0.5" (5.4)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: box mask around each detected source; 2-sigma clean threshold from continuum rms  
  > "adopting a 2-$\sigma$ cleaning threshold based on the continuum estimate" (3 Observations)
- multiscale scales: _not stated_
- continuum subtraction: uv-plane subtraction of continuum from line-free channels  
  > "The pure–line map is obtained by subtracting (in uv-space) the continuum emission from the map created at step #5." (3 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: 30 km/s channels, linear interpolator  
  > "We adopt 30 km s$^{-1}$ channels with a linear interpolator in order to resample the cube in velocity space." (3 Observations)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Cosmology  
  > "we assume a standard $\Lambda$CDM cosmology with $H_0=70$ km s$^{-1}$ Mpc$^{-1}$, $\Omega_{\rm m}=0.3$ and $\Omega_{\Lambda}=0.7$ (cite: planck15)" (1 Introduction) [from (cite: planck15)]
- [CII]-based SFR calibration  
  > "Our [C ii]–based SFR estimates follow the fit to the [C ii]–SFR (24 $\mu$m–based) relation in 46 local galaxies from the KINGFISH sample" (5.3) [from (cite: herreracamus15)]
- IR-based SFR calibration  
  > "For the dust–based SFR estimates, we follow (cite: kennicutt12)" (5.3) [from (cite: kennicutt12)]
- Sigma_FIR approach  
  > "We follow here the analysis presented by (cite: diazsantos17)" (5.2) [from (cite: diazsantos17)]
- Rotating disk dynamical mass with i=55 deg and 0.75 FWHM factor  
  > "If we assume an inclination of $i=55^\circ$ (cite: willott15)" (5.4) [from (cite: willott15)]
- Continuum analysis deferred to companion paper  
  > "a companion paper (Venemans et al. in prep.) will analyze the underlying continuum emission from the same dataset" (1 Introduction) [from Venemans et al. in prep.]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges used for continuum maps
- Exact MCMC code, chain length, widths of Gaussian priors on flux
- Clean iteration limits and image size/cell size
- Flux calibrator and flux scale uncertainty
- Values of y (70/160 um ratio) assumed in the [CII]-SFR correction
- Exact box mask definitions and region for 2D fit
- Continuum flux density measurement method at 158 um and the continuum size fits (R_cont)

## Analysis recipe

1. **Calibrate and image cubes**: CASA pipeline calibration; tclean with natural weighting; 30 km/s channels; masked cleaning  
  > "The cubes were imaged using Briggs cleaning (via the CASA task tclean) with robustness parameter = 2" (3 Observations)
   - software: CASA
   - parameter: robust = 2; 2-sigma clean threshold; 30 km/s channels  
  > "adopting a 2-$\sigma$ cleaning threshold based on the continuum estimate" (3 Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit 1D spectra for line parameters**: Extract single-pixel spectrum at source; fit flat continuum + Gaussian  
  > "We fit the spectra assuming a flat continuum emission from the dust, plus a Gaussian for the [C ii] line." (4.1)
   - software: custom Metropolis MCMC
   - parameter: Detection if integrated flux exceeds 5 times lower-side uncertainty  
  > "We consider a line detected if its integrated flux exceeds 5 times its lower-side uncertainty." (4.1)
   - fitting: Metropolis MCMC; flat prior on peak frequency, Maxwellian (300 km/s) prior on width, broad Gaussian prior on line and continuum flux; median and 14-86% quantiles  
  > "We adopt a flat prior for the line peak frequency, a Maxwellian distribution with a line width of 300 km s$^{-1}$" (4.1)
   - validation: _not stated_
3. **Measure line flux and size in 2D**: Fit 2D Gaussian to continuum-subtracted line map in CASA, correct by 1/0.83 for line wings  
  > "In the following, we define a source’s [C ii] flux through the measurement via the 2D spatial Gaussian fit, and scaling by a fixed $1/0.83\times$ factor" (4.2)
   - software: CASA
   - parameter: line map collapsed over peak ±1.4 sigma_line  
  > "we collapse the data cube in the frequency range set by the line peak $\pm 1.4\,\sigma_{\rm line}$ from the best (spectral) fit" (3 Observations)
   - fitting: 2D Gaussian with free centroid, flux, deconvolved axes, PA, convolved with beam  
  > "The modeled emission is then convolved with the observed beam, when fitting to the data." (4.2)
   - validation: Compared 2D flux vs single-pixel flux  
  > "the more extended objects tend to deviate from the 1–to–1 relation" (4.2)
4. **Derive luminosities, FIR and EW**: L_[CII] formula; modified blackbody normalized at 158 um, integrated 3-1100 um; L_FIR=0.75 L_IR; EW from flux ratio  
  > "IR luminosities, $L_{\rm IR}$, are calculated by integrating equation [\[eq_mbb\]](#eq_mbb) between 3 and 1100 $\mu$m (rest frame" (5.1)
   - parameter: T_dust=47 K, beta=1.6, kappa=0.77 (nu/352 GHz)^beta cm^2/g  
  > "$\kappa_\nu(\beta)=0.77\,(\nu / {\rm 352\,GHz})^\beta$ cm$^2$ g$^{-1}$ is the opacity law" (5.1)
   - assumption: Single modified blackbody, T_dust=47 K, beta=1.6; Planck15 cosmology  
  > "where $T_{\rm dust}=47$ K is the dust temperature" (5.1)
   - fitting: _not stated_
   - validation: Single-component model underestimates IR luminosity by <15% versus templates  
  > "This effect however appears to be modest ($<15$%) once we compare the IR luminosities adopted here" (Footnote 3)
5. **Estimate SFRs and surface densities**: Herrera-Camus [CII]-SFR relation and Kennicutt&Evans IR-SFR relation; Sigma_FIR=L_FIR/(2 pi R_cont^2)  
  > "We compute $\Sigma_{\rm FIR}=L_{\rm FIR}\,(2 \pi R_{\rm cont}^2)^{-1}$ based on the 2D Gaussian fit size of the continuum map" (5.2)
   - assumption: T_dust=47 K  
  > "computed assuming $T_{\rm dust}=47$ K" (5.3)
   - fitting: _not stated_
   - validation: Adopting De Looze calibration gives comparable SFRs  
  > "Adopting the calibration by (cite: delooze14) results in comparable SFR estimates." (5.3)
6. **Dynamical masses and BH mass limits**: Disk formula M_dyn=G^-1 R (0.75 FWHM/sin i)^2 with i=55 deg; isothermal alternative; minimum M_BH from Eddington with L_bol from 1450 A  
  > "$$M_{\rm dyn}= G^{-1}\,R_{\rm [CII]}\,(0.75\,{\rm FWHM} /\sin i)^2.$$" (5.4)
   - assumption: inclination 55 deg; Eddington-limited accretion  
  > "If we assume an inclination of $i=55^\circ$ (cite: willott15)" (5.4)
   - fitting: _not stated_
   - validation: _not stated_
7. **Stack spectra**: Shift to rest frame, subtract continuum, inverse-variance weighted average of [CII]-detected sources; limits integrating ±400 km/s  
  > "After shifting all the observed spectra to the rest frame, we subtract the continuum (from the spectral fit), and average by weighting by the inverse of the variance" (5.6)
   - fitting: _not stated_
   - validation: Also stacked continuum-normalized spectra and width-scaled template  
  > "We also do not detect these lines if we stack the continuum–normalized spectra" (5.6)

## Software

- **CASA** 4.7.1: Pipeline calibration, tclean imaging, 2D Gaussian fits  
  > "pipeline for ALMA (version 4.7.1), using the default calibration procedure" (3 Observations)
- **custom Metropolis MCMC code** : Fitting line + continuum to spectra  
  > "We use a custom Metropolis Monte Carlo Markov Chain code to sample the posterior probability of the models" (4.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| [CII] detection rate (>5 sigma) | 23 of 27 (85%) | not stated | sources | 2 | The [C ii] line was significantly detected (at $>5$-$\sigma$) in 23 sources (85%). |
| Mean [CII] FWHM (this sample) | 385 | 115 (std dev) | km/s | 2 | The mean and standard deviations of the two distributions are $385\pm115$ km s$^{-1}$ and $350\pm125$ km s$^{-1}$ |
| Weighted mean velocity offset pre-ALMA redshift vs [CII] | -620 | 8 | km/s | 2 | is $-620\pm8$ km s$^{-1}$ |
| Host dynamical mass range | 2e10 to 2e11 | not stated | Msun | 6 | Basic estimates of the dynamical masses of the host galaxies give masses between $2\times10^{10}$ and $2\times10^{11}$ M$_\odot$ |
| Minimum BH mass range | (0.3-3)e9 | not stated | Msun | 6 | We derive lower limits on the black hole masses of $M_{\rm BH}^{\rm min}$=$(0.3-3)\times 10^9$ M$_\odot$. |
| [CII] luminosity range | 1e9 - 1e10 | not stated | Lsun | 4 | We find typical line luminosities of $L_{\rm [CII]}=10^{9-10}$ L$_\odot$ |
| Number of well-resolved sources | 4 | not stated | sources | 3 | Four quasar host galaxies are clearly resolved in their [C ii] emission on a few kpc scales. |
| BH-to-host mass ratio for high S/N sources | >0.03 | not stated | dimensionless | 6 | have a mass ratio of $>$0.03, i.e., $>$15 times higher than the value observed in the local universe |

## Qualitative findings

- Stacked [CII] spectrum shows no deviation from a single Gaussian, so strong outflow like J1148+5251 is not common  
  > "The strong outflow reported for an individual high–redshift quasar (cite: cicone15) thus does not appear to be a common feature of $z>6$ quasar hosts." (6)
- No Sigma_SFR approaches the Eddington limit (<100 Msun/yr/kpc2)  
  > "are always $<100$ M$_\odot$ yr$^{-1}$ kpc$^{-2}$" (5.3)

## Claim tuples

- H: Are [CII] and FIR emission common in z>6 quasar hosts? | E: 8 min ALMA snapshots of 27 quasars | R: 23/27 detected, L_[CII]=1e9-1e10 Lsun | F: Bright [CII] and dust are ubiquitous in z~6 quasar hosts | **supported**
- H: Are high-z quasar hosts undermassive relative to black holes compared to local relations? | E: Dynamical mass from [CII] size and width vs Eddington-based minimum BH mass | R: M_BH/M_dyn >0.03 for most high S/N sources | F: Mass ratio >15 times local | **supported**
- H: Do stacked [CII] profiles show broad non-Gaussian outflow components? | E: Inverse-variance stacking of detected sources | R: No deviation from Gaussian | F: Outflow wings not common | **supported**
- H: Does quasar UV luminosity correlate with [CII] properties? | E: Compare L_[CII], EW and [CII]/FIR against M1450 | R: Mild L_[CII] dependence driven by literature sample; EW independent | F: Weak or no correlation | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Natural weighting used to maximize S/N  
  > "to maximize the signal-to-noise ratio of our observations" (3 Observations)
- How they decided it was enough: _not stated_
- Limitation (authors): Low angular resolution means sizes are tentative and dynamical masses may be overestimated  
  > "suggesting that our [C ii] size estimates are only tentative" (4.2); "the dynamical mass estimates in some of the sources in our sample might be overestimated" (5.4)
- Caveat (inferred, ours): Sizes barely resolved, so M_dyn and Sigma values are weakly constrained
- Caveat (inferred, ours): Fixed T_dust=47 K assumed for all sources
- Caveat (inferred, ours): BH masses are Eddington lower limits, not measurements
- Caveat (inferred, ours): Unknown companions may contaminate flux and size

## Reproducibility

- Data public (paper): Program ID given; public status not explicitly stated  
  > "ALMA data: 2015.1.01115.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Custom MCMC code
- Missing: Line-free channel selection
- Missing: Flux calibrator details
- Missing: Image cell/size and clean limits
- Missing: Continuum sizes and fluxes are in companion paper
- Data volume (inferred): ~50-150 GB raw for 27 short compact-array execution blocks
- Score (inferred): 3/5, Data are single-project and procedures are mostly described, but the MCMC code and several imaging parameters are not given.
- Rediscovery candidate: no, Recipe is incomplete (custom MCMC, unspecified line-free channels, continuum sizes deferred to a companion paper).

## Links

- Method: (cite: decarli17) (Blind line search in the same cubes)
- Method: (cite: deblok14) (Dynamical mass from unresolved observations)
- Companion: Venemans et al. in prep. (Continuum analysis of the same dataset)
- Companion: (cite: decarli17) ([CII]-bright companions in four fields)
- Related: GOALS
- Related: KINGFISH

## Checks

```json
{
 "quotes": 72,
 "quotes_ok": 72,
 "quote_pass_rate": 1.0,
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
  "facts": 85,
  "stated": 54,
  "rate": 0.635
 },
 "evidence_ok": true
}
```
