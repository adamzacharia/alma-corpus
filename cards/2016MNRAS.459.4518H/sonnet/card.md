# The detection of dust around NN Ser

`2016MNRAS.459.4518H` | Monthly Notices of the Royal Astronomical Society 2016 | first author: Hardy, Adam | arXiv: 1604.05808 | DOI: 10.1093/mnras/stw976

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: stellar_physics, protoplanetary_disks
- Question: Is there dust (a circumbinary disc) around the post-common-envelope binary NN Ser, and what is its origin?  
  > "To test this hypothesis, we searched for dust remaining after the common envelope around NN Ser." (Introduction)
- Target **NN Ser**: coordinates _not stated_; z/distance 512±43 pc  
  > "where a distance of $512\pm43$ pc was assumed (cite: Parsons2010a)" (3.2 Thermal emission from dust); distance from Parsons et al. 2010a  
  > "where a distance of $512\pm43$ pc was assumed (cite: Parsons2010a)" (3.2 Thermal emission from dust)

## Data provenance

- ALMA projects: 2013.1.01342.S
- bands: Band 6 (1.3 mm), single continuum mode  
  > "The single continuum mode in Band 6 was used, implying a total bandwidth of 7.5 GHz with individual channel widths of 15.625 MHz." (ALMA Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: 7.5 GHz total, 15.625 MHz channels  
  > "implying a total bandwidth of 7.5 GHz with individual channel widths of 15.625 MHz" (ALMA Observations)
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15.1 m to 348.5 m, 39 antennas  
  > "39 antennas were used, with minimum and maximum baselines of 15.1 m and 348.5 m respectively." (ALMA Observations)
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: requested rms 25 μJy  
  > "as the rms sensitivity of the data did not reach the requested value of 25$\mu$J in the first instance" (ALMA Observations)
- time on source: 34.35 min (5 scans of 6.87 min)  
  > "The observations consisted of 5 scans of 6.87 min each, translating to a total time on the science target of 34.35 min." (ALMA Observations)
- observing dates: 2014-04-30 and repeated 2015-01-22; only the second used  
  > "The Atacama Large Millimeter/submillimeter Array (ALMA) observations were conducted on 2014-04-30 and repeated on the 2015-01-22" (ALMA Observations)
- pi or archival as stated: _not stated_
- Other facility **SOFI/NTT**: J, H, Ks photometry  
  > "$J, H$ and $K$ band observations of NN Ser were obtained with the Son of Isaac instrument (SOFI)" (SOFI Observations)
- Other facility **Spitzer IRAC**: 3.6-8.0 um photometry  
  > "Data were taken with the Infrared Array Camera (cite: Fazio2004) with 25 x 100s dithers in all 4 channels (3.6 um - 8.0 um)." (Spitzer Observations)
- External data: Optical photometry and light curve model of NN Ser; distance  
  > "we also took the optical data from (cite: Parsons2010a), and calculated the emission at our chosen phase" (Observations) [from Parsons et al. 2010a (cite: Parsons2010a)]
- External data: 1.3 mm dust mass constant  
  > "We adopt the constant derived for 1.3mm by (cite: Cieza2008a)" (3.2 Thermal emission from dust) [from (cite: Cieza2008a)]
- Simulation/model as data: Modified MERCURY N-body simulations with BSE luminosity input  
  > "Three simulations were performed using a modified version of the N-body simulator MERCURY (cite: Chambers1999)." (Possible origins for the dust)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: not stated; bandpass J1337-1257, phase J1550+0527  
  > "The calibration sources associated with these observations were J1337-1257 for band-pass calibration, and J1550+0527 for phase calibrations." (ALMA Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CLEAN; flux from uvmodelfit point-source fit  
  > "a point-source fit to the visibilities was performed using the uvmodelfit task in casapy version 4.2.2" (ALMA Observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "deconvolved using the CLEAN algorithm with natural weighting to create the final image" (ALMA Observations)
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

- Dust mass constant for 1.3 mm  
  > "We adopt the constant derived for 1.3mm by (cite: Cieza2008a)" (3.2 Thermal emission from dust) [from (cite: Cieza2008a)]

### Not stated but needed to reproduce (our reading)

- Pipeline vs manual calibration and CASA version used for calibration
- Flux calibrator and flux scale uncertainty
- Image size, cell size, beam, and rms
- Clean threshold/masking
- Whether the first epoch was fully discarded and details of pointing error
- Source position used in uvmodelfit

## Analysis recipe

1. **Measure 1.3 mm flux**: Point-source fit to visibilities  
  > "a point-source fit to the visibilities was performed using the uvmodelfit task in casapy version 4.2.2, resulting in a flux value of 0.11$\pm$0.03 mJy" (ALMA Observations)
   - software: CASA uvmodelfit
   - fitting: _not stated_
   - validation: _not stated_
2. **Estimate dust mass**: Optically thin scaling M_dust=0.566 F(1300)/mJy (d/140 pc)^2 Earth masses  
  > "M_{\mathrm{dust}}=0.566 \times \left[ \dfrac{F_{\nu}(1300)}{\rm mJy} \left( \dfrac{d}{140\,\rm pc} \right)^{2} \right] M_{\oplus}" (3.2 Thermal emission from dust)
   - assumption: optically thin dust, distance 512±43 pc  
  > "the dust emission at this wavelength is optically thin" (3.2 Thermal emission from dust)
   - fitting: _not stated_
   - validation: _not stated_
3. **Test dust origin with N-body simulations**: Modified MERCURY with radiation forces, wind drag, mass loss; collisional timescale from Wyatt 2010  
  > "The modifications account for the additional forces felt by particles surrounding the binary." (Possible origins for the dust)
   - software: MERCURY, BSE
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA (casapy)** 4.2.2: uvmodelfit point-source fit and CLEAN  
  > "uvmodelfit task in casapy version 4.2.2" (ALMA Observations)
- **MERCURY** : N-body simulations of dust  
  > "modified version of the N-body simulator MERCURY (cite: Chambers1999)" (Possible origins for the dust)
- **BSE** : time-varying luminosity  
  > "calculated using the Binary Star Evolution (BSE) code (cite: Hurley2002)" (Possible origins for the dust)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 1.3 mm flux | 0.11 | 0.03 | mJy | 1 | resulting in a flux value of 0.11$\pm$0.03 mJy |
| dust mass | 0.8 | 0.2 | Earth masses | 2 | to a derive value of $0.8\pm0.2\,M_{\oplus}$ for the dust mass around NN Ser |

## Qualitative findings

- Dust most likely originates from common-envelope material forming a circumbinary disc  
  > "we find that a disc of left over common-envelope material is the most likely explanation for the detection." (Conclusions)

## Claim tuples

- H: Does NN Ser host detectable cold dust? | E: ALMA Band 6 observation | R: 0.11±0.03 mJy at 1.3 mm, giving ~0.8 Earth masses | F: Excess likely thermal dust emission | **supported**
- H: Could the dust be a surviving first-generation debris disc? | E: MERCURY simulations of discs at 10, 50, 100 au | R: At least ~90% flux decrease; collisional timescales very long | F: Very unlikely pre-CE dust | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Gyrosynchrotron emission considered unlikely but not ruled out  
  > "this gyrosynchrotron emission cannot be conclusively ruled out without further observations" (Gyrosynchrotron emission)
- How they decided it was enough: _not stated_
- Limitation (authors): Single SED point, grain size and surface density unconstrained; dust mass relies on grain assumptions  
  > "With just one SED point, the grain size distribution and surface density distribution of this disc cannot be constrained." (3.2 Thermal emission from dust)
- Caveat (inferred, ours): Detection is ~3.7 sigma from a single unresolved point
- Caveat (inferred, ours): Gyrosynchrotron not excluded without second frequency
- Caveat (inferred, ours): Project code in acknowledgements differs from the archive-linked code
- Caveat (inferred, ours): Dust opacity and temperature assumptions are simple

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Full calibration details and CASA version
- Missing: Modified MERCURY code
- Missing: Imaging parameters
- Data volume (inferred): ~10-50 GB raw single-execution continuum
- Score (inferred): 3/5, Simple flux measurement is reproducible but calibration and code details are missing.
- Rediscovery candidate: no, Calibration and imaging recipes are incomplete and the simulation code is not public.

## Links

- Method: Cieza et al. 2008a (cite: Cieza2008a) (dust mass constant)
- Method: Wyatt 2010 (cite: Wyatt2010) (collisional rate prescription)
- Companion: Parsons et al. 2010a (cite: Parsons2010a) (optical data, light curve model, distance)

## Checks

```json
{
 "quotes": 34,
 "quotes_ok": 34,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2013.1.01342.S"
 ],
 "obscore_codes_not_in_card": [
  "2013.1.00468.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 2,
 "numeric_problems": 0,
 "fill": {
  "facts": 65,
  "stated": 28,
  "rate": 0.431
 },
 "evidence_ok": true
}
```
