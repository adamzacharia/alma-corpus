# Dust Production and Particle Acceleration in Supernova 1987A Revealed with ALMA

`2014ApJ...782L...2I` | The Astrophysical Journal Letters 2014 | first author: Indebetouw, R. | arXiv: 1312.4086 | DOI: 10.1088/2041-8205/782/1/L2

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism, astrochemistry
- Question: Where does the far-infrared/submillimeter emission of SN 1987A originate, and was the large dust mass formed in the inner ejecta; what is the spectrum of the shock-accelerated torus emission?  
  > "Resolved observations of SN$\,$1987A in the submillimeter regime are required to establish the location of the emission measured by Herschel." (Introduction)
- Target **SN 1987A**: coordinates _not stated_; z/distance 50 kpc (LMC)  
  > "Supernova (SN) 1987A in the Large Magellanic Cloud was the closest supernova explosion to Earth (50kpc)" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00273.S
- bands: Bands 3, 6, 7, 9 (2.8 mm, 1.4 mm, 870 um, 450 um)  
  > "Bands 3,6,7, and 9 (2.8$\,$mm, 1.4$\,$mm, 870$\,$$\mu$m, and 450$\,$$\mu$m) were observed in approximately chronological order." (Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: ~20 m to ~400 m, ~20 antennas  
  > "SN$\,$1987A was observed during 2012 multiple times with $\sim$20 antennas in configurations containing baselines between $\sim$20$\,$m and $\sim$400$\,$m." (Observations)
- angular resolution: 1.3'' (2.8 mm), 0.7'' (1.4 mm), 0.5'' (870 um), 0.3'' (450 um)  
  > "| torus | 345 | 870 $\mu$m | 10$\pm$1.5 | 2012 | ALMA | 0.5$''$ | this |" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2012: Band 3 Apr; Band 6 Apr, Jul, Aug; Band 7 Jul, Aug; Band 9 Aug, Nov  
  > "Band 7: A002/X45e2af/X458 (14 Jul), A002/X4ae797/X776 (24 Aug)" (Observations)
- pi or archival as stated: PI Indebetouw, project 2011.0.00273.S  
  > "ADS/JAO.ALMA#2011.0.00273.S (PI Indebetouw)" (Acknowledgements)
- Other facility **ATCA**: 6.8 mm clean model used as torus template; 8.3, 6.8, 3.2 mm torus fluxes  
  > "The torus was represented with the clean model (collection of point sources or clean components) from deconvolving the ATCA 6.8$\,$mm image." (Results)
- Other facility **Herschel**: 100-350 um photometry used in SED fit  
  > "The ALMA and Herschel photometry can be fit with 0.23$\pm$0.05$\,$M$_\odot$ of amorphous carbon dust at 26$\pm$3$\,$K (Fig. 3)." (Discussion)
- External data: ATCA/Herschel/APEX flux densities in Table 1 (8.3 mm, 6.8 mm, 3.2 mm, 100-350 um)  
  > "| torus | 44 | 6.8 mm | 40$\pm$2 | 2011 | ATCA | 0.3$''$ | (cite: zanardo13) |" (Table 1) [from potter09; zanardo13; laki-atca; matsuura11; laki-saboca]
- External data: Amorphous carbon opacity kappa=10 and 3 cm2/g at 450 and 870 um  
  > "We use amorphous carbon opacity $\kappa$=10 and 3$\,$cm$^2$g$^{-1}$ at 450 and 870$\,$$\mu$m, respectively (cite: rouleau91)." (Discussion) [from (cite: rouleau91)]

## Processing

### Calibration

- pipeline or manual: Each dataset calibrated individually with CASA  
  > "Each dataset was calibrated individually with Common Astronomy Software Applications (CASA; [casa.nrao.edu](casa.nrao.edu))." (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: clean, all data per band combined  
  > "All data in a given wavelength band were then combined for imaging and deconvolution with the “clean” algorithm." (Observations)
- deconvolver: _not stated_
- weighting robust: Briggs weighting; robust values given in figures  
  > "Briggs weighting was used with “robust” parameters and resulting Gaussian restoring beams as noted in the Figures." (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: 212.56-213.59 GHz (Band 6) and 100.07-103.91 GHz (Band 3)  
  > "Only the channels free of bright CO and SiO emission were used (212.56-213.59$\;$GHz and 100.07-103.91$\;$GHz in bands 6 and 3)." (Observations)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- Robust values and beam sizes (only in figures)
- Image size, cell size, masking, clean threshold
- CASA version
- Flux calibrators and flux scale uncertainty
- Line-free channels for Bands 7 and 9
- SED fit method, priors, and grain size
- Scaling factors used in torus/ejecta decomposition

## Analysis recipe

1. **Calibrate and image**: Calibrate each dataset in CASA, combine per band, clean with Briggs weighting on line-free channels  
  > "All data in a given wavelength band were then combined for imaging and deconvolution with the “clean” algorithm." (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Decompose torus and inner ejecta**: Image-plane subtraction of scaled clean models (ATCA 6.8 mm for torus, ALMA 450 um for ejecta), restored and residuals added back; scaling varied to minimize residuals  
  > "The amplitude scaling is varied to minimize the residuals in the subtracted image." (Results)
   - software: CASA
   - fitting: _not stated_
   - validation: Also done in Fourier plane with consistent results  
  > "The torus and ejecta were also subtracted from each other in the Fourier plane, with consistent results." (Results)
3. **Fit torus spectrum and ejecta dust SED**: Power-law fit to torus 17 mm to 870 um; amorphous carbon dust model fit to ALMA and Herschel ejecta photometry  
  > "The ALMA and Herschel photometry can be fit with 0.23$\pm$0.05$\,$M$_\odot$ of amorphous carbon dust at 26$\pm$3$\,$K (Fig. 3)." (Discussion)
   - assumption: Amorphous carbon kappa=10 and 3 cm2/g at 450 and 870 um; optically thin  
  > "The emission is optically thin at 450$\,$$\mu$m, and M$_d$ is insensitive to unresolved clumpiness" (Discussion)
   - fitting: _not stated_
   - validation: Tested carbon+silicate mix and pure silicate; compared temperature to models  
  > "the best fit using pure silicate is 4$\,$M$_\odot$ at 21$\,$K" (Discussion)

## Software

- **CASA** : Calibration and clean imaging  
  > "Each dataset was calibrated individually with Common Astronomy Software Applications (CASA; [casa.nrao.edu](casa.nrao.edu))." (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Torus spectral index | -0.8 | 0.1 | dimensionless | 3 | a power-law with a spectral index $\alpha$ = -0.8$\pm$0.1 (F$_\nu\propto\nu^\alpha$) |
| Dust mass (amorphous carbon) | 0.23 | 0.05 | Msun | 3 | 0.23$\pm$0.05$\,$M$_\odot$ of amorphous carbon dust at 26$\pm$3$\,$K |
| Dust temperature | 26 | 3 | K | 3 | 0.23$\pm$0.05$\,$M$_\odot$ of amorphous carbon dust at 26$\pm$3$\,$K |
| Ejecta 450 um flux | 50 | 15 | mJy | 2 | / ejecta / 680 / 440 $\mu$m / 50$\pm$15 / 2012 / ALMA / 0.3$''$ / this / |
| Ejecta 450 um deconvolved FWHM | 0.3 x 0.16 arcsec | 0.03 / 0.05 | arcsec | 2 | beam-deconvolved full-width at half-max (FWHM) of 0.3$\pm$0.03$''$ by 0.16$\pm$0.05$''$ |

## Qualitative findings


## Claim tuples

- H: Herschel-detected dust formed in the inner ejecta | E: Resolved ALMA images at 450 um-2.8 mm with torus subtraction | R: Ejecta emission compact, rising steeply with frequency, fit by 0.23 Msun carbon dust at 26 K | F: Large dust mass formed in the inner ejecta, not yet processed by reverse shock | **supported**
- H: Torus emission is shock synchrotron | E: Power-law fit to torus fluxes | R: alpha = -0.8±0.1, no break | F: Shock modified by accelerated particles or amplified field | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Pulsar wind nebula emission rejected for the ejecta spectrum  
  > "The spectrum of the inner ejecta rises steeply with frequency, inconsistent with PWN emission, but very well modeled by dust." (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Silicate dust mass not strongly constrained  
  > "Although these data do not strongly constrain the mass of silicate dust" (Discussion)
- Caveat (inferred, ours): Dust mass depends on assumed opacity and composition
- Caveat (inferred, ours): Fit procedure and degeneracies not documented

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: SED fitting details
- Missing: Torus scaling factors
- Data volume (inferred): ~10-50 GB raw
- Score (inferred): 3/5, Project code given but imaging and fitting details sparse.
- Rediscovery candidate: no, Recipe incomplete.

## Links

- Companion: (cite: kam13) (ALMA CO and SiO from the same dataset)

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
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 60,
  "stated": 24,
  "rate": 0.4
 },
 "evidence_ok": true
}
```
