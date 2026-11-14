# Physical conditions of the gas in an ALMA [C ii]-identified submillimetre  galaxy at z = 4.44.

`2013MNRAS.431L..88H` | Monthly Notices of the Royal Astronomical Society 2013 | first author: Huynh, M. T. | arXiv: 1302.3297 | DOI: 10.1093/mnrasl/slt014

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies
- Question: What are the cold gas content and PDR physical conditions of the ALMA [CII]-detected SMG ALESS65.1 at z=4.44, using ATCA CO(2-1) observations plus the ALMA [CII] detection?  
  > "In this paper we present $^{12}$CO(2–1) observations of one of the ALMA detected SMGs, ALESS J033252.26-273526.3 (hereafter ALESS65.1)." (Introduction)
- Target **ALESS65.1 (ALESS J033252.26-273526.3)**: coordinates RA(J2000) = 03 32 52.26, Dec(J2000) = -27 35 26.3  
  > "in ALESS65.1 (RA(J2000) = 03 32 52.26, Dec(J2000) = $-$27 35 26.3) (S12)" (2 Observations and Results); "4.4445 $\pm$ 0.0005 | S12" (Table 1); z/distance z = 4.4445 ± 0.0005  
  > "in ALESS65.1 (RA(J2000) = 03 32 52.26, Dec(J2000) = $-$27 35 26.3) (S12)" (2 Observations and Results); "4.4445 $\pm$ 0.0005 | S12" (Table 1); distance from [CII] redshift from S12 (Swinbank et al. 2012)  
  > "in ALESS65.1 (RA(J2000) = 03 32 52.26, Dec(J2000) = $-$27 35 26.3) (S12)" (2 Observations and Results); "4.4445 $\pm$ 0.0005 | S12" (Table 1)

## Data provenance

- ALMA projects: _none stated_
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (230.538 GHz)
- Line: [CII] 2P3/2-2P1/2 (157.74 micron (rest wavelength))
- Other facility **ATCA (CABB, 7mm)**: 12CO(2-1) observations at 42.3 GHz, ~20 hr on source, H75 configuration, 9-12 Aug 2012  
  > "was observed over a period of four consecutive nights, 9 – 12 August 2012, with the Australia Telescope Compact Array (ATCA), using the Compact Array Broadband Backend (CABB)." (2 Observations and Results)
- Other facility **Chandra 250ks**: X-ray non-detection constraining AGN  
  > "ALESS65.1 is not detected in the 250ks *Chandra* X-Ray observations of this region (cite: lehmer2005)" (3 Discussion)
- External data: [CII] redshift, intensity, FWHM (470 km/s), L[CII], LFIR, LIR, stellar mass, dynamical mass, [CII] size  
  > "FWHM$_{\rm [CII]}$ | 470 $\pm$ 35 km s$^{-1}$ | S12" (Table 1) [from Swinbank et al. 2012 (cite: swinbank2012)]
