# Detection of a Millimeter Flare from Proxima Centauri

`2018ApJ...855L...2M` | The Astrophysical Journal Letters 2018 | first author: MacGregor, Meredith A. | arXiv: 1802.08257 | DOI: 10.3847/2041-8213/aaad6b

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: stellar_physics, debris_disks, exoplanets
- Question: Does the 1.3 mm emission from Proxima Cen require dust belts, or is it explained by stellar flaring and coronal emission?  
  > "Since the ACA observations do not show any quiescent excess emission, we conclude that there is no need to invoke the presence of a dust belt at $1-4$ AU." (abstract)
- Target **Proxima Centauri**: coordinates _not stated_; z/distance 1.3 pc  
  > "At a distance of only 1.3 pc (cite: van07), Proxima Centauri b" (Introduction); distance from van Leeuwen 2007 (cite: van07)  
  > "At a distance of only 1.3 pc (cite: van07), Proxima Centauri b" (Introduction)

## Data provenance

- ALMA projects: 2016.A.00013.S
- bands: Band 6, 233 GHz (1.3 mm)  
  > "Proxima Centauri was observed with ALMA at 233 GHz (1.3 mm) from 2017 January 21 through 2017 April 25" (Observations)
- frequencies and spectral setup: four spectral windows at 225, 227, 239, 241 GHz; 1.875 GHz each, 120 channels  
  > "The correlator was set-up to maximize continuum sensitivity with four spectral windows centered at 225, 227, 239 and 241 GHz." (Observations)
