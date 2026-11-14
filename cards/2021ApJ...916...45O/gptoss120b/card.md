# The Core Mass Function across Galactic Environments. III. Massive Protoclusters

`2021ApJ...916...45O` | The Astrophysical Journal 2021 | first author: O'Neill, Theo J. | arXiv: 2104.08861 | DOI: 10.3847/1538-4357/ac062d | **HELD OUT (benchmark)**

Card schema 1.0 | model gpt-oss-120b | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: What is the shape of the core mass function in massive protoclusters within 3.5 kpc?  
  > "Here we measure the CMF in 28 dense clumps within 3.5 kpc that are likely to be central regions of massive protoclusters, observed via $1.3\:{\rm{mm}}$ dust continuum emission by the ALMAGAL project." (Abstract)
- Target **G18.30**: coordinates l=18.30268°, b=-0.38638°  
  > "| G18.30 | 82445 | 9393 | 18.30268 | -0.38638 | 2.96 | 0.18 | 946 | 1.87 | 2 | 0.39 | 5 |" (Table 1); z/distance 2.96 kpc  
  > "| G18.30 | 82445 | 9393 | 18.30268 | -0.38638 | 2.96 | 0.18 | 946 | 1.87 | 2 | 0.39 | 5 |" (Table 1); distance from Table 1  
  > "| G18.30 | 82445 | 9393 | 18.30268 | -0.38638 | 2.96 | 0.18 | 946 | 1.87 | 2 | 0.39 | 5 |" (Table 1)

## Data provenance

- ALMA projects: 2019.1.00195.L
- bands: Band 6 (1.3 mm)  
  > "observed via $1.3\:{\rm{mm}}$ dust continuum emission" (Abstract)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: 0.30 mJy beam^{-1}  
  > "The median value of $\sigma$ was 0.30 mJy $\textrm{beam}^{-1}$." (Core Identification)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: PI: S. Molinari  
  > "ALMAGAL: ALMA Evolutionary Study of High Mass Protocluster Formation in the Galaxy” (PI: S. Molinari)." (Source Selection)
- External data: clump radius, mass, and surface density  
  > "The radius, mass, $\Sigma_{\rm cl}$, and type were derived by (cite: elia_hi-gal_2017)" (Table 1) [from (cite: elia_hi-gal_2017)]

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

- core identification method using dendrogram  
  > "To identify cores, we followed the methods used in our studies of the G286 protocluster (Paper I) and IRDCs (Paper II)" (Core Identification) [from Paper I and Paper II]
- core mass estimation assuming optically thin dust  
  > "We estimated masses of cores by assuming optically thin thermal emission from dust, as in Papers I and II." (Core Mass Estimation) [from Paper I and Paper II]
- completeness correction methodology  
  > "In Papers I and II, we derived correction factors to estimate a complete, “true”, CMF from an observed “raw” CMF." (Core Flux Recovery and Completeness Corrections) [from Paper I and Paper II]

### Not stated but needed to reproduce (our reading)

- Imaging weighting robust parameter
- uv taper settings
- cell size and image size for tclean
- primary beam correction flag
- self‑calibration solution interval and number of iterations
- CASA version used for calibration and imaging
- exact spectral setup (spectral windows, channel widths)

## Analysis recipe

1. **identify cores**: dendrogram algorithm with F_min=4σ, δ=1σ, S_min=0.5 beam  
  > "We required parent structures (trunks) in the dendrogram to have a minimum intensity $F_{\rm min}$ of $4\sigma$. We also required substructures (*branches* and *leaves*) to have a minimum increase in intensity $\delta$ of $1\sigma$ and a minimum area $S_{\rm{min}}$ of half the synthesized beam" (Core Identification)
   - software: astrodendro
   - parameter: F_min = 4σ  
  > "minimum intensity $F_{\rm min}$ of $4\sigma$" (Core Identification)
   - parameter: δ = 1σ  
  > "minimum increase in intensity $\delta$ of $1\sigma$" (Core Identification)
   - parameter: S_min = 0.5 beam  
  > "minimum area $S_{\rm{min}}$ of half the synthesized beam" (Core Identification)
   - assumption: cores are the leaves of the dendrogram  
  > "We defined cores as the leaves of the dendrogram." (Core Identification)
   - fitting: _not stated_
   - validation: comparison with previous papers’ core catalogs  
  > "To identify cores, we followed the methods used in our studies of the G286 protocluster (Paper I) and IRDCs (Paper II)" (Core Identification)
