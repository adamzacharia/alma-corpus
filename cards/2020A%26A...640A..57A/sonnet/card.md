# Modeling the quiet Sun cell and network emission with ALMA

`2020A&A...640A..57A` | Astronomy and Astrophysics 2020 | first author: Alissandrakis, C. E. | arXiv: 2006.09886 | DOI: 10.1051/0004-6361/202038461

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: sun
- Question: What are the electron temperature structures of the average quiet Sun, cell interior and network from ALMA Band 3 and 6 images, and how well is the ALMA full-disk absolute calibration known?  
  > "We also examine the absolute calibration of ALMA full-disk images." (abstract)
- Target **Quiet Sun (full disk, cell interior and network regions)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2017.1.00870.S, 2018.1.01763.S, 2016.1.00572.S, 2017.1.00653.S, 2011.0.00020.SV, 2019.1.01532.S
- bands: Band 3 (3 mm) and Band 6 (1.26 mm)  
  > "high resolution ALMA images at 3 mm (Band 3) and 1.26 mm (Band 6)" (abstract)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: FD ~60'' Band 3, ~30'' Band 6; HR 3-4'' (2017), ~2'' Band 3 and ~1'' Band 6 (2018)  
  > "providing full-disk (FD) images with a resolution of $\sim60$$''$ in Band 3 and $\sim30$$''$ in Band 6" (2.1); "these images had a resolution of $\sim2$$''$ in Band 3 and $\sim1$$''$ in Band 6" (3.2 Processing and results)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: Dec 2015, Mar 16 2017, Apr 12 2018, May 1 2018, Dec 20 2018  
  > "Dec 20, 2018" (Table 1)
- pi or archival as stated: _not stated_
- Other facility **Bastian et al. 1993 353 GHz observations**: 353 GHz center-to-limb data used with ALMA  
  > "together with the observations of (cite: 1993ApJ...415..364B) at 353 GHz" (1 Introduction)
- External data: Recommended disk-center Tb normalization (7300 K Band 3, 5900 K Band 6)  
  > "whereas for Band 6 it is 280 K above the recommended value (6180 K, compared to 5900  K)" (2.1) [from (cite: 2017SoPh..292...88W)]
- External data: Cell and network Tb values near disk center at 100 GHz  
  > "values derived from (cite: 2019ApJ...877L..26L) at 100 GHz near the center of the disk, measured from the histograms of their Figure 2a" (3.2 Processing and results) [from (cite: 2019ApJ...877L..26L)]
- Simulation/model as data: FAL93 models A, C, F and VAL81 segregation compared with measurements; rMHD model of Wedemeyer et al. 2020  
  > "the cell and network values (a single set at 100 GHz, $\mu=1$) form the radiative MHD model of (cite: 2020A&A...635A..71W) are plotted" (3.2 Processing and results)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: Systematic uncertainty of order 5% in the White et al. FD calibration, considered too low  
  > "a systematic uncertainty of order 5% comes in through the product of the “forward scattering and spillover” coefficient and the “forward efficiency”." (2.2)
- self calibration: Feathered HR images improved by self-calibration  
  > "In both cases we used “feathered” images, improved by self-calibration" (3.2 Processing and results)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Circular FOV: 40'' radius (Band 3), 17.5'' radius (Band 6)  
  > "whereas the radius used for Band 6 was 17.5$''$" (3.2 Processing and results)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: HR interferometric data feathered with FD images  
  > "“feathered” images (combining HR interferometric data with FD)" (2.1)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Diffuse-light correction and no-sky-background assumption for FD images  
  > "the observed $T_b$ was corrected for diffuse light as explained in Paper I (Section 3 and Figure 4)" (2.1) [from Paper I (cite: 2017A&A...605A..78A)]
- 2017 observation targets and cell/network equal-pixel split  
  > "(Table 1 of Paper II)" (3.2 Processing and results) [from Paper II (cite: 2018A&A...619L...6N)]

### Not stated but needed to reproduce (our reading)

- Imaging, feathering and self-calibration parameters for HR data
- CASA version and calibration details
- Exact commissioning mosaic dataset identifiers
- Details of the inversion procedure from Tb(mu) to Te(tau) beyond log fit
- Details of how network/cell pixel selection thresholds were applied across regions
- Data of April 12 2018 observations not given a project code

## Analysis recipe

