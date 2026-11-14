# First detection of PSR B1259-63/LS 2883 in the millimeter and submillimeter wavelengths with ALMA

`2019PASJ...71L...3F` | Publications of the Astronomical Society of Japan 2019 | first author: Fujita, Yutaka | arXiv: 1904.08429 | DOI: 10.1093/pasj/psz085

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Does the pulsar-Be star binary PSR B1259-63/LS 2883 emit at mm/submm wavelengths after periastron, and what do the fluxes imply for synchrotron emission, magnetic field and circumstellar disk emission?  
  > "We report Atacama Large Millimeter/submillimeter Array (ALMA) observations of the binary system containing the pulsar PSR B1259–63 orbiting around a Be star LS 2883 after the 2017 periastron passage." (abstract)
- Target **PSR B1259-63/LS 2883**: coordinates _not stated_; z/distance 2.6 kpc  
  > "The distance to the binary is inferred to be 2.6 kpc (cite: 2018MNRAS.479.4849M)." (Introduction); distance from Miller-Jones et al. 2018  
  > "The distance to the binary is inferred to be 2.6 kpc (cite: 2018MNRAS.479.4849M)." (Introduction)

## Data provenance

- ALMA projects: 2017.1.01188.S
- bands: Band 3 (97 GHz) and Band 7 (343 GHz)  
  > "The data were taken with time division mode (TDM) centered at 97 GHz for Band 3 and 343 GHz for Band 7." (2.1 ALMA)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12 m antennas (42, 45, 47)  
  > "Band 7 ($\lambda=0.9\:\rm mm$) observation was carried out on 2017 November 30 with forty-seven $12\rm\: m$ antennas" (2.1 ALMA)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: about 5 minutes for each of three observations  
  > "The total on-source time is about 5 minutes for all three observations." (2.1 ALMA)
- observing dates: Band 3: 2017 Dec 2 and Dec 15; Band 7: 2017 Nov 30  
  > "ALMA Band 3 ($\lambda=3\:\rm mm$) observations were carried out on 2017 December 2 with forty-two $12\rm\: m$ antennas and December 15" (2.1 ALMA)
- pi or archival as stated: _not stated_
- Other facility **ATCA**: 94 GHz observations around the 2014 periastron (upper limits)  
  > "The observations at $3\rm\: mm$ wavelength (94 GHz) with ATCA were also carried out around and after the 2014 periastron passage of the binary." (2.2 ATCA)
- Other facility **Fermi**: GeV flare timing from literature  
  > "These activities were observed from $\sim t_{\rm p}+40$ days to $\sim t_{\rm p}+75$ days" (3 Results and Discussion)
- External data: Unpulsed ATCA radio fluxes at 1384, 2496, 4800, 8400 MHz for 2000 and 2004 periastrons  
  > "we show unpulsed (total minus pulsed) radio fluxes at 1384, 2496, 4800, and 8400 MHz obtained with ATCA at similar post-periastron days at the 2000 and 2004 periastron passages." (3 Results and Discussion) [from Johnston et al. 2005 (cite: 2005MNRAS.358.1069J)]
- External data: Predicted Be disk emission spectrum  
  > "The dashed black lines in figure [1](#fig:spec) show a prediction of the disk emission (cite: 2011MNRAS.412.1721V)." (3 Results and Discussion) [from (cite: 2011MNRAS.412.1721V)]

## Processing

### Calibration

- pipeline or manual: CASA/ALMA Pipeline, standard  
  > "The data were processed with the CASA/ALMA Pipeline (Pipeline-CASA51-P2B) in a standard manner." (2.1 ALMA)
- casa version: _not stated_
- pipeline version: Pipeline-CASA51-P2B  
  > "The data were processed with the CASA/ALMA Pipeline (Pipeline-CASA51-P2B) in a standard manner." (2.1 ALMA)
- archive products used as is: _not stated_
- flux calibrator: Amplitude scaling derived with the bandpass calibrator (J1647-5848 Band 3; J1337-1257 Band 7)  
  > "Amplitude scaling was derived with the bandpass calibrator." (2.1 ALMA)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean, all spectral windows combined per band  
  > "Images were created by combining all spectral windows in each band." (2.1 ALMA)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "Deconvolution was done using the CASA task `tclean` with the Briggs weight of robust parameter of 0.5." (2.1 ALMA)
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

### Not stated but needed to reproduce (our reading)