2. **estimate core masses**: optically thin dust emission conversion using κ=0.899 cm^2 g^{-1}, gas‑to‑dust ratio 141, T_d=20 K  
  > "We assumed an opacity per unit dust mass $\kappa_{\rm 1.3mm,d}=0.899\: {\rm cm^2 \ g}^{-1}$ ... using a gas‑to‑refractory‑component‑dust ratio of 141" (Core Mass Estimation); "In the absence of measurements of temperature for each source, we assumed dust temperatures $T_{d} =$ 20 K." (Core Mass Estimation)
   - parameter: κ_{1.3mm}=6.38×10^{-3} cm^2 g^{-1}  
  > "which results in $\kappa_{\rm 1.3mm}= {\rm 6.38\times10^{-3}\:cm^2\:g}^{-1}$" (Core Mass Estimation)
   - parameter: T_d = 20 K  
  > "In the absence of measurements of temperature for each source, we assumed dust temperatures $T_{d} =$ 20 K." (Core Mass Estimation)
   - assumption: optically thin thermal dust emission  
  > "We estimated masses of cores by assuming optically thin thermal emission from dust" (Core Mass Estimation)
   - fitting: _not stated_
   - validation: consistency with previous Papers I and II mass estimates  
  > "as in Papers I and II" (Core Mass Estimation)
3. **derive flux and number recovery fractions**: insert artificial cores of varying mass into real images and recover with the same dendrogram parameters  
  > "Artificial cores of varying masses were randomly inserted into real clump images to estimate the amount of the flux typically detected by the dendrogram algorithm" (Core Flux Recovery and Completeness Corrections)
   - parameter: range of inserted core masses  
  > "Artificial cores of varying masses were randomly inserted into real clump images" (Core Flux Recovery and Completeness Corrections)
   - fitting: _not stated_
   - validation: median values of f_flux and f_num adopted for the whole sample  
  > "We adopted the median values of these factors as universal values with which to correct our observed “raw” CMFs" (Core Flux Recovery and Completeness Corrections)
4. **apply completeness corrections to obtain the “true” CMF**: multiply each core mass by f_flux and adjust number counts by f_num  
  > "We applied $f_{\rm{flux}}$ corrections to each core, which increased all masses... and used $f_{\rm{num}}$ to create a final “true” CMF" (Core Flux Recovery and Completeness Corrections)
   - fitting: _not stated_
   - validation: comparison of corrected CMF shape with raw CMF  
  > "The number correction yields a significantly increased population of low mass ($\lesssim 1 M_{\odot}$) cores in the true CMF." (Results)
5. **fit power‑law(s) to the CMF**: weighted least squares (WLS) and maximum likelihood estimation (MLE, MLE‑B) over mass range M≥0.79 M⊙  
  > "We fit a power law of the form of Equation ([\eq:pl]) to the binned raw, flux‑corrected and true CMFs." (Single Power‑Law Fits to the CMF); "We first adopt $M_{\rm{min}}$ $=0.79$ $M_{\odot}$ (corresponding to the bin centered at $1\:M_{\odot}$)." (Single Power‑Law Fits to the CMF)
   - parameter: M_min = 0.79 M⊙  
  > "$M_{\rm{min}}$ $=0.79$ $M_{\odot}$" (Single Power‑Law Fits to the CMF)
   - parameter: bins per dex = 5  
  > "five bins per dex" (Construction of the CMF)
   - assumption: Poisson counting uncertainties  
  > "We assumed $\textit{N}^{1/2}$ Poisson counting uncertainties for each bin." (Construction of the CMF)
   - fitting: WLS, MLE (unbinned), MLE‑B (binned)  
  > "The MLE type is a fit to the unbinned sample of cores, while MLE‑B type is a fit to a binned histogram of the data." (Single Power‑Law Fits to the CMF)
   - validation: p‑values from KS, AD statistics and AIC comparisons  
  > "The single power law best fit to the true CMF is then $\alpha=0.94 \pm 0.08$" (Results)
