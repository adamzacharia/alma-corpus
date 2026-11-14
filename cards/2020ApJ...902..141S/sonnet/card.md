# The VLA/ALMA Nascent Disk and Multiplicity (VANDAM) Survey of Orion Protostars. III. Substructures in Protostellar Disks

`2020ApJ...902..141S` | The Astrophysical Journal 2020 | first author: Sheehan, Patrick D. | arXiv: 2010.00606 | DOI: 10.3847/1538-4357/abbad5

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, protoplanetary_disks
- Question: How early do substructures (rings, gaps, cavities, asymmetries) form in protostellar disks, and how young/embedded are the disks that show them?  
  > "Two questions of particular note are: 1. How do these substructures form? And, 2. How early do they form?" (1 Introduction)
- Target **HH270-MMS2**: coordinates _not stated_; z/distance 400 pc (assumed)  
  > "in the absence of measured distances for individual sources, we assume they are all at 400 pc, a typical distance for Orion (cite: Zucker2019)" (3.3 Radiative Transfer Modeling); distance from typical Orion distance, Zucker2019  
  > "in the absence of measured distances for individual sources, we assume they are all at 400 pc, a typical distance for Orion (cite: Zucker2019)" (3.3 Radiative Transfer Modeling)
- Target **HOPS-56B**: coordinates _not stated_; z/distance 400 pc (assumed)  
  > "in the absence of measured distances for individual sources, we assume they are all at 400 pc, a typical distance for Orion" (Radiative Transfer Modeling); distance from Zucker2019  
  > "we assume they are all at 400 pc, a typical distance for Orion (cite: Zucker2019)" (Radiative Transfer Modeling)
- Target **HOPS-65**: coordinates _not stated_; z/distance 400 pc (assumed)  
  > "in the absence of measured distances for individual sources, we assume they are all at 400 pc, a typical distance for Orion" (Radiative Transfer Modeling); distance from Zucker2019  
  > "we assume they are all at 400 pc, a typical distance for Orion (cite: Zucker2019)" (Radiative Transfer Modeling)
- Target **HOPS-124**: coordinates _not stated_; z/distance 400 pc (assumed)  
  > "in the absence of measured distances for individual sources, we assume they are all at 400 pc, a typical distance for Orion" (Radiative Transfer Modeling); distance from Zucker2019  
  > "we assume they are all at 400 pc, a typical distance for Orion (cite: Zucker2019)" (Radiative Transfer Modeling)
- Target **HOPS-140**: coordinates _not stated_; z/distance 400 pc (assumed)  
  > "in the absence of measured distances for individual sources, we assume they are all at 400 pc, a typical distance for Orion" (Radiative Transfer Modeling); distance from Zucker2019  
  > "we assume they are all at 400 pc, a typical distance for Orion (cite: Zucker2019)" (Radiative Transfer Modeling)
- Target **HOPS-157**: coordinates _not stated_; z/distance 400 pc (assumed)  
  > "in the absence of measured distances for individual sources, we assume they are all at 400 pc, a typical distance for Orion" (Radiative Transfer Modeling); distance from Zucker2019  
  > "we assume they are all at 400 pc, a typical distance for Orion (cite: Zucker2019)" (Radiative Transfer Modeling)
- Target **HOPS-163**: coordinates _not stated_; z/distance 400 pc (assumed)  
  > "in the absence of measured distances for individual sources, we assume they are all at 400 pc, a typical distance for Orion" (Radiative Transfer Modeling); distance from Zucker2019  
  > "we assume they are all at 400 pc, a typical distance for Orion (cite: Zucker2019)" (Radiative Transfer Modeling)

## Data provenance

- ALMA projects: 2015.1.00041.S, 2018.1.01284.S
- bands: _not stated_
- frequencies and spectral setup: VANDAM at 345 GHz; ACA continuum spws centered at 332.975 and 343.975 GHz, 2.000 GHz bandwidth each  
  > "The spectral windows for the continuum imaging were centered on 332.975 and 343.975 GHz, with the correlator providing bandwidths of 2.000 GHz at each frequency." (2 Sample Selection & Data Reduction)
