# Measuring Dust Masses of Protoplanetary Disks in Serpens and L1641/L1647 with ALMA

`2025ApJ...995...16Z` | The Astrophysical Journal 2025 | first author: Zamudio-Ruvalcaba, Luisa F. | arXiv: 2511.20817 | DOI: 10.3847/1538-4357/ae1588

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type archival_reuse

## Science

- Fields: protoplanetary_disks, star_formation
- Question: Measure dust masses of 178 T Tauri disks in Serpens and L1641/L1647 with SED modeling and compare with optically thin millimeter-flux masses  
  > "We analyze 178 T-Tauri stars, 18 in Serpens and 160 in L1641/L1647, and measure their disk dust masses using spectral energy distribution (SED) modeling and multiwavelength data, including 1.3 mm (ALMA band 6) fluxes from the literature." (abstract)
- Target **Serpens sample (18 modeled T Tauri disks)**: coordinates _not stated_; z/distance per-source Gaia DR3 parallaxes (Table 1)  
  > "We use ALMA 1.3 mm continuum observations from the Serpens star-forming region" (1 Introduction); "distances derived from parallaxes" (3.2.1 The model); distance from Gaia DR3 parallaxes  
  > "We use ALMA 1.3 mm continuum observations from the Serpens star-forming region" (1 Introduction); "distances derived from parallaxes" (3.2.1 The model)
- Target **L1641/L1647 sample (160 modeled T Tauri disks, Orion A)**: coordinates _not stated_; z/distance per-source Gaia DR3 parallaxes  
  > "the Orion A cloud in the L1641 and L1647 regions" (1 Introduction); distance from Gaia DR3 parallaxes  
  > "the Orion A cloud in the L1641 and L1647 regions" (1 Introduction)

## Data provenance

- ALMA projects: 2019.1.00218.S, 2019.1.01813.S
- bands: Band 6 (1.3 mm)  
  > "including 1.3 mm (ALMA band 6) fluxes from the literature" (abstract)
- frequencies and spectral setup: 1.3 mm band centered at 241.1 GHz (Serpens) and 225 GHz (L1641/L1647)  
  > "use the ALMA 1.3 mm band (centered at 241.1 GHz and 225 GHz, respectively)" (2 Sample selection)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: ALMA 1.3 mm fluxes taken from published surveys (Anderson et al. 2022; van Terwisga et al. 2022); no data reduction done here  
  > "including 1.3 mm (ALMA band 6) fluxes from the literature" (abstract)
- Other facility **Spitzer IRS (CASSIS)**: low-resolution mid-IR spectra used in the SED fits  
  > "Infrared Spectrograph (IRS) spectra from CASSIS" (1 Introduction)
- Other facility **VizieR multiwavelength photometry (including 2MASS, WISE/c2d)**: broad-band photometry compiled for each SED  
  > "We compile the SEDs using multiwavelength photometry gathered for each object from the Vizier catalog access tool" (3.1 SEDs)
- Other facility **Gaia DR3**: parallaxes (distances) and, for some sources, Teff and Av from GSP-Phot  
  > "derived values from GSP-Phot using BP/RP spectra" (Table 1 notes)
- External data: ALMA 1.3 mm continuum fluxes for Serpens and L1641/L1647 disks  
  > "including 1.3 mm (ALMA band 6) fluxes from the literature" (abstract) [from Anderson et al. 2022 (cite: 2022Anderson); van Terwisga et al. 2022 (cite: 2022vanTerwisga)]
- External data: Stellar parameters (spectral type, Teff, Av, L*, M*, R*) used as priors  
  > "Additional parameters are obtained from various sources as follows" (Table 1 notes); "These are all parameters later used as priors for the ANN." (A Sample selection criteria) [from Oliveira et al. 2009, 2013; Erickson et al. 2015 and others for Serpens; Fang, Hsu, Da Rio, Kounkel, Kim, Yao and others for L1641/L1647]
- External data: SED model results for 41 L1641 sources  
  > "we incorporate their model results here" (3 Analysis and Results) [from Rilinger et al. 2023 (cite: 2023Rilinger)]
