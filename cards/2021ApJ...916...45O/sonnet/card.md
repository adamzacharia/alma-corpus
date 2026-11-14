# The Core Mass Function across Galactic Environments. III. Massive Protoclusters

`2021ApJ...916...45O` | The Astrophysical Journal 2021 | first author: O'Neill, Theo J. | arXiv: 2104.08861 | DOI: 10.3847/1538-4357/ac062d | **HELD OUT (benchmark)**

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: star_formation
- Question: What is the shape of the core mass function in 28 massive protocluster clumps observed by ALMAGAL, does it show a break, and does it differ from the G286 protocluster and IRDC CMFs?  
  > "Here we measure the CMF in 28 dense clumps within 3.5 kpc that are likely to be central regions of massive protoclusters, observed via $1.3\:{\rm{mm}}$ dust continuum emission by the ALMAGAL project." (abstract)
- Target **28 ALMAGAL clumps (e.g. G18.30, G345.50, G341.92)**: coordinates Galactic coordinates per clump in Table 1 (e.g. G18.30: l=18.30268, b=-0.38638)  
  > "we limited our analysis to sources within 3.5 kpc that had 12m-array observations delivered to the *ALMA* archive by May 2020. This yields a sample of 28 sources" (Source Selection); z/distance 0.76-3.5 kpc (per clump, Table 1)  
  > "we limited our analysis to sources within 3.5 kpc that had 12m-array observations delivered to the *ALMA* archive by May 2020. This yields a sample of 28 sources" (Source Selection); distance from Hi-GAL (Elia et al. 2017)  
  > "we limited our analysis to sources within 3.5 kpc that had 12m-array observations delivered to the *ALMA* archive by May 2020. This yields a sample of 28 sources" (Source Selection)

## Data provenance

- ALMA projects: 2019.1.00195.L
- bands: 1.3 mm (near 1.4 mm) continuum, 12m array  
  > "ALMAGAL was designed to observe continuum and line emission near $1.4\:$mm from $\gtrsim$1000 high-mass Galactic clumps" (Source Selection)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12m array  
  > "we limited our analysis to sources within 3.5 kpc that had 12m-array observations delivered to the *ALMA* archive by May 2020." (Source Selection)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: median 1σ RMS 0.30 mJy/beam (range 0.13-1.38)  
  > "The median value of $\sigma$ was 0.30 mJy $\textrm{beam}^{-1}$." (Core Identification)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **Herschel Hi-GAL**: Clump selection, distances, masses, radii, surface densities, evolutionary type  
  > "The radius, mass, $\Sigma_{\rm cl}$, and type were derived by (cite: elia_hi-gal_2017)" (Table 1)
- External data: Clump distances, radii, masses, surface densities and type from Hi-GAL  
  > "The radius, mass, $\Sigma_{\rm cl}$, and type were derived by (cite: elia_hi-gal_2017)" (Table 1) [from (cite: elia_hi-gal_2017)]
- External data: Dust opacity 0.899 cm2/g (Ossenkopf & Henning thin ice mantle model)  
  > "the value from the moderately coagulated thin ice mantle model of (cite: ossenkopf_dust_1994)" (Core Mass Estimation) [from (cite: ossenkopf_dust_1994)]
- External data: G286 and IRDC CMFs for comparison  
  > "compares the “true” CMFs that we have derived for the massive protocluster sample to those derived in Paper I for the G286 protocluster and Paper II for the IRDC clumps." (Comparison of CMFs) [from (cite: cheng_core_2018); (cite: liu_core_2018)]

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
- primary beam correction: Cores identified in images not corrected for primary beam  
  > "we diverge from Paper I’s methods and follow those used in Paper II by identifying cores in images that have not been corrected for the primary beam." (Core Identification)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Core identification method (dendrogram parameters)  
  > "To identify cores, we followed the methods used in our studies of the G286 protocluster (Paper I) and IRDCs (Paper II)" (Core Identification) [from Papers I and II (cite: cheng_core_2018; liu_core_2018)]
- Mass estimation, binning and WLS fitting methods  
  > "We estimated masses of cores by assuming optically thin thermal emission from dust, as in Papers I and II." (Core Mass Estimation) [from Papers I and II]
- Flux and number recovery correction curves from artificial core insertion  
  > "In Papers I and II, we derived correction factors to estimate a complete, i.e., “true”, CMF from an observed “raw” CMF." (Core Flux Recovery and Completeness Corrections) [from Papers I and II]

### Not stated but needed to reproduce (our reading)

- Imaging details of the ALMAGAL continuum images (CASA version, weighting, robust, beam, cell size, line-free channels)
- Whether archive-delivered products were used and their pipeline version
- Final synthesized beam sizes per clump
- Exact correction curve values f_flux and f_num as functions of normalized flux
- Random seeds and number of core insertions
- Which statistical code was used for PPL fitting

