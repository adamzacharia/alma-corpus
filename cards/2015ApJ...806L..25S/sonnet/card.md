# ALMA Detected Overdensity of Sub-millimeter Sources Around WISE/NVSS-selected z ~ 2 Dusty Quasars

`2015ApJ...806L..25S` | The Astrophysical Journal Letters 2015 | first author: Silva, Andrea | arXiv: 1505.05160 | DOI: 10.1088/2041-8205/806/2/L25

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: Are the fields around WISE/NVSS-selected hyper-luminous dusty z~2 quasars overdense in sub-mm galaxies relative to blank-field counts?  
  > "we compute the sub-mm galaxy source counts in the near vicinity of 49 *WISE*/NVSS-selected $z\sim$2, dusty, hyper-luminous" (Introduction)
- Target **49 WISE/NVSS-selected dusty quasars**: coordinates see Table 1 (field names)  
  > "Optical spectroscopic redshifts are available for 43 of the 49 ALMA sources and range from $\sim$ 0.47 – 2.85, with a mean redshift of $\langle z\rangle$ = 1.69." (3 Observations & Data Reduction); z/distance z ~0.47-2.85, mean 1.69  
  > "Optical spectroscopic redshifts are available for 43 of the 49 ALMA sources and range from $\sim$ 0.47 – 2.85, with a mean redshift of $\langle z\rangle$ = 1.69." (3 Observations & Data Reduction); distance from optical spectroscopic redshifts (L15)  
  > "Optical spectroscopic redshifts are available for 43 of the 49 ALMA sources and range from $\sim$ 0.47 – 2.85, with a mean redshift of $\langle z\rangle$ = 1.69." (3 Observations & Data Reduction)

## Data provenance

