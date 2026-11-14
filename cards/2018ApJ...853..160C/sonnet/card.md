# The Core Mass Function in the Massive Protocluster G286.21+0.17 Revealed by ALMA

`2018ApJ...853..160C` | The Astrophysical Journal 2018 | first author: Cheng, Yu | arXiv: 1706.06584 | DOI: 10.3847/1538-4357/aaa3f1

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: What is the core mass function of the massive protocluster G286.21+0.17 from 1.3 mm ALMA continuum, and how does it compare with the Salpeter IMF and depend on core-finding method?  
  > "We measure the CMF in the central region, exploring various core detection algorithms, which give source numbers ranging from 60 to 125, depending on parameter selection." (abstract)
- Target **G286.21+0.17**: coordinates RA=10:38:33, Dec=-58:19:22 (field center)  
  > "G286.21+0.17 (hereafter G286) is a massive protocluster associated with the $\eta$ Car giant molecular cloud at a distance of $2.5\pm0.3\:$kpc" (1 Introduction); "The position of field center is R.A.=10:38:33, decl.=-58:19:22." (2.1 Observational Set-Up); z/distance 2.5±0.3 kpc  
  > "G286.21+0.17 (hereafter G286) is a massive protocluster associated with the $\eta$ Car giant molecular cloud at a distance of $2.5\pm0.3\:$kpc" (1 Introduction); "The position of field center is R.A.=10:38:33, decl.=-58:19:22." (2.1 Observational Set-Up); distance from Barnes et al. 2010; Andersen et al. 2017  
  > "G286.21+0.17 (hereafter G286) is a massive protocluster associated with the $\eta$ Car giant molecular cloud at a distance of $2.5\pm0.3\:$kpc" (1 Introduction); "The position of field center is R.A.=10:38:33, decl.=-58:19:22." (2.1 Observational Set-Up)

## Data provenance

