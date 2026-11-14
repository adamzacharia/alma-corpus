# The Evolution of Dust Disk Sizes from a Homogeneous Analysis of 1-10 Myr old Stars

`2020ApJ...895..126H` | The Astrophysical Journal 2020 | first author: Hendler, Nathanial | arXiv: 2001.02666 | DOI: 10.3847/1538-4357/ab70ba

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks, solar_system
- Question: How do dust disk sizes, and their relations to mm luminosity and stellar properties, differ among star-forming regions of different ages when derived homogeneously, and how does the Solar System's outer edge compare?  
  > "We use these 199 homogeneously derived disk sizes to identify empirical disk-disk and disk-host property relations as well as to search for evolutionary trends." (abstract)
- Target **Lupus disks (62 detections modelled; 50 retained)**: coordinates _not stated_; z/distance Gaia DR2 distances from Andrews2018a (~136-175 pc, Table 2)  
  > "We include in our sample all the 62 detections from the ALMA project `2013.1.00220.S` (PI: Johnathan Williams) as presented in (cite: Ansdell2016)." (2.2 Lupus, Cha I, and USco); distance from Gaia DR2 as presented in Andrews2018a  
  > "We include in our sample all the 62 detections from the ALMA project `2013.1.00220.S` (PI: Johnathan Williams) as presented in (cite: Ansdell2016)." (2.2 Lupus, Cha I, and USco)
- Target **Chamaeleon I disks (72 detections; 58 retained)**: coordinates _not stated_; z/distance Bailer-Jones2018 Gaia DR2 distances; median 190 pc when unavailable  
  > "We use the 11 detections reported in (cite: Long2018), giving us a total of 72 Cha I disks." (2.2 Lupus, Cha I, and USco); distance from Bailer-Jones et al. 2018 Gaia catalogue  
  > "We use the 11 detections reported in (cite: Long2018), giving us a total of 72 Cha I disks." (2.2 Lupus, Cha I, and USco)
- Target **Upper Scorpius disks (50 detections; 44 retained)**: coordinates _not stated_; z/distance Bailer-Jones2018 Gaia DR2 distances; median 144 pc when unavailable  
  > "To estimate disk sizes we have selected those 50 USco targets that were detected." (2.2 Lupus, Cha I, and USco); distance from Bailer-Jones et al. 2018 Gaia catalogue  
  > "To estimate disk sizes we have selected those 50 USco targets that were detected." (2.2 Lupus, Cha I, and USco)

## Data provenance

