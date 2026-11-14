# New detections of Galactic molecular absorption systems toward ALMA calibrator sources

`2016PASJ...68....6A` | Publications of the Astronomical Society of Japan 2016 | first author: Ando, Ryo | arXiv: 1510.05004 | DOI: 10.1093/pasj/psv110

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: milky_way_ism, astrochemistry
- Question: Do ALMA calibrator spectra in the archive contain Galactic molecular absorption lines, and what do HCO/H13CO+ ratios imply about the diffuse ISM?  
  > "it is possible that ALMA has detected molecular absorption lines within the spectra of its calibrator sources, and such cases would equate to discoveries of new systems *without* any additional observation." (Introduction)
- Target **J1717-337**: coordinates _not stated_; z/distance Galactic absorption (distance not stated)  
  > "All of these are found to be Galactic in origin, based on consideration of the line velocities." (Results); distance from _not stated_
- Target **J1625-254**: coordinates _not stated_; z/distance Galactic absorption (distance not stated)  
  > "All of these are found to be Galactic in origin, based on consideration of the line velocities." (Results); distance from _not stated_
- Target **J1604-446**: coordinates _not stated_; z/distance Galactic absorption (distance not stated)  
  > "All of these are found to be Galactic in origin, based on consideration of the line velocities." (Results); distance from _not stated_
- Target **NRAO 530**: coordinates _not stated_; z/distance Galactic absorption, VLSR = 6 km/s  
  > "A single velocity component is identified, the velocity of which ($V_{\mathrm{LSR}} = 6$ km/s) is consistent with the values reported in previous studies" (Results); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00217.S, 2011.0.00259.S, 2011.0.00351.S, 2011.0.00524.S, 2011.0.00531.S, 2011.0.00733.S
- bands: Bands 3, 6 and 7  
  > "molecular absorption lines in Bands 3, 6 and 7 toward four radio-loud quasars" (abstract)
- frequencies and spectral setup: frequency resolution < 1 MHz in FDM  
  > "The data are taken at a frequency resolution of $< 1$ MHz in frequency division mode (FDM)." (Data Analysis)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: Cycle 0 data, prior to late 2014  
  > "The data are available in the ALMA archive from prior to late 2014, i.e., Cycle 0 data" (Data Analysis)
- pi or archival as stated: _not stated_
- Line: HCO 1(0,1)-0(0,0) (86.6708 GHz)
- Line: H13CO+ 1-0 (86.7543 GHz)
- Line: CO 2-1 (230.5380 GHz)
- Line: CO 3-2 (345.7960 GHz)
- External data: HCO and H13CO+ column densities toward previous HCO-absorption sightlines  
  > "compared with the values measured on the lines-of-sight of the sources toward which HCO absorption was previously detected ((cite: Liszt+14))" (Discussion) [from (cite: Liszt+14)]
