# Extended and Compact Ortho-H<SUB>2</SUB>D<SUP>+</SUP> Structures Close to the Moment of Star Formation: Evidence from ALMA-ACA Observations in Taurus

`2025ApJ...992...55T` | The Astrophysical Journal 2025 | first author: Tokuda, Kazuki | arXiv: 2509.02932 | DOI: 10.3847/1538-4357/ae0460

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: Can ortho-H2D+ (1_10-1_11) trace the dense centers of cores at stages around the onset of star formation (prestellar L1544, first-core candidate MC 35-mm, Class 0 VeLLO MC 27), and where does its emission arise?  
  > "we experimentally investigate whether one of the deuterated isotopologues of H$_3^+$, orth-H$_2$D$^{+}$, can effectively serve as tracers of such dense core centers in the low-mass star formation regime" (Introduction)
- Target **L1544**: coordinates _not stated_; z/distance 171.7 pc  
  > "| L1544 | 171.7 | $\sim$10$^{7}$ | $\sim-$10$^4$ | Free-fall timescale | (cite: Caselli_2019) | $\cdots$ |" (Table 1); distance from not stated (Table 1 note; Taurus 130-170 pc from Galli 2018, 2019)  
  > "| L1544 | 171.7 | $\sim$10$^{7}$ | $\sim-$10$^4$ | Free-fall timescale | (cite: Caselli_2019) | $\cdots$ |" (Table 1)
- Target **MC 35-mm**: coordinates _not stated_; z/distance 128.7 pc  
  > "| MC 35-mm | 128.7 | $>$10$^{7}$ | 0–10$^4$ | Outflow dynamical timescale | (cite: Fujishiro_2020) | L1535-NE |" (Table 1); distance from _not stated_
- Target **MC 27/L1521F**: coordinates _not stated_; z/distance 140 pc  
  > "| MC 27 | 140 | $>$10$^{7}$ | $\sim$5 $\times$ 10$^{4}$ | Rarefaction wave timescale | (cite: Tokuda_2016; Tokuda_2024) | L1521F |" (Table 1); distance from _not stated_

## Data provenance

- ALMA projects: 2023.1.00225.S, 2016.1.00240.S
- bands: Band 7 (0.8 mm)  
  > "Band 7 ortho-H$_2$D$^+$ observations using the Atacama Compact Array (ACA) stand-alone mode" (Introduction)
- frequencies and spectral setup: o-H2D+ at 372.42078 GHz, 62 MHz bandwidth, 61 kHz resolution; continuum bands at 357.99950 and 369.92909 GHz (2 GHz each); 360.16919 GHz (30 kHz, DCO+) and 372.67200 GHz (61 kHz, N2H+)  
  > "we allocated a central frequency of 372.42078 GHz with a bandwidth of 62 MHz and a frequency resolution of 61 kHz." (2 Observations)
- continuum bandwidth: 4 GHz total, 7 m only  
  > "The total bandwidth was 4 GHz, and the sensitivity was 0.78 mJy beam$^{-1}$." (2 Observations)
