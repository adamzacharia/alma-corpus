# GASP XXIII: A Jellyfish Galaxy as an Astrophysical Laboratory of the Baryonic Cycle

`2019ApJ...887..155P` | The Astrophysical Journal 2019 | first author: Poggianti, Bianca M. | arXiv: 1910.11622 | DOI: 10.3847/1538-4357/ab5224

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, agn_and_quasars, galaxy_clusters_and_sz
- Question: What are the physical origins of the multiwavelength (Halpha, CO, UV, radio, X-ray) emission in the tail of jellyfish galaxy JW100, and how do the gas phases and star formation relate?  
  > "The aim of this work is to shed some light on the physical mechanisms that create tails observable at different wavelengths in jellyfish galaxies" (Introduction)
- Target **JW100 (IC5337) in Abell 2626**: coordinates 23:36:25.054 +21:09:02.64 (J2000)  
  > "| JW100 | A2626 | 0.06189 | 0.05509 | $650^{+53}_{-49}$ | 23:36:25.054 | +21:09:02.64 |" (Table 1); "At the JW100 cluster redshift (z=0.05509), this yields 1$^{\prime\prime}$=1.071 kpc. The galaxy itself has a redshift z=0.06189." (Introduction); z/distance z=0.06189 (galaxy); cluster z=0.05509  
  > "| JW100 | A2626 | 0.06189 | 0.05509 | $650^{+53}_{-49}$ | 23:36:25.054 | +21:09:02.64 |" (Table 1); "At the JW100 cluster redshift (z=0.05509), this yields 1$^{\prime\prime}$=1.071 kpc. The galaxy itself has a redshift z=0.06189." (Introduction); distance from H0=70, Om=0.3, OL=0.7 cosmology  
  > "| JW100 | A2626 | 0.06189 | 0.05509 | $650^{+53}_{-49}$ | 23:36:25.054 | +21:09:02.64 |" (Table 1); "At the JW100 cluster redshift (z=0.05509), this yields 1$^{\prime\prime}$=1.071 kpc. The galaxy itself has a redshift z=0.06189." (Introduction)

## Data provenance

