# Multiscale Gas Structure and Dynamics in an Extragalactic Central Molecular Zone

`2026ApJ..1003..231W` | The Astrophysical Journal 2026 | first author: Wang, Liam M. | arXiv: 2604.06354 | DOI: 10.3847/1538-4357/ae6448

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, milky_way_ism
- Question: How do molecular gas structure, ordered versus random motions, and self-gravity vary with spatial scale in the CMZ of NGC 3351?  
  > "examine the scale dependence of molecular gas structure and dynamics in the central molecular zone (CMZ) of a nearby galaxy, NGC 3351." (abstract)
- Target **NGC 3351**: coordinates _not stated_; z/distance not stated (0.1'' ≈ 5 pc, 2.1'' ~ 100 pc)  
  > "We convert this angular size into a physical size, $r_\mathrm{phy}$, according to the distance to NGC 3351." (2 Data and Method); distance from possibly Anand2021 (cite given for proximity)  
  > "We convert this angular size into a physical size, $r_\mathrm{phy}$, according to the distance to NGC 3351." (2 Data and Method)

## Data provenance

- ALMA projects: 2021.1.00059.S, 2022.1.00159.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: two 12m array configurations plus the 7m array  
  > "We combine data from two 12m array configurations and the 7m array to recover flux on spatial scales up to the full size of the CMZ in NGC 3351." (footnote 1)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.1'' ~ 5 pc  
  > "to achieve both high resolution ($0.1''\sim5$ pc) and full recovery of flux on larger scales" (2 Data and Method)
- max recoverable scale: _not stated_
- sensitivity: noise 1.3 K per 2.5 km/s channel  
  > "has a velocity channel width of 2.5 km/s and a noise level of 1.3 K." (2 Data and Method)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=3-2 (not stated)
- External data: CO isotopologue data (incl. CO 1-0) at 2.1'' resolution used for LVG alpha_CO modeling  
  > "using all the CO isotopologue data in (cite: Teng2022)" (2.2 Gas Mass) [from (cite: Teng2022)]
- External data: Arctan rotation curve of NGC 3351 (V0=206.8 km/s, Rt=0.3 kpc)  
  > "We use the arctan model of the galactic rotation curve fitted in (cite: Lang2020)" (4 Discussion) [from (cite: Lang2020)]
