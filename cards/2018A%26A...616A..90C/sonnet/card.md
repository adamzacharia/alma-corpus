# The ALMA-PILS survey: complex nitriles towards IRAS 16293-2422

`2018A&A...616A..90C` | Astronomy and Astrophysics 2018 | first author: Calcutt, H. | arXiv: 1804.09210 | DOI: 10.1051/0004-6361/201732289

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: astrochemistry, star_formation
- Question: What is the inventory, abundance, excitation, isotopic ratios and spatial extent of complex nitriles towards the two hot corino sources IRAS 16293A and B?  
  > "The goal of this work is to determine the inventory of one family of nitrogen-bearing organic molecules, complex nitriles (molecules with a –C$\equiv$N functional group) towards two hot corino sources in the low-mass protostellar binary IRAS 16293–2422." (abstract)
- Target **IRAS 16293-2422 A and B**: coordinates Analysis positions: B offset 16h32m22.58s, -24d28m32.8s; A offset 16h32m22.90s, -24d28m36.2s (J2000)  
  > "relatively close location (120 pc; (cite: Loinard2008))" (1 Introduction); "The second position is offset by 0.6$''$ (68 AU) north east from the peak continuum position." (2 Observations); z/distance 120 pc  
  > "relatively close location (120 pc; (cite: Loinard2008))" (1 Introduction); "The second position is offset by 0.6$''$ (68 AU) north east from the peak continuum position." (2 Observations); distance from Loinard et al. 2008  
  > "relatively close location (120 pc; (cite: Loinard2008))" (1 Introduction); "The second position is offset by 0.6$''$ (68 AU) north east from the peak continuum position." (2 Observations)

## Data provenance

- ALMA projects: 2013.1.00278.S
- bands: Band 7  
  > "30 hours of observations with the Atacama Compact Array (ACA; typically 8–10 antennas) in band 7, between 329.147 GHz and 362.896 GHz." (2 Observations)
