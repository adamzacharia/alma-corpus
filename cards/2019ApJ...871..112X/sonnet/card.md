# ALMA Observations of the Spatial Distribution of Three C<SUB>2</SUB>H<SUB>4</SUB>O<SUB>2</SUB> Isomers toward Sgr B2(N)

`2019ApJ...871..112X` | The Astrophysical Journal 2019 | first author: Xue, Ci | arXiv: 1812.07091 | DOI: 10.3847/1538-4357/aaf738

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: astrochemistry, star_formation
- Question: How do the spatial distributions and abundances of the three C2H4O2 isomers (glycolaldehyde, acetic acid, methyl formate) compare toward Sgr B2(N), using a uniform ALMA Band 3 data set and a quantitative selection of uncontaminated transitions?  
  > "we present an intensive and rigorous spectral and morphological analysis of the isomers towards Sgr B2(N) with interferometers, $ALMA$ Band 3 observations." (abstract)
- Target **Sgr B2(N) (LMH, N1, N2, N3)**: coordinates RA 17h47m19.87s, Dec -28d22m16s (J2000) field center  
  > "The phase center of the observations was pointed toward Sgr B2 with the field center at $\alpha_\text{J2000}=17\mathrm{h}47\mathrm{m}19.87\mathrm{s}$" (2 OBSERVATIONS); "The northern clump of Sgr B2(N) molecular cloud, which lies $\sim$120 pc from the Galactic center" (Introduction); z/distance ~120 pc from the Galactic center  
  > "The phase center of the observations was pointed toward Sgr B2 with the field center at $\alpha_\text{J2000}=17\mathrm{h}47\mathrm{m}19.87\mathrm{s}$" (2 OBSERVATIONS); "The northern clump of Sgr B2(N) molecular cloud, which lies $\sim$120 pc from the Galactic center" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00017.S, 2012.1.00012.S
- bands: Band 3  
  > "the observations were carried out in the same receiver band, ALMA Band 3" (3.1 Transition Selection Processes)
- frequencies and spectral setup: 5 setups (S1-S5), 4 spectral windows each, 84.1-114.4 GHz, 488.3 kHz resolution (1.29-1.70 km/s)  
  > "Each setup contains 4 spectral windows within the overall frequency range from 84.1 to 114.4 GHz." (2 OBSERVATIONS); "The spectral resolution was 488.3 kHz, which corresponds to a velocity resolution of 1.29 to 1.70 $\mathrm{km\ s^{-1}}$ across the observing band." (2 OBSERVATIONS)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: synthesized beam median ~1.6 arcsec; minimum 1.58 x 1.22 arcsec  
  > "The resulting size of the synthesized beam (HPBW) of each data cube has a medium value $\sim$ $1.6 \ensuremath{''}$." (2 OBSERVATIONS)
- max recoverable scale: _not stated_
- sensitivity: median rms 4.4 mJy/beam per channel  
  > "The median of resultant typical rms noise levels is 4.4 mJy beam$^{-1}$." (2 OBSERVATIONS)
- time on source: _not stated_
- observing dates: S1-S4 Cycle 0 (2012); S5 Cycle 1 (2014)  
  > "S1-S4 were performed during Cycle 0 (2012)" (2 OBSERVATIONS)
- pi or archival as stated: Archival EMoCA survey data from the ALMA Science Archive  
  > "The interferometric data used here were acquired from the ALMA Science Archive" (2 OBSERVATIONS)
- Line: Methyl formate (HCOOCH3, MF) 26 least contaminated transitions, v=0 and vt=1 (84-114 GHz)
- Line: Glycolaldehyde (CH2OHCHO, GLA) 10 least contaminated transitions (84-114 GHz)
- Line: Acetic acid (CH3COOH, AcA) 5 transitions (84-114 GHz)
- External data: Rest frequencies and spectral line parameters from CDMS, JPL and SLAIM catalogs  
  > "the rest frequencies and other spectral line parameters of the three isomers were taken from the above databases." (3.1) [from (cite: mssw2005), (cite: ppcd1998)]
