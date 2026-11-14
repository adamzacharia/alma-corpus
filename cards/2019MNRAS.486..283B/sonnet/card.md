# Young massive star cluster formation in the Galactic Centre is driven by global gravitational collapse of high-mass molecular clouds

`2019MNRAS.486..283B` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Barnes, A. T. | arXiv: 1903.06158 | DOI: 10.1093/mnras/stz796

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism, astrochemistry
- Question: Do dust-ridge Galactic Centre YMC progenitor clouds (Cloud D, Cloud E/F) show gravitational collapse at core and proto-cluster scales, discriminating conveyor-belt, in situ and popping cluster formation?  
  > "a relatively simple test to discriminate between the conveyor-belt, in situ, and popping cluster formation scenarios can be conducted by comparing molecular clouds, proto-clusters and clusters at different evolutionary stages." (1 INTRODUCTION)
- Target **Cloud D (G0.412+0.052)**: coordinates G0.412+0.052  
  > "“Cloud D” (G0.412+0.052)" (1 INTRODUCTION); "at a distance of ∼ 8 kpc (Reid et al. 2014; Gravity Collaboration et al. 2018)" (Figure 1 caption); z/distance ~8 kpc  
  > "“Cloud D” (G0.412+0.052)" (1 INTRODUCTION); "at a distance of ∼ 8 kpc (Reid et al. 2014; Gravity Collaboration et al. 2018)" (Figure 1 caption); distance from Reid et al. 2014; Gravity Collaboration et al. 2018  
  > "“Cloud D” (G0.412+0.052)" (1 INTRODUCTION); "at a distance of ∼ 8 kpc (Reid et al. 2014; Gravity Collaboration et al. 2018)" (Figure 1 caption)
- Target **Cloud E/F (G0.489+0.010)**: coordinates G0.489+0.010  
  > "“Cloud E/F” (G0.489+0.010)" (1 INTRODUCTION); "at a distance of ∼ 8 kpc (Reid et al. 2014; Gravity Collaboration et al. 2018)" (Figure 1 caption); z/distance ~8 kpc  
  > "“Cloud E/F” (G0.489+0.010)" (1 INTRODUCTION); "at a distance of ∼ 8 kpc (Reid et al. 2014; Gravity Collaboration et al. 2018)" (Figure 1 caption); distance from Reid et al. 2014; Gravity Collaboration et al. 2018  
  > "“Cloud E/F” (G0.489+0.010)" (1 INTRODUCTION); "at a distance of ∼ 8 kpc (Reid et al. 2014; Gravity Collaboration et al. 2018)" (Figure 1 caption)

## Data provenance

- ALMA projects: 2013.1.00617.S
- bands: Band 6  
  > "The observations made use of the Band 6 receiver" (2.1 ALMA interferometric observations)
- frequencies and spectral setup: 4 SPWs at 250.5, 252.5, 265.5, 267.5 GHz, each 1875 MHz (1920 channels), 977 kHz spacing regridded to 1.25 km/s  
  > "centred at 250.5 GHz, 252.5 GHz, 265.5 GHz, and 267.5 GHz, each with a bandwidth of 1875 MHz (1920 channels)" (2.1 ALMA interferometric observations)
