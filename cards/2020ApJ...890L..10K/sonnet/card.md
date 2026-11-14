# Systematic Variations of CO J = 2-1/1-0 Ratio and Their Implications in The Nearby Barred Spiral Galaxy M83

`2020ApJ...890L..10K` | The Astrophysical Journal Letters 2020 | first author: Koda, Jin | arXiv: 2001.11043 | DOI: 10.3847/2041-8213/ab70b7

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, milky_way_ism
- Question: How does the CO 2-1/1-0 line ratio vary across the disk of M83, and how does it relate to molecular gas surface density, FUV/IR emission and dust temperature?  
  > "While the intensities of these two lines correlate tightly, ${R_{21/10}}$ varies over the disk, with a disk average ratio of 0.69, and shows the galactic center and a two-arm spiral pattern." (abstract)
- Target **M83**: coordinates _not stated_; z/distance 4.5 Mpc  
  > "the barred spiral galaxy M83 at a distance of 4.5 Mpc (cite: Thim:2003aa)" (Introduction); distance from Thim et al. 2003 (cite: Thim:2003aa)  
  > "the barred spiral galaxy M83 at a distance of 4.5 Mpc (cite: Thim:2003aa)" (Introduction)

## Data provenance

- ALMA projects: 2013.1.01161.S, 2015.1.00121.S, 2016.1.00386.S, 2017.1.00079.S
- bands: _not stated_
- frequencies and spectral setup: CO(1-0): 250 MHz band, 61 kHz channels; CO(2-1): 2 GHz/977 kHz or 1 GHz/488 kHz  
  > "The ACA correlator was used to obtain spectra with band and channel widths of 250 MHz and 61 kHz." (CO(1-0)); "The band and channel widths were 2 GHz and 977 kHz or 1 GHz and 488 kHz." (CO(2-1))
