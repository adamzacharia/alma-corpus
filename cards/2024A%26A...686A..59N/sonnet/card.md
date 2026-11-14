# A deep search for large complex organic species toward IRAS16293-2422 B at 3 mm with ALMA

`2024A&A...686A..59N` | Astronomy and Astrophysics 2024 | first author: Nazari, P. | arXiv: 2401.04760 | DOI: 10.1051/0004-6361/202347832

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: astrochemistry, star_formation
- Question: Can large complex organic molecules (>8 atoms; e.g. glycerol, propanols) be detected in the deep ALMA Band 3 spectrum of IRAS16293 B, and do column densities and ratios to methanol differ from Band 7 (PILS) because of dust optical depth?  
  > "We aim to search for large molecules ($> 8$ atoms) in the Atacama Large Millimeter/submillimeter Array (ALMA) Band 3 spectrum of IRAS 16293-2422 B." (abstract)
- Target **IRAS 16293-2422 B**: coordinates 0.5'' offset position from B continuum peak: RA 16h32m22.58s, Dec -24d28m32.8s (J2000)  
  > "$\alpha_{\rm J2000} = 16^{\rm h} 32^{\rm m} 22^{\rm s}.58$ and $\delta_{J2000} = -24^{\circ} 28\ensuremath{'} 32.8\ensuremath{''}$" (2.1 Data); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2017.1.00518.S, 2013.1.00278.S
- bands: Band 3 (~100 GHz); PILS Band 7 (~345 GHz) for comparison  
  > "This paper uses the data of IRAS16293 B taken with ALMA in Band 3" (2.1 Data)
