# A Submillimeter Perspective on the GOODS Fields (SUPER GOODS). III. A Large Sample of ALMA Sources in the GOODS-S

`2018ApJ...865..106C` | The Astrophysical Journal 2018 | first author: Cowie, L. L. | arXiv: 1805.09424 | DOI: 10.3847/1538-4357/aadc63

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: Characterize the ALMA band 7 counterparts of a complete SCUBA-2 850 um sample in GOODS-S: multiplicity, redshifts (FIR photometric), high-z candidates, morphologies, and X-ray/AGN properties  
  > "We analyze the $>4\sigma$ sources in the most sensitive 100 arcmin$^2$ area (rms $<0.56$ mJy) of a SCUBA-2 850 $\mu$m survey of the GOODS-S" (abstract)
- Target **GOODS-S / CDF-S SCUBA-2 sources**: coordinates R.A. 03:32:26.49, Decl. -27:48:29.0 (J2000.0) (SCUBA-2 mean aimpoint)  
  > "The mean aimpoint of our SCUBA-2 observations is R.A. 03:32:26.49, Decl. $-27$:48:29.0 (J2000.0)." (2.1 SCUBA-2 Observations); z/distance median z=2.74 (mixed spec/FIR/photo redshifts)  
  > "The mean aimpoint of our SCUBA-2 observations is R.A. 03:32:26.49, Decl. $-27$:48:29.0 (J2000.0)." (2.1 SCUBA-2 Observations); distance from literature specz, S16 photz, own FIR photz  
  > "The mean aimpoint of our SCUBA-2 observations is R.A. 03:32:26.49, Decl. $-27$:48:29.0 (J2000.0)." (2.1 SCUBA-2 Observations)

## Data provenance

- ALMA projects: 2015.1.00242.S, 2016.1.01079.S, 2012.1.00307.S, 2012.1.00869.S, 2013.1.00205.S, 2012.1.00983.S
- bands: Band 7  
  > "with the C40-4 array configuration in band 7" (ALMA Observations)