- External data: PDR column densities for comparison  
  > "along with the values in several PDRs ((cite: Schilke+01); (cite: Gerin+09))" (Discussion) [from (cite: Schilke+01); (cite: Gerin+09)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Neptune  
  > "The spectrum of the flux calibrator (the Neptune in this case)" (Data Analysis)
- flux scale uncertainty: ~10%  
  > "free from flux calibration uncertainty ($\sim 10$%)" (Data Analysis)
- self calibration: _not stated_

### Imaging

- task: CASA CLEAN  
  > "using the Common Astronomy Software Applications (CASA) package `CLEAN` task" (Data Analysis)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "with Briggs weighting (with a `robust` parameter of 0.5)" (Data Analysis)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: IMCONTSUB in image plane, then IMMATH division  
  > "The continuum spectrum is subtracted from that of the detected absorption lines using the `IMCONTSUB` task" (Data Analysis)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Optical depth and column density equations  
  > "calculated using equations (1) and (2) of Greaves and Nyman" (Data Analysis) [from Greaves and Nyman 1996 (cite: GN96)]
- Tex = 2.73 K assumption (CMB equilibrium)  
  > "as has been widely assumed in the previous studies on Galactic molecular absorption systems" (Data Analysis) [from (cite: GN96); (cite: LL98); (cite: Liszt+14)]

### Not stated but needed to reproduce (our reading)

- Image size, cell size, channel width and velocity resolution of cubes
- Clean mask and threshold
- Continuum-channel selection for IMCONTSUB
- Which spectral windows/EBs per source and CASA version
- Beam size / extraction aperture for spectra
- Fitting method for Gaussians and error budget details
- Coordinates of targets

## Analysis recipe

1. **select calibrators**: Select 36 archive calibrators by Cycle 0 availability, >0.2 Jy continuum, <1 MHz resolution FDM  
  > "We select 36 calibrator sources from the whole sky, which fulfill the following criteria" (Data Analysis)
   - fitting: _not stated_
   - validation: _not stated_
2. **make cubes and re-do bandpass**: CLEAN cubes from calibrated visibilities; flag and interpolate absorbing bandpass channels, reapply bandpass  
  > "The bandpass-calibrator frequency channels showing absorption lines (typical widths of $< 5$ km s$^{-1}$ or $< 2.5$ MHz) are flagged and linearly interpolated using nearby channels" (Data Analysis)
   - software: CASA
   - parameter: robust = 0.5  
  > "with Briggs weighting (with a `robust` parameter of 0.5)" (Data Analysis)
   - fitting: _not stated_
   - validation: Neptune spectrum with interpolated bandpass shows no artificial features at line frequencies  
  > "does not exhibit any artificial features at the frequencies where the lines are found" (Data Analysis)
3. **normalize and fit lines**: Continuum subtraction, divide by continuum, Gaussian fit for velocity, FWHM, depth  
  > "The normalized line spectrum is then Gaussian fitted to allow measurement of the central velocity, full width at half maximum (FWHM), and the absorption line depth" (Data Analysis)
   - software: CASA IMCONTSUB, CASA IMMATH
   - fitting: Gaussian fit  
  > "The normalized line spectrum is then Gaussian fitted" (Data Analysis)
   - validation: image-plane and uv-plane continuum subtraction give same result  
  > "we have confirmed that the same continuum subtraction is conducted in both the image and $uv$ planes" (Data Analysis)
4. **derive optical depths and column densities**: tau from line/continuum ratio; N from Greaves & Nyman formula with Gaussian integrated tau  
  > "the integrated optical depths are calculated as" (Derivation of molecule optical depths and column densities)
   - assumption: Tex = 2.73 K  
  > "assuming that the excitation temperatures ($T_{\mathrm{ex}}$) of the detected molecules are 2.73 K" (Data Analysis)
   - fitting: _not stated_
   - validation: Tex = 10 K changes abundance ratios by no more than 10%  
  > "this does not change the abundance ratios no more than 10%" (Data Analysis)
5. **compare N(HCO)/N(H13CO+) with PDRs**: Compare ratios with literature PDR and diffuse sightline values  
  > "which are comparable to the values for well-known PDRs" (Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : cube creation (CLEAN), IMCONTSUB, IMMATH  
  > "using the Common Astronomy Software Applications (CASA) package `CLEAN` task" (Data Analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| N(HCO)/N(H13CO+) toward J1717-337 | 24 | ±4 | dimensionless | 4 | are $24 \pm 4$ and $23 \pm 7$, respectively |
| N(HCO)/N(H13CO+) toward NRAO530 | 23 | ±7 | dimensionless | 4 | are $24 \pm 4$ and $23 \pm 7$, respectively |
| CO Tex toward J1604-446 (rotation diagram) | 6.2 | not stated | K | 4 | the $T_{\mathrm{ex}}$ of the main CO component is calculated to be 6.2 K |
| CO total column density J1604-446 main component | 1.1e16 | not stated | cm^-2 | 4 | the total column density and $T_{\mathrm{ex}}$ of the main CO component are determined to be $1.1 \times 10^{16}$ cm$^{-2}$ and 6.2 K |

## Qualitative findings

- Three of four absorption systems are new; all Galactic; HCO detected toward J1717-337 and NRAO530  
  > "the other three systems, toward J1717$-$337, J1625$-$254, and J1604$-$446 are newly detected in this work" (Results)

## Claim tuples

- H: ALMA calibrators contain undiscovered molecular absorption systems | E: Searched 36 Cycle 0 calibrators for >3 sigma absorption | R: Four sources show absorption, three new | F: Archive calibrators are useful for finding new absorption systems | **supported**
- H: Diffuse ISM toward these sources is PDR-like | E: Compare N(HCO)/N(H13CO+) with PDR values | R: Ratios 24±4 and 23±7 | F: PDR-like chemistry driven by FUV in diffuse ISM | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Tex = 2.73 K assumption caution in PDRs; CO rotation diagram assumes LTE and optically thin  
  > "this assumption should be treated with caution if the ISM in question is located in a photodissociation region" (Data Analysis)
- Caveat (inferred, ours): Tex = 2.73 K likely underestimates column densities in PDR-like gas
- Caveat (inferred, ours): No quantified uncertainty treatment for Tex
- Caveat (inferred, ours): Sightline beam vs. continuum source structure not discussed

## Reproducibility

- Data public (paper): Data from the ALMA archive  
  > "The data are available in the ALMA archive" (Data Analysis)
- Products in archive: _not stated_
- Missing: Full imaging parameters
- Missing: Spectral window and execution block lists
- Missing: Exact continuum channel choices
- Data volume (inferred): ~100 GB
- Score (inferred): 3/5, Public data and simple analysis, but imaging details and CASA version missing.
- Rediscovery candidate: yes, Public archival data, simple recipe, numeric ratios.

## Links

- Method: Greaves and Nyman 1996 (cite: GN96) (optical depth and column density formulae)
- Companion: Ando et al., in preparation (further analysis of Tex impact and J1717-337 molecules)

## Checks

```json
{
 "quotes": 49,
 "quotes_ok": 49,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 6,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00017.S",
  "2011.0.00020.S",
  "2011.0.00046.S",
  "2011.0.00061.S",
  "2011.0.00083.S",
  "2011.0.00099.S",
  "2011.0.00108.S",
  "2011.0.00121.S",
  "2011.0.00170.S",
  "2011.0.00172.S",
  "2011.0.00175.S",
  "2011.0.00208.S",
  "2011.0.00243.S",
  "2011.0.00273.S",
  "2011.0.00307.S",
  "2011.0.00471.S",
  "2011.0.00497.S",
  "2011.0.00525.S",
  "2011.0.00526.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 32,
  "rate": 0.421
 },
 "evidence_ok": true
}
```
