# ALMA Observations of the Archetypal “Hot Core” That Is Not: Orion-KL

`2017ApJ...847...66O` | The Astrophysical Journal 2017 | first author: Orozco-Aguilera, M. T. | arXiv: 1708.08448 | DOI: 10.3847/1538-4357/aa88cd

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation, astrochemistry
- Question: Are there compact continuum (proto)stellar sources inside the Orion-KL hot molecular core that could heat it internally?  
  > "we carried out a search for compact and faint continuum sources (in five different continuum bands of ALMA) that are probably associated with (proto)stellar objects and with hot molecular gas within the HMC in Orion-KL." (Introduction)
- Target **Orion-KL hot molecular core (ALMA 1-3, Source I, BN)**: coordinates ALMA 1: 05 35 14.225, -05 22 28.02 (J2000); ALMA 2: 05 35 14.428, -05 22 33.56; ALMA 3: 05 35 14.802, -05 22 30.69  
  > "| ALMA 1       | 05 35 14.225    | $-$05 22 28.02" (Table 2); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.01034.S, 2012.1.00146.S, 2013.1.00048.S, 2012.1.00123.S
- bands: Bands 4, 6, 7, 8, 9 (149-658 GHz)  
  > "The observations were made in five different spectral bands (bands 3, 6, 7, 8, and 9) covering a very broad range of frequencies (149 – 658 GHz)." (abstract)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.1" – 0.3"  
  > "high angular resolution ($\sim$ 0.1$''$ – 0.3$''$)" (abstract)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2014/07/26 to 2015/09/22  
  > "The observations were carried out with ALMA between 2014 and 2015" (Observations)
- pi or archival as stated: _not stated_
- External data: NH3(12,12) hot gas peak positions (Eu=1456 K) plotted in Figure 3  
  > "the positions of the peaks of the hot molecular gas as traced by the NH$_3$(12,12) with a temperature in the upper level of 1456 K" (Results) [from (cite: god2011)]
- External data: CH3CN(12_9,11_9) hot gas peak positions (Eu=646 K)  
  > "CH$_3$CN(12$_{9}$,11$_{9}$) with a temperature in the upper level of 646 K" (Results) [from (cite: zap2011b)]

## Processing

### Calibration

