# Complex organics in IRAS 4A revisited with ALMA and PdBI: Striking contrast between two neighbouring protostellar cores

`2017A&A...606A.121L` | Astronomy and Astrophysics 2017 | first author: López-Sepulcre, A. | arXiv: 1707.03745 | DOI: 10.1051/0004-6361/201630334

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: Which complex organic molecules are present in each of the two protostellar cores A1 and A2 of NGC 1333 IRAS 4A, and what are their abundances and the chemical contrast between the cores?  
  > "We aim to perform an interferometric study of multiple COMs in NGC1333 IRAS 4A, which is a protostellar binary hosting hot corino activity" (abstract)
- Target **NGC 1333 IRAS 4A (A1, A2)**: coordinates phase centre RA 03:29:10.51, Dec +31:13:31.3 (J2000)  
  > "IRAS 4A is located in the Perseus star formation complex at a distance of 235 pc (cite: hirota08)." (1 Introduction); "The phase centre of the observation was R.A.(J2000) $=$ 03$^\mathrm{d}$29$^\mathrm{m}$10.51$^\mathrm{s}$, Dec.(J2000) $=$+31$^\circ$13$'$31.3$''$" (2.1 ALMA 1.2 mm observations); z/distance 235 pc  
  > "IRAS 4A is located in the Perseus star formation complex at a distance of 235 pc (cite: hirota08)." (1 Introduction); "The phase centre of the observation was R.A.(J2000) $=$ 03$^\mathrm{d}$29$^\mathrm{m}$10.51$^\mathrm{s}$, Dec.(J2000) $=$+31$^\circ$13$'$31.3$''$" (2.1 ALMA 1.2 mm observations); distance from Hirota et al. 2008  
  > "IRAS 4A is located in the Perseus star formation complex at a distance of 235 pc (cite: hirota08)." (1 Introduction); "The phase centre of the observation was R.A.(J2000) $=$ 03$^\mathrm{d}$29$^\mathrm{m}$10.51$^\mathrm{s}$, Dec.(J2000) $=$+31$^\circ$13$'$31.3$''$" (2.1 ALMA 1.2 mm observations)

## Data provenance

- ALMA projects: 2013.1.01102.S
- bands: ALMA Band 6 (~250 GHz, 1.2 mm); PdBI 2.7 mm  
  > "to observe IRAS 4A in Band 6 ($\sim 250$ GHz)" (2.1 ALMA 1.2 mm observations)
- frequencies and spectral setup: 16 spectral windows between 244 and 264 GHz, 58.6 MHz bandwidth, 122 kHz (0.14 km/s) resolution  
  > "We employed 16 spectral windows between 244 and 264 GHz, whose bandwidth and spectral resolution are 58.6 MHz (70 km s$^{-1}$) and 122 kHz (0.14 km s$^{-1}$), respectively." (2.1 ALMA 1.2 mm observations)
- continuum bandwidth: _not stated_
- arrays: ALMA 12 m array, 35 antennas  
  > "A total of 35 antennas of the 12 m array were used" (2.1 ALMA 1.2 mm observations)
- configurations: _not stated_
- baselines: ALMA 18-784 m; PdBI 32-400 m  
  > "with a minimum and maximum baseline length of 18 m and 784 m, respectively" (2.1 ALMA 1.2 mm observations); "The baselines ranged from 32 to 400 m." (2.2 IRAM PdBI 2.7 mm observations)
- angular resolution: ALMA continuum beam 0.66'' x 0.35'' (PA -29 deg)  
  > "The resulting synthesised beam for the continuum image is $0.66'' \times 0.35''$ (P.A. $=$ $-29^\circ$)." (2.1 ALMA 1.2 mm observations)
- max recoverable scale: 3.3 arcsec  
  > "the largest scale recovered by the array is 3.3$''$" (2.1 ALMA 1.2 mm observations)