## Analysis recipe

1. **Measure noise and identify cores**: astrodendro dendrogram on non-primary-beam-corrected images; cores are leaves  
  > "We defined cores as the leaves of the dendrogram." (Core Identification)
   - software: astrodendro
   - parameter: F_min=4σ, δ=1σ, S_min=half synthesized beam; σ from 50 random beam-sized areas  
  > "We required parent structures (trunks) in the dendrogram to have a minimum intensity $F_{\rm min}$ of $4\sigma$." (Core Identification)
   - fitting: _not stated_
   - validation: Varied F_min (3,4,5σ) and S_min (0.5,1 beam): 128-293 cores, alpha 0.94-1.10  
  > "For the true CMF, $M_{\rm{min}}$ typically ranged between 3 and $8\:M_{\odot}$ with $\alpha$’s between 0.94 and 1.10." (Effects of Dendrogram Parameters)
2. **Estimate core masses**: optically thin dust emission mass from integrated flux  
  > "We estimated masses of cores by assuming optically thin thermal emission from dust, as in Papers I and II." (Core Mass Estimation)
   - assumption: Td=20 K; kappa_1.3mm,d=0.899 cm2/g; gas-to-dust 141; Hi-GAL distances  
  > "In the absence of measurements of temperature for each source, we assumed dust temperatures $T_{d} =$ 20 K." (Core Mass Estimation)
   - fitting: _not stated_
   - validation: Temperature 15 K or 30 K changes masses by factors 1.48 and 0.604  
  > "If temperatures of 15 K or 30 K were to be adopted, the mass estimates would differ by factors of 1.48 and 0.604, respectively." (Core Mass Estimation)
3. **Apply flux and number completeness corrections and build CMF**: median f_flux and f_num from artificial core insertion as function of flux/σ; five bins per dex, Poisson errors  
  > "with all bins equal in size in $\Delta \rm{log_{10}}M$ with five bins per dex, and a bin centered on 1 $M_{\odot}$." (Construction of the CMF)
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit single power laws and find optimal M_min**: WLS, MLE (unbinned) and MLE-B (binned); M_min chosen via KS and Anderson-Darling distance; bootstrap p-values with 3000 synthetic CMFs  
  > "We then repeated this procedure $N=3000$ times, i.e., with 3000 different synthetic CMFs for each $M_{\rm min}$" (Single Power-Law Fits)
   - software: powerlaw
   - parameter: best fit chosen at lowest M_min with p>=0.10 from A^2  
  > "we report final “best” fits that begin at the lowest significant ($p \geq .10$) $M_{\rm min}$ value as assessed by $A^2$." (Single Power-Law Fits)
   - fitting: MLE following Clauset et al. 2009; binned MLE following Virkar & Clauset 2014  
  > "This method is based on that proposed by (cite: virkar_power-law_2014), with a log-likelihood function above some minimum bin $M_{\rm{min}}$ of the form:" (Results, Single Power-Law Fits to the CMF)
   - validation: bootstrap goodness-of-fit p-values  
  > "To circumvent this issue, correct $p$-values can instead be estimated via bootstrap resampling (cite: babu_goodness–fit_2004; clauset_power-law_2009)." (Results, Single Power-Law Fits to the CMF)
5. **Test for break with piecewise power laws**: non-linear WLS fits of single, double and triple PPL; AICc and Akaike weights vs M_min  
  > "we fit a single power-law, a double PPL, and a triple PPL by performing non-linear WLS regression." (PPL fits)
   - fitting: WLS, AICc  
  > "we fit a single power-law, a double PPL, and a triple PPL by performing non-linear WLS regression." (Results, PPL fits and evidence for a break in the CMF)
   - validation: Consistent transition from double to single PPL as M_min increases  
  > "We conclude that this consistent transition from a double to single power-law as $M_{\rm min}$ increases indicates the presence of a break" (PPL fits)
6. **Compare log-normal vs power law and CMFs between environments, clustering**: Vuong log-likelihood ratio, AICc; KS tests vs Papers I/II; MST Q parameter  
  > "For each clump, we calculated the dimensionless $Q$ parameter" (Spatial Distribution of Cores)
   - software: powerlaw, networkx
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **astrodendro** : core identification  
  > "We used the dendrogram algorithm (cite: rosolowsky_structural_2008) as implemented in the python package `astrodendro` to identify cores." (Core Identification)
- **powerlaw** : significance of log-normal vs power-law  
  > "The significance levels of this test were calculated through the `powerlaw` Python package (cite: alstott_powerlaw_2014)." (Comparison to log-normal)
