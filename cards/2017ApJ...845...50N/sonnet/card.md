# A Multi-wavelength Study of the Turbulent Central Engine of the Low-mass AGN Hosted by NGC 404

`2017ApJ...845...50N` | The Astrophysical Journal 2017 | first author: Nyland, Kristina | arXiv: 1707.02303 | DOI: 10.3847/1538-4357/aa7ecf

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: What is the origin of the resolved nuclear radio emission in the low-mass AGN of NGC 404, and is there evidence for shocks or local feedback?  
  > "we find the most likely scenario for the origin of the radio source in the center of NGC 404 to be a radio outflow associated with a confined jet driven by the active nucleus." (abstract)
- Target **NGC 404**: coordinates RA 01h09m27.000s, Dec +35d43m04.93s (J2000, CO disk)  
  > "NGC 404 is a nearby (D = 3 _._ 06 _±_ 0 _._ 37 Mpc; Karachentsev et al. 2002), dwarf S0 galaxy" (1. INTRODUCTION AND MOTIVATION); "This source is located at _α_ J2000 = 01 [h] 09 [m] 27.000 [s] and _δ_ J2000 = +35 _[◦]_ 43 _[′]_ 04.93 _[′′]_" (3.2 Molecular Gas Properties); z/distance D = 3.06 ± 0.37 Mpc; z = -0.00016  
  > "NGC 404 is a nearby (D = 3 _._ 06 _±_ 0 _._ 37 Mpc; Karachentsev et al. 2002), dwarf S0 galaxy" (1. INTRODUCTION AND MOTIVATION); "This source is located at _α_ J2000 = 01 [h] 09 [m] 27.000 [s] and _δ_ J2000 = +35 _[◦]_ 43 _[′]_ 04.93 _[′′]_" (3.2 Molecular Gas Properties); distance from Karachentsev et al. 2002  
  > "NGC 404 is a nearby (D = 3 _._ 06 _±_ 0 _._ 37 Mpc; Karachentsev et al. 2002), dwarf S0 galaxy" (1. INTRODUCTION AND MOTIVATION); "This source is located at _α_ J2000 = 01 [h] 09 [m] 27.000 [s] and _δ_ J2000 = +35 _[◦]_ 43 _[′]_ 04.93 _[′′]_" (3.2 Molecular Gas Properties)

## Data provenance

- ALMA projects: 2015.1.00597.S
- bands: Band 6 covering CO(2–1)  
  > "ALMA observations in band 6 covering the CO(2–1) line at a rest frequency of 230 GHz were performed on October 31, 2015 (P.I. Anil Seth)." (2.2 ALMA)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.06" x 0.04" (0.9 x 0.6 pc)  
  > "a synthesized beam size of 0 _._ 06 _[′′]_ _×_ 0 _._ 04 _[′′]_" (2.2 ALMA)
- max recoverable scale: _not stated_
- sensitivity: 0.4 mJy/beam per 10 km/s channel; continuum 5σ limit 51 µJy/beam  
  > "a channel width of 10 km s [−][1], a sensitivity of 0.4 mJy beam [−][1]" (2.2 ALMA)
- time on source: _not stated_
- observing dates: 2015 October 31  
  > "performed on October 31, 2015 (P.I. Anil Seth)" (2.2 ALMA)
- pi or archival as stated: PI Anil Seth  
  > "(P.I. Anil Seth)" (2.2 ALMA)
- Line: CO J=2–1 (230 GHz)
- Other facility **VLA**: Ku-band 12–18 GHz imaging (project 14A-305)  
  > "project ID: 14A-305" (2.1 VLA)
- Other facility **HST**: archival narrowband Halpha and F814W imaging  
  > "archival H _α_ data from _HST_" (5.1 Shocks)
- Other facility **Chandra**: archival soft X-ray image (obsid 12239)  
  > "we reprocessed obsid 12239 using CIAO v4.9" (5.1.2 Soft X-rays)
- Other facility **Spitzer IRS**: archival mid-IR spectra via CASSIS  
  > "we obtained archival _Spitzer_ Infrared Spectrograph" (5.1.3 Infrared Spectroscopy)