- continuum bandwidth: _not stated_
- arrays: ALMA 12-m (41 antennas) and ACA (8-11 7-m antennas)  
  > "$2\times\sim$1.3 hour scheduling blocks (SBs) using the full 12-m array (41 antennas) and $13\times\sim$1.6 hour SBs using the ACA (8–11 7-m antennas)" (Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.99"x0.87" (12-m); 7.3"x5.5" (ACA)  
  > "the beam size is $0.99\ensuremath{''}\times0.87\ensuremath{''}$" (3.1 ALMA 12-m Observations)
- max recoverable scale: _not stated_
- sensitivity: 9.5 uJy/beam (12-m), 47 uJy/beam (ACA)  
  > "with sensitivities of 9.5 and 47 $\mu$Jy beam$^{-1}$, respectively" (abstract)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archival data of PI Anglada, published in Anglada et al. 2017  
  > "We obtained the raw data from the ALMA archive" (Observations)
- External data: Photospheric flux at 1.3 mm of 74±4 uJy from SED emission model  
  > "the expected photospheric flux at 1.3 mm is $74\pm4$ $\mu$Jy" (3.1 ALMA 12-m Observations) [from Ribas et al. 2017 (cite: Ribas:2017)]
- External data: Background source counts at 1.3 mm  
  > "Deep ALMA surveys at millimeter wavelengths have placed strong constraints on the expected number of faint background sources in an image (cite: Carniani:2015)" (4.2 New Constraints on Dust Emission) [from Carniani et al. 2015 (cite: Carniani:2015)]

## Processing

### Calibration

- pipeline or manual: Calibrated with provided scripts in CASA  
  > "generated calibrated measurement sets in `CASA` (cite: Petry:2012) using the scripts provided" (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ganymede, Callisto, Titan, J1427−4206, J1517−2422  
  > "Several sources were used for both absolute flux calibration (Ganymede, Callisto, Titan, J1427−4206, and J1517−2422)" (Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean; uvmodelfit for point-source fits  
  > "All continuum images were produced using the `clean` task in `CASA`" (Observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "shows the natural weight continuum image produced by combining both ALMA 12-m array observations" (3.1 ALMA 12-m Observations)
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

- Observation description and calibration scripts from the original publication  
  > "Additional discussion of these observations can be found in (cite: ang17)." (Observations) [from Anglada et al. 2017 (cite: ang17)]
- Excess variance definition  
  > "following (cite: Nadra:1997)" (3.1 ALMA 12-m Observations) [from Nadra et al. 1997 (cite: Nadra:1997)]

### Not stated but needed to reproduce (our reading)

- CASA version
- clean cell size, image size, niter, and threshold
- uvmodelfit starting parameters
- how the spectral index and uncertainties were derived
- how flux density in the 2 s and 5 s bins was extracted
- how the number of background sources was computed from the counts

## Analysis recipe

1. **Image and fit 12-m continuum**: Natural-weight clean image and uvmodelfit point source fit to visibilities, combined and per SB/scan  
  > "Fitting a point source model to the visibilities using the `CASA` task `uvmodelfit` yields a total flux density of $101\pm9$ $\mu$Jy" (3.1 ALMA 12-m Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared with Anglada et al. 106±12 uJy  
  > "consistent with the result of $106\pm12$ $\mu$Jy reported by (cite: ang17)" (3.1 ALMA 12-m Observations)
2. **Variability, spectral index and polarization of quiescent emission**: Excess variance of per-scan fluxes; XX and YY imaged separately for |Q/I|; flux in 225+227 and 239+241 GHz windows for alpha  
  > "Combining both observations together, but imaging the XX and YY polarizations separately, yields total flux densities" (3.1 ALMA 12-m Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Find and characterize ACA flare**: Image the 13 ACA observations individually, then fit visibilities in 2 s intervals in the flare scan; alpha and |Q/I| in 5 s bins  
  > "we fit models to the visibilities in this scan in 2 second intervals using `uvmodelfit` in `CASA`" (3.2 ACA Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: No variability in calibrator flux densities at similar timescales  
  > "We do not detect any variability in the calibrator flux densities when imaged on similar timescales." (3.2 ACA Observations)
4. **Infer electron power-law index**: Optically thin gyrosynchrotron relation alpha = 1.22 - 0.9 delta  
  > "$\alpha = 1.22 - 0.9\delta$ (cite: Dulk:1985; Osten:2016)" (4.1 Nature of the Detected Stellar Flare)
   - assumption: Optically thin gyrosynchrotron emission  
  > "This spectral index may indicate that we are seeing the optically thin part of the gyrosynchrotron spectrum" (4.1 Nature of the Detected Stellar Flare)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibration, clean imaging, uvmodelfit  
  > "All continuum images were produced using the `clean` task in `CASA`" (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 12-m flux density | 101 | 9 | uJy | 1 | yields a total flux density of $101\pm9$ $\mu$Jy |
| Excess variance 12-m | 0.017 | 0.030 | dimensionless | 2 | $\sigma_\text{rms}^2=0.017\pm0.030$ |
| Quiescent spectral index | 2.58 | 2.05 | dimensionless | 2 | The resulting spectral index is $\alpha = 2.58 \pm2.05$ |
| Flare peak flux density | 100 | 4 | mJy | 3 | At peak brightness, the flux density reaches $100\pm4$ mJy |
| Flare peak luminosity | 2.04e14 | 0.15e14 | erg/s/Hz | 3 | a luminosity of $2.04\pm0.15\times10^{14}$ erg s$^{-1}$ Hz$^{-1}$ at 1.3 pc |
| Flare minimum spectral index | -1.77 | 0.45 | dimensionless | 3 | a minimum value of $\alpha = -1.77\pm0.45$ |
| Flare |Q/I| at peak | 0.19 | 0.02 | dimensionless | 3 | $/Q/I/ = 0.19\pm0.02$ |
| Electron power-law index delta | 3.32 | 0.83 | dimensionless | 4 | we can determine $\delta=3.32\pm0.83$ |

## Qualitative findings

- The ACA detection is entirely due to a ~1 minute flare, with no quiescent excess  
  > "the entirety of the 1.3 mm emission detected by the ACA results from the short duration stellar flare" (4.2 New Constraints on Dust Emission)

## Claim tuples

- H: Is the ACA 1.3 mm detection a cold dust belt at 1-4 AU? | E: Imaged ACA observations individually and fit visibilities in short time bins | R: Source appears only in one scan as a 100 mJy flare; the other 12 observations show no >3 sigma source | F: No need for the 1-4 AU belt | **supported**
- H: Does the 12-m excess require warm dust at ~0.4 AU? | E: Compared 12-m flux to photosphere and considered coronal flaring | R: 101±9 vs 74±4 uJy | F: Excess may be coronal heating from small flares, removing the need for warm dust | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Outer belt at ~30 AU not tested, but caution advised due to expected background sources and cirrus  
  > "suggest that caution should be used in over-interpreting this marginal result" (5 Conclusions)
- How they decided it was enough: _not stated_
- Limitation (authors): No polarization calibration, so |Q/I| is only a lower limit  
  > "Since there are no polarization calibration and cross products available for these observations, $|Q/I|$ provides only a lower limit" (3.1 ALMA 12-m Observations)
- Caveat (inferred, ours): Spectral index uses two narrow frequency groups, so uncertainty is large
- Caveat (inferred, ours): Short time-bin flux fits in ACA data have uncertain systematics
- Caveat (inferred, ours): Excess-flux explanation by small flares is speculative

## Reproducibility

- Data public (paper): Raw data obtained from ALMA archive  
  > "We obtained the raw data from the ALMA archive" (Observations)
- Products in archive: _not stated_
- Missing: CASA version
- Missing: imaging parameters
- Missing: uvmodelfit initial guesses and time-binning details
- Data volume (inferred): tens of GB
- Score (inferred): 3/5, Data public and approach simple, but CASA version and fit details are missing.
- Rediscovery candidate: yes, Public data, simple recipe and numeric results (flare peak, spectral index).

## Links

- Companion: Anglada et al. 2017 (cite: ang17) (Original publication of the same observations)

## Checks

```json
{
 "quotes": 41,
 "quotes_ok": 41,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 64,
  "stated": 29,
  "rate": 0.453
 },
 "evidence_ok": true
}
```
