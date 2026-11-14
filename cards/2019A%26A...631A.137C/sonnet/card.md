# The ALMA-PILS survey: propyne (CH<SUB>3</SUB>CCH) in IRAS 16293-2422

`2019A&A...631A.137C` | Astronomy and Astrophysics 2019 | first author: Calcutt, H. | arXiv: 1909.13329 | DOI: 10.1051/0004-6361/201936323

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: astrochemistry, star_formation
- Question: What are the abundances, excitation temperatures and spatial scales of CH3CCH towards IRAS 16293A and B, and which gas-phase and grain-surface reactions form it?  
  > "This study explores the emission of CH$_3$CCH in the low-mass protostellar binary, IRAS 16293–2422, examining the spatial scales traced by this molecule, as well as its formation and destruction pathways." (abstract)
- Target **IRAS 16293A**: coordinates extraction position α=16h32m22.90s, δ=−24°28'36.2"  
  > "IRAS 16293 is a low-mass protostellar binary, located at a distance of 141 pc (cite: Dzib2018)." (Introduction); "This is offset from the peak continuum position of IRAS 16293A by 0.6$''$ (85 au), in the north east direction." (Observational results and analysis); z/distance 141 pc  
  > "IRAS 16293 is a low-mass protostellar binary, located at a distance of 141 pc (cite: Dzib2018)." (Introduction); "This is offset from the peak continuum position of IRAS 16293A by 0.6$''$ (85 au), in the north east direction." (Observational results and analysis); distance from Dzib et al. 2018  
  > "IRAS 16293 is a low-mass protostellar binary, located at a distance of 141 pc (cite: Dzib2018)." (Introduction); "This is offset from the peak continuum position of IRAS 16293A by 0.6$''$ (85 au), in the north east direction." (Observational results and analysis)
- Target **IRAS 16293B**: coordinates extraction position α=16h32m22.58s, δ=−24°28'32.8"  
  > "This is offset from the continuum peak position of IRAS 16293B in the south west direction by one beam (0.5$''$, 70 au)." (Observational results and analysis); z/distance 141 pc  
  > "This is offset from the continuum peak position of IRAS 16293B in the south west direction by one beam (0.5$''$, 70 au)." (Observational results and analysis); distance from Dzib et al. 2018  
  > "This is offset from the continuum peak position of IRAS 16293B in the south west direction by one beam (0.5$''$, 70 au)." (Observational results and analysis)

## Data provenance

- ALMA projects: 2013.1.00278.S, 2012.1.00712.S
- bands: Band 7 (329.147–362.896 GHz) and Band 3 used  
  > "The survey covers Band 7 between 329.147 and 362.896 GHz, and selected frequency windows in Bands 3 and 6. For the purposes of this study the Band 7 and Band 3 data are used." (Observations)
- frequencies and spectral setup: Band 3: four basebands, 89.5–89.7, 92.8–92.9, 102.5–102.7, 103.2–103.4 GHz; 0.4 km/s resolution  
  > "The Band 3 data cover four basebands, spanning the frequency ranges 89.5 – 89.7 GHz, 92.8 – 92.9 GHz, 102.5 – 102.7 GHz, and 103.2 – 103.4 GHz." (Observations)
