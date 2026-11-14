# Linking interstellar and cometary O<SUB>2</SUB>: a deep search for <SUP>16</SUP>O<SUP>18</SUP>O in the solar-type protostar IRAS 16293-2422

`2018A&A...618A..11T` | Astronomy and Astrophysics 2018 | first author: Taquet, V. | arXiv: 1805.12492 | DOI: 10.1051/0004-6361/201833175

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry, solar_system
- Question: Is gaseous 16O18O (hence O2) detectable in the warm gas around IRAS16293 B, and how does the O2 abundance compare with comet 67P/C-G?  
  > "in order to compare the O$_2$ abundance between IRAS16293 and comet 67P/C-G." (abstract)
- Target **IRAS 16293-2422 (source B)**: coordinates pointing 16:32:22.72, -24:28:34.3 (J2000)  
  > "IRAS16293, located at 141 pc, has a total luminosity of 21 $L_{\odot}$ and a total envelope mass of 2 $M_{\odot}$" (2 Observations and data reduction); "IRAS 16293 was observed with one pointing centered on $\alpha_{\rm J2000}$ = 16:32:22.72, $\delta_{\rm J2000}$ = -24:28:34.3 located between sources A and B." (2 Observations and data reduction); z/distance 141 pc  
  > "IRAS16293, located at 141 pc, has a total luminosity of 21 $L_{\odot}$ and a total envelope mass of 2 $M_{\odot}$" (2 Observations and data reduction); "IRAS 16293 was observed with one pointing centered on $\alpha_{\rm J2000}$ = 16:32:22.72, $\delta_{\rm J2000}$ = -24:28:34.3 located between sources A and B." (2 Observations and data reduction); distance from cite: Jorgensen2005; Lombardi2008; OrtizLeon2017; Dzib2018  
  > "IRAS16293, located at 141 pc, has a total luminosity of 21 $L_{\odot}$ and a total envelope mass of 2 $M_{\odot}$" (2 Observations and data reduction); "IRAS 16293 was observed with one pointing centered on $\alpha_{\rm J2000}$ = 16:32:22.72, $\delta_{\rm J2000}$ = -24:28:34.3 located between sources A and B." (2 Observations and data reduction)

## Data provenance

- ALMA projects: 2016.1.01150.S
- bands: Band 6  
  > "in dual-polarization mode in Band 6." (2 Observations and data reduction)
