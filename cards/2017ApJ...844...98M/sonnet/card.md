# ALMA Observations of N83C in the Early Stage of Star Formation in the Small Magellanic Cloud

`2017ApJ...844...98M` | The Astrophysical Journal 2017 | first author: Muraoka, Kazuyuki | arXiv: 1706.04871 | DOI: 10.3847/1538-4357/aa7a0b

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, nearby_galaxies, astrochemistry
- Question: What are the molecular gas structure, density, temperature and CO-to-H2 conversion factor in the low-metallicity star-forming region N83C in the SMC, and how do they relate to YSOs?  
  > "Then, we derive various properties of molecular clouds: virial mass, average gas density, kinetic temperature, and $X_{\rm CO}$." (Introduction)
- Target **N83C (SMC)**: coordinates RA 01h14m05.414s, Dec -73d17m03.908s (J2000)  
  > "The observations were centered on ($\alpha_{\rm J2000}$, $\delta_{\rm J2000}$) = ($01^h 14^m 05\rlap.{^s}414$, $-73^{\circ} 17' 03\rlap.{''}908$)." (Observations); "its proximity ($\sim$ 60 kpc; (cite: hilditch2005))" (Introduction); z/distance ~60 kpc  
  > "The observations were centered on ($\alpha_{\rm J2000}$, $\delta_{\rm J2000}$) = ($01^h 14^m 05\rlap.{^s}414$, $-73^{\circ} 17' 03\rlap.{''}908$)." (Observations); "its proximity ($\sim$ 60 kpc; (cite: hilditch2005))" (Introduction); distance from Hilditch et al. 2005  
  > "The observations were centered on ($\alpha_{\rm J2000}$, $\delta_{\rm J2000}$) = ($01^h 14^m 05\rlap.{^s}414$, $-73^{\circ} 17' 03\rlap.{''}908$)." (Observations); "its proximity ($\sim$ 60 kpc; (cite: hilditch2005))" (Introduction)

## Data provenance

- ALMA projects: 2013.1.00212.S
- bands: Band 6 (211-275 GHz) and Band 7 (275-373 GHz)  
  > "ALMA Cycle 2 observations toward N83C were carried out in Band 6 (211 – 275 GHz) and Band 7 (275 – 373 GHz)" (Observations)
- frequencies and spectral setup: Line windows 117.19 MHz (30.5 kHz x 3840 channels); Band 6 continuum window 1875.0 MHz (488.3 kHz x 3840 channels)  
  > "with a bandwidth of 117.19 MHz (30.5 kHz $\times$ 3840 channels)" (Observations); "bandwidth of 1875.0 MHz (488.3 kHz $\times$ 3840 channels) in Band 6" (Observations)
- continuum bandwidth: _not stated_
- arrays: 12 m main array, ACA 7 m, and TP 12 m  
  > "with the main array 12 m antennas, the Atacama Compact Array (ACA) 7 m antennas, and total power (TP) 12 m antennas" (Observations)
- configurations: _not stated_
- baselines: Max baseline 348.5 m (12 m array), 48.9 m (ACA)  
  > "The maximum baseline of the 12 m array is 348.5 m and that of ACA is 48.9 m." (Observations)
- angular resolution: Band 6: 1.72" x 1.37" (0.50 x 0.40 pc); Band 7: 4.64" x 4.33"  
  > "which provided synthesized beam sizes of 1$\rlap.{''}$72 $\times$ 1$\rlap.{''}$37 (0.50 pc $\times$ 0.40 pc at 60 kpc)" (Observations)
- max recoverable scale: _not stated_
- sensitivity: rms 17 mJy/beam (Band 6), 148 mJy/beam (Band 7) at 0.2 km/s  
  > "The rms noise levels of molecular lines at the velocity resolution of 0.2 km s$^{-1}$ are 17 mJy beam$^{-1}$ in Band 6 and 148 mJy beam$^{-1}$ in Band 7" (Observations)
- time on source: _not stated_
- observing dates: 2014 May to 2015 September  
  > "between 2014 May and 2015 September" (Observations)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (not stated)
- Line: 13CO J=2-1 (not stated)
- Line: C18O J=2-1 (not stated)
- Line: 12CO J=3-2 (not stated)
- Line: 13CO J=3-2 (not stated)
- Line: CS J=7-6 (not stated)
- Other facility **Spitzer Space Telescope**: YSO identifications  
  > "identified based on the $Spitzer$ $Space$ $Telescope$ data (see also Figure 1(c))" (Maps)