- continuum bandwidth: _not stated_
- arrays: Band 7: 12 m array plus ACA  
  > "The Band 7 data are a combination of 12 m array and Atacama Compact Array (ACA) observations" (Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Band 7 restoring beam 0.5" at 0.2 km/s resolution  
  > "which have been combined to have a restoring beam of 0.5$''$ at a spectral resolution of 0.2 km s$^{-1}$" (Observations)
- max recoverable scale: Band 7: 13" (1820 au); Band 3: 17" (2380 au)  
  > "They probe spatial scales of 1.4$''$ (196 au) to 17$''$ (2380 au)" (Observations)
- sensitivity: Band 7: 7–10 mJy/beam/channel (~5 mJy/beam km/s); Band 3: ~5 mJy/beam km/s  
  > "They reach a sensitivity of about 7 – 10 mJy beam$^{-1}$ channel$^{-1}$, i.e. approximately $\sim$5 mJy beam$^{-1}$ km s$^{-1}$ across the entire frequency range." (Observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CH3CCH J=6–5 K ladder (Band 3), J=20–19 and 21–20 K ladders (Band 7) (102.53–102.55, 341.51–341.74, 358.57–358.82 GHz)
- Other facility **IRAM 30 m (literature)**: Single-dish CH3CCH spectra from Andron et al. 2018 used for comparison  
  > "the IRAM 30 m observations are $\sim$50% brighter than the CH$_3$CCH emission found in the the PILS convolved observations" (3.2 Spatial extent)
- External data: H2 column densities: >1.2e25 cm-2 toward B, 6.3e24 cm-2 toward A  
  > "H$_2$ column densities are based on the values determined in (cite: Jorgensen2016) towards IRAS 16293B ($>$1.2$\times$10$^{25}\,$cm$^{-2}$)" (Table 3 notes) [from Jorgensen2016; Calcutt2018a]
- External data: Spectroscopic data from CDMS catalogue  
  > "Rest frequencies and related information on CH$_3$CCH, CH$_2$DCCH and CH$_3$CCD were taken from the CDMS catalogue (cite: Endres2016)." (Observational results and analysis) [from Endres2016]
- External data: Distance 141 pc  
  > "located at a distance of 141 pc (cite: Dzib2018)" (Introduction) [from Dzib2018]
- Simulation/model as data: MAGICKAL three-phase chemical models at final nH = 1.6e7, 6e8, 6e9, 6e10 cm-3  
  > "four models have been run to explore the solid-phase and gas-phase abundances of CH$_3$CCH at different final densities" (4 Chemical modelling)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: better than 5% (Band 7)  
  > "The flux calibration errors on the Band 7 dataset were estimated to be better than 5% by (cite: Jorgensen2016)." (3.1)
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
- smoothing: Convolved with a 24" beam in CASA for comparison with IRAM 30 m  
  > "was used to convolve the PILS data with a 24$''$ beam" (3.2 Spatial extent)
- final beam: Band 7 restoring beam 0.5"  
  > "restoring beam of 0.5$''$" (Observations)
- final rms: _not stated_

### Inherited from earlier work

- Data reduction and continuum subtraction follow the PILS survey paper  
  > "Further details of the PILS datasets and the reduction and the continuum subtraction procedure can be found in (cite: Jorgensen2016)." (Observations) [from Jorgensen2016]
- VINE map construction follows earlier work  
  > "Further details of how these maps are produced and a comparison between a VINE map and a standard integrated emission map for IRAS 16293 can be found in (cite: Calcutt2018b)." (3.2 Spatial extent) [from Calcutt2018b]
- FWHM and Vpeak ranges based on previous analyses at the same positions  
  > "The range in FWHMs and peak velocities modelled was based on previous analysis towards each of the offset positions used in this work" (3.1) [from Calcutt2018b; Manigand2019]

### Not stated but needed to reproduce (our reading)

- Grid step sizes for Ntot, Tex, FWHM and Vpeak in CASSIS
- Exact spectrum extraction aperture
- CASA version and convolution details
- Exact VINE map velocity maps and pixel-level parameters
- MAGICKAL network files and code availability
- Method of error estimation by varying Ntot and Tex

## Analysis recipe

1. **Extract spectra at offset positions**: Spectra extracted at positions offset from the continuum peaks of B and A to avoid absorption and blending  
  > "Spectra were extracted from two positions, where line emission is bright, does not have strong absorption features and does not suffer from high continuum optical depth" (Observational results and analysis)
   - fitting: _not stated_
   - validation: _not stated_
2. **LTE fit for Tex and Ntot**: Grid of LTE models in CASSIS, reduced chi2 minimum; severely blended lines excluded; second grid with optically thin lines (tau<0.2)  
  > "The reduced $\chi^2$ minimum was then computed to determine the best fit model" (3.1); "a second grid of models was performed, where only the optically thin lines ($\tau<$0.2) were used to determine the best fit model" (3.1)
   - software: CASSIS
   - parameter: Ntot 5e13–5e18 cm-2; Tex 80–300 K; FWHM 2.0–2.6 (A), 0.8–1.2 (B) km/s  
  > "Column densities were varied between 5$\times$10$^{13}$ – 5$\times$10$^{18}$ cm$^{-2}$, and excitation temperatures between 80 – 300 K." (3.1)
   - assumption: LTE; source sizes 1.4"/1.1" (A/B) for Band 7 and 1.6"/1.7" for Band 3  
  > "assuming a source size of 1.4$''$ and 1.1$''$ for A and B respectively, for the higher upper energy lines in Band 7" (3.1)
   - fitting: Grid search with reduced chi2 minimisation, including RMS and flux calibration error  
  > "Both the flux calibration error and the root mean square (RMS) are used by CASSIS when determining the best fit model." (3.1)
   - validation: Band 3 and Band 7 fitted independently then combined; similar parameters  
  > "All of the best fit parameters were similar for each source independent of which dataset was modelled." (3.1)
3. **Isotopologue upper limits**: 3 sigma limits 1.05×3×RMS×sqrt(ΔV×FWHM) using the CH3CCH Tex  
  > "The upper limits are determined from $1.05{\times}3{\times}RMS{\times}\sqrt{{\Delta}V{\times}FWHM}$ to compute the 3$\sigma$ limit" (3.1)
   - parameter: Line widths 2 km/s (A) and 1 km/s (B)  
  > "Line widths of 2 km s$^{-1}$ and 1 km s$^{-1}$ are used for IRAS 16293A and IRAS 16293B, respectively." (3.1)
   - fitting: _not stated_
   - validation: Consistent with isotopic ratios from previous works  
  > "The upper limit column densities values are found to be consistent with the isotopic ratios that have been determined in both sources by previous works" (3.1)
4. **Measure spatial extent**: VINE integrated-emission maps; FWHM of 2D Gaussian fitted to emission  
  > "The values were calculated by determining the FWHM of a 2D-Gaussian fitted to the emission of each source." (3.2 Spatial extent)
   - parameter: VINE velocity interval 3.2 km/s (A), 1.2 km/s (B)  
  > "The velocity interval used is 3.2 km s$^{-1}$ and 1.2 km s$^{-1}$ for IRAS 16293 A and IRAS 16293B, respectively." (3.2 Spatial extent)
   - assumption: Distance 141 pc  
  > "The spatial extent in au is calculated for a source distance of 141 pc" (Table 2 notes)
   - fitting: _not stated_
   - validation: _not stated_
5. **Compare with IRAM 30 m**: Convolve PILS Band 3 data to 24" beam and compare with Andron et al. spectra  
  > "was used to convolve the PILS data with a 24$''$ beam, to determine how much of the emission from the hot corino components could explain the emission detected in the IRAM 30 m observations" (3.2 Spatial extent)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
6. **Chemical modelling**: MAGICKAL three-phase model: cold collapse then warm-up to 400 K at four final densities  
  > "This is then followed by a static warm-up to 400 K." (4 Chemical modelling)
   - software: MAGICKAL
   - parameter: zeta = 1.3e-17 s-1; collapse 1.63e6 yr; warm-up reaching 400 K at 2.8e5 yr  
  > "The cosmic-ray ionisation rate, $\zeta$, is assumed to be 1.3$\times$10$^{-17}$ s$^{-1}$" (4 Chemical modelling)
   - assumption: Single-point uniform density; gas 10 K, dust 16 to 8 K in collapse  
  > "The chemical model is a single-point model, thus it has a uniform density." (4 Chemical modelling)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASSIS** : LTE synthetic spectra and grid fitting  
  > "The spectral modelling software CASSIS[^1] was used to calculate synthetic spectra and determine best fit spectral models" (3.1)
- **CASA** : Convolving PILS data to 24" beam  
  > "The Common Astronomy Software Applications package (CASA; (cite: Casa)) was used to convolve the PILS data with a 24$''$ beam" (3.2 Spatial extent)
- **MAGICKAL** : Three-phase chemical kinetics modelling  
  > "The three-phase chemical kinetics model *MAGICKAL* (cite: Garrod2013; Willis2017) was used to model the formation and destruction pathways of CH$_3$CCH." (4 Chemical modelling)
- **Astropy** : Acknowledged as used  
  > "This research has also made use of Astropy" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Tex IRAS 16293A | 90 | ±30 | K | 2 | / IRAS 16293A / 90$\pm$30 / 7.8$\pm$1.0$\times$10$^{15}$ / 1.2$\times$10$^{-9}$ / 2.0$\pm$0.2 / 1.0$\pm$0.2 / |
| Ntot IRAS 16293A | 7.8e15 | ±1.0e15 | cm-2 | 2 | / IRAS 16293A / 90$\pm$30 / 7.8$\pm$1.0$\times$10$^{15}$ / 1.2$\times$10$^{-9}$ / 2.0$\pm$0.2 / 1.0$\pm$0.2 / |
| Tex IRAS 16293B | 100 | ±20 | K | 2 | / IRAS 16293B / 100$\pm$20 / 6.8$\pm$0.2$\times$10$^{15}$ / $<$5.7$\times$10$^{-10}$ / 1.0$\pm$0.2 / 2.5$\pm$0.2 / |
| Ntot IRAS 16293B | 6.8e15 | ±0.2e15 | cm-2 | 2 | / IRAS 16293B / 100$\pm$20 / 6.8$\pm$0.2$\times$10$^{15}$ / $<$5.7$\times$10$^{-10}$ / 1.0$\pm$0.2 / 2.5$\pm$0.2 / |
| CH3CCH/H2 in A | 1.2e-9 | not stated | dimensionless | 2 | / IRAS 16293A / 90$\pm$30 / 7.8$\pm$1.0$\times$10$^{15}$ / 1.2$\times$10$^{-9}$ / |
| Spatial extent FWHM, 6 1–5 1 in A | 1.7 (233 au) | not stated | arcsec | 4 | /  CH$_3$CCH 6 1 – 5 1  /     24 K     /       1.7$''$ 233 au       / |
| Spatial extent FWHM, 20 3–19 3 in B | 1.0 (145 au) | not stated | arcsec | 4 | / CH$_3$CCH 20 3 – 19 3 /     237 K     /       1.0$''$ 145 au       / |
| Upper limit CH3CCD in A and B | <7.91e14 | not stated | cm-2 | 3 | /    CH$_3$CCD     / $<$7.91$\times$10$^{14}$ / $<$1.26$\times$10$^{-10}$ / |

## Qualitative findings

- IRAM 30 m emission is ~50% brighter than the convolved PILS emission, implying an extra cold extended component filtered out by PILS  
  > "This suggests there is an additional cold component of CH$_3$CCH emission that is detected in the IRAM 30 m observations" (3.2 Spatial extent)

## Claim tuples

- H: CH3CCH traces the hot corino around each protostar with similar properties | E: LTE fits and 2D Gaussian size of VINE maps | R: Tex 90 K (A) and 100 K (B); sizes ~1–2" (145–260 au) | F: CH3CCH traces the hot corino components in both sources | **supported**
- H: IRAM 30 m emission could be explained by the hot corinos alone | E: Convolve PILS Band 3 data to 24" and compare | R: Convolved PILS is ~50% weaker than IRAM | F: An additional cold extended component exists | **supported**
- H: Both gas-phase and grain-surface routes are needed to form CH3CCH | E: MAGICKAL models at four densities | R: Grain hydrogenation plus gas-phase recombination tied to CH4 desorption | F: Both pathways are required | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Offset positions avoid blending and absorption at the continuum peaks  
  > "to overcome issues of line blending and absorption contamination which affect the peak continuum position" (Observational results and analysis)
- How they decided it was enough: _not stated_
- Limitation (authors): Line blending and optically thick lines affect fit quality  
  > "Line blending and optically thick lines can significantly impact the quality of the fit." (3.1)
- Caveat (inferred, ours): Chemical model is single-point and not fitted quantitatively to the observations
- Caveat (inferred, ours): Errors on Tex and Ntot estimated informally
- Caveat (inferred, ours): The IRAM comparison uses a figure from another paper with absorption-contaminated lines

## Reproducibility

- Data public (paper): Acknowledges ALMA project data; PILS survey data  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00278.S and ADS/JAO.ALMA#2012.1.00712.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Reduced PILS cubes (need PILS release or reprocessing)
- Missing: CASSIS grid steps
- Missing: MAGICKAL code and network
- Data volume (inferred): Large (hundreds of GB raw; PILS cubes tens of GB)
- Score (inferred): 3/5, Data are public and the LTE fit is described, but reduced cubes, grid steps and model code are not provided.
- Rediscovery candidate: no, Requires PILS reduced products and several unstated settings, and part of the results come from a chemical model.

## Links

- Method: Jorgensen2016 (PILS survey description, reduction and continuum subtraction)
- Method: Calcutt2018b (VINE map method)
- Companion: Andron2018 (IRAM 30 m CH3CCH observations compared with PILS)
- Related: PILS (Protostellar Interferometric Line Survey)

## Checks

```json
{
 "quotes": 67,
 "quotes_ok": 67,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 85,
  "stated": 48,
  "rate": 0.565
 },
 "evidence_ok": true
}
```