- Image sizes, cell sizes, masking and clean thresholds
- Image rms and beam values (table not included in text)
- Flux calibrator name and ALMA flux scale uncertainty
- Gaussian fit procedure details for flux errors
- ATCA calibrators and rms values (table not in text)
- Pitch angle alpha adopted

## Analysis recipe

1. **Measure ALMA fluxes**: Gaussian model fitting total flux density on tclean images  
  > "The flux was evaluated as the total flux density derived by a Gaussian model fitting." (2.1 ALMA)
   - software: CASA
   - assumption: Pulsed component negligible at ALMA bands  
  > "Thus, it can safely be ignored at the ALMA bands." (2.1 ALMA)
   - fitting: _not stated_
   - validation: _not stated_
2. **Constrain B field and electron cutoff**: Equate synchrotron cooling time to time since injection at disk passage (t_p+20 d) to get B and gamma  
  > "Here, we assumed that the electrons were injected when the pulsar passed through the disk around the Be star at $\sim t_{\rm p}+20$ days" (3 Results and Discussion)
   - parameter: nu = 97 GHz, T = 64 days  
  > "If we assume that $B=0.6$ G and $T=64$ days, the Lorentz factor is $\gamma=360$" (3 Results and Discussion)
   - assumption: Instantaneous injection of power-law electrons  
  > "if electrons are instantaneously injected" (3 Results and Discussion)
   - fitting: _not stated_
   - validation: _not stated_
3. **ATCA 2014 upper limits**: MIRIAD imfit Gaussian fit on Stokes I; 3 sigma upper limits from residual rms  
  > "A Gaussian fit was performed on the Stokes *I* images with the MIRIAD task `imfit`" (2.2 ATCA)
   - software: MIRIAD
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** Pipeline-CASA51-P2B: Pipeline calibration and tclean imaging  
  > "The data were processed with the CASA/ALMA Pipeline (Pipeline-CASA51-P2B) in a standard manner." (2.1 ALMA)
- **MIRIAD** : ATCA data reduction and imfit  
  > "The data was processed using the data reduction package MIRIAD" (2.2 ATCA)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Magnetic field upper limit | 0.6 | not stated | G | 2 | the magnetic field associated with the synchrotron emission is $B\lesssim 0.6$ G |
| Lorentz factor cutoff | 360 | not stated | dimensionless | 2 | the Lorentz factor is $\gamma=360$ |
| Disk radius matching Band 7 flux | ~30 | not stated | R_* | 0 | The Band 7 flux is consistent with the spectrum when the disk radius is $\sim 30\: R_*$. |

## Qualitative findings

- Band 3 flux unchanged between t_p+71 and +84 days, uncorrelated with GeV flares  
  > "the Band 3 flux did not indicate any time correlation with them" (abstract)

## Claim tuples

- H: mm emission is synchrotron extension of the radio spectrum | E: ALMA Band 3 fluxes compared with ATCA low-frequency spectra | R: Band 3 fluxes consistent with extrapolation | F: Synchrotron extends to 97 GHz; B≲0.6 G, gamma≳360 | **supported**
- H: Band 7 flux has a non-synchrotron origin | E: Compared Band 7 flux with extrapolation and disk model | R: Significant excess | F: Possibly circumstellar disk emission | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Low-frequency spectra for 2017 are unavailable; earlier periastron spectra used instead  
  > "Unfortunately, observational results for the 2007–2017 periastron passages at those low frequencies have not been published." (3 Results and Discussion)
- Caveat (inferred, ours): Comparison uses spectra from different periastrons
- Caveat (inferred, ours): Only single Band 7 epoch, disk interpretation weakly tested
- Caveat (inferred, ours): Flux errors and calibration uncertainty not given

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Image rms/flux table values
- Missing: Flux calibrator details
- Data volume (inferred): ~ few GB (three short TDM execution blocks)
- Score (inferred): 5/5, Short data, standard pipeline and simple imaging, but few parameters given.
- Rediscovery candidate: no, Flux table values not in text and recipe details sparse.

## Links

- Companion: Johnston et al. 2005 (cite: 2005MNRAS.358.1069J) (Earlier radio light curves and spectra)

## Checks

```json
{
 "quotes": 33,
 "quotes_ok": 33,
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
  "facts": 63,
  "stated": 26,
  "rate": 0.413
 },
 "evidence_ok": true
}
```
