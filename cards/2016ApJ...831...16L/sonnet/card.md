# A Portrait of Cold Gas in Galaxies at 60 pc Resolution and a Simple Method to Test Hypotheses That Link Small-scale ISM Structure to Galaxy-scale Processes

`2016ApJ...831...16L` | The Astrophysical Journal 2016 | first author: Leroy, Adam K. | arXiv: 1606.07077 | DOI: 10.3847/0004-637X/831/1/16

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, milky_way_ism, star_formation
- Question: How can cloud-scale (60 pc) gas surface density, velocity dispersion and boundedness be measured beam-by-beam, and how do they vary within and among six nearby galaxies?  
  > "We present a simple approach to make such measurements and to test hypotheses that link small-scale gas structure to star formation and galactic environment." (abstract)
- Target **Antennae (overlap region)**: coordinates _not stated_; z/distance 21.5 Mpc  
  > "Antennae CO (3-2) 21.5 60 5.0 17.4 Whitmore et al. (2014)" (Table 2); distance from _not stated_
- Target **M74 (NGC 628)**: coordinates _not stated_; z/distance 9.0 Mpc  
  > "M74 CO (2-1) 9.0 45 2.0 7.9 Schinnerer et al. (in prep.)" (Table 2); distance from _not stated_
- Target **LMC, M31, M33, M51**: coordinates _not stated_; z/distance LMC 0.05, M31 0.78, M33 0.84, M51 7.6 Mpc  
  > "M51 CO (1-0) 7.6 45 5.0 4.35 Schinnerer et al. (2013); Pety et al. (2013)" (Table 2); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00876.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: native 45 pc for M74 (ALMA CO 2-1); all data analysed at common 60 pc  
  > "M74 CO (2-1) 9.0 45 2.0 7.9 Schinnerer et al. (in prep.)" (Table 2)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: M74 ALMA map P.I. Schinnerer; Antennae ALMA from Whitmore et al. 2014  
  > "the ALMA CO 2-1 map of M74 (P.I.: Schinnerer)" (3. DATA AND APPLICATION)
- Line: CO J=2-1 (M74, M33), 1-0 (others), 3-2 (Antennae) (not stated)
- Other facility **PAWS (IRAM)**: M51 CO 1-0 map  
  > "the PAWS map of CO 1-0 from M51 (Schinnerer et al. 2013)" (3. DATA AND APPLICATION)
- Other facility **CARMA**: M31 CO 1-0 survey  
  > "the CARMA CO 1-0 survey of Andromeda (Schruba et al., in prep.)" (3. DATA AND APPLICATION)
- Other facility **IRAM 30m**: M33 CO 2-1 survey  
  > "the IRAM CO 2-1 survey of M33 (Druard et al. 2014; Gratier et al. 2010)" (3. DATA AND APPLICATION)
- Other facility **MAGMA (Mopra)**: LMC CO 1-0 survey  
  > "the MAGMA CO 1-0 survey of the Large Magellanic Cloud (Hughes et al. 2010; Wong et al. 2011)" (3. DATA AND APPLICATION)
- External data: CO cubes for Antennae, LMC, M31, M33, M51 from published surveys  
  > "LMC CO (1-0) 0.05 15 1.6 8.7 Wong et al. (2011)" (Table 2) [from Whitmore et al. (2014); Wong et al. (2011); Druard et al. (2014); Schinnerer et al. (2013)]
- External data: M74 CO(2-1)/(1-0) ratio ~0.55 from two pointings  
  > "The line ratio measurement comes from two pointings by Usero et al. (2015)" (3.2 Adopted Conversion Factors) [from Usero et al. (2015)]

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
- smoothing: cubes convolved to round beam, 60 pc  
  > "For each cube, we convolve the data to have a round beam, convert to units of Kelvin" (3. DATA AND APPLICATION)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Bright-signal masking follows CPROPS  
  > "We identify bright signal in the data cube following the CPROPS methodology of Rosolowsky & Leroy (2006)." (3. DATA AND APPLICATION) [from Rosolowsky & Leroy (2006)]
- M74 ALMA data reduction not given  
  > "M74 from ALMA (Schinnerer, Sliwa, et al. in prep.)" (Figure 3 caption) [from Schinnerer, Sliwa, et al. in prep.]

### Not stated but needed to reproduce (our reading)

- ALMA calibration, imaging and short-spacing combination for M74
- Exact line frequencies and bands
- Channel-to-channel values for stacking per galaxy beyond Table 3
- Code for beamwise/shuffling analysis not released

## Analysis recipe

1. **mask bright signal and compute moments**: Mask with 2 consecutive channels above S/N=5, expand to S/N=1.5; compute integrated intensity, moments, peak  
  > "We begin with regions that show ≥ 2 consecutive channels above S/N = 5. We then expand the mask to include all contiguous regions with ≥ 2 consecutive channels above S/N = 1.5." (3. DATA AND APPLICATION)
   - software: CPROPS
   - fitting: _not stated_
   - validation: _not stated_
