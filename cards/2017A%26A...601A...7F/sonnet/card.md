# SPHERE/SHINE reveals concentric rings in the debris disk of HIP 73145

`2017A&A...601A...7F` | Astronomy and Astrophysics 2017 | first author: Feldt, M. | arXiv: 1612.07621 | DOI: 10.1051/0004-6361/201629261

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: debris_disks
- Question: What is the structure of the HIP 73145 debris disk in scattered light (SPHERE) and in the mm (ALMA), and what do the combined modeling and SED imply for dust properties?  
  > "We detect a bright ring of scattered light plus some secondary structures inside, at least one of them forming a secondary, concentric ring with the first." (abstract)
- Target **HIP 73145**: coordinates _not stated_; z/distance 123 pc (122.7 +16.2/-12.8 pc)  
  > "is an A2IV star ((cite: Houk1982)) 123 pc from Earth ((cite: vanLeeuwen2007)) and has an age of about 15 Myr ((cite: Pecaut2012))." (1 Introduction); distance from van Leeuwen 2007  
  > "is an A2IV star ((cite: Houk1982)) 123 pc from Earth ((cite: vanLeeuwen2007)) and has an age of about 15 Myr ((cite: Pecaut2012))." (1 Introduction)

## Data provenance

- ALMA projects: 2012.1.00688.S
- bands: Band 6 (245 GHz, 1.22 mm)  
  > "Band 6 (245 GHz, 1.22 mm)" (2.2 ALMA)
- frequencies and spectral setup: two broadest spectral windows, 128 channels covering 1.875 GHz each  
  > "We exported the complex visibilities from the two broadest spectral windows (128 channels covering 1.875 GHz each)." (2.2 ALMA)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.20" x 0.95", PA 25.4 deg  
  > "The beam has a size of $1.20^{\prime\prime} \times 0.95^{\prime\prime}$, with a position angle of $25.4^{\circ}$" (2.2 ALMA)
- max recoverable scale: _not stated_
- sensitivity: 0.12 mJy/beam rms in empty regions  
  > "we measure a standard deviation of $0.12$ mJy/beam in empty regions of the image" (2.2 ALMA)
- time on source: _not stated_
- observing dates: 10 Jan. 2014, Cycle 0  
  > "On the 10$^{\mathrm{th}}$ of Jan. 2014, HIP 73145 was observed during Cycle 0" (2.2 ALMA)
- pi or archival as stated: _not stated_
- Other facility **VLT/SPHERE (IRDIS, IFS)**: H2/H3 and YJ ADI scattered-light imaging, companion search  
  > "HIP 73145 was observed with the extreme adaptive optics coronagraphic instrument SPHERE" (2.1 SPHERE)
- Other facility **Herschel/PACS**: 70 and 100 micron resolved sizes compared with model (from literature)  
  > "found that the debris disk was marginally resolved with the *Herschel*/PACS observations at 70 and 100 $\mu$m" (5.3 Modeling results)
- External data: SED fluxes used for SED modeling  
  > "constructed with the fluxes reported in (cite: Moor2015)" (7 Modeling the SED) [from Moor2015]

## Processing

### Calibration

