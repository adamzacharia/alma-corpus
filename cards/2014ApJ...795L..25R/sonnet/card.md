# Turbulence Sets the Initial Conditions for Star Formation in High-pressure Environments

`2014ApJ...795L..25R` | The Astrophysical Journal Letters 2014 | first author: Rathborne, J. M. | arXiv: 1409.0935 | DOI: 10.1088/2041-8205/795/2/L25

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: milky_way_ism, star_formation
- Question: Do theoretical predictions of supersonically turbulent, isothermal cloud structure and star formation thresholds, validated in solar neighbourhood clouds, hold in a high-pressure CMZ cloud?  
  > "it is unknown if these theories extend to clouds in high-pressure ($P/k>10^7~{\rm K}~{\rm cm}^{-3}$) environments, like those in the Galaxy’s inner 200 pc Central Molecular Zone (CMZ) and in the early Universe." (abstract)
- Target **G0.253+0.016**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00217.S
- bands: 3 mm (90 GHz)  
  > "We obtained a 3’$\times$1’ mosaic of the 3 mm (90 GHz) dust continuum and molecular line emission across G0.253+0.016" (Observations)
- frequencies and spectral setup: 4 spectral windows centred at 87.2, 89.1, 99.1 and 101.1 GHz, each 1875 MHz bandwidth, 488 kHz channel spacing  
  > "The correlator was configured to use 4 spectral windows in dual polarization mode centred at 87.2, 89.1, 99.1 and 101.1 GHz each with 1875 MHz bandwidth and 488 kHz (1.4$-$1.7 km s$^{-1}$) channel spacing." (Observations)