- External data: 12CO(2-1)/(1-0) ratio of 0.9  
  > "we assume the $^{12}$CO($J=2-1$)/$^{12}$CO($J=1-0$) ratio of 0.9 according to (cite: bolatto2003)" (5.1 XCO in the SMC) [from (cite: bolatto2003)]
- External data: YSO luminosities of sources A and B  
  > "the luminosity of source A, 20140 $L_{\odot}$, is three times larger than that of source B, 6899 $L_{\odot}$ (cite: kamath2014)" (Discussion) [from (cite: kamath2014)]
- External data: YSOs C, D, E identification  
  > "A and B are identified by (cite: kamath2014), and C, D, and E are by (cite: sewilo2013)." (Table 1) [from (cite: sewilo2013)]

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

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting for Band 6 and Band 7  
  > "We applied natural weighting for both Band 6 and Band 7 data" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Band 7 uses only ACA+TP; C18O(2-1) uses only ACA+TP  
  > "Note that we only used ACA and TP data in Band 7 because we could not obtain the main-array data" (Observations)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Virial mass formula  
  > "We estimate the virial mass ($M_{\rm vir}$) of molecular clouds associated with sources A and B as follows (cite: solomon1987)" (Maps) [from (cite: solomon1987)]
- LVG abundance ratio 12CO/13CO = 50 and Z(12CO) scaled from LMC  
  > "The assumed \[$^{12}$CO\]/\[$^{13}$CO\] of 50 is the same as that in the LMC (cite: mizuno2010)." (Deriving gas density) [from (cite: mizuno2010)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration (pipeline or manual) details
- Imaging task, cell size, image size, masks, deconvolver
- Continuum subtraction and line-free channels
- How 12m, ACA and TP data were combined
- LVG code used and grid ranges
- Moment-map velocity ranges and clipping
- Flux calibrators and flux uncertainty
- How L_CO integration area and sigma_v fits were done

## Analysis recipe

1. **Make line maps**: Reduce data in CASA with natural weighting; make integrated intensity maps  
  > "The data were reduced using the Common Astronomy Software Application (CASA) package." (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Virial mass and density of clumps**: M_vir = 1040 sigma_v^2 R with R the effective radius above half peak and sigma_v from Gaussian fit; density from M_vir  
  > "Here, $R$ was determined as the effective radius of the area whose CO intensity exceeds half the peak, and $\sigma_v$ was calculated from the gaussian fitting of the CO line integrated over the area." (Maps)
   - assumption: mu_H2 ~ 2.7  
  > "where $\mu_{\rm H_2} \sim 2.7$ is the mean molecular weight per H$_2$ molecule (including the contribution by He)" (Maps)
   - fitting: Gaussian fit to line  
  > "$\sigma_v$ was calculated from the gaussian fitting of the CO line integrated over the area" (Results and Analyses, Maps)
   - validation: _not stated_
3. **LVG density and temperature**: LVG from 13CO(3-2)/12CO(3-2) and 13CO(3-2)/13CO(2-1) ratio maps  
  > "we estimate gas density and kinetic temperature of molecular clouds using line ratios obtained from ALMA observations based on the Large Velocity Gradient (LVG) approximation" (Deriving gas density)
   - parameter: Z(12CO)=8.0e-6, [12CO]/[13CO]=50, dv/dr=2.0 km/s/pc  
  > "the molecular abundance $Z$($^{12}$CO) = \[$^{12}$CO\]/\[H$_2$\] of $8.0 \times 10^{-6}$, the \[$^{12}$CO\]/\[$^{13}$CO\] abundance ratio of 50, and the velocity gradient $dv/dr$ of 2.0 km s$^{-1}$ pc$^{-1}$" (Deriving gas density)
   - fitting: _not stated_
   - validation: LVG density compared with virial density  
  > "The derived gas density based on the LVG calculation is consistent with that calculated from the virial mass." (Deriving gas density)
4. **Derive XCO**: X_CO = (M_vir/(mu m_H))/L_CO for sources A and B, averaged  
  > "$$\begin{eqnarray}
X_{\rm CO} = \frac{M_{\rm vir} / (\mu_{\rm H_2} \times m_{\rm H})}{L_{\rm CO}} \,\, ,
\end{eqnarray}$$" (5.1 XCO in the SMC)
   - assumption: 12CO(2-1)/(1-0) = 0.9  
  > "we assume the $^{12}$CO($J=2-1$)/$^{12}$CO($J=1-0$) ratio of 0.9 according to (cite: bolatto2003)" (5.1 XCO in the SMC)
   - fitting: _not stated_
   - validation: Compared with Bolatto et al. 2003 N83 value  
  > "which is in good agreement with that in N83 obtained by (cite: bolatto2003)" (5.1 XCO in the SMC)

## Software

- **CASA** : Data reduction  
  > "The data were reduced using the Common Astronomy Software Application (CASA) package." (Observations)
- **APLpy** : Plotting  
  > "This research made use of APLpy, an open-source plotting package for Python (cite: robitaille2012)." (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Average X_CO | 7.5e20 | not stated | cm^-2 (K km/s)^-1 | 4 | The averaged $X_{\rm CO}$ of $7.5 \times 10^{20}$ cm$^{-2}$ (K km s$^{-1}$)$^{-1}$ is four times higher than that in the MW disk |
| X_CO source A | 6.2e20 | not stated | cm^-2 (K km/s)^-1 | 4 | yield $X_{\rm CO}$ of $6.2 \times 10^{20}$ cm$^{-2}$ (K km s$^{-1}$)$^{-1}$ |
| X_CO source B | 8.7e20 | not stated | cm^-2 (K km/s)^-1 | 4 | $8.7 \times 10^{20}$ cm$^{-2}$ (K km s$^{-1}$)$^{-1}$, from $M_{\rm vir}$ of $1.5 \times 10^3 M_{\odot}$ |
| Virial mass source A (12CO 2-1) | 2.5e3 | not stated | Msun | 2 | / A / $^{12}$CO($J$=2-1) / 1.69 / 0.8 / 2.5 $\times$ 10$^3$ / 1.5 $\times$ 10$^4$ / 186 / |
| LVG gas density at A and B | ~1.5e4 | not stated | cm^-3 | 3 | We found gas densities of $\sim 1.5 \times 10^4$ cm$^{-3}$ and kinetic temperatures of 30 – 50 K at sources A and B. |
| Kinetic temperature | 30-50 | not stated | K | 3 | kinetic temperatures of 30 – 50 K at sources A and B |

## Qualitative findings

- Molecular gas is distributed along the edge of the neighboring HII region, with CO peaks at YSOs A and B  
  > "we also found that overall molecular gas is distributed along the edge of the neighboring H$\,$ii region" (abstract)

## Claim tuples

- H: Is XCO in resolved clumps of N83C higher than the Galactic value? | E: Virial masses and CO luminosities of clumps A and B | R: Average XCO 7.5e20 | F: XCO about four times the MW value | **supported**
- H: Why is gas density high in CO-traced clumps? | E: Virial and LVG densities | R: ~1e4 cm^-3 | F: FUV photodissociation means only innermost dense parts are seen in CO | **partially**
- H: Do sources A and B differ in nature? | E: Compare CS, C18O, Halpha and Band 6 continuum | R: CS stronger in A, C18O only in B, continuum peak at A | F: Source A likely hosts a deeply embedded YSO in a very dense clump | **partially**

## Reasoning

- Why this data: Higher angular resolution needed to resolve clouds and get more accurate XCO  
  > "further observations with higher angular resolution are indispensable" (Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): High-T_K linear feature is an artefact of one-zone LVG breakdown  
  > "This is due to the breakdown of the one-zone model in the LVG approximation by the overlap of molecular gas with multiple velocity components." (Deriving gas density)
- Caveat (inferred, ours): No uncertainties on virial masses, XCO or LVG results
- Caveat (inferred, ours): Only two clumps used for XCO
- Caveat (inferred, ours): Virial equilibrium and spherical geometry assumed
- Caveat (inferred, ours): LVG assumptions (abundance, dv/dr) fixed, not fitted
- Caveat (inferred, ours): Different beams between lines in ratio maps

## Reproducibility

- Data public (paper): ALMA data cited by project code in acknowledgments  
  > "This paper makes use of the following ALMA data: \[ADS/JAO.ALMA#2013.1.00212.S\]." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version and imaging parameters
- Missing: LVG code
- Missing: Velocity integration ranges
- Missing: Details of uv combination
- Data volume (inferred): ~100-300 GB raw for three arrays across two bands
- Score (inferred): 4/5, Short methods; public data but imaging, combination and LVG details missing.
- Rediscovery candidate: no, Recipe is incomplete (imaging, TP combination, LVG code unspecified).

## Links

- Method: (cite: solomon1987) (Virial mass formula)
- Companion: (cite: bolatto2003) (Earlier CO study of N83 and XCO)

## Checks

```json
{
 "quotes": 56,
 "quotes_ok": 56,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 35,
  "rate": 0.515
 },
 "evidence_ok": true
}
```