- ALMA projects: 2013.1.00220.S, 2013.1.00437.S, 2015.1.00333.S, 2011.0.00526.S, 2013.1.00395.S
- bands: Band 7 (~880-975 um)  
  > "We re-reduce band 7 ($\sim880-975\ensuremath{\mu}m$) observations of similar sensitivity for the sample of disks presented in Section [2.2](#sec_sample_alma)." (3 ALMA Observations and Data Reduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Typical beams: Lupus 0.28-0.35", Cha I 0.5-0.7", USco 0.35-0.75"  
  > "| Lupus   | ALMA      |  935-954  | $0.28 - 0.35$ |     |     |" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archival ALMA data; 2011.0.00526.S measurement sets provided by PI/co-author J. Carpenter  
  > "We utilize ALMA archival data to estimate the dust disk size of 152 protoplanetary disks" (abstract); "Measurement sets from the project `2011.0.00526.S` (USco) were directly provided by the PI and co-author J. Carpenter." (3 ALMA Observations and Data Reduction)
- Other facility **SMA**: Oph and Tau/Aur disk sizes taken from literature (880 um)  
  > "We use previously published disk sizes for Oph and Tau/Aur with observations obtained by the Submillimeter Array (SMA; see Section [2.1](#sec_sample_lit) for more details)" (2 Initial Sample Selection)
- Other facility **Gaia DR2**: Distances used to rescale stellar luminosities  
  > "Then, we scale these luminosities to the new Gaia DR2 distances." (2.2.1 Stellar masses)
- External data: Oph and Tau/Aur disk sizes (R68), Gaia-updated  
  > "relying on the Gaia-updated values reported in (cite: Andrews2018a)" (2.1 Oph and Tau/Aur) [from (cite: Tripathi2017); (cite: Andrews2018a)]
- External data: Stellar Teff and bolometric luminosities for Lupus, Cha I, USco  
  > "For Lupus we rely on (cite: Alcala2014; Biazzo2017; Frasca2017; Andrews2018a); For Cha I on (cite: Manara2016; Manara2017); while for USco we rely on (cite: Barenfeld2016)." (2.2.1 Stellar masses) [from Alcala2014; Biazzo2017; Frasca2017; Andrews2018a; Manara2016; Manara2017; Barenfeld2016]
- External data: Self-calibrated visibilities for the 10 brightest Cha I disks  
  > "for the 10 brightest Cha I disks[^1], we use self-calibrated visibilities from (cite: Pascucci2016)" (3 ALMA Observations and Data Reduction) [from (cite: Pascucci2016)]

## Processing

### Calibration

- pipeline or manual: NAASC-provided calibration scripts (phase, bandpass, flux) used to build measurement sets  
  > "measurement sets are built using the calibration scripts created by the North American ALMA Science Center (NAASC)." (3 ALMA Observations and Data Reduction)
- casa version: Same as NAASC scripts; CASA 4.7.2-el6 for averaging; 5.1.1-5.el7 for 2013.1.00220.S and A001_X11d_X13  
  > "Calibration of the sources in science goal `A001_X11d_X13` (Cha I) and project `2013.1.00220.S` (Lupus) was performed using `CASA` version `5.1.1-5.el7`." (3 ALMA Observations and Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Only for 10 brightest Cha I disks (from Pascucci2016); not applied elsewhere  
  > "The disk sizes resulting from self-calibrated visibilities are the same as those derived from non-self-calibrated visibilities, hence we do not apply self calibration to the other regions." (3 ALMA Observations and Data Reduction)

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

- Nuker-profile visibility modeling and effective-radius (R68) definition  
  > "To expand upon the results presented in (cite: Tripathi2017) and (cite: Andrews2018a), we use a similar method to derive disk sizes for Lupus, ChaI and USco." (4 Modeling Method) [from (cite: Tripathi2017); (cite: Andrews2018a)]
- Stellar masses via Bayesian inference approach  
  > "Stellar masses are determined following the Bayesian inference approach described in (cite: Pascucci2016)." (2.2.1 Stellar masses) [from (cite: Pascucci2016)]
- Dust mass: optically thin, 20 K  
  > "Dust disk masses are estimated assuming optically thin emission and a fixed temperature of 20 K for the emitting grains as in the 20 K dust-mass calculation described in (cite: Pascucci2016)." (6.2 The outer edge of the Solar System) [from (cite: Pascucci2016)]
- Lmm definition: flux density scaled to 140 pc  
  > "For consistency, our definition of $L_{\text{mm}}$ is the same as found in (cite: Andrews2018a). It is a flux density scaled to 140 pc." (Table 2 notes) [from (cite: Andrews2018a)]

### Not stated but needed to reproduce (our reading)

- Exact channel/time averaging per source
- Weighting/robust and imaging parameters (visibility fitting only, uv-data weights)
- Flux calibration uncertainty
- Line-free channel selection / handling of CO line contamination in band 7
- Exact Lmm conversion (flux integration, fluxes used) from Andrews2018a
- Exact MCMC convergence criterion per source
- Rule for choosing between resolved and unresolved model beyond reduced chi2
- Cha I science goal A001_X11d_X13 project code not printed

## Analysis recipe

1. **Reduce and average visibilities**: NAASC calibration scripts, remove 8 edge channels per spw, average in time and channel  
  > "Because the 8 outermost edge channels in each spectral window are typically noisy, we remove them from our measurement sets." (3 ALMA Observations and Data Reduction)
   - software: CASA
   - parameter: Spw averaging typically 19 channels (22 for 2011.0.00526.S); time averaging 2-30 s  
  > "However, we constrain all time averaging to be between 2 and 30 seconds." (3 ALMA Observations and Data Reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit radial brightness profiles to visibilities**: Nuker profile and point source fit in visibility domain with GALARIO and emcee; also fit i, PA, offsets, lnwcorr  
  > "For all disks, we test two different functions for generating the radial profile shape: a Nuker profile (cite: Lauer1995) and a Dirac delta function (point source)." (4 Modeling Method)
   - software: GALARIO, emcee
   - parameter: 70 walkers, 100,000 steps, burn-in 100 walkers x 1000 steps; uniform priors  
  > "We cover this parameter space with 70 chains (ensemble sample walkers) which individually take 100,000 steps in order to sample the posterior probability distribution function (PDF)." (4 Modeling Method)
   - assumption: Axisymmetric disks  
  > "we assume axisymmetric disks and use a parametric radial intensity profile to fit the disk intensity in the visibility domain." (4 Modeling Method)
   - fitting: emcee MCMC, uniform priors (Rt in [0.005,3], gamma [-11,4], logalpha [0.3,1.3], beta [1,17], logF0 [3,12], i [0,90], PA [0,179], offsets +-3 arcsec, lnwcorr [-10,10]); likelihood on real and imaginary visibilities  
  > "Uniform priors are used over a parameter space defined as: $\ensuremath{
    R_{\text{t}}}
 \in [0.005,3]$ au, $\gamma \in [-11,4]$" (4 Modeling Method)
   - validation: Autocorrelation length for convergence; Lupus results compared with Andrews2018a  
  > "We use the autocorrelation length as a guide to understand at what point in the chain convergence occurs." (4 Modeling Method)
3. **Derive effective radii and resolved/unresolved status**: R68 and R90 from cumulative flux for 5000 random models from second half of chain; median and 16/84 quantiles; compare reduced chi2 of Nuker vs point source; 84th percentile as upper limit if unresolved  
  > "We randomly sample 5000 models from the second half of our MCMC chain, and for each model we calculate $R_{\text{eff}}$ ." (4 Modeling Method)
   - fitting: _not stated_
   - validation: Compared with Andrews2018a Lupus sizes; stuck-walker test  
  > "our method retrieves the same disk sizes as those in (cite: Andrews2018a) for most sources" (4 Modeling Method)
4. **Sample selection**: Remove multiples with separation <=2"; remove 15 spurious models with size uncertainty >66% of size inspected by eye  
  > "Of the 23 disks that meet this metric, we find 15 that are obviously problematic, and hence removed them from our analysis" (10 Determination and removal of spurious modeling)
   - fitting: _not stated_
   - validation: _not stated_
5. **Derive stellar masses**: Bayesian inference with literature Teff and L (rescaled to Gaia DR2)  
  > "we assume an uncertainty of 0.02 dex in the stellar temperature for spectral types earlier than M3 and 0.01 dex for later spectral types and a 0.1 dex uncertainty on all stellar luminosities." (2.2.1 Stellar masses)
   - fitting: _not stated_
   - validation: _not stated_
6. **Statistical comparison of regions and relations**: Kaplan-Meier CDFs, Anderson-Darling tests, Shapiro-Wilk, Pearson/Spearman, linmix regression of log Reff vs Lmm, M*, L*  
  > "For this task we use the Bayesian method of linear regression described in (cite: Kelly2007) (as implemented in the `linmix` code by Joshua E. Meyers)" (5.1.1 Disk radii and millimeter luminosities)
   - software: linmix, lifelines, scipy
   - parameter: p<0.05 threshold  
  > "In cases where the p-value for the chosen statistic is $<0.05$ we consider the data to be correlated." (5.1 Relations between stellar and disk properties)
   - fitting: linmix Bayesian regression accounting for errors and upper limits  
  > "we fit the $\log{R_{\text{eff}}}-\log{\ensuremath{ L_{\text{mm}}}}$ relation in each individual region taking into account measured $R_{\text{eff}}$ , the associated uncertainties, as well as upper limits in $R_{\text{eff}}$ ." (5.1.1 Disk radii and millimeter luminosities)
   - validation: Comparison of Lupus linmix fits with Andrews2018a  
  > "Our fitting of both the (cite: Andrews2018a) sample and our sample gives results that are consistent with each other" (8.1 Lupus comparison)

## Software

- **CASA** 4.7.2-el6; 5.1.1-5.el7: Calibration scripts and averaging  
  > "For these steps, we use `CASA` version `4.7.2-el6`." (3 ALMA Observations and Data Reduction)
- **GALARIO** : Fourier transform of model images to visibilities  
  > "which is Fourier transformed and sampled at the same spatial frequencies as our observational data using `GALARIO` (cite: Tazzari2018)" (4 Modeling Method)
- **emcee** : MCMC fitting  
  > "using the `emcee` implementation (cite: Foreman-Mackey2013) of the Markov Chain Monte Carlo method (MCMC)" (4 Modeling Method)
- **linmix** : Bayesian linear regression  
  > "(as implemented in the `linmix` code by Joshua E. Meyers)" (5.1.1 Disk radii and millimeter luminosities)
- **lifelines** v0.21.3: Kaplan-Meier estimator  
  > "We use the Python lifelines (cite: cameron_davidson_pilon_2019_3240536) Kaplan-Meier implementation." (footnote 4)
- **uvplot** : Listed in software section (uv plotting)  
  > "uvplot (cite: Tazzariuvplot)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Disks with estimated sizes | 152 (50 Lupus, 58 Cha I, 44 USco) | not stated | disks | 4 | This leaves us with 152 disks: 50 from Lupus, 58 from Cha I and 44 from USco which we include in our analysis. |
| Median R68 Lupus | 46.6 | not stated | au | 3 | Lupus & 30 & 46.6 & 128.1 & 63.2 & 213.1 |
| Median R68 Cha I | 33.9 | not stated | au | 3 | Cha I & 33 & 33.9 & 140.9 & 43.1 & 231.3 |
| Median R68 USco | 26.8 | not stated | au | 3 | USco & 22 & 26.8 & 100.8 & 33.4 & 126.2 |
| Anderson-Darling significance USco vs Lupus | 0.013 | not stated | dimensionless | 6 | USco & Lupus & 3.4 & $0.013$ |
| log Reff-log Lmm slope beta, Lupus | 0.57 | +/-0.10 | dimensionless | 6 | $2.20^{+0.14}_{-0.13}$ & $0.57^{+0.10}_{-0.10}$ |
| log Reff-log Lmm slope beta, Cha I | 0.40 | +/-0.06 | dimensionless | 6 | $1.97^{+0.08}_{-0.08}$ & $0.40^{+0.06}_{-0.06}$ |
| log Reff-log Lmm slope beta, USco | 0.22 | +0.11/-0.10 | dimensionless | 6 | $1.68^{+0.23}_{-0.22}$ & $0.22^{+0.11}_{-0.10}$ |
| Temperature index q | 0.32 (Cha I); -0.85 (USco) | +0.33/-0.4 (Cha I); +1.42/-3.1 (USco) | dimensionless | 6 | values of $q$ of $0.32^{+0.33}_{-0.4}$ for Cha I and $-0.85^{+1.42}_{-3.1}$ for USco |
| R90 for near-solar-mass stars | 20-103 | not stated | au | 3 | $R_{\text{90}}$ disk sizes range from 20-103 au. |
| R90 vs R68 relation | log R90 = -0.037 + 1.1 log R68 | not stated | au | 3 | \log{\ensuremath{
    R_{\text{90}}}
} = -0.037 \text{(au)} + 1.1 \log{\ensuremath{
    R_{\text{68}}}
} \text{(au)} |

## Qualitative findings

- Cha I disks are not smaller than Lupus disks, contrary to Eisner2018  
  > "We find that the disks in Cha I are not smaller than those in Lupus as previously suggested in (cite: Eisner2018)" (7 Summary)

## Claim tuples

- H: Is the Reff-Lmm relation universal across regions? | E: linmix fits per region for 5 regions | R: slopes 0.57 (Lupus), 0.40 (Cha I), 0.22 (USco) | F: The relation flattens in older regions and is not universal | **supported**
- H: Are USco disks smaller than those in younger regions? | E: Compare R68 distributions with Anderson-Darling | R: Median 26.8 au vs 46.6 (Lupus) and 33.9 (Cha I); sig. 0.013-0.014 | F: USco disks are smaller, though by less than factor 3 | **supported**
- H: Are Cha I disks smaller than those in other regions of similar age? | E: Compare homogeneous Cha I and Lupus sizes | R: Anderson-Darling sig 0.105 | F: Cha I not smaller than Lupus | **supported**
- H: Is the Solar System's outer edge consistent with disk sizes? | E: Compare R90 of Lupus/Cha I disks to ~45 au Kuiper Belt edge | R: R90 for near-solar-mass stars 20-103 au | F: Solar System not an outlier; no truncation required | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Same modeling as Tripathi2017 and Andrews2018a to get homogeneous sizes  
  > "using the same modeling techniques in order to present a homogeneously derived census of disk sizes within five regions of varying ages" (1 Introduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Oph and Tau/Aur SMA samples are flux-limited and biased bright  
  > "the Oph and Tau/Aur samples come from flux-limited SMA observations, and consequently are biased towards brighter objects" (2.1 Oph and Tau/Aur)
- Limitation (authors): Correlation tests do not include upper limits and uncertainties  
  > "A limitation of all these statistical tests is that they do not include upper-limits and uncertainties in the assessment." (5.1 Relations)
- Caveat (inferred, ours): Age ordering of regions is uncertain with overlapping ages
- Caveat (inferred, ours): Unresolved disks at ~0.3-0.7" resolution limit small-size conclusions
- Caveat (inferred, ours): Stuck walkers left in chains
- Caveat (inferred, ours): Solar System comparison relies on strong assumptions

## Reproducibility

- Data public (paper): Archival ALMA data from public projects (one set provided by PI)  
  > "the raw data is taken from the ALMA archive" (3 ALMA Observations and Data Reduction)
- Products in archive: _not stated_
- Missing: Per-source averaging parameters
- Missing: Exact sampler convergence settings per source
- Missing: Full fit outputs only in electronic version
- Missing: Andrews2018a Lmm and R68 tables for Oph/Tau/Aur
- Data volume (inferred): ~100s of GB raw for ~180 band 7 datasets; far less after averaging (~ tens of GB)
- Score (inferred): 3/5, Methods, priors, sampler and software are given and data public, but per-source averaging and several inherited choices are unstated and fits are heavy.
- Rediscovery candidate: no, Recipe is mostly stated but needs literature inputs and unstated per-source choices; large MCMC runs for ~150 disks.

## Links

- Method: (cite: Tripathi2017) (Nuker-profile visibility fitting and Reff definition)
- Method: (cite: Andrews2018a) (Lupus/Oph/Tau-Aur sizes and Lmm definition, comparison)
- Method: (cite: Tazzari2018) (GALARIO)
- Method: (cite: Kelly2007) (linmix regression)
- Companion: (cite: Pascucci2016) (Cha I ALMA survey and stellar mass method)
- Companion: (cite: Ansdell2016) (Lupus ALMA survey)
- Companion: (cite: Barenfeld2016) (USco ALMA survey)
- Companion: (cite: Long2018) (Cha I high-resolution detections)
- Related: ALMA Lupus survey
- Related: ALMA Cha I survey
- Related: ALMA USco survey

## Checks

```json
{
 "quotes": 70,
 "quotes_ok": 70,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 5,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 89,
  "stated": 48,
  "rate": 0.539
 },
 "evidence_ok": true
}
```
