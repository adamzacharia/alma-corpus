# Re-exploring Molecular Complexity with ALMA (ReMoCA): interstellar detection of urea

`2019A&A...628A..10B` | Astronomy and Astrophysics 2019 | first author: Belloche, A. | arXiv: 1906.04614 | DOI: 10.1051/0004-6361/201935428

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: astrochemistry, star_formation
- Question: Is urea detected toward the hot cores of Sgr B2(N) in the ReMoCA ALMA survey, and how does its abundance compare with related COMs and chemical models?  
  > "We want to take advantage of the increased sensitivity and angular resolution provided by the Atacama Large Millimeter/submillimeter Array (ALMA) to search for urea toward the hot molecular cores embedded in the high-mass-star-forming region Sgr B2(N)." (abstract)
- Target **Sgr B2(N1S)**: coordinates (17h47m19.870s, -28°22'19.48'') J2000  
  > "We call this position Sgr B2(N1S)." (4.3 Position selection); "about 1$\ensuremath{''}$ to the south of Sgr B2(N1)" (4.3 Position selection); z/distance _not stated_; distance from _not stated_
- Target **Sgr B2(N2)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.00074.S
- bands: 84.1–114.4 GHz (3 mm), five spectral setups S1–S5  
  > "We performed a complete spectral line survey toward Sgr B2(N) with ALMA between 84.1 GHz and 114.4 GHz." (2.1 Observations)
- frequencies and spectral setup: four 1875 MHz spectral windows per setup; channel spacing 244.141 kHz, smoothed to 488.3 kHz  
  > "The observations were performed with a channel spacing of 244.141 kHz and the spectra were smoothed to a resolution of 488.3 kHz (1.7 to 1.3 km s$^{-1}$)." (2.1 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15–3600 m ranges across setups  
  > "2017-07-23 | 05:36 | 46 | 17–3600" (Table 1)
- angular resolution: HPBW from 0.86x0.67'' (S1) down to 0.38x0.25'' (S5)  
  > "| S1       | 0        | 84 112 – 85 990   | $0.86 \times 0.67$ | $-84$      |   | 0.98  | 0.29  |" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: median rms 0.39–1.05 mJy/beam per window  
  > "The sensitivity in flux density of the ReMoCA survey is a factor of three times better than that of the EMoCA survey." (2.2 Data reduction)
- time on source: four observing blocks of 47–50 min per setup  
  > "Each setup was observed in four observing blocks of 47–50 min on-source integration time each." (2.1 Observations)
- observing dates: 2016-10-29 to 2017-07-24 (Cycle 4)  
  > "All observations were performed during ALMA’s observing cycle 4." (2.1 Observations)
- pi or archival as stated: _not stated_
- Line: NH2C(O)NH2 (urea) nine clearly detected lines, v=0 and v=1 (90.4–112.4 GHz)
- Other facility **Laboratory spectroscopy (Medvedev group)**: Urea rotational spectroscopy predictions for v=0 and v=1  
  > "A steady flow of urea through a two-meter long absorption cell heated to 120$^\circ$C facilitated the acquisition of continuous spectra in the 210–270 GHz and 300–500 GHz bands." (3 Spectroscopy)
- External data: N2 column densities of other species from EMoCA, and N2 rotational temperature/size for acetamide  
  > "assuming the same rotational temperature (180 K) and source size (0.9$\ensuremath{''}$) as derived for CH$_3$C(O)NH$_2$ toward N2 by (cite: Belloche17)" (4.4 Detection of urea) [from (cite: Belloche17)]
- Simulation/model as data: MAGICKAL gas-grain chemical kinetics model, fast/medium/slow warm-up  
  > "For the warm-up phase, here the usual three warm-up timescales (fast, medium, and slow) are tested" (5 Chemical modeling)

## Processing

### Calibration

- pipeline or manual: JAO-provided procedures for bandpass, amplitude, phase calibration  
  > "We used the procedures provided by the Joint ALMA Observatory to apply the bandpass, amplitude, and phase calibrations." (2.2 Data reduction)
- casa version: CASA 4.2.0 (r28322) for S1–S4; 4.2.1 (r29047) for S5  
  > "version 4.2.0 (r28322) for setups S1 to S4 and version 4.2.1 (r29047) for setup S5" (2.2 Data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: 3–4 iterations using a strong line toward Sgr B2(N1) in each setup  
  > "three or four iterations of self-calibration were performed using a strong spectral line detected toward Sgr B2(N1) in each setup." (2.2 Data reduction)

### Imaging

- task: _not stated_
- deconvolver: csclean imager mode  
  > "The deconvolution was performed with the *csclean* imager mode" (2.2 Data reduction)
- weighting robust: Briggs, robust = 0.5  
  > "a *Briggs* weighting scheme with a *robust* parameter of 0.5" (2.2 Data reduction)
- uv taper: _not stated_
- cell size: 0.12'' (S1–S3), 0.06'' (S4–S5)  
  > "The pixel size was set to 0.12$\ensuremath{''}$ for setups S1–S3 and 0.06$\ensuremath{''}$ for setups S4–S5" (2.2 Data reduction)
- image size: 1000x1000 (S1–S3), 1890x1890 pixels (S4–S5)  
  > "with 1000 $\times$ 1000 pixels and 1890 $\times$ 1890 pixels, respectively." (2.2 Data reduction)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: image-plane, automatic, with GILDAS/CLASS; preliminary  
  > "we performed the splitting in the image plane, in an automatic way using the GILDAS/CLASS software" (2.2 Data reduction)
- line free channels: channels with absorption identified at four continuum positions and masked; baseline set from lower Gaussian width per pixel  
  > "We estimated the width of this lower part on pixels that appeared free from line emission and used this width to define the level of the baseline in each pixel." (2.2 Data reduction)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: spectra smoothed to 488.3 kHz  
  > "the spectra were smoothed to a resolution of 488.3 kHz (1.7 to 1.3 km s$^{-1}$)" (2.1 Observations)
- final beam: see Table 1, e.g. 0.86x0.67'' to 0.38x0.25''  
  > "S1 | 0 | 84 112 – 85 990 | $0.86 \times 0.67$" (Table 1)
- final rms: _not stated_

### Inherited from earlier work

- Observing strategy similar to EMoCA  
  > "The observations of the ReMoCA survey were conducted in a very similar way as for the EMoCA survey (cite: Belloche16)." (2.1 Observations) [from (cite: Belloche16)]
- Weeds LTE modeling method of the spectrum  
  > "We followed the same method as (cite: Belloche16) to model the spectrum of N1S." (4.3 Position selection) [from (cite: Belloche16)]
- Population diagram method  
  > "We also built a population diagram following the same method as (cite: Belloche16)" (4.4 Detection of urea) [from (cite: Belloche16)]
- Chemical model setup and network  
  > "with a physical and chemical setup very similar to that presented by (cite: Belloche17)" (5 Chemical modeling) [from (cite: Belloche17); (cite: Garrod13)]

### Not stated but needed to reproduce (our reading)

- Pipeline/QA details and flux calibrator names and flux scale uncertainty
- Which line was used for self-calibration in each setup
- Exact channel masks for continuum determination
- Clean thresholds, masks and iteration counts
- Full list of molecules/parameters in the full Weeds model
- Uncertainties on LTE column densities
- Urea spectroscopic line list (Medvedev et al. in prep.)
- Details of the MAGICKAL network and parameters beyond Belloche17

## Analysis recipe

1. **Calibrate and image the survey**: JAO calibration procedures plus self-calibration, csclean imaging  
  > "The data was calibrated and imaged with the Common Astronomy Software Applications package (CASA)" (2.2 Data reduction)
   - software: CASA
   - parameter: Briggs robust 0.5  
  > "a *Briggs* weighting scheme with a *robust* parameter of 0.5" (2.2 Data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Separate continuum from line emission**: Image-plane automatic baseline estimation per pixel  
  > "Therefore we performed the splitting in the image plane, in an automatic way using the GILDAS/CLASS software" (2.2 Data reduction)
   - software: GILDAS/CLASS
   - fitting: _not stated_
   - validation: Compared S1 and S5 continuum maps and with literature maps  
  > "the similarities between both maps give us confidence in their reliability." (4.1 Continuum emission)
3. **Select analysis position**: Choose position offset ~1'' south of N1 peak to avoid continuum opacity, with narrow lines (~5 km/s)  
  > "We selected N1S because of its narrow linewidths, on the order of 5 km s$^{-1}$" (4.3 Position selection)
   - fitting: _not stated_
   - validation: _not stated_
4. **Model full spectrum and fit urea LTE emission**: Weeds LTE synthetic spectra of all identified molecules, parameters optimized by visual inspection; urea at 160 K, size 2'', N=2.7e16  
  > "The synthetic spectrum matches the ReMoCA spectrum relatively well, as evaluated by visual inspection" (4.4 Detection of urea)
   - software: Weeds, CDMS-format predictions
   - parameter: source size 2''; Trot 160 K; Delta V 5.0 km/s  
  > "NH$_2$C(O)NH$_2$, $\varv=0$$^\star$ | d | 7 | 2.0 | 160 | 2.7 (16) | 1.86 | 5.0 | 0.0 | 1" (Table 3)
   - assumption: LTE, source size 2'' for all species  
  > "We assumed a source size of 2$\ensuremath{''}$ for all species, which is more extended than the beam." (4.3 Position selection)
   - fitting: Visual optimization, no sampler  
  > "the quality of this match is carefully evaluated by visual inspection of the spectra themselves which we use to optimize the model parameters." (4.4 Detection of urea)
   - validation: Nine clearly detected lines; checked Halpha contamination  
  > "We can thus safely conclude that at the high angular resolution of the ReMoCA survey and toward the specific position Sgr B2(N1S), the ReMoCA spectrum is not significantly contaminated by H$\alpha$ emission." (6.1 Astronomical detection)
5. **Population diagrams**: Population diagrams corrected for opacity and contamination  
  > "yields a rotational temperature of $350 \pm 190$ K" (4.4 Detection of urea)
   - assumption: Background continuum negligible (found invalid at this resolution)  
  > "requires the background continuum temperature to be negligible compared to the excitation temperature of the transitions." (4.4 Detection of urea)
   - fitting: linear fit  
  > "This dependence on the background level affects the observed datapoints as well and cannot be accounted for by a simple linear fit to the population diagram." (4.4 Detection of urea)
   - validation: considered unreliable for urea  
  > "this population diagram should be viewed with caution." (4.4 Detection of urea)
6. **Derive N2 upper limit and compare N1S/N2**: Used N2 model at 180 K, 0.9''; abundances relative to formamide  
  > "No sign of urea was found" (4.4 Detection of urea)
   - software: Weeds
   - fitting: _not stated_
   - validation: _not stated_
7. **Chemical modeling**: MAGICKAL cold collapse then warm-up (fast, medium, slow); compare peak gas-phase abundances with observed ratios  
  > "we used the astrochemical kinetics code MAGICKAL (cite: Garrod13)" (5 Chemical modeling)
   - software: MAGICKAL
   - parameter: zeta = 1.3e-17 s-1; warm-up to 200 K in 5e4, 2e5 or 1e6 yr  
  > "The cosmic-ray ionization rate is held at the canonical value, $\zeta$=$1.3 \times 10^{-17}$ s$^{-1}$." (5 Chemical modeling)
   - assumption: E_des(CH3NCO)=6486 K, N-methylformamide 7386 K  
  > "to give $E_{\mathrm{des}}$(CH$_3$NCO) = $E_{\mathrm{des}}$(CH$_3$NC) + $E_{\mathrm{des}}$(O) = 6486 K" (5 Chemical modeling)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.2.0 / 4.2.1: calibration and imaging  
  > "The data was calibrated and imaged with the Common Astronomy Software Applications package (CASA)" (2.2 Data reduction)
- **GILDAS/CLASS** : line/continuum splitting  
  > "in an automatic way using the GILDAS/CLASS software" (2.2 Data reduction)
- **Weeds** : LTE synthetic spectra  
  > "we use the Weeds software (cite: Maret11) to produce synthetic spectra of complex organic molecules under the LTE assumption" (4.3 Position selection)
- **SPFIT/SPCAT** : fitting urea laboratory spectrum  
  > "all fits were performed with the SPFIT /SPCAT package (cite: Pickett91)" (3 Spectroscopy)
- **MAGICKAL** : chemical kinetics modeling  
  > "we used the astrochemical kinetics code MAGICKAL (cite: Garrod13)" (5 Chemical modeling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Urea column density toward N1S | 2.7e16 | not stated | cm^-2 | 4 | NH$_2$C(O)NH$_2$, $\varv=0$$^\star$ / d / 7 / 2.0 / 160 / 2.7 (16) |
| Urea rotational temperature from population diagram | 350 | 190 | K | 5 | yields a rotational temperature of $350 \pm 190$ K |
| Urea column density upper limit toward N2 | <2.3e15 | not stated | cm^-2 | 6 | NH$_2$C(O)NH$_2$, $\varv=0$ / n / 0 / 0.9 / 180 / $<$ 2.3 (15) |
| N-methylformamide column density toward N1S | 2.6e17 | not stated | cm^-2 | 4 | CH$_3$NHCHO, $\varv=0$$^\star$ / d / 38 / 2.0 / 160 / 2.6 (17) |
| Formamide column density toward N1S | 2.9e18 | not stated | cm^-2 | 4 | NH$_2$CHO, $\varv=0$$^\star$ / d / 20 / 2.0 / 160 / 2.9 (18) |
| Urea/formamide abundance ratio N1S | 0.0093 | not stated | dimensionless | 6 | 1 / 0.086 / 0.090 / 0.14 / 0.0093 for Sgr B2(N1S) |
| Formamide rotational temperature | 159 | 5 | K | 5 | well-constrained rotational temperature of $159 \pm 5$ K |
| 16O/18O ratio from formamide | 140 | not stated | dimensionless | 4 | The $^{16}$O/$^{18}$O ratio of 140 |
| 14N/15N ratio from formamide | 314 | not stated | dimensionless | 4 | The $^{14}$N/$^{15}$N ratio of 314 |

## Qualitative findings

- Sixty clearly detected N-methylformamide lines confirm its interstellar detection  
  > "we count sixty clearly detected lines" (4.5 Confirmation of N-methylformamide)
- Model overproduces urea by at least one order of magnitude  
  > "but it overproduces urea by at least one order of magnitude." (abstract)

## Claim tuples

- H: Is urea securely detectable toward Sgr B2(N1S) in ReMoCA? | E: Full-spectrum LTE modeling and line identification | R: Nine clearly detected lines, N=2.7e16 cm^-2 at 160 K | F: Secure first detection of urea in the ISM | **supported**
- H: Is urea present in Sgr B2(N2)? | E: Search with N2 model | R: No detection; N<2.3e15 cm^-2 | F: Urea at least an order of magnitude less abundant relative to other species than in N1S | **supported**
- H: Does chemical modeling reproduce observed relative abundances? | E: MAGICKAL fast/medium/slow models | R: Reproduces four species roughly; urea overproduced | F: Urea grain production too efficient or gas destruction missing | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Population diagrams unreliable due to continuum opacity so full-model visual comparison is preferred  
  > "We rather consider it as a convenient tool to visualize in a concise way the match between the synthetic and observed spectra." (4.4 Detection of urea)
- Alternative: Did not apply Xue et al. P and D factor method due to unaccounted systematic uncertainties and arbitrary frequency range  
  > "we did not attempt to apply this method here for two reasons." (6.1 Astronomical detection)
- How they decided it was enough: _not stated_
- Limitation (authors): Line-continuum splitting is preliminary with unexplained baseline artifacts  
  > "the splitting of the line and continuum emission performed so far is still preliminary and we plan to improve it in the future." (2.2 Data reduction)
- Caveat (inferred, ours): No formal uncertainties on LTE column densities
- Caveat (inferred, ours): Detection significance judged by visual inspection, not statistically
- Caveat (inferred, ours): Temperature of urea poorly constrained (350±190 K)
- Caveat (inferred, ours): Urea spectroscopy not yet published
- Caveat (inferred, ours): Source size 2'' assumed for all species

## Reproducibility

- Data public (paper): Data available in ALMA archive  
  > "The interferometric data are available in the ALMA archive at https://almascience.eso.org/aq/." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Urea line list (Medvedev et al. in prep.)
- Missing: Full Weeds model parameters for all species
- Missing: Exact continuum-splitting parameters
- Missing: Flux calibrator details
- Data volume (inferred): Large: ~20 spectral windows over 18 execution blocks, likely several hundred GB to ~1 TB raw
- Score (inferred): 3/5, Public data and clear parameters, but reproduction depends on custom line list, manual visual fitting and prior-work model details.
- Rediscovery candidate: no, Needs unpublished urea predictions, and results come from visual model fitting of a full-spectrum model.

## Links

- Method: (cite: Belloche16) (EMoCA survey observing and LTE modeling method)
- Method: (cite: Belloche17) (N2 molecular composition and chemical model setup)
- Method: (cite: Garrod13) (MAGICKAL code)
- Companion: Medvedev et al. in prep. (urea laboratory spectroscopy)
- Related: EMoCA
- Related: ReMoCA
- Related: PILS

## Checks

```json
{
 "quotes": 72,
 "quotes_ok": 72,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 89,
  "stated": 56,
  "rate": 0.629
 },
 "evidence_ok": true
}
```