- frequencies and spectral setup: four 1.875 GHz spectral windows around 343.5 GHz  
  > "four 1.875 GHz spectral windows (using time division mode) placed around a central frequency of 343.5 GHz" (2.3 ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C40-4 (cycle 3), C40-3 (cycle 4)  
  > "in the C40-3 array configuration in band 7 (hereafter, the cycle4 program)" (2.3 ALMA Observations)
- baselines: _not stated_
- angular resolution: natural beam 0.38x0.3 arcsec (cycle3), 0.15x0.1 (cycle4); tapered 0.53x0.48 arcsec  
  > "to achieve a representative synthesized beam of $0.53\ensuremath{''}\times0.48\ensuremath{''}$" (2.3 ALMA Observations)
- max recoverable scale: _not stated_
- sensitivity: median rms 0.15 mJy (cycle3), 0.29 mJy (cycle4-only)  
  > "We measured a median rms noise for the sources in the cycle3 program of 0.15 mJy" (2.4 ALMA Source Catalog Construction)
- time on source: 2.4-3.2 min per source (cycle3); 2.7 min (cycle4)  
  > "with combined integration times between 2.4 min and 3.2 min for each source" (2.3 ALMA Observations)
- observing dates: Jul 13-Nov 25 2016 (cycle3); Jul-Aug 2017 (cycle4)  
  > "between July 13 and November 25, 2016" (2.3 ALMA Observations)
- pi or archival as stated: _not stated_
- Other facility **JCMT SCUBA-2**: 850 um and 450 um survey and source catalog  
  > "We made observations from late 2011 through early 2017 using SCUBA-2" (2.1 SCUBA-2 Observations)
- Other facility **Chandra 7 Ms**: X-ray fluxes for ALMA sources  
  > "The total ALMA sample lies in the deepest region of the 7 Ms *Chandra* X-ray exposure (Luo et al. 2017)." (8 X-ray Luminosities)
- Other facility **Herschel and Spitzer**: FIR/MIR photometry for FIR photometric redshifts  
  > "deep 100 $\mu$m and 160 $\mu$m *Herschel* PACS images of the GOODS-S (Elbaz et al. 2011)" (4.5 FIR Counterparts)
- Other facility **HST**: F160W morphology and counterparts  
  > "version 1.5 data release of the Hubble Legacy Fields by Illingworth et al. (2016)" (4.1 Optical and F160W Counterparts)
- External data: Photometric redshifts  
  > "We take our photzs from S16, who used the EAZY code (Brammer et al. 2008)" (4.3 Redshifts) [from Straatman et al. 2016 (S16)]
- External data: 1.13 mm ALMA fluxes  
  > "In Table 4, we give the F18 fluxes based on their GALFIT values and without applying any deboosting." (2.6 Comparison with 1.13 mm ALMA sample) [from Franco et al. (2018)]
- External data: X-ray catalog  
  > "Just over half (41) of the ALMA sources are detected in the Luo et al. catalog using a $1.5\ensuremath{''}$ matching radius" (8 X-ray Luminosities) [from Luo et al. 2017]
- External data: CANDELS multiwavelength catalog  
  > "we adopted the optical and NIR magnitudes from G13." (4.1) [from Guo et al. 2013 (G13)]
- Simulation/model as data: Arp 220 SED template of Silva et al. (1998) for FIR photometric redshifts  
  > "We overlay the Arp 220 SED of Silva et al. (1998) in black." (4.6 FIR Photometric Redshifts)

## Processing

### Calibration

- pipeline or manual: CASA pipeline plus manual flagging  
  > "We performed manual flagging in addition to the pipeline processing to remove outlier baselines and/or antennas." (2.3 ALMA Observations)
- casa version: 4.7.0 (cycle3); 4.7.2 (cycle4 and archival)  
  > "We calibrated the data and made images using casa version 4.7.0 and the included pipeline." (2.3 ALMA Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ceres and J0334-4008 (cycle3); J0334-4008 (cycle4)  
  > "Ceres and J0334-4008 as the flux calibrators" (2.3 ALMA Observations)
- flux scale uncertainty: ~5%  
  > "We estimate the final error in the absolute flux calibration to be $\sim5$%." (2.3 ALMA Observations)
- self calibration: _not stated_

### Imaging

- task: CASA clean; concatenate for combining cycles  
  > "We made images of the targets using the task clean." (2.3 ALMA Observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "We made dirty images using natural weighting and a mild *uv*-taper" (2.3 ALMA Observations)
- uv taper: mild taper to ~0.5 arcsec beam  
  > "we adopted a beam size of $\approx0.5\ensuremath{''}$" (2.3 ALMA Observations)
- cell size: _not stated_
- image size: _not stated_
- masking: 2x2 arcsec clean boxes around S/N>=5 sources; 1000 iterations  
  > "placing $2''\times2''$ clean boxes around all secure sources detected with S/N$\geq5$ in the dirty images" (2.3 ALMA Observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: cycle3+cycle4 visibilities concatenated  
  > "We combined the visibilities for the fields that were observed in both cycles using the casa task concatenate" (2.3 ALMA Observations)
- smoothing: _not stated_
- final beam: 0.53x0.48 arcsec, PA -87.16 deg  
  > "a position angle of -87.16$^\circ$" (2.3 ALMA Observations)
- final rms: _not stated_

### Inherited from earlier work

- SCUBA-2 reduction procedures  
  > "Our reduction procedures follow Chen et al. (2013) and are described in detail in Paper I." (2.1 SCUBA-2 Observations) [from Chen et al. 2013; Cowie et al. 2017 (Paper I)]
- SCUBA-2 source catalog construction  
  > "As in Paper I, we generated the source catalogs by identifying the peak S/N pixel" (2.2) [from Paper I]
- Conversion of luminosity to SFR  
  > "we also need to take into account Paper I’s conversion from $L_{8-1000~\mu{\rm m}}$ to SFR" (6) [from Paper I]
- uv-plane Gaussian fits and sizes  
  > "J. González-López et al. (2018, in preparation) give more details on these fits" (2.4) [from González-López et al. 2018 (in prep.)]

### Not stated but needed to reproduce (our reading)

- Which archival data are used for each of the 12 archival fields and exact field list
- Number/exact line-free handling and spectral windows used for continuum
- Primary beam correction procedure for final fluxes
- Clean threshold and cell/image size
- uv-taper parameters
- Aperture flux error estimation details
- Photometry used in FIR fits (Herschel catalog values) and fit grid/redshift step
- How confidence ranges for fractions are computed (beyond Poisson)

## Analysis recipe

1. **Calibrate and image ALMA data**: CASA pipeline + manual flagging; concatenate cycles; natural-weighted tapered clean to ~0.5 arcsec  
  > "We made dirty images using natural weighting and a mild *uv*-taper" (2.3 ALMA Observations)
   - software: CASA
   - parameter: clean boxes 2x2 arcsec, 1000 iterations  
  > "We stopped the final cleaning process after 1000 iterations" (2.3 ALMA Observations)
   - fitting: _not stated_
   - validation: cycle3 final fluxes compared with individual executions  
  > "The flux densities that we measured in the final images of the cycle3 program are in good agreement with the ones we obtained for the individual executions" (2.3 ALMA Observations)
2. **Build ALMA source catalog and total fluxes**: Peak S/N>4.5 within 8.75 arcsec radius; aperture flux (0.6 arcsec) or peak x 1.22 for total flux; uv Gaussian fit check  
  > "For the remaining sources, we used the peak flux times the median correction of 1.22." (2.4)
   - parameter: S/N>4.5; noise from 100 independent beam positions  
  > "We determined the peak flux noise using the dispersion in 100 independent beam positions surrounding the source." (2.4)
   - fitting: _not stated_
   - validation: negative-image test gave no sources above 4.5 sigma; uv fits agree with best fluxes  
  > "This gives two sources at S/N$=4-4.5$ and none above 4.5, consistent with the Gaussian expectation." (2.4)
3. **Compare ALMA with SCUBA-2 and derive multiplicity**: Convolve ALMA sources with SCUBA-2 matched-filter PSF, subtract from SCUBA-2 map, search residuals; count multiple counterparts  
  > "Each ALMA source is convolved with the SCUBA-2 matched-filter PSF and added to form a final image." (3 ALMA versus SCUBA-2)
   - fitting: _not stated_
   - validation: _not stated_
4. **Estimate FIR photometric redshifts**: chi2 fit of Arp 220 template to Herschel, SCUBA-2 450, ALMA 850 and F18 1.13 mm data with 20% systematic error  
  > "we used the Arp 220 template to estimate FIR photometric redshifts (hereafter, FIRzs) using a $\chi^2$ fit" (4.6)
   - parameter: ALMA flux >1.65 mJy; reject chi2 probability <5%  
  > "where the $\chi^2$ fit is poor (probability less than 5%)" (4.6)
   - assumption: Arp 220-like SED; graybody beta=1.5 for temperatures  
  > "assuming a graybody with an emissivity $\beta=1.5$" (4.6)
   - fitting: chi2 minimization with 95% confidence range  
  > "We give the estimated FIRzs in Table 5, together with the 95% confidence range." (FIR Photometric Redshifts)
   - validation: compared FIRz to specz/photz  
  > "the overall correlation is reasonable for most of the sources" (4.6)
5. **Morphology and merger fraction**: Visual classification of F160W images  
  > "In the present paper, we only visually classify the galaxies." (7)
   - fitting: _not stated_
   - validation: Poisson errors only  
  > "The errors are Poissonian based on the number of sources and do not include uncertainties in the classifications." (7)
6. **X-ray luminosities and obscuration**: Match to Luo+17 catalog (1.5 arcsec); compute L2-8 and L8-28 keV with Gamma=1.8; compare to Mineo/Barger relation; N_H from photon index vs redshift  
  > "we compute the rest-frame $2-8$ keV luminosities, $L_{2-8~{\rm keV}}$, from the observed-frame $0.5-2$ keV fluxes with no absorption correction and $\Gamma=1.8$" (8)
   - assumption: Cosmology H0=70.5, OmegaM=0.27, OmegaL=0.73  
  > "We assume the Wilkinson Microwave Anisotropy Probe cosmology of $H_0=70.5$ km s$^{-1}$ Mpc$^{-1}$" (1)
   - fitting: _not stated_
   - validation: matching radius 1.0 vs 1.5 arcsec changes one match  
  > "then we would only reduce the number of matches by one source." (8)

## Software

- **CASA** 4.7.0 / 4.7.2: calibration, concatenation and clean imaging  
  > "We calibrated the data and made images using casa version 4.7.2 and the corresponding included pipeline." (2.3)
- **EAZY** : photometric redshifts (from S16, not run here)  
  > "who used the EAZY code (Brammer et al. 2008)" (4.3)
- **SExtractor** : star-galaxy classifier for compactness  
  > "appears compact based on the SExtractor star-galaxy classifier" (7)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA >4.5 sigma sources | 75 | not stated | sources | 2 | In total, we have 75 $>4.5\sigma$ ALMA sources |
| fraction of SCUBA-2 sources >2.25 mJy with multiple ALMA counterparts | 13% | 68% range 7-19% | percent | 3 | The overall percentage of SCUBA-2 sources above 2.25 mJy with multiple ALMA counterparts is 13% (68% confidence range 7–19%). |
| median redshift of ALMA sources >1.65 mJy | 2.74 | not stated | dimensionless | 4 | The median redshift is $z=2.74$, while above 3 mJy, the median redshift is $z=3.26$. |
| z_median vs S850 slope | 0.09 | ±0.03 | per mJy | 4 | z_{median}=2.40 + 0.09 (\pm0.03) \times S_{850}\ {\rm (mJy)} |
| merger fraction | 44% | 68% range 35-53% | percent | 5 | Overall, we obtain a merger fraction of 44% (68% confidence range 35–53%). |
| X-ray detected fraction above 4 mJy | 86% | 68% range 67-95% | percent | 6 | Above 4 mJy, 12 of the 14 ALMA sources have X-ray counterparts (86%, with a 68% confidence range 67–95%) |
| median log N_H | 23.5 | not stated | cm^-2 | 6 | the median $\log N_H$ of the sample is 23.5 cm$^{-2}$ |

## Qualitative findings

- 4.5 um and 24 um to 850 um flux ratios decline with redshift and flag z>~4 candidates  
  > "We see the expected decline with redshift of the 4.5 $\mu$m and 24 $\mu$m to 850 $\mu$m flux ratios" (abstract)

## Claim tuples

- H: Do SCUBA-2 sources break into many ALMA multiples? | E: ALMA band 7 follow-up of complete SCUBA-2 sample | R: 13% multiples, 5 of 53 undetected | F: Low multiplicity compared with ALESS | **supported**
- H: Color selections find high-z SMGs completely | E: KIEROs/HIEROs/three-color tests | R: detection rates 41-55% | F: Color selections are incomplete | **supported**
- H: Many ALMA SMGs are mergers | E: Visual F160W classification of 52 sources | R: 24 mergers, 44% | F: High apparent merger fraction | **partially**
- H: X-ray emission traces star formation or AGN | E: 7 Ms Chandra luminosities vs 850 um flux | R: soft-band sources consistent with SF relation; hard-band mostly obscured moderate AGN | F: Two high-z candidates may be Compton thick | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: ~0.5 arcsec taper balances rms and sensitivity to extended sources  
  > "which offers the best trade-off between retaining a relatively low rms and increasing the sensitivity to extended sources in our data" (2.3)
- How they decided it was enough: _not stated_
- Limitation (authors): Redshifts mostly estimated; may be problematic with AGN or high z  
  > "However, these rely on mostly estimated redshifts, which may be problematic if there is AGN activity or if sources lie at high redshift." (9 Summary)
- Caveat (inferred, ours): FIRz depends on a single Arp 220 template with no temperature evolution
- Caveat (inferred, ours): Visual merger classification is subjective
- Caveat (inferred, ours): Fraction uncertainties are Poisson only
- Caveat (inferred, ours): Completeness of ALMA sample inferred from SCUBA-2 completeness

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters (cell, image size, threshold)
- Missing: Exact aperture-flux procedure code
- Missing: Herschel photometry used per source
- Missing: Visual classification labels
- Data volume (inferred): ~100s GB to ~1 TB raw for ~95 fields across 6 projects
- Score (inferred): 3/5, Data from named projects and a clear workflow, but several imaging and fitting details are missing and parts rely on in-preparation companions.
- Rediscovery candidate: no, Recipe is incomplete and results depend on many external catalogs and subjective classification.

## Links

- Method: Chen et al. 2013 (SCUBA-2 reduction)
- Method: Cowie et al. 2017 (Paper I) (SCUBA-2 catalog and FIRz method)
- Companion: Barger et al. 2017 (Paper II) (GOODS-N SUPER GOODS)
- Companion: González-López et al. 2018 (in prep.) (ALMA sizes and uv fits)
- Companion: Franco et al. 2018 (1.13 mm ALMA sample in GOODS-S)
- Related: BASIC
- Related: ALESS
- Related: SUPER GOODS
- Related: GOODS-S/CANDELS
- Related: 7 Ms CDF-S

## Checks

```json
{
 "quotes": 75,
 "quotes_ok": 75,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 6,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00294.S"
 ],
 "codes_printed_but_missing": [
  "2011.1.00294.S"
 ],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 84,
  "stated": 57,
  "rate": 0.679
 },
 "evidence_ok": true
}
```
