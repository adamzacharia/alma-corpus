# Simultaneous low- and high-mass star formation in a massive protocluster: ALMA observations of G11.92-0.61<SUP>★</SUP>

`2017MNRAS.468.3694C` | Monthly Notices of the Royal Astronomical Society 2017 | first author: Cyganowski, C. J. | arXiv: 1701.02802 | DOI: 10.1093/mnras/stx043

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Do low-mass cores exist within the accretion reservoir of the massive protostars in G11.92-0.61, and are low- and high-mass stars forming simultaneously?  
  > "designed to search for low-mass cores within the accretion reservoir of the massive protostars." (abstract)
- Target **G11.92-0.61**: coordinates phase centre 18h13m58.110s, -18°54'22.141" (J2000, central mosaic pointing)  
  > "Throughout, we adopt the maser parallax distance to G11.92–0.61 of 3.37$^{+0.39}_{-0.32}$ kpc (cite: Sato2014)." (1 Introduction); z/distance 3.37 kpc  
  > "Throughout, we adopt the maser parallax distance to G11.92–0.61 of 3.37$^{+0.39}_{-0.32}$ kpc (cite: Sato2014)." (1 Introduction); distance from maser parallax (Sato2014)  
  > "Throughout, we adopt the maser parallax distance to G11.92–0.61 of 3.37$^{+0.39}_{-0.32}$ kpc (cite: Sato2014)." (1 Introduction)

## Data provenance

- ALMA projects: 2013.1.00812.S
- bands: 1.05 mm (Cycle 2)  
  > "We observed G11.92$-$0.61 at 1.05 mm with ALMA in Cycle 2, with 37 antennas available for the observations." (2.1 ALMA)
- frequencies and spectral setup: Two wide spws (LSB 278.2 GHz, USB 292.0 GHz centres, 1.875 GHz each) plus five narrow spws (N2H+, DCN, 34SO, H2CO, C33S)  
  > "The ALMA correlator was configured to cover seven spectral windows (spws): two with wide bandwidths and relatively coarse spectral resolution for continuum sensitivity" (2.1 ALMA)
- continuum bandwidth: ~2.4 GHz line-free  
  > "The total "line-free" bandwidth used for our final continuum image is $\sim$2.4 GHz." (2.1 ALMA)
- arrays: _not stated_
- configurations: C34-3/(4)  
  > "| Configuration | C34-3/(4) | Extended | A | B |" (Table 1)
- baselines: ~21-542 kλ projected  
  > "the projected baselines ranged from $\sim$21-542 k$\lambda$." (2.1 ALMA)
- angular resolution: 0.49" x 0.34" (continuum)  
  > "This yields a synthesised beam of 0.49$''$$\times$0.34$''$" (2.1 ALMA)
- max recoverable scale: ~8" (~0.13 pc)  
  > "The largest angular scale on which the observations are sensitive to smooth structures is $\sim$8$''$" (2.1 ALMA)
- sensitivity: continuum rms 0.35 mJy/beam representative (0.25 to >0.5 varying)  
  > "| Continuum rms noise$^{e}$ | 0.35 mJy beam$^{-1}$ |" (Table 1)
- time on source: 44 minutes  
  > "The total time on-source was 44 minutes" (2.1 ALMA)
- observing dates: 2015 May 14  
  > "| Observing date (UT) | 2015 May 14 | 2011 Aug 19 | 2015 Jun 25 | 2015 Feb 9-10 |" (Table 1)
- pi or archival as stated: _not stated_
- Line: DCN 4-3 (289.64492 GHz)
- Line: H2CO 4(0,4)-3(0,3) (290.62341 GHz)
- Line: N2H+ 3-2 (279.51175 GHz)
- Line: CH3OH 9(-1)-8(0) (278.30451 GHz)
- Other facility **SMA**: 12CO(3-2) outflow data (0.88 mm), previously published  
  > "here, we consider only the $^{12}$CO(3-2) data." (2.2 SMA and VLA)
- Other facility **VLA**: 3 cm and 0.9 cm images for centimetre counterparts  
  > "The VLA 3 cm and 0.9 cm data were used by (cite: Ilee2016) to study G11.92$-$0.61 MM1" (2.2 SMA and VLA)
- Other facility **ATLASGAL**: 870 um clump flux density  
  > "We measure an integrated flux density of 11.0$\pm$0.3 Jy from the ATLASGAL 870 $\mu$m map" (4.1)
- External data: Dust opacity kappa_1.05mm = 1.45 cm2/g (thick ice mantles)  
  > "we adopt $\kappa_{\rm 1.05mm}=$1.45 cm$^2$ g$^{-1}$, for grains with thick ice mantles in regions of high gas density (cite: OH94)" (4.1) [from (cite: OH94)]
- External data: MM1 and MM6 outflow properties from 12CO(2-1) SMA  
  > "MM1 outflow: from (cite: C11sma), rescaled for D=3.37 kpc." (Table 3) [from (cite: C11sma)]

## Processing

### Calibration

- pipeline or manual: ALMA calibration pipeline  
  > "The ALMA data were calibrated using the CASA 4.2.2 version of the ALMA calibration pipeline." (2.1 ALMA)
