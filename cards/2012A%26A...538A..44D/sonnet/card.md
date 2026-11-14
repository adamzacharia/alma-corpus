# Pre-ALMA observations of GRBs in the mm/submm range

`2012A&A...538A..44D` | Astronomy and Astrophysics 2012 | first author: de Ugarte Postigo, A. | arXiv: 1108.1797 | DOI: 10.1051/0004-6361/201117848

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: transients, high_z_galaxies
- Question: Statistical analysis of the complete sample of mm/submm observations of GRB afterglows obtained before ALMA science operations, including the first ALMA GRB detection  
  > "In this work we do a statistical analysis of the complete sample of mm/submm observations of GRB afterglows obtained before the beginning of scientific operations at ALMA." (abstract)
- Target **GRB 110715A**: coordinates 15:50:44.05 -46:14:06.54 (ALMA centroid, sign as printed lost in conversion)  
  > "Its redshift was measured to be z = 0.82 (Piranomonte et al. 2011)." (2. Observations); "The centroid of the ALMA position is 15:50:44.05 46:14:06.54 with an uncertainty of 0′′.3 × 0′′.1 at a position angle of 76 degrees." (2. Observations); z/distance z = 0.82  
  > "Its redshift was measured to be z = 0.82 (Piranomonte et al. 2011)." (2. Observations); "The centroid of the ALMA position is 15:50:44.05 46:14:06.54 with an uncertainty of 0′′.3 × 0′′.1 at a position angle of 76 degrees." (2. Observations); distance from Piranomonte et al. 2011  
  > "Its redshift was measured to be z = 0.82 (Piranomonte et al. 2011)." (2. Observations); "The centroid of the ALMA position is 15:50:44.05 46:14:06.54 with an uncertainty of 0′′.3 × 0′′.1 at a position angle of 76 degrees." (2. Observations)

## Data provenance

