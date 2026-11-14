# Constraining globular cluster formation through studies of young massive clusters - V. ALMA observations of clusters in the Antennae

`2015MNRAS.448.2224C` | Monthly Notices of the Royal Astronomical Society 2015 | first author: Cabrera-Ziri, I. | arXiv: 1501.05657 | DOI: 10.1093/mnras/stv163

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation, nearby_galaxies
- Question: Do young massive clusters in the Antennae (50-200 Myr) contain the large molecular gas reservoirs required by AGB-type multiple-population GC formation scenarios?  
  > "we use deep observations taken with Atacama Large Millimeter/sub-millimeter Array (ALMA) to assess the amount of molecular gas within 3 young ($50-200$ Myr) massive ($\sim10^6$ M$_\odot$) clusters in the Antennae galaxies." (abstract)
- Target **W31730, W32604, W32187 (Antennae clusters)**: coordinates W31730 12 01 55.462 -18 52 19.108; W32604 12 01 55.354 -18 52 17.824; W32187 12 01 55.184 -18 52 18.442  
  > "W32187, W32604 and W31730 (from east to west respectively, W10)" (Data); "a luminosity distance of $D_\text{L}= 21.8$ Mpc to the Antennae galaxies and a redshift of $z=0.005688$" (Molecular gas and stellar mass estimates); z/distance D_L = 21.8 Mpc, z = 0.005688  
  > "W32187, W32604 and W31730 (from east to west respectively, W10)" (Data); "a luminosity distance of $D_\text{L}= 21.8$ Mpc to the Antennae galaxies and a redshift of $z=0.005688$" (Molecular gas and stellar mass estimates); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00876.S
- bands: Band 7 (345 GHz), Cycle 0  
  > "We made use of “Band 7" (345 GHz) ALMA observations of the Antennae galaxies (NGC 4038/39) from Cycle 0 project 2011.0.00876." (Data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: synthesised beam 0.56"x0.43"; channel spacing 5 km/s  
  > "For these observations the channel spacing is 5 km/s and the synthesised beam size is 0.56"$\times$0.43"." (Data)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO 3-2 (not stated)
- Other facility **HST**: Imaging (ACS V-band, I-band) for cluster positions and sizes  
  > "All spectra were extracted from single beams taken from the approximate I-band intensity peak." (Data)
- External data: Cluster ages and photometric masses  
  > "The ages and photometric masses are from W10." (Molecular gas and stellar mass estimates) [from Whitmore et al. 2010 (cite: Whitmore:2010p2561)]
- External data: CO(3-2)/CO(1-0) ratio r31=0.792, averaged from Table 2  
  > "this value was obtained averaging the measurements of $r_{31}$ reported for the Antennae on Table 2 from (cite: Zhu:2003p2569)." (Molecular gas and stellar mass estimates) [from Zhu et al. 2003 (cite: Zhu:2003p2569)]
- External data: Velocity dispersions and dynamical masses (recalculated with new sizes)  
  > "We remeasured the sizes of these clusters and used these values to recalculate the dynamical masses of (cite: Mengel:2008p2564), hereafter M08." (Molecular gas and stellar mass estimates) [from Mengel et al. 2008 (cite: Mengel:2008p2564)]

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
- primary beam correction: spectra are primary beam corrected  
  > "Fig. [2](#spec) shows the spectra of the (primary beam corrected) CO (3–2) emission towards the three clusters in units of mJy/beam." (Data)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA observations and data reduction  
  > "A detailed description of these observations and data reduction can be found in (cite: Whitmore:2014p2682)" (Data) [from (cite: Whitmore:2014p2682)]
- Size measurement technique with ISHAPE  
  > "(see (cite: Bastian:2009p1988) for more details on the technique)" (Molecular gas and stellar mass estimates) [from (cite: Bastian:2009p1988)]
- H2 mass equation  
  > "Following equation (3) in (cite: Bolatto:2013p2560):" (Molecular gas and stellar mass estimates) [from (cite: Bolatto:2013p2560)]

### Not stated but needed to reproduce (our reading)

- Calibration, CASA version and imaging parameters (all deferred to Whitmore et al. 2014)
- How the spectrum rms was measured (channel range, line-free channels)
- Configuration, time on source, sensitivity
- Details of binning to 10/20 km/s

## Analysis recipe

1. **Extract CO(3-2) spectra at cluster positions**: Single-beam spectra at I-band intensity peak, primary-beam corrected, binned to 10 or 20 km/s  
  > "All spectra were extracted from single beams taken from the approximate I-band intensity peak." (Data)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive 1-sigma upper limits on H2 mass**: S_CO Δv = F_rms Δv / r31, then Bolatto et al. 2013 eq. 3  
  > "we assumed this value to be the standard deviation of the flux, $\sigma$, for these spectra" (Molecular gas and stellar mass estimates)
   - parameter: r31 = 0.792  
  > "We adopted $r_{31}=0.792$" (Molecular gas and stellar mass estimates)
   - assumption: X_CO = 2e20 cm^-2 (K km/s)^-1, D_L = 21.8 Mpc, z = 0.005688  
  > "we assume a CO (1–0)-to-H$_2$ conversion factor of $X_\text{CO} = 2 \times 10^{20} \text{ cm}^{-2} (\text{K km/s})^{-1}$" (Molecular gas and stellar mass estimates)
   - fitting: _not stated_
   - validation: _not stated_