- casa version: CASA 4.2.2  
  > "The ALMA data were calibrated using the CASA 4.2.2 version of the ALMA calibration pipeline." (2.1 ALMA)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan  
  > "Titan was used to set the absolute flux scale" (2.1 ALMA)
- flux scale uncertainty: ~10%  
  > "we estimate the absolute flux uncertainty to be $\sim$10%." (2.1 ALMA)
- self calibration: continuum iteratively self-calibrated, solutions applied to line data  
  > "The continuum data were iteratively self-calibrated, and the solutions applied to the line data." (2.1 ALMA)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: continuum robust 0; line cubes robust 0.5  
  > "The final ALMA continuum image was made using multi-frequency synthesis and a robust weighting parameter of 0." (2.1 ALMA); "The line image cubes were made with a robust weighting parameter of 0.5" (2.1 ALMA)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: line-free channels used for continuum subtraction  
  > "To select line-free channels for continuum imaging and continuum subtraction" (2.1 ALMA)
- line free channels: threshold tests on dirty line+continuum cubes; C33S spw omitted; 10-15% residual line contamination in MM1  
  > "we first made dirty line+continuum cubes of the seven ALMA spws. Using these cubes, we tested different threshold levels for line-free channel identification" (2.1 ALMA)
- primary beam correction: all measurements from primary-beam-corrected images  
  > "All measurements were made from images corrected for the primary beam response." (2.1 ALMA)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.49" x 0.34" continuum  
  > "| Synthesised beam$^{d}$ | 0.49$''$$\times$0.34$''$ |" (Table 1)
- final rms: _not stated_

### Inherited from earlier work

- Line-free channel selection approach similar to Brogan2016  
  > "this approach is similar to that used by (cite: Brogan2016) in their study of NGC6334I, with two line-rich hot cores" (2.1 ALMA) [from (cite: Brogan2016)]
- Outflow property method similar to C11sma  
  > "using an approach similar to that of (cite: C11sma)" (4.2 Outflow properties) [from (cite: C11sma)]
- T_dust = 20 K  
  > "T$_{\rm dust}=$20 K (cite: Brogan2011)" (4.1) [from (cite: Brogan2011)]
