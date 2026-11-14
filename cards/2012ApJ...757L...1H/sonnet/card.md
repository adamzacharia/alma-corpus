# The First Detection of the 232 GHz Vibrationally Excited H<SUB>2</SUB>O Maser in Orion KL with ALMA

`2012ApJ...757L...1H` | The Astrophysical Journal Letters 2012 | first author: Hirota, Tomoya | arXiv: 1208.4489 | DOI: 10.1088/2041-8205/757/1/L1

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation, astrochemistry
- Question: Is there a vibrationally excited H2O maser at 232.68670 GHz in Orion KL, blended with HCOOCH3, and where is it located?  
  > "We investigated the ALMA science verification data of Orion KL and found a spectral signature of the vibrationally excited H$_{2}$O maser line at 232.68670 GHz" (abstract)
- Target **Orion KL**: coordinates RA 05h35m14.35s, Dec -05d22m35.0s (J2000), tracking center  
  > "The tracking center position of Orion KL was set to be R. A. =05h35m14.35s and decl.=$-$05$^{\circ}$22$'$35$''$.0 (J2000)." (Observation); "in a massive SFR Orion KL at a distance of 420 pc (cite: hirota2007; kim2008)" (Introduction); z/distance 420 pc  
  > "The tracking center position of Orion KL was set to be R. A. =05h35m14.35s and decl.=$-$05$^{\circ}$22$'$35$''$.0 (J2000)." (Observation); "in a massive SFR Orion KL at a distance of 420 pc (cite: hirota2007; kim2008)" (Introduction); distance from hirota2007; kim2008  
  > "The tracking center position of Orion KL was set to be R. A. =05h35m14.35s and decl.=$-$05$^{\circ}$22$'$35$''$.0 (J2000)." (Observation); "in a massive SFR Orion KL at a distance of 420 pc (cite: hirota2007; kim2008)" (Introduction)

## Data provenance

- ALMA projects: 2011.0.00009.SV, 2011.0.00199.S
- bands: Band 6 (215-245 GHz) SV spectral line survey; Cycle 0 band 6 continuum at 240-244 and 256-260 GHz  
  > "They are part of a spectral line survey toward the Orion KL region at band 6 (215-245 GHz)." (Observation)
- frequencies and spectral setup: SV correlator resolution 488 kHz (0.60-0.65 km/s); Cycle 0 continuum resolution 15.625 MHz  
  > "The spectral resolution of the ALMA correlator was 488 kHz, corresponding to the velocity resolution of 0.60$-$0.65 km s$^{-1}$ at the observed frequency range." (Observation)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 17 to 265 kλ (22 to 345 m), 16 x 12 m antennas (SV)  
  > "The baseline lengths ranged from 17 to 265 k$\lambda$ (from 22 to 345 m) consisted of 16$\times$12 m antennas." (Observation)
- angular resolution: SV natural-weighted beam 1.7"x1.4", PA 171 deg; Cycle 0 uniform-weighted 0.74"x0.56", PA 101 deg  
  > "The natural weighted beam size was 1$''$.7$\times$1$''$.4 with the position angle of 171$^{\circ}$." (Observation)
- max recoverable scale: _not stated_
- sensitivity: 0.01-0.03 Jy/beam per channel (SV); 7 mJy/beam (Cycle 0 continuum)  
  > "The resultant typical rms (root-mean-square) noise level is 0.01$-$0.03 Jy beam$^{-1}$ for each channel map." (Observation)
- time on source: about 20 min per setting (SV); 30 s (Cycle 0)  
  > "net on-source time for each setting was about 20 minutes" (Observation)
- observing dates: SV 2012 January 20; Cycle 0 2012 April 08  
  > "The observation was done in the extended configuration on 2012 April 08 with 17$\times$12 m antennas." (Observation)
- pi or archival as stated: Public ALMA SV data  
  > "We employed the public data obtained with the ALMA science verification (SV) on 2012 January 20." (Observation)
- Line: H2O (v2=1) 5(5,0)-6(4,3) (232.68670 GHz)
- Line: HCOOCH3 (vt=1) 19(10,10)-18(10,9) E (232.68393 GHz)
- Line: HCOOCH3 (vt=1) 19(8,11)-18(8,10) E (232.73862 GHz)
- External data: 22 GHz H2O shell maser spectrum compared with the 232 GHz feature  
  > "appears to be analogous to the 22 GHz shell masers (cite: gaume1998)" (Results) [from (cite: gaume1998)]
