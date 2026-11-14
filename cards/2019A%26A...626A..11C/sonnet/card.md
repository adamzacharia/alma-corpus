# ALMA survey of Class II protoplanetary disks in Corona Australis: a young region with low disk masses

`2019A&A...626A..11C` | Astronomy and Astrophysics 2019 | first author: Cazzoletti, P. | arXiv: 1904.02409 | DOI: 10.1051/0004-6361/201935273

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: How do the dust masses of Class II disks in Corona Australis compare with those in other star-forming regions, and why are they low?  
  > "We want to compare the general properties of disks and their host stars in the nearby ($d=160\,\rm pc$) Corona Australis (CrA) star forming region to those of the disks and stars in other regions." (abstract)
- Target **Corona Australis Class II YSOs (43 disks around 41 targets)**: coordinates Listed per source in the stellar properties table (e.g., CrA-1 18:56:39.76 -37:07:20.8)  
  > "For each object, the average distance of the cluster $d=154$ pc was used." (4.1 Dust masses); z/distance 154 pc  
  > "For each object, the average distance of the cluster $d=154$ pc was used." (4.1 Dust masses); distance from Dzib et al. 2018 average distance (cite: 2018ApJ...867..151D)  
  > "For each object, the average distance of the cluster $d=154$ pc was used." (4.1 Dust masses)

## Data provenance

- ALMA projects: 2015.1.01058.S
- bands: 1.3 mm (230 GHz)  
  > "We have carried out three executions of observations at 1.3 mm towards 43 Class II YSOs in the Corona Australis molecular cloud" (3.1 ALMA observations)