- External data: Size-linewidth relations for NGC 253 and Milky Way CMZ for comparison  
  > "compares this relation with those found with $\mathrm{CO}\,(3\text{--}2)$ data for the CMZs of NGC 253 and our Milky Way" (3.1 Larson's Relations) [from (cite: Krieger2020)]

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
- masking: strict mask: >2σ over 4 consecutive channels, expanded to connected >2σ over 2 channels  
  > "we include CO detection above 2$\sigma$ over 4 consecutive channels, and then expand to all morphologically connected CO emission above 2$\sigma$ over 2 channels in the cube." (footnote 2)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: two 12m configurations + 7m combined  
  > "We combine data from two 12m array configurations and the 7m array to recover flux on spatial scales up to the full size of the CMZ in NGC 3351." (footnote 1)
- smoothing: convolved to 2.1'' common beam for alpha_CO  
  > "we convolve our $\mathrm{CO}\,(3\text{--}2)$ data to match the minimum common beam size of $2.1''$" (2.2 Gas Mass)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Observational design and data reduction taken from Sun2024  
  > "Interested readers are encouraged to consult (cite: Sun2024) for more details about the observational design and data reduction." (2 Data and Method) [from (cite: Sun2024)]
- Strict masking scheme  
  > "following the “strict” masking scheme[^2] defined by (cite: Leroy2021)" (2 Data and Method) [from (cite: Leroy2021)]
- alpha_CO via LVG modeling procedure  
  > "following their procedure for measuring $\alpha_\mathrm{CO}$ based on Large Velocity Gradient (LVG) modeling (cite: Teng2023)" (2.2 Gas Mass) [from (cite: Teng2022; Teng2023)]

### Not stated but needed to reproduce (our reading)

- astrodendro min_value, min_delta values in K and min_npix beyond 'beam size'
- Adopted distance to NGC 3351
- Exact pixel size and beam of the cube and details of outer-ring mask
- Whether sigma_v and radius use astrodendro defaults (e.g. bijection/ scaling factors)
- Binning for running median
- Fit weighting details for np.polyfit (log space, errors)

## Analysis recipe

1. **Build dendrogram**: astrodendro on PPV cube within strict signal mask over the outer ring  
  > "we create a dendrogram from the CO PPV data cube with `astrodendro`" (2 Data and Method)
   - software: astrodendro
   - parameter: structures no smaller than the beam; child brighter than parent by at least 2 rms  
  > "each “child” structure should be brighter than its “parent” structure by at least twice the rms noise." (2 Data and Method)
   - fitting: _not stated_
   - validation: _not stated_
2. **Structure size and gas mass**: radius from second moment converted with distance; M = alpha_CO(3-2) L_CO(3-2) with alpha from LVG map at ~100 pc  
  > "we derive a $\alpha_\mathrm{CO(3{-}2)}$ map at $\sim$100 pc resolution" (2.2 Gas Mass)
   - software: astrodendro
   - assumption: alpha_CO(3-2) 0.3-0.7 Msun pc^-2 (K km/s)^-1 from one-component LVG, median of probability distribution  
  > "we extract the median value of each probability distribution to be our $\alpha_\mathrm{CO(3{-}2)}$ solutions." (2.2 Gas Mass)
   - fitting: Bayesian likelihood LVG modeling following Teng2022  
  > "We then incorporate the convolved $\mathrm{CO}\,(3\text{--}2)$ data into their one-component LVG modeling and Bayesian likelihood analysis." (2.2 Gas Mass)
   - validation: _not stated_
3. **Separate ordered and random motions**: fit linear velocity gradient per structure weighted by brightness temperature; sigma_rand = rms residual; sigma_ord by quadrature difference; alternative method uses moment-1 as ordered model  
  > "We then fit our velocity gradient model for each structure in PPV space, weighted by the brightness temperature at each pixel." (2.4 Velocity Dispersions)
   - fitting: _not stated_
   - validation: two methods give upper/lower bounds  
  > "Using two different methods for separating ordered and random motions, we assess the level of systematic uncertainties associated with this process." (2.4 Velocity Dispersions)
4. **Timescales and scaling relations**: t_ff assuming spherical symmetry, t_cr = r/sigma; power-law fits with np.polyfit  
  > "Here we assume spherical symmetry and use the gas mass and physical radius" (2.3 Free-Fall Time)
   - software: NumPy
   - fitting: linear np.polyfit on power-law dependence  
  > "found using a linear `np.polyfit` fit on a power law dependence" (3.1 Larson's Relations)
   - validation: _not stated_
5. **Compare with galactic rotation model**: project arctan rotation curve, fit linear gradients per structure, compare amplitude and PA with observed  
  > "we fit a linear velocity gradient to the galactic rotation model within the footprint of each gas structure" (4 Discussion)
   - parameter: systemic velocity 778 km/s, inclination 45.1°, PA 188.4°  
  > "systemic velocity (778 km/s), inclination angle (45.1$^\circ$), and position angle (188.4$^\circ$)" (4 Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **astrodendro** : dendrogram, sizes, luminosities, velocity dispersions  
  > "we create a dendrogram from the CO PPV data cube with `astrodendro`" (2 Data and Method)
- **NumPy (np.polyfit)** : power-law fits  
  > "found using a linear `np.polyfit` fit on a power law dependence" (3.1 Larson's Relations)
- **spectral-cube** v0.4.5: listed in software  
  > "`spectral-cube` (cite: spectralcube)" (Software)
- **CARTA** 2.0.0: listed in software  
  > "`CARTA` (cite: CARTA_2.0.0)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of unique dendrogram structures | 398 | not stated | structures | 1 | the dendrogram includes 398 unique gas structures |
| Number of trunks | 16 | not stated | trunks | 1 | can be traced down to 16 unique “trunks” |
| Size–linewidth slope | 0.58 | 0.02 | dimensionless | 4 | \left(\frac{r_\mathrm{phy}}{10\rm\,pc}\right)^{0.58 \pm 0.02} |
| Size–linewidth normalization at 10 pc | 7.2 | 0.3 | km/s | 4 | (7.2 \pm 0.3) |
| Size–mass slope | 2.54 | 0.04 | dimensionless | 4 | \left(\frac{r_\mathrm{phy}}{10\rm\,pc}\right)^{2.54 \pm 0.04} |
| Size–mass normalization at 10 pc | 4.1e5 | 0.4e5 | Msun | 4 | (4.1 \pm 0.4) |
| Fraction of <10 pc structures with t_ff < t_cr,ord | 43 | not stated | % | 4 | $43\%$ of structures under $10$ pc have $t_\mathrm{ff}$ shorter than $t_\mathrm{cr,\,ord}$ |
| Fraction of <10 pc structures with t_ff < t_cr,rand | 21 | not stated | % | 4 | only $21\%$ have $t_\mathrm{ff}$ shorter than $t_\mathrm{cr,\,rand}$ |

## Qualitative findings

- Random motions dominate below ~30 pc; ordered motions dominate in the largest structures, consistent with galactic rotation  
  > "we find that most structures on $\lesssim30$ pc scales tend to have larger random motion than ordered motion." (3.2 Ordered versus Random Motions)

## Claim tuples

- H: Size–linewidth relation in NGC 3351 CMZ resembles other CMZs | E: Power-law fit to 398 dendrogram structures | R: slope 0.58±0.02, normalization 7.2 km/s at 10 pc | F: Similar slope to NGC 253 and MW, normalization below NGC 253 | **supported**
- H: Ordered vs random motion dominance depends on scale | E: Velocity gradient and moment-1 decomposition | R: random dominant ≲30 pc, ordered at larger scales | F: Ordered motion driven by large-scale processes | **supported**
- H: Self-gravity vs motions at different scales | E: Compare t_ff with t_cr of ordered and random motions | R: t_ff comparable to t_cr,ord at all scales; longer than t_cr,rand below ~10 pc | F: Random motions can counter self-gravity at small scales, modulo alpha_CO uncertainty | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Low-resolution alpha_CO may bias small-structure masses  
  > "our gas mass estimates for most structures smaller than $\sim50$ pc may not be totally accurate" (3.1 Larson's Relations)
- Caveat (inferred, ours): alpha_CO at 100 pc applied to ~5 pc structures
- Caveat (inferred, ours): Velocity-gradient model bounds are crude
- Caveat (inferred, ours): No uncertainties propagated to individual structures

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Calibrated/combined CO(3-2) cube from Sun2024
- Missing: alpha_CO map from Teng2022/2023 data
- Missing: astrodendro numerical thresholds
- Missing: distance adopted
- Data volume (inferred): tens of GB raw; cube ~ a few GB
- Score (inferred): 3/5, Analysis is clearly described but input cube, distance, and dendrogram thresholds are not given, and the alpha_CO map relies on other papers.
- Rediscovery candidate: no, Data rely on a previously reduced cube and alpha_CO map from other papers; public status is not stated.

## Links

- Method: (cite: Rosolowsky2008) (dendrogram technique)
- Method: (cite: Teng2023) (LVG alpha_CO procedure)
- Method: (cite: Leroy2021) (strict masking)
- Companion: (cite: Sun2024) (observations and data reduction)
- Companion: (cite: Teng2022) (multi-line CO data)

## Checks

```json
{
 "quotes": 47,
 "quotes_ok": 47,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 32,
  "rate": 0.438
 },
 "evidence_ok": true
}
```