- frequencies and spectral setup: 329.147-362.896 GHz, 0.2 km/s resolution  
  > "between 329.147 GHz and 362.896 GHz" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: Main array (15 h, 36-41 antennas) plus ACA (30 h, 8-10 antennas)  
  > "The data are a combination of 15 hours of observations with the main array (typically 36–41 antennas in the array at the time of observations)" (2 Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.5 arcsec circular restoring beam  
  > "produced with a circular restoring beam of 0.5$''$ at a spectral resolution of 0.2 km s$^{-1}$" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: RMS 7-10 mJy/beam/channel (0.2 km/s)  
  > "an RMS of about 7–10 mJy beam$^{-1}$ channel$^{-1}$, i.e. approximately 4–5 mJy beam$^{-1}$ km s$^{-1}$" (2 Observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CH3CN and isotopologues (v8=1, 13C, 15N, D) multiple, e.g. J=19-18, 20-19 K ladders (329-362 GHz)
- Line: C2H5CN, C2H3CN, HC3N multiple (329-362 GHz)
- External data: Methanol column densities (via CH3 18OH x 560) used as reference abundance  
  > "For methanol the column densities are taken from (cite: Jorgensen2016) and Jørgensen et al. (subm.) for IRAS 16293B and Manigand et al. (in prep.) for IRAS 16293A" (3.2 Relative abundances) [from Jørgensen 2016 (cite: Jorgensen2016); Jørgensen et al. subm.; Manigand et al. in prep.]
- External data: Sgr B2(N2) nitrile abundances for comparison  
  > "the abundance of nitriles with respect to methyl cyanide determined in Sgr B2(N2) by (cite: Belloche2016) is plotted" (4.3) [from (cite: Belloche2016)]
- External data: ISM 12C/13C ratio 68±15  
  > "similar to the ISM value of 68$\pm15$ ((cite: Milam2005))" (3.3) [from (cite: Milam2005)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 5% flux calibration uncertainty  
  > "1.05 is a factor to account for a 5% flux calibration uncertainty" (3.1)
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
- continuum subtraction: Described in Jørgensen et al. 2016  
  > "Further details of the data reduction and continuum subtraction procedure can be found in (cite: Jorgensen2016)." (2 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.5 arcsec circular  
  > "circular restoring beam of 0.5$''$" (2 Observations)
- final rms: 7-10 mJy/beam/channel  
  > "an RMS of about 7–10 mJy beam$^{-1}$ channel$^{-1}$" (2 Observations)

### Inherited from earlier work

- Data reduction and continuum subtraction  
  > "Further details of the data reduction and continuum subtraction procedure can be found in (cite: Jorgensen2016)." (2 Observations) [from Jørgensen et al. 2016 (cite: Jorgensen2016)]
- Correction for dust/gas decoupling of continuum background (1.14 at B, 1.24 at A at 125 K)  
  > "The correction is calculated as in (cite: Jorgensen2016) and is 1.14 at 125 K towards the B position and 1.24 at 125 K towards the A position." (3) [from (cite: Jorgensen2016)]

### Not stated but needed to reproduce (our reading)

- Calibration pipeline/CASA version and self-calibration details
- Clean parameters and weighting used for the combined PILS cubes
- Line-free channels and continuum subtraction specifics
- Grid step sizes for Tex, N, FWHM and Vpeak in CASSIS
- Exact method to compute the velocity map and channels integrated for VINE maps
- How the error bars were quantified

## Analysis recipe

1. **Extract spectra at offset positions**: Spectra extracted at positions offset from continuum peaks of A and B to limit blending and absorption  
  > "The spectral analysis presented in this work is performed towards two positions" (2 Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **LTE spectral modelling for Tex and N**: Grid of LTE models in CASSIS; best fit by minimum reduced chi2; blended and optically thick lines excluded  
  > "A large grid of models was run to determine the best fit excitation temperature, $FWHM$, velocity peak $V\rm{_{peak}}$, and column density for each molecule." (3)
   - software: CASSIS, CDMS
   - parameter: Tex 90-300 K; N 1e13-1e17 cm-2; FWHM 1.8-2.4 (A), 0.8-1.2 (B) km/s  
  > "Excitation temperatures of 90 – 300 K are explored for both sources." (3)
   - parameter: Only optically thin lines (tau<0.2) used  
  > "only optically thin lines ($\tau$\<0.2) are used to determine the best fit model" (3)
   - assumption: LTE, source size 0.5 arcsec, Gaussian profiles, continuum as background temperature  
  > "All models assume LTE and a source size of 0.5$''$." (Table 1 notes)
   - fitting: Reduced chi2 minimum over grid; for CH3CN species Tex fixed to average from fit of CH3C15N and CHD2CN  
  > "We then performed a second fit for all methyl cyanide species to determine their column densities with a fixed excitation temperature of the average determined from the first fit." (3.1)
   - validation: Errors estimated by varying Ntot and Tex and checking the fit  
  > "We estimate the errors, based on varying the $N_{\rm tot}$ and $T_{\rm ex}$ to determine the impact this has on the fit of the observations." (3)
3. **Upper limit for vinyl cyanide towards A**: 3 sigma limit on 331.087 GHz line, 1sigma=1.05 x RMS x sqrt(dV x FWHM); tested Tex 50-500 K  
  > "using $1.05{\times}RMS{\times}\sqrt{{\Delta}V{\times}FWHM}$ to compute the 1$\sigma$ limit" (3.1)
   - software: CASSIS
   - fitting: _not stated_
   - validation: Higher-Tex limits overproduced emission in other lines  
  > "plotting these column densities with CASSIS led to a clear overproduction of emission for some lines" (3.2)
4. **Relative abundances and isotopic ratios**: Column density ratios relative to CH3CN (from v8=1) and methanol; isotopic ratios from isotopologue/CH3CN with statistical correction for D/H  
  > "the column density of the excited (v$_8$=1) state of methyl cyanide is used to compute the $^{12}$C/$^{13}$C, the $^{14}$N/$^{15}$N, and the D/H ratios" (3.3)
   - assumption: 16O/18O = 560 for methanol  
  > "multiplied by the standard $^{16}$O/$^{18}$O ISM value of 560 (cite: Wilson1994)" (3.2)
   - fitting: _not stated_
   - validation: _not stated_
5. **Make VINE maps**: Velocity map from methanol 7(3,5)-6(4,4) line at 337.519 GHz gives per-pixel centroid channel; integrate channels either side for unblended lines  
  > "We then use this velocity map to determine the centroid channel for a given transition in each pixel, integrating over several channels either side to cover the whole spectral profile." (3.4)
   - fitting: _not stated_
   - validation: Compared with uncorrected 6 km/s integrated map for 13CH3CN 339.360 GHz  
  > "The first map is the emission integrated over 6 km s$^{-1}$." (3.4)

## Software

- **CASSIS** : LTE spectral modelling and fitting  
  > "the spectral modelling software CASSIS[^2] has been used to compute the best fit spectral models" (3)
- **CDMS catalogue** : Line lists  
  > "Line lists for each of the molecules discussed in this work were taken from the CDMS catalogue[^3]." (3)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CH3CN (v8=1) column density, IRAS 16293A | 8.0e16 | 1.0e16 | cm-2 | 2 | / CH$_3$CN$^{\dagger}$ / 120 (10) / 8.0 (1.0)$\times$10$^{16}$ / 1 / |
| CH3CN (v8=1) column density, IRAS 16293B | 4.0e16 | 1.0e16 | cm-2 | 2 | / CH$_3$CN$^{\dagger}$ / 110 (10) / 4.0 (1.0)$\times$10$^{16}$ / 1 / |
| Tex CH3CN, A / B | 120 / 110 | 10 | K | 2 | / CH$_3$CN$^{\dagger}$ / 110 (10) / 4.0 (1.0)$\times$10$^{16}$ / 1 / |
| C2H5CN column density A / B | 9.0e15 / 3.6e15 | 0.2e15 (A), 0.2e15 (B) | cm-2 | 2 | / C$_2$H$_5$CN / 140 (10) / 9.0 (0.2)$\times$10$^{15}$ / 0.113 / |
| C2H3CN column density B | 7.4e14 | 0.2e14 | cm-2 | 2 | / C$_2$H$_3$CN / 110 (10) / 7.4 (0.2)$\times$10$^{14}$ / 0.019 / |
| C2H3CN upper limit A | <=2.4e14 | 3 sigma limit | cm-2 | 3 | / C$_2$H$_3$CN / 150 (10) / $\leq$2.4$\times$10$^{14\dagger\dagger}$ / $\leq$0.002$^{\dagger\dagger}$ / |
| CHD2CN column density A / B | 2.2e14 / 2.0e14 | 0.5e14 / 0.2e14 | cm-2 | 2 | / CHD$_2$CN / 120 (10) / 2.2 (0.5)$\times$10$^{14}$ / 0.003 / |
| 14N/15N A / B | 235 / 250 | 33 / 70 | dimensionless | 4 | /    $^{14}$N/$^{15}$N    /  235$\pm$33  /  250$\pm$70  / |
| 12C/13C (13CH3CN) A / B | 80 / 67 | 19 / 17 | dimensionless | 4 | /  80$\pm$19   /  67$\pm$17   / |
| D/H from CH2DCN A / B | 1.5% / 1.2% | 0.3% | percent | 4 | /    D/H(D1,D0)$^{b}$     / 1.5$\pm$0.3% / 1.2$\pm$0.3% / |
| D/H from CHD2CN A / B | 3.0% / 4.0% | 0.3% / 0.5% | percent | 4 | /    D/H(D2,D0)$^{b}$     / 3.0$\pm$0.3% / 4.0$\pm$0.5% / |
| C2H5CN/C2H3CN ratio B / A | 5 / >53 | not stated | dimensionless | 4 | In IRAS 16293B the ethyl cyanide to vinyl cyanide ratio is 5 while in IRAS 16293A it is \>53 |

## Qualitative findings

- First detection of CHD2CN in the ISM; double-peaked molecular emission in source A resolved for the first time  
  > "We also detect a spatially double-peaked emission for the first time in molecular emission in the A source" (abstract)

## Claim tuples

- H: Nitrile abundances differ between IRAS 16293A and B | E: LTE modelling of PILS spectra at offset positions | R: Relative abundances agree within 0.6-1.7 except vinyl cyanide, >=9x more abundant in B | F: Sources chemically similar on small scales; vinyl cyanide indicates different evolution or warm-up timescale | **supported**
- H: Isotopic ratios in methyl cyanide reflect ISM and deuterium enrichment | E: Ratios of isotopologue column densities | R: 12C/13C consistent with ISM 68±15; D/H 1.2-1.5% (singly) vs 3-4% (doubly) | F: Deuterium enrichment in doubly-deuterated form, possibly via H-D substitution | **partially**
- H: Velocity-corrected integration reveals spatial structure in source A | E: VINE maps from a methanol velocity map | R: Two emission peaks either side of the continuum peak in A | F: Double peak likely from rotating toroid, not multiple sources | **partially**

## Reasoning

- Why this data: Offset position chosen for bright lines without strong absorption or high continuum optical depth  
  > "This position is used as the lines are particularly bright, do not have strong absorption features towards the bright continuum of IRAS 16293B" (2 Observations)
- Why this method: _not stated_
- Alternative: Excitation-temperature explanation for vinyl cyanide difference in A rejected  
  > "We are therefore confident that the abundance differences for vinyl cyanide determined between IRAS 16293A and B are due to chemical differences and not excitation effects." (3.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Errors depend on LTE, optically thin and Gaussian assumptions; HC3N only 3 lines, two blended  
  > "which relies on the assumption of LTE, optically thin emission and Gaussian profiles" (3)
- Caveat (inferred, ours): Fixed 0.5 arcsec source size and LTE for both sources are assumptions that affect column densities
- Caveat (inferred, ours): Error bars from manual variation are not rigorous
- Caveat (inferred, ours): Offset positions may not represent whole sources
- Caveat (inferred, ours): Methanol reference values come from unpublished work

## Reproducibility

- Data public (paper): ALMA project 2013.1.00278.S cited; PILS website given  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00278.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Combined PILS imaged cubes (from Jørgensen 2016 reduction)
- Missing: Model grid step sizes
- Missing: VINE map implementation details
- Data volume (inferred): Large: combined 12m+ACA band 7 spectral cubes spanning 33 GHz; hundreds of GB raw
- Score (inferred): 3/5, Data public and LTE fit parameters tabulated, but reduction inherited and fitting details and VINE implementation vague.
- Rediscovery candidate: no, Requires the PILS reduced cubes and unstated fitting grid details; manual line selection and blending flags involved.

## Links

- Method: Jørgensen et al. 2016 (cite: Jorgensen2016) (PILS data reduction, continuum subtraction, dust-gas correction)
- Companion: Coutens et al. 2016; Ligterink et al. 2017; Manigand et al. in prep. (Other PILS molecular studies)
- Related: PILS
- Related: EMoCA
- Related: TIMASS

## Checks

```json
{
 "quotes": 60,
 "quotes_ok": 60,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 38,
  "rate": 0.528
 },
 "evidence_ok": true
}
```