- External data: SED-model dust masses and flux-based masses for 10 other star-forming regions used for comparison  
  > "Here, we compare the results obtained for Serpens and L1641/L1647 with the 10 other star-forming regions studied in (cite: 2023Rilinger)." (4.2 Comparison of Serpens & L1641/L1647 with other Star-Forming Regions) [from Rilinger et al. 2023 (cite: 2023Rilinger)]
- External data: Masses of confirmed exoplanets  
  > "The masses of presently known and confirmed exoplanets were gathered from the" (4.3 The missing mass problem) [from NASA Exoplanet Archive]
- Simulation/model as data: D'Alessio Irradiated Accretion Disk (DIAD) models, emulated by an ANN trained on them (Ribas et al. 2020)  
  > "the ANN takes a few milliseconds to evaluate the SEDs, compared to the 1-2 hours that the DIAD models require" (3.2.1 The model)

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

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- SED model: ANN trained on DIAD models, model description and steps  
  > "We direct the reader to Section 4 and Figure 2 of (cite: 2020Ribas) for a detailed description of the model" (3.2.1 The model) [from (cite: 2020Ribas)]
- Bayesian approach for posterior estimation  
  > "We follow a Bayesian approach as detailed in (cite: 2020Ribas) and (cite: 2023Xin)" (3.2 SED modeling) [from (cite: 2020Ribas); (cite: 2023Xin)]
- Likelihood functions  
  > "Following (cite: 2023Rilinger), we adopted the likelihood functions from (cite: 2020Ribas) and (cite: 2023Xin)" (3.2.2 Markov Chain Monte Carlo (MCMC)) [from (cite: 2023Rilinger); (cite: 2020Ribas); (cite: 2023Xin)]
- Mixture-model treatment of outlier photometry and scaling of uncertainties by parameter f  
  > "(cite: 2023Xin) employed a mixture model approach, following the methodology described by (cite: 2010Hogg)." (3.2.2 Markov Chain Monte Carlo (MCMC)) [from (cite: 2023Xin); (cite: 2010Hogg)]
- Minimum Teff uncertainty of 100 K  
  > "we adopted an uncertainty of 100 K for those objects with reported uncertainties below 100 K, following (cite: 2020Ribas)" (2 Sample selection) [from (cite: 2020Ribas)]
- L* and M* estimation with the MassAge code  
  > "estimated here using the MassAge code following (cite: 2023Hernandez)" (Table 1 notes) [from (cite: 2023Hernandez)]
- Extinction law applied to model SEDs  
  > "applying the (cite: 2009McClure) extinction law (cite: 2017Ribas)" (3.2.1 The model) [from (cite: 2009McClure); (cite: 2017Ribas)]
- Dust opacity law used for flux-based masses  
  > "we adopt $\kappa_{\nu} = (\nu/100$ GHz) (cite: 1990Bekwith) resulting in $2.41\ cm^2g^{-1}$ while assuming $\beta = 1$" (4.1 The importance of optical depth when deriving disk masses) [from following (cite: 2022Anderson)]
- Flux-weighted mean optical depth methodology  
  > "Following the same methodology detailed in (cite: 2023Xin), we used the median values obtained from the ANN as input parameters" (4.1 The importance of optical depth when deriving disk masses) [from (cite: 2023Xin)]
- Exoplanet-systems CDF selection (systems with at least one planet above 0.3 M_Jup)  
  > "Following the methodology detailed in (cite: 2020Tychoniec), we restrict our sample to only systems containing at least one planet with a total mass" (4.3 The missing mass problem) [from (cite: 2020Tychoniec)]

### Not stated but needed to reproduce (our reading)

- The ANN weights and code of Ribas et al. 2020 and the DIAD model grid ranges are needed but only referenced, not given here
- MCMC settings for ptemcee (walkers, temperatures, steps, burn-in, convergence test) are not stated
- Prior ranges for all flat priors and the exact scale of the Gaussian priors beyond centre/width are not stated
- The ALMA 1.3 mm flux values and uncertainties per source are not tabulated in this paper; they must be taken from the cited surveys
- The list of photometric catalogs per source is only in a table not included in the text; flux and error handling per catalog is not stated
- Criteria used to judge a fit successful or unsuccessful are qualitative and not defined
- Which 10% of the L1641/L1647 sample is plotted in the optical-depth figure is not stated
- How the 7 mm optical depths were computed (same procedure as 1.3 mm at a different wavelength) is only implied