- ALMA projects: 2015.1.00357.S
- bands: Band 6 (230 GHz, 1.3 mm)  
  > "Here we present the ALMA Band 6 (230 GHz) continuum observation of G286" (1 Introduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: 2.0 GHz total, centered 231.00 GHz (SPW1)  
  > "The second baseband SPW1 was set to $231.00\:$GHz, i.e., 1.30 mm, to observe continuum with a total bandwidth of $2.0\:$GHz." (2.1 Observational Set-Up)
- arrays: 12-m array and 7-m array (plus total power for lines)  
  > "Additionally, a 35-pointing mosaic was performed for each strip using the 7-m array, probing scales up to 18.6$''$." (2.1 Observational Set-Up)
- configurations: 12-m C36-1; extra coverage from C37/C38-1 transition for two strips  
  > "We employed the compact configuration C36-1 to recover scales between 1.5$''$ and 11.0$''$." (2.1 Observational Set-Up)
- baselines: _not stated_
- angular resolution: ~1.0'' (2500 au) high-res; 1.62''x1.41'' with taper; 7-m 7.32''x4.42''  
  > "which results in a resolution of 1.07$''$$\times$1.02$''$." (2.1 Observational Set-Up)
- max recoverable scale: ~20'' combined (7-m up to 18.6'')  
  > "The image combining all data has a spatial dynamic range that recovers structures from $\sim1\ensuremath{''}$ to $\sim20\ensuremath{''}$." (3.1 1.3 mm Continuum Image)
- sensitivity: 1σ 0.45 mJy/beam in central strip; 0.2–0.46 mJy/beam range  
  > "The $1\sigma$ noise of the central strip is $0.45\:{\rm{mJy}}\:{\rm{beam}}^{-1}$." (2.1 Observational Set-Up)
- time on source: _not stated_
- observing dates: Dec. 2015 to Sept. 2016  
  > "during a period from Dec. 2015 to Sept. 2016" (2.1 Observational Set-Up)
- pi or archival as stated: _not stated_
- Line: N2D+ 3-2 (231.32 GHz)
- Line: C18O 2-1 (219.56 GHz)
- External data: Dust opacity 0.899 cm2/g at 1.3 mm (Ossenkopf & Henning moderately coagulated thin ice mantle model)  
  > "(moderately coagulated thin ice mantle model of Ossenkopf & Henning 1994)" (2.3 Core Mass Estimation) [from Ossenkopf & Henning 1994]
- External data: Gas-to-refractory-dust ratio of 141  
  > "using a gas-to-refractory-component-dust ratio of 141 (Draine 2011)" (2.3 Core Mass Estimation) [from Draine 2011]

## Processing

### Calibration

- pipeline or manual: ALMA data reduction pipeline  
  > "Both the 7-m and 12-m array data were calibrated with the data reduction pipeline using *Casa* 4.7.0." (2.1 Observational Set-Up)
- casa version: CASA 4.7.0  
  > "Both the 7-m and 12-m array data were calibrated with the data reduction pipeline using *Casa* 4.7.0." (2.1 Observational Set-Up)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean in CASA; all five strips combined into one mosaic  
  > "We performed imaging with *tclean* task in *Casa* and during cleaning we combined data for all five strips to generate a final mosaic map." (2.1 Observational Set-Up)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5  
  > "The 7-m array data was imaged using a Briggs weighting scheme with a robust parameter of 0.5" (2.1 Observational Set-Up)
- uv taper: 0.6'' uvtaper for 1.62''x1.41'' image; smaller taper (value not given) for 1.07''x1.02''  
  > "we also apply a 0.6$''$ *uvtaper* to suppress longer baselines, which results in $1.62\ensuremath{''}\times1.41\ensuremath{''}\:$ resolution." (2.1 Observational Set-Up)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: continuum built from all line-free channels (ranges not given)  
  > "The continuum visibility data was constructed with all line-free channels." (2.1 Observational Set-Up)
- primary beam correction: _not stated_
- array combination: 12-m and 7-m data combined in tclean  
  > "For the combined data, we used the same Briggs parameter." (2.1 Observational Set-Up)
- smoothing: _not stated_
- final beam: 1.07''x1.02'' (high-res)  
  > "which results in a resolution of 1.07$''$$\times$1.02$''$." (2.1 Observational Set-Up)
- final rms: 0.45 mJy/beam (high-res image)  
  > "The 1$\sigma$ noise level in this image is $0.45\:{\rm{mJy}}\:{\rm{beam}}^{-1}$." (2.1 Observational Set-Up)

### Inherited from earlier work

- Dendrogram algorithm  
  > "The dendrogram algorithm is described by Rosolowsky et al. (2008) and implemented in *astrodendro*." (2.2.1 The Dendrogram Method) [from Rosolowsky et al. 2008]
- Clumpfind algorithm  
  > "The clumpfind algorithm (Williams et al. 1994) works by first contouring the data at a multiple of the rms noise of the observation" (2.2.2 The Clumpfind Method) [from Williams et al. 1994]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for continuum
- Taper value for the 1'' image
- Image size, cell size, masking, clean threshold and deconvolver
- Pixel/beam-size and primary-beam correction details
- Power-law fit procedure details (bin edges, error weighting)
- Clumpfind implementation used
- Exact flux and number correction functional forms
- Which scheduling blocks/execution blocks were used

## Analysis recipe

1. **Make continuum images**: Pipeline-calibrated 7-m and 12-m data imaged with tclean, Briggs weighting, with and without uvtaper  
  > "We performed imaging with *tclean* task in *Casa* and during cleaning we combined data for all five strips to generate a final mosaic map." (2.1 Observational Set-Up)
   - software: CASA
   - parameter: robust 0.5; 0.6'' uvtaper  
  > "we also apply a 0.6$''$ *uvtaper* to suppress longer baselines" (2.1 Observational Set-Up)
   - fitting: _not stated_
   - validation: _not stated_
2. **Identify cores**: Dendrogram (leaves) and clumpfind with fiducial Fmin=4σ, δ=1σ or Δ=3σ, Smin=0.5 beam; parameters varied  
  > "The fiducial dendrogram method ($F_{\rm min}=4\sigma$, $\delta=1\sigma$, $S_{\rm min}=0.5S_{\rm beam}$) identifies 76 cores" (3.2 The Core Population and CMF)
   - software: astrodendro, clumpfind
   - fitting: _not stated_
   - validation: Parameter variations, resolution and 12m-only tests  
  > "Our 12m only image has an rms noise level of 0.47 mJy beam$^{-1}$." (3.2 The Core Population and CMF)
3. **Derive core masses**: Optically thin dust emission: M = 0.192 (F/mJy)(d/2.5 kpc)^2 Msun  
  > "We estimate core masses by assuming optically thin thermal emission from dust." (2.3 Core Mass Estimation)
   - assumption: Td = 20 K uniform; kappa_1.3mm,d=0.899 cm2/g; gas-to-dust 141; d=2.5 kpc  
  > "for simplicity we have adopted an uniform value of $T_{d}=20\:$ K for all cores in our fiducial analysis." (2.3 Core Mass Estimation)
   - fitting: _not stated_
   - validation: Mass uncertainty about factor of two; 15 K and 30 K change masses by 1.48 and 0.604  
  > "Overall, we estimate absolute mass uncertainties of about a factor of two" (2.3 Core Mass Estimation)
4. **Completeness corrections**: Artificial core insertion (10 beam-shaped cores per run, 30 repeats) to get flux and number recovery fractions  
  > "In each experiment, we insert 10 cores (i.e., $\sim$10% of the total number to avoid excessive blending) of a given total flux" (2.4 Core Flux Recovery and Completeness Corrections)
   - assumption: Artificial cores have synthesized-beam shape; positions random scaled to 7-m flux profile  
  > "The artificial cores are assumed to have the same shape as the synthesized beam" (2.4 Core Flux Recovery and Completeness Corrections)
   - fitting: _not stated_
   - validation: _not stated_
5. **Fit CMF power law**: Power law dN/dlogM ∝ M^-α fit to bins above 0.8 Msun, 5 bins per dex, chi2 in log space  
  > "Our fitting method, which we note minimizes $\chi^2$ in log space, treats the empty bins as effective upper limits." (3.2 The Core Population and CMF)
   - fitting: chi2 minimization in log space; Poisson errors  
  > "Poisson counting errors are shown for each bin." (3.2 The Core Population and CMF)
   - validation: Excluding the ~100 Msun core, different mass ranges  
  > "if we were to exclude this source and fit the CMF only over the range from 0.8 to $\sim20\:M_\odot$" (3.2 The Core Population and CMF)

## Software

- **CASA** 4.7.0: Calibration pipeline and tclean imaging  
  > "Both the 7-m and 12-m array data were calibrated with the data reduction pipeline using *Casa* 4.7.0." (2.1 Observational Set-Up)
- **astrodendro** : Dendrogram core identification  
  > "The dendrogram algorithm is described by Rosolowsky et al. (2008) and implemented in *astrodendro*." (2.2.1 The Dendrogram Method)
- **clumpfind** : Core identification  
  > "The clumpfind algorithm (Williams et al. 1994) works by first contouring the data at a multiple of the rms noise of the observation" (2.2.2 The Clumpfind Method)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Fiducial dendrogram true CMF slope α (M>0.8 Msun) | 1.24 | 0.17 | dimensionless | 5 | while that for the fully (flux and number) corrected, i.e., “true”, CMF yields $\alpha=1.24\pm0.17$ |
| Fiducial clumpfind true CMF slope α | 0.64 | 0.13 | dimensionless | 5 | then we find $\alpha=0.64\pm0.13$ |
| Dendrogram raw CMF slope α | 1.11 | 0.20 | dimensionless | 5 | We find $\alpha=1.11\pm0.20$. |
| Number of cores, fiducial dendrogram | 76 | not stated | cores | 2 | identifies 76 cores, while the fiducial clumpfind method |
| Number of cores, fiducial clumpfind | 83 | not stated | cores | 2 | finds 83 cores |
| Dendrogram true CMF slope for M>0.3 Msun | 0.83 | 0.11 | dimensionless | 5 | we derive a moderately shallower value of $\alpha=0.83\pm0.11$ |
| Number of dendrogram cores for Fmin=3σ | 125 | not stated | cores | 2 | 125 cores are now found |
| Completeness by number at ~1 Msun | ~50% | not stated | percent | 4 | We estimate that we are about 50% complete by number for $\sim1\:M_\odot$ cores. |

## Qualitative findings

- Whether a CMF peak near 1 Msun appears depends on core finder, parameters and completeness correction  
  > "Thus we cannot make firm conclusions about the presence of a peak or characteristic core mass near $1\:M_\odot$." (4 Discussion and Conclusions)

## Claim tuples

- H: Is the high-mass CMF slope in G286 consistent with the Salpeter IMF? | E: Dendrogram core identification, completeness correction, power law fit | R: α=1.24±0.17 versus Salpeter 1.35 | F: Dendrogram CMF is consistent with the Salpeter IMF slope; clumpfind CMF is shallower | **supported**
- H: Does the CMF show a peak or break near 1 Msun? | E: Raw and completeness-corrected CMFs with varied algorithms | R: Raw CMFs peak near 1 Msun but corrected CMFs are consistent with a single power law to ~0.5 Msun | F: Only tentative evidence for shallowing | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Temperature assumed uniform at 20 K; masses uncertain by factor ~2; possible fragmentation at higher resolution  
  > "Overall, we estimate absolute mass uncertainties of about a factor of two" (2.3 Core Mass Estimation)
- Caveat (inferred, ours): Single uniform dust temperature for all cores
- Caveat (inferred, ours): Power-law fit with log-space chi2 and sparse high-mass bins
- Caveat (inferred, ours): Mixture of prestellar and protostellar cores
- Caveat (inferred, ours): Artificial cores assumed unresolved

## Reproducibility

- Data public (paper): Project ID cited, ALMA data acknowledged  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00357.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters (cell, size, masks, thresholds)
- Missing: Line-free channels
- Missing: Exact correction factor tables
- Data volume (inferred): Hundreds of GB (mosaic of 5 strips, 12-m and 7-m)
- Score (inferred): 3/5, Public data and clear algorithm parameters, but imaging details and correction functions are incomplete.
- Rediscovery candidate: yes, Public data, specified core-finder parameters, and numeric slope results.

## Links

- Method: Rosolowsky et al. 2008 (Dendrogram algorithm)
- Method: Williams et al. 1994 (Clumpfind algorithm)
- Companion: Barnes et al. 2010 (Earlier study of G286 infall)

## Checks

```json
{
 "quotes": 60,
 "quotes_ok": 60,
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
  "facts": 70,
  "stated": 43,
  "rate": 0.614
 },
 "evidence_ok": true
}
```