- External data: Previous IRAM 30m Tex, column densities, source sizes for the isomers  
  > "(cite: bmmsc2013) suggest that $T_\text{ex}$ = 80 K and $N_{T,MF} = 4.37 \times 10^{17}\ \mathrm{cm}^{-2}$ with a source size of 4.0$\ensuremath{''}$ for MF" (3.3) [from (cite: bmmsc2013)]
- External data: Vlsr 64 km/s and dV ~7 km/s toward LMH used for simulations  
  > "constrained by previous studies to the values of 64 $\mathrm{km\ s^{-1}}$ for $V_\text{lsr}$ and $\sim$ 7 $\mathrm{km\ s^{-1}}$ for $\Delta V$" (3.1) [from (cite: bmcmso2008)]

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

- task: CASA used for imaging; spectral cubes  
  > "The Common Astronomy Software Applications package (CASA) (cite: mws2007) was used for imaging and analysis." (2 OBSERVATIONS)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "we used the Briggs scheme with a robust parameter of 0.5 and a cell size of $0.3 \ensuremath{''}$ for imaging." (2 OBSERVATIONS)
- uv taper: _not stated_
- cell size: 0.3 arcsec  
  > "we used the Briggs scheme with a robust parameter of 0.5 and a cell size of $0.3 \ensuremath{''}$ for imaging." (2 OBSERVATIONS)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: UV-plane subtraction using line-free channels  
  > "Afterwards, the ranges were used to subtract the continuum emission in the UV-plane before imaging the spectral cubes." (2 OBSERVATIONS)
- line free channels: selected per SPW from mean spectrum of CASA cube, technique of McGuire et al. 2017  
  > "the relatively line-free continuum channel ranges were selected with the techniques, as described in (cite: gswb2017), which are based on the mean spectrum generated from the CASA image cube." (2 OBSERVATIONS)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: median 4.4 mJy/beam  
  > "The median of resultant typical rms noise levels is 4.4 mJy beam$^{-1}$." (2 OBSERVATIONS)

### Inherited from earlier work

- Observations and data calibration  
  > "A detailed description of the observations and the data calibration was presented in (cite: bmgk2016)." (2 OBSERVATIONS) [from (cite: bmgk2016)]
- Line-free channel selection technique  
  > "the relatively line-free continuum channel ranges were selected with the techniques, as described in (cite: gswb2017)" (2 OBSERVATIONS) [from (cite: gswb2017)]
- Single-excitation LTE model convention  
  > "The single-excitation model follows the convention of (cite: hjlr2004) with corrections for optical depth as discussed in (cite: tur1991) and (cite: ms2015)." (3.1) [from (cite: hjlr2004), (cite: tur1991), (cite: ms2015)]

### Not stated but needed to reproduce (our reading)

- Calibration details (CASA version, calibrators, flux scale) are only in Belloche et al. 2016
- Continuum channel ranges per SPW not listed
- Image size and deconvolution settings (niter, threshold, masks) not given
- Aperture/pixel used to extract the LMH spectrum is given only as beam size and centroid; the Python simulation code is not released
- Primary beam correction and how moment-8 maps were made (masking, clipping) not specified
- Chemical-map stacking: how images were aligned/regridded to common beam not stated
- DME and ethanol chemical maps (transitions used) not detailed

## Analysis recipe

1. **Image cubes and subtract continuum**: Select line-free channels, subtract continuum in uv-plane, image with Briggs weighting  
  > "the ranges were used to subtract the continuum emission in the UV-plane before imaging the spectral cubes." (2 OBSERVATIONS)
   - software: CASA
   - parameter: robust 0.5, cell 0.3 arcsec  
  > "we used the Briggs scheme with a robust parameter of 0.5 and a cell size of $0.3 \ensuremath{''}$ for imaging." (2 OBSERVATIONS)
   - fitting: _not stated_
   - validation: _not stated_