## Analysis recipe

1. **select the disk sample from ALMA 1.3 mm surveys**: Apply a series of cuts (Class II, ALMA detection, photometry coverage, no TD/flat/binary, Gaia astrometric quality, T Tauri mass range, literature stellar parameters) to the Serpens and L1641/L1647 survey samples  
  > "The original sample of 320 Serpens sources (cite: 2022Anderson) comes down to 23 objects, and the 873 L1641/L1647 sources (cite: 2022vanTerwisga) to 188 objects after considering several criteria." (2 Sample selection)
   - parameter: ALMA detections of at least 3 sigma  
  > "Only sources with ALMA detections of at least 3$\sigma$ were included." (2 Sample selection)
   - parameter: parallax error below 20% and RUWE < 1.4  
  > "We apply two criteria for good astrometric fits: a parallax error below 20$\%$, and a RUWE $<$1.4." (A Sample selection criteria)
   - fitting: _not stated_
   - validation: _not stated_
2. **compile multiwavelength SEDs**: Gather photometry from VizieR with a 2 arcsec search radius and add Spitzer IRS spectra from CASSIS where available  
  > "We compile the SEDs using multiwavelength photometry gathered for each object from the Vizier catalog access tool (cite: 2000Vizier), using a search radius of 2" (3.1 SEDs)
   - software: VizieR, CASSIS
   - fitting: _not stated_
   - validation: _not stated_
3. **fit SEDs with ANN-based DIAD models using MCMC**: Bayesian MCMC fit with an ANN emulating DIAD disk models; parallel-tempering ptemcee sampler  
  > "We implement a Bayesian analysis framework as a Markov Chain Monte Carlo (MCMC) fitting process to probe the large parameter space and estimate posterior distributions for the model parameters." (3.2.2 Markov Chain Monte Carlo (MCMC))
   - software: ptemcee, emcee, ANN of Ribas et al. 2020, DIAD, MIST
   - parameter: 17 free parameters in total (13 model parameters plus 4 outlier/systematic-uncertainty parameters)  
  > "This results in a total of 17 free parameters, which are varied during the fitting to compute posterior probability distributions." (3.2.2 Markov Chain Monte Carlo (MCMC))
   - parameter: photometry split into critical (2MASS and ALMA) and general (all other) groups  
  > "critical: includes 2MASS and ALMA photometry" (3.2.2 Markov Chain Monte Carlo (MCMC))
   - parameter: Gaussian priors on M* and parallax centred on literature values; flat priors where literature values are absent  
  > "using their values as the centers and their uncertainties as the standard deviations, while flat priors are used when literature values are absent (e.g., inclination)." (3.2.2 Markov Chain Monte Carlo (MCMC))
   - assumption: Dust composition and gas-to-dust ratio fixed; disk substructures not modeled  
  > "Some physical properties remain fixed (e.g. dust composition, gas-to-dust ratio) or not considered in the modeling" (3.2.1 The model)
   - fitting: Gaussian likelihoods for critical photometry, IRS spectra, T* and R*; mixture model for general photometry; ptemcee sampler; Gaussian and flat priors  
  > "Four standard Gaussian likelihood functions are used, each for the critical photometry data, the spectral data (i.e., IRS Spectra)" (3.2.2 Markov Chain Monte Carlo (MCMC))
   - validation: _not stated_
4. **reject poorly fitted sources**: Visual judgement of model fits reduces 211 sources to 178 (18 Serpens, 160 L1641/L1647)  
  > "We end with the resulting model fits and further reduce our sample to 178 sources (18 from Serpens and 160 from L1641/L1647) based on the quality of the fits." (3 Analysis and Results)
   - fitting: _not stated_
   - validation: _not stated_