- frequencies and spectral setup: Six spectral windows; continuum windows 1875 MHz wide at 216.797 and 231.484 GHz  
  > "The spectral setup consists of six spectral windows, of which the (central frequency \[GHz\], total bandwidth \[MHz\], and frequency channel width \[kHz\]) are (216.797, 1875, 488)" (3.1 ALMA observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 14-1110 m  
  > "Project baseline lengths (min-max) \[m\] | 14-1108 | 15-1075 | 15-1110" (Table 1)
- angular resolution: 0.33" x 0.31" (PA 67 deg), ~50 au  
  > "the synthesized beam is $\theta_{\mbox{\scriptsize maj}}\times\theta_{\mbox{\scriptsize min}}$=0.33$''$$\times$0.31$''$ (P.A.=67$^{\circ}$)" (3.1 ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: ~0.15 mJy/beam rms  
  > "the achieved continuum root-mean-square (RMS) noise level is $\sim$0.15 mJy beam$^{-1}$" (3.1 ALMA observations)
- time on source: ~1 minute per source per epoch  
  > "Each one of the 43 target sources were integrated for approximately 1 minute in each epoch." (3.1 ALMA observations)
- observing dates: 2016 Aug 1-2  
  > "Time (UTC; 2016) | (Aug.01) 03:32-04:54 | (Aug.01) 05:01-06:23 | (Aug.02) 03:18-04:40" (Table 1)
- pi or archival as stated: PI H. B. Liu (co-author)  
  > "using ALMA (2015.1.01058.S, PI: H. B. Liu)" (3.1 ALMA observations)
- Line: 12CO, 13CO, C18O 2-1 (not stated)
- Line: SO, SiO 6-5, 5-4 (not stated)
- Other facility **VLT/X-Shooter**: New spectra for targets lacking spectral type  
  > "The spectroscopic follow-up observations for the 13 targets with missing spectral type information were carried out" (3.2 VLT/X-Shooter observations)
- Other facility **Spitzer (Peterson et al. catalogue)**: YSO catalogue, Class II selection and nominal positions  
  > "Our sample includes all the Class II sources from the (cite: peterson) catalogue." (2 Sample selection)
- External data: Mm fluxes/upper limits and dust masses of Lupus, Taurus, Cha I, Upper Sco, sigma Ori, IC348 for comparison  
  > "with the continuum fluxes (or the $3\,\sigma$ upper limits) from our ALMA data or from the literature" (4.3 Comparison with other regions) [from (cite: lupus); (cite: 2016ApJ...827..142B); (cite: 2017AJ....153..240A)]
- External data: Spectral types, extinctions, 2MASS J magnitudes from literature  
  > "The spectral type for the targets were obtained from the literature (see Tab. [\[tab:stellarprop\]](#tab:stellarprop)) or from the VLT/X-Shooter spectra." (4.1 Stellar properties) [from (cite: dunham); (cite: 2011ApJ...736..137S); (cite: 2003yCat.2246....0C)]
- Simulation/model as data: Evolutionary tracks of Baraffe et al. 2015 (M<1.4 Msun) and Siess et al. 2000 for stellar masses  
  > "using the evolutionary tracks by (cite: B15) for $M_\star<1.4 M_\odot$ and (cite: Siess00) for higher $M_\star$" (4.1 Stellar properties)

## Processing

### Calibration

- pipeline or manual: Manual calibration (first epoch special handling); other epochs standard QA2  
  > "The data were manually calibrated using the CASA v5.1.1 software package" (3.1 ALMA observations)
- casa version: CASA v5.1.1  
  > "The data were manually calibrated using the CASA v5.1.1 software package" (3.1 ALMA observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Pallas; bootstrapped J1924-2914 consistent with SMA calibrator list to ~10%  
  > "Absolute flux calibrator | Pallas | Pallas | Pallas" (Table 1); "consistent with the SMA Calibrator list" (3.1 ALMA observations)
- flux scale uncertainty: ~10%  
  > "not the 10% absolute flux calibration uncertainty." (4.2 footnote)
- self calibration: _not stated_

### Imaging

- task: CASA clean, multi-frequency synthesis, all three epochs jointly  
  > "The continuum data imaging was performed with multi-frequency synthesis (MFS) imaging of the continuum data using the CASA-`clean` task, and correcting for the primary beam." (3.1 ALMA observations)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub on line data  
  > "we fit the continuum baseline and subtract it from the spectral line data, using the CASA task `uvcontsub`" (3.1 ALMA observations)
- line free channels: _not stated_
- primary beam correction: Applied; needed because RA decimals were trimmed giving offsets up to 15" from phase center  
  > "this results in an offset of the sources of up to 15$^{\prime\prime}$ east of the phase center: as a consequence, our images had to be primary beam corrected." (3.1 ALMA observations)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.33" x 0.31", PA 67 deg  
  > "0.33$''$$\times$0.31$''$ (P.A.=67$^{\circ}$)" (3.1 ALMA observations)
- final rms: ~0.15 mJy/beam  
  > "$\sim$0.15 mJy beam$^{-1}$" (3.1 ALMA observations)

### Inherited from earlier work

- Dust mass method: kappa=10 cm2/g at 1000 GHz scaled with beta=1, T=20 K, same as Lupus survey  
  > "for the dust opacity $\kappa_\nu$ we follow the same approach of (cite: lupus), assuming $\kappa_\nu=10\,\rm cm^2\,g^{-1}$ at 1000 GHz" (4.3 Dust masses) [from (cite: lupus)]
- Bayesian linear regression (linmix) for Mdust-Mstar  
  > "We derive the $M_{\rm dust}-M_\star$ relation using the same linear-regression Bayesian approach followed by (cite: 2017AJ....153..240A) and presented by (cite: 2007ApJ...665.1489K)" (4.4 Mdisk-Mstar relation) [from (cite: 2017AJ....153..240A); (cite: 2007ApJ...665.1489K)]
- Monte Carlo stellar mass normalisation for comparison  
  > "we employ a Monte Carlo (MC) approach similar to that used by (cite: andrews2013)" (5.2 Is CrA young?) [from (cite: andrews2013)]
- Spectral-type indices from X-Shooter, as in earlier work  
  > "taken by those calibrated by (cite: riddick07), (cite: jeffries07), and (cite: 2014ApJ...786...97H), as in (cite: 2017A&A...604A.127M)" (4.1 Stellar properties) [from (cite: 2017A&A...604A.127M); (cite: manara13a)]

### Not stated but needed to reproduce (our reading)

- clean parameters: weighting/robust, deconvolver, threshold, mask, cell and image size
- line-free channels used for uvcontsub and which spectral windows form the continuum
- self-calibration (not stated whether done)
- Spectral-index thresholds and exact bins for stellar mass matching in MC test
- Number of linmix chains/iterations and priors
- Details of upper limit treatment (3 sigma value) for each non-detection
- Details of stacking procedure (weighting)

## Analysis recipe

1. **Calibrate and image continuum**: Manual CASA calibration; joint MFS clean imaging of three epochs with primary beam correction  
  > "By jointly imaging all three epochs of data, for each target source field, the achieved continuum root-mean-square (RMS) noise level is $\sim$0.15 mJy beam$^{-1}$" (3.1 ALMA observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Flux consistent with SMA calibrator list to ~10%  
  > "consistent with the SMA Calibrator list" (3.1 ALMA observations)
2. **Measure continuum fluxes and noise**: Gaussian fit in the image plane (two Gaussians for binaries); rms by imstat  
  > "a Gaussian is therefore fitted to the detected sources (two Gaussians for the binaries) in the image plane using the `imfit` task in `CASA`" (4.2 mm continuum emission)
   - software: CASA imfit, CASA imstat
   - parameter: Detection threshold >=4 sigma within 1" of Spitzer position; rms for non-detections within 1" radius, for detections in 2"-4" annulus  
  > "show a clear ($\geq4\sigma$) detection within a $1^{\prime\prime}$ radius from the nominal *Spitzer* location" (4.2 mm continuum emission)
   - fitting: _not stated_
   - validation: _not stated_
3. **Stack non-detections**: Images centered on Spitzer coordinates and stacked  
  > "The images were centered at their *Spitzer* coordinates (Table [\[tab:stellarprop\]](#tab:stellarprop)) and then stacked." (4.2 mm continuum emission)
   - software: CASA
   - assumption: unresolved disks  
  > "a $3\sigma$ upper limit of $0.051\,\rm mJy$ is found assuming unresolved disks" (4.2 mm continuum emission)
   - fitting: _not stated_
   - validation: Caveat: positional offset may cause sources not to overlap  
  > "it is therefore possible that the undetected sources did not overlap during the stacking" (4.2 mm continuum emission)
4. **Derive stellar properties**: Spectral types from X-Shooter indices; Teff, L from J-band and BC; masses from tracks  
  > "Stellar luminosity ($L_\star$) is obtained from the reddening-corrected $J$-band magnitudes and using the bolometric correction from (cite: 2014ApJ...786...97H)" (4.1 Stellar properties)
   - software: ESO X-Shooter pipeline, IRAF
   - assumption: Cardelli reddening law, R_V=3.1; distance 154 pc  
  > "the reddening law by (cite: cardelli) with $R_V$=3.1" (4.1 Stellar properties)
   - fitting: _not stated_
   - validation: Extinctions compared with Sicilia-Aguilar et al. 2011 for 8 common targets  
  > "We found that the extinctions derived with the two methods are consistent within the uncertainties." (Additional stellar properties)
5. **Convert fluxes to dust masses**: Optically thin isothermal relation M=F d^2/(kappa B(T))  
  > "Assuming that the observed sub-millimeter emission is optically thin and isothermal" (4.3 Dust masses)
   - parameter: kappa=2.3 cm2/g at 230 GHz; T_dust=20 K; d=154 pc  
  > "The adopted value is therefore $\kappa_\nu=2.3\,\rm cm^2\,g^{-1}$ at $\nu=230\,\rm GHz$ (1.3 mm)." (4.3 Dust masses)
   - assumption: _not stated_
   - fitting: _not stated_
   - validation: _not stated_
6. **Compare average dust masses across regions**: Kaplan-Meier estimator for left-censored data  
  > "The Kaplan-Meier estimator from the `lifelines`[^3] and ` ASURV` (cite: 1992ASPC...25..245L) packages were then used to estimate the cumulative mass distribution" (4.3 Comparison with other regions)
   - software: lifelines, ASURV
   - parameter: Only stars with M*>=0.1 Msun included  
  > "we only include the disks around stars with masses above the brown-dwarf limit ($M_\star\geq0.1\,\rm M_\odot$)" (4.3 Comparison with other regions)
   - fitting: _not stated_
   - validation: _not stated_
7. **Fit Mdust-Mstar relation**: Bayesian linear regression with censoring (linmix), 100 random draws for missing stellar masses; T CrA and TY CrA excluded  
  > "This uncertainty is also taken into account in the Bayesian approach we adopt by performing 100 different draws." (4.4 Mdisk-Mstar relation)
   - software: linmix
   - parameter: 20% uncertainty on M*  
  > "a standard uncertainty of 20% of $M_\star$ on the stellar mass is assumed" (4.4 Mdisk-Mstar relation)
   - fitting: _not stated_
   - validation: Fit without random draws gives consistent results  
  > "we also run the fit described above without any random draw, finding consistent results." (4.4 Mdisk-Mstar relation)
8. **Test stellar-mass effect via Monte Carlo logrank**: Draw equal numbers per stellar mass bin from CrA and comparison sample, two-sample logrank test for censored data, 10^4 repetitions  
  > "We then perform a two-sample logrank test for censored datasets between the disk dust masses of the two samples" (5.2 Is CrA young?)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.1.1: Calibration, uvcontsub, clean imaging, imfit, imstat  
  > "The data were manually calibrated using the CASA v5.1.1 software package" (3.1 ALMA observations)
- **ESO X-Shooter pipeline** 2.9.3: Reduction of X-Shooter spectra  
  > "The reduction of the data was performed using the ESO X-Shooter pipeline 2.9.3" (3.2 VLT/X-Shooter observations)
- **IRAF** : 1D spectrum extraction  
  > "We extracted the 1D spectra from the 2D images produced by the pipeline using IRAF" (3.2 VLT/X-Shooter observations)
- **lifelines** : Kaplan-Meier estimation  
  > "The Kaplan-Meier estimator from the `lifelines`[^3] and ` ASURV`" (4.3 Comparison with other regions)
- **ASURV** : Survival analysis with upper limits  
  > "The Kaplan-Meier estimator from the `lifelines`[^3] and ` ASURV`" (4.3 Comparison with other regions)
- **linmix** : Bayesian linear regression for Mdust-Mstar  
  > "presented by (cite: 2007ApJ...665.1489K)[^4]" (4.4 Mdisk-Mstar relation)
- **matplotlib** : Figures  
  > "All the figures were generated with the `python`-based package `matplotlib`" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of detected disks | 24 of 43 | not stated | disks | 2 | The total number of detections is therefore 24 out of the 43 targeted disks, so the detection rate is $\sim56\%$ . |
| Average dust mass of CrA disks (Kaplan-Meier) | 6 | ±3 | M_earth | 6 | With an average dust mass of $6\pm3 \rm\, M_\oplus$ |
| Stacked non-detection rms | 0.017 | not stated | mJy/beam | 3 | an average rms noise is $0.017\,\rm mJy\,beam^{-1}$, corresponding to a $3\sigma$ upper limit of $0.051\,\rm mJy$ |
| Stacked 3 sigma dust mass upper limit | 0.036 | not stated | M_earth | 5 | The stacking of the non-detections gives an average $3\sigma$ upper limit corresponding to $0.036\,\rm M_\oplus$ |
| Mdust-Mstar slope | 2.32 | ±0.77 | dimensionless | 7 | the best-fit model has a slope $\beta=2.32\pm0.77$ and intercept $\alpha=1.29\pm0.60$ |
| Mdust-Mstar intercept | 1.29 | ±0.60 | dimensionless | 7 | the best-fit model has a slope $\beta=2.32\pm0.77$ and intercept $\alpha=1.29\pm0.60$ |
| Median logrank p value vs Upper Sco | 0.53 | not stated | dimensionless | 8 | we find a median $p_\phi$ value of 0.53, while the median $p_\phi$ for Lupus is only 0.004 |
| Median logrank p value vs Lupus | 0.004 | not stated | dimensionless | 8 | we find a median $p_\phi$ value of 0.53, while the median $p_\phi$ for Lupus is only 0.004 |
| CrA-45 E 1.3 mm flux | 29.82 | ±0.35 | mJy | 2 | CrA-45 E / -0.36 / 0.63 / $29.82  \pm   0.35$ |

## Qualitative findings

- No disk shows clear substructures or cavities >25 au; disks unresolved or marginally resolved  
  > "None of the disks show clear substructures, no transition disk with cavities with radius $>25\,\rm au$ are found" (4.2 mm continuum emission)
- HR diagram suggests CrA age similar to Lupus rather than Upper Sco  
  > "the HR diagram supports the scenario of a young CrA cluster with an age more consistent to that of Lupus than to Upper Sco." (5.1 Is CrA old?)

## Claim tuples

- H: CrA disks have dust masses comparable to other 1-3 Myr regions | E: Mm survey of 43 disks, Kaplan-Meier average with upper limits, compared to other regions | R: Average 6±3 Mearth vs 14±3 (Lupus), 13±2 (Taurus), 24±9 (Cha I); similar to Upper Sco 5±3 | F: CrA disk masses are significantly lower than in similarly young regions | **supported**
- H: Low masses are due to an older population | E: Placed stars on HR diagram vs Lupus and Upper Sco | R: CrA median luminosities follow younger isochrones | F: CrA appears young, coeval with Lupus | **partially**
- H: Low masses are explained by external photoevaporation or low stellar masses | E: No correlation with distance from R CrA, FUV estimate, MC logrank test normalised in stellar mass | R: FUV ~1 G0; p=0.004 vs Lupus | F: Neither explains the low masses | **supported**
- H: Mdust-Mstar correlation holds in CrA | E: Bayesian regression with upper limits | R: slope 2.32±0.77, intercept 1.29±0.60, lower intercept | F: Correlation present with lower intercept; slope poorly constrained | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Single opacity and temperature adopted for uniform comparison with other surveys  
  > "to facilitate the comparison with other star-forming regions" (4.3 Dust masses)
- Alternative: T_dust = 25 K (L*/Lsun)^0.25 relation not used  
  > "rather than the $T_{\rm dust}=25{\,\rm K}\times(L_{*}/L_\odot)^{0.25}$ relation" (4.3 Dust masses)
- How they decided it was enough: _not stated_
- Limitation (authors): Dust possibly hidden by high optical depth in inner disk  
  > "it is still possible that a similar amount of dust mass is hidden at the inner few region due to very high optical depth" (4.3 Dust masses)
- Limitation (authors): Stacking upper limit may be underestimated due to position offsets  
  > "the upper limit is actually higher than that quoted" (4.2 mm continuum emission)
- Caveat (inferred, ours): Flux errors exclude the 10% absolute calibration
- Caveat (inferred, ours): Uniform T=20 K and kappa ignore stellar luminosity dependence, optically thick disks
- Caveat (inferred, ours): Spectral types missing for several sources; stellar masses randomly drawn
- Caveat (inferred, ours): Interpretation of initial conditions is speculative and untested
- Caveat (inferred, ours): Small, low-number sample limits slope constraint

## Reproducibility

- Data public (paper): Data cited by ALMA project code; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.01058.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: clean imaging parameters
- Missing: Table of stellar masses assumed for the comparison samples
- Missing: Exact literature fluxes used for other regions
- Missing: linmix settings
- Data volume (inferred): ~20-50 GB raw (3 short executions, 43 fields); not stated in paper
- Score (inferred): 3/5, Simple measurements and public project code, but imaging parameters and comparison-sample inputs not given.
- Rediscovery candidate: yes, Data are from a single ALMA project, the recipe (flux fit, dust mass formula, Kaplan-Meier) is simple and results are numeric.

## Links

- Method: (cite: lupus) (Dust mass and survey methodology followed)
- Method: (cite: 2017AJ....153..240A) (Bayesian regression approach)
- Method: (cite: 2007ApJ...665.1489K) (linmix regression method)
- Companion: (cite: peterson) (Source catalogue of Class II YSOs in CrA)
- Related: ALMA Lupus survey
- Related: Upper Sco survey (Barenfeld et al. 2016)
- Related: sigma Orionis survey
- Related: Gould Belt Spitzer Legacy program

## Checks

```json
{
 "quotes": 80,
 "quotes_ok": 80,
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
  "facts": 95,
  "stated": 62,
  "rate": 0.653
 },
 "evidence_ok": true
}
```
