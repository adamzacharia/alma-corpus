# The SCUBA-2 Cosmology Legacy Survey: Multiwavelength Counterparts to 10<SUP>3</SUP> Submillimeter Galaxies in the UKIDSS-UDS Field

`2016ApJ...820...82C` | The Astrophysical Journal 2016 | first author: Chen, Chian-Chou | arXiv: 1601.02630 | DOI: 10.3847/0004-637X/820/2/82

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies
- Question: Which multiwavelength counterparts (radio and optical-IR colour selected) can be identified for SCUBA-2 850 um sources in UKIDSS-UDS, trained on ALMA-detected SMGs, and what are their redshift distribution and clustering?  
  > "By utilising an ALMA pilot study on a subset of our bright SCUBA-2 sample as a training set" (abstract)
- Target **SCUBA-2 sources in the UKIDSS-UDS field (30 ALMA-observed bright sources)**: coordinates _not stated_; z/distance photometric redshifts; median z=2.3  
  > "We have carried out ALMA follow-up observations at 870 $\mu$m on 30 of the brighter SCUBA-2 sources in a Cycle-1 project 2012.1.00090.S" (2.2 ALMA); distance from photometric redshifts from eazy (Hartley et al. 2013)  
  > "We have carried out ALMA follow-up observations at 870 $\mu$m on 30 of the brighter SCUBA-2 sources in a Cycle-1 project 2012.1.00090.S" (2.2 ALMA)

## Data provenance

- ALMA projects: 2012.1.00090.S
- bands: 870 um (ALMA Cycle 1)  
  > "We have carried out ALMA follow-up observations at 870 $\mu$m on 30 of the brighter SCUBA-2 sources" (2.2 ALMA)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.8'' FWHM (also ~0.3'' versions)  
  > "with a synthesized beam of $\sim$ 0$\ensuremath{''}$8 FWHM" (2.2 ALMA)
- max recoverable scale: _not stated_
- sensitivity: median rms 0.26 mJy/beam  
  > "With a median rms of $\sigma =$ 0.26 mJy beam$^{-1}$" (2.2 ALMA)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **JCMT SCUBA-2 (S2CLS)**: 850 um survey map and 1088 sources  
  > "In total we detect 1088 submillimeter sources at $\geq$ 3.5 $\sigma$" (2.1 SCUBA-2)
- Other facility **VLA 1.4 GHz (UDS20)**: radio counterparts  
  > "The VLA radio observations at 1.4 GHz (20 cm) were carried out by the project UDS20" (2.3 Multi-wavelength ancillary data)
- Other facility **UKIDSS UDS, Subaru, CFHT, Spitzer**: optical-NIR-MIR photometry and photo-z  
  > "Eleven-band photometry ($UBVRIzJHK$\[3.6\]\[4.5\]) was measured with 3$''$ diameter apertures" (2.3 Multi-wavelength ancillary data)
- External data: ALMA SMG catalogue (52 SMGs) from the UDS pilot  
  > "the primary ALMA catalog consists of 52 SMGs detected by ALMA at $> 4\,\sigma$" (2.2 ALMA) [from (cite: Simpson:2015ab)]
- External data: photometric redshifts for the K-band parent sample  
  > "Photometric redshifts ($z_{\rm photo}$) have been derived for the DR8 parent sample" (2.3 Multi-wavelength ancillary data) [from (cite: Hartley:2013aa)]

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

- ALMA data reduction and source extraction  
  > "the data reduction and source extraction can be found in (cite: Simpson:2015ab)" (2.2 ALMA) [from (cite: Simpson:2015ab)]
- SCUBA-2 reduction and source extraction  
  > "The full data reduction steps are described fully in Geach et al. (2015 in preparation)" (2.1 SCUBA-2) [from Geach et al. in prep]

### Not stated but needed to reproduce (our reading)

- ALMA calibration, imaging parameters and CASA version (deferred to Simpson et al. 2015)
- ALMA catalogue positions and fluxes needed to rebuild the training set
- Binning used for the f_OIRTC histograms
- Radio catalogue (UDS20) not yet published
- Photometric catalogue (Almaini et al. in prep)

## Analysis recipe

1. **Test radio and MIPS p-value identifications against ALMA**: Corrected-Poissonian p-values; accuracy and completeness measured against 52 ALMA SMGs  
  > "p=1-exp(-\pi n \theta^2)" (3.1 Radio identifications)
   - fitting: _not stated_
   - validation: Accuracy and completeness compared with ALMA  
  > "The main parameters we consider in the tests and the training are accuracy and completeness" (Counterpart identification)