5. **check posteriors against literature stellar parameters**: Compare M*, R*, parallax and Teff posteriors with the literature values used as priors  
  > "is conducted to validate the robustness of the ANN fitting methodology" (3.3 Model results)
   - fitting: _not stated_
   - validation: Posteriors consistent with literature stellar parameters  
  > "are in general consistent with literature measurements" (B Priors vs Posteriors)
6. **recompute flux-based dust masses**: Optically thin Hildebrand equation applied to the literature 1.3 mm fluxes with Gaia DR3 distances  
  > "is the Planck function evaluated at the dust temperature" (4.1 The importance of optical depth when deriving disk masses)
   - parameter: Td = 20 K constant, flux at 1.3 mm (241 GHz), kappa = 2.41 cm^2 g^-1 with beta = 1  
  > "which is typically assumed to be constant with a value of $T_d = 20\ K$ for a Class II object" (4.1 The importance of optical depth when deriving disk masses)
   - assumption: Optically thin emission at the observing frequency  
  > "Equation [\[eq: Hildebrand\]](#eq: Hildebrand) assumes that the disk emission is optically thin at the reference frequency" (4.1 The importance of optical depth when deriving disk masses)
   - fitting: _not stated_
   - validation: _not stated_
7. **compare SED-model masses with flux-based masses**: Compute the ratio M_dust,DIAD / M_dust,lit per source and across 12 regions  
  > "We find that, on average, our masses are a factor of about 2.0 higher for both Serpens and L1641/L1647." (4.1 The importance of optical depth when deriving disk masses)
   - fitting: _not stated_
   - validation: _not stated_
8. **compute optical depth at 1.3 mm and 7 mm**: Generate DIAD models from ANN median parameters, compute line-of-sight optical depth versus radius at 225 GHz, and take the flux-weighted mean; repeat at 7 mm  
  > "This is followed by computing a flux-weighted mean optical depth where the flux at each radius is used as the weight for the optical depth corresponding to that radius." (4.1 The importance of optical depth when deriving disk masses); "we calculate the optical depth at a longer reference wavelength of 7mm corresponding to ALMA band 1 for Serpens and L1641/L1647" (4.3 The missing mass problem)
   - software: DIAD
   - parameter: 225 GHz (1.3 mm) and 7 mm  
  > "as a function of the radius at 225 GHz (1.3 mm)" (4.1 The importance of optical depth when deriving disk masses)
   - fitting: _not stated_
   - validation: _not stated_
9. **compare with other regions and exoplanet masses**: Compare dust-mass distributions with 10 regions from Rilinger et al. 2023 and build cumulative distributions against confirmed exoplanet masses  
  > "amounting to a sample of 3401 exoplanets with known masses and respective errors" (4.3 The missing mass problem)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **ptemcee** : parallel-tempering MCMC sampling  
  > "the `ptemcee` (cite: 2016Vousden) parallel-tempering version of the `emcee` MCMC code (cite: 2013Foreman-Mackey)" (3.2.2 Markov Chain Monte Carlo (MCMC))
- **emcee** : MCMC code that ptemcee extends  
  > "the `ptemcee` (cite: 2016Vousden) parallel-tempering version of the `emcee` MCMC code (cite: 2013Foreman-Mackey)" (3.2.2 Markov Chain Monte Carlo (MCMC))
- **MassAge** : estimating L* and M* from literature data  
  > "estimated here using the MassAge code following (cite: 2023Hernandez)" (Table 1 notes)
- **MIST** : evolutionary models used to derive M*  
  > "is derived using the MIST (cite: 2016Dotter) evolutionary models" (Table 1 notes)