- pipeline or manual: CASA with observatory-provided scripts  
  > "We reduced the observations within CASA ((cite: McMullin2007)) with scripts provided by the observatory." (2.2 ALMA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: clean algorithm used for reconstructed image  
  > "we show the reconstructed image obtained with the `clean` algorithm" (2.2 ALMA)
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

- ALMA visibility modeling procedure  
  > "To model the ALMA observations, we proceeded as in (cite: Olofsson2016)" (6 Modeling of the ALMA observations) [from Olofsson2016]
- SED modeling procedure  
  > "We follow the same procedure as described in (cite: Olofsson2016)" (7 Modeling the SED) [from Olofsson2016]

### Not stated but needed to reproduce (our reading)

- CASA version
- clean parameters (weighting, robust, cell, niter, masks)
- flux calibrator and calibration details
- grid ranges and sampling of the chi2 search
- observation details such as baselines/configuration

## Analysis recipe

1. **Average ALMA visibilities**: Export visibilities from two widest spws, average over channels, estimate uncertainties from scatter  
  > "We averaged the complex visibilities over the 128 spectral channels" (2.2 ALMA)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Model ALMA visibilities**: Synthetic 1.22 mm image, Fourier transformed and interpolated at uv points; chi2 grid over r0, alpha_out, f_mm with other parameters fixed to SPHERE best fit  
  > "we instead perform a simple $\chi^2$ grid search over the following three free parameters" (6 Modeling of the ALMA observations)
   - software: DDiT
   - assumption: Central star not included; inclination and PA from SPHERE fit  
  > "We do not include the central star in the synthetic image." (6 Modeling of the ALMA observations)
   - fitting: chi2 grid search, degeneracy between r0 and alpha_out  
  > "there is a valley of low $\chi^2$ values" (6 Modeling of the ALMA observations)
   - validation: _not stated_

## Software

- **CASA** : ALMA data reduction and clean imaging  
  > "We reduced the observations within CASA ((cite: McMullin2007))" (2.2 ALMA)
- **emcee** : MCMC for SPHERE and SED modeling  
  > "implemented in the `emcee` Python package" (5.2 Modeling strategy)
- **DDiT** : synthetic disk images  
  > "we produce a synthetic image using the `DDiT` code" (5.2 Modeling strategy)
- **scikit-learn** : PCA in forward modeling  
  > "using the implementation of the `scikit-learn` Python package" (5.2 Modeling strategy)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA best-fit reference radius | 21.6 | conservative interval [20,110] | au | 2 | $r_0 = 21.6$ au, $\alpha_{\mathrm{out}} = -1.95$, and $f_{\mathrm{mm}} = 3.5$ mJy |
| ALMA 1.22 mm flux | 3.5 | not stated | mJy | 2 | $f_{\mathrm{mm}} = 3.5$ mJy |
| SPHERE B1 reference radius | 90.1 | +1.2/-1.1 | au | 0 | $90.1_{-1.1}^{+1.2}$ |
| Outer belt dust mass | 7.2 | +/-0.6 | Earth masses | 0 | $7.2_{-0.6}^{+0.6}$ |

## Qualitative findings

- The ALMA disk appears more compact than in SPHERE, reconcilable via radiation pressure on small grains.  
  > "Therefore the disk would appear more extended in the SPHERE observations than in the ALMA observations." (6 Modeling of the ALMA observations)

## Claim tuples

- H: Is the mm disk as extended as the scattered-light disk? | E: chi2 grid fit of ALMA visibilities | R: r0 = 21.6 au best fit but degenerate with alpha_out; r0 in [20,110] au | F: The data cannot exclude an extent like SPHERE; higher resolution is needed. | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: MCMC was rejected for the ALMA data because the disk is barely resolved and parameters are degenerate.  
  > "the MCMC approach we used for the SPHERE data has difficulty providing meaningful constraints on the disk parameters" (6 Modeling of the ALMA observations)
- How they decided it was enough: _not stated_
- Limitation (authors): The disk is barely resolved by ALMA, giving a degenerate r0 and alpha_out.  
  > "Given that the disk is barely resolved (see Fig.[8](#fig:alma))" (6 Modeling of the ALMA observations)
- Caveat (inferred, ours): Low ALMA resolution (about 1 arcsec) limits the constraints
- Caveat (inferred, ours): Single-epoch data; ALMA imaging details are sparse

## Reproducibility

- Data public (paper): Cycle 0 program cited with ALMA acknowledgement  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA 2012.1.00688.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: CASA version and clean parameters
- Missing: DDiT code availability
- Missing: chi2 grid specifics
- Data volume (inferred): ~5-20 GB for the ALMA Cycle 0 dataset
- Score (inferred): 3/5, The ALMA data appear public and the visibility modeling is simple, but the processing is sparsely described and relies on Olofsson2016.
- Rediscovery candidate: no, The ALMA part is minor and the modeling relies on unreleased or inherited code with incomplete parameters.

## Links

- Method: Olofsson2016 (modeling strategy for scattered light, ALMA and SED)
- Companion: Lieman-Sifry et al., submitted (source of the ALMA program)
- Related: SHINE

## Checks

```json
{
 "quotes": 35,
 "quotes_ok": 35,
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
  "stated": 27,
  "rate": 0.435
 },
 "evidence_ok": true
}
```