- SMA data reduction described in earlier paper  
  > "The SMA 0.88 mm dataset was used by (cite: Cyganowski2014) to study the candidate massive prestellar core G11.92$-$0.61 MM2, and is described in that publication." (2.2 SMA and VLA) [from (cite: Cyganowski2014)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges and the exact threshold adopted
- Self-calibration solution intervals and number of iterations
- Cell size, image size, clean threshold and masks
- Source-finding procedure beyond the local 5 sigma criterion
- SMA and VLA calibration details (only in earlier papers)
- Software used for Gaussian fitting beyond CASA IMFIT

## Analysis recipe

1. **Build continuum image and detect sources**: Line-free pseudo-continuum, multi-frequency synthesis, self-calibration; sources >5 sigma local rms  
  > "we detect 16 new sources at $>$5$\sigma$" (3.1)
   - software: CASA
   - parameter: robust = 0; ~2.4 GHz line-free bandwidth  
  > "a robust weighting parameter of 0." (2.1 ALMA)
   - fitting: _not stated_
   - validation: VLA 3 cm and 0.9 cm nondetections check against free-free emission  
  > "None of MM4...MM19 are detected in the VLA images" (3.1)
2. **Measure source properties**: Two-dimensional Gaussian fits (single or multiple components) for peak, integrated flux, size  
  > "as determined from two-dimensional Gaussian fits" (3.1)
   - software: CASA IMFIT
   - fitting: Multi-component Gaussians for MM1-MM3; zero-level offsets for MM1 and MM11  
  > "To obtain a reasonably good fit, MM1-C3 was fit separately (while MM1-C1 and MM1-C2 were fit simultaneously, with a two-component Gaussian fit) and a zero-level offset of 0.77 mJy beam$^{-1}$ was required." (Table 1 footnotes (continuum properties table))
   - validation: noise-like residuals  
  > "require multiple Gaussian components to obtain reasonably noise-like residuals" (3.1)
3. **Derive core masses, densities, free-fall times**: Isothermal dust emission with opacity correction  
  > "which assumes isothermal dust emission and includes a correction for dust opacity" (4.1)
   - assumption: gas-to-dust 100, kappa 1.45 cm2/g, T_dust 20 K, D 3.37 kpc, mu_H2 2.8, spherical  
  > "R is the gas-to-dust mass ratio (assumed to be 100)" (4.1)
   - fitting: _not stated_
   - validation: Compared with nearby low-mass cores; 15 K case as sensitivity check  
  > "these values increase to $\sim$33 M$_{\odot}$ and $\sim$5% if we instead assume T$_{\rm dust}$=15 K" (4.1 Low-mass cores in a massive protocluster)
4. **Derive outflow properties**: Optically thin mass per channel in 3 sigma moment-0 masks; momentum, energy, dynamical times  
  > "we define a mask based on the 3$\sigma$ contour in the integrated intensity image (moment 0 map) of that lobe." (4.2 Outflow properties)
   - software: Splatalogue, CDMS
   - assumption: T_ex=30 K, X_CO=1e-4, X_H2CO=1e-8, v_LSR=35 km/s, no inclination correction  
  > "We adopt T$_{ex}$=30 K, $\chi_{\rm CO}$=10$^{-4}$ (cite: Dunham2014), and $\chi_{\rm H_{2}CO}$=10$^{-8}$" (4.2 Outflow properties)
   - fitting: _not stated_
   - validation: Compare CO(3-2), CO(2-1) and H2CO estimates for the same outflows  
  > "we find remarkably good agreement (within a factor of 2) for the total outflow mass and mass outflow rate" (4.2 Outflow properties)

## Software

- **CASA** 4.2.2: Calibration pipeline, imaging, IMFIT  
  > "The ALMA data were calibrated using the CASA 4.2.2 version of the ALMA calibration pipeline." (2.1 ALMA)
- **Astropy** : Python analysis  
  > "Astropy, a community-developed core Python package for Astronomy" (Acknowledgements)
- **APLpy** : Plotting  
  > "APLpy, an open-source plotting package for Python" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of new continuum sources | 16 | not stated | sources | 1 | we detect 16 new sources at $>$5$\sigma$ |
| Median core mass | 1.3 | not stated | Msun | 3 | with a median mass of 1.3 M$_{\odot}$ and a median radius of $\sim$1600 au |
| Core mass range | 0.2-2.8 | not stated | Msun | 3 | range from 0.2-2.8 M$_{\odot}$ |
| Median projected separation from MM1 | ~0.17 | not stated | pc | 3 | the median offset from MM1 of the low-mass cores is $\sim$0.17 pc |
| Total mass of MM4..MM18 (T=20 K) | ~22 | not stated | Msun | 3 | The total mass of the newly-detected ALMA sources MM4..MM19 is $\sim$22 M$_{\odot}$, or $\sim$3% of the ATLASGAL clump mass |
| ATLASGAL flux within mosaic | 11.0 | 0.3 | Jy | 0 | We measure an integrated flux density of 11.0$\pm$0.3 Jy from the ATLASGAL 870 $\mu$m map |
| MM12 outflow mass (H2CO) | 0.09 | not stated | Msun | 4 | / M$_{\rm out}$-total (M$_{\odot}$) / 0.09 / 0.05 / |
| MM6 outflow mass (12CO(3-2)) | 0.02 | not stated | Msun | 4 | / M$_{\rm out}$-total (M$_{\odot}$) / 0.02 / 0.03 / 0.10 / 0.04 / 0.6 / |

## Qualitative findings

- Newly detected sources lie mostly in the outer accretion reservoir and most have no compact line emission  
  > "Most of the new sources are located in the outer reaches of the accretion reservoir" (abstract)

## Claim tuples

- H: Low-mass cores exist in the accretion reservoir of the massive protostars | E: 1.05 mm ALMA mosaic, source extraction and mass estimates | R: 16 new sources, median mass 1.3 Msun, radius 1600 au | F: Sources are low-mass prestellar/protostellar cores | **supported**
- H: Low- and high-mass stars form simultaneously | E: Outflow detection in SMA CO(3-2) and ALMA H2CO/CH3OH | R: Outflows from MM6, MM7/9, MM12 as well as MM1 | F: Concurrent accretion, consistent with competitive accretion models | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: MM19 may be optically thick free-free rather than a core; cannot be ruled out  
  > "we cannot rule out optically thick free-free as an explanation for its millimetre emission" (4.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Outflow masses are underestimates due to spatial filtering, cloud confusion and optical depth  
  > "All of these factors act to make our estimated outflow masses underestimates" (4.2 Outflow properties)
- Caveat (inferred, ours): Core masses depend on assumed fixed T_dust=20 K and kappa
- Caveat (inferred, ours): Residual line contamination (10-15%) in MM1 continuum
- Caveat (inferred, ours): Single protocluster cannot establish coeval onset
- Caveat (inferred, ours): Outflow driving sources are assigned by morphology without measured LSR velocities

## Reproducibility

- Data public (paper): ALMA project 2013.1.00812.S acknowledged  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00812.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Line-free channel ranges
- Missing: Self-calibration parameters
- Missing: Cell and image sizes, clean settings
- Data volume (inferred): tens of GB (single 7-pointing mosaic, 7 spws)
- Score (inferred): 3/5, Public data and clear calculation recipe, but imaging and self-calibration details are missing.
- Rediscovery candidate: yes, Public ALMA data; source table and mass equations with stated assumptions allow redoing the numeric results.

## Links

- Method: (cite: Brogan2016) (line-free channel identification approach)
- Method: (cite: C11sma) (outflow property method)
- Companion: (cite: Ilee2016) (MM1 Keplerian disc using SMA/VLA)
- Companion: (cite: Cyganowski2014) (MM2 massive starless core candidate, SMA data)
- Related: ATLASGAL

## Checks

```json
{
 "quotes": 69,
 "quotes_ok": 69,
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
  "facts": 73,
  "stated": 52,
  "rate": 0.712
 },
 "evidence_ok": true
}
```