- External data: VLA 1.5, 5, 7.5 GHz measurements  
  > "as well as the _L_ - and _C_ -band data presented in Nyland et al. (2012)" (3.1.1 Morphology and Flux Density) [from Nyland et al. (2012)]
- External data: Total molecular gas mass 9.0e6 Msun from BIMA CO(1-0)  
  > "total molecular gas mass measured in Taylor et al. (2015) of 9.0 _×_ 10 [6] M _⊙_" (3.2 Molecular Gas Properties) [from Taylor et al. (2015)]
- External data: Galactic SNR spectral index database  
  > "Using the database of Galactic supernova remnant properties compiled by Green (2014)" (4.2 Supernova Remnant) [from Green (2014)]

## Processing

### Calibration

- pipeline or manual: ALMA calibration pipeline  
  > "calibration was performed using the ALMA calibration pipeline." (2.2 ALMA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA CLEAN  
  > "Imaging was performed in CASA using the CLEAN task with Briggs weighting and a robustness parameter of 0.5." (2.2 ALMA)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "Briggs weighting and a robustness parameter of 0.5" (2.2 ALMA)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: UVCONTSUB in CASA  
  > "We produced a continuum-subtracted spectral line cube using the UVCONTSUB task in CASA." (2.2 ALMA)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.06" x 0.04"  
  > "a synthesized beam size of 0 _._ 06 _[′′]_ _×_ 0 _._ 04 _[′′]_" (2.2 ALMA)
- final rms: _not stated_

### Inherited from earlier work

- Full ALMA data details deferred to companion paper  
  > "Full details on these data will be presented in Davis et al. (in preparation)." (2.2 ALMA) [from Davis et al. (in preparation)]

### Not stated but needed to reproduce (our reading)

- CASA version for ALMA reduction
- Line-free channels and continuum-subtraction fit order
- Cell and image size, masking, and clean threshold for ALMA
- Moment-map clipping and region used for flux integration
- Spectral setup and integration time of ALMA data

## Analysis recipe

1. **Image CO(2-1) cube and continuum**: CLEAN with Briggs robust 0.5, UVCONTSUB, 10 km/s channels  
  > "We produced a continuum-subtracted spectral line cube using the UVCONTSUB task in CASA." (2.2 ALMA)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive molecular gas mass of CO disk**: Bolatto et al. (2013) equation from CO(2-1) flux with CO(2-1)/(1-0) ratio  
  > "we obtain a molecular gas mass of _M_ H 2 = 1 _._ 1 _×_ 10 [5] M _⊙_ for the nuclear CO(2–1) disk." (3.2 Molecular Gas Properties)
   - parameter: integrated CO(2-1) flux 2.68 Jy km/s over ~100 km/s  
  > "integrated CO(2–1) line flux of 2.68 Jy km s [−][1] (measured over a linewidth of _∼_ 100 km s [−][1] )" (3.2 Molecular Gas Properties)
   - assumption: Milky Way XCO = 2.3e20 and CO(2-1)/(1-0) flux ratio 3.2  
  > "We assume a standard Milky Way _X_ CO value of 2.3 _×_ 10 [20] cm [−][2] (K km s [−][1] ) [−][1]" (3.2 Molecular Gas Properties)
   - fitting: _not stated_
   - validation: _not stated_
3. **Estimate nuclear SFR from molecular gas**: Gao & Solomon SFR-H2 relation and Kennicutt-Schmidt relation with annular disk area  
  > "we find a nuclear SFR of 1 _._ 6 _×_ 10 [−][4] M _⊙_ yr [−][1] ." (4.1.2 Molecular Gas Constraints on Star Formation)
   - parameter: annulus r_inner 0.25 pc, r_outer 3 pc  
  > "an inner radius of _r_ inner = 0 _._ 25 pc and an outer radius of _r_ outer = 3 pc" (4.1.2 Molecular Gas Constraints on Star Formation)
   - fitting: _not stated_
   - validation: Compared with Halpha and radio SFR limits  
  > "factors of about 2 to 7 times lower than the SFR upper limit from the nuclear H _α_ observations" (4.1.2 Molecular Gas Constraints on Star Formation)

## Software

- **CASA** 4.1.0 (VLA); ALMA version not stated: calibration and imaging of VLA and ALMA data  
  > "(version 4.1.0)" (2.1 VLA)
- **AIPS JMFIT** : Gaussian fits for flux measurement of VLA data  
  > "measured using the JMFIT task in the Astronomical Image Processing System (AIPS)" (Table 1)
- **CIAO** v4.9: Chandra reprocessing and smoothing  
  > "we reprocessed obsid 12239 using CIAO v4.9" (5.1.2 Soft X-rays)
- **PAHFIT** : fitting PAH features in Spitzer IRS  
  > "spectral fitting tool PAHFIT (Smith et al. 2007)" (5.1.3 Infrared Spectroscopy)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(2-1) nuclear disk molecular gas mass | 1.1e5 | not stated | Msun | 2 | we obtain a molecular gas mass of _M_ H 2 = 1 _._ 1 _×_ 10 [5] M _⊙_ for the nuclear CO(2–1) disk. |
| Nuclear SFR from CO (Gao & Solomon) | 1.6e-4 | not stated | Msun/yr | 3 | we find a nuclear SFR of 1 _._ 6 _×_ 10 [−][4] M _⊙_ yr [−][1] . |
| 1-18 GHz radio spectral index | -1.08 | 0.03 | dimensionless | 0 | of _α_ = −1 _._ 08 _±_ 0.03 |

## Qualitative findings

- CO(2-1) disk is regularly rotating and centered on the radio peak, within 0.02" of the VLA position  
  > "The VLA position is wellmatched to that of the center of rotation of the CO(2–1) nuclear disk detected by ALMA, with a spatial offset of only 0.02 _[′′]_ ." (3.3 Astrometry)

## Claim tuples

- H: Is the resolved nuclear radio source powered by star formation? | E: Compared CO-derived SFR with radio and Halpha SFR | R: CO SFRs are 2-7 times lower than the radio and Halpha SFRs | F: Star formation origin is disfavored | **supported**
- H: Is the radio source an AGN-driven confined jet or outflow? | E: Multiwavelength astrometric coincidence, spectral index and size | R: Radio peak coincides with CO disk center, dynamical center and X-ray source; alpha=-1.08 | F: Confined jet/outflow from the MBH is most likely | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Supernova remnant, X-ray binary/microquasar and disk wind origins judged unlikely or challenging  
  > "pose substantial challenges to the supernova remnant scenario" (6. SUMMARY AND FUTURE WORK)
- How they decided it was enough: _not stated_
- Limitation (authors): ALMA data likely resolve out most extended molecular gas  
  > "the ALMA CO(2–1) observations have likely resolved out most of the molecular gas detected in Taylor et al. (2015)." (3.2 Molecular Gas Properties)
- Caveat (inferred, ours): XCO and CO line ratio assumptions are uncertain in a low-metallicity dwarf nucleus
- Caveat (inferred, ours): ALMA processing is only sketched; the main ALMA analysis is deferred to a companion paper

## Reproducibility

- Data public (paper): ALMA project code acknowledged; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00597.S." (ACKNOWLEDGMENTS)
- Products in archive: _not stated_
- Missing: Detailed ALMA reduction parameters
- Missing: CASA version for ALMA
- Missing: Details given only in Davis et al. in prep
- Data volume (inferred): ~10-50 GB (single Band 6 cube dataset)
- Score (inferred): 3/5, ALMA part is minor and thinly described, though the derived mass is easily reproducible from the quoted flux.
- Rediscovery candidate: no, ALMA recipe incomplete and details deferred to unpublished companion paper.

## Links

- Method: Bolatto et al. (2013) (CO-to-H2 mass equation and XCO)
- Companion: Davis et al. (in preparation) (Full ALMA data details and MBH dynamical modeling)
- Companion: Nguyen et al. (2017) (Stellar dynamics MBH mass limit and HST data)

## Checks

```json
{
 "quotes": 48,
 "quotes_ok": 48,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 37,
  "rate": 0.529
 },
 "evidence_ok": true
}
```
