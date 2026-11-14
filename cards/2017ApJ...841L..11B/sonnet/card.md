# First Millimeter Detection of the Disk around a Young, Isolated, Planetary-mass Object

`2017ApJ...841L..11B` | The Astrophysical Journal Letters 2017 | first author: Bayo, Amelia | arXiv: 1705.06378 | DOI: 10.3847/2041-8213/aa7046

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: Can the dust disk around the planetary-mass free-floating object OTS44 be detected at millimeter wavelengths, and does its dust mass follow the M_dust-M_* relation of brown dwarfs and stars?  
  > "We compare the properties of this unique disk with those recently reported around higher-mass (brown dwarfs) young objects in order to infer constraints on its mechanism of formation." (abstract)
- Target **OTS44**: coordinates _not stated_; z/distance 160 pc (Cha I)  
  > "where $F_{\nu}$ is the flux density, $d$ is the distance to Cha I (160 pc is assumed; (cite: Whittet97))" (4 Results and discussion: dust disk mass); distance from Whittet et al. 1997  
  > "where $F_{\nu}$ is the flux density, $d$ is the distance to Cha I (160 pc is assumed; (cite: Whittet97))" (4 Results and discussion: dust disk mass)

## Data provenance

- ALMA projects: 2015.1.00243.S
- bands: Band 6 (233 GHz), Cycle 3  
  > "We have obtained Band 6 (233 GHz) ALMA continuum data of this very young disk-bearing object." (abstract)