- ALMA projects: 2017.1.00496.S
- bands: Band 3 (~100 GHz) and Band 6 (~220 GHz); this paper uses Band 6 plus ACA  
  > "Observations in Band 3 ($\sim$100 GHz) and band 6 ($\sim$220 GHz), were taken to sample the CO(1-0) and CO(2-1) lines, respectively" (Data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: ALMA 12m plus ACA, Cycle 5  
  > "we use the Band 6 data combined with" (Data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~1 arcsec in both bands  
  > "achieving in both bands a resolution of $\sim$1 arcsec" (Data)
- max recoverable scale: 1 to 26 arcsec angular scales (Band 6 + ACA)  
  > "sampling the angular scale from 1 to 26 arcsec" (Data)
- sensitivity: rms ~0.8 mJy/beam in 20 km/s channels  
  > "an rms in 20 km/s wide channels of $\sim$0.8 mJy/beam" (Data)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (not stated)
- Line: CO J=1-0 (not stated)
- Other facility **MUSE (VLT)**: Halpha and emission-line maps, ionization classification  
  > "observed as part of the GASP programme with the MUSE spectrograph in wide-field mode on July 15 2016" (Data)
- Other facility **Chandra ACIS-S**: X-ray imaging and spectra (ObsIDs 3192, 16136)  
  > "January 2003 (ObsId: 3192, PI: C. Sarazin, 25 ks exposure time) and in October 2013 (ObsID: 16136, PI: C. Sarazin, 110 ks exposure time)" (Chandra)
- Other facility **VLA 1.4 GHz**: radio continuum map, project AG795  
  > "project code AG795, PI Gitti" (Data)
- Other facility **UVIT/ASTROSAT**: NUV imaging, N242W filter  
  > "we use NUV imaging observations taken with the N242W broad band filter" (UVIT)
- External data: Optical ionization classification (BPT diagnostics) and Halpha/SFR from MUSE  
  > "taken from (cite: Poggianti2019)" (Data) [from (cite: Poggianti2019)]
- External data: VLA 5.5 GHz maps used for spectral index limit  
  > "using the VLA maps presented in Ignesti et al. (2017, Fig. 1)" (2 Radio-continuum) [from Ignesti et al. (2017)]

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

- ALMA observations, data reduction and analysis  
  > "The details of the ALMA observations, data reduction and analysis can be found in Moretti et al. (submitted)." (Data) [from Moretti et al. (submitted)]
- VLA observations and data reduction  
  > "These observations and the data reduction are described in (cite: Gitti2013)." (Data) [from (cite: Gitti2013)]
- MUSE observations, reduction and analysis  
  > "The MUSE observations, data reduction and the methods of analysis are described in (cite: Poggianti2017)." (Data) [from (cite: Poggianti2017)]

### Not stated but needed to reproduce (our reading)

- All ALMA calibration, imaging (robust, masking, continuum subtraction), and CO moment-map settings
- ACA and 12m combination method
- CO moment map thresholds used for Fig. 7/8 classification
- Regions used for Halpha-X-ray surface brightness comparison

## Analysis recipe

1. **Compare CO(2-1), Halpha, UV spatially**: Visual comparison of CO(2-1), Halpha, NUV maps and BPT classification, assigning clumps to star-formation evolutionary stages  
  > "For the purposes of this paper, it is interesting to compare the CO emission with both the $\rm H\alpha$ emission (middle left panel) and with the regions that are powered by star formation" (Results: 5.1)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7: imaging of VLA 1.4 GHz data (not ALMA)  
  > "we produced this image with CASA (Common Astronomy Software application) v 4.7" (Data)
- **XSPEC** 12.10: Chandra spectral fitting  
  > "We performed a spectroscopic analysis of the *Chandra* data with XSPEC v 12.10" (Spectral analysis of the galaxy)
- **CIAO** 4.10: Chandra reprocessing and source detection (WAVDETECT)  
  > "reprocessed them with CIAO 4.10 and CALDB 4.8.1" (Chandra)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ICM temperature | 3.5 | 0.1 | keV | 0 | We measure a kT=$3.5\pm0.1$ keV |
| Halpha vs X-ray slope, star-forming regions | 0.87 | 0.17 | dimensionless | 0 | with $s=0.87\pm0.17$ and $s=0.44\pm0.17$ respectively |
| Halpha vs X-ray slope, [OI]-excess regions | 0.44 | 0.17 | dimensionless | 0 | with $s=0.87\pm0.17$ and $s=0.44\pm0.17$ respectively |
| ULX candidate L_X(0.3-10) | 7.8e40 | not stated | erg/s | 0 | the detected flux corresponds to $L_X (0.3-10) = 7.8 \times 10^{40} \rm \, erg \, s^{-1}$ |

## Qualitative findings

- CO, Halpha and UV mismatch on ~1 kpc scales is explained by different star-formation stages; CO clouds lie farther from the disk in the southern tail  
  > "We interpret this as a star formation sequence, in which star formation progresses from the molecular cloud phase with no stars formed yet" (Summary)

## Claim tuples

- H: Does the CO/Halpha/UV mismatch reflect star formation stages? | E: Compared CO(2-1), Halpha, NUV and BPT maps | R: Regions with CO only, CO+Halpha+UV, Halpha+UV and UV only form a spatial sequence | F: Different stages of star formation explain the small-scale mismatch | **supported**
- H: Is the X-ray tail powered by star formation or stripped halo? | E: X-ray spectral fits, SFR calibration comparison, halo stripping model | R: X-ray SFR is 4-30 times Halpha SFR; halo stripped in ~15 Myr | F: ISM heating by the ICM is the favoured origin | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Tidal interaction with the BCG disfavoured  
  > "Finally, the one-sided ionized gas tail and its direction with respect to the BCG disfavour the tidal hypothesis." (The galaxy)
- How they decided it was enough: _not stated_
- Limitation (authors): X-ray data cannot distinguish models or confirm the bow shock  
  > "the *Chandra* data can neither confirm nor deny the existence of the shock front" (Search for the bow shock)
- Caveat (inferred, ours): ALMA is used only qualitatively; no CO fluxes or masses given
- Caveat (inferred, ours): X-ray statistics are low and the models are degenerate

## Reproducibility

- Data public (paper): Chandra data from the archive; ALMA project code given; VLA project AG795  
  > "We retrieved the datasets from the *Chandra* archive" (Chandra)
- Products in archive: _not stated_
- Missing: ALMA reduction details (in Moretti et al. submitted)
- Missing: Region definitions for the Halpha-X-ray analysis
- Data volume (inferred): ~50-100 GB for ALMA plus Chandra
- Score (inferred): 2/5, ALMA is only qualitatively used and its processing is deferred to another paper.
- Rediscovery candidate: no, The ALMA recipe is not given and the main results are X-ray based.

## Links

- Method: Moretti et al. (submitted) (ALMA observations, reduction and CO analysis)
- Method: (cite: Gitti2013) (VLA data reduction)
- Companion: (cite: Poggianti2019) (MUSE ionization analysis of GASP tails)
- Related: GASP

## Checks

```json
{
 "quotes": 40,
 "quotes_ok": 40,
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
  "facts": 61,
  "stated": 26,
  "rate": 0.426
 },
 "evidence_ok": true
}
```
