# A Study of the Relation between Star Formation and Molecular Clumps on Subparsec Scales in 30 Doradus

`2016ApJ...831...32N` | The Astrophysical Journal 2016 | first author: Nayak, O. | arXiv: 1608.05451 | DOI: 10.3847/0004-637X/831/1/32

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type archival_reuse

## Science

- Fields: star_formation, nearby_galaxies
- Question: How do massive and low-mass young stellar objects relate to CO molecular clumps (dendrogram-identified) on subparsec scales in 30 Doradus, and what are the clump size-linewidth and virial properties?  
  > "Our goal in this paper is to conduct a thorough investigation of early stage massive YSOs and later stage low-mass YSOs, and their relation to the clump structure of $\mathrm{^{12}CO}$ (2-1) and $\mathrm{^{13}CO}$ (2-1) molecular gas." (1.2 Star Formation and Molecular Clumps in 30 Doradus)
- Target **30 Doradus (north of R136)**: coordinates _not stated_; z/distance 50 kpc  
  > "the distance to the LMC is well-determined (50 kpc, (cite: feas99))" (1.1 Star Formation in the Large Magellanic Cloud); "The ALMA Cycle 0 footprint of 30 Doradus is a small region north of R136" (2.3 ALMA 12CO (2-1) and 13CO (2-1) Observation); distance from Feast 1999 (cite: feas99)  
  > "the distance to the LMC is well-determined (50 kpc, (cite: feas99))" (1.1 Star Formation in the Large Magellanic Cloud); "The ALMA Cycle 0 footprint of 30 Doradus is a small region north of R136" (2.3 ALMA 12CO (2-1) and 13CO (2-1) Observation)

## Data provenance

- ALMA projects: _none stated_
- bands: ALMA Cycle 0 12CO(2-1) and 13CO(2-1), combined with APEX single dish  
  > "We use the ALMA Cycle 0 combined with APEX single dish observations of $\mathrm{^{12}CO}$ (2-1) and $\mathrm{^{13}CO}$ (2-1) made by (cite: inde13) in our analysis." (2.3 ALMA 12CO (2-1) and 13CO (2-1) Observation)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.5 pc beam  
  > "the current numbers thus include convolution by the $\sim$ 0.5pc beam." (Appendix C)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Data from Indebetouw et al. 2013 (reanalysed)  
  > "We use the same data as (cite: inde13) in this work." (5.1 Size, Linewidth, and Mass Surface Density)
- Line: 12CO 2-1 (not stated)
- Line: 13CO 2-1 (not stated)
- Other facility **Spitzer SAGE / Herschel HERITAGE**: IR photometry for massive YSO candidates  
  > "The SAGE survey imaged the LMC using IRAC (3.6 $\mu$m, 4.5 $\mu$m, 5.8 $\mu$m, 8.0 $\mu$m) and MIPS (24 $\mu$m, 70 $\mu$m, 160 $\mu$m) instruments" (2.1)
- Other facility **HST HTTP**: Halpha-excess low-mass YSO catalog and photometry  
  > "We have used the HTTP catalog (cite: sabb16) to select the low-mass Stage III YSO candidates with H$\mathrm{\alpha}$ excess within the ALMA footprint" (4.1 Stage III Low-Mass YSOs)
- External data: ALMA+APEX CO cubes and cprops clump sizes/linewidths  
  > "We got the size and linewidth values of $\mathrm{^{13}CO}$ clumps output from cprops from our personal correspondence with Remy Indebetouw." (Appendix B) [from Indebetouw et al. 2013 (cite: inde13)]
- External data: 12CO X-factor 12 ± 4 Msun pc-2 (K km/s)-1  
  > "We calculate the brightness temperature integrated over the velocity for $\mathrm{^{12}CO}$ (2-1) and use a X-factor of $12 \pm 4\;\mathrm{M_{\odot}\;pc^{-2}\;(K\;km\;s^{-1})^{-1}}$." (3.3) [from (cite: inde13)]
- External data: HTTP photometry catalog  
  > "We have used the HTTP catalog (cite: sabb16)" (4.1) [from (cite: sabb16)]