- sensitivity: _not stated_
- time on source: 26 min (ALMA)  
  > "the total integration time on-source was 26 min" (2.1 ALMA 1.2 mm observations)
- observing dates: ALMA 14 June 2014 (Cycle 2); PdBI 29 January 2005  
  > "was used on 14 June 2014, in its Cycle 2 operations" (2.1 ALMA 1.2 mm observations); "The PdBI was used on 29 January 2005 in its A configuration" (2.2 IRAM PdBI 2.7 mm observations)
- pi or archival as stated: _not stated_
- Line: CH3CN J=6-5 K=0-5 (110.33-110.38 GHz)
- Line: HNCO 12(0,12)-11(0,11) (263.74863 GHz)
- Line: HCOOCH3 20(5,16)-19(5,15) A (249.04743 GHz)
- Other facility **IRAM PdBI**: 2.7 mm continuum and CH3CN J=6-5 lines at 1'' resolution  
  > "Continuum emission as well as five CH$_3$CN transitions at 110.4 GHz were observed." (2.2 IRAM PdBI 2.7 mm observations)
- Other facility **IRAM 30m (ASAI)**: single-dish data used to estimate recovered line flux  
  > "Through comparison with IRAM 30 m data of IRAS 4A obtained in the framework of the large programme ASAI" (3.2 Molecular line emission)
- External data: Dust mass opacity tabulated values (thin icy mantles, density 1e8 cm-3)  
  > "of the tabulated values given in (cite: ossenkopf94), for thin icy mantles and a gas density of 10$^8$ cm$^{-3}$" (3.1 Dust continuum emission) [from (cite: ossenkopf94)]
- External data: L1544 prestellar COM abundances for comparison  
  > "plots molecular abundances measured in a prestellar core, L1544, as reported in (cite: vastel14; yo15), and (cite: js16)" (4.3 IRAS 4A1: Abundances below prestellar values?) [from (cite: vastel14; yo15; js16)]