- continuum bandwidth: _not stated_
- arrays: 25 antennas, ALMA Early Science Cycle 0  
  > "using 25 antennas as part of ALMA’s Early Science Cycle 0" (Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.7" (0.07 pc)  
  > "an angular resolution of 1.7” (0.07 pc)" (Observations)
- max recoverable scale: large-scale emission >1.2' filtered out  
  > "The ALMA data does not include the large-scale emission ($>$ 1.2’) that is filtered out by the interferometer." (Deriving the column density)
- sensitivity: 1 sigma rms ~25 uJy/beam  
  > "a 1 $\sigma$ rms sensitivity of $\sim$ 25$\mu$Jy beam$^{-1}$" (Observations)
- time on source: _not stated_
- observing dates: six occasions, 29 July – 1 August 2012  
  > "The cloud was imaged on six occasions between 29 July – 1 August 2012." (Observations)
- pi or archival as stated: _not stated_
- Line: H2CS not stated (not stated)
- Other facility **Herschel**: 500 um continuum (33" resolution) used as single-dish large-scale template; dust temperature  
  > "we scale the 500 $\mu$m  dust continuum emission (*Herschel*, 33$''$  angular resolution) to what is expected at 3 mm" (Deriving the column density)
- Other facility **Spitzer**: 3.6 and 8 um images for Figure 1  
  > "Figure [1](#image) combines *Spitzer*  3.6 and 8 $\mu$m  images (blue and green, respectively)" (Observations)
- External data: Dust temperature profile from Herschel (27 K edge to 19 K interior)  
  > "*Herschel* observations show that the dust temperature (T$_{dust}$) within G0.253+0.016  decreases from 27 K on its outer edges to 19 K in its interior" (Deriving the column density) [from (cite: Longmore12)]
- External data: Dust opacity kappa_1.2mm = 0.8 cm2/g scaled with nu^beta  
  > "dust absorption coefficient ($\kappa_{3mm}$) of 0.27 cm$^{2}$ g$^{-1}$ (using $\kappa_{1.2mm}$ = 0.8 cm$^{2}$ g$^{-1}$, and $\kappa \propto \nu^{\beta}$; (cite: Chen08; Ossenkopf94))" (Deriving the column density) [from (cite: Chen08; Ossenkopf94)]
- External data: Solar neighbourhood N-PDF parameters and cloud properties for comparison (Table 1)  
  > "Molecular cloud properties within the solar neighbourhood (Solar) and Central Molecular Zone (CMZ)." (Table 1) [from (cite: Kainulainen09; Kainulainen13; Schneider14)]
- External data: N-PDF to rho-PDF conversion factor xi with ~15% uncertainty  
  > "Theoretical work suggests that the conversion is a multiplication by a factor $\xi$, where $\sigma_{\log{\rho}}=\xi\, \sigma_{\log{N}}$ (cite: Brunt10b)." (Discussion) [from (cite: Brunt10b)]

## Processing

### Calibration

- pipeline or manual: Each dataset independently calibrated before merging (by ALMA Contact Scientist)  
  > "Each dataset was independently calibrated before being merged." (Observations); "We thank our ALMA Contact Scientist, Dr Crystal Brogan, for preparing the observations and performing the data calibration." (Acknowledgments)
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
- cell size: 0.35"  
  > "The continuum image has a pixel size of 0.35$''$" (Observations)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: ALMA combined with Herschel 500 um scaled to 3 mm via CLEAN in CASA  
  > "The combination of the datasets was performed in CASA via the CLEAN algorithm (see (cite: Rathborne-overview))." (Deriving the column density)
- smoothing: _not stated_
- final beam: 1.7"  
  > "an angular resolution of 1.7” (0.07 pc)" (Observations)
- final rms: ~25 uJy/beam  
  > "a 1 $\sigma$ rms sensitivity of $\sim$ 25$\mu$Jy beam$^{-1}$" (Observations)

### Inherited from earlier work

- Combination of ALMA and Herschel data details  
  > "The combination of the datasets was performed in CASA via the CLEAN algorithm (see (cite: Rathborne-overview))." (Deriving the column density) [from (cite: Rathborne-overview)]
- Molecular line cubes and kinematics  
  > "combined, they reveal the gas kinematics and chemistry within the cloud (see (cite: Rathborne-overview))." (Observations) [from (cite: Rathborne-overview)]

### Not stated but needed to reproduce (our reading)

- Imaging weighting/robust, deconvolver, masks, and CLEAN parameters
- Details of the SD+interferometer combination (feathering vs CLEAN model, scaling)
- N-PDF binning, fitting method, and range used for log-normal fits
- Calibrator names and flux scale
- Source coordinates and distance adopted
- How the 72 Msun core was defined (aperture) and the velocity dispersion source line
- CASA/Miriad versions

## Analysis recipe

1. **Combine ALMA with scaled Herschel 500 um**: Scale Herschel 500 um to 3 mm assuming greybody nu^(2+beta); combine with ALMA in CASA via CLEAN; test beta values 1.0-2.0  
  > "we performed the image scaling using a range of values for $\beta$  (1.0, 1.2, 1.5, 1.75, 1.9, 2.0)." (Deriving the column density)
   - software: CASA
   - parameter: beta = 1.2 ± 0.1 chosen  
  > "Thus, we assume $\beta$ of 1.2 $\pm$ 0.1." (Deriving the column density)
   - assumption: T_dust = 20 ± 1 K  
  > "thus, we assume T$_{dust}$ is 20 $\pm$ 1 K ." (Deriving the column density)
   - fitting: _not stated_
   - validation: Removal of zero-spacing imaging artefacts justifies beta ~1.2  
  > "The removal of the image artefacts justifies the value for $\beta$ $\sim$1.2" (Deriving the column density)
2. **Convert 3 mm intensity to column density**: Multiply intensity in mJy by 1.9e23 cm^-2/mJy for optically thin dust  
  > "was converted to column density, N(H$_{2}$), by multiplying by 1.9 $\times$ 10$^{23}$ ${\rm cm}^{-2}$/mJy." (Deriving the column density)
   - parameter: kappa_3mm = 0.27 cm2/g  
  > "dust absorption coefficient ($\kappa_{3mm}$) of 0.27 cm$^{2}$ g$^{-1}$" (Deriving the column density)
   - assumption: gas to dust mass ratio of 100  
  > "assuming a gas to dust mass ratio of 100" (Deriving the column density)
   - fitting: _not stated_
   - validation: T_dust and beta uncertainties give ~10% column density uncertainty  
  > "introduce an uncertainty of $\sim$ 10% for the column density, volume density, mass, and virial ratio." (Deriving the column density)
3. **Derive and fit N-PDF**: Build N-PDF from ALMA-only and combined images; fit log-normal; compare with solar neighbourhood  
  > "Both N-PDFs are well fitted by a log-normal distribution." (The column density PDF)
   - fitting: log-normal fit; uncertainties ~10% dispersion, ~25% peak column density  
  > "there is an uncertainty of $\sim$10% in the dispersion and $\sim$25% for the peak column density." (Deriving the column density)
   - validation: Compare ALMA-only vs combined PDFs  
  > "the derived dispersion is narrower and the peak column density higher compared to using the ALMA-only image." (The column density PDF)
4. **Core mass, density and virial parameter**: Mass from 3 mm emission, alpha_vir = 3kσ²R/GM with k=1.16 and σ<1.4 km/s from H2CS  
  > "we determine the virial parameter, $\alpha_{\rm vir}$, defined as $\alpha_{\rm vir}=3k\sigma^2R/GM$" (The column density PDF)
   - parameter: R ~0.04 pc  
  > "we calculate the mass of this core (R$\sim$0.04 pc) to be 72 M$_{\odot}$" (The column density PDF)
   - assumption: density profile rho ∝ r^-1.8, k=1.16  
  > "For high-mass star-forming cores with density profiles $\rho \propto r^{-1.8}$ (cite: Garay07), $k$ is 1.16." (The column density PDF)
   - fitting: _not stated_
   - validation: _not stated_
5. **Compare with turbulence theory**: Compute Mach numbers, predicted sigma_log rho, pressures, rho_crit for solar and CMZ environments and compare with measured PDF  
  > "their $\mathcal{M}_{1{\rm D}}$  numbers are $\sim$10 and $\sim$30, which corresponds to predictions of $\sigma_{\log{\rho}} \sim$ 2.08 and 2.55" (Discussion)
   - parameter: b = 0.5  
  > "(assuming $b$=0.5)" (Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : data reduction and ALMA+Herschel combination  
  > "All data reduction was performed using the CASA and Miriad software packages." (Observations)
- **Miriad** : data reduction  
  > "All data reduction was performed using the CASA and Miriad software packages." (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| N-PDF dispersion sigma_logN (combined) | 0.34 | 0.03 | dimensionless | 3 | 0.34 $\pm$ 0.03 |
| Mean column density N0 | 86e21 | 20e21 | cm^-2 | 3 | 86 $\pm$ 20 $\times10^{21}$ ${\rm cm}^{-2}$  in G0.253+0.016 |
| Flux fraction recovered by ALMA-only | ~18 | not stated | % | 1 | Since the ALMA-only image recovers a small fraction of the total flux ($\sim$ 18%) |
| Star-forming core mass (T=20 K) | 72 | not stated | Msun | 4 | we calculate the mass of this core (R$\sim$0.04 pc) to be 72 M$_{\odot}$ |
| Core volume density | >3.0e6 | not stated | cm^-3 | 4 | its volume density to be $>$3.0 $\times$ 10$^{6}$ ${\rm cm}^{-3}$ |
| Virial parameter of core (M=72 Msun) | <1.1 | not stated | dimensionless | 4 | for a mass of 72  M$_{\odot}$  $\alpha_{\rm vir}$ $<$ 1.1 |
| Mass fraction in star-forming region | 0.06 | not stated | % | 3 | only one region, corresponding to 0.06% of the total mass, shows evidence for star formation |

## Qualitative findings

- N-PDF is log-normal with a small high-density deviation coincident with a water maser, indicating self-gravity  
  > "There is a small deviation from the log-normal distribution at the highest column densities which indicates self-gravitating gas where star formation is commencing." (The column density PDF)

## Claim tuples

- H: Turbulence theory predicts similar PDF dispersion but ~100x higher mean column density in the CMZ | E: Derived N-PDF of G0.253+0.016 from combined ALMA+Herschel 3 mm map; compared with solar neighbourhood | R: sigma_logN=0.34±0.03 vs 0.28–0.59; N0 86e21 vs 0.5–3e21 cm^-2 | F: Similarity and difference match turbulent model predictions | **supported**
- H: Star formation threshold depends on environment | E: Compared core density with predicted rho_crit | R: core density >1e6 cm^-3 versus predicted ~1e8 for CMZ and ~1e4 for solar | F: Consistent with environmentally dependent volume density threshold; universal column density threshold doubtful | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Herschel 500 um chosen for most reliable large-scale recovery and closest wavelength to 3 mm  
  > "We choose to scale the 500 $\mu$m  emission as it is the closest in wavelength to 3 mm, minimising the effect of the assumption of $\beta$." (Deriving the column density)
- Alternative: ALMA-only N-PDF considered but not used for comparison since it misses large-scale emission  
  > "Thus, to make meaningful comparisons between the N-PDF for the G0.253+0.016  and to solar neighbourhood clouds and theoretical predictions requires the inclusion of the large-scale emission." (The column density PDF)
- How they decided it was enough: _not stated_
- Limitation (authors): Core unresolved so density is a lower limit; deviation may be from temperature  
  > "the density is a lower limit since this core is unresolved" (The column density PDF)
- Caveat (inferred, ours): Single cloud; generalisation to early Universe is speculative
- Caveat (inferred, ours): Herschel scaling includes line-of-sight contamination and assumes uniform beta and T
- Caveat (inferred, ours): N-PDF to rho-PDF conversion is uncertain
- Caveat (inferred, ours): Solar neighbourhood comparison values are order-of-magnitude

## Reproducibility

- Data public (paper): ALMA data cited by project code  
  > "We make use of the following ALMA data: ADS/JAO.ALMA#2011.0.00217.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CLEAN/combination parameters (deferred to companion paper)
- Missing: Herschel map and exact scaling procedure
- Missing: N-PDF fitting procedure
- Data volume (inferred): ~50-100 GB (six Cycle 0 execution blocks, mosaic with 4 wide spectral windows)
- Score (inferred): 3/5, Public data and simple conversion chain, but imaging and combination details are deferred to a companion paper.
- Rediscovery candidate: no, Combination and PDF-fitting details are not given in this letter.

## Links

- Method: (cite: Rathborne-overview) (Details of observations, imaging and ALMA+Herschel combination)
- Companion: (cite: Longmore12) (Herschel dust temperature and cloud properties)
- Companion: (cite: Johnston14) (SMA 1 mm N-PDF of the same cloud)
- Related: Herschel

## Checks

```json
{
 "quotes": 57,
 "quotes_ok": 57,
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
  "facts": 78,
  "stated": 44,
  "rate": 0.564
 },
 "evidence_ok": true
}
```