1. **Normalize FD images**: Least-square fit of all FD sets to a common linear function of log mu at 100 GHz; Band 3 factor set to unity  
  > "we set the normalization factor for that at unity, leaving the factors for the other data sets to be determined by the fit." (2.1)
   - parameter: Reduction to f_ref = 100 GHz via Tb((f/fref)^2 mu, fref)=Tb(mu,f)  
  > "we had reduced all data to a common reference frequency, $f_{ref}$" (2.1)
   - assumption: Commissioning calibration correct; opacity proportional to f^-2  
  > "assuming that the commissioning calibration was correct" (4 Summary)
   - fitting: Linear fit (quadratic made no difference)  
  > "Here a linear fit function was used, as a quadratic fit made no difference." (2.1)
   - validation: rms deviation about 20 K; feathered/FD comparison factor 1.066  
  > "with a root mean square (rms) deviation of about 20 K for the ALMA data" (2.1)
2. **Invert average QS Te(tau)**: Tb(mu)=a1+a2(ln mu - gamma) giving Te=a1+a2 ln tau  
  > "T_b(\mu)=a_1+a_2(\ln\mu-\gamma)" (2.1)
   - assumption: Plane-parallel atmosphere, valid to mu~0.15  
  > "is valid up to $\mu\simeq0.15$ ($\sim10$$''$ from the limb)" (2.2)
   - fitting: _not stated_
   - validation: Scatter of single-day inversions gives error estimates  
  > "which gives $\delta a_1=14$ K and $\delta a_2=15$ K." (2.2)
3. **Measure cell and network Tb**: Pixel segregation: set 1 equal split; set 2 lowest 8% cell, top 4% network; HR values corrected to match global inversion  
  > "attributing the lowest 8% of the pixels to cell interior and the top 4% to the network" (3.2 Processing and results)
   - fitting: Linear regression of Tb vs log mu100, inverted to Te(tau100)  
  > "together with the corresponding linear regression lines and FAL93 models" (3.2 Processing and results)
   - validation: _not stated_

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| a1 (average QS) | 6999 | 14 K | K | 2 | / $a_1 (K)$ /   6999    /  6887   / |
| a2 (average QS) | -563 | 15 K | K | 2 | / $a_2 (K)$ /  $-$563   / $-$608  / |
| Band 6 disk-centre Tb | 6343 | not stated | K | 2 | the Band 6 average value (6343 K) is 443 K or 7.5% above the recommended (5900 K) |
| Network-cell Te difference at tau100=1 (set 1 / set 2) | 657 / 1554 | not stated | K | 3 | / set 1          /    657     / 1.10  / |
| Network/cell Te ratio (set 1 / set 2) | 1.10 / 1.24 | not stated | dimensionless | 3 | / set 2          /    1554    / 1.24  / |
| Limb height Band 6 / Band 3 | 2.4 / 4.2 | 1.7 / 2.5 | Mm | 0 | 2.4 Mm in Band 6 and 4.2 Mm in Band 3 |

## Qualitative findings

- Network/cell Te curves diverge with decreasing tau, suggesting steeper temperature rise in network  
  > "indicating an increase of contrast with height and possibly a steeper temperature rise in the network than in the cell interior." (abstract)

## Claim tuples

- H: ALMA FD Band 6 normalization recommended by White et al. is correct | E: Fit all FD sets to common Tb-log mu relation | R: Band 6 normalization factors ~1.084 | F: Recommended Band 6 disk-centre Tb is ~440 K too low | **supported**
- H: Cell/network contrast follows FAL93 models | E: Measure cell and network Tb in HR images, invert to Te | R: Contrast far lower than models | F: Cell hotter than model A, network cooler than model F | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Poor statistics of HR data and reliance on commissioning calibration  
  > "In spite of the poor statistics" (4 Summary)
- Caveat (inferred, ours): Small, inhomogeneous HR sample
- Caveat (inferred, ours): Normalization anchored to assumed-correct commissioning values
- Caveat (inferred, ours): Segregation scheme dependence

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Reduced FD and feathered images
- Missing: Processing parameters
- Data volume (inferred): ~100s GB
- Score (inferred): 3/5, Data identified but processing and inversion details are sparse.
- Rediscovery candidate: no, Recipe incomplete; relies on inherited Paper I/II procedures.

## Links

- Method: (cite: 2017SoPh..292...88W) (FD solar imaging and calibration)
- Companion: (cite: 2017A&A...605A..78A) (Paper I)
- Companion: (cite: 2018A&A...619L...6N) (Paper II)

## Checks

```json
{
 "quotes": 42,
 "quotes_ok": 42,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 6,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.0.00020.SV",
  "2019.1.01532.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 63,
  "stated": 26,
  "rate": 0.413
 },
 "evidence_ok": true
}
```