- External data: Distance 235 pc  
  > "at a distance of 235 pc (cite: hirota08)" (1 Introduction) [from (cite: hirota08)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: ALMA bandpass J0237+2848, flux J0238+166, phase J0319+4130  
  > "The bandpass, flux, and phase calibrators used were J0237+2848, J0238+166, and J0319+4130, respectively." (2.1 ALMA 1.2 mm observations)
- flux scale uncertainty: 10%  
  > "The flux calibration error is estimated to be 10%." (2.1 ALMA 1.2 mm observations)
- self calibration: Phase self-calibration of continuum, applied to continuum and lines  
  > "We performed phase self-calibration of the continuum data and applied the solutions to both the continuum and molecular lines." (2.1 ALMA 1.2 mm observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5 (ALMA); robust 0.1 continuum and natural for lines (PdBI)  
  > "We CLEANed the continuum image and spectral cubes using Briggs weighting with the robustness parameter set to 0.5." (2.1 ALMA 1.2 mm observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: in the visibility plane; continuum from averaging line-free channels  
  > "We then generated spectral cubes by subtracting the continuum emission directly in the visibility plane." (2.1 ALMA 1.2 mm observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: PdBI continuum 1.17''x1.01'', cube 1.35''x1.04''  
  > "that of the spectral cube is $1.35'' \times 1.04''$ (P.A. $=$ $-168^\circ$)" (2.2 IRAM PdBI 2.7 mm observations)
- final rms: continuum 0.96 mJy/beam (ALMA), 0.44 mJy/beam (PdBI)  
  > "The root mean square (RMS) noise levels of the ALMA and PdBI continuum emission maps are 0.96 mJy beam$^{-1}$ and 0.44 mJy beam$^{-1}$, respectively" (3.1 Dust continuum emission)

### Not stated but needed to reproduce (our reading)

- Line-free channel selection for continuum
- Self-calibration solution intervals and number of iterations
- CLEAN masks, thresholds, cell and image size
- CASA version
- Spectroscopic partition functions and their source
- Details of the rotational diagram fitting procedure and error envelope

## Analysis recipe

1. **Continuum fluxes, sizes, masses and N(H2)**: 2D Gaussian fits in the visibility plane; optically thin isothermal dust mass and column density  
  > "obtained from 2D Gaussian fits in the visibility plane" (3.1 Dust continuum emission)
   - software: GILDAS
   - parameter: Td = 50-200 K  
  > "a range of dust temperatures between $T_\mathrm{d} = 50$ and 200 K" (3.1 Dust continuum emission)
   - assumption: kappa = 1.3 (1.2 mm) and 0.30 cm2/g (2.7 mm), dust-to-gas 0.01, mu=2.33, d=235 pc  
  > "$R_\mathrm{d}$ the dust-to-gas mass ratio, adopted to be 0.01" (3.1 Dust continuum emission)
   - fitting: _not stated_
   - validation: Fluxes consistent within 30% with previous work  
  > "The resulting fluxes are consistent within 30% with those measured by (cite: persson12) and (cite: santangelo15)." (3.1 Dust continuum emission)
2. **Line identification and Gaussian line fits**: Identification with CDMS and JPL databases; Gaussian fits to spectra at continuum peaks  
  > "In total, we detect 23 well-isolated lines with $S/N > 4$ for a channel spacing of 0.2 km s$^{-1}$" (3.2 Molecular line emission)
   - software: GILDAS
   - fitting: _not stated_
   - validation: Compared with other studies and sources with the same setup  
  > "many of the lines we detect in IRAS 4A are also detected in other sources, in particular in B335 (cite: imai16), which lends further validity to our line identification." (Molecular line emission)
3. **A2 column densities and temperatures**: Rotational diagrams for HCOOCH3 and CH3OCH3 with beam filling correction; other species with Tex 100-200 K  
  > "we adopted the excitation temperature range $T_\mathrm{ex} = 100 - 200$ K to estimate the column densities of the other eight molecular species" (3.3.1 IRAS 4A2)
   - parameter: hot corino size 0.3''  
  > "with the deconvolved hot corino size, $\theta_\mathrm{hc}$, roughly equal to 0.3$''$" (3.3.1 IRAS 4A2)
   - assumption: LTE, optically thin  
  > "which assumes local thermodynamic equilibrium (LTE) and optically thin line emission" (3.3.1 IRAS 4A2)
   - fitting: Linear fit with envelope lines spanning errors  
  > "each rotational diagram shows, in addition to the best fit line, two opposite lines that encompass the whole range of possible rotational temperatures and molecular column densities within the errors of all the data points." (Derivation of column densities and fractional abundances, IRAS 4A2)
   - validation: Optical depths of order 0.1 or below verified a posteriori  
  > "the optical depth values we measured are of the order of 0.1 or well below" (3.3.1 IRAS 4A2)
4. **A1 upper limits and abundance ratios**: 3 sigma upper limits at 1 km/s channel width, line width 2.5 km/s, Tex 50 and 100 K; X = N/N(H2)  
  > "we provide, in Table [\[tcol\]](#tcol), 3$\sigma$ upper limits to the beam-averaged column densities in A1" (3.3.2 IRAS 4A1)
   - assumption: Optically thin dust, LTE  
  > "We obtained the upper limit column densities assuming LTE conditions." (3.3.2 IRAS 4A1)
   - fitting: _not stated_
   - validation: Dust optical depth test (tau ~1.6 from CH3CN at 2.7 mm)  
  > "it should suffer an attenuation of $\sim$80% by dust in the former in order to fall below 3$\sigma$ (for a channel width of 1 km s$^{-1}$). This translates into a dust optical depth $\sim 1.6$" (IRAS 4A1: Possible explanations for the lack of COM emission)

## Software

- **CASA** : ALMA data reduction  
  > "We reduced the data with the Common Astronomy Software Applications package (CASA)" (2.1 ALMA 1.2 mm observations)
- **GILDAS** : Image and spectral analysis; PdBI reduction (CLIC, MAPPING)  
  > "The data were reduced using the packages CLIC and MAPPING of the GILDAS software collection." (2.2 IRAM PdBI 2.7 mm observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total continuum flux ALMA 1.2 mm | 3.88 | 0.39 | Jy | 1 | the total fluxes within the 5$\sigma$ contour levels are 3.88 $\pm$ 0.39 Jy and 0.56 $\pm$ 0.06 Jy, respectively |
| HCOOCH3 Trot in A2 | 196 | +15/-35 | K | 3 | $T_\mathrm{rot} = 196^{+15}_{-35}$ K and $N = 3.5^{+0.2}_{-0.4} \times 10^{16}$ cm$^{-2}$ for HCOOCH$_3$ |
| CH3OCH3 Trot in A2 | 132 | +17/-11 | K | 3 | $T_\mathrm{rot} = 132^{+17}_{-11}$ K and $N = 4.5^{+0.3}_{-0.2} \times 10^{16}$ cm$^{-2}$ for CH$_3$OCH$_3$ |
| Hot corino size in A2 | ~70 | not stated | au | 2 | the hot corino surrounding A2 protostar has an approximate size of 70 au |
| Max size of hypothetical A1 hot corino | 12 | not stated | au | 4 | a hypothetical hot corino in A1 should have a size smaller than about 12 au |
| A2/A1 abundance ratio lower limit for HCOOCH3 | >120 | not stated | dimensionless | 4 | $<$ 8.2 $\times 10^{-11}$ / \> 120 |

## Qualitative findings

- All organic emission comes from A2; A1 is devoid of COMs even though it is the stronger continuum emitter.  
  > "Molecular emission from organic molecules is concentrated exclusively in A2, while A1 appears completely devoid of COMs" (abstract)

## Claim tuples

- H: Does A1 lack COMs because dust hides a hot corino? | E: Estimate the dust optical depth needed to hide a hot corino like A2's, using CH3CN at 2.7 mm and CH3CHO at 1.2 mm | R: Required tau >3.2 and N(H2) >2.7e26 cm-2, implausible | F: The contrast is most probably real | **supported**
- H: A2 has typical hot corino abundances | E: Derived abundances compared with I16293, B335 and IRAS 2A | R: Abundances 1e-10 to 1e-8 | F: Comparable to other hot corinos | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: A1 hot corino attenuated by optically thick dust, judged unlikely  
  > "While such a large gas density is not totally impossible, it is highly unlikely." (4.2 IRAS 4A1: Possible explanations)
- How they decided it was enough: _not stated_
- Limitation (authors): Isothermal dust assumption is a simplification; A1 masses are lower limits  
  > "We are aware that the assumption of isothermality is a simplification" (3.1 Dust continuum emission)
- Caveat (inferred, ours): Abundances rely on beam-averaged N(H2) with a wide Td assumption
- Caveat (inferred, ours): A1 upper limits depend on assumed Tex and linewidth
- Caveat (inferred, ours): Many species rely on a single line

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: CASA version and calibration script
- Missing: Self-calibration parameters
- Missing: Partition function sources
- Data volume (inferred): ~20-50 GB for the 26 min ALMA Cycle 2 band 6 dataset
- Score (inferred): 5/5, Data are likely public; the recipe is moderately described but lacks imaging and self-calibration details.
- Rediscovery candidate: no, Public status is not stated in the paper, and key imaging and self-calibration details are missing.

## Links

- Companion: (cite: taquet15) (Earlier lower-resolution PdBI COM study of IRAS 4A)
- Companion: (cite: imai16) (Same ALMA setup applied to B335)
- Related: ASAI

## Checks

```json
{
 "quotes": 61,
 "quotes_ok": 61,
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
  "facts": 70,
  "stated": 43,
  "rate": 0.614
 },
 "evidence_ok": true
}
```
