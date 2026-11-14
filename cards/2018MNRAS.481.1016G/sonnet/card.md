# Connecting young star clusters to CO molecular gas in NGC 7793 with ALMA-LEGUS

`2018MNRAS.481.1016G` | Monthly Notices of the Royal Astronomical Society 2018 | first author: Grasha, K. | arXiv: 1808.02496 | DOI: 10.1093/mnras/sty2154

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation, milky_way_ism
- Question: How are young star clusters spatially and temporally related to GMCs in NGC 7793, and is the cluster hierarchy inherited from the GMC hierarchy?  
  > "We present an investigation of the relationship between giant molecular cloud (GMC) properties and the associated stellar clusters in the nearby flocculent galaxy NGC 7793." (abstract)
- Target **NGC 7793**: coordinates _not stated_; z/distance 3.44±0.15 Mpc  
  > "NGC 7793 is located at $3.44\pm0.15$ Mpc" (3.1 Star Cluster Selection); "NGC 7793 is a nearby (cite: pietrzynski10) SAd flocculent galaxy in the Sculptor group." (2.1 The HST UV/Optical Observations); distance from not stated (cited Pietrzynski et al. 2010 for nearby)  
  > "NGC 7793 is located at $3.44\pm0.15$ Mpc" (3.1 Star Cluster Selection); "NGC 7793 is a nearby (cite: pietrzynski10) SAd flocculent galaxy in the Sculptor group." (2.1 The HST UV/Optical Observations)

## Data provenance