- frequencies and spectral setup: 4 spectral windows, 468.5 MHz each, 122 kHz (0.156 km/s) resolution: 233.712-234.180, 234.918-235.385, 235.908-236.379, 236.368-236.841 GHz  
  > "Four spectral windows were observed each with a bandwidth of 468.500 MHz and a spectral resolution of 122 kHz or 0.156 km s$^{-1}$" (2 Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: 12m main array, 39-40 antennas  
  > "39-40 antennas of the main array were used, with baselines ranging from 15.1 to 1062.5 m." (2 Observations and data reduction)
- configurations: _not stated_
- baselines: 15.1 to 1062.5 m  
  > "with baselines ranging from 15.1 to 1062.5 m." (2 Observations and data reduction)
- angular resolution: 0.5 arcsec synthesized beam (matched to PILS)  
  > "the synthesized beam has been defined to 0.5$''$ to match the beam size of the PILS data." (2 Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: 1.2-1.4 mJy/beam/channel (0.47-0.55 mJy/beam km/s)  
  > "rms sensitivity of 1.2 - 1.4 mJy beam$^{-1}$ channel$^{-1}$ or 0.47 - 0.55 mJy beam$^{-1}$ km s$^{-1}$" (2 Observations and data reduction)
- time on source: _not stated_
- observing dates: 2016 Nov 10, 20, 22, 26 (four executions)  
  > "four execution on 2016 November 10, 20, 22, and 26" (2 Observations and data reduction)
- pi or archival as stated: Cycle 4, PI Taquet  
  > "during Cycle 4, under program 2016.1.01150.S (PI: Taquet)" (2 Observations and data reduction)
- Line: 16O18O 2_1-0_1 (233.94610 GHz)
- Line: HO2 4_{1,4,9/2,5}-5_{0,5,11/2,6} (strongest of five) (236.28092 GHz)
- Line: H2O2 4_{2,3}-5_{1,5} (235.95594 GHz)
- External data: N(CH3OH) = 2e19 and 1e19 cm-2 toward western half-beam and full-beam positions (from CH3 18OH)  
  > "giving $N$(CH$_3$OH) $= 2 \times 10^{19}$ and $1 \times 10^{19}$ cm$^{-2}$ towards the western half-beam and full-beam offset positions of IRAS16293 B" (4 Discussion and conclusions) [from (cite: Jorgensen2016; Jorgensen2018)]
- External data: c-C2H4O column densities and Tex for synthetic spectrum  
  > "assuming the column densities and excitation temperatures derived by (cite: Lykke2017)" (3.3 Analysis of the HO2 and H2O2 transitions) [from (cite: Lykke2017)]
- External data: N(H2) > 1.2e25 cm-2  
  > "(cite: Jorgensen2016) derived a lower limit for the H$_2$ column density $N$(H$_2$) $> 1.2 \times 10^{25}$ cm$^{-2}$" (4 Discussion and conclusions) [from (cite: Jorgensen2016)]
- External data: CH3OH in 67P/C-G 0.31-0.55% relative to H2O  
  > "with an abundance of $0.31-0.55$ % relative to H$_2$O (cite: Leroy2015)" (4 Discussion and conclusions) [from (cite: Leroy2015)]
- External data: 16O18O/O2 ratio of 280  
  > "assuming a $^{16}$O$^{18}$O/O$_2$ abundance ratio of 280" (3.2 Analysis of the 16O18O transition) [from (cite: Wilson1994)]

## Processing

### Calibration

- pipeline or manual: calibrated with CASA; details not given  
  > "The data were calibrated with the CASA software (cite: McMullin2007)." (2 Observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1527-2422 (executions 1-3), J1517-2422 (execution 4)  
  > "the flux calibrators were J1527-2422 (executions 1 to 3) and J1517-2422 (execution 4)" (2 Observations and data reduction)
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
- continuum subtraction: Per-pixel two-step Gaussian fit to the spectrum distribution; centroid of second Gaussian taken as continuum  
  > "The centroid of the second Gaussian function is then considered as the continuum level for each pixel." (2 Observations and data reduction)
- line free channels: none usable; line-free channels cannot be found  
  > "it is impossible to find spectral regions with line-free channels that can be used to derive the continuum emission." (2 Observations and data reduction)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.5 arcsec  
  > "the synthesized beam has been defined to 0.5$''$ to match the beam size of the PILS data." (2 Observations and data reduction)
- final rms: 1.2-1.4 mJy/beam/channel  
  > "rms sensitivity of 1.2 - 1.4 mJy beam$^{-1}$ channel$^{-1}$" (2 Observations and data reduction)

### Inherited from earlier work

- Continuum determination method for subtraction  
  > "we follow the methodology defined in (cite: Jorgensen2016) to obtain the continuum emission maps" (2 Observations and data reduction) [from (cite: Jorgensen2016)]
- Tex = 125 K and column densities for LTE line identification  
  > "following the excitation temperature found for complex organic molecules by (cite: Jorgensen2016)" (3.2 Analysis of the 16O18O transition) [from (cite: Jorgensen2016)]
- LTE intensity methodology  
  > "The model computes the intensity following the methodology summarised in (cite: Goldsmith1999)." (3.1 Overview of the Band 6 data) [from (cite: Goldsmith1999)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration/pipeline details
- Imaging task, weighting/robust, cell and image size, and how the beam was set to 0.5 arcsec
- Flux calibrator flux densities and flux-scale uncertainty
- Self-calibration, if any
- Exact LTE code used for the upper limits
- Which PILS column densities were adopted for each species in the line-identification model
- Full residual-fit procedure details (2 sigma threshold per pixel implementation)

## Analysis recipe

1. **Continuum subtraction**: Per-pixel two-step Gaussian fit to the datacube spectrum following PILS method  
  > "First, a Gaussian function is used to fit the emission distribution towards each pixel of the datacube." (2 Observations and data reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Line identification with LTE model**: LTE model with PILS column densities and Tex; 253 spectroscopic entries from CDMS and JPL  
  > "A total number of 253 spectroscopic entries mostly using the CDMS (cite: Muller2005; Endres2016) and JPL (cite: Pickett1998) catalogues" (3.1 Overview of the Band 6 data)
   - software: CDMS, JPL catalogue
   - parameter: Vlsr = 2.7 km/s, FWHM = 1 km/s, source size 0.5 arcsec, beam filling factor 0.5  
  > "assuming a systemic velocity $V_{\rm lsr} = 2.7$ km s$^{-1}$, a linewidth $FWHM = 1$ km s$^{-1}$, and a Gaussian source distribution with a size of 0.5$''$" (3.1 Overview of the Band 6 data)
   - fitting: _not stated_
   - validation: _not stated_
3. **Subtract contaminating lines near 16O18O**: Fit two neighbouring lines with Gaussians and with the CH3NCO 234.08809 GHz line profile per pixel (varying peak and velocity) when detected above 2 sigma; examine residuals  
  > "we fitted the two transitions with the profile of the CH$_3$NCO transition by varying the intensity maximum and the intensity peak velocity when one of the transitions is detected above the 2$\sigma$ level." (3.2 Analysis of the 16O18O transition)
   - fitting: Gaussian and observed-profile fits  
  > "The residual spectra still show a weak intensity emission around $2.8 - 3.2$ km s$^{-1}$ towards the continuum peak and the two western positions both using the Gaussian and the "observed" line profiles." (Analysis of the $^{16}$O$^{18}$O transition)
   - validation: Both Gaussian and observed-profile subtractions leave weak residual at 2.8-3.2 km/s  
  > "The residual spectra still show a weak intensity emission around $2.8 - 3.2$ km s$^{-1}$" (3.2 Analysis of the 16O18O transition)
4. **O2 column density upper limit and tentative value**: 3 sigma upper limit 3σ√(FWHM δv) in LTE with Tex 125-300 K; alternatively Gaussian fit to residual  
  > "deriving the 3$\sigma$ intensity upper limits $3 \sigma \sqrt{FWHM \delta v}$ of the transition at 233.946 GHz of the residual spectrum" (3.2 Analysis of the 16O18O transition)
   - parameter: FWHM = 1.0 km/s, δv = 0.156 km/s, Tex 125-300 K  
  > "assumed to be 1.0 km s$^{-1}$, and $\delta v$ is the velocity resolution (= 0.156 km s$^{-1}$)" (3.2 Analysis of the 16O18O transition)
   - assumption: LTE; 16O18O/O2 = 280  
  > "assuming a $^{16}$O$^{18}$O/O$_2$ abundance ratio of 280" (3.2 Analysis of the 16O18O transition)
   - fitting: _not stated_
   - validation: _not stated_
5. **HO2 upper limits**: Vary LTE column density to reproduce wing at 3.0-3.6 km/s of 236.280 GHz line; check other transitions undetected  
  > "we vary the column density that reproduces best the wing between 3.0 and 3.6 km s$^{-1}$ of the observed spectrum" (3.3 Analysis of the HO2 and H2O2 transitions)
   - assumption: LTE, Tex 125-300 K  
  > "We assumed Local Thermodynamic Equilibrium (LTE) and we varied the excitation temperature $T_{\rm ex}$ between 125 K and 300 K" (Analysis of the $^{16}$O$^{18}$O transition)
   - fitting: _not stated_
   - validation: Other HO2 transitions confirmed undetected at 3σ a posteriori  
  > "We confirmed *a posteriori* that the other HO$_2$ transitions are not detected at the 3$\sigma$ limit" (3.3 Analysis of the HO2 and H2O2 transitions)
6. **Abundance ratios vs CH3OH and H2O and comparison with 67P**: Divide O2 column by N(CH3OH) and by N(H2O)=1e-4 N(H2)  
  > "resulting in a lower limit in the H$_2$O column density $N$(H$_2$O) $> 1.2 \times 10^{21}$ cm$^{-2}$." (4 Discussion and conclusions)
   - assumption: H2O ice abundance 1e-4 relative to H2, fully sublimated  
  > "H$_2$O ice has a typical abundance of $1 \times 10^{-4}$ relative to H$_2$ in molecular clouds" (4 Discussion and conclusions)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Data calibration  
  > "The data were calibrated with the CASA software (cite: McMullin2007)." (2 Observations and data reduction)
- **CDMS** : Spectroscopic catalogue for line identification  
  > "mostly using the CDMS (cite: Muller2005; Endres2016) and JPL (cite: Pickett1998) catalogues" (3.1 Overview of the Band 6 data)
- **JPL catalogue** : Spectroscopic catalogue for line identification  
  > "mostly using the CDMS (cite: Muller2005; Endres2016) and JPL (cite: Pickett1998) catalogues" (3.1 Overview of the Band 6 data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Lines detected above 5σ | 671 | not stated | transitions | 2 | We detect a total of 671 transitions above the 5$\sigma$ level |
| N(16O18O) upper limit | (1.5-3.2)e17 | not stated | cm-2 | 4 | We obtain an upper limit in $N$($^{16}$O$^{18}$O$) of $(1.5 - 3.2) \times 10^{17}$ cm$^{-2}$ |
| N(O2) upper limit | (4.2-9.0)e19 | not stated | cm-2 | 4 | implying an upper limit in the O$_2$ column density of $(4.2 - 9.0) \times 10^{19}$ cm$^{-2}$ |
| N(O2) if tentative detection | (9.9-21)e19 | not stated | cm-2 | 4 | giving $N$(O$_2$) $= (9.9 - 21) \times 10^{19}$ cm$^{-2}$ |
| N(HO2) upper limit | <=1.1e14 (125 K), <=2.8e14 (300 K) | not stated | cm-2 | 5 | We obtained upper limits of $N$(HO$_2$) $\leq 1.1 \times 10^{14}$ and $\leq 2.8 \times 10^{14}$ cm$^{-2}$ |
| [O2]/[CH3OH] upper limit | <=2.1-4.5 | not stated | percent | 6 | we therefore derive \[O$_2$\]/\[CH$_3$OH\] $\leq 2.1 - 4.5$. |
| [O2]/[H2O] upper limit | <3.5 | not stated | percent | 6 | \[O$_2$\]/\[H$_2$O\] $< 3.5$% |
| N(CH2OH) fitted to doublet | 3e16 | not stated | cm-2 | 3 | is best fitted with $N$(CH$_2$OH) = $3 \times 10^{16}$ cm$^{-2}$ |

## Qualitative findings

- H2O2 line at 235.955 GHz is dominated by c-C2H4O, so H2O2 cannot be constrained; HO2 not detected.  
  > "Unfortunately, the H$_2$O$_2$ rotational transition is dominated by ethylene oxide c-C$_2$H$_4$O while HO$_2$ is not detected." (abstract)
- About 70% of ~670 lines remain unidentified at 5σ.  
  > "$\sim 70$ % of the $\sim 670$ transitions remain unidentified at a 5$\sigma$ level" (3.1 Overview of the Band 6 data)

## Claim tuples

- H: 16O18O is detectable in IRAS16293 B | E: Deep ALMA Band 6 search, subtraction of two contaminating lines | R: Residual ~3σ emission offset 0.3-0.5 km/s from source velocity | F: Only tentative detection; non-detection treated as safer case | **partially**
- H: IRAS16293 has O2 abundance similar to comet 67P | E: Compare O2/CH3OH upper limits with 67P ROSINA | R: [O2]/[CH3OH] <= 2-5 vs 5-15 in 67P | F: Lower O2 abundance, possibly due to colder (16 K) precursor cloud | **partially**

## Reasoning

- Why this data: Band 6 2_1-0_1 line has higher Einstein A than the Band 7 PILS 3_2-1_1 line, so deeper constraints  
  > "this line is expected to be much weaker than the $2_1-0_1$ transition at 233.946 GHz due to its lower Einstein coefficient" (2 Observations and data reduction)
- Why this method: _not stated_
- Alternative: CH2OH doublet identification rejected since predicted Band 7 lines are not detected  
  > "are not detected with a sensitivity of 5 mJy beam km s$^{-1}$, a factor of 20 lower, negating this identification of CH$_2$OH." (3.2 Analysis of the 16O18O transition)
- How they decided it was enough: _not stated_
- Limitation (authors): Residual emission velocity-offset and low S/N; line profiles are non-Gaussian so subtraction uncertain.  
  > "Given the low signal-to-noise of the residual transition and its velocity shift with respect to the source velocity of 2.7 km s$^{-1}$" (3.2 Analysis of the 16O18O transition)
- Caveat (inferred, ours): Upper limit depends on the line-subtraction template choice (CH3NCO) and LTE assumption
- Caveat (inferred, ours): Source filling factor and optical depth effects not explored
- Caveat (inferred, ours): Water abundance based on assumed 1e-4 relative to H2

## Reproducibility

- Data public (paper): ALMA program cited in acknowledgements  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.01150.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: CASA version and calibration scripts
- Missing: Imaging parameters
- Missing: Exact residual-fit code
- Data volume (inferred): ~100-300 GB for four executions with 4 spectral windows
- Score (inferred): 3/5, Data public and approach described, but imaging and calibration details are sparse and rely on PILS papers.
- Rediscovery candidate: no, Imaging settings missing and result is largely upper limits dependent on subtle line subtraction.

## Links

- Method: (cite: Jorgensen2016) (PILS survey continuum method and column densities)
- Companion: (cite: Lykke2017) (Column densities and Tex around source B)
- Related: PILS (Protostellar Interferometric Line Survey)

## Checks

```json
{
 "quotes": 67,
 "quotes_ok": 67,
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
  "facts": 81,
  "stated": 49,
  "rate": 0.605
 },
 "evidence_ok": true
}
```