- continuum bandwidth: _not stated_
- arrays: ALMA Total Power (TP) array  
  > "M83 was observed with the Total Power (TP) array of ALMA in CO(1-0) and CO(2-1)." (Observations and Data Reduction)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 56.6 arcsec (~1.2 kpc) after regridding/smoothing  
  > "we analyze the data at the full-width half maximum (FWHM) beam size of the CO(1-0) data, $56.6\ensuremath{''}$ ($\sim1.2$ kpc)" (Observations and Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: CO(1-0) ~6.2 mK in 0.159 km/s channels; CO(2-1) ~2.0 mK in 1.276 km/s channels (Tmb)  
  > "an root-mean-square noise of $\sim 6.2$ mK in $T_{\rm mb}$ in a velocity channel width of $0.159\, {\rm km \, s^{-1}}$" (CO(1-0)); "an RMS noise of $\sim 2.0$ mK in $T_{\rm mb}$ with a pixel scale of $2.81\ensuremath{''}$ and velocity channel width of $1.276\, {\rm km \, s^{-1}}$" (CO(2-1))
- time on source: CO(1-0): 110.1 h observing, 60.4 h on-source (120 EBs); CO(2-1): 132.8 h observing, 66.4 h on-source (160 EBs)  
  > "the total observing and on-source times were 110.1 h and 60.4 h, respectively" (CO(1-0)); "The total observing and on-source times were 132.8 h and 66.4h." (CO(2-1))
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=1-0 (not stated)
- Line: CO J=2-1 (not stated)
- Other facility **GALEX**: FUV 1516 Å intensity map  
  > "specific intensity (brightness) maps in GALEX FUV (1516$\AA$) (cite: Gil-de-Paz:2007lj)" (Ancillary Data)
- Other facility **Spitzer**: 24 micron map  
  > "in Spitzer 24$\mu$m (cite: Bendo:2012aa)" (Ancillary Data)
- Other facility **Herschel**: 70 and 350 micron maps  
  > "and in Herschel 70 and 350$\mu$m (cite: Bendo:2012ab)" (Ancillary Data)
- External data: GALEX FUV map of M83  
  > "specific intensity (brightness) maps in GALEX FUV (1516$\AA$) (cite: Gil-de-Paz:2007lj)" (Ancillary Data) [from Gil de Paz et al. 2007 (cite: Gil-de-Paz:2007lj)]
- External data: Spitzer 24 micron map  
  > "in Spitzer 24$\mu$m (cite: Bendo:2012aa)" (Ancillary Data) [from Bendo et al. 2012a (cite: Bendo:2012aa)]
- External data: Herschel 70 and 350 micron maps  
  > "and in Herschel 70 and 350$\mu$m (cite: Bendo:2012ab)" (Ancillary Data) [from Bendo et al. 2012b (cite: Bendo:2012ab)]

## Processing

### Calibration

- pipeline or manual: Standard pipeline-style calibration with more careful relative flux scaling among execution blocks  
  > "The calibration was performed in the standard way as for the ALMA data reduction pipeline, with a more careful calibration of the relative flux scales among execution blocks" (Observations and Data Reduction)
- casa version: CASA 5.4.1-31  
  > "CASA 5.4.1-31 (cite: McMullin:2007aa)" (Software)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: about 5% absolute (per observatory)  
  > "systematic errors in absolute flux calibrations (about 5% according to the observatory)" (The CO 2-1/1-0 Ratio)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: CO(1-0) 5.62 arcsec; CO(2-1) 2.81 arcsec  
  > "re-sampled on a grid of pixel size $5.62\ensuremath{''}$ using the prolate spheroidal function with a size of 6 pixels" (CO(1-0))
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Spectral baselines subtracted with straight lines (CO(1-0))  
  > "Spectral baselines were subtracted with straight lines." (CO(1-0))
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: RA and Dec OTF scans combined with Emerson & Graeve method  
  > "The two were combined with the (cite: Emerson:1988hz) method." (CO(1-0))
- smoothing: CO(2-1) deconvolved with its beam and convolved with CO(1-0) beam; ancillary maps smoothed to 56.6 arcsec  
  > "the CO(2-1) map was smoothed by a sequence of a deconvolution with the CO(2-1) beam and convolution with the CO(1-0) beam." (The CO 2-1/1-0 Ratio)
- final beam: 56.6 arcsec  
  > "The effective FWHM beam size after this regridding/smoothing is $56.6\ensuremath{''}$." (CO(1-0))
- final rms: 1 sigma ~61 and 14 mK km/s in I_CO1-0 and I_CO2-1  
  > "The $1\sigma$ noise is about 61 and 14 $\rm \rm mK \cdot km/s$ in $I_{\rm CO1-0}$ and $I_{\rm CO2-1}$, respectively." (The CO 2-1/1-0 Ratio)

### Inherited from earlier work

- Gridding with prolate spheroidal function  
  > "using the prolate spheroidal function with a size of 6 pixels (cite: Schwab:1980aa; Schwab:1984)" (CO(1-0)) [from Schwab 1980; Schwab 1984]
- Combination of scans using Emerson & Graeve method  
  > "The two were combined with the (cite: Emerson:1988hz) method." (CO(1-0)) [from Emerson & Graeve 1988]
- Linear regression via OLS bisector  
  > "ordinary least squares bisector fitting (cite: Isobe:1990aa)" (Table 1) [from Isobe et al. 1990]

### Not stated but needed to reproduce (our reading)

- Which EBs/project codes belong to CO(1-0) vs CO(2-1)
- List of the 5 rejected EBs and the exact rejection criteria
- Flux/bandpass/pointing calibrators used
- Pipeline version and exact calibration scripts
- Exact ancillary map product versions and background/zero-point handling
- Inclination and position angle used for deprojection
- Pixel selection details for Table 1 fits and handling of S/N cuts
- Conversion factor used for the 8e6 Msun mass estimate
- Line-free channels for baseline fitting

## Analysis recipe

1. **Relative flux scaling of EBs**: Cubes per EB, flux ratios of all pairs, solve for relative scales by inverting design matrix, then co-add  
  > "calculated the flux ratios and errors of all of their pairs, and solved for relative flux scales by inverting the design matrix." (CO(1-0))
   - software: CASA
   - parameter: scatter of coefficients 1.3% (CO 1-0), 3.1% (CO 2-1)  
  > "The coefficients have a small scatter of 3.1%, and we made a correction for this before co-adding the data." (CO(2-1))
   - fitting: _not stated_
   - validation: _not stated_
2. **Convert to Tmb and make cubes**: Main beam efficiency 0.856 (CO 1-0) and 0.836 (CO 2-1)  
  > "We used a main beam efficiency of 0.836." (CO(2-1))
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Integrated intensity maps and ratio**: Integrate cubes over velocity without clipping, smooth CO(2-1) to CO(1-0) beam, regrid, divide; trim edges where smoothed uniform-field value <0.99  
  > "The CO(1-0) and CO(2-1) data cubes were integrated along velocity without any clip/mask, to produce integrated intensity maps" (The CO 2-1/1-0 Ratio)
   - software: CASA
   - parameter: final FOV about 7.0' x 7.0'  
  > "This reduced the field-of-view to about $7.0\ensuremath{'} \times 7.0 \ensuremath{'}$." (The CO 2-1/1-0 Ratio)
   - fitting: _not stated_
   - validation: Edge effect quantified with uniform-illumination image  
  > "we applied the above smoothing procedure to an image with a uniform illumination over the field of view" (The CO 2-1/1-0 Ratio)
4. **Correlate R21/10 with CO, FUV, IR and dust color**: Use every 5th pixel; OLS bisector linear regression with correlation coefficients; radial profiles with inclination correction  
  > "We use only every 5th pixel when they are correlated with other data (Sec. [3](#sec:results))." (The CO 2-1/1-0 Ratio)
   - assumption: I70/I350 as a proxy for dust temperature  
  > "(dust color, a proxy of dust temperature $T_{\rm d}$; Figure [4](#fig:f70f350))" (Results)
   - fitting: OLS bisector (Isobe et al. 1990)  
  > "ordinary least squares bisector fitting (cite: Isobe:1990aa)" (Table 1)
   - validation: _not stated_

## Software

- **CASA** 5.4.1-31: Data reduction of ALMA TP data  
  > "The data were reduced using the Common Astronomy Software Applications package (cite: McMullin:2007aa)." (Observations and Data Reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Disk average/median R21/10 | 0.69 | not stated | dimensionless | 3 | Both the average and median of ${R_{21/10}}$ in this region are 0.69. |
| Correlation coefficient R21/10 vs log I70/I350 | 0.83 | not stated | dimensionless | 4 | / $\log I_{\rm 70\mu m}/I_{\rm 350\mu m}$ / ${R_{21/10}}$ / 0.292 / 0.569 / 0.83 / |
| Correlation coefficient R21/10 vs log I_FUV | 0.82 | not stated | dimensionless | 4 | / $\log I_{\rm FUV}$ / ${R_{21/10}}$ / 0.161 / 0.897 / 0.82 / |
| CO(1-0) radial scale length | ~94 (~2.0 kpc) | not stated | arcsec | 4 | decays exponentially with a scale length of $\sim 94\ensuremath{''}$ ($\sim$2.0 kpc) |
| Random error in R21/10 at lowest contour | about 4% | not stated | percent | 3 | The random error in ${R_{21/10}}$ is about 4% at the lowest $I_{\rm CO1-0}$ contour or less at higher $I_{\rm CO1-0}$. |

## Qualitative findings

- R21/10 is higher at the downstream (convex) sides of spiral arms and in the galactic center (>0.8), and ~0.7 along the bar  
  > "${R_{21/10}}$ is high$>0.8$ in the galactic center, as is also observed in the MW center" (Results)

## Claim tuples

- H: Does R21/10 vary systematically across M83? | E: Ratio map of ALMA TP CO(2-1) and CO(1-0) at 56.6 arcsec | R: Mean 0.69; range ~0.5-0.8, higher in center and spiral arms' downstream sides | F: R21/10 is not constant | **supported**
- H: Is R21/10 linked to dust heating by the ISRF? | E: Pixel correlations of R21/10 with FUV, IR and I70/I350 | R: FUV (r=0.82) and I70/I350 (r=0.83) correlate best | F: Suggests a link between dust heating and GMC conditions | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Single-dish analysis is a solid first confirmation since interferometer data are susceptible to imaging noise  
  > "the analysis of single-dish data is an important first step for a solid confirmation of the variations of ${R_{21/10}}$" (Observations and Data Reduction)
- Alternative: Majority of CO emission from optically thin gas outside GMCs not considered  
  > "we did not consider the possibility that the *majority* of CO emission arises from the optically-thin CO gas outside GMCs" (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Low resolution (~1.2 kpc) smears structures; one galaxy only  
  > "Obviously, the analysis of one galaxy is limited and a larger sample is called for." (Discussion)
- Caveat (inferred, ours): Correlations at 1.2 kpc cannot isolate GMC conditions
- Caveat (inferred, ours): FUV is affected by extinction and no causal link is established
- Caveat (inferred, ours): Regression uncertainties not given
- Caveat (inferred, ours): No mask means noisy pixels are included in the ratio

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Execution-block to project mapping
- Missing: Calibration scripts and rejected EB list
- Missing: Inclination/PA parameters
- Missing: Pixel selection details
- Data volume (inferred): Large raw TP data (~285 EBs), likely tens to hundreds of GB
- Score (inferred): 4/5, Public ALMA TP data and clear recipe, but custom EB scaling and several parameters are unstated.
- Rediscovery candidate: no, The custom TP reduction and flux-scaling are not fully specified, and the raw data volume is large.

## Links

- Method: Koda et al. 2012 (cite: Koda:2012lr) (Earlier R21/10 analysis in M51 and non-LTE interpretation)

## Checks

```json
{
 "quotes": 57,
 "quotes_ok": 57,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 40,
  "rate": 0.563
 },
 "evidence_ok": true
}
```