- frequencies and spectral setup: ~90.59-91.41 GHz (continuum), ~93.14-93.20 GHz, ~103.28-103.52 GHz; resolution 0.805, 0.049, 0.088 km/s  
  > "The frequency ranges covered were ${\sim}90.59-91.41$ GHz (continuum), ${\sim}93.14-93.20$ GHz and ${\sim}103.28-103.52$ GHz." (2.1 Data); "The spectral resolution was 0.805 km s$^{-1}$, 0.049 km s$^{-1}$, and 0.088 km s$^{-1}$." (2.1 Data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-4  
  > "We used the data with configuration C43-4" (2.1 Data)
- baselines: _not stated_
- angular resolution: ~0.9'' x 0.7''  
  > "The data have an angular resolution of ${\sim} 0.9\ensuremath{''} \times 0.7\ensuremath{''}$" (2.1 Data)
- max recoverable scale: _not stated_
- sensitivity: rms ~0.1 K, ~0.3 K and 0.2 K per spectral window (brightness temperature)  
  > "the rms found from line-free regions in each spectral window is ${\sim}0.1$ K, ${\sim}0.3$ K and $0.2$ K" (2.1 Data)
- time on source: 171.7 minutes  
  > "following 171.7 minutes on-source integration time" (2.1 Data)
- observing dates: _not stated_
- pi or archival as stated: PI E. F. van Dishoeck; PILS continuum taken from ALMA archive  
  > "We took the continuum image of the PILS survey at $\nu {\sim}348.815$ GHz from the ALMA archive" (4.1 Dust optical depth)
- Other facility **ALMA PILS (Band 7)**: Band 7 column densities and continuum image for comparison  
  > "We took the continuum image of the PILS survey at $\nu {\sim}348.815$ GHz from the ALMA archive" (4.1 Dust optical depth)
- External data: PILS Band 7 column densities of many species  
  > "The column densities of PILS are taken from (cite: Coutens2016) (NH$_2$CHO)" (4.2.2 Column density) [from Coutens2016; Jorgensen2016; Calcutt2018; Jorgensen2018; Persson2018; Manigand2020; Drozdovskaya2022; Ilyushin2022; Drozdovskaya2018; Ferrer2023; Lykke2017]
- External data: 12C/13C = 68  
  > "scaling the $^{13}$CH$_3$OH column density by $^{12}$C/$^{13}$C $= 68$ ((cite: Milam2005))" (Table 1 notes) [from Milam2005]
- External data: Dust temperature range / inner region ~90 K  
  > "The temperature of the inner regions based on models of (cite: Jacobsen2018) is ${\sim} 90$ K." (4.1 Dust optical depth) [from Jacobsen2018]

## Processing

### Calibration

- pipeline or manual: CASA pipeline, then self-calibrated with CASA  
  > "calibrated with the CASA pipeline ((cite: McMullin2007)) and then self-calibrated with CASA" (2.1 Data)
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
- continuum subtraction: STATCONT on self-calibrated cubes  
  > "Continuum subtraction was done on the self-calibrated image datacubes using STATCONT ((cite: Sanchez2018))." (2.1 Data)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Data calibration, reduction and imaging  
  > "For more information on the data calibration, reduction and imaging, as well as first results on gas accretion flow in the IRAS16293 system see (cite: Murillo2022)" (2.1 Data) [from (cite: Murillo2022)]
- Fit-by-eye LTE fitting and uncertainty estimate  
  > "The fitting followed a similar procedure as the fit-by-eye method used in (cite: Nazari2022ALMAGAL)." (2.2 Spectral modeling) [from (cite: Nazari2022ALMAGAL)]
- Extraction position 0.5'' offset from continuum peak  
  > "extracted from the same $0.5\ensuremath{''}$ offset position from the continuum peak of B that was used in many of the works from ALMA-PILS" (2.1 Data) [from (cite: Coutens2016); (cite: Jorgensen2018); (cite: Calcutt2018)]

### Not stated but needed to reproduce (our reading)

- Imaging parameters (weighting, robust, cell, image size, tclean settings) not given
- Self-calibration solution intervals and CASA version for reduction
- Line-free channels used by STATCONT
- Exact definition of the 1'' beam used for column densities
- Detailed procedure for the column density uncertainties and upper limits
- Flux scale calibrators and uncertainty

## Analysis recipe

1. **Extract spectrum**: Spectrum extracted at 0.5'' offset position from continuum peak of B  
  > "The spectrum of IRAS16293 B (Fig. [1](#fig:overview)) was extracted from the same $0.5\ensuremath{''}$ offset position from the continuum peak of B" (2.1 Data)
   - software: CASA, STATCONT
   - fitting: _not stated_
   - validation: _not stated_
2. **LTE fit of column densities and Tex**: CASSIS LTE modelling varying N and Tex by eye; all lines of a molecule fitted simultaneously; detection if >=3 lines at >=3 sigma  
  > "We consider a molecule as detected if it has at least three lines at a peak of $\geq3\sigma$ level." (2.2 Spectral modeling)
   - software: CASSIS
   - parameter: FWHM fitted on unblended lines then fixed (~1.8±0.5 km/s); Tex fitted only if >=2 lines with range of Eup, else fixed to 100 K (300 K for t-HCOOH, NH2CHO)  
  > "If not enough lines with a range of $E_{\rm up}$ were detected, the temperature is fixed to 100 K" (2.2 Spectral modeling)
   - parameter: Vlsr = 2.7 km/s  
  > "the source velocity was fixed to $V_{\rm lsr} = 2.7$ km s$^{-1}$" (2.2 Spectral modeling)
   - assumption: LTE, beam dilution of unity (source fills ~1'' beam)  
  > "a beam dilution of unity was assumed resulting in our column densities being representative of those within a beam" (2.2 Spectral modeling)
   - fitting: Fit by eye; typical column density uncertainty ~20%  
  > "the typical uncertainty from the fits is on the order of 20$\%$" (2.2 Spectral modeling)
   - validation: Lines explained within ~20-30%  
  > "the rest of the lines are explained reasonably well (i.e., within ${\sim}20-30\%$" (2.2 Spectral modeling)
3. **Upper limits for non-detections**: Model upper limits with Tex fixed to 100 K and FWHM to 2 km/s  
  > "The upper limits are measured by fixing $T_{\rm ex}$ to 100 K and FWHM to 2 km s$^{-1}$." (Table 3 notes)
   - software: CASSIS
   - fitting: _not stated_
   - validation: _not stated_
4. **Continuum dust optical depth**: tau = -ln(1 - F/(Omega B(Tdust))) at Band 3 and PILS Band 7 continuum, at peak and offset position, over a range of Tdust  
  > "Next, we calculated $\tau_{\rm dust}$ for a range of dust temperatures that are feasible for IRAS16293B" (4.1 Dust optical depth)
   - software: CASA 6.5.2.26
   - assumption: Tdust ~90 K  
  > "The temperature of the inner regions based on models of (cite: Jacobsen2018) is ${\sim} 90$ K." (4.1 Dust optical depth)
   - fitting: _not stated_
   - validation: _not stated_
5. **Compare with PILS**: Correct PILS column densities by beam dilution factor 0.5, compare N and N/N(CH3OH) between bands  
  > "The PILS column densities are converted to an average over the PILS beam (or filling the PILS beam uniformly) by multiplication with their beam dilution factor" (4.2.2 Column density)
   - fitting: _not stated_
   - validation: CH3COOH refit in Band 7 with new spectroscopy  
  > "we re-did the fit to CH$_3$COOH in the Band 7 data using new spectroscopic data" (4.2.2 Column density)

## Software

- **CASA** 6.5.2.26 (for continuum flux measurement): Calibration pipeline, self-calibration, continuum flux measurement  
  > "For this measurement we used CASA ((cite: McMullin2007)) version 6.5.2.26" (4.1 Dust optical depth)
- **STATCONT** : Continuum subtraction  
  > "Continuum subtraction was done on the self-calibrated image datacubes using STATCONT" (2.1 Data)
- **CASSIS** : Line identification and LTE spectral fitting  
  > "we identified as many molecules as possible using the CASSIS[^1] spectral analysis tool" (2.2 Spectral modeling)
- **CDMS/JPL** : Spectroscopic line lists  
  > "The line lists were taken from the CDMS ((cite: Muller2001); (cite: Muller2005)) or the JPL database ((cite: Pickett1998))." (2.2 Spectral modeling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Line density Band 3 (>=6 sigma) | 1 per ~8.5 MHz | not stated | MHz per line | 2 | The line density of the lines detected at $\gtrsim 6\sigma$ level in Band 3 (${\sim}100$ GHz) data is 1 per ${\sim}8.5$ MHz |
| CH3OH column density (from 13CH3OH x 68) | 8.2e18 | not stated | cm-2 | 2 | is found to be $8.2 \times 10^{18}$ cm$^{-2}$ in the ${\sim}1\ensuremath{''}$ beam |
| Optical depth at offset position (Band 3 and Band 7) | ~0.15 | not stated | dimensionless | 4 | the dust optical depth for the PILS continuum is almost the same as that of Band 3 which is ${\sim}0.15$ |
| Glycerol/methanol upper limits (GGag'g' and G'Gg'gg') | <1e-4 and <8e-4 | not stated | dimensionless | 3 | are ${<}10^{-4}$ and ${<}8 \times 10^{-4}$ |
| Scatter of Band 3 vs Band 7 column densities | factor 1.9 below, 1.8 above | not stated | dimensionless | 5 | the scatter around the line of $N_{\rm Band 3} = N_{\rm Band 7}$ is a factor of 1.9 below the line and 1.8 above the line |
| Gg'G (gGg') ethylene glycol column density | 5.0e16 | +1.7/-1.4e16 | cm-2 | 2 | gGg$^{\prime}$-(CH$_2$OH)$_2$ / 5.0$^{+1.7}_{-1.4}$ $\times 10^{16}$ / 160$^{+40}_{-40}$ |

## Qualitative findings

- No glycerol, i- or n-propanol detected; 31 species detected (~15 tentative); ~25-30% of >=6 sigma lines unidentified  
  > "We do not detect glycerol or i- and n-propanol but provide upper limits for them" (abstract)

## Claim tuples

- H: Band 3 spectra are much less line-confused than Band 7 | E: Count lines at >=6 sigma | R: 1 line per 8.5 MHz vs 1 per 3.5 MHz | F: Line density only ~2.5 times lower; spectrum remains crowded | **supported**
- H: Larger COMs (glycerol, propanols) are detectable at 3 mm | E: Fit LTE models, derive upper limits | R: Non-detections with limits consistent with lab studies | F: 3 mm has not yet yielded larger molecules in warm sources | **refuted**
- H: Dust optical depth affects column densities and ratios between bands | E: Compare Band 3 and PILS Band 7 values at offset position | R: Agreement within factor ~2 | F: Dust optical depth effect is minimal at off-source location | **supported**

## Reasoning

- Why this data: Settings optimized for glycerol and propanols; lower line confusion expected at 3 mm  
  > "This data set was specifically taken to search for large species due to the expected lower line density and line confusion in Band 3" (3.1)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Single/limited lines for some species; coarse spectral resolution; low angular resolution; upper limits depend on assumed Tex and lines covered  
  > "given that the upper limits reported here depend on the assumed excitation temperature and more importantly the lines covered in our data" (4.3)
- Caveat (inferred, ours): Fit-by-eye fitting without a formal likelihood or sampler
- Caveat (inferred, ours): Beam dilution of unity ignores differing emitting areas
- Caveat (inferred, ours): Single offset position cannot test on-source dust attenuation
- Caveat (inferred, ours): Tex fixed for many species

## Reproducibility

- Data public (paper): Project codes given; PILS continuum from ALMA archive  
  > "We took the continuum image of the PILS survey at $\nu {\sim}348.815$ GHz from the ALMA archive" (4.1)
- Products in archive: _not stated_
- Missing: Imaging and self-calibration parameters
- Missing: Fit-by-eye procedure details and uncertainty method (only referenced)
- Missing: Line-free channels for continuum subtraction
- Data volume (inferred): ~50-100 GB
- Score (inferred): 5/5, Public data and a tabulated results set, but imaging/calibration details are deferred to another paper and fitting is by eye.
- Rediscovery candidate: no, Fit-by-eye procedure and missing reduction details make exact reproduction hard.

## Links

- Method: Murillo2022 (Data calibration, reduction and imaging)
- Method: Nazari2022ALMAGAL (Fit-by-eye LTE fitting and uncertainties)
- Companion: Jorgensen2016 (PILS survey Band 7 comparison)
- Related: PILS

## Checks

```json
{
 "quotes": 51,
 "quotes_ok": 51,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 38,
  "rate": 0.507
 },
 "evidence_ok": true
}
```