- arrays: ACA 7 m array and total power (TP) array, Cycle 10  
  > "We conducted ALMA Cycle 10 observations targeting the three sources using the 7 m array and total power (TP) array." (2 Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 7 m: 4.5" x 3.5" (~500 au); TP: 17.5" (~2,500 au)  
  > "with a beam size of 4.5$''$ $\times$ 3.5$''$ ($\sim$500 au). For the TP array, the sensitivity was 0.025 K, and the beam size was 17.5$''$" (2 Observations)
- max recoverable scale: ~2,500 au (17.5")  
  > "a maximum recoverable scale of $\sim$2,500 au" (Concluding remarks)
- sensitivity: H2D+ 7 m: 0.1 K; TP: 0.025 K; 0.83 mm continuum 0.78 mJy/beam  
  > "The sensitivity of the H$_2$D$^+$ data obtained with the 7 m array was 0.1 K" (2 Observations)
- time on source: _not stated_
- observing dates: October 2023 to September 2024  
  > "The ACA observation period spanned from October 2023 to September 2024." (2 Observations)
- pi or archival as stated: _not stated_
- Line: ortho-H2D+ 1_10-1_11 (372.42134 GHz)
- Line: DCO+ 5-4 (not stated)
- Line: N2H+ 4-3 (not stated)
- External data: Tex = 7 K (L1544) and 9 K (MC 27) for o-H2D+  
  > "with an excitation temperature ($T_{\rm ex}$) of 7 K (cite: Caselli_2008)" (3 Results) [from (cite: Caselli_2008)]
- External data: Td = 7 K and kappa(0.8mm)=0.01 cm2/g  
  > "assuming $T_{\rm d}$ = 7 K (cite: Evans_2001) and $\kappa_{\rm 0.8\,mm}$ = 0.01 cm$^{2}$ g$^{-1}$" (3 Results) [from (cite: Evans_2001); (cite: Ward-Thompsoon_1994)]
- External data: ~4 mJy of MC 27 flux from protostellar disk  
  > "The previous 12 m array observations (cite: Tokuda_2017) estimated that $\sim$4 mJy of this flux arises from the protostellar disk component." (3 Results) [from (cite: Tokuda_2017)]
- External data: Physical model of 1D core collapse (density, temperature, Av profiles)  
  > "under the physical conditions taken from the one-dimensional core collapse model of (cite: Masunaga_2000)" (4 Discussion) [from (cite: Masunaga_2000)]
- Simulation/model as data: Chemical network (Furuya 2015) on Masunaga & Inutsuka collapse model at t_core=-6.4e3 yr and -5.6e2 yr, static, evolved 2e5 yr, followed by LIME LTE radiative transfer  
  > "calculated the chemical abundances, including o-H$_2$D$^+$, by evolving a chemical reaction network for 2$\times$10$^5$ years." (4 Discussion)

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

- task: tclean  
  > "The `tclean` task was performed with the multi-scale deconvolver, and clean masks were manually selected." (2 Observations)
- deconvolver: multi-scale  
  > "The `tclean` task was performed with the multi-scale deconvolver" (2 Observations)
- weighting robust: natural weighting  
  > "Imaging was carried out with natural weighting to maximize sensitivity." (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: manual masks; none for non-detections  
  > "some sources were not detected with the 7 m array, and for those cases, mask regions were not selected." (2 Observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 7 m and TP analyzed independently, not combined  
  > "the 7 m array data and the TP array data were analyzed independently without combining the two datasets." (2 Observations)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- Calibration approach (pipeline vs manual), flux calibrators and flux uncertainty
- Multiscale scales, cell and image size
- Continuum subtraction and line-free channels
- Mask definitions for MC 35-mm
- Phase centers/coordinates of targets
- TP imaging procedure
- Chemical network initial conditions and LIME setup
- Integrated intensity velocity ranges

## Analysis recipe

1. **Image 7 m and TP data**: tclean multi-scale, natural weighting, 0.05 km/s channels; 7 m and TP analyzed separately  
  > "The velocity grid was set to 0.05 km s$^{-1}$ for imaging." (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive N(H2) from 0.83 mm continuum peak**: Optically thin dust emission at peak with assumed Td and kappa  
  > "corresponds to an $N_{\rm H_2}$ of $6 \times10^{22}$ cm$^{-2}$ assuming $T_{\rm d}$ = 7 K" (3 Results)
   - assumption: Td=7 K, kappa0.8mm=0.01 cm2/g; MC 27 Td=9 K after subtracting 4 mJy disk  
  > "assumpsion of $T_{\rm d}$ = 9 K, which is the same as $T_{\rm ex}$ of ortho-H$_2$D$^{+}$" (3 Results)
   - fitting: _not stated_
   - validation: _not stated_
3. **o-H2D+ column density and abundance (upper limits)**: LTE with Tex, dv=0.1 km/s, Tb limit, ratio to N(H2) at same position and beam  
  > "Assuming the LTE (local thermodynamic equilibrium) condition with an excitation temperature ($T_{\rm ex}$) of 7 K" (3 Results)
   - parameter: dv=0.1 km/s (2 channels), Tb=0.3 K limit for L1544  
  > "using $\Delta v$ = 0.1 km s$^{-1}$ (= 2 channels) and $T_{\rm b}$ = 0.3 K as the observed upper limit" (3 Results)
   - assumption: LTE; Tex 7 K (L1544, MC 35-mm), 9 K (MC 27)  
  > "Assuming an excitation temperature of $T_{\rm ex} = 9$ K (cite: Caselli_2008)" (3 Results)
   - fitting: _not stated_
   - validation: _not stated_
4. **Chemical + radiative transfer modelling**: Chemical network on static collapse-model profiles, then LIME LTE to compute o-H2D+ brightness  
  > "LTE radiative transfer simulations were performed with LIME code (cite: Brinch_2010) to compute the ortho-H$_2$D$^+$ peak brightness temperature distribution." (4 Discussion)
   - software: LIME
   - assumption: static physical structure at each radius, 2e5 yr  
  > "we assumed a static physical structure" (4 Discussion)
   - fitting: _not stated_
   - validation: Qualitative only; absolute intensities not matched  
  > "the absolute values of H$_2$D$^+$ intensity do not necessarily match the present observations." (4 Discussion)

## Software

- **CASA** v6.6.4-34: data reduction and imaging  
  > "We used the Common Astronomy Software Application package (cite: CASA_2022), v6.6.4-34, for data reduction." (2 Observations)
- **LIME** : LTE radiative transfer of model  
  > "LTE radiative transfer simulations were performed with LIME code (cite: Brinch_2010)" (4 Discussion)
- **astropy** : listed in software section  
  > "astropy (cite: Astropy18), CASA (cite: CASA_2022)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| L1544 peak 0.87 mm continuum | 7 | not stated | mJy/beam | 1 | The 0.87 mm continuum intensity at the peak is measured to be 7 mJy beam$^{-1}$ |
| L1544 N(H2) | 6e22 | not stated | cm-2 | 2 | corresponds to an $N_{\rm H_2}$ of $6 \times10^{22}$ cm$^{-2}$ |
| L1544 N(o-H2D+) upper limit | <1e12 | not stated | cm-2 | 3 | is calculated to be $<$1 $\times$10$^{12}$ cm$^{-2}$ |
| L1544 [o-H2D+]/[H2] upper limit | <~2e-11 | not stated | dimensionless | 3 | to be $\lesssim 2 \times 10^{-11}$ |
| MC 35-mm o-H2D+ peak | 0.35 (3.5 sigma) | not stated | K | 1 | revealing a $\sim$0.35 K (=3.5$\sigma$) detection |
| MC 35-mm N(o-H2D+) | ~1e12 | not stated | cm-2 | 3 | $N_{\rm o-H_2D^+}\sim1\times10^{12}$ cm$^{-2}$ |
| MC 35-mm [o-H2D+]/[H2] | 3e-11 | not stated | dimensionless | 3 | The resulting abundance ratio of \[ortho-H$_2$D$^{+}$\]/\[H$_2$\] is $3 \times 10^{-11}$. |
| MC 27 N(H2) | ~9e22 | not stated | cm-2 | 2 | we estimate the H$_2$ column density to be $N$(H$_2$) $\sim 9 \times10^{22}$ cm$^{-2}$ |
| MC 27 [o-H2D+]/[H2] upper limit | <~7e-12 | not stated | dimensionless | 3 | $\lesssim$7 $\times$10$^{-12}$ |

## Qualitative findings

- o-H2D+ detected with TP in all three cores but 7 m only toward MC 35-mm, implying extended distribution resolved out by the interferometer.  
  > "These results suggest that ortho-H$_2$D$^+$ predominantly exhibits an extended distribution over several thousand au in the early stages of star formation." (abstract)

## Claim tuples

- H: Is o-H2D+ a compact tracer of dense core centers near star formation? | E: ACA 7 m and TP observations of three Taurus cores | R: 7 m detection only in MC 35-mm (~3 sigma); upper limits ~1e-11 elsewhere; TP detections in all | F: o-H2D+ is mostly extended; compact detection only close to protostar formation | **supported**
- H: Chemistry explains the lack of central o-H2D+ in prestellar cores | E: Chemical network plus LIME on collapse model | R: H2D+ shallower than N(H2) in prestellar model; first-core model slightly more concentrated | F: Qualitatively consistent with observations | **partially**

## Reasoning

- Why this data: Spatial filtering makes 12 m unsuitable; ACA stand-alone chosen for few-arcsec structures  
  > "observations using the 12 m array are not necessarily the ideal option due to spatial filtering effects." (Introduction)
- Why this method: _not stated_
- Alternative: Spatial/spectral smoothing of MC 35-mm data gave no significant S/N improvement  
  > "we attempted spatial and spectral smoothing to improve the signal-to-noise ratio, but no significant enhancement was obtained." (3 Results)
- How they decided it was enough: _not stated_
- Limitation (authors): MC 35-mm detection marginal; model absolute intensities not matched  
  > "This suggests that, even if the emission is real, it is confined to a very narrow range both spatially and in velocity." (3 Results)
- Caveat (inferred, ours): MC 35-mm detection only ~3 sigma
- Caveat (inferred, ours): Single Tex and Td assumptions drive abundance limits
- Caveat (inferred, ours): Chemical model is static and only qualitative
- Caveat (inferred, ours): No 7m+TP combination

## Reproducibility

- Data public (paper): Project code given; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO. ALMA#2023.1.00225.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters (scales, cell, size, masks)
- Missing: Integrated-intensity velocity windows
- Missing: Chemical/LIME model setup details
- Data volume (inferred): tens of GB
- Score (inferred): 3/5, Data identified and key assumptions listed, but imaging and model details are sparse.
- Rediscovery candidate: no, Recipe lacks imaging/calibration details and the main detection is marginal; data public status unclear.

## Links

- Method: (cite: Furuya_2015) (chemical network used)
- Method: (cite: Brinch_2010) (LIME code)
- Companion: (cite: Fujishiro_2020) (MC 35-mm first core candidate)
- Companion: (cite: Caselli_2019) (L1544 ALMA continuum)
- Related: 2016.1.00240.S

## Checks

```json
{
 "quotes": 57,
 "quotes_ok": 57,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2016.1.00240.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 40,
  "rate": 0.526
 },
 "evidence_ok": true
}
```