- Simulation/model as data: Robitaille YSO SED model grid; Padova isochrones and tracks  
  > "We plot isochrones and mass evolutionary tracks taken from the Padova code (cite: bres12; chen15) on these figures." (4.1)

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
- array combination: ALMA combined with APEX single dish (from Indebetouw+13)  
  > "We use the ALMA Cycle 0 combined with APEX single dish observations" (2.3)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA/APEX data reduction and cubes  
  > "made by (cite: inde13) in our analysis." (2.3) [from (cite: inde13)]
- H2/13CO abundance ratio  
  > "the same abundance factor that was used by (cite: inde13)" (3.3) [from (cite: inde13)]
- Halpha-excess selection criteria  
  > "using the stringent selection criteria as defined by (cite: dema11.1)" (4.1) [from (cite: dema11.1)]

### Not stated but needed to reproduce (our reading)

- astrodendro min_value, min_delta, min_npix for each cube
- ALMA project code, calibration and imaging details (cleaning, weighting, noise)
- Cube rms and velocity resolution used
- Size-linewidth fitting method (regression with errors)
- Inconsistent X-factor (12 in text vs 8.4 in table) and H2/13CO (5e6 vs 5e2)
- Code for SED fitting wrapper not released

## Analysis recipe

1. **Identify clumps via dendrogram**: astrodendro clipping method on 12CO brightness temperature and 13CO column-density cubes  
  > "The *astrodendro* program uses what is known as the clipping method to calculate clump properties from a 2D image or a 3D data cube." (3.2 Method)
   - software: astrodendro
   - parameter: inputs: minimum value, leaf threshold, minimum pixels (values not stated)  
  > "The user has to input the minimum value to be considered in the data set, the threshold value that determines if a leaf will be a single entity or not, and the minimum number of pixels" (3.2 Method)
   - fitting: _not stated_
   - validation: Compared with cprops clumps of Indebetouw+13 for 8 matched clumps  
  > "There are a total of 8 such clumps we can match from the two different algorithms" (Appendix B)
2. **Derive clump masses**: 12CO: integrated Tb times X-factor; 13CO: LTE column density with 12CO Tex, converted to H2 mass  
  > "We assume that $\mathrm{^{13}CO}$ is optically thin." (Appendix A)
   - assumption: 12CO optically thick; 13CO same Tex as 12CO; LTE; H2/13CO = 5e6  
  > "Further assumptions of the local thermodynamic equilibrium (or LTE) analysis include: $\mathrm{^{13}CO}$ has the same excitation temperature as $\mathrm{^{12}CO}$" (Appendix A)
   - fitting: _not stated_
   - validation: Masses consistent with Indebetouw+13 dust and LTE masses  
  > "The mass estimated from $\mathrm{^{13}CO}$ (2-1) and $\mathrm{^{12}CO}$ (2-1) in this work are consistent with each other" (3.3)
3. **Build YSO catalogs**: Halpha-excess selection from HTTP for low-mass; SAGE point sources fit with Robitaille SED fitter for massive, chi2 criteria  
  > "we require the reduced $\mathrm{\chi^{2}}$ of the best fit YSO SED to be less than 10 and the reduced $\mathrm{\chi^{2}}$ of the best fit stellar photosphere to be greater than 10" (4.2.1)
   - software: Robitaille SED fitter
   - fitting: Maximum likelihood of YSO parameters with 1 sigma errors  
  > "This code outputs the maximum likelihood of the YSO parameters such as mass, luminosity, accretion rate, and associated 1$\mathrm{\sigma}$ errors." (4.2.1)
   - validation: Compared with Carlson+12 color cuts  
  > "(cite: carl12) also used multi-color cuts" (4.2.1)
4. **Size-linewidth, virial and association analysis**: Power-law fits of linewidth vs radius; virial parameter 5σ²r/GM; YSO-clump association within effective radius  
  > "We define the virial parameter, $\alpha$, to equal to $\mathrm{\frac{5 \sigma^{2}\;r}{G\;M}}$" (5.2 Energy Balance)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **astrodendro** : dendrogram clump identification  
  > "This research made use of astrodendro, a Python package to compute dendrograms of Astronomical data" (Acknowledgements)
- **Astropy** : general analysis  
  > "This research also made use of Astropy" (Acknowledgements)