- **networkx** : minimum spanning trees  
  > "which were generated using the Python package $\tt{networkx}$ (cite: SciPyProceedings_11)" (Spatial Distribution of Cores)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of cores | 222 | not stated | cores | 1 | We found 222 cores in total |
| True CMF power-law index above ~5 Msun | 0.94 | 0.08 | dimensionless | 4 | The best fit to the true CMF is $\alpha = 0.94 \pm 0.08$ above the bin with a lower limit of $M_{\rm{min}}$ $\sim 5.0 \ M_{\odot}$ ($p=.12$). |
| True CMF alpha, WLS, M>=0.79 Msun | 0.50 | 0.07 | dimensionless | 4 | True  /  WLS  /    0.79\*     /   0.50   /      0.07      / $<$.001 |
| True CMF alpha, MLE-B, M>=0.79 Msun | 0.60 | 0.05 | dimensionless | 4 | for the true CMF we derived $\alpha=0.60 \pm 0.05$ (via MLE-B) |
| Double PPL for true CMF: break mass | 15 | not stated | Msun | 5 | For the true CMF the best fit results are $M_{1} = 15 \: M_{\odot}$, $\alpha_1 = 0.11 \pm 0.12$, and $\alpha_2 = 1.29 \pm 0.26$. |
| Raw core mass range | 0.04-252, median 3.0 | not stated | Msun | 2 | “Raw” masses ranged from 0.04 to 252 $M_{\odot}$ with a median mass of 3.0 $M_{\odot}$. |
| Q parameter range for clumps with >=10 cores | 0.64-0.82 | not stated | dimensionless | 6 | with values of $Q$ ranging from 0.64 to 0.82 |

## Qualitative findings

- Massive protocluster CMF has more high-mass cores than G286 and IRDC CMFs; attributed to higher clump surface density  
  > "Thus, we conclude that this difference in environmental conditions is the factor that is most likely to be responsible for the variation in the observed CMFs." (Comparison of CMFs)

## Claim tuples

- H: Does the massive protocluster CMF show a break in power-law behavior? | E: Single vs piecewise power-law fits with AICc and KS/AD M_min analysis | R: Double PPL preferred for M_min~1 Msun, single power law above ~5 Msun | F: A break exists between ~5 and 15 Msun | **supported**
- H: Is the high-mass CMF consistent with the Salpeter-like IMF slope? | E: Power-law fit above M_min~5 Msun | R: alpha=0.94±0.08 | F: Shallower than Salpeter 1.35 | **supported**
- H: Does the CMF differ among environments? | E: KS tests vs G286 and IRDC true CMFs for M>=0.79 Msun | R: p<0.001 for both | F: Massive protocluster CMF is more top-heavy | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Log-normal fit to true CMF not preferred over double PPL (w=0.03 vs 0.85)  
  > "for the true CMF a log-normal fit was not the best description ($w_{i}$(AIC)$_{\rm{ln}}=0.03$) and a double PPL was preferred" (Comparison to log-normal)
- How they decided it was enough: _not stated_
- Limitation (authors): Masses uncertain due to assumed 20 K temperature and no local background correction  
  > "The core masses we report have significant uncertainties due to no correction being made for the local backgrounds within which the cores are embedded, and also from a lack of temperature information on the scales of the cores." (Discussion and Conclusions)
- Caveat (inferred, ours): Low-mass number corrections large and uncertain
- Caveat (inferred, ours): Single temperature for all cores
- Caveat (inferred, ours): Sample not complete or necessarily unbiased
- Caveat (inferred, ours): Poisson uncertainties underestimate the true errors

## Reproducibility

- Data public (paper): Data delivered to the ALMA archive  
  > "had 12m-array observations delivered to the *ALMA* archive by May 2020" (Source Selection)
- Products in archive: _not stated_
- Missing: Imaging parameters and exact images used
- Missing: Correction curve tables
- Missing: Analysis code
- Data volume (inferred): Tens of GB (28 pointings of continuum images)
- Score (inferred): 3/5, Methods and statistics are described in detail and the core table is given, but imaging details and correction curves are not provided.
- Rediscovery candidate: yes, Public archive data, the recipe is largely specified, and results are numeric (alpha, break mass, core table).

## Links

- Method: (cite: cheng_core_2018) (Paper I methods for CMF and completeness corrections)
- Method: (cite: liu_core_2018) (Paper II methods for non-primary-beam corrected identification)
- Method: (cite: clauset_power-law_2009) (MLE power-law fitting and bootstrap)
- Companion: (cite: cheng_core_2018) (G286 CMF)
- Companion: (cite: liu_core_2018) (IRDC CMF)
- Related: ALMAGAL
- Related: Hi-GAL

## Checks

```json
{
 "quotes": 49,
 "quotes_ok": 49,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 37,
  "rate": 0.481
 },
 "evidence_ok": true
}
```
