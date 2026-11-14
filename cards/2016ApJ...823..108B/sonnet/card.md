# A Comprehensive Dust Model Applied to the Resolved Beta Pictoris Debris Disk from Optical to Radio Wavelengths

`2016ApJ...823..108B` | The Astrophysical Journal 2016 | first author: Ballering, Nicholas P. | arXiv: 1605.01731 | DOI: 10.3847/0004-637X/823/2/108

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: debris_disks
- Question: Can varying the dust composition (optical constants) let a single model fit both thermal emission and scattered light of the beta Pic debris disk?  
  > "We investigate whether varying the dust composition (described by the optical constants) can solve a persistent problem in debris disk modeling—the inability to fit the thermal emission without over-predicting the scattered light." (abstract)
- Target **beta Pictoris**: coordinates _not stated_; z/distance 19.44 pc  
  > "$\beta$ Pic is a 21–24 Myr-old (cite: binks2014; binks2016) A6V star located at a distance of 19.44 pc (cite: vanleeuwen2007)" (2 Stellar Properties); distance from van Leeuwen 2007  
  > "$\beta$ Pic is a 21–24 Myr-old (cite: binks2014; binks2016) A6V star located at a distance of 19.44 pc (cite: vanleeuwen2007)" (2 Stellar Properties)

## Data provenance

- ALMA projects: _none stated_
- bands: ALMA 870 micron continuum  
  > "We used the ALMA 870 $\ensuremath{\mu}m$ continuum image previously published by (cite: dent2014)." (ALMA)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: beam 0.709" x 0.556"  
  > "$b_\text{maj}=0.709\ensuremath{''}$ and $b_\text{min}=0.556\ensuremath{''}$ are the FWHM of the Gaussian beam major and minor axes" (ALMA)
- max recoverable scale: _not stated_
- sensitivity: 0.061 mJy rms  
  > "combining 0.061 mJy rms uncertainty and 10% calibration uncertainty in quadrature" (ALMA)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **HST/STIS**: 0.58 micron scattered light image (GO-12551)  
  > "under program GO-12551 (PI: Apai)" (HST/STIS)
- Other facility **HST/WFC3**: 1.16 micron scattered light image, GO-11150, first published here  
  > "from program GO-11150 (PI: Graham)" (HST/WFC3)
- Other facility **Spitzer/MIPS**: 24 micron image and 70/160 micron photometry  
  > "The data at all three bands (24, 70, and 160 $\ensuremath{\mu}m$) are published here for the first time." (Spitzer/MIPS)
- Other facility **Herschel/PACS**: 70 micron image  
  > "PACS 70 $\ensuremath{\mu}m$ scan map observations of $\beta$ Pic (PI G. Olofsson, observation IDs 1342186612 and 1342186613)" (Herschel/PACS at 70 micron)
- External data: ALMA 870 micron continuum image and beam parameters  
  > "We used the ALMA 870 $\ensuremath{\mu}m$ continuum image previously published by (cite: dent2014)." (ALMA) [from Dent et al. 2014 (cite: dent2014)]
- External data: HST/STIS star-subtracted disk image  
  > "the results of these observations were published in (cite: apai2015)" (HST/STIS) [from (cite: apai2015)]
- External data: Optical constants: astronomical silicates  
  > "astronomical silicates with optical constants from (cite: draine2003)" (6.4) [from (cite: draine2003)]
- External data: Optical constants: water ice and refractory organics  
  > "water ice with optical constants from (cite: li1998), refractory organic material with optical constants from (cite: li1997)" (6.4) [from (cite: li1998); (cite: li1997)]

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

- ALMA image reduction/imaging and beam taken from the earlier paper  
  > "We used the ALMA 870 $\ensuremath{\mu}m$ continuum image previously published by (cite: dent2014)." (ALMA) [from (cite: dent2014)]

### Not stated but needed to reproduce (our reading)

- ALMA project code, observing setup and calibration of the image (only the Dent et al. image is used)
- Whether the image is primary-beam corrected
- Exact radial extraction pixel grid and center for the ALMA profile
- Upper bound ranges of the grid for composition fractions (only 'steps of 0.2' mentioned in the discussion)

## Analysis recipe