- External data: PDR model curves  
  > "solar metallically PDR model curves (cite: kaufman1999)" (3 Discussion) [from (cite: kaufman1999)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Uranus (MIRIAD model)  
  > "Flux density calibration was performed on Uranus at the beginning of the nights" (2 Observations and Results)
- flux scale uncertainty: 30%  
  > "The uncertainty in the flux density calibration using the standard MIRIAD model of Uranus is estimated to be 30% (cite: emonts2011)." (2 Observations and Results)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "The synthesized beam from natural weighting is 14.0 $\times$ 9.9 arcsec." (2 Observations and Results)
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
- final beam: 14.0 x 9.9 arcsec  
  > "The synthesized beam from natural weighting is 14.0 $\times$ 9.9 arcsec." (2 Observations and Results)
- final rms: 11 μJy/beam continuum; 0.11 and 0.08 mJy/beam in 100 and 200 km/s channels  
  > "The spectra at the source position in the 100 and 200 km s$^{-1}$ binned cubes (Figure 1) have an rms of 0.11 and 0.08 mJy beam$^{-1}$, respectively." (2 Observations and Results)

### Inherited from earlier work

- Bandpass calibration scans at start, middle and end of each night  
  > "so, following (cite: emonts2011), a bandpass calibration scan was acquired at the beginning, middle and end of each 8 hour night." (2 Observations and Results) [from (cite: emonts2011)]
- AGN contribution to FIR via multicomponent fit method  
  > "following the method described by (cite: seymour2012)" (3 Discussion) [from (cite: seymour2012)]
- Size scaling from M82 using Wolfire et al. laws  
  > "Following Stacey et al. (2010), we scale up from M82 using two laws from (cite: wolfire1990) to constrain the size" (3 Discussion) [from Stacey et al. (2010)]

### Not stated but needed to reproduce (our reading)

- Calibrator/flagging details and MIRIAD tasks and parameters
- Exact [CII]/FIR values used in PDR diagram and how L_FIR derived
- Details of Decompir fit
- ALMA data processing, taken from S12

## Analysis recipe

1. **Search for CO(2-1) and set flux limit**: Calibrate and image with MIRIAD; bin to 50/100/200 km/s; flag noise spike; 3 sigma limit assuming FWHM = 470 km/s  
  > "Assuming a line FWHM identical to the \[CII\] emission line (470 km s$^{-1}$, S12) and adopting a 3$\sigma$ limit" (2 Observations and Results)
   - software: MIRIAD, KARMA
   - fitting: _not stated_
   - validation: Noise spike rejected as present in one channel only and one night only  
  > "It was deemed a noise spike because it is only present in one channel in all three binned images" (2 Observations and Results)
2. **Derive gas mass and depletion time**: L'CO via Solomon & Vanden Bout; thermalised; alpha=0.8; SFR from LIR (Kennicutt 1998)  
  > "a CO-to-H$_2$ conversion factor $\alpha = 0.8$ ${\rm M}_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$, which is appropriate for ULIRGs" (3 Discussion)
   - assumption: L'CO(2-1)=L'CO(1-0); alpha=0.8  
  > "so $L'_{\rm CO(2-1)}$ = $L'_{\rm CO(1-0)}$" (3 Discussion)
   - fitting: _not stated_
   - validation: _not stated_
3. **Constrain G0 and n with PDR models**: Compare L[CII]/LFIR vs LCO/LFIR with Kaufman et al. 1999 models; CO flux x2, [CII] x0.7; CO(2-1)/CO(1-0)=7.2  
  > "we multiply the $^{12}$CO(2–1) flux by a factor of two to account for the line being optically thick" (3 Discussion)
   - fitting: _not stated_
   - validation: AGN contribution to FIR ≲10% from Decompir fit; X-ray non-detection  
  > "find the AGN contribution to the total FIR luminosity is $\lesssim$10%" (3 Discussion)

## Software

- **MIRIAD** : calibration, mapping, analysis of ATCA data  
  > "The data were calibrated, mapped and analysed using the standard MIRIAD (cite: sault1999) and KARMA (cite: gooch1996) packages." (2 Observations and Results)
- **KARMA** : visualisation and analysis of ATCA data  
  > "The data were calibrated, mapped and analysed using the standard MIRIAD (cite: sault1999) and KARMA (cite: gooch1996) packages." (2 Observations and Results)
- **Decompir** : AGN+starburst fit to FIR SED  
  > "using `Decompir` software (cite: mullaney2011)" (3 Discussion)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(2-1) line intensity | <0.11 | 3 sigma limit | Jy km/s | 1 | $< 0.11$ Jy km s$^{-1}$ (3$\sigma$) |
| L'CO(2-1) | <2.2e10 | not stated | K km/s pc^2 | 2 | $L'_{\rm CO(2-1)}$ $<$ 2.2 $\times$ $10^{10}$ K km s$^{-1}$ pc$^2$ |
| Cold gas mass | <1.7e10 | 3 sigma | Msun | 2 | $M_{\rm gas} < 1.7 \times 10^{10}$ ${\rm M}_\odot$ |
| Gas depletion timescale | <50 | not stated | Myr | 2 | $\tau = M_{\rm gas} /{\rm SFR} < 50$ Myr |
| G0 | ~1e3 | not stated | Habing | 3 | we find ALESS65.1 has $G_0 \sim 10^3$ and $n \lesssim10^5$ cm$^{-3}$ |
| L[CII]/LFIR | 2.3e-3 | not stated | dimensionless | 3 | $L_{\rm [CII]}/L_{\rm FIR} = 2.3 \times 10^{-3}$ |
| L[CII]/LCO | >~2700 | not stated | dimensionless | 3 | ALESS65.1 has $L_{\rm [CII]}/L_{\rm CO} \gtrsim 2700$ |
| Emission region diameter | 1.1–2.1 | not stated | kpc | 3 | yields a diameter of 1.1 – 2.1 kpc |

## Qualitative findings


## Claim tuples

- H: Does ALESS65.1 have a gas reservoir and depletion time like other z>4 SMGs? | E: ATCA 20 hr CO(2-1) search | R: No detection; Mgas<1.7e10 Msun, tau<50 Myr | F: Consistent with z>4 SMGs being progenitors of red-and-dead galaxies | **supported**
- H: What explains high [CII]/FIR? | E: PDR diagnostic diagram | R: G0≳1e3, [CII]/CO≳2700 | F: Extended star formation more likely than low metallicity | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Single-phase ISM assumed; atomic mass very uncertain  
  > "We have assumed a single-phase ISM in this work." (3 Discussion)
- Caveat (inferred, ours): Alpha=0.8 and thermalisation assumptions drive the limit
- Caveat (inferred, ours): Upper limit only; no CO detection
- Caveat (inferred, ours): Beam is large compared to source

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ATCA data access details
- Missing: MIRIAD processing parameters
- Data volume (inferred): ATCA ~ tens of GB; ALMA [CII] not reprocessed
- Score (inferred): 3/5, ATCA analysis is simple but uses little-specified steps; ALMA data are only taken from S12.
- Rediscovery candidate: no, Main new data are ATCA, with an upper limit; ALMA is minor.

## Links

- Companion: Swinbank et al. 2012 (cite: swinbank2012) (ALMA [CII] detection of ALESS65.1)
- Related: ALESS
- Related: LESS

## Checks

```json
{
 "quotes": 43,
 "quotes_ok": 43,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00294.S"
 ],
 "codes_printed_but_missing": [
  "2011.1.00294.S"
 ],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 64,
  "stated": 26,
  "rate": 0.406
 },
 "evidence_ok": true
}
```
