# The Association of Molecular Gas and Natal Super Star Clusters in Henize 2-10

`2018ApJ...853..125J` | The Astrophysical Journal 2018 | first author: Johnson, Kelsey E. | arXiv: 1712.02791 | DOI: 10.3847/1538-4357/aa9ff8

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, nearby_galaxies, astrochemistry
- Question: What are the molecular gas conditions (line ratios, gas mass, line widths) around natal super star clusters in the dwarf starburst He 2-10, and do they trace cluster evolution?  
  > "Our goal in this program is to utilize the sensitivity and resolution of ALMA to investigate the physical conditions associated with the so-called “super star clusters”." (1 Introduction)
- Target **Henize 2-10 (He 2-10)**: coordinates _not stated_; z/distance D ~ 9 Mpc  
  > "He 2-10 is the nearest ($D\sim 9$ Mpc) galaxy known to host *multiple* nascent super star clusters" (1.1 The Target Galaxy: Henize 2-10); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00348.S
- bands: Band 3 (86.9-90.7 GHz and 98.8-102.5 GHz)  
  > "Henize 2-10 was observed with ALMA Band 3 (86.9-90.7 GHz and 98.8-102.5 GHz)" (2 Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: 7 GHz in 4 spectral windows  
  > "the remaining 7GHz of bandwidth in 4 spectral windows was combined to create a 3.3 mm continuum image" (2 Observations)
- arrays: _not stated_
- configurations: _not stated_
- baselines: ~50-400 m projected; 15-25 antennas  
  > "with the number of antennas on-line varying between 15-25 and projected baseline lengths from $\sim 50-400$ m" (2 Observations)
- angular resolution: 1.7x1.6 arcsec lines; 1.6x1.5 arcsec continuum  
  > "imaged at $1.''7 \times 1.''6$ (75 pc$\times$70 pc) resolution" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: line rms 0.45 mJy/beam per 10 km/s; continuum 1.1e-5 Jy/beam  
  > "with an rms of 0.45 mJy$\;$bm$^{-1}$ per 10$\;$km$\;$s$^{-1}$ channel" (2 Observations)
- time on source: 3.6 hours  
  > "The total time on source was 3.6 hours" (2 Observations)
- observing dates: May-December 2012  
  > "between May and December of 2012" (2 Observations)
- pi or archival as stated: _not stated_
- Line: HCO+ 1-0 (not stated)
- Line: HCN 1-0 (not stated)
- Line: HNC 1-0 (not stated)
- Line: CCH 1-0 (hyperfine blend) (87.317 and 87.329 GHz)
- Other facility **SMA**: CO(2-1) data, 1.9x1.3 arcsec, compact+extended  
  > "We also incorporate existing SMA CO(2-1) observations with a resolution of $1.''9 \times 1.''3$ (cite: santangelo09)" (2 Observations)
- External data: SMA CO(2-1) observations and reduction  
  > "The original observations and data reduction are described in (cite: santangelo09)." (2 Observations) [from (cite: santangelo09)]
- External data: Radio 3.6 cm data used to extrapolate free-free emission  
  > "Based on the radio observations of (cite: jk03), we can extrapolate the free-free contribution to 88 GHz" (3.6.1 88 GHz Continuum) [from (cite: jk03)]
- External data: Single-dish CO(3-2) intensity and CO(3-2)/(2-1) ratio  
  > "(cite: meier01) present single dish observations of He 2-10 using the CO(3-2) transition with a total intensity $I_{CO} = 16.6$ K km s$^{-1}$" (3.5 Comparison Between Single Dish and Interferometric Observations) [from (cite: meier01)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan and Ceres  
  > "Titan and Ceres were used as the primary amplitude calibrators" (2 Observations)
- flux scale uncertainty: ~15%  
  > "we estimate the flux uncertainty to be $\sim 15$%" (2 Observations)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust 0.5  
  > "Synthesis images were created with Briggs weighting and a robust parameter of 0.5." (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: spectral regions around emission lines flagged; remainder combined for continuum  
  > "Spectral regions around the emission lines were flagged" (2 Observations)
- line free channels: _not stated_
- primary beam correction: not applied; PB 55" much larger than galaxy (10")  
  > "so no primary beam correction is required" (2 Observations)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: 0.45 mJy/beam per 10 km/s (lines)  
  > "with an rms of 0.45 mJy$\;$bm$^{-1}$ per 10$\;$km$\;$s$^{-1}$ channel" (2 Observations)

### Inherited from earlier work

- SMA CO(2-1) observations and data reduction  
  > "The original observations and data reduction are described in (cite: santangelo09)." (2 Observations) [from (cite: santangelo09)]
- Gas mass from dust continuum formula  
  > "the total dust continuum flux density can be used to calculate the total gas mass following (cite: lh97):" (3.6.1 88 GHz Continuum) [from (cite: lh97)]

### Not stated but needed to reproduce (our reading)

- CASA version and whether the pipeline or manual calibration was used
- Line-free channels for continuum, cell and image size, deconvolver, masking, clean thresholds
- Self-calibration choices
- Spectral window frequencies and channelization
- Beta value used to scale the dust opacity to 88 GHz
- PCA implementation details
- Flux calibrator models and the phase calibrator for the full dataset

## Analysis recipe

1. **Image continuum and lines**: Briggs weighting robust 0.5; line-free spectral windows combined into continuum image; line cubes at 10 km/s  
  > "Synthesis images were created with Briggs weighting and a robust parameter of 0.5." (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Moment maps and aperture photometry**: Moment 0 over 770-935 km/s; moment 8 maps with thresholds; fluxes in r=0.8" apertures; uncertainty from recentering dispersion, 20% calibration, rms  
  > "Fluxes were measured in r=0.8$''$ circular apertures on the image integrated in velocity from 770 to 935 km$\;$s$^{-1}$." (3.1 Morphology of the molecular emission)
   - assumption: alpha_CO = 4.3 Msun pc^-2 (K km/s)^-1; CO(2-1)=0.5xCO(1-0); 9 Mpc  
  > "adopting a conversion of CO(2-1)$= 0.5\times$CO(1-0)" (3.1.1 CO(2-1) Emission)
   - fitting: _not stated_
   - validation: _not stated_
3. **Line widths and cloud size**: Gaussian fits in CASA per region; compare CO luminosity vs sigma via rearranged Heyer et al. relation for radii 8,16,32 pc  
  > "were fit with a Gaussian model and measured in CASA" (3.2 Line Widths)
   - software: CASA
   - fitting: Gaussian  
  > "The width of the emission lines from each of the regions identified in Figure [6](#Mom8_regions) were fit with a Gaussian model and measured in CASA." (Line Widths)
   - validation: _not stated_
4. **Principal component analysis**: PCA of rms-normalized integrated intensity images within CO 3-sigma region  
  > "here we show the results when images are normalized by their rms." (3.3 Principle Component Analysis)
   - fitting: _not stated_
   - validation: Peak vs rms normalization and thresholds of 2.5-4 sigma give consistent results  
  > "The results are not sensitive to choices for that threshold between 2.5 and 4$\sigma$." (3.3 Principle Component Analysis)
5. **Gas mass from 88 GHz dust continuum**: Subtract free-free extrapolated from 3.6 cm with alpha=-0.1; apply Launhardt & Henning formula  
  > "we can extrapolate the free-free contribution to 88 GHz assuming a standard spectral index of $\alpha=-0.1$." (3.6.1 88 GHz Continuum)
   - assumption: optically thin, isothermal, T=25 K, kappa_88GHz=0.0007 cm2/g  
  > "We assume the emission is optically thin isothermal emission, and a temperature of 25 K." (3.6.1 88 GHz Continuum)
   - fitting: _not stated_
   - validation: Compared with Kobulnicky 1995 CO-based gas mass  
  > "This value **is** broadly consistent with that inferred by (cite: kobulnicky95) of $1.6-9.6\times 10^8$ M$_\odot$ based on CO(1-0) observations." (3.6.1 88 GHz Continuum)

## Software

- **CASA** : Gaussian line-width fitting  
  > "were fit with a Gaussian model and measured in CASA" (3.2 Line Widths)
- **yt** : Rotations of full velocity cubes  
  > "Rotations of the full velocity cubes created with the *yt* program (cite: turk11)" (2 Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 88 GHz integrated flux density | 11.4 | 1.7 | mJy | 5 | with an integrated flux density of $F_{88GHz} = 11.4\pm 1.7$ mJy |
| Total gas mass | 4-6e8 | not stated | Msun | 5 | The resulting gas mass is $M_{gas} = 4-6\times 10^{8}$ M$_\odot$. |
| Dust flux at 88 GHz | 4.2-6.5 | not stated | mJy | 5 | the 88 GHz emission due to dust is $4.2$ mJy. |
| SMA CO(2-1) integrated intensity | 382 | 12 | Jy km/s | 0 | integrated CO(2-1) intensity of $382\pm12$ Jy km s$^{-1}$ |
| ALMA HCN(1-0) integrated flux | 1.27 | 0.15 | Jy km/s | 0 | we measure a HCN(1-0) integrated flux of $1.27\pm0.15$ Jy km s$^{-1}$ |

## Qualitative findings

- HCO+ is the best general tracer of molecular emission per PCA  
  > "Based on a principle component analysis, HCO$^+$ is found to be the best “general” tracer of molecular emission." (abstract)

## Claim tuples

- H: Natal SSC regions have distinct molecular line ratios | E: Aperture photometry of 21 regions in five lines | R: Thermal radio regions all have CO(2-1)/HCO+ < 16 (except H) | F: Line ratios separate natal cluster regions | **supported**
- H: Gas mass derived from dust continuum | E: Subtract free-free and apply dust mass formula | R: Mgas = 4-6e8 Msun | F: 5-20% of dynamical mass | **supported**
- H: HNC/HCN is lowest near natal clusters | E: Compare HNC/HCN across regions | R: Ratios 0.3-1 with no clear minimum near clusters | F: Hypothesis not confirmed | **refuted**
- H: HCO+/CO traces cluster evolution | E: Compare ratios with cluster ages and the Antennae Firecracker | R: CO/HCO+ ∝ age^-1 | F: Ratio correlates with evolutionary stage | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Interferometer recovers only ~64% of single-dish HCN flux; free-free contamination may overestimate gas mass  
  > "suggesting that these ALMA observations only recover $\sim 64$% of the HCN(1-0) emission" (3.5 Comparison Between Single Dish and Interferometric Observations)
- Caveat (inferred, ours): Gas mass depends on assumed kappa, T=25 K and free-free subtraction
- Caveat (inferred, ours): Weak HNC and CCH detections (3-5 sigma)
- Caveat (inferred, ours): Evolution trend rests on few sources with uncertain ages
- Caveat (inferred, ours): Regions are unresolved and beam-averaged

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters beyond robust
- Missing: Spectral windows and line-free channels
- Missing: Exact PCA implementation
- Missing: Reduced SMA data
- Data volume (inferred): ~10-50 GB raw
- Score (inferred): 3/5, Project code and key assumptions are given, but imaging and calibration details are sparse.
- Rediscovery candidate: no, Imaging details and the SMA data are incompletely specified.

## Links

- Method: (cite: lh97) (Dust-continuum gas mass formula)
- Method: (cite: heyer09) (Size-linewidth-surface density relation)
- Companion: (cite: santangelo09) (SMA CO(2-1) data)
- Companion: (cite: kepley16) (Similar ALMA observations of IIZw40)

## Checks

```json
{
 "quotes": 50,
 "quotes_ok": 50,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 35,
  "rate": 0.5
 },
 "evidence_ok": true
}
```