- **cprops** : clump decomposition in prior work, compared  
  > "analyzed by (cite: inde13) using cprops (cite: roso06)" (5.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 12CO size-linewidth fit | σ = 1.66 r^0.65 | ±0.06 (norm), ±0.04 (slope) | km/s, pc | 4 | $\mathrm{\sigma = (1.66 \pm 0.06) r^{(0.65 \pm 0.04)}}$ |
| 13CO size-linewidth fit | σ = 1.58 r^0.97 | ±0.18 (norm), ±0.12 (slope) | km/s, pc | 4 | $\mathrm{\sigma = (1.58 \pm 0.18) r^{(0.97 \pm 0.12)}}$ |
| Total 13CO H2 mass | 6.7e4 | not stated | Msun | 2 | is $6.7 \times 10^{4}\;\mathrm{M_{\odot}}$ |
| Total 12CO mass | 1.3e5 | 0.4e5 | Msun | 2 | is $1.3 \pm 0.4 \times 10^{5}\;\mathrm{M_{\odot}}$ |
| Fraction of 13CO clumps with virial parameter ≤1 | 72 | not stated | percent | 4 | 72$\%$ of the $\mathrm{^{13}CO}$ (2-1) clumps have a virial parameter equal to 1 or less |
| YSOs associated with clumps | 7/10 massive, 7/87 low-mass | not stated | counts | 4 | We find 7/87 more evolved low-mass YSOs and 7/10 massive young YSO candidates are associated with clumps. |
| ν ∝ Σ^x exponent | 0.45 | not stated | dimensionless | 4 | We find that $\mathrm{\nu \propto \Sigma ^{0.45}}$. |

## Qualitative findings

- 30 Dor clumps have larger linewidths at given size than quiescent Milky Way clumps, similar to IR dark clouds  
  > "Clumps in 30 Doradus have a larger linewidths than typical Milky Way clumps, however they have similar linewidth as infrared dark clouds that are very likely forming protostars." (5.1)

## Claim tuples

- H: 30 Dor clumps follow the same size-linewidth relation as Milky Way clumps | E: Dendrogram fits to 12CO and 13CO clumps compared with literature | R: Slopes 0.65 and 0.97 consistent within 3σ, offsets of 3.8 and 2.5 in linewidth | F: Larger linewidths likely due to energetic environment | **supported**
- H: A threshold exists for massive star formation in clumps | E: Lowest-mass/density clump hosting a massive YSO | R: mass >1.83e2 Msun, Σ >6.67e2 Msun/pc², σ >1.18 km/s | F: Massive star formation needs high mass, linewidth, density | **partially**
- H: Larson's first law is universal | E: ν vs Σ | R: ν ∝ Σ^0.45 | F: Not universal | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Low-mass YSO catalog incomplete due to Halpha duty cycle (~1/3) and embedded low-mass YSOs missed  
  > "We are not complete in our catalog of low-mass YSOs due to the H$\mathrm{\alpha}$ duty cycle" (4.1)
- Limitation (authors): 13CO may not be thermalized, underestimating mass  
  > "It is possible that the $\mathrm{^{13}CO}$ (2-1) line is not fully thermalized, therefore leading to an underestimate of the true mass." (5.2)
- Caveat (inferred, ours): Inconsistent X-factor and abundance values between text, tables and appendix
- Caveat (inferred, ours): Linewidth definitions differ from prior work and depend on algorithm parameters
- Caveat (inferred, ours): Threshold derived from a single clump
- Caveat (inferred, ours): Small clump sample with nested, non-independent structures

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Reduced cubes (from Indebetouw+13)
- Missing: astrodendro parameters
- Missing: SED fitting wrapper code
- Data volume (inferred): ~ few GB (ALMA Cycle 0 cubes) plus catalogs
- Score (inferred): 3/5, Data public but dendrogram parameters and cube details missing; inputs inherited.
- Rediscovery candidate: no, Cubes come from prior paper and dendrogram parameters are not given.

## Links

- Method: Indebetouw et al. 2013 (cite: inde13) (ALMA/APEX data and cprops analysis)
- Method: Robitaille et al. 2006 (cite: robi06) (SED fitter)
- Companion: Sabbi et al. 2016 (cite: sabb16) (HTTP catalog)
- Related: Spitzer SAGE
- Related: Herschel HERITAGE
- Related: Hubble Tarantula Treasury Project

## Checks

```json
{
 "quotes": 47,
 "quotes_ok": 47,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00471.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 32,
  "rate": 0.444
 },
 "evidence_ok": true
}
```