- continuum bandwidth: _not stated_
- arrays: 12 m (C34-1) and 7 m ACA  
  > "the configurations of 12 m and 7 m arrays had projected baseline ranges of 15.0 − 348.5 m (configuration C34-1) and 8.9 − 48.9 m (ACA)" (2.1 ALMA interferometric observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Cloud D 1.47x0.90 arcsec; Cloud E/F 1.27x0.90 arcsec  
  > "major axis, θ major ( [′′] ) 1.47 1.27" (Table 2)
- max recoverable scale: ~50''  
  > "gives an combined angular resolution of ∼ 1 [′′] and a maximum recoverable size scale up to ∼ 50 [′′]" (2.1 ALMA interferometric observations)
- sensitivity: continuum rms 0.4 (D) / 0.6 (E/F) mJy/beam; line rms 0.1 K / 0.07 K per channel  
  > "Continuum rms level, σ rms (mJy beam [−][1] ) [a] 0.4 0.6" (Table 2)
- time on source: _not stated_
- observing dates: April, August and September 2015  
  > "The observations were carried out in April, August and September 2015" (2.1 ALMA interferometric observations)
- pi or archival as stated: _not stated_
- Line: c-C3H2 7(0,7)-6(1,6) (251.31 GHz)
- Line: CH2NH 4(1,3)-3(1,2) (266.27 GHz)
- Line: HCN J=3-2 (265.89 GHz)
- Line: HCO+ 3-2 (267.56 GHz)
- Other facility **CSO BOLOCAM (BGPS)**: 1.1 mm single-dish continuum for zero-spacing  
  > "were used to estimate the zero-spacing (i.e. the missing uv -coverage of the interferometric observations)" (2.2 ALMA and single dish continuum observations)
- Other facility **Herschel**: dust temperature maps used for column density and masses  
  > "both the molecular hydrogen column density and dust temperature at each position is determined by fitting the spectral energy distribution from 70−500 µm" (3.1 Column density analysis)
- Other facility **SMA (CMZoom)**: comparison continuum and higher gas temperatures  
  > "Walker et al. (2018) found higher gas temperatures of 86 K towards core d2, and >150 K towards core e1" (4.2 Virial state of the cores)
- External data: Herschel dust temperature maps  
  > "maps of the Herschel derived dust temperature across each region (Barnes et al. 2017; Battersby et al. in prep)" (Figure 4 caption) [from Barnes et al. 2017; Battersby et al. in prep]
- External data: Gas temperatures 86 K (d2) and 150 K (e1) from SMA formaldehyde  
  > "higher gas temperature estimate of 86 K determined by Walker et al. (2018)" (Table 4) [from Walker et al. (2018)]
- External data: BGPS 1.1 mm image and spectral index ~3.75  
  > "Ginsburg et al. (2013) found that the spectral index from the BOLOCAM to higher frequency Herschel observations is approximately α ν ∼ 3.75" (2.2 ALMA and single dish continuum observations) [from Ginsburg et al. (2013)]
- External data: Sgr B2 YSO/HII source masses for surface density profiles  
  > "Each source is, therefore, individually assigned the average mass above this limit, assuming some initial mass function, which they calculate to be 45.5 M ⊙ ." (5.1 The mass distribution for young mass cluster formation) [from Ginsburg et al. 2018]

## Processing

### Calibration

- pipeline or manual: Manual calibration (QA0 Semi-Pass, no pipeline)  
  > "The raw data, therefore, had to be manually calibrated." (2.1.1 Calibration)
- casa version: CASA 4.4.0 for calibration; 4.7.0 for tclean/feather  
  > "Common Astronomy Software Applications package casa [2] version 4.4.0" (2.1.1 Calibration)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan, Neptune (see Table 1)  
  > "D 26/04/2015 12 m C34-1/(2) 1:11 J1733-1304, 1924-2914 Titan, Neptune J1744-3116" (Table 1)
- flux scale uncertainty: 20 per cent adopted  
  > "We adopt a higher than typically assumed uncertainty of 20 per cent in the absolute flux scale of the ALMA observations" (5.4.1 Uncertainty propagation on mass and virial estimates)
- self calibration: _not stated_

### Imaging

- task: tclean in CASA-4.7.0, 12m and 7m imaged together; feather for single-dish  
  > "The calibrated data sets from the 12m and 7m ar rays were weighted and imaged together with clean process tclean in CASA-4.7.0." (2.1.1 Calibration)
- deconvolver: multiscale  
  > "The data were cleaned down to a given noise level (with a “multiscale” deconvolver)" (2.1.2 Imaging)
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: iterative masks from ~10 sigma, pruned at ~3 beams, then lowered by factor ~2  
  > "an initial mask corresponding to some high multiple of the noise was produced (typically ∼10 σ rms )." (2.1.2 Imaging)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub first-order polynomial; model continuum used for continuum imaging  
  > "a first-order polynomial baseline was fit to the remaining channels using the task uvcontsub." (2.1.1 Calibration)
- line free channels: _not stated_
- primary beam correction: continuum corrected; line cubes not corrected  
  > "the cubes are not primary beam corrected, and therefore have uniform σ rms levels" (2.3 ALMA line observations)
- array combination: feather of ALMA 12m+7m with BGPS, default parameters  
  > "we used the feather function from CASAversion 4.7.0 with the default parameter set" (2.2 ALMA and single dish continuum observations)
- smoothing: cubes regridded to 1.25 km/s  
  > "uniformly regridded to 1.25 km s [−][1] in all cubes used throughout this work" (2.1 ALMA interferometric observations)
- final beam: 1.47x0.90 arcsec PA -23.2 (D); 1.27x0.90 PA 0 (E/F)  
  > "beam position angle, θ PA ( [◦] ) -23.2 0.0" (Table 2)
- final rms: 0.4 and 0.6 mJy/beam continuum  
  > "with a 1 σ rms sensitivity of ∼ 0.4 mJy beam [−][1]" (2.2 ALMA and single dish continuum observations)

### Inherited from earlier work

- Dust temperature and column density SED fitting method  
  > "Following the method outlined in Battersby et al. (2011)" (3.1 Column density analysis) [from Battersby et al. 2011; Barnes et al. 2017]
- Dust opacity kappa0 = 0.9 cm2/g at 230 GHz  
  > "with the linear absorption coefficient κ 0 = 0.9 cm [2] g [−][1] (Ossenkopf & Henning 1994)" (3.1 Column density analysis) [from Ossenkopf & Henning 1994]
- Core nomenclature  
  > "We assign a similar nomenclature to these as Walker et al. (2018)" (4.1 Defining the core and proto-cluster regions) [from Walker et al. 2018]
- Virial factor a = 2 ± 1  
  > "takes a value of a = 2 ± 1 (Kauffmann et al. 2013)" (4.2 Virial state of the cores) [from Kauffmann et al. 2013]

### Not stated but needed to reproduce (our reading)

- Clean thresholds, niter and scales values for multiscale
- Line-free channel ranges (in online appendix, not given)
- Cell and image size, weighting/robust
- Exact astrodendro parameters for core identification
- Core ellipse definitions are by eye
- Self-calibration not mentioned
- pyspeckit initial guesses and exact fit window
- Distance used in mass calculation (8.1 kpc implied)

## Analysis recipe

1. **Calibrate and image 12m+7m data**: Manual calibration, uvcontsub, iterative masked multiscale tclean  
  > "the cleaning of both the continuum maps and molecular line cubes was done in an iterative process." (2.1.2 Imaging)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared with SMA; model-continuum vs masked imaging agree within 10-20%  
  > "on scales of up to 5 [′′] and 10 [′′] the fluxes are in agreement to within 10% and 20%, respectively." (2.1.1 Calibration)
2. **Combine with single dish continuum**: Scale BGPS to ALMA frequency with (259/272)^3.75 ~0.8, regrid, feather  
  > "We used the “feathering” technique to combine the prepared BOLOCAM image and ALMA image." (2.2 ALMA and single dish continuum observations)
   - software: CASA feather
   - fitting: _not stated_
   - validation: Total flux in mapped region conserved vs BOLOCAM  
  > "found that the total flux within the mapped region was conserved" (2.2 ALMA and single dish continuum observations)
3. **Derive column density and mass maps**: Solve optically-thin-capable radiative transfer with Herschel dust temperature  
  > "These maps are interpolated onto the higher angular resolution ALMA pixel grid, and then used to calculate the column density at each position" (3.1 Column density analysis)
   - assumption: gas-to-dust 100, mu_H2 = 2.8, kappa0=0.9 cm2/g at 230 GHz, beta=1.75  
  > "where f gd is the gas-to-dust ratio (typically assumed to be 100), µ H 2 is the mean molecular weight per hydrogen molecule (2.8 a.m.u" (3.1 Column density analysis)
   - fitting: _not stated_
   - validation: _not stated_
4. **Moment maps and line identification**: Splatalogue matching; moment maps above 3 sigma  
  > "The moment maps were then created using the spectral cube package for python." (3.2 Moment map analysis)
   - software: spectral-cube, Splatalogue
   - fitting: _not stated_
   - validation: _not stated_
5. **Identify cores and proto-clusters**: Dendrogram leaves define elliptical cores; proto-cluster ellipse covers ~2e23 cm-2 contour  
  > "We make use of the astrodendro package in python to inspect the complex structure observed within our maps" (4.1 Defining the core and proto-cluster regions)
   - software: astrodendro
   - fitting: _not stated_
   - validation: _not stated_
6. **Line widths and virial parameters**: Gaussian fit to c-C3H2 averaged spectra, subtract channel width in quadrature, alpha = 5 sigma^2 R a/(GM)  
  > "The python package pyspeckit [13] was used to a fit a Gaussian profile to the emission above the σ rms level of each spectra." (4.2 Virial state of the cores)
   - software: pyspeckit
   - assumption: a = 2 ± 1; no magnetic fields, shear or external pressure  
  > "the virial parameter takes the form" (4.2 Virial state of the cores)
   - fitting: _not stated_
   - validation: Fits robust to range of initial guesses  
  > "the fitting procedure provided robust fits for a range of initial guesses" (4.2 Virial state of the cores)
7. **Proto-cluster virial state with relative core velocities**: sigma_rel = standard deviation of core centroid velocities  
  > "define the relative velocity dispersion, as the standard deviation of core centroid velocities" (4.3 Virial state of the proto-clusters)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.4.0 (calibration), 4.7.0 (tclean/feather): calibration, imaging, uvcontsub, feather  
  > "version 4.4.0" (2.1.1 Calibration)
- **spectral-cube** : moment maps  
  > "using the spectral cube package for python." (3.2 Moment map analysis)
- **astrodendro** : identify core structures  
  > "We make use of the astrodendro package in python" (4.1 Defining the core and proto-cluster regions)
- **pyspeckit** 0.1.20: Gaussian line fits  
  > "Version: 0.1.20" (4.2 Virial state of the cores)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Peak column density Cloud D | 3.1e23 | not stated | cm-2 | 3 | the peak column density towards the centre of Cloud D is 3.1× 10 [23] cm [−][2] |
| Peak column density Cloud E/F | 3.7e24 | not stated | cm-2 | 3 | towards the south of Cloud E/F it is 3.7× 10 [24] cm [−][2] |
| Proto-cluster virial parameter Cloud D (sigma_line) | 1.7 | ±1.1 | dimensionless | 6 | α vir (σ line ) = 1.7 ± 1.1 for Cloud D |
| Proto-cluster virial parameter Cloud E/F (sigma_line) | 0.5 | ±0.3 | dimensionless | 6 | α vir (σ line ) = 0.5 ± 0.3 for Cloud E/F |
| Relative velocity dispersion Cloud D / E/F | 1.5 / 1.0 | not stated | km/s | 7 | σ rel = 1.5 km s [−][1] and for Cloud E/F is σ rel = 1.0 km s [−][1] |
| Virial parameter with sigma_rel Cloud D / E/F | 1.5 / 0.2 | ±1.0 / ±0.1 | dimensionless | 7 | α vir (σ rel ) = 1.5 ± 1.0 and for Cloud E/F is α vir (σ rel ) = 0.2 ± 0.1 |
| Core e1a mass (Herschel T) | 311 | ~60% | Msun | 3 | Mass, M (M ⊙ ) 2993 311 (28) [a] 72 19 49 59 148 89 |
| Fraction of cores with alpha_vir <= 2 | 5/10 | not stated | dimensionless | 6 | we find that half (5/10) of the cores have the correct criteria for being gravitationally bound |

## Qualitative findings

- c-C3H2 and CH2NH are optically thin and selectively trace dense gas, unlike self-absorbed HCN and HCO+  
  > "This would point to the CH 2 NH and c-C 3 H 2 being both optically thin" (3.2 Moment map analysis)

## Claim tuples

- H: Are the YMC progenitor cores and proto-clusters gravitationally unstable? | E: Virial analysis using c-C3H2 line widths and dust masses | R: 5/10 cores and both proto-clusters have alpha_vir <= 2 | F: Global gravitational collapse, favouring conveyor-belt formation | **supported**
- H: Do the clouds have a higher critical density for star formation than the disc? | E: Compare core densities with maser-hosting core | R: critical density ~5e6 cm-3 | F: Higher threshold than the disc | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Herschel temperatures on large scales; no magnetic fields, shear or external pressure in virial analysis  
  > "We currently do not know the strength of the magnetic field within the clouds investigated here" (5.4.2 Additional uncertainties)
- Caveat (inferred, ours): Mass depends on coarse Herschel temperatures
- Caveat (inferred, ours): Virial parameters uncertain by 65%
- Caveat (inferred, ours): Assumes clouds will form YMCs
- Caveat (inferred, ours): Core boundaries by eye

## Reproducibility

- Data public (paper): ALMA project listed; BGPS publicly available  
  > "The BGPS is a publicly available, [6] 1.1 mm survey of dust emission" (2.2 ALMA and single dish continuum observations)
- Products in archive: _not stated_
- Missing: Clean parameters and line-free channels
- Missing: Herschel temperature maps (in prep)
- Missing: Core dendrogram parameters
- Data volume (inferred): ~100-300 GB raw for 12m+7m mosaics
- Score (inferred): 5/5, Data public and many steps described, but key imaging parameters and core definitions missing.
- Rediscovery candidate: no, Imaging and core identification details are underspecified and rely on unpublished temperature maps.

## Links

- Method: Battersby et al. 2011 (SED fitting for column density and temperature)
- Companion: Walker et al. 2018 (SMA CMZoom observations of the same clouds)
- Related: CMZoom
- Related: BGPS
- Related: Hi-GAL

## Checks

```json
{
 "quotes": 79,
 "quotes_ok": 79,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2012.1.00133.S"
 ],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 86,
  "stated": 57,
  "rate": 0.663
 },
 "evidence_ok": true
}
```