- ALMA projects: _none stated_
- bands: Band 7 (345 GHz), 8 GHz bandwidth  
  > "the observations were conducted in Band 7 (345 GHz) with an 8 GHz bandwidth." (3 Observations & Data Reduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 15, 19, 23 antennas  
  > "The different number of antennae available (15, 19, and 23, respectively)" (3 Observations & Data Reduction)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.24'', 0.55'', 0.45'' for the three runs  
  > "the synthesized beamsizes are 1.24$''$, 0.55$''$, and 0.45$''$ for each run." (3 Observations & Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: rms 0.60, 0.30, 0.32 mJy/beam  
  > "which are respectively: 0.60, 0.30, and 0.32 mJy beam$^{-1}$" (3 Observations & Data Reduction)
- time on source: ~1.5 min per object  
  > "The time on source was $\sim$ 1.5 min per object." (3 Observations & Data Reduction)
- observing dates: 2011 Nov 16 (23 sources), 2012 May 25 (14), 2012 Aug 28 (12)  
  > "twenty-three sources on November 16 2011, fourteen on May 25 2012, and twelve on August 28 2012." (3 Observations & Data Reduction)
- pi or archival as stated: _not stated_
- Other facility **WISE and NVSS**: sample selection (22 um and 1.4 GHz)  
  > "selected on the basis of *WISE* 22 $\mu$m and NVSS 1.4 GHz detection" (2 Sample selection)
- External data: Sample selection, redshifts and central-source properties  
  > "Full details on the sample selection are given in L15." (2 Sample selection) [from Lonsdale et al. 2015, submitted (L15)]
- External data: Literature source counts and models for comparison  
  > "We compare our counts with those expected from models (cite: shimizu2012; hayward2013; dacunha2013)" (4.3 Source Counts) [from shimizu2012; hayward2013; dacunha2013; karim2013; hatsukade2013; ono2014; jones2015]

## Processing

### Calibration

- pipeline or manual: standard procedures in CASA  
  > "The data were reduced using standard procedures and the Common Astronomy Software, casa (cite: mcmullin2007)." (3 Observations & Data Reduction)
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
- image size: pixel size 0.1'' (low-rms fields) vs 0.25'' (high-rms)  
  > "A change in pixel size from 0.1$''$ to 0.25$''$ in the lower-rms fields (thus matching the higher-rms fields) does not affect our results." (footnote 3)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: F_pbc = F0 exp(4 ln2 d^2/theta^2); primary beam 18.2''  
  > "$F_{pbc}=F_{0}\exp\left(4\ln(2)\frac{d^2}{\theta^2}\right)$" (footnote 5)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Observations and data reduction details  
  > "For further details on the observations and data reduction see L15." (3 Observations & Data Reduction) [from L15 (Lonsdale et al. 2015, submitted)]
- Source-count method  
  > "by following the method described in (cite: ono2014)" (4.3 Source Counts) [from (cite: ono2014)]

### Not stated but needed to reproduce (our reading)

- tclean/clean parameters (weighting, robust, deconvolver, threshold)
- CASA version
- project code(s) and calibrators
- SExtractor detection parameters and thresholds
- imfit settings
- deboosting procedure details
- uv range/self-calibration

## Analysis recipe

1. **find field sources**: SExtractor >2 sigma detection in positive and negative maps within primary beam, excluding 1.5'' central region; threshold 3.75 sigma  
  > "use SExtractor (cite: bertin1996) to find all $>$2$\sigma$ “sources" in both our positive and negative maps." (4.1 Identifying field sources)
   - software: SExtractor, CASA imfit
   - parameter: threshold 3.75 sigma; high-confidence 5.25 sigma in low-rms fields  
  > "we only keep sources with SNR$>$ 5.25$\sigma$ in these lower-rms fields" (4.1 Identifying field sources)
   - fitting: _not stated_
   - validation: spurious fraction from negative sources: 42% (rms 0.3) and 12% (0.6)  
  > "The result is a spurious fraction of 42% and 12% for images with rms of 0.3 and 0.6 mJy beam$^{-1}$, respectively." (4.1 Identifying field sources)
2. **compute integral source counts**: N(>S)=sum (1-fc)/(C*A_T), completeness from 50 injected sources x1000 trials  
  > "calculated by injecting 50 artificial sources at random positions in an image where all sources with SNR$\geq$3.0 are removed." (4.3 Source Counts)
   - assumption: literature counts converted to 870 um with modified blackbody beta=1.5, Td=35 K, z=2.5  
  > "assuming $\beta$ = 1.5, $T_{d}=35K$ and $z=2.5$" (4.3 Source Counts)
   - fitting: _not stated_
   - validation: compared primary and high-confidence samples; flux boosting checked via injected sources  
  > "The results are consistent with each other suggesting the details of the serendipitous sample selection do not significantly affect our conclusions." (4.3 Source Counts)

## Software

- **CASA** : data reduction and imfit flux measurement  
  > "we measure flux densities and associated uncertainties of all SExtractor-selected sources using imfit in casa." (4.1 Identifying field sources)
- **SExtractor** : source finding  
  > "use SExtractor (cite: bertin1996) to find all $>$2$\sigma$ “sources"" (4.1 Identifying field sources)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| additional SMGs | 23 sources in 17 fields | not stated | count | 1 | Using this threshold, we detect 23 sources in 17 fields |
| high-confidence sample | 10 sources in 10 fields | not stated | count | 1 | This leaves us with a total of 10 sources spread among 10 fields. |
| overdensity vs blank field | ~10 | not stated | dimensionless | 2 | The measured 870 $\mu$m source counts are $\sim$ 10 $\times$ expectations for unbiased regions |

## Qualitative findings

- No evidence of angular clustering toward the central source; tentative dearth of SMGs near centre (~2 sigma)  
  > "the significance of this result is only $\sim$ 2$\sigma$ and needs further investigation before it is conclusive." (4.2 Angular distribution of serendipitous sources)

## Claim tuples

- H: Fields of dusty WISE/NVSS quasars are overdense in SMGs | E: Source counts in 49 ALMA 345 GHz fields vs blank-field counts and models | R: ~10x excess, ~5 sigma vs closest model | F: Such quasars probe high-density peaks | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): High spurious fraction in low-rms fields; sub-sample lacks most radio-loud sources  
  > "the spurious source fraction (as implied by the presence of “negative" sources above this SNR threshold) is non-negligible." (4.1 Identifying field sources)
- Caveat (inferred, ours): Redshifts of serendipitous SMGs unknown, so association with quasars unconfirmed
- Caveat (inferred, ours): Very short integrations (~1.5 min) give low S/N and large spurious fractions
- Caveat (inferred, ours): Blank-field comparison counts at 870 um depend on converted literature values

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: project code not printed in text
- Missing: imaging parameters
- Missing: source-finding parameters
- Missing: L15 details
- Data volume (inferred): small, ~tens of GB
- Score (inferred): 3/5, Archival data, simple method, but imaging and extraction parameters and project code not given.
- Rediscovery candidate: no, Recipe incomplete and project code not printed.

## Links

- Method: (cite: ono2014) (source-count method)
- Companion: Lonsdale et al. 2015 (L15) (sample and observation details)
- Companion: (cite: jones2015) (SCUBA overdensity comparison)
- Related: WISE
- Related: NVSS

## Checks

```json
{
 "quotes": 33,
 "quotes_ok": 33,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00397.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 60,
  "stated": 28,
  "rate": 0.467
 },
 "evidence_ok": true
}
```
