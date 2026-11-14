# Spatially resolved images of reactive ions in the Orion Bar

`2017A&A...601L...9G` | Astronomy and Astrophysics 2017 | first author: Goicoechea, Javier R. | arXiv: 1704.08621 | DOI: 10.1051/0004-6361/201730716

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: milky_way_ism, astrochemistry, star_formation
- Question: Where do the reactive ions SH+, HOC+ and SO+ emit in the Orion Bar PDR, and what do their distribution, excitation and abundances reveal about the chemistry near the dissociation front?  
  > "Therefore, the true spatial distribution of the reactive ions emission is mostly unknown." (Introduction)
- Target **Orion Bar**: coordinates RA(J2000) 5h35m20.6s, Dec -05d25m20s (mosaic center)  
  > "The observations consisted of a 10-pointing mosaic centered at $\alpha$(2000) = 5$^h$35$^m$20.6$^s$; $\delta$(2000) = $-$05$^o$25$'$20$''$." (2 Observations and data reduction); z/distance _not stated_; distance from Menten et al. 2007 (cited for proximity only)  
  > "The observations consisted of a 10-pointing mosaic centered at $\alpha$(2000) = 5$^h$35$^m$20.6$^s$; $\delta$(2000) = $-$05$^o$25$'$20$''$." (2 Observations and data reduction)

## Data provenance