- frequencies and spectral setup: Four spectral windows at 224, 226, 240, 242 GHz, each ~1.9 GHz wide  
  > "Four spectral windows (centered at 224, 226, 240, and 242 GHz and each one with $\sim$1.9 GHz bandwidth) were defined" (3 ALMA data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.6" x 1.6" beam  
  > "has a beam of 1.6" $\times$ 1.6", a RMS of 9.8$\mu$Jy/beam" (3 ALMA data)
- max recoverable scale: _not stated_
- sensitivity: RMS 9.8 uJy/beam  
  > "a RMS of 9.8$\mu$Jy/beam" (3 ALMA data)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **Spitzer and Herschel**: Mid/far-IR excess and SED used previously for disk model (dust mass 0.17 Earth masses)  
  > "First evidence for a disk around OTS44 came from mid- and far-IR excess emission detected with $Spitzer$ and $Herschel$" (2 OTS44)
- Other facility **VLT/SINFONI**: Pa beta emission showing accretion  
  > "we observed OTS44 with VLT/SINFONI and detected strong, broad, and variable Pa $\beta$ emission" (2 OTS44)
- External data: OTS44 luminosity 0.0024 Lsun  
  > "assuming a luminosity of 0.0024 $L_{\odot}$; (cite: Joergens13)" (4 Results and discussion: dust disk mass) [from (cite: Joergens13)]
- External data: Literature dust masses for comparison samples (Cha I, Taurus, brown dwarfs), rescaled to common opacity  
  > "we show how our four estimates of the dust mass in the disk around OTS44 compare to literature values for stellar and substellar objects" (4 Results and discussion: dust disk mass) [from (cite: Pascucci16; vanderPlas16; Daemgen16; Testi16)]
- External data: Stellar parameters for Cha I comparison sample  
  > "we adopted the stellar parameters from (cite: Manara14; Manara16) and (cite: Manara17), for the (cite: Pascucci16) sample" (4 Results and discussion: dust disk mass) [from (cite: Manara14; Manara16; Manara17)]

## Processing

### Calibration

- pipeline or manual: Standard CASA steps (flagging, bandpass, flux, phase calibration)  
  > "The data processing was performed with CASA (cite: McMullin07), following the standard steps starting from the measurement sets" (3 ALMA data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: derived ~8%; 10% adopted  
  > "the derived flux uncertainty is $\sim$8%, but, based on the ALMA documentation, we assumed a more conservative 10% value from now on" (3 ALMA data)
- self calibration: Attempted but S/N too low  
  > "we tried to apply self-calibration to improve the extended flux recovery but the signal-to-noise ratio (S/N) of the data was not good enough" (3 ALMA data)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "The final CLEAN, primary beam corrected image (natural weighting)" (3 ALMA data)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied  
  > "The final CLEAN, primary beam corrected image (natural weighting)" (3 ALMA data)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.6" x 1.6"  
  > "has a beam of 1.6" $\times$ 1.6"" (3 ALMA data)
- final rms: 9.8 uJy/beam  
  > "a RMS of 9.8$\mu$Jy/beam" (3 ALMA data)

### Inherited from earlier work

- Dust opacity 2.3 cm2/g at 230 GHz, nu^0.4  
  > "We have adopted a $\kappa_{\nu}$ value of 2.3 cm$^2$ g$^{-1}$ at 230 GHz with a frequency dependence of $\nu^{0.4}$, the same as in (cite: Andrews13) for Taurus" (4 Results and discussion: dust disk mass) [from (cite: Andrews13); (cite: Pascucci16)]
- Dust temperature-luminosity relations  
  > "$T_{\rm dust} = 25 \times (L_*/L_{\odot})^{1/4}K$" (4 Results and discussion: dust disk mass) [from (cite: Andrews13); (cite: vanderPlas16)]

### Not stated but needed to reproduce (our reading)

- CASA version
- Image size, cell size, clean threshold, and mask
- Peak vs. aperture flux extraction method
- Observing dates, array configuration, calibrators
- Exact rescaled literature values used in Fig. 2

## Analysis recipe

1. **Calibrate and image continuum**: CASA standard calibration, then CLEAN of the four-spw broadband continuum with natural weighting and primary beam correction  
  > "The final CLEAN, primary beam corrected image (natural weighting) has a beam of 1.6" $\times$ 1.6"" (3 ALMA data)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive dust mass**: Optically thin isothermal dust mass formula M = F d^2/(kappa B(T)) for four dust temperatures  
  > "we assume that the emission is optically thin and isothermal at temperature T$_{\rm dust}$" (4 Results and discussion: dust disk mass)
   - parameter: T_dust = 20, 8.4, 7.5, 5.5 K  
  > "the “classical" 20 K, the 8.4 K obtained assuming the relationship from (cite: vanderPlas16), that of IRF (7.5 K, (cite: Draine11)), and the 5.5 K" (4 Results and discussion: dust disk mass)
   - assumption: d = 160 pc; kappa = 2.3 cm2/g at 230 GHz, nu^0.4  
  > "160 pc is assumed; (cite: Whittet97)" (4 Results and discussion: dust disk mass)
   - fitting: _not stated_
   - validation: _not stated_
3. **Compare with M_dust-M_* relation**: Plot against literature interferometric samples with consistently rescaled opacities  
  > "we recalculated the dust masses using the same absorption coefficient" (4 Results and discussion: dust disk mass)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Data calibration and imaging  
  > "The data processing was performed with CASA (cite: McMullin07)" (3 ALMA data)
- **Astropy** : Acknowledged as used in research  
  > "Astropy, a community-developed core Python package for Astronomy (cite: astropy)" (Acknowledgments)
- **APLpy** : Plotting  
  > "APLpy, an open-source plotting package for Python" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Peak flux density at 233 GHz | 0.101 | 0.01 | mJy/beam | 1 | We detected OTS44 as a point-like source with a peak flux value 0.101$\pm$0.01mJy |
| Dust mass (T=20, 8.4, 7.5, 5.5 K) | 0.07, 0.27, 0.33, 0.63 | not stated | Earth masses | 2 | The corresponding estimates for the dust mass of the disk of OTS44 are: 0.07, 0.27, 0.33, and 0.63 M$_{\oplus}$, respectively. |
| Dust temperature from van der Plas relation | 8.4 | not stated | K | 2 | which translates to a dust temperature of 8.4 K for OTS44 |

## Qualitative findings

- Disk unresolved; self-calibration and spectral index not possible due to low S/N  
  > "the S/N of the data was not good enough for this purpose" (3 ALMA data)

## Claim tuples

- H: The OTS44 disk is detectable in the millimeter | E: ALMA Band 6 continuum observation | R: Point source with peak 0.101±0.01 mJy | F: First millimeter detection of a disk around an isolated planetary-mass object | **supported**
- H: Disk dust mass follows the M_dust-M_* relation down to planetary masses | E: Dust masses for four T_dust compared with literature | R: T=5.5-8.4 K masses are compatible with the relation; 20 K falls at the lower envelope | F: Consistent with a unique log-log relation, depending on assumptions | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: T_dust of 5.5 K from Andrews13 relation and 20 K judged probably unrealistic  
  > "20 K is probably an unrealistic value for the dust temperature" (4 Results and discussion: dust disk mass)
- How they decided it was enough: _not stated_
- Limitation (authors): Mass estimates limited by poorly constrained dust properties; grain growth cannot be probed with one band  
  > "these mass estimates are severely limited by assumptions on poorly constrained parameters such as the dust properties" (Conclusions)
- Caveat (inferred, ours): Single-band, low S/N detection; dust mass depends strongly on assumed T_dust and opacity
- Caveat (inferred, ours): No uncertainty on the dust masses
- Caveat (inferred, ours): Comparison sample rescaled with a common opacity

## Reproducibility

- Data public (paper): Program 2015.1.00243.S cited; public status not stated  
  > "This Letter makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00243.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: CASA version
- Missing: Literature table values
- Data volume (inferred): ~5-20 GB
- Score (inferred): 3/5, Simple analysis and single flux measurement, but imaging details are missing.
- Rediscovery candidate: yes, Single-project continuum detection with a simple mass formula and numeric results, though imaging details are missing.

## Links

- Companion: (cite: Joergens13) (Earlier discovery of accretion and OTS44 parameters)
- Companion: (cite: Liu15) (SED radiative transfer modeling of the OTS44 disk)
- Related: Pascucci et al. 2016 ALMA Cha I survey

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
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 67,
  "stated": 33,
  "rate": 0.493
 },
 "evidence_ok": true
}
```