2. **Simulate LTE spectra and select unblended transitions with P and D factors**: Single-Tex LTE spectra from catalogs compared with the LMH spectrum; P factor (frequency agreement) and D factor (intensity) computed over channels above 10% of simulated peak; thresholds P>90% (95% for MF), D>60%  
  > "we assign a transition with a $P$ factor at least larger than 90% and a $D$ factor larger than 60% to be an unblended transition candidate." (3.2)
   - software: Python program for simulating spectra (McGuire)
   - parameter: dV = 6.5 km/s, Vlsr = 64 km/s, Tex = 190 K  
  > "By setting the $\Delta V$ to 6.5 $\mathrm{km\ s^{-1}}$, $V_\text{lsr}$ to 64 $\mathrm{km\ s^{-1}}$, $T_\text{ex}$ to 190 K" (3.1)
   - assumption: LTE, single Tex, dense LMH region (n>1e9 cm^-3), negligible beam dilution  
  > "The LMH region is dense with $n_{\ce{H2}} (\text{Sgr B2(N)}) > 10^{9}\ \mathrm{cm}^{-3}$ (cite: sss2017), and hence LTE is assumed to be reached." (3.1)
   - fitting: _not stated_
   - validation: Snyder criteria; A-E pair checks; spatial inspection of transition maps  
  > "we have additionally checked every interferometric transition map of the less contaminated transitions found by our methods and marked the spatially polluted transitions" (3.1)
3. **Fit Tex and column density**: chi-square fit of simulated to observed peak intensities of uncontaminated transitions toward LMH  
  > "we perform a $\chi^2$ fitting over these less contaminated transitions to statistically determine $\mathrm{T_{ex}}$ toward the LMH region." (3.3)
   - fitting: chi2 = sum (Iobs-Isim)^2/sigma^2, sigma = rms; Tex and NT free  
  > "$\sigma$ is the rms noise level of the observed spectrum." (3.3)
   - validation: Compared with IRAM 30m and OVRO ratios  
  > "Although this result is in agreement with the suggested ratio of \[\]:\[\] $\sim$ 6.7 observed with the OVRO array (cite: hlj2000), we find an enhancement of the abundance of AcA" (3.3 Column Density)
4. **Make transition maps and stacked chemical maps**: Moment-8 peak intensity maps over 59-68 (low) and 70-75 km/s (high) for MF/GLA, 59-67 km/s for AcA; stack with inverse-variance weights  
  > "For the low-velocity component, the integrated velocity range is 59-68 $\mathrm{km\ s^{-1}}$ while for the high-velocity component, the range is 70-75 $\mathrm{km\ s^{-1}}$." (4.1); "In the stacking process, we used the inverse-variance weighting for each transition, where the variance is the square of the noise of each data cube." (4.2)
   - software: CASA
   - fitting: _not stated_
   - validation: Consistency of maps across Eu range  
  > "Because the uncontaminated transitions covering an extensive range of upper-state energies show similar morphology, the effect of excitation conditions is ruled out" (4.2)

## Software

- **CASA** : imaging, continuum subtraction, analysis  
  > "The Common Astronomy Software Applications package (CASA) (cite: mws2007) was used for imaging and analysis." (2 OBSERVATIONS)
- **Python spectral simulation program (B. McGuire)** : simulating and visualizing molecular emission spectra  
  > "We are indebted to B.A. McGuire for providing a Python program for simulating and visualizing molecular emission spectra" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| MF Tex | 201 | 12 | K | 3 | For MF, a $T_\text{ex}$ of 201(12) K and a $N_{T,MF}$ of $1.18(0.05) \times 10^{17}\ \mathrm{cm}^{-2}$ minimized the $\chi^2$ to 314.6 |
| MF column density | 1.18e17 | 0.05e17 | cm^-2 | 3 | $N_{T,MF}$ of $1.18(0.05) \times 10^{17}\ \mathrm{cm}^{-2}$ |
| GLA Tex | 146 | 25 | K | 3 | a $T_\text{ex}$ of 146(25) K and a $N_{T,GLA}$ of $1.57(0.12) \times 10^{16}\ \mathrm{cm}^{-2}$ |
| GLA column density | 1.57e16 | 0.12e16 | cm^-2 | 3 | $N_{T,GLA}$ of $1.57(0.12) \times 10^{16}\ \mathrm{cm}^{-2}$ |
| AcA Tex | 296 | 59 | K | 3 | $T_\text{ex} = 296(59) \mathrm{K}$ and $N_{T,AcA} = 4.63(0.92) \times 10^{16}\ \mathrm{cm}^{-2}$ |
| AcA column density | 4.63e16 | 0.92e16 | cm^-2 | 3 | $N_{T,AcA} = 4.63(0.92) \times 10^{16}\ \mathrm{cm}^{-2}$ |
| Abundance ratio MF:AcA:GLA | ~7.5:2.9:1 | not stated | dimensionless | 3 | suggests abundance ratios of MF, AcA, and GLA \[\]:\[\]:\[\] of $\sim$ 7.5:2.9:1. |
| Separation MF1-MF2 | 3.8 | not stated | arcsec | 4 | which are connected with each other over a distance of $3.8 \ensuremath{''}$ |
| Separation MF3-MF4 | 8.1 | not stated | arcsec | 4 | are separated by around $8.1 \ensuremath{''}$ |
| GLA2 north of GLA1 | 5.9 | not stated | arcsec | 4 | GLA2 is $\sim 5.9 \ensuremath{''}$ north of GLA1. |