- ALMA projects: 2011.0.99001.CSV
- bands: Band 7 (345 GHz) for ALMA GRB 110715A  
  > "The ALMA Science Team report a preliminary detection from a test observation of this source of 4.9±0.6 mJy at 345 GHz after 25 mins on source with 7 antennas." (2. Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 7 antennas, commissioning  
  > "after 25 mins on source with 7 antennas" (2. Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 25 min  
  > "after 25 mins on source with 7 antennas" (2. Observations)
- observing dates: 2011 July 19 at 02:50 UT (3.57 days after burst)  
  > "Observations began on July 19 at 02:50 UT (3.57 days after the burst)." (2. Observations)
- pi or archival as stated: _not stated_
- Other facility **APEX/LABOCA**: 345 GHz continuum observations of 6 GRBs  
  > "All these observations were performed using the Large Apex BOlometer CAmera (LABOCA; Siringo et al. 2009)" (2. Observations)
- Other facility **SMA**: Follow-up of 4 bursts  
  > "we have followedup 4 other bursts" (2. Observations)
- External data: Catalogue of published mm/submm GRB observations (Table 1) from 102 GRBs  
  > "we have collected, in Table 1, the most complete sample of continuum observations that have been published to date of GRB afterglows and their host galaxies" (3. The pre-ALMA millimeter/submillimeter sample of GRBs) [from many, e.g. Castro-Tirado et al. 2012; Sheth et al. 2003; Galama et al. 1999]
- External data: X-ray flux densities at 0.5 and 1 day from the Swift burst analyser  
  > "we use the flux densities measured 0.5 days after the burst (when we can assume that the emission is dominated by the afterglow) at 10 keV (Evans et al. 2010)" (3.4 Comparison with X-ray flux densities) [from Evans et al. 2010]

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

- Full analysis of GRB 110715A afterglow deferred to companion paper  
  > "A complete analysis of the afterglow emission of this burst, will be presented by Sanchez-Ramirez et al. (2012)." (2. Observations) [from Sanchez-Ramirez et al. (2012)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration and imaging details (CASA version, calibrators, weighting) for the commissioning data
- How the 4.9 mJy flux and position were measured and the flux scale uncertainty
- Exact gaussian parameters for the peak flux distribution
- Spectral index/offset scheme for Fig. 9

## Analysis recipe

1. **Compile catalogue and detection statistics**: Collect published mm/submm observations, classify detections at >3 sigma, split by ALMA band  
  > "considering as detections only those with higher significance than 3σ, and otherwise providing detection limits" (3. The pre-ALMA millimeter/submillimeter sample of GRBs)
   - fitting: _not stated_
   - validation: _not stated_
2. **Estimate peak flux density distribution and ALMA detection fractions**: Assume log-gaussian peak flux distribution normalised by 30% band 3 detections to ~0.9 mJy, dispersion from X-ray, bias correction factor 1.7  
  > "We assume that the peak flux density of GRB afterglows can be described by a gaussian function in the logarithmic space" (3.3 Estimation of the peak flux density distribution)
   - parameter: dispersion 0.56 (X-ray)  
  > "for the X-rays, using the data from the burst analyser (Evans et al. 2010) find a dispersion of 0.56" (3.3 Estimation of the peak flux density distribution)
   - assumption: Gaussian in log space  
  > "We assume that the peak flux density of GRB afterglows can be described by a gaussian function in the logarithmic space" (3.3. Estimation of the peak flux density distribution)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **BoA** : LABOCA/APEX data reduction  
  > "Data reduction of LABOCA/APEX observations was done using BoA" (2. Observations)
- **CRUSH** : LABOCA data reduction (CRUSH and miniCRUSH)  
  > "as well as CRUSH and miniCRUSH (Kov´acs 2008) software packages." (2. Observations)
- **MIRIAD** : SMA data reduction  
  > "Observations from SMA were reduced using the MIR-IDL [2] and MIRIAD (Sault et al. 1995) packages." (2. Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA flux density of GRB 110715A at 345 GHz | 4.9 | 0.6 | mJy | 0 | ALMA 3.570 345.0 4.90 ± 0.60 |
| Afterglow detections in sample | 22 of 88 (25%) | not stated | dimensionless | 1 | Total 22 / 88 (25%) 4 / 36 (11%) |
| Average peak spectral luminosity | 10^(32.1±0.7) | 0.7 dex | erg s^-1 Hz^-1 | 1 | we obtain an average peak spectral luminosity of 10 [(32][.][1][±][0][.][7)] erg s [−][1] Hz [−][1] |
| Predicted ALMA band 3 detection fraction (early / full) | 87% / 98% | not stated | percent | 2 | 87 % of all the afterglows already in its early configuration with 16 antennas, and 98 % in its full setup of 66 |

## Qualitative findings

- Peak mm/submm flux correlates with X-ray flux at 0.5 d, with significant dispersion  
  > "we can see, as expected, a correlation between the flux density measured in X-rays and in mm/submm, although with a significant dispersion." (3.4 Comparison with X-ray flux densities)

## Claim tuples

- H: Can ALMA detect most GRB afterglows? | E: Estimated peak flux distribution compared with ALMA sensitivities | R: 87% early, 98% full detection in band 3 | F: ALMA will detect nearly all afterglows near peak | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Peak detections are only lower limits; samples are biased by low detection rates  
  > "The peak detections are, strictly speaking, only lower limits to the peak flux density in each band" (3. The pre-ALMA millimeter/submillimeter sample of GRBs)
- Caveat (inferred, ours): Heterogeneous literature sample with strong selection bias
- Caveat (inferred, ours): ALMA result is preliminary and unprocessed details absent
- Caveat (inferred, ours): Peak distribution estimate rests on ad hoc assumptions

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA commissioning data reduction details
- Missing: Peak distribution fit specifics
- Data volume (inferred): small (<1 GB for one short commissioning observation)
- Score (inferred): 2/5, ALMA part is a single preliminary flux; main results derive from literature compilation.
- Rediscovery candidate: no, ALMA data are commissioning and recipe is incomplete.

## Links

- Companion: Sanchez-Ramirez et al. (2012) (Full analysis of GRB 110715A)
- Related: Swift XRT burst analyser

## Checks

```json
{
 "quotes": 32,
 "quotes_ok": 32,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.0.99001.CSV"
 ],
 "obscore_codes_not_in_card": [
  "2011.0.00001.E"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 61,
  "stated": 22,
  "rate": 0.361
 },
 "evidence_ok": true
}
```