6. **search for a break in the CMF**: evaluate KS and Anderson‑Darling statistics as a function of M_min, bootstrap synthetic CMFs, and compare AIC for single vs. double vs. triple piecewise power‑laws  
  > "We varied the parameters used to identify cores with the dendrogram to test the effects on our results." (PPL fits and evidence for a break in the CMF); "We calculated the fraction of synthetic values of $\hat{D}$ or $\hat{A}^2$ that were larger than the original $D$ or $A^2$ fit to the real CMF and we estimate a $p$‑value" (PPL fits and evidence for a break in the CMF)
   - software: powerlaw
   - fitting: AIC and AICc model selection  
  > "The Akaike Information Criterion (AIC) can be used to choose a best fit model" (PPL fits and evidence for a break in the CMF)
   - validation: break mass identified between ~5 and 15 M⊙ with p≥0.10 for single power‑law above that mass  
  > "we find evidence of a break in this power‑law behavior between $\sim5$ and $15\:M_{\odot}$" (Abstract)
7. **compare CMF with previous environments and with the IMF**: Kolmogorov‑Smirnov tests and visual comparison of CMFs  
  > "We performed Kolmogorov‑Smirnov tests comparing CMFs from our previous studies in G286 and IRDCs to the CMF derived here" (Comparison of CMFs in Different Environments and Implications for Massive Star Formation)
   - fitting: _not stated_
   - validation: significant differences (p < .001) found  
  > "The true CMF is significantly different than the true CMFs of Paper I ($p < .001$) and Paper II ($p < .001$)." (Comparison of CMFs in Different Environments and Implications for Massive Star Formation)
8. **analyse spatial distribution of cores**: minimum spanning tree (MST) analysis and Q‑parameter calculation using networkx  
  > "The resulting MSTs, which were generated using the Python package $\tt{networkx}$ (cite: SciPyProceedings_11), are shown in Figure [9]" (Spatial Distribution of Cores)
   - software: networkx
   - fitting: _not stated_
   - validation: Q values between 0.64 and 0.82 indicating lack of strong central concentration  
  > "We found little evidence for centrally condensed structures in these regions, with values of $Q$ ranging from 0.64 to 0.82" (Spatial Distribution of Cores)

## Software

- **astrodendro** : core identification via dendrogram algorithm  
  > "We used the dendrogram algorithm (cite: rosolowsky_structural_2008) as implemented in the python package `astrodendro` to identify cores." (Core Identification)
- **networkx** : minimum spanning tree and Q‑parameter calculation  
  > "The resulting MSTs, which were generated using the Python package $\tt{networkx}$ (cite: SciPyProceedings_11), are shown in Figure [9]." (Spatial Distribution of Cores)
- **powerlaw** : likelihood‑ratio test between power‑law and log‑normal fits  
  > "The significance levels of this test were calculated through the `powerlaw` Python package (cite: alstott_powerlaw_2014)." (Comparison of log‑normal distributions)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| number_of_cores_identified | 222 | not stated | dimensionless | 1 | We found 222 cores in total |
| raw_mass_median | 3.0 | not stated | M_⊙ | 4 | “Raw” masses ranged from 0.04 to 252 $M_{\odot}$ with a median mass of 3.0 $M_{\odot}$. |
| corrected_mass_median | 4.6 | not stated | M_⊙ | 4 | resulted in a new median mass of 4.6 $M_{\odot}$ |
| raw_surface_density_median | 1.5 | not stated | g cm^{-2} | 4 | We find a median values of $\Sigma_c =1.5$ g cm$^{-2}$. |
| corrected_surface_density_median | 2.6 | not stated | g cm^{-2} | 4 | new median $\Sigma_c = 2.6$ g cm$^{-2}$. |
| power_law_index_true_CMF | 0.94 | 0.08 | dimensionless | 5 | with $\alpha\simeq0.94\pm0.08$. |
| break_mass_range | 5-15 | not stated | M_⊙ | 6 | we find evidence of a break in this power‑law behavior between $\sim5$ and $15\:M_{\odot}$ |
| power_law_index_true_CMF_MLE_B | 0.60 | 0.05 | dimensionless | 5 | we derived $\alpha = 0.60 \pm 0.05$ for $M \geq 0.79 \ M_{\odot}$. |
| power_law_index_G286 | 1.45 | 0.15 | dimensionless | 7 | we derive $\alpha = 1.45 \pm 0.15$ for G286 when $M \geq 0.79 \ M_{\odot}$ |
| power_law_index_IRDCs | 1.03 | 0.07 | dimensionless | 7 | $\alpha = 1.03 \pm 0.07$ for the sample of IRDCs for $M \geq \ 0.79 \ M_{\odot}$ |