## Qualitative findings

- MF and GLA show two velocity components (~64 and ~73 km/s); AcA only ~64 km/s  
  > "each display two different velocity components, while only one velocity component of is resolved." (abstract)
- MF is extended and offset from the continuum peak; GLA and AcA are compact near the continuum peak  
  > "the distribution of is extended and offset from the continuum emission, unlike and , for which the low-velocity component is found to be compact" (abstract)

## Claim tuples

- H: Quantitative P/D selection yields uncontaminated isomer transitions, including previously unreported ones | E: Compared LTE simulated and observed spectra toward LMH with thresholds | R: 26 MF, 10 GLA, 5 AcA least contaminated transitions | F: Method identifies clean new transitions, mostly different from previously reported lines | **supported**
- H: The three isomers have different spatial distributions | E: Stacked chemical maps of clean transitions | R: MF extended and offset; GLA and AcA compact and co-spatial with continuum | F: Distinct morphologies, not caused by excitation | **supported**
- H: Existing chemical models explain the observed distributions | E: Qualitative comparison with grain-surface and gas-phase schemes, DME/ethanol maps | R: No clear relation to proposed gas-phase precursors | F: Current theory cannot explain the distributions | **refuted**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Excitation temperature, photodestruction, and density differences ruled out as causes of morphology  
  > "Therefore, selective photo-destruction fails to account for the differentiation in these morphologies." (5 DISCUSSION)
- How they decided it was enough: _not stated_
- Limitation (authors): AcA morphology cannot be accurately determined due to few transitions and spatial contamination  
  > "the morphology of AcA cannot be accurately determined based on the limited number and the spatial contamination of the transition maps." (4.1)
- Limitation (authors): Spectral simulation parameters chosen subjectively  
  > "we find that though subjective the single-excitation temperature simulations yield the most consistent fit" (3.1)
- Caveat (inferred, ours): Single Tex LTE spectrum from one position used for line selection; no source size or multiple components
- Caveat (inferred, ours): chi-square fit on few lines with peak intensities, degeneracy of Tex and N
- Caveat (inferred, ours): Spatial contamination of maps remains
- Caveat (inferred, ours): MF chi2 of 314.6 for 15 dof indicates poor fit

## Reproducibility

- Data public (paper): Data from the ALMA Science Archive  
  > "The interferometric data used here were acquired from the ALMA Science Archive" (2 OBSERVATIONS)
- Products in archive: _not stated_
- Missing: Calibrated data or calibration script (in Belloche et al. 2016)
- Missing: Spectral simulation code
- Missing: Line-free channel ranges
- Missing: Exact stacking and moment-map procedure
- Data volume (inferred): ~100-300 GB raw for 5 setups; cubes tens of GB
- Score (inferred): 3/5, Public data and clear selection criteria and fits, but calibration, code and mapping details are not given.
- Rediscovery candidate: no, Requires external calibration paper and unreleased simulation code; line selection partly subjective.

## Links

- Method: (cite: slhf2005) (Snyder criteria for line assignment)
- Method: (cite: gswb2017) (continuum channel selection technique)
- Companion: (cite: bmgk2016) (EMoCA survey observations and calibration)
- Companion: (cite: bbmgm2017) (continuum source characterization in Sgr B2(N))
- Related: EMoCA

## Checks

```json
{
 "quotes": 63,
 "quotes_ok": 63,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 40,
  "rate": 0.563
 },
 "evidence_ok": true
}
```