3. **Remeasure cluster sizes and dynamical masses**: ISHAPE fits on ACS V-band images with empirical PSF  
  > "we made an empirical PSF based on ACS $V$-band drizzled images and used ISHAPE (cite: Larsen:1999p2562) to measure the effective radii adopting different profiles" (Molecular gas and stellar mass estimates)
   - software: ISHAPE
   - fitting: _not stated_
   - validation: Photometric and dynamical masses agree  
  > "We find excellent agreement between the photometric and dynamical masses." (Molecular gas and stellar mass estimates)
4. **Toy model of expected gas mass in AGB scenario**: Compute 2G mass from 1:1 ratio and SFE=1/3, divide gas over 50 Myr window with SF timescale  
  > "if we adopt a standard star-formation efficiency for this cluster of SFE=$1/3$ (e.g. (cite: Lada:2003p2573)), this means that M$_{gas}^{\text{2G}}=7.5\times10^5$ M$_{\odot}$" (Toy model)
   - assumption: current mass ~4x the mass at 10 Gyr; 1:1 1G:2G  
  > "assume that the current mass of the cluster is $\sim4$ times more massive than it will be in $\sim10$ Gyr" (Toy model)
   - fitting: _not stated_
   - validation: Agrees with D08 for Δt_SF = 0.6 Myr  
  > "a good agreement is achieved between D08 model and our “toy model", if one adopts a relatively short $\Delta t^{\text{2G}}_{SF}$ of 0.6 Myr." (Summary of the toy model and comparison with previous works)

## Software

- **ISHAPE** : Effective radius measurement of clusters  
  > "used ISHAPE (cite: Larsen:1999p2562) to measure the effective radii" (Molecular gas and stellar mass estimates)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| H2 mass 1-sigma upper limit, W31730 | 1.25 (2.01 binned) | not stated | 1e5 Msun | 2 | 1.25 (2.01)$^b$ |
| H2 mass 1-sigma upper limit, W32604 | 1.40 (3.56 binned) | not stated | 1e5 Msun | 2 | 1.40 (3.56)$^c$ |
| H2 mass 1-sigma upper limit, W32187 | 1.38 (2.17 binned) | not stated | 1e5 Msun | 2 | 1.38 (2.17)$^b$ |
| Gas fraction upper limits (W31730, W32604, W32187) | 7.4, 8.8, 7.3 | not stated | % of stellar mass | 2 | or 7.4, 8.8, and 7.3 % of their stellar mass, respectively |

## Qualitative findings

- No significant CO(3-2) emission associated with any of the three clusters.  
  > "No significant CO(3–2) emission was found associated with any of the three clusters." (abstract)

## Claim tuples

- H: Young massive clusters host large cold gas reservoirs as required by AGB scenarios | E: Search for CO(3-2) in ALMA spectra of three Antennae clusters and convert to H2 limits | R: Upper limits ~1e5 Msun, <9% of stellar mass | F: Results in tension with scenarios predicting large gas reservoirs, notably CS11 | **supported**
- H: D08 AGB scenario is constrained by the data | E: Toy model comparison | R: Consistent with D08 for short SF timescales; less extreme parameters would give detectable gas | F: Not conclusive in ruling out the AGB scenario | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Upper limits depend on X_CO, which may be overestimated by up to an order of magnitude  
  > "We note, however, that the adopted $X_\text{CO}$ may be overestimated by up to an order of magnitude" (Conclusions)
- Caveat (inferred, ours): Limits are 1-sigma, not conventional 3-sigma
- Caveat (inferred, ours): Single-beam rms used as sigma without stated measurement region
- Caveat (inferred, ours): Cluster positions had to be corrected for an offset
- Caveat (inferred, ours): Toy model depends on several assumptions

## Reproducibility

- Data public (paper): Cycle 0 project 2011.0.00876 data used; public status not explicitly stated  
  > "This paper makes use of ALMA data: ADS/JAO.ALMA#2011.0.00876.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Calibration and imaging details (in Whitmore et al. 2014)
- Missing: rms measurement ranges
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Simple calculation with clear formula and values, but reduction and imaging are deferred to another paper.
- Rediscovery candidate: no, Reduction details are inherited from another paper and spectrum extraction is under-specified.

## Links

- Method: Whitmore et al. 2014 (cite: Whitmore:2014p2682) (ALMA observations and data reduction)
- Method: Bolatto et al. 2013 (cite: Bolatto:2013p2560) (H2 mass equation)
- Companion: Bastian et al. 2013 (cite: Bastian:2013p2022) (Earlier paper in series: ionised gas in YMCs)

## Checks

```json
{
 "quotes": 37,
 "quotes_ok": 37,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 26,
  "rate": 0.382
 },
 "evidence_ok": true
}
```