## Qualitative findings


## Claim tuples

- H: The core mass function (CMF) in massive protoclusters differs from that in less massive or more distant environments. | E: Measured the CMF in 28 clumps within 3.5 kpc using ALMA 1.3 mm continuum, applied completeness corrections, and fitted power‑law models. | R: Derived a shallow power‑law index $\alpha = 0.94 \pm 0.08$ for $M \gtrsim 5\,M_{\odot}$ and identified a break between $\sim5$ and $15\,M_{\odot}$; the CMF contains a larger fraction of high‑mass cores than in G286 or IRDC samples. | F: The CMF in massive protoclusters is significantly different and more top‑heavy, indicating an environmental effect. | **supported**
- H: A single power‑law does not adequately describe the CMF over the full mass range. | E: Fitted single power‑law and piecewise power‑law models; evaluated KS, AD, and AIC statistics across varying $M_{\rm min}$. | R: Single power‑law fits have low $p$‑values below $\sim5\,M_{\odot}$; double piecewise power‑law is preferred for $M_{\rm min}\lesssim5\,M_{\odot}$. | F: There is a statistically significant break in the CMF, requiring at least a double power‑law description. | **supported**
- H: The CMF in massive protoclusters is top‑heavy relative to the stellar IMF. | E: Compared the derived CMF slope to the Salpeter IMF slope ($\alpha=1.35$). | R: CMF slope $\alpha=0.94\pm0.08$ is significantly shallower than the Salpeter value. | F: The CMF is top‑heavy, implying a higher proportion of massive cores. | **supported**

## Reasoning

- Why this data: to probe down to relatively low core masses (∼1 M⊙) in distant massive clumps  
  > "To be able to probe down to relatively low core masses, i.e., $\sim1\:M_\odot$, we limited our analysis to sources within 3.5 kpc" (Source Selection)
- Why this method: to enable direct comparison with previous Papers I and II  
  > "To identify cores, we followed the methods used in our studies of the G286 protocluster (Paper I) and IRDCs (Paper II)" (Core Identification)
- Alternative: use of clumpfind algorithm instead of dendrogram  
  > "We note that the effects of using the `clumpfind` algorithm (cite: williams_determining_1994) instead of the dendrogram method were explored in Paper I, and we do not repeat this analysis here." (Core Identification)
- How they decided it was enough: _not stated_
- Limitation (authors): core masses uncertain due to assumed uniform temperature of 20 K  
  > "In the absence of measurements of temperature for each source, we assumed dust temperatures $T_{d} =$ 20 K." (Core Mass Estimation)
- Limitation (authors): no correction for local background emission  
  > "The core masses we report have significant uncertainties due to no correction being made for the local backgrounds within which the cores are embedded" (Discussion and Conclusions)
- Caveat (inferred, ours): Uncertainties in temperature and background subtraction may bias core mass estimates.
- Caveat (inferred, ours): Lack of detailed imaging parameters (robust weighting, cell size) hampers exact reproduction of continuum images.

## Reproducibility

- Data public (paper): yes  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA\#2019.1.00195.L." (Acknowledgements)
- Products in archive: yes  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA\#2019.1.00195.L." (Acknowledgements)
- Code: _not stated_
- Missing: CASA version and pipeline details
- Missing: tclean parameters (robust, cell size, image size, deconvolver)
- Missing: self‑calibration strategy (if any)
- Missing: exact uv‑taper or weighting applied
- Data volume (inferred): not stated
- Score (inferred): 7/5, ALMA data are central and most processing steps are described, but key imaging parameters and calibration details are missing, limiting full reproducibility.
- Rediscovery candidate: yes, All raw ALMA data are publicly archived, the analysis workflow (core identification, mass estimation, completeness corrections, fitting) is described with enough quantitative detail to reproduce the main numeric results (e.g., α=0.94±0.08, break at 5‑15 M⊙).

## Links

- Method: (cite: cheng_core_2018) (provides the core identification and mass estimation methodology used as baseline)
- Method: (cite: liu_core_2018) (describes the completeness correction approach adopted)
- Related: ALMAGAL

## Checks

```json
{
 "quotes": 70,
 "quotes_ok": 54,
 "quote_pass_rate": 0.771,
 "quotes_too_long": 1,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 89,
  "stated": 50,
  "rate": 0.562
 },
 "evidence_ok": false
}
```