2. **shuffle, weight and average to 500 pc**: Shuffle spectra by first moment, weight by integrated intensity, convolve to 500 pc Gaussian beam, divide by convolved intensity; derive I, I_pk, sigma, B  
  > "We weight each measurement (moment) and each spectrum in the shuffled cube by the local integrated intensity" (3. DATA AND APPLICATION)
   - parameter: measurement scale 60 pc, averaging scale 500 pc  
  > "we examine ⟨I 60pc ⟩ 500pc (among other quantities)" (2.2 Two Scales: Measurement and Averaging)
   - assumption: alpha_CO per galaxy (e.g. 4.35 Galactic), depth l=60 pc, T=25 K  
  > "Here, we adopt a fiducial l ≈ 60 pc" (5.4 Physical State of the Gas)
   - fitting: _not stated_
   - validation: Compared with gridded GMC catalogs from CPROPS, CLUMPFIND, dendrograms  
  > "Figure 5 and Table 4 report the ratio of ensemble average measurements based on cloud catalogs" (4. BEAMWISE MEASUREMENTS AND CLOUD PROPERTIES)
3. **flux distribution and uncertainties**: Progressive intensity thresholding to get flux CDF (16/50/84 percentiles, Delta84-16); Monte Carlo with 100 noise realizations  
  > "We realize 100 data sets with randomly generated noise and record these as an ensemble of mock databases." (3. DATA AND APPLICATION)
   - fitting: bivariate fit sigma vs Sigma excluding Antennae  
  > "the equation is a bivariate fit to the ensemble of data excluding the Antennae" (5.5 A Scaling Between Surface Density and Line Width)
   - validation: Flux completeness 70-110% (Table 3)  
  > "At our resolution of θ = 60 pc, we recover ∼70−100% of the total flux in the cube." (3.1 Convergence)

## Software

- **CPROPS** : masking and cloud property measurement  
  > "We apply the CPROPS algorithm (Rosolowsky & Leroy 2006)" (3. DATA AND APPLICATION)
- **CLUMPFIND (seeded)** : cloud decomposition  
  > "a seeded version of the CLUMPFIND (Williams et al. 1994; Rosolowsky & Blitz 2005) algorithm" (3. DATA AND APPLICATION)
- **dendrogram** : multiscale cloud decomposition  
  > "the dendrogram multiscale approach (Rosolowsky et al. 2008)" (3. DATA AND APPLICATION)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Flux-distribution width Delta84-16 | ~0.6 | not stated | dex | 3 | ∆ [84][−][16] /2, which will be the rms dispersion for a lognormal distribution, is ∼0.3 dex over most of the area |
| log10 sigma = a log10(Sigma/50) + b slope | 0.31 | ±0.04 | dimensionless | 3 | (0.31 ± 0.04) log 10 |
| Intercept of sigma-Sigma fit | 0.74 | ±0.01 | log10 km/s | 3 | + (0.74 ± 0.01) |
| alpha_vir to B relation (CPROPS) | alpha_vir ≈ 1.3 B^-1 | not stated | dimensionless | 2 | We prefer the CPROPS value and will take α vir,60pc ≈ 1.3B 60pc |
| Surface density increase 60 to 30 pc | 1.6 | not stated | dimensionless | 3 | contrast is a factor of 1.6, which is far weaker than the |
| Median Antennae log10 Sigma | 2.81 | 16-84%: 2.51 to 3.54 | Msun pc^-2 | 2 | log 10 Σ 2.81 1.27 1.09 1.30 2.20 1.71 |

## Qualitative findings

- Local Group galaxies are similar; Antennae and M51 show higher intensity and line width; M31 gas appears unbound  
  > "The Antennae and M51 show markedly higher I and σ than the Local Group targets." (5.1 Variations Within and Among Galaxies)

## Claim tuples

- H: Beamwise intensity-weighted measurements capture the same physics as cloud-property catalogs | E: Compare gridded GMC catalog properties to beamwise values at 60 pc, 500 pc averaging | R: Median ratios 0.7-1.3 for I and sigma with CPROPS; B correlates with alpha_vir | F: Beamwise approach is a simple valid alternative | **supported**
- H: Flux distribution vs surface density has a universal shape | E: Flux CDF within 500 pc beams | R: Roughly lognormal, 1σ ~0.3 dex, center varies | F: Cloud-scale gas depends on environment | **supported**
- H: Self-gravity depends on scale | E: Repeat at 30 pc for LMC and M31 | R: Higher surface density, lower line width, higher alpha_vir^-1 | F: Gas more self-gravitating at smaller scales | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Antennae lacks short-spacing data; M31 alpha_CO uncertain  
  > "lack of short spacing data" (3. DATA AND APPLICATION)
- Caveat (inferred, ours): Adopted alpha_CO per galaxy drives Sigma and boundedness
- Caveat (inferred, ours): Only two ALMA datasets of six; M74 data unpublished
- Caveat (inferred, ours): Line width includes multiple components in the Antennae

## Reproducibility

- Data public (paper): M33 and MAGMA data stated as public  
  > "thank the M33 and MAGMA teams for making their data public" (Acknowledgments)
- Products in archive: _not stated_
- Missing: M74 ALMA processing
- Missing: Analysis code
- Missing: Non-ALMA cubes need separate retrieval
- Data volume (inferred): tens of GB for ALMA parts
- Score (inferred): 2/5, Method is well described but most data are non-ALMA or unpublished and code is not released.
- Rediscovery candidate: no, Several inputs are unpublished or non-archival.

## Links

- Method: Rosolowsky & Leroy (2006) (CPROPS masking and cloud properties)
- Method: Schruba et al. (2011) (spectral stacking)
- Companion: Schinnerer et al. in prep. (M74 ALMA data)
- Related: PAWS
- Related: MAGMA
- Related: HERACLES

## Checks

```json
{
 "quotes": 41,
 "quotes_ok": 41,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2012.1.00650.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 29,
  "rate": 0.397
 },
 "evidence_ok": true
}
```