- ALMA projects: 2015.1.00782.S
- bands: Band 6 (230.36366 GHz)  
  > "We observed the CO (2–1) transition with ALMA band 6 (230.36366 GHz)" (2.2 The ALMA CO Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12-m array, mosaic of 149 pointings, 12.9'' spacing  
  > "The total integration time is 3 hours with the 12-m array with 149 pointings at 72.6 seconds of integration per pointing with a mosaic spacing of 12.9$''$ between pointings." (2.2 The ALMA CO Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.85'' (~8 pc scales)  
  > "Our angular resolution of 0.85$''$ allows us to resolve sub-GMC sizes (8 pc scales)" (2.2 The ALMA CO Observations)
- max recoverable scale: 11'' (~175 pc)  
  > "we are sensitive to emission on scales as large as 11” ($\sim$175 pc)" (2.2 The ALMA CO Observations)
- sensitivity: rms ~4 mJy/beam; 1.2 km/s velocity resolution; clouds ~1e4 Msun detectable  
  > "The final rms noise of the observations is $\sim$4 mJy/beam." (2.2 The ALMA CO Observations)
- time on source: 3 hours total  
  > "The total integration time is 3 hours with the 12-m array" (2.2 The ALMA CO Observations)
- observing dates: _not stated_
- pi or archival as stated: PI: K.E. Johnson; data reduction in Bittle et al. in prep  
  > "(ALMA programs 2015.1.00782 & 2016.1.00674; PI: K.E. Johnson)" (2.2 The ALMA CO Observations)
- Line: CO J=2-1 (230.36366 GHz)
- Other facility **HST LEGUS**: UV/optical imaging and star cluster catalog (370 clusters, class 1-3)  
  > "The final cluster catalog for NGC 7793 contains 370 clusters of class 1, 2, and 3." (3.2 Visual Inspection and Star Cluster Classification)
- External data: LEGUS star cluster catalog (ages, masses, E(B-V)) for NGC 7793  
  > "The final star cluster catalog for NGC 7793, as well as the rest of the LEGUS star cluster catalogs, is available online" (3.2 Visual Inspection and Star Cluster Classification) [from (cite: adamo17)]
- External data: NGC 5194 cluster-GMC results for comparison  
  > "The median age of the star clusters in NGC 5194 is 30 Myr, five times older than the median population in NGC 7793." (4.3.1 The Whirlpool Galaxy NGC 5194) [from (cite: grasha18)]
- External data: Previously computed two-point correlation function for NGC 7793 star clusters  
  > "We have previously computed the correlation function for the star clusters in NGC 7793" (4.4 The Two-Point Correlation Function) [from (cite: grasha17a)]

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

- ALMA data acquisition, reduction and GMC catalog details  
  > "are described in Bittle et al.(in prep). We list here the details necessary for this study." (2.2 The ALMA CO Observations) [from Bittle et al. (in prep)]
- LEGUS cluster selection, photometry, SED fitting  
  > "A detailed description of the cluster selection, identification, photometry, spectral energy distribution (SED) fitting procedures, and completion limits for the LEGUS galaxies is presented in (cite: adamo17)." (3 Creating the Visually-Identified Star Cluster Catalogs) [from (cite: adamo17)]
- Two-point correlation function formalism  
  > "A detailed description of the formalism and methodology of the two-point correlation function as applied to star clusters within other LEGUS galaxies can be found in both (cite: grasha15) and (cite: grasha17a)." (4.4 The Two-Point Correlation Function) [from (cite: grasha15); (cite: grasha17a)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration, CASA version, imaging parameters (robust, deconvolver, masks)
- Final GMC catalog (positions, radii, masses) not released; CO-to-H2 conversion factor not given
- CPROPS kernel and rms values/parameters
- Number of random points and binning for the two-point correlation function
- Fit method for power law slope and error estimation
- Mass-matching procedure details for SFE cuts

## Analysis recipe

1. **Build GMC catalog from CO cube**: CPROPS segmentation of CO(2-1) PPV data  
  > "We create the GMC catalog from the CO(2-1) position-position-velocity data with the CPROPS segmentation algorithm for spectral line emission" (2.3 Creating the GMC Catalog)
   - software: CPROPS
   - parameter: peaks >4σ; emission >2σ in at least two continuous channels; shared contour 3.5σ  
  > "local maxima are identified above 4-$\sigma$. Emission above 2-$\sigma$ that lie in at least two continuous velocity channels around an identified peak is then assigned to that peak." (2.3 Creating the GMC Catalog)
   - assumption: GMCs are significant CO peaks assumed to be cluster-forming structures  
  > "we assume that these correspond to the cluster-forming structures" (2.3 Creating the GMC Catalog)
   - fitting: _not stated_
   - validation: _not stated_
2. **Cluster–GMC separations and age vs distance**: Shortest projected distance from each cluster to nearest GMC center; clusters binned by distance in GMC radii; median ages with bootstrap errors  
  > "We take all the star clusters within the ALMA coverage, reducing the total clusters in the catalog from 370 to 293, and measure the shortest distance to the center of the nearest GMC." (4.1.1 Shortest Distance between Clusters and GMCs)
   - parameter: unassociated defined as >3 R_GMC  
  > "located at distances greater than $3\times R_{\rm GMC}$ from the center of the nearest GMC" (4.2 Properties of Star Clusters Associated with GMCs)
   - assumption: each cluster assigned to only one (closest) GMC  
  > "We do not allow double counting and each cluster can be assigned to only one GMC." (4.2 Properties of Star Clusters Associated with GMCs)
   - fitting: _not stated_
   - validation: Compared to randomized cluster positions preserving radial density; bootstrap of 10,000 samples; mass cut at 5000 Msun check  
  > "We estimate the 1$\sigma$ uncertainties on the median age estimates from bootstrap measurements based on 10,000 samples." (4.2 Properties of Star Clusters Associated with GMCs)
3. **Two-point correlation function of clusters and GMCs**: Landy-Szalay estimator with random catalog matching ALMA coverage; power-law fits of 1+ω(θ) in log-log over 40–800 pc, also with mass/age cuts  
  > "We perform single power law fits in log-log space to both distributions over scale lengths 40–800 pc when $1+\omega(\theta)>1$." (4.4 The Two-Point Correlation Function)
   - software: TreeCorr
   - parameter: SFE of 1% and 3% used to match GMC and cluster mass limits  
  > "match the mass limit between the star clusters and GMCs by assuming a star formation efficiency (SFE) of 1% and 3%" (4.4 The Two-Point Correlation Function)
   - assumption: Fractal dimension D2 = α+2 ≈ 1.5 for ISM  
  > "typical fractal dimension of $D2 = \alpha+2 \simeq 1.5$" (4.4 The Two-Point Correlation Function)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CPROPS** : GMC identification and property measurement  
  > "CPROPS segmentation algorithm for spectral line emission (cite: rosolowsky06)" (2.3 Creating the GMC Catalog)
- **TreeCorr** : listed in software acknowledgement (presumably pair counts)  
  > "*Software*: Astropy (cite: astropy), iPython (cite: ipython), Matplotlib (cite: matplotlib), Numpy (cite: numpy), TreeCorr (cite: treecorr)" (Acknowledgements)
- **SExtractor** : automated cluster candidate extraction  
  > "with source extractor (cite: bertin96)" (3.1 Star Cluster Selection)
- **SLUG** : stochastic cluster property derivation (checked, not used for final)  
  > "Stochastically Lighting Up Galaxies (cite: dasilva12; krumholz15b) code" (3.1 Star Cluster Selection)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| median cluster–GMC distance, all clusters | 53 | ±5 | pc | 2 | the median of the distances is $53\pm5$ pc |
| median distance, clusters <10 Myr | 41 | ±4 | pc | 2 | drops to $41\pm4$ pc |
| clusters within a GMC extent | 13 | not stated | clusters | 2 | we find 13 star clusters (4%) lie within the extent of 12 GMCs |
| median age of clusters within 1 R_GMC | 2 | 1 | Myr | 2 | / $\leq$ 1$R_{\rm GMC}$ / 13 / 12 / 2(1) / |
| median age of unassociated clusters | 7 | 1 | Myr | 2 | / Unassociated / 224 / 492 / 7(1) / |
| cluster drift/erosion velocity (distance/age) | 6.2 | ±0.9 | km/s | 2 | The resulting velocity of 6.2 $\pm$ 0.9 km s$^{-1}$ |
| two-point slope, all star clusters | -0.35 | ±0.02 | dimensionless | 3 | / All                                          / 293  / 8.3$\pm$0.2  / $-$0.35$\pm$0.02 / |
| two-point slope, all GMCs | -0.18 | ±0.02 | dimensionless | 3 | / All                                          / 534  / 3.2$\pm$0.2  / $-$0.18$\pm$0.02 / |
| slope, GMCs >1e5 Msun | -0.44 | ±0.03 | dimensionless | 3 | / Mass $\geq$1$\times$10$^5$ M$_\odot$         / 85   / 18.6$\pm$1.4 / $-$0.44$\pm$0.03 / |
| slope, clusters >=1000 Msun & <=10 Myr | -0.45 | ±0.06 | dimensionless | 3 | / Mass $\geq$1000 M$_\odot$ & Age $\leq$10 Myr / 54   / 20$\pm$3     / $-$0.45$\pm$0.06 / |

## Qualitative findings

- Clusters emerge from natal clouds much faster than cloud dispersal timescales (~10–30 Myr).  
  > "Thus, star clusters are able to emerge from their natal clouds long before the timescale required for clouds to disperse." (abstract)

## Claim tuples

- H: Young clusters are spatially correlated with GMCs and clusters separate from clouds quickly | E: Nearest-GMC distances and age vs distance bins | R: Associated clusters have median age 2 Myr; unassociated 7 Myr; all associated <11 Myr | F: Clusters disassociate from GMCs in 2–3 Myr | **supported**
- H: Cluster hierarchy is inherited from GMC hierarchy | E: Two-point correlation function slopes with and without mass/age cuts | R: Star clusters slope -0.35 vs GMCs -0.18; with cuts -0.45 vs -0.44 | F: Massive clusters trace the same hierarchy as massive GMCs, assuming SFE of a few percent | **supported**
- H: Association timescale differs between NGC 7793 and NGC 5194 | E: Compare relative median ages vs distance | R: Difference significant at 3.2σ | F: Clusters in NGC 7793 clear gas faster in relative units | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Stochastic (SLUG) cluster properties give insensitive results, so only deterministic models used  
  > "in this paper we only consider the cluster properties that are derived with deterministic models that assume a universal IMF." (3.1 Star Cluster Selection)
- How they decided it was enough: _not stated_
- Limitation (authors): Age uncertainties for young clusters are a large fraction of age; small number statistics  
  > "The young ($\ensuremath{\lesssim}$5 Myr) star clusters in this study can have age uncertainties that are a considerable fraction of the actual assigned value." (4.2 Properties of Star Clusters Associated with GMCs)
- Limitation (authors): Extended emission not detected by ALMA, claimed not to affect results  
  > "The non-detection of spatially extended emission should not affect any of the results presented in this paper." (2.2 The ALMA CO Observations)
- Caveat (inferred, ours): Small sample (13 associated clusters); association defined in projection only
- Caveat (inferred, ours): Inconsistent slope for GMCs in summary (-0.25) vs abstract/table (-0.18)
- Caveat (inferred, ours): Uncertainties on slopes differ between abstract (±0.03, ±0.04) and text/table (±0.02)
- Caveat (inferred, ours): CO-dark gas and CO-to-H2 factor affect GMC masses and mass matching

## Reproducibility

- Data public (paper): LEGUS catalog public on MAST; ALMA data cited by project code  
  > "is available online[^3] on the Mikulski Archive for Space Telescopes (MAST)." (3.2 Visual Inspection and Star Cluster Classification)
- Products in archive: _not stated_
- Missing: GMC catalog (Bittle et al. in prep)
- Missing: ALMA calibration and imaging parameters
- Missing: Details of correlation function fitting
- Data volume (inferred): ~50-200 GB raw ALMA (3 hr 12-m mosaic) plus small HST catalog
- Score (inferred): 3/5, Public data and clear analysis outline, but ALMA reduction and GMC catalog deferred to an unpublished paper.
- Rediscovery candidate: no, GMC catalog and imaging recipe are deferred to a paper in preparation, so the recipe is incomplete.

## Links

- Method: (cite: rosolowsky06) (CPROPS GMC identification)
- Method: (cite: adamo17) (LEGUS cluster catalog methodology)
- Method: (cite: grasha17a) (two-point correlation function methodology)
- Companion: Bittle et al. (in prep) (ALMA data reduction and GMC catalog)
- Companion: (cite: grasha18) (same analysis on NGC 5194)
- Related: LEGUS
- Related: PAWS

## Checks

```json
{
 "quotes": 54,
 "quotes_ok": 54,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 36,
  "rate": 0.493
 },
 "evidence_ok": true
}
```
