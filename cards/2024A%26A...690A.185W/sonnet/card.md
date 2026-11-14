# Dynamical accretion flows: ALMAGAL: Flows along filamentary structures in high-mass star-forming clusters

`2024A&A...690A.185W` | Astronomy and Astrophysics 2024 | first author: Wells, M. R. A. | arXiv: 2408.08299 | DOI: 10.1051/0004-6361/202449794

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: star_formation, milky_way_ism
- Question: What are the properties of longitudinal accretion flows along filaments onto cores in high-mass star-forming clusters, and how do they depend on evolutionary stage, offset from core and core mass?  
  > "This work aims to answer the question: what are the properties of accretion flows in high-mass star-forming clusters?" (Conclusions)
- Target **100 selected ALMAGAL regions (87 used, 182 cores); example AG348.5792-0.9197**: coordinates _not stated_; z/distance ~2 to 6 kpc  
  > "we choose a smaller subset of 100 regions for a focused study on flow rates and the relationship between them and other core properties." (Sample selection); "the distances were derived with the (cite: 2021Mege) method using the ALMAGAL spectral cubes" (Sample); distance from Mège et al. 2021 method applied to ALMAGAL cubes  
  > "we choose a smaller subset of 100 regions for a focused study on flow rates and the relationship between them and other core properties." (Sample selection); "the distances were derived with the (cite: 2021Mege) method using the ALMAGAL spectral cubes" (Sample)

## Data provenance

- ALMA projects: 2019.1.00195.L
- bands: Band 6 (1.3 mm), 217-221 GHz  
  > "The 1017 regions were observed in ALMA band 6 at frequencies from 217 to 221 GHz (corresponding to 1.3 mm)." (ALMAGAL survey details)
- frequencies and spectral setup: 2 broad windows of 1.875 GHz (1.3 km/s resolution) and 2 narrow windows of 0.468 GHz (0.3 km/s)  
  > "two of them covering a broad frequency range of 2x 1.875 GHz being sensitive to the continuum emission, as well as many spectral lines at low spectral resolution (1.3 km/s)" (ALMAGAL survey details)
- continuum bandwidth: _not stated_
- arrays: 12m (two configs) plus 7m ACA; this work uses 7M + TM2 combined  
  > "The data products used in this work are images with combined data from the 7m array (7M hereafter) and the most compact 12-m array configuration (TM2 hereafter)." (ALMAGAL survey details)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.5-1.0 arcsec, ~5000 au  
  > "The resulting images have angular resolutions of 0.5-1.0$''$, depending on the distance of the source, which result in similar linear resolutions of 5000 au for all the targets." (ALMAGAL survey details)
- max recoverable scale: _not stated_
- sensitivity: continuum rms ~0.15 mJy/beam; H2CO ~9 mJy/beam; SO ~5 mJy/beam  
  > "Continuum RMS |         $\sim$0.15 mJy/beam" (Table 1)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: H2CO 3(0,3)-2(0,2) (218.222 GHz)
- Line: SO 6(5)-5(4) (219.949 GHz)
- Other facility **Herschel Hi-GAL, MIPSGAL, GLIMPSE**: 70, 24 and 8 micron images for evolutionary classification; Hi-GAL dust temperatures  
  > "Hi-GAL 70 μm (cite: Elia2017), MIPSGAL 24 μm (cite: 2009Carey), and GLIMPSE 8 μm (cite: 2009Churchwell)" (Evolutionary stage)
- External data: Evolutionary classification scheme and ATLASGAL cross-match classifications  
  > "We use the sequence and classification scheme defined by (cite: 2022Urquhart), which divides the sources into four evolutionary stages" (Evolutionary stage) [from (cite: 2022Urquhart)]
- External data: Dust opacity kappa = 0.899 cm2/g at 1300 um  
  > "$\kappa_\mathrm{\nu}$ = 0.899 cm^2^ g^−1^ (interpolated to 1300 μm from Table 1, Col. 5 of (cite: ossenkopf1994))" (Column density) [from (cite: ossenkopf1994)]