- ALMA projects: 2012.1.00352.S
- bands: _not stated_
- frequencies and spectral setup: ~345-358 GHz; ~500 kHz resolution over 937.5 MHz bandwidth  
  > "Lines were observed with correlators providing $\sim$500 kHz resolution over a 937.5 MHz bandwidth." (2 Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: ACA 7 m antennas plus total-power 12 m antennas  
  > "The interferometric images were taken with the 7 m antennas of the Atacama Compact Array (ACA), Chile." (2 Observations and data reduction)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 4.9" x 3.0" synthesized beam  
  > "using the synthesized beam size of 4.9$''$$\times$3.0$''$" (2 Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: rms ~10-20 mK per 0.5 km/s channel  
  > "The achieved rms noise is $\sim$10-20 mK per 0.5 km s$^{-1}$ smoothed channel" (2 Observations and data reduction)
- time on source: ~6 h  
  > "The ALMA-ACA observation time was $\sim$6 h." (2 Observations and data reduction)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO 3-2 (345795.9899 MHz)
- Line: HOC+ 4-3 (357922.0140 MHz)
- Line: SH+ 1_0-0_1 1/2-3/2 (345944.4205 MHz)
- Line: SO+ 15/2- - 13/2+ (347740.0110 MHz)
- Line: H13CO+ 4-3 (346998.3360 MHz)
- Line: SO 8_9-7_8 (346528.5280 MHz)
- Line: HCO+ 4-3 (356734.2246 MHz)
- Other facility **IRAM 30 m**: Pointed multi-line observations toward the DF (line survey)  
  > "we carried out pointed observations toward the DF with the IRAM 30 m telescope (Spain)." (2 Observations and data reduction)
- Other facility **Herschel**: CH+ PACS and SH+ HIFI data from literature  
  > "by *Herschel*/HIFI at $\sim$526 GHz (cite: Nagy_2013)" (Appendix B)
- External data: H2 v=1-0 S(1) image of the DF  
  > "vibrationally excited molecular hydrogen (H$_{2}^{*}$) v=1-0 $S$(1) line (cite: Walmsley_2000)" (3 Results) [from Walmsley_2000]
- External data: Spitzer/IRAC 8 micron image  
  > "as traced by the *Spitzer*/IRAC 8 $\mu$m emission (cite: Megeath_2012)" (3 Results) [from Megeath_2012]
- External data: Dust continuum model for far-IR radiation field  
  > "The resulting continuum levels (Fig. [4](#fig:continuum)) reproduce the far-IR photometric measurements toward the Orion Bar; we refer to (cite: Arab_2012)." (Appendix B) [from Arab_2012]
- Simulation/model as data: Meudon PDR code v1.5.2 constant-pressure slab models, P_th/k 2e7 to 2e8 K cm-3, chi=1e4  
  > "We used version 1.5.2 of the Meudon PDR code (cite: LePetit_2006) to model the formation and destruction of reactive ions" (4 Discussion)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ~10%  
  > "with an absolute flux accuracy of $\sim$10%" (2 Observations and data reduction)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: Högbom CLEAN  
  > "The dirty image was deconvolved using the Högbom CLEAN algorithm." (2 Observations and data reduction)
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Total-power 12 m single-dish maps used to create short-spacing visibilities with GILDAS/MAPPING and merged with ACA  
  > "We used the GILDAS/MAPPING software to create the short-spacing visibilities not sampled by ALMA-ACA." (2 Observations and data reduction)
- smoothing: 0.5 km/s channels  
  > "per 0.5 km s$^{-1}$ smoothed channel" (2 Observations and data reduction)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Short-spacing merging procedure  
  > "These visibilities were merged with the interferometric observations (cite: Pety_2010)." (2 Observations and data reduction) [from (cite: Pety_2010)]
- IRAM 30 m line survey data  
  > "These multi-line observations are part of a complete 80-360 GHz line survey at resolutions between $\sim$30$''$ and $\sim$7$''$ (cite: Cuadrado_2015a)." (2 Observations and data reduction) [from (cite: Cuadrado_2015a)]

### Not stated but needed to reproduce (our reading)

- CASA/GILDAS versions and calibration procedure
- CLEAN mask, weighting, cell and image size
- Line-free channels / continuum subtraction
- Total-power observation details and project codes
- Spatial cut definition for Fig 2a
- Distance adopted to Orion
- IRAM 30 m spectra needed for population diagrams

## Analysis recipe

1. **Image ACA+TP cubes**: Merge ACA with single-dish short spacings, Högbom CLEAN, convert to brightness temperature  
  > "The resulting cubes were scaled from Jy/beam to brightness temperature scale using the synthesized beam size of 4.9$''$$\times$3.0$''$." (2 Observations and data reduction)
   - software: GILDAS/MAPPING
   - fitting: _not stated_
   - validation: _not stated_
2. **Rotational population diagrams**: Derive Trot and N from IRAM 30 m lines for uniform filling and 10" filament  
  > "We first derived H$^{13}$CO$^+$, HOC$^+$, SO$^+$, and SO rotational temperatures ($T_{\rm rot}$) and column densities ($N$) by building rotational population diagrams" (3 Results)
   - assumption: 10" width filamentary emission layer with beam dilution correction  
  > "for a more realistic filamentary emission layer of $\sim$10$''$ width and correcting for beam dilution" (3 Results)
   - fitting: _not stated_
   - validation: _not stated_
3. **Non-LTE Monte Carlo excitation model**: Statistical equilibrium and radiative transfer with H2 and e- collisions and dust+CMB radiative pumping, varying N, nH, Tk  
  > "By varying $N$, $n_{\rm H}$ and $T_{\rm k}$, we tried to reproduce the H$^{13}$CO$^+$, HOC$^+$, SH$^+$, and SO$^+$ line intensities" (Appendix B)
   - software: non-LTE code (Goicoechea 2006)
   - parameter: n(e-)=10 cm-3; Td=50 K; beta=1.6; tau_d~0.03 at 160 um; sigma~1 km/s  
  > "effective dust temperature of $T_{\rm d}$=50 K, spectral emissivity index of $\beta$=1.6, and a dust opacity ($\tau_{\rm d}$) of $\simeq$0.03" (Appendix B)
   - fitting: Manual variation of parameters; no sampler stated  
  > "By varying $N$, $n_{\rm H}$ and $T_{\rm k}$, we tried to reproduce the H$^{13}$CO$^+$, HOC$^+$, SH$^+$, and SO$^+$ line intensities observed by ALMA-ACA" (Collisional and radiative excitation of H$^{13}$CO$^+$, HOC$^+$, SH$^+$, and SO$^+$)
   - validation: Best models fit intensities within factor 2 and reproduce Trot within 3 K  
  > "Our best models fit the intensities by less than a factor of 2." (Appendix B)
4. **Compare with PDR model**: Meudon PDR code columns compared with observed columns accounting for tilt angle and depth  
  > "Recent studies constrain $\alpha$ and $l_{\rm depth}$ to $\lesssim$4$^o$ and $\simeq$0.28 pc, respectively" (4 Discussion)
   - software: Meudon PDR code
   - assumption: Undepleted sulfur [S]=1.4e-5  
  > "We adopt an undepleted sulfur abundance of \[S\]=1.4$\times$10$^{-5}$" (4 Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **GILDAS/MAPPING** : Short-spacing visibilities and merging  
  > "We used the GILDAS/MAPPING software to create the short-spacing visibilities" (2 Observations and data reduction)
- **Meudon PDR code** 1.5.2: PDR chemical models  
  > "We used version 1.5.2 of the Meudon PDR code" (4 Discussion)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Half-power width of SH+ and HOC+ emission layer | ~10 | not stated | arcsec | 1 | with a half-power-width of $\Delta(\delta x)$$\simeq$10$''$ ($\simeq$0.02 pc) |
| SH+ line width | 2.8 | 0.1 | km/s | 1 | SH$^+$ 1$_0$-0$_1$ ($\Delta$v=2.8$\pm$0.1 km s$^{-1}$) |
| SO line width | 1.8 | 0.1 | km/s | 1 | the SO 8$_9$-7$_8$ line is narrower ($\Delta$v=1.8$\pm$0.1 km s$^{-1}$) |
| [HCO+]/[HOC+] at dx=12-22" | 145 | 5 | dimensionless | 0 | roughly constant \[HCO$^+$\]/\[HOC$^+$\] ratio of 145$\pm$5 along the $\delta x$=12-22$''$ layer |
| [HCO+]/[HOC+] at dx=22-32" | 180 | 4 | dimensionless | 0 | \[HCO$^+$\]/\[HOC$^+$\]=180$\pm$4 along the $\delta x$=22-32$''$ layer |
| SH+ column density (10" filament) | 1.5e13 | 0.5e13 | cm-2 | 2 | (1.5 $\pm$ 0.5) $\times$ 10$^{13}$ |
| CH+ Trot from PACS | ~150 | not stated | K | 0 | we derive $T_{\rm rot}^{\rm PACS}$$\simeq$150 K |

## Qualitative findings

- Except SO+, reactive ion emission starts near the DF and follows vibrationally excited H2; SO+ peaks deeper in the cloud.  
  > "except for SO$^+$, the emission from reactive ions starts very close to the DF, and globally follows that of H$_{2}^{*}$" (3 Results)

## Claim tuples

- H: Reactive ions SH+ and HOC+ trace a narrow layer at the DF | E: ACA+TP images and emission cuts | R: Half-power width ~10" layer delineating the DF | F: SH+ and HOC+ emission is an indicator of FUV-irradiated gas | **supported**
- H: High-pressure PDR models explain observed columns | E: Meudon models compared with observed N | R: Agreement for HOC+, H13CO+, SO+; SH+ exceeds model by factor ~3-30 | F: Extra SH+ source needed | **partially**
- H: Broader CH+ lines and warmer Trot arise from its short lifetime and radiative pumping | E: Compared destruction timescales with excitation rates | R: CH+ pumped by radiation many times during lifetime, heavier ions by collisions | F: Explains narrower lines and lower Trot of heavier ions | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): No published collisional rates for SH+ and SO+; estimated rates used, SH+ requires denser gas  
  > "For SH$^+$ ($^3\Sigma^-$) there are no published collisional rate coefficients." (Footnote 3)
- Caveat (inferred, ours): Single-component non-LTE models fit to one position
- Caveat (inferred, ours): Scaled/estimated collisional rates for SH+ and SO+
- Caveat (inferred, ours): 1D isobaric PDR model not directly comparable with spatial scales
- Caveat (inferred, ours): Little processing detail

## Reproducibility

- Data public (paper): ALMA data cited by project code  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00352.S." (footnote 1)
- Products in archive: _not stated_
- Missing: IRAM 30 m spectra
- Missing: TP data reduction details
- Missing: CASA and GILDAS versions
- Missing: imaging parameters
- Missing: private collisional rates (J. Black)
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Public ALMA data but sparse processing details and private collisional rates.
- Rediscovery candidate: no, Imaging details and IRAM data are missing and the modeling relies on private rates.

## Links

- Method: Pety_2010 (Short-spacing merging)
- Method: Goicoechea_2006 (Non-LTE code)
- Method: LePetit_2006 (Meudon PDR code)
- Companion: Goicoechea_2016 (ALMA HCO+ high-resolution images of the Bar)
- Companion: Cuadrado_2015a (IRAM 30 m line survey)
- Related: IRAM 30 m Orion Bar line survey

## Checks

```json
{
 "quotes": 53,
 "quotes_ok": 53,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 34,
  "rate": 0.486
 },
 "evidence_ok": true
}
```