2. **Develop OIRTC colour selection**: MIC correlation of S850 with colours; fit f_OIRTC=1/(a+exp(-b(x-c))) per colour; weighted mean fraction cut at 0.05  
  > "We therefore first model $f_{\rm OIRTC}$ as a function of color by fitting a functional form, parametrized as $1/(a + e^{-b(x-c)})$" (3.3 Optical-IR Triple Color (OIRTC))
   - software: MINE
   - fitting: chi2 fit, errors from Delta chi2=1; f_OIRTC errors from 100 Monte Carlo realisations  
  > "All errors are obtained assuming $\Delta \chi^2 = 1$" (Optical-IR Triple Color (OIRTC))
   - validation: Tested on SMA sample and ALESS  
  > "We test our counterpart identification technique on two independent samples that are obtained from ALMA and SMA observations." (3.4.1 Testing our identification methodology)
3. **Redshift distribution and clustering**: Lognormal fit to photo-z distribution; Landy-Szalay w(theta) with integral constraint and jackknife errors  
  > "we calculate the two-point autocorrelation function $w(\theta)$ using the Landy & Szalay (1993) estimator." (SMG clustering)
   - fitting: chi2 minimisation  
  > "We then perform $\chi^2$ minimization using [\[eqn:wth\]](#eqn:wth) to find the best fit $w(\theta)_{true}$" (SMG clustering)
   - validation: _not stated_

## Software

- **MINE** : maximal information coefficient  
  > "we use the maximal information coefficient (MIC) statistics of the MINE package" (3.3 Optical-IR Triple Color (OIRTC))
- **eazy** : photometric redshifts  
  > "the photometric redshifts are estimated using the eazy template-fitting package" (2.3 Multi-wavelength ancillary data)
- **SExtractor** : 24 um source extraction  
  > "we use SExtractor (cite: Bertin:1996zr) to extract sources" (2.3 Multi-wavelength ancillary data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Class=1 identification accuracy (ALMA-trained) | 82 | 20 | % | 2 | we expect the accuracy of these identifications to be $82\pm20$%, with a completeness of $69\pm16$% |
| Median photo-z of counterparts | 2.3 | 0.1 | dimensionless | 3 | with a median redshift of $z=2.3\pm0.1$ |
| Median z corrected for unidentified sources | 2.6 | 0.1 | dimensionless | 3 | we estimate the median redshift to be $z=2.6\pm0.1$ |
| Galaxy bias | 9.1 | +2.1/-2.8 | dimensionless | 3 | galaxy bias of $b = 9.1^{+2.1}_{-2.8}$ |

## Qualitative findings


## Claim tuples

- H: Can radio plus optical-IR colours identify SMG counterparts as accurately as p-values but with higher completeness? | E: Trained on 52 ALMA SMGs and tested on SMA and ALESS | R: Radio+OIRTC accuracy 83%, completeness 67% | F: The OIRTC technique complements radio identification | **supported**
- H: What is the SMG redshift distribution? | E: Photo-z of candidate counterparts | R: Median z=2.3 with lognormal fit | F: Median z about 2.6 after correcting for unidentified sources | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Caveat (inferred, ours): Training set is small and biased to bright sources
- Caveat (inferred, ours): Photo-z and counterpart incompleteness bias against high z
- Caveat (inferred, ours): ALMA is used only as a training set

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Full ALMA catalogue and photometric catalogues not given in this paper
- Missing: Radio catalogue unpublished
- Data volume (inferred): small if only catalogues used; tens of GB for raw ALMA data
- Score (inferred): 3/5, The ALMA role is a catalogue training set; the inputs come from other papers.
- Rediscovery candidate: no, Depends on catalogues not provided here.

## Links

- Method: (cite: Simpson:2015ab) (ALMA reduction and catalogue)
- Companion: (cite: Simpson:2015aa) (ALMA pilot study of SMG sizes)
- Related: S2CLS
- Related: UKIDSS UDS
- Related: ALESS

## Checks

```json
{
 "quotes": 31,
 "quotes_ok": 31,
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
  "facts": 62,
  "stated": 23,
  "rate": 0.371
 },
 "evidence_ok": true
}
```