- External data: 43 GHz SiO (v=1) maser spectrum  
  > "the 43 GHz SiO ($v$=1) masers (cite: kim2008)" (Results) [from (cite: kim2008)]
- External data: Line frequencies from Splatalogue (JPL, CDMS, Lovas/NIST)  
  > "Splatalogue[^1], which is a compilation of the JPL, CDMS, and Lovas/NIST catalogs (cite: pickett1998; muller2005; lovas2004)" (Results) [from (cite: pickett1998; muller2005; lovas2004)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Calibrated SV data used  
  > "We made synthesis imaging with the calibrated data for selected observing frequency ranges by using the Common Astronomy Software Applications (CASA) package." (Observation)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Natural weighting (SV line); uniform weighting (Cycle 0 continuum)  
  > "The uniform-weighted synthesized beam size was 0$''$.74$\times$0$''$.56 at a position angle of 101$^{\circ}$." (Observation)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Line emission subtracted from visibilities for Cycle 0 continuum; effective bandwidth about half  
  > "The line emissions were subtracted from the visibility data and effective bandwidth was almost half of the observed frequency range." (Observation)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Further details of Cycle 0 continuum data deferred to a forthcoming paper  
  > "Further details will be published in the forthcoming paper (T. Hirota et al., in preparation)." (Observation) [from T. Hirota et al., in preparation]

### Not stated but needed to reproduce (our reading)

- CASA version and task parameters (cell, image size, deconvolution, masking)
- Which SV spectral settings/execution blocks and calibration products were used
- Continuum subtraction for SV data
- Aperture/position used for spectra at Source I (2x2 arcsec stated only in Discussion)
- Velocity-integration ranges for moment maps
- Initial guesses for the Gaussian fit

## Analysis recipe

1. **Image the blended and pure HCOOCH3 features**: Synthesis imaging of calibrated SV data around 232.68 and 232.74 GHz  
  > "Then we made synthesis images of the spectral feature of the 232.68393 GHz HCOOCH$_{3}$ line and/or the 232.68670 GHz H$_{2}$O line" (Results)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared with five other unblended HCOOCH3 lines, none peaking at Source I  
  > "we found that none of them shows a significant peak at the Source I position." (Results)
2. **Isolate H2O emission by map subtraction**: Subtract pure HCOOCH3 map from blended map; residual concentrated at Source I  
  > "By subtracting the *pure* HCOOCH$_{3}$ map from the *blended* HCOOCH$_{3}$/H$_{2}$O map, the residual emission component is clearly concentrated at the Source I position" (Results)
   - software: CASA
   - assumption: Pure line has similar frequency, lower-state energy and expected intensity to the blended HCOOCH3 line  
  > "having a similar frequency, lower state energy, and expected intensity" (Results)
   - fitting: _not stated_
   - validation: _not stated_
3. **Extract spectra and fit peaks**: Channel maps and spectra at selected positions; two-component Gaussian fit to Source I spectrum  
  > "Their peak flux densities are derived by the two-component Gaussian fitting to be 0.28$\pm$0.02 Jy and 0.43$\pm$0.02 Jy" (Results)
   - software: CASA
   - fitting: Two-component Gaussian  
  > "Their peak flux densities are derived by the two-component Gaussian fitting to be 0.28$\pm$0.02 Jy and 0.43$\pm$0.02 Jy at the velocity of $-$2.1$\pm$0.6 km s$^{-1}$ and 13.3$\pm$0.4 km s$^{-1}$" (Results)
   - validation: Compared with 22 GHz H2O and 43 GHz SiO maser spectra  
  > "One can see a common structure showing double-peaks at almost the same velocities and velocity ranges." (Results)
4. **Estimate brightness temperature**: Peak 0.43 Jy in 2x2 arcsec aperture gives 2.4 K; diluted to 0.01 K in a 30 arcsec single-dish beam  
  > "It corresponds to the brightness temperature of 2.4 K." (Discussion)
   - assumption: Emitting region as compact as the aperture  
  > "If this emitting region is as compact as this aperture size" (Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Synthesis imaging of SV and Cycle 0 data  
  > "The synthesis imaging was done with the CASA software package." (Observation)
- **Splatalogue** : Line identification  
  > "We checked the database of molecular lines, Splatalogue[^1]" (Results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Peak flux of blue component | 0.28 | 0.02 | Jy | 3 | 0.28$\pm$0.02 Jy and 0.43$\pm$0.02 Jy at the velocity of $-$2.1$\pm$0.6 km s$^{-1}$ and 13.3$\pm$0.4 km s$^{-1}$ |
| Peak flux of red component | 0.43 | 0.02 | Jy | 3 | 0.28$\pm$0.02 Jy and 0.43$\pm$0.02 Jy at the velocity of $-$2.1$\pm$0.6 km s$^{-1}$ and 13.3$\pm$0.4 km s$^{-1}$ |
| Peak velocities | -2.1 and 13.3 | 0.6 and 0.4 | km/s | 3 | at the velocity of $-$2.1$\pm$0.6 km s$^{-1}$ and 13.3$\pm$0.4 km s$^{-1}$ |
| Brightness temperature (2x2 arcsec) | 2.4 | not stated | K | 4 | It corresponds to the brightness temperature of 2.4 K. |
| Compact Ridge integrated intensity, blended and pure | 3.5 and 4.9 | not stated | Jy/beam km/s | 1 | 3.5 Jy beam$^{-1}$ km s$^{-1}$ and 4.9 Jy beam$^{-1}$ km s$^{-1}$ |

## Qualitative findings

- The 232 GHz H2O maser emission is concentrated at Source I and is unresolved at 1.7x1.4 arcsec resolution.  
  > "the distribution of the 232 GHz H$_{2}$O maser features could not be resolved with the ALMA SV data" (Discussion)

## Claim tuples

- H: The 232.68670 GHz vibrationally excited H2O maser is present in a YSO | E: Compared blended and pure HCOOCH3 maps and spectra toward Source I | R: Excess compact emission at Source I with double-peaked spectrum from -10 to 20 km/s | F: First detection of the 232 GHz vibrationally excited H2O maser in star-forming regions | **supported**
- H: The 232 GHz maser is related to the 22 GHz H2O or 43 GHz SiO masers | E: Compared spectral profiles | R: Double peaks at similar velocities; closer to 22 GHz H2O masers | F: Likely associated with outflow/jet root or disk around Source I | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Blending HCOOCH3 line and other lines (13CH3CH2CN, 13CH3CCH, acetone) considered; the Source I wide-velocity emission is not explained by them  
  > "It is unlikely that other molecular lines with high velocity components contribute to this peak" (Results)
- How they decided it was enough: _not stated_
- Limitation (authors): Could not perfectly separate HCOOCH3 and H2O contributions due to insufficient spatial resolution  
  > "we could not perfectly separate the contribution from the HCOOCH$_{3}$ and the 232 GHz H$_{2}$O maser lines mainly due to the insufficient spatial resolution" (Discussion)
- Caveat (inferred, ours): Identification rests on the assumption that the pure HCOOCH3 line predicts the blended line's thermal emission
- Caveat (inferred, ours): Flux-scale uncertainty not given
- Caveat (inferred, ours): No LTE or non-LTE modelling to confirm maser nature

## Reproducibility

- Data public (paper): Public SV data  
  > "We employed the public data obtained with the ALMA science verification (SV) on 2012 January 20." (Observation)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: Exact spectral windows and extraction apertures
- Missing: Gaussian fitting details
- Data volume (inferred): Tens of GB (SV Orion KL band 6 line survey)
- Score (inferred): 5/5, Public data and a simple method, but imaging and extraction parameters are missing.
- Rediscovery candidate: yes, The data are public and the main results are numeric (Gaussian peaks), though imaging settings are not given.

## Links

- Companion: T. Hirota et al., in preparation (Further details of the Cycle 0 continuum data)
- Related: ALMA Science Verification Orion KL spectral line survey

## Checks

```json
{
 "quotes": 50,
 "quotes_ok": 50,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 34,
  "rate": 0.515
 },
 "evidence_ok": true
}
```