- pipeline or manual: Data calibrated with CASA; quasars used for bandpass, amplitude and gain  
  > "Quasars J0529$-0519$, J0423$-$013, J0607$-$0834, and J0532$-$0307 were used to calibrate the bandpass, the amplitude and the gain fluctuations." (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Phase-only self-cal, 1-2 rounds per observation; amplitude+phase tried without improvement  
  > "We self-calibrate all images in phase. In average, we give about 1 to 2 rounds in phase for every observation." (Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: robust = 0  
  > "We used ROBUST parameter of CLEAN equal to zero in the continuum maps presented in this study." (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: All images corrected for primary beam attenuation  
  > "All the resulting ALMA images are corrected by the primary beam attenuation." (Observations)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: Band 4 0.36x0.34" (0.29x0.28" restricted), Band 6 0.21x0.17", Band 7 0.29x0.26", Band 8 0.10x0.08", Band 9 0.17x0.14"  
  > "| 8 | 2015/09/22 | 433.7 | 5624 |  200 – 3100 | 35 | $\sim$ 25 | 0.10$\times$0.08 |  $+$70 | 5.0 |" (Table 1)
- final rms: 2.5 (Band 4 full), 1.5, 4.5, 6.1, 4.6, 5.0, 34.0 mJy/beam  
  > "| 9 | 2014/08/05 | 658.5 | 7500 |  300 – 1400 | 35 | $\sim$ 5 | 0.17$\times$0.14 |  $-$42 | 34.0 |" (Table 1)

### Not stated but needed to reproduce (our reading)

- Number of CLEAN iterations, thresholds, masks, cell and image sizes
- Self-calibration solution intervals and reference data
- Flux calibrator and flux scale uncertainty
- Which spectral windows/channels were used for continuum, line-free channels
- Distance to Orion-KL
- Exact method for brightness temperature
- CASA version

## Analysis recipe

1. **Image continuum with restricted uv-range**: Constrain uv-range to remove extended emission, CLEAN with robust=0, phase self-calibration, primary beam correction  
  > "We chose the *uv-range* based on a trade off between removing as much extended emission as possible and keeping enough visibilities to obtain a good map." (Observations)
   - software: CASA
   - parameter: uv cut >150 kλ (Bands 4, 7), >200 kλ (Band 6), >300 kλ (Band 9)  
  > "baselines that are sensitive to compact emission ($>$ 200 k$\lambda$ for band 6, and $>$ 300 k$\lambda$ for band 6)" (Results)
   - fitting: _not stated_
   - validation: Flux densities with full and restricted uv-ranges are very similar  
  > "We also have compared the flux densities of the ALMA compact sources reported here with the full and restricted uv-ranges, and find that these are very similar." (Discussion and Conclusions)
2. **Measure source positions and flux densities**: Gaussian fit using the CASA viewer; sources counted if detected above 5-sigma and present in other bands  
  > "These parameters were obtained from a Gaussian fit using the viewer in CASA." (Table 2)
   - software: CASA
   - fitting: Gaussian fit  
  > "These parameters were obtained from a Gaussian fit using the viewer in CASA." (Table 2 notes)
   - validation: _not stated_
3. **Derive spectral indices and brightness temperatures**: Least-squares power-law fit of S_nu ∝ nu^alpha across bands; Tb from 658 GHz flux densities  
  > "We estimated the values of the spectral indices using the least-squares power-law technique." (Discussion and Conclusions)
   - fitting: least-squares power law  
  > "We estimated the values of the spectral indices using the least-squares power-law technique." (Discussion and Conclusions)
   - validation: Source I index 1.74 compared with literature value 1.8  
  > "The value of 1.8 for spectral index for Source I reported in (cite: tom2015) is the closest one to that found in this study" (Discussion and Conclusions)

## Software

- **CASA** : Calibration, imaging, analysis, Gaussian fits  
  > "The data were calibrated, imaged, and analyzed using the Common Astronomy Software Applications (cite: mac2007)." (Observations)
- **karma** : Additional data analysis  
  > "The data presented in this paper were also analyzed using the karma software (cite: goo1996)." (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Spectral index ALMA 1 | 1.47 | 0.15 | dimensionless | 3 | / ALMA 1       / 05 35 14.225    / $-$05 22 28.02  / 18$\pm$2   / 80$\pm$5   / 90$\pm$5   / 170$\pm$15   / –            / 1.47$\pm$0.15 / |
| Spectral index ALMA 2 | 1.48 | 0.18 | dimensionless | 3 | / ALMA 2       / 05 35 14.428    / $-$05 22 33.56  / 41$\pm$5   / 138$\pm$10 / 210$\pm$20 / 305$\pm$25   / 820$\pm$120  / 1.48$\pm$0.18 / |
| Spectral index ALMA 3 | 1.56 | 0.13 | dimensionless | 3 | / ALMA 3       / 05 35 14.802    / $-$05 22 30.69  / 31$\pm$3   / 117$\pm$15 / 180$\pm$15 / 260$\pm$22   / 720$\pm$60   / 1.56$\pm$0.13 / |
| Spectral index Source I | 1.74 | 0.15 | dimensionless | 3 | / 1-8 Source I / 05 35 14.515    / $-$05 22 30.60  / 150$\pm$14 / 590$\pm$80 / 905$\pm$90 / 1518$\pm$150 / 3950$\pm$320 / 1.74$\pm$0.15 / |
| Brightness temperature of ALMA 1-3 at 658 GHz | 100 to 200 | not stated | K | 3 | we estimated brightness temperatures of about 100 to 200 K. |

## Qualitative findings

- Three new compact submillimeter sources (ALMA 1-3) are found near the HMC but do not coincide with hot molecular gas peaks  
  > "None of these positions coincide with the submillimeter compact sources reported in this paper." (Results)

## Claim tuples

- H: Do compact continuum sources internally heat the Orion-KL HMC? | E: Multi-band ALMA continuum imaging with restricted uv-range, comparison to hot gas peaks | R: Three new sources, with spectral indices 1.47-1.56, not coincident with hot gas | F: HMC is heated externally | **supported**
- H: What is the nature of ALMA 1-3? | E: Spectral index and brightness temperature | R: Index 1.47-1.56, Tb 100-200 K | F: Moderately optically thick dust emission, possibly with grain growth | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: uv-range restricted to filter extended emission while retaining enough visibilities  
  > "We chose the *uv-range* based on a trade off between removing as much extended emission as possible and keeping enough visibilities to obtain a good map." (Observations)
- How they decided it was enough: _not stated_
- Limitation (authors): Continuum may be contaminated by faint lines; mass estimate unreliable because emission is optically thick  
  > "we have probably some contamination from very faint lines." (Observations)
- Caveat (inferred, ours): Archival data from different programs and epochs; flux scale and cross-band consistency not quantified
- Caveat (inferred, ours): uv-range cuts differ by band, which can bias the spectral indices
- Caveat (inferred, ours): Brightness temperature method not described
- Caveat (inferred, ours): Orion Source I and BN are not the focus and may be affected by free-free emission
- Caveat (inferred, ours): Conclusion of external heating is only indirect

## Reproducibility

- Data public (paper): Programs listed with ADS/JAO.ALMA codes; public status not explicitly stated  
  > "This paper makes use of the following ALMA data:" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Full imaging parameters (cell, size, masks, iterations)
- Missing: Self-calibration details
- Missing: Continuum channel selection
- Missing: Flux calibrator and calibration version
- Data volume (inferred): ~200-500 GB raw for five bands
- Score (inferred): 4/5, Data are archival with a simple recipe, but imaging parameters are sparse and fluxes depend on uv-cut choices.
- Rediscovery candidate: no, Recipe is incomplete (no masks, channels, or self-cal details), and numbers are sensitive to choices.

## Links

- Companion: (cite: god2011) (NH3 hot gas peak positions used for comparison)
- Companion: (cite: zap2011b) (CH3CN hot gas peak positions used for comparison)

## Checks

```json
{
 "quotes": 39,
 "quotes_ok": 39,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 59,
  "stated": 27,
  "rate": 0.458
 },
 "evidence_ok": true
}
```