- **DIAD (D'Alessio Irradiated Accretion Disk code)** : disk models underlying the ANN and optical-depth calculation  
  > "This paper utilizes the D" (Acknowledgments)
- **TOPCAT** : interactive viewer and editor for tabular data  
  > "interactive graphical viewer and editor for tabular data TOPCAT" (Acknowledgments)
- **AstroPy** : _not stated_
- **NumPy** : _not stated_
- **SciPy** : _not stated_
- **lifelines** : _not stated_
- **matplotlib** : _not stated_
- **pandas** : _not stated_

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Final modeled sample size | 178 (18 Serpens, 160 L1641/L1647) | not stated | disks | 4 | 18 in Serpens and 160 in L1641/L1647 |
| Sample before fit-quality cut | 211 | not stated | sources | 1 | This results in an overall sample of 211 objects. |
| Average ratio of SED-model dust mass to flux-based mass (Serpens and L1641/L1647) | about 2.0 | not stated | dimensionless | 7 | We find that, on average, our masses are a factor of about 2.0 higher for both Serpens and L1641/L1647. |
| Median discrepancy factor M_dust,DIAD / M_dust,lit over all 12 regions | ~1.74 | not stated | dimensionless | 7 | has a median of $\sim$1.74 for all regions and shows a slight increase toward the most massive disks |
| Discrepancy factor for Taurus and Upper Sco | Taurus 4.09 (largest); Upper Sco 0.72 (lowest) | not stated | dimensionless | 7 | Taurus has the biggest discrepancy factor (4.09), and Upper Sco has the lowest (0.72). |
| Median disk dust mass, Serpens | ~55.3 | not stated | M_earth | 3 | median disk dust mass is $\sim$55.3 $M_{\oplus}$, and L1641/L1647 |
| Median disk dust mass, L1641/L1647 | ~17.9 | not stated | M_earth | 3 | median disk dust mass is $\sim$17.9 $M_{\oplus}$; whereas the median for all 12 star-forming regions is $\sim$9.28 $M_{\oplus}$ |
| Median disk dust mass over all 12 star-forming regions | ~9.28 | not stated | M_earth | 9 | median disk dust mass is $\sim$17.9 $M_{\oplus}$; whereas the median for all 12 star-forming regions is $\sim$9.28 $M_{\oplus}$ |
| L1641/L1647 sources discarded for failed fits | 28 | not stated | sources | 4 | For the L1641/L1647 region, 28 sources were discarded based on failed fits. |
| Exoplanets with known masses used for the CDF | 3401 | not stated | exoplanets | 9 | amounting to a sample of 3401 exoplanets with known masses and respective errors |

## Qualitative findings

- Dust settling parameter epsilon prefers low values in both samples, indicating significant settling  
  > "shows a preference towards lower values in both samples (i.e., $\epsilon < 10^{-2}$)" (3.3 Model results)
- R_disk and a_max,midplane are not well constrained  
  > "are not well constrained, consistent with the results of (cite: 2020Ribas) and (cite: 2023Xin), which use the same method" (3.3 Model results)
- Higher mass discrepancy factors are caused by high optical depths, driven by high dust masses and small disk sizes  
  > "Panel (c) clearly demonstrates that higher disk dust mass discrepancy factors are caused by high optical depths." (4.1 The importance of optical depth when deriving disk masses)
- Most disks are optically thick at 1.3 mm and the vast majority are optically thin at 7 mm  
  > "found that most disks are optically thick at 1.3mm while the vast majority are optically thin at 7 mm" (5 Summary)

## Claim tuples

- H: SED-model dust masses differ from optically thin millimeter-flux masses | E: Fit ANN-DIAD SED models to 178 disks and recompute flux-based masses with the Hildebrand equation | R: SED-model masses are on average about a factor 2.0 higher | F: Flux-based masses underestimate disk dust mass because many disks are optically thick at 1.3 mm | **supported**
- H: The mass discrepancy is driven by optical depth | E: Compute flux-weighted mean optical depth at 1.3 mm and compare with dust mass, disk size and discrepancy factor | R: Mean optical depth rises with dust mass and falls with disk size and correlates with the discrepancy factor | F: High optical depth at (sub-)mm wavelengths causes the underestimates | **supported**
- H: Longer wavelengths trace dust mass better | E: Compute optical depth at 7 mm (ALMA band 1) for the same disks | R: The vast majority of objects become optically thin at 7 mm | F: Observations at band 3 and band 1 are essential to measure disk dust masses | **supported**
- H: Serpens and L1641/L1647 follow the dust mass versus age trend of other regions | E: Compare dust mass distributions with 10 other regions from Rilinger et al. 2023 | R: Younger regions have higher median dust mass than older ones | F: Both samples follow the observed relation between dust mass and age | **supported**
- H: Correcting for optical depth resolves the missing mass problem | E: Compare cumulative distributions of SED-model and flux-based dust masses with confirmed exoplanet masses | R: Dust masses remain lower than exoplanet system masses at the high-mass end | F: The missing mass problem persists and likely has multiple causes | **refuted**

## Reasoning

- Why this data: Millimeter observations are needed to constrain dust mass, so the sample was built from ALMA surveys of the regions  
  > "so we compiled our sample using (sub)millimeter surveys of these regions" (2 Sample selection)
- Why this method: ANN emulation of DIAD models makes SED fitting of large samples fast  
  > "the ANN takes a few milliseconds to evaluate the SEDs, compared to the 1-2 hours that the DIAD models require" (3.2.1 The model)
- How they decided it was enough: _not stated_
- Limitation (authors): Sample includes only sources detected in the (sub)mm, biasing toward massive disks  
  > "Most importantly, this sample is only made up of sources detected in the (sub)mm range." (3.2.1 The model)
- Limitation (authors): Regions biased toward higher masses and have different detection limits  
  > "We note that the objects included in each region are biased towards higher masses as we only include sources with millimeter-wavelength detections." (4.2 Comparison of Serpens & L1641/L1647 with other Star-Forming Regions)
- Limitation (authors): Region discrepancy factors may be affected by differing sample sizes  
  > "It is important to note that these regions have different sample sizes, so it is likely that these values are influenced by the number of objects." (4.1 The importance of optical depth when deriving disk masses)
- Limitation (authors): Not sensitive to grains larger than 1 mm  
  > "First, we are not sensitive to grains $> 1$ mm." (4.3 The missing mass problem)
- Caveat (inferred, ours): Dust masses depend on fixed DIAD assumptions (dust composition, gas-to-dust ratio, no substructure), so the factor of 2 may be model-dependent
- Caveat (inferred, ours): Fit quality cuts are judged by eye and remove 33 sources, which may bias the result toward well-behaved disks
- Caveat (inferred, ours): Flux-based comparison uses a constant 20 K, which may exaggerate the discrepancy for luminous stars
- Caveat (inferred, ours): No independent test of the SED masses, such as longer-wavelength fluxes, is shown

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Code: No code release stated; MCMC corner plots for all 178 disks hosted on Zenodo  
  > "The corresponding corner plots generated from the MCMC process for all 178 disks are hosted within the designated" (3.3 Model results)
- Missing: ANN weights and DIAD code from earlier papers
- Missing: MCMC sampler settings and prior bounds
- Missing: Per-source photometry table and ALMA fluxes from the cited surveys
- Missing: Definition of successful versus unsuccessful fits
- Data volume (inferred): Under 1 GB: published fluxes and catalog photometry; no ALMA visibilities processed
- Score (inferred): 2/5, Uses only published ALMA fluxes and a pre-trained ANN from earlier papers; the paper gives the pipeline outline but leaves model and sampler settings to references
- Rediscovery candidate: no, The core recipe depends on the Ribas et al. 2020 ANN and unstated MCMC settings, and no ALMA data processing is involved

## Links

- Method: Ribas et al. 2020 (cite: 2020Ribas) (ANN-DIAD SED fitting method used here)
- Method: Xin et al. 2023 (cite: 2023Xin) (likelihood, mixture model and optical depth methodology)
- Method: Rilinger et al. 2023 (cite: 2023Rilinger) (MCMC set-up, 41 L1641 results and 10 comparison regions)
- Companion: Anderson et al. 2022 (cite: 2022Anderson) (ALMA 1.3 mm Serpens survey supplying fluxes)
- Companion: van Terwisga et al. 2022 (cite: 2022vanTerwisga) (Survey of Orion Disks with ALMA supplying L1641/L1647 fluxes)
- Related: Survey of Orion Disks with ALMA (SODA)
- Related: Spitzer c2d
- Related: Gould Belt Survey
- Related: CASSIS

## Checks

```json
{
 "quotes": 86,
 "quotes_ok": 86,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 122,
  "stated": 64,
  "rate": 0.525
 },
 "evidence_ok": true
}
```