- continuum bandwidth: _not stated_
- arrays: ALMA main array plus ACA 7M  
  > "with the ALMA Compact Array 7M array (ACA)" (2 Sample Selection & Data Reduction)
- configurations: _not stated_
- baselines: ACA: 8.9 m to 48.9 m  
  > "The minimum baseline was 8.9 m, and the maximum was 48.9 m." (2 Sample Selection & Data Reduction)
- angular resolution: ~0.1" (~40 au); 0.06" for HOPS-124  
  > "with ALMA at 345 GHz and $\sim$0.1" spatial resolution ($\sim40$ au at the distance of Orion" (2 Sample Selection & Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: ACA: 4500 to 6000 s  
  > "On-source integration times ranged from 4500 to 6000 seconds" (2 Sample Selection & Data Reduction)
- observing dates: ACA: 2-30 October 2018  
  > "These observations were conducted between 2 October and 30 October 2018." (2 Sample Selection & Data Reduction)
- pi or archival as stated: _not stated_
- Other facility **Herschel Orion Protostar Survey (Spitzer, Herschel, 2MASS)**: SED photometry and Spitzer IRS spectra for RT fitting  
  > "This dataset includes near-infrared Spitzer IRAC and MIPS photometry, Herschel PACS photometry, 2MASS J, H, and K photometry, and Spitzer IRS spectroscopy." (2 Sample Selection & Data Reduction)
- Other facility **HST NICMOS/WFC3**: archival near-IR images to check multiplicity  
  > "we compare our ALMA observations with Hubble Space Telescope (HST) archival near-infrared imaging with NICMOS or WFC3 (cite: Kounkel2016)" (4 Discussion)
- Other facility **APEX/LABOCA**: 870 um single-dish fluxes  
  > "$F_{0.87{}mm,APEX}$" (Table 1)
- External data: Source properties (Lbol, Tbol, class, 0.87 mm and 9 mm fluxes) from VANDAM overview  
  > "We report the source properties from (cite: Tobin2020) for all 7 disks in our sample" (2 Sample Selection & Data Reduction) [from (cite: Tobin2020)]
- External data: Herschel Orion Protostar Survey SEDs and IRS spectra  
  > "we collect supplementary photometric and spectroscopic data from the *Herschel* Orion Protostar Survey (cite: Fischer2013)" (2 Sample Selection & Data Reduction) [from (cite: Fischer2013)]

## Processing

### Calibration

- pipeline or manual: ACA: ALMA pipeline reduction scripts from data package  
  > "Calibration was completed using the basic reduction scripts included in the data package for running the ALMA pipeline." (2 Sample Selection & Data Reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Calibrated MS used without modification for most sources  
  > "For most sources we use the ALMA visibilities from the (self-)calibrated Measurement Set files, without modification, for our analysis." (2 Sample Selection & Data Reduction)
- flux calibrator: _not stated_
- flux scale uncertainty: typically ~10%  
  > "flux calibration uncertainties, which are typically on the order of 10%." (Table 1)
- self calibration: self-calibration done for all sources in the paper (per Tobin2020)  
  > "We note that self-calibration was done for all of the sources considered in this manuscript." (2 Sample Selection & Data Reduction)

### Imaging

- task: CASA clean and uvsub used to remove companions in HOPS-56B and HOPS-140  
  > "we first run the CASA *clean* task to generate a $clean$-component model of the data." (2 Sample Selection & Data Reduction)
- deconvolver: _not stated_
- weighting robust: Briggs robust 0.5 for most; superuniform for HOPS-124  
  > "All of these images were made with a robust parameter of 0.5 and a beam size of $\sim0.1"$, with the exception of HOPS-124" (2 Sample Selection & Data Reduction)
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
- final beam: ~0.1"; 0.06" for HOPS-124  
  > "we used superuniform weighting to achieve a resolution of 0.06"." (2 Sample Selection & Data Reduction)
- final rms: _not stated_

### Inherited from earlier work

- Data reduction, self-calibration and imaging of VANDAM data  
  > "Details of the data reduction, self-calibration when the signal-to-noise ratio was high enough, and imaging can be found in the survey overview paper (cite: Tobin2020)." (2 Sample Selection & Data Reduction) [from (cite: Tobin2020)]
- Radiative transfer modeling methodology  
  > "Our modeling follows the methods described in (cite: Sheehan2017b), with a few minor updates and differences." (3.3 Radiative Transfer Modeling) [from (cite: Sheehan2017b)]
- Analytic model form  
  > "motivated by the models fit in (cite: vanderMarel2015)" (3.1 Analytic Models) [from (cite: vanderMarel2015)]
- Dust opacity 1.84 cm2/g  
  > "dust with an opacity of 1.84 cm$^2$ g$^{-1}$ (cite: Ossenkopf1994; Tobin2020)" (3.2 Analytic Modeling Results) [from (cite: Ossenkopf1994; Tobin2020)]

### Not stated but needed to reproduce (our reading)

- CASA version used
- Exact clean parameters and masks for the sources imaged here, and uvsub masks for HOPS-56B and HOPS-140
- dynesty settings (live points, stopping criteria)
- emcee walker number, steps, burn-in and priors for the RT models
- Full RT parameter list, priors and dust model details (deferred to Sheehan2017b)
- Which analytic model components are used for each source beyond the Bayes factor table
- Public availability of the self-calibrated MS files

## Analysis recipe

1. **select disks with substructure**: Visual inspection of images of all VANDAM sources, using several robust values and superuniform weighting  
  > "we selected every source that, by visual inspection, showed clear and unambiguous evidence of annular substructures/local extrema" (2 Sample Selection & Data Reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: Excluded tentative sources to avoid imaging artefacts  
  > "we excluded these sources out of caution to not falsely identify imaging artefacts as substructures" (2 Sample Selection & Data Reduction)
2. **isolate target visibilities**: clean model, mask target components, uvsub remainder for HOPS-56B and HOPS-140  
  > "subtract the remaining $clean$ components from the data in the visibility plane using the CASA $uvsub$ task" (2 Sample Selection & Data Reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: Re-imaged to check no residual sources and structure unaltered  
  > "we confirm this by re-imaging the data to ensure that there are no traces remaining of the additional sources" (2 Sample Selection & Data Reduction)
3. **fit analytic ring/asymmetry/point/Gaussian models in uv plane**: Image-plane model Fourier-transformed with GALARIO at observed baselines; up to 18 parameters  
  > "we generate an image-plane model image, and use the `GALARIO` package (cite: Tazzari2018) to compute the Fourier transform of that image sampled at the same baselines as our observations." (3.1 Analytic Models)
   - software: GALARIO, dynesty
   - parameter: Visibility weights multiplied by ~0.25 to match image RMS  
  > "the weights provided by the ALMA pipeline need to be multiplied by a factor of $\sim0.25$ to match the RMS of the images" (2 Sample Selection & Data Reduction)
   - fitting: Bayesian nested sampling with dynesty, uniform priors; best fit = maximum posterior sample; uncertainties 95% inclusion interval  
  > "Samples are drawn from uniform priors on all parameters, with limits listed in Table [\[table:analytic_priors\]]" (3.1 Analytic Models)
   - validation: Bayes factors between model complexities; residual images and visibility profiles  
  > "we provide a calculation of Bayes Factor in Table [\[table:analytic_best_fits\]] for each model considered, compared with the most complete model" (3.2 Analytic Modeling Results)
4. **estimate large-scale Gaussian mass**: Optically thin dust mass from flux  
  > "standard assumptions of optically thin, isothermal (T $=20$ K) dust with an opacity of 1.84 cm$^2$ g$^{-1}$" (3.2 Analytic Modeling Results)
   - assumption: T=20 K, kappa=1.84 cm2/g, gas-to-dust 100  
  > "a gas-to-dust ratio of 100 to convert the millimeter flux to a mass" (3.2 Analytic Modeling Results)
   - fitting: _not stated_
   - validation: _not stated_
5. **fit protostar+disk+envelope RT models**: RADMC-3D models of SED and 345 GHz image, GALARIO to visibilities, emcee MCMC; visibilities centered using analytic best-fit centroids  
  > "we instead use the `emcee` code to run a Markov Chain Monte Carlo (MCMC) fit of the synthetic observations to our dataset" (3.3 Radiative Transfer Modeling)
   - software: RADMC-3D, GALARIO, emcee, pdspy
   - parameter: Protostar T=4000 K, luminosity free; inner disk radius 0.1 au; cavity or gap added  
  > "we fix the inner radius of the disk at 0.1 au, and include a central cavity or a gap with some amount of depletion" (3.3 Radiative Transfer Modeling)
   - assumption: Distance 400 pc; axisymmetric models; Ulrich envelope  
  > "we assume they are all at 400 pc, a typical distance for Orion" (3.3 Radiative Transfer Modeling)
   - fitting: emcee; best fit = max posterior, 95% range uncertainties; lost walkers redistributed  
  > "Walkers that got “lost" (cite: Sheehan2019), were redistributed around the median of the post-burn-in samples" (3.4 Radiative Transfer Modeling Results)
   - validation: Compared models to ACA data not included in fit  
  > "Despite not being included in the fits, our best fit models show good consistency with the short-baseline ACA data" (3.4 Radiative Transfer Modeling Results)
6. **derive Menv/Mdisk evolutionary indicator**: Posterior of envelope-to-disk mass ratio from RT fits  
  > "we suggest using the ratio of the envelope mass to the disk mass ($M_{env}/M_{disk}$) as an evolutionary indicator" (3.4 Radiative Transfer Modeling Results)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : clean, uvsub, ACA reduction  
  > "we first run the CASA *clean* task to generate a $clean$-component model of the data" (2 Sample Selection & Data Reduction)
- **GALARIO** : Fourier transform of model images to visibilities  
  > "use the `GALARIO` package (cite: Tazzari2018) to compute the Fourier transform" (3.1 Analytic Models)
- **dynesty** : nested sampling of analytic models  
  > "use the multi-nested sampler `dynesty` (cite: Speagle2019a)" (3.1 Analytic Models)
- **RADMC-3D** : radiative transfer, temperature, synthetic SEDs and images  
  > "We use the RADMC-3D code (cite: Dullemond2012) to run the radiative transfer" (3.3 Radiative Transfer Modeling)
- **emcee** : MCMC fitting of RT models  
  > "we instead use the `emcee` code to run a Markov Chain Monte Carlo (MCMC) fit" (3.3 Radiative Transfer Modeling)
- **pdspy** : listed in Software section (modeling framework)  
  > "pdspy (cite: Sheehan2018b), CASA (cite: McMullin2007), RADMC-3D (cite: Dullemond2012)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Menv/Mdisk range, lowest (HOPS-65) | 0.003 | +0.005/-0.002 | dimensionless | 6 | ranging from $0.003^{+0.005}_{-0.002}$ (HOPS-65) – $94.38^{+121.86}_{-56.13}$ (HOPS-157) |
| Menv/Mdisk HOPS-157 | 94.38 | +121.86/-56.13 | dimensionless | 6 | $94.38^{+121.86}_{-56.13}$ (HOPS-157) |
| Menv/Mdisk HOPS-124 | 1.95 | +0.40/-0.44 | dimensionless | 6 | HOPS-124 has $M_{env}/M_{disk} = 1.95^{+0.40}_{-0.44}$ |
| Menv/Mdisk HOPS-163 | 0.037 | +0.024/-0.027 | dimensionless | 6 | HOPS-163 has $M_{env}/M_{disk} = 0.037^{+0.024}_{-0.027}$ |
| Mass in large-scale Gaussian components (dust+gas) | 0.014 – 0.32 | not stated | Msun | 4 | This simple method estimates a range of 0.014 – 0.32 M$_{\odot}$ of material in these components of dust+gas on large scales. |
| Ring center radii range | ~0.1"-0.6" (40-240 au) | not stated | arcsec | 3 | The radii of the centers of the rings range from $\sim0.1"-0.6"$ ($40-240$ au at the distance of Orion) |
| Ring radius HOPS-124 (analytic) | 146.9 | +0.7/-0.6 | mas | 3 | $r_{c,r}$ (mas)           / $105.0^{+  1.7}_{-  2.0}$     / $331.0^{+ 10.0}_{- 10.6}$     / $595.9^{+ 16.7}_{- 20.7}$     / $146.9^{+  0.7}_{-  0.6}$ |

## Qualitative findings

- Each disk is dominated by a single bright ring; five have a brightness asymmetry and four show inner point-source emission offset from the ring center.  
  > "Each of the disks in our sample is dominated by a single bright ring." (3 Analysis & Results)

## Claim tuples

- H: Substructures can form in very young, embedded protostellar disks | E: Identified 7 VANDAM disks with rings/cavities/asymmetries and modeled with RT to get envelope masses | R: Menv/Mdisk ranges 0.003 to 94; several sources ~1 or >>1 | F: Substructures develop while disks are still embedded in substantial envelopes; these are the youngest disks with substructure known | **supported**
- H: The inner disks are centered on the rings | E: Posterior of point-source position vs ring center in analytic fits | R: Point source offset from ring center in all four sources | F: Inner disks are offset from ring centers | **supported**
- H: The features are due to multiplicity | E: Compared ALMA with HST images | R: No compelling evidence for multiplicity, but HST resolution is coarse | F: Binary origin plausible but untested | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: RT models give a more physical evolutionary status than spectral-index classes  
  > "These are designed, in particular, to gain a better picture of the physical structure of these systems to better understand their evolutionary status" (3 Analysis & Results)
- Alternative: Leaving the centroid free in RT fits was rejected since axisymmetric models could not reproduce asymmetries  
  > "we found that the inability of our models to reproduce non-axisymmetric structure often affected the resulting best-fit model" (3.3 Radiative Transfer Modeling)
- How they decided it was enough: _not stated_
- Limitation (authors): HOPS-56B envelope mass is more uncertain due to nearby source subtraction  
  > "the results for HOPS-56B should be considered more uncertain than the nominal errors show" (3.4 Radiative Transfer Modeling Results)
- Limitation (authors): HOPS-124 and HOPS-157 envelope masses may be lower limits  
  > "the envelope masses measured here, and consequently their $M_{env}/M_{disk}$ ratios, might reasonably be considered lower limits" (3.4 Radiative Transfer Modeling Results)
- Caveat (inferred, ours): Distance fixed at 400 pc for all sources
- Caveat (inferred, ours): RT models axisymmetric, cannot fit asymmetries or offset inner disks
- Caveat (inferred, ours): Visibility weight rescaling of 0.25 is ad hoc
- Caveat (inferred, ours): Sample selected by eye, so no statistics on prevalence
- Caveat (inferred, ours): Envelope mass degenerate with dust properties and opacity assumptions

## Reproducibility

- Data public (paper): Project codes given; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00041.S, 2018.1.01284.S." (Acknowledgments)
- Products in archive: _not stated_
- Code: pdspy cited (Zenodo) but no analysis scripts stated  
  > "pdspy (cite: Sheehan2018b)" (Software)
- Missing: Self-calibrated VANDAM measurement sets (from Tobin2020 processing)
- Missing: MCMC and nested-sampling run configuration
- Missing: Full RT priors from Sheehan2017b
- Data volume (inferred): ~100-300 GB for VANDAM MS plus ACA data (tens of GB)
- Score (inferred): 3/5, Models and priors are well described and results are tabulated, but imaging and calibration details are deferred to Tobin2020, and sampler settings and RT priors are missing.
- Rediscovery candidate: no, Recipe relies on inherited reduction and heavy RT modeling with missing sampler settings.

## Links

- Method: Tobin et al. 2020 (cite: Tobin2020) (VANDAM data reduction and source properties)
- Method: Sheehan & Eisner 2017 (cite: Sheehan2017b) (RT modeling method)
- Method: Tazzari et al. 2018 (cite: Tazzari2018) (GALARIO)
- Companion: Tobin et al. 2020 (cite: Tobin2020) (VANDAM survey overview)
- Related: VANDAM: Orion
- Related: Herschel Orion Protostar Survey

## Checks

```json
{
 "quotes": 79,
 "quotes_ok": 79,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 103,
  "stated": 66,
  "rate": 0.641
 },
 "evidence_ok": true
}
```