1. **Extract radial profiles**: Rotate images to align the disk mid-plane, take a strip along the mid-plane and average the pixels, separately for the NE and SW sides  
  > "We extracted radial profiles by selecting a strip of each image along the mid-plane of the disk and computed the mean value of the pixels at each point along the length of the strip." (3 Data)
   - software: MATLAB
   - parameter: ALMA strip width 5 pixels (0.5")  
  > "5 pixels (0.5$''$) for the STIS, WFC3, MIPS, PACS, and ALMA images, respectively" (3 Data)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit spatial parameters of the parent body belt to ALMA**: Grid search over r_in, r_out, p and amplitude with chi-squared on the radial profile  
  > "We performed this fit with a grid search across the parameters of interest" (5 The Dust Spatial Distribution)
   - software: dustmap
   - parameter: r_in 35–70 au, r_out 130–170 au, p 0–2.0  
  > "We generated models with $r_\text{in}$ ranging from 35 to 70 au, $r_\text{out}$ from 130 to 170 au, and $p$ from 0 to 2.0." (5 The Dust Spatial Distribution)
   - assumption: Fixed a_min 5 micron, a_max 5000 micron, q=3.65, astronomical silicates; 4 deg half-opening wedge, edge-on  
  > "the grain properties were fixed at $a_\text{min}$ = 5 $\ensuremath{\mu}m$, $a_\text{max}$ = 5000 $\ensuremath{\mu}m$, $q$ = 3.65" (5 The Dust Spatial Distribution)
   - fitting: Grid search chi-squared  
  > "We performed this fit with a grid search across the parameters of interest, and the results are shown in red in Figure [8](#fig:SpatialConstraints)." (The Dust Spatial Distribution)
   - validation: Agrees with Dent et al. 2014 annuli modeling  
  > "Our values of $r_\text{in}$ and $r_\text{out}$ agree well with the analysis by (cite: dent2014)" (5 The Dust Spatial Distribution)
3. **Fit halo spatial parameters**: Fit WFC3 profile at r>8" for halo p; PACS for halo r_out  
  > "To measure $p$, we used the WFC3 data" (5 The Dust Spatial Distribution)
   - software: dustmap
   - fitting: _not stated_
   - validation: Checked against alpha=-p-1 relation of Strubbe & Chiang 2006  
  > "predicted $p$ values of 2.5 and 3.0 for the NE and SW sides, which agreed with what we found from model fitting" (5 The Dust Spatial Distribution)
4. **Fit grain sizes and composition to all five images simultaneously**: Grid search chi-squared per image, normalized by each image's minimum and averaged; fit r>3" on NE side; models with 100% astrosil, generic optical constants, and four-material Bruggeman mixture  
  > "We normalized the matrix from each image by the $\chi^2$ value of the best fitting model to that image in an attempt to weight the contribution from each of the five images equally." (6.1 Fitting Procedure)
   - software: dustmap, miex
   - assumption: Densities 2.7, 1.2, 1.8 g/cm3 for silicate, ice, organics  
  > "The grain densities were 2.7 g/cm$^3$ for the astronomical silicates (as is commonly assumed), and 1.2 and 1.8 g/cm$^3$ for the ice and organics" (6.4)
   - fitting: Grid search, chi-squared  
  > "We performed our fitting with a grid search, populating a chi-squared matrix for each of the five images, with one dimension of the matrix for each free parameter." (Fitting Procedure)
   - validation: Checked against SED, SW side, T-ReCS profiles and scattered light colors  
  > "In all three cases, our model agrees satisfactorily with the additional data set." (6.5 SED)

## Software

- **dustmap** v.3.1.1: Generating model images in thermal emission and scattered light  
  > "We used the code `dustmap` v.3.1.1 (cite: stark2011) to generate model disk images" (4 Model Images)
- **miex** : Absorption and radiation-pressure efficiencies  
  > "We computed the absorption efficiency, $Q_\text{abs}(\lambda,a)$, with the code `miex` (cite: wolf2004)" (6.5 SED)
- **MATLAB** : Interpolation and convolution of model images  
  > "we performed the convolution of the two images with MATLAB’s `conv2` function" (4 Model Images)
- **TinyTim** : HST model PSFs  
  > "We used the `TinyTim` software (cite: Krist2011) to generate model PSFs for the two *HST* images." (4 Model Images)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Parent body r_out (NE) | 150 | not stated | au | 2 | the best fit model had $r_\text{in}$ = 45 au, $r_\text{out}$ = 150 au, and $p$ = 0.5 |
| Silicate volume fraction | 0.6 | not stated | dimensionless | 4 | $f_\text{sil}$ / 0.6 |
| Organic volume fraction | 0.4 | not stated | dimensionless | 4 | $f_\text{org}$ / 0.4 |
| Parent body dust mass | 7.49e-2 | not stated | Earth masses | 4 | $M_\text{PB}$ / 7.49 $\times 10^{-2} M_\ensuremath{\oplus}$ |
| Blowout grain size | 2.7 | not stated | micron | 4 | the blowout size was 2.7 $\ensuremath{\mu}m$ |

## Qualitative findings

- Pure astronomical silicates cannot fit both thermal and scattered light; silicate+organic mix does, with little ice or vacuum  
  > "We achieve a good fit to all datasets with grains composed predominantly of silicates and organics, while ice and vacuum are, at most, present in small amounts." (abstract)

## Claim tuples

- H: Astronomical silicates alone can fit thermal and scattered light | E: Grid fit of five radial profiles | R: Model too faint at MIPS/PACS, too bright at STIS | F: Not adequate | **refuted**
- H: Silicate/ice/organic/vacuum mix fits all data | E: Bruggeman-mixed grid fit | R: Best fit f_sil=0.6, f_org=0.4 | F: Silicates and organics preferred | **supported**
- H: Sub-blowout grains are needed in the halo | E: Three-component fit with imposed depletion | R: No good fit with depletion | F: Sub-blowout grains necessary | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Fit only to NE side; SW side fit imperfectly at 70 micron  
  > "the halo component under-predicts the observed flux at 70 $\ensuremath{\mu}m$" (Appendix A.1)
- Caveat (inferred, ours): Grid search with coarse steps gives no formal uncertainties
- Caveat (inferred, ours): Composition degenerate among material choices; only one optical-constant set tested

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Reduced ALMA image (obtained from Dent et al.)
- Missing: Tabulated optical constants of the best model are only partly printed
- Data volume (inferred): small (reduced images from several facilities)
- Score (inferred): 3/5, Modeling recipe is detailed but ALMA data are an inherited image and dustmap needed.
- Rediscovery candidate: no, ALMA image is from a prior paper and the work relies on multiple non-ALMA datasets.

## Links

- Method: Stark 2011 (cite: stark2011) (dustmap code)
- Companion: Dent et al. 2014 (cite: dent2014) (source of ALMA image)

## Checks

```json
{
 "quotes": 44,
 "quotes_ok": 44,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00087.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 34,
  "rate": 0.459
 },
 "evidence_ok": true
}
```