- External data: L/M-based temperature prescription for sources  
  > "Coletta et al. (in prep.) have estimated temperatures that can be assigned to sources based on their evolutionary stage (indicated by luminosity to mass ratio)" (Temperature estimates) [from Coletta et al. (in prep.)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10% calibration uncertainty on flux density  
  > "for the flux density we take 10% from the calibration uncertainty" (Error propagation)
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
- array combination: 7M + TM2 combined images from ALMAGAL pipeline  
  > "The data products used in this work are images with combined data from the 7m array (7M hereafter) and the most compact 12-m array configuration (TM2 hereafter)." (ALMAGAL survey details)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Observations, data reduction and image generation  
  > "Information about the observations, data reduction and image generation are presented and discussed in more detail in the ALMAGAL data reduction paper (Sanchez-Monge et al., in prep)." (ALMAGAL survey details) [from Sanchez-Monge et al. (in prep.)]
- Flow rate estimation approach  
  > "To estimate the flow rates along the filamentary structures leading toward the cores, we follow the approach outlined in (cite: 2020Beuther)." (Quantifying flow rates) [from (cite: 2020Beuther)]
- Velocity extraction with KeplerFit code  
  > "To calculate a velocity difference we used the KeplerFit code from (cite: 2019Bosco)." (Velocity difference) [from (cite: 2019Bosco)]

### Not stated but needed to reproduce (our reading)

- Imaging parameters (robust, cell size, deconvolution) of ALMAGAL 7M+TM2 products
- Continuum-subtraction and line-free channels
- Exact PV cut angles and lengths per source
- Whether the 0.7 or 0.6 km/s velocity resolution is used consistently
- Flow rate table is only a preview; full table needed
- Fit procedure for the M^2/3 relation (binning, fitting method)
- Which of 1013/1017 regions are in the parent sample

## Analysis recipe

1. **Select sample and classify evolution**: Visual selection of 100 regions (25 per stage) with strong emission; classification via 70/24/8 um appearance  
  > "These sources were selected visually based on having strong continuum and line emission so that the initial sample includes 25 regions from each of the 4 evolutionary stages" (Sample selection)
   - fitting: _not stated_
   - validation: Compared with luminosity-to-mass ratio  
  > "as expected the two classification schemes roughly agree, with some overlap" (Evolutionary stage)
2. **Identify cores in continuum**: astrodendro leaves on continuum image  
  > "The highest hierarchical level for each structure is a "leaf" (i.e a structure with no substructure), these correspond to what we define as a core." (Core identification)
   - software: astrodendro
   - parameter: min_value = 5 sigma_cont, min_delta = 5 sigma_cont, min_npix = beam area  
  > "We use $min\_value$ = 5 $\sigma_{cont}$, $min\_delta$ = 5 $\sigma_{cont}$ and $min\_npix$ = beam area." (Core identification)
   - fitting: _not stated_
   - validation: _not stated_
3. **Check outflow contamination and make PV cuts**: SO(6-5) wing emission inspected visually; H2CO PV cuts along filaments, perpendicular to outflow signatures  
  > "the cut was made perpendicular to any signatures where possible, whilst keeping the cut inline with the filamentary structure." (Position-Velocity diagrams)
   - fitting: _not stated_
   - validation: _not stated_
4. **Column density and core mass**: Optically thin dust emission, modified blackbody per pixel; mass from integrated leaf flux  
  > "Column density maps were made using Equation [\[colden\]](#colden) (modified black body emission equation from (cite: 2009Schuller)) assuming optically thin dust emission at mm wavelengths" (3.2 Column density)
   - parameter: T = 20 K (L/M<1), 35 K (1-10), max(21.1 L/M^0.22, 35 K) (>10)  
  > "20~\si{\K} & \mathrm{if}\quad L/M < 1," (Temperature estimates)
   - assumption: mu = 2.8, gas-to-dust 150, kappa = 0.899 cm2/g  
  > "We also assumed a gas-to-dust mass ratio $R = 150$" (Column density)
   - fitting: _not stated_
   - validation: Hi-GAL dust temperatures give only ~5-10% differences  
  > "Comparing the results there were no qualitative and only small quantitative differences ($\sim$ 5-10%)" (Temperature estimates)
5. **Velocity difference**: KeplerFit on PV cut, read velocities at 3 sigma_line contour relative to rest velocity  
  > "taking the strongest (largest intensity) opposing quadrants and reading out the velocity values from the pixels that the specified $\sigma_{line}$ contours go through (here we used 3 $\sigma_{line}$)." (Velocity difference)
   - software: KeplerFit
   - assumption: Region rest velocity is a proxy for core velocity  
  > "this makes the rest velocity a good proxy for the reference velocity." (Velocity difference)
   - fitting: _not stated_
   - validation: Rest velocities compared to H2CO moment-1 at core peaks  
  > "we find that the majority of the values are less than our velocity resolution of 0.6 kms$^{-1}$." (Velocity difference)
6. **Compute flow rates**: Mdot = Sigma * dv * w at four positions (0.75'' and 1.75'' either side), width 1''  
  > "Two inner and two outer positions (0.75$''$ and 1.75$''$ away on either side of the core) excluding the central most 0.5$''$" (Width)
   - assumption: Inclination i = 0 (plane of sky); flow directed toward cores  
  > "We set the inclination angle, $i$, to 0 for the filamentary structures in the plane of the sky." (Inclination angle)
   - fitting: _not stated_
   - validation: Gaussian error propagation, ~50% errors; analytic inclination spread model  
  > "When combining these we end up with $\pm 50\%$ error margins on our final flow rates." (Error propagation)
7. **Statistical comparison and scaling**: KS and Mann-Whitney U tests between stages and inner/outer; flow rate vs core mass binned with best-fit line  
  > "we applied two different, well-known, significance tests, the Kolmogorov-Smirnov (KS) test and the Mann-Whitney U test" (Statistical testing)
   - parameter: significance level 0.05  
  > "Here we use 0.05, as used by (cite: chakravarti1967handbook)." (Statistical testing)
   - fitting: line of best fit through binned values  
  > "Here we also have a line of best fit through these binned values." (Core mass)
   - validation: _not stated_

## Software

- **astrodendro** : core identification  
  > "We used the `astrodendro`[^1] program on the continuum data for core identification" (Core identification)
- **KeplerFit** : velocity extraction from PV cuts  
  > "To calculate a velocity difference we used the KeplerFit code from (cite: 2019Bosco)." (Velocity difference)
- **Spectral-Cube** v0.4.4: cube handling (acknowledged)  
  > "NumPy (cite: numpy), matplotlib (cite: matplotlib) and Spectral-Cube (cite: spectralcube)." (Acknowledgements)
- **Astropy** : general analysis (acknowledged)  
  > "Astropy:[^3] a community-developed core Python package and an ecosystem of tools and resources for astronomy" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Cores identified initially | 203 cores in 100 regions | not stated | cores | 2 | Running the analysis with these parameters we identify 203 cores within the 100 regions. |
| Final sample | 87 regions, 182 cores | not stated | count | 3 | the final sample consists of 87 regions with 182 cores in total. |
| Number of flow rates | 728 | not stated | count | 6 | contains 728 measured flow rates |
| Typical flow rate | ~1e-4 | ±50% | Msun/yr | 6 | We get flow rates on average on the order of $\sim$10$^{-4}$ M$_{\ensuremath{\odot}}\mathrm{yr}^{-1}$ with error margins of $\pm$50%. |
| Median velocity difference | 3.4 | not stated | km/s | 5 | our median velocity difference measurement $\Delta v$ of 3.4 km s$^{-1}$ |
| Median inner-minus-outer flow rate | 1.12e-5 | not stated | Msun/yr | 7 | With a median of 1.12$\times$10$^{-5}~$M$_{\ensuremath{\odot}}$yr$^{-1}$ |
| Flow rate vs core mass exponent | ~2/3 | not stated | dimensionless | 7 | This suggests that we have a relationship where the flow rate follows $\sim$M$^{2/3}$. |
| Inner vs outer KS p-value | 0.0691 (Mann-Whitney 0.0731) | not stated | dimensionless | 7 | The p-values from the two tests were 0.0691 and 0.0731 respectively. |

## Qualitative findings

- No correlation of flow rate with parental clump mass or with distance  
  > "We also looked to see if there was a relationship between these flow rates and the mass of the parental clump and we found no correlation." (Core mass)

## Claim tuples

- H: Flow rates change with evolutionary stage | E: Compare flow rate distributions across four stages with KS and Mann-Whitney tests | R: Mean/median increase by eye; KS significant for quiescent combos, Mann-Whitney not | F: Increasing trend, statistically ambiguous | **partially**
- H: Flow rates depend on offset from core | E: Compare inner (0.75'') and outer (1.75'') flow rates | R: Inner larger, median difference 1.12e-5 Msun/yr; tests p~0.07 | F: Trend toward larger inner rates, not significant by tests | **partially**
- H: Flow rate scales with core mass, revealing accretion mechanism | E: Flow rate vs core mass with binned fit | R: Flow rate ~ M^2/3 | F: Consistent with tidal-lobe accretion | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: H2CO(3-2) chosen for intermediate critical density matching expected densities  
  > "due to its intermediate critical density ($\sim$ 7$\times$10$^{5}$ cm$^{-3}$, (cite: shirley2015)) that is similar to the densities we expect to trace in our regions." (Position-Velocity diagrams)
- Alternative: Hi-GAL dust temperatures tested; gas temperatures adopted  
  > "we are confident to proceed with the gas temperatures with the reasoning that the dust temperatures are tracing primarily cold gas" (Temperature estimates)
- How they decided it was enough: _not stated_
- Limitation (authors): Missing flux: masses and column densities are lower limits  
  > "Missing flux has effects on our mass and column density estimates, so we take these values as lower limits." (Data)
- Limitation (authors): Unknown inclination; Hii region flows may not be accretion  
  > "Hence, the Hii flow rates are not necessarily accretion flows." (Results)
- Caveat (inferred, ours): Rest-velocity proxy and visual PV cuts introduce subjectivity
- Caveat (inferred, ours): Flow rate and core mass both depend on same column density/flux, so correlation may be partly built in
- Caveat (inferred, ours): Temperatures assigned by L/M rather than measured
- Caveat (inferred, ours): Inclination fixed to zero

## Reproducibility

- Data public (paper): ALMAGAL data used via ALMA project; processing in unpublished companion papers  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA2019.1.00195.L." (Acknowledgements)
- Products in archive: _not stated_
- Missing: ALMAGAL image products and pipeline details (in prep. papers)
- Missing: Per-source PV cut definitions
- Missing: Full flow rate table
- Data volume (inferred): ~100 regions of 7M+TM2 continuum and line cubes; tens of GB
- Score (inferred): 3/5, Methods and equations clear, but data products and several choices rely on in-prep papers and visual selections.
- Rediscovery candidate: no, Reliance on unpublished survey products and visual PV cuts prevents a straightforward redo.

## Links

- Method: (cite: 2020Beuther) (flow rate method)
- Method: (cite: 2019Bosco) (KeplerFit)
- Companion: Molinari et al. (in prep.) (ALMAGAL survey)
- Companion: Sanchez-Monge et al. (in prep.) (data reduction)
- Companion: Coletta et al. (in prep.) (core catalogue and temperatures)
- Related: ALMAGAL
- Related: Hi-GAL
- Related: ATLASGAL
- Related: RMS survey

## Checks

```json
{
 "quotes": 62,
 "quotes_ok": 62,
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
  "facts": 85,
  "stated": 45,
  "rate": 0.529
 },
 "evidence_ok": true
}
```
